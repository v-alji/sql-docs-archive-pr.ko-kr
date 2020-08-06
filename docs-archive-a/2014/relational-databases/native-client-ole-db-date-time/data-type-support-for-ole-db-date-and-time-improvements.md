---
title: OLE DB 날짜 및 시간 기능 향상을 위한 데이터 형식 지원 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- date/time [OLE DB], data type support
- OLE DB, date/time improvements
ms.assetid: d40e3fd6-9057-4371-8236-95cef300603e
author: rothja
ms.author: jroth
ms.openlocfilehash: 834583fdec63a8f613e623c239f9c3a1c9398950
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738259"
---
# <a name="data-type-support-for-ole-db-date-and-time-improvements"></a><span data-ttu-id="d202d-102">OLE DB 날짜 및 시간 기능 향상을 위한 데이터 형식 지원</span><span class="sxs-lookup"><span data-stu-id="d202d-102">Data Type Support for OLE DB Date and Time Improvements</span></span>
  <span data-ttu-id="d202d-103">이 항목에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 날짜/시간 데이터 형식을 지원하는 OLE DB([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client) 유형에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="d202d-103">This topic provides information about OLE DB ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client) types that support [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] date/time data types.</span></span>  
  
## <a name="data-type-mapping-in-rowsets-and-parameters"></a><span data-ttu-id="d202d-104">행 집합 및 매개 변수의 데이터 형식 매핑</span><span class="sxs-lookup"><span data-stu-id="d202d-104">Data Type Mapping in Rowsets and Parameters</span></span>  
 <span data-ttu-id="d202d-105">OLE DB는 새 서버 유형 DBTYPE_DBTIME2 및 DBTYPE_DBTIMESTAMPOFFSET를 지원 하기 위한 두 가지 새 데이터 형식을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="d202d-105">OLE DB provides two new data types to support the new server types: DBTYPE_DBTIME2 and DBTYPE_DBTIMESTAMPOFFSET.</span></span> <span data-ttu-id="d202d-106">다음 표에서는 전체 서버 유형 매핑을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d202d-106">The following table shows the complete server type mapping:</span></span>  
  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="d202d-107">데이터 형식</span><span class="sxs-lookup"><span data-stu-id="d202d-107">data type</span></span>|<span data-ttu-id="d202d-108">OLE DB 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="d202d-108">OLE DB data type</span></span>|<span data-ttu-id="d202d-109">값</span><span class="sxs-lookup"><span data-stu-id="d202d-109">Value</span></span>|  
