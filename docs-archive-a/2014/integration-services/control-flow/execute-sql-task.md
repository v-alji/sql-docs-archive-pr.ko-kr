---
title: SQL 실행 태스크 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.executesqltask.f1
helpviewer_keywords:
- Transact-SQL statements, SSIS
- statements [Integration Services]
- batches [Integration Services]
- Execute SQL task [Integration Services]
ms.assetid: bebb2e8c-0410-43b2-ac2f-6fc80c8f2e9e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e77b9f442ae8478c57d5b0e68955b541eda38aff
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729708"
---
# <a name="execute-sql-task"></a><span data-ttu-id="2ddc7-102">SQL 실행 태스크</span><span class="sxs-lookup"><span data-stu-id="2ddc7-102">Execute SQL Task</span></span>
  <span data-ttu-id="2ddc7-103">SQL 실행 태스크는 패키지에서 SQL 문이나 저장 프로시저를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="2ddc7-103">The Execute SQL task runs SQL statements or stored procedures from a package.</span></span> <span data-ttu-id="2ddc7-104">이 태스크는 단일 SQL 문 또는 순서대로 실행되는 여러 SQL 문을 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2ddc7-104">The task can contain either a single SQL statement or multiple SQL statements that run sequentially.</span></span> <span data-ttu-id="2ddc7-105">SQL 실행 태스크는 다음 용도로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2ddc7-105">You can use the Execute SQL task for the following purposes:</span></span>  
  
-   <span data-ttu-id="2ddc7-106">데이터를 삽입하기 위해 테이블 또는 뷰를 자릅니다.</span><span class="sxs-lookup"><span data-stu-id="2ddc7-106">Truncate a table or view in preparation for inserting data.</span></span>  
  
-   <span data-ttu-id="2ddc7-107">테이블 및 뷰와 같은 데이터베이스 개체를 만들고 변경 및 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="2ddc7-107">Create, alter, and drop database objects such as tables and views.</span></span>  
  
-   <span data-ttu-id="2ddc7-108">팩트 및 차원 테이블에 데이터를 로드하기 전에 해당 테이블을 다시 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2ddc7-108">Re-create fact and dimension tables before loading data into them.</span></span>  
  
-   <span data-ttu-id="2ddc7-109">저장 프로시저를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="2ddc7-109">Run stored procedures.</span></span> <span data-ttu-id="2ddc7-110">SQL 문이 임시 테이블의 결과를 반환하는 저장 프로시저를 호출하는 경우 WITH RESULT SETS 옵션을 사용하여 결과 집합의 메타데이터를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="2ddc7-110">If the SQL statement invokes a stored procedure that returns results from a temporary table, use the WITH RESULT SETS option to define metadata for the result set.</span></span>  
  
-   <span data-ttu-id="2ddc7-111">쿼리에서 반환된 행 집합을 변수에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="2ddc7-111">Save the rowset returned from a query into a variable.</span></span>  
  
 <span data-ttu-id="2ddc7-112">SQL 실행 태스크를 Foreach 루프 및 For 루프 컨테이너와 함께 사용하여 여러 개의 SQL 문을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2ddc7-112">The Execute SQL task can be used in combination with the Foreach Loop and For Loop containers to run multiple SQL statements.</span></span> <span data-ttu-id="2ddc7-113">두 컨테이너는 패키지의 반복 제어 흐름을 구현하며 SQL 실행 태스크를 반복해서 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2ddc7-113">These containers implement repeating control flows in a package and they can run the Execute SQL task repeatedly.</span></span> <span data-ttu-id="2ddc7-114">예를 들어 Foreach 루프 컨테이너를 사용하면 패키지가 폴더에 있는 파일을 열거하고 SQL 실행 태스크를 반복 실행하여 각 파일에 저장된 SQL 문을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2ddc7-114">For example, using the Foreach Loop container, a package can enumerate files in a folder and run an Execute SQL task repeatedly to execute the SQL statement stored in each file.</span></span>  
  
