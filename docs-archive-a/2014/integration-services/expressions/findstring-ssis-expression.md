---
title: FINDSTRING(SSIS 식) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- FINDSTRING function
ms.assetid: c83cb1b1-3c52-4496-b518-4c9253b9336d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 72f2ff21cb179ce565e60c6550b8ecc2618a5adb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650199"
---
# <a name="findstring-ssis-expression"></a><span data-ttu-id="2d718-102">FINDSTRING(SSIS 식)</span><span class="sxs-lookup"><span data-stu-id="2d718-102">FINDSTRING (SSIS Expression)</span></span>
  <span data-ttu-id="2d718-103">문자 식에서 지정한 문자열 발생 위치를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="2d718-103">Returns the location of the specified occurrence of a string within a character expression.</span></span> <span data-ttu-id="2d718-104">반환 결과는 항목의 인덱스(1부터 시작)입니다.</span><span class="sxs-lookup"><span data-stu-id="2d718-104">The return result is the one-based index of the occurrence.</span></span> <span data-ttu-id="2d718-105">문자열 매개 변수는 문자 식으로 계산되고 발생 빈도 매개 변수는 정수여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2d718-105">The string parameter must evaluate to a character expression, and the occurrence parameter must evaluate to an integer.</span></span> <span data-ttu-id="2d718-106">문자열을 찾을 수 없는 경우 반환 값은 0입니다.</span><span class="sxs-lookup"><span data-stu-id="2d718-106">If the string is not found, the return value is 0.</span></span> <span data-ttu-id="2d718-107">문자열이 발생 인수에 지정된 횟수보다 적게 발생하는 경우에도 반환 값이 0입니다.</span><span class="sxs-lookup"><span data-stu-id="2d718-107">If the string occurs fewer times than the occurrence argument specifies, the return value is 0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d718-108">구문</span><span class="sxs-lookup"><span data-stu-id="2d718-108">Syntax</span></span>  
  
```  
  
FINDSTRING(character_expression, searchstring, occurrence)  
```  
  
