---
title: 쿼리 범위 셀 계산 만들기 (MDX) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- WITH keyword
- query-scoped cell calculations [MDX]
ms.assetid: 45987daa-4400-41e9-add7-2428fd75709b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5a9c9d529bfeb26b959b2521e4ce3c3d7f10d082
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741392"
---
# <a name="creating-query-scoped-cell-calculations-mdx"></a><span data-ttu-id="a1ef1-102">쿼리 범위 셀 계산 만들기(MDX)</span><span class="sxs-lookup"><span data-stu-id="a1ef1-102">Creating Query-Scoped Cell Calculations (MDX)</span></span>
  <span data-ttu-id="a1ef1-103">MDX에서 `WITH` 키워드를 사용하여 쿼리 컨텍스트 내의 계산 셀을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="a1ef1-103">You use the `WITH` keyword in Multidimensional Expressions (MDX) to describe calculated cells within the context of a query.</span></span> <span data-ttu-id="a1ef1-104">`WITH` 키워드는 다음 구문을 가집니다.</span><span class="sxs-lookup"><span data-stu-id="a1ef1-104">The `WITH` keyword has the following syntax:</span></span>  
  
```  
WITH CELL CALCULATION Cube_Name.CellCalc_Identifier  String_Expression  
```  
  
 <span data-ttu-id="a1ef1-105">`CellCalc_Identifier` 값은 계산 셀의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="a1ef1-105">The `CellCalc_Identifier` value is the name of the calculated cells.</span></span> <span data-ttu-id="a1ef1-106">`String_Expression` 값에는 직각의 단일 차원 MDX 집합 식 목록이 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1ef1-106">The `String_Expression` value contains a list of orthogonal, single-dimensional MDX set expressions.</span></span> <span data-ttu-id="a1ef1-107">이들 각각의 집합 식은 다음 테이블에 나열된 범주 중 하나로 확인되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1ef1-107">Each of these set expressions must resolve to one of the categories listed in the following table.</span></span>  
  
