---
title: 날짜 및 시간 형식 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- time data types [Integration Services]
- fast parse [Integration Services]
- date data types
- date and time formats for fast parse
ms.assetid: bed6e2c1-791a-4fa1-b29f-cbfdd1fa8d39
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5e6c461c0cfed6a776875831a46c94c70d895ba3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647769"
---
# <a name="date-and-time-formats"></a><span data-ttu-id="a0cc5-102">날짜 및 시간 형식</span><span class="sxs-lookup"><span data-stu-id="a0cc5-102">Date and Time Formats</span></span>
  <span data-ttu-id="a0cc5-103">빠른 구문 분석에서는 데이터 구문 분석을 위한 신속하고 간단한 루틴을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="a0cc5-103">Fast parse provides a fast, simple set of routines for parsing data.</span></span> <span data-ttu-id="a0cc5-104">빠른 구문 분석에서는 날짜 및 시간 데이터 형식에 대해 다음과 같은 형식이 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="a0cc5-104">Fast parse supports the following formats for date and time data types.</span></span>  
  
## <a name="date-data-types"></a><span data-ttu-id="a0cc5-105">날짜 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="a0cc5-105">Date Data Types</span></span>  
 <span data-ttu-id="a0cc5-106">빠른 구문 분석에서는 날짜 데이터에 대해 다음과 같은 문자열 형식이 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="a0cc5-106">Fast parse supports the following string formats for date data:</span></span>  
  
-   <span data-ttu-id="a0cc5-107">선행 공백을 포함하는 날짜 형식.</span><span class="sxs-lookup"><span data-stu-id="a0cc5-107">Date formats that include leading white spaces.</span></span> <span data-ttu-id="a0cc5-108">예를 들어 " 2004-02-03"은 유효한 값입니다.</span><span class="sxs-lookup"><span data-stu-id="a0cc5-108">For example, the value " 2004- 02-03" is valid.</span></span>  
  
-   <span data-ttu-id="a0cc5-109">다음 표에 나열된 ISO 8601 형식</span><span class="sxs-lookup"><span data-stu-id="a0cc5-109">ISO 8601 formats, as listed in the following table:</span></span>  
  
    |<span data-ttu-id="a0cc5-110">서식</span><span class="sxs-lookup"><span data-stu-id="a0cc5-110">Format</span></span>|<span data-ttu-id="a0cc5-111">Description</span><span class="sxs-lookup"><span data-stu-id="a0cc5-111">Description</span></span>|  
    |------------|-----------------|  
    |<span data-ttu-id="a0cc5-112">YYYYMMDD</span><span class="sxs-lookup"><span data-stu-id="a0cc5-112">YYYYMMDD</span></span><br /><br /> <span data-ttu-id="a0cc5-113">YYYY-MM-DD</span><span class="sxs-lookup"><span data-stu-id="a0cc5-113">YYYY-MM-DD</span></span>|<span data-ttu-id="a0cc5-114">네 자리 연도, 두 자리 월 및 두 자리 일이 포함된 기본 및 하이픈으로 연결된 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="a0cc5-114">Basic and extended formats for a four-digit year, a two-digit month, and a two-digit day.</span></span> <span data-ttu-id="a0cc5-115">하이픈으로 연결된 형식에서 날짜 부분은 하이픈(-)으로 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="a0cc5-115">In the extended format, the date parts are separated by a hyphen (-).</span></span>|  
    |<span data-ttu-id="a0cc5-116">YYYY-MM</span><span class="sxs-lookup"><span data-stu-id="a0cc5-116">YYYY-MM</span></span>|<span data-ttu-id="a0cc5-117">네 자리 연도와 두 자리 연도의 기본 및 하이픈으로 연결된 축약 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="a0cc5-117">Basic and extended reduced precision formats for a four-digit year and a two-digit month.</span></span> <span data-ttu-id="a0cc5-118">하이픈으로 연결된 형식에서 날짜 부분은 하이픈(-)으로 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="a0cc5-118">In the extended format, the date parts are separated by a hyphen (-).</span></span>|  
    |<span data-ttu-id="a0cc5-119">YYYY</span><span class="sxs-lookup"><span data-stu-id="a0cc5-119">YYYY</span></span>|<span data-ttu-id="a0cc5-120">네 자리 연도의 축약 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="a0cc5-120">Reduced precision format is a four-digit year.</span></span>|  
  
 <span data-ttu-id="a0cc5-121">빠른 구문 분석에서는 날짜 데이터에 대해 다음과 같은 형식이 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a0cc5-121">Fast parse does not support the following formats for date data:</span></span>  
  
