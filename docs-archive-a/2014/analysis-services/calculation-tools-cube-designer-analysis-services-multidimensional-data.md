---
title: 계산 도구 (계산 탭, 큐브 디자이너) (Analysis Services 다차원 데이터) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.calculationsview.calculationtoolspane.f1
ms.assetid: b1aa8a1a-6532-45d2-8f53-d3e211d7197a
author: minewiskan
ms.author: owend
ms.openlocfilehash: 6701a15a7d773a90e48ec39dc976b9ef579c9ec8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648078"
---
# <a name="calculation-tools-calculations-tab-cube-designer-analysis-services---multidimensional-data"></a><span data-ttu-id="27eec-102">계산 도구(계산 탭, 큐브 디자이너)(Analysis Services - 다차원 데이터)</span><span class="sxs-lookup"><span data-stu-id="27eec-102">Calculation Tools (Calculations Tab, Cube Designer) (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="27eec-103">큐브 디자이너의 **계산** 탭에 있는 **계산 도구** 창을 사용하여 계산에 사용할 수 있는 메타데이터, 함수 및 템플릿을 탐색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="27eec-103">Use the **Calculation Tools** pane on the **Calculations** tab in Cube Designer to explore metadata, functions, and templates available for use in calculations.</span></span>  
  
## <a name="options"></a><span data-ttu-id="27eec-104">옵션</span><span class="sxs-lookup"><span data-stu-id="27eec-104">Options</span></span>  
 <span data-ttu-id="27eec-105">**메타데이터**</span><span class="sxs-lookup"><span data-stu-id="27eec-105">**Metadata**</span></span>  
 <span data-ttu-id="27eec-106">선택한 큐브의 메타데이터를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="27eec-106">Displays the metadata for the selected cube.</span></span>  
  
 <span data-ttu-id="27eec-107">선택한 요소를 스크립트 편집기, 계산 멤버 폼 편집기 또는 명명된 집합 폼 편집기 창으로 끌어 그 위치에 해당 요소에 대한 MDX(Multidimensional Expressions) 구문을 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="27eec-107">Drag a selected element to the Script Editor, Calculated Member Form Editor, or Named Set Form Editor pane to include the Multidimensional Expressions (MDX) syntax for that element at the selected location in the pane.</span></span>  
  
 <span data-ttu-id="27eec-108">**함수**</span><span class="sxs-lookup"><span data-stu-id="27eec-108">**Functions**</span></span>  
 <span data-ttu-id="27eec-109">식과 조건에 사용 가능한 함수를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="27eec-109">Displays the functions available for expressions and conditions.</span></span>  
  
 <span data-ttu-id="27eec-110">선택한 요소를 **스크립트 편집기**, **계산 멤버 폼 편집기**또는 **명명된 집합 폼 편집기** 창으로 끌어 그 위치에 해당 요소에 대한 MDX 구문을 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="27eec-110">Drag a selected element to the **Script Editor**, **Calculated Member Form Editor**, or **Named Set Form Editor** pane to include the MDX syntax for that element at the selected location in the pane.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="27eec-111">프로젝트 모드에서 **계산 도구** 대화 상자는 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]에 포함된 MDXFunctions.xml이라는 XML 파일에서 이 옵션에 대한 정보를 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="27eec-111">In project mode, the **Calculation Tools** dialog box reads information for this option from an XML file named MDXFunctions.xml, included with [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="27eec-112">온라인 모드에서 이 옵션에 대한 정보를 해당 인스턴스의 MDSCHEMA_FUNCTIONS 스키마 행 집합에서 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="27eec-112">In online mode, information for this option is retrieved from the MDSCHEMA_FUNCTIONS schema rowset for the instance.</span></span>  
  
 <span data-ttu-id="27eec-113">**템플릿**</span><span class="sxs-lookup"><span data-stu-id="27eec-113">**Templates**</span></span>  
 <span data-ttu-id="27eec-114">계산 멤버, 명명된 집합 및 스크립트 명령에 사용 가능한 미리 정의된 템플릿을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="27eec-114">Displays the predefined templates available for calculated members, named sets, and script commands.</span></span>  
  
 <span data-ttu-id="27eec-115">선택한 요소를 **스크립트 편집기**, **계산 멤버 폼 편집기**또는 **명명된 집합 폼 편집기** 창으로 끌어 그 위치에 해당 요소에 대한 MDX 구문을 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="27eec-115">Drag a selected element to the **Script Editor**, **Calculated Member Form Editor**, or **Named Set Form Editor** pane to include the MDX syntax for that element at the selected location in the pane.</span></span>  
  
## <a name="context-menu"></a><span data-ttu-id="27eec-116">상황에 맞는 메뉴</span><span class="sxs-lookup"><span data-stu-id="27eec-116">Context Menu</span></span>  
 <span data-ttu-id="27eec-117">다음 옵션은 **계산 도구** 창에서 요소를 마우스 오른쪽 단추로 클릭하면 표시되는 상황에 맞는 메뉴를 통해 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="27eec-117">The following options are available in the context menu displayed by right-clicking an element in the **Calculation Tools** pane:</span></span>  
  
 <span data-ttu-id="27eec-118">**복사**</span><span class="sxs-lookup"><span data-stu-id="27eec-118">**Copy**</span></span>  
 <span data-ttu-id="27eec-119">**메타데이터** 또는 **함수** 에서 선택한 요소를 클립보드로 복사하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="27eec-119">Select to copy the selected element in **Metadata** or **Functions** to the Clipboard.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="27eec-120"> 이 옵션은 **템플릿** 을 선택하면 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="27eec-120">This option is not displayed if **Templates** is selected.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="27eec-121">**메타데이터** 에 표시된 차원의 **집합** 폴더 또는 **함수**에 표시된 함수의 함수 그룹 폴더와 같이 선택한 멤버를 복사할 수 없는 경우에는 이 옵션을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="27eec-121">This option is disabled if the selected member cannot be copied, such as the **Sets** folder of a dimension displayed in **Metadata** or the function group folder for a function displayed in **Functions**.</span></span>  
  
 <span data-ttu-id="27eec-122">**멤버 필터**</span><span class="sxs-lookup"><span data-stu-id="27eec-122">**Filter Members**</span></span>  
 <span data-ttu-id="27eec-123">**멤버 필터** 대화 상자를 표시하고 **메타데이터**에서 선택한 요소에 대해 표시된 멤버를 필터링하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="27eec-123">Select to display the **Filter Members** dialog box and filter members displayed for the selected element in **Metadata**.</span></span> <span data-ttu-id="27eec-124">**멤버 필터** 대화 상자에 대한 자세한 내용은 [멤버 필터 대화 상자&#40;Analysis Services - 다차원 데이터&#41;](filter-members-dialog-box-analysis-services-multidimensional-data.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="27eec-124">For more information about the **Filter Members** dialog box, see [Filter Members Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](filter-members-dialog-box-analysis-services-multidimensional-data.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="27eec-125"> 이 옵션은 **메타데이터** 를 선택한 경우에만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="27eec-125">This option is displayed only if **Metadata** is selected.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="27eec-126"> 이 옵션은 **메타데이터**에서 특성의 수준을 선택한 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="27eec-126">This option is enabled only if a level for an attribute is selected in **Metadata**.</span></span>  
  
 <span data-ttu-id="27eec-127">**템플릿 추가**</span><span class="sxs-lookup"><span data-stu-id="27eec-127">**Add Template**</span></span>  
 <span data-ttu-id="27eec-128">폼 보기에서 선택한 템플릿을 기반으로 새 계산 멤버, 명명된 집합 또는 스크립트 명령을 큐브 스크립트에 추가하고 해당 명령에 맞게 **스크립트 편집기**, **계산 멤버 폼 편집기**또는 **명명된 집합 폼 편집기** 를 표시하거나 스크립트 보기에서 **스크립트 편집기** 창의 내용을 큐브 스크립트의 명령 위치로 스크롤하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="27eec-128">Select to add a new calculated member, named set, or script command based on the selected template to the cube script and display the **Script Editor**, **Calculated Member Form Editor**, or **Named Set Form Editor** as appropriate for that command (in form view) or to scroll the contents of the **Script Editor** pane to the location of the command in the cube script (in script view).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="27eec-129"> 이 옵션은 **메타데이터** 를 선택한 경우에만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="27eec-129">This option is displayed only if **Metadata** is selected.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27eec-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="27eec-130">See Also</span></span>  
 <span data-ttu-id="27eec-131">[큐브 디자이너 &#40;Analysis Services 다차원 데이터&#41;](cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="27eec-131">[Cube Designer &#40;Analysis Services - Multidimensional Data&#41;](cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="27eec-132">[도구 모음 &#40;계산 탭, 큐브 디자이너&#41; &#40;Analysis Services 다차원 데이터&#41;](toolbar-calculations-tab-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="27eec-132">[Toolbar &#40;Calculations Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](toolbar-calculations-tab-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="27eec-133">[스크립트 구성 도우미 &#40;계산 탭, 큐브 디자이너&#41; &#40;Analysis Services 다차원 데이터&#41;](script-organizer-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="27eec-133">[Script Organizer &#40;Calculations Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](script-organizer-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="27eec-134">[계산 멤버 폼 편집기 &#40;계산 탭, 큐브 디자이너&#41; &#40;Analysis Services 다차원 데이터&#41;](calculated-member-form-editor-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="27eec-134">[Calculated Member Form Editor &#40;Calculations Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](calculated-member-form-editor-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="27eec-135">[명명 된 집합 폼 편집기 &#40;계산 탭, 큐브 디자이너&#41; &#40;Analysis Services 다차원 데이터&#41;](named-set-form-editor-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="27eec-135">[Named Set Form Editor &#40;Calculations Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](named-set-form-editor-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="27eec-136">[스크립트 편집기 &#40;계산 탭, 큐브 디자이너&#41; &#40;Analysis Services 다차원 데이터&#41;](script-editor-calculations-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="27eec-136">[Script Editor &#40;Calculations Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](script-editor-calculations-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="27eec-137">큐브 디자이너의 계산 &#40;다차원 데이터&#41; &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="27eec-137">Calculations &#40;Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;</span></span>](calculations-cube-designer-analysis-services-multidimensional-data.md)  
  
  
