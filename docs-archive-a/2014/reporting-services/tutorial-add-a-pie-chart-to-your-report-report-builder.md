---
title: '자습서: 보고서에 원형 차트 추가(보고서 작성기) | Microsoft Docs'
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: eaadf7bf-c312-428a-b214-0a1fbf959c3f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 318370b185dcd75a8c3c54be49c47756bad5f3c9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735951"
---
# <a name="tutorial-add-a-pie-chart-to-your-report-report-builder"></a><span data-ttu-id="53728-102">자습서: 보고서에 원형 차트 추가(보고서 작성기)</span><span class="sxs-lookup"><span data-stu-id="53728-102">Tutorial: Add a Pie Chart to Your Report (Report Builder)</span></span>
  <span data-ttu-id="53728-103">원형 차트와 도넛형 차트는 데이터를 전체에 대한 비율로 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="53728-103">Pie charts and doughnut charts display data as a proportion of the whole.</span></span> <span data-ttu-id="53728-104">원형 차트는 그룹 간의 비교에 가장 일반적으로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="53728-104">Pie charts are most commonly used to make comparisons between groups.</span></span> <span data-ttu-id="53728-105">원형 및 도넛형 차트는 피라미드형 및 깔때기형 차트와 마찬가지로 셰이프 차트라고 하는 차트 그룹으로 이루어집니다.</span><span class="sxs-lookup"><span data-stu-id="53728-105">Pie and doughnut charts, along with pyramid and funnel charts, constitute a group of charts known as shape charts.</span></span> <span data-ttu-id="53728-106">셰이프 차트에는 축이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="53728-106">Shape charts have no axes.</span></span> <span data-ttu-id="53728-107">셰이프 차트에 숫자 필드를 배치하면 차트에서 각각의 값이 전체 합계에 대해 차지하는 비율이 계산됩니다.</span><span class="sxs-lookup"><span data-stu-id="53728-107">When a numeric field is dropped on a shape chart, the chart calculates the percentage of each value to the total.</span></span>  
  
 <span data-ttu-id="53728-108">원형 차트에 데이터 요소가 너무 많으면 데이터 요소 레이블이 복잡해져서 가독성이 떨어질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="53728-108">If there are too many data points on a pie chart, your data point labels might be too crowded to read.</span></span> <span data-ttu-id="53728-109">이런 경우에는 꺾은선형 차트를 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="53728-109">In that case, consider using a line chart.</span></span> <span data-ttu-id="53728-110">원형 차트는 데이터를 몇 개의 데이터 요소로 집계한 후에만 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="53728-110">Consider using pie charts only after you have aggregated your data into a few data points.</span></span>  
  
 <span data-ttu-id="53728-111">다음 그림에서는 만들려는 원형 차트를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="53728-111">The following illustration shows the pie chart you will create.</span></span>  
  
 <span data-ttu-id="53728-112">![rs_TutorialPieChartConcave](../../2014/tutorials/media/rs-tutorialpiechartconcave.gif "rs_TutorialPieChartConcave")</span><span class="sxs-lookup"><span data-stu-id="53728-112">![rs_TutorialPieChartConcave](../../2014/tutorials/media/rs-tutorialpiechartconcave.gif "rs_TutorialPieChartConcave")</span></span>  
  
##  <a name="what-you-will-learn"></a><a name="BackToTop"></a><span data-ttu-id="53728-113">학습 내용</span><span class="sxs-lookup"><span data-stu-id="53728-113">What You Will Learn</span></span>  
 <span data-ttu-id="53728-114">이 자습서에서는 다음 작업 방법을 배웁니다.</span><span class="sxs-lookup"><span data-stu-id="53728-114">In this tutorial, you will learn how to:</span></span>  
  
