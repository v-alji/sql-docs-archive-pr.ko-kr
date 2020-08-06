---
title: 스크립트 구성 도우미 (계산 탭, 큐브 디자이너) (Analysis Services 다차원 데이터) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.calculationsview.scriptorganizerpane.f1
ms.assetid: 92624ca4-de67-4ebd-aab2-8adb527d327e
author: minewiskan
ms.author: owend
ms.openlocfilehash: 4ee8ccb491995176dc56da90e4cbf48961e30e98
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647906"
---
# <a name="script-organizer-calculations-tab-cube-designer-analysis-services---multidimensional-data"></a><span data-ttu-id="33f84-102">스크립트 구성 도우미(계산 탭, 큐브 디자이너)(Analysis Services - 다차원 데이터)</span><span class="sxs-lookup"><span data-stu-id="33f84-102">Script Organizer (Calculations Tab, Cube Designer) (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="33f84-103">큐브 디자이너의 **계산** 탭에 있는 **스크립트 구성 도우미** 창을 사용하여 지정한 큐브에 대한 큐브 스크립트에 포함된 계산 멤버, 명명된 집합 및 스크립트 명령에 액세스하고 다시 정렬할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="33f84-103">Use the **Script Organizer** pane on the **Calculations** tab in Cube Designer to access and reorder the calculated members, named sets, and script commands contained in the cube script for the specified cube.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="33f84-104">이 창은 폼 보기에 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="33f84-104">This pane is not displayed in form view.</span></span>  
  
## <a name="options"></a><span data-ttu-id="33f84-105">옵션</span><span class="sxs-lookup"><span data-stu-id="33f84-105">Options</span></span>  
 <span data-ttu-id="33f84-106">**Step**</span><span class="sxs-lookup"><span data-stu-id="33f84-106">**Step**</span></span>  
 <span data-ttu-id="33f84-107">큐브 스크립트에서 계산 멤버, 명명된 집합 및 스크립트 명령의 실행 순서를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="33f84-107">Displays the execution order of the calculated members, named sets, and script commands within the cube script.</span></span>  
  
 <span data-ttu-id="33f84-108">계산의 실행 순서를 변경하려면 **도구 모음** 창 또는 상황에 맞는 메뉴에서 **위로 이동** 또는 **아래로 이동** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="33f84-108">Click **Move Up** or **Move Down** in the **Toolbar** pane or context menu to change the execution order of the calculations.</span></span>  
  
 <span data-ttu-id="33f84-109">**형식**</span><span class="sxs-lookup"><span data-stu-id="33f84-109">**Type**</span></span>  
 <span data-ttu-id="33f84-110">계산을 계산 멤버, 명명된 집합 또는 스크립트 명령으로 식별하는 아이콘을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="33f84-110">Displays an icon that identifies the calculation as a calculated member, a named set, or a script command.</span></span>  
  
 <span data-ttu-id="33f84-111">**명령**</span><span class="sxs-lookup"><span data-stu-id="33f84-111">**Command**</span></span>  
 <span data-ttu-id="33f84-112">명령의 이름(계산 멤버 및 명명된 집합의 경우) 또는 계산의 첫 줄(스크립트 명령의 경우)을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="33f84-112">Displays the name of the command (for calculated members and named sets) or the first line of the calculation (for script commands.)</span></span>  
  
 <span data-ttu-id="33f84-113">명령을 선택하여 폼 보기에서 해당 명령에 적합한 **스크립트 편집기**, **계산 멤버 폼 편집기**또는 **명명된 집합 폼 편집기** 를 표시하거나 스크립트 보기에서 **스크립트 편집기** 창의 내용을 큐브 스크립트의 명령 위치로 스크롤합니다.</span><span class="sxs-lookup"><span data-stu-id="33f84-113">Select a command to display the **Script Editor**, **Calculated Member Form Editor**, or **Named Set Form Editor** as appropriate for that command (in form view) or to scroll the contents of the **Script Editor** pane to the location of the command in the cube script (in script view).</span></span>  
  
## <a name="context-menu"></a><span data-ttu-id="33f84-114">상황에 맞는 메뉴</span><span class="sxs-lookup"><span data-stu-id="33f84-114">Context Menu</span></span>  
 <span data-ttu-id="33f84-115">다음 옵션은 **스크립트 구성 도우미** 창에서 명령을 마우스 오른쪽 단추로 클릭하면 표시되는 상황에 맞는 메뉴를 통해 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="33f84-115">The following options are available in the context menu displayed by right-clicking a command in the **Script Organizer** pane:</span></span>  
  
