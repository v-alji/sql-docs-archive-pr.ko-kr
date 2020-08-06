---
title: Azure에 대 한 SQL Server Managed Backup 모니터링 | Microsoft Docs
description: 이 문서에서는 Azure에 대 한 SQL Server Managed Backup을 사용 하 여 백업의 전체 상태를 확인 하 고 오류를 식별 하는 데 사용할 수 있는 도구에 대해 설명 합니다.
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: cfb9e431-7d4c-457c-b090-6f2528b2f315
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: baec99e63c70befde0cfce76e42dd6202ebc0bad
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660136"
---
# <a name="monitor-sql-server-managed-backup-to-azure"></a><span data-ttu-id="e6fe6-103">Azure에 SQL Server 관리 백업 모니터링</span><span class="sxs-lookup"><span data-stu-id="e6fe6-103">Monitor SQL Server Managed Backup to Azure</span></span>
  [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]<span data-ttu-id="e6fe6-104">은 백업 프로세스 중에 문제 및 오류와 가능한 경우 수정 작업을 포함하는 해결책을 식별하는 기본 제공된 조치를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="e6fe6-104">has built-in measures to identify problems and errors during backup processes and remedy with corrective action when possible.</span></span>  <span data-ttu-id="e6fe6-105">그러나 사용자 개입이 필요한 특정 상황이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6fe6-105">However there are certain situations where user intervention is required.</span></span> <span data-ttu-id="e6fe6-106">이 항목에서는 백업의 전체 상태를 확인하고 해결해야 할 오류를 식별하는 데 사용할 수 있는 도구에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="e6fe6-106">This topic describes the tools that you can use to determine the overall health status of backups, and identify any errors that need to be addressed.</span></span>  
  
