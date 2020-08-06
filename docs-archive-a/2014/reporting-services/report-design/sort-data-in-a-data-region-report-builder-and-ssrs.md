---
title: 데이터 영역의 데이터 정렬(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 2fcb9be2-1daa-4c92-ad00-5f63cdf39f70
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: bc1fb458066bb942a490b08c0faad876dd3d5438
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739225"
---
# <a name="sort-data-in-a-data-region-report-builder-and-ssrs"></a><span data-ttu-id="6bb6c-102">데이터 영역의 데이터 정렬(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="6bb6c-102">Sort Data in a Data Region (Report Builder and SSRS)</span></span>
  <span data-ttu-id="6bb6c-103">보고서를 처음 실행할 때 데이터 영역에 있는 데이터의 정렬 순서를 변경하려면 데이터 영역 또는 그룹에서 정렬 식을 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6bb6c-103">To change the sort order of data in a data region when a report first runs, you must set the sort expression on the data region or group.</span></span> <span data-ttu-id="6bb6c-104">기본적으로 그룹의 정렬 식은 그룹 식과 같은 값으로 자동으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="6bb6c-104">By default, the sort expression for a group is automatically set to the same value as the group expression.</span></span>  
  
-   <span data-ttu-id="6bb6c-105">테이블릭스 데이터 영역에서는 세부 정보 그룹을 포함한 데이터 영역 또는 각 그룹에 대한 정렬 식을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="6bb6c-105">In a tablix data region, set the sort expression for the data region or for each group, including the details group.</span></span> <span data-ttu-id="6bb6c-106">테이블릭스 데이터 영역에 하나의 세부 정보 그룹만 있는 경우 데이터 영역이나 세부 정보 그룹에서 쿼리로 정렬 식을 정의할 수 있으며 모두 동일한 결과를 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6bb6c-106">If you have only one details group in a tablix data region, you can define a sort expression in the query, on the data region, or on the details group and they all have the same effect.</span></span>  
  
-   <span data-ttu-id="6bb6c-107">차트 데이터 영역에서는 범주 및 계열 그룹에 대한 정렬 식을 설정하여 각 그룹에 대한 정렬 순서를 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="6bb6c-107">In a chart data region, set the sort expression for the Category and Series groups to control the sort order for each group.</span></span> <span data-ttu-id="6bb6c-108">차트 범례에서 색 순서는 범주 그룹의 데이터 요소에 대한 정렬 식으로 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="6bb6c-108">The order for colors in a chart legend is determined by the sort expression for the data points in the Category group.</span></span>  
  
-   <span data-ttu-id="6bb6c-109">계기 데이터 영역에서는 범위에 상대적인 단일 값이 계기에 표시되므로 일반적으로 데이터를 정렬하지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6bb6c-109">In a gauge data region, you do not typically need to sort data because the gauge displays a single value relative to a range.</span></span> <span data-ttu-id="6bb6c-110">계기에서 데이터를 정렬해야 하는 경우 그룹을 먼저 정의한 다음 그룹에 대한 정렬 식을 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6bb6c-110">If you do need sort data in a gauge, you must first define a group, and then set the sort expression for the group.</span></span>  
  
 <span data-ttu-id="6bb6c-111">자세한 내용은 [데이터 필터링, 그룹화 및 정렬&#40;보고서 작성기 및 SSRS&#41;](filter-group-and-sort-data-report-builder-and-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6bb6c-111">For more information, see [Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;](filter-group-and-sort-data-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="6bb6c-112">테이블릭스 데이터 영역의 경우 열 머리글 위쪽에 대화형 정렬 단추를 추가하면 사용자가 그룹 또는 정보 행의 정렬 순서를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6bb6c-112">For a tablix data region, you can also add an interactive sort button to the top of a column header to provide the user with the ability to change the sort order of groups or detail rows.</span></span> <span data-ttu-id="6bb6c-113">자세한 내용은 [대화형 정렬&#40;보고서 작성기 및 SSRS&#41;](interactive-sort-report-builder-and-ssrs.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6bb6c-113">For more information, see [Interactive Sort &#40;Report Builder and SSRS&#41;](interactive-sort-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-sort-data-in-a-tablix-data-region"></a><span data-ttu-id="6bb6c-114">테이블릭스 데이터 영역에서 데이터를 정렬하려면</span><span class="sxs-lookup"><span data-stu-id="6bb6c-114">To sort data in a Tablix data region</span></span>  
  
1.  <span data-ttu-id="6bb6c-115">디자인 화면에서 행 핸들을 마우스 오른쪽 단추로 클릭한 다음 **테이블릭스 속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6bb6c-115">On the design surface, right-click a row handle, and then click **Tablix Properties**.</span></span>  
  
2.  <span data-ttu-id="6bb6c-116">**정렬**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6bb6c-116">Click **Sorting**.</span></span>  
  
3.  <span data-ttu-id="6bb6c-117">각 정렬 식에 대해 다음 단계를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="6bb6c-117">For each sort expression, follow these steps:</span></span>  
  
    1.  <span data-ttu-id="6bb6c-118">**추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6bb6c-118">Click **Add**.</span></span>  
  
    2.  <span data-ttu-id="6bb6c-119">데이터를 정렬할 식을 입력하거나 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6bb6c-119">Type or select an expression by which to sort the data.</span></span>  
  
    3.  <span data-ttu-id="6bb6c-120">**순서** 열 드롭다운 목록에서 각 식에 대한 정렬 방향을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6bb6c-120">From the **Order** column drop-down list, choose the sort direction for each expression.</span></span> <span data-ttu-id="6bb6c-121">**A-Z** 를 선택하면 식이 오름차순으로 정렬되고</span><span class="sxs-lookup"><span data-stu-id="6bb6c-121">**A-Z** sorts the expression in ascending order.</span></span> <span data-ttu-id="6bb6c-122">**Z-A** 를 선택하면 식이 내림차순으로 정렬됩니다.</span><span class="sxs-lookup"><span data-stu-id="6bb6c-122">**Z-A** sorts the expression in descending order.</span></span>  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-sort-values-in-a-group-including-the-details-group-for-a-tablix"></a><span data-ttu-id="6bb6c-123">테이블릭스에 대해 세부 정보 그룹을 포함한 그룹 내 값을 정렬하려면</span><span class="sxs-lookup"><span data-stu-id="6bb6c-123">To sort values in a group, including the details group, for a Tablix</span></span>  
  
1.  <span data-ttu-id="6bb6c-124">디자인 화면에서 테이블릭스 데이터 영역을 클릭하여 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6bb6c-124">On the design surface, click in the tablix data region to select it.</span></span> <span data-ttu-id="6bb6c-125">그룹화 창에 테이블릭스 데이터 영역에 대한 행 그룹과 열 그룹이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="6bb6c-125">The Grouping pane displays the row groups and column groups for the Tablix data region.</span></span>  
  
2.  <span data-ttu-id="6bb6c-126">행 그룹 창에서 그룹 이름을 마우스 오른쪽 단추로 클릭한 다음 **그룹 편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6bb6c-126">In the Row Groups pane, right-click the group name, and then click **Edit Group**.</span></span>  
  
3.  <span data-ttu-id="6bb6c-127">**테이블릭스 그룹** 대화 상자에서 **정렬**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6bb6c-127">In the **Tablix Group** dialog box, click **Sort**.</span></span>  
  
4.  <span data-ttu-id="6bb6c-128">각 정렬 식에 대해 다음 단계를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="6bb6c-128">For each sort expression, follow these steps:</span></span>  
  
    1.  <span data-ttu-id="6bb6c-129">**추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6bb6c-129">Click **Add**.</span></span>  
  
    2.  <span data-ttu-id="6bb6c-130">데이터를 정렬할 식을 입력하거나 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6bb6c-130">Type or select an expression by which to sort the data.</span></span>  
  
    3.  <span data-ttu-id="6bb6c-131">**순서** 열 드롭다운 목록에서 각 식에 대한 정렬 방향을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6bb6c-131">From the **Order** column drop-down list, choose the sort direction for each expression.</span></span> <span data-ttu-id="6bb6c-132">**A-Z** 를 선택하면 식이 오름차순으로 정렬되고</span><span class="sxs-lookup"><span data-stu-id="6bb6c-132">**A-Z** sorts the expression in ascending order.</span></span> <span data-ttu-id="6bb6c-133">**Z-A** 를 선택하면 식이 내림차순으로 정렬됩니다.</span><span class="sxs-lookup"><span data-stu-id="6bb6c-133">**Z-A** sorts the expression in descending order.</span></span>  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-sort-x-axis-labels-in-alphabetical-order-on-a-chart"></a><span data-ttu-id="6bb6c-134">차트에서 x축 레이블을 사전순으로 정렬하려면</span><span class="sxs-lookup"><span data-stu-id="6bb6c-134">To sort x-axis labels in alphabetical order on a chart</span></span>  
  
1.  <span data-ttu-id="6bb6c-135">범주 필드 끌어 놓기 영역의 필드를 마우스 오른쪽 단추로 클릭하고 **범주 그룹 속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6bb6c-135">Right-click a field in the Category Field drop-zone and click **Category GroupProperties**.</span></span>  
  
2.  <span data-ttu-id="6bb6c-136">**범주 그룹 속성** 대화 상자에서 **정렬**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6bb6c-136">In the **Category Group Properties** dialog box, click **Sorting**.</span></span>  
  
3.  <span data-ttu-id="6bb6c-137">각 정렬 식에 대해 다음 단계를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="6bb6c-137">For each sort expression, follow these steps:</span></span>  
  
    1.  <span data-ttu-id="6bb6c-138">**추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6bb6c-138">Click **Add**.</span></span>  
  
    2.  <span data-ttu-id="6bb6c-139">그룹화 필드와 일치하는 식을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6bb6c-139">Select the expression that matches your grouping field.</span></span> <span data-ttu-id="6bb6c-140">**그룹화**를 클릭하여 그룹화 필드에 대한 식을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6bb6c-140">You can verify the expression for the grouping field by clicking **Grouping**.</span></span>  
  
    3.  <span data-ttu-id="6bb6c-141">**순서** 열 드롭다운 목록에서 각 식에 대한 정렬 방향을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6bb6c-141">From the **Order** column drop-down list, choose the sort direction for each expression.</span></span> <span data-ttu-id="6bb6c-142">**A-Z** 를 선택하면 식이 오름차순 영문자 순서로 정렬되고</span><span class="sxs-lookup"><span data-stu-id="6bb6c-142">**A-Z** sorts the expression in ascending alphabetical order.</span></span> <span data-ttu-id="6bb6c-143">**Z-A** 를 선택하면 식이 내림차순 영문자 순서로 정렬됩니다.</span><span class="sxs-lookup"><span data-stu-id="6bb6c-143">**Z-A** sorts the expression in descending alphabetical order.</span></span>  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-sort-the-data-points-in-ascending-or-descending-order-on-a-chart"></a><span data-ttu-id="6bb6c-144">차트에서 데이터 요소를 오름차순 또는 내림차순으로 정렬하려면</span><span class="sxs-lookup"><span data-stu-id="6bb6c-144">To sort the data points in ascending or descending order on a chart</span></span>  
  
1.  <span data-ttu-id="6bb6c-145">범주 필드 끌어 놓기 영역의 필드를 마우스 오른쪽 단추로 클릭하고 **범주 그룹 속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6bb6c-145">Right-click a field in the Category Field drop zone and click **Category GroupProperties**.</span></span>  
  
2.  <span data-ttu-id="6bb6c-146">**범주 그룹 속성** 대화 상자에서 **정렬**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6bb6c-146">In the **Category Group Properties** dialog box, click **Sorting**.</span></span>  
  
3.  <span data-ttu-id="6bb6c-147">각 정렬 식에 대해 다음 단계를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="6bb6c-147">For each sort expression, follow these steps:</span></span>  
  
    1.  <span data-ttu-id="6bb6c-148">**추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6bb6c-148">Click **Add**.</span></span>  
  
    2.  <span data-ttu-id="6bb6c-149">데이터 필드와 일치하는 식을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6bb6c-149">Select the expression that matches your data field.</span></span> <span data-ttu-id="6bb6c-150">대부분의 경우 `=Sum(Fields!Quantity.Value)`과 같은 집계 값입니다.</span><span class="sxs-lookup"><span data-stu-id="6bb6c-150">In most cases, this is an aggregated value, such as `=Sum(Fields!Quantity.Value)`.</span></span>  
  
    3.  <span data-ttu-id="6bb6c-151">**순서** 열 드롭다운 목록에서 각 식에 대한 정렬 방향을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6bb6c-151">From the **Order** column drop-down list, choose the sort direction for each expression.</span></span> <span data-ttu-id="6bb6c-152">**A-Z** 를 선택하면 식이 오름차순으로 정렬되고</span><span class="sxs-lookup"><span data-stu-id="6bb6c-152">**A-Z** sorts the expression in ascending order.</span></span> <span data-ttu-id="6bb6c-153">**Z-A** 를 선택하면 식이 내림차순으로 정렬됩니다.</span><span class="sxs-lookup"><span data-stu-id="6bb6c-153">**Z-A** sorts the expression in descending order.</span></span>  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-sort-data-in-ascending-or-descending-order-for-display-on-a-gauge"></a><span data-ttu-id="6bb6c-154">계기 화면에서 데이터를 오름차순 또는 내림차순으로 정렬하려면</span><span class="sxs-lookup"><span data-stu-id="6bb6c-154">To sort data in ascending or descending order for display on a gauge</span></span>  
  
1.  <span data-ttu-id="6bb6c-155">계기를 마우스 오른쪽 단추로 클릭하고 **데이터 그룹 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6bb6c-155">Right-click the gauge and click **Add Data Group**.</span></span>  
  
2.  <span data-ttu-id="6bb6c-156">필요한 경우 **계기 패널 그룹 속성** 대화 상자에서 **일반** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6bb6c-156">In the **Gauge Panel GroupProperties** dialog box, click **General** if necessary.</span></span>  
  
3.  <span data-ttu-id="6bb6c-157">**그룹 식**에서 **추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6bb6c-157">In **Group expressions**, click **Add**.</span></span>  
  
4.  <span data-ttu-id="6bb6c-158">**그룹화 대상**에서 데이터를 그룹화할 식을 입력하거나 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6bb6c-158">In **Group on**, type or select an expression by which to group the data.</span></span>  
  
5.  <span data-ttu-id="6bb6c-159">사용할 그룹 식을 모두 추가할 때까지 3-4단계를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="6bb6c-159">Repeat steps 3 and 4 until you have added all the group expressions you want to use.</span></span>  
  
6.  <span data-ttu-id="6bb6c-160">**정렬**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6bb6c-160">Click **Sorting**.</span></span>  
  
7.  <span data-ttu-id="6bb6c-161">각 정렬 식에 대해 다음 단계를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="6bb6c-161">For each sort expression, follow these steps:</span></span>  
  
    1.  <span data-ttu-id="6bb6c-162">**추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6bb6c-162">Click **Add**.</span></span>  
  
    2.  <span data-ttu-id="6bb6c-163">그룹화 필드와 일치하는 식을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6bb6c-163">Select the expression that matches your grouping field.</span></span> <span data-ttu-id="6bb6c-164">**그룹화**를 클릭하여 그룹화 필드에 대한 식을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6bb6c-164">You can verify the expression for the grouping field by clicking **Grouping**.</span></span>  
  
    3.  <span data-ttu-id="6bb6c-165">**순서** 열 드롭다운 목록에서 각 식에 대한 정렬 방향을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6bb6c-165">From the **Order** column drop-down list, choose the sort direction for each expression.</span></span> <span data-ttu-id="6bb6c-166">**A-Z** 를 선택하면 식이 오름차순으로 정렬되고</span><span class="sxs-lookup"><span data-stu-id="6bb6c-166">**A-Z** sorts the expression in ascending order.</span></span> <span data-ttu-id="6bb6c-167">**Z-A** 를 선택하면 식이 내림차순으로 정렬됩니다.</span><span class="sxs-lookup"><span data-stu-id="6bb6c-167">**Z-A** sorts the expression in descending order.</span></span>  
  
8.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
 <span data-ttu-id="6bb6c-168">계기에서 데이터를 그룹화하는 방법에 대한 자세한 내용은 [계기&#40;보고서 작성기 및 SSRS&#41;](gauges-report-builder-and-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6bb6c-168">For more information about how data is grouped in a gauge, see [Gauges &#40;Report Builder and SSRS&#41;](gauges-report-builder-and-ssrs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6bb6c-169">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6bb6c-169">See Also</span></span>  
 <span data-ttu-id="6bb6c-170">[대화 상자, 창 및 마법사에 대 한 보고서 작성기 도움말](../report-builder-help-for-dialog-boxes-panes-and-wizards.md) </span><span class="sxs-lookup"><span data-stu-id="6bb6c-170">[Report Builder Help for Dialog Boxes, Panes, and Wizards](../report-builder-help-for-dialog-boxes-panes-and-wizards.md) </span></span>  
 <span data-ttu-id="6bb6c-171">[차트 &#40;보고서 작성기 및 SSRS&#41;](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="6bb6c-171">[Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="6bb6c-172">[차트의 축 레이블 서식 지정 &#40;보고서 작성기 및 SSRS&#41;](formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="6bb6c-172">[Formatting Axis Labels on a Chart &#40;Report Builder and SSRS&#41;](formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="6bb6c-173">여러 셰이프 차트에 일관된 색 지정&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="6bb6c-173">Specify Consistent Colors across Multiple Shape Charts &#40;Report Builder and SSRS&#41;</span></span>](shape-charts-report-builder-and-ssrs.md)  
  
  
