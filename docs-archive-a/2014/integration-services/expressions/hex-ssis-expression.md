---
title: HEX(SSIS 식) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- hexadecimal data
- HEX function
ms.assetid: f5d471ee-aeef-421c-b6e1-55b9676c3842
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 640ae38ec5d2cd5ffb448e9aebde5ba5ceba2684
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736633"
---
# <a name="hex-ssis-expression"></a><span data-ttu-id="4ca3a-102">HEX(SSIS 식)</span><span class="sxs-lookup"><span data-stu-id="4ca3a-102">HEX (SSIS Expression)</span></span>
  <span data-ttu-id="4ca3a-103">정수의 16진수 값을 나타내는 문자열을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="4ca3a-103">Returns a string representing the hexadecimal value of an integer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ca3a-104">구문</span><span class="sxs-lookup"><span data-stu-id="4ca3a-104">Syntax</span></span>  
  
```  
  
HEX(integer_expression)  
```  
  
## <a name="arguments"></a><span data-ttu-id="4ca3a-105">인수</span><span class="sxs-lookup"><span data-stu-id="4ca3a-105">Arguments</span></span>  
 <span data-ttu-id="4ca3a-106">*integer_expression*</span><span class="sxs-lookup"><span data-stu-id="4ca3a-106">*integer_expression*</span></span>  
 <span data-ttu-id="4ca3a-107">부호 있는 정수 또는 부호 없는 정수입니다.</span><span class="sxs-lookup"><span data-stu-id="4ca3a-107">Is a signed or unsigned integer.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="4ca3a-108">결과 형식</span><span class="sxs-lookup"><span data-stu-id="4ca3a-108">Result Types</span></span>  
 <span data-ttu-id="4ca3a-109">DT_WSTR</span><span class="sxs-lookup"><span data-stu-id="4ca3a-109">DT_WSTR</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4ca3a-110">설명</span><span class="sxs-lookup"><span data-stu-id="4ca3a-110">Remarks</span></span>  
 <span data-ttu-id="4ca3a-111">*integer_expression* 이 null이면 HEX는 null을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="4ca3a-111">HEX returns null if *integer_expression* is null.</span></span>  
  
 <span data-ttu-id="4ca3a-112">*integer_expression* 인수는 정수여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4ca3a-112">The *integer_expression* argument must evaluate to an integer.</span></span> <span data-ttu-id="4ca3a-113">자세한 내용은 [Integration Services Data Types](../data-flow/integration-services-data-types.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4ca3a-113">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
 <span data-ttu-id="4ca3a-114">반환 결과는 0x 접두사와 같은 한정자를 포함하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4ca3a-114">The return result does not include qualifiers such as the 0x prefix.</span></span> <span data-ttu-id="4ca3a-115">접두사를 포함하려면 +(연결) 연산자를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="4ca3a-115">To include a prefix, use the + (Concatenate) operator.</span></span> <span data-ttu-id="4ca3a-116">자세한 내용은 [+&#40;연결&#41;&#40;SSIS 식&#41;](concatenate-ssis-expression.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4ca3a-116">For more information, see [+ &#40;Concatenate&#41; &#40;SSIS Expression&#41;](concatenate-ssis-expression.md).</span></span>  
  
 <span data-ttu-id="4ca3a-117">HEX 표기에 사용되는 문자 A - F는 대문자로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="4ca3a-117">The letters A - F, used in HEX notations, appear as uppercase characters.</span></span>  
  
 <span data-ttu-id="4ca3a-118">정수 데이터 형식의 결과 문자열 길이는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="4ca3a-118">The length of the resulting string for integer data types is as follows:</span></span>  
  
-   <span data-ttu-id="4ca3a-119">DT_I1과 DT_UI1은 최대 길이가 2인 문자열을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="4ca3a-119">DT_I1 and DT_UI1 return a string with a maximum length of 2.</span></span>  
  
-   <span data-ttu-id="4ca3a-120">DT_I2와 DT_UI2는 최대 길이가 4인 문자열을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="4ca3a-120">DT_I2 and DT_UI2 return a string with a maximum length of 4.</span></span>  
  
-   <span data-ttu-id="4ca3a-121">DT_I4와 DT_UI4는 최대 길이가 8인 문자열을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="4ca3a-121">DT_I4 and DT_UI4 return a string with a maximum length of 8.</span></span>  
  
-   <span data-ttu-id="4ca3a-122">DT_I8과 DT_UI8은 최대 길이가 16인 문자열을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="4ca3a-122">DT_I8 and DT_UI8 return a string with a maximum length of 16.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="4ca3a-123">식 예</span><span class="sxs-lookup"><span data-stu-id="4ca3a-123">Expression Examples</span></span>  
 <span data-ttu-id="4ca3a-124">이 예에서는 숫자 리터럴을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="4ca3a-124">This example uses a numeric literal.</span></span> <span data-ttu-id="4ca3a-125">이 함수는 값 190을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="4ca3a-125">The function returns the value 190.</span></span>  
  
```  
HEX(400)   
```  
  
 <span data-ttu-id="4ca3a-126">이 예에서는 **ReorderPoint** 열을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="4ca3a-126">This example uses the **ReorderPoint** column.</span></span> <span data-ttu-id="4ca3a-127">열 데이터 형식은 `smallint`입니다.</span><span class="sxs-lookup"><span data-stu-id="4ca3a-127">The column data type is `smallint`.</span></span> <span data-ttu-id="4ca3a-128">**ReorderPoint** 가 750이면 2EE를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="4ca3a-128">If **ReorderPoint** is 750, the function returns 2EE.</span></span>  
  
```  
HEX(ReorderPoint)   
```  
  
 <span data-ttu-id="4ca3a-129">이 예에서는 시스템 변수 **LocaleID**를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="4ca3a-129">This example uses **LocaleID**, a system variable.</span></span> <span data-ttu-id="4ca3a-130">**LocaleID** 가 1033이면 409를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="4ca3a-130">If **LocaleID** is 1033, the function returns 409.</span></span>  
  
```  
HEX(@LocaleID)  
```  
  
## <a name="see-also"></a><span data-ttu-id="4ca3a-131">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4ca3a-131">See Also</span></span>  
 [<span data-ttu-id="4ca3a-132">함수&#40;SSIS 식&#41;</span><span class="sxs-lookup"><span data-stu-id="4ca3a-132">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
