---
title: Slicer 축의 내용 지정 (MDX) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- slicer axis
- filtering data [MDX]
ms.assetid: c56b0a70-cdec-427f-990e-425290344e7d
author: minewiskan
ms.author: owend
ms.openlocfilehash: 8620c54970ea14a2ac01c85262a372d2b3db0d68
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728879"
---
# <a name="specifying-the-contents-of-a-slicer-axis-mdx"></a><span data-ttu-id="bae23-102">Slicer 축의 내용 지정(MDX)</span><span class="sxs-lookup"><span data-stu-id="bae23-102">Specifying the Contents of a Slicer Axis (MDX)</span></span>
  <span data-ttu-id="bae23-103">slicer 축은 지정된 멤버와 교차되는 데이터만 반환되도록 반환 데이터를 제한하여 MDX SELECT 문에 의해 반환된 데이터를 필터링합니다.</span><span class="sxs-lookup"><span data-stu-id="bae23-103">The slicer axis filters the data returned by the Multidimensional Expressions (MDX) SELECT statement, restricting the returned data so that only data intersecting with the specified members will be returned.</span></span> <span data-ttu-id="bae23-104">slicer 축은 표시되지 않는 쿼리의 추가 축으로 간주할 수 있으며</span><span class="sxs-lookup"><span data-stu-id="bae23-104">It can be thought of as an invisible extra axis in a query.</span></span> <span data-ttu-id="bae23-105">MDX에서 SELECT 문의 WHERE 절에 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="bae23-105">The slicer axis is defined in the WHERE clause of the SELECT statement in MDX.</span></span>  
  
## <a name="slicer-axis-syntax"></a><span data-ttu-id="bae23-106">Slicer 축 구문</span><span class="sxs-lookup"><span data-stu-id="bae23-106">Slicer Axis Syntax</span></span>  
 <span data-ttu-id="bae23-107">slicer 축을 명시적으로 지정하려면 다음 구문에 설명된 것과 같이 MDX에서 `<SELECT slicer axis clause>` 를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="bae23-107">To explicitly specify a slicer axis, you  using the `<SELECT slicer axis clause>` in MDX, as described in the following syntax:</span></span>  
  
```  
<SELECT slicer axis clause> ::=  WHERE Set_Expression  
```  
  
 <span data-ttu-id="bae23-108">표시된 slicer 축 구문에서 `Set_Expression` 은 절을 계산할 목적의 집합으로 취급되는 튜플 식 또는 집합 식을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bae23-108">In the slicer axis syntax shown, `Set_Expression` can take either a tuple expression, which is treated as a set for the purposes of evaluating the clause, or a set expression.</span></span> <span data-ttu-id="bae23-109">집합 식이 지정된 경우 MDX는 집합과 함께 모든 튜플에 있는 결과 셀을 집계하여 집합을 계산하려고 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="bae23-109">If a set expression is specified, MDX will try to evaluate the set, aggregating the result cells in every tuple along the set.</span></span> <span data-ttu-id="bae23-110">즉, MDX는 집합에 대해 [Aggregate](/sql/mdx/aggregate-mdx) 함수 사용을 시도하여 각 측정값을 관련 집계 함수로 집계합니다.</span><span class="sxs-lookup"><span data-stu-id="bae23-110">In other words, MDX will try to use the [Aggregate](/sql/mdx/aggregate-mdx) function on the set, aggregating each measure by its associated aggregation function.</span></span> <span data-ttu-id="bae23-111">또한 집합 식을 특성 계층 멤버의 크로스 조인으로 표현할 수 없는 경우 MDX는 slicer에 대한 집합 식 범위에 속하지 않는 셀을 계산 목적의 Null로 취급합니다.</span><span class="sxs-lookup"><span data-stu-id="bae23-111">Also, if the set expression cannot be expressed as a crossjoin of attribute hierarchy members, MDX treats cells that fall outside of the set expression for the slicer as null for evaluation purposes.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="bae23-112">SQL의 WHERE 절과 달리, MDX SELECT 문의 WHERE 절은 쿼리의 Rows 축에서 반환되는 항목을 직접 필터링하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bae23-112">Unlike the WHERE clause in SQL, the WHERE clause of an MDX SELECT statement never directly filters what is returned on the Rows axis of a query.</span></span> <span data-ttu-id="bae23-113">쿼리의 Rows 또는 Columns 축에 나타나는 항목을 필터링하는 데 FILTER, NONEMPTY, TOPCOUNT 등의 다양한 MDX 함수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bae23-113">To filter what appears on the Rows or Columns axis of a query, you can use a variety of MDX functions, for example FILTER, NONEMPTY and TOPCOUNT.</span></span>  
  
