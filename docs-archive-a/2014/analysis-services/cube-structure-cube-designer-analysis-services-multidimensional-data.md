---
title: 큐브 구조 (큐브 디자이너) (Analysis Services 다차원 데이터) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.cubebuilderview.f1
ms.assetid: 00f0b605-5352-4b42-84f5-bd6c3e42d3d1
author: minewiskan
ms.author: owend
ms.openlocfilehash: 857dd87c1d638a29adfa11c7de5a4d9f2d006314
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653683"
---
# <a name="cube-structure-cube-designer-analysis-services---multidimensional-data"></a><span data-ttu-id="c1e74-102">큐브 구조(큐브 디자이너)(Analysis Services - 다차원 데이터)</span><span class="sxs-lookup"><span data-stu-id="c1e74-102">Cube Structure (Cube Designer) (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="c1e74-103">\*\*\*\* 큐브 디자이너 **의** 큐브 구조 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 탭을 사용하여 측정값 그룹과 측정값을 생성 및 수정하고, 큐브 차원을 추가하고, 연결된 데이터 원본 뷰에서 큐브에 포함된 개체를 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1e74-103">Use the **Cube Structure** tab in **Cube Designer** in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] to create and modify measure groups and measures, add cube dimensions, and display the objects included in the cube from the associated data source view.</span></span>  
  
 <span data-ttu-id="c1e74-104">**큐브 구조** 탭에는 다음 창이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1e74-104">The **Cube Structure** tab contains the following panes:</span></span>  
  
## <a name="panes"></a><span data-ttu-id="c1e74-105">창</span><span class="sxs-lookup"><span data-stu-id="c1e74-105">Panes</span></span>  
  
|<span data-ttu-id="c1e74-106">창</span><span class="sxs-lookup"><span data-stu-id="c1e74-106">Pane</span></span>|<span data-ttu-id="c1e74-107">정의</span><span class="sxs-lookup"><span data-stu-id="c1e74-107">Definition</span></span>|  
|----------|----------------|  
|<span data-ttu-id="c1e74-108">**도구 모음**</span><span class="sxs-lookup"><span data-stu-id="c1e74-108">**Toolbar**</span></span>|<span data-ttu-id="c1e74-109">이 탭에서 일반 동작을 수행 하려면 도구 모음을 사용 합니다. 이 창에 대 한 자세한 내용은 [도구 모음 &#40;큐브 구조 탭, 큐브 디자이너&#41; &#40;Analysis Services-다차원 데이터&#41;](toolbar-cube-structure-cube-designer-analysis-services-multidimensional-data.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c1e74-109">Use the toolbar to perform common actions in this tab. For more information about this pane, see [Toolbar &#40;Cube Structure Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](toolbar-cube-structure-cube-designer-analysis-services-multidimensional-data.md).</span></span>|  
|<span data-ttu-id="c1e74-110">**측정값**</span><span class="sxs-lookup"><span data-stu-id="c1e74-110">**Measures**</span></span>|<span data-ttu-id="c1e74-111">**측정값** 창을 사용하여 선택한 큐브의 측정값 그룹과 측정값을 생성 및 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1e74-111">Use the **Measures** pane to create and modify measure groups and measures for the selected cube.</span></span> <span data-ttu-id="c1e74-112">이 창에 대한 자세한 내용은 [측정값&#40;큐브 구조 탭, 큐브 디자이너&#41;&#40;Analysis Services - 다차원 데이터&#41;](measures-cube-structure-cube-designer-analysis-services-multidimensional-data.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c1e74-112">For more information about this pane, see [Measures &#40;Cube Structure Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](measures-cube-structure-cube-designer-analysis-services-multidimensional-data.md).</span></span>|  
|<span data-ttu-id="c1e74-113">**차원**</span><span class="sxs-lookup"><span data-stu-id="c1e74-113">**Dimensions**</span></span>|<span data-ttu-id="c1e74-114">**차원** 창을 사용하여 선택한 큐브의 큐브 차원을 포함하고 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1e74-114">Use the **Dimensions** pane to include and modify cube dimensions for the selected cube.</span></span> <span data-ttu-id="c1e74-115">이 창에 대한 자세한 내용은 [차원&#40;큐브 구조 탭, 큐브 디자이너&#41;&#40;Analysis Services - 다차원 데이터&#41;](dimensions-cube-structure-cube-designer-analysis-services-multidimensional-data.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c1e74-115">For more information about this pane, see [Dimensions &#40;Cube Structure Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](dimensions-cube-structure-cube-designer-analysis-services-multidimensional-data.md).</span></span>|  
|<span data-ttu-id="c1e74-116">**데이터 원본 뷰**</span><span class="sxs-lookup"><span data-stu-id="c1e74-116">**Data Source View**</span></span>|<span data-ttu-id="c1e74-117">**데이터 원본 뷰** 창을 사용하여 선택한 큐브와 연결된 데이터 원본 뷰를 보고 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1e74-117">Use the **Data Source View** pane to view and edit the data source view associated with the selected cube.</span></span> <span data-ttu-id="c1e74-118">이 창에 대한 자세한 내용은 [데이터 원본 뷰&#40;큐브 구조 탭, 큐브 디자이너&#41;&#40;Analysis Services - 다차원 데이터&#41;](data-source-view-cube-designer-analysis-services-multidimensional-data.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c1e74-118">For more information about this pane, see [Data Source View &#40;Cube Structure Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](data-source-view-cube-designer-analysis-services-multidimensional-data.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c1e74-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c1e74-119">See Also</span></span>  
 <span data-ttu-id="c1e74-120">[논리적 아키텍처 &#40;Analysis Services 다차원 데이터&#41;](multidimensional-models/olap-logical/understanding-microsoft-olap-logical-architecture.md) </span><span class="sxs-lookup"><span data-stu-id="c1e74-120">[Logical Architecture &#40;Analysis Services - Multidimensional Data&#41;](multidimensional-models/olap-logical/understanding-microsoft-olap-logical-architecture.md) </span></span>  
 <span data-ttu-id="c1e74-121">[다차원 모델의 큐브](multidimensional-models/cubes-in-multidimensional-models.md) </span><span class="sxs-lookup"><span data-stu-id="c1e74-121">[Cubes in Multidimensional Models](multidimensional-models/cubes-in-multidimensional-models.md) </span></span>  
 <span data-ttu-id="c1e74-122">[측정값 속성 구성](multidimensional-models/configure-measure-properties.md) </span><span class="sxs-lookup"><span data-stu-id="c1e74-122">[Configure Measure Properties](multidimensional-models/configure-measure-properties.md) </span></span>  
 <span data-ttu-id="c1e74-123">[차원 &#40;Analysis Services 다차원 데이터&#41;](multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="c1e74-123">[Dimensions &#40;Analysis Services - Multidimensional Data&#41;](multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="c1e74-124">[다차원 모델의 데이터 원본 뷰](multidimensional-models/data-source-views-in-multidimensional-models.md) </span><span class="sxs-lookup"><span data-stu-id="c1e74-124">[Data Source Views in Multidimensional Models](multidimensional-models/data-source-views-in-multidimensional-models.md) </span></span>  
 [<span data-ttu-id="c1e74-125">큐브 디자이너 &#40;Analysis Services 다차원 데이터&#41;</span><span class="sxs-lookup"><span data-stu-id="c1e74-125">Cube Designer &#40;Analysis Services - Multidimensional Data&#41;</span></span>](cube-designer-analysis-services-multidimensional-data.md)  
  
  
