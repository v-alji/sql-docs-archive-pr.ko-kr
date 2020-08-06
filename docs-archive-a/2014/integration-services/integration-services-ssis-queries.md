---
title: Integration Services(SSIS) 쿼리 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Query Builder [Integration Services]
- queries [Integration Services]
- statements [Integration Services]
- queries [Integration Services], about queries in packages
ms.assetid: 8822bd29-4575-46c8-92a0-1a39bc2604c1
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5119ff27606ce4e43f65cc129f3caac764e78e0b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651157"
---
# <a name="integration-services-ssis-queries"></a><span data-ttu-id="9a9a2-102">Integration Services(SSIS) 쿼리</span><span class="sxs-lookup"><span data-stu-id="9a9a2-102">Integration Services (SSIS) Queries</span></span>
  <span data-ttu-id="9a9a2-103">SQL 쿼리는 SQL 실행 태스크, OLE DB 원본, OLE DB 대상 및 조회 변환에서 사용될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9a9a2-103">The Execute SQL task, the OLE DB source, the OLE DB destination, and the Lookup transformation can use SQL queries.</span></span> <span data-ttu-id="9a9a2-104">SQL 실행 태스크에서 SQL 문은 데이터베이스 개체 및 데이터를 생성, 업데이트 및 삭제할 수 있으며 저장 프로시저를 실행하고 SELECT 문을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9a9a2-104">In the Execute SQL task, the SQL statements can create, update, and delete database objects and data; run stored procedures; and perform SELECT statements.</span></span> <span data-ttu-id="9a9a2-105">OLE DB 원본 및 조회 변환에서 일반적으로 SQL 문은 SELECT 문 또는 EXEC 문입니다.</span><span class="sxs-lookup"><span data-stu-id="9a9a2-105">In the OLE DB source and the Lookup transformation, the SQL statements are typically SELECT statements or EXEC statements.</span></span> <span data-ttu-id="9a9a2-106">후자는 결과 집합을 반환하는 저장 프로시저를 가장 자주 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="9a9a2-106">The latter most frequently run stored procedures that return result sets.</span></span>  
  
 <span data-ttu-id="9a9a2-107">쿼리 유효성 여부를 확인하기 위해 구문 분석을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9a9a2-107">A query can be parsed to establish whether it is valid.</span></span> <span data-ttu-id="9a9a2-108">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]에 대한 연결을 사용하는 쿼리를 구문 분석하는 경우 쿼리를 구문 분석하고 실행한 다음 구문 분석 결과에 실행 결과(성공 또는 실패)를 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="9a9a2-108">When parsing a query that uses a connection to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], the query is parsed, executed, and the execution outcome (success or failure) is assigned to the parsing outcome.</span></span> <span data-ttu-id="9a9a2-109">쿼리가 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]이외의 데이터로의 연결을 사용하는 경우 문은 구문 분석만 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9a9a2-109">If the query uses a connection to a data other than [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], the statement is parsed only.</span></span>  
  
 <span data-ttu-id="9a9a2-110">SQL 문은 디자이너에 직접 입력하여 정의하거나 해당 문을 포함하는 파일 연결 또는 변수를 지정하여 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9a9a2-110">The SQL statement can be defined either by entering it directly in the designer, or by specifying a file connection or a variable that contains the statement.</span></span>  
  
## <a name="direct-input-sql"></a><span data-ttu-id="9a9a2-111">SQL 직접 입력</span><span class="sxs-lookup"><span data-stu-id="9a9a2-111">Direct Input SQL</span></span>  
 <span data-ttu-id="9a9a2-112">쿼리 작성기는 SQL 실행 태스크, OLE DB 원본, OLE DB 대상 및 조회 변환의 사용자 인터페이스에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9a9a2-112">Query Builder is available in the user interface for the Execute SQL task, the OLE DB source, the OLE DB destination, and the Lookup transformation.</span></span> <span data-ttu-id="9a9a2-113">쿼리 작성기를 사용하면 다음과 같은 이점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9a9a2-113">Query Builder offers the following advantages:</span></span>  
  
-   <span data-ttu-id="9a9a2-114">시각적으로 또는 SQL 명령으로 작업합니다.</span><span class="sxs-lookup"><span data-stu-id="9a9a2-114">Work visually or with SQL commands.</span></span>  
  
     <span data-ttu-id="9a9a2-115">쿼리 작성기는 쿼리를 시각적으로 구성하는 그래픽 창과 쿼리의 SQL 텍스트를 표시하는 텍스트 창을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="9a9a2-115">Query Builder includes graphical panes that compose your query visually and a text pane that displays the SQL text of your query.</span></span> <span data-ttu-id="9a9a2-116">그래픽 또는 텍스트 창에서 작업할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9a9a2-116">You can work in either the graphical or text panes.</span></span> <span data-ttu-id="9a9a2-117">쿼리 작성기는 뷰를 동기화하므로 쿼리 텍스트와 그래픽 표현이 항상 일치합니다.</span><span class="sxs-lookup"><span data-stu-id="9a9a2-117">Query Builder synchronizes the views so that the query text and graphical representation always match.</span></span>  
  
-   <span data-ttu-id="9a9a2-118">관련 테이블을 조인합니다.</span><span class="sxs-lookup"><span data-stu-id="9a9a2-118">Join related tables.</span></span>  
  
     <span data-ttu-id="9a9a2-119">둘 이상의 테이블을 쿼리에 추가하면 쿼리 작성기는 테이블이 관련되는 방법과 적절한 조인 명령을 생성하는 방법을 자동으로 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="9a9a2-119">If you add more than one table to your query, Query Builder automatically determines how the tables are related and constructs the appropriate join command.</span></span>  
  
