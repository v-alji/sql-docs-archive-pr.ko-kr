---
title: 트랜잭션 아티클에 대한 변경 내용을 전파하는 방법 지정 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- transactional replication, propagation methods
ms.assetid: a10c5001-22cc-4667-8f0b-3d0818dca2e9
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 72d377ba89f1d393eab48bd9c918012b0f503f9c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731500"
---
# <a name="specify-how-changes-are-propagated-for-transactional-articles"></a><span data-ttu-id="b4bb7-102">트랜잭션 아티클에 대한 변경 내용을 전파하는 방법 지정</span><span class="sxs-lookup"><span data-stu-id="b4bb7-102">Specify How Changes Are Propagated for Transactional Articles</span></span>
  <span data-ttu-id="b4bb7-103">트랜잭션 복제를 사용하여 데이터 변경 내용이 게시자에서 구독자로 전파되는 방법을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4bb7-103">Transactional replication allows you to specify how data changes are propagated from the Publisher to Subscribers.</span></span> <span data-ttu-id="b4bb7-104">다음 4가지 중 하나를 사용하여 게시된 각 테이블에 대해 INSERT, UPDATE 또는 DELETE 등의 각 작업이 구독자로 전파되는 방법을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4bb7-104">For each published table, you can specify one of four ways that each operation (INSERT, UPDATE, or DELETE) should be propagated to the Subscriber:</span></span>  
  
-   <span data-ttu-id="b4bb7-105">트랜잭션 복제가 저장 프로시저를 스크립팅한 후 저장 프로시저를 호출하여 변경 내용을 구독자로 전파하도록 지정합니다(기본값).</span><span class="sxs-lookup"><span data-stu-id="b4bb7-105">Specify that transactional replication should script out and subsequently call a stored procedure to propagate changes to Subscribers (the default).</span></span>  
  
