---
title: CEILING(SSIS 식) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- smallest integer great than or equal to expression
- CEILING function [SSIS]
ms.assetid: c35bd4ee-1ab6-46ab-89a7-cf771527faa2
author: chugugrace
ms.author: chugu
ms.openlocfilehash: cd2f9f455226925d6bf00842e80a8713e6c72771
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661255"
---
# <a name="ceiling-ssis-expression"></a><span data-ttu-id="904ac-102">CEILING(SSIS 식)</span><span class="sxs-lookup"><span data-stu-id="904ac-102">CEILING (SSIS Expression)</span></span>
  <span data-ttu-id="904ac-103">숫자 식보다 크거나 같은 최소 정수를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="904ac-103">Returns the smallest integer that is greater than or equal to a numeric expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="904ac-104">구문</span><span class="sxs-lookup"><span data-stu-id="904ac-104">Syntax</span></span>  
  
```  
  
CEILING(numeric_expression)  
```  
  
## <a name="arguments"></a><span data-ttu-id="904ac-105">인수</span><span class="sxs-lookup"><span data-stu-id="904ac-105">Arguments</span></span>  
 <span data-ttu-id="904ac-106">*numeric_expression*</span><span class="sxs-lookup"><span data-stu-id="904ac-106">*numeric_expression*</span></span>  
 <span data-ttu-id="904ac-107">유효한 숫자 식입니다.</span><span class="sxs-lookup"><span data-stu-id="904ac-107">Is a valid numeric expression.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="904ac-108">결과 형식</span><span class="sxs-lookup"><span data-stu-id="904ac-108">Result Types</span></span>  
 <span data-ttu-id="904ac-109">함수에 전달된 숫자 식의 데이터 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="904ac-109">The data type of the numeric expression submitted to the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="904ac-110">설명</span><span class="sxs-lookup"><span data-stu-id="904ac-110">Remarks</span></span>  
 <span data-ttu-id="904ac-111">인수가 Null이면 CEILING 결과도 Null입니다.</span><span class="sxs-lookup"><span data-stu-id="904ac-111">CEILING returns a null result if the argument is null.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="904ac-112">식 예</span><span class="sxs-lookup"><span data-stu-id="904ac-112">Expression Examples</span></span>  
 <span data-ttu-id="904ac-113">이 예에서는 양수, 음수 및 0 값에 CEILING 함수를 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="904ac-113">These examples apply the CEILING function to positive, negative, and zero values.</span></span>  
  
```  
CEILING(123.74)  
```  
  
 <span data-ttu-id="904ac-114">124.00을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="904ac-114">Returns 124.00</span></span>  
  
```  
CEILING(-124.27)  
```  
  
 <span data-ttu-id="904ac-115">-124.00을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="904ac-115">Returns -124.00</span></span>  
  
```  
CEILING(0.00)  
```  
  
 <span data-ttu-id="904ac-116">0\.00을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="904ac-116">Returns 0.00</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="904ac-117">참고 항목</span><span class="sxs-lookup"><span data-stu-id="904ac-117">See Also</span></span>  
 <span data-ttu-id="904ac-118">[FLOOR&#40;SSIS 식&#41;](floor-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="904ac-118">[FLOOR &#40;SSIS Expression&#41;](floor-ssis-expression.md) </span></span>  
 [<span data-ttu-id="904ac-119">함수&#40;SSIS 식&#41;</span><span class="sxs-lookup"><span data-stu-id="904ac-119">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
