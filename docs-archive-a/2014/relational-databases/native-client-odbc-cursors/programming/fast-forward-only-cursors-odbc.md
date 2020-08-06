---
title: 빠른 전진 전용 커서 (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- fast forward-only cursors
- forward-only cursors
- cursors [ODBC], fast forward-only
- ODBC cursors, fast forward-only
ms.assetid: 0707d07e-fc95-42ed-9280-b7e508ac8c62
author: rothja
ms.author: jroth
ms.openlocfilehash: de8d82a0c72ad51741a3785fba2910f691028cba
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653344"
---
# <a name="fast-forward-only-cursors-odbc"></a><span data-ttu-id="d8773-102">빠른 정방향 전용 커서(ODBC)</span><span class="sxs-lookup"><span data-stu-id="d8773-102">Fast Forward-Only Cursors (ODBC)</span></span>
  <span data-ttu-id="d8773-103">의 인스턴스에 연결 된 경우 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] NATIVE Client ODBC 드라이버는 앞 으로만 이동 가능한 읽기 전용 커서에 대해 성능 최적화를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="d8773-103">When connected to an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver supports performance optimizations for forward-only, read-only cursors.</span></span> <span data-ttu-id="d8773-104">빠른 정방향 전용 커서는 기본 결과 집합과 매우 유사한 방식으로 드라이버 및 서버에서 내부적으로 구현됩니다.</span><span class="sxs-lookup"><span data-stu-id="d8773-104">Fast forward-only cursors are implemented internally by the driver and server in a manner very similar to default result sets.</span></span> <span data-ttu-id="d8773-105">정방향 전용 커서는 높은 성능 외에도 다음과 같은 특성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d8773-105">Besides having high performance, fast forward-only cursors also have these characteristics:</span></span>  
  
-   <span data-ttu-id="d8773-106">[SQLGetData](../../native-client-odbc-api/sqlgetdata.md) 는 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d8773-106">[SQLGetData](../../native-client-odbc-api/sqlgetdata.md) is not supported.</span></span> <span data-ttu-id="d8773-107">결과 집합 열은 프로그램 변수에 바인딩되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d8773-107">The result set columns must be bound to program variables.</span></span>  
  
