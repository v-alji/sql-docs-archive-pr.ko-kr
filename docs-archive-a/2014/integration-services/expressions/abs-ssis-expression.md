---
title: ABS(SSIS 식) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- ABS function
- absolute positive value
ms.assetid: 156747f6-e016-44cf-9a9f-ae8e4a1b4f17
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a2f429dda94282646ef769a1c393f9fa54b56e5e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652975"
---
# <a name="abs-ssis-expression"></a><span data-ttu-id="b9066-102">ABS(SSIS 식)</span><span class="sxs-lookup"><span data-stu-id="b9066-102">ABS (SSIS Expression)</span></span>
  <span data-ttu-id="b9066-103">숫자 식의 절대값을 양수로 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="b9066-103">Returns the absolute, positive value of a numeric expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9066-104">구문</span><span class="sxs-lookup"><span data-stu-id="b9066-104">Syntax</span></span>  
  
```  
  
ABS(numeric_expression)  
```  
  
## <a name="arguments"></a><span data-ttu-id="b9066-105">인수</span><span class="sxs-lookup"><span data-stu-id="b9066-105">Arguments</span></span>  
 <span data-ttu-id="b9066-106">*numeric_expression*</span><span class="sxs-lookup"><span data-stu-id="b9066-106">*numeric_expression*</span></span>  
 <span data-ttu-id="b9066-107">부호 있는 숫자 식이거나 부호 없는 숫자 식입니다.</span><span class="sxs-lookup"><span data-stu-id="b9066-107">Is a signed or unsigned numeric expression.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="b9066-108">결과 형식</span><span class="sxs-lookup"><span data-stu-id="b9066-108">Result Types</span></span>  
 <span data-ttu-id="b9066-109">함수에 전달된 숫자 식의 데이터 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="b9066-109">The data type of the numeric expression submitted to the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b9066-110">설명</span><span class="sxs-lookup"><span data-stu-id="b9066-110">Remarks</span></span>  
 <span data-ttu-id="b9066-111">인수가 Null이면 ABS 결과도 Null입니다.</span><span class="sxs-lookup"><span data-stu-id="b9066-111">ABS returns a null result if the argument is null.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="b9066-112">식 예</span><span class="sxs-lookup"><span data-stu-id="b9066-112">Expression Examples</span></span>  
 <span data-ttu-id="b9066-113">이 예에서는 ABS 함수를 양수와 음수에 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="b9066-113">These examples apply the ABS function to a positive and a negative number.</span></span> <span data-ttu-id="b9066-114">둘 다 1.23을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="b9066-114">Both return 1.23.</span></span>  
  
```  
ABS(-1.23)  
ABS(1.23)  
```  
  
 <span data-ttu-id="b9066-115">이 예에서는 변수 **HighTemperature** 와 **LowTempature**의 값을 빼는 식에 ABS 함수를 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="b9066-115">This example applies the ABS function to an expression that subtracts values in the variables **HighTemperature** and **LowTempature**.</span></span>  
  
```  
ABS(@HighTemperature - @LowTemperature)  
```  
  
## <a name="see-also"></a><span data-ttu-id="b9066-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b9066-116">See Also</span></span>  
 [<span data-ttu-id="b9066-117">함수&#40;SSIS 식&#41;</span><span class="sxs-lookup"><span data-stu-id="b9066-117">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
