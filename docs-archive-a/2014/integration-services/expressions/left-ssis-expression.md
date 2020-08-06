---
title: LEFT(SSIS 식) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 5634dbfb-740d-4c93-8fd5-2854cc741327
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7f21d134988414c7d8579d720877feec45383270
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659530"
---
# <a name="left-ssis-expression"></a><span data-ttu-id="c7ccb-102">LEFT(SSIS 식)</span><span class="sxs-lookup"><span data-stu-id="c7ccb-102">LEFT (SSIS Expression)</span></span>
  <span data-ttu-id="c7ccb-103">지정한 문자 식의 왼쪽부터 지정한 개수의 문자를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="c7ccb-103">Returns the specified number of characters from the leftmost portion of the given character expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7ccb-104">구문</span><span class="sxs-lookup"><span data-stu-id="c7ccb-104">Syntax</span></span>  
  
```  
  
LEFT(character_expression,number)  
```  
  
## <a name="arguments"></a><span data-ttu-id="c7ccb-105">인수</span><span class="sxs-lookup"><span data-stu-id="c7ccb-105">Arguments</span></span>  
 <span data-ttu-id="c7ccb-106">*character_expression*</span><span class="sxs-lookup"><span data-stu-id="c7ccb-106">*character_expression*</span></span>  
 <span data-ttu-id="c7ccb-107">문자를 추출할 문자 식입니다.</span><span class="sxs-lookup"><span data-stu-id="c7ccb-107">Is a character expression from which to extract characters.</span></span>  
  
 <span data-ttu-id="c7ccb-108">*number*</span><span class="sxs-lookup"><span data-stu-id="c7ccb-108">*number*</span></span>  
 <span data-ttu-id="c7ccb-109">반환할 문자 수를 나타내는 정수 식입니다.</span><span class="sxs-lookup"><span data-stu-id="c7ccb-109">Is an integer expression that indicates the number of characters to be returned.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="c7ccb-110">결과 형식</span><span class="sxs-lookup"><span data-stu-id="c7ccb-110">Result Types</span></span>  
 <span data-ttu-id="c7ccb-111">DT_WSTR</span><span class="sxs-lookup"><span data-stu-id="c7ccb-111">DT_WSTR</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c7ccb-112">설명</span><span class="sxs-lookup"><span data-stu-id="c7ccb-112">Remarks</span></span>  
 <span data-ttu-id="c7ccb-113">*number* 가 *character_expression*의 길이보다 큰 경우 함수는 *character_expression*을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="c7ccb-113">If *number* is greater than the length of *character_expression*, the function returns *character_expression*.</span></span>  
  
 <span data-ttu-id="c7ccb-114">*number* 가 0이면 함수는 길이가 0인 문자열을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="c7ccb-114">If *number* is zero, the function returns a zero-length string.</span></span>  
  
 <span data-ttu-id="c7ccb-115">*number* 가 음수이면 오류가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7ccb-115">If *number* is a negative number, the function returns an error.</span></span>  
  
 <span data-ttu-id="c7ccb-116">*number* 인수는 변수와 열을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7ccb-116">The *number* argument can take variables and columns.</span></span>  
  
 <span data-ttu-id="c7ccb-117">LEFT는 DT_WSTR 데이터 형식에서만 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7ccb-117">LEFT works only with the DT_WSTR data type.</span></span> <span data-ttu-id="c7ccb-118">문자열 리터럴이나 DT_STR 데이터 형식의 데이터 열인 *character_expression* 인수는 LEFT가 연산을 수행하기 전에 DT_WSTR 데이터 형식으로 암시적으로 캐스팅됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7ccb-118">A *character_expression* argument that is a string literal or a data column with the DT_STR data type is implicitly cast to the DT_WSTR data type before LEFT performs its operation.</span></span> <span data-ttu-id="c7ccb-119">다른 데이터 형식은 DT_WSTR 데이터 형식으로 명시적으로 캐스팅되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7ccb-119">Other data types must be explicitly cast to the DT_WSTR data type.</span></span> <span data-ttu-id="c7ccb-120">자세한 내용은 [Integration Services 데이터 형식](../data-flow/integration-services-data-types.md) 및 [캐스트&#40;SSIS 식&#41;](cast-ssis-expression.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c7ccb-120">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md) and [Cast &#40;SSIS Expression&#41;](cast-ssis-expression.md).</span></span>  
  
 <span data-ttu-id="c7ccb-121">두 인수 중 하나가 Null이면 LEFT 결과도 Null입니다.</span><span class="sxs-lookup"><span data-stu-id="c7ccb-121">LEFT returns a null result if either argument is null.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="c7ccb-122">식 예</span><span class="sxs-lookup"><span data-stu-id="c7ccb-122">Expression Examples</span></span>  
 <span data-ttu-id="c7ccb-123">다음 예에서는 문자열 리터럴을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="c7ccb-123">The following example uses a string literal.</span></span> <span data-ttu-id="c7ccb-124">반환 결과는 `"Mountain"`입니다.</span><span class="sxs-lookup"><span data-stu-id="c7ccb-124">The return result is `"Mountain"`.</span></span>  
  
```  
LEFT("Mountain Bike", 8)  
```  
  
## <a name="see-also"></a><span data-ttu-id="c7ccb-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c7ccb-125">See Also</span></span>  
 <span data-ttu-id="c7ccb-126">[RIGHT&#40;SSIS 식&#41;](right-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="c7ccb-126">[RIGHT &#40;SSIS Expression&#41;](right-ssis-expression.md) </span></span>  
 [<span data-ttu-id="c7ccb-127">함수&#40;SSIS 식&#41;</span><span class="sxs-lookup"><span data-stu-id="c7ccb-127">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
