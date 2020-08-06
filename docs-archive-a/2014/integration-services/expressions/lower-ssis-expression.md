---
title: LOWER(SSIS 식) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- converting uppercase to lowercase
- LOWER function
- uppercase characters [Integration Services]
- lowercase characters
ms.assetid: 109328e1-5604-40ff-895e-f2e7c13fff41
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 180be8f3cfb5a15eb0fcd6ddd3d63b09fe874af5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650197"
---
# <a name="lower-ssis-expression"></a><span data-ttu-id="55b70-102">LOWER(SSIS 식)</span><span class="sxs-lookup"><span data-stu-id="55b70-102">LOWER (SSIS Expression)</span></span>
  <span data-ttu-id="55b70-103">대문자를 소문자로 변환한 후에 문자 식을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="55b70-103">Returns a character expression after converting uppercase characters to lowercase characters.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55b70-104">구문</span><span class="sxs-lookup"><span data-stu-id="55b70-104">Syntax</span></span>  
  
```  
  
LOWER(character_expression)  
```  
  
## <a name="arguments"></a><span data-ttu-id="55b70-105">인수</span><span class="sxs-lookup"><span data-stu-id="55b70-105">Arguments</span></span>  
 <span data-ttu-id="55b70-106">*character_expression*</span><span class="sxs-lookup"><span data-stu-id="55b70-106">*character_expression*</span></span>  
 <span data-ttu-id="55b70-107">소문자로 변환할 문자 식입니다.</span><span class="sxs-lookup"><span data-stu-id="55b70-107">Is a character expression to convert to lowercase characters.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="55b70-108">결과 형식</span><span class="sxs-lookup"><span data-stu-id="55b70-108">Result Types</span></span>  
 <span data-ttu-id="55b70-109">DT_WSTR</span><span class="sxs-lookup"><span data-stu-id="55b70-109">DT_WSTR</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="55b70-110">설명</span><span class="sxs-lookup"><span data-stu-id="55b70-110">Remarks</span></span>  
 <span data-ttu-id="55b70-111">LOWER는 DT_WSTR 데이터 형식에서만 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="55b70-111">LOWER works only with the DT_WSTR data type.</span></span> <span data-ttu-id="55b70-112">문자열 리터럴이나 DT_STR 데이터 형식의 데이터 열인 *character_expression* 인수는 LOWER가 연산을 수행하기 전에 DT_WSTR 데이터 형식으로 암시적으로 캐스팅됩니다.</span><span class="sxs-lookup"><span data-stu-id="55b70-112">A *character_expression* argument that is a string literal or a data column with the DT_STR data type is implicitly cast to the DT_WSTR data type before LOWER performs its operation.</span></span> <span data-ttu-id="55b70-113">다른 데이터 형식은 DT_WSTR 데이터 형식으로 명시적으로 캐스팅되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="55b70-113">Other data types must be explicitly cast to the DT_WSTR data type.</span></span> <span data-ttu-id="55b70-114">자세한 내용은 [Integration Services 데이터 형식](../data-flow/integration-services-data-types.md) 및 [캐스트&#40;SSIS 식&#41;](cast-ssis-expression.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="55b70-114">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md) and [Cast &#40;SSIS Expression&#41;](cast-ssis-expression.md).</span></span>  
  
 <span data-ttu-id="55b70-115">인수가 Null이면 LOWER 결과도 Null입니다.</span><span class="sxs-lookup"><span data-stu-id="55b70-115">LOWER returns a null result if the argument is null.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="55b70-116">식 예</span><span class="sxs-lookup"><span data-stu-id="55b70-116">Expression Examples</span></span>  
 <span data-ttu-id="55b70-117">이 예에서는 문자열 리터럴을 소문자로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="55b70-117">This example converts a string literal to lowercase characters.</span></span> <span data-ttu-id="55b70-118">반환 결과는 "new york"입니다.</span><span class="sxs-lookup"><span data-stu-id="55b70-118">The return result is "new york".</span></span>  
  
```  
LOWER("New York")  
```  
  
 <span data-ttu-id="55b70-119">이 예에서는 첫 문자를 제외하고 **Color** 입력 열의 모든 문자를 소문자로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="55b70-119">This example converts all characters from the **Color** input column, except the first character, to lowercase characters.</span></span> <span data-ttu-id="55b70-120">Color가 YELLOW이면 반환 결과는 "Yellow"입니다.</span><span class="sxs-lookup"><span data-stu-id="55b70-120">If Color is YELLOW, the return result is "Yellow".</span></span> <span data-ttu-id="55b70-121">자세한 내용은 [SUBSTRING&#40;SSIS 식&#41;](substring-ssis-expression.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="55b70-121">For more information, see [SUBSTRING &#40;SSIS Expression&#41;](substring-ssis-expression.md).</span></span>  
  
```  
LOWER(SUBSTRING(Color, 2, 15))  
```  
  
 <span data-ttu-id="55b70-122">이 예에서는 **CityName** 변수 값을 소문자로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="55b70-122">This example converts the value in the **CityName** variable to lowercase characters.</span></span>  
  
```  
LOWER(@CityName)  
```  
  
## <a name="see-also"></a><span data-ttu-id="55b70-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="55b70-123">See Also</span></span>  
 <span data-ttu-id="55b70-124">[UPPER&#40;SSIS 식&#41;](upper-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="55b70-124">[UPPER &#40;SSIS Expression&#41;](upper-ssis-expression.md) </span></span>  
 [<span data-ttu-id="55b70-125">함수&#40;SSIS 식&#41;</span><span class="sxs-lookup"><span data-stu-id="55b70-125">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
