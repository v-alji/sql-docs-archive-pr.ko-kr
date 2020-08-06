---
title: SharePoint 2013에 대 한 SharePoint 모드 설치 Reporting Services | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: b29d0f45-0068-4c84-bd7e-5b8a9cd1b538
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 9190f990503a66a088351323effa6c17695f9757
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661506"
---
# <a name="install-reporting-services-sharepoint-mode-for-sharepoint-2013"></a><span data-ttu-id="1dfe7-102">Install Reporting Services SharePoint Mode for SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="1dfe7-102">Install Reporting Services SharePoint Mode for SharePoint 2013</span></span>
  <span data-ttu-id="1dfe7-103">이 항목의 절차에서는 SharePoint 배포 모드에서 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 의 단일 서버 설치 과정을 안내합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-103">The procedures in this topic guide you through a single server installation of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in SharePoint mode.</span></span> <span data-ttu-id="1dfe7-104">이 단계에는 SharePoint 중앙 관리를 사용하는 구성 태스크 및 SQL Server 설치 마법사의 실행이 포합됩니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-104">The steps include running the SQL Server installation wizard as well as configuration tasks that use SharePoint Central Administration.</span></span> <span data-ttu-id="1dfe7-105">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 서비스 애플리케이션을 만드는 등 기존 설치를 업데이트하는 개별 절차에 이 항목을 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-105">The topic can also be used for individual procedures for updating an existing installation, for example to create a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service application.</span></span>  
  
||  
|-|  
|<span data-ttu-id="1dfe7-106">**[!INCLUDE[applies](../../includes/applies-md.md)]** SharePoint 2013 &#124; **참고:** sharepoint [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 모드에서는 sharepoint 서버 다중 테 넌 트를 지원 **하지** 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-106">**[!INCLUDE[applies](../../includes/applies-md.md)]**  SharePoint 2013 &#124; **Note:** [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint mode does **not** support SharePoint Server multi-tenancy.</span></span>|  
  
 <span data-ttu-id="1dfe7-107">기존 팜에 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 서버를 추가하는 방법은 다음을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-107">For information on adding more [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] servers to an existing farm, see the following:</span></span>  
  
