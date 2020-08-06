---
title: 커서 구현 방법 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, cursors
- ODBC cursors, about ODBC cursors
- ODBC applications, cursors
- cursors [ODBC], about ODBC cursors
ms.assetid: 2b1d7dd4-08a4-43fc-b3eb-70c183d0941f
author: rothja
ms.author: jroth
ms.openlocfilehash: 18995355b825d9cb1e62b4794429b5e98ef2b472
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649071"
---
# <a name="how-cursors-are-implemented"></a><span data-ttu-id="3e283-102">커서 구현 방법</span><span class="sxs-lookup"><span data-stu-id="3e283-102">How Cursors Are Implemented</span></span>
  <span data-ttu-id="3e283-103">ODBC 애플리케이션은 SQL 문을 실행하기 전에 문 특성을 하나 이상 설정하여 커서의 동작을 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="3e283-103">ODBC applications control the behavior of a cursor by setting one or more statement attributes before executing an SQL statement.</span></span> <span data-ttu-id="3e283-104">ODBC에는 커서의 특징을 지정하는 다음 두 가지 방법이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3e283-104">ODBC has two different ways to specify the characteristics of a cursor:</span></span>  
  
-   <span data-ttu-id="3e283-105">커서 유형</span><span class="sxs-lookup"><span data-stu-id="3e283-105">Cursor type</span></span>  
  
     <span data-ttu-id="3e283-106">커서 유형은 [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md)의 SQL_ATTR_CURSOR_TYPE 특성을 사용 하 여 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3e283-106">Cursor types are set using the SQL_ATTR_CURSOR_TYPE attribute of [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md).</span></span> <span data-ttu-id="3e283-107">ODBC 커서 유형은 정방향 전용, 정적, 키 집합, 혼합 및 동적입니다.</span><span class="sxs-lookup"><span data-stu-id="3e283-107">The ODBC cursor types are forward-only, static, keyset-driven, mixed, and dynamic.</span></span> <span data-ttu-id="3e283-108">커서 유형 설정은 ODBC에서 커서를 지정하는 원래 방법이었습니다.</span><span class="sxs-lookup"><span data-stu-id="3e283-108">Setting the cursor type was the original method of specifying cursors in ODBC.</span></span>  
  
-   <span data-ttu-id="3e283-109">커서 동작</span><span class="sxs-lookup"><span data-stu-id="3e283-109">Cursor behavior</span></span>  
  
     <span data-ttu-id="3e283-110">커서 동작은 **SQLSetStmtAttr**의 SQL_ATTR_CURSOR_SCROLLABLE 및 SQL_ATTR_CURSOR_SENSITIVITY 특성을 사용 하 여 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3e283-110">Cursor behavior is set using the SQL_ATTR_CURSOR_SCROLLABLE and SQL_ATTR_CURSOR_SENSITIVITY attributes of **SQLSetStmtAttr**.</span></span> <span data-ttu-id="3e283-111">이러한 특성은 ISO 표준에서 DECLARE CURSOR에 대해 정의된 SCROLL 및 SENSITIVE 키워드를 기반으로 모델링됩니다.</span><span class="sxs-lookup"><span data-stu-id="3e283-111">These attributes are modeled on the SCROLL and SENSITIVE keywords defined for the DECLARE CURSOR statement in ISO standards.</span></span> <span data-ttu-id="3e283-112">이 두 개의 ISO 옵션은 ODBC 버전 3.0에서 도입되었습니다.</span><span class="sxs-lookup"><span data-stu-id="3e283-112">These two ISO options were introduced in ODBC version 3.0.</span></span>  
  
 <span data-ttu-id="3e283-113">ODBC 커서의 특징은 두 방법 중 하나를 사용하여 지정해야 하며, ODBC 커서 유형을 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="3e283-113">The characteristics of an ODBC cursor should be specified using either one or the other of these two methods, with the preference being to use the ODBC cursor types.</span></span>  
  
 <span data-ttu-id="3e283-114">커서 유형을 설정하는 것 외에도 ODBC 애플리케이션은 각 인출에서 반환된 행 수, 동시 옵션 및 트랜잭션 격리 수준과 같은 다른 옵션을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="3e283-114">In addition to setting the type of a cursor, ODBC applications also set other options, such as the number of rows returned on each fetch, concurrency options, and transaction isolation levels.</span></span> <span data-ttu-id="3e283-115">ODBC 스타일 커서(정방향 전용, 정적, 키 집합, 혼합 및 동적) 또는 ISO 스타일 커서(스크롤 가능 여부 및 민감도)에 대해 이러한 옵션을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3e283-115">These options can be set for either ODBC-style cursors (forward-only, static, keyset-driven, mixed, and dynamic) or ISO style cursors (scrollability and sensitivity).</span></span>  
  
 <span data-ttu-id="3e283-116">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native CLIENT ODBC 드라이버는 다양 한 유형의 커서를 물리적으로 구현 하는 여러 가지 방법을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e283-116">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver supports several ways to physically implement the various types of cursors.</span></span> <span data-ttu-id="3e283-117">이 드라이버는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 기본 결과 집합을 사용하여 일부 커서 유형을 구현합니다. 다른 커서는 서버 커서로 구현하거나 ODBC 커서 라이브러리를 사용하여 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="3e283-117">The driver implements some types of cursors using a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] default result set; it implements others as server cursors or by using the ODBC Cursor Library.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3e283-118">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="3e283-118">In This Section</span></span>  
  
-   [<span data-ttu-id="3e283-119">SQL Server 기본 결과 집합 사용</span><span class="sxs-lookup"><span data-stu-id="3e283-119">Using SQL Server Default Result Sets</span></span>](using-sql-server-default-result-sets.md)  
  
-   [<span data-ttu-id="3e283-120">서버 커서 사용</span><span class="sxs-lookup"><span data-stu-id="3e283-120">Using Server Cursors</span></span>](using-server-cursors.md)  
  
-   [<span data-ttu-id="3e283-121">ODBC 커서 라이브러리</span><span class="sxs-lookup"><span data-stu-id="3e283-121">ODBC Cursor Library</span></span>](odbc-cursor-library.md)  
  
## <a name="see-also"></a><span data-ttu-id="3e283-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3e283-122">See Also</span></span>  
 [<span data-ttu-id="3e283-123">ODBC&#41;&#40;커서 사용</span><span class="sxs-lookup"><span data-stu-id="3e283-123">Using Cursors &#40;ODBC&#41;</span></span>](../using-cursors-odbc.md)  
  
  
