---
title: 동작 폼 편집기 (동작 탭, 큐브 디자이너) (Analysis Services 다차원 데이터) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.actionexpression.action.f1
ms.assetid: c363a29b-6099-473c-9625-460cc15b3d95
author: minewiskan
ms.author: owend
ms.openlocfilehash: b08ed03e843ba206f22969f9ada0da5a590a5811
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647345"
---
# <a name="action-form-editor-actions-tab-cube-designer-analysis-services---multidimensional-data"></a><span data-ttu-id="f925b-102">동작 폼 편집기(동작 탭, 큐브 디자이너)(Analysis Services - 다차원 데이터)</span><span class="sxs-lookup"><span data-stu-id="f925b-102">Action Form Editor (Actions Tab, Cube Designer) (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="f925b-103">큐브 디자이너의 **작업** 탭에서 동작 폼 편집기 창을 사용하여 표준 작업을 생성 및 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f925b-103">Use the Action Form Editor pane on the **Actions** tab in Cube Designer to create and modify standard actions.</span></span>  
  
## <a name="options"></a><span data-ttu-id="f925b-104">옵션</span><span class="sxs-lookup"><span data-stu-id="f925b-104">Options</span></span>  
 <span data-ttu-id="f925b-105">**이름**</span><span class="sxs-lookup"><span data-stu-id="f925b-105">**Name**</span></span>  
 <span data-ttu-id="f925b-106">동작의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="f925b-106">Type the name of the action.</span></span>  
  
 <span data-ttu-id="f925b-107">**동작 대상**</span><span class="sxs-lookup"><span data-stu-id="f925b-107">**Action Target**</span></span>  
 <span data-ttu-id="f925b-108">**대상 유형** 및 **대상 개체** 옵션을 보려면 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="f925b-108">Expand to view the **Target type** and **Target object** options.</span></span>  
  
 <span data-ttu-id="f925b-109">**대상 유형**</span><span class="sxs-lookup"><span data-stu-id="f925b-109">**Target type**</span></span>  
 <span data-ttu-id="f925b-110">동작을 연결할 개체의 유형을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f925b-110">Select the type of object to which the action is to be associated.</span></span> <span data-ttu-id="f925b-111">서버는 지정한 유형의 개체에 해당되는 동작만 클라이언트에 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="f925b-111">The server returns to the client only those actions that apply to the object of the specified type.</span></span> <span data-ttu-id="f925b-112">**조건** 을 만족하고 다음 표에 지정된 개체를 선택한 경우에만 클라이언트에서 이러한 동작을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f925b-112">The action is available to the client if the **Condition** is met and if the objects specified in the following table are selected.</span></span>  
  
