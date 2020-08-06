---
title: SharePoint용 PowerPivot (SSAS) | Microsoft Docs
ms.custom: ''
ms.date: 11/25/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: c4c393d3-4856-47ac-ab5f-15da2f240d1d
author: minewiskan
ms.author: owend
ms.openlocfilehash: 58ebcf004224d21ab5b47aaee1e2e7e3ef2047ad
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651323"
---
# <a name="powerpivot-for-sharepoint-ssas"></a><span data-ttu-id="fedf5-102">SharePoint용 PowerPivot(SSAS)</span><span class="sxs-lookup"><span data-stu-id="fedf5-102">PowerPivot for SharePoint (SSAS)</span></span>
  <span data-ttu-id="fedf5-103">SharePoint용 PowerPivot은 SharePoint 모드에서 실행되는 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 서버입니다.</span><span class="sxs-lookup"><span data-stu-id="fedf5-103">PowerPivot for SharePoint is a [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] server running in SharePoint mode.</span></span> <span data-ttu-id="fedf5-104">SharePoint용 PowerPivot은 SharePoint 팜에서 PowerPivot 데이터의 서버 호스팅을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="fedf5-104">PowerPivot for SharePoint provides server hosting of PowerPivot data in a SharePoint farm.</span></span> <span data-ttu-id="fedf5-105">PowerPivot 데이터는 다음 중 하나를 사용하여 빌드하는 분석 데이터 모델입니다.</span><span class="sxs-lookup"><span data-stu-id="fedf5-105">PowerPivot data is an analytical data model that you build using one of the following:</span></span>  
  
-   <span data-ttu-id="fedf5-106">PowerPivot for Excel 2010 추가 기능</span><span class="sxs-lookup"><span data-stu-id="fedf5-106">The PowerPivot for Excel 2010 add-in</span></span>  
  
