---
title: SQRT(SSIS 식) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- SQRT function
- square root of given expression
ms.assetid: 54a75389-c501-4e22-87b8-905f66d6a3a5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9efa3f8da2e5280692aa65a25610211aba2fa40f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732792"
---
# <a name="sqrt-ssis-expression"></a><span data-ttu-id="e5c5d-102">SQRT(SSIS 식)</span><span class="sxs-lookup"><span data-stu-id="e5c5d-102">SQRT (SSIS Expression)</span></span>
  <span data-ttu-id="e5c5d-103">숫자 식의 제곱근을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="e5c5d-103">Returns the square root of a numeric expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5c5d-104">구문</span><span class="sxs-lookup"><span data-stu-id="e5c5d-104">Syntax</span></span>  
  
```  
  
SQRT(numeric_expression)  
```  
  
## <a name="arguments"></a><span data-ttu-id="e5c5d-105">인수</span><span class="sxs-lookup"><span data-stu-id="e5c5d-105">Arguments</span></span>  
 <span data-ttu-id="e5c5d-106">*numeric_expression*</span><span class="sxs-lookup"><span data-stu-id="e5c5d-106">*numeric_expression*</span></span>  
 <span data-ttu-id="e5c5d-107">임의의 숫자 데이터 형식을 갖는 숫자 식입니다.</span><span class="sxs-lookup"><span data-stu-id="e5c5d-107">Is a numeric expression of any numeric data type.</span></span> <span data-ttu-id="e5c5d-108">자세한 내용은 [Integration Services Data Types](../data-flow/integration-services-data-types.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e5c5d-108">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="e5c5d-109">결과 형식</span><span class="sxs-lookup"><span data-stu-id="e5c5d-109">Result Types</span></span>  
 <span data-ttu-id="e5c5d-110">DT_R8</span><span class="sxs-lookup"><span data-stu-id="e5c5d-110">DT_R8</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e5c5d-111">설명</span><span class="sxs-lookup"><span data-stu-id="e5c5d-111">Remarks</span></span>  
 <span data-ttu-id="e5c5d-112">인수가 Null이면 SQRT 결과도 Null입니다.</span><span class="sxs-lookup"><span data-stu-id="e5c5d-112">SQRT returns a null result if the argument is null.</span></span>  
  
 <span data-ttu-id="e5c5d-113">인수가 음수 값이면 SQRT가 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="e5c5d-113">SQRT fails if the argument is a negative value.</span></span>  
  
 <span data-ttu-id="e5c5d-114">인수는 제곱근 연산 전에 DT_R8 데이터 형식으로 캐스팅됩니다.</span><span class="sxs-lookup"><span data-stu-id="e5c5d-114">The argument is cast to the DT_R8 data type before the square root operation.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="e5c5d-115">식 예</span><span class="sxs-lookup"><span data-stu-id="e5c5d-115">Expression Examples</span></span>  
 <span data-ttu-id="e5c5d-116">이 예에서는 숫자 리터럴의 제곱근을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="e5c5d-116">This example returns the square root of a numeric literal.</span></span> <span data-ttu-id="e5c5d-117">반환 결과는 12입니다.</span><span class="sxs-lookup"><span data-stu-id="e5c5d-117">The return result is 12.</span></span>  
  
```  
SQRT(144)  
```  
  
 <span data-ttu-id="e5c5d-118">이 예에서는 **Value1** 열과 **Value2** 열의 값을 뺀 결과인 식의 제곱근을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="e5c5d-118">This example returns the square root of an expression, the result of subtracting values in the **Value1** and **Value2** columns.</span></span>  
  
```  
SQRT(Value1 - Value2)  
```  
  
 <span data-ttu-id="e5c5d-119">이 예에서는 두 변수에 SQUARE 함수를 적용한 후 합계의 제곱근을 계산하여 삼각형의 3번째 변의 길이를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="e5c5d-119">This example returns the length of the third side of a right triangle by applying the SQUARE function to two variables and then calculating the square root of their sum.</span></span> <span data-ttu-id="e5c5d-120">**Side1** 에 3이 포함되어 있고 **Side2** 에 4가 포함되어 있으면 SQRT 함수는 5를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="e5c5d-120">If **Side1** contains 3 and **Side2** contains 4, the SQRT function returns 5.</span></span>  
  
```  
SQRT(SQUARE(@Side1) + SQUARE(@Side2))  
```  
  
> [!NOTE]  
>  <span data-ttu-id="e5c5d-121">식에서 변수 이름에는 항상 \@ 접두사가 포함되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5c5d-121">In expressions, variable names always include the \@ prefix.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5c5d-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e5c5d-122">See Also</span></span>  
 [<span data-ttu-id="e5c5d-123">함수&#40;SSIS 식&#41;</span><span class="sxs-lookup"><span data-stu-id="e5c5d-123">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