|-----------------------------------------|----------------------|-----------|  
|<span data-ttu-id="d202d-110">Datetime</span><span class="sxs-lookup"><span data-stu-id="d202d-110">datetime</span></span>|<span data-ttu-id="d202d-111">DBTYPE_DBTIMESTAMP</span><span class="sxs-lookup"><span data-stu-id="d202d-111">DBTYPE_DBTIMESTAMP</span></span>|<span data-ttu-id="d202d-112">135(oledb.h)</span><span class="sxs-lookup"><span data-stu-id="d202d-112">135 (oledb.h)</span></span>|  
|<span data-ttu-id="d202d-113">smalldatetime</span><span class="sxs-lookup"><span data-stu-id="d202d-113">smalldatetime</span></span>|<span data-ttu-id="d202d-114">DBTYPE_DBTIMESTAMP</span><span class="sxs-lookup"><span data-stu-id="d202d-114">DBTYPE_DBTIMESTAMP</span></span>|<span data-ttu-id="d202d-115">135(oledb.h)</span><span class="sxs-lookup"><span data-stu-id="d202d-115">135 (oledb.h)</span></span>|  
|<span data-ttu-id="d202d-116">date</span><span class="sxs-lookup"><span data-stu-id="d202d-116">date</span></span>|<span data-ttu-id="d202d-117">DBTYPE_DBDATE</span><span class="sxs-lookup"><span data-stu-id="d202d-117">DBTYPE_DBDATE</span></span>|<span data-ttu-id="d202d-118">133(oledb.h)</span><span class="sxs-lookup"><span data-stu-id="d202d-118">133 (oledb.h)</span></span>|  
|<span data-ttu-id="d202d-119">time</span><span class="sxs-lookup"><span data-stu-id="d202d-119">time</span></span>|<span data-ttu-id="d202d-120">DBTYPE_DBTIME2</span><span class="sxs-lookup"><span data-stu-id="d202d-120">DBTYPE_DBTIME2</span></span>|<span data-ttu-id="d202d-121">145 (sqlncli)</span><span class="sxs-lookup"><span data-stu-id="d202d-121">145 (sqlncli.h)</span></span>|  
|<span data-ttu-id="d202d-122">datetimeoffset</span><span class="sxs-lookup"><span data-stu-id="d202d-122">datetimeoffset</span></span>|<span data-ttu-id="d202d-123">DBTYPE_DBTIMESTAMPOFFSET</span><span class="sxs-lookup"><span data-stu-id="d202d-123">DBTYPE_DBTIMESTAMPOFFSET</span></span>|<span data-ttu-id="d202d-124">146 (sqlncli)</span><span class="sxs-lookup"><span data-stu-id="d202d-124">146 (sqlncli.h)</span></span>|  
|<span data-ttu-id="d202d-125">datetime2</span><span class="sxs-lookup"><span data-stu-id="d202d-125">datetime2</span></span>|<span data-ttu-id="d202d-126">DBTYPE_DBTIMESTAMP</span><span class="sxs-lookup"><span data-stu-id="d202d-126">DBTYPE_DBTIMESTAMP</span></span>|<span data-ttu-id="d202d-127">135(oledb.h)</span><span class="sxs-lookup"><span data-stu-id="d202d-127">135 (oledb.h)</span></span>|  
  
## <a name="data-formats-strings-and-literals"></a><span data-ttu-id="d202d-128">데이터 형식: 문자열 및 리터럴</span><span class="sxs-lookup"><span data-stu-id="d202d-128">Data Formats: Strings and Literals</span></span>  
  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="d202d-129">데이터 형식</span><span class="sxs-lookup"><span data-stu-id="d202d-129">data type</span></span>|<span data-ttu-id="d202d-130">OLE DB 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="d202d-130">OLE DB data type</span></span>|<span data-ttu-id="d202d-131">클라이언트 변환을 위한 문자열 형식</span><span class="sxs-lookup"><span data-stu-id="d202d-131">String format for client conversions</span></span>|  
