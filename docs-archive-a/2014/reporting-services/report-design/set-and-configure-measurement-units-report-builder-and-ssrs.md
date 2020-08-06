---
title: 단위 설정 및 구성(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: a15a96c3-7d2c-433e-a440-4ea051e967a9
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c01523dad9a96d2d45b96474d36873bac2484343
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639295"
---
# <a name="set-and-configure-measurement-units-report-builder-and-ssrs"></a><span data-ttu-id="c8eb0-102">단위 설정 및 구성(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="c8eb0-102">Set and Configure Measurement Units (Report Builder and SSRS)</span></span>
  <span data-ttu-id="c8eb0-103">표시기는 백분율과 숫자라는 두 가지 측정 단위를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="c8eb0-103">Indicators provide two measurement units: percentage and numeric.</span></span> <span data-ttu-id="c8eb0-104">표시기는 기본적으로 백분율을 단위로 사용하도록 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="c8eb0-104">By default, indicators are configured to use percentages as the measurement unit.</span></span> <span data-ttu-id="c8eb0-105">즉, 표시기 집합에서 각 아이콘에 할당되는 표시기 값은 백분율 범위로 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="c8eb0-105">This means that the indicator values assigned to each icon in the indicator set are determined by a percentage range.</span></span> <span data-ttu-id="c8eb0-106">백분율 범위는 표시기 집합의 아이콘에 대해 균등하게 분할됩니다.</span><span class="sxs-lookup"><span data-stu-id="c8eb0-106">The percentage ranges are evenly divided across the icons in the indicator set.</span></span> <span data-ttu-id="c8eb0-107">각 아이콘은 표시기 상태를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c8eb0-107">Each icon represents an indicator state.</span></span> <span data-ttu-id="c8eb0-108">다른 시작 백분율 및 끝 백분율을 지정하여 표시기 집합의 각 아이콘에 대한 백분율을 변경할 수 있습니다</span><span class="sxs-lookup"><span data-stu-id="c8eb0-108">You can change the percentages for each icon in the indicator set by specifying different start and end percentages.</span></span> <span data-ttu-id="c8eb0-109">또한 표시기는 데이터의 최소값 및 최대값을 자동으로 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="c8eb0-109">Indicators also automatically detect the minimum and maximum values in the data.</span></span>  
  
 <span data-ttu-id="c8eb0-110">측정 단위를 숫자 값이 되도록 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8eb0-110">You can change the measurement unit to be a numeric value.</span></span> <span data-ttu-id="c8eb0-111">이 경우에는 데이터의 최소값 및 최대값을 지정하지 않습니다. 대신 표시기에 사용되는 각 아이콘의 시작 값과 끝 값만 제공하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c8eb0-111">In this case, you do not specify minimum or maximum for the data; instead, you provide only the start and end values for each icon that the indicator uses.</span></span>  
  
 <span data-ttu-id="c8eb0-112">식을 사용하여 단위 등의 옵션을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8eb0-112">Options such as measurement units can be set by using expressions.</span></span> <span data-ttu-id="c8eb0-113">자세한 내용은 [식&#40;보고서 작성기 및 SSRS&#41;](expressions-report-builder-and-ssrs.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c8eb0-113">For more information, see [Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-use-the-numeric-state-measurement-unit"></a><span data-ttu-id="c8eb0-114">숫자 상태 단위를 사용하려면</span><span class="sxs-lookup"><span data-stu-id="c8eb0-114">To use the numeric state measurement unit</span></span>  
  
1.  <span data-ttu-id="c8eb0-115">변경할 표시기를 마우스 오른쪽 단추로 클릭하고 **표시기 속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c8eb0-115">Right-click the indicator you want to change and click **Indicator Properties**.</span></span>  
  
2.  <span data-ttu-id="c8eb0-116">왼쪽 창에서 **값 및 상태** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c8eb0-116">Click **Values and States** in the left pane.</span></span>  
  
3.  <span data-ttu-id="c8eb0-117">**상태 단위** 목록에서 **숫자**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c8eb0-117">In the **States Measurement Unit** list, click **Numeric**.</span></span>  
  
     <span data-ttu-id="c8eb0-118">필요한 경우 **식** (*fx*) 단추를 클릭하여 이 옵션의 값을 설정하는 식을 편집합니다.</span><span class="sxs-lookup"><span data-stu-id="c8eb0-118">Optionally, click the **Expression** (*fx*) button to edit an expression that sets the value of the option.</span></span>  
  
4.  <span data-ttu-id="c8eb0-119">표시기 집합의 각 아이콘에 대해 **시작** 및 **끝** 입력란의 값을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="c8eb0-119">For each icon in the indicator set, update the values in the **Start** and **End** text boxes.</span></span>  
  
     <span data-ttu-id="c8eb0-120">필요한 경우 **식** (*fx*) 단추를 클릭하여 **시작** 및 **끝** 옵션의 값을 설정하는 식을 편집합니다.</span><span class="sxs-lookup"><span data-stu-id="c8eb0-120">Optionally, click the **Expression** (*fx*) button to edit an expression that sets the values of the **Start** and **End** options.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c8eb0-121">**시작** 및 **끝** 입력란의 값은 숫자여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8eb0-121">The values in the **Start** and **End** text boxes must be numeric.</span></span>  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-use-the-percentage-measurement-unit"></a><span data-ttu-id="c8eb0-122">백분율 단위를 사용하려면</span><span class="sxs-lookup"><span data-stu-id="c8eb0-122">To use the percentage measurement unit</span></span>  
  
1.  <span data-ttu-id="c8eb0-123">변경할 표시기를 마우스 오른쪽 단추로 클릭하고 **표시기 속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c8eb0-123">Right-click the indicator you want to change and click **Indicator Properties**.</span></span>  
  
2.  <span data-ttu-id="c8eb0-124">왼쪽 창에서 **값 및 상태** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c8eb0-124">Click **Values and States** in the left pane.</span></span>  
  
3.  <span data-ttu-id="c8eb0-125">**상태 단위** 목록에서 **백분율**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c8eb0-125">In the **States Measurement Unit** list, click **Percentage**.</span></span>  
  
     <span data-ttu-id="c8eb0-126">필요한 경우 **식** (*fx*) 단추를 클릭하여 이 옵션의 값을 설정하는 식을 편집합니다.</span><span class="sxs-lookup"><span data-stu-id="c8eb0-126">Optionally, click the **Expression** (*fx*) button to edit an expression that sets the value of the option.</span></span>  
  
4.  <span data-ttu-id="c8eb0-127">필요한 경우 **최소값** 및 **최대값** 옵션을 변경하여 표시기가 사용하는 데이터의 최소값 및 최대값을 자동으로 검색하는 대신 특정 값을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="c8eb0-127">Optionally, change the **Minimum** and **Maximum** options to use specific values instead of automatically detecting the minimum and maximum values of the data that the indicator uses.</span></span> <span data-ttu-id="c8eb0-128">**최소값** 이 **최대값**보다 작아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8eb0-128">The value of **Minimum** must be smaller than the value of **Maximum**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c8eb0-129">최소값 및 최대값을 명시적으로 설정하는 경우 데이터의 실제 최소값 및 최대값에 관계없이 표시기에서 해당 값 범위를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="c8eb0-129">If you explicitly set minimum and maximum values, that value range is used by the indicator regardless of the actual the minimum and maximum values in the data.</span></span> <span data-ttu-id="c8eb0-130">즉, 최소값보다 작은 값과 최대값보다 큰 값은 보고서에 표시할 표시기 아이콘을 결정하는 평가에서 제외됩니다.</span><span class="sxs-lookup"><span data-stu-id="c8eb0-130">This means that values lower than the minimum and higher than the maximum are excluded from the evaluation that determine what indictor icon to show in the report.</span></span>  
  
     <span data-ttu-id="c8eb0-131">필요한 경우 **식** (*fx*) 단추를 클릭하여 이 옵션의 값을 설정하는 식을 편집합니다.</span><span class="sxs-lookup"><span data-stu-id="c8eb0-131">Optionally, click the **Expression** (*fx*) button to edit an expression that sets the values of the option.</span></span>  
  
5.  <span data-ttu-id="c8eb0-132">표시기 집합의 각 아이콘에 대해 **시작** 및 **끝** 입력란의 값을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="c8eb0-132">For each icon in the indicator set, update the values in the **Start** and **End** text boxes.</span></span>  
  
     <span data-ttu-id="c8eb0-133">필요한 경우 **식** (*fx*) 단추를 클릭하여 **시작** 및 **끝** 옵션의 값을 설정하는 식을 편집합니다.</span><span class="sxs-lookup"><span data-stu-id="c8eb0-133">Optionally, click the **Expression** (*fx*) button to edit an expression that sets the values of the **Start** and **End** options.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c8eb0-134">**시작** 및 **끝** 입력란의 값은 숫자여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8eb0-134">The values in the **Start** and **End** text boxes must be numeric.</span></span>  
  
6.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c8eb0-135">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c8eb0-135">See Also</span></span>  
 [<span data-ttu-id="c8eb0-136">표시기&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="c8eb0-136">Indicators &#40;Report Builder and SSRS&#41;</span></span>](indicators-report-builder-and-ssrs.md)  
  
  
