---
title: ODBC 원본 편집기 (연결 관리자 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.designer.odbcsource.connection.f1
ms.assetid: e2c8dc83-6394-4d6c-9232-97e94be72431
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c8b54ce4a1c1b3fea0afb51f1cbf7447971ccab4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734352"
---
# <a name="odbc-source-editor-connection-manager-page"></a><span data-ttu-id="f5cd8-102">ODBC 원본 편집기(연결 관리자 페이지)</span><span class="sxs-lookup"><span data-stu-id="f5cd8-102">ODBC Source Editor (Connection Manager Page)</span></span>
  <span data-ttu-id="f5cd8-103">**ODBC 원본 편집기** 대화 상자의 **연결 관리자** 페이지를 사용하여 원본의 ODBC 연결 관리자를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f5cd8-103">Use the **Connection Manager** page of the **ODBC Source Editor** dialog box to select the ODBC connection manager for the source.</span></span> <span data-ttu-id="f5cd8-104">이 페이지를 사용하면 데이터베이스에서 테이블이나 뷰를 선택할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f5cd8-104">This page also lets you select a table or view from the database.</span></span>  
  
 <span data-ttu-id="f5cd8-105">ODBC 원본에 대한 자세한 내용은 [ODBC Source](data-flow/odbc-source.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="f5cd8-105">For more information about the ODBC source, see [ODBC Source](data-flow/odbc-source.md).</span></span>  
  
## <a name="task-list"></a><span data-ttu-id="f5cd8-106">작업 목록</span><span class="sxs-lookup"><span data-stu-id="f5cd8-106">Task List</span></span>  
 <span data-ttu-id="f5cd8-107">**ODBC 원본 편집기의 연결 관리자 페이지를 열려면**</span><span class="sxs-lookup"><span data-stu-id="f5cd8-107">**To open the ODBC Source Editor Connection Manager Page**</span></span>  
  
-   <span data-ttu-id="f5cd8-108">[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]에서 ODBC 원본이 있는 [!INCLUDE[ssISCurrent](../includes/ssiscurrent-md.md)] 패키지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="f5cd8-108">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], open the [!INCLUDE[ssISCurrent](../includes/ssiscurrent-md.md)] package that has the ODBC source.</span></span>  
  
-   <span data-ttu-id="f5cd8-109">**데이터 흐름** 탭에서 ODBC 원본을 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f5cd8-109">On the **Data Flow** tab, double-click the ODBC source.</span></span>  
  
## <a name="options"></a><span data-ttu-id="f5cd8-110">옵션</span><span class="sxs-lookup"><span data-stu-id="f5cd8-110">Options</span></span>  
  
### <a name="connection-manager"></a><span data-ttu-id="f5cd8-111">ODBC 대상 편집기</span><span class="sxs-lookup"><span data-stu-id="f5cd8-111">Connection manager</span></span>  
 <span data-ttu-id="f5cd8-112">목록에서 기존 ODBC 연결 관리자를 선택 하거나 **새로** 만들기를 클릭 하 여 새 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f5cd8-112">Select an existing ODBC connection manager from the list, or click **New** to create a new connection.</span></span> <span data-ttu-id="f5cd8-113">어느 ODBC 지원 데이터베이스에나 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f5cd8-113">The connection can be to any ODBC-supported database.</span></span>  
  
### <a name="new"></a><span data-ttu-id="f5cd8-114">새로 만들기</span><span class="sxs-lookup"><span data-stu-id="f5cd8-114">New</span></span>  
 <span data-ttu-id="f5cd8-115">**새로 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f5cd8-115">Click **New**.</span></span> <span data-ttu-id="f5cd8-116">새 ODBC 연결 관리자를 만들 수 있는 **ODBC 연결 관리자 편집기 구성** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="f5cd8-116">The **Configure ODBC Connection Manager Editor** dialog box opens where you can create a new ODBC connection manager.</span></span>  
  
### <a name="data-access-mode"></a><span data-ttu-id="f5cd8-117">데이터 액세스 모드</span><span class="sxs-lookup"><span data-stu-id="f5cd8-117">Data Access Mode</span></span>  
 <span data-ttu-id="f5cd8-118">원본에서 데이터를 선택하는 방법을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f5cd8-118">Select the method for selecting data from the source.</span></span> <span data-ttu-id="f5cd8-119">옵션은 다음 표에 표시되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f5cd8-119">The options are shown in the following table:</span></span>  
  
|<span data-ttu-id="f5cd8-120">옵션</span><span class="sxs-lookup"><span data-stu-id="f5cd8-120">Option</span></span>|<span data-ttu-id="f5cd8-121">Description</span><span class="sxs-lookup"><span data-stu-id="f5cd8-121">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="f5cd8-122">테이블 이름</span><span class="sxs-lookup"><span data-stu-id="f5cd8-122">Table Name</span></span>|<span data-ttu-id="f5cd8-123">ODBC 데이터 원본에 있는 테이블이나 뷰에서 데이터를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="f5cd8-123">Retrieve data from a table or view in the ODBC data source.</span></span> <span data-ttu-id="f5cd8-124">이 옵션을 선택할 경우 다음 목록에서 값을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f5cd8-124">When you select this option, select a value from the list for the following:</span></span>|  
||<span data-ttu-id="f5cd8-125">**테이블 또는 뷰 이름**: 목록에서 사용 가능한 테이블 또는 뷰를 선택하거나 테이블을 식별할 수 있는 정규식을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="f5cd8-125">**Name of the table or the view**: Select an available table or view from the list or type a regular expression to identify the table.</span></span>|  
||<span data-ttu-id="f5cd8-126">이 목록에는 처음 1000개의 테이블만 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f5cd8-126">This list contains the first 1000 tables only.</span></span> <span data-ttu-id="f5cd8-127">데이터베이스에 포함되어 있는 테이블이 1000개를 넘는 경우 테이블 이름의 시작 부분을 입력하거나 와일드카드(\*)를 통해 이름의 일부를 입력하여 사용할 테이블을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="f5cd8-127">If your database contains more than 1000 tables, you can type the beginning of a table name or use the (\*) wild card to enter any part of the name to display the table or tables you want to use.</span></span>|  
|<span data-ttu-id="f5cd8-128">SQL 명령</span><span class="sxs-lookup"><span data-stu-id="f5cd8-128">SQL command</span></span>|<span data-ttu-id="f5cd8-129">SQL 쿼리를 사용하여 ODBC 데이터 원본에서 데이터를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="f5cd8-129">Retrieve data from the ODBC data source by using an SQL query.</span></span> <span data-ttu-id="f5cd8-130">사용할 원본 데이터베이스의 구문으로 쿼리를 작성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f5cd8-130">You should write the query in the syntax of the source database you are working with.</span></span> <span data-ttu-id="f5cd8-131">이 옵션을 선택할 경우 다음 중 한 가지 방법으로 쿼리를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="f5cd8-131">When you select this option, enter a query in one of the following ways:</span></span>|  
||<span data-ttu-id="f5cd8-132">**SQL 명령 텍스트** 필드에 SQL 쿼리 텍스트를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="f5cd8-132">Enter the text of the SQL query in the **SQL command text** field.</span></span>|  
||<span data-ttu-id="f5cd8-133">**찾아보기** 를 클릭하여 텍스트 파일에서 SQL 쿼리를 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="f5cd8-133">Click **Browse** to load the SQL query from a text file.</span></span>|  
||<span data-ttu-id="f5cd8-134">**쿼리 구문 분석** 을 클릭하여 쿼리 텍스트의 구문을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="f5cd8-134">Click **Parse query** to verify the syntax of the query text.</span></span>|  
  
### <a name="preview"></a><span data-ttu-id="f5cd8-135">미리 보기</span><span class="sxs-lookup"><span data-stu-id="f5cd8-135">Preview</span></span>  
 <span data-ttu-id="f5cd8-136">**미리 보기** 를 클릭하면 선택한 테이블 또는 뷰에서 추출된 최대 200개의 데이터 행을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f5cd8-136">Click **Preview** to view up to the first 200 rows of the data extracted from the table or view you selected.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5cd8-137">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f5cd8-137">See Also</span></span>  
 <span data-ttu-id="f5cd8-138">[ODBC 원본 사용자 지정 속성](data-flow/odbc-source-custom-properties.md) </span><span class="sxs-lookup"><span data-stu-id="f5cd8-138">[ODBC Source Custom Properties](data-flow/odbc-source-custom-properties.md) </span></span>  
 <span data-ttu-id="f5cd8-139">[ODBC 원본 편집기 &#40;열 페이지&#41;](../../2014/integration-services/odbc-source-editor-columns-page.md) </span><span class="sxs-lookup"><span data-stu-id="f5cd8-139">[ODBC Source Editor &#40;Columns Page&#41;](../../2014/integration-services/odbc-source-editor-columns-page.md) </span></span>  
 [<span data-ttu-id="f5cd8-140">ODBC 원본 편집기&#40;오류 출력 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="f5cd8-140">ODBC Source Editor &#40;Error Output Page&#41;</span></span>](../../2014/integration-services/odbc-source-editor-error-output-page.md)  
  
  
