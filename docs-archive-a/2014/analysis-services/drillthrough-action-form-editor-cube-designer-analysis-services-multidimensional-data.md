---
title: 드릴스루 동작 폼 편집기 (동작 탭, 큐브 디자이너) (Analysis Services 다차원 데이터) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.actionexpression.drillthroughaction.f1
ms.assetid: 225fd818-b5ea-494f-b67b-66e09798274a
author: minewiskan
ms.author: owend
ms.openlocfilehash: 546448bd05f3af45b7093acb2dbb9d1e1a8f1bd5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659712"
---
# <a name="drillthrough-action-form-editor-actions-tab-cube-designer-analysis-services---multidimensional-data"></a><span data-ttu-id="33b82-102">드릴스루 동작 폼 편집기(동작 탭, 큐브 디자이너)(Analysis Services - 다차원 데이터)</span><span class="sxs-lookup"><span data-stu-id="33b82-102">Drillthrough Action Form Editor (Actions Tab, Cube Designer) (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="33b82-103">큐브 디자이너의 **작업** 탭에 있는 **드릴스루 동작 폼 편집기** 창을 사용하여 **작업 구성 도우미** 창에서 선택한 드릴스루 작업을 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="33b82-103">Use the **Drillthrough Action Form Editor** pane on the **Actions** tab in Cube Designer to modify the drillthrough action selected in the **Action Organizer** pane.</span></span> <span data-ttu-id="33b82-104">드릴스루 동작에 대한 자세한 내용은 [작업&#40;Analysis Services - 다차원 데이터&#41;](multidimensional-models/actions-analysis-services-multidimensional-data.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="33b82-104">For more information about drillthrough actions, see [Actions &#40;Analysis Services - Multidimensional Data&#41;](multidimensional-models/actions-analysis-services-multidimensional-data.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="33b82-105">드릴스루 동작은 더 이상 기본 데이터 저장소로 드릴다운하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="33b82-105">Drillthrough actions no longer drill down to the underlying data store.</span></span> <span data-ttu-id="33b82-106">드릴스루 동작에서 액세스하는 정보는 차원 또는 계층 멤버를 사용하여 큐브 내에서 모델링해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="33b82-106">The information that drillthrough actions access must be modeled within the cube by using dimension or hierarchy members.</span></span>  
  
## <a name="options"></a><span data-ttu-id="33b82-107">옵션</span><span class="sxs-lookup"><span data-stu-id="33b82-107">Options</span></span>  
 <span data-ttu-id="33b82-108">**name**</span><span class="sxs-lookup"><span data-stu-id="33b82-108">**name**</span></span>  
 <span data-ttu-id="33b82-109">동작의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="33b82-109">Type the name of the action.</span></span>  
  
 <span data-ttu-id="33b82-110">**동작 대상**</span><span class="sxs-lookup"><span data-stu-id="33b82-110">**Action Target**</span></span>  
 <span data-ttu-id="33b82-111">확장하면 **측정값 그룹 멤버** 옵션이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="33b82-111">Expand to view the **Measure group members** option.</span></span>  
  
 <span data-ttu-id="33b82-112">**측정값 그룹 멤버**</span><span class="sxs-lookup"><span data-stu-id="33b82-112">**Measure group members**</span></span>  
 <span data-ttu-id="33b82-113">드릴스루 동작을 연결할 측정값 그룹을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="33b82-113">Select the measure group to which the drillthrough action is to be associated.</span></span>  
  
 <span data-ttu-id="33b82-114">**조건(옵션)**</span><span class="sxs-lookup"><span data-stu-id="33b82-114">**Condition (Optional)**</span></span>  
 <span data-ttu-id="33b82-115">선택적 조건을 기술하는 MDX(Multidimensional Expression) 식을 입력합니다. 이 옵션은 **측정값 그룹 멤버**와 함께 사용되어 동작의 가용성을 추가로 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="33b82-115">Enter the Multidimensional Expressions (MDX) expression that describes an optional condition, used in conjunction with **Measure group members**, which further restricts when the action is available.</span></span> <span data-ttu-id="33b82-116">식은 부울 값을 반환해야 합니다. True인 경우 동작을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="33b82-116">The expression must return a Boolean value that, if true, indicates the action is available.</span></span>  
  
 <span data-ttu-id="33b82-117">**계산 도구** 창에서 선택한 요소를 이 옵션으로 끌어서 놓으면 선택한 요소의 MDX 구문을 포함시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="33b82-117">Drag selected elements from the **Calculation Tools** pane to this option to include the MDX syntax for the selected element.</span></span>  
  
 <span data-ttu-id="33b82-118">**드릴스루 열**</span><span class="sxs-lookup"><span data-stu-id="33b82-118">**Drillthrough Columns**</span></span>  
 <span data-ttu-id="33b82-119">확장하면 사용자가 이 동작을 실행할 때 반환되는 특성을 나타내는 표가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="33b82-119">Expand to display a grid in which to indicate the attributes that are returned when the user runs this action.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="33b82-120">둘 이상의 차원을 선택할 수 있지만 드릴스루 동작에서 한 차원을 두 번 이상 사용할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="33b82-120">You can select more than one dimension, but no dimension can be used more than once in a drillthrough action.</span></span>  
  
 <span data-ttu-id="33b82-121">표에는 다음 열이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="33b82-121">The grid contains the following columns:</span></span>  
  
