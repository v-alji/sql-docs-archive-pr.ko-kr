---
title: 큐브 공간 | Microsoft Docs
ms.custom: ''
ms.date: 07/17/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: c3a012b4-9ca0-4fb8-9c26-5ecc0e2e2b2b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 0a6a6da73815f06aa5ab80f6ad5a9d06227ed842
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649739"
---
# <a name="cube-space"></a><span data-ttu-id="2efef-102">큐브 공간</span><span class="sxs-lookup"><span data-stu-id="2efef-102">Cube Space</span></span>
  <span data-ttu-id="2efef-103">큐브 공간은 큐브 특성 계층의 멤버와 큐브의 측정값을 곱하여 생성된 공간입니다.</span><span class="sxs-lookup"><span data-stu-id="2efef-103">Cube space is the product of the members of a cube's attribute hierarchies with the cube's measures.</span></span> <span data-ttu-id="2efef-104">따라서 큐브 공간은 큐브의 모든 특성 계층 멤버와 큐브의 측정값을 곱한 결과의 조합으로 결정되며 큐브의 최대 크기를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="2efef-104">Therefore, the cube space is determined by the combinatorial product of all attribute hierarchy members in the cube and the cube's measures and defines the maximum size of the cube.</span></span> <span data-ttu-id="2efef-105">실제로는 조합이 불가능한 것으로 간주될 수도 있지만(예: 도시는 파리이고 국가는 잉글랜드, 스페인, 일본 또는 인도인 조합의 경우) 이 공간은 특성 계층 멤버의 가능한 모든 조합을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="2efef-105">It is important to note that this space includes all possible combinations of attribute hierarchy members; even combinations that might be deem as impossible in the real world i.e. combinations where the city is Paris and the countries are England or Spain or Japan or India or elsewhere.</span></span>  
  
## <a name="autoexists-and-cube-space"></a><span data-ttu-id="2efef-106">AUTOEXIST 및 큐브 공간</span><span class="sxs-lookup"><span data-stu-id="2efef-106">Autoexists and cube space</span></span>  
 <span data-ttu-id="2efef-107">*AUTOEXIST* 의 개념은 이 큐브 공간을 실제로 존재하는 셀로 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="2efef-107">The concept of *autoexists* limits this cube space to those cells that actually exist.</span></span> <span data-ttu-id="2efef-108">한 차원에 있는 특성 계층의 멤버가 동일한 차원에 있는 다른 특성 계층의 멤버와 함께 존재하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2efef-108">Members of an attribute hierarchy in a dimension may not exist with members of another attribute hierarchy in the same dimension.</span></span>  
  
 <span data-ttu-id="2efef-109">예를 들어 City 특성 계층, Country 특성 계층 및 Internet Sales Amount 측정값이 있는 큐브에서 이 큐브의 공간에는 서로 함께 존재하는 멤버만 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="2efef-109">For example, if you have a cube that has a City attribute hierarchy, a Country attribute hierarchy, and an Internet Sales Amount measure, the space of this cube only includes those members that exist with each other.</span></span> <span data-ttu-id="2efef-110">예를 들어 City 특성 계층에 New York, London, Paris, Tokyo 및 Melbourne이 포함되어 있고 Country 특성 계층에 United States, United Kingdom, France, Japan 및 Australia가 포함되어 있는 경우 Paris와 United States가 교차하는 지점의 공간(셀)은 해당 큐브 공간에 포함되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2efef-110">For example, if the City attribute hierarchy includes the cities New York, London, Paris, Tokyo, and Melbourne; and the Country attribute hierarchy includes the countries United States, United Kingdom, France, Japan, and Australia; then the space of the cube does not include the space (cell) at the intersection of Paris and United States.</span></span>  
  
 <span data-ttu-id="2efef-111">존재하지 않는 셀을 쿼리하면 존재하지 않는 셀에서는 Null이 반환됩니다. 즉, 이 셀에는 계산이 들어 있지 않으며 이 공간에 쓰는 계산은 정의할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2efef-111">When querying cells that do not exist, non-existing cells return nulls; that is, they cannot contain calculations and you cannot define a calculation that writes to this space.</span></span> <span data-ttu-id="2efef-112">예를 들어 다음 문은 존재하지 않는 셀을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="2efef-112">For example, the following statement includes cells that do not exist.</span></span>  
  
