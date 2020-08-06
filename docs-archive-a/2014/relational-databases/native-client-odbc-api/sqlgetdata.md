---
title: SQLGetData | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLGetData function
ms.assetid: 204848be-8787-45b4-816f-a60ac9d56fcf
author: rothja
ms.author: jroth
ms.openlocfilehash: c351cf7340bc7b0afeb76b139bd75aa429f56e10
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638753"
---
# <a name="sqlgetdata"></a><span data-ttu-id="225ed-102">SQLGetData</span><span class="sxs-lookup"><span data-stu-id="225ed-102">SQLGetData</span></span>
  <span data-ttu-id="225ed-103">**SQLGetData** 는 열 값을 바인딩하지 않고 결과 집합 데이터를 검색하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="225ed-103">**SQLGetData** is used to retrieve result set data without binding column values.</span></span> <span data-ttu-id="225ed-104">동일한 열에서**SQLGetData** 를 연속해서 호출하여 **text**, **ntext**또는 **image** 데이터 형식 열에서 많은 양의 데이터를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="225ed-104">**SQLGetData** can be called successively on the same column to retrieve large amounts of data from a column with a **text**, **ntext**, or **image** data type.</span></span>  
  
 <span data-ttu-id="225ed-105">애플리케이션이 결과 집합 데이터를 인출하기 위해 변수를 바인딩해야 하는 요구 사항은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="225ed-105">There is no requirement that an application bind variables to fetch result set data.</span></span> <span data-ttu-id="225ed-106">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SQLGetData **를 사용하여**Native Client ODBC 드라이버에서 모든 열의 데이터를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="225ed-106">The data of any column can be retrieved from the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver by using **SQLGetData**.</span></span>  
  
 <span data-ttu-id="225ed-107">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 드라이버는 임의의 열 순서로 데이터를 검색하기 위한 **SQLGetData** 사용을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="225ed-107">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver does not support using **SQLGetData** to retrieve data in random column order.</span></span> <span data-ttu-id="225ed-108">**SQLGetData** 를 사용하여 처리된, 바인딩되지 않은 모든 열은 결과 집합의 바인딩된 열보다 높은 열 서수를 가져야 합니다.</span><span class="sxs-lookup"><span data-stu-id="225ed-108">All unbound columns processed with **SQLGetData** must have higher column ordinals than the bound columns in the result set.</span></span> <span data-ttu-id="225ed-109">애플리케이션은 바인딩되지 않은 가장 낮은 서수 열 값에서 가장 높은 서수 열 값으로 데이터를 처리해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="225ed-109">The application must process data from the lowest unbound ordinal column value to the highest.</span></span> <span data-ttu-id="225ed-110">서수 번호가 더 낮은 열의 데이터를 검색하려고 하면 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="225ed-110">Attempting to retrieve data from a lower ordinally numbered column results in an error.</span></span> <span data-ttu-id="225ed-111">애플리케이션에서 서버 커서를 사용하여 결과 집합 행을 보고하는 경우 현재 행을 다시 인출한 다음 열 값을 인출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="225ed-111">If the application is using server cursors to report result set rows, the application can refetch the current row and then fetch the value of a column.</span></span> <span data-ttu-id="225ed-112">읽기 전용, 정방향 전용 기본 커서에서 문이 실행된 경우 해당 문을 다시 실행하여 **SQLGetData**를 백업해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="225ed-112">If a statement is executed on the default read-only, forward-only cursor, you must re-execute the statement to back up **SQLGetData**.</span></span>  
  
 <span data-ttu-id="225ed-113">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 드라이버는 **SQLGetData**를 사용하여 검색된 **text**, **ntext** 및 **image**데이터의 길이를 정확하게 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="225ed-113">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver accurately reports the length of **text**, **ntext**, and **image** data retrieved using **SQLGetData**.</span></span> <span data-ttu-id="225ed-114">애플리케이션은 *StrLen_or_IndPtr* 매개 변수 반환 값을 이용하여 긴 데이터를 신속하게 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="225ed-114">The application can make good use of the *StrLen_or_IndPtr* parameter return to retrieve long data rapidly.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="225ed-115">큰 값 형식에 대해 *StrLen_or_IndPtr* 은 데이터 잘림이 발생할 경우 SQL_NO_TOTAL을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="225ed-115">For large value types, *StrLen_or_IndPtr* will return SQL_NO_TOTAL in cases of data truncation.</span></span>  
  
