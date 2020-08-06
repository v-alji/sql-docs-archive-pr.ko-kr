---
title: BACPAC 파일을 가져와 새 사용자 데이터베이스 만들기 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.importdac.progress.f1
- sql12.swb. importdac.settings.f1
- sql12.swb.importdac.storagebrowser.f1
- sql12.swb. importdac.summary.f1
- sql12.swb.importdac.results.f1
- sql12.swb. importdac.progress.f1
- sql12.swb.importdac.welcome.f1
- sql12.swb.importdac.settings.f1
- sql12.swb. importdac.results.f1
- sql12.swb.importdac.summary.f1
helpviewer_keywords:
- Data-tier application
- SQL Server DAC
- Migrate database
- DAC
ms.assetid: 736d8d9a-39f1-4bf8-b81f-2e56c134d12e
author: stevestein
ms.author: sstein
ms.openlocfilehash: 66e71453f38fe15f295fceaf63b5edba5ab5ff43
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653439"
---
# <a name="import-a-bacpac-file-to-create-a-new-user-database"></a><span data-ttu-id="6f2fb-102">BACPAC 파일을 가져와 새 사용자 데이터베이스 만들기</span><span class="sxs-lookup"><span data-stu-id="6f2fb-102">Import a BACPAC File to Create a New User Database</span></span>
  <span data-ttu-id="6f2fb-103">DAC(데이터 계층 애플리케이션) 파일(.bacpac 파일)을 가져와 [!INCLUDE[ssDE](../../includes/ssde-md.md)]의 새 인스턴스에서 또는 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]에 데이터를 사용하여 원본 데이터베이스의 복제본을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="6f2fb-103">Import a data-tier application (DAC) file - a .bacpac file - to create a copy of the original database, with the data, on a new instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)], or to [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].</span></span> <span data-ttu-id="6f2fb-104">내보내기 및 가져오기 작업을 결합하여 인스턴스 간에 DAC나 데이터베이스를 마이그레이션하거나 논리 백업을 만들 수 있습니다. 예를 들어 [!INCLUDE[ssSDS](../../includes/sssds-md.md)]에 배포된 데이터베이스의 온-프레미스 복사본을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f2fb-104">Export-import operations can be combined to migrate a DAC or database between instances, or to create a logical backup, such as creating an on-premise copy of a database deployed in [!INCLUDE[ssSDS](../../includes/sssds-md.md)].</span></span>  
  
## <a name="before-you-begin"></a><span data-ttu-id="6f2fb-105">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="6f2fb-105">Before You Begin</span></span>  
 <span data-ttu-id="6f2fb-106">가져오기 프로세스에서는 새로운 DAC를 두 단계로 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="6f2fb-106">The import process builds a new DAC in two stages.</span></span>  
  
1.  <span data-ttu-id="6f2fb-107">DAC 배포 시 DAC 패키지 파일의 정의로부터 새로운 DAC가 만들어지는 것과 마찬가지로, 가져오기 프로세스에서는 내보내기 파일에 저장된 DAC 정의를 사용하여 새 DAC와 관련 데이터베이스가 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="6f2fb-107">The import creates a new DAC and associated database using the DAC definition stored in the export file, the same way a DAC deploy creates a new DAC from the definition in a DAC package file.</span></span>  
  