|-----------------------------------------|----------------------|------------------------------------------|  
|<span data-ttu-id="d202d-132">Datetime</span><span class="sxs-lookup"><span data-stu-id="d202d-132">datetime</span></span>|<span data-ttu-id="d202d-133">DBTYPE_DBTIMESTAMP</span><span class="sxs-lookup"><span data-stu-id="d202d-133">DBTYPE_DBTIMESTAMP</span></span>|<span data-ttu-id="d202d-134">'yyyy-mm-dd hh:mm:ss[.999]'</span><span class="sxs-lookup"><span data-stu-id="d202d-134">'yyyy-mm-dd hh:mm:ss[.999]'</span></span><br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="d202d-135">는 Datetime에 대해 최대 3자리의 소수 자릿수 초를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="d202d-135">supports up to three fractional second digits for Datetime.</span></span>|  
|<span data-ttu-id="d202d-136">smalldatetime</span><span class="sxs-lookup"><span data-stu-id="d202d-136">smalldatetime</span></span>|<span data-ttu-id="d202d-137">DBTYPE_DBTIMESTAMP</span><span class="sxs-lookup"><span data-stu-id="d202d-137">DBTYPE_DBTIMESTAMP</span></span>|<span data-ttu-id="d202d-138">'yyyy-mm-dd hh:mm:ss'</span><span class="sxs-lookup"><span data-stu-id="d202d-138">'yyyy-mm-dd hh:mm:ss'</span></span><br /><br /> <span data-ttu-id="d202d-139">이 데이터 형식의 정확도는 1분 단위입니다.</span><span class="sxs-lookup"><span data-stu-id="d202d-139">This data type has an accuracy of one minute.</span></span> <span data-ttu-id="d202d-140">초 구성 요소 부분은 출력 시 0이 되고, 입력 시 서버에 의해 반올림됩니다.</span><span class="sxs-lookup"><span data-stu-id="d202d-140">The seconds component will be zero on output and will be rounded by the server on input.</span></span>|  
|<span data-ttu-id="d202d-141">date</span><span class="sxs-lookup"><span data-stu-id="d202d-141">date</span></span>|<span data-ttu-id="d202d-142">DBTYPE_DBDATE</span><span class="sxs-lookup"><span data-stu-id="d202d-142">DBTYPE_DBDATE</span></span>|<span data-ttu-id="d202d-143">'yyyy-mm-dd'</span><span class="sxs-lookup"><span data-stu-id="d202d-143">'yyyy-mm-dd'</span></span>|  
|<span data-ttu-id="d202d-144">time</span><span class="sxs-lookup"><span data-stu-id="d202d-144">time</span></span>|<span data-ttu-id="d202d-145">DBTYPE_DBTIME2</span><span class="sxs-lookup"><span data-stu-id="d202d-145">DBTYPE_DBTIME2</span></span>|<span data-ttu-id="d202d-146">'hh:mm:ss[.9999999]'</span><span class="sxs-lookup"><span data-stu-id="d202d-146">'hh:mm:ss[.9999999]'</span></span><br /><br /> <span data-ttu-id="d202d-147">필요한 경우 소수 자릿수 초를 일곱 자리까지 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d202d-147">Fractional seconds can optionally be specified using up to seven digits.</span></span>|  
|<span data-ttu-id="d202d-148">datetime2</span><span class="sxs-lookup"><span data-stu-id="d202d-148">datetime2</span></span>|<span data-ttu-id="d202d-149">DBTYPE_DBTIMESTAMP</span><span class="sxs-lookup"><span data-stu-id="d202d-149">DBTYPE_DBTIMESTAMP</span></span>|<span data-ttu-id="d202d-150">'yyyy-mm-dd hh:mm:ss[.fffffff]'</span><span class="sxs-lookup"><span data-stu-id="d202d-150">'yyyy-mm-dd hh:mm:ss[.fffffff]'</span></span><br /><br /> <span data-ttu-id="d202d-151">필요한 경우 소수 자릿수 초를 일곱 자리까지 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d202d-151">Fractional seconds can optionally be specified using up to seven digits.</span></span>|  
|<span data-ttu-id="d202d-152">datetimeoffset</span><span class="sxs-lookup"><span data-stu-id="d202d-152">datetimeoffset</span></span>|<span data-ttu-id="d202d-153">DBTYPE_DBTIMESTAMPOFFSET</span><span class="sxs-lookup"><span data-stu-id="d202d-153">DBTYPE_DBTIMESTAMPOFFSET</span></span>|<span data-ttu-id="d202d-154">'yyyy-mm-dd hh:mm:ss[.fffffff] +/-hh:mm'</span><span class="sxs-lookup"><span data-stu-id="d202d-154">'yyyy-mm-dd hh:mm:ss[.fffffff] +/-hh:mm'</span></span><br /><br /> <span data-ttu-id="d202d-155">필요한 경우 소수 자릿수 초를 일곱 자리까지 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d202d-155">Fractional seconds can optionally be specified using up to seven digits.</span></span>|  
  
 <span data-ttu-id="d202d-156">날짜/시간 리터럴에 대한 이스케이프 시퀀스에는 변경 내용이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d202d-156">There are no changes to the escape sequences for date/time literals.</span></span>  
  
 <span data-ttu-id="d202d-157">결과의 소수 자릿수 초는 콜론(:)이 아닌 점(.)을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="d202d-157">Fractional seconds in results use a dot (.) rather than a colon (:).</span></span>  
  
 <span data-ttu-id="d202d-158">애플리케이션에 반환되는 문자열 값은 지정된 열에 대해 길이가 항상 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="d202d-158">String values returned to applications will always be the same length for a given column.</span></span> <span data-ttu-id="d202d-159">연도, 월, 일, 시간, 분 및 초 구성 요소에는 최대 너비까지 앞에 0이 채워지고</span><span class="sxs-lookup"><span data-stu-id="d202d-159">Year, month, day, hour, minute, and second components will be padded with leading zeros to their maximum width.</span></span> <span data-ttu-id="d202d-160">날짜와 시간 사이 및 시간과 표준 시간대 오프셋 사이에는 공백이 하나씩 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d202d-160">There will be exactly one space between date and time and exactly one space between the time and timezone offset.</span></span> <span data-ttu-id="d202d-161">표준 시간대 오프셋 앞에는 항상 부호가 나오며</span><span class="sxs-lookup"><span data-stu-id="d202d-161">A timezone offset will always be preceded by a sign.</span></span> <span data-ttu-id="d202d-162">오프셋이 0인 경우에는 더하기(+) 부호가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="d202d-162">This sign will be a plus (+) when the offset is zero.</span></span> <span data-ttu-id="d202d-163">부호와 오프셋 값 사이에는 공백이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d202d-163">There will be no white space between the sign and the offset value.</span></span> <span data-ttu-id="d202d-164">필요한 경우 소수 자릿수 초의 뒷부분은 열에 정의된 전체 자릿수까지만 0으로 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="d202d-164">Fractional seconds will be padded with trailing zeros, if necessary, up to the defined precision for the column, but no further.</span></span> <span data-ttu-id="d202d-165">datetime 열의 경우 소수 자릿수 초는 3자리입니다.</span><span class="sxs-lookup"><span data-stu-id="d202d-165">For datetime columns, there will be three fractional seconds digits.</span></span> <span data-ttu-id="d202d-166">smalldatetime 열의 경우 소수 자릿수 초의 자릿수가 정의되지 않으며 초는 항상 0이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d202d-166">For smalldatetime columns, there will be no fractional seconds digits and the seconds will always be zero.</span></span>  
  
 <span data-ttu-id="d202d-167">애플리케이션에서 제공하는 문자열 값을 보다 유연하게 변환할 수 있으며 최대 너비보다 작은 구성 요소 값도 허용됩니다.</span><span class="sxs-lookup"><span data-stu-id="d202d-167">Conversions from string values provided by the application will be more flexible and will allow component values less than maximum width.</span></span> <span data-ttu-id="d202d-168">연도는 1 - 4자리일 수 있고</span><span class="sxs-lookup"><span data-stu-id="d202d-168">Years can be 1-4 digits.</span></span> <span data-ttu-id="d202d-169">월, 일, 시간, 분 및 초는 1자리 또는 2자리일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d202d-169">Months, days, hours, minutes, and seconds can be 1 or 2 digits.</span></span> <span data-ttu-id="d202d-170">날짜/시간 및 시간/표준 시간대 오프셋 사이에 임의의 개수의 공백을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d202d-170">There can be arbitrary white space between date/time and time/timezone offsets.</span></span> <span data-ttu-id="d202d-171">0시간 0분 오프셋의 부호는 더하기 또는 빼기 모두 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d202d-171">The sign of an offset with zero hours and zero minutes can be plus or minus.</span></span> <span data-ttu-id="d202d-172">소수 자릿수 초의 뒤에는 0을 최대 9자리까지 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d202d-172">Trailing zeros are allowed for fractional seconds up to a maximum of 9 digits.</span></span> <span data-ttu-id="d202d-173">시간 구성 요소는 소수 자릿수 초의 자릿수 없이 소수점으로 끝날 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d202d-173">A time component can terminate with a decimal point and no fractional seconds digits.</span></span>  
  
 <span data-ttu-id="d202d-174">빈 문자열은 유효한 날짜/시간 리터럴이 아니며 NULL 값을 나타내지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d202d-174">An empty string is not a valid date/time literal and it does not represent a NULL value.</span></span> <span data-ttu-id="d202d-175">빈 문자열을 날짜/시간 값으로 변환하려고 하면 SQLState 22018 및 "캐스트 사양의 문자 값이 올바르지 않습니다."라는 메시지와 함께 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="d202d-175">An attempt to convert an empty string to a date/time value will result in errors with SQLState 22018 and the message "Invalid character value for cast specification".</span></span>  
  
