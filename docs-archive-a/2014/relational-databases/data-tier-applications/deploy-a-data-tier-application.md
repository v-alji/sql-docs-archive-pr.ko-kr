---
title: 데이터 계층 애플리케이션 배포 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.deploydacwizard.updateconfiguration.f1
- sql12.swb.deploydacwizard.selectdac.f1
- sql12.swb.deploydacwizard.deploydac.f1
- sql12.swb.deploydacwizard.introduction.f1
- sql12.swb.deploydacwizard.summary.f1
helpviewer_keywords:
- Deploy data-tier application
- deploy DAC
- data-tier application [SQL Server], deploy
- How to [DAC], deploy
- wizard [DAC], deploy
ms.assetid: c117af35-aa53-44a5-8034-fa8715dc735f
author: stevestein
ms.author: sstein
ms.openlocfilehash: fd4a09eed946863064728fd8c62230121ad3d403
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740036"
---
# <a name="deploy-a-data-tier-application"></a><span data-ttu-id="c3610-102">데이터 계층 애플리케이션 배포</span><span class="sxs-lookup"><span data-stu-id="c3610-102">Deploy a Data-tier Application</span></span>
  <span data-ttu-id="c3610-103">마법사 또는 PowerShell 스크립트를 사용하여 DAC 패키지의 DAC(데이터 계층 애플리케이션)를 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 또는 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] 의 기존 인스턴스에 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c3610-103">You can deploy a data-tier application (DAC) from a DAC package to an existing instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] or [!INCLUDE[ssSDS](../../includes/sssds-md.md)] by using a wizard or a PowerShell script.</span></span> <span data-ttu-id="c3610-104">배포 프로세스에서는 **msdb** 시스템 데이터베이스(**의** master [!INCLUDE[ssSDS](../../includes/sssds-md.md)])에 DAC 정의를 저장하여 DAC 인스턴스를 등록하고 데이터베이스를 만든 다음 DAC에 정의된 모든 데이터베이스 개체로 데이터베이스를 채웁니다.</span><span class="sxs-lookup"><span data-stu-id="c3610-104">The deployment process registers a DAC instance by storing the DAC definition in the **msdb** system database (**master** in [!INCLUDE[ssSDS](../../includes/sssds-md.md)]), creates a database, and then populates the database with all the database objects defined in the DAC.</span></span>  
  
