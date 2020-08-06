---
title: Autoexists | Microsoft Docs
ms.custom: ''
ms.date: 07/17/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 56283497-624c-45b5-8a0d-036b0e331d22
author: minewiskan
ms.author: owend
ms.openlocfilehash: dd35958a364456c12d58392afe3754f6adcf97b8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652416"
---
# <a name="autoexists"></a><span data-ttu-id="626bb-102">AUTOEXIST</span><span class="sxs-lookup"><span data-stu-id="626bb-102">Autoexists</span></span>
  <span data-ttu-id="626bb-103">*AUTOEXIST* 개념에서는 동일한 계층의 특성 계층 멤버로 만들 수 있는 모든 조합의 결과로 존재하는 셀이 아니라 큐브에서 실제로 존재하는 셀로 큐브 공간을 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="626bb-103">The concept of *autoexists* limits the cube space to those cells that actually exist in the cube in contraposition to those that might exist as a result of creating all possible combinations of attribute hierarchy members from the same hierarchy.</span></span> <span data-ttu-id="626bb-104">이는 한 특성 계층의 멤버가 동일한 차원에 있는 다른 특성 계층의 멤버와 함께 존재할 수 없기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="626bb-104">This is because members of one attribute hierarchy cannot exist with members of another attribute hierarchy in the same dimension.</span></span> <span data-ttu-id="626bb-105">SELECT 문에서 동일한 차원의 특성 계층이 두 개 이상 사용되는 경우 Analysis Services에서는 이러한 특성의 멤버가 다른 모든 특성의 조건에 맞게 적절히 제한되도록 특성의 식을 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="626bb-105">When two or more attribute hierarchies of the same dimension are used in a SELECT statement, Analysis Services evaluates the attributes' expressions to make sure that the members of those attributes are properly confined to meet the criteria of all other attributes.</span></span>  
  
 <span data-ttu-id="626bb-106">예를 들어 Geography 차원의 특성을 사용한다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="626bb-106">For example, suppose you are working with attributes from the Geography dimension.</span></span> <span data-ttu-id="626bb-107">City 특성의 모든 멤버를 반환하는 식과 Country 특성의 멤버를 유럽의 모든 국가로 제한하는 다른 식이 있는 경우 City 멤버는 유럽 국가에 속한 도시로만 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="626bb-107">If you have one expression that returns all members from the City attribute and another expression that confines members from the Country attribute to all countries in Europe, then this will result in the City members being confined to only those cities that belong to countries in Europe.</span></span> <span data-ttu-id="626bb-108">이것은 Analysis Services의 AUTOEXIST 특징 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="626bb-108">This is because of the autoexists characteristic of Analysis Services.</span></span> <span data-ttu-id="626bb-109">Autoexists는 한 특성 식에서 제외된 차원 레코드를 다른 특성 식에서 포함하지 않도록 하기 때문에 동일한 차원의 특성에만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="626bb-109">Autoexists only applies to attributes from the same dimension because it tries to prevent the dimension records excluded in one attribute expression from being included by the other attribute expressions.</span></span> <span data-ttu-id="626bb-110">결과적으로 차원 행에서 서로 다른 특성 식이 교차하는 것으로 AUTOEXIST를 이해할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="626bb-110">Autoexists can also be understood as the resulting intersection of the different attributes expressions over the dimension rows.</span></span>  
  
## <a name="cell-existence"></a><span data-ttu-id="626bb-111">셀 존재</span><span class="sxs-lookup"><span data-stu-id="626bb-111">Cell Existence</span></span>  
 <span data-ttu-id="626bb-112">다음 셀은 항상 존재합니다.</span><span class="sxs-lookup"><span data-stu-id="626bb-112">The following cells always exist:</span></span>  
  
-   <span data-ttu-id="626bb-113">동일한 차원에 있는 다른 계층의 멤버와 교차할 경우 모든 계층의 (All) 멤버</span><span class="sxs-lookup"><span data-stu-id="626bb-113">The (All) member, of every hierarchy, when crossed with members of other hierarchies in the same dimension.</span></span>  
  
-   <span data-ttu-id="626bb-114">비계산 형제 또는 비계산 형제의 부모나 하위 항목과 교차할 경우 계산 멤버</span><span class="sxs-lookup"><span data-stu-id="626bb-114">Calculated members when crossed with their non-calculated siblings, or with the parents or descendants of their non-calculated siblings.</span></span>  
  
## <a name="providing-non-existing-cells"></a><span data-ttu-id="626bb-115">존재하지 않는 셀 제공</span><span class="sxs-lookup"><span data-stu-id="626bb-115">Providing Non-existing cells</span></span>  
 <span data-ttu-id="626bb-116">존재하지 않는 셀은 큐브에 존재하지 않은 셀을 요청하는 쿼리나 계산에 대한 응답으로 시스템에서 제공하는 셀입니다.</span><span class="sxs-lookup"><span data-stu-id="626bb-116">A non-existing cell is a cell provided by the system as a response to a query or calculation that requests a cell that does not exist in the cube.</span></span> <span data-ttu-id="626bb-117">예를 들어 Geography 차원에 속하는 City 특성 계층 및 Country 특성 계층과 Internet Sales Amount 측정값이 있는 큐브에서 이 큐브의 공간에는 서로 함께 존재하는 멤버만 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="626bb-117">For example, if you have a cube that has a City attribute hierarchy and a Country attribute hierarchy that belong to the Geography dimension, and an Internet Sales Amount measure, the space of this cube only includes those members that exist with each other.</span></span> <span data-ttu-id="626bb-118">예를 들어 City 특성 계층에 New York, London, Paris, Tokyo 및 Melbourne이 포함되어 있고 Country 특성 계층에 United States, United Kingdom, France, Japan 및 Australia가 포함되어 있는 경우 Paris와 United States가 교차하는 지점의 공간(셀)은 해당 큐브 공간에 포함되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="626bb-118">For example, if the City attribute hierarchy includes the cities New York, London, Paris, Tokyo, and Melbourne; and the Country attribute hierarchy includes the countries United States, United Kingdom, France, Japan, and Australia; then the space of the cube does not include the space (cell) at the intersection of Paris and United States.</span></span>  
  
 <span data-ttu-id="626bb-119">존재하지 않는 셀을 쿼리하면 존재하지 않는 셀에서는 Null이 반환됩니다. 즉, 이 셀에는 계산이 들어 있지 않으며 이 공간에 쓰는 계산은 정의할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="626bb-119">When querying cells that do not exist, non-existing cells return nulls; that is, they cannot contain calculations and you cannot define a calculation that writes to this space.</span></span> <span data-ttu-id="626bb-120">예를 들어 다음 문은 존재하지 않는 셀을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="626bb-120">For example, the following statement includes cells that do not exist.</span></span>  
  
