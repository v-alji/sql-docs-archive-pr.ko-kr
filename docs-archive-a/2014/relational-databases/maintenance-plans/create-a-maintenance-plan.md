---
title: 유지 관리 계획 만들기 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- maintenance plans [SQL Server], creating
ms.assetid: a945cb65-ba7a-42f4-bbd9-6ec675745523
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 3df0c1cd06427deb051a9c4214d03084b44c6f9b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653357"
---
# <a name="create-a-maintenance-plan"></a><span data-ttu-id="0bdc0-102">유지 관리 계획 만들기</span><span class="sxs-lookup"><span data-stu-id="0bdc0-102">Create a Maintenance Plan</span></span>
  <span data-ttu-id="0bdc0-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 에서 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 또는 [!INCLUDE[tsql](../../includes/tsql-md.md)]을 사용하여 단일 서버 또는 다중 서버 유지 관리 계획을 만드는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="0bdc0-103">This topic describes how to create a single server or multiserver maintenance plan in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="0bdc0-104">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]를 사용하면 유지 관리 계획 마법사나 디자인 화면을 통해 이러한 유지 관리 계획을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0bdc0-104">Using [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], you can create these maintenance plans in one of two ways: by either using the Maintenance Plan Wizard or the design surface.</span></span> <span data-ttu-id="0bdc0-105">기본 유지 관리 계획을 만들 때는 마법사가 적합한 반면 디자인 화면을 사용하여 계획을 만들면 워크플로의 향상된 기능을 활용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0bdc0-105">The Wizard is best for creating basic maintenance plans, while creating a plan using the design surface allows you to utilize enhanced workflow.</span></span>  
  
 <span data-ttu-id="0bdc0-106">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="0bdc0-106">**In This Topic**</span></span>  
  
