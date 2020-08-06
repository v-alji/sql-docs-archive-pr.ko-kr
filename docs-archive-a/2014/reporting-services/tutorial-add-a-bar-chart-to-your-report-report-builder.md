---
title: '자습서: 보고서에 막대 차트 추가(보고서 작성기) | Microsoft Docs'
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 6956ebd6-0217-4087-a4fa-5cc1c3804691
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 01708ca548c40118daa03fac34d8a323d628b012
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649358"
---
# <a name="tutorial-add-a-bar-chart-to-your-report-report-builder"></a><span data-ttu-id="ce829-102">자습서: 보고서에 막대형 차트 추가(보고서 작성기)</span><span class="sxs-lookup"><span data-stu-id="ce829-102">Tutorial: Add a Bar Chart to Your Report (Report Builder)</span></span>
  <span data-ttu-id="ce829-103">가로 막대형 차트는 범주 데이터를 가로로 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-103">A bar chart displays category data horizontally.</span></span> <span data-ttu-id="ce829-104">이렇게 하면 다음 작업에 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-104">This can help to:</span></span>  
  
-   <span data-ttu-id="ce829-105">긴 범주 이름의 가독성 향상</span><span class="sxs-lookup"><span data-stu-id="ce829-105">Improve readability of long category names.</span></span>  
  
-   <span data-ttu-id="ce829-106">값으로 표시되는 시간을 이해하기 쉽게 표현</span><span class="sxs-lookup"><span data-stu-id="ce829-106">Improve understandability of times plotted as values.</span></span>  
  
-   <span data-ttu-id="ce829-107">여러 계열의 상대 값 비교</span><span class="sxs-lookup"><span data-stu-id="ce829-107">Compare the relative value of multiple series.</span></span>  
  
 <span data-ttu-id="ce829-108">다음 그림에서는 2008년 및 2009년 상위 5명에 속하는 영업 사원의 판매 실적을 가지고 사전순으로 만든 가로 막대 차트를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-108">The following illustration shows the bar chart that you will create, with sales for 2008 and 2009 for the top five salespeople, in alphabetical order.</span></span>  
  
 <span data-ttu-id="ce829-109">![rs_BarChartTutorial](../../2014/tutorials/media/rs-barcharttutorial.gif "rs_BarChartTutorial")</span><span class="sxs-lookup"><span data-stu-id="ce829-109">![rs_BarChartTutorial](../../2014/tutorials/media/rs-barcharttutorial.gif "rs_BarChartTutorial")</span></span>  
  
##  <a name="what-you-will-learn"></a><a name="BackToTop"></a><span data-ttu-id="ce829-110">학습 내용</span><span class="sxs-lookup"><span data-stu-id="ce829-110">What You Will Learn</span></span>  
 <span data-ttu-id="ce829-111">이 자습서에서는 다음 작업 방법을 배웁니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-111">In this tutorial you will learn how to do the following:</span></span>  
  
