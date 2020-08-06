---
title: 멤버, 튜플 및 집합 작업 (MDX) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- MDX [Analysis Services], tuples
- member keys [MDX]
- MDX [Analysis Services], sets
- calculated members [MDX]
- members [MDX]
- Multidimensional Expressions [Analysis Services], members
- named sets [MDX]
- Multidimensional Expressions [Analysis Services], tuples
- member functions [MDX]
- sets [MDX]
- MDX [Analysis Services], members
- member names [MDX]
- Multidimensional Expressions [Analysis Services], sets
- tuple functions
- tuples
- set functions [MDX]
ms.assetid: b6ec2439-caef-46d3-9fd7-5f4526cee334
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5ce3bf2d5ad7df2b1cd74897b3b49c7cef97e8ed
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646679"
---
# <a name="working-with-members-tuples-and-sets-mdx"></a><span data-ttu-id="97bd8-102">멤버, 튜플 및 집합 작업(MDX)</span><span class="sxs-lookup"><span data-stu-id="97bd8-102">Working with Members, Tuples, and Sets (MDX)</span></span>
  <span data-ttu-id="97bd8-103">MDX는 하나 이상의 멤버, 튜플 또는 집합을 반환하거나 멤버, 튜플 또는 집합에 대해 실행되는 다양한 함수를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="97bd8-103">MDX provides numerous functions that return one or more members, tuples, or sets; or that act upon a member, tuple, or set.</span></span>  
  
## <a name="member-functions"></a><span data-ttu-id="97bd8-104">멤버 함수</span><span class="sxs-lookup"><span data-stu-id="97bd8-104">Member Functions</span></span>  
 <span data-ttu-id="97bd8-105">MDX는 차원, 수준, 집합 또는 튜플 등의 다른 MDX 엔터티에서 멤버를 검색할 수 있는 여러 함수를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="97bd8-105">MDX provides several functions for retrieving members from other MDX entities, such as from dimensions, levels, sets, or tuples.</span></span> <span data-ttu-id="97bd8-106">예를 들어 [FirstChild](/sql/mdx/firstchild-mdx) 함수는 멤버에 대해 실행되고 멤버를 반환하는 함수입니다.</span><span class="sxs-lookup"><span data-stu-id="97bd8-106">For example, the [FirstChild](/sql/mdx/firstchild-mdx) function is a function that acts upon a member and returns a member.</span></span>  
  
 <span data-ttu-id="97bd8-107">다음 예에서와 같이 Time 차원의 첫 번째 자식 멤버를 가져오기 위해 명시적으로 멤버를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="97bd8-107">To obtain the first child member of the Time dimension, you can explicitly state the member, as in the following example.</span></span>  
  
```  
SELECT [Date].[Calendar Year].[CY 2001] on 0  
FROM [Adventure Works]  
  
```  
  
 <span data-ttu-id="97bd8-108">또한 다음 예에서와 같이 `FirstChild` 함수를 사용하여 앞의 예제와 동일한 멤버를 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="97bd8-108">You can also use the `FirstChild` function to return the same member, as in the following example.</span></span>  
  
