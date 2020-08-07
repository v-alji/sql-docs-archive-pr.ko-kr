---
title: 다른 컴퓨터로 보고서 서버 데이터베이스 이동(SSRS 기본 모드) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 44a9854d-e333-44f6-bdc7-8837b9f34416
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 49fd35f57cf783b262b3c690e3047e5f479ab193
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727915"
---
# <a name="moving-the-report-server-databases-to-another-computer-ssrs-native-mode"></a><span data-ttu-id="6549e-102">다른 컴퓨터로 보고서 서버 데이터베이스 이동(SSRS 기본 모드)</span><span class="sxs-lookup"><span data-stu-id="6549e-102">Moving the Report Server Databases to Another Computer (SSRS Native Mode)</span></span>
  <span data-ttu-id="6549e-103">설치에 사용 되는 보고서 서버 데이터베이스를 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] 다른 컴퓨터에 있는 인스턴스로 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6549e-103">You can move the report server databases that are used in an installation [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] to an instance that is on a different computer.</span></span> <span data-ttu-id="6549e-104">reportserver 데이터베이스와 reportservertempdb 데이터베이스를 모두 이동하거나 함께 복사해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6549e-104">Both the reportserver and reportservertempdb databases must be moved or copied together.</span></span> <span data-ttu-id="6549e-105">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 를 설치하려면 두 데이터베이스가 모두 필요합니다. reportservertempdb 데이터베이스는 이동하는 주 reportserver 데이터베이스와 이름으로 관련되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6549e-105">A [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installation requires both databases; the reportservertempdb database must be related by name to the primary reportserver database you are moving.</span></span>  
  
 <span data-ttu-id="6549e-106">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]기본 모드입니다.</span><span class="sxs-lookup"><span data-stu-id="6549e-106">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native mode.</span></span>  
  
 <span data-ttu-id="6549e-107">데이터베이스를 이동해도 보고서 서버 항목에 대해 현재 정의되어 있는 예약된 작업에는 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6549e-107">Moving a database does not effect scheduled operations that are currently defined for report server items.</span></span>  
  
-   <span data-ttu-id="6549e-108">일정은 보고서 서버 서비스를 처음으로 다시 시작할 때 다시 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="6549e-108">Schedules will be recreated the first time that you restart the Report Server service.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="6549e-109">에이전트 작업은 새 데이터베이스 인스턴스에서 다시 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="6549e-109">Agent jobs that are used to trigger a schedule will be recreated on the new database instance.</span></span> <span data-ttu-id="6549e-110">해당 작업을 새 컴퓨터로 이동하지 않아도 되지만 더 이상 사용되지 않을 컴퓨터 작업은 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6549e-110">You do not have to move the jobs to the new computer, but you might want to delete jobs on the computer that will no longer be used.</span></span>  
  
-   <span data-ttu-id="6549e-111">구독, 캐시된 보고서 및 스냅샷은 이동된 데이터베이스에 그대로 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="6549e-111">Subscriptions, cached reports, and snapshots are preserved in the moved database.</span></span> <span data-ttu-id="6549e-112">데이터베이스를 이동한 후 스냅샷이 새로 고친 데이터를 가져오지 않은 경우 보고서 관리자에서 스냅샷 옵션의 선택을 취소하고 **적용** 을 클릭하여 변경 내용을 저장합니다. 그런 다음 일정을 다시 만들고 **적용** 을 클릭하여 변경 내용을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="6549e-112">If a snapshot is not picking up refreshed data after the database is moved, clear the snapshot options in Report Manager, click **Apply** to save your changes, re-create the schedule, and click **Apply** again to save your changes.</span></span>  
  
