---
title: REVERSE(SSIS 식) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- REVERSE function
- reverse character expressions
ms.assetid: bcebcc55-7247-4896-8f53-4d582d58cfb4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 2ace136eed0abcb9df7b25d9370c46d7556c1d48
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732815"
---
# <a name="reverse-ssis-expression"></a><span data-ttu-id="934b0-102">REVERSE(SSIS 식)</span><span class="sxs-lookup"><span data-stu-id="934b0-102">REVERSE (SSIS Expression)</span></span>
  <span data-ttu-id="934b0-103">문자 식을 역 순서로 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="934b0-103">Returns a character expression in reverse order.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="934b0-104">구문</span><span class="sxs-lookup"><span data-stu-id="934b0-104">Syntax</span></span>  
  
```  
  
REVERSE(character_expression)  
```  
  
## <a name="arguments"></a><span data-ttu-id="934b0-105">인수</span><span class="sxs-lookup"><span data-stu-id="934b0-105">Arguments</span></span>  
 <span data-ttu-id="934b0-106">*character_expression*</span><span class="sxs-lookup"><span data-stu-id="934b0-106">*character_expression*</span></span>  
 <span data-ttu-id="934b0-107">되돌릴 문자 식입니다.</span><span class="sxs-lookup"><span data-stu-id="934b0-107">Is a character expression to be reversed.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="934b0-108">결과 형식</span><span class="sxs-lookup"><span data-stu-id="934b0-108">Result Types</span></span>  
 <span data-ttu-id="934b0-109">DT_WSTR</span><span class="sxs-lookup"><span data-stu-id="934b0-109">DT_WSTR</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="934b0-110">설명</span><span class="sxs-lookup"><span data-stu-id="934b0-110">Remarks</span></span>  
 <span data-ttu-id="934b0-111">*character_expression* DT_WSTR 데이터 형식이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="934b0-111">The *character_expression* argument must have the DT_WSTR data type.</span></span>  
  
 <span data-ttu-id="934b0-112">*character_expression* 이 null인 경우 REVERSE가 null 결과를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="934b0-112">REVERSE returns a null result if *character_expression* is null.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="934b0-113">식 예</span><span class="sxs-lookup"><span data-stu-id="934b0-113">Expression Examples</span></span>  
 <span data-ttu-id="934b0-114">이 예에서는 문자열 리터럴을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="934b0-114">This example uses a string literal.</span></span> <span data-ttu-id="934b0-115">반환 결과는 "ekiB niatnuoM"입니다.</span><span class="sxs-lookup"><span data-stu-id="934b0-115">The return result is "ekiB niatnuoM".</span></span>  
  
```  
REVERSE("Mountain Bike")  
```  
  
 <span data-ttu-id="934b0-116">이 예에서는 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="934b0-116">This example uses a variable.</span></span> <span data-ttu-id="934b0-117">**Name** 이 Touring Bike이면 반환 결과는 "ekiB gniruoT"입니다.</span><span class="sxs-lookup"><span data-stu-id="934b0-117">If **Name** contains Touring Bike, the return result is "ekiB gniruoT".</span></span>  
  
```  
REVERSE(@Name)  
```  
  
## <a name="see-also"></a><span data-ttu-id="934b0-118">참고 항목</span><span class="sxs-lookup"><span data-stu-id="934b0-118">See Also</span></span>  
 [<span data-ttu-id="934b0-119">함수&#40;SSIS 식&#41;</span><span class="sxs-lookup"><span data-stu-id="934b0-119">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
