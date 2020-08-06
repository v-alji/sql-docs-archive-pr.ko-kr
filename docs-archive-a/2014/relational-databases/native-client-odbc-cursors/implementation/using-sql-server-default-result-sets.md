---
title: SQL Server 기본 결과 집합 사용 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQLSetStmtAttr function
- ODBC cursors, default result sets
- cursors [ODBC], default result sets
- default result sets
- result sets [ODBC], default
- ODBC applications, cursors
ms.assetid: ee1db3e5-60eb-4425-8a6b-977eeced3f98
author: rothja
ms.author: jroth
ms.openlocfilehash: 18cd10dd95329f68a42497d2bea5ce63f345ceff
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649060"
---
# <a name="using-sql-server-default-result-sets"></a><span data-ttu-id="fa5a5-102">SQL Server 기본 결과 집합 사용</span><span class="sxs-lookup"><span data-stu-id="fa5a5-102">Using SQL Server Default Result Sets</span></span>
  <span data-ttu-id="fa5a5-103">기본 ODBC 커서 특성은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="fa5a5-103">The default ODBC cursor attributes are:</span></span>  
  
```  
SQLSetStmtAttr(hstmt, SQL_ATTR_CURSOR_TYPE, SQL_CURSOR_FORWARD_ONLY, SQL_IS_INTEGER);  
SQLSetStmtAttr(hstmt, SQL_ATTR_CONCURRENCY, SQL_CONCUR_READ_ONLY, SQL_IS_INTEGER);  
SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_ARRAY_SIZE, 1, SQL_IS_INTEGER);  
```  
  
 <span data-ttu-id="fa5a5-104">이러한 특성이 기본값으로 설정 된 경우 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native CLIENT ODBC 드라이버는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 기본 결과 집합을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa5a5-104">Whenever these attributes are set to their defaults, the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver uses a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] default result set.</span></span> <span data-ttu-id="fa5a5-105">기본 결과 집합은 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]가 지원하는 모든 SQL 문에서 사용할 수 있으며 클라이언트에 전체 결과 집합을 전송하는 가장 효율적인 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="fa5a5-105">Default result sets can be used for any SQL statement supported by [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], and are the most efficient method of transferring an entire result set to the client.</span></span>  
  
 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]<span data-ttu-id="fa5a5-106">MARS (multiple active result sets)를 지원 합니다. 이제 응용 프로그램에는 연결당 활성 기본 결과 집합이 둘 이상 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa5a5-106">introduced support for multiple active result sets (MARS); applications can now have more than one active default result set per connection.</span></span> <span data-ttu-id="fa5a5-107">MARS 기능은 기본적으로 해제됩니다.</span><span class="sxs-lookup"><span data-stu-id="fa5a5-107">MARS is not enabled by default.</span></span>  
  
 <span data-ttu-id="fa5a5-108">[!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 이전에는 기본 결과 집합이 동일한 연결에서 다중 활성 문을 지원하지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="fa5a5-108">Before [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], default result sets did not support multiple active statements on the same connection.</span></span> <span data-ttu-id="fa5a5-109">따라서 연결에서 SQL 문을 실행한 후 결과 집합의 모든 행이 처리될 때까지 서버가 클라이언트에서 나머지 결과 집합을 취소하는 요청을 제외한 다른 명령을 받지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="fa5a5-109">After an SQL statement is executed on a connection, the server does not accept commands (except a request to cancel the rest of the result set) from the client on that connection until all the rows in the result set have been processed.</span></span> <span data-ttu-id="fa5a5-110">부분적으로 처리 된 결과 집합의 나머지를 취소 하려면 *Foption* 매개 변수를 SQL_CLOSE로 설정 하 여 [SQLCloseCursor](../../native-client-odbc-api/sqlclosecursor.md) 또는 [SQLFreeStmt](../../native-client-odbc-api/sqlfreestmt.md) 를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa5a5-110">To cancel the remainder of a partially processed result set, call [SQLCloseCursor](../../native-client-odbc-api/sqlclosecursor.md) or [SQLFreeStmt](../../native-client-odbc-api/sqlfreestmt.md) with the *fOption* parameter set to SQL_CLOSE.</span></span> <span data-ttu-id="fa5a5-111">부분적으로 처리 된 결과 집합을 완료 하 고 다른 결과 집합이 있는지 테스트 하려면 [SQLMoreResults](../../native-client-odbc-api/sqlmoreresults.md)를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa5a5-111">To finish a partially processed result set and test for the presence of another result set, call [SQLMoreResults](../../native-client-odbc-api/sqlmoreresults.md).</span></span> <span data-ttu-id="fa5a5-112">기본 결과 집합이 완전히 처리 되기 전에 ODBC 응용 프로그램에서 연결 핸들에 대해 명령을 시도 하는 경우 호출은 SQL_ERROR를 생성 하 고 **SQLGetDiagRec** 에 대 한 호출은 다음을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa5a5-112">If an ODBC application attempts a command on a connection handle before a default result set has been completely processed, the call generates SQL_ERROR and a call to **SQLGetDiagRec** returns:</span></span>  
  
```  
szSqlState: "HY000", pfNativeError: 0  
szErrorMsg: "[Microsoft][SQL Server Native Client]  
                Connection is busy with results for another hstmt."  
```  
  
## <a name="see-also"></a><span data-ttu-id="fa5a5-113">참고 항목</span><span class="sxs-lookup"><span data-stu-id="fa5a5-113">See Also</span></span>  
 [<span data-ttu-id="fa5a5-114">커서 구현 방법</span><span class="sxs-lookup"><span data-stu-id="fa5a5-114">How Cursors Are Implemented</span></span>](how-cursors-are-implemented.md)  
  
  
