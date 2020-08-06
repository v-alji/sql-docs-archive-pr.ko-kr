---
title: 데이터베이스 엔진 쿼리 편집기
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.swb.tsqlquery.f1
dev_langs:
- TSQL
helpviewer_keywords:
- Query Editor [Database Engine]
- Transact-SQL Editor See Query Editor [Database Engine]
- Database Engine Query Editor See Query Editor [Database Engine]
- Query Editor [Database Engine], Toolbar
- editors [SQL Server Management Studio], Database Engine Query Editor
- Query Editor [Database Engine], Features
- SQL Server Management Studio [SQL Server], Database Engine Query Editor
ms.assetid: 05cfae9b-96d5-4a35-a098-0bc3a548bcfc
author: rothja
ms.author: jroth
ms.openlocfilehash: 4dcb4298ec55181ea3c979228e8decf681483f74
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638636"
---
# <a name="database-engine-query-editor-sql-server-management-studio"></a><span data-ttu-id="7ea23-102">데이터베이스 엔진 쿼리 편집기(SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="7ea23-102">Database Engine Query Editor (SQL Server Management Studio)</span></span>
  <span data-ttu-id="7ea23-103">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 쿼리 편집기를 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문을 포함하는 스크립트를 만들고 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ea23-103">Use the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor to create and run scripts containing [!INCLUDE[tsql](../../includes/tsql-md.md)] statements.</span></span> <span data-ttu-id="7ea23-104">또한 편집기는 **sqlcmd** 명령을 포함하는 스크립트 실행을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="7ea23-104">The editor also supports running scripts that contain **sqlcmd** commands.</span></span>  
  
## <a name="transact-sql-f1-help"></a><span data-ttu-id="7ea23-105">Transact-SQL F1 도움말</span><span class="sxs-lookup"><span data-stu-id="7ea23-105">Transact-SQL F1 Help</span></span>  
 <span data-ttu-id="7ea23-106">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 쿼리 편집기는 F1 키를 선택할 때 특정 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문에 대한 참조 항목을 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ea23-106">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor supports linking you to the reference topic for a specific [!INCLUDE[tsql](../../includes/tsql-md.md)] statement when you select F1.</span></span> <span data-ttu-id="7ea23-107">이렇게 하려면 Transact-SQL 문의 이름을 강조 표시하고 F1 키를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="7ea23-107">To do so, highlight the name of a Transact-SQL statement and then select F1.</span></span> <span data-ttu-id="7ea23-108">그러면 도움말 검색 엔진에서 강조 표시된 문자열과 일치하는 F1 도움말 특성을 가진 항목을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="7ea23-108">The help search engine will then search for a topic that has an F1 help attribute that matches the string you highlighted.</span></span>  
  
 <span data-ttu-id="7ea23-109">도움말 검색 엔진에서 강조 표시된 문자열과 정확히 일치하는 F1 도움말 키워드를 포함하는 항목을 찾을 수 없을 경우 이 항목이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ea23-109">If the help search engine does not find a topic with an F1 help keyword that exactly matches the string you highlighted, then this topic is displayed.</span></span> <span data-ttu-id="7ea23-110">이 경우 다음과 같은 두 가지 방법으로 원하는 도움말을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ea23-110">In that case, there are two approaches to finding the help you are looking for:</span></span>  
  
-   <span data-ttu-id="7ea23-111">편집기에서 선택한 문자열을 복사한 다음 SQL Server 온라인 설명서의 검색 탭에 붙여 넣고 검색을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="7ea23-111">Copy and paste the editor string you highlighted into the search tab of SQL Server Books Online and do a search.</span></span>  
  
