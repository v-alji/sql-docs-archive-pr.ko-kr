---
title: 행렬 및 차트에 같은 데이터 표시(보고서 작성기) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 1262f283-9fc2-4bc1-9c79-457f7642abc7
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 7746ce1f06d4dcc67c51ddc40714f19a3ff83d51
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736084"
---
# <a name="display-the-same-data-on-a-matrix-and-a-chart-report-builder"></a><span data-ttu-id="d273d-102">행렬 및 차트에 같은 데이터 표시(보고서 작성기)</span><span class="sxs-lookup"><span data-stu-id="d273d-102">Display the Same Data on a Matrix and a Chart (Report Builder)</span></span>
  <span data-ttu-id="d273d-103">행렬 및 차트에 같은 데이터를 표시하려면 두 데이터 영역에서 같은 데이터 세트를 지정하는 속성을 설정해야 하고 필터, 그룹, 정렬 및 데이터에 대한 동일한 식도 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d273d-103">When you want to show the same data in a matrix and a chart, you must set properties on both data regions to specify the same dataset, and also the same expressions for filters, groups, sorts, and data.</span></span>  
  
 <span data-ttu-id="d273d-104">두 데이터 영역에는 동일한 데이터 상위 항목(보고서 데이터 세트)이 있으므로 행렬에 대화형 정렬 단추를 추가하여 사용자가 단추를 클릭할 때 행렬 및 차트에 대한 정렬 순서를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d273d-104">Because both data regions will have the same ancestor for data (the report dataset), you can add an interactive sort button to the matrix that, when the user clicks it, changes the sort order for both the matrix and the chart.</span></span> <span data-ttu-id="d273d-105">자세한 내용은 [테이블 또는 행렬에 대화형 정렬 추가&#40;보고서 작성기 및 SSRS&#41;](add-interactive-sort-to-a-table-or-matrix-report-builder-and-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d273d-105">For more information, see [Add Interactive Sort to a Table or Matrix &#40;Report Builder and SSRS&#41;](add-interactive-sort-to-a-table-or-matrix-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="d273d-106">행렬 열 그룹 값을 차트에 대한 범례로 사용하려면 차트의 계열 데이터에 대한 색을 지정한 다음 같은 색을 그룹 값을 표시하는 행렬 셀의 입력란 배경색으로 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d273d-106">To use the matrix column group values as a legend for the chart, you must specify the colors for the series data on the chart, and then use the same colors as the fill colors for the background of the text boxes in the matrix cell that displays the group values.</span></span> <span data-ttu-id="d273d-107">자세한 내용은 [여러 셰이프 차트에 일관된 색 지정&#40;보고서 작성기 및 SSRS&#41;](charts-report-builder-and-ssrs.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d273d-107">For more information, see [Specify Consistent Colors across Multiple Shape Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="d273d-108">보고서에 그룹 정의에 대한 그룹 값이 너무 많은 경우 런타임에 보고서가 복잡하게 표시될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d273d-108">At run-time, your report may appear cluttered if there are too many group values for your group definitions.</span></span> <span data-ttu-id="d273d-109">값을 필터링하고 그룹을 결합하거나 차트에서 그룹을 결합하는 임계값을 조정해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d273d-109">You might need to filter values, combine groups, or adjust the threshold for the chart to combine groups for you.</span></span> <span data-ttu-id="d273d-110">자세한 내용은 [동일한 데이터 세트에 여러 데이터 영역 연결하기 &#40;보고서 작성기 및 SSRS#41;](linking-multiple-data-regions-to-the-same-dataset-report-builder-and-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d273d-110">For more information, see [Linking Multiple Data Regions to the Same Dataset &#40;Report Builder and SSRS&#41;](linking-multiple-data-regions-to-the-same-dataset-report-builder-and-ssrs.md)</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-matrix-and-chart-to-display-the-same-data"></a><span data-ttu-id="d273d-111">같은 데이터를 표시하는 행렬 및 차트를 추가하려면</span><span class="sxs-lookup"><span data-stu-id="d273d-111">To add a matrix and chart to display the same data</span></span>  
  
1.  <span data-ttu-id="d273d-112">디자인 뷰에서 보고서를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="d273d-112">Open a report in design view.</span></span>  
  
2.  <span data-ttu-id="d273d-113">**삽입** 탭의 **데이터 영역** 그룹에서 **행렬**을 클릭한 다음 보고서 본문이나 보고서 본문의 사각형을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d273d-113">From the **Insert** tab, in the **Data Regions** group, click **Matrix**, and then click the report body or in a rectangle in the report body.</span></span> <span data-ttu-id="d273d-114">보고서에 행렬이 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="d273d-114">A matrix is added to the report.</span></span>  
  
3.  <span data-ttu-id="d273d-115">**삽입** 탭의 **데이터 영역** 그룹에서 **차트**를 클릭한 다음 차트 종류를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d273d-115">From the **Insert** tab, in the **Data Regions** group, click **Chart**, and then select the chart type.</span></span> <span data-ttu-id="d273d-116">보고서에 차트가 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="d273d-116">A chart is added to the report.</span></span>  
  
4.  <span data-ttu-id="d273d-117">(옵션) **삽입** 탭의 **보고서 항목** 그룹에서 **사각형**을 클릭한 다음 보고서를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d273d-117">(Optional) From the **Insert** tab, in the **Report Items** group, click **Rectangle**, and then click the report.</span></span> <span data-ttu-id="d273d-118">보고서에 사각형이 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="d273d-118">A rectangle is added to the report.</span></span> <span data-ttu-id="d273d-119">2단계와 3단계에서 만든 행렬과 차트를 이 사각형으로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="d273d-119">Drag the matrix and chart from steps 2 and 3 into the rectangle.</span></span>  
  
     <span data-ttu-id="d273d-120">사각형 컨테이너에 여러 데이터 영역을 배치하면 보고서를 볼 때 행렬과 차트의 렌더링 방식을 제어하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d273d-120">By placing multiple data regions in the rectangle container, you help control how the matrix and chart render when you view the report.</span></span>  
  
     <span data-ttu-id="d273d-121">다음 단계에서는 행렬 및 차트에 같은 데이터 세트 필드가 표시되도록 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d273d-121">In the next few steps, you will choose the same dataset field to display in the matrix and to display in the chart.</span></span>  
  
5.  <span data-ttu-id="d273d-122">보고서 데이터 창에서 행렬의 데이터 셀로 숫자 데이터 세트 필드를 끕니다.</span><span class="sxs-lookup"><span data-stu-id="d273d-122">From the Report Data pane, drag a numeric dataset field to the Data cell in the matrix.</span></span>  
  
     <span data-ttu-id="d273d-123">기본적으로 그룹 값을 계산하는 데는 Sum 집계 함수가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="d273d-123">By default, the aggregate function Sum is used for calculating the group value.</span></span> <span data-ttu-id="d273d-124">행렬의 집계 함수를 변경할 경우에는 차트의 함수도 변경해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d273d-124">If you change the aggregate function in the matrix, you must change in the chart also.</span></span>  
  
6.  <span data-ttu-id="d273d-125">행렬에서 데이터가 있는 셀을 마우스 오른쪽 단추로 클릭하고 **입력란 속성**을 클릭한 다음 **숫자**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d273d-125">In the matrix, right-click the cell with data, click **Text Box Properties**, and then click **Number**.</span></span> <span data-ttu-id="d273d-126">데이터 세트 필드 값에 적합한 형식을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d273d-126">Choose an appropriate format for the dataset field value.</span></span>  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
8.  <span data-ttu-id="d273d-127">3단계에서 선택한 같은 데이터 세트 필드를 끌어 차트의 **값** 영역에 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="d273d-127">Drag the same dataset field you chose in step 3 to the **Values** area on the chart.</span></span>  
  
9. <span data-ttu-id="d273d-128">차트에서 Y 축을 마우스 오른쪽 단추로 클릭하고 **축 속성**을 클릭한 다음 **숫자**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d273d-128">In the chart, right-click the Y axis, click **Axis Properties**, and then click **Number**.</span></span> <span data-ttu-id="d273d-129">4단계에서 선택한 것과 같은 데이터 형식을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d273d-129">Choose the same format for the data that you chose in step 4.</span></span>  
  
10. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
     <span data-ttu-id="d273d-130">다음 단계에서는 행렬 행 그룹 및 차트 계열 그룹을 같은 식으로 설정하고 차트 계열 그룹에 대한 정렬 순서도 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="d273d-130">In the next few steps, you will set the matrix row group and the chart series group to the same expression, and also set the sort order for the chart series group.</span></span>  
  
11. <span data-ttu-id="d273d-131">보고서 데이터 창에서 행렬 행에 대해 그룹화할 데이터 세트 필드를 행 그룹 창으로 끌어옵니다.</span><span class="sxs-lookup"><span data-stu-id="d273d-131">From the Report Data pane, drag the dataset field that you want to group by for matrix rows to the Row Groups pane.</span></span>  
  
     <span data-ttu-id="d273d-132">기본적으로 행렬 행 그룹은 그룹 식과 동일한 정렬 식을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="d273d-132">By default, the matrix row group adds a sort expression that is the same as the group expression.</span></span>  
  
12. <span data-ttu-id="d273d-133">9단계에서 사용한 것과 같은 데이터 세트 필드를 끌어 차트의 **계열 그룹** 영역에 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="d273d-133">Drag the same dataset field that you used in step 9 to the **Series Groups** area for the chart.</span></span>  
  
13. <span data-ttu-id="d273d-134">**계열 그룹** 영역에서 해당 그룹을 마우스 오른쪽 단추로 클릭한 다음 **계열 그룹 속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d273d-134">Right-click the group in the **Series Groups** area, and then click **Series Group Properties**.</span></span>  
  
14. <span data-ttu-id="d273d-135">**정렬**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d273d-135">Click **Sorting**.</span></span>  
  
15. <span data-ttu-id="d273d-136">**추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d273d-136">Click **Add**.</span></span> <span data-ttu-id="d273d-137">새로운 행이 정렬 식 표에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="d273d-137">A new row appears in the sort expressions grid.</span></span>  
  
16. <span data-ttu-id="d273d-138">**정렬 기준**의 드롭다운 목록에서 9단계에서 그룹화할 대상으로 선택했던 데이터 세트 필드를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d273d-138">In **Sort by**, from the drop-down list, choose the dataset field that you chose to group by in step 9.</span></span>  
  
17. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
     <span data-ttu-id="d273d-139">다음 단계에서는 행렬 열 그룹 및 차트 범주 그룹을 같은 식으로 설정하고 차트 범주 그룹에 대한 정렬 순서도 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="d273d-139">In the next few steps, you will set the matrix column group and the chart category group to the same expression, and also set the sort order for the chart category group.</span></span>  
  
18. <span data-ttu-id="d273d-140">보고서 데이터 창에서 행렬 열에 대한 그룹화할 데이터 세트 필드를 열 그룹 창으로 끌어옵니다.</span><span class="sxs-lookup"><span data-stu-id="d273d-140">From the Report Data pane, drag the dataset field that you want to group by for matrix columns to the Column Groups pane.</span></span>  
  
     <span data-ttu-id="d273d-141">기본적으로 행렬 열 그룹은 그룹 식과 동일한 정렬 식을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="d273d-141">By default, the matrix column group adds a sort expression that is the same as the group expression.</span></span>  
  
19. <span data-ttu-id="d273d-142">16단계에서 사용한 것과 같은 데이터 세트 필드를 끌어 차트의 **범주 그룹** 영역에 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="d273d-142">Drag the same dataset field that you used in step 16 to the **Category Groups** area for the chart.</span></span>  
  
20. <span data-ttu-id="d273d-143">**범주 그룹** 영역에서 그룹을 마우스 오른쪽 단추로 클릭한 다음 **범주 그룹 속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d273d-143">Right-click the group in the **CategoryGroups** area, and then click **Category Group Properties**.</span></span>  
  
21. <span data-ttu-id="d273d-144">**정렬**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d273d-144">Click **Sorting**.</span></span>  
  
22. <span data-ttu-id="d273d-145">**추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d273d-145">Click **Add**.</span></span> <span data-ttu-id="d273d-146">새로운 행이 정렬 식 표에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="d273d-146">A new row appears in the sort expressions grid.</span></span>  
  
23. <span data-ttu-id="d273d-147">**정렬 기준**의 드롭다운 목록에서 16단계에서 그룹화할 대상으로 선택했던 데이터 세트 필드를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d273d-147">In **Sort by**, from the drop-down list, choose the dataset field that you chose to group by in step 16.</span></span>  
  
24. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
25. <span data-ttu-id="d273d-148">결과를 미리 봅니다.</span><span class="sxs-lookup"><span data-stu-id="d273d-148">Preview the result.</span></span> <span data-ttu-id="d273d-149">행렬 행 및 열 그룹에 차트 계열 및 범주 그룹과 같은 데이터가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d273d-149">The matrix row and column groups display the same data as the chart series and category groups.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d273d-150">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d273d-150">See Also</span></span>  
 <span data-ttu-id="d273d-151">[동일한 데이터 세트에 여러 데이터 영역 연결&#40;보고서 작성기 및 SSRS&#41;](linking-multiple-data-regions-to-the-same-dataset-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="d273d-151">[Linking Multiple Data Regions to the Same Dataset &#40;Report Builder and SSRS&#41;](linking-multiple-data-regions-to-the-same-dataset-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="d273d-152">[데이터 세트 필터, 데이터 영역 필터 및 그룹 필터 추가&#40;보고서 작성기 및 SSRS&#41;](add-dataset-filters-data-region-filters-and-group-filters.md) </span><span class="sxs-lookup"><span data-stu-id="d273d-152">[Add Dataset Filters, Data Region Filters, and Group Filters &#40;Report Builder and SSRS&#41;](add-dataset-filters-data-region-filters-and-group-filters.md) </span></span>  
 <span data-ttu-id="d273d-153">[&#40;보고서 작성기 및 SSRS를 나열&#41;](tables-matrices-and-lists-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="d273d-153">[Lists &#40;Report Builder and SSRS&#41;](tables-matrices-and-lists-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="d273d-154">차트&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="d273d-154">Charts &#40;Report Builder and SSRS&#41;</span></span>](charts-report-builder-and-ssrs.md)  
  
  
