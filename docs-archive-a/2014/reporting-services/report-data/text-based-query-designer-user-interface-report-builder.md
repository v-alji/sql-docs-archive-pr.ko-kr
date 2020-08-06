---
title: 텍스트 기반 쿼리 디자이너 사용자 인터페이스(보고서 작성기) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10010"
helpviewer_keywords:
- query designers, text-based
ms.assetid: 89fddca5-bd96-4128-9072-5348d1b6e02c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c1415bdfada46ac09c9ab04047d63484593933e8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639321"
---
# <a name="text-based-query-designer-user-interface-report-builder"></a><span data-ttu-id="ceddd-102">텍스트 기반 쿼리 디자이너 사용자 인터페이스(보고서 작성기)</span><span class="sxs-lookup"><span data-stu-id="ceddd-102">Text-based Query Designer User Interface (Report Builder)</span></span>
  <span data-ttu-id="ceddd-103">텍스트 기반 쿼리 디자이너에서 데이터 원본에서 지원하는 쿼리 언어를 사용하여 쿼리를 지정하고, 쿼리를 실행하고, 디자인 타임에 결과를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ceddd-103">Use the text-based query designer to specify a query using the query language supported by the data source, run the query, and view the results at design time.</span></span> <span data-ttu-id="ceddd-104">여러 개의 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 문, 사용자 지정 데이터 처리 확장 프로그램에 대한 쿼리 또는 명령 구문, 식으로 지정된 쿼리를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ceddd-104">You can specify multiple [!INCLUDE[tsql](../../../includes/tsql-md.md)] statements, query or command syntax for custom data processing extensions, and queries that are specified as expressions.</span></span> <span data-ttu-id="ceddd-105">텍스트 기반 쿼리 디자이너는 쿼리를 전처리하지 않고 모든 종류의 쿼리 구문을 포함할 수 있으므로 많은 데이터 원본 유형에 대한 기본 쿼리 디자이너 도구입니다.</span><span class="sxs-lookup"><span data-stu-id="ceddd-105">Because the text-based query designer does not preprocess the query and can accommodate any kind of query syntax, this is the default query designer tool for many data source types.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="ceddd-106">사용자는 쿼리를 작성하고 실행할 때 데이터 원본에 액세스합니다.</span><span class="sxs-lookup"><span data-stu-id="ceddd-106">Users access data sources when they create and run queries.</span></span> <span data-ttu-id="ceddd-107">데이터 원본에 대해서는 읽기 전용 권한과 같이 최소한의 사용 권한을 부여해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ceddd-107">You should grant minimal permissions on the data sources, such as read-only permissions.</span></span>

 <span data-ttu-id="ceddd-108">텍스트 기반 쿼리 디자이너에서는 도구 모음과 다음과 같은 두 개의 창이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="ceddd-108">The text-based query designer displays a toolbar and the following two panes:</span></span>

-   <span data-ttu-id="ceddd-109">**쿼리** 쿼리 유형에 따라 쿼리 텍스트, 테이블 이름 또는 저장 프로시저 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="ceddd-109">**Query** Shows the query text, table name, or stored procedure name depending on the query type.</span></span> <span data-ttu-id="ceddd-110">모든 데이터 원본 유형에서 모든 쿼리 유형을 사용할 수 있는 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="ceddd-110">Not all query types are available for all data source types.</span></span> <span data-ttu-id="ceddd-111">예를 들어 테이블 이름은 OLE DB와 같은 데이터 원본 유형에만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="ceddd-111">For example, table name is supported only for the data source type OLE DB.</span></span>

-   <span data-ttu-id="ceddd-112">**결과** 디자인 타임에 쿼리 실행 결과를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="ceddd-112">**Result** Shows the results of running the query at design time.</span></span>

