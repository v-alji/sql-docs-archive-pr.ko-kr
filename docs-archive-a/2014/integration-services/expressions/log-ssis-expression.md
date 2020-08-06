---
title: LOG(SSIS 식) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- base-10 logarithms
- LOG function
ms.assetid: f7fccace-c178-4e13-bde9-7dc4ef1d98fa
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0de84c1a92f94507bcc69c47cc4d9b6cda50a4f9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652956"
---
# <a name="log-ssis-expression"></a><span data-ttu-id="4267c-102">LOG(SSIS 식)</span><span class="sxs-lookup"><span data-stu-id="4267c-102">LOG (SSIS Expression)</span></span>
  <span data-ttu-id="4267c-103">숫자 식의 상용 로그를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="4267c-103">Returns the base-10 logarithm of a numeric expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4267c-104">구문</span><span class="sxs-lookup"><span data-stu-id="4267c-104">Syntax</span></span>  
  
```  
  
LOG(numeric_expression)  
```  
  
## <a name="arguments"></a><span data-ttu-id="4267c-105">인수</span><span class="sxs-lookup"><span data-stu-id="4267c-105">Arguments</span></span>  
 <span data-ttu-id="4267c-106">*numeric_expression*</span><span class="sxs-lookup"><span data-stu-id="4267c-106">*numeric_expression*</span></span>  
 <span data-ttu-id="4267c-107">0이 아니거나 음수가 아닌 유효한 숫자 식입니다.</span><span class="sxs-lookup"><span data-stu-id="4267c-107">Is a valid nonzero or nonnegative numeric expression.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="4267c-108">결과 형식</span><span class="sxs-lookup"><span data-stu-id="4267c-108">Result Types</span></span>  
 <span data-ttu-id="4267c-109">DT_R8</span><span class="sxs-lookup"><span data-stu-id="4267c-109">DT_R8</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4267c-110">설명</span><span class="sxs-lookup"><span data-stu-id="4267c-110">Remarks</span></span>  
 <span data-ttu-id="4267c-111">*숫자 식* 은 로그를 계산하기 전에 DT_R8 데이터 형식으로 캐스팅됩니다.</span><span class="sxs-lookup"><span data-stu-id="4267c-111">The *numeric expression* is cast to the DT_R8 data type before the logarithm is computed.</span></span> <span data-ttu-id="4267c-112">자세한 내용은 [Integration Services Data Types](../data-flow/integration-services-data-types.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4267c-112">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
 <span data-ttu-id="4267c-113">*numeric_expression* 이 0 또는 음수 값으로 계산되면 반환 결과는 Null입니다.</span><span class="sxs-lookup"><span data-stu-id="4267c-113">If *numeric_expression* evaluates to zero or a negative value, the return result is null.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="4267c-114">식 예</span><span class="sxs-lookup"><span data-stu-id="4267c-114">Expression Examples</span></span>  
 <span data-ttu-id="4267c-115">이 예에서는 숫자 리터럴을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="4267c-115">This example uses a numeric literal.</span></span> <span data-ttu-id="4267c-116">이 함수는 값 1.988291341907488을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="4267c-116">The function returns the value 1.988291341907488.</span></span>  
  
```  
LOG(97.34)  
```  
  
 <span data-ttu-id="4267c-117">이 예에서는 열 **Length**를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="4267c-117">This example uses the column **Length**.</span></span> <span data-ttu-id="4267c-118">열 값이 101.24이면 2.005352136486217을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="4267c-118">If the column is 101.24, the function returns 2.005352136486217.</span></span>  
  
```  
LOG(Length)   
```  
  
 <span data-ttu-id="4267c-119">이 예에서는 변수 **Length**를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="4267c-119">This example uses the variable **Length**.</span></span> <span data-ttu-id="4267c-120">변수가 숫자 데이터 형식이거나 식이 숫자 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 데이터 형식으로의 명시적 캐스트를 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4267c-120">The variable must have a numeric data type or the expression must include an explicit cast to a numeric [!INCLUDE[ssIS](../../includes/ssis-md.md)] data type.</span></span> <span data-ttu-id="4267c-121">**Length** 가 234.567이면 함수는 2.370266913465859을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="4267c-121">If **Length** is 234.567, the function returns 2.370266913465859.</span></span>  
  
```  
LOG(@Length)   
```  
  
## <a name="see-also"></a><span data-ttu-id="4267c-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4267c-122">See Also</span></span>  
 <span data-ttu-id="4267c-123">[EXP&#40;SSIS 식&#41;](exp-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="4267c-123">[EXP &#40;SSIS Expression&#41;](exp-ssis-expression.md) </span></span>  
 <span data-ttu-id="4267c-124">[LN&#40;SSIS 식&#41;](ln-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="4267c-124">[LN &#40;SSIS Expression&#41;](ln-ssis-expression.md) </span></span>  
 [<span data-ttu-id="4267c-125">함수&#40;SSIS 식&#41;</span><span class="sxs-lookup"><span data-stu-id="4267c-125">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
