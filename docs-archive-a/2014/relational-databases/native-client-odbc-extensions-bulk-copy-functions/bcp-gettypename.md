---
title: bcp_gettypename | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- bcp_gettypename
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_gettypename function
ms.assetid: 65f036d1-f60e-4b8a-97b3-76fccf0dfed4
author: rothja
ms.author: jroth
ms.openlocfilehash: b2d92498b9d863fa2cb700ec4d88868c0984c4d4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649056"
---
# <a name="bcp_gettypename"></a><span data-ttu-id="f8960-102">bcp_gettypename</span><span class="sxs-lookup"><span data-stu-id="f8960-102">bcp_gettypename</span></span>
  <span data-ttu-id="f8960-103">지정한 BCP 유형 토큰의 SQL 유형 이름을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="f8960-103">Returns the SQL type name for a specified BCP type token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8960-104">구문</span><span class="sxs-lookup"><span data-stu-id="f8960-104">Syntax</span></span>  
  
```  
  
RETCODE bcp_gettypename (  
INT   
token  
,  
DBBOOL   
fIsMaxType  
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="f8960-105">인수</span><span class="sxs-lookup"><span data-stu-id="f8960-105">Arguments</span></span>  
 <span data-ttu-id="f8960-106">*토큰*</span><span class="sxs-lookup"><span data-stu-id="f8960-106">*token*</span></span>  
 <span data-ttu-id="f8960-107">BCP 유형 토큰을 나타내는 값입니다.</span><span class="sxs-lookup"><span data-stu-id="f8960-107">A value indicating a BCP type token.</span></span>  
  
 <span data-ttu-id="f8960-108">*필드가*</span><span class="sxs-lookup"><span data-stu-id="f8960-108">*field*</span></span>  
 <span data-ttu-id="f8960-109">요청된 토큰이 max 유형인지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="f8960-109">Indicates if token requested is a max type.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="f8960-110">반환</span><span class="sxs-lookup"><span data-stu-id="f8960-110">Returns</span></span>  
 <span data-ttu-id="f8960-111">BCP 유형에 해당하는 SQL 유형 이름이 포함된 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="f8960-111">A string containing the SQL type name corresponding to the BCP type.</span></span> <span data-ttu-id="f8960-112">잘못된 BCP 유형을 지정하면 빈 문자열이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="f8960-112">If an invalid BCP type is specified, an empty string is returned..</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f8960-113">설명</span><span class="sxs-lookup"><span data-stu-id="f8960-113">Remarks</span></span>  
 <span data-ttu-id="f8960-114">BCP 유형 토큰은 sqlncli.h 헤더 파일과 sqlncli11.lib 라이브러리에서 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="f8960-114">The BCP type tokens are defined in the sqlncli.h header file and the sqlncli11.lib library.</span></span>  
  
 <span data-ttu-id="f8960-115">다음 표에서는 가능한 BCP 유형, max 유형인지 여부 및 예상 출력을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f8960-115">The table below specifies the possible BCP types, whether or not they are max types, and the expected output.</span></span>  
  
|<span data-ttu-id="f8960-116">BCP 유형 이름</span><span class="sxs-lookup"><span data-stu-id="f8960-116">BCP type name</span></span>|<span data-ttu-id="f8960-117">MaxType</span><span class="sxs-lookup"><span data-stu-id="f8960-117">MaxType</span></span>|<span data-ttu-id="f8960-118">출력</span><span class="sxs-lookup"><span data-stu-id="f8960-118">Output</span></span>|  
|-------------------|-------------|------------|  
|`SQLDECIMAL`|<span data-ttu-id="f8960-119">여기서는</span><span class="sxs-lookup"><span data-stu-id="f8960-119">Either</span></span>|<span data-ttu-id="f8960-120">**decimal**</span><span class="sxs-lookup"><span data-stu-id="f8960-120">**decimal**</span></span>|  
|`SQLNUMERIC`|<span data-ttu-id="f8960-121">여기서는</span><span class="sxs-lookup"><span data-stu-id="f8960-121">Either</span></span>|<span data-ttu-id="f8960-122">**numeric**</span><span class="sxs-lookup"><span data-stu-id="f8960-122">**numeric**</span></span>|  
|`SQLINT1`|<span data-ttu-id="f8960-123">여기서는</span><span class="sxs-lookup"><span data-stu-id="f8960-123">Either</span></span>|<span data-ttu-id="f8960-124">**tinyint**</span><span class="sxs-lookup"><span data-stu-id="f8960-124">**tinyint**</span></span>|  
|`SQLINT2`|<span data-ttu-id="f8960-125">여기서는</span><span class="sxs-lookup"><span data-stu-id="f8960-125">Either</span></span>|<span data-ttu-id="f8960-126">**smallint**</span><span class="sxs-lookup"><span data-stu-id="f8960-126">**smallint**</span></span>|  
|`SQLINT4`|<span data-ttu-id="f8960-127">여기서는</span><span class="sxs-lookup"><span data-stu-id="f8960-127">Either</span></span>|<span data-ttu-id="f8960-128">**int**</span><span class="sxs-lookup"><span data-stu-id="f8960-128">**int**</span></span>|  
|`SQLMONEY`|<span data-ttu-id="f8960-129">여기서는</span><span class="sxs-lookup"><span data-stu-id="f8960-129">Either</span></span>|<span data-ttu-id="f8960-130">**money**</span><span class="sxs-lookup"><span data-stu-id="f8960-130">**money**</span></span>|  
|`SQLFLT8`|<span data-ttu-id="f8960-131">여기서는</span><span class="sxs-lookup"><span data-stu-id="f8960-131">Either</span></span>|<span data-ttu-id="f8960-132">**float**</span><span class="sxs-lookup"><span data-stu-id="f8960-132">**float**</span></span>|  
|`SQLDATETIME`|<span data-ttu-id="f8960-133">여기서는</span><span class="sxs-lookup"><span data-stu-id="f8960-133">Either</span></span>|<span data-ttu-id="f8960-134">**datetime**</span><span class="sxs-lookup"><span data-stu-id="f8960-134">**datetime**</span></span>|  
|`SQLBITN`|<span data-ttu-id="f8960-135">여기서는</span><span class="sxs-lookup"><span data-stu-id="f8960-135">Either</span></span>|<span data-ttu-id="f8960-136">**bit-null**</span><span class="sxs-lookup"><span data-stu-id="f8960-136">**bit-null**</span></span>|  
|`SQLBIT`|<span data-ttu-id="f8960-137">여기서는</span><span class="sxs-lookup"><span data-stu-id="f8960-137">Either</span></span>|<span data-ttu-id="f8960-138">**bit**</span><span class="sxs-lookup"><span data-stu-id="f8960-138">**bit**</span></span>|  
|`SQLBIGCHAR`|<span data-ttu-id="f8960-139">아니요</span><span class="sxs-lookup"><span data-stu-id="f8960-139">No</span></span>|<span data-ttu-id="f8960-140">**char**</span><span class="sxs-lookup"><span data-stu-id="f8960-140">**char**</span></span>|  
|`SQLCHARACTER`|<span data-ttu-id="f8960-141">아니요</span><span class="sxs-lookup"><span data-stu-id="f8960-141">No</span></span>|<span data-ttu-id="f8960-142">**char**</span><span class="sxs-lookup"><span data-stu-id="f8960-142">**char**</span></span>|  
|`SQLBIGVARCHAR`|<span data-ttu-id="f8960-143">아니요</span><span class="sxs-lookup"><span data-stu-id="f8960-143">No</span></span>|<span data-ttu-id="f8960-144">**varchar**</span><span class="sxs-lookup"><span data-stu-id="f8960-144">**varchar**</span></span>|  
|`SQLVARCHAR`|<span data-ttu-id="f8960-145">예</span><span class="sxs-lookup"><span data-stu-id="f8960-145">No</span></span>|<span data-ttu-id="f8960-146">**varchar**</span><span class="sxs-lookup"><span data-stu-id="f8960-146">**varchar**</span></span>|  
|`SQLTEXT`|<span data-ttu-id="f8960-147">여기서는</span><span class="sxs-lookup"><span data-stu-id="f8960-147">Either</span></span>|<span data-ttu-id="f8960-148">**text**</span><span class="sxs-lookup"><span data-stu-id="f8960-148">**text**</span></span>|  
|`SQLBIGBINARY`|<span data-ttu-id="f8960-149">예</span><span class="sxs-lookup"><span data-stu-id="f8960-149">No</span></span>|<span data-ttu-id="f8960-150">**binary**</span><span class="sxs-lookup"><span data-stu-id="f8960-150">**binary**</span></span>|  
|`SQLBINARY`|<span data-ttu-id="f8960-151">아니요</span><span class="sxs-lookup"><span data-stu-id="f8960-151">No</span></span>|<span data-ttu-id="f8960-152">**이진**</span><span class="sxs-lookup"><span data-stu-id="f8960-152">**Binary**</span></span>|  
|`SQLBIGVARBINARY`|<span data-ttu-id="f8960-153">아니요</span><span class="sxs-lookup"><span data-stu-id="f8960-153">No</span></span>|<span data-ttu-id="f8960-154">**Varbinary**</span><span class="sxs-lookup"><span data-stu-id="f8960-154">**Varbinary**</span></span>|  
|`SQLVARBINARY`|<span data-ttu-id="f8960-155">아니요</span><span class="sxs-lookup"><span data-stu-id="f8960-155">No</span></span>|<span data-ttu-id="f8960-156">**Varbinary**</span><span class="sxs-lookup"><span data-stu-id="f8960-156">**Varbinary**</span></span>|  
|`SQLIMAGE`|<span data-ttu-id="f8960-157">여기서는</span><span class="sxs-lookup"><span data-stu-id="f8960-157">Either</span></span>|<span data-ttu-id="f8960-158">**Image**</span><span class="sxs-lookup"><span data-stu-id="f8960-158">**Image**</span></span>|  
|`SQLINTN`|<span data-ttu-id="f8960-159">여기서는</span><span class="sxs-lookup"><span data-stu-id="f8960-159">Either</span></span>|<span data-ttu-id="f8960-160">**int-null**</span><span class="sxs-lookup"><span data-stu-id="f8960-160">**int-null**</span></span>|  
|`SQLDATETIMN`|<span data-ttu-id="f8960-161">여기서는</span><span class="sxs-lookup"><span data-stu-id="f8960-161">Either</span></span>|<span data-ttu-id="f8960-162">**datetime-null**</span><span class="sxs-lookup"><span data-stu-id="f8960-162">**datetime-null**</span></span>|  
|`SQLMONEYN`|<span data-ttu-id="f8960-163">여기서는</span><span class="sxs-lookup"><span data-stu-id="f8960-163">Either</span></span>|<span data-ttu-id="f8960-164">**money-null**</span><span class="sxs-lookup"><span data-stu-id="f8960-164">**money-null**</span></span>|  
|`SQLFLTN`|<span data-ttu-id="f8960-165">여기서는</span><span class="sxs-lookup"><span data-stu-id="f8960-165">Either</span></span>|<span data-ttu-id="f8960-166">**float-null**</span><span class="sxs-lookup"><span data-stu-id="f8960-166">**float-null**</span></span>|  
|`SQLAOPSUM`|<span data-ttu-id="f8960-167">여기서는</span><span class="sxs-lookup"><span data-stu-id="f8960-167">Either</span></span>|<span data-ttu-id="f8960-168">**총합**</span><span class="sxs-lookup"><span data-stu-id="f8960-168">**Sum**</span></span>|  
|`SQLAOPAVG`|<span data-ttu-id="f8960-169">여기서는</span><span class="sxs-lookup"><span data-stu-id="f8960-169">Either</span></span>|<span data-ttu-id="f8960-170">**매출**</span><span class="sxs-lookup"><span data-stu-id="f8960-170">**Avg**</span></span>|  
|`SQLAOPCNT`|<span data-ttu-id="f8960-171">여기서는</span><span class="sxs-lookup"><span data-stu-id="f8960-171">Either</span></span>|<span data-ttu-id="f8960-172">**Count**</span><span class="sxs-lookup"><span data-stu-id="f8960-172">**Count**</span></span>|  
|`SQLAOPMIN`|<span data-ttu-id="f8960-173">여기서는</span><span class="sxs-lookup"><span data-stu-id="f8960-173">Either</span></span>|<span data-ttu-id="f8960-174">**일별**</span><span class="sxs-lookup"><span data-stu-id="f8960-174">**Min**</span></span>|  
|`SQLAOPMAX`|<span data-ttu-id="f8960-175">여기서는</span><span class="sxs-lookup"><span data-stu-id="f8960-175">Either</span></span>|<span data-ttu-id="f8960-176">**최대값**</span><span class="sxs-lookup"><span data-stu-id="f8960-176">**Max**</span></span>|  
|`SQLDATETIM4`|<span data-ttu-id="f8960-177">여기서는</span><span class="sxs-lookup"><span data-stu-id="f8960-177">Either</span></span>|<span data-ttu-id="f8960-178">**smalldatetime**</span><span class="sxs-lookup"><span data-stu-id="f8960-178">**smalldatetime**</span></span>|  
|`SQLMONEY4`|<span data-ttu-id="f8960-179">여기서는</span><span class="sxs-lookup"><span data-stu-id="f8960-179">Either</span></span>|<span data-ttu-id="f8960-180">**Smallmoney**</span><span class="sxs-lookup"><span data-stu-id="f8960-180">**Smallmoney**</span></span>|  
|`SQLFLT4`|<span data-ttu-id="f8960-181">여기서는</span><span class="sxs-lookup"><span data-stu-id="f8960-181">Either</span></span>|<span data-ttu-id="f8960-182">**실제로**</span><span class="sxs-lookup"><span data-stu-id="f8960-182">**Real**</span></span>|  
|`SQLUNIQUEID`|<span data-ttu-id="f8960-183">여기서는</span><span class="sxs-lookup"><span data-stu-id="f8960-183">Either</span></span>|<span data-ttu-id="f8960-184">**uniqueidentifier**</span><span class="sxs-lookup"><span data-stu-id="f8960-184">**uniqueidentifier**</span></span>|  
|`SQLNCHAR`|<span data-ttu-id="f8960-185">예</span><span class="sxs-lookup"><span data-stu-id="f8960-185">No</span></span>|<span data-ttu-id="f8960-186">**Nchar**</span><span class="sxs-lookup"><span data-stu-id="f8960-186">**Nchar**</span></span>|  
|`SQLNVARCHAR`|<span data-ttu-id="f8960-187">아니요</span><span class="sxs-lookup"><span data-stu-id="f8960-187">No</span></span>|<span data-ttu-id="f8960-188">**Nvarchar**</span><span class="sxs-lookup"><span data-stu-id="f8960-188">**Nvarchar**</span></span>|  
|`SQLNTEXT`|<span data-ttu-id="f8960-189">여기서는</span><span class="sxs-lookup"><span data-stu-id="f8960-189">Either</span></span>|<span data-ttu-id="f8960-190">**N**</span><span class="sxs-lookup"><span data-stu-id="f8960-190">**Ntext**</span></span>|  
|`SQLVARIANT`|<span data-ttu-id="f8960-191">여기서는</span><span class="sxs-lookup"><span data-stu-id="f8960-191">Either</span></span>|<span data-ttu-id="f8960-192">**sql_variant**</span><span class="sxs-lookup"><span data-stu-id="f8960-192">**sql_variant**</span></span>|  
|`SQLINT8`|<span data-ttu-id="f8960-193">여기서는</span><span class="sxs-lookup"><span data-stu-id="f8960-193">Either</span></span>|<span data-ttu-id="f8960-194">**Bigint**</span><span class="sxs-lookup"><span data-stu-id="f8960-194">**Bigint**</span></span>|  
|`SQLCHARACTER`|<span data-ttu-id="f8960-195">예</span><span class="sxs-lookup"><span data-stu-id="f8960-195">Yes</span></span>|<span data-ttu-id="f8960-196">**varchar(max)**</span><span class="sxs-lookup"><span data-stu-id="f8960-196">**varchar(max)**</span></span>|  
|`SQLBIGCHAR`|<span data-ttu-id="f8960-197">예</span><span class="sxs-lookup"><span data-stu-id="f8960-197">Yes</span></span>|<span data-ttu-id="f8960-198">**varchar(max)**</span><span class="sxs-lookup"><span data-stu-id="f8960-198">**varchar(max)**</span></span>|  
|`SQLBIGVARCHAR`|<span data-ttu-id="f8960-199">예</span><span class="sxs-lookup"><span data-stu-id="f8960-199">Yes</span></span>|<span data-ttu-id="f8960-200">**varchar(max)**</span><span class="sxs-lookup"><span data-stu-id="f8960-200">**varchar(max)**</span></span>|  
|`SQLVARCHAR`|<span data-ttu-id="f8960-201">예</span><span class="sxs-lookup"><span data-stu-id="f8960-201">Yes</span></span>|<span data-ttu-id="f8960-202">**varchar(max)**</span><span class="sxs-lookup"><span data-stu-id="f8960-202">**varchar(max)**</span></span>|  
|`SQLBINARY`|<span data-ttu-id="f8960-203">예</span><span class="sxs-lookup"><span data-stu-id="f8960-203">Yes</span></span>|<span data-ttu-id="f8960-204">**varbinary(max)**</span><span class="sxs-lookup"><span data-stu-id="f8960-204">**varbinary(max)**</span></span>|  
|`SQLBIGBINARY`|<span data-ttu-id="f8960-205">예</span><span class="sxs-lookup"><span data-stu-id="f8960-205">Yes</span></span>|<span data-ttu-id="f8960-206">**varbinary(max)**</span><span class="sxs-lookup"><span data-stu-id="f8960-206">**varbinary(max)**</span></span>|  
|`SQLBIGVARBINARY`|<span data-ttu-id="f8960-207">예</span><span class="sxs-lookup"><span data-stu-id="f8960-207">Yes</span></span>|<span data-ttu-id="f8960-208">**varbinary(max)**</span><span class="sxs-lookup"><span data-stu-id="f8960-208">**varbinary(max)**</span></span>|  
|`SQLVARBINARY`|<span data-ttu-id="f8960-209">예</span><span class="sxs-lookup"><span data-stu-id="f8960-209">Yes</span></span>|<span data-ttu-id="f8960-210">**varbinary(max)**</span><span class="sxs-lookup"><span data-stu-id="f8960-210">**varbinary(max)**</span></span>|  
|`SQLNCHAR`|<span data-ttu-id="f8960-211">예</span><span class="sxs-lookup"><span data-stu-id="f8960-211">Yes</span></span>|<span data-ttu-id="f8960-212">**nvarchar(max)**</span><span class="sxs-lookup"><span data-stu-id="f8960-212">**nvarchar(max)**</span></span>|  
|`SQLNVARCHAR`|<span data-ttu-id="f8960-213">예</span><span class="sxs-lookup"><span data-stu-id="f8960-213">Yes</span></span>|<span data-ttu-id="f8960-214">**nvarchar(max)**</span><span class="sxs-lookup"><span data-stu-id="f8960-214">**nvarchar(max)**</span></span>|  
|`SQLXML`|<span data-ttu-id="f8960-215">예</span><span class="sxs-lookup"><span data-stu-id="f8960-215">Yes</span></span>|<span data-ttu-id="f8960-216">**Xml**</span><span class="sxs-lookup"><span data-stu-id="f8960-216">**Xml**</span></span>|  
|`SQLUDT`|<span data-ttu-id="f8960-217">여기서는</span><span class="sxs-lookup"><span data-stu-id="f8960-217">Either</span></span>|<span data-ttu-id="f8960-218">**Udt**</span><span class="sxs-lookup"><span data-stu-id="f8960-218">**Udt**</span></span>|  
  
## <a name="bcp_gettypename-support-for-enhanced-date-and-time-features"></a><span data-ttu-id="f8960-219">향상된 날짜 및 시간 기능에 대한 bcp_gettypename 지원</span><span class="sxs-lookup"><span data-stu-id="f8960-219">bcp_gettypename Support for Enhanced Date and Time Features</span></span>  
 <span data-ttu-id="f8960-220">날짜/시간 형식에 대 한 토큰 매개 변수 값은 [OLE DB 및 ODBC&#41;&#40;향상 된 날짜 및 시간 형식에 대 한 대량 복사 변경 내용 ](../native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md)에서 테이블의 "sqlncli 형식" 열에 설명 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f8960-220">The token parameter values for date/time types are described in the "Type in sqlncli.h" column of the table in [Bulk Copy Changes for Enhanced Date and Time Types &#40;OLE DB and ODBC&#41;](../native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md).</span></span> <span data-ttu-id="f8960-221">반환 값은 "파일 스토리지 유형" 열의 해당 행에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f8960-221">The returned value is in the corresponding row of the "File storage type" column.</span></span>  
  
 <span data-ttu-id="f8960-222">자세한 내용은 [ODBC&#41;&#40;날짜 및 시간 향상 ](../native-client-odbc-date-time/date-and-time-improvements-odbc.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f8960-222">For more information, see [Date and Time Improvements &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8960-223">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f8960-223">See Also</span></span>  
 [<span data-ttu-id="f8960-224">Bulk Copy Functions</span><span class="sxs-lookup"><span data-stu-id="f8960-224">Bulk Copy Functions</span></span>](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
