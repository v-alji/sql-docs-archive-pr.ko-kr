---
title: '&amp;&amp; (논리적 AND)(SSIS 식) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- '&& (logical AND)'
- AND, logical AND
- logical AND (&&)
ms.assetid: a8cb3517-d5d1-4861-9f04-905c719185ff
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8d973d7d4e86f88f7ae88c820ed4e4a5c1ce526f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729668"
---
# <a name="ampamp-logical-and-ssis-expression"></a><span data-ttu-id="789e6-102">&amp;&amp; (논리적 AND)(SSIS 식)</span><span class="sxs-lookup"><span data-stu-id="789e6-102">&amp;&amp; (Logical AND) (SSIS Expression)</span></span>
  <span data-ttu-id="789e6-103">논리적 AND 연산을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="789e6-103">Performs a logical AND operation.</span></span> <span data-ttu-id="789e6-104">모든 조건이 TRUE이면 식도 TRUE가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="789e6-104">The expression evaluates to TRUE if all conditions are TRUE.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="789e6-105">구문</span><span class="sxs-lookup"><span data-stu-id="789e6-105">Syntax</span></span>  
  
```  
  
boolean_expression1 && boolean_expression2  
```  
  
## <a name="arguments"></a><span data-ttu-id="789e6-106">인수</span><span class="sxs-lookup"><span data-stu-id="789e6-106">Arguments</span></span>  
 <span data-ttu-id="789e6-107">*boolean _expression1, boolean_expression2*</span><span class="sxs-lookup"><span data-stu-id="789e6-107">*boolean _expression1, boolean_expression2*</span></span>  
 <span data-ttu-id="789e6-108">TRUE, FALSE 또는 NULL로 계산되는 임의의 유효한 식입니다.</span><span class="sxs-lookup"><span data-stu-id="789e6-108">Is any valid expression that evaluates to TRUE, FALSE, or NULL.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="789e6-109">결과 형식</span><span class="sxs-lookup"><span data-stu-id="789e6-109">Result Types</span></span>  
 <span data-ttu-id="789e6-110">DT_BOOL</span><span class="sxs-lookup"><span data-stu-id="789e6-110">DT_BOOL</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="789e6-111">설명</span><span class="sxs-lookup"><span data-stu-id="789e6-111">Remarks</span></span>  
 <span data-ttu-id="789e6-112">다음 표에서는 && 연산자의 결과를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="789e6-112">The following table shows the result of the && operator.</span></span>  
  
