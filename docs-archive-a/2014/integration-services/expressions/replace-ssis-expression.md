---
title: REPLACE(SSIS 식) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- replacing string expression
- REPLACE function
ms.assetid: a6837043-ea70-4c6a-9c7a-6868b02b2adc
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e483ba6c9c72cb777f2955929a717c6c2e17a8c5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732823"
---
# <a name="replace-ssis-expression"></a><span data-ttu-id="85be5-102">REPLACE(SSIS 식)</span><span class="sxs-lookup"><span data-stu-id="85be5-102">REPLACE (SSIS Expression)</span></span>
  <span data-ttu-id="85be5-103">식 내의 문자열을 다른 문자열이나 빈 문자열로 바꾼 후 문자 식을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="85be5-103">Returns a character expression after replacing a character string within the expression with either a different character string or an empty string.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="85be5-104">REPLACE 함수는 주로 긴 문자열을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="85be5-104">The REPLACE function frequently uses long strings.</span></span> <span data-ttu-id="85be5-105">잘림 결과가 적절하게 처리될 수 있지만 경고나 오류를 일으킬 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="85be5-105">The consequences of truncation can be handled gracefully or cause a warning or an error.</span></span> <span data-ttu-id="85be5-106">자세한 내용은 [구문&#40;SSIS&#41;](syntax-ssis.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="85be5-106">For more information, see [Syntax &#40;SSIS&#41;](syntax-ssis.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85be5-107">구문</span><span class="sxs-lookup"><span data-stu-id="85be5-107">Syntax</span></span>  
  
```  
  
REPLACE(character_expression,searchstring,replacementstring)  
```  
  
## <a name="arguments"></a><span data-ttu-id="85be5-108">인수</span><span class="sxs-lookup"><span data-stu-id="85be5-108">Arguments</span></span>  
 <span data-ttu-id="85be5-109">*character_expression*</span><span class="sxs-lookup"><span data-stu-id="85be5-109">*character_expression*</span></span>  
 <span data-ttu-id="85be5-110">함수가 검색하는 유효한 문자 식입니다.</span><span class="sxs-lookup"><span data-stu-id="85be5-110">Is a valid character expression that the function searches.</span></span>  
  
 <span data-ttu-id="85be5-111">*searchstring*</span><span class="sxs-lookup"><span data-stu-id="85be5-111">*searchstring*</span></span>  
 <span data-ttu-id="85be5-112">함수가 검색하는 유효한 문자 식입니다.</span><span class="sxs-lookup"><span data-stu-id="85be5-112">Is a valid character expression that the function attempts to locate.</span></span>  
  
 <span data-ttu-id="85be5-113">*replacementstring*</span><span class="sxs-lookup"><span data-stu-id="85be5-113">*replacementstring*</span></span>  
 <span data-ttu-id="85be5-114">대체 식인 유효한 문자 식입니다.</span><span class="sxs-lookup"><span data-stu-id="85be5-114">Is a valid character expression that is the replacement expression.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="85be5-115">결과 형식</span><span class="sxs-lookup"><span data-stu-id="85be5-115">Result Types</span></span>  
 <span data-ttu-id="85be5-116">DT_WSTR</span><span class="sxs-lookup"><span data-stu-id="85be5-116">DT_WSTR</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="85be5-117">설명</span><span class="sxs-lookup"><span data-stu-id="85be5-117">Remarks</span></span>  
 <span data-ttu-id="85be5-118">*searchstring* 길이는 0이 아니어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="85be5-118">The length of *searchstring* must not be zero.</span></span>  
  
 <span data-ttu-id="85be5-119">*replacementstring* 길이는 0이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="85be5-119">The length of *replacementstring* may be zero.</span></span>  
  
 <span data-ttu-id="85be5-120">*searchstring* 및 *replacementstring* 인수는 변수와 열을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="85be5-120">The *searchstring* and *replacementstring* arguments can use variables and columns.</span></span>  
  
 <span data-ttu-id="85be5-121">REPLACE는 DT_WSTR 데이터 형식에서만 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="85be5-121">REPLACE works only with the DT_WSTR data type.</span></span> <span data-ttu-id="85be5-122">DT_STR 데이터 형식인 문자열 리터럴 및 데이터 열인*character_expression1, character_expression2* 및 *character_expression3* 인수는 REPLACE 연산이 수행되기 전에 DT_WSTR 데이터 형식으로 암시적으로 캐스팅됩니다.</span><span class="sxs-lookup"><span data-stu-id="85be5-122">*character_expression1, character_expression2,* and *character_expression3* arguments that are string literals or data columns with the DT_STR data type are implicitly cast to the DT_WSTR data type before REPLACE performs its operation.</span></span> <span data-ttu-id="85be5-123">다른 데이터 형식은 DT_WSTR 데이터 형식으로 명시적으로 캐스팅되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="85be5-123">Other data types must be explicitly cast to the DT_WSTR data type.</span></span> <span data-ttu-id="85be5-124">자세한 내용은 [캐스트&#40;SSIS 식&#41;](cast-ssis-expression.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="85be5-124">For more information, see [Cast &#40;SSIS Expression&#41;](cast-ssis-expression.md).</span></span>  
  
 <span data-ttu-id="85be5-125">인수가 Null이면 REPLACE 결과도 Null입니다.</span><span class="sxs-lookup"><span data-stu-id="85be5-125">REPLACE returns a null result if any argument is null.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="85be5-126">식 예</span><span class="sxs-lookup"><span data-stu-id="85be5-126">Expression Examples</span></span>  
 <span data-ttu-id="85be5-127">이 예에서는 문자열 리터럴을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="85be5-127">This example uses a string literal.</span></span> <span data-ttu-id="85be5-128">반환 결과는 "All Terrain Bike"입니다.</span><span class="sxs-lookup"><span data-stu-id="85be5-128">The return result is "All Terrain Bike".</span></span>  
  
```  
REPLACE("Mountain Bike", "Mountain","All Terrain")  
```  
  
 <span data-ttu-id="85be5-129">이 예에서는 **Product** 열에서 문자열 "Bike"를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="85be5-129">This example removes the string "Bike" from the **Product** column.</span></span>  
  
```  
REPLACE(Product, "Bike","")  
```  
  
 <span data-ttu-id="85be5-130">이 예에서는 **DaysToManufacture** 열의 값을 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="85be5-130">This example replaces values in the **DaysToManufacture** column.</span></span> <span data-ttu-id="85be5-131">열에는 정수 데이터 형식이 있고 식에는 DT_WSTR 데이터 형식으로의 **DaysToManufacture** 캐스팅이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="85be5-131">The column has an integer data type and the expression includes casting **DaysToManufacture** to the DT_WSTR data type.</span></span>  
  
```  
REPLACE((DT_WSTR,8)DaysToManufacture,"6","5")  
```  
  
## <a name="see-also"></a><span data-ttu-id="85be5-132">참고 항목</span><span class="sxs-lookup"><span data-stu-id="85be5-132">See Also</span></span>  
 <span data-ttu-id="85be5-133">[SUBSTRING&#40;SSIS 식&#41;](substring-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="85be5-133">[SUBSTRING &#40;SSIS Expression&#41;](substring-ssis-expression.md) </span></span>  
 [<span data-ttu-id="85be5-134">함수&#40;SSIS 식&#41;</span><span class="sxs-lookup"><span data-stu-id="85be5-134">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
