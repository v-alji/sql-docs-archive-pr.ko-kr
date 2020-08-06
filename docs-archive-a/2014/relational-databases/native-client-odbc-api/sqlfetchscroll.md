---
title: SQLFetchScroll | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLFetchScroll function
ms.assetid: 524a3985-a08d-4445-99e0-bb551a666615
author: rothja
ms.author: jroth
ms.openlocfilehash: eecf9714a97577ff490b642cee5b9c380333e40b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649074"
---
# <a name="sqlfetchscroll"></a><span data-ttu-id="7add4-102">SQLFetchScroll</span><span class="sxs-lookup"><span data-stu-id="7add4-102">SQLFetchScroll</span></span>
  <span data-ttu-id="7add4-103">**Sqlfetchscroll** 은 응용 프로그램에 데이터의 한 행 집합을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="7add4-103">**SQLFetchScroll** returns one row set of data to the application.</span></span> <span data-ttu-id="7add4-104">행 집합의 크기는 [SQLSetStmtAttr](sqlsetstmtattr.md)를 사용 하 여 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7add4-104">The size of the row set is set using [SQLSetStmtAttr](sqlsetstmtattr.md).</span></span> <span data-ttu-id="7add4-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native CLIENT ODBC 드라이버는 다음과 같은 제한 사항을 사용 하 여 정의 된 모든 fetch 명령 (예: SQL_FETCH_RELATIVE)을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="7add4-105">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver supports all defined fetch instructions (for example, SQL_FETCH_RELATIVE) with the following limitations:</span></span>  
  
-   <span data-ttu-id="7add4-106">문에 대해 정방향 전용 커서가 정의된 경우 SQL_FETCH_NEXT가 필요하며, 다른 방식으로 인출을 시도하면 오류가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="7add4-106">If a forward-only cursor is defined for the statement, SQL_FETCH_NEXT is required and attempts to fetch in any other fashion will result in an error return.</span></span>  
  
-   <span data-ttu-id="7add4-107">SQL_FETCH_BOOKMARK는 정적 및 키 집합 커서에 대해서만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="7add4-107">SQL_FETCH_BOOKMARK is supported for static and keyset-driven cursors only.</span></span>  
  
## <a name="sqlfetchscroll-support-for-enhanced-date-and-time-features"></a><span data-ttu-id="7add4-108">향상된 날짜 및 시간 기능에 대한 SQLFetchScroll 지원</span><span class="sxs-lookup"><span data-stu-id="7add4-108">SQLFetchScroll Support for Enhanced Date and Time Features</span></span>  
 <span data-ttu-id="7add4-109">날짜/시간 형식의 결과 열 값은 [SQL에서 C로 변환](../native-client-odbc-date-time/datetime-data-type-conversions-from-sql-to-c.md)에 설명 된 대로 변환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7add4-109">Result column values of date/time types are converted as described in [Conversions from SQL to C](../native-client-odbc-date-time/datetime-data-type-conversions-from-sql-to-c.md).</span></span>  
  
 <span data-ttu-id="7add4-110">자세한 내용은 [ODBC&#41;&#40;날짜 및 시간 향상 ](../native-client-odbc-date-time/date-and-time-improvements-odbc.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="7add4-110">For more information, see [Date and Time Improvements &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).</span></span>  
  
## <a name="sqlfetchscroll-support-for-large-clr-udts"></a><span data-ttu-id="7add4-111">큰 CLR UDT에 대한 SQLFetchScroll 지원</span><span class="sxs-lookup"><span data-stu-id="7add4-111">SQLFetchScroll Support for Large CLR UDTs</span></span>  
 <span data-ttu-id="7add4-112">**Sqlfetchscroll** 은 많은 CLR udt (사용자 정의 형식)를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="7add4-112">**SQLFetchScroll** supports large CLR user-defined types (UDTs).</span></span> <span data-ttu-id="7add4-113">자세한 내용은 [ODBC&#41;&#40;LARGE CLR 사용자 정의 형식 ](../native-client/odbc/large-clr-user-defined-types-odbc.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="7add4-113">For more information, see [Large CLR User-Defined Types &#40;ODBC&#41;](../native-client/odbc/large-clr-user-defined-types-odbc.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7add4-114">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7add4-114">See Also</span></span>  
 <span data-ttu-id="7add4-115">[SQLFetchScroll 함수](https://go.microsoft.com/fwlink/?LinkId=59343) </span><span class="sxs-lookup"><span data-stu-id="7add4-115">[SQLFetchScroll Function](https://go.microsoft.com/fwlink/?LinkId=59343) </span></span>  
 [<span data-ttu-id="7add4-116">ODBC API 구현 정보</span><span class="sxs-lookup"><span data-stu-id="7add4-116">ODBC API Implementation Details</span></span>](odbc-api-implementation-details.md)  
  
  
