---
title: '자습서: 자유 형식 보고서 만들기(보고서 작성기) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 87288b59-faf2-4b1d-a8e4-a7582baedf2f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 515b0d2566efa4e11216a28648338c7ec43f3950
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737839"
---
# <a name="tutorial-creating-a-free-form-report-report-builder"></a><span data-ttu-id="68575-102">자습서: 자유 형식 보고서 만들기(보고서 작성기)</span><span class="sxs-lookup"><span data-stu-id="68575-102">Tutorial: Creating a Free Form Report (Report Builder)</span></span>
  <span data-ttu-id="68575-103">이 자습서에서는 양식 편지와 유사한 SSRS 자유 형식 보고서를 만드는 방법을 배웁니다.</span><span class="sxs-lookup"><span data-stu-id="68575-103">This tutorial teaches you how to create an SSRS free form report that resembles a forms letter.</span></span> <span data-ttu-id="68575-104">입력란, 이미지 및 다른 데이터 영역이 있는 양식을 만들기 위해 보고서 항목을 정렬할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="68575-104">You can arrange report items to create a form with text boxes, images and other data regions.</span></span>

 <span data-ttu-id="68575-105">이 자습서에서 만드는 보고서는 자습서에 포함된 샘플 판매 데이터를 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-105">The report you create in this tutorial is based on sample sales data that is included in the tutorial.</span></span> <span data-ttu-id="68575-106">이 보고서에서는 정보가 지역별로 그룹화되고 지역의 판매 관리자 이름과 세부 및 요약 판매 정보가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="68575-106">The report groups information by territory and displays the name of the sales manager for the territory as well as detailed and summary sales information.</span></span> <span data-ttu-id="68575-107">목록 데이터 영역을 자유 형식 보고서의 기초로 사용한 다음, 이미지가 있는 장식 패널, 데이터가 삽입된 정적 텍스트, 세부 정보를 표시할 테이블, 요약 정보를 표시할 원형 및 세로 막대형 차트(선택 사항) 등을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-107">You will use the list data region as the foundation for the free form report, and then add a decorative panel with an image, static text with data inserted, a table to show detailed information, and optionally, pie and column charts to display summary information.</span></span>

##  <a name="what-you-will-learn"></a><a name="BackToTop"></a><span data-ttu-id="68575-108">학습 내용</span><span class="sxs-lookup"><span data-stu-id="68575-108">What You Will Learn</span></span>
 <span data-ttu-id="68575-109">이 자습서에서는 다음 작업 방법을 배웁니다.</span><span class="sxs-lookup"><span data-stu-id="68575-109">In this tutorial, you will learn how to do the following:</span></span>

