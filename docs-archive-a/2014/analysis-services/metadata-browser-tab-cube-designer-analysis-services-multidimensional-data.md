---
title: 메타 데이터 (브라우저 탭, 큐브 디자이너) (Analysis Services 다차원 데이터) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.browsecube.metadatapane.f1
ms.assetid: a1ace545-488d-4645-8330-56408a5e8abd
author: minewiskan
ms.author: owend
ms.openlocfilehash: 8093ac8cac8e3cd5a609e97b47ede89912897e8a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740576"
---
# <a name="metadata-browser-tab-cube-designer-analysis-services---multidimensional-data"></a><span data-ttu-id="bcb44-102">메타데이터(브라우저 탭, 큐브 디자이너)(Analysis Services - 다차원 데이터)</span><span class="sxs-lookup"><span data-stu-id="bcb44-102">Metadata (Browser Tab, Cube Designer) (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="bcb44-103">큐브 디자이너의 **브라우저** 탭에 있는 **메타데이터** 창을 사용하여 큐브 구조를 찾아보고, 관련 측정값을 확인하고, 차원을 보거나 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bcb44-103">Use the **Metadata** pane on the **Browser** tab in Cube Designer to browse the structure of the cube, to see related measures, and to view and create dimensions.</span></span> <span data-ttu-id="bcb44-104">계층을 드릴다운하고, 사용 가능한 측정값 및 KPI 목록을 보고, 개체의 정규화된 이름을 복사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bcb44-104">You can drill down into hierarchies, view a list of available measures and KPIs, and copy the fully qualified names of objects.</span></span>  
  
 <span data-ttu-id="bcb44-105">**메타데이터** 창에서 개체 및 계층을 쿼리 작성 영역으로 끌어 새 쿼리를 만들거나 Excel에서 찾아보도록 데이터를 내보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bcb44-105">You can also drag the objects and hierarchies in the **Metadata** pane to the query building area, to create new queries or export data for browsing in Excel.</span></span>  
  
## <a name="options"></a><span data-ttu-id="bcb44-106">옵션</span><span class="sxs-lookup"><span data-stu-id="bcb44-106">Options</span></span>  
 <span data-ttu-id="bcb44-107">**메타데이터**</span><span class="sxs-lookup"><span data-stu-id="bcb44-107">**Metadata**</span></span>  
 <span data-ttu-id="bcb44-108">현재 뷰에 사용 가능한 메타데이터가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="bcb44-108">Displays the metadata available in the current view.</span></span> <span data-ttu-id="bcb44-109">큐브 아이콘을 클릭하여 뷰(현재 선택된 큐브 뷰 또는 큐브)를 변경한 다음 **큐브 선택** 대화 상자를 사용하여 새 큐브 또는 큐브 뷰를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bcb44-109">You can change the view (that is, the currently selected perspective or cube) by clicking the cube icon, and then using the **Cube Selection** dialog box to choose a new cube or perspective.</span></span> <span data-ttu-id="bcb44-110">**측정값 그룹**을 클릭하고 드롭다운 목록에서 새 측정값 그룹을 선택하여 **메타데이터** 창에서 사용할 수 있는 개체를 필터링할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bcb44-110">You can also click **Measure Group**, and select a new measure group from the dropdown list to filter the objects that are available in the **Metadata** pane.</span></span>  
  
 <span data-ttu-id="bcb44-111">[!INCLUDE[msCoName](../includes/msconame-md.md)] 보고서 **창에서** Office 11.0 피벗 테이블 컨트롤의 필터, 데이터, 행 또는 열 영역으로 선택한 항목을 끌어서 선택한 항목에 대한 데이터를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="bcb44-111">Drag selected items to the filter, data, row, or column areas of the [!INCLUDE[msCoName](../includes/msconame-md.md)] Office 11.0 PivotTable control in the **Report** pane to display the data for the selected item.</span></span>  
  
 <span data-ttu-id="bcb44-112">**함수**</span><span class="sxs-lookup"><span data-stu-id="bcb44-112">**Functions**</span></span>  
 <span data-ttu-id="bcb44-113">**브라우저**에서 쿼리 또는 데이터 뷰를 만드는 데 사용할 수 있는 모든 함수, 연산자 및 상수 목록을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="bcb44-113">Displays a list of all functions, operators, and constants that can be used to create queries or data views in the **Browser**.</span></span> <span data-ttu-id="bcb44-114">함수를 사용하려면 원하는 함수를 찾아 쿼리 영역으로 끌어서 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="bcb44-114">To use a function, locate the one you want, and drag it into the query area.</span></span> <span data-ttu-id="bcb44-115">구문 정의가 텍스트에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="bcb44-115">The syntax definition is added to the text</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="bcb44-116"> 그래픽 디자인 뷰에서 작업할 때는 **함수** 목록을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="bcb44-116">The **Function** list is not available when you are working in graphical design view.</span></span>  
  
 <span data-ttu-id="bcb44-117">테이블 형식 모델을 사용할 경우 함수 목록에 MDX 함수와 DAX 함수가 모두 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="bcb44-117">When working with a tabular model, the list of functions includes both MDX functions and DAX functions.</span></span> <span data-ttu-id="bcb44-118">그 외의 경우에는 MDX만 목록에 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="bcb44-118">Otherwise, the list includes only MDX.</span></span> <span data-ttu-id="bcb44-119">다차원 모델은 DAX 식을 개체 정의의 일부로 포함할 수는 있지만 DAX 함수를 직접 사용할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="bcb44-119">A multidimensional model cannot use DAX functions directly, although a DAX expression might be included as part of an object definition.</span></span>  
  
 <span data-ttu-id="bcb44-120">팁: DAX 함수가 포함된 폴더는 모두 대문자로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="bcb44-120">Tip: The folders that contain DAX functions are listed in all upper-case letters.</span></span> <span data-ttu-id="bcb44-121">다른 모든 폴더에는 MDX 함수가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="bcb44-121">All other folders contain MDX functions.</span></span> <span data-ttu-id="bcb44-122">예를 들어 통계 함수를 위한 폴더가 두 개 있는 경우 **STATISTICAL** 에는 관련 DAX 함수가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="bcb44-122">For example, there are two folders for statistical functions: **STATISTICAL** contains the related DAX functions.</span></span>  
  
