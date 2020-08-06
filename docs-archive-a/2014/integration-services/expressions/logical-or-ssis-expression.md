---
title: '||(논리적 OR)(SSIS 식) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- OR operator
- logical OR (||)
- '|| (logical OR)'
ms.assetid: a3c07c09-f121-4187-9617-b01adcf843c4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 72d4a1c7b54856675f0faa7f5f58452cb8bca450
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729671"
---
# <a name="-logical-or-ssis-expression"></a><span data-ttu-id="dcfd4-102">||(논리적 OR)(SSIS 식)</span><span class="sxs-lookup"><span data-stu-id="dcfd4-102">|| (Logical OR) (SSIS Expression)</span></span>
  <span data-ttu-id="dcfd4-103">논리적 OR 연산을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="dcfd4-103">Performs a logical OR operation.</span></span> <span data-ttu-id="dcfd4-104">두 조건 중 하나 또는 둘 다가 TRUE이면 식도 TRUE가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dcfd4-104">The expression evaluates to TRUE if one or both conditions are TRUE.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dcfd4-105">구문</span><span class="sxs-lookup"><span data-stu-id="dcfd4-105">Syntax</span></span>  
  
```  
  
boolean_expression1 || boolean_expression2  
```  
  
## <a name="arguments"></a><span data-ttu-id="dcfd4-106">인수</span><span class="sxs-lookup"><span data-stu-id="dcfd4-106">Arguments</span></span>  
 <span data-ttu-id="dcfd4-107">*boolean_expression1, boolean_expression2*</span><span class="sxs-lookup"><span data-stu-id="dcfd4-107">*boolean_expression1, boolean_expression2*</span></span>  
 <span data-ttu-id="dcfd4-108">TRUE, FALSE 또는 NULL로 계산되는 임의의 유효한 식입니다.</span><span class="sxs-lookup"><span data-stu-id="dcfd4-108">Is any valid expression that evaluates to TRUE, FALSE, or NULL.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="dcfd4-109">결과 형식</span><span class="sxs-lookup"><span data-stu-id="dcfd4-109">Result Types</span></span>  
 <span data-ttu-id="dcfd4-110">DT_BOOL</span><span class="sxs-lookup"><span data-stu-id="dcfd4-110">DT_BOOL</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dcfd4-111">설명</span><span class="sxs-lookup"><span data-stu-id="dcfd4-111">Remarks</span></span>  
 <span data-ttu-id="dcfd4-112">다음 표에서는 || 연산자의 결과를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="dcfd4-112">The following table shows the result of the || operator.</span></span>  
  
|<span data-ttu-id="dcfd4-113">결과</span><span class="sxs-lookup"><span data-stu-id="dcfd4-113">Result</span></span>|<span data-ttu-id="dcfd4-114">식</span><span class="sxs-lookup"><span data-stu-id="dcfd4-114">Expression</span></span>|<span data-ttu-id="dcfd4-115">식</span><span class="sxs-lookup"><span data-stu-id="dcfd4-115">Expression</span></span>|  
|------------|----------------|----------------|  
|<span data-ttu-id="dcfd4-116">TRUE</span><span class="sxs-lookup"><span data-stu-id="dcfd4-116">TRUE</span></span>|<span data-ttu-id="dcfd4-117">TRUE</span><span class="sxs-lookup"><span data-stu-id="dcfd4-117">TRUE</span></span>|<span data-ttu-id="dcfd4-118">TRUE</span><span class="sxs-lookup"><span data-stu-id="dcfd4-118">TRUE</span></span>|  
|<span data-ttu-id="dcfd4-119">TRUE</span><span class="sxs-lookup"><span data-stu-id="dcfd4-119">TRUE</span></span>|<span data-ttu-id="dcfd4-120">TRUE</span><span class="sxs-lookup"><span data-stu-id="dcfd4-120">TRUE</span></span>|<span data-ttu-id="dcfd4-121">FALSE</span><span class="sxs-lookup"><span data-stu-id="dcfd4-121">FALSE</span></span>|  
|<span data-ttu-id="dcfd4-122">FALSE</span><span class="sxs-lookup"><span data-stu-id="dcfd4-122">FALSE</span></span>|<span data-ttu-id="dcfd4-123">FALSE</span><span class="sxs-lookup"><span data-stu-id="dcfd4-123">FALSE</span></span>|<span data-ttu-id="dcfd4-124">FALSE</span><span class="sxs-lookup"><span data-stu-id="dcfd4-124">FALSE</span></span>|  
|<span data-ttu-id="dcfd4-125">NULL</span><span class="sxs-lookup"><span data-stu-id="dcfd4-125">NULL</span></span>|<span data-ttu-id="dcfd4-126">NULL</span><span class="sxs-lookup"><span data-stu-id="dcfd4-126">NULL</span></span>|<span data-ttu-id="dcfd4-127">NULL</span><span class="sxs-lookup"><span data-stu-id="dcfd4-127">NULL</span></span>|  
|<span data-ttu-id="dcfd4-128">TRUE</span><span class="sxs-lookup"><span data-stu-id="dcfd4-128">TRUE</span></span>|<span data-ttu-id="dcfd4-129">NULL</span><span class="sxs-lookup"><span data-stu-id="dcfd4-129">NULL</span></span>|<span data-ttu-id="dcfd4-130">TRUE</span><span class="sxs-lookup"><span data-stu-id="dcfd4-130">TRUE</span></span>|  
|<span data-ttu-id="dcfd4-131">NULL</span><span class="sxs-lookup"><span data-stu-id="dcfd4-131">NULL</span></span>|<span data-ttu-id="dcfd4-132">NULL</span><span class="sxs-lookup"><span data-stu-id="dcfd4-132">NULL</span></span>|<span data-ttu-id="dcfd4-133">FALSE</span><span class="sxs-lookup"><span data-stu-id="dcfd4-133">FALSE</span></span>|  
  
