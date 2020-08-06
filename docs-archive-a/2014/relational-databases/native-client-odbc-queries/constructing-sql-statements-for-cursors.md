---
title: 커서에 대 한 SQL 문 생성 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- cursors [ODBC], statement construction
- ODBC applications, cursors
- SQL Server Native Client ODBC driver, statements
- statements [ODBC], constructing
- ODBC applications, statements
- statements [ODBC], cursors
ms.assetid: 134003fd-9c93-4f5c-a988-045990933b80
author: rothja
ms.author: jroth
ms.openlocfilehash: b0fe0831b97c13c5d20067386f4e9d8c97ee19ed
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646414"
---
# <a name="constructing-sql-statements-for-cursors"></a><span data-ttu-id="43a1a-102">쿼리에 대한 SQL 문 생성</span><span class="sxs-lookup"><span data-stu-id="43a1a-102">Constructing SQL Statements for Cursors</span></span>
  <span data-ttu-id="43a1a-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native CLIENT odbc 드라이버는 서버 커서를 사용 하 여 odbc 사양에 정의 된 커서 기능을 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="43a1a-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver uses server cursors to implement the cursor functionality defined in the ODBC specification.</span></span> <span data-ttu-id="43a1a-104">ODBC 응용 프로그램은 [SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md) 를 사용 하 여 다른 문 특성을 설정 하 여 커서 동작을 제어 합니다.</span><span class="sxs-lookup"><span data-stu-id="43a1a-104">An ODBC application controls the cursor behavior by using [SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md) to set different statement attributes.</span></span> <span data-ttu-id="43a1a-105">다음은 이러한 특성과 해당 기본값에 대한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="43a1a-105">These are the attributes and their defaults.</span></span>  
  
|<span data-ttu-id="43a1a-106">attribute</span><span class="sxs-lookup"><span data-stu-id="43a1a-106">Attribute</span></span>|<span data-ttu-id="43a1a-107">기본값</span><span class="sxs-lookup"><span data-stu-id="43a1a-107">Default</span></span>|  
|---------------|-------------|  
|<span data-ttu-id="43a1a-108">SQL_ATTR_CONCURRENCY</span><span class="sxs-lookup"><span data-stu-id="43a1a-108">SQL_ATTR_CONCURRENCY</span></span>|<span data-ttu-id="43a1a-109">SQL_CONCUR_READ_ONLY</span><span class="sxs-lookup"><span data-stu-id="43a1a-109">SQL_CONCUR_READ_ONLY</span></span>|  
|<span data-ttu-id="43a1a-110">SQL_ATTR_CURSOR_TYPE</span><span class="sxs-lookup"><span data-stu-id="43a1a-110">SQL_ATTR_CURSOR_TYPE</span></span>|<span data-ttu-id="43a1a-111">SQL_CURSOR_FORWARD_ONLY</span><span class="sxs-lookup"><span data-stu-id="43a1a-111">SQL_CURSOR_FORWARD_ONLY</span></span>|  
|<span data-ttu-id="43a1a-112">SQL_ATTR_CURSOR_SCROLLABLE</span><span class="sxs-lookup"><span data-stu-id="43a1a-112">SQL_ATTR_CURSOR_SCROLLABLE</span></span>|<span data-ttu-id="43a1a-113">SQL_NONSCROLLABLE</span><span class="sxs-lookup"><span data-stu-id="43a1a-113">SQL_NONSCROLLABLE</span></span>|  
|<span data-ttu-id="43a1a-114">SQL_ATTR_CURSOR_SENSITIVITY</span><span class="sxs-lookup"><span data-stu-id="43a1a-114">SQL_ATTR_CURSOR_SENSITIVITY</span></span>|<span data-ttu-id="43a1a-115">SQL_UNSPECIFIED</span><span class="sxs-lookup"><span data-stu-id="43a1a-115">SQL_UNSPECIFIED</span></span>|  
|<span data-ttu-id="43a1a-116">SQL_ATTR_ROW_ARRAY_SIZE</span><span class="sxs-lookup"><span data-stu-id="43a1a-116">SQL_ATTR_ROW_ARRAY_SIZE</span></span>|<span data-ttu-id="43a1a-117">1</span><span class="sxs-lookup"><span data-stu-id="43a1a-117">1</span></span>|  
  
 <span data-ttu-id="43a1a-118">SQL 문이 실행 될 때 이러한 옵션을 기본값으로 설정 하면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native CLIENT ODBC 드라이버는 서버 커서를 사용 하 여 결과 집합을 구현 하지 않고 대신 기본 결과 집합을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="43a1a-118">When these options are set to their defaults at the time an SQL statement is executed, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver does not use a server cursor to implement the result set; instead, it uses a default result set.</span></span> <span data-ttu-id="43a1a-119">SQL 문이 실행 될 때 이러한 옵션이 기본값에서 변경 된 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native CLIENT ODBC 드라이버는 서버 커서를 사용 하 여 결과 집합을 구현 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="43a1a-119">If any of these options are changed from their defaults at the time an SQL statement is executed, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver attempts to use a server cursor to implement the result set.</span></span>  
  
 <span data-ttu-id="43a1a-120">기본 결과 집합을 사용할 때는 모든 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문이 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="43a1a-120">Default result sets support all of the [!INCLUDE[tsql](../../includes/tsql-md.md)] statements.</span></span> <span data-ttu-id="43a1a-121">기본 결과 집합을 사용할 경우 실행할 수 있는 SQL 문의 유형에는 제한이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="43a1a-121">There are no restrictions on the types of SQL statements that can be executed when using a default result set.</span></span>  
  
 <span data-ttu-id="43a1a-122">서버 커서를 사용할 경우에는 일부 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문이 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="43a1a-122">Server cursors do not support all [!INCLUDE[tsql](../../includes/tsql-md.md)] statements.</span></span> <span data-ttu-id="43a1a-123">서버 커서에서는 여러 결과 집합을 생성하는 SQL 문이 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="43a1a-123">Server cursors do not support any SQL statement that generates multiple result sets.</span></span>  
  
 <span data-ttu-id="43a1a-124">서버 커서에서 지원되지 않는 문 유형은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="43a1a-124">The following types of statements are not supported by server cursors:</span></span>  
  