-   <span data-ttu-id="d8773-108">서버에서 커서 끝을 감지하면 커서를 자동으로 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="d8773-108">The server automatically closes the cursor when the end of the cursor is detected.</span></span> <span data-ttu-id="d8773-109">응용 프로그램에서 [SQLCloseCursor](../../native-client-odbc-api/sqlclosecursor.md) 또는 [SQLFreeStmt](../../native-client-odbc-api/sqlfreestmt.md)(SQL_CLOSE)를 호출 해야 하지만 드라이버에서 CLOSE 요청을 서버로 보낼 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d8773-109">The application must still call [SQLCloseCursor](../../native-client-odbc-api/sqlclosecursor.md) or [SQLFreeStmt](../../native-client-odbc-api/sqlfreestmt.md)(SQL_CLOSE), but the driver does not have to send the close request to the server.</span></span> <span data-ttu-id="d8773-110">따라서 서버로의 네트워크 왕복이 줄어듭니다.</span><span class="sxs-lookup"><span data-stu-id="d8773-110">This saves a roundtrip across the network to the server.</span></span>  
  
 <span data-ttu-id="d8773-111">애플리케이션에서는 각 드라이버에 맞는 문 특성 SQL_SOPT_SS_CURSOR_OPTIONS를 사용하여 빠른 정방향 전용 커서를 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="d8773-111">The application requests fast forward-only cursors using the driver-specific statement attribute SQL_SOPT_SS_CURSOR_OPTIONS.</span></span> <span data-ttu-id="d8773-112">SQL_CO_FFO로 설정하면 자동 인출 없이 빠른 정방향 전용 커서를 활성화합니다.</span><span class="sxs-lookup"><span data-stu-id="d8773-112">When set to SQL_CO_FFO, fast forward-only cursors are enabled without autofetch.</span></span> <span data-ttu-id="d8773-113">SQL_CO_FFO_AF로 설정하면 자동 인출 옵션도 활성화됩니다.</span><span class="sxs-lookup"><span data-stu-id="d8773-113">When set to SQL_CO_FFO_AF, the autofetch option is also enabled.</span></span> <span data-ttu-id="d8773-114">자동 인출에 대 한 자세한 내용은 [ODBC 커서로 자동 인출 사용](using-autofetch-with-odbc-cursors.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d8773-114">For more information about autofetch, see [Using Autofetch with ODBC Cursors](using-autofetch-with-odbc-cursors.md).</span></span>  
  
 <span data-ttu-id="d8773-115">자동 인출 기능을 사용하는 빠른 정방향 전용 커서는 서버 왕복을 하나만 포함하는 작은 결과 집합을 검색하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d8773-115">Fast forward-only cursors with autofetch can be used to retrieve a small result set with only one roundtrip to the server.</span></span> <span data-ttu-id="d8773-116">이러한 단계에서 *n* 은 반환 되는 행의 수입니다.</span><span class="sxs-lookup"><span data-stu-id="d8773-116">In these steps, *n* is the number of rows to be returned:</span></span>  
  
1.  <span data-ttu-id="d8773-117">SQL_SOPT_SS_CURSOR_OPTIONS를 SQL_CO_FFO_AF로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="d8773-117">Set SQL_SOPT_SS_CURSOR_OPTIONS to SQL_CO_FFO_AF.</span></span>  
  
2.  <span data-ttu-id="d8773-118">SQL_ATTR_ROW_ARRAY_SIZE를 *n* + 1로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d8773-118">Set SQL_ATTR_ROW_ARRAY_SIZE to *n* + 1.</span></span>  
  
3.  <span data-ttu-id="d8773-119">N 개 이상의 행이 실제로 인출 *되 면 안전* 하 게 하기 위해 *n* + 1 개 요소의 배열에 결과 열을 바인딩합니다.</span><span class="sxs-lookup"><span data-stu-id="d8773-119">Bind the result columns to arrays of *n* + 1 elements (to be safe if *n* + 1 rows are actually fetched).</span></span>  
  
4.  <span data-ttu-id="d8773-120">**Sqlexecdirect** 또는 **sqlexecute**를 사용 하 여 커서를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="d8773-120">Open the cursor with either **SQLExecDirect** or **SQLExecute**.</span></span>  
  
5.  <span data-ttu-id="d8773-121">반환 상태가 SQL_SUCCESS 인 경우 **SQLFreeStmt** 또는 **SQLCloseCursor** 를 호출 하 여 커서를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="d8773-121">If the return status is SQL_SUCCESS, then call **SQLFreeStmt** or **SQLCloseCursor** to close the cursor.</span></span> <span data-ttu-id="d8773-122">행의 모든 데이터가 바인딩된 프로그램 변수에 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="d8773-122">All data for the rows will be in the bound program variables.</span></span>  
  
 <span data-ttu-id="d8773-123">이러한 단계에서 **Sqlexecdirect** 또는 **sqlexecute** 는 자동 인출 옵션을 사용 하 여 커서 열기 요청을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="d8773-123">With these steps, the **SQLExecDirect** or **SQLExecute** sends a cursor open request with the autofetch option enabled.</span></span> <span data-ttu-id="d8773-124">클라이언트의 해당 단일 요청에 대해 서버는 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="d8773-124">On that single request from the client, the server:</span></span>  
  
-   <span data-ttu-id="d8773-125">커서를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="d8773-125">Opens the cursor.</span></span>  
  
-   <span data-ttu-id="d8773-126">결과 집합을 작성하고 행을 클라이언트에 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="d8773-126">Builds the result set and sends the rows to the client.</span></span>  
  
-   <span data-ttu-id="d8773-127">행 집합 크기를 결과 집합의 행 수보다 1개 많은 수로 설정했으므로 서버가 커서의 끝을 발견하고 커서를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="d8773-127">Because the rowset size was set to 1 more than the number of rows in the result set, the server detects the end of the cursor and closes the cursor.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8773-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d8773-128">See Also</span></span>  
 [<span data-ttu-id="d8773-129">ODBC&#41;&#40;커서 프로그래밍 정보</span><span class="sxs-lookup"><span data-stu-id="d8773-129">Cursor Programming Details &#40;ODBC&#41;</span></span>](cursor-programming-details-odbc.md)  
  
  
