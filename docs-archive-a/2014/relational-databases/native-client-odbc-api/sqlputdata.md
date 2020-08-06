---
title: SQLPutData | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLPutData function
ms.assetid: d39aaa5b-7fbc-4315-a7f2-5a7787e04f25
author: rothja
ms.author: jroth
ms.openlocfilehash: 31da9c21f9e4323a492a25629a979c66a4f7d365
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660525"
---
# <a name="sqlputdata"></a><span data-ttu-id="5568d-102">SQLPutData</span><span class="sxs-lookup"><span data-stu-id="5568d-102">SQLPutData</span></span>
  <span data-ttu-id="5568d-103">SQLPutData를 사용 하 여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SQL_LONGVARCHAR ( `text` ), SQL_WLONGVARCHAR ( `ntext` ) 또는 SQL_LONGVARBINARY () 열에 대해 65535 바이트 이상의 데이터 (버전 4.21 a) 또는 400 KB의 데이터 (SQL Server 버전 6.0 이상)를 전송 하는 경우 다음과 같은 제한 사항이 적용 됩니다 `image` .</span><span class="sxs-lookup"><span data-stu-id="5568d-103">The following restrictions apply when using SQLPutData to send more than 65,535 bytes of data (for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] version 4.21a) or 400 KB of data (for SQL Server version 6.0 and later) for a SQL_LONGVARCHAR (`text`), SQL_WLONGVARCHAR (`ntext`) or SQL_LONGVARBINARY (`image`) column:</span></span>  
  
-   <span data-ttu-id="5568d-104">참조 된 매개 변수는 INSERT 문에서 *insert_value* 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5568d-104">The referenced parameter can be the *insert_value* in an INSERT statement.</span></span>  
  
-   <span data-ttu-id="5568d-105">참조 된 매개 변수는 UPDATE 문의 SET 절에 있는 *식일* 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5568d-105">The referenced parameter can be an *expression* in the SET clause of an UPDATE statement.</span></span>  
  
 <span data-ttu-id="5568d-106">을 실행 하는 서버에 블록의 데이터를 제공 하는 SQLPutData 호출의 시퀀스를 취소 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 하면 버전 6.5 또는 이전 버전을 사용할 때 열의 값이 부분적으로 업데이트 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5568d-106">Canceling a sequence of SQLPutData calls that provide data in blocks to a server running [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] causes a partial update of the column's value when using version 6.5 or earlier.</span></span> <span data-ttu-id="5568d-107">`text` `ntext` `image` Sqlcancel이 호출 될 때 참조 된, 또는 열은 중간 자리 표시자 값으로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5568d-107">The `text`, `ntext`, or `image` column that was referenced when SQLCancel was called is set to an intermediate placeholder value.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5568d-108">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 드라이버는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 6.5 및 이전 버전에 대한 연결을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5568d-108">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver does not support connecting to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] version 6.5 and earlier.</span></span>  
  
## <a name="diagnostics"></a><span data-ttu-id="5568d-109">진단</span><span class="sxs-lookup"><span data-stu-id="5568d-109">Diagnostics</span></span>  
 <span data-ttu-id="5568d-110">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]SQLPutData에 대해 하나의 Native Client 특정 SQLSTATE가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5568d-110">There is one [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client specific SQLSTATE for SQLPutData:</span></span>  
  
|<span data-ttu-id="5568d-111">SQLSTATE</span><span class="sxs-lookup"><span data-stu-id="5568d-111">SQLSTATE</span></span>|<span data-ttu-id="5568d-112">오류</span><span class="sxs-lookup"><span data-stu-id="5568d-112">Error</span></span>|<span data-ttu-id="5568d-113">Description</span><span class="sxs-lookup"><span data-stu-id="5568d-113">Description</span></span>|  
|--------------|-----------|-----------------|  
|<span data-ttu-id="5568d-114">22026</span><span class="sxs-lookup"><span data-stu-id="5568d-114">22026</span></span>|<span data-ttu-id="5568d-115">문자열 데이터, 길이가 일치하지 않음</span><span class="sxs-lookup"><span data-stu-id="5568d-115">String data, length mismatch</span></span>|<span data-ttu-id="5568d-116">전송할 데이터 길이 (바이트)를 응용 프로그램에서 지정 하는*경우 (예*SQL_LEN_DATA_AT_EXEC: *n* 이 0 보다 큰 경우)에는 sqlputdata를 통해 응용 프로그램에서 제공 하는 총 바이트 수가 지정 된 길이와 일치 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5568d-116">If the length of data in bytes to be sent has been specified by an application, for example, with SQL_LEN_DATA_AT_EXEC(*n*) where *n* is greater than 0, the total number of bytes given by the application via SQLPutData must match the specified length.</span></span>|  
  
## <a name="sqlputdata-and-table-valued-parameters"></a><span data-ttu-id="5568d-117">SQLPutData 및 테이블 반환 매개 변수</span><span class="sxs-lookup"><span data-stu-id="5568d-117">SQLPutData and Table-Valued Parameters</span></span>  
 <span data-ttu-id="5568d-118">SQLPutData는 테이블 반환 매개 변수와 함께 가변 행 바인딩을 사용할 때 응용 프로그램에서 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5568d-118">SQLPutData is used by an application when using variable row binding with table-valued parameters.</span></span> <span data-ttu-id="5568d-119">*StrLen_Or_Ind* 매개 변수는 드라이버가 다음 행 또는 테이블 반환 매개 변수 데이터의 행에 대 한 데이터를 수집할 준비가 되었거나 더 이상 행을 사용할 수 없음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5568d-119">The *StrLen_Or_Ind* parameter indicates that it is ready for the driver to collect data for the next row or rows of table-valued parameter data, or that no more rows are available:</span></span>  
  
