---
title: 쿼리 실행 (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC applications, executing queries
- SQL Server Native Client ODBC driver, statements
- ODBC applications, statements
- SQL Server Native Client ODBC driver, queries
- queries [ODBC]
ms.assetid: d935bcba-8ce6-4159-8395-6c86431602ad
author: rothja
ms.author: jroth
ms.openlocfilehash: adc51186803148056401f58f1207d3e9a7abf9c5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646412"
---
# <a name="executing-queries-odbc"></a><span data-ttu-id="d1ab5-102">쿼리 실행(ODBC)</span><span class="sxs-lookup"><span data-stu-id="d1ab5-102">Executing Queries (ODBC)</span></span>
  <span data-ttu-id="d1ab5-103">ODBC 애플리케이션은 연결 핸들을 초기화하고 데이터 원본에 연결한 후 연결 핸들에 하나 이상의 문 핸들을 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="d1ab5-103">After an ODBC application initializes a connection handle and connects with a data source, it allocates one or more statement handles on the connection handle.</span></span> <span data-ttu-id="d1ab5-104">그런 다음 응용 프로그램은 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 문 핸들에서 문을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d1ab5-104">The application can then execute [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] statements on the statement handle.</span></span> <span data-ttu-id="d1ab5-105">SQL 문을 실행하는 이벤트의 일반적인 순서는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="d1ab5-105">The general sequence of events in executing an SQL statement is:</span></span>  
  
1.  <span data-ttu-id="d1ab5-106">필요한 모든 문 특성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="d1ab5-106">Set any required statement attributes.</span></span>  
  
2.  <span data-ttu-id="d1ab5-107">해당 문을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="d1ab5-107">Construct the statement.</span></span>  
  
3.  <span data-ttu-id="d1ab5-108">해당 문을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="d1ab5-108">Execute the statement.</span></span>  
  
4.  <span data-ttu-id="d1ab5-109">결과 집합을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="d1ab5-109">Retrieve any result sets.</span></span>  
  
 <span data-ttu-id="d1ab5-110">애플리케이션은 SQL 문으로 반환된 모든 결과 집합에서 모든 행을 검색한 후 동일한 문 핸들에서 다른 쿼리를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d1ab5-110">After an application retrieves all the rows in all of the result sets returned by the SQL statement, it can execute another query on the same statement handle.</span></span> <span data-ttu-id="d1ab5-111">응용 프로그램에서 특정 결과 집합의 모든 행을 검색할 필요가 없다고 결정 한 경우 [SQLMoreResults](../native-client-odbc-api/sqlmoreresults.md) 또는 [SQLCloseCursor](../native-client-odbc-api/sqlclosecursor.md)를 호출 하 여 나머지 결과 집합을 취소할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d1ab5-111">If an application determines that it is not required to retrieve all the rows in a particular result set, it can cancel the rest of the result set by calling either [SQLMoreResults](../native-client-odbc-api/sqlmoreresults.md) or [SQLCloseCursor](../native-client-odbc-api/sqlclosecursor.md).</span></span>  
  
 <span data-ttu-id="d1ab5-112">ODBC 애플리케이션에서 서로 다른 데이터를 사용하여 동일한 SQL 문을 여러 번 실행해야 한다면 SQL 문을 생성할 때 물음표(?)로 표시되는 매개 변수 표식을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="d1ab5-112">If, in an ODBC application, you must execute the same SQL statement multiple times with different data, use a parameter marker denoted by a question mark (?) in the construction of an SQL statement:</span></span>  
  
```  
INSERT INTO MyTable VALUES (?, ?, ?)  
```  
  
 <span data-ttu-id="d1ab5-113">그런 다음 [SQLBindParameter](../native-client-odbc-api/sqlbindparameter.md)를 호출 하 여 각 매개 변수 표식을 프로그램 변수에 바인딩할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d1ab5-113">Each parameter marker can then be bound to a program variable by calling [SQLBindParameter](../native-client-odbc-api/sqlbindparameter.md).</span></span>  
  
 <span data-ttu-id="d1ab5-114">모든 SQL 문을 실행하고 해당 결과 집합을 처리한 후 애플리케이션은 문 핸들을 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="d1ab5-114">After all SQL statements execute and their result sets process, the application frees the statement handle.</span></span>  
  
 <span data-ttu-id="d1ab5-115">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native CLIENT ODBC 드라이버는 연결 핸들 당 여러 문 핸들을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="d1ab5-115">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver supports multiple statement handles per connection handle.</span></span> <span data-ttu-id="d1ab5-116">트랜잭션은 연결 수준에서 관리되므로 단일 연결 핸들의 모든 문 핸들에서 수행된 모든 작업은 동일한 트랜잭션의 일부로 관리됩니다.</span><span class="sxs-lookup"><span data-stu-id="d1ab5-116">Transactions are managed at the connection level, so that all work performed on all statement handles on a single connection handle are managed as part of the same transaction.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d1ab5-117">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="d1ab5-117">In This Section</span></span>  
  
-   [<span data-ttu-id="d1ab5-118">문 핸들 할당</span><span class="sxs-lookup"><span data-stu-id="d1ab5-118">Allocating a Statement Handle</span></span>](allocating-a-statement-handle.md)  
  
-   [<span data-ttu-id="d1ab5-119">ODBC&#41;&#40;SQL 문 생성</span><span class="sxs-lookup"><span data-stu-id="d1ab5-119">Constructing an SQL Statement &#40;ODBC&#41;</span></span>](constructing-an-sql-statement-odbc.md)  
  
-   [<span data-ttu-id="d1ab5-120">쿼리에 대한 SQL 문 생성</span><span class="sxs-lookup"><span data-stu-id="d1ab5-120">Constructing SQL Statements for Cursors</span></span>](constructing-sql-statements-for-cursors.md)  
  
-   [<span data-ttu-id="d1ab5-121">문 매개 변수 사용</span><span class="sxs-lookup"><span data-stu-id="d1ab5-121">Using Statement Parameters</span></span>](using-statement-parameters.md)  
  
-   [<span data-ttu-id="d1ab5-122">ODBC&#41;&#40;문을 실행 하는 중</span><span class="sxs-lookup"><span data-stu-id="d1ab5-122">Executing Statements &#40;ODBC&#41;</span></span>](executing-statements/executing-statements-odbc.md)  
  
-   [<span data-ttu-id="d1ab5-123">문 핸들 해제</span><span class="sxs-lookup"><span data-stu-id="d1ab5-123">Freeing a Statement Handle</span></span>](freeing-a-statement-handle.md)  
  
## <a name="see-also"></a><span data-ttu-id="d1ab5-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d1ab5-124">See Also</span></span>  
 [<span data-ttu-id="d1ab5-125">SQL Server Native Client &#40;ODBC&#41;</span><span class="sxs-lookup"><span data-stu-id="d1ab5-125">SQL Server Native Client &#40;ODBC&#41;</span></span>](../native-client/odbc/sql-server-native-client-odbc.md)  
  
  