-   [<span data-ttu-id="68575-110">빈 보고서, 데이터 원본 및 데이터 세트 만들기</span><span class="sxs-lookup"><span data-stu-id="68575-110">Create a Blank Report, Data Source, and Dataset</span></span>](#BlankReport)

-   [<span data-ttu-id="68575-111">목록 추가 및 구성</span><span class="sxs-lookup"><span data-stu-id="68575-111">Add and Configure a List</span></span>](#List)

-   [<span data-ttu-id="68575-112">그래픽 추가</span><span class="sxs-lookup"><span data-stu-id="68575-112">Add Graphics</span></span>](#Graphics)

-   [<span data-ttu-id="68575-113">자유 형식 텍스트 추가</span><span class="sxs-lookup"><span data-stu-id="68575-113">Add Free Form Text</span></span>](#Text)

-   [<span data-ttu-id="68575-114">테이블을 추가하여 세부 정보 표시</span><span class="sxs-lookup"><span data-stu-id="68575-114">Add a Table to Show Details</span></span>](#Table)

-   [<span data-ttu-id="68575-115">데이터 서식 지정</span><span class="sxs-lookup"><span data-stu-id="68575-115">Format Data</span></span>](#Format)

-   [<span data-ttu-id="68575-116">보고서 저장</span><span class="sxs-lookup"><span data-stu-id="68575-116">Save the Report</span></span>](#Save)

### <a name="other-optional-steps"></a><span data-ttu-id="68575-117">기타 선택적 단계</span><span class="sxs-lookup"><span data-stu-id="68575-117">Other Optional Steps</span></span>

-   [<span data-ttu-id="68575-118">선을 추가하여 보고서 영역 구분</span><span class="sxs-lookup"><span data-stu-id="68575-118">Add a Line to Separate Areas of Report</span></span>](#Line)

-   [<span data-ttu-id="68575-119">요약 데이터 시각화 추가</span><span class="sxs-lookup"><span data-stu-id="68575-119">Add Summary Data Visualization</span></span>](#Visualization)

 <span data-ttu-id="68575-120">이 자습서에 소요되는 예상 시간: 20분</span><span class="sxs-lookup"><span data-stu-id="68575-120">Estimated time to complete this tutorial: 20 minutes.</span></span>

## <a name="requirements"></a><span data-ttu-id="68575-121">요구 사항</span><span class="sxs-lookup"><span data-stu-id="68575-121">Requirements</span></span>
 <span data-ttu-id="68575-122">요구 사항에 대한 자세한 내용은 [자습서의 필수 조건&#40;보고서 작성기&#41;](../reporting-services/report-builder-tutorials.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="68575-122">For more information about requirements, see [Prerequisites for Tutorials &#40;Report Builder&#41;](../reporting-services/report-builder-tutorials.md).</span></span>

##  <a name="1-create-a-blank-report-data-source-and-dataset"></a><a name="BlankReport"></a><span data-ttu-id="68575-123">1. 빈 보고서, 데이터 원본 및 데이터 집합 만들기</span><span class="sxs-lookup"><span data-stu-id="68575-123">1. Create a Blank Report, Data Source, and Dataset</span></span>

> [!NOTE]
>  <span data-ttu-id="68575-124">이 자습서에서 쿼리는 데이터 값을 포함하므로 보고서에는 외부 데이터 원본이 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="68575-124">In this tutorial, the query contains the data values so that the report does not need an external data source.</span></span> <span data-ttu-id="68575-125">이러한 종류의 내부 데이터의 사용은 학습 목적으로는 훌륭하지만 이 방식으로 만드는 쿼리는 길어집니다.</span><span class="sxs-lookup"><span data-stu-id="68575-125">The use of this type of internal data is great for learning purposes, but the approach makes the query long.</span></span> <span data-ttu-id="68575-126">.</span><span class="sxs-lookup"><span data-stu-id="68575-126">.</span></span>

#### <a name="to-create-a-blank-report"></a><span data-ttu-id="68575-127">빈 보고서를 만들려면</span><span class="sxs-lookup"><span data-stu-id="68575-127">To create a blank report</span></span>

1.  <span data-ttu-id="68575-128">**시작**을 클릭하고 **프로그램**, **Microsoft SQL Server 2012 보고서 작성기**를 차례로 가리킨 다음 **보고서 작성기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-128">Click **Start**, point to **Programs**, point to **Microsoft SQL Server 2012 Report Builder**, and then click **Report Builder**.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="68575-129">**시작** 대화 상자가 나타나야 합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-129">The **Getting Started** dialog box should appear.</span></span> <span data-ttu-id="68575-130">이 대화 상자가 나타나지 않으면 보고서 작성기 단추에서 **새로 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-130">If it does not, from the Report Builder button, click **New**.</span></span>

2.  <span data-ttu-id="68575-131">**시작** 대화 상자의 왼쪽 창에서 **새 보고서** 가 선택되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-131">In the left pane of the **Getting Started** dialog box, verify that **New Report** is selected.</span></span>

3.  <span data-ttu-id="68575-132">오른쪽 창에서 **빈 보고서**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-132">In the right pane, click **Blank Report**.</span></span>

#### <a name="to-create-a-new-data-source"></a><span data-ttu-id="68575-133">새 데이터 원본을 만들려면</span><span class="sxs-lookup"><span data-stu-id="68575-133">To create a new data source</span></span>

1.  <span data-ttu-id="68575-134">보고서 데이터 창에서 **새로 만들기**를 클릭 한 다음 **데이터 원본**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-134">In the Report Data pane, click **New**, and then click **Data Source**.</span></span>

2.  <span data-ttu-id="68575-135">상자에 `Name` **listdatasource** 를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-135">In the `Name` box, type: **ListDataSource**</span></span>

3.  <span data-ttu-id="68575-136">**내 보고서에 포함된 연결 사용**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-136">Click **Use a connection embedded in my report**.</span></span>

4.  <span data-ttu-id="68575-137">연결 형식이 Microsoft SQL Server 인지 확인 한 다음 **연결 문자열** 상자에 \*\*Data Source = \<servername> \*\* 를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-137">Verify that the connection type is Microsoft SQL Server, and then in the **Connection string** box type: **Data Source = \<servername>**</span></span>

     <span data-ttu-id="68575-138">\<servername>예를 들어: Report001)는 SQL Server 데이터베이스 엔진 인스턴스가 설치 된 컴퓨터를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-138">\<servername>, for example Report001, specifies a computer on which an instance of the SQL Server Database Engine is installed.</span></span> <span data-ttu-id="68575-139">보고서 데이터는 SQL Server 데이터베이스에서 추출되지 않았으므로 데이터베이스 이름을 포함하지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-139">Because the report data is not extracted from a SQL Server database, you need not include the name of a database.</span></span> <span data-ttu-id="68575-140">지정된 서버의 기본 데이터베이스는 쿼리를 구문 분석하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="68575-140">The default database on the specified server is used to parse the query.</span></span>

5.  <span data-ttu-id="68575-141">**자격 증명**을 클릭하고 SQL Server 데이터베이스 엔진의 인스턴스에 연결해야 하는 자격 증명을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-141">Click **Credentials**, and enter the credentials needed to connect to the instance of the SQL Server Database Engine.</span></span>

6.  <span data-ttu-id="68575-142">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-142">Click **OK**.</span></span>

#### <a name="to-create-a-new-dataset"></a><span data-ttu-id="68575-143">새 데이터 세트를 만들려면</span><span class="sxs-lookup"><span data-stu-id="68575-143">To create a new dataset</span></span>

1.  <span data-ttu-id="68575-144">보고서 데이터 창에서 **새로 만들기**를 클릭 한 다음 **데이터 집합**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-144">In the Report Data pane, click **New**, and then click **Dataset**.</span></span>

2.  <span data-ttu-id="68575-145">상자에 `Name` Listdataset을 입력 **합니다.**</span><span class="sxs-lookup"><span data-stu-id="68575-145">In the `Name` box, type: **ListDataset.**</span></span>

3.  <span data-ttu-id="68575-146">**내 보고서에 포함된 데이터 세트 사용**을 클릭하고 데이터 원본이 **ListDataSource**인지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-146">Click **Use a dataset embedded in my report**, and verify that the data source is **ListDataSource**.</span></span>

4.  <span data-ttu-id="68575-147">**텍스트** 쿼리 유형이 선택되어 있는지 확인한 다음 **쿼리 디자이너**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-147">Verify that the **Text** query type is selected, and then click **Query Designer**.</span></span>

5.  <span data-ttu-id="68575-148">**텍스트로 편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-148">Click **Edit as Text**.</span></span>

6.  <span data-ttu-id="68575-149">쿼리 창에 다음 쿼리를 복사하여 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="68575-149">Copy and paste the following query into the query pane:</span></span>

    ```
    SELECT CAST('2009-01-05' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory, 'Accessories' as Subcategory,'Carrying Case' as Product, CAST(16996.60 AS money) AS Sales, 68 as Quantity
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory, 'Accessories' as Subcategory, 'Carrying Case' as Product, CAST(13747.25 AS money) AS Sales, 55 as Quantity
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory, 'Accessories' as Subcategory,'Carrying Case' as Product, CAST(9248.15 AS money) As Sales, 37 as Quantity
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory, 'Accessories' as Subcategory,'Tripod' as Product, CAST(1350.00 AS money) AS Sales, 18 as Quantity
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory, 'Accessories' as Subcategory,'Tripod' as Product, CAST(1800.00 AS money) AS Sales, 24 as Quantity
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory, 'Accessories' as Subcategory,'Tripod' as Product, CAST(1125.00 AS money) AS Sales, 15 as Quantity
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory, 'Accessories' as Subcategory,'Lens Adapter' as Product, CAST(1147.50 AS money) AS Sales, 17 as Quantity
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory, 'Accessories' as Subcategory,  'Lens Adapter' as Product, CAST(742.50 AS money) AS Sales, 11 as Quantity
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory, 'Accessories' as Subcategory,'Lens Adapter' as Product, CAST(1417.50 AS money) AS Sales, 21 as Quantity
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory, 'Accessories' as Subcategory, 'Carrying Case' as Product, CAST(13497.30 AS money) AS Sales, 54 as Quantity
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory, 'Accessories' as Subcategory, 'Carrying Case' as Product, CAST(11997.60 AS money) AS Sales, 48 as Quantity
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory, 'Accessories' as Subcategory, 'Carrying Case' as Product, CAST(10247.95 AS money) As Sales, 41 as Quantity
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory, 'Accessories' as Subcategory, 'Tripod' as Product, CAST(1200.00 AS money) AS Sales, 16 as Quantity
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory, 'Accessories' as Subcategory,'Tripod' as Product, CAST(2025.00 AS money) AS Sales, 27 as Quantity
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory, 'Accessories' as Subcategory,'Tripod' as Product, CAST(1425.00 AS money) AS Sales, 19 as Quantity
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory, 'Accessories' as Subcategory,'Lens Adapter' as Product, CAST(887.50 AS money) AS Sales, 13 as Quantity
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory, 'Accessories' as Subcategory, 'Lens Adapter' as Product, CAST(607.50 AS money) AS Sales, 9 as Quantity
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory, 'Accessories' as Subcategory,'Lens Adapter' as Product, CAST(1215.00 AS money) AS Sales, 18 as Quantity
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate,  'Lauren Johnson' as FullName,'Central' as Territory, 'Digital' as Subcategory,'Compact Digital' as Product, CAST(10191.00 AS money) AS Sales, 79 as Quantity
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate,  'Warren Pal' as FullName,'North' as Territory, 'Digital' as Subcategory, 'Compact Digital' as Product, CAST(8772.00 AS money) AS Sales, 68 as Quantity
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate,  'Fernando Ross' as FullName,'South' as Territory, 'Digital' as Subcategory, 'Compact Digital' as Product, CAST(10578.00 AS money) AS Sales, 82 as Quantity
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory,'Digital' as Subcategory, 'Slim Digital' as Product, CAST(7218.10 AS money) AS Sales, 38 as Quantity
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory,'Digital' as Subcategory, 'Slim Digital' as Product, CAST(8357.80 AS money) AS Sales, 44 as Quantity
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory,'Digital' as Subcategory,'Slim Digital' as Product, CAST(9307.55 AS money) AS Sales, 49 as Quantity
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate,  'Lauren Johnson' as FullName,'Central' as Territory, 'Digital' as Subcategory,'Compact Digital' as Product, CAST(3870.00 AS money) AS Sales, 30 as Quantity
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate,  'Warren Pal' as FullName,'North' as Territory, 'Digital' as Subcategory,'Compact Digital' as Product, CAST(5805.00 AS money) AS Sales, 45 as Quantity
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate,  'Fernando Ross' as FullName,'South' as Territory, 'Digital' as Subcategory, 'Compact Digital' as Product, CAST(8643.00 AS money) AS Sales, 67 as Quantity
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory, 'Digital' as Subcategory, 'Slim Digital' as Product, CAST(9877.40 AS money) AS Sales, 52 as Quantity
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory, 'Digital' as Subcategory, 'Slim Digital' as Product, CAST(12536.70 AS money) AS Sales, 66 as Quantity
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory, 'Digital' as Subcategory, 'Slim Digital' as Product, CAST(6648.25 AS money) AS Sales, 35 as Quantity
    ```

7.  <span data-ttu-id="68575-150">실행 아이콘을 클릭하여 쿼리를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-150">Click Run icon to run the query.</span></span>

     <span data-ttu-id="68575-151">쿼리 결과는 보고서에 표시할 수 있는 데이터입니다.</span><span class="sxs-lookup"><span data-stu-id="68575-151">The query results are the data available to display in your report.</span></span>

     <span data-ttu-id="68575-152">![쿼리 디자이너](../../2014/tutorials/media/tutorial-querydesigner.png "쿼리 디자이너")</span><span class="sxs-lookup"><span data-stu-id="68575-152">![Query Designer](../../2014/tutorials/media/tutorial-querydesigner.png "Query Designer")</span></span>

8.  [!INCLUDE[clickOK](../includes/clickok-md.md)]

##  <a name="2-add-and-configure-a-list"></a><a name="List"></a><span data-ttu-id="68575-153">2. 목록 추가 및 구성</span><span class="sxs-lookup"><span data-stu-id="68575-153">2. Add and Configure a List</span></span>
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]<span data-ttu-id="68575-154">에서는 테이블, 행렬 및 목록이라는 세 가지 데이터 영역 템플릿을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-154">provides three data region templates: table, matrix, and list.</span></span> <span data-ttu-id="68575-155">이러한 템플릿은 모두 테이블릭스 데이터 영역을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-155">These templates are all based on a tablix data region.</span></span>

 <span data-ttu-id="68575-156">이 자습서에서는 목록을 사용하여 회보와 유사한 보고서에 판매 지역에 대한 판매 정보를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-156">In this tutorial, you will use a list to display the sales information for sales territories in a report that resembles a newsletter.</span></span> <span data-ttu-id="68575-157">이 정보는 지역별로 그룹화됩니다.</span><span class="sxs-lookup"><span data-stu-id="68575-157">The information is grouped by territory.</span></span> <span data-ttu-id="68575-158">데이터를 지역별로 그룹화하는 새 행 그룹을 추가한 다음 기본 제공된 세부 정보 행 그룹을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-158">You will add a new row group that groups data by territory, and then delete the built-in Details row group.</span></span> <span data-ttu-id="68575-159">목록 템플릿은 자유 형식 보고서를 만드는 데 이상적입니다.</span><span class="sxs-lookup"><span data-stu-id="68575-159">The list template is ideal for creating free form reports.</span></span> <span data-ttu-id="68575-160">자세한 내용은 [목록 &#40;보고서 작성기 및 SSRS&#41;](report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="68575-160">For more information, see [Lists &#40;Report Builder and SSRS&#41;](report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md).</span></span>

> [!NOTE]
>  <span data-ttu-id="68575-161">이 보고서에서는 Letter(8.5 X11) 용지 크기와 1인치 여백을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-161">This report uses the paper size Letter (8.5 X11) and 1 inch margins.</span></span> <span data-ttu-id="68575-162">보고서 페이지의 높이가 9인치보다 크거나 너비가 6 1/2인치보다 클 경우 빈 페이지가 생성될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="68575-162">A report page taller than 9 inches or wider than 6 1/2 inches might generate blank pages.</span></span>

#### <a name="to-add-a-list"></a><span data-ttu-id="68575-163">목록을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="68575-163">To add a list</span></span>

1.  <span data-ttu-id="68575-164">리본 메뉴의 **삽입** 탭에 있는 **데이터 영역** 영역에서 **목록** 을 클릭하고 보고서 본문 안으로 목록을 끌어옵니다.</span><span class="sxs-lookup"><span data-stu-id="68575-164">On the **Insert** tab of the ribbon, in the **Data Regions** area, click **List** and then drag the list inside the report body.</span></span> <span data-ttu-id="68575-165">목록의 높이와 너비를 각각 7인치와 6.25인치로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="68575-165">Make the list 7 inches tall and 6.25 inches wide.</span></span>

2.  <span data-ttu-id="68575-166">목록 안을 클릭하고 목록 맨 위를 마우스 오른쪽 단추로 클릭한 다음 **테이블릭스 속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-166">Click inside the list, right-click the top of the list, and then click **Tablix Properties**.</span></span>

     <span data-ttu-id="68575-167">![목록 추가](../../2014/tutorials/media/tutorial-addinglistwithnumbers.png "목록 추가")</span><span class="sxs-lookup"><span data-stu-id="68575-167">![Adding list](../../2014/tutorials/media/tutorial-addinglistwithnumbers.png "Adding list")</span></span>

3.  <span data-ttu-id="68575-168">**데이터 세트 이름** 드롭다운 목록에서 **ListDataset**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-168">In the **Dataset name** drop-down list, select **ListDataset**.</span></span>

4.  [!INCLUDE[clickOK](../includes/clickok-md.md)]

5.  <span data-ttu-id="68575-169">목록 안을 마우스 오른쪽 단추로 클릭한 다음 **사각형 속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-169">Right-click inside the list, and then click **Rectangle Properties**.</span></span>

     <span data-ttu-id="68575-170">![사각형 속성 명령](../../2014/tutorials/media/tutorial-rectanglepropertiescommand.png "사각형 속성 명령")</span><span class="sxs-lookup"><span data-stu-id="68575-170">![Rectangle Properties command](../../2014/tutorials/media/tutorial-rectanglepropertiescommand.png "Rectangle Properties command")</span></span>

6.  <span data-ttu-id="68575-171">**일반** 탭에서 **뒤에 페이지 나누기 추가** 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-171">On the **General** tab, select the **Add a page break after** checkbox.</span></span>

7.  [!INCLUDE[clickOK](../includes/clickok-md.md)]

#### <a name="to-add-a-new-row-group-and-to-delete-the-details-group"></a><span data-ttu-id="68575-172">새 행 그룹을 추가하고 세부 정보 그룹을 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="68575-172">To add a new row group and to delete the Details group</span></span>

1.  <span data-ttu-id="68575-173">행 그룹 창에서 세부 정보 그룹을 마우스 오른쪽 단추로 클릭하고 **그룹 추가**를 가리킨 다음 **부모 그룹**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-173">In the Row Groups pane, right-click the Details group, point to **Add Group**, and then click **Parent Group**.</span></span>

     <span data-ttu-id="68575-174">![상위 그룹 명령](../../2014/tutorials/media/tutorial-parentgroupcommand.png "상위 그룹 명령")</span><span class="sxs-lookup"><span data-stu-id="68575-174">![Parent Group command](../../2014/tutorials/media/tutorial-parentgroupcommand.png "Parent Group command")</span></span>

2.  <span data-ttu-id="68575-175">드롭다운 목록에서 `[Territory].`를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-175">In the drop-down list, select `[Territory].`</span></span>

3.  [!INCLUDE[clickOK](../includes/clickok-md.md)]

     <span data-ttu-id="68575-176">열이 목록에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="68575-176">A column is added to the list.</span></span> <span data-ttu-id="68575-177">이 열에는 `[Territory].` 셀이 있습니다</span><span class="sxs-lookup"><span data-stu-id="68575-177">The column contains the cell `[Territory].`</span></span>

4.  <span data-ttu-id="68575-178">목록에서 Territory 열을 마우스 오른쪽 단추로 클릭한 다음 **열 삭제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-178">Right-click the Territory column in the list, and then click **Delete Columns**.</span></span>

     <span data-ttu-id="68575-179">![열 삭제](../../2014/tutorials/media/tutorial-deletecolumnscommand.png "열 삭제")</span><span class="sxs-lookup"><span data-stu-id="68575-179">![Delete columns](../../2014/tutorials/media/tutorial-deletecolumnscommand.png "Delete columns")</span></span>

5.  <span data-ttu-id="68575-180">**열만 삭제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-180">Click **Delete Columns only**.</span></span>

     <span data-ttu-id="68575-181">![열 삭제 대화 상자](../../2014/tutorials/media/tutorial-deletecolumnsdialog.png "열 삭제 대화 상자")</span><span class="sxs-lookup"><span data-stu-id="68575-181">![Delete Columns dialog box](../../2014/tutorials/media/tutorial-deletecolumnsdialog.png "Delete Columns dialog box")</span></span>

6.  <span data-ttu-id="68575-182">행 그룹 창에서 **세부 정보** 그룹을 마우스 오른쪽 단추로 클릭한 다음 **그룹 삭제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-182">In the Row Groups pane, right-click the **Details** group, and then click **Delete Group**.</span></span>

     <span data-ttu-id="68575-183">![세부 정보 그룹 삭제](../../2014/tutorials/media/tutorial-deletedetailsgroup.png "세부 정보 그룹 삭제")</span><span class="sxs-lookup"><span data-stu-id="68575-183">![Delete Details Group](../../2014/tutorials/media/tutorial-deletedetailsgroup.png "Delete Details Group")</span></span>

7.  <span data-ttu-id="68575-184">**그룹만 삭제**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-184">Click **Delete Group only**.</span></span>

8.  [!INCLUDE[clickOK](../includes/clickok-md.md)]

##  <a name="3-add-graphics"></a><a name="Graphics"></a><span data-ttu-id="68575-185">3. 그래픽 추가</span><span class="sxs-lookup"><span data-stu-id="68575-185">3. Add Graphics</span></span>
 <span data-ttu-id="68575-186">목록 데이터 영역을 사용할 경우의 장점 중 하나는 테이블 형식 레이아웃으로 제한하지 않고 사각형 및 입력란과 같은 보고서 항목을 어느 곳에나 추가할 수 있다는 점입니다.</span><span class="sxs-lookup"><span data-stu-id="68575-186">One of the advantages of using a list data region is that you can add report items such as rectangles and text boxes anywhere, instead of being limited to a tabular layout.</span></span> <span data-ttu-id="68575-187">색으로 채워진 사각형과 같은 그래픽을 추가하여 보고서의 모양을 돋보이게 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="68575-187">You will enhance the appearance of the report by adding a graphic (a rectangle filled with a color).</span></span>

#### <a name="to-add-graphic-elements-to-the-report"></a><span data-ttu-id="68575-188">보고서에 그래픽 요소를 추가하려면</span><span class="sxs-lookup"><span data-stu-id="68575-188">To add graphic elements to the report</span></span>

1.  <span data-ttu-id="68575-189">리본의 **삽입** 탭에서 **사각형**을 클릭 한 다음 목록의 왼쪽 위 모퉁이로 사각형을 끕니다.</span><span class="sxs-lookup"><span data-stu-id="68575-189">On the **Insert** tab of the ribbon, click **Rectangle**,and then drag a rectangle to the upper left corner of the list.</span></span> <span data-ttu-id="68575-190">사각형의 높이와 너비를 각각 7인치와 1인치로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="68575-190">Make the rectangle 7 inches tall and 1 inch wide.</span></span>

2.  <span data-ttu-id="68575-191">사각형을 마우스 오른쪽 단추로 클릭한 다음 **사각형 속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-191">Right-click the rectangle, and then click **Rectangle Properties**.</span></span>

3.  <span data-ttu-id="68575-192">**채우기** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-192">Click the **Fill** tab.</span></span>

4.  <span data-ttu-id="68575-193">**채우기 색** 드롭다운 목록에서 **다른 색**을 클릭한 다음 **진한 회색** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-193">In the **Fill color** drop-down list, click **More Colors**, and then select the **DarkGray** color.</span></span>

     <span data-ttu-id="68575-194">![채우기 색 선택](../../2014/tutorials/media/tutorial-selectfillcolorwithnumbers.png "채우기 색 선택")</span><span class="sxs-lookup"><span data-stu-id="68575-194">![Select fill color](../../2014/tutorials/media/tutorial-selectfillcolorwithnumbers.png "Select fill color")</span></span>

5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]

6.  <span data-ttu-id="68575-195">**실행** 을 클릭하여 보고서를 미리 봅니다.</span><span class="sxs-lookup"><span data-stu-id="68575-195">Click **Run** to preview the report.</span></span>

 <span data-ttu-id="68575-196">이제 보고서의 왼쪽에 진한 회색 사각형으로 구성된 세로 그래픽이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="68575-196">The left side of the report now has vertical graphic that consists of a dark gray rectangle.</span></span>

##  <a name="4-add-free-form-text"></a><a name="Text"></a><span data-ttu-id="68575-197">4. 자유 형식 텍스트 추가</span><span class="sxs-lookup"><span data-stu-id="68575-197">4. Add Free Form Text</span></span>
 <span data-ttu-id="68575-198">입력란에는 각 보고서 페이지와 데이터 필드에서 반복되는 정적 텍스트가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="68575-198">A text box contains static text that is repeated on each report page as well as data fields.</span></span>

#### <a name="to-add-text-to-the-report"></a><span data-ttu-id="68575-199">보고서에 텍스트를 추가하려면</span><span class="sxs-lookup"><span data-stu-id="68575-199">To add text to the report</span></span>

1.  <span data-ttu-id="68575-200">**디자인** 을 클릭하여 디자인 뷰로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="68575-200">Click **Design** to return to design view.</span></span>

2.  <span data-ttu-id="68575-201">리본 메뉴의 **삽입** 탭에서 **입력란**을 클릭한 다음 입력란을 목록의 왼쪽 상단으로 끌어 이전에 추가한 사각형 안에 배치합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-201">On the **Insert** tab of the ribbon, click **Text Box**, and then drag a text box to the upper left corner of the list, but inside of the rectangle you added previously.</span></span> <span data-ttu-id="68575-202">입력란의 높이와 너비를 각각 3인치와 5인치로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="68575-202">Make the text box about 3 inches tall and 5 inches wide.</span></span>

3.  <span data-ttu-id="68575-203">입력란의 위쪽에 커서를 놓고 **Newsletter for** 를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-203">Place the cursor in the upper part of the text box, and then type: **Newsletter for** .</span></span>

     <span data-ttu-id="68575-204">![뉴스레터 제목 텍스트 추가](../../2014/tutorials/media/tutorial-newsletterfor.png "뉴스레터 제목 텍스트 추가")</span><span class="sxs-lookup"><span data-stu-id="68575-204">![Add newsletter heading text](../../2014/tutorials/media/tutorial-newsletterfor.png "Add newsletter heading text")</span></span>

    > [!NOTE]
    >  <span data-ttu-id="68575-205">"for" 단어 뒤에 추가 공백을 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-205">Be sure to include the extra space after the word "for".</span></span> <span data-ttu-id="68575-206">이 공백은 텍스트와 다음 단계에서 추가할 필드를 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-206">The space separates the text and the field that you will add in the next step.</span></span>

4.  <span data-ttu-id="68575-207">Territory 필드를 입력란으로 끌어 3단계에서 입력한 텍스트 뒤에 배치합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-207">Drag the Territory field to the text box and place it after the text you typed in step 3.</span></span>

     <span data-ttu-id="68575-208">![영역 필드 추가](../../2014/tutorials/media/tutorial-addterritorialfield.png "영역 필드 추가")</span><span class="sxs-lookup"><span data-stu-id="68575-208">![Add Territorial field](../../2014/tutorials/media/tutorial-addterritorialfield.png "Add Territorial field")</span></span>

5.  <span data-ttu-id="68575-209">모든 텍스트를 선택하고 마우스 오른쪽 단추를 클릭한 다음 **텍스트 속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-209">Select all text, right-click, and then click **Text Properties**.</span></span>

6.  <span data-ttu-id="68575-210">**글꼴** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-210">Click the **Font** tab.</span></span>

7.  <span data-ttu-id="68575-211">**글꼴** 목록에서 **Times New Roman**을 선택하고 **크기** 에서 **20pt**를 선택한 다음 **색** 에서 **빨강**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-211">In the **Font** list, select **Times New Roman**; in **Size** select **20 pt**, in **Color** select **Red**.</span></span>

     <span data-ttu-id="68575-212">![텍스트 속성](../../2014/tutorials/media/tutorial-textpropertieswithnumbers.png "텍스트 속성")</span><span class="sxs-lookup"><span data-stu-id="68575-212">![Text Properties](../../2014/tutorials/media/tutorial-textpropertieswithnumbers.png "Text Properties")</span></span>

8.  [!INCLUDE[clickOK](../includes/clickok-md.md)]

9. <span data-ttu-id="68575-213">3단계에서 입력한 텍스트 아래에 커서를 놓고 **Hello** 를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-213">Place the cursor below the text you typed in step 3 and type: **Hello** .</span></span>

    > [!NOTE]
    >  <span data-ttu-id="68575-214">"Hello" 단어 뒤에 추가 공백을 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-214">Be sure to include the extra space after the word "Hello".</span></span> <span data-ttu-id="68575-215">이 공백은 텍스트와 다음 단계에서 추가할 필드를 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-215">The space separates the text and the field that you will add in the next step.</span></span>

10. <span data-ttu-id="68575-216">FullName 필드를 입력란으로 끌어 9단계에서 입력한 텍스트 뒤에 배치한 다음 쉼표(,)를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-216">Drag the FullName field to the text box and place it after the text you typed in step 9, and then type a comma (,).</span></span>

     <span data-ttu-id="68575-217">![전체 이름 필드 추가](../../2014/tutorials/media/tutorial-addfullnamefield.png "전체 이름 필드 추가")</span><span class="sxs-lookup"><span data-stu-id="68575-217">![Add Full Name field](../../2014/tutorials/media/tutorial-addfullnamefield.png "Add Full Name field")</span></span>

11. <span data-ttu-id="68575-218">9-10단계에서 추가한 텍스트를 선택하고 마우스 오른쪽 단추를 클릭한 다음 **텍스트 속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-218">Select the text you added in steps 9 and 10, right-click, and then click **Text Properties**.</span></span>

12. <span data-ttu-id="68575-219">**글꼴** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-219">Click the **Font** tab.</span></span>

13. <span data-ttu-id="68575-220">**글꼴** 목록에서 **Times New Roman**을 선택하고 **크기** 에서 **16pt**를 선택한 다음 **색** 에서 **검정** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-220">In the **Font** list, select **Times New Roman**; in **Size** select **16 pt**, in **Color** select **Black** color.</span></span>

14. [!INCLUDE[clickOK](../includes/clickok-md.md)]

15. <span data-ttu-id="68575-221">9-13단계에서 추가한 텍스트 아래에 커서를 놓고 다음의 예제 텍스트를 복사하여 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="68575-221">Place the cursor below the text you added in steps 9 through 13, and then copy and paste the following "greeked" text:</span></span>

    ```
    Lorem ipsum dolor sit amet, consectetur adipiscing elit. Proin sed dolor in ipsum pulvinar egestas. Sed sed lacus at leo ornare ultricies. Vivamus velit risus, euismod nec sodales gravida, gravida in dui. Etiam ullamcorper elit vitae justo fermentum ut ullamcorper augue sodales. Ut placerat, nisl quis feugiat adipiscing, nibh est aliquet est, mollis faucibus mauris lectus quis arcu. In mollis tincidunt lacinia. In vitae erat ut lorem tincidunt luctus. Curabitur et magna nunc, sit amet adipiscing nisi. Nulla rhoncus elementum orci nec tincidunt. Aliquam imperdiet cursus erat vel tincidunt. Donec et neque ac urna rutrum sodales. In id purus et nisl dignissim dapibus. Sed rhoncus metus at felis feugiat eu tempor dolor vehicula. Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nullam faucibus consectetur diam eu pellentesque. 
    Nulla facilisi. Proin ligula enim, porta ut tincidunt id, adipiscing sit amet eros. Ut purus sem, bibendum et vulputate sit amet, facilisis eget magna. Sed aliquam erat non erat eleifend hendrerit. Ut a ligula est, sit amet eleifend enim. Ut et nisl enim, sit amet adipiscing augue. Vivamus eu arcu ac libero posuere elementum. Integer condimentum bibendum venenatis. Integer odio tellus, feugiat in pellentesque semper, interdum nec sem. Sed cursus euismod sem, ut elementum sapien placerat vel. 
    ```

16. <span data-ttu-id="68575-222">15단계에서 추가한 텍스트를 선택하고 마우스 오른쪽 단추를 클릭한 다음 **텍스트 속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-222">Select the text you added in steps 15, right-click, and then click **Text Properties**.</span></span>

17. <span data-ttu-id="68575-223">**글꼴** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-223">Click the **Font** tab.</span></span>

18. <span data-ttu-id="68575-224">**글꼴** 목록에서 **Arial**을 선택하고 **크기** 에서 **10pt**를 선택한 다음 **색상** 에서 **검정**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-224">In the **Font** list, select **Arial**; in **Size** select **10 pt**, in **Color** select **Black**.</span></span>

19. [!INCLUDE[clickOK](../includes/clickok-md.md)]

     <span data-ttu-id="68575-225">![뉴스레터 텍스트 추가](../../2014/tutorials/media/tutorial-newslettertext.png "뉴스레터 텍스트 추가")</span><span class="sxs-lookup"><span data-stu-id="68575-225">![Add newsletter text](../../2014/tutorials/media/tutorial-newslettertext.png "Add newsletter text")</span></span>

20. <span data-ttu-id="68575-226">15단계에서 붙여 넣은 텍스트 아래에 커서를 놓고 **Congratulations on your total sales of** 를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-226">Place the cursor below the text you pasted in step 15, and then type: **Congratulations on your total sales of** .</span></span>

    > [!NOTE]
    >  <span data-ttu-id="68575-227">"of" 단어 뒤에 추가 공백을 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-227">Be sure to include the extra space after the word "of".</span></span> <span data-ttu-id="68575-228">이 공백은 텍스트와 다음 단계에서 추가할 필드를 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-228">The space separates the text and the field that you will add in the next step.</span></span>

21. <span data-ttu-id="68575-229">Sales 필드를 입력란으로 끌어 20단계에서 입력한 텍스트 뒤에 배치한 다음 느낌표(!)를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-229">Drag the Sales field to the text box, place it after the text you typed in step 20, and then type an exclamation mark (!).</span></span>

22. <span data-ttu-id="68575-230">Sales 필드를 강조 표시 하 고 필드를 마우스 오른쪽 단추로 클릭 한 다음 **식**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-230">Highlight the Sales field, right-click the field, and then click **Expression**.</span></span>

23. <span data-ttu-id="68575-231">식 상자에서 다음과 같이 Sum 함수를 포함하도록 식을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-231">In the expression box, change the expression to include the Sum function as follows:</span></span>

    ```
    =Sum(Fields!Sales.value)
    ```

24. [!INCLUDE[clickOK](../includes/clickok-md.md)]

     <span data-ttu-id="68575-232">![판매량 필드에 식 추가](../../2014/tutorials/media/tutorial-addexpressiontosalesfield.png "판매량 필드에 식 추가")</span><span class="sxs-lookup"><span data-stu-id="68575-232">![Add an expression to sales field](../../2014/tutorials/media/tutorial-addexpressiontosalesfield.png "Add an expression to sales field")</span></span>

25. <span data-ttu-id="68575-233">20-23단계에서 추가한 텍스트를 선택하고 마우스 오른쪽 단추를 클릭한 다음 **텍스트 속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-233">Select the text you added in steps 20 through 23, right-click, and then click **Text Properties**.</span></span>

26. <span data-ttu-id="68575-234">**글꼴** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-234">Click the **Font** tab.</span></span>

27. <span data-ttu-id="68575-235">**글꼴** 목록에서 **Times New Roman**을 선택하고 **크기** 에서 **16pt**를 선택한 다음 **색** 에서 **빨강**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-235">In the **Font** list, select **Times New Roman**; in **Size** select **16 pt**, in **Color** select **Red**.</span></span>

28. [!INCLUDE[clickOK](../includes/clickok-md.md)]

29. <span data-ttu-id="68575-236">`[Sum(Sales)]` 를 선택하고 **홈** 탭의 **숫자** 그룹에서 **통화** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-236">Select `[Sum(Sales)]` and on the **Home** tab, in the **Number** group, click the **Currency** button.</span></span>

     <span data-ttu-id="68575-237">![통화 기호 추가](../../2014/tutorials/media/tutorial-addcurrencysymbol.png "통화 기호 추가")</span><span class="sxs-lookup"><span data-stu-id="68575-237">![Add currency symbol](../../2014/tutorials/media/tutorial-addcurrencysymbol.png "Add currency symbol")</span></span>

30. <span data-ttu-id="68575-238">"제목을 추가하려면 클릭하십시오." 텍스트가 있는 입력란을 마우스 오른쪽 단추로 클릭한 다음 **삭제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-238">Right-click the text box with the "Click to add title" text, and then click **Delete**.</span></span>

31. <span data-ttu-id="68575-239">목록 상자를 선택하고 화살표 키를 사용하여 페이지의 위쪽으로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-239">Select the list box and using the arrow keys, move it to the top of the page.</span></span>

32. <span data-ttu-id="68575-240">**실행** 을 클릭하여 보고서를 미리 봅니다.</span><span class="sxs-lookup"><span data-stu-id="68575-240">Click **Run** to preview the report.</span></span>

 <span data-ttu-id="68575-241">보고서에 정적 테스트가 표시되고 각 보고서 페이지에 지역과 관련된 데이터가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="68575-241">The report displays static text and each report page includes data that pertains to a territory.</span></span> <span data-ttu-id="68575-242">Sales의 서식이 통화로 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="68575-242">Sales are formatted as currency.</span></span>

 <span data-ttu-id="68575-243">![뉴스레터 미리 보기](../../2014/tutorials/media/tutorial-newsletters.png "뉴스레터 미리 보기")</span><span class="sxs-lookup"><span data-stu-id="68575-243">![Preview of Newsletter](../../2014/tutorials/media/tutorial-newsletters.png "Preview of Newsletter")</span></span>

##  <a name="5-add-a-table-to-show-sales-details"></a><a name="Table"></a><span data-ttu-id="68575-244">5. 테이블을 추가 하 여 판매 세부 정보 표시</span><span class="sxs-lookup"><span data-stu-id="68575-244">5. Add a Table to Show Sales Details</span></span>
 <span data-ttu-id="68575-245">새 테이블 및 행렬 마법사를 사용하여 자유 형식 보고서에 테이블을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-245">Use the New Table and Matrix Wizard to add a table to the free form report.</span></span> <span data-ttu-id="68575-246">마법사를 완료한 후에는 합계를 표시할 행을 수동으로 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-246">After you complete the wizard, you will manually add a row for totals.</span></span>

#### <a name="to-add-a-table"></a><span data-ttu-id="68575-247">테이블을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="68575-247">To add a table</span></span>

1.  <span data-ttu-id="68575-248">리본 메뉴의 **삽입** 탭에 있는 **데이터 영역** 영역에서 **테이블**을 클릭한 다음 **테이블 마법사**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-248">On the **Insert** tab of the ribbon, in the **Data Regions** area, click **Table**, and then click **Table Wizard**.</span></span>

2.  <span data-ttu-id="68575-249">데이터 세트 선택 페이지에서 **ListDataset**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-249">On the Choose a dataset page, click **ListDataset**.</span></span>

3.  <span data-ttu-id="68575-250">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-250">Click **Next**.</span></span>

4.  <span data-ttu-id="68575-251">**필드 정렬** 페이지에서 **사용 가능한 필드** 의 Product 필드를 **값**으로 끌어옵니다.</span><span class="sxs-lookup"><span data-stu-id="68575-251">On the **Arrange fields** page, drag the Product field from **Available fields** to **Values.**</span></span>

5.  <span data-ttu-id="68575-252">SalesDate, Quantity 및 Sales에 대해 4단계를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-252">Repeat step 4, for SalesDate, Quantity, and Sales.</span></span> <span data-ttu-id="68575-253">SalesDate는 Product 아래에 배치하고, Quantity는 SalesDate 아래에 배치하고, Sales는SalesDate 아래에 배치합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-253">Place SalesDate below Product, Quantity below SalesDate, and Sales below SalesDate.</span></span>

6.  <span data-ttu-id="68575-254">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-254">Click **Next**.</span></span>

7.  <span data-ttu-id="68575-255">**레이아웃 선택** 페이지에서 테이블의 레이아웃을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-255">On the **Choose the layout** page, view the layout of the table.</span></span>

     <span data-ttu-id="68575-256">이 테이블은 매우 간단하여</span><span class="sxs-lookup"><span data-stu-id="68575-256">The table is very simple.</span></span> <span data-ttu-id="68575-257">5개의 열로 구성되며 행 또는 열 그룹이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="68575-257">It consists of five columns and has no row or column groups.</span></span> <span data-ttu-id="68575-258">그룹이 없기 때문에 그룹과 관련된 레이아웃 옵션은 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="68575-258">Because it has no groups, the layout options related to groups, are not available.</span></span> <span data-ttu-id="68575-259">이 자습서의 뒷부분에서 합계를 포함하도록 테이블을 수동으로 업데이트할 것입니다.</span><span class="sxs-lookup"><span data-stu-id="68575-259">You will manually update the table to include a total later in the tutorial.</span></span>

8.  <span data-ttu-id="68575-260">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-260">Click **Next**.</span></span>

9. <span data-ttu-id="68575-261">**스타일 선택** 페이지의 **스타일** 창에서 **Slate**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-261">On the **Choose a Style** page, in the **Styles** pane, select **Slate**.</span></span>

10. <span data-ttu-id="68575-262">**Finish**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-262">Click **Finish**.</span></span>

11. <span data-ttu-id="68575-263">테이블을 4단원에서 추가한 입력란 아래로 끌어옵니다.</span><span class="sxs-lookup"><span data-stu-id="68575-263">Drag the table to below the text box that you added in lesson 4.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="68575-264">테이블이 목록 내에 표시되는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-264">Make sure the table is inside the list.</span></span>

12. <span data-ttu-id="68575-265">테이블이 선택되었는지 확인한 다음 행 그룹 창에서 세부 정보를 마우스 오른쪽 단추로 클릭하고 **합계 추가**를 가리킨 다음 **뒤**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-265">Confirmed that the table is selected, then in the Row Group pane right-click Details, point to **Add Total**, and then click **After**.</span></span>

     <span data-ttu-id="68575-266">![보고서 합계 추가](../../2014/tutorials/media/tutorial-addtotal.png "보고서 합계 추가")</span><span class="sxs-lookup"><span data-stu-id="68575-266">![Add report total](../../2014/tutorials/media/tutorial-addtotal.png "Add report total")</span></span>

13. <span data-ttu-id="68575-267">**실행** 을 클릭하여 보고서를 미리 봅니다.</span><span class="sxs-lookup"><span data-stu-id="68575-267">Click **Run** to preview the report.</span></span>

 <span data-ttu-id="68575-268">보고서에 판매 세부 정보 및 합계가 포함된 테이블이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="68575-268">The report displays a table with sales details and totals.</span></span>

 <span data-ttu-id="68575-269">![보고서의 판매량 합계](../../2014/tutorials/media/tutorial-reportsalestotals.png "보고서의 판매량 합계")</span><span class="sxs-lookup"><span data-stu-id="68575-269">![Sales totals in report](../../2014/tutorials/media/tutorial-reportsalestotals.png "Sales totals in report")</span></span>

##  <a name="6-format-data"></a><a name="Format"></a><span data-ttu-id="68575-270">6. 데이터 서식 지정</span><span class="sxs-lookup"><span data-stu-id="68575-270">6. Format Data</span></span>
 <span data-ttu-id="68575-271">숫자 데이터의 서식을 통화로 지정하고 날짜의 서식을 날짜와 시간으로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-271">Format numeric data as currency and dates as day and time only.</span></span>

#### <a name="to-format-fields-table"></a><span data-ttu-id="68575-272">필드 테이블의 형식을 지정하려면</span><span class="sxs-lookup"><span data-stu-id="68575-272">To format fields table</span></span>

1.  <span data-ttu-id="68575-273">디자인 **을 클릭 하 여 디자인** 뷰로 전환 합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-273">Click **Design** to switch to design view.</span></span>

2.  <span data-ttu-id="68575-274">`[Sum(SalesSales)]` 이 들어 있는 테이블 셀을 클릭하고 **홈** 탭의 **숫자** 그룹에서 **통화** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-274">Click the table cells that contain `[Sum(SalesSales)]` and on the **Home** tab, in the **Number** group, click the **Currency** button.</span></span>

     <span data-ttu-id="68575-275">![판매 합계에 통화 기호 추가](../../2014/tutorials/media/tutorial-sumsales-currencysymbol.png "판매 합계에 통화 기호 추가")</span><span class="sxs-lookup"><span data-stu-id="68575-275">![Add currency symbol to sum sales](../../2014/tutorials/media/tutorial-sumsales-currencysymbol.png "Add currency symbol to sum sales")</span></span>

3.  <span data-ttu-id="68575-276">`[SalesDate]` 가 들어 있는 셀을 클릭하고 **숫자** 그룹의 드롭다운 목록에서 **날짜**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-276">Click the cell that contains `[SalesDate]` and in the **Number** group, from the drop-down list, select **Date**.</span></span>

4.  <span data-ttu-id="68575-277">**실행** 을 클릭하여 보고서를 미리 봅니다.</span><span class="sxs-lookup"><span data-stu-id="68575-277">Click **Run** to preview the report.</span></span>

 <span data-ttu-id="68575-278">이제 보고서에 서식이 지정된 데이터가 표시되므로 보다 쉽게 읽을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="68575-278">The report now displays formatted data and is easier to read.</span></span>

 <span data-ttu-id="68575-279">![보고서의 판매량 합계 서식 지정](../../2014/tutorials/media/tutorial-reportsalestotals-formatted.png "보고서의 판매량 합계 서식 지정")</span><span class="sxs-lookup"><span data-stu-id="68575-279">![Format sales totals in report](../../2014/tutorials/media/tutorial-reportsalestotals-formatted.png "Format sales totals in report")</span></span>

##  <a name="7-save-the-report"></a><a name="Save"></a><span data-ttu-id="68575-280">7. 보고서 저장</span><span class="sxs-lookup"><span data-stu-id="68575-280">7. Save the Report</span></span>
 <span data-ttu-id="68575-281">보고서를 보고서 서버, SharePoint 라이브러리 또는 컴퓨터에 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="68575-281">You can save reports to a report server, SharePoint library, or your computer.</span></span> <span data-ttu-id="68575-282">보고서를 실행하고 **내보내기** 메뉴에서 형식을 선택하여 보고서를 Word 및 PDF 등의 다양한 형식으로 내보낼 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="68575-282">You can also export the report to a variety of formats such as Word and PDF, by running the report and selecting the format from the **Export** menu.</span></span>

 <span data-ttu-id="68575-283">이 자습서에서는 보고서를 보고서 서버에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-283">In this tutorial, save the report to a report server.</span></span> <span data-ttu-id="68575-284">보고서 서버에 액세스할 수 없는 경우에는 보고서를 컴퓨터에 저장하십시오.</span><span class="sxs-lookup"><span data-stu-id="68575-284">If you do not have access to a report server, save the report to your computer.</span></span>

#### <a name="to-save-the-report-on-a-report-server"></a><span data-ttu-id="68575-285">보고서를 보고서 서버에 저장하려면</span><span class="sxs-lookup"><span data-stu-id="68575-285">To save the report on a report server</span></span>

1.  <span data-ttu-id="68575-286">**보고서 작성기** 단추에서 다른 **이름으로 저장**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-286">From the **Report Builder** button, click **Save As**.</span></span>

2.  <span data-ttu-id="68575-287">**최근에 사용한 사이트 및 서버**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-287">Click **Recent Sites and Servers**.</span></span>

3.  <span data-ttu-id="68575-288">보고서를 저장할 수 있는 권한을 가진 보고서 서버의 이름을 선택하거나 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-288">Select or type the name of the report server where you have permission to save reports.</span></span>

     <span data-ttu-id="68575-289">"보고서 서버에 연결하는 중"이라는 메시지가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="68575-289">The message "Connecting to report server" appears.</span></span> <span data-ttu-id="68575-290">연결되면 보고서 서버 관리자가 보고서의 기본 위치로 지정한 보고서 폴더의 내용이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="68575-290">When the connection is complete, you see the contents of the report folder that the report server administrator specified as the default location for reports.</span></span>

4.  <span data-ttu-id="68575-291">에서 `Name` 기본 이름을 **Salesinformationbyterritory**로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="68575-291">In `Name`, replace the default name with **SalesInformationByTerritory**.</span></span>

5.  <span data-ttu-id="68575-292">**저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-292">Click **Save**.</span></span>

 <span data-ttu-id="68575-293">보고서가 보고서 서버에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="68575-293">The report is saved to the report server.</span></span> <span data-ttu-id="68575-294">연결된 보고서 서버의 이름이 창 아래쪽에 있는 상태 표시줄에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="68575-294">The name of report server that you are connected to appears in the status bar at the bottom of the window.</span></span>

#### <a name="to-save-the-report-on-your-computer"></a><span data-ttu-id="68575-295">컴퓨터에 보고서를 저장하려면</span><span class="sxs-lookup"><span data-stu-id="68575-295">To save the report on your computer</span></span>

1.  <span data-ttu-id="68575-296">**보고서 작성기** 단추에서 다른 **이름으로 저장**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-296">From the **Report Builder** button, click **Save As**.</span></span>

2.  <span data-ttu-id="68575-297">**바탕 화면**, **내 문서**또는 **내 컴퓨터**를 클릭한 다음 보고서를 저장할 폴더를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="68575-297">Click **Desktop**, **My Documents**, or **My computer**, and then browse to the folder where you want to save the report.</span></span>

3.  <span data-ttu-id="68575-298">에서 `Name` 기본 이름을 **Salesinformationbyterritory**로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="68575-298">In `Name`, replace the default name with **SalesInformationByTerritory**.</span></span>

4.  <span data-ttu-id="68575-299">**저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-299">Click **Save**.</span></span>

##  <a name="8-optional-add-a-line-to-separate-areas-of-the-report"></a><a name="Line"></a><span data-ttu-id="68575-300">8. (선택 사항) 선을 추가 하 여 보고서 영역 구분</span><span class="sxs-lookup"><span data-stu-id="68575-300">8. (Optional) Add a Line to Separate Areas of the Report</span></span>
 <span data-ttu-id="68575-301">선을 추가하여 보고서의 편집 영역과 세부 정보 영역을 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-301">Add a line to separate the editorial and details areas of the report.</span></span>

#### <a name="to-add-a-line"></a><span data-ttu-id="68575-302">선을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="68575-302">To add a line</span></span>

1.  <span data-ttu-id="68575-303">**디자인** 을 클릭하여 디자인 뷰로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="68575-303">Click **Design** to return to design view.</span></span>

2.  <span data-ttu-id="68575-304">리본 메뉴의 **삽입** 탭에 있는 **보고서 항목** 영역에서 **선**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-304">On the **Insert** tab of the ribbon, in the **Report Items** area, click **Line.**</span></span>

3.  <span data-ttu-id="68575-305">4단원에서 추가한 자유 형식 입력란 아래로 선을 끌어옵니다.</span><span class="sxs-lookup"><span data-stu-id="68575-305">Draw a line below the free form text box you added in lesson 4.</span></span>

4.  <span data-ttu-id="68575-306">선을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-306">Click the line.</span></span>

5.  <span data-ttu-id="68575-307">**홈** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-307">Click the **Home** tab.</span></span>

6.  <span data-ttu-id="68575-308">**테두리** 영역에서 너비를 **4 1/2** pt로 선택하고 색을 **빨강**으로 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-308">In the **Border** area, for width select **4 1/2** pt and for color, for color select **Red**.</span></span>

     <span data-ttu-id="68575-309">![보고서에 선 추가](../../2014/tutorials/media/tutorial-reportwithline.png "보고서에 선 추가")</span><span class="sxs-lookup"><span data-stu-id="68575-309">![Add line to report](../../2014/tutorials/media/tutorial-reportwithline.png "Add line to report")</span></span>

##  <a name="9-optional-add-summary-data-visualization"></a><a name="Visualization"></a><span data-ttu-id="68575-310">9. (선택 사항) 요약 데이터 시각화 추가</span><span class="sxs-lookup"><span data-stu-id="68575-310">9. (Optional) Add Summary Data Visualization</span></span>
 <span data-ttu-id="68575-311">사각형은 보고서가 렌더링되는 방식을 제어하는 데 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-311">Rectangles help you control how the report renders.</span></span> <span data-ttu-id="68575-312">원형 및 세로 막대형 차트를 사각형 내에 배치하여 보고서가 원하는 방식으로 렌더링되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-312">Place a pie and column chart inside a rectangle to ensure that the report renders the way you want.</span></span>

#### <a name="to-add-a-rectangle"></a><span data-ttu-id="68575-313">사각형을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="68575-313">To add a rectangle</span></span>

1.  <span data-ttu-id="68575-314">**디자인** 을 클릭하여 디자인 뷰로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="68575-314">Click **Design** to return to design view.</span></span>

2.  <span data-ttu-id="68575-315">리본 메뉴의 **삽입** 탭에 있는 **보고서 항목** 영역에서 **사각형**을 클릭한 다음 사각형을 테이블 오른쪽의 목록 안으로 끌어옵니다.</span><span class="sxs-lookup"><span data-stu-id="68575-315">On the **Insert** tab of the ribbon, in the **Report Items** area click **Rectangle**, and then drag the rectangle inside the list, to the right of the table.</span></span> <span data-ttu-id="68575-316">사각형의 너비와 높이를 각각 2인치와 4인치로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="68575-316">Make the rectangle 2 inches wide and 4 inches tall.</span></span>

3.  <span data-ttu-id="68575-317">사각형과 테이블의 위쪽을 맞춥니다.</span><span class="sxs-lookup"><span data-stu-id="68575-317">Align the tops of the rectangle and the table.</span></span>

#### <a name="to-add-a-pie-chart"></a><span data-ttu-id="68575-318">원형 차트를 추가하려면</span><span class="sxs-lookup"><span data-stu-id="68575-318">To add a pie chart</span></span>

1.  <span data-ttu-id="68575-319">리본 메뉴의 **삽입** 탭에 있는 **데이터 시각화** 영역에서 **차트** 를 클릭한 다음 **차트 마법사**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-319">On the **Insert** tab of the ribbon, in the **Data Visualizations** area, click **Chart,** and then click **Chart Wizard**.</span></span>

2.  <span data-ttu-id="68575-320">데이터 세트 선택 페이지에서 **ListDataset**을 클릭한 후, **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-320">On the Choose a dataset page, click **ListDataset**, and then click **Next**.</span></span>

3.  <span data-ttu-id="68575-321">**원형**을 클릭하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-321">Click **Pie**, and then click **Next**.</span></span>

4.  <span data-ttu-id="68575-322">차트 필드 정렬 페이지에서 Product를 **범주**로 끌어옵니다.</span><span class="sxs-lookup"><span data-stu-id="68575-322">On the arrange chart fields page, drag Product to **Categories**.</span></span>

5.  <span data-ttu-id="68575-323">Quantity를 **값**으로 끌어 **오고 다음을 클릭 합니다**.</span><span class="sxs-lookup"><span data-stu-id="68575-323">Drag Quantity to **Values**, and then click **Next**.</span></span>

6.  <span data-ttu-id="68575-324">**스타일 선택** 페이지의 **스타일** 창에서 **Slate**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-324">On the **Choose a Style** page, in the **Styles** pane, select **Slate**.</span></span>

7.  <span data-ttu-id="68575-325">**Finish**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-325">Click **Finish**.</span></span>

8.  <span data-ttu-id="68575-326">보고서의 왼쪽 위 모퉁이에 나타나는 차트의 높이와 너비를 각각 1 1/2인치와 2인치로 조정합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-326">Resize the chart that appears in the upper left corner of the report, to be 1 1/2 inches tall and 2 inches wide.</span></span>

9. <span data-ttu-id="68575-327">차트를 사각형 안으로 끌어옵니다.</span><span class="sxs-lookup"><span data-stu-id="68575-327">Drag the chart inside the rectangle.</span></span>

     <span data-ttu-id="68575-328">![원형 차트 추가](../../2014/tutorials/media/tutorial-addpiechart.png "원형 차트 추가")</span><span class="sxs-lookup"><span data-stu-id="68575-328">![Add pie chart](../../2014/tutorials/media/tutorial-addpiechart.png "Add pie chart")</span></span>

10. <span data-ttu-id="68575-329">차트 제목을 마우스 오른쪽 단추로 클릭한 다음 **제목 속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-329">Right-click the chart title, and then click **Title Properties**.</span></span>

11. <span data-ttu-id="68575-330">**차트 제목 속성** 대화 상자의 제목 입력란에 **Product Quantities Sold**를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-330">In the **Chart Title Properties** dialog box, in Title text, type: **Product Quantities Sold**.</span></span>

12. <span data-ttu-id="68575-331">**글꼴** 탭을 클릭하고 **크기** 목록에서 **10pt**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-331">Click the **Font** tab, and in the **Size** list, click **10pt**.</span></span>

13. [!INCLUDE[clickOK](../includes/clickok-md.md)]

#### <a name="to-add-a-column-chart"></a><span data-ttu-id="68575-332">세로 막대형 차트를 추가하려면</span><span class="sxs-lookup"><span data-stu-id="68575-332">To add a column chart</span></span>

1.  <span data-ttu-id="68575-333">리본 메뉴의 **삽입** 탭에 있는 **데이터 시각화** 영역에서 **차트** 를 클릭한 다음 **차트 마법사**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-333">On the **Insert** tab of the ribbon, in the **Data Visualizations** area, click **Chart,** and then click **Chart Wizard**.</span></span>

2.  <span data-ttu-id="68575-334">**데이터 세트 선택** 페이지에서 **ListDataset**을 클릭한 후, **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-334">On the **Choose a dataset** page, click **ListDataset**, and then click **Next**.</span></span>

3.  <span data-ttu-id="68575-335">**세로 막대형**을 클릭하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-335">Click **Column**, and then click **Next**.</span></span>

4.  <span data-ttu-id="68575-336">차트 필드 정렬 페이지에서 Product 필드를 **범주**로 끌어 옵니다.</span><span class="sxs-lookup"><span data-stu-id="68575-336">On the arrange chart fields page, drag the Product field to **Categories**.</span></span>

5.  <span data-ttu-id="68575-337">Sales를 **값** 으로 끌어온 후 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-337">Drag Sales to **Values,** and then click **Next**.</span></span>

     <span data-ttu-id="68575-338">세로 축에 값이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="68575-338">Values display on the vertical axis.</span></span>

6.  <span data-ttu-id="68575-339">**스타일 선택** 페이지의 **스타일** 창에서 **Slate**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-339">On the **Choose a Style** page, in the **Styles** pane, select **Slate**.</span></span>

7.  <span data-ttu-id="68575-340">**Finish**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-340">Click **Finish**.</span></span>

     <span data-ttu-id="68575-341">세로 막대형 차트가 보고서의 왼쪽 위 모퉁이에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="68575-341">A column chart is added to the upper left corner of the report.</span></span>

8.  <span data-ttu-id="68575-342">차트의 너비와 높이를 모두 2인치로 조정합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-342">Resize the chart to be 2 inches wide and 2 inches tall.</span></span>

9. <span data-ttu-id="68575-343">차트를 원형 차트 아래의 사각형 안으로 끌어옵니다.</span><span class="sxs-lookup"><span data-stu-id="68575-343">Drag the chart inside the rectangle, below the pie chart.</span></span>

     <span data-ttu-id="68575-344">![세로 막대형 차트 추가](../../2014/tutorials/media/tutorial-addcolumnchart.png "세로 막대형 차트 추가")</span><span class="sxs-lookup"><span data-stu-id="68575-344">![Add column chart](../../2014/tutorials/media/tutorial-addcolumnchart.png "Add column chart")</span></span>

10. <span data-ttu-id="68575-345">차트 제목을 마우스 오른쪽 단추로 클릭 한 다음 **제목 속성**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-345">Right-click the chart title and then click **Title Properties**.</span></span>

11. <span data-ttu-id="68575-346">**차트 제목 속성** 대화 상자의 제목 입력란에 **Product Sales**를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-346">In the **Chart Title Properties** dialog box, in Title text, type: **Product Sales**.</span></span>

12. <span data-ttu-id="68575-347">**글꼴** 탭을 클릭하고 **크기** 목록에서 **10pt**를 클릭한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-347">Click the **Font** tab, and in the **Size** list click **10pt**, and then click **OK**.</span></span>

13. <span data-ttu-id="68575-348">세로 막대형 차트에서 세로 축을 마우스 오른쪽 단추로 클릭한 다음 **축 제목 표시**의 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-348">In the column chart, right click the vertical axis, and then deselect **Show Axis Title**.</span></span>

14. <span data-ttu-id="68575-349">가로 축에 대해 13단계를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-349">Repeat step 13 for the horizontal axis.</span></span>

15. <span data-ttu-id="68575-350">범례를 마우스 오른쪽 단추로 클릭한 다음 **범례 삭제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-350">Right click the legend, and then click **Delete Legend**.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="68575-351">차트 크기가 작은 경우 축 제목 및 범례를 제거하면 차트를 더 쉽게 읽을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="68575-351">Removing axis titles and the legend makes the chart more readable when it is a small size.</span></span>

 <span data-ttu-id="68575-352">![차트 제목 변경 및 축 제목 제거](../../2014/tutorials/media/tutorial-columnchart-newtitle-noaxistitle.png "차트 제목 변경 및 축 제목 제거")</span><span class="sxs-lookup"><span data-stu-id="68575-352">![Change chart titles and remove axis title](../../2014/tutorials/media/tutorial-columnchart-newtitle-noaxistitle.png "Change chart titles and remove axis title")</span></span>

#### <a name="to-verify-the-charts-are-inside-the-rectangle"></a><span data-ttu-id="68575-353">차트가 사각형 내에 있는지 확인하려면</span><span class="sxs-lookup"><span data-stu-id="68575-353">To verify the charts are inside the rectangle</span></span>

1.  <span data-ttu-id="68575-354">이 단원의 앞부분에서 추가한 사각형을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-354">Click the rectangle you added earlier in this lesson.</span></span>

     <span data-ttu-id="68575-355">속성 창의 `Name` 속성에 사각형의 이름이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="68575-355">In the Properties pane, the `Name` property displays the name of the rectangle.</span></span>

     <span data-ttu-id="68575-356">![사각형의 이름](../../2014/tutorials/media/tutorial-rectanglename.png "사각형의 이름")</span><span class="sxs-lookup"><span data-stu-id="68575-356">![Name of rectangle](../../2014/tutorials/media/tutorial-rectanglename.png "Name of rectangle")</span></span>

2.  <span data-ttu-id="68575-357">원형 차트를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-357">Click the pie chart.</span></span>

3.  <span data-ttu-id="68575-358">**속성** 창에서 `Parent` 속성에 사각형의 이름이 포함 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-358">In the **Properties** pane, verify that the `Parent` property contains the name of the rectangle.</span></span>

     <span data-ttu-id="68575-359">![원형 차트의 상위 속성](../../2014/tutorials/media/tutorial-piechart-parentproperty.png "원형 차트의 상위 속성")</span><span class="sxs-lookup"><span data-stu-id="68575-359">![Parent property for pie chart](../../2014/tutorials/media/tutorial-piechart-parentproperty.png "Parent property for pie chart")</span></span>

4.  <span data-ttu-id="68575-360">세로 막대형 차트를 클릭하고 2~3단계를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-360">Click the column chart and repeat steps 2 and 3.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="68575-361">차트가 사각형 내에 없으면 렌더링된 보고서에 차트가 함께 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="68575-361">If the charts are not inside the rectangle, the rendered report does not display the charts together.</span></span>

#### <a name="to-make-the-charts-the-same-size"></a><span data-ttu-id="68575-362">차트의 크기를 동일하게 하려면</span><span class="sxs-lookup"><span data-stu-id="68575-362">To make the charts the same size</span></span>

1.  <span data-ttu-id="68575-363">원형 차트를 클릭하고 Ctrl 키를 누른 다음 세로 막대형 차트를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-363">Click the pie chart, press the Ctrl key, and then click the column chart.</span></span>

2.  <span data-ttu-id="68575-364">두 차트를 모두 선택한 상태로 마우스 오른쪽 단추를 클릭한 다음 **레이아웃**을 가리키고 **같은 너비로**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="68575-364">With both charts selected, right-click, point to **Layout**, and then click **Make Same Width**.</span></span>

     <span data-ttu-id="68575-365">![차트 너비를 같게 만들기](../../2014/tutorials/media/tutorial-makechartssamewidth.png "차트 너비를 같게 만들기")</span><span class="sxs-lookup"><span data-stu-id="68575-365">![Make chart widths the same](../../2014/tutorials/media/tutorial-makechartssamewidth.png "Make chart widths the same")</span></span>

    > [!NOTE]
    >  <span data-ttu-id="68575-366">선택한 모든 항목의 너비는 처음 클릭한 항목의 너비에 따라 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="68575-366">The item you click first determines the width of all the selected items.</span></span>

3.  <span data-ttu-id="68575-367">**실행** 을 클릭하여 보고서를 미리 봅니다.</span><span class="sxs-lookup"><span data-stu-id="68575-367">Click **Run** to preview the report.</span></span>

 <span data-ttu-id="68575-368">이제 보고서의 원형 차트 및 세로 막대형 차트에 요약 판매 데이터가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="68575-368">The report now displays summary sales data in pie and column charts.</span></span>

 <span data-ttu-id="68575-369">![SSRS 자습서, 자유 형식 보고서](../../2014/tutorials/media/tutorial-reportfinal.png "SSRS 자습서, 자유 형식 보고서")</span><span class="sxs-lookup"><span data-stu-id="68575-369">![SSRS tutorial, free form report](../../2014/tutorials/media/tutorial-reportfinal.png "SSRS tutorial, free form report")</span></span>

## <a name="more-information"></a><span data-ttu-id="68575-370">추가 정보</span><span class="sxs-lookup"><span data-stu-id="68575-370">More Information</span></span>
 <span data-ttu-id="68575-371">목록에 대 한 자세한 내용은 [테이블, 행렬 및 목록 &#40;보고서 작성기 및 ssrs&#41;](report-design/tables-matrices-and-lists-report-builder-and-ssrs.md), 목록 [&#40;보고서 작성기 및 ssrs&#41;](report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md), 테이블 [릭 스 데이터 영역 &#40;보고서 작성기 및 Ssrs&#41;](report-design/tablix-data-region-areas-report-builder-and-ssrs.md), [테이블 릭 스 데이터 영역 셀, 행 및 열](report-design/tablix-data-region-cells-rows-and-columns-report-builder-and-ssrs.md)&#40;보고서 작성기&#41; 및 ssrs를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="68575-371">For more information about lists, see [Tables, Matrices, and Lists &#40;Report Builder and SSRS&#41;](report-design/tables-matrices-and-lists-report-builder-and-ssrs.md), [Lists &#40;Report Builder and SSRS&#41;](report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md), [Tablix Data Region Areas &#40;Report Builder and SSRS&#41;](report-design/tablix-data-region-areas-report-builder-and-ssrs.md), and [Tablix Data Region Cells, Rows, and Columns &#40;Report Builder&#41; and SSRS](report-design/tablix-data-region-cells-rows-and-columns-report-builder-and-ssrs.md).</span></span>

 <span data-ttu-id="68575-372">쿼리 디자이너에 대한 자세한 내용은 [쿼리 디자이너&#40;보고서 작성기&#41;](../../2014/reporting-services/query-designers-report-builder.md) 및 [텍스트 기반 쿼리 디자이너 사용자 인터페이스&#40;보고서 작성기&#41;](report-data/text-based-query-designer-user-interface-report-builder.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="68575-372">For more information about query designers, see [Query Designers &#40;Report Builder&#41;](../../2014/reporting-services/query-designers-report-builder.md) and [Text-based Query Designer User Interface &#40;Report Builder&#41;](report-data/text-based-query-designer-user-interface-report-builder.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="68575-373">참고 항목</span><span class="sxs-lookup"><span data-stu-id="68575-373">See Also</span></span>
 <span data-ttu-id="68575-374">[2014 SQL Server의](report-builder/report-builder-in-sql-server-2016.md) [자습서 &#40;보고서 작성기 보고서 작성기&#41;](report-builder-tutorials.md)</span><span class="sxs-lookup"><span data-stu-id="68575-374">[Tutorials &#40;Report Builder&#41;](report-builder-tutorials.md) [Report Builder in SQL Server 2014](report-builder/report-builder-in-sql-server-2016.md)</span></span>


