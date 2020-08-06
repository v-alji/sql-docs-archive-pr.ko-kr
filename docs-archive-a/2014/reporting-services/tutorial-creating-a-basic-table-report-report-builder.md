---
title: '자습서: 기본 테이블 보고서 만들기(보고서 작성기) | Microsoft Docs'
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: d9e30521-f8ae-4c45-89c3-d40727f622f7
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3587e2a53e2b09dd347a2733875eafd708b8a05a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648253"
---
# <a name="tutorial-creating-a-basic-table-report-report-builder"></a><span data-ttu-id="6dde7-102">자습서: 기본 테이블 보고서 만들기(보고서 작성기)</span><span class="sxs-lookup"><span data-stu-id="6dde7-102">Tutorial: Creating a Basic Table Report (Report Builder)</span></span>
  <span data-ttu-id="6dde7-103">이 자습서에서는 예제 판매 데이터를 기반으로 기본 테이블 보고서를 만드는 방법을 배웁니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-103">This tutorial teaches you to create a basic table report based on sample sales data.</span></span> <span data-ttu-id="6dde7-104">다음 그림에서는 만들려는 보고서를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-104">The following illustration shows the report you will create.</span></span>  
  
 <span data-ttu-id="6dde7-105">![rs_CreateBasicReportTutorial](../../2014/tutorials/media/rs-createbasicreporttutorial.gif "rs_CreateBasicReportTutorial")</span><span class="sxs-lookup"><span data-stu-id="6dde7-105">![rs_CreateBasicReportTutorial](../../2014/tutorials/media/rs-createbasicreporttutorial.gif "rs_CreateBasicReportTutorial")</span></span>  
  
##  <a name="what-you-will-learn"></a><a name="BackToTop"></a><span data-ttu-id="6dde7-106">학습 내용</span><span class="sxs-lookup"><span data-stu-id="6dde7-106">What You Will Learn</span></span>  
 <span data-ttu-id="6dde7-107">이 자습서에서는 다음 작업 방법을 배웁니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-107">In this tutorial, you will learn how to do the following:</span></span>  
  
