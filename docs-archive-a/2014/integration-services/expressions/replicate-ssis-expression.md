---
title: REPLICATE(SSIS 식) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- REPLICATE function
ms.assetid: e7a37b93-6d1d-42d5-9a65-de1790abf6a5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9502df5bc20c6ad85f1f98fb57fe6b3cf431cc20
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732816"
---
# <a name="replicate-ssis-expression"></a><span data-ttu-id="f27ce-102">REPLICATE(SSIS 식)</span><span class="sxs-lookup"><span data-stu-id="f27ce-102">REPLICATE (SSIS Expression)</span></span>
  <span data-ttu-id="f27ce-103">지정한 횟수만큼 복제된 문자 식을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="f27ce-103">Returns a character expression that is replicated a number of times.</span></span> <span data-ttu-id="f27ce-104">*times* 인수는 정수여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f27ce-104">The *times* argument must evaluate to an integer.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f27ce-105">REPLICATE 함수는 긴 문자열을 사용하므로 식 길이에서 4000자 제한에 걸릴 가능성이 큽니다.</span><span class="sxs-lookup"><span data-stu-id="f27ce-105">The REPLICATE function frequently uses long strings, and therefore is more likely to incur the 4000-character limit on expression length.</span></span> <span data-ttu-id="f27ce-106">식의 평가 결과에 Integration Services 데이터 형식 DT_WSTR 또는 DT_STR이 있는 경우 식이 4000자에서 잘립니다.</span><span class="sxs-lookup"><span data-stu-id="f27ce-106">If the evaluation result of an expression has the Integration Services data type DT_WSTR or DT_STR, the expression will be truncated at 4000 characters.</span></span> <span data-ttu-id="f27ce-107">하위 식의 결과 유형이 DT_STR 또는 DT_WSTR인 경우 전체 식 결과 유형에 관계없이 해당 하위 식이 4000자로 잘립니다.</span><span class="sxs-lookup"><span data-stu-id="f27ce-107">If the result type of a sub-expression is DT_STR or DT_WSTR, that sub-expression likewise will be truncated to 4000 characters, regardless of the overall expression result type.</span></span> <span data-ttu-id="f27ce-108">잘림 결과가 적절하게 처리될 수 있지만 경고나 오류를 일으킬 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f27ce-108">The consequences of truncation can be handled gracefully or cause a warning or an error.</span></span> <span data-ttu-id="f27ce-109">자세한 내용은 [구문&#40;SSIS&#41;](syntax-ssis.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f27ce-109">For more information, see [Syntax &#40;SSIS&#41;](syntax-ssis.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f27ce-110">구문</span><span class="sxs-lookup"><span data-stu-id="f27ce-110">Syntax</span></span>  
  
```  
  
REPLICATE(character_expression,times)  
```  
  
## <a name="arguments"></a><span data-ttu-id="f27ce-111">인수</span><span class="sxs-lookup"><span data-stu-id="f27ce-111">Arguments</span></span>  
 <span data-ttu-id="f27ce-112">*character_expression*</span><span class="sxs-lookup"><span data-stu-id="f27ce-112">*character_expression*</span></span>  
 <span data-ttu-id="f27ce-113">복제할 문자 식입니다.</span><span class="sxs-lookup"><span data-stu-id="f27ce-113">Is a character expression to replicate.</span></span>  
  
 <span data-ttu-id="f27ce-114">*times*</span><span class="sxs-lookup"><span data-stu-id="f27ce-114">*times*</span></span>  
 <span data-ttu-id="f27ce-115">*character_expression* 이 복제되는 횟수를 지정하는 정수 식입니다.</span><span class="sxs-lookup"><span data-stu-id="f27ce-115">Is an integer expression that specifies the number of times *character_expression* is replicated.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="f27ce-116">결과 형식</span><span class="sxs-lookup"><span data-stu-id="f27ce-116">Result Types</span></span>  
 <span data-ttu-id="f27ce-117">DT_WSTR</span><span class="sxs-lookup"><span data-stu-id="f27ce-117">DT_WSTR</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f27ce-118">설명</span><span class="sxs-lookup"><span data-stu-id="f27ce-118">Remarks</span></span>  
 <span data-ttu-id="f27ce-119">*times* 가 0이면 빈 문자열이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="f27ce-119">If *times* is zero, the function returns a zero-length string.</span></span>  
  
 <span data-ttu-id="f27ce-120">*times* 가 음수이면 오류가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="f27ce-120">If *times* is a negative number, the function returns an error.</span></span>  
  
 <span data-ttu-id="f27ce-121">*times* 인수는 변수와 열을 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f27ce-121">The *times* argument can also use variables and columns.</span></span>  
  
 <span data-ttu-id="f27ce-122">REPLICATE는 DT_WSTR 데이터 형식에서만 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="f27ce-122">REPLICATE works only with the DT_WSTR data type.</span></span> <span data-ttu-id="f27ce-123">문자열 리터럴이나 DT_STR 데이터 형식의 데이터 열인 *character_expression* 인수는 REPLICATE가 연산을 수행하기 전에 DT_WSTR 데이터 형식으로 암시적으로 캐스팅됩니다.</span><span class="sxs-lookup"><span data-stu-id="f27ce-123">A *character_expression* argument that is a string literal or a data column with the DT_STR data type is implicitly cast to the DT_WSTR data type before REPLICATE performs its operation.</span></span> <span data-ttu-id="f27ce-124">다른 데이터 형식은 DT_WSTR 데이터 형식으로 명시적으로 캐스팅되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f27ce-124">Other data types must be explicitly cast to the DT_WSTR data type.</span></span> <span data-ttu-id="f27ce-125">자세한 내용은 [Integration Services 데이터 형식](../data-flow/integration-services-data-types.md) 및 [캐스트&#40;SSIS 식&#41;](cast-ssis-expression.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f27ce-125">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md) and [Cast &#40;SSIS Expression&#41;](cast-ssis-expression.md).</span></span>  
  
 <span data-ttu-id="f27ce-126">두 인수 중 하나가 Null이면 REPLICATE 결과도 Null입니다.</span><span class="sxs-lookup"><span data-stu-id="f27ce-126">REPLICATE returns a null result if either argument is null.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="f27ce-127">식 예</span><span class="sxs-lookup"><span data-stu-id="f27ce-127">Expression Examples</span></span>  
 <span data-ttu-id="f27ce-128">이 예에서는 문자열 리터럴을 3번 복제합니다.</span><span class="sxs-lookup"><span data-stu-id="f27ce-128">This example replicates a string literal three times.</span></span> <span data-ttu-id="f27ce-129">반환 결과는 "Mountain BikeMountain BikeMountain Bike"입니다.</span><span class="sxs-lookup"><span data-stu-id="f27ce-129">The return result is "Mountain BikeMountain BikeMountain Bike".</span></span>  
  
```  
REPLICATE("Mountain Bike", 3)  
```  
  
 <span data-ttu-id="f27ce-130">이 예에서는 **Name** 열의 값을 **Times** 변수 값만큼 복제합니다.</span><span class="sxs-lookup"><span data-stu-id="f27ce-130">This example replicates values in the **Name** column by the value in the **Times** variable.</span></span> <span data-ttu-id="f27ce-131">**Times** 가 3이고 **Name** 이 Touring Front Wheel이면 반환 결과는 Touring Front WheelTouring Front WheelTouring Front Wheel입니다.</span><span class="sxs-lookup"><span data-stu-id="f27ce-131">If **Times** is 3 and **Name** is Touring Front Wheel, the return result is Touring Front WheelTouring Front WheelTouring Front Wheel.</span></span>  
  
```  
REPLICATE(Name, @Times)  
```  
  
 <span data-ttu-id="f27ce-132">이 예에서는 **Name** 변수 값을 **Times** 열의 값만큼 복제합니다.</span><span class="sxs-lookup"><span data-stu-id="f27ce-132">This example replicates the value in the **Name** variable by the value in the **Times** column.</span></span> <span data-ttu-id="f27ce-133">**Times** 데이터 형식은 정수가 아니고 정수 데이터 형식으로의 명시적 캐스트가 식에 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f27ce-133">**Times** has a non-integer data type and the expression includes an explicit cast to an integer data type.</span></span> <span data-ttu-id="f27ce-134">**Name** 이 Helmet이고 **Times** 가 2이면 반환 결과는 "HelmetHelmet"입니다.</span><span class="sxs-lookup"><span data-stu-id="f27ce-134">If **Name** contains Helmet and **Times** is 2, the return result is "HelmetHelmet".</span></span>  
  
```  
REPLICATE(@Name, (DT_I4(Times))  
```  
  
## <a name="see-also"></a><span data-ttu-id="f27ce-135">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f27ce-135">See Also</span></span>  
 [<span data-ttu-id="f27ce-136">함수&#40;SSIS 식&#41;</span><span class="sxs-lookup"><span data-stu-id="f27ce-136">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
