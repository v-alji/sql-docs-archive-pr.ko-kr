---
title: 패스 순서 및 계산 순서 이해 (MDX) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- evaluation order [MDX]
- calculation order [MDX]
- SOLVE_ORDER property
- queries [MDX], solve orders
- solve orders [MDX]
- pass orders [MDX]
- expressions [MDX], solve orders
ms.assetid: 7ed7d4ee-4644-4c5d-99a4-c4b429d0203c
author: minewiskan
ms.author: owend
ms.openlocfilehash: d92ccd9d1eeb05272a95c6f429f8c756bcb0022e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649734"
---
# <a name="understanding-pass-order-and-solve-order-mdx"></a><span data-ttu-id="63341-102">패스 순서 및 계산 순서 이해(MDX)</span><span class="sxs-lookup"><span data-stu-id="63341-102">Understanding Pass Order and Solve Order (MDX)</span></span>
  <span data-ttu-id="63341-103">MDX 스크립트 결과로 계산될 때 큐브는 사용되는 여러 계산 관련 기능에 따라 여러 계산 단계를 거칠 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63341-103">When a cube is calculated as the result of an MDX script, it can go through many stages of computation depending on the use of various calculation-related features.</span></span> <span data-ttu-id="63341-104">이러한 각 단계를 계산 패스라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="63341-104">Each of these stages is referred to as a calculation pass.</span></span>  
  
 <span data-ttu-id="63341-105">계산 패스는 계산 패스 번호라는 서수 위치로 참조될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63341-105">A calculation pass can be referred to by an ordinal position, called the calculation pass number.</span></span> <span data-ttu-id="63341-106">큐브의 모든 셀 컴퓨팅을 완전히 마치는 데 필요한 컴퓨팅 패스 개수를 큐브의 컴퓨팅 패스 깊이라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="63341-106">The count of calculation passes that are required to fully compute all the cells of a cube is referred to as the calculation pass depth of the cube.</span></span>  
  
 <span data-ttu-id="63341-107">팩트 테이블 및 쓰기 저장 데이터는 패스 0에만 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="63341-107">Fact table and writeback data only impact pass 0.</span></span> <span data-ttu-id="63341-108">스크립트는 패스 0 이후의 데이터를 채우며 스크립트에서 각 대입식 및 계산 문은 새로운 패스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="63341-108">Scripts populate data after pass 0; each assignment and calculate statement in a script creates a new pass.</span></span> <span data-ttu-id="63341-109">MDX 스크립트 외부에서 절대 패스 0에 대한 참조는 큐브의 스크립트에서 만든 마지막 패스를 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="63341-109">Outside the MDX script, references to absolute pass 0 refer to the last pass created by the script for the cube.</span></span>  
  
 <span data-ttu-id="63341-110">계산 멤버는 모든 패스에서 생성되지만 식은 현재 패스에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="63341-110">Calculated members are created at all passes, but the expression is applied at the current pass.</span></span> <span data-ttu-id="63341-111">이전 패스에는 계산 측정값이 포함되지만 Null 값이 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63341-111">Prior passes contain the calculated measure, but with a null value.</span></span>  
  
## <a name="solve-order"></a><span data-ttu-id="63341-112">계산 순서</span><span class="sxs-lookup"><span data-stu-id="63341-112">Solve Order</span></span>  
 <span data-ttu-id="63341-113">계산 순서는 식을 완료하는 경우 계산의 우선 순위를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="63341-113">Solve order determines the priority of calculation in the event of competing expressions.</span></span> <span data-ttu-id="63341-114">단일 패스 내에서 계산 순서는 다음 두 가지를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="63341-114">Within a single pass, solve order determines two things:</span></span>  
  
-   <span data-ttu-id="63341-115">에서 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 차원, 멤버, 계산 멤버, 사용자 지정 롤업 및 계산 셀을 계산 하는 순서입니다.</span><span class="sxs-lookup"><span data-stu-id="63341-115">The order in which [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] evaluates dimensions, members, calculated members, custom rollups, and calculated cells.</span></span>  
  