|<span data-ttu-id="789e6-113">결과</span><span class="sxs-lookup"><span data-stu-id="789e6-113">Result</span></span>|<span data-ttu-id="789e6-114">식</span><span class="sxs-lookup"><span data-stu-id="789e6-114">Expression</span></span>|<span data-ttu-id="789e6-115">식</span><span class="sxs-lookup"><span data-stu-id="789e6-115">Expression</span></span>|  
|------------|----------------|----------------|  
|<span data-ttu-id="789e6-116">TRUE</span><span class="sxs-lookup"><span data-stu-id="789e6-116">TRUE</span></span>|<span data-ttu-id="789e6-117">TRUE</span><span class="sxs-lookup"><span data-stu-id="789e6-117">TRUE</span></span>|<span data-ttu-id="789e6-118">TRUE</span><span class="sxs-lookup"><span data-stu-id="789e6-118">TRUE</span></span>|  
|<span data-ttu-id="789e6-119">FALSE</span><span class="sxs-lookup"><span data-stu-id="789e6-119">FALSE</span></span>|<span data-ttu-id="789e6-120">TRUE</span><span class="sxs-lookup"><span data-stu-id="789e6-120">TRUE</span></span>|<span data-ttu-id="789e6-121">FALSE</span><span class="sxs-lookup"><span data-stu-id="789e6-121">FALSE</span></span>|  
|<span data-ttu-id="789e6-122">FALSE</span><span class="sxs-lookup"><span data-stu-id="789e6-122">FALSE</span></span>|<span data-ttu-id="789e6-123">FALSE</span><span class="sxs-lookup"><span data-stu-id="789e6-123">FALSE</span></span>|<span data-ttu-id="789e6-124">FALSE</span><span class="sxs-lookup"><span data-stu-id="789e6-124">FALSE</span></span>|  
|<span data-ttu-id="789e6-125">NULL</span><span class="sxs-lookup"><span data-stu-id="789e6-125">NULL</span></span>|<span data-ttu-id="789e6-126">NULL</span><span class="sxs-lookup"><span data-stu-id="789e6-126">NULL</span></span>|<span data-ttu-id="789e6-127">NULL</span><span class="sxs-lookup"><span data-stu-id="789e6-127">NULL</span></span>|  
|<span data-ttu-id="789e6-128">NULL</span><span class="sxs-lookup"><span data-stu-id="789e6-128">NULL</span></span>|<span data-ttu-id="789e6-129">NULL</span><span class="sxs-lookup"><span data-stu-id="789e6-129">NULL</span></span>|<span data-ttu-id="789e6-130">TRUE</span><span class="sxs-lookup"><span data-stu-id="789e6-130">TRUE</span></span>|  
|<span data-ttu-id="789e6-131">FALSE</span><span class="sxs-lookup"><span data-stu-id="789e6-131">FALSE</span></span>|<span data-ttu-id="789e6-132">NULL</span><span class="sxs-lookup"><span data-stu-id="789e6-132">NULL</span></span>|<span data-ttu-id="789e6-133">FALSE</span><span class="sxs-lookup"><span data-stu-id="789e6-133">FALSE</span></span>|  
  
## <a name="expression-examples"></a><span data-ttu-id="789e6-134">식 예</span><span class="sxs-lookup"><span data-stu-id="789e6-134">Expression Examples</span></span>  
 <span data-ttu-id="789e6-135">이 예에서는 **StandardCost** 열과 **ListPrice** 열을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="789e6-135">This example uses the **StandardCost** and the **ListPrice** columns.</span></span> <span data-ttu-id="789e6-136">**StandardCost** 열의 값이 300보다 작고 **ListPrice** 열의 값이 500보다 크면 TRUE가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="789e6-136">The example evaluates to TRUE if the value of the **StandardCost** column is less than 300 and the **ListPrice** column is greater than 500.</span></span>  
  
```  
StandardCost < 300 && ListPrice > 500  
```  
  
 <span data-ttu-id="789e6-137">이 예에서는 리터럴 대신 변수 **SPrice** 와 **LPrice** 를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="789e6-137">This example uses the variables **SPrice** and **LPrice** instead of literals.</span></span>  
  
```  
StandardCost < @SPrice && ListPrice > @LPrice  
```  
  
## <a name="see-also"></a><span data-ttu-id="789e6-138">참고 항목</span><span class="sxs-lookup"><span data-stu-id="789e6-138">See Also</span></span>  
 <span data-ttu-id="789e6-139">[&&#40;비트 AND&#41;&#40;SSIS 식&#41;](bitwise-and-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="789e6-139">[& &#40;Bitwise AND&#41; &#40;SSIS Expression&#41;](bitwise-and-ssis-expression.md) </span></span>  
 <span data-ttu-id="789e6-140">[연산자 우선 순위 및 계산 방향](operator-precedence-and-associativity.md) </span><span class="sxs-lookup"><span data-stu-id="789e6-140">[Operator Precedence and Associativity](operator-precedence-and-associativity.md) </span></span>  
 [<span data-ttu-id="789e6-141">연산자&#40;SSIS 식&#41;</span><span class="sxs-lookup"><span data-stu-id="789e6-141">Operators &#40;SSIS Expression&#41;</span></span>](operators-ssis-expression.md)  
  
  
