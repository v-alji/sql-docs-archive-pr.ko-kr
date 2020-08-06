---
title: SharePoint 목록 쿼리 디자이너 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 593de30c-69f0-42a8-8467-16e78647b74c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 018b525cb68972f579aebfbfec70d0b94afc4b55
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729027"
---
# <a name="sharepoint-list-query-designer"></a><span data-ttu-id="3c7af-102">SharePoint 목록 쿼리 디자이너</span><span class="sxs-lookup"><span data-stu-id="3c7af-102">SharePoint List Query Designer</span></span>
  <span data-ttu-id="3c7af-103">보고서 디자이너는 SharePoint 사이트에서 보고서 데이터 세트에 대해 검색할 데이터를 지정하는 쿼리를 만들 수 있도록 그래픽 쿼리 디자이너와 텍스트 기반 쿼리 디자이너를 모두 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="3c7af-103">Report Designer provides both a graphical query designer and a text-based query designer to help you create a query that specifies the data to retrieve from a SharePoint site for a report dataset.</span></span> <span data-ttu-id="3c7af-104">그래픽 쿼리 디자이너를 사용하면 SharePoint 목록 메타데이터를 탐색하고, 쿼리를 대화형으로 작성하고, 쿼리 결과를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3c7af-104">Use the graphical query designer to explore the SharePoint list metadata, interactively build a query, and view the results of your query.</span></span> <span data-ttu-id="3c7af-105">텍스트 기반 쿼리 디자이너를 사용하면 그래픽 쿼리 디자이너로 만든 쿼리를 보거나 쿼리를 수정하거나 쿼리 명령을 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3c7af-105">Use the text-based query designer to view the query that was built by the graphical query designer, modify a query, or type the query commands.</span></span> <span data-ttu-id="3c7af-106">파일 또는 보고서에서 기존 쿼리를 가져올 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3c7af-106">You can also import an existing query from a file or report.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="3c7af-107">사용자는 쿼리를 작성하고 실행할 때 데이터 원본에 액세스합니다.</span><span class="sxs-lookup"><span data-stu-id="3c7af-107">Users access data sources when they create and run queries.</span></span> <span data-ttu-id="3c7af-108">데이터 원본에 대해서는 읽기 전용 권한과 같이 최소한의 사용 권한을 부여해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c7af-108">You should grant minimal permissions on the data sources, such as read-only permissions.</span></span>  
  
## <a name="graphical-query-designer"></a><span data-ttu-id="3c7af-109">그래픽 쿼리 디자이너</span><span class="sxs-lookup"><span data-stu-id="3c7af-109">Graphical Query Designer</span></span>  
 <span data-ttu-id="3c7af-110">그래픽 쿼리 디자이너에서는 SharePoint 사이트를 탐색하고 데이터 세트에 대한 SharePoint 목록 데이터를 검색하는 명령을 대화형으로 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3c7af-110">In the graphical query designer you can explorer the SharePoint site, interactively build the command that retrieve SharePoint list data for a dataset.</span></span> <span data-ttu-id="3c7af-111">데이터 세트에 포함할 필드를 선택하고 필요에 따라 데이터 세트의 데이터를 제한할 필터를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3c7af-111">You choose the fields to include in the dataset and optionally, specify filters that limit the data in the dataset.</span></span> <span data-ttu-id="3c7af-112">필터를 매개 변수로 사용하여 런타임에 필터의 값을 제공하도록 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3c7af-112">You can specify that filters are used as parameters and provide the value of the filter at run-time.</span></span>  
  
 <span data-ttu-id="3c7af-113">SharePoint 목록에는 보고서에 별로 필요하지 않을 수 있는 SharePoint 관련 필드가 많이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3c7af-113">SharePoint lists include a large number of SharePoint specific fields that might not be useful to include in reports.</span></span> <span data-ttu-id="3c7af-114">쿼리 디자이너에서는 사용할 필드를 더 쉽고 빠르게 확인할 수 있도록 이러한 필드를 숨길 수 있는 옵션을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="3c7af-114">The query designer provides an option to hide these fields to make it easier and quicker to determine the fields to use.</span></span>  
  
 <span data-ttu-id="3c7af-115">그래픽 쿼리 디자이너는 다음 세 영역으로 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c7af-115">The graphical query designer is divided into three areas</span></span>  
  
-   <span data-ttu-id="3c7af-116">사용할 목록 항목과 필드를 선택하는 탐색 창</span><span class="sxs-lookup"><span data-stu-id="3c7af-116">Explore pane in which you select the list items and their fields to use.</span></span>  
  
-   <span data-ttu-id="3c7af-117">쿼리를 작성하는 디자인 영역</span><span class="sxs-lookup"><span data-stu-id="3c7af-117">Design area in which you build the query.</span></span>  
  
