---
title: SQLBindParameter | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLBindParameter function
ms.assetid: c302c87a-e7f4-4d2b-a0a7-de42210174ac
author: rothja
ms.author: jroth
ms.openlocfilehash: 6e50886457c4c20110880cc5b75ec594fd3eaba5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660544"
---
# <a name="sqlbindparameter"></a><span data-ttu-id="118a1-102">SQLBindParameter</span><span class="sxs-lookup"><span data-stu-id="118a1-102">SQLBindParameter</span></span>
  <span data-ttu-id="118a1-103">`SQLBindParameter`는 Native Client ODBC 드라이버에 대 한 데이터를 제공 하는 데 사용 될 때 데이터 변환 부담을 없앨 수 있으므로 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 응용 프로그램의 클라이언트 및 서버 구성 요소 모두에서 성능이 크게 향상 됩니다.</span><span class="sxs-lookup"><span data-stu-id="118a1-103">`SQLBindParameter` can eliminate the burden of data conversion when used to provide data for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver, resulting in significant performance gains for both the client and server components of applications.</span></span> <span data-ttu-id="118a1-104">이 외에도 근사치 데이터 형식을 삽입하거나 업데이트할 경우의 전체 자릿수 손실을 줄일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="118a1-104">Other benefits include reduced loss of precision when inserting or updating approximate numeric data types.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="118a1-105">`char` 및 `wchar` 형식 데이터를 이미지 열에 삽입할 경우 이진 형식으로 변환된 후의 데이터 크기가 아니라 전달되는 데이터의 크기가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="118a1-105">When inserting `char` and `wchar` type data into an image column, the size of the data being passed in is used, as opposed to the size of the data after conversion to a binary format.</span></span>  
  
 <span data-ttu-id="118a1-106">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 드라이버에서 매개 변수 배열의 배열 요소 하나에 오류가 발생하면 드라이버는 나머지 배열 요소에 대해 문을 계속해서 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="118a1-106">If the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver encounters an error on a single array element of an array of parameters, the driver continues to execute the statement for the remaining array elements.</span></span> <span data-ttu-id="118a1-107">애플리케이션에서 문에 대해 매개 변수 상태 요소의 배열을 바인딩한 경우에는 오류가 발생한 매개 변수의 행을 배열에서 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="118a1-107">If the application has bound an array of parameter status elements for the statement, the rows of parameters generating errors can be determined from the array.</span></span>  
  
 <span data-ttu-id="118a1-108">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 드라이버를 사용할 경우 입력 매개 변수를 바인딩할 때 SQL_PARAM_INPUT을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="118a1-108">When using the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver, specify SQL_PARAM_INPUT when binding input parameters.</span></span> <span data-ttu-id="118a1-109">OUTPUT 키워드를 사용하여 정의된 저장 프로시저 매개 변수를 바인딩할 경우에는 SQL_PARAM_OUTPUT 또는 SQL_PARAM_INPUT_OUTPUT만 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="118a1-109">Only specify SQL_PARAM_OUTPUT or SQL_PARAM_INPUT_OUTPUT when binding stored procedure parameters defined with the OUTPUT keyword.</span></span>  
  
 <span data-ttu-id="118a1-110">[SQLRowCount](sqlrowcount.md) [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 바인딩된 매개 변수 배열의 배열 요소에서 문 실행 시 오류가 발생 하는 경우에는 Native Client ODBC 드라이버를 사용 하 여 sqlrowcount를 신뢰할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="118a1-110">[SQLRowCount](sqlrowcount.md) is unreliable with the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver if an array element of a bound-parameter array causes an error in statement execution.</span></span> <span data-ttu-id="118a1-111">ODBC 문 특성 SQL_ATTR_PARAMS_PROCESSED_PTR은 오류가 발생하기 전까지 처리된 행 수를 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="118a1-111">The ODBC statement attribute SQL_ATTR_PARAMS_PROCESSED_PTR reports the number of rows processed before the error occurs.</span></span> <span data-ttu-id="118a1-112">그러면 필요한 경우 애플리케이션에서는 해당 매개 변수 상태 배열을 확인하여 성공적으로 실행된 문 수를 파악할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="118a1-112">The application can then traverse its parameter status array to discover the number of statements successfully executed, if necessary.</span></span>  
  
## <a name="binding-parameters-for-sql-character-types"></a><span data-ttu-id="118a1-113">SQL 문자 형식에 대한 매개 변수 바인딩</span><span class="sxs-lookup"><span data-stu-id="118a1-113">Binding Parameters for SQL Character Types</span></span>  
 <span data-ttu-id="118a1-114">전달된 SQL 데이터 형식이 문자 형식인 경우 *ColumnSize* 는 문자 수입니다(바이트 아님).</span><span class="sxs-lookup"><span data-stu-id="118a1-114">If the SQL data type passed in is a character type, *ColumnSize* is the size in characters (not bytes).</span></span> <span data-ttu-id="118a1-115">바이트 단위의 데이터 문자열 길이가 8000 보다 큰 경우 *Columnsize* 는 `SQL_SS_LENGTH_UNLIMITED` SQL 형식의 크기에 제한이 없음을 나타내는로 설정 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="118a1-115">If the length of the data string in bytes is greater than 8000, *ColumnSize* should be set to `SQL_SS_LENGTH_UNLIMITED`, indicating that there is no limit to the size of the SQL type.</span></span>  
  
 <span data-ttu-id="118a1-116">예를 들어 SQL 데이터 형식이 인 경우 `SQL_WVARCHAR` *columnsize* 는 4000 보다 클 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="118a1-116">For instance, if the SQL data type is `SQL_WVARCHAR`, *ColumnSize* should not be greater than 4000.</span></span> <span data-ttu-id="118a1-117">실제 데이터 길이가 4000 보다 큰 경우에는 *Columnsize* 를로 설정 하 `SQL_SS_LENGTH_UNLIMITED` `nvarchar(max)` 여가 드라이버에서 사용 되도록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="118a1-117">If the actual data length is greater than 4000, then *ColumnSize* should be set to `SQL_SS_LENGTH_UNLIMITED` so that `nvarchar(max)` will be used by driver.</span></span>  
  
## <a name="sqlbindparameter-and-table-valued-parameters"></a><span data-ttu-id="118a1-118">SQLBindParameter와 테이블 반환 매개 변수</span><span class="sxs-lookup"><span data-stu-id="118a1-118">SQLBindParameter and Table-Valued Parameters</span></span>  
 <span data-ttu-id="118a1-119">다른 매개 변수 형식과 마찬가지로 테이블 반환 매개 변수는 SQLBindParameter에 의해 바인딩됩니다.</span><span class="sxs-lookup"><span data-stu-id="118a1-119">Like other parameter types, table-valued parameters are bound by SQLBindParameter.</span></span>  
  
 <span data-ttu-id="118a1-120">테이블 반환 매개 변수가 바인딩된 후에는 해당 열도 바인딩됩니다.</span><span class="sxs-lookup"><span data-stu-id="118a1-120">After a table-valued parameter has been bound, its columns are also bound.</span></span> <span data-ttu-id="118a1-121">열을 바인딩하려면 [SQLSetStmtAttr](sqlsetstmtattr.md) 을 호출하여 테이블 반환 매개 변수의 서수에 SQL_SOPT_SS_PARAM_FOCUS를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="118a1-121">To bind the columns, you call [SQLSetStmtAttr](sqlsetstmtattr.md) to set SQL_SOPT_SS_PARAM_FOCUS to the ordinal of the table-valued parameter.</span></span> <span data-ttu-id="118a1-122">그런 다음 테이블 반환 매개 변수의 각 열에 대해 SQLBindParameter를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="118a1-122">Then, call SQLBindParameter for each column in the table-valued parameter.</span></span> <span data-ttu-id="118a1-123">SQL_SOPT_SS_PARAM_FOCUS를 0으로 설정하면 최상위 매개 변수 바인딩으로 돌아갈 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="118a1-123">To return to the top-level parameter bindings, set SQL_SOPT_SS_PARAM_FOCUS to 0.</span></span>  
  
 <span data-ttu-id="118a1-124">매개 변수를 테이블 반환 매개 변수의 설명자 필드에 매핑하는 방법에 대 한 자세한 내용은 [테이블 반환 매개 변수 및 열 값의 바인딩 및 데이터 전송](../native-client-odbc-table-valued-parameters/binding-and-data-transfer-of-table-valued-parameters-and-column-values.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="118a1-124">For information about mapping parameters to descriptor fields for table-valued parameters, see [Binding and Data Transfer of Table-Valued Parameters and Column Values](../native-client-odbc-table-valued-parameters/binding-and-data-transfer-of-table-valued-parameters-and-column-values.md).</span></span>  
  
 <span data-ttu-id="118a1-125">테이블 반환 매개 변수에 대 한 자세한 내용은 [ODBC&#41;&#40;테이블 반환 매개 변수 ](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="118a1-125">For more information about table-valued parameters, see [Table-Valued Parameters &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).</span></span>  
  
## <a name="sqlbindparameter-support-for-enhanced-date-and-time-features"></a><span data-ttu-id="118a1-126">향상된 날짜 및 시간 기능에 대한 SQLBindParameter 지원</span><span class="sxs-lookup"><span data-stu-id="118a1-126">SQLBindParameter Support for Enhanced Date and Time Features</span></span>  
 <span data-ttu-id="118a1-127">날짜/시간 형식의 매개 변수 값은 [C에서 SQL로 변환](../native-client-odbc-date-time/datetime-data-type-conversions-from-c-to-sql.md)에 설명 된 대로 변환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="118a1-127">Parameter values of date/time types are converted as described in [Conversions from C to SQL](../native-client-odbc-date-time/datetime-data-type-conversions-from-c-to-sql.md).</span></span> <span data-ttu-id="118a1-128">및 형식의 매개 변수는 `time` `datetimeoffset` 해당 하는 *ValueType* `SQL_C_DEFAULT` `SQL_C_BINARY` 구조체 (및)를 사용 하는 경우 또는로 지정 된 ValueType을 포함 해야 합니다 `SQL_SS_TIME2_STRUCT` `SQL_SS_TIMESTAMPOFFSET_STRUCT` .</span><span class="sxs-lookup"><span data-stu-id="118a1-128">Note that parameters of type `time` and `datetimeoffset` must have *ValueType* specified as `SQL_C_DEFAULT` or `SQL_C_BINARY` if their corresponding structures (`SQL_SS_TIME2_STRUCT` and `SQL_SS_TIMESTAMPOFFSET_STRUCT`) are used.</span></span>  
  
 <span data-ttu-id="118a1-129">자세한 내용은 [ODBC&#41;&#40;날짜 및 시간 향상 ](../native-client-odbc-date-time/date-and-time-improvements-odbc.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="118a1-129">For more information, see [Date and Time Improvements &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).</span></span>  
  
## <a name="sqlbindparameter-support-for-large-clr-udts"></a><span data-ttu-id="118a1-130">큰 CLR UDT에 대한 SQLBindParameter 지원</span><span class="sxs-lookup"><span data-stu-id="118a1-130">SQLBindParameter Support for Large CLR UDTs</span></span>  
 <span data-ttu-id="118a1-131">`SQLBindParameter`는 큰 CLR UDT(사용자 정의 형식)를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="118a1-131">`SQLBindParameter` supports large CLR user-defined types (UDTs).</span></span> <span data-ttu-id="118a1-132">자세한 내용은 [ODBC&#41;&#40;LARGE CLR 사용자 정의 형식 ](../native-client/odbc/large-clr-user-defined-types-odbc.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="118a1-132">For more information, see [Large CLR User-Defined Types &#40;ODBC&#41;](../native-client/odbc/large-clr-user-defined-types-odbc.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="118a1-133">참고 항목</span><span class="sxs-lookup"><span data-stu-id="118a1-133">See Also</span></span>  
 <span data-ttu-id="118a1-134">[ODBC API 구현 세부 정보](odbc-api-implementation-details.md) </span><span class="sxs-lookup"><span data-stu-id="118a1-134">[ODBC API Implementation Details](odbc-api-implementation-details.md) </span></span>  
 [<span data-ttu-id="118a1-135">SQLBindParameter 함수</span><span class="sxs-lookup"><span data-stu-id="118a1-135">SQLBindParameter Function</span></span>](https://go.microsoft.com/fwlink/?LinkId=59328)  
  
  
