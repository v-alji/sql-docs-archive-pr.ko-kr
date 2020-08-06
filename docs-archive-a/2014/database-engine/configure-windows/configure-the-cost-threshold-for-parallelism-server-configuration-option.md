---
title: cost threshold for parallelism 서버 구성 옵션 구성 | Microsoft Docs
ms.custom: ''
ms.date: 10/26/2015
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- cost threshold for parallelism option
ms.assetid: dad21bee-fe28-41f6-9d2f-e6ababfaf9db
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 675055a753e84ace3a4fcb44b41b8c914326c5c6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647240"
---
# <a name="configure-the-cost-threshold-for-parallelism-server-configuration-option"></a><span data-ttu-id="516fe-102">cost threshold for parallelism 서버 구성 옵션 구성</span><span class="sxs-lookup"><span data-stu-id="516fe-102">Configure the cost threshold for parallelism Server Configuration Option</span></span>
  <span data-ttu-id="516fe-103">이 항목에서는 **또는** 을 사용하여 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 에서 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 병렬 처리에 대한 비용 임계값 [!INCLUDE[tsql](../../includes/tsql-md.md)]서버 구성 옵션을 구성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="516fe-103">This topic describes how to configure the **cost threshold for parallelism** server configuration option in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="516fe-104">**cost threshold for parallelism** 옵션은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가 쿼리에 대한 병렬 계획을 만들고 실행하는 임계값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="516fe-104">The **cost threshold for parallelism** option specifies the threshold at which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] creates and runs parallel plans for queries.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="516fe-105">는 동일한 쿼리의 직렬 계획을 실행하는 데 드는 예상 비용이 **병렬 처리에 대한 비용 임계값**에 설정된 값보다 높은 경우에만 해당 쿼리에 대한 병렬 계획을 만들고 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="516fe-105">creates and runs a parallel plan for a query only when the estimated cost to run a serial plan for the same query is higher than the value set in **cost threshold for parallelism**.</span></span> <span data-ttu-id="516fe-106">이 비용은 특정 하드웨어 구성에서 직렬 계획을 실행하는 데 필요한 예상 경과 시간(초)을 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="516fe-106">The cost refers to an estimated elapsed time in seconds required to run the serial plan on a specific hardware configuration.</span></span> <span data-ttu-id="516fe-107">**병렬 처리에 대한 비용 임계값** 옵션은 0에서 32767 사이의 모든 값으로 설정할 수 있으며</span><span class="sxs-lookup"><span data-stu-id="516fe-107">The **cost threshold for parallelism** option can be set to any value from 0 through 32767.</span></span> <span data-ttu-id="516fe-108">기본값은 5입니다.</span><span class="sxs-lookup"><span data-stu-id="516fe-108">The default value is 5.</span></span>  
  
 <span data-ttu-id="516fe-109">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="516fe-109">**In This Topic**</span></span>  
  