-   <span data-ttu-id="6549e-113">reportservertempdb에 저장된 임시 보고서 및 사용자 세션 데이터는 해당 데이터베이스를 이동해도 그대로 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="6549e-113">Temporary report and user session data that is stored in reportservertempdb are persisted when you move that database.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="6549e-114">에서는 백업 및 복원, 연결 및 분리, 복사를 비롯한 여러 가지 방법으로 데이터베이스를 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6549e-114">provides several approaches for moving databases, including backup and restore, attach and detach, and copy.</span></span> <span data-ttu-id="6549e-115">기존 데이터베이스 위치를 새 서버 인스턴스로 다시 지정하는 데 이러한 방법이 모두 적합한 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="6549e-115">Not all approaches are appropriate for relocating an existing database to a new server instance.</span></span> <span data-ttu-id="6549e-116">보고서 서버 데이터베이스를 이동하는 데 사용해야 하는 방법은 시스템 가용성 요구 사항에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="6549e-116">The approach that you should use to move the report server database will vary depending on your system availability requirements.</span></span> <span data-ttu-id="6549e-117">보고서 서버 데이터베이스를 이동하는 가장 쉬운 방법은 데이터베이스를 분리 후 연결하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="6549e-117">The easiest way to move the report server databases is to attach and detach them.</span></span> <span data-ttu-id="6549e-118">그러나 이 방법을 사용하려면 데이터베이스를 분리하는 동안 보고서 서버를 오프라인 상태로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6549e-118">However, this approach requires that you take the report server offline while you detach the database.</span></span> <span data-ttu-id="6549e-119">서비스 장애를 최소화하려면 백업 및 복원을 사용하는 것이 낫지만 [!INCLUDE[tsql](../../includes/tsql-md.md)] 명령을 실행하여 작업을 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6549e-119">Backup and restore is a better choice if you want to minimize service disruptions, but you must run [!INCLUDE[tsql](../../includes/tsql-md.md)] commands to perform the operations.</span></span> <span data-ttu-id="6549e-120">데이터베이스 복사 마법사를 사용하여 데이터베이스를 복사할 경우 데이터베이스의 사용 권한 설정이 유지되지 않으므로 이 방법은 사용하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="6549e-120">Copying the database is not recommended (specifically, by using the Copy Database Wizard); it does not preserve permission settings in the database.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="6549e-121">이 항목에 설명된 단계는 기존 설치에서 보고서 서버 데이터베이스를 재배치하는 작업만 수행하려는 경우에 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="6549e-121">The steps provided in this topic are recommended when relocating the report server database is the only change you are making to the existing installation.</span></span> <span data-ttu-id="6549e-122">전체 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 설치를 마이그레이션하려면, 즉 데이터베이스를 이동하고 해당 데이터베이스를 사용하는 보고서 서버 Windows 서비스의 ID를 변경하려면 연결을 다시 구성하고 암호화 키를 다시 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6549e-122">Migrating an entire [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installation (that is, moving the database and changing the identity of the Report Server Windows service that uses the database) requires connection reconfiguration and an encryption key reset.</span></span>  
  
## <a name="detaching-and-attaching-the-report-server-databases"></a><span data-ttu-id="6549e-123">보고서 서버 데이터베이스 분리 및 연결</span><span class="sxs-lookup"><span data-stu-id="6549e-123">Detaching and Attaching the Report Server Databases</span></span>  
 <span data-ttu-id="6549e-124">보고서 서버를 오프라인 상태로 만들 수 있는 경우 데이터베이스를 분리한 후 사용하려는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스로 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6549e-124">If you can take the report server offline, you can detach the databases to move them to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance you want to use.</span></span> <span data-ttu-id="6549e-125">이 방법을 사용하면 데이터베이스의 사용 권한이 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="6549e-125">This approach preserves permissions in the databases.</span></span> <span data-ttu-id="6549e-126">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 데이터베이스를 사용하는 경우 이를 다른 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 인스턴스로 이동해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6549e-126">If you are using a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] database, you must move it to another [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] instance.</span></span> <span data-ttu-id="6549e-127">데이터베이스를 이동한 후에는 보고서 서버와 보고서 서버 데이터베이스의 연결을 다시 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6549e-127">After you move the databases, you must reconfigure the report server connection to the report server database.</span></span> <span data-ttu-id="6549e-128">스케일 아웃 배포를 실행하려면 배포 환경의 각 보고서 서버에 대한 보고서 서버 데이터베이스 연결을 다시 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6549e-128">If you are running a scale-out deployment, you must reconfigure the report server database connection for each report server in the deployment.</span></span>  
  
 <span data-ttu-id="6549e-129">다음 단계에 따라 데이터베이스를 이동하십시오.</span><span class="sxs-lookup"><span data-stu-id="6549e-129">Use the following steps to move the databases:</span></span>  
  
