---
title: SQLGetDescField | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLGetDescField function
ms.assetid: 3e59a37a-28ee-4c91-8968-7fe3b966739d
author: rothja
ms.author: jroth
ms.openlocfilehash: 4538396dbfb5406d0464c4730c1f6f3bd5882799
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652101"
---
# <a name="sqlgetdescfield"></a><span data-ttu-id="06bec-102">SQLGetDescField</span><span class="sxs-lookup"><span data-stu-id="06bec-102">SQLGetDescField</span></span>
  <span data-ttu-id="06bec-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 드라이버는 IRD(구현 행 설명자) 전용의 드라이버별 설명자 필드를 노출합니다.</span><span class="sxs-lookup"><span data-stu-id="06bec-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver exposes driver-specific descriptor fields for the implementation row descriptor (IRD) only.</span></span> <span data-ttu-id="06bec-104">IRD 내에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 설명자 필드는 드라이버별 열 특성을 통해 참조됩니다.</span><span class="sxs-lookup"><span data-stu-id="06bec-104">Within the IRD, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] descriptor fields are referenced through driver-specific column attributes.</span></span> <span data-ttu-id="06bec-105">사용 가능한 드라이버별 설명자 필드의 전체 목록에 대한 자세한 내용은 [SQLColAttribute](sqlcolattribute.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="06bec-105">For information about a complete list of available driver-specific descriptor fields, see [SQLColAttribute](sqlcolattribute.md).</span></span>  
  
 <span data-ttu-id="06bec-106">열 식별자 문자열이 포함된 설명자 필드는 대체로 길이가 0인 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="06bec-106">Descriptor fields that contain column identifier strings are often zero-length strings.</span></span> <span data-ttu-id="06bec-107">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]관련 설명자 필드 값은 모두 읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="06bec-107">All [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-specific descriptor field values are read-only.</span></span>  
  
 <span data-ttu-id="06bec-108">SQLColAttribute를 사용 하 여 검색 된 특성과 마찬가지로 행 수준 특성 (예: SQL_CA_SS_COMPUTE_ID)을 보고 하는 설명자 필드는 결과 집합의 모든 열에 대해 보고 됩니다.</span><span class="sxs-lookup"><span data-stu-id="06bec-108">Like attributes retrieved with SQLColAttribute, descriptor fields that report row-level attributes (such as SQL_CA_SS_COMPUTE_ID) are reported for all columns in the result set.</span></span>  
  
## <a name="sqlgetdescfield-and-table-valued-parameters"></a><span data-ttu-id="06bec-109">SQLGetDescField 및 테이블 반환 매개 변수</span><span class="sxs-lookup"><span data-stu-id="06bec-109">SQLGetDescField and Table-Valued Parameters</span></span>  
 <span data-ttu-id="06bec-110">SQLGetDescField를 사용 하 여 테이블 반환 매개 변수 및 테이블 반환 매개 변수 열의 확장 특성에 대 한 값을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="06bec-110">SQLGetDescField can be used to get values for extended attributes of table-valued parameters and table-valued parameter columns.</span></span> <span data-ttu-id="06bec-111">테이블 반환 매개 변수에 대 한 자세한 내용은 [ODBC&#41;&#40;테이블 반환 매개 변수 ](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="06bec-111">For more information about table-valued parameters, see [Table-Valued Parameters &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).</span></span>  
  
## <a name="sqlgetdescfield-support-for-enhanced-date-and-time-features"></a><span data-ttu-id="06bec-112">향상된 날짜 및 시간 기능에 대한 SQLGetDescField 지원</span><span class="sxs-lookup"><span data-stu-id="06bec-112">SQLGetDescField Support for Enhanced Date and Time Features</span></span>  
 <span data-ttu-id="06bec-113">새로운 날짜/시간 형식에 사용할 수 있는 설명자 필드에 대한 자세한 내용은 [Parameter and Result Metadata](../native-client-odbc-date-time/metadata-parameter-and-result.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="06bec-113">For information about the descriptor fields available with the new date/time types, see [Parameter and Result Metadata](../native-client-odbc-date-time/metadata-parameter-and-result.md).</span></span>  
  
 <span data-ttu-id="06bec-114">자세한 내용은 [ODBC&#41;&#40;날짜 및 시간 향상 ](../native-client-odbc-date-time/date-and-time-improvements-odbc.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="06bec-114">For more information, see [Date and Time Improvements &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).</span></span>  
  
 <span data-ttu-id="06bec-115">부터 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] `SQL_C_SS_TIME2` `time` `SQL_C_SS_TIMESTAMPOFFSET` `datetimeoffset` `SQL_C_BINARY` 응용 프로그램에서 ODBC 3.8를 사용 하는 경우 SQLGetDescField는 대신 (형식) 또는 (의 경우)를 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="06bec-115">Beginning in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], SQLGetDescField can return `SQL_C_SS_TIME2` (for `time` types) or `SQL_C_SS_TIMESTAMPOFFSET` (for `datetimeoffset`) instead of `SQL_C_BINARY`, if your application uses ODBC 3.8.</span></span>  
  
## <a name="sqlgetdescfield-support-for-large-clr-udts"></a><span data-ttu-id="06bec-116">큰 CLR UDT에 대한 SQLGetDescField 지원</span><span class="sxs-lookup"><span data-stu-id="06bec-116">SQLGetDescField Support for Large CLR UDTs</span></span>  
 <span data-ttu-id="06bec-117">`SQLGetDescField`는 큰 CLR UDT(사용자 정의 형식)를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="06bec-117">`SQLGetDescField` supports large CLR user-defined types (UDTs).</span></span> <span data-ttu-id="06bec-118">자세한 내용은 [ODBC&#41;&#40;LARGE CLR 사용자 정의 형식 ](../native-client/odbc/large-clr-user-defined-types-odbc.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="06bec-118">For more information, see [Large CLR User-Defined Types &#40;ODBC&#41;](../native-client/odbc/large-clr-user-defined-types-odbc.md).</span></span>  
  
## <a name="sqlgetdescfield-support-for-sparse-columns"></a><span data-ttu-id="06bec-119">스파스 열에 대한 SQLGetDescField 지원</span><span class="sxs-lookup"><span data-stu-id="06bec-119">SQLGetDescField Support for Sparse Columns</span></span>  
 <span data-ttu-id="06bec-120">SQLGetDescField를 사용 하 여 열이 열 인지 여부를 확인 하는 SQL_CA_SS_IS_COLUMN_SET 새 IRD 필드를 쿼리할 수 있습니다 `column_set` .</span><span class="sxs-lookup"><span data-stu-id="06bec-120">SQLGetDescField can be used to query the new IRD field SQL_CA_SS_IS_COLUMN_SET to determine if a column is a `column_set` column.</span></span>  
  
 <span data-ttu-id="06bec-121">자세한 내용은 [스파스 열 지원 &#40;ODBC&#41;](../native-client/odbc/sparse-columns-support-odbc.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="06bec-121">For more information, see [Sparse Columns Support &#40;ODBC&#41;](../native-client/odbc/sparse-columns-support-odbc.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="06bec-122">예제</span><span class="sxs-lookup"><span data-stu-id="06bec-122">Example</span></span>  
  
```  
typedef struct tagCOMPUTEBYLIST  
    {  
    SQLSMALLINT nBys;  
    SQLSMALLINT aByList[1];  
    } COMPUTEBYLIST;  
typedef COMPUTEBYLIST* PCOMPUTEBYLIST;   
  
SQLHDESC    hIRD;   
SQLINTEGER  cbIRD;   
SQLINTEGER  nSet = 0;   
  
// . . .  
// Execute a statement that contains a COMPUTE clause,  
//  then get the descriptor handle of the IRD and  
//  get some IRD values.  
  
SQLGetStmtAttr(g_hStmt, SQL_ATTR_IMP_ROW_DESC,  
    (SQLPOINTER) &hIRD, sizeof(SQLHDESC), &cbIRD);  
  
// For statement-wide column attributes, any  
//  descriptor record will do. You know that 1 exists,  
//  so use it.  
SQLGetDescField(hIRD, 1, SQL_CA_SS_NUM_COMPUTES,  
    (SQLPOINTER) &nComputes, SQL_IS_INTEGER, &cbIRD);  
  
if (nSet == 0)  
    {  
    SQLINTEGER      nOrderID;  
  
    printf_s("Normal result set.\n");  
  
    for (nCol = 0; nCol < nCols; nCol++)  
        {  
        SQLGetDescField(hIRD, nCol+1,  
            SQL_CA_SS_COLUMN_ORDER,  
            (SQLPOINTER) &nOrderID, SQL_IS_INTEGER,  
            &cbIRD);  
  
        if (nOrderID != 0)  
            {  
            printf_s("Col in ORDER BY, pos: %ld",  
                nOrderID);  
            }  
            printf_s("\n");  
        }  
  
    printf_s("\n");  
    }  
else  
    {  
    PCOMPUTEBYLIST  pByList;  
    SQLSMALLINT     nBy;  
    SQLINTEGER      nColID;  
  
    printf_s("Computed result set number: %lu\n",  
        nSet);  
  
    SQLGetDescField(hIRD, 1, SQL_CA_SS_COMPUTE_BYLIST,  
        (SQLPOINTER) &pByList, SQL_IS_INTEGER,  
        &cbIRD);  
  
    if (pByList != NULL)  
        {  
        printf_s("Clause ordered by columns: ");  
        for (nBy = 0; nBy < pByList->nBys; )  
            {  
            printf_s("%u", pByList->aByList[nBy]);  
            nBy++;  
  
            if (nBy == pByList->nBys)  
                {  
                printf_s("\n");  
                }  
            else  
                {  
                printf_s(", ");  
                }  
            }  
        }  
    else  
        {  
        printf_s("Compute clause set not ordered.\n");  
        }  
  
    for (nCol = 0; nCol < nCols; nCol++)  
        {  
        SQLGetDescField(hIRD, nCol+1,  
            SQL_CA_SS_COLUMN_ID, (SQLPOINTER) &nColID,  
            SQL_IS_INTEGER, &cbIRD);  
        printf_s("ColumnID: %lu, nColID);  
        }  
    printf_s("\n");  
    }  
  
if (SQLMoreResults(g_hStmt) == SQL_SUCCESS)  
    {  
    // Determine the result set indicator.  
    SQLGetDescField(hIRD, 1, SQL_CA_SS_COMPUTE_ID,  
        (SQLPOINTER) &nSet, SQL_IS_INTEGER, &cbIRD);  
    }  
```  
  
## <a name="see-also"></a><span data-ttu-id="06bec-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="06bec-123">See Also</span></span>  
 <span data-ttu-id="06bec-124">[SQLGetDescField 함수](https://go.microsoft.com/fwlink/?LinkId=59351) </span><span class="sxs-lookup"><span data-stu-id="06bec-124">[SQLGetDescField Function](https://go.microsoft.com/fwlink/?LinkId=59351) </span></span>  
 [<span data-ttu-id="06bec-125">ODBC API 구현 정보</span><span class="sxs-lookup"><span data-stu-id="06bec-125">ODBC API Implementation Details</span></span>](odbc-api-implementation-details.md)  
  
  
