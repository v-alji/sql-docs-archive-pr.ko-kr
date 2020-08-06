---
title: 결과 처리 (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- result sets [ODBC], about result sets
- SQLRowCount function
- SQL Server Native Client ODBC driver, result sets
- ODBC applications, result sets
- COMPUTE clause
- result sets [ODBC]
- COMPUTE BY clause
ms.assetid: 61a8db19-6571-47dd-84e8-fcc97cb60b45
author: rothja
ms.author: jroth
ms.openlocfilehash: 72c0d15231b07a23f10a03b0fca270d1d014891c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741971"
---
# <a name="processing-results-odbc"></a><span data-ttu-id="d0c05-102">결과 처리(ODBC)</span><span class="sxs-lookup"><span data-stu-id="d0c05-102">Processing Results (ODBC)</span></span>
  <span data-ttu-id="d0c05-103">애플리케이션이 SQL 문을 제출하면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 결과 데이터를 하나 이상의 결과 집합으로 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="d0c05-103">After an application submits a SQL statement, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] returns any resulting data as one or more result sets.</span></span> <span data-ttu-id="d0c05-104">결과 집합은 쿼리 조건과 일치하는 행과 열 집합입니다.</span><span class="sxs-lookup"><span data-stu-id="d0c05-104">A result set is a set of rows and columns that match the criteria of the query.</span></span> <span data-ttu-id="d0c05-105">SELECT 문, 카탈로그 함수 및 일부 저장 프로시저는 애플리케이션에서 사용할 수 있는 결과 집합을 테이블 형식으로 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="d0c05-105">SELECT statements, catalog functions, and some stored procedures produce a result set made available to an application in tabular form.</span></span> <span data-ttu-id="d0c05-106">실행한 SQL 문이 저장 프로시저, 여러 명령이 포함된 일괄 처리 또는 키워드가 포함된 SELECT 문이면 처리할 결과 집합이 여러 개가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d0c05-106">If the executed SQL statement is a stored procedure, a batch containing multiple commands, or a SELECT statement containing keywords, there will be multiple result sets to process.</span></span>  
  
 <span data-ttu-id="d0c05-107">또한 ODBC 카탈로그 함수는 데이터를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0c05-107">ODBC catalog functions also can retrieve data.</span></span> <span data-ttu-id="d0c05-108">예를 들어 [Sqlcolumns](../native-client-odbc-api/sqlcolumns.md) 는 데이터 원본에 있는 열에 대 한 데이터를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0c05-108">For example, [SQLColumns](../native-client-odbc-api/sqlcolumns.md) retrieves data about columns in the data source.</span></span> <span data-ttu-id="d0c05-109">이러한 결과 집합에는 0개 이상의 행이 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0c05-109">These result sets can contain zero or more rows.</span></span>  
  
 <span data-ttu-id="d0c05-110">GRANT 또는 REVOKE와 같은 다른 SQL 문은 결과 집합을 반환하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d0c05-110">Other SQL statements, such as GRANT or REVOKE, do not return result sets.</span></span> <span data-ttu-id="d0c05-111">이러한 문의 경우 **Sqlexecute** 또는 **sqlexecdirect** 의 반환 코드는 일반적으로 문이 성공 했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="d0c05-111">For these statements, the return code from **SQLExecute** or **SQLExecDirect** is usually the only indication the statement was successful.</span></span>  
  
 <span data-ttu-id="d0c05-112">각 INSERT, UPDATE 및 DELETE 문은 수정 내용이 적용되는 행 수만 포함된 결과 집합을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="d0c05-112">Each INSERT, UPDATE, and DELETE statement returns a result set containing only the number of rows affected by the modification.</span></span> <span data-ttu-id="d0c05-113">이 개수는 응용 프로그램이 [Sqlrowcount](../native-client-odbc-api/sqlrowcount.md)를 호출할 때 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0c05-113">This count is made available when application calls [SQLRowCount](../native-client-odbc-api/sqlrowcount.md).</span></span> <span data-ttu-id="d0c05-114">ODBC 3. *x* 응용 프로그램은 **sqlrowcount** 를 호출 하 여 결과 집합을 검색 하거나 [SQLMoreResults](../native-client-odbc-api/sqlmoreresults.md) 를 호출 하 여 취소 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0c05-114">ODBC 3.*x* applications must either call **SQLRowCount** to retrieve the result set or [SQLMoreResults](../native-client-odbc-api/sqlmoreresults.md) to cancel it.</span></span> <span data-ttu-id="d0c05-115">응용 프로그램이 여러 INSERT, UPDATE 또는 DELETE 문을 포함 하는 일괄 처리 또는 저장 프로시저를 실행 하는 경우 각 수정 문의 결과 집합을 **Sqlrowcount** 를 사용 하 여 처리 하거나 **SQLMoreResults**를 사용 하 여 취소 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0c05-115">When an application executes a batch or stored procedure containing multiple INSERT, UPDATE, or DELETE statements, the result set from each modification statement must be processed using **SQLRowCount** or cancelled using **SQLMoreResults**.</span></span> <span data-ttu-id="d0c05-116">일괄 처리나 저장 프로시저에 SET NOCOUNT ON 문을 포함하여 이 개수를 취소할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0c05-116">These counts can be cancelled by including a SET NOCOUNT ON statement in the batch or stored procedure.</span></span>  
  
 <span data-ttu-id="d0c05-117">Transact-SQL에는 SET NOCOUNT 문이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0c05-117">Transact-SQL includes the SET NOCOUNT statement.</span></span> <span data-ttu-id="d0c05-118">NOCOUNT 옵션을 on으로 설정 하면 SQL Server는 문의 영향을 받는 행 수를 반환 하지 않으며 **Sqlrowcount** 는 0을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0c05-118">When the NOCOUNT option is set on, SQL Server does not return the counts of the rows affected by a statement and **SQLRowCount** returns 0.</span></span> <span data-ttu-id="d0c05-119">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native CLIENT ODBC 드라이버 버전은 NOCOUNT 옵션의 설정 또는 해제 여부를 보고 하는 드라이버 관련 [SQLGetStmtAttr](../native-client-odbc-api/sqlgetstmtattr.md) 옵션인 SQL_SOPT_SS_NOCOUNT_STATUS를 소개 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0c05-119">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver version introduces a driver-specific [SQLGetStmtAttr](../native-client-odbc-api/sqlgetstmtattr.md) option, SQL_SOPT_SS_NOCOUNT_STATUS, to report on whether the NOCOUNT option is on or off.</span></span> <span data-ttu-id="d0c05-120">**Sqlrowcount** 가 0을 반환할 때마다 응용 프로그램이 SQL_SOPT_SS_NOCOUNT_STATUS를 테스트 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0c05-120">Anytime **SQLRowCount** returns 0, the application should test SQL_SOPT_SS_NOCOUNT_STATUS.</span></span> <span data-ttu-id="d0c05-121">SQL_NC_ON 반환 되는 경우 **Sqlrowcount** 의 값이 0 이면 SQL Server 행 개수가 반환 되지 않았음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="d0c05-121">If SQL_NC_ON is returned, the value of 0 from **SQLRowCount** only indicates that SQL Server has not returned a row count.</span></span> <span data-ttu-id="d0c05-122">SQL_NC_OFF 반환 되는 경우에는 NOCOUNT가 OFF이 고 **Sqlrowcount** 의 값 0은 문이 행에 영향을 주지 않았음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="d0c05-122">If SQL_NC_OFF is returned, it means that NOCOUNT is off and the value of 0 from **SQLRowCount** indicates that the statement did not affect any rows.</span></span> <span data-ttu-id="d0c05-123">SQL_SOPT_SS_NOCOUNT_STATUS SQL_NC_OFF 되 면 응용 프로그램에서 **Sqlrowcount** 값을 표시 해서는 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d0c05-123">Applications should not display the value of **SQLRowCount** when SQL_SOPT_SS_NOCOUNT_STATUS is SQL_NC_OFF.</span></span> <span data-ttu-id="d0c05-124">큰 일괄 처리나 저장 프로시저에는 여러 개의 SET NOCOUNT 문이 포함될 수 있으므로 프로그래머는 SQL_SOPT_SS_NOCOUNT_STATUS가 일정하게 유지된다고 가정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d0c05-124">Large batches or stored procedures may contain multiple SET NOCOUNT statements so programmers cannot assume SQL_SOPT_SS_NOCOUNT_STATUS remains constant.</span></span> <span data-ttu-id="d0c05-125">**Sqlrowcount** 가 0을 반환할 때마다이 옵션을 테스트 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0c05-125">The option should be tested each time **SQLRowCount** returns 0.</span></span>  
  
 <span data-ttu-id="d0c05-126">다른 몇 개의 Transact-SQL 문은 데이터를 결과 집합이 아닌 메시지로 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="d0c05-126">Several other Transact-SQL statements return their data in messages rather than result sets.</span></span> <span data-ttu-id="d0c05-127">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native CLIENT ODBC 드라이버는 이러한 메시지를 받을 때 정보 메시지를 사용할 수 있다는 것을 응용 프로그램에 알리기 위해 SQL_SUCCESS_WITH_INFO를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0c05-127">When the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver receives these messages, it returns SQL_SUCCESS_WITH_INFO to let the application know that informational messages are available.</span></span> <span data-ttu-id="d0c05-128">그런 다음 응용 프로그램은 **SQLGetDiagRec** 를 호출 하 여 이러한 메시지를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0c05-128">The application can then call **SQLGetDiagRec** to retrieve these messages.</span></span> <span data-ttu-id="d0c05-129">이런 방식으로 작동하는 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="d0c05-129">The [!INCLUDE[tsql](../../includes/tsql-md.md)] statements that work this way are:</span></span>  
  
