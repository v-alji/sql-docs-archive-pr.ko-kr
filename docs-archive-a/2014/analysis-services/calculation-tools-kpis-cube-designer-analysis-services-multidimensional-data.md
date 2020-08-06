---
title: 계산 도구 (Kpi 탭, 큐브 디자이너) (Analysis Services 다차원 데이터) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.kpisview.calculationtoolspane.f1
ms.assetid: c030c725-7763-4c23-9988-4b274a88fc31
author: minewiskan
ms.author: owend
ms.openlocfilehash: 7bb8470173b0a413795fb7b5e3213bb50aa8ee43
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648076"
---
# <a name="calculation-tools-kpis-tab-cube-designer-analysis-services---multidimensional-data"></a><span data-ttu-id="a9c89-102">계산 도구(KPI 탭, 큐브 디자이너)(Analysis Services - 다차원 데이터)</span><span class="sxs-lookup"><span data-stu-id="a9c89-102">Calculation Tools (KPIs Tab, Cube Designer) (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="a9c89-103">큐브 디자이너의 **KPI** 탭에 있는 **계산 도구** 창을 사용하여 KPI(핵심 성과 지표)에 사용할 수 있는 메타데이터, 함수 및 템플릿을 탐색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a9c89-103">Use the **Calculation Tools** pane on the **KPIs** tab in Cube Designer to explore metadata, functions, and templates available for use in Key Performance Indicators (KPIs).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a9c89-104">이 창은 폼 보기에만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a9c89-104">This pane is displayed only in form view.</span></span>  
  
