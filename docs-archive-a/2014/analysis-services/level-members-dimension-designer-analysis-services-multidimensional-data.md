---
title: 수준 및 멤버 (브라우저 탭, 차원 디자이너) (Analysis Services 다차원 데이터) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dimensiondesigner.browsertab.levelsandmembers.f1
ms.assetid: 3f61e384-5b4e-4480-a7ed-b408de2fdea7
author: minewiskan
ms.author: owend
ms.openlocfilehash: 21680f00b82b5410e2c7a67122fdcfeb78c999dc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743584"
---
# <a name="level-and-members-browser-tab-dimension-designer-analysis-services---multidimensional-data"></a><span data-ttu-id="cea6f-102">수준 및 멤버(브라우저 탭, 차원 디자이너)(Analysis Services - 다차원 데이터)</span><span class="sxs-lookup"><span data-stu-id="cea6f-102">Level and Members (Browser Tab, Dimension Designer) (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="cea6f-103">이 창을 사용하여 현재 선택한 계층 및 언어의 멤버를 찾아볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cea6f-103">Use this pane to browse the members of the currently selected hierarchy and language.</span></span> <span data-ttu-id="cea6f-104">찾아볼 계층 또는 언어를 선택하려면 **도구 모음** 창의 **계층** 및 **언어** 옵션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="cea6f-104">To select a hierarchy or language to browse, use the **Hierarchy** and **Language** options on the **Toolbar** pane.</span></span> <span data-ttu-id="cea6f-105">도구 모음 창에 대 한 자세한 내용은 [도구 모음 &#40;브라우저 탭, 차원 디자이너&#41; &#40;Analysis Services-다차원 데이터&#41;](toolbar-browser-tab-dimension-designer-analysis-services-multidimensional-data.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="cea6f-105">For more information about the Toolbar pane, see [Toolbar &#40;Browser Tab, Dimension Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](toolbar-browser-tab-dimension-designer-analysis-services-multidimensional-data.md).</span></span>  
  
## <a name="writeback-mode"></a><span data-ttu-id="cea6f-106">쓰기 저장 모드</span><span class="sxs-lookup"><span data-stu-id="cea6f-106">Writeback Mode</span></span>  
 <span data-ttu-id="cea6f-107">쓰기 저장 모드를 설정하면 이 창의 기능이 바뀝니다.</span><span class="sxs-lookup"><span data-stu-id="cea6f-107">The functionality of this pane changes if writeback mode is enabled.</span></span> <span data-ttu-id="cea6f-108">쓰기 저장 모드를 설정하려면 선택한 차원을 쓰기 가능하도록 설정, 즉 차원의 `WriteEnabled` 속성을 true로 설정하고 해당 차원을 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 인스턴스에 배포해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cea6f-108">The selected dimension must be write-enabled (in other words, the `WriteEnabled` property of the dimension must be set to true) and the dimension must be deployed to an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance in order to enable writeback mode.</span></span>  
  
 <span data-ttu-id="cea6f-109">쓰기 저장 모드를 설정하려면 **도구 모음** 창에서 **쓰기 저장** 을 선택하거나 **수준 및 멤버** 창을 마우스 오른쪽 단추로 클릭한 다음 상황에 맞는 메뉴에서 **쓰기 저장** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="cea6f-109">To enable writeback mode, you can either select **Writeback** from the **Toolbar** pane, or right-click the **Level and Members** pane and select **Writeback** from the context menu.</span></span>  
  
 <span data-ttu-id="cea6f-110">쓰기 저장 모드를 설정하면 **수준 및 멤버** 창에서 다음과 같은 추가 동작을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cea6f-110">If writeback mode is enabled, you can perform the following additional actions in the **Level and Members** pane:</span></span>  
  
