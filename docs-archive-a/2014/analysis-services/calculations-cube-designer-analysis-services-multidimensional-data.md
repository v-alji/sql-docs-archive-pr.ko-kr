---
title: 계산 (큐브 디자이너) (Analysis Services 다차원 데이터) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.calculationsview.f1
ms.assetid: 46e2fbe2-bb41-4eaa-91f8-eb2bd3b8d00d
author: minewiskan
ms.author: owend
ms.openlocfilehash: fdbc35a8e47557923b90cda4e72280c3cca940dc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648706"
---
# <a name="calculations-cube-designer-analysis-services---multidimensional-data"></a><span data-ttu-id="cf6a1-102">계산(큐브 디자이너)(Analysis Services - 다차원 데이터)</span><span class="sxs-lookup"><span data-stu-id="cf6a1-102">Calculations (Cube Designer) (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="cf6a1-103">큐브 디자이너의 **계산** 탭을 사용하여 선택한 큐브에 대한 계산 멤버, 명명된 집합 및 MDX(Multidimensional Expressions) 스크립트 명령을 포함한 계산을 보고 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cf6a1-103">Use the **Calculations** tab in Cube Designer to view and edit calculations, including calculated members, named sets, and Multidimensional Expressions (MDX) script commands for the selected cube.</span></span>  
  
## <a name="form-view-and-script-view"></a><span data-ttu-id="cf6a1-104">폼 보기 및 스크립트 보기</span><span class="sxs-lookup"><span data-stu-id="cf6a1-104">Form View and Script View</span></span>  
 <span data-ttu-id="cf6a1-105">**계산** 탭에서는 계산을 보거나 편집할 때 다음 두 가지 보기를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cf6a1-105">The **Calculations** tab supports two different views when viewing or editing calculations:</span></span>  
  
-   <span data-ttu-id="cf6a1-106">폼 보기</span><span class="sxs-lookup"><span data-stu-id="cf6a1-106">Form view</span></span>  
  
     <span data-ttu-id="cf6a1-107">이 보기에서는 큐브에 연결된 MDX 스크립트에 포함된 계산 멤버, 명명된 집합 및 스크립트 명령의 구조화된 보기를 표시하며 큐브에 사용 가능한 메타데이터, 함수 및 도구를 표시할 뿐만 아니라 계산 멤버 및 명명된 집합을 보고 편집할 수 있는 폼 편집기를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="cf6a1-107">This view displays an organized view of the calculated members, named sets, and script commands contained in the MDX script associated with the cube and provides form editors to view and edit calculated members and named sets, as well as displaying the metadata, functions, and tools available to the cube.</span></span>  
  
-   <span data-ttu-id="cf6a1-108">스크립트 보기</span><span class="sxs-lookup"><span data-stu-id="cf6a1-108">Script view</span></span>  
  
     <span data-ttu-id="cf6a1-109">고급 사용자를 위해 이 보기에서는 큐브에 사용 가능한 메타데이터, 함수 및 도구를 표시할 뿐만 아니라 큐브에 연결된 전체 MDX 스크립트를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="cf6a1-109">For advanced users, this view displays the entire MDX script associated with the cube, as well as displaying the metadata, functions, and tools available to the cube.</span></span>  
  
