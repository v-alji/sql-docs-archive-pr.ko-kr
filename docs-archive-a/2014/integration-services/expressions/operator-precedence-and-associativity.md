---
title: 연산자 우선 순위 및 계산 방향 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- associativity [Integration Services]
- precedence [Integration Services]
ms.assetid: 5094164f-dabc-45b5-b611-384feb2b3fe3
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 90ec23f9e961cbe4df291b9670c09e51d5d8704b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734375"
---
# <a name="operator-precedence-and-associativity"></a><span data-ttu-id="64406-102">연산자 우선 순위 및 계산 방향</span><span class="sxs-lookup"><span data-stu-id="64406-102">Operator Precedence and Associativity</span></span>
  <span data-ttu-id="64406-103">식 계산기가 지원하는 연산자 집합의 각 연산자에는 우선 순위 계층에서 지정된 우선 순위와 계산 방향이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="64406-103">Each operator in the set of operators that the expression evaluator supports has a designated precedence in the precedence hierarchy and includes a direction in which it is evaluated.</span></span> <span data-ttu-id="64406-104">연산자의 계산 방향은 연산자의 연결성을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="64406-104">The direction of evaluation for an operator is operator associativity.</span></span> <span data-ttu-id="64406-105">우선 순위가 높은 연산자가 우선 순위가 낮은 연산자보다 먼저 계산됩니다.</span><span class="sxs-lookup"><span data-stu-id="64406-105">Operators with higher precedence are evaluated before operators with lower precedence.</span></span> <span data-ttu-id="64406-106">복잡한 식에 여러 개의 연산자가 있을 경우 연산자 우선 순위가 연산 수행 순서를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="64406-106">If a complex expression has multiple operators, operator precedence determines the order in which the operations are performed.</span></span> <span data-ttu-id="64406-107">실행 순서는 결과 값에 중대한 영향을 줄 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="64406-107">The order of execution can significantly affect the resulting value.</span></span> <span data-ttu-id="64406-108">일부 연산자는 우선 순위가 같습니다.</span><span class="sxs-lookup"><span data-stu-id="64406-108">Some operators have equal precedence.</span></span> <span data-ttu-id="64406-109">우선 순위가 같은 여러 개의 연산자가 식에 포함되어 있으면 연산자는 왼쪽에서 오른쪽으로 또는 오른쪽에서 왼쪽으로 계산됩니다.</span><span class="sxs-lookup"><span data-stu-id="64406-109">If an expression contains multiple operators of equal precedence, the operators are evaluated directionally, from left to right or right to left.</span></span>  
  
 <span data-ttu-id="64406-110">다음 표에서는 연산자의 우선 순위를 높은 순서부터 낮은 순서로 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="64406-110">The following table lists the precedence of operators in order of high to low.</span></span> <span data-ttu-id="64406-111">동일한 수준의 연산자는 우선 순위가 같습니다.</span><span class="sxs-lookup"><span data-stu-id="64406-111">Operators at the same level have equal precedence.</span></span>  
  
