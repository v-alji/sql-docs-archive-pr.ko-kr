---
title: SQL Server 연결 형식(SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 957e7091-e08f-48d2-9506-872227ae8b20
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 34a519c8a291dc351be98316b18a45ade4918579
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653226"
---
# <a name="sql-server-connection-type-ssrs"></a><span data-ttu-id="aab78-102">SQL Server 연결 형식(SSRS)</span><span class="sxs-lookup"><span data-stu-id="aab78-102">SQL Server Connection Type (SSRS)</span></span>
  <span data-ttu-id="aab78-103">보고서에 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스의 데이터를 포함하려면 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 형식의 보고서 데이터 원본을 기반으로 하는 데이터 세트가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="aab78-103">To include data from a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database in your report, you must have a dataset that is based on a report data source of type [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="aab78-104">이 기본 제공 데이터 원본 형식은 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터 확장 프로그램을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="aab78-104">This built-in data source type is based on the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data extension.</span></span> <span data-ttu-id="aab78-105">이 데이터 원본 유형을 사용하여 현재 버전 및 이전 버전의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스에 연결하고 이 데이터베이스에서 데이터를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aab78-105">Use this data source type to connect to and retrieve data from the current version and earlier versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases.</span></span>  
  
 <span data-ttu-id="aab78-106">이 데이터 확장 프로그램은 연결 문자열과 별개로 관리되는 다중값 매개 변수, 서버 집계 및 자격 증명을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="aab78-106">This data extension supports multivalue parameters, server aggregates, and credentials managed separately from the connection string.</span></span>  
  
 <span data-ttu-id="aab78-107">이 항목의 정보를 사용하여 데이터 원본을 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aab78-107">Use the information in this topic to build a data source.</span></span> <span data-ttu-id="aab78-108">단계별 지침은 [데이터 연결이 나 데이터 원본 &#40;추가 및 확인 보고서 작성기 및 SSRS&#41;](add-and-verify-a-data-connection-report-builder-and-ssrs.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="aab78-108">For step-by-step instructions, see [Add and Verify a Data Connection or Data Source &#40;Report Builder and SSRS&#41;](add-and-verify-a-data-connection-report-builder-and-ssrs.md).</span></span>  
  
##  <a name="connection-string"></a><a name="Connection"></a> <span data-ttu-id="aab78-109">연결 문자열</span><span class="sxs-lookup"><span data-stu-id="aab78-109">Connection String</span></span>  
 <span data-ttu-id="aab78-110">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스에 연결할 때는 서버에 있는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스의 데이터베이스 개체에 연결하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="aab78-110">When you connect to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database, you are connecting to the database object in an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on a server.</span></span> <span data-ttu-id="aab78-111">데이터베이스에는 여러 개의 테이블, 뷰 및 저장 프로시저가 있는 스키마가 여러 개 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aab78-111">The database might have multiple schemas that have multiple tables, views, and stored procedures.</span></span> <span data-ttu-id="aab78-112">쿼리 디자이너에서 사용할 데이터베이스 개체를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="aab78-112">You specify the database object to use in the query designer.</span></span> <span data-ttu-id="aab78-113">연결 문자열에 데이터베이스를 지정하지 않을 경우 데이터베이스 관리자가 할당한 기본 데이터베이스에 연결됩니다.</span><span class="sxs-lookup"><span data-stu-id="aab78-113">If you do not specify a database in the connection string, you connect to the default database that the database administrator assigned to you.</span></span>  
  
 <span data-ttu-id="aab78-114">데이터 원본 연결에 사용할 자격 증명 및 연결 정보는 데이터베이스 관리자에게 문의하십시오.</span><span class="sxs-lookup"><span data-stu-id="aab78-114">Contact your database administrator for connection information and for the credentials to use to connect to the data source.</span></span> <span data-ttu-id="aab78-115">다음 연결 문자열 예에서는 로컬 클라이언트에 있는 예제 데이터베이스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="aab78-115">The following connection string example specifies a sample database on the local client:</span></span>  
  
```  
Data Source=<server>;Initial Catalog=AdventureWorks  
```  
  
 <span data-ttu-id="aab78-116">연결 문자열 예제에 대한 자세한 내용은 [보고서 작성기의 데이터 연결, 데이터 원본 및 연결 문자열](../data-connections-data-sources-and-connection-strings-in-report-builder.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="aab78-116">For more information about connection string examples, see [Data Connections, Data Sources, and Connection Strings in Report Builder](../data-connections-data-sources-and-connection-strings-in-report-builder.md).</span></span>  
  
##  <a name="credentials"></a><a name="Credentials"></a> <span data-ttu-id="aab78-117">자격 증명</span><span class="sxs-lookup"><span data-stu-id="aab78-117">Credentials</span></span>  
 <span data-ttu-id="aab78-118">쿼리를 실행하거나 보고서를 로컬로 미리 보거나 보고서 서버의 보고서를 미리 보려면 자격 증명이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="aab78-118">Credentials are required to run queries, to preview the report locally, and to preview the report from the report server.</span></span>  
  
 <span data-ttu-id="aab78-119">보고서를 게시한 후 보고서를 보고서 서버에서 실행할 때 데이터를 검색할 수 있는 권한이 유효하도록 데이터 원본에 대한 자격 증명을 변경해야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aab78-119">After you publish your report, you may need to change the credentials for the data source so that when the report runs on the report server, the permissions to retrieve the data are valid.</span></span>  
  
 <span data-ttu-id="aab78-120">보고서 작성 클라이언트에서는 다음 옵션을 사용하여 자격 증명을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aab78-120">From a report authoring client, the following options are available to specify credentials:</span></span>  
  
-   <span data-ttu-id="aab78-121">현재 Windows 사용자(통합 보안)</span><span class="sxs-lookup"><span data-stu-id="aab78-121">Current Windows user (also known as integrated security).</span></span>  
  
-   <span data-ttu-id="aab78-122">저장된 사용자 이름 및 암호 사용.</span><span class="sxs-lookup"><span data-stu-id="aab78-122">Use a stored user name and password.</span></span>  
  
-   <span data-ttu-id="aab78-123">사용자에게 자격 증명을 입력하도록 메시지 표시</span><span class="sxs-lookup"><span data-stu-id="aab78-123">Prompt the user for credentials.</span></span> <span data-ttu-id="aab78-124">이 옵션은 Windows 통합 보안만 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="aab78-124">This option supports Windows integrated security only.</span></span>  
  
-   <span data-ttu-id="aab78-125">자격 증명 필요 없음.</span><span class="sxs-lookup"><span data-stu-id="aab78-125">No credentials are required.</span></span> <span data-ttu-id="aab78-126">이 옵션을 사용하려면 보고서 서버에서 무인 실행 계정을 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="aab78-126">To use this option, you must have the unattended execution account configured on the report server.</span></span> <span data-ttu-id="aab78-127">자세한 내용은 msdn.microsoft.com의 [Reporting Services 설명서](https://go.microsoft.com/fwlink/?linkid=121312)에서 [무인 실행 계정 구성&#40;SSRS 구성 관리자&#41;](../install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="aab78-127">For more information, see [Configure the Unattended Execution Account &#40;SSRS Configuration Manager&#41;](../install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md) in the [Reporting Services documentation](https://go.microsoft.com/fwlink/?linkid=121312) in on msdn.microsoft.com.</span></span>  
  
 <span data-ttu-id="aab78-128">자세한 내용은 [Reporting Services의 데이터 연결, 데이터 원본 및 연결 문자열](../data-connections-data-sources-and-connection-strings-in-reporting-services.md) 을 참조 하거나 [보고서 작성기에서 자격 증명을 지정](../specify-credentials-in-report-builder.md)하세요.</span><span class="sxs-lookup"><span data-stu-id="aab78-128">For more information, see [Data Connections, Data Sources, and Connection Strings in Reporting Services](../data-connections-data-sources-and-connection-strings-in-reporting-services.md) or [Specify Credentials in Report Builder](../specify-credentials-in-report-builder.md).</span></span>  
  
  
##  <a name="queries"></a><a name="Query"></a> <span data-ttu-id="aab78-129">쿼리</span><span class="sxs-lookup"><span data-stu-id="aab78-129">Queries</span></span>  
 <span data-ttu-id="aab78-130">쿼리는 보고서 데이터 세트에 대해 검색할 데이터를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="aab78-130">A query specifies which data to retrieve for a report dataset.</span></span> <span data-ttu-id="aab78-131">쿼리 결과 집합의 열은 데이터 세트의 필드 컬렉션을 채웁니다.</span><span class="sxs-lookup"><span data-stu-id="aab78-131">The columns in the result set for a query populate the field collection for a dataset.</span></span> <span data-ttu-id="aab78-132">보고서는 쿼리가 검색하는 첫 번째 결과 집합만 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="aab78-132">A report processes only the first result set that a query retrieves.</span></span>  
  
 <span data-ttu-id="aab78-133">기본적으로 그래픽 쿼리 디자이너에 나타낼 수 있는 새 쿼리를 만들거나 기존 쿼리를 열 경우 관계형 쿼리 디자이너를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aab78-133">By default, if you create a new query or open an existing query that can be represented in the graphical query designer, the relational query designer is available.</span></span> <span data-ttu-id="aab78-134">다음과 같은 방법으로 쿼리를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aab78-134">You can specify a query in the following ways:</span></span>  
  
-   <span data-ttu-id="aab78-135">대화식으로 쿼리를 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="aab78-135">Build a query interactively.</span></span> <span data-ttu-id="aab78-136">관계형 쿼리 디자이너를 사용합니다. 관계형 쿼리 디자이너는 테이블, 뷰, 저장 프로시저 및 기타 데이터베이스 항목을 데이터베이스 스키마별로 구성하여 계층 구조로 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="aab78-136">Use the relational query designer that displays a hierarchical view of tables, views, stored procedures, and other database items, organized by database schema.</span></span> <span data-ttu-id="aab78-137">테이블 또는 뷰에서 열을 선택하거나 저장 프로시저 또는 테이블 반환 함수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="aab78-137">Select columns from tables or views, or specify stored procedures or table-valued functions.</span></span> <span data-ttu-id="aab78-138">필터 조건을 지정하여 검색할 데이터 행 수를 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="aab78-138">Limit the number of rows of data to retrieve by specifying filter criteria.</span></span> <span data-ttu-id="aab78-139">매개 변수 옵션을 설정하여 보고서를 실행할 때 필터를 사용자 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="aab78-139">Customize the filter when the report runs by setting the parameter option.</span></span>  
  
-   <span data-ttu-id="aab78-140">쿼리를 입력하거나 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="aab78-140">Type or paste a query.</span></span> <span data-ttu-id="aab78-141">텍스트 기반 쿼리 디자이너를 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)] 텍스트를 직접 입력하거나, 다른 원본에서 쿼리 텍스트를 붙여넣거나, 관계형 쿼리 디자이너를 사용하여 작성할 수 없는 복잡한 쿼리를 입력하거나, 쿼리 기반 식을 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aab78-141">Use the text-based query designer to enter [!INCLUDE[tsql](../../includes/tsql-md.md)] text directly, to paste query text from another source, to enter complex queries that cannot be built by using the relational query designer, or to enter query-based expressions.</span></span>  
  
-   <span data-ttu-id="aab78-142">파일 또는 보고서에서 기존 쿼리를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="aab78-142">Import an existing query from a file or report.</span></span> <span data-ttu-id="aab78-143">쿼리 디자이너에서 쿼리 **가져오기** 단추를 사용하여 .sql 파일 또는 .rdl 파일을 찾아서 쿼리를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="aab78-143">Use the **Import** query button from either query designer to browse to a .sql file or .rdl file and import a query.</span></span>  
  
 <span data-ttu-id="aab78-144">자세한 내용은 [관계형 쿼리 디자이너 사용자 인터페이스&#40;보고서 작성기&#41;](relational-query-designer-user-interface-report-builder.md) 및 [텍스트 기반 쿼리 디자이너 사용자 인터페이스&#40;보고서 작성기&#41;](text-based-query-designer-user-interface-report-builder.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="aab78-144">For more information, see [Relational Query Designer User Interface &#40;Report Builder&#41;](relational-query-designer-user-interface-report-builder.md) and [Text-based Query Designer User Interface &#40;Report Builder&#41;](text-based-query-designer-user-interface-report-builder.md).</span></span>  
  
 <span data-ttu-id="aab78-145">지원되는 쿼리 모드는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="aab78-145">The following query modes are supported:</span></span>  
  
-   <span data-ttu-id="aab78-146">[Text](#QueryText)[!INCLUDE[tsql](../../includes/tsql-md.md)] 명령을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="aab78-146">[Text](#QueryText) Type in [!INCLUDE[tsql](../../includes/tsql-md.md)] commands.</span></span>  
  
-   <span data-ttu-id="aab78-147">[Stored Procedure](#QueryStoredProcedure) 저장 프로시저 목록에서 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="aab78-147">[Stored Procedure](#QueryStoredProcedure) Choose from a list of stored procedures.</span></span>  
  
###  <a name="using-query-type-text"></a><a name="QueryText"></a> <span data-ttu-id="aab78-148">Text 쿼리 유형 사용</span><span class="sxs-lookup"><span data-stu-id="aab78-148">Using Query Type Text</span></span>  
 <span data-ttu-id="aab78-149">텍스트 기반 쿼리 디자이너에서는 [!INCLUDE[tsql](../../includes/tsql-md.md)] 명령을 입력하여 데이터 세트의 데이터를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aab78-149">In the text-based query designer, you can type [!INCLUDE[tsql](../../includes/tsql-md.md)] commands to define the data in a dataset.</span></span> <span data-ttu-id="aab78-150">예를 들어 다음 [!INCLUDE[tsql](../../includes/tsql-md.md)] 쿼리는 마케팅 지원을 담당하는 모든 직원의 이름을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="aab78-150">For example, the following [!INCLUDE[tsql](../../includes/tsql-md.md)] query selects the names of all employees who are marketing assistants:</span></span>  
  
```  
SELECT  
  HumanResources.Employee.BusinessEntityID  
  ,HumanResources.Employee.JobTitle  
  ,Person.Person.FirstName  
  ,Person.Person.LastName  
FROM  
  Person.Person  
  INNER JOIN HumanResources.Employee  
    ON Person.Person.BusinessEntityID = HumanResources.Employee.BusinessEntityID  
WHERE HumanResources.Employee.JobTitle = 'Marketing Assistant'   
```  
  
 <span data-ttu-id="aab78-151">쿼리를 실행하고 결과 집합을 표시하려면 도구 모음에서 **실행** 단추( **!** )를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="aab78-151">Click the **Run** button (**!**) on the toolbar to run the query and display a result set.</span></span>  
  
 <span data-ttu-id="aab78-152">이 쿼리에서 매개 변수를 사용하려면 쿼리 매개 변수를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="aab78-152">To parameterize this query, add a query parameter.</span></span> <span data-ttu-id="aab78-153">예를 들어 WHERE 절을 다음과 같이 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="aab78-153">For example, change the WHERE clause to the following:</span></span>  
  
 `WHERE HumanResources.Employee.JobTitle = (@JobTitle)`  
  
 <span data-ttu-id="aab78-154">쿼리를 실행하면 쿼리 매개 변수에 해당하는 보고서 매개 변수가 자동으로 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="aab78-154">When you run the query, report parameters that correspond to query parameters are automatically created.</span></span> <span data-ttu-id="aab78-155">자세한 내용은 이 항목의 뒷부분에 나오는 [쿼리 매개 변수](#Parameters) 를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="aab78-155">For more information, see [Query Parameters](#Parameters) later in this topic.</span></span>  
  
  
###  <a name="using-query-type-storedprocedure"></a><a name="QueryStoredProcedure"></a> <span data-ttu-id="aab78-156">StoredProcedure 쿼리 유형 사용</span><span class="sxs-lookup"><span data-stu-id="aab78-156">Using Query Type StoredProcedure</span></span>  
 <span data-ttu-id="aab78-157">다음 중 한 가지 방법으로 데이터 세트 쿼리에 대해 저장 프로시저를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aab78-157">You can specify a stored procedure for a dataset query in one of the following ways:</span></span>  
  
-   <span data-ttu-id="aab78-158">**데이터 세트 속성** 대화 상자에서 **저장 프로시저** 옵션을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="aab78-158">In the **Dataset Properties** dialog box, set the **Stored Procedure** option.</span></span> <span data-ttu-id="aab78-159">저장 프로시저 및 테이블 반환 함수 드롭다운 목록에서 원하는 항목을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="aab78-159">Choose from the drop-down list of stored procedures and table-valued functions.</span></span>  
  
-   <span data-ttu-id="aab78-160">관계형 쿼리 디자이너에서는 데이터베이스 뷰 창에서 저장 프로시저 또는 테이블 반환 함수를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="aab78-160">In the relational query designer, in the Database view pane, select a stored procedure or table-valued function.</span></span>  
  
-   <span data-ttu-id="aab78-161">텍스트 기반 쿼리 디자이너에서는 도구 모음에서 **StoredProcedure** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="aab78-161">In the text-based query designer, select **StoredProcedure** from the toolbar.</span></span>  
  
 <span data-ttu-id="aab78-162">저장 프로시저나 테이블 반환 함수를 선택한 후 쿼리를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aab78-162">After you select a stored procedure or table-valued function, you can run the query.</span></span> <span data-ttu-id="aab78-163">입력 매개 변수 값을 입력하라는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="aab78-163">You will be prompted for input parameter values.</span></span> <span data-ttu-id="aab78-164">쿼리를 실행하면 입력 매개 변수에 해당하는 보고서 매개 변수가 자동으로 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="aab78-164">When you run the query, report parameters that correspond to input parameters are automatically created.</span></span> <span data-ttu-id="aab78-165">자세한 내용은 이 항목의 뒷부분에 나오는 [쿼리 매개 변수](#Parameters) 를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="aab78-165">For more information, see [Query Parameters](#Parameters) later in this topic.</span></span>  
  
 <span data-ttu-id="aab78-166">저장 프로시저의 경우 첫 번째로 검색된 결과 집합만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="aab78-166">Only the first result set that is retrieved for a stored procedure is supported.</span></span> <span data-ttu-id="aab78-167">저장 프로시저에서 여러 개의 결과 집합을 반환할 경우 첫 번째 결과 집합만 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="aab78-167">If a stored procedure returns multiple result sets, only the first one is used.</span></span>  
  
 <span data-ttu-id="aab78-168">저장 프로시저에 기본값을 사용하는 매개 변수가 있는 경우 매개 변수의 값으로 DEFAULT 키워드를 사용하여 해당 값에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aab78-168">If a stored procedure has a parameter that has a default value, you can access that value by using the DEFAULT keyword as a value for the parameter.</span></span> <span data-ttu-id="aab78-169">쿼리 매개 변수가 보고서 매개 변수에 연결되어 있으면 사용자가 보고서 매개 변수의 입력란에 DEFAULT라는 단어를 입력하거나 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aab78-169">If the query parameter is linked to a report parameter, the user can type or select the word DEFAULT in the input box for the report parameter.</span></span>  
  
 <span data-ttu-id="aab78-170">자세한 내용은 msdn.microsoft.com의 [SQL Server 온라인 설명서](https://go.microsoft.com/fwlink/?linkid=98335) 에서 "저장 프로시저(데이터베이스 엔진)"를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="aab78-170">For more information, see "Stored Procedures (Database Engine)" in [SQL Server Books Online](https://go.microsoft.com/fwlink/?linkid=98335) on msdn.microsoft.com.</span></span>  
  
  
##  <a name="parameters"></a><a name="Parameters"></a> <span data-ttu-id="aab78-171">매개 변수</span><span class="sxs-lookup"><span data-stu-id="aab78-171">Parameters</span></span>  
 <span data-ttu-id="aab78-172">쿼리 텍스트에 입력 매개 변수가 있는 쿼리 변수 또는 저장 프로시저가 포함된 경우 데이터 세트에 대한 해당 쿼리 매개 변수와 보고서에 대한 해당 보고서 매개 변수가 자동으로 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="aab78-172">When query text contains query variables or stored procedures that have input parameters, the corresponding query parameters for the dataset and report parameters for the report are automatically generated.</span></span> <span data-ttu-id="aab78-173">쿼리 텍스트는 각 쿼리 변수에 대한 DECLARE 문을 포함하지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="aab78-173">The query text must not include the DECLARE statement for each query variable.</span></span>  
  
 <span data-ttu-id="aab78-174">예를 들어 다음 SQL 쿼리는 `EmpID`라는 보고서 매개 변수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="aab78-174">For example, the following SQL query creates a report parameter named `EmpID`:</span></span>  
  
```  
SELECT FirstName, LastName FROM HumanResources.Employee E INNER JOIN  
       Person.Contact C ON  E.ContactID=C.ContactID   
WHERE EmployeeID = (@EmpID)  
```  
  
 <span data-ttu-id="aab78-175">보고서 매개 변수는 수정해야 할 수도 있는 기본 속성 값을 사용하여 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="aab78-175">Report parameters are created with default property values that you might need to modify.</span></span> <span data-ttu-id="aab78-176">다음은 그 예입니다.</span><span class="sxs-lookup"><span data-stu-id="aab78-176">For example:</span></span>  
  
-   <span data-ttu-id="aab78-177">기본적으로 각 보고서 매개 변수의 데이터 형식은 **Text**입니다.</span><span class="sxs-lookup"><span data-stu-id="aab78-177">By default, each report parameter is data type **Text**.</span></span> <span data-ttu-id="aab78-178">기본 데이터의 데이터 형식이 다르면 매개 변수 데이터 형식을 변경해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="aab78-178">If the underlying data is a different data type, you must change the parameter data type.</span></span>  
  
-   <span data-ttu-id="aab78-179">다중값 매개 변수에 대한 옵션을 선택한 경우 `IN`과 같이 `WHERE EmployeeID IN (@EmpID)` 연산자를 사용하여 값이 집합의 일부인지 여부를 테스트하도록 쿼리를 수동으로 변경해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="aab78-179">If you select the option for multivalued parameters, you must manually change the query to test whether values are part of a set by using the `IN` operator, for example, `WHERE EmployeeID IN (@EmpID)`.</span></span>  
  
 <span data-ttu-id="aab78-180">자세한 내용은 [보고서 매개 변수&#40;보고서 작성기 및 보고서 디자이너&#41;](../report-design/report-parameters-report-builder-and-report-designer.md)에 대해 자세히 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="aab78-180">For more information, see [Report Parameters &#40;Report Builder and Report Designer&#41;](../report-design/report-parameters-report-builder-and-report-designer.md).</span></span>  
  
  
##  <a name="remarks"></a><a name="Remarks"></a> <span data-ttu-id="aab78-181">주의</span><span class="sxs-lookup"><span data-stu-id="aab78-181">Remarks</span></span>  
 <span data-ttu-id="aab78-182">OLE DB 또는 ODBC 데이터 원본 유형을 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스에서 데이터를 검색할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aab78-182">You can also retrieve data from a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database by using an OLE DB or ODBC data source type.</span></span> <span data-ttu-id="aab78-183">자세한 내용은 [OLE DB 연결 형식&#40;SSRS&#41;](ole-db-connection-type-ssrs.md) 또는 [ODBC 연결 형식&#40;SSRS&#41;](odbc-connection-type-ssrs.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="aab78-183">For more information, see [OLE DB Connection Type &#40;SSRS&#41;](ole-db-connection-type-ssrs.md) or [ODBC Connection Type &#40;SSRS&#41;](odbc-connection-type-ssrs.md).</span></span>  
  
###### <a name="platform-and-version-information"></a><span data-ttu-id="aab78-184">플랫폼 및 버전 정보</span><span class="sxs-lookup"><span data-stu-id="aab78-184">Platform and Version Information</span></span>  
 <span data-ttu-id="aab78-185">플랫폼 및 버전 지원에 대한 자세한 내용은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [온라인 설명서](https://go.microsoft.com/fwlink/?linkid=121312)의 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 설명서에서 [Reporting Services&#40;SSRS&#41;에서 지원하는 데이터 원본](../create-deploy-and-manage-mobile-and-paginated-reports.md).</span><span class="sxs-lookup"><span data-stu-id="aab78-185">For more information about platform and version support, see [Data Sources Supported by Reporting Services &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md) in the [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] documentation in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?linkid=121312).</span></span>  
  
  
##  <a name="how-to-topics"></a><a name="HowTo"></a> <span data-ttu-id="aab78-186">방법 도움말 항목</span><span class="sxs-lookup"><span data-stu-id="aab78-186">How-To Topics</span></span>  
 <span data-ttu-id="aab78-187">이 섹션에서는 데이터 연결, 데이터 원본 및 데이터 세트를 사용하는 방법을 단계별로 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="aab78-187">This section contains step-by-step instructions for working with data connections, data sources, and datasets.</span></span>  
  
 [<span data-ttu-id="aab78-188">데이터 연결이 나 데이터 원본 &#40;보고서 작성기 및 SSRS를 추가 하 고 확인&#41;</span><span class="sxs-lookup"><span data-stu-id="aab78-188">Add and Verify a Data Connection or Data Source &#40;Report Builder and SSRS&#41;</span></span>](add-and-verify-a-data-connection-report-builder-and-ssrs.md)  
  
 [<span data-ttu-id="aab78-189">공유 데이터 세트 또는 포함된 데이터 세트 만들기&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="aab78-189">Create a Shared Dataset or Embedded Dataset &#40;Report Builder and SSRS&#41;</span></span>](create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md)  
  
 [<span data-ttu-id="aab78-190">데이터 세트에 필터 추가&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="aab78-190">Add a Filter to a Dataset &#40;Report Builder and SSRS&#41;</span></span>](add-a-filter-to-a-dataset-report-builder-and-ssrs.md)  
  
  
##  <a name="related-sections"></a><a name="Related"></a> <span data-ttu-id="aab78-191">관련 단원</span><span class="sxs-lookup"><span data-stu-id="aab78-191">Related Sections</span></span>  
 <span data-ttu-id="aab78-192">설명서의 다음 섹션에서는 보고서 데이터에 대한 깊이 있는 개념 정보를 제공하며, 데이터와 관련된 보고서 부분을 정의, 사용자 지정 및 사용하는 방법을 절차적인 측면에서 소개합니다.</span><span class="sxs-lookup"><span data-stu-id="aab78-192">These sections of the documentation provide in-depth conceptual information about report data, and procedural information about how to define, customize, and use parts of a report that are related to data.</span></span>  
  
 [<span data-ttu-id="aab78-193">보고서 &#40;보고서 작성기 및 SSRS&#41;에 데이터를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="aab78-193">Add Data to a Report &#40;Report Builder and SSRS&#41;</span></span>](report-datasets-ssrs.md)  
 <span data-ttu-id="aab78-194">보고서의 데이터 액세스에 대한 개요를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="aab78-194">Provides an overview of accessing data for your report.</span></span>  
  
 [<span data-ttu-id="aab78-195">보고서 작성기의 데이터 연결, 데이터 원본 및 연결 문자열</span><span class="sxs-lookup"><span data-stu-id="aab78-195">Data Connections, Data Sources, and Connection Strings in Report Builder</span></span>](../data-connections-data-sources-and-connection-strings-in-report-builder.md)  
 <span data-ttu-id="aab78-196">데이터 연결 및 데이터 원본에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="aab78-196">Provides information about data connections and data sources.</span></span>  
  
 [<span data-ttu-id="aab78-197">보고서 포함된 데이터 세트 및 공유 데이터 세트&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="aab78-197">Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;</span></span>](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)  
 <span data-ttu-id="aab78-198">포함된 데이터 세트 및 공유 데이터 세트에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="aab78-198">Provides information about embedded and shared datasets.</span></span>  
  
 [<span data-ttu-id="aab78-199">데이터 세트 필드 컬렉션&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="aab78-199">Dataset Fields Collection &#40;Report Builder and SSRS&#41;</span></span>](dataset-fields-collection-report-builder-and-ssrs.md)  
 <span data-ttu-id="aab78-200">쿼리에 의해 생성되는 데이터 세트 필드 컬렉션에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="aab78-200">Provides information about the dataset field collection generated by the query.</span></span>  
  
 <span data-ttu-id="aab78-201">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [온라인 설명서](https://go.microsoft.com/fwlink/?linkid=121312)에 있는 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 설명서의 [Reporting Services&#40;SSRS&#41;에서 지원하는 데이터 원본](../create-deploy-and-manage-mobile-and-paginated-reports.md).</span><span class="sxs-lookup"><span data-stu-id="aab78-201">[Data Sources Supported by Reporting Services &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md) in the [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] documentation in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?linkid=121312).</span></span>  
 <span data-ttu-id="aab78-202">각 데이터 확장 프로그램의 플랫폼 및 버전 지원에 대한 자세한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="aab78-202">Provides in-depth information about platform and version support for each data extension.</span></span>  
  
  
## <a name="see-also"></a><span data-ttu-id="aab78-203">참고 항목</span><span class="sxs-lookup"><span data-stu-id="aab78-203">See Also</span></span>  
 <span data-ttu-id="aab78-204">[보고서 매개 변수&#40;보고서 작성기 및 보고서 디자이너&#41;](../report-design/report-parameters-report-builder-and-report-designer.md) </span><span class="sxs-lookup"><span data-stu-id="aab78-204">[Report Parameters &#40;Report Builder and Report Designer&#41;](../report-design/report-parameters-report-builder-and-report-designer.md) </span></span>  
 <span data-ttu-id="aab78-205">[데이터 필터링, 그룹화 및 정렬&#40;보고서 작성기 및 SSRS&#41;](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="aab78-205">[Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="aab78-206">식&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="aab78-206">Expressions &#40;Report Builder and SSRS&#41;</span></span>](../report-design/expressions-report-builder-and-ssrs.md)  
  
  
