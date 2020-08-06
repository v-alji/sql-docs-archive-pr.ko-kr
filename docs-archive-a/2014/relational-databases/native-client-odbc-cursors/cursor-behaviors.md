---
title: 커서 동작 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- scrollable cursors [SQL Server]
- SQL Server Native Client ODBC driver, cursors
- version-based optimistic concurrency
- cursors [ODBC], cursor behaviors
- ODBC applications, cursors
- SQL_ATTR_CURSOR_SENSITIVITY option
- SQL_ATTR_CURSOR_SCROLLABLE option
- sensitivity behavior of cursor
- ODBC cursors, cursor behaviors
ms.assetid: 742ddcd2-232b-4aa1-9212-027df120ad35
author: rothja
ms.author: jroth
ms.openlocfilehash: 89c7c4e9a8dcffe03dd12f8013d5ed43810547f3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650938"
---
# <a name="cursor-behaviors"></a><span data-ttu-id="efaa8-102">커서 동작</span><span class="sxs-lookup"><span data-stu-id="efaa8-102">Cursor Behaviors</span></span>
  <span data-ttu-id="efaa8-103">ODBC는 커서의 스크롤 가능 여부 및 민감도를 지정하여 커서의 동작을 지정하는 ISO 옵션을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="efaa8-103">ODBC supports the ISO options for specifying the behavior of cursors by specifying their scrollability and sensitivity.</span></span> <span data-ttu-id="efaa8-104">이러한 동작은 [SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md)에 대 한 호출에서 SQL_ATTR_CURSOR_SCROLLABLE 및 SQL_ATTR_CURSOR_SENSITIVITY 옵션을 설정 하 여 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="efaa8-104">These behaviors are specified by setting the SQL_ATTR_CURSOR_SCROLLABLE and SQL_ATTR_CURSOR_SENSITIVITY options on a call to [SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md).</span></span> <span data-ttu-id="efaa8-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 드라이버는 다음과 같은 특징을 가진 서버 커서를 요청하여 이러한 옵션을 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="efaa8-105">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver implements these options by requesting server cursors with the following characteristics.</span></span>  
  
|<span data-ttu-id="efaa8-106">커서 동작 설정</span><span class="sxs-lookup"><span data-stu-id="efaa8-106">Cursor behavior settings</span></span>|<span data-ttu-id="efaa8-107">필요한 서버 커서 특징</span><span class="sxs-lookup"><span data-stu-id="efaa8-107">Server cursor characteristics requested</span></span>|  
|------------------------------|---------------------------------------------|  
|<span data-ttu-id="efaa8-108">SQL_SCROLLABLE 및 SQL_SENSITIVE</span><span class="sxs-lookup"><span data-stu-id="efaa8-108">SQL_SCROLLABLE and SQL_SENSITIVE</span></span>|<span data-ttu-id="efaa8-109">키 집합 커서 및 버전 기반 낙관적 동시성</span><span class="sxs-lookup"><span data-stu-id="efaa8-109">Keyset-driven cursor and version-based optimistic concurrency</span></span>|  
|<span data-ttu-id="efaa8-110">SQL_SCROLLABLE 및 SQL_INSENSITIVE</span><span class="sxs-lookup"><span data-stu-id="efaa8-110">SQL_SCROLLABLE and SQL_INSENSITIVE</span></span>|<span data-ttu-id="efaa8-111">정적 커서 및 읽기 전용 동시성</span><span class="sxs-lookup"><span data-stu-id="efaa8-111">Static cursor and read-only concurrency</span></span>|  
|<span data-ttu-id="efaa8-112">SQL_SCROLLABLE 및 SQL_UNSPECIFIED</span><span class="sxs-lookup"><span data-stu-id="efaa8-112">SQL_SCROLLABLE and SQL_UNSPECIFIED</span></span>|<span data-ttu-id="efaa8-113">정적 커서 및 읽기 전용 동시성</span><span class="sxs-lookup"><span data-stu-id="efaa8-113">Static cursor and read-only concurrency</span></span>|  
|<span data-ttu-id="efaa8-114">SQL_NONSCROLLABLE 및 SQL_SENSITIVE</span><span class="sxs-lookup"><span data-stu-id="efaa8-114">SQL_NONSCROLLABLE and SQL_SENSITIVE</span></span>|<span data-ttu-id="efaa8-115">정방향 전용 커서 및 버전 기반 낙관적 동시성</span><span class="sxs-lookup"><span data-stu-id="efaa8-115">Forward-only cursor and version-based optimistic concurrency</span></span>|  
|<span data-ttu-id="efaa8-116">SQL_NONSCROLLABLE 및 SQL_INSENSITIVE</span><span class="sxs-lookup"><span data-stu-id="efaa8-116">SQL_NONSCROLLABLE and SQL_INSENSITIVE</span></span>|<span data-ttu-id="efaa8-117">기본 결과 집합(정방향 전용, 읽기 전용)</span><span class="sxs-lookup"><span data-stu-id="efaa8-117">Default result set (forward-only, read-only)</span></span>|  
|<span data-ttu-id="efaa8-118">SQL_NONSCROLLABLE 및 SQL_UNSPECIFIED</span><span class="sxs-lookup"><span data-stu-id="efaa8-118">SQL_NONSCROLLABLE and SQL_UNSPECIFIED</span></span>|<span data-ttu-id="efaa8-119">기본 결과 집합(정방향 전용, 읽기 전용)</span><span class="sxs-lookup"><span data-stu-id="efaa8-119">Default result set (forward-only, read-only)</span></span>|  
  
 <span data-ttu-id="efaa8-120">버전 기반 낙관적 동시성을 사용 하려면 기본 테이블에 **timestamp** 열이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="efaa8-120">Version-based optimistic concurrency requires a **timestamp** column in the underlying table.</span></span> <span data-ttu-id="efaa8-121">**Timestamp** 열이 없는 테이블에 대해 버전 기반 낙관적 동시성 제어를 요청 하는 경우 서버는 값 기반 낙관적 동시성을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="efaa8-121">If version-based optimistic concurrency control is requested on a table that does not have a **timestamp** column, the server uses values-based optimistic concurrency.</span></span>  
  
