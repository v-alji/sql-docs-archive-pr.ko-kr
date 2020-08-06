---
title: 보이는 합계 및 비시각적 합계 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: ea9d02f2-a668-4547-ade5-e3d077a2e1bd
author: minewiskan
ms.author: owend
ms.openlocfilehash: ddff047be6a819d05276848cbeb430fb8e4c9c2f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736982"
---
# <a name="visual-totals-and-non-visual-totals"></a><span data-ttu-id="e8d65-102">보이는 값 합계 및 보이지 않는 값 합계</span><span class="sxs-lookup"><span data-stu-id="e8d65-102">Visual Totals and Non Visual Totals</span></span>
  <span data-ttu-id="e8d65-103">보이는 값 합계는 열이나 행에서 볼 수 있는 모든 항목이 더해지는 열이나 행의 끝에 있는 합계입니다.</span><span class="sxs-lookup"><span data-stu-id="e8d65-103">Visual Totals are totals at the end of a column or row that add up all of the items visible in the column or row.</span></span> <span data-ttu-id="e8d65-104">이 동작은 표시된 대부분의 테이블에서 기본 동작입니다.</span><span class="sxs-lookup"><span data-stu-id="e8d65-104">This is the default behavior for most tables when displayed.</span></span> <span data-ttu-id="e8d65-105">그러나 사용자가 테이블의 특정 열만 표시하고 표시되지 않은 열을 포함하여 전체 행에 대한 합계를 유지하려는 경우가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8d65-105">However, there are times when the user wants to display only certain columns in a table but keep the totals for the entire row, including those that are not displayed.</span></span> <span data-ttu-id="e8d65-106">이러한 경우를 `Non Visual Totals`라고 하는데 이는 보이는 값과 보이지 않는 값 모두에서 합계가 제공되기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="e8d65-106">These are called `Non Visual Totals`, because the total comes from both the visible and non-visible values.</span></span>  
  
 <span data-ttu-id="e8d65-107">다음 시나리오에서는 보이지 않는 값 합계의 동작을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="e8d65-107">The following scenario demonstrates the behavior of Non Visual totals.</span></span> <span data-ttu-id="e8d65-108">첫 번째 단계에서는 보이는 값 합계의 기본 동작을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="e8d65-108">The first step shows the default behavior of Visual Totals.</span></span>  
  
 <span data-ttu-id="e8d65-109">다음 예는 제품 범주가 열이고 대리점 업종이 행인 테이블에서 [Reseller Sales Amount] 수치를 가져오기 위한 [Adventure Works]의 쿼리입니다.</span><span class="sxs-lookup"><span data-stu-id="e8d65-109">The following example is a query of [Adventure Works] to obtain [Reseller Sales Amount] figures in a table where the product categories are the columns and the reseller business types are the rows.</span></span> <span data-ttu-id="e8d65-110">다음 SELECT 문이 실행될 경우 제품과 대리점 둘 다에 대한 합계가 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8d65-110">Note that totals are given for both products and resellers when the following SELECT statement is issued:</span></span>  
  
 `select [Category].members on 0,`  
  
 `[Business Type].members on 1`  
  
 `from [Adventure Works]`  
  
 `where [Measures].[Reseller Sales Amount]`  
  
 <span data-ttu-id="e8d65-111">결과는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="e8d65-111">Produces the following results:</span></span>  
  