|<span data-ttu-id="f925b-113">값</span><span class="sxs-lookup"><span data-stu-id="f925b-113">Value</span></span>|<span data-ttu-id="f925b-114">선택한 개체</span><span class="sxs-lookup"><span data-stu-id="f925b-114">Selected Object</span></span>|  
|-----------|---------------------|  
|<span data-ttu-id="f925b-115">특성 멤버</span><span class="sxs-lookup"><span data-stu-id="f925b-115">Attribute members</span></span>|<span data-ttu-id="f925b-116">**대상 개체**의 특성에 기반한 수준에서 멤버가 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="f925b-116">A member is selected from a level based on the attribute in **Target object**.</span></span>|  
|<span data-ttu-id="f925b-117">셀</span><span class="sxs-lookup"><span data-stu-id="f925b-117">Cells</span></span>|<span data-ttu-id="f925b-118">**대상 개체** 의 명명된 집합이 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="f925b-118">The named set in **Target object** is selected.</span></span> <span data-ttu-id="f925b-119">큐브의 모든 셀을 선택하려면 **셀 추가** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f925b-119">Select **All cells** to select all of the cells in the cube.</span></span>|  
|<span data-ttu-id="f925b-120">큐브</span><span class="sxs-lookup"><span data-stu-id="f925b-120">Cube</span></span>|<span data-ttu-id="f925b-121">**대상 개체** 의 큐브가 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="f925b-121">The cube in **Target object** is selected.</span></span> <span data-ttu-id="f925b-122">현재 큐브를 사용하려면 CURRENTCUBE를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f925b-122">Select CURRENTCUBE to use the current cube.</span></span><br /><br /> <span data-ttu-id="f925b-123">참고: CURRENTCUBE를 사용하면 큐브의 이름을 바꾸거나 동작을 다른 큐브로 복사하는 경우 이식성이 향상됩니다.</span><span class="sxs-lookup"><span data-stu-id="f925b-123">Note: Using CURRENTCUBE provides additional portability in cases where the cube may be renamed or the action copied to other cubes.</span></span> <span data-ttu-id="f925b-124">CURRENTCUBE를 사용하여 현재 큐브를 나타내는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="f925b-124">It is recommended that you use CURRENTCUBE to represent the current cube.</span></span>|  
|<span data-ttu-id="f925b-125">차원 멤버</span><span class="sxs-lookup"><span data-stu-id="f925b-125">Dimension members</span></span>|<span data-ttu-id="f925b-126">**대상 개체** 의 차원 멤버가 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="f925b-126">A member of the dimension in **Target object** is selected.</span></span>|  
|<span data-ttu-id="f925b-127">계층</span><span class="sxs-lookup"><span data-stu-id="f925b-127">Hierarchy</span></span>|<span data-ttu-id="f925b-128">**대상 개체** 의 계층이 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="f925b-128">The hierarchy in **Target object** is selected.</span></span>|  
|<span data-ttu-id="f925b-129">계층 멤버</span><span class="sxs-lookup"><span data-stu-id="f925b-129">Hierarchy members</span></span>|<span data-ttu-id="f925b-130">**대상 개체** 의 계층 내에 있는 멤버가 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="f925b-130">A member within the hierarchy in **Target object** is selected.</span></span>|  
|<span data-ttu-id="f925b-131">Level</span><span class="sxs-lookup"><span data-stu-id="f925b-131">Level</span></span>|<span data-ttu-id="f925b-132">**대상 개체** 의 수준이 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="f925b-132">The level in **Target object** is selected.</span></span>|  
|<span data-ttu-id="f925b-133">수준 멤버</span><span class="sxs-lookup"><span data-stu-id="f925b-133">Level members</span></span>|<span data-ttu-id="f925b-134">**대상 개체** 의 수준 내에 있는 멤버가 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="f925b-134">A member within the level in **Target object** is selected.</span></span>|  
  
 <span data-ttu-id="f925b-135">**대상 개체**</span><span class="sxs-lookup"><span data-stu-id="f925b-135">**Target object**</span></span>  
 <span data-ttu-id="f925b-136">동작을 연결할 개체를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f925b-136">Select the object to which the action is to be associated.</span></span> <span data-ttu-id="f925b-137">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 인스턴스는 선택한 개체에 적용되는 동작만 클라이언트에 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="f925b-137">The [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance returns to the client only those actions that apply to the selected object.</span></span> <span data-ttu-id="f925b-138">사용 가능한 개체 목록은 **대상 유형**에서 선택한 항목에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="f925b-138">The list of available objects is constrained by the choice of **Target type**.</span></span>  
  
 <span data-ttu-id="f925b-139">**조건(옵션)**</span><span class="sxs-lookup"><span data-stu-id="f925b-139">**Condition (Optional)**</span></span>  
 <span data-ttu-id="f925b-140">선택적 조건을 기술하는 MDX(Multidimensional Expression) 식을 입력합니다. 이 옵션은 **대상 개체**와 함께 사용되어 동작의 가용성을 추가로 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="f925b-140">Enter the Multidimensional Expressions (MDX) expression that describes an optional condition, used in conjunction with **Target object**, which further restricts when the action is available.</span></span> <span data-ttu-id="f925b-141">식은 부울 값을 반환해야 합니다. True인 경우 동작을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f925b-141">The expression must return a Boolean value that, if true, indicates the action is available.</span></span>  
  
 <span data-ttu-id="f925b-142">**계산 도구** 창에서 선택한 요소를 이 옵션으로 끌어서 놓으면 선택한 요소의 MDX 구문을 포함시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f925b-142">Drag selected elements from the **Calculation Tools** pane to this option to include the MDX syntax for the selected element.</span></span>  
  
 <span data-ttu-id="f925b-143">**동작 내용**</span><span class="sxs-lookup"><span data-stu-id="f925b-143">**Action Content**</span></span>  
 <span data-ttu-id="f925b-144">**유형** 및 **동작 식** 옵션을 보려면 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="f925b-144">Expand to view the **Type** and **Action expression** options.</span></span>  
  
 <span data-ttu-id="f925b-145">**형식**</span><span class="sxs-lookup"><span data-stu-id="f925b-145">**Type**</span></span>  
 <span data-ttu-id="f925b-146">작업을 실행할 때의 동작 유형을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f925b-146">Select the type of action to take when the action is run.</span></span> <span data-ttu-id="f925b-147">사용할 수 있는 동작 유형은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="f925b-147">The following action types are available:</span></span>  
  
