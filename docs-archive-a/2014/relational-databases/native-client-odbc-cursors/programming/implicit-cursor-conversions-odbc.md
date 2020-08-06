---
title: 암시적 커서 변환 (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC cursors, implicit cursor conversions
- implicit cursor conversions
- cursors [ODBC], implicit cursor conversions
ms.assetid: fe29a58d-8448-4512-9ffd-b414784ba338
author: rothja
ms.author: jroth
ms.openlocfilehash: ff8350c71a853e39ff1d35a1f3fba6e8e1944934
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653337"
---
# <a name="implicit-cursor-conversions-odbc"></a><span data-ttu-id="645d4-102">암시적 커서 변환(ODBC)</span><span class="sxs-lookup"><span data-stu-id="645d4-102">Implicit Cursor Conversions (ODBC)</span></span>
  <span data-ttu-id="645d4-103">응용 프로그램은 [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md) 를 통해 커서 유형을 요청한 다음 요청한 유형의 서버 커서에서 지원 되지 않는 SQL 문을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="645d4-103">Applications can request a cursor type through [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md) and then execute an SQL statement that is not supported by server cursors of the type requested.</span></span> <span data-ttu-id="645d4-104">**Sqlexecute** 또는 **sqlexecdirect** 를 호출 하면 SQL_SUCCESS_WITH_INFO 반환 되 고 **SQLGetDiagRec** 에서 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="645d4-104">A call to **SQLExecute** or **SQLExecDirect** returns SQL_SUCCESS_WITH_INFO and **SQLGetDiagRec** returns:</span></span>  
  
```  
szSqlState = "01S02", *pfNativeError = 0,  
szErrorMsg="[Microsoft][SQL Server Native Client] Cursor type changed"  
```  
  
 <span data-ttu-id="645d4-105">응용 프로그램은 SQL_CURSOR_TYPE로 설정 된 **SQLGetStmtOption** 를 호출 하 여 현재 사용 중인 커서 유형을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="645d4-105">The application can determine what type of cursor is now being used by calling **SQLGetStmtOption** set to SQL_CURSOR_TYPE.</span></span> <span data-ttu-id="645d4-106">커서 유형 변환은 하나의 문에만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="645d4-106">The cursor type conversion applies to only one statement.</span></span> <span data-ttu-id="645d4-107">다음 **Sqlexecdirect** 또는 **sqlexecute** 는 원래 문 커서 설정을 사용 하 여 수행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="645d4-107">The next **SQLExecDirect** or **SQLExecute** will be done using the original statement cursor settings.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="645d4-108">참고 항목</span><span class="sxs-lookup"><span data-stu-id="645d4-108">See Also</span></span>  
 [<span data-ttu-id="645d4-109">ODBC&#41;&#40;커서 프로그래밍 정보</span><span class="sxs-lookup"><span data-stu-id="645d4-109">Cursor Programming Details &#40;ODBC&#41;</span></span>](cursor-programming-details-odbc.md)  
  
  
