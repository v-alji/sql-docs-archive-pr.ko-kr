---
title: '7 단원: 측정값 만들기 | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 01bd2ad7-09b7-49ae-ad80-83f25da301aa
author: minewiskan
ms.author: owend
ms.openlocfilehash: d89ea5c847276c7a34b4fc800d8bed7b9cd8ad34
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649773"
---
# <a name="lesson-7-create-measures"></a><span data-ttu-id="0bd70-102">7단원: 측정값 만들기</span><span class="sxs-lookup"><span data-stu-id="0bd70-102">Lesson 7: Create Measures</span></span>
  <span data-ttu-id="0bd70-103">이 단원에서는 모델에 포함할 측정값을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0bd70-103">In this lesson, you will create measures to be included in your model.</span></span> <span data-ttu-id="0bd70-104">이전 단원에서 만든 계산 열과 마찬가지로 측정값은 기본적으로 DAX 수식을 사용해 만든 계산입니다.</span><span class="sxs-lookup"><span data-stu-id="0bd70-104">Similar to the calculated columns you created in the previous lesson, a measure is essentially a calculation created using a DAX formula.</span></span> <span data-ttu-id="0bd70-105">그러나 계산 열과는 달리 측정값은 사용자가 선택한 *필터*를 기반으로 계산됩니다. 피벗 테이블의 행 레이블 필드에 추가된 특정 열이나 슬라이서를 예로 들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0bd70-105">However, unlike calculated columns, measures are evaluated based on a user selected *filter*; for example, a particular column or slicer added to the Row Labels field in a PivotTable.</span></span>   <span data-ttu-id="0bd70-106">그러면 필터의 각 셀에 대한 값이 적용된 측정값으로 계산됩니다.</span><span class="sxs-lookup"><span data-stu-id="0bd70-106">A value for each cell in the filter is then calculated by the applied measure.</span></span> <span data-ttu-id="0bd70-107">측정값은 숫자 데이터에 대해 동적 계산을 수행하기 위해 대부분의 테이블 형식 모델에 포함할 수 있는 강력하고 유연한 계산입니다.</span><span class="sxs-lookup"><span data-stu-id="0bd70-107">Measures are powerful, flexible calculations that you will want to include in almost all tabular models, to perform dynamic calculations on numerical data.</span></span> <span data-ttu-id="0bd70-108">자세한 내용은 [측정값&#40;SSAS 테이블 형식&#41;](tabular-models/measures-ssas-tabular.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0bd70-108">To learn more, see [Measures &#40;SSAS Tabular&#41;](tabular-models/measures-ssas-tabular.md).</span></span>  
  
 <span data-ttu-id="0bd70-109">측정값을 만들려면 측정값 표를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="0bd70-109">To create measures, you will use the Measure Grid.</span></span> <span data-ttu-id="0bd70-110">기본적으로 각 테이블에는 빈 측정값 표가 들어 있지만 일반적으로 모든 테이블에 대해 측정값을 만들지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0bd70-110">By default, each table has an empty measure grid; however, you typically will not create measures for every table.</span></span> <span data-ttu-id="0bd70-111">측정값 표는 모델 디자이너의 데이터 보기에서 테이블 아래에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="0bd70-111">The Measure Grid appears below a table in the model designer when in Data View.</span></span> <span data-ttu-id="0bd70-112">테이블에 대한 측정값 표를 숨기거나 표시하려면 **테이블** 메뉴를 클릭한 다음 **측정값 표 표시**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0bd70-112">To hide or show the measure grid for a table, click the **Table** menu, and then click **Show Measure Grid**.</span></span>  
  
 <span data-ttu-id="0bd70-113">측정값 표에서 빈 셀을 클릭한 다음 수식 입력줄에 DAX 수식을 입력하여 측정값을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0bd70-113">You can create a measure by clicking on an empty cell in the measure grid, and then typing a DAX formula in the formula bar.</span></span> <span data-ttu-id="0bd70-114">Enter 키를 눌러 수식을 완성하면 셀에 측정값이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="0bd70-114">When you click ENTER to complete the formula, the measure will then appear in the cell.</span></span> <span data-ttu-id="0bd70-115">열을 클릭한 후 도구 모음에서 자동 합계 단추(**∑**)를 클릭하여 표준 집계 함수로 측정값을 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0bd70-115">You can also create measures using a standard aggregation function by clicking on a column, and then clicking on the AutoSum button (**∑**) on the toolbar.</span></span> <span data-ttu-id="0bd70-116">자동 합계 기능을 이용해 만든 측정값은 해당 열 바로 아래에 있는 측정값 표 셀에 표시되지만 필요하면 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0bd70-116">Measures created using the AutoSum feature will appear in the measure grid cell directly beneath the column, but can be moved if necessary.</span></span>  
  
 <span data-ttu-id="0bd70-117">이 단원에서는 수식 입력줄에 DAX 수식을 입력하는 방법과 자동 합계 기능을 이용하는 방법을 모두 사용해 측정값을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0bd70-117">In this lesson, you will create measures by both entering a DAX formula in the formula bar and by using the AutoSum feature.</span></span>  
  
 <span data-ttu-id="0bd70-118">이 단원을 완료하기 위한 예상 시간: **30분**</span><span class="sxs-lookup"><span data-stu-id="0bd70-118">Estimated time to complete this lesson: **30 minutes**</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="0bd70-119">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="0bd70-119">Prerequisites</span></span>  
 <span data-ttu-id="0bd70-120">이 항목은 테이블 형식 모델링 자습서에 포함되며 순서대로 완료해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0bd70-120">This topic is part of a tabular modeling tutorial, which should be completed in order.</span></span> <span data-ttu-id="0bd70-121">이 단원의 태스크를 수행하려면 이전 단원인 [6단원: 계산 열 만들기](lesson-5-create-calculated-columns.md)를 완료해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0bd70-121">Before performing the tasks in this lesson, you should have completed the previous lesson: [Lesson 6: Create Calculated Columns](lesson-5-create-calculated-columns.md).</span></span>  
  
## <a name="create-measures"></a><span data-ttu-id="0bd70-122">측정값 만들기</span><span class="sxs-lookup"><span data-stu-id="0bd70-122">Create Measures</span></span>  
  
#### <a name="to-create-a-days-current-quarter-to-date-measure-in-the-date-table"></a><span data-ttu-id="0bd70-123">날짜 테이블에서 Days Current Quarter to Date 측정값을 만들려면</span><span class="sxs-lookup"><span data-stu-id="0bd70-123">To create a Days Current Quarter to Date measure in the Date table</span></span>  
  
1.  <span data-ttu-id="0bd70-124">모델 디자이너에서 **Date** 테이블을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0bd70-124">In the model designer, click the **Date** table.</span></span>  
  
2.  <span data-ttu-id="0bd70-125">테이블 아래에 빈 측정값 표가 표시되지 않으면 **테이블** 메뉴를 클릭한 다음 **측정값 표 표시**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0bd70-125">If an empty measure grid does not already appear beneath the table, click on the **Table** menu, and then click **Show Measure Grid**.</span></span>  
  
3.  <span data-ttu-id="0bd70-126">측정값 표에서 왼쪽 위 빈 셀을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0bd70-126">In the measure grid, click the top-left empty cell.</span></span>  
  
4.  <span data-ttu-id="0bd70-127">테이블 위의 수식 입력줄에 다음 수식을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="0bd70-127">In the formula bar, above the table, type the following formula:</span></span>  
  
     `=COUNTROWS( DATESQTD( 'Date'[Date]))`  
  
     <span data-ttu-id="0bd70-128">수식 작성을 마쳤으면 Enter 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="0bd70-128">When you have finished building the formula, press ENTER.</span></span>  
  
     <span data-ttu-id="0bd70-129">이제 왼쪽 위 셀에 **Measure 1**이라는 측정값 이름과 **30**이라는 결과 값이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="0bd70-129">Notice the top-left cell now contains a measure name, **Measure 1**, followed by the result, **30**.</span></span> <span data-ttu-id="0bd70-130">측정값 이름은 수식 입력줄의 수식 앞에도 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="0bd70-130">The measure name also precedes the formula in the formula bar.</span></span>  
  
5.  <span data-ttu-id="0bd70-131">측정값의 이름을 바꾸려면 수식 입력줄에서 **measure 1**을 강조 표시 한 다음를 입력 하 `Days Current Quarter to Date` 고 enter 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="0bd70-131">To rename the measure, in the formula bar, highlight the name, **Measure  1**, then type `Days Current Quarter to Date`, and then press ENTER.</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="0bd70-132">수식 입력줄에서 수식을 입력할 때 먼저 측정값 이름을 입력한 다음 콜론(:), 공백, 수식을 차례로 입력해도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0bd70-132">When typing a formula in the formula bar, you can also first type the measure name followed by a colon (:), followed by a space, and then followed by the formula.</span></span> <span data-ttu-id="0bd70-133">이 방법을 사용하면 측정값 이름을 바꿀 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0bd70-133">Using this method, you do not have to rename the measure.</span></span>  
  
#### <a name="to-create-a-days-in-current-quarter-measure-in-the-date-table"></a><span data-ttu-id="0bd70-134">날짜 테이블에서 Days in Current Quarter 측정값을 만들려면</span><span class="sxs-lookup"><span data-stu-id="0bd70-134">To create a Days in Current Quarter measure in the Date table</span></span>  
  
1.  <span data-ttu-id="0bd70-135">모델 디자이너에서 **Date** 테이블을 활성화한 상태로 측정값 표에서 방금 만든 측정값 아래의 빈 셀을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0bd70-135">With the **Date** table still active in the model designer, in the measure grid, click the empty cell below the measure you just created.</span></span>  
  
2.  <span data-ttu-id="0bd70-136">수식 입력줄에 다음 수식을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="0bd70-136">In the formula bar, type the following formula:</span></span>  
  
     `Days in Current Quarter :=COUNTROWS( DATESBETWEEN( 'Date'[Date], STARTOFQUARTER( LASTDATE('Date'[Date])), ENDOFQUARTER('Date'[Date])))`  
  
     <span data-ttu-id="0bd70-137">이 수식에서 측정값 이름을 먼저 포함한 후 콜론(:)을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="0bd70-137">Notice in this formula you first included the measure name followed by a colon (:).</span></span>  
  
     <span data-ttu-id="0bd70-138">수식 작성을 마쳤으면 Enter 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="0bd70-138">When you have finished building the formula, press ENTER.</span></span>  
  
 <span data-ttu-id="0bd70-139">불완전한 기간과 이전 기간 간의 비교 비율을 만들 경우 경과한 기간의 비율을 고려하여 이를 이전 기간의 동일한 비율과 비교하도록 수식을 작성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0bd70-139">When creating a comparison ratio between one incomplete period and the previous period; the formula must take into account the proportion of the period that has elapsed, and compare it to the same proportion in the previous period.</span></span> <span data-ttu-id="0bd70-140">이 경우 [Days Current Quarter to Date]/[Days in Current Quarter]와 같이 수식을 작성하면 현재 기간에서 경과한 비율을 구할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0bd70-140">In this case, [Days Current Quarter to Date]/[Days in Current Quarter] gives the proportion elapsed in the current period.</span></span>  
  
#### <a name="to-create-an-internet-distinct-count-sales-order-measure-in-the-internet-sales-table"></a><span data-ttu-id="0bd70-141">인터넷 판매 테이블에서 Internet Distinct Count Sales Order 측정값을 만들려면</span><span class="sxs-lookup"><span data-stu-id="0bd70-141">To create an Internet Distinct Count Sales Order measure in the Internet Sales table</span></span>  
  
1.  <span data-ttu-id="0bd70-142">모델 디자이너에서 **Internet Sales** 테이블(탭)을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0bd70-142">In the model designer, click the **Internet Sales** table (tab).</span></span>  
  
     <span data-ttu-id="0bd70-143">측정값 표가 표시되지 않으면 **Internet Sales** 테이블(탭)을 마우스 오른쪽 단추로 클릭한 다음 **측정값 표 표시**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0bd70-143">If the measure grid does not already appear, right-click the **Internet Sales** table (tab), and then click **Show Measure Grid**.</span></span>  
  
2.  <span data-ttu-id="0bd70-144">**판매 주문 번호** 열 제목을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0bd70-144">Click on the **Sales Order Number** column heading.</span></span>  
  
3.  <span data-ttu-id="0bd70-145">도구 모음에서 자동 합계(**∑**) 단추 옆에 있는 아래쪽 화살표를 클릭한 다음 **DistinctCount**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0bd70-145">On the toolbar, click the down-arrow next to the AutoSum (**∑**) button, and then select **DistinctCount**.</span></span>  
  
     <span data-ttu-id="0bd70-146">자동 합계 기능은 DistinctCount 표준 집계 수식을 사용하여 선택된 열에 대한 측정값을 자동으로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0bd70-146">The AutoSum feature automatically creates a measure for the selected column using the DistinctCount standard aggregation formula.</span></span>  
  
     <span data-ttu-id="0bd70-147">측정값 표에서 해당 열 아래에 있는 맨 위 셀에 **Distinct Count Sales Order Number**라는 측정값 이름이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="0bd70-147">Notice the top cell below the column in the measure grid now contains a measure name, **Distinct Count Sales Order Number**.</span></span> <span data-ttu-id="0bd70-148">자동 합계 기능을 이용해 만든 측정값은 측정값 표에서 관련 열 아래에 있는 맨 위 셀에 자동으로 배치됩니다.</span><span class="sxs-lookup"><span data-stu-id="0bd70-148">Measures created using the AutoSum feature are automatically placed in the top-most cell in the measure grid below the associated column.</span></span>  
  
4.  <span data-ttu-id="0bd70-149">측정값 표에서 새 측정값을 클릭한 다음 **속성** 창의 **측정값 이름**에서 측정값 이름을 **Internet Distinct Count Sales Order**로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="0bd70-149">In the measure grid, click the new measure, and then in the **Properties** window, in **Measure Name**, rename the measure to **Internet Distinct Count Sales Order**.</span></span>  
  
#### <a name="to-create-additional-measures-in-the-internet-sales-table"></a><span data-ttu-id="0bd70-150">인터넷 판매 테이블에서 측정값을 추가로 만들려면</span><span class="sxs-lookup"><span data-stu-id="0bd70-150">To create additional measures in the Internet Sales table</span></span>  
  
1.  <span data-ttu-id="0bd70-151">자동 합계 기능을 사용하여 다음 측정값을 만들고 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="0bd70-151">By using the AutoSum feature, create and name the following measures:</span></span>  
  
    |<span data-ttu-id="0bd70-152">측정값 이름</span><span class="sxs-lookup"><span data-stu-id="0bd70-152">Measure Name</span></span>|<span data-ttu-id="0bd70-153">열</span><span class="sxs-lookup"><span data-stu-id="0bd70-153">Column</span></span>|<span data-ttu-id="0bd70-154">자동 합계(∑)</span><span class="sxs-lookup"><span data-stu-id="0bd70-154">AutoSum (∑)</span></span>|<span data-ttu-id="0bd70-155">수식</span><span class="sxs-lookup"><span data-stu-id="0bd70-155">Formula</span></span>|  
    |------------------|------------|-------------------|-------------|  
    |<span data-ttu-id="0bd70-156">Internet Order Lines Count</span><span class="sxs-lookup"><span data-stu-id="0bd70-156">Internet Order Lines Count</span></span>|<span data-ttu-id="0bd70-157">Sales Order Line Number</span><span class="sxs-lookup"><span data-stu-id="0bd70-157">Sales Order Line Number</span></span>|<span data-ttu-id="0bd70-158">개수</span><span class="sxs-lookup"><span data-stu-id="0bd70-158">Count</span></span>|<span data-ttu-id="0bd70-159">=COUNT([Sales Order Line Number])</span><span class="sxs-lookup"><span data-stu-id="0bd70-159">=COUNT([Sales Order Line Number])</span></span>|  
    |<span data-ttu-id="0bd70-160">Internet Total Units</span><span class="sxs-lookup"><span data-stu-id="0bd70-160">Internet Total Units</span></span>|<span data-ttu-id="0bd70-161">Order Quantity</span><span class="sxs-lookup"><span data-stu-id="0bd70-161">Order Quantity</span></span>|<span data-ttu-id="0bd70-162">Sum</span><span class="sxs-lookup"><span data-stu-id="0bd70-162">Sum</span></span>|<span data-ttu-id="0bd70-163">=SUM([Order Quantity])</span><span class="sxs-lookup"><span data-stu-id="0bd70-163">=SUM([Order Quantity])</span></span>|  
    |<span data-ttu-id="0bd70-164">Internet Total Discount Amount</span><span class="sxs-lookup"><span data-stu-id="0bd70-164">Internet Total Discount Amount</span></span>|<span data-ttu-id="0bd70-165">Discount Amount</span><span class="sxs-lookup"><span data-stu-id="0bd70-165">Discount Amount</span></span>|<span data-ttu-id="0bd70-166">Sum</span><span class="sxs-lookup"><span data-stu-id="0bd70-166">Sum</span></span>|<span data-ttu-id="0bd70-167">=SUM([Discount Amount])</span><span class="sxs-lookup"><span data-stu-id="0bd70-167">=SUM([Discount Amount])</span></span>|  
    |<span data-ttu-id="0bd70-168">Internet Total Product Cost</span><span class="sxs-lookup"><span data-stu-id="0bd70-168">Internet Total Product Cost</span></span>|<span data-ttu-id="0bd70-169">Total Product Cost</span><span class="sxs-lookup"><span data-stu-id="0bd70-169">Total Product Cost</span></span>|<span data-ttu-id="0bd70-170">Sum</span><span class="sxs-lookup"><span data-stu-id="0bd70-170">Sum</span></span>|<span data-ttu-id="0bd70-171">=SUM([Total Product Cost])</span><span class="sxs-lookup"><span data-stu-id="0bd70-171">=SUM([Total Product Cost])</span></span>|  
    |<span data-ttu-id="0bd70-172">Internet Total Sales</span><span class="sxs-lookup"><span data-stu-id="0bd70-172">Internet Total Sales</span></span>|<span data-ttu-id="0bd70-173">Sales Amount</span><span class="sxs-lookup"><span data-stu-id="0bd70-173">Sales Amount</span></span>|<span data-ttu-id="0bd70-174">Sum</span><span class="sxs-lookup"><span data-stu-id="0bd70-174">Sum</span></span>|<span data-ttu-id="0bd70-175">=SUM([Sales Amount])</span><span class="sxs-lookup"><span data-stu-id="0bd70-175">=SUM([Sales Amount])</span></span>|  
    |<span data-ttu-id="0bd70-176">Internet Total Margin</span><span class="sxs-lookup"><span data-stu-id="0bd70-176">Internet Total Margin</span></span>|<span data-ttu-id="0bd70-177">Margin</span><span class="sxs-lookup"><span data-stu-id="0bd70-177">Margin</span></span>|<span data-ttu-id="0bd70-178">Sum</span><span class="sxs-lookup"><span data-stu-id="0bd70-178">Sum</span></span>|<span data-ttu-id="0bd70-179">=SUM([Margin])</span><span class="sxs-lookup"><span data-stu-id="0bd70-179">=SUM([Margin])</span></span>|  
    |<span data-ttu-id="0bd70-180">Internet Total Tax Amt</span><span class="sxs-lookup"><span data-stu-id="0bd70-180">Internet Total Tax Amt</span></span>|<span data-ttu-id="0bd70-181">Tax Amt</span><span class="sxs-lookup"><span data-stu-id="0bd70-181">Tax Amt</span></span>|<span data-ttu-id="0bd70-182">Sum</span><span class="sxs-lookup"><span data-stu-id="0bd70-182">Sum</span></span>|<span data-ttu-id="0bd70-183">=SUM([Tax Amt])</span><span class="sxs-lookup"><span data-stu-id="0bd70-183">=SUM([Tax Amt])</span></span>|  
    |<span data-ttu-id="0bd70-184">Internet Total Freight</span><span class="sxs-lookup"><span data-stu-id="0bd70-184">Internet Total Freight</span></span>|<span data-ttu-id="0bd70-185">Freight</span><span class="sxs-lookup"><span data-stu-id="0bd70-185">Freight</span></span>|<span data-ttu-id="0bd70-186">Sum</span><span class="sxs-lookup"><span data-stu-id="0bd70-186">Sum</span></span>|<span data-ttu-id="0bd70-187">=SUM([Freight])</span><span class="sxs-lookup"><span data-stu-id="0bd70-187">=SUM([Freight])</span></span>|  
  
2.  <span data-ttu-id="0bd70-188">측정값 표에서 빈 셀을 클릭하고 수식 입력줄을 사용하여 다음과 같이 측정값을 만들고 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="0bd70-188">By clicking on an empty cell in the measure grid, and by using the formula bar, create and name the following measures:</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="0bd70-189">다음 측정값에서 뒤에 나오는 측정값의 수식은 이전 측정값을 참조하므로 순서대로 측정값을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0bd70-189">You must create the following measures in order; formulas in later measures refer to earlier measures.</span></span>  
  
    |<span data-ttu-id="0bd70-190">측정값 이름</span><span class="sxs-lookup"><span data-stu-id="0bd70-190">Measure Name</span></span>|<span data-ttu-id="0bd70-191">수식</span><span class="sxs-lookup"><span data-stu-id="0bd70-191">Formula</span></span>|  
    |------------------|-------------|  
    |<span data-ttu-id="0bd70-192">Internet Previous Quarter Margin</span><span class="sxs-lookup"><span data-stu-id="0bd70-192">Internet Previous Quarter Margin</span></span>|<span data-ttu-id="0bd70-193">=CALCULATE([Internet Total Margin],PREVIOUSQUARTER('Date'[Date]))</span><span class="sxs-lookup"><span data-stu-id="0bd70-193">=CALCULATE([Internet Total Margin],PREVIOUSQUARTER('Date'[Date]))</span></span>|  
    |<span data-ttu-id="0bd70-194">Internet Current Quarter Margin</span><span class="sxs-lookup"><span data-stu-id="0bd70-194">Internet Current Quarter Margin</span></span>|<span data-ttu-id="0bd70-195">=TOTALQTD([Internet Total Margin],'Date'[Date])</span><span class="sxs-lookup"><span data-stu-id="0bd70-195">=TOTALQTD([Internet Total Margin],'Date'[Date])</span></span>|  
    |<span data-ttu-id="0bd70-196">Internet Previous Quarter Margin Proportion to QTD</span><span class="sxs-lookup"><span data-stu-id="0bd70-196">Internet Previous Quarter Margin Proportion to QTD</span></span>|<span data-ttu-id="0bd70-197">=[Internet Previous Quarter Margin]\*([Days Current Quarter to Date]/[Days In Current Quarter])</span><span class="sxs-lookup"><span data-stu-id="0bd70-197">=[Internet Previous Quarter Margin]\*([Days Current Quarter to Date]/[Days In Current Quarter])</span></span>|  
    |<span data-ttu-id="0bd70-198">Internet Previous Quarter Sales</span><span class="sxs-lookup"><span data-stu-id="0bd70-198">Internet Previous Quarter Sales</span></span>|<span data-ttu-id="0bd70-199">=CALCULATE([Internet Total Sales],PREVIOUSQUARTER('Date'[Date]))</span><span class="sxs-lookup"><span data-stu-id="0bd70-199">=CALCULATE([Internet Total Sales],PREVIOUSQUARTER('Date'[Date]))</span></span>|  
    |<span data-ttu-id="0bd70-200">Internet Current Quarter Sales</span><span class="sxs-lookup"><span data-stu-id="0bd70-200">Internet Current Quarter Sales</span></span>|<span data-ttu-id="0bd70-201">=TOTALQTD([Internet Total Sales],'Date'[Date])</span><span class="sxs-lookup"><span data-stu-id="0bd70-201">=TOTALQTD([Internet Total Sales],'Date'[Date])</span></span>|  
    |<span data-ttu-id="0bd70-202">Internet Previous Quarter Sales Proportion to QTD</span><span class="sxs-lookup"><span data-stu-id="0bd70-202">Internet Previous Quarter Sales Proportion to QTD</span></span>|<span data-ttu-id="0bd70-203">=[Internet Previous Quarter Sales]\*([Days Current Quarter to Date]/[Days In Current Quarter])</span><span class="sxs-lookup"><span data-stu-id="0bd70-203">=[Internet Previous Quarter Sales]\*([Days Current Quarter to Date]/[Days In Current Quarter])</span></span>|  
  
 <span data-ttu-id="0bd70-204">인터넷 판매 테이블에서 만든 측정값을 사용하여 사용자가 선택한 필터로 필터링된 항목의 매출, 비용, 이익률 등의 중요 회계 데이터를 분석할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0bd70-204">Measures created for the Internet Sales table can be used to analyze critical financial data such as sales, costs, and profit margin for items defined by the user selected filter.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="0bd70-205">다음 단계</span><span class="sxs-lookup"><span data-stu-id="0bd70-205">Next Step</span></span>  
 <span data-ttu-id="0bd70-206">이 자습서를 계속하려면 다음 단원인 [8단원: 핵심 성과 지표 만들기](lesson-7-create-key-performance-indicators.md)로 이동하세요.</span><span class="sxs-lookup"><span data-stu-id="0bd70-206">To continue this tutorial, go to the next lesson: [Lesson 8: Create Key Performance Indicators](lesson-7-create-key-performance-indicators.md).</span></span>  
  
  
