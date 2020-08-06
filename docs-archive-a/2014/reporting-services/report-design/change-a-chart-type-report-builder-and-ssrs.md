---
title: 차트 종류 변경(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: fff24978-e3bd-4fac-8cd7-d6aa81f3cc25
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: fb466bed475b27206bf6837a60d0867f5fb745be
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728047"
---
# <a name="change-a-chart-type-report-builder-and-ssrs"></a><span data-ttu-id="8c9bb-102">차트 종류 변경(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="8c9bb-102">Change a Chart Type (Report Builder and SSRS)</span></span>
  <span data-ttu-id="8c9bb-103">처음으로 보고서에 차트를 삽입하면 **차트 종류 선택** 대화 상자가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="8c9bb-103">When you first insert a chart into a report, the **Select Chart Type** dialog appears.</span></span> <span data-ttu-id="8c9bb-104">이 대화 상자를 취소하면 세로 막대형 차트가 기본적으로 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="8c9bb-104">If you cancel this dialog, a Column chart type is added by default.</span></span>  
  
 <span data-ttu-id="8c9bb-105">보고서를 디자인할 때 언제든지 보고서에 보다 적합한 종류로 차트를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8c9bb-105">At any point when designing the report, you can change the chart type to something more suitable to the report.</span></span> <span data-ttu-id="8c9bb-106">데이터가 올바르게 해석될 수 있도록 적합한 차트 종류를 선택하는 것이 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="8c9bb-106">It is important to select the correct chart type for your data so that it can be interpreted correctly.</span></span> <span data-ttu-id="8c9bb-107">데이터에 가장 적합한 차트 종류를 결정하려면 각 차트 종류의 특징을 이해해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8c9bb-107">You should understand each chart type's characteristics to determine what chart type is best suited for your data.</span></span> <span data-ttu-id="8c9bb-108">자세한 내용은 [차트 종류&#40;보고서 작성기 및 SSRS&#41;](chart-types-report-builder-and-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8c9bb-108">For more information, see [Chart Types &#40;Report Builder and SSRS&#41;](chart-types-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="8c9bb-109">차트에 여러 계열이 표시되는 경우 개별 계열의 차트 종류를 변경해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8c9bb-109">When multiple series are displayed on a chart, you may want to change the chart type of an individual series.</span></span> <span data-ttu-id="8c9bb-110">개별 계열의 차트 종류는 영역형 차트, 세로 막대형 차트, 꺾은선형 차트 또는 분산형 차트인 경우에만 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8c9bb-110">You can only change the chart type of an individual series if the chart type is Area, Column, Line, or Scatter.</span></span> <span data-ttu-id="8c9bb-111">다른 모든 차트 종류의 경우 차트의 모든 계열이 선택한 차트 종류로 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="8c9bb-111">For all other chart types, all series in your chart will be changed to the selected chart type.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-change-the-chart-type"></a><span data-ttu-id="8c9bb-112">차트 종류를 변경하려면</span><span class="sxs-lookup"><span data-stu-id="8c9bb-112">To change the chart type</span></span>  
  
1.  <span data-ttu-id="8c9bb-113">디자인 뷰에서 차트를 마우스 오른쪽 단추로 클릭한 다음 **차트 종류 변경**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8c9bb-113">In Design view, right-click the chart and then click **Change Chart Type**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="8c9bb-114">차트에 여러 계열이 있는 경우 차트가 아니라 변경하려는 계열을 마우스 오른쪽 단추로 클릭해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8c9bb-114">When there are multiple series on a chart, you must right-click on the series, not the chart, which you want to change.</span></span>  
  
2.  <span data-ttu-id="8c9bb-115">**차트 종류 선택** 대화 상자의 목록에서 차트 종류를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8c9bb-115">In the **SelectChart Type** dialog box, select a chart type from the list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c9bb-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8c9bb-116">See Also</span></span>  
 <span data-ttu-id="8c9bb-117">[차트&#40;보고서 작성기 및 SSRS&#41;](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="8c9bb-117">[Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="8c9bb-118">[계기&#40;보고서 작성기 및 SSRS&#41;](gauges-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="8c9bb-118">[Gauges &#40;Report Builder and SSRS&#41;](gauges-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="8c9bb-119">보고서에 차트 추가&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="8c9bb-119">Add a Chart to a Report &#40;Report Builder and SSRS&#41;</span></span>](add-a-chart-to-a-report-report-builder-and-ssrs.md)  
  
  
