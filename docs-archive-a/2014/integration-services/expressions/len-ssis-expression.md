---
title: LEN(SSIS 식) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- LEN function
- number of characters
ms.assetid: d961398b-e4d0-4936-be17-8f4c5882a640
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8863864168295a3a9a924df588312ee65b6f7fa7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649594"
---
# <a name="len-ssis-expression"></a><span data-ttu-id="e7a34-102">LEN(SSIS 식)</span><span class="sxs-lookup"><span data-stu-id="e7a34-102">LEN (SSIS Expression)</span></span>
  <span data-ttu-id="e7a34-103">문자 식에 포함된 문자의 수를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="e7a34-103">Returns the number of characters in a character expression.</span></span> <span data-ttu-id="e7a34-104">문자열에 선행 및 후행 공백이 포함되어 있으면 공백도 개수에 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="e7a34-104">If the string includes leading and trailing blanks, the function includes them in the count.</span></span> <span data-ttu-id="e7a34-105">LEN은 싱글바이트 및 더블바이트 문자의 동일한 문자열에 대해 같은 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="e7a34-105">LEN returns identical values for the same string of single and double byte characters.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7a34-106">구문</span><span class="sxs-lookup"><span data-stu-id="e7a34-106">Syntax</span></span>  
  
```  
  
LEN(character_expression)  
```  
  
## <a name="arguments"></a><span data-ttu-id="e7a34-107">인수</span><span class="sxs-lookup"><span data-stu-id="e7a34-107">Arguments</span></span>  
 <span data-ttu-id="e7a34-108">*character_expression*</span><span class="sxs-lookup"><span data-stu-id="e7a34-108">*character_expression*</span></span>  
 <span data-ttu-id="e7a34-109">계산할 식입니다.</span><span class="sxs-lookup"><span data-stu-id="e7a34-109">Is the expression to evaluate.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="e7a34-110">결과 형식</span><span class="sxs-lookup"><span data-stu-id="e7a34-110">Result Types</span></span>  
 <span data-ttu-id="e7a34-111">DT_I4</span><span class="sxs-lookup"><span data-stu-id="e7a34-111">DT_I4</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e7a34-112">설명</span><span class="sxs-lookup"><span data-stu-id="e7a34-112">Remarks</span></span>  
 <span data-ttu-id="e7a34-113">*character_expression* 인수는 DT_WSTR, DT_TEXT, DT_NTEXT 또는 DT_IMAGE 데이터 형식일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e7a34-113">The *character_expression* argument can be a DT_WSTR, DT_TEXT, DT_NTEXT, or DT_IMAGE data type.</span></span> <span data-ttu-id="e7a34-114">자세한 내용은 [Integration Services Data Types](../data-flow/integration-services-data-types.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e7a34-114">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
 <span data-ttu-id="e7a34-115">*character_expression* 이 문자열 리터럴 또는 DT_STR 데이터 형식의 데이터 열인 경우 LEN이 연산을 수행하기 전에 DT_WSTR 데이터 형식으로 암시적으로 캐스팅됩니다.</span><span class="sxs-lookup"><span data-stu-id="e7a34-115">If *character_expression* is a string literal or a data column with the DT_STR data type, it is implicitly cast to the DT_WSTR data type before LEN performs its operation.</span></span> <span data-ttu-id="e7a34-116">다른 데이터 형식은 DT_WSTR 데이터 형식으로 명시적으로 캐스팅되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e7a34-116">Other data types must be explicitly cast to the DT_WSTR data type.</span></span> <span data-ttu-id="e7a34-117">자세한 내용은 [캐스트&#40;SSIS 식&#41;](cast-ssis-expression.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e7a34-117">For more information, see [Cast &#40;SSIS Expression&#41;](cast-ssis-expression.md).</span></span>  
  
 <span data-ttu-id="e7a34-118">LEN 함수로 전달된 인수가 DT_TEXT, DT_NTEXT 또는 DT_IMAGE와 같은 BLOB(Binary Large Object Block) 데이터 형식이면 1바이트 개수가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="e7a34-118">If the argument passed to the LEN function has a Binary Large Object Block (BLOB) data type, such as DT_TEXT, DT_NTEXT, or DT_IMAGE, the function returns a byte count.</span></span>  
  
 <span data-ttu-id="e7a34-119">인수가 Null이면 LEN 결과도 Null입니다.</span><span class="sxs-lookup"><span data-stu-id="e7a34-119">LEN returns a null result if the argument is null.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="e7a34-120">식 예</span><span class="sxs-lookup"><span data-stu-id="e7a34-120">Expression Examples</span></span>  
 <span data-ttu-id="e7a34-121">이 예에서는 문자열 리터럴의 길이를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="e7a34-121">This example returns the length of a string literal.</span></span> <span data-ttu-id="e7a34-122">반환 결과는 12입니다.</span><span class="sxs-lookup"><span data-stu-id="e7a34-122">The return result is 12.</span></span>  
  
```  
LEN("Ball Bearing")  
```  
  
 <span data-ttu-id="e7a34-123">이 예에서는 **FirstName** 열과 **LastName** 열의 값 길이의 차이를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="e7a34-123">This example returns the difference between the length of values in the **FirstName** and **LastName** columns.</span></span>  
  
```  
LEN(FirstName) - LEN(LastName)  
```  
  
 <span data-ttu-id="e7a34-124">시스템 변수 **MachineName**을 사용하여 컴퓨터 이름의 길이를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="e7a34-124">Returns the length of a computer name using the System variable **MachineName**.</span></span>  
  
```  
LEN(@MachineName)  
```  
  
## <a name="see-also"></a><span data-ttu-id="e7a34-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e7a34-125">See Also</span></span>  
 [<span data-ttu-id="e7a34-126">함수&#40;SSIS 식&#41;</span><span class="sxs-lookup"><span data-stu-id="e7a34-126">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