-   <span data-ttu-id="63341-116">[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 에서 사용자 지정 멤버, 계산 멤버, 사용자 지정 롤업 및 계산 셀을 계산하는 순서</span><span class="sxs-lookup"><span data-stu-id="63341-116">The order in which [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] calculates custom members, calculated members, custom rollup, and calculated cells.</span></span>  
  
 <span data-ttu-id="63341-117">계산 순서가 가장 높은 멤버가 우선 순위가 가장 높습니다.</span><span class="sxs-lookup"><span data-stu-id="63341-117">The member with the highest solve order takes precedence.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="63341-118">집계 함수는 이러한 우선 순위에서 제외됩니다.</span><span class="sxs-lookup"><span data-stu-id="63341-118">The exception to this precedence is the Aggregate function.</span></span> <span data-ttu-id="63341-119">집계 함수의 계산 멤버는 교차하는 계산 측정값 보다 계산 순서가 낮습니다.</span><span class="sxs-lookup"><span data-stu-id="63341-119">Calculated members with the Aggregate function have a lower solve order than any intersecting calculated measure.</span></span>  
  
## <a name="solve-order-values-and-precedence"></a><span data-ttu-id="63341-120">계산 순서 값 및 우선 순위</span><span class="sxs-lookup"><span data-stu-id="63341-120">Solve Order Values and Precedence</span></span>  
 <span data-ttu-id="63341-121">계산 순서 값의 범위는 -8181에서 65535 사이입니다.</span><span class="sxs-lookup"><span data-stu-id="63341-121">Solve order values can range from -8181 to 65535.</span></span> <span data-ttu-id="63341-122">이 범위에서 일부 계산 순서 값은 다음 표에서와 같이 특정 유형의 계산에 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="63341-122">In this range, some solve order values correspond to specific kinds of calculations, as shown in the following table.</span></span>  
  
|<span data-ttu-id="63341-123">계산</span><span class="sxs-lookup"><span data-stu-id="63341-123">Calculation</span></span>|<span data-ttu-id="63341-124">계산 순서</span><span class="sxs-lookup"><span data-stu-id="63341-124">Solve Order</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="63341-125">사용자 지정 멤버 수식</span><span class="sxs-lookup"><span data-stu-id="63341-125">Custom member formulas</span></span>|<span data-ttu-id="63341-126">-5119</span><span class="sxs-lookup"><span data-stu-id="63341-126">-5119</span></span>|  
|<span data-ttu-id="63341-127">단항 연산자</span><span class="sxs-lookup"><span data-stu-id="63341-127">Unary operators</span></span>|<span data-ttu-id="63341-128">-5119</span><span class="sxs-lookup"><span data-stu-id="63341-128">-5119</span></span>|  
|<span data-ttu-id="63341-129">보이는 합계 계산</span><span class="sxs-lookup"><span data-stu-id="63341-129">Visual totals calculation</span></span>|<span data-ttu-id="63341-130">-4096</span><span class="sxs-lookup"><span data-stu-id="63341-130">-4096</span></span>|  
|<span data-ttu-id="63341-131">그 외 모든 계산(특별히 지정되지 않은 경우)</span><span class="sxs-lookup"><span data-stu-id="63341-131">All other calculations (if not otherwise specified)</span></span>|<span data-ttu-id="63341-132">0</span><span class="sxs-lookup"><span data-stu-id="63341-132">0</span></span>|  
  
 <span data-ttu-id="63341-133">계산 순서 값을 설정할 때는 양의 정수만 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="63341-133">It is highly recommended that you use only positive integers when setting solve order values.</span></span> <span data-ttu-id="63341-134">이전 테이블에서 표시된 계산 순서 값보다 낮은 값을 지정하면 계산 패스를 예측하지 못할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63341-134">If you assign values that are lower than the solve order values shown in the previous table, the calculation pass can become unpredictable.</span></span> <span data-ttu-id="63341-135">예를 들어 계산 멤버에 대한 계산에 기본 사용자 지정 롤업 수식 값인 -5119보다 낮은 계산 순서 값이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="63341-135">For example, the calculation for a calculated member receives a solve order value that is lower than the default custom rollup formula value of -5119.</span></span> <span data-ttu-id="63341-136">이러한 낮은 계산 순서 값은 계산 멤버가 사용자 지정 롤업 수식보다 먼저 계산되도록 하므로 잘못된 결과가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63341-136">Such a low solve order value causes the calculated members to be calculated before the custom rollup formulas, and can produce incorrect results.</span></span>  
  
### <a name="creating-and-changing-solve-order"></a><span data-ttu-id="63341-137">계산 순서 만들기 및 바꾸기</span><span class="sxs-lookup"><span data-stu-id="63341-137">Creating and Changing Solve Order</span></span>  
 <span data-ttu-id="63341-138">큐브 디자이너의 **계산**창에서 계산 순서를 바꿔서 계산 멤버 및 계산 셀에 대한 계산 순서를 바꿀 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63341-138">In Cube Designer, on the **Calculations Pane**, you can change the solve order for calculated members and calculated cells by changing the order of the calculations.</span></span>  
  
 <span data-ttu-id="63341-139">MDX에서는 `SOLVE_ORDER` 키워드를 사용하여 계산 멤버 및 계산 셀을 만들거나 바꿀 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63341-139">In MDX, you can use the `SOLVE_ORDER` keyword to create or change calculated members and calculated cells.</span></span>  
  
## <a name="solve-order-examples"></a><span data-ttu-id="63341-140">계산 순서 예</span><span class="sxs-lookup"><span data-stu-id="63341-140">Solve Order Examples</span></span>  
 <span data-ttu-id="63341-141">계산 순서의 복잡성을 설명하기 위해 다음 일련의 MDX 쿼리는 각각 계산 순서가 문제시 되지 않는 두 개의 쿼리로 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="63341-141">To illustrate the potential complexities of solve order, the following series of MDX queries starts with two queries that each individually have no solve order issues.</span></span> <span data-ttu-id="63341-142">그런 다음 이 두 쿼리는 계산 순서가 필요한 하나의 쿼리로 조합됩니다.</span><span class="sxs-lookup"><span data-stu-id="63341-142">These two queries are then combined into a query that requires solve order.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="63341-143">Adventure Works 예제 다차원 데이터베이스에 대해 이러한 MDX 쿼리를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63341-143">You can run these MDX queries against the Adventure Works sample multidimensional database.</span></span> <span data-ttu-id="63341-144">codeplex 사이트에서 [AdventureWorks 다차원 모델 SQL Server 2012](https://msftdbprodsamples.codeplex.com/releases/view/55330) 예제를 다운로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63341-144">You can download the [AdventureWorks Multidimensional Models SQL Server 2012](https://msftdbprodsamples.codeplex.com/releases/view/55330) sample from the codeplex site.</span></span>  
  
### <a name="query-1-differences-in-income-and-expenses"></a><span data-ttu-id="63341-145">쿼리 1-수입 및 비용 차이</span><span class="sxs-lookup"><span data-stu-id="63341-145">Query 1-Differences in Income and Expenses</span></span>  
 <span data-ttu-id="63341-146">첫 번째 MDX 쿼리에서는 다음 예와 비슷한 간단한 MDX 쿼리를 구성하여 각 해의 판매액 및 비용 차이를 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="63341-146">For the first MDX query, calculate the difference in sales and costs for each year by constructing a simple MDX query similar to the following example:</span></span>  
  
```  
WITH   
MEMBER  
[Date].[Calendar].[Year Difference] AS ([Date].[Calendar].[Calendar Year].&[2008] - [Date].[Calendar].[Calendar Year].&[2007] )  
SELECT   
{[Measures].[Internet Sales Amount], [Measures].[Internet Total Product Cost] }  
ON COLUMNS ,  
{ [Date].[Calendar].[Calendar Year].&[2007], [Date].[Calendar].[Calendar Year].&[2008], [Date].[Year Difference] }  
ON ROWS  
FROM [Adventure Works]  
```  
  
 <span data-ttu-id="63341-147">이 쿼리에는 계산 멤버가 `Year Difference`하나만 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63341-147">In this query, there is only one calculated member, `Year Difference`.</span></span> <span data-ttu-id="63341-148">계산 멤버가 하나뿐이기 때문에 큐브에 계산 멤버가 사용되지 않으면 계산 순서가 문제가 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="63341-148">Because there is only one calculated member, solve order is not an issue, as long as the cube does not use any calculated members.</span></span>  
  
 <span data-ttu-id="63341-149">이 MDX 쿼리는 다음 표와 비슷한 결과 집합을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="63341-149">This MDX query produces a result set similar to the following table.</span></span>  
  
||<span data-ttu-id="63341-150">Internet Sales Amount</span><span class="sxs-lookup"><span data-stu-id="63341-150">Internet Sales Amount</span></span>|<span data-ttu-id="63341-151">Internet Total Product Cost</span><span class="sxs-lookup"><span data-stu-id="63341-151">Internet Total Product Cost</span></span>|  
|-|---------------------------|---------------------------------|  
|<span data-ttu-id="63341-152">**CY 2007**</span><span class="sxs-lookup"><span data-stu-id="63341-152">**CY 2007**</span></span>|<span data-ttu-id="63341-153">$9,791,060.30</span><span class="sxs-lookup"><span data-stu-id="63341-153">$9,791,060.30</span></span>|<span data-ttu-id="63341-154">$5,718,327.17</span><span class="sxs-lookup"><span data-stu-id="63341-154">$5,718,327.17</span></span>|  
|<span data-ttu-id="63341-155">**CY 2008**</span><span class="sxs-lookup"><span data-stu-id="63341-155">**CY 2008**</span></span>|<span data-ttu-id="63341-156">$9,770,899.74</span><span class="sxs-lookup"><span data-stu-id="63341-156">$9,770,899.74</span></span>|<span data-ttu-id="63341-157">$5,721,205.24</span><span class="sxs-lookup"><span data-stu-id="63341-157">$5,721,205.24</span></span>|  
|<span data-ttu-id="63341-158">**Year Difference**</span><span class="sxs-lookup"><span data-stu-id="63341-158">**Year Difference**</span></span>|<span data-ttu-id="63341-159">($20,160.56)</span><span class="sxs-lookup"><span data-stu-id="63341-159">($20,160.56)</span></span>|<span data-ttu-id="63341-160">$2,878.06</span><span class="sxs-lookup"><span data-stu-id="63341-160">$2,878.06</span></span>|  
  
### <a name="query-2-percentage-of-income-after-expenses"></a><span data-ttu-id="63341-161">쿼리 2-지출 후 수입 비율</span><span class="sxs-lookup"><span data-stu-id="63341-161">Query 2-Percentage of Income after Expenses</span></span>  
 <span data-ttu-id="63341-162">두 번째 쿼리에서는 다음 MDX 쿼리를 사용하여 각 해의 비용에 따른 수입 백분율을 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="63341-162">For the second query, calculate the percentage of income after expenses for each year using the following MDX query:</span></span>  
  
```  
WITH   
MEMBER  
[Measures].[Profit Margin] AS   
([Measures].[Internet Sales Amount] - [Measures].[Internet Total Product Cost] ) / [Measures].[Internet Sales Amount] ,  
FORMAT_STRING="Percent"  
SELECT   
{[Measures].[Internet Sales Amount], [Measures].[Internet Total Product Cost], [Measures].[Profit Margin] }  
ON COLUMNS ,  
{ [Date].[Calendar].[Calendar Year].&[2007], [Date].[Calendar].[Calendar Year].&[2008] }  
ON ROWS  
FROM [Adventure Works]  
```  
  
 <span data-ttu-id="63341-163">이 MDX 쿼리에는 이전 쿼리와 같이 계산 멤버가 `Profit Margin`하나만 있으며, 따라서 계산 순서와 관련된 복잡한 문제가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="63341-163">This MDX query, like the previous one, has only a single calculated member, `Profit Margin`, and therefore does not have any solve order complications.</span></span>  
  
 <span data-ttu-id="63341-164">이 MDX 쿼리는 다음 표와 비슷한 약간 다른 결과 집합을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="63341-164">This MDX query produces a slightly different result set, similar to the following table.</span></span>  
  
||<span data-ttu-id="63341-165">Internet Sales Amount</span><span class="sxs-lookup"><span data-stu-id="63341-165">Internet Sales Amount</span></span>|<span data-ttu-id="63341-166">Internet Total Product Cost</span><span class="sxs-lookup"><span data-stu-id="63341-166">Internet Total Product Cost</span></span>|<span data-ttu-id="63341-167">이익률</span><span class="sxs-lookup"><span data-stu-id="63341-167">Profit Margin</span></span>|  
|-|---------------------------|---------------------------------|-------------------|  
|<span data-ttu-id="63341-168">**CY 2007**</span><span class="sxs-lookup"><span data-stu-id="63341-168">**CY 2007**</span></span>|<span data-ttu-id="63341-169">$9,791,060.30</span><span class="sxs-lookup"><span data-stu-id="63341-169">$9,791,060.30</span></span>|<span data-ttu-id="63341-170">$5,718,327.17</span><span class="sxs-lookup"><span data-stu-id="63341-170">$5,718,327.17</span></span>|<span data-ttu-id="63341-171">41.60%</span><span class="sxs-lookup"><span data-stu-id="63341-171">41.60%</span></span>|  
|<span data-ttu-id="63341-172">**CY 2008**</span><span class="sxs-lookup"><span data-stu-id="63341-172">**CY 2008**</span></span>|<span data-ttu-id="63341-173">$9,770,899.74</span><span class="sxs-lookup"><span data-stu-id="63341-173">$9,770,899.74</span></span>|<span data-ttu-id="63341-174">$5,721,205.24</span><span class="sxs-lookup"><span data-stu-id="63341-174">$5,721,205.24</span></span>|<span data-ttu-id="63341-175">41.45%</span><span class="sxs-lookup"><span data-stu-id="63341-175">41.45%</span></span>|  
  
 <span data-ttu-id="63341-176">결과 집합에서 첫 번째 쿼리와 두 번째 쿼리의 차이는 계산 멤버의 배치 차이로 인해 비롯됩니다.</span><span class="sxs-lookup"><span data-stu-id="63341-176">The difference in result sets between the first query and the second query comes from the difference in placement of the calculated member.</span></span> <span data-ttu-id="63341-177">첫 번째 쿼리에서 계산 멤버는 두 번째 쿼리에 표시된 COLUMNS 축이 아니라 ROWS 축의 일부입니다.</span><span class="sxs-lookup"><span data-stu-id="63341-177">In the first query, the calculated member is part of the ROWS axis, not the COLUMNS axis shown in the second query.</span></span> <span data-ttu-id="63341-178">이러한 배치 차이는 두 계산 멤버를 단일 MDX 쿼리로 조합하는 다음 쿼리에서 중요해집니다.</span><span class="sxs-lookup"><span data-stu-id="63341-178">This difference in placement becomes important in the next query, which combines the two calculated members in a single MDX query.</span></span>  
  
### <a name="query-3-combined-year-difference-and-net-income-calculations"></a><span data-ttu-id="63341-179">쿼리 3-결합 된 연도 차이 및 순 수입 계산</span><span class="sxs-lookup"><span data-stu-id="63341-179">Query 3-Combined Year Difference and Net Income Calculations</span></span>  
 <span data-ttu-id="63341-180">이 마지막 쿼리에서는 이전 예에서의 두 쿼리를 단일 MDX 쿼리로 조합하며 열과 행 모두에 대한 계산 때문에 계산 순서가 중요해집니다.</span><span class="sxs-lookup"><span data-stu-id="63341-180">In this final query combining both of the previous examples into a single MDX query, solve order becomes important because of the calculations on both columns and rows.</span></span> <span data-ttu-id="63341-181">올바른 순서로 계산되도록 보장하기 위해 `SOLVE_ORDER` 키워드를 사용하여 계산이 발생하는 순서를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="63341-181">To make sure that the calculations occur in the correct sequence, define the sequence in which the calculations occur by using the `SOLVE_ORDER` keyword.</span></span>  
  
 <span data-ttu-id="63341-182">`SOLVE_ORDER` 키워드는 MDX 쿼리 또는 `CREATE MEMBER` 명령의 계산 멤버에 대한 계산 순서를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="63341-182">The `SOLVE_ORDER` keyword specifies the solve order of calculated members in an MDX query or a `CREATE MEMBER` command.</span></span> <span data-ttu-id="63341-183">`SOLVE_ORDER` 키워드에 사용된 정수 값은 상대적이며 0부터 시작할 필요가 없으며 연속적일 필요도 없습니다.</span><span class="sxs-lookup"><span data-stu-id="63341-183">The integer values used with the `SOLVE_ORDER` keyword are relative, do not need to start at zero, and do not need to be consecutive.</span></span> <span data-ttu-id="63341-184">이 값은 MDX에서 단순히 더 큰 값의 멤버 계산으로부터 파생된 값에 따라 멤버를 계산하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="63341-184">The value simply tells MDX to calculate a member based on values derived from calculating members with a higher value.</span></span> <span data-ttu-id="63341-185">계산 멤버가 `SOLVE_ORDER` 키워드 없이 정의된 경우 해당 계산 멤버의 기본값은 0입니다.</span><span class="sxs-lookup"><span data-stu-id="63341-185">If a calculated member is defined without the `SOLVE_ORDER` keyword, the default value of that calculated member is zero.</span></span>  
  
 <span data-ttu-id="63341-186">예를 들어 처음 두 쿼리 예에서 사용된 값을 조합할 경우 두 계산 멤버인 `Year Difference` 및 `Profit Margin`은 MDX 쿼리 예의 결과 데이터 세트에 있는 단일 셀에서 교차합니다.</span><span class="sxs-lookup"><span data-stu-id="63341-186">For example, if you combine the calculations used in the first two example queries, the two calculated members, `Year Difference` and `Profit Margin`, intersect at a single cell in the result dataset of the MDX query example.</span></span> <span data-ttu-id="63341-187">[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 에서 이 셀을 계산하는 방법은 계산 순서에 의해서만 결정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63341-187">The only way to determine how [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] will evaluate this cell is by the solve order.</span></span> <span data-ttu-id="63341-188">이 셀을 구성하는 데 사용된 수식은 두 계산 멤버의 계산 순서에 따라 서로 다른 결과를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="63341-188">The formulas that are used to construct this cell will produce different results depending upon the solve order of the two calculated members.</span></span>  
  
 <span data-ttu-id="63341-189">먼저 처음 두 쿼리에 사용된 계산을 다음 MDX 쿼리에서 조합해 보십시오.</span><span class="sxs-lookup"><span data-stu-id="63341-189">First, try combining the calculations used in the first two queries in the following MDX query:</span></span>  
  
```  
WITH   
MEMBER  
[Date].[Calendar].[Year Difference] AS ([Date].[Calendar].[Calendar Year].&[2008] - [Date].[Calendar].[Calendar Year].&[2007] ) ,  
SOLVE_ORDER = 1  
MEMBER  
[Measures].[Profit Margin] AS   
( [Measures].[Internet Sales Amount] - [Measures].[Internet Total Product Cost] ) / [Measures].[Internet Sales Amount] ,  
FORMAT_STRING="Percent" ,  
SOLVE_ORDER = 2  
SELECT   
{[Measures].[Internet Sales Amount], [Measures].[Internet Total Product Cost], [Measures].[Profit Margin] }  
ON COLUMNS ,  
{ [Date].[Calendar].[Calendar Year].&[2007], [Date].[Calendar].[Calendar Year].&[2008], [Date].[Year Difference] }  
ON ROWS  
FROM [Adventure Works]  
```  
  
 <span data-ttu-id="63341-190">이 조합된 MDX 쿼리 예에서 `Profit Margin` 은 계산 순서가 가장 높기 때문에 두 식이 교차할 때 우선 순위를 갖습니다.</span><span class="sxs-lookup"><span data-stu-id="63341-190">In this combined MDX query example, `Profit Margin` has the highest solve order, so it takes precedence when the two expressions interact.</span></span> [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] <span data-ttu-id="63341-191">는 `Profit Margin` 수식을 사용하여 문제의 셀을 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="63341-191">evaluates the cell in question by using the `Profit Margin` formula.</span></span> <span data-ttu-id="63341-192">이 중첩된 계산의 결과는 다음 표에 표시된 것과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="63341-192">The results of this nested calculation, as shown in the following table.</span></span>  
  
||<span data-ttu-id="63341-193">Internet Sales Amount</span><span class="sxs-lookup"><span data-stu-id="63341-193">Internet Sales Amount</span></span>|<span data-ttu-id="63341-194">Internet Total Product Cost</span><span class="sxs-lookup"><span data-stu-id="63341-194">Internet Total Product Cost</span></span>|<span data-ttu-id="63341-195">이익률</span><span class="sxs-lookup"><span data-stu-id="63341-195">Profit Margin</span></span>|  
|-|---------------------------|---------------------------------|-------------------|  
|<span data-ttu-id="63341-196">**CY 2007**</span><span class="sxs-lookup"><span data-stu-id="63341-196">**CY 2007**</span></span>|<span data-ttu-id="63341-197">$9,791,060.30</span><span class="sxs-lookup"><span data-stu-id="63341-197">$9,791,060.30</span></span>|<span data-ttu-id="63341-198">$5,718,327.17</span><span class="sxs-lookup"><span data-stu-id="63341-198">$5,718,327.17</span></span>|<span data-ttu-id="63341-199">41.60%</span><span class="sxs-lookup"><span data-stu-id="63341-199">41.60%</span></span>|  
|<span data-ttu-id="63341-200">**CY 2008**</span><span class="sxs-lookup"><span data-stu-id="63341-200">**CY 2008**</span></span>|<span data-ttu-id="63341-201">$9,770,899.74</span><span class="sxs-lookup"><span data-stu-id="63341-201">$9,770,899.74</span></span>|<span data-ttu-id="63341-202">$5,721,205.24</span><span class="sxs-lookup"><span data-stu-id="63341-202">$5,721,205.24</span></span>|<span data-ttu-id="63341-203">41.45%</span><span class="sxs-lookup"><span data-stu-id="63341-203">41.45%</span></span>|  
|<span data-ttu-id="63341-204">**Year Difference**</span><span class="sxs-lookup"><span data-stu-id="63341-204">**Year Difference**</span></span>|<span data-ttu-id="63341-205">($20,160.56)</span><span class="sxs-lookup"><span data-stu-id="63341-205">($20,160.56)</span></span>|<span data-ttu-id="63341-206">$2,878.06</span><span class="sxs-lookup"><span data-stu-id="63341-206">$2,878.06</span></span>|<span data-ttu-id="63341-207">114.28%</span><span class="sxs-lookup"><span data-stu-id="63341-207">114.28%</span></span>|  
  
 <span data-ttu-id="63341-208">공유 셀의 결과는 `Profit Margin`에 대한 수식을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="63341-208">The result in the shared cell is based on the formula for `Profit Margin`.</span></span> <span data-ttu-id="63341-209">즉, [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 는 `Year Difference` 데이터로 공유 셀의 결과를 계산하여 다음 수식을 만듭니다(쉽게 구분할 수 있도록 결과가 반올림됨).</span><span class="sxs-lookup"><span data-stu-id="63341-209">That is, [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] calculates the result in the shared cell with the `Year Difference` data, producing the following formula (the result is rounded for clarity):</span></span>  
  
```  
((9,770,899.74 - 9,791,060.30) - (5,721,205.24 - 5,718,327.17)) / (9,770,899.74 - 9,791,060.30) = 1.14275744   
```  
  
 <span data-ttu-id="63341-210">를 실행하거나</span><span class="sxs-lookup"><span data-stu-id="63341-210">or</span></span>  
  
```  
(23,038.63) / (20,160.56) = 114.28%  
```  
  
 <span data-ttu-id="63341-211">확실하게 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="63341-211">This is clearly incorrect.</span></span> <span data-ttu-id="63341-212">하지만 MDX 쿼리에서 계산 멤버에 대한 계산 순서를 바꾸면 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 는 공유 셀의 결과를 다르게 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="63341-212">However, [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] calculates the result in the shared cell differently if you switch the solve orders for the calculated members in the MDX query.</span></span> <span data-ttu-id="63341-213">다음 조합 MDX 쿼리는 계산 멤버에 대한 계산 순서를 반대로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="63341-213">The following combined MDX query reverses the solve order for the calculated members:</span></span>  
  
```  
WITH   
MEMBER  
[Date].[Calendar].[Year Difference] AS ([Date].[Calendar].[Calendar Year].&[2008] - [Date].[Calendar].[Calendar Year].&[2007] ) ,  
SOLVE_ORDER = 2  
MEMBER  
[Measures].[Profit Margin] AS   
( [Measures].[Internet Sales Amount] - [Measures].[Internet Total Product Cost] ) / [Measures].[Internet Sales Amount] ,  
FORMAT_STRING="Percent" ,  
SOLVE_ORDER = 1  
SELECT   
{[Measures].[Internet Sales Amount], [Measures].[Internet Total Product Cost], [Measures].[Profit Margin] }  
ON COLUMNS ,  
{ [Date].[Calendar].[Calendar Year].&[2007], [Date].[Calendar].[Calendar Year].&[2008], [Date].[Year Difference] }  
ON ROWS  
FROM [Adventure Works]  
```  
  
 <span data-ttu-id="63341-214">계산 멤버의 순서가 바뀌면 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 는 다음 표에 표시된 것과 같이 `Year Difference` 수식을 사용하여 셀을 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="63341-214">As the order of the calculated members has been switched, [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] uses the `Year Difference` formula to evaluate the cell, as shown in the following table.</span></span>  
  
||<span data-ttu-id="63341-215">Internet Sales Amount</span><span class="sxs-lookup"><span data-stu-id="63341-215">Internet Sales Amount</span></span>|<span data-ttu-id="63341-216">Internet Total Product Cost</span><span class="sxs-lookup"><span data-stu-id="63341-216">Internet Total Product Cost</span></span>|<span data-ttu-id="63341-217">이익률</span><span class="sxs-lookup"><span data-stu-id="63341-217">Profit Margin</span></span>|  
|-|---------------------------|---------------------------------|-------------------|  
|<span data-ttu-id="63341-218">**CY 2007**</span><span class="sxs-lookup"><span data-stu-id="63341-218">**CY 2007**</span></span>|<span data-ttu-id="63341-219">$9,791,060.30</span><span class="sxs-lookup"><span data-stu-id="63341-219">$9,791,060.30</span></span>|<span data-ttu-id="63341-220">$5,718,327.17</span><span class="sxs-lookup"><span data-stu-id="63341-220">$5,718,327.17</span></span>|<span data-ttu-id="63341-221">41.60%</span><span class="sxs-lookup"><span data-stu-id="63341-221">41.60%</span></span>|  
|<span data-ttu-id="63341-222">**CY 2008**</span><span class="sxs-lookup"><span data-stu-id="63341-222">**CY 2008**</span></span>|<span data-ttu-id="63341-223">$9,770,899.74</span><span class="sxs-lookup"><span data-stu-id="63341-223">$9,770,899.74</span></span>|<span data-ttu-id="63341-224">$5,721,205.24</span><span class="sxs-lookup"><span data-stu-id="63341-224">$5,721,205.24</span></span>|<span data-ttu-id="63341-225">41.45%</span><span class="sxs-lookup"><span data-stu-id="63341-225">41.45%</span></span>|  
|<span data-ttu-id="63341-226">**Year Difference**</span><span class="sxs-lookup"><span data-stu-id="63341-226">**Year Difference**</span></span>|<span data-ttu-id="63341-227">($20,160.56)</span><span class="sxs-lookup"><span data-stu-id="63341-227">($20,160.56)</span></span>|<span data-ttu-id="63341-228">$2,878.06</span><span class="sxs-lookup"><span data-stu-id="63341-228">$2,878.06</span></span>|<span data-ttu-id="63341-229">(0.15%)</span><span class="sxs-lookup"><span data-stu-id="63341-229">(0.15%)</span></span>|  
  
 <span data-ttu-id="63341-230">이 쿼리에는 `Year Difference` 데이터와 함께 `Profit Margin` 수식이 사용되기 때문에 공유 셀에 대한 수식은 다음 계산과 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="63341-230">Because this query uses the `Year Difference` formula with the `Profit Margin` data, the formula for the shared cell resembles the following calculation:</span></span>  
  
```  
(($9,770,899.74 - 5,721,205.24) / $9,770,899.74) - ((9,791,060.30 - 5,718,327.17) / 9,791,060.30) = -0.15   
```  
  
 <span data-ttu-id="63341-231">또는</span><span class="sxs-lookup"><span data-stu-id="63341-231">Or</span></span>  
  
```  
0.4145 - 0.4160= -0.15  
```  
  
## <a name="additional-considerations"></a><span data-ttu-id="63341-232">기타 고려 사항</span><span class="sxs-lookup"><span data-stu-id="63341-232">Additional Considerations</span></span>  
 <span data-ttu-id="63341-233">계산 멤버, 사용자 지정 롤업 수식 또는 계산 셀이 포함된 차원 수가 높은 큐브에서는 특히 계산 순서를 다루기가 매우 복잡할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63341-233">Solve order can be a very complex issue to deal with, especially in cubes with a high number of dimensions involving calculated member, custom rollup formulas, or calculated cells.</span></span> <span data-ttu-id="63341-234">[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 에서 MDX 쿼리를 계산할 때 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 는 MDX 쿼리에 지정된 큐브의 차원을 비롯하여 지정된 패스 내에 관련된 모든 사항에 대한 계산 순서 값을 고려합니다.</span><span class="sxs-lookup"><span data-stu-id="63341-234">When [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] evaluates an MDX query, [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] takes into account the solve order values for everything involved within a given pass, including the dimensions of the cube specified in the MDX query.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63341-235">참고 항목</span><span class="sxs-lookup"><span data-stu-id="63341-235">See Also</span></span>  
 <span data-ttu-id="63341-236">[CalculationCurrentPass &#40;MDX&#41;](/sql/mdx/calculationcurrentpass-mdx) </span><span class="sxs-lookup"><span data-stu-id="63341-236">[CalculationCurrentPass &#40;MDX&#41;](/sql/mdx/calculationcurrentpass-mdx) </span></span>  
 <span data-ttu-id="63341-237">[CalculationPassValue &#40;MDX&#41;](/sql/mdx/calculationpassvalue-mdx) </span><span class="sxs-lookup"><span data-stu-id="63341-237">[CalculationPassValue &#40;MDX&#41;](/sql/mdx/calculationpassvalue-mdx) </span></span>  
 <span data-ttu-id="63341-238">[CREATE MEMBER 문 &#40;MDX&#41;](/sql/mdx/mdx-data-definition-create-member) </span><span class="sxs-lookup"><span data-stu-id="63341-238">[CREATE MEMBER Statement &#40;MDX&#41;](/sql/mdx/mdx-data-definition-create-member) </span></span>  
 [<span data-ttu-id="63341-239">데이터 조작&#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="63341-239">Manipulating Data &#40;MDX&#41;</span></span>](mdx-data-manipulation-manipulating-data.md)  
  
