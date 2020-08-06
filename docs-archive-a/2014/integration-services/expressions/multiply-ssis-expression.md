---
title: '* (곱하기)(SSIS 식) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- '* (multiply operator)'
- multiply operator (*)
ms.assetid: d457f052-ffbb-4485-833f-f4bed4349b69
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 16d8429a869b60be31a94244a2ce47d515770c6b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650193"
---
# <a name="-multiply-ssis-expression"></a><span data-ttu-id="3b079-102">\*(곱하기)(SSIS 식)</span><span class="sxs-lookup"><span data-stu-id="3b079-102">\* (Multiply) (SSIS Expression)</span></span>
  <span data-ttu-id="3b079-103">두 숫자 식을 곱합니다.</span><span class="sxs-lookup"><span data-stu-id="3b079-103">Multiplies two numeric expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b079-104">구문</span><span class="sxs-lookup"><span data-stu-id="3b079-104">Syntax</span></span>  
  
```  
  
numeric_expression1 * numeric_expression2  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="3b079-105">인수</span><span class="sxs-lookup"><span data-stu-id="3b079-105">Arguments</span></span>  
 <span data-ttu-id="3b079-106">*numeric_expression1, numeric_expression2*</span><span class="sxs-lookup"><span data-stu-id="3b079-106">*numeric_expression1, numeric_expression2*</span></span>  
 <span data-ttu-id="3b079-107">숫자 데이터 형식의 유효한 식입니다.</span><span class="sxs-lookup"><span data-stu-id="3b079-107">Is any valid expression of a numeric data type.</span></span> <span data-ttu-id="3b079-108">자세한 내용은 [Integration Services Data Types](../data-flow/integration-services-data-types.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3b079-108">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="3b079-109">결과 형식</span><span class="sxs-lookup"><span data-stu-id="3b079-109">Result Types</span></span>  
 <span data-ttu-id="3b079-110">두 인수의 데이터 형식에 따라 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="3b079-110">Determined by data types of the two arguments.</span></span> <span data-ttu-id="3b079-111">자세한 내용은 [Integration Services Data Types in Expressions](integration-services-data-types-in-expressions.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3b079-111">For more information, see [Integration Services Data Types in Expressions](integration-services-data-types-in-expressions.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3b079-112">설명</span><span class="sxs-lookup"><span data-stu-id="3b079-112">Remarks</span></span>  
 <span data-ttu-id="3b079-113">두 피연산자 중 하나가 Null이면 결과도 Null입니다.</span><span class="sxs-lookup"><span data-stu-id="3b079-113">If either operand is null, the result is null.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="3b079-114">식 예</span><span class="sxs-lookup"><span data-stu-id="3b079-114">Expression Examples</span></span>  
 <span data-ttu-id="3b079-115">이 예에서는 숫자 리터럴을 곱합니다.</span><span class="sxs-lookup"><span data-stu-id="3b079-115">This example multiplies numeric literals.</span></span>  
  
```  
5 * 6.09  
```  
  
 <span data-ttu-id="3b079-116">이 예에서는 **ListPrice** 열의 값에 10%를 곱합니다.</span><span class="sxs-lookup"><span data-stu-id="3b079-116">This example multiplies values in the **ListPrice** column by 10 percent.</span></span>  
  
```  
ListPrice * .10  
```  
  
 <span data-ttu-id="3b079-117">이 예에서는 **ListPrice** 열에서 식 결과를 뺍니다.</span><span class="sxs-lookup"><span data-stu-id="3b079-117">This example subtracts the result of an expression from the **ListPrice** column.</span></span> <span data-ttu-id="3b079-118">변수 **Discount%** 는 이름에 % 문자가 포함되어 있으므로 대괄호로 묶어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3b079-118">The variable **Discount%** must be enclosed in brackets because the name includes the % character.</span></span> <span data-ttu-id="3b079-119">자세한 내용은 [식별자&#40;SSIS&#41;](identifiers-ssis.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3b079-119">For more information, see [Identifiers &#40;SSIS&#41;](identifiers-ssis.md).</span></span>  
  
```  
ListPrice - (ListPrice * @[Discount%])  
```  
  
## <a name="see-also"></a><span data-ttu-id="3b079-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3b079-120">See Also</span></span>  
 <span data-ttu-id="3b079-121">[연산자 우선 순위 및 계산 방향](operator-precedence-and-associativity.md) </span><span class="sxs-lookup"><span data-stu-id="3b079-121">[Operator Precedence and Associativity](operator-precedence-and-associativity.md) </span></span>  
 [<span data-ttu-id="3b079-122">연산자&#40;SSIS 식&#41;</span><span class="sxs-lookup"><span data-stu-id="3b079-122">Operators &#40;SSIS Expression&#41;</span></span>](operators-ssis-expression.md)  
  
  