|||||||  
|-|-|-|-|-|-|  
||<span data-ttu-id="e8d65-112">**모든 제품**</span><span class="sxs-lookup"><span data-stu-id="e8d65-112">**All Products**</span></span>|<span data-ttu-id="e8d65-113">**액세서리**</span><span class="sxs-lookup"><span data-stu-id="e8d65-113">**Accessories**</span></span>|<span data-ttu-id="e8d65-114">**자전거**</span><span class="sxs-lookup"><span data-stu-id="e8d65-114">**Bikes**</span></span>|<span data-ttu-id="e8d65-115">**Clothing**</span><span class="sxs-lookup"><span data-stu-id="e8d65-115">**Clothing**</span></span>|<span data-ttu-id="e8d65-116">**Components**</span><span class="sxs-lookup"><span data-stu-id="e8d65-116">**Components**</span></span>|  
|<span data-ttu-id="e8d65-117">**All Resellers**</span><span class="sxs-lookup"><span data-stu-id="e8d65-117">**All Resellers**</span></span>|<span data-ttu-id="e8d65-118">**$80,450,596.98**</span><span class="sxs-lookup"><span data-stu-id="e8d65-118">**$80,450,596.98**</span></span>|<span data-ttu-id="e8d65-119">**$571,297.93**</span><span class="sxs-lookup"><span data-stu-id="e8d65-119">**$571,297.93**</span></span>|<span data-ttu-id="e8d65-120">**$66,302,381.56**</span><span class="sxs-lookup"><span data-stu-id="e8d65-120">**$66,302,381.56**</span></span>|<span data-ttu-id="e8d65-121">**$1,777,840.84**</span><span class="sxs-lookup"><span data-stu-id="e8d65-121">**$1,777,840.84**</span></span>|<span data-ttu-id="e8d65-122">**$11,799,076.66**</span><span class="sxs-lookup"><span data-stu-id="e8d65-122">**$11,799,076.66**</span></span>|  
|<span data-ttu-id="e8d65-123">**Specialty Bike Shop**</span><span class="sxs-lookup"><span data-stu-id="e8d65-123">**Specialty Bike Shop**</span></span>|<span data-ttu-id="e8d65-124">**$6,756,166.18**</span><span class="sxs-lookup"><span data-stu-id="e8d65-124">**$6,756,166.18**</span></span>|<span data-ttu-id="e8d65-125">**$65,125.48**</span><span class="sxs-lookup"><span data-stu-id="e8d65-125">**$65,125.48**</span></span>|<span data-ttu-id="e8d65-126">**$6,080,117.73**</span><span class="sxs-lookup"><span data-stu-id="e8d65-126">**$6,080,117.73**</span></span>|<span data-ttu-id="e8d65-127">**$252,933.91**</span><span class="sxs-lookup"><span data-stu-id="e8d65-127">**$252,933.91**</span></span>|<span data-ttu-id="e8d65-128">**$357,989.07**</span><span class="sxs-lookup"><span data-stu-id="e8d65-128">**$357,989.07**</span></span>|  
|<span data-ttu-id="e8d65-129">**Value Added Reseller**</span><span class="sxs-lookup"><span data-stu-id="e8d65-129">**Value Added Reseller**</span></span>|<span data-ttu-id="e8d65-130">**$34,967,517.33**</span><span class="sxs-lookup"><span data-stu-id="e8d65-130">**$34,967,517.33**</span></span>|<span data-ttu-id="e8d65-131">**$175,002.81**</span><span class="sxs-lookup"><span data-stu-id="e8d65-131">**$175,002.81**</span></span>|<span data-ttu-id="e8d65-132">**$30,892,354.33**</span><span class="sxs-lookup"><span data-stu-id="e8d65-132">**$30,892,354.33**</span></span>|<span data-ttu-id="e8d65-133">**$592,385.71**</span><span class="sxs-lookup"><span data-stu-id="e8d65-133">**$592,385.71**</span></span>|<span data-ttu-id="e8d65-134">**$3,307,774.48**</span><span class="sxs-lookup"><span data-stu-id="e8d65-134">**$3,307,774.48**</span></span>|  
|<span data-ttu-id="e8d65-135">**웨어하우스**</span><span class="sxs-lookup"><span data-stu-id="e8d65-135">**Warehouse**</span></span>|<span data-ttu-id="e8d65-136">**$38,726,913.48**</span><span class="sxs-lookup"><span data-stu-id="e8d65-136">**$38,726,913.48**</span></span>|<span data-ttu-id="e8d65-137">**$331,169.64**</span><span class="sxs-lookup"><span data-stu-id="e8d65-137">**$331,169.64**</span></span>|<span data-ttu-id="e8d65-138">**$29,329,909.50**</span><span class="sxs-lookup"><span data-stu-id="e8d65-138">**$29,329,909.50**</span></span>|<span data-ttu-id="e8d65-139">**$932,521.23**</span><span class="sxs-lookup"><span data-stu-id="e8d65-139">**$932,521.23**</span></span>|<span data-ttu-id="e8d65-140">**$8,133,313.11**</span><span class="sxs-lookup"><span data-stu-id="e8d65-140">**$8,133,313.11**</span></span>|  
  
## <a name="non-visual-on-rows-and-columns"></a><span data-ttu-id="e8d65-141">행과 열에 대한 보이지 않는 값 합계</span><span class="sxs-lookup"><span data-stu-id="e8d65-141">Non-Visual on rows and columns</span></span>  
 <span data-ttu-id="e8d65-142">Accessories 및 Clothing 제품과 Value Added Reseller 및 Warehouse 대리점에 대한 데이터만 포함된 테이블을 만들고 전체 합계를 유지하려면 NON VISUAL을 사용하여 다음과 같이 문을 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8d65-142">To produce a table with data only for the Accessories and Clothing products, the Value Added Reseller and Warehouse resellers, yet keeping the overall totals could be written as follows using NON VISUAL:</span></span>  
  
 `select [Category].members on 0,`  
  
 `[Business Type].members on 1`  
  
 `from NON VISUAL (Select {[Category].Accessories, [Category].Clothing} on 0,`  
  
 `{[Business Type].[Value Added Reseller], [Business Type].[Warehouse]} on 1`  
  
 `from [Adventure Works])`  
  
 `where [Measures].[Reseller Sales Amount]`  
  
 <span data-ttu-id="e8d65-143">결과는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="e8d65-143">Produces the following results:</span></span>  
  
