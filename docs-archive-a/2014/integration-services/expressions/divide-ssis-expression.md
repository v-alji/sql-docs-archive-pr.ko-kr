---
title: 나누기(SSIS 식) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- / (divide)
- divide operator (/)
ms.assetid: 5bde9223-872d-443e-8a27-57735e1d8f3d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 4541cd4601047770d1bf361077b1c474219e8833
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647758"
---
# <a name="divide-ssis-expression"></a><span data-ttu-id="36c39-102">Divide (SSIS Expression)</span><span class="sxs-lookup"><span data-stu-id="36c39-102">Divide (SSIS Expression)</span></span>
  <span data-ttu-id="36c39-103">첫 번째 숫자 식을 두 번째 숫자 식으로 나눕니다.</span><span class="sxs-lookup"><span data-stu-id="36c39-103">Divides the first numeric expression by the second one.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36c39-104">구문</span><span class="sxs-lookup"><span data-stu-id="36c39-104">Syntax</span></span>  
  
```  
  
dividend / divisor  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="36c39-105">인수</span><span class="sxs-lookup"><span data-stu-id="36c39-105">Arguments</span></span>  
 <span data-ttu-id="36c39-106">*dividend*</span><span class="sxs-lookup"><span data-stu-id="36c39-106">*dividend*</span></span>  
 <span data-ttu-id="36c39-107">나눌 숫자 식입니다.</span><span class="sxs-lookup"><span data-stu-id="36c39-107">Is the numeric expression to divide.</span></span> <span data-ttu-id="36c39-108">*dividend* 는 임의의 유효한 숫자 식일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36c39-108">*dividend* can be any valid numeric expression.</span></span> <span data-ttu-id="36c39-109">자세한 내용은 [Integration Services Data Types](../data-flow/integration-services-data-types.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="36c39-109">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
 <span data-ttu-id="36c39-110">*divisor*</span><span class="sxs-lookup"><span data-stu-id="36c39-110">*divisor*</span></span>  
 <span data-ttu-id="36c39-111">피제수를 나눌 숫자 식입니다.</span><span class="sxs-lookup"><span data-stu-id="36c39-111">Is the numeric expression to divide the dividend by.</span></span> <span data-ttu-id="36c39-112">*divisor* 는 0을 제외한 임의의 유효한 숫자 식일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36c39-112">*divisor* can be any valid numeric expression except zero.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="36c39-113">결과 형식</span><span class="sxs-lookup"><span data-stu-id="36c39-113">Result Types</span></span>  
 <span data-ttu-id="36c39-114">두 인수의 데이터 형식에 따라 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="36c39-114">Determined by data types of the two arguments.</span></span> <span data-ttu-id="36c39-115">자세한 내용은 [Integration Services Data Types in Expressions](integration-services-data-types-in-expressions.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="36c39-115">For more information, see [Integration Services Data Types in Expressions](integration-services-data-types-in-expressions.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="36c39-116">설명</span><span class="sxs-lookup"><span data-stu-id="36c39-116">Remarks</span></span>  
 <span data-ttu-id="36c39-117">두 피연산자 중 하나가 Null이면 결과도 Null입니다.</span><span class="sxs-lookup"><span data-stu-id="36c39-117">If either operand is null, the result is null.</span></span>  
  
 <span data-ttu-id="36c39-118">0으로 나눌 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="36c39-118">Dividing by zero is not legal.</span></span> <span data-ttu-id="36c39-119">*divisor* 하위 식의 계산 방법에 따라 다음 오류 중 하나가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="36c39-119">Depending on how the *divisor* subexpression is evaluated, one of following errors occurs:</span></span>  
  
-   <span data-ttu-id="36c39-120">계산 결과가 0인 *divisor* 하위 식이 상수이면 디자인 타임에 오류가 표시되어 식의 유효성 검사가 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="36c39-120">If the *divisor* subexpression that evaluates to zero is a constant, the error appears at design time, causing the expression to fail validation.</span></span>  
  
-   <span data-ttu-id="36c39-121">계산 결과가 0인 *divisor* 하위 식에 변수가 포함되어 있지만 입력 열이 없으면 해당 식이 속해 있는 구성 요소가 패키지 실행 전에 수행되는 실행 전 유효성 검사에 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="36c39-121">If the *divisor* subexpression that evaluates to zero contains variables, but no input columns, the component to which the expression belongs fails the pre-execution validation that occurs before the package runs.</span></span>  
  
-   <span data-ttu-id="36c39-122">계산 결과가 0인 *divisor* 하위 식에 입력 열이 포함되어 있으면 런타임에 오류가 표시되고 데이터 흐름 구성 요소의 오류 흐름 규칙에 따라 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="36c39-122">If the *divisor* subexpression that evaluates to zero contains input columns, the error appears at run time and is handled according to the error flow rules of the data flow component.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="36c39-123">식 예</span><span class="sxs-lookup"><span data-stu-id="36c39-123">Expression Examples</span></span>  
 <span data-ttu-id="36c39-124">이 예에서는 두 개의 숫자 리터럴을 나눕니다.</span><span class="sxs-lookup"><span data-stu-id="36c39-124">This example divides two numeric literals.</span></span>  
  
```  
25 / 5  
```  
  
 <span data-ttu-id="36c39-125">이 예에서는 **ListPrice** 열의 값을 **StandardCost** 열의 값으로 나눕니다.</span><span class="sxs-lookup"><span data-stu-id="36c39-125">This example divides values in the **ListPrice** column by values in the **StandardCost** column.</span></span>  
  
```  
ListPrice / StandardCost  
```  
  
## <a name="see-also"></a><span data-ttu-id="36c39-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="36c39-126">See Also</span></span>  
 <span data-ttu-id="36c39-127">[연산자 우선 순위 및 계산 방향](operator-precedence-and-associativity.md) </span><span class="sxs-lookup"><span data-stu-id="36c39-127">[Operator Precedence and Associativity](operator-precedence-and-associativity.md) </span></span>  
 [<span data-ttu-id="36c39-128">연산자&#40;SSIS 식&#41;</span><span class="sxs-lookup"><span data-stu-id="36c39-128">Operators &#40;SSIS Expression&#41;</span></span>](operators-ssis-expression.md)  
  
  
