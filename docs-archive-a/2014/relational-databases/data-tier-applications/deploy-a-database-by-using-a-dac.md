---
title: DAC를 사용하여 데이터베이스 배포 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.dbdeployment.settings.f1
- sql12.swb.dbdeployment.progress.f1
- sql12.swb.dbdeployment.summary.f1
- sql12.swb.dbdeployment.results.f1
- sql12.swb.dbdeployment.welcome.f1
helpviewer_keywords:
- deploy database wizard
- database deploy [SQL Server]
ms.assetid: 08c506e8-4ba0-4a19-a066-6e6a5c420539
author: stevestein
ms.author: sstein
ms.openlocfilehash: f753cfaf44e51b5bd3ffb939e38e2a300acb9703
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740030"
---
# <a name="deploy-a-database-by-using-a-dac"></a><span data-ttu-id="639d9-102">DAC를 사용 하여 데이터베이스 배포</span><span class="sxs-lookup"><span data-stu-id="639d9-102">Deploy a Database By Using a DAC</span></span>
  <span data-ttu-id="639d9-103">**SQL Azure에 데이터베이스 배포** 마법사를 사용하여 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 인스턴스와 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] 서버 간에 또는 두 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]서버 간에 데이터베이스를 배포합니다.</span><span class="sxs-lookup"><span data-stu-id="639d9-103">Use the **Deploy a Database to SQL Azure** Wizard to deploy a database between an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] and a [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] server, or between two [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]servers.</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeBegin"></a> <span data-ttu-id="639d9-104">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="639d9-104">Before You Begin</span></span>  
 <span data-ttu-id="639d9-105">마법사는 DAC(데이터 계층 애플리케이션) BACPAC 아카이브 파일을 사용하여 데이터 및 데이터베이스 개체의 데이터 및 정의를 배포합니다.</span><span class="sxs-lookup"><span data-stu-id="639d9-105">The wizard uses a Data-tier Application (DAC) BACPAC archive file to deploy both the data and the definitions of database objects.</span></span> <span data-ttu-id="639d9-106">원본 데이터베이스에서 DAC 내보내기 작업과 대상으로 DAC 가져오기 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="639d9-106">It performs a DAC export operation from the source database, and a DAC import to the destination.</span></span>  
  
###  <a name="database-options-and-settings"></a><a name="DBOptSettings"></a> <span data-ttu-id="639d9-107">데이터베이스 옵션 및 설정</span><span class="sxs-lookup"><span data-stu-id="639d9-107">Database Options and Settings</span></span>  
 <span data-ttu-id="639d9-108">기본적으로 배포 중에 생성된 데이터베이스에는 CREATE DATABASE 문의 기본 설정이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="639d9-108">By default, the database created during the deployment will have the default settings from the CREATE DATABASE statement.</span></span> <span data-ttu-id="639d9-109">예외는 데이터베이스 데이터 정렬 및 호환성 수준이 원본 데이터베이스의 값으로 설정된다는 점입니다.</span><span class="sxs-lookup"><span data-stu-id="639d9-109">The exception is that the database collation and compatibility level are set to the values from the source database.</span></span>  
  
 <span data-ttu-id="639d9-110">TRUSTWORTHY, DB_CHAINING 및 HONOR_BROKER_PRIORITY와 같은 데이터베이스 옵션은 배포 프로세스 도중 조정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="639d9-110">Database options, such as TRUSTWORTHY, DB_CHAINING and HONOR_BROKER_PRIORITY, cannot be adjusted as part of the deployment process.</span></span> <span data-ttu-id="639d9-111">파일 그룹의 수, 파일의 수 및 크기와 같은 물리적 속성은 배포 프로세스 도중 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="639d9-111">Physical properties, such as the number of filegroups, or the numbers and sizes of files cannot be altered as part of the deployment process.</span></span> <span data-ttu-id="639d9-112">배포가 완료된 후 ALTER DATABASE 문, [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]또는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell을 사용하여 데이터베이스를 맞춤 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="639d9-112">After the deployment completes, you can use the ALTER DATABASE statement, [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell to tailor the database.</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="LimitationsRestrictions"></a> <span data-ttu-id="639d9-113">제한 사항</span><span class="sxs-lookup"><span data-stu-id="639d9-113">Limitations and Restrictions</span></span>  
 <span data-ttu-id="639d9-114">**데이터베이스 배포** 마법사는 다음과 같은 데이터베이스 배포를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="639d9-114">The **Deploy Database** wizard supports deploying a database:</span></span>  
  
-   <span data-ttu-id="639d9-115">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 의 인스턴스에서 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]로 배포</span><span class="sxs-lookup"><span data-stu-id="639d9-115">From an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] to [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].</span></span>  
  
