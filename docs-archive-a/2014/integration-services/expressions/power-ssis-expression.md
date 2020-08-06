---
title: POWER(SSIS 식) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- POWER function
ms.assetid: db48ae65-bfa6-4db1-8d3c-d0d4f8a399bc
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e1f5742f482ae52620ec11d95b84cb3d06199fab
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651777"
---
# <a name="power-ssis-expression"></a><span data-ttu-id="4d5e2-102">POWER(SSIS 식)</span><span class="sxs-lookup"><span data-stu-id="4d5e2-102">POWER (SSIS Expression)</span></span>
  <span data-ttu-id="4d5e2-103">숫자 식의 거듭제곱을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="4d5e2-103">Returns the result of raising a numeric expression to a power.</span></span> <span data-ttu-id="4d5e2-104">거듭제곱 매개 변수는 정수여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d5e2-104">The power parameter must evaluate to an integer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d5e2-105">구문</span><span class="sxs-lookup"><span data-stu-id="4d5e2-105">Syntax</span></span>  
  
```  
  
POWER(numeric_expression,power)  
```  
  
## <a name="arguments"></a><span data-ttu-id="4d5e2-106">인수</span><span class="sxs-lookup"><span data-stu-id="4d5e2-106">Arguments</span></span>  
 <span data-ttu-id="4d5e2-107">*numeric_expression*</span><span class="sxs-lookup"><span data-stu-id="4d5e2-107">*numeric_expression*</span></span>  
 <span data-ttu-id="4d5e2-108">유효한 숫자 식입니다.</span><span class="sxs-lookup"><span data-stu-id="4d5e2-108">Is a valid numeric expression.</span></span>  
  
 <span data-ttu-id="4d5e2-109">*power*</span><span class="sxs-lookup"><span data-stu-id="4d5e2-109">*power*</span></span>  
 <span data-ttu-id="4d5e2-110">유효한 숫자 식입니다.</span><span class="sxs-lookup"><span data-stu-id="4d5e2-110">Is a valid numeric expression.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="4d5e2-111">결과 형식</span><span class="sxs-lookup"><span data-stu-id="4d5e2-111">Result Types</span></span>  
 <span data-ttu-id="4d5e2-112">DT_R8</span><span class="sxs-lookup"><span data-stu-id="4d5e2-112">DT_R8</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4d5e2-113">설명</span><span class="sxs-lookup"><span data-stu-id="4d5e2-113">Remarks</span></span>  
 <span data-ttu-id="4d5e2-114">*numeric_expression* 및 *power* 인수는 거듭제곱을 계산하기 전에 DT_R8 데이터 형식으로 캐스팅됩니다.</span><span class="sxs-lookup"><span data-stu-id="4d5e2-114">The *numeric_expression* and *power* arguments are cast to the DT_R8 data type before the power is computed.</span></span> <span data-ttu-id="4d5e2-115">자세한 내용은 [Integration Services Data Types](../data-flow/integration-services-data-types.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4d5e2-115">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
 <span data-ttu-id="4d5e2-116">*numeric_expression* 이 0이고 *power* 가 음수이면 식 계산기는 오류를 반환하고 반환 결과를 Null로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="4d5e2-116">If *numeric_expression* evaluates to zero and *power* is negative, the expression evaluator returns an error and sets the return result to null.</span></span>  
  
 <span data-ttu-id="4d5e2-117">*numeric_expression* 또는 *power* 의 계산 결과를 알 수 없는 경우 반환 결과는 Null입니다.</span><span class="sxs-lookup"><span data-stu-id="4d5e2-117">If *numeric_expression* or *power* evaluate to indeterminate results, the return result is null.</span></span>  
  
 <span data-ttu-id="4d5e2-118">*power* 인수는 분수일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4d5e2-118">The *power* argument can be a fraction.</span></span> <span data-ttu-id="4d5e2-119">예를 들어 값 0.5를 거듭제곱으로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4d5e2-119">For example, you can use the value 0.5 as the power.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="4d5e2-120">식 예</span><span class="sxs-lookup"><span data-stu-id="4d5e2-120">Expression Examples</span></span>  
 <span data-ttu-id="4d5e2-121">이 예에서는 숫자 리터럴을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="4d5e2-121">This example uses a numeric literal.</span></span> <span data-ttu-id="4d5e2-122">이 함수는 4의 3 거듭제곱을 계산하여 64를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="4d5e2-122">The function raises 4 to the power of 3 and returns 64.</span></span>  
  
```  
POWER(4,3)  
```  
  
 <span data-ttu-id="4d5e2-123">이 예에서는 **Length** 열과 **DimensionCount** 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="4d5e2-123">This example uses the **Length** column and the **DimensionCount** variable.</span></span> <span data-ttu-id="4d5e2-124">**Length** 가 8이고 **DimensionCount** 가 2이면 반환 결과는 64입니다.</span><span class="sxs-lookup"><span data-stu-id="4d5e2-124">If **Length** is 8, and **DimensionCount** is 2, the return result is 64.</span></span>  
  
```  
POWER(Length, @DimensionCount)   
```  
  
## <a name="see-also"></a><span data-ttu-id="4d5e2-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4d5e2-125">See Also</span></span>  
 [<span data-ttu-id="4d5e2-126">함수&#40;SSIS 식&#41;</span><span class="sxs-lookup"><span data-stu-id="4d5e2-126">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
