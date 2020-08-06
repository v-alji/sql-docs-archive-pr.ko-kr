---
title: 보조 데이터베이스 설정 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.databaseproperties.logshipping.settings.dest.f1
ms.assetid: f992ffc9-ee42-43fe-acec-512032f0ded1
author: stevestein
ms.author: sstein
ms.openlocfilehash: 265d6beda830e2090392918ae14d10c8b7752d02
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650080"
---
# <a name="secondary-database-settings"></a><span data-ttu-id="a7df3-102">보조 데이터베이스 설정</span><span class="sxs-lookup"><span data-stu-id="a7df3-102">Secondary Database Settings</span></span>
  <span data-ttu-id="a7df3-103">이 대화 상자를 사용하여 로그 전달 구성에서 보조 데이터베이스의 속성을 구성하고 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a7df3-103">Use this dialog box to configure and to modify the properties of a secondary database in the log shipping configuration.</span></span>  
  
 <span data-ttu-id="a7df3-104">로그 전달 개념에 대한 설명은 [로그 전달 정보&#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a7df3-104">For an explanation of log shipping concepts, see [About Log Shipping &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="a7df3-105">옵션</span><span class="sxs-lookup"><span data-stu-id="a7df3-105">Options</span></span>  
 <span data-ttu-id="a7df3-106">**보조 서버 인스턴스**</span><span class="sxs-lookup"><span data-stu-id="a7df3-106">**Secondary server instance**</span></span>  
 <span data-ttu-id="a7df3-107">로그 전달 구성에서 현재 보조 서버로 구성되어 있는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="a7df3-107">Displays the name of the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] currently configured to be a secondary server in the log shipping configuration.</span></span>  
  
 <span data-ttu-id="a7df3-108">**보조 데이터베이스**</span><span class="sxs-lookup"><span data-stu-id="a7df3-108">**Secondary database**</span></span>  
 <span data-ttu-id="a7df3-109">로그 전달 구성의 보조 데이터베이스 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="a7df3-109">Displays the name of the secondary database for the log shipping configuration.</span></span> <span data-ttu-id="a7df3-110">로그 전달 구성에 새 보조 데이터베이스를 추가하는 경우 목록에서 데이터베이스를 선택하거나 입력란에 새 데이터베이스의 이름을 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a7df3-110">When adding a new secondary database to a log shipping configuration, you can choose a database from the list or type the name of a new of the database into the box.</span></span> <span data-ttu-id="a7df3-111">새 데이터베이스의 이름을 입력하는 경우 **초기화** 탭에서 주 데이터베이스의 전체 데이터베이스 백업을 보조 데이터베이스로 복원하는 옵션을 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a7df3-111">If you enter the name of a new database, you must select an option on the **Initialization** tab that restores a full database backup of the primary database into the secondary database.</span></span> <span data-ttu-id="a7df3-112">이 복원 작업을 실행하는 과정의 일부로서 새 데이터베이스가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="a7df3-112">The new database is created as part of the restore operation.</span></span>  
  
 <span data-ttu-id="a7df3-113">**연결**</span><span class="sxs-lookup"><span data-stu-id="a7df3-113">**Connect**</span></span>  
 <span data-ttu-id="a7df3-114">로그 전달 구성에서 보조 서버로 사용할 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="a7df3-114">Connect to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] for use as a secondary server in the log shipping configuration.</span></span> <span data-ttu-id="a7df3-115">연결 시 사용한 계정은 보조 서버 인스턴스에서 sysadmin 고정 서버 역할의 멤버여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a7df3-115">The account used to connect must be a member of the sysadmin fixed server role on the secondary server instance.</span></span>  
  
 <span data-ttu-id="a7df3-116">**초기화 탭**</span><span class="sxs-lookup"><span data-stu-id="a7df3-116">**Initialize tab**</span></span>  
 <span data-ttu-id="a7df3-117">옵션은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="a7df3-117">The options are as follows:</span></span>  
  
 <span data-ttu-id="a7df3-118">**예, 주 데이터베이스의 전체 백업을 생성하고 보조 데이터베이스에 복원합니다.**</span><span class="sxs-lookup"><span data-stu-id="a7df3-118">**Yes, generate a full backup of the primary database and restore it to the secondary database**</span></span>  
 <span data-ttu-id="a7df3-119">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 에서 주 데이터베이스를 백업하여 보조 서버에 복원하는 방법으로 보조 데이터베이스를 구성하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="a7df3-119">Have [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] configure your secondary database by backing up the primary database and restoring it on the secondary server.</span></span> <span data-ttu-id="a7df3-120">**보조 데이터베이스** 입력란에 새 데이터베이스 이름을 입력한 경우 복원 작업을 실행하는 과정의 일부로 해당 데이터베이스가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="a7df3-120">If you entered a new database name in the **Secondary database** box, the database will be created as part of the restore operation.</span></span>  
  
 <span data-ttu-id="a7df3-121">**복원 옵션**</span><span class="sxs-lookup"><span data-stu-id="a7df3-121">**Restore Options**</span></span>  
 <span data-ttu-id="a7df3-122">보조 서버에서 기본 위치 이외의 위치에 보조 데이터베이스의 데이터 및 로그 파일을 복원하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a7df3-122">Click if you want to restore the data and log files for the secondary database into nondefault locations on the secondary server.</span></span>  
  
 <span data-ttu-id="a7df3-123">이 단추를 클릭하면 **복원 옵션** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="a7df3-123">This button opens the **Restore Options** dialog box.</span></span> <span data-ttu-id="a7df3-124">이 대화 상자에서 기본 폴더 이외의 폴더 경로를 지정하여 보조 데이터베이스와 로그 파일을 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a7df3-124">There, you can specify paths to nondefault folders where you want the secondary database and its log to reside.</span></span> <span data-ttu-id="a7df3-125">두 폴더 중 하나라도 지정하면 나머지 폴더도 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a7df3-125">If you specify either folder, you must specify both.</span></span>  
  
 <span data-ttu-id="a7df3-126">경로는 보조 서버의 로컬 드라이브를 나타내야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a7df3-126">The paths must refer to drives that are local to the secondary server.</span></span> <span data-ttu-id="a7df3-127">또한 경로는 로컬 드라이브 문자와 콜론(예: `C:`)으로 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a7df3-127">Also, the paths must begin with a local drive letter and colon (for example, `C:`).</span></span> <span data-ttu-id="a7df3-128">매핑된 드라이브 문자 또는 네트워크 경로는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a7df3-128">Mapped drive letters or network paths are invalid.</span></span>  
  
 <span data-ttu-id="a7df3-129">**복원 옵션** 단추를 클릭했지만 기본 폴더를 사용하려는 경우에는 **복원 옵션** 대화 상자를 취소하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="a7df3-129">If you click the **Restore Options** button and then decide that you want to use the default folders, we recommend that you cancel the **Restore Options** dialog box.</span></span> <span data-ttu-id="a7df3-130">이미 다른 위치를 지정한 경우에 다시 기본 위치를 사용하려면 **복원 옵션** 을 다시 클릭하고 입력란의 내용을 지운 다음 확인을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a7df3-130">If you have already specified nondefault locations and now want to use the default locations instead, click **Restore Options** again, clear the text boxes, and click OK.</span></span>  
  
 <span data-ttu-id="a7df3-131">**예, 주 데이터베이스의 기존 백업을 보조 데이터베이스에 복원합니다.**</span><span class="sxs-lookup"><span data-stu-id="a7df3-131">**Yes, restore an existing backup of the primary database to the secondary database**</span></span>  
 <span data-ttu-id="a7df3-132">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 에서 주 데이터베이스의 기존 백업을 사용하여 보조 데이터베이스를 초기화하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="a7df3-132">Have [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] use an existing backup of your primary database to initialize the secondary database.</span></span> <span data-ttu-id="a7df3-133">**백업 파일** 입력란에 해당 백업 파일이 저장된 위치를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="a7df3-133">Type the location of that backup in the **Backup file** box.</span></span> <span data-ttu-id="a7df3-134">보조 데이터베이스 입력란에 새 데이터베이스 이름을 입력한 경우 복원 작업을 실행하는 과정의 일부로서 해당 데이터베이스가 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="a7df3-134">If you entered a new database name in the Secondary database box, the database will be created as part of the restore operation.</span></span>  
  
 <span data-ttu-id="a7df3-135">**백업 파일**</span><span class="sxs-lookup"><span data-stu-id="a7df3-135">**Backup file**</span></span>  
 <span data-ttu-id="a7df3-136">**예, 주 데이터베이스의 기존 백업을 보조 데이터베이스에 복원합니다.** 옵션을 선택한 경우에 보조 데이터베이스를 초기화하는 데 사용할 전체 데이터베이스 백업의 경로와 파일 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="a7df3-136">Type the path and filename of the full database backup you want to use to initialize the secondary database if you chose the **Yes, restore and existing backup of the primary database to the secondary database option**.</span></span>  
  
 <span data-ttu-id="a7df3-137">**복원 옵션**</span><span class="sxs-lookup"><span data-stu-id="a7df3-137">**Restore Options**</span></span>  
 <span data-ttu-id="a7df3-138">이 도움말 항목의 앞에서 설명한 내용을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="a7df3-138">See the description of this button earlier in this topic.</span></span>  
  
 <span data-ttu-id="a7df3-139">**아니요, 보조 데이터베이스가 초기화되었습니다.**</span><span class="sxs-lookup"><span data-stu-id="a7df3-139">**No, the secondary database is initialized**</span></span>  
 <span data-ttu-id="a7df3-140">보조 데이터베이스가 이미 초기화되었고 주 데이터베이스로부터 트랜잭션 로그 백업을 받을 준비가 되었음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a7df3-140">Specify that the secondary database is already initialized and ready to accept transaction log backups from the primary database.</span></span> <span data-ttu-id="a7df3-141">이 옵션은 **보조 데이터베이스** 입력란에 새 데이터베이스 이름을 입력한 경우에는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a7df3-141">This option is not available if you typed a new database name in the **Secondary database** box.</span></span>  
  
 <span data-ttu-id="a7df3-142">**파일 복사 탭**</span><span class="sxs-lookup"><span data-stu-id="a7df3-142">**Copy Files tab**</span></span>  
 <span data-ttu-id="a7df3-143">옵션은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="a7df3-143">The options are as follows:</span></span>  
  
 <span data-ttu-id="a7df3-144">**복사한 파일의 대상 폴더**</span><span class="sxs-lookup"><span data-stu-id="a7df3-144">**Destination folder for copied files**</span></span>  
 <span data-ttu-id="a7df3-145">보조 데이터베이스를 복원하기 위해 트랜잭션 로그 백업을 복사할 경로를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="a7df3-145">Type the path to which transaction log backups should be copied for restoration to the secondary database.</span></span> <span data-ttu-id="a7df3-146">일반적으로 이 경로는 보조 서버에 있는 폴더의 로컬 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="a7df3-146">This is usually a local path to a folder located on the secondary server.</span></span> <span data-ttu-id="a7df3-147">폴더가 다른 서버에 있으면 해당 폴더의 UNC 경로를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a7df3-147">If the folder is located on another server, however, you must specify a UNC path to the folder.</span></span> <span data-ttu-id="a7df3-148">보조 서버 인스턴스의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 서비스 계정에는 이 폴더에 대한 읽기 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a7df3-148">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service account of the secondary server instance must have Read permissions on this folder.</span></span> <span data-ttu-id="a7df3-149">또한 보조 서버 인스턴스에서 복사 및 복원 작업을 실행하는 데 사용할 프록시 계정에 이 네트워크 공유를 읽고 쓸 수 있는 권한을 부여해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a7df3-149">You must also grant read and write permissions on this network share to the proxy accounts under which the copy and restore jobs will run at the secondary server instances.</span></span> <span data-ttu-id="a7df3-150">기본적으로 이 계정은 보조 서버 인스턴스의 SQL Server 에이전트 서비스 계정이지만 sysadmin 권한이 있는 사용자가 다른 프록시 계정을 선택하여 작업에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a7df3-150">By default, this is the SQL Server Agent service account of the secondary server instance, but a sysadmin can choose other proxy accounts for the jobs.</span></span>  
  
 <span data-ttu-id="a7df3-151">**다음 기간 이후에 복사한 파일 삭제**</span><span class="sxs-lookup"><span data-stu-id="a7df3-151">**Delete copied files after**</span></span>  
 <span data-ttu-id="a7df3-152">복사한 트랜잭션 로그 백업 파일을 삭제하기 전에 대상 폴더에 보존할 기간을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a7df3-152">Choose the length of time you want the copied transaction log backup files to remain in the destination folder before being deleted.</span></span>  
  
 <span data-ttu-id="a7df3-153">**작업 이름**</span><span class="sxs-lookup"><span data-stu-id="a7df3-153">**Job name**</span></span>  
 <span data-ttu-id="a7df3-154">주 서버에서 보조 서버로 트랜잭션 로그 백업 파일을 복사하는 데 사용된 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 작업의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="a7df3-154">Displays the name of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job used to copy transaction log backup files from the primary server to the secondary server.</span></span> <span data-ttu-id="a7df3-155">처음 이 작업을 만들 때 입력란에 이름을 입력하여 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a7df3-155">When first creating this job, you can change the name by typing in the box.</span></span>  
  
 <span data-ttu-id="a7df3-156">**일정**</span><span class="sxs-lookup"><span data-stu-id="a7df3-156">**Schedule**</span></span>  
 <span data-ttu-id="a7df3-157">주 서버에서 보조 서버로 트랜잭션 로그 백업을 복사하는 SQL Server 에이전트 복사 작업의 현재 일정을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="a7df3-157">Displays the current schedule for the SQL Server Agent copy job to copy transaction log backups from the primary server to the secondary server.</span></span> <span data-ttu-id="a7df3-158">**일정...** 을 클릭하여 이 일정을 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a7df3-158">You can modify this schedule by clicking **Schedule...**.</span></span>  
  
 <span data-ttu-id="a7df3-159">**일정...**</span><span class="sxs-lookup"><span data-stu-id="a7df3-159">**Schedule...**</span></span>  
 <span data-ttu-id="a7df3-160">주 서버에서 보조 서버로 트랜잭션 로그 백업을 복사하는 SQL Server 에이전트 작업의 매개 변수를 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="a7df3-160">Modify the parameters of the SQL Server Agent job that copies transaction log backups from the primary server to the secondary server.</span></span>  
  
 <span data-ttu-id="a7df3-161">**이 작업 비활성화**</span><span class="sxs-lookup"><span data-stu-id="a7df3-161">**Disable this job**</span></span>  
 <span data-ttu-id="a7df3-162">SQL Server 에이전트 복사 작업을 일시 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="a7df3-162">Suspend the SQL Server Agent copy job.</span></span>  
  
 <span data-ttu-id="a7df3-163">**트랜잭션 로그 복원 탭**</span><span class="sxs-lookup"><span data-stu-id="a7df3-163">**Restore Transaction Log tab**</span></span>  
 <span data-ttu-id="a7df3-164">옵션은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="a7df3-164">The options are as follows:</span></span>  
  
 <span data-ttu-id="a7df3-165">**백업 복원 시 데이터베이스의 사용자 연결 끊기**</span><span class="sxs-lookup"><span data-stu-id="a7df3-165">**Disconnect users in the database when restoring backups**</span></span>  
 <span data-ttu-id="a7df3-166">트랜잭션 로그 백업을 복원하는 동안 자동으로 보조 데이터베이스에서 사용자의 연결을 끊습니다.</span><span class="sxs-lookup"><span data-stu-id="a7df3-166">Automatically disconnect users from the secondary database while transaction log backups are being restored.</span></span>  
  
 <span data-ttu-id="a7df3-167">**복구 안 함 모드**</span><span class="sxs-lookup"><span data-stu-id="a7df3-167">**No recovery mode**</span></span>  
 <span data-ttu-id="a7df3-168">보조 데이터베이스를 NORECOVERY 모드로 유지합니다.</span><span class="sxs-lookup"><span data-stu-id="a7df3-168">Leave the secondary database in NORECOVERY mode.</span></span>  
  
 <span data-ttu-id="a7df3-169">**대기 모드**</span><span class="sxs-lookup"><span data-stu-id="a7df3-169">**Standby mode**</span></span>  
 <span data-ttu-id="a7df3-170">보조 데이터베이스를 STANDBY 모드로 유지합니다.</span><span class="sxs-lookup"><span data-stu-id="a7df3-170">Leave the secondary database in STANDBY mode.</span></span> <span data-ttu-id="a7df3-171">이 모드를 선택하면 데이터베이스에서 읽기 전용 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a7df3-171">This mode will allow read-only operations to be performed on the database.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="a7df3-172">기존 보조 데이터베이스의 복구 모드를 변경하면(예: **복구 안 함 모드** 에서 **대기 모드**로) 다음 로그 백업이 데이터베이스로 복원된 후에만 변경 내용이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="a7df3-172">If you change the recovery mode of an existing secondary database, for example, from **No recovery mode** to **Standby mode**, the change takes effect only after the next log backup is restored to the database.</span></span>  
  
 <span data-ttu-id="a7df3-173">**최소 다음 기간 동안 백업 복원 지연**</span><span class="sxs-lookup"><span data-stu-id="a7df3-173">**Delay restoring backups at least**</span></span>  
 <span data-ttu-id="a7df3-174">보조 데이터베이스에 트랜잭션 로그 백업(있는 경우)을 복원하기 전에 지연하는 시간을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a7df3-174">Choose the delay before transaction log backups are restored to the secondary database, if any.</span></span>  
  
 <span data-ttu-id="a7df3-175">**다음 기간 내에 복원이 발생하지 않으면 경고**</span><span class="sxs-lookup"><span data-stu-id="a7df3-175">**Alert if no restore occurs within**</span></span>  
 <span data-ttu-id="a7df3-176">트랜잭션 로그 복원이 수행되지 않았다는 경고를 발생시키기 전까지 로그 전달에서 기다리는 시간을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a7df3-176">Choose the amount of time you want log shipping to wait before raising an alert that no transaction log restores have occurred.</span></span>  
  
 <span data-ttu-id="a7df3-177">**작업 이름**</span><span class="sxs-lookup"><span data-stu-id="a7df3-177">**Job name**</span></span>  
 <span data-ttu-id="a7df3-178">보조 데이터베이스에 트랜잭션 로그 백업을 복원하는 데 사용된 SQL Server 에이전트 작업의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="a7df3-178">Displays the name of the SQL Server Agent job used to restore transaction log backups to the secondary database.</span></span> <span data-ttu-id="a7df3-179">처음 이 작업을 만들 때 입력란에 이름을 입력하여 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a7df3-179">When first creating this job, you can change the name by typing in the box.</span></span>  
  
 <span data-ttu-id="a7df3-180">**일정**</span><span class="sxs-lookup"><span data-stu-id="a7df3-180">**Schedule**</span></span>  
 <span data-ttu-id="a7df3-181">보조 데이터베이스에 트랜잭션 로그 백업을 복원하는 데 사용된 SQL Server 에이전트 작업의 현재 일정을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="a7df3-181">Displays the current schedule for the SQL Server Agent job used for restoring transaction log backups to the secondary database.</span></span> <span data-ttu-id="a7df3-182">**일정...** 을 클릭하여 이 옵션을 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a7df3-182">You can modify this option by clicking **Schedule...**.</span></span>  
  
 <span data-ttu-id="a7df3-183">**일정...**</span><span class="sxs-lookup"><span data-stu-id="a7df3-183">**Schedule...**</span></span>  
 <span data-ttu-id="a7df3-184">SQL Server 에이전트 복원 작업과 연관된 매개 변수를 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="a7df3-184">Modify the parameters associate with the SQL Server Agent restore job.</span></span>  
  
 <span data-ttu-id="a7df3-185">**이 작업 비활성화**</span><span class="sxs-lookup"><span data-stu-id="a7df3-185">**Disable this job**</span></span>  
 <span data-ttu-id="a7df3-186">보조 데이터베이스로의 복원 작업을 일시 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="a7df3-186">Suspend restore operations to the secondary database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7df3-187">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a7df3-187">See Also</span></span>  
 <span data-ttu-id="a7df3-188">[SQL Server 데이터베이스 백업 및 복원](../backup-restore/back-up-and-restore-of-sql-server-databases.md) </span><span class="sxs-lookup"><span data-stu-id="a7df3-188">[Back Up and Restore of SQL Server Databases](../backup-restore/back-up-and-restore-of-sql-server-databases.md) </span></span>  
 [<span data-ttu-id="a7df3-189">로그 전달 정보&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a7df3-189">About Log Shipping &#40;SQL Server&#41;</span></span>](../../database-engine/log-shipping/about-log-shipping-sql-server.md)  
  
  
