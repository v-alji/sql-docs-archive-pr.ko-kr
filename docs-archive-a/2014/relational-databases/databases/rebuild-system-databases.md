---
title: 시스템 데이터베이스 다시 빌드 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- master database [SQL Server], rebuilding
- REBUILDDATABASE parameter
- rebuilding databases, master
- system databases [SQL Server], rebuilding
ms.assetid: af457ecd-523e-4809-9652-bdf2e81bd876
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5f695589fa0fc1b86d4433d36afa1bc6357aabd6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650093"
---
# <a name="rebuild-system-databases"></a><span data-ttu-id="85407-102">시스템 데이터베이스 다시 작성</span><span class="sxs-lookup"><span data-stu-id="85407-102">Rebuild System Databases</span></span>
  <span data-ttu-id="85407-103">[master](master-database.md), [model](model-database.md), [msdb](msdb-database.md)또는 [resource](resource-database.md) 시스템 데이터베이스의 손상 문제를 수정하거나 기본 서버 수준 데이터 정렬을 변경하려면 시스템 데이터베이스를 다시 작성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="85407-103">System databases must be rebuilt to fix corruption problems in the [master](master-database.md), [model](model-database.md), [msdb](msdb-database.md), or [resource](resource-database.md) system databases or to modify the default server-level collation.</span></span> <span data-ttu-id="85407-104">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]에서 시스템 데이터베이스를 다시 작성하는 단계별 지침을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="85407-104">This topic provides step-by-step instructions to rebuild system databases in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
 <span data-ttu-id="85407-105">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="85407-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="85407-106">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="85407-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="85407-107">제한 사항</span><span class="sxs-lookup"><span data-stu-id="85407-107">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="85407-108">필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="85407-108">Prerequisites</span></span>](#Prerequisites)  
  
-   <span data-ttu-id="85407-109">**절차:**</span><span class="sxs-lookup"><span data-stu-id="85407-109">**Procedures:**</span></span>  
  
     [<span data-ttu-id="85407-110">시스템 데이터베이스 다시 작성</span><span class="sxs-lookup"><span data-stu-id="85407-110">Rebuild System Databases</span></span>](#RebuildProcedure)  
  
     [<span data-ttu-id="85407-111">리소스 데이터베이스 다시 작성</span><span class="sxs-lookup"><span data-stu-id="85407-111">Rebuild the resource Database</span></span>](#Resource)  
  
     [<span data-ttu-id="85407-112">새 msdb 데이터베이스 만들기</span><span class="sxs-lookup"><span data-stu-id="85407-112">Create a New msdb Database</span></span>](#CreateMSDB)  
  
-   <span data-ttu-id="85407-113">**후속 작업:**</span><span class="sxs-lookup"><span data-stu-id="85407-113">**Follow Up:**</span></span>  
  
     [<span data-ttu-id="85407-114">다시 작성 오류 문제 해결</span><span class="sxs-lookup"><span data-stu-id="85407-114">Troubleshoot Rebuild Errors</span></span>](#Troubleshoot)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="85407-115">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="85407-115">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="85407-116">제한 사항</span><span class="sxs-lookup"><span data-stu-id="85407-116">Limitations and Restrictions</span></span>  
 <span data-ttu-id="85407-117">master, model, msdb 및 tempdb 시스템 데이터베이스를 다시 작성하면 해당 데이터베이스가 삭제된 후 원래 위치에 다시 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="85407-117">When the master, model, msdb, and tempdb system databases are rebuilt, the databases are dropped and re-created in their original location.</span></span> <span data-ttu-id="85407-118">REBUILD 문에 새로운 데이터 정렬이 지정되면 해당 데이터 정렬 설정을 사용하여 시스템 데이터베이스가 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="85407-118">If a new collation is specified in the rebuild statement, the system databases are created using that collation setting.</span></span> <span data-ttu-id="85407-119">이러한 데이터베이스에 사용자들이 변경한 내용은 손실됩니다.</span><span class="sxs-lookup"><span data-stu-id="85407-119">Any user modifications to these databases are lost.</span></span> <span data-ttu-id="85407-120">예를 들어, master 데이터베이스에 사용자 정의 개체가 있거나, msdb에 예약된 작업이 있거나 model 데이터베이스에서 기본 데이터베이스 설정을 변경했을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="85407-120">For example, you may have user-defined objects in the master database, scheduled jobs in msdb, or changes to the default database settings in the model database.</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="85407-121">필수 조건</span><span class="sxs-lookup"><span data-stu-id="85407-121">Prerequisites</span></span>  
 <span data-ttu-id="85407-122">시스템 데이터베이스를 다시 작성하기 전에 다음 태스크를 수행하면 시스템 데이터베이스를 현재 설정으로 복원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="85407-122">Perform the following tasks before you rebuild the system databases to ensure that you can restore the system databases to their current settings.</span></span>  
  
1.  <span data-ttu-id="85407-123">서버 차원의 모든 구성 값을 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="85407-123">Record all server-wide configuration values.</span></span>  
  
    ```  
    SELECT * FROM sys.configurations;  
    ```  
  
2.  <span data-ttu-id="85407-124">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스와 현재 데이터 정렬에 적용된 모든 서비스 팩과 핫픽스를 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="85407-124">Record all service packs and hotfixes applied to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and the current collation.</span></span> <span data-ttu-id="85407-125">시스템 데이터베이스를 다시 작성한 후 이러한 업데이트를 다시 적용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="85407-125">You must reapply these updates after rebuilding the system databases.</span></span>  
  
    ```  
    SELECT  
    SERVERPROPERTY('ProductVersion ') AS ProductVersion,  
    SERVERPROPERTY('ProductLevel') AS ProductLevel,  
    SERVERPROPERTY('ResourceVersion') AS ResourceVersion,  
    SERVERPROPERTY('ResourceLastUpdateDateTime') AS ResourceLastUpdateDateTime,  
    SERVERPROPERTY('Collation') AS Collation;  
    ```  
  
3.  <span data-ttu-id="85407-126">시스템 데이터베이스의 모든 데이터와 로그 파일의 현재 위치를 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="85407-126">Record the current location of all data and log files for the system databases.</span></span> <span data-ttu-id="85407-127">시스템 데이터베이스를 다시 작성하면 모든 시스템 데이터베이스가 원래 위치에 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="85407-127">Rebuilding the system databases installs all system databases to their original location.</span></span> <span data-ttu-id="85407-128">시스템 데이터베이스 데이터나 로그 파일을 다른 위치로 이동한 경우 해당 파일을 다시 이동해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="85407-128">If you have moved system database data or log files to a different location, you must move the files again.</span></span>  
  
    ```  
    SELECT name, physical_name AS current_file_location  
    FROM sys.master_files  
    WHERE database_id IN (DB_ID('master'), DB_ID('model'), DB_ID('msdb'), DB_ID('tempdb'));  
    ```  
  
4.  <span data-ttu-id="85407-129">master, model, msdb 데이터베이스의 현재 백업을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="85407-129">Locate the current backup of the master, model, and msdb databases.</span></span>  
  
5.  <span data-ttu-id="85407-130">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스가 복제 배포자로 구성된 경우 배포 데이터베이스의 현재 백업을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="85407-130">If the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is configured as a replication Distributor, locate the current backup of the distribution database.</span></span>  
  
6.  <span data-ttu-id="85407-131">시스템 데이터베이스를 다시 작성할 수 있는 권한이 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="85407-131">Ensure you have appropriate permissions to rebuild the system databases.</span></span> <span data-ttu-id="85407-132">이 작업을 수행하려면 `sysadmin` 고정 서버 역할의 멤버여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="85407-132">To perform this operation, you must be a member of the `sysadmin` fixed server role.</span></span> <span data-ttu-id="85407-133">자세한 내용은 [서버 수준 역할](../security/authentication-access/server-level-roles.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="85407-133">For more information, see [Server-Level Roles](../security/authentication-access/server-level-roles.md).</span></span>  
  
7.  <span data-ttu-id="85407-134">master, model, msdb 데이터와 로그 템플릿 파일의 복사본이 로컬 서버에 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="85407-134">Verify that copies of the master, model, msdb data and log template files exist on the local server.</span></span> <span data-ttu-id="85407-135">템플릿 파일의 기본 위치는 C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Binn\Templates입니다.</span><span class="sxs-lookup"><span data-stu-id="85407-135">The default location for the template files is C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Binn\Templates.</span></span> <span data-ttu-id="85407-136">이러한 파일은 다시 작성 프로세스 중에 사용되므로 성공적으로 설치를 수행하려면 반드시 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="85407-136">These files are used during the rebuild process and must be present for Setup to succeed.</span></span> <span data-ttu-id="85407-137">이러한 파일이 없으면 설치 시 복구 기능을 실행하거나 설치 미디어에서 해당 파일을 직접 복사하세요.</span><span class="sxs-lookup"><span data-stu-id="85407-137">If they are missing, run the Repair feature of Setup, or manually copy the files from your installation media.</span></span> <span data-ttu-id="85407-138">설치 미디어에서 이러한 파일을 찾으려면 해당 플랫폼 디렉터리(x86 또는 x64)로 이동한 후 setup\sql_engine_core_inst_msi\Pfiles\SqlServr\MSSQL.X\MSSQL\Binn\Templates로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="85407-138">To locate the files on the installation media, navigate to the appropriate platform directory (x86 or x64) and then navigate to setup\sql_engine_core_inst_msi\Pfiles\SqlServr\MSSQL.X\MSSQL\Binn\Templates.</span></span>  
  
##  <a name="rebuild-system-databases"></a><a name="RebuildProcedure"></a> <span data-ttu-id="85407-139">시스템 데이터베이스 다시 작성</span><span class="sxs-lookup"><span data-stu-id="85407-139">Rebuild System Databases</span></span>  
 <span data-ttu-id="85407-140">다음은 master, model, msdb 및 tempdb 시스템 데이터베이스를 다시 작성하는 절차입니다.</span><span class="sxs-lookup"><span data-stu-id="85407-140">The following procedure rebuilds the master, model, msdb, and tempdb system databases.</span></span> <span data-ttu-id="85407-141">다시 작성할 시스템 데이터베이스를 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="85407-141">You cannot specify the system databases to be rebuilt.</span></span> <span data-ttu-id="85407-142">클러스터형 인스턴스의 경우 액티브 노드에서 이 절차를 수행해야 하고, 이 절차를 수행하기 전에 해당 클러스터 애플리케이션 그룹의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 리소스를 오프라인으로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="85407-142">For clustered instances, this procedure must be performed on the active node and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] resource in the corresponding cluster application group must be taken offline before performing the procedure.</span></span>  
  
 <span data-ttu-id="85407-143">리소스 데이터베이스는 이 절차를 통해 다시 작성할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="85407-143">This procedure does not rebuild the resource database.</span></span> <span data-ttu-id="85407-144">이 항목 뒷부분에 나오는 "리소스 데이터베이스 다시 작성 절차" 섹션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="85407-144">See the section, "Rebuild the resource Database Procedure" later in this topic.</span></span>  
  
#### <a name="to-rebuild-system-databases-for-an-instance-of-sql-server"></a><span data-ttu-id="85407-145">SQL Server 2008 인스턴스의 시스템 데이터베이스를 다시 작성하려면</span><span class="sxs-lookup"><span data-stu-id="85407-145">To rebuild system databases for an instance of SQL Server:</span></span>  
  
1.  <span data-ttu-id="85407-146">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 설치 미디어를 디스크 드라이브에 넣거나, 명령 프롬프트에서 로컬 서버의 setup.exe 파일이 있는 디렉터리로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="85407-146">Insert the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] installation media into the disk drive, or, from a command prompt, change directories to the location of the setup.exe file on the local server.</span></span> <span data-ttu-id="85407-147">서버의 기본 위치는 C:\Program Files\Microsoft SQL Server\120\Setup Bootstrap\Release입니다.</span><span class="sxs-lookup"><span data-stu-id="85407-147">The default location on the server is C:\Program Files\Microsoft SQL Server\120\Setup Bootstrap\Release.</span></span>  
  
2.  <span data-ttu-id="85407-148">명령 프롬프트 창에서 다음 명령을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="85407-148">From a command prompt window, enter the following command.</span></span> <span data-ttu-id="85407-149">대괄호([])는 옵션 매개 변수를 나타내는 데 사용되며,</span><span class="sxs-lookup"><span data-stu-id="85407-149">Square brackets are used to indicate optional parameters.</span></span> <span data-ttu-id="85407-150">입력하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="85407-150">Do not enter the brackets.</span></span> <span data-ttu-id="85407-151">Windows 운영 체제에서 UAC(사용자 계정 컨트롤)를 사용할 경우 설치를 실행하려면 승격된 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="85407-151">When using a Windows operating system that has User Account Control (UAC) enabled, running Setup requires elevated privileges.</span></span> <span data-ttu-id="85407-152">명령 프롬프트에서 관리자 권한으로 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="85407-152">The command prompt must be run as Administrator.</span></span>  
  
     `Setup /QUIET /ACTION=REBUILDDATABASE /INSTANCENAME=InstanceName /SQLSYSADMINACCOUNTS=accounts [ /SAPWD= StrongPassword ] [ /SQLCOLLATION=CollationName]`  
  
    |<span data-ttu-id="85407-153">매개 변수 이름</span><span class="sxs-lookup"><span data-stu-id="85407-153">Parameter name</span></span>|<span data-ttu-id="85407-154">Description</span><span class="sxs-lookup"><span data-stu-id="85407-154">Description</span></span>|  
    |--------------------|-----------------|  
    |<span data-ttu-id="85407-155">/QUIET 또는 /Q</span><span class="sxs-lookup"><span data-stu-id="85407-155">/QUIET or /Q</span></span>|<span data-ttu-id="85407-156">설치 프로그램이 사용자 인터페이스 없이 실행되도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="85407-156">Specifies that Setup run without any user interface.</span></span>|  
    |<span data-ttu-id="85407-157">/ACTION=REBUILDDATABASE</span><span class="sxs-lookup"><span data-stu-id="85407-157">/ACTION=REBUILDDATABASE</span></span>|<span data-ttu-id="85407-158">설치 시 시스템 데이터베이스를 다시 작성하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="85407-158">Specifies that Setup re-create the system databases.</span></span>|  
    |<span data-ttu-id="85407-159">/INSTANCENAME=*InstanceName*</span><span class="sxs-lookup"><span data-stu-id="85407-159">/INSTANCENAME=*InstanceName*</span></span>|<span data-ttu-id="85407-160">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="85407-160">Is the name of the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="85407-161">기본 인스턴스의 경우 MSSQLSERVER를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="85407-161">For the default instance, enter MSSQLSERVER.</span></span>|  
    |<span data-ttu-id="85407-162">/SQLSYSADMINACCOUNTS=*accounts*</span><span class="sxs-lookup"><span data-stu-id="85407-162">/SQLSYSADMINACCOUNTS=*accounts*</span></span>|<span data-ttu-id="85407-163">`sysadmin` 고정 서버 역할에 추가할 Windows 그룹이나 개별 계정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="85407-163">Specifies the Windows groups or individual accounts to add to the `sysadmin` fixed server role.</span></span> <span data-ttu-id="85407-164">둘 이상의 계정을 지정할 경우 각 계정 이름을 공백으로 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="85407-164">When specifying more than one account, separate the accounts with a blank space.</span></span> <span data-ttu-id="85407-165">예를 들면 **BUILTIN\Administrators MyDomain\MyUser**와 같이 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="85407-165">For example, enter **BUILTIN\Administrators MyDomain\MyUser**.</span></span> <span data-ttu-id="85407-166">계정 이름에 공백이 포함되어 있는 계정을 지정할 때는 계정을 큰따옴표로 묶습니다.</span><span class="sxs-lookup"><span data-stu-id="85407-166">When you are specifying an account that contains a blank space within the account name, enclose the account in double quotation marks.</span></span> <span data-ttu-id="85407-167">예를 들어 다음과 같이 입력합니다. `NT AUTHORITY\SYSTEM`</span><span class="sxs-lookup"><span data-stu-id="85407-167">For example, enter `NT AUTHORITY\SYSTEM`.</span></span>|  
    |<span data-ttu-id="85407-168">[ /SAPWD=*StrongPassword* ]</span><span class="sxs-lookup"><span data-stu-id="85407-168">[ /SAPWD=*StrongPassword* ]</span></span>|<span data-ttu-id="85407-169">계정에 대 한 암호를 지정 합니다 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `sa` .</span><span class="sxs-lookup"><span data-stu-id="85407-169">Specifies the password for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `sa` account.</span></span> <span data-ttu-id="85407-170">해당 인스턴스에서 혼합 인증([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 및 Windows 인증) 모드를 사용할 경우 이 매개 변수가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="85407-170">This parameter is required if the instance uses Mixed Authentication ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and Windows Authentication) mode.</span></span><br /><br /> <span data-ttu-id="85407-171">\*\* \* \* 보안 \* 정보 \* \*\* `sa` 계정은 잘 알려진 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 계정 이므로 악의적인 사용자의 대상이 되는 경우가 많습니다.</span><span class="sxs-lookup"><span data-stu-id="85407-171">**\*\* Security Note \*\*** The `sa` account is a well-known [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account and it is often targeted by malicious users.</span></span> <span data-ttu-id="85407-172">`sa` 로그인에 대해 강력한 암호를 사용하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="85407-172">It is very important that you use a strong password for the `sa` login.</span></span><br /><br /> <span data-ttu-id="85407-173">Windows 인증 모드에 이 매개 변수를 지정하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="85407-173">Do not specify this parameter for Windows Authentication mode.</span></span>|  
    |<span data-ttu-id="85407-174">[ /SQLCOLLATION=*CollationName* ]</span><span class="sxs-lookup"><span data-stu-id="85407-174">[ /SQLCOLLATION=*CollationName* ]</span></span>|<span data-ttu-id="85407-175">서버 수준 데이터 정렬을 새로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="85407-175">Specifies a new server-level collation.</span></span> <span data-ttu-id="85407-176">이 매개 변수는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="85407-176">This parameter is optional.</span></span> <span data-ttu-id="85407-177">지정하지 않으면 서버의 현재 데이터 정렬이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="85407-177">When not specified, the current collation of the server is used.</span></span><br /><br /> <span data-ttu-id="85407-178">**\*\* 중요 \*\*** 서버 수준 데이터 정렬을 변경해도 기존 사용자 데이터베이스의 데이터 정렬은 변경되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="85407-178">**\*\* Important \*\*** Changing the server-level collation does not change the collation of existing user databases.</span></span> <span data-ttu-id="85407-179">새로 만드는 모든 사용자 데이터베이스는 기본적으로 새로운 데이터 정렬을 사용하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="85407-179">All newly created user databases will use the new collation by default.</span></span><br /><br /> <span data-ttu-id="85407-180">자세한 내용은 [서버 데이터 정렬 설정 또는 변경](../collations/set-or-change-the-server-collation.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="85407-180">For more information, see [Set or Change the Server Collation](../collations/set-or-change-the-server-collation.md).</span></span>|  
  
3.  <span data-ttu-id="85407-181">시스템 데이터베이스를 다시 작성하는 작업이 완료되면 아무런 메시지 없이 명령 프롬프트로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="85407-181">When Setup has completed rebuilding the system databases, it returns to the command prompt with no messages.</span></span> <span data-ttu-id="85407-182">Summary.txt 로그 파일을 검토하여 프로세스가 성공적으로 완료되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="85407-182">Examine the Summary.txt log file to verify that the process completed successfully.</span></span> <span data-ttu-id="85407-183">이 파일은 C:\Program Files\Microsoft SQL Server\120\Setup Bootstrap\Logs에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="85407-183">This file is located at C:\Program Files\Microsoft SQL Server\120\Setup Bootstrap\Logs.</span></span>  
  
## <a name="post-rebuild-tasks"></a><span data-ttu-id="85407-184">다시 작성 후 수행할 태스크</span><span class="sxs-lookup"><span data-stu-id="85407-184">Post-Rebuild Tasks</span></span>  
 <span data-ttu-id="85407-185">데이터베이스를 다시 작성한 후에는 다음과 같은 추가 태스크를 수행해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="85407-185">After rebuilding the database you may need to perform the following additional tasks:</span></span>  
  
-   <span data-ttu-id="85407-186">master, model 및 msdb 데이터베이스의 최근 전체 백업을 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="85407-186">Restore your most recent full backups of the master, model, and msdb databases.</span></span> <span data-ttu-id="85407-187">자세한 내용은 [시스템 데이터베이스 백업 및 복원&#40;SQL Server&#41;](../backup-restore/back-up-and-restore-of-system-databases-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="85407-187">For more information, see [Back Up and Restore of System Databases &#40;SQL Server&#41;](../backup-restore/back-up-and-restore-of-system-databases-sql-server.md).</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="85407-188">서버 데이터 정렬을 변경했을 경우 시스템 데이터베이스를 복원하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="85407-188">If you have changed the server collation, do not restore the system databases.</span></span> <span data-ttu-id="85407-189">시스템 데이터베이스를 복원하면 새로운 데이터 정렬이 이전 데이터 정렬 설정으로 바뀝니다.</span><span class="sxs-lookup"><span data-stu-id="85407-189">Doing so will replace the new collation with the previous collation setting.</span></span>  
  
     <span data-ttu-id="85407-190">백업을 사용할 수 없거나 복원된 백업이 최신 백업이 아닌 경우 누락된 항목을 다시 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="85407-190">If a backup is not available or if the restored backup is not current, re-create any missing entries.</span></span> <span data-ttu-id="85407-191">예를 들어 사용자 데이터베이스, 백업 디바이스, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그인, 끝점 등에 대한 모든 누락 항목을 다시 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="85407-191">For example, re-create all missing entries for your user databases, backup devices, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] logins, end points, and so on.</span></span> <span data-ttu-id="85407-192">항목을 다시 만드는 가장 좋은 방법은 해당 항목을 만들었던 원래 스크립트를 실행하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="85407-192">The best way to re-create entries is to run the original scripts that created them.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="85407-193">스크립트에 보안을 설정해 무단으로 내용을 변경할 수 없도록 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="85407-193">We recommend that you secure your scripts to prevent their being altered by unauthorized by individuals.</span></span>  
  
-   <span data-ttu-id="85407-194">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스가 복제 배포자로 구성된 경우 배포 데이터베이스를 복원해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="85407-194">If the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is configured as a replication Distributor, you must restore the distribution database.</span></span> <span data-ttu-id="85407-195">자세한 내용은 [복제된 데이터베이스 백업 및 복원](../replication/administration/back-up-and-restore-replicated-databases.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="85407-195">For more information, see [Back Up and Restore Replicated Databases](../replication/administration/back-up-and-restore-replicated-databases.md).</span></span>  
  
-   <span data-ttu-id="85407-196">시스템 데이터베이스를 앞에서 기록해 둔 위치로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="85407-196">Move the system databases to the locations you recorded previously.</span></span> <span data-ttu-id="85407-197">자세한 내용은 [시스템 데이터베이스 이동](system-databases.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="85407-197">For more information, see [Move System Databases](system-databases.md).</span></span>  
  
-   <span data-ttu-id="85407-198">서버 차원의 구성 값이 앞에서 기록해 둔 값과 일치하는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="85407-198">Verify the server-wide configuration values match the values you recorded previously.</span></span>  
  
##  <a name="rebuild-the-resource-database"></a><a name="Resource"></a> <span data-ttu-id="85407-199">리소스 데이터베이스 다시 작성</span><span class="sxs-lookup"><span data-stu-id="85407-199">Rebuild the resource Database</span></span>  
 <span data-ttu-id="85407-200">다음은 리소스 시스템 데이터베이스를 다시 작성하는 절차입니다.</span><span class="sxs-lookup"><span data-stu-id="85407-200">The following procedure rebuilds the resource system database.</span></span> <span data-ttu-id="85407-201">리소스 데이터베이스를 다시 작성하면 모든 서비스 팩과 핫픽스 업데이트가 손실되므로 다시 적용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="85407-201">When you rebuild the resource database, all service packs and hot fixes are lost, and therefore must be reapplied.</span></span>  
  
#### <a name="to-rebuild-the-resource-system-database"></a><span data-ttu-id="85407-202">리소스 시스템 데이터베이스를 다시 작성하려면</span><span class="sxs-lookup"><span data-stu-id="85407-202">To rebuild the resource system database:</span></span>  
  
1.  <span data-ttu-id="85407-203">배포 미디어에서 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 설치 프로그램(setup.exe)을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="85407-203">Launch the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Setup program (setup.exe) from the distribution media.</span></span>  
  
2.  <span data-ttu-id="85407-204">왼쪽의 탐색 영역에서 **유지 관리**를 클릭한 다음 **복구**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="85407-204">In the left navigation area, click **Maintenance**, and then click **Repair**.</span></span>  
  
3.  <span data-ttu-id="85407-205">시스템에 사전 요구 사항가 설치되어 있고 컴퓨터가 설치 유효성 검사 규칙을 통과하는지 확인하기 위해 설치 지원 규칙 및 파일 루틴이 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="85407-205">Setup support rule and file routines run to ensure that your system has prerequisites installed and that the computer passes Setup validation rules.</span></span> <span data-ttu-id="85407-206">계속하려면 **확인** 또는 **설치** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="85407-206">Click **OK** or **Install** to continue.</span></span>  
  
4.  <span data-ttu-id="85407-207">인스턴스 선택 페이지에서 복구할 인스턴스를 선택한 후 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="85407-207">On the Select Instance page, select the instance to repair, and then click **Next**.</span></span>  
  
5.  <span data-ttu-id="85407-208">작업이 유효한지 검사하는 복구 규칙이 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="85407-208">The repair rules will run to validate the operation.</span></span> <span data-ttu-id="85407-209">계속하려면 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="85407-209">To continue, click **Next**.</span></span>  
  
6.  <span data-ttu-id="85407-210">**복구 준비** 페이지에서 **복구**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="85407-210">From the **Ready to Repair** page, click **Repair**.</span></span> <span data-ttu-id="85407-211">완료 페이지에서 작업이 완료되었음을 알려 줍니다.</span><span class="sxs-lookup"><span data-stu-id="85407-211">The Complete page indicates that the operation is finished.</span></span>  
  
##  <a name="create-a-new-msdb-database"></a><a name="CreateMSDB"></a> <span data-ttu-id="85407-212">새 msdb 데이터베이스 만들기</span><span class="sxs-lookup"><span data-stu-id="85407-212">Create a New msdb Database</span></span>  
 <span data-ttu-id="85407-213">데이터베이스가 손상 된 경우 데이터베이스 백업이 없는 경우에는 인스턴스를 `msdb` `msdb` `msdb` 사용 하 여 **instmsdb** 새를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="85407-213">If the `msdb` database is damaged and you do not have a backup of the `msdb` database, you can create a new `msdb` by using the **instmsdb** script.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="85407-214">사용 된 `msdb` **msdb** 스크립트를 사용 하 여 데이터베이스를 다시 작성 하면 `msdb` 작업, 경고, 운영자, 유지 관리 계획, 백업 기록, 정책 기반 관리 설정, 데이터베이스 메일, 성능 데이터 웨어하우스 등과 같은에 저장 된 모든 정보가 제거 됩니다.</span><span class="sxs-lookup"><span data-stu-id="85407-214">Rebuilding the `msdb` database using the **instmsdb** script will eliminate all the information stored in `msdb` such as jobs, alert, operators, maintenance plans, backup history, Policy-Based Management settings, Database Mail, Performance Data Warehouse, etc.</span></span>  
  
1.  <span data-ttu-id="85407-215">[!INCLUDE[ssDE](../../includes/ssde-md.md)]에이전트, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , [!INCLUDE[ssRS](../../includes/ssrs.md)]를 포함하는 [!INCLUDE[ssIS](../../includes/ssis-md.md)]에 연결된 서비스 및 데이터 저장소와 같은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 를 사용하는 애플리케이션을 모두 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="85407-215">Stop all services connecting to the [!INCLUDE[ssDE](../../includes/ssde-md.md)], including [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent, [!INCLUDE[ssRS](../../includes/ssrs.md)], [!INCLUDE[ssIS](../../includes/ssis-md.md)], and all applications using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] as data store.</span></span>  
  
2.  <span data-ttu-id="85407-216">다음 명령을 사용하여 명령줄에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 를 시작합니다. `NET START MSSQLSERVER /T3608`</span><span class="sxs-lookup"><span data-stu-id="85407-216">Start [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] from the command line using the command: `NET START MSSQLSERVER /T3608`</span></span>  
  
     <span data-ttu-id="85407-217">자세한 내용은 [SQL Server 서비스 시작, 중지, 일시 중지, 재개 및 다시 시작](../../database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="85407-217">For more information, see [Start, Stop, Pause, Resume, Restart the Database Engine, SQL Server Agent, or SQL Server Browser Service](../../database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md).</span></span>  
  
3.  <span data-ttu-id="85407-218">다른 명령줄 창에서 `msdb` 다음 명령을 실행 하 여 데이터베이스를 분리 하 고을 *\<servername>* 인스턴스로 바꿉니다 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .`SQLCMD -E -S<servername> -dmaster -Q"EXEC sp_detach_db msdb"`</span><span class="sxs-lookup"><span data-stu-id="85407-218">In another command line window, detach the `msdb` database by executing the following command, replacing *\<servername>* with the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: `SQLCMD -E -S<servername> -dmaster -Q"EXEC sp_detach_db msdb"`</span></span>  
  
4.  <span data-ttu-id="85407-219">Windows 탐색기를 사용 하 여 데이터베이스 파일의 이름을 바꿉니다 `msdb` .</span><span class="sxs-lookup"><span data-stu-id="85407-219">Using the Windows Explorer, rename the `msdb` database files.</span></span> <span data-ttu-id="85407-220">기본적으로 이러한 데이터베이스는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스의 데이터 하위 폴더에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="85407-220">By default these are in the DATA sub-folder for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span>  
  
5.  <span data-ttu-id="85407-221">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구성 관리자를 사용하여 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 서비스를 중지하고 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="85407-221">Using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, stop and restart the [!INCLUDE[ssDE](../../includes/ssde-md.md)] service normally.</span></span>  
  
6.  <span data-ttu-id="85407-222">명령줄 창에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 를 다시 시작하고 다음 명령을 실행합니다. `SQLCMD -E -S<servername> -i"C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Install\instmsdb.sql" -o" C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Install\instmsdb.out"`</span><span class="sxs-lookup"><span data-stu-id="85407-222">In a command line window, connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and execute the command: `SQLCMD -E -S<servername> -i"C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Install\instmsdb.sql" -o" C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Install\instmsdb.out"`</span></span>  
  
     <span data-ttu-id="85407-223">*\<servername>* 을 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 인스턴스로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="85407-223">Replace *\<servername>* with the instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span> <span data-ttu-id="85407-224">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스의 파일 시스템 경로를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="85407-224">Use the file system path of the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
7.  <span data-ttu-id="85407-225">Windows 메모장을 사용하여 **instmsdb.out** 파일을 열고 오류 출력을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="85407-225">Using the Windows Notepad, open the **instmsdb.out** file and check the output for any errors.</span></span>  
  
8.  <span data-ttu-id="85407-226">인스턴스에 이미 설치된 서비스 팩 또는 핫픽스를 모두 다시 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="85407-226">Re-apply any service packs or hotfix installed on the instance.</span></span>  
  
9. <span data-ttu-id="85407-227">작업, 경고 등의 데이터베이스에 저장 된 사용자 콘텐츠를 다시 만듭니다 `msdb` .</span><span class="sxs-lookup"><span data-stu-id="85407-227">Recreate the user content stored in the `msdb` database, such as jobs, alert, etc.</span></span>  
  
10. <span data-ttu-id="85407-228">`msdb` 데이터베이스를 백업합니다.</span><span class="sxs-lookup"><span data-stu-id="85407-228">Backup the `msdb` database.</span></span>  
  
##  <a name="troubleshoot-rebuild-errors"></a><a name="Troubleshoot"></a> <span data-ttu-id="85407-229">다시 작성 오류 문제 해결</span><span class="sxs-lookup"><span data-stu-id="85407-229">Troubleshoot Rebuild Errors</span></span>  
 <span data-ttu-id="85407-230">구문 및 기타 런타임 오류는 명령 프롬프트 창에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="85407-230">Syntax and other run-time errors are displayed in the command prompt window.</span></span> <span data-ttu-id="85407-231">설치 문에 다음과 같은 구문 오류가 없는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="85407-231">Examine the Setup statement for the following syntax errors:</span></span>  
  
-   <span data-ttu-id="85407-232">각 매개 변수 이름 앞에 슬래시(/)가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="85407-232">Missing slash mark (/) in front of each parameter name.</span></span>  
  
-   <span data-ttu-id="85407-233">매개 변수 이름과 매개 변수 값 사이에 등호(=)가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="85407-233">Missing equal sign (=) between the parameter name and the parameter value.</span></span>  
  
-   <span data-ttu-id="85407-234">매개 변수 이름과 등호 사이에 공백이 없어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="85407-234">Presence of blank spaces between the parameter name and the equal sign.</span></span>  
  
-   <span data-ttu-id="85407-235">구문에 지정되지 않은 쉼표(,)나 기타 문자가 없어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="85407-235">Presence of commas (,) or other characters that are not specified in the syntax.</span></span>  
  
 <span data-ttu-id="85407-236">다시 작성 작업이 완료되면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그를 검토하여 오류가 없는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="85407-236">After the rebuild operation is complete, examine the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] logs for any errors.</span></span> <span data-ttu-id="85407-237">로그의 기본 위치는 C:\Program Files\Microsoft SQL Server\120\Setup Bootstrap\Logs입니다.</span><span class="sxs-lookup"><span data-stu-id="85407-237">The default log location is C:\Program Files\Microsoft SQL Server\120\Setup Bootstrap\Logs.</span></span> <span data-ttu-id="85407-238">다시 작성 프로세스의 결과가 들어 있는 로그 파일을 찾으려면 명령 프롬프트에서 Logs 폴더로 이동한 후 `findstr /s RebuildDatabase summary*.*`를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="85407-238">To locate the log file that contains the results of the rebuild process, change directories to the Logs folder from a command prompt, and then run `findstr /s RebuildDatabase summary*.*`.</span></span> <span data-ttu-id="85407-239">이렇게 검색하면 시스템 데이터베이스 다시 작성의 결과가 들어 있는 모든 로그 파일이 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="85407-239">This search will point you to any log files that contain the results of rebuilding system databases.</span></span> <span data-ttu-id="85407-240">로그 파일을 열고 검토하여 관련된 오류 메시지가 없는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="85407-240">Open the log files and examine them for relevant error messages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85407-241">참고 항목</span><span class="sxs-lookup"><span data-stu-id="85407-241">See Also</span></span>  
 [<span data-ttu-id="85407-242">시스템 데이터베이스</span><span class="sxs-lookup"><span data-stu-id="85407-242">System Databases</span></span>](system-databases.md)  
  
  