-   <span data-ttu-id="d0c05-130">DBCC</span><span class="sxs-lookup"><span data-stu-id="d0c05-130">DBCC</span></span>  
  
-   <span data-ttu-id="d0c05-131">SET SHOWPLAN(이전 버전의 SQL Server에서 사용 가능)</span><span class="sxs-lookup"><span data-stu-id="d0c05-131">SET SHOWPLAN (available with earlier versions of SQL Server)</span></span>  
  
-   <span data-ttu-id="d0c05-132">SET STATISTICS</span><span class="sxs-lookup"><span data-stu-id="d0c05-132">SET STATISTICS</span></span>  
  
-   <span data-ttu-id="d0c05-133">PRINT</span><span class="sxs-lookup"><span data-stu-id="d0c05-133">PRINT</span></span>  
  
-   <span data-ttu-id="d0c05-134">RAISERROR</span><span class="sxs-lookup"><span data-stu-id="d0c05-134">RAISERROR</span></span>  
  
 <span data-ttu-id="d0c05-135">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native CLIENT ODBC 드라이버는 심각도가 11 이상인 RAISERROR에 SQL_ERROR를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0c05-135">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver returns SQL_ERROR on a RAISERROR with a severity of 11 or higher.</span></span> <span data-ttu-id="d0c05-136">RAISERROR의 심각도가 19이면 연결도 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="d0c05-136">If the severity of the RAISERROR is 19 or higher, the connection is also dropped.</span></span>  
  
 <span data-ttu-id="d0c05-137">SQL 문의 결과 집합을 처리하기 위해 애플리케이션은 다음 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="d0c05-137">To process the result sets from an SQL statement, the application:</span></span>  
  
