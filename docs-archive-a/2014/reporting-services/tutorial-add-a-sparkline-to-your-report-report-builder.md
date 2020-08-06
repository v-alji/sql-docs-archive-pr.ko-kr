---
title: '자습서: 보고서에 스파크라인 추가(보고서 작성기) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 18c90a36-48bf-4805-a960-2d1e8f00c2dc
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: fb1bf83810b6c743b977e399864ce2edd514f572
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735947"
---
# <a name="tutorial-add-a-sparkline-to-your-report-report-builder"></a><span data-ttu-id="50710-102">자습서: 보고서에 스파크라인 추가(보고서 작성기)</span><span class="sxs-lookup"><span data-stu-id="50710-102">Tutorial: Add a Sparkline to Your Report (Report Builder)</span></span>
  <span data-ttu-id="50710-103">이 자습서에서는 예제 판매 데이터를 기반으로 하는 기본 테이블 보고서를 만든 다음 테이블의 셀에 스파크라인 차트를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="50710-103">In this tutorial, you create a basic table report based on sample sales data, and then add a sparkline chart to a cell in the table.</span></span>  
  
 <span data-ttu-id="50710-104">이 자습서에서 만드는 향상된 버전의 보고서는 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] 보고서 작성기의 예제 보고서로 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="50710-104">An enhanced version of the report you create in this tutorial is available as a sample [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] Report Builder report.</span></span> <span data-ttu-id="50710-105">이 예제 보고서 및 기타 보고서를 다운로드하는 방법은 [보고서 작성기 예제 보고서(Report Builder sample reports)](https://go.microsoft.com/fwlink/?LinkId=184851)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="50710-105">For more information about downloading this sample report and others, see [Report Builder sample reports](https://go.microsoft.com/fwlink/?LinkId=184851).</span></span> <span data-ttu-id="50710-106">다음 그림에서는 만들려는 보고서와 비슷한 예제 보고서를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="50710-106">The following illustration shows the sample report similar to the one that you will create.</span></span>  
  
 <span data-ttu-id="50710-107">![rs_SparklineMatrixTutorial](../../2014/tutorials/media/rs-sparklinematrixtutorial.gif "rs_SparklineMatrixTutorial")</span><span class="sxs-lookup"><span data-stu-id="50710-107">![rs_SparklineMatrixTutorial](../../2014/tutorials/media/rs-sparklinematrixtutorial.gif "rs_SparklineMatrixTutorial")</span></span>  
  
 <span data-ttu-id="50710-108">비디오 [방법: 테이블에 스파크라인 만들기(보고서 작성기 비디오)](https://technet.microsoft.com/bi/ff871942.aspx) 는 스파크라인이 있는 비슷한 보고서를 만드는 방법을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="50710-108">The video [How to: Create a Sparkline in a Table (Report Builder Video)](https://technet.microsoft.com/bi/ff871942.aspx) illustrates how to create a similar report with sparklines.</span></span>  
  
##  <a name="what-you-will-learn"></a><a name="BackToTop"></a><span data-ttu-id="50710-109">학습 내용</span><span class="sxs-lookup"><span data-stu-id="50710-109">What You Will Learn</span></span>  
 <span data-ttu-id="50710-110">이 자습서에서는 다음 작업 방법을 배웁니다.</span><span class="sxs-lookup"><span data-stu-id="50710-110">In this tutorial, you will learn how to do the following:</span></span>  
  
 1. [<span data-ttu-id="50710-111">테이블이 있는 보고서 만들기</span><span class="sxs-lookup"><span data-stu-id="50710-111">Create a Report with a Table</span></span>](#CreateTable)  
  
 2. [<span data-ttu-id="50710-112">테이블 또는 행렬 마법사에서 쿼리 만들기</span><span class="sxs-lookup"><span data-stu-id="50710-112">Create a Query in the Table or Matrix Wizard</span></span>](#Query)  
  
 3. [<span data-ttu-id="50710-113">테이블에 스파크라인 추가</span><span class="sxs-lookup"><span data-stu-id="50710-113">Add a Sparkline to the Table</span></span>](#Sparkline)  
  
 4. [<span data-ttu-id="50710-114">세로 및 가로로 스파크라인 맞추기</span><span class="sxs-lookup"><span data-stu-id="50710-114">Align the Sparklines Vertically and Horizontally</span></span>](#AlignSparklines)  
  
### <a name="other-optional-steps"></a><span data-ttu-id="50710-115">기타 선택적 단계</span><span class="sxs-lookup"><span data-stu-id="50710-115">Other Optional Steps</span></span>  
 5. [<span data-ttu-id="50710-116">데이터 형식을 통화로 지정</span><span class="sxs-lookup"><span data-stu-id="50710-116">Format Data as Currency</span></span>](#FormatCurrency)  
  
 6. [<span data-ttu-id="50710-117">데이터 서식을 날짜로 지정</span><span class="sxs-lookup"><span data-stu-id="50710-117">Format Data as Dates</span></span>](#FormatDates)  
  
 7. [<span data-ttu-id="50710-118">열 너비 변경</span><span class="sxs-lookup"><span data-stu-id="50710-118">Change Column Widths</span></span>](#Width)  
  
 8. [<span data-ttu-id="50710-119">보고서 제목 추가</span><span class="sxs-lookup"><span data-stu-id="50710-119">Add a Report Title</span></span>](#Title)  
  
 9. [<span data-ttu-id="50710-120">보고서 저장</span><span class="sxs-lookup"><span data-stu-id="50710-120">Save the Report</span></span>](#Save)  
  
 <span data-ttu-id="50710-121">이 자습서에 소요되는 예상 시간: 30분</span><span class="sxs-lookup"><span data-stu-id="50710-121">Estimated time to complete this tutorial: 30 minutes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="50710-122">요구 사항</span><span class="sxs-lookup"><span data-stu-id="50710-122">Requirements</span></span>  
 <span data-ttu-id="50710-123">요구 사항에 대한 자세한 내용은 [자습서의 필수 조건&#40;보고서 작성기&#41;](../reporting-services/report-builder-tutorials.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="50710-123">For more information about requirements, see [Prerequisites for Tutorials &#40;Report Builder&#41;](../reporting-services/report-builder-tutorials.md).</span></span>  
  
##  <a name="1-create-a-report-with-a-table"></a><a name="CreateTable"></a><span data-ttu-id="50710-124">1. 테이블이 있는 보고서 만들기</span><span class="sxs-lookup"><span data-stu-id="50710-124">1. Create a Report with a Table</span></span>  
  
#### <a name="to-create-a-report"></a><span data-ttu-id="50710-125">보고서를 만들려면</span><span class="sxs-lookup"><span data-stu-id="50710-125">To create a report</span></span>  
  
1.  <span data-ttu-id="50710-126">**시작**을 클릭하고 **프로그램**, **Microsoft SQL Server 2012 보고서 작성기**를 차례로 가리킨 다음 **보고서 작성기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="50710-126">Click **Start**, point to **Programs**, point to **Microsoft SQL Server 2012 Report Builder**, and then click **Report Builder**.</span></span>  
  
     <span data-ttu-id="50710-127">**시작** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="50710-127">The **Getting Started** dialog box opens.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="50710-128">**시작** 대화 상자가 나타나지 않으면 **보고서 작성기** 단추에서 **새로 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="50710-128">If the **Getting Started** dialog box does not appear, from the **Report Builder** button, click **New**.</span></span>  
  
2.  <span data-ttu-id="50710-129">왼쪽 창에 **새 보고서** 가 선택되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="50710-129">In the left pane, verify that **New Report** is selected.</span></span>  
  
3.  <span data-ttu-id="50710-130">오른쪽 창에서 **테이블 또는 행렬 마법사**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="50710-130">In the right pane, click **Table or Matrix Wizard**.</span></span>  
  
4.  <span data-ttu-id="50710-131">**데이터 세트 선택** 페이지에서 **데이터 세트 만들기**를 선택한 후, **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="50710-131">On the **Choose a dataset** page, select **Create a dataset**, and then click **Next**.</span></span> <span data-ttu-id="50710-132">**데이터 원본에 대한 연결 선택** 페이지가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="50710-132">The **Choose a connection to a data source** page opens.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="50710-133">이 자습서를 사용하기 위해 특정 데이터가 필요하지는 않습니다. [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] 데이터베이스에 연결하기만 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="50710-133">This tutorial does not need specific data; it just needs a connection to a [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] database.</span></span> <span data-ttu-id="50710-134">**데이터 원본 연결**에 나열된 데이터 원본 연결이 이미 있는 경우 해당 데이터 원본 연결을 선택하고 10단계로 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50710-134">If you already have a data source connection listed under **Data Source Connections**, you can select it and go to step 10.</span></span> <span data-ttu-id="50710-135">자세한 내용은 [데이터에 연결하는 다른 방법&#40;보고서 작성기&#41;](../reporting-services/alternative-ways-to-get-a-data-connection-report-builder.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="50710-135">For more information, see [Alternative Ways to Get a Data Connection &#40;Report Builder&#41;](../reporting-services/alternative-ways-to-get-a-data-connection-report-builder.md).</span></span>  
  
5.  <span data-ttu-id="50710-136">**새로 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="50710-136">Click **New**.</span></span> <span data-ttu-id="50710-137">**데이터 원본 속성** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="50710-137">The **Data Source Properties** dialog box opens.</span></span>  
  
6.  <span data-ttu-id="50710-138">**이름**에 데이터 원본 이름으로 **Product Sales**를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="50710-138">In **Name**, type **Product Sales**, a name for the data source.</span></span>  
  
7.  <span data-ttu-id="50710-139">**연결 유형 선택**에서 **Microsoft SQL Server** 가 선택되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="50710-139">In **Select a connection type**, verify that **Microsoft SQL Server** is selected.</span></span>  
  
8.  <span data-ttu-id="50710-140">**연결 문자열**에 다음 텍스트를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="50710-140">In **Connection string**, type the following text:</span></span>  
  
     <span data-ttu-id="50710-141">**데이터 원본 =\<servername>**</span><span class="sxs-lookup"><span data-stu-id="50710-141">**Data Source=\<servername>**</span></span>  
  
     <span data-ttu-id="50710-142">\<servername>식(예: Report001)은 SQL Server 데이터베이스 엔진의 인스턴스가 설치된 컴퓨터를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="50710-142">The expression \<servername>, for example Report001, specifies a computer on which an instance of the SQL Server Database Engine is installed.</span></span> <span data-ttu-id="50710-143">보고서 데이터는 SQL Server 데이터베이스에서 추출되지 않았으므로 데이터베이스 이름을 포함하지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="50710-143">Because the report data is not extracted from a SQL Server database, you need not include the name of a database.</span></span> <span data-ttu-id="50710-144">지정된 서버의 기본 데이터베이스는 쿼리를 구문 분석하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="50710-144">The default database on the specified server is used to parse the query.</span></span>  
  
9. <span data-ttu-id="50710-145">**자격 증명**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="50710-145">Click **Credentials**.</span></span> <span data-ttu-id="50710-146">외부 데이터 원본에 액세스하는 데 필요한 자격 증명을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="50710-146">Enter the credentials that you need to access the external data source.</span></span>  
  
10. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
     <span data-ttu-id="50710-147">**데이터 원본에 대한 연결 선택** 페이지로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="50710-147">You are back on the **Choose a connection to a data source** page.</span></span>  
  
11. <span data-ttu-id="50710-148">데이터 원본에 연결할 수 있는지 확인하려면 **연결 테스트**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="50710-148">To verify that you can connect to the data source, click **Test Connection**.</span></span>  
  
     <span data-ttu-id="50710-149">"연결되었습니다."라는 메시지가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="50710-149">The message "Connection created successfully" appears.</span></span>  
  
12. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
13. <span data-ttu-id="50710-150">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="50710-150">Click **Next**.</span></span>  
  
##  <a name="2-create-a-query-in-the-table-wizard"></a><a name="Query"></a><span data-ttu-id="50710-151">2. 테이블 마법사에서 쿼리 만들기</span><span class="sxs-lookup"><span data-stu-id="50710-151">2. Create a Query in the Table Wizard</span></span>  
 <span data-ttu-id="50710-152">보고서에서는 미리 정의된 쿼리가 포함된 공유 데이터 세트를 사용하거나 해당 보고서에만 사용할 포함된 데이터 세트를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50710-152">In a report, you can use a shared dataset that has a predefined query, or you can create an embedded dataset for use only in your report.</span></span> <span data-ttu-id="50710-153">이 자습서에서는 포함된 데이터 세트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="50710-153">In this tutorial, you will create an embedded dataset.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="50710-154">이 자습서의 쿼리에는 데이터 값이 포함되어 있으므로 외부 데이터 원본이 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="50710-154">In this tutorial, the query contains the data values, so that it does not need an external data source.</span></span> <span data-ttu-id="50710-155">따라서 쿼리가 상당히 길어집니다.</span><span class="sxs-lookup"><span data-stu-id="50710-155">This makes the query quite long.</span></span> <span data-ttu-id="50710-156">비즈니스 환경에서는 쿼리에 데이터가 포함되지 않을 것입니다.</span><span class="sxs-lookup"><span data-stu-id="50710-156">In a business environment, a query would not contain the data.</span></span> <span data-ttu-id="50710-157">이 자습서의 쿼리는 학습용으로만 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="50710-157">This is for learning purposes only.</span></span>  
  
#### <a name="to-create-a-query"></a><span data-ttu-id="50710-158">쿼리를 만들려면</span><span class="sxs-lookup"><span data-stu-id="50710-158">To create a query</span></span>  
  
1.  <span data-ttu-id="50710-159">**쿼리 디자인** 페이지에 관계형 쿼리 디자이너가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="50710-159">On the **Design a query** page, the relational query designer is open.</span></span> <span data-ttu-id="50710-160">이 자습서에서는 텍스트 기반 쿼리 디자이너를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="50710-160">For this tutorial, you will use the text-based query designer.</span></span>  
  
2.  <span data-ttu-id="50710-161">**텍스트로 편집을**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="50710-161">Click **Edit As Text**.</span></span> <span data-ttu-id="50710-162">텍스트 기반 쿼리 디자이너에 쿼리 창과 결과 창이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="50710-162">The text-based query designer displays a query pane and a results pane.</span></span>  
  
3.  <span data-ttu-id="50710-163">[!INCLUDE[tsql](../includes/tsql-md.md)] 쿼리 **상자에 다음** 쿼리를 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="50710-163">Paste the following [!INCLUDE[tsql](../includes/tsql-md.md)] query into the **Query** box.</span></span>  
  
    ```  
    SELECT CAST('2010-01-04' AS date) as SalesDate, 'Accessories' as Subcategory,   
       'Carrying Case' as Product, CAST(16996.60 AS money) AS Sales, 68 as Quantity  
    UNION SELECT CAST('2010-01-05' AS date) as SalesDate, 'Accessories' as Subcategory,  
       'Carrying Case' as Product, CAST(1350.00 AS money) AS Sales, 18 as Quantity  
    UNION SELECT CAST('2010-01-10' AS date) as SalesDate, 'Accessories' as Subcategory,  
       'Carrying Case' as Product, CAST(1147.50 AS money) AS Sales, 17 as Quantity  
    UNION SELECT CAST('2010-01-04' AS date) as SalesDate, 'Accessories' as Subcategory,  
       'Budget Movie-Maker' as Product, CAST(1056.00 AS money) AS Sales, 44 as Quantity  
    UNION SELECT CAST('2010-01-05' AS date) as SalesDate,  'Accessories' as Subcategory,  
       'Slim Digital' as Product, CAST(1380.00 AS money) AS Sales, 18 as Quantity  
    UNION SELECT CAST('2010-01-05' AS date) as SalesDate,'Accessories' as Subcategory,    
       'Budget Movie-Maker' as Product, CAST(780.00 AS money) AS Sales, 26 as Quantity  
    UNION SELECT CAST('2010-01-07' AS date) as SalesDate, 'Accessories' as Subcategory,   
       'Budget Movie-Maker' as Product, CAST(3798.00 AS money) AS Sales, 9 as Quantity  
    UNION SELECT CAST('2010-01-08' AS date) as SalesDate, 'Camcorders' as Subcategory,   
       'Budget Movie-Maker' as Product, CAST(10400.00 AS money) AS Sales, 13 as Quantity  
    UNION SELECT CAST('2010-01-09' AS date) as SalesDate, 'Camcorders' as Subcategory,   
       'Budget Movie-Maker' as Product, CAST(3000.00 AS money) AS Sales, 60 as Quantity  
    UNION SELECT CAST('2010-01-10' AS date) as SalesDate,  'Digital' as Subcategory,   
       'Budget Movie-Maker' as Product, CAST(7234.50 AS money) AS Sales, 39 as Quantity  
    UNION SELECT CAST('2010-01-06' AS date) as SalesDate,  'Digital' as Subcategory,   
       'Carrying Case' as Product, CAST(10836.00 AS money) AS Sales, 84 as Quantity  
    UNION SELECT CAST('2010-01-07' AS date) as SalesDate,  'Digital' as Subcategory,   
       'Slim Digital' as Product, CAST(2550.00 AS money) AS Sales, 17 as Quantity  
    UNION SELECT CAST('2010-01-04' AS date) as SalesDate, 'Digital' as Subcategory,   
       'Slim Digital' as Product, CAST(8357.80 AS money) AS Sales, 44 as Quantity  
    UNION SELECT CAST('2010-01-08' AS date) as SalesDate, 'Digital SLR' as Subcategory,   
       'Slim Digital' as Product, CAST(18530.00 AS money) AS Sales, 34 as Quantity  
    UNION SELECT CAST('2010-01-06' AS date) as SalesDate, 'Digital SLR' as Subcategory,   
       'Slim Digital' as Product, CAST(26576.00 AS money) AS Sales, 88 as Quantity  
    ```  
  
4.  <span data-ttu-id="50710-164">쿼리 디자이너 도구 모음에서 실행 (**!**)을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="50710-164">On the query designer toolbar, click Run  (**!**).</span></span>  
  
     <span data-ttu-id="50710-165">쿼리가 실행되고 **SalesDate**, **Subcategory**, **Product**, **Sales**및 **Quantity**필드에 대한 결과 집합이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="50710-165">The query runs and displays the result set for the fields **SalesDate**, **Subcategory**, **Product**, **Sales**, and **Quantity**.</span></span>  
  
5.  <span data-ttu-id="50710-166">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="50710-166">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="50710-167">**필드 정렬** 페이지에서 **값** 에 **Sales**를 끌어옵니다.</span><span class="sxs-lookup"><span data-stu-id="50710-167">On the **Arrange fields** page, drag **Sales** to **Values**.</span></span>  
  
     <span data-ttu-id="50710-168">**Sales** 는 Sum 함수로 집계됩니다.</span><span class="sxs-lookup"><span data-stu-id="50710-168">**Sales** is aggregated by the Sum function.</span></span> <span data-ttu-id="50710-169">값은 [Sum(Sales)]입니다.</span><span class="sxs-lookup"><span data-stu-id="50710-169">The value is [Sum(Sales)].</span></span>  
  
7.  <span data-ttu-id="50710-170">**행 그룹** 에 **Product**를 끌어옵니다.</span><span class="sxs-lookup"><span data-stu-id="50710-170">Drag **Product** to **Row groups**.</span></span>  
  
8.  <span data-ttu-id="50710-171">**열 그룹** 에 **SalesDate**를 끌어옵니다.</span><span class="sxs-lookup"><span data-stu-id="50710-171">Drag **SalesDate** to **Column groups**.</span></span>  
  
9. <span data-ttu-id="50710-172">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="50710-172">Click **Next**.</span></span>  
  
10. <span data-ttu-id="50710-173">**레이아웃 선택** 페이지의 **옵션**에서 **부분합 및 총합계 표시** 가 선택 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="50710-173">On the **Choose the layout** page, under **Options**, verify that **Show subtotals and grand totals** is selected.</span></span>  
  
     <span data-ttu-id="50710-174">마법사 미리 보기 창에 3개의 행이 있는 테이블이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="50710-174">The wizard Preview pane displays a table with three rows.</span></span> <span data-ttu-id="50710-175">보고서를 실행하면 각 행이 다음과 같은 방식으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="50710-175">When you run the report, each row will display in the following way:</span></span>  
  
    1.  <span data-ttu-id="50710-176">첫 번째 행은 열 제목을 보여 주기 위해 테이블에 대해 한 번씩 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="50710-176">The first row will appear once for the table to show column headings.</span></span>  
  
    2.  <span data-ttu-id="50710-177">두 번째 행은 각 제품에 대해 한 번씩 반복되고 제품 이름, 일일 합계 및 라인 합계를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="50710-177">The second row will repeat once for each product and display the product name, total per day, and line total.</span></span>  
  
    3.  <span data-ttu-id="50710-178">세 번째 행은 테이블에 대해 한 번씩 나타나 총합계를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="50710-178">The third row will appear once for the table to display the grand totals.</span></span>  
  
11. <span data-ttu-id="50710-179">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="50710-179">Click **Next**.</span></span>  
  
12. <span data-ttu-id="50710-180">**스타일 선택** 페이지의 **스타일** 창에서 **Slate**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="50710-180">On the **Choose a Style** page, in the **Styles** pane, select **Slate**.</span></span>  
  
     <span data-ttu-id="50710-181">미리 보기 창에 해당 스타일이 적용된 예제 테이블이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="50710-181">The Preview pane displays a sample of the table with that style.</span></span>  
  
13. <span data-ttu-id="50710-182">**Finish**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="50710-182">Click **Finish**.</span></span>  
  
14. <span data-ttu-id="50710-183">디자인 화면에 테이블이 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="50710-183">The table is added to the design surface.</span></span> <span data-ttu-id="50710-184">이 테이블에는 열 3개와 행 3개가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50710-184">The table has three columns and three rows.</span></span>  
  
     <span data-ttu-id="50710-185">그룹화 창을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="50710-185">Look in the Grouping pane.</span></span> <span data-ttu-id="50710-186">그룹화 창이 표시되지 않는 경우 **보기** 메뉴에서 **그룹화**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="50710-186">If you can't see the Grouping pane, on the **View** menu, click **Grouping**.</span></span> <span data-ttu-id="50710-187">행 그룹 창에는 **Product**라는 한 개의 행 그룹이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="50710-187">The Row Groups pane shows one row group: **Product**.</span></span> <span data-ttu-id="50710-188">열 그룹 창에는 **SalesDate**라는 한 개의 열 그룹이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="50710-188">The Column Groups pane shows one column group: **SalesDate**.</span></span> <span data-ttu-id="50710-189">세부 데이터는 모두 데이터 세트 쿼리로 검색된 데이터입니다.</span><span class="sxs-lookup"><span data-stu-id="50710-189">Detail data is all the data that is retrieved by the dataset query.</span></span>  
  
15. <span data-ttu-id="50710-190">**실행** 을 클릭하여 보고서를 미리 봅니다.</span><span class="sxs-lookup"><span data-stu-id="50710-190">Click **Run** to preview the report.</span></span>  
  
##  <a name="3-add-a-sparkline"></a><a name="Sparkline"></a><span data-ttu-id="50710-191">3. 스파크 라인 추가</span><span class="sxs-lookup"><span data-stu-id="50710-191">3. Add a Sparkline</span></span>  
  
#### <a name="to-add-a-sparkline-chart-to-a-table"></a><span data-ttu-id="50710-192">테이블에 스파크라인 차트를 추가하려면</span><span class="sxs-lookup"><span data-stu-id="50710-192">To add a sparkline chart to a table</span></span>  
  
1.  <span data-ttu-id="50710-193">**디자인** 을 클릭하여 디자인 뷰로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="50710-193">Click **Design** to return to design view.</span></span>  
  
2.  <span data-ttu-id="50710-194">테이블의 Total 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="50710-194">Select the Total column in your table.</span></span>  
  
3.  <span data-ttu-id="50710-195">마우스 오른쪽 단추를 클릭하고 **열 삽입**을 가리킨 다음 **왼쪽**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="50710-195">Right-click, point to **Insert Column**, and then click **Left**.</span></span>  
  
4.  <span data-ttu-id="50710-196">새 열에서 [Product] 행을 마우스 오른쪽 단추로 클릭하고 **삽입** 리본 탭을 가리킨 다음 **스파크라인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="50710-196">In the new column, right-click in the [Product] row, point to the **Insert** ribbon tab, and then click **Sparkline**.</span></span>  
  
5.  <span data-ttu-id="50710-197">**열** 행의 첫 번째 스파크라인이 선택되어 있는지 확인한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="50710-197">Make sure the first sparkline in the **Column** row is selected and then click **OK**.</span></span>  
  
6.  <span data-ttu-id="50710-198">스파크라인을 클릭하여 차트 데이터 창을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="50710-198">Click the sparkline to show the Chart Data pane.</span></span>  
  
7.  <span data-ttu-id="50710-199">값 상자의 더하기 기호(+)를 클릭한 다음 **Sales**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="50710-199">Click the plus (+) sign in the Values box, and then click **Sales**.</span></span>  
  
     <span data-ttu-id="50710-200">그러면 **Sales** 필드의 값이 스파크라인의 값이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="50710-200">The values in the **Sales** field are now the values for the sparkline.</span></span>  
  
8.  <span data-ttu-id="50710-201">범주 그룹 상자의 더하기 기호(+)를 클릭한 다음 **SalesDate**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="50710-201">Click the plus (+) sign in the Category Groups box, and then click **SalesDate**.</span></span>  
  
9. <span data-ttu-id="50710-202">**실행** 을 클릭하여 보고서를 미리 봅니다.</span><span class="sxs-lookup"><span data-stu-id="50710-202">Click **Run** to preview your report.</span></span>  
  
     <span data-ttu-id="50710-203">테이블의 각 행에 스파크라인 차트가 있지만 올바르지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="50710-203">Note that there are sparkline charts in each row of the table, but they're not correct.</span></span> <span data-ttu-id="50710-204">차트의 각 막대가 서로 정렬되어 있지 않고,</span><span class="sxs-lookup"><span data-stu-id="50710-204">The bars in the charts don't line up with each other.</span></span> <span data-ttu-id="50710-205">데이터의 두 번째 행에는 네 개의 막대만 있으므로 여섯 개의 막대가 있는 첫 번째 행보다 막대의 너비가 넓습니다.</span><span class="sxs-lookup"><span data-stu-id="50710-205">There are only four bars in the second row of data, so the bars are wider than the bars in the first row, which has six.</span></span> <span data-ttu-id="50710-206">이로 인해 각 제품의 값을 일별로 비교할 수 없으므로</span><span class="sxs-lookup"><span data-stu-id="50710-206">You can't compare values for each product per day.</span></span> <span data-ttu-id="50710-207">막대가 서로 정렬되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="50710-207">They need to line up with each other.</span></span>  
  
     <span data-ttu-id="50710-208">또한 각 행마다 해당 행의 가장 높은 막대는 행 높이와 같습니다.</span><span class="sxs-lookup"><span data-stu-id="50710-208">Also note that for each row, the tallest bar for that row is the height of the row.</span></span> <span data-ttu-id="50710-209">이는 각 행에 대 한 가장 큰 값이 동일 하지 않기 때문에 잘못 된 것입니다. 예산 영화 제조업체의 가장 큰 값은 $10400 이지만, 슬림형 Digital의 가장 큰 값은 $26576-크게 두 배 이상입니다.</span><span class="sxs-lookup"><span data-stu-id="50710-209">This is misleading, too, because the largest values for each row are not equal: the largest value for Budget Movie-Maker is $10,400, but the largest value for Slim Digital is $26,576-more than twice as large.</span></span> <span data-ttu-id="50710-210">그럼에도 불구하고 이 두 행의 가장 큰 막대는 서로 높이가 같습니다.</span><span class="sxs-lookup"><span data-stu-id="50710-210">And yet the largest bars in those two rows are about the same height.</span></span> <span data-ttu-id="50710-211">이러한 막대도 다른 스파크라인에 따라 크기를 조정할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="50710-211">That also needs to be made to scale with the other sparklines.</span></span>  
  
     <span data-ttu-id="50710-212">![rs_SprklineMtrxUnaligndBars](../../2014/tutorials/media/rs-sprklinemtrxunaligndbars.gif "rs_SprklineMtrxUnaligndBars")</span><span class="sxs-lookup"><span data-stu-id="50710-212">![rs_SprklineMtrxUnaligndBars](../../2014/tutorials/media/rs-sprklinemtrxunaligndbars.gif "rs_SprklineMtrxUnaligndBars")</span></span>  
  
##  <a name="4-align-the-sparklines-vertically-and-horizontally"></a><a name="AlignSparklines"></a><span data-ttu-id="50710-213">4. 세로 및 가로로 스파크 라인 맞추기</span><span class="sxs-lookup"><span data-stu-id="50710-213">4. Align the Sparklines Vertically and Horizontally</span></span>  
 <span data-ttu-id="50710-214">스파크 라인은 모두 동일한 측정값을 사용 하지 않는 경우 읽기가 어렵습니다.</span><span class="sxs-lookup"><span data-stu-id="50710-214">The sparklines are hard to read when they don't all use the same measurements.</span></span> <span data-ttu-id="50710-215">각 스파크라인의 가로 축과 세로 축이 나머지와 일치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="50710-215">Both the horizontal and vertical axes for each need to match the rest.</span></span>  
  
#### <a name="to-set-alignment-for-the-sparklines-in-the-table"></a><span data-ttu-id="50710-216">테이블의 스파크라인 맞춤을 설정하려면</span><span class="sxs-lookup"><span data-stu-id="50710-216">To set alignment for the sparklines in the table</span></span>  
  
1.  <span data-ttu-id="50710-217">**디자인** 을 클릭하여 디자인 뷰로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="50710-217">Click **Design** to return to design view.</span></span>  
  
2.  <span data-ttu-id="50710-218">스파크라인을 마우스 오른쪽 단추로 클릭하고 **세로 축 속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="50710-218">Right-click the sparkline and click **Vertical Axis Properties**.</span></span>  
  
3.  <span data-ttu-id="50710-219">**다음 위치의 축 정렬** 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="50710-219">Check the **Align axes in** check box.</span></span>  
  
     <span data-ttu-id="50710-220">목록에 Tablix1이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="50710-220">Tablix1 is showing in the list.</span></span> <span data-ttu-id="50710-221">Tablix1이 유일한 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="50710-221">That is the only option.</span></span> <span data-ttu-id="50710-222">이 옵션은 각 스파크라인의 막대 높이를 서로 상대적인 높이로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="50710-222">This sets the height of the bars in each sparkline relative to the others.</span></span>  
  
4.  <span data-ttu-id="50710-223">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="50710-223">Click **OK**.</span></span>  
  
5.  <span data-ttu-id="50710-224">스파크라인을 마우스 오른쪽 단추로 클릭한 다음 **가로 축 속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="50710-224">Right-click the sparkline and click **Horizontal Axis Properties**.</span></span>  
  
6.  <span data-ttu-id="50710-225">**다음 위치의 축 정렬** 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="50710-225">Check the **Align axes in** check box.</span></span>  
  
     <span data-ttu-id="50710-226">목록에 Tablix1이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="50710-226">Tablix1 is showing in the list.</span></span> <span data-ttu-id="50710-227">Tablix1이 유일한 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="50710-227">That is the only option.</span></span> <span data-ttu-id="50710-228">이 옵션은 각 스파크라인의 막대 너비를 서로 상대적인 너비로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="50710-228">This sets the width of the bars in each sparkline relative to the others.</span></span> <span data-ttu-id="50710-229">다른 스파크라인보다 막대가 적은 스파크라인에서는 데이터가 없는 부분을 나타내는 빈 공간이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="50710-229">If some sparklines have fewer bars than others, then those sparklines will have blank spaces for the missing data.</span></span>  
  
7.  <span data-ttu-id="50710-230">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="50710-230">Click **OK**.</span></span>  
  
8.  <span data-ttu-id="50710-231">**실행** 을 다시 클릭하여 보고서를 미리 봅니다.</span><span class="sxs-lookup"><span data-stu-id="50710-231">Click **Run** to preview your report again.</span></span>  
  
 <span data-ttu-id="50710-232">이제 모든 막대가 다른 행의 막대에 정렬되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50710-232">Note that all the bars are now aligned with the bars in the other rows.</span></span>  
  
##  <a name="5-optional-format-data-as-currency"></a><a name="FormatCurrency"></a><span data-ttu-id="50710-233">5. (선택 사항) 데이터 서식을 통화로 지정</span><span class="sxs-lookup"><span data-stu-id="50710-233">5. (Optional) Format Data as Currency</span></span>  
 <span data-ttu-id="50710-234">기본적으로 **Sales** 필드의 요약 데이터에는 일반 숫자가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="50710-234">By default, the summary data for the **Sales** field displays a general number.</span></span> <span data-ttu-id="50710-235">서식을 지정하여 숫자가 통화로 표시되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="50710-235">Format it to display the number as currency.</span></span> <span data-ttu-id="50710-236">**자리 표시자 스타일** 을 설정/해제하여 서식 있는 입력란 및 자리 표시자 텍스트를 보기 값으로 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="50710-236">Toggle **Placeholder Styles** to display formatted text boxes and placeholder text as sample values.</span></span>  
  
#### <a name="to-format-a-currency-field"></a><span data-ttu-id="50710-237">통화 필드의 서식을 지정하려면</span><span class="sxs-lookup"><span data-stu-id="50710-237">To format a currency field</span></span>  
  
1.  <span data-ttu-id="50710-238">디자인 **을 클릭 하 여 디자인** 뷰로 전환 합니다.</span><span class="sxs-lookup"><span data-stu-id="50710-238">Click **Design** to switch to design view.</span></span>  
  
2.  <span data-ttu-id="50710-239">**SalesDate** 열에서 두 번째 행(열 머리글 행 아래)의 셀을 클릭하고 끌어서 `[Sum(Sales)]`이 포함된 모든 셀을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="50710-239">Click the cell in the second row (under the column headings row) in the **SalesDate** column and drag to select all cells that contain `[Sum(Sales)]`.</span></span>  
  
3.  <span data-ttu-id="50710-240">**홈** 탭의 **숫자** 그룹에서 **통화** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="50710-240">On the **Home** tab, in the **Number** group, click the **Currency** button.</span></span> <span data-ttu-id="50710-241">셀이 변경되어 형식 지정된 통화가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="50710-241">The cells change to show the formatted currency.</span></span>  
  
     <span data-ttu-id="50710-242">국가별 설정이 영어(미국)인 경우 기본 예제 텍스트는 [**$12,345.00**]입니다.</span><span class="sxs-lookup"><span data-stu-id="50710-242">If your regional setting is English (United States), the default sample text is [**$12,345.00**].</span></span> <span data-ttu-id="50710-243">예제 통화 값이 표시되지 않으면 **숫자** 그룹에서 **자리 표시자 스타일** 을 클릭한 다음 **보기 값**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="50710-243">If you do not see an example currency value, click **Placeholder Styles** in the **Numbers** group, and then click **Sample Values**.</span></span>  
  
4.  <span data-ttu-id="50710-244">**실행** 을 클릭하여 보고서를 미리 봅니다.</span><span class="sxs-lookup"><span data-stu-id="50710-244">Click **Run** to preview your report.</span></span>  
  
 <span data-ttu-id="50710-245">**Sales** 의 요약 값이 통화로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="50710-245">The summary values for **Sales** display as currency.</span></span>  
  
##  <a name="6-optional-format-data-as-dates"></a><a name="FormatDates"></a><span data-ttu-id="50710-246">6. (선택 사항) 데이터 서식을 날짜로 지정</span><span class="sxs-lookup"><span data-stu-id="50710-246">6. (Optional) Format Data as Dates</span></span>  
 <span data-ttu-id="50710-247">기본적으로 **salesdate** 필드에는 날짜 및 시간 정보가 모두 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="50710-247">By default, the **SalesDate** field displays both date and time information.</span></span> <span data-ttu-id="50710-248">날짜만 표시되도록 서식을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50710-248">You can format them to display only the date.</span></span>  
  
#### <a name="to-format-a-date-field-as-the-default-format"></a><span data-ttu-id="50710-249">날짜 필드를 기본 형식으로 지정하려면</span><span class="sxs-lookup"><span data-stu-id="50710-249">To format a date field as the default format</span></span>  
  
1.  <span data-ttu-id="50710-250">**디자인** 을 클릭하여 디자인 뷰로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="50710-250">Click **Design** to return to design view.</span></span>  
  
2.  <span data-ttu-id="50710-251">`[SalesDate]`가 들어 있는 셀을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="50710-251">Click the cell that contains `[SalesDate]`.</span></span>  
  
3.  <span data-ttu-id="50710-252">리본의 **홈** 탭에 있는 **숫자** 그룹의 드롭다운 목록에서 **날짜**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="50710-252">On the Ribbon, on the **Home** tab, in the **Number** group, from the drop-down list, select **Date**.</span></span>  
  
     <span data-ttu-id="50710-253">셀에 예제 날짜 **[1/31/2000]** 가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="50710-253">The cell displays the example date **[1/31/2000]**.</span></span> <span data-ttu-id="50710-254">예제 날짜가 표시되지 않으면 **숫자** 그룹에서 **자리 표시자 스타일** 을 클릭한 다음 **보기 값**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="50710-254">If you do not see an example date, click **Placeholder Styles** in the **Numbers** group, and then click **Sample Values**.</span></span>  
  
4.  <span data-ttu-id="50710-255">**실행** 을 클릭하여 보고서를 미리 봅니다.</span><span class="sxs-lookup"><span data-stu-id="50710-255">Click **Run** to preview the report.</span></span>  
  
 <span data-ttu-id="50710-256">**SalesDate** 값이 기본 날짜 형식으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="50710-256">The **SalesDate** values display in the default date format.</span></span>  
  
##  <a name="7-optional-change-column-widths"></a><a name="Width"></a><span data-ttu-id="50710-257">7. (선택 사항) 열 너비 변경</span><span class="sxs-lookup"><span data-stu-id="50710-257">7. (Optional) Change Column Widths</span></span>  
 <span data-ttu-id="50710-258">기본적으로 테이블의 각 셀은 입력란을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="50710-258">By default, each cell in a table contains a text box.</span></span> <span data-ttu-id="50710-259">페이지를 렌더링하면 입력란은 텍스트를 수용하도록 세로로 확장됩니다.</span><span class="sxs-lookup"><span data-stu-id="50710-259">A text box expands vertically to accommodate text when the page is rendered.</span></span> <span data-ttu-id="50710-260">렌더링된 보고서에서 각 행은 해당 행에서 가장 길게 렌더링된 입력란의 높이에 맞춰 확장됩니다.</span><span class="sxs-lookup"><span data-stu-id="50710-260">In the rendered report, each row expands to the height of the tallest rendered text box in the row.</span></span> <span data-ttu-id="50710-261">디자인 화면에서 행의 높이는 렌더링된 보고서의 행 높이에 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="50710-261">The height of the row on the design surface has no affect on the height of the row in the rendered report.</span></span>  
  
 <span data-ttu-id="50710-262">각 행의 세로 크기를 줄이려면 열 입력란에 들어갈 예상 내용이 한 줄에 수용되는 범위에서 열 너비를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="50710-262">To reduce the amount of vertical space each row takes, expand the column width to accommodate the expected contents of the text boxes in the column on one line.</span></span>  
  
#### <a name="to-change-the-width-of-columns"></a><span data-ttu-id="50710-263">열의 너비를 변경하려면</span><span class="sxs-lookup"><span data-stu-id="50710-263">To change the width of columns</span></span>  
  
1.  <span data-ttu-id="50710-264">**디자인** 을 클릭하여 디자인 뷰로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="50710-264">Click **Design** to return to design view.</span></span>  
  
2.  <span data-ttu-id="50710-265">테이블을 클릭하여 열 핸들과 행 핸들이 테이블 위와 옆에 표시되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="50710-265">Click the table so that column and row handles appear above and next to the table.</span></span>  
  
     <span data-ttu-id="50710-266">테이블 위쪽 및 옆쪽을 따라 표시되는 회색 막대는 행 및 열 핸들입니다.</span><span class="sxs-lookup"><span data-stu-id="50710-266">The gray bars along the top and side of the table are the column and row handles.</span></span>  
  
3.  <span data-ttu-id="50710-267">열 핸들 사이의 선에 커서를 두면 커서가 양방향 화살표로 바뀝니다.</span><span class="sxs-lookup"><span data-stu-id="50710-267">Point to the line between column handles so that the cursor changes into a double arrow.</span></span> <span data-ttu-id="50710-268">이 상태에서 열을 끌어 크기를 원하는 대로 조정합니다.</span><span class="sxs-lookup"><span data-stu-id="50710-268">Drag the columns to the size you want.</span></span> <span data-ttu-id="50710-269">예를 들어 제품 이름이 한 줄에 표시되도록 **Product** 에 대한 열을 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="50710-269">For example, expand the column for **Product** so that the product name displays on one line.</span></span>  
  
4.  <span data-ttu-id="50710-270">**실행** 을 클릭하여 보고서를 미리 봅니다.</span><span class="sxs-lookup"><span data-stu-id="50710-270">Click **Run** to preview your report.</span></span>  
  
##  <a name="8-optional-add-a-report-title"></a><a name="Title"></a><span data-ttu-id="50710-271">8. (선택 사항) 보고서 제목 추가</span><span class="sxs-lookup"><span data-stu-id="50710-271">8. (Optional) Add a Report Title</span></span>  
 <span data-ttu-id="50710-272">보고서 제목은 보고서 맨 위에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="50710-272">A report title appears at the top of the report.</span></span> <span data-ttu-id="50710-273">보고서 제목을 보고서 머리글에 배치하거나, 보고서 머리글이 사용되지 않을 경우 보고서 본문의 맨 위에 있는 입력란에 배치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50710-273">You can place the report title in a report header or if the report does not use one, in a text box at the top of the report body.</span></span> <span data-ttu-id="50710-274">이 자습서에서는 보고서 본문의 맨 위에 자동으로 표시되는 입력란을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="50710-274">In this tutorial, you will use the text box that is automatically placed at the top of the report body.</span></span>  
  
 <span data-ttu-id="50710-275">글꼴 스타일, 크기 및 색을 텍스트의 각 문자나 구 단위로 다르게 적용하여 더 보기 좋게 꾸밀 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50710-275">The text can be further enhanced by applying different font styles, sizes, and colors to phrases and individual characters of the text.</span></span> <span data-ttu-id="50710-276">자세한 내용은 [입력란의 텍스트 서식 지정&#40;보고서 작성기 및 SSRS&#41;](report-design/format-text-in-a-text-box-report-builder-and-ssrs.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="50710-276">For more information, see [Format Text in a Text Box &#40;Report Builder and SSRS&#41;](report-design/format-text-in-a-text-box-report-builder-and-ssrs.md).</span></span>  
  
#### <a name="to-add-a-report-title"></a><span data-ttu-id="50710-277">보고서 제목을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="50710-277">To add a report title</span></span>  
  
1.  <span data-ttu-id="50710-278">디자인 화면에서 **제목을 추가하려면 클릭하십시오.** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="50710-278">On the design surface, click **Click to add title**.</span></span>  
  
2.  <span data-ttu-id="50710-279">**Product Sales**를 입력한 다음 입력란 바깥쪽을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="50710-279">Type **Product Sales**, and then click outside the text box.</span></span>  
  
3.  <span data-ttu-id="50710-280">**Product Sales** 가 들어 있는 입력란을 마우스 오른쪽 단추로 클릭하고 **입력란 속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="50710-280">Right-click the text box that contains **Product Sales** and click **Text Box Properties**.</span></span>  
  
4.  <span data-ttu-id="50710-281">**입력란 속성** 대화 상자에서 **글꼴**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="50710-281">In the **Text Box Properties** dialog box, click **Font**.</span></span>  
  
5.  <span data-ttu-id="50710-282">**크기** 목록에서 **18pt**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="50710-282">In the **Size** list, select **18pt**.</span></span>  
  
6.  <span data-ttu-id="50710-283">**색** 목록에서 **적갈색**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="50710-283">In the **Color** list, select **Maroon**.</span></span>  
  
7.  <span data-ttu-id="50710-284">**굵게**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="50710-284">Select **Bold**.</span></span>  
  
8.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
##  <a name="9-save-the-report"></a><a name="Save"></a><span data-ttu-id="50710-285">9. 보고서 저장</span><span class="sxs-lookup"><span data-stu-id="50710-285">9. Save the Report</span></span>  
 <span data-ttu-id="50710-286">보고서 서버 또는 컴퓨터에 보고서를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="50710-286">Save the report to a report server or your computer.</span></span> <span data-ttu-id="50710-287">보고서를 보고서 서버에 저장하지 않을 경우 보고서 파트 및 하위 보고서와 같은 여러 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 기능을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="50710-287">If you do not save the report to the report server, a number of [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] features such as report parts and subreports are not available.</span></span>  
  
#### <a name="to-save-the-report-on-a-report-server"></a><span data-ttu-id="50710-288">보고서를 보고서 서버에 저장하려면</span><span class="sxs-lookup"><span data-stu-id="50710-288">To save the report on a report server</span></span>  
  
1.  <span data-ttu-id="50710-289">**보고서 작성기** 단추에서 다른 **이름으로 저장**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="50710-289">From the **Report Builder** button, click **Save As**.</span></span>  
  
2.  <span data-ttu-id="50710-290">**최근에 사용한 사이트 및 서버**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="50710-290">Click **Recent Sites and Servers**.</span></span>  
  
3.  <span data-ttu-id="50710-291">보고서를 저장할 수 있는 권한을 가진 보고서 서버의 이름을 선택하거나 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="50710-291">Select or type the name of the report server where you have permission to save reports.</span></span>  
  
     <span data-ttu-id="50710-292">"보고서 서버에 연결하는 중"이라는 메시지가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="50710-292">The message "Connecting to report server" appears.</span></span> <span data-ttu-id="50710-293">연결되면 보고서 서버 관리자가 보고서의 기본 위치로 지정한 보고서 폴더의 내용이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="50710-293">When the connection is complete, you see the contents of the report folder that the report server administrator specified as the default location for reports.</span></span>  
  
4.  <span data-ttu-id="50710-294">**이름**에서 기본 이름을 **Product Sales**로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="50710-294">In **Name**, replace the default name with **Product Sales**.</span></span>  
  
5.  <span data-ttu-id="50710-295">**저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="50710-295">Click **Save**.</span></span>  
  
 <span data-ttu-id="50710-296">보고서가 보고서 서버에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="50710-296">The report is saved to the report server.</span></span> <span data-ttu-id="50710-297">연결된 보고서 서버의 이름이 창 아래쪽에 있는 상태 표시줄에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="50710-297">The name of report server that you are connected to appears in the status bar at the bottom of the window.</span></span>  
  
#### <a name="to-save-the-report-on-your-computer"></a><span data-ttu-id="50710-298">컴퓨터에 보고서를 저장하려면</span><span class="sxs-lookup"><span data-stu-id="50710-298">To save the report on your computer</span></span>  
  
1.  <span data-ttu-id="50710-299">**보고서 작성기** 단추에서 다른 **이름으로 저장**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="50710-299">From the **Report Builder** button, click **Save As**.</span></span>  
  
2.  <span data-ttu-id="50710-300">**바탕 화면**, **내 문서**또는 **내 컴퓨터**를 클릭하여 보고서를 저장할 폴더를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="50710-300">Click **Desktop**, **My Documents**, or **My computer**, and browse to the folder where you want to save the report.</span></span>  
  
3.  <span data-ttu-id="50710-301">**이름**에서 기본 이름을 **Product Sales**로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="50710-301">In **Name**, replace the default name with **Product Sales**.</span></span>  
  
4.  <span data-ttu-id="50710-302">**저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="50710-302">Click **Save**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="50710-303">다음 단계</span><span class="sxs-lookup"><span data-stu-id="50710-303">Next Steps</span></span>  
 <span data-ttu-id="50710-304">이것으로 스파크라인 차트가 있는 테이블 보고서를 만드는 자습서를 마칩니다.</span><span class="sxs-lookup"><span data-stu-id="50710-304">This concludes the tutorial for creating a table report with sparkline charts.</span></span> <span data-ttu-id="50710-305">스파크라인에 대한 자세한 내용은 [스파크라인 및 데이터 막대 추가&#40;보고서 작성기 및 SSRS&#41;](report-design/sparklines-and-data-bars-report-builder-and-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="50710-305">For more information about sparklines, see [Sparklines and Data Bars &#40;Report Builder and SSRS&#41;](report-design/sparklines-and-data-bars-report-builder-and-ssrs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50710-306">참고 항목</span><span class="sxs-lookup"><span data-stu-id="50710-306">See Also</span></span>  
 <span data-ttu-id="50710-307">[자습서 &#40;보고서 작성기&#41;](report-builder-tutorials.md) </span><span class="sxs-lookup"><span data-stu-id="50710-307">[Tutorials &#40;Report Builder&#41;](report-builder-tutorials.md) </span></span>  
 [<span data-ttu-id="50710-308">SQL Server 2014의 보고서 작성기</span><span class="sxs-lookup"><span data-stu-id="50710-308">Report Builder in SQL Server 2014</span></span>](report-builder/report-builder-in-sql-server-2016.md)  
  
  