-   [<span data-ttu-id="1dfe7-108">팜에 추가 보고서 서버 추가&#40;SSRS 확장&#41;</span><span class="sxs-lookup"><span data-stu-id="1dfe7-108">Add an Additional Report Server to a Farm &#40;SSRS Scale-out&#41;</span></span>](../../reporting-services/install-windows/add-an-additional-report-server-to-a-farm-ssrs-scale-out.md)  
  
-   [<span data-ttu-id="1dfe7-109">팜에 추가 Reporting Services 웹 프런트 엔드 추가</span><span class="sxs-lookup"><span data-stu-id="1dfe7-109">Add an Additional Reporting Services Web Front-end to a Farm</span></span>](../../reporting-services/install-windows/add-an-additional-reporting-services-web-front-end-to-a-farm.md)  
  
 <span data-ttu-id="1dfe7-110">단일 서버 설치는 개발 및 테스트 시나리오에 유용하지만 프로덕션 환경에서는 권장되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-110">A single server installation is useful for development and testing scenarios but it is not recommended for production environments.</span></span>  
  
 <span data-ttu-id="1dfe7-111">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="1dfe7-111">**In this topic:**</span></span>  
  
-   [<span data-ttu-id="1dfe7-112">단일 서버 배포 예</span><span class="sxs-lookup"><span data-stu-id="1dfe7-112">Example Single-Server Deployment</span></span>](#bkmk_singleserver)  
  
-   [<span data-ttu-id="1dfe7-113">설치 계정</span><span class="sxs-lookup"><span data-stu-id="1dfe7-113">Setup accounts</span></span>](#bkmk_setupaccounts)  
  
-   [<span data-ttu-id="1dfe7-114">1단계: SharePoint 모드에서 Reporting Services 보고서 서버 설치</span><span class="sxs-lookup"><span data-stu-id="1dfe7-114">Step 1: Install Reporting Services Report Server in SharePoint mode</span></span>](#bkmk_install_SSRS)  
  
-   [<span data-ttu-id="1dfe7-115">2 단계: Reporting Services SharePoint 서비스 등록 및 시작</span><span class="sxs-lookup"><span data-stu-id="1dfe7-115">Step 2: Register and Start the Reporting Services SharePoint Service</span></span>](#bkmk_install_SSRS_sharedservice)  
  
-   [<span data-ttu-id="1dfe7-116">3 단계: Reporting Services 서비스 응용 프로그램 만들기</span><span class="sxs-lookup"><span data-stu-id="1dfe7-116">Step 3: Create a Reporting Services Service Application</span></span>](#bkmk_create_serrviceapplication)  
  
-   [<span data-ttu-id="1dfe7-117">4 단계: 파워 뷰 사이트 모음 기능을 활성화 합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-117">Step 4: Activate the Power View Site Collection Feature.</span></span>](#bkmk_powerview)  
  
-   [<span data-ttu-id="1dfe7-118">1-4 단계에 대 한 Windows PowerShell 스크립트</span><span class="sxs-lookup"><span data-stu-id="1dfe7-118">Windows PowerShell script for Steps 1-4</span></span>](#bkmk_full_script)  
  
-   <span data-ttu-id="1dfe7-119">[Additional Configuration](#bkmk_additional_config) 에는 구독과 경고에 대한 프로비전, [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 콘텐츠 형식 및 Analysis Services 서버 사용을 위한 Excel Services 구성이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-119">[Additional Configuration](#bkmk_additional_config) including provisioning for subscriptions and alerts, [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] content types, and configuring Excel Services to Use an Analysis Services Server.</span></span>  
  
-   [<span data-ttu-id="1dfe7-120">설치 확인</span><span class="sxs-lookup"><span data-stu-id="1dfe7-120">Verify the installation</span></span>](#bkmk_verify_installation)  
  
##  <a name="example-single-server-deployment"></a><a name="bkmk_singleserver"></a> <span data-ttu-id="1dfe7-121">단일 서버 배포 예</span><span class="sxs-lookup"><span data-stu-id="1dfe7-121">Example Single-Server Deployment</span></span>  
 <span data-ttu-id="1dfe7-122">단일 서버 설치는 개발 및 테스트 시나리오에 유용하지만 프로덕션 환경에서 단일 서버는 권장되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-122">A single-server installation is useful for development and testing scenarios but a single-server is not recommended for a production environment.</span></span> <span data-ttu-id="1dfe7-123">단일 서버 환경은 같은 컴퓨터에 SharePoint 및 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 구성 요소가 설치된 단일 컴퓨터를 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-123">The single-server environment refers to a single computer that has SharePoint and [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] components installed on the same computer.</span></span> <span data-ttu-id="1dfe7-124">이 항목에서는 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 서버가 여러 대인 확장을 다루지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-124">The topic does not cover scale-out with multiple [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] servers.</span></span>  
  
 <span data-ttu-id="1dfe7-125">다음 다이어그램에서는 단일 서버 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 배포의 일부인 구성 요소를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-125">The following diagram illustrates the components that are part of a single server [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] deployment.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1dfe7-126">**(1**</span><span class="sxs-lookup"><span data-stu-id="1dfe7-126">**(1)**</span></span>|<span data-ttu-id="1dfe7-127">SQL Server와 함께 설치되는 SharePoint 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-127">SharePoint service installed from SQL Server installation.</span></span> <span data-ttu-id="1dfe7-128">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 서비스 애플리케이션을 하나 이상 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-128">You can create one or more [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service applications.</span></span>|  
|<span data-ttu-id="1dfe7-129">**fs**</span><span class="sxs-lookup"><span data-stu-id="1dfe7-129">**(2)**</span></span>|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="1dfe7-130">추가 기능(SharePoint 제품용)은 SharePoint Server에 사용자 인터페이스 구성 요소를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-130">add-in for SharePoint products provides the user interface components on the SharePoint Servers.</span></span>|  
|<span data-ttu-id="1dfe7-131">**3**</span><span class="sxs-lookup"><span data-stu-id="1dfe7-131">**(3)**</span></span>|<span data-ttu-id="1dfe7-132">Excel Services 애플리케이션은 Power View 및 PowerPivot에서 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-132">The Excel Service Application used by Power View and PowerPivot.</span></span>|  
|<span data-ttu-id="1dfe7-133">**3-4**</span><span class="sxs-lookup"><span data-stu-id="1dfe7-133">**(4)**</span></span>|<span data-ttu-id="1dfe7-134">PowerPivot 서비스 애플리케이션입니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-134">PowerPivot service application.</span></span>|  
  
 <span data-ttu-id="1dfe7-135">![SSRS SharePoint 모드 단일 서버 배포](../../../2014/sql-server/install/media/rs-sharepoint-1server-deployment.gif "SSRS SharePoint 모드 단일 서버 배포")</span><span class="sxs-lookup"><span data-stu-id="1dfe7-135">![SSRS SharePoint Mode Single Server Deployment](../../../2014/sql-server/install/media/rs-sharepoint-1server-deployment.gif "SSRS SharePoint Mode Single Server Deployment")</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="1dfe7-136"> 더 복잡한 배포 예는 [Deployment Topologies for SQL Server BI Features in SharePoint](deployment-topologies-for-sql-server-bi-features-in-sharepoint.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-136">For more complex deployment examples, see [Deployment Topologies for SQL Server BI Features in SharePoint](deployment-topologies-for-sql-server-bi-features-in-sharepoint.md).</span></span>  
  
##  <a name="setup-accounts"></a><a name="bkmk_setupaccounts"></a><span data-ttu-id="1dfe7-137">설치 계정</span><span class="sxs-lookup"><span data-stu-id="1dfe7-137">Setup accounts</span></span>  
 <span data-ttu-id="1dfe7-138">이 세션에서는 SharePoint 모드에서 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 의 기본 배포 단계에 사용된 계정 및 권한에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-138">This section describes the accounts and permissions used for the primary deployment steps of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in SharePoint mode.</span></span>  
  
 <span data-ttu-id="1dfe7-139">**[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 서비스의 설치 및 등록:**</span><span class="sxs-lookup"><span data-stu-id="1dfe7-139">**Installation and registering the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Service:**</span></span>  
  
-   <span data-ttu-id="1dfe7-140">SharePoint 모드에서를 설치 하는 동안 현재 계정 (' 설치 ' 계정 이라고 함)에는 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 로컬 컴퓨터에 대 한 관리 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-140">The current account during the installation (referred to as the 'setup' account) of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in SharePoint mode needs to have administrative rights in the local computer.</span></span> <span data-ttu-id="1dfe7-141">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]Sharepoint를 설치 하 고 ' 설치 ' 계정이 sharepoint 팜 관리자 그룹의 구성원 이기도 한 경우 설치 하는 경우 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 설치 시 서비스를 등록 합니다 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="1dfe7-141">If you are installing [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] after SharePoint is installed and the 'setup' account is also a member of the SharePoint farm administrators group, the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installation will register the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service for you.</span></span> <span data-ttu-id="1dfe7-142">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]SharePoint가 설치 되기 전에를 설치 하거나 ' 설치 ' 계정이 팜 관리자 그룹의 구성원이 아닌 경우에는 서비스를 수동으로 등록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-142">If you install [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] before SharePoint is installed or the 'setup' account is not a member of the farm administrators group, you register the service manually.</span></span> <span data-ttu-id="1dfe7-143">[2단계: Reporting Services SharePoint 서비스 등록 및 시작](#bkmk_install_SSRS_sharedservice)섹션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-143">See the section [Step 2: Register and Start the Reporting Services SharePoint Service](#bkmk_install_SSRS_sharedservice).</span></span>  
  
 <span data-ttu-id="1dfe7-144">**[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 서비스 애플리케이션 만들기**</span><span class="sxs-lookup"><span data-stu-id="1dfe7-144">**Creating [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Service Applications**</span></span>  
  
-   <span data-ttu-id="1dfe7-145">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 서비스를 설치하고 등록하여 하나 이상의 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 서비스 애플리케이션을 만드세요.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-145">Following installation and registering the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service, create one or more [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service applications.</span></span> <span data-ttu-id="1dfe7-146">"SharePoint 팜 서비스 계정"이 일시적으로 로컬 관리자 그룹의 멤버여야 Reporting Services 서비스 애플리케이션을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-146">The "SharePoint farm service account " needs to temporarily be a member of the local administrators group so the Reporting Services service application can be created.</span></span> <span data-ttu-id="1dfe7-147">SharePoint 2013 계정 권한에 대 한 자세한 내용은 [sharepoint 2013의 계정 권한 및 보안 설정](https://technet.microsoft.com/library/cc678863.aspx) ()을 참조 하세요 https://technet.microsoft.com/library/cc678863.aspx) .</span><span class="sxs-lookup"><span data-stu-id="1dfe7-147">For more information on SharePoint 2013 account permissions, see [Account permissions and security settings in SharePoint 2013](https://technet.microsoft.com/library/cc678863.aspx) (https://technet.microsoft.com/library/cc678863.aspx).</span></span>  
  
     <span data-ttu-id="1dfe7-148">SharePoint 팜 관리자 계정이 또한 로컬 운영 체제 관리자 계정이 아닌 것이 가장 좋은 보안 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-148">It is security best practice that SharePoint farm administrator accounts are not also local operating system administrator accounts.</span></span> <span data-ttu-id="1dfe7-149">설치 프로세스의 일부로 로컬 관리자 그룹에 팜 관리자 계정을 추가하는 경우 설치가 완료된 후 로컬 관리자 그룹에서 계정을 제거하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-149">If you add a farm admin account to the local administrators group as part of your installation process, it is recommended you remove the account from the local administrators group after installation is complete.</span></span>  
  
##  <a name="step-1-install-reporting-services-report-server-in-sharepoint-mode"></a><a name="bkmk_install_SSRS"></a><span data-ttu-id="1dfe7-150">1 단계: SharePoint 모드에서 Reporting Services 보고서 서버 설치</span><span class="sxs-lookup"><span data-stu-id="1dfe7-150">Step 1: Install Reporting Services Report Server in SharePoint mode</span></span>  
 <span data-ttu-id="1dfe7-151">이 단계는 SharePoint 모드의 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 보고서 서버와 SharePoint 제품용 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 추가 기능을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-151">This step installs a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] report server in SharePoint mode and the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] add-in for SharePoint products.</span></span> <span data-ttu-id="1dfe7-152">컴퓨터에 이미 설치된 기능에 따라 다음 단계에 설명된 설치 페이지 중 일부가 표시되지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-152">Depending on what is already installed on your computer, you may not see some of the installation pages described in the following steps.</span></span>  
  
1.  <span data-ttu-id="1dfe7-153">SQL Server 설치 마법사(Setup.exe)를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-153">Run the SQL Server Installation Wizard (Setup.exe).</span></span>  
  
2.  <span data-ttu-id="1dfe7-154">마법사의 왼쪽에서 **설치** 를 클릭하고 **새 SQL Server 독립 실행형 설치 또는 기존 설치에 기능 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-154">Click **Installation** in the left side of the wizard and then click **New SQL Server stand-alone installation or add features to an existing installation**.</span></span>  
  
3.  <span data-ttu-id="1dfe7-155">모든 규칙이 통과되었다고 가정하고 **설치 지원 규칙** 페이지에서 **확인** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-155">Click **OK** on the **Setup Support Rules** page, assuming all rules passed.</span></span>  
  
4.  <span data-ttu-id="1dfe7-156">**설치 지원 파일** 페이지에서 **설치** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-156">Click **Install** on the **Setup Support Files** page.</span></span> <span data-ttu-id="1dfe7-157">컴퓨터에 이미 설치된 기능에 따라 다음과 같은 메시지가 표시될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-157">Depending on what is already installed on your computer, you might see the following message:</span></span>  
  
    -   <span data-ttu-id="1dfe7-158">"영향을 받는 하나 이상의 파일에 보류 중인 작업이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-158">"One or more affected files have operations pending.</span></span> <span data-ttu-id="1dfe7-159">설치 프로세스가 완료된 후 컴퓨터를 다시 시작해야 합니다."</span><span class="sxs-lookup"><span data-stu-id="1dfe7-159">You must restart your computer after the setup process is completed."</span></span>  
  
    -   <span data-ttu-id="1dfe7-160">**Ok**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-160">Click **Ok**.</span></span>  
  
5.  <span data-ttu-id="1dfe7-161">지원 파일 설치가 끝내고 **지원 규칙** 페이지에 **통과** 상태가 표시되면 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-161">Click **Next** after the support files have completed installing and the **Support Rules** pages show a status of **Passed**.</span></span> <span data-ttu-id="1dfe7-162">경고 또는 차단 문제를 검토합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-162">Review any warnings or blocking issues.</span></span>  
  
6.  <span data-ttu-id="1dfe7-163">**설치 유형** 페이지에서 **SQL Server 2014의 기존 인스턴스에 기능 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-163">On the **Installation Type** page, click **Add features to an existing instance of SQL Server 2014**.</span></span> <span data-ttu-id="1dfe7-164">드롭다운 목록에서 올바른 인스턴스를 선택하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-164">Select the correct instance in the drop-down list and click **Next**.</span></span>  
  
7.  <span data-ttu-id="1dfe7-165">**제품 키** 페이지가 표시되면 키를 입력하거나 기본값인 '평가판' 버전을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-165">If you see the **Product Key** page, type your key or accept the default of the 'Enterprise Evaluation' edition.</span></span>  
  
     <span data-ttu-id="1dfe7-166">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-166">Click **Next**.</span></span>  
  
8.  <span data-ttu-id="1dfe7-167">사용 조건 페이지가 표시되면 사용 조건을 검토하고 동의합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-167">If you see the License terms page, review and accept the license terms.</span></span> <span data-ttu-id="1dfe7-168">제품 기능 및 지원 향상에 도움이 되는 기능 사용량 현황 데이터 전송에 동의한 것에 감사한다는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-168">Microsoft appreciates you clicking to agree to send feature usage data to help improve product features and support.</span></span>  
  
     <span data-ttu-id="1dfe7-169">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-169">Click **Next**.</span></span>  
  
9. <span data-ttu-id="1dfe7-170">**설치 역할** 페이지가 표시되면 **SQL Server 기능 설치**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-170">If you see the **Setup Role** page, select **SQL Server Feature Installation**</span></span>  
  
     <span data-ttu-id="1dfe7-171">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-171">Click **Next**</span></span>  
  
     <span data-ttu-id="1dfe7-172">![설치 역할을 위한 SQL Server 기능 설치](../../../2014/sql-server/install/media/rs-setuprole.gif "설치 역할을 위한 SQL Server 기능 설치")</span><span class="sxs-lookup"><span data-stu-id="1dfe7-172">![SQL Server Feature Installation for setup role](../../../2014/sql-server/install/media/rs-setuprole.gif "SQL Server Feature Installation for setup role")</span></span>  
  
10. <span data-ttu-id="1dfe7-173">**기능 선택** 페이지에서 다음을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-173">Select the following on the **Feature Selection** page:</span></span>  
  
    -   <span data-ttu-id="1dfe7-174">**Reporting Services-SharePoint**</span><span class="sxs-lookup"><span data-stu-id="1dfe7-174">**Reporting Services - SharePoint**</span></span>  
  
    -   <span data-ttu-id="1dfe7-175">**SharePoint 제품용 추가 기능을 Reporting Services**합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-175">**Reporting Services add-in for SharePoint Products**.</span></span>  
  
         <span data-ttu-id="1dfe7-176">![참고](../../../2014/reporting-services/media/rs-fyinote.png "참고") 추가 기능을 설치 하는 설치 마법사 옵션은 릴리스의 새로운 기능입니다 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="1dfe7-176">![note](../../../2014/reporting-services/media/rs-fyinote.png "note") The installation wizard option for installing the add-in is new with the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] release.</span></span>  
  
    -   <span data-ttu-id="1dfe7-177">아직 SQL Server [!INCLUDE[ssDE](../../includes/ssde-md.md)]의 인스턴스가 없는 경우 전체 환경에 대해 **데이터베이스 엔진 서비스** 및 **관리 도구 전체** 를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-177">If you do not already have an instance of SQL Server [!INCLUDE[ssDE](../../includes/ssde-md.md)], you could also select **Database Engine Services** and **Management Tools Complete** for a complete environment.</span></span>  
  
     <span data-ttu-id="1dfe7-178">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-178">Click **Next**.</span></span>  
  
     <span data-ttu-id="1dfe7-179">![SharePoint 모드로 SSRS 기능 선택](../../../2014/sql-server/install/media/rs-setupfeatureselection-sharepoint-with-circles.gif "SharePoint 모드로 SSRS 기능 선택")</span><span class="sxs-lookup"><span data-stu-id="1dfe7-179">![SSRS Feature Selection for SharePoint mode](../../../2014/sql-server/install/media/rs-setupfeatureselection-sharepoint-with-circles.gif "SSRS Feature Selection for SharePoint mode")</span></span>  
  
11. <span data-ttu-id="1dfe7-180">**설치 규칙** 페이지가 표시되면 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-180">If you see the **Installation Rules** page.</span></span> <span data-ttu-id="1dfe7-181">경고 또는 차단 문제를 검토합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-181">Review any warnings or blocking issues.</span></span> <span data-ttu-id="1dfe7-182">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-182">Then click **Next**</span></span>  
  
12. <span data-ttu-id="1dfe7-183">데이터베이스 엔진 서비스를 선택한 경우 **인스턴스 구성** 페이지에서 **MSSQLSERVER** 의 기본 인스턴스를 적용하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-183">If you selected the Database Engine services, accept the default instance of **MSSQLSERVER** on the **Instance Configuration** page and click **Next**.</span></span>  
  
     <span data-ttu-id="1dfe7-184">![참고](../../../2014/reporting-services/media/rs-fyinote.png "참고")Reporting Services SharePoint 서비스 아키텍처는 이전 Reporting Services 아키텍처처럼 SQL Server "인스턴스"를 기반으로 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-184">![note](../../../2014/reporting-services/media/rs-fyinote.png "note")The Reporting Services SharePoint service architecture is not based on a SQL Server "instance" as was the previous Reporting Services architecture.</span></span>  
  
13. <span data-ttu-id="1dfe7-185">**디스크 공간 요구 사항** 페이지를 검토하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-185">Review the **Disk Space Requirements** page and click **Next**.</span></span>  
  
14. <span data-ttu-id="1dfe7-186">**서버 구성** 페이지가 표시되면 적합한 자격 증명을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-186">If you see the **Server Configuration** page type appropriate credentials.</span></span> <span data-ttu-id="1dfe7-187">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 데이터 경고 또는 가입 기능을 사용하려면 SQL Server 에이전트의 **시작 유형** 을 **자동**으로 변경해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-187">If you want to use the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] data alerting or subscription features, you need to change the **Startup Type** for SQL Server Agent to **Automatic**.</span></span> <span data-ttu-id="1dfe7-188">컴퓨터에 이미 설치된 기능에 따라 **서버 구성** 페이지가 표시되지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-188">You may not see the **Server Configuration** page, depending on what is already installed on the computer.</span></span>  
  
     <span data-ttu-id="1dfe7-189">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-189">Click **Next**.</span></span>  
  
15. <span data-ttu-id="1dfe7-190">데이터베이스 엔진 서비스를 선택한 경우 **데이터베이스 엔진 구성** 페이지가 표시되면 해당 계정을 SQL 관리자 목록에 추가하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-190">If you selected the Database Engine services, you will see the **Database Engine Configuration** page, add appropriate accounts to the list of SQL Administrators and click **Next**.</span></span>  
  
16. <span data-ttu-id="1dfe7-191">**Reporting Services 구성** 페이지에서 **설치만** 옵션이 선택된 상태로 표시되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-191">On the **Reporting Services Configuration** page you should see the **Install only** option is selected.</span></span> <span data-ttu-id="1dfe7-192">이 옵션은 보고서 서버 파일을 설치하고 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]용 SharePoint 환경을 구성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-192">This option installs the report server files, and does not configure the SharePoint environment for [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="1dfe7-193">SQL Server 설치가 완료되면 이 항목의 다른 섹션을 따라 SharePoint 환경을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-193">When the SQL Server installation is complete, follow the other sections of this topic to configure the SharePoint environment.</span></span> <span data-ttu-id="1dfe7-194">이 절차에는 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 공유 서비스 설치 및 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 서비스 애플리케이션 생성이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-194">This Includes installing the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] shared service and creating [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service applications.</span></span>  
  
     <span data-ttu-id="1dfe7-195">![SQL Server 설치 마법사 - SSRS 구성 페이지](../../../2014/sql-server/install/media/rs-2012sp1-setup-ssrs-configpage-with-circles.gif "SQL Server 설치 마법사 - SSRS 구성 페이지")</span><span class="sxs-lookup"><span data-stu-id="1dfe7-195">![SQL Server Setup Wizard - SSRS Configuration Page](../../../2014/sql-server/install/media/rs-2012sp1-setup-ssrs-configpage-with-circles.gif "SQL Server Setup Wizard - SSRS Configuration Page")</span></span>  
  
17. <span data-ttu-id="1dfe7-196">**오류 보고** 페이지에서 오류 보고서를 보내기 위한 확인란을 클릭하면 Microsoft가 SQL Server 기능 및 서비스를 개선하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-196">Help Microsoft improve SQL Server features and services by clicking the check box to send error reports on the **Error Reporting** page.</span></span>  
  
     <span data-ttu-id="1dfe7-197">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-197">Click **Next**.</span></span>  
  
18. <span data-ttu-id="1dfe7-198">경고를 검토한 후 **설치 구성 규칙** 페이지에서 **다음** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-198">Review any warnings and then click **Next** on the **Installation Configuration Rules** page.</span></span>  
  
19. <span data-ttu-id="1dfe7-199">**설치 준비** 페이지에서 설치 요약을 검토한 후 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-199">On the **Ready to Install** page, review the installation summary and then click **Next**.</span></span> <span data-ttu-id="1dfe7-200">요약에 **SharePointFilesOnlyMode** 값을 표시하는 **Reporting Services SharePoint 모드**하위 노드가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-200">The summary will include a **Reporting Services SharePoint Mode** child node that will show a value of **SharePointFilesOnlyMode**.</span></span> <span data-ttu-id="1dfe7-201">**설치**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-201">Click **Install**.</span></span>  
  
20. <span data-ttu-id="1dfe7-202">설치하는 데 몇 분 정도 걸립니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-202">The installation will take several minutes.</span></span> <span data-ttu-id="1dfe7-203">기능 목록 및 각 기능의 상태가 표시된 **완료** 페이지가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-203">You will see the **Complete** page with the features listed and the status of each feature.</span></span> <span data-ttu-id="1dfe7-204">컴퓨터를 다시 시작해야 함을 나타내는 정보 대화 상자가 표시될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-204">You may see an information dialog indicating the computer needs to be restarted.</span></span>  
  
##  <a name="step-2-register-and-start-the-reporting-services-sharepoint-service"></a><a name="bkmk_install_SSRS_sharedservice"></a><span data-ttu-id="1dfe7-205">2 단계: Reporting Services SharePoint 서비스 등록 및 시작</span><span class="sxs-lookup"><span data-stu-id="1dfe7-205">Step 2: Register and Start the Reporting Services SharePoint Service</span></span>  
 <span data-ttu-id="1dfe7-206">![PowerShell 관련 콘텐츠](../../../2014/reporting-services/media/rs-powershellicon.jpg "PowerShell 관련 콘텐츠")</span><span class="sxs-lookup"><span data-stu-id="1dfe7-206">![PowerShell related content](../../../2014/reporting-services/media/rs-powershellicon.jpg "PowerShell related content")</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1dfe7-207">기존 SharePoint 팜에 설치하는 경우에는 이 섹션의 단계를 완료할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-207">If you are installing into an existing SharePoint farm, you do not need to complete the steps in this section.</span></span> <span data-ttu-id="1dfe7-208">이 문서의 이전 섹션의 일부로 SQL Server 설치 마법사를 실행한 경우 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint 서비스가 설치되어 시작되었습니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-208">The [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint service is installed and started when you ran the SQL Server installation wizard as part of the previous section of this document.</span></span>  
  
 <span data-ttu-id="1dfe7-209">다음은 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 서비스를 수동으로 등록해야 하는 일반적인 이유입니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-209">The following are the common reasons why you need to manually register the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service.</span></span>  
  
-   <span data-ttu-id="1dfe7-210">SharePoint가 설치되기 전에 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint 모드를 설치했습니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-210">You installed [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint mode before SharePoint was installed.</span></span>  
  
-   <span data-ttu-id="1dfe7-211">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint 모드 설치에 사용된 계정이 SharePoint 팜 관리자 그룹의 멤버가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-211">The account used to install [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint mode, was not a member of the SharePoint farm administrators group.</span></span> <span data-ttu-id="1dfe7-212">자세한 내용은 [설치 계정](#bkmk_setupaccounts)섹션을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-212">For more information, see the section [Setup accounts](#bkmk_setupaccounts).</span></span>  
  
 <span data-ttu-id="1dfe7-213">필요한 파일이 SQL Server 설치 마법사의 일부로 설치되었지만 서비스를 SharePoint 팜에 등록해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-213">The necessary files were installed as part of the SQL Server installation wizard, but the services need to be registered into the SharePoint farm.</span></span> <span data-ttu-id="1dfe7-214">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 릴리스에는 SharePoint 모드의 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 에 대한 PowerShell 지원이 도입되었습니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-214">The [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] release introduces PowerShell support for [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in SharePoint mode.</span></span>  
  
 <span data-ttu-id="1dfe7-215">다음 단계에서는 SharePoint 관리 셸을 열고 cmdlet을 실행하는 절차를 안내합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-215">The following steps guide you through opening the SharePoint Management Shell and running cmdlets:</span></span>  
  
1.  <span data-ttu-id="1dfe7-216">**시작** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-216">Click the **Start** button</span></span>  
  
2.  <span data-ttu-id="1dfe7-217">**Microsoft SharePoint 2013 제품** 그룹을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-217">Click the **Microsoft SharePoint 2013 Products** group.</span></span>  
  
3.  <span data-ttu-id="1dfe7-218">**SharePoint 2013 관리 셸** 을 마우스 오른쪽 단추로 클릭하고 **관리자 권한으로 실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-218">Right-click **SharePoint 2013 Management Shell** click **Run as administrator**.</span></span> <span data-ttu-id="1dfe7-219">참고: SharePoint 명령은 표준 Windows PowerShell 창에서 인식되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-219">NOTE: the SharePoint commands are not recognized in the standard Windows PowerShell window.</span></span> <span data-ttu-id="1dfe7-220">**SharePoint 2013 관리 셸**을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-220">Use the **SharePoint 2013 Management Shell**.</span></span>  
  
4.  <span data-ttu-id="1dfe7-221">다음 PowerShell 명령을 실행하여 SharePoint 서비스를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-221">Run the following PowerShell command to install the SharePoint service.</span></span> <span data-ttu-id="1dfe7-222">명령을 성공적으로 완료하면 관리 셸에 새 줄이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-222">A successful completion of the command displays a new line in the management shell.</span></span> <span data-ttu-id="1dfe7-223">명령을 성공적으로 완료하면**메시지가 관리 셸로 반환되지 않습니다.**</span><span class="sxs-lookup"><span data-stu-id="1dfe7-223">**No message is returned** to the management shell when the command completes successfully:</span></span>  
  
    ```powershell
    Install-SPRSService  
    ```  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="1dfe7-224">다음과 유사한 오류 메시지가 표시되는 경우</span><span class="sxs-lookup"><span data-stu-id="1dfe7-224">If you see an error message similar to the following:</span></span>  
    >   
    >  <span data-ttu-id="1dfe7-225">Install-sprsserviceinstall-sprsservice: ' Install-sprsserviceinstall-sprsservice ' 용어는로 **인식 되지 않습니다** .</span><span class="sxs-lookup"><span data-stu-id="1dfe7-225">Install-SPRSService : The term 'Install-SPRSService' **is not recognized** as the</span></span>  
    > <span data-ttu-id="1dfe7-226">cmdlet, 함수, 스크립트 파일 또는 실행 프로그램의 이름으로 인식되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-226">name of a cmdlet, function, script file, or operable program.</span></span> <span data-ttu-id="1dfe7-227">데이터 마이그레이션 솔루션에 대한</span><span class="sxs-lookup"><span data-stu-id="1dfe7-227">Check the</span></span>  
    > <span data-ttu-id="1dfe7-228">경로가 올바른지 확인한 다음</span><span class="sxs-lookup"><span data-stu-id="1dfe7-228">spelling of the name, or if a path was included, verify that the path is</span></span>  
    > <span data-ttu-id="1dfe7-229">다시 시도하세요.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-229">correct and try again.</span></span>  
  
5.  <span data-ttu-id="1dfe7-230">다음 PowerShell 명령을 실행하여 서비스 프록시를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-230">Run the following PowerShell command to install the service proxy.</span></span> <span data-ttu-id="1dfe7-231">명령을 성공적으로 완료하면 관리 셸에 새 줄이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-231">A successful completion of the command displays a new line in the management shell.</span></span> <span data-ttu-id="1dfe7-232">명령을 성공적으로 완료하면**메시지가 관리 셸로 반환되지 않습니다.**</span><span class="sxs-lookup"><span data-stu-id="1dfe7-232">**No message is returned** to the management shell when the command completes successfully:</span></span>  
  
    ```powershell
    Install-SPRSServiceProxy  
    ```  
  
6.  <span data-ttu-id="1dfe7-233">다음 PowerShell 명령을 실행하여 서비스를 시작하거나 SharePoint 중앙 관리에서 서비스를 시작하는 방법에 대한 다음 지침 참고 사항을 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-233">Run the following PowerShell command to start the service or see the following notes for instructions on how to start the service from SharePoint Central administration:</span></span>  
  
    ```powershell
    Get-SPServiceInstance -all |where {$_.TypeName -like "SQL Server Reporting*"} | Start-SPServiceInstance  
    ```  
  
 <span data-ttu-id="1dfe7-234">SharePoint 관리 셸 대신 Windows PowerShell에 있거나 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint 모드가 설치되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-234">Either you are in the Windows Powershell instead of the SharePoint Management Shell  or [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint mode is not installed.</span></span> <span data-ttu-id="1dfe7-235">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 및 PowerShell에 대한 자세한 내용은 [Reporting Services SharePoint 모드용 PowerShell cmdlet](../../../2014/reporting-services/powershell-cmdlets-for-reporting-services-sharepoint-mode.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-235">For more information on [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] and PowerShell, see [PowerShell cmdlets for Reporting Services SharePoint Mode](../../../2014/reporting-services/powershell-cmdlets-for-reporting-services-sharepoint-mode.md).</span></span>  
  
 <span data-ttu-id="1dfe7-236">또한 세 번째 PowerShell 명령을 실행하는 대신 SharePoint 중앙 관리에서 서비스를 시작할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-236">You can also start the service from SharePoint central Administration rather than running the third PowerShell command.</span></span> <span data-ttu-id="1dfe7-237">또한 다음 단계는 서비스가 실행 중인지 확인하는 데 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-237">The following steps are also useful to verify that the service is running.</span></span>  
  
1.  <span data-ttu-id="1dfe7-238">SharePoint 중앙 관리의 **시스템 설정** 그룹에서 **서버의 서비스 관리** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-238">In SharePoint Central Administration, click **Manage Services on Server** in the **System Settings** group.</span></span>  
  
2.  <span data-ttu-id="1dfe7-239">**SQL Server Reporting Services 서비스** 를 찾고 동작 열의 **시작** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-239">Find **SQL Server Reporting Services Service** and click **Start** in the Action column.</span></span>  
  
3.  <span data-ttu-id="1dfe7-240">Reporting Services 서비스 상태가 **중지됨** 에서 **시작됨**으로 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-240">The status of the Reporting Services service will change from **Stopped** to **Started**.</span></span> <span data-ttu-id="1dfe7-241">Reporting Services 서비스가 목록에 없으면 PowerShell을 사용하여 서비스를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-241">If the Reporting Services service is not in the list, use PowerShell to install the service.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="1dfe7-242">Reporting Services 서비스가 **시작 중** 상태를 유지 하 고 **시작 됨**으로 변경 되지 않으면 Windows 서버 관리자에서 ' SharePoint 2013 관리 ' 서비스가 시작 되었는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-242">If the Reporting Services service stays in the **Starting** status and does not change to **Started**, verify the 'SharePoint 2013 Administration' service is started in Windows Server Manager.</span></span>  
  
##  <a name="step-3-create-a-reporting-services-service-application"></a><a name="bkmk_create_serrviceapplication"></a> <span data-ttu-id="1dfe7-243">3단계: Reporting Services 서비스 애플리케이션 만들기</span><span class="sxs-lookup"><span data-stu-id="1dfe7-243">Step 3: Create a Reporting Services Service Application</span></span>  
 <span data-ttu-id="1dfe7-244">이 섹션에서는 서비스 애플리케이션을 만드는 단계와 속성에 대한 설명(기존 서비스 애플리케이션을 검토하려는 경우)을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-244">This section provides the steps to create a service application and a description of the properties, if you are reviewing an existing service application.</span></span>  
  
1.  <span data-ttu-id="1dfe7-245">SharePoint 중앙 관리의 **응용 프로그램 관리** 그룹에서 **서비스 응용 프로그램 관리**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-245">In SharePoint Central Administration, in the **Application Management** group, click **Manage Service Applications**.</span></span>  
  
2.  <span data-ttu-id="1dfe7-246">SharePoint 리본에서 **새로 만들기** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-246">In the SharePoint ribbon, click the **New** button.</span></span>  
  
3.  <span data-ttu-id="1dfe7-247">새로 만들기 메뉴에서 **SQL Server Reporting Services 서비스 애플리케이션**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-247">In the New menu, click **SQL Server Reporting Services Service Application.**.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="1dfe7-248">이 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 옵션이 목록에 표시 되지 않으면 \*\* [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 공유 서비스가 설치 되어 있지 않음을 나타냅니다\*\*.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-248">If the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] option does not appear in the list, it is an **indication that the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] shared service is not installed**.</span></span> <span data-ttu-id="1dfe7-249">PowerShell cmdlt을 사용하여 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 서비스를 설치하는 방법에 대한 이전 섹션을 검토합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-249">Review the previous section on how to use PowerShell cmdlts to install the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service.</span></span>  
  
4.  <span data-ttu-id="1dfe7-250">**SQL Server Reporting Services 서비스 애플리케이션 만들기** 페이지에서 애플리케이션의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-250">In the **Create SQL Server Reporting Services Service Application** page, enter a name for the application.</span></span> <span data-ttu-id="1dfe7-251">여러 개의 Reporting Services 서비스 애플리케이션을 만들 경우 설명이 포함된 이름이나 명명 규칙을 사용하면 관리 및 운영 작업을 구성하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-251">If you are creating multiple Reporting Services service applications, a descriptive name or naming convention will help you organize your administration and management operations.</span></span>  
  
5.  <span data-ttu-id="1dfe7-252">**애플리케이션 풀** 섹션에서 애플리케이션에 대한 새 애플리케이션 풀을 만듭니다(권장).</span><span class="sxs-lookup"><span data-stu-id="1dfe7-252">In **Application Pool** section, create a new application pool for the application (recommended).</span></span> <span data-ttu-id="1dfe7-253">애플리케이션 풀과 서비스 애플리케이션에 동일한 이름을 사용할 경우 진행 중인 관리를 쉽게 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-253">If you use the same name for both the application pool and the services application, it can make ongoing administration easier.</span></span> <span data-ttu-id="1dfe7-254">이는 만들려는 서비스 애플리케이션 수와 단일 애플리케이션 풀에 여러 서비스 애플리케이션을 사용해야 하는지 여부의 영향을 받을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-254">This can also be affected by how many service applications you will create and if you need to use several in a single application pool.</span></span> <span data-ttu-id="1dfe7-255">애플리케이션 풀 관리에 대한 권장 사항 및 모범 사례에 대해서는 SharePoint Server 설명서를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-255">See the SharePoint Server documentation on recommendations and best practices for application pool management.</span></span>  
  
     <span data-ttu-id="1dfe7-256">애플리케이션 풀에 대한 보안 계정을 선택하거나 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-256">Select or create a security account for the application pool.</span></span> <span data-ttu-id="1dfe7-257">도메인 사용자 계정을 지정하세요.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-257">Be sure to specify a domain user account.</span></span> <span data-ttu-id="1dfe7-258">도메인 사용자 계정을 사용하면 SharePoint의 관리되는 계정 기능을 사용할 수 있으므로 암호 및 계정 정보를 한 곳에서 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-258">A domain user account enables the use of the SharePoint managed account feature, which lets you update passwords and account information in one place.</span></span> <span data-ttu-id="1dfe7-259">같은 ID로 실행할 추가 서비스 인스턴스를 포함하도록 배포를 확장하려는 경우에도 도메인 계정이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-259">Domain accounts are also required if you plan to scale out the deployment to include additional service instances that run under the same identity.</span></span>  
  
6.  <span data-ttu-id="1dfe7-260">**데이터베이스 서버**에서 현재 서버를 사용하거나 다른 SQL Server를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-260">In the **Database Server**, you can use the current server or choose a different SQL Server.</span></span>  
  
7.  <span data-ttu-id="1dfe7-261">**데이터베이스 이름** 에서 기본값은 `ReportingService_<guid>`이고 고유한 데이터베이스 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-261">In **Database Name** the default value is `ReportingService_<guid>`, which is a unique database name.</span></span> <span data-ttu-id="1dfe7-262">새 값을 입력하는 경우 고유한 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-262">If you type a new value, type a unique value.</span></span> <span data-ttu-id="1dfe7-263">이 데이터베이스는 서비스 애플리케이션용으로 새로 만든 것입니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-263">This is the new database to be created specifically for the services application.</span></span>  
  
8.  <span data-ttu-id="1dfe7-264">**데이터베이스 인증**에서 기본값은 Windows  인증입니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-264">In **Database Authentication**, the default is Windows Authentication.</span></span> <span data-ttu-id="1dfe7-265">**SQL 인증**을 선택하는 경우 SharePoint 배포에서 이 인증 유형을 사용하는 최선의 구현 방법은 SharePoint 설명서를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-265">If you choose **SQL Authentication**, refer to SharePoint documentation for best practices on how to use this authentication type in a SharePoint deployment.</span></span>  
  
9. <span data-ttu-id="1dfe7-266">**웹 애플리케이션 연결** 섹션에서 현재 Reporting Services 서비스 애플리케이션에 의해 액세스하기 위해 프로비전 대상 웹 애플리케이션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-266">In the **Web Application Association** section, select the Web Application to be provisioned for access by the current Reporting Services Service Application.</span></span> <span data-ttu-id="1dfe7-267">하나의 Reporting Services 서비스 애플리케이션을 하나의 웹 애플리케이션에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-267">You can associate one Reporting Services service application to one web application.</span></span> <span data-ttu-id="1dfe7-268">모든 현재 웹 애플리케이션이 이미 Reporting Services 서비스 애플리케이션에 연결된 경우 경고 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-268">If all of the current web applications are already associated with a Reporting Services service application, you see a warning message.</span></span>  
  
10. <span data-ttu-id="1dfe7-269">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-269">Click **OK**.</span></span>  
  
11. <span data-ttu-id="1dfe7-270">서비스 애플리케이션 만들기를 완료하는 데 몇 분이 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-270">The process to create a service application could take several minutes to complete.</span></span> <span data-ttu-id="1dfe7-271">완료되면 확인 메시지와 **구독 및 경고 프로비전** 페이지로 이동하는 링크가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-271">When it is complete, you will see a confirmation message and a link to a **Provision Subscriptions and Alerts** page.</span></span> <span data-ttu-id="1dfe7-272">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 구독 기능 및 데이터 경고 기능을 사용하려면 프로비전 단계를 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-272">Complete the provision step if you want to use the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] subscriptions feature or the data alerts feature.</span></span> <span data-ttu-id="1dfe7-273">자세한 내용은 [SSRS 서비스 애플리케이션에 대한 구독 및 경고 프로비전](../../reporting-services/install-windows/provision-subscriptions-and-alerts-for-ssrs-service-applications.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-273">For more information, see [Provision Subscriptions and Alerts for SSRS Service Applications](../../reporting-services/install-windows/provision-subscriptions-and-alerts-for-ssrs-service-applications.md).</span></span>  
  
 <span data-ttu-id="1dfe7-274">![PowerShell 관련 콘텐츠](../../../2014/reporting-services/media/rs-powershellicon.jpg "PowerShell 관련 콘텐츠") PowerShell을 사용 하 여 서비스 응용 프로그램을 만드는 방법에 대 한 자세한 내용은 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 다음을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-274">![PowerShell related content](../../../2014/reporting-services/media/rs-powershellicon.jpg "PowerShell related content") For information on using PowerShell to create a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service application, see:</span></span>  
  
-   <span data-ttu-id="1dfe7-275">다음 섹션인 [1-4단계를 위한 Windows PowerShell 스크립트](#bkmk_full_script)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-275">See the following section [Windows PowerShell script for Steps 1-4](#bkmk_full_script).</span></span>  
  
-   <span data-ttu-id="1dfe7-276">항목 [PowerShell을 사용하여 Reporting Services 서비스 애플리케이션을 만들려면](../../../2014/reporting-services/reporting-services-sharepoint-service-and-service-applications.md#bkmk_powershell_create_ssrs_serviceapp)</span><span class="sxs-lookup"><span data-stu-id="1dfe7-276">Topic [To create a Reporting Services Service Application using PowerShell](../../../2014/reporting-services/reporting-services-sharepoint-service-and-service-applications.md#bkmk_powershell_create_ssrs_serviceapp).</span></span>  
  
##  <a name="step-4-activate-the-power-view-site-collection-feature"></a><a name="bkmk_powerview"></a><span data-ttu-id="1dfe7-277">4 단계: 파워 뷰 사이트 모음 기능을 활성화 합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-277">Step 4: Activate the Power View Site Collection Feature.</span></span>  
 [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]<span data-ttu-id="1dfe7-278">는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] SharePoint 제품용 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 추가 기능으로, 사이트 모음 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-278">, a feature of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Add-in for [!INCLUDE[msCoName](../../includes/msconame-md.md)] SharePoint Products, is a site collection feature.</span></span> <span data-ttu-id="1dfe7-279">이 기능은 루트 사이트 모음과 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 추가 기능이 설치된 후에 생성된 사이트 모음에 대해 자동으로 활성화됩니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-279">The feature is activated automatically for root site collections and site collections created after the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] add-in is installed.</span></span> <span data-ttu-id="1dfe7-280">[!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]를 사용하려면 기능이 활성화되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-280">If you plan to use [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)], verify that the feature is activated.</span></span>  
  
 <span data-ttu-id="1dfe7-281">SharePoint Server 설치 후에 SharePoint 제품용 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 추가 기능을 설치하면 보고서 서버 통합 기능 및 Power View 통합 기능이 루트 사이트 모음에 대해서만 활성화됩니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-281">If you install the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] add-in for SharePoint Products after the installation of the SharePoint Server, then the Report Server integration feature and the Power View integration feature will only be activated for root site collections.</span></span> <span data-ttu-id="1dfe7-282">기타 사이트 모음의 경우 기능을 수동으로 활성화합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-282">For other site collections, manually activate the features.</span></span>  
  
#### <a name="to-activate-or-verify-the-power-view-site-collection-feature"></a><span data-ttu-id="1dfe7-283">Power View 사이트 모음 기능을 활성화하거나 확인하려면</span><span class="sxs-lookup"><span data-stu-id="1dfe7-283">To Activate or Verify the Power View Site Collection Feature</span></span>  
  
1.  <span data-ttu-id="1dfe7-284">다음 단계에서는 SharePoint 사이트가 2013 **환경 버전**에 대해 구성되었다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-284">The following steps assume your SharePoint site is configured for the 2013 **experience version**.</span></span>  
  
     <span data-ttu-id="1dfe7-285">원하는 SharePoint 사이트로 브라우저를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-285">Open your browser to the desired SharePoint site.</span></span> <span data-ttu-id="1dfe7-286">예: http:// \<servername> /sites/bi</span><span class="sxs-lookup"><span data-stu-id="1dfe7-286">For example http://\<servername>/sites/bi</span></span>  
  
2.  <span data-ttu-id="1dfe7-287">**설정**![SharePoint 설정](https://docs.microsoft.com/analysis-services/analysis-services/media/as-sharepoint2013-settings-gear.gif "SharePoint 설정")을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-287">Click **Settings**![SharePoint Settings](https://docs.microsoft.com/analysis-services/analysis-services/media/as-sharepoint2013-settings-gear.gif "SharePoint Settings").</span></span>  
  
3.  <span data-ttu-id="1dfe7-288">**사이트 설정**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-288">Click **Site settings**.</span></span>  
  
4.  <span data-ttu-id="1dfe7-289">**사이트 모음 관리** 그룹에서 **사이트 모음 기능**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-289">In the **Site Collection Administration** group Click **Site collection features**.</span></span>  
  
5.  <span data-ttu-id="1dfe7-290">목록에서 **Power View 통합 기능** 을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-290">Find **Power View Integration Feature** in the list.</span></span>  
  
6.  <span data-ttu-id="1dfe7-291">**활성화**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-291">Click **Activate**.</span></span> <span data-ttu-id="1dfe7-292">기능 상태가 **활성**으로 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-292">The feature status will change to **Active**.</span></span>  
  
 <span data-ttu-id="1dfe7-293">이 절차는 사이트 모음별로 완료됩니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-293">This procedure is completed per site collection.</span></span> <span data-ttu-id="1dfe7-294">자세한 내용은 [SharePoint에서 보고서 서버 및 파워 뷰 통합 사이트 모음 기능 활성화](../../../2014/reporting-services/activate-the-report-server-and-power-view-integration-features-in-sharepoint.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-294">For more information, see [Activate the Report Server and Power View Integration Features in SharePoint](../../../2014/reporting-services/activate-the-report-server-and-power-view-integration-features-in-sharepoint.md).</span></span>  
  
##  <a name="windows-powershell-script-for-steps-1-4"></a><a name="bkmk_full_script"></a><span data-ttu-id="1dfe7-295">1-4 단계에 대 한 Windows PowerShell 스크립트</span><span class="sxs-lookup"><span data-stu-id="1dfe7-295">Windows PowerShell script for Steps 1-4</span></span>  
 <span data-ttu-id="1dfe7-296">이 섹션의 PowerShells 스크립트는 이전 섹션의 1~4단계를 완료하는 것과 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-296">The PowerShells script in this section are the equivalent of completing steps 1 to 4 in the previous sections.</span></span> <span data-ttu-id="1dfe7-297">이 스크립트는 다음 작업을 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-297">The script completes the following:</span></span>  
  
-   <span data-ttu-id="1dfe7-298">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 서비스 및 서비스 프록시를 설치하고 서비스를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-298">Installs [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service and service proxy, and starts the service.</span></span>  
  
-   <span data-ttu-id="1dfe7-299">“Reporting Services”라는 서비스 프록시를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-299">Creates a service proxy named "Reporting Services".</span></span>  
  
-   <span data-ttu-id="1dfe7-300">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]"Reporting Services application" 이라는 서비스 응용 프로그램을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-300">Creates a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service application named "Reporting Services Application".</span></span>  
  
-   <span data-ttu-id="1dfe7-301">사이트 모음에 대해 [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] 기능을 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-301">Enables the [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] feature for a site collection.</span></span>  
  
 <span data-ttu-id="1dfe7-302">매개 변수</span><span class="sxs-lookup"><span data-stu-id="1dfe7-302">Parameters</span></span>  
  
-   <span data-ttu-id="1dfe7-303">서비스 프록시에 대해 **-Account** 를 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-303">Update the **-Account** for the service proxy.</span></span> <span data-ttu-id="1dfe7-304">계정은 SharePoint 팜에서 관리되는 서비스 계정이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-304">The account needs to be a managed service account in the SharePoint farm.</span></span> <span data-ttu-id="1dfe7-305">자세한 내용은 SharePoint 항목 [SharePoint 2013에서 관리 및 서비스 계정 계획](https://technet.microsoft.com/library/cc263445.aspx)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-305">For more information, see the SharePoint topic [Plan for administrative and service accounts in SharePoint 2013](https://technet.microsoft.com/library/cc263445.aspx).</span></span>  
  
-   <span data-ttu-id="1dfe7-306">서비스 응용 프로그램에 대 한 **-databaseserver** 매개 변수를 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-306">Update the **-DatabaseServer** parameter for the service application.</span></span> <span data-ttu-id="1dfe7-307">이 매개 변수는 데이터베이스 엔진 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-307">This parameter is the database engine instance</span></span>  
  
-   <span data-ttu-id="1dfe7-308">기능을 사용 하도록 설정할 사이트의 **-url** 매개 변수를 업데이트 [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-308">Update the **-url** parameter of the site that you want the [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] feature enabled.</span></span>  
  
 <span data-ttu-id="1dfe7-309">**스크립트를 사용하려면:**</span><span class="sxs-lookup"><span data-stu-id="1dfe7-309">**To use the script:**</span></span>  
  
1.  <span data-ttu-id="1dfe7-310">관리 권한으로 Windows PowerShell을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-310">Open Windows PowerShell with administrative privileges.</span></span>  
  
2.  <span data-ttu-id="1dfe7-311">다음 코드를 스크립트 창에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-311">Copy the following code into the script window.</span></span>  
  
3.  <span data-ttu-id="1dfe7-312">이전 섹션에서 설명한 세 가지 매개 변수를 업데이트한 후 스크립트를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-312">Update the three parameters described in the previous section, and then run the script.</span></span>  
  
```powershell
#This script Configures SQL Server Reporting Services SharePoint mode  
  
$starttime = Get-Date  
Write-Host -foregroundcolor DarkGray StartTime>> $starttime   
  
Write-Host -ForegroundColor Green "Import the SharePoint PowerShell snappin"  
Add-PSSnapin Microsoft.Sharepoint.Powershell -EA 0  
  
Write-Host -ForegroundColor Green "Install SSRS Service and Service Proxy, and start the service"  
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"  
  
    Write-Host -ForegroundColor Green "Install the Reporting Services Shared Service"  
    Install-SPRSService  
  
    Write-Host -ForegroundColor Green " Install the Reporting Services Service Proxy"  
    Install-SPRSServiceProxy  
  
    # Get the ID of the RS Service Instance and start the service   
    Write-Host -ForegroundColor Green "Start the Reporting Services Service"  
    $RS = Get-SPServiceInstance | Where {$_.TypeName -eq "SQL Server Reporting Services Service"}  
    Start-SPServiceInstance -Identity $RS.Id.ToString()  
  
    # Wait for the Reporting Services Service to start...  
    $Status = Get-SPServiceInstance $RS.Id.ToString()  
    While ($Status.Status -ne "Online")  
    {  
        Write-Host -ForegroundColor Green "SSRS Service Not Online...Current Status = " $Status.Status  
        Start-Sleep -Seconds 2  
        $Status = Get-SPServiceInstance $RS.Id.ToString()  
    }  
  
$time = Get-Date  
Write-Host -foregroundcolor DarkGray StartTime>> $starttime   
Write-Host -foregroundcolor DarkGray $time  
  
Write-Host -ForegroundColor Green "Create a new application pool and Reporting Services service application"  
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"  
Write-Host -ForegroundColor Green "Create a new application pool"  
#!!!! update "-Account" with an existing Managed Service Account  
New-SPServiceApplicationPool -Name "Reporting Services" -Account "<domain>\User name>"  
$appPool = Get-SPServiceApplicationPool "Reporting Services"  
  
Write-Host -ForegroundColor Green " Create the Reporting Services Service Application"  
#!!!! Update "-DatabaseServer", an instance of the SQL Server database engine   
$rsService = New-SPRSServiceApplication -Name "Reporting Services Application" -ApplicationPool $appPool -DatabaseName "Reporting_Services_Application" -DatabaseServer "<server name>"  
  
Write-Host -ForegroundColor Green "Create the Reporting Services Service Application Proxy"  
$rsServiceProxy = New-SPRSServiceApplicationProxy -Name "Reporting Services Application Proxy" -ServiceApplication $rsService  
  
Write-Host -ForegroundColor Green "Associate service application proxy to default web site and grant web applications rights to SSRS application pool"  
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"     
# Associate the Reporting Services Service Applicatoin Proxy to the default web site...  
Get-SPServiceApplicationProxyGroup -default | Add-SPServiceApplicationProxyGroupMember -Member $rsServiceProxy  
  
$time=Get-Date  
Write-Host -foregroundcolor DarkGray StartTime>> $starttime   
Write-Host -foregroundcolor DarkGray $time  
  
Write-Host -ForegroundColor Green "Enable the PowerView and reportserver site features"  
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"  
#!!!! update "-url"  of the site where you want the features enabled  
Enable-SPfeature -identity "powerview" -Url http://server/sites/bi  
Enable-SPfeature -identity "reportserver" -Url http://server/sites/bi  
  
####To Verify, you can run the following:  
#Get-SPRSServiceApplication  
#Get-SPServiceApplicationPool | where {$_.name -like "reporting*"}  
#Get-SPRSServiceApplicationProxy
```  
  
##  <a name="additional-configuration"></a><a name="bkmk_additional_config"></a><span data-ttu-id="1dfe7-313">추가 구성</span><span class="sxs-lookup"><span data-stu-id="1dfe7-313">Additional Configuration</span></span>  
 <span data-ttu-id="1dfe7-314">이 섹션에서는 대부분의 SharePoint 배포에서 중요한 추가 구성 단계에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-314">This section describes additional configuration steps that are important in most SharePoint deployments.</span></span>  
  
###  <a name="configure-excel-services-and-powerpivot"></a><a name="bkmk_configure_ECS"></a><span data-ttu-id="1dfe7-315">Excel Services 및 PowerPivot 구성</span><span class="sxs-lookup"><span data-stu-id="1dfe7-315">Configure Excel Services and PowerPivot</span></span>  
 <span data-ttu-id="1dfe7-316">SharePoint의 Excel 2013 통합 문서에서 [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] Power View 보고서를 보려는 경우 팜에서 Excel Services 애플리케이션을 SharePoint 모드의 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 서버를 사용하도록 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-316">If you want to view [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] Power View reports in an Excel 2013 workbook in SharePoint, an Excel Services Application on the farm needs to be configured to use an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Server in SharePoint mode.</span></span> <span data-ttu-id="1dfe7-317">또한, [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 서비스 애플리케이션에서 사용하는 애플리케이션 풀 보안 계정은 Analysis Services 서버에서 관리자여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-317">Also, the application pool security account used by the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service application, must be an administrator on the Analysis Services Server.</span></span> <span data-ttu-id="1dfe7-318">자세한 내용은</span><span class="sxs-lookup"><span data-stu-id="1dfe7-318">For more information, see the following:</span></span>  
  
-   <span data-ttu-id="1dfe7-319">[SharePoint용 PowerPivot 2013 설치](https://docs.microsoft.com/analysis-services/instances/install-windows/install-analysis-services-in-power-pivot-mode)에서 "Analysis Services 통합을 위한 Excel Services 구성" 섹션</span><span class="sxs-lookup"><span data-stu-id="1dfe7-319">The section "Configure Excel Services for Analysis Services integration" in [PowerPivot for SharePoint 2013 Installation](https://docs.microsoft.com/analysis-services/instances/install-windows/install-analysis-services-in-power-pivot-mode).</span></span>  
  
-   <span data-ttu-id="1dfe7-320">[Excel Services 데이터 모델 설정(SharePoint Server 2013)](https://technet.microsoft.com/library/jj219780.aspx).</span><span class="sxs-lookup"><span data-stu-id="1dfe7-320">[Manage Excel Services data model settings (SharePoint Server 2013)](https://technet.microsoft.com/library/jj219780.aspx).</span></span>  
  
###  <a name="provision-subscriptions-and-alerts"></a><a name="bkmk_provision_agent"></a><span data-ttu-id="1dfe7-321">구독 및 경고 프로 비전</span><span class="sxs-lookup"><span data-stu-id="1dfe7-321">Provision Subscriptions and Alerts</span></span>  
 <span data-ttu-id="1dfe7-322">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 구독 및 데이터 경고 기능을 사용하려면 SQL Server 에이전트 권한 구성이 필요할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-322">The [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] subscription and data alert features may require the configuration of SQL Server Agent permissions.</span></span> <span data-ttu-id="1dfe7-323">SQL Server 에이전트가 필요하고 SQL Server 에이전트 실행 확인을 나타내는 오류 메시지가 표시되는 경우 사용 권한을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-323">If you see an error message that indicates SQL Server Agent is required and you have verified SQL Server Agent is running, update the permissions.</span></span> <span data-ttu-id="1dfe7-324">서비스 애플리케이션 만들기 성공 페이지에서 **구독 및 경고 프로비전** 링크를 클릭하여 SQL Server 에이전트를 프로비전할 다른 페이지로 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-324">You can click the link **Provision Subscriptions and Alerts** on the create service application success page to go to another page for provisioning SQL Server Agent.</span></span> <span data-ttu-id="1dfe7-325">예를 들어 SQL Server 데이터베이스 인스턴스가 다른 시스템에 있는 경우와 같이 여러 시스템 경계를 이동하며 배포하는 경우 프로비전 단계가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-325">The provision step is needed if your deployment crosses machine boundaries, for example when the SQL Server database instance is on a different machine.</span></span> <span data-ttu-id="1dfe7-326">자세한 내용은 [SSRS 서비스 응용 프로그램에 대 한 구독 및 경고 프로 비전](../../reporting-services/install-windows/provision-subscriptions-and-alerts-for-ssrs-service-applications.md) 을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-326">For more information, see [Provision Subscriptions and Alerts for SSRS Service Applications](../../reporting-services/install-windows/provision-subscriptions-and-alerts-for-ssrs-service-applications.md)</span></span>  
  
### <a name="configure-e-mail-for-ssrs-service-applications"></a><span data-ttu-id="1dfe7-327">SSRS 서비스 애플리케이션에 대한 전자 메일 구성</span><span class="sxs-lookup"><span data-stu-id="1dfe7-327">Configure E-mail for SSRS Service Applications</span></span>  
 <span data-ttu-id="1dfe7-328">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 데이터 경고 기능은 전자 메일 메시지로 경고를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-328">The [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] data alerts feature sends alerts in e-mail messages.</span></span> <span data-ttu-id="1dfe7-329">전자 메일을 보내기 위해 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 서비스 애플리케이션을 구성하고 서비스 애플리케이션을 위한 전자 메일 배달 확장 프로그램을 수정해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-329">To send e-mail you may need to configure your [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service application and you may need to modify the e-mail delivery extension for the service application.</span></span> <span data-ttu-id="1dfe7-330">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 가입 기능을 위해 전자 메일 배달 확장 프로그램을 사용하려면 전자 메일 설정이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-330">If you plan to use the e-mail delivery extension for the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] subscription feature, the e-mail settings are required.</span></span> <span data-ttu-id="1dfe7-331">자세한 내용은 [Reporting Services 서비스 애플리케이션에 대한 메일 구성&#40;SharePoint 2010 및 SharePoint 2013&#41;](../../reporting-services/install-windows/configure-e-mail-for-a-reporting-services-service-application.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-331">For more information, see [Configure E-mail for a Reporting Services Service Application &#40;SharePoint 2010 and SharePoint 2013&#41;](../../reporting-services/install-windows/configure-e-mail-for-a-reporting-services-service-application.md)</span></span>  
  
### <a name="add-reporting-services-content-types-to-content-libraries"></a><span data-ttu-id="1dfe7-332">콘텐츠 라이브러리에 Reporting Services 콘텐츠 형식 추가</span><span class="sxs-lookup"><span data-stu-id="1dfe7-332">Add Reporting Services Content Types to Content Libraries</span></span>  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="1dfe7-333">는 공유 데이터 원본 파일(.rsds), 보고서 모델 파일(.smdl) 및 보고서 작성기 보고서 정의 파일(.rdl)을 관리하는 데 사용하는 미리 정의된 콘텐츠 형식을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-333">provides predefined content types that are used to manage shared data source (.rsds) files, report models (.smdl), and Report Builder report definition (.rdl) files.</span></span> <span data-ttu-id="1dfe7-334">**보고서 작성기 보고서**, **보고서 모델**및 **보고서 데이터 원본** 콘텐츠 형식을 라이브러리에 추가하면 해당 유형의 새 문서를 만들 수 있도록 **새로 만들기** 명령이 활성화됩니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-334">Adding a **Report Builder Report**, **Report Model**, and **Report Data Source** content type to a library enables the **New** command so that you can create new documents of that type.</span></span> <span data-ttu-id="1dfe7-335">자세한 내용은 [SharePoint 통합 모드&#41;에서 &#40;Reporting Services 라이브러리에 보고서 서버 콘텐츠 형식 추가 ](../../../2014/reporting-services/add-reporting-services-content-types-to-a-sharepoint-library.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-335">For more information, see [Add Report Server Content Types to a Library &#40;Reporting Services in SharePoint Integrated Mode&#41;](../../../2014/reporting-services/add-reporting-services-content-types-to-a-sharepoint-library.md).</span></span>  
  
### <a name="activate-the-report-server-file-sync-feature"></a><span data-ttu-id="1dfe7-336">보고서 서버 파일 동기화 기능 활성화</span><span class="sxs-lookup"><span data-stu-id="1dfe7-336">Activate the Report Server File sync Feature</span></span>  
 <span data-ttu-id="1dfe7-337">사용자가 게시된 보고서 항목을 SharePoint 문서 라이브러리에 직접 자주 업로드하는 경우 **보고서 서버 파일 동기화** 사이트 수준 기능이 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-337">If users will frequently upload published report items directly to SharePoint document libraries, the **Report Server File Sync** site level feature will be beneficial.</span></span> <span data-ttu-id="1dfe7-338">파일 동기화 기능은 보고서 서버 카탈로그를 문서 라이브러리의 항목과 자주 동기화합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-338">The file sync feature will synchronize the report server catalog with items in document libraries on a more frequent basis.</span></span> <span data-ttu-id="1dfe7-339">자세한 내용은 [SharePoint 중앙 관리에서 보고서 서버 파일 동기화 기능을 활성화](../../../2014/reporting-services/activate-report-server-file-sync-feature-sharepoint-central-administration.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-339">For more information, see [Activate the Report Server File Sync Feature in SharePoint Central Administration](../../../2014/reporting-services/activate-report-server-file-sync-feature-sharepoint-central-administration.md).</span></span>  
  
##  <a name="verify-the-installation"></a><a name="bkmk_verify_installation"></a><span data-ttu-id="1dfe7-340">설치 확인</span><span class="sxs-lookup"><span data-stu-id="1dfe7-340">Verify the installation</span></span>  
 <span data-ttu-id="1dfe7-341">다음은 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint 모드 배포를 확인하기 위해 권장되는 단계 및 절차입니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-341">The following are suggested steps and procedures to verify the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint mode deployment.</span></span>  
  
-   <span data-ttu-id="1dfe7-342">확인 항목 [Verify a Reporting Services Installation](../../reporting-services/install-windows/verify-a-reporting-services-installation.md)에서 SharePoint 섹션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-342">See the SharePoint section in the verification topic [Verify a Reporting Services Installation](../../reporting-services/install-windows/verify-a-reporting-services-installation.md).</span></span>  
  
-   <span data-ttu-id="1dfe7-343">SharePoint 문서 라이브러리에서 텍스트 상자(예: 제목)만 포함된 기본 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 보고서를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-343">In a SharePoint document library, create a basic [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] report that only contains a text box, for example a title.</span></span> <span data-ttu-id="1dfe7-344">이 보고서에는 어떠한 데이터 원본 또는 데이터 세트도 포함되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-344">The report does not contain any data sources or datasets.</span></span> <span data-ttu-id="1dfe7-345">이 보고서의 목적은 보고서 작성기를 열고, 기본 보고서를 작성하고, 보고서를 미리 볼 수 있는지 확인하기 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-345">The goal is to verify you can open Report Builder, build a basic report, and preview the report.</span></span>  
  
     <span data-ttu-id="1dfe7-346">보고서를 문서 라이브러리에 저장하고 라이브러리에서 보고서를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-346">Save the report to the document library and the run the report from the library.</span></span> <span data-ttu-id="1dfe7-347">보고서 작성기로 보고서를 만드는 방법은 [보고서 작성기 시작(보고서 작성기)](https://technet.microsoft.com/library/ms159221.aspx)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1dfe7-347">For more information on creating reports with Report Builder, see [Start Report Builder (Report Builder)](https://technet.microsoft.com/library/ms159221.aspx).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1dfe7-348">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1dfe7-348">See Also</span></span>  
 <span data-ttu-id="1dfe7-349">[Reporting Services SharePoint 모드용 PowerShell cmdlet](../../../2014/reporting-services/powershell-cmdlets-for-reporting-services-sharepoint-mode.md) </span><span class="sxs-lookup"><span data-stu-id="1dfe7-349">[PowerShell cmdlets for Reporting Services SharePoint Mode](../../../2014/reporting-services/powershell-cmdlets-for-reporting-services-sharepoint-mode.md) </span></span>  
 <span data-ttu-id="1dfe7-350">[Reporting Services 업그레이드 및 마이그레이션](../../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="1dfe7-350">[Upgrade and Migrate Reporting Services](../../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md) </span></span>  
 <span data-ttu-id="1dfe7-351">[콘텐츠 로드맵: SharePoint Server 및 SQL Server BI 설정 및 구성](https://technet.microsoft.com/library/dn205112.aspx) </span><span class="sxs-lookup"><span data-stu-id="1dfe7-351">[Content Roadmap: Set up and configure SharePoint Server and SQL Server BI](https://technet.microsoft.com/library/dn205112.aspx) </span></span>  
 <span data-ttu-id="1dfe7-352">[SQL Server 2012 버전에서 지 원하는 기능](https://go.microsoft.com/fwlink/?linkid=232473) </span><span class="sxs-lookup"><span data-stu-id="1dfe7-352">[Features Supported by the Editions of SQL Server 2012](https://go.microsoft.com/fwlink/?linkid=232473) </span></span>  
 [<span data-ttu-id="1dfe7-353">Reporting Services SharePoint Service 및 서비스 애플리케이션</span><span class="sxs-lookup"><span data-stu-id="1dfe7-353">Reporting Services SharePoint Service and Service Applications</span></span>](../../../2014/reporting-services/reporting-services-sharepoint-service-and-service-applications.md)