1.  <span data-ttu-id="6549e-130">이동하려는 보고서 서버 데이터베이스의 암호화 키를 백업합니다.</span><span class="sxs-lookup"><span data-stu-id="6549e-130">Backup the encryption keys for the report server database you want to move.</span></span> <span data-ttu-id="6549e-131">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 구성 도구를 사용하여 키를 백업할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6549e-131">You can use the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration tool backup the keys.</span></span>  
  
2.  <span data-ttu-id="6549e-132">보고서 서버 서비스를 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="6549e-132">Stop the Report Server service.</span></span> <span data-ttu-id="6549e-133">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 구성 도구를 사용하여 서비스를 중지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6549e-133">You can use the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration tool to stop the service.</span></span>  
  
3.  <span data-ttu-id="6549e-134">를 시작 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 하 고 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 보고서 서버 데이터베이스를 호스팅하는 인스턴스에 대 한 연결을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="6549e-134">Start [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] and open a connection to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance that hosts the report server databases.</span></span>  
  
4.  <span data-ttu-id="6549e-135">보고서 서버 데이터베이스를 마우스 오른쪽 단추로 클릭하고 태스크를 가리킨 다음 **분리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6549e-135">Right-click the report server database, point to Tasks, and click **Detach**.</span></span> <span data-ttu-id="6549e-136">보고서 서버 임시 데이터베이스에 대해 이 단계를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="6549e-136">Repeat this step for the report server temporary database.</span></span>  
  
5.  <span data-ttu-id="6549e-137">사용하려는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스의 데이터 폴더로 .mdf 및 .ldf 파일을 복사하거나 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="6549e-137">Copy or move the .mdf and .ldf files to the Data folder of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance you want to use.</span></span> <span data-ttu-id="6549e-138">두 개의 데이터베이스를 이동하고 있으므로 이동하거나 복사하는 파일이 모두 네 개인지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="6549e-138">Because you are moving two databases, make sure that you move or copy all four files.</span></span>  
  