-   <span data-ttu-id="7ea23-112">항목에 적용되는 F 도움말 키워드와 일치할 것으로 예상되는 Transact-SQL 문 부분만 선택한 다음 F1 키를 다시 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="7ea23-112">Highlight only the part of the Transact-SQL statement likely to match an F1 help keyword applied to a topic and select F1 again.</span></span> <span data-ttu-id="7ea23-113">그러면 검색 엔진에서 강조 표시된 문자열과 항목에 할당된 F1 도움말 키워드를 정확하게 일치시킵니다.</span><span class="sxs-lookup"><span data-stu-id="7ea23-113">The search engine requires an exact match between the string you highlighted and an F1 help keyword assigned to a topic.</span></span> <span data-ttu-id="7ea23-114">강조 표시된 문자열에 열이나 매개 변수 이름과 같이 사용자 환경 고유의 요소가 포함되어 있을 경우 검색 엔진에서 일치하는 항목을 찾을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7ea23-114">If the string you highlighted contains elements unique to your environment, such as column or parameter names, the search engine will not get a match.</span></span> <span data-ttu-id="7ea23-115">선택할 수 있는 문자열의 예는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="7ea23-115">Examples of the strings to highlight include:</span></span>  
  
    -   <span data-ttu-id="7ea23-116">SELECT, CREATE DATABASE, BEGIN TRANSACTION 등의 Transact-SQL 문 이름</span><span class="sxs-lookup"><span data-stu-id="7ea23-116">The name of a Transact-SQL statement, such as SELECT, CREATE DATABASE or BEGIN TRANSACTION.</span></span>  
  
    -   <span data-ttu-id="7ea23-117">SERVERPROPERTY, @@VERSION 등의 기본 제공 함수 이름</span><span class="sxs-lookup"><span data-stu-id="7ea23-117">The name of a built-in function, such as SERVERPROPERTY, or @@VERSION.</span></span>  
  
    -   <span data-ttu-id="7ea23-118">sys.data_spaces, sp_tableoption 등의 시스템 저장 프로시저 테이블 또는 뷰 이름</span><span class="sxs-lookup"><span data-stu-id="7ea23-118">The name of a system stored procedure table, or view, such as sys.data_spaces or sp_tableoption.</span></span>  
  
