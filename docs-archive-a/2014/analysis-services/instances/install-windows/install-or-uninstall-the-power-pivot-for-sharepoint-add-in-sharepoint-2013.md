---
title: SharePoint용 PowerPivot 추가 기능 설치 또는 제거 (SharePoint 2013) | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: fe13ce8b-9369-4126-928a-9426f9119424
author: minewiskan
ms.author: owend
ms.openlocfilehash: 7df54d11021163167149e5b0c1edd960fee1a2ed
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729920"
---
# <a name="install-or-uninstall-the-powerpivot-for-sharepoint-add-in-sharepoint-2013"></a><span data-ttu-id="c0fc7-102">SharePoint용 PowerPivot 추가 기능 설치 또는 제거(SharePoint 2013)</span><span class="sxs-lookup"><span data-stu-id="c0fc7-102">Install or Uninstall the PowerPivot for SharePoint Add-in (SharePoint 2013)</span></span>
  [!INCLUDE[ssGeminiShortvnext](../../../includes/ssgeminishortvnext-md.md)] <span data-ttu-id="c0fc7-103">는 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] 팜에서 [!INCLUDE[SPS2013](../../../includes/sps2013-md.md)] 데이터 액세스를 제공하는 애플리케이션 서버 구성 요소 및 백 엔드 서비스의 컬렉션입니다.</span><span class="sxs-lookup"><span data-stu-id="c0fc7-103">is a collection of application server components and back-end services that provide [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] data access in a [!INCLUDE[SPS2013](../../../includes/sps2013-md.md)] farm.</span></span> <span data-ttu-id="c0fc7-104">SharePoint용 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] 추가 기능(**spPowerpivot.msi**)은 애플리케이션 서버 구성 요소를 설치하는 데 사용되는 설치 관리자 패키지입니다.</span><span class="sxs-lookup"><span data-stu-id="c0fc7-104">The [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] for SharePoint add-in (**spPowerpivot.msi**) is an installer package used to install the application server components.</span></span>

-   <span data-ttu-id="c0fc7-105">이 추가 기능은 SharePoint 2010 배포에 필수적 요소가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="c0fc7-105">The add-in is not required for SharePoint 2010 deployments.</span></span>