-   <span data-ttu-id="a0cc5-122">영문자 월 값.</span><span class="sxs-lookup"><span data-stu-id="a0cc5-122">Alphabetical month values.</span></span> <span data-ttu-id="a0cc5-123">예를 들어 Oct-31-2003 날짜 형식은 유효하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a0cc5-123">For example, the date format Oct-31-2003 is not valid.</span></span>  
  
-   <span data-ttu-id="a0cc5-124">DD-MM-YYYY 및 MM-DD-YYYY와 같은 모호한 형식.</span><span class="sxs-lookup"><span data-stu-id="a0cc5-124">Ambiguous formats such as DD-MM-YYYY and MM-DD-YYYY.</span></span> <span data-ttu-id="a0cc5-125">예를 들어 03-04-1995 및 04-03-1995는 유효하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a0cc5-125">For example, the dates 03-04-1995 and 04-03-1995 are not valid.</span></span>  
  
-   <span data-ttu-id="a0cc5-126">네 자리 역년과 일 년 내의 세 자리 일의 기본 및 확장 잘림 형식(YYYYDDD 및 YYYY-DDD)입니다.</span><span class="sxs-lookup"><span data-stu-id="a0cc5-126">Basic and extended truncated formats for a four-digit calendar year and a three-digit day within a year, YYYYDDD and YYYY-DDD.</span></span>  
  
-   <span data-ttu-id="a0cc5-127">네 자리 연도, 해당 연도의 주를 나타내는 두 자리 숫자 및 해당 주의 일을 나타내는 한 자리 숫자의 기본 및 확장 형식(YYYYWwwD 및 YYYY-Www-D)입니다.</span><span class="sxs-lookup"><span data-stu-id="a0cc5-127">Basic and extended formats for a four-digit year, a two-digit number for the week of the year, and a one-digit number for the day of the week, YYYYWwwD and YYYY-Www-D</span></span>  
  