|<span data-ttu-id="cea6f-111">할 일</span><span class="sxs-lookup"><span data-stu-id="cea6f-111">To do</span></span>|<span data-ttu-id="cea6f-112">수행하는 작업</span><span class="sxs-lookup"><span data-stu-id="cea6f-112">Perform</span></span>|  
|-----------|-------------|  
|<span data-ttu-id="cea6f-113">선택한 계층 내에서 형제 및 자식 멤버 생성</span><span class="sxs-lookup"><span data-stu-id="cea6f-113">Create sibling and child members within the selected hierarchy.</span></span>|<span data-ttu-id="cea6f-114">선택한 멤버를 마우스 오른쪽 단추로 클릭한 다음 상황에 맞는 메뉴에서 **형제 만들기**를 선택하여 형제 멤버를 만들거나 **자식 만들기**를 선택하여 자식 멤버를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="cea6f-114">Right-click the selected member and select either **Create Sibling**, to create a sibling member, or **Create Child**, to create a child member, from the context menu.</span></span>|  
|<span data-ttu-id="cea6f-115">선택한 멤버를 계층에서 위 또는 아래로 이동</span><span class="sxs-lookup"><span data-stu-id="cea6f-115">Move a selected member up or down the hierarchy.</span></span>|<span data-ttu-id="cea6f-116">멤버를 해당 부모 또는 자식 멤버로 끌거나 **도구 모음** 창에서 **들여쓰기** 또는 **내어쓰기** 를 클릭하여 선택한 멤버를 계층 수준에서 위 또는 아래로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="cea6f-116">Either drag the selected member to the appropriate parent or child member, or click **Increase Indent** or **Decrease Indent** on the **Toolbar** pane to move the selected member up or down the levels of the hierarchy.</span></span>|  
|<span data-ttu-id="cea6f-117">선택한 멤버 이름 바꾸기</span><span class="sxs-lookup"><span data-stu-id="cea6f-117">Rename a selected member.</span></span>|<span data-ttu-id="cea6f-118">선택한 멤버를 마우스 오른쪽 단추로 클릭한 다음 **이름 바꾸기**를 선택하거나 이미 선택한 멤버를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cea6f-118">Either right-click the selected member and select **Rename**, or click an already-selected member.</span></span>|  
|<span data-ttu-id="cea6f-119">멤버 속성 값 편집</span><span class="sxs-lookup"><span data-stu-id="cea6f-119">Edit member property values</span></span>|<span data-ttu-id="cea6f-120">선택한 멤버에 대해 선택한 멤버 속성에서 값을 두 번 클릭하여 편집합니다.</span><span class="sxs-lookup"><span data-stu-id="cea6f-120">Double-click the value in the selected member property for the selected member to edit the value.</span></span>|  
  
## <a name="options"></a><span data-ttu-id="cea6f-121">옵션</span><span class="sxs-lookup"><span data-stu-id="cea6f-121">Options</span></span>  
 <span data-ttu-id="cea6f-122">**현재 수준**</span><span class="sxs-lookup"><span data-stu-id="cea6f-122">**Current level**</span></span>  
 <span data-ttu-id="cea6f-123">**트리** 에서 현재 선택한 멤버가 속한 수준을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="cea6f-123">Displays the level to which the currently selected member in **Tree** belongs.</span></span>  
  
 <span data-ttu-id="cea6f-124">**Tree**</span><span class="sxs-lookup"><span data-stu-id="cea6f-124">**Tree**</span></span>  
 <span data-ttu-id="cea6f-125">현재 선택한 계층 및 언어의 멤버를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="cea6f-125">Displays the members of the currently selected hierarchy and language.</span></span>  
  
 <span data-ttu-id="cea6f-126">도구 모음 창의 **멤버 속성** 옵션에서 멤버 속성을 선택하면 각 멤버 속성이 열로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="cea6f-126">If member properties are selected from the **Member Properties** option of the Toolbar pane, each member property is displayed as a column.</span></span>  
  
 <span data-ttu-id="cea6f-127">쓰기 저장 모드를 설정하면 차원의 키 특성과 연결된 각 키 열에 대해 하나의 열이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="cea6f-127">If writeback mode is enabled, one column for each key column associated with the key attribute in the dimension is displayed.</span></span>  
  
