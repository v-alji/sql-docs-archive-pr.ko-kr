---
title: SharePoint 용 Reporting Services 추가 기능 설치 또는 제거 (SharePoint 2010 및 SharePoint 2013) | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: c2804a9a-08ea-4f4a-805d-a2c19c68733d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: e30014ec823e89172b36f35d7f313568432a26f1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652634"
---
# <a name="install-or-uninstall-the-reporting-services-add-in-for-sharepoint-sharepoint-2010-and-sharepoint-2013"></a><span data-ttu-id="d1fe7-102">SharePoint용 Reporting Services 추가 기능 설치 또는 제거(SharePoint 2010 및 SharePoint 2013)</span><span class="sxs-lookup"><span data-stu-id="d1fe7-102">Install or Uninstall the Reporting Services Add-in for SharePoint (SharePoint 2010 and SharePoint 2013)</span></span>
  <span data-ttu-id="d1fe7-103">Sharepoint [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 서버에서 sharepoint 제품용 설치 패키지 추가 기능 (rsSharePoint.msi)을 실행 하 여 sharepoint [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 배포 내에서 기능을 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-103">Run the installation package [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Add-in for SharePoint products (rsSharePoint.msi) on SharePoint servers to enable [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] features within a SharePoint deployment.</span></span> <span data-ttu-id="d1fe7-104">이러한 기능에는 SharePoint 사이트에서 보고서, 보고서 모델, 데이터 원본 및 기타 보고서 서버 내용을 생성, 확인 및 관리할 수 있도록 Power View, 보고서 뷰어 웹 파트, URL 프록시 엔드포인트, 콘텐츠 형식 및 애플리케이션 페이지가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-104">Features include Power View, a Report Viewer Web Part, a URL proxy endpoint, content types, and application pages so that you can create, view, and manage reports, report models, data sources and other report server content on a SharePoint site.</span></span> <span data-ttu-id="d1fe7-105">SharePoint 제품용 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 추가 기능은 SharePoint 모드에서 실행되는 보고서 서버의 필수 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-105">The [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Add-in for SharePoint products is a required component for a report server that runs in SharePoint mode.</span></span> <span data-ttu-id="d1fe7-106">추가 기능은 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 설치 마법사에서 설치하거나 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 기능 팩에서 rsSharePoint.msi를 다운로드하여 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-106">The add-in can be installed from either the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] setup wizard or by downloading the rsSharePoint.msi from the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] feature pack.</span></span> <span data-ttu-id="d1fe7-107">추가 기능의 버전 목록 및 다운로드 페이지는 [SharePoint 제품용 Reporting Services 추가 기능 검색 위치](../../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-107">For a list of the versions of the add-in and download pages, see [Where to find the Reporting Services add-in for SharePoint Products](../../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md).</span></span>

||
|-|
|<span data-ttu-id="d1fe7-108">**[!INCLUDE[applies](../../includes/applies-md.md)]** Sharepoint 2013 &#124; SharePoint 2010</span><span class="sxs-lookup"><span data-stu-id="d1fe7-108">**[!INCLUDE[applies](../../includes/applies-md.md)]**  SharePoint 2013 &#124; SharePoint 2010</span></span>|

 <span data-ttu-id="d1fe7-109">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="d1fe7-109">**In this topic:**</span></span>

-   [<span data-ttu-id="d1fe7-110">필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="d1fe7-110">Prerequisites</span></span>](#bkmk_prereq)

-   [<span data-ttu-id="d1fe7-111">추가 기능과 함께 설치되는 항목</span><span class="sxs-lookup"><span data-stu-id="d1fe7-111">What Does The Add-in Install?</span></span>](#bkmk_whatinstalled)

-   [<span data-ttu-id="d1fe7-112">설치 방법 개요</span><span class="sxs-lookup"><span data-stu-id="d1fe7-112">Overview of the Installation Methods</span></span>](#bkmk_3ways_to_install)

-   [<span data-ttu-id="d1fe7-113">설치 파일을 사용 하 여 추가 기능을 설치 rsSharePoint.msi</span><span class="sxs-lookup"><span data-stu-id="d1fe7-113">Install the add-in using the installation file rsSharePoint.msi</span></span>](#bkmk_install_rssharepoint)

    -   [<span data-ttu-id="d1fe7-114">파일만 설치</span><span class="sxs-lookup"><span data-stu-id="d1fe7-114">Files-only installation</span></span>](#bkmk_files_only_installation)

-   [<span data-ttu-id="d1fe7-115">Reporting Services 추가 기능을 제거하는 방법</span><span class="sxs-lookup"><span data-stu-id="d1fe7-115">How to Remove the Reporting Services Add-in</span></span>](#bkmk_remove_addin)

-   [<span data-ttu-id="d1fe7-116">명령줄에서 rssharepoint.msi를 복구하는 방법</span><span class="sxs-lookup"><span data-stu-id="d1fe7-116">How to Repair rssharepoint.msi from the Command Line</span></span>](#bkmk_repair)

-   [<span data-ttu-id="d1fe7-117">설치 로그 파일</span><span class="sxs-lookup"><span data-stu-id="d1fe7-117">Setup Log Files</span></span>](#bkmk_logfiles)

-   [<span data-ttu-id="d1fe7-118">업그레이드</span><span class="sxs-lookup"><span data-stu-id="d1fe7-118">Upgrade</span></span>](#bkmk_upgrade)

-   [<span data-ttu-id="d1fe7-119">rsCustomAction.exe</span><span class="sxs-lookup"><span data-stu-id="d1fe7-119">RsCustomAction.exe</span></span>](#bkmk_rscustomaction)

##  <a name="prerequisites"></a><a name="bkmk_prereq"></a> <span data-ttu-id="d1fe7-120">필수 조건</span><span class="sxs-lookup"><span data-stu-id="d1fe7-120">Prerequisites</span></span>
 <span data-ttu-id="d1fe7-121">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 추가 기능 설치 작업은 보고서 서버를 SharePoint 제품 인스턴스와 통합하는 데 필요한 몇 가지 단계 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-121">Installing the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Add-in is one of several steps that are necessary for integrating a report server with an instance of a SharePoint product.</span></span> <span data-ttu-id="d1fe7-122">SharePoint 모드 사용을 위한 전체 요구 사항 집합에 대한 자세한 내용은 [Hardware and Software Requirements for Reporting Services in SharePoint Mode](../../../2014/sql-server/install/hardware-and-software-requirements-for-reporting-services-in-sharepoint-mode.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-122">For more information about the complete set of requirements for using SharePoint mode, see [Hardware and Software Requirements for Reporting Services in SharePoint Mode](../../../2014/sql-server/install/hardware-and-software-requirements-for-reporting-services-in-sharepoint-mode.md).</span></span> <span data-ttu-id="d1fe7-123">설치 및 구성에 대 한 자세한 내용은 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] [sharepoint 2013에 대 한 Sharepoint 모드 설치 Reporting Services](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2013.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-123">For more information on installing and configuring [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], see [Install Reporting Services SharePoint Mode for SharePoint 2013](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2013.md).</span></span>

-   <span data-ttu-id="d1fe7-124">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 를 웹 프런트 엔드 애플리케이션이 여러 개 있는 SharePoint 팜과 통합하는 경우 웹 서버 프런트 엔드가 있는 팜의 각 컴퓨터에 추가 기능을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-124">If you are integrating [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] with a SharePoint farm that has multiple Web front end applications, install the add-in to each computer in the farm that has a Web server front-end.</span></span> <span data-ttu-id="d1fe7-125">이 작업은 보고서 서버 내용에 액세스하는 데 사용될 웹 프런트 엔드에 대해서만 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-125">Do this only for Web front ends that will be used to access report server content.</span></span>

-   <span data-ttu-id="d1fe7-126">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 추가 기능을 설치하려면 컴퓨터의 관리자여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-126">To install the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Add-in, you must be an administrator on the computer.</span></span> <span data-ttu-id="d1fe7-127">예를 들어 명령줄에서 rsSharePoint.msi를 실행하려면 **관리자 권한으로 실행** 옵션을 사용하여 관리자 권한으로 명령 프롬프트를 열어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-127">For example if you are going to run the rsSharePoint.msi at the command prompt, you should open the command prompt with administrator privileges by using the **Run as administrator** option.</span></span>

-   <span data-ttu-id="d1fe7-128">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 추가 기능을 설치하려면 SharePoint 팜 관리자 그룹의 구성원여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-128">To install the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Add-in, you must be a member of the SharePoint Farm Administrators group.</span></span>

-   <span data-ttu-id="d1fe7-129">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 통합 기능을 활성화하려면 사이트 모음 관리자여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-129">You must be a Site Collection administrator to activate the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] integration feature.</span></span>

-   <span data-ttu-id="d1fe7-130">추가 기능을 사용 하는 예제 배포 다이어그램은 [SharePoint의 SQL SERVER BI 기능에 대 한 배포 토폴로지](../../sql-server/install/deployment-topologies-for-sql-server-bi-features-in-sharepoint.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-130">For diagrams of example deployments with the add-in, see [Deployment Topologies for SQL Server BI Features in SharePoint](../../sql-server/install/deployment-topologies-for-sql-server-bi-features-in-sharepoint.md).</span></span>

##  <a name="what-does-the-add-in-install"></a><a name="bkmk_whatinstalled"></a><span data-ttu-id="d1fe7-131">추가 기능을 설치 하는 방법</span><span class="sxs-lookup"><span data-stu-id="d1fe7-131">What Does The Add-in Install?</span></span>
 <span data-ttu-id="d1fe7-132">추가 기능 설치 과정은 두 단계로 구성되며, 표준 설치를 완료하면 두 단계 모두 자동으로 완료됩니다.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-132">The add-in setup process is composed of two phases, both are completed automatically when you complete a standard installation:</span></span>

-   <span data-ttu-id="d1fe7-133">첫 번째 단계에서는 파일을 적합한 폴더에 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-133">The first phase is to install files to the proper folders.</span></span> <span data-ttu-id="d1fe7-134">폴더는 SharePoint 배포를 위한 표준 폴더입니다.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-134">The folders are standard for SharePoint deployments.</span></span> <span data-ttu-id="d1fe7-135">이렇게 설치되는 파일 중 하나는 rsCustomAction.exe입니다.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-135">One of the files that is installed is rsCustomAction.exe.</span></span>

-   <span data-ttu-id="d1fe7-136">두 번째 설치 단계에서는 사용자 지정 동작 집합을 실행하여 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 파일을 SharePoint에 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-136">The second portion of the installation is to run a set of custom actions to register the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] files with SharePoint.</span></span> <span data-ttu-id="d1fe7-137">사용자 지정 동작은 rsCustomAction.exe로부터 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-137">The custom actions are run from rsCustomAction.exe.</span></span> <span data-ttu-id="d1fe7-138">이 exe 파일은 두 단계로 이뤄진 전체 설치가 완료될 때 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-138">The exe is removed when the full two phase installation completes.</span></span> <span data-ttu-id="d1fe7-139">**파일만** 설치를 실행할 수 있으며, 이 경우 설치 종료 시 rsCustomAction.exe가 실행되지 않고 드라이브에 남아 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-139">You can run a **files only** installation and rsCustomAction.exe is not run at the end of installation and it is left on the drive.</span></span>

## <a name="the-reporting-services-installation-order"></a><span data-ttu-id="d1fe7-140">Reporting Services 설치 순서</span><span class="sxs-lookup"><span data-stu-id="d1fe7-140">The Reporting Services Installation order</span></span>
 <span data-ttu-id="d1fe7-141">SharePoint 설치 전이나 후에 추가 기능을 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-141">The add-in can be installed before installing SharePoint or after SharePoint installation.</span></span> <span data-ttu-id="d1fe7-142">추가 기능은 SharePoint 배포 전 표준을 따르며 SharePoint 설치에 사용되는 위치에 파일을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-142">The add-in follows SharePoint pre-deployment standards and installs files in locations used by the SharePoint installation.</span></span>

> [!NOTE]
>  <span data-ttu-id="d1fe7-143">SharePoint 제품보다 추가 기능을 먼저 설치하면 팜에 새 서버를 추가할 경우 SharePoint 팜에서 Reporting Services 추가 기능을 구성하고 활성화한다는 이점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-143">The advantage of installing the add-in prior to the SharePoint product is that as new servers are added to the farm, the Reporting Services Add-in will be configured and activated by the SharePoint farm.</span></span>

 <span data-ttu-id="d1fe7-144">**SharePoint 2010**</span><span class="sxs-lookup"><span data-stu-id="d1fe7-144">**SharePoint 2010**</span></span>

-   <span data-ttu-id="d1fe7-145">SharePoint 2010 제품 준비 도구는 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 버전의 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 추가 기능을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-145">The SharePoint 2010 Products Preparation tool installs the [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] version of the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] add-in.</span></span> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<span data-ttu-id="d1fe7-146">에는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 기능에 필요한 새 버전의 추가 기능이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-146">includes a new version of the add-in that is required for [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] features.</span></span>

     <span data-ttu-id="d1fe7-147">SharePoint 제품 준비 도구를 실행할 경우에도 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 버전의 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 추가 기능을 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-147">If you run the SharePoint Products Preparation Tool, you still need to install the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] version of the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Add-in.</span></span>

-   <span data-ttu-id="d1fe7-148">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 버전의 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 추가 기능을 먼저 설치하면 SharePoint 제품 준비 도구를 실행할 때 준비 도구에서 새 버전이 감지되어 이전 버전의 추가 기능이 설치되지 않았음을 알리는 대화 상자가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-148">If you install [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] version of the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] add-in first, then when you run the SharePoint Products preparation tool you will see the following dialog indicating the preparation tool did not install the older version of the add-in as the newer version was detected.</span></span> <span data-ttu-id="d1fe7-149">이 동작은 정상적인 동작입니다.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-149">This is expected behavior</span></span>

     <span data-ttu-id="d1fe7-150">![SSRS 추가 기능이 이미 설치되었음](../../../2014/sql-server/install/media/rs-sharepointprereq-complete.gif "SSRS 추가 기능이 이미 설치되었음")</span><span class="sxs-lookup"><span data-stu-id="d1fe7-150">![SSRS add-in is already installed.](../../../2014/sql-server/install/media/rs-sharepointprereq-complete.gif "SSRS add-in is already installed.")</span></span>

 <span data-ttu-id="d1fe7-151">**SharePoint 2013**</span><span class="sxs-lookup"><span data-stu-id="d1fe7-151">**SharePoint 2013**</span></span>

 <span data-ttu-id="d1fe7-152">SharePoint 20103 제품 준비 도구는 **Not** [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] sharepoint 제품용 추가 기능을 설치 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-152">The SharePoint 20103 Products Preparation tool does **Not** install the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] add-in for SharePoint products.</span></span>

##  <a name="overview-of-the-installation-methods"></a><a name="bkmk_3ways_to_install"></a><span data-ttu-id="d1fe7-153">설치 방법 개요</span><span class="sxs-lookup"><span data-stu-id="d1fe7-153">Overview of the Installation Methods</span></span>
 <span data-ttu-id="d1fe7-154">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 다음 두 가지 방법 중 하나를 사용 하 여 SharePoint 제품용 추가 기능을 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-154">The [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Add-in for SharePoint products can be installed using one of the following two methods:</span></span>

-   <span data-ttu-id="d1fe7-155">**설치 마법사:** 에 대 한 새로운 ![정보](../../../2014/reporting-services/media/rs-fyinote.png "참고") [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] , 설치 마법사를 통해 추가 기능을 설치할 수 있습니다 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="d1fe7-155">**The installation wizard:** ![note](../../../2014/reporting-services/media/rs-fyinote.png "note")New with [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], the add-in can be installed by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installation wizard.</span></span> <span data-ttu-id="d1fe7-156">마법사의 **기능 선택** 페이지에서 **SharePoint 제품용 Reporting Services 추가 기능** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-156">Choose **Reporting Services Add-in for SharePoint Products** on the **Feature Selection** page of the wizard.</span></span>

-   <span data-ttu-id="d1fe7-157">**rsSharepoint.msi:** 추가 기능 파일은 설치 미디어에서 직접 설치하거나 다운로드한 후 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-157">**rsSharepoint.msi:** The add-in can be installed directly from the installation media or downloaded and installed.</span></span> <span data-ttu-id="d1fe7-158">rsSharepoint.msi는 그래픽 사용자 인터페이스 및 명령줄 설치를 둘 다 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-158">The rsSharepoint.msi supports both a graphical user interface and a command line installation.</span></span> <span data-ttu-id="d1fe7-159">먼저 승격된 권한으로 명령 프롬프트 창을 연 다음 명령줄에서 rsSharepoint.msi를 실행하여 관리자 권한으로 .msi를 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-159">You must run the .msi with administrator privileges by first opening a command prompt with elevated permissions, and then running the rsSharepoint.msi from the command line.</span></span> <span data-ttu-id="d1fe7-160">추가 기능 다운로드에 대한 자세한 내용은 [SharePoint 제품용 Reporting Services 추가 기능 검색 위치](../../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-160">For more information on downloading the add-in, see [Where to find the Reporting Services add-in for SharePoint Products](../../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md).</span></span>

    > [!NOTE]
    >  <span data-ttu-id="d1fe7-161">자동 명령줄 설치를 위해 **/q** 스위치를 사용할 경우 최종 사용자 사용권 계약이 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-161">If you use the **/q** switch for a silent command line installation, the end-user license agreement will not be displayed.</span></span> <span data-ttu-id="d1fe7-162">설치 방법에 관계없이 본 소프트웨어의 설치는 사용권 계약에 의해 제한되며 사용자는 사용권 계약을 준수해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-162">Regardless of the installation method, the use of this software is governed by a license agreement and you are responsible for complying with the license agreement.</span></span>

##  <a name="install-the-add-in-using-the-installation-file-rssharepointmsi"></a><a name="bkmk_install_rssharepoint"></a> <span data-ttu-id="d1fe7-163">rsSharePoint.msi 설치 파일을 사용하여 추가 기능 설치</span><span class="sxs-lookup"><span data-stu-id="d1fe7-163">Install the add-in using the installation file rsSharePoint.msi</span></span>
 <span data-ttu-id="d1fe7-164">이 섹션은 .msi 설치 마법사를 실행하거나 명령줄 설치를 실행하여 rssharepoint.msi를 직접 설치하는 방법과 관련이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-164">This section is related to installing the rssharepoint.msi directly, by either running the .msi installation wizard or a command line installation.</span></span> <span data-ttu-id="d1fe7-165">SQL Server 설치 마법사를 사용하여 추가 기능을 설치한 경우 이 단계를 수행할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-165">If you installed the add-in using the SQL Server installation Wizard, you do not need to follow these steps.</span></span>

 <span data-ttu-id="d1fe7-166">명령줄 스위치의 전체 목록은 다음 명령을 실행하여 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-166">You can see a full list of command line switches by running the following command:</span></span>

```
Rssharepoint.msi /?
```

1.  <span data-ttu-id="d1fe7-167">`rsSharepoint.msi`추가 기능에 대 한 설치 프로그램 ()을 다운로드 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-167">Download the Setup program (`rsSharepoint.msi`) for the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Add-in.</span></span> <span data-ttu-id="d1fe7-168">추가 기능 다운로드에 대한 자세한 내용은 [SharePoint 제품용 Reporting Services 추가 기능 검색 위치](../../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-168">For more information on downloading the add-in, see [Where to find the Reporting Services add-in for SharePoint Products](../../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md).</span></span>

2.  <span data-ttu-id="d1fe7-169">관리자 권한으로 `rsSharepoint.msi`를 실행하여 설치 마법사를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-169">As an administrator, run `rsSharepoint.msi` to run the Installation Wizard.</span></span> <span data-ttu-id="d1fe7-170">그러면 시작 페이지, 소프트웨어 사용 조건 및 등록 정보 페이지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-170">The wizard displays a Welcome page, the Software license terms, and a registration information page.</span></span> <span data-ttu-id="d1fe7-171">설치 프로그램은 다음 경로 아래에 폴더를 만들고 이 폴더에 파일을 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-171">Setup creates folders under the following path and copies files to the folders:</span></span>

     `%program files%\common files\Microsoft Shared\Web Server Extensions\14\`

     <span data-ttu-id="d1fe7-172">를 실행하거나</span><span class="sxs-lookup"><span data-stu-id="d1fe7-172">or</span></span>

     `%program files%\common files\Microsoft Shared\Web Server Extensions\15\`

3.  <span data-ttu-id="d1fe7-173">SharePoint 중앙 관리에서 보고서 서버 설정 및 기능 활성화를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-173">Configure the report server settings and feature activation in SharePoint Central Administration.</span></span> <span data-ttu-id="d1fe7-174">.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-174">.</span></span> <span data-ttu-id="d1fe7-175">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint 모드 설치 및 구성에 대한 자세한 내용은 [SharePoint 2010용 Reporting Services SharePoint 모드 설치](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-175">For more information on installing and configuring [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint mode, see [Install Reporting Services SharePoint Mode for SharePoint 2010](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md).</span></span>

###  <a name="files-only-installation"></a><a name="bkmk_files_only_installation"></a><span data-ttu-id="d1fe7-176">파일만 설치</span><span class="sxs-lookup"><span data-stu-id="d1fe7-176">Files-only installation</span></span>
 <span data-ttu-id="d1fe7-177">파일을 설치하고 설치 중 사용자 지정 동작 단계를 건너뛰려면 SKIPCA 옵션을 사용하여 명령줄에서 rssharepoint.msi를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-177">To install the files but skip the custom action phase of installation, run the rssharepoint.msi from the command line with the SKIPCA option:</span></span>

1.  <span data-ttu-id="d1fe7-178">**관리자 권한으로**명령 프롬프트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-178">Open a command prompt **with administrator permissions**.</span></span>

2.  <span data-ttu-id="d1fe7-179">다음 명령 실행:</span><span class="sxs-lookup"><span data-stu-id="d1fe7-179">Run the following command:</span></span>

    ```cmd
    Msiexec.exe /i rsSharePoint.msi SKIPCA=1
    ```

 <span data-ttu-id="d1fe7-180">설치 사용자 인터페이스가 열려 일반적인 방식으로 실행되고 `rsCustomAction.exe` 파일이 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-180">The installation user interface will open and run as normal and the `rsCustomAction.exe` file is installed.</span></span> <span data-ttu-id="d1fe7-181">그러나 설치가 끝난 후에도 .exe가 실행되지 않으며, 설치 완료 시 `rsCustomAction.exe`가 컴퓨터에 남아 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-181">However, the .exe will not run at the end of the installation and `rsCustomAction.exe` will remain on the computer when the installation is completed.</span></span>

### <a name="use-a-two-step-installation-to-troubleshoot-installation-issues-or-install-the-content-types"></a><span data-ttu-id="d1fe7-182">2단계 설치로 설치 문제 해결 또는 콘텐츠 형식 설치</span><span class="sxs-lookup"><span data-stu-id="d1fe7-182">Use a two-step installation to troubleshoot installation issues or install the content types</span></span>
 <span data-ttu-id="d1fe7-183">설치 중 오류가 발생하거나 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 콘텐츠 형식이 문서 라이브러리 설정에 나타나지 않는 경우, 명령줄에서 설치 프로그램을 두 단계 프로세스로 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-183">If you get errors during installation or the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] content types do not appear in the document library settings, you can run Setup as a two-step process from the command line:</span></span>

1.  <span data-ttu-id="d1fe7-184">**관리자 권한으로** 명령 프롬프트를 열고 이전 섹션에 설명된 대로 파일만 설치를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-184">Open a command prompt **with administrator permissions** and run a files only installation as described in the previous section.</span></span>

2.  <span data-ttu-id="d1fe7-185">사용자 지정 동작 실행 파일 실행:</span><span class="sxs-lookup"><span data-stu-id="d1fe7-185">Run the custom actions executable:</span></span>

    1.  <span data-ttu-id="d1fe7-186">`rsCustomAction.exe` 파일이 포함된 폴더로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-186">Navigate to the folder that contains the file `rsCustomAction.exe`.</span></span> <span data-ttu-id="d1fe7-187">이 파일은 추가 기능의 파일만 설치에 따라 컴퓨터에 복사됩니다.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-187">This file is copied to your computer by the files only installation of the add-in.</span></span> <span data-ttu-id="d1fe7-188">`rsCustomAction.exe`**% Temp%** 디렉터리에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-188">`rsCustomAction.exe` is located in the **%Temp%** directory.</span></span> <span data-ttu-id="d1fe7-189">파일로 이동하려면 명령 프롬프트에서 다음을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-189">To navigate to the file, type the following from the command prompt:</span></span>

         <span data-ttu-id="d1fe7-190">**CD %temp%**.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-190">**CD %temp%**.</span></span>

         <span data-ttu-id="d1fe7-191">이 파일은 다음 위치에 있습니다. **/Users\\<사용자 이름\>/AppData/Local/Temp**</span><span class="sxs-lookup"><span data-stu-id="d1fe7-191">The file should be located in: **\Users\\<your name\>\AppData\Local\Temp**</span></span>

    2.  <span data-ttu-id="d1fe7-192">다음 명령을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-192">Type the following command.</span></span> <span data-ttu-id="d1fe7-193">이 구성 단계를 마치는 데 몇 분 정도 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-193">This configuration step will take several minutes to finish.</span></span> <span data-ttu-id="d1fe7-194">이 프로세스 중 W3SVC 서비스가 다시 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-194">The W3SVC service will be restarted during this process.</span></span> <span data-ttu-id="d1fe7-195">프로그램이 파일을 복사하고, 구성 요소를 등록하고, SharePoint 제품 구성 마법사를 실행하면서 해당 상태 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-195">Several Status messages will be displayed as the program copies files, registers components, and runs the SharePoint Product Configuration Wizard.</span></span>

        ```cmd
        rsCustomAction.exe /i
        ```

    3.  <span data-ttu-id="d1fe7-196">변경 내용을 적용하는 데 걸리는 시간은 서버 환경에 따라 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-196">The amount of time it takes for the changes to take effect may vary, depending on your server environment.</span></span> <span data-ttu-id="d1fe7-197">또한 빠른 업데이트를 적용하기 위해 **iisreset** 를 실행할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-197">You can also run **iisreset** to force a quicker update.</span></span>

### <a name="quiet-installation-for-scripting"></a><span data-ttu-id="d1fe7-198">스크립팅을 위한 자동 설치</span><span class="sxs-lookup"><span data-stu-id="d1fe7-198">Quiet installation for scripting</span></span>
 <span data-ttu-id="d1fe7-199">대화 상자 또는 경고가 표시 되지 않는 "자동" 설치에 **/q** 또는 **/quiet** 스위치를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-199">You can use the **/q** or **/quiet** switches for a "quiet" installation that will not display any dialogs or warnings.</span></span> <span data-ttu-id="d1fe7-200">자동 설치는 추가 기능 설치를 스크립팅하려는 경우에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-200">The quiet installation is useful if you want to script the installation of the add-in.</span></span>

> [!NOTE]
>  <span data-ttu-id="d1fe7-201">자동 명령줄 설치를 위해 **/q** 스위치를 사용할 경우 최종 사용자 사용권 계약이 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-201">If you use the **/q** switch for a silent command line installation, the end-user license agreement will not be displayed.</span></span> <span data-ttu-id="d1fe7-202">설치 방법에 관계없이 본 소프트웨어의 설치는 사용권 계약에 의해 제한되며 사용자는 사용권 계약을 준수해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-202">Regardless of the installation method, the use of this software is governed by a license agreement and you are responsible for complying with the license agreement.</span></span>

 <span data-ttu-id="d1fe7-203">자동 설치를 수행하려면</span><span class="sxs-lookup"><span data-stu-id="d1fe7-203">To perform a quiet installation:</span></span>

1.  <span data-ttu-id="d1fe7-204">**관리자 권한으로**명령 프롬프트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-204">Open a command prompt **with administrator permissions**.</span></span>

2.  <span data-ttu-id="d1fe7-205">다음 명령 실행:</span><span class="sxs-lookup"><span data-stu-id="d1fe7-205">Run the following command:</span></span>

    ```cmd
    Msiexec.exe /i rsSharePoint.msi /q
    ```

##  <a name="how-to-remove-the-reporting-services-add-in"></a><a name="bkmk_remove_addin"></a><span data-ttu-id="d1fe7-206">Reporting Services 추가 기능을 제거 하는 방법</span><span class="sxs-lookup"><span data-stu-id="d1fe7-206">How to Remove the Reporting Services Add-in</span></span>
 <span data-ttu-id="d1fe7-207">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Windows 제어판이나 명령줄에서 SharePoint 제품용 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 추가 기능을 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-207">You can uninstall the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Add-in for SharePoint Products from [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows control panel or the command line.</span></span>

1.  <span data-ttu-id="d1fe7-208">제어판을 사용하면 현재 컴퓨터에서 파일 전체 제거가 실행되며 **또한** SharePoint 팜에서 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 개체 및 기능이 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-208">Using control panel will run a complete uninstall of the files on the current computer **AND** it will remove the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] object and features from the SharePoint farm.</span></span> <span data-ttu-id="d1fe7-209">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 개체 및 기능이 제거되면 더 이상 보고서를 검토하고 업데이트할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-209">When the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] object and features are removed you can no longer review and update reports.</span></span>

2.  <span data-ttu-id="d1fe7-210">추가 기능을 제거하기 위한 명령줄 방법을 사용하면 LocalOnly 매개 변수를 사용하여 로컬 컴퓨터에서는 추가 기능 파일만 제거하고 팜의 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 개체 및 기능은 변경되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-210">The command line method to uninstall the add-in allows you to use the LocalOnly parameter to only remove the add-in files from the local computer and the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] object and features in the farm will not be changed.</span></span>

 <span data-ttu-id="d1fe7-211">추가 기능을 제거하면 보고서 서버에서 보고서를 처리하는 데 사용되는 서버 통합 기능이 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-211">Uninstalling the add-in will remove server integration features that are used to process reports on a report server.</span></span> <span data-ttu-id="d1fe7-212">SharePoint 중앙 관리의 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 페이지 및 기타 사용자 지정 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 페이지도 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-212">It will also remove the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] pages from SharePoint Central Administration and other custom [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] pages.</span></span> <span data-ttu-id="d1fe7-213">SharePoint 사이트에서 더 이상 사용하지 않는 보고서와 다른 보고서 서버 항목을 제거할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-213">You may also want to remove any reports and other report server items that you no longer use on the affected SharePoint sites.</span></span> <span data-ttu-id="d1fe7-214">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 추가 기능을 제거한 후에는 이러한 항목이 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-214">They will not run after the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Add-in is removed.</span></span>

 <span data-ttu-id="d1fe7-215">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 추가 기능을 제거하려면 [!INCLUDE[SPF2010](../../includes/spf2010-md.md)] 또는 [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] 설치가 실행 중이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-215">To uninstall the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Add-in, you must have a [!INCLUDE[SPF2010](../../includes/spf2010-md.md)] or [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] installation still running.</span></span> <span data-ttu-id="d1fe7-216">SharePoint 2010을 먼저 제거한 경우 다시 설치해야 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 추가 기능을 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-216">If you uninstall the SharePoint 2010 first, you must reinstall it to uninstall the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Add-in.</span></span>

 <span data-ttu-id="d1fe7-217">추가 기능을 제거하는 단계는 독립 실행형 서버 및 서버 팜 모두에서 같습니다.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-217">The steps for uninstalling the add-in are the same for both stand-alone servers and server farms.</span></span> <span data-ttu-id="d1fe7-218">설치 프로그램에서는 설치 중 추가된 프로그램 파일과 모든 구성 설정을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-218">Setup will remove program files and any configuration settings that were added during installation.</span></span>

 <span data-ttu-id="d1fe7-219">추가 기능을 제거해도 다음 항목은 제거되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-219">Uninstalling the add-in will not remove the following:</span></span>

-   <span data-ttu-id="d1fe7-220">SharePoint 구성 및 콘텐츠 데이터베이스에 액세스하는 데 사용되는 보고서 서버 서비스 계정에 대해 생성된 로그인.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-220">Logins created for the Report Server service account that is used to access the SharePoint configuration and content databases.</span></span> <span data-ttu-id="d1fe7-221">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] SharePoint 데이터베이스를 호스트 하는 데 사용 되는 인스턴스에서 보고서 서버 서비스 계정에 대 한 로그인을 모두 삭제 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-221">You must delete any logins for the Report Server service account from the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] instance used to host the SharePoint databases.</span></span>

-   <span data-ttu-id="d1fe7-222">보고서 사용자에 대해 만든 사용 권한 또는 그룹.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-222">Permissions or groups that you created for report users.</span></span> <span data-ttu-id="d1fe7-223">보고서 서버 기능에 대한 액세스 권한을 부여하기 위해 사용자 지정 권한 수준이나 SharePoint 그룹을 만든 경우 더 이상 필요하지 않은 사용 권한을 취소해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-223">If you created custom permission levels or SharePoint groups to grant access to report server features, you should revoke any permissions that are no longer required.</span></span>

-   <span data-ttu-id="d1fe7-224">보고서 정의 파일(.rdl), 공유 데이터 원본 파일(.rsds) 및 게시된 보고서 항목 파일(.rsc)을 비롯하여 SharePoint 라이브러리에 업로드한 데이터 파일.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-224">Data files that you uploaded to a SharePoint library, including report definition (.rdl), shared data source (.rsds), and published report items (.rsc) files.</span></span> <span data-ttu-id="d1fe7-225">이러한 파일의 경우 삭제되지는 않지만 더 이상 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-225">They are not deleted, but they will no longer run.</span></span> <span data-ttu-id="d1fe7-226">해당 파일은 직접 삭제해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-226">You must delete the files manually.</span></span>

-   <span data-ttu-id="d1fe7-227">설치 프로그램에서는 보고서 서버 데이터베이스를 삭제하지 않으며 통합 작업에 사용되는 보고서 서버 인스턴스를 수정하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-227">Setup will not delete the report server database or modify the report server instance that was used for integrated operations.</span></span>

### <a name="to-uninstall-from-windows-control-panel"></a><span data-ttu-id="d1fe7-228">Windows 제어판에서 제거하려면</span><span class="sxs-lookup"><span data-stu-id="d1fe7-228">To Uninstall from Windows Control Panel</span></span>
 <span data-ttu-id="d1fe7-229">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 제어판에서 마법사를 시작하고 추가 기능을 제거하려면</span><span class="sxs-lookup"><span data-stu-id="d1fe7-229">To start the wizard from [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Control Panel and remove the add-in:</span></span>

1.  <span data-ttu-id="d1fe7-230">제어판의 **프로그램**에서 **프로그램 제거**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-230">In Control Panel, in **Programs**, select **Uninstall a Program**</span></span>

2.  <span data-ttu-id="d1fe7-231">**SharePoint용 Microsoft SQL Server RS 추가 기능**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-231">Select **Microsoft SQL Server RS Add-in for SharePoint**.</span></span> <span data-ttu-id="d1fe7-232">명령 프롬프트에서 스위치 없이 **rssharepoint.msi** 를 실행하여 제거 마법사를 시작할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-232">You can also start the uninstall wizard by running **rssharepoint.msi** from the command prompt with no switches.</span></span>

3.  <span data-ttu-id="d1fe7-233">**제거**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-233">Click **Remove**.</span></span>

### <a name="uninstall-from-the-command-line"></a><span data-ttu-id="d1fe7-234">명령줄에서 제거</span><span class="sxs-lookup"><span data-stu-id="d1fe7-234">Uninstall from the command line</span></span>
 <span data-ttu-id="d1fe7-235">명령줄에서 추가 기능을 제거하려면</span><span class="sxs-lookup"><span data-stu-id="d1fe7-235">To uninstall the add-in from the command line:</span></span>

1.  <span data-ttu-id="d1fe7-236">**관리자 권한으로**명령 프롬프트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-236">Open a command prompt **with administrator permissions**.</span></span>

2.  <span data-ttu-id="d1fe7-237">다음 명령 실행:</span><span class="sxs-lookup"><span data-stu-id="d1fe7-237">Run the following command:</span></span>

    ```cmd
    msiexec.exe /uninstall rsSharePoint.msi
    ```

3.  <span data-ttu-id="d1fe7-238">확인 메시지 상자가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-238">You will see a confirmation message box.</span></span> <span data-ttu-id="d1fe7-239">**예**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-239">Click **Yes**.</span></span>

### <a name="uninstall-the-add-in-from-the-local-server-only"></a><span data-ttu-id="d1fe7-240">로컬 서버에서만 추가 기능 제거</span><span class="sxs-lookup"><span data-stu-id="d1fe7-240">Uninstall the add-in from the local server only</span></span>
 <span data-ttu-id="d1fe7-241">이전 방법으로 추가 기능을 제거하면 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 기능 및 개체가 팜에서 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-241">The previous methods of uninstalling the add-in will remove the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] features and object from the farm.</span></span> <span data-ttu-id="d1fe7-242">다중 서버 팜에서 로컬 컴퓨터의 추가 기능만 제거하고 SharePoint 팜은 계속 작동하게 유지하려면 다음 단계를 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-242">If you have a multi-server farm and want to uninstall the add-in from only the local computer and leave the SharePoint farm in a functional state, complete the following steps:</span></span>

1.  <span data-ttu-id="d1fe7-243">**관리자 권한으로**명령 프롬프트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-243">Open a command prompt **with administrator permissions**.</span></span>

2.  <span data-ttu-id="d1fe7-244">다음 명령 실행:</span><span class="sxs-lookup"><span data-stu-id="d1fe7-244">Run the following command:</span></span>

    ```cmd
    Msiexec.exe /uninstall rsSharePoint.msi LocalOnly=1
    ```

 <span data-ttu-id="d1fe7-245">이 옵션은 로컬 컴퓨터에서만 SharePoint에서 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 구성 요소의 등록을 해제하고 파일을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-245">This will unregister the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] components from SharePoint and remove the files, but for the local computer only.</span></span>

 <span data-ttu-id="d1fe7-246">SharePoint에서 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 기능의 등록을 해제하지만 나중에 사용할 수 있도록 디스크에 파일을 남겨 두려면 다음 단계를 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-246">If you want to unregister the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] features from SharePoint but leave the files on the disk for use later, complete the following steps:</span></span>

1.  <span data-ttu-id="d1fe7-247">**관리자 권한으로**명령 프롬프트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-247">Open a command prompt **with administrator permissions**.</span></span>

2.  <span data-ttu-id="d1fe7-248">다음 명령 실행:</span><span class="sxs-lookup"><span data-stu-id="d1fe7-248">Run the following command:</span></span>

    ```cmd
    rsCustomAction.exe /p
    ```

 <span data-ttu-id="d1fe7-249">SkipCA=1을 사용하여 .msi를 설치하고 rscusstomaction.exe를 사용할 수 있다는 가정 하에 위의 단계가 진행됩니다.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-249">The above steps assume you completed an installation of the .msi with SkipCA=1 and the rscusstomaction.exe is available.</span></span> <span data-ttu-id="d1fe7-250">자세한 내용은 파일만 설치 설명 섹션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-250">For more information, see the section describing the files only installation.</span></span>

##  <a name="how-to-repair-rssharepointmsi-from-the-command-line"></a><a name="bkmk_repair"></a><span data-ttu-id="d1fe7-251">명령줄에서 rssharepoint.msi를 복구 하는 방법</span><span class="sxs-lookup"><span data-stu-id="d1fe7-251">How to Repair rssharepoint.msi from the Command Line</span></span>
 <span data-ttu-id="d1fe7-252">명령줄을 사용하여 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 추가 기능을 복구하거나 제거하려면 다음 단계를 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-252">To repair or uninstall the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] add-in using the command line, complete the following steps:</span></span>

1.  <span data-ttu-id="d1fe7-253">**관리자 권한으로**명령 프롬프트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-253">Open a command prompt **with administrator permissions**.</span></span>

2.  <span data-ttu-id="d1fe7-254">다음 명령 실행:</span><span class="sxs-lookup"><span data-stu-id="d1fe7-254">Run the following command:</span></span>

    ```cmd
    msiexec.exe /f rssharepoint.msi
    ```

##  <a name="setup-log-files"></a><a name="bkmk_logfiles"></a><span data-ttu-id="d1fe7-255">설치 로그 파일</span><span class="sxs-lookup"><span data-stu-id="d1fe7-255">Setup Log Files</span></span>
 <span data-ttu-id="d1fe7-256">설치 프로그램을 실행하면 **%temp%** 폴더의 로그 파일에 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 추가 기능을 설치한 사용자에 대한 정보가 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-256">When Setup runs, it logs information to a log file in the **%temp%** folder for the user who installed the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Add-in.</span></span> <span data-ttu-id="d1fe7-257">예: **c:\Users \\<username \> \AppData\Local\Temp** . 파일 이름은 RS_SP_ (예: **RS_SP_0 .log**)입니다 \*\* \<number> .\*\*</span><span class="sxs-lookup"><span data-stu-id="d1fe7-257">For example **c:\Users\\<username\>\AppData\Local\Temp** .The file name is **RS_SP_\<number>.log**, for example **RS_SP_0.log**.</span></span> <span data-ttu-id="d1fe7-258">로그의 각 오류는 문자열 "SSRSCustomActionError"로 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-258">Each error in the log starts with the string "SSRSCustomActionError".</span></span>

> [!NOTE]
>  <span data-ttu-id="d1fe7-259">AppData는 Windows 운영 체제의 숨겨진 폴더입니다.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-259">AppData is a hidden folder in the Windows operating system.</span></span> <span data-ttu-id="d1fe7-260">숨겨진 파일과 폴더를 표시할 수 있도록 Windows 탐색기 폴더 설정을 수정해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-260">You may need to modify your Windows Explorer folder settings so you can see hidden files and folders.</span></span>

#### <a name="view-a-log-file-with-windows-notepad"></a><span data-ttu-id="d1fe7-261">Windows 메모장으로 로그 파일 보기</span><span class="sxs-lookup"><span data-stu-id="d1fe7-261">View a log file with Windows Notepad</span></span>

1.  <span data-ttu-id="d1fe7-262">다음 명령을 수행하면 명령 프롬프트 경로가 변경되고 rs 로그 파일이 나열된 후 파일 중 하나가 Windows 메모장으로 열립니다.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-262">The following commands will change the command prompt path, list the rs log files and then open one of the files with Windows Notepad:</span></span>

    ```cmd
    cd %temp%
    ```

    ```cmd
    dir rs_sp*.log
    ```

    ```cmd
    notepad rs_sp_3.log
    ```

#### <a name="view-a-log-file-with-powershell"></a><span data-ttu-id="d1fe7-263">PowerShell에서 로그 파일 보기</span><span class="sxs-lookup"><span data-stu-id="d1fe7-263">View a Log file with PowerShell</span></span>

1.  <span data-ttu-id="d1fe7-264">파일에서 "ssrscustomactionerror"가 포함된 필터링된 행 목록을 반환하려면 SharePoint 관리 셸에서 다음 명령을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-264">Type the following command from the SharePoint Management Shell to return a filtered list of rows from the file, that contain "ssrscustomactionerror":</span></span>

    ```powershell
    Get-Content -Path C:\Users\<UserName\AppData\Local\Temp\rs_sp_0.log | Select-String "ssrscustomactionerror"
    ```

2.  <span data-ttu-id="d1fe7-265">출력은 다음과 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-265">The output will look similar to the following:</span></span>

     <span data-ttu-id="d1fe7-266">`2011-05-23 12:40:12: SSRSCustomActionError: SharePoint is installed, but not configured`.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-266">`2011-05-23 12:40:12: SSRSCustomActionError: SharePoint is installed, but not configured`.</span></span>

##  <a name="upgrade"></a><a name="bkmk_upgrade"></a><span data-ttu-id="d1fe7-267">업그레이드할</span><span class="sxs-lookup"><span data-stu-id="d1fe7-267">Upgrade</span></span>
 <span data-ttu-id="d1fe7-268">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 추가 기능이 이미 설치되어 있으면 현재 버전으로 업그레이드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-268">If you have an existing installation of the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Add-in, you can upgrade to the current version.</span></span> <span data-ttu-id="d1fe7-269">추가 기능 설치 프로그램이 기존 버전을 감지하여 업데이트할 것인지 확인하는 메시지를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-269">The add-in setup will detect the existing version and prompt you to confirm the update.</span></span> <span data-ttu-id="d1fe7-270">메시지는 다음과 유사합니다.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-270">The message will be similar to the following:</span></span>

 <span data-ttu-id="d1fe7-271">**시스템에서이 제품의 하위 버전이 검색 되었습니다. 기존 설치를 업그레이드 하 시겠습니까?**</span><span class="sxs-lookup"><span data-stu-id="d1fe7-271">**A Lower version of this product has been detected on your system. Would you like to upgrade your existing installation?**</span></span>

 <span data-ttu-id="d1fe7-272">확인하면 이전 버전의 추가 기능이 제거되고 새 버전이 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-272">If you confirm, the older version of the add-in will be removed and then the new version will be installed.</span></span>

 <span data-ttu-id="d1fe7-273">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 추가 기능은 인스턴스를 인식하지 못하므로</span><span class="sxs-lookup"><span data-stu-id="d1fe7-273">Note that the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Add-in is not instance-aware.</span></span> <span data-ttu-id="d1fe7-274">컴퓨터에서 하나의 추가 기능 인스턴스만 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-274">You can only have one instance of the add-in on a computer.</span></span> <span data-ttu-id="d1fe7-275">따라서 다른 버전을 현재 버전과 함께 실행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-275">You cannot run different versions side-by-side the current version.</span></span>

##  <a name="rscustomactionexe"></a><a name="bkmk_rscustomaction"></a><span data-ttu-id="d1fe7-276">RsCustomAction.exe</span><span class="sxs-lookup"><span data-stu-id="d1fe7-276">RsCustomAction.exe</span></span>
 <span data-ttu-id="d1fe7-277">다음 표에서는 rscustomaction.exe 스위치를 요약해서 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-277">The following table summarizes the rscustomaction.exe switches:</span></span>

|<span data-ttu-id="d1fe7-278">스위치</span><span class="sxs-lookup"><span data-stu-id="d1fe7-278">Switch</span></span>|<span data-ttu-id="d1fe7-279">Description</span><span class="sxs-lookup"><span data-stu-id="d1fe7-279">Description</span></span>|
|------------|-----------------|
|<span data-ttu-id="d1fe7-280">i</span><span class="sxs-lookup"><span data-stu-id="d1fe7-280">i</span></span>|<span data-ttu-id="d1fe7-281">사용자 지정 동작을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-281">Install the custom actions.</span></span> <span data-ttu-id="d1fe7-282">그러면 SharePoint의 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 구성 요소가 등록되고</span><span class="sxs-lookup"><span data-stu-id="d1fe7-282">This will register the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] components in SharePoint.</span></span> <span data-ttu-id="d1fe7-283">W3SVCservice가 다시 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-283">This will restart the W3SVCservice.</span></span>|
|<span data-ttu-id="d1fe7-284">r</span><span class="sxs-lookup"><span data-stu-id="d1fe7-284">r</span></span>|<span data-ttu-id="d1fe7-285">Repair</span><span class="sxs-lookup"><span data-stu-id="d1fe7-285">Repair</span></span>|
|<span data-ttu-id="d1fe7-286">u</span><span class="sxs-lookup"><span data-stu-id="d1fe7-286">u</span></span>|<span data-ttu-id="d1fe7-287">제거.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-287">Uninstall.</span></span> <span data-ttu-id="d1fe7-288">이 스위치는 전체 SharePoint 팜에서 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 구성 요소의 등록을 해제하지만 디스크에 파일을 남겨 둡니다.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-288">This will unregister the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] components from the entire SharePoint farm but leave the files on disk.</span></span> <span data-ttu-id="d1fe7-289">W3SVCservice가 다시 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-289">This will restart the W3SVCservice.</span></span>|
|<span data-ttu-id="d1fe7-290">p</span><span class="sxs-lookup"><span data-stu-id="d1fe7-290">p</span></span>|<span data-ttu-id="d1fe7-291">로컬 제거.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-291">Local uninstall.</span></span> <span data-ttu-id="d1fe7-292">이 스위치는 로컬 컴퓨터에서만 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 구성 요소의 등록을 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-292">This will unregister the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] components from only the local computer.</span></span> <span data-ttu-id="d1fe7-293">파일은 디스크에 유지되고</span><span class="sxs-lookup"><span data-stu-id="d1fe7-293">The files will remain on disk.</span></span> <span data-ttu-id="d1fe7-294">W3SVCservice가 다시 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-294">This will restart the W3SVCservice.</span></span>|
|<span data-ttu-id="d1fe7-295">t</span><span class="sxs-lookup"><span data-stu-id="d1fe7-295">t</span></span>|<span data-ttu-id="d1fe7-296">SQL Server [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 2005에만 해당</span><span class="sxs-lookup"><span data-stu-id="d1fe7-296">SQL Server [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 2005 only.</span></span> <span data-ttu-id="d1fe7-297">스위치는 보고서 서버에 보고서 서버 데이터베이스에 대한 작업 연결이 있는지를 테스트합니다.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-297">The switch tests if the report server has a working connection to the report server database.</span></span>|

## <a name="configuring-reporting-services"></a><span data-ttu-id="d1fe7-298">Reporting Services 구성</span><span class="sxs-lookup"><span data-stu-id="d1fe7-298">Configuring Reporting Services</span></span>
 <span data-ttu-id="d1fe7-299">모든 필요한 컴퓨터에 추가 기능을 설치한 다음에는 SharePoint 중앙 관리에서 보고서 서버를 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-299">After you have installed the add-in on all the necessary computers, you need to configure the report server from SharePoint Central Administration.</span></span> <span data-ttu-id="d1fe7-300">필요한 단계는 설치된 여러 기술의 순서에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="d1fe7-300">The steps that are needed depend on the order which the different technologies were installed.</span></span> <span data-ttu-id="d1fe7-301">자세한 내용은 sharepoint [2010에 대 한 Sharepoint 모드 설치 Reporting Services](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md) 및 [Reporting Services 보고서 서버 &#40;sharepoint 모드](../../../2014/reporting-services/reporting-services-report-server-sharepoint-mode.md) 를 참조 하세요&#41;</span><span class="sxs-lookup"><span data-stu-id="d1fe7-301">For more information, see [Install Reporting Services SharePoint Mode for SharePoint 2010](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md) and [Reporting Services Report Server &#40;SharePoint Mode&#41;](../../../2014/reporting-services/reporting-services-report-server-sharepoint-mode.md)</span></span>

## <a name="see-also"></a><span data-ttu-id="d1fe7-302">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d1fe7-302">See Also</span></span>
 <span data-ttu-id="d1fe7-303">Sharepoint 2010 [Reporting Services 보고서 서버 &#40;Sharepoint 모드](../../../2014/reporting-services/reporting-services-report-server-sharepoint-mode.md) [에 대 한 Reporting Services sharepoint 모드 설치](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md)&#41;</span><span class="sxs-lookup"><span data-stu-id="d1fe7-303">[Install Reporting Services SharePoint Mode for SharePoint 2010](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md) [Reporting Services Report Server &#40;SharePoint Mode&#41;](../../../2014/reporting-services/reporting-services-report-server-sharepoint-mode.md)</span></span>
