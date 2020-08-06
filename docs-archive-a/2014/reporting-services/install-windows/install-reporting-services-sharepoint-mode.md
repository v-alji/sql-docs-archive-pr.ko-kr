---
title: SharePoint 모드 설치 Reporting Services (SharePoint 2010 및 SharePoint 2013) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- default configuration [Reporting Services]
- installing Reporting Services, SharePoint integrated mode
- installation options [Reporting Services]
ms.assetid: ac6cba68-2665-4a39-8fa3-cb7d7e6723c0
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c27b6f9fbeebcc896b1a6097cb51e8d2e15924bf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646832"
---
# <a name="reporting-services-sharepoint-mode-installation-sharepoint-2010-and-sharepoint-2013"></a><span data-ttu-id="7f621-102">Reporting Services SharePoint 모드 설치(SharePoint 2010 및 SharePoint 2013)</span><span class="sxs-lookup"><span data-stu-id="7f621-102">Reporting Services SharePoint Mode Installation (SharePoint 2010 and SharePoint 2013)</span></span>
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]<span data-ttu-id="7f621-103">에서 SharePoint 모드는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 및 SharePoint 제품을 기반으로 보고서 생성 및 배달을 제공 하는 서버 구성 요소의 모음입니다 [!INCLUDE[msCoName](../../includes/msconame-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="7f621-103">in SharePoint mode is a collection of server components that provide report generation and delivery, based on [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and [!INCLUDE[msCoName](../../includes/msconame-md.md)] SharePoint products.</span></span>  
  
 <span data-ttu-id="7f621-104">SharePoint 모드에서 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]를 실행하면 [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] 및 데이터 경고 기능을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7f621-104">Running [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in SharePoint mode provides the [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] and data alerting features.</span></span> <span data-ttu-id="7f621-105">SharePoint 모드의 기능에 대 한 자세한 내용은 [Reporting Services Report Server](../reporting-services-report-server.md) 의 "서버 모드의 기능 지원 및 동작 차이점" 섹션을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="7f621-105">For more information regarding features in SharePoint mode, see the section "Feature Support and Behavior Differences by Server Mode" in [Reporting Services Report Server](../reporting-services-report-server.md)</span></span>  
  
 <span data-ttu-id="7f621-106">SharePoint 모드의 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]에는 기본적으로 두 가지 설치가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="7f621-106">There are two fundamental installations needed for [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in SharePoint mode:</span></span>  
  
|<span data-ttu-id="7f621-107">설치</span><span class="sxs-lookup"><span data-stu-id="7f621-107">Installation</span></span>|<span data-ttu-id="7f621-108">Description</span><span class="sxs-lookup"><span data-stu-id="7f621-108">Description</span></span>|  
|------------------|-----------------|  
|<span data-ttu-id="7f621-109">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint 제품용 추가 기능</span><span class="sxs-lookup"><span data-stu-id="7f621-109">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] add-in for SharePoint products.</span></span>|<span data-ttu-id="7f621-110">이 추가 기능은 SharePoint 웹 프런트 엔드 서버에 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] UI(사용자 인터페이스) 페이지 및 기능을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="7f621-110">The add-in installs the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] user interface (UI) pages and features on a SharePoint web front-end server.</span></span> <span data-ttu-id="7f621-111">UI 기능에는 [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)], SharePoint 중앙 관리의 관리 페이지, SharePoint 문서 라이브러리 내에 사용되는 기능 페이지 및 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 데이터 경고 페이지가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="7f621-111">The UI features include [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)], administration pages in SharePoint Central Administration, feature pages used within SharePoint document libraries, and [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Data Alerting pages.</span></span>|  
|<span data-ttu-id="7f621-112">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint 모드로 설치 된 보고서 서버</span><span class="sxs-lookup"><span data-stu-id="7f621-112">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] report server installed in SharePoint Mode</span></span>|<span data-ttu-id="7f621-113">보고서 서버는 데이터 및 보고서 처리와 렌더링은 물론 등록 및 데이터 경고 처리를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="7f621-113">The report server handles the data and report processing and rendering as well subscription and Data Alert processing.</span></span> <span data-ttu-id="7f621-114">SharePoint 모드 보고서 서버는 SharePoint 공유 서비스로 설계되고 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="7f621-114">The SharePoint mode report server is architected and installed as a SharePoint Shared Service.</span></span>|  
  
 <span data-ttu-id="7f621-115">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]를 설치하려면 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 설치 미디어를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="7f621-115">To install [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], use the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] installation media.</span></span>  
  
 <span data-ttu-id="7f621-116">고급 배포 시나리오에 대 한 지침은 [배포 검사 목록: Reporting Services, 파워 뷰 및 SharePoint용 PowerPivot](../../sql-server/install/deployment-checklist-reporting-services-power-view-power-pivot-for-sharepoint.md) 및 [배포 검사 목록: 기존 SharePoint 팜에 Reporting Services 설치](../../sql-server/install/deployment-checklist-install-reporting-services-existing-sharepoint-farm.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="7f621-116">For instructions on advanced deployment scenarios, see [Deployment Checklist: Reporting Services, Power View, and PowerPivot for SharePoint](../../sql-server/install/deployment-checklist-reporting-services-power-view-power-pivot-for-sharepoint.md) and [Deployment Checklist: Install Reporting Services into an Existing SharePoint Farm](../../sql-server/install/deployment-checklist-install-reporting-services-existing-sharepoint-farm.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7f621-117">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="7f621-117">In This Section</span></span>  
 [<span data-ttu-id="7f621-118">지원 되는 SharePoint 및 Reporting Services 서버 조합 및 추가 기능 &#40;SQL Server 2014&#41;</span><span class="sxs-lookup"><span data-stu-id="7f621-118">Supported Combinations of SharePoint and Reporting Services Server and Add-in &#40;SQL Server 2014&#41;</span></span>](supported-combinations-of-sharepoint-and-reporting-services-server.md)  
  
 [<span data-ttu-id="7f621-119">Install Reporting Services SharePoint Mode for SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="7f621-119">Install Reporting Services SharePoint Mode for SharePoint 2013</span></span>](../../sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2013.md)  
  
 [<span data-ttu-id="7f621-120">SharePoint 2010에 대 한 Reporting Services SharePoint 모드 설치</span><span class="sxs-lookup"><span data-stu-id="7f621-120">Install Reporting Services SharePoint Mode for SharePoint 2010</span></span>](../../sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md)  
  
 [<span data-ttu-id="7f621-121">Sharepoint 2010 및 SharePoint 2013 &#40;Reporting Services 추가 기능을 설치 하거나 제거&#41;</span><span class="sxs-lookup"><span data-stu-id="7f621-121">Install or Uninstall the Reporting Services Add-in for SharePoint &#40;SharePoint 2010 and SharePoint 2013&#41;</span></span>](install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)  
  
 [<span data-ttu-id="7f621-122">SharePoint 제품용 Reporting Services 추가 기능 검색 위치</span><span class="sxs-lookup"><span data-stu-id="7f621-122">Where to find the Reporting Services add-in for SharePoint Products</span></span>](where-to-find-the-reporting-services-add-in-for-sharepoint-products.md)  
  
 [<span data-ttu-id="7f621-123">팜에 추가 보고서 서버 추가&#40;SSRS 확장&#41;</span><span class="sxs-lookup"><span data-stu-id="7f621-123">Add an Additional Report Server to a Farm &#40;SSRS Scale-out&#41;</span></span>](add-an-additional-report-server-to-a-farm-ssrs-scale-out.md)  
  
 [<span data-ttu-id="7f621-124">팜에 추가 Reporting Services 웹 프런트 엔드 추가</span><span class="sxs-lookup"><span data-stu-id="7f621-124">Add an Additional Reporting Services Web Front-end to a Farm</span></span>](add-an-additional-reporting-services-web-front-end-to-a-farm.md)  
  
 [<span data-ttu-id="7f621-125">Reporting Services 서비스 애플리케이션에 대한 메일 구성&#40;SharePoint 2010 및 SharePoint 2013&#41;</span><span class="sxs-lookup"><span data-stu-id="7f621-125">Configure E-mail for a Reporting Services Service Application &#40;SharePoint 2010 and SharePoint 2013&#41;</span></span>](configure-e-mail-for-a-reporting-services-service-application.md)  
  
 [<span data-ttu-id="7f621-126">SSRS 서비스 애플리케이션에 대한 구독 및 경고 프로비전</span><span class="sxs-lookup"><span data-stu-id="7f621-126">Provision Subscriptions and Alerts for SSRS Service Applications</span></span>](provision-subscriptions-and-alerts-for-ssrs-service-applications.md)  
  
 [<span data-ttu-id="7f621-127">Windows 토큰 서비스에 대 한 클레임 &#40;C2WTS&#41; 및 Reporting Services</span><span class="sxs-lookup"><span data-stu-id="7f621-127">Claims to Windows Token Service &#40;C2WTS&#41; and Reporting Services</span></span>](../../sql-server/install/claims-to-windows-token-service-c2wts-and-reporting-services.md)  
  
## <a name="see-also"></a><span data-ttu-id="7f621-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7f621-128">See Also</span></span>  
 <span data-ttu-id="7f621-129">[데이터 경고 아키텍처 및 워크플로](../reporting-services-data-alerts.md#AlertingWF) </span><span class="sxs-lookup"><span data-stu-id="7f621-129">[Data Alerts Architecture and Workflow](../reporting-services-data-alerts.md#AlertingWF) </span></span>  
 [<span data-ttu-id="7f621-130">경고 담당자를 위한 데이터 경고 관리자</span><span class="sxs-lookup"><span data-stu-id="7f621-130">Data Alert Manager for Alerting Administrators</span></span>](../data-alert-manager-for-alerting-administrators.md)  
  
  