```  
SELECT [Customer].[Gender].[Gender].Members ON COLUMNS,  
{[Customer].[Customer].[Aaron A. Allen]  
   ,[Customer].[Customer].[Abigail Clark]} ON ROWS   
FROM [Adventure Works]  
WHERE Measures.[Internet Sales Amount]  
```  
  
> [!NOTE]  
>  <span data-ttu-id="626bb-121">이 쿼리에서는 [Members(집합)(MDX)](/sql/mdx/members-set-mdx) 함수를 사용하여 Gender 특성 계층의 멤버 집합을 열 축에 반환하고 Customer 특성 계층의 지정한 멤버 집합과 이 집합을 행 축에서 교차시킵니다.</span><span class="sxs-lookup"><span data-stu-id="626bb-121">This query uses the [Members (Set) (MDX)](/sql/mdx/members-set-mdx) function to return the set of members of the Gender attribute hierarchy on the column axis, and crosses this set with the specified set of members from the Customer attribute hierarchy on the row axis.</span></span>  
  
 <span data-ttu-id="626bb-122">앞의 쿼리를 실행하면 Aaron A. Allen과 Female이 교차하는 셀에는 Null이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="626bb-122">When you execute the previous query, the cell at the intersection of Aaron A. Allen and Female displays a null.</span></span> <span data-ttu-id="626bb-123">마찬가지로 Abigail Clark와 Male이 교차하는 셀에도 Null이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="626bb-123">Similarly, the cell at the intersection of Abigail Clark and Male displays a null.</span></span> <span data-ttu-id="626bb-124">이러한 셀은 존재하지 않으며 값을 포함할 수 없지만 쿼리에서 반환되는 결과에는 존재하지 않는 셀도 나타날 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="626bb-124">These cells do not exist and cannot contain a value, but cells that do not exist can appear in the result returned by a query.</span></span>  
  
 <span data-ttu-id="626bb-125">[Crossjoin(MDX)](/sql/mdx/crossjoin-mdx) 함수를 사용하여 동일한 차원에 있는 특성 계층의 특성 계층 멤버 간 교차곱을 반환할 때 AUTOEXIST는 전체 카티전 곱이 반환되는 것이 아니라 실제 존재하는 튜플 집합만 반환되도록 튜플을 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="626bb-125">When you use the [Crossjoin (MDX)](/sql/mdx/crossjoin-mdx) function to return the cross-product of attribute hierarchy members from attribute hierarchies in the same dimension, auto-exists limits those tuples being returned to the set of tuples that actually exist, rather than returning a full Cartesian product.</span></span> <span data-ttu-id="626bb-126">예를 들어 다음 쿼리를 실행한 다음 실행 결과를 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="626bb-126">For example, run and then examine the results from the execution of the following query.</span></span>  
  
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
>  <span data-ttu-id="626bb-127">0은 열 축을 지정하는 데 사용되었으며 열 축을 나타내는 axis(0)을 줄여 쓴 것입니다.</span><span class="sxs-lookup"><span data-stu-id="626bb-127">Notice that 0 is used to designate the column axis, which is shorthand for axis(0) - which is the column axis.</span></span>  
  
 <span data-ttu-id="626bb-128">앞의 쿼리는 쿼리의 각 특성 계층에서 서로 함께 존재하는 멤버의 셀만 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="626bb-128">The previous query only returns cells for members from each attribute hierarchy in the query that exist with each other.</span></span> <span data-ttu-id="626bb-129">[Crossjoin (MDX)](/sql/mdx/crossjoin-mdx) 함수의 새로운 \* 변형을 사용 하 여 이전 쿼리를 작성할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="626bb-129">The previous query can also be written using the new \* variant of the [Crossjoin (MDX)](/sql/mdx/crossjoin-mdx) function.</span></span>  
  
```  
SELECT   
   [Customer].[Country].[United States] *   
      [Customer].[State-Province].Members  
ON 0   
FROM [Adventure Works]  
WHERE Measures.[Internet Sales Amount]  
```  
  
 <span data-ttu-id="626bb-130">이 쿼리는 다음과 같이 작성할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="626bb-130">The previous query could also be written in the following manner:</span></span>  
  
```  
SELECT [Customer].[State-Province].Members  
ON 0   
FROM [Adventure Works]  
WHERE (Measures.[Internet Sales Amount],  
   [Customer].[Country].[United States])  
```  
  
 <span data-ttu-id="626bb-131">결과 집합의 메타데이터는 다르지만 반환되는 셀 값은 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="626bb-131">The cells values returned will be identical, although the metadata in the result set will be different.</span></span> <span data-ttu-id="626bb-132">예를 들어 앞의 쿼리를 사용할 경우 Country 계층은 WHERE 절을 통해 slicer 축으로 이동되므로 결과 집합에 명시적으로 나타나지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="626bb-132">For example, with the previous query, the Country hierarchy was moved to the slicer axis (in the WHERE clause) and therefore does not appear explicitly in the result set.</span></span>  
  
 <span data-ttu-id="626bb-133">위의 세 쿼리는 각각에서 자동 존재 동작의 효과를 보여 줍니다 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="626bb-133">Each of these three previous queries demonstrates the effect of the auto-exists behavior in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].</span></span>  
  
## <a name="deep-and-shallow-autoexists"></a><span data-ttu-id="626bb-134">전체 및 단순 AUTOEXIST</span><span class="sxs-lookup"><span data-stu-id="626bb-134">Deep and Shallow Autoexists</span></span>  
 <span data-ttu-id="626bb-135">AUTOEXIST는 식에 전체 또는 단순 적용될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="626bb-135">Autoexists can be applied to the expressions as Deep or Shallow.</span></span> <span data-ttu-id="626bb-136">`Deep Autoexists`는 slicer 식, 축의 하위 선택 식 등을 적용한 후 가능한 가장 범위가 큰 공간에 맞게 모든 식이 계산됨을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="626bb-136">`Deep Autoexists` means that all expressions will be evaluated to meet the deepest possible space after applying the slicer expressions, the sub select expressions in the axis, and so on.</span></span> <span data-ttu-id="626bb-137">`Shallow Autoexists`는 현재 식과 해당 결과가 현재 식에 전달되기 전에 외부 식이 계산됨을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="626bb-137">`Shallow Autoexists` means that external expressions are evaluated before the current expression and those results are passed to the current expression.</span></span> <span data-ttu-id="626bb-138">기본 설정은 전체 AUTOEXIST입니다.</span><span class="sxs-lookup"><span data-stu-id="626bb-138">The default setting is deep autoexists.</span></span>  
  
 <span data-ttu-id="626bb-139">다음 시나리오와 샘플에서는 여러 다른 유형의 AUTOEXIST를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="626bb-139">The following scenario and samples will help to illustrate the different types of Autoexistss.</span></span> <span data-ttu-id="626bb-140">다음 예에서는 두 집합인 계산 식으로서의 집합과 상수 식으로서의 집합을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="626bb-140">In the following examples two sets will be created: one as a calculated expression and the other as a constant expression.</span></span>  
  
 `//Obtain the Top 10 best reseller selling products by Name`  
  
 `with member [Measures].[PCT Discount] AS '[Measures].[Discount Amount]/[Measures].[Reseller Sales Amount]', FORMAT_STRING = 'Percent'`  
  
 `set Top10SellingProducts as 'topcount([Product].[Model Name].children, 10, [Measures].[Reseller Sales Amount])'`  
  
 `set Preferred10Products as '`  
  
 `{[Product].[Model Name].&[Mountain-200],`  
  
 `[Product].[Model Name].&[Road-250],`  
  
 `[Product].[Model Name].&[Mountain-100],`  
  
 `[Product].[Model Name].&[Road-650],`  
  
 `[Product].[Model Name].&[Touring-1000],`  
  
 `[Product].[Model Name].&[Road-550-W],`  
  
 `[Product].[Model Name].&[Road-350-W],`  
  
 `[Product].[Model Name].&[HL Mountain Frame],`  
  
 `[Product].[Model Name].&[Road-150],`  
  
 `[Product].[Model Name].&[Touring-3000]`  
  
 `}'`  
  
 `select {[Measures].[Reseller Sales Amount], [Measures].[Discount Amount], [Measures].[PCT Discount]} on 0,`  
  
 `Top10SellingProducts on 1`  
  
 `from [Adventure Works]`  
  
 <span data-ttu-id="626bb-141">다음과 같은 결과 집합을 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="626bb-141">The obtained result set is:</span></span>  
  
