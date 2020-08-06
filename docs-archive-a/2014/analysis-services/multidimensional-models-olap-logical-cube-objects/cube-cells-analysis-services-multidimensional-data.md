---
title: 큐브 셀 (Analysis Services 다차원 데이터) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- storing data [Analysis Services], cells
- hierarchies [Analysis Services], cells
- OLAP objects [Analysis Services], cells
- data members [Analysis Services]
- cubes [Analysis Services], cells
- empty cells [Analysis Services]
- nonleaf members
- cubes [Analysis Services], examples
- storage [Analysis Services], cells
- nonleaf cells
- calculated cells [Analysis Services]
- dimensions [Analysis Services], cells
- cells [Analysis Services]
- leaf members
- leaf cells
ms.assetid: 9945773c-a43b-40d4-91cf-3d2ebc90bca5
author: minewiskan
ms.author: owend
ms.openlocfilehash: 0b55e940f75319a965fb1441520a7e16ce7ab2f6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647316"
---
# <a name="cube-cells-analysis-services---multidimensional-data"></a><span data-ttu-id="89ed1-102">큐브 셀(Analysis Services - 다차원 데이터)</span><span class="sxs-lookup"><span data-stu-id="89ed1-102">Cube Cells (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="89ed1-103">큐브는 셀로 이루어져 있으며 셀은 측정값 그룹과 차원으로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="89ed1-103">A cube is composed of cells, organized by measure groups and dimensions.</span></span> <span data-ttu-id="89ed1-104">셀은 큐브의 모든 차원에서 한 멤버 큐브의 고유한 논리적 교집합을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="89ed1-104">A cell represents the unique logical intersection in a cube of one member from every dimension in the cube.</span></span> <span data-ttu-id="89ed1-105">예를 들어 아래 다이어그램의 큐브는 Source, Route 및 Time이라는 세 차원으로 이루어지며 두 측정값을 갖는 측정값 그룹을 하나 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="89ed1-105">For example, the cube described by the following diagram contains one measure group that has two measures, organized along three dimensions named Source, Route, and Time.</span></span>  
  
 <span data-ttu-id="89ed1-106">![단일 셀을 식별하는 큐브 다이어그램](../../analysis-services/dev-guide/media/as-cubeintro5.gif "단일 셀을 식별하는 큐브 다이어그램")</span><span class="sxs-lookup"><span data-stu-id="89ed1-106">![Cube diagram identifying a single cell](../../analysis-services/dev-guide/media/as-cubeintro5.gif "Cube diagram identifying a single cell")</span></span>  
  
 <span data-ttu-id="89ed1-107">이 다이어그램에서 회색으로 표시된 단일 셀은 다음 멤버의 교집합입니다.</span><span class="sxs-lookup"><span data-stu-id="89ed1-107">The single shaded cell in this diagram is the intersection of the following members:</span></span>  
  
-   <span data-ttu-id="89ed1-108">경로 차원의 항공 멤버</span><span class="sxs-lookup"><span data-stu-id="89ed1-108">The air member of the Route dimension.</span></span>  
  
-   <span data-ttu-id="89ed1-109">원본 유형 차원의 아프리카 멤버</span><span class="sxs-lookup"><span data-stu-id="89ed1-109">The Africa member of the Source dimension.</span></span>  
  
-   <span data-ttu-id="89ed1-110">시간 차원의 4사분기 멤버</span><span class="sxs-lookup"><span data-stu-id="89ed1-110">The 4th quarter member of the Time dimension.</span></span>  
  
-   <span data-ttu-id="89ed1-111">패키지 측정값</span><span class="sxs-lookup"><span data-stu-id="89ed1-111">The Packages measure.</span></span>  
  