## <a name="connecting-to-a-data-source"></a><span data-ttu-id="2ddc7-115">데이터 소스에 연결</span><span class="sxs-lookup"><span data-stu-id="2ddc7-115">Connecting to a Data Source</span></span>  
 <span data-ttu-id="2ddc7-116">SQL 실행 태스크는 여러 유형의 연결 관리자를 사용하여 SQL 문이나 저장 프로시저가 실행될 데이터 원본에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2ddc7-116">The Execute SQL task can use different types of connection managers to connect to the data source where it runs the SQL statement or stored procedure.</span></span> <span data-ttu-id="2ddc7-117">다음 표에 나열된 연결 형식을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2ddc7-117">The task can use the connection types listed in the following table.</span></span>  
  
|<span data-ttu-id="2ddc7-118">연결 형식</span><span class="sxs-lookup"><span data-stu-id="2ddc7-118">Connection type</span></span>|<span data-ttu-id="2ddc7-119">ODBC 대상 편집기</span><span class="sxs-lookup"><span data-stu-id="2ddc7-119">Connection manager</span></span>|  
|---------------------|------------------------|  
|<span data-ttu-id="2ddc7-120">EXCEL</span><span class="sxs-lookup"><span data-stu-id="2ddc7-120">EXCEL</span></span>|[<span data-ttu-id="2ddc7-121">Excel 연결 관리자</span><span class="sxs-lookup"><span data-stu-id="2ddc7-121">Excel Connection Manager</span></span>](../connection-manager/excel-connection-manager.md)|  
|<span data-ttu-id="2ddc7-122">OLE DB</span><span class="sxs-lookup"><span data-stu-id="2ddc7-122">OLE DB</span></span>|[<span data-ttu-id="2ddc7-123">OLE DB 연결 관리자</span><span class="sxs-lookup"><span data-stu-id="2ddc7-123">OLE DB Connection Manager</span></span>](../connection-manager/ole-db-connection-manager.md)|  
|<span data-ttu-id="2ddc7-124">ODBC</span><span class="sxs-lookup"><span data-stu-id="2ddc7-124">ODBC</span></span>|[<span data-ttu-id="2ddc7-125">ODBC 연결 관리자</span><span class="sxs-lookup"><span data-stu-id="2ddc7-125">ODBC Connection Manager</span></span>](../connection-manager/odbc-connection-manager.md)|  
|<span data-ttu-id="2ddc7-126">ADO</span><span class="sxs-lookup"><span data-stu-id="2ddc7-126">ADO</span></span>|[<span data-ttu-id="2ddc7-127">ADO 연결 관리자</span><span class="sxs-lookup"><span data-stu-id="2ddc7-127">ADO Connection Manager</span></span>](../connection-manager/ado-connection-manager.md)|  
|<span data-ttu-id="2ddc7-128">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="2ddc7-128">ADO.NET</span></span>|[<span data-ttu-id="2ddc7-129">ADO.NET 연결 관리자</span><span class="sxs-lookup"><span data-stu-id="2ddc7-129">ADO.NET Connection Manager</span></span>](../connection-manager/ado-net-connection-manager.md)|  
|<span data-ttu-id="2ddc7-130">SQLMOBILE</span><span class="sxs-lookup"><span data-stu-id="2ddc7-130">SQLMOBILE</span></span>|[<span data-ttu-id="2ddc7-131">SQL Server Compact Edition 연결 관리자</span><span class="sxs-lookup"><span data-stu-id="2ddc7-131">SQL Server Compact Edition Connection Manager</span></span>](../connection-manager/sql-server-compact-edition-connection-manager.md)|  
  
