---
title: 행 집합 인출 및 업데이트 (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- rowsets [ODBC]
ms.assetid: cf0eb3b4-8b72-49fc-a845-95edc360cf93
author: rothja
ms.author: jroth
ms.openlocfilehash: e09a3033e0883452ecd69b82c9375ed28c920da0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638741"
---
# <a name="fetch-and-update-rowsets-odbc"></a><span data-ttu-id="8d56e-102">행 집합 인출 및 업데이트(ODBC)</span><span class="sxs-lookup"><span data-stu-id="8d56e-102">Fetch and Update Rowsets (ODBC)</span></span>
    
### <a name="to-fetch-and-update-rowsets"></a><span data-ttu-id="8d56e-103">행 집합을 인출하고 업데이트하려면</span><span class="sxs-lookup"><span data-stu-id="8d56e-103">To fetch and update rowsets</span></span>  
  
1.  <span data-ttu-id="8d56e-104">필요에 따라 SQL_ROW_ARRAY_SIZE를 사용 하 여 [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md) 를 호출 하 여 행 집합의 행 수 (R)를 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d56e-104">Optionally, call [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md) with SQL_ROW_ARRAY_SIZE to change the number of rows (R) in the rowset.</span></span>  
  
2.  <span data-ttu-id="8d56e-105">[SQLFetch](https://go.microsoft.com/fwlink/?LinkId=58401) 또는 [SQLFetchScroll](../../native-client-odbc-api/sqlfetchscroll.md) 을 호출하여 행 집합을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="8d56e-105">Call [SQLFetch](https://go.microsoft.com/fwlink/?LinkId=58401) or [SQLFetchScroll](../../native-client-odbc-api/sqlfetchscroll.md) to get a rowset.</span></span>  
  
3.  <span data-ttu-id="8d56e-106">바인딩된 열이 사용된 경우 행 집합의 바인딩된 열 버퍼에 있는 데이터 값과 데이터 길이를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="8d56e-106">If bound columns are used, use the data values and data lengths now available in the bound column buffers for the rowset.</span></span>  
  
     <span data-ttu-id="8d56e-107">바인딩되지 않은 열이 사용된 경우 각 행에 대해 SQL_POSITION과 함께 [SQLSetPos](https://go.microsoft.com/fwlink/?LinkId=58407) 를 호출하여 커서 위치를 설정한 다음 바인딩되지 않은 각 열에 대해 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="8d56e-107">If unbound columns are used, for each row call [SQLSetPos](https://go.microsoft.com/fwlink/?LinkId=58407) with SQL_POSITION to set the cursor position; then, for each unbound column:</span></span>  
  
    -   <span data-ttu-id="8d56e-108">[SQLGetData](../../native-client-odbc-api/sqlgetdata.md) 를 한 번 이상 호출하여 행 집합의 바인딩된 마지막 열 이후의 바인딩되지 않은 열 데이터를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="8d56e-108">Call [SQLGetData](../../native-client-odbc-api/sqlgetdata.md) one or more times to get the data for unbound columns after the last bound column of the rowset.</span></span> <span data-ttu-id="8d56e-109">[SQLGetData](../../native-client-odbc-api/sqlgetdata.md) 는 번호가 가장 작은 열부터 차례로 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d56e-109">Calls to [SQLGetData](../../native-client-odbc-api/sqlgetdata.md) should be in order of increasing column number.</span></span>  
  
    -   <span data-ttu-id="8d56e-110">[SQLGetData](../../native-client-odbc-api/sqlgetdata.md) 를 여러 번 호출하여 텍스트나 이미지 열에서 데이터를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="8d56e-110">Call [SQLGetData](../../native-client-odbc-api/sqlgetdata.md) multiple times to get data from a text or image column.</span></span>  
  
4.  <span data-ttu-id="8d56e-111">실행 시 데이터 텍스트 또는 이미지 열을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8d56e-111">Set up any data-at-execution text or image columns.</span></span>  
  
5.  <span data-ttu-id="8d56e-112">[SQLSetPos](https://go.microsoft.com/fwlink/?LinkId=58407) 또는 [SQLBulkOperations](https://go.microsoft.com/fwlink/?LinkId=58398) 를 호출하여 행 집합 내에서 커서 위치를 설정하거나 행을 새로 고침, 업데이트, 삭제 또는 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="8d56e-112">Call [SQLSetPos](https://go.microsoft.com/fwlink/?LinkId=58407) or [SQLBulkOperations](https://go.microsoft.com/fwlink/?LinkId=58398) to set the cursor position, refresh, update, delete, or add row(s) within the rowset.</span></span>  
  
     <span data-ttu-id="8d56e-113">업데이트 또는 추가 작업에 실행 시 데이터 텍스트 또는 이미지 열이 사용된 경우 해당 열을 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="8d56e-113">If data-at-execution text or image columns are used for an update or add operation, handle them.</span></span>  
  
6.  <span data-ttu-id="8d56e-114">필요한 경우 커서 이름( [SQLGetCursorName](../../native-client-odbc-api/sqlgetcursorname.md)에서 사용 가능)을 지정하고 같은 연결에서 다른 문 핸들을 사용하여 지정된 UPDATE 문이나 DELETE 문을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="8d56e-114">Optionally, execute a positioned UPDATE or DELETE statement, specifying the cursor name (available from [SQLGetCursorName](../../native-client-odbc-api/sqlgetcursorname.md)) and using a different statement handle on the same connection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d56e-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8d56e-115">See Also</span></span>  
 [<span data-ttu-id="8d56e-116">커서 사용 방법 항목 ODBC&#41;&#40;</span><span class="sxs-lookup"><span data-stu-id="8d56e-116">Using Cursors How-to Topics &#40;ODBC&#41;</span></span>](using-cursors-how-to-topics-odbc.md)  
  
  
