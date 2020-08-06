---
title: 분산형 차트(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 2520ae24-0609-4890-807d-3267018aba8e
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 93f9b31089eb8399c7fdfd201d3c799608f2e91e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87733620"
---
# <a name="scatter-charts-report-builder-and-ssrs"></a><span data-ttu-id="ce9e2-102">분산형 차트(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="ce9e2-102">Scatter Charts (Report Builder and SSRS)</span></span>
  <span data-ttu-id="ce9e2-103">분산형 차트에서 계열은 일련의 점으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="ce9e2-103">A scatter chart displays a series as a set of points.</span></span> <span data-ttu-id="ce9e2-104">값은 차트에서 점의 위치로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="ce9e2-104">Values are represented by the position of the points on the chart.</span></span> <span data-ttu-id="ce9e2-105">범주는 차트에서 여러 가지 표식으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="ce9e2-105">Categories are represented by different markers on the chart.</span></span> <span data-ttu-id="ce9e2-106">분산형 차트는 일반적으로 범주 간 집계 데이터를 비교하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="ce9e2-106">Scatter charts are typically used to compare aggregated data across categories.</span></span> <span data-ttu-id="ce9e2-107">분산형 차트에 데이터를 추가하는 방법에 대한 자세한 내용은 [차트&#40;보고서 작성기 및 SSRS&#41;](charts-report-builder-and-ssrs.md)</span><span class="sxs-lookup"><span data-stu-id="ce9e2-107">For more information on how to add data to a scatter chart, see [Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md)</span></span>  
  
 <span data-ttu-id="ce9e2-108">다음 그림에서는 분산형 차트의 예를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ce9e2-108">The following illustration shows an example of a scatter chart.</span></span>  
  
 <span data-ttu-id="ce9e2-109">![분산형 차트](../media/rs-scatterchart.gif "분산형 차트")</span><span class="sxs-lookup"><span data-stu-id="ce9e2-109">![Scatter chart](../media/rs-scatterchart.gif "Scatter chart")</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="variations"></a><span data-ttu-id="ce9e2-110">변형</span><span class="sxs-lookup"><span data-stu-id="ce9e2-110">Variations</span></span>  
  
-   <span data-ttu-id="ce9e2-111">**거품형.**</span><span class="sxs-lookup"><span data-stu-id="ce9e2-111">**Bubble.**</span></span> <span data-ttu-id="ce9e2-112">거품형 차트는 두 데이터 요소 값의 차이를 거품의 크기로 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="ce9e2-112">Bubble charts display the difference between two values of a data point based on the size of the bubble.</span></span> <span data-ttu-id="ce9e2-113">거품이 클수록 두 값의 차이가 큰 것입니다.</span><span class="sxs-lookup"><span data-stu-id="ce9e2-113">The larger the bubble, the larger the difference between the two values.</span></span>  
  
-   <span data-ttu-id="ce9e2-114">**3차원 거품형**.</span><span class="sxs-lookup"><span data-stu-id="ce9e2-114">**3-D Bubble**.</span></span> <span data-ttu-id="ce9e2-115">3차원으로 표시되는 거품형 차트입니다.</span><span class="sxs-lookup"><span data-stu-id="ce9e2-115">A bubble chart displayed in 3-D.</span></span>  
  
## <a name="data-considerations-for-a-scatter-chart"></a><span data-ttu-id="ce9e2-116">분산형 차트의 데이터 고려 사항</span><span class="sxs-lookup"><span data-stu-id="ce9e2-116">Data Considerations for a Scatter Chart</span></span>  
  
-   <span data-ttu-id="ce9e2-117">분산형 차트는 과학, 통계 및 공학 데이터와 같은 숫자 값을 표시하고 비교하는 데 주로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="ce9e2-117">Scatter charts are commonly used for displaying and comparing numeric values, such as scientific, statistical, and engineering data.</span></span>  
  
-   <span data-ttu-id="ce9e2-118">시간에 관계없이 많은 수의 데이터 요소를 비교하려면 분산형 차트를 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="ce9e2-118">Use the scatter chart when you want to compare large numbers of data points without regard to time.</span></span> <span data-ttu-id="ce9e2-119">분산형 차트에 포함되는 데이터가 많을수록 비교가 더 정확해집니다.</span><span class="sxs-lookup"><span data-stu-id="ce9e2-119">The more data that you include in a scatter chart, the better the comparisons that you can make.</span></span>  
  
-   <span data-ttu-id="ce9e2-120">거품형 차트에는 데이터 요소마다 두 개의 값(상위 값 및 하위 값)이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="ce9e2-120">The bubble chart requires two values (top and bottom) per data point.</span></span>  
  
-   <span data-ttu-id="ce9e2-121">분산형 차트는 데이터 요소의 클러스터 및 값 분포를 처리하는 데 적합하며</span><span class="sxs-lookup"><span data-stu-id="ce9e2-121">Scatter charts are ideal for handling the distribution of values and clusters of data points.</span></span> <span data-ttu-id="ce9e2-122">데이터 세트에 요소가 많은 경우(예: 수천 개) 가장 적합한 차트 유형입니다.</span><span class="sxs-lookup"><span data-stu-id="ce9e2-122">This is the best chart type if your dataset contains many points (for example, several thousand points).</span></span> <span data-ttu-id="ce9e2-123">점 차트에 여러 계열을 표시하는 것은 시각적인 혼란을 주므로 피하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="ce9e2-123">Displaying multiple series on a point chart is visually distracting and should be avoided.</span></span> <span data-ttu-id="ce9e2-124">이런 경우에는 꺾은선형 차트를 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="ce9e2-124">In this scenario, consider using a line chart.</span></span>  
  
-   <span data-ttu-id="ce9e2-125">기본적으로 분산형 차트에서는 데이터 요소가 원으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="ce9e2-125">By default, scatter charts display data points as circles.</span></span> <span data-ttu-id="ce9e2-126">분산형 차트에 여러 계열이 있는 경우에는 각 요소의 표식 모양을 사각형, 삼각형, 다이아몬드 등으로 바꾸어 보십시오.</span><span class="sxs-lookup"><span data-stu-id="ce9e2-126">If you have multiple series on a scatter chart, consider changing the marker shape of each point to be square, triangle, diamond, or another shape.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce9e2-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ce9e2-127">See Also</span></span>  
 <span data-ttu-id="ce9e2-128">[차트&#40;보고서 작성기 및 SSRS&#41;](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="ce9e2-128">[Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="ce9e2-129">[차트 종류&#40;보고서 작성기 및 SSRS&#41;](chart-types-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="ce9e2-129">[Chart Types &#40;Report Builder and SSRS&#41;](chart-types-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="ce9e2-130">[차트 서식 지정&#40;보고서 작성기 및 SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="ce9e2-130">[Formatting a Chart &#40;Report Builder and SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="ce9e2-131">꺾은선형 차트&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="ce9e2-131">Line Charts &#40;Report Builder and SSRS&#41;</span></span>](line-charts-report-builder-and-ssrs.md)  
  
  