2.  <span data-ttu-id="6f2fb-108">내보내기 파일의 데이터에서 대량 복사본 가져오기</span><span class="sxs-lookup"><span data-stu-id="6f2fb-108">The import bulk copies in the data from the export file.</span></span>  
  
 
## <a name="sql-server-utility"></a><span data-ttu-id="6f2fb-109">SQL Server 유틸리티</span><span class="sxs-lookup"><span data-stu-id="6f2fb-109">SQL Server Utility</span></span>  
 <span data-ttu-id="6f2fb-110">DAC를 데이터베이스 엔진의 관리되는 인스턴스로 가져오는 경우 가져온 DAC는 유틸리티 컬렉션 집합이 다음에 인스턴스에서 유틸리티 제어 지점으로 전송될 때 SQL Server 유틸리티로 통합됩니다.</span><span class="sxs-lookup"><span data-stu-id="6f2fb-110">If you import a DAC to a managed instance of the Database Engine, the imported DAC is incorporated into the SQL Server Utility the next time the utility collection set is sent from the instance to the utility control point.</span></span> <span data-ttu-id="6f2fb-111">그러면 DAC가 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] **유틸리티 탐색기**의 **배포된 데이터 계층 애플리케이션 노드**에 표시되고 **배포된 데이터 계층 애플리케이션** 세부 정보 페이지에 보고됩니다.</span><span class="sxs-lookup"><span data-stu-id="6f2fb-111">The DAC will then be present in the **Deployed Data-tier Applications** node of the [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] **Utility Explorer** and reported in the **Deployed Data-tier Applications** details page.</span></span>  
  
## <a name="database-options-and-settings"></a><span data-ttu-id="6f2fb-112">데이터베이스 옵션 및 설정</span><span class="sxs-lookup"><span data-stu-id="6f2fb-112">Database Options and Settings</span></span>  
 <span data-ttu-id="6f2fb-113">기본적으로 가져오기 중에 만들어진 데이터베이스에는 CREATE DATABASE 문의 모든 기본 설정이 적용됩니다. 단, 데이터베이스 데이터 정렬 및 호환성 수준은 DAC 내보내기 파일에 정의된 값으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="6f2fb-113">By default, the database created during the import will have all of the default settings from the CREATE DATABASE statement, except that the database collation and compatibility level are set to the values defined in the DAC export file.</span></span> <span data-ttu-id="6f2fb-114">DAC 내보내기 파일은 원본 데이터베이스의 값을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6f2fb-114">A DAC export file uses the values from the original database.</span></span>  
  
 <span data-ttu-id="6f2fb-115">TRUSTWORTHY, DB_CHAINING 및 HONOR_BROKER_PRIORITY와 같은 일부 데이터베이스 옵션은 가져오기 프로세스 도중 조정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6f2fb-115">Some database options, such as TRUSTWORTHY, DB_CHAINING, and HONOR_BROKER_PRIORITY, cannot be adjusted as part of the import process.</span></span> <span data-ttu-id="6f2fb-116">파일 그룹의 수, 파일의 수 및 크기와 같은 물리적 속성은 가져오기 프로세스 도중 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6f2fb-116">Physical properties, such as the number of filegroups, or the numbers and sizes of files cannot be altered as part of the import process.</span></span> <span data-ttu-id="6f2fb-117">가져오기가 완료된 후 ALTER DATABASE 문, [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]또는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell을 사용하여 데이터베이스를 맞춤 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f2fb-117">After the import completes, you can use the ALTER DATABASE statement, [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell to tailor the database.</span></span> <span data-ttu-id="6f2fb-118">자세한 내용은 [Databases](../databases/databases.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6f2fb-118">For more information, see [Databases](../databases/databases.md).</span></span>  
  
