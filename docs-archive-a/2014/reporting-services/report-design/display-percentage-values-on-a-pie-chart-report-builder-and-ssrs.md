---
title: 원형 차트에서 백분율 값 표시(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: eb905fc1-5235-4773-a27e-b07be9318be5
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2dee9017d34f2751b790b2e4928571160b597f1d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650731"
---
# <a name="display-percentage-values-on-a-pie-chart-report-builder-and-ssrs"></a><span data-ttu-id="d7a1d-102">원형 차트에서 백분율 값 표시(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="d7a1d-102">Display Percentage Values on a Pie Chart (Report Builder and SSRS)</span></span>
  <span data-ttu-id="d7a1d-103">기본적으로 범주는 범례에 표시되어 각 값을 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="d7a1d-103">By default, categories are shown in the legend to identify each value.</span></span> <span data-ttu-id="d7a1d-104">범주 레이블을 사용하여 원형 차트에 레이블을 적용했다면 범례에 백분율을 표시하기를 원할 것입니다.</span><span class="sxs-lookup"><span data-stu-id="d7a1d-104">If you have labeled the pie chart using category labels, you may want show percentages in the legend.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-display-percentage-values-as-labels-on-a-pie-chart"></a><span data-ttu-id="d7a1d-105">원형 차트에 레이블로 백분율 값을 표시하려면</span><span class="sxs-lookup"><span data-stu-id="d7a1d-105">To display percentage values as labels on a pie chart</span></span>  
  
1.  <span data-ttu-id="d7a1d-106">보고서에 원형 차트를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="d7a1d-106">Add a pie chart to your report.</span></span> <span data-ttu-id="d7a1d-107">자세한 내용은 [보고서에 차트 추가&#40;보고서 작성기 및 SSRS&#41;](add-a-chart-to-a-report-report-builder-and-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d7a1d-107">For more information, see [Add a Chart to a Report &#40;Report Builder and SSRS&#41;](add-a-chart-to-a-report-report-builder-and-ssrs.md).</span></span>  
  
2.  <span data-ttu-id="d7a1d-108">디자인 화면에서 원형을 마우스 오른쪽 단추로 클릭하고 **데이터 레이블 표시**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d7a1d-108">On the design surface, right-click on the pie and select **Show Data Labels**.</span></span> <span data-ttu-id="d7a1d-109">원형 차트의 각 조각 내에 데이터 레이블이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d7a1d-109">The data labels should appear within each slice on the pie chart.</span></span>  
  
3.  <span data-ttu-id="d7a1d-110">디자인 화면에서 레이블을 마우스 오른쪽 단추로 클릭하고 **계열 레이블 속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d7a1d-110">On the design surface, right-click on the labels and select **Series Label Properties**.</span></span> <span data-ttu-id="d7a1d-111">**계열 레이블 속성** 대화 상자가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d7a1d-111">The **Series Label Properties** dialog box appears.</span></span>  
  
4.  <span data-ttu-id="d7a1d-112">`#PERCENT` **레이블 데이터** 옵션에를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="d7a1d-112">Type `#PERCENT` for the **Label data** option.</span></span>  
  
5.  <span data-ttu-id="d7a1d-113">(옵션) 레이블을 표시할 때 사용할 소수 자릿수를 지정하려면 "#PERCENT{P*n*}"를 입력합니다. 여기서 *n* 은 표시할 소수 자릿수입니다.</span><span class="sxs-lookup"><span data-stu-id="d7a1d-113">(Optional) To specify how many decimal places the label shows, type "#PERCENT{P*n*}" where *n* is the number of decimal places to display.</span></span> <span data-ttu-id="d7a1d-114">예를 들어 소수 자릿수를 표시하지 않으려면 "#PERCENT{P0}"를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="d7a1d-114">For example, to display no decimal places, type "#PERCENT{P0}".</span></span>  
  
### <a name="to-display-percentage-values-in-the-legend-of-a-pie-chart"></a><span data-ttu-id="d7a1d-115">원형 차트의 범례에 백분율 값을 표시하려면</span><span class="sxs-lookup"><span data-stu-id="d7a1d-115">To display percentage values in the legend of a pie chart</span></span>  
  
1.  <span data-ttu-id="d7a1d-116">디자인 화면에서 원형 차트를 마우스 오른쪽 단추로 클릭하고 **계열 속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d7a1d-116">On the design surface, right-click on the pie chart and select **Series Properties**.</span></span> <span data-ttu-id="d7a1d-117">**계열 속성** 대화 상자가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d7a1d-117">The **Series Properties** dialog box displays.</span></span>  
  
2.  <span data-ttu-id="d7a1d-118">**범례**에서 `#PERCENT` **사용자 지정 범례 텍스트** 속성에를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="d7a1d-118">In **Legend**, type `#PERCENT` for the **Custom legend text** property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7a1d-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d7a1d-119">See Also</span></span>  
 <span data-ttu-id="d7a1d-120">[원형 차트는 보고서 작성기 및 SSRS를 &#40;&#41;](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="d7a1d-120">[Pie Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="d7a1d-121">[차트의 범례 서식 지정 &#40;보고서 작성기 및 SSRS&#41;](chart-legend-formatting-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="d7a1d-121">[Formatting the Legend on a Chart &#40;Report Builder and SSRS&#41;](chart-legend-formatting-report-builder.md) </span></span>  
 <span data-ttu-id="d7a1d-122">[원형 차트 외부에 데이터 요소 레이블을 표시 하 고 보고서 작성기 및 SSRS를 &#40;&#41;](display-data-point-labels-outside-a-pie-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="d7a1d-122">[Display Data Point Labels Outside a Pie Chart &#40;Report Builder and SSRS&#41;](display-data-point-labels-outside-a-pie-chart-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="d7a1d-123">원형 차트에서 작은 조각 수집&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="d7a1d-123">Collect Small Slices on a Pie Chart &#40;Report Builder and SSRS&#41;</span></span>](collect-small-slices-on-a-pie-chart-report-builder-and-ssrs.md)  
  
  
