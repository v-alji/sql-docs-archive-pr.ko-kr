---
title: DATEDIFF(SSIS 식) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- DATEDIFF statement
- dates [Integration Services], DATEDIFF
ms.assetid: 449b327f-47c7-4709-8bc6-4ee9a35cc330
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 33edf2a152f70bb8c5bbd1f69cb87354e099b246
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731920"
---
# <a name="datediff-ssis-expression"></a><span data-ttu-id="55f11-102">DATEDIFF(SSIS 식)</span><span class="sxs-lookup"><span data-stu-id="55f11-102">DATEDIFF (SSIS Expression)</span></span>
  <span data-ttu-id="55f11-103">지정한 두 날짜 간에 교차되는 날짜와 시간 경계값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="55f11-103">Returns the number of date and time boundaries crossed between two specified dates.</span></span> <span data-ttu-id="55f11-104">*datepart* 매개 변수는 비교할 날짜 및 시간 범위를 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="55f11-104">The *datepart* parameter identifies which date and time boundaries to compare.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55f11-105">구문</span><span class="sxs-lookup"><span data-stu-id="55f11-105">Syntax</span></span>  
  
```  
  
DATEDIFF(datepart, startdate, endate)  
```  
  
## <a name="arguments"></a><span data-ttu-id="55f11-106">인수</span><span class="sxs-lookup"><span data-stu-id="55f11-106">Arguments</span></span>  
 <span data-ttu-id="55f11-107">*datepart*</span><span class="sxs-lookup"><span data-stu-id="55f11-107">*datepart*</span></span>  
 <span data-ttu-id="55f11-108">비교하여 값을 반환할 날짜 부분을 지정하는 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="55f11-108">Is the parameter that specifies which part of the date to compare and return a value for.</span></span>  
  
 <span data-ttu-id="55f11-109">*startdate*</span><span class="sxs-lookup"><span data-stu-id="55f11-109">*startdate*</span></span>  
 <span data-ttu-id="55f11-110">간격의 시작 날짜입니다.</span><span class="sxs-lookup"><span data-stu-id="55f11-110">Is the start date of the interval.</span></span>  
  
 <span data-ttu-id="55f11-111">*endate*</span><span class="sxs-lookup"><span data-stu-id="55f11-111">*endate*</span></span>  
 <span data-ttu-id="55f11-112">간격의 종료 날짜입니다.</span><span class="sxs-lookup"><span data-stu-id="55f11-112">Is the end date of the interval.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="55f11-113">결과 형식</span><span class="sxs-lookup"><span data-stu-id="55f11-113">Result Types</span></span>  
 <span data-ttu-id="55f11-114">DT_I4</span><span class="sxs-lookup"><span data-stu-id="55f11-114">DT_I4</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="55f11-115">설명</span><span class="sxs-lookup"><span data-stu-id="55f11-115">Remarks</span></span>  
 <span data-ttu-id="55f11-116">다음 표에서는 식 계산기가 인식하는 날짜 부분 및 약어를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="55f11-116">The following table lists the dateparts and abbreviations recognized by the expression evaluator.</span></span>  
  
