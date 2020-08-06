---
title: 추적 결과 보기 수정 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 860a80dc-bac0-4ef0-bf7f-7a9b430d7aa3
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 050c8f179742cf3cef6473b03f062390caf195f6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647185"
---
# <a name="modify-the-trace-results-view"></a><span data-ttu-id="a56fc-102">추적 결과 보기 수정</span><span class="sxs-lookup"><span data-stu-id="a56fc-102">Modify the Trace Results View</span></span>
  <span data-ttu-id="a56fc-103">이 항목에서는 다음 작업을 수행하여 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] 에서 확장 이벤트 세션에 대한 추적 결과 뷰를 수정하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="a56fc-103">This topic describes how to modify the trace results view of an Extended Events session in [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] by performing the following tasks.</span></span>  
  
1.  [<span data-ttu-id="a56fc-104">열 추가 또는 제거</span><span class="sxs-lookup"><span data-stu-id="a56fc-104">Add or Remove Columns</span></span>](#AddRemoveColumns)  
  
2.  [<span data-ttu-id="a56fc-105">병합된 열 만들기, 편집 및 삭제</span><span class="sxs-lookup"><span data-stu-id="a56fc-105">Create, Edit, or Delete Merged Columns</span></span>](#ChangeColumns)  
  
3.  [<span data-ttu-id="a56fc-106">결과 정렬</span><span class="sxs-lookup"><span data-stu-id="a56fc-106">Sort the Results</span></span>](#SortResults)  
  
4.  [<span data-ttu-id="a56fc-107">결과 그룹화</span><span class="sxs-lookup"><span data-stu-id="a56fc-107">Group the Results</span></span>](#GroupResults)  
  
5.  [<span data-ttu-id="a56fc-108">결과 집계</span><span class="sxs-lookup"><span data-stu-id="a56fc-108">Aggregate the Results</span></span>](#AggregateResults)  
  
6.  [<span data-ttu-id="a56fc-109">결과 필터링</span><span class="sxs-lookup"><span data-stu-id="a56fc-109">Filter the Results</span></span>](#Filter)  
  
7.  [<span data-ttu-id="a56fc-110">열에서 텍스트 검색</span><span class="sxs-lookup"><span data-stu-id="a56fc-110">Search for Text in Columns</span></span>](#Search)  
  
8.  [<span data-ttu-id="a56fc-111">표시 설정 변경</span><span class="sxs-lookup"><span data-stu-id="a56fc-111">Change the Display Settings</span></span>](#ChangeDisplay)  
  
##  <a name="add-or-remove-columns"></a><a name="AddRemoveColumns"></a><span data-ttu-id="a56fc-112">열 추가 또는 제거</span><span class="sxs-lookup"><span data-stu-id="a56fc-112">Add or Remove Columns</span></span>  
  
1.  <span data-ttu-id="a56fc-113">.XEL 파일을 열고 추적 결과를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="a56fc-113">Open a .XEL file to view the trace results.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a56fc-114"> 세션 이름을 마우스 오른쪽 단추로 클릭하고 **라이브 데이터 감시**를 선택해도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a56fc-114">You can also right click the session name, and then select **Watch Live Data**.</span></span>  
  
2.  <span data-ttu-id="a56fc-115">추적 결과 창에서 열 머리글을 마우스 오른쪽 단추로 클릭한 다음 **열 선택**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a56fc-115">In the trace results window, right-click the column header, and then select **Choose Columns**.</span></span>  
  
3.  <span data-ttu-id="a56fc-116">**열 선택** 대화 상자의 **사용 가능한 열** 섹션에서 추가할 열 이름을 선택한 다음 오른쪽 화살표를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a56fc-116">In the **Choose Columns** dialog box, in the **Available columns** section, select the column names you want to add, and then click the right arrow.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a56fc-117">기본적으로 열은 이름을 기준으로 정렬됩니다.</span><span class="sxs-lookup"><span data-stu-id="a56fc-117">By default, the columns are arranged by name.</span></span> <span data-ttu-id="a56fc-118">열을 이벤트 기준으로 표시하려면 **이벤트별 정렬**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a56fc-118">To display the columns by event, click **Arrange by event**.</span></span>  
  
     <span data-ttu-id="a56fc-119">열을 제거하려면 **선택한 열** 섹션에서 제거할 열을 선택하고 왼쪽 화살표를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a56fc-119">To remove columns, in the **Selected columns** section, select the columns you want to remove, and click the left arrow.</span></span>  
  
4.  <span data-ttu-id="a56fc-120">**선택한 열** 섹션에서 열 순서 표시를 변경하려면 각각 **위로 이동** 또는 **아래로 이동** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a56fc-120">In the **Selected columns** section, to change the column order display, click **Move Up** or **Move Down** respectively.</span></span> <span data-ttu-id="a56fc-121">여러 행을 이동할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a56fc-121">You cannot move multiple rows.</span></span>  
  
5.  <span data-ttu-id="a56fc-122">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a56fc-122">Click **OK**.</span></span>  
  
##  <a name="create-edit-or-delete-merged-columns"></a><a name="ChangeColumns"></a><span data-ttu-id="a56fc-123">병합 된 열 만들기, 편집 또는 삭제</span><span class="sxs-lookup"><span data-stu-id="a56fc-123">Create, Edit, or Delete Merged Columns</span></span>  
  
#### <a name="to-create-merged-columns"></a><span data-ttu-id="a56fc-124">병합된 열을 만들려면</span><span class="sxs-lookup"><span data-stu-id="a56fc-124">To create merged columns</span></span>  
  
1.  <span data-ttu-id="a56fc-125">.XEL 파일을 열고 추적 결과를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="a56fc-125">Open a .XEL file to view the trace results.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a56fc-126"> 세션 이름을 마우스 오른쪽 단추로 클릭하고 **라이브 데이터 감시**를 선택해도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a56fc-126">You can also right click the session name, and then select **Watch Live Data**.</span></span>  
  
2.  <span data-ttu-id="a56fc-127">추적 결과 창에서 열 머리글을 마우스 오른쪽 단추로 클릭한 다음 **열 선택**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a56fc-127">In the trace results window, right-click the column header, and then click **Choose Columns**.</span></span>  
  
3.  <span data-ttu-id="a56fc-128">**열 선택** 대화 상자에서 **새로 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a56fc-128">In the **Choose Columns** dialog box, click **New**.</span></span>  
  
4.  <span data-ttu-id="a56fc-129">**새로 병합된 열** 대화 상자의 **병합된 열 이름** 상자에 병합된 열의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="a56fc-129">In the **New Merged Column** dialog box, in the **Merged column name** box, enter a name for the merged columns.</span></span>  
  
5.  <span data-ttu-id="a56fc-130">**병합할 원본 열** 상자의 드롭다운 목록에서 병합할 두 개 이상의 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a56fc-130">In the **Original columns to merge** box, select two or more columns to merge from the drop-down list.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a56fc-131">확장 이벤트는 최대 5개 열의 병합만 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="a56fc-131">Extended Events only supports merging up to five columns.</span></span>  
  
6.  <span data-ttu-id="a56fc-132">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a56fc-132">Click **OK**.</span></span>  
  
#### <a name="to-edit-merged-columns"></a><span data-ttu-id="a56fc-133">병합된 열을 편집하려면</span><span class="sxs-lookup"><span data-stu-id="a56fc-133">To edit merged columns</span></span>  
  
1.  <span data-ttu-id="a56fc-134">.XEL 파일을 열고 추적 결과를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="a56fc-134">Open a .XEL file to view the trace results.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a56fc-135"> 세션 이름을 마우스 오른쪽 단추로 클릭하고 **라이브 데이터 감시**를 선택해도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a56fc-135">You can also right click the session name, and then select **Watch Live Data**.</span></span>  
  
2.  <span data-ttu-id="a56fc-136">추적 결과 창에서 열 머리글을 마우스 오른쪽 단추로 클릭한 다음 **열 선택**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a56fc-136">In the trace results window, right-click the column header, and then click **Choose Columns**.</span></span>  
  
3.  <span data-ttu-id="a56fc-137">**열 선택** 대화 상자에서 **편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a56fc-137">In the **Choose Columns** dialog box, click **Edit**.</span></span>  
  
4.  <span data-ttu-id="a56fc-138">병합된 열의 이름을 변경하려면 **새로 병합된 열** 대화 상자의 **병합된 열 이름** 상자에 새 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="a56fc-138">To change the name of the merged column, in the **New Merged Column** dialog box, in the **Merged column name** box, enter the new name.</span></span>  
  
     <span data-ttu-id="a56fc-139">병합할 열을 변경하려면 **병합할 원본 열** 상자의 드롭다운 목록에서 병합할 열을 선택하고 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a56fc-139">To change the columns you want to merge, in the **Original columns to merge** box, select the columns you want to merge from the drop-down list, and then click **OK**.</span></span>  
  
#### <a name="to-delete-merged-columns"></a><span data-ttu-id="a56fc-140">병합된 열을 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="a56fc-140">To delete merged columns</span></span>  
  
1.  <span data-ttu-id="a56fc-141">.XEL 파일을 열고 추적 결과를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="a56fc-141">Open a .XEL file to view the trace results.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a56fc-142"> 세션 이름을 마우스 오른쪽 단추로 클릭하고 **라이브 데이터 감시**를 선택해도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a56fc-142">You can also right click the session name, and then select **Watch Live Data**.</span></span>  
  
2.  <span data-ttu-id="a56fc-143">추적 결과 창에서 열 머리글을 마우스 오른쪽 단추로 클릭한 다음 **열 선택**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a56fc-143">In the trace results window, right-click the column header, and then click **Choose Columns**.</span></span>  
  
3.  <span data-ttu-id="a56fc-144">**열 선택** 대화 상자에서 삭제할 병합된 열의 이름을 선택한 다음 **삭제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a56fc-144">In the **Choose Columns** dialog box, select the name of the merged column you want to delete, and then click **Delete**.</span></span>  
  
##  <a name="sort-the-results"></a><a name="SortResults"></a><span data-ttu-id="a56fc-145">결과 정렬</span><span class="sxs-lookup"><span data-stu-id="a56fc-145">Sort the Results</span></span>  
  
#### <a name="to-sort-the-results-in-ascending-or-descending-order"></a><span data-ttu-id="a56fc-146">결과를 오름차순 또는 내림차순으로 정렬하려면</span><span class="sxs-lookup"><span data-stu-id="a56fc-146">To sort the results in ascending or descending order</span></span>  
  
-   <span data-ttu-id="a56fc-147">.XEL 파일을 열고 추적 결과를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="a56fc-147">Open a .XEL file to view the trace results.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a56fc-148"> 세션 이름을 마우스 오른쪽 단추로 클릭하고 **라이브 데이터 감시**를 선택한 다음 도구 모음에서 **데이터 피드 중지** 단추를 클릭할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a56fc-148">You can also right click the session name, select **Watch Live Data**, and then click the **Stop Data Feed** button on the toolbar.</span></span>  
  
-   <span data-ttu-id="a56fc-149">추적 결과 창에서 정렬할 열 머리글을 마우스 오른쪽 단추로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a56fc-149">In the trace results window, right-click the column heading you want to sort.</span></span> <span data-ttu-id="a56fc-150">열을 오름차순 또는 내림차순으로 정렬하려면 각각 **오름차순 정렬** 또는 **내림차순 정렬** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a56fc-150">Click **Sort Ascending** or **Sort Descending** to sort the column in ascending or descending order respectively.</span></span>  
  
     <span data-ttu-id="a56fc-151">그룹화된 열이 있는 경우 열을 정렬하면 그룹 내의 데이터만 정렬됩니다.</span><span class="sxs-lookup"><span data-stu-id="a56fc-151">If you have grouped columns, sorting the column will only sort data within the group.</span></span>  
  
##  <a name="group-results"></a><a name="GroupResults"></a><span data-ttu-id="a56fc-152">그룹 결과</span><span class="sxs-lookup"><span data-stu-id="a56fc-152">Group Results</span></span>  
  
#### <a name="to-group-the-results-by-a-single-column"></a><span data-ttu-id="a56fc-153">결과를 단일 열로 그룹화하려면</span><span class="sxs-lookup"><span data-stu-id="a56fc-153">To group the results by a single column</span></span>  
  
1.  <span data-ttu-id="a56fc-154">.XEL 파일을 열고 추적 결과를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="a56fc-154">Open a .XEL file to view the trace results.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a56fc-155"> 세션 이름을 마우스 오른쪽 단추로 클릭하고 **라이브 데이터 감시**를 선택한 다음 확장 이벤트 도구 모음에서 **데이터 피드 중지** 단추를 클릭할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a56fc-155">You can also right click the session name, select **Watch Live Data**, and then click the **Stop Data Feed** button on the Extended Events toolbar.</span></span>  
  
2.  <span data-ttu-id="a56fc-156">추적 결과 창에서 그룹화하려는 열 머리글을 마우스 오른쪽 단추로 클릭한 다음 **이 열을 기준으로 그룹화**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a56fc-156">In the trace results window, right-click the column header you want to group, and then click **Group By This Column**.</span></span>  
  
#### <a name="to-group-the-results-by-multiple-columns"></a><span data-ttu-id="a56fc-157">결과를 복수 열로 그룹화하려면</span><span class="sxs-lookup"><span data-stu-id="a56fc-157">To group the results by multiple columns</span></span>  
  
1.  <span data-ttu-id="a56fc-158">.XEL 파일을 열고 추적 결과를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="a56fc-158">Open a .XEL file to view the trace results.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a56fc-159"> 세션 이름을 마우스 오른쪽 단추로 클릭하고 **라이브 데이터 감시**를 선택한 다음 도구 모음에서 **데이터 피드 중지** 단추를 클릭할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a56fc-159">You can also right click the session name, select **Watch Live Data**, and then click the **Stop Data Feed** button on the toolbar.</span></span>  
  
2.  <span data-ttu-id="a56fc-160">확장 이벤트 도구 모음에서 **그룹화** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a56fc-160">Click the **Grouping** button on the Extended Events toolbar.</span></span>  
  
3.  <span data-ttu-id="a56fc-161">**그룹화** 대화 상자의 **사용 가능한 열** 상자에서 그룹화할 열을 선택한 다음 오른쪽 화살표를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a56fc-161">In the **Grouping** dialog box, in the **Available columns** box, select the columns you want to group, and then click the right arrow.</span></span>  
  
     <span data-ttu-id="a56fc-162">그룹화 순서를 변경하려면 **그룹화된 열** 섹션에서 위로 또는 아래로 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a56fc-162">To change the grouping order, in the **Columns grouped on** section, click the up or down arrows.</span></span>  
  
     <span data-ttu-id="a56fc-163">그룹화에서 열을 제거하려면 **그룹화된 열** 상자에서 제거할 열을 선택한 다음 왼쪽 화살표를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a56fc-163">To remove columns from the grouping, in the **Columns grouped on** box, select the columns you want to remove and then click the left arrow.</span></span>  
  
4.  <span data-ttu-id="a56fc-164">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a56fc-164">Click **OK**.</span></span>  
  
##  <a name="aggregate-results"></a><a name="AggregateResults"></a><span data-ttu-id="a56fc-165">집계 결과</span><span class="sxs-lookup"><span data-stu-id="a56fc-165">Aggregate Results</span></span>  
 <span data-ttu-id="a56fc-166">확장 이벤트는 다섯 가지 집계 함수를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="a56fc-166">Extended Events supports five aggregation functions:</span></span>  
  
-   <span data-ttu-id="a56fc-167">Sum</span><span class="sxs-lookup"><span data-stu-id="a56fc-167">Sum</span></span>  
  
-   <span data-ttu-id="a56fc-168">최소값</span><span class="sxs-lookup"><span data-stu-id="a56fc-168">Min</span></span>  
  
-   <span data-ttu-id="a56fc-169">최대값</span><span class="sxs-lookup"><span data-stu-id="a56fc-169">Max</span></span>  
  
-   <span data-ttu-id="a56fc-170">평균</span><span class="sxs-lookup"><span data-stu-id="a56fc-170">Average</span></span>  
  
-   <span data-ttu-id="a56fc-171">개수</span><span class="sxs-lookup"><span data-stu-id="a56fc-171">Count</span></span>  
  
 <span data-ttu-id="a56fc-172">Sum, Min, Max 및 Average는 사용 가능한 숫자 열에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a56fc-172">Sum, Min,  Max, and Average can only be used with available numeric columns.</span></span> <span data-ttu-id="a56fc-173">count는 그룹에서 선택한 열에 대해 존재하는 Null이 아닌 값의 숫자입니다.</span><span class="sxs-lookup"><span data-stu-id="a56fc-173">Count is the number of non-null values that exist for the selected column in the group.</span></span>  
  
#### <a name="to-aggregate-results"></a><span data-ttu-id="a56fc-174">결과를 집계하려면</span><span class="sxs-lookup"><span data-stu-id="a56fc-174">To aggregate results</span></span>  
  
1.  <span data-ttu-id="a56fc-175">.XEL 파일을 열고 추적 결과를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="a56fc-175">Open a .XEL file to view the trace results.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a56fc-176"> 세션 이름을 마우스 오른쪽 단추로 클릭하고 **라이브 데이터 감시**를 선택한 다음 도구 모음에서 **데이터 피드 중지** 단추를 클릭할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a56fc-176">You can also right click the session name, select **Watch Live Data**, and then click the **Stop Data Feed** button on the toolbar.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a56fc-177">그룹에 대해 집계가 실행되므로 집계를 실행하기 전에 결과를 그룹화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a56fc-177">Aggregation is run against a group, so you must group the results before you can perform the aggregation.</span></span>  
  
2.  <span data-ttu-id="a56fc-178">확장 이벤트 도구 모음에서 **집계** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a56fc-178">On the Extended Events toolbar, click the **Aggregate** button.</span></span>  
  
     <span data-ttu-id="a56fc-179">**집계** 대화 상자가 나타나면서 집계에 사용할 수 있는 열이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a56fc-179">The **Aggregation** dialog box appears displaying the columns available for aggregation.</span></span>  
  
3.  <span data-ttu-id="a56fc-180">**집계 유형**의 드롭다운 목록에서 해당 열을 집계할 방법을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a56fc-180">Under **Aggregation Type**, select how you want to aggregate the corresponding column from the drop-down list.</span></span>  
  
4.  <span data-ttu-id="a56fc-181">**집계 정렬 기준** 상자의 드롭다운 목록에서 정렬할 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a56fc-181">In the **Sort aggregation by** box, select the column you want to sort by from the drop-down list.</span></span>  
  
5.  <span data-ttu-id="a56fc-182">집계 결과를 오름차순으로 정렬하려면 **오름차순** 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a56fc-182">Select the **In ascending order** option to sort the aggregation result in ascending order.</span></span>  
  
6.  <span data-ttu-id="a56fc-183">집계 결과를 내림차순으로 정렬하려면 **내림차순** 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a56fc-183">Select the **In descending order** option to sort the aggregation result in descending order.</span></span>  
  
7.  <span data-ttu-id="a56fc-184">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a56fc-184">Click **OK**.</span></span>  
  
##  <a name="filter-results"></a><a name="Filter"></a><span data-ttu-id="a56fc-185">필터 결과</span><span class="sxs-lookup"><span data-stu-id="a56fc-185">Filter Results</span></span>  
 <span data-ttu-id="a56fc-186">필터를 적용하여 추적 창에 표시되는 추적 결과의 범위를 좁힐 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a56fc-186">You can apply filters to narrow down the trace results that are displayed in the trace window.</span></span> <span data-ttu-id="a56fc-187">표시 필터에는 시간 필터 및 고급 필터가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a56fc-187">The display filter includes a time filter and an advanced filter.</span></span> <span data-ttu-id="a56fc-188">시간 필터를 사용하여 이벤트 타임스탬프를 기준으로 추적 결과를 필터링할 수 있으며, 고급 필터를 사용하면 이벤트 필드와 동작을 사용하여 필터 조건을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a56fc-188">You use the time filter to filter the trace results by event timestamp, and you use the advanced filter to construct filter conditions using the event fields and actions.</span></span> <span data-ttu-id="a56fc-189">시간 및 고급 필터 간에는 논리적 AND의 관계가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a56fc-189">There is an logical AND relationship between the Time and Advanced Filters.</span></span>  
  
#### <a name="to-create-a-filter"></a><span data-ttu-id="a56fc-190">필터를 만들려면</span><span class="sxs-lookup"><span data-stu-id="a56fc-190">To create a filter</span></span>  
  
1.  <span data-ttu-id="a56fc-191">.XEL 파일을 열고 추적 결과를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="a56fc-191">Open a .XEL file to view the trace results.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a56fc-192"> 세션 이름을 마우스 오른쪽 단추로 클릭하고 **라이브 데이터 감시**를 선택해도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a56fc-192">You can also right click the session name, and then select **Watch Live Data**.</span></span>  
  
2.  <span data-ttu-id="a56fc-193">추적 결과 창에서 필터링하려는 결과를 선택한 다음 확장 이벤트 도구 모음에서 **필터** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a56fc-193">In the trace results window, select the results you want to filter, and then on the Extended Events toolbar, click the **Filters** button.</span></span>  
  
3.  <span data-ttu-id="a56fc-194">**필터** 대화 상자에서 **시간 필터 설정** 을 선택하고 슬라이더 막대를 끌어 시간대를 설정하여 시간 필터를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="a56fc-194">In the **Filters** dialog box, select **Set time filter** to set the time filter by dragging the slider bars to set the timeline.</span></span> <span data-ttu-id="a56fc-195">슬라이더 막대를 움직이면 그에 따라 시간 상자에 시간이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a56fc-195">Note that when you move the slider bars, the time box displays the time value accordingly.</span></span> <span data-ttu-id="a56fc-196">시간 상자에 시간을 입력하거나 드롭다운 목록에서 선택할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a56fc-196">You can also enter the time in the time boxes, or you select it from the drop-down list.</span></span> <span data-ttu-id="a56fc-197">시간을 입력하면 그에 따라 왼쪽의 시간 슬라이더가 움직입니다.</span><span class="sxs-lookup"><span data-stu-id="a56fc-197">Note that when you enter the time, the left time slider will move accordingly.</span></span>  
  
4.  <span data-ttu-id="a56fc-198">**추가 필터** 섹션에서 필터 조건을 적용 한 다음 **적용**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="a56fc-198">In the **Additional Filters** section, apply your filter criteria, and then click **Apply**.</span></span> <span data-ttu-id="a56fc-199">필터 만들기를 마쳤으면 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a56fc-199">When your finished created the filter, click **OK**.</span></span>  
  
 <span data-ttu-id="a56fc-200">이벤트 필드 이름이 동작 이름과 같은 특수한 상황이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a56fc-200">A special situation is when an event field has the same name as an action.</span></span> <span data-ttu-id="a56fc-201">일례로 session_id로 들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a56fc-201">An example of this would be session_id.</span></span> <span data-ttu-id="a56fc-202">session_id 필드를 포함하는 여러 이벤트가 있으며 session_id 동작을 추가할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a56fc-202">There are several events that include a session_id field and you could also add the session_id action.</span></span> <span data-ttu-id="a56fc-203">두 정보는 모두 수집되지만 확장 이벤트 프로파일러 디스플레이 표는 다음 논리를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a56fc-203">Both pieces of information are collected, but the Extended Events profiler display grid uses the following logic.</span></span>  
  
-   <span data-ttu-id="a56fc-204">표에 열(이 경우 session_id)의 복사본이 하나만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a56fc-204">Only one copy of the column (session_id in this case) is shown in the grid display.</span></span>  
  
-   <span data-ttu-id="a56fc-205">필드 및 동작이 데이터에 존재할 경우 필드 값이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a56fc-205">If both fields and action exist in the data, the field value is shown.</span></span>  
  
-   <span data-ttu-id="a56fc-206">필드 또는 동작이 데이터에 존재할 경우 해당 필드 또는 동작이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a56fc-206">If only field or action is exists in the data, the field or action is displayed.</span></span>  
  
-   <span data-ttu-id="a56fc-207">동작도 필드도 없을 경우 NULL이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a56fc-207">If neither action nor field exists, display NULL.</span></span>  
  
##  <a name="search-for-text-in-columns"></a><a name="Search"></a><span data-ttu-id="a56fc-208">열에서 텍스트 검색</span><span class="sxs-lookup"><span data-stu-id="a56fc-208">Search for Text in Columns</span></span>  
  
1.  <span data-ttu-id="a56fc-209">.XEL 파일을 열고 추적 결과를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="a56fc-209">Open a .XEL file to view the trace results.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a56fc-210"> 세션 이름을 마우스 오른쪽 단추로 클릭하고 **라이브 데이터 감시**를 선택해도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a56fc-210">You can also right click the session name, and then select **Watch Live Data**.</span></span>  
  
2.  <span data-ttu-id="a56fc-211">확장 이벤트 도구 모음에서 **찾기** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a56fc-211">On the Extended Events toolbar, click the **Find** button.</span></span>  
  
3.  <span data-ttu-id="a56fc-212">**확장 이벤트에서 찾기** 대화 상자의 **찾을 내용** 상자에 검색하려는 텍스트를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="a56fc-212">In the **Find in Extended Events** dialog box, in the **Find what** box, enter the text you want to search for.</span></span>  
  
     <span data-ttu-id="a56fc-213">드롭다운 목록에서 가장 최근에 검색한 20개의 문자열 중 하나를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a56fc-213">You can select one of your last 20 search strings from the drop-down list.</span></span>  
  
4.  <span data-ttu-id="a56fc-214">**찾는 위치** 상자의 드롭다운 목록에서 지정된 텍스트를 검색할 위치를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a56fc-214">In the **Look in** box, select the location in which to search for the specified text from the drop-down list.</span></span> <span data-ttu-id="a56fc-215">검색 시 다음 옵션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a56fc-215">Use the following options for searching:</span></span>  
  
    -   <span data-ttu-id="a56fc-216">**테이블 열**.</span><span class="sxs-lookup"><span data-stu-id="a56fc-216">**Table Columns**.</span></span> <span data-ttu-id="a56fc-217">추적 창에 표시되는 모든 열을 검색하려면 이 옵션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a56fc-217">Use this option to search all visible columns in the trace window.</span></span>  
  
    -   <span data-ttu-id="a56fc-218">**세부 정보**.</span><span class="sxs-lookup"><span data-stu-id="a56fc-218">**Details**.</span></span> <span data-ttu-id="a56fc-219">**확장 이벤트에서 찾기** 대화 상자를 열기 전에 선택한 추적 창에서 승격 된 모든 열 (승격 된 열 및 승격 되지 않은 열)을 검색 하려면이 옵션을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a56fc-219">Use this option to search all columns (promoted and non-promoted) in the trace window that were selected before opening the **Find in Extended Events** dialog box.</span></span>  
  
    -   <span data-ttu-id="a56fc-220">**\<Event column name>**.</span><span class="sxs-lookup"><span data-stu-id="a56fc-220">**\<Event column name>**.</span></span> <span data-ttu-id="a56fc-221">드롭다운 목록의 특정 이벤트 열에서 검색하려면 이 옵션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a56fc-221">Use this option to search in a specific event column from the drop-down list.</span></span>  
  
5.  <span data-ttu-id="a56fc-222">검색을 정의하는 방법을 지정하려면 다음 옵션을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="a56fc-222">Use the following options to specify how you want to define the search:</span></span>  
  
    1.  <span data-ttu-id="a56fc-223">**Case를 찾습니다**.</span><span class="sxs-lookup"><span data-stu-id="a56fc-223">**Match case**.</span></span> <span data-ttu-id="a56fc-224">이 옵션을 사용 하 여 **찾을 내용** 상자에 입력 한 텍스트에 대 한 검색 결과를 내용과 대/소문자가 모두 일치 하도록 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a56fc-224">Use this option to display the search results for the text you entered in the **Find what** box that are matched both by content and by case.</span></span>  
  
    2.  <span data-ttu-id="a56fc-225">**단어 단위로 검색**합니다.</span><span class="sxs-lookup"><span data-stu-id="a56fc-225">**Match whole word**.</span></span> <span data-ttu-id="a56fc-226">입력한 텍스트와 전체 단어가 일치하는 검색 결과만 표시하려면 이 옵션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a56fc-226">Use this option to display only the search results for the text you entered that match complete words.</span></span>  
  
    3.  <span data-ttu-id="a56fc-227">**위로 검색**.</span><span class="sxs-lookup"><span data-stu-id="a56fc-227">**Search up**.</span></span> <span data-ttu-id="a56fc-228">커서 위치에서 결과의 위로 검색하려면 이 옵션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a56fc-228">Use this option to search from your cursor location to the beginning of the results.</span></span>  
  
    4.  <span data-ttu-id="a56fc-229">를 **사용**합니다.</span><span class="sxs-lookup"><span data-stu-id="a56fc-229">**Use**.</span></span> <span data-ttu-id="a56fc-230">**찾을 내용** 상자에 입력한 특수 문자 및 정규식을 해석하려면 이 옵션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a56fc-230">Use this option to interpret the special characters and the regular expressions you entered in the **Find what** box.</span></span> <span data-ttu-id="a56fc-231">특수 문자에는 하나 이상의 문자를 나타내는 와일드카드 문자(\*) 및 (?)가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="a56fc-231">Special characters include the wildcard characters (\*) and (?) to represent one or more characters.</span></span> <span data-ttu-id="a56fc-232">정규식은 검색 텍스트의 패턴을 정의하는 데 사용하는 특수 표기입니다.</span><span class="sxs-lookup"><span data-stu-id="a56fc-232">Regular expressions are special notations used to define patterns of search text.</span></span>  
  
6.  <span data-ttu-id="a56fc-233">**찾을 내용** 상자에 입력한 다음 텍스트를 검색하려면 **다음 찾기** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a56fc-233">Click **Find Next** to search for the next text that you entered in the **Find what** box.</span></span>  
  
##  <a name="change-the-display-settings"></a><a name="ChangeDisplay"></a><span data-ttu-id="a56fc-234">표시 설정 변경</span><span class="sxs-lookup"><span data-stu-id="a56fc-234">Change the Display Settings</span></span>  
 <span data-ttu-id="a56fc-235">추적 결과의 열 정보(열 순서, 병합 열 및 열 너비) 및 필터 정보를 확장 이벤트의 표시 설정 파일(.viewsetting 파일)에 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a56fc-235">You can save column information (column order, merge column, and column width) and filter information of a trace result into an Extended Events display setting file (.viewsetting file).</span></span> <span data-ttu-id="a56fc-236">파일을 저장한 후 추적 결과에 이 파일을 적용하여 뷰를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a56fc-236">After saving the file, you can apply it to your trace results to change the view.</span></span>  
  
#### <a name="to-change-the-display-settings"></a><span data-ttu-id="a56fc-237">표시 설정을 변경하려면</span><span class="sxs-lookup"><span data-stu-id="a56fc-237">To change the display settings</span></span>  
  
1.  <span data-ttu-id="a56fc-238">.XEL 파일을 열고 추적 결과를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="a56fc-238">Open a .XEL file to view the trace results.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a56fc-239"> 세션 이름을 마우스 오른쪽 단추로 클릭하고 **라이브 데이터 감시**를 선택해도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a56fc-239">You can also right click the session name, and then select **Watch Live Data**.</span></span>  
  
2.  <span data-ttu-id="a56fc-240">추적 결과 창의 확장 이벤트 도구 모음이나 메뉴에서 **표시 설정**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a56fc-240">In the trace results window, on the Extended Events toolbar or menu, select **Display Settings**.</span></span>  
  
3.  <span data-ttu-id="a56fc-241">드롭다운 목록에서 다음 옵션 중 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a56fc-241">From the drop-down list, select one of the following options:</span></span>  
  
    -   <span data-ttu-id="a56fc-242">다른 **이름으로 저장**.</span><span class="sxs-lookup"><span data-stu-id="a56fc-242">**Save as**.</span></span> <span data-ttu-id="a56fc-243">추적 결과의 열 및 필터 정보를 .viewsetting 파일에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="a56fc-243">Save the columns and filter information of a trace result to a .viewsetting file.</span></span>  
  
    -   <span data-ttu-id="a56fc-244">를 **엽니다**.</span><span class="sxs-lookup"><span data-stu-id="a56fc-244">**Open**.</span></span> <span data-ttu-id="a56fc-245">기존 .viewsetting 파일을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="a56fc-245">Open an existing .viewsetting file.</span></span>  
  
    -   <span data-ttu-id="a56fc-246">**최근**항목을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="a56fc-246">**Open recent**.</span></span> <span data-ttu-id="a56fc-247">최근에 저장한 .viewsetting 파일을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="a56fc-247">Open a recently saved .viewsetting file.</span></span>  
  
  
