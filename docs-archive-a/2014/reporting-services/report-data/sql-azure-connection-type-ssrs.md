---
title: SQL Azure 연결 형식(SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: c84def6c-e8cf-43d9-9912-098171a7ce79
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: e2c3d3e75117996f088cff96b2b7a8d4cd504127
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653228"
---
# <a name="sql-azure-connection-type-ssrs"></a><span data-ttu-id="f63a2-102">SQL Azure 연결 형식(SSRS)</span><span class="sxs-lookup"><span data-stu-id="f63a2-102">SQL Azure Connection Type (SSRS)</span></span>
  [!INCLUDE[msCoName](../../includes/msconame-md.md)]<span data-ttu-id="f63a2-103">[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]는 기술을 기반으로 작성 된 클라우드 기반의 호스팅되는 관계형 데이터베이스입니다 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="f63a2-103">[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] is a cloud-based, hosted relational database built on [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] technologies.</span></span> <span data-ttu-id="f63a2-104">보고서에 [!INCLUDE[ssSDS](../../includes/sssds-md.md)]의 데이터를 포함하려면 [!INCLUDE[ssSDS](../../includes/sssds-md.md)]유형의 보고서 데이터 원본을 기반으로 하는 데이터 세트가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f63a2-104">To include data from [!INCLUDE[ssSDS](../../includes/sssds-md.md)] in your report, you must have a dataset that is based on a report data source of type [!INCLUDE[ssSDS](../../includes/sssds-md.md)].</span></span> <span data-ttu-id="f63a2-105">이 기본 제공 데이터 원본 유형은 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] 데이터 확장 프로그램을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="f63a2-105">This built-in data source type is based on the [!INCLUDE[ssSDS](../../includes/sssds-md.md)] data extension.</span></span> <span data-ttu-id="f63a2-106">이 데이터 원본 유형을 사용하여 [!INCLUDE[ssSDS](../../includes/sssds-md.md)]에 연결하고 데이터를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f63a2-106">Use this data source type to connect to and retrieve data from [!INCLUDE[ssSDS](../../includes/sssds-md.md)].</span></span>

 <span data-ttu-id="f63a2-107">이 데이터 확장 프로그램은 다중값 매개 변수, 서버 집계 및 연결 문자열과 별개로 관리되는 자격 증명을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="f63a2-107">This data extension supports multivalued parameters, server aggregates, and credentials managed separately from the connection string.</span></span>

 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] <span data-ttu-id="f63a2-108">가 사용자 컴퓨터의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스와 비슷하기 때문에 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] 에서 데이터를 가져오는 방법은 몇 가지 예외를 제외하고 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 데이터를 가져오는 방법과 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="f63a2-108">is similar to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on your premises and getting data from [!INCLUDE[ssSDS](../../includes/sssds-md.md)] is, with a few exceptions, identical to getting data from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>