-   <span data-ttu-id="fedf5-107">Excel 2013</span><span class="sxs-lookup"><span data-stu-id="fedf5-107">Excel 2013</span></span>  
  
 <span data-ttu-id="fedf5-108">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]2013 | [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]2010</span><span class="sxs-lookup"><span data-stu-id="fedf5-108">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2013 | [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2010</span></span>  
  
 <span data-ttu-id="fedf5-109">이 데이터의 서버 호스팅에는 SharePoint, Excel 서비스 및 SharePoint용 PowerPivot 설치가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="fedf5-109">Server hosting of that data requires SharePoint, Excel Services, and an installation of PowerPivot for SharePoint.</span></span> <span data-ttu-id="fedf5-110">데이터는 SharePoint용 PowerPivot 인스턴스에 로드되며 여기서 서버가 Excel 2010 통합 문서용으로 제공하거나 SharePoint 2013 Excel 서비스가 Excel 2013 통합 문서용으로 제공하는 PowerPivot 데이터 새로 고침 기능을 사용하여 예약된 간격으로 데이터를 새로 고칠 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fedf5-110">Data is loaded on PowerPivot for SharePoint instances where it can be refreshed at scheduled intervals using the PowerPivot data refresh capability that the server provides for Excel 2010 workbooks or that SharePoint 2013 Excel Services provides for Excel 2013 workbooks.</span></span>  
  
## <a name="powerpivot-for-sharepoint-2013"></a><span data-ttu-id="fedf5-111">SharePoint 2013용 PowerPivot</span><span class="sxs-lookup"><span data-stu-id="fedf5-111">PowerPivot for SharePoint 2013</span></span>  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<span data-ttu-id="fedf5-112">[!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]지원 [!INCLUDE[msCoName](../../includes/msconame-md.md)] SharePoint 2013 Excel 서비스는 데이터 모델 및 파워 뷰 보고서를 포함 하는 Excel 통합 문서를 사용 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="fedf5-112">[!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] supports [!INCLUDE[msCoName](../../includes/msconame-md.md)] SharePoint 2013 Excel Services usage of Excel workbooks containing data models and [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Power View reports.</span></span>  
  
 <span data-ttu-id="fedf5-113">SharePoint 2013의 Excel Services에는 브라우저에서 PowerPivot 통합 문서와 상호 작용할 수 있도록 데이터 모델 기능이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fedf5-113">Excel Services in SharePoint 2013 includes data model functionality to enable interaction with a PowerPivot workbook in the browser.</span></span> <span data-ttu-id="fedf5-114">SharePoint 2013용 PowerPivot 추가 기능을 팜에 배포하지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fedf5-114">You do not need to deploy the PowerPivot for SharePoint 2013 add-in into the farm.</span></span> <span data-ttu-id="fedf5-115">SharePoint 모드의 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 서버를 설치하고 Excel Services **데이터 모델** 설정 내에 서버를 등록해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fedf5-115">You only need to install an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] server in SharePoint mode and register the server within the Excel Services **Data Model** settings.</span></span>  
  
 <span data-ttu-id="fedf5-116">SharePoint 2013용 PowerPivot 추가 기능을 배포하면 추가 기능 및 SharePoint 팜의 기능을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fedf5-116">Deploying the PowerPivot for SharePoint 2013 add-in enables additional functionality and features in your SharePoint farm.</span></span> <span data-ttu-id="fedf5-117">추가 기능에는 PowerPivot 갤러리, 데이터 새로 고침 예약 및 PowerPivot 관리 대시보드가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fedf5-117">The additional features include PowerPivot Gallery, Schedule Data Refresh, and the PowerPivot Management Dashboard.</span></span>  
  
 <span data-ttu-id="fedf5-118">![SSAS PowerPivot 모드 2 서버 배포](../media/as-powerpivot-mode-2server-deployment.gif "SSAS PowerPivot 모드 2 서버 배포")</span><span class="sxs-lookup"><span data-stu-id="fedf5-118">![SSAS PowerPivot Mode 2 Server Deployment](../media/as-powerpivot-mode-2server-deployment.gif "SSAS PowerPivot Mode 2 Server Deployment")</span></span>  
  
## <a name="powerpivot-for-sharepoint-2010"></a><span data-ttu-id="fedf5-119">SharePoint용 PowerPivot 2010</span><span class="sxs-lookup"><span data-stu-id="fedf5-119">PowerPivot for SharePoint 2010</span></span>  
 <span data-ttu-id="fedf5-120">SharePoint용 PowerPivot 2010은 SharePoint 2010 팜에서 PowerPivot 데이터의 서버 호스팅을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="fedf5-120">PowerPivot for SharePoint 2010 provides server hosting of PowerPivot data in a SharePoint 2010 farm.</span></span> <span data-ttu-id="fedf5-121">PowerPivot 데이터는 PowerPivot for Excel 추가 기능을 사용하여 Excel에서 작성하는 분석 데이터 모델입니다.</span><span class="sxs-lookup"><span data-stu-id="fedf5-121">PowerPivot data is an analytical data model that you build in Excel using the PowerPivot for Excel add-in.</span></span> <span data-ttu-id="fedf5-122">이 데이터의 서버 호스팅에는 SharePoint 2010, Excel 서비스 및 SharePoint용 PowerPivot 설치가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="fedf5-122">Server hosting of that data requires SharePoint 2010, Excel Services, and an installation of PowerPivot for SharePoint.</span></span> <span data-ttu-id="fedf5-123">데이터는 팜에서 SharePoint용 PowerPivot 인스턴스에 로드되며 여기서 서버가 제공하는 PowerPivot 데이터 새로 고침 기능을 사용하여 예약된 간격으로 데이터를 새로 고칠 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fedf5-123">Data is loaded on PowerPivot for SharePoint instances in the farm, where it can be refreshed at scheduled intervals using the PowerPivot data refresh capability that the server provides.</span></span>  
  
### <a name="components-of-powerpivot-for-sharepoint-2010"></a><span data-ttu-id="fedf5-124">SharePoint용 PowerPivot 2010의 구성 요소</span><span class="sxs-lookup"><span data-stu-id="fedf5-124">Components of PowerPivot for SharePoint 2010</span></span>  
 <span data-ttu-id="fedf5-125">SharePoint용 PowerPivot은 공유 서비스로 구현되므로 기본 제공 기능과 인프라를 사용하여 PowerPivot 서비스 애플리케이션을 관리, 보호 및 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fedf5-125">PowerPivot for SharePoint is implemented as a shared service, which means that the built-in features and infrastructure can be used to administer, secure, and use a PowerPivot service application.</span></span> <span data-ttu-id="fedf5-126">서버 및 데이터 검색, 리디렉션 및 연결 관리는 모두 팜 수준에서 관리됩니다.</span><span class="sxs-lookup"><span data-stu-id="fedf5-126">Server and database discovery, redirection, and connection management is all managed at the farm level.</span></span> <span data-ttu-id="fedf5-127">중앙 관리는 서버 ID, 서버 상태 및 구성 속성을 관리하는 데 사용되는 서비스에 관리 인터페이스를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="fedf5-127">Central Administration provides the administrative interface to the services used to manage server identity, server state, and configuration properties.</span></span>  
  
 <span data-ttu-id="fedf5-128">SharePoint용 PowerPivot의 전체 배포에는 SharePoint 팜에서 Excel 및 Excel 서비스와 통합되는 클라이언트 및 서버 구성 요소가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="fedf5-128">A complete deployment of PowerPivot for SharePoint includes client and server components that integrate with Excel and Excel Services in a SharePoint farm.</span></span> <span data-ttu-id="fedf5-129">Excel 통합 문서 내부의 PowerPivot 데이터는 데이터를 로드하고 쿼리하기 위해 Analysis Services xVelocity 메모리 내 분석 엔진(VertiPaq)이 필요한 Analysis Services 데이터베이스입니다.</span><span class="sxs-lookup"><span data-stu-id="fedf5-129">The PowerPivot data inside an Excel workbook is an Analysis Services database that requires an Analysis Services xVelocity in-memory analytics engine (VertiPaq) to load and query the data.</span></span> <span data-ttu-id="fedf5-130">클라이언트 워크스테이션에서 xVelocity 엔진은 Excel 내에서 in-process로 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="fedf5-130">On a client workstation, the xVelocity engine runs in-process within Excel.</span></span> <span data-ttu-id="fedf5-131">SharePoint 팜에서 Analysis Services는 PowerPivot 데이터에 대한 요청을 처리하는 관련 서비스와 함께 애플리케이션 서버에서 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="fedf5-131">On a SharePoint farm, Analysis Services runs on an application server where it is paired with related services that handle requests for PowerPivot data.</span></span> <span data-ttu-id="fedf5-132">다음 다이어그램에서는 PowerPivot 클라이언트와 서버 구성 요소를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="fedf5-132">The following diagram illustrates PowerPivot client and server components:</span></span>  
  
 <span data-ttu-id="fedf5-133">![GMNI_GeminiArch2](../media/gmni-geminiarch2.gif "GMNI_GeminiArch2")</span><span class="sxs-lookup"><span data-stu-id="fedf5-133">![GMNI_GeminiArch2](../media/gmni-geminiarch2.gif "GMNI_GeminiArch2")</span></span>  
  
 <span data-ttu-id="fedf5-134">PowerPivot 웹 서비스는 웹 애플리케이션 서버에서 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="fedf5-134">PowerPivot Web service runs on a web application server.</span></span> <span data-ttu-id="fedf5-135">이 서비스는 웹 애플리케이션에서 팜의 PowerPivot 시스템 서비스 인스턴스로 요청을 리디렉션합니다.</span><span class="sxs-lookup"><span data-stu-id="fedf5-135">It redirects requests from the web application to a PowerPivot System Service instance in the farm.</span></span>  
  
 <span data-ttu-id="fedf5-136">PowerPivot 시스템 서비스는 Analysis Services에 대한 로드 요청을 실행하고 메모리에 이미 로드되어 있는 데이터에 대해 진행 중인 연결을 관리하며 데이터가 더 이상 사용되지 않거나 시스템 리소스에 대한 경합이 있는 경우 데이터를 캐시하거나 언로드합니다.</span><span class="sxs-lookup"><span data-stu-id="fedf5-136">PowerPivot System Service issues load requests to the Analysis Services server and manages ongoing connections to data that is already loaded in memory, caching or unloading data if it is no longer used or when there is contention for system resources.</span></span> <span data-ttu-id="fedf5-137">사용자 작업도 추적합니다.</span><span class="sxs-lookup"><span data-stu-id="fedf5-137">It also tracks user activity.</span></span> <span data-ttu-id="fedf5-138">서버 상태 데이터 및 기타 사용량 현황 데이터가 수집되고 보고서에 표시되어 시스템 성능을 파악할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fedf5-138">Server health data and other usage data is gathered and presented in reports to indicate how well the system is performing.</span></span>  
  
 <span data-ttu-id="fedf5-139">SharePoint 통합 모드의 Analysis Service 서비스 인스턴스는 배포를 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="fedf5-139">An Analysis Service server instance in SharePoint integrated mode completes the deployment.</span></span> <span data-ttu-id="fedf5-140">이 인스턴스는 데이터를 로드, 쿼리 및 언로드합니다.</span><span class="sxs-lookup"><span data-stu-id="fedf5-140">It loads, queries, and unloads data.</span></span> <span data-ttu-id="fedf5-141">또한 이 인스턴스는 통합 문서가 PowerPivot 데이터 새로 고침에 대해 구성된 경우 데이터도 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="fedf5-141">It also processes data if the workbook is configured for PowerPivot data refresh.</span></span>  <span data-ttu-id="fedf5-142">각 인스턴스는 동일한 설치에 속하는 로컬 PowerPivot 시스템 서비스와 긴밀하게 결합됩니다.</span><span class="sxs-lookup"><span data-stu-id="fedf5-142">Each instance is tightly coupled with the local PowerPivot System Service that is part of the same installation.</span></span>  
  
##  <a name="in-this-section"></a><a name="bkmk_RelatedContent"></a> <span data-ttu-id="fedf5-143">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="fedf5-143">In This Section</span></span>  
 [<span data-ttu-id="fedf5-144">중앙 관리에서 PowerPivot 서버 관리 및 구성</span><span class="sxs-lookup"><span data-stu-id="fedf5-144">PowerPivot Server Administration and Configuration in Central Administration</span></span>](power-pivot-server-administration-and-configuration-in-central-administration.md)  
  
 [<span data-ttu-id="fedf5-145">Windows PowerShell을 사용하여 PowerPivot 구성</span><span class="sxs-lookup"><span data-stu-id="fedf5-145">PowerPivot Configuration using Windows PowerShell</span></span>](power-pivot-configuration-using-windows-powershell.md)  
  
 [<span data-ttu-id="fedf5-146">PowerPivot Configuration Tools</span><span class="sxs-lookup"><span data-stu-id="fedf5-146">PowerPivot Configuration Tools</span></span>](power-pivot-configuration-tools.md)  
  
 [<span data-ttu-id="fedf5-147">PowerPivot 인증 및 권한 부여</span><span class="sxs-lookup"><span data-stu-id="fedf5-147">PowerPivot Authentication and Authorization</span></span>](power-pivot-authentication-and-authorization.md)  
  
 [<span data-ttu-id="fedf5-148">PowerPivot 상태 규칙 - 구성</span><span class="sxs-lookup"><span data-stu-id="fedf5-148">PowerPivot Health Rules - Configure</span></span>](configure-power-pivot-health-rules.md)  
  
 [<span data-ttu-id="fedf5-149">PowerPivot 관리 대시보드 및 사용량 현황 데이터</span><span class="sxs-lookup"><span data-stu-id="fedf5-149">PowerPivot Management Dashboard and Usage Data</span></span>](power-pivot-management-dashboard-and-usage-data.md)  
  
 [<span data-ttu-id="fedf5-150">PowerPivot 갤러리</span><span class="sxs-lookup"><span data-stu-id="fedf5-150">PowerPivot Gallery</span></span>](../../index.yml)  
  
 [<span data-ttu-id="fedf5-151">PowerPivot 데이터 액세스</span><span class="sxs-lookup"><span data-stu-id="fedf5-151">PowerPivot Data Access</span></span>](power-pivot-data-access.md)  
  
 [<span data-ttu-id="fedf5-152">PowerPivot 데이터 새로 고침</span><span class="sxs-lookup"><span data-stu-id="fedf5-152">PowerPivot Data Refresh</span></span>](power-pivot-data-refresh.md)  
  
 [<span data-ttu-id="fedf5-153">PowerPivot 데이터 피드</span><span class="sxs-lookup"><span data-stu-id="fedf5-153">PowerPivot Data Feeds</span></span>](power-pivot-data-feeds.md)  
  
 [<span data-ttu-id="fedf5-154">PowerPivot BI 의미 체계 모델 연결 &#40;. bism&#41;</span><span class="sxs-lookup"><span data-stu-id="fedf5-154">PowerPivot BI Semantic Model Connection &#40;.bism&#41;</span></span>](power-pivot-bi-semantic-model-connection-bism.md)  
  
 <span data-ttu-id="fedf5-155">**다른 섹션**</span><span class="sxs-lookup"><span data-stu-id="fedf5-155">**In other sections**</span></span>  
  
## <a name="additional-topics"></a><span data-ttu-id="fedf5-156">추가 항목</span><span class="sxs-lookup"><span data-stu-id="fedf5-156">Additional topics</span></span>  
 [<span data-ttu-id="fedf5-157">SharePoint용 PowerPivot 업그레이드</span><span class="sxs-lookup"><span data-stu-id="fedf5-157">Upgrade PowerPivot for SharePoint</span></span>](../../database-engine/install-windows/upgrade-power-pivot-for-sharepoint.md)  
  
 [<span data-ttu-id="fedf5-158">SharePoint 2013용 PowerPivot 설치</span><span class="sxs-lookup"><span data-stu-id="fedf5-158">PowerPivot for SharePoint 2013 Installation</span></span>](../instances/install-windows/install-analysis-services-in-power-pivot-mode.md)  
  
 [<span data-ttu-id="fedf5-159">SharePoint용 PowerPivot에 대한 PowerShell 참조</span><span class="sxs-lookup"><span data-stu-id="fedf5-159">PowerShell Reference for PowerPivot for SharePoint</span></span>](/sql/analysis-services/powershell/powershell-reference-for-power-pivot-for-sharepoint)  
  
 [<span data-ttu-id="fedf5-160">SQL Server 2014 셀프 서비스 비즈니스 인텔리전스에 대 한 예제 라이선스 토폴로지 및 비용</span><span class="sxs-lookup"><span data-stu-id="fedf5-160">Example License Topologies and Costs  for SQL Server 2014 Self-Service Business Intelligence</span></span>](../../sql-server/install/example-license-topologies-costs-self-service-business-intelligence.md)  
  
## <a name="see-also"></a><span data-ttu-id="fedf5-161">참고 항목</span><span class="sxs-lookup"><span data-stu-id="fedf5-161">See Also</span></span>  
 <span data-ttu-id="fedf5-162">[PowerPivot 계획 및 배포](https://go.microsoft.com/fwlink/?linkID=220972) </span><span class="sxs-lookup"><span data-stu-id="fedf5-162">[PowerPivot Planning and Deployment](https://go.microsoft.com/fwlink/?linkID=220972) </span></span>  
 [<span data-ttu-id="fedf5-163">SharePoint용 PowerPivot 재해 복구</span><span class="sxs-lookup"><span data-stu-id="fedf5-163">Disaster Recovery for PowerPivot for SharePoint</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389570)  
  
  