```  
SELECT [Customer].[Gender].[Gender].Members ON COLUMNS,  
{[Customer].[Customer].[Aaron A. Allen]  
   ,[Customer].[Customer].[Abigail Clark]} ON ROWS   
FROM [Adventure Works]  
WHERE Measures.[Internet Sales Amount]  
```  
  
> [!NOTE]  
>  <span data-ttu-id="2efef-113">이 쿼리에서는 [Members(집합)(MDX)](/sql/mdx/members-set-mdx) 함수를 사용하여 Gender 특성 계층의 멤버 집합을 열 축에 반환하고 Customer 특성 계층의 지정한 멤버 집합과 이 집합을 행 축에서 교차시킵니다.</span><span class="sxs-lookup"><span data-stu-id="2efef-113">This query uses the [Members (Set) (MDX)](/sql/mdx/members-set-mdx) function to return the set of members of the Gender attribute hierarchy on the column axis, and crosses this set with the specified set of members from the Customer attribute hierarchy on the row axis.</span></span>  
  
 <span data-ttu-id="2efef-114">앞의 쿼리를 실행하면 Aaron A. Allen과 Female이 교차하는 셀에는 Null이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="2efef-114">When you execute the previous query, the cell at the intersection of Aaron A. Allen and Female displays a null.</span></span> <span data-ttu-id="2efef-115">마찬가지로 Abigail Clark와 Male이 교차하는 셀에도 Null이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="2efef-115">Similarly, the cell at the intersection of Abigail Clark and Male displays a null.</span></span> <span data-ttu-id="2efef-116">이러한 셀은 존재하지 않으며 값을 포함할 수 없지만 쿼리에서 반환되는 결과에는 존재하지 않는 셀도 나타날 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2efef-116">These cells do not exist and cannot contain a value, but cells that do not exist can appear in the result returned by a query.</span></span>  
  
 <span data-ttu-id="2efef-117">[Crossjoin(MDX)](/sql/mdx/crossjoin-mdx) 함수를 사용하여 동일한 차원에 있는 특성 계층의 특성 계층 멤버 간 교차곱을 반환할 때 AUTOEXIST는 전체 카티전 곱이 반환되는 것이 아니라 실제 존재하는 튜플 집합만 반환되도록 튜플을 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="2efef-117">When you use the [Crossjoin (MDX)](/sql/mdx/crossjoin-mdx) function to return the cross-product of attribute hierarchy members from attribute hierarchies in the same dimension, auto-exists limits those tuples being returned to the set of tuples that actually exist, rather than returning a full Cartesian product.</span></span> <span data-ttu-id="2efef-118">예를 들어 다음 쿼리를 실행한 다음 실행 결과를 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="2efef-118">For example, run and then examine the results from the execution of the following query.</span></span>  
  
```  
SELECT CROSSJOIN  
   (  
      {[Customer].[Country].[United States]},  
         [Customer].[State-Province].Members  
  ) ON 0   
FROM [Adventure Works]  
WHERE Measures.[Internet Sales Amount]  
```  
  
> [!NOTE]  
>  <span data-ttu-id="2efef-119">0은 열 축을 지정하는 데 사용되었으며 열 축을 나타내는 axis(0)을 줄여 쓴 것입니다.</span><span class="sxs-lookup"><span data-stu-id="2efef-119">Notice that 0 is used to designate the column axis, which is shorthand for axis(0) - which is the column axis.</span></span>  
  
 <span data-ttu-id="2efef-120">앞의 쿼리는 쿼리의 각 특성 계층에서 서로 함께 존재하는 멤버의 셀만 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="2efef-120">The previous query only returns cells for members from each attribute hierarchy in the query that exist with each other.</span></span> <span data-ttu-id="2efef-121">이전 쿼리는 [ \* (Crossjoin) (MDX)](/sql/mdx/crossjoin-mdx) 함수의 새로운 \* 변형을 사용 하 여 작성할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2efef-121">The previous query can also be written using the new \* variant of the [\* (Crossjoin) (MDX)](/sql/mdx/crossjoin-mdx) function.</span></span>  
  
