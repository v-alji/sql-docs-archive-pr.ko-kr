---
title: ODBC의 행 책갈피 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- cursors [ODBC], fetching rows
- ODBC cursors, fetching rows
- cursors [ODBC], scrolling rows
- ODBC cursors, scrolling rows
- bookmarks [ODBC]
ms.assetid: 9cfcd243-c9d4-4c2a-abc4-399dbabe5f6b
author: rothja
ms.author: jroth
ms.openlocfilehash: def05f478c16dcbcdc91771925a11b0b91da2e9e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739922"
---
# <a name="bookmarking-rows-in-odbc"></a><span data-ttu-id="24906-102">ODBC의 행 집합에 책갈피 설정</span><span class="sxs-lookup"><span data-stu-id="24906-102">Bookmarking Rows in ODBC</span></span>
  <span data-ttu-id="24906-103">책갈피는 데이터의 행을 식별하는 데 사용되는 값입니다.</span><span class="sxs-lookup"><span data-stu-id="24906-103">A bookmark is a value used to identify a row of data.</span></span> <span data-ttu-id="24906-104">책갈피 값의 의미는 드라이버나 데이터 원본에만 알려집니다.</span><span class="sxs-lookup"><span data-stu-id="24906-104">The meaning of the bookmark value is known only to the driver or data source.</span></span> <span data-ttu-id="24906-105">예를 들어 책갈피 값은 행 번호처럼 간단하거나 디스크 주소처럼 복잡할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="24906-105">For example, it might be as simple as a row number or as complex as a disk address.</span></span> <span data-ttu-id="24906-106">ODBC 애플리케이션에서는 특정 행에 대해 책갈피를 요청하고 이를 저장한 다음 다시 커서에 전달하여 원래 행으로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="24906-106">In ODBC, the application requests a bookmark for a particular row, stores it, and passes it back to the cursor to return to the row.</span></span>  
  
 <span data-ttu-id="24906-107">[Sqlfetchscroll](../native-client-odbc-api/sqlfetchscroll.md)을 사용 하 여 행을 인출 하는 경우 응용 프로그램은 시작 행을 선택 하기 위한 기준으로 책갈피를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="24906-107">When fetching rows with [SQLFetchScroll](../native-client-odbc-api/sqlfetchscroll.md), an application can use a bookmark as a basis for selecting the starting row.</span></span> <span data-ttu-id="24906-108">이 책갈피는 현재 커서 위치를 사용하지 않기 때문에 절대 주소 형태로 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="24906-108">This is a form of absolute addressing because it does not depend on the current cursor position.</span></span> <span data-ttu-id="24906-109">책갈피가 설정 된 행으로 스크롤하려면 응용 프로그램은 SQL_FETCH_BOOKMARK의 *Fetchorientation* 로 **sqlfetchscroll** 을 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="24906-109">To scroll to a bookmarked row, the application calls **SQLFetchScroll** with a *FetchOrientation* of SQL_FETCH_BOOKMARK.</span></span> <span data-ttu-id="24906-110">이 작업은 SQL_ATTR_FETCH_BOOKMARK_PTR 옵션 특성이 가리키는 책갈피를 사용하며</span><span class="sxs-lookup"><span data-stu-id="24906-110">This operation uses the bookmark pointed to by the SQL_ATTR_FETCH_BOOKMARK_PTR option attribute.</span></span> <span data-ttu-id="24906-111">이 책갈피를 통해 식별된 행부터 행 집합을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="24906-111">It returns the rowset starting with the row identified by that bookmark.</span></span> <span data-ttu-id="24906-112">응용 프로그램은 **Sqlfetchscroll**에 대 한 호출의 *fetchoffset* 인수에서이 작업에 대 한 오프셋을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="24906-112">An application can specify an offset for this operation in the *FetchOffset* argument of the call to **SQLFetchScroll**.</span></span> <span data-ttu-id="24906-113">오프셋이 지정되면 책갈피를 통해 식별된 행 수에 FetchOffset 인수에 지정된 숫자를 더하는 방식으로 반환된 행 집합의 첫 번째 행이 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="24906-113">When an offset is specified, the first row of the returned rowset is determined by adding the number in the FetchOffset argument to the number of the row identified by the bookmark.</span></span> <span data-ttu-id="24906-114">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 드라이버는 정적 및 키 집합 커서에 대해서만 책갈피를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="24906-114">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver only supports bookmarks on static and keyset cursors.</span></span> <span data-ttu-id="24906-115">책갈피가 설정되어 있을 때 동적 커서가 요청되면 키 집합 커서가 대신 열립니다.</span><span class="sxs-lookup"><span data-stu-id="24906-115">If a dynamic cursor is requested when bookmarks are set on, a keyset cursor is opened instead.</span></span>  
  
 <span data-ttu-id="24906-116">책갈피를 **SQLBulkOperations** 함수와 함께 사용 하 여 책갈피에서 시작 하는 행 집합에 대 한 작업을 수행할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="24906-116">Bookmarks can also be used with the **SQLBulkOperations** function to perform operations on a set of rows starting at the bookmark.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24906-117">참고 항목</span><span class="sxs-lookup"><span data-stu-id="24906-117">See Also</span></span>  
 [<span data-ttu-id="24906-118">행 스크롤 및 페치</span><span class="sxs-lookup"><span data-stu-id="24906-118">Scrolling and Fetching Rows</span></span>](../native-client-ole-db-rowsets/fetching-rows.md)  
  
  