|<span data-ttu-id="33f84-116">옵션</span><span class="sxs-lookup"><span data-stu-id="33f84-116">Option</span></span>|<span data-ttu-id="33f84-117">정의</span><span class="sxs-lookup"><span data-stu-id="33f84-117">Definition</span></span>|  
|------------|----------------|  
|<span data-ttu-id="33f84-118">**새 계산 멤버**</span><span class="sxs-lookup"><span data-stu-id="33f84-118">**New Calculated Member**</span></span>|<span data-ttu-id="33f84-119">**계산 멤버 폼 편집기** 를 표시하고 새 계산 멤버를 만들려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="33f84-119">Select to display the **Calculated Member Form Editor** and create a new calculated member.</span></span> <span data-ttu-id="33f84-120">**계산 멤버 폼 편집기**에 대 한 자세한 내용은 계산 [멤버 폼 편집기 &#40;계산 탭, 큐브 디자이너&#41; &#40;Analysis Services 다차원 데이터&#41;](calculated-member-form-editor-cube-designer-analysis-services-multidimensional-data.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="33f84-120">For more information about the **Calculated Member Form Editor**, see [Calculated Member Form Editor &#40;Calculations Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](calculated-member-form-editor-cube-designer-analysis-services-multidimensional-data.md).</span></span>|  
|<span data-ttu-id="33f84-121">**새 명명된 집합**</span><span class="sxs-lookup"><span data-stu-id="33f84-121">**New Named Set**</span></span>|<span data-ttu-id="33f84-122">**명명된 집합 폼 편집기** 를 표시하고 새 명명된 집합을 만들려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="33f84-122">Select to display the **Named Set Form Editor** and create a new named set.</span></span> <span data-ttu-id="33f84-123">**명명 된 집합 폼 편집기**에 대 한 자세한 내용은 [명명 된 집합 폼 편집기 &#40;계산 탭, 큐브 디자이너&#41; &#40;Analysis Services-다차원 데이터&#41;](named-set-form-editor-cube-designer-analysis-services-multidimensional-data.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="33f84-123">For more information about the **Named Set Form Editor**, see [Named Set Form Editor &#40;Calculations Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](named-set-form-editor-cube-designer-analysis-services-multidimensional-data.md).</span></span>|  
|<span data-ttu-id="33f84-124">**새 스크립트 명령**</span><span class="sxs-lookup"><span data-stu-id="33f84-124">**New Script Command**</span></span>|<span data-ttu-id="33f84-125">**스크립트 편집기** 를 표시하고 새 스크립트 명령을 만들려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="33f84-125">Select to display the **Script Editor** and create a new script command.</span></span> <span data-ttu-id="33f84-126">**스크립트 편집기**에 대 한 자세한 내용은 [스크립트 편집기 &#40;계산 탭, 큐브 디자이너&#41; &#40;Analysis Services-다차원 데이터&#41;](script-editor-calculations-cube-designer-analysis-services-multidimensional-data.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="33f84-126">For more information about the **Script Editor**, see [Script Editor &#40;Calculations Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](script-editor-calculations-cube-designer-analysis-services-multidimensional-data.md).</span></span>|  
|<span data-ttu-id="33f84-127">**위로 이동**</span><span class="sxs-lookup"><span data-stu-id="33f84-127">**Move Up**</span></span>|<span data-ttu-id="33f84-128">선택한 계산을 한 단계 위로 이동하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="33f84-128">Select to move the selected calculation up one place.</span></span><br /><br /> <span data-ttu-id="33f84-129">참고: 선택한 계산을 더 이상 이동할 수 없는 경우 이 옵션을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="33f84-129">Note: This option is disabled if the selected calculation cannot be moved further.</span></span>|  
|<span data-ttu-id="33f84-130">**아래로 이동**</span><span class="sxs-lookup"><span data-stu-id="33f84-130">**Move Down**</span></span>|<span data-ttu-id="33f84-131">선택한 계산을 한 단계 아래로 이동하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="33f84-131">Select to move the selected calculation down one place.</span></span><br /><br /> <span data-ttu-id="33f84-132">참고: 선택한 계산을 더 이상 이동할 수 없는 경우 이 옵션을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="33f84-132">Note: This option is disabled if the selected calculation cannot be moved further.</span></span>|  
|<span data-ttu-id="33f84-133">**삭제**</span><span class="sxs-lookup"><span data-stu-id="33f84-133">**Delete**</span></span>|<span data-ttu-id="33f84-134">선택한 계산을 삭제하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="33f84-134">Select to delete the selected calculation.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="33f84-135">참고 항목</span><span class="sxs-lookup"><span data-stu-id="33f84-135">See Also</span></span>  
 <span data-ttu-id="33f84-136">[큐브 디자이너 &#40;Analysis Services 다차원 데이터&#41;](cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="33f84-136">[Cube Designer &#40;Analysis Services - Multidimensional Data&#41;](cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="33f84-137">[도구 모음 &#40;계산 탭, 큐브 디자이너&#41; &#40;Analysis Services 다차원 데이터&#41;](toolbar-calculations-tab-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="33f84-137">[Toolbar &#40;Calculations Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](toolbar-calculations-tab-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="33f84-138">[계산 도구 &#40;계산 탭, 큐브 디자이너&#41; &#40;Analysis Services 다차원 데이터&#41;](calculation-tools-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="33f84-138">[Calculation Tools &#40;Calculations Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](calculation-tools-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="33f84-139">[계산 멤버 폼 편집기 &#40;계산 탭, 큐브 디자이너&#41; &#40;Analysis Services 다차원 데이터&#41;](calculated-member-form-editor-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="33f84-139">[Calculated Member Form Editor &#40;Calculations Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](calculated-member-form-editor-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="33f84-140">[명명 된 집합 폼 편집기 &#40;계산 탭, 큐브 디자이너&#41; &#40;Analysis Services 다차원 데이터&#41;](named-set-form-editor-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="33f84-140">[Named Set Form Editor &#40;Calculations Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](named-set-form-editor-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="33f84-141">[스크립트 편집기 &#40;계산 탭, 큐브 디자이너&#41; &#40;Analysis Services 다차원 데이터&#41;](script-editor-calculations-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="33f84-141">[Script Editor &#40;Calculations Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](script-editor-calculations-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="33f84-142">큐브 디자이너의 계산 &#40;다차원 데이터&#41; &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="33f84-142">Calculations &#40;Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;</span></span>](calculations-cube-designer-analysis-services-multidimensional-data.md)  
  
  
