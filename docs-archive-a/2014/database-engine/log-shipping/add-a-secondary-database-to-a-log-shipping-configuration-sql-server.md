---
title: 로그 전달 구성에 보조 데이터베이스 추가(SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- adding secondary databases
- secondary databases [SQL Server], in log shipping
- secondary data files [SQL Server], adding
- log shipping [SQL Server], secondary databases
ms.assetid: b02eba13-f8e6-4684-b7e4-75ea038ea473
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 062df1b53ed74321ba0c75c9df763de79a4802bd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651245"
---
# <a name="add-a-secondary-database-to-a-log-shipping-configuration-sql-server"></a><span data-ttu-id="c7308-102">로그 전달 구성에 보조 데이터베이스 추가(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="c7308-102">Add a Secondary Database to a Log Shipping Configuration (SQL Server)</span></span>
  <span data-ttu-id="c7308-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 를 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)]에서 기존의 로그 전달 구성에 보조 데이터베이스를 추가하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="c7308-103">This topic describes how to add a secondary database to an existing log shipping configuration in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="c7308-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="c7308-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="c7308-105">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="c7308-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="c7308-106">보안</span><span class="sxs-lookup"><span data-stu-id="c7308-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="c7308-107">**로그 전달 보조 데이터베이스를 추가하려면:**</span><span class="sxs-lookup"><span data-stu-id="c7308-107">**To add a log shipping secondary database, using:**</span></span>  
  
     [<span data-ttu-id="c7308-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="c7308-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="c7308-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="c7308-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   [<span data-ttu-id="c7308-110">관련 작업</span><span class="sxs-lookup"><span data-stu-id="c7308-110">Related Tasks</span></span>](#RelatedTasks)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="c7308-111">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="c7308-111">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="c7308-112">보안</span><span class="sxs-lookup"><span data-stu-id="c7308-112">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="c7308-113">권한</span><span class="sxs-lookup"><span data-stu-id="c7308-113">Permissions</span></span>  
 <span data-ttu-id="c7308-114">로그 전달 저장 프로시저를 사용하려면 **sysadmin** 고정 서버 역할의 멤버 자격이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="c7308-114">The log-shipping stored procedures require membership in the **sysadmin** fixed server role.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="c7308-115">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="c7308-115">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-add-a-log-shipping-secondary-database"></a><span data-ttu-id="c7308-116">로그 전달 보조 데이터베이스를 추가하려면</span><span class="sxs-lookup"><span data-stu-id="c7308-116">To add a log shipping secondary database</span></span>  
  
1.  <span data-ttu-id="c7308-117">로그 전달 구성에서 주 데이터베이스로 사용하려는 데이터베이스를 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c7308-117">Right-click the database you want to use as your primary database in the log shipping configuration, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="c7308-118">**페이지 선택**에서 **트랜잭션 로그 전달**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c7308-118">Under **Select a page**, click **Transaction Log Shipping**.</span></span>  
  
3.  <span data-ttu-id="c7308-119">**보조 서버 인스턴스 및 데이터베이스**에서 **추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c7308-119">Under **Secondary server instances and databases**, click **Add**.</span></span>  
  
4.  <span data-ttu-id="c7308-120">**연결** 을 클릭하여 보조 서버로 사용하려는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="c7308-120">Click **Connect** and connect to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that you want to use as your secondary server.</span></span>  
  
5.  <span data-ttu-id="c7308-121">**보조 데이터베이스** 상자의 목록에서 데이터베이스를 선택하거나 만들려는 데이터베이스의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="c7308-121">In the **Secondary database** box, choose a database from the list or type the name of the database you want to create.</span></span>  
  
6.  <span data-ttu-id="c7308-122">**보조 데이터베이스 초기화** 탭에서 보조 데이터베이스 초기화에 사용하려는 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c7308-122">On the **Initialize Secondary database** tab, choose the option that you want to use to initialize the secondary database.</span></span>  
  
7.  <span data-ttu-id="c7308-123">**파일 복사**탭의 **복사한 파일의 대상 폴더** 입력란에 트랜잭션 로그 백업을 복사할 대상 폴더의 경로를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="c7308-123">On the **Copy Files tab**, in the **Destination folder for copied files** box, type the path of the folder into which the transaction logs backups should be copied.</span></span> <span data-ttu-id="c7308-124">이 폴더는 대개 보조 서버에 위치합니다.</span><span class="sxs-lookup"><span data-stu-id="c7308-124">This folder is often located on the secondary server.</span></span>  
  
8.  <span data-ttu-id="c7308-125">복사 일정은 **복사 작업** 의 **일정**상자에 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7308-125">Note the copy schedule listed in the **Schedule** box under **Copy job**.</span></span> <span data-ttu-id="c7308-126">설치 일정을 사용자 지정하려면 **일정** 을 클릭한 다음 필요에 따라 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 일정을 조정합니다.</span><span class="sxs-lookup"><span data-stu-id="c7308-126">If you want to customize the schedule for your installation, click **Schedule** and then adjust the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent schedule as needed.</span></span> <span data-ttu-id="c7308-127">이 일정은 백업 일정과 비슷해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7308-127">This schedule should approximate the backup schedule.</span></span>  
  
9. <span data-ttu-id="c7308-128">**트랜잭션 로그 복원** 탭의 **백업 복원 시 데이터베이스 상태**에서 **복구 안 함 모드** 또는 **대기 모드** 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c7308-128">On the **Restore** tab, under **Database state when restoring backups**, choose the **No recovery mode** or **Standby mode** option.</span></span>  
  
10. <span data-ttu-id="c7308-129">**대기 모드** 옵션을 선택한 경우 복원 작업을 진행하는 동안 보조 데이터베이스에서 사용자와의 연결을 끊을지 여부를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c7308-129">If you chose the **Standby mode** option, choose if you want to disconnect users from the secondary database while the restore operation is underway.</span></span>  
  
11. <span data-ttu-id="c7308-130">보조 서버에서 복원 프로세스를 지연시키려면 **최소 다음 기간 동안 백업 복원 지연**에서 지연 시간을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c7308-130">If you want to delay the restore process on the secondary server, choose a delay time under **Delay restoring backups at least**.</span></span>  
  
12. <span data-ttu-id="c7308-131">**다음 기간 내에 복원이 발생하지 않으면 경고**에서 경고 임계값을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c7308-131">Choose an alert threshold under **Alert if no restore occurs within**.</span></span>  
  
13. <span data-ttu-id="c7308-132">복원 일정은 **복원 작업** 의 **일정**상자에 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7308-132">Note the restore schedule listed in the **Schedule** box under **Restore job**.</span></span> <span data-ttu-id="c7308-133">설치 일정을 사용자 지정하려면 **일정** 을 클릭한 다음 필요에 따라 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 일정을 조정합니다.</span><span class="sxs-lookup"><span data-stu-id="c7308-133">If you want to customize the schedule for your installation, click **Schedule** and then adjust the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent schedule as needed.</span></span> <span data-ttu-id="c7308-134">이 일정은 백업 일정과 비슷해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7308-134">This schedule should approximate the backup schedule.</span></span>  
  
14. <span data-ttu-id="c7308-135">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c7308-135">Click **OK**.</span></span>  
  
15. <span data-ttu-id="c7308-136">데이터베이스 속성 대화 상자에서 **확인** 을 클릭하여 구성 프로세스를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="c7308-136">Click **OK** on the Database Properties dialog box to begin the configuration process.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="c7308-137">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="c7308-137">Using Transact-SQL</span></span>  
  
#### <a name="to-add-a-log-shipping-secondary-database"></a><span data-ttu-id="c7308-138">로그 전달 보조 데이터베이스를 추가하려면</span><span class="sxs-lookup"><span data-stu-id="c7308-138">To add a log shipping secondary database</span></span>  
  
1.  <span data-ttu-id="c7308-139">보조 서버에서 [sp_add_log_shipping_secondary_primary](/sql/relational-databases/system-stored-procedures/sp-add-log-shipping-secondary-primary-transact-sql) 를 실행하여 주 서버와 데이터베이스에 대한 세부 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="c7308-139">On the secondary server, execute [sp_add_log_shipping_secondary_primary](/sql/relational-databases/system-stored-procedures/sp-add-log-shipping-secondary-primary-transact-sql) supplying the details of the primary server and database.</span></span> <span data-ttu-id="c7308-140">이 저장 프로시저는 보조 ID와 복사 및 복원 작업 ID를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="c7308-140">This stored procedure returns the secondary ID and the copy and restore job IDs.</span></span>  
  
2.  <span data-ttu-id="c7308-141">보조 서버에서 [sp_add_jobschedule](/sql/relational-databases/system-stored-procedures/sp-add-jobschedule-transact-sql) 을 실행하여 복사 및 복원 작업의 일정을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="c7308-141">On the secondary server, execute [sp_add_jobschedule](/sql/relational-databases/system-stored-procedures/sp-add-jobschedule-transact-sql) to set the schedule for the copy and restore jobs.</span></span>  
  
3.  <span data-ttu-id="c7308-142">보조 서버에서 [sp_add_log_shipping_secondary_database](/sql/relational-databases/system-stored-procedures/sp-add-log-shipping-secondary-database-transact-sql) 를 실행하여 보조 데이터베이스를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="c7308-142">On the secondary server, execute [sp_add_log_shipping_secondary_database](/sql/relational-databases/system-stored-procedures/sp-add-log-shipping-secondary-database-transact-sql) to add a secondary database.</span></span>  
  
4.  <span data-ttu-id="c7308-143">주 서버에서 [sp_add_log_shipping_primary_secondary](/sql/relational-databases/system-stored-procedures/sp-add-log-shipping-primary-secondary-transact-sql) 를 실행하여 새 보조 데이터베이스에 대한 필요 정보를 주 서버에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="c7308-143">On the primary server, execute [sp_add_log_shipping_primary_secondary](/sql/relational-databases/system-stored-procedures/sp-add-log-shipping-primary-secondary-transact-sql) to add the required information about the new secondary database to the primary server.</span></span>  
  
5.  <span data-ttu-id="c7308-144">보조 서버에서 복사 및 복원 작업을 활성화합니다.</span><span class="sxs-lookup"><span data-stu-id="c7308-144">On the secondary server, enable the copy and restore jobs.</span></span> <span data-ttu-id="c7308-145">자세한 내용은 [Disable or Enable a Job](../../ssms/agent/disable-or-enable-a-job.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c7308-145">For more information, see [Disable or Enable a Job](../../ssms/agent/disable-or-enable-a-job.md).</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="c7308-146">관련 작업</span><span class="sxs-lookup"><span data-stu-id="c7308-146">Related Tasks</span></span>  
  
-   [<span data-ttu-id="c7308-147">SQL Server 2014 &#40;Transact-sql&#41;로그 전달 업그레이드</span><span class="sxs-lookup"><span data-stu-id="c7308-147">Upgrade Log Shipping to SQL Server 2014 &#40;Transact-SQL&#41;</span></span>](upgrading-log-shipping-to-sql-server-2016-transact-sql.md)  
  
-   [<span data-ttu-id="c7308-148">로그 전달 구성&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="c7308-148">Configure Log Shipping &#40;SQL Server&#41;</span></span>](configure-log-shipping-sql-server.md)  
  
-   [<span data-ttu-id="c7308-149">로그 전달 구성에서 보조 데이터베이스 제거&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="c7308-149">Remove a Secondary Database from a Log Shipping Configuration &#40;SQL Server&#41;</span></span>](remove-a-secondary-database-from-a-log-shipping-configuration-sql-server.md)  
  
-   [<span data-ttu-id="c7308-150">로그 전달 제거&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="c7308-150">Remove Log Shipping &#40;SQL Server&#41;</span></span>](remove-log-shipping-sql-server.md)  
  
-   [<span data-ttu-id="c7308-151">로그 전달 보고서 보기&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="c7308-151">View the Log Shipping Report &#40;SQL Server Management Studio&#41;</span></span>](view-the-log-shipping-report-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="c7308-152">로그 전달 모니터링&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="c7308-152">Monitor Log Shipping &#40;Transact-SQL&#41;</span></span>](monitor-log-shipping-transact-sql.md)  
  
-   [<span data-ttu-id="c7308-153">로그 전달 보조 데이터베이스로 장애 조치(failover)&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="c7308-153">Fail Over to a Log Shipping Secondary &#40;SQL Server&#41;</span></span>](fail-over-to-a-log-shipping-secondary-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="c7308-154">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c7308-154">See Also</span></span>  
 <span data-ttu-id="c7308-155">[로그 전달 정보&#40;SQL Server&#41;](about-log-shipping-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="c7308-155">[About Log Shipping &#40;SQL Server&#41;](about-log-shipping-sql-server.md) </span></span>  
 [<span data-ttu-id="c7308-156">로그 전달 테이블 및 저장 프로시저</span><span class="sxs-lookup"><span data-stu-id="c7308-156">Log Shipping Tables and Stored Procedures</span></span>](log-shipping-tables-and-stored-procedures.md)  
  
  