|||||  
|-|-|-|-|  
||<span data-ttu-id="e8d65-144">**모든 제품**</span><span class="sxs-lookup"><span data-stu-id="e8d65-144">**All Products**</span></span>|<span data-ttu-id="e8d65-145">**액세서리**</span><span class="sxs-lookup"><span data-stu-id="e8d65-145">**Accessories**</span></span>|<span data-ttu-id="e8d65-146">**Clothing**</span><span class="sxs-lookup"><span data-stu-id="e8d65-146">**Clothing**</span></span>|  
|<span data-ttu-id="e8d65-147">**All Resellers**</span><span class="sxs-lookup"><span data-stu-id="e8d65-147">**All Resellers**</span></span>|<span data-ttu-id="e8d65-148">**$80,450,596.98**</span><span class="sxs-lookup"><span data-stu-id="e8d65-148">**$80,450,596.98**</span></span>|<span data-ttu-id="e8d65-149">**$571,297.93**</span><span class="sxs-lookup"><span data-stu-id="e8d65-149">**$571,297.93**</span></span>|<span data-ttu-id="e8d65-150">**$1,777,840.84**</span><span class="sxs-lookup"><span data-stu-id="e8d65-150">**$1,777,840.84**</span></span>|  
|<span data-ttu-id="e8d65-151">**Value Added Reseller**</span><span class="sxs-lookup"><span data-stu-id="e8d65-151">**Value Added Reseller**</span></span>|<span data-ttu-id="e8d65-152">**$34,967,517.33**</span><span class="sxs-lookup"><span data-stu-id="e8d65-152">**$34,967,517.33**</span></span>|<span data-ttu-id="e8d65-153">**$175,002.81**</span><span class="sxs-lookup"><span data-stu-id="e8d65-153">**$175,002.81**</span></span>|<span data-ttu-id="e8d65-154">**$592,385.71**</span><span class="sxs-lookup"><span data-stu-id="e8d65-154">**$592,385.71**</span></span>|  
|<span data-ttu-id="e8d65-155">**웨어하우스**</span><span class="sxs-lookup"><span data-stu-id="e8d65-155">**Warehouse**</span></span>|<span data-ttu-id="e8d65-156">**$38,726,913.48**</span><span class="sxs-lookup"><span data-stu-id="e8d65-156">**$38,726,913.48**</span></span>|<span data-ttu-id="e8d65-157">**$331,169.64**</span><span class="sxs-lookup"><span data-stu-id="e8d65-157">**$331,169.64**</span></span>|<span data-ttu-id="e8d65-158">**$932,521.23**</span><span class="sxs-lookup"><span data-stu-id="e8d65-158">**$932,521.23**</span></span>|  
  
## <a name="non-visual-on-rows"></a><span data-ttu-id="e8d65-159">행에 대한 보이지 않는 값 합계</span><span class="sxs-lookup"><span data-stu-id="e8d65-159">Non-Visual on rows</span></span>  
 <span data-ttu-id="e8d65-160">열에는 보이는 값 합계만 포함하고 행 합계에는 모든 [Category]의 순 합계를 표시하는 테이블을 만들려면 다음과 같은 쿼리를 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8d65-160">To produce a table that visually totals the columns but for row totals brings the true total of all [Category], the following query should be issued:</span></span>  
  
 `select [Category].members on 0,`  
  
 `[Business Type].members on 1`  
  
 `from NON VISUAL (Select {[Category].Accessories, [Category].Clothing} on 0`  
  
 `from ( Select {[Business Type].[Value Added Reseller], [Business Type].[Warehouse]} on 0`  
  
 `from [Adventure Works])`  
  
 `)`  
  
 `where [Measures].[Reseller Sales Amount]`  
  
 <span data-ttu-id="e8d65-161">NON VISUAL이 어떻게 [Category]에만 적용되는지 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="e8d65-161">Note how NON VISUAL is only applied to [Category].</span></span>  
  
 <span data-ttu-id="e8d65-162">위 쿼리는 다음과 같은 결과를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="e8d65-162">The above query produces the following results:</span></span>  
  