## <a name="data-formats-data-structures"></a><span data-ttu-id="d202d-176">데이터 형식: 데이터 구조</span><span class="sxs-lookup"><span data-stu-id="d202d-176">Data Formats: Data Structures</span></span>  
 <span data-ttu-id="d202d-177">아래에 설명된 OLE DB별 구조에서 OLE DB에는 ODBC와 동일한 제약 조건이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="d202d-177">In the OLE DB-specific structures described below, OLE DB conforms to the same constraints as ODBC.</span></span> <span data-ttu-id="d202d-178">이러한 제약 조건은 일반 달력을 기준으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="d202d-178">These are taken from the Gregorian calendar:</span></span>  
  
-   <span data-ttu-id="d202d-179">월 범위는 1에서 12까지입니다.</span><span class="sxs-lookup"><span data-stu-id="d202d-179">Month range is 1 through 12.</span></span>  
  
-   <span data-ttu-id="d202d-180">일 필드의 범위는 1에서 해당 월의 일 수까지이며, 윤년을 고려하여 연도 및 월 필드와 일관성을 유지해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d202d-180">Day field range is 1 through the number of days in the month, and must be consistent with year and month fields, taking account of leap years.</span></span>  
  
-   <span data-ttu-id="d202d-181">시 범위는 0에서 23까지입니다.</span><span class="sxs-lookup"><span data-stu-id="d202d-181">Hour range is 0 through 23.</span></span>  
  
