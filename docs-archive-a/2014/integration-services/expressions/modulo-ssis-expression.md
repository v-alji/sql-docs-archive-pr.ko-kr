---
title: (모듈로)(SSIS 식) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- '% (modulo operator)'
- remainder of division operation
- modulo operator (%)
ms.assetid: e2920821-2f5b-4c76-8db8-8b9eddf4606f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 2e23152fca9c9f2c7c3ac11490a56b03d1a1f9dd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650196"
---
# <a name="modulo-ssis-expression"></a><span data-ttu-id="4b80c-102">(모듈로)(SSIS 식)</span><span class="sxs-lookup"><span data-stu-id="4b80c-102">(Modulo) (SSIS Expression)</span></span>
  <span data-ttu-id="4b80c-103">첫 번째 숫자 식을 두 번째 식으로 나눈 다음 나머지의 정수 부분을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="4b80c-103">Provides the integer remainder after dividing the first numeric expression by the second one.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b80c-104">구문</span><span class="sxs-lookup"><span data-stu-id="4b80c-104">Syntax</span></span>  
  
```  
  
dividend % divisor  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="4b80c-105">인수</span><span class="sxs-lookup"><span data-stu-id="4b80c-105">Arguments</span></span>  
 <span data-ttu-id="4b80c-106">*dividend*</span><span class="sxs-lookup"><span data-stu-id="4b80c-106">*dividend*</span></span>  
 <span data-ttu-id="4b80c-107">나눌 숫자 식입니다.</span><span class="sxs-lookup"><span data-stu-id="4b80c-107">Is the numeric expression to divide.</span></span> <span data-ttu-id="4b80c-108">*dividend* 는 임의의 유효한 숫자 식일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4b80c-108">*dividend* can be any valid numeric expression.</span></span> <span data-ttu-id="4b80c-109">자세한 내용은 [Integration Services 데이터 형식](../data-flow/integration-services-data-types.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4b80c-109">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md)</span></span>  
  
 <span data-ttu-id="4b80c-110">*divisor*</span><span class="sxs-lookup"><span data-stu-id="4b80c-110">*divisor*</span></span>  
 <span data-ttu-id="4b80c-111">피제수를 나눌 숫자 식입니다.</span><span class="sxs-lookup"><span data-stu-id="4b80c-111">Is the numeric expression to divide the dividend by.</span></span> <span data-ttu-id="4b80c-112">*divisor* 는 0을 제외한 임의의 유효한 숫자 식일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4b80c-112">*divisor* can be any valid numeric expression except zero.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="4b80c-113">결과 형식</span><span class="sxs-lookup"><span data-stu-id="4b80c-113">Result Types</span></span>  
 <span data-ttu-id="4b80c-114">두 인수의 데이터 형식에 따라 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="4b80c-114">Determined by data types of the two arguments.</span></span> <span data-ttu-id="4b80c-115">자세한 내용은 [Integration Services Data Types in Expressions](integration-services-data-types-in-expressions.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4b80c-115">For more information, see [Integration Services Data Types in Expressions](integration-services-data-types-in-expressions.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4b80c-116">설명</span><span class="sxs-lookup"><span data-stu-id="4b80c-116">Remarks</span></span>  
 <span data-ttu-id="4b80c-117">두 식이 모두 부호 있는 정수 또는 부호 없는 정수 데이터 형식이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4b80c-117">Both expressions must evaluate to signed or unsigned integer data types.</span></span>  
  
 <span data-ttu-id="4b80c-118">두 피연산자 중 하나가 Null이면 결과도 Null입니다.</span><span class="sxs-lookup"><span data-stu-id="4b80c-118">If either operand is null, the result is null.</span></span>  
  
 <span data-ttu-id="4b80c-119">모듈로 0은 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4b80c-119">Modulo zero is not legal.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="4b80c-120">식 예</span><span class="sxs-lookup"><span data-stu-id="4b80c-120">Expression Examples</span></span>  
 <span data-ttu-id="4b80c-121">이 예에서는 두 개의 숫자 리터럴에서 모듈러스를 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="4b80c-121">This example computes the modulus from two numeric literals.</span></span> <span data-ttu-id="4b80c-122">결과는 3입니다.</span><span class="sxs-lookup"><span data-stu-id="4b80c-122">The result is 3.</span></span>  
  
```  
42 % 13  
```  
  
 <span data-ttu-id="4b80c-123">이 예에서는 **SalesQuota** 열과 하나의 숫자 리터럴에서 모듈러스를 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="4b80c-123">This example computes the modulus from the **SalesQuota** column and a numeric literal.</span></span>  
  
```  
SalesQuota % 12  
```  
  
 <span data-ttu-id="4b80c-124">이 예에서는 두 개의 숫자 변수 **Sales$** 와 **Month**에서 모듈러스를 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="4b80c-124">This example computes the modulus from two numeric variables **Sales$** and **Month**.</span></span> <span data-ttu-id="4b80c-125">변수 **Sales$** 는 이름에 $ 문자가 포함되어 있으므로 대괄호로 묶어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4b80c-125">The variable **Sales$** must be enclosed in brackets because the name includes the $ character.</span></span> <span data-ttu-id="4b80c-126">자세한 내용은 [식별자&#40;SSIS&#41;](identifiers-ssis.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4b80c-126">For more information, see [Identifiers &#40;SSIS&#41;](identifiers-ssis.md).</span></span>  
  
```  
@[Sales$] % @Month  
```  
  
 <span data-ttu-id="4b80c-127">이 예에서는 모듈로 연산자를 사용하여 **Value** 변수가 짝수 또는 홀수인지를 확인하고 조건부 연산자를 사용하여 결과를 설명하는 문자열을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="4b80c-127">This example uses the modulo operator to determine if the value of the **Value** variable is even or odd, and uses the conditional operator to return a string that describes the result.</span></span> <span data-ttu-id="4b80c-128">자세한 내용은 [? :&#40;조건&#41;&#40;SSIS 식&#41;](conditional-ssis-expression.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4b80c-128">For more information, see [? : &#40;Conditional&#41; &#40;SSIS Expression&#41;](conditional-ssis-expression.md).</span></span>  
  
```  
@Value % 2 == 0? "even":"odd"  
```  
  
## <a name="see-also"></a><span data-ttu-id="4b80c-129">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4b80c-129">See Also</span></span>  
 <span data-ttu-id="4b80c-130">[연산자 우선 순위 및 계산 방향](operator-precedence-and-associativity.md) </span><span class="sxs-lookup"><span data-stu-id="4b80c-130">[Operator Precedence and Associativity](operator-precedence-and-associativity.md) </span></span>  
 [<span data-ttu-id="4b80c-131">연산자&#40;SSIS 식&#41;</span><span class="sxs-lookup"><span data-stu-id="4b80c-131">Operators &#40;SSIS Expression&#41;</span></span>](operators-ssis-expression.md)  
  
  
