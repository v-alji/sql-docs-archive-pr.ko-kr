---
title: max degree of parallelism 서버 구성 옵션 구성 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- parallel queries [SQL Server]
- processors [SQL Server], parallel queries
- number of processors for parallel queries
- max degree of parallelism option
ms.assetid: 86b65bf1-a6a1-4670-afc0-cdfad1558032
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 824dc837142acc4a0898cb04b4a8687bc5be4043
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652342"
---
# <a name="configure-the-max-degree-of-parallelism-server-configuration-option"></a><span data-ttu-id="67911-102">max degree of parallelism 서버 구성 옵션 구성</span><span class="sxs-lookup"><span data-stu-id="67911-102">Configure the max degree of parallelism Server Configuration Option</span></span>
  <span data-ttu-id="67911-103">이 항목에서는 또는을 사용 하 `max degree of parallelism` 여에서 서버 구성 옵션을 구성 하는 방법에 대해 설명 합니다 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="67911-103">This topic describes how to configure the `max degree of parallelism` server configuration option in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="67911-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스는 마이크로프로세서나 CPU가 둘 이상인 컴퓨터에서 실행될 경우 최적 병렬 처리 수준, 즉 각 병렬 계획 실행에 대해 단일 문을 실행하는 데 사용된 프로세서 수를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="67911-104">When an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] runs on a computer that has more than one microprocessor or CPU, it detects the best degree of parallelism, that is, the number of processors employed to run a single statement, for each parallel plan execution.</span></span> <span data-ttu-id="67911-105">`max degree of parallelism` 옵션을 사용하여 병렬 계획 실행에 사용되도록 프로세서 수를 제한할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67911-105">You can use the `max degree of parallelism` option to limit the number of processors to use in parallel plan execution.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="67911-106">는 쿼리에 대한 병렬 실행 계획, 인덱스 DDL(데이터 정의 언어) 작업 및 정적 커서와 키 집합 커서 채우기를 고려합니다.</span><span class="sxs-lookup"><span data-stu-id="67911-106">considers parallel execution plans for queries, index data definition language (DDL) operations, and static and keyset-driven cursor population.</span></span>  
  
 <span data-ttu-id="67911-107">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="67911-107">**In This Topic**</span></span>  
  
