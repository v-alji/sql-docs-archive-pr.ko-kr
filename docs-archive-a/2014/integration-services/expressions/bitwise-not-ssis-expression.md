---
title: ~(비트 Not)(SSIS 식) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- bitwise NOT (~)
- ~ (bitwise NOT)
ms.assetid: e4413ddd-0d0e-40c3-9c76-b5ce323218ec
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 75745a0650c1744064f2a671659879e11464514e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652961"
---
# <a name="-bitwise-not-ssis-expression"></a><span data-ttu-id="b4252-102">~(비트 Not)(SSIS 식)</span><span class="sxs-lookup"><span data-stu-id="b4252-102">~ (Bitwise Not) (SSIS Expression)</span></span>
  <span data-ttu-id="b4252-103">정수의 비트 부정을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="b4252-103">Performs a bitwise negation of an integer.</span></span> <span data-ttu-id="b4252-104">이 연산자는 부호 있는 정수 또는 부호 없는 정수 데이터 형식에 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4252-104">This operator can be applied to signed and unsigned integer data types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4252-105">구문</span><span class="sxs-lookup"><span data-stu-id="b4252-105">Syntax</span></span>  
  
```  
  
~integer_expression  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="b4252-106">인수</span><span class="sxs-lookup"><span data-stu-id="b4252-106">Arguments</span></span>  
 <span data-ttu-id="b4252-107">*integer_expression*</span><span class="sxs-lookup"><span data-stu-id="b4252-107">*integer_expression*</span></span>  
 <span data-ttu-id="b4252-108">정수 데이터 형식의 유효한 식입니다.</span><span class="sxs-lookup"><span data-stu-id="b4252-108">Is any valid expression of an integer data type.</span></span> <span data-ttu-id="b4252-109">*integer*_*expression* 은 비트 연산을 위해 이진수로 변환되는 정수입니다.</span><span class="sxs-lookup"><span data-stu-id="b4252-109">*integer*_*expression* is an integer that is transformed into a binary number for the bitwise operation.</span></span> <span data-ttu-id="b4252-110">자세한 내용은 [Integration Services Data Types](../data-flow/integration-services-data-types.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b4252-110">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="b4252-111">결과 형식</span><span class="sxs-lookup"><span data-stu-id="b4252-111">Result Types</span></span>  
 <span data-ttu-id="b4252-112">*integer_expression*의 데이터 형식을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="b4252-112">Returns the data type of *integer_expression.*</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b4252-113">설명</span><span class="sxs-lookup"><span data-stu-id="b4252-113">Remarks</span></span>  
 <span data-ttu-id="b4252-114">None</span><span class="sxs-lookup"><span data-stu-id="b4252-114">None</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="b4252-115">식 예</span><span class="sxs-lookup"><span data-stu-id="b4252-115">Expression Examples</span></span>  
 <span data-ttu-id="b4252-116">이 예에서는 숫자 170(0000 0000 1010 1010)에 비트 ~(NOT) 연산을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="b4252-116">This example performs a bitwise ~ (NOT) operation on the number 170 (0000 0000 1010 1010).</span></span> <span data-ttu-id="b4252-117">숫자는 부호 있는 정수입니다.</span><span class="sxs-lookup"><span data-stu-id="b4252-117">The number is a signed integer.</span></span>  
  
```  
  
~ 170  
```  
  
 <span data-ttu-id="b4252-118">식은 -170(1111111101010101)으로 계산됩니다.</span><span class="sxs-lookup"><span data-stu-id="b4252-118">The expression evaluates to -170 (1111111101010101).</span></span>  
  
 <span data-ttu-id="b4252-119">0000000010101010</span><span class="sxs-lookup"><span data-stu-id="b4252-119">0000000010101010</span></span>  
  
 ---------------------\-  
  
 <span data-ttu-id="b4252-120">1111111101010101</span><span class="sxs-lookup"><span data-stu-id="b4252-120">1111111101010101</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4252-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b4252-121">See Also</span></span>  
 <span data-ttu-id="b4252-122">[연산자 우선 순위 및 계산 방향](operator-precedence-and-associativity.md) </span><span class="sxs-lookup"><span data-stu-id="b4252-122">[Operator Precedence and Associativity](operator-precedence-and-associativity.md) </span></span>  
 [<span data-ttu-id="b4252-123">연산자&#40;SSIS 식&#41;</span><span class="sxs-lookup"><span data-stu-id="b4252-123">Operators &#40;SSIS Expression&#41;</span></span>](operators-ssis-expression.md)  
  
  
