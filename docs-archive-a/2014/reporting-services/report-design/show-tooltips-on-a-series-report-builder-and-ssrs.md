---
title: 계열에 도구 설명 표시(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 4c9606ff-e1c3-4cf7-a4e7-bb16f1a9e8ab
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9113ec843b3b9255f380b17ee1ab6b360fa1f60d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659812"
---
# <a name="show-tooltips-on-a-series-report-builder-and-ssrs"></a><span data-ttu-id="19cbc-102">계열에 도구 설명 표시(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="19cbc-102">Show ToolTips on a Series (Report Builder and SSRS)</span></span>
  <span data-ttu-id="19cbc-103">차트에 있는 계열의 각 데이터 요소에 도구 설명을 추가하여 사용자가 렌더링된 보고서에서 데이터 요소 위로 마우스를 이동할 때 그룹 이름, 데이터 요소 값 또는 계열 합계에 대한 백분율 같은 데이터 요소에 대한 정보를 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19cbc-103">You can add a ToolTip to each data point on the series of a chart to display information related to the data point, such as the group name, the value of the data point, or the percentage of the data point relative to the series total when users hover over the data point in a rendered report.</span></span>  
  
 <span data-ttu-id="19cbc-104">계산된 계열에는 도구 설명을 추가할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="19cbc-104">You cannot add a ToolTip to a calculated series.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-specify-a-tooltip-on-each-data-point"></a><span data-ttu-id="19cbc-105">각 데이터 요소에 도구 설명을 지정하려면</span><span class="sxs-lookup"><span data-stu-id="19cbc-105">To specify a ToolTip on each data point</span></span>  
  
1.  <span data-ttu-id="19cbc-106">**값** 영역에 포함된 필드 또는 계열을 마우스 오른쪽 단추로 클릭하고 **계열 속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="19cbc-106">Right-click on the series or right-click on the field in the **Values** area, and click **Series Properties**.</span></span>  
  
2.  <span data-ttu-id="19cbc-107">**계열 데이터** 를 클릭하고 **도구 설명** 속성에서 문자열이나 식을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="19cbc-107">Click **Series Data** and, for the **ToolTip** property, type in a string or expression.</span></span> <span data-ttu-id="19cbc-108">차트 관련 키워드를 사용하여 차트의 다른 요소를 나타낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19cbc-108">You can use any chart-specific keyword to represent another element on the chart.</span></span> <span data-ttu-id="19cbc-109">자세한 내용은 [차트의 데이터 요소에 서식 지정&#40;보고서 작성기 및 SSRS&#41;](formatting-data-points-on-a-chart-report-builder-and-ssrs.md)을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="19cbc-109">For more information, see [Formatting Data Points on a Chart &#40;Report Builder and SSRS&#41;](formatting-data-points-on-a-chart-report-builder-and-ssrs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19cbc-110">참고 항목</span><span class="sxs-lookup"><span data-stu-id="19cbc-110">See Also</span></span>  
 <span data-ttu-id="19cbc-111">[차트의 데이터 요소에 서식 지정 &#40;보고서 작성기 및 SSRS&#41;](formatting-data-points-on-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="19cbc-111">[Formatting Data Points on a Chart &#40;Report Builder and SSRS&#41;](formatting-data-points-on-a-chart-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="19cbc-112">[범례 항목의 텍스트를 변경 &#40;보고서 작성기 및 SSRS&#41;](chart-legend-change-item-text-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="19cbc-112">[Change the Text of a Legend Item &#40;Report Builder and SSRS&#41;](chart-legend-change-item-text-report-builder.md) </span></span>  
 <span data-ttu-id="19cbc-113">[차트에서 계열 색 서식 지정 &#40;보고서 작성기 및 SSRS&#41;](formatting-series-colors-on-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="19cbc-113">[Formatting Series Colors on a Chart &#40;Report Builder and SSRS&#41;](formatting-series-colors-on-a-chart-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="19cbc-114">보고서에 드릴스루 동작 추가&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="19cbc-114">Add a Drillthrough Action on a Report &#40;Report Builder and SSRS&#41;</span></span>](add-a-drillthrough-action-on-a-report-report-builder-and-ssrs.md)  
  
  
