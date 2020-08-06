---
title: 텍스트 기반 쿼리 디자이너 사용자 인터페이스 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10010"
- sql12.rtp.rptdesigner.dataview.genericquerydesigner.f1
helpviewer_keywords:
- text-based query designer [Reporting Services]
- query designers [Reporting Services], text-based
ms.assetid: 44b7c664-03aa-494e-a484-052b318e810c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 1647d69246ba85dfbe0718799441c3687c0beca3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739075"
---
# <a name="text-based-query-designer-user-interface"></a><span data-ttu-id="b5ccd-102">텍스트 기반 쿼리 디자이너 사용자 인터페이스</span><span class="sxs-lookup"><span data-stu-id="b5ccd-102">Text-based Query Designer User Interface</span></span>
  <span data-ttu-id="b5ccd-103">텍스트 기반 쿼리 디자이너에서 데이터 원본에서 지원하는 쿼리 언어를 사용하여 쿼리를 지정하고, 쿼리를 실행하고, 디자인 타임에 결과를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b5ccd-103">Use the text-based query designer to specify a query using the query language supported by the data source, run the query, and view the results at design time.</span></span> <span data-ttu-id="b5ccd-104">여러 개의 [!INCLUDE[tsql](../includes/tsql-md.md)] 문, 사용자 지정 데이터 처리 확장 프로그램에 대한 쿼리 또는 명령 구문, 식으로 지정된 쿼리를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b5ccd-104">You can specify multiple [!INCLUDE[tsql](../includes/tsql-md.md)] statements, query or command syntax for custom data processing extensions, and queries that are specified as expressions.</span></span> <span data-ttu-id="b5ccd-105">텍스트 기반 쿼리 디자이너는 쿼리를 전처리하지 않고 모든 종류의 쿼리 구문을 포함할 수 있으므로 많은 데이터 원본 유형에 대한 기본 쿼리 디자이너 도구입니다.</span><span class="sxs-lookup"><span data-stu-id="b5ccd-105">Because the text-based query designer does not preprocess the query and can accommodate any kind of query syntax, this is the default query designer tool for many data source types.</span></span>

 <span data-ttu-id="b5ccd-106">텍스트 기반 쿼리 디자이너에서는 도구 모음과 다음과 같은 두 개의 창이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b5ccd-106">The text-based query designer displays a toolbar and the following two panes:</span></span>

-   <span data-ttu-id="b5ccd-107">**쿼리** 쿼리 텍스트, 테이블 이름 또는 저장 프로시저 이름을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="b5ccd-107">**Query** Shows the query text, table name, or stored procedure name.</span></span>

-   <span data-ttu-id="b5ccd-108">**결과** 디자인 타임에 쿼리 실행 결과를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="b5ccd-108">**Result** Shows the results of running the query at design time.</span></span>

## <a name="text-based-query-designer-toolbar"></a><span data-ttu-id="b5ccd-109">텍스트 기반 쿼리 디자이너 도구 모음</span><span class="sxs-lookup"><span data-stu-id="b5ccd-109">Text-based Query Designer Toolbar</span></span>
 <span data-ttu-id="b5ccd-110">텍스트 쿼리 디자이너는 모든 명령 유형을 위한 단일 도구 모음을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="b5ccd-110">The text-based query designer provides a single toolbar for all the command types.</span></span> <span data-ttu-id="b5ccd-111">다음 표에서는 도구 모음에 있는 각 단추와 해당 기능을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="b5ccd-111">The following table lists each button on the toolbar and its function.</span></span>

