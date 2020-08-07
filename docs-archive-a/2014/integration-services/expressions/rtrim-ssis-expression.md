---
title: RTRIM(SSIS 식) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- RTRIM function
- trailing blanks
ms.assetid: 529bd43e-3f8a-4682-a33e-569176aa7fc4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 727c30fd72bfca5676b71f4ba42e936a9b926817
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732804"
---
# <a name="rtrim-ssis-expression"></a><span data-ttu-id="1a6ab-102">RTRIM(SSIS 식)</span><span class="sxs-lookup"><span data-stu-id="1a6ab-102">RTRIM (SSIS Expression)</span></span>
  <span data-ttu-id="1a6ab-103">후행 공백을 제거하고 문자 식을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="1a6ab-103">Returns a character expression after removing trailing spaces.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1a6ab-104">RTRIM은 탭이나 줄 바꿈 문자와 같은 공백 문자를 제거하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1a6ab-104">RTRIM does not remove white space characters such as the tab or line feed characters.</span></span> <span data-ttu-id="1a6ab-105">유니코드는 많은 다른 공백 유형에 대해 코드 포인트를 제공하지만 이 함수는 유니코드 코드 포인트 0x0020만 인식합니다.</span><span class="sxs-lookup"><span data-stu-id="1a6ab-105">Unicode provides code points for many different types of spaces, but this function recognizes only the Unicode code point 0x0020.</span></span> <span data-ttu-id="1a6ab-106">DBCS(더블바이트 문자 집합) 문자열이 유니코드로 변환될 때 0x0020이 아닌 공백 문자를 포함할 수도 있는데 이 함수에서는 이러한 공백을 제거할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1a6ab-106">When double-byte character set (DBCS) strings are converted to Unicode they may include space characters other than 0x0020 and the function cannot remove such spaces.</span></span> <span data-ttu-id="1a6ab-107">모든 종류의 공백을 제거하려면 스크립트 구성 요소의 스크립트 실행에서 Microsoft Visual Basic .NET RTrim 메서드를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1a6ab-107">To remove all kinds of spaces, you can use the Microsoft Visual Basic .NET RTrim method in a script run from the Script component.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a6ab-108">구문</span><span class="sxs-lookup"><span data-stu-id="1a6ab-108">Syntax</span></span>  
  
```  
  
RTRIM(character expression)  
```  
  
## <a name="arguments"></a><span data-ttu-id="1a6ab-109">인수</span><span class="sxs-lookup"><span data-stu-id="1a6ab-109">Arguments</span></span>  
 <span data-ttu-id="1a6ab-110">*character_expression*</span><span class="sxs-lookup"><span data-stu-id="1a6ab-110">*character_expression*</span></span>  
 <span data-ttu-id="1a6ab-111">공백을 제거할 문자 식입니다.</span><span class="sxs-lookup"><span data-stu-id="1a6ab-111">Is a character expression from which to remove spaces.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="1a6ab-112">결과 형식</span><span class="sxs-lookup"><span data-stu-id="1a6ab-112">Result Types</span></span>  
 <span data-ttu-id="1a6ab-113">DT_WSTR</span><span class="sxs-lookup"><span data-stu-id="1a6ab-113">DT_WSTR</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1a6ab-114">설명</span><span class="sxs-lookup"><span data-stu-id="1a6ab-114">Remarks</span></span>  
 <span data-ttu-id="1a6ab-115">RTRIM은 DT_WSTR 데이터 형식에서만 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="1a6ab-115">RTRIM works only with the DT_WSTR data type.</span></span> <span data-ttu-id="1a6ab-116">문자열 리터럴이나 DT_STR 데이터 형식의 데이터 열인 *character_expression* 인수는 RTRIM이 연산을 수행하기 전에 DT_WSTR 데이터 형식으로 암시적으로 캐스팅됩니다.</span><span class="sxs-lookup"><span data-stu-id="1a6ab-116">A *character_expression* argument that is a string literal or a data column with the DT_STR data type is implicitly cast to the DT_WSTR data type before RTRIM performs its operation.</span></span> <span data-ttu-id="1a6ab-117">다른 데이터 형식은 DT_WSTR 데이터 형식으로 명시적으로 캐스팅되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a6ab-117">Other data types must be explicitly cast to the DT_WSTR data type.</span></span> <span data-ttu-id="1a6ab-118">자세한 내용은 [Integration Services 데이터 형식](../data-flow/integration-services-data-types.md) 및 [캐스트&#40;SSIS 식&#41;](cast-ssis-expression.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1a6ab-118">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md) and [Cast &#40;SSIS Expression&#41;](cast-ssis-expression.md).</span></span>  
  
 <span data-ttu-id="1a6ab-119">인수가 Null이면 RTRIM 결과도 Null입니다.</span><span class="sxs-lookup"><span data-stu-id="1a6ab-119">RTRIM returns a null result if the argument is null.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="1a6ab-120">식 예</span><span class="sxs-lookup"><span data-stu-id="1a6ab-120">Expression Examples</span></span>  
 <span data-ttu-id="1a6ab-121">이 예에서는 문자열 리터럴에서 후행 공백을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="1a6ab-121">This example removes trailing spaces from a string literal.</span></span> <span data-ttu-id="1a6ab-122">반환 결과는 "Hello"입니다.</span><span class="sxs-lookup"><span data-stu-id="1a6ab-122">The return result is "Hello".</span></span>  
  
```  
RTRIM("Hello   ")  
```  
  
 <span data-ttu-id="1a6ab-123">이 예에서는 **FirstName** 열과 **LastName** 열의 연결에서 후행 공백을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="1a6ab-123">This example removes trailing spaces from a concatenation of the **FirstName** and **LastName** columns.</span></span>  
  
```  
RTRIM(FirstName + " " + LastName)  
```  
  
 <span data-ttu-id="1a6ab-124">이 예에서는 **FirstName** 변수에서 후행 공백을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="1a6ab-124">This example removes trailing spaces from the **FirstName** variable.</span></span>  
  
```  
RTRIM(@FirstName)  
```  
  
## <a name="see-also"></a><span data-ttu-id="1a6ab-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1a6ab-125">See Also</span></span>  
 <span data-ttu-id="1a6ab-126">[LTRIM&#40;SSIS 식&#41;](trim-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="1a6ab-126">[LTRIM &#40;SSIS Expression&#41;](trim-ssis-expression.md) </span></span>  
 <span data-ttu-id="1a6ab-127">[TRIM&#40;SSIS 식&#41;](trim-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="1a6ab-127">[TRIM &#40;SSIS Expression&#41;](trim-ssis-expression.md) </span></span>  
 [<span data-ttu-id="1a6ab-128">함수&#40;SSIS 식&#41;</span><span class="sxs-lookup"><span data-stu-id="1a6ab-128">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
