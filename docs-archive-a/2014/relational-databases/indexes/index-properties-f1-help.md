---
title: 인덱스 속성 F1 도움말 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
f1_keywords:
- sql12.swb.indexproperties.storage.f1
- sql12.swb.indexproperties.columns.f1
- sql12.swb.indexproperties.partitions.f1
- sql12.swb.indexproperties.general.f1
- sql12.swb.indexproperties.filter.f1
- sql12.swb.indexproperties.options.f1
- sql12.swb.indexproperties.spatial.f1
ms.assetid: 45efd81a-3796-4b04-b0cc-f3deec94c733
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 390a63d21dc72e052017f2d30b061d71de863bc1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742043"
---
# <a name="index-properties-f1-help"></a><span data-ttu-id="07a82-102">인덱스 속성 F1 도움말</span><span class="sxs-lookup"><span data-stu-id="07a82-102">Index Properties F1 Help</span></span>
  <span data-ttu-id="07a82-103">이 항목의 섹션에서는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 대화 상자를 사용하여 이용할 수 있는 다양한 인덱스 속성을 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="07a82-103">The sections in this topic refer to various index properties that are available by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] dialogs.</span></span>  
  
 <span data-ttu-id="07a82-104">**항목 내용:**</span><span class="sxs-lookup"><span data-stu-id="07a82-104">**In This Topic:**</span></span>  
  
 [<span data-ttu-id="07a82-105">인덱스 속성 일반 페이지</span><span class="sxs-lookup"><span data-stu-id="07a82-105">Index Properties General Page</span></span>](#General)  
  
 [<span data-ttu-id="07a82-106">(인덱스) 열 선택 대화 상자</span><span class="sxs-lookup"><span data-stu-id="07a82-106">Select (Index) Columns Dialog Box</span></span>](#Columns)  
  
 [<span data-ttu-id="07a82-107">인덱스 속성 스토리지 페이지</span><span class="sxs-lookup"><span data-stu-id="07a82-107">Index Properties Storage Page</span></span>](#Storage)  
  
 [<span data-ttu-id="07a82-108">인덱스 속성 공간 페이지</span><span class="sxs-lookup"><span data-stu-id="07a82-108">Index Properties Spatial Page</span></span>](#Spatial)  
  
 [<span data-ttu-id="07a82-109">인덱스 속성 필터 페이지</span><span class="sxs-lookup"><span data-stu-id="07a82-109">Index Properties Filter Page</span></span>](#Filter)  
  
##  <a name="index-properties-general-page"></a><a name="General"></a> <span data-ttu-id="07a82-110">인덱스 속성 일반 페이지</span><span class="sxs-lookup"><span data-stu-id="07a82-110">Index Properties General Page</span></span>  
 <span data-ttu-id="07a82-111">일반 페이지를 사용하여 선택한 테이블 또는 뷰의 인덱스 속성을 확인하거나 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07a82-111">Use the General page to view or modify index properties for the selected table or view.</span></span> <span data-ttu-id="07a82-112">각 페이지의 옵션은 선택하는 인덱스의 유형에 따라 변경될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07a82-112">The options for each page may change based on the type of index selected.</span></span>  
  
 <span data-ttu-id="07a82-113">**테이블 이름**</span><span class="sxs-lookup"><span data-stu-id="07a82-113">**Table name**</span></span>  
 <span data-ttu-id="07a82-114">인덱스가 생성된 테이블 또는 뷰의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="07a82-114">Displays the name of the table or view that the index was created on.</span></span> <span data-ttu-id="07a82-115">이 필드는 읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="07a82-115">This field is read-only.</span></span> <span data-ttu-id="07a82-116">다른 테이블을 선택하려면 인덱스 속성 페이지를 닫고 올바른 테이블을 선택한 다음 인덱스 속성 페이지를 다시 엽니다.</span><span class="sxs-lookup"><span data-stu-id="07a82-116">To select a different table, close the Index Properties page, select the correct table, and then open the Index Properties page again.</span></span>  
  
 <span data-ttu-id="07a82-117">공간 인덱스는 인덱싱된 뷰에 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="07a82-117">Spatial indexes cannot be specified on indexed views.</span></span> <span data-ttu-id="07a82-118">공간 인덱스는 기본 키가 있는 테이블에 대해서만 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07a82-118">Spatial indexes can be defined only for a table that has a primary key.</span></span> <span data-ttu-id="07a82-119">테이블의 최대 기본 키 열 수는 15개입니다.</span><span class="sxs-lookup"><span data-stu-id="07a82-119">The maximum number of primary key columns on the table is 15.</span></span> <span data-ttu-id="07a82-120">기본 키 열의 결합된 행별 크기는 최대 895바이트로 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="07a82-120">The combined per-row size of the primary-key columns is limited to a maximum of 895 bytes.</span></span>  
  
 <span data-ttu-id="07a82-121">**인덱스 이름**</span><span class="sxs-lookup"><span data-stu-id="07a82-121">**Index name**</span></span>  
 <span data-ttu-id="07a82-122">인덱스 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="07a82-122">Displays the name of the index.</span></span> <span data-ttu-id="07a82-123">기존 인덱스의 경우 이 필드는 읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="07a82-123">This field is read-only for an existing index.</span></span> <span data-ttu-id="07a82-124">새 인덱스를 만드는 중이면 인덱스 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="07a82-124">When creating a new index, type the name of the index.</span></span>  
  
 <span data-ttu-id="07a82-125">**인덱스 유형**</span><span class="sxs-lookup"><span data-stu-id="07a82-125">**Index type**</span></span>  
 <span data-ttu-id="07a82-126">인덱스의 유형을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="07a82-126">Indicates the type of index.</span></span> <span data-ttu-id="07a82-127">새 인덱스의 경우 대화 상자를 열 때 선택한 인덱스의 유형을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="07a82-127">For new indexes, indicates the type of index selected when opening the dialog box.</span></span> <span data-ttu-id="07a82-128">인덱스는 **클러스터형**, **비클러스터형**, **기본 XML**, **보조 XML**, **공간**, **클러스터형 Columnstore** 또는 **비클러스터형 Columnstore**일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07a82-128">Indexes can be: **Clustered**, **Nonclustered**, **Primary XML**, **Secondary XML**, **Spatial**, **Clustered columnstore**, or **Nonclustered Columnstore**.</span></span>  
  
 <span data-ttu-id="07a82-129">**참고** 각 테이블에 대해 클러스터형 인덱스는 하나만 허용됩니다.</span><span class="sxs-lookup"><span data-stu-id="07a82-129">**Note** Only one clustered index is allowed for each table.</span></span> <span data-ttu-id="07a82-130">각 테이블에 대해 xVelocity 메모리 액세스에 최적화된 columnstore 인덱스는 하나만 허용됩니다.</span><span class="sxs-lookup"><span data-stu-id="07a82-130">Only one xVelocity memory optimized columnstore index is allowed for each table.</span></span>  
  
 <span data-ttu-id="07a82-131">**고유**</span><span class="sxs-lookup"><span data-stu-id="07a82-131">**Unique**</span></span>  
 <span data-ttu-id="07a82-132">이 확인란을 선택하면 인덱스가 고유해집니다.</span><span class="sxs-lookup"><span data-stu-id="07a82-132">Selecting this check box makes the index unique.</span></span> <span data-ttu-id="07a82-133">두 행의 인덱스 값이 같을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="07a82-133">No two rows are permitted to have the same index value.</span></span> <span data-ttu-id="07a82-134">이 확인란은 기본적으로 선택되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="07a82-134">By default, this check box is cleared.</span></span> <span data-ttu-id="07a82-135">기존 인덱스를 수정할 때 두 행의 값이 같으면 인덱스 만들기에 실패하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="07a82-135">When modifying an existing index, index creation will fail if two rows have the same value.</span></span> <span data-ttu-id="07a82-136">Null이 허용되는 열에서 고유한 인덱스는 하나의 Null 값을 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="07a82-136">For columns where NULL is permitted, a unique index permits one NULL value.</span></span>  
  
 <span data-ttu-id="07a82-137">**인덱스 유형** 필드에서 **공간** 을 선택하면 **고유** 확인란이 흐리게 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="07a82-137">If you select **Spatial** in the **Index type** field, the **Unique** check box is dimmed.</span></span>  
  
 <span data-ttu-id="07a82-138">**인덱스 키 열**</span><span class="sxs-lookup"><span data-stu-id="07a82-138">**Index key columns**</span></span>  
 <span data-ttu-id="07a82-139">**인덱스 키 열** 표에 원하는 열을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="07a82-139">Add the desired columns to the **Index key columns** grid.</span></span> <span data-ttu-id="07a82-140">여러 열을 추가할 때는 원하는 순서대로 열을 나열해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="07a82-140">When more than one column is added, the columns must be listed in the order desired.</span></span> <span data-ttu-id="07a82-141">인덱스의 열 순서는 인덱스 성능에 큰 영향을 미칠 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07a82-141">The column order in an index can have a great impact on the index performance.</span></span>  
  
 <span data-ttu-id="07a82-142">16개 이하의 열만 단일 복합 인덱스에 참여할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07a82-142">No more than 16 columns can participate in a single composite index.</span></span> <span data-ttu-id="07a82-143">열이 17개 이상인 경우에는 이 항목의 마지막 부분에 있는 "포괄 열"을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="07a82-143">For greater than 16 columns, see included columns at the end of this topic.</span></span>  
  
 <span data-ttu-id="07a82-144">공간 인덱스는 공간 데이터 형식이 포함되어 있는 단일 열( *공간 열*)에 대해서만 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07a82-144">A spatial index can be defined only on a single column that contains a spatial data type (a *spatial column*).</span></span>  
  
 <span data-ttu-id="07a82-145">**이름**</span><span class="sxs-lookup"><span data-stu-id="07a82-145">**Name**</span></span>  
 <span data-ttu-id="07a82-146">인덱스 키에 참여하는 열 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="07a82-146">Displays the name of the column that participates in the index key.</span></span>  
  
 <span data-ttu-id="07a82-147">**정렬 순서**</span><span class="sxs-lookup"><span data-stu-id="07a82-147">**Sort Order**</span></span>  
 <span data-ttu-id="07a82-148">선택한 인덱스 열의 정렬 방향( **오름차순** 또는 **내림차순**)을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="07a82-148">Specifies the sort direction of the selected index column, either **Ascending** or **Descending**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="07a82-149">인덱스 유형이 **기본 XML** 또는 **공간**인 경우에는 테이블에 이 열이 나타나지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="07a82-149">If the index type is **Primary XML** or **Spatial**, this column does not appear in the table.</span></span>  
  
 <span data-ttu-id="07a82-150">**데이터 형식**</span><span class="sxs-lookup"><span data-stu-id="07a82-150">**Data Type**</span></span>  
 <span data-ttu-id="07a82-151">데이터 형식 정보를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="07a82-151">Displays the data type information.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="07a82-152">테이블 열이 계산 열인 경우에는 **데이터 형식** 에 "계산 열"이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="07a82-152">If the table column is a computed column, **Data type** displays "computed column."</span></span>  
  
 <span data-ttu-id="07a82-153">**크기**</span><span class="sxs-lookup"><span data-stu-id="07a82-153">**Size**</span></span>  
 <span data-ttu-id="07a82-154">열 데이터 형식을 저장하는 데 필요한 최대 바이트 수를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="07a82-154">Displays the maximum number of bytes required to store the column data type.</span></span> <span data-ttu-id="07a82-155">공간 또는 XML 열의 경우에는 0이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="07a82-155">Displays zero (0) for a spatial or XML column.</span></span>  
  
 <span data-ttu-id="07a82-156">**ID**</span><span class="sxs-lookup"><span data-stu-id="07a82-156">**Identity**</span></span>  
 <span data-ttu-id="07a82-157">인덱스 키에 참여하는 열이 ID 열인지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="07a82-157">Displays whether the column participating in the index key is an identity column.</span></span>  
  
 <span data-ttu-id="07a82-158">**NULL 허용**</span><span class="sxs-lookup"><span data-stu-id="07a82-158">**Allow NULLs**</span></span>  
 <span data-ttu-id="07a82-159">인덱스 키에 참여하는 열이 테이블 또는 뷰 열에 NULL 값을 저장하도록 허용할지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="07a82-159">Displays whether the column participating in the index key allows NULL values to be stored in the table or view column.</span></span>  
  
 <span data-ttu-id="07a82-160">**추가**</span><span class="sxs-lookup"><span data-stu-id="07a82-160">**Add**</span></span>  
 <span data-ttu-id="07a82-161">인덱스 키에 열을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="07a82-161">Adds a column to the index key.</span></span> <span data-ttu-id="07a82-162">**추가**를 클릭하면 나타나는 *\<table name>* **에서 열 선택** 대화 상자에서 테이블 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="07a82-162">Select table columns from the **Select Columns from** *\<table name>* dialog box that appears when you click **Add**.</span></span> <span data-ttu-id="07a82-163">공간 인덱스의 경우 열을 하나 선택하면 이 단추가 흐리게 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="07a82-163">For a spatial index, after you select one column, this button is dimmed.</span></span>  
  
 <span data-ttu-id="07a82-164">**제거**</span><span class="sxs-lookup"><span data-stu-id="07a82-164">**Remove**</span></span>  
 <span data-ttu-id="07a82-165">선택된 열을 인덱스 키에 참여하는 열에서 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="07a82-165">Removes the selected column from participation in the index key.</span></span>  
  
 <span data-ttu-id="07a82-166">**위로 이동**</span><span class="sxs-lookup"><span data-stu-id="07a82-166">**Move Up**</span></span>  
 <span data-ttu-id="07a82-167">인덱스 키 표에서 선택된 열을 위로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="07a82-167">Moves the selected column up in the index key grid.</span></span>  
  
 <span data-ttu-id="07a82-168">**아래로 이동**</span><span class="sxs-lookup"><span data-stu-id="07a82-168">**Move Down**</span></span>  
 <span data-ttu-id="07a82-169">인덱스 키 표에서 선택된 열을 아래로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="07a82-169">Moves the selected column down in the index key grid.</span></span>  
  
 <span data-ttu-id="07a82-170">**Columnstore 열**</span><span class="sxs-lookup"><span data-stu-id="07a82-170">**Columnstore columns**</span></span>  
 <span data-ttu-id="07a82-171">**추가** 를 클릭하여 columnstore 인덱스의 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="07a82-171">Click **Add** to select columns for the columnstore index.</span></span> <span data-ttu-id="07a82-172">columnstore 인덱스에 대한 제한 사항은 [CREATE COLUMNSTORE INDEX&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-columnstore-index-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="07a82-172">For limitations on a columnstore index, see [CREATE COLUMNSTORE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-columnstore-index-transact-sql).</span></span>  
  
 <span data-ttu-id="07a82-173">**포괄 열**</span><span class="sxs-lookup"><span data-stu-id="07a82-173">**Included columns**</span></span>  
 <span data-ttu-id="07a82-174">비클러스터형 인덱스에 키가 아닌 열을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="07a82-174">Include nonkey columns in the nonclustered index.</span></span> <span data-ttu-id="07a82-175">이 옵션을 사용하면 비클러스터형 인덱스의 리프 수준에 열을 추가할 때 키가 아닌 열로 추가하여 인덱스 키의 전체 크기 및 인덱스 키에 포함되는 최대 열 수에 대한 제한을 무시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07a82-175">This option allows you to bypass the current index limits on the total size of an index key and the maximum number of columns participating in an index key by adding columns as nonkey columns in the leaf level of the nonclustered index.</span></span> <span data-ttu-id="07a82-176">자세한 내용은 [포괄 열을 사용하여 인덱스 만들기](create-indexes-with-included-columns.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="07a82-176">For more information, see [Create Indexes with Included Columns](create-indexes-with-included-columns.md)</span></span>  
  
##  <a name="select-index-columns-dialog-box"></a><a name="Columns"></a> <span data-ttu-id="07a82-177">(인덱스) 열 선택 대화 상자</span><span class="sxs-lookup"><span data-stu-id="07a82-177">Select (Index) Columns Dialog Box</span></span>  
 <span data-ttu-id="07a82-178">인덱스를 만들거나 수정할 때 이 페이지를 사용하여 **인덱스 속성 일반** 페이지에 열을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07a82-178">Use this page to add columns to the **Index Properties General** page when creating or modifying an index.</span></span>  
  
 <span data-ttu-id="07a82-179">**확인란**</span><span class="sxs-lookup"><span data-stu-id="07a82-179">**Check box**</span></span>  
 <span data-ttu-id="07a82-180">열을 추가하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="07a82-180">Select to add columns.</span></span>  
  
 <span data-ttu-id="07a82-181">**이름**</span><span class="sxs-lookup"><span data-stu-id="07a82-181">**Name**</span></span>  
 <span data-ttu-id="07a82-182">열의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="07a82-182">Name of the column.</span></span>  
  
 <span data-ttu-id="07a82-183">**데이터 형식**</span><span class="sxs-lookup"><span data-stu-id="07a82-183">**Data Type**</span></span>  
 <span data-ttu-id="07a82-184">열의 데이터 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="07a82-184">The data type of the column.</span></span>  
  
 <span data-ttu-id="07a82-185">**바이트**</span><span class="sxs-lookup"><span data-stu-id="07a82-185">**Bytes**</span></span>  
 <span data-ttu-id="07a82-186">열의 크기를 바이트 단위로 표시한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="07a82-186">The size of the column in bytes.</span></span>  
  
 <span data-ttu-id="07a82-187">**ID**</span><span class="sxs-lookup"><span data-stu-id="07a82-187">**Identity**</span></span>  
 <span data-ttu-id="07a82-188">ID 열인 경우 **예** 를 표시하고 ID 열이 아닌 경우 **아니요** 를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="07a82-188">Displays **Yes** for identity columns, and **No** when the column is not an identity column.</span></span>  
  
 <span data-ttu-id="07a82-189">**Null 허용**</span><span class="sxs-lookup"><span data-stu-id="07a82-189">**Allow Nulls**</span></span>  
 <span data-ttu-id="07a82-190">테이블 정의에 따라 열에 Null 값이 허용되는 경우 **예** 를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="07a82-190">Displays **Yes** when the table definition allows null values for the column.</span></span> <span data-ttu-id="07a82-191">테이블 정의에 따라 열에 Null 값이 허용되지 않는 경우 **아니요** 를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="07a82-191">Displays **No** when the table definition does not allow nulls for the column.</span></span>  
  
##  <a name="storage-page-options"></a><a name="Storage"></a> <span data-ttu-id="07a82-192">스토리지 페이지 옵션</span><span class="sxs-lookup"><span data-stu-id="07a82-192">Storage Page Options</span></span>  
 <span data-ttu-id="07a82-193">이 페이지를 사용하여 선택한 인덱스의 파일 그룹 또는 파티션 구성표 속성을 확인하거나 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07a82-193">Use this page to view or modify filegroup or partition scheme properties for the selected index.</span></span> <span data-ttu-id="07a82-194">인덱스 유형과 관련된 옵션만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="07a82-194">Only shows options related to the type of index.</span></span>  
  
 <span data-ttu-id="07a82-195">**파일 그룹**</span><span class="sxs-lookup"><span data-stu-id="07a82-195">**Filegroup**</span></span>  
 <span data-ttu-id="07a82-196">지정한 파일 그룹에 인덱스를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="07a82-196">Stores the index in the specified filegroup.</span></span> <span data-ttu-id="07a82-197">목록에는 표준(행) 파일 그룹만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="07a82-197">The list only displays standard (row) filegroups.</span></span> <span data-ttu-id="07a82-198">목록에서는 기본적으로 데이터베이스의 PRIMARY 파일 그룹이 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="07a82-198">The default list selection is the PRIMARY filegroup of the database.</span></span> <span data-ttu-id="07a82-199">자세한 내용은 [Database Files and Filegroups](../databases/database-files-and-filegroups.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="07a82-199">For more information, see [Database Files and Filegroups](../databases/database-files-and-filegroups.md).</span></span>  
  
 <span data-ttu-id="07a82-200">**Filestream 파일 그룹**</span><span class="sxs-lookup"><span data-stu-id="07a82-200">**Filestream filegroup**</span></span>  
 <span data-ttu-id="07a82-201">FILESTREAM 데이터의 파일 그룹을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="07a82-201">Specifies the filegroup for FILESTREAM data.</span></span> <span data-ttu-id="07a82-202">이 목록에는 FILESTREAM 파일 그룹만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="07a82-202">This list displays only FILESTREAM filegroups.</span></span> <span data-ttu-id="07a82-203">목록에서는 기본적으로 PRIMARY FILESTREAM 파일 그룹이 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="07a82-203">The default list selection is the PRIMARY FILESTREAM filegroup.</span></span> <span data-ttu-id="07a82-204">자세한 내용은 [FILESTREAM&#40;SQL Server&#41;](../blob/filestream-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="07a82-204">For more information, see [FILESTREAM &#40;SQL Server&#41;](../blob/filestream-sql-server.md).</span></span>  
  
 <span data-ttu-id="07a82-205">**파티션 구성표**</span><span class="sxs-lookup"><span data-stu-id="07a82-205">**Partition scheme**</span></span>  
 <span data-ttu-id="07a82-206">파티션 구성표에 인덱스를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="07a82-206">Stores the index in a partition scheme.</span></span> <span data-ttu-id="07a82-207">**파티션 구성표** 를 클릭하면 아래의 표가 활성화됩니다.</span><span class="sxs-lookup"><span data-stu-id="07a82-207">Clicking **Partition Scheme** enables the grid below.</span></span> <span data-ttu-id="07a82-208">목록에서는 기본적으로 테이블 데이터를 저장하는 데 사용되는 파티션 구성표가 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="07a82-208">The default list selection is the partition scheme that is used for storing the table data.</span></span> <span data-ttu-id="07a82-209">목록에서 다른 파티션 구성표를 선택하면 표의 정보가 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="07a82-209">When you select a different partition scheme in the list, the information in the grid is updated.</span></span> <span data-ttu-id="07a82-210">자세한 내용은 [Partitioned Tables and Indexes](../partitions/partitioned-tables-and-indexes.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="07a82-210">For more information, see [Partitioned Tables and Indexes](../partitions/partitioned-tables-and-indexes.md).</span></span>  
  
 <span data-ttu-id="07a82-211">데이터베이스에 파티션 구성표가 없으면 파티션 구성표 옵션을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="07a82-211">The partition scheme option is unavailable if there are no partition schemes in the database.</span></span>  
  
 <span data-ttu-id="07a82-212">**Filestream 파티션 구성표**</span><span class="sxs-lookup"><span data-stu-id="07a82-212">**Filestream partition scheme**</span></span>  
 <span data-ttu-id="07a82-213">FILESTREAM 데이터의 파티션 구성표를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="07a82-213">Specifies the partition scheme for FILESTREAM data.</span></span> <span data-ttu-id="07a82-214">이 파티션 구성표는 **파티션 구성표** 옵션에서 지정한 구성표와 대칭이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="07a82-214">The partition scheme must be symmetric with the scheme that is specified in the **Partition scheme** option.</span></span>  
  
 <span data-ttu-id="07a82-215">테이블이 분할되지 않은 경우 이 필드가 비어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07a82-215">If the table is not partitioned, the field is blank.</span></span>  
  
 <span data-ttu-id="07a82-216">**파티션 구성표 매개 변수**</span><span class="sxs-lookup"><span data-stu-id="07a82-216">**Partition Scheme Parameter**</span></span>  
 <span data-ttu-id="07a82-217">파티션 구성표에 포함되는 열의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="07a82-217">Displays the name of the column that participates in the partition scheme.</span></span>  
  
 <span data-ttu-id="07a82-218">**테이블 열**</span><span class="sxs-lookup"><span data-stu-id="07a82-218">**Table Column**</span></span>  
 <span data-ttu-id="07a82-219">파티션 구성표에 매핑할 테이블 또는 뷰를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="07a82-219">Select the table or view to map to the partition scheme.</span></span>  
  
 <span data-ttu-id="07a82-220">**열 데이터 형식**</span><span class="sxs-lookup"><span data-stu-id="07a82-220">**Column Data Type**</span></span>  
 <span data-ttu-id="07a82-221">열의 데이터 형식을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="07a82-221">Displays data type information about the column.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="07a82-222">테이블 열이 계산 열이면 **열 데이터 형식** 에 "계산 열"이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="07a82-222">If the table column is a computed column, **Column Data Type** displays "computed column."</span></span>  
  
 <span data-ttu-id="07a82-223">**인덱스를 이동하는 동안 DML 문의 온라인 처리 허용**</span><span class="sxs-lookup"><span data-stu-id="07a82-223">**Allow online processing of DML statements while moving the index**</span></span>  
 <span data-ttu-id="07a82-224">이 옵션을 사용하면 사용자는 인덱스 작업 중에 기본 테이블이나 클러스터형 인덱스 데이터 및 연관된 모든 비클러스터형 인덱스에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07a82-224">Allows users to access the underlying table or clustered index data and any associated nonclustered indexes during the index operation.</span></span> <span data-ttu-id="07a82-225">자세한 내용은 [Perform Index Operations Online](perform-index-operations-online.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="07a82-225">For more information, see [Perform Index Operations Online](perform-index-operations-online.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="07a82-226">이 옵션은 XML 인덱스에 대해서는 사용할 수 없으며 인덱스가 비활성화된 클러스터형 인덱스인 경우에도 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="07a82-226">This option is not available for XML indexes, or if the index is a disabled clustered index.</span></span>  
  
 <span data-ttu-id="07a82-227">**최대 병렬 처리 수준 설정**</span><span class="sxs-lookup"><span data-stu-id="07a82-227">**Set maximum degree of parallelism**</span></span>  
 <span data-ttu-id="07a82-228">병렬 계획 실행 중 사용할 프로세서 수를 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="07a82-228">Limits the number of processors to use during parallel plan execution.</span></span> <span data-ttu-id="07a82-229">기본값인 0으로 설정하면 사용 가능한 실제 CPU 수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="07a82-229">The default value, 0, uses the actual number of available CPUs.</span></span> <span data-ttu-id="07a82-230">값을 1로 설정하면 병렬 계획이 생성되지 않습니다. 값을 1보다 큰 값으로 설정하면 단일 쿼리 실행에서 사용하는 최대 프로세서 수가 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="07a82-230">Setting the value to 1 suppresses parallel plan generation; setting the value to a number greater than 1 restricts the maximum number of processors used by a single query execution.</span></span> <span data-ttu-id="07a82-231">이 옵션은 대화 상자가 **다시 작성** 또는 **다시 만들기** 상태에 있을 때만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07a82-231">This option only becomes available if the dialog box is in the **Rebuild** or **Recreate** state.</span></span> <span data-ttu-id="07a82-232">자세한 내용은 [최적 성능을 위해 최대 병렬 처리 수준 옵션 설정](../policy-based-management/set-the-max-degree-of-parallelism-option-for-optimal-performance.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="07a82-232">For more information, see [Set the Max Degree of Parallelism Option for Optimal Performance](../policy-based-management/set-the-max-degree-of-parallelism-option-for-optimal-performance.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="07a82-233">사용 가능한 CPU 수보다 더 큰 수를 지정하면 사용 가능한 실제 CPU 수가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="07a82-233">If a value greater than the number of available CPUs is specified, the actual number of available CPUs is used.</span></span>  
  
##  <a name="spatial-page-index-options"></a><a name="Spatial"></a> <span data-ttu-id="07a82-234">공간 페이지 인덱스 옵션</span><span class="sxs-lookup"><span data-stu-id="07a82-234">Spatial Page Index Options</span></span>  
 <span data-ttu-id="07a82-235">**공간** 페이지를 사용하여 공간 속성의 값을 확인하거나 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07a82-235">Use the **Spatial** page to view or specify the values of the spatial properties.</span></span> <span data-ttu-id="07a82-236">자세한 내용은 [공간 데이터&#40;SQL Server&#41;](../spatial/spatial-data-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="07a82-236">For more information, see [Spatial Data &#40;SQL Server&#41;](../spatial/spatial-data-sql-server.md).</span></span>  
  
### <a name="bounding-box"></a><span data-ttu-id="07a82-237">경계 상자</span><span class="sxs-lookup"><span data-stu-id="07a82-237">Bounding Box</span></span>  
 <span data-ttu-id="07a82-238">*경계 상자* 는 기하 평면에서 최상위 표의 경계입니다.</span><span class="sxs-lookup"><span data-stu-id="07a82-238">The *bounding box* is the perimeter of the top-level grid of a geometric plane.</span></span> <span data-ttu-id="07a82-239">경계 상자 매개 변수는 기하 도형 표 공간 분할에서만 존재합니다.</span><span class="sxs-lookup"><span data-stu-id="07a82-239">The bounding-box parameters exist only in the geometry grid tessellation.</span></span> <span data-ttu-id="07a82-240">이러한 매개 변수는 **공간 분할(tessellation) 구성표** 가 **지리 표**인 경우 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="07a82-240">These parameters are unavailable if the **Tessellation Scheme** is **Geography grid**.</span></span>  
  
 <span data-ttu-id="07a82-241">패널은 경계 상자의 **( *`X-min`* , *`Y-min`* )** 및 **( *`X-max`* , *`Y-max`* )** 좌표를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="07a82-241">The panel displays the **(*`X-min`*,*`Y-min`*)** and **(*`X-max`*,*`Y-max`*)** coordinates of the bounding box.</span></span> <span data-ttu-id="07a82-242">기본 좌표 값은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="07a82-242">There are no default coordinate values.</span></span> <span data-ttu-id="07a82-243">따라서 `geometry` 유형 열에 새 공간 인덱스를 만드는 경우 좌표 값을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="07a82-243">Therefore, when you are creating a new spatial index on a `geometry` type column, you must specify the coordinate values.</span></span>  
  
 `X-min`  
 <span data-ttu-id="07a82-244">경계 상자의 왼쪽 아래 모퉁이의 X 좌표입니다.</span><span class="sxs-lookup"><span data-stu-id="07a82-244">The X-coordinate of the lower-left corner of the bounding box.</span></span>  
  
 `Y-min`  
 <span data-ttu-id="07a82-245">경계 상자의 왼쪽 아래 모퉁이의 Y 좌표입니다.</span><span class="sxs-lookup"><span data-stu-id="07a82-245">The Y-coordinate of the lower-left corner of the bounding box.</span></span>  
  
 `X-max`  
 <span data-ttu-id="07a82-246">경계 상자의 오른쪽 위 모퉁이의 X 좌표입니다.</span><span class="sxs-lookup"><span data-stu-id="07a82-246">The X-coordinate of the upper-right corner of the bounding box.</span></span>  
  
 `Y-max`  
 <span data-ttu-id="07a82-247">경계 상자의 오른쪽 위 모퉁이의 Y 좌표입니다.</span><span class="sxs-lookup"><span data-stu-id="07a82-247">The Y-coordinate of upper-right corner of the bounding box.</span></span>  
  
### <a name="general"></a><span data-ttu-id="07a82-248">일반</span><span class="sxs-lookup"><span data-stu-id="07a82-248">General</span></span>  
 <span data-ttu-id="07a82-249">**공간 분할(tessellation) 구성표**</span><span class="sxs-lookup"><span data-stu-id="07a82-249">**Tessellation Scheme**</span></span>  
 <span data-ttu-id="07a82-250">인덱스의 공간 분할(tessellation) 구성표를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="07a82-250">Indicates the tessellation scheme of the index.</span></span> <span data-ttu-id="07a82-251">지원되는 공간 분할(tessellation) 구성표는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="07a82-251">The supported tessellation schemes are as follows.</span></span>  
  
 <span data-ttu-id="07a82-252">**기하 도형 표**</span><span class="sxs-lookup"><span data-stu-id="07a82-252">**Geometry grid**</span></span>  
 <span data-ttu-id="07a82-253">`geometry` 데이터 형식의 열에 적용되는 기하 도형 표 공간 분할(tessellation) 구성표를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="07a82-253">Specifies the geometry grid tessellation scheme, which applies to a column of the `geometry` data type.</span></span>  
  
 <span data-ttu-id="07a82-254">**기하 도형 자동 표**</span><span class="sxs-lookup"><span data-stu-id="07a82-254">**Geometry Auto grid**</span></span>  
 <span data-ttu-id="07a82-255">이 옵션은 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 에서 데이터베이스 호환성 수준이 110 이상으로 설정된 경우에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07a82-255">This option is enabled for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] when database compatibility level is set to 110 or higher.</span></span>  
  
 <span data-ttu-id="07a82-256">**지리 표**</span><span class="sxs-lookup"><span data-stu-id="07a82-256">**Geography grid**</span></span>  
 <span data-ttu-id="07a82-257">**geography** 데이터 형식의 열에 적용되는 지리 표 공간 분할(tessellation) 구성표를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="07a82-257">Specifies the geography grid tessellation scheme, which applies to a column of the **geography** data type.</span></span>  
  
 <span data-ttu-id="07a82-258">**지리 자동 표**</span><span class="sxs-lookup"><span data-stu-id="07a82-258">**Geography Auto grid**</span></span>  
 <span data-ttu-id="07a82-259">이 옵션은 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 에서 데이터베이스 호환성 수준이 110 이상으로 설정된 경우에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07a82-259">This option is enabled for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] when database compatibility level is set to 110 or higher.</span></span>  
  
 <span data-ttu-id="07a82-260">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에서 공간 분할을 구현하는 방법은 [공간 데이터&#40;SQL Server&#41;](../spatial/spatial-data-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="07a82-260">For information about how [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] implements tessellation, see [Spatial Data &#40;SQL Server&#41;](../spatial/spatial-data-sql-server.md).</span></span>  
  
 <span data-ttu-id="07a82-261">**개체당 셀 수**</span><span class="sxs-lookup"><span data-stu-id="07a82-261">**Cells Per Object**</span></span>  
 <span data-ttu-id="07a82-262">인덱스의 단일 공간 개체에 사용할 수 있는 개체당 공간 분할(tessellation) 셀 수를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="07a82-262">Indicates the number of tessellation cells-per-object that can be used for a single spatial object in the index.</span></span> <span data-ttu-id="07a82-263">이 수는 1과 8192(포함) 사이의 정수일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07a82-263">This number can be any integer between 1 and 8192, inclusive.</span></span> <span data-ttu-id="07a82-264">기본값은 16이며, 이전 버전의 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 에서 데이터베이스 호환성 수준이 110 이상으로 설정된 경우에는 8입니다.</span><span class="sxs-lookup"><span data-stu-id="07a82-264">The default is 16, and 8 for earlier versions of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] when database compatibility level is set to 110 or higher.</span></span>  
  
 <span data-ttu-id="07a82-265">최상위 수준에서, 개체가 *n*으로 지정된 셀보다 많은 셀을 포함하는 경우 인덱싱 시 전체 최상위 수준 공간 분할을 제공하는 데 필요한 만큼의 셀 수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="07a82-265">At the top level, if an object covers more cells than specified by *n*, the indexing uses as many cells as necessary to provide a complete top-level tessellation.</span></span> <span data-ttu-id="07a82-266">이 경우 개체는 지정된 셀 수보다 많은 수의 셀을 받을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07a82-266">In such cases, an object might receive more than the specified number of cells.</span></span> <span data-ttu-id="07a82-267">여기서 최대 수는 최상위 표에 의해 생성된 셀의 개수로, **수준 1** 밀도에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="07a82-267">In this case, the maximum number is the number of cells generated by the top-level grid, which depends on the **Level 1** density.</span></span>  
  
### <a name="grids"></a><span data-ttu-id="07a82-268">표</span><span class="sxs-lookup"><span data-stu-id="07a82-268">Grids</span></span>  
 <span data-ttu-id="07a82-269">이 패널에는 각 공간 분할(tessellation) 구성표 수준에서 표의 밀도가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="07a82-269">This panel shows the density of the grid at each level of the tessellation scheme.</span></span> <span data-ttu-id="07a82-270">밀도는 **낮음**, **보통**또는 **높음**으로 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="07a82-270">Density is specified as **Low**, **Medium**, or **High**.</span></span> <span data-ttu-id="07a82-271">기본값은 **보통**입니다.</span><span class="sxs-lookup"><span data-stu-id="07a82-271">The default is **Medium**.</span></span> <span data-ttu-id="07a82-272">**낮음** 은 4x4 표(16개의 셀), **보통** 은 8x8 표(64개의 셀), **높음** 은 16x16 표(256개의 셀)를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="07a82-272">**Low** represents a 4x4 grid (16 cells), **Medium** represents an 8x8 grid (64 cells), and **High** represents a 16x16 grid (256 cells).</span></span> <span data-ttu-id="07a82-273">**기하 도형 자동 표** 또는 **지리 자동 표** 공간 분할 옵션을 선택한 경우에는 이러한 옵션을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="07a82-273">These options are not available when the **Geometry Auto grid** or **Geography Auto grid** tessellation options are chosen.</span></span>  
  
 <span data-ttu-id="07a82-274">**수준 1**</span><span class="sxs-lookup"><span data-stu-id="07a82-274">**Level 1**</span></span>  
 <span data-ttu-id="07a82-275">첫째 수준(최상위) 표의 밀도입니다.</span><span class="sxs-lookup"><span data-stu-id="07a82-275">The density of the first-level (top) grid.</span></span>  
  
 <span data-ttu-id="07a82-276">**수준 2**</span><span class="sxs-lookup"><span data-stu-id="07a82-276">**Level 2**</span></span>  
 <span data-ttu-id="07a82-277">둘째 수준 표의 밀도입니다.</span><span class="sxs-lookup"><span data-stu-id="07a82-277">The density of the second-level grid.</span></span>  
  
 <span data-ttu-id="07a82-278">**수준 3**</span><span class="sxs-lookup"><span data-stu-id="07a82-278">**Level 3**</span></span>  
 <span data-ttu-id="07a82-279">셋째 수준 표의 밀도입니다.</span><span class="sxs-lookup"><span data-stu-id="07a82-279">The density of the third-level grid.</span></span>  
  
 <span data-ttu-id="07a82-280">**수준 4**</span><span class="sxs-lookup"><span data-stu-id="07a82-280">**Level 4**</span></span>  
 <span data-ttu-id="07a82-281">넷째 수준 표의 밀도입니다.</span><span class="sxs-lookup"><span data-stu-id="07a82-281">The density of the fourth-level grid.</span></span>  
  
##  <a name="filter-page"></a><a name="Filter"></a> <span data-ttu-id="07a82-282">필터 페이지</span><span class="sxs-lookup"><span data-stu-id="07a82-282">Filter Page</span></span>  
 <span data-ttu-id="07a82-283">이 페이지를 사용하여 필터링된 인덱스에 대한 필터 조건자를 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07a82-283">Use this page to enter the filter predicate for a filtered index.</span></span> <span data-ttu-id="07a82-284">자세한 내용은 [Create Filtered Indexes](create-filtered-indexes.md)을(를) 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="07a82-284">For more information, see [Create Filtered Indexes](create-filtered-indexes.md).</span></span>  
  
 <span data-ttu-id="07a82-285">**필터 식**</span><span class="sxs-lookup"><span data-stu-id="07a82-285">**Filter Expression**</span></span>  
 <span data-ttu-id="07a82-286">필터링된 인덱스에 포함할 데이터 행을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="07a82-286">Defines which data rows to include in the filtered index.</span></span> <span data-ttu-id="07a82-287">예를 들어 `StartDate > '20000101' AND EndDate IS NOT NULL'.`</span><span class="sxs-lookup"><span data-stu-id="07a82-287">For example, `StartDate > '20000101' AND EndDate IS NOT NULL'.`</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07a82-288">참고 항목</span><span class="sxs-lookup"><span data-stu-id="07a82-288">See Also</span></span>  
 <span data-ttu-id="07a82-289">[인덱스 옵션 설정](set-index-options.md) </span><span class="sxs-lookup"><span data-stu-id="07a82-289">[Set Index Options](set-index-options.md) </span></span>  
 <span data-ttu-id="07a82-290">[INDEXPROPERTY&#40;Transact-SQL&#41;](/sql/t-sql/functions/indexproperty-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="07a82-290">[INDEXPROPERTY &#40;Transact-SQL&#41;](/sql/t-sql/functions/indexproperty-transact-sql) </span></span>  
 [<span data-ttu-id="07a82-291">sys.indexes&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="07a82-291">sys.indexes &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-indexes-transact-sql)  
  
  