|||||  
|-|-|-|-|  
||<span data-ttu-id="626bb-142">**Reseller Sales Amount**</span><span class="sxs-lookup"><span data-stu-id="626bb-142">**Reseller Sales Amount**</span></span>|<span data-ttu-id="626bb-143">**Discount Amount**</span><span class="sxs-lookup"><span data-stu-id="626bb-143">**Discount Amount**</span></span>|<span data-ttu-id="626bb-144">**PCT Discount**</span><span class="sxs-lookup"><span data-stu-id="626bb-144">**PCT Discount**</span></span>|  
|<span data-ttu-id="626bb-145">**Mountain-200**</span><span class="sxs-lookup"><span data-stu-id="626bb-145">**Mountain-200**</span></span>|<span data-ttu-id="626bb-146">**$14,356,699.36**</span><span class="sxs-lookup"><span data-stu-id="626bb-146">**$14,356,699.36**</span></span>|<span data-ttu-id="626bb-147">**$19,012.71**</span><span class="sxs-lookup"><span data-stu-id="626bb-147">**$19,012.71**</span></span>|<span data-ttu-id="626bb-148">**0.13%**</span><span class="sxs-lookup"><span data-stu-id="626bb-148">**0.13%**</span></span>|  
|<span data-ttu-id="626bb-149">**Road-250**</span><span class="sxs-lookup"><span data-stu-id="626bb-149">**Road-250**</span></span>|<span data-ttu-id="626bb-150">**$9,377,457.68**</span><span class="sxs-lookup"><span data-stu-id="626bb-150">**$9,377,457.68**</span></span>|<span data-ttu-id="626bb-151">**$4,032.47**</span><span class="sxs-lookup"><span data-stu-id="626bb-151">**$4,032.47**</span></span>|<span data-ttu-id="626bb-152">**0.04%**</span><span class="sxs-lookup"><span data-stu-id="626bb-152">**0.04%**</span></span>|  
|<span data-ttu-id="626bb-153">**Mountain-100**</span><span class="sxs-lookup"><span data-stu-id="626bb-153">**Mountain-100**</span></span>|<span data-ttu-id="626bb-154">**$8,568,958.27**</span><span class="sxs-lookup"><span data-stu-id="626bb-154">**$8,568,958.27**</span></span>|<span data-ttu-id="626bb-155">**$139,393.27**</span><span class="sxs-lookup"><span data-stu-id="626bb-155">**$139,393.27**</span></span>|<span data-ttu-id="626bb-156">**1.63%**</span><span class="sxs-lookup"><span data-stu-id="626bb-156">**1.63%**</span></span>|  
|<span data-ttu-id="626bb-157">**Road-650**</span><span class="sxs-lookup"><span data-stu-id="626bb-157">**Road-650**</span></span>|<span data-ttu-id="626bb-158">**$7,442,141.81**</span><span class="sxs-lookup"><span data-stu-id="626bb-158">**$7,442,141.81**</span></span>|<span data-ttu-id="626bb-159">**$39,698.30**</span><span class="sxs-lookup"><span data-stu-id="626bb-159">**$39,698.30**</span></span>|<span data-ttu-id="626bb-160">**0.53%**</span><span class="sxs-lookup"><span data-stu-id="626bb-160">**0.53%**</span></span>|  
|<span data-ttu-id="626bb-161">**Touring-1000**</span><span class="sxs-lookup"><span data-stu-id="626bb-161">**Touring-1000**</span></span>|<span data-ttu-id="626bb-162">**$6,723,794.29**</span><span class="sxs-lookup"><span data-stu-id="626bb-162">**$6,723,794.29**</span></span>|<span data-ttu-id="626bb-163">**$166,144.17**</span><span class="sxs-lookup"><span data-stu-id="626bb-163">**$166,144.17**</span></span>|<span data-ttu-id="626bb-164">**2.47%**</span><span class="sxs-lookup"><span data-stu-id="626bb-164">**2.47%**</span></span>|  
|<span data-ttu-id="626bb-165">**Road-550-W**</span><span class="sxs-lookup"><span data-stu-id="626bb-165">**Road-550-W**</span></span>|<span data-ttu-id="626bb-166">**$3,668,383.88**</span><span class="sxs-lookup"><span data-stu-id="626bb-166">**$3,668,383.88**</span></span>|<span data-ttu-id="626bb-167">**$1,901.97**</span><span class="sxs-lookup"><span data-stu-id="626bb-167">**$1,901.97**</span></span>|<span data-ttu-id="626bb-168">**0.05%**</span><span class="sxs-lookup"><span data-stu-id="626bb-168">**0.05%**</span></span>|  
|<span data-ttu-id="626bb-169">**Road-350-W**</span><span class="sxs-lookup"><span data-stu-id="626bb-169">**Road-350-W**</span></span>|<span data-ttu-id="626bb-170">**$3,665,932.31**</span><span class="sxs-lookup"><span data-stu-id="626bb-170">**$3,665,932.31**</span></span>|<span data-ttu-id="626bb-171">**$20,946.50**</span><span class="sxs-lookup"><span data-stu-id="626bb-171">**$20,946.50**</span></span>|<span data-ttu-id="626bb-172">**0.57%**</span><span class="sxs-lookup"><span data-stu-id="626bb-172">**0.57%**</span></span>|  
|<span data-ttu-id="626bb-173">**HL Mountain Frame**</span><span class="sxs-lookup"><span data-stu-id="626bb-173">**HL Mountain Frame**</span></span>|<span data-ttu-id="626bb-174">**$3,365,069.27**</span><span class="sxs-lookup"><span data-stu-id="626bb-174">**$3,365,069.27**</span></span>|<span data-ttu-id="626bb-175">**$174.11**</span><span class="sxs-lookup"><span data-stu-id="626bb-175">**$174.11**</span></span>|<span data-ttu-id="626bb-176">**0.01%**</span><span class="sxs-lookup"><span data-stu-id="626bb-176">**0.01%**</span></span>|  
|<span data-ttu-id="626bb-177">**Road-150**</span><span class="sxs-lookup"><span data-stu-id="626bb-177">**Road-150**</span></span>|<span data-ttu-id="626bb-178">**$2,363,805.16**</span><span class="sxs-lookup"><span data-stu-id="626bb-178">**$2,363,805.16**</span></span>|<span data-ttu-id="626bb-179">**$0.00**</span><span class="sxs-lookup"><span data-stu-id="626bb-179">**$0.00**</span></span>|<span data-ttu-id="626bb-180">**0.00%**</span><span class="sxs-lookup"><span data-stu-id="626bb-180">**0.00%**</span></span>|  
|<span data-ttu-id="626bb-181">**Touring-3000**</span><span class="sxs-lookup"><span data-stu-id="626bb-181">**Touring-3000**</span></span>|<span data-ttu-id="626bb-182">**$2,046,508.26**</span><span class="sxs-lookup"><span data-stu-id="626bb-182">**$2,046,508.26**</span></span>|<span data-ttu-id="626bb-183">**$79,582.15**</span><span class="sxs-lookup"><span data-stu-id="626bb-183">**$79,582.15**</span></span>|<span data-ttu-id="626bb-184">**3.89%**</span><span class="sxs-lookup"><span data-stu-id="626bb-184">**3.89%**</span></span>|  
  
 <span data-ttu-id="626bb-185">이 결과 제품 집합은 Preferred10Products와 동일합니다. Preferred10Products 집합은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="626bb-185">The obtained set of products seems to be the same as Preferred10Products; so, verifying the Preferred10Products set:</span></span>  
  
 `with member [Measures].[PCT Discount] AS '[Measures].[Discount Amount]/[Measures].[Reseller Sales Amount]', FORMAT_STRING = 'Percent'`  
  
 `set Top10SellingProducts as 'topcount([Product].[Model Name].children, 10, [Measures].[Reseller Sales Amount])'`  
  
 `set Preferred10Products as '`  
  
 `{[Product].[Model Name].&[Mountain-200],`  
  
 `[Product].[Model Name].&[Road-250],`  
  
 `[Product].[Model Name].&[Mountain-100],`  
  
 `[Product].[Model Name].&[Road-650],`  
  
 `[Product].[Model Name].&[Touring-1000],`  
  
 `[Product].[Model Name].&[Road-550-W],`  
  
 `[Product].[Model Name].&[Road-350-W],`  
  
 `[Product].[Model Name].&[HL Mountain Frame],`  
  
 `[Product].[Model Name].&[Road-150],`  
  
 `[Product].[Model Name].&[Touring-3000]`  
  
 `}'`  
  
 `select {[Measures].[Reseller Sales Amount], [Measures].[Discount Amount], [Measures].[PCT Discount]} on 0,`  
  
 `Preferred10Products on 1`  
  
 `from [Adventure Works]`  
  
 <span data-ttu-id="626bb-186">다음 결과에 따라 두 집합(Top10SellingProducts, Preferred10Products)은 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="626bb-186">As per the following results, both sets (Top10SellingProducts, Preferred10Products) are the same</span></span>  
  
