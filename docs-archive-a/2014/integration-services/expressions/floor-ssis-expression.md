---
title: FLOOR(SSIS 식) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- largest integer less than or equal to expression
- FLOOR function [SSIS]
ms.assetid: 168084db-badd-40f2-87b4-1f5bc45c3e24
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b638c9a7215d120c562e416cdecee463f031ad2a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650200"
---
# <a name="floor-ssis-expression"></a><span data-ttu-id="81d34-102">FLOOR(SSIS 식)</span><span class="sxs-lookup"><span data-stu-id="81d34-102">FLOOR (SSIS Expression)</span></span>
  <span data-ttu-id="81d34-103">숫자 식보다 작거나 같은 최대 정수를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="81d34-103">Returns the largest integer that is less than or equal to a numeric expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81d34-104">구문</span><span class="sxs-lookup"><span data-stu-id="81d34-104">Syntax</span></span>  
  
```  
  
FLOOR(numeric_expression)  
```  
  
## <a name="arguments"></a><span data-ttu-id="81d34-105">인수</span><span class="sxs-lookup"><span data-stu-id="81d34-105">Arguments</span></span>  
 <span data-ttu-id="81d34-106">*numeric_expression*</span><span class="sxs-lookup"><span data-stu-id="81d34-106">*numeric_expression*</span></span>  
 <span data-ttu-id="81d34-107">유효한 숫자 식입니다.</span><span class="sxs-lookup"><span data-stu-id="81d34-107">Is a valid numeric expression.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="81d34-108">결과 형식</span><span class="sxs-lookup"><span data-stu-id="81d34-108">Result Types</span></span>  
 <span data-ttu-id="81d34-109">인수 식의 숫자 데이터 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="81d34-109">The numeric data type of the argument expression.</span></span> <span data-ttu-id="81d34-110">결과는 *numeric_expression*과 동일한 데이터 형식으로 계산된 값의 정수 부분입니다.</span><span class="sxs-lookup"><span data-stu-id="81d34-110">The result is the integer portion of the calculated value in the same data type as *numeric_expression.*</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="81d34-111">설명</span><span class="sxs-lookup"><span data-stu-id="81d34-111">Remarks</span></span>  
 <span data-ttu-id="81d34-112">인수가 Null이면 FLOOR 결과도 Null입니다.</span><span class="sxs-lookup"><span data-stu-id="81d34-112">FLOOR returns a null result if the argument is null.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="81d34-113">식 예</span><span class="sxs-lookup"><span data-stu-id="81d34-113">Expression Examples</span></span>  
 <span data-ttu-id="81d34-114">이 예에서는 FLOOR 함수를 양수, 음수 및 0 값에 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="81d34-114">These examples apply the FLOOR function to positive, negative, and zero values.</span></span>  
  
```  
FLOOR(123.45)  
```  
  
 <span data-ttu-id="81d34-115">123.00을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="81d34-115">Returns 123.00</span></span>  
  
```  
FLOOR(-123.45)  
```  
  
 <span data-ttu-id="81d34-116">-124.00을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="81d34-116">Returns -124.00</span></span>  
  
```  
FLOOR(0.00)  
```  
  
 <span data-ttu-id="81d34-117">0\.00을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="81d34-117">Returns 0.00</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81d34-118">참고 항목</span><span class="sxs-lookup"><span data-stu-id="81d34-118">See Also</span></span>  
 <span data-ttu-id="81d34-119">[CEILING&#40;SSIS 식&#41;](ceiling-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="81d34-119">[CEILING &#40;SSIS Expression&#41;](ceiling-ssis-expression.md) </span></span>  
 [<span data-ttu-id="81d34-120">함수&#40;SSIS 식&#41;</span><span class="sxs-lookup"><span data-stu-id="81d34-120">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
