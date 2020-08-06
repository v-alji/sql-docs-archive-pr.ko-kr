---
title: SQL 실행 태스크 편집기 (일반 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.executesqltask.general.f1
helpviewer_keywords:
- Execute SQL Task Editor
ms.assetid: beb39086-28ce-46af-b6d8-f7b4fb8d9069
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 32bec035646c976442eb66ff1270b961835b243b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647760"
---
# <a name="execute-sql-task-editor-general-page"></a><span data-ttu-id="08d9d-102">SQL 실행 태스크 편집기(일반 페이지)</span><span class="sxs-lookup"><span data-stu-id="08d9d-102">Execute SQL Task Editor (General Page)</span></span>
  <span data-ttu-id="08d9d-103">**SQL 실행 태스크 편집기** 대화 상자의 **일반** 페이지를 사용하여 SQL 실행 태스크를 구성하고 해당 태스크에서 실행할 SQL 문을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="08d9d-103">Use the **General** page of the **Execute SQL Task Editor** dialog box to configure the Execute SQL task and provide the SQL statement that the task runs.</span></span>  
  
 <span data-ttu-id="08d9d-104">이 태스크에 대해 알아보려면 [SQL 실행 태스크](control-flow/execute-sql-task.md), [SQL 실행 태스크의 매개 변수 및 반환 코드](../../2014/integration-services/parameters-and-return-codes-in-the-execute-sql-task.md) 및 [SQL 실행 태스크의 결과 집합](../../2014/integration-services/result-sets-in-the-execute-sql-task.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="08d9d-104">To learn about this task, see [Execute SQL Task](control-flow/execute-sql-task.md), [Parameters and Return Codes in the Execute SQL Task](../../2014/integration-services/parameters-and-return-codes-in-the-execute-sql-task.md), and [Result Sets in the Execute SQL Task](../../2014/integration-services/result-sets-in-the-execute-sql-task.md).</span></span> <span data-ttu-id="08d9d-105">Transact-SQL 쿼리 언어에 대한 자세한 내용은 [Transact-SQL 참조&#40;데이터베이스 엔진&#41;](/sql/t-sql/language-reference)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="08d9d-105">To learn more about the Transact-SQL query language, see [Transact-SQL Reference &#40;Database Engine&#41;](/sql/t-sql/language-reference).</span></span>  
  
## <a name="static-options"></a><span data-ttu-id="08d9d-106">정적 옵션</span><span class="sxs-lookup"><span data-stu-id="08d9d-106">Static Options</span></span>  
 <span data-ttu-id="08d9d-107">**이름**</span><span class="sxs-lookup"><span data-stu-id="08d9d-107">**Name**</span></span>  
 <span data-ttu-id="08d9d-108">워크플로의 SQL 실행 태스크에 사용할 고유 이름을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="08d9d-108">Provide a unique name for the Execute SQL task in the workflow.</span></span> <span data-ttu-id="08d9d-109">제공한 이름은 [!INCLUDE[ssIS](../includes/ssis-md.md)] 디자이너에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="08d9d-109">The name that is provided will be displayed within [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer.</span></span>  
  
 <span data-ttu-id="08d9d-110">**설명**</span><span class="sxs-lookup"><span data-stu-id="08d9d-110">**Description**</span></span>  
 <span data-ttu-id="08d9d-111">SQL 실행 태스크를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="08d9d-111">Describe the Execute SQL task.</span></span> <span data-ttu-id="08d9d-112">해당 태스크의 용도를 설명하여 패키지를 이해하기 쉽고 유지 관리하기 편하도록 만드는 것이 가장 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="08d9d-112">As a best practice, to make packages self-documenting and easier to maintain, describe the task in terms of its purpose.</span></span>  
  
 <span data-ttu-id="08d9d-113">**TimeOut**</span><span class="sxs-lookup"><span data-stu-id="08d9d-113">**TimeOut**</span></span>  
 <span data-ttu-id="08d9d-114">태스크 제한 시간이 초과될 때까지 걸리는 최대 시간(초)을 지정합니다. 값 0은 제한 시간이 없음을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="08d9d-114">Specify the maximum number of seconds the task will run before timing out. A value of 0 indicates an infinite time.</span></span> <span data-ttu-id="08d9d-115">기본값은 0입니다.</span><span class="sxs-lookup"><span data-stu-id="08d9d-115">The default is 0.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="08d9d-116">저장 프로시저에서 연결 설정 및 트랜잭션 완료 시간으로 **TimeOut**에서 지정한 시간(초)보다 큰 수를 지정하여 대기 기능을 에뮬레이트할 경우 저장 프로시저의 제한 시간이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="08d9d-116">Stored procedures do not time out if they emulate sleep functionality by providing time for connections to be made and transactions to complete that is greater than the number of seconds specified by **TimeOut**.</span></span> <span data-ttu-id="08d9d-117">그러나 쿼리를 실행하는 저장 프로시저는 항상 **TimeOut**에서 지정한 시간의 제한을 받습니다.</span><span class="sxs-lookup"><span data-stu-id="08d9d-117">However, stored procedures that execute queries are always subject to the time restriction specified by **TimeOut**.</span></span>  
  
 <span data-ttu-id="08d9d-118">**CodePage**</span><span class="sxs-lookup"><span data-stu-id="08d9d-118">**CodePage**</span></span>  
 <span data-ttu-id="08d9d-119">변수의 유니코드 값을 변환할 때 사용할 코드 페이지를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="08d9d-119">Specify the code page to use when translating Unicode values in variables.</span></span> <span data-ttu-id="08d9d-120">기본값은 로컬 컴퓨터의 코드 페이지입니다.</span><span class="sxs-lookup"><span data-stu-id="08d9d-120">The default value is the code page of the local computer.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="08d9d-121">SQL 실행 태스크에서 ADO 또는 ODBC 연결 관리자를 사용할 때는 **CodePage** 속성을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="08d9d-121">When the Execute SQL task uses an ADO or ODBC connection manager, the **CodePage** property is not available.</span></span> <span data-ttu-id="08d9d-122">솔루션에 코드 페이지의 사용이 필요한 경우에는 SQL 실행 태스크에서 OLE DB 또는 ADO.NET 연결 관리자를 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="08d9d-122">If your solution requires the use of a code page, use an OLE DB or an ADO.NET connection manager with the Execute SQL task.</span></span>  
  
 <span data-ttu-id="08d9d-123">**TypeConversionMode**</span><span class="sxs-lookup"><span data-stu-id="08d9d-123">**TypeConversionMode**</span></span>  
 <span data-ttu-id="08d9d-124">이 속성을 `Allowed`로 설정하면 SQL 실행 태스크는 출력 매개 변수와 쿼리 결과를 결과가 할당되는 변수의 데이터 형식으로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="08d9d-124">When you set this property to `Allowed`, the Execute SQL Task will attempt to convert output parameter and query results to the data type of the variable the results are assigned to.</span></span> <span data-ttu-id="08d9d-125">이는 **단일 행** 결과 집합 유형에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="08d9d-125">This applies to the **Single row** result set type.</span></span>  
  
 <span data-ttu-id="08d9d-126">**ResultSet**</span><span class="sxs-lookup"><span data-stu-id="08d9d-126">**ResultSet**</span></span>  
 <span data-ttu-id="08d9d-127">실행 중인 SQL 문에서 예상하는 결과 유형을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="08d9d-127">Specify the result type expected by the SQL statement being run.</span></span> <span data-ttu-id="08d9d-128">**단일 행**, **전체 결과 집합**, **XML**또는 **없음**중에서 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="08d9d-128">Choose among **Single row**, **Full result set**, **XML**, or **None**.</span></span>  
  
 <span data-ttu-id="08d9d-129">**ConnectionType**</span><span class="sxs-lookup"><span data-stu-id="08d9d-129">**ConnectionType**</span></span>  
 <span data-ttu-id="08d9d-130">데이터 원본에 연결할 때 사용할 연결 관리자 유형을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="08d9d-130">Choose the type of connection manager to use to connect to the data source.</span></span> <span data-ttu-id="08d9d-131">사용 가능한 연결 형식에는 **OLE DB**, **ODBC**, **ADO**, **ADO.NET** 및 **SQLMOBILE**이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="08d9d-131">Available connection types include **OLE DB**, **ODBC**, **ADO**, **ADO.NET** and **SQLMOBILE**.</span></span>  
  
 <span data-ttu-id="08d9d-132">**관련 항목:** [OLE DB 연결 관리자](connection-manager/ole-db-connection-manager.md), [ODBC 연결 관리자](connection-manager/odbc-connection-manager.md), [ADO 연결 관리자](connection-manager/ado-connection-manager.md), [ADO.NET 연결 관리자](connection-manager/ado-net-connection-manager.md), [SQL Server Compact Edition 연결 관리자](connection-manager/sql-server-compact-edition-connection-manager.md)</span><span class="sxs-lookup"><span data-stu-id="08d9d-132">**Related Topics:** [OLE DB Connection Manager](connection-manager/ole-db-connection-manager.md), [ODBC Connection Manager](connection-manager/odbc-connection-manager.md), [ADO Connection Manager](connection-manager/ado-connection-manager.md), [ADO.NET Connection Manager](connection-manager/ado-net-connection-manager.md), [SQL Server Compact Edition Connection Manager](connection-manager/sql-server-compact-edition-connection-manager.md)</span></span>  
  
 <span data-ttu-id="08d9d-133">**연결**</span><span class="sxs-lookup"><span data-stu-id="08d9d-133">**Connection**</span></span>  
 <span data-ttu-id="08d9d-134">정의된 연결 관리자 목록에서 연결을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="08d9d-134">Choose the connection from a list of defined connection managers.</span></span> <span data-ttu-id="08d9d-135">새 연결을 설정하려면 \<**New connection...**>을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="08d9d-135">To create a new connection, select \<**New connection...**>.</span></span>  
  
 <span data-ttu-id="08d9d-136">**SQLSourceType**</span><span class="sxs-lookup"><span data-stu-id="08d9d-136">**SQLSourceType**</span></span>  
 <span data-ttu-id="08d9d-137">태스크에서 실행하는 SQL 문의 원본 유형을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="08d9d-137">Select the source type of the SQL statement that the task runs.</span></span>  
  
 <span data-ttu-id="08d9d-138">SQL 실행 태스크에서 사용하는 연결 관리자 유형에 따라 매개 변수가 있는 SQL 문에서 특정 매개 변수 표식을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="08d9d-138">Depending on the connection manager type that Execute SQL task uses, you must use specific parameter markers in parameterized SQL statements.</span></span>  
  
 <span data-ttu-id="08d9d-139">**관련 항목:**[SQL 실행 태스크](control-flow/execute-sql-task.md)</span><span class="sxs-lookup"><span data-stu-id="08d9d-139">**Related Topics:** Running Parameterized SQL Commands section in [Execute SQL Task](control-flow/execute-sql-task.md)</span></span>  
  
 <span data-ttu-id="08d9d-140">이 속성의 옵션은 다음 표에 나열되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="08d9d-140">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="08d9d-141">값</span><span class="sxs-lookup"><span data-stu-id="08d9d-141">Value</span></span>|<span data-ttu-id="08d9d-142">Description</span><span class="sxs-lookup"><span data-stu-id="08d9d-142">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="08d9d-143">**직접 입력**</span><span class="sxs-lookup"><span data-stu-id="08d9d-143">**Direct input**</span></span>|<span data-ttu-id="08d9d-144">원본을 Transact-SQL 문으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="08d9d-144">Set the source to a Transact-SQL statement.</span></span> <span data-ttu-id="08d9d-145">이 값을 선택하면 동적 옵션 **SQLStatement**가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="08d9d-145">Selecting this value displays the dynamic option, **SQLStatement**.</span></span>|  
|<span data-ttu-id="08d9d-146">**파일 연결**</span><span class="sxs-lookup"><span data-stu-id="08d9d-146">**File connection**</span></span>|<span data-ttu-id="08d9d-147">Transact-SQL 문이 포함된 파일을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="08d9d-147">Select a file that contains a Transact-SQL statement.</span></span> <span data-ttu-id="08d9d-148">이 옵션을 설정하면 동적 옵션 **FileConnection**이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="08d9d-148">Setting this option displays the dynamic option, **FileConnection**.</span></span>|  
|<span data-ttu-id="08d9d-149">**변수**</span><span class="sxs-lookup"><span data-stu-id="08d9d-149">**Variable**</span></span>|<span data-ttu-id="08d9d-150">원본을 Transact-SQL 문을 정의하는 변수로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="08d9d-150">Set the source to a variable that defines the Transact-SQL statement.</span></span> <span data-ttu-id="08d9d-151">이 값을 선택하면 동적 옵션 **SourceVariable**이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="08d9d-151">Selecting this value displays the dynamic option, **SourceVariable**.</span></span>|  
  
 <span data-ttu-id="08d9d-152">**QueryIsStoredProcedure**</span><span class="sxs-lookup"><span data-stu-id="08d9d-152">**QueryIsStoredProcedure**</span></span>  
 <span data-ttu-id="08d9d-153">실행하도록 지정한 SQL 문이 저장 프로시저인지 여부를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="08d9d-153">Indicates whether the specified SQL statement to be run is a stored procedure.</span></span> <span data-ttu-id="08d9d-154">이 속성은 태스크에서 ADO 연결 관리자를 사용하는 경우에만 읽기/쓰기가 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="08d9d-154">This property is read/write only if the task uses the ADO connection manager.</span></span> <span data-ttu-id="08d9d-155">그렇지 않은 경우 읽기 전용이고 값은 `false`입니다.</span><span class="sxs-lookup"><span data-stu-id="08d9d-155">Otherwise the property is read-only and its value is `false`.</span></span>  
  
 <span data-ttu-id="08d9d-156">**BypassPrepare**</span><span class="sxs-lookup"><span data-stu-id="08d9d-156">**BypassPrepare**</span></span>  
 <span data-ttu-id="08d9d-157">SQL 문의 준비 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="08d9d-157">Indicate whether the SQL statement is prepared.</span></span>  <span data-ttu-id="08d9d-158">`true`이면 준비를 건너뛰고 `false`이면 SQL 문을 실행하기 전에 SQL 문을 준비합니다.</span><span class="sxs-lookup"><span data-stu-id="08d9d-158">`true` skips preparation; `false` prepares the SQL statement before running it.</span></span> <span data-ttu-id="08d9d-159">이 옵션은 준비를 지원하는 OLE DB 연결에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="08d9d-159">This option is available only with OLE DB connections that support preparation.</span></span>  
  
 <span data-ttu-id="08d9d-160">**관련 항목:**  [준비된 실행](../relational-databases/native-client-odbc-queries/executing-statements/prepared-execution.md)</span><span class="sxs-lookup"><span data-stu-id="08d9d-160">**Related Topics:**  [Prepared Execution](../relational-databases/native-client-odbc-queries/executing-statements/prepared-execution.md)</span></span>  
  
 <span data-ttu-id="08d9d-161">**찾아보기**</span><span class="sxs-lookup"><span data-stu-id="08d9d-161">**Browse**</span></span>  
 <span data-ttu-id="08d9d-162">**열기** 대화 상자를 사용하여 SQL 문이 포함된 파일을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="08d9d-162">Locate a file that contains a SQL statement by using the **Open** dialog box.</span></span> <span data-ttu-id="08d9d-163">해당 내용을 **SQLStatement** 속성에 SQL 문으로 복사할 파일을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="08d9d-163">Select a file to copy the contents of the file as a SQL statement into the **SQLStatement** property.</span></span>  
  
 <span data-ttu-id="08d9d-164">**쿼리 작성**</span><span class="sxs-lookup"><span data-stu-id="08d9d-164">**Build Query**</span></span>  
 <span data-ttu-id="08d9d-165">쿼리를 만들 때 사용하는 그래픽 도구인 **쿼리 작성기** 대화 상자를 사용하여 SQL 문을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="08d9d-165">Create an SQL statement using the **Query Builder** dialog box, a graphical tool used to create queries.</span></span> <span data-ttu-id="08d9d-166">이 옵션은 **SQLSourceType** 옵션을 **직접 입력**으로 설정한 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="08d9d-166">This option is available when the **SQLSourceType** option is set to **Direct input**.</span></span>  
  
 <span data-ttu-id="08d9d-167">**쿼리 구문 분석**</span><span class="sxs-lookup"><span data-stu-id="08d9d-167">**Parse Query**</span></span>  
 <span data-ttu-id="08d9d-168">SQL 문의 구문 유효성을 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="08d9d-168">Validate the syntax of the SQL statement.</span></span>  
  
## <a name="sqlsourcetype-dynamic-options"></a><span data-ttu-id="08d9d-169">SQLSourceType 동적 옵션</span><span class="sxs-lookup"><span data-stu-id="08d9d-169">SQLSourceType Dynamic Options</span></span>  
  
### <a name="sqlsourcetype--direct-input"></a><span data-ttu-id="08d9d-170">SQLSourceType = 직접 입력</span><span class="sxs-lookup"><span data-stu-id="08d9d-170">SQLSourceType = Direct input</span></span>  
 <span data-ttu-id="08d9d-171">**SQLStatement**</span><span class="sxs-lookup"><span data-stu-id="08d9d-171">**SQLStatement**</span></span>  
 <span data-ttu-id="08d9d-172">실행할 SQL 문을 옵션 상자에 입력하거나, 찾아보기 단추(...)를 클릭하여 **SQL 쿼리 입력** 대화 상자에 SQL 문을 입력하거나, **쿼리 작성**을 클릭하고 **쿼리 작성기** 대화 상자를 사용하여 SQL 문을 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="08d9d-172">Type the SQL statement to execute in the option box, or click the browse button (...) to type the SQL statement in the **Enter SQL Query** dialog box, or click **Build Query** to compose the statement using the **Query Builder** dialog box.</span></span>  
  
 <span data-ttu-id="08d9d-173">**관련 항목:** [쿼리 작성기](../../2014/integration-services/query-builder.md)</span><span class="sxs-lookup"><span data-stu-id="08d9d-173">**Related Topics:** [Query Builder](../../2014/integration-services/query-builder.md)</span></span>  
  
### <a name="sqlsourcetype--file-connection"></a><span data-ttu-id="08d9d-174">SQLSourceType = 파일 연결</span><span class="sxs-lookup"><span data-stu-id="08d9d-174">SQLSourceType = File connection</span></span>  
 <span data-ttu-id="08d9d-175">**FileConnection**</span><span class="sxs-lookup"><span data-stu-id="08d9d-175">**FileConnection**</span></span>  
 <span data-ttu-id="08d9d-176">기존 파일 연결 관리자를 선택하거나 \<**New connection...**>을 클릭하여 새 연결 관리자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="08d9d-176">Select an existing File connection manager, or click \<**New connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="08d9d-177">**관련 항목:** [파일 연결 관리자](connection-manager/file-connection-manager.md), [파일 연결 관리자 편집기](../../2014/integration-services/file-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="08d9d-177">**Related Topics:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)</span></span>  
  
### <a name="sqlsourcetype--variable"></a><span data-ttu-id="08d9d-178">SQLSourceType = 변수</span><span class="sxs-lookup"><span data-stu-id="08d9d-178">SQLSourceType = Variable</span></span>  
 <span data-ttu-id="08d9d-179">**SourceVariable**</span><span class="sxs-lookup"><span data-stu-id="08d9d-179">**SourceVariable**</span></span>  
 <span data-ttu-id="08d9d-180">기존 변수를 선택하거나 \<**New variable...**>를 클릭하여 새 변수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="08d9d-180">Select an existing variable, or click \<**New variable...**> to create a new variable.</span></span>  
  
 <span data-ttu-id="08d9d-181">**관련 항목:** [Integration Services&#40;SSIS&#41; 변수](integration-services-ssis-variables.md), [변수 추가](../../2014/integration-services/add-variable.md)</span><span class="sxs-lookup"><span data-stu-id="08d9d-181">**Related Topics:** [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), [Add Variable](../../2014/integration-services/add-variable.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08d9d-182">참고 항목</span><span class="sxs-lookup"><span data-stu-id="08d9d-182">See Also</span></span>  
 <span data-ttu-id="08d9d-183">[Integration Services 오류 및 메시지 참조](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="08d9d-183">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="08d9d-184">[SQL 실행 태스크 편집기 &#40;매개 변수 매핑 페이지&#41;](../../2014/integration-services/execute-sql-task-editor-parameter-mapping-page.md) </span><span class="sxs-lookup"><span data-stu-id="08d9d-184">[Execute SQL Task Editor &#40;Parameter Mapping Page&#41;](../../2014/integration-services/execute-sql-task-editor-parameter-mapping-page.md) </span></span>  
 [<span data-ttu-id="08d9d-185">SQL 실행 태스크 편집기 &#40;결과 집합 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="08d9d-185">Execute SQL Task Editor &#40;Result Set Page&#41;</span></span>](../../2014/integration-services/execute-sql-task-editor-result-set-page.md)  
  
  
