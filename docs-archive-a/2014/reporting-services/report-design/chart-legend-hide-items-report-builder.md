---
title: 차트에서 범례 항목 숨기기(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 92256240-0cd5-4be4-8904-d1e3b93cb6b3
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 20444432f580ffaf1c5f4de1320b06319f973a01
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659825"
---
# <a name="hide-legend-items-on-the-chart-report-builder-and-ssrs"></a><span data-ttu-id="aa12c-102">차트에서 범례 항목 숨기기(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="aa12c-102">Hide Legend Items on the Chart (Report Builder and SSRS)</span></span>
  <span data-ttu-id="aa12c-103">기본적으로 셰이프 차트가 아닌 차트에 추가된 모든 계열은 범례에서 항목으로 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa12c-103">By default, any series added to a non-Shape chart will be added as an item in the legend.</span></span> <span data-ttu-id="aa12c-104">원형, 도넛형, 깔때기형 및 피라미드형 차트의 경우 차트에 계열을 추가하면 범례에 개별 데이터 요소가 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa12c-104">For pie, doughnut, funnel, and pyramid charts, any series added to the chart will add individual data points in the legend.</span></span>  
  
 <span data-ttu-id="aa12c-105">범례에서 모든 항목을 숨길 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa12c-105">You can hide any item on the legend.</span></span> <span data-ttu-id="aa12c-106">범례 항목을 숨기더라도 차트에는 계속 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="aa12c-106">When you hide a legend item, it will still appear in the chart.</span></span> <span data-ttu-id="aa12c-107">이 기능은 차트에 추가된 계열에 대한 자세한 정보를 표시하지 않으려는 경우에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="aa12c-107">This is useful in situations where you do not want to show more information for a series that is added to the chart.</span></span> <span data-ttu-id="aa12c-108">예를 들어 이동 평균과 같은 계산된 계열을 차트에 추가한 경우 원래 계열에 대해서만 자세한 정보가 표시되도록 이 항목을 범례에서 숨길 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa12c-108">For example, if you have added a calculated series like a moving average to the chart, you may want to hide this entry in the legend so that more information is only shown for the original series.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-hide-an-item-from-display-in-the-legend"></a><span data-ttu-id="aa12c-109">범례에서 항목을 숨기려면</span><span class="sxs-lookup"><span data-stu-id="aa12c-109">To hide an item from display in the legend</span></span>  
  
1.  <span data-ttu-id="aa12c-110">숨기려는 계열을 마우스 오른쪽 단추로 클릭하고 **계열 속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="aa12c-110">Right-click on the series you want to hide and select **Series Properties**.</span></span>  
  
2.  <span data-ttu-id="aa12c-111">**범례**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="aa12c-111">Click **Legend**.</span></span> <span data-ttu-id="aa12c-112">**범례에 이 계열 표시 안 함** 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="aa12c-112">Select the **Do not show this series in a legend** option.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="aa12c-113">한 그룹에서 계열을 숨기고 다른 그룹에서는 표시하는 기능은 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="aa12c-113">You cannot hide a series for one group and not for the others.</span></span> <span data-ttu-id="aa12c-114">**계열 그룹** 영역에 필드를 추가하면 해당 그룹에 속한 모든 계열이 숨겨집니다.</span><span class="sxs-lookup"><span data-stu-id="aa12c-114">If you have added a field to the **Series Groups** area, all series belonging to this group will be hidden.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa12c-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="aa12c-115">See Also</span></span>  
 <span data-ttu-id="aa12c-116">[차트의 범례 서식 지정&#40;보고서 작성기 및 SSRS&#41;](chart-legend-formatting-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="aa12c-116">[Formatting the Legend on a Chart &#40;Report Builder and SSRS&#41;](chart-legend-formatting-report-builder.md) </span></span>  
 <span data-ttu-id="aa12c-117">[차트의 데이터 요소에 서식 지정&#40;보고서 작성기 및 SSRS&#41;](formatting-data-points-on-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="aa12c-117">[Formatting Data Points on a Chart &#40;Report Builder and SSRS&#41;](formatting-data-points-on-a-chart-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="aa12c-118">[범례 항목의 텍스트 변경&#40;보고서 작성기 및 SSRS&#41;](chart-legend-change-item-text-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="aa12c-118">[Change the Text of a Legend Item &#40;Report Builder and SSRS&#41;](chart-legend-change-item-text-report-builder.md) </span></span>  
 <span data-ttu-id="aa12c-119">[차트에 이동 평균 추가&#40;보고서 작성기 및 SSRS&#41;](add-a-moving-average-to-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="aa12c-119">[Add a Moving Average to a Chart &#40;Report Builder and SSRS&#41;](add-a-moving-average-to-a-chart-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="aa12c-120">범례 속성 대화 상자, 일반&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="aa12c-120">Legend Properties Dialog Box, General &#40;Report Builder and SSRS&#41;</span></span>](../legend-properties-dialog-box-general-report-builder-and-ssrs.md)  
  
  
