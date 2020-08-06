---
title: '! (논리적 Not)(SSIS 식) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- logical Not (!)
- '! (logical Not)'
ms.assetid: d5c4d1e1-7be4-4d25-bcd9-5b6ddb53b3b3
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1bbf313930575e864f1556952425567fca96db15
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650198"
---
# <a name="-logical-not-ssis-expression"></a><span data-ttu-id="d81c8-103">!</span><span class="sxs-lookup"><span data-stu-id="d81c8-103">!</span></span> <span data-ttu-id="d81c8-104">(논리적 Not)(SSIS 식)</span><span class="sxs-lookup"><span data-stu-id="d81c8-104">(Logical Not) (SSIS Expression)</span></span>
  <span data-ttu-id="d81c8-105">부울 피연산자를 부정합니다.</span><span class="sxs-lookup"><span data-stu-id="d81c8-105">Negates a Boolean operand.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d81c8-106">! 연산자는</span><span class="sxs-lookup"><span data-stu-id="d81c8-106">The !</span></span> <span data-ttu-id="d81c8-107">다른 연산자와 함께 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d81c8-107">operator cannot be used in conjunction with other operators.</span></span> <span data-ttu-id="d81c8-108">예를 들어 ! 연산자와</span><span class="sxs-lookup"><span data-stu-id="d81c8-108">For example, you cannot combine the !</span></span> <span data-ttu-id="d81c8-109">> 연산자를 !> 연산자로</span><span class="sxs-lookup"><span data-stu-id="d81c8-109">and the > operators into the !>.</span></span> <span data-ttu-id="d81c8-110">결합할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d81c8-110">operator.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d81c8-111">구문</span><span class="sxs-lookup"><span data-stu-id="d81c8-111">Syntax</span></span>  
  
```  
  
!boolean_expression  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="d81c8-112">인수</span><span class="sxs-lookup"><span data-stu-id="d81c8-112">Arguments</span></span>  
 <span data-ttu-id="d81c8-113">*boolean_expression*</span><span class="sxs-lookup"><span data-stu-id="d81c8-113">*boolean_expression*</span></span>  
 <span data-ttu-id="d81c8-114">부울로 계산되는 유효한 식입니다.</span><span class="sxs-lookup"><span data-stu-id="d81c8-114">Is any valid expression that evaluates to a Boolean.</span></span> <span data-ttu-id="d81c8-115">자세한 내용은 [Integration Services Data Types](../data-flow/integration-services-data-types.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d81c8-115">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="d81c8-116">결과 형식</span><span class="sxs-lookup"><span data-stu-id="d81c8-116">Result Types</span></span>  
 <span data-ttu-id="d81c8-117">DT_BOOL</span><span class="sxs-lookup"><span data-stu-id="d81c8-117">DT_BOOL</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d81c8-118">설명</span><span class="sxs-lookup"><span data-stu-id="d81c8-118">Remarks</span></span>  
 <span data-ttu-id="d81c8-119">다음 표에서는 ! 연산의 결과를</span><span class="sxs-lookup"><span data-stu-id="d81c8-119">The following table shows the result of the !</span></span> <span data-ttu-id="d81c8-120">작업을 완료하기 위해 수행해야 하는 다음 단계가 있는 경우 추가로 연락을 드리겠습니다.</span><span class="sxs-lookup"><span data-stu-id="d81c8-120">operation.</span></span>  
  
|<span data-ttu-id="d81c8-121">원래 부울 식</span><span class="sxs-lookup"><span data-stu-id="d81c8-121">Original Boolean expression</span></span>|<span data-ttu-id="d81c8-122">! 연산자를</span><span class="sxs-lookup"><span data-stu-id="d81c8-122">After applying the !</span></span> <span data-ttu-id="d81c8-123">operator</span><span class="sxs-lookup"><span data-stu-id="d81c8-123">operator</span></span>|  
|---------------------------------|------------------------------------|  
|<span data-ttu-id="d81c8-124">TRUE</span><span class="sxs-lookup"><span data-stu-id="d81c8-124">TRUE</span></span>|<span data-ttu-id="d81c8-125">FALSE</span><span class="sxs-lookup"><span data-stu-id="d81c8-125">FALSE</span></span>|  
|<span data-ttu-id="d81c8-126">NULL</span><span class="sxs-lookup"><span data-stu-id="d81c8-126">NULL</span></span>|<span data-ttu-id="d81c8-127">NULL</span><span class="sxs-lookup"><span data-stu-id="d81c8-127">NULL</span></span>|  
|<span data-ttu-id="d81c8-128">FALSE</span><span class="sxs-lookup"><span data-stu-id="d81c8-128">FALSE</span></span>|<span data-ttu-id="d81c8-129">TRUE</span><span class="sxs-lookup"><span data-stu-id="d81c8-129">TRUE</span></span>|  
  
## <a name="expression-examples"></a><span data-ttu-id="d81c8-130">식 예</span><span class="sxs-lookup"><span data-stu-id="d81c8-130">Expression Examples</span></span>  
 <span data-ttu-id="d81c8-131">이 예에서는 **Color** 열의 값이 "red"이면 FALSE가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d81c8-131">This example evaluates to FALSE if the **Color** column value is "red".</span></span>  
  
```  
!(Color == "red")  
```  
  
 <span data-ttu-id="d81c8-132">이 예에서는 **MonthNumber** 변수 값이 현재 월을 나타내는 정수와 같으면 TRUE가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d81c8-132">This example evaluates to TRUE if the value of the **MonthNumber** variable is the same as the integer that represents the current month.</span></span> <span data-ttu-id="d81c8-133">자세한 내용은 [MONTH&#40;SSIS 식&#41;](month-ssis-expression.md) 및 [GETDATE&#40;SSIS 식&#41;](getdate-ssis-expression.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d81c8-133">For more information, see [MONTH &#40;SSIS Expression&#41;](month-ssis-expression.md) and [GETDATE &#40;SSIS Expression&#41;](getdate-ssis-expression.md).</span></span>  
  
```  
!(@MonthNumber != MONTH(GETDATE())  
```  
  
## <a name="see-also"></a><span data-ttu-id="d81c8-134">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d81c8-134">See Also</span></span>  
 <span data-ttu-id="d81c8-135">[연산자 우선 순위 및 계산 방향](operator-precedence-and-associativity.md) </span><span class="sxs-lookup"><span data-stu-id="d81c8-135">[Operator Precedence and Associativity](operator-precedence-and-associativity.md) </span></span>  
 [<span data-ttu-id="d81c8-136">연산자&#40;SSIS 식&#41;</span><span class="sxs-lookup"><span data-stu-id="d81c8-136">Operators &#40;SSIS Expression&#41;</span></span>](operators-ssis-expression.md)  
  
  
