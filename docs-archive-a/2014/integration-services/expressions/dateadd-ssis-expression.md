---
title: DATEADD(SSIS 식) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- dates [Integration Services], DATEADD
- dates [Integration Services]
- DATEADD function
ms.assetid: fa5c37b1-2ddc-4857-8f8e-f6d5643b654f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9feb288318bdf9705928cb930f175f5c170c384e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736639"
---
# <a name="dateadd-ssis-expression"></a><span data-ttu-id="b4531-102">DATEADD(SSIS 식)</span><span class="sxs-lookup"><span data-stu-id="b4531-102">DATEADD (SSIS Expression)</span></span>
  <span data-ttu-id="b4531-103">날짜에서 지정한 날짜 부분에 날짜 또는 시간 간격을 나타내는 숫자를 더한 후 새로운 DT_DBTIMESTAMP 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="b4531-103">Returns a new DT_DBTIMESTAMP value after adding a number that represents a date or time interval to the specified datepart in a date.</span></span> <span data-ttu-id="b4531-104">숫자 매개 변수는 정수로 계산되고 날짜 매개 변수는 유효한 날짜여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4531-104">The number parameter must evaluate to an integer, and the date parameter must evaluate to a valid date.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4531-105">구문</span><span class="sxs-lookup"><span data-stu-id="b4531-105">Syntax</span></span>  
  
```  
  
DATEADD(datepart, number, date)  
```  
  
## <a name="arguments"></a><span data-ttu-id="b4531-106">인수</span><span class="sxs-lookup"><span data-stu-id="b4531-106">Arguments</span></span>  
 <span data-ttu-id="b4531-107">*datepart*</span><span class="sxs-lookup"><span data-stu-id="b4531-107">*datepart*</span></span>  
 <span data-ttu-id="b4531-108">숫자를 더할 날짜 부분을 지정하는 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="b4531-108">Is the parameter that specifies which part of the date to add a number to.</span></span>  
  
 <span data-ttu-id="b4531-109">*number*</span><span class="sxs-lookup"><span data-stu-id="b4531-109">*number*</span></span>  
 <span data-ttu-id="b4531-110">*datepart*에 더해지는 값입니다.</span><span class="sxs-lookup"><span data-stu-id="b4531-110">Is the value used to increment *datepart*.</span></span> <span data-ttu-id="b4531-111">값은 식을 구문 분석할 때 알려진 정수 값이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4531-111">The value must be an integer value that is known when the expression is parsed.</span></span>  
  
 <span data-ttu-id="b4531-112">*date*</span><span class="sxs-lookup"><span data-stu-id="b4531-112">*date*</span></span>  
 <span data-ttu-id="b4531-113">유효한 날짜 또는 날짜 형식의 문자열을 반환하는 식입니다.</span><span class="sxs-lookup"><span data-stu-id="b4531-113">Is an expression that returns a valid date or a string in date format.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="b4531-114">결과 형식</span><span class="sxs-lookup"><span data-stu-id="b4531-114">Result Types</span></span>  
 <span data-ttu-id="b4531-115">DT_DBTIMESTAMP</span><span class="sxs-lookup"><span data-stu-id="b4531-115">DT_DBTIMESTAMP</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b4531-116">설명</span><span class="sxs-lookup"><span data-stu-id="b4531-116">Remarks</span></span>  
 <span data-ttu-id="b4531-117">다음 표에서는 식 계산기가 인식하는 날짜 부분 및 약어를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="b4531-117">The following table lists the dateparts and abbreviations recognized by the expression evaluator.</span></span> <span data-ttu-id="b4531-118">날짜 부분 이름은 대/소문자를 구분하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b4531-118">Datepart names are not case sensitive.</span></span>  
  