-   <span data-ttu-id="43a1a-125">Batch</span><span class="sxs-lookup"><span data-stu-id="43a1a-125">Batches</span></span>  
  
     <span data-ttu-id="43a1a-126">다음 예와 같이 두 개 이상의 개별 SQL SELECT 문으로 작성된 SQL 문</span><span class="sxs-lookup"><span data-stu-id="43a1a-126">SQL statements built from two or more individual SQL SELECT statements, for example:</span></span>  
  
    ```  
    SELECT * FROM Authors; SELECT * FROM Titles  
    ```  
  
-   <span data-ttu-id="43a1a-127">여러 SELECT 문이 있는 저장 프로시저</span><span class="sxs-lookup"><span data-stu-id="43a1a-127">Stored procedures with multiple SELECT statements</span></span>  
  
     <span data-ttu-id="43a1a-128">둘 이상의 SELECT 문이 포함된 저장 프로시저를 실행하는 SQL 문.</span><span class="sxs-lookup"><span data-stu-id="43a1a-128">SQL statements that execute a stored procedure containing more than one SELECT statement.</span></span> <span data-ttu-id="43a1a-129">여기에는 매개 변수나 변수를 채우는 SELECT 문도 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="43a1a-129">This includes SELECT statements that fill parameters or variables.</span></span>  
  