```  
SELECT [Date].[Calendar Year].FirstChild on 0  
FROM [Adventure Works]  
  
```  
  
 <span data-ttu-id="97bd8-109">MDX 멤버 함수에 대한 자세한 내용은 [MDX 함수 참조&#40;MDX&#41;](/sql/mdx/mdx-function-reference-mdx)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="97bd8-109">For more information about MDX member functions, see [MDX Function Reference &#40;MDX&#41;](/sql/mdx/mdx-function-reference-mdx).</span></span>  
  
## <a name="tuple-functions"></a><span data-ttu-id="97bd8-110">튜플 함수</span><span class="sxs-lookup"><span data-stu-id="97bd8-110">Tuple Functions</span></span>  
 <span data-ttu-id="97bd8-111">MDX는 튜플을 반환하는 몇 개의 함수를 제공하며 튜플이 허용되는 곳이면 어디든 이 함수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="97bd8-111">MDX provides several functions that return tuples, and they can be used anywhere that a tuple is accepted.</span></span> <span data-ttu-id="97bd8-112">예를 들어 [Item&#40;Tuple&#41;&#40;MDX&#41;](/sql/mdx/item-tuple-mdx) 함수를 사용하여 집합에서 첫 번째 튜플을 추출할 수 있습니다. 이 함수는 집합이 단일 튜플로 구성되어 있을 때 튜플이 필요한 함수에 튜플을 제공하려는 경우에 매우 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="97bd8-112">For example, the [Item &#40;Tuple&#41; &#40;MDX&#41;](/sql/mdx/item-tuple-mdx) function can be used to extract the first tuple from set, which is very useful when you know that a set is composed of a single tuple and you want to supply that tuple to a function that requires a tuple.</span></span>  
  
 <span data-ttu-id="97bd8-113">다음 예에서는 튜플 집합 내의 첫 번째 튜플을 열 축에 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="97bd8-113">The following example returns the first tuple from within the set of tuples on the column axis.</span></span>  
  
```  
SELECT {  
   ([Measures].[Reseller Sales Amount]  
      ,[Date].[Calendar Year].[CY 2003]  
   )  
, ([Measures].[Reseller Sales Amount]  
      ,[Date].[Calendar Year].[CY 2004]  
   )  
}.Item(0)  
ON COLUMNS   
FROM [Adventure Works]  
```  
  
 <span data-ttu-id="97bd8-114">튜플 함수에 대한 자세한 내용은 [MDX 함수 참조&#40;MDX&#41;](/sql/mdx/mdx-function-reference-mdx)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="97bd8-114">For more information about tuple functions, see [MDX Function Reference &#40;MDX&#41;](/sql/mdx/mdx-function-reference-mdx).</span></span>  
  
## <a name="set-functions"></a><span data-ttu-id="97bd8-115">집합 함수</span><span class="sxs-lookup"><span data-stu-id="97bd8-115">Set Functions</span></span>  
 <span data-ttu-id="97bd8-116">MDX는 집합을 반환하는 여러 함수를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="97bd8-116">MDX provides several functions that return sets.</span></span> <span data-ttu-id="97bd8-117">명시적으로 튜플을 입력하고 중괄호로 묶는 것이 집합 검색을 위한 유일한 방법은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="97bd8-117">Explicitly typing tuples and enclosing them in braces is not the only way to retrieve a set.</span></span> <span data-ttu-id="97bd8-118">집합을 반환하는 멤버 함수에 대한 자세한 내용은 [MDX의 주요 개념&#40;Analysis Services&#41;](../key-concepts-in-mdx-analysis-services.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="97bd8-118">For more information about the members function to return a set, see [Key Concepts in MDX &#40;Analysis Services&#41;](../key-concepts-in-mdx-analysis-services.md).</span></span> <span data-ttu-id="97bd8-119">여러 가지 추가 집합 함수가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="97bd8-119">There are many additional set functions.</span></span>  
  
 <span data-ttu-id="97bd8-120">콜론 연산자를 사용하면 멤버의 자연 순서를 사용해 집합을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="97bd8-120">The colon operator lets you use the natural order of members to create a set.</span></span> <span data-ttu-id="97bd8-121">예를 들어 다음 예의 집합은 2002년 1분기부터 4분기까지의 튜플을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="97bd8-121">For example, the set shown in the following example contains tuples for the 1st through the 4th quarter of calendar year 2002.</span></span>  
  
```  
SELECT   
   {[Calendar Quarter].[Q1 CY 2002]:[Calendar Quarter].[Q4 CY 2002]}   
ON 0  
FROM [Adventure Works]  
```  
  
 <span data-ttu-id="97bd8-122">콜론 연산자를 사용하여 집합을 만들지 않을 경우 다음 예에서처럼 튜플을 지정하여 동일한 멤버 집합을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="97bd8-122">If you do not use the colon operator to create the set, you can create the same set of members by specifying the tuples in the following example.</span></span>  
  
```  
SELECT {  
   [Calendar Quarter].[Q1 CY 2002],   
   [Calendar Quarter].[Q2 CY 2002],   
   [Calendar Quarter].[Q3 CY 2002],   
   [Calendar Quarter].[Q4 CY 2002]  
   } ON 0  
FROM [Adventure Works]  
  
```  
  
 <span data-ttu-id="97bd8-123">콜론 연산자는 시작과 끝을 포함하는 함수이므로</span><span class="sxs-lookup"><span data-stu-id="97bd8-123">The colon operator is an inclusive function.</span></span> <span data-ttu-id="97bd8-124">연산자 양쪽의 멤버도 결과 집합에 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="97bd8-124">The members on both sides of the colon operator are included in the resulting set.</span></span>  
  
 <span data-ttu-id="97bd8-125">집합 함수에 대한 자세한 내용은 [MDX 함수 참조&#40;MDX&#41;](/sql/mdx/mdx-function-reference-mdx)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="97bd8-125">For more information about set functions, see [MDX Function Reference &#40;MDX&#41;](/sql/mdx/mdx-function-reference-mdx).</span></span>  
  
## <a name="array-functions"></a><span data-ttu-id="97bd8-126">배열 함수</span><span class="sxs-lookup"><span data-stu-id="97bd8-126">Array Functions</span></span>  
 <span data-ttu-id="97bd8-127">배열 함수는 집합에 대해 실행되고 배열을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="97bd8-127">An array function acts upon a set and returns an array.</span></span> <span data-ttu-id="97bd8-128">배열 함수에 대한 자세한 내용은 [MDX 함수 참조&#40;MDX&#41;](/sql/mdx/mdx-function-reference-mdx)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="97bd8-128">For more information about array functions, see [MDX Function Reference &#40;MDX&#41;](/sql/mdx/mdx-function-reference-mdx).</span></span>  
  
## <a name="hierarchy-functions"></a><span data-ttu-id="97bd8-129">계층 함수</span><span class="sxs-lookup"><span data-stu-id="97bd8-129">Hierarchy Functions</span></span>  
 <span data-ttu-id="97bd8-130">계층 함수는 멤버, 수준, 계층 또는 문자열에 대해 실행되며 계층을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="97bd8-130">A hierarchy function returns a hierarchy by acting upon a member, level, hierarchy, or string.</span></span> <span data-ttu-id="97bd8-131">계층 함수에 대한 자세한 내용은 [MDX 함수 참조&#40;MDX&#41;](/sql/mdx/mdx-function-reference-mdx)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="97bd8-131">For more information about hierarchy functions, see [MDX Function Reference &#40;MDX&#41;](/sql/mdx/mdx-function-reference-mdx).</span></span>  
  
## <a name="level-functions"></a><span data-ttu-id="97bd8-132">수준 함수</span><span class="sxs-lookup"><span data-stu-id="97bd8-132">Level Functions</span></span>  
 <span data-ttu-id="97bd8-133">수준 함수는 멤버, 수준 또는 문자열에 대해 실행되며 수준을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="97bd8-133">A level function returns a level by acting upon a member, level, or string.</span></span> <span data-ttu-id="97bd8-134">수준 함수에 대한 자세한 내용은 [MDX 함수 참조&#40;MDX&#41;](/sql/mdx/mdx-function-reference-mdx)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="97bd8-134">For more information about level functions, see [MDX Function Reference &#40;MDX&#41;](/sql/mdx/mdx-function-reference-mdx).</span></span>  
  
## <a name="logical-functions"></a><span data-ttu-id="97bd8-135">논리 함수</span><span class="sxs-lookup"><span data-stu-id="97bd8-135">Logical Functions</span></span>  
 <span data-ttu-id="97bd8-136">논리 함수는 MDX 식에 대해 실행되며 식의 튜플, 멤버 또는 집합에 대한 정보를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="97bd8-136">A logical function acts upon a MDX expression to return information about the tuples, members, or sets in the expression.</span></span> <span data-ttu-id="97bd8-137">예를 들어 [IsEmpty&#40;MDX&#41;](/sql/mdx/isempty-mdx) 함수는 식이 빈 셀 값을 반환했는지 여부를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="97bd8-137">For example, the [IsEmpty &#40;MDX&#41;](/sql/mdx/isempty-mdx) function evaluates whether an expression has returned an empty cell value.</span></span> <span data-ttu-id="97bd8-138">논리 함수에 대한 자세한 내용은 [MDX 함수 참조&#40;MDX&#41;](/sql/mdx/mdx-function-reference-mdx)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="97bd8-138">For more information about logical functions, see [MDX Function Reference &#40;MDX&#41;](/sql/mdx/mdx-function-reference-mdx).</span></span>  
  
## <a name="numeric-functions"></a><span data-ttu-id="97bd8-139">숫자 함수</span><span class="sxs-lookup"><span data-stu-id="97bd8-139">Numeric Functions</span></span>  
 <span data-ttu-id="97bd8-140">숫자 함수는 MDX 식에 대해 실행되며 스칼라 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="97bd8-140">A numeric function acts upon a MDX expression to return a scalar value.</span></span> <span data-ttu-id="97bd8-141">예를 들어 [Aggregate&#40;MDX&#41;](/sql/mdx/aggregate-mdx) 함수는 지정된 집합의 튜플에 대해 측정값을 집계하여 계산된 스칼라 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="97bd8-141">For example, the [Aggregate &#40;MDX&#41;](/sql/mdx/aggregate-mdx) function returns a scalar value calculated by aggregating measures over the tuples in a specified set.</span></span> <span data-ttu-id="97bd8-142">숫자 함수에 대한 자세한 내용은 [MDX 함수 참조&#40;MDX&#41;](/sql/mdx/mdx-function-reference-mdx)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="97bd8-142">For more information about numeric functions, see [MDX Function Reference &#40;MDX&#41;](/sql/mdx/mdx-function-reference-mdx).</span></span>  
  
## <a name="string-functions"></a><span data-ttu-id="97bd8-143">문자열 함수</span><span class="sxs-lookup"><span data-stu-id="97bd8-143">String Functions</span></span>  
 <span data-ttu-id="97bd8-144">문자열 함수는 MDX 식에 대해 실행되며 문자열을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="97bd8-144">A string function acts upon a MDX expression to return a string.</span></span> <span data-ttu-id="97bd8-145">예를 들어 [UniqueName&#40;MDX&#41;](/sql/mdx/uniquename-mdx) 함수는 차원, 계층, 수준 또는 멤버의 고유 이름이 들어 있는 문자열 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="97bd8-145">For example, the [UniqueName &#40;MDX&#41;](/sql/mdx/uniquename-mdx) function returns a string value containing the unique name of a dimension, hierarchy, level, or member.</span></span> <span data-ttu-id="97bd8-146">문자열 함수에 대한 자세한 내용은 [MDX 함수 참조&#40;MDX&#41;](/sql/mdx/mdx-function-reference-mdx)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="97bd8-146">For more information about string functions, see [MDX Function Reference &#40;MDX&#41;](/sql/mdx/mdx-function-reference-mdx).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97bd8-147">참고 항목</span><span class="sxs-lookup"><span data-stu-id="97bd8-147">See Also</span></span>  
 <span data-ttu-id="97bd8-148">[MDX의 주요 개념 &#40;Analysis Services&#41;](../key-concepts-in-mdx-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="97bd8-148">[Key Concepts in MDX &#40;Analysis Services&#41;](../key-concepts-in-mdx-analysis-services.md) </span></span>  
 <span data-ttu-id="97bd8-149">[MDX 쿼리 기본 사항 &#40;Analysis Services&#41;](mdx-query-fundamentals-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="97bd8-149">[MDX Query Fundamentals &#40;Analysis Services&#41;](mdx-query-fundamentals-analysis-services.md) </span></span>  
 [<span data-ttu-id="97bd8-150">MDX 함수 참조&#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="97bd8-150">MDX Function Reference &#40;MDX&#41;</span></span>](/sql/mdx/mdx-function-reference-mdx)  
  
  