-   <span data-ttu-id="516fe-110">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="516fe-110">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="516fe-111">제한 사항</span><span class="sxs-lookup"><span data-stu-id="516fe-111">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="516fe-112">권장 사항</span><span class="sxs-lookup"><span data-stu-id="516fe-112">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="516fe-113">보안</span><span class="sxs-lookup"><span data-stu-id="516fe-113">Security</span></span>](#Security)  
  
-   <span data-ttu-id="516fe-114">**병렬 처리에 대한 비용 임계값 옵션을 구성하려면:**</span><span class="sxs-lookup"><span data-stu-id="516fe-114">**To configure the cost threshold for parallelism option, using:**</span></span>  
  
     [<span data-ttu-id="516fe-115">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="516fe-115">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="516fe-116">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="516fe-116">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="516fe-117">**후속 작업:**  [병렬 처리에 대한 비용 임계값 옵션을 구성한 후](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="516fe-117">**Follow Up:**  [After you configure the cost threshold for parallelism option](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="516fe-118">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="516fe-118">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="516fe-119">제한 사항</span><span class="sxs-lookup"><span data-stu-id="516fe-119">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="516fe-120">이 비용은 특정 하드웨어 구성에서 직렬 계획을 실행하는 데 필요한 예상 경과 시간(초)을 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="516fe-120">The cost refers to an estimated elapsed time in seconds required to run the serial plan on a specific hardware configuration.</span></span> <span data-ttu-id="516fe-121">**cost threshold for parallelism** 은 대칭적 다중 프로세서에서만 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="516fe-121">Only set **cost threshold for parallelism** on symmetric multiprocessors.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="516fe-122">에서는 다음 조건에서 **병렬 처리에 대한 비용 임계값** 값을 무시합니다.</span><span class="sxs-lookup"><span data-stu-id="516fe-122">ignores the **cost threshold for parallelism** value under the following conditions:</span></span>  
  
    -   <span data-ttu-id="516fe-123">컴퓨터에 논리적 프로세서가 하나만 있습니다.</span><span class="sxs-lookup"><span data-stu-id="516fe-123">Your computer has only one logical processor.</span></span>  
  
    -   <span data-ttu-id="516fe-124">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 선호도 마스크 **구성 옵션 때문에** 에 단일 논리적 프로세서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="516fe-124">Only a single logical processor is available to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] because of the **affinity mask** configuration option.</span></span>  
  
    -   <span data-ttu-id="516fe-125">**병렬 처리에 대한 비용 임계값** 옵션이 1로 설정되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="516fe-125">The **max degree of parallelism** option is set to 1.</span></span>  
  
 <span data-ttu-id="516fe-126">논리적 프로세서는 운영 체제가 태스크를 전달하거나 스레드 컨텍스트를 실행할 수 있도록 허용하는 프로세서 하드웨어의 기본 단위입니다.</span><span class="sxs-lookup"><span data-stu-id="516fe-126">A logical processor is the basic unit of processor hardware that allows the operating system to dispatch a task or execute a thread context.</span></span> <span data-ttu-id="516fe-127">각 논리적 프로세서는 한 번에 하나만 스레드 컨텍스트를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="516fe-127">Each logical processor can execute only one thread context at a time.</span></span> <span data-ttu-id="516fe-128">프로세서 코어는 명령을 암호 해독하고 실행할 수 있는 기능을 제공하는 회로입니다.</span><span class="sxs-lookup"><span data-stu-id="516fe-128">The processor core is the circuitry that provides ability to decode and execute instructions.</span></span> <span data-ttu-id="516fe-129">프로세서 코어에는 하나 이상의 논리적 프로세서가 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="516fe-129">A processor core may contain one or more logical processors.</span></span> <span data-ttu-id="516fe-130">다음 [!INCLUDE[tsql](../../includes/tsql-md.md)] 쿼리를 사용하면 시스템의 CPU 정보를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="516fe-130">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] query can be used for obtaining CPU information for the system.</span></span>  
  
```  
SELECT (cpu_count / hyperthread_ratio) AS PhysicalCPUs,   
cpu_count AS logicalCPUs   
FROM sys.dm_os_sys_info  
```  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="516fe-131">권장 사항</span><span class="sxs-lookup"><span data-stu-id="516fe-131">Recommendations</span></span>  
  
-   <span data-ttu-id="516fe-132">이 옵션은 고급 옵션으로, 숙련된 데이터베이스 관리자나 공인된 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 기술 지원 담당자만 변경해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="516fe-132">This option is an advanced option and should be changed only by an experienced database administrator or certified [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] technician.</span></span>  
  
-   <span data-ttu-id="516fe-133">경우에 따라 쿼리 비용 계획이 현재 **병렬 처리에 대한 비용 임계값** 값보다 작아도 병렬 계획을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="516fe-133">In certain cases, a parallel plan may be chosen even though the query's cost plan is less than the current **cost threshold for parallelism** value.</span></span> <span data-ttu-id="516fe-134">이는 먼저 제공되는 비용 평가에 따라 병렬 계획 또는 직렬 계획을 사용할 것인지를 결정해야 전체 최적화가 완료되기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="516fe-134">This can happen because the decision to use a parallel or serial plan is based on a cost estimate provided before the full optimization is complete.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="516fe-135">보안</span><span class="sxs-lookup"><span data-stu-id="516fe-135">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="516fe-136">권한</span><span class="sxs-lookup"><span data-stu-id="516fe-136">Permissions</span></span>  
 <span data-ttu-id="516fe-137">매개 변수 없이 또는 첫 번째 매개 변수만 사용하여 **sp_configure** 를 실행할 수 있는 권한은 기본적으로 모든 사용자에게 부여됩니다.</span><span class="sxs-lookup"><span data-stu-id="516fe-137">Execute permissions on **sp_configure** with no parameters or with only the first parameter are granted to all users by default.</span></span> <span data-ttu-id="516fe-138">구성 옵션을 변경하거나 RECONFIGURE 문을 실행하는 두 매개 변수를 사용하여 **sp_configure** 를 실행하려면 사용자에게 ALTER SETTINGS 서버 수준 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="516fe-138">To execute **sp_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server-level permission.</span></span> <span data-ttu-id="516fe-139">**sysadmin** 및 **serveradmin** 고정 서버 역할은 ALTER SETTINGS 권한을 암시적으로 보유하고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="516fe-139">The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="516fe-140">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="516fe-140">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-configure-the-cost-threshold-for-parallelism-option"></a><span data-ttu-id="516fe-141">병렬 처리에 대한 비용 임계값 옵션을 구성하려면</span><span class="sxs-lookup"><span data-stu-id="516fe-141">To configure the cost threshold for parallelism option</span></span>  
  
1.  <span data-ttu-id="516fe-142">개체 탐색기에서 서버를 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="516fe-142">In Object Explorer, right-click a server and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="516fe-143">**고급** 노드를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="516fe-143">Click the **Advanced** node.</span></span>  
  
3.  <span data-ttu-id="516fe-144">**병렬 처리**에서 **병렬 처리에 대한 비용 임계값** 옵션을 원하는 값으로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="516fe-144">Under **Parallelism**, change the **CostThresholdForParallelism** option to the value you want.</span></span> <span data-ttu-id="516fe-145">0에서 32767까지의 값을 입력 또는 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="516fe-145">Type or select a value from 0 to 32767.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="516fe-146">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="516fe-146">Using Transact-SQL</span></span>  
  
#### <a name="to-configure-the-cost-threshold-for-parallelism-option"></a><span data-ttu-id="516fe-147">병렬 처리에 대한 비용 임계값 옵션을 구성하려면</span><span class="sxs-lookup"><span data-stu-id="516fe-147">To configure the cost threshold for parallelism option</span></span>  
  
1.  <span data-ttu-id="516fe-148">[!INCLUDE[ssDE](../../includes/ssde-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="516fe-148">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="516fe-149">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="516fe-149">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="516fe-150">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="516fe-150">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="516fe-151">다음 예에서는 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) 를 사용하여 `cost threshold for parallelism` 옵션의 값을 `10`(으)로 설정하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="516fe-151">This example shows how to use [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) to set the value of the `cost threshold for parallelism` option to `10`.</span></span>  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1 ;  
GO  
RECONFIGURE  
GO  
EXEC sp_configure 'cost threshold for parallelism', 10 ;  
GO  
RECONFIGURE  
GO  
```  
  
 <span data-ttu-id="516fe-152">자세한 내용은 [서버 구성 옵션&#40;SQL Server&#41;](server-configuration-options-sql-server.md)서버 구성 옵션을 보거나 구성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="516fe-152">For more information, see [Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md).</span></span>  
  
##  <a name="follow-up-after-you-configure-the-cost-threshold-for-parallelism-option"></a><a name="FollowUp"></a> <span data-ttu-id="516fe-153">후속 작업: 병렬 처리에 대한 비용 임계값 옵션을 구성한 후</span><span class="sxs-lookup"><span data-stu-id="516fe-153">Follow Up: After you configure the cost threshold for parallelism option</span></span>  
 <span data-ttu-id="516fe-154">이 설정은 서버를 다시 시작하지 않아도 즉시 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="516fe-154">The setting takes effect immediately without restarting the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="516fe-155">참고 항목</span><span class="sxs-lookup"><span data-stu-id="516fe-155">See Also</span></span>  
 <span data-ttu-id="516fe-156">[병렬 인덱스 작업 구성](../../relational-databases/indexes/configure-parallel-index-operations.md) </span><span class="sxs-lookup"><span data-stu-id="516fe-156">[Configure Parallel Index Operations](../../relational-databases/indexes/configure-parallel-index-operations.md) </span></span>  
 <span data-ttu-id="516fe-157">[쿼리 힌트&#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-query) </span><span class="sxs-lookup"><span data-stu-id="516fe-157">[Query Hints &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-query) </span></span>  
 <span data-ttu-id="516fe-158">[ALTER WORKLOAD GROUP&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-workload-group-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="516fe-158">[ALTER WORKLOAD GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-workload-group-transact-sql) </span></span>  
 <span data-ttu-id="516fe-159">[선호도 마스크 서버 구성 옵션](affinity-mask-server-configuration-option.md) </span><span class="sxs-lookup"><span data-stu-id="516fe-159">[affinity mask Server Configuration Option](affinity-mask-server-configuration-option.md) </span></span>  
 <span data-ttu-id="516fe-160">[RECONFIGURE&#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="516fe-160">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="516fe-161">[서버 구성 옵션&#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="516fe-161">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 [<span data-ttu-id="516fe-162">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="516fe-162">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