## <a name="text-based-query-designer-toolbar"></a><span data-ttu-id="ceddd-113">텍스트 기반 쿼리 디자이너 도구 모음</span><span class="sxs-lookup"><span data-stu-id="ceddd-113">Text-based Query Designer Toolbar</span></span>
 <span data-ttu-id="ceddd-114">텍스트 쿼리 디자이너는 모든 명령 유형을 위한 단일 도구 모음을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="ceddd-114">The text-based query designer provides a single toolbar for all the command types.</span></span> <span data-ttu-id="ceddd-115">다음 표에서는 도구 모음에 있는 각 단추와 해당 기능을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="ceddd-115">The following table lists each button on the toolbar and its function.</span></span>

|<span data-ttu-id="ceddd-116">단추</span><span class="sxs-lookup"><span data-stu-id="ceddd-116">Button</span></span>|<span data-ttu-id="ceddd-117">설명</span><span class="sxs-lookup"><span data-stu-id="ceddd-117">Description</span></span>|
|------------|-----------------|
|<span data-ttu-id="ceddd-118">**텍스트로 편집**</span><span class="sxs-lookup"><span data-stu-id="ceddd-118">**Edit As Text**</span></span>|<span data-ttu-id="ceddd-119">텍스트 기반 쿼리 디자이너와 그래픽 쿼리 디자이너 사이를 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="ceddd-119">Toggle between the text-based query designer and the graphical query designer.</span></span> <span data-ttu-id="ceddd-120">모든 데이터 원본 유형에서 그래픽 쿼리 디자이너를 지원하는 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="ceddd-120">Not all data source types support graphical query designers.</span></span>|
|<span data-ttu-id="ceddd-121">**가져오기**</span><span class="sxs-lookup"><span data-stu-id="ceddd-121">**Import**</span></span>|<span data-ttu-id="ceddd-122">파일 또는 보고서에서 기존 쿼리를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ceddd-122">Import an existing query from a file or report.</span></span> <span data-ttu-id="ceddd-123">sql 및 rdl 파일 형식만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="ceddd-123">Only file types sql and rdl are supported</span></span>|
|<span data-ttu-id="ceddd-124">![쿼리 실행](../../analysis-services/media/rsqdicon-run.gif "쿼리 실행")</span><span class="sxs-lookup"><span data-stu-id="ceddd-124">![Run the query](../../analysis-services/media/rsqdicon-run.gif "Run the query")</span></span>|<span data-ttu-id="ceddd-125">쿼리를 실행하고 결과 창에 결과 집합을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="ceddd-125">Run the query and display the result set in the Result pane.</span></span>|
|<span data-ttu-id="ceddd-126">**명령 유형**</span><span class="sxs-lookup"><span data-stu-id="ceddd-126">**Command Type**</span></span>|<span data-ttu-id="ceddd-127">**Text**, **StoredProcedure**또는 **TableDirect**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ceddd-127">Select **Text**, **StoredProcedure**, or **TableDirect**.</span></span> <span data-ttu-id="ceddd-128">저장 프로시저에 매개 변수가 있을 경우 도구 모음에서 **실행** 을 클릭하면 **쿼리 매개 변수 정의** 대화 상자가 표시되며 필요에 따라 값을 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ceddd-128">If a stored procedure has parameters, the **Define Query Parameters** dialog box appears when you click **Run** on the toolbar, and you can fill in values as needed.</span></span><br /><br /> <span data-ttu-id="ceddd-129">참고: 저장 프로시저에서 둘 이상의 결과 세트를 반환할 경우 첫 번째 결과 집합만 데이터 세트를 채우는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="ceddd-129">Note: If a stored procedure returns more than one result set, only the first result set is used to populate the dataset.</span></span>|

