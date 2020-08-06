---
title: ADO NET 대상 편집기 (연결 관리자 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.adonetdest.connection.f1
ms.assetid: a3b11286-32c8-40e1-8ae7-090e2590345a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 78851d5bbad18d2d1076eaa87200dd73e6962a90
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638961"
---
# <a name="ado-net-destination-editor-connection-manager-page"></a><span data-ttu-id="be85b-102">ADO NET 대상 편집기(연결 관리자 페이지)</span><span class="sxs-lookup"><span data-stu-id="be85b-102">ADO NET Destination Editor (Connection Manager Page)</span></span>
  <span data-ttu-id="be85b-103">**ADO NET 대상 편집기** 대화 상자의 **연결 관리자** 페이지를 사용하여 대상에 대한 [!INCLUDE[vstecado](../includes/vstecado-md.md)] 연결을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="be85b-103">Use the **Connection Manager** page of the **ADO NET Destination Editor** dialog box to select the [!INCLUDE[vstecado](../includes/vstecado-md.md)] connection for the destination.</span></span> <span data-ttu-id="be85b-104">이 페이지를 사용하면 데이터베이스에서 테이블이나 뷰를 선택할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="be85b-104">This page also lets you select a table or view from the database.</span></span>  
  
 <span data-ttu-id="be85b-105">ADO NET 대상에 대한 자세한 내용은 [ADO NET Destination](data-flow/ado-net-destination.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="be85b-105">To learn more about the ADO NET destination, see [ADO NET Destination](data-flow/ado-net-destination.md).</span></span>  
  
 <span data-ttu-id="be85b-106">**연결 관리자 페이지를 열려면**</span><span class="sxs-lookup"><span data-stu-id="be85b-106">**To open the Connection Manager page**</span></span>  
  
1.  <span data-ttu-id="be85b-107">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]에서 ADO NET 대상이 있는 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 패키지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="be85b-107">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package that has the ADO NET destination.</span></span>  
  
2.  <span data-ttu-id="be85b-108">**데이터 흐름** 탭에서 ADO NET 대상을 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="be85b-108">On the **Data Flow** tab, double-click the ADO NET destination.</span></span>  
  
3.  <span data-ttu-id="be85b-109">**ADO NET 대상 편집기**에서 **연결 관리자**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="be85b-109">In the **ADO NET Destination Editor**, click **Connection Manager**.</span></span>  
  
## <a name="static-options"></a><span data-ttu-id="be85b-110">정적 옵션</span><span class="sxs-lookup"><span data-stu-id="be85b-110">Static Options</span></span>  
 <span data-ttu-id="be85b-111">**Connection manager**</span><span class="sxs-lookup"><span data-stu-id="be85b-111">**Connection manager**</span></span>  
 <span data-ttu-id="be85b-112">목록에서 기존 연결 관리자를 선택하거나 **새로 만들기**를 클릭하여 새 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="be85b-112">Select an existing connection manager from the list, or create a new connection by clicking **New**.</span></span>  
  
 <span data-ttu-id="be85b-113">**새로 만들기**</span><span class="sxs-lookup"><span data-stu-id="be85b-113">**New**</span></span>  
 <span data-ttu-id="be85b-114">**ADO.NET 연결 관리자 구성** 대화 상자를 사용하여 새 연결 관리자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="be85b-114">Create a new connection manager by using the **Configure ADO.NET Connection Manager** dialog box.</span></span>  
  
 <span data-ttu-id="be85b-115">**테이블 또는 뷰 사용**</span><span class="sxs-lookup"><span data-stu-id="be85b-115">**Use a table or view**</span></span>  
 <span data-ttu-id="be85b-116">목록에서 기존 테이블 또는 뷰를 선택하거나 **새로 만들기**를 클릭하여 새 테이블을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="be85b-116">Select an existing table or view from the list, or create a new table by clicking **New**..</span></span>  
  
 <span data-ttu-id="be85b-117">**새로 만들기**</span><span class="sxs-lookup"><span data-stu-id="be85b-117">**New**</span></span>  
 <span data-ttu-id="be85b-118">**테이블 만들기** 대화 상자를 사용하여 새 테이블 또는 뷰를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="be85b-118">Create a new table or view by using the **Create Table** dialog box.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="be85b-119">**새로 만들기**를 클릭하면 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 에서 연결된 데이터 원본에 따라 기본 CREATE TABLE 문을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="be85b-119">When you click **New**, [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] generates a default CREATE TABLE statement based on the connected data source.</span></span> <span data-ttu-id="be85b-120">원본 테이블에 선언된 FILESTREAM 특성이 포함된 열이 있어도 기본 CREATE TABLE 문은 FILESTREAM 특성을 포함하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="be85b-120">This default CREATE TABLE statement will not include the FILESTREAM attribute even if the source table includes a column with the FILESTREAM attribute declared.</span></span> <span data-ttu-id="be85b-121">FILESTREAM 특성이 포함된 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 구성 요소를 실행하려면 먼저 대상 데이터베이스에서 FILESTREAM 스토리지를 구현하십시오.</span><span class="sxs-lookup"><span data-stu-id="be85b-121">To run an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] component with the FILESTREAM attribute, first implement FILESTREAM storage on the destination database.</span></span> <span data-ttu-id="be85b-122">그런 다음 **테이블 만들기** 대화 상자에서 FILESTREAM 특성을 CREATE TABLE 문에 추가하십시오.</span><span class="sxs-lookup"><span data-stu-id="be85b-122">Then, add the FILESTREAM attribute to the CREATE TABLE statement in the **Create Table** dialog box.</span></span> <span data-ttu-id="be85b-123">자세한 내용은 [Blob&#40;Binary Large Object&#41; 데이터&#40;SQL Server&#41;](../relational-databases/blob/binary-large-object-blob-data-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="be85b-123">For more information, see [Binary Large Object &#40;Blob&#41; Data &#40;SQL Server&#41;](../relational-databases/blob/binary-large-object-blob-data-sql-server.md).</span></span>  
  
 <span data-ttu-id="be85b-124">**미리 보기**</span><span class="sxs-lookup"><span data-stu-id="be85b-124">**Preview**</span></span>  
 <span data-ttu-id="be85b-125">**쿼리 결과 미리 보기** 대화 상자를 사용하여 결과를 미리 봅니다.</span><span class="sxs-lookup"><span data-stu-id="be85b-125">Preview results by using the **Preview Query Results** dialog box.</span></span> <span data-ttu-id="be85b-126">미리 보기에는 최대 200개의 행이 표시될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="be85b-126">Preview can display up to 200 rows.</span></span>  
  
 <span data-ttu-id="be85b-127">**사용 가능한 경우 대량 삽입 사용**</span><span class="sxs-lookup"><span data-stu-id="be85b-127">**Use bulk insert when available**</span></span>  
 <span data-ttu-id="be85b-128"><xref:System.Data.SqlClient.SqlBulkCopy> 인터페이스를 사용하여 대량 삽입 작업의 성능을 향상시킬지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="be85b-128">Specify whether to use the <xref:System.Data.SqlClient.SqlBulkCopy> interface to improve the performance of bulk insert operations.</span></span>  
  
 <span data-ttu-id="be85b-129"><xref:System.Data.SqlClient.SqlConnection> 개체를 반환하는 ADO.NET 공급자만 <xref:System.Data.SqlClient.SqlBulkCopy> 인터페이스의 사용을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="be85b-129">Only ADO.NET providers that return a <xref:System.Data.SqlClient.SqlConnection> object support the use of the <xref:System.Data.SqlClient.SqlBulkCopy> interface.</span></span> <span data-ttu-id="be85b-130">.NET Data Provider for SQL Server(SqlClient)는 <xref:System.Data.SqlClient.SqlConnection> 개체를 반환하고, 사용자 지정 공급자는 <xref:System.Data.SqlClient.SqlConnection> 개체를 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="be85b-130">The .NET Data Provider for SQL Server (SqlClient) returns a <xref:System.Data.SqlClient.SqlConnection> object, and a custom provider may return a <xref:System.Data.SqlClient.SqlConnection> object.</span></span>  
  
 <span data-ttu-id="be85b-131">.NET Data Provider for SQL Server(SqlClient)를 사용하여 [!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssSDSfull](../includes/sssdsfull-md.md)]에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="be85b-131">You can use the .NET Data Provider for SQL Server (SqlClient) to connect to [!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssSDSfull](../includes/sssdsfull-md.md)].</span></span>  
  
 <span data-ttu-id="be85b-132">**사용 가능한 경우 대량 삽입 사용**을 선택하고 **오류** 옵션을 **행 리디렉션**으로 설정하면 대상에서 오류 출력으로 리디렉션하는 일괄 처리 데이터에 올바른 행이 포함될 수 있습니다. 대량 작업에서 오류 처리에 대한 자세한 내용은 [데이터 오류 처리](data-flow/error-handling-in-data.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="be85b-132">If you select **Use bulk insert when available**, and set the **Error** option to **Redirect the row**, the batch of data that the destination redirects to the error output may include good rows.For more information about handling errors in bulk operations, see [Error Handling in Data](data-flow/error-handling-in-data.md).</span></span> <span data-ttu-id="be85b-133">**오류** 옵션에 대한 자세한 내용은 [ADO NET 대상 편집기&#40;오류 출력 페이지&#41;](../../2014/integration-services/ado-net-destination-editor-error-output-page.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="be85b-133">For more information about the **Error** option, see [ADO NET Destination Editor &#40;Error Output Page&#41;](../../2014/integration-services/ado-net-destination-editor-error-output-page.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="be85b-134">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 또는 Sybase 원본 테이블에 ID 열이 포함되어 있으면 SQL 실행 태스크를 사용하여 ADO NET 대상 전과 후에 SET IDENTITY_INSERT 문을 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="be85b-134">If a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] or Sybase source table includes an identity column, you must use Execute SQL tasks to run a SET IDENTITY_INSERT statement before and after the ADO NET destination.</span></span> <span data-ttu-id="be85b-135">ID 열 속성은 열에 대한 증분 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="be85b-135">The identity column property specifies an incremental value for the column.</span></span> <span data-ttu-id="be85b-136">SET IDENTITY_INSERT 문을 사용하면 ID 열에 명시적 값을 삽입할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="be85b-136">The SET IDENTITY_INSERT statement enables explicit values to be inserted into the identity column.</span></span> <span data-ttu-id="be85b-137">같은 데이터베이스 연결에서 CREATE TABLE 및 SET IDENTITY 문을 실행하려면 [!INCLUDE[vstecado](../includes/vstecado-md.md)] 연결 관리자의 `RetainSameConnection` 속성을 `True`로 설정하십시오.</span><span class="sxs-lookup"><span data-stu-id="be85b-137">To run the CREATE TABLE and SET IDENTITY statements on the same database connection, set the `RetainSameConnection` property of the [!INCLUDE[vstecado](../includes/vstecado-md.md)] connection manager to `True`.</span></span> <span data-ttu-id="be85b-138">또한 SQL 실행 태스크와 ADO NET 대상에 같은 [!INCLUDE[vstecado](../includes/vstecado-md.md)] 연결 관리자를 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="be85b-138">Also, use the same [!INCLUDE[vstecado](../includes/vstecado-md.md)] connection manager for the Execute SQL tasks and the ADO NET destination.</span></span>  
>   
>  <span data-ttu-id="be85b-139">자세한 내용은 [SET IDENTITY_INSERT&#40;Transact-SQL&#41;](/sql/t-sql/statements/set-identity-insert-transact-sql) 및 [IDENTITY&#40;속성&#41;&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql-identity-property)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="be85b-139">For more information, see [SET IDENTITY_INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-identity-insert-transact-sql) and [IDENTITY &#40;Property&#41; &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql-identity-property).</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="be85b-140">외부 리소스</span><span class="sxs-lookup"><span data-stu-id="be85b-140">External Resources</span></span>  
 <span data-ttu-id="be85b-141">sqlcat.com의 기술 문서 - [Azure SQL Database에 빨리 데이터 로드](https://go.microsoft.com/fwlink/?LinkId=244333)</span><span class="sxs-lookup"><span data-stu-id="be85b-141">Technical article, [Loading data to Azure SQL Database the fast way](https://go.microsoft.com/fwlink/?LinkId=244333), on sqlcat.com</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be85b-142">참고 항목</span><span class="sxs-lookup"><span data-stu-id="be85b-142">See Also</span></span>  
 <span data-ttu-id="be85b-143">[ADO NET 대상 편집기 &#40;매핑 페이지&#41;](../../2014/integration-services/ado-net-destination-editor-mappings-page.md) </span><span class="sxs-lookup"><span data-stu-id="be85b-143">[ADO NET Destination Editor &#40;Mappings Page&#41;](../../2014/integration-services/ado-net-destination-editor-mappings-page.md) </span></span>  
 <span data-ttu-id="be85b-144">[ADO NET 대상 편집기 &#40;오류 출력 페이지&#41;](../../2014/integration-services/ado-net-destination-editor-error-output-page.md) </span><span class="sxs-lookup"><span data-stu-id="be85b-144">[ADO NET Destination Editor &#40;Error Output Page&#41;](../../2014/integration-services/ado-net-destination-editor-error-output-page.md) </span></span>  
 <span data-ttu-id="be85b-145">[ADO.NET 연결 관리자](connection-manager/ado-net-connection-manager.md) </span><span class="sxs-lookup"><span data-stu-id="be85b-145">[ADO.NET Connection Manager](connection-manager/ado-net-connection-manager.md) </span></span>  
 [<span data-ttu-id="be85b-146">SQL 실행 태스크</span><span class="sxs-lookup"><span data-stu-id="be85b-146">Execute SQL Task</span></span>](control-flow/execute-sql-task.md)  
  
  
