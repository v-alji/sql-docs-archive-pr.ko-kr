---
title: 드릴다운 작업(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10249"
- "10186"
- sql12.rtp.rptdesigner.calculatedseriesproperties.visibility.f1
- sql12.rtp.rptdesigner.seriesproperties.visibility.f1
- sql12.rtp.rptdesigner.chartareaproperties.visibility.f1
- "10092"
- sql12.rtp.rptdesigner.textboxproperties.visibility.f1
- sql12.rtp.rptdesigner.charttitleproperties.visibility.f1
- "10167"
- sql12.rtp.rptdesigner.rectangleproperties.visibility.f1
- "10174"
- sql12.rtp.rptdesigner.majorgridlineproperties.visibility.f1
- "10155"
- "10123"
- sql12.rtp.rptdesigner.subreportproperties.visibility.f1
- "10425"
- sql12.rtp.rptdesigner.minorgridlineproperties.visibility.f1
- "10217"
- sql12.rtp.rptdesigner.axisproperties.visibility.f1
- sql12.rtp.rptdesigner.serieslabelproperties.visibility.f1
- "10161"
- sql12.rtp.rptdesigner.chartproperties.visibility.f1
- sql12.rtp.rptdesigner.legendproperties.visibility.f1
- sql12.rtp.rptdesigner.pictureproperties.visibility.f1
- "10215"
- "10258"
- "10144"
- "10062"
- "10053"
ms.assetid: 1f8d1ef2-0daf-40c6-9ba7-3b391249bcd4
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2fe3d55dc70a606df759c049b7b147820f0e3110
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659823"
---
# <a name="drilldown-action-report-builder-and-ssrs"></a><span data-ttu-id="1e463-102">드릴다운 동작(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="1e463-102">Drilldown Action (Report Builder and SSRS)</span></span>
  <span data-ttu-id="1e463-103">입력란에 더하기 또는 빼기 아이콘을 제공하면 사용자가 항목을 대화식으로 숨기거나 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e463-103">B providing plus and minus icons on a text box, you can enable users to hide and display items interactively.</span></span> <span data-ttu-id="1e463-104">이를 *드릴다운* 동작이라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e463-104">This is called a *drilldown* action.</span></span> <span data-ttu-id="1e463-105">테이블 또는 행렬에 대해서는 정적 행과 열 또는 그룹과 연결된 행과 열을 표시하거나 숨길 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e463-105">For a table or matrix, you can show or hide static rows and columns, or rows and columns that are associated with groups.</span></span>  
  
 <span data-ttu-id="1e463-106">![rs_drilldown](../media/rs-drilldown.gif "rs_drilldown")</span><span class="sxs-lookup"><span data-stu-id="1e463-106">![rs_drilldown](../media/rs-drilldown.gif "rs_drilldown")</span></span>  
  
 <span data-ttu-id="1e463-107">이 그림에서 사용자는 보고서에서 더하기 기호(+)를 클릭하여 세부 데이터를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="1e463-107">In this illustration, the user clicks the plus signs (+) in the report to show detail data.</span></span>  
  
 <span data-ttu-id="1e463-108">예를 들어 처음에는 행 그룹이 있는 테이블의 외부 그룹 요약 행을 제외한 모든 행을 숨길 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e463-108">For example, you can initially hide all the rows except the outer group summary row for a table with row groups.</span></span> <span data-ttu-id="1e463-109">세부 정보 그룹이 포함된 각 내부 그룹의 경우 포함 그룹의 그룹화 셀에 확장/축소 아이콘을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="1e463-109">For each inner group (including the details group), add an expand/collapse icon to the grouping cell of the containing group.</span></span> <span data-ttu-id="1e463-110">보고서가 렌더링되면 사용자가 입력란을 클릭하여 세부 데이터를 확장하거나 축소할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e463-110">When the report is rendered, the user can click the text box to expand and collapse the detail data.</span></span> <span data-ttu-id="1e463-111">자세한 내용은 [테이블&#40;보고서 작성기 및 SSRS&#41;](tables-report-builder-and-ssrs.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1e463-111">For more information, see [Tables &#40;Report Builder  and SSRS&#41;](tables-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="1e463-112">사용자가 항목을 확장 또는 축소할 수 있도록 하려면 해당 항목에 표시 유형 속성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="1e463-112">To allow users to expand or collapse an item, you set the visibility properties for that item.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1e463-113">드릴다운 동작이 있는 보고서를 만드는 경우에는 표시 유형 정보를 행이나 열의 단일 입력란이 아닌 숨기려는 그룹,  열 또는 행에서 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e463-113">When you create a report with a drilldown action, the visibility information must be set on the group, column, or row that you want to hide, not just a single text box in the row or column.</span></span> <span data-ttu-id="1e463-114">또한 토글에 사용하는 입력란은 표시하거나 숨기려는 항목을 제어하는 포함 범위에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e463-114">In addition, the text box that you use for the toggle must be in a containing scope that controls the item that you want to show or hide.</span></span>  
>   
>  <span data-ttu-id="1e463-115">예를 들어 중첩된 그룹에 연결된 행을 숨기려면 입력란이 포함 계층 구조에서 부모 그룹 이상의 그룹과 연결된 행에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e463-115">For example, to hide a row associated with a nested group, the text box must be in a row associated with the parent group or higher in the containment hierarchy.</span></span>  
>   
>  <span data-ttu-id="1e463-116">그룹, 열 또는 행의 가시 정보 설정에 대한 자세한 내용은 [항목에 확장 또는 축소 동작 추가&#40;보고서 작성기 및 SSRS&#41;](add-an-expand-or-collapse-action-to-an-item-report-builder-and-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1e463-116">For information on setting visibility information on the group, column or row, see [Add an Expand or Collapse Action to an Item &#40;Report Builder and SSRS&#41;](add-an-expand-or-collapse-action-to-an-item-report-builder-and-ssrs.md)</span></span>  
  
 <span data-ttu-id="1e463-117">보고서 항목을 숨기는 방법에 대한 자세한 내용은 [항목 숨기기&#40;보고서 작성기 및 SSRS&#41;](../report-builder/hide-an-item-report-builder-and-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1e463-117">For more information about hiding report items, see [Hide an Item &#40;Report Builder and SSRS&#41;](../report-builder/hide-an-item-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="comparing-drilldown-and-drillthrough-reports"></a><span data-ttu-id="1e463-118">드릴다운 및 드릴스루 보고서 비교</span><span class="sxs-lookup"><span data-stu-id="1e463-118">Comparing Drilldown and Drillthrough Reports</span></span>  
 <span data-ttu-id="1e463-119">드릴다운 보고서에서 사용자는 더하기 또는 빼기 단추를 클릭하여 보고서의 섹션을 확장 또는 축소함으로써 해당 위치의 세부 데이터를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="1e463-119">In a drilldown report, a user clicks a plus or minus button to expand or collapse a section of a report to show detail data in place.</span></span> <span data-ttu-id="1e463-120">드릴스루 보고서에서 사용자는 요약 값 링크를 클릭하여 별도의 관련 보고서를 열고 세부 데이터를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e463-120">In a drillthrough report, the user clicks a link for a summary value, and this opens a separate, related report to show detail data.</span></span> <span data-ttu-id="1e463-121">세부 데이터는 세부 정보 보고서가 실행될 때만 검색됩니다.</span><span class="sxs-lookup"><span data-stu-id="1e463-121">The detail data is only retrieved when the detail report runs.</span></span> <span data-ttu-id="1e463-122">일반적으로 드릴스루 보고서는 드릴다운 보고서보다 필요한 리소스가 적습니다.</span><span class="sxs-lookup"><span data-stu-id="1e463-122">Drillthrough reports typically require fewer resources than drilldown reports.</span></span> <span data-ttu-id="1e463-123">자세한 내용은 [드릴스루, 드릴다운, 하위 보고서 및 중첩 데이터 영역&#40;보고서 작성기 및 SSRS&#41;](drillthrough-drilldown-subreports-and-nested-data-regions.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1e463-123">For more information, see [Drillthrough, Drilldown, Subreports, and Nested Data Regions &#40;Report Builder and SSRS&#41;](drillthrough-drilldown-subreports-and-nested-data-regions.md).</span></span>  
  
## <a name="rendering-extension-support-for-hidden-report-items"></a><span data-ttu-id="1e463-124">숨겨진 보고서 항목에 대한 렌더링 확장 프로그램별 지원 기능</span><span class="sxs-lookup"><span data-stu-id="1e463-124">Rendering Extension Support for Hidden Report Items</span></span>  
 <span data-ttu-id="1e463-125">보고서 항목의 표시/숨기기 토글 기능은 사용자 상호 작용을 지원하는 렌더링 확장 프로그램(예:  보고서 작성기 및 보고서 관리자에서 보고서를 실행할 때 사용되는 HTML  렌더링 확장 프로그램)에서만 지원되며,</span><span class="sxs-lookup"><span data-stu-id="1e463-125">The show-and-hide toggle on report items is supported only by rendering extensions that support user interactivity, such as the HTML rendering extension that is used when you run a report in Report Builder and in Report Manager, for example.</span></span> <span data-ttu-id="1e463-126">다른 렌더링 확장 프로그램은 숨겨진 항목을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="1e463-126">Other rendering extensions display hidden items.</span></span> <span data-ttu-id="1e463-127">아래에서는 조건부 표시 유형이 적용된 보고서 항목에 대한 지원을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="1e463-127">The following list describes support for report items with conditional visibility:</span></span>  
  
-   <span data-ttu-id="1e463-128">HTML에서 숨겨진 항목은 HTML  원본에 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1e463-128">In HTML, if items are hidden, they are not visible in the HTML source.</span></span>  
  
-   <span data-ttu-id="1e463-129">XML  렌더링 확장 프로그램은 숨김 여부에 관계없이 모든 보고서 항목을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="1e463-129">The XML rendering extension displays all report items, regardless of whether they are hidden.</span></span>  
  
-   <span data-ttu-id="1e463-130">Excel  렌더링 확장 프로그램은 테이블,  행렬 또는 목록에 대해 숨겨진 행과 열을 표시하고 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="1e463-130">The Excel rendering extension displays and expands hidden rows and columns for a table, matrix, or list.</span></span> <span data-ttu-id="1e463-131">행과 열이 모두 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="1e463-131">All rows and columns are visible.</span></span>  
  
 <span data-ttu-id="1e463-132">자세한 내용은 [렌더링 동작&#40;보고서 작성기 및 SSRS&#41;](rendering-behaviors-report-builder-and-ssrs.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1e463-132">For more information, see [Rendering Behaviors &#40;Report Builder  and SSRS&#41;](rendering-behaviors-report-builder-and-ssrs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e463-133">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1e463-133">See Also</span></span>  
 <span data-ttu-id="1e463-134">[드릴스루, 드릴다운, 하위 보고서 및 중첩 데이터 영역&#40;보고서 작성기 및 SSRS&#41;](drillthrough-drilldown-subreports-and-nested-data-regions.md) </span><span class="sxs-lookup"><span data-stu-id="1e463-134">[Drillthrough, Drilldown, Subreports, and Nested Data Regions &#40;Report Builder and SSRS&#41;](drillthrough-drilldown-subreports-and-nested-data-regions.md) </span></span>  
 <span data-ttu-id="1e463-135">[대화형 정렬, 문서 구조 및 링크&#40;보고서 작성기 및 SSRS&#41;](interactive-sort-document-maps-and-links-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="1e463-135">[Interactive Sort, Document Maps, and Links &#40;Report Builder and SSRS&#41;](interactive-sort-document-maps-and-links-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="1e463-136">식 예&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="1e463-136">Expression Examples &#40;Report Builder and SSRS&#41;</span></span>](expression-examples-report-builder-and-ssrs.md)  
  
  