|<span data-ttu-id="55f11-117">날짜 부분</span><span class="sxs-lookup"><span data-stu-id="55f11-117">Datepart</span></span>|<span data-ttu-id="55f11-118">약어</span><span class="sxs-lookup"><span data-stu-id="55f11-118">Abbreviations</span></span>|  
|--------------|-------------------|  
|<span data-ttu-id="55f11-119">Year</span><span class="sxs-lookup"><span data-stu-id="55f11-119">Year</span></span>|<span data-ttu-id="55f11-120">yy, yyyy</span><span class="sxs-lookup"><span data-stu-id="55f11-120">yy, yyyy</span></span>|  
|<span data-ttu-id="55f11-121">Quarter</span><span class="sxs-lookup"><span data-stu-id="55f11-121">Quarter</span></span>|<span data-ttu-id="55f11-122">qq, q</span><span class="sxs-lookup"><span data-stu-id="55f11-122">qq, q</span></span>|  
|<span data-ttu-id="55f11-123">Month</span><span class="sxs-lookup"><span data-stu-id="55f11-123">Month</span></span>|<span data-ttu-id="55f11-124">mm, m</span><span class="sxs-lookup"><span data-stu-id="55f11-124">mm, m</span></span>|  
|<span data-ttu-id="55f11-125">Dayofyear</span><span class="sxs-lookup"><span data-stu-id="55f11-125">Dayofyear</span></span>|<span data-ttu-id="55f11-126">dy, y</span><span class="sxs-lookup"><span data-stu-id="55f11-126">dy, y</span></span>|  
|<span data-ttu-id="55f11-127">일</span><span class="sxs-lookup"><span data-stu-id="55f11-127">Day</span></span>|<span data-ttu-id="55f11-128">dd, d</span><span class="sxs-lookup"><span data-stu-id="55f11-128">dd, d</span></span>|  
|<span data-ttu-id="55f11-129">Week</span><span class="sxs-lookup"><span data-stu-id="55f11-129">Week</span></span>|<span data-ttu-id="55f11-130">wk, ww</span><span class="sxs-lookup"><span data-stu-id="55f11-130">wk, ww</span></span>|  
|<span data-ttu-id="55f11-131">요일</span><span class="sxs-lookup"><span data-stu-id="55f11-131">Weekday</span></span>|<span data-ttu-id="55f11-132">dw, w</span><span class="sxs-lookup"><span data-stu-id="55f11-132">dw, w</span></span>|  
|<span data-ttu-id="55f11-133">Hour</span><span class="sxs-lookup"><span data-stu-id="55f11-133">Hour</span></span>|<span data-ttu-id="55f11-134">Hh</span><span class="sxs-lookup"><span data-stu-id="55f11-134">Hh</span></span>|  
|<span data-ttu-id="55f11-135">Minute</span><span class="sxs-lookup"><span data-stu-id="55f11-135">Minute</span></span>|<span data-ttu-id="55f11-136">mi, n</span><span class="sxs-lookup"><span data-stu-id="55f11-136">mi, n</span></span>|  
|<span data-ttu-id="55f11-137">초</span><span class="sxs-lookup"><span data-stu-id="55f11-137">Second</span></span>|<span data-ttu-id="55f11-138">ss, s</span><span class="sxs-lookup"><span data-stu-id="55f11-138">ss, s</span></span>|  
|<span data-ttu-id="55f11-139">Millisecond</span><span class="sxs-lookup"><span data-stu-id="55f11-139">Millisecond</span></span>|<span data-ttu-id="55f11-140">Ms</span><span class="sxs-lookup"><span data-stu-id="55f11-140">Ms</span></span>|  
  
 <span data-ttu-id="55f11-141">인수가 Null이면 DATEDIFF 결과도 Null입니다.</span><span class="sxs-lookup"><span data-stu-id="55f11-141">DATEDIFF returns a null result if any argument is null.</span></span>  
  
 <span data-ttu-id="55f11-142">날짜 리터럴은 다음의 날짜 데이터 형식 중 하나로 명시적 캐스팅되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="55f11-142">A date literal must be explicitly cast to one of the date data types.</span></span> <span data-ttu-id="55f11-143">자세한 내용은 [Integration Services Data Types](../data-flow/integration-services-data-types.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="55f11-143">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
 <span data-ttu-id="55f11-144">올바른 날짜가 아니거나, 날짜 또는 시간 단위가 문자열이 아니거나, 시작 날짜가 날짜가 아니거나, 종료 날짜가 날짜가 아니면 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="55f11-144">An error occurs if a date is not valid, if the date or time unit is not a string, if the start date is not a date, or if the end date is not a date.</span></span>  
  
 <span data-ttu-id="55f11-145">종료 날짜가 시작 날짜보다 빠르면 음수가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="55f11-145">If the end date is earlier than the start date, the function returns a negative number.</span></span> <span data-ttu-id="55f11-146">시작 날짜와 종료 날짜가 같거나 동일한 간격 내에 있으면 0이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="55f11-146">If the start and end dates are equal or fall within the same interval, the function returns zero.</span></span>  
  
## <a name="ssis-expression-examples"></a><span data-ttu-id="55f11-147">SSIS 식 예</span><span class="sxs-lookup"><span data-stu-id="55f11-147">SSIS Expression Examples</span></span>  
 <span data-ttu-id="55f11-148">이 예에서는 두 날짜 리터럴 사이의 일 수를 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="55f11-148">This example calculates the number of days between two date literals.</span></span> <span data-ttu-id="55f11-149">날짜 형식이 "mm/dd/yyyy"이면 7이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="55f11-149">If the date is in "mm/dd/yyyy" format, the function returns 7.</span></span>  
  
```  
DATEDIFF("dd", (DT_DBTIMESTAMP)"8/1/2003", (DT_DBTIMESTAMP)"8/8/2003")  
```  
  
 <span data-ttu-id="55f11-150">이 예에서는 날짜 리터럴과 현재 날짜 사이의 개월 수를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="55f11-150">This example returns the number of months between a date literal and the current date.</span></span>  
  
```  
DATEDIFF("mm", (DT_DBTIMESTAMP)"8/1/2003",GETDATE())  
```  
  
 <span data-ttu-id="55f11-151">이 예에서는 **ModifiedDate** 열의 날짜와 **YearEndDate** 변수 사이의 주 수를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="55f11-151">This example returns the number of weeks between the date in the **ModifiedDate** column and the **YearEndDate** variable.</span></span> <span data-ttu-id="55f11-152">**YearEndDate** 에 데이터 형식이 있는 경우에는 `date` 명시적 캐스팅이 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="55f11-152">If **YearEndDate** has a `date` data type, no explicit casting is required.</span></span>  
  
```  
DATEDIFF("Week", ModifiedDate,@YearEndDate)  
```  
  
## <a name="see-also"></a><span data-ttu-id="55f11-153">참고 항목</span><span class="sxs-lookup"><span data-stu-id="55f11-153">See Also</span></span>  
 <span data-ttu-id="55f11-154">[DATEADD&#40;SSIS 식&#41;](dateadd-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="55f11-154">[DATEADD &#40;SSIS Expression&#41;](dateadd-ssis-expression.md) </span></span>  
 <span data-ttu-id="55f11-155">[DATEPART&#40;SSIS 식&#41;](datepart-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="55f11-155">[DATEPART &#40;SSIS Expression&#41;](datepart-ssis-expression.md) </span></span>  
 <span data-ttu-id="55f11-156">[DAY&#40;SSIS 식&#41;](day-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="55f11-156">[DAY &#40;SSIS Expression&#41;](day-ssis-expression.md) </span></span>  
 <span data-ttu-id="55f11-157">[MONTH&#40;SSIS 식&#41;](month-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="55f11-157">[MONTH &#40;SSIS Expression&#41;](month-ssis-expression.md) </span></span>  
 <span data-ttu-id="55f11-158">[YEAR&#40;SSIS 식&#41;](year-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="55f11-158">[YEAR &#40;SSIS Expression&#41;](year-ssis-expression.md) </span></span>  
 [<span data-ttu-id="55f11-159">함수&#40;SSIS 식&#41;</span><span class="sxs-lookup"><span data-stu-id="55f11-159">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