-   <span data-ttu-id="43a1a-130">키워드</span><span class="sxs-lookup"><span data-stu-id="43a1a-130">Keywords</span></span>  
  
     <span data-ttu-id="43a1a-131">FOR BROWSE 또는 INTO 키워드를 포함하는 SQL 문</span><span class="sxs-lookup"><span data-stu-id="43a1a-131">SQL statements containing the keywords FOR BROWSE, or INTO.</span></span>  
  
 <span data-ttu-id="43a1a-132">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 이러한 조건과 일치하는 SQL 문을 서버 커서를 사용하여 실행하면 서버 커서가 암시적으로 기본 결과 집합으로 변환됩니다.</span><span class="sxs-lookup"><span data-stu-id="43a1a-132">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], if an SQL statement that matches any of these conditions is executed with a server cursor, the server cursor is implicitly converted to a default result set.</span></span> <span data-ttu-id="43a1a-133">**Sqlexecdirect** 또는 **sqlexecute** 가 SQL_SUCCESS_WITH_INFO 반환 된 후에는 커서 특성이 기본 설정으로 다시 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="43a1a-133">After **SQLExecDirect** or **SQLExecute** returns SQL_SUCCESS_WITH_INFO, the cursor attributes will be set back to their default settings.</span></span>  
  
 <span data-ttu-id="43a1a-134">위의 범주에 맞지 않는 SQL 문은 모든 문 특성 설정을 사용하여 실행할 수 있으며, 기본 결과 집합이나 서버 커서 중 무엇을 사용하든 동일하게 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="43a1a-134">SQL statements that do not fit the categories above can be executed with any statement attribute settings; they work equally well with either a default result set or a server cursor.</span></span>  
  
## <a name="errors"></a><span data-ttu-id="43a1a-135">오류</span><span class="sxs-lookup"><span data-stu-id="43a1a-135">Errors</span></span>  
 <span data-ttu-id="43a1a-136">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 7.0 이상에서 여러 결과 집합을 반환하는 문을 실행하려고 하면 SQL_SUCCESS_WITH INFO 및 다음 메시지가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="43a1a-136">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 7.0 and later, an attempt to execute a statement that produces multiple result sets generates SQL_SUCCESS_WITH INFO and the following message:</span></span>  
  
```  
SqlState: 01S02"  
pfNative: 0  
szErrorMsgString: "[Microsoft][SQL Server Native Client][SQL Server]  
               Cursor type changed."  
```  
  
 <span data-ttu-id="43a1a-137">이 메시지를 수신 하는 ODBC 응용 프로그램은 [SQLGetStmtAttr](../native-client-odbc-api/sqlgetstmtattr.md) 를 호출 하 여 현재 커서 설정을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="43a1a-137">ODBC applications receiving this message can call [SQLGetStmtAttr](../native-client-odbc-api/sqlgetstmtattr.md) to determine the current cursor settings.</span></span>  
  
 <span data-ttu-id="43a1a-138">서버 커서를 사용할 때 여러 SELECT 문이 포함된 프로시저를 실행하려고 하면 다음 오류가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="43a1a-138">An attempt to execute a procedure with multiple SELECT statements when using server cursors generates the following error:</span></span>  
  
```  
SqlState: 42000  
pfNative: 16937  
szErrorMsgString: [Microsoft][SQL Server Native Client][SQL Server]  
               A server cursor is not allowed on a stored procedure  
               with more than one SELECT statement in it. Use a  
               default result set or client cursor.  
```  
  
 <span data-ttu-id="43a1a-139">서버 커서를 사용할 때 여러 SELECT 문이 포함된 일괄 처리를 실행하려고 하면 다음 오류가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="43a1a-139">An attempt to execute a batch with multiple SELECT statements when using server cursors generates the following error:</span></span>  
  
```  
SqlState: 42000  
pfNative: 16938  
szErrorMsgString: [Microsoft][SQL Server Native Client][SQL Server]  
               sp_cursoropen. The statement parameter can only  
               be a single SELECT statement or a single stored   
               procedure.  
```  
  
 <span data-ttu-id="43a1a-140">이 오류를 수신하는 ODBC 애플리케이션은 문을 실행하기 전에 모든 커서 문 특성을 기본값으로 다시 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="43a1a-140">ODBC applications receiving these errors must reset all the cursor statement attributes to their defaults before attempting to execute the statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43a1a-141">참고 항목</span><span class="sxs-lookup"><span data-stu-id="43a1a-141">See Also</span></span>  
 [<span data-ttu-id="43a1a-142">ODBC&#41;&#40;쿼리 실행</span><span class="sxs-lookup"><span data-stu-id="43a1a-142">Executing Queries &#40;ODBC&#41;</span></span>](executing-queries-odbc.md)  
  
  