-   <span data-ttu-id="639d9-116">[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] 에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]의 인스턴스로 배포</span><span class="sxs-lookup"><span data-stu-id="639d9-116">From [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] to an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
-   <span data-ttu-id="639d9-117">두 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] 서버 간에 배포</span><span class="sxs-lookup"><span data-stu-id="639d9-117">Between two [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] servers.</span></span>  
  
 <span data-ttu-id="639d9-118">마법사는 [!INCLUDE[ssDE](../../includes/ssde-md.md)]의 두 인스턴스 간의 배포를 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="639d9-118">The wizard does not support deploying databases between two instances of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
 <span data-ttu-id="639d9-119">마법사를 작동하려면 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 의 인스턴스가 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] SP4(서비스 팩 4) 이상을 실행하고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="639d9-119">An instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] must be running [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 4 (SP4) or later to work with the wizard.</span></span> <span data-ttu-id="639d9-120">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 인스턴스의 데이터베이스에 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]에서 지원되지 않는 개체가 포함되는 경우 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]에 데이터베이스를 배포하는 데 마법사를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="639d9-120">If a database on an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] contains objects not supported on [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)], you cannot use the wizard to deploy the database to [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].</span></span> <span data-ttu-id="639d9-121">[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] 의 데이터베이스에 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 지원되지 않는 개체가 포함되는 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스에 데이터베이스를 배포하는 데 마법사를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="639d9-121">If a database on [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] contains objects not supported by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], you cannot use the wizard to deploy the database to instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="639d9-122">보안</span><span class="sxs-lookup"><span data-stu-id="639d9-122">Security</span></span>  
 <span data-ttu-id="639d9-123">보안을 개선하기 위해 SQL Server 인증 로그인은 암호 없이 DAC BACPAC 파일에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="639d9-123">To improve security, SQL Server Authentication logins are stored in a DAC BACPAC file without a password.</span></span> <span data-ttu-id="639d9-124">BACPAC를 가져오면 생성된 암호와 함께 비활성 로그인이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="639d9-124">When the BACPAC is imported, the login is created as a disabled login with a generated password.</span></span> <span data-ttu-id="639d9-125">로그인을 활성화하려면 ALTER ANY LOGIN 권한이 있는 로그인을 사용하여 로그인하고 ALTER LOGIN을 사용하여 로그인을 활성화하여 사용자에게 알려 줄 수 있는 새 암호를 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="639d9-125">To enable the logins, log in using a login that has ALTER ANY LOGIN permission and use ALTER LOGIN to enable the login and assign a new password that can be communicated to the user.</span></span> <span data-ttu-id="639d9-126">Windows 인증 로그인의 경우 암호가 SQL Server에서 관리되지 않으므로 이 과정이 필요 없습니다.</span><span class="sxs-lookup"><span data-stu-id="639d9-126">This is not needed for Windows Authentication logins because their passwords are not managed by SQL Server.</span></span>  
  
