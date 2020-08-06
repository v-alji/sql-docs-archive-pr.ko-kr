---
title: 세션 범위 계산 셀 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- session-scoped calculated members [MDX]
ms.assetid: f2d14a89-6286-4e74-9afb-091076f93f21
author: minewiskan
ms.author: owend
ms.openlocfilehash: 199de07778a153cd1bc40b5033d364e5e0055bd3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649736"
---
# <a name="creating-session-scoped-calculated-cells"></a><span data-ttu-id="f6632-102">세션 범위 계산 셀 만들기</span><span class="sxs-lookup"><span data-stu-id="f6632-102">Creating Session-Scoped Calculated Cells</span></span>
    
> [!IMPORTANT]  
>  <span data-ttu-id="f6632-103">이 구문은 더 이상 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f6632-103">This syntax has been deprecated.</span></span> <span data-ttu-id="f6632-104">대신 MDX 대입을 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="f6632-104">You should use MDX assignments should instead.</span></span> <span data-ttu-id="f6632-105">할당에 대한 자세한 내용은 [기본 MDX 스크립트&#40;MDX&#41;](the-basic-mdx-script-mdx.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f6632-105">For more information on assignments, see [The Basic MDX Script &#40;MDX&#41;](the-basic-mdx-script-mdx.md).</span></span>  
  
 <span data-ttu-id="f6632-106">동일한 세션의 모든 쿼리에 사용할 수 있는 계산 셀을 만들려면 [CREATE CELL CALCULATION](/sql/mdx/mdx-data-definition-create-cell-calculation) 문 또는 [ALTER CUBE](/sql/mdx/mdx-data-definition-alter-cube) 문을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6632-106">To create calculated cells that are available to all queries in the same session, you can use either the [CREATE CELL CALCULATION](/sql/mdx/mdx-data-definition-create-cell-calculation) statement or the [ALTER CUBE](/sql/mdx/mdx-data-definition-alter-cube) statement.</span></span> <span data-ttu-id="f6632-107">두 문의 결과는 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="f6632-107">Both statements have the same result.</span></span>  
  
## <a name="create-cell-calculation-syntax"></a><span data-ttu-id="f6632-108">CREATE CELL CALCULATION 구문</span><span class="sxs-lookup"><span data-stu-id="f6632-108">CREATE CELL CALCULATION Syntax</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="f6632-109">이 구문은 더 이상 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f6632-109">This syntax has been deprecated.</span></span> <span data-ttu-id="f6632-110">대신 MDX 대입을 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="f6632-110">You should use MDX assignments should instead.</span></span> <span data-ttu-id="f6632-111">할당에 대한 자세한 내용은 [기본 MDX 스크립트&#40;MDX&#41;](the-basic-mdx-script-mdx.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f6632-111">For more information on assignments, see [The Basic MDX Script &#40;MDX&#41;](the-basic-mdx-script-mdx.md).</span></span>  
  
 <span data-ttu-id="f6632-112">세션 범위 계산 셀을 정의하려면 다음 구문을 이용해 CREATE CELL CALCULATION 문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f6632-112">Use the following syntax to use the CREATE CELL CALCULATION statement to define a session-scoped calculated cell:</span></span>  
  
```  
CREATE CELL CALCULATION Cube_Expression.<CREATE CELL CALCULATION body clause>  
  
<CREATE CELL CALCULATION body clause> ::=CellCalc_Identifier FOR String_Expression AS 'MDX_Expression'   
   [ <CREATE CELL CALCULATION property clause> [ , <CREATE CELL CALCULATION property clause> ... ] ]  
  
<CREATE CELL CALCULATION property clause> ::=  
   ( CONDITION = 'Logical_Expression' ) |   
   ( DISABLED = { TRUE | FALSE } ) |   
   ( DESCRIPTION =String_Expression ) |   
   ( CALCULATION_PASS_NUMBER = Integer_Expression ) |   
   ( CALCULATION_PASS_DEPTH = Integer_Expression ) |   
   ( SOLVE_ORDER = Integer_Expression ) |   
   ( FORMAT_STRING = String_Expression ) |   
   ( CellProperty_Identifier = Scalar_Expression )  
```  
  
## <a name="alter-cube-syntax"></a><span data-ttu-id="f6632-113">ALTER CUBE 구문</span><span class="sxs-lookup"><span data-stu-id="f6632-113">ALTER CUBE Syntax</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="f6632-114">이 구문은 더 이상 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f6632-114">This syntax has been deprecated.</span></span> <span data-ttu-id="f6632-115">대신 MDX 대입을 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="f6632-115">You should use MDX assignments should instead.</span></span> <span data-ttu-id="f6632-116">할당에 대한 자세한 내용은 [기본 MDX 스크립트&#40;MDX&#41;](the-basic-mdx-script-mdx.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f6632-116">For more information on assignments, see [The Basic MDX Script &#40;MDX&#41;](the-basic-mdx-script-mdx.md).</span></span>  
  
 <span data-ttu-id="f6632-117">세션 범위 계산 셀을 정의하는 ALTER CUBE 문에는 다음 구문을 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="f6632-117">Use the following syntax to use the ALTER CUBE statement to define a session-scoped calculated cell:</span></span>  
  
```  
ALTER CUBE Cube_Identifier CREATE CELL CALCULATION  
FOR String_Expression AS 'MDX_Expression'   
   [ <CREATE CELL CALCULATION property clause> [ , <CREATE CELL CALCULATION property clause> ... ] ]  
  
<CREATE CELL CALCULATION property clause> ::=  
   ( CONDITION = 'Logical_Expression' ) |   
   ( DISABLED = { TRUE | FALSE } ) |   
   ( DESCRIPTION =String_Expression ) |   
   ( CALCULATION_PASS_NUMBER = Integer_Expression ) |   
   ( CALCULATION_PASS_DEPTH = Integer_Expression ) |   
   ( SOLVE_ORDER = Integer_Expression ) |   
   ( FORMAT_STRING = String_Expression ) |   
   ( CellProperty_Identifier = Scalar_Expression )  
```  
  
 <span data-ttu-id="f6632-118">`String_Expression` 값은 다음 표에 나열된 집합의 범주 중 하나로 확인되어야 하는 직각의 단일 차원 MDX 집합 식 목록을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="f6632-118">The `String_Expression` value contains a list of orthogonal, single-dimensional MDX set expressions, each of which must resolve to one of the categories of sets that are listed in the following table.</span></span>  
  
|<span data-ttu-id="f6632-119">Category</span><span class="sxs-lookup"><span data-stu-id="f6632-119">Category</span></span>|<span data-ttu-id="f6632-120">Description</span><span class="sxs-lookup"><span data-stu-id="f6632-120">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="f6632-121">빈 집합</span><span class="sxs-lookup"><span data-stu-id="f6632-121">Empty set</span></span>|<span data-ttu-id="f6632-122">빈 집합으로 확인되는 MDX 집합 식입니다.</span><span class="sxs-lookup"><span data-stu-id="f6632-122">An MDX set expression that resolves into an empty set.</span></span> <span data-ttu-id="f6632-123">이 경우 계산 셀의 범위는 전체 큐브입니다.</span><span class="sxs-lookup"><span data-stu-id="f6632-123">In this case, the scope of the calculated cell is the whole cube.</span></span>|  
|<span data-ttu-id="f6632-124">단일 멤버 집합</span><span class="sxs-lookup"><span data-stu-id="f6632-124">Single member set</span></span>|<span data-ttu-id="f6632-125">단일 멤버로 확인되는 MDX 집합 식입니다.</span><span class="sxs-lookup"><span data-stu-id="f6632-125">An MDX set expression that resolves into a single member.</span></span>|  
|<span data-ttu-id="f6632-126">수준 멤버 집합</span><span class="sxs-lookup"><span data-stu-id="f6632-126">Set of level members</span></span>|<span data-ttu-id="f6632-127">단일 수준의 멤버로 확인되는 MDX 집합 식입니다.</span><span class="sxs-lookup"><span data-stu-id="f6632-127">An MDX set expression that resolves into the members of a single level.</span></span> <span data-ttu-id="f6632-128">이에 대 한 예는 *Level_Expression*입니다.`Members`</span><span class="sxs-lookup"><span data-stu-id="f6632-128">An example of this is the *Level_Expression*.`Members`</span></span> <span data-ttu-id="f6632-129">MDX 함수.</span><span class="sxs-lookup"><span data-stu-id="f6632-129">MDX function.</span></span> <span data-ttu-id="f6632-130">계산 멤버를 포함 하려면 *Level_Expression*을 사용 합니다.`AllMembers`</span><span class="sxs-lookup"><span data-stu-id="f6632-130">To include calculated members, use the *Level_Expression*.`AllMembers`</span></span> <span data-ttu-id="f6632-131">MDX 함수.</span><span class="sxs-lookup"><span data-stu-id="f6632-131">MDX function.</span></span><br /><br /> <span data-ttu-id="f6632-132">자세한 내용은 [AllMembers&#40;MDX&#41;](/sql/mdx/allmembers-mdx)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f6632-132">For more information, see [AllMembers &#40;MDX&#41;](/sql/mdx/allmembers-mdx).</span></span>|  
|<span data-ttu-id="f6632-133">하위 항목 집합</span><span class="sxs-lookup"><span data-stu-id="f6632-133">Set of descendants</span></span>|<span data-ttu-id="f6632-134">지정된 멤버의 하위 항목으로 확인되는 MDX 집합 식입니다.</span><span class="sxs-lookup"><span data-stu-id="f6632-134">An MDX set expression that resolves into the descendants of a specified member.</span></span> <span data-ttu-id="f6632-135">이에 대 한 예는 `Descendants` (*Member_Expression*, *Level_Expression*, *Desc_Flag*) MDX 함수입니다.</span><span class="sxs-lookup"><span data-stu-id="f6632-135">An example of this is the `Descendants`(*Member_Expression*, *Level_Expression*, *Desc_Flag*) MDX function.</span></span><br /><br /> <span data-ttu-id="f6632-136">자세한 내용은 [Descendants&#40;MDX&#41;](/sql/mdx/descendants-mdx)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f6632-136">For more information, see [Descendants &#40;MDX&#41;](/sql/mdx/descendants-mdx).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f6632-137">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f6632-137">See Also</span></span>  
 [<span data-ttu-id="f6632-138">MDX로 셀 계산 작성&#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="f6632-138">Building Cell Calculations in MDX &#40;MDX&#41;</span></span>](../../multidimensional-models-olap-logical-cube-objects/calculations.md)  
  
  