### <a name="command-type-text"></a><span data-ttu-id="ceddd-130">Text 명령 유형</span><span class="sxs-lookup"><span data-stu-id="ceddd-130">Command Type Text</span></span>
 <span data-ttu-id="ceddd-131">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터 세트를 만들 때 기본적으로 관계형 쿼리 디자이너가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="ceddd-131">When you create a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dataset, the relational query designer opens by default.</span></span> <span data-ttu-id="ceddd-132">텍스트 기반 쿼리 디자이너로 전환하려면 도구 모음에서 **텍스트로 편집** 토글 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ceddd-132">To switch to the text-based query designer, click the **Edit As Text** toggle button on the toolbar.</span></span> <span data-ttu-id="ceddd-133">텍스트 기반 쿼리 디자이너에는 쿼리 창 및 결과 창이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="ceddd-133">The text-based query designer presents two panes: the Query pane and the Result pane.</span></span> <span data-ttu-id="ceddd-134">다음 그림에서는 레이블과 함께 각 창을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ceddd-134">The following figure labels each pane.</span></span>

 <span data-ttu-id="ceddd-135">![관계형 데이터 쿼리를 위한 일반 쿼리 디자이너](../../analysis-services/media/rsqd-dsaw-sql-generic.gif "관계형 데이터 쿼리를 위한 일반 쿼리 디자이너")</span><span class="sxs-lookup"><span data-stu-id="ceddd-135">![Generic query designer, for relational data query](../../analysis-services/media/rsqd-dsaw-sql-generic.gif "Generic query designer, for relational data query")</span></span>

 <span data-ttu-id="ceddd-136">다음 표에서는 각 창의 기능을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="ceddd-136">The following table describes the function of each pane.</span></span>

|<span data-ttu-id="ceddd-137">창</span><span class="sxs-lookup"><span data-stu-id="ceddd-137">Pane</span></span>|<span data-ttu-id="ceddd-138">함수</span><span class="sxs-lookup"><span data-stu-id="ceddd-138">Function</span></span>|
|----------|--------------|
|<span data-ttu-id="ceddd-139">쿼리</span><span class="sxs-lookup"><span data-stu-id="ceddd-139">Query</span></span>|<span data-ttu-id="ceddd-140">[!INCLUDE[tsql](../../../includes/tsql-md.md)] 쿼리 텍스트를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="ceddd-140">Displays the [!INCLUDE[tsql](../../../includes/tsql-md.md)] query text.</span></span> <span data-ttu-id="ceddd-141">이 창을 사용하여 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 쿼리를 작성하거나 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ceddd-141">Use this pane to write or edit a [!INCLUDE[tsql](../../../includes/tsql-md.md)] query.</span></span>|
|<span data-ttu-id="ceddd-142">결과</span><span class="sxs-lookup"><span data-stu-id="ceddd-142">Result</span></span>|<span data-ttu-id="ceddd-143">쿼리 결과를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="ceddd-143">Displays the results of the query.</span></span> <span data-ttu-id="ceddd-144">쿼리를 실행하려면 아무 창이나 마우스 오른쪽 단추로 클릭한 다음 **실행**을 클릭하거나 도구 모음에서 **실행** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ceddd-144">To run the query, right-click in any pane and click **Run**, or click the **Run** button on the toolbar.</span></span>|

#### <a name="example"></a><span data-ttu-id="ceddd-145">예제</span><span class="sxs-lookup"><span data-stu-id="ceddd-145">Example</span></span>
 <span data-ttu-id="ceddd-146">다음 쿼리는 [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] **2008** 데이터베이스 `ContactType` 테이블에서 스키마에 대 한 마지막 이름 목록을 반환 합니다 `Person` .</span><span class="sxs-lookup"><span data-stu-id="ceddd-146">The following query returns the list of last names from the [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)]**2008** database `ContactType` table for the `Person` schema.</span></span>

```
SELECT Name FROM Person.ContactType
```

 <span data-ttu-id="ceddd-147">도구 모음에서 **실행** 을 클릭할 경우 **쿼리** 창의 명령이 실행되고 **결과** 창에 결과가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="ceddd-147">When you click **Run** on the toolbar, the command in the **Query** pane runs and the results are displayed in the **Result** pane.</span></span> <span data-ttu-id="ceddd-148">결과 집합에 소유자 또는 영업 담당자 등의 20가지 연락처 유형이 있는 목록이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="ceddd-148">The resultset displays a list of 20 types of contacts, for example, Owner or Sales Agent.</span></span>

