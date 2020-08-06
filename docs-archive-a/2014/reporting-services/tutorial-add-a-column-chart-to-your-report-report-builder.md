---
title: '자습서: 보고서에 세로 막대형 차트 추가(보고서 작성기) | Microsoft Docs'
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 63480059-b7b9-44b5-9d7f-91780db708b6
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 0ef3b3f2872c2f8181296bb05337ca18975ac2f2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737863"
---
# <a name="tutorial-add-a-column-chart-to-your-report-report-builder"></a><span data-ttu-id="c8388-102">자습서: 보고서에 세로 막대형 차트 추가(보고서 작성기)</span><span class="sxs-lookup"><span data-stu-id="c8388-102">Tutorial: Add a Column Chart to Your Report (Report Builder)</span></span>
  <span data-ttu-id="c8388-103">세로 막대형 차트에서 계열은 범주별로 그룹화된 일련의 세로 막대로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c8388-103">A column chart displays a series as a set of vertical bars that are grouped by category.</span></span> <span data-ttu-id="c8388-104">다음과 같은 경우에 세로 막대형 차트가 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8388-104">A column chart can be useful to:</span></span>  
  
-   <span data-ttu-id="c8388-105">일정 시간 동안의 데이터 변화 표시</span><span class="sxs-lookup"><span data-stu-id="c8388-105">Show data changes over a period of time.</span></span>  
  
-   <span data-ttu-id="c8388-106">여러 계열의 상대 값 비교</span><span class="sxs-lookup"><span data-stu-id="c8388-106">Compare the relative value of multiple series.</span></span>  
  
-   <span data-ttu-id="c8388-107">추세를 나타내기 위해 이동 평균 표시</span><span class="sxs-lookup"><span data-stu-id="c8388-107">Display a moving average to show trends.</span></span>  
  
 <span data-ttu-id="c8388-108">다음 그림에서는 이동 평균을 사용하여 만들려는 세로 막대형 차트를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c8388-108">The following illustration shows the column chart you will create, with a moving average.</span></span>  
  
 <span data-ttu-id="c8388-109">![rs_TutorialColChartFinished](../../2014/tutorials/media/rs-tutorialcolchartfinished.gif "rs_TutorialColChartFinished")</span><span class="sxs-lookup"><span data-stu-id="c8388-109">![rs_TutorialColChartFinished](../../2014/tutorials/media/rs-tutorialcolchartfinished.gif "rs_TutorialColChartFinished")</span></span>  
  
##  <a name="what-you-will-learn"></a><a name="BackToTop"></a><span data-ttu-id="c8388-110">학습 내용</span><span class="sxs-lookup"><span data-stu-id="c8388-110">What You Will Learn</span></span>  
 <span data-ttu-id="c8388-111">이 자습서에서는 다음 작업 방법을 배웁니다.</span><span class="sxs-lookup"><span data-stu-id="c8388-111">In this tutorial you will learn how to do the following:</span></span>  
  
