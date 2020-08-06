---
title: 작업 만들기 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], creating
- SQL Server Agent jobs, creating
ms.assetid: b35af2b6-6594-40d1-9861-4d5dd906048c
author: stevestein
ms.author: sstein
ms.openlocfilehash: de74f032924fbb0b6643bd8f3d482481ffb1f983
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639230"
---
# <a name="create-a-job"></a><span data-ttu-id="70be2-102">작업 만들기</span><span class="sxs-lookup"><span data-stu-id="70be2-102">Create a Job</span></span>
  <span data-ttu-id="70be2-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 또는 SMO(SQL Server 관리 개체)를 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)]에서 SQL Server 에이전트 작업을 만드는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="70be2-103">This topic describes how to create a SQL Server Agent job in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)], or SQL Server Management Objects (SMO).</span></span>  
  
 <span data-ttu-id="70be2-104">운영자에게 전송할 수 있는 작업 단계, 일정, 경고 및 알림을 추가하려면 참조 섹션에 있는 항목에 대한 링크를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="70be2-104">To add job steps, schedules, alerts, and notifications that can be sent to operators, see the links to topics in the See Also section.</span></span>  
  
-   <span data-ttu-id="70be2-105">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="70be2-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="70be2-106">제한 사항</span><span class="sxs-lookup"><span data-stu-id="70be2-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="70be2-107">보안</span><span class="sxs-lookup"><span data-stu-id="70be2-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="70be2-108">**다음을 사용하여 작업을 만듭니다.**</span><span class="sxs-lookup"><span data-stu-id="70be2-108">**To create a job, using:**</span></span>  
  
     <span data-ttu-id="70be2-109">[SQL Server Management Studio](#SSMSProcedure),</span><span class="sxs-lookup"><span data-stu-id="70be2-109">[SQL Server Management Studio](#SSMSProcedure),</span></span>  
  
     [<span data-ttu-id="70be2-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="70be2-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="70be2-111">SQL Server 관리 개체</span><span class="sxs-lookup"><span data-stu-id="70be2-111">SQL Server Management Objects</span></span>](#SMOProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="70be2-112">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="70be2-112">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="70be2-113">제한 사항</span><span class="sxs-lookup"><span data-stu-id="70be2-113">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="70be2-114">작업을 만들려면 사용자가 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 고정 데이터베이스 역할이나 **sysadmin** 고정 서버 역할 중 하나의 멤버여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="70be2-114">To create a job, a user must be a member of one of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent fixed database roles or the **sysadmin** fixed server role.</span></span> <span data-ttu-id="70be2-115">작업은 소유자나 **sysadmin** 역할의 멤버만 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="70be2-115">A job can be edited only by its owner or members of the **sysadmin** role.</span></span> <span data-ttu-id="70be2-116">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 고정 데이터베이스 역할에 대한 자세한 내용은 [SQL Server 에이전트 고정 데이터베이스 역할](sql-server-agent-fixed-database-roles.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="70be2-116">For more information about the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent fixed database roles, see [SQL Server Agent Fixed Database Roles](sql-server-agent-fixed-database-roles.md).</span></span>  
  
-   <span data-ttu-id="70be2-117">다른 로그인에 작업을 할당한다고 해서 새 소유자가 작업을 성공적으로 실행할 수 있는 충분한 권한을 가진다고 보장할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="70be2-117">Assigning a job to another login does not guarantee that the new owner has sufficient permission to run the job successfully.</span></span>  
  
-   <span data-ttu-id="70be2-118">로컬 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트가 로컬 작업을 캐시하므로</span><span class="sxs-lookup"><span data-stu-id="70be2-118">Local jobs are cached by the local [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.</span></span> <span data-ttu-id="70be2-119">수정 내용이 있을 경우 이 내용은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트에서 작업을 다시 캐시하도록 암시적으로 강제 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="70be2-119">Therefore, any modifications implicitly force [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to re-cache the job.</span></span> <span data-ttu-id="70be2-120">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sp_add_jobserver **가 호출될 때까지는** 에이전트가 작업을 캐시하지 않으므로 마지막에 **sp_add_jobserver** 를 호출하는 것이 효율적입니다.</span><span class="sxs-lookup"><span data-stu-id="70be2-120">Because [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent does not cache the job until **sp_add_jobserver** is called, it is more efficient to call **sp_add_jobserver** last.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="70be2-121">보안</span><span class="sxs-lookup"><span data-stu-id="70be2-121">Security</span></span>  
  
-   <span data-ttu-id="70be2-122">작업 소유자를 변경하려면 시스템 관리자여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="70be2-122">You must be a system administrator to change the owner of a job.</span></span>  
  
-   <span data-ttu-id="70be2-123">보안을 위해 작업 소유자나 **sysadmin** 역할의 멤버만 작업 정의를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="70be2-123">For security reasons, only the job owner or a member of the **sysadmin** role can change the definition of the job.</span></span> <span data-ttu-id="70be2-124">**sysadmin** 고정 서버 역할의 멤버만 작업 소유권을 다른 사용자에게 할당할 수 있으며 작업 소유자가 아니어도 모든 작업을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="70be2-124">Only members of the **sysadmin** fixed server role can assign job ownership to other users, and they can run any job, regardless of the job owner.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="70be2-125">**sysadmin** 고정 서버 역할의 멤버가 아닌 사용자로 작업 소유권을 변경하고 이 작업이 프록시 계정을 필요로 하는 작업 단계를 실행 중이면(예: [!INCLUDE[ssIS](../../includes/ssis-md.md)] 패키지 실행) 사용자가 해당 프록시 계정에 액세스할 수 있어야 작업이 실패하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="70be2-125">If you change job ownership to a user who is not a member of the **sysadmin** fixed server role, and the job is executing job steps that require proxy accounts (for example, [!INCLUDE[ssIS](../../includes/ssis-md.md)] package execution), make sure that the user has access to that proxy account or else the job will fail.</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="70be2-126">권한</span><span class="sxs-lookup"><span data-stu-id="70be2-126">Permissions</span></span>  
 <span data-ttu-id="70be2-127">자세한 내용은 [SQL Server 에이전트 보안 구현](implement-sql-server-agent-security.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="70be2-127">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="70be2-128">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="70be2-128">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-a-sql-server-agent-job"></a><span data-ttu-id="70be2-129">SQL Server 에이전트 작업을 만들려면</span><span class="sxs-lookup"><span data-stu-id="70be2-129">To create a SQL Server Agent job</span></span>  
  
1.  <span data-ttu-id="70be2-130">**개체 탐색기**에서 더하기 기호를 클릭하여 SQL Server 에이전트 작업을 만들려는 서버를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="70be2-130">In the **Object Explorer**, click the plus sign to expand the server where you want to create a SQL Server Agent job.</span></span>  
  
2.  <span data-ttu-id="70be2-131">더하기 기호를 클릭하여 **SQL Server 에이전트**를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="70be2-131">Click the plus sign to expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="70be2-132">**작업** 폴더를 마우스 오른쪽 단추로 클릭하고 **새 작업...** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="70be2-132">Right-click the **Jobs** folder and select **New Job...**.</span></span>  
  
4.  <span data-ttu-id="70be2-133">**새 작업** 대화 상자의 **일반** 페이지에서 작업의 일반 속성을 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="70be2-133">In the **New Job** dialog box, on the **General** page, modify the general properties of the job.</span></span> <span data-ttu-id="70be2-134">이 페이지에서 사용할 수 있는 옵션에 대 한 자세한 내용은 [작업 속성 및 새 작업 &#40;일반 페이지](../../integration-services/general-page-of-integration-services-designers-options.md) 를 참조 하세요&#41;</span><span class="sxs-lookup"><span data-stu-id="70be2-134">For more information on the available options on this page, see [Job Properties and New Job &#40;General Page&#41;](../../integration-services/general-page-of-integration-services-designers-options.md)</span></span>  
  
5.  <span data-ttu-id="70be2-135">**단계** 페이지에서 작업 단계를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="70be2-135">On the **Steps** page, organize the job steps.</span></span> <span data-ttu-id="70be2-136">이 페이지에서 사용할 수 있는 옵션에 대 한 자세한 내용은 [작업 속성: 새 작업 &#40;단계 페이지](job-properties-new-job-steps-page.md) 를 참조 하세요&#41;</span><span class="sxs-lookup"><span data-stu-id="70be2-136">For more information on the available options on this page, see [Job Properties:New Job &#40;Steps Page&#41;](job-properties-new-job-steps-page.md)</span></span>  
  
6.  <span data-ttu-id="70be2-137">**일정** 페이지에서 작업 일정을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="70be2-137">On the **Schedules** page, organize schedules for the job.</span></span> <span data-ttu-id="70be2-138">이 페이지에서 사용할 수 있는 옵션에 대 한 자세한 내용은 [작업 속성: 새 작업 &#40;일정 페이지](job-properties-new-job-schedules-page.md) 를 참조 하세요&#41;</span><span class="sxs-lookup"><span data-stu-id="70be2-138">For more information on the available options on this page, see [Job Properties: New Job &#40;Schedules Page&#41;](job-properties-new-job-schedules-page.md)</span></span>  
  
7.  <span data-ttu-id="70be2-139">**경고** 페이지에서 작업에 대한 경고를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="70be2-139">On the **Alerts** page, organize the alerts for the job.</span></span> <span data-ttu-id="70be2-140">이 페이지에서 사용할 수 있는 옵션에 대 한 자세한 내용은 [작업 속성: 새 작업 &#40;경고 페이지](job-properties-new-job-alerts-page.md) 를 참조 하세요&#41;</span><span class="sxs-lookup"><span data-stu-id="70be2-140">For more information on the available options on this page, see [Job Properties: New Job &#40;Alerts Page&#41;](job-properties-new-job-alerts-page.md)</span></span>  
  
8.  <span data-ttu-id="70be2-141">**알림** 페이지에서 작업이 완료될 때 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트가 수행할 동작을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="70be2-141">On the **Notifications** page, set actions for [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to perform when the job completes.</span></span> <span data-ttu-id="70be2-142">이 페이지에서 사용할 수 있는 옵션에 대 한 자세한 내용은 [작업 속성: 새 작업 &#40;알림 페이지&#41;](job-properties-new-job-notifications-page.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="70be2-142">For more information on the available options on this page, see [Job Properties: New Job &#40;Notifications Page&#41;](job-properties-new-job-notifications-page.md).</span></span>  
  
9. <span data-ttu-id="70be2-143">**대상** 페이지에서 작업의 대상 서버를 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="70be2-143">On the **Targets** page, manage the target servers for the job.</span></span> <span data-ttu-id="70be2-144">이 페이지에서 사용할 수 있는 옵션에 대 한 자세한 내용은 [작업 속성: 새 작업 &#40;대상 페이지&#41;](job-properties-new-job-targets-page.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="70be2-144">For more information on the available options on this page, see [Job Properties: New Job &#40;Targets Page&#41;](job-properties-new-job-targets-page.md).</span></span>  
  
10. <span data-ttu-id="70be2-145">완료되었으면 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="70be2-145">When finished, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="70be2-146">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="70be2-146">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-sql-server-agent-job"></a><span data-ttu-id="70be2-147">SQL Server 에이전트 작업을 만들려면</span><span class="sxs-lookup"><span data-stu-id="70be2-147">To create a SQL Server Agent job</span></span>  
  
1.  <span data-ttu-id="70be2-148">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="70be2-148">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="70be2-149">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="70be2-149">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="70be2-150">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="70be2-150">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```sql
    USE msdb ;  
    GO  
    EXEC dbo.sp_add_job  
        @job_name = N'Weekly Sales Data Backup' ;  
    GO  
    EXEC sp_add_jobstep  
        @job_name = N'Weekly Sales Data Backup',  
        @step_name = N'Set database to read only',  
        @subsystem = N'TSQL',  
        @command = N'ALTER DATABASE SALES SET READ_ONLY',   
        @retry_attempts = 5,  
        @retry_interval = 5 ;  
    GO  
    EXEC dbo.sp_add_schedule  
        @schedule_name = N'RunOnce',  
        @freq_type = 1,  
        @active_start_time = 233000 ;  
    USE msdb ;  
    GO  
    EXEC sp_attach_schedule  
       @job_name = N'Weekly Sales Data Backup',  
       @schedule_name = N'RunOnce';  
    GO  
    EXEC dbo.sp_add_jobserver  
        @job_name = N'Weekly Sales Data Backup';  
    GO  
    ```  
  
 <span data-ttu-id="70be2-151">자세한 내용은 다음을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="70be2-151">For more information, see:</span></span>  
  
-   [<span data-ttu-id="70be2-152">sp_add_job&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="70be2-152">sp_add_job &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-add-job-transact-sql)  
  
-   [<span data-ttu-id="70be2-153">sp_add_jobstep&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="70be2-153">sp_add_jobstep &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql)  
  
-   [<span data-ttu-id="70be2-154">sp_add_schedule&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="70be2-154">sp_add_schedule &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-add-schedule-transact-sql)  
  
-   [<span data-ttu-id="70be2-155">sp_attach_schedule&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="70be2-155">sp_attach_schedule &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-attach-schedule-transact-sql)  
  
-   [<span data-ttu-id="70be2-156">Transact-sql&#41;sp_add_jobserver &#40;</span><span class="sxs-lookup"><span data-stu-id="70be2-156">sp_add_jobserver &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-add-jobserver-transact-sql)  
  
##  <a name="using-sql-server-management-objects"></a><a name="SMOProcedure"></a><span data-ttu-id="70be2-157">SQL Server 관리 개체 사용</span><span class="sxs-lookup"><span data-stu-id="70be2-157">Using SQL Server Management Objects</span></span>  
 <span data-ttu-id="70be2-158">**SQL Server 에이전트 작업을 만들려면**</span><span class="sxs-lookup"><span data-stu-id="70be2-158">**To create a SQL Server Agent job**</span></span>  
  
 <span data-ttu-id="70be2-159">Visual Basic, Visual C#, PowerShell 등 선택한 프로그래밍 언어를 사용하여 `Create` 클래스의 `Job` 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="70be2-159">Call the `Create` method of the `Job` class by using a programming language that you choose, such as Visual Basic, Visual C#, or PowerShell.</span></span> <span data-ttu-id="70be2-160">예제 코드를 보려면 [SQL Server 에이전트에서 자동 관리 태스크 예약](sql-server-agent.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="70be2-160">For example code, see [Scheduling Automatic Administrative Tasks in SQL Server Agent](sql-server-agent.md).</span></span>  
  
##  <a name="SSMSProc2"></a>  
