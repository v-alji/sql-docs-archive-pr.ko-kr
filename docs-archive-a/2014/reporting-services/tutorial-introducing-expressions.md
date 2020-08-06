---
title: '자습서: 식 소개 | Microsoft Docs'
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 2d05ef4c-5f91-48b2-8795-f0a201a0b3cc
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 62a815800dba0730052eb812124d4561d031d0e3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737797"
---
# <a name="tutorial-introducing-expressions"></a><span data-ttu-id="853de-102">자습서: 식 소개</span><span class="sxs-lookup"><span data-stu-id="853de-102">Tutorial: Introducing Expressions</span></span>
  <span data-ttu-id="853de-103">식은 강력하고 융통성 있는 보고서를 만드는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="853de-103">Expressions help you create powerful and flexible reports.</span></span> <span data-ttu-id="853de-104">이 자습서에서는 일반 함수와 연산자를 사용하는 식을 만들고 구현하는 방법을 배웁니다.</span><span class="sxs-lookup"><span data-stu-id="853de-104">This tutorial teaches you to create and implement expressions that use common functions and operators.</span></span> <span data-ttu-id="853de-105">**식** 대화 상자를 사용 하 여 이름 값을 연결 하 고, 별도의 데이터 집합에서 값을 조회 하 고, 필드 값에 따라 다른 그림을 표시 하는 식을 작성 합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-105">You will use the **Expression** dialog box to write expressions that concatenate name values, look up values in a separate dataset, display different pictures based on field values, and so on.</span></span>  
  
 <span data-ttu-id="853de-106">보고서에는 가로줄무늬가 있으며 흰색 행과 다른 색 행이 번갈아 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="853de-106">The report is a barred report with alternating row colors in white and a color.</span></span> <span data-ttu-id="853de-107">보고서에는 흰색이 아닌 행의 색을 선택하기 위한 매개 변수가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="853de-107">The report includes a parameter for selecting the color of the non-white rows.</span></span>  
  
 <span data-ttu-id="853de-108">다음 그림에서는 만들려는 보고서와 비슷한 보고서를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="853de-108">The following illustration shows a report similar to the one you will create.</span></span>  
  
 <span data-ttu-id="853de-109">![rs_ExpressionsTutorial](../../2014/tutorials/media/rs-expressionstutorial.gif "rs_ExpressionsTutorial")</span><span class="sxs-lookup"><span data-stu-id="853de-109">![rs_ExpressionsTutorial](../../2014/tutorials/media/rs-expressionstutorial.gif "rs_ExpressionsTutorial")</span></span>  
  
##  <a name="what-you-will-learn"></a><a name="BackToTop"></a><span data-ttu-id="853de-110">학습 내용</span><span class="sxs-lookup"><span data-stu-id="853de-110">What You Will Learn</span></span>  
 <span data-ttu-id="853de-111">이 자습서에서는 다음 작업 방법을 배웁니다.</span><span class="sxs-lookup"><span data-stu-id="853de-111">In this tutorial you will learn how to do the following:</span></span>  
  
