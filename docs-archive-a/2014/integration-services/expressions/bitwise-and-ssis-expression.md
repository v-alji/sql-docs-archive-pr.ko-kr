---
title: '&amp; (비트 AND)(SSIS 식) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- AND, bitwise AND
- '& (bitwise AND)'
- bitwise AND (&)
ms.assetid: 06d2958e-66a5-44d8-8bc4-56209ebe1ff2
author: chugugrace
ms.author: chugu
ms.openlocfilehash: fbf3c8ffcef079e25c82478947bc3b92a6b4be93
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652968"
---
# <a name="amp-bitwise-and-ssis-expression"></a><span data-ttu-id="4eb75-102">&amp; (비트 AND)(SSIS 식)</span><span class="sxs-lookup"><span data-stu-id="4eb75-102">&amp; (Bitwise AND) (SSIS Expression)</span></span>
  <span data-ttu-id="4eb75-103">두 정수 값의 비트 AND 연산을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="4eb75-103">Performs a bitwise AND operation of two integer values.</span></span> <span data-ttu-id="4eb75-104">그런 후 첫 번째 피연산자의 각 비트를 두 번째 피연산자의 해당 비트와 비교합니다.</span><span class="sxs-lookup"><span data-stu-id="4eb75-104">It compares each bit of its first operand to the corresponding bit of its second operand.</span></span> <span data-ttu-id="4eb75-105">두 비트가 모두 1이면 해당 결과 비트가 1로 설정되고,</span><span class="sxs-lookup"><span data-stu-id="4eb75-105">If both bits are 1, the corresponding result bit is set to 1.</span></span> <span data-ttu-id="4eb75-106">그렇지 않으면 해당 결과 비트가 0으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="4eb75-106">Otherwise, the corresponding result bit is set to 0.</span></span>  
  
 <span data-ttu-id="4eb75-107">두 조건이 모두 부호 있는 정수 유형이거나 또는 부호 없는 정수 유형이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4eb75-107">Both conditions must be a signed integer type or both conditions must be an unsigned integer type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4eb75-108">구문</span><span class="sxs-lookup"><span data-stu-id="4eb75-108">Syntax</span></span>  
  