1.  [<span data-ttu-id="c8388-112">차트 마법사에서 차트 만들기</span><span class="sxs-lookup"><span data-stu-id="c8388-112">Create a Chart from the Chart Wizard</span></span>](#Chart)  
  
2.  [<span data-ttu-id="c8388-113">차트 종류 선택</span><span class="sxs-lookup"><span data-stu-id="c8388-113">Choose the Chart Type</span></span>](#ChartType)  
  
3.  [<span data-ttu-id="c8388-114">가로 축의 서식 및 레이블 지정</span><span class="sxs-lookup"><span data-stu-id="c8388-114">Format and Label the Horizontal Axis</span></span>](#Horizontal)  
  
4.  [<span data-ttu-id="c8388-115">범례 이동</span><span class="sxs-lookup"><span data-stu-id="c8388-115">Move the Legend</span></span>](#Legend)  
  
5.  [<span data-ttu-id="c8388-116">차트 제목 지정</span><span class="sxs-lookup"><span data-stu-id="c8388-116">Title the Chart</span></span>](#ChartTitle)  
  
6.  [<span data-ttu-id="c8388-117">세로 축의 서식 및 레이블 지정</span><span class="sxs-lookup"><span data-stu-id="c8388-117">Format and Label the Vertical Axis</span></span>](#Vertical)  
  
7.  [<span data-ttu-id="c8388-118">이동 평균 추가</span><span class="sxs-lookup"><span data-stu-id="c8388-118">Add a Moving Average</span></span>](#Average)  
  
8.  [<span data-ttu-id="c8388-119">보고서 제목 추가</span><span class="sxs-lookup"><span data-stu-id="c8388-119">Add a Report Title</span></span>](#Title)  
  
9. [<span data-ttu-id="c8388-120">보고서 저장</span><span class="sxs-lookup"><span data-stu-id="c8388-120">Save the Report</span></span>](#Save)  
  
> [!NOTE]  
>  <span data-ttu-id="c8388-121">이 자습서에서 마법사의 단계는 하나의 절차로 통합됩니다.</span><span class="sxs-lookup"><span data-stu-id="c8388-121">In this tutorial, the steps for the wizard are consolidated into one procedure.</span></span> <span data-ttu-id="c8388-122">보고서 서버를 찾고, 데이터 원본을 선택하고, 데이터 세트를 만드는 방법에 대한 단계별 지침은 이 시리즈의 첫 번째 자습서인 [자습서: 기본 테이블 보고서 만들기&#40;보고서 작성기&#41;](../reporting-services/tutorial-creating-a-basic-table-report-report-builder.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c8388-122">For step-by-step instructions about how to browse to a report server, choose a data source, and create a dataset, see the first tutorial in this series: [Tutorial: Creating a Basic Table Report &#40;Report Builder&#41;](../reporting-services/tutorial-creating-a-basic-table-report-report-builder.md).</span></span>  
  
 <span data-ttu-id="c8388-123">이 자습서에 소요되는 예상 시간: 15분</span><span class="sxs-lookup"><span data-stu-id="c8388-123">Estimated time to complete this tutorial: 15 minutes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c8388-124">요구 사항</span><span class="sxs-lookup"><span data-stu-id="c8388-124">Requirements</span></span>  
 <span data-ttu-id="c8388-125">요구 사항에 대한 자세한 내용은 [자습서의 필수 조건&#40;보고서 작성기&#41;](../reporting-services/report-builder-tutorials.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c8388-125">For information about requirements, see [Prerequisites for Tutorials &#40;Report Builder&#41;](../reporting-services/report-builder-tutorials.md).</span></span>  
  
##  <a name="1-create-a-chart-report-from-the-chart-wizard"></a><a name="Chart"></a><span data-ttu-id="c8388-126">1. 차트 마법사에서 차트 보고서 만들기</span><span class="sxs-lookup"><span data-stu-id="c8388-126">1. Create a Chart Report from the Chart Wizard</span></span>  
 <span data-ttu-id="c8388-127">**시작** 대화 상자에서 차트 마법사를 사용 하 여 포함 된 데이터 집합을 만들고, 공유 데이터 원본을 선택 하 고, 세로 막대형 차트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c8388-127">From the **Getting Started** dialog box, use the Chart Wizard to create an embedded dataset, choose a shared data source, and create a column chart.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c8388-128">이 자습서의 쿼리에는 데이터 값이 포함되어 있으므로 외부 데이터 원본이 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c8388-128">In this tutorial, the query contains the data values, so that it does not need an external data source.</span></span> <span data-ttu-id="c8388-129">따라서 쿼리가 상당히 길어집니다.</span><span class="sxs-lookup"><span data-stu-id="c8388-129">This makes the query quite long.</span></span> <span data-ttu-id="c8388-130">비즈니스 환경에서는 쿼리에 데이터가 포함되지 않을 것입니다.</span><span class="sxs-lookup"><span data-stu-id="c8388-130">In a business environment, a query would not contain the data.</span></span> <span data-ttu-id="c8388-131">이 자습서의 쿼리는 학습용으로만 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="c8388-131">This is for learning purposes only.</span></span>  
  
#### <a name="to-create-a-new-chart-report"></a><span data-ttu-id="c8388-132">새 차트 보고서를 만들려면</span><span class="sxs-lookup"><span data-stu-id="c8388-132">To create a new chart report</span></span>  
  
1.  <span data-ttu-id="c8388-133">**시작**을 클릭하고 **프로그램**, **Microsoft SQL Server 2012 보고서 작성기**를 차례로 가리킨 다음 **보고서 작성기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c8388-133">Click **Start**, point to **Programs**, point to **Microsoft SQL Server 2012 Report Builder**, and then click **Report Builder**.</span></span>  
  
     <span data-ttu-id="c8388-134">**시작** 대화 상자가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="c8388-134">The **Getting Started** dialog box appears.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c8388-135">**시작** 대화 상자가 나타나지 않으면 **보고서 작성기** 단추에서 **새로 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c8388-135">If the **Getting Started** dialog box does not appear, from the **Report Builder** button, click **New**.</span></span>  
  
2.  <span data-ttu-id="c8388-136">왼쪽 창에 **새 보고서** 가 선택되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="c8388-136">In the left pane, verify that **New Report** is selected.</span></span>  
  
3.  <span data-ttu-id="c8388-137">오른쪽 창에서 **차트 마법사**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c8388-137">In the right pane, click **Chart Wizard**.</span></span>  
  
4.  <span data-ttu-id="c8388-138">**데이터 집합 선택 페이지**에서 **데이터 집합 만들기**를 클릭 하 고 **다음**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8388-138">On the **Choose a dataset page**, click **Create a dataset**, and then click **Next**.</span></span>  
  
5.  <span data-ttu-id="c8388-139">**데이터 원본에 대한 연결 선택** 페이지에서 기존 데이터 원본을 선택하거나 보고서 서버를 찾아 데이터 원본을 선택하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c8388-139">On the **Choose a connection to a data source** page, select an existing data source or browse to the report server and select a data source, and then click **Next**.</span></span> <span data-ttu-id="c8388-140">사용자 이름과 암호를 입력해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8388-140">You may need to enter a user name and password.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c8388-141">적절한 권한만 가지고 있으면 선택하는 데이터 원본은 중요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c8388-141">The data source you choose is unimportant, as long as you have adequate permissions.</span></span> <span data-ttu-id="c8388-142">데이터를 데이터 원본에서 가져오는 것은 아니기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="c8388-142">You will not be getting data from the data source.</span></span> <span data-ttu-id="c8388-143">자세한 내용은 [데이터에 연결하는 다른 방법&#40;보고서 작성기&#41;](../reporting-services/alternative-ways-to-get-a-data-connection-report-builder.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c8388-143">For more information, see [Alternative Ways to Get a Data Connection &#40;Report Builder&#41;](../reporting-services/alternative-ways-to-get-a-data-connection-report-builder.md).</span></span>  
  
6.  <span data-ttu-id="c8388-144">**쿼리 디자인** 페이지에서 **텍스트로 편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c8388-144">On the **Design a query** page, click **Edit as Text**.</span></span>  
  
7.  <span data-ttu-id="c8388-145">쿼리 창에 다음 쿼리를 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="c8388-145">Paste the following query into the query pane:</span></span>  
  
    ```  
    SELECT CAST('2009-01-01' AS date) AS SalesDate, CAST(54995.21 AS money) AS Sales  
    UNION SELECT CAST('2009-01-05' AS date) AS SalesDate, CAST(64499.04 AS money) AS Sales  
    UNION SELECT CAST('2009-02-11' AS date) AS SalesDate, CAST(37821.79 AS money) AS Sales  
    UNION SELECT CAST('2009-03-18' AS date) AS SalesDate, CAST(53633.08 AS money) AS Sales  
    UNION SELECT CAST('2009-04-23' AS date) AS SalesDate, CAST(24019.3 AS money) AS Sales  
    UNION SELECT CAST('2009-05-01' AS date) AS SalesDate, CAST(93245.5 AS money) AS Sales  
    UNION SELECT CAST('2009-06-06' AS date) AS SalesDate, CAST(55288.0 AS money) AS Sales  
    UNION SELECT CAST('2009-06-16' AS date) AS SalesDate, CAST(68733.5 AS money) AS Sales  
    UNION SELECT CAST('2009-07-16' AS date) AS SalesDate, CAST(24750.85 AS money) AS Sales  
    UNION SELECT CAST('2009-08-23' AS date) AS SalesDate, CAST(43452.3 AS money) AS Sales  
    UNION SELECT CAST('2009-09-24' AS date) AS SalesDate, CAST(58656. AS money) AS Sales  
    UNION SELECT CAST('2009-10-15' AS date) AS SalesDate, CAST(44583. AS money) AS Sales  
    UNION SELECT CAST('2009-11-21' AS date) AS SalesDate, CAST(81568. AS money) AS Sales  
    UNION SELECT CAST('2009-12-15' AS date) AS SalesDate, CAST(45973. AS money) AS Sales  
    UNION SELECT CAST('2009-12-26' AS date) AS SalesDate, CAST(96357. AS money) AS Sales  
    UNION SELECT CAST('2009-12-31' AS date) AS SalesDate, CAST(81946. AS money) AS Sales  
    ```  
  
8.  <span data-ttu-id="c8388-146">(옵션) 실행 단추(**!**)를 클릭하여 차트의 기반으로 사용될 데이터를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="c8388-146">(Optional) Click the Run button (**!**) to see the data your chart will be based on.</span></span>  
  
9. <span data-ttu-id="c8388-147">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c8388-147">Click **Next**.</span></span>  
  
##  <a name="2-choose-the-chart-type"></a><a name="ChartType"></a><span data-ttu-id="c8388-148">2. 차트 종류 선택</span><span class="sxs-lookup"><span data-stu-id="c8388-148">2. Choose the Chart Type</span></span>  
 <span data-ttu-id="c8388-149">미리 정의된 다양한 차트 종류 중에서 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8388-149">You can choose from a variety of predefined chart types.</span></span>  
  
#### <a name="to-add-a-column-chart"></a><span data-ttu-id="c8388-150">세로 막대형 차트를 추가하려면</span><span class="sxs-lookup"><span data-stu-id="c8388-150">To add a column chart</span></span>  
  
1.  <span data-ttu-id="c8388-151">**차트 종류 선택** 페이지에서 기본 차트 종류는 세로 막대형 차트입니다.</span><span class="sxs-lookup"><span data-stu-id="c8388-151">On the **Choose a chart type** page, the column chart is the default chart type.</span></span> <span data-ttu-id="c8388-152">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c8388-152">Click **Next**.</span></span>  
  
2.  <span data-ttu-id="c8388-153">**차트 필드 정렬** 페이지에서 SalesDate 필드를 **범주**창으로 끌어옵니다.</span><span class="sxs-lookup"><span data-stu-id="c8388-153">On the **Arrange chart fields** page, drag the SalesDate field to **Categories**.</span></span> <span data-ttu-id="c8388-154">가로 축에 범주가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c8388-154">Categories display on the horizontal axis.</span></span>  
  
3.  <span data-ttu-id="c8388-155">Sales 필드를 **값**으로 끌어옵니다.</span><span class="sxs-lookup"><span data-stu-id="c8388-155">Drag the Sales field to **Values**.</span></span> <span data-ttu-id="c8388-156">매출 합계 값의 합은 각 날짜에 대해 집계되기 때문에 **값** 상자에는 Sum(Sales)가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c8388-156">The **Values** box displays Sum(Sales) because the sum of the sales total value is aggregated for each date.</span></span> <span data-ttu-id="c8388-157">세로 축에 값이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c8388-157">Values display on the vertical axis.</span></span>  
  
4.  <span data-ttu-id="c8388-158">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c8388-158">Click **Next**.</span></span>  
  
5.  <span data-ttu-id="c8388-159">스타일 **선택** 페이지의 스타일 상자에서 스타일을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8388-159">On the **Choose a Style** page, in the Styles box, select a style.</span></span>  
  
     <span data-ttu-id="c8388-160">스타일은 글꼴 스타일, 색 집합 및 테두리 스타일을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c8388-160">A style specifies a font style, a set of colors, and a border style.</span></span> <span data-ttu-id="c8388-161">스타일을 선택하면 미리 보기 창에 해당 스타일이 적용된 예제 차트가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c8388-161">When you select a style, the Preview pane displays a sample of the chart with that style.</span></span>  
  
6.  <span data-ttu-id="c8388-162">**Finish**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c8388-162">Click **Finish**.</span></span>  
  
     <span data-ttu-id="c8388-163">디자인 화면에 차트가 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="c8388-163">The chart is added to the design surface.</span></span>  
  
7.  <span data-ttu-id="c8388-164">차트를 클릭하여 차트 핸들을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="c8388-164">Click the chart to display the chart handles.</span></span> <span data-ttu-id="c8388-165">차트의 오른쪽 아래 모퉁이를 끌어 차트의 크기를 늘립니다.</span><span class="sxs-lookup"><span data-stu-id="c8388-165">Drag the bottom-right corner of the chart to increase the size of the chart.</span></span> <span data-ttu-id="c8388-166">보고서 디자인 화면이 차트 크기에 맞게 늘어납니다.</span><span class="sxs-lookup"><span data-stu-id="c8388-166">Note that the report design surface increases in size to accommodate the chart size.</span></span>  
  
8.  <span data-ttu-id="c8388-167">**실행** 을 클릭하여 보고서를 미리 봅니다.</span><span class="sxs-lookup"><span data-stu-id="c8388-167">Click **Run** to preview the report.</span></span>  
  
##  <a name="3-format-and-label-the-horizontal-axis"></a><a name="Horizontal"></a><span data-ttu-id="c8388-168">3. 가로 축의 서식 및 레이블 지정</span><span class="sxs-lookup"><span data-stu-id="c8388-168">3. Format and Label the Horizontal Axis</span></span>  
 <span data-ttu-id="c8388-169">기본적으로 가로 축에는 차트 크기에 맞게 자동으로 늘어나는 일반 형식으로 값이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c8388-169">By default, the horizontal axis displays values in a general format that is automatically scaled to fit the size of the chart.</span></span>  
  
#### <a name="to-format-a-date-on-the-horizontal-axis"></a><span data-ttu-id="c8388-170">가로 축의 날짜에 형식을 지정하려면</span><span class="sxs-lookup"><span data-stu-id="c8388-170">To format a date on the horizontal axis</span></span>  
  
1.  <span data-ttu-id="c8388-171">보고서 디자인 뷰로 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="c8388-171">Switch to report design view.</span></span>  
  
2.  <span data-ttu-id="c8388-172">가로 축을 마우스 오른쪽 단추로 클릭 한 다음 **가로 축 속성**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8388-172">Right-click the horizontal axis, and then click **Horizontal Axis Properties**.</span></span>  
  
3.  <span data-ttu-id="c8388-173">**숫자**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8388-173">Click **Number**.</span></span>  
  
4.  <span data-ttu-id="c8388-174">**범주**에서 **날짜**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8388-174">In **Category**, select **Date**.</span></span>  
  
5.  <span data-ttu-id="c8388-175">**형식** 상자에서 **Jan 31, 2000**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c8388-175">In the **Type** box, select **31 Jan 2000**.</span></span>  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
7.  <span data-ttu-id="c8388-176">홈 탭에서 **실행** 을 클릭하여 보고서를 미리 봅니다.</span><span class="sxs-lookup"><span data-stu-id="c8388-176">On the Home tab, click **Run** to preview the report.</span></span>  
  
 <span data-ttu-id="c8388-177">선택한 날짜 형식으로 날짜가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c8388-177">The date displays in the date format that you selected.</span></span> <span data-ttu-id="c8388-178">차트에서 가로 축의 범주 중 일부에는 레이블이 지정되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c8388-178">Notice that the chart does not label every category on the horizontal axis.</span></span> <span data-ttu-id="c8388-179">기본적으로 축 옆에 맞는 레이블만 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="c8388-179">By default, only labels that fit next to the axis are included.</span></span>  
  
 <span data-ttu-id="c8388-180">레이블을 회전하고 간격을 지정하여 레이블 표시를 사용자 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8388-180">You can customize the label display by rotating the labels and specifying the interval.</span></span>  
  
#### <a name="to-rotate-the-axis-labels-and-change-the-display-interval-along-the-horizontal-axis"></a><span data-ttu-id="c8388-181">축 레이블을 회전하고 가로 축의 표시 간격을 변경하려면</span><span class="sxs-lookup"><span data-stu-id="c8388-181">To rotate the axis labels and change the display interval along the horizontal axis</span></span>  
  
1.  <span data-ttu-id="c8388-182">보고서 디자인 뷰로 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="c8388-182">Switch to report design view.</span></span>  
  
2.  <span data-ttu-id="c8388-183">가로 축 제목을 마우스 오른쪽 단추로 클릭 한 다음 **축 제목 표시** 를 클릭 하 여 제목을 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8388-183">Right-click the horizontal axis title, and then click **Show Axis Title** to remove the title.</span></span> <span data-ttu-id="c8388-184">가로 축에는 날짜가 표시되므로 제목이 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c8388-184">Because the horizontal axis displays dates, the title is not needed.</span></span>  
  
3.  <span data-ttu-id="c8388-185">가로 축을 마우스 오른쪽 단추로 클릭 한 다음 **가로 축 속성**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8388-185">Right-click the horizontal axis and then click **Horizontal Axis Properties**.</span></span>  
  
4.  <span data-ttu-id="c8388-186">축 **옵션** 페이지의 **축 범위 및 간격**아래에서 **간격**에 **3** 을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8388-186">In the **Axis Options** page under **Axis range and interval**, type **3** for **Interval**.</span></span> <span data-ttu-id="c8388-187">차트에 3일 단위로 날짜가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c8388-187">The chart will display every third date.</span></span>  
  
5.  <span data-ttu-id="c8388-188">**레이블**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8388-188">Click **Labels**.</span></span>  
  
6.  <span data-ttu-id="c8388-189">**축 레이블 자동 맞춤 옵션 변경**에서 **자동 맞춤 사용 안 함**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8388-189">In **Change axis label auto-fit options**, select **Disable auto-fit**.</span></span>  
  
7.  <span data-ttu-id="c8388-190">**레이블 회전 각도**에서 **-90**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c8388-190">In **Label rotation angle**, select **-90**.</span></span>  
  
8.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
     <span data-ttu-id="c8388-191">가로 축의 샘플 텍스트가 90도 회전합니다.</span><span class="sxs-lookup"><span data-stu-id="c8388-191">The sample text for the horizontal axis rotates by 90 degrees.</span></span>  
  
9. <span data-ttu-id="c8388-192">**실행** 을 클릭하여 보고서를 미리 봅니다.</span><span class="sxs-lookup"><span data-stu-id="c8388-192">Click **Run** to preview the report.</span></span>  
  
 <span data-ttu-id="c8388-193">차트에서는 레이블이 회전하고 레이블이 3일 단위로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c8388-193">On the chart, the labels are rotated and the label for every third date is shown.</span></span>  
  
##  <a name="4-move-the-legend"></a><a name="Legend"></a><span data-ttu-id="c8388-194">4. 범례 이동</span><span class="sxs-lookup"><span data-stu-id="c8388-194">4. Move the Legend</span></span>  
 <span data-ttu-id="c8388-195">범례는 범주와 계열 데이터에서 자동으로 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="c8388-195">The legend is automatically created from category and series data.</span></span>  
  
#### <a name="to-move-the-legend-below-the-chart-area-of-a-column-chart"></a><span data-ttu-id="c8388-196">세로 막대형 차트의 차트 영역 아래로 범례를 이동하려면</span><span class="sxs-lookup"><span data-stu-id="c8388-196">To move the legend below the chart area of a column chart</span></span>  
  
1.  <span data-ttu-id="c8388-197">보고서 디자인 뷰로 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="c8388-197">Switch to report design view.</span></span>  
  
2.  <span data-ttu-id="c8388-198">차트의 범례를 마우스 오른쪽 단추로 클릭 한 다음 **범례 속성**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8388-198">Right-click the legend on the chart, and then click **Legend Properties**.</span></span>  
  
3.  <span data-ttu-id="c8388-199">**레이아웃 및 위치**에서 다른 위치를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8388-199">For **Layout and Position**, select a different position.</span></span> <span data-ttu-id="c8388-200">예를 들어 아래쪽 가운데 옵션으로 위치를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="c8388-200">For example, set the position to the middle bottom option.</span></span>  
  
     <span data-ttu-id="c8388-201">범례가 차트의 위쪽이나 아래쪽에 배치될 경우 범례 레이아웃은 세로에서 가로로 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="c8388-201">When the legend is placed at the top or bottom of a chart, the layout of the legend changes from vertical to horizontal.</span></span> <span data-ttu-id="c8388-202">**레이아웃** 드롭다운 목록에서 다른 레이아웃을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8388-202">You can select a different layout from the **Layout** drop-down list.</span></span>  
  
4.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
5.  <span data-ttu-id="c8388-203">(옵션) 이 자습서에는 범주가 하나만 있기 때문에 범례가 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c8388-203">(Optional) Because there is only one category in this tutorial, the legend is not needed.</span></span> <span data-ttu-id="c8388-204">범례를 제거 하려면 범례를 마우스 오른쪽 단추로 클릭 한 다음 **범례 삭제**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8388-204">To remove the legend, right-click the legend and then click **Delete Legend**.</span></span>  
  
6.  <span data-ttu-id="c8388-205">**실행** 을 클릭하여 보고서를 미리 봅니다.</span><span class="sxs-lookup"><span data-stu-id="c8388-205">Click **Run** to preview the report.</span></span>  
  
##  <a name="5-title-the-chart"></a><a name="ChartTitle"></a><span data-ttu-id="c8388-206">5. 차트 제목</span><span class="sxs-lookup"><span data-stu-id="c8388-206">5. Title the Chart</span></span>  
  
#### <a name="to-change-the-chart-title-above-the-chart-area"></a><span data-ttu-id="c8388-207">차트 영역 위쪽에 있는 차트 제목을 변경하려면</span><span class="sxs-lookup"><span data-stu-id="c8388-207">To change the chart title above the chart area</span></span>  
  
1.  <span data-ttu-id="c8388-208">보고서 디자인 뷰로 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="c8388-208">Switch to report design view.</span></span>  
  
2.  <span data-ttu-id="c8388-209">차트 위쪽의 **차트 제목** 단어를 선택 하 고 다음 텍스트를 입력 합니다. **매장 판매 주문 합계**.</span><span class="sxs-lookup"><span data-stu-id="c8388-209">Select the words **Chart Title** at the top of the chart, and then type the following text: **Store Sales Order Totals**.</span></span>  
  
3.  <span data-ttu-id="c8388-210">**실행** 을 클릭하여 보고서를 미리 봅니다.</span><span class="sxs-lookup"><span data-stu-id="c8388-210">Click **Run** to preview the report.</span></span>  
  
##  <a name="6-format-and-label-the-vertical-axis"></a><a name="Vertical"></a><span data-ttu-id="c8388-211">6. 세로 축의 서식 및 레이블 지정</span><span class="sxs-lookup"><span data-stu-id="c8388-211">6. Format and Label the Vertical Axis</span></span>  
 <span data-ttu-id="c8388-212">기본적으로 세로 축에는 차트 크기에 맞게 자동으로 늘어나는 일반 형식으로 값이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c8388-212">By default, the vertical axis displays values in a general format that is automatically scaled to fit the size of the chart.</span></span>  
  
#### <a name="to-format-as-currency-the-numbers-on-the-vertical-axis"></a><span data-ttu-id="c8388-213">세로 축의 숫자를 통화 형식으로 지정하려면</span><span class="sxs-lookup"><span data-stu-id="c8388-213">To format as currency the numbers on the vertical axis</span></span>  
  
1.  <span data-ttu-id="c8388-214">보고서 디자인 뷰로 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="c8388-214">Switch to report design view.</span></span>  
  
2.  <span data-ttu-id="c8388-215">차트 측면의 세로 축에 있는 레이블을 두 번 클릭하여 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c8388-215">Double-click the labels on the vertical axis along the side of the chart to select them.</span></span>  
  
3.  <span data-ttu-id="c8388-216">리본 메뉴의 **홈** 탭에 있는 **숫자** 그룹에서 **통화** 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8388-216">On the ribbon, on the **Home** tab, in the **Number** group, click the **Currency** button.</span></span> <span data-ttu-id="c8388-217">축 레이블이 변경되어 통화 형식이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c8388-217">The axis labels change to show the currency format.</span></span>  
  
4.  <span data-ttu-id="c8388-218">리본 메뉴의 **홈** 탭에 있는 **숫자** 그룹에서 **소수 자릿수 줄이기** 단추를 두 번 클릭 하 여 가장 가까운 원화로 반올림 한 숫자를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8388-218">On the ribbon, on the **Home** tab, in the **Number** group, click the **Decrease Decimal** button two times, to show the number rounded to the nearest dollar.</span></span>  
  
5.  <span data-ttu-id="c8388-219">세로 축을 마우스 오른쪽 단추로 클릭 하 고 **세로 축 속성**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8388-219">Right-click the vertical axis and click **Vertical Axis Properties**.</span></span>  
  
6.  <span data-ttu-id="c8388-220">**숫자**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8388-220">Click **Number**.</span></span> <span data-ttu-id="c8388-221">**범주** 상자에서 **통화** 는 이미 선택 되어 있으며 **소수 자릿수** 는 이미 **0** 입니다.</span><span class="sxs-lookup"><span data-stu-id="c8388-221">Note that **Currency** is already selected in the **Category** box, and **Decimal places** is already **0** (zero).</span></span>  
  
7.  <span data-ttu-id="c8388-222">**값 표시 위치** 상자에서 **천**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8388-222">In the **Show Values in** box, click **Thousands**.</span></span>  
  
8.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
9. <span data-ttu-id="c8388-223">차트의 측면을 따라 세로 축 제목을 마우스 오른쪽 단추로 클릭 하 고 **축 제목 속성**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8388-223">Right-click the vertical axis title along the side of the chart and click **Axis Title Properties**.</span></span>  
  
10. <span data-ttu-id="c8388-224">**제목 텍스트** 필드의 텍스트를 **Sales Total (천 단위)** 텍스트로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="c8388-224">Replace the text in the **Title text** field with the following text: **Sales Total (in Thousands)**.</span></span> <span data-ttu-id="c8388-225">제목의 형식을 지정하는 방법과 관련된 다양한 옵션을 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8388-225">You can also specify a variety of options related to how the title is formatted.</span></span>  
  
11. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
12. <span data-ttu-id="c8388-226">**실행** 을 클릭하여 보고서를 미리 봅니다.</span><span class="sxs-lookup"><span data-stu-id="c8388-226">Click **Run** to preview the report.</span></span>  
  
##  <a name="7-add-a-moving-average"></a><a name="Average"></a><span data-ttu-id="c8388-227">7. 이동 평균 추가</span><span class="sxs-lookup"><span data-stu-id="c8388-227">7. Add a Moving Average</span></span>  
  
#### <a name="to-add-a-moving-average"></a><span data-ttu-id="c8388-228">이동 평균을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="c8388-228">To add a moving average</span></span>  
  
1.  <span data-ttu-id="c8388-229">보고서 디자인 뷰로 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="c8388-229">Switch to report design view.</span></span>  
  
2.  <span data-ttu-id="c8388-230">차트를 두 번 클릭하여 **차트 데이터** 창을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="c8388-230">Double-click the chart to display the **Chart Data** pane.</span></span>  
  
3.  <span data-ttu-id="c8388-231">**값** 영역에 있는 **[Sum (Sales)]** 필드를 마우스 오른쪽 단추로 클릭 한 다음 **계산 된 계열 추가**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8388-231">Right-click the **[Sum(Sales)]** field that is in the **Values** area, and then click **Add Calculated Series**.</span></span>  
  
4.  <span data-ttu-id="c8388-232">**수식**에서 **이동 평균** 이 선택되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="c8388-232">In **Formula**, verify that **Moving average** is selected.</span></span>  
  
5.  <span data-ttu-id="c8388-233">**수식 매개 변수 설정**의 **기간**에서 **4**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c8388-233">In **Set Formula Parameters**, for **Period**, select **4**.</span></span>  
  
6.  <span data-ttu-id="c8388-234">**테두리**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8388-234">Click **Border**.</span></span>  
  
7.  <span data-ttu-id="c8388-235">**선 두께**에서 **3pt**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8388-235">In **Line width**, select **3pt**.</span></span>  
  
8.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
9. <span data-ttu-id="c8388-236">**실행** 을 클릭하여 보고서를 미리 봅니다.</span><span class="sxs-lookup"><span data-stu-id="c8388-236">Click **Run** to preview the report.</span></span>  
  
 <span data-ttu-id="c8388-237">차트에 4일 단위로 평균이 계산된 날짜별 총 판매액의 이동 평균을 나타내는 선이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c8388-237">The chart displays a line that shows the moving average for total sales by date, averaged over every four dates.</span></span>  
  
##  <a name="8-add-a-report-title"></a><a name="Title"></a><span data-ttu-id="c8388-238">8. 보고서 제목 추가</span><span class="sxs-lookup"><span data-stu-id="c8388-238">8. Add a Report Title</span></span>  
  
#### <a name="to-add-a-report-title"></a><span data-ttu-id="c8388-239">보고서 제목을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="c8388-239">To add a report title</span></span>  
  
1.  <span data-ttu-id="c8388-240">보고서 디자인 뷰로 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="c8388-240">Switch to report design view.</span></span>  
  
2.  <span data-ttu-id="c8388-241">디자인 화면에서 **제목을 추가하려면 클릭하십시오.** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c8388-241">On the design surface, click **Click to add title**.</span></span>  
  
3.  <span data-ttu-id="c8388-242">**Sales Chart**를 입력 하 고 enter 키를 누른 다음 **1 월부터 12 월 2009**을 입력 하면 다음과 같이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c8388-242">Type **Sales Chart**, press ENTER, and then type **January to December 2009**, so it looks like this:</span></span>  
  
     <span data-ttu-id="c8388-243">**Sales Chart**</span><span class="sxs-lookup"><span data-stu-id="c8388-243">**Sales Chart**</span></span>  
  
     <span data-ttu-id="c8388-244">**January to December 2009**</span><span class="sxs-lookup"><span data-stu-id="c8388-244">**January to December 2009**</span></span>  
  
4.  <span data-ttu-id="c8388-245">**Sales Chart**를 선택 하 고 리본 메뉴의 **홈** 탭에 있는 **글꼴** 섹션에서 **굵게** 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8388-245">Select **Sales Chart**, and click the **Bold** button in the **Font** section on the **Home** tab of the ribbon.</span></span>  
  
5.  <span data-ttu-id="c8388-246">**1 월 ~ 12 월 2009**을 선택 하 고 **홈** 탭의 **글꼴** 섹션에서 글꼴 크기를 **10**으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8388-246">Select **January to December 2009**, and in the **Font** section on the **Home** tab, set the font size to **10**.</span></span>  
  
6.  <span data-ttu-id="c8388-247">필드 아래쪽 가장자리의 가운데를 클릭할 때 양방향 화살표를 끌어 두 줄의 텍스트를 포함 하기 위해 **제목** 입력란을 더 길게 만들어야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8388-247">(Optional) You may need to make the **Title** text box taller to accommodate the two lines of text by pulling down on the double-headed arrows when you click in the middle of the bottom edge.</span></span>  
  
     <span data-ttu-id="c8388-248">이 제목은 보고서 맨 위에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="c8388-248">This title will appear at the top of the report.</span></span> <span data-ttu-id="c8388-249">페이지 머리글이 정의되지 않았을 경우 보고서 본문의 맨 위에 있는 항목은 보고서 머리글에 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="c8388-249">When there is no page header defined, items at the top of the report body are the equivalent of a report header.</span></span>  
  
7.  <span data-ttu-id="c8388-250">**실행** 을 클릭하여 보고서를 미리 봅니다.</span><span class="sxs-lookup"><span data-stu-id="c8388-250">Click **Run** to preview the report.</span></span>  
  
##  <a name="9-save-the-report"></a><a name="Save"></a><span data-ttu-id="c8388-251">9. 보고서 저장</span><span class="sxs-lookup"><span data-stu-id="c8388-251">9. Save the Report</span></span>  
  
#### <a name="to-save-the-report"></a><span data-ttu-id="c8388-252">보고서를 저장하려면</span><span class="sxs-lookup"><span data-stu-id="c8388-252">To save the report</span></span>  
  
1.  <span data-ttu-id="c8388-253">보고서 디자인 뷰로 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="c8388-253">Switch to report design view.</span></span>  
  
2.  <span data-ttu-id="c8388-254">보고서 작성기 단추에서 **다른 이름으로 저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c8388-254">From the Report Builder button, click **Save As**.</span></span>  
  
3.  <span data-ttu-id="c8388-255">**이름**에 **Sales Order Column Chart**를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="c8388-255">In **Name**, type **Sales Order Column Chart**.</span></span>  
  
4.  <span data-ttu-id="c8388-256">**저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c8388-256">Click **Save**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="c8388-257">다음 단계</span><span class="sxs-lookup"><span data-stu-id="c8388-257">Next Steps</span></span>  
 <span data-ttu-id="c8388-258">보고서에 세로 막대형 차트 추가 자습서를 성공적으로 완료했습니다.</span><span class="sxs-lookup"><span data-stu-id="c8388-258">You have successfully completed the Adding a Column Chart to Your Report tutorial.</span></span> <span data-ttu-id="c8388-259">차트에 대한 자세한 내용은 [차트&#40;보고서 작성기 및 SSRS&#41;](report-design/charts-report-builder-and-ssrs.md) 및 [스파크라인 및 데이터 막대&#40;보고서 작성기 및 SSRS&#41;](report-design/sparklines-and-data-bars-report-builder-and-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c8388-259">To learn more about charts, see [Charts &#40;Report Builder and SSRS&#41;](report-design/charts-report-builder-and-ssrs.md) and [Sparklines and Data Bars &#40;Report Builder and SSRS&#41;](report-design/sparklines-and-data-bars-report-builder-and-ssrs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8388-260">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c8388-260">See Also</span></span>  
 <span data-ttu-id="c8388-261">[자습서 &#40;보고서 작성기&#41;](report-builder-tutorials.md) </span><span class="sxs-lookup"><span data-stu-id="c8388-261">[Tutorials &#40;Report Builder&#41;](report-builder-tutorials.md) </span></span>  
 [<span data-ttu-id="c8388-262">SQL Server 2014의 보고서 작성기</span><span class="sxs-lookup"><span data-stu-id="c8388-262">Report Builder in SQL Server 2014</span></span>](report-builder/report-builder-in-sql-server-2016.md)  
  
  
