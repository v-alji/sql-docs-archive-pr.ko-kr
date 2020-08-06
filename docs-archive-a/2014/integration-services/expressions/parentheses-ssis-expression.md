---
title: ()(괄호)(SSIS 식) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- () (parentheses operator)
- evaluation order [Integration Services]
- parentheses operator ()
ms.assetid: 931e10eb-1707-4121-b2f1-43565561119f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e390e10e485bd9cc22480300b6a9c33098bda8f1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740156"
---
# <a name="-parentheses-ssis-expression"></a><span data-ttu-id="0b7c6-102">()(괄호)(SSIS 식)</span><span class="sxs-lookup"><span data-stu-id="0b7c6-102">() (Parentheses) (SSIS Expression)</span></span>
  <span data-ttu-id="0b7c6-103">식의 계산 순서를 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="0b7c6-103">Identifies the evaluation order of expressions.</span></span> <span data-ttu-id="0b7c6-104">괄호로 묶인 식의 계산 우선 순위가 가장 높습니다.</span><span class="sxs-lookup"><span data-stu-id="0b7c6-104">Expressions enclosed in parentheses have the highest evaluation precedence.</span></span> <span data-ttu-id="0b7c6-105">괄호로 묶인 중첩 식은 안에서부터 밖으로 계산됩니다.</span><span class="sxs-lookup"><span data-stu-id="0b7c6-105">Nested expressions enclosed in parentheses are evaluated in inner-to-outer order.</span></span>  
  
 <span data-ttu-id="0b7c6-106">괄호를 사용하면 복잡한 식을 쉽게 이해하는 데에도 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0b7c6-106">Parentheses are also used to make complex expressions easier to understand.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b7c6-107">구문</span><span class="sxs-lookup"><span data-stu-id="0b7c6-107">Syntax</span></span>  
  
```  
  
(expression)  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="0b7c6-108">인수</span><span class="sxs-lookup"><span data-stu-id="0b7c6-108">Arguments</span></span>  
 <span data-ttu-id="0b7c6-109">*expression*</span><span class="sxs-lookup"><span data-stu-id="0b7c6-109">*expression*</span></span>  
 <span data-ttu-id="0b7c6-110">유효한 식입니다.</span><span class="sxs-lookup"><span data-stu-id="0b7c6-110">Is any valid expression.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="0b7c6-111">결과 형식</span><span class="sxs-lookup"><span data-stu-id="0b7c6-111">Result Types</span></span>  
 <span data-ttu-id="0b7c6-112">*expression*의 데이터 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="0b7c6-112">The data type of *expression*.</span></span> <span data-ttu-id="0b7c6-113">자세한 내용은 [Integration Services Data Types](../data-flow/integration-services-data-types.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0b7c6-113">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="0b7c6-114">식 예</span><span class="sxs-lookup"><span data-stu-id="0b7c6-114">Expression Examples</span></span>  
 <span data-ttu-id="0b7c6-115">이 예에서는 괄호를 사용하여 연산자의 우선 순위을 수정하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="0b7c6-115">This example shows how the use of parenthesis modifies the precedence of operators.</span></span> <span data-ttu-id="0b7c6-116">첫 번째 식은 100으로 계산되고 두 번째 식은 31로 계산됩니다.</span><span class="sxs-lookup"><span data-stu-id="0b7c6-116">The first expression evaluates to 100, whereas the second one evaluates to 31.</span></span>  
  
```  
(5 + 5) * (4 + 6)  
5 + 5 * 4 + 6  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="0b7c6-117">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0b7c6-117">See Also</span></span>  
 <span data-ttu-id="0b7c6-118">[연산자 우선 순위 및 계산 방향](operator-precedence-and-associativity.md) </span><span class="sxs-lookup"><span data-stu-id="0b7c6-118">[Operator Precedence and Associativity](operator-precedence-and-associativity.md) </span></span>  
 [<span data-ttu-id="0b7c6-119">연산자&#40;SSIS 식&#41;</span><span class="sxs-lookup"><span data-stu-id="0b7c6-119">Operators &#40;SSIS Expression&#41;</span></span>](operators-ssis-expression.md)  
  
  