## <a name="panes"></a><span data-ttu-id="cf6a1-110">창</span><span class="sxs-lookup"><span data-stu-id="cf6a1-110">Panes</span></span>  
 <span data-ttu-id="cf6a1-111">**도구 모음**</span><span class="sxs-lookup"><span data-stu-id="cf6a1-111">**Toolbar**</span></span>  
 <span data-ttu-id="cf6a1-112">폼 보기와 스크립트 보기 모두의 도구 모음을 사용 하 여이 탭에서 일반적인 작업을 수행할 수 있습니다. 이 창에 대 한 자세한 내용은 [도구 모음 &#40;계산 탭, 큐브 디자이너&#41; &#40;Analysis Services 다차원 데이터&#41;](toolbar-calculations-tab-cube-designer-analysis-services-multidimensional-data.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="cf6a1-112">Use the toolbar in both form view and script view to perform common operations on this tab. For more information about this pane, see [Toolbar &#40;Calculations Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](toolbar-calculations-tab-cube-designer-analysis-services-multidimensional-data.md).</span></span>  
  
 <span data-ttu-id="cf6a1-113">**스크립트 구성 도우미**</span><span class="sxs-lookup"><span data-stu-id="cf6a1-113">**Script Organizer**</span></span>  
 <span data-ttu-id="cf6a1-114">폼 보기의 **스크립트 구성 도우미** 창을 사용하여 큐브 스크립트 내용을 정렬된 형식으로 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cf6a1-114">Use the **Script Organizer** pane in form view to display the contents of the cube script in an ordered format.</span></span> <span data-ttu-id="cf6a1-115">이 창에 대한 자세한 내용은 [스크립트 구성 도우미&#40;계산 탭, 큐브 디자이너&#41;&#40;Analysis Services - 다차원 데이터#41;](script-organizer-cube-designer-analysis-services-multidimensional-data.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cf6a1-115">For more information about this pane, see [Script Organizer &#40;Calculations Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](script-organizer-cube-designer-analysis-services-multidimensional-data.md).</span></span>  
  
 <span data-ttu-id="cf6a1-116">**계산 도구**</span><span class="sxs-lookup"><span data-stu-id="cf6a1-116">**Calculation Tools**</span></span>  
 <span data-ttu-id="cf6a1-117">폼 보기와 스크립트 보기 둘 다에 있는 **계산 도구** 창을 사용하여 큐브에 사용 가능한 메타데이터, 함수 및 도구를 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cf6a1-117">Use the **Calculation Tools** pane in both form view and script view to display metadata, functions, and tools available to the cube.</span></span> <span data-ttu-id="cf6a1-118">이 창에 대한 자세한 내용은 [계산 도구&#40;계산 탭, 큐브 디자이너&#41;&#40;Analysis Services - 다차원 데이터#41;](calculation-tools-cube-designer-analysis-services-multidimensional-data.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cf6a1-118">For more information about this pane, see [Calculation Tools &#40;Calculations Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](calculation-tools-cube-designer-analysis-services-multidimensional-data.md).</span></span>  
  
 <span data-ttu-id="cf6a1-119">**스크립트 편집기**</span><span class="sxs-lookup"><span data-stu-id="cf6a1-119">**Script Editor**</span></span>  
 <span data-ttu-id="cf6a1-120">스크립트 보기의 **스크립트 편집기** 창을 사용하여 전체 큐브 스크립트를 편집하고 폼 보기의 스크립트 편집기 창을 사용하여 큐브 스크립트에 포함된 스크립트 명령을 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cf6a1-120">Use the **Script Editor** pane in script view to edit the entire cube script and in form view to edit script commands contained in the cube script.</span></span> <span data-ttu-id="cf6a1-121">이 창에 대한 자세한 내용은 [스크립트 편집기&#40;계산 탭, 큐브 디자이너&#41;&#40;Analysis Services - 다차원 데이터#41;](script-editor-calculations-cube-designer-analysis-services-multidimensional-data.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cf6a1-121">For more information about this pane, see [Script Editor &#40;Calculations Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](script-editor-calculations-cube-designer-analysis-services-multidimensional-data.md).</span></span>  
  
 <span data-ttu-id="cf6a1-122">**계산 멤버 폼 편집기**</span><span class="sxs-lookup"><span data-stu-id="cf6a1-122">**Calculated Member Form Editor**</span></span>  
 <span data-ttu-id="cf6a1-123">폼 보기의 **계산 멤버 폼 편집기** 창을 사용하여 큐브 스크립트의 계산 멤버를 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cf6a1-123">Use the **Calculated Member Form Editor** pane in form view to edit calculated members in the cube script.</span></span> <span data-ttu-id="cf6a1-124">이 창에 대한 자세한 내용은 [계산 멤버 폼 편집기&#40;계산 탭, 큐브 디자이너&#41;&#40;Analysis Services - 다차원 데이터&#41;](calculated-member-form-editor-cube-designer-analysis-services-multidimensional-data.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cf6a1-124">For more information about this pane, see [Calculated Member Form Editor &#40;Calculations Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](calculated-member-form-editor-cube-designer-analysis-services-multidimensional-data.md).</span></span>  
  
 <span data-ttu-id="cf6a1-125">**명명된 집합 폼 편집기**</span><span class="sxs-lookup"><span data-stu-id="cf6a1-125">**Named Set Form Editor**</span></span>  
 <span data-ttu-id="cf6a1-126">폼 보기의 **명명된 집합 폼 편집기** 창을 사용하여 큐브 스크립트의 명명된 집합을 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cf6a1-126">Use the **Named Set Form Editor** pane in form view to edit named sets in the cube script.</span></span> <span data-ttu-id="cf6a1-127">이 창에 대한 자세한 내용은 [명명된 집합 폼 편집기&#40;계산 탭, 큐브 디자이너&#41;&#40;Analysis Services - 다차원 데이터&#41;](named-set-form-editor-cube-designer-analysis-services-multidimensional-data.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cf6a1-127">For more information about this pane, see [Named Set Form Editor &#40;Calculations Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](named-set-form-editor-cube-designer-analysis-services-multidimensional-data.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf6a1-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="cf6a1-128">See Also</span></span>  
 <span data-ttu-id="cf6a1-129">[큐브 개체는 Analysis Services 다차원 데이터를 &#40;&#41;](multidimensional-models-olap-logical-cube-objects/cube-objects-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="cf6a1-129">[Cube Objects &#40;Analysis Services - Multidimensional Data&#41;](multidimensional-models-olap-logical-cube-objects/cube-objects-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="cf6a1-130">[계산](multidimensional-models-olap-logical-cube-objects/calculations.md) </span><span class="sxs-lookup"><span data-stu-id="cf6a1-130">[Calculations](multidimensional-models-olap-logical-cube-objects/calculations.md) </span></span>  
 <span data-ttu-id="cf6a1-131">[MDX 스크립팅 기본 사항 &#40;Analysis Services&#41;](multidimensional-models/mdx/mdx-scripting-fundamentals-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="cf6a1-131">[MDX Scripting Fundamentals &#40;Analysis Services&#41;](multidimensional-models/mdx/mdx-scripting-fundamentals-analysis-services.md) </span></span>  
 <span data-ttu-id="cf6a1-132">[큐브 디자이너 &#40;Analysis Services 다차원 데이터&#41;](cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="cf6a1-132">[Cube Designer &#40;Analysis Services - Multidimensional Data&#41;](cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="cf6a1-133">명명된 집합 만들기</span><span class="sxs-lookup"><span data-stu-id="cf6a1-133">Create Named Sets</span></span>](multidimensional-models/create-named-sets.md)  
  
  
