---
title: 커서 행 집합 크기 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- cursors [ODBC], rowset size
- ODBC cursors, rowset size
- rowsets [ODBC]
ms.assetid: 2febe2ae-fdc1-490e-a79f-c516bc8e7c3f
author: rothja
ms.author: jroth
ms.openlocfilehash: 83c4e55025e6e3724f354f022760b7ba1e2f10e1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653331"
---
# <a name="cursor-rowset-size"></a><span data-ttu-id="b8457-102">커서 행 집합 크기</span><span class="sxs-lookup"><span data-stu-id="b8457-102">Cursor Rowset Size</span></span>
  <span data-ttu-id="b8457-103">ODBC 커서는 한 번에 한 행씩만 인출하도록 제한되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b8457-103">ODBC cursors are not limited to fetching one row at a time.</span></span> <span data-ttu-id="b8457-104">**Sqlfetch** 또는 [sqlfetchscroll](../../native-client-odbc-api/sqlfetchscroll.md)에 대 한 각 호출에서 여러 행을 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b8457-104">They can retrieve multiple rows in each call to **SQLFetch** or [SQLFetchScroll](../../native-client-odbc-api/sqlfetchscroll.md).</span></span> <span data-ttu-id="b8457-105">Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]와 같은 클라이언트/서버 데이터베이스 작업을 할 때는 한 번에 여러 행을 인출하는 것이 효율적입니다.</span><span class="sxs-lookup"><span data-stu-id="b8457-105">When you are working with a client/server database such as Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], it is more efficient to fetch several rows at a time.</span></span> <span data-ttu-id="b8457-106">인출 시 반환 되는 행 수는 행 집합 크기 라고 하며 [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md)의 SQL_ATTR_ROW_ARRAY_SIZE을 사용 하 여 지정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b8457-106">The number of rows returned on a fetch is called the rowset size and is specified by using the SQL_ATTR_ROW_ARRAY_SIZE of [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md).</span></span>  
  
```  
SQLUINTEGER uwRowsize;  
SQLSetStmtAttr(m_hstmt, SQL_ATTR_ROW_ARRAY_SIZE, (SQLPOINTER)uwRowsetSize, SQL_IS_UINTEGER);  
```  
  
 <span data-ttu-id="b8457-107">행 집합 크기가 1보다 큰 커서를 블록 커서라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8457-107">Cursors with a rowset size greater than 1 are called block cursors.</span></span>  
  
 <span data-ttu-id="b8457-108">블록 커서를 위해 결과 집합 열을 바인딩하는 다음 두 가지 옵션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b8457-108">There are two options for binding result set columns for block cursors:</span></span>  
  
-   <span data-ttu-id="b8457-109">열 단위 바인딩</span><span class="sxs-lookup"><span data-stu-id="b8457-109">Column-wise binding</span></span>  
  
     <span data-ttu-id="b8457-110">각 열이 변수 배열에 바인딩됩니다.</span><span class="sxs-lookup"><span data-stu-id="b8457-110">Each column is bound to an array of variables.</span></span> <span data-ttu-id="b8457-111">각 배열의 요소 수는 행 집합 크기와 같습니다.</span><span class="sxs-lookup"><span data-stu-id="b8457-111">Each array has the same number of elements as the rowset size.</span></span>  
  
-   <span data-ttu-id="b8457-112">행 단위 바인딩</span><span class="sxs-lookup"><span data-stu-id="b8457-112">Row-wise binding</span></span>  
  
     <span data-ttu-id="b8457-113">행의 모든 열에 대한 데이터와 표시기가 포함된 구조를 사용하여 배열이 작성됩니다.</span><span class="sxs-lookup"><span data-stu-id="b8457-113">An array is built using structures that hold the data and indicators for all the columns in a row.</span></span> <span data-ttu-id="b8457-114">배열의 구조 수는 행 집합 크기와 같습니다.</span><span class="sxs-lookup"><span data-stu-id="b8457-114">The array has the same number of structures as the rowset size.</span></span>  
  
 <span data-ttu-id="b8457-115">열 단위 또는 행 단위 바인딩을 사용할 경우 **Sqlfetch** 또는 **sqlfetchscroll** 을 호출할 때마다 바인딩된 배열이 검색 된 행 집합의 데이터로 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="b8457-115">When either column-wise or row-wise binding is used, each call to **SQLFetch** or **SQLFetchScroll** fills the bound arrays with data from the rowset retrieved.</span></span>  
  
 <span data-ttu-id="b8457-116">[SQLGetData](../../native-client-odbc-api/sqlgetdata.md) 는 블록 커서에서 열 데이터를 검색 하는 데도 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b8457-116">[SQLGetData](../../native-client-odbc-api/sqlgetdata.md) can also be used to retrieve column data from a block cursor.</span></span> <span data-ttu-id="b8457-117">**Sqlgetdata** 는 한 번에 한 행씩 작동 하므로 **sqlgetdata**를 호출 하기 전에 **SQLSetPos** 를 호출 하 여 행 집합의 특정 행을 현재 행으로 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8457-117">Because **SQLGetData** works one row at a time, **SQLSetPos** must be called to set a specific row in the rowset as the current row before calling **SQLGetData**.</span></span>  
  
 <span data-ttu-id="b8457-118">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native CLIENT ODBC 드라이버는 행 집합을 사용 하 여 전체 결과 집합을 신속 하 게 검색 하는 최적화를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8457-118">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver offers an optimization using rowsets to retrieve a whole result set quickly.</span></span> <span data-ttu-id="b8457-119">이 최적화를 사용 하려면 **Sqlexecdirect** 또는 **sqlexecute** 를 호출할 때 커서 특성을 기본값 (앞 으로만 이동, 읽기 전용, 행 집합 크기 = 1)으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8457-119">To use this optimization, set the cursor attributes to their defaults (forward-only, read-only, rowset size = 1) at the time **SQLExecDirect** or **SQLExecute** is called.</span></span> <span data-ttu-id="b8457-120">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native CLIENT ODBC 드라이버는 기본 결과 집합을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8457-120">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver sets up a default result set.</span></span> <span data-ttu-id="b8457-121">스크롤 없이 결과를 클라이언트로 전송하는 경우 이 방법이 서버 커서보다 더 효율적입니다.</span><span class="sxs-lookup"><span data-stu-id="b8457-121">This is more efficient than server cursors when transferring results to the client without scrolling.</span></span> <span data-ttu-id="b8457-122">문이 실행된 후 행 집합 크기를 늘리고 열 단위 또는 행 단위 바인딩을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b8457-122">After the statement has been executed, increase the rowset size and use either column-wise or row-wise binding.</span></span> <span data-ttu-id="b8457-123">이렇게 하면 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 기본 결과 집합을 사용 하 여 클라이언트에 결과 행을 효율적으로 보낼 수 있으며, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] NATIVE client ODBC 드라이버는 계속 해 서 클라이언트의 네트워크 버퍼에서 행을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="b8457-123">This lets [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] use a default result set to send result rows efficiently to the client, while the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver continuously pulls rows from the network buffers on the client.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8457-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b8457-124">See Also</span></span>  
 [<span data-ttu-id="b8457-125">커서 속성</span><span class="sxs-lookup"><span data-stu-id="b8457-125">Cursor Properties</span></span>](cursor-properties.md)  
  
  
