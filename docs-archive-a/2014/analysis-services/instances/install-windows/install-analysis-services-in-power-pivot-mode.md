---
title: SharePoint용 PowerPivot 2013 설치 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: d3310562-82c1-454f-9c48-33a241749238
author: minewiskan
ms.author: owend
ms.openlocfilehash: 74d0e1cc78b4004a832a312f9f8ae8deb23904f0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729948"
---
# <a name="powerpivot-for-sharepoint-2013-installation"></a><span data-ttu-id="33e9b-102">PowerPivot for SharePoint 2013 Installation</span><span class="sxs-lookup"><span data-stu-id="33e9b-102">PowerPivot for SharePoint 2013 Installation</span></span>
  <span data-ttu-id="33e9b-103">이 항목의 절차에서는 SharePoint 배포 모드에서 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 서버의 단일 서버 설치하는 단계를 안내합니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-103">The procedures in this topic guide you through a single server installation of a [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] server in SharePoint deployment mode.</span></span> <span data-ttu-id="33e9b-104">이 단계에는 SharePoint 2013 중앙 관리를 사용하는 SQL Server 설치 마법사 및 구성 태스크가 포합됩니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-104">The steps include running the SQL Server installation wizard as well as configuration tasks that use SharePoint 2013 Central Administration.</span></span>  
  
 <span data-ttu-id="33e9b-105">**[!INCLUDE[applies](../../../includes/applies-md.md)]** SharePoint 2013 | SharePoint 201</span><span class="sxs-lookup"><span data-stu-id="33e9b-105">**[!INCLUDE[applies](../../../includes/applies-md.md)]**  SharePoint 2013 | SharePoint 201</span></span>  
  
 <span data-ttu-id="33e9b-106">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="33e9b-106">**In this topic:**</span></span>  
  
 [<span data-ttu-id="33e9b-107">배경</span><span class="sxs-lookup"><span data-stu-id="33e9b-107">Background</span></span>](#bkmk_background)  
  
 [<span data-ttu-id="33e9b-108">필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="33e9b-108">Prerequisites</span></span>](#bkmk_prereq)  
  
 [<span data-ttu-id="33e9b-109">1단계: SharePoint용 PowerPivot 설치</span><span class="sxs-lookup"><span data-stu-id="33e9b-109">Step 1: Install PowerPivot for SharePoint</span></span>](#InstallSQL)  
  
 [<span data-ttu-id="33e9b-110">2단계: Basic Analysis Services SharePoint 통합 구성</span><span class="sxs-lookup"><span data-stu-id="33e9b-110">Step 2: Configure Basic Analysis Services SharePoint Integration</span></span>](#bkmk_config)  
  
 [<span data-ttu-id="33e9b-111">3단계 통합 확인</span><span class="sxs-lookup"><span data-stu-id="33e9b-111">Step 3: Verify the Integration</span></span>](#bkmk_verify)  
  
 [<span data-ttu-id="33e9b-112">Analysis Services 액세스를 허용하도록 Windows 방화벽 구성</span><span class="sxs-lookup"><span data-stu-id="33e9b-112">Configure the Windows Firewall to Allow Analysis Services Access</span></span>](#bkmk_firewall)  
  
 [<span data-ttu-id="33e9b-113">통합 문서 업그레이드 및 예약된 데이터 새로 고침</span><span class="sxs-lookup"><span data-stu-id="33e9b-113">Upgrade Workbooks and Scheduled Data Refresh</span></span>](#bkmk_upgrade_workbook)  
  
 [<span data-ttu-id="33e9b-114">단일 서버 설치 외-PowerPivot for Microsoft SharePoint</span><span class="sxs-lookup"><span data-stu-id="33e9b-114">Beyond the Single-Server Installation -PowerPivot for Microsoft SharePoint</span></span>](#bkmk_multiple_servers)  
  
##  <a name="background"></a><a name="bkmk_background"></a> <span data-ttu-id="33e9b-115">배경</span><span class="sxs-lookup"><span data-stu-id="33e9b-115">Background</span></span>  
 <span data-ttu-id="33e9b-116">SharePoint용 PowerPivot은 SharePoint 2013 팜에서 PowerPivot 데이터 액세스를 제공하는 중간 계층 및 백 엔드 서비스의 모음입니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-116">PowerPivot for SharePoint is a collection of middle-tier and backend services that provide PowerPivot data access in a SharePoint 2013 farm.</span></span>  
  
-   <span data-ttu-id="33e9b-117">**백 엔드 서비스:** PowerPivot for Excel을 사용하여 분석 데이터가 포함된 통합 문서를 만드는 경우 서버 환경에서 이러한 데이터에 액세스하려면 SharePoint용 PowerPivot이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-117">**Backend services:** If you use PowerPivot for Excel to create workbooks that contain analytical data, you must have PowerPivot for SharePoint to access that data in a server environment.</span></span> <span data-ttu-id="33e9b-118">SharePoint Server 2013이 설치된 컴퓨터 또는 SharePoint 소프트웨어가 설치되지 않은 다른 컴퓨터에서 SQL Server 설치 프로그램을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-118">You can run SQL Server Setup on a computer that has SharePoint Server 2013 installed, or on a different computer that has no SharePoint software.</span></span> <span data-ttu-id="33e9b-119">Analysis Services는 SharePoint에 종속성이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-119">Analysis Services does not have any dependencies on SharePoint.</span></span>  
  
     <span data-ttu-id="33e9b-120">**고:** 이 항목에서는 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 서버와 백 엔드 서비스의 설치에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-120">**Note:** This topic describes the installation of the [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] server and the backend services.</span></span>  
  
-   <span data-ttu-id="33e9b-121">**중간 계층:** PowerPivot 갤러리, 데이터 새로 고침 예약, 관리 대시보드 및 데이터 공급자를 포함한 SharePoint의 PowerPivot 환경 향상.</span><span class="sxs-lookup"><span data-stu-id="33e9b-121">**Middle-tier:** Enhancements to the PowerPivot experiences in SharePoint including PowerPivot Gallery, Schedule data refresh, Management dashboard, and data providers.</span></span> <span data-ttu-id="33e9b-122">중간 계층 설치 및 구성에 대한 자세한 내용은 다음 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="33e9b-122">For more information on installing and configuring the middle-tier, see the following:</span></span>  
  
    -   [<span data-ttu-id="33e9b-123">SharePoint 2013 &#40;SharePoint용 PowerPivot 추가 기능 설치 또는 제거&#41;</span><span class="sxs-lookup"><span data-stu-id="33e9b-123">Install or Uninstall the PowerPivot for SharePoint Add-in &#40;SharePoint 2013&#41;</span></span>](https://docs.microsoft.com/analysis-services/instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2013)  
  
    -   [<span data-ttu-id="33e9b-124">SharePoint 2013&#41;&#40;PowerPivot 구성 및 솔루션 배포</span><span class="sxs-lookup"><span data-stu-id="33e9b-124">Configure PowerPivot and Deploy Solutions &#40;SharePoint 2013&#41;</span></span>](https://docs.microsoft.com/analysis-services/instances/install-windows/configure-power-pivot-and-deploy-solutions-sharepoint-2013)  
  
##  <a name="prerequisites"></a><a name="bkmk_prereq"></a> <span data-ttu-id="33e9b-125">필수 조건</span><span class="sxs-lookup"><span data-stu-id="33e9b-125">Prerequisites</span></span>  
  
1.  <span data-ttu-id="33e9b-126">SQL Server 설치 프로그램을 실행하려면 로컬 관리자여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-126">You must be a local administrator to run SQL Server Setup.</span></span>  
  
2.  <span data-ttu-id="33e9b-127">SharePoint용 PowerPivot를 사용하려면 SharePoint Server 2013 Enterprise Edition이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-127">SharePoint Server 2013 enterprise edition is required for PowerPivot for SharePoint.</span></span> <span data-ttu-id="33e9b-128">Evaluation Enterprise Edition을 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-128">You can also use the evaluation enterprise edition.</span></span>  
  
3.  <span data-ttu-id="33e9b-129">Excel Services와 동일한 Active Directory 포리스트의 도메인에 컴퓨터가 참가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-129">The computer must be joined to a domain in the same Active Directory forest as Excel Services.</span></span>  
  
4.  <span data-ttu-id="33e9b-130">PowerPivot 인스턴스 이름을 사용할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-130">The PowerPivot instance name must be available.</span></span> <span data-ttu-id="33e9b-131">SharePoint 모드에서 Analysis Services를 설치 중인 컴퓨터에 PowerPivot이라고 명명된 기존 인스턴스가 있어서는 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-131">You cannot have an existing PowerPivot-named instance on the computer on which you are installing Analysis Services in SharePoint mode.</span></span>  
  
5.  <span data-ttu-id="33e9b-132">[SharePoint 모드의 Analysis Services Server에 대 한 하드웨어 및 소프트웨어 요구 사항을 검토 &#40;SQL Server 2014&#41;](../../../sql-server/install/hardware-software-requirements-analysis-services-server-sharepoint-mode.md).</span><span class="sxs-lookup"><span data-stu-id="33e9b-132">Review [Hardware and Software Requirements for Analysis Services Server in SharePoint Mode &#40;SQL Server 2014&#41;](../../../sql-server/install/hardware-software-requirements-analysis-services-server-sharepoint-mode.md).</span></span>  
  
6.  <span data-ttu-id="33e9b-133">[SQL Server 2012 서비스 팩 1 릴리스 정보](https://go.microsoft.com/fwlink/?LinkID=248389) ()에서 릴리스 정보를 검토 합니다 https://go.microsoft.com/fwlink/?LinkID=248389) .</span><span class="sxs-lookup"><span data-stu-id="33e9b-133">Review the release notes at [SQL Server 2012 Service Pack 1 Release Notes](https://go.microsoft.com/fwlink/?LinkID=248389) (https://go.microsoft.com/fwlink/?LinkID=248389).</span></span>  
  
###  <a name="sql-server-edition-requirements"></a><a name="bkmk_sqleditions"></a> <span data-ttu-id="33e9b-134">SQL Server 버전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="33e9b-134">SQL Server Edition Requirements</span></span>  
 <span data-ttu-id="33e9b-135">비즈니스 인텔리전스 기능은 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]의 일부 버전에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-135">Business intelligence features are not all available in all editions of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="33e9b-136">자세한 내용은 [SQL Server 2012 https://go.microsoft.com/fwlink/?linkid=232473) 버전에서 지 원하는 기능](https://go.microsoft.com/fwlink/?linkid=232473) , [SQL Server 2014의 버전 및 구성 요소](../../../sql-server/editions-and-components-of-sql-server-2016.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="33e9b-136">For details, see [Features Supported by the Editions of SQL Server 2012 (https://go.microsoft.com/fwlink/?linkid=232473)](https://go.microsoft.com/fwlink/?linkid=232473) and [Editions and Components of SQL Server 2014](../../../sql-server/editions-and-components-of-sql-server-2016.md).</span></span>  
  
 <span data-ttu-id="33e9b-137">현재 릴리스 정보는 [SQL Server 2012 SP1 릴리스 정보](https://go.microsoft.com/fwlink/?LinkID=248389) ()에서 찾을 수 있습니다 https://go.microsoft.com/fwlink/?LinkID=248389) .</span><span class="sxs-lookup"><span data-stu-id="33e9b-137">The current release notes can be found at [SQL Server 2012 SP1 Release Notes](https://go.microsoft.com/fwlink/?LinkID=248389) (https://go.microsoft.com/fwlink/?LinkID=248389).</span></span>  
  
 <span data-ttu-id="33e9b-138">[Microsoft SQL Server 2012 릴리스 정보 ( https://go.microsoft.com/fwlink/?LinkId=236893) ](https://go.microsoft.com/fwlink/?LinkId=236893).</span><span class="sxs-lookup"><span data-stu-id="33e9b-138">[Microsoft SQL Server 2012 Release Notes (https://go.microsoft.com/fwlink/?LinkId=236893)](https://go.microsoft.com/fwlink/?LinkId=236893).</span></span>  
  
##  <a name="step-1-install-powerpivot-for-sharepoint"></a><a name="InstallSQL"></a><span data-ttu-id="33e9b-139">1 단계: SharePoint용 PowerPivot 설치</span><span class="sxs-lookup"><span data-stu-id="33e9b-139">Step 1: Install PowerPivot for SharePoint</span></span>  
 <span data-ttu-id="33e9b-140">이 단계에서는 SQL Server 설치 프로그램을 실행하여 SharePoint 모드에서 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 서버를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-140">In this step, you run SQL Server Setup to install an [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] server in SharePoint mode.</span></span> <span data-ttu-id="33e9b-141">이후 단계에서는 통합 문서 데이터 모델에 이 서버를 사용하도록 Excel Services를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-141">In a subsequent step, you configure Excel Services to use this server for workbook data models.</span></span>  
  
1.  <span data-ttu-id="33e9b-142">SQL Server 설치 마법사(Setup.exe)를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-142">Run the SQL Server Installation Wizard (Setup.exe).</span></span>  
  
2.  <span data-ttu-id="33e9b-143">왼쪽 탐색 창에서 **설치** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-143">Click **Installation** in the left navigation.</span></span>  
  
3.  <span data-ttu-id="33e9b-144">**새 SQL Server 독립 실행형 설치 또는 기존 설치에 기능 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-144">Click **New SQL Server stand-alone installation or add features to an existing installation**.</span></span>  
  
4.  <span data-ttu-id="33e9b-145">**제품 키** 페이지가 표시되면 평가판 버전을 지정하거나 라이선스를 받은 엔터프라이즈 버전의 제품 키를 입력하고</span><span class="sxs-lookup"><span data-stu-id="33e9b-145">If you see the **Product Key** page, specify the evaluation edition or enter a product key for a licensed copy of the enterprise edition.</span></span> <span data-ttu-id="33e9b-146">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-146">Click **Next**.</span></span> <span data-ttu-id="33e9b-147">버전에 대한 자세한 내용은 [Editions and Components of SQL Server 2014](../../../sql-server/editions-and-components-of-sql-server-2016.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="33e9b-147">For more information on editions, see [Editions and Components of SQL Server 2014](../../../sql-server/editions-and-components-of-sql-server-2016.md).</span></span>  
  
5.  <span data-ttu-id="33e9b-148">Microsoft 소프트웨어 사용권 계약을 검토한 후 동의하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-148">Review and accept the Microsoft Software License Terms of agreement, and then click **Next**.</span></span>  
  
6.  <span data-ttu-id="33e9b-149">**전역 규칙** 페이지가 나타나면 설치 마법사에 표시되는 규칙 정보를 검토합니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-149">If you see the **Global Rules** page, review any rules information the setup wizard displays.</span></span>  
  
7.  <span data-ttu-id="33e9b-150">**Microsoft Update** 페이지에서 Microsoft Update를 사용하여 업데이트를 확인한 후 **다음**을 클릭하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-150">On the **Microsoft Update** page, it is recommended you use Microsoft Update to check for updates, then click **Next**.</span></span>  
  
8.  <span data-ttu-id="33e9b-151">**설치 파일 설치** 페이지가 몇 분 동안 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-151">The **Install Setup Files** page runs for several minutes.</span></span> <span data-ttu-id="33e9b-152">규칙 경고 또는 실패한 규칙을 검토한 후 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-152">Review any rule warnings or failed rules, and then click **Next**.</span></span>  
  
9. <span data-ttu-id="33e9b-153">다른 **설치 지원 규칙**이 표시되면 경고를 검토하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-153">If you see another **Setup Support Rules**, review any warnings and click **Next**.</span></span>  
  
     <span data-ttu-id="33e9b-154">**참고:** Windows 방화벽이 설정되었기 때문에 원격 액세스를 사용할 수 있도록 포트를 열라는 경고가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-154">**Note:** Because Windows Firewall is enabled, you see a warning to open ports to enable remote access.</span></span>  
  
10. <span data-ttu-id="33e9b-155">**설치 역할** 페이지에서 **SQL Server SharePoint용 PowerPivot**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-155">On the **Setup Role** page, select **SQL Server PowerPivot for SharePoint**.</span></span> <span data-ttu-id="33e9b-156">이 옵션을 선택하면 SharePoint 모드에서 Analysis Services를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-156">This option installs Analysis Services in SharePoint mode.</span></span>  
  
     <span data-ttu-id="33e9b-157">또는 설치에 데이터베이스 엔진 인스턴스를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-157">Optionally, you can add an instance of the Database Engine to your installation.</span></span> <span data-ttu-id="33e9b-158">새 팜을 설정 하 고 팜의 구성 및 콘텐츠 데이터베이스를 실행 하기 위해 데이터베이스 서버가 필요한 경우 데이터베이스 엔진를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-158">You might add the Database Engine when setting up a new farm and need a database server to run the farm's configuration and content databases.</span></span> <span data-ttu-id="33e9b-159">이 옵션을 선택해도 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]가 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-159">This option also installs [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)].</span></span>  
  
     <span data-ttu-id="33e9b-160">데이터베이스 엔진을 추가하는 경우 **PowerPivot** 이라는 인스턴스로 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-160">If you add the Database Engine, it is installed as a **PowerPivot** named instance.</span></span> <span data-ttu-id="33e9b-161">이 인스턴스에 대한 연결을 지정하려면 데이터베이스 이름을 [`servername`]\PowerPivot 형식으로 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-161">Whenever you specify a connection to this instance, enter the database name in this format: [`servername`]\PowerPivot.</span></span>  
  
     <span data-ttu-id="33e9b-162">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-162">Click **Next**.</span></span>  
  
     <span data-ttu-id="33e9b-163">![설치 역할](../../../sql-server/install/media/gmni-setupui-featurerole-sql2012sp1.gif "설치 역할")</span><span class="sxs-lookup"><span data-stu-id="33e9b-163">![Setup Role](../../../sql-server/install/media/gmni-setupui-featurerole-sql2012sp1.gif "Setup Role")</span></span>  
  
11. <span data-ttu-id="33e9b-164">기능 선택에서 기능의 읽기 전용 목록이 확인용으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-164">In Feature Selection, a read-only list of the features is displayed for informational purposes.</span></span> <span data-ttu-id="33e9b-165">해당 역할에 대해 미리 선택되어 있는 항목을 추가하거나 제거할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-165">You cannot add or remove items the preselected items for this role.</span></span> <span data-ttu-id="33e9b-166">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-166">Click **Next**.</span></span>  
  
12. <span data-ttu-id="33e9b-167">**인스턴스 구성** 페이지에서 확인용으로 'PowerPivot'이라는 읽기 전용 인스턴스 이름이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-167">On the **Instance Configuration** page, a read-only instance name of 'PowerPivot' is displayed for informational purposes.</span></span> <span data-ttu-id="33e9b-168">이 인스턴스 이름은 필수 항목이며 수정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-168">This instance name is required and it cannot be modified.</span></span> <span data-ttu-id="33e9b-169">그러나 고유한 인스턴스 ID를 입력해 인스턴스를 설명하는 디렉터리 이름과 레지스트리 키를 지정할 수는 있습니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-169">However, you can enter a unique Instance ID to specify a descriptive directory name and registry keys.</span></span> <span data-ttu-id="33e9b-170">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-170">Click **Next**.</span></span>  
  
13. <span data-ttu-id="33e9b-171">**서버 구성** 페이지에서 자동 **시작 유형**에 대해 모든 서비스를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-171">On the **Server Configuration** page, configure all of the services for Automatic **Startup Type**.</span></span> <span data-ttu-id="33e9b-172">다음 다이어그램의 **SQL Server Analysis Services**, **(1)** 에 대해 원하는 도메인 계정과 암호를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-172">Specify the desired domain account and password for **SQL Server Analysis Services**, **(1)** in the following diagram.</span></span>  
  
    -   <span data-ttu-id="33e9b-173">[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]의 경우 **도메인 사용자** 계정 또는 **NetworkService** 계정을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-173">For [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], you can use a **domain user** account or **NetworkService** account.</span></span> <span data-ttu-id="33e9b-174">LocalSystem 또는 LocalService 계정을 사용하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="33e9b-174">Do not use LocalSystem or LocalService accounts.</span></span>  
  
    -   <span data-ttu-id="33e9b-175">SQL Server 데이터베이스 엔진 및 SQL Server 에이전트를 추가한 경우 도메인 사용자 계정으로 실행하거나 기본 가상 계정으로 실행하도록 서비스를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-175">If you added the SQL Server Database Engine and SQL Server Agent, you can configure the services to run under domain user accounts or under the default virtual account.</span></span>  
  
    -   <span data-ttu-id="33e9b-176">사용자의 도메인 사용자 계정으로 서비스 계정을 프로비전하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="33e9b-176">Never provision service accounts with your own domain user account.</span></span> <span data-ttu-id="33e9b-177">그렇게 하면 네트워크에서 리소스에 대해 갖는 권한과 동일한 권한이 서버에 부여됩니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-177">Doing so grants the server the same permissions that you have to the resources in your network.</span></span> <span data-ttu-id="33e9b-178">악의적인 사용자가 서버를 침해할 경우 해당 사용자가 사용자의 도메인 자격 증명으로 로그인한 후</span><span class="sxs-lookup"><span data-stu-id="33e9b-178">If a malicious user compromises the server, that user is logged in under your domain credentials.</span></span> <span data-ttu-id="33e9b-179">사용자와 동일한 데이터 및 애플리케이션을 다운로드하거나 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-179">The user has the permissions to download or use the same data and applications that you do.</span></span>  
  
     <span data-ttu-id="33e9b-180">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-180">Click **Next**.</span></span>  
  
     <span data-ttu-id="33e9b-181">![SSAS Server 구성](../../../sql-server/install/media/ssas-powerpivotsetupsql2012sp1-serverconfiguration.gif "SSAS Server 구성")</span><span class="sxs-lookup"><span data-stu-id="33e9b-181">![SSAS Server Configuration](../../../sql-server/install/media/ssas-powerpivotsetupsql2012sp1-serverconfiguration.gif "SSAS Server Configuration")</span></span>  
  
14. <span data-ttu-id="33e9b-182">[!INCLUDE[ssDE](../../../includes/ssde-md.md)]을 설치하는 경우 **데이터베이스 엔진 구성** 페이지가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-182">If you are installing the [!INCLUDE[ssDE](../../../includes/ssde-md.md)], the **Database Engine Configuration** page appears.</span></span> <span data-ttu-id="33e9b-183">[!INCLUDE[ssDE](../../../includes/ssde-md.md)] 구성에서 **현재 사용자 추가** 를 클릭하여 사용자 계정에 데이터베이스 엔진 인스턴스에 대한 관리자 권한을 부여합니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-183">In [!INCLUDE[ssDE](../../../includes/ssde-md.md)] Configuration, click **Add Current User** to grant your user account administrator permissions on the Database Engine instance.</span></span>  
  
     <span data-ttu-id="33e9b-184">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-184">Click **Next**.</span></span>  
  
15. <span data-ttu-id="33e9b-185">**Analysis Services 구성** 페이지에서 **현재 사용자 추가** 를 클릭하여 사용자 계정에 관리 권한을 부여합니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-185">On the **Analysis Services Configuration** page, click **Add Current User** to grant your user account administrative permissions.</span></span> <span data-ttu-id="33e9b-186">설치가 완료된 후 서버를 구성하려면 관리 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-186">You will need administrative permission to configure the server after Setup is finished.</span></span>  
  
    -   <span data-ttu-id="33e9b-187">같은 페이지에서 관리 권한이 필요한 모든 사용자의 Windows 사용자 계정을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-187">In the same page, add the Windows user account of any person who also requires administrative permissions.</span></span> <span data-ttu-id="33e9b-188">예를 들어 SQL [!INCLUDE[ssGeminiSrv](../../../includes/ssgeminisrv-md.md)] 에서 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 인스턴스에 연결하여 데이터베이스 연결 문제를 해결하려는 모든 사용자에게는 시스템 관리자 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-188">For example, any user who wants to connect to the [!INCLUDE[ssGeminiSrv](../../../includes/ssgeminisrv-md.md)] instance in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] to troubleshoot database connection problems must have system administrator permissions.</span></span> <span data-ttu-id="33e9b-189">현재 서버 문제를 해결하거나 서버를 관리해야 하는 사용자의 계정을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-189">Add the user account of any person who might need to troubleshoot or administer the server now.</span></span>  
  
    -   > [!NOTE]  
        >  <span data-ttu-id="33e9b-190">Analysis Services 서버 인스턴스에 액세스해야 하는 모든 서비스 애플리케이션에는 Analysis Services 관리 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-190">All service applications that require access to the Analysis Services server instance need to have Analysis Services Administrative permissions.</span></span> <span data-ttu-id="33e9b-191">예를 들어 Excel Services, Power View 및 Performance Point Services에 서비스 계정을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-191">For example, add the service accounts for Excel Services, Power View, and Performance Point Services.</span></span> <span data-ttu-id="33e9b-192">또한 SharePoint 팜 계정을 추가합니다. 이 계정은 중앙 관리를 호스팅하는 웹 애플리케이션의 ID로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-192">Also, add the SharePoint farm account, which is used as the identity of the web application that hosts Central Administration.</span></span>  
  
     <span data-ttu-id="33e9b-193">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-193">Click **Next**.</span></span>  
  
16. <span data-ttu-id="33e9b-194">**오류 보고** 페이지에서 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-194">On the **Error Reporting** page, click **Next**.</span></span>  
  
17. <span data-ttu-id="33e9b-195">**설치할 준비가 되었습니다** 페이지에서 **설치**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-195">On the **Ready to Install** page, click **Install**.</span></span>  
  
18. <span data-ttu-id="33e9b-196">**컴퓨터 다시 시작 필요** 대화 상자가 표시되면 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-196">If you see the dialog **Computer Restart Required**, click **OK**.</span></span>  
  
19. <span data-ttu-id="33e9b-197">설치가 완료되면 **닫기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-197">When the installation is complete, click **Close**.</span></span>  
  
20. <span data-ttu-id="33e9b-198">컴퓨터를 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-198">Restart the computer.</span></span>  
  
21. <span data-ttu-id="33e9b-199">사용자 환경에 방화벽이 있는 경우 SQL Server 온라인 설명서의 [Configure the Windows Firewall to Allow Analysis Services Access](../configure-the-windows-firewall-to-allow-analysis-services-access.md)항목을 검토하세요.</span><span class="sxs-lookup"><span data-stu-id="33e9b-199">If you have a firewall in your environment, review the SQL Server Books Online topic, [Configure the Windows Firewall to Allow Analysis Services Access](../configure-the-windows-firewall-to-allow-analysis-services-access.md).</span></span>  
  
### <a name="verify-the-sql-server-installation"></a><span data-ttu-id="33e9b-200">SQL Server 설치 확인</span><span class="sxs-lookup"><span data-stu-id="33e9b-200">Verify the SQL Server Installation</span></span>  
 <span data-ttu-id="33e9b-201">Analysis Services Service가 실행 중인지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-201">Verify that the Analysis Services Service is running.</span></span>  
  
1.  <span data-ttu-id="33e9b-202">Microsoft Windows에서 **시작**, **모든 프로그램**, **Microsoft SQL Server 2012** 그룹을 차례로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-202">In Microsoft Windows click **Start**, click **All Programs**, and click the **Microsoft SQL Server 2012** group.</span></span>  
  
2.  <span data-ttu-id="33e9b-203">**SQL Server Management Studio**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-203">Click **SQL Server Management Studio**.</span></span>  
  
3.  <span data-ttu-id="33e9b-204">Analysis Services 인스턴스(예: **[서버 이름]\POWERPIVOT**)에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-204">Connect to the Analysis Services instance, for example **[your server name]\POWERPIVOT**.</span></span> <span data-ttu-id="33e9b-205">인스턴스에 연결할 수 있는 경우 서비스가 실행 중인 것입니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-205">If you can connect to the instance, you have verified the Service is running.</span></span>  
  
##  <a name="step-2-configure-basic-analysis-services-sharepoint-integration"></a><a name="bkmk_config"></a><span data-ttu-id="33e9b-206">2 단계: 기본 Analysis Services SharePoint 통합 구성</span><span class="sxs-lookup"><span data-stu-id="33e9b-206">Step 2: Configure Basic Analysis Services SharePoint Integration</span></span>  
 <span data-ttu-id="33e9b-207">다음 단계에서는 SharePoint 문서 라이브러리에서 Excel 고급 데이터 모델과 상호 작용하는 데 필요한 구성 변경 내용에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-207">The following steps describe configuration changes needed so you can interact with Excel advanced data models inside a SharePoint document library.</span></span> <span data-ttu-id="33e9b-208">SharePoint Server 2013 및 SQL Server Analysis Services를 설치한 후 이 단계를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-208">Complete these steps after you install SharePoint Server 2013 and SQL Server Analysis Services.</span></span>  
  
### <a name="grant-excel-services-server-administration-rights-on-analysis-services"></a><span data-ttu-id="33e9b-209">Analysis Services에 Excel Services 서버 관리 권한 부여</span><span class="sxs-lookup"><span data-stu-id="33e9b-209">Grant Excel Services Server Administration Rights on Analysis Services</span></span>  
 <span data-ttu-id="33e9b-210">Analysis Services를 설치하는 동안 Excel Services 애플리케이션 서비스 계정을 Analysis Services 관리자로 추가했다면 이 섹션을 완료하지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-210">You do not need to complete this section if during the Analysis Services installation; you added the Excel Services Application service account as an Analysis Services administrator.</span></span>  
  
1.  <span data-ttu-id="33e9b-211">Analysis Services 서버에서 SQL Server Management Studio를 시작하고 Analysis Services 인스턴스에 연결합니다(예: `[MyServer]\POWERPIVOT`).</span><span class="sxs-lookup"><span data-stu-id="33e9b-211">On the Analysis Services server, start SQL Server Management Studio and connect to the Analysis Services instance, for example `[MyServer]\POWERPIVOT`.</span></span>  
  
2.  <span data-ttu-id="33e9b-212">개체 탐색기에서 인스턴스 이름을 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-212">In Object Explorer, Right-click the instance name and click **Properties**.</span></span>  
  
     <span data-ttu-id="33e9b-213">![SSAS 서버 속성 보기](../../../sql-server/install/media/as-ssms-proeprties.gif "SSAS 서버 속성 보기")</span><span class="sxs-lookup"><span data-stu-id="33e9b-213">![View Properties of an SSAS server](../../../sql-server/install/media/as-ssms-proeprties.gif "View Properties of an SSAS server")</span></span>  
  
3.  <span data-ttu-id="33e9b-214">왼쪽 창에서 **보안**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-214">In the left pane, click **Security**.</span></span> <span data-ttu-id="33e9b-215">1단계에서 Excel Services 애플리케이션에 대해 구성한 도메인 로그인을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-215">Add the domain login you configured for the Excel Services Application in step 1.</span></span>  
  
     <span data-ttu-id="33e9b-216">![SSAS 서버의 보안 설정](../../../sql-server/install/media/as-ssms-security.gif "SSAS 서버의 보안 설정")</span><span class="sxs-lookup"><span data-stu-id="33e9b-216">![Security Settings of an SSAS Server](../../../sql-server/install/media/as-ssms-security.gif "Security Settings of an SSAS Server")</span></span>  
  
### <a name="configure-excel-services-for-analysis-services-integration"></a><span data-ttu-id="33e9b-217">Analysis Services 통합을 위한 Excel Services 구성</span><span class="sxs-lookup"><span data-stu-id="33e9b-217">Configure Excel Services for Analysis Services integration</span></span>  
  
1.  <span data-ttu-id="33e9b-218">SharePoint 중앙 관리의 애플리케이션 관리 그룹에서 **서비스 애플리케이션 관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-218">In SharePoint Central Administration, in the Application Management group, click **Manage Service Applications**.</span></span>  
  
2.  <span data-ttu-id="33e9b-219">서비스 애플리케이션 이름을 클릭합니다. 기본값은 **Excel Services 애플리케이션**입니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-219">Click the name of your service application, the default is **Excel Services Application**.</span></span>  
  
3.  <span data-ttu-id="33e9b-220">**Excel Services 애플리케이션 관리 페이지**에서 **데이터 모델 설정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-220">On the **Manage Excel Services Application page**, click **Data Model Settings**.</span></span>  
  
4.  <span data-ttu-id="33e9b-221">**서버 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-221">Click **Add Server**.</span></span>  
  
5.  <span data-ttu-id="33e9b-222">**서버 이름**에 Analysis Services 서버 이름과 PowerPivot 인스턴스 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-222">In **Server Name**, type the Analysis Services server name and the PowerPivot instance name.</span></span> <span data-ttu-id="33e9b-223">예: `MyServer\POWERPIVOT`.</span><span class="sxs-lookup"><span data-stu-id="33e9b-223">For example `MyServer\POWERPIVOT`.</span></span> <span data-ttu-id="33e9b-224">PowerPivot 인스턴스 이름이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-224">The PowerPivot instance name is required.</span></span>  
  
     <span data-ttu-id="33e9b-225">설명을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-225">Type a description.</span></span>  
  
6.  <span data-ttu-id="33e9b-226">**Ok**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-226">Click **Ok**.</span></span>  
  
7.  <span data-ttu-id="33e9b-227">변경 내용은 몇 분 후에 적용됩니다. 또는 **Excel 계산 서비스** 를 **중지** 하고 **시작**할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-227">The changes will take effect in a few minutes or you can **Stop** and **Start** the service **Excel Calculation Services**.</span></span> <span data-ttu-id="33e9b-228">대상</span><span class="sxs-lookup"><span data-stu-id="33e9b-228">To</span></span>  
  
     <span data-ttu-id="33e9b-229">다른 옵션은 관리 권한으로 명령 프롬프트를 열고 `iisreset /noforce`를 입력하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-229">Another option is to open a command prompt with administrative privileges, and type `iisreset /noforce`.</span></span>  
  
     <span data-ttu-id="33e9b-230">ULS 블로그의 항목을 검토하여 서버가 Excel Services에서 인식되는지 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-230">You can verify the server is recognized by Excel Services by reviewing entries in the ULS log.</span></span> <span data-ttu-id="33e9b-231">다음과 유사한 항목이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-231">You will see entries similar to the following:</span></span>  
  
    ```  
    Excel Services Application            Data Model        27           Medium                Check Administrator Access ([ServerName]\POWERPIVOT): Pass.        f127bd9b-bae3-e0e0-9b48-3f7b5ad1eae6  
    Excel Services Application            Data Model        27           Medium                Check Server Version ([ServerName]\POWERPIVOT): Pass (11.0.2809.24 >= 11.0.2800.0).         f127bd9b-bae3-e0e0-9b48-3f7b5ad1eae6  
    Excel Services Application            Data Model        27           Medium                Check Deployment Mode ([ServerName]\POWERPIVOT): Pass.            f127bd9b-bae3-e0e0-9b48-3f7b5ad1eae6  
  
    ```  
  
##  <a name="step-3-verify-the-integration"></a><a name="bkmk_verify"></a><span data-ttu-id="33e9b-232">3 단계: 통합 확인</span><span class="sxs-lookup"><span data-stu-id="33e9b-232">Step 3: Verify the Integration</span></span>  
 <span data-ttu-id="33e9b-233">다음 단계에서는 새 통합 문서를 만들고 업로드하여 Analysis Services 통합을 확인하는 방법을 단계별로 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-233">The following steps walk you through creating and uploading a new workbook to verify the Analysis Services integration.</span></span> <span data-ttu-id="33e9b-234">이들 단계를 완료하려면 SQL Server 데이터베이스가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-234">You will need a SQL Server database to complete the steps.</span></span>  
  
1.  <span data-ttu-id="33e9b-235">**참고:** 슬라이서 또는 필터가 포함된 고급 통합 문서가 이미 있는 경우 이 통합 문서를 SharePoint 문서 라이브러리에 업로드하고 문서 라이브러리 뷰에서 슬라이서 및 필터와 상호 작용할 수 있는지 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-235">**Note:** If you already have an advanced workbook with slicers or filters, you can upload it to your SharePoint document library and verify you are able to interact with the slicers and filters from the document library view.</span></span>  
  
2.  <span data-ttu-id="33e9b-236">Excel에서 새 통합 문서를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-236">Start a new workbook in Excel.</span></span>  
  
3.  <span data-ttu-id="33e9b-237">데이터 탭의 **외부 데이터 가져오기** 에 있는 리본에서 **기타 원본**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-237">On the Data tab, click **From Other Sources** on the ribbon in the **Get External Data**.</span></span>  
  
4.  <span data-ttu-id="33e9b-238">**SQL Server**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-238">Select **From SQL Server**.</span></span>  
  
5.  <span data-ttu-id="33e9b-239">**데이터 연결 마법사**에 사용할 데이터베이스가 있는 SQL Server 인스턴스 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-239">In the **Data Connection Wizard**, enter the name of the SQL Server instance that has the database you want to use.</span></span>  
  
6.  <span data-ttu-id="33e9b-240">또는 로그온 자격 증명을 통해 **Windows 인증 사용** 이 선택되어 있는지 확인한 후 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-240">or Log on credentials, verify that **Use Windows Authentication** is selected, and then click **Next**.</span></span>  
  
7.  <span data-ttu-id="33e9b-241">사용할 데이터베이스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-241">Select the database you want to use.</span></span>  
  
8.  <span data-ttu-id="33e9b-242">**특정 테이블에 연결** 확인란이 선택되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-242">Verify that the **Connect to specific table** checkbox is selected.</span></span>  
  
9. <span data-ttu-id="33e9b-243">**여러 테이블 선택 가능 및 Excel 데이터 모델에 테이블 추가** 확인란을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-243">Click the **Enable selection of multiple tables and add tables to the Excel Data Model** checkbox.</span></span>  
  
10. <span data-ttu-id="33e9b-244">가져올 테이블을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-244">Select the tables you want to import.</span></span>  
  
11. <span data-ttu-id="33e9b-245">**선택한 테이블 간의 관계 가져오기**확인란을 클릭한 후 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-245">Click the checkbox **Import relationships between selected tables**, and then click **Next**.</span></span> <span data-ttu-id="33e9b-246">관계형 데이터베이스에서 여러 테이블을 가져오면 이미 관련된 테이블로 작업할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-246">Importing multiple tables from a relational database lets you work with tables that are already related.</span></span> <span data-ttu-id="33e9b-247">관계를 수동으로 만들지 않아도 되므로 단계를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-247">You save steps because you don't have to build the relationships manually.</span></span>  
  
12. <span data-ttu-id="33e9b-248">마법사의 **데이터 연결 파일 저장 및 마침** 페이지에서 연결의 이름을 입력하고 **마침**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-248">In the **Save Data Connection File and Finish** page of the wizard,, type a dame for your connection and click **Finish**.</span></span>  
  
13. <span data-ttu-id="33e9b-249">**데이터 가져오기** 대화 상자가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-249">The **Import Data** dialog box will appear.</span></span> <span data-ttu-id="33e9b-250">**PivotTable 보고서**를 선택한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-250">Choose **PivotTable Report**, and then click **Ok**.</span></span>  
  
14. <span data-ttu-id="33e9b-251">PivotTable 필드 목록이 통합 문서에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-251">A PivotTable Field List appears in the workbook.</span></span>   
    <span data-ttu-id="33e9b-252">필드 목록에서 **모두** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-252">On the field list, click the **All** tab</span></span>  
  
15. <span data-ttu-id="33e9b-253">필드 목록의 행, 열 및 값 영역에 필드를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-253">Add fields to the Row, Columns, and Value areas in the field list.</span></span>  
  
16. <span data-ttu-id="33e9b-254">슬라이서 또는 필터를 PivotTable에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-254">Add a slicer or a filter to the PivotTable.</span></span> <span data-ttu-id="33e9b-255">**이 단계를 건너뛰지 마십시오**.</span><span class="sxs-lookup"><span data-stu-id="33e9b-255">**Do not skip this step**.</span></span> <span data-ttu-id="33e9b-256">슬라이서 또는 필터는 Analysis Services 설치를 확인하는 데 도움을 주는 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-256">A slicer or filter is the element that will help you verify your Analysis Services installation.</span></span>  
  
17. <span data-ttu-id="33e9b-257">통합 문서를 Excel Services가 구성된 SharePoint Server 2013의 문서 라이브러리에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-257">Save the workbook to a document library on a SharePoint Server 2013 that has Excel Services configured.</span></span> <span data-ttu-id="33e9b-258">파일 공유에 통합 문서를 저장한 다음 SharePoint Server 2013 문서 라이브러리에 업로드할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-258">You can also save the workbook to a file share and then upload it to the SharePoint Server 2013 document library.</span></span>  
  
18. <span data-ttu-id="33e9b-259">통합 문서 이름을 클릭하여 SharePoint에서 보고 슬라이서를 클릭하거나 이전에 추가한 필터를 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-259">Click the name of your workbook to view it in SharePoint and click the slicer or change the filter that you previously added.</span></span> <span data-ttu-id="33e9b-260">데이터 업데이트가 발생하면 Analysis Services가 설치되었고 Excel Services에 사용할 수 있음을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-260">If a data update occurs, you know that Analysis Services is installed and available to Excel Services.</span></span> <span data-ttu-id="33e9b-261">Excel에서 통합 문서를 여는 경우 Analysis Services 서버를 사용하지 않고 캐시된 복사본을 사용하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-261">If you open the workbook in Excel you will be using a cached copy and not using the Analysis Services server.</span></span>  
  
##  <a name="configure-the-windows-firewall-to-allow-analysis-services-access"></a><a name="bkmk_firewall"></a><span data-ttu-id="33e9b-262">Analysis Services 액세스를 허용 하도록 Windows 방화벽 구성</span><span class="sxs-lookup"><span data-stu-id="33e9b-262">Configure the Windows Firewall to Allow Analysis Services Access</span></span>  
 <span data-ttu-id="33e9b-263">[Configure the Windows Firewall to Allow Analysis Services Access](../configure-the-windows-firewall-to-allow-analysis-services-access.md) 항목에 있는 정보를 사용하여 방화벽의 포트 차단을 해제하여 Analysis Services 또는 SharePoint용 PowerPivot에 대한 액세스를 허용하도록 결정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-263">Use the information in the topic [Configure the Windows Firewall to Allow Analysis Services Access](../configure-the-windows-firewall-to-allow-analysis-services-access.md) to determine whether you need to unblock ports in a firewall to allow access to Analysis Services or PowerPivot for SharePoint.</span></span> <span data-ttu-id="33e9b-264">이 항목에서 제공하는 단계를 수행하여 포트와 방화벽 설정을 모두 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-264">You can follow the steps provided in the topic to configure both port and firewall settings.</span></span> <span data-ttu-id="33e9b-265">실제로는 Analysis Services 서버에 대한 액세스를 허용하기 위해 이러한 단계를 함께 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-265">In practice, you should perform these steps together to allow access to your Analysis Services server.</span></span>  
  
##  <a name="upgrade-workbooks-and-scheduled-data-refresh"></a><a name="bkmk_upgrade_workbook"></a><span data-ttu-id="33e9b-266">통합 문서 업그레이드 및 예약 된 데이터 새로 고침</span><span class="sxs-lookup"><span data-stu-id="33e9b-266">Upgrade Workbooks and Scheduled Data Refresh</span></span>  
 <span data-ttu-id="33e9b-267">이전 버전의 PowerPivot에서 만든 통합 문서를 업그레이드 하는 데 필요한 단계는 통합 문서를 만든 PowerPivot의 버전에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-267">The steps required to upgrade workbooks created in previous versions of PowerPivot depend on what version of PowerPivot created the workbook.</span></span> <span data-ttu-id="33e9b-268">자세한 내용은 [통합 문서 업그레이드 및 예약된 데이터 새로 고침&#40;SharePoint 2013&#41;](https://docs.microsoft.com/analysis-services/instances/install-windows/upgrade-workbooks-and-scheduled-data-refresh-sharepoint-2013)을 검토하세요.</span><span class="sxs-lookup"><span data-stu-id="33e9b-268">For more information, see [Upgrade Workbooks and Scheduled Data Refresh &#40;SharePoint 2013&#41;](https://docs.microsoft.com/analysis-services/instances/install-windows/upgrade-workbooks-and-scheduled-data-refresh-sharepoint-2013).</span></span>  
  
##  <a name="beyond-the-single-server-installation--powerpivot-for-microsoft-sharepoint"></a><a name="bkmk_multiple_servers"></a><span data-ttu-id="33e9b-269">단일 서버 설치 외-PowerPivot for Microsoft SharePoint</span><span class="sxs-lookup"><span data-stu-id="33e9b-269">Beyond the Single-Server Installation -PowerPivot for Microsoft SharePoint</span></span>  
 <span data-ttu-id="33e9b-270">**WFE(웹 프런트 엔드)** or **중간 계층:** 더 큰 SharePoint 팜에 SharePoint 모드의 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 서버를 사용하고 팜에 추가 PowerPivot 기능을 설치하려면 각 SharePoint 서버에서 설치 관리자 패키지 **spPowerPivot.msi** 를 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-270">**Web front-end (WFE)** or **Middle-tier:**: To use an [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] server in SharePoint mode in a larger SharePoint farm and to install additional PowerPivot features into the farm, run the installer package **spPowerPivot.msi** on each of the SharePoint servers.</span></span> <span data-ttu-id="33e9b-271">Sppowerpivot.msi는 필요한 데이터 공급자와 SharePoint 2013용 PowerPivot 구성 도구를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-271">The spPowerPivot.msi installs required data providers and the PowerPivot for SharePoint 2013 Configuration tool.</span></span>  
  
 <span data-ttu-id="33e9b-272">중간 계층 설치 및 구성에 대한 자세한 내용은 다음 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="33e9b-272">For more information on installing and configuring the middle-tier, see the following:</span></span>  
  
-   [<span data-ttu-id="33e9b-273">SharePoint 2013 &#40;SharePoint용 PowerPivot 추가 기능 설치 또는 제거&#41;</span><span class="sxs-lookup"><span data-stu-id="33e9b-273">Install or Uninstall the PowerPivot for SharePoint Add-in &#40;SharePoint 2013&#41;</span></span>](https://docs.microsoft.com/analysis-services/instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2013)  
  
-   <span data-ttu-id="33e9b-274">.msi를 다운로드하려면 [Microsoft SharePoint 2013용 Microsoft SQL Server 2014 PowerPivot](https://go.microsoft.com/fwlink/?LinkID=324854)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="33e9b-274">To download the .msi, see [Microsoft SQL Server 2014 PowerPivot for Microsoft SharePoint 2013](https://go.microsoft.com/fwlink/?LinkID=324854)</span></span>  
  
-   [<span data-ttu-id="33e9b-275">SharePoint 2013&#41;&#40;PowerPivot 구성 및 솔루션 배포</span><span class="sxs-lookup"><span data-stu-id="33e9b-275">Configure PowerPivot and Deploy Solutions &#40;SharePoint 2013&#41;</span></span>](https://docs.microsoft.com/analysis-services/instances/install-windows/configure-power-pivot-and-deploy-solutions-sharepoint-2013)  
  
 <span data-ttu-id="33e9b-276">**중복 및 서버 부하:** SharePoint 모드의 보조 또는 추가 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 서버를 설치하면 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 서버 기능이 중복됩니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-276">**Redundancy and server load:** Installing a second, or more [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] servers in SharePoint mode will provide redundancy of the [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] server functionality.</span></span> <span data-ttu-id="33e9b-277">또한 서버 간에 부하가 분산됩니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-277">Additional servers will also spread the load across servers.</span></span> <span data-ttu-id="33e9b-278">자세한 내용은</span><span class="sxs-lookup"><span data-stu-id="33e9b-278">For more information, see the following:</span></span>  
  
-   <span data-ttu-id="33e9b-279">[Excel Services에서 데이터 모델 처리를 위한 Analysis Services 구성](https://technet.microsoft.com/library/jj614437\(v=office.15\)) ( https://technet.microsoft.com/library/jj614437(v=office.15)) .</span><span class="sxs-lookup"><span data-stu-id="33e9b-279">[Configure Analysis Services for processing data models in Excel Services](https://technet.microsoft.com/library/jj614437\(v=office.15\)) (https://technet.microsoft.com/library/jj614437(v=office.15)).</span></span>  
  
-   <span data-ttu-id="33e9b-280">[Excel Services 데이터 모델 설정 관리 (SharePoint Server 2013) ()](https://technet.microsoft.com/library/jj219780\(v=office.15\)) https://technet.microsoft.com/library/jj219780(v=office.15))</span><span class="sxs-lookup"><span data-stu-id="33e9b-280">[Manage Excel Services data model settings (SharePoint Server 2013)](https://technet.microsoft.com/library/jj219780\(v=office.15\)) (https://technet.microsoft.com/library/jj219780(v=office.15)).</span></span>  
  
 <span data-ttu-id="33e9b-281">![SharePoint 설정은](https://docs.microsoft.com/analysis-services/analysis-services/media/as-sharepoint2013-settings-gear.gif "SharePoint 설정") [Microsoft SQL Server 연결 ()을 통해 사용자 의견 및 연락처 정보를 제출](https://connect.microsoft.com/SQLServer/Feedback) https://connect.microsoft.com/SQLServer/Feedback) 합니다.</span><span class="sxs-lookup"><span data-stu-id="33e9b-281">![SharePoint Settings](https://docs.microsoft.com/analysis-services/analysis-services/media/as-sharepoint2013-settings-gear.gif "SharePoint Settings") [Submit feedback and contact information through Microsoft SQL Server Connect](https://connect.microsoft.com/SQLServer/Feedback) (https://connect.microsoft.com/SQLServer/Feedback).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33e9b-282">참고 항목</span><span class="sxs-lookup"><span data-stu-id="33e9b-282">See Also</span></span>  
 <span data-ttu-id="33e9b-283">[PowerPivot을 SharePoint 2013로 마이그레이션](https://docs.microsoft.com/analysis-services/instances/install-windows/migrate-power-pivot-to-sharepoint-2013) </span><span class="sxs-lookup"><span data-stu-id="33e9b-283">[Migrate PowerPivot to SharePoint 2013](https://docs.microsoft.com/analysis-services/instances/install-windows/migrate-power-pivot-to-sharepoint-2013) </span></span>  
 <span data-ttu-id="33e9b-284">[SharePoint 2013 &#40;SharePoint용 PowerPivot 추가 기능 설치 또는 제거&#41;](https://docs.microsoft.com/analysis-services/instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2013) </span><span class="sxs-lookup"><span data-stu-id="33e9b-284">[Install or Uninstall the PowerPivot for SharePoint Add-in &#40;SharePoint 2013&#41;](https://docs.microsoft.com/analysis-services/instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2013) </span></span>  
 [<span data-ttu-id="33e9b-285">SharePoint 2013&#41;&#40;통합 문서 업그레이드 및 예약 된 데이터 새로 고침</span><span class="sxs-lookup"><span data-stu-id="33e9b-285">Upgrade Workbooks and Scheduled Data Refresh &#40;SharePoint 2013&#41;</span></span>](https://docs.microsoft.com/analysis-services/instances/install-windows/upgrade-workbooks-and-scheduled-data-refresh-sharepoint-2013)  
  
  
