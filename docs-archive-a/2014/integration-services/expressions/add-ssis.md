---
title: + (추가)(SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- + (add)
- add operator (+)
- adding expressions
ms.assetid: 44df4154-fed5-4e7f-9995-e703a0164f6a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: fe1e8f2118e6328582cb24abfd44eef5f3b15f79
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652973"
---
# <a name="-add-ssis"></a><span data-ttu-id="25108-102">+(더하기)(SSIS)</span><span class="sxs-lookup"><span data-stu-id="25108-102">+ (Add) (SSIS)</span></span>
  <span data-ttu-id="25108-103">두 숫자 식을 더합니다.</span><span class="sxs-lookup"><span data-stu-id="25108-103">Adds two numeric expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25108-104">구문</span><span class="sxs-lookup"><span data-stu-id="25108-104">Syntax</span></span>  
  
```  
  
numeric_expression1 + numeric_expression2  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="25108-105">인수</span><span class="sxs-lookup"><span data-stu-id="25108-105">Arguments</span></span>  
 <span data-ttu-id="25108-106">*numeric_expression1, numeric_ expression2*</span><span class="sxs-lookup"><span data-stu-id="25108-106">*numeric_expression1, numeric_ expression2*</span></span>  
 <span data-ttu-id="25108-107">숫자 데이터 형식의 유효한 식입니다.</span><span class="sxs-lookup"><span data-stu-id="25108-107">Is any valid expression of a numeric data type.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="25108-108">결과 형식</span><span class="sxs-lookup"><span data-stu-id="25108-108">Result Types</span></span>  
 <span data-ttu-id="25108-109">두 인수의 데이터 형식에 따라 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="25108-109">Determined by data types of the two arguments.</span></span> <span data-ttu-id="25108-110">자세한 내용은 [Integration Services Data Types](../data-flow/integration-services-data-types.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="25108-110">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="25108-111">설명</span><span class="sxs-lookup"><span data-stu-id="25108-111">Remarks</span></span>  
 <span data-ttu-id="25108-112">두 피연산자 중 하나가 Null이면 결과도 Null입니다.</span><span class="sxs-lookup"><span data-stu-id="25108-112">If either operand is null, the result is null.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="25108-113">식 예</span><span class="sxs-lookup"><span data-stu-id="25108-113">Expression Examples</span></span>  
 <span data-ttu-id="25108-114">이 예에서는 숫자 리터럴을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="25108-114">This example adds numeric literals.</span></span>  
  
```  
5 + 6.09 + 7.0  
```  
  
 <span data-ttu-id="25108-115">이 예에서는 **VacationHours** 열과 **SickLeaveHours** 열의 값을 더합니다.</span><span class="sxs-lookup"><span data-stu-id="25108-115">This example adds values in the **VacationHours** and **SickLeaveHours** columns.</span></span>  
  
```  
VacationHours + SickLeaveHours  
```  
  
 <span data-ttu-id="25108-116">이 예에서는 **StandardCost** 열에 계산된 값을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="25108-116">This example adds a calculated value to the **StandardCost** column.</span></span> <span data-ttu-id="25108-117">변수 **Profit%** 은 이름에 % 문자가 포함되어 있으므로 대괄호로 묶어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="25108-117">The variable **Profit%** must be enclosed in brackets because the name includes the % character.</span></span> <span data-ttu-id="25108-118">자세한 내용은 [식별자&#40;SSIS&#41;](identifiers-ssis.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="25108-118">For more information, see [Identifiers &#40;SSIS&#41;](identifiers-ssis.md).</span></span>  
  
```  
StandardCost + (StandardCost * @[Profit%])  
```  
  
## <a name="see-also"></a><span data-ttu-id="25108-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="25108-119">See Also</span></span>  
 <span data-ttu-id="25108-120">[연산자 우선 순위 및 계산 방향](operator-precedence-and-associativity.md) </span><span class="sxs-lookup"><span data-stu-id="25108-120">[Operator Precedence and Associativity](operator-precedence-and-associativity.md) </span></span>  
 [<span data-ttu-id="25108-121">연산자&#40;SSIS 식&#41;</span><span class="sxs-lookup"><span data-stu-id="25108-121">Operators &#40;SSIS Expression&#41;</span></span>](operators-ssis-expression.md)  
  
  
