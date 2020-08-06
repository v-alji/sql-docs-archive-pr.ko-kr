---
title: 시스템 데이터베이스 이동 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- moving system databases
- disaster recovery [SQL Server], moving database files
- database files [SQL Server], moving
- data files [SQL Server], moving
- tempdb database [SQL Server], moving
- system databases [SQL Server], moving
- scheduled disk maintenace [SQL Server]
- moving databases
- msdb database [SQL Server], moving
- moving database files
- relocating database files
- planned database relocations [SQL Server]
- master database [SQL Server], moving
- model database [SQL Server], moving
- Resource database [SQL Server]
- databases [SQL Server], moving
ms.assetid: 72bb62ee-9602-4f71-be51-c466c1670878
author: stevestein
ms.author: sstein
ms.openlocfilehash: 748d781d6bbefb0dc710427a34ebd71ec7037fdb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743328"
---
# <a name="move-system-databases"></a><span data-ttu-id="39745-102">시스템 데이터베이스 이동</span><span class="sxs-lookup"><span data-stu-id="39745-102">Move System Databases</span></span>
  <span data-ttu-id="39745-103">이 항목에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 시스템 데이터베이스를 이동하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="39745-103">This topic describes how to move system databases in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="39745-104">시스템 데이터베이스 이동은 다음과 같은 경우에 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39745-104">Moving system databases may be useful in the following situations:</span></span>  
  
-   <span data-ttu-id="39745-105">오류 복구.</span><span class="sxs-lookup"><span data-stu-id="39745-105">Failure recovery.</span></span> <span data-ttu-id="39745-106">하드웨어 오류로 인해 데이터베이스가 주의 대상 모드에 있거나 종료된 경우를 예로 들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39745-106">For example, the database is in suspect mode or has shut down because of a hardware failure.</span></span>  
  
-   <span data-ttu-id="39745-107">계획된 재배치</span><span class="sxs-lookup"><span data-stu-id="39745-107">Planned relocation.</span></span>  
  
-   <span data-ttu-id="39745-108">예약된 디스크 유지 관리를 위한 재배치</span><span class="sxs-lookup"><span data-stu-id="39745-108">Relocation for scheduled disk maintenance.</span></span>  
  
 <span data-ttu-id="39745-109">다음 절차는 동일한 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스 내에서 데이터베이스 파일을 이동하는 경우에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="39745-109">The following procedures apply to moving database files within the same instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="39745-110">데이터베이스를 다른 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스나 다른 서버로 이동하려면 [백업 및 복원](../backup-restore/back-up-and-restore-of-sql-server-databases.md) 작업이나 [분리/연결](move-a-database-using-detach-and-attach-transact-sql.md) 작업을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="39745-110">To move a database to another instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] or to another server, use the [backup and restore](../backup-restore/back-up-and-restore-of-sql-server-databases.md) or [detach and attach](move-a-database-using-detach-and-attach-transact-sql.md) operations.</span></span>  
  
 <span data-ttu-id="39745-111">이 항목의 절차를 사용하려면 데이터베이스 파일의 논리적 이름이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="39745-111">The procedures in this topic require the logical name of the database files.</span></span> <span data-ttu-id="39745-112">논리적 파일 이름을 구하려면 [sys.master_files](/sql/relational-databases/system-catalog-views/sys-master-files-transact-sql) 카탈로그 뷰의 name 열을 쿼리합니다.</span><span class="sxs-lookup"><span data-stu-id="39745-112">To obtain the name, query the name column in the [sys.master_files](/sql/relational-databases/system-catalog-views/sys-master-files-transact-sql) catalog view.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="39745-113">시스템 데이터베이스를 이동한 다음 나중에 master 데이터베이스를 다시 작성하는 경우 다시 작성 작업에서 모든 시스템 데이터베이스를 기본 위치에 설치하기 때문에 시스템 데이터베이스를 다시 이동해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="39745-113">If you move a system database and later rebuild the master database, you must move the system database again because the rebuild operation installs all system databases to their default location.</span></span>  
  
##  <a name="in-this-topic"></a><a name="Intro"></a> <span data-ttu-id="39745-114">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="39745-114">**In This Topic**</span></span>  
  
