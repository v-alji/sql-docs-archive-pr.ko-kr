---
title: 계산 도구 (동작 탭, 큐브 디자이너) (Analysis Services 다차원 데이터) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.actionsview.calculationtoolspane.f1
ms.assetid: a3370370-43cd-4cc2-bb9f-c0d988b96f05
author: minewiskan
ms.author: owend
ms.openlocfilehash: 123fa38ea2decb6af914e93fcefda4508f08545e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648077"
---
# <a name="calculation-tools-actions-tab-cube-designer-analysis-services---multidimensional-data"></a><span data-ttu-id="002bc-102">계산 도구(동작 탭, 큐브 디자이너)(Analysis Services - 다차원 데이터)</span><span class="sxs-lookup"><span data-stu-id="002bc-102">Calculation Tools (Actions Tab, Cube Designer) (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="002bc-103">큐브 디자이너의 **동작** 탭에 있는 **계산 도구** 창을 사용하여 작업, 드릴스루 작업 및 보고 작업에 사용할 수 있는 메타데이터, 함수 및 템플릿을 탐색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="002bc-103">Use the **Calculation Tools** pane on the **Actions** tab in Cube Designer to explore metadata, functions, and templates available for use in actions, drillthrough actions, and report actions.</span></span>  
  
## <a name="options"></a><span data-ttu-id="002bc-104">옵션</span><span class="sxs-lookup"><span data-stu-id="002bc-104">Options</span></span>  
 <span data-ttu-id="002bc-105">**메타데이터**</span><span class="sxs-lookup"><span data-stu-id="002bc-105">**Metadata**</span></span>  
 <span data-ttu-id="002bc-106">선택한 큐브의 메타데이터를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="002bc-106">Displays the metadata for the selected cube.</span></span>  
  
 <span data-ttu-id="002bc-107">선택한 요소를 **동작 폼 편집기**, **드릴스루 동작 폼 편집기**또는 **보고서 동작 폼 편집기** 창으로 끌어 선택한 위치에 해당 요소에 대한 MDX(Multidimensional Expressions) 구문을 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="002bc-107">Drag a selected element to the **Action Form Editor**, **Drillthrough Action Form Editor**, or **Report Action Form Editor** pane to include the Multidimensional Expressions (MDX) syntax for that element at the selected location in the pane.</span></span>  
  
 <span data-ttu-id="002bc-108">**함수**</span><span class="sxs-lookup"><span data-stu-id="002bc-108">**Functions**</span></span>  
 <span data-ttu-id="002bc-109">식과 조건에 사용 가능한 함수를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="002bc-109">Displays the functions available for expressions and conditions.</span></span>  
  
 <span data-ttu-id="002bc-110">선택한 요소를 **동작 폼 편집기**, **드릴스루 작업 폼 편집기**또는 **보고 작업 폼 편집기** 창으로 끌어 그 위치에 해당 요소에 대한 MDX 구문을 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="002bc-110">Drag a selected element to the **Action Form Editor**, **Drillthrough Action Form Editor**, or **Report Action Form Editor** pane to include the MDX syntax for that element at the selected location in the pane.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="002bc-111">프로젝트 모드에서 **계산 도구** 대화 상자는 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]에 포함된 MDXFunctions.xml이라는 XML 파일에서 이 옵션에 대한 정보를 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="002bc-111">In project mode, the **Calculation Tools** dialog box reads information for this option from an XML file named MDXFunctions.xml, included with [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="002bc-112">온라인 모드에서 이 옵션에 대한 정보를 해당 인스턴스의 MDSCHEMA_FUNCTIONS 스키마 행 집합에서 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="002bc-112">In online mode, information for this option is retrieved from the MDSCHEMA_FUNCTIONS schema rowset for the instance.</span></span>  
  
 <span data-ttu-id="002bc-113">**템플릿**</span><span class="sxs-lookup"><span data-stu-id="002bc-113">**Templates**</span></span>  
 <span data-ttu-id="002bc-114">동작에 사용 가능한 미리 정의된 템플릿을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="002bc-114">Displays the predefined templates available for actions.</span></span>  
  
 <span data-ttu-id="002bc-115">선택한 요소를 **동작 폼 편집기**, **드릴스루 작업 폼 편집기**또는 **보고 작업 폼 편집기** 창으로 끌어 그 위치에 해당 요소에 대한 MDX 구문을 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="002bc-115">Drag a selected element to the **Action Form Editor**, **Drillthrough Action Form Editor**, or **Report Action Form Editor** pane to include the MDX syntax for that element at the selected location in the pane.</span></span>  
  
## <a name="context-menu"></a><span data-ttu-id="002bc-116">상황에 맞는 메뉴</span><span class="sxs-lookup"><span data-stu-id="002bc-116">Context Menu</span></span>  
 <span data-ttu-id="002bc-117">다음 옵션은 **계산 도구** 창에서 요소를 마우스 오른쪽 단추로 클릭하면 표시되는 상황에 맞는 메뉴를 통해 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="002bc-117">The following options are available in the context menu displayed by right-clicking an element in the **Calculation Tools** pane:</span></span>  
  
|<span data-ttu-id="002bc-118">옵션</span><span class="sxs-lookup"><span data-stu-id="002bc-118">Option</span></span>|<span data-ttu-id="002bc-119">정의</span><span class="sxs-lookup"><span data-stu-id="002bc-119">Definition</span></span>|  
|------------|----------------|  
|<span data-ttu-id="002bc-120">**복사**</span><span class="sxs-lookup"><span data-stu-id="002bc-120">**Copy**</span></span>|<span data-ttu-id="002bc-121">**메타데이터** 또는 **함수** 에서 선택한 요소를 클립보드로 복사하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="002bc-121">Select to copy the selected element in **Metadata** or **Functions** to the Clipboard.</span></span><br /><br /> <span data-ttu-id="002bc-122">**템플릿이** 선택 된 경우에는이 옵션이 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="002bc-122">Note that this option is not displayed if **Templates** is selected.</span></span> <span data-ttu-id="002bc-123">또한 **메타 데이터** 에 표시 된 차원의 **집합** 폴더 **또는 함수에**표시 된 함수의 함수 그룹 폴더와 같이 선택한 멤버를 복사할 수 없는 경우에는이 옵션을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="002bc-123">Also note that this option is disabled if the selected member cannot be copied, such as the **Sets** folder of a dimension displayed in **Metadata** or the function group folder for a function displayed in **Functions**.</span></span>|  
|<span data-ttu-id="002bc-124">**멤버 필터**</span><span class="sxs-lookup"><span data-stu-id="002bc-124">**Filter Members**</span></span>|<span data-ttu-id="002bc-125">**멤버 필터** 대화 상자를 표시하고 **메타데이터**에서 선택한 요소에 대해 표시된 멤버를 필터링하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="002bc-125">Select to display the **Filter Members** dialog box and filter members displayed for the selected element in **Metadata**.</span></span> <span data-ttu-id="002bc-126">**멤버 필터** 대화 상자에 대한 자세한 내용은 [멤버 필터 대화 상자&#40;Analysis Services - 다차원 데이터&#41;](filter-members-dialog-box-analysis-services-multidimensional-data.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="002bc-126">For more information about the **Filter Members** dialog box, see [Filter Members Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](filter-members-dialog-box-analysis-services-multidimensional-data.md).</span></span><br /><br /> <span data-ttu-id="002bc-127">이 옵션은 **메타 데이터** 를 선택한 경우에만 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="002bc-127">Note that this option is displayed only if **Metadata** is selected.</span></span> <span data-ttu-id="002bc-128">또한이 옵션은 **메타 데이터**에서 특성의 수준을 선택한 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="002bc-128">Also note that this option is enabled only if a level for an attribute is selected in **Metadata**.</span></span>|  
|<span data-ttu-id="002bc-129">**템플릿 추가**</span><span class="sxs-lookup"><span data-stu-id="002bc-129">**Add Template**</span></span>|<span data-ttu-id="002bc-130">큐브 및 화면 표시에 대해 선택한 템플릿을 기반으로 새 동작, 드릴스루 작업 또는 보고 작업을 각각 **작업 폼 편집기**, **드릴스루 작업 폼 편집기**또는 **보고 작업 폼 편집기**에 추가하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="002bc-130">Select to add a new action, drillthrough action, or report action based on the selected template to the cube and display, respectively, the **Action Form Editor**, **Drillthrough Action Form Editor**, or **Report Action Form Editor**.</span></span><br /><br /> <span data-ttu-id="002bc-131">참고:이 옵션은 **메타 데이터** 를 선택한 경우에만 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="002bc-131">Note: This option is displayed only if **Metadata** is selected.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="002bc-132">참고 항목</span><span class="sxs-lookup"><span data-stu-id="002bc-132">See Also</span></span>  
 <span data-ttu-id="002bc-133">[MDX 스크립팅 기본 사항 &#40;Analysis Services&#41;](multidimensional-models/mdx/mdx-scripting-fundamentals-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="002bc-133">[MDX Scripting Fundamentals &#40;Analysis Services&#41;](multidimensional-models/mdx/mdx-scripting-fundamentals-analysis-services.md) </span></span>  
 <span data-ttu-id="002bc-134">[큐브 디자이너 Analysis Services&#41; &#40;&#40;작업은 다차원 데이터&#41;](actions-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="002bc-134">[Actions &#40;Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](actions-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="002bc-135">[도구 모음 &#40;동작 탭, 큐브 디자이너&#41; &#40;Analysis Services 다차원 데이터&#41;](toolbar-actions-tab-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="002bc-135">[Toolbar &#40;Actions Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](toolbar-actions-tab-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="002bc-136">[동작 구성 도우미 &#40;동작 탭, 큐브 디자이너&#41; &#40;Analysis Services 다차원 데이터&#41;](action-organizer-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="002bc-136">[Action Organizer &#40;Actions Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](action-organizer-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="002bc-137">[작업 폼 편집기 &#40;동작 탭, 큐브 디자이너&#41; &#40;Analysis Services 다차원 데이터&#41;](action-form-editor-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="002bc-137">[Action Form Editor &#40;Actions Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](action-form-editor-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="002bc-138">[드릴스루 동작 폼 편집기 &#40;동작 탭, 큐브 디자이너&#41; &#40;Analysis Services 다차원 데이터&#41;](drillthrough-action-form-editor-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="002bc-138">[Drillthrough Action Form Editor &#40;Actions Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](drillthrough-action-form-editor-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="002bc-139">보고서 동작 폼 편집기 &#40;동작 탭, 큐브 디자이너&#41; &#40;Analysis Services-다차원 데이터&#41;</span><span class="sxs-lookup"><span data-stu-id="002bc-139">Report Action Form Editor &#40;Actions Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;</span></span>](report-action-form-editor-cube-designer-analysis-services-multidimensional-data.md)  
  
  