> [!NOTE]
>  <span data-ttu-id="f63a2-109">[!INCLUDE[ssSDS](../../includes/sssds-md.md)]에 대한 연결을 열 때 연결 시간 제한을 30초로 설정하세요.</span><span class="sxs-lookup"><span data-stu-id="f63a2-109">When opening a connection to a [!INCLUDE[ssSDS](../../includes/sssds-md.md)], set the connection timeout to 30 seconds.</span></span>

 <span data-ttu-id="f63a2-110">자세한 내용은 [Azure SQL Database 설명서](https://docs.microsoft.com/azure/sql-database/)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f63a2-110">For more information, see [Azure SQL Database Documentation](https://docs.microsoft.com/azure/sql-database/).</span></span>

 <span data-ttu-id="f63a2-111">이 항목의 정보를 사용하여 데이터 원본을 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f63a2-111">Use the information in this topic to build a data source.</span></span> <span data-ttu-id="f63a2-112">단계별 지침은 [데이터 연결이 나 데이터 원본 &#40;추가 및 확인 보고서 작성기 및 SSRS&#41;](add-and-verify-a-data-connection-report-builder-and-ssrs.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f63a2-112">For step-by-step instructions, see [Add and Verify a Data Connection or Data Source &#40;Report Builder and SSRS&#41;](add-and-verify-a-data-connection-report-builder-and-ssrs.md).</span></span>

##  <a name="connection-string"></a><a name="Connection"></a><span data-ttu-id="f63a2-113">연결 문자열</span><span class="sxs-lookup"><span data-stu-id="f63a2-113">Connection String</span></span>
 <span data-ttu-id="f63a2-114">[!INCLUDE[ssSDS](../../includes/sssds-md.md)]에 연결하면 클라우드의 데이터베이스 개체에 연결하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f63a2-114">When you connect to [!INCLUDE[ssSDS](../../includes/sssds-md.md)], you are connecting to a database object in the cloud.</span></span> <span data-ttu-id="f63a2-115">온사이트 데이터베이스와 마찬가지로 호스팅되는 데이터베이스에는 여러 테이블, 뷰 및 저장 프로시저가 있는 스키마가 여러 개 있을 수 있으므로</span><span class="sxs-lookup"><span data-stu-id="f63a2-115">Just like onsite databases, the hosted database might have multiple schemas that have multiple tables, views, and stored procedures.</span></span> <span data-ttu-id="f63a2-116">쿼리 디자이너에서 사용할 데이터베이스 개체를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f63a2-116">You specify the database object to use in the query designer.</span></span> <span data-ttu-id="f63a2-117">연결 문자열에 데이터베이스를 지정하지 않을 경우 관리자가 할당한 기본 데이터베이스에 연결됩니다.</span><span class="sxs-lookup"><span data-stu-id="f63a2-117">If you do not specify a database in the connection string, you connect to the default database that the administrator assigned to you.</span></span>

 <span data-ttu-id="f63a2-118">데이터 원본 연결에 사용할 자격 증명 및 연결 정보는 데이터베이스 관리자에게 문의하십시오.</span><span class="sxs-lookup"><span data-stu-id="f63a2-118">Contact your database administrator for connection information and for the credentials to use to connect to the data source.</span></span> <span data-ttu-id="f63a2-119">다음 연결 문자열 예에서는 AdventureWorks라는 호스팅되는 예제 데이터베이스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f63a2-119">The following connection string example specifies a hosted sample database named AdventureWorks.</span></span>

```
Data Source=<host>;Initial Catalog=AdventureWorks; Encrypt=True;
```

 <span data-ttu-id="f63a2-120">또한 **데이터 원본 속성** 대화 상자를 사용하여 사용자 이름과 암호 같은 자격 증명을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f63a2-120">In addition, you use the **Data Sources Properties** dialog box to provide credentials such as user name and password.</span></span> <span data-ttu-id="f63a2-121">그러면 `User Id` 및 `Password` 옵션이 자동으로 연결 문자열에 추가되기 때문에 이러한 옵션을 연결 문자열의 일부로 입력할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f63a2-121">The `User Id` and `Password` options are automatically appended to the connection string; you do not need to type them as part of the connection string.</span></span>

 <span data-ttu-id="f63a2-122">자세한 내용 및 연결 문자열 예제는 [보고서 작성기의 데이터 연결, 데이터 원본 및 연결 문자열](../data-connections-data-sources-and-connection-strings-in-report-builder.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f63a2-122">For more information and connection string examples, see [Data Connections, Data Sources, and Connection Strings in Report Builder](../data-connections-data-sources-and-connection-strings-in-report-builder.md).</span></span>

##  <a name="credentials"></a><a name="Credentials"></a><span data-ttu-id="f63a2-123">자격 증명</span><span class="sxs-lookup"><span data-stu-id="f63a2-123">Credentials</span></span>
 <span data-ttu-id="f63a2-124">Windows 인증(통합 보안)이 지원되지 않기 때문에</span><span class="sxs-lookup"><span data-stu-id="f63a2-124">Windows Authentication (integrated security) is not supported.</span></span> <span data-ttu-id="f63a2-125">Windows 인증을 사용하여 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] 에 연결하려고 하면 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="f63a2-125">If you attempt to connect to [!INCLUDE[ssSDS](../../includes/sssds-md.md)] using Windows Authentication an error occurs.</span></span> [!INCLUDE[ssSDS](../../includes/sssds-md.md)] <span data-ttu-id="f63a2-126">에서는 SQL Server 인증(사용자 이름 및 암호)만 지원하므로 [!INCLUDE[ssSDS](../../includes/sssds-md.md)]에 연결할 때마다 자격 증명(로그인 및 암호)을 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f63a2-126">supports only SQL Server Authentication (user name and password) and users must provide credentials (login and password) every time they connect to [!INCLUDE[ssSDS](../../includes/sssds-md.md)].</span></span>

 <span data-ttu-id="f63a2-127">자격 증명에는 데이터베이스에 액세스할 수 있는 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f63a2-127">Credentials must be sufficient to access the database.</span></span> <span data-ttu-id="f63a2-128">쿼리에 따라 저장 프로시저를 실행하고 테이블 및 뷰에 액세스할 수 있는 권한과 같은 다른 사용 권한이 필요할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f63a2-128">Depending on your query, you might need other permissions, such as sufficient permissions to run stored procedures and access tables and views.</span></span> <span data-ttu-id="f63a2-129">외부 데이터 원본의 소유자는 사용자에게 필요한 데이터베이스 개체에 대한 읽기 전용 권한을 제공할 수 있는 자격 증명을 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f63a2-129">The owner of the external data source must configure credentials that are sufficient to provide read-only access to the database objects that you need.</span></span>

 <span data-ttu-id="f63a2-130">보고서 작성 클라이언트에서는 다음 옵션을 사용하여 자격 증명을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f63a2-130">From a report authoring client, the following options are available to specify credentials:</span></span>

-   <span data-ttu-id="f63a2-131">저장된 사용자 이름 및 암호 사용.</span><span class="sxs-lookup"><span data-stu-id="f63a2-131">Use a stored user name and password.</span></span> <span data-ttu-id="f63a2-132">보고서 데이터를 포함하는 데이터베이스가 보고서 서버와 다른 경우 발생하는 이중 홉을 협상하려면 Windows 자격 증명을 자격 증명으로 사용하도록 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f63a2-132">To negotiate the double hop that occurs when the database that contains the report data is different than the report server, select options to use credentials as Windows credentials.</span></span> <span data-ttu-id="f63a2-133">데이터 원본에 연결한 후 인증된 사용자를 가장하도록 선택할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f63a2-133">You can also chose to impersonate the authenticated user after connecting to the data source.</span></span>

-   <span data-ttu-id="f63a2-134">자격 증명 필요 없음.</span><span class="sxs-lookup"><span data-stu-id="f63a2-134">No credentials are required.</span></span> <span data-ttu-id="f63a2-135">이 옵션을 사용하려면 보고서 서버에서 무인 실행 계정을 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f63a2-135">To use this option, you must have the unattended execution account configured on the report server.</span></span> <span data-ttu-id="f63a2-136">자세한 내용은 msdn.microsoft.com의 [Reporting Services 설명서](https://go.microsoft.com/fwlink/?linkid=121312)에서 [무인 실행 계정 구성&#40;SSRS 구성 관리자&#41;](../install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f63a2-136">For more information, see [Configure the Unattended Execution Account &#40;SSRS Configuration Manager&#41;](../install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md) in the [Reporting Services documentation](https://go.microsoft.com/fwlink/?linkid=121312) in on msdn.microsoft.com.</span></span>

 <span data-ttu-id="f63a2-137">자세한 내용은 [Reporting Services의 데이터 연결, 데이터 원본 및 연결 문자열](../data-connections-data-sources-and-connection-strings-in-reporting-services.md) 을 참조 하거나 [보고서 작성기에서 자격 증명을 지정](../specify-credentials-in-report-builder.md)하세요.</span><span class="sxs-lookup"><span data-stu-id="f63a2-137">For more information, see [Data Connections, Data Sources, and Connection Strings in Reporting Services](../data-connections-data-sources-and-connection-strings-in-reporting-services.md) or [Specify Credentials in Report Builder](../specify-credentials-in-report-builder.md).</span></span>

 

##  <a name="queries"></a><a name="Query"></a><span data-ttu-id="f63a2-138">쿼리</span><span class="sxs-lookup"><span data-stu-id="f63a2-138">Queries</span></span>
 <span data-ttu-id="f63a2-139">쿼리는 보고서 데이터 세트에 대해 검색할 데이터를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f63a2-139">A query specifies which data to retrieve for a report dataset.</span></span> <span data-ttu-id="f63a2-140">쿼리 결과 집합의 열은 데이터 세트의 필드 컬렉션을 채웁니다.</span><span class="sxs-lookup"><span data-stu-id="f63a2-140">The columns in the result set for a query populate the field collection for a dataset.</span></span> <span data-ttu-id="f63a2-141">쿼리가 여러 결과 집합을 반환할 경우 보고서는 쿼리가 검색한 첫 번째 결과 집합만 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="f63a2-141">If the query returns multiple result sets, the report processes only the first result set that the query retrieves.</span></span> <span data-ttu-id="f63a2-142">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 과(와) [!INCLUDE[ssSDS](../../includes/sssds-md.md)]은(는) 지원되는 데이터베이스 크기 등이 다를 수 있지만 [!INCLUDE[ssSDS](../../includes/sssds-md.md)]에 대한 쿼리를 작성하는 방법과 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스에 대한 쿼리를 작성하는 방법은 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="f63a2-142">Although there are some differences between [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and [!INCLUDE[ssSDS](../../includes/sssds-md.md)]s such as the sizes of databases supported, writing queries against [!INCLUDE[ssSDS](../../includes/sssds-md.md)]s is similar to writing queries against [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases.</span></span> <span data-ttu-id="f63a2-143">BACKUP과 같은 일부 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문은 [!INCLUDE[ssSDS](../../includes/sssds-md.md)]에서 지원되지 않지만 이러한 문은 보고서 쿼리에 사용하는 문이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="f63a2-143">Some [!INCLUDE[tsql](../../includes/tsql-md.md)] statements such as BACKUP are not supported in [!INCLUDE[ssSDS](../../includes/sssds-md.md)], but they are not ones that you use in report queries.</span></span> <span data-ttu-id="f63a2-144">자세한 내용은 [SQL Server 연결 형식&#40;SSRS&#41;](sql-server-connection-type-ssrs.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f63a2-144">For more information, see [SQL Server Connection Type &#40;SSRS&#41;](sql-server-connection-type-ssrs.md).</span></span>

 <span data-ttu-id="f63a2-145">기본적으로 그래픽 쿼리 디자이너에 나타낼 수 있는 새 쿼리를 만들거나 기존 쿼리를 열 경우 관계형 쿼리 디자이너를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f63a2-145">By default, if you create a new query or open an existing query that can be represented in the graphical query designer, the relational query designer is available.</span></span> <span data-ttu-id="f63a2-146">다음과 같은 방법으로 쿼리를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f63a2-146">You can specify a query in the following ways:</span></span>

-   <span data-ttu-id="f63a2-147">대화식으로 쿼리를 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="f63a2-147">Build a query interactively.</span></span> <span data-ttu-id="f63a2-148">관계형 쿼리 디자이너를 사용합니다. 관계형 쿼리 디자이너는 테이블, 뷰, 저장 프로시저 및 기타 데이터베이스 항목을 데이터베이스 스키마별로 구성하여 계층 구조로 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="f63a2-148">Use the relational query designer that displays a hierarchical view of tables, views, stored procedures, and other database items, organized by database schema.</span></span> <span data-ttu-id="f63a2-149">테이블 또는 뷰에서 열을 선택하거나 저장 프로시저 또는 테이블 반환 함수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f63a2-149">Select columns from tables or views, or specify stored procedures or table-valued functions.</span></span> <span data-ttu-id="f63a2-150">필터 조건을 지정하여 검색할 데이터 행 수를 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="f63a2-150">Limit the number of rows of data to retrieve by specifying filter criteria.</span></span> <span data-ttu-id="f63a2-151">매개 변수 옵션을 설정하여 보고서를 실행할 때 필터를 사용자 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f63a2-151">Customize the filter when the report runs by setting the parameter option.</span></span>

-   <span data-ttu-id="f63a2-152">쿼리를 입력하거나 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="f63a2-152">Type or paste a query.</span></span> <span data-ttu-id="f63a2-153">텍스트 기반 쿼리 디자이너를 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)] 텍스트를 직접 입력하거나, 다른 원본에서 쿼리 텍스트를 붙여넣거나, 관계형 쿼리 디자이너를 사용하여 작성할 수 없는 복잡한 쿼리를 입력하거나, 쿼리 기반 식을 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f63a2-153">Use the text-based query designer to enter [!INCLUDE[tsql](../../includes/tsql-md.md)] text directly, to paste query text from another source, to enter complex queries that cannot be built by using the relational query designer, or to enter query-based expressions.</span></span>

-   <span data-ttu-id="f63a2-154">파일 또는 보고서에서 기존 쿼리를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="f63a2-154">Import an existing query from a file or report.</span></span> <span data-ttu-id="f63a2-155">쿼리 디자이너에서 쿼리 **가져오기** 단추를 사용하여 .sql 파일 또는 .rdl 파일을 찾아서 쿼리를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="f63a2-155">Use the **Import** query button from either query designer to browse to a .sql file or .rdl file and import a query.</span></span>

 <span data-ttu-id="f63a2-156">텍스트 기반 쿼리 디자이너에서는 다음과 같은 두 가지 모드를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="f63a2-156">The text-based query designer supports the following two modes:</span></span>

-   <span data-ttu-id="f63a2-157">[텍스트](#QueryText) 데이터 원본에서 데이터를 선택하는 [!INCLUDE[tsql](../../includes/tsql-md.md)] 명령을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="f63a2-157">[Text](#QueryText) Type [!INCLUDE[tsql](../../includes/tsql-md.md)] commands that select data from the data source.</span></span>

-   <span data-ttu-id="f63a2-158">[Stored Procedure](#QueryStoredProcedure) 저장 프로시저 목록에서 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f63a2-158">[Stored Procedure](#QueryStoredProcedure) Choose from a list of stored procedures.</span></span>

 <span data-ttu-id="f63a2-159">자세한 내용은 [관계형 쿼리 디자이너 사용자 인터페이스&#40;보고서 작성기&#41;](relational-query-designer-user-interface-report-builder.md) 및 [텍스트 기반 쿼리 디자이너 사용자 인터페이스&#40;보고서 작성기&#41;](text-based-query-designer-user-interface-report-builder.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f63a2-159">For more information, see [Relational Query Designer User Interface &#40;Report Builder&#41;](relational-query-designer-user-interface-report-builder.md) and [Text-based Query Designer User Interface &#40;Report Builder&#41;](text-based-query-designer-user-interface-report-builder.md).</span></span>

 <span data-ttu-id="f63a2-160">[!INCLUDE[ssSDS](../../includes/sssds-md.md)] 에서 사용하는 그래픽 쿼리 디자이너는 요약 데이터만 검색하는 쿼리를 작성하는 데 도움이 되는 그룹화 및 집계를 기본적으로 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="f63a2-160">The graphical query designer that [!INCLUDE[ssSDS](../../includes/sssds-md.md)] uses provides built-in support for grouping and aggregates to help you write queries that retrieve only summary data.</span></span> <span data-ttu-id="f63a2-161">[!INCLUDE[tsql](../../includes/tsql-md.md)] 언어 기능은 GROUP BY 절, DISTINCT 키워드 및 SUM, COUNT 등과 같은 집계입니다.</span><span class="sxs-lookup"><span data-stu-id="f63a2-161">The [!INCLUDE[tsql](../../includes/tsql-md.md)] language features are: the GROUP BY clause, DISTINCT keyword, and aggregates such as SUM and COUNT.</span></span> <span data-ttu-id="f63a2-162">텍스트 기반 쿼리 디자이너는 그룹화 및 집계를 비롯한 [!INCLUDE[tsql](../../includes/tsql-md.md)] 언어를 완벽하게 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="f63a2-162">The text-based query designer provides full support for the [!INCLUDE[tsql](../../includes/tsql-md.md)] language, including grouping and aggregates.</span></span> <span data-ttu-id="f63a2-163">[!INCLUDE[tsql](../../includes/tsql-md.md)]에 대한 자세한 내용은 msdn.microsoft.com의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [온라인 설명서](https://go.microsoft.com/fwlink/?LinkId=141687)에서 [Transact-SQL 참조&#40;데이터베이스 엔진&#41;](/sql/t-sql/language-reference)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f63a2-163">For more information about [!INCLUDE[tsql](../../includes/tsql-md.md)], see [Transact-SQL Reference &#40;Database Engine&#41;](/sql/t-sql/language-reference)in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?LinkId=141687) on msdn.microsoft.com.</span></span>

###  <a name="using-query-type-text"></a><a name="QueryText"></a> <span data-ttu-id="f63a2-164">Text 쿼리 유형 사용</span><span class="sxs-lookup"><span data-stu-id="f63a2-164">Using Query Type Text</span></span>
 <span data-ttu-id="f63a2-165">텍스트 기반 쿼리 디자이너에서는 [!INCLUDE[tsql](../../includes/tsql-md.md)] 명령을 입력하여 데이터 세트의 데이터를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="f63a2-165">In the text-based query designer, you type [!INCLUDE[tsql](../../includes/tsql-md.md)] commands to define the data in a dataset.</span></span> <span data-ttu-id="f63a2-166">예를 들어 다음 [!INCLUDE[tsql](../../includes/tsql-md.md)] 쿼리는 마케팅 지원을 담당하는 모든 직원의 이름을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f63a2-166">For example, the following [!INCLUDE[tsql](../../includes/tsql-md.md)] query selects the names of all employees who are marketing assistants:</span></span>

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

 <span data-ttu-id="f63a2-167">쿼리를 실행하고 결과 집합을 표시하려면 도구 모음에서 **실행** 단추(**!**)를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f63a2-167">Click the **Run** button (**!**) on the toolbar to run the query and display a result set.</span></span>

 <span data-ttu-id="f63a2-168">이 쿼리에서 매개 변수를 사용하려면 쿼리 매개 변수를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="f63a2-168">To parameterize this query, add a query parameter.</span></span> <span data-ttu-id="f63a2-169">예를 들어 WHERE 절을 다음과 같이 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="f63a2-169">For example, change the WHERE clause to the following:</span></span>

```
WHERE HumanResources.Employee.JobTitle = (@JobTitle)
```

 <span data-ttu-id="f63a2-170">쿼리를 실행하면 쿼리 매개 변수에 해당하는 보고서 매개 변수가 자동으로 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="f63a2-170">When you run the query, report parameters that correspond to query parameters are automatically created.</span></span> <span data-ttu-id="f63a2-171">자세한 내용은 이 항목의 뒷부분에 나오는 [쿼리 매개 변수](#Parameters) 를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="f63a2-171">For more information, see [Query Parameters](#Parameters) later in this topic.</span></span>



###  <a name="using-query-type-storedprocedure"></a><a name="QueryStoredProcedure"></a><span data-ttu-id="f63a2-172">StoredProcedure 쿼리 유형 사용</span><span class="sxs-lookup"><span data-stu-id="f63a2-172">Using Query Type StoredProcedure</span></span>
 <span data-ttu-id="f63a2-173">다음 중 한 가지 방법으로 데이터 세트 쿼리에 대해 저장 프로시저를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f63a2-173">You can specify a stored procedure for a dataset query in one of the following ways:</span></span>

-   <span data-ttu-id="f63a2-174">**데이터 세트 속성** 대화 상자에서 **저장 프로시저** 옵션을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="f63a2-174">In the **Dataset Properties** dialog box, set the **Stored Procedure** option.</span></span> <span data-ttu-id="f63a2-175">저장 프로시저 및 테이블 반환 함수 드롭다운 목록에서 원하는 항목을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f63a2-175">Choose from the drop-down list of stored procedures and table-valued functions.</span></span>

-   <span data-ttu-id="f63a2-176">관계형 쿼리 디자이너에서는 데이터베이스 뷰 창에서 저장 프로시저 또는 테이블 반환 함수를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f63a2-176">In the relational query designer, in the Database view pane, select a stored procedure or table-valued function.</span></span>

-   <span data-ttu-id="f63a2-177">텍스트 기반 쿼리 디자이너에서는 도구 모음에서 **StoredProcedure** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f63a2-177">In the text-based query designer, select **StoredProcedure** from the toolbar.</span></span>

 <span data-ttu-id="f63a2-178">저장 프로시저나 테이블 반환 함수를 선택한 후 쿼리를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f63a2-178">After you select a stored procedure or table-valued function, you can run the query.</span></span> <span data-ttu-id="f63a2-179">입력 매개 변수 값을 입력하라는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f63a2-179">You will be prompted for input parameter values.</span></span> <span data-ttu-id="f63a2-180">쿼리를 실행하면 입력 매개 변수에 해당하는 보고서 매개 변수가 자동으로 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="f63a2-180">When you run the query, report parameters that correspond to input parameters are automatically created.</span></span> <span data-ttu-id="f63a2-181">자세한 내용은 이 항목의 뒷부분에 나오는 [쿼리 매개 변수](#Parameters) 를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="f63a2-181">For more information, see [Query Parameters](#Parameters) later in this topic.</span></span>

 <span data-ttu-id="f63a2-182">저장 프로시저의 경우 첫 번째로 검색된 결과 집합만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="f63a2-182">Only the first result set that is retrieved for a stored procedure is supported.</span></span> <span data-ttu-id="f63a2-183">저장 프로시저에서 여러 개의 결과 집합을 반환할 경우 첫 번째 결과 집합만 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f63a2-183">If a stored procedure returns multiple result sets, only the first one is used.</span></span>

 <span data-ttu-id="f63a2-184">저장 프로시저에 기본값을 사용하는 매개 변수가 있는 경우 매개 변수의 값으로 DEFAULT 키워드를 사용하여 해당 값에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f63a2-184">If a stored procedure has a parameter that has a default value, you can access that value by using the DEFAULT keyword as a value for the parameter.</span></span> <span data-ttu-id="f63a2-185">쿼리 매개 변수가 보고서 매개 변수에 연결되어 있으면 사용자가 보고서 매개 변수의 입력란에 DEFAULT라는 단어를 입력하거나 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f63a2-185">If the query parameter is linked to a report parameter, the user can type or select the word DEFAULT in the input box for the report parameter.</span></span>

 <span data-ttu-id="f63a2-186">저장 프로시저에 대한 자세한 내용은 msdn.microsoft.com의 [SQL Server 온라인 설명서](https://go.microsoft.com/fwlink/?linkid=98335) 에서 "저장 프로시저(데이터베이스 엔진)"를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f63a2-186">For more information about stored procedures, see "Stored Procedures (Database Engine)" in [SQL Server Books Online](https://go.microsoft.com/fwlink/?linkid=98335) on msdn.microsoft.com.</span></span>



##  <a name="parameters"></a><a name="Parameters"></a> <span data-ttu-id="f63a2-187">매개 변수</span><span class="sxs-lookup"><span data-stu-id="f63a2-187">Parameters</span></span>
 <span data-ttu-id="f63a2-188">쿼리 텍스트에 입력 매개 변수가 있는 쿼리 변수 또는 저장 프로시저가 포함된 경우 데이터 세트에 대한 해당 쿼리 매개 변수와 보고서에 대한 해당 보고서 매개 변수가 자동으로 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="f63a2-188">When query text contains query variables or stored procedures that have input parameters, the corresponding query parameters for the dataset and report parameters for the report are automatically generated.</span></span> <span data-ttu-id="f63a2-189">쿼리 텍스트는 각 쿼리 변수에 대한 DECLARE 문을 포함하지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f63a2-189">The query text must not include the DECLARE statement for each query variable.</span></span>

 <span data-ttu-id="f63a2-190">예를 들어 다음 SQL 쿼리는 `EmpID`라는 보고서 매개 변수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f63a2-190">For example, the following SQL query creates a report parameter named `EmpID`:</span></span>

```
SELECT FirstName, LastName FROM HumanResources.Employee E INNER JOIN
       Person.Contact C ON  E.ContactID=C.ContactID 
WHERE EmployeeID = (@EmpID)
```

 <span data-ttu-id="f63a2-191">기본적으로 각 보고서 매개 변수는 데이터 형식이 Text이며 사용 가능한 값의 드롭다운 목록을 제공하기 위해 자동으로 작성된 데이터 세트를 가집니다.</span><span class="sxs-lookup"><span data-stu-id="f63a2-191">By default, each report parameter has data type Text and an automatically created dataset to provide a drop-down list of available values.</span></span> <span data-ttu-id="f63a2-192">보고서 매개 변수가 만들어진 후에는 기본값을 변경해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f63a2-192">After the report parameters are created, you might have to change default values.</span></span> <span data-ttu-id="f63a2-193">자세한 내용은 [보고서 매개 변수&#40;보고서 작성기 및 보고서 디자이너&#41;](../report-design/report-parameters-report-builder-and-report-designer.md)에 대해 자세히 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="f63a2-193">For more information, see [Report Parameters &#40;Report Builder and Report Designer&#41;](../report-design/report-parameters-report-builder-and-report-designer.md).</span></span>



##  <a name="remarks"></a><a name="Remarks"></a> <span data-ttu-id="f63a2-194">주의</span><span class="sxs-lookup"><span data-stu-id="f63a2-194">Remarks</span></span>

###### <a name="alternate-data-extensions"></a><span data-ttu-id="f63a2-195">대체 데이터 확장 프로그램</span><span class="sxs-lookup"><span data-stu-id="f63a2-195">Alternate Data Extensions</span></span>
 <span data-ttu-id="f63a2-196">OLE DB 데이터 원본 유형을 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스에서 데이터를 검색할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f63a2-196">You can also retrieve data from a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database by using an ODBC data source type.</span></span> <span data-ttu-id="f63a2-197">OLE DB를 사용하여 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] 에 연결할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f63a2-197">Connecting to [!INCLUDE[ssSDS](../../includes/sssds-md.md)] by using OLE DB is not supported.</span></span>

 <span data-ttu-id="f63a2-198">자세한 내용은 [ODBC 연결 형식&#40;SSRS&#41;](odbc-connection-type-ssrs.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f63a2-198">For more information, see [ODBC Connection Type &#40;SSRS&#41;](odbc-connection-type-ssrs.md).</span></span>

###### <a name="platform-and-version-information"></a><span data-ttu-id="f63a2-199">플랫폼 및 버전 정보</span><span class="sxs-lookup"><span data-stu-id="f63a2-199">Platform and Version Information</span></span>
 <span data-ttu-id="f63a2-200">플랫폼 및 버전 지원에 대한 자세한 내용은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [온라인 설명서](https://go.microsoft.com/fwlink/?linkid=121312)의 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 설명서에서 [Reporting Services&#40;SSRS&#41;에서 지원하는 데이터 원본](../create-deploy-and-manage-mobile-and-paginated-reports.md).</span><span class="sxs-lookup"><span data-stu-id="f63a2-200">For more information about platform and version support, see [Data Sources Supported by Reporting Services &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md) in the [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] documentation in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?linkid=121312).</span></span>



##  <a name="how-to-topics"></a><a name="HowTo"></a><span data-ttu-id="f63a2-201">방법 도움말 항목</span><span class="sxs-lookup"><span data-stu-id="f63a2-201">How-To Topics</span></span>
 <span data-ttu-id="f63a2-202">이 섹션에서는 데이터 연결, 데이터 원본 및 데이터 세트를 사용하는 방법을 단계별로 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f63a2-202">This section contains step-by-step instructions for working with data connections, data sources, and datasets.</span></span>

 [<span data-ttu-id="f63a2-203">데이터 연결이 나 데이터 원본 &#40;보고서 작성기 및 SSRS를 추가 하 고 확인&#41;</span><span class="sxs-lookup"><span data-stu-id="f63a2-203">Add and Verify a Data Connection or Data Source &#40;Report Builder and SSRS&#41;</span></span>](add-and-verify-a-data-connection-report-builder-and-ssrs.md)

 [<span data-ttu-id="f63a2-204">공유 데이터 세트 또는 포함된 데이터 세트 만들기&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="f63a2-204">Create a Shared Dataset or Embedded Dataset &#40;Report Builder and SSRS&#41;</span></span>](create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md)

 [<span data-ttu-id="f63a2-205">데이터 세트에 필터 추가&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="f63a2-205">Add a Filter to a Dataset &#40;Report Builder and SSRS&#41;</span></span>](add-a-filter-to-a-dataset-report-builder-and-ssrs.md)



##  <a name="related-sections"></a><a name="Related"></a> <span data-ttu-id="f63a2-206">관련 섹션</span><span class="sxs-lookup"><span data-stu-id="f63a2-206">Related Sections</span></span>
 <span data-ttu-id="f63a2-207">설명서의 다음 섹션에서는 보고서 데이터에 대한 깊이 있는 개념 정보를 제공하며, 데이터와 관련된 보고서 부분을 정의, 사용자 지정 및 사용하는 방법을 절차적인 측면에서 소개합니다.</span><span class="sxs-lookup"><span data-stu-id="f63a2-207">These sections of the documentation provide in-depth conceptual information about report data, and procedural information about how to define, customize, and use parts of a report that are related to data.</span></span>

 <span data-ttu-id="f63a2-208">[보고서 &#40;보고서 작성기 및 SSRS&#41;에 데이터를 추가 합니다](report-datasets-ssrs.md) . 보고서의 데이터에 액세스 하는 방법에 대 한 개요를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="f63a2-208">[Add Data to a Report &#40;Report Builder and SSRS&#41;](report-datasets-ssrs.md) Provides an overview of accessing data for your report.</span></span>

 <span data-ttu-id="f63a2-209">[보고서 작성기의 데이터 연결, 데이터 원본 및 연결 문자열](../data-connections-data-sources-and-connection-strings-in-report-builder.md) 데이터 연결 및 데이터 원본에 대 한 정보를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="f63a2-209">[Data Connections, Data Sources, and Connection Strings in Report Builder](../data-connections-data-sources-and-connection-strings-in-report-builder.md) Provides information about data connections and data sources.</span></span>

 <span data-ttu-id="f63a2-210">[보고서 포함 된 데이터 집합 및 공유 데이터 집합 &#40;보고서 작성기 및 SSRS&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md) 포함 된 데이터 집합 및 공유 데이터 집합에 대 한 정보를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="f63a2-210">[Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md) Provides information about embedded and shared datasets.</span></span>

 <span data-ttu-id="f63a2-211">[데이터 집합 필드 컬렉션 &#40;보고서 작성기 및 SSRS&#41;](dataset-fields-collection-report-builder-and-ssrs.md) 쿼리에 의해 생성 되는 데이터 집합 필드 컬렉션에 대 한 정보를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="f63a2-211">[Dataset Fields Collection &#40;Report Builder and SSRS&#41;](dataset-fields-collection-report-builder-and-ssrs.md) Provides information about the dataset field collection generated by the query.</span></span>

 <span data-ttu-id="f63a2-212">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [온라인 설명서](https://go.microsoft.com/fwlink/?linkid=121312)에 있는 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 설명서의 [Reporting Services&#40;SSRS&#41;에서 지원하는 데이터 원본](../create-deploy-and-manage-mobile-and-paginated-reports.md).</span><span class="sxs-lookup"><span data-stu-id="f63a2-212">[Data Sources Supported by Reporting Services &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md) in the [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] documentation in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?linkid=121312).</span></span>
<span data-ttu-id="f63a2-213">각 데이터 확장 프로그램의 플랫폼 및 버전 지원에 대한 자세한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="f63a2-213">Provides in-depth information about platform and version support for each data extension.</span></span>



## <a name="see-also"></a><span data-ttu-id="f63a2-214">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f63a2-214">See Also</span></span>
 <span data-ttu-id="f63a2-215">[보고서 매개 변수 보고서 작성기 및 보고서 디자이너&#41;](../report-design/report-parameters-report-builder-and-report-designer.md) [필터링, 그룹화 및 정렬 데이터](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md) &#40;보고서 작성기 및 ssrs&#41;식 &#40;보고서 작성기 [및 ssrs](../report-design/expressions-report-builder-and-ssrs.md) 를 &#40;&#41;</span><span class="sxs-lookup"><span data-stu-id="f63a2-215">[Report Parameters &#40;Report Builder and Report Designer&#41;](../report-design/report-parameters-report-builder-and-report-designer.md) [Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md) [Expressions &#40;Report Builder and SSRS&#41;](../report-design/expressions-report-builder-and-ssrs.md)</span></span>


