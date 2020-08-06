---
title: 보기 페이지, 보고서 (보고서 관리자) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 4874ba29-429b-4dd4-a8cb-d4f087237dc2
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 4eb5733bf6ddfc8d7ba5a1d3d6f5ebe18ce85c66
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737780"
---
# <a name="view-page-reports-report-manager"></a><span data-ttu-id="c055c-102">보기 페이지, 보고서(보고서 관리자)</span><span class="sxs-lookup"><span data-stu-id="c055c-102">View Page, Reports (Report Manager)</span></span>
  <span data-ttu-id="c055c-103">보고서의 보기 페이지를 사용하여 보고서를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c055c-103">Use the View page for reports to view a report.</span></span> <span data-ttu-id="c055c-104">보고서 관리자에서 보고서를 처음 열면 HTML 형식으로 열립니다.</span><span class="sxs-lookup"><span data-stu-id="c055c-104">When you first open a report in Report Manager, it is formatted in HTML.</span></span> <span data-ttu-id="c055c-105">HTML 보고서의 맨 위에는 보고서 도구 모음이 포함되어 있어서 보고서 페이지를 탐색하고 보고서 내에서 검색하거나 보고서를 다른 형식으로 내보내는 작업이 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="c055c-105">HTML reports include a report toolbar that appears at the top of the report so that you can navigate through report pages, search within a report, or export the report to a different format.</span></span> <span data-ttu-id="c055c-106">다음 다이어그램에서는 보고서 도구 모음을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c055c-106">The following diagram shows the report toolbar.</span></span>  
  
 <span data-ttu-id="c055c-107">![보고서 도구 모음](media/htmlviewer-toolbar.gif "보고서 도구 모음")</span><span class="sxs-lookup"><span data-stu-id="c055c-107">![Report toolbar](media/htmlviewer-toolbar.gif "Report toolbar")</span></span>  
<span data-ttu-id="c055c-108">보고서 도구 모음</span><span class="sxs-lookup"><span data-stu-id="c055c-108">Report toolbar</span></span>  
  
 <span data-ttu-id="c055c-109">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]에서는 요청 시 실행되거나 보고서 실행 스냅샷에서 실행되도록 보고서를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c055c-109">In [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], reports can be configured to run on demand or from a report execution snapshot.</span></span> <span data-ttu-id="c055c-110">보고서가 요청 시 실행되는 경우 보고서를 열 때마다 모든 데이터 및 보고서가 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="c055c-110">If a report is run on demand, all data processing and report processing occur each time you open the report.</span></span> <span data-ttu-id="c055c-111">보고서 실행 스냅샷으로 실행되도록 구성된 보고서를 보는 경우 스냅샷을 만들 때 데이터가 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="c055c-111">If you view a report that is configured to run as a report execution snapshot, data processing occurred when the snapshot was created.</span></span>  
  
## <a name="exporting-reports"></a><span data-ttu-id="c055c-112">보고서 내보내기</span><span class="sxs-lookup"><span data-stu-id="c055c-112">Exporting Reports</span></span>  
 <span data-ttu-id="c055c-113">일부 보고서 기능은 일부 내보내기 형식에서 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c055c-113">Not all report features are available in all of the export formats.</span></span> <span data-ttu-id="c055c-114">HTML 보고서를 다른 형식으로 내보내는 경우 보고서 표시 방법이 서로 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c055c-114">If you export an HTML report to another format, you can expect to see some differences in how the report appears.</span></span> <span data-ttu-id="c055c-115">또한 보고서에 하이퍼링크, 책갈피 또는 문서 구조 등의 대화형 기능이 있는 경우 새 형식에서는 이러한 기능을 사용할 수 없거나 동작 방식이 다를 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c055c-115">Also, if the report includes interactive features (such as hyperlinks, bookmarks, or document maps) those features might not be available or work the same way in the new format.</span></span>  
  
## <a name="generating-data-feeds-from-report-data"></a><span data-ttu-id="c055c-116">보고서 데이터에서 데이터 피드 생성</span><span class="sxs-lookup"><span data-stu-id="c055c-116">Generating Data Feeds from Report Data</span></span>  
 <span data-ttu-id="c055c-117">보고서에서 데이터 피드를 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c055c-117">You can generate data feeds from reports.</span></span> <span data-ttu-id="c055c-118">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Atom 렌더링 확장 프로그램에서는 보고서가 제공하는 데이터 피드를 나열하는 Atom 서비스 문서와 보고서 데이터를 포함하는 데이터 피드의 두 가지 Atom 호환 문서를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="c055c-118">The [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Atom rendering extension generates two Atom-compliant documents: an Atom service document that lists the data feeds the report provides and the data feeds that contains the report data.</span></span> <span data-ttu-id="c055c-119">데이터 피드는 Atom 호환 데이터 피드를 사용하는 애플리케이션에서 읽고 교환할 수 있는 표준화된 Atom 1.0 호환 형식으로 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 에서 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="c055c-119">The data feeds are generated by [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] in a standardized Atom 1.0 compliant format that it readable and exchangeable with applications that consume Atom compliant data feeds.</span></span> <span data-ttu-id="c055c-120">예를 들어 [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] 클라이언트는 보고서에서 생성된 데이터 피드를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c055c-120">For example the [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] client can consume data feeds that are generated from reports.</span></span>  
  
## <a name="running-parameterized-reports"></a><span data-ttu-id="c055c-121">매개 변수 있는 보고서 실행</span><span class="sxs-lookup"><span data-stu-id="c055c-121">Running Parameterized Reports</span></span>  
 <span data-ttu-id="c055c-122">입력 필드 및 **보고서 보기** 단추를 포함하는 보고서를 매개 변수가 있는 보고서라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="c055c-122">A report that contains input fields and a **View Report** button is a parameterized report.</span></span> <span data-ttu-id="c055c-123">매개 변수가 있는 보고서를 보려면 보고서 실행에 사용되는 값을 제공해야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c055c-123">To view a parameterized report, you may need to provide values that are used to run the report.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c055c-124">보고서 실행 스냅샷 및 일부 내보내기 형식은 일부 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]에서 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c055c-124">Report execution snapshots and some export formats are not available in all editions of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="c055c-125">자세한 내용은 [Features Supported by the Editions of SQL Server 2014](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c055c-125">For more information, see [Features Supported by the Editions of SQL Server 2014](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c055c-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c055c-126">See Also</span></span>  
 <span data-ttu-id="c055c-127">[보고서 관리자&#40;SSRS 기본 모드&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="c055c-127">[Report Manager  &#40;SSRS Native Mode&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span></span>  
 [<span data-ttu-id="c055c-128">보고서 관리자 F1 도움말</span><span class="sxs-lookup"><span data-stu-id="c055c-128">Report Manager F1 Help</span></span>](../../2014/reporting-services/report-manager-f1-help.md)  
  
  
