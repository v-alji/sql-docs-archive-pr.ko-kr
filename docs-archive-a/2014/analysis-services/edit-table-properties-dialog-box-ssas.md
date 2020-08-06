---
title: 테이블 속성 편집 대화 상자 (SSAS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.edittablepropdb.f1
ms.assetid: 8d913e83-7246-44cc-8fc7-31729023c0d8
author: minewiskan
ms.author: owend
ms.openlocfilehash: 6664d244f5f653610b37bd628abdb2263e015c0b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659706"
---
# <a name="edit-table-properties-dialog-box-ssas"></a><span data-ttu-id="dbcaa-102">테이블 속성 편집 대화 상자(SSAS)</span><span class="sxs-lookup"><span data-stu-id="dbcaa-102">Edit Table Properties Dialog Box (SSAS)</span></span>
  <span data-ttu-id="dbcaa-103">**테이블 속성 편집** 대화 상자에서는 테이블 가져오기 마법사를 사용하여 모델 디자이너로 가져온 테이블의 속성을 보고 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dbcaa-103">The **Edit Table Properties** dialog box enables you to view and modify the properties of tables that are imported into the model designer by using the Table Import Wizard.</span></span> <span data-ttu-id="dbcaa-104">모델 디자이너에서 이 대화 상자를 열려면 가져온 데이터의 테이블을 선택한 다음 **테이블** 메뉴를 클릭하고 **테이블 속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="dbcaa-104">To access this dialog box, in the model designer, select a table, then click the **Table** menu, and then click **Table Properties**.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="dbcaa-105">UI 요소 목록</span><span class="sxs-lookup"><span data-stu-id="dbcaa-105">UI element list</span></span>  
 <span data-ttu-id="dbcaa-106">이 대화 상자의 옵션은 데이터를 가져올 때 목록에서 테이블을 선택하는 방법을 사용했는지 SQL 쿼리를 사용했는지에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="dbcaa-106">The options for this dialog box are different depending on whether you originally imported data by selecting tables from a list or by using a SQL query.</span></span>  
  
## <a name="table-preview-mode"></a><span data-ttu-id="dbcaa-107">테이블 미리 보기 모드</span><span class="sxs-lookup"><span data-stu-id="dbcaa-107">Table Preview Mode</span></span>  
 <span data-ttu-id="dbcaa-108">**테이블 이름**</span><span class="sxs-lookup"><span data-stu-id="dbcaa-108">**Table name**</span></span>  
 <span data-ttu-id="dbcaa-109">모델에 데이터 테이블의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="dbcaa-109">Displays the name of the data table in the model.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="dbcaa-110">여기서 이름을 편집할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="dbcaa-110">You cannot edit the name here.</span></span> <span data-ttu-id="dbcaa-111">그러나 모델 디자이너 아래쪽에 있는 테이블 탭을 마우스 오른쪽 단추로 클릭하면 테이블 이름을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dbcaa-111">However, you can change the name of the table by right-clicking the table tab at the bottom of the model designer.</span></span>  
  
 <span data-ttu-id="dbcaa-112">**연결 이름**</span><span class="sxs-lookup"><span data-stu-id="dbcaa-112">**Connection name**</span></span>  
 <span data-ttu-id="dbcaa-113">현재 사용 중인 연결의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="dbcaa-113">Displays the name of the connection that is currently in use.</span></span>  
  
 <span data-ttu-id="dbcaa-114">**원본 이름**</span><span class="sxs-lookup"><span data-stu-id="dbcaa-114">**Source name**</span></span>  
 <span data-ttu-id="dbcaa-115">가져올 데이터가 포함되어 있는 테이블을 표시하거나 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="dbcaa-115">Display or change the table from which the data is obtained.</span></span>  
  
 <span data-ttu-id="dbcaa-116">현재 테이블과 다른 열이 있는 테이블로 원본을 변경하면 열이 다르다는 경고 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="dbcaa-116">If you change the source to a table that has different columns than the current table, a message is displayed warning that the columns are different.</span></span> <span data-ttu-id="dbcaa-117">그런 다음 현재 테이블에 넣을 열을 선택하고 **저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="dbcaa-117">You must then select the columns that you want to put in the current table and click **Save**.</span></span> <span data-ttu-id="dbcaa-118">테이블 왼쪽의 확인란을 선택하여 테이블 전체를 바꿀 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dbcaa-118">You can replace the entire table by selecting the check box at the left of the table.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="dbcaa-119">테이블의 데이터 원본을 변경하면 현재 테이블의 내용이 새 원본 테이블의 내용으로 바뀝니다.</span><span class="sxs-lookup"><span data-stu-id="dbcaa-119">When you change the data source of a table, you essentially replace the contents of the current table with the contents of the new source table.</span></span>  
  
 <span data-ttu-id="dbcaa-120">**열 이름 숨기기**</span><span class="sxs-lookup"><span data-stu-id="dbcaa-120">**Column names from**</span></span>  
 |||  
|-|-|  
|<span data-ttu-id="dbcaa-121">**원본**</span><span class="sxs-lookup"><span data-stu-id="dbcaa-121">**Source**</span></span>|<span data-ttu-id="dbcaa-122">현재 열 이름을 선택된 원본 테이블의 열 이름으로 바꾸려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="dbcaa-122">Select this option to replace the current column names with the column names from the selected source table.</span></span>|  
|<span data-ttu-id="dbcaa-123">**모델**</span><span class="sxs-lookup"><span data-stu-id="dbcaa-123">**Model**</span></span>|<span data-ttu-id="dbcaa-124">모델에 있는 대로 현재 열 이름을 사용하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="dbcaa-124">Select this option to use the current column names as they exist in the model.</span></span>|  
  
 <span data-ttu-id="dbcaa-125">**미리 보기 새로 고침**</span><span class="sxs-lookup"><span data-stu-id="dbcaa-125">**Refresh preview**</span></span>  
 <span data-ttu-id="dbcaa-126">현재 선택된 원본 테이블의 데이터 열을 보려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="dbcaa-126">Click to view the columns of data in the currently selected source table.</span></span>  
  
 <span data-ttu-id="dbcaa-127">**전환**</span><span class="sxs-lookup"><span data-stu-id="dbcaa-127">**Switch to**</span></span>  
 |||  
|-|-|  
|<span data-ttu-id="dbcaa-128">**테이블 미리 보기**</span><span class="sxs-lookup"><span data-stu-id="dbcaa-128">**Table preview**</span></span>|<span data-ttu-id="dbcaa-129">선택된 테이블과 제한된 수의 데이터 행을 미리 보려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="dbcaa-129">Select this option to preview the selected table and a limited number of rows of data.</span></span>|  
|<span data-ttu-id="dbcaa-130">**쿼리 편집기**</span><span class="sxs-lookup"><span data-stu-id="dbcaa-130">**Query editor**</span></span>|<span data-ttu-id="dbcaa-131">선택된 데이터 원본에 대한 쿼리를 보려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="dbcaa-131">Select this option to view the query against the selected data source.</span></span> <span data-ttu-id="dbcaa-132">일부 데이터 원본에 대해서는 이 옵션을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="dbcaa-132">This option is not available for all data sources.</span></span>|  
  
 <span data-ttu-id="dbcaa-133">**열 머리글의 확인란**</span><span class="sxs-lookup"><span data-stu-id="dbcaa-133">**Checkbox in the column header**</span></span>  
 <span data-ttu-id="dbcaa-134">데이터 가져오기에 열을 포함하려면 이 확인란을 선택하고,</span><span class="sxs-lookup"><span data-stu-id="dbcaa-134">Select the checkbox to include the column in the data import.</span></span> <span data-ttu-id="dbcaa-135">데이터 가져오기에서 열을 제거하려면 이 확인란의 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="dbcaa-135">Clear the checkbox to remove the column from the data import.</span></span>  
  
 <span data-ttu-id="dbcaa-136">**열 머리글의 아래쪽 화살표 단추**</span><span class="sxs-lookup"><span data-stu-id="dbcaa-136">**Down-arrow button in the column header**</span></span>  
 <span data-ttu-id="dbcaa-137">열의 데이터를 필터링합니다.</span><span class="sxs-lookup"><span data-stu-id="dbcaa-137">Filter data in the column.</span></span>  
  
 <span data-ttu-id="dbcaa-138">**행 필터 지우기**</span><span class="sxs-lookup"><span data-stu-id="dbcaa-138">**Clear row filters**</span></span>  
 <span data-ttu-id="dbcaa-139">적용된 모든 필터를 제거하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="dbcaa-139">Click to remove any filters that have been applied.</span></span>  
  
 <span data-ttu-id="dbcaa-140">**확인**</span><span class="sxs-lookup"><span data-stu-id="dbcaa-140">**OK**</span></span>  
 <span data-ttu-id="dbcaa-141">열 바꾸기를 비롯한 모든 변경 내용을 적용하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="dbcaa-141">Click to apply all changes that you made, including replacing columns.</span></span>  
  
## <a name="query-design-mode"></a><span data-ttu-id="dbcaa-142">쿼리 디자인 모드</span><span class="sxs-lookup"><span data-stu-id="dbcaa-142">Query Design Mode</span></span>  
 <span data-ttu-id="dbcaa-143">**테이블 이름**</span><span class="sxs-lookup"><span data-stu-id="dbcaa-143">**Table name**</span></span>  
 <span data-ttu-id="dbcaa-144">모델에 데이터 테이블의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="dbcaa-144">Displays the name of the data table in the model.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="dbcaa-145">여기서 이름을 편집할 수는 없지만 디자이너 아래쪽에 있는 테이블 탭을 마우스 오른쪽 단추로 클릭하면 테이블 이름을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dbcaa-145">You cannot edit the name here; however, you can change the name of the table by right-clicking the table tab at the bottom of the designer.</span></span>  
  
 <span data-ttu-id="dbcaa-146">**연결 이름**</span><span class="sxs-lookup"><span data-stu-id="dbcaa-146">**Connection name**</span></span>  
 <span data-ttu-id="dbcaa-147">현재 사용 중인 연결의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="dbcaa-147">Displays the name of the connection that is currently in use.</span></span>  
  
 <span data-ttu-id="dbcaa-148">**전환**</span><span class="sxs-lookup"><span data-stu-id="dbcaa-148">**Switch to**</span></span>  
 |||  
|-|-|  
|<span data-ttu-id="dbcaa-149">**테이블 미리 보기**</span><span class="sxs-lookup"><span data-stu-id="dbcaa-149">**Table preview**</span></span>|<span data-ttu-id="dbcaa-150">선택된 테이블과 몇 개의 데이터 행을 미리 보려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="dbcaa-150">Select this option to preview the selected table and a few rows of data.</span></span>|  
|<span data-ttu-id="dbcaa-151">**쿼리 편집기**</span><span class="sxs-lookup"><span data-stu-id="dbcaa-151">**Query editor**</span></span>|<span data-ttu-id="dbcaa-152">선택된 데이터 원본에 대해 실행될 쿼리를 보려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="dbcaa-152">Select this option to view the query that will be issued against the selected data source.</span></span>|  
  
 <span data-ttu-id="dbcaa-153">**Sql 문**</span><span class="sxs-lookup"><span data-stu-id="dbcaa-153">**Sql statement**</span></span>  
 <span data-ttu-id="dbcaa-154">행을 검색하기 위해 현재 데이터 원본에 대해 실행된 SQL 문을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="dbcaa-154">Displays the SQL statement that is issued against the current data source to retrieve rows.</span></span> <span data-ttu-id="dbcaa-155">기본적으로 모든 행이 검색되지만 필터를 디자인하거나 SQL 문을 직접 편집하여 행의 일부만 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dbcaa-155">By default, all rows are retrieved, but you can retrieve a subset of rows, either by designing a filter, or by manually editing the SQL statement.</span></span>  
  
 <span data-ttu-id="dbcaa-156">**유효성 검사**</span><span class="sxs-lookup"><span data-stu-id="dbcaa-156">**Validate**</span></span>  
 <span data-ttu-id="dbcaa-157">선택된 데이터 원본 및 공급자에 대해 문이 구문적으로 올바른지 확인하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="dbcaa-157">Click to verify that the statement is syntactically correct for the selected data source and provider.</span></span>  
  
 <span data-ttu-id="dbcaa-158">**디자인**</span><span class="sxs-lookup"><span data-stu-id="dbcaa-158">**Design**</span></span>  
 <span data-ttu-id="dbcaa-159">시각적 쿼리 디자이너를 열고 쿼리 문을 작성하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="dbcaa-159">Click to open a visual query designer and build a query statement.</span></span> <span data-ttu-id="dbcaa-160">디자이너를 사용하는 방법을 보려면 디자이너에서 F1 키를 누르십시오.</span><span class="sxs-lookup"><span data-stu-id="dbcaa-160">For information about how to use the designer, press F1 from the designer.</span></span>  
  
 <span data-ttu-id="dbcaa-161">**확인**</span><span class="sxs-lookup"><span data-stu-id="dbcaa-161">**OK**</span></span>  
 <span data-ttu-id="dbcaa-162">열 바꾸기를 비롯한 모든 변경 내용을 적용하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="dbcaa-162">Click to apply all changes that you made, including replacing columns.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dbcaa-163">참고 항목</span><span class="sxs-lookup"><span data-stu-id="dbcaa-163">See Also</span></span>  
 [<span data-ttu-id="dbcaa-164">테이블 및 열&#40;SSAS 테이블 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="dbcaa-164">Tables and Columns &#40;SSAS Tabular&#41;</span></span>](tabular-models/tables-and-columns-ssas-tabular.md)  
  
  