1.  [<span data-ttu-id="ce829-112">차트 마법사에서 차트 만들기</span><span class="sxs-lookup"><span data-stu-id="ce829-112">Create a Chart from the Chart Wizard</span></span>](#Chart)  
  
2.  [<span data-ttu-id="ce829-113">차트 종류 선택</span><span class="sxs-lookup"><span data-stu-id="ce829-113">Choose the Chart Type</span></span>](#ChartType)  
  
3.  [<span data-ttu-id="ce829-114">세로 축에 모든 범주 값 표시</span><span class="sxs-lookup"><span data-stu-id="ce829-114">Display all Category Values on the Vertical Axis</span></span>](#AllValues)  
  
4.  [<span data-ttu-id="ce829-115">세로 축의 이름 표시 수정</span><span class="sxs-lookup"><span data-stu-id="ce829-115">Modify the Display of Names on the Vertical Axis</span></span>](#Sort)  
  
5.  [<span data-ttu-id="ce829-116">범례 이동</span><span class="sxs-lookup"><span data-stu-id="ce829-116">Move the Legend</span></span>](#Legend)  
  
6.  [<span data-ttu-id="ce829-117">차트 제목 이동</span><span class="sxs-lookup"><span data-stu-id="ce829-117">Move the Chart Title</span></span>](#ChartTitle)  
  
7.  [<span data-ttu-id="ce829-118">가로 축의 서식 및 레이블 지정</span><span class="sxs-lookup"><span data-stu-id="ce829-118">Format and Label the Horizontal Axis</span></span>](#Horizontal)  
  
8.  [<span data-ttu-id="ce829-119">상위 5개 값을 표시하는 필터 추가</span><span class="sxs-lookup"><span data-stu-id="ce829-119">Add a Filter to Display the Top Five Values</span></span>](#Filter)  
  
9. [<span data-ttu-id="ce829-120">보고서 제목 추가</span><span class="sxs-lookup"><span data-stu-id="ce829-120">Add a Report Title</span></span>](#Title)  
  
10. [<span data-ttu-id="ce829-121">보고서 저장</span><span class="sxs-lookup"><span data-stu-id="ce829-121">Save the Report</span></span>](#Save)  
  
> [!NOTE]  
>  <span data-ttu-id="ce829-122">이 자습서에서 마법사의 단계는 하나의 절차로 통합됩니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-122">In this tutorial, the steps for the wizard are consolidated into one procedure.</span></span> <span data-ttu-id="ce829-123">보고서 서버를 찾고, 데이터 세트를 만들고, 데이터 원본을 선택하는 방법에 대한 단계별 지침은 이 시리즈의 첫 번째 자습서인 [자습서: 기본 테이블 보고서 만들기&#40;보고서 작성기&#41;](../reporting-services/tutorial-creating-a-basic-table-report-report-builder.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ce829-123">For step-by-step instructions about how to browse to a report server, create a dataset, and choose a data source, see the first tutorial in this series: [Tutorial: Creating a Basic Table Report &#40;Report Builder&#41;](../reporting-services/tutorial-creating-a-basic-table-report-report-builder.md).</span></span>  
  
 <span data-ttu-id="ce829-124">이 자습서에 소요되는 예상 시간: 15분</span><span class="sxs-lookup"><span data-stu-id="ce829-124">Estimated time to complete this tutorial: 15 minutes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ce829-125">요구 사항</span><span class="sxs-lookup"><span data-stu-id="ce829-125">Requirements</span></span>  
 <span data-ttu-id="ce829-126">요구 사항에 대한 자세한 내용은 [자습서의 필수 조건&#40;보고서 작성기&#41;](../reporting-services/report-builder-tutorials.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ce829-126">For more information about requirements, see [Prerequisites for Tutorials &#40;Report Builder&#41;](../reporting-services/report-builder-tutorials.md).</span></span>  
  
##  <a name="1-create-a-chart-report-from-the-chart-wizard"></a><a name="Chart"></a><span data-ttu-id="ce829-127">1. 차트 마법사에서 차트 보고서 만들기</span><span class="sxs-lookup"><span data-stu-id="ce829-127">1. Create a Chart Report from the Chart Wizard</span></span>  
 <span data-ttu-id="ce829-128">**시작** 대화 상자에서 포함 된 데이터 집합을 만들고, 공유 데이터 원본을 선택 하 고, 차트 마법사를 사용 하 여 가로 막대형 차트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-128">From the **Getting Started** dialog box, create an embedded dataset, choose a shared data source, and create a bar chart by using the Chart Wizard.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ce829-129">이 자습서의 쿼리에는 데이터 값이 포함되어 있으므로 외부 데이터 원본이 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-129">In this tutorial, the query contains the data values so that it does not need an external data source.</span></span> <span data-ttu-id="ce829-130">따라서 쿼리가 상당히 길어집니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-130">This makes the query quite long.</span></span> <span data-ttu-id="ce829-131">비즈니스 환경에서는 쿼리에 데이터가 포함되지 않을 것입니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-131">In a business environment, a query would not contain the data.</span></span> <span data-ttu-id="ce829-132">이 자습서의 쿼리는 학습용으로만 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-132">This is for learning purposes only.</span></span>  
  
#### <a name="to-create-a-new-chart-report"></a><span data-ttu-id="ce829-133">새 차트 보고서를 만들려면</span><span class="sxs-lookup"><span data-stu-id="ce829-133">To create a new chart report</span></span>  
  
1.  <span data-ttu-id="ce829-134">**시작**을 클릭하고 **프로그램**, **Microsoft SQL Server 2012 보고서 작성기**를 차례로 가리킨 다음 **보고서 작성기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-134">Click **Start**, point to **Programs**, point to **Microsoft SQL Server 2012 Report Builder**, and then click **Report Builder**.</span></span>  
  
     <span data-ttu-id="ce829-135">**시작** 대화 상자가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-135">The **Getting Started** dialog box appears.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ce829-136">**시작** 대화 상자가 나타나지 않으면 보고서 작성기 단추를 클릭 한 다음 **새로 만들기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-136">If the **Getting Started** dialog box does not appear, click the Report Builder button, and then click **New**.</span></span>  
  
2.  <span data-ttu-id="ce829-137">왼쪽 창에 **새 보고서** 가 선택되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-137">In the left pane, verify that **New Report** is selected.</span></span>  
  
3.  <span data-ttu-id="ce829-138">오른쪽 창에서 **차트 마법사**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-138">In the right pane, click **Chart Wizard**.</span></span>  
  
4.  <span data-ttu-id="ce829-139">**데이터 세트 선택** 페이지에서 **데이터 세트 만들기**를 클릭한 후, **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-139">On the **Choose a dataset** page, click **Create a dataset**, and then click **Next**.</span></span>  
  
5.  <span data-ttu-id="ce829-140">**데이터 원본에 대한 연결 선택** 페이지에서 기존 데이터 원본을 선택하거나 보고서 서버를 찾아 데이터 원본을 선택하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-140">On the **Choose a connection to a data source** page, select an existing data source or browse to the report server and select a data source, and then click **Next**.</span></span> <span data-ttu-id="ce829-141">사용자 이름과 암호를 입력해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-141">You may need to enter a user name and password.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ce829-142">적절한 권한만 가지고 있으면 선택하는 데이터 원본은 중요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-142">The data source you choose is unimportant, as long as you have adequate permissions.</span></span> <span data-ttu-id="ce829-143">데이터를 데이터 원본에서 가져오는 것은 아니기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-143">You will not be getting data from the data source.</span></span> <span data-ttu-id="ce829-144">자세한 내용은 [데이터에 연결하는 다른 방법&#40;보고서 작성기&#41;](../reporting-services/alternative-ways-to-get-a-data-connection-report-builder.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ce829-144">For more information, see [Alternative Ways to Get a Data Connection &#40;Report Builder&#41;](../reporting-services/alternative-ways-to-get-a-data-connection-report-builder.md).</span></span>  
  
6.  <span data-ttu-id="ce829-145">**쿼리 디자인** 페이지에서 **텍스트로 편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-145">On the **Design a query** page, click **Edit as Text**.</span></span>  
  
7.  <span data-ttu-id="ce829-146">쿼리 창에 다음 쿼리를 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-146">Paste the following query into the query pane:</span></span>  
  
    ```  
    SELECT 'Luis' as FirstName, 'Alverca' as LastName, CAST(170000.00 AS money) AS SalesYear2009, CAST(150000. AS money) AS SalesYear2008  
    UNION SELECT 'Jeffrey' as FirstName, 'Zeng' as LastName, CAST(210000. AS money) AS SalesYear2009, CAST(190000. AS money) AS SalesYear2008  
    UNION SELECT 'Houman' as FirstName, 'Pournasseh' as LastName, CAST(150000. AS money) AS SalesYear2009, CAST(180000. AS money) AS SalesYear2008  
    UNION SELECT 'Robin' as FirstName, 'Wood' as LastName, CAST(75000. AS money) AS SalesYear2009, CAST(175000. AS money) AS SalesYear2008  
    UNION SELECT 'Daniela' as FirstName, 'Guaita' as LastName,  CAST(170000. AS money) AS SalesYear2009, CAST(175000. AS money) AS SalesYear2008  
    UNION SELECT 'John' as FirstName, 'Yokim' as LastName, CAST(160000. AS money) AS SalesYear2009, CAST(195000. AS money) AS SalesYear2008  
    UNION SELECT 'Delphine' as FirstName, 'Ribaute' as LastName, CAST(180000. AS money) AS SalesYear2009, CAST(205000. AS money) AS SalesYear2008  
    UNION SELECT 'Robert' as FirstName, 'Hernady' as LastName, CAST(140000. AS money) AS SalesYear2009, CAST(180000. AS money) AS SalesYear2008  
    UNION SELECT 'Tanja' as FirstName, 'Plate' as LastName, CAST(150000. AS money) AS SalesYear2009, CAST(160000. AS money) AS SalesYear2008  
    UNION SELECT 'David' as FirstName, 'Bradley' as LastName, CAST(210000. AS money) AS SalesYear2009, CAST(180000. AS money) AS SalesYear2008  
    UNION SELECT 'Michal' as FirstName, 'Jaworski' as LastName, CAST(175000. AS money) AS SalesYear2009, CAST(220000. AS money) AS SalesYear2008  
    UNION SELECT 'Chris' as FirstName, 'Ashton' as LastName, CAST(195000. AS money) AS SalesYear2009, CAST(205000. AS money) AS SalesYear2008  
    UNION SELECT 'Pongsiri' as FirstName, 'Hirunyanitiwatna' as LastName, CAST(175000. AS money) AS SalesYear2009, CAST(215000. AS money) AS SalesYear2008  
    UNION SELECT 'Brian' as FirstName, 'Burke' as LastName, CAST(187000. AS money) AS SalesYear2009, CAST(207000. AS money) AS SalesYear2008  
    ```  
  
8.  <span data-ttu-id="ce829-147">(옵션) 실행 단추(**!**)를 클릭하여 차트의 기반으로 사용될 데이터를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-147">(Optional) Click the Run button (**!**) to see the data your chart will be based on.</span></span>  
  
9. <span data-ttu-id="ce829-148">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-148">Click **Next**.</span></span>  
  
##  <a name="2-choose-the-chart-type"></a><a name="ChartType"></a><span data-ttu-id="ce829-149">2. 차트 종류 선택</span><span class="sxs-lookup"><span data-stu-id="ce829-149">2. Choose the Chart Type</span></span>  
 <span data-ttu-id="ce829-150">미리 정의된 다양한 차트 종류 중에서 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-150">You can choose from a variety of predefined chart types.</span></span>  
  
#### <a name="to-add-a-column-chart"></a><span data-ttu-id="ce829-151">세로 막대형 차트를 추가하려면</span><span class="sxs-lookup"><span data-stu-id="ce829-151">To add a column chart</span></span>  
  
1.  <span data-ttu-id="ce829-152">**차트 종류 선택** 페이지에서 기본 차트 종류는 세로 막대형 차트입니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-152">On the **Choose a chart type** page, the column chart is the default chart type.</span></span>  
  
2.  <span data-ttu-id="ce829-153">**가로 막대형**을 클릭하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-153">Click **Bar**, and then click **Next**.</span></span>  
  
     <span data-ttu-id="ce829-154">**차트 필드 정렬** 페이지의 **사용 가능한 필드** 창에는 FirstName, LastName, SalesYear2009 및 SalesYear2008의 4 개 필드가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-154">On the **Arrange chart fields** page, there are four fields in the **Available fields** pane: FirstName, LastName, SalesYear2009, and SalesYear2008.</span></span>  
  
3.  <span data-ttu-id="ce829-155">LastName을 범주 창으로 끌어 옵니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-155">Drag LastName to the Categories pane.</span></span>  
  
4.  <span data-ttu-id="ce829-156">SalesYear2009를 값 창으로 끌어 옵니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-156">Drag SalesYear2009 to the Values pane.</span></span> <span data-ttu-id="ce829-157">SalesYear2009는 각 영업 사원의 2009년도 판매액을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-157">SalesYear2009 represents the sales amount for each salesperson for the year 2009.</span></span> <span data-ttu-id="ce829-158">차트에 각 제품의 집계가 표시되기 때문에 값 창에는 `[Sum(SalesYear2009)]` 가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-158">The Values pane displays `[Sum(SalesYear2009)]` because the chart displays the aggregate for each product.</span></span>  
  
5.  <span data-ttu-id="ce829-159">SalesYear2008을 SalesYear2009 아래의 값 창으로 끌어 옵니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-159">Drag SalesYear2008 to the Values pane under SalesYear2009.</span></span> <span data-ttu-id="ce829-160">SalesYear2008은 각 영업 사원의 2008년도 판매액을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-160">SalesYear2008 represents the sales amount for each salesperson for the year 2008.</span></span>  
  
6.  <span data-ttu-id="ce829-161">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-161">Click **Next**.</span></span>  
  
7.  <span data-ttu-id="ce829-162">스타일 **선택** 페이지의 스타일 창에서 스타일을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-162">On the **Choose a style** page, in the Styles pane, select a style.</span></span>  
  
     <span data-ttu-id="ce829-163">스타일은 글꼴 스타일, 색 집합 및 테두리 스타일을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-163">A style specifies a font style, a set of colors, and a border style.</span></span> <span data-ttu-id="ce829-164">스타일을 선택하면 미리 보기 창에 해당 스타일이 적용된 예제 차트가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-164">When you select a style, the Preview pane displays a sample of the chart with that style.</span></span>  
  
8.  <span data-ttu-id="ce829-165">**Finish**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-165">Click **Finish**.</span></span>  
  
     <span data-ttu-id="ce829-166">디자인 화면에 차트가 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-166">The chart is added to the design surface.</span></span>  
  
9. <span data-ttu-id="ce829-167">차트를 클릭하여 차트 핸들을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-167">Click the chart to display the chart handles.</span></span> <span data-ttu-id="ce829-168">차트의 오른쪽 아래 모퉁이를 끌어 차트의 크기를 늘립니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-168">Drag the bottom-right corner of the chart to increase the size of the chart.</span></span>  
  
10. <span data-ttu-id="ce829-169">**실행** 을 클릭하여 보고서를 미리 봅니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-169">Click **Run** to preview the report.</span></span>  
  
 <span data-ttu-id="ce829-170">보고서에는 각 영업 사원의 2008년과 2009년 판매량에 대한 가로 막대형 차트가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-170">The report displays the bar chart for sales for each sales person for the years 2008 and 2009.</span></span> <span data-ttu-id="ce829-171">막대 길이는 총 판매량에 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-171">The length of the bar corresponds to the sales total.</span></span>  
  
##  <a name="3-modify-the-display-of-names-on-the-vertical-axis"></a><a name="AllValues"></a><span data-ttu-id="ce829-172">3. 세로 축의 이름 표시 수정</span><span class="sxs-lookup"><span data-stu-id="ce829-172">3. Modify the Display of Names on the Vertical Axis</span></span>  
 <span data-ttu-id="ce829-173">기본적으로 세로 축의 값 중 일부만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-173">By default, only some of the values on the vertical axis appear.</span></span> <span data-ttu-id="ce829-174">모든 범주를 표시하도록 차트를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-174">You can change the chart to display all categories.</span></span>  
  
#### <a name="to-display-all-sales-persons-along-the-category-axis-of-a-bar-chart"></a><span data-ttu-id="ce829-175">가로 막대형 차트의 범주 축에 모든 영업 사원을 표시하려면</span><span class="sxs-lookup"><span data-stu-id="ce829-175">To display all sales persons along the category axis of a bar chart</span></span>  
  
1.  <span data-ttu-id="ce829-176">보고서 디자인 뷰로 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-176">Switch to report design view.</span></span>  
  
2.  <span data-ttu-id="ce829-177">세로 축을 마우스 오른쪽 단추로 클릭 한 다음 **세로 축 속성**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-177">Right-click the vertical axis, and then click **Vertical Axis Properties**.</span></span>  
  
3.  <span data-ttu-id="ce829-178">**축 범위 및 간격**의 **간격** 상자에 **1**을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-178">Under **Axis range and interval**, in the **Interval** box, type **1**.</span></span>  
  
4.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
5.  <span data-ttu-id="ce829-179">세로 **축 제목을** 마우스 오른쪽 단추로 클릭 하 고 **축 제목 표시** 확인란의 선택을 취소 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-179">Right-click the vertical **Axis Title** and clear the **Show Axis Title** check box.</span></span>  
  
6.  <span data-ttu-id="ce829-180">**실행** 을 클릭하여 보고서를 미리 봅니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-180">Click **Run** to preview the report.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ce829-181">세로 축에서 영업 사원의 이름을 읽을 수 없는 경우에는 차트를 늘리거나 축 레이블의 서식 옵션을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-181">If you cannot read the salesperson names on the vertical axis, you can make your chart taller or change the formatting options for the axis labels.</span></span>  
  
###  <a name="display-last-name-and-first-name-on-vertical-axis"></a><a name="CategoryExpression"></a><span data-ttu-id="ce829-182">세로 축에 성 및 이름 표시</span><span class="sxs-lookup"><span data-stu-id="ce829-182">Display Last Name and First Name on Vertical Axis</span></span>  
 <span data-ttu-id="ce829-183">각 영업 사원의 성 다음에 이름이 오도록 범주 식을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-183">You can change the category expression to include last name followed by first name of each sales person.</span></span>  
  
##### <a name="to-change-the-category-expression"></a><span data-ttu-id="ce829-184">범주 식을 변경하려면</span><span class="sxs-lookup"><span data-stu-id="ce829-184">To change the category expression</span></span>  
  
1.  <span data-ttu-id="ce829-185">보고서 디자인 뷰로 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-185">Switch to report design view.</span></span>  
  
2.  <span data-ttu-id="ce829-186">차트를 두 번 클릭하여 **차트 데이터** 창을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-186">Double-click the chart to display the **Chart Data** pane.</span></span>  
  
3.  <span data-ttu-id="ce829-187">**범주 그룹** 영역에서 [LastName]을 마우스 오른쪽 단추로 클릭한 다음 **범주 그룹 속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-187">In the **Category Groups** area, right-click [LastName], and then click **Category Group Properties**.</span></span>  
  
4.  <span data-ttu-id="ce829-188">레이블에서 식 단추(fx)를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-188">In Label, click the expression (Fx) button.</span></span>  
  
5.  <span data-ttu-id="ce829-189">다음 식을 입력합니다. `=Fields!LastName.Value & ", " & Fields!FirstName.Value`</span><span class="sxs-lookup"><span data-stu-id="ce829-189">Type the following expression: `=Fields!LastName.Value & ", " & Fields!FirstName.Value`</span></span>  
  
     <span data-ttu-id="ce829-190">이 식은 성, 쉼표 및 이름을 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-190">This expression concatenates the last name, a comma, and the first name.</span></span>  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
7.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
8.  <span data-ttu-id="ce829-191">**실행** 을 클릭하여 보고서를 미리 봅니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-191">Click **Run** to preview the report.</span></span>  
  
 <span data-ttu-id="ce829-192">보고서를 실행할 때 이름이 표시되지 않으면 데이터를 수동으로 새로 고칩니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-192">If the first names do not appear when you run the report, you can refresh the data manually.</span></span> <span data-ttu-id="ce829-193">미리 보기 모드에 있는 동안 **탐색** 그룹의 **실행** 탭에서 **새로 고침**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-193">While still in preview mode, on the **Run** tab in the **Navigation** group, click **Refresh**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ce829-194">세로 축에서 영업 사원의 이름을 읽을 수 없는 경우에는 차트를 늘리거나 축 레이블의 서식 옵션을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-194">If you cannot read the salesperson names on the vertical axis, you can make your chart taller or change the formatting options for the axis labels.</span></span>  
  
##  <a name="4-change-the-sort-order-for-names-on-the-vertical-axis"></a><a name="Sort"></a><span data-ttu-id="ce829-195">4. 세로 축에서 이름에 대 한 정렬 순서 변경</span><span class="sxs-lookup"><span data-stu-id="ce829-195">4. Change the Sort Order for Names on the Vertical Axis</span></span>  
 <span data-ttu-id="ce829-196">차트에서 데이터를 정렬하면 범주 축에서 값 순서를 변경하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-196">When you sort the data on a chart, you are changing the order of values on the category axis.</span></span>  
  
#### <a name="to-sort-the-names-in-alphabetical-order-on-the-bar-chart"></a><span data-ttu-id="ce829-197">가로 막대형 차트에서 이름을 사전순으로 정렬하려면</span><span class="sxs-lookup"><span data-stu-id="ce829-197">To sort the names in alphabetical order on the bar chart</span></span>  
  
1.  <span data-ttu-id="ce829-198">보고서 디자인 뷰로 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-198">Switch to report design view.</span></span>  
  
2.  <span data-ttu-id="ce829-199">차트를 두 번 클릭하여 **차트 데이터** 창을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-199">Double-click the chart to display the **Chart Data** pane.</span></span>  
  
3.  <span data-ttu-id="ce829-200">**범주 그룹** 영역에서 [LastName]을 마우스 오른쪽 단추로 클릭한 다음 **범주 그룹 속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-200">In the **Category Groups** area, right-click [LastName], and then click **Category Group Properties**.</span></span>  
  
4.  <span data-ttu-id="ce829-201">**정렬**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-201">Click **Sorting**.</span></span> <span data-ttu-id="ce829-202">**정렬 옵션을 변경하십시오.** 페이지에 정렬 식 목록이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-202">The **Change sorting options** page displays a list of sort expressions.</span></span> <span data-ttu-id="ce829-203">기본적으로 이 목록에는 원래 범주 그룹 식과 동일한 정렬 식이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-203">By default, this list has one sort expression that is the same as the original category group expression.</span></span>  
  
5.  <span data-ttu-id="ce829-204">정렬 기준에서 식 단추 (**Fx**)를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-204">In Sort by, click the expression (**Fx**) button.</span></span>  
  
6.  <span data-ttu-id="ce829-205">다음 식을 입력합니다. `=Fields!LastName.Value & ", " & Fields!FirstName.Value`</span><span class="sxs-lookup"><span data-stu-id="ce829-205">Type the following expression: `=Fields!LastName.Value & ", " & Fields!FirstName.Value`</span></span>  
  
7.  <span data-ttu-id="ce829-206">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-206">Click **OK**.</span></span>  
  
8.  <span data-ttu-id="ce829-207">다시 **범주 그룹 속성** 페이지의 **순서** 드롭다운 목록에서 **내림차순**을 선택 합니다. 이렇게 하면 이름이 위쪽에서 아래쪽 순서로 표시 되도록 역방향 사전순이 선택 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-207">Back on the **Category Group Properties** page, in the **Order** drop-down list, select **Z to A**. This selects reverse alphabetical order so that the names appear in order from top to bottom.</span></span>  
  
9. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
10. <span data-ttu-id="ce829-208">**실행** 을 클릭하여 보고서를 미리 봅니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-208">Click **Run** to preview the report.</span></span>  
  
 <span data-ttu-id="ce829-209">가로 축의 이름은 역순으로 정렬 되며 맨 위에 있는 **alerca 맨** 및 **Zeng** 는 아래쪽에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-209">The names on the horizontal axis are sorted in reverse order, with **Alerca** at the top and **Zeng** at the bottom.</span></span>  
  
##  <a name="5-move-the-legend"></a><a name="Legend"></a><span data-ttu-id="ce829-210">5. 범례 이동</span><span class="sxs-lookup"><span data-stu-id="ce829-210">5. Move the Legend</span></span>  
 <span data-ttu-id="ce829-211">차트 값을 더 쉽게 읽을 수 있도록 차트 범례를 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-211">To improve the readability of the chart values, you might want to move the chart legend.</span></span> <span data-ttu-id="ce829-212">예를 들어 막대가 가로로 표시되는 가로 막대형 차트에서는 범례가 차트 영역의 위나 아래에 표시되도록 범례 위치를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-212">For example, in a bar chart where bars are shown horizontally, you can change the position of the legend so that it is above or below the chart area.</span></span> <span data-ttu-id="ce829-213">이렇게 하면 막대의 가로 공간을 늘릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-213">This gives more horizontal space to the bars.</span></span>  
  
#### <a name="to-display-the-legend-below-the-chart-area-of-a-bar-chart"></a><span data-ttu-id="ce829-214">가로 막대형 차트의 차트 영역 아래쪽에 범례를 표시하려면</span><span class="sxs-lookup"><span data-stu-id="ce829-214">To display the legend below the chart area of a bar chart</span></span>  
  
1.  <span data-ttu-id="ce829-215">보고서 디자인 뷰로 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-215">Switch to report design view.</span></span>  
  
2.  <span data-ttu-id="ce829-216">차트의 범례를 마우스 오른쪽 단추로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-216">Right-click the legend on the chart.</span></span>  
  
3.  <span data-ttu-id="ce829-217">**범례 속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-217">Select **Legend Properties**.</span></span>  
  
4.  <span data-ttu-id="ce829-218">**범례 위치**에서 다른 위치를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-218">For **Legend position**, select a different position.</span></span> <span data-ttu-id="ce829-219">예를 들어 아래쪽 가운데 옵션으로 위치를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-219">For example, set the position to the middle bottom option.</span></span>  
  
     <span data-ttu-id="ce829-220">범례가 차트의 위쪽이나 아래쪽에 배치될 경우 범례 레이아웃은 세로에서 가로로 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-220">When the legend is placed at the top or bottom of a chart, the layout of the legend changes from vertical to horizontal.</span></span> <span data-ttu-id="ce829-221">**레이아웃** 드롭다운 목록에서 다른 레이아웃을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-221">You can select a different layout from the **Layout** drop-down list.</span></span>  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
6.  <span data-ttu-id="ce829-222">**실행** 을 클릭하여 보고서를 미리 봅니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-222">Click **Run** to preview the report.</span></span>  
  
##  <a name="6-title-the-chart"></a><a name="ChartTitle"></a><span data-ttu-id="ce829-223">6. 차트 제목</span><span class="sxs-lookup"><span data-stu-id="ce829-223">6. Title the Chart</span></span>  
  
#### <a name="to-change-the-chart-title-above-the-chart-area-of-a-bar-chart"></a><span data-ttu-id="ce829-224">가로 막대형 차트의 차트 영역 위쪽에 있는 차트 제목을 변경하려면</span><span class="sxs-lookup"><span data-stu-id="ce829-224">To change the chart title above the chart area of a bar chart</span></span>  
  
1.  <span data-ttu-id="ce829-225">보고서 디자인 뷰로 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-225">Switch to report design view.</span></span>  
  
2.  <span data-ttu-id="ce829-226">차트 위쪽의 **차트 제목** 단어를 선택 하 고 다음 텍스트를 입력 합니다. **판매: 2008 및 2009**</span><span class="sxs-lookup"><span data-stu-id="ce829-226">Select the words **Chart Title** at the top of the chart, and then type the following text: **Sales for 2008 and 2009**.</span></span>  
  
3.  <span data-ttu-id="ce829-227">텍스트 외부의 아무 곳이나 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-227">Click anywhere outside the text.</span></span>  
  
4.  <span data-ttu-id="ce829-228">**실행** 을 클릭하여 보고서를 미리 봅니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-228">Click **Run** to preview the report.</span></span>  
  
##  <a name="7-format-and-label-the-horizontal-axis"></a><a name="Horizontal"></a><span data-ttu-id="ce829-229">7. 가로 축의 서식 및 레이블 지정</span><span class="sxs-lookup"><span data-stu-id="ce829-229">7. Format and Label the Horizontal Axis</span></span>  
 <span data-ttu-id="ce829-230">기본적으로 가로 축에는 차트 크기에 맞게 자동으로 늘어나는 일반 형식으로 값이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-230">By default, the horizontal axis displays values in a general format that is automatically scaled to fit the size of the chart.</span></span>  
  
#### <a name="to-format-the-numbers-on-the-horizontal-axis"></a><span data-ttu-id="ce829-231">가로 축의 숫자에 형식을 지정하려면</span><span class="sxs-lookup"><span data-stu-id="ce829-231">To format the numbers on the horizontal axis</span></span>  
  
1.  <span data-ttu-id="ce829-232">보고서 디자인 뷰로 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-232">Switch to report design view.</span></span>  
  
2.  <span data-ttu-id="ce829-233">차트 아래쪽의 가로 축을 클릭하여 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-233">Click the horizontal axis along the bottom of the chart to select it.</span></span>  
  
     <span data-ttu-id="ce829-234">리본 메뉴의 **홈** 탭에 있는 **숫자** 그룹에서 **통화** 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-234">On the ribbon, on the **Home** tab, in the **Number** group, click the **Currency** button.</span></span> <span data-ttu-id="ce829-235">가로 축 레이블이 통화로 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-235">The horizontal axis labels change to currency.</span></span>  
  
3.  <span data-ttu-id="ce829-236">(선택 사항) 십진수를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-236">(Optional) Remove the decimal digits.</span></span> <span data-ttu-id="ce829-237">**통화** 단추 주위에 있는 **소수 자릿수 줄이기** 단추를 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-237">Near the **Currency** button, click the **Decrease Decimal** button twice.</span></span>  
  
4.  <span data-ttu-id="ce829-238">가로 축을 마우스 오른쪽 단추로 클릭한 다음 **가로 축 속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-238">Right-click the horizontal axis, and click **Horizontal Axis Properties**.</span></span>  
  
5.  <span data-ttu-id="ce829-239">**숫자** 탭에서 **천 단위로 값 표시를 선택 합니다.**</span><span class="sxs-lookup"><span data-stu-id="ce829-239">On the **Number** tab, select **Show values in Thousands.**</span></span>  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
7.  <span data-ttu-id="ce829-240">**축 제목** 을 마우스 오른쪽 단추로 클릭 하 고 **축 제목 속성**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-240">Right-click **Axis Title** and click **Axis Title Properties**.</span></span>  
  
8.  <span data-ttu-id="ce829-241">**제목 텍스트** 상자에 **천 단위로 Sales** 를 입력 하 고 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-241">In the **Title text** box, type **Sales in thousands** and click **OK**.</span></span>  
  
9. <span data-ttu-id="ce829-242">**실행** 을 클릭하여 보고서를 미리 봅니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-242">Click **Run** to preview the report.</span></span>  
  
 <span data-ttu-id="ce829-243">판매액은 보고서 가로 축에 천 단위로 표시되며 십진수가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-243">The report displays the sales amount on the horizontal axis as currency in thousands, and has no decimal digits.</span></span>  
  
##  <a name="8-add-a-filter-to-display-the-top-five-values"></a><a name="Filter"></a><span data-ttu-id="ce829-244">8. 상위 5 개 값을 표시 하는 필터 추가</span><span class="sxs-lookup"><span data-stu-id="ce829-244">8. Add a Filter to Display the Top Five Values</span></span>  
 <span data-ttu-id="ce829-245">차트에 필터를 추가하여 차트에 포함하거나 제외할 데이터 세트의 데이터를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-245">You can add a filter to the chart to specify which data from the dataset to include or exclude in the chart.</span></span>  
  
#### <a name="to-add-a-filter-and-display-the-top-five-values"></a><span data-ttu-id="ce829-246">상위 5개 값을 표시하는 필터를 추가하려면</span><span class="sxs-lookup"><span data-stu-id="ce829-246">To add a filter and display the top five values</span></span>  
  
1.  <span data-ttu-id="ce829-247">보고서 디자인 뷰로 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-247">Switch to report design view.</span></span>  
  
2.  <span data-ttu-id="ce829-248">차트를 두 번 클릭하여 **차트 데이터** 창을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-248">Double-click the chart to display the **Chart Data** pane.</span></span>  
  
3.  <span data-ttu-id="ce829-249">**범주 그룹** 영역에서 [LastName] 필드를 마우스 오른쪽 단추로 클릭한 다음 **범주 그룹 속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-249">In the **Category Groups** area, right-click the [LastName] field, and then click **Category Group Properties**.</span></span>  
  
4.  <span data-ttu-id="ce829-250">**필터**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-250">Click **Filters**.</span></span> <span data-ttu-id="ce829-251">**필터 변경** 페이지에 필터 식 목록이 표시될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-251">The **Change filters** page can display a list of filter expressions.</span></span> <span data-ttu-id="ce829-252">기본적으로 이 목록은 비어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-252">By default, this list is empty.</span></span>  
  
5.  <span data-ttu-id="ce829-253">**추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-253">Click **Add**.</span></span> <span data-ttu-id="ce829-254">새로운 빈 필터가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-254">A new blank filter appears.</span></span>  
  
6.  <span data-ttu-id="ce829-255">**식**에서 **[Sum (SalesYear2009)]** 을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-255">In **Expression**, type **[Sum(SalesYear2009)]**.</span></span> <span data-ttu-id="ce829-256">기본 식 `=Sum(Fields!SalesYear2009.Value)`이 만들어집니다. 이 식은 **fx** 단추를 클릭하면 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-256">This creates the underlying expression `=Sum(Fields!SalesYear2009.Value)`, which you can see if you click the **fx** button.</span></span>  
  
7.  <span data-ttu-id="ce829-257">데이터 형식이 **Text**인지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-257">Verify that the data type is **Text**.</span></span>  
  
8.  <span data-ttu-id="ce829-258">**연산자**의 드롭다운 목록에서 **Top N** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-258">In **Operator**, select **Top N** from the drop-down list.</span></span>  
  
9. <span data-ttu-id="ce829-259">**값**에 **=5**식을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-259">In **Value**, type the following expression: **=5**</span></span>  
  
10. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
11. <span data-ttu-id="ce829-260">**실행** 을 클릭하여 보고서를 미리 봅니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-260">Click **Run** to preview the report.</span></span>  
  
 <span data-ttu-id="ce829-261">보고서를 실행할 때 결과가 필터링되지 않으면 데이터를 수동으로 새로 고칩니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-261">If the results are not filtered when you run the report, you can refresh the data manually.</span></span> <span data-ttu-id="ce829-262">**탐색** 그룹의 **실행** 탭에서 **새로 고침**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-262">On the **Run** tab in the **Navigation** group, click **Refresh**.</span></span>  
  
 <span data-ttu-id="ce829-263">2009년도 매출 데이터에서 상위 5명에 속하는 영업 사원의 이름이 차트에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-263">The chart shows the top five salesperson names from the 2009 sales data.</span></span>  
  
##  <a name="9-add-a-report-title"></a><a name="Title"></a><span data-ttu-id="ce829-264">9. 보고서 제목 추가</span><span class="sxs-lookup"><span data-stu-id="ce829-264">9. Add a Report Title</span></span>  
  
#### <a name="to-add-a-report-title"></a><span data-ttu-id="ce829-265">보고서 제목을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="ce829-265">To add a report title</span></span>  
  
1.  <span data-ttu-id="ce829-266">디자인 화면에서 **제목을 추가하려면 클릭하십시오.** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-266">On the design surface, click **Click to add title**.</span></span>  
  
2.  <span data-ttu-id="ce829-267">**Sales Bar Chart**를 입력 하 고 enter 키를 누른 다음 **2009에 대 한 상위 5 개 판매자**를 입력 합니다. 그러면 다음과 같이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-267">Type **Sales Bar Chart**, press ENTER, and then type **Top Five Sellers for 2009**, so it looks like this:</span></span>  
  
     <span data-ttu-id="ce829-268">**Sales Bar Chart**</span><span class="sxs-lookup"><span data-stu-id="ce829-268">**Sales Bar Chart**</span></span>  
  
     <span data-ttu-id="ce829-269">**Top Five Sellers for 2009**</span><span class="sxs-lookup"><span data-stu-id="ce829-269">**Top Five Sellers for 2009**</span></span>  
  
3.  <span data-ttu-id="ce829-270">**Sales Bar Chart**를 선택하고 **굵게** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-270">Select **Sales Bar Chart**, and click the **Bold** button.</span></span>  
  
4.  <span data-ttu-id="ce829-271">**2009에 대 한 상위 5 개 판매자**를 선택 하 고 **홈** 탭의 **글꼴** 섹션에서 글꼴 크기를 **10**으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-271">Select **Top Five Sellers for 2009**, and in the **Font** section on the **Home** tab, set the font size to **10**.</span></span>  
  
5.  <span data-ttu-id="ce829-272">(선택 사항) 제목 입력란을 두 줄 텍스트를 포함하도록 크게 만들어야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-272">(Optional) You may need to make the Title text box taller to accommodate the two lines of text.</span></span>  
  
     <span data-ttu-id="ce829-273">이 제목은 보고서 맨 위에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-273">This title will appear at the top of the report.</span></span> <span data-ttu-id="ce829-274">페이지 머리글이 정의되지 않았을 경우 보고서 본문의 맨 위에 있는 항목은 보고서 머리글에 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-274">When there is no page header defined, items at the top of the report body are the equivalent of a report header.</span></span>  
  
6.  <span data-ttu-id="ce829-275">**실행** 을 클릭하여 보고서를 미리 봅니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-275">Click **Run** to preview the report.</span></span>  
  
##  <a name="10-save-the-report"></a><a name="Save"></a><span data-ttu-id="ce829-276">10. 보고서 저장</span><span class="sxs-lookup"><span data-stu-id="ce829-276">10. Save the Report</span></span>  
  
#### <a name="to-save-the-report"></a><span data-ttu-id="ce829-277">보고서를 저장하려면</span><span class="sxs-lookup"><span data-stu-id="ce829-277">To save the report</span></span>  
  
1.  <span data-ttu-id="ce829-278">보고서 디자인 뷰로 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-278">Switch to report design view.</span></span>  
  
2.  <span data-ttu-id="ce829-279">**보고서 작성기** 단추에서 다른 **이름으로 저장**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-279">From the **Report Builder** button, click **Save As**.</span></span>  
  
3.  <span data-ttu-id="ce829-280">**이름**에 **Sales Bar Chart**를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-280">In **Name**, type **Sales Bar Chart**.</span></span>  
  
4.  <span data-ttu-id="ce829-281">**저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-281">Click **Save**.</span></span>  
  
 <span data-ttu-id="ce829-282">보고서가 보고서 서버에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-282">Your report is saved on the report server.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="ce829-283">다음 단계</span><span class="sxs-lookup"><span data-stu-id="ce829-283">Next Steps</span></span>  
 <span data-ttu-id="ce829-284">보고서에 가로 막대형 차트 추가 자습서를 성공적으로 완료했습니다.</span><span class="sxs-lookup"><span data-stu-id="ce829-284">You have successfully completed the Adding a Bar Chart to Your Report tutorial.</span></span> <span data-ttu-id="ce829-285">차트에 대한 자세한 내용은 [차트&#40;보고서 작성기 및 SSRS&#41;](report-design/charts-report-builder-and-ssrs.md) 및 [스파크라인 및 데이터 막대&#40;보고서 작성기 및 SSRS&#41;](report-design/sparklines-and-data-bars-report-builder-and-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ce829-285">To learn more about charts, see [Charts &#40;Report Builder and SSRS&#41;](report-design/charts-report-builder-and-ssrs.md) and [Sparklines and Data Bars &#40;Report Builder and SSRS&#41;](report-design/sparklines-and-data-bars-report-builder-and-ssrs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce829-286">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ce829-286">See Also</span></span>  
 <span data-ttu-id="ce829-287">[자습서 &#40;보고서 작성기&#41;](report-builder-tutorials.md) </span><span class="sxs-lookup"><span data-stu-id="ce829-287">[Tutorials &#40;Report Builder&#41;](report-builder-tutorials.md) </span></span>  
 [<span data-ttu-id="ce829-288">SQL Server 2014의 보고서 작성기</span><span class="sxs-lookup"><span data-stu-id="ce829-288">Report Builder in SQL Server 2014</span></span>](report-builder/report-builder-in-sql-server-2016.md)  
  
  