|<span data-ttu-id="a1ef1-108">Category</span><span class="sxs-lookup"><span data-stu-id="a1ef1-108">Category</span></span>|<span data-ttu-id="a1ef1-109">설명</span><span class="sxs-lookup"><span data-stu-id="a1ef1-109">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="a1ef1-110">빈 집합</span><span class="sxs-lookup"><span data-stu-id="a1ef1-110">Empty set</span></span>|<span data-ttu-id="a1ef1-111">빈 집합으로 확인되는 MDX 집합 식입니다.</span><span class="sxs-lookup"><span data-stu-id="a1ef1-111">An MDX set expression that resolves into an empty set.</span></span> <span data-ttu-id="a1ef1-112">이 경우 계산 셀의 범위는 전체 큐브입니다.</span><span class="sxs-lookup"><span data-stu-id="a1ef1-112">In this case, the scope of the calculated cell is the whole cube.</span></span>|  
|<span data-ttu-id="a1ef1-113">단일 멤버 집합</span><span class="sxs-lookup"><span data-stu-id="a1ef1-113">Single member set</span></span>|<span data-ttu-id="a1ef1-114">단일 멤버로 확인되는 MDX 집합 식입니다.</span><span class="sxs-lookup"><span data-stu-id="a1ef1-114">An MDX set expression that resolves into a single member.</span></span>|  
|<span data-ttu-id="a1ef1-115">수준 멤버 집합</span><span class="sxs-lookup"><span data-stu-id="a1ef1-115">Set of level members</span></span>|<span data-ttu-id="a1ef1-116">단일 수준의 멤버로 확인되는 MDX 집합 식입니다.</span><span class="sxs-lookup"><span data-stu-id="a1ef1-116">An MDX set expression that resolves into the members of a single level.</span></span> <span data-ttu-id="a1ef1-117">이러한 집합 식의 예는 *Level_Expression*입니다.`Members`</span><span class="sxs-lookup"><span data-stu-id="a1ef1-117">An example of such a set expression is the *Level_Expression*.`Members`</span></span> <span data-ttu-id="a1ef1-118">MDX 함수.</span><span class="sxs-lookup"><span data-stu-id="a1ef1-118">MDX function.</span></span> <span data-ttu-id="a1ef1-119">계산 멤버를 포함 하려면 *Level_Expression*을 사용 합니다.`AllMembers`</span><span class="sxs-lookup"><span data-stu-id="a1ef1-119">To include calculated members, use the *Level_Expression*.`AllMembers`</span></span> <span data-ttu-id="a1ef1-120">MDX 함수.</span><span class="sxs-lookup"><span data-stu-id="a1ef1-120">MDX function.</span></span> <span data-ttu-id="a1ef1-121">자세한 내용은 [AllMembers&#40;MDX&#41;](/sql/mdx/allmembers-mdx)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a1ef1-121">For more information, see [AllMembers &#40;MDX&#41;](/sql/mdx/allmembers-mdx).</span></span>|  
|<span data-ttu-id="a1ef1-122">하위 항목 집합</span><span class="sxs-lookup"><span data-stu-id="a1ef1-122">Set of descendants</span></span>|<span data-ttu-id="a1ef1-123">지정된 멤버의 하위 항목으로 확인되는 MDX 집합 식입니다.</span><span class="sxs-lookup"><span data-stu-id="a1ef1-123">An MDX set expression that resolves into the descendants of a specified member.</span></span> <span data-ttu-id="a1ef1-124">이러한 집합 식의 예는 `Descendants` (*Member_Expression*, *Level_Expresion*, *Desc_Flag*) MDX 함수입니다.</span><span class="sxs-lookup"><span data-stu-id="a1ef1-124">An example of such a set expression is the `Descendants`(*Member_Expression*, *Level_Expresion*, *Desc_Flag*) MDX function.</span></span> <span data-ttu-id="a1ef1-125">자세한 내용은 [Descendants&#40;MDX&#41;](/sql/mdx/descendants-mdx)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a1ef1-125">For more information, see [Descendants &#40;MDX&#41;](/sql/mdx/descendants-mdx).</span></span>|  
  
 <span data-ttu-id="a1ef1-126">`String_Expression` 인수가 차원을 설명하지 않으면 MDX는 계산 하위 큐브를 만들 목적으로 모든 멤버가 포함되는 것으로 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="a1ef1-126">If the `String_Expression` argument does not describe a dimension, MDX assumes that all members are included for the purposes of constructing the calculation subcube.</span></span> <span data-ttu-id="a1ef1-127">따라서 `String_Expression` 인수가 NULL이면 계산 셀 정의는 전체 큐브에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="a1ef1-127">Therefore, if the `String_Expression` argument is NULL, the calculated cells definition applies to the whole cube.</span></span>  
  
 <span data-ttu-id="a1ef1-128">`MDX_Expression` 인수는 `String_Expression` 인수에 정의된 모든 셀에 대한 셀 값이 되는 MDX 식을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="a1ef1-128">The `MDX_Expression` argument contains an MDX expression that evaluates to a cell value for all the cells defined in the `String_Expression` argument.</span></span>  
  
## <a name="additional-considerations"></a><span data-ttu-id="a1ef1-129">기타 고려 사항</span><span class="sxs-lookup"><span data-stu-id="a1ef1-129">Additional Considerations</span></span>  
 <span data-ttu-id="a1ef1-130">MDX는 `CONDITION` 속성으로 지정되는 계산 조건을 한 번만 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="a1ef1-130">MDX processes the calculation condition, specified by the `CONDITION` property, only once.</span></span> <span data-ttu-id="a1ef1-131">이 단 한 번의 처리로 특히 전체 큐브 패스에 대해 중복되는 계산 셀을 통해 여러 계산 셀 정의 평가에 대한 성능이 향상됩니다.</span><span class="sxs-lookup"><span data-stu-id="a1ef1-131">This single processing provides increased performance for the evaluation of multiple calculated cells definitions, especially with overlapping calculated cells across cube passes.</span></span>  
  
 <span data-ttu-id="a1ef1-132">이런 단일 처리가 발생하는 시기는 계산 셀 정의의 작성 범위에 따라 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="a1ef1-132">When this single processing occurs depends on the creation scope of the calculated cells definition:</span></span>  
  
-   <span data-ttu-id="a1ef1-133">전체 범위에서 큐브의 일부로 만들어지는 경우 MDX는 큐브가 처리될 때 계산 조건을 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="a1ef1-133">If created at global scope, as part of a cube, MDX process the calculation condition when the cube is processed.</span></span> <span data-ttu-id="a1ef1-134">큐브에서 어떤 방식으로든 셀이 수정되고 그 셀이 계산 셀 정의의 계산 하위 큐브에 포함되는 경우에는 큐브가 다시 처리될 때까지는 셀 조건이 정확하지 않을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1ef1-134">If cells are modified in the cube in any way, and the cells are included in the calculation subcube of a calculated cells definition, the calculation condition may not be accurate until the cube is reprocessed.</span></span> <span data-ttu-id="a1ef1-135">예를 들어 셀은 쓰기 저장에서 수정될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1ef1-135">Cell modification can occur from writebacks, for example.</span></span> <span data-ttu-id="a1ef1-136">계산 조건은 큐브를 다시 처리할 때 다시 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="a1ef1-136">The calculation condition is reprocessed when the cube is reprocessed.</span></span>  
  
-   <span data-ttu-id="a1ef1-137">세션 범위에서 만들어진 경우 MDX는 세션 중에 문이 실행될 때 계산 조건을 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="a1ef1-137">If created at session scope, MDX process the calculation condition when the statement is issued during the session.</span></span> <span data-ttu-id="a1ef1-138">계산 셀 정의가 전체적으로 만들어지는 경우와 마찬가지로, 셀이 수정되는 경우에는 계산 조건이 계산 셀 정의에 대해 정확하지 않을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1ef1-138">As with calculated cells definitions created globally, if the cells are modified, the calculation condition may not be accurate for the calculated cells definition.</span></span>  
  
-   <span data-ttu-id="a1ef1-139">쿼리 범위에서 만들어진 경우 MDX는 쿼리가 실행될 때 계산 조건을 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="a1ef1-139">If created at query scope, MDX processes the calculation condition when the query runs.</span></span> <span data-ttu-id="a1ef1-140">MDX 쿼리 실행의 짧은 처리 시간 때문에 데이터 대기 시간 문제가 최소화되긴 하지만 셀 수정 문제는 여기서도 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="a1ef1-140">The cell modification issue applies here, also, although data latency issues are minimal because of the low processing time of MDX query execution.</span></span>  
  
 <span data-ttu-id="a1ef1-141">한편으로 MDX는 계산 셀 정의에 포함된 셀과 관련된 큐브에 대해 MDX 쿼리를 실행할 때마다 계산 수식을 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="a1ef1-141">On the other hand, MDX processes the calculation formula whenever an MDX query is issued against the cube involving cells included in the calculated cells definition.</span></span> <span data-ttu-id="a1ef1-142">작성 범위에 상관없이 이렇게 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="a1ef1-142">This processing occurs regardless of the creation scope.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1ef1-143">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a1ef1-143">See Also</span></span>  
 [<span data-ttu-id="a1ef1-144">CREATE CELL CALCULATION 문&#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="a1ef1-144">CREATE CELL CALCULATION Statement &#40;MDX&#41;</span></span>](/sql/mdx/mdx-data-definition-create-cell-calculation)  
  
  
