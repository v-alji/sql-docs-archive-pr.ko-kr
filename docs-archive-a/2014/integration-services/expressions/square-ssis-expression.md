---
title: SQUARE(SSIS 식) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- SQUARE
- square values
ms.assetid: cecf1bb2-3d55-40a6-9688-ed67bcc150b4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 09955e708aae707a88aa7821d2a72651a3a44d59
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732788"
---
# <a name="square-ssis-expression"></a><span data-ttu-id="7959b-102">SQUARE(SSIS 식)</span><span class="sxs-lookup"><span data-stu-id="7959b-102">SQUARE (SSIS Expression)</span></span>
  <span data-ttu-id="7959b-103">숫자 식의 제곱을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="7959b-103">Returns the square of a numeric expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7959b-104">구문</span><span class="sxs-lookup"><span data-stu-id="7959b-104">Syntax</span></span>  
  
```  
  
SQUARE(numeric_expression)  
```  
  
## <a name="arguments"></a><span data-ttu-id="7959b-105">인수</span><span class="sxs-lookup"><span data-stu-id="7959b-105">Arguments</span></span>  
 <span data-ttu-id="7959b-106">*numeric_expression*</span><span class="sxs-lookup"><span data-stu-id="7959b-106">*numeric_expression*</span></span>  
 <span data-ttu-id="7959b-107">임의의 숫자 데이터 형식을 갖는 숫자 식입니다.</span><span class="sxs-lookup"><span data-stu-id="7959b-107">Is a numeric expression of any numeric data type.</span></span> <span data-ttu-id="7959b-108">자세한 내용은 [Integration Services Data Types](../data-flow/integration-services-data-types.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7959b-108">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="7959b-109">결과 형식</span><span class="sxs-lookup"><span data-stu-id="7959b-109">Result Types</span></span>  
 <span data-ttu-id="7959b-110">DT_R8</span><span class="sxs-lookup"><span data-stu-id="7959b-110">DT_R8</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7959b-111">설명</span><span class="sxs-lookup"><span data-stu-id="7959b-111">Remarks</span></span>  
 <span data-ttu-id="7959b-112">인수가 Null이면 SQUARE 결과도 Null입니다.</span><span class="sxs-lookup"><span data-stu-id="7959b-112">SQUARE returns a null result if the argument is null.</span></span>  
  
 <span data-ttu-id="7959b-113">인수는 제곱 연산 전에 DT_R8 데이터 형식으로 캐스팅됩니다.</span><span class="sxs-lookup"><span data-stu-id="7959b-113">The argument is cast to the DT_R8 data type before the square operation.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="7959b-114">식 예</span><span class="sxs-lookup"><span data-stu-id="7959b-114">Expression Examples</span></span>  
 <span data-ttu-id="7959b-115">이 예에서는 12의 제곱을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="7959b-115">This example returns the square of 12.</span></span> <span data-ttu-id="7959b-116">반환 결과는 144입니다.</span><span class="sxs-lookup"><span data-stu-id="7959b-116">The return result is 144.</span></span>  
  
```  
SQUARE(12)  
```  
  
 <span data-ttu-id="7959b-117">이 예에서는 두 열의 값을 뺀 결과의 제곱을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="7959b-117">This example returns the square of the result of subtracting values in two columns.</span></span> <span data-ttu-id="7959b-118">**Value1** 이 12이고 **Value2** 가 4이면 SQUARE 함수는 64를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="7959b-118">If **Value1** contains 12 and **Value2** contains 4, the SQUARE function returns 64.</span></span>  
  
```  
SQUARE(Value1 - Value2)  
```  
  
 <span data-ttu-id="7959b-119">이 예에서는 두 변수에 SQUARE 함수를 적용한 후 합계의 제곱근을 계산하여 직각 삼각형의 3번째 변의 길이를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="7959b-119">This example returns the length of the third side of a right angle triangle by applying the SQUARE function to two variables and then calculating the square root of their sum.</span></span> <span data-ttu-id="7959b-120">**Side1** 에 3이 포함되어 있고 **Side2** 에 4가 포함되어 있으면 SQRT 함수는 5를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="7959b-120">If **Side1** contains 3 and **Side2** contains 4, the SQRT function returns 5.</span></span>  
  
```  
SQRT(SQUARE(@Side1) + SQUARE(@Side2))  
```  
  
> [!NOTE]  
>  <span data-ttu-id="7959b-121">식에서 변수 이름에는 항상 \@ 접두사가 포함되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7959b-121">In expressions, variable names always include the \@ prefix.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7959b-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7959b-122">See Also</span></span>  
 [<span data-ttu-id="7959b-123">함수&#40;SSIS 식&#41;</span><span class="sxs-lookup"><span data-stu-id="7959b-123">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
