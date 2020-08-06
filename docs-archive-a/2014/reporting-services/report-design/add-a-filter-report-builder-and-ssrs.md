---
title: 필터 추가(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 10ae54e7-0e8a-4dff-995d-05516c51d076
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 61a5444c437027d92a9f054e74cbcac6af5cc776
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742831"
---
# <a name="add-a-filter-report-builder-and-ssrs"></a><span data-ttu-id="cd243-102">필터 추가(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="cd243-102">Add a Filter (Report Builder and SSRS)</span></span>
  <span data-ttu-id="cd243-103">계산 또는 표시 내용에 특정 값을 포함하거나 제외하려는 경우 데이터 세트, 데이터 영역 또는 그룹에 필터를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd243-103">Add a filter to a dataset, data region, or group when you want to include or exclude specific values for calculations or display.</span></span> <span data-ttu-id="cd243-104">필터는 런타임에 데이터 세트에 대해 가장 먼저 적용된 다음 데이터 영역과 그룹(그룹 계층 구조에 대해 하향식으로)에 차례로 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="cd243-104">Filters are applied at run time first on the dataset, and then on the data region, and then on the group, in top-down order for group hierarchies.</span></span> <span data-ttu-id="cd243-105">테이블, 행렬 또는 목록에서 행 그룹, 열 그룹 및 인접 그룹의 필터는 독립적으로 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="cd243-105">In a table, matrix, or list, filters for row groups, column groups, and adjacent groups are applied independently.</span></span> <span data-ttu-id="cd243-106">또한 차트에서 범주 그룹 및 계열 그룹의 필터는 독립적으로 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="cd243-106">In a chart, filters for category groups and series groups are applied independently.</span></span>  
  
 <span data-ttu-id="cd243-107">필터를 추가하려면 하나 이상의 필터 수식을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd243-107">To add a filter, you must specify one or more filter equations.</span></span> <span data-ttu-id="cd243-108">필터 수식은 필터링할 데이터를 식별하는 식, 연산자 및 비교할 값으로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="cd243-108">A filter equation consists of an expression that identifies the data that you want to filter, an operator, and the value to compare to.</span></span> <span data-ttu-id="cd243-109">필터링된 데이터와 값의 데이터 형식은 일치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd243-109">The data types of the filtered data and the value must match.</span></span> <span data-ttu-id="cd243-110">데이터 세트나 데이터 영역에는 집계 값에 대한 필터링이 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="cd243-110">Filtering on aggregate values for a dataset or data region is not supported.</span></span>  
  
 <span data-ttu-id="cd243-111">차트에서 데이터 요소를 필터링하려면 범주 그룹이나 계열 그룹에 대해 필터를 설정하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cd243-111">To filter data points in a chart, you can set a filter on a category group or a series group.</span></span> <span data-ttu-id="cd243-112">기본적으로 차트에서는 기본 제공 함수 Sum을 사용하여 동일한 그룹에 속하는 값을 계열의 개별 데이터 요소로 집계합니다.</span><span class="sxs-lookup"><span data-stu-id="cd243-112">By default, the chart uses the built-in function Sum to aggregate values that belong to the same group into an individual data point in the series.</span></span> <span data-ttu-id="cd243-113">계열의 집계 함수를 변경할 경우에는 필터 식의 집계 함수를 변경해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd243-113">If you change the aggregate function of a series, you must change the aggregate function in the filter expression.</span></span>  
  
 <span data-ttu-id="cd243-114">포함된 데이터 세트 및 공유 데이터 세트 필터링에 대한 자세한 내용은 [데이터 세트에 필터 추가&#40;보고서 작성기 및 SSRS&#41;](../report-data/add-a-filter-to-a-dataset-report-builder-and-ssrs.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cd243-114">For more information about filtering embedded and shared datasets, see [Add a Filter to a Dataset &#40;Report Builder and SSRS&#41;](../report-data/add-a-filter-to-a-dataset-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-set-a-filter-on-a-data-region"></a><span data-ttu-id="cd243-115">데이터 영역에 대해 필터를 설정하려면</span><span class="sxs-lookup"><span data-stu-id="cd243-115">To set a filter on a data region</span></span>  
  
1.  <span data-ttu-id="cd243-116">**디자인** 뷰에서 보고서를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="cd243-116">Open a report in **Design** view.</span></span>  
  
2.  <span data-ttu-id="cd243-117">디자인 화면에서 데이터 영역을 선택한 다음 속성을 마우스 오른쪽 단추로 클릭 _\<data region>_ **Properties**합니다.</span><span class="sxs-lookup"><span data-stu-id="cd243-117">Select the data region on the design surface, and then right-click _\<data region>_**Properties**.</span></span> <span data-ttu-id="cd243-118">계기의 경우 **계기 패널 속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="cd243-118">For a gauge, select **Gauge Panel Properties**.</span></span> <span data-ttu-id="cd243-119">_\<data region>_ **속성** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="cd243-119">The _\<data region>_**Properties** dialog box opens.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="cd243-120">테이블릭스 데이터 영역에서 모퉁이 셀이나 행 또는 열 핸들을 마우스 오른쪽 단추로 클릭한 다음 **테이블릭스 속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cd243-120">On a Tablix data region, right-click the corner cell or a row or column handle, and then click **Tablix Properties**.</span></span>  
  
3.  <span data-ttu-id="cd243-121">**필터**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cd243-121">Click **Filters**.</span></span> <span data-ttu-id="cd243-122">그러면 현재 필터 수식 목록이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="cd243-122">This displays the current list of filter equations.</span></span> <span data-ttu-id="cd243-123">기본적으로 이 목록은 비어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd243-123">By default, the list is empty.</span></span>  
  
4.  <span data-ttu-id="cd243-124">**추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cd243-124">Click **Add**.</span></span> <span data-ttu-id="cd243-125">새로운 빈 필터 수식이 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="cd243-125">A new blank filter equation appears.</span></span>  
  
5.  <span data-ttu-id="cd243-126">**식**에서 필터링할 필드에 대한 식을 입력하거나 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="cd243-126">In **Expression**, type or select the expression for the field to filter.</span></span> <span data-ttu-id="cd243-127">식을 편집하려면 식(*fx*) 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cd243-127">To edit the expression, click the expression (*fx*) button.</span></span>  
  
6.  <span data-ttu-id="cd243-128">5단계에서 만든 식의 데이터 형식과 일치하는 데이터 형식을 드롭다운 상자에서 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="cd243-128">From the drop-down box, select the data type that matches the type of data in the expression you created in step 5.</span></span>  
  
7.  <span data-ttu-id="cd243-129">**연산자** 상자에서 해당 필터로 **식** 상자와 **값** 상자의 값을 비교하는 데 사용할 연산자를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="cd243-129">In the **Operator** box, select the operator that you want the filter to use to compare the values in the **Expression** box and the **Value** box.</span></span> <span data-ttu-id="cd243-130">선택한 연산자에 따라 다음 단계에서 사용하는 값의 수가 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="cd243-130">The operator you choose determines the number of values that are used from the next step.</span></span>  
  
8.  <span data-ttu-id="cd243-131">**값** 상자에 해당 필터로 **식**의 값을 계산하는 데 기준이 되는 식 또는 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="cd243-131">In the **Value** box, type the expression or value against which you want the filter to evaluate the value in **Expression**.</span></span>  
  
     <span data-ttu-id="cd243-132">필터 수식의 예는 [필터 수식 예&#40;보고서 작성기 및 SSRS&#41;](filter-equation-examples-report-builder-and-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cd243-132">For examples of filter equations, see [Filter Equation Examples &#40;Report Builder and SSRS&#41;](filter-equation-examples-report-builder-and-ssrs.md).</span></span>  
  
9. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-set-a-filter-on-a-tablix-row-or-column-group"></a><span data-ttu-id="cd243-133">테이블릭스 행 또는 열 그룹에 대해 필터를 설정하려면</span><span class="sxs-lookup"><span data-stu-id="cd243-133">To set a filter on a Tablix row or column group</span></span>  
  
1.  <span data-ttu-id="cd243-134">**디자인** 뷰에서 보고서를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="cd243-134">Open a report in **Design** view.</span></span>  
  
2.  <span data-ttu-id="cd243-135">디자인 화면의 테이블, 행렬 또는 목록 데이터 영역을 마우스 오른쪽 단추로 클릭하여 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="cd243-135">Right-click the table, matrix, or list data region on the design surface to select it.</span></span> <span data-ttu-id="cd243-136">그룹화 창에 선택한 항목에 대한 그룹이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="cd243-136">The Grouping pane displays the groups for the selected item.</span></span>  
  
3.  <span data-ttu-id="cd243-137">그룹화 창에서 그룹을 마우스 오른쪽 단추로 클릭한 다음 **그룹 편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cd243-137">In the Grouping pane, right-click the group, and then click **Edit Group**.</span></span> <span data-ttu-id="cd243-138">**테이블릭스 그룹** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="cd243-138">The **Tablix Group** dialog box opens.</span></span>  
  
4.  <span data-ttu-id="cd243-139">**필터**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cd243-139">Click **Filters**.</span></span> <span data-ttu-id="cd243-140">그러면 현재 필터 수식 목록이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="cd243-140">This displays the current list of filter equations.</span></span> <span data-ttu-id="cd243-141">기본적으로 이 목록은 비어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd243-141">By default, the list is empty.</span></span>  
  
5.  <span data-ttu-id="cd243-142">**추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cd243-142">Click **Add**.</span></span> <span data-ttu-id="cd243-143">새로운 빈 필터 수식이 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="cd243-143">A new blank filter equation appears.</span></span>  
  
6.  <span data-ttu-id="cd243-144">**식**에서 필터링할 필드에 대한 식을 입력하거나 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="cd243-144">In **Expression**, type or select the expression for the field to filter.</span></span> <span data-ttu-id="cd243-145">식을 편집하려면 식(*fx*) 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cd243-145">To edit the expression, click the expression (*fx*) button.</span></span>  
  
7.  <span data-ttu-id="cd243-146">5단계에서 만든 식의 데이터 형식과 일치하는 데이터 형식을 드롭다운 상자에서 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="cd243-146">From the drop-down box, select the data type that matches the type of data in the expression you created in step 5.</span></span>  
  
8.  <span data-ttu-id="cd243-147">**연산자** 상자에서 해당 필터로 **식** 상자와 **값** 상자의 값을 비교하는 데 사용할 연산자를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="cd243-147">In the **Operator** box, select the operator that you want the filter to use to compare the values in the **Expression** box and the **Value** box.</span></span> <span data-ttu-id="cd243-148">선택한 연산자에 따라 다음 단계에서 사용하는 값의 수가 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="cd243-148">The operator you choose determines the number of values that are used from the next step.</span></span>  
  
9. <span data-ttu-id="cd243-149">**값** 상자에 해당 필터로 **식**의 값을 계산하는 데 기준이 되는 식 또는 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="cd243-149">In the **Value** box, type the expression or value against which you want the filter to evaluate the value in **Expression**.</span></span>  
  
     <span data-ttu-id="cd243-150">필터 수식의 예는 [필터 수식 예&#40;보고서 작성기 및 SSRS&#41;](filter-equation-examples-report-builder-and-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cd243-150">For examples of filter equations, see [Filter Equation Examples &#40;Report Builder and SSRS&#41;](filter-equation-examples-report-builder-and-ssrs.md).</span></span>  
  
10. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-set-a-filter-on-a-chart-category-group"></a><span data-ttu-id="cd243-151">차트 범주 그룹에 대해 필터를 설정하려면</span><span class="sxs-lookup"><span data-stu-id="cd243-151">To set a filter on a Chart category group</span></span>  
  
1.  <span data-ttu-id="cd243-152">**디자인** 뷰에서 보고서를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="cd243-152">Open a report in **Design** view.</span></span>  
  
2.  <span data-ttu-id="cd243-153">디자인 화면에서 차트를 두 번 클릭하여 데이터, 계열 및 범주 필드 끌어 놓기 영역을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="cd243-153">On the design surface, click the chart twice to bring up data, series and category field drop zones.</span></span>  
  
3.  <span data-ttu-id="cd243-154">범주 필드 끌어 놓기 영역에 포함된 필드를 마우스 오른쪽 단추로 클릭하고 **범주 그룹 속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="cd243-154">Right-click on a field contained in the category field drop zone and select **Category Group Properties**.</span></span>  
  
4.  <span data-ttu-id="cd243-155">**필터**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cd243-155">Click **Filters**.</span></span> <span data-ttu-id="cd243-156">그러면 현재 필터 수식 목록이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="cd243-156">This displays the current list of filter equations.</span></span> <span data-ttu-id="cd243-157">기본적으로 이 목록은 비어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd243-157">By default, the list is empty.</span></span>  
  
5.  <span data-ttu-id="cd243-158">**추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cd243-158">Click **Add**.</span></span> <span data-ttu-id="cd243-159">새로운 빈 필터 수식이 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="cd243-159">A new blank filter equation appears.</span></span>  
  
6.  <span data-ttu-id="cd243-160">**식**에서 필터링할 필드에 대한 식을 입력하거나 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="cd243-160">In **Expression**, type or select the expression for the field to filter.</span></span> <span data-ttu-id="cd243-161">식을 편집하려면 식(*fx*) 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cd243-161">To edit the expression, click the expression (*fx*) button.</span></span>  
  
7.  <span data-ttu-id="cd243-162">5단계에서 만든 식의 데이터 형식과 일치하는 데이터 형식을 드롭다운 상자에서 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="cd243-162">From the drop-down box, select the data type that matches the type of data in the expression you created in step 5.</span></span>  
  
8.  <span data-ttu-id="cd243-163">**연산자** 상자에서 해당 필터로 **식** 상자와 **값** 상자의 값을 비교하는 데 사용할 연산자를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="cd243-163">In the **Operator** box, select the operator that you want the filter to use to compare the values in the **Expression** box and the **Value** box.</span></span> <span data-ttu-id="cd243-164">선택한 연산자에 따라 다음 단계에서 사용하는 값의 수가 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="cd243-164">The operator you choose determines the number of values that are used from the next step.</span></span>  
  
9. <span data-ttu-id="cd243-165">**값** 상자에 해당 필터로 **식**의 값을 계산하는 데 기준이 되는 식 또는 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="cd243-165">In the **Value** box, type the expression or value against which you want the filter to evaluate the value in **Expression**.</span></span>  
  
     <span data-ttu-id="cd243-166">필터 수식의 예는 [필터 수식 예&#40;보고서 작성기 및 SSRS&#41;](filter-equation-examples-report-builder-and-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cd243-166">For examples of filter equations, see [Filter Equation Examples &#40;Report Builder and SSRS&#41;](filter-equation-examples-report-builder-and-ssrs.md).</span></span>  
  
10. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-set-a-filter-on-a-chart-series-group"></a><span data-ttu-id="cd243-167">차트 계열 그룹에 대해 필터를 설정하려면</span><span class="sxs-lookup"><span data-stu-id="cd243-167">To set a filter on a Chart series group</span></span>  
  
1.  <span data-ttu-id="cd243-168">**디자인** 뷰에서 보고서를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="cd243-168">Open a report in **Design** view.</span></span>  
  
2.  <span data-ttu-id="cd243-169">디자인 화면에서 차트를 두 번 클릭하여 데이터, 계열 및 범주 필드 끌어 놓기 영역을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="cd243-169">On the design surface, click the chart twice to bring up data, series and category field drop zones.</span></span>  
  
3.  <span data-ttu-id="cd243-170">계열 필드 끌어 놓기 영역에 포함된 필드를 마우스 오른쪽 단추로 클릭하고 **계열 그룹 속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="cd243-170">Right-click on a field contained in the series field drop zone and select **Series Group Properties**.</span></span>  
  
4.  <span data-ttu-id="cd243-171">**필터**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cd243-171">Click **Filters**.</span></span> <span data-ttu-id="cd243-172">그러면 현재 필터 수식 목록이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="cd243-172">This displays the current list of filter equations.</span></span> <span data-ttu-id="cd243-173">기본적으로 이 목록은 비어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd243-173">By default, the list is empty.</span></span>  
  
5.  <span data-ttu-id="cd243-174">**추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cd243-174">Click **Add**.</span></span> <span data-ttu-id="cd243-175">새로운 빈 필터 수식이 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="cd243-175">A new blank filter equation appears.</span></span>  
  
6.  <span data-ttu-id="cd243-176">**식**에서 필터링할 필드에 대한 식을 입력하거나 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="cd243-176">In **Expression**, type or select the expression for the field to filter.</span></span> <span data-ttu-id="cd243-177">식을 편집하려면 식(*fx*) 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cd243-177">To edit the expression, click the expression (*fx*) button.</span></span>  
  
7.  <span data-ttu-id="cd243-178">5단계에서 만든 식의 데이터 형식과 일치하는 데이터 형식을 드롭다운 상자에서 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="cd243-178">From the drop-down box, select the data type that matches the type of data in the expression you created in step 5.</span></span>  
  
8.  <span data-ttu-id="cd243-179">**연산자** 상자에서 해당 필터로 **식** 상자와 **값** 상자의 값을 비교하는 데 사용할 연산자를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="cd243-179">In the **Operator** box, select the operator that you want the filter to use to compare the values in the **Expression** box and the **Value** box.</span></span> <span data-ttu-id="cd243-180">선택한 연산자에 따라 다음 단계에서 사용하는 값의 수가 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="cd243-180">The operator you choose determines the number of values that are used from the next step.</span></span>  
  
9. <span data-ttu-id="cd243-181">**값** 상자에 해당 필터로 **식**의 값을 계산하는 데 기준이 되는 식 또는 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="cd243-181">In the **Value** box, type the expression or value against which you want the filter to evaluate the value in **Expression**.</span></span>  
  
     <span data-ttu-id="cd243-182">필터 수식의 예는 [필터 수식 예&#40;보고서 작성기 및 SSRS&#41;](filter-equation-examples-report-builder-and-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cd243-182">For examples of filter equations, see [Filter Equation Examples &#40;Report Builder and SSRS&#41;](filter-equation-examples-report-builder-and-ssrs.md).</span></span>  
  
10. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="cd243-183">참고 항목</span><span class="sxs-lookup"><span data-stu-id="cd243-183">See Also</span></span>  
 <span data-ttu-id="cd243-184">[데이터 세트 필터, 데이터 영역 필터 및 그룹 필터 추가&#40;보고서 작성기 및 SSRS&#41;](add-dataset-filters-data-region-filters-and-group-filters.md) </span><span class="sxs-lookup"><span data-stu-id="cd243-184">[Add Dataset Filters, Data Region Filters, and Group Filters &#40;Report Builder and SSRS&#41;](add-dataset-filters-data-region-filters-and-group-filters.md) </span></span>  
 <span data-ttu-id="cd243-185">[식 예&#40;보고서 작성기 및 SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="cd243-185">[Expression Examples &#40;Report Builder and SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="cd243-186">[계기&#40;보고서 작성기 및 SSRS&#41;](gauges-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="cd243-186">[Gauges &#40;Report Builder and SSRS&#41;](gauges-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="cd243-187">[&#40;보고서 작성기 및 SSRS를 나열&#41;](tables-matrices-and-lists-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="cd243-187">[Lists &#40;Report Builder and SSRS&#41;](tables-matrices-and-lists-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="cd243-188">차트&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="cd243-188">Charts &#40;Report Builder and SSRS&#41;</span></span>](charts-report-builder-and-ssrs.md)  
  
  