-   <span data-ttu-id="c0fc7-106">이 추가 기능은 SharePoint 2013 및 SharePoint 모드의 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 를 포함하는 단일 서버 배포에 필수적 요소가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="c0fc7-106">The add-in is not required on a single server deployment that includes SharePoint 2013 and [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] in SharePoint mode.</span></span> <span data-ttu-id="c0fc7-107">이 추가 기능에서 설치하는 구성 요소는 SharePoint 모드에서 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 서버를 설치하면 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="c0fc7-107">The components installed by the add-in are included when you install an [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] server in SharePoint mode.</span></span> <span data-ttu-id="c0fc7-108">추가 기능을 사용 하는 예제 배포 다이어그램은 [SharePoint의 SQL SERVER BI 기능에 대 한 배포 토폴로지](../../../sql-server/install/deployment-topologies-for-sql-server-bi-features-in-sharepoint.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c0fc7-108">For diagrams of example deployments with the add-in, see [Deployment Topologies for SQL Server BI Features in SharePoint](../../../sql-server/install/deployment-topologies-for-sql-server-bi-features-in-sharepoint.md).</span></span>

 <span data-ttu-id="c0fc7-109">**참고:** 이 항목에서는 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] 솔루션 파일 및 SharePoint 2013용 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] 구성 도구 설치에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="c0fc7-109">**Note:** This topic describes installing the [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] solution files and [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] for SharePoint 2013 Configuration tool.</span></span> <span data-ttu-id="c0fc7-110">설치 후 구성 도구와 추가 기능에 대 한 자세한 내용은 [PowerPivot 구성 및 솔루션 배포 &#40;SharePoint 2013&#41;](https://docs.microsoft.com/analysis-services/instances/install-windows/configure-power-pivot-and-deploy-solutions-sharepoint-2013)항목을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="c0fc7-110">After the installation, see the following topic for information on the configuration tool and additional features, [Configure PowerPivot and Deploy Solutions &#40;SharePoint 2013&#41;](https://docs.microsoft.com/analysis-services/instances/install-windows/configure-power-pivot-and-deploy-solutions-sharepoint-2013).</span></span>

 <span data-ttu-id="c0fc7-111">**spPowerPivot.msi**를 다운로드하는 방법은 [Microsoft® SQL Server® 2014 PowerPivot® for Microsoft SharePoint®](https://go.microsoft.com/fwlink/?LinkID=324854)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c0fc7-111">For information on how to download **spPowerPivot.msi**, see [Microsoft® SQL Server® 2014 PowerPivot® for Microsoft SharePoint®](https://go.microsoft.com/fwlink/?LinkID=324854).</span></span>

 <span data-ttu-id="c0fc7-112">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="c0fc7-112">**In this topic:**</span></span>

-   [<span data-ttu-id="c0fc7-113">배경</span><span class="sxs-lookup"><span data-stu-id="c0fc7-113">Background</span></span>](#bkmk_background)

-   [<span data-ttu-id="c0fc7-114">spPowerPivot.msi 설치 위치</span><span class="sxs-lookup"><span data-stu-id="c0fc7-114">Where to Install spPowerPivot.msi?</span></span>](#bkmk_where_to_install)

-   [<span data-ttu-id="c0fc7-115">요구 사항 및 필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="c0fc7-115">Requirements and Prerequisites</span></span>](#bkmk_prereq)

-   [<span data-ttu-id="c0fc7-116">SharePoint용 PowerPivot을 설치하려면</span><span class="sxs-lookup"><span data-stu-id="c0fc7-116">To Install PowerPivot for SharePoint</span></span>](#bkmk_install)

-   [<span data-ttu-id="c0fc7-117">SharePoint 2013용 PowerPivot 구성 도구를 사용하여 SharePoint 솔루션 파일 배포</span><span class="sxs-lookup"><span data-stu-id="c0fc7-117">Deploy the SharePoint Solution Files with the PowerPivot for SharePoint 2013 Configuration Tool</span></span>](#bkmk_deploy_solution)

-   [<span data-ttu-id="c0fc7-118">추가 기능 제거 또는 복구</span><span class="sxs-lookup"><span data-stu-id="c0fc7-118">Uninstall or repair the add-in</span></span>](#bkmk_remove_addin)

##  <a name="background"></a><a name="bkmk_background"></a> <span data-ttu-id="c0fc7-119">배경</span><span class="sxs-lookup"><span data-stu-id="c0fc7-119">Background</span></span>

-   <span data-ttu-id="c0fc7-120">**애플리케이션 서버:** [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] SharePoint 2013 기능에는 통합 문서를 데이터 원본으로 사용하는 기능, 예약된 데이터 새로 고침 및 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] 관리 대시보드가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="c0fc7-120">**Application Server:** [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] functionality in SharePoint 2013 includes using workbooks as a data source, scheduled data refresh, and the [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] Management Dashboard.</span></span>

     [!INCLUDE[ssGeminiShortvnext](../../../includes/ssgeminishortvnext-md.md)]<span data-ttu-id="c0fc7-121">는 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Analysis Services 클라이언트 라이브러리를\*\* \*\*배포 하 고 [!INCLUDE[ssGeminiShortvnext](../../../includes/ssgeminishortvnext-md.md)] 설치 파일을 컴퓨터에 복사 하는 Windows Installer 패키지 (spPowerpivot.msi)입니다.</span><span class="sxs-lookup"><span data-stu-id="c0fc7-121">is a [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows Installer package (**spPowerpivot.msi**) that deploys Analysis Services client libraries and copies [!INCLUDE[ssGeminiShortvnext](../../../includes/ssgeminishortvnext-md.md)] installation files to the computer.</span></span> <span data-ttu-id="c0fc7-122">설치 관리자는 SharePoint의 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] 기능을 배포 또는 구성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c0fc7-122">The installer does not deploy or configure [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] features in SharePoint.</span></span> <span data-ttu-id="c0fc7-123">다음 구성 요소가 기본적으로 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="c0fc7-123">The following components install by default:</span></span>

    -   [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)] <span data-ttu-id="c0fc7-124">2013. 이 구성 요소에는 PowerShell 스크립트(.ps1 파일), SharePoint 솔루션 패키지(.wsp) 및 SharePoint 2013 팜에서 [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)] 을 배포하기 위한 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] 2013 구성 도구가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0fc7-124">2013. This component includes PowerShell scripts (.ps1 files), SharePoint solution packages (.wsp), and the [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)] 2013 configuration tool to deploy [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] in a SharePoint 2013 farm.</span></span>

    -   [!INCLUDE[msCoName](../../../includes/msconame-md.md)] <span data-ttu-id="c0fc7-125">Analysis Services용 OLE DB 공급자(MSOLAP)</span><span class="sxs-lookup"><span data-stu-id="c0fc7-125">OLE DB Provider for Analysis Services (MSOLAP).</span></span>

    -   <span data-ttu-id="c0fc7-126">ADOMD.NET 데이터 공급자</span><span class="sxs-lookup"><span data-stu-id="c0fc7-126">ADOMD.NET data provider.</span></span>

    -   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="c0fc7-127">Analysis Management Objects</span><span class="sxs-lookup"><span data-stu-id="c0fc7-127">Analysis Management Objects.</span></span>

-   <span data-ttu-id="c0fc7-128">**백 엔드 서비스:** Excel용 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] 를 사용해서 분석 데이터가 포함된 통합 문서를 만들 경우, SharePoint 모드로 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 를 실행하는 BI 서버에 Excel Services가 구성되어 서버 환경에서 데이터에 액세스할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0fc7-128">**Backend services:** If you use [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] for Excel to create workbooks that contain analytical data, you must have Excel Services configured with a BI server running [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] in SharePoint mode to access that data in a server environment.</span></span> <span data-ttu-id="c0fc7-129">SharePoint Server 2013이 설치된 컴퓨터 또는 SharePoint 소프트웨어가 설치되지 않은 다른 컴퓨터에서 SQL Server 설치 프로그램을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0fc7-129">You can run SQL Server Setup on a computer that has SharePoint Server 2013 installed, or on a different computer that has no SharePoint software.</span></span> <span data-ttu-id="c0fc7-130">Analysis Services는 SharePoint에 종속성이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c0fc7-130">Analysis Services does not have any dependencies on SharePoint.</span></span>

     <span data-ttu-id="c0fc7-131">백 엔드 서비스 설치, 제거 및 구성에 대한 자세한 내용은 다음 항목을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c0fc7-131">For more information on installing, uninstalling, and configuring the backend services, see the following:</span></span>

    -   [<span data-ttu-id="c0fc7-132">SharePoint 2013용 PowerPivot 설치</span><span class="sxs-lookup"><span data-stu-id="c0fc7-132">PowerPivot for SharePoint 2013 Installation</span></span>](https://docs.microsoft.com/analysis-services/instances/install-windows/install-analysis-services-in-power-pivot-mode)

    -   [<span data-ttu-id="c0fc7-133">SharePoint용 PowerPivot 제거</span><span class="sxs-lookup"><span data-stu-id="c0fc7-133">Uninstall PowerPivot for SharePoint</span></span>](../../../sql-server/install/uninstall-power-pivot-for-sharepoint.md)

##  <a name="where-to-install-sppowerpivotmsi"></a><a name="bkmk_where_to_install"></a><span data-ttu-id="c0fc7-134">spPowerPivot.msi 설치 위치</span><span class="sxs-lookup"><span data-stu-id="c0fc7-134">Where to Install spPowerPivot.msi?</span></span>
 <span data-ttu-id="c0fc7-135">권장되는 최선의 구현 방법은 구성 일치를 위해 애플리케이션 서버 및 웹 프런트 엔드 서버를 포함하여 SharePoint 팜의 모든 서버에 **spPowerPivot.msi** 를 설치하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="c0fc7-135">A recommended best practice is to install **spPowerPivot.msi** on all servers in the SharePoint farm for configuration consistency, including application servers and web-front end servers.</span></span> <span data-ttu-id="c0fc7-136">설치 관리자 패키지에는 [!INCLUDE[ssGeminiShortvnext](../../../includes/ssgeminishortvnext-md.md)] 구성 도구뿐만 아니라 Analysis Services 데이터 공급자도 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0fc7-136">The installer package includes the Analysis Services data providers as well as the [!INCLUDE[ssGeminiShortvnext](../../../includes/ssgeminishortvnext-md.md)] configuration tool.</span></span> <span data-ttu-id="c0fc7-137">**spPowerPivot.msi** 를 설치하는 경우 개별 구성 요소를 제외하여 설치를 사용자 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0fc7-137">When you install **spPowerPivot.msi** you can customize the installation by excluding individual components.</span></span>

 <span data-ttu-id="c0fc7-138">**데이터 공급자:** 여러 SharePoint 및 SQL Server 기술은 Excel Services, PerformancePoint Services 및 Power View 등 Analysis Services 데이터 공급자를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="c0fc7-138">**Data providers:** Several SharePoint and SQL Server technologies use the Analysis Services data providers including Excel Services, PerformancePoint Services, and Power View.</span></span> <span data-ttu-id="c0fc7-139">모든 SharePoint 서버에 **spPowerPivot.msi** 를 설치하면 Analysis Services 데이터 공급자의 전체 집합과 PowerPivot 연결이 팜에서 일관적으로 사용할 수 있음을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0fc7-139">Installing **spPowerPivot.msi** on all SharePoint servers ensures the full set of Analysis Services data providers and PowerPivot connectivity is consistently available across the farm.</span></span>

> [!NOTE]
>  <span data-ttu-id="c0fc7-140">**spPowerPivot.msi**를 사용하여 SharePoint 2013 서버에 Analysis Services 데이터 공급자를 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0fc7-140">You must install the Analysis Services data providers on a SharePoint 2013 server using **spPowerPivot.msi**.</span></span> <span data-ttu-id="c0fc7-141">[!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)] 기능 팩에서 사용할 수 있는 다른 설치 관리자 패키지는 이 환경에서 데이터 공급자가 요구되는 SharePoint 2013 지원 파일을 포함하지 않으므로 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c0fc7-141">Other installer packages available in the [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)] Feature Pack are not supported because these packages do not include the SharePoint 2013 support files that the data providers require in this environment.</span></span>

 <span data-ttu-id="c0fc7-142">**구성 도구:** SharePoint 2013용 PowerPivot 구성 도구는 SharePoint 서버 중 하나에서만 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="c0fc7-142">**Configuration Tool:** The PowerPivot for SharePoint 2013 configuration tool is required on only one of the SharePoint servers.</span></span> <span data-ttu-id="c0fc7-143">그러나 다중 서버 팜에서 권장되는 최선의 구현 방법은 두 서버 중 하나가 오프라인일 때 구성 도구에 액세스할 수 있도록 최소 2개 이상의 서버에 구성 도구를 설치하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="c0fc7-143">However a recommended best practice in multi-server farms is to install the configuration tool on at least two servers so you have access to the configuration tool if one of the two servers is offline.</span></span>

##  <a name="requirements-and-prerequisites"></a><a name="bkmk_prereq"></a><span data-ttu-id="c0fc7-144">요구 사항 및 필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="c0fc7-144">Requirements and Prerequisites</span></span>

-   [!INCLUDE[msCoName](../../../includes/msconame-md.md)] <span data-ttu-id="c0fc7-145">SharePoint Server 2013</span><span class="sxs-lookup"><span data-stu-id="c0fc7-145">SharePoint Server 2013.</span></span>

-   <span data-ttu-id="c0fc7-146">SharePoint 제품 및 기술 요구 사항에 따라**spPowerPivot.msi** 는 64비트 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="c0fc7-146">**spPowerPivot.msi** is 64-bit only, in accordance with the requirements of SharePoint products and technologies.</span></span>

-   <span data-ttu-id="c0fc7-147">PowerPivot 모드의 [!INCLUDE[ssASCurrent](../../../includes/ssascurrent-md.md)] 서버.</span><span class="sxs-lookup"><span data-stu-id="c0fc7-147">A [!INCLUDE[ssASCurrent](../../../includes/ssascurrent-md.md)] server in PowerPivot mode.</span></span> <span data-ttu-id="c0fc7-148">Excel Services에서는 SQL Server Analysis Services 인스턴스를 PowerPivot 서버로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="c0fc7-148">Excel Services will use the SQL Server Analysis Services instance as a PowerPivot server.</span></span> <span data-ttu-id="c0fc7-149">Analysis Services는 로컬 컴퓨터 또는 원격 컴퓨터에서 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0fc7-149">Analysis Services can run on the local or a remote computer.</span></span>

-   <span data-ttu-id="c0fc7-150">**사용 권한:**[!INCLUDE[ssGeminiShortvnext](../../../includes/ssgeminishortvnext-md.md)]을 설치하려면 현재 사용자가 컴퓨터의 관리자이며 SharePoint 팜 관리자 그룹의 멤버여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0fc7-150">**Permissions:** To install [!INCLUDE[ssGeminiShortvnext](../../../includes/ssgeminishortvnext-md.md)], the current user is required to be an administrator on the computer and a SharePoint Farm Administrators group.</span></span>

-   <span data-ttu-id="c0fc7-151">요구 사항 및 필수 구성 요소에 대 한 자세한 내용은 [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)] [SharePoint 모드의 Analysis Services Server에 대 한 하드웨어 및 소프트웨어 요구 사항 &#40;SQL Server 2014&#41;](../../../sql-server/install/hardware-software-requirements-analysis-services-server-sharepoint-mode.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c0fc7-151">For more information on [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)] requirements and pre-requisites, go to [Hardware and Software Requirements for Analysis Services Server in SharePoint Mode &#40;SQL Server 2014&#41;](../../../sql-server/install/hardware-software-requirements-analysis-services-server-sharepoint-mode.md).</span></span>

##  <a name="to-install-powerpivot-for-sharepoint"></a><a name="bkmk_install"></a><span data-ttu-id="c0fc7-152">SharePoint용 PowerPivot를 설치 하려면</span><span class="sxs-lookup"><span data-stu-id="c0fc7-152">To Install PowerPivot for SharePoint</span></span>
 <span data-ttu-id="c0fc7-153">**spPowerpivot.msi** 설치 관리자 패키지는 그래픽 사용자 인터페이스 및 명령줄 설치 모드를 둘 다 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="c0fc7-153">The **spPowerpivot.msi** installer package supports both a graphical user interface and a command-line mode.</span></span> <span data-ttu-id="c0fc7-154">두 설치 방법 모두 관리자 권한으로 .msi를 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0fc7-154">Both methods of installation require that you run the .msi with administrator privileges.</span></span> <span data-ttu-id="c0fc7-155">설치 후 구성 도구와 추가 기능에 대 한 자세한 내용은 [PowerPivot 구성 및 솔루션 배포 &#40;SharePoint 2013&#41;](https://docs.microsoft.com/analysis-services/instances/install-windows/configure-power-pivot-and-deploy-solutions-sharepoint-2013)항목을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="c0fc7-155">After the installation, see the following topic for information on the configuration tool and additional features, [Configure PowerPivot and Deploy Solutions &#40;SharePoint 2013&#41;](https://docs.microsoft.com/analysis-services/instances/install-windows/configure-power-pivot-and-deploy-solutions-sharepoint-2013).</span></span>

### <a name="user-interface-installation"></a><span data-ttu-id="c0fc7-156">사용자 인터페이스 설치</span><span class="sxs-lookup"><span data-stu-id="c0fc7-156">User interface installation</span></span>
 <span data-ttu-id="c0fc7-157">그래픽 사용자 인터페이스를 사용하여 [!INCLUDE[ssGeminiShortvnext](../../../includes/ssgeminishortvnext-md.md)] 을 설치하려면 다음 단계를 완료하세요.</span><span class="sxs-lookup"><span data-stu-id="c0fc7-157">To install [!INCLUDE[ssGeminiShortvnext](../../../includes/ssgeminishortvnext-md.md)] with the graphical user interface, complete the following steps:</span></span>

1.  <span data-ttu-id="c0fc7-158">**SpPowerPivot.msi**를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="c0fc7-158">Run **SpPowerPivot.msi**.</span></span>

2.  <span data-ttu-id="c0fc7-159">시작 페이지에서 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c0fc7-159">Click **Next** on the Welcome page.</span></span>

3.  <span data-ttu-id="c0fc7-160">사용권 계약을 검토하고 이에 동의한 후 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c0fc7-160">Review and accept the license agreement, then click **Next**.</span></span>

4.  <span data-ttu-id="c0fc7-161">**기능 선택** 페이지에서 모든 기능이 기본적으로 선택되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0fc7-161">On the **Feature Selection** page, all of the features are selected by default.</span></span>

5.  <span data-ttu-id="c0fc7-162">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c0fc7-162">Click **Next**.</span></span>

6.  <span data-ttu-id="c0fc7-163">**설치** 를 클릭하여 설치하고 설치를 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="c0fc7-163">Click **Install** to install to finish the installation.</span></span>

### <a name="command-line-installation"></a><span data-ttu-id="c0fc7-164">명령줄 설치</span><span class="sxs-lookup"><span data-stu-id="c0fc7-164">Command Line Installation</span></span>
 <span data-ttu-id="c0fc7-165">명령줄 설치의 경우 관리 권한으로 명령 프롬프트를 연 다음 **spPowerPivot.msi**를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="c0fc7-165">For a command-line installation, open a command prompt with administrative permissions, and then run the **spPowerPivot.msi**.</span></span> <span data-ttu-id="c0fc7-166">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="c0fc7-166">For example:</span></span>

 <span data-ttu-id="c0fc7-167">`Msiexec.exe /i SpPowerPivot.msi`.</span><span class="sxs-lookup"><span data-stu-id="c0fc7-167">`Msiexec.exe /i SpPowerPivot.msi`.</span></span>

 <span data-ttu-id="c0fc7-168">설치 로그를 만들려면 표준 MsiExec 로깅 스위치를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="c0fc7-168">To create an installation log, use the standard MsiExec logging switches.</span></span> <span data-ttu-id="c0fc7-169">다음 예에서는 "v" 자세한 로깅 스위치를 사용 하 여 "Install_Log.txt" 로그 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c0fc7-169">The following example creates the log file "Install_Log.txt" using the "v" verbose logging switch.</span></span>

```cmd
Msiexec.exe /i SpPowerPivot.msi /L v c:\test\Install_Log.txt
```

### <a name="quiet-command-line-installation-for-scripting"></a><span data-ttu-id="c0fc7-170">스크립팅을 위한 자동 명령줄 설치</span><span class="sxs-lookup"><span data-stu-id="c0fc7-170">Quiet Command Line Installation for scripting</span></span>
 <span data-ttu-id="c0fc7-171">대화 상자 또는 경고가 표시 되지 않는 "자동" 설치에 **/q** 또는 **/quiet** 스위치를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0fc7-171">You can use the **/q** or **/quiet** switches for a "quiet" installation that will not display any dialogs or warnings.</span></span> <span data-ttu-id="c0fc7-172">자동 설치는 추가 기능 설치를 스크립팅하려는 경우에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="c0fc7-172">The quiet installation is useful if you want to script the installation of the add-in.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="c0fc7-173">자동 명령줄 설치를 위해 **/q** 스위치를 사용할 경우 최종 사용자 사용권 계약이 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c0fc7-173">If you use the **/q** switch for a silent command line installation, the end-user license agreement will not be displayed.</span></span> <span data-ttu-id="c0fc7-174">설치 방법에 관계없이 본 소프트웨어의 설치는 사용권 계약에 의해 제한되며 사용자는 사용권 계약을 준수해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0fc7-174">Regardless of the installation method, the use of this software is governed by a license agreement and you are responsible for complying with the license agreement.</span></span>

#### <a name="to-perform-a-quiet-installation"></a><span data-ttu-id="c0fc7-175">자동 설치를 수행 하려면</span><span class="sxs-lookup"><span data-stu-id="c0fc7-175">To perform a quiet installation</span></span>

1.  <span data-ttu-id="c0fc7-176">**관리자 권한으로**명령 프롬프트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="c0fc7-176">Open a command prompt **with administrator permissions**.</span></span>

2.  <span data-ttu-id="c0fc7-177">다음 명령 실행:</span><span class="sxs-lookup"><span data-stu-id="c0fc7-177">Run the following command:</span></span>

    ```cmd
    Msiexec.exe /i spPowerPivot.msi /q
    ```

### <a name="command-line-installation-to-include-specific-components"></a><span data-ttu-id="c0fc7-178">특정 구성 요소를 포함하는 명령줄 설치</span><span class="sxs-lookup"><span data-stu-id="c0fc7-178">Command Line Installation to include specific components</span></span>
 <span data-ttu-id="c0fc7-179">모든 SharePoint 서버에 [!INCLUDE[ssGeminiShortvnext](../../../includes/ssgeminishortvnext-md.md)] 구성 도구가 필요한 것은 아닙니다. 그러나 구성 도구가 필요한 경우 사용할 수 있도록 최소 2개 이상의 서버에 설치하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="c0fc7-179">The [!INCLUDE[ssGeminiShortvnext](../../../includes/ssgeminishortvnext-md.md)] Configuration tool is not required on every SharePoint server, however it is recommended to install it on at least two servers so the configuration tool is available when you need it.</span></span>

 <span data-ttu-id="c0fc7-180">spPowerPivot.msi를 설치하는 경우 [!INCLUDE[ssGeminiShortvnext](../../../includes/ssgeminishortvnext-md.md)] 구성 도구가 아닌 데이터 공급자 등의 특정 항목을 설치하는 명령줄 옵션을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0fc7-180">When you install the spPowerPivot.msi, you can use the command line options to install specific items, such as the data providers and not the [!INCLUDE[ssGeminiShortvnext](../../../includes/ssgeminishortvnext-md.md)] Configuration tool.</span></span> <span data-ttu-id="c0fc7-181">다음 명령줄은 구성 도구를 제외하고 모든 구성 요소를 설치하는 예입니다.</span><span class="sxs-lookup"><span data-stu-id="c0fc7-181">The following command line is an example of installing all components except the configuration tool:</span></span>

```
Msiexec /i spPowerPivot.msi AGREETOLICENSE="yes" ADDLOCAL=" SQL_OLAPDM,SQL_ADOMD,SQL_AMO,SQLAS_SP_Common"
```

|<span data-ttu-id="c0fc7-182">옵션</span><span class="sxs-lookup"><span data-stu-id="c0fc7-182">Option</span></span>|<span data-ttu-id="c0fc7-183">Description</span><span class="sxs-lookup"><span data-stu-id="c0fc7-183">Description</span></span>|
|------------|-----------------|
|<span data-ttu-id="c0fc7-184">Analysis_Server_SP_addin</span><span class="sxs-lookup"><span data-stu-id="c0fc7-184">Analysis_Server_SP_addin</span></span>|<span data-ttu-id="c0fc7-185">PowerPivot 구성</span><span class="sxs-lookup"><span data-stu-id="c0fc7-185">PowerPivot Configuration</span></span>|
|<span data-ttu-id="c0fc7-186">SQL_OLAPDM</span><span class="sxs-lookup"><span data-stu-id="c0fc7-186">SQL_OLAPDM</span></span>|<span data-ttu-id="c0fc7-187">MSOLAP</span><span class="sxs-lookup"><span data-stu-id="c0fc7-187">MSOLAP</span></span>|
|<span data-ttu-id="c0fc7-188">SQL_ADOMD</span><span class="sxs-lookup"><span data-stu-id="c0fc7-188">SQL_ADOMD</span></span>|<span data-ttu-id="c0fc7-189">ADOMD.net 공급자</span><span class="sxs-lookup"><span data-stu-id="c0fc7-189">ADOMD.net provider</span></span>|
|<span data-ttu-id="c0fc7-190">SQL_AMO</span><span class="sxs-lookup"><span data-stu-id="c0fc7-190">SQL_AMO</span></span>|<span data-ttu-id="c0fc7-191">AMO 공급자</span><span class="sxs-lookup"><span data-stu-id="c0fc7-191">AMO provider</span></span>|
|<span data-ttu-id="c0fc7-192">SQLAS_SP_Common</span><span class="sxs-lookup"><span data-stu-id="c0fc7-192">SQLAS_SP_Common</span></span>|<span data-ttu-id="c0fc7-193">SharePoint 2013용 Analysis Services 일반 구성 요소</span><span class="sxs-lookup"><span data-stu-id="c0fc7-193">Analysis Services common components for SharePoint 2013</span></span>|

##  <a name="deploy-the-sharepoint-solution-files-with-the-powerpivot-for-sharepoint-2013-configuration-tool"></a><a name="bkmk_deploy_solution"></a><span data-ttu-id="c0fc7-194">SharePoint용 PowerPivot 2013 구성 도구를 사용 하 여 SharePoint 솔루션 파일 배포</span><span class="sxs-lookup"><span data-stu-id="c0fc7-194">Deploy the SharePoint Solution Files with the PowerPivot for SharePoint 2013 Configuration Tool</span></span>
 <span data-ttu-id="c0fc7-195">spPowerPivot.msi에서 하드 드라이브에 복사하는 파일 중 3개는 SharePoint 솔루션 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="c0fc7-195">Three of the files copied to the hard drive by spPowerPivot.msi are SharePoint solution files.</span></span> <span data-ttu-id="c0fc7-196">솔루션 파일의 범위는 웹 애플리케이션 수준이지만 다른 파일의 범위는 팜 수준입니다.</span><span class="sxs-lookup"><span data-stu-id="c0fc7-196">The scope of one solution file is the Web application level while the scope of the other files is the farm level.</span></span> <span data-ttu-id="c0fc7-197">파일은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="c0fc7-197">The files are the following:</span></span>

-   `PowerPivotFarmSolution.wsp`

-   `PowerPivotFarm14Solution.wsp`

-   `PowerPivotWebApplicationSolution.wsp`

 <span data-ttu-id="c0fc7-198">솔루션 파일은 다음 폴더에 복사됩니다.</span><span class="sxs-lookup"><span data-stu-id="c0fc7-198">The solution files are copied to the following folder:</span></span>

 `C:\Program Files\Microsoft SQL Server\120\Tools\PowerPivotTools\SPAddinConfiguration\Resources`

 <span data-ttu-id="c0fc7-199">.msi 설치에 따라 [!INCLUDE[ssGeminiShortvnext](../../../includes/ssgeminishortvnext-md.md)] 구성 도구를 실행하여 SharePoint 팜의 솔루션을 구성하고 배포합니다.</span><span class="sxs-lookup"><span data-stu-id="c0fc7-199">Following the .msi installation, run the [!INCLUDE[ssGeminiShortvnext](../../../includes/ssgeminishortvnext-md.md)] Configuration Tool to configure and deploy the solutions in the SharePoint farm.</span></span>

### <a name="to-start-the-configuration-tool"></a><span data-ttu-id="c0fc7-200">구성 도구를 시작 하려면</span><span class="sxs-lookup"><span data-stu-id="c0fc7-200">To start the configuration tool</span></span> 

 <span data-ttu-id="c0fc7-201">Windows 시작 화면에서 "power"를 입력 하 고 앱 검색 결과에서 **SharePoint용 PowerPivot 2013 구성**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0fc7-201">From the Windows Start screen type "power" and in the Apps search results, click **PowerPivot for SharePoint 2013 Configuration**.</span></span> <span data-ttu-id="c0fc7-202">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 설치 프로그램은 SharePoint 2010 및 SharePoint 2013에 대해 별개의 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] 구성 도구를 설치하기 때문에 검색 결과에 두 개의 링크가 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0fc7-202">Note that the search results may include two links because [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] setup installs separate [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] configuration tools for SharePoint 2010 and SharePoint 2013.</span></span> <span data-ttu-id="c0fc7-203">SharePoint 2013용 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] 구성 도구를 시작하는지 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="c0fc7-203">Make sure you start the [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] for SharePoint 2013 Configuration tool.</span></span>

 <span data-ttu-id="c0fc7-204">![두 개의 powerpivot 구성 도구](../../media/as-powerpivot-configtools-bothicons.gif "두 개의 powerpivot 구성 도구")</span><span class="sxs-lookup"><span data-stu-id="c0fc7-204">![two powerpivot configuration tools](../../media/as-powerpivot-configtools-bothicons.gif "two powerpivot configuration tools")</span></span>

 <span data-ttu-id="c0fc7-205">**디스크나**</span><span class="sxs-lookup"><span data-stu-id="c0fc7-205">**Or**</span></span>

1.  <span data-ttu-id="c0fc7-206">**시작**, **모든 프로그램**으로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="c0fc7-206">Go to **Start**, **All Programs**.</span></span>

2.  <span data-ttu-id="c0fc7-207">**Microsoft SQL Server 2014**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c0fc7-207">Click **Microsoft SQL Server 2014**.</span></span>

3.  <span data-ttu-id="c0fc7-208">**구성 도구**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c0fc7-208">Click **Configuration Tools**.</span></span>

4.  <span data-ttu-id="c0fc7-209">**SharePoint 2013용 PowerPivot 구성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c0fc7-209">Click **PowerPivot for SharePoint 2013 Configuration**.</span></span>

 <span data-ttu-id="c0fc7-210">구성 도구에 대한 자세한 내용은 [PowerPivot Configuration Tools](../../power-pivot-sharepoint/power-pivot-configuration-tools.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c0fc7-210">For more information on the configuration tool, see [PowerPivot Configuration Tools](../../power-pivot-sharepoint/power-pivot-configuration-tools.md).</span></span>

##  <a name="uninstall-or-repair-the-add-in"></a><a name="bkmk_remove_addin"></a><span data-ttu-id="c0fc7-211">추가 기능 제거 또는 복구</span><span class="sxs-lookup"><span data-stu-id="c0fc7-211">Uninstall or repair the add-in</span></span>

> [!CAUTION]
>  <span data-ttu-id="c0fc7-212">**spPowerPivot.msi** 를 제거하는 경우 데이터 공급자 및 구성 도구가 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="c0fc7-212">If you uninstall **spPowerPivot.msi** the data providers and the configuration tool are uninstalled.</span></span> <span data-ttu-id="c0fc7-213">데이터 공급자를 제거하면 서버가 PowerPivot에 연결할 수 없게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c0fc7-213">Uninstalling the data providers will cause the server to be unable to connect to PowerPivot.</span></span>

 <span data-ttu-id="c0fc7-214">다음 방법 중 하나를 사용하여 [!INCLUDE[ssGeminiShortvnext](../../../includes/ssgeminishortvnext-md.md)] 을 제거하거나 복구할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0fc7-214">You can uninstall or repair [!INCLUDE[ssGeminiShortvnext](../../../includes/ssgeminishortvnext-md.md)] using one of the following methods:</span></span>

1.  <span data-ttu-id="c0fc7-215">**Windows 제어판:\*\*\*\*Microsoft SQL Server 2012 SharePoint 2013용 PowerPivot**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c0fc7-215">**Windows control panel:** Select **Microsoft SQL Server 2012 PowerPivot for SharePoint 2013**.</span></span> <span data-ttu-id="c0fc7-216">**제거** 또는 **복구**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c0fc7-216">Click either **Uninstall** or **Repair**.</span></span>

2.  <span data-ttu-id="c0fc7-217">spPowerPivot.msi를 실행하고 **제거** 옵션 또는 **복구** 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c0fc7-217">Run the spPowerPivot.msi and select the **Remove** option or the **Repair** option.</span></span>

 <span data-ttu-id="c0fc7-218">**명령줄:** 명령줄을 사용하여 SharePoint 2013용 PowerPivot을 복구하거나 제거하려면 **관리자 권한으로** 명령 프롬프트를 열고 다음 명령 중 하나를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="c0fc7-218">**Command Line:** To repair or uninstall PowerPivot for SharePoint 2013 using the command line, open a command prompt **with administrator permissions** and run one of the following commands:</span></span>

-   <span data-ttu-id="c0fc7-219">복구하려면 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="c0fc7-219">To Repair, run the following command:</span></span>

    ```cmd
    msiexec.exe /f spPowerPivot.msi
    ```

 <span data-ttu-id="c0fc7-220">또는</span><span class="sxs-lookup"><span data-stu-id="c0fc7-220">OR</span></span>

-   <span data-ttu-id="c0fc7-221">제거하려면 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="c0fc7-221">To uninstall, run the following command:</span></span>

    ```cmd
    msiexec.exe /uninstall spPowerPivot.msi
    ```