## <a name="limitations-and-restrictions"></a><span data-ttu-id="6f2fb-119">제한 사항</span><span class="sxs-lookup"><span data-stu-id="6f2fb-119">Limitations and Restrictions</span></span>  
 <span data-ttu-id="6f2fb-120">[!INCLUDE[ssSDS](../../includes/sssds-md.md)]SP4(서비스 팩 4) 이상을 실행하는 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 인스턴스 또는 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 에만 DAC를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f2fb-120">A DAC can be imported to [!INCLUDE[ssSDS](../../includes/sssds-md.md)], or an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] running [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 4 (SP4) or later.</span></span> <span data-ttu-id="6f2fb-121">이후 버전에서 DAC를 내보내는 경우 DAC에 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]에서 지원되지 않는 개체가 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f2fb-121">If you export a DAC from a higher version, the DAC may contain objects not supported by [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].</span></span> <span data-ttu-id="6f2fb-122">이러한 DAC를 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]인스턴스에 배포할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6f2fb-122">You cannot deploy those DACs to instances of [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="6f2fb-123">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="6f2fb-123">Prerequisites</span></span>  
 <span data-ttu-id="6f2fb-124">출처를 알 수 없거나 신뢰할 수 없는 DAC 내보내기 파일은 가져오지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="6f2fb-124">We recommend that you do not import a DAC export file from unknown or untrusted sources.</span></span> <span data-ttu-id="6f2fb-125">이러한 파일에 포함된 악성 코드가 의도하지 않은 Transact-SQL 코드를 실행하거나 스키마를 수정하여 오류가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f2fb-125">Such files could contain malicious code that might execute unintended Transact-SQL code or cause errors by modifying the schema.</span></span> <span data-ttu-id="6f2fb-126">출처를 알 수 없거나 신뢰할 수 없는 내보내기 파일을 사용하려면 먼저 DAC의 압축을 풀고 저장 프로시저 및 다른 사용자 정의 코드와 같은 코드를 검사하세요.</span><span class="sxs-lookup"><span data-stu-id="6f2fb-126">Before you use an export file from an unknown or untrusted source, unpack the DAC and examine the code, like stored procedures and other user-defined code.</span></span> <span data-ttu-id="6f2fb-127">이러한 검사를 수행하는 방법은 [Validate a DAC Package](validate-a-dac-package.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6f2fb-127">For more information about how to perform these checks, see [Validate a DAC Package](validate-a-dac-package.md).</span></span>  
  
## <a name="security"></a><span data-ttu-id="6f2fb-128">보안</span><span class="sxs-lookup"><span data-stu-id="6f2fb-128">Security</span></span>  
 <span data-ttu-id="6f2fb-129">보안을 개선하기 위해 SQL Server 인증 로그인은 암호 없이 DAC 내보내기 파일에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="6f2fb-129">To improve security, SQL Server Authentication logins are stored in a DAC export file without a password.</span></span> <span data-ttu-id="6f2fb-130">파일을 가져오면 생성된 암호와 함께 비활성 로그인이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="6f2fb-130">When the file is imported, the login is created as a disabled login with a generated password.</span></span> <span data-ttu-id="6f2fb-131">로그인을 활성화하려면 ALTER ANY LOGIN 권한이 있는 로그인을 사용하여 로그인하고 ALTER LOGIN을 사용하여 로그인을 활성화하여 사용자에게 알려 줄 수 있는 새 암호를 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="6f2fb-131">To enable the logins, log in using a login that has ALTER ANY LOGIN permission and use ALTER LOGIN to enable the login and assign a new password that can be communicated to the user.</span></span> <span data-ttu-id="6f2fb-132">Windows 인증 로그인의 경우 암호가 SQL Server에서 관리되지 않으므로 이 과정이 필요 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6f2fb-132">This is not needed for Windows Authentication logins because their passwords are not managed by SQL Server.</span></span>  
  
## <a name="permissions"></a><span data-ttu-id="6f2fb-133">사용 권한</span><span class="sxs-lookup"><span data-stu-id="6f2fb-133">Permissions</span></span>  
 <span data-ttu-id="6f2fb-134">**sysadmin** 또는 **serveradmin** 고정 서버 역할의 멤버를 통하거나 **dbcreator** 고정 서버 역할에 포함되고 ALTER ANY LOGIN 권한이 있는 로그인을 통해서만 DAC를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f2fb-134">A DAC can only be imported by members of the **sysadmin** or **serveradmin** fixed server roles, or by logins that are in the **dbcreator** fixed server role and have ALTER ANY LOGIN permissions.</span></span> <span data-ttu-id="6f2fb-135">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sa **라는 기본 제공** 시스템 관리자 계정도 DAC를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f2fb-135">The built-in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system administrator account named **sa** can also import a DAC.</span></span> <span data-ttu-id="6f2fb-136">[!INCLUDE[ssSDS](../../includes/sssds-md.md)] 에 대한 로그인이 있는 DAC를 가져오려면 loginmanager 또는 serveradmin 역할의 멤버 자격이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="6f2fb-136">Importing a DAC with logins to [!INCLUDE[ssSDS](../../includes/sssds-md.md)] requires membership in the loginmanager or serveradmin roles.</span></span> <span data-ttu-id="6f2fb-137">[!INCLUDE[ssSDS](../../includes/sssds-md.md)] 에 대한 로그인이 없는 DAC를 가져오려면 dbmanager 또는 serveradmin 역할의 멤버 자격이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="6f2fb-137">Importing a DAC without logins to [!INCLUDE[ssSDS](../../includes/sssds-md.md)] requires membership in the dbmanager or serveradmin roles.</span></span>  
  
