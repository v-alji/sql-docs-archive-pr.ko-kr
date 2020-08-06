---
title: EXP(SSIS 식) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- exponential functions
- EXP function
ms.assetid: 4cd96d3c-58c9-4a67-a6f6-b72758232912
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 150c92355ab3e0d3a028c98defe2e2fa9a1bf8ad
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651780"
---
# <a name="exp-ssis-expression"></a><span data-ttu-id="aad91-102">EXP(SSIS 식)</span><span class="sxs-lookup"><span data-stu-id="aad91-102">EXP (SSIS Expression)</span></span>
  <span data-ttu-id="aad91-103">밑이 e인 숫자 식의 지수를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="aad91-103">Returns the exponent to base e of a numeric expression.</span></span> <span data-ttu-id="aad91-104">EXP 함수는 LN 함수의 동작을 보완하며 역대수라고도 합니다.</span><span class="sxs-lookup"><span data-stu-id="aad91-104">The EXP function complements the action of the LN function and is sometimes referred to as the antilogarithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aad91-105">구문</span><span class="sxs-lookup"><span data-stu-id="aad91-105">Syntax</span></span>  
  
```  
  
EXP(numeric_expression)  
```  
  
## <a name="arguments"></a><span data-ttu-id="aad91-106">인수</span><span class="sxs-lookup"><span data-stu-id="aad91-106">Arguments</span></span>  
 <span data-ttu-id="aad91-107">*numeric_expression*</span><span class="sxs-lookup"><span data-stu-id="aad91-107">*numeric_expression*</span></span>  
 <span data-ttu-id="aad91-108">유효한 숫자 식입니다.</span><span class="sxs-lookup"><span data-stu-id="aad91-108">Is a valid numeric expression.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="aad91-109">결과 형식</span><span class="sxs-lookup"><span data-stu-id="aad91-109">Result Types</span></span>  
 <span data-ttu-id="aad91-110">DT_R8</span><span class="sxs-lookup"><span data-stu-id="aad91-110">DT_R8</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aad91-111">설명</span><span class="sxs-lookup"><span data-stu-id="aad91-111">Remarks</span></span>  
 <span data-ttu-id="aad91-112">숫자 식은 지수를 계산하기 전에 DT_R8 데이터 형식으로 캐스팅됩니다.</span><span class="sxs-lookup"><span data-stu-id="aad91-112">The numeric expression is cast to the DT_R8 data type before the exponent is computed.</span></span> <span data-ttu-id="aad91-113">자세한 내용은 [Integration Services Data Types](../data-flow/integration-services-data-types.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="aad91-113">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
 <span data-ttu-id="aad91-114">반환 결과는 항상 양수입니다.</span><span class="sxs-lookup"><span data-stu-id="aad91-114">The return result is always a positive number.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="aad91-115">식 예</span><span class="sxs-lookup"><span data-stu-id="aad91-115">Expression Examples</span></span>  
 <span data-ttu-id="aad91-116">이 예에서는 양수, 음수 및 0에 EXP 함수를 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="aad91-116">These examples apply the EXP function to positive and negative values and to zero.</span></span>  
  
```  
EXP(74)  
```  
  
 <span data-ttu-id="aad91-117">1\.373382979540176E+32를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="aad91-117">Returns 1.373382979540176E+32.</span></span>  
  
```  
EXP(-27)  
```  
  
 <span data-ttu-id="aad91-118">1\.879528816539083E-12를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="aad91-118">Returns 1.879528816539083E-12.</span></span>  
  
```  
EXP(0)  
```  
  
 <span data-ttu-id="aad91-119">1을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="aad91-119">Returns 1.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aad91-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="aad91-120">See Also</span></span>  
 <span data-ttu-id="aad91-121">[LOG&#40;SSIS 식&#41;](log-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="aad91-121">[LOG &#40;SSIS Expression&#41;](log-ssis-expression.md) </span></span>  
 [<span data-ttu-id="aad91-122">함수&#40;SSIS 식&#41;</span><span class="sxs-lookup"><span data-stu-id="aad91-122">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