### <a name="command-type-storedprocedure"></a><span data-ttu-id="ceddd-149">StoredProcedure 명령 유형</span><span class="sxs-lookup"><span data-stu-id="ceddd-149">Command Type StoredProcedure</span></span>
 <span data-ttu-id="ceddd-150">**명령 typeStoredProcedure**를 선택하면 텍스트 기반 쿼리 디자이너에 쿼리 창 및 결과 창이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="ceddd-150">When you select **Command typeStoredProcedure**, the text-based query designer presents two panes: the Query pane and the Result pane.</span></span> <span data-ttu-id="ceddd-151">쿼리 창에 저장 프로시저 이름을 입력하고 도구 모음에서 **실행** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ceddd-151">Enter the stored procedure name in the Query pane and click **Run** on the toolbar.</span></span> <span data-ttu-id="ceddd-152">저장 프로시저에서 매개 변수를 사용하는 경우 **쿼리 매개 변수 정의** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="ceddd-152">If the stored procedures uses parameters, the **Define Query Parameters** dialog box opens.</span></span> <span data-ttu-id="ceddd-153">저장 프로시저에 대한 매개 변수 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="ceddd-153">Enter the parameter values for the stored procedure.</span></span> <span data-ttu-id="ceddd-154">모든 저장 프로시저 입력 매개 변수에 대해 보고서 매개 변수가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="ceddd-154">A report parameter is created for every stored procedure input parameter.</span></span>

 <span data-ttu-id="ceddd-155">다음 그림에서는 저장 프로시저를 실행할 때 쿼리 및 결과 창을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ceddd-155">The following figure shows the Query and Results panes when you run a stored procedure.</span></span> <span data-ttu-id="ceddd-156">이 경우 입력 매개 변수는 상수입니다.</span><span class="sxs-lookup"><span data-stu-id="ceddd-156">In this case, the input parameters are constants.</span></span>

 <span data-ttu-id="ceddd-157">![텍스트 기반 쿼리 디자이너의 저장 프로시저](../../analysis-services/media/rs-relational-text-sp.gif "텍스트 기반 쿼리 디자이너의 저장 프로시저")</span><span class="sxs-lookup"><span data-stu-id="ceddd-157">![Stored procedure in text-based query designer](../../analysis-services/media/rs-relational-text-sp.gif "Stored procedure in text-based query designer")</span></span>

 <span data-ttu-id="ceddd-158">다음 표에서는 각 창의 기능을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="ceddd-158">The following table describes the function of each pane.</span></span>

|<span data-ttu-id="ceddd-159">창</span><span class="sxs-lookup"><span data-stu-id="ceddd-159">Pane</span></span>|<span data-ttu-id="ceddd-160">함수</span><span class="sxs-lookup"><span data-stu-id="ceddd-160">Function</span></span>|
|----------|--------------|
|<span data-ttu-id="ceddd-161">쿼리</span><span class="sxs-lookup"><span data-stu-id="ceddd-161">Query</span></span>|<span data-ttu-id="ceddd-162">저장 프로시저의 이름 및 입력 매개 변수(있는 경우)를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="ceddd-162">Displays the name of the stored procedure and any input parameters.</span></span>|
|<span data-ttu-id="ceddd-163">결과</span><span class="sxs-lookup"><span data-stu-id="ceddd-163">Result</span></span>|<span data-ttu-id="ceddd-164">쿼리 결과를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="ceddd-164">Displays the results of the query.</span></span> <span data-ttu-id="ceddd-165">쿼리를 실행하려면 아무 창이나 마우스 오른쪽 단추로 클릭한 다음 **실행**을 클릭하거나 도구 모음에서 **실행** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ceddd-165">To run the query, right-click in any pane and click **Run**, or click the **Run** button on the toolbar.</span></span>|