-   <span data-ttu-id="d202d-182">분 범위는 0에서 59까지입니다.</span><span class="sxs-lookup"><span data-stu-id="d202d-182">Minute range is 0 through 59.</span></span>  
  
-   <span data-ttu-id="d202d-183">초 범위는 0에서 59까지입니다.</span><span class="sxs-lookup"><span data-stu-id="d202d-183">Seconds range from 0 through 59.</span></span> <span data-ttu-id="d202d-184">이는 항성시와의 동기화를 유지하기 위한 최대 2초의 윤초를 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="d202d-184">This allows up to two leap seconds to maintain synchronization with sidereal time.</span></span>  
  
 <span data-ttu-id="d202d-185">다음과 같은 기존 OLE DB 구조체의 구현은 새로운 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 날짜 및 시간 데이터 형식을 지원하도록 수정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="d202d-185">Implementations for the following existing OLE DB structs have been modified to support the new [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] date and time data types.</span></span> <span data-ttu-id="d202d-186">단, 정의는 변경되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="d202d-186">The definitions, however, have not changed.</span></span>  
  
-   <span data-ttu-id="d202d-187">DBTYPE_DATE. 자동 DATE 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="d202d-187">DBTYPE_DATE (This is an automation DATE type.</span></span> <span data-ttu-id="d202d-188">내부적으로 `double`로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d202d-188">It is internally represented as a `double`..</span></span> <span data-ttu-id="d202d-189">정수 부분은 1899년 12월 30일 이후의 일 수이고, 소수 부분은 하루를 분수로 표시한 수입니다.</span><span class="sxs-lookup"><span data-stu-id="d202d-189">The whole part is the number of days since December 30, 1899 and the fractional part is the fraction of a day.</span></span> <span data-ttu-id="d202d-190">이 형식의 정확도는 1초 단위이므로 소수 자릿수가 0입니다.</span><span class="sxs-lookup"><span data-stu-id="d202d-190">This type has an accuracy of 1 second, so has an effective scale of 0.)</span></span>  
  
-   <span data-ttu-id="d202d-191">DBTYPE_DBDATE</span><span class="sxs-lookup"><span data-stu-id="d202d-191">DBTYPE_DBDATE</span></span>  
  
-   <span data-ttu-id="d202d-192">DBTYPE_DBTIME</span><span class="sxs-lookup"><span data-stu-id="d202d-192">DBTYPE_DBTIME</span></span>  
  
-   <span data-ttu-id="d202d-193">DBTYPE_DBTIMESTAMP. OLE DB에서 분수 필드는 10억분의 1초(나노초)로 정의되며 범위는 0-999,999,999입니다.</span><span class="sxs-lookup"><span data-stu-id="d202d-193">DBTYPE_DBTIMESTAMP (the fraction field is defined by OLE DB as the number of billionths of a second (nanoseconds) and ranges from 0-999,999,999)</span></span>  
  
-   <span data-ttu-id="d202d-194">DBTYPE_FILETIME</span><span class="sxs-lookup"><span data-stu-id="d202d-194">DBTYPE_FILETIME</span></span>  
  
### <a name="dbtype_dbtime2"></a><span data-ttu-id="d202d-195">DBTYPE_DBTIME2</span><span class="sxs-lookup"><span data-stu-id="d202d-195">DBTYPE_DBTIME2</span></span>  
 <span data-ttu-id="d202d-196">이 구조체는 32비트와 64비트 운영 체제 모두에서 12바이트까지 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="d202d-196">This struct is padded to 12 bytes on both 32-bit and 64-bit operating systems.</span></span>  
  
```  
typedef struct tagDBTIME2 {  
    USHORT hour;  
    USHORT minute;  
    USHORT second;  
    ULONG fraction;  
    } DBTIME2;  
```  
  
### <a name="dbtype_-dbtimestampoffset"></a><span data-ttu-id="d202d-197">DBTYPE_ DBTIMESTAMPOFFSET</span><span class="sxs-lookup"><span data-stu-id="d202d-197">DBTYPE_ DBTIMESTAMPOFFSET</span></span>  
  
```  
typedef struct tagDBTIMESTAMPOFFSET {  
    SHORT year;  
    USHORT month;  
    USHORT day;  
    USHORT hour;  
    USHORT minute;  
    USHORT second;  
    ULONG fraction;  
    SHORT timezone_hour;  
    SHORT timezone_minute;  
    } DBTIMESTAMPOFFSET;  
```  
  
 <span data-ttu-id="d202d-198">`timezone_hour`가 음수인 경우 `timezone_minute`는 음수 또는 0이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d202d-198">If `timezone_hour` is negative, `timezone_minute` must be negative or zero.</span></span> <span data-ttu-id="d202d-199">`timezone_hour`가 양수인 경우 `timezone minute`는 양수 또는 0이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d202d-199">If `timezone_hour` is positive, `timezone minute` must be positive or zero.</span></span> <span data-ttu-id="d202d-200">`timezone_hour`가 0인 경우 `timezone minute`의 값 범위는 -59에서 +59까지입니다.</span><span class="sxs-lookup"><span data-stu-id="d202d-200">If `timezone_hour` is zero, `timezone minute` can hold a value between -59 and +59.</span></span>  
  
### <a name="ssvariant"></a><span data-ttu-id="d202d-201">SSVARIANT</span><span class="sxs-lookup"><span data-stu-id="d202d-201">SSVARIANT</span></span>  
 <span data-ttu-id="d202d-202">이 구조체는 이제 새로운 구조인 DBTYPE_DBTIME2와 DBTYPE_DBTIMESTAMPOFFSET을 포함하고 적절한 형식에 소수 자릿수 초의 자릿수를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="d202d-202">This struct now includes the new structures, DBTYPE_DBTIME2 and DBTYPE_DBTIMESTAMPOFFSET, and adds fractional seconds scale for appropriate types.</span></span>  
  
```  
struct SSVARIANT {  
   SSVARTYPE vt;  
   DWORD dwReserved1;  
   DWORD dwReserved2;  
   union {  
// ...  
      DBTIMESTAMP tsDateTimeVal;  
      DBDATE dDateVal;  
      struct _Time2Val {  
         DBTIME2 tTime2Val;  
         BYTE bScale;  
      } Time2Val;  
      struct _DateTimeVal {  
         DBTIMESTAMP tsDateTimeVal;  
         BYTE bScale;  
      } DateTimeVal;  
      struct _DateTimeOffsetVal {   
         DBTIMESTAMPOFFSET tsoDateTimeOffsetVal;  
         BYTE bScale;  
      } DateTimeOffsetVal;  
// ...  
   };  
};  
```  
  
 <span data-ttu-id="d202d-203">또한 열거형 형식을 결정하는 SSVARIANT 형식 인코딩과 관련된 열거형은 다음과 같이 확장됩니다.</span><span class="sxs-lookup"><span data-stu-id="d202d-203">In addition, the enum associated with SSVARIANT type encoding, which determines the type of the enum, will be extended as follows:</span></span>  
  
```  
enum SQLVARENUM {  
// ...  
   // Datetime  
   VT_SS_DATETIME      = DBTYPE_DBTIMESTAMP,  
   VT_SS_SMALLDATETIME = 206,  
  
   VT_SS_DATE = DBTYPE_DBDATE,  
   VT_SS_TIME2 = DBTYPE_DBTIME2,  
   VT_SS_DATETIME2 = 212  
   VT_SS_DATETIMEOFFSET = DBTYPE_DBTIMESTAMPOFFSET  
};  
```  
  
 <span data-ttu-id="d202d-204">`sql_variant`를 사용하고 `datetime`의 제한된 정밀도에 의존하는 애플리케이션을 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client로 마이그레이션하는 경우 `datetime2` 대신 `datetime`를 사용하도록 기본 스키마가 업데이트되면 해당 애플리케이션도 이에 맞게 업데이트되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d202d-204">Applications migrating to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client that use `sql_variant` and rely on the limited precision of `datetime` will have to be updated if the underlying schema is updated to use `datetime2` rather than `datetime`.</span></span>  
  
 <span data-ttu-id="d202d-205">SSVARIANT의 액세스 매크로도 다음과 같은 추가를 통해 확장되었습니다.</span><span class="sxs-lookup"><span data-stu-id="d202d-205">The access macros for SSVARIANT have also been extended with the addition of the following:</span></span>  
  
```  
#define V_SS_DATETIME2(X)       V_SS_UNION(X, DateTimeVal)  
#define V_SS_TIME2(X)           V_SS_UNION(X, Time2Val)  
#define V_SS_DATE(X)            V_SS_UNION(X, dDateVal)  
#define V_SS_DATETIMEOFFSET(X)  V_SS_UNION(X, DateTimeOffsetVal)  
```  
  
## <a name="data-type-mapping-in-itabledefinitioncreatetable"></a><span data-ttu-id="d202d-206">ITableDefinition::CreateTable의 데이터 형식 매핑</span><span class="sxs-lookup"><span data-stu-id="d202d-206">Data Type Mapping in ITableDefinition::CreateTable</span></span>  
 <span data-ttu-id="d202d-207">다음 형식 매핑은 ITableDefinition::CreateTable에서 사용되는 DBCOLUMNDESC 구조체와 함께 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="d202d-207">The following type mapping is used with DBCOLUMNDESC structures used by ITableDefinition::CreateTable:</span></span>  
  
|<span data-ttu-id="d202d-208">OLE DB 데이터 형식(*wType*)</span><span class="sxs-lookup"><span data-stu-id="d202d-208">OLE DB data type (*wType*)</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="d202d-209">데이터 형식</span><span class="sxs-lookup"><span data-stu-id="d202d-209">data type</span></span>|<span data-ttu-id="d202d-210">참고</span><span class="sxs-lookup"><span data-stu-id="d202d-210">Notes</span></span>|  
|----------------------------------|-----------------------------------------|-----------|  
|<span data-ttu-id="d202d-211">DBTYPE_DBDATE</span><span class="sxs-lookup"><span data-stu-id="d202d-211">DBTYPE_DBDATE</span></span>|<span data-ttu-id="d202d-212">date</span><span class="sxs-lookup"><span data-stu-id="d202d-212">date</span></span>||  
|<span data-ttu-id="d202d-213">DBTYPE_DBTIMESTAMP</span><span class="sxs-lookup"><span data-stu-id="d202d-213">DBTYPE_DBTIMESTAMP</span></span>|<span data-ttu-id="d202d-214">`datetime2`(p)</span><span class="sxs-lookup"><span data-stu-id="d202d-214">`datetime2`(p)</span></span>|<span data-ttu-id="d202d-215">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 공급자는 DBCOLUMDESC *bscale* 멤버를 검사 하 여 초 소수 부분 자릿수를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="d202d-215">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider inspects the DBCOLUMDESC *bScale* member to determine the fractional seconds precision.</span></span>|  
|<span data-ttu-id="d202d-216">DBTYPE_DBTIME2</span><span class="sxs-lookup"><span data-stu-id="d202d-216">DBTYPE_DBTIME2</span></span>|<span data-ttu-id="d202d-217">`time`(p)</span><span class="sxs-lookup"><span data-stu-id="d202d-217">`time`(p)</span></span>|<span data-ttu-id="d202d-218">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 공급자는 DBCOLUMDESC *bscale* 멤버를 검사 하 여 초 소수 부분 자릿수를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="d202d-218">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider inspects the DBCOLUMDESC *bScale* member to determine the fractional seconds precision.</span></span>|  
|<span data-ttu-id="d202d-219">DBTYPE_DBTIMESTAMPOFFSET</span><span class="sxs-lookup"><span data-stu-id="d202d-219">DBTYPE_DBTIMESTAMPOFFSET</span></span>|<span data-ttu-id="d202d-220">`datetimeoffset`(p)</span><span class="sxs-lookup"><span data-stu-id="d202d-220">`datetimeoffset`(p)</span></span>|<span data-ttu-id="d202d-221">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 공급자는 DBCOLUMDESC *bscale* 멤버를 검사 하 여 초 소수 부분 자릿수를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="d202d-221">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider inspects the DBCOLUMDESC *bScale* member to determine the fractional seconds precision.</span></span>|  
  
 <span data-ttu-id="d202d-222">응용 프로그램에서 *Wtype*에 DBTYPE_DBTIMESTAMP를 지정 하는 경우 `datetime2` *pwszTypeName*에서 형식 이름을 제공 하 여에 대 한 매핑을 재정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d202d-222">When an application specifies DBTYPE_DBTIMESTAMP in *wType*, it can override the mapping to `datetime2` by supplying a type name in *pwszTypeName*.</span></span> <span data-ttu-id="d202d-223">`datetime`을 지정 하는 경우 *bscale* 은 3 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d202d-223">If `datetime` is specified, *bScale* must be 3.</span></span> <span data-ttu-id="d202d-224">`smalldatetime`을 지정 하면 *bscale* 은 0 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d202d-224">If `smalldatetime` is specified, *bScale* must be 0.</span></span> <span data-ttu-id="d202d-225">*Bscale* 이 *Wtype* 및 *pwszTypeName*와 일치 하지 않는 경우 DB_E_BADSCALE 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d202d-225">If *bScale* is not consistent with *wType* and *pwszTypeName*,DB_E_BADSCALE is returned.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d202d-226">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d202d-226">See Also</span></span>  
 [<span data-ttu-id="d202d-227">날짜 및 시간 기능 향상&#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="d202d-227">Date and Time Improvements &#40;OLE DB&#41;</span></span>](date-and-time-improvements-ole-db.md)  
  
  
