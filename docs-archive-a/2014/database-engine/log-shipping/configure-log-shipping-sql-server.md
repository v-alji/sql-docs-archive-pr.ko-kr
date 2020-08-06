---
title: 로그 전달 구성(SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- log shipping [SQL Server], enabling
- log shipping [SQL Server], configuring
ms.assetid: c42aa04a-4945-4417-b4c7-50589d727e9c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 269b0ae2980435e507128cc87606f7eb702c2b7f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729747"
---
# <a name="configure-log-shipping-sql-server"></a><span data-ttu-id="f9118-102">로그 전달 구성(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="f9118-102">Configure Log Shipping (SQL Server)</span></span>
  <span data-ttu-id="f9118-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 을 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)]에서 로그 전달을 구성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f9118-103">This topic describes how to configure log shipping in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssEnterpriseEd10](../../includes/ssenterpriseed10-md.md)] <span data-ttu-id="f9118-104">이상 버전에서는 백업 압축을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="f9118-104">and later versions support backup compression.</span></span> <span data-ttu-id="f9118-105">로그 전달 구성을 만들 때 로그 백업의 백업 압축 동작을 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f9118-105">When creating a log shipping configuration, you can control the backup compression behavior of log backups.</span></span> <span data-ttu-id="f9118-106">자세한 내용은 [백업 압축&#40;SQL Server&#41;](../../relational-databases/backup-restore/backup-compression-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f9118-106">For more information, see [Backup Compression &#40;SQL Server&#41;](../../relational-databases/backup-restore/backup-compression-sql-server.md).</span></span>  
  
 <span data-ttu-id="f9118-107">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="f9118-107">**In This Topic**</span></span>  
  
-   <span data-ttu-id="f9118-108">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="f9118-108">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="f9118-109">필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="f9118-109">Prerequisites</span></span>](#Prerequisites)  
  
     [<span data-ttu-id="f9118-110">보안</span><span class="sxs-lookup"><span data-stu-id="f9118-110">Security</span></span>](#Security)  
  
-   <span data-ttu-id="f9118-111">**로그 전달을 구성하려면:**</span><span class="sxs-lookup"><span data-stu-id="f9118-111">**To configure log shipping, using:**</span></span>  
  
     [<span data-ttu-id="f9118-112">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="f9118-112">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="f9118-113">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="f9118-113">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   [<span data-ttu-id="f9118-114">관련 작업</span><span class="sxs-lookup"><span data-stu-id="f9118-114">Related Tasks</span></span>](#RelatedTasks)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="f9118-115">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="f9118-115">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="f9118-116">필수 조건</span><span class="sxs-lookup"><span data-stu-id="f9118-116">Prerequisites</span></span>  
  
-   <span data-ttu-id="f9118-117">주 데이터베이스는 전체 또는 대량 로그 복구 모델이어야 합니다. 데이터베이스를 단순 복구로 전환하면 로그 전달이 작동하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f9118-117">The primary database must use the full or bulk-logged recovery model; switching the database to simple recovery will cause log shipping to stop functioning.</span></span>  
  
-   <span data-ttu-id="f9118-118">로그 전달을 구성하려면 먼저 공유를 만들어 트랜잭션 로그 백업을 보조 서버에서 사용할 수 있도록 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f9118-118">Before you configure log shipping, you must create a share to make the transaction log backups available to the secondary server.</span></span> <span data-ttu-id="f9118-119">이 공유는 트랜잭션 로그 백업이 생성될 디렉터리의 공유입니다.</span><span class="sxs-lookup"><span data-stu-id="f9118-119">This is a share of the directory where the transaction log backups will be generated.</span></span> <span data-ttu-id="f9118-120">예를 들어 트랜잭션 로그를 c:\data\tlogs\\디렉터리로 백업할 경우 이 디렉터리의 \\\\*primaryserver*\tlogs 공유를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f9118-120">For example, if you back up your transaction logs to the directory c:\data\tlogs\\, you could create the \\\\*primaryserver*\tlogs share of that directory.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="f9118-121">보안</span><span class="sxs-lookup"><span data-stu-id="f9118-121">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="f9118-122">권한</span><span class="sxs-lookup"><span data-stu-id="f9118-122">Permissions</span></span>  
 <span data-ttu-id="f9118-123">로그 전달 저장 프로시저를 사용하려면 **sysadmin** 고정 서버 역할의 멤버 자격이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="f9118-123">The log-shipping stored procedures require membership in the **sysadmin** fixed server role.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="f9118-124">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="f9118-124">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-configure-log-shipping"></a><span data-ttu-id="f9118-125">로그 전달을 구성하려면</span><span class="sxs-lookup"><span data-stu-id="f9118-125">To configure log shipping</span></span>  
  
1.  <span data-ttu-id="f9118-126">로그 전달 구성에서 주 데이터베이스로 사용하려는 데이터베이스를 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f9118-126">Right click the database you want to use as your primary database in the log shipping configuration, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="f9118-127">**페이지 선택**에서 **트랜잭션 로그 전달**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f9118-127">Under **Select a page**, click **Transaction Log Shipping**.</span></span>  
  
3.  <span data-ttu-id="f9118-128">**이 데이터베이스를 로그 전달 구성의 주 데이터베이스로 사용** 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f9118-128">Select the **Enable this as a primary database in a log shipping configuration** check box.</span></span>  
  
4.  <span data-ttu-id="f9118-129">**트랜잭션 로그 백업**에서 **백업 설정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f9118-129">Under **Transaction log backups**, click **Backup Settings**.</span></span>  
  
5.  <span data-ttu-id="f9118-130">**백업 폴더의 네트워크 경로** 입력란에 트랜잭션 로그 백업 폴더용으로 만든 공유의 네트워크 경로를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="f9118-130">In the **Network path to the backup folder** box, type the network path to the share you created for the transaction log backup folder.</span></span>  
  
6.  <span data-ttu-id="f9118-131">백업 폴더가 주 서버에 있는 경우 **백업 폴더가 주 서버에 있는 경우 폴더의 로컬 경로를 입력하세요** 입력란에 백업 폴더의 로컬 경로를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="f9118-131">If the backup folder is located on the primary server, type the local path to the backup folder in the **If the backup folder is located on the primary server, type a local path to the folder** box.</span></span> <span data-ttu-id="f9118-132">백업 폴더가 주 서버에 있지 않은 경우 이 입력란을 비워 둘 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f9118-132">(If the backup folder is not on the primary server, you can leave this box empty.)</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="f9118-133">주 서버의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 서비스 계정이 로컬 시스템 계정으로 실행 중인 경우 주 서버에 백업 폴더를 만들고 해당 폴더의 로컬 경로를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f9118-133">If the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service account on your primary server runs under the local system account, you must create your backup folder on the primary server and specify a local path to that folder.</span></span>  
  
7.  <span data-ttu-id="f9118-134">**다음보다 오래된 파일 삭제** 및 **다음 기간 내에 백업이 발생하지 않으면 경고** 매개 변수를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="f9118-134">Configure the **Delete files older than** and **Alert if no backup occurs within** parameters.</span></span>  
  
8.  <span data-ttu-id="f9118-135">백업 일정은 **백업 작업** 의 **일정**상자에 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="f9118-135">Note the backup schedule listed in the **Schedule** box under **Backup job**.</span></span> <span data-ttu-id="f9118-136">설치 일정을 사용자 지정하려면 **일정** 을 클릭한 다음 필요에 따라 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 일정을 조정합니다.</span><span class="sxs-lookup"><span data-stu-id="f9118-136">If you want to customize the schedule for your installation, then click **Schedule** and adjust the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent schedule as needed.</span></span>  
  
9. [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="f9118-137">에서는 [백업 압축](../../relational-databases/backup-restore/backup-compression-sql-server.md)을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="f9118-137">supports [backup compression](../../relational-databases/backup-restore/backup-compression-sql-server.md).</span></span> <span data-ttu-id="f9118-138">로그 전달 구성을 만들 때 다음 옵션 중 하나를 선택하여 로그 백업의 백업 압축 동작을 제어할 수 있습니다. **기본 서버 설정 사용**, **백업 압축** 또는 **백업 압축 안 함**.</span><span class="sxs-lookup"><span data-stu-id="f9118-138">When creating a log shipping configuration, you can control the backup compression behavior of log backups by choosing one of the following options: **Use the default server setting**, **Compress backup**, or **Do not compress backup**.</span></span> <span data-ttu-id="f9118-139">자세한 내용은 [Log Shipping Transaction Log Backup Settings](../../relational-databases/databases/log-shipping-transaction-log-backup-settings.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f9118-139">For more information, see [Log Shipping Transaction Log Backup Settings](../../relational-databases/databases/log-shipping-transaction-log-backup-settings.md).</span></span>  
  
10. <span data-ttu-id="f9118-140">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f9118-140">Click **OK**.</span></span>  
  
11. <span data-ttu-id="f9118-141">**보조 서버 인스턴스 및 데이터베이스**에서 **추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f9118-141">Under **Secondary server instances and databases**, click **Add**.</span></span>  
  
12. <span data-ttu-id="f9118-142">**연결** 을 클릭하여 보조 서버로 사용하려는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="f9118-142">Click **Connect** and connect to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that you want to use as your secondary server.</span></span>  
  
13. <span data-ttu-id="f9118-143">**보조 데이터베이스** 입력란의 목록에서 데이터베이스를 선택하거나 만들 데이터베이스의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="f9118-143">In the **Secondary Database** box, choose a database from the list or type the name of the database you want to create.</span></span>  
  
14. <span data-ttu-id="f9118-144">**보조 데이터베이스 초기화** 탭에서 보조 데이터베이스 초기화에 사용하려는 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f9118-144">On the **Initialize Secondary database** tab, choose the option that you want to use to initialize the secondary database.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f9118-145">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 가 데이터베이스 백업에서 보조 데이터베이스를 초기화하도록 선택하면 보조 데이터베이스의 데이터 및 로그 파일이 **master** 데이터베이스의 데이터 및 로그 파일과 동일한 위치에 배치됩니다.</span><span class="sxs-lookup"><span data-stu-id="f9118-145">If you choose to have [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] initialize the secondary database from a database backup, the data and log files of the secondary database are placed in the same location as the data and log files of the **master** database.</span></span> <span data-ttu-id="f9118-146">이 위치는 주 데이터베이스 데이터 및 로그 파일의 위치와 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f9118-146">This location is likely to be different than the location of the data and log files of the primary database.</span></span>  
  
15. <span data-ttu-id="f9118-147">**파일 복사** 탭의 **복사한 파일의 대상 폴더** 입력란에 트랜잭션 로그 백업을 복사할 대상 폴더의 경로를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="f9118-147">On the **Copy Files** tab, in the **Destination folder for copied files** box, type the path of the folder into which the transaction logs backups should be copied.</span></span> <span data-ttu-id="f9118-148">이 폴더는 대개 보조 서버에 위치합니다.</span><span class="sxs-lookup"><span data-stu-id="f9118-148">This folder is often located on the secondary server.</span></span>  
  
16. <span data-ttu-id="f9118-149">복사 일정은 **복사 작업** 의 **일정**상자에 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="f9118-149">Note the copy schedule listed in the **Schedule** box under **Copy job**.</span></span> <span data-ttu-id="f9118-150">설치 일정을 사용자 지정하려면 **일정** 을 클릭한 다음 필요에 따라 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 일정을 조정합니다.</span><span class="sxs-lookup"><span data-stu-id="f9118-150">If you want to customize the schedule for your installation, click **Schedule** and then adjust the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent schedule as needed.</span></span> <span data-ttu-id="f9118-151">이 일정은 백업 일정과 비슷해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f9118-151">This schedule should approximate the backup schedule.</span></span>  
  
17. <span data-ttu-id="f9118-152">**트랜잭션 로그 복원** 탭의 **백업 복원 시 데이터베이스 상태**에서 **복구 안 함 모드** 또는 **대기 모드** 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f9118-152">On the **Restore** tab, under **Database state when restoring backups**, choose the **No recovery mode** or **Standby mode** option.</span></span>  
  
18. <span data-ttu-id="f9118-153">**대기 모드** 옵션을 선택한 경우 복원 작업을 진행하는 동안 보조 데이터베이스에서 사용자와의 연결을 끊을지 여부를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f9118-153">If you chose the **Standby mode** option, choose if you want to disconnect users from the secondary database while the restore operation is underway.</span></span>  
  
19. <span data-ttu-id="f9118-154">보조 서버에서 복원 프로세스를 지연시키려면 **최소 다음 기간 동안 백업 복원 지연**에서 지연 시간을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f9118-154">If you want to delay the restore process on the secondary server, choose a delay time under **Delay restoring backups at least**.</span></span>  
  
20. <span data-ttu-id="f9118-155">**다음 기간 내에 복원이 발생하지 않으면 경고**에서 경고 임계값을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f9118-155">Choose an alert threshold under **Alert if no restore occurs within**.</span></span>  
  
21. <span data-ttu-id="f9118-156">복원 일정은 **복원 작업** 의 **일정**상자에 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="f9118-156">Note the restore schedule listed in the **Schedule** box under **Restore job**.</span></span> <span data-ttu-id="f9118-157">설치 일정을 사용자 지정하려면 **일정** 을 클릭한 다음 필요에 따라 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 일정을 조정합니다.</span><span class="sxs-lookup"><span data-stu-id="f9118-157">If you want to customize the schedule for your installation, click **Schedule** and then adjust the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent schedule as needed.</span></span> <span data-ttu-id="f9118-158">이 일정은 백업 일정과 비슷해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f9118-158">This schedule should approximate the backup schedule.</span></span>  
  
22. <span data-ttu-id="f9118-159">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f9118-159">Click **OK**.</span></span>  
  
23. <span data-ttu-id="f9118-160">**모니터 서버 인스턴스**에서 **모니터 서버 인스턴스 사용** 확인란을 선택하고 **설정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f9118-160">Under **Monitor server instance**, select the **Use a monitor server instance** check box, and then click **Settings**.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="f9118-161">이 로그 전달 구성을 모니터링하려면 지금 모니터 서버를 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f9118-161">To monitor this log shipping configuration, you must add the monitor server now.</span></span> <span data-ttu-id="f9118-162">나중에 모니터 서버를 추가하려면 이 로그 전달 구성을 제거한 다음 모니터 서버가 포함된 새 구성으로 바꾸어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f9118-162">To add the monitor server later, you would need to remove this log shipping configuration and then replace it with a new configuration that includes a monitor server.</span></span>  
  
24. <span data-ttu-id="f9118-163">**연결** 을 클릭하여 모니터 서버로 사용하려는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="f9118-163">Click **Connect** and connect to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that you want to use as your monitor server.</span></span>  
  
25. <span data-ttu-id="f9118-164">**모니터 연결**에서 백업, 복사 및 복원 작업을 모니터 서버에 연결하는 데 사용할 연결 방법을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f9118-164">Under **Monitor connections**, choose the connection method to be used by the backup, copy, and restore jobs to connect to the monitor server.</span></span>  
  
26. <span data-ttu-id="f9118-165">**기록 보존**에서 로그 전달 기록을 보관할 기간을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f9118-165">Under **History retention**, choose the length of time you want to retain a record of your log shipping history.</span></span>  
  
27. <span data-ttu-id="f9118-166">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f9118-166">Click **OK**.</span></span>  
  
28. <span data-ttu-id="f9118-167">**데이터베이스 속성** 대화 상자에서 **확인** 을 눌러 구성 프로세스를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="f9118-167">On the **Database Properties** dialog box, click **OK** to begin the configuration process.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="f9118-168">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="f9118-168">Using Transact-SQL</span></span>  
  
#### <a name="to-configure-log-shipping"></a><span data-ttu-id="f9118-169">로그 전달을 구성하려면</span><span class="sxs-lookup"><span data-stu-id="f9118-169">To configure log shipping</span></span>  
  
1.  <span data-ttu-id="f9118-170">보조 서버에서 주 데이터베이스의 전체 백업을 복원하는 방법으로 보조 데이터베이스를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="f9118-170">Initialize the secondary database by restoring a full backup of the primary database on the secondary server.</span></span>  
  
2.  <span data-ttu-id="f9118-171">주 서버에서 [sp_add_log_shipping_primary_database](/sql/relational-databases/system-stored-procedures/sp-add-log-shipping-primary-database-transact-sql) 를 실행하여 주 데이터베이스를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="f9118-171">On the primary server, execute [sp_add_log_shipping_primary_database](/sql/relational-databases/system-stored-procedures/sp-add-log-shipping-primary-database-transact-sql) to add a primary database.</span></span> <span data-ttu-id="f9118-172">저장 프로시저는 백업 작업 ID 및 주 ID를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="f9118-172">The stored procedure returns the backup job ID and primary ID.</span></span>  
  
3.  <span data-ttu-id="f9118-173">주 서버에서 [sp_add_jobschedule](/sql/relational-databases/system-stored-procedures/sp-add-jobschedule-transact-sql) 을 실행하여 백업 작업에 대한 일정을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="f9118-173">On the primary server, execute [sp_add_jobschedule](/sql/relational-databases/system-stored-procedures/sp-add-jobschedule-transact-sql) to add a schedule for the backup job.</span></span>  
  
4.  <span data-ttu-id="f9118-174">모니터 서버에서 [sp_add_log_shipping_alert_job](/sql/relational-databases/system-stored-procedures/sp-add-log-shipping-alert-job-transact-sql) 을 실행하여 경고 작업을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="f9118-174">On the monitor server, execute [sp_add_log_shipping_alert_job](/sql/relational-databases/system-stored-procedures/sp-add-log-shipping-alert-job-transact-sql) to add the alert job.</span></span>  
  
5.  <span data-ttu-id="f9118-175">주 서버에서 백업 작업을 활성화합니다.</span><span class="sxs-lookup"><span data-stu-id="f9118-175">On the primary server, enable the backup job.</span></span>  
  
6.  <span data-ttu-id="f9118-176">보조 서버에서 [sp_add_log_shipping_secondary_primary](/sql/relational-databases/system-stored-procedures/sp-add-log-shipping-secondary-primary-transact-sql) 를 실행하여 주 서버와 데이터베이스에 대한 세부 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="f9118-176">On the secondary server, execute [sp_add_log_shipping_secondary_primary](/sql/relational-databases/system-stored-procedures/sp-add-log-shipping-secondary-primary-transact-sql) supplying the details of the primary server and database.</span></span> <span data-ttu-id="f9118-177">이 저장 프로시저는 보조 ID와 복사 및 복원 작업 ID를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="f9118-177">This stored procedure returns the secondary ID and the copy and restore job IDs.</span></span>  
  
7.  <span data-ttu-id="f9118-178">보조 서버에서 [sp_add_jobschedule](/sql/relational-databases/system-stored-procedures/sp-add-jobschedule-transact-sql) 을 실행하여 복사 및 복원 작업의 일정을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="f9118-178">On the secondary server, execute [sp_add_jobschedule](/sql/relational-databases/system-stored-procedures/sp-add-jobschedule-transact-sql) to set the schedule for the copy and restore jobs.</span></span>  
  
8.  <span data-ttu-id="f9118-179">보조 서버에서 [sp_add_log_shipping_secondary_database](/sql/relational-databases/system-stored-procedures/sp-add-log-shipping-secondary-database-transact-sql) 를 실행하여 보조 데이터베이스를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="f9118-179">On the secondary server, execute [sp_add_log_shipping_secondary_database](/sql/relational-databases/system-stored-procedures/sp-add-log-shipping-secondary-database-transact-sql) to add a secondary database.</span></span>  
  
9. <span data-ttu-id="f9118-180">주 서버에서 [sp_add_log_shipping_primary_secondary](/sql/relational-databases/system-stored-procedures/sp-add-log-shipping-primary-secondary-transact-sql) 를 실행하여 새 보조 데이터베이스에 대한 필요 정보를 주 서버에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="f9118-180">On the primary server, execute [sp_add_log_shipping_primary_secondary](/sql/relational-databases/system-stored-procedures/sp-add-log-shipping-primary-secondary-transact-sql) to add the required information about the new secondary database to the primary server.</span></span>  
  
10. <span data-ttu-id="f9118-181">보조 서버에서 복사 및 복원 작업을 활성화합니다.</span><span class="sxs-lookup"><span data-stu-id="f9118-181">On the secondary server, enable the copy and restore jobs.</span></span> <span data-ttu-id="f9118-182">자세한 내용은 [Disable or Enable a Job](../../ssms/agent/disable-or-enable-a-job.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f9118-182">For more information, see [Disable or Enable a Job](../../ssms/agent/disable-or-enable-a-job.md).</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="f9118-183">관련 작업</span><span class="sxs-lookup"><span data-stu-id="f9118-183">Related Tasks</span></span>  
  
-   [<span data-ttu-id="f9118-184">SQL Server 2014 &#40;Transact-sql&#41;로그 전달 업그레이드</span><span class="sxs-lookup"><span data-stu-id="f9118-184">Upgrade Log Shipping to SQL Server 2014 &#40;Transact-SQL&#41;</span></span>](upgrading-log-shipping-to-sql-server-2016-transact-sql.md)  
  
-   [<span data-ttu-id="f9118-185">로그 전달 구성에 보조 데이터베이스 추가&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="f9118-185">Add a Secondary Database to a Log Shipping Configuration &#40;SQL Server&#41;</span></span>](add-a-secondary-database-to-a-log-shipping-configuration-sql-server.md)  
  
-   [<span data-ttu-id="f9118-186">로그 전달 구성에서 보조 데이터베이스 제거&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="f9118-186">Remove a Secondary Database from a Log Shipping Configuration &#40;SQL Server&#41;</span></span>](remove-a-secondary-database-from-a-log-shipping-configuration-sql-server.md)  
  
-   [<span data-ttu-id="f9118-187">로그 전달 제거&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="f9118-187">Remove Log Shipping &#40;SQL Server&#41;</span></span>](remove-log-shipping-sql-server.md)  
  
-   [<span data-ttu-id="f9118-188">로그 전달 보고서 보기&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="f9118-188">View the Log Shipping Report &#40;SQL Server Management Studio&#41;</span></span>](view-the-log-shipping-report-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="f9118-189">로그 전달 모니터링&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f9118-189">Monitor Log Shipping &#40;Transact-SQL&#41;</span></span>](monitor-log-shipping-transact-sql.md)  
  
-   [<span data-ttu-id="f9118-190">로그 전달 보조 데이터베이스로 장애 조치(failover)&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="f9118-190">Fail Over to a Log Shipping Secondary &#40;SQL Server&#41;</span></span>](fail-over-to-a-log-shipping-secondary-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="f9118-191">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f9118-191">See Also</span></span>  
 <span data-ttu-id="f9118-192">[로그 전달 정보&#40;SQL Server&#41;](about-log-shipping-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="f9118-192">[About Log Shipping &#40;SQL Server&#41;](about-log-shipping-sql-server.md) </span></span>  
 [<span data-ttu-id="f9118-193">로그 전달 테이블 및 저장 프로시저</span><span class="sxs-lookup"><span data-stu-id="f9118-193">Log Shipping Tables and Stored Procedures</span></span>](log-shipping-tables-and-stored-procedures.md)  
  
  