-   <span data-ttu-id="a0cc5-128">연도와 주 날짜에 대한 기본 및 확장 잘림 형식(YYYWww 및 YYYY-Www)은 네 자리 연도와 주를 나타내는 두 자리 숫자입니다.</span><span class="sxs-lookup"><span data-stu-id="a0cc5-128">Basic and extended truncated formats for a year and week date are a four-digit year and a two-digit number for the week, YYYWww and YYYY-Www</span></span>  
  
 <span data-ttu-id="a0cc5-129">빠른 구문 분석에서는 날짜가 DT_DBDATE로 출력됩니다.</span><span class="sxs-lookup"><span data-stu-id="a0cc5-129">Fast parse outputs the data as DT_DBDATE.</span></span> <span data-ttu-id="a0cc5-130">잘림 형식의 날짜 값은 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="a0cc5-130">Date values in truncated formats are padded.</span></span> <span data-ttu-id="a0cc5-131">예를 들어 YYYY는 YYYY0101이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a0cc5-131">For example, YYYY becomes YYYY0101.</span></span>  
  
 <span data-ttu-id="a0cc5-132">자세한 내용은 [Integration Services Data Types](data-flow/integration-services-data-types.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a0cc5-132">For more information, see [Integration Services Data Types](data-flow/integration-services-data-types.md).</span></span>  
  
## <a name="time-data-type"></a><span data-ttu-id="a0cc5-133">시간 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="a0cc5-133">Time Data Type</span></span>  
 <span data-ttu-id="a0cc5-134">빠른 구문 분석에서는 시간 데이터에 대해 다음과 같은 문자열 형식이 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="a0cc5-134">Fast parse supports the following string formats for time data:</span></span>  
  
-   <span data-ttu-id="a0cc5-135">선행 공백을 포함하는 시간 형식.</span><span class="sxs-lookup"><span data-stu-id="a0cc5-135">Time formats that include leading white spaces.</span></span> <span data-ttu-id="a0cc5-136">예를 들어 " 10:24"는 유효한 값입니다.</span><span class="sxs-lookup"><span data-stu-id="a0cc5-136">For example, the value " 10:24" is valid.</span></span>  
  
-   <span data-ttu-id="a0cc5-137">24시간 형식.</span><span class="sxs-lookup"><span data-stu-id="a0cc5-137">24-hour format.</span></span> <span data-ttu-id="a0cc5-138">빠른 구문 분석에서는 AM 및 PM 표기가 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a0cc5-138">Fast parse does not support the AM and PM notation.</span></span>  
  
-   <span data-ttu-id="a0cc5-139">다음 표에 나열된 ISO 8601 시간 형식</span><span class="sxs-lookup"><span data-stu-id="a0cc5-139">ISO 8601 time formats, as listed in the following table:</span></span>  
  
    |<span data-ttu-id="a0cc5-140">서식</span><span class="sxs-lookup"><span data-stu-id="a0cc5-140">Format</span></span>|<span data-ttu-id="a0cc5-141">Description</span><span class="sxs-lookup"><span data-stu-id="a0cc5-141">Description</span></span>|  
    |------------|-----------------|  
    |<span data-ttu-id="a0cc5-142">HHMISS</span><span class="sxs-lookup"><span data-stu-id="a0cc5-142">HHMISS</span></span><br /><br /> <span data-ttu-id="a0cc5-143">HH:MI:SS</span><span class="sxs-lookup"><span data-stu-id="a0cc5-143">HH:MI:SS</span></span>|<span data-ttu-id="a0cc5-144">두 자리 시간, 두 자리 분 및 두 자리 초의 기본 및 확장 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="a0cc5-144">Basic and extended formats for a two-digit hour, a two-digit minute, and a two-digit second.</span></span> <span data-ttu-id="a0cc5-145">확장 형식에서 시간 부분은 콜론(:)으로 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="a0cc5-145">In the extended format, the time parts are separated by a colon (:).</span></span>|  
    |<span data-ttu-id="a0cc5-146">HHMI</span><span class="sxs-lookup"><span data-stu-id="a0cc5-146">HHMI</span></span><br /><br /> <span data-ttu-id="a0cc5-147">HH:MI</span><span class="sxs-lookup"><span data-stu-id="a0cc5-147">HH:MI</span></span>|<span data-ttu-id="a0cc5-148">두 자리 시간과 두 자리 분의 기본 및 확장 잘림 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="a0cc5-148">Basic and extended truncated format for a two-digit hour and a two-digit minute.</span></span> <span data-ttu-id="a0cc5-149">확장 형식에서 시간 부분은 콜론(:)으로 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="a0cc5-149">In the extended format, the time parts are separated by a colon (:).</span></span>|  
    |<span data-ttu-id="a0cc5-150">HH</span><span class="sxs-lookup"><span data-stu-id="a0cc5-150">HH</span></span>|<span data-ttu-id="a0cc5-151">두 자리 시간의 잘림 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="a0cc5-151">Truncated format for a two-digit hour.</span></span>|  
    |<span data-ttu-id="a0cc5-152">00:00:00</span><span class="sxs-lookup"><span data-stu-id="a0cc5-152">00:00:00</span></span><br /><br /> <span data-ttu-id="a0cc5-153">000000</span><span class="sxs-lookup"><span data-stu-id="a0cc5-153">000000</span></span><br /><br /> <span data-ttu-id="a0cc5-154">0000</span><span class="sxs-lookup"><span data-stu-id="a0cc5-154">0000</span></span><br /><br /> <span data-ttu-id="a0cc5-155">00</span><span class="sxs-lookup"><span data-stu-id="a0cc5-155">00</span></span><br /><br /> <span data-ttu-id="a0cc5-156">240000</span><span class="sxs-lookup"><span data-stu-id="a0cc5-156">240000</span></span><br /><br /> <span data-ttu-id="a0cc5-157">24:00:00</span><span class="sxs-lookup"><span data-stu-id="a0cc5-157">24:00:00</span></span><br /><br /> <span data-ttu-id="a0cc5-158">2400</span><span class="sxs-lookup"><span data-stu-id="a0cc5-158">2400</span></span><br /><br /> <span data-ttu-id="a0cc5-159">24</span><span class="sxs-lookup"><span data-stu-id="a0cc5-159">24</span></span>|<span data-ttu-id="a0cc5-160">자정 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="a0cc5-160">The format for midnight.</span></span>|  
  
-   <span data-ttu-id="a0cc5-161">다음 표에 나열된 표준 시간대를 지정하는 시간 형식</span><span class="sxs-lookup"><span data-stu-id="a0cc5-161">Time formats that specify a time zone, as listed in the following table:.</span></span>  
  
    |<span data-ttu-id="a0cc5-162">서식</span><span class="sxs-lookup"><span data-stu-id="a0cc5-162">Format</span></span>|<span data-ttu-id="a0cc5-163">Description</span><span class="sxs-lookup"><span data-stu-id="a0cc5-163">Description</span></span>|  
    |------------|-----------------|  
    |<span data-ttu-id="a0cc5-164">+HH:MI</span><span class="sxs-lookup"><span data-stu-id="a0cc5-164">+HH:MI</span></span><br /><br /> <span data-ttu-id="a0cc5-165">+HHMI</span><span class="sxs-lookup"><span data-stu-id="a0cc5-165">+HHMI</span></span>|<span data-ttu-id="a0cc5-166">현지 시간을 얻기 위해 UTC(Coordinated Universal Time)에 더한 시간과 분을 나타내는 기본 및 확장 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="a0cc5-166">Basic and extended formats that indicate the number of hours and minutes that are added to Coordinated Universal Time (UTC) to obtain the local time.</span></span>|  
    |<span data-ttu-id="a0cc5-167">-HH:MI</span><span class="sxs-lookup"><span data-stu-id="a0cc5-167">-HH:MI</span></span><br /><br /> <span data-ttu-id="a0cc5-168">-HHMI</span><span class="sxs-lookup"><span data-stu-id="a0cc5-168">-HHMI</span></span>|<span data-ttu-id="a0cc5-169">현지 시간을 얻기 위해 UTC에서 뺀 시간과 분을 나타내는 기본 및 확장 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="a0cc5-169">Basic and extended formats that indicate the number of hours and minutes that are subtracted from UTC to obtain the local time.</span></span>|  
    |<span data-ttu-id="a0cc5-170">+HH</span><span class="sxs-lookup"><span data-stu-id="a0cc5-170">+HH</span></span>|<span data-ttu-id="a0cc5-171">현지 시간을 얻기 위해 UTC에 더한 시간을 나타내는 잘림 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="a0cc5-171">Truncated format that indicates the number of hours that are added to UTC to obtain the local time.</span></span>|  
    |<span data-ttu-id="a0cc5-172">-HH</span><span class="sxs-lookup"><span data-stu-id="a0cc5-172">-HH</span></span>|<span data-ttu-id="a0cc5-173">현지 시간을 얻기 위해 UTC에서 뺀 시간을 나타내는 잘림 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="a0cc5-173">Truncated format that indicates the number of hours that are subtracted from UTC to obtain the local time.</span></span>|  
    |<span data-ttu-id="a0cc5-174">Z</span><span class="sxs-lookup"><span data-stu-id="a0cc5-174">Z</span></span>|<span data-ttu-id="a0cc5-175">값 0은 시간이 UTC 시간임을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a0cc5-175">A value of 0 that indicates the time is represented in UTC.</span></span>|  
  
     <span data-ttu-id="a0cc5-176">모든 시간 및 날짜/시간 데이터의 형식은 표준 시간대 요소를 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a0cc5-176">The formats for all time and date/time data can include a time zone element.</span></span> <span data-ttu-id="a0cc5-177">그러나 데이터가 DT_DBTIMESTAMPOFFSET 유형인 경우를 제외하고 시스템에서는 표준 시간대 값이 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a0cc5-177">However, the system ignores the time zone value except when the data is of type DT_DBTIMESTAMPOFFSET.</span></span> <span data-ttu-id="a0cc5-178">자세한 내용은 [Integration Services Data Types](data-flow/integration-services-data-types.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a0cc5-178">For more information, see [Integration Services Data Types](data-flow/integration-services-data-types.md).</span></span>  
  
     <span data-ttu-id="a0cc5-179">표준 시간대 요소를 포함하는 형식에서는 다음 예와 같이 시간 요소와 표준 시간대 요소 사이에 공백이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a0cc5-179">In formats that include a time zone element, there is no space between the time element and the time zone element, as shown in the following example:</span></span>  
  
     <span data-ttu-id="a0cc5-180">HH:MI:SS[+HH:MI]</span><span class="sxs-lookup"><span data-stu-id="a0cc5-180">HH:MI:SS[+HH:MI]</span></span>  
  
     <span data-ttu-id="a0cc5-181">앞의 예에서 대괄호는 표준 시간대 값이 선택 사항임을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a0cc5-181">The brackets in the previous example indicate that the time zone value is optional.</span></span>  
  
-   <span data-ttu-id="a0cc5-182">다음 표에 나열된 소수 부분을 포함하는 시간 형식</span><span class="sxs-lookup"><span data-stu-id="a0cc5-182">Time formats that include a decimal fraction, as listed in the following table:</span></span>  
  
    |<span data-ttu-id="a0cc5-183">서식</span><span class="sxs-lookup"><span data-stu-id="a0cc5-183">Format</span></span>|<span data-ttu-id="a0cc5-184">Description</span><span class="sxs-lookup"><span data-stu-id="a0cc5-184">Description</span></span>|  
    |------------|-----------------|  
    |<span data-ttu-id="a0cc5-185">HH[.nnnnnnn]</span><span class="sxs-lookup"><span data-stu-id="a0cc5-185">HH[.nnnnnnn]</span></span>|<span data-ttu-id="a0cc5-186">n은 시간의 소수 부분을 나타내는 0에서 9999999 사이의 값입니다.</span><span class="sxs-lookup"><span data-stu-id="a0cc5-186">n is a value between 0 and 9999999 that represents a fraction of hours.</span></span> <span data-ttu-id="a0cc5-187">대괄호는 이 값이 선택 사항임을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a0cc5-187">The brackets indicate that this value is optional.</span></span><br /><br /> <span data-ttu-id="a0cc5-188">예를 들어 값 12.750은 12:45를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a0cc5-188">For example, the value 12.750 indicates 12:45.</span></span>|  
    |<span data-ttu-id="a0cc5-189">HHMI[.nnnnnnn]</span><span class="sxs-lookup"><span data-stu-id="a0cc5-189">HHMI[.nnnnnnn]</span></span><br /><br /> <span data-ttu-id="a0cc5-190">HH:MI[.nnnnnnn]</span><span class="sxs-lookup"><span data-stu-id="a0cc5-190">HH:MI[.nnnnnnn]</span></span>|<span data-ttu-id="a0cc5-191">n은 분의 소수 부분을 나타내는 0에서 9999999 사이의 값입니다.</span><span class="sxs-lookup"><span data-stu-id="a0cc5-191">n is a value between 0 and 9999999 that represents a fraction of minutes.</span></span> <span data-ttu-id="a0cc5-192">대괄호는 이 값이 선택 사항임을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a0cc5-192">The brackets indicate that this value is optional.</span></span><br /><br /> <span data-ttu-id="a0cc5-193">예를 들어 값 1220.500은 12:20:30을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a0cc5-193">For example, the value 1220.500 indicates 12:20:30.</span></span>|  
    |<span data-ttu-id="a0cc5-194">HHMISS[.nnnnnnn]</span><span class="sxs-lookup"><span data-stu-id="a0cc5-194">HHMISS[.nnnnnnn]</span></span><br /><br /> <span data-ttu-id="a0cc5-195">HH:MI:SS[.nnnnnnn]</span><span class="sxs-lookup"><span data-stu-id="a0cc5-195">HH:MI:SS[.nnnnnnn]</span></span>|<span data-ttu-id="a0cc5-196">n은 초의 소수 부분을 나타내는 0에서 9999999 사이의 값입니다.</span><span class="sxs-lookup"><span data-stu-id="a0cc5-196">n is a value between 0 and 9999999 that represents a fraction of seconds.</span></span> <span data-ttu-id="a0cc5-197">대괄호는 이 값이 선택 사항임을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a0cc5-197">The brackets indicate that this value is optional.</span></span><br /><br /> <span data-ttu-id="a0cc5-198">예를 들어 값 122040.250은 12:20:40.15를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a0cc5-198">For example, the value 122040.250 indicates 12:20:40.15.</span></span>|  
  
    > [!NOTE]  
    >  <span data-ttu-id="a0cc5-199">앞의 표에서 시간 형식의 소수 구분 기호는 소수점이나 쉼표일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a0cc5-199">The fraction separator for the time formats in the previous table can be a decimal or a comma.</span></span>  
  
-   <span data-ttu-id="a0cc5-200">다음 예와 같이 윤초를 포함하는 시간 값</span><span class="sxs-lookup"><span data-stu-id="a0cc5-200">Time values that include a leap second, as shown in the following examples:</span></span>  
  
     <span data-ttu-id="a0cc5-201">23:59:60[.0000000]</span><span class="sxs-lookup"><span data-stu-id="a0cc5-201">23:59:60[.0000000]</span></span>  
  
     <span data-ttu-id="a0cc5-202">235960[.0000000]</span><span class="sxs-lookup"><span data-stu-id="a0cc5-202">235960[.0000000]</span></span>  
  
 <span data-ttu-id="a0cc5-203">빠른 구문 분석에서는 문자열이 DT_DBTIME 및 DT_DBTIME2로 출력됩니다.</span><span class="sxs-lookup"><span data-stu-id="a0cc5-203">Fast parse outputs the strings as DT_DBTIME and DT_DBTIME2.</span></span> <span data-ttu-id="a0cc5-204">잘림 형식의 시간 값은 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="a0cc5-204">Time values in truncated formats are padded.</span></span> <span data-ttu-id="a0cc5-205">예를 들어 HH:MI는 HH:MM:00.000이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a0cc5-205">For example, HH:MI becomes HH:MM:00.000.</span></span>  
  
 <span data-ttu-id="a0cc5-206">자세한 내용은 [Integration Services Data Types](data-flow/integration-services-data-types.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a0cc5-206">For more information, see [Integration Services Data Types](data-flow/integration-services-data-types.md).</span></span>  
  
## <a name="datetime-data-type"></a><span data-ttu-id="a0cc5-207">날짜/시간 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="a0cc5-207">Date/Time Data Type</span></span>  
 <span data-ttu-id="a0cc5-208">빠른 구문 분석에서는 날짜/시간 데이터에 대해 다음과 같은 문자열 형식이 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="a0cc5-208">Fast parse supports the following string formats for date/time data:</span></span>  
  
-   <span data-ttu-id="a0cc5-209">선행 공백을 포함하는 형식.</span><span class="sxs-lookup"><span data-stu-id="a0cc5-209">Formats that include leading white spaces.</span></span> <span data-ttu-id="a0cc5-210">예를 들어 "  2003-01-10T203910"은 유효한 값입니다.</span><span class="sxs-lookup"><span data-stu-id="a0cc5-210">For example, the value "  2003-01-10T203910" is valid.</span></span>  
  
-   <span data-ttu-id="a0cc5-211">대문자 T로 구분된 유효한 날짜 형식과 유효한 시간 형식의 조합(예: YYYYMMDDT[HHMISS][+HH:MI]).</span><span class="sxs-lookup"><span data-stu-id="a0cc5-211">Combinations of valid date formats and valid time formats separated by an uppercase T, and valid time zone formats, such as YYYYMMDDT[HHMISS][+HH:MI].</span></span> <span data-ttu-id="a0cc5-212">시간 및 표준 시간대 값은 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a0cc5-212">The time and time zone values are not required.</span></span> <span data-ttu-id="a0cc5-213">예를 들어 "2003-10-14"는 유효합니다.</span><span class="sxs-lookup"><span data-stu-id="a0cc5-213">For example, "2003-10-14" is valid.</span></span>  
  
 <span data-ttu-id="a0cc5-214">빠른 구문 분석에서는 시간 간격이 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a0cc5-214">Fast parse does not support time intervals.</span></span> <span data-ttu-id="a0cc5-215">예를 들어 YYYYMMDDThhmmss/YYYYMMDDThhmmss 형식에서 시작 및 종료 날짜/시간으로 구분된 시간 간격은 구문 분석할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a0cc5-215">For example, a time interval identified by a start and end date and time in the format YYYYMMDDThhmmss/YYYYMMDDThhmmss cannot be parsed.</span></span>  
  
 <span data-ttu-id="a0cc5-216">빠른 구문 분석에서는 문자열이 DT_DATE, DT_DBTIMESTAMP, DT_DBTIMESTAMP2 및 DT_DBTIMESTAMPOFFSET으로 출력됩니다.</span><span class="sxs-lookup"><span data-stu-id="a0cc5-216">Fast parse outputs the strings as DT_DATE, DT_DBTIMESTAMP, DT_DBTIMESTAMP2, and DT_DBTIMESTAMPOFFSET.</span></span> <span data-ttu-id="a0cc5-217">잘림 형식의 날짜/시간 값은 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="a0cc5-217">Date/time values in truncated formats are padded.</span></span> <span data-ttu-id="a0cc5-218">다음 표에서는 누락된 날짜 및 시간 부분에 대해 추가되는 값을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="a0cc5-218">The following table lists the values that are added for missing date and time parts.</span></span>  
  
|<span data-ttu-id="a0cc5-219">날짜/시간 부분</span><span class="sxs-lookup"><span data-stu-id="a0cc5-219">Date/Time part</span></span>|<span data-ttu-id="a0cc5-220">안쪽 여백</span><span class="sxs-lookup"><span data-stu-id="a0cc5-220">Padding</span></span>|  
|---------------------|-------------|  
|<span data-ttu-id="a0cc5-221">초</span><span class="sxs-lookup"><span data-stu-id="a0cc5-221">Seconds</span></span>|<span data-ttu-id="a0cc5-222">00을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="a0cc5-222">Add 00.</span></span>|  
|<span data-ttu-id="a0cc5-223">분</span><span class="sxs-lookup"><span data-stu-id="a0cc5-223">Minutes</span></span>|<span data-ttu-id="a0cc5-224">00:00을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="a0cc5-224">Add 00:00.</span></span>|  
|<span data-ttu-id="a0cc5-225">시간</span><span class="sxs-lookup"><span data-stu-id="a0cc5-225">Hour</span></span>|<span data-ttu-id="a0cc5-226">00:00:00을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="a0cc5-226">Add 00:00:00.</span></span>|  
|<span data-ttu-id="a0cc5-227">일</span><span class="sxs-lookup"><span data-stu-id="a0cc5-227">Day</span></span>|<span data-ttu-id="a0cc5-228">해당 월의 일에 대해 01을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="a0cc5-228">Add 01 for the day of the month.</span></span>|  
|<span data-ttu-id="a0cc5-229">월</span><span class="sxs-lookup"><span data-stu-id="a0cc5-229">Month</span></span>|<span data-ttu-id="a0cc5-230">해당 연도의 월에 대해 01을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="a0cc5-230">Add 01 for the month of the year.</span></span>|  
  
 <span data-ttu-id="a0cc5-231">자세한 내용은 [Integration Services Data Types](data-flow/integration-services-data-types.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a0cc5-231">For more information, see [Integration Services Data Types](data-flow/integration-services-data-types.md).</span></span>  
  
  