## <a name="scrollability"></a><span data-ttu-id="efaa8-122">스크롤 가능 여부</span><span class="sxs-lookup"><span data-stu-id="efaa8-122">Scrollability</span></span>  
 <span data-ttu-id="efaa8-123">SQL_ATTR_CURSOR_SCROLLABLE을 SQL_SCROLLABLE로 설정 하면 커서가 [Sqlfetchscroll](../native-client-odbc-api/sqlfetchscroll.md)의 *fetchorientation* 매개 변수에 대해 다른 모든 값을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="efaa8-123">When SQL_ATTR_CURSOR_SCROLLABLE is set to SQL_SCROLLABLE, the cursor supports all the different values for the *FetchOrientation* parameter of [SQLFetchScroll](../native-client-odbc-api/sqlfetchscroll.md).</span></span> <span data-ttu-id="efaa8-124">SQL_ATTR_CURSOR_SCROLLABLE을 SQL_NONSCROLLABLE로 설정 하면 커서는 SQL_FETCH_NEXT의 *Fetchorientation* 값만 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="efaa8-124">When SQL_ATTR_CURSOR_SCROLLABLE is set to SQL_NONSCROLLABLE, the cursor only supports a *FetchOrientation* value of SQL_FETCH_NEXT.</span></span>  
  
## <a name="sensitivity"></a><span data-ttu-id="efaa8-125">민감도</span><span class="sxs-lookup"><span data-stu-id="efaa8-125">Sensitivity</span></span>  
 <span data-ttu-id="efaa8-126">SQL_ATTR_CURSOR_SENSITIVITY가 SQL_SENSITIVE로 설정되면 커서는 현재 사용자가 수행하거나 다른 사용자가 커밋한 데이터 수정 내용을 반영합니다.</span><span class="sxs-lookup"><span data-stu-id="efaa8-126">When SQL_ATTR_CURSOR_SENSITIVITY is set to SQL_SENSITIVE, the cursor reflects data modifications made by the current user or committed by other users.</span></span> <span data-ttu-id="efaa8-127">SQL_ATTR_CURSOR_SENSITIVITY가 SQL_INSENSITIVE로 설정되면 커서는 데이터 수정 내용을 반영하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="efaa8-127">When SQL_ATTR_CURSOR_SENSITIVITY is set to SQL_INSENSITIVE, the cursor does not reflect data modifications.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="efaa8-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="efaa8-128">See Also</span></span>  
 [<span data-ttu-id="efaa8-129">ODBC&#41;&#40;커서 사용</span><span class="sxs-lookup"><span data-stu-id="efaa8-129">Using Cursors &#40;ODBC&#41;</span></span>](using-cursors-odbc.md)  
  
  