-   <span data-ttu-id="b4bb7-106">INSERT, UPDATE 또는 DELETE 문을 사용하여 변경 내용을 전파하도록 지정합니다.[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 이외 구독자인 경우 기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="b4bb7-106">Specify that the change should be propagated using an INSERT, UPDATE, or DELETE statement (the default for non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Subscribers).</span></span>  
  
-   <span data-ttu-id="b4bb7-107">사용자 지정 저장 프로시저를 사용하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b4bb7-107">Specify that a custom stored procedure should be used.</span></span>  
  
-   <span data-ttu-id="b4bb7-108">어떤 구독자도 이 동작을 수행하지 않도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b4bb7-108">Specify that this action should not be performed at any Subscriber.</span></span> <span data-ttu-id="b4bb7-109">해당 유형의 트랜잭션은 복제되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b4bb7-109">Transactions of that type are not replicated.</span></span>  
  
 <span data-ttu-id="b4bb7-110">기본적으로 트랜잭션 복제는 각 구독자에 설치된 저장 프로시저 집합를 통하여 변경 내용을 구독자로 전파합니다.</span><span class="sxs-lookup"><span data-stu-id="b4bb7-110">By default, transactional replication propagates changes to Subscribers through a set of stored procedures that are installed on each Subscriber.</span></span> <span data-ttu-id="b4bb7-111">게시자의 테이블에서 삽입, 업데이트 또는 삭제 작업이 발생하면 이러한 작업은 구독자에서 저장 프로시저에 대한 호출로 변환됩니다.</span><span class="sxs-lookup"><span data-stu-id="b4bb7-111">When an insert, update or delete occurs on a table at the Publisher, the operation is translated into a call to a stored procedure at the Subscriber.</span></span> <span data-ttu-id="b4bb7-112">저장 프로시저에서는 테이블의 열로 매핑하는 매개 변수를 적용하여 이러한 열이 구독자에서 변경되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4bb7-112">The stored procedure accepts parameters that map to the columns in the table, allowing those columns to be changed at the Subscriber.</span></span>  
  
 <span data-ttu-id="b4bb7-113">트랜잭션 아티클의 데이터 변경 내용을 전파하는 방법을 설정하려면 [트랜잭션 아티클의 데이터 변경 내용을 전파하는 방법 설정](../publish/set-the-propagation-method-for-data-changes-to-transactional-articles.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="b4bb7-113">To set the propagation method for data changes to transactional articles, see [Set the Propagation Method for Data Changes to Transactional Articles](../publish/set-the-propagation-method-for-data-changes-to-transactional-articles.md).</span></span>  
  
## <a name="default-and-custom-stored-procedures"></a><span data-ttu-id="b4bb7-114">기본 저장 프로시저 및 사용자 지정 저장 프로시저</span><span class="sxs-lookup"><span data-stu-id="b4bb7-114">Default and custom stored procedures</span></span>  
 <span data-ttu-id="b4bb7-115">복제 시 각 테이블 아티클에 대해 기본적으로 생성되는 3가지 프로시저는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="b4bb7-115">The three procedures that replication creates by default for each table article are:</span></span>  
  
-   <span data-ttu-id="b4bb7-116">**sp_MSins_\<** *tablename* **>** - 삽입 처리</span><span class="sxs-lookup"><span data-stu-id="b4bb7-116">**sp_MSins_\<** *tablename* **>**, which handles inserts.</span></span>  
  
-   <span data-ttu-id="b4bb7-117">**sp_MSupd_\<** *tablename* **>** - 업데이트 처리</span><span class="sxs-lookup"><span data-stu-id="b4bb7-117">**sp_MSupd_\<** *tablename* **>**, which handles updates.</span></span>  
  
-   <span data-ttu-id="b4bb7-118">**sp_MSdel_\<** *tablename* **>** - 삭제 처리</span><span class="sxs-lookup"><span data-stu-id="b4bb7-118">**sp_MSdel_\<** *tablename* **>**, which handles deletes.</span></span>  
  
 <span data-ttu-id="b4bb7-119">프로시저에서 사용하는 **\<***tablename***>** 은 아티클을 게시에 추가하는 방법과 구독 데이터베이스에 소유자는 다르지만 이름이 같은 테이블이 포함되어 있는지 여부에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="b4bb7-119">The **\<***tablename***>** used in the procedure depends on how the article was added to the publication and whether the subscription database contains a table of the same name with a different owner.</span></span>  
  
 <span data-ttu-id="b4bb7-120">이러한 프로시저는 아티클을 게시에 추가할 때 지정하는 사용자 지정 프로시저로 바꿀 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4bb7-120">Any of these procedures can be replaced with a custom procedure that you specify when adding an article to a publication.</span></span> <span data-ttu-id="b4bb7-121">구독자에서 행이 업데이트될 때 데이터를 감사 테이블에 삽입하는 경우와 같이 애플리케이션에 사용자 지정 논리가 필요할 경우 사용자 지정 프로시저를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b4bb7-121">Custom procedures are used if an application requires custom logic, such as inserting data into an audit table when a row is updated at a Subscriber.</span></span> <span data-ttu-id="b4bb7-122">사용자 지정 저장 프로시저 지정 방법은 위에 나열된 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="b4bb7-122">For more information about specifying custom stored procedures, see the how to topics listed above.</span></span>  
  
 <span data-ttu-id="b4bb7-123">기본 복제 프로시저 또는 사용자 지정 프로시저를 지정하면 각 프로시저에 대한 호출 구문도 지정해야 합니다. 기본 프로시저를 사용할 경우에는 복제에서 기본값을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b4bb7-123">If you specify the default replication procedures or custom procedures, you also specify call syntax for each procedure (replication selects defaults if you use the default procedures).</span></span> <span data-ttu-id="b4bb7-124">호출 구문은 프로시저에 제공되는 매개 변수의 구조 및 각 데이터 변경 시 구독자로 보낼 정보의 양을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="b4bb7-124">The call syntax determines the structure of the parameters provided to the procedure and how much information is sent to the Subscriber with each data change.</span></span> <span data-ttu-id="b4bb7-125">자세한 내용은 이 항목의 "저장 프로시저 호출 구문" 섹션을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="b4bb7-125">For more information, see the section "Call Syntax for Stored Procedures" in this topic.</span></span>  
  
### <a name="considerations-for-using-custom-stored-procedures"></a><span data-ttu-id="b4bb7-126">사용자 지정 저장 프로시저 사용 시 고려 사항</span><span class="sxs-lookup"><span data-stu-id="b4bb7-126">Considerations for Using Custom Stored Procedures</span></span>  
 <span data-ttu-id="b4bb7-127">사용자 지정 저장 프로시저를 사용할 때는 다음 사항을 고려하십시오.</span><span class="sxs-lookup"><span data-stu-id="b4bb7-127">Keep the following considerations in mind when using custom stored procedures:</span></span>  
  
-   <span data-ttu-id="b4bb7-128">[!INCLUDE[msCoName](../../../includes/msconame-md.md)] 에서는 사용자 지정 논리를 지원하지 않으므로 사용자가 저장 프로시저의 논리를 지원해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4bb7-128">You must support the logic in the stored procedure; [!INCLUDE[msCoName](../../../includes/msconame-md.md)] does not provide support for custom logic.</span></span>  
  
-   <span data-ttu-id="b4bb7-129">복제에서 사용하는 트랜잭션과 충돌을 피하려면 사용자 지정 프로시저에서 명시적 트랜잭션을 사용하지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4bb7-129">In order to avoid conflicts with the transactions used by replication, explicit transactions should not be used in custom procedures.</span></span>  
  
-   <span data-ttu-id="b4bb7-130">일반적으로 구독자에 있는 스키마는 게시자에 있는 스키마는 동일하지만 열 필터링을 사용할 경우 게시자 스키마의 하위 집합일 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4bb7-130">The schema at the Subscriber is typically identical to the schema at the Publisher, but can also be a subset of the Publisher schema if column filtering is used.</span></span> <span data-ttu-id="b4bb7-131">데이터를 이동할 때 구독자에 있는 스키마가 게시자에 있는 스키마의 하위 집합이 되지 않도록 스키마를 변환하려면 [!INCLUDE[ssISCurrent](../../../includes/ssiscurrent-md.md)] 를 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="b4bb7-131">However, if you need to transform the schema as the data is moved such that the schema on the Subscriber is not a subset of the schema on the Publisher, [!INCLUDE[ssISCurrent](../../../includes/ssiscurrent-md.md)] is the recommended solution.</span></span> <span data-ttu-id="b4bb7-132">자세한 내용은 [SQL Server Integration Services](../../../integration-services/sql-server-integration-services.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b4bb7-132">For more information, see [SQL Server Integration Services](../../../integration-services/sql-server-integration-services.md).</span></span>  
  
-   <span data-ttu-id="b4bb7-133">게시된 테이블에 대해 스키마 변경을 적용하면 사용자 지정 프로시저를 다시 생성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4bb7-133">If you make schema changes to a published table, the custom procedures must be regenerated.</span></span> <span data-ttu-id="b4bb7-134">자세한 내용은 [스키마 변경 내용을 반영하기 위해 사용자 지정 트랜잭션 프로시저 다시 생성](transactional-articles-regenerate-to-reflect-schema-changes.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b4bb7-134">For more information, see [Regenerate Custom Transactional Procedures to Reflect Schema Changes](transactional-articles-regenerate-to-reflect-schema-changes.md).</span></span>  
  
-   <span data-ttu-id="b4bb7-135">배포 에이전트의 **-SubscriptionStreams** 매개 변수에 1보다 큰 값을 사용할 경우 기본 키 열에 대한 업데이트가 성공했는지 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4bb7-135">If you use a value greater than 1 for **-SubscriptionStreams** parameter of the Distribution Agent, you must ensure that updates to primary key columns are successful.</span></span> <span data-ttu-id="b4bb7-136">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="b4bb7-136">For example:</span></span>  
  
    ```  
    update ... set pk = 2 where pk = 1 -- update 1  
    update ... set pk = 3 where pk = 2 -- update 2  
    ```  
  
     <span data-ttu-id="b4bb7-137">배포 에이전트에서 두 개 이상의 연결을 사용할 경우 이러한 두 업데이트를 서로 다른 연결을 통해 복제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4bb7-137">If the Distribution Agent uses more than one connection, these two updates might be replicated over different connections.</span></span> <span data-ttu-id="b4bb7-138">업데이트 1이 먼저 적용되면 아무 문제 없지만 업데이트 2가 먼저 적용되면 업데이트 1이 아직 적용되지 않았기 때문에 '적용된 행 없음' 메시지가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="b4bb7-138">If update 1 is applied first, there is no problem; if update 2 is applied first it will return '0 rows affected' because update 1 has not yet occurred.</span></span> <span data-ttu-id="b4bb7-139">기본 프로시저에서는 업데이트 시 변경된 행이 없을 경우 오류를 발생시켜 이 상황을 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="b4bb7-139">This situation is handled in the default procedures by raising an error if no rows are affected on an update:</span></span>  
  
    ```  
    if @@rowcount = 0  
        if @@microsoftversion>0x07320000  
            exec sys.sp_MSreplraiserror 20598  
    ```  
  
     <span data-ttu-id="b4bb7-140">오류가 발생하면 배포 에이전트가 단일 연결을 통해 업데이트를 다시 시도하고 이로 인해 업데이트가 성공적으로 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="b4bb7-140">Raising the error forces the Distribution Agent to retry the updates over a single connection, which will succeed.</span></span> <span data-ttu-id="b4bb7-141">사용자 지정 저장 프로시저에도 비슷한 논리가 포함되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4bb7-141">Custom stored procedures must include similar logic.</span></span>  
  
### <a name="call-syntax-for-stored-procedures"></a><span data-ttu-id="b4bb7-142">저장 프로시저 호출 구문</span><span class="sxs-lookup"><span data-stu-id="b4bb7-142">Call syntax for stored procedures</span></span>  
 <span data-ttu-id="b4bb7-143">트랜잭션 복제에서 사용하는 프로시저를 호출하는 데 사용되는 구문은 5개가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4bb7-143">There are five options for the syntax used to call the procedures used by transactional replication:</span></span>  
  
-   <span data-ttu-id="b4bb7-144">CALL 구문.</span><span class="sxs-lookup"><span data-stu-id="b4bb7-144">CALL syntax.</span></span> <span data-ttu-id="b4bb7-145">삽입, 업데이트 및 삭제에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4bb7-145">Can be used for inserts, updates, and deletes.</span></span> <span data-ttu-id="b4bb7-146">기본적으로 복제에서는 이 구문을 삽입 및 삭제에 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b4bb7-146">By default, replication uses this syntax for inserts and deletes.</span></span>  
  
-   <span data-ttu-id="b4bb7-147">SCALL 구문.</span><span class="sxs-lookup"><span data-stu-id="b4bb7-147">SCALL syntax.</span></span> <span data-ttu-id="b4bb7-148">업데이트에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4bb7-148">Can be used for updates only.</span></span> <span data-ttu-id="b4bb7-149">기본적으로 복제에서는 이 구문을 업데이트에 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b4bb7-149">By default, replication uses this syntax for updates.</span></span>  
  
-   <span data-ttu-id="b4bb7-150">MCALL 구문.</span><span class="sxs-lookup"><span data-stu-id="b4bb7-150">MCALL syntax.</span></span> <span data-ttu-id="b4bb7-151">업데이트에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4bb7-151">Can be used for updates only.</span></span>  
  
-   <span data-ttu-id="b4bb7-152">XCALL 구문.</span><span class="sxs-lookup"><span data-stu-id="b4bb7-152">XCALL syntax.</span></span> <span data-ttu-id="b4bb7-153">업데이트 및 삭제에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4bb7-153">Can be used for updates and deletes.</span></span>  
  
-   <span data-ttu-id="b4bb7-154">VCALL 구문.</span><span class="sxs-lookup"><span data-stu-id="b4bb7-154">VCALL.</span></span> <span data-ttu-id="b4bb7-155">업데이트할 수 있는 구독에 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b4bb7-155">Used for updatable subscriptions.</span></span> <span data-ttu-id="b4bb7-156">내부적으로만 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="b4bb7-156">Internal use only.</span></span>  
  
 <span data-ttu-id="b4bb7-157">각 방법은 구독자로 전파되는 데이터 양에 차이가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4bb7-157">Each method differs in the amount of data that is propagated to the Subscriber.</span></span> <span data-ttu-id="b4bb7-158">예를 들어 SCALL은 실제로 업데이트가 적용된 열 값만 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="b4bb7-158">For example, SCALL passes in values only for the columns that are actually affected by an update.</span></span> <span data-ttu-id="b4bb7-159">이와 대조적으로 XCALL은 업데이트 적용 여부에 상관없이 모든 열 및 각 열에 대한 모든 이전 데이터 값이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="b4bb7-159">XCALL, by contrast, requires all columns (whether affected by an update or not) and all the old data values for each column.</span></span> <span data-ttu-id="b4bb7-160">대부분의 경우 업데이트에는 SCALL이 적합하지만 애플리케이션에서 업데이트하는 동안 모든 데이터를 필요로 하는 경우에는 XCALL이 적합합니다.</span><span class="sxs-lookup"><span data-stu-id="b4bb7-160">In many cases, SCALL is appropriate for updates, but if your application requires all the data values during an update, XCALL allows for this.</span></span>  
  
#### <a name="call-syntax"></a><span data-ttu-id="b4bb7-161">CALL 구문</span><span class="sxs-lookup"><span data-stu-id="b4bb7-161">CALL Syntax</span></span>  
 <span data-ttu-id="b4bb7-162">INSERT 저장 프로시저</span><span class="sxs-lookup"><span data-stu-id="b4bb7-162">INSERT stored procedures</span></span>  
 <span data-ttu-id="b4bb7-163">INSERT 문을 처리하는 저장 프로시저는 모든 열에 대해 삽입된 값을 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="b4bb7-163">Stored procedures handling INSERT statements will be passed the inserted values for all columns:</span></span>  
  
```  
c1, c2, c3,... cn  
```  
  
 <span data-ttu-id="b4bb7-164">UPDATE 저장 프로시저</span><span class="sxs-lookup"><span data-stu-id="b4bb7-164">UPDATE stored procedures</span></span>  
 <span data-ttu-id="b4bb7-165">UPDATE 문을 처리하는 저장 프로시저에 아티클에 정의된 모든 열에 대해 업데이트된 값이 전달된 다음 기본 키 열의 원래 값이 전달됩니다. 변경된 열은 확인하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b4bb7-165">Stored procedures handling UPDATE statements will be passed the updated values for all columns defined in the article, followed by the original values for the primary key columns (no attempt is made to determine which columns were changed.):</span></span>  
  
```  
c1, c2, c3,... cn, pkc1, pkc2, pkc3,... pkcn  
```  
  
 <span data-ttu-id="b4bb7-166">DELETE 저장 프로시저</span><span class="sxs-lookup"><span data-stu-id="b4bb7-166">DELETE stored procedures</span></span>  
 <span data-ttu-id="b4bb7-167">DELETE 문을 처리하는 저장 프로시저에 기본 키 열에 대한 값이 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="b4bb7-167">Stored procedures handling DELETE statements will be passed values for the primary key columns:</span></span>  
  
```  
pkc1, pkc2, pkc3,... pkcn  
```  
  
#### <a name="scall-syntax"></a><span data-ttu-id="b4bb7-168">SCALL 구문</span><span class="sxs-lookup"><span data-stu-id="b4bb7-168">SCALL Syntax</span></span>  
 <span data-ttu-id="b4bb7-169">UPDATE 저장 프로시저</span><span class="sxs-lookup"><span data-stu-id="b4bb7-169">UPDATE stored procedures</span></span>  
 <span data-ttu-id="b4bb7-170">변경된 열에 대해서만 UPDATE 문을 처리하는 저장 프로시저에 업데이트된 값이 전달된 다음 차례대로 기본 키 열의 원래 값과 변경된 열을 나타내는 비트 마스크(`binary(n)`) 매개 변수가 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="b4bb7-170">Stored procedures handling UPDATE statements will be passed the updated values only for those columns that have changed, followed by the original values for the primary key columns, followed by a bitmask (`binary(n)`) parameter that indicates the changed columns.</span></span> <span data-ttu-id="b4bb7-171">다음 예에서 열 2(c2)는 변경되지 않은 것입니다.</span><span class="sxs-lookup"><span data-stu-id="b4bb7-171">In the following example, column 2 (c2) has not changed:</span></span>  
  
```  
c1, , c3,... cn, pkc1, pkc2, pkc3,... pkcn, bitmask  
```  
  
#### <a name="mcall-syntax"></a><span data-ttu-id="b4bb7-172">MCALL 구문</span><span class="sxs-lookup"><span data-stu-id="b4bb7-172">MCALL Syntax</span></span>  
 <span data-ttu-id="b4bb7-173">UPDATE 저장 프로시저</span><span class="sxs-lookup"><span data-stu-id="b4bb7-173">UPDATE stored procedures</span></span>  
 <span data-ttu-id="b4bb7-174">UPDATE 문을 처리하는 저장 프로시저에 아티클에 정의된 모든 열에 대해 업데이트된 값이 전달된 다음 차례대로 기본 키 열의 원래 값과 변경된 열을 나타내는 비트 마스크(`binary(n)`) 매개 변수가 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="b4bb7-174">Stored procedures handling UPDATE statements will be passed the updated values for all columns defined in the article, followed by the original values for the primary key columns, followed by a bitmask (`binary(n)`) parameter that indicates the changed columns:</span></span>  
  
```  
c1, c2, c3,... cn, pkc1, pkc2, pkc3,... pkcn, bitmask  
```  
  
#### <a name="xcall-syntax"></a><span data-ttu-id="b4bb7-175">XCALL 구문</span><span class="sxs-lookup"><span data-stu-id="b4bb7-175">XCALL Syntax</span></span>  
 <span data-ttu-id="b4bb7-176">UPDATE 저장 프로시저</span><span class="sxs-lookup"><span data-stu-id="b4bb7-176">UPDATE stored procedures</span></span>  
 <span data-ttu-id="b4bb7-177">UPDATE 문을 처리하는 저장 프로시저에 아티클에 정의된 모든 열에 대한 원래 값(이전 이미지)이 전달된 다음 아티클에 정의된 모든 열의 업데이트 값(이후 이미지)이 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="b4bb7-177">Stored procedures handling UPDATE statements will be passed the original values (the before image) for all columns defined in the article, followed by the updated values (the after image) for all columns defined in the article:</span></span>  
  
```  
old-c1, old-c2, old-c3,... old-cn, c1, c2, c3,... cn,  
```  
  
 <span data-ttu-id="b4bb7-178">DELETE 저장 프로시저</span><span class="sxs-lookup"><span data-stu-id="b4bb7-178">DELETE stored procedures</span></span>  
 <span data-ttu-id="b4bb7-179">DELETE 문을 처리하는 저장 프로시저에 아티클에 정의된 모든 열에 대한 원래 값(이전 이미지)이 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="b4bb7-179">Stored procedures handling DELETE statements will be passed the original (the before image) values for all columns defined in the article:</span></span>  
  
```  
old-c1, old-c2, old-c3,... old-cn  
```  
  
> [!NOTE]  
>  <span data-ttu-id="b4bb7-180">XCALL을 사용하는 경우 **text** 및 **image** 열에 대한 이전 이미지 값은 NULL이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b4bb7-180">When using XCALL, the before image values for **text** and **image** columns are expected to be NULL.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="b4bb7-181">예제</span><span class="sxs-lookup"><span data-stu-id="b4bb7-181">Examples</span></span>  
 <span data-ttu-id="b4bb7-182">다음 프로시저는 `Vendor Table` 예제 데이터베이스의 [!INCLUDE[ssSampleDBCoShort](../../../includes/sssampledbcoshort-md.md)] 용으로 만든 기본 프로시저입니다.</span><span class="sxs-lookup"><span data-stu-id="b4bb7-182">The following procedures are the default procedures created for the `Vendor Table` in the [!INCLUDE[ssSampleDBCoShort](../../../includes/sssampledbcoshort-md.md)] sample database.</span></span>  
  
```  
--INSERT procedure using CALL syntax  
create procedure [sp_MSins_PurchasingVendor]   
  @c1 int,@c2 nvarchar(15),@c3 nvarchar(50),@c4 tinyint,@c5 bit,@c6 bit,@c7 nvarchar(1024),@c8 datetime  
as   
begin   
insert into [Purchasing].[Vendor]([VendorID]  
,[AccountNumber]  
,[Name]  
,[CreditRating]  
,[PreferredVendorStatus]  
,[ActiveFlag]  
,[PurchasingWebServiceURL]  
,[ModifiedDate])  
values (   
 @c1  
,@c2  
,@c3  
,@c4  
,@c5  
,@c6  
,@c7  
,@c8  
 )   
end  
go  
  
--UPDATE procedure using SCALL syntax  
create procedure [sp_MSupd_PurchasingVendor]   
 @c1 int = null,@c2 nvarchar(15) = null,@c3 nvarchar(50) = null,@c4 tinyint = null,@c5 bit = null,@c6 bit = null,@c7 nvarchar(1024) = null,@c8 datetime = null,@pkc1 int  
,@bitmap binary(2)  
as  
begin  
update [Purchasing].[Vendor] set   
 [AccountNumber] = case substring(@bitmap,1,1) & 2 when 2 then @c2 else [AccountNumber] end  
,[Name] = case substring(@bitmap,1,1) & 4 when 4 then @c3 else [Name] end  
,[CreditRating] = case substring(@bitmap,1,1) & 8 when 8 then @c4 else [CreditRating] end  
,[PreferredVendorStatus] = case substring(@bitmap,1,1) & 16 when 16 then @c5 else [PreferredVendorStatus] end  
,[ActiveFlag] = case substring(@bitmap,1,1) & 32 when 32 then @c6 else [ActiveFlag] end  
,[PurchasingWebServiceURL] = case substring(@bitmap,1,1) & 64 when 64 then @c7 else [PurchasingWebServiceURL] end  
,[ModifiedDate] = case substring(@bitmap,1,1) & 128 when 128 then @c8 else [ModifiedDate] end  
where [VendorID] = @pkc1  
if @@rowcount = 0  
    if @@microsoftversion>0x07320000  
        exec sp_MSreplraiserror 20598  
end  
go  
  
--DELETE procedure using CALL syntax  
create procedure [sp_MSdel_PurchasingVendor]   
  @pkc1 int  
as   
begin   
delete [Purchasing].[Vendor]  
where [VendorID] = @pkc1  
if @@rowcount = 0  
    if @@microsoftversion>0x07320000  
        exec sp_MSreplraiserror 20598  
end   
go  
```  
  
## <a name="see-also"></a><span data-ttu-id="b4bb7-183">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b4bb7-183">See Also</span></span>  
 [<span data-ttu-id="b4bb7-184">Article Options for Transactional Replication</span><span class="sxs-lookup"><span data-stu-id="b4bb7-184">Article Options for Transactional Replication</span></span>](article-options-for-transactional-replication.md)  
  
  