-   <span data-ttu-id="5568d-120">0보다 큰 값은 다음 행 값의 집합을 사용할 수 있음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5568d-120">A value greater than 0 indicates that the next set of row values is available.</span></span>  
  
-   <span data-ttu-id="5568d-121">값이 0이면 보낼 행이 더 이상 없음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5568d-121">A value of 0 indicates that there are no more rows to be sent.</span></span>  
  
-   <span data-ttu-id="5568d-122">0보다 작은 값은 오류를 나타내며 SQLState HY090 및 "잘못된 문자열 또는 버퍼 길이입니다."라는 메시지가 포함된 진단 레코드가 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="5568d-122">Any value less than 0 is an error and results in a diagnostic record being logged with SQLState HY090 and the messaage "Invalid string or buffer length".</span></span>  
  
 <span data-ttu-id="5568d-123">*Dataptr* 매개 변수는 무시 되지만 NULL이 아닌 값으로 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5568d-123">The *DataPtr* parameter is ignored, but must be set to a non-NULL value.</span></span> <span data-ttu-id="5568d-124">자세한 내용은 [테이블 반환 매개 변수 및 열 값의 바인딩 및 데이터 전송](../native-client-odbc-table-valued-parameters/binding-and-data-transfer-of-table-valued-parameters-and-column-values.md)의 변수 TVP 행 바인딩에 대 한 섹션을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5568d-124">For more information, see the section on Variable TVP row binding in [Binding and Data Transfer of Table-Valued Parameters and Column Values](../native-client-odbc-table-valued-parameters/binding-and-data-transfer-of-table-valued-parameters-and-column-values.md).</span></span>  
  
 <span data-ttu-id="5568d-125">*StrLen_Or_Ind* 의 값이 SQL_DEFAULT_PARAM 또는 0과 SQL_PARAMSET_SIZE 사이의 숫자 (즉, SQLBindParameter의 *columnsize* 매개 변수) 인 경우에는 오류가 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="5568d-125">If *StrLen_Or_Ind* has any value other than SQL_DEFAULT_PARAM or a number between 0 and the SQL_PARAMSET_SIZE (that is, the *ColumnSize* parameter of SQLBindParameter), it is an error.</span></span> <span data-ttu-id="5568d-126">이 오류가 발생 하면 SQLPutData에서 SQLSTATE = HY090, "잘못 된 문자열 또는 버퍼 길이" SQL_ERROR 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5568d-126">This error causes SQLPutData to return SQL_ERROR: SQLSTATE=HY090, "Invalid string or buffer length".</span></span>  
  
 <span data-ttu-id="5568d-127">테이블 반환 매개 변수에 대 한 자세한 내용은 [ODBC&#41;&#40;테이블 반환 매개 변수 ](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5568d-127">For more information about table-valued parameters, see [Table-Valued Parameters &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).</span></span>  
  
## <a name="sqlputdata-support-for-enhanced-date-and-time-features"></a><span data-ttu-id="5568d-128">향상된 날짜 및 시간 기능에 대한 SQLPutData 지원</span><span class="sxs-lookup"><span data-stu-id="5568d-128">SQLPutData Support for Enhanced Date and Time Features</span></span>  
 <span data-ttu-id="5568d-129">날짜/시간 형식의 매개 변수 값은 [C에서 SQL로 변환](../native-client-odbc-date-time/datetime-data-type-conversions-from-c-to-sql.md)에 설명 된 대로 변환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5568d-129">Parameter values of date/time types are converted as described in [Conversions from C to SQL](../native-client-odbc-date-time/datetime-data-type-conversions-from-c-to-sql.md).</span></span>  
  
 <span data-ttu-id="5568d-130">자세한 내용은 [ODBC&#41;&#40;날짜 및 시간 향상 ](../native-client-odbc-date-time/date-and-time-improvements-odbc.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5568d-130">For more information, see [Date and Time Improvements &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).</span></span>  
  
## <a name="sqlputdata-support-for-large-clr-udts"></a><span data-ttu-id="5568d-131">큰 CLR UDT에 대한 SQLPutData 지원</span><span class="sxs-lookup"><span data-stu-id="5568d-131">SQLPutData Support for Large CLR UDTs</span></span>  
 <span data-ttu-id="5568d-132">`SQLPutData`는 큰 CLR UDT(사용자 정의 형식)를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="5568d-132">`SQLPutData` supports large CLR user-defined types (UDTs).</span></span> <span data-ttu-id="5568d-133">자세한 내용은 [ODBC&#41;&#40;LARGE CLR 사용자 정의 형식 ](../native-client/odbc/large-clr-user-defined-types-odbc.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5568d-133">For more information, see [Large CLR User-Defined Types &#40;ODBC&#41;](../native-client/odbc/large-clr-user-defined-types-odbc.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5568d-134">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5568d-134">See Also</span></span>  
 <span data-ttu-id="5568d-135">[SQLPutData 함수](https://go.microsoft.com/fwlink/?LinkId=59365) </span><span class="sxs-lookup"><span data-stu-id="5568d-135">[SQLPutData Function](https://go.microsoft.com/fwlink/?LinkId=59365) </span></span>  
 [<span data-ttu-id="5568d-136">ODBC API 구현 정보</span><span class="sxs-lookup"><span data-stu-id="5568d-136">ODBC API Implementation Details</span></span>](odbc-api-implementation-details.md)  
  
  
