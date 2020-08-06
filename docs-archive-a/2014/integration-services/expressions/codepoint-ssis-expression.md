---
title: CODEPOINT(SSIS 식) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- CODEPOINT function
- leftmost character of expression
ms.assetid: 0783d05e-7f35-42fb-a2c4-9621c46effd6
author: chugugrace
ms.author: chugu
ms.openlocfilehash: bf05cc0838763ba9e22707af57892133d449da07
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646556"
---
# <a name="codepoint-ssis-expression"></a><span data-ttu-id="07554-102">CODEPOINT(SSIS 식)</span><span class="sxs-lookup"><span data-stu-id="07554-102">CODEPOINT (SSIS Expression)</span></span>
  <span data-ttu-id="07554-103">문자 식에서 가장 왼쪽 문자의 유니코드 코드 포인트를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="07554-103">Returns the Unicode code point of the leftmost character of a character expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07554-104">구문</span><span class="sxs-lookup"><span data-stu-id="07554-104">Syntax</span></span>  
  
```  
  
CODEPOINT(character_expression)  
```  
  
## <a name="arguments"></a><span data-ttu-id="07554-105">인수</span><span class="sxs-lookup"><span data-stu-id="07554-105">Arguments</span></span>  
 <span data-ttu-id="07554-106">*character_expression*</span><span class="sxs-lookup"><span data-stu-id="07554-106">*character_expression*</span></span>  
 <span data-ttu-id="07554-107">가장 왼쪽의 문자를 평가할 문자 식입니다.</span><span class="sxs-lookup"><span data-stu-id="07554-107">Is a character expression whose leftmost character will be evaluated.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="07554-108">결과 형식</span><span class="sxs-lookup"><span data-stu-id="07554-108">Result Types</span></span>  
 <span data-ttu-id="07554-109">DT_UI2</span><span class="sxs-lookup"><span data-stu-id="07554-109">DT_UI2</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="07554-110">설명</span><span class="sxs-lookup"><span data-stu-id="07554-110">Remarks</span></span>  
 <span data-ttu-id="07554-111">*character_expression* 인수는 DT_WSTR 데이터 형식이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="07554-111">*character_expression* must have the DT_WSTR data type.</span></span>  
  
 <span data-ttu-id="07554-112">*character_expression* 이 Null이거나 빈 문자열이면 CODEPOINT 결과도 Null이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="07554-112">CODEPOINT returns a null result if *character_expression* is null or an empty string.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="07554-113">식 예</span><span class="sxs-lookup"><span data-stu-id="07554-113">Expression Examples</span></span>  
 <span data-ttu-id="07554-114">이 예에서는 문자열 리터럴을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="07554-114">This example uses a string literal.</span></span> <span data-ttu-id="07554-115">반환 결과는 M의 유니코드 코드 포인트인 77입니다.</span><span class="sxs-lookup"><span data-stu-id="07554-115">The return result is 77, the Unicode code point for M.</span></span>  
  
```  
CODEPOINT("Mountain Bike")  
```  
  
 <span data-ttu-id="07554-116">이 예에서는 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="07554-116">This example uses a variable.</span></span> <span data-ttu-id="07554-117">**Name** 이 Touring Front Wheel이면 반환 결과는 T의 유니코드 코드 포인트인 84입니다.</span><span class="sxs-lookup"><span data-stu-id="07554-117">If **Name** is Touring Front Wheel, the return result is 84, the Unicode code point for T.</span></span>  
  
```  
CODEPOINT(@Name)  
```  
  
## <a name="see-also"></a><span data-ttu-id="07554-118">참고 항목</span><span class="sxs-lookup"><span data-stu-id="07554-118">See Also</span></span>  
 [<span data-ttu-id="07554-119">함수&#40;SSIS 식&#41;</span><span class="sxs-lookup"><span data-stu-id="07554-119">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
