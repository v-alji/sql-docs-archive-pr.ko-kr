---
title: DAY(SSIS 식) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- DAY function
- dates [Integration Services], DAY
ms.assetid: d8447187-49df-45b7-a98e-142ad44fd3e2
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1b7acac3f3949cbbd07adbe6382ea3d875f94cb2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731912"
---
# <a name="day-ssis-expression"></a><span data-ttu-id="19038-102">DAY(SSIS 식)</span><span class="sxs-lookup"><span data-stu-id="19038-102">DAY (SSIS Expression)</span></span>
  <span data-ttu-id="19038-103">날짜의 일 부분을 나타내는 정수를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="19038-103">Returns an integer that represents the day datepart of a date.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19038-104">구문</span><span class="sxs-lookup"><span data-stu-id="19038-104">Syntax</span></span>  
  
```  
  
DAY(date)  
```  
  
## <a name="arguments"></a><span data-ttu-id="19038-105">인수</span><span class="sxs-lookup"><span data-stu-id="19038-105">Arguments</span></span>  
 <span data-ttu-id="19038-106">*date*</span><span class="sxs-lookup"><span data-stu-id="19038-106">*date*</span></span>  
 <span data-ttu-id="19038-107">유효한 날짜 또는 날짜 형식의 문자열을 반환하는 식입니다.</span><span class="sxs-lookup"><span data-stu-id="19038-107">Is an expression that returns a valid date or a string in date format.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="19038-108">결과 형식</span><span class="sxs-lookup"><span data-stu-id="19038-108">Result Types</span></span>  
 <span data-ttu-id="19038-109">DT_I4</span><span class="sxs-lookup"><span data-stu-id="19038-109">DT_I4</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="19038-110">설명</span><span class="sxs-lookup"><span data-stu-id="19038-110">Remarks</span></span>  
 <span data-ttu-id="19038-111">인수가 Null이면 DAY 결과도 Null입니다.</span><span class="sxs-lookup"><span data-stu-id="19038-111">DAY returns a null result if the argument is null.</span></span>  
  
 <span data-ttu-id="19038-112">날짜 리터럴은 다음의 날짜 데이터 형식 중 하나로 명시적 캐스팅되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="19038-112">A date literal must be explicitly cast to one of the date data types.</span></span> <span data-ttu-id="19038-113">자세한 내용은 [Integration Services Data Types](../data-flow/integration-services-data-types.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="19038-113">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="19038-114">날짜 리터럴이 DT_DBTIMESTAMPOFFSET 및 DT_DBTIMESTAMP2 날짜 데이터 형식 중 하나로 명시적 캐스팅되면 식의 유효성 검사가 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="19038-114">The expression fails to validate when a date literal is explicitly cast to one of these date data types: DT_DBTIMESTAMPOFFSET and DT_DBTIMESTAMP2.</span></span>  
  
 <span data-ttu-id="19038-115">DAY 함수는 DATEPART("Day", date) 함수보다 간단하지만 동일한 결과를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="19038-115">Using the DAY function is briefer but equivalent to using DATEPART("Day", date).</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="19038-116">식 예</span><span class="sxs-lookup"><span data-stu-id="19038-116">Expression Examples</span></span>  
 <span data-ttu-id="19038-117">이 예에서는 날짜 리터럴의 일 수를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="19038-117">This example returns the number of the day in a date literal.</span></span> <span data-ttu-id="19038-118">날짜 형식이 "mm/dd/yyyy"이면 23이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="19038-118">If the date format is in "mm/dd/yyyy" format, this example returns 23.</span></span>  
  
```  
DAY((DT_DBTIMESTAMP)"11/23/2002")  
```  
  
 <span data-ttu-id="19038-119">이 예에서는 **ModifiedDate** 열의 일 부분을 나타내는 정수를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="19038-119">This example returns the integer that represents the day in the **ModifiedDate** column.</span></span>  
  
```  
DAY(ModifiedDate)  
```  
  
 <span data-ttu-id="19038-120">이 예에서는 현재 날짜의 일을 나타내는 정수를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="19038-120">This example returns the integer that represents the day of the current date.</span></span>  
  
```  
DAY(GETDATE())  
```  
  
## <a name="see-also"></a><span data-ttu-id="19038-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="19038-121">See Also</span></span>  
 <span data-ttu-id="19038-122">[DATEADD&#40;SSIS 식&#41;](dateadd-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="19038-122">[DATEADD &#40;SSIS Expression&#41;](dateadd-ssis-expression.md) </span></span>  
 <span data-ttu-id="19038-123">[DATEDIFF&#40;SSIS 식&#41;](datediff-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="19038-123">[DATEDIFF &#40;SSIS Expression&#41;](datediff-ssis-expression.md) </span></span>  
 <span data-ttu-id="19038-124">[DATEPART&#40;SSIS 식&#41;](datepart-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="19038-124">[DATEPART &#40;SSIS Expression&#41;](datepart-ssis-expression.md) </span></span>  
 <span data-ttu-id="19038-125">[MONTH&#40;SSIS 식&#41;](month-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="19038-125">[MONTH &#40;SSIS Expression&#41;](month-ssis-expression.md) </span></span>  
 <span data-ttu-id="19038-126">[YEAR&#40;SSIS 식&#41;](year-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="19038-126">[YEAR &#40;SSIS Expression&#41;](year-ssis-expression.md) </span></span>  
 [<span data-ttu-id="19038-127">함수&#40;SSIS 식&#41;</span><span class="sxs-lookup"><span data-stu-id="19038-127">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
