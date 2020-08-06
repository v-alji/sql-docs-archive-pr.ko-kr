---
title: 보고서 서버에 보고서 게시 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- production environments [Reporting Services]
- report projects [Reporting Services]
- Debug configuration [Reporting Services]
- report publishing [Reporting Services]
- publishing reports [Reporting Services]
- report properties [Reporting Services]
- Report Designer [Reporting Services], deploying reports
- Production configuration [Reporting Services]
- publishing reports [Reporting Services], production environments
- DebugLocal configuration [Reporting Services]
- deploying [Reporting Services], reports
- Report Designer [Reporting Services], publishing reports
ms.assetid: bd7aa5e0-61ce-43fd-8f74-5d1aeed078bb
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 644db7cc0d6647c160836596e6c87d524a94a4aa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649377"
---
# <a name="publishing-reports-to-a-report-server"></a><span data-ttu-id="3d676-102">보고서 서버에 보고서 게시</span><span class="sxs-lookup"><span data-stu-id="3d676-102">Publishing Reports to a Report Server</span></span>
  <span data-ttu-id="3d676-103">보고서 또는 보고서 집합을 디자인 및 테스트한 후 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]의 기본 제공 배포 기능을 사용하여 보고서를 보고서 서버에 게시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d676-103">After you have designed and tested a report or set of reports, you can use the built-in deployment features in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] to publish the reports to a report server.</span></span> <span data-ttu-id="3d676-104">개별 보고서 또는 보고서 서버 프로젝트를 게시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d676-104">You can publish individual reports or a Report Server project.</span></span> <span data-ttu-id="3d676-105">보고서 서버 프로젝트를 게시하는 것은 여러 보고서를 게시하는 가장 쉬운 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="3d676-105">Publishing a Report Server project is the easiest way to publish multiple reports.</span></span> [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]<span data-ttu-id="3d676-106">는 *게시*라는 용어 대신에 *배포*라는 용어를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="3d676-106">uses the term *deploy*, instead ofthe term *publish*.</span></span> <span data-ttu-id="3d676-107">두 용어는 같은 의미로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d676-107">The two terms are interchangeable.</span></span>  
  
 <span data-ttu-id="3d676-108">보고서를 게시하려면 보고서를 게시할 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3d676-108">Before you can publish a report, you must have permission to do so.</span></span> <span data-ttu-id="3d676-109">사용 권한은 보고서 서버 관리자가 정의하는 역할 기반 보안을 통해 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="3d676-109">Permission is determined through role-based security that is defined by your report server administrator.</span></span> <span data-ttu-id="3d676-110">게시 작업은 일반적으로 게시자 역할을 통해 허가됩니다.</span><span class="sxs-lookup"><span data-stu-id="3d676-110">Publishing operations are typically granted through the Publisher role.</span></span>  
  
 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] <span data-ttu-id="3d676-111">는 보고서 게시 관리를 위한 프로젝트 구성을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="3d676-111">provides project configurations for managing report publication.</span></span> <span data-ttu-id="3d676-112">이 구성은 보고서 서버의 위치, 보고서 서버에 설치된 SQL Server Reporting Services의 버전, 보고서 서버에 게시된 데이터 원본을 덮어쓰는지 여부 등을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3d676-112">The configuration specifies the location of the report server, the version of SQL Server Reporting Services installed on the report server, whether the data sources published to the report server are overwritten and so forth.</span></span> <span data-ttu-id="3d676-113">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 에서 제공하는 구성을 사용하는 것 외에도 추가 구성을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d676-113">In addition to using the configurations that [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] provides, you can create additional configurations.</span></span>  
  
