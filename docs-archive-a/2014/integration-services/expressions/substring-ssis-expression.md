---
title: SUBSTRING(SSIS 식) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- SUBSTRING function
- part of expression returned [Integration Services]
ms.assetid: 3a46748a-f5f8-4a6c-9108-673666754068
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ba53676bc6d13ed34892f48fca3b70372cb30604
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732779"
---
# <a name="substring-ssis-expression"></a><span data-ttu-id="9057c-102">SUBSTRING(SSIS 식)</span><span class="sxs-lookup"><span data-stu-id="9057c-102">SUBSTRING (SSIS Expression)</span></span>
  <span data-ttu-id="9057c-103">문자 식에서 지정된 위치부터 시작하여 지정된 길이만큼 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="9057c-103">Returns the part of a character expression that starts at the specified position and has the specified length.</span></span> <span data-ttu-id="9057c-104">*position* 매개 변수와 *length* 매개 변수는 정수여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9057c-104">The *position* parameter and the *length* parameter must evaluate to integers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9057c-105">구문</span><span class="sxs-lookup"><span data-stu-id="9057c-105">Syntax</span></span>  
  
```  
  
SUBSTRING(character_expression, position, length)  
```  
  
## <a name="arguments"></a><span data-ttu-id="9057c-106">인수</span><span class="sxs-lookup"><span data-stu-id="9057c-106">Arguments</span></span>  
 <span data-ttu-id="9057c-107">*character_expression*</span><span class="sxs-lookup"><span data-stu-id="9057c-107">*character_expression*</span></span>  
 <span data-ttu-id="9057c-108">문자를 추출할 문자 식입니다.</span><span class="sxs-lookup"><span data-stu-id="9057c-108">Is a character expression from which to extract characters.</span></span>  
  
 <span data-ttu-id="9057c-109">*position*</span><span class="sxs-lookup"><span data-stu-id="9057c-109">*position*</span></span>  
 <span data-ttu-id="9057c-110">하위 문자열이 시작되는 지점을 지정하는 정수입니다.</span><span class="sxs-lookup"><span data-stu-id="9057c-110">Is an integer that specifies where the substring begins.</span></span>  
  
 <span data-ttu-id="9057c-111">*length*</span><span class="sxs-lookup"><span data-stu-id="9057c-111">*length*</span></span>  
 <span data-ttu-id="9057c-112">부분 문자열의 길이를 문자 수로 지정하는 정수입니다.</span><span class="sxs-lookup"><span data-stu-id="9057c-112">Is an integer that specifies the length of the substring as number of characters.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="9057c-113">결과 형식</span><span class="sxs-lookup"><span data-stu-id="9057c-113">Result Types</span></span>  
 <span data-ttu-id="9057c-114">DT_WSTR</span><span class="sxs-lookup"><span data-stu-id="9057c-114">DT_WSTR</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9057c-115">설명</span><span class="sxs-lookup"><span data-stu-id="9057c-115">Remarks</span></span>  
 <span data-ttu-id="9057c-116">SUBSTRING은 1부터 시작하는 인덱스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="9057c-116">SUBSTRING uses a one-based index.</span></span> <span data-ttu-id="9057c-117">*position* 이 1이면 부분 문자열은 *character_expression*의 첫 번째 문자로 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="9057c-117">If *position* is 1, the substring begins with the first character in *character_expression*.</span></span>  
  
 <span data-ttu-id="9057c-118">SUBSTRING은 DT_WSTR 데이터 형식에서만 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="9057c-118">SUBSTRING works only with the DT_WSTR data type.</span></span> <span data-ttu-id="9057c-119">문자열 리터럴이나 DT_STR 데이터 형식의 데이터 열인 *character_expression* 인수는 SUBSTRING이 연산을 수행하기 전에 DT_WSTR 데이터 형식으로 암시적으로 캐스팅됩니다.</span><span class="sxs-lookup"><span data-stu-id="9057c-119">A *character_expression* argument that is a string literal or a data column with the DT_STR data type is implicitly cast to the DT_WSTR data type before SUBSTRING performs its operation.</span></span> <span data-ttu-id="9057c-120">다른 데이터 형식은 DT_WSTR 데이터 형식으로 명시적으로 캐스팅되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9057c-120">Other data types must be explicitly cast to the DT_WSTR data type.</span></span> <span data-ttu-id="9057c-121">자세한 내용은 [Integration Services 데이터 형식](../data-flow/integration-services-data-types.md) 및 [캐스트&#40;SSIS 식&#41;](cast-ssis-expression.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9057c-121">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md) and [Cast &#40;SSIS Expression&#41;](cast-ssis-expression.md).</span></span>  
  
 <span data-ttu-id="9057c-122">인수가 Null이면 SUBSTRING 결과도 Null입니다.</span><span class="sxs-lookup"><span data-stu-id="9057c-122">SUBSTRING returns a null result if the argument is null.</span></span>  
  
 <span data-ttu-id="9057c-123">식의 모든 인수가 변수와 열을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9057c-123">All arguments in the expression can use variables and columns.</span></span>  
  
 <span data-ttu-id="9057c-124">*length* 인수는 문자열 길이를 초과할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9057c-124">The *length* argument can exceed the length of the string.</span></span> <span data-ttu-id="9057c-125">이 경우 문자열의 나머지가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="9057c-125">In that case, the function returns the remainder of the string.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="9057c-126">식 예</span><span class="sxs-lookup"><span data-stu-id="9057c-126">Expression Examples</span></span>  
 <span data-ttu-id="9057c-127">이 예에서는 문자 4부터 시작하여 문자열 리터럴의 두 문자가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="9057c-127">This example returns two characters, beginning with character 4, from a string literal.</span></span> <span data-ttu-id="9057c-128">반환 결과는 "ph"입니다.</span><span class="sxs-lookup"><span data-stu-id="9057c-128">The return result is "ph".</span></span>  
  
```  
SUBSTRING("elephant",4,2)  
```  
  
 <span data-ttu-id="9057c-129">이 예에서는 4번째 문자부터 시작하여 문자열 리터럴의 나머지가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="9057c-129">This example returns the remainder of a string literal, beginning at the fourth character.</span></span> <span data-ttu-id="9057c-130">반환 결과는 "phant"입니다.</span><span class="sxs-lookup"><span data-stu-id="9057c-130">The return result is "phant".</span></span> <span data-ttu-id="9057c-131">*length* 인수가 문자열 길이를 초과하는 것은 오류가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="9057c-131">It is not an error for the *length* argument to exceed the length of the string.</span></span>  
  
```  
SUBSTRING ("elephant",4,50)  
```  
  
 <span data-ttu-id="9057c-132">이 예에서는 **MiddleName** 열의 첫 문자가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="9057c-132">This example returns the first letter from the **MiddleName** column.</span></span>  
  
```  
SUBSTRING(MiddleName,1,1)  
```  
  
 <span data-ttu-id="9057c-133">이 예에서는 *position* 및 *length* 인수에 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="9057c-133">This example uses variables in the *position* and *length* arguments.</span></span> <span data-ttu-id="9057c-134">**Start** 가 1이고 **Length** 가 5이면 **Name** 열의 처음 5문자가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="9057c-134">If **Start** is 1 and **Length** is 5, the function returns the first five characters in the **Name** column.</span></span>  
  
```  
SUBSTRING(Name,@Start,@Length)  
```  
  
 <span data-ttu-id="9057c-135">이 예에서는 여섯 번째 문자부터 시작하여 **PostalCode** 변수의 마지막 네 문자가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="9057c-135">This example returns the last four characters from the **PostalCode** variable beginning at the sixth character.</span></span>  
  
```  
SUBSTRING (@PostalCode,6,4)  
```  
  
 <span data-ttu-id="9057c-136">이 예에서는 문자열 리터럴의 길이가 0인 문자열이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="9057c-136">This example returns a zero-length string from a string literal.</span></span>  
  
```  
SUBSTRING ("Redmond",4,0)  
```  
  
## <a name="see-also"></a><span data-ttu-id="9057c-137">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9057c-137">See Also</span></span>  
 [<span data-ttu-id="9057c-138">함수&#40;SSIS 식&#41;</span><span class="sxs-lookup"><span data-stu-id="9057c-138">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