## <a name="leaf-and-nonleaf-cells"></a><span data-ttu-id="89ed1-112">리프 셀 및 리프가 아닌 셀</span><span class="sxs-lookup"><span data-stu-id="89ed1-112">Leaf and Nonleaf Cells</span></span>  
 <span data-ttu-id="89ed1-113">큐브의 셀 값은 여러 방법을 사용하여 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="89ed1-113">The value for a cell in a cube can be obtained in one of several ways.</span></span> <span data-ttu-id="89ed1-114">위의 예에서는 셀을 식별 하는 데 사용 되는 모든 멤버가 *리프 멤버*이므로 셀의 값을 큐브의 팩트 테이블에서 직접 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="89ed1-114">In the previous example, the value in the cell can be directly retrieved from the fact table of the cube, because all the members used to identify that cell are *leaf members*.</span></span> <span data-ttu-id="89ed1-115">리프 멤버에는 계층적으로 자식 멤버가 없으며 대개 차원 테이블의 단일 레코드를 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="89ed1-115">A leaf member has no child members, hierarchically speaking, and typically references a single record in a dimension table.</span></span> <span data-ttu-id="89ed1-116">이러한 종류의 셀을 *리프 셀*이라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="89ed1-116">This kind of cell is referred to as a *leaf cell*.</span></span>  
  
 <span data-ttu-id="89ed1-117">그러나 *리프가 아닌 멤버*를 사용 하 여 셀을 식별할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="89ed1-117">However, a cell can also be identified by using *nonleaf members*.</span></span> <span data-ttu-id="89ed1-118">리프가 아닌 멤버는 하나 이상의 자식 멤버가 있는 멤버입니다.</span><span class="sxs-lookup"><span data-stu-id="89ed1-118">A nonleaf member is a member that has one or more child members.</span></span> <span data-ttu-id="89ed1-119">이 경우 셀 값은 대개 리프가 아닌 멤버와 연결된 자식 멤버의 집계에서 파생됩니다.</span><span class="sxs-lookup"><span data-stu-id="89ed1-119">In this case, the value of the cell is typically derived from the aggregation of child members associated with the nonleaf member.</span></span> <span data-ttu-id="89ed1-120">예를 들어 다음과 같은 멤버와 차원의 교집합은 집계를 통해 값이 제공되는 셀을 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="89ed1-120">For example, the intersection of the following members and dimensions refers to a cell whose value is supplied by aggregation:</span></span>  
  
-   <span data-ttu-id="89ed1-121">경로 차원의 항공 멤버</span><span class="sxs-lookup"><span data-stu-id="89ed1-121">The air member of the Route dimension.</span></span>  
  
-   <span data-ttu-id="89ed1-122">원본 유형 차원의 아프리카 멤버</span><span class="sxs-lookup"><span data-stu-id="89ed1-122">The Africa member of the Source dimension.</span></span>  
  
-   <span data-ttu-id="89ed1-123">Time 차원의 하반기 멤버</span><span class="sxs-lookup"><span data-stu-id="89ed1-123">The 2nd half member of the Time dimension.</span></span>  
  
