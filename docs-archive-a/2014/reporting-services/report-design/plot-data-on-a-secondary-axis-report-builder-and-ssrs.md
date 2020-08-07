---
title: 보조 축에 데이터 표시(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 094f39bf-3634-4852-9fc3-3adec4b266e5
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: cec58820e0373bb1e9ef2d50d022e5b4ef7e962b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727932"
---
# <a name="plot-data-on-a-secondary-axis-report-builder-and-ssrs"></a><span data-ttu-id="f4482-102">보조 축에 데이터 표시(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="f4482-102">Plot Data on a Secondary Axis (Report Builder and SSRS)</span></span>
  <span data-ttu-id="f4482-103">차트는 기본 및 보조라는 두 가지 축 유형이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f4482-103">The chart has two axis types: primary and secondary.</span></span> <span data-ttu-id="f4482-104">보조 축은 공통 범주를 공유하는 두 개의 개별 데이터 범위를 사용하여 두 개의 값 집합을 비교할 때 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="f4482-104">The secondary axis is useful when comparing two value sets with two distinct data ranges that share a common category.</span></span>  
  
 <span data-ttu-id="f4482-105">예를 들어 2008년에 대한 수익과 세금을 계산하는 차트가 있다고 가정해 보십시오.</span><span class="sxs-lookup"><span data-stu-id="f4482-105">For example, suppose you have a chart that calculates Revenue vs. Tax for the year 2008.</span></span> <span data-ttu-id="f4482-106">이 경우 2008년이라는 기간은 두 값 집합에 대한 공통 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="f4482-106">In this case, the 2008 time period is common to both value sets.</span></span> <span data-ttu-id="f4482-107">하지만 두 계열을 동일한 y축에 표시할 경우 y축 눈금은 데이터 세트의 가장 큰 값에 최적화되기 때문에 제대로 된 비교를 할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f4482-107">However, when both series are plotted on the same y-axis, we cannot make a useful comparison because the scale of the y-axis is optimized for the largest values in the dataset.</span></span> <span data-ttu-id="f4482-108">수익을 기본 축에 표시하고 세금을 보조 축에 표시하면 고유한 값 눈금이 있는 y축에 각 계열을 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f4482-108">If we show Revenue on the primary axis, and Tax on the secondary axis, we can display each series on its own y-axis with its own scale of values.</span></span> <span data-ttu-id="f4482-109">계열은 여전히 공통 x축을 공유합니다.</span><span class="sxs-lookup"><span data-stu-id="f4482-109">The series still share a common x-axis.</span></span>  
  
 <span data-ttu-id="f4482-110">비교할 계열이 3개 이상인 경우에는 차트의 여러 계열을 비교 및 표시하기 위한 다른 방법을 고려해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4482-110">In situations where there are more than two series to be compared, consider a different approach for comparing and displaying multiple series in a chart.</span></span> <span data-ttu-id="f4482-111">자세한 내용은 [차트의 여러 계열&#40;보고서 작성기 및 SSRS&#41;](multiple-series-on-a-chart-report-builder-and-ssrs.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f4482-111">For more information, see [Multiple Series on a Chart &#40;Report Builder and SSRS&#41;](multiple-series-on-a-chart-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="f4482-112">이 차트의 예는 예제 보고서로 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="f4482-112">An example of this chart is available as a sample report.</span></span> <span data-ttu-id="f4482-113">이 예제 보고서 및 기타 보고서를 다운로드 하는 방법에 대 한 자세한 내용은 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [보고서 작성기 및 보고서 디자이너 샘플 보고서](https://go.microsoft.com/fwlink/?LinkId=198283)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f4482-113">For more information about downloading this sample report and others, see [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][Report Builder and Report Designer sample reports](https://go.microsoft.com/fwlink/?LinkId=198283).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-plot-a-series-on-the-secondary-axis"></a><span data-ttu-id="f4482-114">보조 축에 계열을 표시하려면</span><span class="sxs-lookup"><span data-stu-id="f4482-114">To plot a series on the secondary axis</span></span>  
  
1.  <span data-ttu-id="f4482-115">차트에서 계열을 마우스 오른쪽 단추로 클릭하거나 **값** 영역에서 보조 축에 표시하려는 필드를 마우스 오른쪽 단추로 클릭하고 **계열 속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f4482-115">Right-click the series in the chart or right-click on a field in the **Values** area that you want to display on the secondary axis and click **Series Properties**.</span></span> <span data-ttu-id="f4482-116">**계열 속성** 대화 상자가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f4482-116">The **Series Properties** dialog box appears.</span></span>  
  
2.  <span data-ttu-id="f4482-117">**축 및 차트 영역**을 클릭하고 설정하려는 보조 축, 값 축 또는 범주 축을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f4482-117">Click **Axes and Chart Area**, and select which of the secondary axes you want to enable, the value axis or the category axis.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4482-118">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f4482-118">See Also</span></span>  
 <span data-ttu-id="f4482-119">[차트의 축 레이블 서식 지정 &#40;보고서 작성기 및 SSRS&#41;](formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="f4482-119">[Formatting Axis Labels on a Chart &#40;Report Builder and SSRS&#41;](formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="f4482-120">축 간격 지정&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="f4482-120">Specify an Axis Interval &#40;Report Builder and SSRS&#41;</span></span>](specify-an-axis-interval-report-builder-and-ssrs.md)  
  
  