-   <span data-ttu-id="c3610-105">**시작하기 전 주의 사항:**  [SQL Server 유틸리티](#SQLUtility), [데이터베이스 옵션 및 설정](#DBOptSettings), [제한 사항](#LimitationsRestrictions), [필수 구성 요소](#Prerequisites), [보안](#Security), [사용 권한](#Permissions)</span><span class="sxs-lookup"><span data-stu-id="c3610-105">**Before you begin:**  [SQL Server Utility](#SQLUtility), [Database Options and Settings](#DBOptSettings), [Limitations and Restrictions](#LimitationsRestrictions), [Prerequisites](#Prerequisites), [Security](#Security), [Permissions](#Permissions)</span></span>  
  
-   <span data-ttu-id="c3610-106">**DAC를 배포하려면:**  [데이터 계층 애플리케이션 배포 마법사](#UsingDeployDACWizard), [PowerShell](#DeployDACPowerShell)</span><span class="sxs-lookup"><span data-stu-id="c3610-106">**To deploy a DAC, using:**  [The Deploy Data-tier Application Wizard](#UsingDeployDACWizard), [PowerShell](#DeployDACPowerShell)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeBegin"></a> <span data-ttu-id="c3610-107">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="c3610-107">Before You Begin</span></span>  
 <span data-ttu-id="c3610-108">동일한 DAC 패키지를 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 의 단일 인스턴스에 여러 번 배포할 수 있지만 배포를 한 번에 하나씩만 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3610-108">The same DAC package can be deployed to a single instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] multiple times, however the deployments must be run one at a time.</span></span> <span data-ttu-id="c3610-109">지정된 DAC 인스턴스 이름은 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스 내에서 각 배포마다 고유해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3610-109">The DAC instance name specified for each deployment must be unique within the instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
###  <a name="sql-server-utility"></a><a name="SQLUtility"></a><span data-ttu-id="c3610-110">SQL Server 유틸리티</span><span class="sxs-lookup"><span data-stu-id="c3610-110">SQL Server Utility</span></span>  
 <span data-ttu-id="c3610-111">DAC를 데이터베이스 엔진의 관리되는 인스턴스로 배포하는 경우 배포된 DAC는 유틸리티 컬렉션 집합이 인스턴스에서 유틸리티 제어 지점으로 다음에 전송될 때 SQL Server 유틸리티에 통합됩니다.</span><span class="sxs-lookup"><span data-stu-id="c3610-111">If you deploy a DAC to a managed instance of the Database Engine, the deployed DAC is incorporated into the SQL Server Utility the next time the utility collection set is sent from the instance to the utility control point.</span></span> <span data-ttu-id="c3610-112">그러면 DAC가 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] **유틸리티 탐색기**의 **배포된 데이터 계층 애플리케이션 노드**에 표시되고 **배포된 데이터 계층 애플리케이션** 세부 정보 페이지에 보고됩니다.</span><span class="sxs-lookup"><span data-stu-id="c3610-112">The DAC will then be present in the **Deployed Data-tier Applications** node of the [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] **Utility Explorer** and reported in the **Deployed Data-tier Applications** details page.</span></span>  
  
###  <a name="database-options-and-settings"></a><a name="DBOptSettings"></a><span data-ttu-id="c3610-113">데이터베이스 옵션 및 설정</span><span class="sxs-lookup"><span data-stu-id="c3610-113">Database Options and Settings</span></span>  
 <span data-ttu-id="c3610-114">기본적으로 배포 중에 생성된 데이터베이스에는 다음을 제외한 CREATE DATABASE 문의 모든 기본 설정이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="c3610-114">By default, the database created during the deployment will have all of the default settings from the CREATE DATABASE statement, except:</span></span>  
  
-   <span data-ttu-id="c3610-115">데이터베이스 데이터 정렬 및 호환성 수준은 DAC 패키지에 정의된 값으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="c3610-115">The database collation and compatibility level are set to the values defined in the DAC package.</span></span> <span data-ttu-id="c3610-116">SQL Server Developer Tools에서 데이터베이스 프로젝트를 기반으로 작성된 DAC 패키지는 데이터베이스 프로젝트에 설정된 값을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="c3610-116">A DAC package built from a database project in the SQL Server Developer Tools uses the values set in the database project.</span></span> <span data-ttu-id="c3610-117">기존 데이터베이스에서 추출한 패키지는 기존 데이터베이스의 값을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="c3610-117">A package extracted from an existing database uses the values from the original database.</span></span>  
  
-   <span data-ttu-id="c3610-118">데이터베이스 이름과 파일 경로와 같은 일부 데이터베이스 설정을 **구성 업데이트** 페이지에서 조정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c3610-118">You can adjust some of the database settings, such as database name and file paths, in the **Update Configuration** page.</span></span> <span data-ttu-id="c3610-119">[!INCLUDE[ssSDS](../../includes/sssds-md.md)]에 배포할 때는 파일 경로를 설정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c3610-119">You cannot set the file paths when deploying to [!INCLUDE[ssSDS](../../includes/sssds-md.md)].</span></span>  
  
 <span data-ttu-id="c3610-120">TRUSTWORTHY, DB_CHAINING 및 HONOR_BROKER_PRIORITY와 같은 일부 데이터베이스 옵션은 배포 프로세스 도중 조정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c3610-120">Some database options, such as TRUSTWORTHY, DB_CHAINING, and HONOR_BROKER_PRIORITY, cannot be adjusted as part of the deployment process.</span></span> <span data-ttu-id="c3610-121">파일 그룹의 수, 파일의 수 및 크기와 같은 물리적 속성은 배포 프로세스 도중 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c3610-121">Physical properties, such as the number of filegroups, or the numbers and sizes of files cannot be altered as part of the deployment process.</span></span> <span data-ttu-id="c3610-122">배포가 완료된 후 ALTER DATABASE 문, [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]또는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell을 사용하여 데이터베이스를 맞춤 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c3610-122">After the deployment completes, you can use the ALTER DATABASE statement, [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell to tailor the database.</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="LimitationsRestrictions"></a> <span data-ttu-id="c3610-123">제한 사항</span><span class="sxs-lookup"><span data-stu-id="c3610-123">Limitations and Restrictions</span></span>  
 <span data-ttu-id="c3610-124">[!INCLUDE[ssSDS](../../includes/sssds-md.md)]SP4(서비스 팩 4) 이상을 실행하는 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 또는 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 인스턴스에 DAC를 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c3610-124">A DAC can be deployed to [!INCLUDE[ssSDS](../../includes/sssds-md.md)], or an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] running [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 4 (SP4) or later.</span></span> <span data-ttu-id="c3610-125">이후 버전을 사용하여 DAC를 만드는 경우 DAC에 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]에서 지원되지 않는 개체가 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c3610-125">If you create a DAC using a later version, the DAC may contain objects not supported by [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].</span></span> <span data-ttu-id="c3610-126">이러한 DAC를 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]인스턴스에 배포할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c3610-126">You cannot deploy those DACs to instances of [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="c3610-127">필수 조건</span><span class="sxs-lookup"><span data-stu-id="c3610-127">Prerequisites</span></span>  
 <span data-ttu-id="c3610-128">출처를 알 수 없거나 신뢰할 수 없는 DAC 패키지는 배포하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="c3610-128">We recommend that you do not deploy a DAC package from unknown or untrusted sources.</span></span> <span data-ttu-id="c3610-129">이러한 패키지에 포함된 악성 코드가 의도하지 않은 Transact-SQL 코드를 실행하거나 스키마를 수정하여 오류가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c3610-129">Such packages could contain malicious code that might execute unintended Transact-SQL code or cause errors by modifying the schema.</span></span> <span data-ttu-id="c3610-130">출처를 알 수 없거나 신뢰할 수 없는 패키지를 사용하려면 먼저 DAC의 압축을 풀고 저장 프로시저나 다른 사용자 정의 코드와 같은 코드를 검사하세요.</span><span class="sxs-lookup"><span data-stu-id="c3610-130">Before you use a package from an unknown or untrusted source, unpack the DAC and examine the code, such as stored procedures or other user-defined code.</span></span> <span data-ttu-id="c3610-131">이러한 검사를 수행하는 방법은 [Validate a DAC Package](validate-a-dac-package.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c3610-131">For more information about how to perform these checks, see [Validate a DAC Package](validate-a-dac-package.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="c3610-132">보안</span><span class="sxs-lookup"><span data-stu-id="c3610-132">Security</span></span>  
 <span data-ttu-id="c3610-133">보안을 개선하기 위해 SQL Server 인증 로그인은 암호 없이 DAC 패키지에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="c3610-133">To improve security, SQL Server Authentication logins are stored in a DAC package without a password.</span></span> <span data-ttu-id="c3610-134">패키지가 배포 또는 업그레이드되면 생성된 암호와 함께 비활성 로그인이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="c3610-134">When the package is deployed or upgraded, the login is created as a disabled login with a generated password.</span></span> <span data-ttu-id="c3610-135">로그인을 활성화하려면 ALTER ANY LOGIN 권한이 있는 로그인을 사용하여 로그인하고 ALTER LOGIN을 사용하여 로그인을 활성화하여 사용자에게 알려 줄 수 있는 새 암호를 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="c3610-135">To enable the logins, log in using a login that has ALTER ANY LOGIN permission and use ALTER LOGIN to enable the login and assign a new password that can be communicated to the user.</span></span> <span data-ttu-id="c3610-136">Windows 인증 로그인의 경우 암호가 SQL Server에서 관리되지 않으므로 이 과정이 필요 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c3610-136">This is not needed for Windows Authentication logins because their passwords are not managed by SQL Server.</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="c3610-137">권한</span><span class="sxs-lookup"><span data-stu-id="c3610-137">Permissions</span></span>  
 <span data-ttu-id="c3610-138">**sysadmin** 또는 **serveradmin** 고정 서버 역할의 멤버를 통하거나 **dbcreator** 고정 서버 역할에 포함되고 ALTER ANY LOGIN 권한이 있는 로그인을 통해서만 DAC를 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c3610-138">A DAC can only be deployed by members of the **sysadmin** or **serveradmin** fixed server roles, or by logins that are in the **dbcreator** fixed server role and have ALTER ANY LOGIN permissions.</span></span> <span data-ttu-id="c3610-139">기본 제공 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 시스템 관리자 계정인 **sa** 도 DAC를 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c3610-139">The built-in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system administrator account named **sa** can also deploy a DAC.</span></span> <span data-ttu-id="c3610-140">[!INCLUDE[ssSDS](../../includes/sssds-md.md)] 에 대한 로그인이 있는 DAC를 배포하려면 loginmanager 또는 serveradmin 역할의 멤버 자격이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="c3610-140">Deploying a DAC with logins to [!INCLUDE[ssSDS](../../includes/sssds-md.md)] requires membership in the loginmanager or serveradmin roles.</span></span> <span data-ttu-id="c3610-141">[!INCLUDE[ssSDS](../../includes/sssds-md.md)] 에 대한 로그인이 없는 DAC를 배포하려면 dbmanager 또는 serveradmin 역할의 멤버 자격이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="c3610-141">Deploying a DAC without logins to [!INCLUDE[ssSDS](../../includes/sssds-md.md)] requires membership in the dbmanager or serveradmin roles.</span></span>  
  
##  <a name="using-the-deploy-data-tier-application-wizard"></a><a name="UsingDeployDACWizard"></a><span data-ttu-id="c3610-142">데이터 계층 응용 프로그램 배포 마법사 사용</span><span class="sxs-lookup"><span data-stu-id="c3610-142">Using the Deploy Data-tier Application Wizard</span></span>  
 <span data-ttu-id="c3610-143">**마법사를 사용하여 DAC를 배포하려면**</span><span class="sxs-lookup"><span data-stu-id="c3610-143">**To Deploy a DAC Using a Wizard**</span></span>  
  
1.  <span data-ttu-id="c3610-144">**개체 탐색기**에서 DAC를 배포할 인스턴스에 대한 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="c3610-144">In **Object Explorer**, expand the node for the instance to which you want to deploy the DAC.</span></span>  
  
2.  <span data-ttu-id="c3610-145">**데이터베이스** 노드를 마우스 오른쪽 단추로 클릭한 다음, **데이터 계층 애플리케이션 배포…** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c3610-145">Right-click the **Databases** node, then select **Deploy Data-tier Application...**</span></span>  
  
3.  <span data-ttu-id="c3610-146">마법사 대화 상자를 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="c3610-146">Complete the wizard dialogs:</span></span>  
  
    -   [<span data-ttu-id="c3610-147">소개 페이지</span><span class="sxs-lookup"><span data-stu-id="c3610-147">Introduction Page</span></span>](#Introduction)  
  
    -   [<span data-ttu-id="c3610-148">DAC 패키지 선택 페이지</span><span class="sxs-lookup"><span data-stu-id="c3610-148">Select DAC Package Page</span></span>](#Select_dac_package)  
  
    -   [<span data-ttu-id="c3610-149">정책 검토 페이지</span><span class="sxs-lookup"><span data-stu-id="c3610-149">Review Policy Page</span></span>](#Review_policy)  
  
    -   [<span data-ttu-id="c3610-150">구성 업데이트 페이지</span><span class="sxs-lookup"><span data-stu-id="c3610-150">Update Configuration Page</span></span>](#Update_configuration)  
  
    -   [<span data-ttu-id="c3610-151">요약 페이지</span><span class="sxs-lookup"><span data-stu-id="c3610-151">Summary Page</span></span>](#Summary)  
  
    -   [<span data-ttu-id="c3610-152">배포 페이지</span><span class="sxs-lookup"><span data-stu-id="c3610-152">Deploy Page</span></span>](#Deploy)  
  
##  <a name="introduction-page"></a><a name="Introduction"></a> <span data-ttu-id="c3610-153">소개 페이지</span><span class="sxs-lookup"><span data-stu-id="c3610-153">Introduction Page</span></span>  
 <span data-ttu-id="c3610-154">이 페이지에서는 데이터 계층 애플리케이션을 배포하는 단계에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="c3610-154">This page describes the steps for deploying a data-tier application.</span></span>  
  
 <span data-ttu-id="c3610-155">**이 페이지를 다시 표시 안 함**</span><span class="sxs-lookup"><span data-stu-id="c3610-155">**Do not show this page again.**</span></span> <span data-ttu-id="c3610-156">- 앞으로 이 페이지가 표시되지 않도록 하려면 이 확인란을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c3610-156">- Click the check box to stop the page from being displayed in the future.</span></span>  
  
 <span data-ttu-id="c3610-157">**다음 >** - **DAC 패키지 선택** 페이지로 진행합니다.</span><span class="sxs-lookup"><span data-stu-id="c3610-157">**Next >** - Proceeds to the **Select DAC Package** page.</span></span>  
  
 <span data-ttu-id="c3610-158">**취소** - DAC를 배포하지 않고 마법사를 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="c3610-158">**Cancel** - Terminates the wizard without deploying a DAC.</span></span>  
  
##  <a name="select-dac-package-page"></a><a name="Select_dac_package"></a><span data-ttu-id="c3610-159">DAC 패키지 선택 페이지</span><span class="sxs-lookup"><span data-stu-id="c3610-159">Select DAC Package Page</span></span>  
 <span data-ttu-id="c3610-160">이 페이지를 사용하여 배포할 데이터 계층 애플리케이션을 포함하는 DAC 패키지를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c3610-160">Use this page to specify the DAC package that contains the data-tier application to be deployed.</span></span> <span data-ttu-id="c3610-161">이 페이지는 세 가지 상태로 전환됩니다.</span><span class="sxs-lookup"><span data-stu-id="c3610-161">The page transitions through three states.</span></span>  
  
### <a name="select-the-dac-package"></a><span data-ttu-id="c3610-162">DAC 패키지 선택</span><span class="sxs-lookup"><span data-stu-id="c3610-162">Select the DAC Package</span></span>  
 <span data-ttu-id="c3610-163">이 페이지의 초기 상태를 사용하여 배포할 DAC 패키지를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c3610-163">Use the initial state of the page to choose the DAC package to deploy.</span></span> <span data-ttu-id="c3610-164">DAC 패키지는 유효한 DAC 패키지 파일이어야 하며 확장자가 .dacpac여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3610-164">The DAC package must be a valid DAC package file and must have a .dacpac extension.</span></span>  
  
 <span data-ttu-id="c3610-165">**DAC 패키지** - 배포할 데이터 계층 애플리케이션이 포함된 DAC 패키지의 경로와 파일 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c3610-165">**DAC Package** - Specify the path and file name of the DAC package that contains the data-tier application to be deployed.</span></span> <span data-ttu-id="c3610-166">입력란 오른쪽의 **찾아보기** 단추를 선택하여 DAC 패키지의 위치를 찾아볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c3610-166">You can select the **Browse** button at the right of the box to browse to the location of the DAC package.</span></span>  
  
 <span data-ttu-id="c3610-167">**애플리케이션 이름** - DAC를 만들거나 데이터베이스에서 추출할 때 할당된 DAC 이름을 표시하는 읽기 전용 입력란입니다.</span><span class="sxs-lookup"><span data-stu-id="c3610-167">**Application Name** - A read-only box that displays the DAC name assigned when the DAC was authored or extracted from a database.</span></span>  
  
 <span data-ttu-id="c3610-168">**버전** - DAC를 만들거나 데이터베이스에서 추출할 때 할당된 버전을 표시하는 읽기 전용 입력란입니다.</span><span class="sxs-lookup"><span data-stu-id="c3610-168">**Version** - A read-only box that displays the version assigned when the DAC was authored or extracted from a database.</span></span>  
  
 <span data-ttu-id="c3610-169">**설명** - DAC를 만들거나 데이터베이스에서 추출할 때 작성된 설명을 표시하는 읽기 전용 입력란입니다.</span><span class="sxs-lookup"><span data-stu-id="c3610-169">**Description** - A read-only box that displays the description written when the DAC was authored or extracted from a database.</span></span>  
  
 <span data-ttu-id="c3610-170">\*\* \< 이전\*\* - **소개** 페이지로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="c3610-170">**\< Previous** - Returns to the **Introduction** page.</span></span>  
  
 <span data-ttu-id="c3610-171">**다음 >** - 선택한 파일이 유효한 DAC 패키지인지 마법사에서 확인하는 동안 진행률 표시줄이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c3610-171">**Next >** - Displays a progress bar as the wizard confirms that the selected file is a valid DAC package.</span></span>  
  
 <span data-ttu-id="c3610-172">**취소** - DAC를 배포하지 않고 마법사를 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="c3610-172">**Cancel** - Terminates the wizard without deploying the DAC.</span></span>  
  
### <a name="validating-the-dac-package"></a><span data-ttu-id="c3610-173">DAC 패키지 유효성 검사</span><span class="sxs-lookup"><span data-stu-id="c3610-173">Validating the DAC Package</span></span>  
 <span data-ttu-id="c3610-174">선택한 파일이 유효한 DAC 패키지인지 마법사에서 확인하는 동안 진행률 표시줄이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c3610-174">Displays a progress bar as the wizard confirms that the selected file is a valid DAC package.</span></span> <span data-ttu-id="c3610-175">DAC 패키지의 유효성이 확인되면 마법사는 유효성 검사 결과를 검토할 수 있는 **패키지 선택** 페이지의 최종 버전으로 진행합니다.</span><span class="sxs-lookup"><span data-stu-id="c3610-175">If the DAC package is validated, the wizard proceeds to the final version of the **Select Package** page where you can review the results of the validation.</span></span> <span data-ttu-id="c3610-176">파일이 유효한 DAC 패키지가 아닌 경우 마법사는 **DAC 패키지 선택**상태로 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="c3610-176">If the file is not a valid DAC package, the wizard remains on the **Select DAC Package**.</span></span> <span data-ttu-id="c3610-177">이 경우 다른 유효한 DAC 패키지를 선택하거나 마법사를 취소하고 새 DAC 패키지를 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c3610-177">Either select another valid DAC package or cancel the wizard and generate a new DAC package.</span></span>  
  
 <span data-ttu-id="c3610-178">**DAC 내용의 유효성을 검사하고 있습니다** - 유효성 검사의 현재 상태를 보고하는 진행률 표시줄입니다.</span><span class="sxs-lookup"><span data-stu-id="c3610-178">**Validating the contents of the DAC** - The progress bar that reports the current status of the validation process.</span></span>  
  
 <span data-ttu-id="c3610-179">\*\* \< 이전\*\* - **패키지 선택** 페이지의 초기 상태로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="c3610-179">**\< Previous** - Returns to the initial state of the **Select Package** page.</span></span>  
  
 <span data-ttu-id="c3610-180">**다음 >** - **패키지 선택** 페이지의 최종 버전으로 진행합니다.</span><span class="sxs-lookup"><span data-stu-id="c3610-180">**Next >** - Proceeds to the final version of the **Select Package** page.</span></span>  
  
 <span data-ttu-id="c3610-181">**취소** - DAC를 배포하지 않고 마법사를 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="c3610-181">**Cancel** - Terminates the wizard without deploying the DAC.</span></span>  
  
##  <a name="review-policy-page"></a><a name="Review_policy"></a><span data-ttu-id="c3610-182">정책 검토 페이지</span><span class="sxs-lookup"><span data-stu-id="c3610-182">Review Policy Page</span></span>  
 <span data-ttu-id="c3610-183">DAC에 정책이 있는 경우 이 페이지를 사용하여 DAC 서버 선택 정책을 평가한 결과를 검토할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c3610-183">Use this page to review the results of evaluating the DAC server selection policy, if the DAC has a policy.</span></span> <span data-ttu-id="c3610-184">DAC 서버 선택 정책은 선택적이며 Visual Studio에서 DAC를 만들면 여기에 할당됩니다.</span><span class="sxs-lookup"><span data-stu-id="c3610-184">The DAC server selection policy is optional, and is assigned to the DAC when it is created in Visual Studio.</span></span> <span data-ttu-id="c3610-185">정책에서는 서버 선택 정책 패싯을 사용하여 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 인스턴스가 DAC를 호스팅하기 위해 충족해야 하는 조건을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c3610-185">The policy uses the server selection policy facets to specify conditions an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] should meet to host the DAC.</span></span>  
  
 <span data-ttu-id="c3610-186">**정책 조건의 평가 결과** - DAC 배포 정책의 조건이 성공했는지 보여 주는 읽기 전용 보고서입니다.</span><span class="sxs-lookup"><span data-stu-id="c3610-186">**Evaluation results of policy conditions** - A read-only report showing whether the conditions of the DAC deployment policy succeeded.</span></span> <span data-ttu-id="c3610-187">각 조건을 평가한 결과가 별도의 행에 보고됩니다.</span><span class="sxs-lookup"><span data-stu-id="c3610-187">The results of evaluating each condition are reported on a separate line.</span></span>  
  
 <span data-ttu-id="c3610-188">DAC를 [!INCLUDE[ssSDS](../../includes/sssds-md.md)]에 배포하는 경우 운영 체제 버전, 언어, 명명된 파이프 설정, 플랫폼, tcp 설정 등의 서버 선택 정책을 평가한 결과가 항상 false입니다.</span><span class="sxs-lookup"><span data-stu-id="c3610-188">The following server selection policies always evaluate to false when deploying a DAC to [!INCLUDE[ssSDS](../../includes/sssds-md.md)]: operating system version, language, named pipes enabled, platform, and tcp enabled.</span></span>  
  
 <span data-ttu-id="c3610-189">**정책 위반을 무시합니다.** - 정책 조건이 한 개 이상 위반되더라도 배포를 진행하려면 이 확인란을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="c3610-189">**Ignore policy violations** - Use this check box to proceed with the deployment if one or more of the policy conditions failed.</span></span> <span data-ttu-id="c3610-190">실패한 모든 조건이 DAC 작동에 영향을 주지 않는 것이 확실한 경우에만 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c3610-190">Only select this option if you are sure that all of the conditions which failed will not prevent the successful operation of the DAC.</span></span>  
  
 <span data-ttu-id="c3610-191">\*\* \< 이전\*\* - **패키지 선택** 페이지로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="c3610-191">**\< Previous** - Returns to the **Select Package** page.</span></span>  
  
 <span data-ttu-id="c3610-192">**다음 >** - **구성 업데이트** 페이지로 진행합니다.</span><span class="sxs-lookup"><span data-stu-id="c3610-192">**Next >** - Proceeds to the **Update Configureation** page.</span></span>  
  
 <span data-ttu-id="c3610-193">**취소** - DAC를 배포하지 않고 마법사를 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="c3610-193">**Cancel** - Terminates the wizard without deploying the DAC.</span></span>  
  
##  <a name="update-configuration-page"></a><a name="Update_configuration"></a><span data-ttu-id="c3610-194">구성 업데이트 페이지</span><span class="sxs-lookup"><span data-stu-id="c3610-194">Update Configuration Page</span></span>  
 <span data-ttu-id="c3610-195">이 페이지를 사용하여 배포된 DAC 인스턴스와 배포를 통해 생성된 데이터베이스의 이름을 지정하고 데이터베이스 옵션을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c3610-195">Use this page to specify the names of the deployed DAC instance and the database created by the deployment, and to set database options.</span></span>  
  
 <span data-ttu-id="c3610-196">**데이터베이스 이름:** - 배포를 통해 생성된 데이터베이스의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c3610-196">**Database Name:** - Specify the name of the database to be created by the deployment.</span></span> <span data-ttu-id="c3610-197">기본은 DAC가 추출된 원본 데이터베이스 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="c3610-197">The default is the name of the source database the DAC was extracted from.</span></span> <span data-ttu-id="c3610-198">이름은 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 인스턴스 내에서 고유해야 하며 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 식별자 규칙을 준수해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3610-198">The name must be unique within the instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] and comply with the rules for [!INCLUDE[ssDE](../../includes/ssde-md.md)] identifiers.</span></span>  
  
 <span data-ttu-id="c3610-199">데이터베이스 이름을 변경하면 새 값에 맞게 데이터 파일과 로그 파일의 이름이 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="c3610-199">If you change the database name, the names of the data file and log files will change to match the new value.</span></span>  
  
 <span data-ttu-id="c3610-200">데이터베이스 이름은 DAC 인스턴스 이름에도 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="c3610-200">The database name is also used as the name of the DAC instance.</span></span> <span data-ttu-id="c3610-201">인스턴스 이름은 **개체 탐색기** 의 **데이터 계층 애플리케이션**노드 아래에 있는 DAC에 대한 노드나 **유틸리티 탐색기** 의 **배포된 데이터 계층 애플리케이션**노드에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c3610-201">The instance name is displayed on the node for the DAC under the **Data-tier Applications** node in **Object Explorer**, or the **Deployed Data-tier Applications** node in the **Utility Explorer**.</span></span>  
  
 <span data-ttu-id="c3610-202">다음 옵션은 [!INCLUDE[ssSDS](../../includes/sssds-md.md)]에는 적용되지 않으며 [!INCLUDE[ssSDS](../../includes/sssds-md.md)]에 배포할 때는 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c3610-202">The following options do not apply to [!INCLUDE[ssSDS](../../includes/sssds-md.md)], and are not displayed when deploying to [!INCLUDE[ssSDS](../../includes/sssds-md.md)].</span></span>  
  
 <span data-ttu-id="c3610-203">**기본 데이터베이스 위치 사용** - [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 대한 기본 위치에 데이터베이스 파일과 로그 파일을 생성하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c3610-203">**Use the default database location** - Select this option to create the database data and log files in the default location for the instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span> <span data-ttu-id="c3610-204">파일 이름은 데이터베이스 이름을 사용하여 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="c3610-204">The file names will be built using the database name.</span></span>  
  
 <span data-ttu-id="c3610-205">**데이터베이스 파일 지정** - 데이터와 로그 파일의 다른 위치나 이름을 지정하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c3610-205">**Specify database files** - Select this option to specify a different location or name for the data and log files.</span></span>  
  
 <span data-ttu-id="c3610-206">**데이터 파일 경로 및 이름: -** 데이터 파일의 전체 경로와 파일 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c3610-206">**Data file path and name: -** Specify the full path and file name for the data file.</span></span> <span data-ttu-id="c3610-207">입력란은 기본 경로와 파일 이름으로 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="c3610-207">The box is populated with the default path and file name.</span></span> <span data-ttu-id="c3610-208">입력란의 문자열을 편집하여 기본값을 변경하거나 찾아보기 단추를 사용하여 데이터 파일이 있는 폴더를 탐색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c3610-208">Edit the string in the box to change the default, or use the Browse button to navigate to the folder where the data file is to be placed.</span></span>  
  
 <span data-ttu-id="c3610-209">**로그 파일 경로 및 이름:** - 로그 파일의 전체 경로와 파일 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c3610-209">**Log file path and name:** - Specify the full path and file name for the log file.</span></span> <span data-ttu-id="c3610-210">입력란은 기본 경로와 파일 이름으로 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="c3610-210">The box is populated with the default path and file name.</span></span> <span data-ttu-id="c3610-211">입력란의 문자열을 편집하여 기본값을 변경하거나 **찾아보기** 단추를 사용하여 로그 파일이 있는 폴더를 탐색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c3610-211">Edit the string in the box to change the default, or use the **Browse** button to navigate to the folder where the log file is to be placed.</span></span>  
  
 <span data-ttu-id="c3610-212">\*\* \< 이전\*\* - **DAC 패키지 선택** 페이지로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="c3610-212">**\< Previous** - Returns to the **Select DAC Package** page.</span></span>  
  
 <span data-ttu-id="c3610-213">**다음 >** - **요약** 페이지로 진행합니다.</span><span class="sxs-lookup"><span data-stu-id="c3610-213">**Next >** - Proceeds to the **Summary** page.</span></span>  
  
 <span data-ttu-id="c3610-214">**취소** - DAC를 배포하지 않고 마법사를 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="c3610-214">**Cancel** - Terminates the wizard without deploying the DAC.</span></span>  
  
##  <a name="summary-page"></a><a name="Summary"></a> <span data-ttu-id="c3610-215">요약 페이지</span><span class="sxs-lookup"><span data-stu-id="c3610-215">Summary Page</span></span>  
 <span data-ttu-id="c3610-216">이 페이지를 사용하여 DAC를 배포할 때 마법사가 수행할 동작을 검토할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c3610-216">Use this page to review the actions the wizard will take when deploying the DAC.</span></span>  
  
 <span data-ttu-id="c3610-217">**DAC를 배포하는 데 사용되는 설정은 다음과 같습니다.**</span><span class="sxs-lookup"><span data-stu-id="c3610-217">**The following settings will be used to deploy your DAC.**</span></span> <span data-ttu-id="c3610-218">- 표시된 정보를 검토하여 수행할 동작이 올바른지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="c3610-218">- Review the information displayed to ensure the actions taken will be correct.</span></span> <span data-ttu-id="c3610-219">창에는 선택한 DAC 패키지와 배포하도록 선택한 DAC 인스턴스 이름이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c3610-219">The window displays the DAC package you selected, and the name you selected for the deployed DAC instance.</span></span> <span data-ttu-id="c3610-220">창에는 DAC와 연결된 데이터베이스를 만들 때 사용되는 설정도 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c3610-220">The window also displays the settings that will be used when creating the database associated with the DAC.</span></span>  
  
 <span data-ttu-id="c3610-221">\*\* \< 이전\*\* - **구성 업데이트** 페이지로 돌아가 선택 항목을 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3610-221">**\< Previous** - Returns you to the **Update Configuration** page to change your selections.</span></span>  
  
 <span data-ttu-id="c3610-222">**다음 >** - DAC를 배포하고 **DAC 배포** 페이지에 결과를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="c3610-222">**Next >** - Deploys the DAC and displays the results in the **Deploy DAC** page.</span></span>  
  
 <span data-ttu-id="c3610-223">**취소** - DAC를 배포하지 않고 마법사를 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="c3610-223">**Cancel** - Terminates the wizard without deploying the DAC.</span></span>  
  
##  <a name="deploy-page"></a><a name="Deploy"></a><span data-ttu-id="c3610-224">배포 페이지</span><span class="sxs-lookup"><span data-stu-id="c3610-224">Deploy Page</span></span>  
 <span data-ttu-id="c3610-225">이 페이지에서는 배포 작업의 성공 또는 실패를 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="c3610-225">This page reports the success or failure of the deploy operation.</span></span>  
  
 <span data-ttu-id="c3610-226">**DAC를 배포하는 중** - DAC를 배포하기 위해 수행한 각 동작의 성공 또는 실패를 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="c3610-226">**Deploying the DAC** - Reports the success or failure of each action taken to deploy the DAC.</span></span> <span data-ttu-id="c3610-227">정보를 검토하여 각 동작의 성공 또는 실패를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="c3610-227">Review the information to determine the success or failure of each action.</span></span> <span data-ttu-id="c3610-228">오류가 발생한 동작에는 모두 **결과** 열에 링크가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c3610-228">Any action that encountered an error will have a link in the **Result** column.</span></span> <span data-ttu-id="c3610-229">링크를 선택하면 해당 동작의 오류에 대한 보고서가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c3610-229">Select the link to view a report of the error for that action.</span></span>  
  
 <span data-ttu-id="c3610-230">**보고서 저장** - 배포 보고서를 HTML 파일로 저장하려면 이 단추를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c3610-230">**Save Report** - Select this button to save the deployment report to an HTML file.</span></span> <span data-ttu-id="c3610-231">파일은 모든 동작에서 생성된 모든 오류를 비롯하여 각 동작의 상태를 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="c3610-231">The file reports the status of each action, including all errors generated by any of the actions.</span></span> <span data-ttu-id="c3610-232">기본 폴더는 Windows 계정의 Documents 폴더에 있는 SQL Server Management Studio\DAC Packages 폴더입니다.</span><span class="sxs-lookup"><span data-stu-id="c3610-232">The default folder is the SQL Server Management Studio\DAC Packages folder in the Documents folder of your Windows account.</span></span>  
  
 <span data-ttu-id="c3610-233">**마침** - 마법사를 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="c3610-233">**Finish** - Terminates the wizard.</span></span>  
  
##  <a name="using-powershell"></a><a name="DeployDACPowerShell"></a> <span data-ttu-id="c3610-234">PowerShell 사용</span><span class="sxs-lookup"><span data-stu-id="c3610-234">Using PowerShell</span></span>  
 <span data-ttu-id="c3610-235">**PowerShell 스크립트에서 Install() 메서드를 사용하여 DAC를 배포하려면**</span><span class="sxs-lookup"><span data-stu-id="c3610-235">**To deploy a DAC using the Install() method in a PowerShell script**</span></span>  
  
1.  <span data-ttu-id="c3610-236">SMO Server 개체를 만든 다음 DAC를 배포할 인스턴스로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="c3610-236">Create a SMO Server object and set it to the instance to which you want to deploy the DAC.</span></span>  
  
2.  <span data-ttu-id="c3610-237">`ServerConnection` 개체를 열고 동일한 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="c3610-237">Open a `ServerConnection` object and connect to the same instance.</span></span>  
  
3.  <span data-ttu-id="c3610-238">`System.IO.File`을 사용하여 DAC 패키지 파일을 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="c3610-238">Use `System.IO.File` to load the DAC package file.</span></span>  
  
4.  <span data-ttu-id="c3610-239">`add_DacActionStarted` 및 `add_DacActionFinished`를 사용하여 DAC 배포 이벤트에 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="c3610-239">Use `add_DacActionStarted` and `add_DacActionFinished` to subscribe to the DAC deployment events.</span></span>  
  
5.  <span data-ttu-id="c3610-240">`DatabaseDeploymentProperties`를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="c3610-240">Set the `DatabaseDeploymentProperties`.</span></span>  
  
6.  <span data-ttu-id="c3610-241">`DacStore.Install` 메서드를 사용하여 DAC를 배포합니다.</span><span class="sxs-lookup"><span data-stu-id="c3610-241">Use the `DacStore.Install` method to deploy the DAC.</span></span>  
  
7.  <span data-ttu-id="c3610-242">DAC 패키지 파일을 읽는 데 사용되는 파일 스트림을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="c3610-242">Close the file stream used to read the DAC package file.</span></span>  
  
### <a name="example-powershell"></a><span data-ttu-id="c3610-243">예제(PowerShell)</span><span class="sxs-lookup"><span data-stu-id="c3610-243">Example (PowerShell)</span></span>  
 <span data-ttu-id="c3610-244">다음 예에서는 MyApplication.dacpac 패키지의 DAC 정의를 사용하여 [!INCLUDE[ssDE](../../includes/ssde-md.md)]의 기본 인스턴스에서 MyApplication이라는 DAC를 배포합니다.</span><span class="sxs-lookup"><span data-stu-id="c3610-244">The following example deploys a DAC named MyApplication on a default instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)], using a DAC definition from a MyApplication.dacpac package.</span></span>  
  
```powershell
## Set a SMO Server object to the default instance on the local computer.  
CD SQLSERVER:\SQL\localhost\DEFAULT  
$srv = Get-Item .  
  
## Open a Common.ServerConnection to the same instance.  
$serverconnection = New-Object Microsoft.SqlServer.Management.Common.ServerConnection($srv.ConnectionContext.SqlConnectionObject)  
$serverconnection.Connect()  
$dacstore = New-Object Microsoft.SqlServer.Management.Dac.DacStore($serverconnection)  
  
## Load the DAC package file.  
$dacpacPath = "C:\MyDACs\MyApplication.dacpac"  
$fileStream = [System.IO.File]::Open($dacpacPath,[System.IO.FileMode]::OpenOrCreate)  
$dacType = [Microsoft.SqlServer.Management.Dac.DacType]::Load($fileStream)  
  
## Subscribe to the DAC deployment events.  
$dacstore.add_DacActionStarted({Write-Host `n`nStarting at $(get-date) :: $_.Description})  
$dacstore.add_DacActionFinished({Write-Host Completed at $(get-date) :: $_.Description})  
  
## Deploy the DAC and create the database.  
$dacName  = "MyApplication"  
$evaluateTSPolicy = $true  
$deployProperties = New-Object Microsoft.SqlServer.Management.Dac.DatabaseDeploymentProperties($serverconnection,$dacName)  
$dacstore.Install($dacType, $deployProperties, $evaluateTSPolicy)  
$fileStream.Close()  
```  
  
## <a name="see-also"></a><span data-ttu-id="c3610-245">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c3610-245">See Also</span></span>  
 <span data-ttu-id="c3610-246">[데이터 계층 애플리케이션](data-tier-applications.md) </span><span class="sxs-lookup"><span data-stu-id="c3610-246">[Data-tier Applications](data-tier-applications.md) </span></span>  
 <span data-ttu-id="c3610-247">[데이터베이스에서 DAC 추출](extract-a-dac-from-a-database.md) </span><span class="sxs-lookup"><span data-stu-id="c3610-247">[Extract a DAC From a Database](extract-a-dac-from-a-database.md) </span></span>  
 [<span data-ttu-id="c3610-248">데이터베이스 식별자</span><span class="sxs-lookup"><span data-stu-id="c3610-248">Database Identifiers</span></span>](../databases/database-identifiers.md)  