## <a name="working-with-the-database-engine-query-editor"></a><span data-ttu-id="7ea23-119">데이터베이스 엔진 쿼리 편집기 작업</span><span class="sxs-lookup"><span data-stu-id="7ea23-119">Working With the Database Engine Query Editor</span></span>  
 <span data-ttu-id="7ea23-120">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 쿼리 편집기는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 구현되는 네 가지 편집기 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="7ea23-120">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor is one of four editors implemented in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="7ea23-121">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 쿼리 편집기에서 구현되는 기능과 이 편집기를 사용하여 수행할 수 있는 주요 태스크에 대한 자세한 내용은 [쿼리 및 텍스트 편집기&#40;SQL Server Management Studio&#41;](../scripting/query-and-text-editors-sql-server-management-studio.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7ea23-121">For a description of the functionality implemented in the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor and the main tasks you can perform using the editor, see [Query and Text Editors &#40;SQL Server Management Studio&#41;](../scripting/query-and-text-editors-sql-server-management-studio.md).</span></span>  
  
## <a name="sql-editor-toolbar"></a><span data-ttu-id="7ea23-122">SQL 편집기 도구 모음</span><span class="sxs-lookup"><span data-stu-id="7ea23-122">SQL Editor Toolbar</span></span>  
 <span data-ttu-id="7ea23-123">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 쿼리 편집기가 열려 있으면 다음 단추를 포함하는 SQL 편집기 도구 모음이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ea23-123">When the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor is open, the SQL Editor toolbar appears with the following buttons.</span></span>  
  
 <span data-ttu-id="7ea23-124">**연결**</span><span class="sxs-lookup"><span data-stu-id="7ea23-124">**Connect**</span></span>  
 <span data-ttu-id="7ea23-125">**서버에 연결** 대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="7ea23-125">Opens the **Connect to Server** dialog box.</span></span> <span data-ttu-id="7ea23-126">이 대화 상자를 사용하여 서버에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="7ea23-126">Use this dialog box to establish a connection to a server.</span></span>  
  
 <span data-ttu-id="7ea23-127">**연결 끊기**</span><span class="sxs-lookup"><span data-stu-id="7ea23-127">**Disconnect**</span></span>  
 <span data-ttu-id="7ea23-128">현재 쿼리 편집기와 서버 간의 연결을 끊습니다.</span><span class="sxs-lookup"><span data-stu-id="7ea23-128">Disconnects the current Query Editor from the server.</span></span>  
  
 <span data-ttu-id="7ea23-129">**연결 변경**</span><span class="sxs-lookup"><span data-stu-id="7ea23-129">**Change Connection**</span></span>  
 <span data-ttu-id="7ea23-130">**서버에 연결** 대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="7ea23-130">Opens the **Connect to Server** dialog box.</span></span> <span data-ttu-id="7ea23-131">이 대화 상자를 사용하여 다른 서버에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="7ea23-131">Use this dialog box to establish a connection to a different server.</span></span>  
  
 <span data-ttu-id="7ea23-132">**현재 연결에서의 새 쿼리**</span><span class="sxs-lookup"><span data-stu-id="7ea23-132">**New Query with Current Connection**</span></span>  
 <span data-ttu-id="7ea23-133">새 쿼리 편집기 창을 열고 현재 쿼리 편집기 창의 연결 정보를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="7ea23-133">Opens a new Query Editor window and uses the connection information from the current Query Editor window.</span></span>  
  
 <span data-ttu-id="7ea23-134">**사용 가능한 데이터베이스**</span><span class="sxs-lookup"><span data-stu-id="7ea23-134">**Available Databases**</span></span>  
 <span data-ttu-id="7ea23-135">같은 서버의 다른 데이터베이스로 연결을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="7ea23-135">Change the connection to a different database on the same server.</span></span>  
  
 <span data-ttu-id="7ea23-136">**실행**</span><span class="sxs-lookup"><span data-stu-id="7ea23-136">**Execute**</span></span>  
 <span data-ttu-id="7ea23-137">선택한 코드를 실행하거나, 코드를 선택하지 않은 경우 쿼리 편집기에 있는 모든 코드를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="7ea23-137">Executes the selected code or, if no code is selected, executes all the code in the Query Editor.</span></span>  
  
 <span data-ttu-id="7ea23-138">**디버그**</span><span class="sxs-lookup"><span data-stu-id="7ea23-138">**Debug**</span></span>  
 <span data-ttu-id="7ea23-139">[!INCLUDE[tsql](../../includes/tsql-md.md)] 디버거를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="7ea23-139">Enables the [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger.</span></span> <span data-ttu-id="7ea23-140">이 디버거에서는 중단점 설정, 변수 조사 및 단계별 코드 실행과 같은 디버깅 동작을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="7ea23-140">This debugger supports debugging actions such as setting breakpoints, watching variables, and stepping through code.</span></span>  
  
 <span data-ttu-id="7ea23-141">**쿼리 실행 취소**</span><span class="sxs-lookup"><span data-stu-id="7ea23-141">**Cancel Executing Query**</span></span>  
 <span data-ttu-id="7ea23-142">취소 요청을 서버로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="7ea23-142">Sends a cancellation request to the server.</span></span> <span data-ttu-id="7ea23-143">일부 쿼리는 바로 취소할 수 없으며 적절한 취소 조건이 될 때까지 기다려야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ea23-143">Some queries cannot be canceled immediately, but must wait for a suitable cancellation condition.</span></span> <span data-ttu-id="7ea23-144">트랜잭션을 취소해도 트랜잭션이 롤백되는 동안 작업이 지연될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ea23-144">When transactions are canceled, delays might occur while transactions are rolled back.</span></span>  
  
 <span data-ttu-id="7ea23-145">**Parse**</span><span class="sxs-lookup"><span data-stu-id="7ea23-145">**Parse**</span></span>  
 <span data-ttu-id="7ea23-146">선택한 코드의 구문을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="7ea23-146">Check the syntax of the selected code.</span></span> <span data-ttu-id="7ea23-147">코드를 선택하지 않은 경우 쿼리 편집기 창에 있는 모든 코드의 구문을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="7ea23-147">If no code is selected, checks the syntax of the all code in the Query Editor window.</span></span>  
  
 <span data-ttu-id="7ea23-148">**예상 실행 계획 표시**</span><span class="sxs-lookup"><span data-stu-id="7ea23-148">**Display Estimated Execution Plan**</span></span>  
 <span data-ttu-id="7ea23-149">쿼리를 실제로 실행하지 않고 쿼리 프로세서에서 쿼리 실행 계획을 요청한 다음 **실행 계획** 창에 계획을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="7ea23-149">Requests a query execution plan from the query processor without actually executing the query, and displays the plan in the **Execution plan** window.</span></span> <span data-ttu-id="7ea23-150">이 계획은 각 쿼리 부분을 실행하는 중 반환될 것으로 예상되는 행 수의 예측으로 인덱스 통계를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="7ea23-150">This plan uses index statistics as an estimate of the number of rows that are expected to be returned during each part of the query execution.</span></span> <span data-ttu-id="7ea23-151">실제 사용되는 쿼리 계획은 예상 실행 계획과 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ea23-151">The actual query plan that is used can be different from the estimated execution plan.</span></span> <span data-ttu-id="7ea23-152">이러한 차이는 반환되는 행 수가 예상치와 크게 다를 경우에 발생할 수 있으며, 쿼리 프로세서는 쿼리 계획을 더 효율적으로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="7ea23-152">This can occur if the number of rows that are returned is significantly different from the estimate, and the query processor changes the plan to be more efficient.</span></span>  
  
 <span data-ttu-id="7ea23-153">**쿼리 옵션**</span><span class="sxs-lookup"><span data-stu-id="7ea23-153">**Query Options**</span></span>  
 <span data-ttu-id="7ea23-154">**쿼리 옵션** 대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="7ea23-154">Opens the **Query Options** dialog box.</span></span> <span data-ttu-id="7ea23-155">이 대화 상자를 사용하여 쿼리 실행 및 쿼리 결과에 대한 기본 옵션을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="7ea23-155">Use this dialog box to configure the default options for query execution and for query results.</span></span>  
  
 <span data-ttu-id="7ea23-156">**IntelliSense 사용**</span><span class="sxs-lookup"><span data-stu-id="7ea23-156">**IntelliSense Enabled**</span></span>  
 <span data-ttu-id="7ea23-157">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 쿼리 편집기에서 IntelliSense 기능을 사용할지를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="7ea23-157">Specifies whether IntelliSense functionality is available in the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor.</span></span>  
  
 <span data-ttu-id="7ea23-158">**실제 실행 계획 포함**</span><span class="sxs-lookup"><span data-stu-id="7ea23-158">**Include Actual Execution Plan**</span></span>  
 <span data-ttu-id="7ea23-159">쿼리를 실행한 후 쿼리 결과와 쿼리에 사용된 실행 계획을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="7ea23-159">Executes the query, returns the query results, and the execution plan that was used for the query.</span></span> <span data-ttu-id="7ea23-160">이러한 결과는 **실행 계획** 창에 그래픽 쿼리 계획으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ea23-160">These appear as a graphical query plan in the **Execution plan** window.</span></span>  
  
 <span data-ttu-id="7ea23-161">**클라이언트 통계 포함**</span><span class="sxs-lookup"><span data-stu-id="7ea23-161">**Include Client Statistics**</span></span>  
 <span data-ttu-id="7ea23-162">쿼리 통계와 네트워크 패킷 통계 및 쿼리 경과 시간이 표시된 **클라이언트 통계** 창을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="7ea23-162">Includes a **Client Statistics** window that contains statistics about the query and about the network packets, and the elapsed time of the query.</span></span>  
  
 <span data-ttu-id="7ea23-163">**텍스트로 결과 표시**</span><span class="sxs-lookup"><span data-stu-id="7ea23-163">**Results to Text**</span></span>  
 <span data-ttu-id="7ea23-164">쿼리 결과를 텍스트로 **결과** 창에 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="7ea23-164">Returns the query results as text in the **Results** window.</span></span>  
  
 <span data-ttu-id="7ea23-165">**표 형태로 결과 표시**</span><span class="sxs-lookup"><span data-stu-id="7ea23-165">**Results to Grid**</span></span>  
 <span data-ttu-id="7ea23-166">쿼리 결과를 하나 이상의 표로 **결과** 창에 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="7ea23-166">Returns the query results as one or more grids in the **Results** window.</span></span>  
  
 <span data-ttu-id="7ea23-167">**파일로 결과 저장**</span><span class="sxs-lookup"><span data-stu-id="7ea23-167">**Results to File**</span></span>  
 <span data-ttu-id="7ea23-168">쿼리를 실행하면 **결과 저장** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="7ea23-168">When the query executes, the **Save Results** dialog box opens.</span></span> <span data-ttu-id="7ea23-169">**저장 위치**에서 파일을 저장할 폴더를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="7ea23-169">In **Save In**, select the folder in which you want to save the file.</span></span> <span data-ttu-id="7ea23-170">**파일 이름**에 파일 이름을 입력하고 **저장** 을 클릭하여 쿼리 결과를 확장명이 .rpt인 **보고서** 파일로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="7ea23-170">In **File name**, type the name of the file, and then click **Save** to save the query results as a **Report** file that has the .rpt extension.</span></span> <span data-ttu-id="7ea23-171">고급 옵션을 보려면 **저장** 단추의 아래쪽 화살표를 클릭한 다음 **인코딩하여 저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7ea23-171">For advanced options, click the down-arrow on the **Save** button, and then click **Save with Encoding**.</span></span>  
  
 <span data-ttu-id="7ea23-172">**선택 영역을 주석으로 처리**</span><span class="sxs-lookup"><span data-stu-id="7ea23-172">**Comment Selection**</span></span>  
 <span data-ttu-id="7ea23-173">줄의 시작 부분에 주석 기호(--)를 추가하여 현재 줄을 주석으로 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="7ea23-173">Makes the current line a comment by adding a comment operator (--) at the beginning of the line.</span></span>  
  
 <span data-ttu-id="7ea23-174">**선택 영역의 주석 처리 제거**</span><span class="sxs-lookup"><span data-stu-id="7ea23-174">**Uncomment Selection**</span></span>  
 <span data-ttu-id="7ea23-175">줄의 시작 부분에서 주석 기호(--)를 제거하여 현재 줄을 활성 소스 코드 문으로 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="7ea23-175">Makes the current line an active source statement by removing any comment operator (--) at the beginning of the line.</span></span>  
  
 <span data-ttu-id="7ea23-176">**줄 내어쓰기**</span><span class="sxs-lookup"><span data-stu-id="7ea23-176">**Decrease Line Indent**</span></span>  
 <span data-ttu-id="7ea23-177">줄의 시작 부분에서 공백을 제거하여 해당 줄의 텍스트를 왼쪽으로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="7ea23-177">Moves the text of the line to the left by removing blanks at the beginning of the line.</span></span>  
  
 <span data-ttu-id="7ea23-178">**줄 들여쓰기**</span><span class="sxs-lookup"><span data-stu-id="7ea23-178">**Increase Line Indent**</span></span>  
 <span data-ttu-id="7ea23-179">줄의 시작 부분에 공백을 추가하여 해당 줄의 텍스트를 오른쪽으로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="7ea23-179">Moves the text of the line to the right by adding blanks at the beginning of the line.</span></span>  
  
 <span data-ttu-id="7ea23-180">**템플릿 매개 변수 값 지정**</span><span class="sxs-lookup"><span data-stu-id="7ea23-180">**Specify Values for Template Parameters**</span></span>  
 <span data-ttu-id="7ea23-181">저장 프로시저 및 함수의 매개 변수 값을 지정하는 데 사용할 수 있는 대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="7ea23-181">Opens a dialog box that you can use to specify values for parameters in stored procedures and functions.</span></span>  
  
 <span data-ttu-id="7ea23-182">**보기** 메뉴를 선택하고 **도구 모음**을 선택한 다음 **SQL 편집기**를 선택하여 SQL 편집기 도구 모음을 추가할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ea23-182">You can also add the SQL Editor toolbar by selecting the **View** menu, selecting **Toolbars**, and then selecting **SQL Editor**.</span></span> <span data-ttu-id="7ea23-183">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 쿼리 편집기 창이 열려 있지 않을 때 SQL 편집기 도구 모음을 추가하면 일부 단추를 사용하지 못할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ea23-183">If you add the SQL Editor toolbar when no [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor windows are open, all the buttons are unavailable.</span></span>  
  
## <a name="sql-editor-toolbar"></a><span data-ttu-id="7ea23-184">SQL 편집기 도구 모음</span><span class="sxs-lookup"><span data-stu-id="7ea23-184">SQL Editor Toolbar</span></span>  
 <span data-ttu-id="7ea23-185">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 쿼리 편집기 창을 열면 **보기** 메뉴, **도구 모음**, **디버그**를 차례로 선택하여 디버그 도구 모음을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ea23-185">When a [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor window is open, you can add the Debug toolbar by selecting the **View** menu, selecting **Toolbars**, and then selecting **Debug**.</span></span> <span data-ttu-id="7ea23-186">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 쿼리 편집기 창이 열려 있지 않을 때 디버그 도구 모음을 추가하면 일부 단추를 사용하지 못할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ea23-186">If you add the Debug toolbar when no [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor windows are open, all the buttons are unavailable.</span></span>  
  
 <span data-ttu-id="7ea23-187">**Continue**</span><span class="sxs-lookup"><span data-stu-id="7ea23-187">**Continue**</span></span>  
 <span data-ttu-id="7ea23-188">중단점이 나올 때까지 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 쿼리 편집기 창에서 코드를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="7ea23-188">Runs the code in the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor window until a breakpoint is encountered.</span></span>  
  
 <span data-ttu-id="7ea23-189">**모두 중단**</span><span class="sxs-lookup"><span data-stu-id="7ea23-189">**Break All**</span></span>  
 <span data-ttu-id="7ea23-190">중단이 발생하면 디버거에 연결된 모든 프로세스를 중단하도록 디버거를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="7ea23-190">Sets the debugger to break all processes to which the debugger is attached when a break occurs.</span></span>  
  
 <span data-ttu-id="7ea23-191">**디버깅 중지**</span><span class="sxs-lookup"><span data-stu-id="7ea23-191">**Stop Debugging**</span></span>  
 <span data-ttu-id="7ea23-192">선택한 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 쿼리 편집기 창에서 디버그 모드를 종료하고 표준 실행 모드로 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="7ea23-192">Takes the selected [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor window out of debug mode, and restores the standard execution mode.</span></span>  
  
 <span data-ttu-id="7ea23-193">**다음 명령문 표시**</span><span class="sxs-lookup"><span data-stu-id="7ea23-193">**Show Next Statement**</span></span>  
 <span data-ttu-id="7ea23-194">커서를 실행할 다음 문으로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="7ea23-194">Moves the cursor to the next statement to be executed.</span></span>  
  
 <span data-ttu-id="7ea23-195">**한 단계씩 코드 실행**</span><span class="sxs-lookup"><span data-stu-id="7ea23-195">**Step Into**</span></span>  
 <span data-ttu-id="7ea23-196">다음 문이 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ea23-196">The next statement is run.</span></span> <span data-ttu-id="7ea23-197">문에서 Transact-SQL 저장 프로시저, 함수 또는 트리거를 호출하면 디버거에서 모듈 코드가 포함된 새 **쿼리 편집기** 창을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="7ea23-197">If the statement invokes a Transact-SQL stored procedure, function, or trigger, the debugger displays a new **Query Editor** window that contains the code of the module.</span></span> <span data-ttu-id="7ea23-198">창이 디버그 모드에 있으며 모듈의 첫 번째 문에서 실행이 일시 중지됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ea23-198">The window is in debug mode, and execution pauses on the first statement in the module.</span></span> <span data-ttu-id="7ea23-199">그리고 나서 중단점을 설정하거나 코드를 단계별로 실행하여 모듈을 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ea23-199">You can then move through the module, for example, by setting breakpoints or stepping through the code.</span></span>  
  
 <span data-ttu-id="7ea23-200">**프로시저 단위 실행**</span><span class="sxs-lookup"><span data-stu-id="7ea23-200">**Step Over**</span></span>  
 <span data-ttu-id="7ea23-201">다음 문이 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ea23-201">The next statement is run.</span></span> <span data-ttu-id="7ea23-202">문에서 Transact-SQL 저장 프로시저, 함수 또는 트리거를 호출하면 모듈이 완료될 때까지 실행되고 결과가 호출 코드에 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ea23-202">If the statement invokes a Transact-SQL stored procedure, function, or trigger, the module is run until it finishes and the results are returned to the calling code.</span></span> <span data-ttu-id="7ea23-203">모듈에 오류가 없으면 모듈을 프로시저 단위로 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ea23-203">If you are sure there are no errors in the module, you can step over it.</span></span> <span data-ttu-id="7ea23-204">이 경우 모듈 호출 이후의 문에서 실행이 일시 중지됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ea23-204">Execution pauses on the statement that follows the call to the module.</span></span>  
  
 <span data-ttu-id="7ea23-205">**프로시저 나가기**</span><span class="sxs-lookup"><span data-stu-id="7ea23-205">**Step Out**</span></span>  
 <span data-ttu-id="7ea23-206">다음으로 가장 높은 호출 수준(함수, 저장 프로시저 또는 트리거)으로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="7ea23-206">Step back to the next highest calling level (function, stored procedure, or trigger).</span></span> <span data-ttu-id="7ea23-207">저장 프로시저, 함수 또는 트리거를 호출한 후 문에서 실행이 일시 중지됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ea23-207">Execution pauses on the statement that follows the call to the stored procedure, function, or trigger.</span></span>  
  
 <span data-ttu-id="7ea23-208">**Windows**</span><span class="sxs-lookup"><span data-stu-id="7ea23-208">**Windows**</span></span>  
 <span data-ttu-id="7ea23-209">**중단점** 창 또는 **직접 실행** 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="7ea23-209">Opens either the **Breakpoint** window or the **Immediate** window.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ea23-210">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7ea23-210">See Also</span></span>  
 [<span data-ttu-id="7ea23-211">SQL Server Management Studio 바로 가기 키</span><span class="sxs-lookup"><span data-stu-id="7ea23-211">SQL Server Management Studio Keyboard Shortcuts</span></span>](../../ssms/sql-server-management-studio-keyboard-shortcuts.md)  
  
  
