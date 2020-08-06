---
title: 계기의 최소값 또는 최대값 설정(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: b4c260c0-5a88-4f30-8977-eb5cc78fc146
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 344122dbff647a8c35b838ecce637602f202864b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647435"
---
# <a name="set-a-minimum-or-maximum-on-a-gauge-report-builder-and-ssrs"></a><span data-ttu-id="b1df2-102">계기의 최소값 또는 최대값 설정(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="b1df2-102">Set a Minimum or Maximum on a Gauge (Report Builder and SSRS)</span></span>
  <span data-ttu-id="b1df2-103">여러 그룹이 정의되는 차트와 달리 계기에는 하나의 값만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b1df2-103">Unlike the chart, where multiple groups are defined, the gauge only shows one value.</span></span> <span data-ttu-id="b1df2-104">보고서 작성기 및 보고서 디자이너에서 사용자가 계기에 표시하려고 하는 한 값의 컨텍스트 또는 상대적 중요도를 확인하므로 사용자가 눈금의 최소값 및 최대값을 정의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1df2-104">Since Report Builder and Report Designer determine the context or relative significance of the one value that you are trying to show on the gauge, you must define the minimum and maximum of the scale.</span></span> <span data-ttu-id="b1df2-105">예를 들어 데이터 값이 0과 10 사이의 순위인 경우에는 대개 최소값과 최대값을 각각 0과 10으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="b1df2-105">For example, if your data values are rankings between 0 and 10, you will want to set the minimum to 0 and maximum to 10.</span></span> <span data-ttu-id="b1df2-106">간격 수는 최소값과 최대값으로 지정된 값을 기반으로 자동으로 계산됩니다.</span><span class="sxs-lookup"><span data-stu-id="b1df2-106">The interval numbers are calculated automatically based on the values specified for the minimum and maximum.</span></span> <span data-ttu-id="b1df2-107">기본적으로 최소값과 최대값은 0과 100으로 설정되지만 이러한 값은 임의의 값이므로 사용자가 변경해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1df2-107">By default, the minimum and maximum are set to 0 and 100, but this is an arbitrary value that you should change.</span></span> <span data-ttu-id="b1df2-108">애플리케이션에서는 값을 백분율로 계산하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b1df2-108">The application does not calculate your value as a percentage.</span></span>  
  
 <span data-ttu-id="b1df2-109">0부터 10000까지와 같이 값 범위가 큰 경우에는 승수를 사용하여 계기에서 0의 개수를 줄이는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="b1df2-109">If the range of your values is large, for example from 0 to 10000, consider using a multiplier to reduce the number of zeroes on the gauge.</span></span> <span data-ttu-id="b1df2-110">승수를 사용하면 계기의 숫자 크기가 줄어들 뿐 값 자체는 줄어들지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b1df2-110">The multiplier will only reduce the scale of the numbers on the gauge, not the value itself.</span></span>  
  
 <span data-ttu-id="b1df2-111">식을 사용하여 **최소값** 및 **최대값** 옵션의 값을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1df2-111">You can use expressions to set the values of the **Minimum** and **Maximum** options.</span></span> <span data-ttu-id="b1df2-112">자세한 내용은 [식&#40;보고서 작성기 및 SSRS&#41;](expressions-report-builder-and-ssrs.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b1df2-112">For more information, see [Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-set-the-minimum-and-maximum-on-the-gauge"></a><span data-ttu-id="b1df2-113">계기의 최소값 및 최대값을 설정하려면</span><span class="sxs-lookup"><span data-stu-id="b1df2-113">To set the minimum and maximum on the gauge</span></span>  
  
1.  <span data-ttu-id="b1df2-114">눈금을 마우스 오른쪽 단추로 클릭하고 **눈금 속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b1df2-114">Right-click on the scale and select **Scale Properties**.</span></span> <span data-ttu-id="b1df2-115">**눈금 속성** 대화 상자가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="b1df2-115">The **Scale Properties** dialog box appears.</span></span>  
  
2.  <span data-ttu-id="b1df2-116">**일반**에서 **최소값**의 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b1df2-116">In **General**, specify a value for **Minimum**.</span></span> <span data-ttu-id="b1df2-117">기본적으로 이 값은 0입니다.</span><span class="sxs-lookup"><span data-stu-id="b1df2-117">By default, this value is 0.</span></span> <span data-ttu-id="b1df2-118">필요한 경우 **식** (*fx*) 단추를 클릭하여 이 옵션의 값을 설정하는 식을 편집합니다.</span><span class="sxs-lookup"><span data-stu-id="b1df2-118">Optionally, click the **Expression** (*fx*) button to edit the expression that sets the value of the option.</span></span>  
  
3.  <span data-ttu-id="b1df2-119">**최대값**의 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b1df2-119">Specify a value for **Maximum**.</span></span> <span data-ttu-id="b1df2-120">기본적으로 이 값은 100입니다.</span><span class="sxs-lookup"><span data-stu-id="b1df2-120">By default, this value is 100.</span></span> <span data-ttu-id="b1df2-121">필요한 경우 **식** (*fx*) 단추를 클릭하여 이 옵션의 값을 설정하는 식을 편집합니다.</span><span class="sxs-lookup"><span data-stu-id="b1df2-121">Optionally, click the **Expression** (*fx*) button to edit the expression that sets the value of the option.</span></span>  
  
4.  <span data-ttu-id="b1df2-122">(옵션) 최소값 및 최대값이 큰 경우 **눈금 레이블 곱하기** 옵션의 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b1df2-122">(Optional) If the values for your minimum and maximum are large, specify a value for the **Multiply scale labels by** option.</span></span> <span data-ttu-id="b1df2-123">눈금을 줄이는 승수를 지정하려면 10진수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b1df2-123">To specify a multiplier that reduces your scale, use a decimal number.</span></span> <span data-ttu-id="b1df2-124">예를 들어 눈금이 0에서 1000 사이인 경우 승수 값을 0.01로 지정하면 눈금이 줄어 0에서 10 사이로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b1df2-124">For example, if you have a scale from 0 to 1000, you can specify a multiplier value of 0.01 to reduce the scale to read 0 to 10.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1df2-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b1df2-125">See Also</span></span>  
 <span data-ttu-id="b1df2-126">[계기의 눈금 서식 지정&#40;보고서 작성기 및 SSRS&#41;](formatting-scales-on-a-gauge-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="b1df2-126">[Formatting Scales on a Gauge &#40;Report Builder and SSRS&#41;](formatting-scales-on-a-gauge-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="b1df2-127">[계기의 포인터 서식 지정&#40;보고서 작성기 및 SSRS&#41;](formatting-pointers-on-a-gauge-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="b1df2-127">[Formatting Pointers on a Gauge &#40;Report Builder and SSRS&#41;](formatting-pointers-on-a-gauge-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="b1df2-128">계기&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="b1df2-128">Gauges &#40;Report Builder and SSRS&#41;</span></span>](gauges-report-builder-and-ssrs.md)  
  
  
