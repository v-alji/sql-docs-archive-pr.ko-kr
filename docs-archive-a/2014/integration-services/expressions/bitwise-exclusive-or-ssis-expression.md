---
title: ^(배타적 비트 OR)(SSIS 식) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- ^ (bitwise exclusive OR operator)
- bitwise exclusive OR (^)
ms.assetid: 6ac53cab-29c4-4835-9f87-371b058b2f38
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d86c3d810e9e5572af93c97f82c2275db2c979b0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652969"
---
# <a name="-bitwise-exclusive-or-ssis-expression"></a><span data-ttu-id="90a3a-102">^(배타적 비트 OR)(SSIS 식)</span><span class="sxs-lookup"><span data-stu-id="90a3a-102">^ (Bitwise Exclusive OR) (SSIS Expression)</span></span>
  <span data-ttu-id="90a3a-103">두 정수 값의 배타적 비트 OR 연산을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="90a3a-103">Performs a bitwise exclusive OR operation of two integer values.</span></span> <span data-ttu-id="90a3a-104">그런 후 첫 번째 피연산자의 각 비트를 두 번째 피연산자의 해당 비트와 비교합니다.</span><span class="sxs-lookup"><span data-stu-id="90a3a-104">It compares each bit of its first operand to the corresponding bit of its second operand.</span></span> <span data-ttu-id="90a3a-105">두 비트 중 하나가 0이고 다른 비트가 1이면 해당 결과 비트는 1로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="90a3a-105">If one bit is 0 and the other bit is 1, the corresponding result bit is set to 1.</span></span> <span data-ttu-id="90a3a-106">두 비트가 모두 0 또는 1이면 해당 결과 비트는 0으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="90a3a-106">If both bits are 0 or both bits are 1, the corresponding result bit is set to 0.</span></span>  
  
 <span data-ttu-id="90a3a-107">두 조건이 모두 부호 있는 정수 데이터 형식이거나 두 조건이 모두 부호 없는 정수 데이터 형식이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="90a3a-107">Both conditions must be a signed integer data type or both conditions must be an unsigned integer data type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90a3a-108">구문</span><span class="sxs-lookup"><span data-stu-id="90a3a-108">Syntax</span></span>  
  
