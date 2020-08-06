---
title: 테이블 및 열 (SSAS 테이블 형식) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: c428d717-05de-436c-b9dc-e8c1925a60ca
author: minewiskan
ms.author: owend
ms.openlocfilehash: 3f23b21ce492fd3160df727c1562ee706848fa99
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738812"
---
# <a name="tables-and-columns-ssas-tabular"></a><span data-ttu-id="2cb0e-102">테이블 및 열(SSAS 테이블 형식)</span><span class="sxs-lookup"><span data-stu-id="2cb0e-102">Tables and Columns (SSAS Tabular)</span></span>
  <span data-ttu-id="2cb0e-103">테이블 가져오기 마법사를 사용하여 테이블과 데이터를 모델에 추가한 후에는 데이터의 새 열 추가, 테이블 간의 관계 만들기, 데이터를 확장하는 계산 정의, 보기 쉽게 테이블의 데이터 필터링 및 정렬 등을 수행하여 테이블 작업을 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2cb0e-103">After you have added tables and data into a model by using the Table Import Wizard, you can begin working with the tables by adding new columns of data, creating relationships between tables, defining calculations that extend the data, and filtering and sorting data in the tables for easier viewing.</span></span>  
  
 <span data-ttu-id="2cb0e-104">이 항목의 섹션:</span><span class="sxs-lookup"><span data-stu-id="2cb0e-104">Sections in this topic:</span></span>  
  
