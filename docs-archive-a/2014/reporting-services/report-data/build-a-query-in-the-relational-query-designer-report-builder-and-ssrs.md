---
title: 관계형 쿼리 디자이너에서 쿼리 작성(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 28b25861-f3b4-4c3e-a9b0-03d6e4cfea26
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 555d72c4d3bca8677d04fdc4160639f004d6bbe9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739424"
---
# <a name="build-a-query-in-the-relational-query-designer-report-builder-and-ssrs"></a><span data-ttu-id="96b6b-102">관계형 쿼리 디자이너에서 쿼리 작성(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="96b6b-102">Build a Query in the Relational Query Designer (Report Builder and SSRS)</span></span>
  <span data-ttu-id="96b6b-103">쿼리 디자이너를 사용하면 보고서 데이터 세트에 사용하기 위해 외부 데이터 원본에서 검색할 데이터를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="96b6b-103">A query designer helps you specify which data to retrieve from an external data source for a report dataset.</span></span> <span data-ttu-id="96b6b-104">마법사에서 쿼리를 작성하거나 데이터 세트 쿼리를 만들 때 쿼리 디자이너를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="96b6b-104">You use a query designer when you build a query in a wizard or create a dataset query.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
 <span data-ttu-id="96b6b-105">데이터 세트는 데이터 원본을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="96b6b-105">A dataset is based on a data source.</span></span> <span data-ttu-id="96b6b-106">데이터 원본의 유형 및 제작 환경에 따라 데이터 세트 쿼리를 정의할 때 열리는 쿼리 디자이너가 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="96b6b-106">The type of data source and the authoring environment determines which query designer opens when you define the dataset query.</span></span> <span data-ttu-id="96b6b-107">쿼리 디자이너 기능은 기본 데이터 원본에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="96b6b-107">Query designer features vary based on the underlying data source.</span></span> <span data-ttu-id="96b6b-108">데이터 계층에 대 한 자세한 내용은 Reporting Services의 데이터 연결 [, 데이터 원본 및 연결 문자열 보고서 작성기](../data-connections-data-sources-and-connection-strings-in-report-builder.md) 또는 [데이터 연결, 데이터 원본 및 연결 문자열](../data-connections-data-sources-and-connection-strings-in-reporting-services.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="96b6b-108">For more information about data layers, see [Data Connections, Data Sources, and Connection Strings in Report Builder](../data-connections-data-sources-and-connection-strings-in-report-builder.md) or [Data Connections, Data Sources, and Connection Strings in Reporting Services](../data-connections-data-sources-and-connection-strings-in-reporting-services.md).</span></span>  
  
 <span data-ttu-id="96b6b-109">다음과 같은 태스크에 쿼리 디자이너를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="96b6b-109">You can use a query designer for the following tasks:</span></span>  
  
-   <span data-ttu-id="96b6b-110">외부 데이터 원본에서 여러 스키마에 대한 메타데이터를 탐색합니다.</span><span class="sxs-lookup"><span data-stu-id="96b6b-110">Explore the metadata for multiple schemas on the external data source</span></span>  
  
-   <span data-ttu-id="96b6b-111">데이터 세트에 대해 검색할 필드를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="96b6b-111">Specify fields to retrieve for the dataset</span></span>  
  
-   <span data-ttu-id="96b6b-112">테이블 등과 같은 두 개체 간의 관계를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="96b6b-112">Specify relationships between two objects such as tables</span></span>  
  
-   <span data-ttu-id="96b6b-113">보고서 데이터로 검색되기 전에 필터를 지정하여 데이터를 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="96b6b-113">Specify filters to restrict the data before it is retrieved as report data</span></span>  
  
-   <span data-ttu-id="96b6b-114">매개 변수를 만들지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="96b6b-114">Indicate whether to create parameters</span></span>  
  
-   <span data-ttu-id="96b6b-115">외부 데이터 원본에서 계산을 수행하기 위해 집계를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="96b6b-115">Specify aggregates to perform calculations on the external data source</span></span>  
  
 <span data-ttu-id="96b6b-116">쿼리 디자이너를 연 후에 포함된 데이터 세트 또는 공유 데이터 세트에 대해 동일한 방법으로 쿼리를 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="96b6b-116">After you open a query designer, you build a query in the same way for either an embedded dataset or a shared dataset.</span></span> <span data-ttu-id="96b6b-117">다음 절차에서는 포함된 데이터 세트 쿼리를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="96b6b-117">The following procedures use an embedded dataset query.</span></span>  
  
 <span data-ttu-id="96b6b-118">자세한 내용은 [관계형 쿼리 디자이너 사용자 인터페이스&#40;보고서 작성기&#41;](relational-query-designer-user-interface-report-builder.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="96b6b-118">For more information, see [Relational Query Designer User Interface &#40;Report Builder&#41;](relational-query-designer-user-interface-report-builder.md).</span></span>  
  
### <a name="to-build-a-query-for-an-embedded-dataset-in-report-design-view"></a><span data-ttu-id="96b6b-119">보고서 디자인 뷰에서 포함된 데이터 세트에 대한 쿼리를 작성하려면</span><span class="sxs-lookup"><span data-stu-id="96b6b-119">To build a query for an embedded dataset in Report Design View</span></span>  
  
1.  <span data-ttu-id="96b6b-120">쿼리 디자이너를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="96b6b-120">Open the query designer.</span></span> <span data-ttu-id="96b6b-121">보고서 데이터 창에서 데이터 세트를 마우스 오른쪽 단추로 클릭한 다음, **쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="96b6b-121">In the Report Data pane, right-click the dataset, and then click **Query**.</span></span>  
  
     <span data-ttu-id="96b6b-122">데이터 원본과 연결된 쿼리 디자이너가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="96b6b-122">The query designer that is associated with the data source opens.</span></span>  
  
2.  <span data-ttu-id="96b6b-123">데이터베이스 뷰 창에서 테이블, 뷰, 저장 프로시저 등과 같은 데이터베이스 스키마 개체의 계층 구조를 표시하는 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="96b6b-123">In the Database view pane, expand the folders that display a hierarchical view of database schema objects such as tables, views, and stored procedures.</span></span> <span data-ttu-id="96b6b-124">선택 상자를 클릭하여 개체의 모든 필드를 선택하거나 노드를 확장하여 개별 필드를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="96b6b-124">Click the select box to select all fields for an object or expand the node to select individual fields.</span></span>  
  
     <span data-ttu-id="96b6b-125">데이터베이스 뷰 창에서 필드를 선택하면 **필드 선택** 창에 선택 항목이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="96b6b-125">As you select fields from the Database view pane, the **Select fields** pane displays your selections.</span></span>  
  
     <span data-ttu-id="96b6b-126">둘 이상의 관련 데이터베이스 테이블에서 필드를 선택한 경우 관계 창을 사용하여 데이터베이스 스키마에서 검색된 테이블 관계를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="96b6b-126">If you select fields from more than one related database table, use the Relationships pane to view the table relationships that were detected from the database schema.</span></span>  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
     <span data-ttu-id="96b6b-127">데이터 세트 필드 목록이 보고서 데이터 창에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="96b6b-127">The list of dataset fields appears in the Report Data pane.</span></span>  
  
### <a name="to-specify-limits-for-a-query"></a><span data-ttu-id="96b6b-128">쿼리에 대한 제한을 지정하려면</span><span class="sxs-lookup"><span data-stu-id="96b6b-128">To specify limits for a query</span></span>  
  
1.  <span data-ttu-id="96b6b-129">관계형 쿼리 디자이너에서 필드가 선택되었으며 **선택한 필드** 창에 해당 필드가 표시되는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="96b6b-129">In the relational query designer, verify that you have fields selected and that the fields appear in the **Selected fields** pane.</span></span>  
  
2.  <span data-ttu-id="96b6b-130">적용된 필터 창 도구 모음에서 **필터 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="96b6b-130">In the Applied filters pane toolbar, click **Add Filter**.</span></span> <span data-ttu-id="96b6b-131">새 필터 행이 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="96b6b-131">A new filter row appears.</span></span>  
  
3.  <span data-ttu-id="96b6b-132">**필드 이름**에서 클릭하여 필드의 드롭다운 목록을 표시한 다음 필터링 기준으로 사용할 필드 이름을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="96b6b-132">In **Field name**, click to display the drop-down list of fields, and then click the name of the field that you want to filter by.</span></span> <span data-ttu-id="96b6b-133">예를 들어 수량으로 필터링하려면 항목 수를 포함하는 필드를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="96b6b-133">For example, to filter by quantity, click the field that contains the number of items.</span></span>  
  
4.  <span data-ttu-id="96b6b-134">**연산자**에서 클릭하여 연산자의 드롭다운 목록을 표시한 다음 필터에서 사용할 비교 연산자를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="96b6b-134">In **Operator**, click to display the drop-down list of operators, and then select the comparison operator to use in the filter.</span></span>  
  
5.  <span data-ttu-id="96b6b-135">**값**에서 필터링 기준으로 사용할 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="96b6b-135">In **Value**, type the value that you want to filter by.</span></span> <span data-ttu-id="96b6b-136">예를 들어 100보다 큰 수량을 필터링하려면 100을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="96b6b-136">For example, to filter on quantity greater than 100, type 100.</span></span>  
  
6.  <span data-ttu-id="96b6b-137">이 행에서 매개 변수 옵션을 선택하여 사용자가 필터 값을 지정할 수 있게 하는 데이터 세트 매개 변수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="96b6b-137">Select the parameter option in this row to create a dataset parameter to enable a user to specify a filter value.</span></span> <span data-ttu-id="96b6b-138">데이터 세트 매개 변수와 일치하는 보고서 매개 변수가 자동으로 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="96b6b-138">A report parameter that matches the dataset parameter is automatically created.</span></span>  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
8.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
 <span data-ttu-id="96b6b-139">데이터 세트 필드 목록이 보고서 데이터 창에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="96b6b-139">The list of dataset fields appears in the Report Data pane.</span></span>  
  
### <a name="to-view-a-query-result-set"></a><span data-ttu-id="96b6b-140">쿼리 결과 집합을 보려면</span><span class="sxs-lookup"><span data-stu-id="96b6b-140">To view a query result set</span></span>  
  
1.  <span data-ttu-id="96b6b-141">쿼리 디자이너 도구 모음에서 **쿼리 실행(!)** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="96b6b-141">On the query designer toolbar, click **Run Query (!)**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="96b6b-142">쿼리 디자이너는 디자인 타임 자격 증명을 사용하여 쿼리를 실행하고 결과 집합을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="96b6b-142">The query designer uses design time credentials to run the query and retrieve the result set.</span></span> <span data-ttu-id="96b6b-143">자세한 내용은 [보고서 작성기에 자격 증명 지정](../specify-credentials-in-report-builder.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="96b6b-143">For more information, see [Specify Credentials in Report Builder](../specify-credentials-in-report-builder.md).</span></span>  
  
 <span data-ttu-id="96b6b-144">쿼리는 데이터 원본에서 실행되고 쿼리 결과 창에 예제 데이터를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="96b6b-144">The query runs on the data source and returns example data in the Query results pane.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96b6b-145">참고 항목</span><span class="sxs-lookup"><span data-stu-id="96b6b-145">See Also</span></span>  
 <span data-ttu-id="96b6b-146">[보고서 &#40;보고서 작성기 및 SSRS&#41;에 데이터를 추가 합니다.](report-datasets-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="96b6b-146">[Add Data to a Report &#40;Report Builder and SSRS&#41;](report-datasets-ssrs.md) </span></span>  
 <span data-ttu-id="96b6b-147">[외부 데이터 원본의 데이터 추가&#40;SSRS&#41;](add-data-from-external-data-sources-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="96b6b-147">[Add Data from External Data Sources &#40;SSRS&#41;](add-data-from-external-data-sources-ssrs.md) </span></span>  
 <span data-ttu-id="96b6b-148">[쿼리 디자이너 &#40;보고서 작성기&#41;](../query-designers-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="96b6b-148">[Query Designers &#40;Report Builder&#41;](../query-designers-report-builder.md) </span></span>  
 <span data-ttu-id="96b6b-149">[공유 데이터 세트 또는 포함된 데이터 세트 만들기&#40;보고서 작성기 및 SSRS&#41;](create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="96b6b-149">[Create a Shared Dataset or Embedded Dataset &#40;Report Builder and SSRS&#41;](create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="96b6b-150">[보고서 디자인 뷰&#40;보고서 작성기&#41;](../report-builder/report-design-view-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="96b6b-150">[Report Design View &#40;Report Builder&#41;](../report-builder/report-design-view-report-builder.md) </span></span>  
 <span data-ttu-id="96b6b-151">[공유 데이터 세트 디자인 뷰&#40;보고서 작성기&#41;](../report-builder/shared-dataset-design-view-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="96b6b-151">[Shared Dataset Design View &#40;Report Builder&#41;](../report-builder/shared-dataset-design-view-report-builder.md) </span></span>  
 [<span data-ttu-id="96b6b-152">Reporting Services 쿼리 디자이너</span><span class="sxs-lookup"><span data-stu-id="96b6b-152">Reporting Services Query Designers</span></span>](../reporting-services-query-designers.md)  
  
  
