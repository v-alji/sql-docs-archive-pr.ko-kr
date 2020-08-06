---
title: 테이블, 행렬 및 목록(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.tablix.visibility.f1
- sql12.rtp.rptdesigner.groupproperties.advanced.f1
- "10045"
- sql12.rtp.rptdesigner.groupproperties.filters.f1
- "10039"
- "10104"
- sql12.rtp.rptdesigner.tablixgroup.f1
- sql12.rtp.rptdesigner.tablix.general.f1
- "10047"
- "10044"
- "10046"
- sql12.rtp.rptdesigner.groupproperties.visibility.f1
- "10101"
- sql12.rtp.rptdesigner.groupproperties.sort.f1
- sql12.rtp.rptdesigner.groupproperties.variables.f1
- sql12.rtp.rptdesigner.groupproperties.general.f1
- "10042"
- sql12.rtp.rptdesigner.tablix.sort.f1
- "10041"
- sql12.rtp.rptdesigner.groupproperties.pagebreaks.f1
- "10102"
- "10103"
- "10043"
- sql12.rtp.rptdesigner.tablix.filter.f1
ms.assetid: 9dcf3fc8-bf9c-4a14-a03d-e78254aa4098
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 03384009b0e51c081f0906ef0a768dafa180be7e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650671"
---
# <a name="tables-matrices-and-lists-report-builder-and-ssrs"></a><span data-ttu-id="839d4-102">테이블, 행렬 및 목록(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="839d4-102">Tables, Matrices, and Lists (Report Builder and SSRS)</span></span>
  <span data-ttu-id="839d4-103">테이블, 행렬 및 목록은 행과 열로 구성되는 셀에 보고서 데이터를 표시하는 데이터 영역입니다.</span><span class="sxs-lookup"><span data-stu-id="839d4-103">Tables, matrices, and lists are data regions that display report data in cells that are organized into rows and columns.</span></span> <span data-ttu-id="839d4-104">셀에는 보통 텍스트, 날짜, 숫자 등의 텍스트 데이터가 포함되지만 계기, 차트, 또는 보고서 항목(예: 이미지)도 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="839d4-104">The cells typically contain text data such as text, dates, and numbers but they can also contain gauges, charts, or report items such as images.</span></span> <span data-ttu-id="839d4-105">테이블, 행렬 및 목록을 집합적으로 테이블릭스 데이터 영역이라고 하는 경우가 많습니다.</span><span class="sxs-lookup"><span data-stu-id="839d4-105">Collectively, tables, matrices, and lists are frequently referred to as tablix data regions.</span></span>  
  
 <span data-ttu-id="839d4-106">테이블, 행렬 및 목록 템플릿은 셀에 데이터를 표시할 수 있는 유동적 눈금인 테이블릭스 데이터 영역에 작성됩니다.</span><span class="sxs-lookup"><span data-stu-id="839d4-106">The table, matrix, and list templates are built on the tablix data region, which is a flexible grid that can display data in cells.</span></span> <span data-ttu-id="839d4-107">테이블 및 행렬 템플릿에서 셀은 행과 열로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="839d4-107">In the table and matrix templates, cells are organized into rows and columns.</span></span> <span data-ttu-id="839d4-108">템플릿은 일반적인 기본 테이블릭스 데이터 영역의 변형이므로 템플릿 형식의 조합으로 데이터를 표시할 수 있으며, 보고서를 개발할 때 다른 데이터 영역의 기능을 포함하도록 테이블, 행렬 또는 목록을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="839d4-108">Because templates are variations of the underlying generic tablix data region, you can display can display data in combination of template formats and change the table, matrix, or list on to include the features of another data region as you develop your report.</span></span> <span data-ttu-id="839d4-109">예를 들어 테이블을 추가했는데 용도에 맞지 않으면 열 그룹을 추가해 테이블을 행렬로 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="839d4-109">For example, if you add a table and find it does not serve your needs, you can add column groups to make the table a matrix.</span></span>  
  
 <span data-ttu-id="839d4-110">테이블 및 행렬 데이터 영역에 중첩된 테이블, 행렬, 목록, 차트 및 계기를 포함해 복잡한 데이터 관계를 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="839d4-110">The table and matrix data regions can display complex data relationships by including nested tables, matrices, lists, charts and gauges.</span></span> <span data-ttu-id="839d4-111">테이블 및 행렬에는 테이블 형식 레이아웃이 있으며 해당 데이터는 단일 데이터 원본에 작성된 단일 데이터 세트에서 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="839d4-111">Tables and matrices have a tabular layout and their data comes from a single dataset, built on a single data source.</span></span> <span data-ttu-id="839d4-112">테이블과 행렬의 가장 큰 차이점은 테이블의 경우 행 그룹만 포함할 수 있지만 행렬은 행 그룹과 열 그룹을 모두 포함할 수 있다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="839d4-112">The key difference between tables and matrices is that tables can include only row groups, where as matrices have row groups and column groups.</span></span>  
  
 <span data-ttu-id="839d4-113">목록은 이 두 항목과 약간 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="839d4-113">Lists are a little different.</span></span> <span data-ttu-id="839d4-114">즉, 목록은 자유 레이아웃을 지원하며 각각 다른 데이터 세트의 데이터를 사용하는 피어 테이블 또는 행렬을 여러 개 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="839d4-114">They support a free-layout that and can include multiple peer tables or matrices, each using data from a different dataset.</span></span> <span data-ttu-id="839d4-115">또한 목록은 송장 등의 양식에도 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="839d4-115">Lists can also be used for forms, such as invoices.</span></span>  
  
 <span data-ttu-id="839d4-116">다음 그림에서는 테이블, 행렬 또는 목록이 포함된 간단한 보고서를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="839d4-116">The following pictures show simple reports with a table, matrix, or list.</span></span>  
  
 <span data-ttu-id="839d4-117">![RS_TableMatrixList](../media/rs-tablematrixlist.gif "RS_TableMatrixList")</span><span class="sxs-lookup"><span data-stu-id="839d4-117">![RS_TableMatrixList](../media/rs-tablematrixlist.gif "RS_TableMatrixList")</span></span>  
  
 <span data-ttu-id="839d4-118">테이블, 행렬 및 목록으로 빠르게 시작하려면 [자습서: 기본 테이블 보고서 만들기&#40;보고서 작성기&#41;](../tutorial-creating-a-basic-table-report-report-builder.md), [자습서: 행렬 보고서 만들기&#40;보고서 작성기&#41;](../tutorial-creating-a-matrix-report-report-builder.md) 및 [자습서: 자유 형식 보고서 만들기&#40;보고서 작성기&#41;](../tutorial-creating-a-free-form-report-report-builder.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="839d4-118">To quickly get started with tables, matrices, and lists, see [Tutorial: Creating a Basic Table Report &#40;Report Builder&#41;](../tutorial-creating-a-basic-table-report-report-builder.md), [Tutorial: Creating a Matrix Report &#40;Report Builder&#41;](../tutorial-creating-a-matrix-report-report-builder.md), and [Tutorial: Creating a Free Form Report &#40;Report Builder&#41;](../tutorial-creating-a-free-form-report-report-builder.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="839d4-119">테이블, 행렬 및 목록을 보고서와는 별도로 보고서 파트로 게시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="839d4-119">You can publish tables, matrices, and lists separately from a report as report parts.</span></span> [!INCLUDE[ssRBrptparts](../../includes/ssrbrptparts-md.md)]  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
##  <a name="table"></a><a name="Table"></a><span data-ttu-id="839d4-120">테이블</span><span class="sxs-lookup"><span data-stu-id="839d4-120">Table</span></span>  
 <span data-ttu-id="839d4-121">세부 데이터를 표시하거나, 데이터를 행 그룹으로 구성하거나, 두 가지 모두를 수행할 때 테이블을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="839d4-121">Use a table to display detail data, organize the data in row groups, or both.</span></span> <span data-ttu-id="839d4-122">테이블 템플릿에는 테이블 머리글 행 및 데이터를 위한 정보 행이 있는 세 열이 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="839d4-122">The Table template contains three columns with a table header row and a details row for data.</span></span> <span data-ttu-id="839d4-123">다음 그림에서는 디자인 화면에서 선택한 초기 테이블 템플릿을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="839d4-123">The following figure shows the initial table template, selected on the design surface:</span></span>  
  
 <span data-ttu-id="839d4-124">![디자인 화면에서 테이블 템플릿이 선택됨](../media/rs-tabletemplatenewselected.gif "디자인 화면에서 테이블 템플릿이 선택됨")</span><span class="sxs-lookup"><span data-stu-id="839d4-124">![Table template on design surface, selected](../media/rs-tabletemplatenewselected.gif "Table template on design surface, selected")</span></span>  
  
 <span data-ttu-id="839d4-125">단일 필드, 여러 필드를 기준으로 하거나 사용자 고유의 식을 작성하여 데이터를 그룹화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="839d4-125">You can group data by a single field, by multiple fields, or by writing your own expression.</span></span> <span data-ttu-id="839d4-126">중첩된 그룹이나 인접한 독립 그룹을 만들고 그룹화된 데이터의 집계된 값을 표시하거나 합계를 그룹에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="839d4-126">You can create nested groups or independent, adjacent groups and display aggregated values for grouped data, or add totals to groups.</span></span> <span data-ttu-id="839d4-127">예를 들어 테이블에 [Category]라는 행 그룹이 있는 경우 각 그룹의 부분합과 보고서의 총합을 모두 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="839d4-127">For example, if your table has a row group called [Category], you can add a subtotal for each group as well as a grand total for the report.</span></span> <span data-ttu-id="839d4-128">테이블의 모양을 개선하고 뚜렷하게 표시할 데이터를 강조하려면 셀을 병합하고 데이터 및 테이블 제목에 서식을 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="839d4-128">To improve the appearance of the table and highlight data you want to emphasize, you can merge cells and apply formatting to data and table headings.</span></span>  
  
 <span data-ttu-id="839d4-129">처음에 정보 데이터나 그룹화된 데이터를 숨길 수 있으며 드릴다운 토글을 포함하여 사용자가 표시할 데이터의 양을 대화형으로 선택하도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="839d4-129">You can initially hide detail or grouped data, and include drilldown toggles to enable a user to interactively choose how much data to show.</span></span>  
  
 <span data-ttu-id="839d4-130">자세한 내용은 [테이블&#40;보고서 작성기 및 SSRS&#41;](tables-report-builder-and-ssrs.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="839d4-130">For more information, see [Tables &#40;Report Builder  and SSRS&#41;](tables-report-builder-and-ssrs.md).</span></span>  
  

  
##  <a name="matrix"></a><a name="Matrix"></a><span data-ttu-id="839d4-131">행렬</span><span class="sxs-lookup"><span data-stu-id="839d4-131">Matrix</span></span>  
 <span data-ttu-id="839d4-132">피벗 테이블 또는 크로스탭처럼 집계된 데이터 요약을 행 및 열로 그룹화하여 표시할 때 행렬을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="839d4-132">Use a matrix to display aggregated data summaries, grouped in rows and columns, similar to a PivotTable or crosstab.</span></span> <span data-ttu-id="839d4-133">그룹의 행과 열 수는 각 행 및 열 그룹의 고유 값 수에 따라 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="839d4-133">The number of rows and columns for groups is determined by the number of unique values for each row and column groups.</span></span> <span data-ttu-id="839d4-134">다음 그림에서는 디자인 화면에서 선택한 초기 행렬 템플릿을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="839d4-134">The following figure shows the initial matrix template, selected on the design surface:</span></span>  
  
 <span data-ttu-id="839d4-135">![도구 상자에서 추가된 새 행렬이 선택됨](../media/rs-matrixtemplatenewselected.gif "도구 상자에서 추가된 새 행렬이 선택됨")</span><span class="sxs-lookup"><span data-stu-id="839d4-135">![New Matrix added from Toolbox, selected](../media/rs-matrixtemplatenewselected.gif "New Matrix added from Toolbox, selected")</span></span>  
  
 <span data-ttu-id="839d4-136">행 및 열 그룹의 여러 필드나 식으로 데이터를 그룹화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="839d4-136">You can group data by multiple fields or expressions in row and column groups.</span></span> <span data-ttu-id="839d4-137">런타임에 보고서 데이터 및 데이터 영역이 결합되면 열 그룹에는 열이, 행 그룹에는 행이 추가되면 페이지에서 행렬이 가로와 세로 방향으로 확장됩니다.</span><span class="sxs-lookup"><span data-stu-id="839d4-137">At run time, when the report data and data regions are combined, a matrix grows horizontally and vertically on the page as columns for column groups and rows for row groups are added.</span></span> <span data-ttu-id="839d4-138">행렬 셀에는 셀이 속한 행 및 열 그룹의 교차점으로 한정된 집계 값이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="839d4-138">The matrix cells display aggregate values that are scoped to the intersection of the row and column groups to which the cell belongs.</span></span> <span data-ttu-id="839d4-139">예를 들어 행렬에 판매량 합계를 표시하는 행 그룹 하나(Category)와 열 그룹 두 개(Territory, Year)가 있는 경우 보고서에서는 두 개의 셀에 Category 그룹의 각 값에 대한 판매량 합계가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="839d4-139">For example, if your matrix has a row group (Category) and two column groups (Territory and Year) that display the sum of sales, the report displays two cells with sums of sales for each value in the Category group.</span></span> <span data-ttu-id="839d4-140">셀의 범위가 되는 두 교차점은 범주와 지역 및 범주와 연도입니다.</span><span class="sxs-lookup"><span data-stu-id="839d4-140">The scope of the cells are the two intersections are: Category and Territory and Category and Year.</span></span> <span data-ttu-id="839d4-141">이 행렬에는 중첩된 그룹과 인접 그룹이 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="839d4-141">The matrix can include nested and adjacent groups.</span></span> <span data-ttu-id="839d4-142">중첩된 그룹에는 부모-자식 관계가 있으며 인접 그룹에는 피어 관계가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="839d4-142">Nested groups have a parent-child relationship and adjacent groups a peer relationship.</span></span> <span data-ttu-id="839d4-143">행렬 내에 있는 중첩된 행 및 열 그룹의 일부 및 모든 수준에 대해 부분합을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="839d4-143">You can add subtotals for any and all levels of nested row and column groups within the matrix.</span></span>  
  
 <span data-ttu-id="839d4-144">행렬 데이터를 보다 읽기 쉽게 만들고 뚜렷하게 표시할 데이터를 강조하려면 셀을 가로 또는 세로로 병합하거나 분할하고 데이터 및 그룹 제목에 서식을 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="839d4-144">To make the matrix data more readable and highlight the data you want to emphasize, you can merge cells or split horizontally and vertically and apply formatting to data and group headings.</span></span>  
  
 <span data-ttu-id="839d4-145">또한 처음에 정보 데이터를 숨기는 드릴다운 토글을 포함할 수도 있습니다. 사용자는 필요한 경우 이 토글을 클릭하여 내용을 자세히 또는 간략히 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="839d4-145">You can also include drilldown toggles that initially hide detail data; the user can then click the toggles to display more or less detail as needed.</span></span>  
  
 <span data-ttu-id="839d4-146">자세한 내용은 [행렬 &#40;보고서 작성기 및 SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="839d4-146">For more information, see [Matrices &#40;Report Builder and SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md).</span></span>  
  

  
##  <a name="list"></a><a name="List"></a><span data-ttu-id="839d4-147">은</span><span class="sxs-lookup"><span data-stu-id="839d4-147">List</span></span>  
 <span data-ttu-id="839d4-148">자유 형식 레이아웃을 만들 때 목록을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="839d4-148">Use a list to create a free-form layout.</span></span> <span data-ttu-id="839d4-149">이를 사용하면 모눈 레이아웃에 제한되지 않고 목록 안에서 필드를 자유롭게 배치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="839d4-149">You are not limited to a grid layout, but can place fields freely inside the list.</span></span> <span data-ttu-id="839d4-150">목록을 사용하여 여러 데이터 세트 필드를 표시하는 폼을 디자인할 수 있으며, 그룹화된 데이터를 위해 여러 데이터 영역을 나란히 표시하기 위한 컨테이너로 목록을 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="839d4-150">You can use a list to design a form for displaying many dataset fields or as a container to display multiple data regions side by side for grouped data.</span></span> <span data-ttu-id="839d4-151">예를 들어 직원 레코드나 환자 레코드에서 목록에 대한 그룹을 정의하고, 테이블, 차트 및 이미지를 추가하고, 각 그룹 값에 대해 테이블 및 그래픽 형식으로 값을 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="839d4-151">For example, you can define a group for a list; add a table, chart, and image; and display values in table and graphic form for each group value, as you might for an employee or patient record.</span></span>  
  
 <span data-ttu-id="839d4-152">![도구 상자에서 추가된 새 목록이 선택됨](../media/rs-listtemplatenewselected.gif "도구 상자에서 추가된 새 목록이 선택됨")</span><span class="sxs-lookup"><span data-stu-id="839d4-152">![New List added from Toolbox, selected](../media/rs-listtemplatenewselected.gif "New List added from Toolbox, selected")</span></span>  
  
 <span data-ttu-id="839d4-153">자세한 내용은 [목록 &#40;보고서 작성기 및 SSRS&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="839d4-153">For more information, see [Lists &#40;Report Builder and SSRS&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md).</span></span>  
  

  
##  <a name="preparing-data"></a><a name="PreparingData"></a><span data-ttu-id="839d4-154">데이터 준비</span><span class="sxs-lookup"><span data-stu-id="839d4-154">Preparing Data</span></span>  
 <span data-ttu-id="839d4-155">테이블, 행렬 및 목록 데이터 영역에는 데이터 세트의 데이터가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="839d4-155">A table, matrix, and list data regions display data from a dataset.</span></span> <span data-ttu-id="839d4-156">데이터 세트의 데이터를 검색하는 쿼리를 사용하거나 테이블, 행렬 또는 목록의 속성을 설정하여 데이터를 준비할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="839d4-156">You can prepare the data in the query that retrieves the data for the dataset or by setting properties in the table, matrix, or list.</span></span>  
  
 <span data-ttu-id="839d4-157">보고서 데이터 세트의 데이터를 검색하는 데 사용하는 [!INCLUDE[tsql](../../includes/tsql-md.md)] 등의 쿼리 언어는 데이터 하위 세트만 포함하도록 필터를 적용하고, 보고서를 좀 더 쉽게 읽을 수 있도록 null 값이나 공백을 상수로 바꾸고, 데이터를 정렬 및 그룹화하여 데이터를 준비할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="839d4-157">The query languages such as [!INCLUDE[tsql](../../includes/tsql-md.md)], that you use to retrieve the data for the report datasets can prepare the data by applying filters to include only a subset of the data, replacing null values or blanks with constants that make the report more readable, and sorting and grouping data.</span></span>  
  
 <span data-ttu-id="839d4-158">보고서의 테이블, 행렬 또는 목록 데이터 영역에서 데이터를 준비하려는 경우에는 데이터 영역 또는 데이터 영역 내의 셀에 대해 속성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="839d4-158">If you choose to prepare the data in the table, matrix, or list data region of a report, you set properties on the data region or cells within the data region.</span></span> <span data-ttu-id="839d4-159">데이터를 필터링하거나 정렬하려는 경우에는 데이터 영역에 대해 속성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="839d4-159">If you want to filter or sort the data, set the properties on the data region.</span></span> <span data-ttu-id="839d4-160">예를 들어 데이터를 정렬하려면 정렬할 열과 정렬 방향을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="839d4-160">For example, to sort the data you specify the columns to sort on and the sort direction.</span></span> <span data-ttu-id="839d4-161">필드에 다른 값을 제공하려는 경우에는 필드를 표시하는 셀 텍스트의 값을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="839d4-161">If you want to provide an alternative value for a field, you set the values of the cell text that displays the field.</span></span> <span data-ttu-id="839d4-162">예를 들어 필드가 비어 있거나 null인 경우 Blank를 표시하려면 식을 사용해 해당 값을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="839d4-162">For example, to display Blank when a field is empty or null, you use an expression to set the value.</span></span>  
  
 <span data-ttu-id="839d4-163">자세한 내용은 [테이블릭스 데이터 영역에 표시하기 위한 데이터 준비&#40;보고서 작성기 및 SSRS&#41;](preparing-data-for-display-in-a-tablix-data-region-report-builder-and-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="839d4-163">For more information, see [Preparing Data for Display in a Tablix Data Region &#40;Report Builder and SSRS&#41;](preparing-data-for-display-in-a-tablix-data-region-report-builder-and-ssrs.md).</span></span>  
  

  
##  <a name="building-and-configuring-a-table-matrix-or-list"></a><a name="BuildingConfiguringTableMatrixList"></a><span data-ttu-id="839d4-164">테이블, 행렬 또는 목록 작성 및 구성</span><span class="sxs-lookup"><span data-stu-id="839d4-164">Building and Configuring a Table, Matrix, or List</span></span>  
 <span data-ttu-id="839d4-165">보고서에 테이블 또는 행렬을 추가할 때는 테이블 및 행렬 마법사를 사용하거나 보고서 작성기 및 보고서 디자이너가 제공하는 템플릿에서 수동으로 테이블 또는 행렬을 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="839d4-165">When you add tables or matrices to your report, you can use the Table and Matrix Wizard or build them manually from the templates that Report Builder and Report Designer provide.</span></span> <span data-ttu-id="839d4-166">목록은 목록 템플릿에서 수동으로 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="839d4-166">Lists are built manually from the list template.</span></span>  
  
 <span data-ttu-id="839d4-167">마법사는 테이블 또는 행렬을 빠르게 작성 및 구성하는 과정을 단계별로 안내합니다.</span><span class="sxs-lookup"><span data-stu-id="839d4-167">The wizard guides you through the steps to quickly build and configure a table or matrix.</span></span> <span data-ttu-id="839d4-168">마법사를 완료한 후 또는 테이블릭스 데이터 영역을 처음부터 작성하는 경우에는 테이블 또는 행렬을 보다 자세하게 구성하고 상세하게 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="839d4-168">After you complete the wizard or if you build the tablix data regions from scratch, you can further configure and refine them.</span></span> <span data-ttu-id="839d4-169">데이터 영역에서 마우스 오른쪽 단추를 클릭하면 표시되는 대화 상자를 사용하면 페이지 나누기, 머리글/바닥글 반복 및 표시 여부, 표시 옵션, 필터 및 정렬에 가장 일반적으로 사용되는 속성을 쉽게 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="839d4-169">The dialog boxes, available from the right-click menus on the data regions, make it easy to set the most commonly used properties for page breaks, repeatability and visibility of headers and footers, display options, filters, and sorting.</span></span> <span data-ttu-id="839d4-170">그러나 테이블릭스 데이터 영역에서는 보다 많은 속성이 추가로 제공되는데, 이들 속성은 보고서 작성기의 속성 창에서만 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="839d4-170">But the tablix data region provides a wealth of additional properties, which you can set only in the Properties pane of Report Builder.</span></span> <span data-ttu-id="839d4-171">예를 들어 테이블, 행렬 또는 목록의 데이터 세트가 비어 있을 때 메시지를 표시하려면 속성 창의 NoRowsMessage 테이블릭스 속성에서 메시지 텍스트를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="839d4-171">For example, if you want to display a message when the dataset for a table, matrix, or list is empty, you specify the message text in the NoRowsMessage tablix property in the Properties pane.</span></span>  
  

  
##  <a name="changing-between-tablix-templates"></a><a name="ChangingBetweenTablixTemplates"></a><span data-ttu-id="839d4-172">테이블 릭 스 템플릿 간 변경</span><span class="sxs-lookup"><span data-stu-id="839d4-172">Changing Between Tablix Templates</span></span>  
 <span data-ttu-id="839d4-173">초기 테이블릭스 템플릿만 선택할 수 있는 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="839d4-173">You are not limited by your initial tablix template choice.</span></span> <span data-ttu-id="839d4-174">그룹, 합계 및 레이블을 추가하다 보면 테이블릭스 디자인의 수정이 필요할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="839d4-174">As you add groups, totals, and labels, you might want to modify your tablix design.</span></span> <span data-ttu-id="839d4-175">예를 들어 테이블로 시작했지만 나중에 정보 행을 삭제하고 열 그룹을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="839d4-175">For example, you might start with a table and then delete the details row and add column groups.</span></span> <span data-ttu-id="839d4-176">자세한 내용은 [테이블릭스 데이터 영역의 유연성 살펴보기&#40;보고서 작성기 및 SSRS&#41;](exploring-the-flexibility-of-a-tablix-data-region-report-builder-and-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="839d4-176">For more information, see [Exploring the Flexibility of a Tablix Data Region &#40;Report Builder and SSRS&#41;](exploring-the-flexibility-of-a-tablix-data-region-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="839d4-177">원하는 테이블릭스 기능을 추가하여 테이블, 행렬 또는 목록을 계속 개발할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="839d4-177">You can continue to develop a table, matrix, or list by adding any tablix feature.</span></span> <span data-ttu-id="839d4-178">테이블릭스 기능에는 세부 데이터를 표시하는 기능이나 그룹화된 데이터의 집계를 행과 열에 표시하는 기능이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="839d4-178">Tablix features include displaying detail data or aggregates for grouped data on rows and columns.</span></span> <span data-ttu-id="839d4-179">중첩된 그룹, 독립적인 인접 그룹 또는 재귀적 그룹을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="839d4-179">You can create nested groups, independent adjacent groups, or recursive groups.</span></span> <span data-ttu-id="839d4-180">그룹화된 데이터를 필터링하고 정렬할 수 있으며 그룹 정의에 여러 개의 그룹 식을 포함하여 그룹을 쉽게 결합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="839d4-180">You can filter and sort grouped data, and easily combine groups by including multiple group expressions in a group definition</span></span>  
  
 <span data-ttu-id="839d4-181">또한 그룹 합계나 데이터 영역의 총합계도 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="839d4-181">You can also add totals for a group or grand totals for the data region.</span></span> <span data-ttu-id="839d4-182">드릴다운 보고서처럼 사용자가 숨겨진 데이터의 표시를 전환할 수 있도록 하고 보고서를 단순화하기 위해 행이나 열을 숨길 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="839d4-182">You can hide rows or columns to simplify a report and enable the user to toggle the display of the hidden data, as in a drilldown report.</span></span> <span data-ttu-id="839d4-183">자세한 내용은 [보고서 페이지에서 테이블릭스 데이터 영역 표시 제어&#40;보고서 작성기 및 SSRS&#41;](controlling-the-tablix-data-region-display-on-a-report-page.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="839d4-183">For more information, see [Controlling the Tablix Data Region Display on a Report Page &#40;Report Builder and SSRS&#41;](controlling-the-tablix-data-region-display-on-a-report-page.md).</span></span>  
  

  
##  <a name="how-to-topics"></a><a name="HowTo"></a><span data-ttu-id="839d4-184">방법 도움말 항목</span><span class="sxs-lookup"><span data-stu-id="839d4-184">How-To Topics</span></span>  
 <span data-ttu-id="839d4-185">이 섹션에는 보고서에서 테이블, 행렬 및 목록을 사용하는 방법, 행 및 열에 데이터를 표시하는 방법, 열을 추가/삭제하고 셀을 병합하고 행 및 열 그룹의 부분합을 포함하는 방법을 단계별로 보여 주는 절차가 나열되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="839d4-185">This section lists procedures that show you, step by step, how to work with work with tables, matrices and lists in your reports; how to display data in rows and columns, add and delete columns, merge cells, and include subtotals for row and column groups.</span></span>  
  
-   [<span data-ttu-id="839d4-186">세부 정보 그룹 추가&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="839d4-186">Add a Details Group &#40;Report Builder and SSRS&#41;</span></span>](add-a-details-group-report-builder-and-ssrs.md)  
  
-   [<span data-ttu-id="839d4-187">그룹 또는 테이블릭스 데이터 영역에 합계 추가&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="839d4-187">Add a Total to a Group or Tablix Data Region &#40;Report Builder and SSRS&#41;</span></span>](add-a-total-to-a-group-or-tablix-data-region-report-builder-and-ssrs.md)  
  
-   [<span data-ttu-id="839d4-188">셀 내 항목 변경&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="839d4-188">Change an Item Within a Cell &#40;Report Builder and SSRS&#41;</span></span>](change-an-item-within-a-cell-report-builder-and-ssrs.md)  
  
-   [<span data-ttu-id="839d4-189">행 높이 또는 열 너비 변경&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="839d4-189">Change Row Height or Column Width &#40;Report Builder and SSRS&#41;</span></span>](change-row-height-or-column-width-report-builder-and-ssrs.md)  
  
-   [<span data-ttu-id="839d4-190">열 삽입 또는 삭제&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="839d4-190">Insert or Delete a Column &#40;Report Builder and SSRS&#41;</span></span>](insert-or-delete-a-column-report-builder-and-ssrs.md)  
  
-   [<span data-ttu-id="839d4-191">행 삽입 또는 삭제&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="839d4-191">Insert or Delete a Row &#40;Report Builder and SSRS&#41;</span></span>](insert-or-delete-a-row-report-builder-and-ssrs.md)  
  
-   [<span data-ttu-id="839d4-192">데이터 영역의 셀 병합&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="839d4-192">Merge Cells in a Data Region &#40;Report Builder and SSRS&#41;</span></span>](merge-cells-in-a-data-region-report-builder-and-ssrs.md)  
  
-   [<span data-ttu-id="839d4-193">재귀 계층 구조 그룹 만들기&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="839d4-193">Create a Recursive Hierarchy Group &#40;Report Builder and SSRS&#41;</span></span>](create-a-recursive-hierarchy-group-report-builder-and-ssrs.md)  
  
-   [<span data-ttu-id="839d4-194">데이터 영역에서 그룹 추가 또는 삭제&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="839d4-194">Add or Delete a Group in a Data Region &#40;Report Builder and SSRS&#41;</span></span>](add-or-delete-a-group-in-a-data-region-report-builder-and-ssrs.md)  
  
-   [<span data-ttu-id="839d4-195">그룹과 함께 머리글 및 바닥글 표시&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="839d4-195">Display Headers and Footers with a Group &#40;Report Builder and SSRS&#41;</span></span>](display-headers-and-footers-with-a-group-report-builder-and-ssrs.md)  
  
-   [<span data-ttu-id="839d4-196">단계별 보고서 만들기&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="839d4-196">Create a Stepped Report &#40;Report Builder and SSRS&#41;</span></span>](create-a-stepped-report-report-builder-and-ssrs.md)  
  
-   [<span data-ttu-id="839d4-197">테이블, 행렬 또는 목록 추가, 이동 또는 삭제&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="839d4-197">Add, Move, or Delete a Table, Matrix, or List &#40;Report Builder and SSRS&#41;</span></span>](add-move-or-delete-a-table-matrix-or-list-report-builder-and-ssrs.md)  
  

  
##  <a name="in-this-section"></a><a name="InThisSection"></a> <span data-ttu-id="839d4-198">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="839d4-198">In This Section</span></span>  
 <span data-ttu-id="839d4-199">다음 항목에서는 테이블릭스 데이터 영역 작업에 대한 추가 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="839d4-199">The following topics provide additional information about working with the tablix data region.</span></span>  
  
 [<span data-ttu-id="839d4-200">테이블릭스 데이터 영역&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="839d4-200">Tablix Data Region &#40;Report Builder and SSRS&#41;</span></span>](../tablix-data-region-report-builder-and-ssrs.md)  
 <span data-ttu-id="839d4-201">테이블릭스의 영역, 세부 데이터 및 그룹화된 데이터, 열 및 행 그룹, 정적/동적 행 및 열과 같은 테이블릭스 데이터 영역과 관련된 주요 개념에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="839d4-201">Explains key concepts related to the tablix data region such as areas of the tablix, detail and grouped data, column and row groups, and static and dynamic rows and columns.</span></span>  
  
 [<span data-ttu-id="839d4-202">테이블릭스 데이터 영역에 데이터 추가&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="839d4-202">Adding Data to a Tablix Data Region &#40;Report Builder and SSRS&#41;</span></span>](adding-data-to-a-tablix-data-region-report-builder-and-ssrs.md)  
 <span data-ttu-id="839d4-203">세부 데이터/그룹화된 데이터, 부분합/합계, 및 레이블을 테이블릭스 데이터 영역에 추가하는 방법에 대한 자세한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="839d4-203">Provides detailed information about adding detail and grouped data, subtotals and totals, and labels to a tablix data region.</span></span>  
  
 [<span data-ttu-id="839d4-204">보고서 페이지에서 테이블릭스 데이터 영역 표시 제어&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="839d4-204">Controlling the Tablix Data Region Display on a Report Page &#40;Report Builder and SSRS&#41;</span></span>](controlling-the-tablix-data-region-display-on-a-report-page.md)  
 <span data-ttu-id="839d4-205">보고서에서 테이블릭스 데이터 영역이 표시되는 방법을 변경할 수 있는 테이블릭스 데이터 영역의 속성에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="839d4-205">Describes properties for a tablix data region that you can modify to change the way a tablix data region appears when you view it in a report.</span></span>  
  
 [<span data-ttu-id="839d4-206">행 및 열 제목 제어&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="839d4-206">Controlling Row and Column Headings &#40;Report Builder and SSRS&#41;</span></span>](controlling-row-and-column-headings-report-builder-and-ssrs.md)  
 <span data-ttu-id="839d4-207">테이블, 행렬 또는 목록 데이터 영역이 가로 또는 세로로 여러 페이지에 걸쳐 있는 경우 행 및 열 머리글을 제어하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="839d4-207">Describes how to control row and column headings when a table, matrix, or list data region cans span multiple pages horizontally or vertically.</span></span>  
  
 [<span data-ttu-id="839d4-208">재귀 계층 구조 그룹 생성&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="839d4-208">Creating Recursive Hierarchy Groups &#40;Report Builder and SSRS&#41;</span></span>](creating-recursive-hierarchy-groups-report-builder-and-ssrs.md)  
 <span data-ttu-id="839d4-209">부모와 자식 간의 관계가 데이터 세트의 필드에 표시되는 재귀적 데이터를 표시하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="839d4-209">Describes how to display recursive data where the relationship between parent and child is represented by fields in the dataset.</span></span>  
  
 [<span data-ttu-id="839d4-210">그룹 이해&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="839d4-210">Understanding Groups &#40;Report Builder and SSRS&#41;</span></span>](understanding-groups-report-builder-and-ssrs.md)  
 <span data-ttu-id="839d4-211">그룹의 의미 및 그룹을 사용하는 경우와 각 테이블릭스 데이터 영역에 사용할 수 있는 그룹에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="839d4-211">Explains what groups are and when you use them and describes the groups available for the different tablix data regions.</span></span>  
  

  
## <a name="see-also"></a><span data-ttu-id="839d4-212">참고 항목</span><span class="sxs-lookup"><span data-stu-id="839d4-212">See Also</span></span>  
 <span data-ttu-id="839d4-213">[데이터 집합 필터, 데이터 영역 필터 및 그룹 필터를 추가 하 여 보고서 작성기 및 SSRS &#40;&#41;](add-dataset-filters-data-region-filters-and-group-filters.md) </span><span class="sxs-lookup"><span data-stu-id="839d4-213">[Add Dataset Filters, Data Region Filters, and Group Filters &#40;Report Builder and SSRS&#41;](add-dataset-filters-data-region-filters-and-group-filters.md) </span></span>  
 <span data-ttu-id="839d4-214">[중첩 된 데이터 영역 &#40;보고서 작성기 및 SSRS&#41;](nested-data-regions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="839d4-214">[Nested Data Regions &#40;Report Builder and SSRS&#41;](nested-data-regions-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="839d4-215">[동일한 데이터 집합에 여러 데이터 영역 연결 &#40;보고서 작성기 및 SSRS&#41;](linking-multiple-data-regions-to-the-same-dataset-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="839d4-215">[Linking Multiple Data Regions to the Same Dataset &#40;Report Builder and SSRS&#41;](linking-multiple-data-regions-to-the-same-dataset-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="839d4-216">[식&#40;보고서 작성기 및 SSRS&#41;](expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="839d4-216">[Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="839d4-217">[데이터 필터링, 그룹화 및 정렬 &#40;보고서 작성기 및 SSRS&#41;](filter-group-and-sort-data-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="839d4-217">[Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;](filter-group-and-sort-data-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="839d4-218">[보고서 매개 변수 &#40;보고서 작성기 및 보고서 디자이너&#41;](report-parameters-report-builder-and-report-designer.md) </span><span class="sxs-lookup"><span data-stu-id="839d4-218">[Report Parameters &#40;Report Builder and Report Designer&#41;](report-parameters-report-builder-and-report-designer.md) </span></span>  
 <span data-ttu-id="839d4-219">[차트 &#40;보고서 작성기 및 SSRS&#41;](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="839d4-219">[Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="839d4-220">계기&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="839d4-220">Gauges &#40;Report Builder and SSRS&#41;</span></span>](gauges-report-builder-and-ssrs.md)  
  
  
