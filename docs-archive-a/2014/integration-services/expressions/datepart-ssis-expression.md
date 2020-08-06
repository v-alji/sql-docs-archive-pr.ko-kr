---
title: DATEPART(SSIS 식) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- dates [Integration Services], DATEPART
- DATEPART function
ms.assetid: 3e590094-fc49-4144-805f-fdc1bf2fe509
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8aed7146c74c6738ba979f422bd65b7e1b539e15
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731916"
---
# <a name="datepart-ssis-expression"></a><span data-ttu-id="d0bff-102">DATEPART(SSIS 식)</span><span class="sxs-lookup"><span data-stu-id="d0bff-102">DATEPART (SSIS Expression)</span></span>
  <span data-ttu-id="d0bff-103">날짜의 특정 부분을 나타내는 정수를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="d0bff-103">Returns an integer representing a datepart of a date.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0bff-104">구문</span><span class="sxs-lookup"><span data-stu-id="d0bff-104">Syntax</span></span>  
  
```  
  
DATEPART(datepart, date)  
```  
  
## <a name="arguments"></a><span data-ttu-id="d0bff-105">인수</span><span class="sxs-lookup"><span data-stu-id="d0bff-105">Arguments</span></span>  
 <span data-ttu-id="d0bff-106">*datepart*</span><span class="sxs-lookup"><span data-stu-id="d0bff-106">*datepart*</span></span>  
 <span data-ttu-id="d0bff-107">새 값을 반환할 날짜 부분을 지정하는 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="d0bff-107">Is the parameter that specifies for which part of the date to return a new value.</span></span>  
  
 <span data-ttu-id="d0bff-108">*date*</span><span class="sxs-lookup"><span data-stu-id="d0bff-108">*date*</span></span>  
 <span data-ttu-id="d0bff-109">유효한 날짜 또는 날짜 형식의 문자열을 반환하는 식입니다.</span><span class="sxs-lookup"><span data-stu-id="d0bff-109">Is an expression that returns a valid date or a string in date format.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="d0bff-110">결과 형식</span><span class="sxs-lookup"><span data-stu-id="d0bff-110">Result Types</span></span>  
 <span data-ttu-id="d0bff-111">DT_I4</span><span class="sxs-lookup"><span data-stu-id="d0bff-111">DT_I4</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d0bff-112">설명</span><span class="sxs-lookup"><span data-stu-id="d0bff-112">Remarks</span></span>  
 <span data-ttu-id="d0bff-113">인수가 Null이면 DATEPART 결과도 Null입니다.</span><span class="sxs-lookup"><span data-stu-id="d0bff-113">DATEPART returns a null result if the argument is null.</span></span>  
  
 <span data-ttu-id="d0bff-114">날짜 리터럴은 다음의 날짜 데이터 형식 중 하나로 명시적 캐스팅되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0bff-114">A date literal must be explicitly cast to one of the date data types.</span></span> <span data-ttu-id="d0bff-115">자세한 내용은 [Integration Services Data Types](../data-flow/integration-services-data-types.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d0bff-115">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
 <span data-ttu-id="d0bff-116">다음 표에서는 식 계산기가 인식하는 날짜 부분 및 약어를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="d0bff-116">The following table lists the dateparts and abbreviations recognized by the expression evaluator.</span></span> <span data-ttu-id="d0bff-117">날짜 부분 이름은 대/소문자를 구분하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d0bff-117">Datepart names are not case sensitive.</span></span>  
  