-   [<span data-ttu-id="39745-115">계획 된 재배치 및 예약 된 디스크 유지 관리 절차</span><span class="sxs-lookup"><span data-stu-id="39745-115">Planned Relocation and Scheduled Disk Maintenance Procedure</span></span>](#Planned)  
  
-   [<span data-ttu-id="39745-116">오류 복구 절차</span><span class="sxs-lookup"><span data-stu-id="39745-116">Failure Recovery Procedure</span></span>](#Failure)  
  
-   [<span data-ttu-id="39745-117">Master 데이터베이스 이동</span><span class="sxs-lookup"><span data-stu-id="39745-117">Moving the master Database</span></span>](#master)  
  
-   [<span data-ttu-id="39745-118">리소스 데이터베이스 이동</span><span class="sxs-lookup"><span data-stu-id="39745-118">Moving the Resource Database</span></span>](#Resource)  
  
-   [<span data-ttu-id="39745-119">후속 작업: 모든 시스템 데이터베이스를 이동한 후</span><span class="sxs-lookup"><span data-stu-id="39745-119">Follow-up: After Moving All System Databases</span></span>](#Follow)  
  
-   [<span data-ttu-id="39745-120">예</span><span class="sxs-lookup"><span data-stu-id="39745-120">Examples</span></span>](#Examples)  
  
##  <a name="planned-relocation-and-scheduled-disk-maintenance-procedure"></a><a name="Planned"></a> <span data-ttu-id="39745-121">계획된 재배치 및 예약된 디스크 유지 관리 절차</span><span class="sxs-lookup"><span data-stu-id="39745-121">Planned Relocation and Scheduled Disk Maintenance Procedure</span></span>  
 <span data-ttu-id="39745-122">계획된 재배치 또는 예약된 유지 관리 작업의 일부로 시스템 데이터베이스 데이터나 로그 파일을 이동하려면 다음 단계를 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="39745-122">To move a system database data or log file as part of a planned relocation or scheduled maintenance operation, follow these steps.</span></span> <span data-ttu-id="39745-123">이 절차는 master 및 리소스 데이터베이스를 제외한 모든 시스템 데이터베이스에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="39745-123">This procedure applies to all system databases except the master and Resource databases.</span></span>  
  
1.  <span data-ttu-id="39745-124">이동할 각 파일에 대해 다음 문을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="39745-124">For each file to be moved, run the following statement.</span></span>  
  
    ```  
    ALTER DATABASE database_name MODIFY FILE ( NAME = logical_name , FILENAME = 'new_path\os_file_name' )  
    ```  
  
2.  <span data-ttu-id="39745-125">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스를 중지하거나 시스템을 종료하여 유지 관리를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="39745-125">Stop the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] or shut down the system to perform maintenance.</span></span> <span data-ttu-id="39745-126">자세한 내용은 [SQL Server 서비스 시작, 중지, 일시 중지, 재개 및 다시 시작](../../database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="39745-126">For more information, see [Start, Stop, Pause, Resume, Restart the Database Engine, SQL Server Agent, or SQL Server Browser Service](../../database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md).</span></span>  
  
3.  <span data-ttu-id="39745-127">파일을 새 위치로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="39745-127">Move the file or files to the new location.</span></span>  
  
4.  <span data-ttu-id="39745-128">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스나 서버를 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="39745-128">Restart the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] or the server.</span></span> <span data-ttu-id="39745-129">자세한 내용은 [SQL Server 서비스 시작, 중지, 일시 중지, 재개 및 다시 시작](../../database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="39745-129">For more information, see [Start, Stop, Pause, Resume, Restart the Database Engine, SQL Server Agent, or SQL Server Browser Service](../../database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md).</span></span>  
  
5.  <span data-ttu-id="39745-130">다음 쿼리를 실행하여 파일 변경 내용을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="39745-130">Verify the file change by running the following query.</span></span>  
  
    ```  
    SELECT name, physical_name AS CurrentLocation, state_desc  
    FROM sys.master_files  
    WHERE database_id = DB_ID(N'<database_name>');  
    ```  
  
 <span data-ttu-id="39745-131">msdb 데이터베이스가 이동되고 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에서 [데이터베이스 메일](../database-mail/database-mail.md)을 구성한 경우 다음 단계를 추가로 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="39745-131">If the msdb database is moved and the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is configured for [Database Mail](../database-mail/database-mail.md), complete these additional steps.</span></span>  
  
1.  <span data-ttu-id="39745-132">다음 쿼리를 실행하여 msdb 데이터베이스에 대해 [!INCLUDE[ssSB](../../../includes/sssb-md.md)]가 설정되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="39745-132">Verify that [!INCLUDE[ssSB](../../../includes/sssb-md.md)] is enabled for the msdb database by running the following query.</span></span>  
  
    ```  
    SELECT is_broker_enabled   
    FROM sys.databases  
    WHERE name = N'msdb';  
    ```  
  
     <span data-ttu-id="39745-133">[!INCLUDE[ssSB](../../../includes/sssb-md.md)]를 설정하는 방법은 [ALTER DATABASE&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="39745-133">For more information about enabling [!INCLUDE[ssSB](../../../includes/sssb-md.md)], see [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql).</span></span>  
  
2.  <span data-ttu-id="39745-134">테스트 메일을 보내 데이터베이스 메일이 작동하는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="39745-134">Verify that Database Mail is working by sending a test mail.</span></span>  
  
##  <a name="failure-recovery-procedure"></a><a name="Failure"></a> <span data-ttu-id="39745-135">오류 복구 절차</span><span class="sxs-lookup"><span data-stu-id="39745-135">Failure Recovery Procedure</span></span>  
 <span data-ttu-id="39745-136">하드웨어 오류로 인해 파일을 이동해야 하는 경우 다음 단계에 따라 파일을 새 위치에 재배치합니다.</span><span class="sxs-lookup"><span data-stu-id="39745-136">If a file must be moved because of a hardware failure, follow these steps to relocate the file to a new location.</span></span> <span data-ttu-id="39745-137">이 절차는 master 및 리소스 데이터베이스를 제외한 모든 시스템 데이터베이스에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="39745-137">This procedure applies to all system databases except the master and Resource databases.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="39745-138">데이터베이스가 주의 대상 모드에 있거나 복구할 수 없는 상태여서 시작할 수 없는 경우에는 sysadmin 고정 역할의 멤버만 파일을 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39745-138">If the database cannot be started, that is it is in suspect mode or in an unrecovered state, only members of the sysadmin fixed role can move the file.</span></span>  
  
1.  <span data-ttu-id="39745-139">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스가 시작된 경우 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="39745-139">Stop the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] if it is started.</span></span>  
  
2.  <span data-ttu-id="39745-140">명령 프롬프트에서 다음 명령 중 하나를 입력하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스를 마스터 전용 복구 모드로 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="39745-140">Start the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in master-only recovery mode by entering one of the following commands at the command prompt.</span></span> <span data-ttu-id="39745-141">이러한 명령에 지정된 매개 변수는 대/소문자를 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="39745-141">The parameters specified in these commands are case sensitive.</span></span> <span data-ttu-id="39745-142">표시된 대로 매개 변수를 지정하지 않으면 명령이 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="39745-142">The commands fail when the parameters are not specified as shown.</span></span>  
  
    -   <span data-ttu-id="39745-143">기본(MSSQLSERVER) 인스턴스의 경우 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="39745-143">For the default (MSSQLSERVER) instance, run the following command:</span></span>  
  
        ```  
        NET START MSSQLSERVER /f /T3608  
        ```  
  
    -   <span data-ttu-id="39745-144">명명된 인스턴스의 경우 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="39745-144">For a named instance, run the following command:</span></span>  
  
        ```  
        NET START MSSQL$instancename /f /T3608  
        ```  
  
     <span data-ttu-id="39745-145">자세한 내용은 [SQL Server 서비스 시작, 중지, 일시 중지, 재개 및 다시 시작](../../database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="39745-145">For more information, see [Start, Stop, Pause, Resume, Restart the Database Engine, SQL Server Agent, or SQL Server Browser Service](../../database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md).</span></span>  
  
3.  <span data-ttu-id="39745-146">이동할 각 파일에 대해 **sqlcmd** 명령 또는 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 를 사용하여 다음 문을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="39745-146">For each file to be moved, use **sqlcmd** commands or [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] to run the following statement.</span></span>  
  
    ```  
    ALTER DATABASE database_name MODIFY FILE( NAME = logical_name , FILENAME = 'new_path\os_file_name' )  
    ```  
  
     <span data-ttu-id="39745-147">**sqlcmd** 유틸리티 사용에 대한 자세한 내용은 [sqlcmd 유틸리티 사용](../scripting/sqlcmd-use-the-utility.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="39745-147">For more information about using the **sqlcmd** utility, see [Use the sqlcmd Utility](../scripting/sqlcmd-use-the-utility.md).</span></span>  
  
4.  <span data-ttu-id="39745-148">**sqlcmd** 유틸리티 또는 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]를 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="39745-148">Exit the **sqlcmd** utility or [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)].</span></span>  
  
5.  <span data-ttu-id="39745-149">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스를 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="39745-149">Stop the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="39745-150">예를 들어 `NET STOP MSSQLSERVER`를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="39745-150">For example, run `NET STOP MSSQLSERVER`.</span></span>  
  
6.  <span data-ttu-id="39745-151">파일을 새 위치로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="39745-151">Move the file or files to the new location.</span></span>  
  
7.  <span data-ttu-id="39745-152">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스를 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="39745-152">Restart the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="39745-153">예를 들어 `NET START MSSQLSERVER`를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="39745-153">For example, run `NET START MSSQLSERVER`.</span></span>  
  
8.  <span data-ttu-id="39745-154">다음 쿼리를 실행하여 파일 변경 내용을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="39745-154">Verify the file change by running the following query.</span></span>  
  
    ```  
    SELECT name, physical_name AS CurrentLocation, state_desc  
    FROM sys.master_files  
    WHERE database_id = DB_ID(N'<database_name>');  
    ```  
  
##  <a name="moving-the-master-database"></a><a name="master"></a> <span data-ttu-id="39745-155">master 데이터베이스 이동</span><span class="sxs-lookup"><span data-stu-id="39745-155">Moving the master Database</span></span>  
 <span data-ttu-id="39745-156">master 데이터베이스를 이동하려면 다음 단계를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="39745-156">To move the master database, follow these steps.</span></span>  
  
1.  <span data-ttu-id="39745-157">**시작** 메뉴에서 **모든 프로그램**, **Microsoft SQL Server**, **구성 도구**를 차례로 가리킨 다음 **SQL Server 구성 관리자**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="39745-157">From the **Start** menu, point to **All Programs**, point to **Microsoft SQL Server**, point to **Configuration Tools**, and then click **SQL Server Configuration Manager**.</span></span>  
  
2.  <span data-ttu-id="39745-158">**SQL Server 서비스** 노드에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스(예: **SQL Server(MSSQLSERVER)** )를 마우스 오른쪽 단추로 클릭한 다음 **속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="39745-158">In the **SQL Server Services** node, right-click the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (for example, **SQL Server (MSSQLSERVER)**) and choose **Properties**.</span></span>  
  
3.  <span data-ttu-id="39745-159">\*\*SQL Server( \*\*\*instance_name \***) 속성** 대화 상자에서 **시작 매개 변수** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="39745-159">In the **SQL Server (***instance_name***) Properties** dialog box, click the **Startup Parameters** tab.</span></span>  
  
4.  <span data-ttu-id="39745-160">**기존 매개 변수** 상자에서 –d 매개 변수를 선택하여 마스터 데이터 파일을 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="39745-160">In the **Existing parameters** box, select the -d parameter to move the master data file.</span></span> <span data-ttu-id="39745-161">**업데이트** 를 클릭하여 변경 내용을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="39745-161">Click **Update** to save the change.</span></span>  
  
     <span data-ttu-id="39745-162">**시작 매개 변수 지정** 상자에서 매개 변수를 master 데이터베이스의 새 경로로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="39745-162">In the **Specify a startup parameter** box, change the parameter to the new path of the master database.</span></span>  
  
5.  <span data-ttu-id="39745-163">**기존 매개 변수** 상자에서 –l 매개 변수를 선택하여 마스터 로그 파일을 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="39745-163">In the **Existing parameters** box, select the -l parameter to move the master log file.</span></span> <span data-ttu-id="39745-164">**업데이트** 를 클릭하여 변경 내용을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="39745-164">Click **Update** to save the change.</span></span>  
  
     <span data-ttu-id="39745-165">**시작 매개 변수 지정** 상자에서 매개 변수를 master 데이터베이스의 새 경로로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="39745-165">In the **Specify a startup parameter** box, change the parameter to the new path of the master database.</span></span>  
  
     <span data-ttu-id="39745-166">데이터 파일의 매개 변수 값은 `-d` 매개 변수 뒤에 와야 하고 로그 파일의 값은 `-l` 매개 변수 뒤에 와야 합니다.</span><span class="sxs-lookup"><span data-stu-id="39745-166">The parameter value for the data file must follow the `-d` parameter and the value for the log file must follow the `-l` parameter.</span></span> <span data-ttu-id="39745-167">다음 예에서는 마스터 데이터 파일의 기본 위치에 대한 매개 변수 값을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="39745-167">The following example shows the parameter values for the default location of the master data file.</span></span>  
  
     `-dC:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\DATA\master.mdf`  
  
     `-lC:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\DATA\mastlog.ldf`  
  
     <span data-ttu-id="39745-168">마스터 데이터 파일의 계획된 재배치가 `E:\SQLData`인 경우 매개 변수 값은 다음과 같이 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="39745-168">If the planned relocation for the master data file is `E:\SQLData`, the parameter values would be changed as follows:</span></span>  
  
     `-dE:\SQLData\master.mdf`  
  
     `-lE:\SQLData\mastlog.ldf`  
  
6.  <span data-ttu-id="39745-169">인스턴스 이름을 마우스 오른쪽 단추로 클릭하고 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 중지 **를 선택하여**인스턴스를 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="39745-169">Stop the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by right-clicking the instance name and choosing **Stop**.</span></span>  
  
7.  <span data-ttu-id="39745-170">master.mdf 및 mastlog.ldf 파일을 새 위치로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="39745-170">Move the master.mdf and mastlog.ldf files to the new location.</span></span>  
  
8.  <span data-ttu-id="39745-171">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스를 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="39745-171">Restart the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
9. <span data-ttu-id="39745-172">다음 쿼리를 실행하여 master 데이터베이스에 대한 파일 변경 내용을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="39745-172">Verify the file change for the master database by running the following query.</span></span>  
  
    ```  
    SELECT name, physical_name AS CurrentLocation, state_desc  
    FROM sys.master_files  
    WHERE database_id = DB_ID('master');  
    GO  
    ```  
  
##  <a name="moving-the-resource-database"></a><a name="Resource"></a> <span data-ttu-id="39745-173">리소스 데이터베이스 이동</span><span class="sxs-lookup"><span data-stu-id="39745-173">Moving the Resource Database</span></span>  
 <span data-ttu-id="39745-174">리소스 데이터베이스의 위치는 \<*drive*>:\Program Files\Microsoft SQL Server\MSSQL\<version>.\<*instance_name*>\MSSQL\Binn\\입니다.</span><span class="sxs-lookup"><span data-stu-id="39745-174">The location of the Resource database is \<*drive*>:\Program Files\Microsoft SQL Server\MSSQL\<version>.\<*instance_name*>\MSSQL\Binn\\.</span></span> <span data-ttu-id="39745-175">데이터베이스는 이동할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="39745-175">The database cannot be moved.</span></span>  
  
##  <a name="follow-up-after-moving-all-system-databases"></a><a name="Follow"></a> <span data-ttu-id="39745-176">후속 작업: 모든 시스템 데이터베이스를 이동한 후</span><span class="sxs-lookup"><span data-stu-id="39745-176">Follow-up: After Moving All System Databases</span></span>  
 <span data-ttu-id="39745-177">모든 시스템 데이터베이스를 새 드라이브 또는 볼륨으로 이동했거나 다른 드라이브 문자를 사용하는 다른 서버에 이동한 경우 다음과 같이 업데이트하세요.</span><span class="sxs-lookup"><span data-stu-id="39745-177">If you have moved all of the system databases to a new drive or volume or to another server with a different drive letter, make the following updates.</span></span>  
  
-   <span data-ttu-id="39745-178">SQL Server 에이전트 로그 경로를 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="39745-178">Change the SQL Server Agent log path.</span></span> <span data-ttu-id="39745-179">이 경로를 업데이트하지 않으면 SQL Server 에이전트가 시작되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="39745-179">If you do not update this path, SQL Server Agent will fail to start.</span></span>  
  
-   <span data-ttu-id="39745-180">데이터베이스 기본 위치를 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="39745-180">Change the database default location.</span></span> <span data-ttu-id="39745-181">기본 위치로 지정한 드라이브 문자 및 경로가 존재하지 않을 경우 새 데이터베이스 만들기가 실패할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39745-181">Creating a new database may fail if the drive letter and path specified as the default location do not exist.</span></span>  
  
#### <a name="change-the-sql-server-agent-log-path"></a><span data-ttu-id="39745-182">SQL Server 에이전트 로그 경로를 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="39745-182">Change the SQL Server Agent Log Path</span></span>  
  
1.  <span data-ttu-id="39745-183">SQL Server Management Studio의 개체 탐색기에서 **SQL Server 에이전트**를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="39745-183">From SQL Server Management Studio, in Object Explorer, expand **SQL Server Agent**.</span></span>  
  
2.  <span data-ttu-id="39745-184">**오류 로그** 를 마우스 오른쪽 단추로 클릭한 다음 **구성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="39745-184">Right-click **Error Logs** and click **Configure**.</span></span>  
  
3.  <span data-ttu-id="39745-185">**SQL Server 에이전트 오류 로그 구성** 대화 상자에서 SQLAGENT.OUT 파일의 새 위치를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="39745-185">In the **Configure SQL Server Agent Error Logs** dialog box, specify the new location of the SQLAGENT.OUT file.</span></span> <span data-ttu-id="39745-186">기본 위치는 C:\Program Files\Microsoft SQL Server\MSSQL12. <instance_name> \MSSQL\Log \\ 입니다.</span><span class="sxs-lookup"><span data-stu-id="39745-186">The default location is C:\Program Files\Microsoft SQL Server\MSSQL12.<instance_name>\MSSQL\Log\\.</span></span>  
  
#### <a name="change-the-database-default-location"></a><span data-ttu-id="39745-187">데이터베이스 기본 위치 변경</span><span class="sxs-lookup"><span data-stu-id="39745-187">Change the database default location</span></span>  
  
1.  <span data-ttu-id="39745-188">SQL Server Management Studio의 개체 탐색기에서 SQL Server 서비스를 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="39745-188">From SQL Server Management Studio, in Object Explorer, right-click the SQL Server server and click **Properties**.</span></span>  
  
2.  <span data-ttu-id="39745-189">**서버 속성** 대화 상자에서 **데이터베이스 설정**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="39745-189">In the **Server Properties** dialog box, select **Database Settings**.</span></span>  
  
3.  <span data-ttu-id="39745-190">**데이터베이스 기본 위치**에서 데이터 및 로그 파일의 새 위치를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="39745-190">Under **Database Default Locations**, browse to the new location for both the data and log files.</span></span>  
  
4.  <span data-ttu-id="39745-191">변경을 완료하려면 SQL Server 서비스를 중지한 후 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="39745-191">Stop and start the SQL Server service to complete the change.</span></span>  
  
##  <a name="examples"></a><a name="Examples"></a> <span data-ttu-id="39745-192">예</span><span class="sxs-lookup"><span data-stu-id="39745-192">Examples</span></span>  
  
### <a name="a-moving-the-tempdb-database"></a><span data-ttu-id="39745-193">A.</span><span class="sxs-lookup"><span data-stu-id="39745-193">A.</span></span> <span data-ttu-id="39745-194">tempdb 데이터베이스 이동</span><span class="sxs-lookup"><span data-stu-id="39745-194">Moving the tempdb database</span></span>  
 <span data-ttu-id="39745-195">다음 예에서는 계획된 재배치의 일부로 `tempdb` 데이터와 로그 파일을 새 위치로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="39745-195">The following example moves the `tempdb` data and log files to a new location as part of a planned relocation.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="39745-196">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스를 시작할 때마다 tempdb가 다시 생성되므로 데이터와 로그 파일을 물리적으로 이동할 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="39745-196">Because tempdb is re-created each time the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is started, you do not have to physically move the data and log files.</span></span> <span data-ttu-id="39745-197">3단계에서 서비스를 다시 시작할 때 새 위치에 파일이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="39745-197">The files are created in the new location when the service is restarted in step 3.</span></span> <span data-ttu-id="39745-198">서비스를 다시 시작할 때까지는 tempdb에서 계속 기존 위치의 데이터와 로그 파일을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="39745-198">Until the service is restarted, tempdb continues to use the data and log files in existing location.</span></span>  
  
1.  <span data-ttu-id="39745-199">`tempdb` 데이터베이스의 논리적 파일 이름 및 디스크에서의 현재 위치를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="39745-199">Determine the logical file names of the `tempdb` database and their current location on the disk.</span></span>  
  
    ```  
    SELECT name, physical_name AS CurrentLocation  
    FROM sys.master_files  
    WHERE database_id = DB_ID(N'tempdb');  
    GO  
    ```  
  
2.  <span data-ttu-id="39745-200">`ALTER DATABASE`를 사용하여 각 파일의 위치를 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="39745-200">Change the location of each file by using `ALTER DATABASE`.</span></span>  
  
    ```  
    USE master;  
    GO  
    ALTER DATABASE tempdb   
    MODIFY FILE (NAME = tempdev, FILENAME = 'E:\SQLData\tempdb.mdf');  
    GO  
    ALTER DATABASE tempdb   
    MODIFY FILE (NAME = templog, FILENAME = 'F:\SQLLog\templog.ldf');  
    GO  
    ```  
  
3.  <span data-ttu-id="39745-201">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스를 중지한 후 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="39745-201">Stop and restart the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
4.  <span data-ttu-id="39745-202">파일 변경 내용을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="39745-202">Verify the file change.</span></span>  
  
    ```  
    SELECT name, physical_name AS CurrentLocation, state_desc  
    FROM sys.master_files  
    WHERE database_id = DB_ID(N'tempdb');  
    ```  
  
5.  <span data-ttu-id="39745-203">원래 위치에서 `tempdb.mdf` 및 `templog.ldf` 파일을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="39745-203">Delete the `tempdb.mdf` and `templog.ldf` files from the original location.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39745-204">참고 항목</span><span class="sxs-lookup"><span data-stu-id="39745-204">See Also</span></span>  
 <span data-ttu-id="39745-205">[Resource 데이터베이스](resource-database.md) </span><span class="sxs-lookup"><span data-stu-id="39745-205">[Resource Database](resource-database.md) </span></span>  
 <span data-ttu-id="39745-206">[tempdb 데이터베이스](tempdb-database.md) </span><span class="sxs-lookup"><span data-stu-id="39745-206">[tempdb Database](tempdb-database.md) </span></span>  
 <span data-ttu-id="39745-207">[master 데이터베이스](master-database.md) </span><span class="sxs-lookup"><span data-stu-id="39745-207">[master Database](master-database.md) </span></span>  
 <span data-ttu-id="39745-208">[msdb 데이터베이스](msdb-database.md) </span><span class="sxs-lookup"><span data-stu-id="39745-208">[msdb Database](msdb-database.md) </span></span>  
 <span data-ttu-id="39745-209">[model 데이터베이스](model-database.md) </span><span class="sxs-lookup"><span data-stu-id="39745-209">[model Database](model-database.md) </span></span>  
 <span data-ttu-id="39745-210">[사용자 데이터베이스 이동](move-user-databases.md) </span><span class="sxs-lookup"><span data-stu-id="39745-210">[Move User Databases](move-user-databases.md) </span></span>  
 <span data-ttu-id="39745-211">[데이터베이스 파일 이동](move-database-files.md) </span><span class="sxs-lookup"><span data-stu-id="39745-211">[Move Database Files](move-database-files.md) </span></span>  
 <span data-ttu-id="39745-212">[데이터베이스 엔진, SQL Server 에이전트 또는 SQL Server Browser 서비스 시작, 중지, 일시 중지, 재개 및 다시 시작](../../database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md) </span><span class="sxs-lookup"><span data-stu-id="39745-212">[Start, Stop, Pause, Resume, Restart the Database Engine, SQL Server Agent, or SQL Server Browser Service](../../database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md) </span></span>  
 <span data-ttu-id="39745-213">[ALTER DATABASE &#40;Transact-SQL &#41;](/sql/t-sql/statements/alter-database-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="39745-213">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span></span>  
 [<span data-ttu-id="39745-214">시스템 데이터베이스 다시 작성</span><span class="sxs-lookup"><span data-stu-id="39745-214">Rebuild System Databases</span></span>](system-databases.md)  
  
  
