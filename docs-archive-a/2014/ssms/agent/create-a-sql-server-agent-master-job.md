---
title: SQL Server 에이전트 마스터 작업 만들기 | Microsoft 문서
ms.custom: ''
ms.date: 04/26/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], master jobs
- jobs [SQL Server Agent], creating
- master SQL Server Agent job [SQL Server]
ms.assetid: c12ab23f-d7ee-43a5-8cd2-0a9121292bcd
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8a6503caec3f153878e360ee29ce09a5c099ade5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732251"
---
# <a name="create-a-sql-server-agent-master-job"></a><span data-ttu-id="bdb32-102">SQL Server 에이전트 마스터 작업 만들기</span><span class="sxs-lookup"><span data-stu-id="bdb32-102">Create a SQL Server Agent Master Job</span></span>
  <span data-ttu-id="bdb32-103">이 항목 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서는 또는을 사용 하 여에서 마스터 에이전트 작업을 만드는 방법에 대해 설명 합니다 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="bdb32-103">This topic describes how to create a master [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="bdb32-104">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="bdb32-104">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="bdb32-105">제한 사항</span><span class="sxs-lookup"><span data-stu-id="bdb32-105">Limitations and Restrictions</span></span>  
 <span data-ttu-id="bdb32-106">마스터 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 작업에 대한 변경 내용은 관련된 모든 대상 서버에 전파되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bdb32-106">Changes to master [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs must be propagated to all involved target servers.</span></span> <span data-ttu-id="bdb32-107">대상 서버는 해당 대상이 지정될 때까지 처음에 작업을 다운로드하지 않으므로 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 는 사용자가 대상 서버를 지정하기 전에 특정 작업에 대한 모든 작업 단계 및 작업 일정을 완료하도록 권장합니다.</span><span class="sxs-lookup"><span data-stu-id="bdb32-107">Because target servers do not initially download a job until those targets are specified, [!INCLUDE[msCoName](../../includes/msconame-md.md)] recommends that you complete all job steps and job schedules for a particular job before you specify any target servers.</span></span> <span data-ttu-id="bdb32-108">그렇지 않으면 **sp_post_msx_operation** 저장 프로시저를 실행하거나 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]를 사용하여 작업을 수정하여 대상 서버가 수정된 작업을 다시 다운로드하도록 수동으로 요청해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bdb32-108">Otherwise, you must manual request that the target servers download the modified job again, either by executing the **sp_post_msx_operation** stored procedure or modifying the job using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="bdb32-109">자세한 내용은 [sp_post_msx_operation &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-post-msx-operation-transact-sql) 또는 [작업 수정](modify-a-job.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="bdb32-109">For more information, see [sp_post_msx_operation &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-post-msx-operation-transact-sql) or [Modify a Job](modify-a-job.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="bdb32-110">보안</span><span class="sxs-lookup"><span data-stu-id="bdb32-110">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="bdb32-111">권한</span><span class="sxs-lookup"><span data-stu-id="bdb32-111">Permissions</span></span>  
 <span data-ttu-id="bdb32-112">프록시와 연관된 단계가 있는 배포된 작업은 대상 서버의 프록시 계정 컨텍스트로 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="bdb32-112">Distributed jobs that have steps which are associated with a proxy run under the context of the proxy account on the target server.</span></span> <span data-ttu-id="bdb32-113">다음 조건이 만족되는지 또는 프록시와 연관된 작업 단계가 마스터 서버에서 대상으로 다운로드되지 않는지 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="bdb32-113">Make sure that the following conditions are met or job steps that are associated with a proxy will not be downloaded from the master server to the target:</span></span>  
  
-   <span data-ttu-id="bdb32-114">레지스트리 하위 키 **\ HKEY_LOCAL_MACHINE \software\microsoft\microsoft SQL Server \\ < *instance_name*> \sql server Agent\AllowDownloadedJobsToMatchProxyName** (REG_DWORD)는 1 (true)로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bdb32-114">The registry subkey **\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<*instance_name*>\SQL Server Agent\AllowDownloadedJobsToMatchProxyName** (REG_DWORD) is set to 1 (true).</span></span> <span data-ttu-id="bdb32-115">기본적으로 이 하위 키는 0(false)으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="bdb32-115">By default, this subkey is set to 0 (false).</span></span>  
  
-   <span data-ttu-id="bdb32-116">프록시 계정이 작업 단계가 실행되는 마스터 서버 프록시 계정과 동일한 이름을 가진 대상 서버에 있는지 여부</span><span class="sxs-lookup"><span data-stu-id="bdb32-116">A proxy account exists on the target server that has the same name as the master server proxy account under which the job step runs.</span></span>  
  
 <span data-ttu-id="bdb32-117">마스터 서버에서 대상 서버로 다운로드할 때 프록시 계정을 사용하는 작업 단계가 실패한 경우 **msdb** 데이터베이스의 **sysdownloadlist** 테이블에 있는 **error_message** 열에서 다음 오류 메시지를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bdb32-117">If job steps that use proxy accounts fail when downloading them from the master server to the target server, you can check the **error_message** column in the **sysdownloadlist** table in the **msdb** database for the following error messages:</span></span>  
  
-   <span data-ttu-id="bdb32-118">"작업 단계에 프록시 계정이 필요하지만 일치하는 프록시를 대상 서버에서 사용할 수 없습니다."</span><span class="sxs-lookup"><span data-stu-id="bdb32-118">"The job step requires a proxy account, however proxy matching is disabled on the target server."</span></span> <span data-ttu-id="bdb32-119">이 오류를 해결하려면 **AllowDownloadedJobsToMatchProxyName** 레지스트리 하위 키를 1로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="bdb32-119">To resolve this error, set the **AllowDownloadedJobsToMatchProxyName** registry subkey to 1.</span></span>  
  
-   <span data-ttu-id="bdb32-120">"프록시를 찾을 수 없습니다."</span><span class="sxs-lookup"><span data-stu-id="bdb32-120">"Proxy not found."</span></span> <span data-ttu-id="bdb32-121">이 오류를 해결하려면 프록시 계정이 작업 단계가 실행되는 마스터 서버 프록시 계정과 동일한 이름을 가진 대상 서버에 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="bdb32-121">To resolve this error, make sure a proxy account exists on the target server that has the same name as the master server proxy account under which the job step runs.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="bdb32-122">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="bdb32-122">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-a-master-sql-server-agent-job"></a><span data-ttu-id="bdb32-123">마스터 SQL Server 에이전트 작업을 만들려면</span><span class="sxs-lookup"><span data-stu-id="bdb32-123">To create a master SQL Server Agent job</span></span>  
  
1.  <span data-ttu-id="bdb32-124">**개체 탐색기**에서 더하기 기호를 클릭하여 SQL Server 에이전트 작업을 만들려는 서버를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="bdb32-124">In the **Object Explorer**, click the plus sign to expand the server where you want to create a SQL Server Agent job.</span></span>  
  
2.  <span data-ttu-id="bdb32-125">더하기 기호를 클릭하여 **SQL Server 에이전트**를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="bdb32-125">Click the plus sign to expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="bdb32-126">**작업** 폴더를 마우스 오른쪽 단추로 클릭하고 **새 작업...** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="bdb32-126">Right-click the **Jobs** folder and select **New Job...**.</span></span>  
  
4.  <span data-ttu-id="bdb32-127">**새 작업** 대화 상자의 **일반** 페이지에서 작업의 일반 속성을 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="bdb32-127">In the **New Job** dialog box, on the **General** page, modify the general properties of the job.</span></span> <span data-ttu-id="bdb32-128">이 페이지에서 사용할 수 있는 옵션에 대 한 자세한 내용은 [작업 속성 및 새 작업 &#40;일반 페이지](../../integration-services/general-page-of-integration-services-designers-options.md) 를 참조 하세요&#41;</span><span class="sxs-lookup"><span data-stu-id="bdb32-128">For more information on the available options on this page, see [Job Properties and New Job &#40;General Page&#41;](../../integration-services/general-page-of-integration-services-designers-options.md)</span></span>  
  
5.  <span data-ttu-id="bdb32-129">**단계** 페이지에서 작업 단계를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="bdb32-129">On the **Steps** page, organize the job steps.</span></span> <span data-ttu-id="bdb32-130">이 페이지에서 사용할 수 있는 옵션에 대 한 자세한 내용은 [작업 속성: 새 작업 &#40;단계 페이지](job-properties-new-job-steps-page.md) 를 참조 하세요&#41;</span><span class="sxs-lookup"><span data-stu-id="bdb32-130">For more information on the available options on this page, see [Job Properties:New Job &#40;Steps Page&#41;](job-properties-new-job-steps-page.md)</span></span>  
  
6.  <span data-ttu-id="bdb32-131">**일정** 페이지에서 작업 일정을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="bdb32-131">On the **Schedules** page, organize schedules for the job.</span></span> <span data-ttu-id="bdb32-132">이 페이지에서 사용할 수 있는 옵션에 대 한 자세한 내용은 [작업 속성: 새 작업 &#40;일정 페이지](job-properties-new-job-schedules-page.md) 를 참조 하세요&#41;</span><span class="sxs-lookup"><span data-stu-id="bdb32-132">For more information on the available options on this page, see [Job Properties: New Job &#40;Schedules Page&#41;](job-properties-new-job-schedules-page.md)</span></span>  
  
7.  <span data-ttu-id="bdb32-133">**경고** 페이지에서 작업에 대한 경고를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="bdb32-133">On the **Alerts** page, organize the alerts for the job.</span></span> <span data-ttu-id="bdb32-134">이 페이지에서 사용할 수 있는 옵션에 대 한 자세한 내용은 [작업 속성: 새 작업 &#40;경고 페이지](job-properties-new-job-alerts-page.md) 를 참조 하세요&#41;</span><span class="sxs-lookup"><span data-stu-id="bdb32-134">For more information on the available options on this page, see [Job Properties: New Job &#40;Alerts Page&#41;](job-properties-new-job-alerts-page.md)</span></span>  
  
8.  <span data-ttu-id="bdb32-135">**알림** 페이지에서 작업이 완료될 때 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트가 수행할 동작을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="bdb32-135">On the **Notifications** page, set actions for [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to perform when the job completes.</span></span> <span data-ttu-id="bdb32-136">이 페이지에서 사용할 수 있는 옵션에 대 한 자세한 내용은 [작업 속성: 새 작업 &#40;알림 페이지&#41;](job-properties-new-job-notifications-page.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="bdb32-136">For more information on the available options on this page, see [Job Properties: New Job &#40;Notifications Page&#41;](job-properties-new-job-notifications-page.md).</span></span>  
  
9. <span data-ttu-id="bdb32-137">**대상** 페이지에서 작업의 대상 서버를 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="bdb32-137">On the **Targets** page, manage the target servers for the job.</span></span> <span data-ttu-id="bdb32-138">이 페이지에서 사용할 수 있는 옵션에 대 한 자세한 내용은 [작업 속성: 새 작업 &#40;대상 페이지&#41;](job-properties-new-job-targets-page.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="bdb32-138">For more information on the available options on this page, see [Job Properties: New Job &#40;Targets Page&#41;](job-properties-new-job-targets-page.md).</span></span>  
  
10. <span data-ttu-id="bdb32-139">완료되었으면 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bdb32-139">When finished, click **OK**.</span></span>  
  

  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="bdb32-140">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="bdb32-140">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-master-sql-server-agent-job"></a><span data-ttu-id="bdb32-141">마스터 SQL Server 에이전트 작업을 만들려면</span><span class="sxs-lookup"><span data-stu-id="bdb32-141">To create a master SQL Server Agent job</span></span>  
  
1.  <span data-ttu-id="bdb32-142">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="bdb32-142">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="bdb32-143">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bdb32-143">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="bdb32-144">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bdb32-144">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE msdb ;  
    GO  
    -- Adds a new job executed by the SQLServerAgent service called 'Weekly Sales Data Backup'  
    EXEC dbo.sp_add_job  
        @job_name = N'Weekly Sales Data Backup' ;  
    GO  
    -- Adds a step (operation) to the 'Weekly Sales Data Backup' job.  
    EXEC sp_add_jobstep  
        @job_name = N'Weekly Sales Data Backup',  
        @step_name = N'Set database to read only',  
        @subsystem = N'TSQL',  
        @command = N'ALTER DATABASE SALES SET READ_ONLY',   
        @retry_attempts = 5,  
        @retry_interval = 5 ;  
    GO  
    -- Creates a schedule called RunOnce  
    EXEC dbo.sp_add_schedule  
        @schedule_name = N'RunOnce',  
        @freq_type = 1,  
        @active_start_time = 233000 ;  
    USE msdb ;  
    GO  
    -- Sets the 'RunOnce' schedule to the "Weekly Sales Data Backup' Job  
    EXEC sp_attach_schedule  
       @job_name = N'Weekly Sales Data Backup',  
       @schedule_name = N'RunOnce';  
    GO  
    -- assigns the multiserver job Weekly Sales Backups to the server SEATTLE2  
    -- assumes that SEATTLE2 is registered as a target server for the current instance.  
    EXEC dbo.sp_add_jobserver  
        @job_name = N'Weekly Sales Data Backups',  
        @server_name = N'SEATTLE2' ;  
    GO  
    ```  
  
 <span data-ttu-id="bdb32-145">자세한 내용은 다음을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="bdb32-145">For more information, see:</span></span>  
  
-   [<span data-ttu-id="bdb32-146">sp_add_job&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="bdb32-146">sp_add_job &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-add-job-transact-sql)  
  
-   [<span data-ttu-id="bdb32-147">sp_add_jobstep&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="bdb32-147">sp_add_jobstep &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql)  
  
-   [<span data-ttu-id="bdb32-148">sp_add_schedule&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="bdb32-148">sp_add_schedule &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-add-schedule-transact-sql)  
  
-   [<span data-ttu-id="bdb32-149">sp_attach_schedule&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="bdb32-149">sp_attach_schedule &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-attach-schedule-transact-sql)  
  
-   [<span data-ttu-id="bdb32-150">Transact-sql&#41;sp_add_jobserver &#40;</span><span class="sxs-lookup"><span data-stu-id="bdb32-150">sp_add_jobserver &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-add-jobserver-transact-sql)  
  

  
  
