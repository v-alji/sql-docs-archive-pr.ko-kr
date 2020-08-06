---
title: 위치 지정 업데이트 (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, cursors
- SQLSetPos function
- SQLSetCursorName function
- ODBC applications, cursors
- cursors [ODBC], positioned updates
- positioned updates [ODBC]
- ODBC cursors, positioned updates
ms.assetid: ff404e02-630f-474d-b5d4-06442b756991
author: rothja
ms.author: jroth
ms.openlocfilehash: 20272014e32632117e6282e5929d1d21789852df
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649059"
---
# <a name="positioned-updates-odbc"></a><span data-ttu-id="e6eb9-102">위치 지정 업데이트(ODBC)</span><span class="sxs-lookup"><span data-stu-id="e6eb9-102">Positioned Updates (ODBC)</span></span>
  <span data-ttu-id="e6eb9-103">ODBC는 커서에서 위치 지정 업데이트를 수행하는 두 가지 방법을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="e6eb9-103">ODBC supports two methods for performing positioned updates in a cursor:</span></span>  
  
-   <span data-ttu-id="e6eb9-104">**SQLSetPos**</span><span class="sxs-lookup"><span data-stu-id="e6eb9-104">**SQLSetPos**</span></span>  
  
-   <span data-ttu-id="e6eb9-105">WHERE CURRENT OF 절</span><span class="sxs-lookup"><span data-stu-id="e6eb9-105">WHERE CURRENT OF clause</span></span>  
  
 <span data-ttu-id="e6eb9-106">가장 일반적인 방법은 **SQLSetPos**를 사용 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="e6eb9-106">The more common approach is to use **SQLSetPos**.</span></span> <span data-ttu-id="e6eb9-107">여기에는 다음 옵션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6eb9-107">It has the following options.</span></span>  
  
 <span data-ttu-id="e6eb9-108">SQL_POSITION</span><span class="sxs-lookup"><span data-stu-id="e6eb9-108">SQL_POSITION</span></span>  
 <span data-ttu-id="e6eb9-109">커서를 현재 행 집합의 특정 행에 위치시킵니다.</span><span class="sxs-lookup"><span data-stu-id="e6eb9-109">Positions the cursor on a specific row in the current rowset.</span></span>  
  
 <span data-ttu-id="e6eb9-110">SQL_REFRESH</span><span class="sxs-lookup"><span data-stu-id="e6eb9-110">SQL_REFRESH</span></span>  
 <span data-ttu-id="e6eb9-111">커서가 현재 위치한 행으로부터 가져온 값을 갖는 결과 집합 열에 바인딩된 프로그램 변수를 새로 고칩니다.</span><span class="sxs-lookup"><span data-stu-id="e6eb9-111">Refreshes program variables bound to the result set columns with the values from the row the cursor is currently positioned on.</span></span>  
  
 <span data-ttu-id="e6eb9-112">SQL_UPDATE</span><span class="sxs-lookup"><span data-stu-id="e6eb9-112">SQL_UPDATE</span></span>  
 <span data-ttu-id="e6eb9-113">결과 집합 열에 바인딩된 프로그램 변수에 저장된 값으로 커서의 현재 행을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="e6eb9-113">Updates the current row in the cursor with the values stored in the program variables bound to the result set columns.</span></span>  
  
 <span data-ttu-id="e6eb9-114">SQL_DELETE</span><span class="sxs-lookup"><span data-stu-id="e6eb9-114">SQL_DELETE</span></span>  
 <span data-ttu-id="e6eb9-115">커서에서 현재 행을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="e6eb9-115">Deletes the current row in the cursor.</span></span>  
  
 <span data-ttu-id="e6eb9-116">서버 커서를 사용 하도록 문 핸들 커서 특성을 설정 하면 **SQLSetPos** 를 모든 문 결과 집합과 함께 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6eb9-116">**SQLSetPos** can be used with any statement result set when the statement handle cursor attributes are set to use server cursors.</span></span> <span data-ttu-id="e6eb9-117">결과 집합 열은 프로그램 변수에 바인딩되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6eb9-117">The result set columns must be bound to program variables.</span></span> <span data-ttu-id="e6eb9-118">응용 프로그램이 행을 인출 하는 즉시 **SQLSetPos**(SQL_POSTION)를 호출 하 여 커서를 행에 배치 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6eb9-118">As soon as the application has fetched a row it calls **SQLSetPos**(SQL_POSTION) to position the cursor on the row.</span></span> <span data-ttu-id="e6eb9-119">그런 다음 SQLSetPos(SQL_DELETE)를 호출하여 현재 행을 삭제하거나, 새 데이터 값을 바인딩된 프로그램 변수로 이동하고 SQLSetPos(SQL_UPDATE)를 호출하여 현재 행을 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6eb9-119">The application could then call SQLSetPos(SQL_DELETE) to delete the current row, or it can move new data values into the bound program variables and call SQLSetPos(SQL_UPDATE) to update the current row.</span></span>  
  
 <span data-ttu-id="e6eb9-120">응용 프로그램은 **SQLSetPos**를 사용 하 여 행 집합의 모든 행을 업데이트 하거나 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6eb9-120">Applications can update or delete any row in the rowset with **SQLSetPos**.</span></span> <span data-ttu-id="e6eb9-121">**SQLSetPos** 호출은 SQL 문을 생성 하 고 실행 하는 편리한 대안입니다.</span><span class="sxs-lookup"><span data-stu-id="e6eb9-121">Calling **SQLSetPos** is a convenient alternative to constructing and executing an SQL statement.</span></span> <span data-ttu-id="e6eb9-122">**SQLSetPos** 는 현재 행 집합에서 작동 하며 [sqlfetchscroll](../native-client-odbc-api/sqlfetchscroll.md)을 호출한 후에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6eb9-122">**SQLSetPos** operates on the current rowset and can be used only after a call to [SQLFetchScroll](../native-client-odbc-api/sqlfetchscroll.md).</span></span>  
  
 <span data-ttu-id="e6eb9-123">행 집합 크기는 SQL_ATTR_ROW_ARRAY_SIZE 특성 인수를 사용 하 여 [SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md) 에 대 한 호출로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e6eb9-123">Rowset size is set by a call to [SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md) with an attribute argument of SQL_ATTR_ROW_ARRAY_SIZE.</span></span> <span data-ttu-id="e6eb9-124">**SQLSetPos** 는 **Sqlfetch** 또는 **sqlfetchscroll**을 호출한 후에만 새 행 집합 크기를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6eb9-124">**SQLSetPos** uses a new rowset size, but only after a call to **SQLFetch** or **SQLFetchScroll**.</span></span> <span data-ttu-id="e6eb9-125">예를 들어 행 집합 크기가 변경 되 면 **SQLSetPos** 를 호출한 다음 **Sqlfetch** 또는 **sqlfetchscroll** 을 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6eb9-125">For example, if the rowset size is changed, **SQLSetPos** is called and then **SQLFetch** or **SQLFetchScroll** is called.</span></span> <span data-ttu-id="e6eb9-126">**SQLSetPos** 를 호출 하면 이전 행 집합 크기가 사용 되지만 **Sqlfetch** 또는 **sqlfetchscroll** 은 새 행 집합 크기를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6eb9-126">The call to **SQLSetPos** uses the old rowset size, but **SQLFetch** or **SQLFetchScroll** uses the new rowset size.</span></span>  
  
 <span data-ttu-id="e6eb9-127">행 집합의 첫 번째 행 번호는 1입니다.</span><span class="sxs-lookup"><span data-stu-id="e6eb9-127">The first row in the rowset is row number 1.</span></span> <span data-ttu-id="e6eb9-128">**SQLSetPos** 의 RowNumber 인수는 행 집합에서 행을 식별 해야 합니다. 즉, 해당 값은 1에서 가장 최근에 인출 된 행 수 사이의 범위에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6eb9-128">The RowNumber argument in **SQLSetPos** must identify a row in the rowset; that is, its value must be in the range between 1 and the number of rows that were most recently fetched.</span></span> <span data-ttu-id="e6eb9-129">이 값은 행 집합 크기보다 작을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6eb9-129">This may be less than the rowset size.</span></span> <span data-ttu-id="e6eb9-130">RowNumber가 0이면 행 집합의 모든 행에 작업이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="e6eb9-130">If RowNumber is 0, the operation applies to every row in the rowset.</span></span>  
  
 <span data-ttu-id="e6eb9-131">**SQLSetPos** 의 삭제 작업은 데이터 원본에서 하나 이상의 선택 된 테이블 행을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6eb9-131">The delete operation of **SQLSetPos** makes the data source delete one or more selected rows of a table.</span></span> <span data-ttu-id="e6eb9-132">**Sqlsetpos**를 사용 하 여 행을 삭제 하기 위해 응용 프로그램은 작업을 SQL_DELETE로 설정 하 고 RowNumber를 삭제할 행 번호로 설정 하 여 **SQLSetPos** 를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6eb9-132">To delete rows with **SQLSetPos**, the application calls **SQLSetPos** with Operation set to SQL_DELETE and RowNumber set to the number of the row to delete.</span></span> <span data-ttu-id="e6eb9-133">RowNumber가 0이면 행 집합의 모든 행이 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="e6eb9-133">If RowNumber is 0, all rows in the rowset are deleted.</span></span>  
  
 <span data-ttu-id="e6eb9-134">**SQLSetPos** 가 반환 된 후 삭제 된 행은 현재 행 이며 상태는 SQL_ROW_DELETED입니다.</span><span class="sxs-lookup"><span data-stu-id="e6eb9-134">After **SQLSetPos** returns, the deleted row is the current row and its status is SQL_ROW_DELETED.</span></span> <span data-ttu-id="e6eb9-135">[SQLGetData](../native-client-odbc-api/sqlgetdata.md) 또는 **SQLSetPos**호출과 같은 추가 위치 지정 작업에는 행을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e6eb9-135">The row cannot be used in any additional positioned operations, such as calls to [SQLGetData](../native-client-odbc-api/sqlgetdata.md) or **SQLSetPos**.</span></span>  
  
 <span data-ttu-id="e6eb9-136">행 집합의 모든 행을 삭제 하는 경우 (RowNumber가 0 인 경우) 응용 프로그램은 **SQLSetPos**의 업데이트 작업과 마찬가지로 행 작업 배열을 사용 하 여 드라이버가 특정 행을 삭제 하지 못하도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6eb9-136">When you delete all rows of the rowset (RowNumber is equal to 0), the application can prevent the driver from deleting certain rows by using the row operation array just like for the update operation of **SQLSetPos**.</span></span>  
  
 <span data-ttu-id="e6eb9-137">삭제되는 모든 행은 결과 집합에 있는 행이여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6eb9-137">Every row that is deleted should be a row that exists in the result set.</span></span> <span data-ttu-id="e6eb9-138">인출로 인해 애플리케이션 버퍼가 가득 차고 행 상태 배열이 유지되는 경우 이러한 각각의 행 위치에서 값은 SQL_ROW_DELETED, SQL_ROW_ERROR 또는 SQL_ROW_NOROW일 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e6eb9-138">If the application buffers were filled by fetching, and if a row status array has been maintained, its values at each of these row positions should not be SQL_ROW_DELETED, SQL_ROW_ERROR, or SQL_ROW_NOROW.</span></span>  
  
 <span data-ttu-id="e6eb9-139">위치 지정 업데이트는 UPDATE, DELETE 및 INSERT 문에 WHERE CURRENT OF 절을 사용하여 수행할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6eb9-139">Positioned updates can also be performed using the WHERE CURRENT OF clause on UPDATE, DELETE, and INSERT statements.</span></span> <span data-ttu-id="e6eb9-140">여기서 CURRENT를 사용 하려면 [SQLGetCursorName](../native-client-odbc-api/sqlgetcursorname.md) 함수를 호출 하거나 **SQLSetCursorName**를 호출 하 여 지정할 수 있는 커서 이름이 ODBC에서 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e6eb9-140">WHERE CURRENT OF requires a cursor name that ODBC will generate when the [SQLGetCursorName](../native-client-odbc-api/sqlgetcursorname.md) function is called, or which you can specify by calling **SQLSetCursorName**.</span></span> <span data-ttu-id="e6eb9-141">다음은 ODBC 애플리케이션에서 WHERE CURRENT OF 업데이트를 수행하는 일반적인 단계입니다.</span><span class="sxs-lookup"><span data-stu-id="e6eb9-141">The following are general steps used to perform a WHERE CURRENT OF update in an ODBC application:</span></span>  
  
-   <span data-ttu-id="e6eb9-142">**SQLSetCursorName** 를 호출 하 여 문 핸들에 대 한 커서 이름을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6eb9-142">Call **SQLSetCursorName** to establish a cursor name for the statement handle.</span></span>  
  
-   <span data-ttu-id="e6eb9-143">FOR UPDATE OF 절을 사용하여 SELECT 문을 작성하고 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="e6eb9-143">Build a SELECT statement with a FOR UPDATE OF clause and execute it.</span></span>  
  
-   <span data-ttu-id="e6eb9-144">**Sqlfetchscroll** 을 호출 하 여 행 집합 또는 **sqlfetch** 를 검색 하 여 행을 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6eb9-144">Call **SQLFetchScroll** to retrieve a rowset or **SQLFetch** to retrieve a row.</span></span>  
  
-   <span data-ttu-id="e6eb9-145">**SQLSetPos** (SQL_POSITION)를 호출 하 여 커서를 행에 배치 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6eb9-145">Call **SQLSetPos** (SQL_POSITION) to position the cursor on the row.</span></span>  
  
-   <span data-ttu-id="e6eb9-146">**SQLSetCursorName**로 설정 된 커서 이름을 사용 하 여 WHERE CURRENT OF 절이 있는 UPDATE 문을 빌드하고 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6eb9-146">Build and execute an UPDATE statement with a WHERE CURRENT OF clause using the cursor name set with **SQLSetCursorName**.</span></span>  
  
 <span data-ttu-id="e6eb9-147">또는 SELECT 문을 실행 하기 전에 **SQLSetCursorName** 를 호출 하는 대신 select 문을 실행 한 후에는 **SQLGetCursorName** 를 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6eb9-147">Alternatively, you could call **SQLGetCursorName** after you execute the SELECT statement instead of calling **SQLSetCursorName** before executing the SELECT statement.</span></span> <span data-ttu-id="e6eb9-148">**SQLGetCursorName** 는 **SQLSetCursorName**를 사용 하 여 커서 이름을 설정 하지 않은 경우 ODBC에서 할당 한 기본 커서 이름을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6eb9-148">**SQLGetCursorName** returns a default cursor name assigned by ODBC if you do not set a cursor name using **SQLSetCursorName**.</span></span>  
  
 <span data-ttu-id="e6eb9-149">서버 커서를 사용 하는 경우 현재 위치 보다 **SQLSetPos** 를 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="e6eb9-149">**SQLSetPos** is preferred over WHERE CURRENT OF when you are using server cursors.</span></span> <span data-ttu-id="e6eb9-150">ODBC 커서 라이브러리에 업데이트 가능한 정적 커서를 사용하면 커서 라이브러리가 기본 테이블의 키 값을 통해 WHERE 절을 추가하는 방법으로 WHERE CURRENT OF 업데이트를 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="e6eb9-150">If you are using a static, updatable cursor with the ODBC cursor library, the cursor library implements WHERE CURRENT OF updates by adding a WHERE clause with the key values for the underlying table.</span></span> <span data-ttu-id="e6eb9-151">이 경우 테이블의 키가 고유하지 않으면 불필요한 업데이트가 수행될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6eb9-151">This can cause unintended updates if the keys in the table are not unique.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6eb9-152">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e6eb9-152">See Also</span></span>  
 [<span data-ttu-id="e6eb9-153">ODBC&#41;&#40;커서 사용</span><span class="sxs-lookup"><span data-stu-id="e6eb9-153">Using Cursors &#40;ODBC&#41;</span></span>](using-cursors-odbc.md)  
  
  
