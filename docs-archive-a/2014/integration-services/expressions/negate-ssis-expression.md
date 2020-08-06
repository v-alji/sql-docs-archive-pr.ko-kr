---
title: '- (부정)(SSIS 식) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- '- (negative)'
- negative operator (-)
ms.assetid: f0118dfc-aced-4de2-953e-5ebf9c962b8d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 2a2d8ba292f2d24633598ab080ddf75ded5e8bd1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735488"
---
# <a name="--negate-ssis-expression"></a><span data-ttu-id="d3acb-102">-(부정)(SSIS 식)</span><span class="sxs-lookup"><span data-stu-id="d3acb-102">- (Negate) (SSIS Expression)</span></span>
  <span data-ttu-id="d3acb-103">숫자 식을 부정합니다.</span><span class="sxs-lookup"><span data-stu-id="d3acb-103">Negates a numeric expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3acb-104">구문</span><span class="sxs-lookup"><span data-stu-id="d3acb-104">Syntax</span></span>  
  
```  
  
-numeric_expression  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="d3acb-105">인수</span><span class="sxs-lookup"><span data-stu-id="d3acb-105">Arguments</span></span>  
 <span data-ttu-id="d3acb-106">*numeric_expression*</span><span class="sxs-lookup"><span data-stu-id="d3acb-106">*numeric_expression*</span></span>  
 <span data-ttu-id="d3acb-107">숫자 데이터 형식의 유효한 식입니다.</span><span class="sxs-lookup"><span data-stu-id="d3acb-107">Is any valid expression of any numeric data type.</span></span> <span data-ttu-id="d3acb-108">부호 있는 숫자 데이터 형식만 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="d3acb-108">Only signed numeric data types are supported.</span></span> <span data-ttu-id="d3acb-109">자세한 내용은 [Integration Services Data Types](../data-flow/integration-services-data-types.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d3acb-109">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="d3acb-110">결과 형식</span><span class="sxs-lookup"><span data-stu-id="d3acb-110">Result Types</span></span>  
 <span data-ttu-id="d3acb-111">*numeric_expression*의 데이터 형식을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="d3acb-111">Returns the data type of *numeric_expression*.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="d3acb-112">식 예</span><span class="sxs-lookup"><span data-stu-id="d3acb-112">Expression Examples</span></span>  
 <span data-ttu-id="d3acb-113">이 예에서는 **Counter** 변수 값을 부정하고 숫자 리터럴 50을 더합니다.</span><span class="sxs-lookup"><span data-stu-id="d3acb-113">This example negates the value of the **Counter** variable and adds the numeric literal 50.</span></span>  
  
```  
-@Counter + 50  
```  
  
## <a name="see-also"></a><span data-ttu-id="d3acb-114">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d3acb-114">See Also</span></span>  
 <span data-ttu-id="d3acb-115">[연산자 우선 순위 및 계산 방향](operator-precedence-and-associativity.md) </span><span class="sxs-lookup"><span data-stu-id="d3acb-115">[Operator Precedence and Associativity](operator-precedence-and-associativity.md) </span></span>  
 [<span data-ttu-id="d3acb-116">연산자&#40;SSIS 식&#41;</span><span class="sxs-lookup"><span data-stu-id="d3acb-116">Operators &#40;SSIS Expression&#41;</span></span>](operators-ssis-expression.md)  
  
  