-   [<span data-ttu-id="2cb0e-105">이점</span><span class="sxs-lookup"><span data-stu-id="2cb0e-105">Benefits</span></span>](#bkmk_benefits)  
  
-   [<span data-ttu-id="2cb0e-106">테이블 및 열 작업</span><span class="sxs-lookup"><span data-stu-id="2cb0e-106">Working with tables and columns</span></span>](#bkmk_working)  
  
-   [<span data-ttu-id="2cb0e-107">관련 작업</span><span class="sxs-lookup"><span data-stu-id="2cb0e-107">Related Tasks</span></span>](#bkmk_related_tasks)  
  
##  <a name="benefits"></a><a name="bkmk_benefits"></a> <span data-ttu-id="2cb0e-108">이점</span><span class="sxs-lookup"><span data-stu-id="2cb0e-108">Benefits</span></span>  
 <span data-ttu-id="2cb0e-109">테이블 형식 모델에서 테이블은 열 및 기타 메타데이터가 정의되는 프레임 워크를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="2cb0e-109">Tables, in tabular models, provide the framework in which columns and other metadata are defined.</span></span> <span data-ttu-id="2cb0e-110">테이블에는 다음이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="2cb0e-110">Tables include:</span></span>  
  
 <span data-ttu-id="2cb0e-111">**테이블 정의**</span><span class="sxs-lookup"><span data-stu-id="2cb0e-111">**Table Definition**</span></span>  
 <span data-ttu-id="2cb0e-112">테이블 정의에는 열 집합이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="2cb0e-112">The table definition includes the set of columns.</span></span> <span data-ttu-id="2cb0e-113">데이터 원본에서 열을 가져오거나 계산 열과 같이 열을 수동으로 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2cb0e-113">Columns can be imported from a data source or added manually, such as with calculated columns.</span></span>  
  
 <span data-ttu-id="2cb0e-114">**테이블 메타 데이터**</span><span class="sxs-lookup"><span data-stu-id="2cb0e-114">**Table Metadata**</span></span>  
 <span data-ttu-id="2cb0e-115">관계, 측정값, 역할, 큐브 뷰 및 붙여넣은 데이터는 모두 테이블 컨텍스트 내에서 개체를 정의하는 메타데이터입니다.</span><span class="sxs-lookup"><span data-stu-id="2cb0e-115">Relationships, measures, roles, perspectives, and pasted data are all metadata the define objects within the context of a table.</span></span>  
  
 <span data-ttu-id="2cb0e-116">**Data**</span><span class="sxs-lookup"><span data-stu-id="2cb0e-116">**Data**</span></span>  
 <span data-ttu-id="2cb0e-117">테이블 가져오기 마법사를 사용하거나 계산 열에서 새 데이터를 만들어 테이블을 처음 가져오면 데이터가 테이블 열에 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="2cb0e-117">Data is populated in table columns when you first import tables by using the Table Import Wizard or by creating new data in calculated columns.</span></span> <span data-ttu-id="2cb0e-118">원본에서 데이터가 변경되거나 모델이 메모리에서 제거되면 처리 작업을 실행하여 데이터를 테이블에 다시 채워야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2cb0e-118">When data changes at the source, or when a model is removed from memory, you must run a process operation to re-populate the data into the tables.</span></span>  
  
##  <a name="working-with-tables-and-columns"></a><a name="bkmk_working"></a><span data-ttu-id="2cb0e-119">테이블 및 열 작업</span><span class="sxs-lookup"><span data-stu-id="2cb0e-119">Working with tables and columns</span></span>  
 <span data-ttu-id="2cb0e-120">모델 디자이너에서는 새 모델 테이블을 직접 만들지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2cb0e-120">In the model designer, you do not create new model tables directly.</span></span> <span data-ttu-id="2cb0e-121">다른 데이터 원본에서 데이터를 가져오거나 복사할 때마다 새 탭이 자동으로 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="2cb0e-121">A new tab is created automatically for you whenever data is imported or copied from another data source.</span></span> <span data-ttu-id="2cb0e-122">모델 디자이너의 각 탭에는 다음을 포함할 수 있는 데이터 테이블이 하나씩 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2cb0e-122">Each tab (in the model designer) contains one table of data, which can include the following:</span></span>  
  
-   <span data-ttu-id="2cb0e-123">관계형 데이터베이스의 단일 테이블이나 뷰 또는 Analysis Services 큐브와 같은 관계형이 아닌 다른 원본</span><span class="sxs-lookup"><span data-stu-id="2cb0e-123">A single table or view from a relational database, or from other non-relational sources, such as an Analysis Services cube.</span></span>  
  
-   <span data-ttu-id="2cb0e-124">피드 또는 텍스트 파일에서 가져온 테이블 형식의 데이터 집합</span><span class="sxs-lookup"><span data-stu-id="2cb0e-124">A tabular set of data imported from a feed or text file.</span></span>  
  
-   <span data-ttu-id="2cb0e-125">복사하여 테이블에 붙여넣은 관계형 데이터 및 테이블 형식(HTML) 데이터의 조합</span><span class="sxs-lookup"><span data-stu-id="2cb0e-125">A combination of both relational data and tabular (HTML) data copy and pasted into the table.</span></span>  
  
 <span data-ttu-id="2cb0e-126">데이터를 가져오면 데이터의 각 테이블이나 뷰, 시트 또는 파일이 모델 디자이너에 테이블로 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="2cb0e-126">When you import data, each table or view, sheet, or file of data is added as a table in the model designer.</span></span> <span data-ttu-id="2cb0e-127">다양한 원본의 데이터를 각각 별도의 탭에 추가하는 것이 일반적지만 **붙여넣기** 및 **추가하여 붙여넣기**를 사용하여 데이터를 단일 테이블로 결합할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2cb0e-127">You typically add data from various sources onto separate tabs, but you can combine data in a single table by using **Paste** and **Paste Append**.</span></span> <span data-ttu-id="2cb0e-128">자세한 내용은 [데이터 복사 및 붙여넣기&#40;SSAS 테이블 형식&#41;](../copy-and-paste-data-ssas-tabular.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2cb0e-128">For more information, see [Copy and Paste Data &#40;SSAS Tabular&#41;](../copy-and-paste-data-ssas-tabular.md).</span></span>  
  
 <span data-ttu-id="2cb0e-129">필요한 데이터를 모두 추가한 후 테이블 간의 추가 관계를 만들거나, 다른 테이블의 관련 값을 조회 또는 참조하거나, 새 계산 열을 추가하여 파생 값을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2cb0e-129">After you have added the data that you need, you can create additional relationships between the tables, look up or reference related values in other tables, or create derived values by adding new calculated columns.</span></span>  
  
 <span data-ttu-id="2cb0e-130">매우 큰 데이터 집합을 작업하는 경우 특정 데이터가 표시되지 않도록 필터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2cb0e-130">If you are working very large data sets, you may want to filter out certain data so it is not visible.</span></span> <span data-ttu-id="2cb0e-131">다른 순서로 데이터를 정렬할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2cb0e-131">You may also want to sort data in a different order.</span></span> <span data-ttu-id="2cb0e-132">모델 디자이너를 사용하면 필터, 정렬 및 숨기기 기능을 사용하여 전체 열 또는 특정 데이터를 표시하거나 표시하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2cb0e-132">By using the model designer, you can use the filter, sort, and hide features to display, or not display, entire columns or certain data.</span></span>  
  
##  <a name="related-tasks"></a><a name="bkmk_related_tasks"></a> <span data-ttu-id="2cb0e-133">관련 작업</span><span class="sxs-lookup"><span data-stu-id="2cb0e-133">Related Tasks</span></span>  
  
|<span data-ttu-id="2cb0e-134">항목</span><span class="sxs-lookup"><span data-stu-id="2cb0e-134">Topic</span></span>|<span data-ttu-id="2cb0e-135">설명</span><span class="sxs-lookup"><span data-stu-id="2cb0e-135">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="2cb0e-136">테이블에 열 추가&#40;SSAS 테이블 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="2cb0e-136">Add Columns to a Table &#40;SSAS Tabular&#41;</span></span>](add-columns-to-a-table-ssas-tabular.md)|<span data-ttu-id="2cb0e-137">원본 열을 테이블 정의에 추가하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="2cb0e-137">Describes how to add a source column to a table definition.</span></span>|  
|[<span data-ttu-id="2cb0e-138">열 삭제&#40;SSAS 테이블 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="2cb0e-138">Delete a Column &#40;SSAS Tabular&#41;</span></span>](delete-a-column-ssas-tabular.md)|<span data-ttu-id="2cb0e-139">모델 디자이너 또는 테이블 속성 대화 상자를 사용하여 모델 테이블 열을 삭제하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="2cb0e-139">Describes how to delete a model table column by using the model designer or by using the Table Properties dialog box.</span></span>|  
|[<span data-ttu-id="2cb0e-140">테이블, 열 또는 행 필터 매핑 변경&#40;SSAS 테이블 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="2cb0e-140">Change table, column, or row filter mappings &#40;SSAS Tabular&#41;</span></span>](change-table-column-or-row-filter-mappings-ssas-tabular.md)|<span data-ttu-id="2cb0e-141">테이블 속성 편집 대화 상자에서 테이블 미리 보기 또는 SQL 쿼리 편집기를 사용하여 테이블, 열 또는 행 필터 매핑을 변경하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="2cb0e-141">Describes how to change table, column, or row filter mappings by using the table preview or SQL query editor in the Edit Table Properties dialog box.</span></span>|  
|[<span data-ttu-id="2cb0e-142">시간 인텔리전스에 사용할 날짜 테이블로 표시 지정&#40;SSAS 테이블 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="2cb0e-142">Specify Mark as Date Table for use with Time Intelligence &#40;SSAS Tabular&#41;</span></span>](specify-mark-as-date-table-for-use-with-time-intelligence-ssas-tabular.md)|<span data-ttu-id="2cb0e-143">날짜 테이블로 표시 대화 상자를 사용하여 날짜 테이블 및 고유 식별자 열을 지정하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="2cb0e-143">Describes how to use the Mark as Date Table dialog box to specify a date table and unique identifier column.</span></span> <span data-ttu-id="2cb0e-144">날짜 테이블 및 고유 식별자 지정은 DAX 수식에서 시간 인텔리전스 기능을 사용할 경우에 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="2cb0e-144">Specifying a date table and unique identifier is necessary when using time intelligence functions in DAX formulas.</span></span>|  
|[<span data-ttu-id="2cb0e-145">테이블 추가&#40;SSAS 테이블 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="2cb0e-145">Add a Table &#40;SSAS Tabular&#41;</span></span>](add-a-table-ssas-tabular.md)|<span data-ttu-id="2cb0e-146">기존 데이터 원본 연결을 사용하여 데이터 원본의 테이블을 추가하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="2cb0e-146">Describes how to add a table from a data source by using an existing data source connection.</span></span>|  
|[<span data-ttu-id="2cb0e-147">테이블 삭제&#40;SSAS 테이블 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="2cb0e-147">Delete a Table &#40;SSAS Tabular&#41;</span></span>](delete-a-table-ssas-tabular.md)|<span data-ttu-id="2cb0e-148">모델 작업 영역 데이터베이스에서 더 이상 필요하지 않은 테이블을 삭제하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="2cb0e-148">Describes how to delete tables in your model workspace database that you no longer need.</span></span>|  
|[<span data-ttu-id="2cb0e-149">테이블 또는 열 이름 바꾸기&#40;SSAS 테이블 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="2cb0e-149">Rename a Table or Column &#40;SSAS Tabular&#41;</span></span>](rename-a-table-or-column-ssas-tabular.md)|<span data-ttu-id="2cb0e-150">모델에서 쉽게 식별할 수 있도록 테이블 또는 열의 이름을 바꾸는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="2cb0e-150">Describes how to rename a table or column to make it more identifiable in your model.</span></span>|  
|[<span data-ttu-id="2cb0e-151">열 데이터 형식 설정&#40;SSAS 테이블 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="2cb0e-151">Set the Data Type of a Column &#40;SSAS Tabular&#41;</span></span>](set-the-data-type-of-a-column-ssas-tabular.md)|<span data-ttu-id="2cb0e-152">열의 데이터 형식을 변경하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="2cb0e-152">Describes how to change the data type of a column.</span></span> <span data-ttu-id="2cb0e-153">데이터 형식은 열의 데이터가 저장되고 표시되는 방법을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="2cb0e-153">The data type defines how data in the column is stored and presented.</span></span>|  
|[<span data-ttu-id="2cb0e-154">열 숨기기 또는 고정&#40;SSAS 테이블 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="2cb0e-154">Hide or Freeze Columns &#40;SSAS Tabular&#41;</span></span>](hide-or-freeze-columns-ssas-tabular.md)|<span data-ttu-id="2cb0e-155">표시 하지 않을 열을 숨기는 방법과 한 영역에서 특정 열을 고정 (잠금) 하 여 모델의 다른 영역으로 스크롤할 때 모델의 영역을 계속 표시 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="2cb0e-155">Describes how to hide columns that you don't want to display and how to keep an area of a model visible while you scroll to another area of the model by freezing (locking) specific columns in one area.</span></span>|  
|[<span data-ttu-id="2cb0e-156">계산 열&#40;SSAS 테이블 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="2cb0e-156">Calculated Columns &#40;SSAS Tabular&#41;</span></span>](ssas-calculated-columns.md)|<span data-ttu-id="2cb0e-157">이 섹션의 항목에서는 계산 열을 사용하여 집계된 데이터를 모델에 추가하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="2cb0e-157">Topics in this section describe how you can use calculated columns to add aggregated data to your model.</span></span>|  
|[<span data-ttu-id="2cb0e-158">데이터 필터링 및 정렬&#40;SSAS 테이블 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="2cb0e-158">Filter and Sort Data &#40;SSAS Tabular&#41;</span></span>](../filter-and-sort-data-ssas-tabular.md)|<span data-ttu-id="2cb0e-159">이 섹션의 항목에서는 모델 디자이너의 컨트롤을 사용하여 데이터를 필터링하거나 정렬하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="2cb0e-159">Topics in this section describe how you can filter or sort data by using controls in the model designer.</span></span>|  
  
  