```  
SELECT   
   [Customer].[Country].[United States] *   
      [Customer].[State-Province].Members  
ON 0   
FROM [Adventure Works]  
WHERE Measures.[Internet Sales Amount]  
```  
  
 <span data-ttu-id="2efef-122">이 쿼리는 다음과 같이 작성할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2efef-122">The previous query could also be written in the following manner:</span></span>  
  
```  
SELECT [Customer].[State-Province].Members  
ON 0   
FROM [Adventure Works]  
WHERE (Measures.[Internet Sales Amount],  
   [Customer].[Country].[United States])  
```  
  
 <span data-ttu-id="2efef-123">결과 집합의 메타데이터는 다르지만 반환되는 셀 값은 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="2efef-123">The cells values returned will be identical, although the metadata in the result set will be different.</span></span> <span data-ttu-id="2efef-124">예를 들어 앞의 쿼리를 사용할 경우 Country 계층은 WHERE 절을 통해 slicer 축으로 이동되므로 결과 집합에 명시적으로 나타나지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2efef-124">For example, with the previous query, the Country hierarchy was moved to the slicer axis (in the WHERE clause) and therefore does not appear explicitly in the result set.</span></span>  
  
 <span data-ttu-id="2efef-125">위의 세 쿼리는 각각에서 자동 존재 동작의 효과를 보여 줍니다 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="2efef-125">Each of these three previous queries demonstrates the effect of the auto-exists behavior in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].</span></span>  
  
## <a name="user-defined-hierarchies-and-cube-space"></a><span data-ttu-id="2efef-126">사용자 정의 계층 및 큐브 공간</span><span class="sxs-lookup"><span data-stu-id="2efef-126">User-Defined Hierarchies and Cube Space</span></span>  
 <span data-ttu-id="2efef-127">이 항목의 앞에 나온 예제에서는 특성 계층을 사용하여 큐브 공간 내의 위치를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="2efef-127">The previous examples in this topic define positions in cube space by using attribute hierarchies.</span></span> <span data-ttu-id="2efef-128">그러나 차원의 특성 계층에 따라 정의한 사용자 정의 계층을 사용하여 큐브 공간 내의 위치를 정의할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2efef-128">However, you can also define a position in cube space by using user-defined hierarchies that have been defined based on attribute hierarchies in a dimension.</span></span> <span data-ttu-id="2efef-129">사용자 정의 계층은 사용자가 큐브 데이터를 쉽게 찾을 수 있도록 디자인된 특성 계층의 한 계층입니다.</span><span class="sxs-lookup"><span data-stu-id="2efef-129">A user-defined hierarchy is a hierarchy of attribute hierarchies designed to facilitate browsing of cube data by users.</span></span>  
  
 <span data-ttu-id="2efef-130">예를 들어 이전 섹션의 `CROSSJOIN` 쿼리를 다음과 같이 작성할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2efef-130">For example, the `CROSSJOIN` query in the previous section could also have been written as follows:</span></span>  
  
