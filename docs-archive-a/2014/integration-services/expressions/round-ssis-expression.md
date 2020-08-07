---
title: ROUND(SSIS 식) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- rounding expressions
- ROUND function [SSIS]
ms.assetid: 376f1947-4fc5-4611-ad86-823e4db1b468
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9d77045787eafbc3dd402db9982d8d7a98190bc2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732807"
---
# <a name="round-ssis-expression"></a><span data-ttu-id="34684-102">ROUND(SSIS 식)</span><span class="sxs-lookup"><span data-stu-id="34684-102">ROUND (SSIS Expression)</span></span>
  <span data-ttu-id="34684-103">특정 길이나 전체 자릿수로 반올림한 숫자 식을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="34684-103">Returns a numeric expression that is rounded to the specified length or precision.</span></span> <span data-ttu-id="34684-104">길이 매개 변수는 정수여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="34684-104">The length parameter must evaluate to an integer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34684-105">구문</span><span class="sxs-lookup"><span data-stu-id="34684-105">Syntax</span></span>  
  
```  
  
ROUND(numeric_expression,length)  
```  
  
## <a name="arguments"></a><span data-ttu-id="34684-106">인수</span><span class="sxs-lookup"><span data-stu-id="34684-106">Arguments</span></span>  
 <span data-ttu-id="34684-107">*numeric_expression*</span><span class="sxs-lookup"><span data-stu-id="34684-107">*numeric_expression*</span></span>  
 <span data-ttu-id="34684-108">유효한 숫자 유형의 식입니다.</span><span class="sxs-lookup"><span data-stu-id="34684-108">Is an expression of a valid numeric type.</span></span> <span data-ttu-id="34684-109">자세한 내용은 [Integration Services Data Types](../data-flow/integration-services-data-types.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="34684-109">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
 <span data-ttu-id="34684-110">*length*</span><span class="sxs-lookup"><span data-stu-id="34684-110">*length*</span></span>  
 <span data-ttu-id="34684-111">정수 식입니다.</span><span class="sxs-lookup"><span data-stu-id="34684-111">Is an integer expression.</span></span> <span data-ttu-id="34684-112">*numeric_expression* 을 반올림할 전체 자릿수입니다.</span><span class="sxs-lookup"><span data-stu-id="34684-112">It is the precision to which *numeric_expression* is rounded.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="34684-113">결과 형식</span><span class="sxs-lookup"><span data-stu-id="34684-113">Result Types</span></span>  
 <span data-ttu-id="34684-114">*numeric*_*expression*과 동일한 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="34684-114">The same type as *numeric*_*expression.*</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="34684-115">설명</span><span class="sxs-lookup"><span data-stu-id="34684-115">Remarks</span></span>  
 <span data-ttu-id="34684-116">*length* 인수는 양의 정수이거나 0이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="34684-116">The *length* argument must evaluate to a positive integer or zero.</span></span>  
  
 <span data-ttu-id="34684-117">인수가 Null이면 ROUND 결과도 Null입니다.</span><span class="sxs-lookup"><span data-stu-id="34684-117">ROUND returns a null result if the argument is null.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="34684-118">식 예</span><span class="sxs-lookup"><span data-stu-id="34684-118">Expression Examples</span></span>  
 <span data-ttu-id="34684-119">이 예에서는 숫자 리터럴을 길이 3으로 반올림합니다.</span><span class="sxs-lookup"><span data-stu-id="34684-119">These examples round numeric literals to a length of three.</span></span> <span data-ttu-id="34684-120">첫 번째 반환 결과는 137.1570이고 두 번째 반환 결과는 137.1580입니다.</span><span class="sxs-lookup"><span data-stu-id="34684-120">The first return result is 137.1570, the second 137.1580.</span></span>  
  
```  
ROUND(137.1574,3)  
ROUND(137.1575,3)  
```  
  
## <a name="see-also"></a><span data-ttu-id="34684-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="34684-121">See Also</span></span>  
 [<span data-ttu-id="34684-122">함수&#40;SSIS 식&#41;</span><span class="sxs-lookup"><span data-stu-id="34684-122">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
