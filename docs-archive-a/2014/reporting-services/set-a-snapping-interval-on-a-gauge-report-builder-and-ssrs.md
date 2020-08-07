---
title: 계기의 맞춤 간격 설정 (보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 0ece7297-6e2f-47fb-835d-b9e9cce53fe2
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: bdc2a621c4406791838d97e93f47cd32fa9d5f94
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734948"
---
# <a name="set-a-snapping-interval-on-a-gauge-report-builder-and-ssrs"></a><span data-ttu-id="f7479-102">계기의 맞춤 간격 설정(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="f7479-102">Set a Snapping Interval on a Gauge (Report Builder and SSRS)</span></span>
  <span data-ttu-id="f7479-103">맞춤 간격은 값이 반올림되는 배수를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="f7479-103">A snapping interval defines the multiple to which values are rounded.</span></span> <span data-ttu-id="f7479-104">기본적으로 계기는 데이터 창에서 지정한 필드의 정확한 값을 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="f7479-104">By default, the gauge will point to the exact value of the field you have specified in the data pane.</span></span> <span data-ttu-id="f7479-105">그러나 포인터가 미리 설정된 간격에 맞도록 정확한 값을 반올림하거나 내림할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7479-105">However, you may want to round the exact value up or down so that the pointer will snap to a preset interval.</span></span> <span data-ttu-id="f7479-106">예를 들어 계기의 값이 34.2이고 맞춤 간격을 5로 지정한 경우에는 계기 포인터는 35를 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="f7479-106">For example, if the value on your gauge is 34.2 and you specify a snapping interval of 5, the gauge pointer will point to 35.</span></span> <span data-ttu-id="f7479-107">계기의 값이 31.2이고 맞춤 간격을 5로 지정한 경우에는 계기 포인터가 30을 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="f7479-107">If the value on your gauge is 31.2 and you specify a snapping interval of 5, the gauge pointer will point to 30.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../includes/ssrbrddup-md.md)]  
  
### <a name="to-set-a-snapping-interval-on-a-gauge"></a><span data-ttu-id="f7479-108">계기의 맞춤 간격을 설정하려면</span><span class="sxs-lookup"><span data-stu-id="f7479-108">To set a snapping interval on a gauge</span></span>  
  
1.  <span data-ttu-id="f7479-109">계기의 숫자를 아무 곳이나 클릭하여 눈금을 강조 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="f7479-109">Click anywhere on the numbers of the gauge to highlight the scale.</span></span>  
  
2.  <span data-ttu-id="f7479-110">속성 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="f7479-110">Open the Properties pane.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f7479-111">속성 창이 표시 되지 않으면 **보기** 탭을 클릭 한 다음 **속성** 확인란을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7479-111">If you do not see the Properties pane, click the **View** tab and then select the **Properties** checkbox.</span></span>  
  
3.  <span data-ttu-id="f7479-112">**포인터** 속성에서 (...) 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7479-112">In the **Pointers** property, click the (...) button.</span></span> <span data-ttu-id="f7479-113">Pointer 컬렉션 편집기가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="f7479-113">The Pointer Collection Editor opens.</span></span>  
  
4.  <span data-ttu-id="f7479-114">**SnappingEnabled** 속성을로 설정 `True` 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7479-114">Set the **SnappingEnabled** property to `True`.</span></span>  
  
5.  <span data-ttu-id="f7479-115">맞춤 간격을 나타내는 값으로 **SnappingInterval** 을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7479-115">Set the **SnappingInterval** to a value that represents the snapping interval.</span></span> <span data-ttu-id="f7479-116">포인터가 지정한 값의 가장 근사한 반올림 배수로 맞춰집니다.</span><span class="sxs-lookup"><span data-stu-id="f7479-116">The pointer will be snapped to the nearest round multiple of the value that you have specified.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7479-117">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f7479-117">See Also</span></span>  
 <span data-ttu-id="f7479-118">[계기의 눈금 서식 지정 &#40;보고서 작성기 및 SSRS&#41;](report-design/formatting-scales-on-a-gauge-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="f7479-118">[Formatting Scales on a Gauge &#40;Report Builder and SSRS&#41;](report-design/formatting-scales-on-a-gauge-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="f7479-119">[계기 &#40;보고서 작성기 및 SSRS에 대 한 형식 지정&#41;](report-design/formatting-pointers-on-a-gauge-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="f7479-119">[Formatting Pointers on a Gauge &#40;Report Builder and SSRS&#41;](report-design/formatting-pointers-on-a-gauge-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="f7479-120">계기&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="f7479-120">Gauges &#40;Report Builder and SSRS&#41;</span></span>](report-design/gauges-report-builder-and-ssrs.md)  
  
  
