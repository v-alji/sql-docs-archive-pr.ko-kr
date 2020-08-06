---
title: 계산 컨텍스트 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: aec8aa98-b77d-4f8f-9684-2618b1d8e970
author: minewiskan
ms.author: owend
ms.openlocfilehash: e6d14df51c6ec37fb96520af7acf207227ae4ea5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87733212"
---
# <a name="calculation-context"></a><span data-ttu-id="e5872-102">계산 컨텍스트</span><span class="sxs-lookup"><span data-stu-id="e5872-102">Calculation Context</span></span>
  <span data-ttu-id="e5872-103">계산 컨텍스트는 식이 계산되고 모든 좌표가 명시적으로 알려지거나 식에서 파생될 수 있는 큐브의 알려진 하위 공간입니다.</span><span class="sxs-lookup"><span data-stu-id="e5872-103">The calculation context is the known subspace of the cube where an expression is evaluated and all coordinates are either explicitly known or can be derived from the expression.</span></span>  
  
## <a name="determining-the-calculation-context"></a><span data-ttu-id="e5872-104">계산 컨텍스트 확인</span><span class="sxs-lookup"><span data-stu-id="e5872-104">Determining the calculation context</span></span>  
 <span data-ttu-id="e5872-105">모든 집합, 멤버, 튜플, 또는 숫자 함수는 MDX 식 또는 문 전체의 컨텍스트에서 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="e5872-105">Every set, member, tuple, or numeric function executes in the context of the entire MDX expression or statement.</span></span> <span data-ttu-id="e5872-106">튜플과 같은 인수가 함수에 전달될 때는 큐브 공간의 일부 좌표만 명시적으로 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="e5872-106">When an argument, such as a tuple, is passed to a function, only some of the coordinates in the cube space are explicitly provided.</span></span> <span data-ttu-id="e5872-107">다른 좌표는 현재 계산 컨텍스트에 따라 얻습니다.</span><span class="sxs-lookup"><span data-stu-id="e5872-107">The other coordinates are obtained based on the current calculation context.</span></span>  
  
 <span data-ttu-id="e5872-108">지정되지 않은 셀 좌표 및 특성 멤버의 계산 컨텍스트는 다음 순서에 따라 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="e5872-108">The calculation context for unspecified cell coordinates and attribute members is determined in the following order:</span></span>  
  
1.  <span data-ttu-id="e5872-109">FROM 절(해당되는 경우) - 이 절은 큐브 전체를 지정하거나 SELECT 문 형식으로 하위 큐브를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e5872-109">The FROM clause (if applicable) - this clause can either specify an entire cube or can specify a subcube in the form of a SELECT statement.</span></span>  
  
2.  <span data-ttu-id="e5872-110">WHERE 절(해당되는 경우) - 이 절은 *slicer 축*이라고도 하며 쿼리에서 열 및 행 축에 반환되는 멤버를 제한하는 집합, 튜플 또는 멤버를 지정하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="e5872-110">The WHERE clause (if applicable) - this clause, which is also known as the *slicer axis*, on which you specify a set, tuple, or member that restricts the members returned on the column and row axis by a query.</span></span> <span data-ttu-id="e5872-111">개념적으로 열 또는 행 축에 명시적으로 지정되지 않은 모든 특성 계층의 기본 멤버는 slicer 축의 일부입니다.</span><span class="sxs-lookup"><span data-stu-id="e5872-111">Conceptually, the default member of every attribute hierarchy that is not explicitly specified on column or row axis is part of the slicer axis.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e5872-112">특정 특성의 셀 좌표가 slicer 축과 다른 축 모두에서 지정된 경우 축의 집합 멤버를 결정할 때는 함수에 지정된 좌표가 우선합니다.</span><span class="sxs-lookup"><span data-stu-id="e5872-112">When cell coordinates for a particular attribute are specified on both the slicer axis and on another axis, the coordinates specified in the function may take precedence in determining the members of the set on the axis.</span></span> <span data-ttu-id="e5872-113">[Filter(MDX)](/sql/mdx/filter-mdx) 및 [Order(MDX)](/sql/mdx/order-mdx) 함수가 이러한 함수의 예입니다. 즉, WHERE 절이나 FROM 절의 SELECT 문을 사용하여 계산 컨텍스트에서 제외된 특성 멤버를 기준으로 결과를 필터링하거나 정렬할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e5872-113">The [Filter (MDX)](/sql/mdx/filter-mdx) and [Order (MDX)](/sql/mdx/order-mdx) functions are examples of such functions - you can filter or order a result by attribute members that are excluded from the calculation context by the WHERE clause, or by a SELECT statement in the FROM clause.</span></span>  
  
3.  <span data-ttu-id="e5872-114">쿼리 또는 식에 정의된 명명된 집합 및 계산 멤버</span><span class="sxs-lookup"><span data-stu-id="e5872-114">The named sets and calculated members defined in the query or expression.</span></span>  
  
4.  <span data-ttu-id="e5872-115">행 및 열 축에 지정된 튜플과 집합. 이때 행, 열 또는 slicer 축에 나타나지 않는 특성에는 기본 멤버를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="e5872-115">The tuples and sets specified on the row and column axes, utilizing the default member for attributes that do not appear on the row, column, or slicer axis.</span></span>  
  