6.  <span data-ttu-id="6549e-139">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]에서 보고서 서버 데이터베이스를 호스팅할 새 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 대한 연결을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="6549e-139">In [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], open a connection to the new [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance that will host the report server databases.</span></span>  
  
7.  <span data-ttu-id="6549e-140">데이터베이스 노드를 마우스 오른쪽 단추로 클릭한 다음 **연결**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6549e-140">Right-click the Databases node, and then click **Attach**.</span></span>  
  
8.  <span data-ttu-id="6549e-141">**추가** 를 클릭하고 연결할 보고서 서버 데이터베이스 .mdf 및 .ldf 파일을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6549e-141">Click **Add** to select the report server database .mdf and .ldf files that you want to attach.</span></span> <span data-ttu-id="6549e-142">보고서 서버 임시 데이터베이스에 대해 이 단계를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="6549e-142">Repeat this step for the report server temporary database.</span></span>  
  
9. <span data-ttu-id="6549e-143">데이터베이스가 연결 된 후 `RSExecRole` 이 보고서 서버 데이터베이스와 임시 데이터베이스의 데이터베이스 역할 인지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="6549e-143">After the databases are attached, verify that the `RSExecRole` is a database role in the report server database and temporary database.</span></span> <span data-ttu-id="6549e-144">`RSExecRole`에는 보고서 서버 데이터베이스 테이블에 대 한 select, insert, update, delete 및 reference 권한과 저장 프로시저에 대 한 execute 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6549e-144">`RSExecRole` must have select, insert, update, delete, and reference permissions on the report server database tables, and execute permissions on the stored procedures.</span></span> <span data-ttu-id="6549e-145">자세한 내용은 [RSExecRole 만들기](../security/create-the-rsexecrole.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6549e-145">For more information, see [Create the RSExecRole](../security/create-the-rsexecrole.md).</span></span>  
  
10. <span data-ttu-id="6549e-146">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 구성 도구를 시작하고 보고서 서버에 대한 연결을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="6549e-146">Start the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration tool and open a connection to the report server.</span></span>  
  
11. <span data-ttu-id="6549e-147">데이터베이스 페이지에서 새 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스를 선택한 다음 **연결**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6549e-147">On the Database page, select the new [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance, and then click **Connect**.</span></span>  
  
12. <span data-ttu-id="6549e-148">방금 이동한 보고서 서버 데이터베이스를 선택한 다음 **적용**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6549e-148">Select the report server database that you just moved, and then click **Apply**.</span></span>  
  
13. <span data-ttu-id="6549e-149">암호화 키 페이지에서 복원을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6549e-149">On the Encryption Keys page, click Restore.</span></span> <span data-ttu-id="6549e-150">키의 백업 복사본이 들어 있는 파일과 파일의 잠금을 해제하기 위한 암호를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6549e-150">Specify the file that contains the backup copy of the keys and the password to unlock the file.</span></span>  
  
14. <span data-ttu-id="6549e-151">보고서 서버 서비스를 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="6549e-151">Restart the Report Server service.</span></span>  
  
## <a name="backing-up-and-restoring-the-report-server-databases"></a><span data-ttu-id="6549e-152">보고서 서버 데이터베이스 백업 및 복원</span><span class="sxs-lookup"><span data-stu-id="6549e-152">Backing Up and Restoring the Report Server Databases</span></span>  
 <span data-ttu-id="6549e-153">보고서 서버를 오프라인으로 설정할 수 없는 경우 백업 후 복원 방법을 사용하여 보고서 서버 데이터베이스 위치를 다시 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6549e-153">If you cannot take the report server offline, you can use backup and restore to relocate the report server databases.</span></span> <span data-ttu-id="6549e-154">백업 및 복원을 수행하려면 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6549e-154">You must use [!INCLUDE[tsql](../../includes/tsql-md.md)] statements to do the backup and restore.</span></span> <span data-ttu-id="6549e-155">데이터베이스를 복원한 후에 새 서버 인스턴스의 데이터베이스를 사용하도록 보고서 서버를 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6549e-155">After you restore the databases, you must configure the report server to use the database on the new server instance.</span></span> <span data-ttu-id="6549e-156">자세한 내용은 이 항목의 마지막 부분에 있는 지침을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="6549e-156">For more information, see the instructions at the end of this topic.</span></span>  
  
### <a name="using-backup-and-copy_only-to-backup-the-report-server-databases"></a><span data-ttu-id="6549e-157">BACKUP 및 COPY_ALL을 사용하여 보고서 서버 데이터베이스 백업</span><span class="sxs-lookup"><span data-stu-id="6549e-157">Using BACKUP and COPY_ONLY to Backup the Report Server Databases</span></span>  
 <span data-ttu-id="6549e-158">데이터베이스를 백업할 때는 COPY_ONLY 인수를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="6549e-158">When backing up the databases, set the COPY_ONLY argument.</span></span> <span data-ttu-id="6549e-159">두 데이터베이스와 로그 파일을 모두 백업해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6549e-159">Be sure to back up both of the databases and log files.</span></span>  
  
```  
-- To permit log backups, before the full database backup, alter the database   
-- to use the full recovery model.  
USE master;  
GO  
ALTER DATABASE ReportServer  
   SET RECOVERY FULL  
  
-- If the ReportServerData device does not exist yet, create it.   
USE master  
GO  
EXEC sp_addumpdevice 'disk', 'ReportServerData',   
'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\BACKUP\ReportServerData.bak'  
  
-- Create a logical backup device, ReportServerLog.  
USE master  
GO  
EXEC sp_addumpdevice 'disk', 'ReportServerLog',   
'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\BACKUP\ReportServerLog.bak'  
  
-- Back up the full ReportServer database.  
BACKUP DATABASE ReportServer  
   TO ReportServerData  
   WITH COPY_ONLY  
  
-- Back up the ReportServer log.  
BACKUP LOG ReportServer  
   TO ReportServerLog  
   WITH COPY_ONLY  
  
-- To permit log backups, before the full database backup, alter the database   
-- to use the full recovery model.  
USE master;  
GO  
ALTER DATABASE ReportServerTempdb  
   SET RECOVERY FULL  
  
-- If the ReportServerTempDBData device does not exist yet, create it.   
USE master  
GO  
EXEC sp_addumpdevice 'disk', 'ReportServerTempDBData',   
'C:\Program Files\Microsoft SQL Server\MSSQL11.MSSQLSERVER\MSSQL\BACKUP\ReportServerTempDBData.bak'  
  
-- Create a logical backup device, ReportServerTempDBLog.  
USE master  
GO  
EXEC sp_addumpdevice 'disk', 'ReportServerTempDBLog',   
'C:\Program Files\Microsoft SQL Server\MSSQL11.MSSQLSERVER\MSSQL\BACKUP\ReportServerTempDBLog.bak'  
  
-- Back up the full ReportServerTempDB database.  
BACKUP DATABASE ReportServerTempDB  
   TO ReportServerTempDBData  
   WITH COPY_ONLY  
  
-- Back up the ReportServerTempDB log.  
BACKUP LOG ReportServerTempDB  
   TO ReportServerTempDBLog  
   WITH COPY_ONLY  
```  
  
### <a name="using-restore-and-move-to-relocate-the-report-server-databases"></a><span data-ttu-id="6549e-160">RESTORE 및 MOVE를 사용하여 보고서 서버 데이터베이스 위치 다시 지정</span><span class="sxs-lookup"><span data-stu-id="6549e-160">Using RESTORE and MOVE to Relocate the Report Server Databases</span></span>  
 <span data-ttu-id="6549e-161">데이터베이스를 복원할 때는 경로를 지정할 수 있도록 MOVE 인수를 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6549e-161">When restoring the databases, be sure to include the MOVE argument so that you can specify a path.</span></span> <span data-ttu-id="6549e-162">NORECOVERY 인수를 사용하여 초기 복원을 수행합니다. 이렇게 하면 데이터베이스의 상태가 RESTORING으로 유지되므로 로그 백업을 검토하여 복원할 사항을 결정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6549e-162">Use the NORECOVERY argument to perform the initial restore; this keeps the database in a RESTORING state, giving you time to review log backups to determine which one to restore.</span></span> <span data-ttu-id="6549e-163">마지막 단계는 RECOVERY 인수를 사용하여 RESTORE 작업을 반복하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="6549e-163">The final step repeats the RESTORE operation with the RECOVERY argument.</span></span>  
  
 <span data-ttu-id="6549e-164">MOVE 인수에는 데이터 파일의 논리적 이름을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6549e-164">The MOVE argument uses the logical name of the data file.</span></span> <span data-ttu-id="6549e-165">논리적 이름을 찾으려면 `RESTORE FILELISTONLY FROM DISK='C:\ReportServerData.bak';`</span><span class="sxs-lookup"><span data-stu-id="6549e-165">To find the logical name, execute the following statement: `RESTORE FILELISTONLY FROM DISK='C:\ReportServerData.bak';`</span></span>  
  
 <span data-ttu-id="6549e-166">다음 예에는 복원할 로그 파일의 위치를 지정할 수 있도록 FILE 인수가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6549e-166">The following examples include the FILE argument so that you can specify the file position of the log file to restore.</span></span> <span data-ttu-id="6549e-167">파일 위치를 찾으려면 `RESTORE HEADERONLY FROM DISK='C:\ReportServerData.bak';`</span><span class="sxs-lookup"><span data-stu-id="6549e-167">To find the file position, execute the following statement: `RESTORE HEADERONLY FROM DISK='C:\ReportServerData.bak';`</span></span>  
  
 <span data-ttu-id="6549e-168">데이터베이스와 로그 파일을 복원할 때 RESTORE 작업을 각각 별도로 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6549e-168">When restoring the database and log files, you should run each RESTORE operation separately.</span></span>  
  
```  
-- Restore the report server database and move to new instance folder   
RESTORE DATABASE ReportServer  
   FROM DISK='C:\ReportServerData.bak'  
   WITH NORECOVERY,   
      MOVE 'ReportServer' TO   
         'C:\Program Files\Microsoft SQL Server\MSSQL11.MSSQLSERVER\MSSQL\Data\ReportServer.mdf',   
      MOVE 'ReportServer_log' TO  
         'C:\Program Files\Microsoft SQL Server\MSSQL11.MSSQLSERVER\MSSQL\Data\ReportServer_Log.ldf';  
GO  
  
-- Restore the report server log file to new instance folder   
RESTORE LOG ReportServer  
   FROM DISK='C:\ReportServerData.bak'  
   WITH NORECOVERY, FILE=2  
      MOVE 'ReportServer' TO   
         'C:\Program Files\Microsoft SQL Server\MSSQL11.MSSQLSERVER\MSSQL\Data\ReportServer.mdf',   
      MOVE 'ReportServer_log' TO  
         'C:\Program Files\Microsoft SQL Server\MSSQL11.MSSQLSERVER\MSSQL\Data\ReportServer_Log.ldf';  
GO  
  
-- Restore and move the report server temporary database  
RESTORE DATABASE ReportServerTempdb  
   FROM DISK='C:\ReportServerTempDBData.bak'  
   WITH NORECOVERY,   
      MOVE 'ReportServerTempDB' TO   
         'C:\Program Files\Microsoft SQL Server\MSSQL11.MSSQLSERVER\MSSQL\Data\ReportServerTempDB.mdf',   
      MOVE 'ReportServerTempDB_log' TO  
         'C:\Program Files\Microsoft SQL Server\MSSQL11.MSSQLSERVER\MSSQL\Data\REportServerTempDB_Log.ldf';  
GO  
  
-- Restore the temporary database log file to new instance folder   
RESTORE LOG ReportServerTempdb  
   FROM DISK='C:\ReportServerTempDBData.bak'  
   WITH NORECOVERY, FILE=2  
      MOVE 'ReportServerTempDB' TO   
         'C:\Program Files\Microsoft SQL Server\MSSQL11.MSSQLSERVER\MSSQL\Data\ReportServerTempDB.mdf',   
      MOVE 'ReportServerTempDB_log' TO  
         'C:\Program Files\Microsoft SQL Server\MSSQL11.MSSQLSERVER\MSSQL\Data\REportServerTempDB_Log.ldf';  
GO  
  
-- Perform final restore  
RESTORE DATABASE ReportServer  
   WITH RECOVERY  
GO  
  
-- Perform final restore  
RESTORE DATABASE ReportServerTempDB  
   WITH RECOVERY  
GO  
```  
  
### <a name="how-to-configure-the-report-server-database-connection"></a><span data-ttu-id="6549e-169">보고서 서버 데이터베이스 연결을 구성하는 방법</span><span class="sxs-lookup"><span data-stu-id="6549e-169">How to Configure the Report Server Database Connection</span></span>  
  
1.  <span data-ttu-id="6549e-170">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 구성 관리자를 시작하고 보고서 서버에 대한 연결을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="6549e-170">Start the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager and open a connection to the report server.</span></span>  
  
2.  <span data-ttu-id="6549e-171">데이터베이스 페이지에서 **데이터베이스 변경**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6549e-171">On the Database page, click **Change Database**.</span></span> <span data-ttu-id="6549e-172">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6549e-172">Click **Next**.</span></span>  
  
3.  <span data-ttu-id="6549e-173">**기존 보고서 서버 데이터베이스 선택**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6549e-173">Click **Choose an existing report server database**.</span></span> <span data-ttu-id="6549e-174">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6549e-174">Click **Next**.</span></span>  
  
4.  <span data-ttu-id="6549e-175">이제 보고서 서버 데이터베이스를 호스팅하는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 를 선택하고 **연결 테스트**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6549e-175">Select the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that now hosts the report server database and click **Test Connection**.</span></span> <span data-ttu-id="6549e-176">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6549e-176">Click **Next**.</span></span>  
  
5.  <span data-ttu-id="6549e-177">데이터베이스 이름에서 사용하려는 보고서 서버 데이터베이스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6549e-177">In Database Name, select the report server database that you want to use.</span></span> <span data-ttu-id="6549e-178">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6549e-178">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="6549e-179">자격 증명에 보고서 서버가 보고서 서버 데이터베이스에 연결하는 데 사용할 자격 증명을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6549e-179">In Credentials, specify the credentials that the report server will use to connect to the report server database.</span></span> <span data-ttu-id="6549e-180">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6549e-180">Click **Next**.</span></span>  
  
7.  <span data-ttu-id="6549e-181">**다음** , **마침**을 차례로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6549e-181">Click **Next** and then **Finish**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6549e-182">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]를 설치하려면 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 인스턴스에 `RSExecRole` 역할을 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6549e-182">A [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installation requires that the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] instance include the `RSExecRole` role.</span></span> <span data-ttu-id="6549e-183">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 구성 도구를 통해 보고서 서버 데이터베이스 연결을 설정하면 역할 만들기, 로그인 등록 및 역할 할당이 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="6549e-183">Role creation, login registration, and role assignments occur when you set the report server database connection through the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration tool.</span></span> <span data-ttu-id="6549e-184">rsconfig.exe 명령 프롬프트 유틸리티를 사용하는 등 다른 방법을 사용하여 연결을 구성하면 보고서 서버가 작동 상태에 있지 않게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6549e-184">If you use alternate approaches (specifically, if you use the rsconfig.exe command prompt utility) to configure the connection, the report server will not be in a working state.</span></span> <span data-ttu-id="6549e-185">이 경우 WMI 코드를 작성하여 보고서 서버를 사용할 수 있게 만들어야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6549e-185">You might have to write WMI code to make the report server available.</span></span> <span data-ttu-id="6549e-186">자세한 내용은 [Reporting Services WMI 공급자 액세스](../tools/access-the-reporting-services-wmi-provider.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6549e-186">For more information, see [Access the Reporting Services WMI Provider](../tools/access-the-reporting-services-wmi-provider.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6549e-187">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6549e-187">See Also</span></span>  
 <span data-ttu-id="6549e-188">[RSExecRole 만들기](../security/create-the-rsexecrole.md) </span><span class="sxs-lookup"><span data-stu-id="6549e-188">[Create the RSExecRole](../security/create-the-rsexecrole.md) </span></span>  
 <span data-ttu-id="6549e-189">[보고서 서버 서비스 시작 및 중지](start-and-stop-the-report-server-service.md) </span><span class="sxs-lookup"><span data-stu-id="6549e-189">[Start and Stop the Report Server Service](start-and-stop-the-report-server-service.md) </span></span>  
 <span data-ttu-id="6549e-190">[SSRS Configuration Manager &#40;보고서 서버 데이터베이스 연결 구성&#41;](../../sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md) </span><span class="sxs-lookup"><span data-stu-id="6549e-190">[Configure a Report Server Database Connection  &#40;SSRS Configuration Manager&#41;](../../sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md) </span></span>  
 <span data-ttu-id="6549e-191">[SSRS Configuration Manager &#40;무인 실행 계정을 구성&#41;](../install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md) </span><span class="sxs-lookup"><span data-stu-id="6549e-191">[Configure the Unattended Execution Account &#40;SSRS Configuration Manager&#41;](../install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md) </span></span>  
 <span data-ttu-id="6549e-192">[Reporting Services 구성 관리자&#40;기본 모드&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="6549e-192">[Reporting Services Configuration Manager &#40;Native Mode&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md) </span></span>  
 <span data-ttu-id="6549e-193">[rsconfig 유틸리티 &#40;SSRS&#41;](../tools/rsconfig-utility-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="6549e-193">[rsconfig Utility &#40;SSRS&#41;](../tools/rsconfig-utility-ssrs.md) </span></span>  
 <span data-ttu-id="6549e-194">[SSRS Configuration Manager &#40;암호화 키 구성 및 관리&#41;](../install-windows/ssrs-encryption-keys-manage-encryption-keys.md) </span><span class="sxs-lookup"><span data-stu-id="6549e-194">[Configure and Manage Encryption Keys &#40;SSRS Configuration Manager&#41;](../install-windows/ssrs-encryption-keys-manage-encryption-keys.md) </span></span>  
 [<span data-ttu-id="6549e-195">보고서 서버 데이터베이스&#40;SSRS 기본 모드&#41;</span><span class="sxs-lookup"><span data-stu-id="6549e-195">Report Server Database &#40;SSRS Native Mode&#41;</span></span>](report-server-database-ssrs-native-mode.md)  
  
  