## <a name="creating-sql-statements"></a><span data-ttu-id="2ddc7-132">SQL 문 만들기</span><span class="sxs-lookup"><span data-stu-id="2ddc7-132">Creating SQL Statements</span></span>  
 <span data-ttu-id="2ddc7-133">이 태스크에 사용되는 SQL 문의 원본은 문이 포함된 작업 속성, 하나 이상의 문이 포함된 파일에 대한 연결 또는 문이 포함된 변수 이름일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2ddc7-133">The source of the SQL statements used by this task can be a task property that contains a statement, a connection to a file that contains one or multiple statements, or the name of a variable that contains a statement.</span></span> <span data-ttu-id="2ddc7-134">SQL 문은 원본 DBMS(데이터베이스 관리 시스템) 언어로 기록되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2ddc7-134">The SQL statements must be written in the dialect of the source database management system (DBMS).</span></span> <span data-ttu-id="2ddc7-135">자세한 내용은 [Integration Services&#40;SSIS&#41; 쿼리](../integration-services-ssis-queries.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2ddc7-135">For more information, see [Integration Services &#40;SSIS&#41; Queries](../integration-services-ssis-queries.md).</span></span>  
  
 <span data-ttu-id="2ddc7-136">SQL 문이 파일에 저장되어 있을 경우 SQL 실행 태스크는 파일 연결 관리자를 사용하여 해당 파일에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="2ddc7-136">If the SQL statements are stored in a file, the task uses a File connection manager to connect to the file.</span></span> <span data-ttu-id="2ddc7-137">자세한 내용은 [File Connection Manager](../connection-manager/file-connection-manager.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2ddc7-137">For more information, see [File Connection Manager](../connection-manager/file-connection-manager.md).</span></span>  
  
 <span data-ttu-id="2ddc7-138">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너에서는 **SQL 실행 태스크 편집기** 대화 상자를 사용하여 SQL 문을 입력하거나 SQL 쿼리 작성용 그래픽 사용자 인터페이스인 **쿼리 작성기**를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2ddc7-138">In [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, you can use the **Execute SQL Task Editor** dialog box to type SQL statements, or use **Query Builder**, a graphical user interface for creating SQL queries.</span></span> <span data-ttu-id="2ddc7-139">자세한 내용은 [SQL 실행 태스크 편집기&#40;일반 페이지&#41;](../execute-sql-task-editor-general-page.md) 및 [쿼리 작성기](../query-builder.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2ddc7-139">For more information, see [Execute SQL Task Editor &#40;General Page&#41;](../execute-sql-task-editor-general-page.md) and [Query Builder](../query-builder.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2ddc7-140">SQL 실행 태스크 외부에서 작성된 SQL 문은 유효하더라도 SQL 실행 태스크에서 성공적으로 구문 분석되지 않을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2ddc7-140">Valid SQL statements written outside the Execute SQL task may not be parsed successfully by the Execute SQL task.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2ddc7-141">SQL 실행 태스크는 `RecognizeAll` ParseMode 열거형 값을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="2ddc7-141">The Execute SQL Task uses the `RecognizeAll` ParseMode enumeration value.</span></span> <span data-ttu-id="2ddc7-142">자세한 내용은 [ManagedBatchParser 네임스페이스](https://go.microsoft.com/fwlink/?LinkId=223617)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="2ddc7-142">For more information, see [ManagedBatchParser Namespace](https://go.microsoft.com/fwlink/?LinkId=223617).</span></span>  
  
## <a name="sending-multiple-statements-in-a-batch"></a><span data-ttu-id="2ddc7-143">여러 개의 문을 일괄 처리로 전송</span><span class="sxs-lookup"><span data-stu-id="2ddc7-143">Sending Multiple Statements in a Batch</span></span>  
 <span data-ttu-id="2ddc7-144">SQL 실행 태스크에 여러 개의 문이 포함된 경우 문을 그룹화하여 일괄 처리로 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2ddc7-144">If you include multiple statements in an Execute SQL task, you can group them and run them as a batch.</span></span> <span data-ttu-id="2ddc7-145">일괄 처리의 마지막을 알리려면 GO 명령을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="2ddc7-145">To signal the end of a batch, use the GO command.</span></span> <span data-ttu-id="2ddc7-146">두 GO 명령 사이의 모든 SQL 문은 일괄 처리로 실행되도록 OLE DB Provider에 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="2ddc7-146">All the SQL statements between two GO commands are sent in a batch to the OLE DB provider to be run.</span></span> <span data-ttu-id="2ddc7-147">SQL 명령은 GO 명령으로 구분된 여러 개의 일괄 처리를 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2ddc7-147">The SQL command can include multiple batches separated by GO commands.</span></span>  
  
 <span data-ttu-id="2ddc7-148">일괄 처리로 그룹화할 수 있는 SQL 문의 종류에는 제한이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2ddc7-148">There are restrictions on the kinds of SQL statements that you can group in a batch.</span></span> <span data-ttu-id="2ddc7-149">자세한 내용은 [Batches of Statements](../../relational-databases/native-client-odbc-queries/executing-statements/batches-of-statements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2ddc7-149">For more information, see [Batches of Statements](../../relational-databases/native-client-odbc-queries/executing-statements/batches-of-statements.md).</span></span>  
  
 <span data-ttu-id="2ddc7-150">SQL 실행 태스크에서 SQL 문의 일괄 처리를 실행하는 경우 해당 일괄 처리에 다음 규칙이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="2ddc7-150">If the Execute SQL task runs a batch of SQL statements, the following rules apply to the batch:</span></span>  
  
-   <span data-ttu-id="2ddc7-151">일괄 처리의 첫 번째 문 하나만 결과 집합을 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2ddc7-151">Only one statement can return a result set and it must be the first statement in the batch.</span></span>  
  
-   <span data-ttu-id="2ddc7-152">결과 집합에 결과 바인딩을 사용하는 경우 쿼리에서 동일한 수의 열이 반환되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2ddc7-152">If the result set uses result bindings, the queries must return the same number of columns.</span></span> <span data-ttu-id="2ddc7-153">쿼리에서 반환된 열 수가 서로 다르면 태스크가 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="2ddc7-153">If the queries return a different number of columns, the task fails.</span></span> <span data-ttu-id="2ddc7-154">그러나 태스크 실패해도 해당 태스크에서 실행하는 DELETE 또는 INSERT와 같은 쿼리는 성공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2ddc7-154">However, even if the task fails, the queries that it runs, such as DELETE or INSERT queries, may succeed.</span></span>  
  
-   <span data-ttu-id="2ddc7-155">결과 바인딩에 열 이름을 사용하는 경우 태스크에 사용된 결과 집합 이름과 동일한 이름이 포함된 열이 쿼리에서 반환되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2ddc7-155">If the result bindings use column names, the query must return columns that have the same names as the result set names that are used in the task.</span></span> <span data-ttu-id="2ddc7-156">해당 열이 없으면 태스크가 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="2ddc7-156">If the columns are missing, the task fails.</span></span>  
  
-   <span data-ttu-id="2ddc7-157">태스크에 매개 변수 바인딩이 사용되는 경우 일괄 처리의 모든 쿼리에 동일한 수와 유형의 매개 변수를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2ddc7-157">If the task uses parameter binding, all the queries in the batch must have the same number and types of parameters.</span></span>  
  
## <a name="running-parameterized-sql-commands"></a><span data-ttu-id="2ddc7-158">매개 변수가 있는 SQL 명령 실행</span><span class="sxs-lookup"><span data-stu-id="2ddc7-158">Running Parameterized SQL Commands</span></span>  
 <span data-ttu-id="2ddc7-159">SQL 문과 저장 프로시저는 일반적으로 입력 매개 변수, 출력 매개 변수 및 반환 코드를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="2ddc7-159">SQL statements and stored procedures frequently use input parameters, output parameters, and return codes.</span></span> <span data-ttu-id="2ddc7-160">SQL 실행 태스크는 `Input`, `Output` 및 `ReturnValue` 매개 변수 유형을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="2ddc7-160">The Execute SQL task supports the `Input`, `Output`, and `ReturnValue` parameter types.</span></span> <span data-ttu-id="2ddc7-161">입력 매개 변수에는 `Input` 유형, 출력 매개 변수에는 `Output` 유형, 반환 코드에는 `ReturnValue` 유형을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="2ddc7-161">You use the `Input` type for input parameters, `Output` for output parameters, and `ReturnValue` for return codes.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2ddc7-162">데이터 공급자가 지원하는 경우에만 SQL 실행 태스크에 매개 변수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2ddc7-162">You can use parameters in an Execute SQL task only if the data provider supports them.</span></span>  
  
 <span data-ttu-id="2ddc7-163">SQL 실행 태스크에서 매개 변수 및 반환 코드를 사용하는 방법은 [SQL 실행 태스크의 매개 변수 및 반환 코드](execute-sql-task.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2ddc7-163">For information on using parameters and return codes in the Execute SQL task, see [Parameters and Return Codes in the Execute SQL Task](execute-sql-task.md).</span></span>  
  
## <a name="specifying-a-result-set-type"></a><span data-ttu-id="2ddc7-164">결과 집합 유형 지정</span><span class="sxs-lookup"><span data-stu-id="2ddc7-164">Specifying a Result Set Type</span></span>  
 <span data-ttu-id="2ddc7-165">SQL 명령 유형에 따라 SQL 실행 태스크에서 결과 집합이 반환될 수도 있고 반환되지 않을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2ddc7-165">Depending on the type of SQL command, a result set may or may not be returned to the Execute SQL task.</span></span> <span data-ttu-id="2ddc7-166">예를 들어 SELECT 문은 일반적으로 결과 집합을 반환하지만 INSERT 문은 결과 집합을 반환하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2ddc7-166">For example, a SELECT statement typically returns a result set, but an INSERT statement does not.</span></span> <span data-ttu-id="2ddc7-167">SELECT 문의 결과 집합은 행을 포함하지 않을 수도 있고, 하나 이상의 행을 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2ddc7-167">The result set from a SELECT statement can contain zero rows, one row, or many rows.</span></span> <span data-ttu-id="2ddc7-168">저장 프로시저도 반환 코드라고 하는 정수 값을 반환하여 프로시저의 실행 상태를 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2ddc7-168">Stored procedures can also return an integer value, called a return code, that indicates the execution status of the procedure.</span></span> <span data-ttu-id="2ddc7-169">이 경우에는 결과 집합이 단일 행으로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="2ddc7-169">In that case, the result set consists of a single row.</span></span>  
  
 <span data-ttu-id="2ddc7-170">SQL 실행 태스크의 SQL 명령에서 결과 집합을 검색하는 방법은 [SQL 실행 태스크의 결과 집합](../result-sets-in-the-execute-sql-task.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2ddc7-170">For information on retrieving result sets from SQL commands in the Execute SQL task, see [Result Sets in the Execute SQL Task](../result-sets-in-the-execute-sql-task.md).</span></span>  
  
## <a name="troubleshooting-the-execute-sql-task"></a><span data-ttu-id="2ddc7-171">SQL 실행 태스크 문제 해결</span><span class="sxs-lookup"><span data-stu-id="2ddc7-171">Troubleshooting the Execute SQL Task</span></span>  
 <span data-ttu-id="2ddc7-172">SQL 실행 태스크가 외부 데이터 공급자에 대해 수행하는 호출을 기록할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2ddc7-172">You can log the calls that the Execute SQL task makes to external data providers.</span></span> <span data-ttu-id="2ddc7-173">이 로깅 기능을 사용하여 SQL 실행 태스크가 실행하는 SQL 명령의 문제를 해결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2ddc7-173">You can use this logging capability to troubleshoot the SQL commands that the Execute SQL task runs.</span></span> <span data-ttu-id="2ddc7-174">SQL 실행 태스크가 외부 데이터 공급자에 대해 수행하는 호출을 기록하려면 패키지 로깅을 사용하도록 설정하고 패키지 수준에서 **Diagnostic** 이벤트를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="2ddc7-174">To log the calls that the Execute SQL task makes to external data providers, enable package logging and select the **Diagnostic** event at the package level.</span></span> <span data-ttu-id="2ddc7-175">자세한 내용은 [패키지 실행 문제 해결 도구](../troubleshooting/troubleshooting-tools-for-package-execution.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2ddc7-175">For more information, see [Troubleshooting Tools for Package Execution](../troubleshooting/troubleshooting-tools-for-package-execution.md).</span></span>  
  
 <span data-ttu-id="2ddc7-176">경우에 따라 SQL 명령 또는 저장 프로시저는 여러 결과 집합을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="2ddc7-176">Sometimes a SQL command or stored procedure returns multiple result sets.</span></span> <span data-ttu-id="2ddc7-177">이러한 결과 집합에는 `SELECT` 쿼리의 결과인 행 집합뿐만 아니라 `RAISERROR` 또는 `PRINT` 문에 대한 오류 결과인 단일 값도 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="2ddc7-177">These result sets include not only rowsets that are the result of `SELECT` queries, but single values that are the result of errors of `RAISERROR` or `PRINT` statements.</span></span> <span data-ttu-id="2ddc7-178">이 태스크에서 첫 번째 결과 집합 후에 발생하는 결과 집합의 오류를 무시할지 여부는 사용되는 연결 관리자의 유형에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="2ddc7-178">Whether the task ignores errors in result sets that occur after the first result set depends on the type of connection manager that is used:</span></span>  
  
-   <span data-ttu-id="2ddc7-179">OLE DB 및 ADO 연결 관리자를 사용하는 경우 태스크에서 첫 번째 결과 집합 후에 발생하는 결과 집합을 무시합니다.</span><span class="sxs-lookup"><span data-stu-id="2ddc7-179">When you use OLE DB and ADO connection managers, the task ignores the result sets that occur after the first result set.</span></span> <span data-ttu-id="2ddc7-180">따라서 이러한 연결 관리자를 사용하는 경우에는 오류가 첫 번째 결과 집합의 일부가 아니면 태스크에서 SQL 명령 또는 저장 프로시저가 반환하는 오류를 무시합니다.</span><span class="sxs-lookup"><span data-stu-id="2ddc7-180">Therefore, with these connection managers, the task ignores an error returned by an SQL command or a stored procedure when the error is not part of the first result set.</span></span>  
  
-   <span data-ttu-id="2ddc7-181">ODBC 및 ADO.NET 연결 관리자를 사용하는 경우 태스크에서 첫 번째 결과 집합 후에 발생하는 결과 집합을 무시하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2ddc7-181">When you use ODBC and ADO.NET connection managers, the task does not ignore result sets that occur after the first result set.</span></span> <span data-ttu-id="2ddc7-182">이러한 연결 관리자를 사용하는 경우 첫 번째 결과 집합이 아닌 다른 결과 집합에 오류가 포함되어 있으면 오류가 발생하여 태스크에 실패하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2ddc7-182">With these connection managers, the task will fail with an error when a result set other than the first result set contains an error.</span></span>  
  
### <a name="custom-log-entries"></a><span data-ttu-id="2ddc7-183">사용자 지정 로그 항목</span><span class="sxs-lookup"><span data-stu-id="2ddc7-183">Custom Log Entries</span></span>  
 <span data-ttu-id="2ddc7-184">다음 표에서는 SQL 실행 태스크에 대한 사용자 지정 로그 항목을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="2ddc7-184">The following table describes the custom log entry for the Execute SQL task.</span></span> <span data-ttu-id="2ddc7-185">자세한 내용은 [Integration Services&#40;SSIS&#41; 로깅](../performance/integration-services-ssis-logging.md) 및 [로깅할 메시지 사용자 지정](../custom-messages-for-logging.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2ddc7-185">For more information, see [Integration Services &#40;SSIS&#41; Logging](../performance/integration-services-ssis-logging.md) and [Custom Messages for Logging](../custom-messages-for-logging.md).</span></span>  
  
|<span data-ttu-id="2ddc7-186">로그 항목</span><span class="sxs-lookup"><span data-stu-id="2ddc7-186">Log entry</span></span>|<span data-ttu-id="2ddc7-187">Description</span><span class="sxs-lookup"><span data-stu-id="2ddc7-187">Description</span></span>|  
|---------------|-----------------|  
|`ExecuteSQLExecutingQuery`|<span data-ttu-id="2ddc7-188">SQL 문의 실행 단계에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="2ddc7-188">Provides information about the execution phases of the SQL statement.</span></span> <span data-ttu-id="2ddc7-189">로그 항목은 태스크에서 데이터베이스에 대한 연결을 설정할 때, 태스크에서 SQL 문 준비를 시작할 때 또는 SQL 문 실행이 완료된 후에 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="2ddc7-189">Log entries are written when the task acquires connection to the database, when the task starts to prepare the SQL statement, and after the execution of the SQL statement is completed.</span></span> <span data-ttu-id="2ddc7-190">준비 단계에 대한 로그 항목은 태스크에서 사용하는 SQL 문을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="2ddc7-190">The log entry for the prepare phase includes the SQL statement that the task uses.</span></span>|  
  
## <a name="configuring-the-execute-sql-task"></a><span data-ttu-id="2ddc7-191">SQL 실행 태스크 구성</span><span class="sxs-lookup"><span data-stu-id="2ddc7-191">Configuring the Execute SQL Task</span></span>  
 <span data-ttu-id="2ddc7-192">다음과 같은 방법으로 SQL 실행 태스크를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2ddc7-192">You can configure the Execute SQL task in the following ways:</span></span>  
  
-   <span data-ttu-id="2ddc7-193">데이터베이스에 연결할 때 사용할 연결 관리자 유형을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2ddc7-193">Specify the type of connection manager to use to connect to a database.</span></span>  
  
-   <span data-ttu-id="2ddc7-194">SQL 문에서 반환되는 결과 집합 유형을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2ddc7-194">Specify the type of result set that the SQL statement returns.</span></span>  
  
-   <span data-ttu-id="2ddc7-195">SQL 문의 제한 시간을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2ddc7-195">Specify a time-out for the SQL statements.</span></span>  
  
-   <span data-ttu-id="2ddc7-196">SQL 문의 원본을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2ddc7-196">Specify the source of the SQL statement.</span></span>  
  
-   <span data-ttu-id="2ddc7-197">태스크에서 SQL 문의 준비 단계를 건너뛸지를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="2ddc7-197">Indicate whether the task skips the prepare phase for the SQL statement.</span></span>  
  
-   <span data-ttu-id="2ddc7-198">ADO 연결 형식을 사용하는 경우 SQL 문이 저장 프로시저인지 여부를 나타내야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2ddc7-198">If you use the ADO connection type, you must indicate whether the SQL statement is a stored procedure.</span></span> <span data-ttu-id="2ddc7-199">다른 연결 유형에서 이 속성은 읽기 전용이며 항상 `false` 값을 갖습니다.</span><span class="sxs-lookup"><span data-stu-id="2ddc7-199">For other connection types, this property is read-only and its value is always `false`.</span></span>  
  
 <span data-ttu-id="2ddc7-200">프로그래밍 방식을 통해 또는 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너를 사용하여 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2ddc7-200">You can set properties programmatically or through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer.</span></span>  
  
 <span data-ttu-id="2ddc7-201">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너에서 설정할 수 있는 속성에 대한 자세한 내용을 보려면 다음 항목 중 하나를 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="2ddc7-201">For more information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="2ddc7-202">SQL 실행 태스크 편집기 &#40;일반 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="2ddc7-202">Execute SQL Task Editor &#40;General Page&#41;</span></span>](../execute-sql-task-editor-general-page.md)  
  
-   [<span data-ttu-id="2ddc7-203">SQL 실행 태스크 편집기 &#40;매개 변수 매핑 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="2ddc7-203">Execute SQL Task Editor &#40;Parameter Mapping Page&#41;</span></span>](../execute-sql-task-editor-parameter-mapping-page.md)  
  
-   [<span data-ttu-id="2ddc7-204">SQL 실행 태스크 편집기 &#40;결과 집합 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="2ddc7-204">Execute SQL Task Editor &#40;Result Set Page&#41;</span></span>](../execute-sql-task-editor-result-set-page.md)  
  
-   [<span data-ttu-id="2ddc7-205">식 페이지</span><span class="sxs-lookup"><span data-stu-id="2ddc7-205">Expressions Page</span></span>](../expressions/expressions-page.md)  
  
 <span data-ttu-id="2ddc7-206">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너에서 이러한 속성을 설정하는 방법을 보려면 다음 항목을 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="2ddc7-206">For more information about how to set these properties in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="2ddc7-207">태스크 또는 컨테이너의 속성 설정</span><span class="sxs-lookup"><span data-stu-id="2ddc7-207">Set the Properties of a Task or Container</span></span>](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="configuring-the-execute-sql-task-programmatically"></a><span data-ttu-id="2ddc7-208">프로그래밍 방식으로 SQL 실행 태스크 구성</span><span class="sxs-lookup"><span data-stu-id="2ddc7-208">Configuring the Execute SQL Task Programmatically</span></span>  
 <span data-ttu-id="2ddc7-209">이러한 속성을 프로그래밍 방식으로 설정하는 방법을 보려면 다음 항목을 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="2ddc7-209">For more information about programmatically setting these properties, click the following topic:</span></span>  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.ExecuteSQLTask.ExecuteSQLTask>  
  
## <a name="related-tasks"></a><span data-ttu-id="2ddc7-210">관련 작업</span><span class="sxs-lookup"><span data-stu-id="2ddc7-210">Related Tasks</span></span>  
  
-   [<span data-ttu-id="2ddc7-211">쿼리 매개 변수를 SQL 실행 태스크의 변수에 매핑</span><span class="sxs-lookup"><span data-stu-id="2ddc7-211">Map Query Parameters to Variables in an Execute SQL Task</span></span>](../map-query-parameters-to-variables-in-an-execute-sql-task.md)  
  
-   [<span data-ttu-id="2ddc7-212">결과 집합을 SQL 실행 태스크의 변수에 매핑</span><span class="sxs-lookup"><span data-stu-id="2ddc7-212">Map Result Sets to Variables in an Execute SQL Task</span></span>](../map-result-sets-to-variables-in-an-execute-sql-task.md)  
  
## <a name="related-content"></a><span data-ttu-id="2ddc7-213">관련 내용</span><span class="sxs-lookup"><span data-stu-id="2ddc7-213">Related Content</span></span>  
  
-   [<span data-ttu-id="2ddc7-214">SQL 실행 태스크의 매개 변수 및 반환 코드</span><span class="sxs-lookup"><span data-stu-id="2ddc7-214">Parameters and Return Codes in the Execute SQL Task</span></span>](execute-sql-task.md)  
  
-   [<span data-ttu-id="2ddc7-215">SQL 실행 태스크의 결과 집합</span><span class="sxs-lookup"><span data-stu-id="2ddc7-215">Result Sets in the Execute SQL Task</span></span>](../result-sets-in-the-execute-sql-task.md)  
  
-   [<span data-ttu-id="2ddc7-216">Transact-SQL 참조 &#40;데이터베이스 엔진&#41;</span><span class="sxs-lookup"><span data-stu-id="2ddc7-216">Transact-SQL Reference &#40;Database Engine&#41;</span></span>](/sql/t-sql/language-reference)  
  
-   <span data-ttu-id="2ddc7-217">mssqltips.com의 블로그 항목 - [SQL Server 2012에서의 새로운 날짜 및 시간 함수](https://go.microsoft.com/fwlink/?LinkId=239783)</span><span class="sxs-lookup"><span data-stu-id="2ddc7-217">Blog entry, [New Date and Time Functions in SQL Server 2012](https://go.microsoft.com/fwlink/?LinkId=239783), on mssqltips.com</span></span>  
  
  