## <a name="arguments"></a><span data-ttu-id="2d718-109">인수</span><span class="sxs-lookup"><span data-stu-id="2d718-109">Arguments</span></span>  
 <span data-ttu-id="2d718-110">*character_expression*</span><span class="sxs-lookup"><span data-stu-id="2d718-110">*character_expression*</span></span>  
 <span data-ttu-id="2d718-111">검색 위치를 나타내는 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="2d718-111">Is the character string to search in.</span></span>  
  
 <span data-ttu-id="2d718-112">*searchstring*</span><span class="sxs-lookup"><span data-stu-id="2d718-112">*searchstring*</span></span>  
 <span data-ttu-id="2d718-113">검색할 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="2d718-113">Is the character string to search for.</span></span>  
  
 <span data-ttu-id="2d718-114">*occurrence*</span><span class="sxs-lookup"><span data-stu-id="2d718-114">*occurrence*</span></span>  
 <span data-ttu-id="2d718-115">보고할 *searchstring* 발생을 지정하는 부호 있는 정수 또는 부호 없는 정수입니다.</span><span class="sxs-lookup"><span data-stu-id="2d718-115">Is a signed or unsigned integer specifying which occurrence of *searchstring* to report.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="2d718-116">결과 형식</span><span class="sxs-lookup"><span data-stu-id="2d718-116">Result Types</span></span>  
 <span data-ttu-id="2d718-117">DT_I4</span><span class="sxs-lookup"><span data-stu-id="2d718-117">DT_I4</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2d718-118">설명</span><span class="sxs-lookup"><span data-stu-id="2d718-118">Remarks</span></span>  
 <span data-ttu-id="2d718-119">FINDSTRING은 DT_WSTR 데이터 형식에서만 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="2d718-119">FINDSTRING works only with the DT_WSTR data type.</span></span>  <span data-ttu-id="2d718-120">문자열 리터럴인*character_expression* 및 *searchstring* 인수나 DT_STR 데이터 형식의 데이터 열은 FINDSTRING 연산이 수행되기 전에 DT_WSTR 데이터 형식으로 암시적으로 캐스팅됩니다.</span><span class="sxs-lookup"><span data-stu-id="2d718-120">*character_expression* and *searchstring* arguments that are string literals or data columns with the DT_STR data type are implicitly cast to the DT_WSTR data type before FINDSTRING performs its operation.</span></span> <span data-ttu-id="2d718-121">다른 데이터 형식은 DT_WSTR 데이터 형식으로 명시적으로 캐스팅되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2d718-121">Other data types must be explicitly cast to the DT_WSTR data type.</span></span> <span data-ttu-id="2d718-122">자세한 내용은 [Integration Services 데이터 형식](../data-flow/integration-services-data-types.md) 및 [캐스트&#40;SSIS 식&#41;](cast-ssis-expression.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2d718-122">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md) and [Cast &#40;SSIS Expression&#41;](cast-ssis-expression.md).</span></span>  
  
 <span data-ttu-id="2d718-123">*character_expression* 또는 *searchstring* 이 Null이면 FINDSTRING은 Null을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="2d718-123">FINDSTRING returns null if either *character_expression* or *searchstring* are null.</span></span>  
  
 <span data-ttu-id="2d718-124">*occurrence* 인수의 값이 1이면 첫 번째 발생의 인덱스를 가져오고 값이 2이면 두 번째 발생의 인덱스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="2d718-124">Use a value of 1 in the *occurrence* argument to get the index of the first occurrence, 2 for the second occurrence and so forth.</span></span>  
  
 <span data-ttu-id="2d718-125">*occurrence* 는 0보다 큰 정수여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2d718-125">The *occurrence* must be an integer with a value greater than 0.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="2d718-126">식 예</span><span class="sxs-lookup"><span data-stu-id="2d718-126">Expression Examples</span></span>  
 <span data-ttu-id="2d718-127">이 예에서는 문자열 리터럴을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="2d718-127">This example uses a string literal.</span></span> <span data-ttu-id="2d718-128">값 11을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="2d718-128">It returns the value 11.</span></span>  
  
```  
FINDSTRING("New York, NY, NY", "NY", 1)   
```  
  
 <span data-ttu-id="2d718-129">이 예에서는 문자열 리터럴을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="2d718-129">This example uses a string literal.</span></span> <span data-ttu-id="2d718-130">"NY" 문자열이 두 번만 발생하므로 반환 결과가 0입니다.</span><span class="sxs-lookup"><span data-stu-id="2d718-130">Because the string "NY" occurs only two times, the return result is 0.</span></span>  
  
```  
FINDSTRING("New York, NY, NY", "NY", 3)   
```  
  
 <span data-ttu-id="2d718-131">이 예에서는 **Name** 열을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="2d718-131">This example uses the **Name** column.</span></span> <span data-ttu-id="2d718-132">**Name** 열에서 값 n의 위치가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="2d718-132">It returns the location of the value n in the **Name** column.</span></span> <span data-ttu-id="2d718-133">반환 결과는 **Name**열의 값에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="2d718-133">The return result varies depending on the value in **Name**.</span></span> <span data-ttu-id="2d718-134">**Name** 열에 Anderson이 포함된 경우 함수는 8을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="2d718-134">If **Name** contains Anderson, the function returns 8.</span></span>  
  
```  
FINDSTRING(Name,"n", 2)   
```  
  
 <span data-ttu-id="2d718-135">이 예에서는 **Name** 열과 **Size** 열을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="2d718-135">This example uses the **Name** and **Size** columns.</span></span> <span data-ttu-id="2d718-136">**Name** 열에서 **Size** 값의 가장 왼쪽 문자 위치가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="2d718-136">It returns the location of the leftmost character of the **Size** value in the **Name** column.</span></span> <span data-ttu-id="2d718-137">반환 결과는 열 값에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="2d718-137">The return result varies depending on column values.</span></span> <span data-ttu-id="2d718-138">**Name** 이 Mountain,500Red,42이고 **Size** 가 42이면 반환 결과는 17입니다.</span><span class="sxs-lookup"><span data-stu-id="2d718-138">If **Name** contains Mountain,500Red,42 and **Size** contains 42, the return result is 17.</span></span>  
  
```  
FINDSTRING(Name,Size,1)   
```  
  
## <a name="see-also"></a><span data-ttu-id="2d718-139">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2d718-139">See Also</span></span>  
 <span data-ttu-id="2d718-140">[REPLACE&#40;SSIS 식&#41;](replace-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="2d718-140">[REPLACE &#40;SSIS Expression&#41;](replace-ssis-expression.md) </span></span>  
 [<span data-ttu-id="2d718-141">함수&#40;SSIS 식&#41;</span><span class="sxs-lookup"><span data-stu-id="2d718-141">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