|||||  
|-|-|-|-|  
||<span data-ttu-id="626bb-187">**Reseller Sales Amount**</span><span class="sxs-lookup"><span data-stu-id="626bb-187">**Reseller Sales Amount**</span></span>|<span data-ttu-id="626bb-188">**Discount Amount**</span><span class="sxs-lookup"><span data-stu-id="626bb-188">**Discount Amount**</span></span>|<span data-ttu-id="626bb-189">**PCT Discount**</span><span class="sxs-lookup"><span data-stu-id="626bb-189">**PCT Discount**</span></span>|  
|<span data-ttu-id="626bb-190">**Mountain-200**</span><span class="sxs-lookup"><span data-stu-id="626bb-190">**Mountain-200**</span></span>|<span data-ttu-id="626bb-191">**$14,356,699.36**</span><span class="sxs-lookup"><span data-stu-id="626bb-191">**$14,356,699.36**</span></span>|<span data-ttu-id="626bb-192">**$19,012.71**</span><span class="sxs-lookup"><span data-stu-id="626bb-192">**$19,012.71**</span></span>|<span data-ttu-id="626bb-193">**0.13%**</span><span class="sxs-lookup"><span data-stu-id="626bb-193">**0.13%**</span></span>|  
|<span data-ttu-id="626bb-194">**Road-250**</span><span class="sxs-lookup"><span data-stu-id="626bb-194">**Road-250**</span></span>|<span data-ttu-id="626bb-195">**$9,377,457.68**</span><span class="sxs-lookup"><span data-stu-id="626bb-195">**$9,377,457.68**</span></span>|<span data-ttu-id="626bb-196">**$4,032.47**</span><span class="sxs-lookup"><span data-stu-id="626bb-196">**$4,032.47**</span></span>|<span data-ttu-id="626bb-197">**0.04%**</span><span class="sxs-lookup"><span data-stu-id="626bb-197">**0.04%**</span></span>|  
|<span data-ttu-id="626bb-198">**Mountain-100**</span><span class="sxs-lookup"><span data-stu-id="626bb-198">**Mountain-100**</span></span>|<span data-ttu-id="626bb-199">**$8,568,958.27**</span><span class="sxs-lookup"><span data-stu-id="626bb-199">**$8,568,958.27**</span></span>|<span data-ttu-id="626bb-200">**$139,393.27**</span><span class="sxs-lookup"><span data-stu-id="626bb-200">**$139,393.27**</span></span>|<span data-ttu-id="626bb-201">**1.63%**</span><span class="sxs-lookup"><span data-stu-id="626bb-201">**1.63%**</span></span>|  
|<span data-ttu-id="626bb-202">**Road-650**</span><span class="sxs-lookup"><span data-stu-id="626bb-202">**Road-650**</span></span>|<span data-ttu-id="626bb-203">**$7,442,141.81**</span><span class="sxs-lookup"><span data-stu-id="626bb-203">**$7,442,141.81**</span></span>|<span data-ttu-id="626bb-204">**$39,698.30**</span><span class="sxs-lookup"><span data-stu-id="626bb-204">**$39,698.30**</span></span>|<span data-ttu-id="626bb-205">**0.53%**</span><span class="sxs-lookup"><span data-stu-id="626bb-205">**0.53%**</span></span>|  
|<span data-ttu-id="626bb-206">**Touring-1000**</span><span class="sxs-lookup"><span data-stu-id="626bb-206">**Touring-1000**</span></span>|<span data-ttu-id="626bb-207">**$6,723,794.29**</span><span class="sxs-lookup"><span data-stu-id="626bb-207">**$6,723,794.29**</span></span>|<span data-ttu-id="626bb-208">**$166,144.17**</span><span class="sxs-lookup"><span data-stu-id="626bb-208">**$166,144.17**</span></span>|<span data-ttu-id="626bb-209">**2.47%**</span><span class="sxs-lookup"><span data-stu-id="626bb-209">**2.47%**</span></span>|  
|<span data-ttu-id="626bb-210">**Road-550-W**</span><span class="sxs-lookup"><span data-stu-id="626bb-210">**Road-550-W**</span></span>|<span data-ttu-id="626bb-211">**$3,668,383.88**</span><span class="sxs-lookup"><span data-stu-id="626bb-211">**$3,668,383.88**</span></span>|<span data-ttu-id="626bb-212">**$1,901.97**</span><span class="sxs-lookup"><span data-stu-id="626bb-212">**$1,901.97**</span></span>|<span data-ttu-id="626bb-213">**0.05%**</span><span class="sxs-lookup"><span data-stu-id="626bb-213">**0.05%**</span></span>|  
|<span data-ttu-id="626bb-214">**Road-350-W**</span><span class="sxs-lookup"><span data-stu-id="626bb-214">**Road-350-W**</span></span>|<span data-ttu-id="626bb-215">**$3,665,932.31**</span><span class="sxs-lookup"><span data-stu-id="626bb-215">**$3,665,932.31**</span></span>|<span data-ttu-id="626bb-216">**$20,946.50**</span><span class="sxs-lookup"><span data-stu-id="626bb-216">**$20,946.50**</span></span>|<span data-ttu-id="626bb-217">**0.57%**</span><span class="sxs-lookup"><span data-stu-id="626bb-217">**0.57%**</span></span>|  
|<span data-ttu-id="626bb-218">**HL Mountain Frame**</span><span class="sxs-lookup"><span data-stu-id="626bb-218">**HL Mountain Frame**</span></span>|<span data-ttu-id="626bb-219">**$3,365,069.27**</span><span class="sxs-lookup"><span data-stu-id="626bb-219">**$3,365,069.27**</span></span>|<span data-ttu-id="626bb-220">**$174.11**</span><span class="sxs-lookup"><span data-stu-id="626bb-220">**$174.11**</span></span>|<span data-ttu-id="626bb-221">**0.01%**</span><span class="sxs-lookup"><span data-stu-id="626bb-221">**0.01%**</span></span>|  
|<span data-ttu-id="626bb-222">**Road-150**</span><span class="sxs-lookup"><span data-stu-id="626bb-222">**Road-150**</span></span>|<span data-ttu-id="626bb-223">**$2,363,805.16**</span><span class="sxs-lookup"><span data-stu-id="626bb-223">**$2,363,805.16**</span></span>|<span data-ttu-id="626bb-224">**$0.00**</span><span class="sxs-lookup"><span data-stu-id="626bb-224">**$0.00**</span></span>|<span data-ttu-id="626bb-225">**0.00%**</span><span class="sxs-lookup"><span data-stu-id="626bb-225">**0.00%**</span></span>|  
|<span data-ttu-id="626bb-226">**Touring-3000**</span><span class="sxs-lookup"><span data-stu-id="626bb-226">**Touring-3000**</span></span>|<span data-ttu-id="626bb-227">**$2,046,508.26**</span><span class="sxs-lookup"><span data-stu-id="626bb-227">**$2,046,508.26**</span></span>|<span data-ttu-id="626bb-228">**$79,582.15**</span><span class="sxs-lookup"><span data-stu-id="626bb-228">**$79,582.15**</span></span>|<span data-ttu-id="626bb-229">**3.89%**</span><span class="sxs-lookup"><span data-stu-id="626bb-229">**3.89%**</span></span>|  
  
 <span data-ttu-id="626bb-230">다음 예에서는 전체 Autoexists의 개념을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="626bb-230">The following example will illustrate the concept of deep Autoexists.</span></span> <span data-ttu-id="626bb-231">예에서 [Mountain] 그룹의 Top10SellingProducts를 [Product].[Product Line] 특성별로 필터링합니다.</span><span class="sxs-lookup"><span data-stu-id="626bb-231">In the example we are filtering Top10SellingProducts by [Product].[Product Line] attribute for those in [Mountain] group.</span></span> <span data-ttu-id="626bb-232">두 특성(slicer 및 축)이 동일한 차원인 [Product]에 속합니다.</span><span class="sxs-lookup"><span data-stu-id="626bb-232">Note that both attributes (slicer and axis) belong to the same dimension, [Product].</span></span>  
  
 `with member [Measures].[PCT Discount] AS '[Measures].[Discount Amount]/[Measures].[Reseller Sales Amount]', FORMAT_STRING = 'Percent'`  
  
 `set Top10SellingProducts as 'topcount([Product].[Model Name].children, 10, [Measures].[Reseller Sales Amount])'`  
  
 `// Preferred10Products set removed for clarity`  
  
 `select {[Measures].[Reseller Sales Amount], [Measures].[Discount Amount], [Measures].[PCT Discount]} on 0,`  
  
 `Top10SellingProducts on 1`  
  
 `from [Adventure Works]`  
  
 `where [Product].[Product Line].[Mountain]`  
  
 <span data-ttu-id="626bb-233">결과 집합은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="626bb-233">Produces the following result set:</span></span>  
  
