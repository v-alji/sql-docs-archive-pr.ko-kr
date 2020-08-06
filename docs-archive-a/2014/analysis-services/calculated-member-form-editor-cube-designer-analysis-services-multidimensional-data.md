---
title: 계산 멤버 폼 편집기 (계산 탭, 큐브 디자이너) (Analysis Services 다차원 데이터) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.calculationexpression.calculatedmember.f1
ms.assetid: f7719b9e-b1e6-4792-90a6-30d9d8eb1196
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9dd45ece03fd81e0e7356e7bdcd0ec8dc53287bb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648088"
---
# <a name="calculated-member-form-editor-calculations-tab-cube-designer-analysis-services---multidimensional-data"></a><span data-ttu-id="76cfe-102">계산 멤버 폼 편집기(계산 탭, 큐브 디자이너)(Analysis Services - 다차원 데이터)</span><span class="sxs-lookup"><span data-stu-id="76cfe-102">Calculated Member Form Editor (Calculations Tab, Cube Designer) (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="76cfe-103">큐브 디자이너의 **계산** 탭에 있는 **계산 멤버 폼 편집기** 창을 사용하여 계산 멤버를 만들거나 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76cfe-103">Use the **Calculated Member Form Editor** pane on the **Calculations** tab in Cube Designer to create or modify a calculated member.</span></span>  
  
 <span data-ttu-id="76cfe-104">**참고** 이 창은 폼 보기에만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="76cfe-104">**Note** This pane is displayed only in form view.</span></span>  
  
