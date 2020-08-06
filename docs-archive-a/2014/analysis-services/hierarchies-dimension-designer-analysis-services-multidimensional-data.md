---
title: 계층 (차원 구조 탭, 차원 디자이너) (Analysis Services 다차원 데이터) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql.asvs.dimensiondesigner.dbv.hierarchieslevelspane.f1
ms.assetid: c37db6c1-b5a5-44e1-ae6d-a96fb9769e68
author: minewiskan
ms.author: owend
ms.openlocfilehash: 544ead21475dbb6134f68cd7582c9c36ceb316af
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649249"
---
# <a name="hierarchies-dimension-structure-tab-dimension-designer-analysis-services---multidimensional-data"></a><span data-ttu-id="46b3f-102">계층(차원 구조 탭, 차원 디자이너)(Analysis Services - 다차원 데이터)</span><span class="sxs-lookup"><span data-stu-id="46b3f-102">Hierarchies (Dimension Structure Tab, Dimension Designer) (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="46b3f-103">**계층** 창을 사용하여 현재 선택한 차원의 계층과 수준을 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="46b3f-103">Use the **Hierarchies** pane to manage the hierarchies and levels for the currently selected dimension.</span></span> <span data-ttu-id="46b3f-104">자세한 내용은 [사용자 정의 계층 만들기](multidimensional-models/user-defined-hierarchies-create.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="46b3f-104">For more information, see [Create User-Defined Hierarchies](multidimensional-models/user-defined-hierarchies-create.md).</span></span>  
  
 <span data-ttu-id="46b3f-105">계층 창을 사용하여 수행할 수 있는 절차는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="46b3f-105">You can use the Hierarchies pane to do the following procedures:</span></span>  
  
-   <span data-ttu-id="46b3f-106">**특성** 창에서 **계층** 창으로 특성을 끌어 새 계층을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="46b3f-106">Create a new hierarchy by dragging an attribute from the **Attributes** pane to the **Hierarchies** pane.</span></span>  
  
-   <span data-ttu-id="46b3f-107">계층 이름 옆의 화살표를 클릭하여 계층 내 모든 수준의 멤버 속성을 표시하거나 숨깁니다.</span><span class="sxs-lookup"><span data-stu-id="46b3f-107">Show or hide member properties for all the levels in the hierarchy by clicking the arrow next to the hierarchy name.</span></span>  
  
-   <span data-ttu-id="46b3f-108">수준 이름 옆의 화살표를 클릭하여 특성 관계를 표시하거나 숨깁니다.</span><span class="sxs-lookup"><span data-stu-id="46b3f-108">Show or hide attribute relationships by clicking the arrow next to the level name.</span></span>  
  
 <span data-ttu-id="46b3f-109">**계층 창을 표시하려면**</span><span class="sxs-lookup"><span data-stu-id="46b3f-109">**To display the Hierarchies pane**</span></span>  
  
1.  <span data-ttu-id="46b3f-110">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]에서 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 프로젝트를 연 다음 원하는 차원을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="46b3f-110">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project, and then open the dimension that you want.</span></span>  
  
2.  <span data-ttu-id="46b3f-111">차원이 선택되지 않은 경우에는 **차원 구조** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="46b3f-111">If not selected, click the **Dimension Structure** tab.</span></span>  
  
## <a name="options"></a><span data-ttu-id="46b3f-112">옵션</span><span class="sxs-lookup"><span data-stu-id="46b3f-112">Options</span></span>  
 <span data-ttu-id="46b3f-113">**계층 구조**</span><span class="sxs-lookup"><span data-stu-id="46b3f-113">**Hierarchies**</span></span>  
 <span data-ttu-id="46b3f-114">현재 생성된 계층을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="46b3f-114">Displays the currently created hierarchies.</span></span> <span data-ttu-id="46b3f-115">각 계층 내부에는 계층의 수준을 구성하는 특성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="46b3f-115">Within each hierarchy are the attributes that make up the levels of the hierarchy.</span></span> <span data-ttu-id="46b3f-116">읽기 전용인 특성 관계도 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="46b3f-116">Attribute relationships are also shown but they are read-only.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46b3f-117">참고 항목</span><span class="sxs-lookup"><span data-stu-id="46b3f-117">See Also</span></span>  
 <span data-ttu-id="46b3f-118">[차원 구조 &#40;차원 디자이너&#41; &#40;Analysis Services 다차원 데이터&#41;](dimension-structure-dimension-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="46b3f-118">[Dimension Structure &#40;Dimension Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](dimension-structure-dimension-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="46b3f-119">[특성 &#40;차원 구조 탭, 차원 디자이너&#41; &#40;Analysis Services-다차원 데이터&#41;](attributes-dimension-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="46b3f-119">[Attributes &#40;Dimension Structure Tab, Dimension Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](attributes-dimension-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="46b3f-120">[데이터 원본 뷰 &#40;차원 구조 탭, 차원 디자이너&#41; &#40;Analysis Services-다차원 데이터&#41;](datasource-view-dimension-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="46b3f-120">[Data Source View &#40;Dimension Structure Tab, Dimension Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](datasource-view-dimension-designer-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="46b3f-121">&#40;차원 구조 탭, 차원 디자이너&#41; &#40;Analysis Services 다차원 데이터&#41;</span><span class="sxs-lookup"><span data-stu-id="46b3f-121">Toolbar &#40;Dimension Structure Tab, Dimension Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;</span></span>](toolbar-dimension-structure-designer-analysis-services-multidimensional-data.md)  
  
  
