---
title: 차트의 빈 데이터 요소 및 Null 데이터 요소(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: faddd29d-4cc1-4c2c-8e29-d3d9918fe22a
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3f0826a202969b432e53b3c57ddfe80680ba99e7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728039"
---
# <a name="empty-and-null-data-points-in-charts-report-builder-and-ssrs"></a><span data-ttu-id="208d0-102">차트의 빈 데이터 요소 및 Null 데이터 요소(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="208d0-102">Empty and Null Data Points in Charts (Report Builder and SSRS)</span></span>
  <span data-ttu-id="208d0-103">빈 값이나 null 값이 있는 필드를 차트에 표시하면 차트가 제대로 표시되지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="208d0-103">If you are displaying fields with empty or null values in your chart, the chart may not look as you expect.</span></span> <span data-ttu-id="208d0-104">차트에서 빈 값이 처리되는 방법은 지정된 차트 종류에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="208d0-104">Charts process empty values differently depending on the specified chart type:</span></span>  
  
-   <span data-ttu-id="208d0-105">차트 종류가 선형 차트 종류(가로 막대형, 세로 막대형, 분산형, 꺾은선형, 영역형, 범위형)인 경우 빈 값은 차트에 빈 공간 또는 "간격"으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="208d0-105">If the chart type is a linear chart type (bar, column, scatter, line, area, range), empty values are displayed as empty spaces or "gaps" in the chart.</span></span> <span data-ttu-id="208d0-106">빈 요소를 표시하려는 경우에는 빈 요소 자리 표시자를 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="208d0-106">If you want to indicate empty points, you must add empty point placeholders.</span></span> <span data-ttu-id="208d0-107">자세한 내용은 [차트에 빈 요소 추가 &#40;보고서 작성기 및 SSRS&#41;](add-empty-points-to-a-chart-report-builder-and-ssrs.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="208d0-107">For more information, see [Add Empty Points to the Chart &#40;Report Builder and SSRS&#41;](add-empty-points-to-a-chart-report-builder-and-ssrs.md).</span></span>  
  
-   <span data-ttu-id="208d0-108">차트 종류가 연속적 선형 차트 종류(영역형, 가로 막대형, 세로 막대형, 꺾은선형, 분산형)인 경우 계열의 연속성을 유지하기 위해 차트에 빈 데이터 요소가 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="208d0-108">If the chart type is a contiguous, linear chart type (area, bar, column, line, scatter), empty data points are added to the chart to maintain continuity in the series.</span></span>  
  
-   <span data-ttu-id="208d0-109">비선형 차트 종류(극좌표형, 원형, 도넛형, 깔때기형, 피라미드형)의 경우 빈 값은 차트 표시에서 생략됩니다.</span><span class="sxs-lookup"><span data-stu-id="208d0-109">If the chart type is a nonlinear chart type (polar, pie, doughnut, funnel or pyramid), empty values are omitted from display on the chart.</span></span>  
  
-   <span data-ttu-id="208d0-110">셰이프 차트 종류에서는 Null 값이 생략됩니다.</span><span class="sxs-lookup"><span data-stu-id="208d0-110">In shape chart types, null values are omitted.</span></span>  
  
 <span data-ttu-id="208d0-111">빈 데이터 요소가 있는 차트의 예는 예제 보고서로 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="208d0-111">An example of a chart with empty data points is available as a sample report.</span></span> <span data-ttu-id="208d0-112">이 예제 보고서 및 기타 보고서를 다운로드 하는 방법에 대 한 자세한 내용은 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [보고서 작성기 및 보고서 디자이너 샘플 보고서](https://go.microsoft.com/fwlink/?LinkId=198283)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="208d0-112">For more information about downloading this sample report and others, see [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][Report Builder and Report Designer sample reports](https://go.microsoft.com/fwlink/?LinkId=198283).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="removing-empty-or-null-values"></a><span data-ttu-id="208d0-113">빈 값 또는 Null 값 제거</span><span class="sxs-lookup"><span data-stu-id="208d0-113">Removing Empty or Null Values</span></span>  
 <span data-ttu-id="208d0-114">중요한 데이터가 가려지지 않도록 하려면 데이터 세트에서 빈 값을 제거하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="208d0-114">To avoid obscuring important data, consider removing empty values from your dataset.</span></span> <span data-ttu-id="208d0-115">Null을 필터링하려면 쿼리에 NOT IS NULL 절을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="208d0-115">To filter nulls, you can use the NOT IS NULL clause in your query.</span></span> <span data-ttu-id="208d0-116">또는 0이 아닌 값만 표시하도록 지정하는 필터링 식을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="208d0-116">Alternatively, you can add a filtering expression that specifies that you only want to display values not equal to zero.</span></span> <span data-ttu-id="208d0-117">자세한 내용은 [데이터 세트 필터, 데이터 영역 필터 및 그룹 필터 추가&#40;보고서 작성기 및 SSRS&#41;](add-dataset-filters-data-region-filters-and-group-filters.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="208d0-117">For more information, see [Add Dataset Filters, Data Region Filters, and Group Filters &#40;Report Builder and SSRS&#41;](add-dataset-filters-data-region-filters-and-group-filters.md).</span></span>  
  
## <a name="fields-with-no-values-in-a-chart"></a><span data-ttu-id="208d0-118">차트에서 값이 없는 필드</span><span class="sxs-lookup"><span data-stu-id="208d0-118">Fields with No Values in a Chart</span></span>  
 <span data-ttu-id="208d0-119">반환된 데이터 세트에서 필드에 값이 포함되어 있지 않은 경우 차트는 데이터 요소가 없는 빈 차트를 표시하지만 계열 이름(일반적으로 필드 이름)은 범례 항목으로 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="208d0-119">If a field does not contain any values in the returned dataset, the chart displays an empty chart with no data points, but the series name (typically the field name) is added as a legend item.</span></span>  
  
 <span data-ttu-id="208d0-120">이 동작은 보고서에 매개 변수가 있고 선택된 값이 빈 결과 세트를 반환할 때 발생할 수 있는 경우인 반환된 데이터 세트에 데이터 행이 0개인 경우와는 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="208d0-120">This behavior differs from the case where there are zero rows of data in the returned dataset, which can occur when the report is parameterized and the selected value returns an empty result set.</span></span> <span data-ttu-id="208d0-121">데이터 세트 쿼리가 0개의 데이터 행을 반환하는 경우 표시할 데이터가 없음을 알리는 메시지가 런타임에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="208d0-121">If your dataset query returns zero rows of data, a message is displayed at run time to indicate that no data can be shown.</span></span> <span data-ttu-id="208d0-122">**속성** 창에서 보고서의 NoDataMessage 캡션을 수정하여 이 메시지를 사용자 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="208d0-122">You can customize this message by modifying the NoDataMessage caption for the report in the **Properties** pane.</span></span> <span data-ttu-id="208d0-123">자세한 내용은 [보고서 포함된 데이터 세트 및 공유 데이터 세트&#40;보고서 작성기 및 SSRS&#41;](../report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="208d0-123">For more information, see [Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;](../report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="208d0-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="208d0-124">See Also</span></span>  
 <span data-ttu-id="208d0-125">[차트 &#40;보고서 작성기 및 SSRS&#41;](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="208d0-125">[Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="208d0-126">[보고서 작성기 및 SSRS&#41;&#40;차트 서식 지정](formatting-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="208d0-126">[Formatting a Chart &#40;Report Builder and SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="208d0-127">[보고서 &#40;보고서 작성기 및 SSRS에 차트 추가&#41;](add-a-chart-to-a-report-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="208d0-127">[Add a Chart to a Report &#40;Report Builder and SSRS&#41;](add-a-chart-to-a-report-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="208d0-128">차트 문제 해결&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="208d0-128">Troubleshoot Charts &#40;Report Builder and SSRS&#41;</span></span>](troubleshoot-charts-report-builder-and-ssrs.md)  
  
  