|<span data-ttu-id="64406-112">연산자 기호</span><span class="sxs-lookup"><span data-stu-id="64406-112">Operator symbol</span></span>|<span data-ttu-id="64406-113">연산 유형</span><span class="sxs-lookup"><span data-stu-id="64406-113">Type of Operation</span></span>|<span data-ttu-id="64406-114">계산 방향</span><span class="sxs-lookup"><span data-stu-id="64406-114">Associativity</span></span>|  
|---------------------|-----------------------|-------------------|  
|<span data-ttu-id="64406-115">( )</span><span class="sxs-lookup"><span data-stu-id="64406-115">( )</span></span>|<span data-ttu-id="64406-116">식</span><span class="sxs-lookup"><span data-stu-id="64406-116">Expression</span></span>|<span data-ttu-id="64406-117">왼쪽에서 오른쪽</span><span class="sxs-lookup"><span data-stu-id="64406-117">Left to right</span></span>|  
|<span data-ttu-id="64406-118">-, !, ~</span><span class="sxs-lookup"><span data-stu-id="64406-118">-, !, ~</span></span>|<span data-ttu-id="64406-119">단항 연산자</span><span class="sxs-lookup"><span data-stu-id="64406-119">Unary</span></span>|<span data-ttu-id="64406-120">오른쪽에서 왼쪽</span><span class="sxs-lookup"><span data-stu-id="64406-120">Right to left</span></span>|  
|<span data-ttu-id="64406-121">casts</span><span class="sxs-lookup"><span data-stu-id="64406-121">casts</span></span>|<span data-ttu-id="64406-122">단항 연산자</span><span class="sxs-lookup"><span data-stu-id="64406-122">Unary</span></span>|<span data-ttu-id="64406-123">오른쪽에서 왼쪽</span><span class="sxs-lookup"><span data-stu-id="64406-123">Right to left</span></span>|  
|<span data-ttu-id="64406-124">\*, / ,%</span><span class="sxs-lookup"><span data-stu-id="64406-124">\*, / ,%</span></span>|<span data-ttu-id="64406-125">곱셈</span><span class="sxs-lookup"><span data-stu-id="64406-125">Multiplicative</span></span>|<span data-ttu-id="64406-126">왼쪽에서 오른쪽</span><span class="sxs-lookup"><span data-stu-id="64406-126">Left to right</span></span>|  
|<span data-ttu-id="64406-127">+, -</span><span class="sxs-lookup"><span data-stu-id="64406-127">+, -</span></span>|<span data-ttu-id="64406-128">가산적</span><span class="sxs-lookup"><span data-stu-id="64406-128">Additive</span></span>|<span data-ttu-id="64406-129">왼쪽에서 오른쪽</span><span class="sxs-lookup"><span data-stu-id="64406-129">Left to right</span></span>|  
|<span data-ttu-id="64406-130">\<, >, \<=, >=</span><span class="sxs-lookup"><span data-stu-id="64406-130">\<, >, \<=, >=</span></span>|<span data-ttu-id="64406-131">관계형</span><span class="sxs-lookup"><span data-stu-id="64406-131">Relational</span></span>|<span data-ttu-id="64406-132">왼쪽에서 오른쪽</span><span class="sxs-lookup"><span data-stu-id="64406-132">Left to right</span></span>|  
|<span data-ttu-id="64406-133">==, !=</span><span class="sxs-lookup"><span data-stu-id="64406-133">==, !=</span></span>|<span data-ttu-id="64406-134">등호</span><span class="sxs-lookup"><span data-stu-id="64406-134">Equality</span></span>|<span data-ttu-id="64406-135">왼쪽에서 오른쪽</span><span class="sxs-lookup"><span data-stu-id="64406-135">Left to right</span></span>|  
|&|<span data-ttu-id="64406-136">비트 AND</span><span class="sxs-lookup"><span data-stu-id="64406-136">Bitwise AND</span></span>|<span data-ttu-id="64406-137">왼쪽에서 오른쪽</span><span class="sxs-lookup"><span data-stu-id="64406-137">Left to right</span></span>|  
|^|<span data-ttu-id="64406-138">배타적 비트 OR</span><span class="sxs-lookup"><span data-stu-id="64406-138">Bitwise exclusive OR</span></span>|<span data-ttu-id="64406-139">왼쪽에서 오른쪽</span><span class="sxs-lookup"><span data-stu-id="64406-139">Left to right</span></span>|  
|<span data-ttu-id="64406-140">&#124;</span><span class="sxs-lookup"><span data-stu-id="64406-140">&#124;</span></span>|<span data-ttu-id="64406-141">포괄적 비트 OR</span><span class="sxs-lookup"><span data-stu-id="64406-141">Bitwise inclusive OR</span></span>|<span data-ttu-id="64406-142">왼쪽에서 오른쪽</span><span class="sxs-lookup"><span data-stu-id="64406-142">Left to right</span></span>|  
|&&|<span data-ttu-id="64406-143">논리적 AND</span><span class="sxs-lookup"><span data-stu-id="64406-143">Logical AND</span></span>|<span data-ttu-id="64406-144">왼쪽에서 오른쪽</span><span class="sxs-lookup"><span data-stu-id="64406-144">Left to right</span></span>|  
|<span data-ttu-id="64406-145">&#124;&#124;</span><span class="sxs-lookup"><span data-stu-id="64406-145">&#124;&#124;</span></span>|<span data-ttu-id="64406-146">논리적 OR</span><span class="sxs-lookup"><span data-stu-id="64406-146">Logical OR</span></span>|<span data-ttu-id="64406-147">왼쪽에서 오른쪽</span><span class="sxs-lookup"><span data-stu-id="64406-147">Left to right</span></span>|  
|<span data-ttu-id="64406-148">?</span><span class="sxs-lookup"><span data-stu-id="64406-148">?</span></span> <span data-ttu-id="64406-149">:</span><span class="sxs-lookup"><span data-stu-id="64406-149">:</span></span>|<span data-ttu-id="64406-150">조건 식</span><span class="sxs-lookup"><span data-stu-id="64406-150">Conditional expression</span></span>|<span data-ttu-id="64406-151">오른쪽에서 왼쪽</span><span class="sxs-lookup"><span data-stu-id="64406-151">Right to left</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="64406-152">참고 항목</span><span class="sxs-lookup"><span data-stu-id="64406-152">See Also</span></span>  
 [<span data-ttu-id="64406-153">연산자&#40;SSIS 식&#41;</span><span class="sxs-lookup"><span data-stu-id="64406-153">Operators &#40;SSIS Expression&#41;</span></span>](operators-ssis-expression.md)  
  
  