## <a name="project-configurations"></a><span data-ttu-id="3d676-114">프로젝트 구성</span><span class="sxs-lookup"><span data-stu-id="3d676-114">Project Configurations</span></span>  
 <span data-ttu-id="3d676-115">유효한 보고서 정의만 보고서 서버에 게시되도록 하기 위해 보고서는 게시되기 전에 빌드됩니다.</span><span class="sxs-lookup"><span data-stu-id="3d676-115">Reports are built before they are published to ensure that only valid report definitions are published to the report server.</span></span> <span data-ttu-id="3d676-116">프로젝트 구성에는 빌드된 보고서를 임시로 저장하는 폴더, 빌드 문제를 처리하는 방법 등과 같은 보고서 빌드를 위한 속성이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="3d676-116">Project configurations include properties for building reports, such as the folder in which to temporarily store the built reports, and how to handle build issues.</span></span> <span data-ttu-id="3d676-117">또한 보고서 서버의 위치 및 버전과 보고서 서버의 폴더를 지정하는 데 사용되는 속성도 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="3d676-117">The configurations also have properties that you use to specify the location and version of the report server, the folders on the report server.</span></span>  
  
 <span data-ttu-id="3d676-118">기본적으로 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 은 DebugLocal, Debug 및 Release라는 세 가지 프로젝트 구성을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="3d676-118">By default, [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] provides three project configurations: DebugLocal, Debug, and Release.</span></span> <span data-ttu-id="3d676-119">기본 구성은 DebugLocal입니다.</span><span class="sxs-lookup"><span data-stu-id="3d676-119">The default configuration is DebugLocal.</span></span> <span data-ttu-id="3d676-120">일반적으로 DebugLocal 구성을 사용하면 로컬 미리 보기 창으로 보고서를 볼 수 있고 Debug 구성을 사용하면 테스트 서버에 보고서를 게시할 수 있으며 Release 구성을 사용하면 프로덕션 서버에 보고서를 게시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d676-120">You typically use the DebugLocal configuration to view reports in a local preview window, the Debug configuration to publish reports to a test server, and the Release configuration to publish reports to a production server.</span></span> <span data-ttu-id="3d676-121">표준 도구 모음의 솔루션 구성 드롭다운 목록에는 활성 구성이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3d676-121">The solution configurations drop-down list on the Standard toolbar shows the active configuration.</span></span> <span data-ttu-id="3d676-122">다른 구성을 사용하려면 목록에서 해당 구성을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3d676-122">To use a different configuration, select it from the list.</span></span>  
  
 <span data-ttu-id="3d676-123">보고 환경에는 여러 보고서 서버와 다른 버전의 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 가 설치되었을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d676-123">Your reporting environment might have multiple report servers and different versions of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installed.</span></span> <span data-ttu-id="3d676-124">여러 구성을 만든 다음 배포 시나리오에 따라 다른 구성을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d676-124">You can create multiple configurations and then use a different one depending the deployment scenario.</span></span> <span data-ttu-id="3d676-125">자세한 내용은 [SQL Server Data Tools의 배포 및 버전 지원 &#40;SSRS&#41;](../tools/deployment-and-version-support-in-sql-server-data-tools-ssrs.md) 및 [배포 속성 설정 &#40;Reporting Services&#41;](../tools/set-deployment-properties-reporting-services.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="3d676-125">For more information, see [Deployment and Version Support in SQL Server Data Tools &#40;SSRS&#41;](../tools/deployment-and-version-support-in-sql-server-data-tools-ssrs.md) and [Set Deployment Properties &#40;Reporting Services&#41;](../tools/set-deployment-properties-reporting-services.md).</span></span>  
  
## <a name="publishing-reports"></a><span data-ttu-id="3d676-126">보고서 게시</span><span class="sxs-lookup"><span data-stu-id="3d676-126">Publishing Reports</span></span>  
 <span data-ttu-id="3d676-127">단일 보고서를 게시하거나 여러 보고서를 포함하는 보고서 서버 프로젝트를 게시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d676-127">You can publish a single report or a Report Server project that contains multiple reports.</span></span> <span data-ttu-id="3d676-128">보고서 게시에 대 한 지침은 [보고서 게시](../publish-reports.md)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="3d676-128">For instructions about publishing reports, see [Publish Reports](../publish-reports.md).</span></span>  
  
### <a name="publishing-a-single-report"></a><span data-ttu-id="3d676-129">단일 보고서 게시</span><span class="sxs-lookup"><span data-stu-id="3d676-129">Publishing a Single Report</span></span>  
 <span data-ttu-id="3d676-130">프로젝트의 보고서를 일부만 게시하려면 단일 보고서만 게시하도록 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d676-130">If you do not want to publish all reports in a project, you can chose to publish only a single report.</span></span> <span data-ttu-id="3d676-131">이렇게 하려면 보고서를 배포하는 구성(예: Release 구성)을 선택하고 마우스 오른쪽 단추로 해당 보고서를 클릭한 다음 **배포**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3d676-131">To do this, select a configuration that deploys the report (for example, the Release configuration), right-click the report, and then click **Deploy**.</span></span>  
  
 <span data-ttu-id="3d676-132">보고서에 공유 데이터 원본을 사용하는 경우 공유 데이터 원본도 배포해야 하며 그렇지 않으면 배포된 보고서가 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3d676-132">If a report uses a shared data source, you need to also deploy the shared data source or the deployed report will not run.</span></span> <span data-ttu-id="3d676-133">공유 데이터 원본을 마우스 오른쪽 단추로 클릭한 다음 **배포**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3d676-133">Right-click the shared data source and then click **Deploy**.</span></span>  
  
 <span data-ttu-id="3d676-134">보고서 서버의 대상 서버 URL을 지정해야 하며 보고서 및 공유 데이터 원본이 배포되는 기본 폴더를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d676-134">The target server URL of the report server must be specified and you might want to change the default folders to which reports and shared data sources deploy.</span></span>  
  
### <a name="publishing-multiple-reports"></a><span data-ttu-id="3d676-135">여러 보고서 게시</span><span class="sxs-lookup"><span data-stu-id="3d676-135">Publishing Multiple Reports</span></span>  
 <span data-ttu-id="3d676-136">보고서 서버 프로젝트를 게시하면 해당 프로젝트의 모든 보고서가 게시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3d676-136">When you publish a Report Server project, you publish all reports in that project.</span></span> <span data-ttu-id="3d676-137">모든 보고서는 동일한 프로젝트 구성을 사용하여 동일한 보고서 서버, 서버의 동일한 폴더 등에 배포됩니다.</span><span class="sxs-lookup"><span data-stu-id="3d676-137">All reports are deployed using the same project configuration: to the same report server, the same folder on the server, and so on.</span></span> <span data-ttu-id="3d676-138">보고서를 다른 서버에 게시하려면 하나씩 게시하거나 보고서 서버 프로젝트에 원하는 보고서만 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="3d676-138">To publish reports to different servers, either publish them one by one or include only reports you want to in the Report Server project.</span></span> <span data-ttu-id="3d676-139">솔루션은 여러 보고서 서버 프로젝트를 포함할 수 있으며 여러 프로젝트를 사용하면 다른 구성을 사용하여 다른 프로젝트를 배포할 수 있으므로 보고서 배포를 더 쉽게 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d676-139">A solution can include multiple Report Server projects, and using multiple project might make it easier to manage the deployment of reports because you can use a different configuration to deploy different projects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d676-140">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3d676-140">See Also</span></span>  
 <span data-ttu-id="3d676-141">[프로젝트 속성 페이지 대화 상자](../tools/project-property-pages-dialog-box.md) </span><span class="sxs-lookup"><span data-stu-id="3d676-141">[Project Property Pages Dialog Box](../tools/project-property-pages-dialog-box.md) </span></span>  
 <span data-ttu-id="3d676-142">[보고서 서버 콘텐츠 관리&#40;SSRS 기본 모드&#41;](../report-server/report-server-content-management-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="3d676-142">[Report Server Content Management &#40;SSRS Native Mode&#41;](../report-server/report-server-content-management-ssrs-native-mode.md) </span></span>  
 [<span data-ttu-id="3d676-143">보고서 업그레이드</span><span class="sxs-lookup"><span data-stu-id="3d676-143">Upgrade Reports</span></span>](../install-windows/upgrade-reports.md)  
  
  