## <a name="ssis-expression-examples"></a><span data-ttu-id="dcfd4-134">SSIS 식 예</span><span class="sxs-lookup"><span data-stu-id="dcfd4-134">SSIS Expression Examples</span></span>  
 <span data-ttu-id="dcfd4-135">이 예에서는 **StandardCost** 열과 **ListPrice** 열을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="dcfd4-135">This example uses the **StandardCost** and **ListPrice** columns.</span></span> <span data-ttu-id="dcfd4-136">**StandardCost** 열의 값이 300보다 작거나 **ListPrice** 열의 값이 500보다 크면 TRUE가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dcfd4-136">The example evaluates to TRUE if the value of the **StandardCost** column is less than 300 or the **ListPrice** column is greater than 500.</span></span>  
  
```  
StandardCost < 300 || ListPrice > 500  
```  
  
 <span data-ttu-id="dcfd4-137">이 예에서는 숫자 리터럴 대신 변수 **SPrice** 와 **LPrice** 를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="dcfd4-137">This example uses the variables **SPrice** and **LPrice** instead of numeric literals.</span></span>  
  
```  
StandardCost < @SPrice || ListPrice > @LPrice  
```  
  
## <a name="see-also"></a><span data-ttu-id="dcfd4-138">참고 항목</span><span class="sxs-lookup"><span data-stu-id="dcfd4-138">See Also</span></span>  
 <span data-ttu-id="dcfd4-139">[&#124;&#40;포괄적 비트 OR&#41;&#40;SSIS 식&#41;](bitwise-inclusive-or-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="dcfd4-139">[&#124; &#40;Bitwise Inclusive OR&#41; &#40;SSIS Expression&#41;](bitwise-inclusive-or-ssis-expression.md) </span></span>  
 <span data-ttu-id="dcfd4-140">[^&#40;배타적 비트 OR&#41;&#40;SSIS 식&#41;](bitwise-exclusive-or-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="dcfd4-140">[^ &#40;Bitwise Exclusive OR&#41; &#40;SSIS Expression&#41;](bitwise-exclusive-or-ssis-expression.md) </span></span>  
 <span data-ttu-id="dcfd4-141">[연산자 우선 순위 및 계산 방향](operator-precedence-and-associativity.md) </span><span class="sxs-lookup"><span data-stu-id="dcfd4-141">[Operator Precedence and Associativity](operator-precedence-and-associativity.md) </span></span>  
 [<span data-ttu-id="dcfd4-142">연산자&#40;SSIS 식&#41;</span><span class="sxs-lookup"><span data-stu-id="dcfd4-142">Operators &#40;SSIS Expression&#41;</span></span>](operators-ssis-expression.md)  
  
  