```  
  
integer_expression1 & integer_expression2  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="4eb75-109">인수</span><span class="sxs-lookup"><span data-stu-id="4eb75-109">Arguments</span></span>  
 <span data-ttu-id="4eb75-110">*integer_expression1, integer_expression2*</span><span class="sxs-lookup"><span data-stu-id="4eb75-110">*integer_expression1, integer_expression2*</span></span>  
 <span data-ttu-id="4eb75-111">부호가 있거나 부호가 없는 정수 데이터 형식의 유효한 식입니다.</span><span class="sxs-lookup"><span data-stu-id="4eb75-111">Is any valid expression of a signed or unsigned integer data type.</span></span> <span data-ttu-id="4eb75-112">자세한 내용은 [Integration Services Data Types](../data-flow/integration-services-data-types.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4eb75-112">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="4eb75-113">결과 형식</span><span class="sxs-lookup"><span data-stu-id="4eb75-113">Result Types</span></span>  
 <span data-ttu-id="4eb75-114">두 인수의 데이터 형식에 따라 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="4eb75-114">Determined by data types of the two arguments.</span></span> <span data-ttu-id="4eb75-115">자세한 내용은 [Integration Services Data Types in Expressions](integration-services-data-types-in-expressions.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4eb75-115">For more information, see [Integration Services Data Types in Expressions](integration-services-data-types-in-expressions.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4eb75-116">설명</span><span class="sxs-lookup"><span data-stu-id="4eb75-116">Remarks</span></span>  
 <span data-ttu-id="4eb75-117">둘 중 한 조건이 Null이면 식 결과도 Null입니다.</span><span class="sxs-lookup"><span data-stu-id="4eb75-117">If either condition is null, the expression result is null.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="4eb75-118">식 예</span><span class="sxs-lookup"><span data-stu-id="4eb75-118">Expression Examples</span></span>  
 <span data-ttu-id="4eb75-119">이 예에서는 **NumberA** 열과 **NumberB**열 사이에 비트 AND 연산을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="4eb75-119">This example performs a bitwise AND operation between the columns **NumberA** and **NumberB**.</span></span> <span data-ttu-id="4eb75-120">**NumberA** 열에는 3(0000011)이 포함되고 **NumberB** 열에는 7(00000111)이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="4eb75-120">**NumberA** contains 3 (0000011) and column **NumberB** contains 7 (00000111).</span></span>  
  
```  
NumberA & NumberB  
```  
  
 <span data-ttu-id="4eb75-121">식은 3(00000011)으로 계산됩니다.</span><span class="sxs-lookup"><span data-stu-id="4eb75-121">The expression evaluates to 3 (00000011).</span></span>  
  
 <span data-ttu-id="4eb75-122">00000011</span><span class="sxs-lookup"><span data-stu-id="4eb75-122">00000011</span></span>  
  
 <span data-ttu-id="4eb75-123">00000111</span><span class="sxs-lookup"><span data-stu-id="4eb75-123">00000111</span></span>  
  
 ----------\-  
  
 <span data-ttu-id="4eb75-124">00000011</span><span class="sxs-lookup"><span data-stu-id="4eb75-124">00000011</span></span>  
  
 <span data-ttu-id="4eb75-125">이 예에서는 **ReorderPoint** 열과 **SafetyStockLevel** 열 사이에 비트 AND 연산을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="4eb75-125">This example performs a bitwise AND operation between the **ReorderPoint** and **SafetyStockLevel** columns.</span></span>  
  
```  
ReorderPoint & SafetyStockLevel  
```  
  
 <span data-ttu-id="4eb75-126">**ReorderPoint** 가 10이고 **SafetyStockLevel** 이 8이면 식은 8(00001000)로 계산됩니다.</span><span class="sxs-lookup"><span data-stu-id="4eb75-126">If **ReorderPoint** is 10 and **SafetyStockLevel** is 8, the expression evaluates to 8 (00001000).</span></span>  
  
 <span data-ttu-id="4eb75-127">00001010</span><span class="sxs-lookup"><span data-stu-id="4eb75-127">00001010</span></span>  
  
 <span data-ttu-id="4eb75-128">00001000</span><span class="sxs-lookup"><span data-stu-id="4eb75-128">00001000</span></span>  
  
 ----------\-  
  
 <span data-ttu-id="4eb75-129">00001000</span><span class="sxs-lookup"><span data-stu-id="4eb75-129">00001000</span></span>  
  
 <span data-ttu-id="4eb75-130">이 예에서는 두 정수 사이에 비트 AND 연산을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="4eb75-130">This example performs a bitwise AND operation between two integers.</span></span>  
  
```  
3 & 5   
```  
  
 <span data-ttu-id="4eb75-131">식은 1(00000001)로 계산됩니다.</span><span class="sxs-lookup"><span data-stu-id="4eb75-131">The expression evaluates to 1(00000001).</span></span>  
  
 <span data-ttu-id="4eb75-132">00000011</span><span class="sxs-lookup"><span data-stu-id="4eb75-132">00000011</span></span>  
  
 <span data-ttu-id="4eb75-133">00000101</span><span class="sxs-lookup"><span data-stu-id="4eb75-133">00000101</span></span>  
  
 ----------\-  
  
 <span data-ttu-id="4eb75-134">00000001</span><span class="sxs-lookup"><span data-stu-id="4eb75-134">00000001</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4eb75-135">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4eb75-135">See Also</span></span>  
 <span data-ttu-id="4eb75-136">[&&&#40;논리적 AND&#41;&#40;SSIS 식&#41;](logical-and-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="4eb75-136">[&& &#40;Logical AND&#41; &#40;SSIS Expression&#41;](logical-and-ssis-expression.md) </span></span>  
 <span data-ttu-id="4eb75-137">[연산자 우선 순위 및 계산 방향](operator-precedence-and-associativity.md) </span><span class="sxs-lookup"><span data-stu-id="4eb75-137">[Operator Precedence and Associativity](operator-precedence-and-associativity.md) </span></span>  
 [<span data-ttu-id="4eb75-138">연산자&#40;SSIS 식&#41;</span><span class="sxs-lookup"><span data-stu-id="4eb75-138">Operators &#40;SSIS Expression&#41;</span></span>](operators-ssis-expression.md)  
  
  
