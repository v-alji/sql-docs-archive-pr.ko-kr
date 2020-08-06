---
title: 식을 사용하여 표시기 크기 지정(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: ab0b86f1-4882-4258-a2b6-c612faecfa4b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b450abb957329b8dbaa4f7f0e4c963c5f63f06b3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639272"
---
# <a name="specify-the-size-of-an-indicator-using-an-expression-report-builder-and-ssrs"></a><span data-ttu-id="587ef-102">식을 사용하여 표시기 크기 지정(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="587ef-102">Specify the Size of an Indicator Using an Expression (Report Builder and SSRS)</span></span>
  <span data-ttu-id="587ef-103">색, 방향 및 모양 외에 크기도 표시기의 시각적 효과를 최대화하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="587ef-103">In addition to color, direction, and shape, you can use size to maximize the visual impact of indicators.</span></span>  
  
 <span data-ttu-id="587ef-104">표시기에는 IndicatorStates라는 표시기 상태 컬렉션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="587ef-104">An indicator has a collection of indicator states named IndicatorStates.</span></span> <span data-ttu-id="587ef-105">일반적으로 IndicatorStates 컬렉션에는 여러 상태가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="587ef-105">The IndicatorStates collection typically have multiple states.</span></span> <span data-ttu-id="587ef-106">각 상태는 컬렉션의 멤버이며 아이콘으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="587ef-106">Each state is a member of the collection and is represented by an icon.</span></span> <span data-ttu-id="587ef-107">이러한 상태가 함께 IndicatorsStates 컬렉션을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="587ef-107">Together the states constitute the IndicatorsStates collection.</span></span>  
  
 <span data-ttu-id="587ef-108">아이콘 크기를 동적으로 구성하려면 보고서 작성기의 속성 창에서 IndicatorsStates 컬렉션 멤버의 속성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="587ef-108">To dynamically configure the sizes of icons, you set properties of members of the IndicatorsStates collection in the Properties pane of Report Builder.</span></span> <span data-ttu-id="587ef-109">**속성** 창이 표시되지 않으면 **보기** 탭을 클릭하고 **속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="587ef-109">If the **Properties** pane is not visible, click the **View** tab and select **Properties**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="587ef-110">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]에서는 **속성** 창을 사용하여 멤버 속성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="587ef-110">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], you use the **Properties** window to set the member properties.</span></span> <span data-ttu-id="587ef-111">**속성** 창이 열리지 않으면 F4 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="587ef-111">If the **Properties** window is not open, press the F4 key.</span></span>  
  
 <span data-ttu-id="587ef-112">**속성** 창에서 표시기의 IndicatorStates 컬렉션 속성에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="587ef-112">The **Properties** pane provides access to the properties of the IndicatorStates collection of an indicator.</span></span> <span data-ttu-id="587ef-113">아이콘을 다양한 크기로 구성하려면 식을 사용하여 IndicatorStates 컬렉션 멤버의 ScaleFactor 속성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="587ef-113">You configure the icons to be different sizes by setting the ScaleFactor property of the IndicatorStates collection members using an expression.</span></span> <span data-ttu-id="587ef-114">자세한 내용은 [식&#40;보고서 작성기 및 SSRS&#41;](expressions-report-builder-and-ssrs.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="587ef-114">For more information, see [Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="587ef-115">이 절차에서 사용된 식이 [표시기&#40;보고서 작성기 및 SSRS&#41;](indicators-report-builder-and-ssrs.md)을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="587ef-115">The expression used in this procedure was also used to generate the report with different sizes of indicators, shown in [Indicators &#40;Report Builder and SSRS&#41;](indicators-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-specify-the-indicator-icon-size-using-an-expression"></a><span data-ttu-id="587ef-116">식을 사용하여 표시기 아이콘 크기를 지정하려면</span><span class="sxs-lookup"><span data-stu-id="587ef-116">To specify the indicator icon size using an expression</span></span>  
  
1.  <span data-ttu-id="587ef-117">변경할 표시기를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="587ef-117">Click the indicator you want to change.</span></span>  
  
2.  <span data-ttu-id="587ef-118">속성 창에서 IndicatorStates 속성을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="587ef-118">In the Properties pane, locate the IndicatorStates property.</span></span>  
  
     <span data-ttu-id="587ef-119">속성 창이 범주별로 구성된 경우 IndicatorStates는 **상태** 범주에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="587ef-119">If the Properties pane is organized by category, you will find IndicatorStates in the **States** category.</span></span>  
  
3.  <span data-ttu-id="587ef-120">IndicatorStates 옆에 있는 줄임표 **(...)** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="587ef-120">Click the ellipsis **(...)** button next to IndicatorStates.</span></span> <span data-ttu-id="587ef-121">**IndicatorState 컬렉션 편집기** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="587ef-121">The **IndicatorState Collection Editor** dialog box opens.</span></span>  
  
     <span data-ttu-id="587ef-122">컬렉션 멤버를 모두 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="587ef-122">Select all members of the collection.</span></span>  
  
4.  <span data-ttu-id="587ef-123">**다중 선택 속성** 목록에서 ScaleFactor 옆의 아래쪽 화살표를 클릭하고 **식**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="587ef-123">In the **Multi-Select Properties** list, click the down arrow next to ScaleFactor and then click **Expression**.</span></span>  
  
5.  <span data-ttu-id="587ef-124">**식** 대화 상자에서 식을 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="587ef-124">In the **Expression** dialog box write the expression.</span></span>  
  
     <span data-ttu-id="587ef-125">다음 예제 식은 **SalesYTD** 필드의 값을 기준으로 아이콘을 다른 크기로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="587ef-125">The following sample expression makes the icon a different size based on the value of the **SalesYTD** field.</span></span>  
  
     `=IIF(Fields!SalesYTD.value = 0,0,Fields!SalesYTD.value/Max(Fields!SalesYTD.value,"Indicator"))`  
  
     <span data-ttu-id="587ef-126">자세한 내용은 [식 예&#40;보고서 작성기 및 SSRS&#41;](expression-examples-report-builder-and-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="587ef-126">For more information, see [Expression Examples &#40;Report Builder and SSRS&#41;](expression-examples-report-builder-and-ssrs.md).</span></span>  
  
6.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="587ef-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="587ef-127">See Also</span></span>  
 [<span data-ttu-id="587ef-128">표시기&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="587ef-128">Indicators &#40;Report Builder and SSRS&#41;</span></span>](indicators-report-builder-and-ssrs.md)  
  
  