## <a name="using-the-import-data-tier-application-wizard"></a><span data-ttu-id="6f2fb-138">데이터 계층 애플리케이션 가져오기 마법사 사용</span><span class="sxs-lookup"><span data-stu-id="6f2fb-138">Using the Import Data-tier Application Wizard</span></span>  
 <span data-ttu-id="6f2fb-139">**마법사를 시작하려면 다음 단계를 따르십시오.**</span><span class="sxs-lookup"><span data-stu-id="6f2fb-139">**To launch the wizard, use the following steps:**</span></span>  
  
1.  <span data-ttu-id="6f2fb-140">온-프레미스 또는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 [!INCLUDE[ssSDS](../../includes/sssds-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="6f2fb-140">Connect to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], whether on-premise or in [!INCLUDE[ssSDS](../../includes/sssds-md.md)].</span></span>  
  
2.  <span data-ttu-id="6f2fb-141">**개체 탐색기**에서 **데이터베이스**를 마우스 오른쪽 단추로 클릭한 후 **데이터 계층 애플리케이션 가져오기** 메뉴 항목을 선택하여 마법사를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="6f2fb-141">In **Object Explorer**, right-click on **Databases**, and then select the **Import Data-tier Application** menu item to launch the wizard.</span></span>  
  
3.  <span data-ttu-id="6f2fb-142">마법사 대화 상자를 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="6f2fb-142">Complete the wizard dialogs:</span></span>  
  
    -   [<span data-ttu-id="6f2fb-143">소개 페이지</span><span class="sxs-lookup"><span data-stu-id="6f2fb-143">Introduction Page</span></span>](#Introduction)  
  
    -   [<span data-ttu-id="6f2fb-144">가져오기 설정 페이지</span><span class="sxs-lookup"><span data-stu-id="6f2fb-144">Import Settings Page</span></span>](#Import_settings)  
  
    -   [<span data-ttu-id="6f2fb-145">데이터베이스 설정 페이지</span><span class="sxs-lookup"><span data-stu-id="6f2fb-145">Database Settings Page</span></span>](#Database_settings)  
  
    -   [<span data-ttu-id="6f2fb-146">요약 페이지</span><span class="sxs-lookup"><span data-stu-id="6f2fb-146">Summary Page</span></span>](#Summary)  
  
    -   [<span data-ttu-id="6f2fb-147">진행률 페이지</span><span class="sxs-lookup"><span data-stu-id="6f2fb-147">Progress Page</span></span>](#Progress)  
  
    -   [<span data-ttu-id="6f2fb-148">결과 페이지</span><span class="sxs-lookup"><span data-stu-id="6f2fb-148">Results Page</span></span>](#Results)  
  
###  <a name="introduction-page"></a><a name="Introduction"></a> <span data-ttu-id="6f2fb-149">소개 페이지</span><span class="sxs-lookup"><span data-stu-id="6f2fb-149">Introduction Page</span></span>  
 <span data-ttu-id="6f2fb-150">이 페이지에서는 데이터 계층 애플리케이션 가져오기 마법사의 단계에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="6f2fb-150">This page describes the steps for the Data-tier Application Import Wizard.</span></span>  
  
 <span data-ttu-id="6f2fb-151">**옵션**</span><span class="sxs-lookup"><span data-stu-id="6f2fb-151">**Options**</span></span>  
  
-   <span data-ttu-id="6f2fb-152">**이 페이지를 다시 표시 안 함**</span><span class="sxs-lookup"><span data-stu-id="6f2fb-152">**Do not show this page again.**</span></span> <span data-ttu-id="6f2fb-153">- 앞으로 소개 페이지가 표시되지 않도록 하려면 이 확인란을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6f2fb-153">- Click the check box to stop the Introduction page from being displayed in the future.</span></span>  
  
-   <span data-ttu-id="6f2fb-154">**다음** - **가져오기 설정** 페이지로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="6f2fb-154">**Next** - Proceeds to the **Import Settings** page.</span></span>  
  
-   <span data-ttu-id="6f2fb-155">**취소** - 작업을 취소하고 마법사를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="6f2fb-155">**Cancel** - Cancels the operation and closes the wizard.</span></span>  
  
###  <a name="import-settings-page"></a><a name="Import_settings"></a> <span data-ttu-id="6f2fb-156">가져오기 설정 페이지</span><span class="sxs-lookup"><span data-stu-id="6f2fb-156">Import Settings Page</span></span>  
 <span data-ttu-id="6f2fb-157">이 페이지에서 가져올 .bacpac 파일의 위치를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f2fb-157">Use this page to specify the location of the .bacpac file to import.</span></span>  
  
-   <span data-ttu-id="6f2fb-158">**로컬 디스크에서 가져오기** - **찾아보기...** 를 클릭하고 로컬 컴퓨터로 이동하거나 제공된 공간에서 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6f2fb-158">**Import from local disk** - Click **Browse...** to navigate the local computer, or specify the path in the space provided.</span></span> <span data-ttu-id="6f2fb-159">경로 이름에 파일 이름과 .bacpac 확장명을 모두 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f2fb-159">The path name must include a file name and the .bacpac extension.</span></span>  
  
-   <span data-ttu-id="6f2fb-160">**Azure에서 가져오기** -azure 컨테이너에서 BACPAC 파일을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="6f2fb-160">**Import from Azure** - Imports a BACPAC file from an Azure container.</span></span> <span data-ttu-id="6f2fb-161">이 옵션의 유효성을 검사하려면 Azure 컨테이너에 연결해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f2fb-161">You must connect to an Azure container in order to validate this option.</span></span> <span data-ttu-id="6f2fb-162">또한 이 옵션을 사용하려면 임시 파일을 보관할 로컬 디렉터리를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f2fb-162">Note that this option also requires that you specify a local directory for the temporary file.</span></span> <span data-ttu-id="6f2fb-163">지정된 위치에 임시 파일이 만들어지고 작업이 완료될 때까지 해당 위치에 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="6f2fb-163">The temporary file will be created at the specified location and will remain there after the operation completes.</span></span>  
  
     <span data-ttu-id="6f2fb-164">Azure를 검색할 때 단일 계정으로 컨테이너 간을 전환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f2fb-164">When browsing Azure, you will be able to switch between containers within a single account.</span></span> <span data-ttu-id="6f2fb-165">가져오기 작업을 계속하려면 단일 .bacpac 파일을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f2fb-165">You must specify a single .bacpac file to continue the import operation.</span></span> <span data-ttu-id="6f2fb-166">**이름**, **크기**또는 **수정한 날짜**별로 열을 정렬할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f2fb-166">Note that you can sort columns by **Name**, **Size**, or **Date Modified**.</span></span>  
  
     <span data-ttu-id="6f2fb-167">계속하려면 가져올 .bacpac 파일을 지정하고 **열기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6f2fb-167">To continue, specify the .bacpac file to import, and then click **Open**.</span></span>  
  
###  <a name="database-settings-page"></a><a name="Database_settings"></a> <span data-ttu-id="6f2fb-168">데이터베이스 설정 페이지</span><span class="sxs-lookup"><span data-stu-id="6f2fb-168">Database Settings Page</span></span>  
 <span data-ttu-id="6f2fb-169">이 페이지에서 만들려는 데이터베이스의 세부 정보를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f2fb-169">Use this page to specify details for the database that will be created.</span></span>  
  
 <span data-ttu-id="6f2fb-170">**로컬 SQL Server 인스턴스의 경우**</span><span class="sxs-lookup"><span data-stu-id="6f2fb-170">**For a local instance of SQL Server:**</span></span>  
  
-   <span data-ttu-id="6f2fb-171">**새 데이터베이스 이름** – 가져온 데이터베이스의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6f2fb-171">**New database name** - Provide a name for the imported database.</span></span>  
  
-   <span data-ttu-id="6f2fb-172">**데이터 파일 경로** - 데이터 파일을 저장할 로컬 디렉터리를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6f2fb-172">**Data file path** - Provide a local directory for data files.</span></span> <span data-ttu-id="6f2fb-173">**찾아보기...** 를 클릭하여 로컬 컴퓨터로 이동하거나 제공된 공간에 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6f2fb-173">Click **Browse...** to navigate the local computer, or specify the path in the space provided.</span></span>  
  
-   <span data-ttu-id="6f2fb-174">**로그 파일 경로** – 로그 파일을 저장할 로컬 디렉터리를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="6f2fb-174">**Log file path** - Provide a local directory for log files.</span></span> <span data-ttu-id="6f2fb-175">**찾아보기...** 를 클릭하여 로컬 컴퓨터로 이동하거나 제공된 공간에 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6f2fb-175">Click **Browse...** to navigate the local computer, or specify the path in the space provided.</span></span>  
  
 <span data-ttu-id="6f2fb-176">계속하려면 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6f2fb-176">To continue, click **Next**.</span></span>  
  
 <span data-ttu-id="6f2fb-177">**SQL 데이터베이스의 경우:**</span><span class="sxs-lookup"><span data-stu-id="6f2fb-177">**For a SQL Database:**</span></span>  
  
-   <span data-ttu-id="6f2fb-178">**새 데이터베이스 이름** -가져온 데이터베이스의 이름을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f2fb-178">**New database name** - Provide a name for the imported database.</span></span>  
  
-   <span data-ttu-id="6f2fb-179">\*\*버전 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] \*\* - [!INCLUDE[ssSDS](../../includes/sssds-md.md)] 비즈니스 또는 웹을 지정 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f2fb-179">**Edition of [!INCLUDE[ssSDS](../../includes/sssds-md.md)]** - Specify [!INCLUDE[ssSDS](../../includes/sssds-md.md)] Business or [!INCLUDE[ssSDS](../../includes/sssds-md.md)] Web.</span></span> <span data-ttu-id="6f2fb-180">[!INCLUDE[ssSDS](../../includes/sssds-md.md)] 버전에 대한 자세한 내용은 이 [SQL Database](https://www.windowsazure.com/home/tour/database/) 웹 사이트를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6f2fb-180">For more information about editions of [!INCLUDE[ssSDS](../../includes/sssds-md.md)], see this [SQL Database](https://www.windowsazure.com/home/tour/database/) web site.</span></span>  
  
-   <span data-ttu-id="6f2fb-181">**최대 데이터베이스 크기 (GB)** -드롭다운 메뉴를 사용 하 여 데이터베이스의 최대 크기를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f2fb-181">**Maximum database size (GB)** - Use the drop-down menu to specify the maximum size for your database.</span></span>  
  
 <span data-ttu-id="6f2fb-182">계속하려면 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6f2fb-182">To continue, click **Next**.</span></span>  
  
### <a name="validation-page"></a><span data-ttu-id="6f2fb-183">유효성 검사 페이지</span><span class="sxs-lookup"><span data-stu-id="6f2fb-183">Validation Page</span></span>  
 <span data-ttu-id="6f2fb-184">이 페이지에서 작업을 차단한 문제를 검토할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f2fb-184">Use this page to review any issues that block the operation.</span></span> <span data-ttu-id="6f2fb-185">계속하려면 차단 문제를 해결하고 **유효성 검사 다시 실행** 을 클릭하여 유효성 검사에 성공했는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="6f2fb-185">To continue, resolve blocking issues and then click **Re-run Validation** to ensure that validation is successful.</span></span>  
  
 <span data-ttu-id="6f2fb-186">계속하려면 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6f2fb-186">To continue, click **Next**.</span></span>  
  
###  <a name="summary-page"></a><a name="Summary"></a> <span data-ttu-id="6f2fb-187">요약 페이지</span><span class="sxs-lookup"><span data-stu-id="6f2fb-187">Summary Page</span></span>  
 <span data-ttu-id="6f2fb-188">이 페이지에서 작업에 대해 지정한 원본 및 대상 설정을 검토할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f2fb-188">Use this page to review the specified source and target settings for the operation.</span></span> <span data-ttu-id="6f2fb-189">지정한 설정을 사용하여 가져오기 작업을 완료하려면 **마침**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6f2fb-189">To complete the import operation using the specified settings, click **Finish**.</span></span> <span data-ttu-id="6f2fb-190">가져오기 작업을 취소하고 마법사를 종료하려면 **취소**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6f2fb-190">To cancel the import operation and exit the wizard, click **Cancel**.</span></span>  
  
###  <a name="progress-page"></a><a name="Progress"></a> <span data-ttu-id="6f2fb-191">진행률 페이지</span><span class="sxs-lookup"><span data-stu-id="6f2fb-191">Progress Page</span></span>  
 <span data-ttu-id="6f2fb-192">이 페이지에는 작업 상태를 나타내는 진행률 표시줄이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="6f2fb-192">This page displays a progress bar that indicates the status of the operation.</span></span> <span data-ttu-id="6f2fb-193">자세한 상태를 보려면 **자세히 보기** 옵션을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6f2fb-193">To view detailed status, click the **View details** option.</span></span>  
  
 <span data-ttu-id="6f2fb-194">계속하려면 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6f2fb-194">To continue, click **Next**.</span></span>  
  
###  <a name="results-page"></a><a name="Results"></a><span data-ttu-id="6f2fb-195">결과 페이지</span><span class="sxs-lookup"><span data-stu-id="6f2fb-195">Results Page</span></span>  
 <span data-ttu-id="6f2fb-196">이 페이지에는 데이터베이스 가져오기 및 만들기 작업의 결과가 성공 또는 실패로 보고됩니다.</span><span class="sxs-lookup"><span data-stu-id="6f2fb-196">This page reports the success or failure of the import and create database operations, showing the success or failure of each action.</span></span> <span data-ttu-id="6f2fb-197">오류가 발생한 동작에는 모두 **결과** 열에 링크가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f2fb-197">Any action that encountered an error will have a link in the **Result** column.</span></span> <span data-ttu-id="6f2fb-198">링크를 클릭하면 해당 동작의 오류에 대한 보고서가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="6f2fb-198">Click the link to view a report of the error for that action.</span></span>  
  
 <span data-ttu-id="6f2fb-199">**닫기**를 클릭하여 마법사를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="6f2fb-199">Click **Close** to close the wizard.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f2fb-200">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6f2fb-200">See Also</span></span>  
 <span data-ttu-id="6f2fb-201">[데이터 계층 애플리케이션](data-tier-applications.md) </span><span class="sxs-lookup"><span data-stu-id="6f2fb-201">[Data-tier Applications](data-tier-applications.md) </span></span>  
 [<span data-ttu-id="6f2fb-202">데이터 계층 애플리케이션 내보내기</span><span class="sxs-lookup"><span data-stu-id="6f2fb-202">Export a Data-tier Application</span></span>](export-a-data-tier-application.md)  
  