## <a name="options"></a><span data-ttu-id="76cfe-105">옵션</span><span class="sxs-lookup"><span data-stu-id="76cfe-105">Options</span></span>  
 <span data-ttu-id="76cfe-106">**이름**</span><span class="sxs-lookup"><span data-stu-id="76cfe-106">**Name**</span></span>  
 <span data-ttu-id="76cfe-107">계산 멤버의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="76cfe-107">Type the name of the calculated member.</span></span>  
  
 <span data-ttu-id="76cfe-108">**부모 속성**</span><span class="sxs-lookup"><span data-stu-id="76cfe-108">**Parent Properties**</span></span>  
 <span data-ttu-id="76cfe-109">**부모 계층**, **부모 멤버**및 **변경** 옵션을 보려면 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="76cfe-109">Expand to view the **Parent hierarchy**, **Parent member**, and **Change** options.</span></span>  
  
 <span data-ttu-id="76cfe-110">**부모 계층**</span><span class="sxs-lookup"><span data-stu-id="76cfe-110">**Parent hierarchy**</span></span>  
 <span data-ttu-id="76cfe-111">선택한 큐브에서 계산 멤버를 포함할 차원 및 계층을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="76cfe-111">Select the dimension and hierarchy in the selected cube that is to include the calculated member.</span></span> <span data-ttu-id="76cfe-112">계산 측정값을 정의하려면 MEASURES를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="76cfe-112">Select MEASURES to define a calculated measure.</span></span>  
  
 <span data-ttu-id="76cfe-113">**부모 멤버**</span><span class="sxs-lookup"><span data-stu-id="76cfe-113">**Parent member**</span></span>  
 <span data-ttu-id="76cfe-114">계산 멤버 위에 나타낼 멤버를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="76cfe-114">Select the member beneath which the calculated member is to appear.</span></span>  
  
 <span data-ttu-id="76cfe-115">**참고** 이 옵션은 **부모 계층** 이 MEASURES 이외의 계층을 지정하는 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76cfe-115">**Note** This option is available if **Parent hierarchy** specifies a hierarchy other than MEASURES.</span></span>  
  
 <span data-ttu-id="76cfe-116">**변경**</span><span class="sxs-lookup"><span data-stu-id="76cfe-116">**Change**</span></span>  
 <span data-ttu-id="76cfe-117">**부모 멤버 선택** 대화 상자를 표시하여 **부모 멤버**에 대한 멤버를 선택하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="76cfe-117">Select to display the **Select Parent Member** dialog box and choose a member for **Parent member**.</span></span> <span data-ttu-id="76cfe-118">**부모 멤버 선택** 대화 상자에 대한 자세한 내용은 [부모 멤버 선택 대화 상자&#40;Analysis Services - 다차원 데이터&#41;](select-parent-member-dialog-box-analysis-services-multidimensional-data.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="76cfe-118">For more information about the **Select Parent Member** dialog box, see [Select Parent Member Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](select-parent-member-dialog-box-analysis-services-multidimensional-data.md).</span></span>  
  
 <span data-ttu-id="76cfe-119">**식**</span><span class="sxs-lookup"><span data-stu-id="76cfe-119">**Expression**</span></span>  
 <span data-ttu-id="76cfe-120">계산 멤버에 대한 MDX(Multidimensional Expression) 식을 보거나 편집하려면 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="76cfe-120">Expand to view or edit the Multidimensional Expressions (MDX) expression for the calculated member.</span></span>  
  
 <span data-ttu-id="76cfe-121">**계산 도구** 창에서 선택한 요소를 이 옵션으로 끌어서 놓으면 선택한 요소의 MDX 구문을 포함시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76cfe-121">Drag selected elements from the **Calculation Tools** pane to this option to include the MDX syntax for the selected element.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="76cfe-122">이 식은 문자열 또는 숫자 값으로 계산되는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="76cfe-122">It is recommended that this expression evaluate to a string or to a numeric value.</span></span>  
  
 <span data-ttu-id="76cfe-123">**추가 속성**</span><span class="sxs-lookup"><span data-stu-id="76cfe-123">**Additional Properties**</span></span>  
 <span data-ttu-id="76cfe-124">**형식 문자열**, **표시**, **비어 있지 않은 동작**, **색 식**및 **글꼴 식** 옵션을 보려면 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="76cfe-124">Expand to view the **Format string**, **Visible**, **Non-empty behavior**, **Color Expressions**, and **Font Expressions** options.</span></span>  
  
 <span data-ttu-id="76cfe-125">**형식 문자열**</span><span class="sxs-lookup"><span data-stu-id="76cfe-125">**Format string**</span></span>  
 <span data-ttu-id="76cfe-126">계산 멤버가 반환한 값의 형식을 지정하는 데 사용되는 MDX 형식 문자열을 입력하거나 미리 정의된 형식 문자열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="76cfe-126">Type the MDX format string used to format the value returned by the calculated member, or select a predefined format string.</span></span>  
  
 <span data-ttu-id="76cfe-127">MDX 형식 문자열에 대한 자세한 내용은 [FORMAT_STRING 내용&#40;MDX&#41;](multidimensional-models/mdx/mdx-cell-properties-format-string-contents.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="76cfe-127">For more information about MDX format strings, see [FORMAT_STRING Contents &#40;MDX&#41;](multidimensional-models/mdx/mdx-cell-properties-format-string-contents.md).</span></span>  
  
 <span data-ttu-id="76cfe-128">**표시**</span><span class="sxs-lookup"><span data-stu-id="76cfe-128">**Visible**</span></span>  
 <span data-ttu-id="76cfe-129">계산 멤버를 클라이언트 애플리케이션에 표시하려면 **True** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="76cfe-129">Select **True** to allow the calculated member to be visible to client applications.</span></span>  
  
 <span data-ttu-id="76cfe-130">**비어 있지 않은 동작**</span><span class="sxs-lookup"><span data-stu-id="76cfe-130">**Non-empty behavior**</span></span>  
 <span data-ttu-id="76cfe-131">계산 멤버에 대해 MDX로 NON EMPTY 쿼리를 해결하는 데 사용하는 측정값의 이름을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="76cfe-131">Select the name of the measure used to resolve NON EMPTY queries in MDX for the calculated member.</span></span> <span data-ttu-id="76cfe-132">**비어 있지 않은 동작** 속성이 비어 있는 경우 계산 멤버를 반복적으로 계산하여 멤버가 비어 있는지 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="76cfe-132">If the **Non Empty Behavior** property is blank, the calculated member must be evaluated repeatedly to determine if a member is empty.</span></span> <span data-ttu-id="76cfe-133">**비어 있지 않은 동작** 속성에 측정값의 이름이 있는 경우 지정한 측정값이 비어 있으면 계산 멤버도 비어 있는 것으로 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="76cfe-133">If the **Non Empty Behavior** property contains the name of a measure, the calculated member is treated as empty if the specified measure is empty.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="76cfe-134">이 속성은 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="76cfe-134">This property is deprecated.</span></span> <span data-ttu-id="76cfe-135">이 속성을 설정하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="76cfe-135">Avoid setting it.</span></span> <span data-ttu-id="76cfe-136">자세한 내용은 [SQL Server 2014에서 사용 되지 않는 Analysis Services 기능](deprecated-analysis-services-features-in-sql-server-2014.md) 을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="76cfe-136">See [Deprecated Analysis Services Features in SQL Server 2014](deprecated-analysis-services-features-in-sql-server-2014.md) for details.</span></span>  
  
 <span data-ttu-id="76cfe-137">**색 식**</span><span class="sxs-lookup"><span data-stu-id="76cfe-137">**Color Expressions**</span></span>  
 <span data-ttu-id="76cfe-138">**전경색** 및 **배경색** 옵션을 보려면 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="76cfe-138">Expand to view the **Fore color** and **Back color** options.</span></span>  
  
 <span data-ttu-id="76cfe-139">**전경색**</span><span class="sxs-lookup"><span data-stu-id="76cfe-139">**Fore color**</span></span>  
 <span data-ttu-id="76cfe-140">계산 멤버의 전경색을 지정하는 MDX 식을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="76cfe-140">Type the MDX expression that provides the foreground color of the calculated member.</span></span>  
  
 <span data-ttu-id="76cfe-141">**계산 도구** 창에서 선택한 요소를 이 옵션으로 끌어서 놓으면 선택한 요소의 MDX 구문을 포함시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76cfe-141">Drag selected elements from the **Calculation Tools** pane to this option to include the MDX syntax for the selected element.</span></span>  
  
 <span data-ttu-id="76cfe-142">색 선택 단추를 클릭하여 **색** 대화 상자를 표시하고 지정한 색의 RGB(Red-Green-Blue) 값을 MDX 식에 삽입할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76cfe-142">Click the color selection button to display the **Color** dialog box and insert the RGB (Red-Green-Blue) value for a specified color into the MDX expression.</span></span> <span data-ttu-id="76cfe-143">RGB 값에 대한 자세한 내용은 [FORE_COLOR 및 BACK_COLOR 내용&#40;MDX&#41;](multidimensional-models/mdx/mdx-cell-properties-fore-color-and-back-color-contents.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="76cfe-143">For more information about RGB values, see [FORE_COLOR and BACK_COLOR Contents &#40;MDX&#41;](multidimensional-models/mdx/mdx-cell-properties-fore-color-and-back-color-contents.md).</span></span>  
  
 <span data-ttu-id="76cfe-144">**배경색**</span><span class="sxs-lookup"><span data-stu-id="76cfe-144">**Back color**</span></span>  
 <span data-ttu-id="76cfe-145">계산 멤버의 배경색을 지정하는 MDX 식을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="76cfe-145">Type the MDX expression that provides the background color of the calculated member.</span></span>  
  
 <span data-ttu-id="76cfe-146">**계산 도구** 창에서 선택한 요소를 이 옵션으로 끌어서 놓으면 선택한 요소의 MDX 구문을 포함시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76cfe-146">Drag selected elements from the **Calculation Tools** pane to this option to include the MDX syntax for the selected element.</span></span>  
  
 <span data-ttu-id="76cfe-147">색 선택 단추를 클릭하여 **색** 대화 상자를 표시하고 지정한 색의 RGB(Red-Green-Blue) 값을 MDX 식에 삽입할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76cfe-147">Click the color selection button to display the **Color** dialog box and insert the RGB (Red-Green-Blue) value for a specified color into the MDX expression.</span></span> <span data-ttu-id="76cfe-148">RGB 값에 대한 자세한 내용은 [FORE_COLOR 및 BACK_COLOR 내용&#40;MDX&#41;](multidimensional-models/mdx/mdx-cell-properties-fore-color-and-back-color-contents.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="76cfe-148">For more information about RGB values, see [FORE_COLOR and BACK_COLOR Contents &#40;MDX&#41;](multidimensional-models/mdx/mdx-cell-properties-fore-color-and-back-color-contents.md).</span></span>  
  
 <span data-ttu-id="76cfe-149">**글꼴 식**</span><span class="sxs-lookup"><span data-stu-id="76cfe-149">**Font Expressions**</span></span>  
 <span data-ttu-id="76cfe-150">**글꼴 이름**, **글꼴 크기**및 **글꼴 플래그** 옵션을 보려면 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="76cfe-150">Expand to view the **Font name**, **Font size**, and **Font flags** options.</span></span>  
  
 <span data-ttu-id="76cfe-151">**글꼴 이름**</span><span class="sxs-lookup"><span data-stu-id="76cfe-151">**Font name**</span></span>  
 <span data-ttu-id="76cfe-152">계산 멤버에 사용되는 글꼴의 이름을 지정하는 MDX 식을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="76cfe-152">Type the MDX expression that provides the name of the font used for the calculated member.</span></span>  
  
 <span data-ttu-id="76cfe-153">**계산 도구** 창에서 선택한 요소를 이 옵션으로 끌어서 놓으면 선택한 요소의 MDX 구문을 포함시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76cfe-153">Drag selected elements from the **Calculation Tools** pane to this option to include the MDX syntax for the selected element.</span></span>  
  
 <span data-ttu-id="76cfe-154">글꼴 선택 단추를 클릭하여 **글꼴** 대화 상자를 표시하고 지정한 글꼴의 속성 값을 MDX 식에 삽입할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76cfe-154">Click the font selection button to display the **Font** dialog box and insert the property values for a specified font into the MDX expression.</span></span> <span data-ttu-id="76cfe-155">속성 값에 대한 자세한 내용은 [속성 값 만들기 및 사용&#40;MDX&#41;](creating-and-using-property-values-mdx.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="76cfe-155">For more information about property values, see [Creating and Using Property Values &#40;MDX&#41;](creating-and-using-property-values-mdx.md).</span></span>  
  
 <span data-ttu-id="76cfe-156">**글꼴 크기**</span><span class="sxs-lookup"><span data-stu-id="76cfe-156">**Font size**</span></span>  
 <span data-ttu-id="76cfe-157">계산 멤버에 사용되는 글꼴의 크기를 지정하는 MDX 식을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="76cfe-157">Type the MDX expression that provides the size of the font used for the calculated member.</span></span>  
  
 <span data-ttu-id="76cfe-158">**계산 도구** 창에서 선택한 요소를 이 옵션으로 끌어서 놓으면 선택한 요소의 MDX 구문을 포함시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76cfe-158">Drag selected elements from the **Calculation Tools** pane to this option to include the MDX syntax for the selected element.</span></span>  
  
 <span data-ttu-id="76cfe-159">글꼴 선택 단추를 클릭하여 **글꼴** 대화 상자를 표시하고 지정한 글꼴의 속성 값을 MDX 식에 삽입할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76cfe-159">Click the font selection button to display the **Font** dialog box and insert the property values for a specified font into the MDX expression.</span></span> <span data-ttu-id="76cfe-160">속성 값에 대한 자세한 내용은 [속성 값 만들기 및 사용&#40;MDX&#41;](creating-and-using-property-values-mdx.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="76cfe-160">For more information about property values, see [Creating and Using Property Values &#40;MDX&#41;](creating-and-using-property-values-mdx.md).</span></span>  
  
 <span data-ttu-id="76cfe-161">**글꼴 플래그**</span><span class="sxs-lookup"><span data-stu-id="76cfe-161">**Font flags**</span></span>  
 <span data-ttu-id="76cfe-162">밑줄이나 굵게와 같이 계산 멤버에 사용되는 글꼴의 글꼴 플래그를 포함하는 비트맵 값을 지정하는 MDX 식을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="76cfe-162">Type the MDX expression that provides the bitmapped value containing the font flags, such as underline or bold, of the font used for the calculated member.</span></span>  
  
 <span data-ttu-id="76cfe-163">**계산 도구** 창에서 선택한 요소를 이 옵션으로 끌어서 놓으면 선택한 요소의 MDX 구문을 포함시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76cfe-163">Drag selected elements from the **Calculation Tools** pane to this option to include the MDX syntax for the selected element.</span></span>  
  
 <span data-ttu-id="76cfe-164">글꼴 선택 단추를 클릭하여 **글꼴** 대화 상자를 표시하고 지정한 글꼴의 속성 값을 MDX 식에 삽입할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76cfe-164">Click the font selection button to display the **Font** dialog box and insert the property values for a specified font into the MDX expression.</span></span> <span data-ttu-id="76cfe-165">속성 값에 대한 자세한 내용은 [속성 값 만들기 및 사용&#40;MDX&#41;](creating-and-using-property-values-mdx.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="76cfe-165">For more information about property values, see [Creating and Using Property Values &#40;MDX&#41;](creating-and-using-property-values-mdx.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76cfe-166">참고 항목</span><span class="sxs-lookup"><span data-stu-id="76cfe-166">See Also</span></span>  
 <span data-ttu-id="76cfe-167">[계산](multidimensional-models-olap-logical-cube-objects/calculations.md) </span><span class="sxs-lookup"><span data-stu-id="76cfe-167">[Calculations](multidimensional-models-olap-logical-cube-objects/calculations.md) </span></span>  
 <span data-ttu-id="76cfe-168">[계산 멤버 만들기](multidimensional-models/create-calculated-members.md) </span><span class="sxs-lookup"><span data-stu-id="76cfe-168">[Create Calculated Members](multidimensional-models/create-calculated-members.md) </span></span>  
 <span data-ttu-id="76cfe-169">[큐브 디자이너 &#40;Analysis Services 다차원 데이터&#41;](cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="76cfe-169">[Cube Designer &#40;Analysis Services - Multidimensional Data&#41;](cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="76cfe-170">[큐브 디자이너의 계산 &#40;다차원 데이터&#41; &#40;Analysis Services&#41;](calculations-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="76cfe-170">[Calculations &#40;Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](calculations-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="76cfe-171">[도구 모음 &#40;계산 탭, 큐브 디자이너&#41; &#40;Analysis Services 다차원 데이터&#41;](toolbar-calculations-tab-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="76cfe-171">[Toolbar &#40;Calculations Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](toolbar-calculations-tab-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="76cfe-172">[스크립트 구성 도우미 &#40;계산 탭, 큐브 디자이너&#41; &#40;Analysis Services 다차원 데이터&#41;](script-organizer-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="76cfe-172">[Script Organizer &#40;Calculations Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](script-organizer-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="76cfe-173">[계산 도구 &#40;계산 탭, 큐브 디자이너&#41; &#40;Analysis Services 다차원 데이터&#41;](calculation-tools-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="76cfe-173">[Calculation Tools &#40;Calculations Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](calculation-tools-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="76cfe-174">[명명 된 집합 폼 편집기 &#40;계산 탭, 큐브 디자이너&#41; &#40;Analysis Services 다차원 데이터&#41;](named-set-form-editor-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="76cfe-174">[Named Set Form Editor &#40;Calculations Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](named-set-form-editor-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="76cfe-175">스크립트 편집기 &#40;계산 탭, 큐브 디자이너&#41; &#40;Analysis Services 다차원 데이터&#41;</span><span class="sxs-lookup"><span data-stu-id="76cfe-175">Script Editor &#40;Calculations Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;</span></span>](script-editor-calculations-cube-designer-analysis-services-multidimensional-data.md)  
  
  