|<span data-ttu-id="33b82-122">열</span><span class="sxs-lookup"><span data-stu-id="33b82-122">Column</span></span>|<span data-ttu-id="33b82-123">Description</span><span class="sxs-lookup"><span data-stu-id="33b82-123">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="33b82-124">**차원**</span><span class="sxs-lookup"><span data-stu-id="33b82-124">**Dimensions**</span></span>|<span data-ttu-id="33b82-125">반환 특성이 파생되는 차원을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="33b82-125">Select the dimension from which the returned attribute is derived.</span></span> <span data-ttu-id="33b82-126">측정값을 드릴스루하려면 MEASURES를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="33b82-126">Select MEASURES to drillthrough on measures.</span></span>|  
|<span data-ttu-id="33b82-127">**반환 열**</span><span class="sxs-lookup"><span data-stu-id="33b82-127">**Return Columns**</span></span>|<span data-ttu-id="33b82-128">선택한 차원에서 동작 실행 시 반환할 특성 또는 측정값을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="33b82-128">Select the attribute or measure from the selected dimension to be returned when the action is run.</span></span>|  
  
 <span data-ttu-id="33b82-129">**추가 속성**</span><span class="sxs-lookup"><span data-stu-id="33b82-129">**Additional Properties**</span></span>  
 <span data-ttu-id="33b82-130">확장하면 **기본값**, **최대 행 수**, **호출**, **애플리케이션**, **설명**, **캡션**및 **MDX 캡션** 옵션이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="33b82-130">Expand to view the **Default**, **Maximum rows**, **Invocation**, **Application**, **Description**, **Caption**, and **Caption Is MDX** options.</span></span>  
  
 <span data-ttu-id="33b82-131">**기본값**</span><span class="sxs-lookup"><span data-stu-id="33b82-131">**Default**</span></span>  
 <span data-ttu-id="33b82-132">이 드릴스루 동작을 기본 드릴스루 동작으로 포함하려면 **True** 를 선택합니다. 포함하지 않으려면 **False**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="33b82-132">Select **True** to include this drillthrough action as a default drillthrough action, otherwise, select **False**.</span></span>  
  
 <span data-ttu-id="33b82-133">`RETURN` `DRILLTHROUGH` 클라이언트 응용 프로그램에서 실행 한 MDX 문에서 절을 생략 하면 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 인스턴스는 모든 기본 드릴스루 동작을 평가 하 고 비어 있지 않은 집합을 반환 하는 첫 번째 기본 드릴스루 동작을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="33b82-133">If the `RETURN` clause is omitted from an MDX `DRILLTHROUGH` statement executed by a client application, the [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance evaluates all default drillthrough actions and runs the first default drillthrough action that returns a non-empty set.</span></span> <span data-ttu-id="33b82-134">MDX 문에 대 한 자세한 내용은 `DRILLTHROUGH` [&#40;mdx&#41;](/sql/mdx/mdx-data-manipulation-drillthrough)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="33b82-134">For more information about the MDX `DRILLTHROUGH` statement, see [DRILLTHROUGH Statement &#40;MDX&#41;](/sql/mdx/mdx-data-manipulation-drillthrough).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="33b82-135">이 옵션은 이전 버전과의 호환성을 위해 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="33b82-135">This option is used for backwards compatibility purposes.</span></span>  
  
 <span data-ttu-id="33b82-136">**최대 행 수**</span><span class="sxs-lookup"><span data-stu-id="33b82-136">**Maximum rows**</span></span>  
 <span data-ttu-id="33b82-137">드릴스루 동작에서 반환할 최대 행 수를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="33b82-137">Type the maximum number of rows to be returned by the drillthrough action.</span></span> <span data-ttu-id="33b82-138">이 옵션을 0 또는 빈 값으로 설정하면 드릴스루 동작은 검색된 모든 행을 클라이언트 애플리케이션으로 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="33b82-138">Setting this option to zero or an empty value indicates that the drillthrough action returns all rows retrieved by the action to the client application.</span></span>  
  
 <span data-ttu-id="33b82-139">**호출**</span><span class="sxs-lookup"><span data-stu-id="33b82-139">**Invocation**</span></span>  
 <span data-ttu-id="33b82-140">동작 실행 시기를 나타내는 설정을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="33b82-140">Select the setting that indicates when the action should be carried out.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="33b82-141">이 옵션은 클라이언트 애플리케이션에 동작 실행 시기에 대한 권장 사항만 제공할 뿐 직접 작업 호출을 제어하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="33b82-141">This option only provides a recommendation to a client application as to when to execute an action, and does not directly control the invocation of the action.</span></span>  
  
 <span data-ttu-id="33b82-142">다음 표에서는 사용 가능한 설정에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="33b82-142">The following table describes the available settings.</span></span>  
  
|<span data-ttu-id="33b82-143">값</span><span class="sxs-lookup"><span data-stu-id="33b82-143">Value</span></span>|<span data-ttu-id="33b82-144">Description</span><span class="sxs-lookup"><span data-stu-id="33b82-144">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="33b82-145">Batch</span><span class="sxs-lookup"><span data-stu-id="33b82-145">Batch</span></span>|<span data-ttu-id="33b82-146">동작이 일괄 처리 작업이나 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 태스크의 일부로 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="33b82-146">The action should run as part of a batch operation or an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] task.</span></span>|  
|<span data-ttu-id="33b82-147">대화형</span><span class="sxs-lookup"><span data-stu-id="33b82-147">Interactive</span></span>|<span data-ttu-id="33b82-148">사용자가 작업을 호출할 때 동작이 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="33b82-148">The action runs when the user invokes the action.</span></span>|  
|<span data-ttu-id="33b82-149">열 때</span><span class="sxs-lookup"><span data-stu-id="33b82-149">On Open</span></span>|<span data-ttu-id="33b82-150">큐브를 처음으로 열 때 동작이 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="33b82-150">The action runs when the cube is first opened.</span></span>|  
  
 <span data-ttu-id="33b82-151">**애플리케이션**</span><span class="sxs-lookup"><span data-stu-id="33b82-151">**Application**</span></span>  
 <span data-ttu-id="33b82-152">드릴스루 동작을 실행할 수 있는 애플리케이션 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="33b82-152">Type the name of the application that can execute the drillthrough action.</span></span>  
  
 <span data-ttu-id="33b82-153">이 옵션을 사용하여 이 동작을 가장 많이 사용하는 클라이언트 애플리케이션을 식별하고 팝업 메뉴에서 해당 작업 옆에 적절한 아이콘을 표시할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="33b82-153">You can also use this option to identify which client application most commonly uses this action, as well as to display appropriate icons next to the action in a pop-up menu.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="33b82-154">이 옵션은 클라이언트 애플리케이션에 동작을 실행해야 하는 클라이언트 애플리케이션에 대한 권장 사항만 제공할 뿐 직접 작업에 대한 액세스를 제어하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="33b82-154">This option only provides a recommendation to a client application as to what client application should execute an action, and does not directly control access to the action.</span></span> <span data-ttu-id="33b82-155">클라이언트 애플리케이션은 다른 클라이언트 애플리케이션에 연결된 모든 동작을 숨겨야 합니다.</span><span class="sxs-lookup"><span data-stu-id="33b82-155">Client applications should hide any actions that are associated with other client applications.</span></span>  
  
 <span data-ttu-id="33b82-156">**설명**</span><span class="sxs-lookup"><span data-stu-id="33b82-156">**Description**</span></span>  
 <span data-ttu-id="33b82-157">동작에 대한 선택적 설명을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="33b82-157">Type the optional description of the action.</span></span>  
  
 <span data-ttu-id="33b82-158">**캡션**</span><span class="sxs-lookup"><span data-stu-id="33b82-158">**Caption**</span></span>  
 <span data-ttu-id="33b82-159">**MDX 캡션** 이 **False**로 설정된 경우 클라이언트 애플리케이션에서 동작에 대해 표시할 캡션을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="33b82-159">Type the caption to be displayed for the action in the client application if **Caption Is MDX** is set to **False**.</span></span>  
  
 <span data-ttu-id="33b82-160">**MDX 캡션** 이 **True**로 설정된 경우 캡션 문자열을 반환하는 MDX(Multidimensional Expression) 식을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="33b82-160">Type the Multidimensional Expressions (MDX) expression that returns a string for the caption if **Caption Is MDX** is set to **True**.</span></span>  
  
 <span data-ttu-id="33b82-161">**MDX 캡션**</span><span class="sxs-lookup"><span data-stu-id="33b82-161">**Caption Is MDX**</span></span>  
 <span data-ttu-id="33b82-162">클라이언트 애플리케이션에서 동작에 대해 표시할 캡션을 나타내는 리터럴 문자열이 **캡션** 에 포함되어 있음을 나타내려면 **False** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="33b82-162">Select **False** to indicate that **Caption** contains a literal string representing a caption to be displayed for the action in the client application.</span></span>  
  
 <span data-ttu-id="33b82-163">클라이언트 애플리케이션에서 동작에 대해 표시할 캡션을 나타내는 문자열을 반환하는 MDX 식이 **캡션** 에 포함되어 있음을 나타내려면 **True** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="33b82-163">Select **True** to indicate that **Caption** contains an MDX expression that returns a string representing a caption to be displayed for the action in the client application.</span></span> <span data-ttu-id="33b82-164">클라이언트 애플리케이션으로 동작을 반환하기 전에 MDX 식을 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="33b82-164">The MDX expression must be resolved before the action is returned to the client application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33b82-165">참고 항목</span><span class="sxs-lookup"><span data-stu-id="33b82-165">See Also</span></span>  
 <span data-ttu-id="33b82-166">[MDX&#41; 참조 &#40;다차원 식](/sql/mdx/multidimensional-expressions-mdx-reference) </span><span class="sxs-lookup"><span data-stu-id="33b82-166">[Multidimensional Expressions &#40;MDX&#41; Reference](/sql/mdx/multidimensional-expressions-mdx-reference) </span></span>  
 <span data-ttu-id="33b82-167">[큐브 디자이너 Analysis Services&#41; &#40;&#40;작업은 다차원 데이터&#41;](actions-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="33b82-167">[Actions &#40;Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](actions-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="33b82-168">[도구 모음 &#40;동작 탭, 큐브 디자이너&#41; &#40;Analysis Services 다차원 데이터&#41;](toolbar-actions-tab-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="33b82-168">[Toolbar &#40;Actions Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](toolbar-actions-tab-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="33b82-169">[동작 구성 도우미 &#40;동작 탭, 큐브 디자이너&#41; &#40;Analysis Services 다차원 데이터&#41;](action-organizer-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="33b82-169">[Action Organizer &#40;Actions Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](action-organizer-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="33b82-170">[계산 도구 &#40;동작 탭, 큐브 디자이너&#41; &#40;Analysis Services 다차원 데이터&#41;](calculation-tools-actions-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="33b82-170">[Calculation Tools &#40;Actions Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](calculation-tools-actions-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="33b82-171">[작업 폼 편집기 &#40;동작 탭, 큐브 디자이너&#41; &#40;Analysis Services 다차원 데이터&#41;](action-form-editor-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="33b82-171">[Action Form Editor &#40;Actions Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](action-form-editor-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="33b82-172">보고서 동작 폼 편집기 &#40;동작 탭, 큐브 디자이너&#41; &#40;Analysis Services-다차원 데이터&#41;</span><span class="sxs-lookup"><span data-stu-id="33b82-172">Report Action Form Editor &#40;Actions Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;</span></span>](report-action-form-editor-cube-designer-analysis-services-multidimensional-data.md)  
  
  