#### <a name="permissions"></a><span data-ttu-id="639d9-127">사용 권한</span><span class="sxs-lookup"><span data-stu-id="639d9-127">Permissions</span></span>  
 <span data-ttu-id="639d9-128">마법사에 원본 데이터베이스에 대한 DAC 내보내기 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="639d9-128">The wizard requires DAC export permissions on the source database.</span></span> <span data-ttu-id="639d9-129">로그인하려면 **sys.sql_expression_dependencies**에 대한 SELECT 권한뿐만 아니라 최소한 ALTER ANY LOGIN 및 데이터베이스 범위 VIEW DEFINITION 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="639d9-129">The login requires at least ALTER ANY LOGIN and database scope VIEW DEFINITION permissions, as well as SELECT permissions on **sys.sql_expression_dependencies**.</span></span> <span data-ttu-id="639d9-130">DAC를 내보내려면 securityadmin 고정 서버 역할의 멤버이면서 DAC를 내보내는 데이터베이스의 database_owner 고정 데이터베이스 역할의 멤버여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="639d9-130">Exporting a DAC can be done by members of the securityadmin fixed server role who are also members of the database_owner fixed database role in the database from which the DAC is exported.</span></span> <span data-ttu-id="639d9-131">sysadmin 고정 서버 역할의 멤버 또는 기본 제공 SQL Server 시스템 관리자 계정인 **sa** 는 DAC를 내보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="639d9-131">Members of the sysadmin fixed server role or the built-in SQL Server system administrator account named **sa** can also export a DAC.</span></span>  
  
 <span data-ttu-id="639d9-132">마법사에 대상 인스턴스 또는 서버에 대한 DAC 가져오기 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="639d9-132">The wizard requires DAC import permissions on the destination instance or server.</span></span> <span data-ttu-id="639d9-133">로그인은 **sysadmin** 또는 **serveradmin** 고정 서버 역할의 멤버이거나 **dbcreator** 고정 서버 역할에 포함되고 ALTER ANY LOGIN 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="639d9-133">The login must be a member of the **sysadmin** or **serveradmin** fixed server roles, or in the **dbcreator** fixed server role and have ALTER ANY LOGIN permissions.</span></span> <span data-ttu-id="639d9-134">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sa **라는 기본 제공** 시스템 관리자 계정도 DAC를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="639d9-134">The built-in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system administrator account named **sa** can also import a DAC.</span></span> <span data-ttu-id="639d9-135">[!INCLUDE[ssSDS](../../includes/sssds-md.md)] 에 대한 로그인이 있는 DAC를 가져오려면 loginmanager 또는 serveradmin 역할의 멤버 자격이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="639d9-135">Importing a DAC with logins to [!INCLUDE[ssSDS](../../includes/sssds-md.md)] requires membership in the loginmanager or serveradmin roles.</span></span> <span data-ttu-id="639d9-136">[!INCLUDE[ssSDS](../../includes/sssds-md.md)] 에 대한 로그인이 없는 DAC를 가져오려면 dbmanager 또는 serveradmin 역할의 멤버 자격이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="639d9-136">Importing a DAC without logins to [!INCLUDE[ssSDS](../../includes/sssds-md.md)] requires membership in the dbmanager or serveradmin roles.</span></span>  
  
##  <a name="using-the-deploy-database-wizard"></a><a name="UsingDeployDACWizard"></a> <span data-ttu-id="639d9-137">데이터베이스 배포 마법사 사용</span><span class="sxs-lookup"><span data-stu-id="639d9-137">Using the Deploy Database Wizard</span></span>  
 <span data-ttu-id="639d9-138">**데이터베이스 배포 마법사를 사용하여 데이터베이스를 마이그레이션하려면**</span><span class="sxs-lookup"><span data-stu-id="639d9-138">**To migrate a database using the Deploy Database Wizard**</span></span>  
  
1.  <span data-ttu-id="639d9-139">배포하려는 데이터베이스의 위치에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="639d9-139">Connect to the location of the database you want to deploy.</span></span> <span data-ttu-id="639d9-140">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 인스턴스 또는 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] 서버를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="639d9-140">You can specify either an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)] or a [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] server.</span></span>  
  
2.  <span data-ttu-id="639d9-141">**개체 탐색기**에서 데이터베이스가 있는 인스턴스에 대한 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="639d9-141">In **Object Explorer**, expand the node for the instance that has the database.</span></span>  
  