|<span data-ttu-id="d0bff-118">날짜 부분</span><span class="sxs-lookup"><span data-stu-id="d0bff-118">Datepart</span></span>|<span data-ttu-id="d0bff-119">약어</span><span class="sxs-lookup"><span data-stu-id="d0bff-119">Abbreviations</span></span>|  
|--------------|-------------------|  
|<span data-ttu-id="d0bff-120">Year</span><span class="sxs-lookup"><span data-stu-id="d0bff-120">Year</span></span>|<span data-ttu-id="d0bff-121">yy, yyyy</span><span class="sxs-lookup"><span data-stu-id="d0bff-121">yy, yyyy</span></span>|  
|<span data-ttu-id="d0bff-122">Quarter</span><span class="sxs-lookup"><span data-stu-id="d0bff-122">Quarter</span></span>|<span data-ttu-id="d0bff-123">qq, q</span><span class="sxs-lookup"><span data-stu-id="d0bff-123">qq, q</span></span>|  
|<span data-ttu-id="d0bff-124">Month</span><span class="sxs-lookup"><span data-stu-id="d0bff-124">Month</span></span>|<span data-ttu-id="d0bff-125">mm, m</span><span class="sxs-lookup"><span data-stu-id="d0bff-125">mm, m</span></span>|  
|<span data-ttu-id="d0bff-126">Dayofyear</span><span class="sxs-lookup"><span data-stu-id="d0bff-126">Dayofyear</span></span>|<span data-ttu-id="d0bff-127">dy, y</span><span class="sxs-lookup"><span data-stu-id="d0bff-127">dy, y</span></span>|  
|<span data-ttu-id="d0bff-128">일</span><span class="sxs-lookup"><span data-stu-id="d0bff-128">Day</span></span>|<span data-ttu-id="d0bff-129">dd, d</span><span class="sxs-lookup"><span data-stu-id="d0bff-129">dd, d</span></span>|  
|<span data-ttu-id="d0bff-130">Week</span><span class="sxs-lookup"><span data-stu-id="d0bff-130">Week</span></span>|<span data-ttu-id="d0bff-131">wk, ww</span><span class="sxs-lookup"><span data-stu-id="d0bff-131">wk, ww</span></span>|  
|<span data-ttu-id="d0bff-132">요일</span><span class="sxs-lookup"><span data-stu-id="d0bff-132">Weekday</span></span>|<span data-ttu-id="d0bff-133">dw</span><span class="sxs-lookup"><span data-stu-id="d0bff-133">dw</span></span>|  
|<span data-ttu-id="d0bff-134">Hour</span><span class="sxs-lookup"><span data-stu-id="d0bff-134">Hour</span></span>|<span data-ttu-id="d0bff-135">Hh</span><span class="sxs-lookup"><span data-stu-id="d0bff-135">Hh</span></span>|  
|<span data-ttu-id="d0bff-136">Minute</span><span class="sxs-lookup"><span data-stu-id="d0bff-136">Minute</span></span>|<span data-ttu-id="d0bff-137">mi, n</span><span class="sxs-lookup"><span data-stu-id="d0bff-137">mi, n</span></span>|  
|<span data-ttu-id="d0bff-138">초</span><span class="sxs-lookup"><span data-stu-id="d0bff-138">Second</span></span>|<span data-ttu-id="d0bff-139">ss, s</span><span class="sxs-lookup"><span data-stu-id="d0bff-139">ss, s</span></span>|  
|<span data-ttu-id="d0bff-140">Millisecond</span><span class="sxs-lookup"><span data-stu-id="d0bff-140">Millisecond</span></span>|<span data-ttu-id="d0bff-141">Ms</span><span class="sxs-lookup"><span data-stu-id="d0bff-141">Ms</span></span>|  
  
## <a name="ssis-expression-examples"></a><span data-ttu-id="d0bff-142">SSIS 식 예</span><span class="sxs-lookup"><span data-stu-id="d0bff-142">SSIS Expression Examples</span></span>  
 <span data-ttu-id="d0bff-143">이 예에서는 날짜 리터럴의 월을 나타내는 정수가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="d0bff-143">This example returns the integer that represents the month in a date literal.</span></span> <span data-ttu-id="d0bff-144">날짜 형식이 "mm/dd/yyyy"이면 이 예에서는 11이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="d0bff-144">If the date is in mm/dd/yyyy" format, this example returns 11.</span></span>  
  
```  
DATEPART("month", (DT_DBTIMESTAMP)"11/04/2002")  
```  
  
 <span data-ttu-id="d0bff-145">이 예에서는 **ModifiedDate** 열의 일 부분을 나타내는 정수를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="d0bff-145">This example returns the integer that represents the day in the **ModifiedDate** column.</span></span>  
  
```  
DATEPART("dd", ModifiedDate)  
```  
  
 <span data-ttu-id="d0bff-146">이 예에서는 현재 날짜의 연도를 나타내는 정수를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="d0bff-146">This example returns the integer that represents the year of the current date.</span></span>  
  
```  
DATEPART("yy",GETDATE())  
```  
  
## <a name="see-also"></a><span data-ttu-id="d0bff-147">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d0bff-147">See Also</span></span>  
 <span data-ttu-id="d0bff-148">[DATEADD&#40;SSIS 식&#41;](dateadd-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="d0bff-148">[DATEADD &#40;SSIS Expression&#41;](dateadd-ssis-expression.md) </span></span>  
 <span data-ttu-id="d0bff-149">[DATEDIFF&#40;SSIS 식&#41;](datediff-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="d0bff-149">[DATEDIFF &#40;SSIS Expression&#41;](datediff-ssis-expression.md) </span></span>  
 <span data-ttu-id="d0bff-150">[DAY&#40;SSIS 식&#41;](day-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="d0bff-150">[DAY &#40;SSIS Expression&#41;](day-ssis-expression.md) </span></span>  
 <span data-ttu-id="d0bff-151">[MONTH&#40;SSIS 식&#41;](month-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="d0bff-151">[MONTH &#40;SSIS Expression&#41;](month-ssis-expression.md) </span></span>  
 <span data-ttu-id="d0bff-152">[YEAR&#40;SSIS 식&#41;](year-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="d0bff-152">[YEAR &#40;SSIS Expression&#41;](year-ssis-expression.md) </span></span>  
 [<span data-ttu-id="d0bff-153">함수&#40;SSIS 식&#41;</span><span class="sxs-lookup"><span data-stu-id="d0bff-153">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
