---
title: 공간 인덱스 만들기, 수정 및 삭제 | Microsoft 문서
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- indexes [SQL Server], creating
- spatial indexes [SQL Server], dropping
- spatial indexes [SQL Server], creating
- indexes [SQL Server], dropping
- indexes [SQL Server], modifying
- spatial indexes [SQL Server], modifying
ms.assetid: 00c1b927-8ec5-44cf-87c2-c8de59745735
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 88de17e8c487d9a965f2e236edac064dc2fe4c7c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646855"
---
# <a name="create-modify-and-drop-spatial-indexes"></a><span data-ttu-id="91ca7-102">공간 인덱스 만들기, 수정 및 삭제</span><span class="sxs-lookup"><span data-stu-id="91ca7-102">Create, Modify, and Drop Spatial Indexes</span></span>
  <span data-ttu-id="91ca7-103">공간 인덱스는 `geometry` 또는 `geography` 데이터 형식의 열 ( *공간 열*)에서 특정 작업을 보다 효율적으로 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="91ca7-103">A spatial index can more efficiently perform certain operations on a column of the `geometry` or `geography` data type (a *spatial column*).</span></span> <span data-ttu-id="91ca7-104">하나의 공간 열에 두 개 이상의 공간 인덱스가 지정될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="91ca7-104">More than one spatial index can be specified on a spatial column.</span></span> <span data-ttu-id="91ca7-105">예를 들어 이 기능은 단일 열에 다른 공간 분할 매개 변수를 인덱싱할 경우에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="91ca7-105">This is useful, for example, for indexing different tessellation parameters in a single column.</span></span>  
  
 <span data-ttu-id="91ca7-106">공간 인덱스를 만드는 작업에 대한 제한 사항이 많이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="91ca7-106">There are a number of restrictions on creating spatial indexes.</span></span> <span data-ttu-id="91ca7-107">자세한 내용은 이 항목의 [공간 인덱스의 제한 사항](#restrictions) 을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="91ca7-107">For more information, see [Restrictions on Spatial Indexes](#restrictions) in this topic.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="91ca7-108">공간 인덱스와 파티션 및 파일 그룹의 관계에 대한 자세한 내용은 [CREATE SPATIAL INDEX&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-spatial-index-transact-sql)의 "주의" 섹션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="91ca7-108">For information about the relationship of spatial indexes to partition and to filegroups, see the "Remarks" section in [CREATE SPATIAL INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-spatial-index-transact-sql).</span></span>  
  
##  <a name="creating-modifying-and-dropping-spatial-indexes"></a><a name="creating"></a> <span data-ttu-id="91ca7-109">공간 인덱스 만들기, 수정 및 삭제</span><span class="sxs-lookup"><span data-stu-id="91ca7-109">Creating, Modifying, and Dropping Spatial Indexes</span></span>  
  
###  <a name="to-create-a-spatial-index"></a><a name="create"></a> <span data-ttu-id="91ca7-110">공간 인덱스를 만들려면</span><span class="sxs-lookup"><span data-stu-id="91ca7-110">To create a spatial index</span></span>  
 <span data-ttu-id="91ca7-111">**Transact-SQL을 사용하여 공간 인덱스를 만들려면**</span><span class="sxs-lookup"><span data-stu-id="91ca7-111">**To create a spatial index by using Transact-SQL**</span></span>  
 [<span data-ttu-id="91ca7-112">CREATE SPATIAL INDEX&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="91ca7-112">CREATE SPATIAL INDEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-spatial-index-transact-sql)  
  
 <span data-ttu-id="91ca7-113">**Management Studio의 새 인덱스 대화 상자를 사용하여 공간 인덱스를 만들려면**</span><span class="sxs-lookup"><span data-stu-id="91ca7-113">**To create a spatial index by using the New Index dialog box in Management Studio**</span></span>  
 ##### <a name="to-create-a-spatial-index-in-management-studio"></a><span data-ttu-id="91ca7-114">Management Studio에서 공간 인덱스를 만들려면</span><span class="sxs-lookup"><span data-stu-id="91ca7-114">To create a spatial index in Management Studio</span></span>  
  
1.  <span data-ttu-id="91ca7-115">개체 탐색기에서 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 의 인스턴스에 연결한 다음 해당 인스턴스를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="91ca7-115">In Object Explorer, connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="91ca7-116">**데이터베이스**를 확장하고 지정한 인덱스가 있는 테이블이 포함된 데이터베이스를 확장한 다음 **테이블**을 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="91ca7-116">Expand **Databases**, expand the database that contains the table with the specified index, and then expand **Tables**.</span></span>  
  
3.  <span data-ttu-id="91ca7-117">인덱스를 만들 테이블을 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="91ca7-117">Expand the table for which you want to create the index.</span></span>  
  
4.  <span data-ttu-id="91ca7-118">**인덱스** 를 마우스 오른쪽 단추로 클릭하고 **새 인덱스**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="91ca7-118">Right-click **Indexes** and select **New Index**.</span></span>  
  
5.  <span data-ttu-id="91ca7-119">**인덱스 이름** 필드에 인덱스의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="91ca7-119">In the **Index name** field, enter a name for the index.</span></span>  
  
6.  <span data-ttu-id="91ca7-120">**인덱스 유형** 드롭다운 목록에서 **공간**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="91ca7-120">In the **Index type** drop-down list, select **Spatial**.</span></span>  
  
7.  <span data-ttu-id="91ca7-121">인덱싱하려는 공간 열을 지정하려면 **추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="91ca7-121">To specify the spatial column that you want to index, click **Add**.</span></span>  
  
8.  <span data-ttu-id="91ca7-122">**에서 열 선택** *\<table name>* 대화 상자에서 해당 확인란을 선택 하 여 또는 형식의 열을 선택 `geometry` `geography` 합니다.</span><span class="sxs-lookup"><span data-stu-id="91ca7-122">In the **Select Columns from** *\<table name>* dialog box, select a column of type `geometry` or `geography` by selecting the corresponding check box.</span></span> <span data-ttu-id="91ca7-123">그러면 다른 공간 열이 편집할 수 없게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="91ca7-123">Any other spatial columns then become uneditable.</span></span> <span data-ttu-id="91ca7-124">다른 공간 열을 선택하려면 먼저 현재 선택된 열의 선택을 취소해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="91ca7-124">If you want to select a different spatial column, you must first clear the currently selected column.</span></span> <span data-ttu-id="91ca7-125">완료되었으면 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="91ca7-125">When finished, click **OK**.</span></span>  
  
9. <span data-ttu-id="91ca7-126">**인덱스 키 열** 표에서 열 선택 사항을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="91ca7-126">Verify your column selection in the **Index key columns** grid.</span></span>  
  
10. <span data-ttu-id="91ca7-127">**인덱스 속성** 대화 상자의 **페이지 선택** 창에서 **공간**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="91ca7-127">In the **Select a page** pane of the **Index Properties** dialog box, click **Spatial**.</span></span>  
  
11. <span data-ttu-id="91ca7-128">**공간** 페이지에서 인덱스의 공간 속성에 사용할 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="91ca7-128">On the **Spatial** page, specify the values that you want to use for the spatial properties of the index.</span></span>  
  
     <span data-ttu-id="91ca7-129">유형 열에 인덱스를 만들 때 `geometry` 경계 상자의 **( *`X-min`* , *`Y-min`* )** 및 **( *`X-max`* , *`Y-max`* )** 좌표를 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="91ca7-129">When creating an index on a `geometry` type column, you must specify the **(*`X-min`*,*`Y-min`*)** and **(*`X-max`*,*`Y-max`*)** coordinates of the bounding box.</span></span> <span data-ttu-id="91ca7-130">유형 열의 인덱스의 경우 지리 `geography` 표 공간 분할 구성표를 지정 하면 지리 표 공간 분할이 경계 상자를 **Geography grid** 사용 하지 않으므로 경계 상자 필드는 읽기 전용이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="91ca7-130">For an index on a `geography` type column, the bounding-box fields become read-only after you specify the **Geography grid** tessellation scheme, because geography grid tessellation does not use a bounding box.</span></span>  
  
     <span data-ttu-id="91ca7-131">필요에 따라 공간 분할(tessellation) 구성표의 모든 수준에서 표 밀도 및 **개체당 셀 수** 필드에 대해 기본값이 아닌 값을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="91ca7-131">Optionally, you can specify nondefault values for the **Cells Per Object** field and for the grid density at any level of the tessellation scheme.</span></span> <span data-ttu-id="91ca7-132">[!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] 또는 [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] 이상의 경우 개체당 기본 셀 수는 각각 16과 8이고, 기본 표 밀도는 **의 경우** 보통 [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]입니다.</span><span class="sxs-lookup"><span data-stu-id="91ca7-132">The default number of cells per object is 16 for [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] or 8 for [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] or higher, and the default grid density is **Medium** for [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)].</span></span>  
  
     <span data-ttu-id="91ca7-133">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서는 공간 분할(tessellation) 구성표의 GEOMETRY_AUTO_GRID 또는 GEOGRAPHY_AUTO_GRID를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="91ca7-133">You can select GEOMETRY_AUTO_GRID or GEOGRAPHY_AUTO_GRID for tessellation scheme in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="91ca7-134">GEOMETRY_AUTO_GRID 또는 GEOGRAPHY_AUTO_GRID를 선택한 경우 수준 1, 수준 2, 수준 3 및 수준 4 표 밀도 옵션은 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="91ca7-134">When GEOMETRY_AUTO_GRID or GEOGRAPHY_AUTO_GRID is selected, then Level 1, Level 2, Level 3, and Level 4 grid density options are disabled.</span></span>  
  
     <span data-ttu-id="91ca7-135">이러한 속성에 대한 자세한 내용은 [Index Properties F1 Help](../indexes/index-properties-f1-help.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="91ca7-135">For more information about these properties, see [Index Properties F1 Help](../indexes/index-properties-f1-help.md).</span></span>  
  
12. <span data-ttu-id="91ca7-136">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="91ca7-136">Click **OK**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="91ca7-137">같은 공간 열 또는 다른 공간 열에 공간 인덱스를 더 만들려면 위 단계를 반복하십시오.</span><span class="sxs-lookup"><span data-stu-id="91ca7-137">To create another spatial index on the same or a different spatial column, repeat the preceding steps.</span></span>  
  
  
 <span data-ttu-id="91ca7-138">**Management Studio의 테이블 디자이너를 사용하여 공간 인덱스를 만들려면**</span><span class="sxs-lookup"><span data-stu-id="91ca7-138">**To create a spatial index by using Table Designer in Management Studio**</span></span>  
 ##### <a name="to-create-a-spatial-index-in-table-designer"></a><span data-ttu-id="91ca7-139">테이블 디자이너에서 공간 인덱스를 만들려면</span><span class="sxs-lookup"><span data-stu-id="91ca7-139">To create a spatial index in Table Designer</span></span>  
  
1.  <span data-ttu-id="91ca7-140">개체 탐색기에서 공간 인덱스를 만들려는 테이블을 마우스 오른쪽 단추로 클릭하고 **디자인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="91ca7-140">In Object Explorer, right-click the table for which you want to create a spatial index, and then click **Design**.</span></span>  
  
     <span data-ttu-id="91ca7-141">테이블 디자이너에서 테이블이 열립니다.</span><span class="sxs-lookup"><span data-stu-id="91ca7-141">The table opens in Table Designer.</span></span>  
  
2.  <span data-ttu-id="91ca7-142">인덱스에 대해 `geometry` 또는 `geography` 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="91ca7-142">Select a `geometry` or `geography` column for the index.</span></span>  
  
3.  <span data-ttu-id="91ca7-143">**테이블 디자이너** 메뉴에서 **공간 인덱스**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="91ca7-143">On the **Table Designer** menu, click **Spatial Index**.</span></span>  
  
4.  <span data-ttu-id="91ca7-144">**공간 인덱스** 대화 상자에서 **추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="91ca7-144">In the **Spatial Indexes** dialog box, click **Add**.</span></span>  
  
5.  <span data-ttu-id="91ca7-145">**선택한 공간 인덱스** 목록에서 새 인덱스를 선택하고 오른쪽에 있는 표에서 공간 인덱스의 속성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="91ca7-145">Select the new index in the **Selected Spatial Index** list, and in the grid to the right, set the properties for the spatial index.</span></span> <span data-ttu-id="91ca7-146">속성에 대한 자세한 내용은 [공간 인덱스 대화 상자&#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/visual-database-tools.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="91ca7-146">For information about the properties, see [Spatial Indexes Dialog Box &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/visual-database-tools.md).</span></span>  
  
  
###  <a name="to-alter-a-spatial-index"></a><a name="alter"></a> <span data-ttu-id="91ca7-147">공간 인덱스를 변경하려면</span><span class="sxs-lookup"><span data-stu-id="91ca7-147">To alter a spatial index</span></span>  
  
-   [<span data-ttu-id="91ca7-148">ALTER INDEX&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="91ca7-148">ALTER INDEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-index-transact-sql)  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="91ca7-149">공간 인덱스에 지정된 옵션(예: BOUNDING_BOX 또는 GRID)을 변경하려면 DROP_EXISTING = ON을 지정하는 CREATE SPATIAL INDEX 문을 사용하거나 해당 공간 인덱스를 삭제하고 새로 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="91ca7-149">To change options that are specific to a spatial index, such as BOUNDING_BOX or GRID, you can either use a CREATE SPATIAL INDEX statement that specifies DROP_EXISTING = ON, or drop the spatial index and create a new one.</span></span> <span data-ttu-id="91ca7-150">예제를 보려면 [CREATE SPATIAL INDEX&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-spatial-index-transact-sql)의 "주의" 섹션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="91ca7-150">For an example, see [CREATE SPATIAL INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-spatial-index-transact-sql).</span></span>  
  
-   [<span data-ttu-id="91ca7-151">인덱스 수정</span><span class="sxs-lookup"><span data-stu-id="91ca7-151">Modify an Index</span></span>](../indexes/modify-an-index.md)  
  
-   [<span data-ttu-id="91ca7-152">다른 파일 그룹으로 기존 인덱스 이동</span><span class="sxs-lookup"><span data-stu-id="91ca7-152">Move an Existing Index to a Different Filegroup</span></span>](../indexes/move-an-existing-index-to-a-different-filegroup.md)  
  
  
###  <a name="to-drop-a-spatial-index"></a><a name="drop"></a> <span data-ttu-id="91ca7-153">공간 인덱스를 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="91ca7-153">To drop a spatial index</span></span>  
 <span data-ttu-id="91ca7-154">**Transact-SQL을 사용하여 공간 인덱스를 삭제하려면**</span><span class="sxs-lookup"><span data-stu-id="91ca7-154">**To drop a spatial index by using Transact-SQL**</span></span>  
 [<span data-ttu-id="91ca7-155">DROP INDEX&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="91ca7-155">DROP INDEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/drop-index-transact-sql)  
  
 <span data-ttu-id="91ca7-156">**Management Studio를 사용하여 인덱스를 삭제하려면**</span><span class="sxs-lookup"><span data-stu-id="91ca7-156">**To drop an index by using Management Studio**</span></span>  
 [<span data-ttu-id="91ca7-157">인덱스 삭제</span><span class="sxs-lookup"><span data-stu-id="91ca7-157">Delete an Index</span></span>](../indexes/delete-an-index.md)  
  
 <span data-ttu-id="91ca7-158">**Management Studio의 테이블 디자이너를 사용하여 공간 인덱스를 삭제하려면**</span><span class="sxs-lookup"><span data-stu-id="91ca7-158">**To drop a spatial index by using Table Designer in Management Studio**</span></span>  
 ##### <a name="to-drop-a-spatial-index-in-table-designer"></a><span data-ttu-id="91ca7-159">테이블 디자이너에서 공간 인덱스를 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="91ca7-159">To drop a spatial index in Table Designer</span></span>  
  
1.  <span data-ttu-id="91ca7-160">개체 탐색기에서 삭제하려는 공간 인덱스가 포함된 테이블을 마우스 오른쪽 단추로 클릭하고 **디자인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="91ca7-160">In Object Explorer, right-click the table with the spatial index you want to delete and click **Design**.</span></span>  
  
     <span data-ttu-id="91ca7-161">테이블 디자이너에서 테이블이 열립니다.</span><span class="sxs-lookup"><span data-stu-id="91ca7-161">The table opens in Table Designer.</span></span>  
  
2.  <span data-ttu-id="91ca7-162">**테이블 디자이너** 메뉴에서 **공간 인덱스**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="91ca7-162">On the **Table Designer** menu, click **Spatial Index**.</span></span>  
  
     <span data-ttu-id="91ca7-163">**공간 인덱스** 대화 상자가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="91ca7-163">The **Spatial Index** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="91ca7-164">**선택한 공간 인덱스** 열에서 삭제하려는 인덱스를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="91ca7-164">Click the index you want to delete in the **Selected Spatial Index** column.</span></span>  
  
4.  <span data-ttu-id="91ca7-165">**삭제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="91ca7-165">Click **Delete**.</span></span>  
  
  
##  <a name="restrictions-on-spatial-indexes"></a><a name="restrictions"></a> <span data-ttu-id="91ca7-166">공간 인덱스의 제한 사항</span><span class="sxs-lookup"><span data-stu-id="91ca7-166">Restrictions on Spatial Indexes</span></span>  
 <span data-ttu-id="91ca7-167">공간 인덱스는 `geometry` 또는 `geography` 유형의 열에서만 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="91ca7-167">A spatial index can be created only on a column of type `geometry` or `geography`.</span></span>  
  
### <a name="table-and-view-restrictions"></a><span data-ttu-id="91ca7-168">테이블 및 뷰 제한 사항</span><span class="sxs-lookup"><span data-stu-id="91ca7-168">Table and View Restrictions</span></span>  
 <span data-ttu-id="91ca7-169">공간 인덱스는 기본 키가 있는 테이블에서만 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="91ca7-169">Spatial indexes can be defined only on a table that has a primary key.</span></span> <span data-ttu-id="91ca7-170">테이블의 최대 기본 키 열 수는 15개입니다.</span><span class="sxs-lookup"><span data-stu-id="91ca7-170">The maximum number of primary key columns on the table is 15.</span></span>  
  
 <span data-ttu-id="91ca7-171">인덱스 키 레코드의 최대 크기는 895바이트입니다.</span><span class="sxs-lookup"><span data-stu-id="91ca7-171">The maximum size of index key records is 895 bytes.</span></span> <span data-ttu-id="91ca7-172">크기가 더 커지면 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="91ca7-172">Larger sizes raise an error.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="91ca7-173">테이블에 공간 인덱스가 정의되는 동안 기본 키 메타데이터를 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="91ca7-173">Primary key metadata cannot be changed while a spatial index is defined on a table.</span></span>  
  
 <span data-ttu-id="91ca7-174">공간 인덱스는 인덱싱된 뷰에 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="91ca7-174">Spatial indexes cannot be specified on indexed views.</span></span>  
  
### <a name="multiple-spatial-index-restrictions"></a><span data-ttu-id="91ca7-175">여러 공간 인덱스 제한 사항</span><span class="sxs-lookup"><span data-stu-id="91ca7-175">Multiple Spatial Index Restrictions</span></span>  
 <span data-ttu-id="91ca7-176">지원되는 테이블의 공간 열에 공간 인덱스를 249개까지 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="91ca7-176">You can create up to 249 spatial indexes on any of the spatial columns in a supported table.</span></span> <span data-ttu-id="91ca7-177">예를 들면 동일한 공간 열에 공간 인덱스를 한 개 이상 만드는 것이 하나의 열에 있는 서로 다른 공간 분할 매개 변수를 인덱싱하는 데 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="91ca7-177">Creating more than one spatial index on the same spatial column can be useful, for example, to index different tessellation parameters in a single column.</span></span>  
  
 <span data-ttu-id="91ca7-178">공간 인덱스는 한 번에 하나씩만 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="91ca7-178">You can create only one spatial index at a time.</span></span>  
  
### <a name="spatial-indexes-and-process-parallelism"></a><span data-ttu-id="91ca7-179">공간 인덱스 및 프로세스 병렬 처리</span><span class="sxs-lookup"><span data-stu-id="91ca7-179">Spatial Indexes and Process Parallelism</span></span>  
 <span data-ttu-id="91ca7-180">인덱스 작성 작업은 사용 가능한 프로세스 병렬 처리를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="91ca7-180">An index build can use available process parallelism.</span></span>  
  
### <a name="version-restrictions"></a><span data-ttu-id="91ca7-181">버전 제한 사항</span><span class="sxs-lookup"><span data-stu-id="91ca7-181">Version Restrictions</span></span>  
 <span data-ttu-id="91ca7-182">[!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] 에 도입된 공간 분할(tessellation)은 [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] 또는 [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]로 복제할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="91ca7-182">Spatial tessellations introduced in [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] cannot be replicated to [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] or [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)].</span></span> <span data-ttu-id="91ca7-183">[!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] 또는 [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] 데이터베이스와의 호환성이 요구되는 경우 공간 인덱스에는 [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] 또는 [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] 공간 분할을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="91ca7-183">You must use [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] or [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] spatial tessellations for spatial indexes when backward compatibility with [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] or [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] databases is a requirement.</span></span>  
  
  
## <a name="see-also"></a><span data-ttu-id="91ca7-184">참고 항목</span><span class="sxs-lookup"><span data-stu-id="91ca7-184">See Also</span></span>  
 [<span data-ttu-id="91ca7-185">공간 인덱스 개요</span><span class="sxs-lookup"><span data-stu-id="91ca7-185">Spatial Indexes Overview</span></span>](spatial-indexes-overview.md)  
  
  
