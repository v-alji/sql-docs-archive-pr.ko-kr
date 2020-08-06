---
title: SQL Server 2014의 SQL Server Reporting Services에서 사용 되지 않는 기능 Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Reporting Services, backward compatibility
- deprecated features [Reporting Services]
- HTML OWC rendering extension [Reporting Services]
- Report Server Web service, endpoints
ms.assetid: 3876c01e-f81d-4cce-9104-5106a8c369e6
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: af858ae94bf5ea3d9f0cfe0b99759442dabd6629
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651535"
---
# <a name="deprecated-features-in-sql-server-reporting-services-in-sql-server-2014"></a><span data-ttu-id="9e0ee-102">SQL Server 2014의 SQL Server Reporting Services에서 지원되지 않는 기능</span><span class="sxs-lookup"><span data-stu-id="9e0ee-102">Deprecated Features in SQL Server Reporting Services in SQL Server 2014</span></span>
  <span data-ttu-id="9e0ee-103">이 항목에서는 지원되지 않는 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 기능에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-103">This topic describes the deprecated [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] features.</span></span> <span data-ttu-id="9e0ee-104">이러한 기능은 지원되지 않는 버전에서 계속 사용할 수 있지만 이후 버전의 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]에서는 기능이 제거될 예정입니다.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-104">The features are still available in the release in which they are deprecated; however the features are scheduled to be removed in a future release of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="9e0ee-105">새 애플리케이션에는 이러한 기능을 사용하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-105">Deprecated features should not be used in new applications.</span></span>  
  
 <span data-ttu-id="9e0ee-106">이 항목의 내용:</span><span class="sxs-lookup"><span data-stu-id="9e0ee-106">In this topic:</span></span>  
  
