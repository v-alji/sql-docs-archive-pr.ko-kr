---
title: 꺾은선형 차트(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 194e6679-890d-4a3e-a756-130d32ef7e29
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 44e7a011186e66e6b8bdc8b5dd31939c883e320b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739268"
---
# <a name="line-charts-report-builder-and-ssrs"></a><span data-ttu-id="ae39c-102">꺾은선형 차트(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="ae39c-102">Line Charts (Report Builder and SSRS)</span></span>
  <span data-ttu-id="ae39c-103">꺾은선형 차트에서 계열은 단일 선으로 연결된 일련의 점으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="ae39c-103">A line chart displays a series as a set of points connected by a single line.</span></span> <span data-ttu-id="ae39c-104">꺾은선형 차트는 연속적인 일정 기간 동안 발생하는 많은 양의 데이터를 표시하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="ae39c-104">Line charts are used to representing large amounts of data that occur over a continuous period of time.</span></span> <span data-ttu-id="ae39c-105">꺾은선형 차트에 데이터를 추가하는 방법에 대한 자세한 내용은 [차트&#40;보고서 작성기 및 SSRS&#41;](charts-report-builder-and-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ae39c-105">For more information about how to add data to a line chart, see [Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="ae39c-106">다음 그림에서는 계열이 세 개 포함된 꺾은선형 차트를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ae39c-106">The following illustration shows a line chart that contains three series.</span></span>  
  
 <span data-ttu-id="ae39c-107">![꺾은선형 차트](../media/rs-linechart.gif "꺾은선형 차트")</span><span class="sxs-lookup"><span data-stu-id="ae39c-107">![Line chart](../media/rs-linechart.gif "Line chart")</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="variations"></a><span data-ttu-id="ae39c-108">변형</span><span class="sxs-lookup"><span data-stu-id="ae39c-108">Variations</span></span>  
  
-   <span data-ttu-id="ae39c-109">**곡선형**.</span><span class="sxs-lookup"><span data-stu-id="ae39c-109">**Smooth line**.</span></span> <span data-ttu-id="ae39c-110">일반적인 선 대신 곡선을 사용하는 꺾은선형 차트입니다.</span><span class="sxs-lookup"><span data-stu-id="ae39c-110">A line chart that uses a curved line instead of a regular line.</span></span>  
  
-   <span data-ttu-id="ae39c-111">**단계별 선형**.</span><span class="sxs-lookup"><span data-stu-id="ae39c-111">**Stepped line**.</span></span> <span data-ttu-id="ae39c-112">일반적인 선 대신 단계별 선을 사용하는 꺾은선형 차트입니다.</span><span class="sxs-lookup"><span data-stu-id="ae39c-112">A line chart that uses a stepped line instead of a regular line.</span></span> <span data-ttu-id="ae39c-113">단계별 선형 차트에서는 사다리나 계단의 층과 같은 모양으로 선을 사용하여 점을 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="ae39c-113">The stepped line connects points by using a line that makes it look like steps on a ladder or staircase.</span></span>  
  
-   <span data-ttu-id="ae39c-114">**스파크라인 차트**.</span><span class="sxs-lookup"><span data-stu-id="ae39c-114">**Sparkline charts**.</span></span> <span data-ttu-id="ae39c-115">테이블 또는 테이블릭스 셀에 선 계열만 표시하는 꺾은선형 차트의 변형입니다.</span><span class="sxs-lookup"><span data-stu-id="ae39c-115">Variations of the line chart that show only the line series in the cell of a table or matrix.</span></span> <span data-ttu-id="ae39c-116">자세한 내용은 [스파크라인 및 데이터 막대&#40;보고서 작성기 및 SSRS&#41;](sparklines-and-data-bars-report-builder-and-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ae39c-116">For more information, see [Sparklines and Data Bars &#40;Report Builder and SSRS&#41;](sparklines-and-data-bars-report-builder-and-ssrs.md).</span></span>  
  
## <a name="data-considerations-for-line-charts"></a><span data-ttu-id="ae39c-117">꺾은선형 차트의 데이터 고려 사항</span><span class="sxs-lookup"><span data-stu-id="ae39c-117">Data Considerations for Line Charts</span></span>  
  
-   <span data-ttu-id="ae39c-118">기본 꺾은선형 차트의 시각적 효과를 높이기 위해 계열 테두리의 두께를 3으로 변경하고 그림자 오프셋 값으로 1을 추가하는 것도 좋은 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="ae39c-118">To improve the visual impact of the default line chart, consider changing the width of the series border to 3, and adding a shadow offset of 1.</span></span> <span data-ttu-id="ae39c-119">이렇게 하면 훨씬 더 강조된 꺾은선형 차트를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ae39c-119">This will create a much bolder line chart.</span></span> <span data-ttu-id="ae39c-120">단, 차트 종류를 꺾은선형에서 다른 종류로 변경하려면 이러한 속성을 원래 값으로 되돌려야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ae39c-120">You will need to revert these properties to their original values if you change the chart type from Line to another type.</span></span>  
  
-   <span data-ttu-id="ae39c-121">데이터 세트에 빈 값이 들어 있는 경우 꺾은선형 차트에서는 차트의 연속성을 유지하기 위해 자리 표시자 선의 형태로 빈 점을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="ae39c-121">If your dataset includes empty values, the line chart will add empty points, in the form of placeholder lines, in order to maintain continuity on the chart.</span></span> <span data-ttu-id="ae39c-122">이러한 선을 표시하지 않으려면 가로 막대형 차트나 세로 막대형 차트 같이 데이터를 연속적으로 표시하지 않는 차트 종류를 사용하여 데이터 세트를 표시하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="ae39c-122">If you would rather not see these lines, consider displaying your dataset using a non-contiguous chart type such as a bar or column chart.</span></span>  
  
-   <span data-ttu-id="ae39c-123">꺾은선형 차트에는 선을 그리기 위한 점이 적어도 두 개 이상 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="ae39c-123">A line chart requires at least two points to draw a line.</span></span>  <span data-ttu-id="ae39c-124">데이터 세트에 포함된 데이터 요소가 한 개뿐이면 꺾은선형 차트가 단일 데이터 요소 표식으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="ae39c-124">If your dataset has only one data point, the line chart will display as a single data point marker.</span></span>  
  
-   <span data-ttu-id="ae39c-125">선으로 그려진 계열은 차트 영역 내에서 공간을 많이 차지하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ae39c-125">A series that is drawn as a line will not take up much space within a chart area.</span></span>  <span data-ttu-id="ae39c-126">따라서 꺾은선형 차트는 세로 막대형 차트 같은 다른 차트 종류와 자주 결합하여 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="ae39c-126">For this reason, line charts are frequently combined with other chart types such as column charts.</span></span> <span data-ttu-id="ae39c-127">그러나 가로 막대형, 극좌표형, 원형 또는 셰이프 차트 종류와는 꺾은선형 차트를 결합할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ae39c-127">However, you cannot combine a line chart with bar, polar, pie or shape chart types.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae39c-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ae39c-128">See Also</span></span>  
 <span data-ttu-id="ae39c-129">[가로 막대형 차트&#40;보고서 작성기 및 SSRS&#41;](bar-charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="ae39c-129">[Bar Charts &#40;Report Builder and SSRS&#41;](bar-charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="ae39c-130">[세로 막대형 차트&#40;보고서 작성기 및 SSRS&#41;](column-charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="ae39c-130">[Column Charts &#40;Report Builder and SSRS&#41;](column-charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="ae39c-131">[차트&#40;보고서 작성기 및 SSRS&#41;](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="ae39c-131">[Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="ae39c-132">[차트 종류&#40;보고서 작성기 및 SSRS&#41;](chart-types-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="ae39c-132">[Chart Types &#40;Report Builder and SSRS&#41;](chart-types-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="ae39c-133">[영역형 차트&#40;보고서 작성기 및 SSRS&#41;](area-charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="ae39c-133">[Area Charts &#40;Report Builder and SSRS&#41;](area-charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="ae39c-134">[차트의 빈 데이터 요소 및 Null 데이터 요소&#40;보고서 작성기 및 SSRS&#41;](empty-and-null-data-points-in-charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="ae39c-134">[Empty and Null Data Points in Charts &#40;Report Builder and SSRS&#41;](empty-and-null-data-points-in-charts-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="ae39c-135">차트&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="ae39c-135">Charts &#40;Report Builder and SSRS&#41;</span></span>](charts-report-builder-and-ssrs.md)  
  
  