3.  <span data-ttu-id="639d9-142">**데이터베이스** 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="639d9-142">Expand the **Databases** node.</span></span>  
  
4.  <span data-ttu-id="639d9-143">배포하려는 데이터베이스를 마우스 오른쪽 단추로 클릭하고 **태스크**를 선택한 다음, **SQL Azure에 데이터베이스 배포...** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="639d9-143">Right click the database you want to deploy, select **Tasks**, and then select **Deploy Database to SQL Azure...**</span></span>  
  
5.  <span data-ttu-id="639d9-144">다음 마법사 대화 상자를 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="639d9-144">Complete the Wizard dialogs:</span></span>  
  
    -   [<span data-ttu-id="639d9-145">소개 페이지</span><span class="sxs-lookup"><span data-stu-id="639d9-145">Introduction Page</span></span>](#Introduction)  
  
    -   [<span data-ttu-id="639d9-146">배포 설정</span><span class="sxs-lookup"><span data-stu-id="639d9-146">Deployment Settings</span></span>](#Deployment_settings)  
  
    -   [<span data-ttu-id="639d9-147">요약 페이지</span><span class="sxs-lookup"><span data-stu-id="639d9-147">Summary Page</span></span>](#Summary)  
  
    -   [<span data-ttu-id="639d9-148">결과</span><span class="sxs-lookup"><span data-stu-id="639d9-148">Results</span></span>](#Results)  
  
##  <a name="introduction-page"></a><a name="Introduction"></a> <span data-ttu-id="639d9-149">소개 페이지</span><span class="sxs-lookup"><span data-stu-id="639d9-149">Introduction Page</span></span>  
 <span data-ttu-id="639d9-150">이 페이지에서는 **데이터베이스 배포** 마법사의 단계를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="639d9-150">This page describes the steps for the **Deploy Database** Wizard.</span></span>  
  
 <span data-ttu-id="639d9-151">**Options**</span><span class="sxs-lookup"><span data-stu-id="639d9-151">**Options**</span></span>  
  
-   <span data-ttu-id="639d9-152">**이 페이지를 다시 표시 안 함**</span><span class="sxs-lookup"><span data-stu-id="639d9-152">**Do not show this page again.**</span></span> <span data-ttu-id="639d9-153">- 앞으로 소개 페이지가 표시되지 않도록 하려면 이 확인란을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="639d9-153">- Click the check box to stop the Introduction page from being displayed in the future.</span></span>  
  
-   <span data-ttu-id="639d9-154">**다음** - **배포 설정** 페이지로 진행합니다.</span><span class="sxs-lookup"><span data-stu-id="639d9-154">**Next** - Proceeds to the **Deployment Settings** page.</span></span>  
  
-   <span data-ttu-id="639d9-155">**취소** -작업을 취소 하 고 마법사를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="639d9-155">**Cancel** - Cancels the operation and closes the Wizard.</span></span>  
  
##  <a name="deployment-settings-page"></a><a name="Deployment_settings"></a><span data-ttu-id="639d9-156">배포 설정 페이지</span><span class="sxs-lookup"><span data-stu-id="639d9-156">Deployment Settings Page</span></span>  
 <span data-ttu-id="639d9-157">이 페이지에서는 대상 서버를 지정하고 새 데이터베이스에 대한 세부 정보를 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="639d9-157">Use this page to specify the destination server and to provide details about your new database.</span></span>  
  
 <span data-ttu-id="639d9-158">**로컬 호스트:**</span><span class="sxs-lookup"><span data-stu-id="639d9-158">**Local host:**</span></span>  
  
-   <span data-ttu-id="639d9-159">**서버 연결** – 서버 연결 세부 정보를 지정한 다음, **연결** 을 클릭하여 연결을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="639d9-159">**Server connection** - Specify server connection details and then click **Connect** to verify the connection.</span></span>  
  
-   <span data-ttu-id="639d9-160">**새 데이터베이스 이름** – 새 데이터베이스 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="639d9-160">**New database name** - Specify a name for the new database.</span></span>  
  
 <span data-ttu-id="639d9-161">**[!INCLUDE[ssSDS](../../includes/sssds-md.md)]데이터베이스 설정:**</span><span class="sxs-lookup"><span data-stu-id="639d9-161">**[!INCLUDE[ssSDS](../../includes/sssds-md.md)] database settings:**</span></span>  
  
-   <span data-ttu-id="639d9-162">\*\* [!INCLUDE[ssSDS](../../includes/sssds-md.md)] 버전\*\* - [!INCLUDE[ssSDS](../../includes/sssds-md.md)] 드롭다운 메뉴에서 버전을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="639d9-162">**[!INCLUDE[ssSDS](../../includes/sssds-md.md)] edition** - Select the edition of [!INCLUDE[ssSDS](../../includes/sssds-md.md)] from the drop-down menu.</span></span>  
  
-   <span data-ttu-id="639d9-163">**최대 데이터베이스 크기** – 드롭다운 메뉴에서 최대 데이터베이스 크기를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="639d9-163">**Maximum database size** - Select the maximum database size from the drop-down menu.</span></span>  
  
 <span data-ttu-id="639d9-164">**기타 설정:**</span><span class="sxs-lookup"><span data-stu-id="639d9-164">**Other settings:**</span></span>  
  
-   <span data-ttu-id="639d9-165">BACPAC 아카이브 파일인 임시 파일의 로컬 디렉터리를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="639d9-165">Specify a local directory for the temporary file, which is the BACPAC archive file.</span></span> <span data-ttu-id="639d9-166">지정된 위치에 파일이 만들어지고 작업이 완료된 후에도 해당 위치에 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="639d9-166">Note that the file will be created at the specified location and will remain there after the operation completes.</span></span>  
  
##  <a name="summary-page"></a><a name="Summary"></a> <span data-ttu-id="639d9-167">요약 페이지</span><span class="sxs-lookup"><span data-stu-id="639d9-167">Summary Page</span></span>  
 <span data-ttu-id="639d9-168">이 페이지에서 작업에 대해 지정한 원본 및 대상 설정을 검토할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="639d9-168">Use this page to review the specified source and target settings for the operation.</span></span> <span data-ttu-id="639d9-169">지정한 설정을 사용하여 배포 작업을 완료하려면 **마침**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="639d9-169">To complete the deploy operation using the specified settings, click **Finish**.</span></span> <span data-ttu-id="639d9-170">배포 작업을 취소하고 마법사를 종료하려면 **취소**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="639d9-170">To cancel the deploy operation and exit the Wizard, click **Cancel**.</span></span>  
  
##  <a name="progress-page"></a><a name="Progress"></a> <span data-ttu-id="639d9-171">진행률 페이지</span><span class="sxs-lookup"><span data-stu-id="639d9-171">Progress Page</span></span>  
 <span data-ttu-id="639d9-172">이 페이지에는 작업 상태를 나타내는 진행률 표시줄이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="639d9-172">This page displays a progress bar that indicates the status of the operation.</span></span> <span data-ttu-id="639d9-173">자세한 상태를 보려면 **자세히 보기** 옵션을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="639d9-173">To view detailed status, click the **View details** option.</span></span>  
  
##  <a name="results-page"></a><a name="Results"></a><span data-ttu-id="639d9-174">결과 페이지</span><span class="sxs-lookup"><span data-stu-id="639d9-174">Results Page</span></span>  
 <span data-ttu-id="639d9-175">이 페이지에서는 배포 작업의 성공 또는 실패를 보고하고 각 작업의 결과를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="639d9-175">This page reports the success or failure of the deploy operation, showing the results of each action.</span></span> <span data-ttu-id="639d9-176">오류가 발생한 동작에는 모두 **결과** 열에 링크가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="639d9-176">Any action that encountered an error will have a link in the **Result** column.</span></span> <span data-ttu-id="639d9-177">링크를 클릭하면 해당 동작의 오류에 대한 보고서가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="639d9-177">Click the link to view a report of the error for that action.</span></span>  
  
 <span data-ttu-id="639d9-178">**마침** 을 클릭 하 여 마법사를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="639d9-178">Click **Finish** to close the Wizard.</span></span>  
  
## <a name="using-a-net-framework-application"></a><span data-ttu-id="639d9-179">.Net Framework 애플리케이션 사용</span><span class="sxs-lookup"><span data-stu-id="639d9-179">Using a .Net Framework Application</span></span>  
 <span data-ttu-id="639d9-180">**.Net Framework 애플리케이션에서 DacStoreExport() 및 Import() 메서드를 사용하여 데이터베이스를 배포합니다.**</span><span class="sxs-lookup"><span data-stu-id="639d9-180">**To deploy a database using the DacStoreExport() and Import() methods in a .Net Framework application.**</span></span>  
  
 <span data-ttu-id="639d9-181">코드 예제를 보려면 [Codeplex](https://go.microsoft.com/fwlink/?LinkId=219575)에서 DAC 샘플 애플리케이션을 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="639d9-181">To view a code example, download the DAC sample application on [Codeplex](https://go.microsoft.com/fwlink/?LinkId=219575)</span></span>  
  
1.  <span data-ttu-id="639d9-182">SMO Server 개체를 만든 후 이 개체를 배포할 데이터베이스를 포함하는 인스턴스 또는 서버로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="639d9-182">Create a SMO Server object and set it to the instance or server that contains the database to be deployed.</span></span>  
  
2.  <span data-ttu-id="639d9-183">`ServerConnection` 개체를 열고 동일한 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="639d9-183">Open a `ServerConnection` object and connect to the same instance.</span></span>  
  
3.  <span data-ttu-id="639d9-184">`Export` 형식의 `Microsoft.SqlServer.Management.Dac.DacStore` 메서드를 사용하여 데이터베이스를 BACPAC 파일로 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="639d9-184">Use the `Export` method of the `Microsoft.SqlServer.Management.Dac.DacStore` type to export the database to a BACPAC file.</span></span> <span data-ttu-id="639d9-185">내보낼 데이터베이스의 이름과 BACPAC 파일을 배치할 폴더의 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="639d9-185">Specify the name of the database to be exported, and the path to the folder where the BACPAC file is to be placed.</span></span>  
  
4.  <span data-ttu-id="639d9-186">SMO Server 개체를 만든 다음 대상 인스턴스 또는 서버로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="639d9-186">Create a SMO Server object and set it to the destination instance or server.</span></span>  
  
5.  <span data-ttu-id="639d9-187">`ServerConnection` 개체를 열고 동일한 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="639d9-187">Open a `ServerConnection` object and connect to the same instance.</span></span>  
  
6.  <span data-ttu-id="639d9-188">`Import` 형식의 `Microsoft.SqlServer.Management.Dac.DacStore` 메서드를 사용하여 BACPAC를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="639d9-188">Use the `Import` method of the `Microsoft.SqlServer.Management.Dac.DacStore` type to import the BACPAC.</span></span> <span data-ttu-id="639d9-189">내보내기에 의해 생성되는 BACPAC 파일을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="639d9-189">Specify the BACPAC file created by the export.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="639d9-190">참고 항목</span><span class="sxs-lookup"><span data-stu-id="639d9-190">See Also</span></span>  
 <span data-ttu-id="639d9-191">[데이터 계층 애플리케이션](data-tier-applications.md) </span><span class="sxs-lookup"><span data-stu-id="639d9-191">[Data-tier Applications](data-tier-applications.md) </span></span>  
 <span data-ttu-id="639d9-192">[데이터 계층 응용 프로그램 내보내기](export-a-data-tier-application.md) </span><span class="sxs-lookup"><span data-stu-id="639d9-192">[Export a Data-tier Application](export-a-data-tier-application.md) </span></span>  
 [<span data-ttu-id="639d9-193">BACPAC 파일을 가져와 새 사용자 데이터베이스 만들기</span><span class="sxs-lookup"><span data-stu-id="639d9-193">Import a BACPAC File to Create a New User Database</span></span>](import-a-bacpac-file-to-create-a-new-user-database.md)  
  
  