-   [<span data-ttu-id="9e0ee-107">SQL Server 2014 R2 Reporting Services에서 지원되지 않는 기능</span><span class="sxs-lookup"><span data-stu-id="9e0ee-107">SQL Server 2014 Reporting Services Deprecated Features</span></span>](#bkmk_2014)  
  
-   [<span data-ttu-id="9e0ee-108">SQL Server 2012 SP1 Reporting Services에서 지원되지 않는 기능</span><span class="sxs-lookup"><span data-stu-id="9e0ee-108">SQL Server 2012 SP1 Reporting Services Deprecated Features</span></span>](#bkmk_2012sp1)  
  
-   [<span data-ttu-id="9e0ee-109">SQL Server 2012 R2 Reporting Services에서 지원되지 않는 기능</span><span class="sxs-lookup"><span data-stu-id="9e0ee-109">SQL Server 2012 Reporting Services Deprecated Features</span></span>](#bkmk_2012)  
  
-   [<span data-ttu-id="9e0ee-110">SQL Server 2008 R2 Reporting Services에서 지원되지 않는 기능</span><span class="sxs-lookup"><span data-stu-id="9e0ee-110">SQL Server 2008 R2 Reporting Services Deprecated Features</span></span>](#bkmk_kj)  
  
##  <a name="sql-server-2014-reporting-services-deprecated-features"></a><a name="bkmk_2014"></a><span data-ttu-id="9e0ee-111">SQL Server 2014 Reporting Services 사용 되지 않는 기능</span><span class="sxs-lookup"><span data-stu-id="9e0ee-111">SQL Server 2014 Reporting Services Deprecated Features</span></span>  
  
### <a name="features-not-supported-in-the-next-version-of-sql-server"></a><span data-ttu-id="9e0ee-112">다음 버전의 SQL Server에서 지원되지 않는 기능</span><span class="sxs-lookup"><span data-stu-id="9e0ee-112">Features Not Supported in the Next Version of SQL Server</span></span>  
 <span data-ttu-id="9e0ee-113">다음 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 기능은의 **다음** 버전에서 지원 되지 않습니다 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="9e0ee-113">The following [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] features will not be supported in the **next** version of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="9e0ee-114">새 개발 작업에서는 이러한 기능을 사용하지 말고, 현재 이러한 기능을 사용하는 애플리케이션은 가능한 한 빨리 수정하십시오.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-114">Do not use these features in new development work, and modify applications that currently use these features as soon as possible.</span></span>  
  
#### <a name="html-rendering-extension-device-information-settings"></a><span data-ttu-id="9e0ee-115">HTML 렌더링 확장 프로그램 디바이스 정보 설정</span><span class="sxs-lookup"><span data-stu-id="9e0ee-115">HTML Rendering Extension Device Information Settings</span></span>  
 <span data-ttu-id="9e0ee-116">HTML 렌더링 확장 프로그램에 대한 다음 디바이스 정보 설정은 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-116">The following device information settings for the HTML rendering extension are deprecated.</span></span>  
  
-   <span data-ttu-id="9e0ee-117">ActionScript</span><span class="sxs-lookup"><span data-stu-id="9e0ee-117">ActionScript</span></span>  
  
-   <span data-ttu-id="9e0ee-118">ActiveXControls</span><span class="sxs-lookup"><span data-stu-id="9e0ee-118">ActiveXControls</span></span>  
  
-   <span data-ttu-id="9e0ee-119">GetImage</span><span class="sxs-lookup"><span data-stu-id="9e0ee-119">GetImage</span></span>  
  
-   <span data-ttu-id="9e0ee-120">OnlyVisibleStyles</span><span class="sxs-lookup"><span data-stu-id="9e0ee-120">OnlyVisibleStyles</span></span>  
  
-   <span data-ttu-id="9e0ee-121">ReplacementRoot</span><span class="sxs-lookup"><span data-stu-id="9e0ee-121">ReplacementRoot</span></span>  
  
-   <span data-ttu-id="9e0ee-122">ResourceStreamRoot</span><span class="sxs-lookup"><span data-stu-id="9e0ee-122">ResourceStreamRoot</span></span>  
  
-   <span data-ttu-id="9e0ee-123">StreamRoot</span><span class="sxs-lookup"><span data-stu-id="9e0ee-123">StreamRoot</span></span>  
  
-   <span data-ttu-id="9e0ee-124">UsePx</span><span class="sxs-lookup"><span data-stu-id="9e0ee-124">UsePx</span></span>  
  
-   <span data-ttu-id="9e0ee-125">Zoom</span><span class="sxs-lookup"><span data-stu-id="9e0ee-125">Zoom</span></span>  
  
 <span data-ttu-id="9e0ee-126">HTML 렌더링 확장 프로그램에 자세한 내용은 [HTML Device Information Settings](html-device-information-settings.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-126">For more information on the HTML rendering extension, see [HTML Device Information Settings](html-device-information-settings.md)</span></span>  
  
#### <a name="microsoft-word-and-microsoft-excel-1997-2003-rendering"></a><span data-ttu-id="9e0ee-127">Microsoft Word 및 Microsoft Excel 1997-2003 렌더링</span><span class="sxs-lookup"><span data-stu-id="9e0ee-127">Microsoft Word and Microsoft Excel 1997-2003 Rendering</span></span>  
 <span data-ttu-id="9e0ee-128">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]BIFF8 렌더링 확장 프로그램은 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] [!INCLUDE[msCoName](../includes/msconame-md.md)] Word 및 [!INCLUDE[msCoName](../includes/msconame-md.md)] Excel 1997-2003 이진 교환 파일 형식으로 보고 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-128">The[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] BIFF8 rendering extensions [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] reports to the [!INCLUDE[msCoName](../includes/msconame-md.md)] Word and [!INCLUDE[msCoName](../includes/msconame-md.md)] Excel 1997-2003 binary interchange file format.</span></span> [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]<span data-ttu-id="9e0ee-129">에는 [!INCLUDE[msCoName](../includes/msconame-md.md)] Office 2007-2010 OPEN XML 형식으로 렌더링 되는 확장 프로그램이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-129">includes extensions that render in the [!INCLUDE[msCoName](../includes/msconame-md.md)] Office 2007-2010 Open XML format.</span></span>  
  
#### <a name="report-definition-language-rdl-2005-and-earlier"></a><span data-ttu-id="9e0ee-130">RDL(Report Definition Language) 2005 및 이전</span><span class="sxs-lookup"><span data-stu-id="9e0ee-130">Report Definition Language (RDL) 2005 and Earlier</span></span>  
 <span data-ttu-id="9e0ee-131">RDL(Report Definition Language) 2005 및 이전 버전은 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-131">Report Definition Language (RDL) 2005 and earlier is deprecated.</span></span> <span data-ttu-id="9e0ee-132">RDL에 대 한 자세한 내용은 [SSRS&#41;&#40;Report Definition Language ](reports/report-definition-language-ssrs.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-132">For more information about RDL, see [Report Definition Language &#40;SSRS&#41;](reports/report-definition-language-ssrs.md).</span></span>  
  
 <span data-ttu-id="9e0ee-133">보고서 업그레이드에 대한 자세한 내용은 [Upgrade Reports](install-windows/upgrade-reports.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-133">For more information on upgrading reports, see [Upgrade Reports](install-windows/upgrade-reports.md).</span></span>  
  
#### <a name="sql-server-2005-and-earlier-custom-report-items"></a><span data-ttu-id="9e0ee-134">SQL Server 2005 및 이전 사용자 지정 보고서 항목</span><span class="sxs-lookup"><span data-stu-id="9e0ee-134">SQL Server 2005 and earlier Custom Report Items</span></span>  
 <span data-ttu-id="9e0ee-135">2005 및 이전 버전에 대해 컴파일된 CRI (사용자 지정 보고서 항목) [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 는 더 이상 사용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-135">Custom Report Items (CRI) compiled for [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 2005 and earlier are deprecated.</span></span>  
  
#### <a name="reporting-services-snapshots-2005-and-earlier"></a><span data-ttu-id="9e0ee-136">Reporting Services 스냅샷 2005 및 이전 버전</span><span class="sxs-lookup"><span data-stu-id="9e0ee-136">Reporting Services Snapshots 2005 and earlier</span></span>  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]<span data-ttu-id="9e0ee-137">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 2005 및 이전 버전으로 렌더링 된 스냅숏은 더 이상 사용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-137">snapshots rendered with [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 2005 and earlier are deprecated.</span></span>  
  
#### <a name="report-models"></a><span data-ttu-id="9e0ee-138">보고서 모델</span><span class="sxs-lookup"><span data-stu-id="9e0ee-138">Report Models</span></span>  
 <span data-ttu-id="9e0ee-139">SMDL(Semantic Modeling Language) 보고서 모델은 더 이상 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-139">Semantic modeling language (SMDL) report models are deprecated.</span></span> <span data-ttu-id="9e0ee-140">보고서에서 기존 보고서 모델을 데이터 원본으로 계속 사용할 수 있지만 보고서 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 모델에 대 한 종속성을 제거 하기 위해 보고서를 업데이트 하는 것을 고려해 야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-140">Although you can you continue to use existing report models as data sources in [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)][!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] reports you should consider updating your reports to remove their dependency on report models.</span></span>  
  
 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]<span data-ttu-id="9e0ee-141">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]에는 보고서 모델을 만들거나 업데이트 하기 위한 도구가 포함 되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-141">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] does not include tools for creating or updating report models.</span></span> <span data-ttu-id="9e0ee-142">자세한 내용은 [2014 SQL Server SQL Server Reporting Services의 주요 변경 내용](breaking-changes-in-sql-server-reporting-services-in-sql-server-2016.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-142">For more information, see [Breaking Changes in SQL Server Reporting Services in SQL Server 2014](breaking-changes-in-sql-server-reporting-services-in-sql-server-2016.md).</span></span>  
  
#### <a name="deprecated-methods-in-the-web-service-endpoint"></a><span data-ttu-id="9e0ee-143">웹 서비스 엔드포인트에서 사용되지 않는 메서드</span><span class="sxs-lookup"><span data-stu-id="9e0ee-143">Deprecated Methods in the Web Service Endpoint</span></span>  
 <span data-ttu-id="9e0ee-144">다음 작업은 <xref:ReportService2010.ReportingService2010> 웹 서비스 엔드포인트에서 더 이상 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-144">The following operations are deprecated in the <xref:ReportService2010.ReportingService2010> Web service endpoint:</span></span>  
  
-   <xref:ReportService2010.ReportingService2010.GetProperties%2A>  
  
-   <xref:ReportService2010.ReportingService2010.IsSSLRequired%2A>  
  
#### <a name="sharepoint-web-parts"></a><span data-ttu-id="9e0ee-145">SharePoint 웹 파트</span><span class="sxs-lookup"><span data-stu-id="9e0ee-145">SharePoint Web Parts</span></span>  
 <span data-ttu-id="9e0ee-146">cab 파일에서 추출할 수 있는 설치 캐비닛 파일 **RSWebParts.cab** 및 SharePoint 웹 파트는 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-146">The installation cabinet file **RSWebParts.cab** and the SharePoint web parts that can be extracted from the cab file, are deprecated.</span></span> <span data-ttu-id="9e0ee-147">사용 되지 않는 웹 파트는 보고서 탐색기 (**Spexplorer. .dwp**) 및 보고서 뷰어 (**spexplorer**)입니다.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-147">The deprecated web parts are Report Explorer (**SPExplorer.dwp**) and Report Viewer (**SPViewer.dwp**).</span></span>  
  
 <span data-ttu-id="9e0ee-148">사용 되지 않는 웹 파트에 대 한 자세한 내용은 [SharePoint 웹 파트를 사용 하 여 기본 모드 보고서 보기 및 탐색 (SSRS)](https://msdn.microsoft.com/library/ms159772.aspx) 을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-148">For more information on the deprecated web parts, see [View and Explore Native Mode Reports Using SharePoint Web Parts (SSRS)](https://msdn.microsoft.com/library/ms159772.aspx)</span></span>  
  
### <a name="features-not-supported-in-a-future-version-of-sql-server"></a><span data-ttu-id="9e0ee-149">이후 버전의 SQL Server에서 지원되지 않는 기능</span><span class="sxs-lookup"><span data-stu-id="9e0ee-149">Features Not Supported in a Future Version of SQL Server</span></span>  
 <span data-ttu-id="9e0ee-150">아래의 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 기능은 다음 버전의 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]에서 지원되지만 이후 버전에서는 제거될 예정입니다.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-150">The following [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] features are supported in the next version of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], but will be removed in a later version.</span></span> <span data-ttu-id="9e0ee-151">어떤 버전의 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 에서 제거될지는 결정되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-151">The specific version of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] has not been determined.</span></span>  
  
 <span data-ttu-id="9e0ee-152">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 에서 사용되지 않는 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]기능은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-152">No [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] features were deprecated in [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].</span></span>  
  
##  <a name="sql-server-2012-sp1-reporting-services-deprecated-features"></a><a name="bkmk_2012sp1"></a><span data-ttu-id="9e0ee-153">SQL Server 2012 SP1 Reporting Services 사용 되지 않는 기능</span><span class="sxs-lookup"><span data-stu-id="9e0ee-153">SQL Server 2012 SP1 Reporting Services Deprecated Features</span></span>  
 <span data-ttu-id="9e0ee-154">이 섹션에서는 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 에서 지원되지 않는 [!INCLUDE[ssSQL11SP1](../includes/sssql11sp1-md.md)]기능에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-154">This section describes [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] features deprecated in [!INCLUDE[ssSQL11SP1](../includes/sssql11sp1-md.md)].</span></span> <span data-ttu-id="9e0ee-155">아래의 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 기능은 다음 버전의 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]에서 지원되지만 이후 버전에서는 제거될 예정입니다.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-155">The following [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] features are supported in the next version of [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], but will be removed in a later version.</span></span> <span data-ttu-id="9e0ee-156">어떤 버전의 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 에서 제거될지는 결정되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-156">The specific version of [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] has not been determined.</span></span>  
  
### <a name="sharepoint-web-parts"></a><span data-ttu-id="9e0ee-157">SharePoint 웹 파트</span><span class="sxs-lookup"><span data-stu-id="9e0ee-157">SharePoint Web Parts</span></span>  
 <span data-ttu-id="9e0ee-158">cab 파일에서 추출할 수 있는 설치 캐비닛 파일 **RSWebParts.cab** 및 SharePoint 웹 파트는 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-158">The installation cabinet file **RSWebParts.cab** and the SharePoint web parts that can be extracted from the cab file, are deprecated.</span></span> <span data-ttu-id="9e0ee-159">사용 되지 않는 웹 파트는 보고서 탐색기 (**Spexplorer. .dwp**) 및 보고서 뷰어 (**spexplorer**)입니다.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-159">The deprecated web parts are Report Explorer (**SPExplorer.dwp**) and Report Viewer (**SPViewer.dwp**).</span></span>  
  
 <span data-ttu-id="9e0ee-160">사용 되지 않는 웹 파트에 대 한 자세한 내용은 [SharePoint 웹 파트를 사용 하 여 기본 모드 보고서 보기 및 탐색 (SSRS)](https://msdn.microsoft.com/library/ms159772.aspx) 을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-160">For more information on the deprecated web parts, see [View and Explore Native Mode Reports Using SharePoint Web Parts (SSRS)](https://msdn.microsoft.com/library/ms159772.aspx)</span></span>  
  
##  <a name="sql-server-2012-reporting-services-deprecated-features"></a><a name="bkmk_2012"></a><span data-ttu-id="9e0ee-161">SQL Server 2012 Reporting Services 사용 되지 않는 기능</span><span class="sxs-lookup"><span data-stu-id="9e0ee-161">SQL Server 2012 Reporting Services Deprecated Features</span></span>  
 <span data-ttu-id="9e0ee-162">이 섹션에서는 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 에서 지원되지 않는 [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]기능에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-162">This section describes [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] features deprecated in [!INCLUDE[ssSQL11](../includes/sssql11-md.md)].</span></span>  
  
### <a name="html-rendering-extension-device-information-settings"></a><span data-ttu-id="9e0ee-163">HTML 렌더링 확장 프로그램 디바이스 정보 설정</span><span class="sxs-lookup"><span data-stu-id="9e0ee-163">HTML Rendering Extension Device Information Settings</span></span>  
 <span data-ttu-id="9e0ee-164">HTML 렌더링 확장 프로그램에 대한 다음 디바이스 정보 설정은 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-164">The following device information settings for the HTML rendering extension are deprecated.</span></span>  
  
-   <span data-ttu-id="9e0ee-165">ActionScript</span><span class="sxs-lookup"><span data-stu-id="9e0ee-165">ActionScript</span></span>  
  
-   <span data-ttu-id="9e0ee-166">ActiveXControls</span><span class="sxs-lookup"><span data-stu-id="9e0ee-166">ActiveXControls</span></span>  
  
-   <span data-ttu-id="9e0ee-167">GetImage</span><span class="sxs-lookup"><span data-stu-id="9e0ee-167">GetImage</span></span>  
  
-   <span data-ttu-id="9e0ee-168">OnlyVisibleStyles</span><span class="sxs-lookup"><span data-stu-id="9e0ee-168">OnlyVisibleStyles</span></span>  
  
-   <span data-ttu-id="9e0ee-169">ReplacementRoot</span><span class="sxs-lookup"><span data-stu-id="9e0ee-169">ReplacementRoot</span></span>  
  
-   <span data-ttu-id="9e0ee-170">ResourceStreamRoot</span><span class="sxs-lookup"><span data-stu-id="9e0ee-170">ResourceStreamRoot</span></span>  
  
-   <span data-ttu-id="9e0ee-171">StreamRoot</span><span class="sxs-lookup"><span data-stu-id="9e0ee-171">StreamRoot</span></span>  
  
-   <span data-ttu-id="9e0ee-172">UsePx</span><span class="sxs-lookup"><span data-stu-id="9e0ee-172">UsePx</span></span>  
  
-   <span data-ttu-id="9e0ee-173">Zoom</span><span class="sxs-lookup"><span data-stu-id="9e0ee-173">Zoom</span></span>  
  
 <span data-ttu-id="9e0ee-174">HTML 렌더링 확장 프로그램에 자세한 내용은 [HTML Device Information Settings](html-device-information-settings.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-174">For more information on the HTML rendering extension, see [HTML Device Information Settings](html-device-information-settings.md)</span></span>  
  
### <a name="microsoft-word-and-microsoft-excel-1997-2003-rendering"></a><span data-ttu-id="9e0ee-175">Microsoft Word 및 Microsoft Excel 1997-2003 렌더링</span><span class="sxs-lookup"><span data-stu-id="9e0ee-175">Microsoft Word and Microsoft Excel 1997-2003 Rendering</span></span>  
 <span data-ttu-id="9e0ee-176">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]BIFF8 렌더링 확장 프로그램은 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] [!INCLUDE[msCoName](../includes/msconame-md.md)] Word 및 [!INCLUDE[msCoName](../includes/msconame-md.md)] Excel 1997-2003 이진 교환 파일 형식으로 보고 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-176">The[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] BIFF8 rendering extensions [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] reports to the [!INCLUDE[msCoName](../includes/msconame-md.md)] Word and [!INCLUDE[msCoName](../includes/msconame-md.md)] Excel 1997-2003 binary interchange file format.</span></span> [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]<span data-ttu-id="9e0ee-177">에는 [!INCLUDE[msCoName](../includes/msconame-md.md)] Office 2007-2010 OPEN XML 형식으로 렌더링 되는 확장 프로그램이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-177">includes extensions that render in the [!INCLUDE[msCoName](../includes/msconame-md.md)] Office 2007-2010 Open XML format.</span></span>  
  
### <a name="report-definition-language-rdl-2005-and-earlier"></a><span data-ttu-id="9e0ee-178">RDL(Report Definition Language) 2005 및 이전</span><span class="sxs-lookup"><span data-stu-id="9e0ee-178">Report Definition Language (RDL) 2005 and Earlier</span></span>  
 <span data-ttu-id="9e0ee-179">RDL(Report Definition Language) 2005 및 이전 버전은 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-179">Report Definition Language (RDL) 2005 and earlier is deprecated.</span></span> <span data-ttu-id="9e0ee-180">RDL에 대 한 자세한 내용은 [SSRS&#41;&#40;Report Definition Language ](reports/report-definition-language-ssrs.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-180">For more information about RDL, see [Report Definition Language &#40;SSRS&#41;](reports/report-definition-language-ssrs.md).</span></span>  
  
 <span data-ttu-id="9e0ee-181">보고서 업그레이드에 대한 자세한 내용은 [Upgrade Reports](install-windows/upgrade-reports.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-181">For more information on upgrading reports, see [Upgrade Reports](install-windows/upgrade-reports.md).</span></span>  
  
### <a name="sql-server-2005-and-earlier-custom-report-items"></a><span data-ttu-id="9e0ee-182">SQL Server 2005 및 이전 사용자 지정 보고서 항목</span><span class="sxs-lookup"><span data-stu-id="9e0ee-182">SQL Server 2005 and earlier Custom Report Items</span></span>  
 <span data-ttu-id="9e0ee-183">2005 및 이전 버전에 대해 컴파일된 CRI (사용자 지정 보고서 항목) [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 는 더 이상 사용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-183">Custom Report Items (CRI) compiled for [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 2005 and earlier are deprecated.</span></span>  
  
### <a name="reporting-services-snapshots-2005-and-earlier"></a><span data-ttu-id="9e0ee-184">Reporting Services 스냅샷 2005 및 이전 버전</span><span class="sxs-lookup"><span data-stu-id="9e0ee-184">Reporting Services Snapshots 2005 and earlier</span></span>  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]<span data-ttu-id="9e0ee-185">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 2005 및 이전 버전으로 렌더링 된 스냅숏은 더 이상 사용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-185">snapshots rendered with [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 2005 and earlier are deprecated.</span></span>  
  
### <a name="report-models"></a><span data-ttu-id="9e0ee-186">보고서 모델</span><span class="sxs-lookup"><span data-stu-id="9e0ee-186">Report Models</span></span>  
 <span data-ttu-id="9e0ee-187">SMDL(Semantic Modeling Language) 보고서 모델은 더 이상 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-187">Semantic modeling language (SMDL) report models are deprecated.</span></span> <span data-ttu-id="9e0ee-188">보고서에서 기존 보고서 모델을 데이터 원본으로 계속 사용할 수 있지만 보고서 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 모델에 대 한 종속성을 제거 하기 위해 보고서를 업데이트 하는 것을 고려해 야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-188">Although you can you continue to use existing report models as data sources in [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)][!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] reports you should consider updating your reports to remove their dependency on report models.</span></span>  
  
 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]<span data-ttu-id="9e0ee-189">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]에는 보고서 모델을 만들거나 업데이트 하기 위한 도구가 포함 되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-189">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] does not include tools for creating or updating report models.</span></span> <span data-ttu-id="9e0ee-190">자세한 내용은 [2014 SQL Server SQL Server Reporting Services의 주요 변경 내용](breaking-changes-in-sql-server-reporting-services-in-sql-server-2016.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-190">For more information, see [Breaking Changes in SQL Server Reporting Services in SQL Server 2014](breaking-changes-in-sql-server-reporting-services-in-sql-server-2016.md).</span></span>  
  
### <a name="deprecated-methods-in-the-web-service-endpoint"></a><span data-ttu-id="9e0ee-191">웹 서비스 엔드포인트에서 사용되지 않는 메서드</span><span class="sxs-lookup"><span data-stu-id="9e0ee-191">Deprecated Methods in the Web Service Endpoint</span></span>  
 <span data-ttu-id="9e0ee-192">다음 작업은 <xref:ReportService2010.ReportingService2010> 웹 서비스 엔드포인트에서 더 이상 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-192">The following operations are deprecated in the <xref:ReportService2010.ReportingService2010> Web service endpoint:</span></span>  
  
-   <xref:ReportService2010.ReportingService2010.GetProperties%2A>  
  
-   <xref:ReportService2010.ReportingService2010.IsSSLRequired%2A>  
  
##  <a name="sql-server-2008-r2-reporting-services-deprecated-features"></a><a name="bkmk_kj"></a><span data-ttu-id="9e0ee-193">SQL Server 2008 R2 Reporting Services 사용 되지 않는 기능</span><span class="sxs-lookup"><span data-stu-id="9e0ee-193">SQL Server 2008 R2 Reporting Services Deprecated Features</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9e0ee-194">SQL Server 2008 R2는 SQL Server 2008의 부 버전 업그레이드이므로 SQL Server 2008 섹션의 내용도 검토하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-194">Because SQL Server 2008 R2 is a minor version upgrade of SQL Server 2008, we recommend that you also review the content in the SQL Server 2008 section.</span></span>  
  
### <a name="report-server-web-service-endpoints"></a><span data-ttu-id="9e0ee-195">보고서 서버 웹 서비스 엔드포인트</span><span class="sxs-lookup"><span data-stu-id="9e0ee-195">Report Server Web Service Endpoints</span></span>  
 <span data-ttu-id="9e0ee-196">이 릴리스에서는 웹 서비스 <xref:ReportService2005.ReportingService2005> 및 <xref:ReportService2006.ReportingService2006>이 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-196">The Web services <xref:ReportService2005.ReportingService2005> and <xref:ReportService2006.ReportingService2006> have been deprecated in this release.</span></span> <span data-ttu-id="9e0ee-197">이러한 엔드포인트는 새 엔드포인트인 <xref:ReportService2010.ReportingService2010>로 대체되었습니다.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-197">These endpoints have been replaced by a new endpoint: <xref:ReportService2010.ReportingService2010>.</span></span>  
  
 <span data-ttu-id="9e0ee-198">새 엔드포인트에는 사용되지 않는 엔드포인트에서 제공하던 모든 기능과 SQL Server 2008 R2에 추가된 새 기능이 모두 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-198">The new endpoint includes all the functionality available in the deprecated endpoints and the new features introduced in SQL Server 2008 R2.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e0ee-199">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9e0ee-199">See Also</span></span>  
 <span data-ttu-id="9e0ee-200">[새로운 기능 &#40;Reporting Services&#41;](what-s-new-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="9e0ee-200">[What's New &#40;Reporting Services&#41;](what-s-new-reporting-services.md) </span></span>  
 <span data-ttu-id="9e0ee-201">[이전 버전과의 호환성](../getting-started/backward-compatibility.md) </span><span class="sxs-lookup"><span data-stu-id="9e0ee-201">[Backward Compatibility](../getting-started/backward-compatibility.md) </span></span>  
 <span data-ttu-id="9e0ee-202">[SQL Server 2014의 SQL Server Reporting Services에 대 한 동작 변경 내용](behavior-changes-to-sql-server-reporting-services-in-sql-server-2016.md) </span><span class="sxs-lookup"><span data-stu-id="9e0ee-202">[Behavior Changes to SQL Server Reporting Services  in SQL Server 2014](behavior-changes-to-sql-server-reporting-services-in-sql-server-2016.md) </span></span>  
 [<span data-ttu-id="9e0ee-203">SQL Server 2014의 SQL Server Reporting Services에서 중단된 기능</span><span class="sxs-lookup"><span data-stu-id="9e0ee-203">Discontinued Functionality to SQL Server Reporting Services in SQL Server 2014</span></span>](discontinued-functionality-to-sql-server-reporting-services-in-sql-server.md)  
  
  