1.  [<span data-ttu-id="6dde7-108">시작 대화 상자에서 새 보고서 만들기</span><span class="sxs-lookup"><span data-stu-id="6dde7-108">Create a New Report from Getting Started</span></span>](#CreateTable)  
  
    1.  [<span data-ttu-id="6dde7-109">테이블 마법사에서 데이터 연결 지정</span><span class="sxs-lookup"><span data-stu-id="6dde7-109">Specify a Data Connection in the Table Wizard</span></span>](#DataConnection)  
  
    2.  [<span data-ttu-id="6dde7-110">테이블 마법사에서 쿼리 만들기</span><span class="sxs-lookup"><span data-stu-id="6dde7-110">Create a Query in the Table Wizard</span></span>](#Query)  
  
    3.  [<span data-ttu-id="6dde7-111">테이블 마법사에서 데이터를 그룹으로 구성</span><span class="sxs-lookup"><span data-stu-id="6dde7-111">Organize Data into Groups in the Table Wizard</span></span>](#Groups)  
  
    4.  [<span data-ttu-id="6dde7-112">테이블 마법사에서 부분합 및 합계 행 추가</span><span class="sxs-lookup"><span data-stu-id="6dde7-112">Add Subtotal and Total Rows in the Table Wizard</span></span>](#Subtotals)  
  
    5.  [<span data-ttu-id="6dde7-113">테이블 마법사에서 스타일 선택</span><span class="sxs-lookup"><span data-stu-id="6dde7-113">Choose a Style in the Table Wizard</span></span>](#Style)  
  
2.  [<span data-ttu-id="6dde7-114">데이터 형식을 통화로 지정</span><span class="sxs-lookup"><span data-stu-id="6dde7-114">Format Data as Currency</span></span>](#FormatCurrency)  
  
3.  [<span data-ttu-id="6dde7-115">데이터 형식을 날짜로 지정</span><span class="sxs-lookup"><span data-stu-id="6dde7-115">Format Data as Date</span></span>](#FormatDate)  
  
4.  [<span data-ttu-id="6dde7-116">열 너비 변경</span><span class="sxs-lookup"><span data-stu-id="6dde7-116">Change Column Widths</span></span>](#Width)  
  
5.  [<span data-ttu-id="6dde7-117">보고서 제목 추가</span><span class="sxs-lookup"><span data-stu-id="6dde7-117">Add a Report Title</span></span>](#Title)  
  
6.  [<span data-ttu-id="6dde7-118">보고서 저장</span><span class="sxs-lookup"><span data-stu-id="6dde7-118">Save the Report</span></span>](#Save)  
  
7.  [<span data-ttu-id="6dde7-119">보고서 내보내기</span><span class="sxs-lookup"><span data-stu-id="6dde7-119">Export the Report</span></span>](#Export)  
  
 <span data-ttu-id="6dde7-120">이 자습서에 소요되는 예상 시간: 20분</span><span class="sxs-lookup"><span data-stu-id="6dde7-120">Estimated time to complete this tutorial: 20 minutes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6dde7-121">요구 사항</span><span class="sxs-lookup"><span data-stu-id="6dde7-121">Requirements</span></span>  
 <span data-ttu-id="6dde7-122">요구 사항에 대한 자세한 내용은 [자습서의 필수 조건&#40;보고서 작성기&#41;](../reporting-services/report-builder-tutorials.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6dde7-122">For more information about requirements, see [Prerequisites for Tutorials &#40;Report Builder&#41;](../reporting-services/report-builder-tutorials.md).</span></span>  
  
##  <a name="1-create-a-new-report-from-getting-started"></a><a name="CreateTable"></a><span data-ttu-id="6dde7-123">1. 시작에서 새 보고서 만들기</span><span class="sxs-lookup"><span data-stu-id="6dde7-123">1. Create a New Report from Getting Started</span></span>  
 <span data-ttu-id="6dde7-124">**시작** 대화 상자에서 테이블 보고서를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-124">Create a table report from the **Getting Started** dialog box.</span></span> <span data-ttu-id="6dde7-125">보고서 디자인 모드와 공유 데이터 세트 디자인 모드라는 두 가지 모드가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-125">There are two modes: report design and shared dataset design.</span></span> <span data-ttu-id="6dde7-126">보고서 디자인 모드에서는 보고서 데이터 창에서 데이터를 지정하고 디자인 화면에서 보고서 레이아웃을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-126">In report design mode, you specify data in the Report Data pane and the report layout on the design surface.</span></span> <span data-ttu-id="6dde7-127">공유 데이터 세트 디자인 모드에서는 다른 사용자와 공유할 데이터 세트 쿼리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-127">In shared dataset design mode, you create dataset queries to share with others.</span></span> <span data-ttu-id="6dde7-128">이 자습서에서는 보고서 디자인 모드를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-128">In this tutorial, you will be using report design mode.</span></span>  
  
#### <a name="to-create-a-new-report"></a><span data-ttu-id="6dde7-129">새 보고서를 만들려면</span><span class="sxs-lookup"><span data-stu-id="6dde7-129">To create a new report</span></span>  
  
1.  <span data-ttu-id="6dde7-130">**시작**을 클릭하고 **프로그램**, **Microsoft SQL Server 2012 보고서 작성기**를 차례로 가리킨 다음 **보고서 작성기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-130">Click **Start**, point to **Programs**, point to **Microsoft SQL Server 2012 Report Builder**, and then click **Report Builder**.</span></span>  
  
     <span data-ttu-id="6dde7-131">**시작** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-131">The **Getting Started** dialog box opens.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="6dde7-132">**시작** 대화 상자가 나타나지 않으면 **보고서 작성기** 단추에서 **새로 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-132">If the **Getting Started** dialog box does not appear, from the **Report Builder** button, click **New**.</span></span>  
  
2.  <span data-ttu-id="6dde7-133">왼쪽 창에 **새 보고서** 가 선택되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-133">In the left pane, verify that **New Report** is selected.</span></span>  
  
3.  <span data-ttu-id="6dde7-134">오른쪽 창에서 **테이블 또는 행렬 마법사** 가 선택되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-134">In the right pane, verify that **Table or Matrix Wizard** is selected.</span></span>  
  
##  <a name="1a-specify-a-data-connection-in-the-table-wizard"></a><a name="DataConnection"></a><span data-ttu-id="6dde7-135">a.</span><span class="sxs-lookup"><span data-stu-id="6dde7-135">1a.</span></span> <span data-ttu-id="6dde7-136">테이블 마법사에서 데이터 연결 지정</span><span class="sxs-lookup"><span data-stu-id="6dde7-136">Specify a Data Connection in the Table Wizard</span></span>  
 <span data-ttu-id="6dde7-137">데이터 연결은 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 데이터베이스와 같은 외부 데이터 원본에 연결하는 데 필요한 정보를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-137">A data connection contains the information to connect to an external data source such as a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] database.</span></span> <span data-ttu-id="6dde7-138">일반적으로 데이터 원본 소유자로부터 사용할 자격 증명 유형과 연결 정보를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-138">Usually, you get the connection information and the type of credentials to use from the data source owner.</span></span> <span data-ttu-id="6dde7-139">데이터 연결을 지정하기 위해 보고서 서버의 공유 데이터 원본을 사용하거나 이 보고서에만 사용되는 포함된 데이터 원본을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-139">To specify a data connection, you can use a shared data source from the report server or create an embedded data source that is used only in this report.</span></span>  
  
 <span data-ttu-id="6dde7-140">이 자습서에서는 포함된 데이터 원본을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-140">In this tutorial, you will use an embedded data source.</span></span> <span data-ttu-id="6dde7-141">공유 데이터 원본 사용 방법에 대한 자세한 내용은 [데이터에 연결하는 다른 방법&#40;보고서 작성기&#41;](../reporting-services/alternative-ways-to-get-a-data-connection-report-builder.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6dde7-141">To learn more about using a shared data sources, see [Alternative Ways to Get a Data Connection &#40;Report Builder&#41;](../reporting-services/alternative-ways-to-get-a-data-connection-report-builder.md).</span></span>  
  
#### <a name="to-create-an-embedded-data-source"></a><span data-ttu-id="6dde7-142">포함된 데이터 원본을 만들려면</span><span class="sxs-lookup"><span data-stu-id="6dde7-142">To create an embedded data source</span></span>  
  
1.  <span data-ttu-id="6dde7-143">**데이터 세트 선택** 페이지에서 **데이터 세트 만들기**를 선택한 후, **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-143">On the **Choose a dataset** page, select **Create a dataset**, and then click **Next**.</span></span> <span data-ttu-id="6dde7-144">**데이터 원본에 대한 연결 선택** 페이지가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-144">The **Choose a connection to a data source** page opens.</span></span>  
  
2.  <span data-ttu-id="6dde7-145">**새로 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-145">Click **New**.</span></span> <span data-ttu-id="6dde7-146">**데이터 원본 속성** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-146">The **Data Source Properties** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="6dde7-147">**이름**에 데이터 원본 이름으로 **Product Sales** 를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-147">In **Name**, type **Product Sales** a name for the data source.</span></span>  
  
4.  <span data-ttu-id="6dde7-148">**연결 유형 선택**에서 **Microsoft SQL Server** 가 선택되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-148">In **Select a connection type**, verify that **Microsoft SQL Server** is selected.</span></span>  
  
5.  <span data-ttu-id="6dde7-149">**연결 문자열**에 다음 텍스트를 입력 합니다. 여기서 *\<servername>* 은 인스턴스의 이름입니다 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="6dde7-149">In **Connection string**, type the following text, where *\<servername>* is the name of an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]:</span></span>  
  
    ```  
    Data Source=<servername>  
    ```  
  
     <span data-ttu-id="6dde7-150">데이터베이스에서 데이터를 검색하는 대신 데이터가 포함된 쿼리를 사용하기 때문에 연결 문자열에 데이터베이스 이름은 포함되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-150">Because you will use a query that contains the data instead of retrieving the data from a database, the connection string does not include the database name.</span></span> <span data-ttu-id="6dde7-151">자세한 내용은 [자습서의 사전 요구 사항 &#40;보고서 작성기&#41;](../reporting-services/report-builder-tutorials.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6dde7-151">For more information, see [Prerequisites for Tutorials &#40;Report Builder&#41;](../reporting-services/report-builder-tutorials.md).</span></span>  
  
6.  <span data-ttu-id="6dde7-152">**자격 증명**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-152">Click **Credentials**.</span></span> <span data-ttu-id="6dde7-153">외부 데이터 원본에 액세스하는 데 필요한 자격 증명을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-153">Enter the credentials that you need to access the external data source.</span></span>  
  
7.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
     <span data-ttu-id="6dde7-154">**데이터 원본에 대한 연결 선택** 페이지로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-154">You are back on the **Choose a connection to a data source** page.</span></span>  
  
8.  <span data-ttu-id="6dde7-155">데이터 원본에 연결할 수 있는지 확인하려면 **연결 테스트**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-155">To verify that you can connect to the data source, click **Test Connection**.</span></span>  
  
     <span data-ttu-id="6dde7-156">"연결되었습니다."라는 메시지가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-156">The message "Connection created successfully" appears.</span></span>  
  
9. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
10. <span data-ttu-id="6dde7-157">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-157">Click **Next**.</span></span>  
  
##  <a name="1b-create-a-query-in-the-table-wizard"></a><a name="Query"></a><span data-ttu-id="6dde7-158">1b.</span><span class="sxs-lookup"><span data-stu-id="6dde7-158">1b.</span></span> <span data-ttu-id="6dde7-159">테이블 마법사에서 쿼리 만들기</span><span class="sxs-lookup"><span data-stu-id="6dde7-159">Create a Query in the Table Wizard</span></span>  
 <span data-ttu-id="6dde7-160">보고서에서는 미리 정의된 쿼리가 포함된 공유 데이터 세트를 사용하거나 해당 보고서에만 사용할 포함된 데이터 세트를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-160">In a report, you can use a shared dataset that has a predefined query, or you can create an embedded dataset for use only in your report.</span></span> <span data-ttu-id="6dde7-161">이 자습서에서는 포함된 데이터 세트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-161">In this tutorial, you will create an embedded dataset.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6dde7-162">이 자습서의 쿼리에는 데이터 값이 포함되어 있으므로 외부 데이터 원본이 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-162">In this tutorial, the query contains the data values, so that it does not need an external data source.</span></span> <span data-ttu-id="6dde7-163">따라서 쿼리가 상당히 길어집니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-163">This makes the query quite long.</span></span> <span data-ttu-id="6dde7-164">비즈니스 환경에서는 쿼리에 데이터가 포함되지 않을 것입니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-164">In a business environment, a query would not contain the data.</span></span> <span data-ttu-id="6dde7-165">이 자습서의 쿼리는 학습용으로만 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-165">This is for learning purposes only.</span></span>  
  
#### <a name="to-create-a-query"></a><span data-ttu-id="6dde7-166">쿼리를 만들려면</span><span class="sxs-lookup"><span data-stu-id="6dde7-166">To create a query</span></span>  
  
1.  <span data-ttu-id="6dde7-167">**쿼리 디자인** 페이지에 관계형 쿼리 디자이너가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-167">On the **Design a query** page, the relational query designer is open.</span></span> <span data-ttu-id="6dde7-168">이 자습서에서는 텍스트 기반 쿼리 디자이너를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-168">For this tutorial, you will use the text-based query designer.</span></span>  
  
     <span data-ttu-id="6dde7-169">**텍스트로 편집을**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-169">Click **Edit As Text**.</span></span> <span data-ttu-id="6dde7-170">텍스트 기반 쿼리 디자이너에 쿼리 창과 결과 창이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-170">The text-based query designer displays a query pane and a results pane.</span></span>  
  
2.  <span data-ttu-id="6dde7-171">[!INCLUDE[tsql](../includes/tsql-md.md)] 쿼리 **상자에 다음** 쿼리를 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-171">Paste the following [!INCLUDE[tsql](../includes/tsql-md.md)] query into the **Query** box.</span></span>  
  
    ```  
    SELECT CAST('2009-01-05' AS date) as SalesDate, 'Accessories' as Subcategory,   
       'Carrying Case' as Product, CAST(9924.60 AS money) AS Sales, 68 as Quantity  
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
  
3.  <span data-ttu-id="6dde7-172">쿼리 디자이너 도구 모음에서 **실행** (**!**)을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-172">On the query designer toolbar, click **Run** (**!**).</span></span>  
  
     <span data-ttu-id="6dde7-173">쿼리가 실행되고 SalesDate, Subcategory, Product, Sales 및 Quantity 필드에 대한 결과 집합이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-173">The query runs and displays the result set for the fields SalesDate, Subcategory, Product, Sales, and Quantity.</span></span>  
  
     <span data-ttu-id="6dde7-174">결과 집합의 열 제목은 쿼리에 있는 이름을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-174">In the result set, the column headings are based on the names in the query.</span></span> <span data-ttu-id="6dde7-175">데이터 세트의 열 제목은 필드 이름이 되며 보고서에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-175">In the dataset, the column headings become the field names, and are saved in the report.</span></span> <span data-ttu-id="6dde7-176">마법사를 완료한 후 보고서 데이터 창에서 데이터 세트 필드 모음을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-176">After you complete the wizard, you can use the Report Data pane to view the collection of dataset fields.</span></span>  
  
4.  <span data-ttu-id="6dde7-177">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-177">Click **Next**.</span></span>  
  
##  <a name="1c-organize-data-into-groups-in-the-table-wizard"></a><a name="Groups"></a><span data-ttu-id="6dde7-178">1c.</span><span class="sxs-lookup"><span data-stu-id="6dde7-178">1c.</span></span> <span data-ttu-id="6dde7-179">테이블 마법사에서 데이터를 그룹으로 구성</span><span class="sxs-lookup"><span data-stu-id="6dde7-179">Organize Data into Groups in the Table Wizard</span></span>  
 <span data-ttu-id="6dde7-180">그룹화할 필드를 선택할 때 세부 데이터와 집계 데이터가 표시되는 행과 열이 포함된 테이블을 디자인합니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-180">When you select fields to group on, you design a table that has rows and columns that display detail data and aggregated data.</span></span>  
  
#### <a name="to-organize-data-into-groups"></a><span data-ttu-id="6dde7-181">데이터를 그룹으로 구성하려면</span><span class="sxs-lookup"><span data-stu-id="6dde7-181">To organize data into groups</span></span>  
  
1.  <span data-ttu-id="6dde7-182">**필드 정렬** 페이지에서 **값**에 Product를 끌어 옵니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-182">On the **Arrange fields** page, drag Product to **Values**.</span></span>  
  
2.  <span data-ttu-id="6dde7-183">**값** 의 Product 아래에 Quantity를 끌어옵니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-183">Drag Quantity to **Values** and place below Product.</span></span>  
  
     <span data-ttu-id="6dde7-184">Quantity는 숫자 필드에 대한 기본 집계 함수인 Sum 함수를 통해 자동으로 집계됩니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-184">Quantity is automatically aggregated by the Sum function, the default aggregate for numeric fields.</span></span> <span data-ttu-id="6dde7-185">값은 [Sum(Quantity)]입니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-185">The value is [Sum(Quantity)].</span></span>  
  
     <span data-ttu-id="6dde7-186">드롭다운 목록을 열어 사용 가능한 다른 집계 함수를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-186">You can open the drop-down list to view the other aggregate functions available.</span></span> <span data-ttu-id="6dde7-187">집계 함수를 변경하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="6dde7-187">Do not change the aggregate function.</span></span>  
  
3.  <span data-ttu-id="6dde7-188">**값** 의 [Sum(Quantity)] 아래에 Sales를 끌어옵니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-188">Drag Sales to **Values** and place below [Sum(Quantity)].</span></span>  
  
     <span data-ttu-id="6dde7-189">Sales는 Sum 함수로 집계됩니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-189">Sales is aggregated by the Sum function.</span></span> <span data-ttu-id="6dde7-190">값은 [Sum(Sales)]입니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-190">The value is [Sum(Sales)].</span></span>  
  
     <span data-ttu-id="6dde7-191">1, 2, 3단계에서는 테이블에 표시할 데이터를 지정했습니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-191">Steps 1, 2, and 3 specify the data to display in the table.</span></span>  
  
4.  <span data-ttu-id="6dde7-192">**행 그룹**에 SalesDate를 끌어옵니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-192">Drag SalesDate to **Row groups**.</span></span>  
  
5.  <span data-ttu-id="6dde7-193">**행 그룹** 의 SalesDate 아래에 Subcategory를 끌어옵니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-193">Drag Subcategory to **Row groups** and place below SalesDate.</span></span>  
  
     <span data-ttu-id="6dde7-194">4, 5단계에서는 필드 값을 먼저 날짜 기준으로 정렬한 다음 해당 날짜의 제품 하위 범주를 기준으로 정렬했습니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-194">Steps 4 and 5 organize the values for the fields first by date, and then by product subcategory for that date.</span></span>  
  
6.  <span data-ttu-id="6dde7-195">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-195">Click **Next**.</span></span>  
  
##  <a name="1d-add-subtotal-and-total-rows-in-the-table-wizard"></a><a name="Subtotals"></a><span data-ttu-id="6dde7-196">차원.</span><span class="sxs-lookup"><span data-stu-id="6dde7-196">1d.</span></span> <span data-ttu-id="6dde7-197">테이블 마법사에서 부분합 및 합계 행 추가</span><span class="sxs-lookup"><span data-stu-id="6dde7-197">Add Subtotal and Total Rows in the Table Wizard</span></span>  
 <span data-ttu-id="6dde7-198">그룹을 만든 후 필드에 대한 집계 값을 표시할 행을 추가하고 행 서식을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-198">After you create groups, you can add and format rows on which to display aggregate values for the fields.</span></span> <span data-ttu-id="6dde7-199">모든 데이터를 표시할지 또는 사용자가 그룹화된 데이터를 대화형으로 확장하거나 축소할 수 있도록 할지 여부를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-199">You can choose whether to show all the data or to let a user expand and collapse grouped data interactively.</span></span>  
  
#### <a name="to-add-subtotals-and-totals"></a><span data-ttu-id="6dde7-200">부분합 및 합계를 추가하려면</span><span class="sxs-lookup"><span data-stu-id="6dde7-200">To add subtotals and totals</span></span>  
  
1.  <span data-ttu-id="6dde7-201">**레이아웃 선택** 페이지의 **옵션**에서 **부분합 및 총합계 표시** 가 선택 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-201">On the **Choose the layout** page, under **Options**, verify that **Show subtotals and grand totals** is selected.</span></span>  
  
2.  <span data-ttu-id="6dde7-202">**블록형, 부분합 하단 표시** 가 선택되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-202">Verify that **Blocked, subtotal below** is selected.</span></span>  
  
     <span data-ttu-id="6dde7-203">마법사 미리 보기 창에 5개의 행이 있는 테이블이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-203">The wizard Preview pane displays a table with five rows.</span></span> <span data-ttu-id="6dde7-204">보고서를 실행하면 각 행이 다음과 같은 방식으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-204">When you run the report, each row will display in the following way:</span></span>  
  
    1.  <span data-ttu-id="6dde7-205">첫 번째 행은 열 제목을 보여 주기 위해 테이블에 대해 한 번씩 반복됩니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-205">The first row will repeat once for the table to show column headings.</span></span>  
  
    2.  <span data-ttu-id="6dde7-206">두 번째 행은 판매 주문의 각 품목에 대해 한 번씩 반복되고 제품 이름, 주문 수량 및 라인 합계를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-206">The second row will repeat once for each line item in the sales order and display the product name, order quantity, and line total.</span></span>  
  
    3.  <span data-ttu-id="6dde7-207">세 번째 행은 주문당 부분합을 표시하기 위해 각 판매 주문에 대해 한 번씩 반복됩니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-207">The third row will repeat once for each sales order to display subtotals per order.</span></span>  
  
    4.  <span data-ttu-id="6dde7-208">네 번째 행은 일별 부분합을 표시하기 위해 각 주문 날짜에 대해 한 번씩 반복됩니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-208">The fourth row will repeat once for each order date to display the subtotals per day.</span></span>  
  
    5.  <span data-ttu-id="6dde7-209">다섯 번째 행은 총합계를 표시하기 위해 테이블에 대해 한 번씩 반복됩니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-209">The fifth row will repeat once for the table to display the grand totals.</span></span>  
  
3.  <span data-ttu-id="6dde7-210">**그룹 확장/축소**옵션을 선택 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-210">Clear the option **Expand/collapse groups**.</span></span> <span data-ttu-id="6dde7-211">이 자습서에서 만든 보고서에는 부모 그룹 계층을 확장하여 자식 그룹 행 및 정보 행을 표시하는 데 사용할 수 있는 드릴다운 기능이 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-211">In this tutorial, the report you create does not use the drilldown feature that lets a user expand a parent group hierarchy to display child group rows and detail rows.</span></span>  
  
4.  <span data-ttu-id="6dde7-212">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-212">Click **Next**.</span></span>  
  
##  <a name="1e-choose-a-style-in-the-table-wizard"></a><a name="Style"></a><span data-ttu-id="6dde7-213">e.</span><span class="sxs-lookup"><span data-stu-id="6dde7-213">1e.</span></span> <span data-ttu-id="6dde7-214">테이블 마법사에서 스타일 선택</span><span class="sxs-lookup"><span data-stu-id="6dde7-214">Choose a Style in the Table Wizard</span></span>  
 <span data-ttu-id="6dde7-215">스타일은 글꼴 스타일, 색 집합 및 테두리 스타일을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-215">A style specifies a font style, a set of colors, and a border style.</span></span>  
  
#### <a name="to-specify-a-table-style"></a><span data-ttu-id="6dde7-216">테이블 스타일을 지정하려면</span><span class="sxs-lookup"><span data-stu-id="6dde7-216">To specify a table style</span></span>  
  
1.  <span data-ttu-id="6dde7-217">**스타일 선택** 페이지의 스타일 창에서 해양를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-217">On the **Choose a Style** page, in the Styles pane, select Ocean.</span></span>  
  
     <span data-ttu-id="6dde7-218">미리 보기 창에 해당 스타일이 적용된 예제 테이블이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-218">The Preview pane displays a sample of the table with that style.</span></span>  
  
2.  <span data-ttu-id="6dde7-219">필요에 따라 다른 스타일을 클릭하여 스타일이 적용된 샘플을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-219">Optionally, click the other styles to see the sample with them applied.</span></span>  
  
3.  <span data-ttu-id="6dde7-220">**Finish**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-220">Click **Finish**.</span></span>  
  
 <span data-ttu-id="6dde7-221">디자인 화면에 테이블이 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-221">The table is added to the design surface.</span></span> <span data-ttu-id="6dde7-222">이 테이블에는 열 5개와 행 5개가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-222">The table has 5 columns and 5 rows.</span></span> <span data-ttu-id="6dde7-223">행 그룹 창에는 SalesDate, Subcategory 및 Details라는 3개의 행 그룹이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-223">The Row Groups pane shows three row groups: SalesDate, Subcategory, and Details.</span></span> <span data-ttu-id="6dde7-224">세부 데이터는 모두 데이터 세트 쿼리로 검색된 데이터입니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-224">Detail data is all the data that is retrieved by the dataset query.</span></span>  
  
##  <a name="2-format-data-as-currency"></a><a name="FormatCurrency"></a><span data-ttu-id="6dde7-225">2. 데이터 서식을 통화로 지정</span><span class="sxs-lookup"><span data-stu-id="6dde7-225">2. Format Data as Currency</span></span>  
 <span data-ttu-id="6dde7-226">기본적으로 Sales 필드의 요약 데이터에는 일반 숫자가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-226">By default, the summary data for the Sales field displays a general number.</span></span> <span data-ttu-id="6dde7-227">서식을 지정하여 숫자가 통화로 표시되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-227">Format it to display the number as currency.</span></span> <span data-ttu-id="6dde7-228">**자리 표시자 스타일** 을 설정/해제하여 서식 있는 입력란 및 자리 표시자 텍스트를 보기 값으로 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-228">Toggle **Placeholder Styles** to display formatted text boxes and placeholder text as sample values.</span></span>  
  
#### <a name="to-format-a-currency-field"></a><span data-ttu-id="6dde7-229">통화 필드의 서식을 지정하려면</span><span class="sxs-lookup"><span data-stu-id="6dde7-229">To format a currency field</span></span>  
  
1.  <span data-ttu-id="6dde7-230">디자인 **을 클릭 하 여 디자인** 뷰로 전환 합니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-230">Click **Design** to switch to design view.</span></span>  
  
2.  <span data-ttu-id="6dde7-231">Sales 열에서 두 번째 행(열 제목 행 아래)의 셀을 클릭하고 아래쪽으로 끌어서 `[Sum(Sales)]`이 포함된 모든 셀을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-231">Click the cell in the second row (under the column headings row) in the Sales column and drag down to select all cells that contain `[Sum(Sales)]`.</span></span>  
  
3.  <span data-ttu-id="6dde7-232">**홈** 탭의 **숫자** 그룹에서 **통화** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-232">On the **Home** tab, in the **Number** group, click the **Currency** button.</span></span> <span data-ttu-id="6dde7-233">셀이 변경되어 형식 지정된 통화가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-233">The cells change to show the formatted currency.</span></span>  
  
     <span data-ttu-id="6dde7-234">국가별 설정이 영어(미국)인 경우 기본 예제 텍스트는 [**$12,345.00**]입니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-234">If your regional setting is English (United States), the default sample text is [**$12,345.00**].</span></span> <span data-ttu-id="6dde7-235">예제 통화 값이 표시되지 않으면 **숫자** 그룹에서 **자리 표시자 스타일** 을 클릭한 다음 **보기 값**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-235">If you do not see an example currency value, click **Placeholder Styles** in the **Numbers** group, and then click **Sample Values**.</span></span>  
  
4.  <span data-ttu-id="6dde7-236">**실행** 을 클릭하여 보고서를 미리 봅니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-236">Click **Run** to preview your report.</span></span>  
  
 <span data-ttu-id="6dde7-237">Sales의 요약 값이 통화로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-237">The summary values for Sales display as currency.</span></span>  
  
##  <a name="3-format-data-as-date"></a><a name="FormatDate"></a><span data-ttu-id="6dde7-238">3. 데이터 형식을 날짜로 지정</span><span class="sxs-lookup"><span data-stu-id="6dde7-238">3. Format Data as Date</span></span>  
 <span data-ttu-id="6dde7-239">기본적으로 SalesDate 필드에는 날짜 및 시간 정보가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-239">By default, the SalesDate field displays both date and time information.</span></span> <span data-ttu-id="6dde7-240">날짜만 표시되도록 서식을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-240">You can format them to display only the date.</span></span>  
  
#### <a name="to-format-a-date-field-as-the-default-format"></a><span data-ttu-id="6dde7-241">날짜 필드를 기본 형식으로 지정하려면</span><span class="sxs-lookup"><span data-stu-id="6dde7-241">To format a date field as the default format</span></span>  
  
1.  <span data-ttu-id="6dde7-242">**디자인** 을 클릭하여 디자인 뷰로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-242">Click **Design** to return to design view.</span></span>  
  
2.  <span data-ttu-id="6dde7-243">`[SalesDate]`가 들어 있는 셀을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-243">Click the cell that contains `[SalesDate]`.</span></span>  
  
3.  <span data-ttu-id="6dde7-244">리본의 **홈** 탭에 있는 **숫자** 그룹의 드롭다운 목록에서 **날짜**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-244">On the Ribbon, on the **Home** tab, in the **Number** group, from the drop-down list, select **Date**.</span></span>  
  
     <span data-ttu-id="6dde7-245">셀에 예제 날짜 **[1/31/2000]** 가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-245">The cell displays the example date **[1/31/2000]**.</span></span> <span data-ttu-id="6dde7-246">예제 날짜가 표시되지 않으면 **숫자** 그룹에서 **자리 표시자 스타일** 을 클릭한 다음 **보기 값**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-246">If you do not see an example date, click **Placeholder Styles** in the **Numbers** group, and then click **Sample Values**.</span></span>  
  
4.  <span data-ttu-id="6dde7-247">**실행** 을 클릭하여 보고서를 미리 봅니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-247">Click **Run** to preview the report.</span></span>  
  
 <span data-ttu-id="6dde7-248">SalesDate 값이 기본 날짜 형식으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-248">The SalesDate values display in the default date format.</span></span>  
  
#### <a name="to-change-the-date-format-to-a-custom-format"></a><span data-ttu-id="6dde7-249">날짜 형식을 사용자 지정 형식으로 변경하려면</span><span class="sxs-lookup"><span data-stu-id="6dde7-249">To change the date format to a custom format</span></span>  
  
1.  <span data-ttu-id="6dde7-250">**디자인** 을 클릭하여 디자인 뷰로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-250">Click **Design** to return to design view.</span></span>  
  
2.  <span data-ttu-id="6dde7-251">`[SalesDate]`가 들어 있는 셀을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-251">Click the cell that contains `[SalesDate]`.</span></span>  
  
3.  <span data-ttu-id="6dde7-252">**홈** 탭의 **숫자** 그룹에서 대화 상자 시작 관리자를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-252">On the **Home** tab, in the **Number** group, click the dialog box launcher.</span></span>  
  
     <span data-ttu-id="6dde7-253">그룹의 오른쪽 모퉁이에 있는 작은 화살표가 실행 프로그램입니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-253">The launcher is the small arrow in the right-hand corner of the group.</span></span> <span data-ttu-id="6dde7-254">**입력란 속성** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-254">The **Text Box Properties** dialog box opens.</span></span>  
  
4.  <span data-ttu-id="6dde7-255">범주 창에서 **날짜** 가 선택되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-255">In the Category pane, verify that **Date** is selected.</span></span>  
  
5.  <span data-ttu-id="6dde7-256">**유형** 창에서 **January 31, 2000**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-256">In the **Type** pane, select **January 31, 2000**.</span></span>  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
     <span data-ttu-id="6dde7-257">셀에 예제 날짜 **[January 31, 2000]** 이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-257">The cell displays the example date **[January 31, 2000]**.</span></span>  
  
7.  <span data-ttu-id="6dde7-258">**실행** 을 클릭하여 보고서를 미리 봅니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-258">Click **Run** to preview your report.</span></span>  
  
 <span data-ttu-id="6dde7-259">SalesDate 값이 월에 해당하는 숫자 대신 월의 이름과 함께 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-259">The SalesDate value displays with the name of the month instead of the number for the month.</span></span>  
  
##  <a name="4-change-column-widths"></a><a name="Width"></a><span data-ttu-id="6dde7-260">4. 열 너비 변경</span><span class="sxs-lookup"><span data-stu-id="6dde7-260">4. Change Column Widths</span></span>  
 <span data-ttu-id="6dde7-261">기본적으로 테이블의 각 셀은 입력란을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-261">By default, each cell in a table contains a text box.</span></span> <span data-ttu-id="6dde7-262">페이지를 렌더링하면 입력란은 텍스트를 수용하도록 세로로 확장됩니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-262">A text box expands vertically to accommodate text when the page is rendered.</span></span> <span data-ttu-id="6dde7-263">렌더링된 보고서에서 각 행은 해당 행에서 가장 길게 렌더링된 입력란의 높이에 맞춰 확장됩니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-263">In the rendered report, each row expands to the height of the tallest rendered text box in the row.</span></span> <span data-ttu-id="6dde7-264">디자인 화면에서 행의 높이는 렌더링된 보고서의 행 높이에 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-264">The height of the row on the design surface has no affect on the height of the row in the rendered report.</span></span>  
  
 <span data-ttu-id="6dde7-265">각 행의 세로 크기를 줄이려면 열 입력란에 들어갈 예상 내용이 한 줄에 수용되는 범위에서 열 너비를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-265">To reduce the amount of vertical space each row takes, expand the column width to accommodate the expected contents of the text boxes in the column on one line.</span></span>  
  
#### <a name="to-change-the-width-of-table-columns"></a><span data-ttu-id="6dde7-266">테이블 열의 너비를 변경하려면</span><span class="sxs-lookup"><span data-stu-id="6dde7-266">To change the width of table columns</span></span>  
  
1.  <span data-ttu-id="6dde7-267">**디자인** 을 클릭하여 디자인 뷰로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-267">Click **Design** to return to design view.</span></span>  
  
2.  <span data-ttu-id="6dde7-268">테이블을 클릭하여 열 핸들과 행 핸들이 테이블 위와 옆에 표시되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-268">Click the table so that column and row handles appear above and next to the table.</span></span>  
  
     <span data-ttu-id="6dde7-269">테이블 위쪽 및 옆쪽을 따라 표시되는 회색 막대는 행 및 열 핸들입니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-269">The gray bars along the top and side of the table are the column and row handles.</span></span>  
  
3.  <span data-ttu-id="6dde7-270">열 핸들 사이의 선에 커서를 두면 커서가 양방향 화살표로 바뀝니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-270">Point to the line between column handles so that the cursor changes into a double arrow.</span></span> <span data-ttu-id="6dde7-271">이 상태에서 열을 끌어 크기를 원하는 대로 조정합니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-271">Drag the columns to the size you want.</span></span> <span data-ttu-id="6dde7-272">예를 들어 제품 이름이 한 줄에 표시되도록 제품에 대한 열을 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-272">For example, expand the column for Product so that the product name displays on one line.</span></span>  
  
4.  <span data-ttu-id="6dde7-273">**실행** 을 클릭하여 보고서를 미리 봅니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-273">Click **Run** to preview your report.</span></span>  
  
##  <a name="5-add-a-report-title"></a><a name="Title"></a><span data-ttu-id="6dde7-274">5. 보고서 제목 추가</span><span class="sxs-lookup"><span data-stu-id="6dde7-274">5. Add a Report Title</span></span>  
 <span data-ttu-id="6dde7-275">보고서 제목은 보고서 맨 위에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-275">A report title appears at the top of the report.</span></span> <span data-ttu-id="6dde7-276">보고서 제목을 보고서 머리글에 배치하거나, 보고서 머리글이 사용되지 않을 경우 보고서 본문의 맨 위에 있는 입력란에 배치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-276">You can place the report title in a report header or if the report does not use one, in a text box at the top of the report body.</span></span> <span data-ttu-id="6dde7-277">이 자습서에서는 보고서 본문의 맨 위에 자동으로 표시되는 입력란을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-277">In this tutorial, you will use the text box that is automatically placed at the top of the report body.</span></span>  
  
 <span data-ttu-id="6dde7-278">글꼴 스타일, 크기 및 색을 텍스트의 각 문자나 구 단위로 다르게 적용하여 더 보기 좋게 꾸밀 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-278">The text can be further enhanced by applying different font styles, sizes, and colors to phrases and individual characters of the text.</span></span> <span data-ttu-id="6dde7-279">자세한 내용은 [입력란의 텍스트 서식 지정&#40;보고서 작성기 및 SSRS&#41;](report-design/format-text-in-a-text-box-report-builder-and-ssrs.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6dde7-279">For more information, see [Format Text in a Text Box &#40;Report Builder and SSRS&#41;](report-design/format-text-in-a-text-box-report-builder-and-ssrs.md).</span></span>  
  
#### <a name="to-add-a-report-title"></a><span data-ttu-id="6dde7-280">보고서 제목을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="6dde7-280">To add a report title</span></span>  
  
1.  <span data-ttu-id="6dde7-281">디자인 화면에서 **제목을 추가하려면 클릭하십시오.** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-281">On the design surface, click **Click to add title**.</span></span>  
  
2.  <span data-ttu-id="6dde7-282">**Product Sales**를 입력한 다음 입력란 바깥쪽을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-282">Type **Product Sales**, and then click outside the text box.</span></span>  
  
3.  <span data-ttu-id="6dde7-283">**Product Sales** 가 들어 있는 입력란을 마우스 오른쪽 단추로 클릭하고 **입력란 속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-283">Right-click the text box that contains **Product Sales** and click **Text Box Properties**.</span></span>  
  
4.  <span data-ttu-id="6dde7-284">**입력란 속성** 대화 상자에서 **글꼴**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-284">In the **Text Box Properties** dialog box, click **Font**.</span></span>  
  
5.  <span data-ttu-id="6dde7-285">**크기** 목록에서 **18pt**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-285">In the **Size** list, select **18pt**.</span></span>  
  
6.  <span data-ttu-id="6dde7-286">**색** 목록에서 **수레국화 청색**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-286">In the **Color** list, select **Cornflower Blue**.</span></span>  
  
7.  <span data-ttu-id="6dde7-287">**굵게**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-287">Select **Bold**.</span></span>  
  
8.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
##  <a name="6-save-the-report"></a><a name="Save"></a><span data-ttu-id="6dde7-288">6. 보고서 저장</span><span class="sxs-lookup"><span data-stu-id="6dde7-288">6. Save the Report</span></span>  
 <span data-ttu-id="6dde7-289">보고서 서버 또는 컴퓨터에 보고서를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-289">Save the report to a report server or your computer.</span></span> <span data-ttu-id="6dde7-290">보고서를 보고서 서버에 저장하지 않을 경우 보고서 파트 및 하위 보고서와 같은 여러 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 기능을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-290">If you do not save the report to the report server, a number of [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] features such as report parts and subreports are not available.</span></span>  
  
#### <a name="to-save-the-report-on-a-report-server"></a><span data-ttu-id="6dde7-291">보고서를 보고서 서버에 저장하려면</span><span class="sxs-lookup"><span data-stu-id="6dde7-291">To save the report on a report server</span></span>  
  
1.  <span data-ttu-id="6dde7-292">**보고서 작성기** 단추에서 다른 **이름으로 저장**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-292">From the **Report Builder** button, click **Save As**.</span></span>  
  
2.  <span data-ttu-id="6dde7-293">**최근에 사용한 사이트 및 서버**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-293">Click **Recent Sites and Servers**.</span></span>  
  
3.  <span data-ttu-id="6dde7-294">보고서를 저장할 수 있는 권한을 가진 보고서 서버의 이름을 선택하거나 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-294">Select or type the name of the report server where you have permission to save reports.</span></span>  
  
     <span data-ttu-id="6dde7-295">"보고서 서버에 연결하는 중"이라는 메시지가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-295">The message "Connecting to report server" appears.</span></span> <span data-ttu-id="6dde7-296">연결되면 보고서 서버 관리자가 보고서의 기본 위치로 지정한 보고서 폴더의 내용이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-296">When the connection is complete, you see the contents of the report folder that the report server administrator specified as the default location for reports.</span></span>  
  
4.  <span data-ttu-id="6dde7-297">**이름**에서 기본 이름을 **Product Sales**로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-297">In **Name**, replace the default name with **Product Sales**.</span></span>  
  
5.  <span data-ttu-id="6dde7-298">**저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-298">Click **Save**.</span></span>  
  
 <span data-ttu-id="6dde7-299">보고서가 보고서 서버에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-299">The report is saved to the report server.</span></span> <span data-ttu-id="6dde7-300">연결된 보고서 서버의 이름이 창 아래쪽에 있는 상태 표시줄에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-300">The name of report server that you are connected to appears in the status bar at the bottom of the window.</span></span>  
  
#### <a name="to-save-the-report-on-your-computer"></a><span data-ttu-id="6dde7-301">컴퓨터에 보고서를 저장하려면</span><span class="sxs-lookup"><span data-stu-id="6dde7-301">To save the report on your computer</span></span>  
  
1.  <span data-ttu-id="6dde7-302">**보고서 작성기** 단추에서 다른 **이름으로 저장**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-302">From the **Report Builder** button, click **Save As**.</span></span>  
  
2.  <span data-ttu-id="6dde7-303">**바탕 화면**, **내 문서**또는 **내 컴퓨터**를 클릭하여 보고서를 저장할 폴더를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-303">Click **Desktop**, **My Documents**, or **My computer**, and browse to the folder where you want to save the report.</span></span>  
  
3.  <span data-ttu-id="6dde7-304">**이름**에서 기본 이름을 **Product Sales**로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-304">In **Name**, replace the default name with **Product Sales**.</span></span>  
  
4.  <span data-ttu-id="6dde7-305">**저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-305">Click **Save**.</span></span>  
  
##  <a name="7-export-the-report"></a><a name="Export"></a><span data-ttu-id="6dde7-306">7. 보고서 내보내기</span><span class="sxs-lookup"><span data-stu-id="6dde7-306">7. Export the Report</span></span>  
 <span data-ttu-id="6dde7-307">보고서는 Microsoft Excel 및 CSV(쉼표로 구분된 값)와 같은 여러 형식으로 내보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-307">Reports can be exported to different formats such Microsoft Excel and comma separated value (CSV).</span></span> <span data-ttu-id="6dde7-308">자세한 내용은 [보고서 작성기 및 SSRS&#41;&#40;보고서 내보내기 ](report-builder/export-reports-report-builder-and-ssrs.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6dde7-308">For more information, see [Exporting Reports &#40;Report Builder and SSRS&#41;](report-builder/export-reports-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="6dde7-309">이 자습서에서는 보고서를 Excel로 내보내고 보고서에 속성을 설정하여 통합 문서 탭 이름을 사용자 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-309">In this tutorial, you will export the report to Excel and set a property on the report to provide a custom name for the workbook tab.</span></span>  
  
#### <a name="to-specify-the-workbook-tab-name"></a><span data-ttu-id="6dde7-310">통합 문서 탭 이름을 지정하려면</span><span class="sxs-lookup"><span data-stu-id="6dde7-310">To specify the workbook tab name</span></span>  
  
1.  <span data-ttu-id="6dde7-311">**디자인** 을 클릭하여 디자인 뷰로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-311">Click **Design** to return to design view.</span></span>  
  
2.  <span data-ttu-id="6dde7-312">보고서 바깥쪽 아무 곳이나 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-312">Click anywhere outside the report.</span></span>  
  
3.  <span data-ttu-id="6dde7-313">. 속성 창에서 InitialPageName 속성을 찾고 **Product Sales Excel**을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-313">.In the Properties pane, locate the InitialPageName property and type **Product Sales Excel**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="6dde7-314">속성 창이 표시 되지 않으면 리본의 보기 탭을 클릭 한 다음 **속성**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-314">If the Properties pane is not visible, click the View tab on the ribbon, and then click **Properties**.</span></span>  
  
#### <a name="to-export-a-report-to-excel"></a><span data-ttu-id="6dde7-315">보고서를 Excel로 내보내려면</span><span class="sxs-lookup"><span data-stu-id="6dde7-315">To export a report to Excel</span></span>  
  
1.  <span data-ttu-id="6dde7-316">**실행** 을 클릭하여 보고서를 미리 봅니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-316">Click **Run** to preview the report.</span></span>  
  
2.  <span data-ttu-id="6dde7-317">. 리본에서 **내보내기**를 클릭 한 다음 **Excel**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-317">.On the ribbon, click **Export**, and then click **Excel**.</span></span>  
  
     <span data-ttu-id="6dde7-318">**다른 이름으로 저장** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-318">The **Save As** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="6dde7-319">**문서** 폴더로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-319">Browse to the **Documents** folder.</span></span>  
  
4.  <span data-ttu-id="6dde7-320">**파일 이름** 입력란에 **Product Sales Excel**을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-320">In the **File name** text box, type **Product Sales Excel**.</span></span>  
  
5.  <span data-ttu-id="6dde7-321">파일 형식이 **Excel 통합 문서**인지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-321">Verify that the file type is **Excel Workbook**.</span></span>  
  
6.  <span data-ttu-id="6dde7-322">**저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-322">Click **Save**.</span></span>  
  
#### <a name="to-view-the-report-in-excel"></a><span data-ttu-id="6dde7-323">Excel에서 보고서를 보려면</span><span class="sxs-lookup"><span data-stu-id="6dde7-323">To view the report in Excel</span></span>  
  
1.  <span data-ttu-id="6dde7-324">**Documents** 폴더를 열고 **Product Sales Excel.xlsx**를 두 번 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-324">Open the **Documents** folder and double click **Product Sales Excel.xlsx**.</span></span>  
  
2.  <span data-ttu-id="6dde7-325">통합 문서 탭의 이름이 **Product Sales Excel**인지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-325">Verify that the name of the workbook tab is **Product Sales Excel**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="6dde7-326">다음 단계</span><span class="sxs-lookup"><span data-stu-id="6dde7-326">Next Steps</span></span>  
 <span data-ttu-id="6dde7-327">이것으로 기본 테이블 보고서를 만드는 방법에 대한 연습을 마칩니다.</span><span class="sxs-lookup"><span data-stu-id="6dde7-327">This concludes the walkthrough for how to create a basic table report.</span></span> <span data-ttu-id="6dde7-328">테이블에 대한 자세한 내용은 [테이블, 행렬 및 목록&#40;보고서 작성기 및 SSRS&#41;](report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6dde7-328">For more information about tables, see [Tables, Matrices, and Lists &#40;Report Builder and SSRS&#41;](report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6dde7-329">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6dde7-329">See Also</span></span>  
 <span data-ttu-id="6dde7-330">[자습서 &#40;보고서 작성기&#41;](report-builder-tutorials.md) </span><span class="sxs-lookup"><span data-stu-id="6dde7-330">[Tutorials &#40;Report Builder&#41;](report-builder-tutorials.md) </span></span>  
 [<span data-ttu-id="6dde7-331">SQL Server 2014의 보고서 작성기</span><span class="sxs-lookup"><span data-stu-id="6dde7-331">Report Builder in SQL Server 2014</span></span>](report-builder/report-builder-in-sql-server-2016.md)  
  
  
