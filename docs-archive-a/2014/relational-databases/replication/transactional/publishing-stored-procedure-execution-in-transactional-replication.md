---
title: 트랜잭션 복제에서 저장 프로시저 실행 게시 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- publishing [SQL Server replication], stored procedure execution
- articles [SQL Server replication], stored procedures and
- transactional replication, publishing stored procedure execution
ms.assetid: f4686f6f-c224-4f07-a7cb-92f4dd483158
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0fb5c40db46772cabcb5d1df19e03aced749e1c6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738187"
---
# <a name="publishing-stored-procedure-execution-in-transactional-replication"></a><span data-ttu-id="2f6a6-102">트랜잭션 복제에서 저장 프로시저 실행 게시</span><span class="sxs-lookup"><span data-stu-id="2f6a6-102">Publishing Stored Procedure Execution in Transactional Replication</span></span>
  <span data-ttu-id="2f6a6-103">게시자에서 실행되고 게시된 테이블에 영향을 주는 하나 이상의 저장 프로시저가 있는 경우 이러한 저장 프로시저를 저장 프로시저 실행 아티클로 게시에 포함해 보십시오.</span><span class="sxs-lookup"><span data-stu-id="2f6a6-103">If you have one or more stored procedures that execute at the Publisher and affect published tables, consider including those stored procedures in your publication as stored procedure execution articles.</span></span> <span data-ttu-id="2f6a6-104">프로시저 정의(CREATE PROCEDURE 문)는 구독이 초기화될 때 구독자로 복제되고 게시자에서 프로시저가 실행되면 복제가 구독자에서 해당하는 프로시저를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="2f6a6-104">The definition of the procedure (the CREATE PROCEDURE statement) is replicated to the Subscriber when the subscription is initialized; when the procedure is executed at the Publisher, replication executes the corresponding procedure at the Subscriber.</span></span> <span data-ttu-id="2f6a6-105">이렇게 하면 프로시저 실행만 복제하고 행별 변경 내용은 복제하지 않으므로 대용량 일괄 처리 작업이 수행되는 경우 성능을 크게 향상시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f6a6-105">This can provide significantly better performance for cases where large batch operations are performed, because only the procedure execution is replicated, bypassing the need to replicate the individual changes for each row.</span></span> <span data-ttu-id="2f6a6-106">예를 들어 게시 데이터베이스에서 다음 저장 프로시저를 생성한다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="2f6a6-106">For example, assume you create the following stored procedure in the publication database:</span></span>  
  
```  
CREATE PROC give_raise AS  
UPDATE EMPLOYEES SET salary = salary * 1.10  
```  
  
 <span data-ttu-id="2f6a6-107">이 프로시저는 회사 내의 직원 10,000명의 급여를 10% 인상합니다.</span><span class="sxs-lookup"><span data-stu-id="2f6a6-107">This procedure gives each of the 10,000 employees in your company a 10 percent pay increase.</span></span> <span data-ttu-id="2f6a6-108">게시자에서 이 저장 프로시저를 실행하면 각 직원의 급여가 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="2f6a6-108">When you execute this stored procedure at the Publisher, it updates the salary for each employee.</span></span> <span data-ttu-id="2f6a6-109">저장 프로시저 실행을 복제하지 않으면 업데이트가 여러 단계의 대규모 트랜잭션으로 구독자로 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="2f6a6-109">Without the replication of stored procedure execution, the update would be sent to Subscribers as a large, multi-step transaction:</span></span>  
  