## <a name="context-menu"></a><span data-ttu-id="bcb44-123">상황에 맞는 메뉴</span><span class="sxs-lookup"><span data-stu-id="bcb44-123">Context Menu</span></span>  
 <span data-ttu-id="bcb44-124">다음 옵션은 **메타데이터** 창에서 요소를 마우스 오른쪽 단추로 클릭하면 표시되는 상황에 맞는 메뉴를 통해 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bcb44-124">The following options are available in the context menu displayed by right-clicking an element displayed in the **Metadata** pane:</span></span>  
  
|<span data-ttu-id="bcb44-125">옵션</span><span class="sxs-lookup"><span data-stu-id="bcb44-125">Option</span></span>|<span data-ttu-id="bcb44-126">Description</span><span class="sxs-lookup"><span data-stu-id="bcb44-126">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="bcb44-127">**쿼리에 추가**</span><span class="sxs-lookup"><span data-stu-id="bcb44-127">**Add to Query**</span></span>|<span data-ttu-id="bcb44-128">쿼리 작성 영역의 아래쪽 창에 선택한 개체를 추가하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bcb44-128">Click to add the selected object to the lower pane of the query building area.</span></span>|  
|<span data-ttu-id="bcb44-129">**필터에 추가**</span><span class="sxs-lookup"><span data-stu-id="bcb44-129">**Add to Filter**</span></span>|<span data-ttu-id="bcb44-130">선택한 차원, 특성, 계층 또는 수준을 **브라우저**의 필터 영역에 추가하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bcb44-130">Click to add the selected dimension, attribute, hierarchy, or level to the filter area of the **Browser**.</span></span><br /><br /> <span data-ttu-id="bcb44-131">참고: 이 옵션은 차원, 특성, 계층 또는 수준을 선택한 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bcb44-131">Note: This option is enabled only if a dimension, attribute, hierarchy, or level is selected.</span></span>|  
|<span data-ttu-id="bcb44-132">**복사**</span><span class="sxs-lookup"><span data-stu-id="bcb44-132">**Copy**</span></span>|<span data-ttu-id="bcb44-133">선택한 항목을 클립보드에 추가하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bcb44-133">Click to add the selected item to the Clipboard.</span></span><br /><br /> <span data-ttu-id="bcb44-134">참고: 이 옵션은 개체의 정규화된 이름을 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="bcb44-134">Note: This option copies the fully qualified name of the object.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bcb44-135">참고 항목</span><span class="sxs-lookup"><span data-stu-id="bcb44-135">See Also</span></span>  
 <span data-ttu-id="bcb44-136">[도구 모음 &#40;브라우저 탭, 큐브 디자이너&#41; &#40;Analysis Services 다차원 데이터&#41;](toolbar-browser-tab-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="bcb44-136">[Toolbar &#40;Browser Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](toolbar-browser-tab-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="bcb44-137">[Excel에서 분석 &#40;브라우저 탭, 큐브 디자이너&#41; &#40;Analysis Services 다차원 데이터&#41;](analyze-in-excel-browser-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="bcb44-137">[Analyze in Excel &#40;Browser Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](analyze-in-excel-browser-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="bcb44-138">[쿼리 및 필터 &#40;브라우저 탭, 큐브 디자이너&#41; &#40;Analysis Services 다차원 데이터&#41;](query-filter-browser-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="bcb44-138">[Query and Filter &#40;Browser Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](query-filter-browser-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="bcb44-139">브라우저 &#40;큐브 디자이너&#41; &#40;Analysis Services 다차원 데이터&#41;</span><span class="sxs-lookup"><span data-stu-id="bcb44-139">Browser &#40;Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;</span></span>](browser-cube-designer-analysis-services-multidimensional-data.md)  
  
  