```  
SELECT CROSSJOIN  
   (  
      {[Customer].[Country].[United States]},  
         [Customer].[Customer Geography].[State-Province].Members  
   )   
ON 0   
FROM [Adventure Works]  
WHERE Measures.[Internet Sales Amount]  
```  
  
 <span data-ttu-id="2efef-131">이 쿼리에서 Customer 차원 내의 사용자 정의 계층인 Customer Geography는 이전에 특성 계층을 사용하여 정의한 큐브 공간 내의 위치를 정의하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="2efef-131">In the previous query, the Customer Geography user-defined hierarchy within the Customer dimension is used to define the position in cube space that was previously defined by using an attribute hierarchy.</span></span> <span data-ttu-id="2efef-132">즉, 큐브 공간 내의 동일한 위치를 특성 계층이나 사용자 정의 계층 중 하나를 사용하여 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2efef-132">The identical position in cube space can be defined by using either attribute hierarchies or user-defined hierarchies.</span></span>  
  
##  <a name="attribute-relationships-and-cube-space"></a><a name="AttribRelationships"></a><span data-ttu-id="2efef-133">특성 관계 및 큐브 공간</span><span class="sxs-lookup"><span data-stu-id="2efef-133">Attribute Relationships and Cube Space</span></span>  
 <span data-ttu-id="2efef-134">관련된 특성 간의 특성 관계를 정의하면 적절한 집계를 쉽게 만들 수 있으므로 쿼리 성능이 향상되며 특성 계층 멤버와 함께 나타나는 관련 특성 계층의 멤버에 영향을 줄 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2efef-134">Defining attribute relationships between related attributes improves query performance (by facilitating the creation of appropriate aggregations) and affects the member of a related attribute hierarchy that appears with an attribute hierarchy member.</span></span> <span data-ttu-id="2efef-135">예를 들어 City 특성 계층의 멤버를 포함하는 튜플을 정의할 때 해당 튜플에 Country 특성 계층 멤버가 명시적으로 정의되어 있지 않으면 기본 Country 특성 계층 멤버가 Country 특성 계층의 관련 멤버가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2efef-135">For example, when you define a tuple that includes a member from the City attribute hierarchy and the tuple does not explicitly define the Country attribute hierarchy member, you might expect that the default Country attribute hierarchy member would be the related member of the Country attribute hierarchy.</span></span> <span data-ttu-id="2efef-136">그러나 이는 City 특성 계층과 Country 특성 계층 간에 특성 관계가 정의되어 있는 경우에만 해당됩니다.</span><span class="sxs-lookup"><span data-stu-id="2efef-136">However, this is only true if an attribute relationship is defined between the City attribute hierarchy and the Country attribute hierarchy.</span></span>  
  
 <span data-ttu-id="2efef-137">다음 예에서는 쿼리에 명시적으로 포함되지 않은 관련 특성 계층의 멤버를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="2efef-137">The following example returns the member of a related attribute hierarchy that is not included explicitly in the query.</span></span>  
  
```  
WITH MEMBER Measures.x AS   
   Customer.Country.CurrentMember.Name  
SELECT Measures.x ON 0,  
Customer.City.Members ON 1  
FROM [Adventure Works]  
```  
  