```  
  
integer_expression1 ^ integer_expression2  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="90a3a-109">인수</span><span class="sxs-lookup"><span data-stu-id="90a3a-109">Arguments</span></span>  
 <span data-ttu-id="90a3a-110">*integer_expression1, integer_expression2*</span><span class="sxs-lookup"><span data-stu-id="90a3a-110">*integer_expression1, integer_expression2*</span></span>  
 <span data-ttu-id="90a3a-111">부호가 있거나 부호가 없는 정수 데이터 형식의 유효한 식입니다.</span><span class="sxs-lookup"><span data-stu-id="90a3a-111">Is any valid expression of a signed or unsigned integer data type.</span></span> <span data-ttu-id="90a3a-112">자세한 내용은 [Integration Services Data Types](../data-flow/integration-services-data-types.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="90a3a-112">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="90a3a-113">결과 형식</span><span class="sxs-lookup"><span data-stu-id="90a3a-113">Result Types</span></span>  
 <span data-ttu-id="90a3a-114">두 인수의 데이터 형식에 따라 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="90a3a-114">Determined by data types of the two arguments.</span></span> <span data-ttu-id="90a3a-115">자세한 내용은 [Integration Services Data Types in Expressions](integration-services-data-types-in-expressions.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="90a3a-115">For more information, see [Integration Services Data Types in Expressions](integration-services-data-types-in-expressions.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="90a3a-116">설명</span><span class="sxs-lookup"><span data-stu-id="90a3a-116">Remarks</span></span>  
 <span data-ttu-id="90a3a-117">둘 중 한 조건이 Null이면 식 결과도 Null입니다.</span><span class="sxs-lookup"><span data-stu-id="90a3a-117">If either condition is null, the expression result is null.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="90a3a-118">식 예</span><span class="sxs-lookup"><span data-stu-id="90a3a-118">Expression Examples</span></span>  
 <span data-ttu-id="90a3a-119">이 예에서는 변수 **NumberA** 와 **NumberB**사이에 배타적 비트 OR 연산을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="90a3a-119">This example performs a bitwise exclusive OR operation between variables **NumberA** and **NumberB**.</span></span> <span data-ttu-id="90a3a-120">**NumberA** 에는 3(00000011)이 포함되고 **NumberB** 에는 7(00000111)이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="90a3a-120">**NumberA** contains 3 (00000011) and **NumberB** contains 7 (00000111).</span></span>  
  
```  
@NumberA ^ @NumberB  
```  
  
 <span data-ttu-id="90a3a-121">식은 4(00000100)로 계산됩니다.</span><span class="sxs-lookup"><span data-stu-id="90a3a-121">The expression evaluates to 4 (00000100).</span></span>  
  
 <span data-ttu-id="90a3a-122">00000011</span><span class="sxs-lookup"><span data-stu-id="90a3a-122">00000011</span></span>  
  
 <span data-ttu-id="90a3a-123">00000111</span><span class="sxs-lookup"><span data-stu-id="90a3a-123">00000111</span></span>  
  
 ----------\-  
  
 <span data-ttu-id="90a3a-124">00000100</span><span class="sxs-lookup"><span data-stu-id="90a3a-124">00000100</span></span>  
  
 <span data-ttu-id="90a3a-125">이 예에서는 **ReorderPoint** 열과 **SafetyStockLevel** 열 사이에 배타적 비트 OR 연산을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="90a3a-125">This example performs a bitwise exclusive OR operation between the **ReorderPoint** and **SafetyStockLevel** columns.</span></span>  
  
```  
ReorderPoint ^ SafetyStockLevel  
```  
  
 <span data-ttu-id="90a3a-126">**ReorderPoint** 가 10이고 **SafetyStockLevel** 이 8이면 식은 2(00000010)로 계산됩니다.</span><span class="sxs-lookup"><span data-stu-id="90a3a-126">If **ReorderPoint** is 10 and **SafetyStockLevel** is 8, the expression evaluates to 2 (00000010).</span></span>  
  
 <span data-ttu-id="90a3a-127">00001010</span><span class="sxs-lookup"><span data-stu-id="90a3a-127">00001010</span></span>  
  
 <span data-ttu-id="90a3a-128">00001000</span><span class="sxs-lookup"><span data-stu-id="90a3a-128">00001000</span></span>  
  
 ----------\-  
  
 <span data-ttu-id="90a3a-129">00000010</span><span class="sxs-lookup"><span data-stu-id="90a3a-129">00000010</span></span>  
  
 <span data-ttu-id="90a3a-130">이 예에서는 두 정수 사이에 배타적 비트 OR 연산을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="90a3a-130">This example performs a bitwise exclusive OR operation between two integers.</span></span>  
  
```  
3 ^ 5   
```  
  
 <span data-ttu-id="90a3a-131">식은 6(00000110)으로 계산됩니다.</span><span class="sxs-lookup"><span data-stu-id="90a3a-131">The expression evaluates to 6 (00000110).</span></span>  
  
 <span data-ttu-id="90a3a-132">00000011</span><span class="sxs-lookup"><span data-stu-id="90a3a-132">00000011</span></span>  
  
 <span data-ttu-id="90a3a-133">00000101</span><span class="sxs-lookup"><span data-stu-id="90a3a-133">00000101</span></span>  
  
 ----------\-  
  
 <span data-ttu-id="90a3a-134">00000110</span><span class="sxs-lookup"><span data-stu-id="90a3a-134">00000110</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90a3a-135">참고 항목</span><span class="sxs-lookup"><span data-stu-id="90a3a-135">See Also</span></span>  
 <span data-ttu-id="90a3a-136">[&#124;&#124;&#40;논리적 OR&#41;&#40;SSIS 식&#41;](logical-or-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="90a3a-136">[&#124;&#124; &#40;Logical OR&#41; &#40;SSIS Expression&#41;](logical-or-ssis-expression.md) </span></span>  
 <span data-ttu-id="90a3a-137">[&#124;&#40;포괄적 비트 OR&#41;&#40;SSIS 식&#41;](bitwise-inclusive-or-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="90a3a-137">[&#124; &#40;Bitwise Inclusive OR&#41; &#40;SSIS Expression&#41;](bitwise-inclusive-or-ssis-expression.md) </span></span>  
 <span data-ttu-id="90a3a-138">[연산자 우선 순위 및 계산 방향](operator-precedence-and-associativity.md) </span><span class="sxs-lookup"><span data-stu-id="90a3a-138">[Operator Precedence and Associativity](operator-precedence-and-associativity.md) </span></span>  
 [<span data-ttu-id="90a3a-139">연산자&#40;SSIS 식&#41;</span><span class="sxs-lookup"><span data-stu-id="90a3a-139">Operators &#40;SSIS Expression&#41;</span></span>](operators-ssis-expression.md)  
  
  
