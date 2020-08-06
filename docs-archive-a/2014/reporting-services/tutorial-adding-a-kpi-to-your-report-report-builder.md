---
title: '자습서: 보고서에 KPI 추가(보고서 작성기) | Microsoft Docs'
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 1bf77859-0b33-4f40-abaf-ebeeb6ebb1f8
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 405978721068583597adf5c4257978a222121078
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735936"
---
# <a name="tutorial-adding-a-kpi-to-your-report-report-builder"></a><span data-ttu-id="98186-102">자습서: 보고서에 KPI 추가(보고서 작성기)</span><span class="sxs-lookup"><span data-stu-id="98186-102">Tutorial: Adding a KPI to Your Report (Report Builder)</span></span>
  <span data-ttu-id="98186-103">KPI(핵심 성과 지표)는 비즈니스에 중요한 의미가 있는 측정 가능한 값입니다.</span><span class="sxs-lookup"><span data-stu-id="98186-103">A key performance indicator (KPI) is a measurable value that has business significance.</span></span> <span data-ttu-id="98186-104">이 자습서에서는 KPI를 보고서에 포함하는 방법을 배웁니다.</span><span class="sxs-lookup"><span data-stu-id="98186-104">This tutorial teaches you how to include a (KPI) in a report.</span></span> <span data-ttu-id="98186-105">이 시나리오에서 제품 하위 범주별 판매 요약이 KPI입니다.</span><span class="sxs-lookup"><span data-stu-id="98186-105">In this scenario, the sales summary by product subcategories is the KPI.</span></span> <span data-ttu-id="98186-106">KPI의 현재 상태는 색, 계기 및 표시기를 사용하여 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="98186-106">The current state of the KPI is shown by using colors, gauges, and indicators.</span></span>  
  
 <span data-ttu-id="98186-107">다음 그림에서는 만들려는 보고서를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="98186-107">The following illustration shows the report that you will create.</span></span>  
  
 <span data-ttu-id="98186-108">![rs_AddKPITutorial](../../2014/tutorials/media/rs-addkpitutorial.gif "rs_AddKPITutorial")</span><span class="sxs-lookup"><span data-stu-id="98186-108">![rs_AddKPITutorial](../../2014/tutorials/media/rs-addkpitutorial.gif "rs_AddKPITutorial")</span></span>  
  
##  <a name="what-you-will-learn"></a><a name="BackToTop"></a><span data-ttu-id="98186-109">학습 내용</span><span class="sxs-lookup"><span data-stu-id="98186-109">What You Will Learn</span></span>  
 <span data-ttu-id="98186-110">이 자습서에서는 셀 값에 기초한 테이블 셀의 배경색을 설정하여 KPI를 추가하고 계기 및 표시기를 추가 및 구성하는 방법을 배웁니다.</span><span class="sxs-lookup"><span data-stu-id="98186-110">In this tutorial, you will learn to add a KPI by setting the background color of table cells based on cell value and add and configure a gauge and an indicator.</span></span> <span data-ttu-id="98186-111">또한 테이블 셀의 배경색을 설정하는 식을 작성하는 방법을 배웁니다.</span><span class="sxs-lookup"><span data-stu-id="98186-111">You also learn to write the expression that sets the background color of the table cells.</span></span>  
  
 <span data-ttu-id="98186-112">이 자습서에는 다음과 같은 절차가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98186-112">This tutorial contains the following procedures:</span></span>  
  