|<span data-ttu-id="f925b-148">값</span><span class="sxs-lookup"><span data-stu-id="f925b-148">Value</span></span>|<span data-ttu-id="f925b-149">Description</span><span class="sxs-lookup"><span data-stu-id="f925b-149">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f925b-150">데이터 세트</span><span class="sxs-lookup"><span data-stu-id="f925b-150">Dataset</span></span>|<span data-ttu-id="f925b-151">클라이언트 애플리케이션에서 실행 및 표시하며 다차원 데이터 세트를 나타내는 MDX(Multidimensional Expressions) 문을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="f925b-151">Returns a Multidimensional Expressions (MDX) statement, representing a multidimensional dataset, to be run and displayed by the client application.</span></span>|  
|<span data-ttu-id="f925b-152">소유</span><span class="sxs-lookup"><span data-stu-id="f925b-152">Proprietary</span></span>|<span data-ttu-id="f925b-153">이 동작에 대한 **애플리케이션** 설정과 연결된 클라이언트 애플리케이션에서 해석할 수 있는 소유 문자열을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="f925b-153">Returns a proprietary string that can be interpreted by client applications associated with the **Application** setting for this action.</span></span>|  
|<span data-ttu-id="f925b-154">행 집합</span><span class="sxs-lookup"><span data-stu-id="f925b-154">Rowset</span></span>|<span data-ttu-id="f925b-155">클라이언트 애플리케이션에서 실행 및 표시하며 테이블 형식 행 집합을 나타내는 MDX(Multidimensional Expressions) 문을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="f925b-155">Returns a Multidimensional Expressions (MDX) statement, representing a tabular rowset, to be run and displayed by the client application.</span></span>|  
|<span data-ttu-id="f925b-156">문</span><span class="sxs-lookup"><span data-stu-id="f925b-156">Statement</span></span>|<span data-ttu-id="f925b-157">클라이언트 애플리케이션에서 실행할 명령 문자열을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="f925b-157">Returns a command string to be run by the client application.</span></span>|  
|<span data-ttu-id="f925b-158">URL</span><span class="sxs-lookup"><span data-stu-id="f925b-158">URL</span></span>|<span data-ttu-id="f925b-159">클라이언트 애플리케이션에서 일반적으로 인터넷 브라우저로 여는 URL(Uniform Resource Location) 문자열을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="f925b-159">Returns a Uniform Resource Location (URL) string to be opened by the client application, typically with an Internet browser.</span></span>|  
  
 <span data-ttu-id="f925b-160">동작 유형에 대한 자세한 내용은 [동작&#40;Analysis Services - 다차원 데이터&#41;](multidimensional-models/actions-analysis-services-multidimensional-data.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f925b-160">For more information about action types, see [Actions &#40;Analysis Services - Multidimensional Data&#41;](multidimensional-models/actions-analysis-services-multidimensional-data.md).</span></span>  
  
 <span data-ttu-id="f925b-161">**동작 식**</span><span class="sxs-lookup"><span data-stu-id="f925b-161">**Action expression**</span></span>  
 <span data-ttu-id="f925b-162">해당 동작에서 실행할 클라이언트 애플리케이션으로 반환한 문자열을 반환하는 MDX(Multidimensional Expression) 식을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="f925b-162">Type the Multidimensional Expressions (MDX) expression that returns the string returned by the action to the client application for execution.</span></span>  
  
 <span data-ttu-id="f925b-163">**추가 속성**</span><span class="sxs-lookup"><span data-stu-id="f925b-163">**Additional Properties**</span></span>  
 <span data-ttu-id="f925b-164">확장하면 **호출**, **애플리케이션**, **설명**, **캡션**및 **MDX 캡션** 옵션이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f925b-164">Expand to view the **Invocation**, **Application**, **Description**, **Caption**, and **Caption Is MDX** options.</span></span>  
  
 <span data-ttu-id="f925b-165">**호출**</span><span class="sxs-lookup"><span data-stu-id="f925b-165">**Invocation**</span></span>  
 <span data-ttu-id="f925b-166">동작 실행 시기를 나타내는 설정을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f925b-166">Select the setting that indicates when the action should be carried out.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f925b-167">이 옵션은 클라이언트 애플리케이션에 동작 실행 시기에 대한 권장 사항만 제공할 뿐 직접 작업 호출을 제어하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f925b-167">This option only provides a recommendation to a client application as to when to execute an action, and does not directly control the invocation of the action.</span></span>  
  
 <span data-ttu-id="f925b-168">다음 표에서는 사용 가능한 설정에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f925b-168">The following table describes the available settings.</span></span>  
  
|<span data-ttu-id="f925b-169">값</span><span class="sxs-lookup"><span data-stu-id="f925b-169">Value</span></span>|<span data-ttu-id="f925b-170">Description</span><span class="sxs-lookup"><span data-stu-id="f925b-170">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f925b-171">Batch</span><span class="sxs-lookup"><span data-stu-id="f925b-171">Batch</span></span>|<span data-ttu-id="f925b-172">동작이 일괄 처리 작업이나 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 태스크의 일부로 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="f925b-172">The action should run as part of a batch operation or an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] task.</span></span>|  
|<span data-ttu-id="f925b-173">대화형</span><span class="sxs-lookup"><span data-stu-id="f925b-173">Interactive</span></span>|<span data-ttu-id="f925b-174">사용자가 작업을 호출할 때 동작이 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="f925b-174">The action runs when the user invokes the action.</span></span>|  
|<span data-ttu-id="f925b-175">열 때</span><span class="sxs-lookup"><span data-stu-id="f925b-175">On Open</span></span>|<span data-ttu-id="f925b-176">큐브를 처음으로 열 때 동작이 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="f925b-176">The action runs when the cube is first opened.</span></span>|  
  
 <span data-ttu-id="f925b-177">**애플리케이션**</span><span class="sxs-lookup"><span data-stu-id="f925b-177">**Application**</span></span>  
 <span data-ttu-id="f925b-178">**동작 식**에서 반환한 문자열을 해석할 수 있는 애플리케이션의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="f925b-178">Type the name of the application that can interpret the string returned by **Action expression**.</span></span>  
  
 <span data-ttu-id="f925b-179">이 옵션을 사용하여 이 동작을 가장 많이 사용하는 클라이언트 애플리케이션을 식별하고 팝업 메뉴에서 해당 작업 옆에 적절한 아이콘을 표시할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f925b-179">You can also use this option to identify which client application most commonly uses this action, as well as to display appropriate icons next to the action in a pop-up menu.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f925b-180">이 옵션은 클라이언트 애플리케이션에 동작을 실행해야 하는 클라이언트 애플리케이션에 대한 권장 사항만 제공할 뿐 직접 작업에 대한 액세스를 제어하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f925b-180">This option only provides a recommendation to a client application as to what client application should execute an action, and does not directly control access to the action.</span></span> <span data-ttu-id="f925b-181">클라이언트 애플리케이션은 다른 클라이언트 애플리케이션에 연결된 모든 동작을 숨겨야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f925b-181">Client applications should hide any actions that are associated with other client applications.</span></span>  
  
 <span data-ttu-id="f925b-182">**설명**</span><span class="sxs-lookup"><span data-stu-id="f925b-182">**Description**</span></span>  
 <span data-ttu-id="f925b-183">동작에 대한 선택적 설명을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="f925b-183">Type the optional description of the action.</span></span>  
  
 <span data-ttu-id="f925b-184">**캡션**</span><span class="sxs-lookup"><span data-stu-id="f925b-184">**Caption**</span></span>  
 <span data-ttu-id="f925b-185">**MDX 캡션** 이 **False**로 설정된 경우 클라이언트 애플리케이션에서 동작에 대해 표시할 캡션을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="f925b-185">Type the caption to be displayed for the action in the client application if **Caption Is MDX** is set to **False**.</span></span>  
  
 <span data-ttu-id="f925b-186">**MDX 캡션** 이 **True**로 설정된 경우 캡션 문자열을 반환하는 MDX(Multidimensional Expression) 식을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="f925b-186">Type the Multidimensional Expressions (MDX) expression that returns a string for the caption if **Caption Is MDX** is set to **True**.</span></span>  
  
 <span data-ttu-id="f925b-187">**MDX 캡션**</span><span class="sxs-lookup"><span data-stu-id="f925b-187">**Caption is MDX**</span></span>  
 <span data-ttu-id="f925b-188">클라이언트 애플리케이션에서 동작에 대해 표시할 캡션을 나타내는 리터럴 문자열이 **캡션** 에 포함되어 있음을 나타내려면 **False** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f925b-188">Select **False** to indicate that **Caption** contains a literal string representing a caption to be displayed for the action in the client application.</span></span>  
  
 <span data-ttu-id="f925b-189">클라이언트 애플리케이션에서 동작에 대해 표시할 캡션을 나타내는 문자열을 반환하는 MDX 식이 **캡션** 에 포함되어 있음을 나타내려면 **True** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f925b-189">Select **True** to indicate that **Caption** contains an MDX expression that returns a string representing a caption to be displayed for the action in the client application.</span></span> <span data-ttu-id="f925b-190">클라이언트 애플리케이션으로 동작을 반환하기 전에 MDX 식을 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f925b-190">The MDX expression must be resolved before the action is returned to the client application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f925b-191">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f925b-191">See Also</span></span>  
 <span data-ttu-id="f925b-192">[큐브 디자이너 Analysis Services&#41; &#40;&#40;작업은 다차원 데이터&#41;](actions-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="f925b-192">[Actions &#40;Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](actions-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="f925b-193">[도구 모음 &#40;동작 탭, 큐브 디자이너&#41; &#40;Analysis Services 다차원 데이터&#41;](toolbar-actions-tab-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="f925b-193">[Toolbar &#40;Actions Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](toolbar-actions-tab-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="f925b-194">[동작 구성 도우미 &#40;동작 탭, 큐브 디자이너&#41; &#40;Analysis Services 다차원 데이터&#41;](action-organizer-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="f925b-194">[Action Organizer &#40;Actions Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](action-organizer-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="f925b-195">[계산 도구 &#40;동작 탭, 큐브 디자이너&#41; &#40;Analysis Services 다차원 데이터&#41;](calculation-tools-actions-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="f925b-195">[Calculation Tools &#40;Actions Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](calculation-tools-actions-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="f925b-196">[드릴스루 동작 폼 편집기 &#40;동작 탭, 큐브 디자이너&#41; &#40;Analysis Services 다차원 데이터&#41;](drillthrough-action-form-editor-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="f925b-196">[Drillthrough Action Form Editor &#40;Actions Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](drillthrough-action-form-editor-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="f925b-197">보고서 동작 폼 편집기 &#40;동작 탭, 큐브 디자이너&#41; &#40;Analysis Services-다차원 데이터&#41;</span><span class="sxs-lookup"><span data-stu-id="f925b-197">Report Action Form Editor &#40;Actions Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;</span></span>](report-action-form-editor-cube-designer-analysis-services-multidimensional-data.md)  
  
  