-   <span data-ttu-id="89ed1-124">패키지 멤버</span><span class="sxs-lookup"><span data-stu-id="89ed1-124">The Packages member.</span></span>  
  
 <span data-ttu-id="89ed1-125">Time 차원의 하반기 멤버는 리프가 아닌 멤버입니다.</span><span class="sxs-lookup"><span data-stu-id="89ed1-125">The 2nd half member of the Time dimension is a nonleaf member.</span></span> <span data-ttu-id="89ed1-126">따라서 이 멤버와 연결된 모든 값은 다음 다이어그램에서와 같이 집계된 값이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="89ed1-126">Therefore, all of values associated with it must be aggregated values, as shown in the following diagram.</span></span>  
  
 <span data-ttu-id="89ed1-127">![두 번째 절반 멤버에 대 한 세 번째 및 네 번째 분기 셀](../../analysis-services/dev-guide/media/as-cubeintro6.gif "두 번째 절반 멤버에 대 한 세 번째 및 네 번째 분기 셀")</span><span class="sxs-lookup"><span data-stu-id="89ed1-127">![3rd and 4th quarter cells for 2nd half member](../../analysis-services/dev-guide/media/as-cubeintro6.gif "3rd and 4th quarter cells for 2nd half member")</span></span>  
  
 <span data-ttu-id="89ed1-128">3사분기와 4사분기 멤버에 대한 집계가 합계라고 가정하면 지정한 셀 값은 위 다이어그램에서 회색으로 표시된 리프 셀을 모두 합한 값인 400입니다.</span><span class="sxs-lookup"><span data-stu-id="89ed1-128">Assuming the aggregations for the 3rd quarter and 4th quarter members are summations, the value of the specified cell is 400, which is the total of all of the leaf cells shaded in the previous diagram.</span></span> <span data-ttu-id="89ed1-129">셀 값이 다른 셀의 집계에서 파생 되기 때문에 지정 된 셀은 *리프가 아닌 셀*로 간주 됩니다.</span><span class="sxs-lookup"><span data-stu-id="89ed1-129">Because the value of the cell is derived from the aggregation of other cells, the specified cell is considered a *nonleaf cell*.</span></span>  
  
 <span data-ttu-id="89ed1-130">사용자 지정 롤업 및 멤버 그룹을 사용하는 멤버와 사용자 지정 멤버에 대해 파생된 셀 값도 비슷한 방식으로 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="89ed1-130">The cell values derived for members that use custom rollups and member groups, in addition to custom members, are handled similarly.</span></span> <span data-ttu-id="89ed1-131">그러나 계산 멤버에 대해 파생된 셀 값은 계산 멤버를 정의하는 데 사용하는 MDX(Multidimensional Expressions)만을 기반으로 합니다. 실제로 관련된 셀 데이터가 없는 경우도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="89ed1-131">However, cell values derived for calculated members are based completely on the Multidimensional Expressions (MDX) expression used to define the calculated member; in some cases, there may be no actual cell data involved.</span></span> <span data-ttu-id="89ed1-132">자세한 내용은 [부모-자식 차원의 사용자 지정 롤업 연산자](../multidimensional-models/parent-child-dimension-attributes-custom-rollup-operators.md), [사용자 지정 멤버 수식](../multidimensional-models/attribute-properties-define-custom-member-formulas.md)및 [계산](../multidimensional-models-olap-logical-cube-objects/calculations.md)정의를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="89ed1-132">For more information, see [Custom Rollup Operators in Parent-Child Dimensions](../multidimensional-models/parent-child-dimension-attributes-custom-rollup-operators.md), [Define Custom Member Formulas](../multidimensional-models/attribute-properties-define-custom-member-formulas.md), and [Calculations](../multidimensional-models-olap-logical-cube-objects/calculations.md).</span></span>  
  
