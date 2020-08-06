---
title: LTRIM(SSIS 식) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- leading blanks
- LTRIM function
ms.assetid: d082f42a-d7e7-49f5-a503-ac44ba630832
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 678d9d93eb1dcd7649d2085b651a08418bbcd6a1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650195"
---
# <a name="ltrim-ssis-expression"></a><span data-ttu-id="73180-102">LTRIM(SSIS 식)</span><span class="sxs-lookup"><span data-stu-id="73180-102">LTRIM (SSIS Expression)</span></span>
  <span data-ttu-id="73180-103">선행 공백을 제거하고 문자 식을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="73180-103">Returns a character expression after removing leading spaces.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="73180-104">LTRIM은 탭이나 줄 바꿈 문자와 같은 공백 문자를 제거하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="73180-104">LTRIM does not remove white-space characters such as the tab or line feed characters.</span></span> <span data-ttu-id="73180-105">유니코드는 많은 다른 공백 유형에 대해 코드 포인트를 제공하지만 이 함수는 유니코드 코드 포인트 0x0020만 인식합니다.</span><span class="sxs-lookup"><span data-stu-id="73180-105">Unicode provides code points for many different types of spaces, but this function recognizes only the Unicode code point 0x0020.</span></span> <span data-ttu-id="73180-106">DBCS(더블바이트 문자 집합) 문자열이 유니코드로 변환될 때 0x0020이 아닌 공백 문자를 포함할 수도 있는데 이 함수에서는 이러한 공백을 제거할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="73180-106">When double-byte character set (DBCS) strings are converted to Unicode they may include space characters other than 0x0020 and the function cannot remove such spaces.</span></span> <span data-ttu-id="73180-107">모든 종류의 공백을 제거하려면 스크립트 구성 요소의 스크립트 실행에서 Microsoft Visual Basic .NET LTrim 메서드를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73180-107">To remove all kinds of spaces, you can use the Microsoft Visual Basic .NET LTrim method in a script run from the Script component.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73180-108">구문</span><span class="sxs-lookup"><span data-stu-id="73180-108">Syntax</span></span>  
  
```  
  
LTRIM(character expression)  
```  
  
## <a name="arguments"></a><span data-ttu-id="73180-109">인수</span><span class="sxs-lookup"><span data-stu-id="73180-109">Arguments</span></span>  
 <span data-ttu-id="73180-110">*character_expression*</span><span class="sxs-lookup"><span data-stu-id="73180-110">*character_expression*</span></span>  
 <span data-ttu-id="73180-111">공백을 제거할 문자 식입니다.</span><span class="sxs-lookup"><span data-stu-id="73180-111">Is a character expression from which to remove spaces.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="73180-112">결과 형식</span><span class="sxs-lookup"><span data-stu-id="73180-112">Result Types</span></span>  
 <span data-ttu-id="73180-113">DT_WSTR</span><span class="sxs-lookup"><span data-stu-id="73180-113">DT_WSTR</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="73180-114">설명</span><span class="sxs-lookup"><span data-stu-id="73180-114">Remarks</span></span>  
 <span data-ttu-id="73180-115">LTRIM은 DT_WSTR 데이터 형식에서만 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="73180-115">LTRIM works only with the DT_WSTR data type.</span></span> <span data-ttu-id="73180-116">문자열 리터럴이나 DT_STR 데이터 형식의 데이터 열인 *character_expression* 인수는 LTRIM이 연산을 수행하기 전에 DT_WSTR 데이터 형식으로 암시적으로 캐스팅됩니다.</span><span class="sxs-lookup"><span data-stu-id="73180-116">A *character_expression* argument that is a string literal or a data column with the DT_STR data type is implicitly cast to the DT_WSTR data type before LTRIM performs its operation.</span></span> <span data-ttu-id="73180-117">다른 데이터 형식은 DT_WSTR 데이터 형식으로 명시적으로 캐스팅되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="73180-117">Other data types must be explicitly cast to the DT_WSTR data type.</span></span> <span data-ttu-id="73180-118">자세한 내용은 [Integration Services 데이터 형식](../data-flow/integration-services-data-types.md) 및 [캐스트&#40;SSIS 식&#41;](cast-ssis-expression.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="73180-118">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md) and [Cast &#40;SSIS Expression&#41;](cast-ssis-expression.md).</span></span>  
  
 <span data-ttu-id="73180-119">인수가 Null이면 LTRIM 결과도 Null입니다.</span><span class="sxs-lookup"><span data-stu-id="73180-119">LTRIM returns a null result if the argument is null.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="73180-120">식 예</span><span class="sxs-lookup"><span data-stu-id="73180-120">Expression Examples</span></span>  
 <span data-ttu-id="73180-121">이 예에서는 문자열 리터럴에서 선행 공백을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="73180-121">This example removes leading spaces from a string literal.</span></span> <span data-ttu-id="73180-122">반환 결과는 "Hello"입니다.</span><span class="sxs-lookup"><span data-stu-id="73180-122">The return result is "Hello".</span></span>  
  
```  
LTRIM("    Hello")  
```  
  
 <span data-ttu-id="73180-123">이 예에서는 **FirstName** 열에서 선행 공백을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="73180-123">This example removes leading spaces from the **FirstName** column.</span></span>  
  
```  
LTRIM(FirstName)  
```  
  
 <span data-ttu-id="73180-124">이 예에서는 **FirstName** 변수에서 선행 공백을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="73180-124">This example removes leading spaces from the **FirstName** variable.</span></span>  
  
```  
LTRIM(@FirstName)  
```  
  
## <a name="see-also"></a><span data-ttu-id="73180-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="73180-125">See Also</span></span>  
 <span data-ttu-id="73180-126">[RTRIM&#40;SSIS 식&#41;](trim-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="73180-126">[RTRIM &#40;SSIS Expression&#41;](trim-ssis-expression.md) </span></span>  
 <span data-ttu-id="73180-127">[TRIM&#40;SSIS 식&#41;](trim-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="73180-127">[TRIM &#40;SSIS Expression&#41;](trim-ssis-expression.md) </span></span>  
 [<span data-ttu-id="73180-128">함수&#40;SSIS 식&#41;</span><span class="sxs-lookup"><span data-stu-id="73180-128">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