|||||  
|-|-|-|-|  
||<span data-ttu-id="626bb-234">**Reseller Sales Amount**</span><span class="sxs-lookup"><span data-stu-id="626bb-234">**Reseller Sales Amount**</span></span>|<span data-ttu-id="626bb-235">**Discount Amount**</span><span class="sxs-lookup"><span data-stu-id="626bb-235">**Discount Amount**</span></span>|<span data-ttu-id="626bb-236">**PCT Discount**</span><span class="sxs-lookup"><span data-stu-id="626bb-236">**PCT Discount**</span></span>|  
|<span data-ttu-id="626bb-237">**Mountain-200**</span><span class="sxs-lookup"><span data-stu-id="626bb-237">**Mountain-200**</span></span>|<span data-ttu-id="626bb-238">**$14,356,699.36**</span><span class="sxs-lookup"><span data-stu-id="626bb-238">**$14,356,699.36**</span></span>|<span data-ttu-id="626bb-239">**$19,012.71**</span><span class="sxs-lookup"><span data-stu-id="626bb-239">**$19,012.71**</span></span>|<span data-ttu-id="626bb-240">**0.13%**</span><span class="sxs-lookup"><span data-stu-id="626bb-240">**0.13%**</span></span>|  
|<span data-ttu-id="626bb-241">**Mountain-100**</span><span class="sxs-lookup"><span data-stu-id="626bb-241">**Mountain-100**</span></span>|<span data-ttu-id="626bb-242">**$8,568,958.27**</span><span class="sxs-lookup"><span data-stu-id="626bb-242">**$8,568,958.27**</span></span>|<span data-ttu-id="626bb-243">**$139,393.27**</span><span class="sxs-lookup"><span data-stu-id="626bb-243">**$139,393.27**</span></span>|<span data-ttu-id="626bb-244">**1.63%**</span><span class="sxs-lookup"><span data-stu-id="626bb-244">**1.63%**</span></span>|  
|<span data-ttu-id="626bb-245">**HL Mountain Frame**</span><span class="sxs-lookup"><span data-stu-id="626bb-245">**HL Mountain Frame**</span></span>|<span data-ttu-id="626bb-246">**$3,365,069.27**</span><span class="sxs-lookup"><span data-stu-id="626bb-246">**$3,365,069.27**</span></span>|<span data-ttu-id="626bb-247">**$174.11**</span><span class="sxs-lookup"><span data-stu-id="626bb-247">**$174.11**</span></span>|<span data-ttu-id="626bb-248">**0.01%**</span><span class="sxs-lookup"><span data-stu-id="626bb-248">**0.01%**</span></span>|  
|<span data-ttu-id="626bb-249">**Mountain-300**</span><span class="sxs-lookup"><span data-stu-id="626bb-249">**Mountain-300**</span></span>|<span data-ttu-id="626bb-250">**$1,907,249.38**</span><span class="sxs-lookup"><span data-stu-id="626bb-250">**$1,907,249.38**</span></span>|<span data-ttu-id="626bb-251">**$876.95**</span><span class="sxs-lookup"><span data-stu-id="626bb-251">**$876.95**</span></span>|<span data-ttu-id="626bb-252">**0.05%**</span><span class="sxs-lookup"><span data-stu-id="626bb-252">**0.05%**</span></span>|  
|<span data-ttu-id="626bb-253">**Mountain-500**</span><span class="sxs-lookup"><span data-stu-id="626bb-253">**Mountain-500**</span></span>|<span data-ttu-id="626bb-254">**$1,067,327.31**</span><span class="sxs-lookup"><span data-stu-id="626bb-254">**$1,067,327.31**</span></span>|<span data-ttu-id="626bb-255">**$17,266.09**</span><span class="sxs-lookup"><span data-stu-id="626bb-255">**$17,266.09**</span></span>|<span data-ttu-id="626bb-256">**1.62%**</span><span class="sxs-lookup"><span data-stu-id="626bb-256">**1.62%**</span></span>|  
|<span data-ttu-id="626bb-257">**Mountain-400-W**</span><span class="sxs-lookup"><span data-stu-id="626bb-257">**Mountain-400-W**</span></span>|<span data-ttu-id="626bb-258">**$592,450.05**</span><span class="sxs-lookup"><span data-stu-id="626bb-258">**$592,450.05**</span></span>|<span data-ttu-id="626bb-259">**$303.49**</span><span class="sxs-lookup"><span data-stu-id="626bb-259">**$303.49**</span></span>|<span data-ttu-id="626bb-260">**0.05%**</span><span class="sxs-lookup"><span data-stu-id="626bb-260">**0.05%**</span></span>|  
|<span data-ttu-id="626bb-261">**LL Mountain Frame**</span><span class="sxs-lookup"><span data-stu-id="626bb-261">**LL Mountain Frame**</span></span>|<span data-ttu-id="626bb-262">**$521,864.42**</span><span class="sxs-lookup"><span data-stu-id="626bb-262">**$521,864.42**</span></span>|<span data-ttu-id="626bb-263">**$252.41**</span><span class="sxs-lookup"><span data-stu-id="626bb-263">**$252.41**</span></span>|<span data-ttu-id="626bb-264">**0.05%**</span><span class="sxs-lookup"><span data-stu-id="626bb-264">**0.05%**</span></span>|  
|<span data-ttu-id="626bb-265">**ML Mountain Frame-W**</span><span class="sxs-lookup"><span data-stu-id="626bb-265">**ML Mountain Frame-W**</span></span>|<span data-ttu-id="626bb-266">**$482,953.16**</span><span class="sxs-lookup"><span data-stu-id="626bb-266">**$482,953.16**</span></span>|<span data-ttu-id="626bb-267">**$206.95**</span><span class="sxs-lookup"><span data-stu-id="626bb-267">**$206.95**</span></span>|<span data-ttu-id="626bb-268">**0.04%**</span><span class="sxs-lookup"><span data-stu-id="626bb-268">**0.04%**</span></span>|  
|<span data-ttu-id="626bb-269">**ML Mountain Frame**</span><span class="sxs-lookup"><span data-stu-id="626bb-269">**ML Mountain Frame**</span></span>|<span data-ttu-id="626bb-270">**$343,785.29**</span><span class="sxs-lookup"><span data-stu-id="626bb-270">**$343,785.29**</span></span>|<span data-ttu-id="626bb-271">**$161.82**</span><span class="sxs-lookup"><span data-stu-id="626bb-271">**$161.82**</span></span>|<span data-ttu-id="626bb-272">**0.05%**</span><span class="sxs-lookup"><span data-stu-id="626bb-272">**0.05%**</span></span>|  
|<span data-ttu-id="626bb-273">**Women's Mountain Shorts**</span><span class="sxs-lookup"><span data-stu-id="626bb-273">**Women's Mountain Shorts**</span></span>|<span data-ttu-id="626bb-274">**$260,304.09**</span><span class="sxs-lookup"><span data-stu-id="626bb-274">**$260,304.09**</span></span>|<span data-ttu-id="626bb-275">**$6,675.56**</span><span class="sxs-lookup"><span data-stu-id="626bb-275">**$6,675.56**</span></span>|<span data-ttu-id="626bb-276">**2.56%**</span><span class="sxs-lookup"><span data-stu-id="626bb-276">**2.56%**</span></span>|  
  
 <span data-ttu-id="626bb-277">위 결과 집합에는 Top10SellingProducts 목록에 7개의 새 항목이 있으며 Mountain-200, Mountain-100 및 HL Mountain Frame이 목록 맨 위로 이동했습니다.</span><span class="sxs-lookup"><span data-stu-id="626bb-277">In the above result set we have seven newcomers to the list of Top10SellingProducts and Mountain-200, Mountain-100, and HL Mountain Frame have moved to the top of the list.</span></span> <span data-ttu-id="626bb-278">이전 결과 집합에서는 이러한 3개의 값이 섞였습니다.</span><span class="sxs-lookup"><span data-stu-id="626bb-278">In the previous result set those three values were interspersed.</span></span>  
  
 <span data-ttu-id="626bb-279">Top10SellingProducts 집합이 쿼리의 조각화 조건을 충족하도록 계산되기 때문에 이를 전체 Autoexists라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="626bb-279">This is called Deep Autoexists, because the Top10SellingProducts set is evaluated to meet the slicing conditions of the query.</span></span> <span data-ttu-id="626bb-280">전체 Autoexists는 slicer 식, 축의 하위 선택 식 등을 적용한 후 가능한 가장 범위가 큰 공간에 맞게 모든 식이 계산됨을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="626bb-280">Deep Autoexists means that all expressions will be evaluated to meet the deepest possible space after applying the slicer expressions, the sub select expressions in the axis, and so on.</span></span>  
  
 <span data-ttu-id="626bb-281">그러나 다음 예와 같이 Top10SellingProducts를 Preferred10Products와 동등하게 분석하기를 원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="626bb-281">However, one might want to be able to do the analysis over the Top10SellingProducts as equivalent to Preferred10Products, as in the following example:</span></span>  
  
 `with member [Measures].[PCT Discount] AS '[Measures].[Discount Amount]/[Measures].[Reseller Sales Amount]', FORMAT_STRING = 'Percent'`  
  
 `set Top10SellingProducts as 'topcount([Product].[Model Name].children, 10, [Measures].[Reseller Sales Amount])'`  
  
 `set Preferred10Products as '`  
  
 `{[Product].[Model Name].&[Mountain-200],`  
  
 `[Product].[Model Name].&[Road-250],`  
  
 `[Product].[Model Name].&[Mountain-100],`  
  
 `[Product].[Model Name].&[Road-650],`  
  
 `[Product].[Model Name].&[Touring-1000],`  
  
 `[Product].[Model Name].&[Road-550-W],`  
  
 `[Product].[Model Name].&[Road-350-W],`  
  
 `[Product].[Model Name].&[HL Mountain Frame],`  
  
 `[Product].[Model Name].&[Road-150],`  
  
 `[Product].[Model Name].&[Touring-3000]`  
  
 `}'`  
  
 `select {[Measures].[Reseller Sales Amount], [Measures].[Discount Amount], [Measures].[PCT Discount]} on 0,`  
  
 `Preferred10Products on 1`  
  
 `from [Adventure Works]`  
  
 `where [Product].[Product Line].[Mountain]`  
  
 <span data-ttu-id="626bb-282">결과 집합은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="626bb-282">Produces the following result set:</span></span>  
  