-   <span data-ttu-id="0bdc0-107">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="0bdc0-107">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="0bdc0-108">제한 사항</span><span class="sxs-lookup"><span data-stu-id="0bdc0-108">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="0bdc0-109">보안</span><span class="sxs-lookup"><span data-stu-id="0bdc0-109">Security</span></span>](#Security)  
  
-   <span data-ttu-id="0bdc0-110">**유지 관리 계획을 만들려면:**</span><span class="sxs-lookup"><span data-stu-id="0bdc0-110">**To create a maintenance plan, using:**</span></span>  
  
     [<span data-ttu-id="0bdc0-111">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="0bdc0-111">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="0bdc0-112">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="0bdc0-112">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="0bdc0-113">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="0bdc0-113">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="0bdc0-114">제한 사항</span><span class="sxs-lookup"><span data-stu-id="0bdc0-114">Limitations and Restrictions</span></span>  
 <span data-ttu-id="0bdc0-115">다중 서버 유지 관리 계획을 만들려면 하나의 마스터 서버 및 하나 이상의 대상 서버가 있는 다중 서버 환경을 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0bdc0-115">To create a multiserver maintenance plan, a multiserver environment containing one master server and one or more target servers must be configured.</span></span> <span data-ttu-id="0bdc0-116">다중 서버 유지 관리 계획은 마스터 서버에서 만들고 유지 관리해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0bdc0-116">Multiserver maintenance plans must be created and maintained on the master server.</span></span> <span data-ttu-id="0bdc0-117">이러한 계획을 대상 서버에서 볼 수 있지만 유지 관리할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0bdc0-117">These plans can be viewed, but not maintained, on target servers.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="0bdc0-118">보안</span><span class="sxs-lookup"><span data-stu-id="0bdc0-118">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="0bdc0-119">권한</span><span class="sxs-lookup"><span data-stu-id="0bdc0-119">Permissions</span></span>  
 <span data-ttu-id="0bdc0-120">유지 관리 계획을 만들거나 관리하려면 **sysadmin** 고정 서버 역할의 멤버여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0bdc0-120">To create or manage Maintenance Plans, you must be a member of the **sysadmin** fixed server role.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="0bdc0-121">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="0bdc0-121">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-a-maintenance-plan-using-the-maintenance-plan-wizard"></a><span data-ttu-id="0bdc0-122">유지 관리 계획 마법사를 사용하여 유지 관리 계획을 만들려면</span><span class="sxs-lookup"><span data-stu-id="0bdc0-122">To create a maintenance plan using the Maintenance Plan Wizard</span></span>  
  
1.  <span data-ttu-id="0bdc0-123">개체 탐색기에서 더하기 기호를 클릭하여 유지 관리 계획을 만들 서버를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="0bdc0-123">In Object Explorer, click the plus sign to expand the server where you want to create a maintenance plan.</span></span>  
  
2.  <span data-ttu-id="0bdc0-124">더하기 기호를 클릭하여 **관리** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="0bdc0-124">Click the plus sign to expand the **Management** folder.</span></span>  
  
3.  <span data-ttu-id="0bdc0-125">**유지 관리 계획** 폴더를 마우스 오른쪽 단추로 클릭하고 **유지 관리 계획 마법사**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0bdc0-125">Right-click the **Maintenance Plans** folder and select **Maintenance Plan Wizard**.</span></span>  
  
4.  <span data-ttu-id="0bdc0-126">마법사의 단계에 따라 유지 관리 계획을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0bdc0-126">Follow the steps of the wizard to create a maintenance plan.</span></span> <span data-ttu-id="0bdc0-127">자세한 내용은 [Use the Maintenance Plan Wizard](use-the-maintenance-plan-wizard.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0bdc0-127">For more information, see [Use the Maintenance Plan Wizard](use-the-maintenance-plan-wizard.md).</span></span>  
  
#### <a name="to-create-a-maintenance-plan-using-the-design-surface"></a><span data-ttu-id="0bdc0-128">디자인 화면을 사용하여 유지 관리 계획을 만들려면</span><span class="sxs-lookup"><span data-stu-id="0bdc0-128">To create a maintenance plan using the design surface</span></span>  
  
1.  <span data-ttu-id="0bdc0-129">개체 탐색기에서 더하기 기호를 클릭하여 유지 관리 계획을 만들 서버를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="0bdc0-129">In Object Explorer, click the plus sign to expand the server where you want to create a maintenance plan.</span></span>  
  
2.  <span data-ttu-id="0bdc0-130">더하기 기호를 클릭하여 **관리** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="0bdc0-130">Click the plus sign to expand the **Management** folder.</span></span>  
  
3.  <span data-ttu-id="0bdc0-131">**유지 관리 계획** 폴더를 마우스 오른쪽 단추로 클릭하고 **새 유지 관리 계획**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0bdc0-131">Right-click the **Maintenance Plans** folder and select **New Maintenance Plan**.</span></span>  
  
4.  <span data-ttu-id="0bdc0-132">[유지 관리 계획 만들기&#40;유지 관리 계획 디자인 화면&#41;](create-a-maintenance-plan-maintenance-plan-design-surface.md)의 단계에 따라 유지 관리 계획을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0bdc0-132">Create a maintenance plan following the steps in [Create a Maintenance Plan &#40;Maintenance Plan Design Surface&#41;](create-a-maintenance-plan-maintenance-plan-design-surface.md).</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="0bdc0-133">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="0bdc0-133">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-maintenance-plan"></a><span data-ttu-id="0bdc0-134">유지 관리 계획을 만들려면</span><span class="sxs-lookup"><span data-stu-id="0bdc0-134">To create a maintenance plan</span></span>  
  
1.  <span data-ttu-id="0bdc0-135">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="0bdc0-135">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="0bdc0-136">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0bdc0-136">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="0bdc0-137">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0bdc0-137">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE msdb;  
    GO  
    --  Adds a new job, executed by the SQL Server Agent service, called "HistoryCleanupTask_1".  
    EXEC dbo.sp_add_job  
       @job_name = N'HistoryCleanupTask_1',   
       @enabled = 1,   
       @description = N'Clean up old task history' ;   
    GO  
    -- Adds a job step for reorganizing all of the indexes in the HumanResources.Employee table to the HistoryCleanupTask_1 job.   
    EXEC dbo.sp_add_jobstep  
        @job_name = N'HistoryCleanupTask_1',   
        @step_name = N'Reorganize all indexes on HumanResources.Employee table',   
        @subsystem = N'TSQL',   
        @command = N'USE AdventureWorks2012  
    GO  
    ALTER INDEX AK_Employee_LoginID ON HumanResources.Employee REORGANIZE WITH ( LOB_COMPACTION = ON )   
    GO  
    USE AdventureWorks2012  
    GO  
    ALTER INDEX AK_Employee_NationalIDNumber ON HumanResources.Employee REORGANIZE WITH ( LOB_COMPACTION = ON )   
    GO  
    USE AdventureWorks2012  
    GO  
    ALTER INDEX AK_Employee_rowguid ON HumanResources.Employee REORGANIZE WITH ( LOB_COMPACTION = ON )   
    GO  
    USE AdventureWorks2012  
    GO  
    ALTER INDEX IX_Employee_OrganizationLevel_OrganizationNode ON HumanResources.Employee REORGANIZE WITH ( LOB_COMPACTION = ON )   
    GO  
    USE AdventureWorks2012  
    GO  
    ALTER INDEX IX_Employee_OrganizationNode ON HumanResources.Employee REORGANIZE WITH ( LOB_COMPACTION = ON )   
    GO  
    USE AdventureWorks2012  
    GO  
    ALTER INDEX PK_Employee_BusinessEntityID ON HumanResources.Employee REORGANIZE WITH ( LOB_COMPACTION = ON )   
    GO  
    ',   
        @retry_attempts = 5,   
        @retry_interval = 5 ;   
    GO  
    -- Creates a schedule named RunOnce that executes every day when the time on the server is 23:00.   
    EXEC dbo.sp_add_schedule  
        @schedule_name = N'RunOnce',   
        @freq_type = 4,   
        @freq_interval = 1,   
        @active_start_time = 233000 ;   
    GO  
    -- Attaches the RunOnce schedule to the job HistoryCleanupTask_1.   
    EXEC sp_attach_schedule  
       @job_name = N'HistoryCleanupTask_1'  
       @schedule_name = N'RunOnce' ;   
    GO  
  
    ```  
  
 <span data-ttu-id="0bdc0-138">자세한 내용은 다음을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0bdc0-138">For more information, see:</span></span>  
  
-   [<span data-ttu-id="0bdc0-139">sp_add_job&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="0bdc0-139">sp_add_job &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-add-job-transact-sql)  
  
-   [<span data-ttu-id="0bdc0-140">sp_add_jobstep&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="0bdc0-140">sp_add_jobstep &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql)  
  
-   [<span data-ttu-id="0bdc0-141">sp_add_schedule&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="0bdc0-141">sp_add_schedule &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-add-schedule-transact-sql)  
  
-   [<span data-ttu-id="0bdc0-142">sp_attach_schedule&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="0bdc0-142">sp_attach_schedule &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-attach-schedule-transact-sql)  
  
  