```  
BEGIN TRAN  
UPDATE EMPLOYEES SET salary = salary * 1.10 WHERE PK = 'emp 1'  
UPDATE EMPLOYEES SET salary = salary * 1.10 WHERE PK = 'emp 2'  
```  
  
 <span data-ttu-id="2f6a6-110">10,000개의 업데이트에 대해 이 프로세스가 반복됩니다.</span><span class="sxs-lookup"><span data-stu-id="2f6a6-110">And this repeats for 10,000 updates.</span></span>  
  
 <span data-ttu-id="2f6a6-111">저장 프로시저 실행을 복제하면 복제에서는 배포 데이터베이스에 모든 업데이트를 기록한 후 네트워크를 통해 구독자로 보내지 않고 구독자에서 저장 프로시저를 실행하는 명령만 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="2f6a6-111">With the replication of stored procedure execution, replication sends only the command to execute the stored procedure at the Subscriber, rather than writing all the updates to the distribution database and then sending them over the network to the Subscriber:</span></span>  
  
```  
EXEC give_raise  
```  
  
> [!IMPORTANT]  
>  <span data-ttu-id="2f6a6-112">저장 프로시저 복제가 모든 애플리케이션에 적절한 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="2f6a6-112">Stored procedure replication is not appropriate for all applications.</span></span> <span data-ttu-id="2f6a6-113">아티클이 수평 분할되어 구독자와는 다른 행 집합이 게시자에 있게 되면 게시자와 구독자 모두에서 같은 저장 프로시저를 실행해도 다른 결과가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="2f6a6-113">If an article is filtered horizontally, so that there are different sets of rows at the Publisher than at the Subscriber, executing the same stored procedure at both returns different results.</span></span> <span data-ttu-id="2f6a6-114">마찬가지로 업데이트가 복제되지 않은 다른 테이블의 하위 쿼리를 기반으로 하면 게시자와 구독자 모두에서 같은 저장 프로시저를 실행해도 다른 결과가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="2f6a6-114">Similarly, if an update is based on a subquery of another, nonreplicated table, executing the same stored procedure at both the Publisher and Subscriber returns different results.</span></span>  
  
 <span data-ttu-id="2f6a6-115">**저장 프로시저의 실행을 게시하려면**</span><span class="sxs-lookup"><span data-stu-id="2f6a6-115">**To publish the execution of a stored procedure**</span></span>  
  