|||||  
|-|-|-|-|  
||<span data-ttu-id="626bb-283">**Reseller Sales Amount**</span><span class="sxs-lookup"><span data-stu-id="626bb-283">**Reseller Sales Amount**</span></span>|<span data-ttu-id="626bb-284">**Discount Amount**</span><span class="sxs-lookup"><span data-stu-id="626bb-284">**Discount Amount**</span></span>|<span data-ttu-id="626bb-285">**PCT Discount**</span><span class="sxs-lookup"><span data-stu-id="626bb-285">**PCT Discount**</span></span>|  
|<span data-ttu-id="626bb-286">**Mountain-200**</span><span class="sxs-lookup"><span data-stu-id="626bb-286">**Mountain-200**</span></span>|<span data-ttu-id="626bb-287">**$14,356,699.36**</span><span class="sxs-lookup"><span data-stu-id="626bb-287">**$14,356,699.36**</span></span>|<span data-ttu-id="626bb-288">**$19,012.71**</span><span class="sxs-lookup"><span data-stu-id="626bb-288">**$19,012.71**</span></span>|<span data-ttu-id="626bb-289">**0.13%**</span><span class="sxs-lookup"><span data-stu-id="626bb-289">**0.13%**</span></span>|  
|<span data-ttu-id="626bb-290">**Mountain-100**</span><span class="sxs-lookup"><span data-stu-id="626bb-290">**Mountain-100**</span></span>|<span data-ttu-id="626bb-291">**$8,568,958.27**</span><span class="sxs-lookup"><span data-stu-id="626bb-291">**$8,568,958.27**</span></span>|<span data-ttu-id="626bb-292">**$139,393.27**</span><span class="sxs-lookup"><span data-stu-id="626bb-292">**$139,393.27**</span></span>|<span data-ttu-id="626bb-293">**1.63%**</span><span class="sxs-lookup"><span data-stu-id="626bb-293">**1.63%**</span></span>|  
|<span data-ttu-id="626bb-294">**HL Mountain Frame**</span><span class="sxs-lookup"><span data-stu-id="626bb-294">**HL Mountain Frame**</span></span>|<span data-ttu-id="626bb-295">**$3,365,069.27**</span><span class="sxs-lookup"><span data-stu-id="626bb-295">**$3,365,069.27**</span></span>|<span data-ttu-id="626bb-296">**$174.11**</span><span class="sxs-lookup"><span data-stu-id="626bb-296">**$174.11**</span></span>|<span data-ttu-id="626bb-297">**0.01%**</span><span class="sxs-lookup"><span data-stu-id="626bb-297">**0.01%**</span></span>|  
  
 <span data-ttu-id="626bb-298">위의 결과에서 조각화를 수행하면 Preferred10Products가 상수 식이기 때문에 예상대로 [Product].[Product Line]에 있는 [Mountain] 그룹의 일부인 Preferred10Products의 제품만 포함하는 결과가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="626bb-298">In the above results, the slicing gives a result that contains only those products from Preferred10Products that are part of the [Mountain] group in [Product].[Product Line]; as expected, because Preferred10Products is a constant expression.</span></span>  
  
 <span data-ttu-id="626bb-299">이러한 결과 집합을 단순 AUTOEXIST라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="626bb-299">This result set is also understood as Shallow Autoexists.</span></span> <span data-ttu-id="626bb-300">이는 식이 조각화 절 이전에 계산되기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="626bb-300">This is because the expression is evaluated before the slicing clause.</span></span> <span data-ttu-id="626bb-301">이전 예에서는 식이 개념 소개를 위한 설명을 제공하기 위해 상수 식이었습니다.</span><span class="sxs-lookup"><span data-stu-id="626bb-301">In the previous example, the expression was a constant expression for illustration purposes in order to introduce the concept.</span></span>  
  
 <span data-ttu-id="626bb-302">Autoexists 동작은 `Autoexists` 연결 문자열 속성을 사용하여 세션 수준에서 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="626bb-302">Autoexists behavior can be modified at the session level using the `Autoexists` connection string property.</span></span> <span data-ttu-id="626bb-303">다음 예에서는 새 세션을 열고 *Autoexists=3* 속성을 연결 문자열에 추가하여 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="626bb-303">The following example begins by opening a new session and adding the *Autoexists=3* property to the connection string.</span></span> <span data-ttu-id="626bb-304">예를 실행하기 위해 새 연결을 열어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="626bb-304">You must open a new connection in order to do the example.</span></span> <span data-ttu-id="626bb-305">Autoexist 설정을 사용하여 연결을 설정하면 연결이 완료될 때까지 계속 연결이 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="626bb-305">Once the connection is established with the Autoexist setting it will remain in effect until that connection is finished.</span></span>  
  
 `with member [Measures].[PCT Discount] AS '[Measures].[Discount Amount]/[Measures].[Reseller Sales Amount]', FORMAT_STRING = 'Percent'`  
  
 `set Top10SellingProducts as 'topcount([Product].[Model Name].children, 10, [Measures].[Reseller Sales Amount])'`  
  
 `//Preferred10Products set removed for clarity`  
  
 `select {[Measures].[Reseller Sales Amount], [Measures].[Discount Amount], [Measures].[PCT Discount]} on 0,`  
  
 `Top10SellingProducts on 1`  
  
 `from [Adventure Works]`  
  
 `where [Product].[Product Line].[Mountain]`  
  
 <span data-ttu-id="626bb-306">다음 결과 집합은 이제 AUTOEXIST의 부분 동작을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="626bb-306">The following result set now shows the shallow behavior of Autoexists.</span></span>  
  