## <a name="empty-cells"></a><span data-ttu-id="89ed1-133">빈 셀</span><span class="sxs-lookup"><span data-stu-id="89ed1-133">Empty Cells</span></span>  
 <span data-ttu-id="89ed1-134">큐브의 모든 셀에 값이 있어야 하는 것은 아닙니다. 큐브에 데이터가 없는 교집합이 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="89ed1-134">It is not required that every cell in a cube contain a value; there can be intersections in a cube that have no data.</span></span> <span data-ttu-id="89ed1-135">빈 셀이라고 하는 이러한 교집합은 큐브 내에 측정값이 있는 차원 특성의 모든 교집합에 팩트 테이블의 해당 레코드가 포함되는 것이 아니기 때문에 큐브에서 종종 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="89ed1-135">These intersections, called empty cells, frequently occur in cubes because not every intersection of a dimension attribute with a measure within a cube contains a corresponding record in a fact table.</span></span> <span data-ttu-id="89ed1-136">큐브의 전체 셀 개수에 대 한 빈 셀의 비율을 일반적으로 큐브의 *희박도* 라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="89ed1-136">The ratio of empty cells in a cube to the total number of cells in a cube is frequently referred to as the *sparsity* of a cube.</span></span>  
  
 <span data-ttu-id="89ed1-137">예를 들어 아래 다이어그램에 표시된 큐브의 구조는 이 항목의 다른 예제와 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="89ed1-137">For example, the structure of the cube shown in the following diagram is similar to other examples in this topic.</span></span> <span data-ttu-id="89ed1-138">그러나 이 예제에서는 3사분기 아프리카행 항공 수송 또는 4사분기 오스트레일리아행 항공 수송이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="89ed1-138">However, in this example, there were no air shipments to Africa for the third quarter or to Australia for the fourth quarter.</span></span> <span data-ttu-id="89ed1-139">이러한 차원과 측정값의 교집합을 지원하는 데이터가 팩트 테이블에 없으므로 해당 교집합의 셀은 빈 셀이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="89ed1-139">There is no data in the fact table to support the intersections of those dimensions and measures; therefore the cells at those intersections are empty.</span></span>  
  
 <span data-ttu-id="89ed1-140">![빈 셀을 식별하는 큐브 다이어그램](../../analysis-services/dev-guide/media/as-cubeintro7.gif "빈 셀을 식별하는 큐브 다이어그램")</span><span class="sxs-lookup"><span data-stu-id="89ed1-140">![Cube diagram identifying empty cells](../../analysis-services/dev-guide/media/as-cubeintro7.gif "Cube diagram identifying empty cells")</span></span>  
  
 <span data-ttu-id="89ed1-141">에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 빈 셀은 특별 한 품질이 있는 셀입니다.</span><span class="sxs-lookup"><span data-stu-id="89ed1-141">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], an empty cell is a cell that has special qualities.</span></span> <span data-ttu-id="89ed1-142">빈 셀은 크로스 조인, 카운트 등의 결과를 달라지게 할 수 있으므로 많은 MDX 함수가 계산을 위한 목적으로 빈 셀을 무시할 수 있는 기능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="89ed1-142">Because empty cells can skew the results of crossjoins, counts, and so on, many MDX functions supply the ability to ignore empty cells for the purposes of calculation.</span></span> <span data-ttu-id="89ed1-143">자세한 내용은 mdx [&#40;mdx&#41; 참조](/sql/mdx/multidimensional-expressions-mdx-reference)및 [mdx &#40;Analysis Services&#41;에 대 한 주요 개념 ](../multidimensional-models/key-concepts-in-mdx-analysis-services.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="89ed1-143">For more information, see [Multidimensional Expressions &#40;MDX&#41; Reference](/sql/mdx/multidimensional-expressions-mdx-reference), and [Key Concepts in MDX &#40;Analysis Services&#41;](../multidimensional-models/key-concepts-in-mdx-analysis-services.md).</span></span>  
  
## <a name="security"></a><span data-ttu-id="89ed1-144">보안</span><span class="sxs-lookup"><span data-stu-id="89ed1-144">Security</span></span>  
 <span data-ttu-id="89ed1-145">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]에서 셀 데이터에 대한 액세스는 역할 수준에서 관리되며 MDX 식을 사용하여 정밀하게 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="89ed1-145">Access to cell data is managed in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] at the role level, and can be finely controlled by using MDX expressions.</span></span> <span data-ttu-id="89ed1-146">자세한 내용은 [차원 데이터에 대 한 사용자 지정 액세스 권한 부여 &#40;Analysis Services&#41;](../multidimensional-models/grant-custom-access-to-dimension-data-analysis-services.md)을 참조 하 고 [셀 데이터 &#40;Analysis Services&#41;에 대 한 사용자 지정 액세스 권한 부여 ](../multidimensional-models/grant-custom-access-to-cell-data-analysis-services.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="89ed1-146">For more information, see [Grant custom access to dimension data &#40;Analysis Services&#41;](../multidimensional-models/grant-custom-access-to-dimension-data-analysis-services.md), and [Grant custom access to cell data &#40;Analysis Services&#41;](../multidimensional-models/grant-custom-access-to-cell-data-analysis-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89ed1-147">참고 항목</span><span class="sxs-lookup"><span data-stu-id="89ed1-147">See Also</span></span>  
 <span data-ttu-id="89ed1-148">[큐브 저장소 &#40;Analysis Services 다차원 데이터&#41;](../multidimensional-models-olap-logical-cube-objects/cube-storage-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="89ed1-148">[Cube Storage &#40;Analysis Services - Multidimensional Data&#41;](../multidimensional-models-olap-logical-cube-objects/cube-storage-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="89ed1-149">Aggregations and Aggregation Designs</span><span class="sxs-lookup"><span data-stu-id="89ed1-149">Aggregations and Aggregation Designs</span></span>](../multidimensional-models-olap-logical-cube-objects/aggregations-and-aggregation-designs.md)  
  
  