1.  [<span data-ttu-id="853de-112">테이블 또는 행렬 마법사에서 테이블 보고서 및 데이터 세트 만들기</span><span class="sxs-lookup"><span data-stu-id="853de-112">Create a Table Report and Dataset from the Table or Matrix Wizard</span></span>](#Setup)  
  
2.  [<span data-ttu-id="853de-113">데이터 원본 및 데이터 세트의 기본 이름 업데이트</span><span class="sxs-lookup"><span data-stu-id="853de-113">Update Default Names of the Data Source and Dataset</span></span>](#UpdateNames)  
  
3.  [<span data-ttu-id="853de-114">이름, 이니셜 및 성 표시</span><span class="sxs-lookup"><span data-stu-id="853de-114">Display First Name, Initial, and Last Name</span></span>](#Concatenate)  
  
4.  [<span data-ttu-id="853de-115">이미지를 사용하여 성별 표시</span><span class="sxs-lookup"><span data-stu-id="853de-115">Use Images to Display Gender</span></span>](#Gender)  
  
5.  [<span data-ttu-id="853de-116">CountryRegion 이름 조회</span><span class="sxs-lookup"><span data-stu-id="853de-116">Look Up CountryRegion Name</span></span>](#Lookup)  
  
6.  [<span data-ttu-id="853de-117">마지막 구입 이후 일수 계산</span><span class="sxs-lookup"><span data-stu-id="853de-117">Count Days Since Last Purchase</span></span>](#Count)  
  
7.  [<span data-ttu-id="853de-118">표시기를 사용하여 판매량 비교 표시</span><span class="sxs-lookup"><span data-stu-id="853de-118">Use an Indicator to Show Sales Comparison</span></span>](#Indicator)  
  
8.  [<span data-ttu-id="853de-119">보고서를 "녹색 막대" 보고서로 만들기</span><span class="sxs-lookup"><span data-stu-id="853de-119">Make the Report a "Green Bar" Report</span></span>](#GreenBar)  
  
### <a name="other-optional-steps"></a><span data-ttu-id="853de-120">기타 선택적 단계</span><span class="sxs-lookup"><span data-stu-id="853de-120">Other Optional Steps</span></span>  
  
-   [<span data-ttu-id="853de-121">날짜 열 서식 지정</span><span class="sxs-lookup"><span data-stu-id="853de-121">Format Date Column</span></span>](#DateFormat)  
  
-   [<span data-ttu-id="853de-122">보고서 제목 추가</span><span class="sxs-lookup"><span data-stu-id="853de-122">Add a Report Title</span></span>](#Title)  
  
-   [<span data-ttu-id="853de-123">보고서 저장</span><span class="sxs-lookup"><span data-stu-id="853de-123">Save the Report</span></span>](#Save)  
  
 <span data-ttu-id="853de-124">이 자습서에 소요되는 예상 시간: 30분</span><span class="sxs-lookup"><span data-stu-id="853de-124">Estimated time to complete this tutorial: 30 minutes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="853de-125">요구 사항</span><span class="sxs-lookup"><span data-stu-id="853de-125">Requirements</span></span>  
 <span data-ttu-id="853de-126">요구 사항에 대한 자세한 내용은 [자습서의 필수 조건&#40;보고서 작성기&#41;](../reporting-services/report-builder-tutorials.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="853de-126">For information about requirements, see [Prerequisites for Tutorials &#40;Report Builder&#41;](../reporting-services/report-builder-tutorials.md).</span></span>  
  
##  <a name="1-create-a-table-report-and-dataset-from-the-table-or-matrix-wizard"></a><a name="Setup"></a><span data-ttu-id="853de-127">1. 테이블 또는 행렬 마법사에서 테이블 보고서 및 데이터 집합 만들기</span><span class="sxs-lookup"><span data-stu-id="853de-127">1. Create a Table Report and Dataset from the Table or Matrix Wizard</span></span>  
 <span data-ttu-id="853de-128">테이블 보고서, 데이터 원본 및 데이터 세트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="853de-128">Create a table report, a data source, and a dataset.</span></span> <span data-ttu-id="853de-129">테이블의 레이아웃을 지정할 때는 몇몇 필드만 포함하고,</span><span class="sxs-lookup"><span data-stu-id="853de-129">When you lay out the table, you will include only a few fields.</span></span> <span data-ttu-id="853de-130">마법사를 완료한 후 열을 수동으로 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-130">After you complete the wizard you will manually add columns.</span></span> <span data-ttu-id="853de-131">마법사에서는 손쉽게 테이블의 레이아웃을 지정하고 스타일을 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="853de-131">The wizard makes it easy for you to lay out the table and apply a style.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="853de-132">이 자습서의 쿼리에는 데이터 값이 포함되어 있으므로 외부 데이터 원본이 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="853de-132">In this tutorial, the query contains the data values, so that it does not need an external data source.</span></span> <span data-ttu-id="853de-133">따라서 쿼리가 상당히 길어집니다.</span><span class="sxs-lookup"><span data-stu-id="853de-133">This makes the query quite long.</span></span> <span data-ttu-id="853de-134">비즈니스 환경에서는 쿼리에 데이터가 포함되지 않을 것입니다.</span><span class="sxs-lookup"><span data-stu-id="853de-134">In a business environment, a query would not contain the data.</span></span> <span data-ttu-id="853de-135">이 자습서의 쿼리는 학습용으로만 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="853de-135">This is for learning purposes only.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="853de-136">이 자습서에서 마법사의 단계는 하나의 절차로 통합됩니다.</span><span class="sxs-lookup"><span data-stu-id="853de-136">In this tutorial, the steps for the wizard are consolidated into one procedure.</span></span> <span data-ttu-id="853de-137">보고서 서버를 찾고, 데이터 원본을 선택하고, 데이터 세트를 만드는 방법에 대한 단계별 지침은 이 시리즈의 첫 번째 자습서인 [자습서: 기본 테이블 보고서 만들기&#40;보고서 작성기&#41;](../reporting-services/tutorial-creating-a-basic-table-report-report-builder.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="853de-137">For step-by-step instructions about how to browse to a report server, choose a data source, and create a dataset, see the first tutorial in this series: [Tutorial: Creating a Basic Table Report &#40;Report Builder&#41;](../reporting-services/tutorial-creating-a-basic-table-report-report-builder.md).</span></span>  
  
#### <a name="to-create-a-new-table-report"></a><span data-ttu-id="853de-138">새 테이블 보고서를 만들려면</span><span class="sxs-lookup"><span data-stu-id="853de-138">To create a new table report</span></span>  
  
1.  <span data-ttu-id="853de-139">**시작**을 클릭 하 고 **프로그램**, [!INCLUDE[ssCurrentUI](../includes/sscurrentui-md.md)] **보고서 작성기**을 차례로 가리킨 다음 **보고서 작성기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-139">Click **Start**, point to **Programs**, click [!INCLUDE[ssCurrentUI](../includes/sscurrentui-md.md)]**Report Builder**, and then click **Report Builder**.</span></span>  
  
     <span data-ttu-id="853de-140">**시작** 대화 상자가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="853de-140">The **Getting Started** dialog box appears.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="853de-141">**시작** 대화 상자가 나타나지 않으면 **보고서 작성기** 단추에서 **새로 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-141">If the **Getting Started** dialog box does not appear, from the **Report Builder** button, click **New**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="853de-142">보고서 작성기 ClickOnce 버전을 사용 하는 것을 선호 하는 경우 보고서 관리자를 열고 **보고서 작성기**를 클릭 하거나, 보고서와 같은 Reporting Services 내용 유형이 설정 된 SharePoint 사이트로 이동 하 고 공유 문서 라이브러리의 **문서** 탭에 있는 **새 문서** 메뉴에서 **보고서 작성기 보고서** 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-142">If you prefer using the ClickOnce version of Report Builder, open Report Manager and click **Report Builder**, or go to a SharePoint site on which Reporting Services content types such as reports are enabled and click **Report Builder Report** on the **New Document** menu on the **Documents** tab of a shared documents library.</span></span>  
  
2.  <span data-ttu-id="853de-143">왼쪽 창에 **새 보고서** 가 선택되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-143">In the left pane, verify that **New Report** is selected.</span></span>  
  
3.  <span data-ttu-id="853de-144">오른쪽 창에서 **테이블 또는 행렬 마법사**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-144">In the right pane, click **Table or Matrix Wizard**.</span></span>  
  
4.  <span data-ttu-id="853de-145">**데이터 세트 선택** 페이지에서 **데이터 세트 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-145">On the **Choose a dataset** page, click **Create a dataset**.</span></span>  
  
5.  <span data-ttu-id="853de-146">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-146">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="853de-147">**데이터 원본에 대한 연결 선택** 페이지에서 **SQL Server**형식의 데이터 원본을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-147">On the **Choose a connection to a data source** page, select a data source that is type **SQL Server**.</span></span> <span data-ttu-id="853de-148">목록에서 데이터 원본을 선택하거나 보고서 서버를 찾아 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-148">Select a data source from the list or browse to the report server to select one.</span></span>  
  
7.  <span data-ttu-id="853de-149">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-149">Click **Next**.</span></span>  
  
8.  <span data-ttu-id="853de-150">**쿼리 디자인** 페이지에서 **텍스트로 편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-150">On the **Design a query** page, click **Edit as Text**.</span></span>  
  
9. <span data-ttu-id="853de-151">쿼리 창에 다음 쿼리를 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="853de-151">Paste the following query into the query pane:</span></span>  
  
    ```  
    SELECT 'Lauren' AS FirstName,'Johnson' AS LastName, 'American Samoa' AS StateProvince, 1 AS CountryRegionID,'Unknown' AS Gender, CAST(9996.60 AS money) AS YTDPurchase, CAST('2010-6-10' AS date) AS LastPurchase  
    UNION SELECT'Warren' AS FirstName, 'Pal' AS LastName, 'New South Wales' AS StateProvince, 2 AS CountryRegionID, 'Male' AS Gender, CAST(5747.25 AS money) AS YTDPurchase, CAST('2010-7-3' AS date) AS LastPurchase  
    UNION SELECT 'Fernando' AS FirstName, 'Ross' AS LastName, 'Alberta' AS StateProvince, 3 AS CountryRegionID, 'Male' AS Gender, CAST(9248.15 AS money) AS YTDPurchase, CAST('2010-10-17' AS date) AS LastPurchase  
    UNION SELECT 'Rob' AS FirstName, 'Caron' AS LastName, 'Northwest Territories' AS StateProvince, 3 AS CountryRegionID, 'Male' AS Gender, CAST(742.50 AS money) AS YTDPurchase, CAST('2010-4-29' AS date) AS LastPurchase  
    UNION SELECT 'James' AS FirstName, 'Bailey' AS LastName, 'British Columbia' AS StateProvince, 3 AS CountryRegionID, 'Male' AS Gender, CAST(1147.50 AS money) AS YTDPurchase, CAST('2010-6-15' AS date) AS LastPurchase  
    UNION SELECT  'Bridget' AS FirstName, 'She' AS LastName, 'Hamburg' AS StateProvince, 4 AS CountryRegionID, 'Female' AS Gender, CAST(7497.30 AS money) AS YTDPurchase, CAST('2010-5-10' AS date) AS LastPurchase  
    UNION SELECT 'Alexander' AS FirstName, 'Martin' AS LastName, 'Saxony' AS StateProvince, 4 AS CountryRegionID, 'Male' AS Gender, CAST(2997.60 AS money) AS YTDPurchase, CAST('2010-11-19' AS date) AS LastPurchase  
    UNION SELECT 'Yolanda' AS FirstName, 'Sharma' AS LastName ,'Micronesia' AS StateProvince, 5 AS CountryRegionID, 'Female' AS Gender, CAST(3247.95 AS money) AS YTDPurchase, CAST('2010-8-23' AS date) AS LastPurchase  
    UNION SELECT 'Marc' AS FirstName, 'Zimmerman' AS LastName, 'Moselle' AS StateProvince, 6 AS CountryRegionID, 'Male' AS Gender, CAST(1200.00 AS money) AS YTDPurchase, CAST('2010-11-16' AS date) AS LastPurchase  
    UNION SELECT 'Katherine' AS FirstName, 'Abel' AS LastName, 'Moselle' AS StateProvince, 6 AS CountryRegionID, 'Female' AS Gender, CAST(2025.00 AS money) AS YTDPurchase, CAST('2010-12-1' AS date) AS LastPurchase  
    UNION SELECT 'Nicolas' as FirstName, 'Anand' AS LastName, 'Seine (Paris)' AS StateProvince, 6 AS CountryRegionID, 'Male' AS Gender, CAST(1425.00 AS money) AS YTDPurchase, CAST('2010-12-11' AS date) AS LastPurchase  
    UNION SELECT 'James' AS FirstName, 'Peters' AS LastName, 'England' AS StateProvince, 12 AS CountryRegionID, 'Male' AS Gender, CAST(887.50 AS money) AS YTDPurchase, CAST('2010-8-15' AS date) AS LastPurchase  
    UNION SELECT 'Alison' AS FirstName, 'Nath' AS LastName, 'Alaska' AS StateProvince, 7 AS CountryRegionID, 'Female' AS Gender, CAST(607.50 AS money) AS YTDPurchase, CAST('2010-10-13' AS date) AS LastPurchase  
    UNION SELECT 'Grace' AS FirstName, 'Patterson' AS LastName, 'Kansas' AS StateProvince, 7 AS CountryRegionID, 'Female' AS Gender, CAST(1215.00 AS money) AS YTDPurchase, CAST('2010-10-18' AS date) AS LastPurchase  
    UNION SELECT 'Bobby' AS FirstName, 'Sanchez' AS LastName, 'North Dakota' AS StateProvince, 7 AS CountryRegionID, 'Female' AS Gender, CAST(6191.00 AS money) AS YTDPurchase, CAST('2010-9-17' AS date) AS LastPurchase  
    UNION SELECT 'Charles' AS FirstName, 'Reed' AS LastName, 'Nebraska' AS StateProvince, 7 AS CountryRegionID, 'Male' AS Gender, CAST(8772.00 AS money) AS YTDPurchase, CAST('2010-8-27' AS date) AS LastPurchase  
    UNION SELECT 'Orlando' AS FirstName, 'Romeo' AS LastName, 'Texas' AS StateProvince, 7 AS CountryRegionID, 'Male' AS Gender, CAST(8578.00 AS money) AS YTDPurchase, CAST('2010-7-29' AS date) AS LastPurchase  
    UNION SELECT 'Cynthia' AS FirstName, 'Randall' AS LastName, 'Utah' AS StateProvince, 7 AS CountryRegionID, 'Female' AS Gender, CAST(7218.10 AS money) AS YTDPurchase, CAST('2010-1-11' AS date) AS LastPurchase  
    UNION SELECT 'Rebecca' AS FirstName, 'Roberts' AS LastName, 'Washington' AS StateProvince, 7 AS CountryRegionID, 'Female' AS Gender, CAST(8357.80 AS money) AS YTDPurchase, CAST('2010-10-28' AS date) AS LastPurchase  
    UNION SELECT 'Cristian' AS FirstName, 'Petulescu' AS LastName, 'Wisconsin' AS StateProvince, 7 AS CountryRegionID, 'Male' AS Gender, CAST(3470.00 AS money) AS YTDPurchase, CAST('2010-11-30' AS date) AS LastPurchase  
    UNION SELECT 'Cynthia' AS FirstName, 'Randall' AS LastName, 'Utah' AS StateProvince, 7 AS CountryRegionID, 'Female' AS Gender, CAST(7218.10 AS money) AS YTDPurchase, CAST('2010-1-11' AS date) AS LastPurchase  
    UNION SELECT 'Rebecca' AS FirstName, 'Roberts' AS LastName, 'Washington' AS StateProvince, 7 AS CountryRegionID, 'Female' AS Gender, CAST(8357.80 AS money) AS YTDPurchase, CAST('2010-10-28' AS date) AS LastPurchase  
    UNION SELECT 'Cristian' AS FirstName, 'Petulescu' AS LastName, 'Wisconsin' AS StateProvince, 7 AS CountryRegionID, 'Male' AS Gender, CAST(3470.00 AS money) AS YTDPurchase, CAST('2010-11-30' AS date) AS LastPurchase  
    ```  
  
     <span data-ttu-id="853de-152">이 쿼리에서는 생일, 이름, 성, 시/도, 국가/지역 식별자, 성별 및 구매량 연간 누계를 포함하는 열 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-152">The query specifies column names that include a birth date, first name, last name, state or province, country/region identifier, gender, and year-to-date purchases.</span></span>  
  
10. <span data-ttu-id="853de-153">쿼리 디자이너 도구 모음에서 **실행** (**!**)을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-153">On the query designer toolbar, click **Run** (**!**).</span></span> <span data-ttu-id="853de-154">결과 집합에는 20행의 데이터가 표시되고 FirstName, LastName, StateProvince, CountryRegionID, Gender, YTDPurchase 및 LastPurchase 열이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="853de-154">The result set displays 20 rows of data and includes the following columns: FirstName, LastName, StateProvince, CountryRegionID, Gender, YTDPurchase, and LastPurchase.</span></span>  
  
11. <span data-ttu-id="853de-155">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-155">Click **Next**.</span></span>  
  
12. <span data-ttu-id="853de-156">**필드 정렬** 페이지에서 다음 필드를 지정된 순서에 따라 **사용 가능한 필드** 목록에서 **값** 목록으로 끌어옵니다.</span><span class="sxs-lookup"><span data-stu-id="853de-156">On the **Arrange fields** page, drag the following fields, in the specified order, from the **Available Fields** list to the **Values** list.</span></span>  
  
    -   <span data-ttu-id="853de-157">StateProvince</span><span class="sxs-lookup"><span data-stu-id="853de-157">StateProvince</span></span>  
  
    -   <span data-ttu-id="853de-158">CountryRegionID</span><span class="sxs-lookup"><span data-stu-id="853de-158">CountryRegionID</span></span>  
  
    -   <span data-ttu-id="853de-159">LastPurchase</span><span class="sxs-lookup"><span data-stu-id="853de-159">LastPurchase</span></span>  
  
    -   <span data-ttu-id="853de-160">YTDPurchase</span><span class="sxs-lookup"><span data-stu-id="853de-160">YTDPurchase</span></span>  
  
     <span data-ttu-id="853de-161">CountryRegionID 및 YTDPurchase는 숫자 데이터를 포함하므로 SUM 집계가 기본적으로 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="853de-161">Because the CountryRegionID and YTDPurchase contain numeric data, the SUM aggregate is applied to them by default.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="853de-162">FirstName 및 LastName 필드는 포함되지 않으며,</span><span class="sxs-lookup"><span data-stu-id="853de-162">The FirstName and LastName fields are not included.</span></span> <span data-ttu-id="853de-163">이후 단계에서 두 필드를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-163">You will add them in a later step.</span></span>  
  
13. <span data-ttu-id="853de-164">**값** 목록에서를 마우스 오른쪽 단추로 클릭 `CountryRegionID` 하 고 **Sum** 옵션을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-164">In the **Values** list, right-click `CountryRegionID` and click the **Sum** option.</span></span>  
  
     <span data-ttu-id="853de-165">Sum은 더 이상 CountryRegionID에 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="853de-165">Sum is no longer applied to CountryRegionID.</span></span>  
  
14. <span data-ttu-id="853de-166">**값** 목록에서 **YTDPurchase** 를 마우스 오른쪽 단추로 클릭하고 **Sum** 옵션을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-166">In the **Values** list, right-click **YTDPurchase** and click the **Sum** option.</span></span>  
  
     <span data-ttu-id="853de-167">Sum은 더 이상 YTDPurchase에 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="853de-167">Sum is no longer applied to YTDPurchase.</span></span>  
  
15. <span data-ttu-id="853de-168">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-168">Click **Next**.</span></span>  
  
16. <span data-ttu-id="853de-169">**레이아웃 선택** 페이지에서 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-169">On the **Choose the layout** page, click **Next**.</span></span>  
  
17. <span data-ttu-id="853de-170">**스타일 선택** 페이지에서 **슬레이트**를 클릭 한 다음 **마침**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-170">On the **Choose a style** page, click **Slate**, and then click **Finish**.</span></span>  
  
##  <a name="2-update-default-names-of-the-data-source-and-dataset"></a><a name="UpdateNames"></a><span data-ttu-id="853de-171">2. 데이터 원본 및 데이터 집합의 기본 이름 업데이트</span><span class="sxs-lookup"><span data-stu-id="853de-171">2. Update Default Names of the Data Source and Dataset</span></span>  
  
#### <a name="to-update-the-default-name-of-the-data-source"></a><span data-ttu-id="853de-172">데이터 원본의 기본 이름을 업데이트하려면</span><span class="sxs-lookup"><span data-stu-id="853de-172">To update the default name of the data source</span></span>  
  
1.  <span data-ttu-id="853de-173">보고서 데이터 창에서 **데이터 원본**을 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-173">In the Report Data pane, expand **Data Sources**.</span></span>  
  
2.  <span data-ttu-id="853de-174">**DataSource1** 을 마우스 오른쪽 단추로 클릭하고 **데이터 원본 속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-174">Right-click **DataSource1** and click **Data Source Properties.**</span></span>  
  
3.  <span data-ttu-id="853de-175">**이름** 상자에 **ExpressionsDataSource**를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-175">In the **Name** box, type **ExpressionsDataSource**</span></span>  
  
4.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
#### <a name="to-update-the-default-name-of-the-dataset"></a><span data-ttu-id="853de-176">데이터 세트의 기본 이름을 업데이트하려면</span><span class="sxs-lookup"><span data-stu-id="853de-176">To update the default name of the dataset</span></span>  
  
1.  <span data-ttu-id="853de-177">보고서 데이터 창에서 **데이터 세트**를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-177">In the Report Data pane, expand **Datasets**.</span></span>  
  
2.  <span data-ttu-id="853de-178">**DataSet1**을 마우스 오른쪽 단추로 클릭하고 **데이터 세트 속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-178">Right-click **DataSet1** and click **Dataset Properties.**</span></span>  
  
3.  <span data-ttu-id="853de-179">**이름** 상자에 **Expressions**를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-179">In the **Name** box, type **Expressions**</span></span>  
  
4.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
##  <a name="3-display-first-name-initial-and-last-name"></a><a name="Concatenate"></a><span data-ttu-id="853de-180">3. 이름, 이니셜 및 성 표시</span><span class="sxs-lookup"><span data-stu-id="853de-180">3. Display First Name, Initial, and Last Name</span></span>  
 <span data-ttu-id="853de-181">이니셜과 성을 포함하는 이름으로 계산되는 식에서 **Left** 함수와 **Concatenate**(**&**) 연산자를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-181">Use the **Left** function and the **Concatenate** (**&**) operator in an expression that evaluates to a name that includes an initial and a last name.</span></span> <span data-ttu-id="853de-182">단계별로 식을 작성하거나 절차에서 단계를 건너뛰고 자습서의 식을 복사하여 **식** 대화 상자에 붙여넣을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="853de-182">You can build the expression step by step or skip ahead in the procedure and copy/paste the expression from the tutorial into the **Expression** dialog box.</span></span>  
  
#### <a name="to-add-the-name-column"></a><span data-ttu-id="853de-183">Name 열을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="853de-183">To add the Name column</span></span>  
  
1.  <span data-ttu-id="853de-184">**StateProvince** 열을 마우스 오른쪽 단추로 클릭하고 **열 삽입**을 가리킨 다음 **왼쪽**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-184">Right-click the **StateProvince** column, point to **Insert Column**, and then click **Left**.</span></span>  
  
     <span data-ttu-id="853de-185">새 열이 **StateProvince** 열의 왼쪽에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="853de-185">A new column is added to the left of the **StateProvince** column.</span></span>  
  
2.  <span data-ttu-id="853de-186">새 열의 제목을 클릭하고 **Name**을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-186">Click the title of the new column and type **Name**</span></span>  
  
3.  <span data-ttu-id="853de-187">**Name** 열의 데이터 셀을 마우스 오른쪽 단추로 클릭하고 **식**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-187">Right-click the data cell for the **Name** column and click **Expression**.</span></span>  
  
4.  <span data-ttu-id="853de-188">**식** 대화 상자에서 **일반 함수**를 확장하고 **텍스트**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-188">In the **Expression** dialog box, expand **Common Functions**, and then click **Text**.</span></span>  
  
5.  <span data-ttu-id="853de-189">**항목** 목록에서 **Left**를 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-189">In the **Item** list, double-click **Left**.</span></span>  
  
     <span data-ttu-id="853de-190">**Left** 함수가 식에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="853de-190">The **Left** function is added to the expression.</span></span>  
  
6.  <span data-ttu-id="853de-191">**범주** 목록에서 **필드(식)** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-191">In the **Category** list, click **Fields (Expressions)**.</span></span>  
  
7.  <span data-ttu-id="853de-192">**값** 목록에서 **FirstName**을 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-192">In the **Values** list, double-click **FirstName**.</span></span>  
  
8.  <span data-ttu-id="853de-193">**, 1)** 을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-193">Type **, 1)**</span></span>  
  
     <span data-ttu-id="853de-194">이 식은 **FirstName** 값에서 가장 왼쪽의 한 자를 추출합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-194">This expression extracts one character from the **FirstName** value, counting from the left.</span></span>  
  
9. <span data-ttu-id="853de-195">**&" "&** 를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-195">Type **&" "&**</span></span>  
  
10. <span data-ttu-id="853de-196">**값** 목록에서 **LastName**을 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-196">In the **Values** list, double-click **LastName**.</span></span>  
  
     <span data-ttu-id="853de-197">완성된 식은 다음과 같습니다. `=Left(Fields!FirstName.Value, 1) &" "& Fields!LastName.Value`</span><span class="sxs-lookup"><span data-stu-id="853de-197">The completed expression: `=Left(Fields!FirstName.Value, 1) &" "& Fields!LastName.Value`</span></span>  
  
11. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
12. <span data-ttu-id="853de-198">**실행** 을 클릭하여 보고서를 미리 봅니다.</span><span class="sxs-lookup"><span data-stu-id="853de-198">Click **Run** to preview the report.</span></span>  
  
##  <a name="4-use-images-to-display-gender"></a><a name="Gender"></a><span data-ttu-id="853de-199">4. 이미지를 사용 하 여 성별 표시</span><span class="sxs-lookup"><span data-stu-id="853de-199">4. Use Images to Display Gender</span></span>  
 <span data-ttu-id="853de-200">이미지를 사용하여 사용자의 성별을 표시하고 제3의 이미지를 사용하여 알 수 없는 성별 값을 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-200">Use images to show the gender of a person, and identify unknown gender values by using a third image.</span></span> <span data-ttu-id="853de-201">보고서에 세 개의 숨겨진 이미지와 새 열을 추가하여 이미지를 표시한 다음 Gender 필드의 값에 따라 열에 나타나는 이미지를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-201">You will add to the report three hidden images and a new column to display the images, and then determine the image that appears in the column based on the value of the Gender field.</span></span>  
  
 <span data-ttu-id="853de-202">보고서를 가로줄무늬가 있는 보고서로 만들 때 이미지가 포함된 테이블 셀에 색을 적용하려면 사각형을 추가한 다음 이미지를 사각형에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-202">To apply a color to the table cell that contains the image when you make the report a barred report, you will add a rectangle and then add the image to the rectangle.</span></span> <span data-ttu-id="853de-203">배경색을 사각형에 적용할 수 있지만 이미지에는 적용할 수 없기 때문에 사각형을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-203">You need to use a rectangle because you can apply a background color to a rectangle, but not to an image.</span></span>  
  
 <span data-ttu-id="853de-204">이 자습서에서는 Windows와 함께 설치된 이미지를 사용하지만 사용 가능한 어떠한 이미지라도 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="853de-204">The tutorial uses images that are installed with Windows, but you can use any images available to you.</span></span> <span data-ttu-id="853de-205">포함 이미지를 사용하지만 포함 이미지가 로컬 컴퓨터나 보고서 서버에 설치되어 있지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="853de-205">You will use embedded images, and they do not need to be installed on your local computer or the report server.</span></span>  
  
#### <a name="to-add-images-to-the-report-body"></a><span data-ttu-id="853de-206">보고서 본문에 이미지를 추가하려면</span><span class="sxs-lookup"><span data-stu-id="853de-206">To add images to the report body</span></span>  
  
1.  <span data-ttu-id="853de-207">**디자인** 을 클릭하여 디자인 뷰로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="853de-207">Click **Design** to return to design view.</span></span>  
  
2.  <span data-ttu-id="853de-208">리본의 **삽입** 탭에서 **이미지**를 클릭한 다음 보고서 본문에서 테이블 아래를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-208">On the **Insert** tab of the ribbon, click **Image** and then click in the report body, below the table.</span></span>  
  
     <span data-ttu-id="853de-209">**이미지 속성** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="853de-209">The **Image Properties** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="853de-210">**가져오기**를 클릭하고 C:\Users\Public\Public Pictures\Sample Pictures로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-210">Click **Import** and navigate to C:\Users\Public\Public Pictures\Sample Pictures.</span></span>  
  
4.  <span data-ttu-id="853de-211">Penguins.JPG를 클릭하고 **열기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-211">Click Penguins.JPG and click **Open**.</span></span>  
  
     <span data-ttu-id="853de-212">**이미지 속성** 대화 상자에서 **표시 유형**을 클릭한 다음 **숨기기** 옵션을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-212">In the **Image Properties** dialog box, click **Visibility** and then click the **Hide** option.</span></span>  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
6.  <span data-ttu-id="853de-213">2~5단계를 반복하되 Koala.JPG를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-213">Repeat steps 2 through 5, but choose Koala.JPG.</span></span>  
  
7.  <span data-ttu-id="853de-214">2~5단계를 반복하되 Tulips.JPG를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-214">Repeat steps 2 through 5, but choose Tulips.JPG.</span></span>  
  
#### <a name="to-add-the-gender-column"></a><span data-ttu-id="853de-215">Gender 열을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="853de-215">To add the Gender column</span></span>  
  
1.  <span data-ttu-id="853de-216">**Name** 열을 마우스 오른쪽 단추로 클릭하고 **열 삽입**을 가리킨 다음 **오른쪽**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-216">Right-click the **Name** column, point to **Insert Column**, and then click **Right**.</span></span>  
  
     <span data-ttu-id="853de-217">새 열이 **Name** 열의 오른쪽에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="853de-217">A new column is added to the right of the **Name** column.</span></span>  
  
2.  <span data-ttu-id="853de-218">새 열의 제목을 클릭하고 **Gender**를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-218">Click the title of the new column and type **Gender**</span></span>  
  
#### <a name="to-add-a-rectangle"></a><span data-ttu-id="853de-219">사각형을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="853de-219">To add a rectangle</span></span>  
  
-   <span data-ttu-id="853de-220">리본의 **삽입** 탭에서 **사각형**을 클릭한 다음 **Gender** 열의 데이터 셀을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-220">On the **Insert** tab of the ribbon, click **Rectangle** and then click in the data cell of the **Gender** column.</span></span>  
  
     <span data-ttu-id="853de-221">셀에 사각형이 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="853de-221">A rectangle is added to the cell.</span></span>  
  
#### <a name="to-add-an-image-to-the-rectangle"></a><span data-ttu-id="853de-222">사각형에 이미지를 추가하려면</span><span class="sxs-lookup"><span data-stu-id="853de-222">To add an image to the rectangle</span></span>  
  
1.  <span data-ttu-id="853de-223">사각형을 마우스 오른쪽 단추로 클릭하고 **삽입**을 가리킨 다음 **이미지**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-223">Right-click in the rectangle, point to **Insert**, and then click **Image**.</span></span>  
  
2.  <span data-ttu-id="853de-224">**이미지 속성** 대화 상자에서 **이 이미지 사용** 옆의 아래쪽 화살표를 클릭하고 추가한 이미지 중 하나(예: Penguins.JPG)를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-224">In the **Image Properties** dialog box, click the down arrow beside **Use this image**, and select one of the images you added, for example, Penguins.JPG.</span></span>  
  
3.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
#### <a name="to-use-images-to-show-gender"></a><span data-ttu-id="853de-225">이미지를 사용하여 성별을 표시하려면</span><span class="sxs-lookup"><span data-stu-id="853de-225">To use images to show gender</span></span>  
  
1.  <span data-ttu-id="853de-226">**Gender** 열에서 데이터 셀의 이미지를 마우스 오른쪽 단추로 클릭하고 **이미지 속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-226">Right-click the image in the data cell in the **Gender** column and click **Image Properties**.</span></span>  
  
2.  <span data-ttu-id="853de-227">**이미지 속성** 대화 상자에서 **이 이미지 사용** 입력란 옆에 있는 식 단추(**fx**)를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-227">In the **Image Properties** dialog box, click the expression **fx** button next to the **Use this image** text box.</span></span>  
  
3.  <span data-ttu-id="853de-228">**식** 대화 상자에서 **일반 함수** 를 확장하고 **프로그램 흐름**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-228">In the **Expression** dialog box, expand **Common Functions** and click **Program Flow**.</span></span>  
  
4.  <span data-ttu-id="853de-229">**항목** 목록에서 **Switch**를 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-229">In the **Item** list, double-click **Switch**.</span></span>  
  
5.  <span data-ttu-id="853de-230">**범주** 목록에서 **필드(식)** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-230">In the **Category** list, click **Fields (Expressions)**.</span></span>  
  
6.  <span data-ttu-id="853de-231">**값** 목록에서 **Gender**를 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-231">In the **Values** list, double-click **Gender**.</span></span>  
  
7.  <span data-ttu-id="853de-232">**="Male", "Koala",** 를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-232">Type **="Male", "Koala",**</span></span>  
  
8.  <span data-ttu-id="853de-233">**값** 목록에서 **Gender**를 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-233">In the **Values** list, double-click **Gender**.</span></span>  
  
9. <span data-ttu-id="853de-234">**="Female", "Penguins",** 를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-234">Type **="Female", "Penguins",**</span></span>  
  
10. <span data-ttu-id="853de-235">**값** 목록에서 **Gender**를 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-235">In the **Values** list, double-click **Gender**.</span></span>  
  
11. <span data-ttu-id="853de-236">**="Unknown", "Tulips")** 를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-236">Type **="Unknown", "Tulips")**</span></span>  
  
     <span data-ttu-id="853de-237">완성된 식은 다음과 같습니다. `=Switch(Fields!Gender.Value ="Male", "Koala",Fields!Gender.Value ="Female","Penguins",Fields!Gender.Value ="Unknown","Tulips")`</span><span class="sxs-lookup"><span data-stu-id="853de-237">The completed expression: `=Switch(Fields!Gender.Value ="Male", "Koala",Fields!Gender.Value ="Female","Penguins",Fields!Gender.Value ="Unknown","Tulips")`</span></span>  
  
12. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
13. <span data-ttu-id="853de-238">**확인**을 다시 클릭하여 **이미지 속성** 대화 상자를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="853de-238">Click **OK** again to close the **Image Properties** dialog box.</span></span>  
  
14. <span data-ttu-id="853de-239">**실행** 을 클릭하여 보고서를 미리 봅니다.</span><span class="sxs-lookup"><span data-stu-id="853de-239">Click **Run** to preview the report.</span></span>  
  
##  <a name="5-look-up-countryregion-name"></a><a name="Lookup"></a><span data-ttu-id="853de-240">5. CountryRegion 이름 조회</span><span class="sxs-lookup"><span data-stu-id="853de-240">5. Look Up CountryRegion Name</span></span>  
 <span data-ttu-id="853de-241">CountryRegion 데이터 세트를 만들고 **Lookup** 함수를 사용하여 국가/지역의 식별자 대신 국가/지역의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-241">Create the CountryRegion dataset and use the **Lookup** function to display the name of a country/region instead of the identifier of the country/region.</span></span>  
  
#### <a name="to-create-the-countryregion-dataset"></a><span data-ttu-id="853de-242">CountryRegion 데이터 세트를 만들려면</span><span class="sxs-lookup"><span data-stu-id="853de-242">To create the CountryRegion dataset</span></span>  
  
1.  <span data-ttu-id="853de-243">**디자인** 을 클릭하여 디자인 뷰로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="853de-243">Click **Design** to return to design view.</span></span>  
  
2.  <span data-ttu-id="853de-244">보고서 데이터 창에서 **새로 만들기**를 클릭한 다음, **데이터 세트**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-244">In the Report Data pane, click **New** and then click **Dataset**.</span></span>  
  
3.  <span data-ttu-id="853de-245">**내 보고서에 포함된 데이터 집합 사용**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-245">Click **Use a dataset embedded in my report**.</span></span>  
  
4.  <span data-ttu-id="853de-246">**데이터 원본** 목록에서 ExpressionsDataSource를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-246">In the **Data source** list, select ExpressionsDataSource.</span></span>  
  
5.  <span data-ttu-id="853de-247">**이름** 상자에 **CountryRegion**을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-247">In the **Name** box, type **CountryRegion**</span></span>  
  
6.  <span data-ttu-id="853de-248">**텍스트** 쿼리 유형이 선택되어 있는지 확인한 다음 **쿼리 디자이너**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-248">Verify that the **Text** query type is selected and click **Query Designer**.</span></span>  
  
7.  <span data-ttu-id="853de-249">**텍스트로 편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-249">Click **Edit as Text**.</span></span>  
  
8.  <span data-ttu-id="853de-250">쿼리 창에 다음 쿼리를 복사하여 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="853de-250">Copy and paste the following query into the query pane:</span></span>  
  
    ```  
    SELECT 1 AS ID, 'American Samoa' AS CountryRegion  
    UNION SELECT 2 AS CountryRegionID, 'Australia' AS CountryRegion  
    UNION SELECT 3 AS ID, 'Canada' AS CountryRegion  
    UNION SELECT 4 AS ID, 'Germany' AS CountryRegion  
    UNION SELECT 5 AS ID, 'Micronesia' AS CountryRegion  
    UNION SELECT 6 AS ID, 'France' AS CountryRegion  
    UNION SELECT 7 AS ID, 'United States' AS CountryRegion  
    UNION SELECT 8 AS ID, 'Brazil' AS CountryRegion  
    UNION SELECT 9 AS ID, 'Mexico' AS CountryRegion  
    UNION SELECT 10 AS ID, 'Japan' AS CountryRegion  
    UNION SELECT 10 AS ID, 'Australia' AS CountryRegion  
    UNION SELECT 12 AS ID, 'United Kingdom' AS CountryRegion  
    ```  
  
9. <span data-ttu-id="853de-251">**실행** (**!**)을 클릭 하 여 쿼리를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-251">Click **Run** (**!**) to run the query.</span></span>  
  
     <span data-ttu-id="853de-252">쿼리 결과는 국가/지역 식별자와 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="853de-252">The query results are the country/region identifiers and names.</span></span>  
  
10. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
11. <span data-ttu-id="853de-253">**확인**을 다시 클릭하여 **데이터 세트 속성** 대화 상자를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="853de-253">Click **OK** again to close the **Dataset Properties** dialog box.</span></span>  
  
#### <a name="to-look-up-values-in-the-countryregion-dataset"></a><span data-ttu-id="853de-254">CountryRegion 데이터 세트에서 값을 조회하려면</span><span class="sxs-lookup"><span data-stu-id="853de-254">To look up values in the CountryRegion dataset</span></span>  
  
1.  <span data-ttu-id="853de-255">**Country Region ID** 열 제목을 클릭하고 텍스트 ID를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-255">Click the **Country Region ID** column title and delete the text: ID.</span></span>  
  
2.  <span data-ttu-id="853de-256">**Country Region** 열의 데이터 셀을 마우스 오른쪽 단추로 클릭하고 **식**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-256">Right-click the data cell for the **Country Region** column and click **Expression**.</span></span>  
  
3.  <span data-ttu-id="853de-257">처음 등호(=)를 제외하고 식을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-257">Delete the expression except the initial equal (=) sign.</span></span>  
  
     <span data-ttu-id="853de-258">나머지 식은 다음과 같습니다. `=`</span><span class="sxs-lookup"><span data-stu-id="853de-258">The remaining expression is: `=`</span></span>  
  
4.  <span data-ttu-id="853de-259">**식** 대화 상자에서 **일반 함수**를 확장하고 **기타**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-259">In the **Expression** dialog box, expand **Common Functions** and click **Miscellaneous**.</span></span>  
  
5.  <span data-ttu-id="853de-260">**항목** 목록에서 **Lookup**을 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-260">In the **Item** list, double-click **Lookup**.</span></span>  
  
6.  <span data-ttu-id="853de-261">**범주** 목록에서 **필드(식)** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-261">In the **Category** list, click **Fields (Expressions)**.</span></span>  
  
7.  <span data-ttu-id="853de-262">**값** 목록에서를 두 번 클릭 `CountryRegionID` 합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-262">In the **Values** list, double-click `CountryRegionID`.</span></span>  
  
8.  <span data-ttu-id="853de-263">`CountryRegionID.Value` 바로 뒤에 커서가 없으면 커서를 그곳에 둡니다.</span><span class="sxs-lookup"><span data-stu-id="853de-263">If the cursor is not already immediately after `CountryRegionID.Value`, place it there.</span></span>  
  
9. <span data-ttu-id="853de-264">오른쪽 괄호를 삭제한 다음 **,Fields!ID.value, Fields!CountryRegion.value, "CountryRegion")** 을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-264">Delete the right parenthesis and then type **,Fields!ID.value, Fields!CountryRegion.value, "CountryRegion")**</span></span>  
  
     <span data-ttu-id="853de-265">완성된 식은 다음과 같습니다. `=Lookup(Fields!CountryRegionID.Value,Fields!ID.value, Fields!CountryRegion.value, "CountryRegion")`</span><span class="sxs-lookup"><span data-stu-id="853de-265">The completed expression: `=Lookup(Fields!CountryRegionID.Value,Fields!ID.value, Fields!CountryRegion.value, "CountryRegion")`</span></span>  
  
     <span data-ttu-id="853de-266">**Lookup** 함수의 구문에서는 CountryRegion 데이터 세트에서 CountryRegionID 및 ID 간의 조회를 지정합니다. 여기에서는 CountryRegion 값을 반환하며 이 값은 CountryRegion 데이터 세트에도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="853de-266">The syntax of the **Lookup** function specifies a lookup between CountryRegionID and ID in the CountryRegion dataset that returns the CountryRegion value, which is also in the CountryRegion dataset.</span></span>  
  
10. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
11. <span data-ttu-id="853de-267">**실행** 을 클릭하여 보고서를 미리 봅니다.</span><span class="sxs-lookup"><span data-stu-id="853de-267">Click **Run** to preview the report.</span></span>  
  
##  <a name="6-count-days-since-last-purchase"></a><a name="Count"></a><span data-ttu-id="853de-268">6. 마지막 구매 이후 일 수 계산</span><span class="sxs-lookup"><span data-stu-id="853de-268">6. Count Days Since Last Purchase</span></span>  
 <span data-ttu-id="853de-269">열을 추가한 다음 **Now** 함수 또는 `ExecutionTime` 기본 제공 전역 변수를 사용 하 여 사용자의 마지막 구매 이후 오늘 까지의 일 수를 계산 합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-269">Add a column and then use the **Now** function or the `ExecutionTime` built-in global variable to calculate the number of days from today since a person's last purchases.</span></span>  
  
#### <a name="to-add-the-days-ago-column"></a><span data-ttu-id="853de-270">Days Ago 열을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="853de-270">To add the Days Ago column</span></span>  
  
1.  <span data-ttu-id="853de-271">**디자인** 을 클릭하여 디자인 뷰로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="853de-271">Click **Design** to return to design view.</span></span>  
  
2.  <span data-ttu-id="853de-272">**Last Purchase** 열을 마우스 오른쪽 단추로 클릭하고 **열 삽입**을 가리킨 다음 **오른쪽**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-272">Right-click the **Last Purchase** column, point to **Insert Column**, and then click **Right**.</span></span>  
  
     <span data-ttu-id="853de-273">새 열이 **Last Purchase** 열의 오른쪽에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="853de-273">A new column is added to the right of the **Last Purchase** column.</span></span>  
  
3.  <span data-ttu-id="853de-274">열 머리글에서 **Days Ago**를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-274">In the column header, type **Days Ago**</span></span>  
  
4.  <span data-ttu-id="853de-275">**Days Ago** 열의 데이터 셀을 마우스 오른쪽 단추로 클릭하고 **식**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-275">Right-click the data cell for the **Days Ago** column and click **Expression**.</span></span>  
  
5.  <span data-ttu-id="853de-276">**식** 대화 상자에서 **일반 함수**를 확장하고 **날짜 및 시간**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-276">In the **Expression** dialog box, expand **Common Functions**, and then click **Date & Time**.</span></span>  
  
6.  <span data-ttu-id="853de-277">**항목** 목록에서 **DateDiff**를 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-277">In the **Item** list, double-click **DateDiff**.</span></span>  
  
7.  <span data-ttu-id="853de-278">`DateDiff(` 바로 뒤에 커서가 없으면 커서를 그곳에 둡니다.</span><span class="sxs-lookup"><span data-stu-id="853de-278">If the cursor is not already immediately after `DateDiff(`, place it there.</span></span>  
  
8.  <span data-ttu-id="853de-279">**"d",** 를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-279">Type **"d",**</span></span>  
  
9. <span data-ttu-id="853de-280">**범주** 목록에서 **필드(식)** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-280">In the **Category** list, click **Fields (Expressions)**.</span></span>  
  
10. <span data-ttu-id="853de-281">**값** 목록에서 **LastPurchase**를 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-281">In the **Values** list, double-click **LastPurchase**.</span></span>  
  
11. <span data-ttu-id="853de-282">`Fields!LastPurchase.Value` 바로 뒤에 커서가 없으면 커서를 그곳에 둡니다.</span><span class="sxs-lookup"><span data-stu-id="853de-282">If the cursor is not already immediately after `Fields!LastPurchase.Value`, place it there.</span></span>  
  
12. <span data-ttu-id="853de-283">유형 **,**</span><span class="sxs-lookup"><span data-stu-id="853de-283">Type **,**</span></span>  
  
13. <span data-ttu-id="853de-284">**범주** 목록에서 **날짜 및 시간**을 다시 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-284">In the **Category** list, click **Date & Time** again.</span></span>  
  
14. <span data-ttu-id="853de-285">**항목** 목록에서 **Now**를 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-285">In the **Item** list, double-click **Now**.</span></span>  
  
    > [!WARNING]  
    >  <span data-ttu-id="853de-286">프로덕션 보고서의 경우, 보고서의 정보 행에서와 같이 보고서가 렌더링되면서 여러 번 계산되는 식에서 **Now** 함수를 사용하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="853de-286">In production reports you should not use the **Now** function in expressions that are evaluated multiple times as the report renders (for example, in the detail rows of a report).</span></span> <span data-ttu-id="853de-287">**Now** 의 값은 행마다 변경되고 서로 다른 값이 식의 계산 결과에 영향을 미치므로 조금씩 일치하지 않는 결과가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-287">The value of **Now** changes from row to row and the different values affect the evaluation results of expressions, which leads to results that are subtly inconsistent.</span></span> <span data-ttu-id="853de-288">대신 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]에서 제공하는 `ExecutionTime` 전역 변수를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-288">Instead, you should use the `ExecutionTime` global variable that [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] provides.</span></span>  
  
15. <span data-ttu-id="853de-289">`Now(` 바로 뒤에 커서가 없으면 커서를 그곳에 둡니다.</span><span class="sxs-lookup"><span data-stu-id="853de-289">If the cursor is not already immediately after `Now(`, place it there.</span></span>  
  
16. <span data-ttu-id="853de-290">왼쪽 괄호를 삭제한 다음 **)** 를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-290">Delete the left parenthesis and then type **)**</span></span>  
  
     <span data-ttu-id="853de-291">완성된 식은 다음과 같습니다. `=DateDiff("d", Fields!LastPurchase.Value, Now)`</span><span class="sxs-lookup"><span data-stu-id="853de-291">The completed expression: `=DateDiff("d", Fields!LastPurchase.Value, Now)`</span></span>  
  
17. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
##  <a name="7-use-an-indicator-to-show-sales-comparison"></a><a name="Indicator"></a><span data-ttu-id="853de-292">7. 표시기를 사용 하 여 판매 비교 표시</span><span class="sxs-lookup"><span data-stu-id="853de-292">7. Use an Indicator to Show Sales Comparison</span></span>  
 <span data-ttu-id="853de-293">새 열을 추가 하 고 표시기를 사용 하 여 연간 연간 누계 (YTD) 구매가 평균 YTD 구매를 초과 하는지 여부를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-293">Add a new column and use an indicator to show whether a person's year-to-date (YTD) purchases are above or below the average YTD purchases.</span></span> <span data-ttu-id="853de-294">**Round** 함수는 값에서 소수를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-294">The **Round** function removes decimals from values.</span></span>  
  
 <span data-ttu-id="853de-295">표시기와 그 상태의 구성에는 많은 단계가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-295">The configuration of the indicator and its states requires many steps.</span></span> <span data-ttu-id="853de-296">원하는 경우 "표시기를 구성 하려면" 절차에서 앞으로 건너뛰고이 자습서의 완성 된 식을 복사 하 여 **식** 대화 상자에 붙여 넣을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="853de-296">If you want to, in the "To configure the indicator" procedure, you can skip ahead and copy/paste the completed expressions from this tutorial into the **Expression** dialog box.</span></span>  
  
#### <a name="to-add-the--or---avg-sales-column"></a><span data-ttu-id="853de-297">+ or - AVG Sales 열을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="853de-297">To add the + or - AVG Sales column</span></span>  
  
1.  <span data-ttu-id="853de-298">**YTD Purchase** 열을 마우스 오른쪽 단추로 클릭하고 **열 삽입**을 가리킨 다음 **오른쪽**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-298">Right-click the **YTD Purchase** column, point to **Insert Column**, and then click **Right**.</span></span>  
  
     <span data-ttu-id="853de-299">새 열이 **YTD Purchase** 열의 오른쪽에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="853de-299">A new column is added to the right of the **YTD Purchase** column.</span></span>  
  
2.  <span data-ttu-id="853de-300">열의 제목을 클릭하고 **+ or - AVG Sales**를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-300">Click the title of the column and type **+ or - AVG Sales**</span></span>  
  
#### <a name="to-add-an-indicator"></a><span data-ttu-id="853de-301">표시기를 추가하려면</span><span class="sxs-lookup"><span data-stu-id="853de-301">To add an indicator</span></span>  
  
1.  <span data-ttu-id="853de-302">리본의 **삽입** 탭에서 **표시기**를 클릭한 다음 **+ or - AVG Sales** 열의 데이터 셀을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-302">On the **Insert** tab of the ribbon, click **Indicator**, and then click the data cell for the **+ or - AVG Sales** column.</span></span>  
  
     <span data-ttu-id="853de-303">**표시기 유형 선택** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="853de-303">The **Select Indicator Type** dialog box opens.</span></span>  
  
2.  <span data-ttu-id="853de-304">아이콘 집합의 **방향** 그룹에서 회색 화살표 3개로 구성된 집합을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-304">In the **Directional** group of icon sets, click the set of three gray arrows.</span></span>  
  
3.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
#### <a name="to-configure-the-indicator"></a><span data-ttu-id="853de-305">표시기를 구성하려면</span><span class="sxs-lookup"><span data-stu-id="853de-305">To configure the indicator</span></span>  
  
1.  <span data-ttu-id="853de-306">표시기를 마우스 오른쪽 단추로 클릭하고 **표시기 속성**을 클릭한 다음 **값 및 상태**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-306">Right-click the indicator, click **Indicator Properties**, and then click **Value and States**.</span></span>  
  
2.  <span data-ttu-id="853de-307">**값** 입력란 옆의 식 단추( **fx** )를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-307">Click the expression **fx** button next to the **Value** text box.</span></span>  
  
3.  <span data-ttu-id="853de-308">**식** 대화 상자에서 **일반 함수**를 확장하고 **수치 연산**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-308">In the **Expression** dialog box, expand **Common Functions**, and then click **Math**.</span></span>  
  
4.  <span data-ttu-id="853de-309">**항목** 목록에서 **Round**를 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-309">In the **Item** list, double-click **Round**.</span></span>  
  
5.  <span data-ttu-id="853de-310">**범주** 목록에서 **필드(식)** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-310">In the **Category** list, click **Fields (Expressions)**.</span></span>  
  
6.  <span data-ttu-id="853de-311">**값** 목록에서 **YTDPurchase**를 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-311">In the **Values** list, double-click **YTDPurchase**.</span></span>  
  
7.  <span data-ttu-id="853de-312">`Fields!YTDPurchase.Value` 바로 뒤에 커서가 없으면 커서를 그곳에 둡니다.</span><span class="sxs-lookup"><span data-stu-id="853de-312">If the cursor is not already immediately after `Fields!YTDPurchase.Value`, place it there.</span></span>  
  
8.  <span data-ttu-id="853de-313">입력할**-**</span><span class="sxs-lookup"><span data-stu-id="853de-313">Type  **-**</span></span>  
  
9. <span data-ttu-id="853de-314">**일반 함수**를 다시 확장하고 **집계**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-314">Expand **Common Functions** again and click **Aggregate**.</span></span>  
  
10. <span data-ttu-id="853de-315">**항목** 목록에서 **Avg**를 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-315">In the **Item** list, double-click **Avg**.</span></span>  
  
11. <span data-ttu-id="853de-316">**범주** 목록에서 **필드(식)** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-316">In the **Category** list, click **Fields (Expressions)**.</span></span>  
  
12. <span data-ttu-id="853de-317">**값** 목록에서 **YTDPurchase**를 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-317">In the **Values** list, double-click **YTDPurchase**.</span></span>  
  
13. <span data-ttu-id="853de-318">`Fields!YTDPurchase.Value` 바로 뒤에 커서가 없으면 커서를 그곳에 둡니다.</span><span class="sxs-lookup"><span data-stu-id="853de-318">If the cursor is not already immediately after `Fields!YTDPurchase.Value`, place it there.</span></span>  
  
14. <span data-ttu-id="853de-319">**, "Expressions"))** 를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-319">Type **, "Expressions"))**</span></span>  
  
     <span data-ttu-id="853de-320">완성된 식은 다음과 같습니다. `=Round(Fields!YTDPurchase.Value - Avg(Fields!YTDPurchase.Value, "Expressions"))`</span><span class="sxs-lookup"><span data-stu-id="853de-320">The completed expression: `=Round(Fields!YTDPurchase.Value - Avg(Fields!YTDPurchase.Value, "Expressions"))`</span></span>  
  
15. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
16. <span data-ttu-id="853de-321">**상태 단위** 상자에서 **숫자**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-321">In the **States Measurement Unit** box, select **Numeric**.</span></span>  
  
17. <span data-ttu-id="853de-322">아래쪽 화살표가 있는 행에서 **시작** 값의 입력란 오른쪽에 있는 **fx** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-322">In the row with the down-pointing arrow, click the **fx** button to the right of the text box for the **Start** value.</span></span>  
  
18. <span data-ttu-id="853de-323">**식** 대화 상자에서 **일반 함수**를 확장하고 **수치 연산**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-323">In the **Expression** dialog box, expand **Common Functions**, and then click **Math**.</span></span>  
  
19. <span data-ttu-id="853de-324">**항목** 목록에서 **Round**를 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-324">In the **Item** list, double-click **Round**.</span></span>  
  
20. <span data-ttu-id="853de-325">**범주** 목록에서 **필드(식)** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-325">In the **Category** list, click **Fields (Expressions)**.</span></span>  
  
21. <span data-ttu-id="853de-326">**값** 목록에서 **YTDPurchase**를 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-326">In the **Values** list, double-click **YTDPurchase**.</span></span>  
  
22. <span data-ttu-id="853de-327">`Fields!YTDPurchase.Value` 바로 뒤에 커서가 없으면 커서를 그곳에 둡니다.</span><span class="sxs-lookup"><span data-stu-id="853de-327">If the cursor is not already immediately after `Fields!YTDPurchase.Value`, place it there.</span></span>  
  
23. <span data-ttu-id="853de-328">입력할**-**</span><span class="sxs-lookup"><span data-stu-id="853de-328">Type  **-**</span></span>  
  
24. <span data-ttu-id="853de-329">**일반 함수**를 다시 확장하고 **집계**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-329">Expand **Common Functions** again and click **Aggregate**.</span></span>  
  
25. <span data-ttu-id="853de-330">**항목** 목록에서 **Avg**를 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-330">In the **Item** list, double-click **Avg**.</span></span>  
  
26. <span data-ttu-id="853de-331">**범주** 목록에서 **필드(식)** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-331">In the **Category** list, click **Fields (Expressions)**.</span></span>  
  
27. <span data-ttu-id="853de-332">**값** 목록에서 **YTDPurchase**를 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-332">In the **Values** list, double-click **YTDPurchase**.</span></span>  
  
28. <span data-ttu-id="853de-333">`Fields!YTDPurchase.Value` 바로 뒤에 커서가 없으면 커서를 그곳에 둡니다.</span><span class="sxs-lookup"><span data-stu-id="853de-333">If the cursor is not already immediately after `Fields!YTDPurchase.Value`, place it there.</span></span>  
  
29. <span data-ttu-id="853de-334">**, "Expressions")) < 0**을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-334">Type **, "Expressions")) < 0**</span></span>  
  
     <span data-ttu-id="853de-335">완성된 식은 다음과 같습니다. `=Round(Fields!YTDPurchase.Value - Avg(Fields!YTDPurchase.Value, "Expressions")) < 0`</span><span class="sxs-lookup"><span data-stu-id="853de-335">The completed expression: `=Round(Fields!YTDPurchase.Value - Avg(Fields!YTDPurchase.Value, "Expressions")) < 0`</span></span>  
  
30. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
31. <span data-ttu-id="853de-336">**끝** 값의 입력란에 **0**을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-336">In the text box for the **End** value, type **0**</span></span>  
  
32. <span data-ttu-id="853de-337">옆쪽 화살표가 있는 행을 클릭하고 **삭제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-337">Click the row with the horizontal-pointing arrow and click **Delete**.</span></span>  
  
33. <span data-ttu-id="853de-338">위쪽 화살표가 있는 행에서 **시작** 상자에 **0**을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-338">In the row with the up-pointing arrow, in the **Start** box, type **0**</span></span>  
  
34. <span data-ttu-id="853de-339">**끝** 값의 입력란 오른쪽에 있는 **fx** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-339">Click the **fx** button to the right of the text box for the **End** value.</span></span>  
  
35. <span data-ttu-id="853de-340">**식** 대화 상자에서 식을 만듭니다.`=Round(Fields!YTDPurchase.Value - Avg(Fields!YTDPurchase.Value, "Expressions")) >0`</span><span class="sxs-lookup"><span data-stu-id="853de-340">In the **Expression** dialog box, create the expression: `=Round(Fields!YTDPurchase.Value - Avg(Fields!YTDPurchase.Value, "Expressions")) >0`</span></span>  
  
36. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
37. <span data-ttu-id="853de-341">**확인** 을 다시 클릭하여 **표시기 속성** 대화 상자를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="853de-341">Click **OK** again to close the **Indicator properties** dialog box.</span></span>  
  
38. <span data-ttu-id="853de-342">**실행** 을 클릭하여 보고서를 미리 봅니다.</span><span class="sxs-lookup"><span data-stu-id="853de-342">Click **Run** to preview the report.</span></span>  
  
##  <a name="8-make-the-report-a-green-bar-report"></a><a name="GreenBar"></a><span data-ttu-id="853de-343">8. 보고서를 "녹색 막대" 보고서로 만들기</span><span class="sxs-lookup"><span data-stu-id="853de-343">8. Make the Report a "Green Bar" Report</span></span>  
 <span data-ttu-id="853de-344">가로줄무늬가 있는 보고서로 만들기 위해 매개 변수를 사용하여 보고서의 행에 번갈아 적용할 색을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-344">Use a parameter to specify the color to apply to alternating rows in the report, making it a barred report.</span></span>  
  
#### <a name="to-add-a-parameter"></a><span data-ttu-id="853de-345">매개 변수를 추가하려면</span><span class="sxs-lookup"><span data-stu-id="853de-345">To add a parameter</span></span>  
  
1.  <span data-ttu-id="853de-346">**디자인** 을 클릭하여 디자인 뷰로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="853de-346">Click **Design** to return to design view.</span></span>  
  
2.  <span data-ttu-id="853de-347">**보고서 데이터** 창에서 **매개 변수** 를 마우스 오른쪽 단추로 클릭하고 **매개 변수 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-347">In the **Report Data** pane, right-click **Parameters** and click **Add Parameter**.</span></span>  
  
     <span data-ttu-id="853de-348">**보고서 매개 변수 속성** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="853de-348">The **Report Parameter Properties** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="853de-349">**프롬프트**에 **Choose color**를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-349">In **Prompt**, type **Choose color**</span></span>  
  
4.  <span data-ttu-id="853de-350">**이름**에 **RowColor**를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-350">In **Name**, type **RowColor**</span></span>  
  
5.  <span data-ttu-id="853de-351">왼쪽 창에서 **사용 가능한 값**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-351">In the left pane, click **Available Values**.</span></span>  
  
6.  <span data-ttu-id="853de-352">**값 지정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-352">Click **Specify values**.</span></span>  
  
7.  <span data-ttu-id="853de-353">**추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-353">Click **Add**.</span></span>  
  
8.  <span data-ttu-id="853de-354">**레이블** 상자에 **Yellow**를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-354">In the **Label** box, type: **Yellow**</span></span>  
  
9. <span data-ttu-id="853de-355">**값** 상자에 **Yellow**를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-355">In the **Value** box, type **Yellow**</span></span>  
  
10. <span data-ttu-id="853de-356">**추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-356">Click **Add**.</span></span>  
  
11. <span data-ttu-id="853de-357">**레이블** 상자에 **Green**을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-357">In the **Label** box, type **Green**</span></span>  
  
12. <span data-ttu-id="853de-358">**값** 상자에 **PaleGreen**을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-358">In the **Value** box, type **PaleGreen**</span></span>  
  
13. <span data-ttu-id="853de-359">**추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-359">Click **Add**.</span></span>  
  
14. <span data-ttu-id="853de-360">**레이블** 상자에 **Blue**를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-360">In the **Label** box, type **Blue**</span></span>  
  
15. <span data-ttu-id="853de-361">**값** 상자에 **LightBlue**를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-361">In the **Value** box, type **LightBlue**</span></span>  
  
16. <span data-ttu-id="853de-362">**추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-362">Click **Add**.</span></span>  
  
17. <span data-ttu-id="853de-363">**레이블** 상자에 **Pink**를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-363">In the **Label** box, type **Pink**</span></span>  
  
18. <span data-ttu-id="853de-364">**값** 상자에 **Pink**를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-364">In the **Value** box, type **Pink**</span></span>  
  
19. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
#### <a name="to-apply-alternating-colors-to-detail-rows"></a><span data-ttu-id="853de-365">정보 행에 색을 번갈아 적용하려면</span><span class="sxs-lookup"><span data-stu-id="853de-365">To apply alternating colors to detail rows</span></span>  
  
1.  <span data-ttu-id="853de-366">리본의 **보기** 탭을 클릭하고 **속성**이 선택되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-366">Click the **View** tab on the ribbon and verify that **Properties** is selected.</span></span>  
  
2.  <span data-ttu-id="853de-367">**Name** 열의 데이터 셀을 클릭하고 Shift 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="853de-367">Click the data cell for the **Name** column and press the Shift key.</span></span>  
  
3.  <span data-ttu-id="853de-368">행의 다른 셀을 차례로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-368">One by one, click the other cells in the row.</span></span>  
  
4.  <span data-ttu-id="853de-369">속성 창에서 **BackgroundColor**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-369">In the Properties pane, click **BackgroundColor**.</span></span>  
  
     <span data-ttu-id="853de-370">속성 창에 속성이 범주별로 표시되어 있으면 **Fill** 범주에서 **BackgroundColor**를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="853de-370">If your Properties pane lists properties by category, you will find the **BackgroundColor** under the **Fill** category.</span></span>  
  
5.  <span data-ttu-id="853de-371">아래쪽 화살표를 클릭한 다음 **식**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-371">Click the down arrow and then click **Expression**.</span></span>  
  
6.  <span data-ttu-id="853de-372">**식** 대화 상자에서 **일반 함수**를 확장하고 **프로그램 흐름**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-372">In the **Expression** dialog box, expand **Common Functions**, and then click **Program Flow**.</span></span>  
  
7.  <span data-ttu-id="853de-373">**항목** 목록에서 **IIf**를 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-373">In the **Item** list, double-click **IIf**.</span></span>  
  
8.  <span data-ttu-id="853de-374">**일반 함수**를 확장하고 **집계**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-374">Expand **Common Functions** and click **Aggregate**.</span></span>  
  
9. <span data-ttu-id="853de-375">**항목** 목록에서 **RunningValue**를 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-375">In the **Item** list, double-click **RunningValue**.</span></span>  
  
10. <span data-ttu-id="853de-376">**범주** 목록에서 **필드(식)** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-376">In the **Category** list, click **Fields (Expressions)**.</span></span>  
  
11. <span data-ttu-id="853de-377">**값** 목록에서 **FirstName**을 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-377">In the **Values** list, double-click **FirstName**.</span></span>  
  
12. <span data-ttu-id="853de-378">`Fields!FirstName.Value` 바로 뒤에 커서가 없으면 커서를 그곳에 두고 **,** 를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-378">If the cursor is not already immediately after `Fields!FirstName.Value`, place it there and type **,**</span></span>  
  
13. <span data-ttu-id="853de-379">**일반 함수**를 확장하고 **집계**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-379">Expand **Common Functions** and click **Aggregate**.</span></span>  
  
14. <span data-ttu-id="853de-380">**항목** 목록에서 **Count**를 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-380">In the **Item** list, double-click **Count**.</span></span>  
  
15. <span data-ttu-id="853de-381">`Count(` 바로 뒤에 커서가 없으면 커서를 그곳에 둡니다.</span><span class="sxs-lookup"><span data-stu-id="853de-381">If the cursor is not already immediately after `Count(`, place it there.</span></span>  
  
16. <span data-ttu-id="853de-382">왼쪽 괄호를 삭제 한 다음 **, "Expressions")를** 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-382">Delete the left parenthesis and then type **,"Expressions")**</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="853de-383">식은 데이터 행 수를 셀 데이터 세트의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="853de-383">Expressions is the name of the dataset in which to count data rows.</span></span>  
  
17. <span data-ttu-id="853de-384">**연산자**를 확장하고 **산술**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-384">Expand **Operators** and click **Arithmetic**.</span></span>  
  
18. <span data-ttu-id="853de-385">**항목** 목록에서 **Mod**를 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-385">In the **Item** list, double-click **Mod**.</span></span>  
  
19. <span data-ttu-id="853de-386">`Mod` 바로 뒤에 커서가 없으면 커서를 그곳에 둡니다.</span><span class="sxs-lookup"><span data-stu-id="853de-386">If the cursor is not already immediately after `Mod`, place it there.</span></span>  
  
20. <span data-ttu-id="853de-387">**2 =0,** 를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-387">Type  **2 =0,**</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="853de-388">숫자 2를 입력하기 전에 공백을 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-388">Be sure you include a space before you type the number 2.</span></span>  
  
21. <span data-ttu-id="853de-389">**매개 변수** 를 클릭하고 **값** 목록에서 **RowColor**를 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-389">Click **Parameters** and in the **Values** list, double-click **RowColor**.</span></span>  
  
22. <span data-ttu-id="853de-390">`Parameters!RowColor.Value` 바로 뒤에 커서가 없으면 커서를 그곳에 둡니다.</span><span class="sxs-lookup"><span data-stu-id="853de-390">If the cursor is not already immediately after `Parameters!RowColor.Value`, place it there.</span></span>  
  
23. <span data-ttu-id="853de-391">**, "White")를 입력 합니다** .</span><span class="sxs-lookup"><span data-stu-id="853de-391">Type **, "White")**</span></span>  
  
     <span data-ttu-id="853de-392">완성된 식은 다음과 같습니다. `=IIf(RunningValue(Fields!FirstName.Value,Count, "Expressions") Mod 2 =0, Parameters!RowColor.Value, "White")`</span><span class="sxs-lookup"><span data-stu-id="853de-392">The completed expression: `=IIf(RunningValue(Fields!FirstName.Value,Count, "Expressions") Mod 2 =0, Parameters!RowColor.Value, "White")`</span></span>  
  
24. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
#### <a name="run-the-report"></a><span data-ttu-id="853de-393">보고서 실행</span><span class="sxs-lookup"><span data-stu-id="853de-393">Run the Report</span></span>  
  
1.  <span data-ttu-id="853de-394">**홈** 탭에 없으면 **홈**을 클릭하여 디자인 뷰로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="853de-394">If not on the **Home** tab, click **Home** to return to design view.</span></span>  
  
2.  <span data-ttu-id="853de-395">**실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-395">Click **Run**.</span></span>  
  
3.  <span data-ttu-id="853de-396">**색 선택** 드롭다운 목록에서 보고서에 표시될 흰색이 아닌 막대의 색을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-396">In the **Choose color** drop-down list, select the color of the non-white bars on the report.</span></span>  
  
4.  <span data-ttu-id="853de-397">**보고서 보기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-397">Click **View Report**.</span></span>  
  
     <span data-ttu-id="853de-398">보고서가 렌더링되고 선택한 배경이 행에 번갈아 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="853de-398">The report renders and alternating rows have the background that you chose.</span></span>  
  
##  <a name="optional-format-date-column"></a><a name="DateFormat"></a><span data-ttu-id="853de-399">필드 날짜 열 서식 지정</span><span class="sxs-lookup"><span data-stu-id="853de-399">(optional) Format Date Column</span></span>  
 <span data-ttu-id="853de-400">날짜가 포함된 **Last Purchase** 열의 서식을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-400">Format the **Last Purchase** column, which contains dates.</span></span>  
  
#### <a name="to-format-date-column"></a><span data-ttu-id="853de-401">날짜 열의 서식을 지정하려면</span><span class="sxs-lookup"><span data-stu-id="853de-401">To format date column</span></span>  
  
1.  <span data-ttu-id="853de-402">**디자인** 을 클릭하여 디자인 뷰로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="853de-402">Click **Design** to return to design view.</span></span>  
  
2.  <span data-ttu-id="853de-403">**Last Purchase** 열의 데이터 셀을 마우스 오른쪽 단추로 클릭하고 **입력란 속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-403">Right-click the data cell for the **Last Purchase** column and click **Text Box Properties**.</span></span>  
  
3.  <span data-ttu-id="853de-404">**입력란 속성** 대화 상자에서 **숫자**, **날짜**, **\*1/31/2000** 형식을 차례로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-404">In the **Text Box Properties** dialog box, click **Number**, click **Date**, and then click the type **\*1/31/2000**.</span></span>  
  
4.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
##  <a name="optional-add-a-report-title"></a><a name="Title"></a><span data-ttu-id="853de-405">필드 보고서 제목 추가</span><span class="sxs-lookup"><span data-stu-id="853de-405">(optional) Add a Report Title</span></span>  
 <span data-ttu-id="853de-406">보고서에 제목을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-406">Add a title to the report.</span></span>  
  
#### <a name="to-add-a-report-title"></a><span data-ttu-id="853de-407">보고서 제목을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="853de-407">To add a report title</span></span>  
  
1.  <span data-ttu-id="853de-408">디자인 화면에서 **제목을 추가하려면 클릭하십시오.** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-408">On the design surface, click **Click to add title**.</span></span>  
  
2.  <span data-ttu-id="853de-409">**Sales Comparison Summary**를 입력한 다음 입력란 바깥쪽을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-409">Type **Sales Comparison Summary**, and then click outside the text box.</span></span>  
  
3.  <span data-ttu-id="853de-410">**Sales Comparison Summary**가 들어 있는 입력란을 마우스 오른쪽 단추로 클릭하고 **입력란 속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-410">Right-click the text box that contains **Sales Comparison Summary** and click **Text Box Properties**.</span></span>  
  
4.  <span data-ttu-id="853de-411">**입력란 속성** 대화 상자에서 **글꼴**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-411">In the **Text Box Properties** dialog box, click **Font**.</span></span>  
  
5.  <span data-ttu-id="853de-412">**크기** 목록에서 **18pt**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-412">In the **Size** list, select **18pt**.</span></span>  
  
6.  <span data-ttu-id="853de-413">**색** 목록에서 **회색**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-413">In the **Color** list, select **Gray**.</span></span>  
  
7.  <span data-ttu-id="853de-414">**굵게** 및 **기울임꼴**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-414">Select  **Bold** and  **Italic**.</span></span>  
  
8.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
##  <a name="optional-save-the-report"></a><a name="Save"></a><span data-ttu-id="853de-415">필드 보고서 저장</span><span class="sxs-lookup"><span data-stu-id="853de-415">(optional) Save the Report</span></span>  
 <span data-ttu-id="853de-416">보고서를 보고서 서버, SharePoint 라이브러리 또는 컴퓨터에 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="853de-416">You can save reports to a report server, SharePoint library, or your computer.</span></span> <span data-ttu-id="853de-417">자세한 내용은 [보고서 저장&#40;보고서 작성기&#41;](report-builder/saving-reports-report-builder.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="853de-417">For more information, see [Saving Reports &#40;Report Builder&#41;](report-builder/saving-reports-report-builder.md).</span></span>  
  
 <span data-ttu-id="853de-418">이 자습서에서는 보고서를 보고서 서버에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-418">In this tutorial, save the report to a report server.</span></span> <span data-ttu-id="853de-419">보고서 서버에 액세스할 수 없는 경우에는 보고서를 컴퓨터에 저장하십시오.</span><span class="sxs-lookup"><span data-stu-id="853de-419">If you do not have access to a report server, save the report to your computer.</span></span>  
  
#### <a name="to-save-the-report-to-a-report-server"></a><span data-ttu-id="853de-420">보고서를 보고서 서버에 저장하려면</span><span class="sxs-lookup"><span data-stu-id="853de-420">To save the report to a report server</span></span>  
  
1.  <span data-ttu-id="853de-421">**보고서 작성기** 단추에서 다른 **이름으로 저장**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-421">From the **Report Builder** button, click **Save As**.</span></span>  
  
2.  <span data-ttu-id="853de-422">**최근에 사용한 사이트 및 서버**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-422">Click **Recent Sites and Servers**.</span></span>  
  
3.  <span data-ttu-id="853de-423">보고서를 저장할 수 있는 권한을 가진 보고서 서버의 이름을 선택하거나 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-423">Select or type the name of the report server where you have permission to save reports.</span></span>  
  
     <span data-ttu-id="853de-424">"보고서 서버에 연결하는 중"이라는 메시지가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="853de-424">The message "Connecting to report server" appears.</span></span> <span data-ttu-id="853de-425">연결되면 보고서 서버 관리자가 기본 보고서 위치로 지정한 보고서 폴더의 내용이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="853de-425">When the connection is complete, you will see the contents of the report folder that the report server administrator specified as the default report location.</span></span>  
  
4.  <span data-ttu-id="853de-426">**이름**에서 기본 이름을 **Sales Comparison Summary**로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="853de-426">In **Name**, replace the default name with **Sales Comparison Summary**.</span></span>  
  
5.  <span data-ttu-id="853de-427">**저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-427">Click **Save**.</span></span>  
  
 <span data-ttu-id="853de-428">보고서가 보고서 서버에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="853de-428">The report is saved to the report server.</span></span> <span data-ttu-id="853de-429">연결된 보고서 서버의 이름이 창 아래쪽에 있는 상태 표시줄에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="853de-429">The name of report server that you are connected to appears in the status bar at the bottom of the window.</span></span>  
  
#### <a name="to-save-the-report-to-your-computer"></a><span data-ttu-id="853de-430">컴퓨터에 보고서를 저장하려면</span><span class="sxs-lookup"><span data-stu-id="853de-430">To save the report to your computer</span></span>  
  
1.  <span data-ttu-id="853de-431">**보고서 작성기** 단추에서 다른 **이름으로 저장**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-431">From the **Report Builder** button, click **Save As**.</span></span>  
  
2.  <span data-ttu-id="853de-432">**바탕 화면**, **내 문서**또는 **내 컴퓨터**를 클릭한 다음 보고서를 저장할 폴더를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="853de-432">Click **Desktop**, **My Documents**, or **My computer**, and then browse to the folder where you want to save the report.</span></span>  
  
3.  <span data-ttu-id="853de-433">**이름**에서 기본 이름을 **Sales Comparison Summary**로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="853de-433">In **Name**, replace the default name with **Sales Comparison Summary**.</span></span>  
  
4.  <span data-ttu-id="853de-434">**저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-434">Click **Save**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="853de-435">참고 항목</span><span class="sxs-lookup"><span data-stu-id="853de-435">See Also</span></span>  
 <span data-ttu-id="853de-436">[식&#40;보고서 작성기 및 SSRS&#41;](report-design/expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="853de-436">[Expressions &#40;Report Builder and SSRS&#41;](report-design/expressions-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="853de-437">[식 예&#40;보고서 작성기 및 SSRS&#41;](report-design/expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="853de-437">[Expression Examples &#40;Report Builder and SSRS&#41;](report-design/expression-examples-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="853de-438">[보고서 작성기 및 SSRS &#40;표시기&#41;](report-design/indicators-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="853de-438">[Indicators &#40;Report Builder and SSRS&#41;](report-design/indicators-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="853de-439">[이미지, 텍스트 상자, 사각형 및 선 &#40;보고서 작성기 및 SSRS&#41;](report-design/rectangles-and-lines-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="853de-439">[Images, Text Boxes, Rectangles, and Lines &#40;Report Builder and SSRS&#41;](report-design/rectangles-and-lines-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="853de-440">[테이블 &#40;보고서 작성기 및 SSRS&#41;](report-design/tables-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="853de-440">[Tables &#40;Report Builder  and SSRS&#41;](report-design/tables-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="853de-441">보고서 &#40;보고서 작성기 및 SSRS&#41;에 데이터를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="853de-441">Add Data to a Report &#40;Report Builder and SSRS&#41;</span></span>](report-data/report-datasets-ssrs.md)  
  
  