## <a name="overview-of-ss_smartbackup-built-in-debugging"></a><span data-ttu-id="e6fe6-107">[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 기본 제공 디버깅 개요</span><span class="sxs-lookup"><span data-stu-id="e6fe6-107">Overview of [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] Built-in Debugging</span></span>  
 <span data-ttu-id="e6fe6-108">[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]은 예약된 백업을 정기적으로 검토하고 실패한 백업을 다시 예약하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6fe6-108">The [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] periodically reviews scheduled backups and attempts to reschedule any failed backups.</span></span> <span data-ttu-id="e6fe6-109">또한 스토리지 계정을 정기적으로 폴링하여 데이터베이스의 복구 기능에 영향을 주는 로그 체인이 끊어지는 상황을 식별하고 이에 따라 새 백업을 예약합니다.</span><span class="sxs-lookup"><span data-stu-id="e6fe6-109">It polls the storage account periodically to identify breaks in log chains affecting recoverability of the database, and schedules new backups accordingly.</span></span> <span data-ttu-id="e6fe6-110">또한 Azure 제한 정책을 고려 하 고 여러 데이터베이스 백업을 관리 하는 메커니즘이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6fe6-110">It also takes into account Azure throttling policies, and has mechanisms in place to manage multiple database backups.</span></span> [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]<span data-ttu-id="e6fe6-111">은 확장 이벤트를 사용하여 모든 작업을 추적합니다.</span><span class="sxs-lookup"><span data-stu-id="e6fe6-111">uses extended events to track all activity.</span></span> <span data-ttu-id="e6fe6-112">[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 에이전트에서 사용하는 확장 이벤트 채널에는 Admin, Operational, Analytical 및 Debug가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6fe6-112">The Extended Event channels used by [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] agent include, Admin, Operational, Analytical, and Debug.</span></span> <span data-ttu-id="e6fe6-113">Admin 범주 아래에 있는 이벤트는 일반적으로 오류와 관련이 있으며 사용자 개입을 필요로 하고 기본적으로 설정되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6fe6-113">Events that fall under the Admin category usually are related to errors and require user intervention and are enabled by default.</span></span> <span data-ttu-id="e6fe6-114">Analytical 이벤트도 기본적으로 설정되어 있지만 일반적으로 사용자 개입이 필요한 오류와 관련이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e6fe6-114">Analytical events are also turned on by default, but usually are not related to errors that require user intervention.</span></span> <span data-ttu-id="e6fe6-115">Operation 이벤트는 일반적으로 정보 제공용입니다.</span><span class="sxs-lookup"><span data-stu-id="e6fe6-115">Operation events are typically informational.</span></span> <span data-ttu-id="e6fe6-116">예를 들어 운영 이벤트에는 백업 예약, 성공적인 백업 완료 등이 포함 됩니다. 디버그는 가장 자세한 정보를 표시 하며 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 문제를 확인 하 고 필요한 경우 수정 하는 데 내부적으로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e6fe6-116">For example, operational events include scheduling a backup, a successful completion of backup, etc. The Debug is the most verbose and is used internally by [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] to determine issues and correct them if required.</span></span>  
  
### <a name="configure-monitoring-parameters-for-ss_smartbackup"></a><span data-ttu-id="e6fe6-117">[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]에 대한 모니터링 매개 변수 구성</span><span class="sxs-lookup"><span data-stu-id="e6fe6-117">Configure Monitoring Parameters for [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]</span></span>  
 <span data-ttu-id="e6fe6-118">**Smart_admin sp_set_parameter** 시스템 저장 프로시저를 사용 하 여 모니터링 설정을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6fe6-118">The **smart_admin.sp_set_parameter** system stored procedure allows you to specify monitoring settings.</span></span> <span data-ttu-id="e6fe6-119">다음 섹션은 확장 이벤트를 설정하고 오류 및 경고에 대한 전자 메일 알림을 설정하는 프로세스를 안내합니다.</span><span class="sxs-lookup"><span data-stu-id="e6fe6-119">The following sections walks through the process of enabling Extended Events,  and enabling email notification for errors and warnings.</span></span>  
  
 <span data-ttu-id="e6fe6-120">**Smart_admin fn_get_parameter** 함수를 사용 하 여 특정 매개 변수 또는 구성 된 모든 매개 변수에 대 한 현재 설정을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6fe6-120">The **smart_admin.fn_get_parameter** function can be used to get the current setting for a specific parameter or all configured parameters.</span></span> <span data-ttu-id="e6fe6-121">매개 변수가 이전에 구성되지 않은 경우 함수가 값을 반환하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e6fe6-121">If the parameters have never been configured, the function does not return any values.</span></span>  
  
1.  <span data-ttu-id="e6fe6-122">[!INCLUDE[ssDE](../includes/ssde-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="e6fe6-122">Connect to the [!INCLUDE[ssDE](../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="e6fe6-123">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e6fe6-123">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="e6fe6-124">다음 예를 복사하여 쿼리 창에 붙여 넣은 후 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e6fe6-124">Copy and paste the following example into the query window and then click **Execute**.</span></span> <span data-ttu-id="e6fe6-125">이렇게 하면 확장 이벤트 및 전자 메일 알림에 대한 현재 구성이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="e6fe6-125">This will return the current configuration for Extended Events, and e-mail notifications.</span></span>  
  
```sql
Use msdb  
Go  
SELECT * FROM smart_admin.fn_get_parameter (NULL)  
GO  
```  
  
 <span data-ttu-id="e6fe6-126">자세한 내용은 [smart_admin fn_get_parameter &#40;&#41;transact-sql](/sql/relational-databases/system-functions/managed-backup-fn-get-parameter-transact-sql) 을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e6fe6-126">For more information, see [smart_admin.fn_get_parameter &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/managed-backup-fn-get-parameter-transact-sql)</span></span>  
  
### <a name="extended-events-for-monitoring"></a><span data-ttu-id="e6fe6-127">모니터링에 대한 확장 이벤트</span><span class="sxs-lookup"><span data-stu-id="e6fe6-127">Extended Events for Monitoring</span></span>  
 <span data-ttu-id="e6fe6-128">기본적으로 Admin, Operational 및 Analytical 이벤트가 설정되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6fe6-128">By default, Admin, Operational and Analytical events are turned on.</span></span> <span data-ttu-id="e6fe6-129">문제를 해결하기 위해 수동 개입이 필요한 오류를 식별할 때 Admin 이벤트가 가장 중요하고 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="e6fe6-129">Admin events are most critical, useful when identifying errors that require manual intervention to solve the problem.</span></span> <span data-ttu-id="e6fe6-130">Operational 및 Debug 이벤트를 설정할 수 있지만 이러한 이벤트는 자세한 정보를 포함하고 필터링이 필요할 수 있다는 사실을 고려하십시오.</span><span class="sxs-lookup"><span data-stu-id="e6fe6-130">You may want to turn on the operational and debug events but consider that these events are verbose and may require some filtering.</span></span> <span data-ttu-id="e6fe6-131">다음 절차에서는 확장 이벤트를 통해 기록된 이벤트를 모니터링하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="e6fe6-131">The following procedures describe how to monitor events logged through Extended Events.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="e6fe6-132">SQL 엔진용 확장 이벤트와 달리 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]은 확장 이벤트 세션 개념을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e6fe6-132">Unlike Extended Events for SQL Engine, [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] does not support Extended Event session concepts.</span></span> <span data-ttu-id="e6fe6-133">시스템 저장 프로시저와 함수는 확장 이벤트와 상호 작용하는 데 사용되는 도구입니다.</span><span class="sxs-lookup"><span data-stu-id="e6fe6-133">System stored procedures and functions are the tools used to interact with extended events.</span></span> <span data-ttu-id="e6fe6-134">또한 로그 디렉터리에서 확장 이벤트 로그를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6fe6-134">You can also view the extended event log from the log directory.</span></span>  
  
##### <a name="to-configure-and-view-extended-events"></a><span data-ttu-id="e6fe6-135">확장 이벤트를 구성하고 보려면</span><span class="sxs-lookup"><span data-stu-id="e6fe6-135">To Configure and View Extended Events</span></span>  
  
1.  <span data-ttu-id="e6fe6-136">사용 가능한 확장 이벤트 채널 및 해당 현재 상태를 보려면 다음 쿼리를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="e6fe6-136">To view available Extended Event channels and their current status by running the following query:</span></span>  
  
    ```sql
    SELECT * FROM smart_admin.fn_get_current_xevent_settings()  
    ```  
  
     <span data-ttu-id="e6fe6-137">이 쿼리의 출력은 event_name, 해당 이벤트가 구성 가능한지 여부 및 해당 이벤트가 현재 설정되어 있는지 여부를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="e6fe6-137">The output from this query will display the event_name, whether it is configurable or not, and whether it is currently enabled.</span></span>  <span data-ttu-id="e6fe6-138">자세한 내용은 [smart_admin fn_get_current_xevent_settings &#40;transact-sql&#41;](/sql/relational-databases/system-functions/managed-backup-fn-get-current-xevent-settings-transact-sql)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e6fe6-138">For more information, see [smart_admin.fn_get_current_xevent_settings &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/managed-backup-fn-get-current-xevent-settings-transact-sql).</span></span>  
  
2.  <span data-ttu-id="e6fe6-139">Debug 이벤트를 설정하려면 다음 쿼리를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="e6fe6-139">To enable debug events, run the following query:</span></span>  
  
    ```sql
    --  to enable debug events  
    Use msdb;  
    GO 
    EXEC smart_admin.sp_set_parameter 'FileRetentionDebugXevent', 'True'  
    ```  
  
     <span data-ttu-id="e6fe6-140">저장 프로시저에 대 한 자세한 내용은 [smart_admin sp_set_parameter &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/managed-backup-sp-set-parameter-transact-sql)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e6fe6-140">For more information about the stored procedure, see [smart_admin.sp_set_parameter &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/managed-backup-sp-set-parameter-transact-sql).</span></span>  
  
3.  <span data-ttu-id="e6fe6-141">기록된 이벤트를 보려면 다음 쿼리를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="e6fe6-141">To view the logged events run the following query:</span></span>  
  
    ```sql
    --  View all events in the current week  
    Use msdb;  
    Go  
    DECLARE @startofweek datetime  
    DECLARE @endofweek datetime  
    SET @startofweek = DATEADD(Day, 1-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)
    SET @endofweek = DATEADD(Day, 7-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)  
  
    EXEC smart_admin.sp_get_backup_diagnostics @begin_time = @startofweek, @end_time = @endofweek;
    ```  
  
    ```sql
    --  view all admin events  
    Use msdb;  
    Go  
    DECLARE @startofweek datetime  
    DECLARE @endofweek datetime  
    SET @startofweek = DATEADD(Day, 1-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)   
    SET @endofweek = DATEADD(Day, 7-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)  
  
    DECLARE @eventresult TABLE  
    (event_type nvarchar(512),  
    event nvarchar (512),  
    timestamp datetime  
    )  
  
    INSERT INTO @eventresult  
  
    EXEC smart_admin.sp_get_backup_diagnostics @begin_time = @startofweek, @end_time = @endofweek  
  
    SELECT * from @eventresult  
    WHERE event_type LIKE '%admin%'
    ```  
  
### <a name="aggregated-error-countshealth-status"></a><span data-ttu-id="e6fe6-142">집계된 오류 수/상태</span><span class="sxs-lookup"><span data-stu-id="e6fe6-142">Aggregated Error Counts/Health Status</span></span>  
 <span data-ttu-id="e6fe6-143">**Smart_admin fn_get_health_status** 함수는의 상태를 모니터링 하는 데 사용할 수 있는 각 범주에 대 한 집계 된 오류 개수 테이블을 반환 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6fe6-143">The **smart_admin.fn_get_health_status** function returns a table of aggregated error counts for each category that can be used to monitor the health status of [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)].</span></span> <span data-ttu-id="e6fe6-144">이 동일한 함수는 이 항목 뒷부분에서 설명하는 시스템에서 구성된 전자 메일 알림 메커니즘에서도 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="e6fe6-144">This same function is also used by the system configured e-mail notification mechanism described later in this topic.</span></span>   
<span data-ttu-id="e6fe6-145">이 집계 수는 시스템 상태를 모니터링하는 데 사용될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6fe6-145">These aggregated counts can be used to monitor system health.</span></span> <span data-ttu-id="e6fe6-146">예를 들어 number_ of_retention_loops 열이 30분에서 0인 경우 보존 관리 작업에 시간이 오래 걸리고 있거나 제대로 작동하지 않고 있을 가능성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6fe6-146">For example, if the number_ of_retention_loops column is 0 in 30 minutes, it is possible that retention management is taking long time or even not working correctly.</span></span> <span data-ttu-id="e6fe6-147">0이 아닌 오류 열은 문제를 나타내며 해당 문제를 검색하기 위해 확장 이벤트 로그를 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6fe6-147">Non-zero error columns may indicate problems and Extended Events logs should be checked to discover the problem.</span></span> <span data-ttu-id="e6fe6-148">또는 smart_admin 저장 프로시저를 호출 하 여 오류에 대 한 세부 정보를 찾을 수 **sp_get_backup_diagnostics 있습니다.**</span><span class="sxs-lookup"><span data-stu-id="e6fe6-148">Alternatively, call **smart_admin.sp_get_backup_diagnostics** stored procedure to find the details of the error.</span></span>  
  
### <a name="using-agent-notification-for-assessing-backup-status-and-health"></a><span data-ttu-id="e6fe6-149">백업 상태 확인을 위해 에이전트 알림 사용</span><span class="sxs-lookup"><span data-stu-id="e6fe6-149">Using Agent Notification for Assessing Backup Status and Health</span></span>  
 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]<span data-ttu-id="e6fe6-150">은 SQL Server 정책 기반 관리 정책에 따른 알림 메커니즘을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="e6fe6-150">includes a notification mechanism that is based on SQL Server policy based management policies.</span></span>  
  
 <span data-ttu-id="e6fe6-151">**사전 요구 사항:**</span><span class="sxs-lookup"><span data-stu-id="e6fe6-151">**Prerequisites:**</span></span>  
  
-   <span data-ttu-id="e6fe6-152">이러한 기능을 사용하려면 데이터베이스 메일이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="e6fe6-152">Database Mail is required to use this functionality.</span></span> <span data-ttu-id="e6fe6-153">SQL Server 인스턴스에 대해 DB 메일을 사용 하도록 설정 하는 방법에 대 한 자세한 내용은 [데이터베이스 메일 구성](../relational-databases/database-mail/configure-database-mail.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e6fe6-153">For more information, about how to enable DB Mail for the instance of SQL Server, see [Configure Database Mail](../relational-databases/database-mail/configure-database-mail.md).</span></span>  
  
-   <span data-ttu-id="e6fe6-154">SQL Server 에이전트 경고 시스템 속성은 데이터베이스 메일을 사용하도록 설정되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6fe6-154">SQL Server Agent Alert System properties should be set to use Database Mail.</span></span>  
  
 <span data-ttu-id="e6fe6-155">**알림 아키텍처:**</span><span class="sxs-lookup"><span data-stu-id="e6fe6-155">**Notification Architecture:**</span></span>  
  
-   <span data-ttu-id="e6fe6-156">**정책 기반 관리:** 백업 상태를 모니터링 하는 두 가지 정책: **스마트 관리 시스템 상태 정책**및 **스마트 관리 사용자 작업 상태 정책**.</span><span class="sxs-lookup"><span data-stu-id="e6fe6-156">**Policy Based Management:** Two policies are set to monitor backup health: **Smart Admin System Health Policy**, and the **Smart Admin User Action Health Policy**.</span></span> <span data-ttu-id="e6fe6-157">스마트 관리 시스템 상태 정책은 SQL 자격 증명 부족 또는 잘못된 SQL 자격 증명과 같은 중요한 오류, 연결 오류를 평가하거나 시스템 상태를 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="e6fe6-157">The Smart Admin System Health Policy evaluates critical errors like lack of or invalid SQL Credentials, connectivity errors and reports the health of the system.</span></span> <span data-ttu-id="e6fe6-158">이 경우 일반적으로 기본 문제를 해결하는 데 수동 작업이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="e6fe6-158">These typically require a manual action to correct the underlying issue.</span></span> <span data-ttu-id="e6fe6-159">스마트 관리 사용자 작업 상태 정책은 손상된 백업과 같은 경고를 평가합니다.</span><span class="sxs-lookup"><span data-stu-id="e6fe6-159">The Smart Admin User Action Health Policy evaluates warnings such as corrupted backups, and such.</span></span>  <span data-ttu-id="e6fe6-160">이 경우 작업은 필요하지 않지만 이벤트 경고만 필요할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6fe6-160">These may not require any action but just a warning of an event.</span></span> <span data-ttu-id="e6fe6-161">이러한 문제는 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 에이전트에 의해 자동으로 처리될 것입니다.</span><span class="sxs-lookup"><span data-stu-id="e6fe6-161">It is expected that such issues will be automatically taken care of by [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] agent.</span></span>  
  
-   <span data-ttu-id="e6fe6-162">**SQL Server 에이전트** 작업: 세 개의 작업 단계를 포함 하는 SQL Server 에이전트 작업을 사용 하 여 알림이 수행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e6fe6-162">**SQL Server Agent** Job: The notification is performed using a SQL Server Agent job that has three job steps.</span></span> <span data-ttu-id="e6fe6-163">첫 번째 작업 단계에서는 데이터베이스 또는 인스턴스에 대한 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]이 구성되어 있는지 여부를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="e6fe6-163">In the first job step it detects to see whether [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] is configured for a database or instance.</span></span> <span data-ttu-id="e6fe6-164">[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]사용 하도록 설정 되 고 구성 된 경우 두 번째 단계를 실행 합니다. SQL Server 정책 기반 관리 정책을 평가 하 여 상태를 평가 하는 PowerShell cmdlet을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6fe6-164">If it finds [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] enabled and configured, it executes the second step: executes a PowerShell cmdlet that assess the health status by evaluating the SQL Server policy based management policies.</span></span> <span data-ttu-id="e6fe6-165">오류 또는 경고가 발견 되 면 오류가 발생 하 고 세 번째 단계를 트리거합니다. 세 번째 단계는 오류/경고 보고서와 함께 전자 메일 알림을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="e6fe6-165">If it finds either an error or warning, it fails which then triggers the third step: The third step sends out an e-mail notification with the error/warning report.</span></span>  <span data-ttu-id="e6fe6-166">그러나 이 SQL Server 에이전트 작업은 기본적으로 설정되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e6fe6-166">However this SQL Server Agent job is not enabled by default.</span></span> <span data-ttu-id="e6fe6-167">전자 메일 알림 작업을 사용 하도록 설정 하려면 **smart_admin. sp_set_backup_parameter** 시스템 저장 프로시저를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6fe6-167">To enable the e-mail notification job, use the **smart_admin.sp_set_backup_parameter** system stored procedure.</span></span>  <span data-ttu-id="e6fe6-168">다음 절차에서 이러한 단계를 자세히 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="e6fe6-168">The following procedure describes the steps in more detail:</span></span>  
  
##### <a name="enabling-email-notification"></a><span data-ttu-id="e6fe6-169">전자 메일 알림 설정</span><span class="sxs-lookup"><span data-stu-id="e6fe6-169">Enabling Email Notification</span></span>  
  
1.  <span data-ttu-id="e6fe6-170">데이터베이스 메일 아직 구성 되지 않은 경우 [데이터베이스 메일 구성](../relational-databases/database-mail/configure-database-mail.md)에 설명 된 단계를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6fe6-170">If Database Mail is not already configured, use the steps described in [Configure Database Mail](../relational-databases/database-mail/configure-database-mail.md).</span></span>  
  
2.  <span data-ttu-id="e6fe6-171">SQL Server 경고 시스템에 대 한 메일 시스템으로 데이터베이스 설정: **SQL Server 에이전트**을 마우스 오른쪽 단추로 클릭 하 고, **경고 시스템**을 선택 하 고, **메일 프로필 사용** 확인란을 선택 하 고, **메일 시스템**으로 **데이터베이스 메일** 을 선택 하 고, 이전에 만든 메일 프로필을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6fe6-171">Set database as the Mail System for SQL Server Alert System: Right Click on **SQL Server Agent**, select **Alert System**, check the **Enable mail profile** box, Select **Database Mail** as the **Mail System**, and select a previously created Mail profile.</span></span>  
  
3.  <span data-ttu-id="e6fe6-172">쿼리 창에서 다음 쿼리를 실행하고 알림을 보낼 전자 메일 주소를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="e6fe6-172">Run the following query in a query window and provide the e-mail address where you want the notification to be sent to:</span></span>  
  
    ```sql
    Use msdb  
    Go  
    EXEC smart_admin.sp_set_parameter @parameter_name = 'SSMBackup2WANotificationEmailIds', @parameter_value = '<email address>'
    ```  
  
     <span data-ttu-id="e6fe6-173">이렇게 하면 상태를 수집하고 백업과 함께 오류 또는 문제가 발생하는 경우 알림을 보내는 데 사용되는 SQL Server 에이전트 작업이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="e6fe6-173">This creates a SQL Server Agent job that is used to gather health status and send notifications when there is an error or an issue with backups.</span></span>  
  
 <span data-ttu-id="e6fe6-174">다음은 SQL Server 에이전트 작업을 통해 DB 메일을 설정하고 전자 메일 알림을 설정하는 샘플 스크립트입니다.</span><span class="sxs-lookup"><span data-stu-id="e6fe6-174">Following is a sample script  to enable DB Mail and set up the e-mail notification through SQL Server Agent Job</span></span>  
  
```sql
-- Prereq: Make sure that SQL Server service runs in a service account that has  
--  access to SMTP Server   
-- set SQL Server service account as domain account   
  
EXEC sp_configure 'show advanced', 1  
RECONFIGURE  
GO  
  
-- Enable DBMail  
EXEC sp_configure 'Database Mail XPs',1  
GO  
RECONFIGURE  
GO  
  
-- Configure DBMail  
DECLARE @emailid NVARCHAR(255)  
-- Note: change this email to your own email id  
SET @emailid = N'emailalias@mycompany.com'  
  
DECLARE @smtpserver NVARCHAR(255)  
SET @smtpserver = N'smtphost.domainname.com'  
  
DECLARE @mailprofile NVARCHAR(255)  
SET @mailprofile = N'my_profile'  
  
EXEC msdb.dbo.sysmail_add_account_sp @account_name=N'myaccount',  
                @email_address = @emailid,  
                @replyto_address = @emailid,  
                @mailserver_name = @smtpserver,  
                @use_default_credentials = 1  
  
EXEC msdb.dbo.sysmail_add_profile_sp @profile_name=@mailprofile  
EXEC msdb.dbo.sysmail_add_profileaccount_sp @profile_name=@mailprofile, @account_name=N'myaccount', @sequence_number=1  
  
-- Set SQL Agent to use DBMail profile  
EXEC msdb.dbo.sp_set_sqlagent_properties @databasemail_profile = @mailprofile  
  
-- Configure Notifications   
EXEC msdb.smart_admin.sp_set_parameter  
@parameter_name = 'SSMBackup2WANotificationEmailIds',  
@parameter_value = @emailid  
  
-- To test is you are receiving notifications  
-- delete few backup files from your storage container, Wait for 15 minutes & see if you get any email notification
```  
  
### <a name="using-powershell-to-setup-custom-health-monitoring"></a><span data-ttu-id="e6fe6-175">PowerShell을 사용하여 사용자 지정 상태 모니터링</span><span class="sxs-lookup"><span data-stu-id="e6fe6-175">Using PowerShell to Setup Custom Health Monitoring</span></span>  
 <span data-ttu-id="e6fe6-176">**Set-sqlsmartadmin** cmdlet을 사용 하 여 사용자 지정 상태 모니터링을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6fe6-176">The **Test-SqlSmartAdmin** cmdlet can be used to create custom health monitoring.</span></span> <span data-ttu-id="e6fe6-177">예를 들어 이전 섹션에서 설명한 알림 옵션은 인스턴스 수준에서 구성될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6fe6-177">For example, the notification option described in the previous section can be configured at the instance level.</span></span>  <span data-ttu-id="e6fe6-178">여러 SQL Server 인스턴스가 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]을 사용하도록 구성된 경우 PowerShell cmdlet을 사용하여 모든 인스턴스의 백업 상태를 수집하는 스크립트를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6fe6-178">If you have several instances of SQL Server configured to use [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)], the PowerShell cmdlet can be used to create scripts in gather the status and health of backups for all the instances.</span></span>  
  
 <span data-ttu-id="e6fe6-179">**Set-sqlsmartadmin** cmdlet은 SQL Server 정책 기반 관리 정책에 의해 반환 되는 오류 및 경고를 평가 하 고 롤업 된 상태를 보고 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6fe6-179">The **Test-SqlSmartAdmin** cmdlet assesses the errors and warnings returned by the SQL Server Policy Based Management policies and reports out a rolled up status.</span></span>  <span data-ttu-id="e6fe6-180">기본적으로 이 cmdlet은 시스템 정책을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="e6fe6-180">By default this cmdlet uses the system policies.</span></span> <span data-ttu-id="e6fe6-181">사용자 지정 정책을 포함하려면 `-AllowUserPolicies` 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="e6fe6-181">To include any custom policy use the `-AllowUserPolicies` parameter.</span></span>  
  
 <span data-ttu-id="e6fe6-182">다음은 생성된 모든 사용자 정책 및 시스템 정책을 기반으로 하는 오류 및 경고 보고서를 반환하는 샘플 PowerShell 스크립트입니다.</span><span class="sxs-lookup"><span data-stu-id="e6fe6-182">Following is a sample PowerShell script that returns a report of errors and warnings based on the system policies and any user policies created:</span></span>  
  
```powershell
$policyResults = Get-SqlSmartAdmin | Test-SqlSmartAdmin -AllowUserPolicies  
$policyResults.PolicyEvaluationDetails | Select Name, Category, Expression, Result, Exception | fl
```  
  
 <span data-ttu-id="e6fe6-183">다음 스크립트는 기본 인스턴스 ()에 대 한 오류 및 경고에 대 한 자세한 보고서를 반환 합니다 `\SQL\COMPUTER\DEFAULT` .</span><span class="sxs-lookup"><span data-stu-id="e6fe6-183">The following script returns a detailed report of the errors and warnings for the default instance (`\SQL\COMPUTER\DEFAULT`):</span></span>  
  
```powershell
(Get-SqlSmartAdmin ).EnumHealthStatus()  
```  
  
### <a name="objects-in-msdb-database"></a><span data-ttu-id="e6fe6-184">MSDB 데이터베이스의 개체</span><span class="sxs-lookup"><span data-stu-id="e6fe6-184">Objects in MSDB database</span></span>  
 <span data-ttu-id="e6fe6-185">기능을 구현하기 위해 설치된 개체가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6fe6-185">There are objects that are installed to implement the functionality.</span></span> <span data-ttu-id="e6fe6-186">이러한 개체는 내부 사용을 위해 예약됩니다.</span><span class="sxs-lookup"><span data-stu-id="e6fe6-186">These objects are reserved for internal use.</span></span> <span data-ttu-id="e6fe6-187">그러나 smart_backup_files 백업 상태를 모니터링 하는 데 유용할 수 있는 시스템 테이블이 하나 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6fe6-187">However, there is one system table that can be useful in monitoring the backup status: smart_backup_files.</span></span> <span data-ttu-id="e6fe6-188">백업 유형, 데이터베이스 이름, 첫 번째 및 마지막 lsn, 백업 만료 날짜와 같은 모니터링과 관련 된이 테이블에 저장 된 대부분의 정보는 시스템 함수를 통해 [smart_admin fn_available_backups &#40;transact-sql&#41;](/sql/relational-databases/system-functions/managed-backup-fn-available-backups-transact-sql)를 통해 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e6fe6-188">Most of the Information   stored in this table relevant to monitoring like the type of backup, database name, first and last lsn, backup expiry dates are exposed through the system function [smart_admin.fn_available_backups &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/managed-backup-fn-available-backups-transact-sql).</span></span> <span data-ttu-id="e6fe6-189">백업 파일의 상태를 나타내는 smart_backup_files 테이블의 상태 열은 이 함수를 통해 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e6fe6-189">However the status column in the smart_backup_files table which indicates the status of the backup file is not available using the function.</span></span> <span data-ttu-id="e6fe6-190">다음은 시스템 테이블에서 상태를 비롯한 몇 가지 정보를 검색하는 데 사용할 수 있는 예제 쿼리입니다.</span><span class="sxs-lookup"><span data-stu-id="e6fe6-190">Following is a sample query you can use to retrieve the some information including the status from the system table:</span></span>  
  
```sql
USE msdb  
GO  
SELECT  
 database_name AS [Database Name] ,backup_path AS [Backup Destination and File]  
,[Backup Type] =  
CASE backup_type  
WHEN 1 THEN 'FULL'  
WHEN 2 THEN 'LOG'  
END  
,[Backup Status] =  
CASE [status]  
WHEN 'A' THEN 'Available'  
WHEN 'B' THEN 'Copy In Progress'  
WHEN 'C' THEN 'Corrupted'  
WHEN 'D' THEN 'Deleted'  
WHEN 'F' THEN 'Copy Failed'  
WHEN 'U' THEN 'Unknown'  
END  
,first_lsn AS [First LSN]  
,last_lsn AS [Last LSN]  
,backup_start_date AS [Backup Start Time]  
,backup_finish_date AS [Backup Completion Time]  
,expiration_date AS [Backup Expiry Date/Time]  
FROM  
smart_backup_files;
```  
  
 <span data-ttu-id="e6fe6-191">다음은 반환된 다른 상태에 대한 자세한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="e6fe6-191">Following is a detailed explanation of the different status returned:</span></span>  
  
-   <span data-ttu-id="e6fe6-192">**사용 가능-A:** 일반 백업 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="e6fe6-192">**Available - A:** This is a normal backup file.</span></span> <span data-ttu-id="e6fe6-193">백업이 완료 되었으며 Azure storage에서 사용할 수 있는지도 확인 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e6fe6-193">The backup has been completed, and also verified that it is available in the Azure storage.</span></span>  
  
-   <span data-ttu-id="e6fe6-194">**복사 진행 중-B:** 이 상태는 특히 가용성 그룹 데이터베이스에 대 한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="e6fe6-194">**Copy in Progress -B:** This status is specifically for Availability Group databases.</span></span> <span data-ttu-id="e6fe6-195">[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]은 백업 로그 체인이 끊어진 것을 검색하는 경우 먼저 그 원인이 될 수 있는 백업을 식별하려고 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="e6fe6-195">If [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] detects a break in the backup log chain, it will first attempt identify the  backup that might have caused the break in backup chain.</span></span> <span data-ttu-id="e6fe6-196">백업 파일을 찾을 때 파일을 Azure storage로 복사 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6fe6-196">On finding the backup file it attempts to copy the file to Azure storage.</span></span> <span data-ttu-id="e6fe6-197">복사 프로세스가 진행 중일 때 이 상태를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="e6fe6-197">When the copying process is in progress it will display this status.</span></span>  
  
-   <span data-ttu-id="e6fe6-198">**복사 실패-F:** 진행 중인 복사와 마찬가지로이는 특정 가용성 그룹 데이터베이스입니다.</span><span class="sxs-lookup"><span data-stu-id="e6fe6-198">**Copy Failed - F:** Similar to Copy In Progress, this is specific t Availability Group databases.</span></span> <span data-ttu-id="e6fe6-199">복사 프로세스가 실패하면 상태가 F로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e6fe6-199">If the copy process fails, the status is marked as F.</span></span>  
  
-   <span data-ttu-id="e6fe6-200">**손상 됨-C:** [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]가 여러 번의 시도 후에도 RESTORE HEADER_ONLY 명령을 수행 하 여 저장소의 백업 파일을 확인할 수 없는 경우이 파일을 손상 된 것으로 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6fe6-200">**Corrupted - C:** If [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] is unable to verify the backup file in the storage by performing a RESTORE HEADER_ONLY command even after multiple attempts, it marks this file as corrupted.</span></span> [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]<span data-ttu-id="e6fe6-201">은 손상된 파일로 인해 백업 체인이 끊어지지 않도록 하기 위해 백업을 예약합니다.</span><span class="sxs-lookup"><span data-stu-id="e6fe6-201">will schedule a backup to ensure that the corrupted file does not result in a break of the backup chain.</span></span>  
  
-   <span data-ttu-id="e6fe6-202">**삭제 됨-D:** Azure storage에서 해당 파일을 찾을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e6fe6-202">**Deleted - D:** The corresponding file cannot be found in the Azure storage.</span></span> [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]<span data-ttu-id="e6fe6-203">은 삭제된 파일로 인해 백업 체인이 끊어지는 경우 백업을 예약합니다.</span><span class="sxs-lookup"><span data-stu-id="e6fe6-203">will schedule a backup if the deleted file results in a break in the backup chain.</span></span>  
  
-   <span data-ttu-id="e6fe6-204">**알 수 없음-U:** 이 상태는에서 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 아직 파일의 존재 여부와 Azure storage의 속성을 확인할 수 없는 것으로 표시 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e6fe6-204">**Unknown - U:** This status indicated that [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] has not yet been able to verify file existence and its properties in the Azure storage.</span></span> <span data-ttu-id="e6fe6-205">약 15분 간격으로 다음에 프로세스가 실행될 때 이 상태가 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="e6fe6-205">The next time the process runs, which is approximately every 15 minutes, this status will be updated.</span></span>  
