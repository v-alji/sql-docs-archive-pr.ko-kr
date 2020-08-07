---
title: 범위형 차트(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 48e351d3-ac5b-4eda-a4bd-32a0de206a30
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 76a9723bc55030da59d22c945a40ce4418b84ab3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87733619"
---
# <a name="range-charts-report-builder-and-ssrs"></a><span data-ttu-id="2c135-102">범위형 차트(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="2c135-102">Range Charts (Report Builder and SSRS)</span></span>
  <span data-ttu-id="2c135-103">범위형 차트에서는 각각 동일한 범주의 여러 값으로 정의된 일련의 데이터 요소를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="2c135-103">A range chart type displays a set of data points that are each defined by multiple values for the same category.</span></span> <span data-ttu-id="2c135-104">값은 값 축을 기준으로 측정되는 표식의 높이로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="2c135-104">Values are represented by the height of the marker as measured by the value axis.</span></span> <span data-ttu-id="2c135-105">범주 레이블은 범주 축에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="2c135-105">Category labels are displayed on the category axis.</span></span> <span data-ttu-id="2c135-106">일반 범위형 차트는 각 데이터 요소의 상위 값과 하위 값 사이 영역을 채웁니다.</span><span class="sxs-lookup"><span data-stu-id="2c135-106">The plain range chart fills in the area between the top and bottom value for each data point.</span></span>  
  
 <span data-ttu-id="2c135-107">다음 그림은 계열이 3개가 있는 일반 범위형 차트를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2c135-107">The following illustration shows a plain range chart with three series.</span></span>  
  
 <span data-ttu-id="2c135-108">![범위형 차트](../media/rs-rangechart.gif "범위형 차트")</span><span class="sxs-lookup"><span data-stu-id="2c135-108">![Range chart](../media/rs-rangechart.gif "Range chart")</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="variations"></a><span data-ttu-id="2c135-109">변형</span><span class="sxs-lookup"><span data-stu-id="2c135-109">Variations</span></span>  
  
-   <span data-ttu-id="2c135-110">**곡선 범위형**.</span><span class="sxs-lookup"><span data-stu-id="2c135-110">**Smooth range**.</span></span> <span data-ttu-id="2c135-111">곡선 범위형 차트는 직선보다는 곡선을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="2c135-111">A smooth range chart displays curved lines rather than straight.</span></span>  
  
-   <span data-ttu-id="2c135-112">**세로 막대 범위형**.</span><span class="sxs-lookup"><span data-stu-id="2c135-112">**Column range**.</span></span> <span data-ttu-id="2c135-113">세로 막대 범위형 차트는 영역 대신 세로 막대를 사용하여 범위를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="2c135-113">A column range chart uses columns instead of areas to display the ranges.</span></span>  
  
-   <span data-ttu-id="2c135-114">**가로 막대 범위형**.</span><span class="sxs-lookup"><span data-stu-id="2c135-114">**Bar range**.</span></span> <span data-ttu-id="2c135-115">가로 막대 범위형 차트는 영역 대신 가로 막대를 사용하여 범위를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="2c135-115">A bar range chart uses bars instead of areas to display the ranges.</span></span>  
  
## <a name="data-considerations-for-range-charts"></a><span data-ttu-id="2c135-116">범위형 차트의 데이터 고려 사항</span><span class="sxs-lookup"><span data-stu-id="2c135-116">Data Considerations for Range Charts</span></span>  
  
-   <span data-ttu-id="2c135-117">범위형 차트 종류에는 데이터 요소마다 두 개의 값이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="2c135-117">Range chart types require two values per data point.</span></span> <span data-ttu-id="2c135-118">이 값은 각 데이터 요소의 범위를 정의하는 상위 값과 하위 값에 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="2c135-118">These values correspond with a high value and a low value that defines the range for each data point.</span></span>  
  
-   <span data-ttu-id="2c135-119">범위형 차트는 상위 값이 하위 값보다 항상 큰 경우에만 분석에 유용하게 사용될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c135-119">Range charts are useful for analysis only if the top values are always higher than the bottom values.</span></span> <span data-ttu-id="2c135-120">그렇지 않은 경우에는 꺾은선형 차트를 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="2c135-120">If this is not the case, consider using a line chart.</span></span> <span data-ttu-id="2c135-121">상위 값이 하위 값보다 작으면 범위형 차트는 두 값의 차이에 대한 절대값을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="2c135-121">If the high value is lower the low value, the range chart will display the absolute value of the difference between these values.</span></span>  
  
-   <span data-ttu-id="2c135-122">하나의 값만 지정된 경우 범위형 차트는 데이터 요소당 값이 하나만 있는 일반적인 영역형 차트와 같이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="2c135-122">If only one value is specified, the range chart will display as if it were a regular area chart, with one value per data point.</span></span>  
  
-   <span data-ttu-id="2c135-123">범위형 차트는 데이터 세트의 각 범주 그룹에 대한 최소값과 최대값을 포함하는 데이터를 그래프로 표시하는 데 많이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="2c135-123">Range charts are often used to graph data that contains minimum and maximum values for each category group in the dataset.</span></span>  
  
-   <span data-ttu-id="2c135-124">범위형 차트에서는 각 데이터 요소에 표식을 표시할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2c135-124">Displaying markers on each data point is not supported on the range chart.</span></span>  
  
-   <span data-ttu-id="2c135-125">영역형 차트와 마찬가지로 일반 범위형 차트에서는 여러 계열의 값이 유사한 경우 계열이 겹쳐 표시될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c135-125">Like the area chart, in a plain range chart, if the values in multiple series are similar, the series will overlap.</span></span> <span data-ttu-id="2c135-126">이러한 경우 일반 범위형 차트 대신 세로 막대 범위형 차트 또는 가로 막대 범위형 차트를 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="2c135-126">In this scenario, you may want to use a column range or bar range chart instead of a plain range chart.</span></span>  
  
-   <span data-ttu-id="2c135-127">Gantt 차트는 범위형 가로 막대 차트를 사용하여 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c135-127">Gantt charts can be created using a range bar chart.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c135-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2c135-128">See Also</span></span>  
 <span data-ttu-id="2c135-129">[차트&#40;보고서 작성기 및 SSRS&#41;](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="2c135-129">[Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="2c135-130">[차트 종류&#40;보고서 작성기 및 SSRS&#41;](chart-types-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="2c135-130">[Chart Types &#40;Report Builder and SSRS&#41;](chart-types-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="2c135-131">차트 서식 지정&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="2c135-131">Formatting a Chart &#40;Report Builder and SSRS&#41;</span></span>](formatting-a-chart-report-builder-and-ssrs.md)  
  
  