-   <span data-ttu-id="67911-108">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="67911-108">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="67911-109">제한 사항</span><span class="sxs-lookup"><span data-stu-id="67911-109">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="67911-110">권장 사항</span><span class="sxs-lookup"><span data-stu-id="67911-110">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="67911-111">보안</span><span class="sxs-lookup"><span data-stu-id="67911-111">Security</span></span>](#Security)  
  
-   <span data-ttu-id="67911-112">**최대 병렬 처리 수준 옵션을 구성하려면:**</span><span class="sxs-lookup"><span data-stu-id="67911-112">**To configure the max degree of parallelism option, using:**</span></span>  
  
     [<span data-ttu-id="67911-113">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="67911-113">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="67911-114">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="67911-114">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="67911-115">**후속 작업:**  [최대 병렬 처리 수준 옵션을 구성한 후](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="67911-115">**Follow Up:**  [After you configure the max degree of parallelism option](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="67911-116">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="67911-116">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="67911-117">제한 사항</span><span class="sxs-lookup"><span data-stu-id="67911-117">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="67911-118">affinity mask 옵션을 기본값으로 설정하지 않으면 SMP(대칭적 다중 처리) 시스템에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에 사용 가능한 프로세서 수가 제한될 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67911-118">If the affinity mask option is not set to the default, it may restrict the number of processors available to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on symmetric multiprocessing (SMP) systems.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="67911-119">권장 사항</span><span class="sxs-lookup"><span data-stu-id="67911-119">Recommendations</span></span>  
  
-   <span data-ttu-id="67911-120">이 옵션은 고급 옵션으로, 숙련된 데이터베이스 관리자나 공인된 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 기술 지원 담당자만 변경해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="67911-120">This option is an advanced option and should be changed only by an experienced database administrator or certified [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] technician.</span></span>  
  
-   <span data-ttu-id="67911-121">서버에서 최대 병렬 처리 수준을 결정할 수 있도록 하려면 이 옵션을 기본값인 0으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="67911-121">To enable the server to determine the maximum degree of parallelism, set this option to 0, the default value.</span></span> <span data-ttu-id="67911-122">최대 병렬 처리 수준을 0으로 설정하면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서는 최대 64개의 프로세서까지 모두 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67911-122">Setting maximum degree of parallelism to 0 allows [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to use all the available processors up to 64 processors.</span></span> <span data-ttu-id="67911-123">병렬 계획을 생성하지 않으려면 `max degree of parallelism`을 1로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="67911-123">To suppress parallel plan generation, set `max degree of parallelism` to 1.</span></span> <span data-ttu-id="67911-124">단일 쿼리 실행에서 사용할 수 있는 프로세서 코어의 최대 개수를 지정하려면 값을 1부터 32,767까지의 값 중 하나를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="67911-124">Set the value to a number from 1 to 32,767 to specify the maximum number of processor cores that can be used by a single query execution.</span></span> <span data-ttu-id="67911-125">사용 가능한 프로세서 수보다 더 큰 수를 지정하면 사용 가능한 실제 프로세서 수가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="67911-125">If a value greater than the number of available processors is specified, the actual number of available processors is used.</span></span> <span data-ttu-id="67911-126">컴퓨터에 프로세서가 하나만 있는 경우 `max degree of parallelism` 값이 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="67911-126">If the computer has only one processor, the `max degree of parallelism` value is ignored.</span></span>  
  
-   <span data-ttu-id="67911-127">쿼리 문에 MAXDOP 쿼리 힌트를 지정하면 쿼리의 max degree of parallelism 값을 재정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67911-127">You can override the max degree of parallelism value in queries by specifying the MAXDOP query hint in the query statement.</span></span> <span data-ttu-id="67911-128">자세한 내용은 [쿼리 힌트&#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-query)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="67911-128">For more information, see [Query Hints &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-query).</span></span>  
  
-   <span data-ttu-id="67911-129">인덱스를 만들거나 다시 작성하는 인덱스 작업 또는 클러스터형 인덱스를 삭제하는 인덱스 작업은 리소스가 많이 소모됩니다.</span><span class="sxs-lookup"><span data-stu-id="67911-129">Index operations that create or rebuild an index, or that drop a clustered index, can be resource intensive.</span></span> <span data-ttu-id="67911-130">인덱스 문에 MAXDOP 인덱스 옵션을 지정하면 인덱스 작업의 max degree of parallelism 값을 재정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67911-130">You can override the max degree of parallelism value for index operations by specifying the MAXDOP index option in the index statement.</span></span> <span data-ttu-id="67911-131">MAXDOP 값은 실행 시 문에 적용되며 인덱스 메타데이터에 저장되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="67911-131">The MAXDOP value is applied to the statement at execution time and is not stored in the index metadata.</span></span> <span data-ttu-id="67911-132">자세한 내용은 [병렬 인덱스 작업 구성](../../relational-databases/indexes/configure-parallel-index-operations.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="67911-132">For more information, see [Configure Parallel Index Operations](../../relational-databases/indexes/configure-parallel-index-operations.md).</span></span>  
  
-   <span data-ttu-id="67911-133">쿼리 및 인덱스 작업과 함께 이 옵션은 DBCC CHECKTABLE, DBCC CHECKDB 및 DBCC CHECKFILEGROUP의 병렬 처리도 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="67911-133">In addition to queries and index operations, this option also controls the parallelism of DBCC CHECKTABLE, DBCC CHECKDB, and DBCC CHECKFILEGROUP.</span></span> <span data-ttu-id="67911-134">추적 플래그 2528을 사용하여 이러한 문의 병렬 실행 계획을 비활성화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67911-134">You can disable parallel execution plans for these statements by using trace flag 2528.</span></span> <span data-ttu-id="67911-135">자세한 내용은 [추적 플래그&#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="67911-135">For more information, see [Trace Flags &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="67911-136">보안</span><span class="sxs-lookup"><span data-stu-id="67911-136">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="67911-137">권한</span><span class="sxs-lookup"><span data-stu-id="67911-137">Permissions</span></span>  
 <span data-ttu-id="67911-138">매개 변수 없이 또는 첫 번째 매개 변수만 사용하여 **sp_configure** 를 실행할 수 있는 권한은 기본적으로 모든 사용자에게 부여됩니다.</span><span class="sxs-lookup"><span data-stu-id="67911-138">Execute permissions on **sp_configure** with no parameters or with only the first parameter are granted to all users by default.</span></span> <span data-ttu-id="67911-139">구성 옵션을 변경하거나 RECONFIGURE 문을 실행하는 두 매개 변수를 사용하여 **sp_configure** 를 실행하려면 사용자에게 ALTER SETTINGS 서버 수준 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="67911-139">To execute **sp_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server-level permission.</span></span> <span data-ttu-id="67911-140">**sysadmin** 및 **serveradmin** 고정 서버 역할은 ALTER SETTINGS 권한을 암시적으로 보유하고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67911-140">The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="67911-141">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="67911-141">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-configure-the-max-degree-of-parallelism-option"></a><span data-ttu-id="67911-142">최대 병렬 처리 수준 옵션을 구성하려면</span><span class="sxs-lookup"><span data-stu-id="67911-142">To configure the max degree of parallelism option</span></span>  
  
1.  <span data-ttu-id="67911-143">**개체 탐색기**에서 서버를 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="67911-143">In **Object Explorer**, right-click a server and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="67911-144">**고급** 노드를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="67911-144">Click the **Advanced** node.</span></span>  
  
3.  <span data-ttu-id="67911-145">**최대 병렬 처리 수준** 상자에서 병렬 계획 실행에 사용할 프로세서의 최대 개수를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="67911-145">In the **Max Degree of Parallelism** box, select the maximum number of processors to use in parallel plan execution.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="67911-146">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="67911-146">Using Transact-SQL</span></span>  
  
#### <a name="to-configure-the-max-degree-of-parallelism-option"></a><span data-ttu-id="67911-147">최대 병렬 처리 수준 옵션을 구성하려면</span><span class="sxs-lookup"><span data-stu-id="67911-147">To configure the max degree of parallelism option</span></span>  
  
1.  <span data-ttu-id="67911-148">[!INCLUDE[ssDE](../../includes/ssde-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="67911-148">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="67911-149">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="67911-149">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="67911-150">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="67911-150">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="67911-151">이 예제에서는 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) 를 사용하여 `max degree of parallelism` 옵션을 `8`으로 구성하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="67911-151">This example shows how to use [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) to configure the `max degree of parallelism` option to `8`.</span></span>  
  
```sql  
USE AdventureWorks2012 ;  
GO   
EXEC sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE WITH OVERRIDE;  
GO  
EXEC sp_configure 'max degree of parallelism', 8;  
GO  
RECONFIGURE WITH OVERRIDE;  
GO  
```  
  
 <span data-ttu-id="67911-152">자세한 내용은 [서버 구성 옵션&#40;SQL Server&#41;](server-configuration-options-sql-server.md)서버 구성 옵션을 보거나 구성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="67911-152">For more information, see [Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md).</span></span>  
  
##  <a name="follow-up-after-you-configure-the-max-degree-of-parallelism-option"></a><a name="FollowUp"></a> <span data-ttu-id="67911-153">후속 작업: 최대 병렬 처리 수준 옵션을 구성한 후</span><span class="sxs-lookup"><span data-stu-id="67911-153">Follow Up: After you configure the max degree of parallelism option</span></span>  
 <span data-ttu-id="67911-154">이 설정은 서버를 다시 시작하지 않아도 즉시 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="67911-154">The setting takes effect immediately without restarting the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67911-155">참고 항목</span><span class="sxs-lookup"><span data-stu-id="67911-155">See Also</span></span>  
 <span data-ttu-id="67911-156">[선호도 마스크 서버 구성 옵션](affinity-mask-server-configuration-option.md) </span><span class="sxs-lookup"><span data-stu-id="67911-156">[affinity mask Server Configuration Option](affinity-mask-server-configuration-option.md) </span></span>  
 <span data-ttu-id="67911-157">[RECONFIGURE&#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="67911-157">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="67911-158">[서버 구성 옵션&#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="67911-158">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 <span data-ttu-id="67911-159">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="67911-159">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span></span>  
 <span data-ttu-id="67911-160">[CREATE INDEX&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="67911-160">[CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql) </span></span>  
 <span data-ttu-id="67911-161">[ALTER INDEX&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="67911-161">[ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql) </span></span>  
 <span data-ttu-id="67911-162">[ALTER TABLE&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="67911-162">[ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql) </span></span>  
 <span data-ttu-id="67911-163">[DBCC CHECKTABLE &#40;Transact-sql&#41;](/sql/t-sql/database-console-commands/dbcc-checktable-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="67911-163">[DBCC CHECKTABLE &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-checktable-transact-sql) </span></span>  
 <span data-ttu-id="67911-164">[DBCC CHECKDB &#40;Transact-sql&#41;](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="67911-164">[DBCC CHECKDB &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) </span></span>  
 <span data-ttu-id="67911-165">[DBCC CHECKFILEGROUP &#40;Transact-sql&#41;](/sql/t-sql/database-console-commands/dbcc-checkfilegroup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="67911-165">[DBCC CHECKFILEGROUP &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-checkfilegroup-transact-sql) </span></span>  
 <span data-ttu-id="67911-166">[병렬 인덱스 작업 구성](../../relational-databases/indexes/configure-parallel-index-operations.md) </span><span class="sxs-lookup"><span data-stu-id="67911-166">[Configure Parallel Index Operations](../../relational-databases/indexes/configure-parallel-index-operations.md) </span></span>  
 <span data-ttu-id="67911-167">[쿼리 힌트&#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-query) </span><span class="sxs-lookup"><span data-stu-id="67911-167">[Query Hints &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-query) </span></span>  
 [<span data-ttu-id="67911-168">인덱스 옵션 설정</span><span class="sxs-lookup"><span data-stu-id="67911-168">Set Index Options</span></span>](../../relational-databases/indexes/set-index-options.md)  
  
  
