---
title: RIGHT(SSIS 식) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- RIGHT function
ms.assetid: 83e70e75-4be5-4783-a8cf-032f82afe16e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 2584ee33ecbf0436c4e3dc6e92b957e60ae396ce
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732812"
---
# <a name="right-ssis-expression"></a><span data-ttu-id="090a6-102">RIGHT(SSIS 식)</span><span class="sxs-lookup"><span data-stu-id="090a6-102">RIGHT (SSIS Expression)</span></span>
  <span data-ttu-id="090a6-103">지정한 문자 식의 오른쪽에서부터 지정한 개수의 문자를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="090a6-103">Returns the specified number of characters from the rightmost portion of the given character expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="090a6-104">구문</span><span class="sxs-lookup"><span data-stu-id="090a6-104">Syntax</span></span>  
  
```  
  
RIGHT(character_expression,integer_expression)  
```  
  
## <a name="arguments"></a><span data-ttu-id="090a6-105">인수</span><span class="sxs-lookup"><span data-stu-id="090a6-105">Arguments</span></span>  
 <span data-ttu-id="090a6-106">*character_expression*</span><span class="sxs-lookup"><span data-stu-id="090a6-106">*character_expression*</span></span>  
 <span data-ttu-id="090a6-107">문자를 추출할 문자 식입니다.</span><span class="sxs-lookup"><span data-stu-id="090a6-107">Is a character expression from which to extract characters.</span></span>  
  
 <span data-ttu-id="090a6-108">*integer_expression*</span><span class="sxs-lookup"><span data-stu-id="090a6-108">*integer_expression*</span></span>  
 <span data-ttu-id="090a6-109">반환할 문자 수를 나타내는 정수 식입니다.</span><span class="sxs-lookup"><span data-stu-id="090a6-109">Is an integer expression that indicates the number of characters to be returned.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="090a6-110">결과 형식</span><span class="sxs-lookup"><span data-stu-id="090a6-110">Result Types</span></span>  
 <span data-ttu-id="090a6-111">DT_WSTR</span><span class="sxs-lookup"><span data-stu-id="090a6-111">DT_WSTR</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="090a6-112">설명</span><span class="sxs-lookup"><span data-stu-id="090a6-112">Remarks</span></span>  
 <span data-ttu-id="090a6-113">*integer_expression* 이 *character_expression*의 길이보다 큰 경우 함수는 *character_expression*을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="090a6-113">If *integer_expression* is greater than the length of *character_expression*, the function returns *character_expression*.</span></span>  
  
 <span data-ttu-id="090a6-114">*integer_expression* 이 0인 경우 함수는 길이가 0인 문자열을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="090a6-114">If *integer_expression* is zero, the function returns a zero-length string.</span></span>  
  
 <span data-ttu-id="090a6-115">*integer_expression* 이 음수인 경우 함수는 오류를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="090a6-115">If *integer_expression* is a negative number, the function returns an error.</span></span>  
  
 <span data-ttu-id="090a6-116">*integer_expression* 인수는 변수와 열을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="090a6-116">The *integer_expression* argument can take variables and columns.</span></span>  
  
 <span data-ttu-id="090a6-117">RIGHT는 DT_WSTR 데이터 형식에서만 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="090a6-117">RIGHT works only with the DT_WSTR data type.</span></span> <span data-ttu-id="090a6-118">문자열 리터럴이나 DT_STR 데이터 형식의 데이터 열인 *character_expression* 인수는 RIGHT가 연산을 수행하기 전에 DT_WSTR 데이터 형식으로 암시적으로 캐스팅됩니다.</span><span class="sxs-lookup"><span data-stu-id="090a6-118">A *character_expression* argument that is a string literal or a data column with the DT_STR data type is implicitly cast to the DT_WSTR data type before RIGHT performs its operation.</span></span> <span data-ttu-id="090a6-119">다른 데이터 형식은 DT_WSTR 데이터 형식으로 명시적으로 캐스팅되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="090a6-119">Other data types must be explicitly cast to the DT_WSTR data type.</span></span> <span data-ttu-id="090a6-120">자세한 내용은 [Integration Services 데이터 형식](../data-flow/integration-services-data-types.md) 및 [캐스트&#40;SSIS 식&#41;](cast-ssis-expression.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="090a6-120">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md) and [Cast &#40;SSIS Expression&#41;](cast-ssis-expression.md).</span></span>  
  
 <span data-ttu-id="090a6-121">두 인수 중 하나가 Null이면 RIGHT 결과도 Null입니다.</span><span class="sxs-lookup"><span data-stu-id="090a6-121">RIGHT returns a null result if either argument is null.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="090a6-122">식 예</span><span class="sxs-lookup"><span data-stu-id="090a6-122">Expression Examples</span></span>  
 <span data-ttu-id="090a6-123">다음 예에서는 문자열 리터럴을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="090a6-123">The following example uses a string literal.</span></span> <span data-ttu-id="090a6-124">반환 결과는 `"Bike"`입니다.</span><span class="sxs-lookup"><span data-stu-id="090a6-124">The return result is `"Bike"`.</span></span>  
  
```  
RIGHT("Mountain Bike", 4)  
```  
  
 <span data-ttu-id="090a6-125">다음 예에서는 `Times` 열의 오른쪽부터 `Name` 변수에 지정한 문자 수만큼의 부분을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="090a6-125">The following example returns the number of rightmost characters that is specified in the `Times` variable, from the `Name` column.</span></span> <span data-ttu-id="090a6-126">`Name` 이 `Touring Front Wheel` 이고 `Times` 가 5이면 반환 결과는 `"Wheel"`입니다.</span><span class="sxs-lookup"><span data-stu-id="090a6-126">If `Name` is `Touring Front Wheel` and `Times` is 5, the return result is `"Wheel"`.</span></span>  
  
```  
RIGHT(Name, @Times)  
```  
  
 <span data-ttu-id="090a6-127">또한 다음 예에서는 `Times` 열의 오른쪽부터 `Name` 변수에 지정한 문자 수만큼의 부분을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="090a6-127">The following example also returns the number of rightmost characters that is specified in the `Times` variable, from the `Name` column.</span></span> <span data-ttu-id="090a6-128">`Times` 데이터 형식이 정수가 아니고 DT_I2 데이터 형식으로의 명시적 캐스트가 식에 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="090a6-128">`Times` has a noninteger data type and the expression includes an explicit cast to the DT_I2 data type.</span></span> <span data-ttu-id="090a6-129">`Name` 이 `Touring Front Wheel` 이고 `Times` 가 `4.32`인 경우 RIGHT 함수가 값 4.32를 4로 변환하고 오른쪽에서부터 4개 문자를 반환하므로 반환 결과는 `"heel"` 입니다.</span><span class="sxs-lookup"><span data-stu-id="090a6-129">If `Name` is `Touring Front Wheel` and `Times` is `4.32`, the return result is `"heel"` because the RIGHT function converts the value of 4.32 to 4, and then returns the rightmost four characters.</span></span>  
  
```  
RIGHT(Name, (DT_I2)@Times))  
```  
  
## <a name="see-also"></a><span data-ttu-id="090a6-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="090a6-130">See Also</span></span>  
 <span data-ttu-id="090a6-131">[LEFT&#40;SSIS 식&#41;](left-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="090a6-131">[LEFT &#40;SSIS Expression&#41;](left-ssis-expression.md) </span></span>  
 [<span data-ttu-id="090a6-132">함수&#40;SSIS 식&#41;</span><span class="sxs-lookup"><span data-stu-id="090a6-132">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