-   <span data-ttu-id="9a9a2-120">데이터베이스를 쿼리 또는 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9a9a2-120">Query or update databases.</span></span>  
  
     <span data-ttu-id="9a9a2-121">쿼리 작성기에서 Transact-SQL SELECT 문을 사용하여 데이터를 반환하거나 데이터베이스에서 레코드를 업데이트, 추가 또는 삭제하는 쿼리를 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9a9a2-121">You can use Query Builder to return data using Transact-SQL SELECT statements, or to create queries that update, add, or delete records in a database.</span></span>  
  
-   <span data-ttu-id="9a9a2-122">결과를 보고 즉시 편집합니다.</span><span class="sxs-lookup"><span data-stu-id="9a9a2-122">View and edit results immediately.</span></span>  
  
     <span data-ttu-id="9a9a2-123">쿼리를 실행하고 레코드 집합을 표 형태로 사용하여 데이터베이스의 레코드를 스크롤하고 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9a9a2-123">You can execute your query and work with a recordset in a grid that lets you scroll through and edit records in the database.</span></span>  
  
 <span data-ttu-id="9a9a2-124">쿼리 작성기의 시각적 기능은 SELECT 문 작성으로 제한되지만 텍스트 창에 DELETE 및 UPDATE 문과 같은 다른 유형의 문을 위한 SQL을 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9a9a2-124">Although Query Builder is visually limited to creating SELECT queries, you can type the SQL for other types of statements such as DELETE and UPDATE statements in the text pane.</span></span> <span data-ttu-id="9a9a2-125">이때 입력한 SQL 문을 반영하도록 그래픽 창이 자동으로 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="9a9a2-125">The graphical pane is automatically updated to reflect the SQL statement that you typed.</span></span>  
  
 <span data-ttu-id="9a9a2-126">태스크 또는 데이터 흐름 구성 요소 대화 상자나 속성 창에 쿼리를 입력하여 직접 입력을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9a9a2-126">You can also provide direct input by typing the query in the task or data flow component dialog box or the Properties window.</span></span>  
  
 <span data-ttu-id="9a9a2-127">자세한 내용은 [Query Builder](../../2014/integration-services/query-builder.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9a9a2-127">For more information, see [Query Builder](../../2014/integration-services/query-builder.md).</span></span>  
  
## <a name="sql-in-files"></a><span data-ttu-id="9a9a2-128">파일 내의 SQL</span><span class="sxs-lookup"><span data-stu-id="9a9a2-128">SQL in Files</span></span>  
 <span data-ttu-id="9a9a2-129">SQL 실행 태스크의 SQL 문을 별도의 파일에 보관할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9a9a2-129">The SQL statement for the Execute SQL task can also reside in a separate file.</span></span> <span data-ttu-id="9a9a2-130">예를 들어 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]의 쿼리 작성기와 같은 도구를 사용하여 쿼리를 작성하고 파일로 저장한 다음 패키지를 실행할 때 파일에서 쿼리를 읽을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9a9a2-130">For example, you can write queries using tools such as the Query Editor in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], save the query to a file, and then read the query from the file when running a package.</span></span> <span data-ttu-id="9a9a2-131">이 파일에는 실행할 SQL 문과 주석만 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9a9a2-131">The file can contain only the SQL statements to run and comments.</span></span> <span data-ttu-id="9a9a2-132">파일에 저장된 SQL 문을 사용하려면 파일 이름 및 위치를 지정하는 파일 연결을 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9a9a2-132">To use a SQL statement stored in a file, you must provide a file connection that specifies the file name and location.</span></span> <span data-ttu-id="9a9a2-133">자세한 내용은 [File Connection Manager](connection-manager/file-connection-manager.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9a9a2-133">For more information, see [File Connection Manager](connection-manager/file-connection-manager.md).</span></span>  
  
## <a name="sql-in-variables"></a><span data-ttu-id="9a9a2-134">변수 내의 SQL</span><span class="sxs-lookup"><span data-stu-id="9a9a2-134">SQL in Variables</span></span>  
 <span data-ttu-id="9a9a2-135">SQL 실행 태스크의 SQL 문 원본이 변수인 경우 쿼리를 포함하는 변수의 이름을 지정하십시오.</span><span class="sxs-lookup"><span data-stu-id="9a9a2-135">If the source of the SQL statement in the Execute SQL task is a variable, you provide the name of the variable that contains the query.</span></span> <span data-ttu-id="9a9a2-136">쿼리 텍스트는 변수의 Value 속성에 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="9a9a2-136">The Value property of the variable contains the query text.</span></span> <span data-ttu-id="9a9a2-137">변수의 ValueType 속성을 문자열 데이터 형식으로 설정한 다음 Value 속성에 SQL 문을 입력하거나 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="9a9a2-137">You set the ValueType property of the variable to a string data type and then type or copy the SQL statement into the Value property.</span></span> <span data-ttu-id="9a9a2-138">자세한 내용은 [Integration Services&#40;SSIS&#41; 변수](integration-services-ssis-variables.md) 및 [패키지에서 변수 사용](../../2014/integration-services/use-variables-in-packages.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9a9a2-138">For more information, see [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md) and [Use Variables in Packages](../../2014/integration-services/use-variables-in-packages.md).</span></span>  
  
  