-   <span data-ttu-id="3c7af-118">쿼리 결과가 표시되는 결과 창</span><span class="sxs-lookup"><span data-stu-id="3c7af-118">Results pane in which you view the query results.</span></span>  
  
 <span data-ttu-id="3c7af-119">다음 그림에서는 SharePoint 목록과 함께 사용할 때의 그래픽 쿼리 디자이너를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="3c7af-119">The following figure shows the graphical query designer when it is used with SharePoint lists.</span></span>  
  
 <span data-ttu-id="3c7af-120">![rsQD_Relational_Graphical_SharePoint](media/rsqd-relational-graphical-sharepoint.gif "rsQD_Relational_Graphical_SharePoint")</span><span class="sxs-lookup"><span data-stu-id="3c7af-120">![rsQD_Relational_Graphical_SharePoint](media/rsqd-relational-graphical-sharepoint.gif "rsQD_Relational_Graphical_SharePoint")</span></span>  
  
 <span data-ttu-id="3c7af-121">다음 표에서는 각 창의 기능을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="3c7af-121">The following table describes the function of each pane.</span></span>  
  
 [<span data-ttu-id="3c7af-122">SharePoint 목록</span><span class="sxs-lookup"><span data-stu-id="3c7af-122">SharePoint Lists</span></span>](#DatabaseView)  
 <span data-ttu-id="3c7af-123">SharePoint 목록과 해당 목록에 있는 각 항목 내의 필드를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="3c7af-123">Displays SharePoint lists and the fields within each item in the list.</span></span>  
  
 [<span data-ttu-id="3c7af-124">선택한 필드</span><span class="sxs-lookup"><span data-stu-id="3c7af-124">Selected fields</span></span>](#SelectedFields)  
 <span data-ttu-id="3c7af-125">SharePoint 목록 창에서 선택된 항목의 SharePoint 목록 필드 이름 목록을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="3c7af-125">Displays the list of SharePoint list field names from the selected items in the SharePoint Lists pane.</span></span> <span data-ttu-id="3c7af-126">이러한 필드는 보고서 데이터 세트에 대한 필드 컬렉션이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c7af-126">These fields become the field collection for the report dataset.</span></span>  
  
 [<span data-ttu-id="3c7af-127">적용된 필터</span><span class="sxs-lookup"><span data-stu-id="3c7af-127">Applied filters</span></span>](#AppliedFilters)  
 <span data-ttu-id="3c7af-128">데이터베이스 뷰의 테이블 또는 뷰에 대한 필드 및 필터 조건 목록을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="3c7af-128">Displays a list of fields and filter criteria for tables or views in the Database view.</span></span>  
  
 [<span data-ttu-id="3c7af-129">쿼리 결과</span><span class="sxs-lookup"><span data-stu-id="3c7af-129">Query results</span></span>](#QueryResults)  
 <span data-ttu-id="3c7af-130">자동으로 생성된 쿼리의 결과 집합에 대한 예제 데이터를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="3c7af-130">Displays sample data for the result set for the automatically generated query.</span></span>  
  
###  <a name="sharepoint-lists-pane"></a><a name="DatabaseView"></a><span data-ttu-id="3c7af-131">SharePoint 목록 창</span><span class="sxs-lookup"><span data-stu-id="3c7af-131">SharePoint Lists Pane</span></span>  
 <span data-ttu-id="3c7af-132">SharePoint 목록 창에는 데이터 원본 연결 및 자격 증명에 따라 사용자가 볼 수 있는 권한이 있는 데이터베이스 개체에 대한 메타데이터가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c7af-132">The SharePoint Lists pane displays the metadata for database objects that you have the permissions to view, which is determined by the data source connection and credentials.</span></span> <span data-ttu-id="3c7af-133">데이터베이스 스키마별로 구성된 데이터베이스 개체가 계층 뷰에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c7af-133">The hierarchical view displays database objects organized by database schema.</span></span> <span data-ttu-id="3c7af-134">각 스키마 노드를 확장하여 테이블,  뷰,  저장 프로시저 및 테이블 반환 함수를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3c7af-134">Expand the node for each schema to view tables, views, stored procedures, and table-valued functions.</span></span> <span data-ttu-id="3c7af-135">열을 표시하려면 테이블이나 뷰를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="3c7af-135">Expand a table or view to display the columns.</span></span>  
  
###  <a name="selected-fields-pane"></a><a name="SelectedFields"></a> <span data-ttu-id="3c7af-136">선택한 필드 창</span><span class="sxs-lookup"><span data-stu-id="3c7af-136">Selected Fields Pane</span></span>  
 <span data-ttu-id="3c7af-137">선택한 필드 창에는 SharePoint 목록 항목에 대해 선택한 목록 항목 필드가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c7af-137">The Selected Fields pane displays the list item fields that you select for SharePoint list items.</span></span> <span data-ttu-id="3c7af-138">이 창에 표시되는 필드는 보고서 데이터 세트의 필드 컬렉션이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c7af-138">The fields that are displayed in this pane become the field collection for the report dataset.</span></span> <span data-ttu-id="3c7af-139">데이터 세트와 쿼리를 만든 후 보고서 데이터 창에서 보고서 데이터 세트의 필드 컬렉션을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3c7af-139">After you create a dataset and a query, use the Report Data pane to view the field collection for a report dataset.</span></span> <span data-ttu-id="3c7af-140">이러한 필드는 보고서를 볼 때 테이블,  차트 및 기타 보고서 항목에 표시할 수 있는 데이터를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="3c7af-140">These fields represent the data you can display in tables, charts, and other report items when you view a report.</span></span>  
  
 <span data-ttu-id="3c7af-141">선택한 필드 창에 필드를 추가하거나 제거하려면 SharePoint 목록 창에서 해당 테이블 또는 뷰 필드의 확인란을 선택하거나 선택 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="3c7af-141">To add or remove fields to this pane, select or clear check boxes for the table or view fields in the SharePoint Lists pane.</span></span>  
  
###  <a name="applied-filters-pane"></a><a name="AppliedFilters"></a> <span data-ttu-id="3c7af-142">적용된 필터 창</span><span class="sxs-lookup"><span data-stu-id="3c7af-142">Applied Filters Pane</span></span>  
 <span data-ttu-id="3c7af-143">적용된 필터 창에는 런타임에 검색되는 데이터 행 수를 제한하는 데 사용되는 조건이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c7af-143">The Applied Filters pane displays the criteria that are used to limit the number of rows of data that are retrieved at run-time.</span></span> <span data-ttu-id="3c7af-144">이 창에 지정된 조건을 사용하여 [!INCLUDE[tsql](../includes/tsql-md.md)] WHERE 절이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c7af-144">Criteria specified in this pane are used to generate a [!INCLUDE[tsql](../includes/tsql-md.md)] WHERE clause.</span></span> <span data-ttu-id="3c7af-145">매개 변수 옵션을 선택하면 보고서 매개 변수가 자동으로 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c7af-145">When you select the parameter option, a report parameter is automatically created.</span></span> <span data-ttu-id="3c7af-146">쿼리 매개 변수에 기반을 둔 보고서 매개 변수를 사용하면 사용자가 쿼리 값을 지정하여 보고서의 데이터를 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3c7af-146">Report parameters that are based on query parameters enable a user to specify values for the query to control the data in the report.</span></span>  
  
 <span data-ttu-id="3c7af-147">표시되는 열은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="3c7af-147">The following columns are displayed:</span></span>  
  
-   <span data-ttu-id="3c7af-148">**필드 이름** 조건을 적용할 필드 이름이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c7af-148">**Field Name** Displays the name of the field to apply the criteria to.</span></span>  
  
-   <span data-ttu-id="3c7af-149">**연산자** 필터 식에서 사용할 연산자가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c7af-149">**Operator** Displays the operation to use in the filter expression.</span></span>  
  
-   <span data-ttu-id="3c7af-150">**값** 필터 식에 사용할 값이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c7af-150">**Value** Displays the value to use in the filter expression.</span></span>  
  
-   <span data-ttu-id="3c7af-151">**매개 변수** 쿼리 매개 변수를 쿼리에 추가하기 위한 옵션이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c7af-151">**Parameter** Displays the option to add a query parameter to the query.</span></span> <span data-ttu-id="3c7af-152">쿼리 매개 변수와 보고서 매개 변수 간의 관계를 보려면 데이터 세트 속성을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="3c7af-152">Use the Dataset properties to view the relationship between query parameter and report parameter.</span></span>  
  
###  <a name="query-results-pane"></a><a name="QueryResults"></a> <span data-ttu-id="3c7af-153">쿼리 결과 창</span><span class="sxs-lookup"><span data-stu-id="3c7af-153">Query Results Pane</span></span>  
 <span data-ttu-id="3c7af-154">쿼리 결과 창에는 다른 창의 선택 내용에 따라 지정되어 자동으로 생성된 쿼리에 대한 결과가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c7af-154">The Query results pane displays the results for the automatically generated query that is specified by selections in the other panes.</span></span> <span data-ttu-id="3c7af-155">결과 집합의 열은 선택한 필드 창에서 지정한 필드이며 행 데이터는 적용된 필터 창에서 지정한 필터에 따라 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c7af-155">The columns in the result set are the fields that you specify in the Selected Fields pane and the row data is limited by the filters that you specify in the Applied Filters pane.</span></span>  
  
 <span data-ttu-id="3c7af-156">이 데이터는 쿼리를 실행할 때의 데이터 원본의 값을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="3c7af-156">This data represents values from the data source at the time that you run the query.</span></span> <span data-ttu-id="3c7af-157">이 데이터는 보고서 정의에 저장되지 않습니다.  보고서의 실제 데이터는 보고서를 처리할 때 검색됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c7af-157">The data is not saved in the report definition .The actual data in the report is retrieved when the report is processed.</span></span>  
  
 <span data-ttu-id="3c7af-158">결과 집합의 정렬 순서는 데이터 원본에서 데이터가 검색되는 순서에 따라 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c7af-158">Sort order in the result set is determined by the order the data is retrieved from the data source.</span></span> <span data-ttu-id="3c7af-159">보고서 데이터를 검색한 후 쿼리를 수정하여 정렬 순서를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3c7af-159">Sort order can be changed by modifying the query or after the data is retrieved for the report.</span></span>  
  
### <a name="graphical-query-designer-toolbar"></a><span data-ttu-id="3c7af-160">그래픽 쿼리 디자이너 도구 모음</span><span class="sxs-lookup"><span data-stu-id="3c7af-160">Graphical Query Designer Toolbar</span></span>  
 <span data-ttu-id="3c7af-161">관계형 쿼리 디자이너 도구 모음은 쿼리 결과를 지정하거나 보는 데 사용할 수 있는 다음 단추를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="3c7af-161">The relational query designer toolbar provides the following buttons to help you specify or view the results of a query.</span></span>  
  
|<span data-ttu-id="3c7af-162">단추</span><span class="sxs-lookup"><span data-stu-id="3c7af-162">Button</span></span>|<span data-ttu-id="3c7af-163">설명</span><span class="sxs-lookup"><span data-stu-id="3c7af-163">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="3c7af-164">**텍스트로 편집**</span><span class="sxs-lookup"><span data-stu-id="3c7af-164">**Edit As Text**</span></span>|<span data-ttu-id="3c7af-165">자동으로 생성된 쿼리를 보거나 쿼리를 수정할 수 있도록 텍스트 기반 쿼리 디자이너로 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="3c7af-165">Toggle to the text-based query designer to view the automatically generated query or to modify the query.</span></span>|  
|<span data-ttu-id="3c7af-166">**가져오기**</span><span class="sxs-lookup"><span data-stu-id="3c7af-166">**Import**</span></span>|<span data-ttu-id="3c7af-167">파일 또는 보고서에서 기존 쿼리를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="3c7af-167">Import an existing query from a file or report.</span></span> <span data-ttu-id="3c7af-168">.sql  및 .rdl  파일 형식이 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c7af-168">File types .sql and .rdl are supported.</span></span>|  
|<span data-ttu-id="3c7af-169">**쿼리 실행**</span><span class="sxs-lookup"><span data-stu-id="3c7af-169">**Run Query**</span></span>|<span data-ttu-id="3c7af-170">쿼리를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="3c7af-170">Run the query.</span></span> <span data-ttu-id="3c7af-171">쿼리 결과 창에 결과 집합이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c7af-171">The Query results pane displays the result set.</span></span>|  
|<span data-ttu-id="3c7af-172">**숨겨진 필드 표시**</span><span class="sxs-lookup"><span data-stu-id="3c7af-172">**Show Hidden Fields**</span></span>|<span data-ttu-id="3c7af-173">SharePoint에 의해 자동으로 생성되지만 일반적으로 보고서에서 사용되지 않는 필드(예: SharePoint 연결 항목의 ProgId 및 Level)를 표시하거나 숨깁니다.</span><span class="sxs-lookup"><span data-stu-id="3c7af-173">Toggle to show or hide the fields that were automatically generated by SharePoint such as the ProgId and Level for SharePoint link items, but are typically not used in reports..</span></span> <span data-ttu-id="3c7af-174">이러한 필드를 숨기면 필드 목록이 간단해져서 사용하기가 쉽습니다.</span><span class="sxs-lookup"><span data-stu-id="3c7af-174">Hiding these fields makes the field list shorter and easier to use.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3c7af-175">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3c7af-175">See Also</span></span>  
 [<span data-ttu-id="3c7af-176">Reporting Services 쿼리 디자이너</span><span class="sxs-lookup"><span data-stu-id="3c7af-176">Reporting Services Query Designers</span></span>](../../2014/reporting-services/reporting-services-query-designers.md)  
  
  
