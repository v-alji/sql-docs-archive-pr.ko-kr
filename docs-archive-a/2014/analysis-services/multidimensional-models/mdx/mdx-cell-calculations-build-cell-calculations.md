---
title: MDX로 셀 계산 작성 (MDX) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- calculated cells [MDX]
- queries [MDX], cell calculations
- cells [MDX]
- MDX [Analysis Services], calculations
- calculation subcubes [MDX]
- calculated values [MDX]
- Multidimensional Expressions [Analysis Services], cell calculations
ms.assetid: 068aea63-d419-4791-a960-3d74e76f808e
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9ab3219850c49c2ec16a12aab3ba7db67e9a8721
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734499"
---
# <a name="building-cell-calculations-in-mdx-mdx"></a><span data-ttu-id="ef310-102">MDX로 셀 계산 작성(MDX)</span><span class="sxs-lookup"><span data-stu-id="ef310-102">Building Cell Calculations in MDX (MDX)</span></span>
  <span data-ttu-id="ef310-103">MDX는 계산 멤버, 사용자 지정 롤업, 사용자 지정 멤버 등 계산 값을 생성하기 위한 여러 가지 도구를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="ef310-103">Multidimensional Expressions (MDX) provides you with a number of tools for generating calculated values, such as calculated members, custom rollups, and custom members.</span></span> <span data-ttu-id="ef310-104">하지만 이러한 기능을 사용하여 특정 셀 집합 또는 문제가 되는 단일 셀에 영향을 주기는 어렵습니다.</span><span class="sxs-lookup"><span data-stu-id="ef310-104">However, using these features to affect a specific set of cells, or a single cell for that matter, would be difficult.</span></span>  
  
 <span data-ttu-id="ef310-105">셀에 맞게 특별히 계산된 값을 생성하려면 MDX에서 계산 셀 기능을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef310-105">To generated calculated values for specifically for cells, you need to use the calculated cells feature in MDX.</span></span> <span data-ttu-id="ef310-106">계산 셀을 이용하면 *계산 하위 큐브*라는 특정 셀 조각을 정의하고 각 셀에 적용될 수 있는 선택 조건에 따라 계산 하위 큐브 내에 있는 각각의 모든 셀에 수식을 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ef310-106">Calculated cells let you define a specific slice of cells, called a *calculation subcube*, and apply a formula to each and every cell within the calculation subcube, subject to an optional condition that can be applied to each cell.</span></span>  
  
 <span data-ttu-id="ef310-107">또한 계산 셀은 KPI에 사용되는 것과 같은 목표값 찾기 수식 또는 이론적인 분석 수식과 같은 복잡한 기능도 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="ef310-107">Calculated cells also offer complex functionality, such as goal-seeking formulas, as used in KPIs, or speculative analysis formulas.</span></span> <span data-ttu-id="ef310-108">이러한 기능 수준은의 패스 순서 기능에서 제공 됩니다 .이 기능을 사용 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 하는 경우 계산 수식이 패스 순서의 특정 패스에 적용 되는 계산 셀을 사용 하 여 재귀 패스를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ef310-108">This level of functionality comes from the pass order feature in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] that allows recursive passes to be made with calculated cells, with calculation formulas applied at specific passes in the pass order.</span></span> <span data-ttu-id="ef310-109">패스 순서에 대한 자세한 내용은 [패스 순서 및 계산 순서 이해&#40;MDX&#41;](mdx-data-manipulation-understanding-pass-order-and-solve-order.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ef310-109">For more information on pass order, see [Understanding Pass Order and Solve Order &#40;MDX&#41;](mdx-data-manipulation-understanding-pass-order-and-solve-order.md).</span></span>  
  
 <span data-ttu-id="ef310-110">작성 범위 측면에서, 계산 셀은 한 세션 또는 단일 쿼리 중에만 임시로 만들거나 큐브의 일부로 전체적으로 사용할 수 있다는 점에서 명명된 집합 및 계산 멤버 모두와 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="ef310-110">In terms of creation scope, calculated cells are similar to both named sets and calculated members in that calculated cells can be temporarily created for the lifetime of either a session or a single query, or made globally available as part of a cube:</span></span>  
  
-   <span data-ttu-id="ef310-111">**쿼리 범위** MDX 쿼리의 일부로 정의되는 계산 셀을 만들어서 해당 범위가 쿼리로 제한되도록 하려면 WITH 키워드를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ef310-111">**Query-scoped** To create a calculated cell that is defined as part of an MDX query, and therefore whose scope is limited to the query, you use the WITH keyword.</span></span> <span data-ttu-id="ef310-112">그런 다음 MDX SELECT 문 내에서 계산 셀을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ef310-112">You can then use the calculated cell within an MDX SELECT statement.</span></span> <span data-ttu-id="ef310-113">이 방식을 사용할 경우 `WITH` 키워드를 사용하여 만든 계산 셀은 SELECT 문을 배포하지 않아도 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ef310-113">Using this approach, the calculated cell created by using the `WITH` keyword can be changed without disturbing the SELECT statement.</span></span>  
  
     <span data-ttu-id="ef310-114">WITH 키워드를 사용하여 계산 멤버를 만드는 방법에 대한 자세한 내용은 [쿼리 범위 셀 계산 만들기&#40;MDX&#41;](../../multidimensional-models-olap-logical-cube-objects/calculations.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ef310-114">For more information about how to use the WITH keyword to create calculated members, see [Creating Query-Scoped Cell Calculations &#40;MDX&#41;](../../multidimensional-models-olap-logical-cube-objects/calculations.md).</span></span>  
  
-   <span data-ttu-id="ef310-115">**세션 범위** 범위가 쿼리 컨텍스트보다 넓은 계산 멤버, 즉 범위가 MDX 세션의 수명인 계산 멤버를 만들려면 CREATE CELL CALCULATION 또는 ALTER CUBE 문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ef310-115">**Session-scoped** To create a calculated member whose scope is wider than the context of the query, that is, whose scope is the lifetime of the MDX session, you use either the CREATE CELL CALCULATION or ALTER CUBE statement.</span></span>  
  
     <span data-ttu-id="ef310-116">CREATE CELL CALCULATION 또는 ALTER CUBE 문을 사용하여 세션에서 계산 셀을 만드는 방법에 대한 자세한 내용은 [세션 범위 계산 셀 만들기](mdx-cell-calculations-session-scoped-calculated-cells.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ef310-116">For more information about how to use either the CREATE CELL CALCULATION or ALTER CUBE statement to create calculated cells in a session, see [Creating Session-Scoped Calculated Cells](mdx-cell-calculations-session-scoped-calculated-cells.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef310-117">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ef310-117">See Also</span></span>  
 <span data-ttu-id="ef310-118">[ALTER CUBE 문은 MDX &#40;&#41;](/sql/mdx/mdx-data-definition-alter-cube) </span><span class="sxs-lookup"><span data-stu-id="ef310-118">[ALTER CUBE Statement &#40;MDX&#41;](/sql/mdx/mdx-data-definition-alter-cube) </span></span>  
 <span data-ttu-id="ef310-119">[MDX를 &#40;셀 계산 문 만들기&#41;](/sql/mdx/mdx-data-definition-create-cell-calculation) </span><span class="sxs-lookup"><span data-stu-id="ef310-119">[CREATE CELL CALCULATION Statement &#40;MDX&#41;](/sql/mdx/mdx-data-definition-create-cell-calculation) </span></span>  
 <span data-ttu-id="ef310-120">[MDX&#41;&#40;쿼리 범위 셀 계산 만들기](../../multidimensional-models-olap-logical-cube-objects/calculations.md) </span><span class="sxs-lookup"><span data-stu-id="ef310-120">[Creating Query-Scoped Cell Calculations &#40;MDX&#41;](../../multidimensional-models-olap-logical-cube-objects/calculations.md) </span></span>  
 [<span data-ttu-id="ef310-121">MDX 쿼리 기본 사항&#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="ef310-121">MDX Query Fundamentals &#40;Analysis Services&#41;</span></span>](mdx-query-fundamentals-analysis-services.md)  
  
  
