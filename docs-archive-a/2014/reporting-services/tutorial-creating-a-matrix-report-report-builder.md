---
title: '자습서: 행렬 보고서 만들기(보고서 작성기) | Microsoft Docs'
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 9ee19c2e-2a8c-4bb0-9274-04a5812c2e96
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3df32098d9e6400931ba2a88b2ffd22d6e015a62
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737821"
---
# <a name="tutorial-creating-a-matrix-report-report-builder"></a><span data-ttu-id="54c45-102">자습서: 행렬 보고서 만들기(보고서 작성기)</span><span class="sxs-lookup"><span data-stu-id="54c45-102">Tutorial: Creating a Matrix Report (Report Builder)</span></span>
  <span data-ttu-id="54c45-103">이 자습서에서는 예제 판매 데이터를 기반으로 기본 행렬 보고서를 만드는 방법을 배웁니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-103">This tutorial teaches you how to create a basic matrix report based on sample sales data.</span></span> <span data-ttu-id="54c45-104">행렬에는 중첩 행 및 열 그룹과 인접 열 그룹이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-104">The matrix has nested row and column groups and an adjacent column group.</span></span> <span data-ttu-id="54c45-105">열의 서식을 지정하고 텍스트를 회전하는 방법도 배웁니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-105">You will also learn how to format columns and rotate text.</span></span> <span data-ttu-id="54c45-106">다음 그림에서는 만들려는 보고서와 비슷한 보고서를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-106">The following illustration shows a report similar to the one you will create.</span></span>  
  
 <span data-ttu-id="54c45-107">![rs_CreateMatixReportTutorial](../../2014/tutorials/media/rs-creatematixreporttutorial.gif "rs_CreateMatixReportTutorial")</span><span class="sxs-lookup"><span data-stu-id="54c45-107">![rs_CreateMatixReportTutorial](../../2014/tutorials/media/rs-creatematixreporttutorial.gif "rs_CreateMatixReportTutorial")</span></span>  
  
 <span data-ttu-id="54c45-108">이 자습서에서 만드는 향상된 버전의 보고서는 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] 보고서 작성기의 예제 보고서로 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-108">An enhanced version of the report you will create in this tutorial is available as a sample [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] Report Builder report.</span></span> <span data-ttu-id="54c45-109">이 예제 보고서 및 기타 보고서를 다운로드하는 방법은 [보고서 작성기 예제 보고서(Report Builder sample reports)](https://go.microsoft.com/fwlink/?LinkId=184851)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="54c45-109">For more information about downloading this sample report and others, see [Report Builder sample reports](https://go.microsoft.com/fwlink/?LinkId=184851).</span></span>  
  
##  <a name="what-you-will-learn"></a><a name="BackToTop"></a><span data-ttu-id="54c45-110">학습 내용</span><span class="sxs-lookup"><span data-stu-id="54c45-110">What You Will Learn</span></span>  
 <span data-ttu-id="54c45-111">이 자습서에서는 다음 작업 방법을 배웁니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-111">In this tutorial, you will learn how to:</span></span>  
  
