---
title: SQLBindCol | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLBindCol function
ms.assetid: fbd7ba20-d917-4ca9-b018-018ac6af9f98
author: rothja
ms.author: jroth
ms.openlocfilehash: 72d0ca1b0fbad144117e409019d8d2247bbf918f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742039"
---
# <a name="sqlbindcol"></a><span data-ttu-id="9e572-102">SQLBindCol</span><span class="sxs-lookup"><span data-stu-id="9e572-102">SQLBindCol</span></span>
  <span data-ttu-id="9e572-103">일반적으로 **SQLBindCol** 를 사용 하 여 데이터를 변환 하는 경우의 의미를 고려 하십시오.</span><span class="sxs-lookup"><span data-stu-id="9e572-103">As a general rule, consider the implications of using **SQLBindCol** to cause data conversion.</span></span> <span data-ttu-id="9e572-104">바인딩 변환은 클라이언트 프로세스입니다. 예를 들어 문자 열에 바인딩된 부동 소수점 값을 검색하면 행이 인출될 때 드라이버가 부동 소수점 수에서 문자로의 변환을 로컬로 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="9e572-104">Binding conversions are client processes, so, for example, retrieving a floating-point value bound to a character column causes the driver to perform the float-to-character conversion locally when a row is fetched.</span></span> <span data-ttu-id="9e572-105">[!INCLUDE[tsql](../../includes/tsql-md.md)] CONVERT 함수를 사용하면 데이터 변환 비용을 서버가 부담하도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e572-105">The [!INCLUDE[tsql](../../includes/tsql-md.md)] CONVERT function can be used to place the cost of data conversion on the server.</span></span>  
  
 <span data-ttu-id="9e572-106">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스의 단일 문 실행에서 결과 행의 집합이 여러 개 반환될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e572-106">An instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] can return multiple sets of result rows on a single statement execution.</span></span> <span data-ttu-id="9e572-107">이 경우 각 결과 집합은 개별적으로 바인딩해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e572-107">Each result set must be bound separately.</span></span> <span data-ttu-id="9e572-108">여러 결과 집합을 바인딩하는 방법에 대 한 자세한 내용은 [SQLMoreResults](sqlmoreresults.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9e572-108">For more information about binding for multiple result sets, see [SQLMoreResults](sqlmoreresults.md).</span></span>  
  
 <span data-ttu-id="9e572-109">개발자는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] *TargetType* 값을 사용 하 여 특정 C 데이터 형식에 열을 바인딩할 수 있습니다 `SQL_C_BINARY` .</span><span class="sxs-lookup"><span data-stu-id="9e572-109">The developer can bind columns to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-specific C data types using the *TargetType* value `SQL_C_BINARY`.</span></span> <span data-ttu-id="9e572-110">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 관련 형식에 바인딩된 열은 이식할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9e572-110">Columns bound to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-specific types are not portable.</span></span> <span data-ttu-id="9e572-111">정의된 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 관련 ODBC C 데이터 형식은 DB-Library의 형식 정의와 일치하므로 애플리케이션을 이식하는 DB-Library 개발자는 이 기능을 이용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e572-111">The defined [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-specific ODBC C data types match the type definitions for DB-Library, and DB-Library developers porting applications may want to take advantage of this feature.</span></span>  
  
 <span data-ttu-id="9e572-112">보고 데이터 잘림은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native CLIENT ODBC 드라이버에 대 한 비용이 많이 드는 프로세스입니다.</span><span class="sxs-lookup"><span data-stu-id="9e572-112">Reporting data truncation is an expensive process for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver.</span></span> <span data-ttu-id="9e572-113">모든 바인딩된 데이터 버퍼의 너비가 반환되는 데이터를 수용할 만큼 넓으면 잘림을 피할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e572-113">You can avoid truncation by ensuring that all bound data buffers are wide enough to return data.</span></span> <span data-ttu-id="9e572-114">문자 데이터의 경우 문자열 종료에 기본 드라이버 동작이 사용될 때는 문자열 종결자를 수용하기 위한 공간도 너비에 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e572-114">For character data, the width should include space for a string terminator when the default driver behavior for string termination is used.</span></span> <span data-ttu-id="9e572-115">예를 들어 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **char (5)** 열을 5 개 문자의 배열에 바인딩하면 인출 되는 모든 값에 대해 잘림이 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e572-115">For example, binding a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **char(5)** column to an array of five characters results in truncation for every value fetched.</span></span> <span data-ttu-id="9e572-116">그러나 이 열을 6개 문자의 배열에 바인딩하면 Null 종결자를 저장할 문자 요소가 제공되므로 잘림이 발생하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9e572-116">Binding the same column to an array of six characters avoids the truncation by providing a character element in which to store the null terminator.</span></span> <span data-ttu-id="9e572-117">[SQLGetData](sqlgetdata.md) 는 잘림 없이 긴 문자 및 이진 데이터를 효율적으로 검색 하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e572-117">[SQLGetData](sqlgetdata.md) can be used to efficiently retrieve long character and binary data without truncation.</span></span>  
  
 <span data-ttu-id="9e572-118">대량 값 데이터 형식의 경우 사용자가 제공한 버퍼가 열의 전체 값을 저장할 만큼 크지 않은 경우 `SQL_SUCCESS_WITH_INFO` 이 반환 되 고 "문자열 데이터; 오른쪽 잘림 "경고가 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e572-118">For large value data types, if the user supplied buffer isn't large enough to hold the entire value of the column, `SQL_SUCCESS_WITH_INFO` is returned and the "string data; right truncation" warning is issued.</span></span> <span data-ttu-id="9e572-119">`StrLen_or_IndPtr` 인수에는 버퍼에 저장된 문자/바이트의 수가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e572-119">The `StrLen_or_IndPtr` argument will contain the number of chars/bytes stored in the buffer.</span></span>  
  
## <a name="sqlbindcol-support-for-enhanced-date-and-time-features"></a><span data-ttu-id="9e572-120">향상된 날짜 및 시간 기능에 대한 SQLBindCol 지원</span><span class="sxs-lookup"><span data-stu-id="9e572-120">SQLBindCol Support for Enhanced Date and Time Features</span></span>  
 <span data-ttu-id="9e572-121">날짜/시간 형식의 결과 열 값은 [SQL에서 C로 변환](../native-client-odbc-date-time/datetime-data-type-conversions-from-sql-to-c.md)에 설명 된 대로 변환 됩니다. Time 및 datetimeoffset 열을 해당 하는 구조 ( `SQL_SS_TIME2_STRUCT` 및 **SQL_SS_TIMESTAMPOFFSET_STRUCT**)로 검색 하려면 *TargetType* 을 또는로 지정 해야 `SQL_C_DEFAULT` 합니다 `SQL_C_BINARY` .</span><span class="sxs-lookup"><span data-stu-id="9e572-121">Result column values of date/time types are converted as described in [Conversions from SQL to C](../native-client-odbc-date-time/datetime-data-type-conversions-from-sql-to-c.md). Note that to retrieve time and datetimeoffset columns as their corresponding structures (`SQL_SS_TIME2_STRUCT` and **SQL_SS_TIMESTAMPOFFSET_STRUCT**), *TargetType* must be specified as `SQL_C_DEFAULT` or `SQL_C_BINARY`.</span></span>  
  
 <span data-ttu-id="9e572-122">자세한 내용은 [ODBC&#41;&#40;날짜 및 시간 향상 ](../native-client-odbc-date-time/date-and-time-improvements-odbc.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9e572-122">For more information, see [Date and Time Improvements &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).</span></span>  
  
## <a name="sqlbindcol-support-for-large-clr-udts"></a><span data-ttu-id="9e572-123">큰 CLR UDT에 대한 SQLBindCol 지원</span><span class="sxs-lookup"><span data-stu-id="9e572-123">SQLBindCol Support for Large CLR UDTs</span></span>  
 <span data-ttu-id="9e572-124">**SQLBindCol** 는 많은 CLR udt (사용자 정의 형식)를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e572-124">**SQLBindCol** supports large CLR user-defined types (UDTs).</span></span> <span data-ttu-id="9e572-125">자세한 내용은 [ODBC&#41;&#40;LARGE CLR 사용자 정의 형식 ](../native-client/odbc/large-clr-user-defined-types-odbc.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9e572-125">For more information, see [Large CLR User-Defined Types &#40;ODBC&#41;](../native-client/odbc/large-clr-user-defined-types-odbc.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e572-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9e572-126">See Also</span></span>  
 <span data-ttu-id="9e572-127">[SQLBindCol 함수](https://go.microsoft.com/fwlink/?LinkId=59327) </span><span class="sxs-lookup"><span data-stu-id="9e572-127">[SQLBindCol Function](https://go.microsoft.com/fwlink/?LinkId=59327) </span></span>  
 [<span data-ttu-id="9e572-128">ODBC API 구현 정보</span><span class="sxs-lookup"><span data-stu-id="9e572-128">ODBC API Implementation Details</span></span>](odbc-api-implementation-details.md)  
  
  