#### <a name="example"></a><span data-ttu-id="ceddd-166">예제</span><span class="sxs-lookup"><span data-stu-id="ceddd-166">Example</span></span>
 <span data-ttu-id="ceddd-167">다음 쿼리는 [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] **2008** 저장 프로시저를 호출 합니다 `uspGetWhereUsedProductID` .</span><span class="sxs-lookup"><span data-stu-id="ceddd-167">The following query calls the [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)]**2008** stored procedure `uspGetWhereUsedProductID`.</span></span> <span data-ttu-id="ceddd-168">쿼리를 실행할 때 제품 ID 번호 매개 변수에 대한 값을 입력해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ceddd-168">You must enter a value for the product identification number parameter when you run the query.</span></span>

```
uspGetWhereUsedProductID
```

 <span data-ttu-id="ceddd-169">**실행** ( **!** ) 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ceddd-169">Click the **Run** (**!**) button.</span></span> <span data-ttu-id="ceddd-170">쿼리 매개 변수를 입력하라는 메시지가 표시되면 다음 표를 사용하여 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="ceddd-170">When prompted for the query parameters, use the following table to enter values.</span></span>

|||
|-|-|
|*@StartProductID*|<span data-ttu-id="ceddd-171">820</span><span class="sxs-lookup"><span data-stu-id="ceddd-171">820</span></span>|
|*@CheckDate*|<span data-ttu-id="ceddd-172">20010115</span><span class="sxs-lookup"><span data-stu-id="ceddd-172">20010115</span></span>|

 <span data-ttu-id="ceddd-173">지정된 날짜에 대해 지정된 구성 요소 번호가 사용된 13개 제품 ID가 있는 목록이 결과 집합에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="ceddd-173">For the specified date, the result set displays a list of 13 product identifiers that used the specified component number.</span></span>

### <a name="command-type-tabledirect"></a><span data-ttu-id="ceddd-174">TableDirect 명령 유형</span><span class="sxs-lookup"><span data-stu-id="ceddd-174">Command Type TableDirect</span></span>
 <span data-ttu-id="ceddd-175">**명령 typeTableDirect**를 선택하면 텍스트 기반 쿼리 디자이너에 쿼리 창 및 결과 창이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="ceddd-175">When you select **Command typeTableDirect**, the text-based query designer presents two panes: the Query pane and the Result pane.</span></span> <span data-ttu-id="ceddd-176">테이블을 입력하고 **실행** 단추를 클릭할 경우 해당 테이블의 모든 열이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="ceddd-176">When you enter a table and click the **Run** button, all the columns for that table are returned.</span></span>

#### <a name="example"></a><span data-ttu-id="ceddd-177">예제</span><span class="sxs-lookup"><span data-stu-id="ceddd-177">Example</span></span>
 <span data-ttu-id="ceddd-178">OLE DB 데이터 원본 유형의 경우 다음 데이터 집합 쿼리는 2008 데이터베이스에 있는 모든 연락처 유형에 대 한 결과 집합을 반환 합니다 [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] **2008** .</span><span class="sxs-lookup"><span data-stu-id="ceddd-178">For a data source type OLE DB, the following dataset query returns a result set for all contact types in the [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)]**2008** database.</span></span>

 `Person.ContactType`

 <span data-ttu-id="ceddd-179">테이블 이름 Person.ContactType을 입력하면 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 문 `SELECT * FROM Person.ContactType`을 만드는 것과 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="ceddd-179">When you enter the table name Person.ContactType, it is the equivalent of creating the [!INCLUDE[tsql](../../../includes/tsql-md.md)] statement `SELECT * FROM Person.ContactType`.</span></span>

## <a name="see-also"></a><span data-ttu-id="ceddd-180">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ceddd-180">See Also</span></span>
 <span data-ttu-id="ceddd-181">[관계형 쿼리 디자이너 사용자 인터페이스 &#40;보고서 작성기&#41;](relational-query-designer-user-interface-report-builder.md) [쿼리 디자이너 &#40;보고서 작성기](../query-designers-report-builder.md)</span><span class="sxs-lookup"><span data-stu-id="ceddd-181">[Relational Query Designer User Interface &#40;Report Builder&#41;](relational-query-designer-user-interface-report-builder.md) [Query Designers &#40;Report Builder&#41;](../query-designers-report-builder.md)</span></span>