1.  [<span data-ttu-id="53728-115">차트 마법사에서 원형 차트 만들기</span><span class="sxs-lookup"><span data-stu-id="53728-115">Create a Pie Chart from the Chart Wizard</span></span>](#Chart)  
  
2.  [<span data-ttu-id="53728-116">차트 종류 선택</span><span class="sxs-lookup"><span data-stu-id="53728-116">Choose the Chart Type</span></span>](#ChartType)  
  
3.  [<span data-ttu-id="53728-117">각 조각에 백분율 표시</span><span class="sxs-lookup"><span data-stu-id="53728-117">Display Percentages in Each Slice</span></span>](#Percentages)  
  
4.  [<span data-ttu-id="53728-118">작은 조각들을 하나의 조각으로 결합</span><span class="sxs-lookup"><span data-stu-id="53728-118">Combine Small Slices into One Slice</span></span>](#CombineSlices)  
  
5.  [<span data-ttu-id="53728-119">그리기 효과 사용자 지정</span><span class="sxs-lookup"><span data-stu-id="53728-119">Customize the Drawing Effect</span></span>](#DrawingEffect)  
  
6.  [<span data-ttu-id="53728-120">보고서 제목 추가</span><span class="sxs-lookup"><span data-stu-id="53728-120">Add a Report Title</span></span>](#Title)  
  
7.  [<span data-ttu-id="53728-121">보고서 저장</span><span class="sxs-lookup"><span data-stu-id="53728-121">Save the Report</span></span>](#Save)  
  
> [!NOTE]  
>  <span data-ttu-id="53728-122">이 자습서에서 마법사의 단계는 두 개의 절차로 통합됩니다.</span><span class="sxs-lookup"><span data-stu-id="53728-122">In this tutorial, the steps for the wizard are consolidated into two procedures.</span></span> <span data-ttu-id="53728-123">보고서 서버를 찾고 데이터 원본을 추가하고 데이터 세트를 추가하는 방법에 대한 단계별 지침은 이 시리즈의 첫 번째 자습서인 [자습서: 기본 테이블 보고서 만들기&#40;보고서 작성기&#41;](../reporting-services/tutorial-creating-a-basic-table-report-report-builder.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="53728-123">For step-by-step instructions about how to browse to a report server, add a data source, and add a dataset, see the first tutorial in this series: [Tutorial: Creating a Basic Table Report &#40;Report Builder&#41;](../reporting-services/tutorial-creating-a-basic-table-report-report-builder.md).</span></span>  
  
 <span data-ttu-id="53728-124">이 자습서에 소요되는 예상 시간: 10분</span><span class="sxs-lookup"><span data-stu-id="53728-124">Estimated time to complete this tutorial: 10 minutes</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="53728-125">요구 사항</span><span class="sxs-lookup"><span data-stu-id="53728-125">Requirements</span></span>  
 <span data-ttu-id="53728-126">요구 사항에 대한 자세한 내용은 [자습서의 필수 조건&#40;보고서 작성기&#41;](../reporting-services/report-builder-tutorials.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="53728-126">For more information about requirements, see [Prerequisites for Tutorials &#40;Report Builder&#41;](../reporting-services/report-builder-tutorials.md).</span></span>  
  
##  <a name="1-create-a-pie-chart-from-the-chart-wizard"></a><a name="Chart"></a><span data-ttu-id="53728-127">1. 차트 마법사에서 원형 차트 만들기</span><span class="sxs-lookup"><span data-stu-id="53728-127">1. Create a Pie Chart from the Chart Wizard</span></span>  
 <span data-ttu-id="53728-128">시작 대화 상자에서 차트 마법사를 사용하여 포함된 데이터 세트을 만들고, 공유 데이터 원본을 선택하고, 원형 차트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="53728-128">From the Getting Started dialog box, use the Chart Wizard to create an embedded dataset, choose a shared data source, and create a pie chart.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="53728-129">이 자습서의 쿼리에는 데이터 값이 포함되어 있으므로 외부 데이터 원본이 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="53728-129">In this tutorial, the query contains the data values, so that it does not need an external data source.</span></span> <span data-ttu-id="53728-130">따라서 쿼리가 상당히 길어집니다.</span><span class="sxs-lookup"><span data-stu-id="53728-130">This makes the query quite long.</span></span> <span data-ttu-id="53728-131">비즈니스 환경에서는 쿼리에 데이터가 포함되지 않을 것입니다.</span><span class="sxs-lookup"><span data-stu-id="53728-131">In a business environment, a query would not contain the data.</span></span> <span data-ttu-id="53728-132">이 자습서의 쿼리는 학습용으로만 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="53728-132">This is for learning purposes only.</span></span>  
  
#### <a name="to-create-a-new-chart-report"></a><span data-ttu-id="53728-133">새 차트 보고서를 만들려면</span><span class="sxs-lookup"><span data-stu-id="53728-133">To create a new chart report</span></span>  
  
1.  <span data-ttu-id="53728-134">**시작**을 클릭하고 **프로그램**, **Microsoft SQL Server 2012 보고서 작성기**를 차례로 가리킨 다음 **보고서 작성기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="53728-134">Click **Start**, point to **Programs**, point to **Microsoft SQL Server 2012 Report Builder**, and then click **Report Builder**.</span></span>  
  
     <span data-ttu-id="53728-135">시작 대화 상자가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="53728-135">The Getting Started dialog box appears.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="53728-136">시작 대화 상자가 나타나지 않으면 보고서 작성기 단추에서 **새로 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="53728-136">If the Getting Started dialog box does not appear, from the Report Builder button, click **New**.</span></span>  
  
2.  <span data-ttu-id="53728-137">왼쪽 창에 **새 보고서** 가 선택되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="53728-137">In the left pane, verify that **New Report** is selected.</span></span>  
  
3.  <span data-ttu-id="53728-138">오른쪽 창에서 **차트 마법사**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="53728-138">In the right pane, click **Chart Wizard**.</span></span>  
  
4.  <span data-ttu-id="53728-139">**데이터 세트 선택** 페이지에서 **데이터 세트 만들기**를 클릭한 후, **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="53728-139">On the **Choose a dataset** page, click **Create a dataset**, and then click **Next**.</span></span>  
  
5.  <span data-ttu-id="53728-140">**데이터 원본에 대한 연결 선택** 페이지에서 기존 데이터 원본을 선택하거나 보고서 서버를 찾아 데이터 원본을 선택하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="53728-140">On the **Choose a connection to a data source** page, select an existing data source or browse to the report server and select a data source, and then click **Next**.</span></span> <span data-ttu-id="53728-141">사용자 이름과 암호를 입력해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="53728-141">You may need to enter a user name and password.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="53728-142">적절한 권한만 가지고 있으면 선택하는 데이터 원본은 중요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="53728-142">The data source you choose is unimportant, as long as you have adequate permissions.</span></span> <span data-ttu-id="53728-143">데이터를 데이터 원본에서 가져오는 것은 아니기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="53728-143">You will not be getting data from the data source.</span></span> <span data-ttu-id="53728-144">자세한 내용은 [데이터에 연결하는 다른 방법&#40;보고서 작성기&#41;](../reporting-services/alternative-ways-to-get-a-data-connection-report-builder.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="53728-144">For more information, see [Alternative Ways to Get a Data Connection &#40;Report Builder&#41;](../reporting-services/alternative-ways-to-get-a-data-connection-report-builder.md).</span></span>  
  
6.  <span data-ttu-id="53728-145">**쿼리 디자인** 페이지에서 **텍스트로 편집**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="53728-145">On the **Design a Query** page, click **Edit as Text**.</span></span>  
  
7.  <span data-ttu-id="53728-146">쿼리 창에 다음 쿼리를 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="53728-146">Paste the following query into the query pane:</span></span>  
  
    ```  
    SELECT 'Advanced Digital Camera' AS Product, CAST(254995.21 AS money) AS Sales  
    UNION SELECT 'Slim Digital Camera' AS Product, CAST(164499.04 AS money) AS Sales  
    UNION SELECT 'SLR Digital Camera' AS Product, CAST(782176.79 AS money) AS Sales  
    UNION SELECT 'Lens Adapter' AS Product, CAST(36333.08 AS money) AS Sales  
    UNION SELECT 'Macro Zoom Lens' AS Product, CAST(40199.3 AS money) AS Sales  
    UNION SELECT 'USB Cable' AS Product, CAST(53245.5 AS money) AS Sales  
    UNION SELECT 'Independent Filmmaker Camcorder' AS Product, CAST(452288.0 AS money) AS Sales  
    UNION SELECT 'Full Frame Digital Camera' AS Product, CAST(247250.85 AS money) AS Sales  
    ```  
  
8.  <span data-ttu-id="53728-147">(옵션) 실행 단추(**!**)를 클릭하여 차트의 기반으로 사용될 데이터를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="53728-147">(Optional) Click the Run button (**!**) to see the data your chart will be based on.</span></span>  
  
9. <span data-ttu-id="53728-148">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="53728-148">Click **Next**.</span></span>  
  
##  <a name="2-choose-the-chart-type"></a><a name="ChartType"></a><span data-ttu-id="53728-149">2. 차트 종류 선택</span><span class="sxs-lookup"><span data-stu-id="53728-149">2. Choose the Chart Type</span></span>  
 <span data-ttu-id="53728-150">미리 정의된 다양한 차트 종류 중에서 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="53728-150">You can choose from a variety of predefined chart types.</span></span>  
  
#### <a name="to-add-a-pie-chart"></a><span data-ttu-id="53728-151">원형 차트를 추가하려면</span><span class="sxs-lookup"><span data-stu-id="53728-151">To add a pie chart</span></span>  
  
1.  <span data-ttu-id="53728-152">**차트 종류 선택** 페이지에서 **원형**을 클릭 하 고 **다음**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="53728-152">On the **Choose a chart type** page, click **Pie**, and then click **Next**.</span></span> <span data-ttu-id="53728-153">**차트 필드 정렬** 페이지가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="53728-153">The **Arrange chart fields** page opens.</span></span>  
  
     <span data-ttu-id="53728-154">**차트 필드 정렬** 페이지에서 Product 필드를 **범주** 창으로 끌어옵니다.</span><span class="sxs-lookup"><span data-stu-id="53728-154">On the **Arrange chart fields** page, drag the Product field to the **Categories** pane.</span></span> <span data-ttu-id="53728-155">범주는 원형 차트의 조각 수를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="53728-155">Categories define the number of slices in the pie chart.</span></span> <span data-ttu-id="53728-156">이 예제에서는 각 제품에 대해 하나씩 총 8개의 조각이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="53728-156">In this example, there will be eight slices, one for each product.</span></span>  
  
2.  <span data-ttu-id="53728-157">Sales 필드를 **값** 창으로 끌어옵니다.</span><span class="sxs-lookup"><span data-stu-id="53728-157">Drag the Sales field to the **Values** pane.</span></span> <span data-ttu-id="53728-158">Sales는 하위 범주의 판매액을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="53728-158">Sales represents the sales amount for the subcategory.</span></span> <span data-ttu-id="53728-159">차트에 각 제품의 집계가 표시되기 때문에 **값** 창에는 `[Sum(Sales)]` 이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="53728-159">The **Values** pane displays `[Sum(Sales)]` because the chart displays the aggregate for each product.</span></span>  
  
3.  <span data-ttu-id="53728-160">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="53728-160">Click **Next**.</span></span>  
  
4.  <span data-ttu-id="53728-161">스타일 **선택** 페이지의 스타일 창에서 스타일을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="53728-161">On the **Choose a style** page, in the Styles pane, select a style.</span></span>  
  
     <span data-ttu-id="53728-162">스타일은 글꼴 스타일, 색 집합 및 테두리 스타일을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="53728-162">A style specifies a font style, a set of colors, and a border style.</span></span> <span data-ttu-id="53728-163">스타일을 선택하면 미리 보기 창에 해당 스타일이 적용된 예제 차트가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="53728-163">When you select a style, the Preview pane displays a sample of the chart with that style.</span></span>  
  
5.  <span data-ttu-id="53728-164">**Finish**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="53728-164">Click **Finish**.</span></span>  
  
     <span data-ttu-id="53728-165">디자인 화면에 차트가 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="53728-165">The chart is added to the design surface.</span></span>  
  
6.  <span data-ttu-id="53728-166">차트를 클릭하여 차트 핸들을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="53728-166">Click the chart to display the chart handles.</span></span> <span data-ttu-id="53728-167">차트의 오른쪽 아래 모퉁이를 끌어 차트의 크기를 늘립니다.</span><span class="sxs-lookup"><span data-stu-id="53728-167">Drag the bottom-right corner of the chart to increase the size of the chart.</span></span> <span data-ttu-id="53728-168">보고서 디자인 화면이 차트 크기에 맞게 늘어납니다.</span><span class="sxs-lookup"><span data-stu-id="53728-168">Note that the report design surface increases in size to accommodate the chart size.</span></span>  
  
7.  <span data-ttu-id="53728-169">**실행** 을 클릭하여 보고서를 미리 봅니다.</span><span class="sxs-lookup"><span data-stu-id="53728-169">Click **Run** to preview the report.</span></span>  
  
 <span data-ttu-id="53728-170">각 제품에 대해 하나씩 총 8개 조각으로 구성된 원형 차트가 보고서에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="53728-170">The report displays the pie chart with eight slices, one for each product.</span></span> <span data-ttu-id="53728-171">각 조각의 크기는 해당 제품의 판매량을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="53728-171">The size of each slice represents the sales for that product.</span></span> <span data-ttu-id="53728-172">전체 조각 중 3개는 폭이 좁습니다.</span><span class="sxs-lookup"><span data-stu-id="53728-172">Three of the slices are quite thin.</span></span>  
  
##  <a name="3-display-percentages-in-each-slice"></a><a name="Percentages"></a><span data-ttu-id="53728-173">3. 각 조각에 백분율 표시</span><span class="sxs-lookup"><span data-stu-id="53728-173">3. Display Percentages in Each Slice</span></span>  
 <span data-ttu-id="53728-174">원형 차트의 각 조각에 원형 전체에 대한 해당 조각의 백분율을 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="53728-174">On each slice of the pie, you can display a percentage for this slice compared to the whole pie.</span></span>  
  
#### <a name="to-display-percentages-in-each-slice-of-the-pie-chart"></a><span data-ttu-id="53728-175">원형 차트의 각 조각에 백분율을 표시하려면</span><span class="sxs-lookup"><span data-stu-id="53728-175">To display percentages in each slice of the pie chart</span></span>  
  
1.  <span data-ttu-id="53728-176">보고서 디자인 뷰로 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="53728-176">Switch to report design view.</span></span>  
  
2.  <span data-ttu-id="53728-177">원형 차트를 마우스 오른쪽 단추로 클릭하고 **데이터 레이블 표시**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="53728-177">Right-click the pie chart and click **Show Data Labels**.</span></span> <span data-ttu-id="53728-178">차트에 데이터 레이블이 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="53728-178">The data labels appear on the chart.</span></span>  
  
3.  <span data-ttu-id="53728-179">레이블을 마우스 오른쪽 단추로 클릭 하 고 **계열 레이블 속성**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="53728-179">Right-click a label, and then click **Series Label Properties**.</span></span>  
  
4.  <span data-ttu-id="53728-180">레이블 데이터의 드롭다운 상자에서 **#PERCENT**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="53728-180">In Label data, from the drop-down box, select **#PERCENT**.</span></span>  
  
     <span data-ttu-id="53728-181">값을 백분율로 표시하려면 UseValueAsLabel 속성이 false여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="53728-181">To display values as percentages, the UseValueAsLabel property must be false.</span></span> <span data-ttu-id="53728-182">**동작 확인** 대화 상자에서 이 값을 설정할지 묻는 메시지가 표시되면 **예**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="53728-182">If you are prompted to set this value in the **Confirm Action** dialog, click **Yes**.</span></span>  
  
5.  <span data-ttu-id="53728-183">필드 레이블에 표시 되는 소수 자릿수를 지정 하려면 다음을 입력 `#PERCENT{Pn}` 합니다. 여기서 *n* 은 표시할 소수 자릿수입니다.</span><span class="sxs-lookup"><span data-stu-id="53728-183">(Optional) To specify how many decimal places the label shows, type `#PERCENT{Pn}` where *n* is the number of decimal places to display.</span></span> <span data-ttu-id="53728-184">예를 들어 소수 자릿수를 표시 하지 않으려면를 입력 `#PERCENT{P0}` 합니다.</span><span class="sxs-lookup"><span data-stu-id="53728-184">For example, to display no decimal places, type `#PERCENT{P0}`.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="53728-185">**계열 레이블 속성** 대화 상자의 **숫자 형식** 은 백분율 서식을 지정하는 데 영향을 주지 않고</span><span class="sxs-lookup"><span data-stu-id="53728-185">**Number Format** in the **Series Label Properties** dialog box has no effect when you format percentages.</span></span> <span data-ttu-id="53728-186">레이블의 서식을 백분율로 지정하기만 하며 각 조각이 원형 차트에서 나타내는 백분율을 계산하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="53728-186">This formats the labels as percentages, but does not calculate the percentage of the pie that each slice represents.</span></span>  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
7.  <span data-ttu-id="53728-187">**실행** 을 클릭하여 보고서를 미리 봅니다.</span><span class="sxs-lookup"><span data-stu-id="53728-187">Click **Run** to preview the report.</span></span>  
  
 <span data-ttu-id="53728-188">각 원형 조각이 전체에서 나타내는 백분율이 보고서에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="53728-188">The report displays the percentage of the whole for each pie slice.</span></span>  
  
##  <a name="4-combine-small-slices-into-one-slice"></a><a name="CombineSlices"></a><span data-ttu-id="53728-189">4. 작은 조각 들을 하나의 조각으로 결합</span><span class="sxs-lookup"><span data-stu-id="53728-189">4. Combine Small Slices into One Slice</span></span>  
 <span data-ttu-id="53728-190">원형 차트의 조각 중 3개는 폭이 좁습니다.</span><span class="sxs-lookup"><span data-stu-id="53728-190">Three of the slices in the pie are quite small.</span></span> <span data-ttu-id="53728-191">여러 개의 작은 조각을 해당 조각 모두를 나타내는 하나의 큰 조각으로 결합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="53728-191">You can combine multiple small slices into one larger slice that represents all of them.</span></span>  
  
#### <a name="to-combine-any-slices-on-the-pie-chart-smaller-than-5-percent-into-one-slice"></a><span data-ttu-id="53728-192">원형 차트에서 5% 미만의 조각을 하나의 조각으로 결합하려면</span><span class="sxs-lookup"><span data-stu-id="53728-192">To combine any slices on the pie chart smaller than 5 percent into one slice</span></span>  
  
1.  <span data-ttu-id="53728-193">보고서 디자인 뷰로 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="53728-193">Switch to report design view.</span></span>  
  
2.  <span data-ttu-id="53728-194">**보기** 탭의 **표시/숨기기** 그룹에서 **속성**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="53728-194">On the **View** tab, in the **Show/Hide** group, select **Properties**.</span></span>  
  
3.  <span data-ttu-id="53728-195">디자인 화면에서 원형 차트의 조각을 아무 것이나 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="53728-195">On the design surface, click on any slice of the pie chart.</span></span> <span data-ttu-id="53728-196">계열의 속성이 속성 창에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="53728-196">The properties for the series are displayed in the Properties pane.</span></span>  
  
4.  <span data-ttu-id="53728-197">**일반** 섹션에서 **CustomAttributes** 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="53728-197">In the **General** section, expand the **CustomAttributes** node.</span></span>  
  
5.  <span data-ttu-id="53728-198">**CollectedStyle** 속성을 **SingleSlice**로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="53728-198">Set the **CollectedStyle** property to **SingleSlice**.</span></span>  
  
6.  <span data-ttu-id="53728-199">**CollectedThreshold** 속성이 5로 설정되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="53728-199">Verify that the **CollectedThreshold** property is set to 5.</span></span>  
  
7.  <span data-ttu-id="53728-200">**CollectedThresholdUsePercent** 속성이 **True**로 설정되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="53728-200">Verify that the **CollectedThresholdUsePercent** property is set to **True**.</span></span>  
  
8.  <span data-ttu-id="53728-201">리본 메뉴의 **홈** 탭에서 **실행** 을 클릭 하 여 보고서를 미리 봅니다.</span><span class="sxs-lookup"><span data-stu-id="53728-201">On the Ribbon, on the **Home** tab, click **Run** to preview the report.</span></span>  
  
 <span data-ttu-id="53728-202">이제 범례에 "기타"라는 범주가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="53728-202">In the legend, the category "Other" now exists.</span></span> <span data-ttu-id="53728-203">새 원형 조각은 5% 미만인 모든 조각을 전체 원형의 6%를 차지하는 조각 하나로 결합합니다.</span><span class="sxs-lookup"><span data-stu-id="53728-203">The new pie slice combines all the slices that were under 5% into one slice that is 6% of the whole pie.</span></span>  
  
##  <a name="5-customize-the-drawing-effect"></a><a name="DrawingEffect"></a><span data-ttu-id="53728-204">5. 그리기 효과 사용자 지정</span><span class="sxs-lookup"><span data-stu-id="53728-204">5. Customize the Drawing Effect</span></span>  
 <span data-ttu-id="53728-205">차트 마법사에서 원형 차트의 기본 스타일은 오목 그리기 효과가 적용된 바다입니다.</span><span class="sxs-lookup"><span data-stu-id="53728-205">In the Chart Wizard, the default style for a pie chart is Ocean, which features a Concave drawing effect.</span></span> <span data-ttu-id="53728-206">마법사를 실행한 후 이러한 스타일을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="53728-206">You can change that after you run the wizard.</span></span>  
  
#### <a name="to-add-a-drawing-effect-to-the-pie-chart"></a><span data-ttu-id="53728-207">원형 차트에 그리기 효과를 추가하려면</span><span class="sxs-lookup"><span data-stu-id="53728-207">To add a drawing effect to the pie chart</span></span>  
  
1.  <span data-ttu-id="53728-208">보고서 디자인 뷰로 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="53728-208">Switch to report design view.</span></span>  
  
2.  <span data-ttu-id="53728-209">속성 창이 아직 열려 있지 않으면 **보기** 탭에서 **속성**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="53728-209">If the Properties pane is not already opened, on the **View** tab, select **Properties**.</span></span>  
  
3.  <span data-ttu-id="53728-210">원형 차트를 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="53728-210">Double-click the pie chart itself.</span></span> <span data-ttu-id="53728-211">원형 차트의 계열 속성이 속성 창에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="53728-211">The series properties for the pie chart are shown in the Properties pane.</span></span>  
  
4.  <span data-ttu-id="53728-212">속성 창에서 **CustomAttributes** 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="53728-212">In the Properties pane, expand the **CustomAttributes** node.</span></span>  
  
5.  <span data-ttu-id="53728-213">**PieDrawingStyle** 를 **소프트 edge**로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="53728-213">Set the **PieDrawingStyle** to **SoftEdge**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="53728-214">그리기 효과와 3D 효과 옵션은 함께 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="53728-214">Drawing effects and three-dimensional effects are exclusive options.</span></span> <span data-ttu-id="53728-215">차트에 3 차원 효과가 적용 되어 있으면 속성 창에서 **PieDrawingStyle** 를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="53728-215">If a chart has three-dimensional effects applied, **PieDrawingStyle** is not available on the Properties pane.</span></span>  
  
6.  <span data-ttu-id="53728-216">**실행** 을 클릭하여 보고서를 미리 봅니다.</span><span class="sxs-lookup"><span data-stu-id="53728-216">Click **Run** to preview the report.</span></span>  
  
 <span data-ttu-id="53728-217">다음 그림에서는 부드러운 가장자리 효과가 적용된 원형 차트를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="53728-217">The following illustration shows the pie chart with the soft edge effect.</span></span>  
  
 <span data-ttu-id="53728-218">![rs_TutorialPieChartSoftEdge](../../2014/tutorials/media/rs-tutorialpiechartsoftedge.gif "rs_TutorialPieChartSoftEdge")</span><span class="sxs-lookup"><span data-stu-id="53728-218">![rs_TutorialPieChartSoftEdge](../../2014/tutorials/media/rs-tutorialpiechartsoftedge.gif "rs_TutorialPieChartSoftEdge")</span></span>  
  
##  <a name="6-add-a-report-title"></a><a name="Title"></a><span data-ttu-id="53728-219">6. 보고서 제목 추가</span><span class="sxs-lookup"><span data-stu-id="53728-219">6. Add a Report Title</span></span>  
  
#### <a name="to-add-a-report-title"></a><span data-ttu-id="53728-220">보고서 제목을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="53728-220">To add a report title</span></span>  
  
1.  <span data-ttu-id="53728-221">디자인 화면에서 **제목을 추가하려면 클릭하십시오.** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="53728-221">On the design surface, click **Click to add title**.</span></span>  
  
2.  <span data-ttu-id="53728-222">**Camera and Camcorder Sales**를 입력하고 Enter 키를 누른 다음 **As a Percentage of Total Sales**를 입력합니다. 그러면 다음과 같이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="53728-222">Type **Camera and Camcorder Sales**, press ENTER, and then type **As a Percentage of Total Sales**, so it looks like this:</span></span>  
  
     <span data-ttu-id="53728-223">**Camera and Camcorder Sales**</span><span class="sxs-lookup"><span data-stu-id="53728-223">**Camera and Camcorder Sales**</span></span>  
  
     <span data-ttu-id="53728-224">**As a Percentage of Total Sales**</span><span class="sxs-lookup"><span data-stu-id="53728-224">**As a Percentage of Total Sales**</span></span>  
  
3.  <span data-ttu-id="53728-225">**카메라 및 캠코더 판매**를 선택 하 고 리본 메뉴의 **홈** 탭에 있는 **글꼴** 섹션에서 **굵게** 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="53728-225">Select **Camera and Camcorder Sales**, and click the **Bold** button from the **Font** section of the **Home** tab of the ribbon.</span></span>  
  
4.  <span data-ttu-id="53728-226">**총 판매량의 백분율로**를 선택 하 고 **홈** 탭의 **글꼴** 섹션에서 글꼴 크기를 **10**으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="53728-226">Select **As a Percentage of Total Sales**, and in the **Font** section on the **Home** tab, set the font size to **10**.</span></span>  
  
5.  <span data-ttu-id="53728-227">(선택 사항) 제목 입력란을 두 줄 텍스트를 포함하도록 크게 만들어야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="53728-227">(Optional) You may need to make the Title text box taller to accommodate the two lines of text.</span></span>  
  
     <span data-ttu-id="53728-228">이 제목은 보고서 맨 위에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="53728-228">This title will appear at the top of the report.</span></span> <span data-ttu-id="53728-229">페이지 머리글이 정의되지 않았을 경우 보고서 본문의 맨 위에 있는 항목은 보고서 머리글에 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="53728-229">When there is no page header defined, items at the top of the report body are the equivalent of a report header.</span></span>  
  
6.  <span data-ttu-id="53728-230">**실행** 을 클릭하여 보고서를 미리 봅니다.</span><span class="sxs-lookup"><span data-stu-id="53728-230">Click **Run** to preview the report.</span></span>  
  
##  <a name="7-save-the-report"></a><a name="Save"></a><span data-ttu-id="53728-231">7. 보고서 저장</span><span class="sxs-lookup"><span data-stu-id="53728-231">7. Save the Report</span></span>  
  
#### <a name="to-save-the-report"></a><span data-ttu-id="53728-232">보고서를 저장하려면</span><span class="sxs-lookup"><span data-stu-id="53728-232">To save the report</span></span>  
  
1.  <span data-ttu-id="53728-233">보고서 디자인 뷰로 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="53728-233">Switch to report design view.</span></span>  
  
2.  <span data-ttu-id="53728-234">보고서 작성기 단추에서 **다른 이름으로 저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="53728-234">From the Report Builder button, click **Save As**.</span></span>  
  
3.  <span data-ttu-id="53728-235">**이름**에 **Sales Pie Chart**를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="53728-235">In **Name**, type **Sales Pie Chart**.</span></span>  
  
4.  <span data-ttu-id="53728-236">**저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="53728-236">Click **Save**.</span></span>  
  
 <span data-ttu-id="53728-237">보고서가 보고서 서버에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="53728-237">Your report is saved on the report server.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="53728-238">다음 단계</span><span class="sxs-lookup"><span data-stu-id="53728-238">Next Steps</span></span>  
 <span data-ttu-id="53728-239">보고서에 원형 차트 추가 자습서를 성공적으로 완료했습니다.</span><span class="sxs-lookup"><span data-stu-id="53728-239">You have successfully completed the Adding a Pie Chart to Your Report tutorial.</span></span> <span data-ttu-id="53728-240">차트에 대한 자세한 내용은 [차트&#40;보고서 작성기 및 SSRS&#41;](report-design/charts-report-builder-and-ssrs.md) 및 [스파크라인 및 데이터 막대&#40;보고서 작성기 및 SSRS&#41;](report-design/sparklines-and-data-bars-report-builder-and-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="53728-240">To learn more about charts, see [Charts &#40;Report Builder and SSRS&#41;](report-design/charts-report-builder-and-ssrs.md) and [Sparklines and Data Bars &#40;Report Builder and SSRS&#41;](report-design/sparklines-and-data-bars-report-builder-and-ssrs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53728-241">참고 항목</span><span class="sxs-lookup"><span data-stu-id="53728-241">See Also</span></span>  
 <span data-ttu-id="53728-242">[자습서 &#40;보고서 작성기&#41;](report-builder-tutorials.md) </span><span class="sxs-lookup"><span data-stu-id="53728-242">[Tutorials &#40;Report Builder&#41;](report-builder-tutorials.md) </span></span>  
 [<span data-ttu-id="53728-243">SQL Server 2014의 보고서 작성기</span><span class="sxs-lookup"><span data-stu-id="53728-243">Report Builder in SQL Server 2014</span></span>](report-builder/report-builder-in-sql-server-2016.md)  
  
  