1.  [<span data-ttu-id="98186-113">테이블 또는 행렬 마법사에서 테이블 보고서 및 데이터 세트 만들기</span><span class="sxs-lookup"><span data-stu-id="98186-113">Create a Table Report and Dataset from the Table or Matrix Wizard</span></span>](#Table)  
  
2.  [<span data-ttu-id="98186-114">테이블 또는 행렬 마법사에서 데이터 구성 및 레이아웃과 스타일 선택</span><span class="sxs-lookup"><span data-stu-id="98186-114">Organize Data, Choose Layout, and Style from the Table or Matrix Wizard</span></span>](#CompleteWizard)  
  
3.  [<span data-ttu-id="98186-115">배경색을 사용하여 KPI 표시</span><span class="sxs-lookup"><span data-stu-id="98186-115">Use Background Colors to Display a KPI</span></span>](#BackgroundColors)  
  
4.  [<span data-ttu-id="98186-116">계기를 사용하여 KPI 표시</span><span class="sxs-lookup"><span data-stu-id="98186-116">Display a KPI by Using a Gauge</span></span>](#Gauge)  
  
5.  [<span data-ttu-id="98186-117">표시기를 사용하여 KPI 표시</span><span class="sxs-lookup"><span data-stu-id="98186-117">Display a KPI by Using an Indicator</span></span>](#Indicator)  
  
6.  [<span data-ttu-id="98186-118">보고서 제목 추가</span><span class="sxs-lookup"><span data-stu-id="98186-118">Add a Report Title</span></span>](#Title)  
  
7.  [<span data-ttu-id="98186-119">보고서 저장</span><span class="sxs-lookup"><span data-stu-id="98186-119">Save the Report</span></span>](#Save)  
  
> [!NOTE]  
>  <span data-ttu-id="98186-120">이 자습서에서 마법사의 단계는 두 개의 절차로 통합됩니다. 하나는 데이터 세트를 만드는 절차이고 다른 하나는 테이블을 만드는 절차입니다.</span><span class="sxs-lookup"><span data-stu-id="98186-120">In this tutorial, the steps for the wizard are consolidated into two procedures: one to create the dataset and one to create a table.</span></span> <span data-ttu-id="98186-121">보고서 서버를 찾고, 데이터 원본을 선택하고, 데이터 세트를 만들고, 마법사를 실행하는 방법에 대한 단계별 지침은 이 시리즈의 첫 번째 자습서인 [자습서: 기본 테이블 보고서 만들기&#40;보고서 작성기&#41;](../reporting-services/tutorial-creating-a-basic-table-report-report-builder.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="98186-121">For step-by-step instructions about how to browse to a report server, choose a data source, create a dataset, and run the wizard, see the first tutorial in this series: [Tutorial: Creating a Basic Table Report &#40;Report Builder&#41;](../reporting-services/tutorial-creating-a-basic-table-report-report-builder.md).</span></span>  
  
 <span data-ttu-id="98186-122">이 자습서에 소요되는 예상 시간: 15분</span><span class="sxs-lookup"><span data-stu-id="98186-122">Estimated time to complete this tutorial: 15 minutes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="98186-123">요구 사항</span><span class="sxs-lookup"><span data-stu-id="98186-123">Requirements</span></span>  
 <span data-ttu-id="98186-124">요구 사항에 대한 자세한 내용은 [자습서의 필수 조건&#40;보고서 작성기&#41;](../reporting-services/report-builder-tutorials.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="98186-124">For more information about requirements, see [Prerequisites for Tutorials &#40;Report Builder&#41;](../reporting-services/report-builder-tutorials.md).</span></span>  
  
##  <a name="1-create-a-table-report-and-dataset-from-the-table-or-matrix-wizard"></a><a name="Table"></a><span data-ttu-id="98186-125">1. 테이블 또는 행렬 마법사에서 테이블 보고서 및 데이터 집합 만들기</span><span class="sxs-lookup"><span data-stu-id="98186-125">1. Create a Table Report and Dataset from the Table or Matrix Wizard</span></span>  
 <span data-ttu-id="98186-126">**시작** 대화 상자에서 공유 데이터 원본을 선택 하 고, 포함 된 데이터 집합을 만들고, 테이블에 데이터를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="98186-126">From the **Getting Started** dialog box, choose a shared data source, create an embedded dataset, and display the data in a table.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="98186-127">이 자습서의 쿼리에는 데이터 값이 포함되어 있으므로 외부 데이터 원본이 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="98186-127">In this tutorial, the query contains the data values, so that it does not need an external data source.</span></span> <span data-ttu-id="98186-128">따라서 쿼리가 상당히 길어집니다.</span><span class="sxs-lookup"><span data-stu-id="98186-128">This makes the query quite long.</span></span> <span data-ttu-id="98186-129">비즈니스 환경에서는 쿼리에 데이터가 포함되지 않을 것입니다.</span><span class="sxs-lookup"><span data-stu-id="98186-129">In a business environment, a query would not contain the data.</span></span> <span data-ttu-id="98186-130">이 자습서의 쿼리는 학습용으로만 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="98186-130">This is for learning purposes only.</span></span>  
  
#### <a name="to-create-a-new-table"></a><span data-ttu-id="98186-131">새 테이블을 만들려면</span><span class="sxs-lookup"><span data-stu-id="98186-131">To create a new table</span></span>  
  
1.  <span data-ttu-id="98186-132">**시작**을 클릭하고 **프로그램**, **Microsoft SQL Server 2012 보고서 작성기**를 차례로 가리킨 다음 **보고서 작성기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="98186-132">Click **Start**, point to **Programs**, point to **Microsoft SQL Server 2012 Report Builder**, and then click **Report Builder**.</span></span>  
  
     <span data-ttu-id="98186-133">**시작** 대화 상자가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="98186-133">The **Getting Started** dialog box appears.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="98186-134">**시작** 대화 상자가 나타나지 않으면 보고서 작성기 단추에서 **새로 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="98186-134">If the **Getting Started** dialog box does not appear, from the Report Builder button, click **New**.</span></span>  
  
2.  <span data-ttu-id="98186-135">왼쪽 창에 **새 보고서** 가 선택되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="98186-135">In the left pane, verify that **New Report** is selected.</span></span>  
  
3.  <span data-ttu-id="98186-136">오른쪽 창에서 **테이블 또는 행렬 마법사**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="98186-136">In the right pane, click **Table or Matrix Wizard**.</span></span>  
  
4.  <span data-ttu-id="98186-137">데이터 세트 선택 페이지에서 **데이터 세트 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="98186-137">On the Choose a dataset page, click **Create a dataset**.</span></span>  
  
5.  <span data-ttu-id="98186-138">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="98186-138">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="98186-139">**데이터 원본에 대 한 연결 선택** 페이지에서 기존 데이터 원본을 선택 하거나 보고서 서버를 찾아 데이터 원본을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="98186-139">On the **Choose a connection to a data source** page, select an existing data source or browse to the report server and select a data source.</span></span> <span data-ttu-id="98186-140">데이터 원본을 사용할 수 없거나 보고서 서버에 대한 액세스 권한이 없는 경우 포함된 데이터 원본을 대신 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98186-140">If there no data source is available or you do not have access to a report server, you can use an embedded data source instead.</span></span> <span data-ttu-id="98186-141">자세한 내용은 [자습서: 기본 테이블 보고서 만들기&#40;보고서 작성기&#41;](../reporting-services/tutorial-creating-a-basic-table-report-report-builder.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="98186-141">For more information, see [Tutorial: Creating a Basic Table Report &#40;Report Builder&#41;](../reporting-services/tutorial-creating-a-basic-table-report-report-builder.md).</span></span>  
  
7.  <span data-ttu-id="98186-142">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="98186-142">Click **Next**.</span></span>  
  
8.  <span data-ttu-id="98186-143">**쿼리 디자인** 페이지에서 **텍스트로 편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="98186-143">On the **Design a query** page, click **Edit as Text**.</span></span>  
  
9. <span data-ttu-id="98186-144">쿼리 창에 다음 쿼리를 복사하여 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="98186-144">Copy and paste the following query into the query pane:</span></span>  
  
    ```  
    SELECT CAST('2009-01-05' AS date) as SalesDate, 'Accessories' as Subcategory,   
       'Carrying Case' as Product, CAST(16996.60 AS money) AS Sales, 68 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Accessories' as Subcategory,  
       'Tripod' as Product, CAST(1350.00 AS money) AS Sales, 18 as Quantity  
    UNION SELECT CAST('2009-01-11' AS date) as SalesDate, 'Accessories' as Subcategory,  
       'Lens Adapter' as Product, CAST(1147.50 AS money) AS Sales, 17 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Accessories' as Subcategory,  
       'Mini Battery Charger' as Product, CAST(1056.00 AS money) AS Sales, 44 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate,  'Accessories' as Subcategory,  
       'Telephoto Conversion Lens' as Product, CAST(1380.00 AS money) AS Sales, 18 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate,'Accessories' as Subcategory,    
       'USB Cable' as Product, CAST(780.00 AS money) AS Sales, 26 as Quantity  
    UNION SELECT CAST('2009-01-08' AS date) as SalesDate, 'Accessories' as Subcategory,   
       'Budget Movie-Maker' as Product, CAST(3798.00 AS money) AS Sales, 9 as Quantity  
    UNION SELECT CAST('2009-01-09' AS date) as SalesDate, 'Camcorders' as Subcategory,   
       'Business Videographer' as Product, CAST(10400.00 AS money) AS Sales, 13 as Quantity  
    UNION SELECT CAST('2009-01-10' AS date) as SalesDate, 'Camcorders' as Subcategory,   
       'Social Videographer' as Product, CAST(3000.00 AS money) AS Sales, 60 as Quantity  
    UNION SELECT CAST('2009-01-11' AS date) as SalesDate,  'Digital' as Subcategory,   
       'Advanced Digital' as Product, CAST(7234.50 AS money) AS Sales, 39 as Quantity  
    UNION SELECT CAST('2009-01-07' AS date) as SalesDate,  'Digital' as Subcategory,   
       'Compact Digital' as Product, CAST(10836.00 AS money) AS Sales, 84 as Quantity  
    UNION SELECT CAST('2009-01-08' AS date) as SalesDate,  'Digital' as Subcategory,   
       'Consumer Digital' as Product, CAST(2550.00 AS money) AS Sales, 17 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Digital' as Subcategory,   
       'Slim Digital' as Product, CAST(8357.80 AS money) AS Sales, 44 as Quantity  
    UNION SELECT CAST('2009-01-09' AS date) as SalesDate, 'Digital SLR' as Subcategory,   
       'SLR Camera 35mm' as Product, CAST(18530.00 AS money) AS Sales, 34 as Quantity  
    UNION SELECT CAST('2009-01-07' AS date) as SalesDate, 'Digital SLR' as Subcategory,   
       'SLR Camera' as Product, CAST(26576.00 AS money) AS Sales, 88 as Quantity  
    ```  
  
10. <span data-ttu-id="98186-145">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="98186-145">Click **Next**.</span></span>  
  
##  <a name="2-organize-data-choose-layout-and-style-from-the-table-or-matrix-wizard"></a><a name="CompleteWizard"></a><span data-ttu-id="98186-146">2. 테이블 또는 행렬 마법사에서 데이터 구성, 레이아웃 및 스타일 선택</span><span class="sxs-lookup"><span data-stu-id="98186-146">2. Organize Data, Choose Layout, and Style from the Table or Matrix Wizard</span></span>  
 <span data-ttu-id="98186-147">이 마법사를 사용하여 데이터를 표시할 시작 디자인을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98186-147">Use the wizard to provide a starting design on which to display data.</span></span> <span data-ttu-id="98186-148">이 마법사의 미리 보기 창에서는 테이블 또는 행렬 디자인을 완료하기 전에 데이터 그룹화의 결과를 시각화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98186-148">The preview pane in the wizard helps you to visualize the result of grouping data before you complete the table or matrix design.</span></span>  
  
#### <a name="to-organize-data-into-groups-choose-a-layout-and-a-style"></a><span data-ttu-id="98186-149">데이터를 그룹으로 구성하고 레이아웃과 스타일을 선택하려면</span><span class="sxs-lookup"><span data-stu-id="98186-149">To organize data into groups, choose a layout and a style</span></span>  
  
1.  <span data-ttu-id="98186-150">필드 정렬 페이지에서 **값**에 Product를 끌어옵니다.</span><span class="sxs-lookup"><span data-stu-id="98186-150">On the Arrange fields page, drag Product to **Values**.</span></span>  
  
2.  <span data-ttu-id="98186-151">**값** 의 Product 아래에 Quantity를 끌어옵니다.</span><span class="sxs-lookup"><span data-stu-id="98186-151">Drag Quantity to **Values** and place below Product.</span></span>  
  
     <span data-ttu-id="98186-152">Quantity는 숫자 필드를 요약하기 위한 기본 함수인 Sum 함수를 사용하여 요약됩니다.</span><span class="sxs-lookup"><span data-stu-id="98186-152">Quantity is summarized with the Sum function, the default function to summarize numeric fields.</span></span>  
  
3.  <span data-ttu-id="98186-153">**값** 의 Quantity 아래에 Sales를 끌어옵니다.</span><span class="sxs-lookup"><span data-stu-id="98186-153">Drag Sales to **Values** and place below Quantity.</span></span>  
  
     <span data-ttu-id="98186-154">1, 2, 3단계에서는 테이블에 표시할 데이터를 지정했습니다.</span><span class="sxs-lookup"><span data-stu-id="98186-154">Steps 1, 2, and 3 specify the data to display in the table.</span></span>  
  
4.  <span data-ttu-id="98186-155">**행 그룹**에 SalesDate를 끌어옵니다.</span><span class="sxs-lookup"><span data-stu-id="98186-155">Drag SalesDate to **Row groups**.</span></span>  
  
5.  <span data-ttu-id="98186-156">**행 그룹** 의 SalesDate 아래에 Subcategory를 끌어옵니다.</span><span class="sxs-lookup"><span data-stu-id="98186-156">Drag Subcategory to **Row groups** and place below SalesDate.</span></span>  
  
     <span data-ttu-id="98186-157">4, 5단계에서는 필드 값을 먼저 날짜 기준으로 정렬한 다음 해당 날짜의 모든 판매를 기준으로 정렬했습니다.</span><span class="sxs-lookup"><span data-stu-id="98186-157">Steps 4 and 5 organize the values for the fields first by date, and then by all sales for that date.</span></span>  
  
6.  <span data-ttu-id="98186-158">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="98186-158">Click **Next**.</span></span>  
  
     <span data-ttu-id="98186-159">보고서를 실행하면 테이블에 각 날짜, 각 날짜의 모든 주문, 각 주문의 모든 제품, 수량 및 판매 합계가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="98186-159">When you run the report, the table displays each date, all orders for each date, and all products, quantities, and sales totals for each order.</span></span>  
  
7.  <span data-ttu-id="98186-160">레이아웃 선택 페이지의 **옵션**에서 **부분합 및 총합계 표시** 가 선택되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="98186-160">On the Choose the Layout page, under **Options**, verify that **Show subtotals and grand totals** is selected.</span></span>  
  
8.  <span data-ttu-id="98186-161">**블록형, 부분합 하단 표시** 가 선택되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="98186-161">Verify that **Blocked, subtotal below** is selected.</span></span>  
  
9. <span data-ttu-id="98186-162">**그룹 확장/축소**옵션을 선택 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="98186-162">Clear the option **Expand/collapse groups**.</span></span>  
  
     <span data-ttu-id="98186-163">이 자습서에서 만든 보고서에는 부모 그룹 계층을 확장하여 자식 그룹 행 및 정보 행을 표시하는 데 사용할 수 있는 드릴다운 기능이 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="98186-163">In this tutorial, the report you create does not use the drilldown feature that lets a user expand a parent group hierarchy to display child group rows and detail rows.</span></span>  
  
10. <span data-ttu-id="98186-164">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="98186-164">Click **Next**.</span></span>  
  
11. <span data-ttu-id="98186-165">스타일 선택 페이지의 스타일 창에서 스타일을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="98186-165">On the Choose a Style page, in the Styles pane, select a style.</span></span>  
  
     <span data-ttu-id="98186-166">완성된 보고서 그림에서는 Ocean 스타일을 사용하는 보고서를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="98186-166">The illustration of the completed report shows the report using the Ocean style.</span></span>  
  
12. <span data-ttu-id="98186-167">**Finish**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="98186-167">Click **Finish**.</span></span>  
  
     <span data-ttu-id="98186-168">디자인 화면에 테이블이 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="98186-168">The table is added to the design surface.</span></span> <span data-ttu-id="98186-169">이 테이블에는 열 5개와 행 5개가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98186-169">The table has five columns and five rows.</span></span> <span data-ttu-id="98186-170">행 그룹 창에는 SalesDate, Subcategory 및 Details라는 3개의 행 그룹이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="98186-170">The Row Groups pane shows three row groups: SalesDate, Subcategory, and Details.</span></span> <span data-ttu-id="98186-171">세부 데이터는 모두 데이터 세트 쿼리로 검색된 데이터입니다.</span><span class="sxs-lookup"><span data-stu-id="98186-171">Detail data is all the data that is retrieved by the dataset query.</span></span>  
  
13. <span data-ttu-id="98186-172">**실행** 을 클릭하여 보고서를 미리 봅니다.</span><span class="sxs-lookup"><span data-stu-id="98186-172">Click **Run** to preview the report.</span></span>  
  
 <span data-ttu-id="98186-173">특정 날짜에 판매되는 각 제품에 대한 제품 이름, 판매 수량 및 판매 합계가 테이블에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="98186-173">For each product that is sold on a specific date, the table displays the product name, the quantity sold, and the sales total.</span></span> <span data-ttu-id="98186-174">이 데이터는 먼저 판매 날짜를 기준으로 정렬된 다음 하위 범주를 기준으로 정렬됩니다.</span><span class="sxs-lookup"><span data-stu-id="98186-174">The data is organized first by sales date and then by subcategory.</span></span>  
  
##  <a name="3-use-background-colors-to-display-a-kpi"></a><a name="BackgroundColors"></a><span data-ttu-id="98186-175">3. 배경색을 사용 하 여 KPI 표시</span><span class="sxs-lookup"><span data-stu-id="98186-175">3. Use Background Colors to Display a KPI</span></span>  
 <span data-ttu-id="98186-176">배경색을 보고서 실행 시 계산되는 식으로 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98186-176">Background colors can be set to an expression that is evaluated when you run the report.</span></span>  
  
#### <a name="to-display-the-present-state-of-a-kpi-by-using-background-colors"></a><span data-ttu-id="98186-177">배경색을 사용하여 KPI의 현재 상태를 표시하려면</span><span class="sxs-lookup"><span data-stu-id="98186-177">To display the present state of a KPI by using background colors</span></span>  
  
1.  <span data-ttu-id="98186-178">테이블에서 `[Sum(Sales)]` 셀 (하위 범주의 판매를 표시 하는 부분합 행)에서 두 셀을 마우스 오른쪽 단추로 클릭 한 다음 **입력란 속성**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="98186-178">In the table, right-click two cells down from the `[Sum(Sales)]` cell (the subtotal row that displays the sales for a subcategory), and then click **Text Box Properties**.</span></span>  
  
2.  <span data-ttu-id="98186-179">**채우기**에서 **채우기 색** 옵션 옆에 있는 **fx** 단추를 클릭 하 고 다음 **에 대 한 식 설정: BackgroundColor** 필드에 다음 식을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="98186-179">In **Fill**, click the **fx** button next to the **Fill color** option and enter the following expression in the **Set expression for: BackgroundColor** field:</span></span>  
  
 `=IIF(Sum(Fields!Sales.Value) >= 5000 ,"Lime", IIF(Sum(Fields!Sales.Value) < 2500, "Red","Yellow"))`  
  
 <span data-ttu-id="98186-180">이렇게 하면 `[Sum(Sales)]`의 집계된 합계가 5000보다 크거나 같은 각 셀의 배경색이 "라임"이라는 녹색 음영을 사용하여 녹색으로 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="98186-180">This changes the background color to green, using the shade of green named "Lime", for each cell that contains an aggregated sum for `[Sum(Sales)]` that is greater than or equal to 5000.</span></span> <span data-ttu-id="98186-181">2500에서 5000 사이의 `[Sum(Sales)]` 값은 노란색으로 표시되고,</span><span class="sxs-lookup"><span data-stu-id="98186-181">Values of `[Sum(Sales)]` between 2500 and 5000 are colored yellow.</span></span> <span data-ttu-id="98186-182">2500보다 작은 값은 빨간색으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="98186-182">Values less than 2500 are colored red.</span></span>  
  
1.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
2.  <span data-ttu-id="98186-183">**실행** 을 클릭하여 보고서를 미리 봅니다.</span><span class="sxs-lookup"><span data-stu-id="98186-183">Click **Run** to preview the report.</span></span>  
  
 <span data-ttu-id="98186-184">하위 범주에 대한 판매가 표시되는 부분합 행에서 셀의 배경색은 판매 합계 값에 따라 빨강, 노랑 또는 녹색으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="98186-184">In the subtotal row that displays the sales for a subcategory, the background color of the cell is red, yellow, or green depending on value of the sales sum.</span></span>  
  
##  <a name="4-display-a-kpi-by-using-a-gauge"></a><a name="Gauge"></a><span data-ttu-id="98186-185">4. 계기를 사용 하 여 KPI 표시</span><span class="sxs-lookup"><span data-stu-id="98186-185">4. Display a KPI by Using a Gauge</span></span>  
 <span data-ttu-id="98186-186">계기는 데이터 세트의 단일 값을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="98186-186">A gauge depicts a single value in a dataset.</span></span> <span data-ttu-id="98186-187">이 자습서에서는 가로 선형 계기를 사용합니다. 이는 이 계기가 작은 크기로 테이블 셀 안에 사용될 경우에도 모양이 읽기 쉽고 단순하기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="98186-187">This tutorial uses a horizontal linear gauge because its shape and simplicity makes it easy to read, even in when it is a small size and used within a table cell.</span></span> <span data-ttu-id="98186-188">자세한 내용은 [계기&#40;보고서 작성기 및 SSRS&#41;](report-design/gauges-report-builder-and-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="98186-188">For more information, see [Gauges &#40;Report Builder and SSRS&#41;](report-design/gauges-report-builder-and-ssrs.md).</span></span>  
  
#### <a name="to-display-the-present-state-of-a-kpi-using-a-gauge"></a><span data-ttu-id="98186-189">계기를 사용하여 KPI의 현재 상태를 표시하려면</span><span class="sxs-lookup"><span data-stu-id="98186-189">To display the present state of a KPI using a gauge</span></span>  
  
1.  <span data-ttu-id="98186-190">디자인 뷰로 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="98186-190">Switch to Design view.</span></span>  
  
2.  <span data-ttu-id="98186-191">테이블에서 이전 절차에서 변경한 셀의 열 처리기를 마우스 오른쪽 단추로 클릭 하 고 **열 삽입**을 가리킨 다음 **오른쪽**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="98186-191">In the table, right-click the column handler for the cell that you changed in the previous procedure, point to **Insert Column**, and then click **Right**.</span></span> <span data-ttu-id="98186-192">테이블에 새 열이 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="98186-192">A new column is added to the table.</span></span>  
  
3.  <span data-ttu-id="98186-193">열 머리글에 **KPI** 를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="98186-193">Type **KPI** in the column heading.</span></span>  
  
4.  <span data-ttu-id="98186-194">**삽입** 탭의 **데이터 영역** 그룹에서 **계기**를 클릭 한 다음 테이블 외부의 디자인 화면을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="98186-194">On the **Insert** tab, in the **Data Regions** group, click **Gauge**, and then click the design surface outside the table.</span></span> <span data-ttu-id="98186-195">**계기 유형 선택** 대화 상자가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="98186-195">The **Select Gauge Type** dialog box appears.</span></span>  
  
5.  <span data-ttu-id="98186-196">**선형**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="98186-196">Click **Linear**.</span></span> <span data-ttu-id="98186-197">첫 번째 선형 계기 유형인 **가로**가 선택 됩니다.</span><span class="sxs-lookup"><span data-stu-id="98186-197">The first linear gauge type, **Horizontal**, is selected.</span></span>  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
     <span data-ttu-id="98186-198">디자인 화면에 계기가 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="98186-198">A gauge is added to the design surface.</span></span>  
  
7.  <span data-ttu-id="98186-199">보고서 데이터 창에서 Sales를 계기로 끌어 옵니다.</span><span class="sxs-lookup"><span data-stu-id="98186-199">From the Report Data pane, drag Sales to the gauge.</span></span> <span data-ttu-id="98186-200">계기로 Sales를 끌 경우 계기 데이터 창이 열립니다.</span><span class="sxs-lookup"><span data-stu-id="98186-200">When you drag Sales across the gauge, the Gauge Data pane opens.</span></span>  
  
8.  <span data-ttu-id="98186-201">**값** 목록에서 Sales를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="98186-201">Drop Sales in the **Values** list.</span></span>  
  
     <span data-ttu-id="98186-202">필드를 계기에 놓으면 기본 제공 Sum 함수를 사용하여 필드가 집계됩니다.</span><span class="sxs-lookup"><span data-stu-id="98186-202">When you drop the field onto the gauge, the field is aggregated by using the built-in Sum function.</span></span>  
  
9. <span data-ttu-id="98186-203">계기에서 포인터를 마우스 오른쪽 단추로 클릭 하 고 **포인터 속성**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="98186-203">Right-click the pointer in the gauge and click **Pointer Properties**.</span></span>  
  
10. <span data-ttu-id="98186-204">**포인터 형식**에서 **막대**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="98186-204">In **Pointer Type**, select **Bar**.</span></span> <span data-ttu-id="98186-205">이렇게 하면 포인터가 표식에서 막대로 변경되어 테이블에 계기를 추가할 때 더 잘 보입니다.</span><span class="sxs-lookup"><span data-stu-id="98186-205">This changes the pointer from a marker to a bar that will be more visible when the gauge is added to the table.</span></span>  
  
11. <span data-ttu-id="98186-206">**포인터 채우기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="98186-206">Click **Pointer Fill**.</span></span> <span data-ttu-id="98186-207">**보조 색** 에서 **노랑**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="98186-207">In **Secondary Color,** pick **Yellow**.</span></span> <span data-ttu-id="98186-208">그라데이션 채우기 패턴이 흰색에서 노란색으로 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="98186-208">The gradient fill pattern will change from white to yellow.</span></span>  
  
12. <span data-ttu-id="98186-209">계기 눈금을 마우스 오른쪽 단추로 클릭하고 **눈금 속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="98186-209">Right-click the scale in the gauge and click **Scale Properties**.</span></span>  
  
13. <span data-ttu-id="98186-210">**최대** 옵션을 25000으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="98186-210">Set the **Maximum** option to 25000.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="98186-211">25000과 같은 상수 대신 식을 사용하여 **최대값** 옵션의 값을 동적으로 계산할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98186-211">Instead of a constant such as 25000, you can use an expression to dynamically calculate the value of the **Maximum** option.</span></span> <span data-ttu-id="98186-212">이 식은 집계 기능의 집계를 사용하며 `=Max(Sum(Fields!Sales.value), "Tablix1")`식처럼 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="98186-212">The expression would use the aggregate of aggregate feature and look similar to the expression `=Max(Sum(Fields!Sales.value), "Tablix1")`.</span></span>  
  
14. <span data-ttu-id="98186-213">테이블에 있는 계기를 앞서 삽입한 열의 하위 범주에 대한 판매를 표시하는 부분합 행의 세 번째 셀로 끌어옵니다.</span><span class="sxs-lookup"><span data-stu-id="98186-213">Drag the gauge inside the table into the third cell in the subtotal row that displays the sales for a subcategory of the column that you inserted.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="98186-214">가로 선형 계기가 셀에 맞도록 열 크기를 조정해야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98186-214">You might have to resize the column so that the horizontal linear gauge fits into the cell.</span></span> <span data-ttu-id="98186-215">열 크기를 조정하려면 열 머리글을 클릭하고 핸들을 사용하여 셀 크기를 가로 또는 세로로 조정합니다.</span><span class="sxs-lookup"><span data-stu-id="98186-215">To resize the column, click a column header and use the handles to resize the cells horizontally and vertically.</span></span>  
  
15. <span data-ttu-id="98186-216">**실행** 을 클릭하여 보고서를 미리 봅니다.</span><span class="sxs-lookup"><span data-stu-id="98186-216">Click **Run** to preview the report.</span></span>  
  
     <span data-ttu-id="98186-217">계기에서 막대의 가로 길이는 KPI 값에 따라 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="98186-217">The horizontal length of the bar in the gauge changes depending on the value of the KPI.</span></span>  
  
16. <span data-ttu-id="98186-218">(선택 사항) 최대값 핀을 추가하여 범위 최대값을 초과하는 값이 항상 최대값 핀을 가리키도록 함으로써 오버플로를 해결합니다.</span><span class="sxs-lookup"><span data-stu-id="98186-218">(Optional) Add a maximum pin to handle overflow so that any value over the scale maximum always points to the maximum pin:</span></span>  
  
    1.  <span data-ttu-id="98186-219">속성 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="98186-219">Open the Properties pane.</span></span>  
  
    2.  <span data-ttu-id="98186-220">눈금을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="98186-220">Click the scale.</span></span> <span data-ttu-id="98186-221">선형 눈금의 속성이 속성 창에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="98186-221">The properties for the linear scale are displayed in the Properties pane.</span></span>  
  
    3.  <span data-ttu-id="98186-222">**크기 조정 핀** 범주에서 **maximumpin** 노드를 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="98186-222">In the **Scale Pins** category, expand the **MaximumPin** node.</span></span>  
  
    4.  <span data-ttu-id="98186-223">**사용** 속성을로 설정 `True` 합니다.</span><span class="sxs-lookup"><span data-stu-id="98186-223">Set the **Enable** property to `True`.</span></span> <span data-ttu-id="98186-224">눈금의 최대값 뒤에 핀이 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="98186-224">A pin appears after the maximum value on the scale.</span></span>  
  
    5.  <span data-ttu-id="98186-225">**BorderColor** 을로 설정 `Lime` 합니다.</span><span class="sxs-lookup"><span data-stu-id="98186-225">Set **BorderColor** to `Lime`.</span></span>  
  
17. <span data-ttu-id="98186-226">**실행** 을 클릭하여 보고서를 미리 봅니다.</span><span class="sxs-lookup"><span data-stu-id="98186-226">Click **Run** to preview the report.</span></span>  
  
##  <a name="5-display-a-kpi-by-using-an-indicator"></a><a name="Indicator"></a><span data-ttu-id="98186-227">5. 표시기를 사용 하 여 KPI 표시</span><span class="sxs-lookup"><span data-stu-id="98186-227">5. Display a KPI by Using an Indicator</span></span>  
 <span data-ttu-id="98186-228">표시기는 데이터 값을 한 눈에 파악할 수 있는 작고 간단한 계기입니다.</span><span class="sxs-lookup"><span data-stu-id="98186-228">Indicators are small simple gauges that communicate data values at a glance.</span></span> <span data-ttu-id="98186-229">크기와 단순함으로 인해 표시기는 흔히 테이블과 행렬에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="98186-229">Because of their size and simplicity, indicators are often used in tables and matrices.</span></span> <span data-ttu-id="98186-230">자세한 내용은 [표시기&#40;보고서 작성기 및 SSRS&#41;](report-design/indicators-report-builder-and-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="98186-230">For more information, see [Indicators &#40;Report Builder and SSRS&#41;](report-design/indicators-report-builder-and-ssrs.md).</span></span>  
  
#### <a name="to-display-the-present-state-of-a-kpi-using-an-indicator"></a><span data-ttu-id="98186-231">표시기를 사용하여 KPI의 현재 상태를 표시하려면</span><span class="sxs-lookup"><span data-stu-id="98186-231">To display the present state of a KPI using an indicator</span></span>  
  
1.  <span data-ttu-id="98186-232">디자인 뷰로 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="98186-232">Switch to Design view.</span></span>  
  
2.  <span data-ttu-id="98186-233">테이블에서 이전 절차에서 변경한 셀의 열 처리기를 마우스 오른쪽 단추로 클릭 하 고 **열 삽입**을 가리킨 다음 **오른쪽**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="98186-233">In the table, right-click the column handler for the cell that you changed in the previous procedure, point to **Insert Column**, and then click **Right**.</span></span> <span data-ttu-id="98186-234">테이블에 새 열이 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="98186-234">A new column is added to the table.</span></span>  
  
3.  <span data-ttu-id="98186-235">열 머리글에 **KPI** 를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="98186-235">Type **KPI** in the column heading.</span></span>  
  
4.  <span data-ttu-id="98186-236">하위 범주 부분합의 셀을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="98186-236">Click the cell for the subcategory subtotal.</span></span>  
  
5.  <span data-ttu-id="98186-237">**삽입** 탭의 **데이터 영역** 그룹에서 표시기를 두 번 클릭 합니다 **.**</span><span class="sxs-lookup"><span data-stu-id="98186-237">On the **Insert** tab, in the **Data Regions** group, double-click **Indicator.**</span></span>  
  
     <span data-ttu-id="98186-238">**표시기 유형 선택** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="98186-238">The **Select Indicator Type** dialog box opens.</span></span>  
  
6.  <span data-ttu-id="98186-239">**셰이프**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="98186-239">Click **Shapes**.</span></span> <span data-ttu-id="98186-240">첫 번째 모양 유형인 **3 개 신호등 (테두리 없음)** 이 선택 됩니다.</span><span class="sxs-lookup"><span data-stu-id="98186-240">The first shape type, **3 Traffic Lights (Unrimmed),** is selected.</span></span>  
  
     <span data-ttu-id="98186-241">자습서에서는 이 표시기를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="98186-241">You will use this indicator in the tutorial.</span></span>  
  
7.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
     <span data-ttu-id="98186-242">디자인 화면에 표시기가 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="98186-242">The indicator is added to the design surface.</span></span>  
  
8.  <span data-ttu-id="98186-243">표시기를 마우스 오른쪽 단추로 클릭하고 **표시기 속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="98186-243">Right-click the indicator and click **Indicator Properties**.</span></span>  
  
9. <span data-ttu-id="98186-244">**값 및 상태를**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="98186-244">Click **Values and States**.</span></span>  
  
10. <span data-ttu-id="98186-245">값 드롭다운 목록에서 **[Sum (Sales)]** 를 선택 하 고 다른 옵션은 변경 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="98186-245">In the Value drop-down list, select **[Sum(Sales)]**, but do not change any other options.</span></span>  
  
     <span data-ttu-id="98186-246">기본적으로 데이터 영역에서 데이터 동기화가 발생하며 보고서에 있는 테이블 데이터 영역의 이름인 **Tablix1**값이 **동기화 범위** 상자에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="98186-246">By default, data synchronization occurs across the data region and you see the value **Tablix1**, the name of the table data region in the report, in the **Synchronization scope** box.</span></span>  
  
     <span data-ttu-id="98186-247">이 보고서에서는 하위 범주 부분합의 셀에 놓인 표시기의 범위를 변경하여 SalesDate 필드에서 동기화할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98186-247">In this report, you can also change the scope of an indicator placed in the cell of the subcategory subtotal to synchronize across the SalesDate field.</span></span>  
  
11. <span data-ttu-id="98186-248">**실행** 을 클릭하여 보고서를 미리 봅니다.</span><span class="sxs-lookup"><span data-stu-id="98186-248">Click **Run** to preview the report.</span></span>  
  
##  <a name="6-add-a-report-title"></a><a name="Title"></a><span data-ttu-id="98186-249">6. 보고서 제목 추가</span><span class="sxs-lookup"><span data-stu-id="98186-249">6. Add a Report Title</span></span>  
 <span data-ttu-id="98186-250">보고서 제목은 보고서 맨 위에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="98186-250">A report title appears at the top of the report.</span></span> <span data-ttu-id="98186-251">보고서 제목을 보고서 머리글에 배치하거나, 보고서 머리글이 사용되지 않을 경우 보고서 본문의 맨 위에 있는 입력란에 배치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98186-251">You can place the report title in a report header or if the report does not use one, in a text box at the top of the report body.</span></span> <span data-ttu-id="98186-252">보고서 본문의 맨 위에 자동으로 배치되는 입력란을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="98186-252">You will use the text box that is automatically placed at the top of the report body.</span></span>  
  
 <span data-ttu-id="98186-253">글꼴 스타일, 크기 및 색을 텍스트의 각 문자나 구 단위로 다르게 적용하여 더 보기 좋게 꾸밀 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98186-253">The text can be further enhanced by applying different font styles, sizes, and colors to phrases and individual characters of the text.</span></span> <span data-ttu-id="98186-254">자세한 내용은 [입력란의 텍스트 서식 지정&#40;보고서 작성기 및 SSRS&#41;](report-design/format-text-in-a-text-box-report-builder-and-ssrs.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="98186-254">For more information, see [Format Text in a Text Box &#40;Report Builder and SSRS&#41;](report-design/format-text-in-a-text-box-report-builder-and-ssrs.md).</span></span>  
  
#### <a name="to-add-a-report-title"></a><span data-ttu-id="98186-255">보고서 제목을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="98186-255">To add a report title</span></span>  
  
1.  <span data-ttu-id="98186-256">디자인 화면에서 **제목을 추가하려면 클릭하십시오.** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="98186-256">On the design surface, click **Click to add title**.</span></span>  
  
2.  <span data-ttu-id="98186-257">**Product SALES KPI**를 입력 한 다음 입력란 바깥쪽을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="98186-257">Type **Product Sales KPI**, and then click outside the text box.</span></span>  
  
3.  <span data-ttu-id="98186-258">필요에 따라 **Product SALES KPI**가 들어 있는 입력란을 마우스 오른쪽 단추로 클릭 하 고 **입력란 속성**을 클릭 한 다음 글꼴 탭에서 다른 글꼴 스타일, 크기 및 색을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="98186-258">Optionally, right-click the text box that contains **Product Sales KPI**, click **Text Box Properties**, and then on the Font tab select the different font styles, sizes and colors.</span></span>  
  
4.  <span data-ttu-id="98186-259">**실행** 을 클릭하여 보고서를 미리 봅니다.</span><span class="sxs-lookup"><span data-stu-id="98186-259">Click **Run** to preview the report.</span></span>  
  
##  <a name="7-save-the-report"></a><a name="Save"></a><span data-ttu-id="98186-260">7. 보고서 저장</span><span class="sxs-lookup"><span data-stu-id="98186-260">7. Save the Report</span></span>  
 <span data-ttu-id="98186-261">보고서 서버 또는 컴퓨터에 보고서를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="98186-261">Save the report to a report server or your computer.</span></span> <span data-ttu-id="98186-262">보고서를 보고서 서버에 저장하지 않을 경우 보고서 파트 및 하위 보고서와 같은 여러 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 기능을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="98186-262">If you do not save the report to the report server, a number of [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] features such as report parts and subreports are not available.</span></span>  
  
#### <a name="to-save-the-report-on-a-report-server"></a><span data-ttu-id="98186-263">보고서를 보고서 서버에 저장하려면</span><span class="sxs-lookup"><span data-stu-id="98186-263">To save the report on a report server</span></span>  
  
1.  <span data-ttu-id="98186-264">**보고서 작성기** 단추에서 다른 **이름으로 저장**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="98186-264">From the **Report Builder** button, click **Save As**.</span></span>  
  
2.  <span data-ttu-id="98186-265">**최근에 사용한 사이트 및 서버**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="98186-265">Click **Recent Sites and Servers**.</span></span>  
  
3.  <span data-ttu-id="98186-266">보고서를 저장할 수 있는 권한을 가진 보고서 서버의 이름을 선택하거나 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="98186-266">Select or type the name of the report server where you have permission to save reports.</span></span>  
  
     <span data-ttu-id="98186-267">"보고서 서버에 연결하는 중"이라는 메시지가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="98186-267">The message "Connecting to report server" appears.</span></span> <span data-ttu-id="98186-268">연결되면 보고서 서버 관리자가 보고서의 기본 위치로 지정한 보고서 폴더의 내용이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="98186-268">When the connection is complete, you see the contents of the report folder that the report server administrator specified as the default location for reports.</span></span>  
  
4.  <span data-ttu-id="98186-269">**이름**에서 기본 이름을 **Product Sales KPI**로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="98186-269">In **Name**, replace the default name with **Product Sales KPI**.</span></span>  
  
5.  <span data-ttu-id="98186-270">**저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="98186-270">Click **Save**.</span></span>  
  
 <span data-ttu-id="98186-271">보고서가 보고서 서버에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="98186-271">The report is saved to the report server.</span></span> <span data-ttu-id="98186-272">연결된 보고서 서버의 이름이 창 아래쪽에 있는 상태 표시줄에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="98186-272">The name of report server that you are connected to appears in the status bar at the bottom of the window.</span></span>  
  
#### <a name="to-save-the-report-on-your-computer"></a><span data-ttu-id="98186-273">컴퓨터에 보고서를 저장하려면</span><span class="sxs-lookup"><span data-stu-id="98186-273">To save the report on your computer</span></span>  
  
1.  <span data-ttu-id="98186-274">**보고서 작성기** 단추에서 다른 **이름으로 저장**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="98186-274">From the **Report Builder** button, click **Save As**.</span></span>  
  
2.  <span data-ttu-id="98186-275">**바탕 화면**, **내 문서**또는 **내 컴퓨터**를 클릭하여 보고서를 저장할 폴더를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="98186-275">Click **Desktop**, **My Documents**, or **My computer**, and browse to the folder where you want to save the report.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="98186-276">보고서 서버에 액세스할 수 없는 경우 **바탕 화면**, **내 문서**또는 **내 컴퓨터** 를 클릭하고 보고서를 컴퓨터에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="98186-276">If you do not have access to a report server, click **Desktop**, **My Documents**, or **My computer** and save the report to your computer.</span></span>  
  
1.  <span data-ttu-id="98186-277">**이름**에서 기본 이름을 **Product Sales KPI**로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="98186-277">In **Name**, replace the default name with **Product Sales KPI**.</span></span>  
  
2.  <span data-ttu-id="98186-278">**저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="98186-278">Click **Save**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="98186-279">다음 단계</span><span class="sxs-lookup"><span data-stu-id="98186-279">Next Steps</span></span>  
 <span data-ttu-id="98186-280">보고서에 KPI 추가 자습서를 성공적으로 완료했습니다.</span><span class="sxs-lookup"><span data-stu-id="98186-280">You have successfully completed the Adding a KPI to Your Report tutorial.</span></span> <span data-ttu-id="98186-281">자세한 내용은 계기 (보고서 작성기) [표시기 &#40;보고서 작성기 및 SSRS&#41;](report-design/indicators-report-builder-and-ssrs.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="98186-281">For more information, see Gauges (Report Builder) [Indicators &#40;Report Builder and SSRS&#41;](report-design/indicators-report-builder-and-ssrs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98186-282">참고 항목</span><span class="sxs-lookup"><span data-stu-id="98186-282">See Also</span></span>  
 <span data-ttu-id="98186-283">[자습서 &#40;보고서 작성기&#41;](report-builder-tutorials.md) </span><span class="sxs-lookup"><span data-stu-id="98186-283">[Tutorials &#40;Report Builder&#41;](report-builder-tutorials.md) </span></span>  
 [<span data-ttu-id="98186-284">SQL Server 2014의 보고서 작성기</span><span class="sxs-lookup"><span data-stu-id="98186-284">Report Builder in SQL Server 2014</span></span>](report-builder/report-builder-in-sql-server-2016.md)  
  
  