|||||  
|-|-|-|-|  
||<span data-ttu-id="626bb-307">**Reseller Sales Amount**</span><span class="sxs-lookup"><span data-stu-id="626bb-307">**Reseller Sales Amount**</span></span>|<span data-ttu-id="626bb-308">**Discount Amount**</span><span class="sxs-lookup"><span data-stu-id="626bb-308">**Discount Amount**</span></span>|<span data-ttu-id="626bb-309">**PCT Discount**</span><span class="sxs-lookup"><span data-stu-id="626bb-309">**PCT Discount**</span></span>|  
|<span data-ttu-id="626bb-310">**Mountain-200**</span><span class="sxs-lookup"><span data-stu-id="626bb-310">**Mountain-200**</span></span>|<span data-ttu-id="626bb-311">**$14,356,699.36**</span><span class="sxs-lookup"><span data-stu-id="626bb-311">**$14,356,699.36**</span></span>|<span data-ttu-id="626bb-312">**$19,012.71**</span><span class="sxs-lookup"><span data-stu-id="626bb-312">**$19,012.71**</span></span>|<span data-ttu-id="626bb-313">**0.13%**</span><span class="sxs-lookup"><span data-stu-id="626bb-313">**0.13%**</span></span>|  
|<span data-ttu-id="626bb-314">**Mountain-100**</span><span class="sxs-lookup"><span data-stu-id="626bb-314">**Mountain-100**</span></span>|<span data-ttu-id="626bb-315">**$8,568,958.27**</span><span class="sxs-lookup"><span data-stu-id="626bb-315">**$8,568,958.27**</span></span>|<span data-ttu-id="626bb-316">**$139,393.27**</span><span class="sxs-lookup"><span data-stu-id="626bb-316">**$139,393.27**</span></span>|<span data-ttu-id="626bb-317">**1.63%**</span><span class="sxs-lookup"><span data-stu-id="626bb-317">**1.63%**</span></span>|  
|<span data-ttu-id="626bb-318">**HL Mountain Frame**</span><span class="sxs-lookup"><span data-stu-id="626bb-318">**HL Mountain Frame**</span></span>|<span data-ttu-id="626bb-319">**$3,365,069.27**</span><span class="sxs-lookup"><span data-stu-id="626bb-319">**$3,365,069.27**</span></span>|<span data-ttu-id="626bb-320">**$174.11**</span><span class="sxs-lookup"><span data-stu-id="626bb-320">**$174.11**</span></span>|<span data-ttu-id="626bb-321">**0.01%**</span><span class="sxs-lookup"><span data-stu-id="626bb-321">**0.01%**</span></span>|  
  
 <span data-ttu-id="626bb-322">Autoexists 동작은 연결 문자열의 AUTOEXISTS = [1 | 2 | 3] 매개 변수를 사용 하 여 수정할 수 있습니다. [&#40;xmla&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties) 및 <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.ConnectionString%2A> 매개 변수 사용에 대해 지원 되는 xmla 속성을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="626bb-322">Autoexists behavior can be modified by using the AUTOEXISTS=[1|2|3] parameter in the connection string; see [Supported XMLA Properties &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties) and <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.ConnectionString%2A> for parameter usage.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="626bb-323">참고 항목</span><span class="sxs-lookup"><span data-stu-id="626bb-323">See Also</span></span>  
 <span data-ttu-id="626bb-324">[MDX의 주요 개념 &#40;Analysis Services&#41;](../key-concepts-in-mdx-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="626bb-324">[Key Concepts in MDX &#40;Analysis Services&#41;](../key-concepts-in-mdx-analysis-services.md) </span></span>  
 <span data-ttu-id="626bb-325">[큐브 공간](cube-space.md) </span><span class="sxs-lookup"><span data-stu-id="626bb-325">[Cube Space](cube-space.md) </span></span>  
 <span data-ttu-id="626bb-326">[옥](tuples.md) </span><span class="sxs-lookup"><span data-stu-id="626bb-326">[Tuples](tuples.md) </span></span>  
 <span data-ttu-id="626bb-327">[MDX &#40;멤버, 튜플 및 집합을 사용 하 여 작업&#41;](working-with-members-tuples-and-sets-mdx.md) </span><span class="sxs-lookup"><span data-stu-id="626bb-327">[Working with Members, Tuples, and Sets &#40;MDX&#41;](working-with-members-tuples-and-sets-mdx.md) </span></span>  
 <span data-ttu-id="626bb-328">[보이는 합계 및 비시각적 합계](visual-totals-and-non-visual-totals.md) </span><span class="sxs-lookup"><span data-stu-id="626bb-328">[Visual Totals and Non Visual Totals](visual-totals-and-non-visual-totals.md) </span></span>  
 <span data-ttu-id="626bb-329">[Mdx 언어 참조 &#40;MDX&#41;](/sql/mdx/mdx-language-reference-mdx) </span><span class="sxs-lookup"><span data-stu-id="626bb-329">[MDX Language Reference &#40;MDX&#41;](/sql/mdx/mdx-language-reference-mdx) </span></span>  
 [<span data-ttu-id="626bb-330">MDX&#40;Multidimensional Expression&#41; 참조</span><span class="sxs-lookup"><span data-stu-id="626bb-330">Multidimensional Expressions &#40;MDX&#41; Reference</span></span>](/sql/mdx/multidimensional-expressions-mdx-reference)  
  
  
