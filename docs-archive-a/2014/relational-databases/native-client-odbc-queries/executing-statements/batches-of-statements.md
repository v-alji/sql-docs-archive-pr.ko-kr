---
title: 문 일괄 처리 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- statements [ODBC], batches
- batches [ODBC]
- ODBC applications, statements
- multiple statements, batches
- SQLMoreResults function
- SQLExecDirect function
ms.assetid: 057d7c1c-1428-4780-9447-a002ea741188
author: rothja
ms.author: jroth
ms.openlocfilehash: 4818b67766dafe851035041c8fd5137a0dfade73
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646411"
---
# <a name="batches-of-statements"></a><span data-ttu-id="e4395-102">문의 일괄 처리</span><span class="sxs-lookup"><span data-stu-id="e4395-102">Batches of Statements</span></span>
  <span data-ttu-id="e4395-103">문 일괄 처리에는 두 개 이상의 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 문이 포함 되어 있습니다. 세미콜론 (;)은 **Sqlexecdirect** 또는 [sqlprepare 함수](https://go.microsoft.com/fwlink/?LinkId=59360)에 전달 된 단일 문자열로 기본 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e4395-103">A batch of [!INCLUDE[tsql](../../../includes/tsql-md.md)] statements contains two or more statements, separated by a semicolon (;), built into a single string passed to **SQLExecDirect** or [SQLPrepare Function](https://go.microsoft.com/fwlink/?LinkId=59360).</span></span> <span data-ttu-id="e4395-104">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="e4395-104">For example:</span></span>  
  
```  
SQLExecDirect(hstmt,   
    "SELECT * FROM Authors; SELECT * FROM Titles",  
    SQL_NTS);  
```  
  
 <span data-ttu-id="e4395-105">일괄 처리를 사용하면 대개 네트워크 트래픽이 줄어들므로 문을 개별적으로 전송하는 것보다 효율적일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4395-105">Batches can be more efficient than submitting statements separately because network traffic is often reduced.</span></span> <span data-ttu-id="e4395-106">[SQLMoreResults](../../native-client-odbc-api/sqlmoreresults.md) 를 사용 하 여 현재 결과 집합을 마치면 다음 결과 집합에 배치 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4395-106">Use [SQLMoreResults](../../native-client-odbc-api/sqlmoreresults.md) to get positioned on the next result set when finished with the current result set.</span></span>  
  
 <span data-ttu-id="e4395-107">ODBC 커서 특성을 행 집합 크기가 1인 정방향 전용의 읽기 전용 커서(기본값)로 설정하면 항상 일괄 처리를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4395-107">Batches can always be used when the ODBC cursor attributes are set to the defaults of a forward-only, read-only cursor with a rowset size of 1.</span></span>  
  
 <span data-ttu-id="e4395-108">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에 대해 서버 커서를 사용할 때 일괄 처리를 실행하면 서버 커서가 암시적으로 기본 결과 집합으로 변환됩니다.</span><span class="sxs-lookup"><span data-stu-id="e4395-108">If a batch is executed when using server cursors against [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], the server cursor is implicitly converted to a default result set.</span></span> <span data-ttu-id="e4395-109">**Sqlexecdirect** 또는 **sqlexecute** 반환 SQL_SUCCESS_WITH_INFO, **SQLGetDiagRec** 에 대 한 호출은 다음을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4395-109">**SQLExecDirect** or **SQLExecute** return SQL_SUCCESS_WITH_INFO, and a call to **SQLGetDiagRec** returns:</span></span>  
  
```  
szSqlState = "01S02", pfNativeError = 0  
szErrorMsg = "[Microsoft][SQL Server Native Server Native Client]Cursor type changed."  
```  
  
## <a name="see-also"></a><span data-ttu-id="e4395-110">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e4395-110">See Also</span></span>  
 [<span data-ttu-id="e4395-111">ODBC&#41;&#40;문을 실행 하는 중</span><span class="sxs-lookup"><span data-stu-id="e4395-111">Executing Statements &#40;ODBC&#41;</span></span>](executing-statements-odbc.md)  
  
  