|||||  
|-|-|-|-|  
||<span data-ttu-id="e8d65-163">All Products</span><span class="sxs-lookup"><span data-stu-id="e8d65-163">All Products</span></span>|<span data-ttu-id="e8d65-164">액세서리</span><span class="sxs-lookup"><span data-stu-id="e8d65-164">Accessories</span></span>|<span data-ttu-id="e8d65-165">Clothing</span><span class="sxs-lookup"><span data-stu-id="e8d65-165">Clothing</span></span>|  
|<span data-ttu-id="e8d65-166">All Resellers</span><span class="sxs-lookup"><span data-stu-id="e8d65-166">All Resellers</span></span>|<span data-ttu-id="e8d65-167">$73,694,430.80</span><span class="sxs-lookup"><span data-stu-id="e8d65-167">$73,694,430.80</span></span>|<span data-ttu-id="e8d65-168">$506,172.45</span><span class="sxs-lookup"><span data-stu-id="e8d65-168">$506,172.45</span></span>|<span data-ttu-id="e8d65-169">$1,524,906.93</span><span class="sxs-lookup"><span data-stu-id="e8d65-169">$1,524,906.93</span></span>|  
|<span data-ttu-id="e8d65-170">Value Added Reseller</span><span class="sxs-lookup"><span data-stu-id="e8d65-170">Value Added Reseller</span></span>|<span data-ttu-id="e8d65-171">$34,967,517.33</span><span class="sxs-lookup"><span data-stu-id="e8d65-171">$34,967,517.33</span></span>|<span data-ttu-id="e8d65-172">$175,002.81</span><span class="sxs-lookup"><span data-stu-id="e8d65-172">$175,002.81</span></span>|<span data-ttu-id="e8d65-173">$592,385.71</span><span class="sxs-lookup"><span data-stu-id="e8d65-173">$592,385.71</span></span>|  
|<span data-ttu-id="e8d65-174">Warehouse</span><span class="sxs-lookup"><span data-stu-id="e8d65-174">Warehouse</span></span>|<span data-ttu-id="e8d65-175">$38,726,913.48</span><span class="sxs-lookup"><span data-stu-id="e8d65-175">$38,726,913.48</span></span>|<span data-ttu-id="e8d65-176">$331,169.64</span><span class="sxs-lookup"><span data-stu-id="e8d65-176">$331,169.64</span></span>|<span data-ttu-id="e8d65-177">$932,521.23</span><span class="sxs-lookup"><span data-stu-id="e8d65-177">$932,521.23</span></span>|  
  
 <span data-ttu-id="e8d65-178">이전 결과와 비교하면 [All Resellers] 행에는 [Value Added Reseller] 및 [Warehouse]에 표시된 값에 대한 합계가 표시되고 [All Products] 열에는 표시되지 않은 제품을 포함한 모든 제품의 합계 값이 표시되는 것을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8d65-178">When compared with the previous results, you can observe that the [All Resellers] row now adds up to the displayed values for [Value Added Reseller] and [Warehouse] but that the [All Products] column shows the total value for all products, including those not displayed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8d65-179">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e8d65-179">See Also</span></span>  
 <span data-ttu-id="e8d65-180">[MDX의 주요 개념 &#40;Analysis Services&#41;](../key-concepts-in-mdx-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="e8d65-180">[Key Concepts in MDX &#40;Analysis Services&#41;](../key-concepts-in-mdx-analysis-services.md) </span></span>  
 <span data-ttu-id="e8d65-181">[Autoexist](autoexists.md) </span><span class="sxs-lookup"><span data-stu-id="e8d65-181">[Autoexists](autoexists.md) </span></span>  
 <span data-ttu-id="e8d65-182">[MDX &#40;멤버, 튜플 및 집합을 사용 하 여 작업&#41;](working-with-members-tuples-and-sets-mdx.md) </span><span class="sxs-lookup"><span data-stu-id="e8d65-182">[Working with Members, Tuples, and Sets &#40;MDX&#41;](working-with-members-tuples-and-sets-mdx.md) </span></span>  
 <span data-ttu-id="e8d65-183">[MDX 쿼리 기본 사항 &#40;Analysis Services&#41;](mdx-query-fundamentals-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="e8d65-183">[MDX Query Fundamentals &#40;Analysis Services&#41;](mdx-query-fundamentals-analysis-services.md) </span></span>  
 <span data-ttu-id="e8d65-184">[MDX &#40;기본 MDX 쿼리&#41;](mdx-query-the-basic-query.md) </span><span class="sxs-lookup"><span data-stu-id="e8d65-184">[The Basic MDX Query &#40;MDX&#41;](mdx-query-the-basic-query.md) </span></span>  
 <span data-ttu-id="e8d65-185">[쿼리 및 Slicer 축을 사용 하 여 쿼리를 제한 &#40;MDX&#41;](mdx-query-and-slicer-axes-restricting-the-query.md) </span><span class="sxs-lookup"><span data-stu-id="e8d65-185">[Restricting the Query with Query and Slicer Axes &#40;MDX&#41;](mdx-query-and-slicer-axes-restricting-the-query.md) </span></span>  
 [<span data-ttu-id="e8d65-186">쿼리에 큐브 컨텍스트 설정&#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="e8d65-186">Establishing Cube Context in a Query &#40;MDX&#41;</span></span>](establishing-cube-context-in-a-query-mdx.md)  
  
  
