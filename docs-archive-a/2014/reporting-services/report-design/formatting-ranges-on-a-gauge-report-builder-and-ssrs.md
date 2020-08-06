---
title: 계기에서 범위 서식 지정(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: ffdec8ca-3e95-41cd-850b-9e8c83be4b49
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 29574c58eef6f18d685b48dd8d695a5fc42c3e6e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728007"
---
# <a name="formatting-ranges-on-a-gauge-report-builder-and-ssrs"></a><span data-ttu-id="b42f2-102">계기에서 범위 서식 지정(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="b42f2-102">Formatting Ranges on a Gauge (Report Builder and SSRS)</span></span>
  <span data-ttu-id="b42f2-103">계기 범위는 계기에서 값의 중요한 하위 섹션을 나타내는 계기 눈금의 영역입니다.</span><span class="sxs-lookup"><span data-stu-id="b42f2-103">A gauge range is a zone or area on the gauge scale that indicates an important subsection of values on the gauge.</span></span> <span data-ttu-id="b42f2-104">계기 범위를 사용하여 포인터 값이 특정 값 범위에 속하는지를 시각적으로 나타낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b42f2-104">Using a gauge range, you can visually indicate when the pointer value has gone into a certain span of values.</span></span> <span data-ttu-id="b42f2-105">범위는 시작 값과 끝 값으로 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="b42f2-105">Ranges are defined by a start value and an end value.</span></span>  
  
 <span data-ttu-id="b42f2-106">또한 범위를 사용하여 계기의 다양한 섹션도 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b42f2-106">You can also use ranges to define different sections of a gauge.</span></span> <span data-ttu-id="b42f2-107">예를 들어 값이 0에서 10까지인 계기에서는 값 0~3에 대해 빨간색 범위, 값 4~7에 대해 노란색 범위, 값 8~10에 대해 녹색 범위를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b42f2-107">For example, on a gauge with values from 0 to 10, you can define a red range that has a value from 0 to 3, a yellow range that has a value from 4 to 7 and a green range that has a value from 8 to 10.</span></span> <span data-ttu-id="b42f2-108">지정한 시작 값이 지정한 끝 값보다 크면 값이 서로 바뀌어서 시작 값이 끝 값이 되고 끝 값이 시작 값이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b42f2-108">If the start value that you specified is greater than the end value that you specified, the values are swapped so that the start value is the end value and the end value is the start value.</span></span>  
  
 <span data-ttu-id="b42f2-109">눈금에서 포인터 위치를 정하는 것과 같은 방법으로 범위의 위치를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b42f2-109">You can position the range in the same way that you position pointers on a scale.</span></span> <span data-ttu-id="b42f2-110">**위치** 및 **눈금에서의 거리** 속성에 따라 범위의 위치가 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="b42f2-110">The **Position** and **Distance from scale** properties determine the position of the range.</span></span> <span data-ttu-id="b42f2-111">자세한 내용은 [계기&#40;보고서 작성기 및 SSRS&#41;](gauges-report-builder-and-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b42f2-111">For more information, see [Gauges &#40;Report Builder and SSRS&#41;](gauges-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b42f2-112">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b42f2-112">See Also</span></span>  
 <span data-ttu-id="b42f2-113">[계기의 눈금 서식 지정&#40;보고서 작성기 및 SSRS&#41;](formatting-scales-on-a-gauge-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="b42f2-113">[Formatting Scales on a Gauge &#40;Report Builder and SSRS&#41;](formatting-scales-on-a-gauge-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="b42f2-114">[계기의 포인터 서식 지정&#40;보고서 작성기 및 SSRS&#41;](formatting-pointers-on-a-gauge-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="b42f2-114">[Formatting Pointers on a Gauge &#40;Report Builder and SSRS&#41;](formatting-pointers-on-a-gauge-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="b42f2-115">[계기의 최소값 또는 최대값 설정&#40;보고서 작성기 및 SSRS&#41;](set-a-minimum-or-maximum-on-a-gauge-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="b42f2-115">[Set a Minimum or Maximum on a Gauge &#40;Report Builder and SSRS&#41;](set-a-minimum-or-maximum-on-a-gauge-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="b42f2-116">[자습서: 보고서에 KPI 추가&#40;보고서 작성기&#41;](../tutorial-adding-a-kpi-to-your-report-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="b42f2-116">[Tutorial: Adding a KPI to Your Report &#40;Report Builder&#41;](../tutorial-adding-a-kpi-to-your-report-report-builder.md) </span></span>  
 [<span data-ttu-id="b42f2-117">계기&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="b42f2-117">Gauges &#40;Report Builder and SSRS&#41;</span></span>](gauges-report-builder-and-ssrs.md)  
  
  