## <a name="context-menu"></a><span data-ttu-id="cea6f-128">상황에 맞는 메뉴</span><span class="sxs-lookup"><span data-stu-id="cea6f-128">Context Menu</span></span>  
 <span data-ttu-id="cea6f-129">선택한 멤버에 대한 **수준 및 멤버** 창을 마우스 오른쪽 단추로 클릭하면 표시되는 상황에 맞는 메뉴에서 다음과 같은 옵션을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cea6f-129">The following options are available in the context menu displayed by right-clicking any part of the **Level and Members** pane for the selected member:</span></span>  
  
 <span data-ttu-id="cea6f-130">**형제 만들기**</span><span class="sxs-lookup"><span data-stu-id="cea6f-130">**Create sibling**</span></span>  
 <span data-ttu-id="cea6f-131">선택한 멤버와 같은 수준에서 새 멤버를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="cea6f-131">Creates a new member at the same level as the selected member.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="cea6f-132">이 옵션은 (All) 수준이 아닌 수준에서 멤버를 선택한 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cea6f-132">This option is enabled only if a member at a level other than the (All) level is selected.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="cea6f-133">이 옵션은 쓰기 저장 모드가 설정된 경우에만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="cea6f-133">This option is displayed only if writeback mode is enabled.</span></span>  
  
 <span data-ttu-id="cea6f-134">**자식 만들기**</span><span class="sxs-lookup"><span data-stu-id="cea6f-134">**Create child**</span></span>  
 <span data-ttu-id="cea6f-135">선택한 멤버의 다음 하위 수준에서 새 멤버를 선택한 멤버의 자식으로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="cea6f-135">Creates a new member at the next lower level as the selected member, as a child of the selected member.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="cea6f-136">이 옵션은 최하위 수준이 아닌 수준의 멤버를 선택한 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cea6f-136">This option is enabled only if a member at a level other than the lowest level is selected.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="cea6f-137">이 옵션은 쓰기 저장 모드가 설정된 경우에만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="cea6f-137">This option is displayed only if writeback mode is enabled.</span></span>  
  
 <span data-ttu-id="cea6f-138">**잘라내기**</span><span class="sxs-lookup"><span data-stu-id="cea6f-138">**Cut**</span></span>  
 <span data-ttu-id="cea6f-139">선택한 멤버를 클립보드로 복사하고 계층에서 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="cea6f-139">Copies the selected members to the clipboard and removes them from the hierarchy.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="cea6f-140">이 옵션은 All 멤버가 아닌 멤버를 선택한 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cea6f-140">This option is enabled only if a member other than the All member is selected.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="cea6f-141">이 옵션은 쓰기 저장 모드가 설정된 경우에만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="cea6f-141">This option is displayed only if writeback mode is enabled.</span></span>  
  
 <span data-ttu-id="cea6f-142">**붙여넣기**</span><span class="sxs-lookup"><span data-stu-id="cea6f-142">**Paste**</span></span>  
 <span data-ttu-id="cea6f-143">**잘라내기** 를 사용하여 이전에 제거한 멤버를 선택한 멤버 바로 뒤에 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="cea6f-143">Pastes members previously removed using **Cut** immediately after the selected member.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="cea6f-144">이 옵션은 쓰기 저장 모드가 설정된 경우에만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="cea6f-144">This option is displayed only if writeback mode is enabled.</span></span>  
  
 <span data-ttu-id="cea6f-145">**삭제**</span><span class="sxs-lookup"><span data-stu-id="cea6f-145">**Delete**</span></span>  
 <span data-ttu-id="cea6f-146">선택한 멤버를 계층에서 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="cea6f-146">Removes the selected members from the hierarchy.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="cea6f-147">이 옵션은 All 멤버가 아닌 멤버를 선택한 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cea6f-147">This option is enabled only if a member other than the All member is selected.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="cea6f-148">이 옵션은 쓰기 저장 모드가 설정된 경우에만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="cea6f-148">This option is displayed only if writeback mode is enabled.</span></span>  
  
 <span data-ttu-id="cea6f-149">**이름 바꾸기**</span><span class="sxs-lookup"><span data-stu-id="cea6f-149">**Rename**</span></span>  
 <span data-ttu-id="cea6f-150">선택한 멤버의 이름을 편집하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="cea6f-150">Select to edit the name of the selected member.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="cea6f-151">이 옵션은 All 멤버가 아닌 멤버를 선택한 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cea6f-151">This option is enabled only if a member other than the All member is selected.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="cea6f-152">이 옵션은 쓰기 저장 모드가 설정된 경우에만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="cea6f-152">This option is displayed only if writeback mode is enabled.</span></span>  
  
 <span data-ttu-id="cea6f-153">**멤버 필터**</span><span class="sxs-lookup"><span data-stu-id="cea6f-153">**Filter Members**</span></span>  
 <span data-ttu-id="cea6f-154">**멤버 필터** 대화 상자를 표시하고 선택한 계층에 대한 **수준 및 멤버**에 표시된 멤버를 필터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cea6f-154">Displays the **Filter Members** dialog box to filter members displayed in **Level and Members** for the selected hierarchy.</span></span> <span data-ttu-id="cea6f-155">**멤버 필터** 대화 상자에 대한 자세한 내용은 [멤버 필터 대화 상자&#40;Analysis Services - 다차원 데이터&#41;](filter-members-dialog-box-analysis-services-multidimensional-data.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cea6f-155">For more information about the **Filter Members** dialog box, see [Filter Members Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](filter-members-dialog-box-analysis-services-multidimensional-data.md).</span></span>  
  
 <span data-ttu-id="cea6f-156">**모두 확장**</span><span class="sxs-lookup"><span data-stu-id="cea6f-156">**Expand All**</span></span>  
 <span data-ttu-id="cea6f-157">**트리**에서 모든 멤버를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="cea6f-157">Expands all members in **Tree**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="cea6f-158">이 옵션은 최하위 수준이 아닌 수준의 멤버를 선택한 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cea6f-158">This option is enabled only if a member at a level other than the lowest level is selected.</span></span>  
  
 <span data-ttu-id="cea6f-159">**모두 축소**</span><span class="sxs-lookup"><span data-stu-id="cea6f-159">**Collapse All**</span></span>  
 <span data-ttu-id="cea6f-160">**트리**에서 모든 멤버를 축소합니다.</span><span class="sxs-lookup"><span data-stu-id="cea6f-160">Collapse all members in **Tree**.</span></span>  
  
 <span data-ttu-id="cea6f-161">**멤버 확장**</span><span class="sxs-lookup"><span data-stu-id="cea6f-161">**Expand Member**</span></span>  
 <span data-ttu-id="cea6f-162">**트리**에서 선택한 멤버를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="cea6f-162">Expand the selected member in **Tree**.</span></span>  
  
 <span data-ttu-id="cea6f-163">**멤버 축소**</span><span class="sxs-lookup"><span data-stu-id="cea6f-163">**Collapse Member**</span></span>  
 <span data-ttu-id="cea6f-164">**트리**에서 선택한 멤버를 축소합니다.</span><span class="sxs-lookup"><span data-stu-id="cea6f-164">Collapse the selected member in **Tree**.</span></span>  
  
 <span data-ttu-id="cea6f-165">**쓰기 저장(writeback)**</span><span class="sxs-lookup"><span data-stu-id="cea6f-165">**Writeback**</span></span>  
 <span data-ttu-id="cea6f-166">쓰기 저장 모드를 설정하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="cea6f-166">Select to enable writeback mode.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cea6f-167">참고 항목</span><span class="sxs-lookup"><span data-stu-id="cea6f-167">See Also</span></span>  
 <span data-ttu-id="cea6f-168">[도구 모음 &#40;브라우저 탭, 차원 디자이너&#41; &#40;Analysis Services 다차원 데이터&#41;](toolbar-browser-tab-dimension-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="cea6f-168">[Toolbar &#40;Browser Tab, Dimension Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](toolbar-browser-tab-dimension-designer-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="cea6f-169">브라우저 &#40;차원 디자이너&#41; &#40;Analysis Services 다차원 데이터&#41;</span><span class="sxs-lookup"><span data-stu-id="cea6f-169">Browser &#40;Dimension Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;</span></span>](browser-dimension-designer-analysis-services-multidimensional-data.md)  
  
  