-   <span data-ttu-id="2f6a6-116">SQL Server Management Studio: [저장 프로시저 실행을 트랜잭션 게시로 게시&#40;SQL Server Management Studio&#41;](../publish/publish-execution-of-stored-procedure-in-transactional-publication.md)</span><span class="sxs-lookup"><span data-stu-id="2f6a6-116">SQL Server Management Studio: [Publish the Execution of a Stored Procedure in a Transactional Publication &#40;SQL Server Management Studio&#41;](../publish/publish-execution-of-stored-procedure-in-transactional-publication.md)</span></span>  
  
-   <span data-ttu-id="2f6a6-117">복제 Transact-sql 프로그래밍: [transact-sql&#41;&#40;sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql) 실행 하 고 매개 변수에 ' serializable proc exec ' (권장) 또는 ' proc exec ' 값을 지정 **@type** 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f6a6-117">Replication Transact-SQL Programming: execute [sp_addarticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql) and specify a value of 'serializable proc exec' (recommended) or 'proc exec' for the parameter **@type**.</span></span> <span data-ttu-id="2f6a6-118">아티클을 정의하는 방법은 [아티클 정의](../publish/define-an-article.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2f6a6-118">For more information about defining articles, see [Define an Article](../publish/define-an-article.md).</span></span>  
  
## <a name="modifying-the-procedure-at-the-subscriber"></a><span data-ttu-id="2f6a6-119">구독자에서 프로시저 수정</span><span class="sxs-lookup"><span data-stu-id="2f6a6-119">Modifying the Procedure at the Subscriber</span></span>  
 <span data-ttu-id="2f6a6-120">기본적으로 게시자의 저장 프로시저 정의는 각 구독자로 전파됩니다.</span><span class="sxs-lookup"><span data-stu-id="2f6a6-120">By default, the stored procedure definition at the Publisher is propagated to each Subscriber.</span></span> <span data-ttu-id="2f6a6-121">그러나 구독자에서 저장 프로시저를 수정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f6a6-121">However, you can also modify the stored procedure at the Subscriber.</span></span> <span data-ttu-id="2f6a6-122">이는 게시자와 구독자에서 다른 논리를 실행하려고 할 때 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="2f6a6-122">This is useful if you want different logic to be executed at the Publisher and Subscriber.</span></span> <span data-ttu-id="2f6a6-123">예를 들어 구독자의 저장 프로시저 **sp_big_delete**에는 두 가지 기능이 있습니다. 복제된 테이블 **big_table1** 에서 1,000,000개의 행을 삭제하고 복제되지 않은 테이블 **big_table2**를 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="2f6a6-123">For example, consider **sp_big_delete**, a stored procedure at the Publisher that has two functions: it deletes 1,000,000 rows from the replicated table **big_table1** and updates the nonreplicated table **big_table2**.</span></span> <span data-ttu-id="2f6a6-124">네트워크 리소스에 대한 수요를 줄이려면 **sp_big_delete**를 게시하여 100만 개의 행 삭제를 저장 프로시저로 전파해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f6a6-124">To reduce the demand on network resources, you should propagate the 1 million row delete as a stored procedure by publishing **sp_big_delete**.</span></span> <span data-ttu-id="2f6a6-125">구독자에서 100만 개의 행만 삭제하고 **big_table2** 에 대한 후속 업데이트를 수행하지 않도록 **sp_big_delete**를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f6a6-125">At the Subscriber, you can modify **sp_big_delete** to delete only the 1 million rows and not perform the subsequent update to **big_table2**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2f6a6-126">기본적으로 게시자에서 ALTER PROCEDURE를 사용하여 적용한 변경 내용은 구독자로 전파됩니다.</span><span class="sxs-lookup"><span data-stu-id="2f6a6-126">By default, any changes made using ALTER PROCEDURE at the Publisher are propagated to the Subscriber.</span></span> <span data-ttu-id="2f6a6-127">이를 방지하려면 ALTER PROCEDURE를 실행하기 전에 스키마 변경 내용을 전파하는 설정을 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="2f6a6-127">To prevent this, disable the propagation of schema changes before executing ALTER PROCEDURE.</span></span> <span data-ttu-id="2f6a6-128">스키마 변경에 대한 자세한 내용은 [게시 데이터베이스의 스키마 변경](../publish/make-schema-changes-on-publication-databases.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2f6a6-128">For information about schema changes, see [Make Schema Changes on Publication Databases](../publish/make-schema-changes-on-publication-databases.md).</span></span>  
  
## <a name="types-of-stored-procedure-execution-articles"></a><span data-ttu-id="2f6a6-129">저장 프로시저 실행 아티클의 유형</span><span class="sxs-lookup"><span data-stu-id="2f6a6-129">Types of Stored Procedure Execution Articles</span></span>  
 <span data-ttu-id="2f6a6-130">직렬화 가능 프로시저 실행 아티클과 프로시저 실행 아티클을 사용하여 저장 프로시저의 실행을 게시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f6a6-130">There are two different ways in which the execution of a stored procedure can be published: serializable procedure execution article and procedure execution article.</span></span>  
  
-   <span data-ttu-id="2f6a6-131">프로시저가 직렬화 가능 트랜잭션의 컨텍스트 내에서 실행되는 경우에만 프로시저 실행을 복제하는 직렬화 가능 옵션을 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="2f6a6-131">The serializable option is recommended because it replicates the procedure execution only if the procedure is executed within the context of a serializable transaction.</span></span> <span data-ttu-id="2f6a6-132">저장 프로시저가 직렬화 가능 트랜잭션 외부에서 실행되면 게시된 테이블의 데이터 변경 내용이 일련의 DML 문으로 복제됩니다.</span><span class="sxs-lookup"><span data-stu-id="2f6a6-132">If the stored procedure is executed from outside a serializable transaction, changes to data in published tables are replicated as a series of DML statements.</span></span> <span data-ttu-id="2f6a6-133">이 동작을 통해 구독자의 데이터와 게시자의 데이터의 일관성을 기할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f6a6-133">This behavior contributes to making data at the Subscriber consistent with data at the Publisher.</span></span> <span data-ttu-id="2f6a6-134">이는 대규모 정리 작업과 같은 일괄 처리 작업에 특히 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="2f6a6-134">This is especially useful for batch operations, such as large cleanup operations.</span></span>  
  
-   <span data-ttu-id="2f6a6-135">프로시저 실행 옵션을 사용하면 저장 프로시저에 있는 개별 문의 성공 여부에 상관없이 실행을 모든 구독자에 복제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f6a6-135">With the procedure execution option, it is possible that execution could be replicated to all Subscribers regardless of whether individual statements in the stored procedure were successful.</span></span> <span data-ttu-id="2f6a6-136">또한 여러 트랜잭션 내에서 저장 프로시저에 의해 데이터가 변경될 수 있으므로 구독자 데이터와 게시자 데이터가 일치하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f6a6-136">Furthermore, because changes made to data by the stored procedure can occur within multiple transactions, data at the Subscribers might not be consistent with data at the Publisher.</span></span> <span data-ttu-id="2f6a6-137">이러한 문제를 해결하려면 구독자가 읽기 전용이어야 하고 커밋되지 않은 읽기보다 높은 격리 수준을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f6a6-137">To address these issues, it is required that Subscribers are read-only and that you use an isolation level greater than read uncommitted.</span></span> <span data-ttu-id="2f6a6-138">커밋되지 않은 읽기를 사용하면 게시된 테이블의 데이터에 대한 변경 내용이 일련의 DML 문으로 복제됩니다.</span><span class="sxs-lookup"><span data-stu-id="2f6a6-138">If you use read uncommitted, changes to data in published tables are replicated as a series of DML statements.</span></span>  
  
 <span data-ttu-id="2f6a6-139">다음 예에서는 프로시저 복제를 직렬화 가능 프로시저 아티클로 설정하는 것을 권장하는 이유를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="2f6a6-139">The following example illustrates why it is recommended that you set up replication of procedures as serializable procedure articles.</span></span>  
  
```  
BEGIN TRANSACTION T1  
SELECT @var = max(col1) FROM tableA  
UPDATE tableA SET col2 = <value>   
   WHERE col1 = @var   
  
BEGIN TRANSACTION T2  
INSERT tableA VALUES <values>  
COMMIT TRANSACTION T2  
```  
  
 <span data-ttu-id="2f6a6-140">위의 예제에서 트랜잭션 T1의 SELECT는 트랜잭션 T2의 INSERT 이전에 발생한다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="2f6a6-140">In the previous example, it is assumed that the SELECT in transaction T1 happens before the INSERT in transaction T2.</span></span>  
  
 <span data-ttu-id="2f6a6-141">프로시저가 직렬화 가능 트랜잭션(격리 수준이 SERIALIZABLE로 설정됨) 내에서 프로시저가 실행되지 않으면 트랜잭션 T2는 T1의 SELECT 문 범위 내에서 새 행을 삽입할 수 있고 T1 이전에 커밋됩니다.</span><span class="sxs-lookup"><span data-stu-id="2f6a6-141">If the procedure is not executed within a serializable transaction (with isolation level set to SERIALIZABLE), transaction T2 will be allowed to insert a new row within the range of the SELECT statement in T1 and it will commit before T1.</span></span> <span data-ttu-id="2f6a6-142">이는 T2가 T1 이전에 구독자에서 적용되는 것을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="2f6a6-142">This also means that it will be applied at the Subscriber before T1.</span></span> <span data-ttu-id="2f6a6-143">T1이 구독자에서 적용되면, SELECT는 게시자에서와 다른 값을 반환할 수 있고 UPDATE와 다른 결과를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f6a6-143">When T1 is applied at the Subscriber, the SELECT can potentially return a different value than at the Publisher and can result in a different outcome from the UPDATE.</span></span>  
  
 <span data-ttu-id="2f6a6-144">프로시저가 직렬화 가능 트랜잭션 내에서 실행되면, 트랜잭션 T2는 T2의 SELECT 문 범위 내에서 삽입을 할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2f6a6-144">If the procedure is executed within a serializable transaction, transaction T2 will not be allowed to insert within the range covered by the SELECT statement in T2.</span></span> <span data-ttu-id="2f6a6-145">구독자에서 같은 결과를 가져오도록 T1이 커밋될 때까지 T2는 차단됩니다.</span><span class="sxs-lookup"><span data-stu-id="2f6a6-145">It will be blocked until T1 commits ensuring the same results at the Subscriber.</span></span>  
  
 <span data-ttu-id="2f6a6-146">직렬화 가능 트랜잭션 내에서 프로시저를 실행하면 잠금이 더 오래 유지되어 동시성이 줄어들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f6a6-146">Locks will be held longer when you execute the procedure within a serializable transaction and may result in reduced concurrency.</span></span>  
  
## <a name="the-xact_abort-setting"></a><span data-ttu-id="2f6a6-147">XACT_ABORT 설정</span><span class="sxs-lookup"><span data-stu-id="2f6a6-147">The XACT_ABORT Setting</span></span>  
 <span data-ttu-id="2f6a6-148">저장 프로시저 실행을 복제할 때 저장 프로시저를 실행하는 세션에 대해 XACT_ABORT 설정을 ON으로 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f6a6-148">When replicating stored procedure execution, the setting for the session executing the stored procedure should specify XACT_ABORT ON.</span></span> <span data-ttu-id="2f6a6-149">XACT_ABORT가 OFF로 설정되면 게시자에서 프로시저 실행 중 오류가 발생하면 구독자에서도 같은 오류가 발생하여 배포 에이전트가 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="2f6a6-149">If XACT_ABORT is set to OFF, and an error occurs during execution of the procedure at the Publisher, the same error will occur at the Subscriber, causing the Distribution Agent to fail.</span></span> <span data-ttu-id="2f6a6-150">XACT_ABORT를 ON으로 지정하면 게시자에서 실행 중 발생한 모든 오류로 인해 전체 실행이 롤백되므로 배포 에이전트 실패를 막을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f6a6-150">Specifying XACT_ABORT ON ensures that any errors encountered during execution at the Publisher cause the entire execution to be rolled back, avoiding the Distribution Agent failure.</span></span> <span data-ttu-id="2f6a6-151">XACT_ABORT 설정에 대한 자세한 내용은 [SET XACT_ABORT&#40;Transact-SQL&#41;](/sql/t-sql/statements/set-xact-abort-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2f6a6-151">For more information about setting XACT_ABORT, see [SET XACT_ABORT &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-xact-abort-transact-sql).</span></span>  
  
 <span data-ttu-id="2f6a6-152">XACT_ABORT를 OFF로 설정해야 하는 경우에는 배포 에이전트에 대해 **-SkipErrors** 매개 변수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2f6a6-152">If you require a setting of XACT_ABORT OFF, specify the **-SkipErrors** parameter for the Distribution Agent.</span></span> <span data-ttu-id="2f6a6-153">그러면 오류가 발생해도 에이전트가 구독자에서 변경 내용을 계속 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f6a6-153">This allows the agent to continue applying changes at the Subscriber even if an error is encountered.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f6a6-154">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2f6a6-154">See Also</span></span>  
 [<span data-ttu-id="2f6a6-155">Article Options for Transactional Replication</span><span class="sxs-lookup"><span data-stu-id="2f6a6-155">Article Options for Transactional Replication</span></span>](article-options-for-transactional-replication.md)  
  
  