|<span data-ttu-id="b5ccd-112">단추</span><span class="sxs-lookup"><span data-stu-id="b5ccd-112">Button</span></span>|<span data-ttu-id="b5ccd-113">설명</span><span class="sxs-lookup"><span data-stu-id="b5ccd-113">Description</span></span>|
|------------|-----------------|
|<span data-ttu-id="b5ccd-114">**텍스트로 편집**</span><span class="sxs-lookup"><span data-stu-id="b5ccd-114">**Edit As Text**</span></span>|<span data-ttu-id="b5ccd-115">텍스트 기반 쿼리 디자이너와 그래픽 쿼리 디자이너 사이를 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="b5ccd-115">Toggle between the text-based query designer and the graphical query designer.</span></span> <span data-ttu-id="b5ccd-116">모든 데이터 원본 유형에서 그래픽 쿼리 디자이너를 지원하는 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="b5ccd-116">Not all data source types support graphical query designers.</span></span>|
|<span data-ttu-id="b5ccd-117">**가져오기**</span><span class="sxs-lookup"><span data-stu-id="b5ccd-117">**Import**</span></span>|<span data-ttu-id="b5ccd-118">파일 또는 보고서에서 기존 쿼리를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="b5ccd-118">Import an existing query from a file or report.</span></span> <span data-ttu-id="b5ccd-119">파일 유형 sql 및 rdl만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="b5ccd-119">Only file types sql and rdl are supported.</span></span> <span data-ttu-id="b5ccd-120">자세한 내용은 [보고서 포함된 데이터 세트 및 공유 데이터 세트&#40;보고서 작성기 및 SSRS&#41;](report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b5ccd-120">For more information, see [Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;](report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md).</span></span>|
|<span data-ttu-id="b5ccd-121">![쿼리 실행](../analysis-services/media/rsqdicon-run.gif "쿼리 실행")</span><span class="sxs-lookup"><span data-stu-id="b5ccd-121">![Run the query](../analysis-services/media/rsqdicon-run.gif "Run the query")</span></span>|<span data-ttu-id="b5ccd-122">쿼리를 실행하고 결과 창에 결과 집합을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="b5ccd-122">Run the query and display the result set in the Result pane.</span></span>|
|<span data-ttu-id="b5ccd-123">**명령 유형**</span><span class="sxs-lookup"><span data-stu-id="b5ccd-123">**Command Type**</span></span>|<span data-ttu-id="b5ccd-124">**Text**, **StoredProcedure**또는 **TableDirect**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b5ccd-124">Select **Text**, **StoredProcedure**, or **TableDirect**.</span></span> <span data-ttu-id="b5ccd-125">저장 프로시저에 매개 변수가 있을 경우 도구 모음에서 **실행** 을 클릭하면 **쿼리 매개 변수 정의** 대화 상자가 표시되며 필요에 따라 값을 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b5ccd-125">If a stored procedure has parameters, the **Define Query Parameters** dialog box appears when you click **Run** on the toolbar, and you can fill in values as needed.</span></span> <span data-ttu-id="b5ccd-126">저장 프로시저에서 둘 이상의 결과 집합을 반환 하는 경우 첫 번째 결과 집합만 데이터 집합을 채우는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b5ccd-126">Note that if a stored procedure returns more than one result set, only the first result set is used to populate the dataset.</span></span><br /><br /> <span data-ttu-id="b5ccd-127">명령 유형에 대한 지원은 데이터 원본 유형에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="b5ccd-127">Support for command type varies by data source type.</span></span> <span data-ttu-id="b5ccd-128">예를 들어 OLE DB 및 ODBC의 경우에만 **TableDirect**를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="b5ccd-128">For example, only OLE DB and ODBC support **TableDirect**.</span></span>|

### <a name="command-type-text"></a><span data-ttu-id="b5ccd-129">Text 명령 유형</span><span class="sxs-lookup"><span data-stu-id="b5ccd-129">Command Type Text</span></span>
 <span data-ttu-id="b5ccd-130">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 데이터 세트을 만들 때 기본적으로 보고서 디자이너에는 그래픽 쿼리 디자이너가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b5ccd-130">When you create a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] dataset, Report Designer displays the graphical query designer by default.</span></span> <span data-ttu-id="b5ccd-131">텍스트 기반 쿼리 디자이너로 전환하려면 도구 모음에서 **텍스트로 편집** 토글 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b5ccd-131">To switch to the text-based query designer, click the **Edit As Text** toggle button on the toolbar.</span></span> <span data-ttu-id="b5ccd-132">텍스트 기반 쿼리 디자이너에는 쿼리 창 및 결과 창이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="b5ccd-132">The text-based query designer presents two panes: the Query pane and the Result pane.</span></span> <span data-ttu-id="b5ccd-133">다음 그림에서는 레이블과 함께 각 창을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b5ccd-133">The following figure labels each pane.</span></span>

 <span data-ttu-id="b5ccd-134">![관계형 데이터 쿼리를 위한 일반 쿼리 디자이너](../analysis-services/media/rsqd-dsaw-sql-generic.gif "관계형 데이터 쿼리를 위한 일반 쿼리 디자이너")</span><span class="sxs-lookup"><span data-stu-id="b5ccd-134">![Generic query designer, for relational data query](../analysis-services/media/rsqd-dsaw-sql-generic.gif "Generic query designer, for relational data query")</span></span>

 <span data-ttu-id="b5ccd-135">다음 표에서는 각 창의 기능을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="b5ccd-135">The following table describes the function of each pane.</span></span>

|<span data-ttu-id="b5ccd-136">창</span><span class="sxs-lookup"><span data-stu-id="b5ccd-136">Pane</span></span>|<span data-ttu-id="b5ccd-137">함수</span><span class="sxs-lookup"><span data-stu-id="b5ccd-137">Function</span></span>|
|----------|--------------|
|<span data-ttu-id="b5ccd-138">쿼리</span><span class="sxs-lookup"><span data-stu-id="b5ccd-138">Query</span></span>|<span data-ttu-id="b5ccd-139">[!INCLUDE[tsql](../includes/tsql-md.md)] 쿼리 텍스트를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="b5ccd-139">Displays the [!INCLUDE[tsql](../includes/tsql-md.md)] query text.</span></span> <span data-ttu-id="b5ccd-140">이 창을 사용하여 [!INCLUDE[tsql](../includes/tsql-md.md)] 쿼리를 작성하거나 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b5ccd-140">Use this pane to write or edit a [!INCLUDE[tsql](../includes/tsql-md.md)] query.</span></span>|
|<span data-ttu-id="b5ccd-141">결과</span><span class="sxs-lookup"><span data-stu-id="b5ccd-141">Result</span></span>|<span data-ttu-id="b5ccd-142">쿼리 결과를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="b5ccd-142">Displays the results of the query.</span></span> <span data-ttu-id="b5ccd-143">쿼리를 실행하려면 아무 창이나 마우스 오른쪽 단추로 클릭한 다음 **실행**을 클릭하거나 도구 모음에서 **실행** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b5ccd-143">To run the query, right-click in any pane and click **Run**, or click the **Run** button on the toolbar.</span></span>|

#### <a name="example"></a><span data-ttu-id="b5ccd-144">예제</span><span class="sxs-lookup"><span data-stu-id="b5ccd-144">Example</span></span>
 <span data-ttu-id="b5ccd-145">다음 쿼리는 [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] 데이터베이스 `Contact` 테이블에서 성 목록을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="b5ccd-145">The following query returns the list of last names from the [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] database `Contact` table.</span></span>

```
SELECT LastName FROM Person.Person;
```

 <span data-ttu-id="b5ccd-146">`EXEC` 문을 비롯하여 Text 명령 유형에 대한 모든 [!INCLUDE[tsql](../includes/tsql-md.md)] 문을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b5ccd-146">You can use any [!INCLUDE[tsql](../includes/tsql-md.md)] statement for Command type Text, including `EXEC` statements.</span></span> <span data-ttu-id="b5ccd-147">다음 쿼리는 [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] 저장 프로시저를 호출 `uspGetEmployeeManagers` 하 고 id 번호가 1 인 직원에 대 한 명령 체인을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="b5ccd-147">The following query calls the [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] stored procedure `uspGetEmployeeManagers` and returns the chain-of-command for the employee with identification number 1.</span></span>

```
EXEC uspGetEmployeeManagers 1;
```

 <span data-ttu-id="b5ccd-148">도구 모음에서 **실행** 을 클릭할 경우 **쿼리** 창의 명령이 실행되고 **결과** 창에 결과가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b5ccd-148">When you click **Run** on the toolbar, the command in the **Query** pane runs and the results are displayed in the **Result** pane.</span></span>

### <a name="command-type-storedprocedure"></a><span data-ttu-id="b5ccd-149">StoredProcedure 명령 유형</span><span class="sxs-lookup"><span data-stu-id="b5ccd-149">Command Type StoredProcedure</span></span>
 <span data-ttu-id="b5ccd-150">**명령 typeStoredProcedure**를 선택하면 텍스트 기반 쿼리 디자이너에 쿼리 창 및 결과 창이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="b5ccd-150">When you select **Command typeStoredProcedure**, the text-based query designer presents two panes: the Query pane and the Result pane.</span></span> <span data-ttu-id="b5ccd-151">쿼리 창에 저장 프로시저 이름을 입력하고 도구 모음에서 **실행** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b5ccd-151">Enter the stored procedure name in the Query pane and click **Run** on the toolbar.</span></span> <span data-ttu-id="b5ccd-152">쿼리 매개 변수 정의 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="b5ccd-152">The Define Query Parameters dialog box opens.</span></span> <span data-ttu-id="b5ccd-153">저장 프로시저에 대한 매개 변수 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="b5ccd-153">Enter the parameter values for the stored procedure.</span></span> <span data-ttu-id="b5ccd-154">모든 저장 프로시저 매개 변수에 대해 보고서 매개 변수가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="b5ccd-154">A report parameter is created for every stored procedure parameter.</span></span>

#### <a name="example"></a><span data-ttu-id="b5ccd-155">예제</span><span class="sxs-lookup"><span data-stu-id="b5ccd-155">Example</span></span>
 <span data-ttu-id="b5ccd-156">다음 쿼리는 [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] 저장 프로시저 `uspGetEmployeeManagers`를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="b5ccd-156">The following query calls the [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] stored procedure `uspGetEmployeeManagers`.</span></span> <span data-ttu-id="b5ccd-157">쿼리를 실행할 때 직원 ID 번호 매개 변수에 대한 값을 입력해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b5ccd-157">You must enter a value for the employee identification number parameter when you run the query.</span></span>

```
uspGetEmployeeManagers;
```

### <a name="command-type-tabledirect"></a><span data-ttu-id="b5ccd-158">TableDirect 명령 유형</span><span class="sxs-lookup"><span data-stu-id="b5ccd-158">Command Type TableDirect</span></span>
 <span data-ttu-id="b5ccd-159">**명령 typeTableDirect**를 선택하면 텍스트 기반 쿼리 디자이너에 쿼리 창 및 결과 창이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="b5ccd-159">When you select **Command typeTableDirect**, the text-based query designer presents two panes: the Query pane and the Result pane.</span></span> <span data-ttu-id="b5ccd-160">테이블을 입력하고 **실행** 단추를 클릭할 경우 해당 테이블의 모든 열이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="b5ccd-160">When you enter a table and click the **Run** button, all the columns for that table are returned.</span></span>

#### <a name="example"></a><span data-ttu-id="b5ccd-161">예제</span><span class="sxs-lookup"><span data-stu-id="b5ccd-161">Example</span></span>
 <span data-ttu-id="b5ccd-162">다음 쿼리는 [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] 데이터베이스의 모든 고객에 대한 결과 집합을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="b5ccd-162">The following query returns a result set for all customers in the [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] database.</span></span>

 `Sales.Customer`

 <span data-ttu-id="b5ccd-163">Sales. Customer 테이블 이름을 입력 하는 경우에는 문을 만드는 것과 동일 합니다 [!INCLUDE[tsql](../includes/tsql-md.md)] `SELECT * FROM Sales.Customer;` .</span><span class="sxs-lookup"><span data-stu-id="b5ccd-163">When you enter the table name Sales.Customer, it is the equivalent of creating the [!INCLUDE[tsql](../includes/tsql-md.md)] statement `SELECT * FROM Sales.Customer;`.</span></span>

## <a name="see-also"></a><span data-ttu-id="b5ccd-164">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b5ccd-164">See Also</span></span>
 <span data-ttu-id="b5ccd-165">[보고서 디자이너 SQL Server Data Tools의 쿼리 디자인 도구 &#40;ssrs&#41;](report-data/query-design-tools-ssrs.md) [보고서 포함 된 데이터 집합 및 공유 데이터 집합 &#40;보고서 작성기 및 ssrs&#41;](report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md) [SQL Server 연결](report-data/sql-server-connection-type-ssrs.md) 형식 &#40;[ssrs&#41;](report-data/ole-db-connection-type-ssrs.md) [ODBC 연결](report-data/odbc-connection-type-ssrs.md) 형식 OLE DB Ssrs &#40;[보고서 포함 된 데이터 집합 및 공유 데이터 집합&#41;&#40;및 ssrs&#41;](report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md) [rsreportdesigner.config 구성 파일](report-server/rsreportdesigner-configuration-file.md)</span><span class="sxs-lookup"><span data-stu-id="b5ccd-165">[Query Design Tools in Report Designer SQL Server Data Tools &#40;SSRS&#41;](report-data/query-design-tools-ssrs.md) [Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;](report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md) [SQL Server Connection Type &#40;SSRS&#41;](report-data/sql-server-connection-type-ssrs.md) [OLE DB Connection Type &#40;SSRS&#41;](report-data/ole-db-connection-type-ssrs.md) [ODBC Connection Type &#40;SSRS&#41;](report-data/odbc-connection-type-ssrs.md) [Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;](report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md) [RSReportDesigner Configuration File](report-server/rsreportdesigner-configuration-file.md)</span></span>


