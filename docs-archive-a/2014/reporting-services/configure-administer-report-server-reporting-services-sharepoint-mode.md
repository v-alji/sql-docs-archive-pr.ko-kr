---
title: 보고서 서버 구성 및 관리 (Reporting Services SharePoint 모드) | Microsoft Docs
ms.custom: ''
ms.date: 11/25/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 846e86d0-fbbb-426c-97f9-f179cd42b390
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ce7c1f524eec4785ddbc25d95c641d070ecbf408
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739561"
---
# <a name="configuration-and-administration-of-a-report-server-reporting-services-sharepoint-mode"></a><span data-ttu-id="a3328-102">보고서 서버의 구성 및 관리(Reporting Services SharePoint 모드)</span><span class="sxs-lookup"><span data-stu-id="a3328-102">Configuration and Administration of a Report Server (Reporting Services SharePoint Mode)</span></span>
  [!INCLUDE[msCoName](../includes/msconame-md.md)]<span data-ttu-id="a3328-103">[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 는 조직에 대 한 보고서를 만들고 배포 하 고 관리 하는 데 도움이 되는 즉시 사용 가능한 모든 도구와 서비스 뿐만 아니라 보고 기능을 확장 하 고 사용자 지정할 수 있는 프로그래밍 기능을 제공 하는 서버 기반 보고 플랫폼입니다.</span><span class="sxs-lookup"><span data-stu-id="a3328-103">[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] is a server-based reporting platform that provides a full range of ready-to-use tools and services to help you create, deploy, and manage reports for your organization, as well as programming features that enable you to extend and customize your reporting functionality.</span></span> <span data-ttu-id="a3328-104">보고 환경을 SharePoint 제품과 통합하면 SharePoint 사이트에서 제공하는 공동 작업 환경을 사용하는 이점을 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a3328-104">You can integrate your reporting environment with a SharePoint product to experience the benefits of using the collaborative environment provided by SharePoint sites.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a3328-105">단원 내용</span><span class="sxs-lookup"><span data-stu-id="a3328-105">In this section</span></span>  
 <span data-ttu-id="a3328-106">다음 섹션을 통해 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 환경과 SharePoint 제품 또는 기술의 통합에 대한 개념, 배포 시나리오, 절차 등을 더 잘 이해할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a3328-106">Use the following sections to help you understand concepts, deployment scenarios, procedures, and more for integrating your [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] environment with a SharePoint product or technology:</span></span>  
  
-   <span data-ttu-id="a3328-107">SharePoint 문서 라이브러리의 메뉴 옵션</span><span class="sxs-lookup"><span data-stu-id="a3328-107">Menu options in a SharePoint document library</span></span>  
  
    -   [<span data-ttu-id="a3328-108">SharePoint 사용자용 데이터 경고 관리자</span><span class="sxs-lookup"><span data-stu-id="a3328-108">Data Alert Manager for SharePoint Users</span></span>](../../2014/reporting-services/data-alert-manager-for-sharepoint-users.md)  
  
    -   [<span data-ttu-id="a3328-109">SharePoint 모드 보고서 서버 구독 만들기 및 관리</span><span class="sxs-lookup"><span data-stu-id="a3328-109">Create and Manage Subscriptions for SharePoint Mode Report Servers</span></span>](subscriptions/create-and-manage-subscriptions-for-sharepoint-mode-report-servers.md)  
  
    -   [<span data-ttu-id="a3328-110">SharePoint 사이트의 보고서 데이터 원본에서 자격 증명 업데이트</span><span class="sxs-lookup"><span data-stu-id="a3328-110">Update Credentials in Report Data Sources from a SharePoint Site</span></span>](report-data/update-credentials-in-report-data-sources-from-a-sharepoint-site.md)  
  
    -   [<span data-ttu-id="a3328-111">공유 데이터 세트 관리</span><span class="sxs-lookup"><span data-stu-id="a3328-111">Manage Shared Datasets</span></span>](report-data/manage-shared-datasets.md)  
  
    -   [<span data-ttu-id="a3328-112">게시된 보고서에 매개 변수 설정&#40;SharePoint 통합 모드의 Reporting Services&#41;</span><span class="sxs-lookup"><span data-stu-id="a3328-112">Set Parameters on a Published Report &#40;Reporting Services in SharePoint Integrated Mode&#41;</span></span>](report-design/set-parameters-on-a-published-report-sharepoint-integrated-mode.md)  
  
    -   [<span data-ttu-id="a3328-113">처리 옵션 설정&#40;SharePoint 통합 모드의 Reporting Services&#41;</span><span class="sxs-lookup"><span data-stu-id="a3328-113">Set Processing Options &#40;Reporting Services in SharePoint Integrated Mode&#41;</span></span>](../../2014/reporting-services/set-processing-options-reporting-services-in-sharepoint-integrated-mode.md)  
  
    -   [<span data-ttu-id="a3328-114">캐시 새로 고침 옵션&#40;보고서 관리자&#41;</span><span class="sxs-lookup"><span data-stu-id="a3328-114">Cache Refresh Options &#40;Report Manager&#41;</span></span>](../../2014/reporting-services/cache-refresh-options-report-manager.md)  
  
-   [<span data-ttu-id="a3328-115">Reporting Services 사이트 모음 기능</span><span class="sxs-lookup"><span data-stu-id="a3328-115">Reporting Services Site Collection Features</span></span>](../../2014/reporting-services/reporting-services-site-collection-features.md)  
  
-   [<span data-ttu-id="a3328-116">SharePoint에서 보고서 서버 및 파워 뷰 통합 사이트 모음 기능 활성화</span><span class="sxs-lookup"><span data-stu-id="a3328-116">Activate the Report Server and Power View Integration Features in SharePoint</span></span>](activate-the-report-server-and-power-view-integration-features-in-sharepoint.md)  
  
-   [<span data-ttu-id="a3328-117">Reporting Services 사이트 설정 및 사이트 기능&#40;SharePoint 모드&#41;</span><span class="sxs-lookup"><span data-stu-id="a3328-117">Reporting Services Site Settings and Site Features&#40;SharePoint Mode&#41;</span></span>](../../2014/reporting-services/reporting-services-site-settings-and-site-features-sharepoint-mode.md)  
  
-   [<span data-ttu-id="a3328-118">SharePoint 중앙 관리에서 보고서 서버 파일 동기화 기능 활성화</span><span class="sxs-lookup"><span data-stu-id="a3328-118">Activate the Report Server File Sync Feature in SharePoint Central Administration</span></span>](../../2014/reporting-services/activate-report-server-file-sync-feature-sharepoint-central-administration.md)  
  
-   [<span data-ttu-id="a3328-119">SharePoint 통합 모드에서 라이브러리 &#40;Reporting Services에 보고서 서버 콘텐츠 형식 추가&#41;</span><span class="sxs-lookup"><span data-stu-id="a3328-119">Add Report Server Content Types to a Library &#40;Reporting Services in SharePoint Integrated Mode&#41;</span></span>](../../2014/reporting-services/add-reporting-services-content-types-to-a-sharepoint-library.md)  
  
-   [<span data-ttu-id="a3328-120">보고서 뷰어의 로컬 모드와 보고서 뷰어의 연결 모드 보고서&#40;SharePoint 모드의 Reporting Services&#41;</span><span class="sxs-lookup"><span data-stu-id="a3328-120">Local Mode vs. Connected Mode Reports in the Report Viewer &#40;Reporting Services in SharePoint Mode&#41;</span></span>](../../2014/reporting-services/local-vs-connected-mode-report-viewer-reporting-services-sharepoint-mode.md)  
  
-   [<span data-ttu-id="a3328-121">SharePoint 라이브러리에 문서 업로드&#40;SharePoint 모드의 Reporting Services&#41;</span><span class="sxs-lookup"><span data-stu-id="a3328-121">Upload Documents to a SharePoint Library &#40;Reporting Services in SharePoint Mode&#41;</span></span>](../../2014/reporting-services/upload-documents-to-a-sharepoint-library-reporting-services-in-sharepoint-mode.md)  
  
-   [<span data-ttu-id="a3328-122">처리 옵션 설정&#40;SharePoint 통합 모드의 Reporting Services&#41;</span><span class="sxs-lookup"><span data-stu-id="a3328-122">Set Processing Options &#40;Reporting Services in SharePoint Integrated Mode&#41;</span></span>](../../2014/reporting-services/set-processing-options-reporting-services-in-sharepoint-integrated-mode.md)  
  
 <span data-ttu-id="a3328-123">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]에 대한 일반적인 정보는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 온라인 설명서의 [Reporting Services&#40;SSRS&#41;](create-deploy-and-manage-mobile-and-paginated-reports.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a3328-123">For more general information about [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], see [Reporting Services &#40;SSRS&#41;](create-deploy-and-manage-mobile-and-paginated-reports.md) in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Books Online.</span></span> <span data-ttu-id="a3328-124">다른 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 구성 요소, 도구 및 리소스에 대한 자세한 내용은 [SQL Server 온라인 설명서](../index.yml)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="a3328-124">For information about other [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] components, tools, and resources, see [SQL Server Books Online](../index.yml).</span></span>  
  
  
