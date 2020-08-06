---
title: LN(SSIS 식) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- LN function
- natural logarithm of expression [Integration Services]
ms.assetid: 55d7b657-b5fd-4753-9c81-54ed7575e720
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 4c06d6e246cfa51f8e84eb93ab7eb73eab40c392
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652960"
---
# <a name="ln-ssis-expression"></a><span data-ttu-id="47431-102">LN(SSIS 식)</span><span class="sxs-lookup"><span data-stu-id="47431-102">LN (SSIS Expression)</span></span>
  <span data-ttu-id="47431-103">숫자 식의 자연 로그를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="47431-103">Returns the natural logarithm of a numeric expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47431-104">구문</span><span class="sxs-lookup"><span data-stu-id="47431-104">Syntax</span></span>  
  
```  
  
LN(numeric_expression)  
```  
  
## <a name="arguments"></a><span data-ttu-id="47431-105">인수</span><span class="sxs-lookup"><span data-stu-id="47431-105">Arguments</span></span>  
 <span data-ttu-id="47431-106">*numeric_expression*</span><span class="sxs-lookup"><span data-stu-id="47431-106">*numeric_expression*</span></span>  
 <span data-ttu-id="47431-107">0과 음수가 아닌 유효한 숫자 식입니다.</span><span class="sxs-lookup"><span data-stu-id="47431-107">Is a valid non-zero and non-negative numeric expression.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="47431-108">결과 형식</span><span class="sxs-lookup"><span data-stu-id="47431-108">Result Types</span></span>  
 <span data-ttu-id="47431-109">DT_R8</span><span class="sxs-lookup"><span data-stu-id="47431-109">DT_R8</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="47431-110">설명</span><span class="sxs-lookup"><span data-stu-id="47431-110">Remarks</span></span>  
 <span data-ttu-id="47431-111">숫자 식은 로그를 계산하기 전에 DT_R8 데이터 형식으로 캐스팅됩니다.</span><span class="sxs-lookup"><span data-stu-id="47431-111">The numeric expression is cast to the DT_R8 data type before the logarithm is computed.</span></span> <span data-ttu-id="47431-112">자세한 내용은 [Integration Services Data Types](../data-flow/integration-services-data-types.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="47431-112">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
 <span data-ttu-id="47431-113">*numeric_expression* 이 0 또는 음수 값으로 계산되면 반환 결과는 Null입니다.</span><span class="sxs-lookup"><span data-stu-id="47431-113">If *numeric_expression* evaluates to zero or a negative value, the return result is null.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="47431-114">식 예</span><span class="sxs-lookup"><span data-stu-id="47431-114">Expression Examples</span></span>  
 <span data-ttu-id="47431-115">이 예에서는 숫자 리터럴을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="47431-115">This example uses a numeric literal.</span></span> <span data-ttu-id="47431-116">이 함수는 값 3.737766961828337을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="47431-116">The function returns the value 3.737766961828337.</span></span>  
  
```  
LN(42)  
```  
  
 <span data-ttu-id="47431-117">이 예에서는 열 **Length**를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="47431-117">This example uses the column **Length**.</span></span> <span data-ttu-id="47431-118">열 값이 53.99이면 3.9887988442302가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="47431-118">If the column value is 53.99, the function returns 3.9887988442302.</span></span>  
  
```  
LN(Length)   
```  
  
 <span data-ttu-id="47431-119">이 예에서는 변수 **Length**를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="47431-119">This example uses the variable **Length**.</span></span> <span data-ttu-id="47431-120">변수가 숫자 데이터 형식이거나 식이 숫자 데이터 형식으로의 명시적 캐스트를 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="47431-120">The variable must have a numeric data type or the expression must include an explicit cast to a numeric data type.</span></span> <span data-ttu-id="47431-121">**Length** 가 234.567이면 함수는 5.45774126708797을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="47431-121">If **Length** is 234.567, the function returns 5.45774126708797.</span></span>  
  
```  
LN(@Length)   
```  
  
## <a name="see-also"></a><span data-ttu-id="47431-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="47431-122">See Also</span></span>  
 <span data-ttu-id="47431-123">[LOG&#40;SSIS 식&#41;](log-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="47431-123">[LOG &#40;SSIS Expression&#41;](log-ssis-expression.md) </span></span>  
 [<span data-ttu-id="47431-124">함수&#40;SSIS 식&#41;</span><span class="sxs-lookup"><span data-stu-id="47431-124">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