## <a name="options"></a><span data-ttu-id="a9c89-105">옵션</span><span class="sxs-lookup"><span data-stu-id="a9c89-105">Options</span></span>  
 <span data-ttu-id="a9c89-106">**메타데이터**</span><span class="sxs-lookup"><span data-stu-id="a9c89-106">**Metadata**</span></span>  
 <span data-ttu-id="a9c89-107">선택한 큐브의 메타데이터를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="a9c89-107">Displays the metadata for the selected cube.</span></span>  
  
 <span data-ttu-id="a9c89-108">해당 요소에 대한 MDX(Multidimensional Expression) 구문을 창에서 선택한 위치에 포함시키려면 선택한 요소를 **KPI 폼 편집기** 창으로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="a9c89-108">Drag a selected element to the **KPI Form Editor** pane to include the Multidimensional Expressions (MDX) syntax for that element at the selected location in the pane.</span></span>  
  
 <span data-ttu-id="a9c89-109">**함수**</span><span class="sxs-lookup"><span data-stu-id="a9c89-109">**Functions**</span></span>  
 <span data-ttu-id="a9c89-110">식과 조건에 사용 가능한 함수를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="a9c89-110">Displays the functions available for expressions and conditions.</span></span>  
  
 <span data-ttu-id="a9c89-111">선택한 요소를 **KPI 폼 편집기** 창으로 끌어 창에서 선택한 위치에 해당 요소에 대한 MDX 구문을 포함시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a9c89-111">Drag a selected element to the **KPI Form Editor** pane to include the MDX syntax for that element at the selected location in the pane.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a9c89-112">프로젝트 모드에서 **계산 도구** 대화 상자는 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]에 포함된 MDXFunctions.xml이라는 XML 파일에서 이 옵션에 대한 정보를 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="a9c89-112">In project mode, the **Calculation Tools** dialog box reads information for this option from an XML file named MDXFunctions.xml, included with [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="a9c89-113">온라인 모드에서 이 옵션에 대한 정보를 해당 인스턴스의 MDSCHEMA_FUNCTIONS 스키마 행 집합에서 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="a9c89-113">In online mode, information for this option is retrieved from the MDSCHEMA_FUNCTIONS schema rowset for the instance.</span></span>  
  
 <span data-ttu-id="a9c89-114">**템플릿**</span><span class="sxs-lookup"><span data-stu-id="a9c89-114">**Templates**</span></span>  
 <span data-ttu-id="a9c89-115">KPI에 사용할 수 있는 미리 정의된 템플릿을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="a9c89-115">Displays the predefined templates available for KPIs.</span></span>  
  
 <span data-ttu-id="a9c89-116">선택한 요소를 **KPI 폼 편집기** 창으로 끌어 창에서 선택한 위치에 해당 요소에 대한 MDX 구문을 포함시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a9c89-116">Drag a selected element to the **KPI Form Editor** pane to include the MDX syntax for that element at the selected location in the pane.</span></span>  
  
## <a name="context-menu"></a><span data-ttu-id="a9c89-117">상황에 맞는 메뉴</span><span class="sxs-lookup"><span data-stu-id="a9c89-117">Context Menu</span></span>  
 <span data-ttu-id="a9c89-118">다음 옵션은 **계산 도구** 창에서 요소를 마우스 오른쪽 단추로 클릭하면 표시되는 상황에 맞는 메뉴를 통해 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a9c89-118">The following options are available in the context menu displayed by right-clicking an element in the **Calculation Tools** pane:</span></span>  
  
 <span data-ttu-id="a9c89-119">**복사**</span><span class="sxs-lookup"><span data-stu-id="a9c89-119">**Copy**</span></span>  
 <span data-ttu-id="a9c89-120">**메타데이터** 또는 **함수** 에서 선택한 요소를 클립보드로 복사하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a9c89-120">Select to copy the selected element in **Metadata** or **Functions** to the Clipboard.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a9c89-121"> 이 옵션은 **템플릿** 을 선택하면 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a9c89-121">This option is not displayed if **Templates** is selected.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a9c89-122">**메타데이터** 에 표시된 차원의 **집합** 폴더 또는 **함수**에 표시된 함수의 함수 그룹 폴더와 같이 선택한 멤버를 복사할 수 없는 경우에는 이 옵션을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a9c89-122">This option is disabled if the selected member cannot be copied, such as the **Sets** folder of a dimension displayed in **Metadata** or the function group folder for a function displayed in **Functions**.</span></span>  
  
 <span data-ttu-id="a9c89-123">**멤버 필터**</span><span class="sxs-lookup"><span data-stu-id="a9c89-123">**Filter Members**</span></span>  
 <span data-ttu-id="a9c89-124">**멤버 필터** 대화 상자를 표시하고 **메타데이터**에서 선택한 요소에 대해 표시된 멤버를 필터링하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a9c89-124">Select to display the **Filter Members** dialog box and filter members displayed for the selected element in **Metadata**.</span></span> <span data-ttu-id="a9c89-125">**멤버 필터** 대화 상자에 대한 자세한 내용은 [멤버 필터 대화 상자&#40;Analysis Services - 다차원 데이터&#41;](filter-members-dialog-box-analysis-services-multidimensional-data.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a9c89-125">For more information about the **Filter Members** dialog box, see [Filter Members Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](filter-members-dialog-box-analysis-services-multidimensional-data.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a9c89-126"> 이 옵션은 **메타데이터** 를 선택한 경우에만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a9c89-126">This option is displayed only if **Metadata** is selected.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a9c89-127"> 이 옵션은 **메타데이터**에서 특성의 수준을 선택한 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a9c89-127">This option is enabled only if a level for an attribute is selected in **Metadata**.</span></span>  
  
 <span data-ttu-id="a9c89-128">**템플릿 추가**</span><span class="sxs-lookup"><span data-stu-id="a9c89-128">**Add Template**</span></span>  
 <span data-ttu-id="a9c89-129">선택한 템플릿을 기반으로 새 계산 멤버, 명명된 집합 또는 스크립트 명령을 큐브 스크립트에 추가하고 폼 보기에서 **KPI 폼 편집기** 를 표시하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a9c89-129">Select to add a new calculated member, named set, or script command based on the selected template to the cube script and display the **KPI Form Editor** in form view.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a9c89-130"> 이 옵션은 **메타데이터** 를 선택한 경우에만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a9c89-130">This option is displayed only if **Metadata** is selected.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9c89-131">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a9c89-131">See Also</span></span>  
 <span data-ttu-id="a9c89-132">[큐브 디자이너 &#40;Analysis Services 다차원 데이터&#41;](cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="a9c89-132">[Cube Designer &#40;Analysis Services - Multidimensional Data&#41;](cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="a9c89-133">[큐브 디자이너 &#40;Kpi&#41; &#40;Analysis Services-다차원 데이터&#41;](kpis-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="a9c89-133">[KPIs &#40;Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](kpis-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="a9c89-134">[도구 모음 &#40;Kpi 탭, 큐브 디자이너&#41; &#40;Analysis Services 다차원 데이터&#41;](toolbar-kpis-tab-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="a9c89-134">[Toolbar &#40;KPIs Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](toolbar-kpis-tab-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="a9c89-135">[KPI 구성 도우미 &#40;Kpi 탭, 큐브 디자이너&#41; &#40;Analysis Services 다차원 데이터&#41;](kpi-organizer-kpis-tab-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="a9c89-135">[KPI Organizer &#40;KPIs Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](kpi-organizer-kpis-tab-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="a9c89-136">[KPI 폼 편집기 &#40;Kpi 탭, 큐브 디자이너&#41; &#40;Analysis Services 다차원 데이터&#41;](kpi-form-editor-kpis-tab-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="a9c89-136">[KPI Form Editor &#40;KPIs Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](kpi-form-editor-kpis-tab-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="a9c89-137">KPI 브라우저 &#40;Kpi 탭, 큐브 디자이너&#41; &#40;Analysis Services 다차원 데이터&#41;</span><span class="sxs-lookup"><span data-stu-id="a9c89-137">KPI Browser &#40;KPIs Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;</span></span>](kpi-browser-kpis-tab-cube-designer-analysis-services-multidimensional-data.md)  
  
  
