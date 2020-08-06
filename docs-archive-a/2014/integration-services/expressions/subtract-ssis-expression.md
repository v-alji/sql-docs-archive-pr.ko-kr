---
title: '- (빼기)(SSIS 식) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- '- (subtract)'
- subtract operator (-)
ms.assetid: b48da086-37dd-460a-8a4b-912f52c9b158
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 79c47689baf47c33952c6b208ac622e9920d05fe
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732775"
---
# <a name="--subtract-ssis-expression"></a><span data-ttu-id="8853a-102">-(빼기)(SSIS 식)</span><span class="sxs-lookup"><span data-stu-id="8853a-102">- (Subtract) (SSIS Expression)</span></span>
  <span data-ttu-id="8853a-103">첫 번째 숫자 식에서 두 번째 식을 뺍니다.</span><span class="sxs-lookup"><span data-stu-id="8853a-103">Subtracts the second numeric expression from the first one.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8853a-104">구문</span><span class="sxs-lookup"><span data-stu-id="8853a-104">Syntax</span></span>  
  
```  
  
numeric_expression1 - numeric_expression2  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="8853a-105">인수</span><span class="sxs-lookup"><span data-stu-id="8853a-105">Arguments</span></span>  
 <span data-ttu-id="8853a-106">*numeric_expression1, numeric_expression2*</span><span class="sxs-lookup"><span data-stu-id="8853a-106">*numeric_expression1, numeric_expression2*</span></span>  
 <span data-ttu-id="8853a-107">숫자 데이터 형식의 유효한 식입니다.</span><span class="sxs-lookup"><span data-stu-id="8853a-107">Is any valid expression of a numeric data type.</span></span> <span data-ttu-id="8853a-108">자세한 내용은 [Integration Services Data Types](../data-flow/integration-services-data-types.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8853a-108">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="8853a-109">결과 형식</span><span class="sxs-lookup"><span data-stu-id="8853a-109">Result Types</span></span>  
 <span data-ttu-id="8853a-110">두 인수의 데이터 형식에 따라 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="8853a-110">Determined by the data types of the two arguments.</span></span> <span data-ttu-id="8853a-111">자세한 내용은 [Integration Services Data Types in Expressions](integration-services-data-types-in-expressions.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8853a-111">For more information, see [Integration Services Data Types in Expressions](integration-services-data-types-in-expressions.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8853a-112">설명</span><span class="sxs-lookup"><span data-stu-id="8853a-112">Remarks</span></span>  
 <span data-ttu-id="8853a-113">식이 올바른 순서로 계산되도록 단항 빼기 식을 괄호로 묶으십시오.</span><span class="sxs-lookup"><span data-stu-id="8853a-113">Enclose the minus unary expression in parenthesis to ensure that the expression is evaluated in the correct order</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8853a-114">설명</span><span class="sxs-lookup"><span data-stu-id="8853a-114">Remarks</span></span>  
 <span data-ttu-id="8853a-115">두 피연산자 중 하나가 Null이면 결과도 Null입니다.</span><span class="sxs-lookup"><span data-stu-id="8853a-115">If either operand is null, the result is null.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="8853a-116">식 예</span><span class="sxs-lookup"><span data-stu-id="8853a-116">Expression Examples</span></span>  
 <span data-ttu-id="8853a-117">이 예에서는 숫자 리터럴을 뺍니다.</span><span class="sxs-lookup"><span data-stu-id="8853a-117">This example subtracts numeric literals.</span></span>  
  
```  
5 - 6.09  
```  
  
 <span data-ttu-id="8853a-118">이 예에서는 **ListPrice** 열의 값에서 **StandardCost** 열의 값을 뺍니다.</span><span class="sxs-lookup"><span data-stu-id="8853a-118">This example subtracts the value in the **StandardCost** column from the value in the **ListPrice** column.</span></span>  
  
```  
ListPrice - StandardCost  
```  
  
 <span data-ttu-id="8853a-119">이 예에서는 **ListPrice** 열에서 계산된 값을 뺍니다.</span><span class="sxs-lookup"><span data-stu-id="8853a-119">This example subtracts a calculated value from the **ListPrice** column.</span></span> <span data-ttu-id="8853a-120">변수 **Discount%** 는 이름에 % 문자가 포함되어 있으므로 대괄호로 묶어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8853a-120">The variable **Discount%** must be enclosed in brackets because the name includes the % character.</span></span> <span data-ttu-id="8853a-121">자세한 내용은 [식별자&#40;SSIS&#41;](identifiers-ssis.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8853a-121">For more information, see [Identifiers &#40;SSIS&#41;](identifiers-ssis.md).</span></span>  
  
```  
ListPrice - (ListPrice * @[Discount%])  
```  
  
## <a name="see-also"></a><span data-ttu-id="8853a-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8853a-122">See Also</span></span>  
 <span data-ttu-id="8853a-123">[연산자 우선 순위 및 계산 방향](operator-precedence-and-associativity.md) </span><span class="sxs-lookup"><span data-stu-id="8853a-123">[Operator Precedence and Associativity](operator-precedence-and-associativity.md) </span></span>  
 [<span data-ttu-id="8853a-124">연산자&#40;SSIS 식&#41;</span><span class="sxs-lookup"><span data-stu-id="8853a-124">Operators &#40;SSIS Expression&#41;</span></span>](operators-ssis-expression.md)  
  
  
