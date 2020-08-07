---
title: UPPER(SSIS 식) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- UPPER function
- converting lowercase to uppercase
- uppercase characters [Integration Services]
- lowercase characters
ms.assetid: d33985f7-1048-4023-83e4-274090acda78
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 181e231d735a8e98cd2bce10c692e35668a686f2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732752"
---
# <a name="upper-ssis-expression"></a><span data-ttu-id="70acb-102">UPPER(SSIS 식)</span><span class="sxs-lookup"><span data-stu-id="70acb-102">UPPER (SSIS Expression)</span></span>
  <span data-ttu-id="70acb-103">소문자를 대문자로 변환한 후에 문자 식을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="70acb-103">Returns a character expression after converting lowercase characters to uppercase characters.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70acb-104">구문</span><span class="sxs-lookup"><span data-stu-id="70acb-104">Syntax</span></span>  
  
```  
  
UPPER(character_expression)  
```  
  
## <a name="arguments"></a><span data-ttu-id="70acb-105">인수</span><span class="sxs-lookup"><span data-stu-id="70acb-105">Arguments</span></span>  
 <span data-ttu-id="70acb-106">*character_expression*</span><span class="sxs-lookup"><span data-stu-id="70acb-106">*character_expression*</span></span>  
 <span data-ttu-id="70acb-107">대문자로 변환할 문자 식입니다.</span><span class="sxs-lookup"><span data-stu-id="70acb-107">Is a character expression to convert to uppercase characters.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="70acb-108">결과 형식</span><span class="sxs-lookup"><span data-stu-id="70acb-108">Result Types</span></span>  
 <span data-ttu-id="70acb-109">DT_WSTR</span><span class="sxs-lookup"><span data-stu-id="70acb-109">DT_WSTR</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="70acb-110">설명</span><span class="sxs-lookup"><span data-stu-id="70acb-110">Remarks</span></span>  
 <span data-ttu-id="70acb-111">UPPER는 DT_WSTR 데이터 형식에서만 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="70acb-111">UPPER works only with the DT_WSTR data type.</span></span> <span data-ttu-id="70acb-112">문자열 리터럴이나 DT_STR 데이터 형식의 데이터 열인 *character_expression* 인수는 UPPER이 연산을 수행하기 전에 DT_WSTR 데이터 형식으로 암시적으로 캐스팅됩니다.</span><span class="sxs-lookup"><span data-stu-id="70acb-112">A *character_expression* argument that is a string literal or a data column with the DT_STR data type is implicitly cast to the DT_WSTR data type before UPPER performs its operation.</span></span> <span data-ttu-id="70acb-113">다른 데이터 형식은 DT_WSTR 데이터 형식으로 명시적으로 캐스팅되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="70acb-113">Other data types must be explicitly cast to the DT_WSTR data type.</span></span> <span data-ttu-id="70acb-114">자세한 내용은 [Integration Services 데이터 형식](../data-flow/integration-services-data-types.md) 및 [캐스트&#40;SSIS 식&#41;](cast-ssis-expression.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="70acb-114">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md) and [Cast &#40;SSIS Expression&#41;](cast-ssis-expression.md).</span></span>  
  
 <span data-ttu-id="70acb-115">인수가 Null이면 UPPER 결과도 Null입니다.</span><span class="sxs-lookup"><span data-stu-id="70acb-115">UPPER returns a null result if the argument is null.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="70acb-116">식 예</span><span class="sxs-lookup"><span data-stu-id="70acb-116">Expression Examples</span></span>  
 <span data-ttu-id="70acb-117">이 예에서는 문자열 리터럴을 대문자로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="70acb-117">This example converts a string literal to uppercase characters.</span></span> <span data-ttu-id="70acb-118">반환 결과는 "HELLO"입니다.</span><span class="sxs-lookup"><span data-stu-id="70acb-118">The return result is "HELLO".</span></span>  
  
```  
UPPER("hello")  
```  
  
 <span data-ttu-id="70acb-119">이 예에서는 **FirstName** 열의 첫 문자를 대문자로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="70acb-119">This example converts the first character in the **FirstName** column to an uppercase character.</span></span> <span data-ttu-id="70acb-120">**FirstName** 이 anna이면 반환 결과는 "A"입니다.</span><span class="sxs-lookup"><span data-stu-id="70acb-120">If **FirstName** is anna, the return result is "A".</span></span> <span data-ttu-id="70acb-121">자세한 내용은 [SUBSTRING&#40;SSIS 식&#41;](substring-ssis-expression.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="70acb-121">For more information, see [SUBSTRING &#40;SSIS Expression&#41;](substring-ssis-expression.md).</span></span>  
  
```  
UPPER(SUBSTRING(FirstName, 1, 1))  
```  
  
 <span data-ttu-id="70acb-122">이 예에서는 **PostalCode** 변수 값을 대문자로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="70acb-122">This example converts the value in the **PostalCode** variable to uppercase characters.</span></span> <span data-ttu-id="70acb-123">**PostalCode** 이 k4b1s2이면 반환 결과는 "K4B1S2"입니다.</span><span class="sxs-lookup"><span data-stu-id="70acb-123">If **PostalCode** is k4b1s2, the return result is "K4B1S2".</span></span>  
  
```  
UPPER(@PostalCode)  
```  
  
## <a name="see-also"></a><span data-ttu-id="70acb-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="70acb-124">See Also</span></span>  
 <span data-ttu-id="70acb-125">[LOWER&#40;SSIS 식&#41;](lower-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="70acb-125">[LOWER &#40;SSIS Expression&#41;](lower-ssis-expression.md) </span></span>  
 [<span data-ttu-id="70acb-126">함수&#40;SSIS 식&#41;</span><span class="sxs-lookup"><span data-stu-id="70acb-126">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