|<span data-ttu-id="b4531-119">날짜 부분</span><span class="sxs-lookup"><span data-stu-id="b4531-119">Datepart</span></span>|<span data-ttu-id="b4531-120">약어</span><span class="sxs-lookup"><span data-stu-id="b4531-120">Abbreviations</span></span>|  
|--------------|-------------------|  
|<span data-ttu-id="b4531-121">Year</span><span class="sxs-lookup"><span data-stu-id="b4531-121">Year</span></span>|<span data-ttu-id="b4531-122">yy, yyyy</span><span class="sxs-lookup"><span data-stu-id="b4531-122">yy, yyyy</span></span>|  
|<span data-ttu-id="b4531-123">Quarter</span><span class="sxs-lookup"><span data-stu-id="b4531-123">Quarter</span></span>|<span data-ttu-id="b4531-124">qq, q</span><span class="sxs-lookup"><span data-stu-id="b4531-124">qq, q</span></span>|  
|<span data-ttu-id="b4531-125">Month</span><span class="sxs-lookup"><span data-stu-id="b4531-125">Month</span></span>|<span data-ttu-id="b4531-126">mm, m</span><span class="sxs-lookup"><span data-stu-id="b4531-126">mm, m</span></span>|  
|<span data-ttu-id="b4531-127">Dayofyear</span><span class="sxs-lookup"><span data-stu-id="b4531-127">Dayofyear</span></span>|<span data-ttu-id="b4531-128">dy, y</span><span class="sxs-lookup"><span data-stu-id="b4531-128">dy, y</span></span>|  
|<span data-ttu-id="b4531-129">일</span><span class="sxs-lookup"><span data-stu-id="b4531-129">Day</span></span>|<span data-ttu-id="b4531-130">dd, d</span><span class="sxs-lookup"><span data-stu-id="b4531-130">dd, d</span></span>|  
|<span data-ttu-id="b4531-131">Week</span><span class="sxs-lookup"><span data-stu-id="b4531-131">Week</span></span>|<span data-ttu-id="b4531-132">wk, ww</span><span class="sxs-lookup"><span data-stu-id="b4531-132">wk, ww</span></span>|  
|<span data-ttu-id="b4531-133">요일</span><span class="sxs-lookup"><span data-stu-id="b4531-133">Weekday</span></span>|<span data-ttu-id="b4531-134">dw, w</span><span class="sxs-lookup"><span data-stu-id="b4531-134">dw, w</span></span>|  
|<span data-ttu-id="b4531-135">Hour</span><span class="sxs-lookup"><span data-stu-id="b4531-135">Hour</span></span>|<span data-ttu-id="b4531-136">Hh</span><span class="sxs-lookup"><span data-stu-id="b4531-136">Hh</span></span>|  
|<span data-ttu-id="b4531-137">Minute</span><span class="sxs-lookup"><span data-stu-id="b4531-137">Minute</span></span>|<span data-ttu-id="b4531-138">mi, n</span><span class="sxs-lookup"><span data-stu-id="b4531-138">mi, n</span></span>|  
|<span data-ttu-id="b4531-139">초</span><span class="sxs-lookup"><span data-stu-id="b4531-139">Second</span></span>|<span data-ttu-id="b4531-140">ss, s</span><span class="sxs-lookup"><span data-stu-id="b4531-140">ss, s</span></span>|  
|<span data-ttu-id="b4531-141">Millisecond</span><span class="sxs-lookup"><span data-stu-id="b4531-141">Millisecond</span></span>|<span data-ttu-id="b4531-142">Ms</span><span class="sxs-lookup"><span data-stu-id="b4531-142">Ms</span></span>|  
  
 <span data-ttu-id="b4531-143">식을 구문 분석할 때 *number* 인수를 사용할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4531-143">The *number* argument must be available when the expression is parsed.</span></span> <span data-ttu-id="b4531-144">인수는 상수 또는 변수일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4531-144">The argument can be a constant or a variable.</span></span> <span data-ttu-id="b4531-145">식을 구문 분석할 때 값을 알 수 없으므로 열 값을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b4531-145">You cannot use column values because the values are not known when the expression is parsed.</span></span>  
  
 <span data-ttu-id="b4531-146">*datepart* 인수는 따옴표로 묶어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4531-146">The *datepart* argument must be enclosed by quotation marks.</span></span>  
  
 <span data-ttu-id="b4531-147">날짜 리터럴은 다음의 날짜 데이터 형식 중 하나로 명시적 캐스팅되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4531-147">A date literal must be explicitly cast to one of the date data types.</span></span> <span data-ttu-id="b4531-148">자세한 내용은 [Integration Services Data Types](../data-flow/integration-services-data-types.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b4531-148">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
 <span data-ttu-id="b4531-149">인수가 Null이면 DATEADD 결과도 Null입니다.</span><span class="sxs-lookup"><span data-stu-id="b4531-149">DATEADD returns a null result if the argument is null.</span></span>  
  
 <span data-ttu-id="b4531-150">날짜가 잘못되었거나 날짜 또는 시간 단위가 문자열이 아니거나 증분이 고정 정수가 아니면 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="b4531-150">Errors occur if a date is invalid, if the date or time unit is not a string, or if the increment is not a static integer.</span></span>  
  