-   <span data-ttu-id="d0c05-138">결과 집합의 특징을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="d0c05-138">Determines the characteristics of the result set.</span></span>  
  
-   <span data-ttu-id="d0c05-139">열을 프로그램 변수에 바인딩합니다.</span><span class="sxs-lookup"><span data-stu-id="d0c05-139">Binds the columns to program variables.</span></span>  
  
-   <span data-ttu-id="d0c05-140">단일 값, 전체 행의 값 또는 여러 행의 값을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="d0c05-140">Retrieves a single value, an entire row of values, or multiple rows of values.</span></span>  
  
-   <span data-ttu-id="d0c05-141">테스트를 통해 추가 결과 집합이 있는지 확인하고, 있는 경우 루프백하여 새 결과 집합의 특징을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="d0c05-141">Tests to see if there are more result sets, and if so, loops back to determining the characteristics of the new result set.</span></span>  
  
 <span data-ttu-id="d0c05-142">데이터 원본에서 행을 검색하고 애플리케이션에 반환하는 프로세스를 인출이라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0c05-142">The process of retrieving rows from the data source and returning them to the application is called fetching.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d0c05-143">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="d0c05-143">In This Section</span></span>  
  
-   [<span data-ttu-id="d0c05-144">ODBC&#41;&#40;결과 집합의 특징 확인</span><span class="sxs-lookup"><span data-stu-id="d0c05-144">Determining the Characteristics of a Result Set &#40;ODBC&#41;</span></span>](determining-the-characteristics-of-a-result-set-odbc.md)  
  
-   [<span data-ttu-id="d0c05-145">스토리지 할당</span><span class="sxs-lookup"><span data-stu-id="d0c05-145">Assigning Storage</span></span>](assigning-storage.md)  
  
-   [<span data-ttu-id="d0c05-146">결과 데이터 인출</span><span class="sxs-lookup"><span data-stu-id="d0c05-146">Fetching Result Data</span></span>](fetching-result-data.md)  
  
-   [<span data-ttu-id="d0c05-147">ODBC&#41;&#40;데이터 형식 매핑</span><span class="sxs-lookup"><span data-stu-id="d0c05-147">Mapping Data Types &#40;ODBC&#41;</span></span>](mapping-data-types-odbc.md)  
  
-   [<span data-ttu-id="d0c05-148">데이터 형식 사용</span><span class="sxs-lookup"><span data-stu-id="d0c05-148">Data Type Usage</span></span>](data-type-usage.md)  
  
-   [<span data-ttu-id="d0c05-149">문자 데이터 자동 변환</span><span class="sxs-lookup"><span data-stu-id="d0c05-149">Autotranslation of Character Data</span></span>](autotranslation-of-character-data.md)  
  
## <a name="see-also"></a><span data-ttu-id="d0c05-150">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d0c05-150">See Also</span></span>  
 <span data-ttu-id="d0c05-151">[ODBC&#41;SQL Server Native Client &#40;](../native-client/odbc/sql-server-native-client-odbc.md) </span><span class="sxs-lookup"><span data-stu-id="d0c05-151">[SQL Server Native Client &#40;ODBC&#41;](../native-client/odbc/sql-server-native-client-odbc.md) </span></span>  
 [<span data-ttu-id="d0c05-152">결과 처리 방법 도움말 항목 &#40;ODBC&#41;</span><span class="sxs-lookup"><span data-stu-id="d0c05-152">Processing Results How-to Topics &#40;ODBC&#41;</span></span>](../../database-engine/dev-guide/processing-results-how-to-topics-odbc.md)  
  
  
