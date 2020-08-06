---
title: 대화형 정렬, 문서 구조 및 링크(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: cc6ef408-4a76-408a-9d3f-033481fe21cf
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 35d88e89ed14a205153374d44562e6d3fda92e02
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739297"
---
# <a name="interactive-sort-document-maps-and-links-report-builder-and-ssrs"></a><span data-ttu-id="15658-102">대화형 정렬, 문서 구조 및 링크(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="15658-102">Interactive Sort, Document Maps, and Links (Report Builder and SSRS)</span></span>
  <span data-ttu-id="15658-103">웹 기반 환경에서 사용자가 보고서와 상호 작용할 수 있도록 해주는 다양한 기능을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15658-103">In Web-based environments, you can add a number of features that let your users interact with reports.</span></span> <span data-ttu-id="15658-104">사용자는 보고서 값의 정렬 순서를 변경할 수 있고, 보고서의 항목을 표시하거나 숨길 수 있으며, 다른 보고서나 웹 페이지로 이동하는 링크를 클릭할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15658-104">Your users can change the sort order of values in your report, show or hide items in the report, or click links that go to other reports or Web pages.</span></span> <span data-ttu-id="15658-105">또한 목차나 문서 구조를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15658-105">You can also add a table of contents or document map.</span></span> <span data-ttu-id="15658-106">보고서 사용자는 목차나 문서 구조의 항목을 클릭하여 보고서 내의 영역으로 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15658-106">Your report users can click items in the table of contents or document map to jump to areas within a report.</span></span>  
  
 <span data-ttu-id="15658-107">보고서 작성기 및 보고서 디자이너에서는 다음과 같이 서로 다른 동작을 수행하는 세 가지 유형의 링크를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="15658-107">Report Builder and Report Designer support three types of links with the following actions:</span></span>  
  
-   <span data-ttu-id="15658-108">**책갈피 링크** 보고서 내의 다른 영역으로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="15658-108">**Bookmark links** Jump to other areas within the report.</span></span>  
  
-   <span data-ttu-id="15658-109">**하이퍼링크** URL 액세스를 사용하여 보고서 서버에서 웹 페이지 또는 보고서의 주소를 지정하는 URL로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="15658-109">**Hyperlinks** Jump to URLs that specify the address of Web pages or reports on a report server by using URL access.</span></span>  
  
-   <span data-ttu-id="15658-110">**드릴스루 보고서 링크** 동일한 보고서 서버의 다른 보고서로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="15658-110">**Drillthrough report links** Jump to other reports on the same report server.</span></span> <span data-ttu-id="15658-111">자세한 내용은 [드릴스루 보고서&#40;보고서 작성기 및 SSRS&#41;](drillthrough-reports-report-builder-and-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="15658-111">For more information, see [Drillthrough Reports &#40;Report Builder and SSRS&#41;](drillthrough-reports-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="15658-112">데이터 세트 필드에 바인딩된 링크는 악의적 의도를 가진 사용자가 임의로 변경할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15658-112">Links that are bound to dataset fields can be vulnerable to tampering for malicious purposes.</span></span> <span data-ttu-id="15658-113">자세한 내용은 msdn.microsoft.com의 [온라인 설명서](../security/secure-reports-and-resources.md) 에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][보고서 및 리소스 보안](https://go.microsoft.com/fwlink/?LinkId=154888) 을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="15658-113">For more information, see [Secure Reports and Resources](../security/secure-reports-and-resources.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][Books Online](https://go.microsoft.com/fwlink/?LinkId=154888) on msdn.microsoft.com.</span></span>  
  
 <span data-ttu-id="15658-114">정렬, 필터 및 표시 유형에 대한 매개 변수 참조를 포함하는 식을 디자인하면 사용자가 보고서 표시 및 콘텐츠를 제어하는 것이 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="15658-114">You can also let your users control report display and content by designing expressions that include parameter references for sort, filter, and visibility.</span></span> <span data-ttu-id="15658-115">자세한 내용은 [보고서 매개 변수&#40;보고서 작성기 및 보고서 디자이너&#41;](report-parameters-report-builder-and-report-designer.md), [데이터 필터링, 그룹화 및 정렬&#40;보고서 작성기 및 SSRS&#41;](filter-group-and-sort-data-report-builder-and-ssrs.md) 및 [데이터 세트 필터, 데이터 영역 필터 및 그룹 필터 추가&#40;보고서 작성기 및 SSRS&#41;](add-dataset-filters-data-region-filters-and-group-filters.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="15658-115">For more information, see [Report Parameters &#40;Report Builder and Report Designer&#41;](report-parameters-report-builder-and-report-designer.md), [Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;](filter-group-and-sort-data-report-builder-and-ssrs.md), and [Add Dataset Filters, Data Region Filters, and Group Filters &#40;Report Builder and SSRS&#41;](add-dataset-filters-data-region-filters-and-group-filters.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="in-this-section"></a><span data-ttu-id="15658-116">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="15658-116">In This Section</span></span>  
 [<span data-ttu-id="15658-117">대화형 정렬&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="15658-117">Interactive Sort &#40;Report Builder and SSRS&#41;</span></span>](interactive-sort-report-builder-and-ssrs.md)  
 <span data-ttu-id="15658-118">열 머리글에 대화형 정렬 단추를 추가하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="15658-118">Explains how to add interactive sort buttons to column headers.</span></span>  
  
 [<span data-ttu-id="15658-119">문서 구조 만들기&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="15658-119">Create a Document Map &#40;Report Builder and SSRS&#41;</span></span>](create-a-document-map-report-builder-and-ssrs.md)  
 <span data-ttu-id="15658-120">목차를 추가하여 큰 보고서에서 탐색을 지원하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="15658-120">Explains how to add a table of contents to support navigation in a large report.</span></span>  
  
 [<span data-ttu-id="15658-121">보고서에 책갈피 추가&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="15658-121">Add a Bookmark to a Report &#40;Report Builder and SSRS&#41;</span></span>](add-a-bookmark-to-a-report-report-builder-and-ssrs.md)  
 <span data-ttu-id="15658-122">책갈피를 추가하여 보고서 내에 링크를 만드는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="15658-122">Explains how to add bookmarks to create links within a report.</span></span>  
  
 [<span data-ttu-id="15658-123">URL에 하이퍼링크 추가&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="15658-123">Add a Hyperlink to a URL &#40;Report Builder and SSRS&#41;</span></span>](add-a-hyperlink-to-a-url-report-builder-and-ssrs.md)  
 <span data-ttu-id="15658-124">보고서의 링크를 URL에 추가하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="15658-124">Explains how to add a link from your report to a URL</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15658-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="15658-125">See Also</span></span>  
 [<span data-ttu-id="15658-126">드릴스루, 드릴다운, 하위 보고서 및 중첩 데이터 영역&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="15658-126">Drillthrough, Drilldown, Subreports, and Nested Data Regions &#40;Report Builder and SSRS&#41;</span></span>](drillthrough-drilldown-subreports-and-nested-data-regions.md)  
  
  