### <a name="implicit-slicer-axis"></a><span data-ttu-id="bae23-114">암시적 Slicer 축</span><span class="sxs-lookup"><span data-stu-id="bae23-114">Implicit Slicer Axis</span></span>  
 <span data-ttu-id="bae23-115">큐브 내에 있는 계층의 멤버가 쿼리 축에 명시적으로 포함되지 않은 경우 해당 계층의 기본 멤버는 slicer 축에 암시적으로 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="bae23-115">If a member from a hierarchy within the cube is not explicitly included in a query axis, the default member from that hierarchy is implicitly included in the slicer axis.</span></span> <span data-ttu-id="bae23-116">기본 멤버에 대한 자세한 내용은 [기본 멤버 정의](../attribute-properties-define-a-default-member.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="bae23-116">For more information about default members, see [Define a Default Member](../attribute-properties-define-a-default-member.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="bae23-117">예</span><span class="sxs-lookup"><span data-stu-id="bae23-117">Examples</span></span>  
 <span data-ttu-id="bae23-118">다음 쿼리는 WHERE 절을 포함하지 않으며 모든 Calendar Year의 Internet Sales Amount 측정값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="bae23-118">The following query does not include a WHERE clause, and returns the value of the Internet Sales Amount measure for all Calendar Years:</span></span>  
  
```  
SELECT {[Measures].[Internet Sales Amount]} ON COLUMNS,  
[Date].[Calendar Year].MEMBERS ON ROWS  
FROM [Adventure Works]  
```  
  
 <span data-ttu-id="bae23-119">다음과 같이 WHERE 절을 추가하는 경우</span><span class="sxs-lookup"><span data-stu-id="bae23-119">Adding a WHERE clause, as follows:</span></span>  
  
```  
SELECT {[Measures].[Internet Sales Amount]} ON COLUMNS,  
[Date].[Calendar Year].MEMBERS ON ROWS  
FROM [Adventure Works]  
WHERE([Customer].[Customer Geography].[Country].&[United States])  
  
```  
  
 <span data-ttu-id="bae23-120">쿼리의 Rows 또는 Columns에서 반환되는 항목은 변경되지 않으며 각 셀에 대해 반환되는 값이 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="bae23-120">does not change what is returned on Rows or Columns in the query; it changes the values returned for each cell.</span></span> <span data-ttu-id="bae23-121">이 예제에서 쿼리는 United States에 거주하는 Customer에만 해당하는 모든 Calendar Year의 Internet Sales Amount 값을 반환하도록 조각화됩니다. 서로 다른 계층의 여러 멤버를 WHERE 절에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bae23-121">In this example, the query is sliced so that it returns the value of Internet Sales Amount for all Calendar Years but only for Customers who live in the United States.Multiple members from different hierarchies can be added to the WHERE clause.</span></span> <span data-ttu-id="bae23-122">다음 쿼리는 United States에 거주하며 Category Bikes에서 Product를 구입한 Customer에 해당하는 모든 Calendar Year의 Internet Sales Amount 값을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="bae23-122">The following query shows the value of Internet Sales Amount for all Calendar Years for Customers who live in the United States and who bought Products in the Category Bikes:</span></span>  
  
```  
SELECT {[Measures].[Internet Sales Amount]} ON COLUMNS,  
[Date].[Calendar Year].MEMBERS ON ROWS  
FROM [Adventure Works]  
WHERE([Customer].[Customer Geography].[Country].&[United States], [Product].[Category].&[1])  
```  
  
 <span data-ttu-id="bae23-123">동일한 계층에서 여러 멤버를 사용하려면 WHERE 절에 집합을 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bae23-123">If you want to use multiple members from the same hierarchy, you need to include a set in the WHERE clause.</span></span> <span data-ttu-id="bae23-124">예를 들어 다음 쿼리는 United States 또는 United Kingdom에 거주하며 Category Bikes에서 Product를 구입한 Customer에 해당하는 모든 Calendar Year의 Internet Sales Amount 값을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="bae23-124">For example, the following query shows the value of Internet Sales Amount for all Calendar Years for Customers who bought Products in the Category Bikes and live in either the United States or the United Kingdom:</span></span>  
  
```  
SELECT {[Measures].[Internet Sales Amount]} ON COLUMNS,  
[Date].[Calendar Year].MEMBERS ON ROWS  
FROM [Adventure Works]  
WHERE(  
{[Customer].[Customer Geography].[Country].&[United States]  
, [Customer].[Customer Geography].[Country].&[United Kingdom]}  
, [Product].[Category].&[1])  
  
```  
  
 <span data-ttu-id="bae23-125">위에서 설명했듯이 WHERE 절에서 집합을 사용하면 해당 집합의 모든 멤버에 대한 값이 암시적으로 집계됩니다.</span><span class="sxs-lookup"><span data-stu-id="bae23-125">As mentioned above, using a set in the WHERE clause will implicitly aggregate values for all members in the set.</span></span> <span data-ttu-id="bae23-126">이 경우 쿼리는 각 셀의 United States 및 United Kingdom에 대한 집계된 값을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="bae23-126">In this case, the query shows aggregated values for the United States and the United Kingdom in each cell.</span></span>  
  
  