1.  [<span data-ttu-id="54c45-112">새 테이블 또는 행렬 마법사에서 행렬 보고서 및 데이터 세트 만들기</span><span class="sxs-lookup"><span data-stu-id="54c45-112">Create a Matrix Report and Dataset from the New Table or Matrix Wizard</span></span>](#CreateMatrix)  
  
2.  [<span data-ttu-id="54c45-113">새 테이블 또는 행렬 마법사에서 데이터 구성 및 레이아웃과 스타일 선택</span><span class="sxs-lookup"><span data-stu-id="54c45-113">Organize Data and Choose Layout and Style from the New Table or Matrix Wizard</span></span>](#Groups)  
  
3.  [<span data-ttu-id="54c45-114">데이터 서식 지정</span><span class="sxs-lookup"><span data-stu-id="54c45-114">Format Data</span></span>](#FormatData)  
  
4.  [<span data-ttu-id="54c45-115">인접 열 그룹 추가</span><span class="sxs-lookup"><span data-stu-id="54c45-115">Add Adjacent Column Group</span></span>](#AdjacentGroup)  
  
5.  [<span data-ttu-id="54c45-116">열 너비 변경</span><span class="sxs-lookup"><span data-stu-id="54c45-116">Change Column Widths</span></span>](#Width)  
  
6.  [<span data-ttu-id="54c45-117">행렬 셀 병합</span><span class="sxs-lookup"><span data-stu-id="54c45-117">Merge Matrix Cells</span></span>](#MergeCells)  
  
7.  [<span data-ttu-id="54c45-118">보고서 머리글 및 보고서 제목 추가</span><span class="sxs-lookup"><span data-stu-id="54c45-118">Add a Report Header and Report Title</span></span>](#HeaderTitle)  
  
8.  [<span data-ttu-id="54c45-119">보고서 저장</span><span class="sxs-lookup"><span data-stu-id="54c45-119">Save the Report</span></span>](#Save)  
  
### <a name="other-optional-step"></a><span data-ttu-id="54c45-120">기타 선택적 단계</span><span class="sxs-lookup"><span data-stu-id="54c45-120">Other Optional Step</span></span>  
  
1.  [<span data-ttu-id="54c45-121">입력란 270도 회전</span><span class="sxs-lookup"><span data-stu-id="54c45-121">Rotate Text Box 270 Degrees</span></span>](#RotateTextBox)  
  
 <span data-ttu-id="54c45-122">이 자습서에 소요되는 예상 시간: 20분</span><span class="sxs-lookup"><span data-stu-id="54c45-122">Estimated time to complete this tutorial: 20 minutes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="54c45-123">요구 사항</span><span class="sxs-lookup"><span data-stu-id="54c45-123">Requirements</span></span>  
 <span data-ttu-id="54c45-124">요구 사항에 대한 자세한 내용은 [자습서의 필수 조건&#40;보고서 작성기&#41;](../reporting-services/report-builder-tutorials.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="54c45-124">For more information about requirements, see [Prerequisites for Tutorials &#40;Report Builder&#41;](../reporting-services/report-builder-tutorials.md).</span></span>  
  
##  <a name="1-create-a-matrix-report-and-dataset-from-the-new-table-or-matrix-wizard"></a><a name="CreateMatrix"></a><span data-ttu-id="54c45-125">1. 새 테이블 또는 행렬 마법사에서 행렬 보고서 및 데이터 집합 만들기</span><span class="sxs-lookup"><span data-stu-id="54c45-125">1. Create a Matrix Report and Dataset from the New Table or Matrix Wizard</span></span>  
 <span data-ttu-id="54c45-126">보고서 작성기의 **시작** 대화 상자에서 공유 데이터 원본을 선택 하 고, 포함 된 데이터 집합을 만들고, 행렬에 데이터를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-126">From the **Getting Started** dialog box in Report Builder, choose a shared data source, create an embedded dataset, and then display the data in a matrix.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="54c45-127">이 자습서의 쿼리에는 이미 데이터 값이 포함되어 있으므로 외부 데이터 원본이 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-127">In this tutorial, the query already contains the data values, so that it does not need an external data source.</span></span> <span data-ttu-id="54c45-128">따라서 쿼리가 상당히 길어집니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-128">This makes the query quite long.</span></span> <span data-ttu-id="54c45-129">비즈니스 환경에서는 쿼리에 데이터가 포함되지 않을 것입니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-129">In a business environment, a query would not contain the data.</span></span> <span data-ttu-id="54c45-130">이 자습서의 쿼리는 학습용으로만 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-130">This is for learning purposes only.</span></span>  
  
#### <a name="to-create-a-new-matrix"></a><span data-ttu-id="54c45-131">새 행렬을 만들려면</span><span class="sxs-lookup"><span data-stu-id="54c45-131">To create a new matrix</span></span>  
  
1.  <span data-ttu-id="54c45-132">**시작**을 클릭하고 **프로그램**, **Microsoft SQL Server 2012 보고서 작성기**를 차례로 가리킨 다음 **보고서 작성기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-132">Click **Start**, point to **Programs**, point to **Microsoft SQL Server 2012 Report Builder**, and then click **Report Builder**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="54c45-133">**시작** 대화 상자가 나타나야 합니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-133">The **Getting Started** dialog box should appear.</span></span> <span data-ttu-id="54c45-134">그렇지 않으면 보고서 작성기 단추에서 **새로 만들기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-134">If it doesn't, from the Report Builder button, click **New**.</span></span>  
  
2.  <span data-ttu-id="54c45-135">왼쪽 창에 **새 보고서** 가 선택되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-135">In the left pane, verify that **New Report** is selected.</span></span>  
  
3.  <span data-ttu-id="54c45-136">오른쪽 창에서 **테이블 또는 행렬 마법사**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-136">In the right pane, click **Table or Matrix Wizard**.</span></span>  
  
4.  <span data-ttu-id="54c45-137">**데이터 세트 선택** 페이지에서 **데이터 세트 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-137">On the **Choose a dataset** page, click **Create a dataset**.</span></span>  
  
5.  <span data-ttu-id="54c45-138">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-138">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="54c45-139">**데이터 원본에 대 한 연결 선택** 페이지에서 기존 데이터 원본을 선택 하거나 보고서 서버로 이동한 후 데이터 원본을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-139">On the **Choose a connection to a data source** page, select an existing data source or browse to the report server, and then select a data source.</span></span> <span data-ttu-id="54c45-140">데이터 원본을 사용할 수 없거나 보고서 서버에 대한 액세스 권한이 없는 경우 포함된 데이터 원본을 대신 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-140">If no data source is available or you do not have access to a report server, you can use an embedded data source instead.</span></span> <span data-ttu-id="54c45-141">포함 된 데이터 원본을 만드는 방법에 대 한 자세한 내용은 [자습서: 기본 테이블 보고서 만들기 &#40;보고서 작성기&#41;](../reporting-services/tutorial-creating-a-basic-table-report-report-builder.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="54c45-141">For more information about creating an embedded data source, see [Tutorial: Creating a Basic Table Report &#40;Report Builder&#41;](../reporting-services/tutorial-creating-a-basic-table-report-report-builder.md).</span></span>  
  
7.  <span data-ttu-id="54c45-142">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-142">Click **Next**.</span></span>  
  
8.  <span data-ttu-id="54c45-143">**쿼리 디자인** 페이지에서 **텍스트로 편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-143">On the **Design a query** page, click **Edit as Text**.</span></span>  
  
9. <span data-ttu-id="54c45-144">쿼리 창에 다음 쿼리를 복사하여 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-144">Copy and paste the following query into the query pane:</span></span>  
  
    ```  
    SELECT CAST('2009-01-05' AS date) as SalesDate, 'Central' as Territory, 'Accessories' as Subcategory,'Carrying Case' as Product, CAST(16996.60 AS money) AS Sales, 68 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'North' as Territory, 'Accessories' as Subcategory, 'Carrying Case' as Product, CAST(13747.25 AS money) AS Sales, 55 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'South' as Territory, 'Accessories' as Subcategory,'Carrying Case' as Product, CAST(9248.15 AS money) As Sales, 37 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Central' as Territory, 'Accessories' as Subcategory,'Tripod' as Product, CAST(1350.00 AS money) AS Sales, 18 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'North' as Territory, 'Accessories' as Subcategory,'Tripod' as Product, CAST(1800.00 AS money) AS Sales, 24 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'South' as Territory, 'Accessories' as Subcategory,'Tripod' as Product, CAST(1125.00 AS money) AS Sales, 15 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Central' as Territory, 'Accessories' as Subcategory,'Lens Adapter' as Product, CAST(1147.50 AS money) AS Sales, 17 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'North' as Territory, 'Accessories' as Subcategory,  'Lens Adapter' as Product, CAST(742.50 AS money) AS Sales, 11 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'South' as Territory, 'Accessories' as Subcategory,'Lens Adapter' as Product, CAST(1417.50 AS money) AS Sales, 21 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Central' as Territory, 'Accessories' as Subcategory, 'Carrying Case' as Product, CAST(13497.30 AS money) AS Sales, 54 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'North' as Territory, 'Accessories' as Subcategory, 'Carrying Case' as Product, CAST(11997.60 AS money) AS Sales, 48 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'South' as Territory, 'Accessories' as Subcategory, 'Carrying Case' as Product, CAST(10247.95 AS money) As Sales, 41 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Central' as Territory, 'Accessories' as Subcategory, 'Tripod' as Product, CAST(1200.00 AS money) AS Sales, 16 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'North' as Territory, 'Accessories' as Subcategory,'Tripod' as Product, CAST(2025.00 AS money) AS Sales, 27 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'South' as Territory, 'Accessories' as Subcategory,'Tripod' as Product, CAST(1425.00 AS money) AS Sales, 19 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Central' as Territory, 'Accessories' as Subcategory,'Lens Adapter' as Product, CAST(887.50 AS money) AS Sales, 13 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'North' as Territory, 'Accessories' as Subcategory, 'Lens Adapter' as Product, CAST(607.50 AS money) AS Sales, 9 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'South' as Territory, 'Accessories' as Subcategory,'Lens Adapter' as Product, CAST(1215.00 AS money) AS Sales, 18 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate,  'Central' as Territory, 'Digital' as Subcategory,'Compact Digital' as Product, CAST(10191.00 AS money) AS Sales, 79 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate,  'North' as Territory, 'Digital' as Subcategory, 'Compact Digital' as Product, CAST(8772.00 AS money) AS Sales, 68 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate,  'South' as Territory, 'Digital' as Subcategory, 'Compact Digital' as Product, CAST(10578.00 AS money) AS Sales, 82 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Central' as Territory,'Digital' as Subcategory, 'Slim Digital' as Product, CAST(7218.10 AS money) AS Sales, 38 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'North' as Territory,'Digital' as Subcategory, 'Slim Digital' as Product, CAST(8357.80 AS money) AS Sales, 44 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'South' as Territory,'Digital' as Subcategory,'Slim Digital' as Product, CAST(9307.55 AS money) AS Sales, 49 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate,  'Central' as Territory, 'Digital' as Subcategory,'Compact Digital' as Product, CAST(3870.00 AS money) AS Sales, 30 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate,  'North' as Territory, 'Digital' as Subcategory,'Compact Digital' as Product, CAST(5805.00 AS money) AS Sales, 45 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate,  'South' as Territory, 'Digital' as Subcategory, 'Compact Digital' as Product, CAST(8643.00 AS money) AS Sales, 67 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Central' as Territory, 'Digital' as Subcategory, 'Slim Digital' as Product, CAST(9877.40 AS money) AS Sales, 52 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'North' as Territory, 'Digital' as Subcategory, 'Slim Digital' as Product, CAST(12536.70 AS money) AS Sales, 66 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'South' as Territory, 'Digital' as Subcategory, 'Slim Digital' as Product, CAST(6648.25 AS money) AS Sales, 35 as Quantity  
    ```  
  
10. <span data-ttu-id="54c45-145">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-145">Click **Next**.</span></span>  
  
##  <a name="2-organize-data-and-choose-layout-and-style-from-the-new-table-or-matrix-wizard"></a><a name="Groups"></a><span data-ttu-id="54c45-146">2. 새 테이블 또는 행렬 마법사에서 데이터 구성 및 레이아웃 및 스타일 선택</span><span class="sxs-lookup"><span data-stu-id="54c45-146">2. Organize Data and Choose Layout and Style from the New Table or Matrix Wizard</span></span>  
 <span data-ttu-id="54c45-147">이 마법사를 사용하여 데이터를 표시할 시작 디자인을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-147">Use the wizard to provide a starting design on which to display data.</span></span> <span data-ttu-id="54c45-148">이 마법사의 미리 보기 창에서는 행렬 디자인을 완료하기 전에 데이터 그룹화의 결과를 시각화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-148">The preview pane in the wizard helps you to visualize the result of grouping data before you complete the matrix design.</span></span>  
  
#### <a name="to-organize-data-into-groups-and-choose-a-layout-and-style"></a><span data-ttu-id="54c45-149">데이터를 그룹으로 구성하고 레이아웃과 스타일을 선택하려면</span><span class="sxs-lookup"><span data-stu-id="54c45-149">To organize data into groups and choose a layout and style</span></span>  
  
1.  <span data-ttu-id="54c45-150">**필드 정렬** 페이지에서 **사용 가능한 필드** 의 Territory를 **행 그룹**으로 끌어옵니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-150">On the **Arrange fields** page, drag Territory from **Available fields** to **Row groups**.</span></span>  
  
2.  <span data-ttu-id="54c45-151">SalesDate를 **행 그룹** 으로 끌어 Territory 아래에 배치합니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-151">Drag SalesDate to **Row groups** and place it below Territory.</span></span>  
  
     <span data-ttu-id="54c45-152">**행 그룹** 에 필드가 나열되는 순서에 따라 그룹 계층 구조가 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-152">The order in which fields are listed in **Row groups** defines the group hierarchy.</span></span> <span data-ttu-id="54c45-153">1-2단계에서는 필드 값을 먼저 지역별로 구성한 다음 판매 날짜별로 구성했습니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-153">Steps 1 and 2 organize the values of the fields first by territory, and then by sales date.</span></span>  
  
3.  <span data-ttu-id="54c45-154">Subcategory를 **열 그룹**으로 끌어옵니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-154">Drag Subcategory to **Column groups**.</span></span>  
  
4.  <span data-ttu-id="54c45-155">Product를 **열 그룹** 으로 끌고 하위 범주 아래에 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-155">Drag Product to **Column groups,** and then place below Subcategory.</span></span>  
  
     <span data-ttu-id="54c45-156">**열 그룹** 에 필드가 나열 되는 순서에 따라 그룹 계층 구조가 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-156">The order in which fields are listed in **Column groups** defines the group hierarchy.</span></span>  
  
     <span data-ttu-id="54c45-157">3-4단계에서는 필드 값을 먼저 하위 범주별로 구성한 다음 제품별로 구성했습니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-157">Steps 3 and 4 organize the values for the fields first by subcategory, and then by product.</span></span>  
  
5.  <span data-ttu-id="54c45-158">Sales를 **값**으로 끌어옵니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-158">Drag Sales to **Values**.</span></span>  
  
     <span data-ttu-id="54c45-159">Sales는 숫자 필드를 요약하기 위한 기본 함수인 Sum 함수를 사용하여 요약됩니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-159">Sales is summarized with the Sum function, the default function to summarize numeric fields.</span></span>  
  
6.  <span data-ttu-id="54c45-160">Quantity를 **값**으로 끌어옵니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-160">Drag Quantity to **Values**.</span></span>  
  
     <span data-ttu-id="54c45-161">Quantity는 Sum 함수를 사용하여 요약됩니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-161">Quantity is summarized with the Sum function.</span></span>  
  
     <span data-ttu-id="54c45-162">5-6단계에서는 행렬 데이터 셀에 표시할 데이터를 지정했습니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-162">Steps 5 and 6 specify the data to display in the matrix data cells.</span></span>  
  
7.  <span data-ttu-id="54c45-163">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-163">Click **Next**.</span></span>  
  
8.  <span data-ttu-id="54c45-164">레이아웃 선택 페이지의 **옵션**에서 **부분합 및 총합계 표시** 가 선택되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-164">On the Choose the Layout page, under **Options**, verify that **Show subtotals and grand totals** is selected.</span></span>  
  
9. <span data-ttu-id="54c45-165">**블록형, 부분합 하단 표시** 가 선택되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-165">Verify that **Blocked, subtotal below** is selected.</span></span>  
  
10. <span data-ttu-id="54c45-166">**그룹 확장/축소** 옵션이 선택되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-166">Verify the option **Expand/collapse groups** is selected.</span></span>  
  
11. <span data-ttu-id="54c45-167">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-167">Click **Next**.</span></span>  
  
12. <span data-ttu-id="54c45-168">스타일 선택 페이지의 스타일 창에서 **Slate**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-168">On the Choose a Style page, in the Styles pane, select **Slate**.</span></span>  
  
13. <span data-ttu-id="54c45-169">**Finish**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-169">Click **Finish**.</span></span>  
  
     <span data-ttu-id="54c45-170">디자인 화면에 행렬이 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-170">The matrix is added to the design surface.</span></span> <span data-ttu-id="54c45-171">행 그룹 창에는 Territory 및 SalesDate라는 두 개의 행 그룹이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-171">The Row Groups pane shows two row groups: Territory and SalesDate.</span></span> <span data-ttu-id="54c45-172">열 그룹 창에는 하위 범주 및 제품이라는 두 개의 열 그룹이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-172">The Column Groups pane shows two column groups: Subcategory and Product.</span></span> <span data-ttu-id="54c45-173">세부 데이터는 모두 데이터 세트 쿼리로 검색된 데이터입니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-173">Detail data is all the data that is retrieved by the dataset query.</span></span>  
  
14. <span data-ttu-id="54c45-174">**실행** 을 클릭하여 보고서를 미리 봅니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-174">Click **Run** to preview the report.</span></span>  
  
 <span data-ttu-id="54c45-175">특정 날짜에 판매된 각 제품에 대해 해당 제품이 속한 하위 범주 및 판매 지역이 행렬에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-175">For each product that is sold on a specific date, the matrix shows the subcategory to which the product belongs and the territory of the sales.</span></span>  
  
##  <a name="3-format-data"></a><a name="FormatData"></a><span data-ttu-id="54c45-176">3. 데이터 서식 지정</span><span class="sxs-lookup"><span data-stu-id="54c45-176">3. Format Data</span></span>  
 <span data-ttu-id="54c45-177">기본적으로 Sales 필드의 요약 데이터에는 일반 숫자가 표시되고, SalesDate 필드의 요약 데이터에는 날짜와 시간 정보가 모두 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-177">By default, the summary data for the Sales field displays a general number and the SalesDate field displays both date and time information.</span></span> <span data-ttu-id="54c45-178">Sales 필드에서는 숫자를 통화로 표시하고 SalesDate 필드에서는 날짜만 표시하도록 서식을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-178">Format the Sales field to display the number as currency and the SalesDate field to display only the date.</span></span> <span data-ttu-id="54c45-179">**자리 표시자 스타일** 을 설정/해제하여 서식 있는 입력란 및 자리 표시자 텍스트를 보기 값으로 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-179">Toggle **Placeholder Styles** to display formatted text boxes and placeholder text as sample values.</span></span>  
  
#### <a name="to-format-fields"></a><span data-ttu-id="54c45-180">필드의 서식을 지정하려면</span><span class="sxs-lookup"><span data-stu-id="54c45-180">To format fields</span></span>  
  
1.  <span data-ttu-id="54c45-181">디자인 **을 클릭 하 여 디자인** 뷰로 전환 합니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-181">Click **Design** to switch to design view.</span></span>  
  
2.  <span data-ttu-id="54c45-182">Ctrl 키를 누른 상태로 `[Sum(Sales)]`이 들어 있는 9개의 셀을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-182">Press the Ctrl key, and then select the nine cells that contain `[Sum(Sales)]`.</span></span>  
  
3.  <span data-ttu-id="54c45-183">**홈** 탭의 **숫자** 그룹에서 **통화**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-183">On the **Home** tab, in the **Number** group, click **Currency**.</span></span> <span data-ttu-id="54c45-184">셀이 변경되어 서식 지정된 통화가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-184">The cells changeto show the formatted currency.</span></span>  
  
     <span data-ttu-id="54c45-185">국가별 설정이 영어(미국)인 경우 기본 예제 텍스트는 [**$12,345.00**]입니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-185">If your regional setting is English (United States), the default sample text is [**$12,345.00**].</span></span> <span data-ttu-id="54c45-186">예제 통화 값이 표시되지 않으면 **숫자** 그룹에서 **자리 표시자 스타일** 을 클릭한 다음 **보기 값**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-186">If you do not see an example currency value, click **Placeholder Styles** in the **Numbers** group, and then click **Sample Values**.</span></span>  
  
4.  <span data-ttu-id="54c45-187">`[SalesDate]`가 들어 있는 셀을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-187">Click the cell that contains `[SalesDate]`.</span></span>  
  
5.  <span data-ttu-id="54c45-188">**숫자** 그룹의 드롭다운 목록에서 **날짜**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-188">In the **Number** group, from the drop-down list, select **Date**.</span></span>  
  
     <span data-ttu-id="54c45-189">셀에 예제 날짜 **[1/31/2000]** 가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-189">The cell displays the example date **[1/31/2000]**.</span></span> <span data-ttu-id="54c45-190">예제 날짜가 표시되지 않으면 **숫자** 그룹에서 **자리 표시자 스타일** 을 클릭한 다음 **보기 값**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-190">If you do not see an example date, click **Placeholder Styles** in the **Numbers** group, and then click **Sample Values**.</span></span>  
  
6.  <span data-ttu-id="54c45-191">**실행** 을 클릭하여 보고서를 미리 봅니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-191">Click **Run** to preview your report.</span></span>  
  
 <span data-ttu-id="54c45-192">날짜 값은 날짜만 표시되고 판매 값은 통화로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-192">The date values display only dates and the sales values display as currency.</span></span>  
  
##  <a name="4-add-adjacent-column-group"></a><a name="AdjacentGroup"></a><span data-ttu-id="54c45-193">4. 인접 열 그룹 추가</span><span class="sxs-lookup"><span data-stu-id="54c45-193">4. Add Adjacent Column Group</span></span>  
 <span data-ttu-id="54c45-194">행 및 열 그룹을 부모-자식 관계로 중첩시키거나 형제 관계로 인접시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-194">You can nest row and column groups in parent child relationships or adjacent in sibling relationships.</span></span>  
  
 <span data-ttu-id="54c45-195">Subcategory 열 그룹에 인접하는 열 그룹을 추가하고, 셀을 복사하여 새 열 그룹을 채운 다음, 식을 사용하여 열 그룹 머리글의 값을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-195">Add a column group that is adjacent to the Subcategory column group, copy cells to populate the new column group, and then use an expression to create the value of the column group header.</span></span>  
  
#### <a name="to-add-an-adjacent-column-group"></a><span data-ttu-id="54c45-196">인접 열 그룹을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="54c45-196">To add an adjacent column group</span></span>  
  
1.  <span data-ttu-id="54c45-197">**디자인** 을 클릭하여 디자인 뷰로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-197">Click **Design** to return to design view.</span></span>  
  
2.  <span data-ttu-id="54c45-198">`[Subcategory]`가 들어 있는 셀을 마우스 오른쪽 단추로 클릭하고 **그룹 추가**를 가리킨 다음 **오른쪽에 인접**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-198">Right-click the cell that contains `[Subcategory]`, point to **Add Group**, and then click **Adjacent Right**.</span></span>  
  
     <span data-ttu-id="54c45-199">**테이블릭스 그룹** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-199">The **Tablix Group** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="54c45-200">**그룹화 방법** 목록에서 SalesDate를 선택한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-200">In the **Group By** list, select SalesDate, and then click **OK**.</span></span>  
  
     <span data-ttu-id="54c45-201">새 열 그룹이 Subcategory 열 그룹의 왼쪽에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-201">A new column group is added to the left of the Subcategory column group.</span></span>  
  
4.  <span data-ttu-id="54c45-202">`[SalesDate],` 가 들어 있는 새 열 그룹의 셀을 마우스 오른쪽 단추로 클릭한 다음 **식**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-202">Right-click the cell in the new column group that contains `[SalesDate],` and then click **Expression**.</span></span>  
  
5.  <span data-ttu-id="54c45-203">식 상자에 다음 식을 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-203">Copy the following expression to expression box.</span></span>  
  
    ```  
    =WeekdayName(DatePart("w",Fields!SalesDate.Value))  
    ```  
  
     <span data-ttu-id="54c45-204">이 식은 판매 날짜에서 요일 이름을 추출합니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-204">This expression extracts the weekday name from the sales date.</span></span> <span data-ttu-id="54c45-205">자세한 내용은 [식&#40;보고서 작성기 및 SSRS&#41;](report-design/expressions-report-builder-and-ssrs.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="54c45-205">For more information, see [Expressions &#40;Report Builder and SSRS&#41;](report-design/expressions-report-builder-and-ssrs.md).</span></span>  
  
6.  <span data-ttu-id="54c45-206">Total이 들어 있는 Subcategory 열 그룹의 셀을 마우스 오른쪽 단추로 클릭한 다음 **복사**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-206">Right-click the cell in the Subcategory column group that contains Total, and then click **Copy**.</span></span>  
  
7.  <span data-ttu-id="54c45-207">5단계에서 만든 식이 들어 있는 셀 바로 아래의 셀을 마우스 오른쪽 단추로 클릭한 다음 **붙여넣기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-207">Right-click the cell immediately below the cell that contains the expression you created in step 5 and click **Paste**.</span></span>  
  
8.  <span data-ttu-id="54c45-208">Ctrl 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-208">Press the Ctrl key.</span></span>  
  
9. <span data-ttu-id="54c45-209">Subcategory 그룹에서 Sales 열 머리글과 해당 열 아래에 있는 세 개의 셀을 클릭한 다음 **복사**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-209">In the Subcategory group, click the Sales column header and the three cells below it, right-click, and then click **Copy**.</span></span>  
  
10. <span data-ttu-id="54c45-210">네 개의 셀을 새 열 그룹에 있는 빈 셀에 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-210">Paste the four cells into the four empty cells in the new column group.</span></span>  
  
11. <span data-ttu-id="54c45-211">**실행** 을 클릭하여 보고서를 미리 봅니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-211">Click **Run** to preview the report.</span></span>  
  
 <span data-ttu-id="54c45-212">보고서에 Monday 및 Tuesday라는 열이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-212">The report includes columns named Monday and Tuesday.</span></span> <span data-ttu-id="54c45-213">데이터 세트에는 이러한 두 요일에 대한 데이터만 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-213">The dataset contains only data for these two days.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="54c45-214">데이터에 다른 요일이 포함된 경우 보고서에도 해당 요일에 대한 열이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-214">If the data included other days, the report would include columns for them as well.</span></span> <span data-ttu-id="54c45-215">각 열에는 열 머리글, `Sales` 및 지역별 판매 합계가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-215">Each column has the column header, `Sales`, and sales totals by territory.</span></span>  
  
##  <a name="5-change-column-widths"></a><a name="Width"></a><span data-ttu-id="54c45-216">5. 열 너비 변경</span><span class="sxs-lookup"><span data-stu-id="54c45-216">5. Change Column Widths</span></span>  
 <span data-ttu-id="54c45-217">행렬이 포함된 보고서를 실행하면 일반적으로 가로와 세로로 확장됩니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-217">A report that includes a matrix typically expands horizontally as well as vertically when it runs.</span></span> <span data-ttu-id="54c45-218">가로 확장을 제어하는 기능은 특히 보고서를 인쇄용 보고서에 사용되는 Microsoft Word 또는 Adobe PDF 등의 형식으로 내보내려고 할 때 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-218">Controlling horizontal expansion is particularly important if you plan to export the report to formats such as Microsoft Word or Adobe PDF that are used for printed reports.</span></span> <span data-ttu-id="54c45-219">보고서가 여러 페이지에 걸쳐 가로로 확장될 경우에는 인쇄된 페이지를 이해하기 어렵습니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-219">If the report expands horizontally across multiple pages, the printed report is difficult to understand.</span></span> <span data-ttu-id="54c45-220">가로 확장을 최소화하려면 데이터를 자르지 않고 표시하는 데 필요한 너비로만 열 크기를 조정합니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-220">To minimize horizontal expansion, you can resize columns to be only the width necessary to display the data without wrapping.</span></span> <span data-ttu-id="54c45-221">제목이 데이터를 표시하는 데 필요한 너비에 맞도록 열의 이름을 변경해도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-221">You can also rename columns so that their titles fit the width needed to display the data.</span></span>  
  
#### <a name="to-rename-and-resize-the-columns"></a><span data-ttu-id="54c45-222">열의 이름을 바꾸고 크기를 조정하려면</span><span class="sxs-lookup"><span data-stu-id="54c45-222">To rename and resize the columns</span></span>  
  
1.  <span data-ttu-id="54c45-223">**디자인** 을 클릭하여 디자인 뷰로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-223">Click **Design** to return to design view.</span></span>  
  
2.  <span data-ttu-id="54c45-224">가장 왼쪽에 있는 Quantity 열의 텍스트를 선택하고 **QTY**를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-224">Select the text in the furthest Quantity column to the left, and then type **QTY**.</span></span>  
  
     <span data-ttu-id="54c45-225">이제 열 제목은 QTY가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-225">The column title is now QTY.</span></span>  
  
3.  <span data-ttu-id="54c45-226">Quantity라는 다른 열에 대해 2단계를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-226">Repeat step 2 for the other columns named Quantity.</span></span> <span data-ttu-id="54c45-227">이제 이 열이 두 개가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-227">There are two of them.</span></span>  
  
4.  <span data-ttu-id="54c45-228">행렬을 클릭하여 열 핸들과 행 핸들이 행렬 위와 옆에 표시되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-228">Click the matrix so that column and row handles appear above and next to the matrix.</span></span>  
  
     <span data-ttu-id="54c45-229">테이블 위쪽 및 옆쪽을 따라 표시되는 회색 막대는 행 및 열 핸들입니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-229">The gray bars along the top and side of the table are the column and row handles.</span></span>  
  
5.  <span data-ttu-id="54c45-230">가장 왼쪽에 있는 QTY 열의 크기를 조정하려면 커서가 양방향 화살표로 바뀌도록 열 핸들 사이의 선에 커서를 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-230">To resize the furthest QTY column to the left, point to the line between column handles so that the cursor changes into a double arrow.</span></span> <span data-ttu-id="54c45-231">열의 너비가 1/2인치가 될 때까지 열을 왼쪽으로 끌어옵니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-231">Drag the column towards the left until it is 1/2 inch wide.</span></span>  
  
     <span data-ttu-id="54c45-232">너비가 1/2인치인 열은 수량을 표시하는 데 충분합니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-232">A column width of 1/2 inch is adequate to display the quantity.</span></span>  
  
6.  <span data-ttu-id="54c45-233">QTY라는 다른 열에 대해 5단계를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-233">Repeat step 5 for the other columns named QTY.</span></span>  
  
7.  <span data-ttu-id="54c45-234">**실행** 을 클릭하여 보고서를 미리 봅니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-234">Click **Run** to preview your report.</span></span>  
  
 <span data-ttu-id="54c45-235">이제 수량이 들어 있는 보고서 열 이름이 QTY가 되고 해당 열의 너비가 좁아집니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-235">The columns in the report that contains quantities are now named QTY and the columns are narrower.</span></span>  
  
##  <a name="6-merge-matrix-cells"></a><a name="MergeCells"></a><span data-ttu-id="54c45-236">6. 행렬 셀 병합</span><span class="sxs-lookup"><span data-stu-id="54c45-236">6. Merge Matrix Cells</span></span>  
 <span data-ttu-id="54c45-237">모퉁이 영역은 행렬의 왼쪽 위 모퉁이에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-237">The corner area is in the upper left corner of the matrix.</span></span> <span data-ttu-id="54c45-238">행렬의 행 및 열 그룹 수에 따라 모퉁이 영역에 있는 셀 수가 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-238">Depending on the number of row and column groups in the matrix, the number of cells in the corner area varies.</span></span> <span data-ttu-id="54c45-239">이 자습서에서 작성하는 행렬의 모퉁이 영역에는 네 개의 셀이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-239">The matrix, built in this tutorial, has four cells in its corner area.</span></span> <span data-ttu-id="54c45-240">이러한 셀은 행 및 열 그룹 계층의 깊이를 반영하여 두 개의 행과 두 개의 열로 정렬됩니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-240">The cells are arranged in two rows and two columns, reflecting the depth of row and column group hierarchies.</span></span> <span data-ttu-id="54c45-241">이 네 개의 셀은 이 보고서에서 사용되지 않으므로 한 개의 셀로 병합합니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-241">The four cells are not used in this report and you will merge them into one.</span></span>  
  
#### <a name="to-merge-matrix-cells"></a><span data-ttu-id="54c45-242">행렬 셀을 병합하려면</span><span class="sxs-lookup"><span data-stu-id="54c45-242">To merge matrix cells</span></span>  
  
1.  <span data-ttu-id="54c45-243">**디자인** 을 클릭하여 디자인 뷰로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-243">Click **Design** to return to design view.</span></span>  
  
2.  <span data-ttu-id="54c45-244">행렬을 클릭하여 열 핸들과 행 핸들이 행렬 위와 옆에 표시되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-244">Click the matrix so that column and row handles appear above and next to the matrix.</span></span>  
  
3.  <span data-ttu-id="54c45-245">Ctrl 키를 누른 상태로 네 개의 모퉁이 셀을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-245">Press the Ctrl key, and then select the four corner cells.</span></span>  
  
4.  <span data-ttu-id="54c45-246">셀을 마우스 오른쪽 단추로 클릭 한 다음 **셀 병합**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-246">Right-click the cells and then click **Merge Cells**.</span></span>  
  
5.  <span data-ttu-id="54c45-247">모퉁이 셀을 마우스 오른쪽 단추로 클릭 하 고 **입력란 속성**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-247">Right-click the corner cell, and then click **Text Box Properties**.</span></span>  
  
6.  <span data-ttu-id="54c45-248">**채우기** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-248">Click the **Fill** tab.</span></span>  
  
7.  <span data-ttu-id="54c45-249">**채우기 색**에 대해 (***fx***) 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-249">Click the (***fx***) button for **Fill color**.</span></span>  
  
8.  <span data-ttu-id="54c45-250">다음 식을 복사하여 식 상자에 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-250">Copy and paste the following expression in the expression box.</span></span>  
  
    ```  
    #96a4b2  
    ```  
  
     <span data-ttu-id="54c45-251">이 값은 Slate 스타일에 사용된 청회색에 대한 RGB 16진수 값입니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-251">This is the RGB hex value for a gray blue color used in the Slate style.</span></span>  
  
9. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
10. <span data-ttu-id="54c45-252">**실행** 을 클릭하여 보고서를 미리 봅니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-252">Click **Run** to preview your report.</span></span>  
  
 <span data-ttu-id="54c45-253">위쪽 모퉁이 행렬이 단일 셀이 되고, 색은 행 그룹 및 열 그룹 셀과 동일하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-253">The upper corner matrix is a single cell and has the same color as the row group and column group cells.</span></span>  
  
##  <a name="7-add-a-report-header-and-report-title"></a><a name="HeaderTitle"></a><span data-ttu-id="54c45-254">7. 보고서 머리글 및 보고서 제목 추가</span><span class="sxs-lookup"><span data-stu-id="54c45-254">7. Add a Report Header and Report Title</span></span>  
 <span data-ttu-id="54c45-255">보고서 제목은 보고서 맨 위에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-255">A report title appears at the top of the report.</span></span> <span data-ttu-id="54c45-256">보고서 제목을 보고서 머리글에 배치하거나, 보고서 머리글이 사용되지 않을 경우 보고서 본문의 맨 위에 있는 입력란에 배치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-256">You can place the report title in a report header or if the report does not use one, in a text box at the top of the report body.</span></span> <span data-ttu-id="54c45-257">이 자습서에서는 보고서의 위쪽에 있는 입력란을 제거하고 머리글에 제목을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-257">In this tutorial, you will remove the text box at the top of the report and add a title to the header.</span></span>  
  
#### <a name="to-add-a-report-header-and-report-title"></a><span data-ttu-id="54c45-258">보고서 머리글 및 보고서 제목을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="54c45-258">To add a report header and report title</span></span>  
  
1.  <span data-ttu-id="54c45-259">**디자인** 을 클릭하여 디자인 뷰로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-259">Click **Design** to return to design view.</span></span>  
  
2.  <span data-ttu-id="54c45-260">**제목을 추가 하려면 클릭**하십시오를 포함 하는 보고서 본문의 맨 위에 있는 입력란을 클릭 한 다음 delete 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-260">Click the text box at the top of the report body that contains **Click to add title**, and then press the Delete key.</span></span>  
  
3.  <span data-ttu-id="54c45-261">리본의 **삽입** 탭에서 **머리글** 을 클릭 한 다음 **머리글 추가**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-261">On the **Insert** tab of the ribbon, click **Header** and then click **Add Header**.</span></span>  
  
     <span data-ttu-id="54c45-262">머리글이 보고서 본문의 위쪽에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-262">A header is added to the top of the report body.</span></span>  
  
4.  <span data-ttu-id="54c45-263">**삽입** 탭에서 **입력란**을 클릭한 다음 입력란을 보고서 머리글 안으로 끌어옵니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-263">On the **Insert** tab, click **Text Box**, and then drag a text box inside the report header.</span></span> <span data-ttu-id="54c45-264">입력란의 길이와 높이를 각각 6인치와 3/4인치로 만들고 보고서 머리글의 왼쪽에 배치합니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-264">Make the text box about 6 inches long and 3/4 inch tall and place it on the left side of the report header.</span></span>  
  
5.  <span data-ttu-id="54c45-265">입력란에 **Sales by Territory, Subcategory, and Day**를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-265">In the text box, type **Sales by Territory, Subcategory, and Day**.</span></span>  
  
6.  <span data-ttu-id="54c45-266">입력 한 텍스트를 선택 하 고 마우스 오른쪽 단추를 클릭 한 다음 **텍스트 속성**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-266">Select the text you typed, right-click, and then click **Text Properties**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="54c45-267">문자의 서식을 동시에 지정하려면 문자가 연속적이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-267">To format characters at the same time, they must be contiguous.</span></span>  
  
7.  <span data-ttu-id="54c45-268">**텍스트 속성** 대화 상자에서 **글꼴**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-268">In the **Text Properties** dialog box, click **Font**.</span></span>  
  
8.  <span data-ttu-id="54c45-269">**글꼴** 목록에서 **Times New Roman**을 선택 합니다. **크기** 에서 **24 포인트**를 선택 하 고 **색** 에서 **적갈색**을 선택 하 고 **스타일** 에서 **기울임꼴**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-269">In the **Font** list, select **Times New Roman**; in **Size** select **24 pt**, in **Color** select **Maroon**, and in **Style** select **Italic**.</span></span>  
  
9. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
10. <span data-ttu-id="54c45-270">**실행** 을 클릭하여 보고서를 미리 봅니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-270">Click **Run** to preview the report.</span></span>  
  
 <span data-ttu-id="54c45-271">보고서의 보고서 머리글에 보고서 제목이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-271">The report includes a report title in the report header.</span></span>  
  
##  <a name="8-save-the-report"></a><a name="Save"></a><span data-ttu-id="54c45-272">8. 보고서 저장</span><span class="sxs-lookup"><span data-stu-id="54c45-272">8. Save the Report</span></span>  
 <span data-ttu-id="54c45-273">보고서를 보고서 서버, SharePoint 라이브러리 또는 컴퓨터에 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-273">You can save reports to a report server, SharePoint library, or your computer.</span></span>  
  
 <span data-ttu-id="54c45-274">이 자습서에서는 보고서를 보고서 서버에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-274">In this tutorial, save the report to a report server.</span></span> <span data-ttu-id="54c45-275">보고서 서버에 액세스할 수 없는 경우에는 보고서를 컴퓨터에 저장하십시오.</span><span class="sxs-lookup"><span data-stu-id="54c45-275">If you do not have access to a report server, save the report to your computer.</span></span>  
  
#### <a name="to-save-the-report-on-a-report-server"></a><span data-ttu-id="54c45-276">보고서를 보고서 서버에 저장하려면</span><span class="sxs-lookup"><span data-stu-id="54c45-276">To save the report on a report server</span></span>  
  
1.  <span data-ttu-id="54c45-277">**보고서 작성기** 단추에서 다른 **이름으로 저장**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-277">From the **Report Builder** button, click **Save As**.</span></span>  
  
2.  <span data-ttu-id="54c45-278">**최근에 사용한 사이트 및 서버**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-278">Click **Recent Sites and Servers**.</span></span>  
  
3.  <span data-ttu-id="54c45-279">보고서를 저장할 수 있는 권한을 가진 보고서 서버의 이름을 선택하거나 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-279">Select or type the name of the report server where you have permission to save reports.</span></span>  
  
     <span data-ttu-id="54c45-280">"보고서 서버에 연결하는 중"이라는 메시지가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-280">The message "Connecting to report server" appears.</span></span> <span data-ttu-id="54c45-281">연결되면 보고서 서버 관리자가 기본 보고서 위치로 지정한 보고서 폴더의 내용이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-281">When the connection is complete, you will see the contents of the report folder that the report server administrator specified as the default report location.</span></span>  
  
4.  <span data-ttu-id="54c45-282">**이름**에서 기본 이름을 **SalesByTerritorySubcategory**로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-282">In **Name**, replace the default name with **SalesByTerritorySubcategory**.</span></span>  
  
5.  <span data-ttu-id="54c45-283">**저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-283">Click **Save**.</span></span>  
  
 <span data-ttu-id="54c45-284">보고서가 보고서 서버에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-284">The report is saved to the report server.</span></span> <span data-ttu-id="54c45-285">연결된 보고서 서버의 이름이 창 아래쪽에 있는 상태 표시줄에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-285">The name of report server that you are connected to appears in the status bar at the bottom of the window.</span></span>  
  
#### <a name="to-save-the-report-on-your-computer"></a><span data-ttu-id="54c45-286">컴퓨터에 보고서를 저장하려면</span><span class="sxs-lookup"><span data-stu-id="54c45-286">To save the report on your computer</span></span>  
  
1.  <span data-ttu-id="54c45-287">**보고서 작성기** 단추에서 다른 **이름으로 저장**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-287">From the **Report Builder** button, click **Save As**.</span></span>  
  
2.  <span data-ttu-id="54c45-288">**바탕 화면**, **내 문서**또는 **내 컴퓨터**를 클릭한 다음 보고서를 저장할 폴더를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-288">Click **Desktop**, **My Documents**, or **My computer**, and then browse to the folder where you want to save the report.</span></span>  
  
3.  <span data-ttu-id="54c45-289">**이름**에서 기본 이름을 **SalesByTerritorySubcategory**로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-289">In **Name**, replace the default name with **SalesByTerritorySubcategory**.</span></span>  
  
4.  <span data-ttu-id="54c45-290">**저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-290">Click **Save**.</span></span>  
  
##  <a name="9-optional-rotate-text-box-270-degrees"></a><a name="RotateTextBox"></a><span data-ttu-id="54c45-291">9. (선택 사항) 텍스트 상자 270도 회전</span><span class="sxs-lookup"><span data-stu-id="54c45-291">9. (Optional) Rotate Text Box 270 Degrees</span></span>  
 <span data-ttu-id="54c45-292">행렬이 있는 보고서는 실행 시 가로 및 세로로 확장될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-292">A report with matrices can expand horizontally and vertically when it runs.</span></span> <span data-ttu-id="54c45-293">입력란을 세로로 회전하거나 270도 회전하면 가로 공간을 절약할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-293">By rotating text boxes vertically, or 270 degrees, you can save horizontal space.</span></span> <span data-ttu-id="54c45-294">그러면 렌더링된 보고서의 너비가 좁아지며, 보고서가 Microsoft Word 등의 형식으로 내보낼 경우 인쇄되는 페이지에 더 잘 맞게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-294">The rendered report is then narrower and if exported to a format such as Microsoft Word, will be more likely to fit on a printed page.</span></span>  
  
 <span data-ttu-id="54c45-295">입력란에서는 텍스트를 가로 및 세로(위에서 아래로)로 표시할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-295">A text box can also display text as horizontal, vertical (top to bottom).</span></span> <span data-ttu-id="54c45-296">자세한 내용은 [입력란&#40;보고서 작성기 및 SSRS&#41;](report-design/text-boxes-report-builder-and-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="54c45-296">For more information, see [Text Boxes &#40;Report Builder and SSRS&#41;](report-design/text-boxes-report-builder-and-ssrs.md).</span></span>  
  
#### <a name="to-rotate-text-box-270-degrees"></a><span data-ttu-id="54c45-297">입력란을 270도 회전하려면</span><span class="sxs-lookup"><span data-stu-id="54c45-297">To rotate text box 270 degrees</span></span>  
  
1.  <span data-ttu-id="54c45-298">**디자인** 을 클릭하여 디자인 뷰로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-298">Click **Design** to return to design view.</span></span>  
  
2.  <span data-ttu-id="54c45-299">`[Territory].`가 들어 있는 셀을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-299">Click the cell that contains `[Territory].`</span></span>  
  
3.  <span data-ttu-id="54c45-300">속성 창에서 WritingMode 속성을 찾고, 드롭다운 목록에서 **Rotate270**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-300">In the Properties pane, locate the WritingMode property and in its drop-down list, select **Rotate270**.</span></span>  
  
     <span data-ttu-id="54c45-301">속성 창이 열려 있지 않으면 리본의 **보기** 탭을 클릭하고 **속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-301">If the Properties pane is not open, click the **View** tab of the ribbon, and then select **Properties**.</span></span>  
  
4.  <span data-ttu-id="54c45-302">CanGrow 속성이로 설정 되었는지 확인 `True` 합니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-302">Verify that the CanGrow property is set to `True`.</span></span>  
  
5.  <span data-ttu-id="54c45-303">Territory 열의 너비를 1/2인치로 조정하고 열 제목을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-303">Resize the Territory column to be 1/2 inch wide and delete the column title.</span></span>  
  
6.  <span data-ttu-id="54c45-304">**실행** 을 클릭하여 보고서를 미리 봅니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-304">Click **Run** to preview your report.</span></span>  
  
 <span data-ttu-id="54c45-305">지역 이름이 아래에서 위쪽으로 세로로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-305">The territory name is written vertically, bottom to top.</span></span> <span data-ttu-id="54c45-306">Territory 행 그룹의 높이는 지역 이름의 길이에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-306">The height of the Territory row group varies by the length of the territory name.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="54c45-307">다음 단계</span><span class="sxs-lookup"><span data-stu-id="54c45-307">Next Steps</span></span>  
 <span data-ttu-id="54c45-308">이것으로 행렬 보고서를 만드는 자습서를 마칩니다.</span><span class="sxs-lookup"><span data-stu-id="54c45-308">This concludes the tutorial for how to create a matrix report.</span></span> <span data-ttu-id="54c45-309">행렬에 대 한 자세한 내용은 [테이블, 행렬 및 목록 &#40;보고서 작성기 및 ssrs&#41;](report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md), [행렬 &#40;보고서 작성기 및 ssrs&#41;](report-design/create-a-matrix-report-builder-and-ssrs.md), 테이블 [릭 스 데이터 영역 &#40;보고서 작성기 및 Ssrs&#41;](report-design/tablix-data-region-areas-report-builder-and-ssrs.md), 테이블 [릭 스 데이터 영역 셀, 행 및 열 &#40;보고서 작성기&#41; 및 ssrs](report-design/tablix-data-region-cells-rows-and-columns-report-builder-and-ssrs.md) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="54c45-309">For more information about matrices, see [Tables, Matrices, and Lists &#40;Report Builder and SSRS&#41;](report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md), [Matrices &#40;Report Builder and SSRS&#41;](report-design/create-a-matrix-report-builder-and-ssrs.md), [Tablix Data Region Areas &#40;Report Builder and SSRS&#41;](report-design/tablix-data-region-areas-report-builder-and-ssrs.md), and [Tablix Data Region Cells, Rows, and Columns &#40;Report Builder&#41; and SSRS](report-design/tablix-data-region-cells-rows-and-columns-report-builder-and-ssrs.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54c45-310">참고 항목</span><span class="sxs-lookup"><span data-stu-id="54c45-310">See Also</span></span>  
 <span data-ttu-id="54c45-311">[자습서 &#40;보고서 작성기&#41;](report-builder-tutorials.md) </span><span class="sxs-lookup"><span data-stu-id="54c45-311">[Tutorials &#40;Report Builder&#41;](report-builder-tutorials.md) </span></span>  
 [<span data-ttu-id="54c45-312">SQL Server 2014의 보고서 작성기</span><span class="sxs-lookup"><span data-stu-id="54c45-312">Report Builder in SQL Server 2014</span></span>](report-builder/report-builder-in-sql-server-2016.md)  
  
  