> [!NOTE]  
>  <span data-ttu-id="2efef-138">`WITH`키워드는 [currentmember (mdx)](/sql/mdx/current-mdx) 및 [Name (mdx)](/sql/mdx/members-string-mdx) 함수와 함께 쿼리에 사용할 계산 멤버를 만드는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2efef-138">Notice that the `WITH` keyword is used with the [CurrentMember (MDX)](/sql/mdx/current-mdx) and [Name (MDX)](/sql/mdx/members-string-mdx) functions to create a calculated member for use in the query.</span></span> <span data-ttu-id="2efef-139">자세한 내용은 [기본 MDX 쿼리&#40;MDX&#41;](mdx-query-the-basic-query.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2efef-139">For more information, see [The Basic MDX Query &#40;MDX&#41;](mdx-query-the-basic-query.md).</span></span>  
  
 <span data-ttu-id="2efef-140">앞의 쿼리에서는 State 특성 계층의 각 멤버와 관련된 Country 특성 계층의 멤버 이름이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="2efef-140">In the previous query, the name of the member of the Country attribute hierarchy that is associated with each member of the State attribute hierarchy is returned.</span></span> <span data-ttu-id="2efef-141">이 경우 City 특성과 Country 특성 간의 특성 관계가 정의되어 있으므로 예상한 Country 멤버가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="2efef-141">The expected Country member appears (because an attribute relationship is defined between the City and Country attributes).</span></span> <span data-ttu-id="2efef-142">그러나 동일한 차원의 특성 계층 간에 특성 관계가 정의되어 있지 않으면 (All) 멤버가 반환됩니다. 다음 쿼리에서는 이를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2efef-142">However, if no attribute relationship were defined between attribute hierarchies in the same dimension, the (All) member would be returned, as illustrated in the following query.</span></span>  
  
```  
WITH MEMBER Measures.x AS   
   Customer.Education.Currentmember.Name  
SELECT Measures.x  ON 0,   
Customer.City.Members ON 1  
FROM [Adventure Works]  
```  
  
 <span data-ttu-id="2efef-143">이 쿼리에서는 Education과 City 간의 관계가 없으므로 (All) 멤버("All Customers")가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="2efef-143">In the previous query, the (All) member ("All Customers") is returned, because there is no relationship between Education and City.</span></span> <span data-ttu-id="2efef-144">따라서 Education 특성 계층의 (All) 멤버는 Education 멤버가 명시적으로 지정되지 않은 경우 City 특성 계층이 관련된 모든 튜플에서 사용되는 Education 특성 계층의 기본 멤버입니다.</span><span class="sxs-lookup"><span data-stu-id="2efef-144">Therefore, the (All) member of the Education attribute hierarchy would be the default member of the Education attribute hierarchy used in any tuple involving the City attribute hierarchy where an Education member is not explicitly provided.</span></span>  
  
## <a name="calculation-context"></a><span data-ttu-id="2efef-145">계산 컨텍스트</span><span class="sxs-lookup"><span data-stu-id="2efef-145">Calculation Context</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2efef-146">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2efef-146">See Also</span></span>  
 <span data-ttu-id="2efef-147">[MDX의 주요 개념 &#40;Analysis Services&#41;](../key-concepts-in-mdx-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="2efef-147">[Key Concepts in MDX &#40;Analysis Services&#41;](../key-concepts-in-mdx-analysis-services.md) </span></span>  
 <span data-ttu-id="2efef-148">[옥](tuples.md) </span><span class="sxs-lookup"><span data-stu-id="2efef-148">[Tuples](tuples.md) </span></span>  
 <span data-ttu-id="2efef-149">[Autoexist](autoexists.md) </span><span class="sxs-lookup"><span data-stu-id="2efef-149">[Autoexists](autoexists.md) </span></span>  
 <span data-ttu-id="2efef-150">[MDX &#40;멤버, 튜플 및 집합을 사용 하 여 작업&#41;](working-with-members-tuples-and-sets-mdx.md) </span><span class="sxs-lookup"><span data-stu-id="2efef-150">[Working with Members, Tuples, and Sets &#40;MDX&#41;](working-with-members-tuples-and-sets-mdx.md) </span></span>  
 <span data-ttu-id="2efef-151">[보이는 합계 및 비시각적 합계](visual-totals-and-non-visual-totals.md) </span><span class="sxs-lookup"><span data-stu-id="2efef-151">[Visual Totals and Non Visual Totals](visual-totals-and-non-visual-totals.md) </span></span>  
 <span data-ttu-id="2efef-152">[Mdx 언어 참조 &#40;MDX&#41;](/sql/mdx/mdx-language-reference-mdx) </span><span class="sxs-lookup"><span data-stu-id="2efef-152">[MDX Language Reference &#40;MDX&#41;](/sql/mdx/mdx-language-reference-mdx) </span></span>  
 [<span data-ttu-id="2efef-153">MDX&#40;Multidimensional Expression&#41; 참조</span><span class="sxs-lookup"><span data-stu-id="2efef-153">Multidimensional Expressions &#40;MDX&#41; Reference</span></span>](/sql/mdx/multidimensional-expressions-mdx-reference)  
  
  
