---
title: 원형 차트 외부에 데이터 요소 레이블 표시(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 959b7574-cf43-470b-b592-4944d8a9948f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: dd4f38f24d2729acacfa3520635b93d8af2e9433
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736096"
---
# <a name="display-data-point-labels-outside-a-pie-chart-report-builder-and-ssrs"></a><span data-ttu-id="2ca0d-102">원형 차트 외부에 데이터 요소 레이블 표시(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="2ca0d-102">Display Data Point Labels Outside a Pie Chart (Report Builder and SSRS)</span></span>
  <span data-ttu-id="2ca0d-103">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]에서 원형 차트 레이블 지정은 몇 개의 데이터 조각에만 레이블을 표시하도록 최적화되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2ca0d-103">In [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], pie chart labeling is optimized to display labels on only several slices of data.</span></span> <span data-ttu-id="2ca0d-104">원형 차트에 조각이 너무 많을 경우 레이블이 겹쳐서 표시될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2ca0d-104">Labels may overlap if the pie chart contains too many slices.</span></span> <span data-ttu-id="2ca0d-105">한 가지 해결 방법은 원형 차트 외부에 레이블을 표시하여 이름이 긴 데이터 레이블에 대한 공간을 더 확보하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="2ca0d-105">One solution is to display the labels outside the pie chart, which may create more room for longer data labels.</span></span> <span data-ttu-id="2ca0d-106">그래도 여전히 레이블이 겹칠 경우 3D를 설정하여 더 많은 공간을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2ca0d-106">If you find that your labels still overlap, you can create more space for them by enabling 3D.</span></span> <span data-ttu-id="2ca0d-107">이렇게 하면 원형 차트의 지름이 줄어 차트 주위에 더 많은 공간이 확보됩니다.</span><span class="sxs-lookup"><span data-stu-id="2ca0d-107">This reduces the diameter of the pie chart, creating more space around the chart.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-display-data-point-labels-inside-a-pie-chart"></a><span data-ttu-id="2ca0d-108">원형 차트 내부에 데이터 요소 레이블을 표시하려면</span><span class="sxs-lookup"><span data-stu-id="2ca0d-108">To display data point labels inside a pie chart</span></span>  
  
1.  <span data-ttu-id="2ca0d-109">보고서에 원형 차트를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="2ca0d-109">Add a pie chart to your report.</span></span> <span data-ttu-id="2ca0d-110">자세한 내용은 [보고서에 차트 추가&#40;보고서 작성기 및 SSRS&#41;](add-a-chart-to-a-report-report-builder-and-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2ca0d-110">For more information, see [Add a Chart to a Report &#40;Report Builder and SSRS&#41;](add-a-chart-to-a-report-report-builder-and-ssrs.md).</span></span>  
  
2.  <span data-ttu-id="2ca0d-111">디자인 화면에서 차트를 마우스 오른쪽 단추로 클릭하고 **데이터 레이블 표시**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="2ca0d-111">On the design surface, right-click on the chart and select **Show Data Labels**.</span></span>  
  
### <a name="to-display-data-point-labels-outside-a-pie-chart"></a><span data-ttu-id="2ca0d-112">원형 차트 외부에 데이터 요소 레이블을 표시하려면</span><span class="sxs-lookup"><span data-stu-id="2ca0d-112">To display data point labels outside a pie chart</span></span>  
  
1.  <span data-ttu-id="2ca0d-113">원형 차트를 만들고 데이터 레이블을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="2ca0d-113">Create a pie chart and display the data labels.</span></span>  
  
2.  <span data-ttu-id="2ca0d-114">속성 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="2ca0d-114">Open the Properties pane.</span></span>  
  
3.  <span data-ttu-id="2ca0d-115">디자인 화면에서 원형 자체를 클릭하여 속성 창에 **범주** 속성을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="2ca0d-115">On the design surface, click on the pie itself to display the **Category** properties in the Properties pane.</span></span>  
  
4.  <span data-ttu-id="2ca0d-116">**CustomAttributes** 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="2ca0d-116">Expand the **CustomAttributes** node.</span></span> <span data-ttu-id="2ca0d-117">원형 차트에 대한 특성 목록이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="2ca0d-117">A list of attributes for the pie chart is displayed.</span></span>  
  
5.  <span data-ttu-id="2ca0d-118">**PieLabelStyle** 속성을 **Outside**로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="2ca0d-118">Set the **PieLabelStyle** property to **Outside**.</span></span>  
  
6.  <span data-ttu-id="2ca0d-119">속성을 `PieLineColor` **Black**으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2ca0d-119">Set the `PieLineColor` property to **Black**.</span></span> <span data-ttu-id="2ca0d-120">PieLineColor 속성은 각 데이터 요소 레이블에 대한 설명선을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="2ca0d-120">The PieLineColor property defines callout lines for each data point label.</span></span>  
  
### <a name="to-prevent-overlapping-labels-displayed-outside-a-pie-chart"></a><span data-ttu-id="2ca0d-121">원형 차트 외부에 표시되는 레이블이 겹쳐지지 않도록 하려면</span><span class="sxs-lookup"><span data-stu-id="2ca0d-121">To prevent overlapping labels displayed outside a pie chart</span></span>  
  
1.  <span data-ttu-id="2ca0d-122">외부 레이블을 사용하여 원형 차트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2ca0d-122">Create a pie chart with external labels.</span></span>  
  
2.  <span data-ttu-id="2ca0d-123">디자인 화면에서 원형 차트 외부와 차트 테두리 내부 사이를 마우스 오른쪽 단추로 클릭하고 **차트 영역 속성**을 선택합니다. **차트 영역 속성** 대화 상자가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="2ca0d-123">On the design surface, right-click outside the pie chart but inside the chart borders and select **Chart Area Properties**.The **Chart AreaProperties** dialog box appears.</span></span>  
  
3.  <span data-ttu-id="2ca0d-124">**3D 옵션** 탭에서 **3D 사용**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="2ca0d-124">On the **3D Options** tab, select **Enable 3D**.</span></span>  
  
4.  <span data-ttu-id="2ca0d-125">레이블을 위한 공간을 더 확보하면서 차트를 계속 2차원으로 표시하려면 **회전** 및 **기울기** 속성을 **0**으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="2ca0d-125">If you want the chart to have more room for labels but still appear two-dimensional, set the **Rotation** and **Inclination** properties to **0**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ca0d-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2ca0d-126">See Also</span></span>  
 <span data-ttu-id="2ca0d-127">[원형 차트&#40;보고서 작성기 및 SSRS&#41;](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="2ca0d-127">[Pie Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="2ca0d-128">[원형 차트에서 작은 조각 수집&#40;보고서 작성기 및 SSRS&#41;](collect-small-slices-on-a-pie-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="2ca0d-128">[Collect Small Slices on a Pie Chart &#40;Report Builder and SSRS&#41;](collect-small-slices-on-a-pie-chart-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="2ca0d-129">원형 차트에서 백분율 값 표시&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="2ca0d-129">Display Percentage Values on a Pie Chart &#40;Report Builder and SSRS&#41;</span></span>](display-percentage-values-on-a-pie-chart-report-builder-and-ssrs.md)  
  
  