5.  <span data-ttu-id="e5872-116">각 축의 큐브 또는 하위 큐브 셀. 이때 축의 빈 튜플은 제거하고 HAVING 절을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="e5872-116">The cube or subcube cells on each axis, eliminating empty tuples on the axis and applying the HAVING clause.</span></span>  
  
6.  <span data-ttu-id="e5872-117">자세한 내용은 [쿼리에 큐브 컨텍스트 설정&#40;MDX&#41;](establishing-cube-context-in-a-query-mdx.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e5872-117">For more information, see [Establishing Cube Context in a Query &#40;MDX&#41;](establishing-cube-context-in-a-query-mdx.md).</span></span>  
  
 <span data-ttu-id="e5872-118">다음 쿼리에서 행 축의 계산 컨텍스트는 WHERE 절에 지정된 Country 특성 멤버와 Calendar Year 특성 멤버에 의해 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="e5872-118">In the following query, the calculation context for the row axis is restricted by the Country attribute member and the Calendar Year attribute member that are specified in the WHERE clause.</span></span>  
  
```  
SELECT Customer.City.City.Members ON 0  
FROM [Adventure Works]  
WHERE (Customer.Country.France, [Date].[Calendar].[Calendar Year].[CY 2004],  
   Measures.[Internet Sales Amount])  
```  
  
 <span data-ttu-id="e5872-119">그러나 행 축에 `FILTER` 함수를 지정하여 이 쿼리를 수정하고 `FILTER` 함수에서 Calendar Year 특성 계층 멤버를 사용하면 열 축의 집합 멤버에 대한 계산 컨텍스트를 지정하는 데 사용된 Calendar Year 특성 계층의 특성 멤버가 수정될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e5872-119">However, if you modify this query by specifying the `FILTER` function on the row axis, and utilize a Calendar Year attribute hierarchy member in the `FILTER` function, then the attribute member from the Calendar Year attribute hierarchy that is used to provide the calculation context for the members of the set on the column axis can be modified.</span></span>  
  
```  
SELECT FILTER  
   (  
      Customer.City.City.Members,   
         ([Date].[Calendar].[Calendar Year].[CY 2003],  
            Measures.[Internet Order Quantity]) > 75   
   ) ON 0  
FROM [Adventure Works]  
WHERE (Customer.Country.France,  
   [Date].[Calendar].[Calendar Year].[CY 2004],  
   Measures.[Internet Sales Amount])  
```  
  
 <span data-ttu-id="e5872-120">이 쿼리에서 Calendar Year 특성 계층의 명목적 계산 컨텍스트는 CY 2004이지만 열 축에 나타나는 튜플의 셀에 대한 계산 컨텍스트는 Calendar Year 특성 계층의 CY 2003 멤버에 따라 필터링됩니다.</span><span class="sxs-lookup"><span data-stu-id="e5872-120">In the previous query, the calculation context for the cells in the tuples that appear on the column axis is filtered by the CY 2003 member of the Calendar Year attribute hierarchy, even though the nominal calculation context for the Calendar Year attribute hierarchy is CY 2004.</span></span> <span data-ttu-id="e5872-121">또한 이 계산 컨텍스트는 Internet Order Quantity 측정값에 따라서도 필터링됩니다.</span><span class="sxs-lookup"><span data-stu-id="e5872-121">Furthermore, it is filtered by the Internet Order Quantity measure.</span></span> <span data-ttu-id="e5872-122">그러나 열 축의 집합 멤버가 설정되고 나면 해당 축에 나타나는 멤버의 값에 대한 계산 컨텍스트는 다시 WHERE 절에 따라 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="e5872-122">However, once the members of the set on the column axis is set, the calculation context for the values for the members that appear on the axis is again determined by the WHERE clause.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="e5872-123">쿼리 성능을 향상시키려면 멤버와 튜플을 확인 과정에서 가능한 한 빨리 제거해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5872-123">To increase query performance, you should eliminate members and tuples as early in the resolution process as possible.</span></span> <span data-ttu-id="e5872-124">이렇게 하면 쿼리할 때 최종 멤버 집합에 대한 복잡한 계산이 가능한 가장 적은 수의 셀에 대해 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="e5872-124">In this manner, complex query time calculations on the final set of members operate on the fewest cells possible.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5872-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e5872-125">See Also</span></span>  
 <span data-ttu-id="e5872-126">[MDX&#41;&#40;쿼리에 큐브 컨텍스트 설정](establishing-cube-context-in-a-query-mdx.md) </span><span class="sxs-lookup"><span data-stu-id="e5872-126">[Establishing Cube Context in a Query &#40;MDX&#41;](establishing-cube-context-in-a-query-mdx.md) </span></span>  
 <span data-ttu-id="e5872-127">[MDX 쿼리 기본 사항 &#40;Analysis Services&#41;](mdx-query-fundamentals-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="e5872-127">[MDX Query Fundamentals &#40;Analysis Services&#41;](mdx-query-fundamentals-analysis-services.md) </span></span>  
 [<span data-ttu-id="e5872-128">MDX의 주요 개념&#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="e5872-128">Key Concepts in MDX &#40;Analysis Services&#41;</span></span>](../key-concepts-in-mdx-analysis-services.md)  
  
  