## <a name="ssis-expression-examples"></a><span data-ttu-id="b4531-151">SSIS 식 예</span><span class="sxs-lookup"><span data-stu-id="b4531-151">SSIS Expression Examples</span></span>  
 <span data-ttu-id="b4531-152">이 예에서는 현재 날짜에 1개월을 더합니다.</span><span class="sxs-lookup"><span data-stu-id="b4531-152">This example adds one month to the current date.</span></span>  
  
```  
DATEADD("Month", 1,GETDATE())  
```  
  
 <span data-ttu-id="b4531-153">이 예에서는 **ModifiedDate** 열의 날짜에 21일을 더합니다.</span><span class="sxs-lookup"><span data-stu-id="b4531-153">This example adds 21 days to the dates in the **ModifiedDate** column.</span></span>  
  
```  
DATEADD("day", 21, ModifiedDate)  
```  
  
 <span data-ttu-id="b4531-154">이 예에서는 리터럴 날짜에 2년을 더합니다.</span><span class="sxs-lookup"><span data-stu-id="b4531-154">This example adds 2 years to a literal date.</span></span>  
  
```  
DATEADD("yyyy", 2, (DT_DBTIMESTAMP)"8/6/2003")  
```  
  
## <a name="see-also"></a><span data-ttu-id="b4531-155">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b4531-155">See Also</span></span>  
 <span data-ttu-id="b4531-156">[DATEDIFF&#40;SSIS 식&#41;](datediff-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="b4531-156">[DATEDIFF &#40;SSIS Expression&#41;](datediff-ssis-expression.md) </span></span>  
 <span data-ttu-id="b4531-157">[DATEPART&#40;SSIS 식&#41;](datepart-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="b4531-157">[DATEPART &#40;SSIS Expression&#41;](datepart-ssis-expression.md) </span></span>  
 <span data-ttu-id="b4531-158">[DAY&#40;SSIS 식&#41;](day-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="b4531-158">[DAY &#40;SSIS Expression&#41;](day-ssis-expression.md) </span></span>  
 <span data-ttu-id="b4531-159">[MONTH&#40;SSIS 식&#41;](month-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="b4531-159">[MONTH &#40;SSIS Expression&#41;](month-ssis-expression.md) </span></span>  
 <span data-ttu-id="b4531-160">[YEAR&#40;SSIS 식&#41;](year-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="b4531-160">[YEAR &#40;SSIS Expression&#41;](year-ssis-expression.md) </span></span>  
 [<span data-ttu-id="b4531-161">함수&#40;SSIS 식&#41;</span><span class="sxs-lookup"><span data-stu-id="b4531-161">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