## <a name="sqlgetdata-support-for-enhanced-date-and-time-features"></a><span data-ttu-id="225ed-116">향상된 날짜 및 시간 기능에 대한 SQLGetData 지원</span><span class="sxs-lookup"><span data-stu-id="225ed-116">SQLGetData Support for Enhanced Date and Time Features</span></span>  
 <span data-ttu-id="225ed-117">날짜/시간 형식의 결과 열 값은 [SQL에서 C로 변환](../native-client-odbc-date-time/datetime-data-type-conversions-from-sql-to-c.md)에 설명 된 대로 변환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="225ed-117">Result column values of date/time types are converted as described in [Conversions from SQL to C](../native-client-odbc-date-time/datetime-data-type-conversions-from-sql-to-c.md).</span></span>  
  
 <span data-ttu-id="225ed-118">자세한 내용은 [ODBC&#41;&#40;날짜 및 시간 향상 ](../native-client-odbc-date-time/date-and-time-improvements-odbc.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="225ed-118">For more information, see [Date and Time Improvements &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).</span></span>  
  
## <a name="sqlgetdata-support-for-large-clr-udts"></a><span data-ttu-id="225ed-119">큰 CLR UDT에 대한 SQLGetData 지원</span><span class="sxs-lookup"><span data-stu-id="225ed-119">SQLGetData Support for Large CLR UDTs</span></span>  
 <span data-ttu-id="225ed-120">**SQLGetData** 는 큰 CLR UDT(사용자 정의 형식)를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="225ed-120">**SQLGetData** supports large CLR user-defined types (UDTs).</span></span> <span data-ttu-id="225ed-121">자세한 내용은 [ODBC&#41;&#40;LARGE CLR 사용자 정의 형식 ](../native-client/odbc/large-clr-user-defined-types-odbc.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="225ed-121">For more information, see [Large CLR User-Defined Types &#40;ODBC&#41;](../native-client/odbc/large-clr-user-defined-types-odbc.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="225ed-122">예제</span><span class="sxs-lookup"><span data-stu-id="225ed-122">Example</span></span>  
  
```  
SQLHDBC     hDbc = NULL;  
SQLHSTMT    hStmt = NULL;  
long        lEmpID;  
PBYTE       pPicture;  
SQLINTEGER  pIndicators[2];  
  
// Get an environment, connection, and so on.  
...  
  
// Get a statement handle and execute a command.  
SQLAllocHandle(SQL_HANDLE_STMT, hDbc, &hStmt);  
  
if (SQLExecDirect(hStmt,  
    (SQLCHAR*) "SELECT EmployeeID, Photo FROM Employees",  
    SQL_NTS) == SQL_ERROR)  
    {  
    // Handle error and return.  
    }  
  
// Retrieve data from row set.  
SQLBindCol(hStmt, 1, SQL_C_LONG, (SQLPOINTER) &lEmpID, sizeof(long),  
    &pIndicators[0]);  
  
while (SQLFetch(hStmt) == SQL_SUCCESS)  
    {  
    cout << "EmployeeID: " << lEmpID << "\n";  
  
    // Call SQLGetData to determine the amount of data that's waiting.  
    if (SQLGetData(hStmt, 2, SQL_C_BINARY, pPicture, 0, &pIndicators[1])  
        == SQL_SUCCESS_WITH_INFO)  
        {  
        cout << "Photo size: " pIndicators[1] << "\n\n";  
  
        // Get all the data at once.  
        pPicture = new BYTE[pIndicators[1]];  
        if (SQLGetData(hStmt, 2, SQL_C_DEFAULT, pPicture,  
            pIndicators[1], &pIndicators[1]) != SQL_SUCCESS)  
            {  
            // Handle error and continue.  
            }  
  
        delete [] pPicture;  
        }  
    else  
        {  
        // Handle error on attempt to get data length.  
        }  
    }  
```  
  
## <a name="see-also"></a><span data-ttu-id="225ed-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="225ed-123">See Also</span></span>  
 <span data-ttu-id="225ed-124">[SQLGetData 함수](https://go.microsoft.com/fwlink/?LinkId=59350) </span><span class="sxs-lookup"><span data-stu-id="225ed-124">[SQLGetData Function](https://go.microsoft.com/fwlink/?LinkId=59350) </span></span>  
 [<span data-ttu-id="225ed-125">ODBC API 구현 정보</span><span class="sxs-lookup"><span data-stu-id="225ed-125">ODBC API Implementation Details</span></span>](odbc-api-implementation-details.md)  
  
  
