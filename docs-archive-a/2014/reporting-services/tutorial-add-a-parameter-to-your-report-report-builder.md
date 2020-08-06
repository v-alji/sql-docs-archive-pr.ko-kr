---
title: '자습서: 보고서에 매개 변수 추가(보고서 작성기) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: eab34ec4-b3ad-4a76-95cc-07b2f75ee6d7
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: dff41066a2d505ab53b17a10fb3da9b6cb17130f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735952"
---
# <a name="tutorial-add-a-parameter-to-your-report-report-builder"></a><span data-ttu-id="5f394-102">자습서: 보고서에 매개 변수 추가(보고서 작성기)</span><span class="sxs-lookup"><span data-stu-id="5f394-102">Tutorial: Add a Parameter to Your Report (Report Builder)</span></span>
  <span data-ttu-id="5f394-103">보고서에 매개 변수를 추가하면 사용자가 데이터 원본이나 보고서에서 보고서 데이터를 필터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-103">Add a parameter to your report to let users filter report data from the data source or in the report.</span></span> <span data-ttu-id="5f394-104">보고서 매개 변수는 데이터 세트 쿼리에 포함하는 각 쿼리 매개 변수에 대해 자동으로 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-104">Report parameters are created automatically for each query parameter that you include in a dataset query.</span></span> <span data-ttu-id="5f394-105">매개 변수 데이터 형식에 따라 보고서 뷰 도구 모음에 매개 변수가 표시되는 방식이 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-105">The parameter data type determines how it appears on the report view toolbar.</span></span>  
  
 <span data-ttu-id="5f394-106">![rs_tut_Parameter](../../2014/tutorials/media/rs-tut-parameter.gif "rs_tut_Parameter")</span><span class="sxs-lookup"><span data-stu-id="5f394-106">![rs_tut_Parameter](../../2014/tutorials/media/rs-tut-parameter.gif "rs_tut_Parameter")</span></span>  
  
##  <a name="what-you-will-learn"></a><a name="BackToTop"></a><span data-ttu-id="5f394-107">학습 내용</span><span class="sxs-lookup"><span data-stu-id="5f394-107">What You Will Learn</span></span>  
 <span data-ttu-id="5f394-108">이 자습서에서는 다음 작업 방법을 배웁니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-108">In this tutorial you will learn how to do the following:</span></span>  
  
1.  [<span data-ttu-id="5f394-109">테이블 또는 행렬 마법사에서 행렬 보고서 및 데이터 집합 만들기</span><span class="sxs-lookup"><span data-stu-id="5f394-109">Create a Matrix Report and Dataset from the Table or Matrix Wizard</span></span>](#Setup)  
  
2.  [<span data-ttu-id="5f394-110">테이블 또는 행렬 마법사에서 데이터 구성 및 레이아웃과 스타일 선택</span><span class="sxs-lookup"><span data-stu-id="5f394-110">Organize Data, Choose Layout, and Style from the Table or Matrix Wizard</span></span>](#CompleteWizard)  
  
3.  [<span data-ttu-id="5f394-111">쿼리 매개 변수를 추가하여 보고서 매개 변수 만들기</span><span class="sxs-lookup"><span data-stu-id="5f394-111">Add a Query Parameter to Create a Report Parameter</span></span>](#Query)  
  
4.  [<span data-ttu-id="5f394-112">보고서 매개 변수의 기본 데이터 형식 및 기타 속성 변경</span><span class="sxs-lookup"><span data-stu-id="5f394-112">Change Default Data Type and Other Properties for a Report Parameter</span></span>](#ChangeDefaultProperties)  
  
    1.  [<span data-ttu-id="5f394-113">사용 가능한 값과 표시 이름을 제공하는 데이터 세트 추가</span><span class="sxs-lookup"><span data-stu-id="5f394-113">Add a Dataset to Provide Available Values and Display Names</span></span>](#AddDataset)  
  
    2.  [<span data-ttu-id="5f394-114">드롭다운 값 목록을 만드는 데 사용 가능한 값 지정</span><span class="sxs-lookup"><span data-stu-id="5f394-114">Specify Available Values to Create a Drop-List of Values</span></span>](#AvailableValues)  
  
    3.  [<span data-ttu-id="5f394-115">보고서가 자동으로 실행되도록 기본값 지정</span><span class="sxs-lookup"><span data-stu-id="5f394-115">Specify Default Values so the Report Runs Automatically</span></span>](#DefaultValues)  
  
    4.  [<span data-ttu-id="5f394-116">이름/값 쌍이 있는 데이터 세트에서 값 조회</span><span class="sxs-lookup"><span data-stu-id="5f394-116">Look up a Value from a Dataset that has Name/Value Pairs</span></span>](#NameValue)  
  
5.  [<span data-ttu-id="5f394-117">보고서에 선택한 매개 변수 값 표시</span><span class="sxs-lookup"><span data-stu-id="5f394-117">Display the Selected Parameter Value in the Report</span></span>](#Expression)  
  
6.  [<span data-ttu-id="5f394-118">필터에서 보고서 매개 변수 사용</span><span class="sxs-lookup"><span data-stu-id="5f394-118">Use the Report Parameter in a Filter</span></span>](#Filter)  
  
7.  [<span data-ttu-id="5f394-119">여러 값을 허용하도록 보고서 매개 변수 변경</span><span class="sxs-lookup"><span data-stu-id="5f394-119">Change the Report Parameter to Accept Multiple Values</span></span>](#Multivalued)  
  
8.  [<span data-ttu-id="5f394-120">조건부 표시에 대한 부울 매개 변수 추가</span><span class="sxs-lookup"><span data-stu-id="5f394-120">Add a Boolean Parameter for Conditional Visibility</span></span>](#Boolean)  
  
9. [<span data-ttu-id="5f394-121">보고서 제목 추가</span><span class="sxs-lookup"><span data-stu-id="5f394-121">Add a Report Title</span></span>](#Title)  
  
10. [<span data-ttu-id="5f394-122">보고서 저장</span><span class="sxs-lookup"><span data-stu-id="5f394-122">Save the Report</span></span>](#Save)  
  
> [!NOTE]  
>  <span data-ttu-id="5f394-123">이 자습서에서 마법사의 단계는 하나의 절차로 통합됩니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-123">In this tutorial, the steps for the wizard are consolidated into one procedure.</span></span> <span data-ttu-id="5f394-124">보고서 서버를 찾고, 데이터 원본을 선택하고, 데이터 세트를 만드는 방법에 대한 단계별 지침은 이 시리즈의 첫 번째 자습서인 [자습서: 기본 테이블 보고서 만들기&#40;보고서 작성기&#41;](../reporting-services/tutorial-creating-a-basic-table-report-report-builder.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5f394-124">For step-by-step instructions about how to browse to a report server, choose a data source, and create a dataset, see the first tutorial in this series: [Tutorial: Creating a Basic Table Report &#40;Report Builder&#41;](../reporting-services/tutorial-creating-a-basic-table-report-report-builder.md).</span></span>  
  
 <span data-ttu-id="5f394-125">이 자습서에 소요되는 예상 시간: 25분</span><span class="sxs-lookup"><span data-stu-id="5f394-125">Estimated time to complete this tutorial: 25 minutes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5f394-126">요구 사항</span><span class="sxs-lookup"><span data-stu-id="5f394-126">Requirements</span></span>  
 <span data-ttu-id="5f394-127">요구 사항에 대한 자세한 내용은 [자습서의 필수 조건&#40;보고서 작성기&#41;](../reporting-services/report-builder-tutorials.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5f394-127">For information about requirements, see [Prerequisites for Tutorials &#40;Report Builder&#41;](../reporting-services/report-builder-tutorials.md).</span></span>  
  
##  <a name="1-create-a-matrix-report-and-dataset-from-the-table-or-matrix-wizard"></a><a name="Setup"></a><span data-ttu-id="5f394-128">1. 테이블 또는 행렬 마법사에서 행렬 보고서 및 데이터 집합 만들기</span><span class="sxs-lookup"><span data-stu-id="5f394-128">1. Create a Matrix Report and Dataset from the Table or Matrix Wizard</span></span>  
 <span data-ttu-id="5f394-129">행렬 보고서, 데이터 원본 및 데이터 세트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-129">Create a matrix report, a data source, and a dataset.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5f394-130">이 자습서의 쿼리에는 데이터 값이 포함되어 있으므로 외부 데이터 원본이 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-130">In this tutorial, the query contains the data values, so that it does not need an external data source.</span></span> <span data-ttu-id="5f394-131">따라서 쿼리가 상당히 길어집니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-131">This makes the query quite long.</span></span> <span data-ttu-id="5f394-132">비즈니스 환경에서는 쿼리에 데이터가 포함되지 않을 것입니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-132">In a business environment, a query would not contain the data.</span></span> <span data-ttu-id="5f394-133">이 자습서의 쿼리는 학습용으로만 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-133">This is for learning purposes only.</span></span>  
  
#### <a name="to-create-a-new-matrix-report"></a><span data-ttu-id="5f394-134">새 행렬 보고서를 만들려면</span><span class="sxs-lookup"><span data-stu-id="5f394-134">To create a new matrix report</span></span>  
  
1.  <span data-ttu-id="5f394-135">**시작**을 클릭 하 고 **프로그램**, 보고서 작성기을 차례로 가리킨 [!INCLUDE[ssCurrentUI](../includes/sscurrentui-md.md)] **Report Builder**다음 **보고서 작성기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-135">Click **Start**, point to **Programs**, point to [!INCLUDE[ssCurrentUI](../includes/sscurrentui-md.md)]**Report Builder**, and then click **Report Builder**.</span></span>  
  
     <span data-ttu-id="5f394-136">**시작** 대화 상자가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-136">The **Getting Started** dialog box appears.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="5f394-137">**시작** 대화 상자가 나타나지 않으면 **보고서 작성기** 단추에서 **새로 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-137">If the **Getting Started** dialog box does not appear, from the **Report Builder** button, click **New**.</span></span>  
  
2.  <span data-ttu-id="5f394-138">왼쪽 창에서 **보고서** 가 선택 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-138">In the left pane, verify that **Report** is selected.</span></span>  
  
3.  <span data-ttu-id="5f394-139">오른쪽 창에서 **테이블 또는 행렬 마법사**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-139">In the right pane, click **Table or Matrix Wizard**.</span></span>  
  
4.  <span data-ttu-id="5f394-140">**만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-140">Click **Create**.</span></span>  
  
5.  <span data-ttu-id="5f394-141">**데이터 세트 선택** 페이지에서 **데이터 세트 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-141">On the **Choose a dataset** page, click **Create a dataset**.</span></span>  
  
6.  <span data-ttu-id="5f394-142">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-142">Click **Next**.</span></span>  
  
7.  <span data-ttu-id="5f394-143">**데이터 원본에 대한 연결 선택** 페이지에서 **SQL Server**형식의 데이터 원본을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-143">On the **Choose a connection to a data source** page, select a data source that is type **SQL Server**.</span></span> <span data-ttu-id="5f394-144">목록에서 데이터 원본을 선택하거나 보고서 서버를 찾아 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-144">Select a data source from the list or browse to the report server to select one.</span></span>  
  
8.  <span data-ttu-id="5f394-145">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-145">Click **Next**.</span></span>  
  
9. <span data-ttu-id="5f394-146">**쿼리 디자인** 페이지에서 **텍스트로 편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-146">On the **Design a query** page, click **Edit as Text**.</span></span>  
  
10. <span data-ttu-id="5f394-147">쿼리 창에 다음 쿼리를 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-147">Paste the following query into the query pane:</span></span>  
  
    ```  
    ;WITH CTE (StoreID, Subcategory, Quantity)   
    AS (  
    SELECT 200 AS StoreID, 'Digital SLR Cameras' AS Subcategory, 2002 AS Quantity  
    UNION SELECT  200 AS StoreID, 'Camcorders' AS Subcategory, 1954 AS Quantity  
    UNION SELECT  200 AS StoreID, 'Accessories' AS Subcategory, 1895 AS Quantity  
    UNION SELECT  199 AS StoreID, 'Digital Cameras' AS Subcategory, 1849 AS Quantity  
    UNION SELECT  306 AS StoreID, 'Digital SLR Cameras' AS Subcategory, 1579 AS Quantity  
    UNION SELECT  306 AS StoreID, 'Camcorders' AS Subcategory, 1561 AS Quantity  
    UNION SELECT  306 AS StoreID, 'Digital Cameras' AS Subcategory, 1553 AS Quantity  
    UNION SELECT  306 AS StoreID, 'Accessories' AS Subcategory, 1534 AS Quantity  
    UNION SELECT 307 AS StoreID, 'Accessories' AS Subcategory, 1755 AS Quantity  
    UNION SELECT 307 AS StoreID, 'Camcorders' AS Subcategory, 1631 AS Quantity  
    UNION SELECT 307 AS StoreID, 'Digital SLR Cameras' AS Subcategory, 1772 AS Quantity)  
    SELECT StoreID, Subcategory, Quantity  
    FROM CTE  
    ```  
  
     <span data-ttu-id="5f394-148">이 쿼리는 공통 테이블 식 안에 있는 몇 가지 [!INCLUDE[tsql](../includes/tsql-md.md)] SELECT 문의 결과를 결합하여 Contoso 예제 데이터베이스의 단순화된 데이터에 따라 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-148">This query combines the results of several [!INCLUDE[tsql](../includes/tsql-md.md)] SELECT statements inside a common table expression to specify values that are based on simplified data from the Contoso sample database.</span></span> <span data-ttu-id="5f394-149">Contoso 판매량 데이터는 소비자 제품에 대한 해외 판매량 데이터를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-149">The Contoso sales data represents international sales data for consumer goods.</span></span> <span data-ttu-id="5f394-150">이 자습서에서는 카메라 판매량 데이터를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-150">This tutorial uses sales data for cameras.</span></span> <span data-ttu-id="5f394-151">하위 범주는 디지털 카메라, 디지털 SLR(Single Lens Reflex) 카메라, 캠코더 및 액세서리를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-151">The subcategories represent digital cameras, digital single lens reflex (SLR) cameras, camcorders, and accessories.</span></span>  
  
     <span data-ttu-id="5f394-152">이 쿼리는 상점 식별자, 판매 항목 하위 범주 및 세 상점의 판매 주문에 대한 주문 수량을 포함하는 열 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-152">The query specifies column names that include a store identifier, a sales item subcategory, and the quantity ordered for sales orders from three stores.</span></span> <span data-ttu-id="5f394-153">이 쿼리에서 상점 이름은 결과 집합에 포함되는 데이터가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-153">In this query, the store name is not part of the result set.</span></span> <span data-ttu-id="5f394-154">이 자습서의 뒷부분에 나오는 별도의 데이터 세트에서 상점 식별자에 해당하는 상점 이름을 조회할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-154">Later in this tutorial, you will look up the name of the store that corresponds to the store identifier from a separate dataset.</span></span>  
  
     <span data-ttu-id="5f394-155">이 쿼리에는 쿼리 매개 변수가 포함되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-155">This query does not contain query parameters.</span></span> <span data-ttu-id="5f394-156">이 자습서의 뒷부분에서 쿼리 매개 변수를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-156">You will add query parameters later in this tutorial.</span></span>  
  
11. <span data-ttu-id="5f394-157">쿼리 디자이너 도구 모음에서 **실행** (**!**)을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-157">On the query designer toolbar, click **Run** (**!**).</span></span> <span data-ttu-id="5f394-158">결과 집합은 4 개 상점의 각 하위 범주에 대해 판매 된 항목의 수량을 표시 하는 11 개 데이터 행을 표시 하 고 StoreID, 하위 범주, 수량 열을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-158">The result set displays 11 rows of data that show the quantity of items sold for each subcategory for four stores, and includes the following columns: StoreID, Subcategory, Quantity.</span></span>  
  
12. <span data-ttu-id="5f394-159">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-159">Click **Next**.</span></span>  
  
##  <a name="2-organize-data-choose-layout-and-style-from-the-table-or-matrix-wizard"></a><a name="CompleteWizard"></a><span data-ttu-id="5f394-160">2. 테이블 또는 행렬 마법사에서 데이터 구성, 레이아웃 및 스타일 선택</span><span class="sxs-lookup"><span data-stu-id="5f394-160">2. Organize Data, Choose Layout, and Style from the Table or Matrix Wizard</span></span>  
 <span data-ttu-id="5f394-161">이 마법사를 사용하여 데이터를 표시할 시작 디자인을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-161">Use the wizard to provide a starting design on which to display data.</span></span> <span data-ttu-id="5f394-162">이 마법사의 미리 보기 창에서는 테이블 또는 행렬 디자인을 완료하기 전에 데이터 그룹화의 결과를 시각화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-162">The preview pane in the wizard helps you to visualize the result of grouping data before you complete the table or matrix design.</span></span>  
  
#### <a name="to-organize-data-into-groups"></a><span data-ttu-id="5f394-163">데이터를 그룹으로 구성하려면</span><span class="sxs-lookup"><span data-stu-id="5f394-163">To organize data into groups</span></span>  
  
1.  <span data-ttu-id="5f394-164">**필드 정렬** 페이지에서 Subcategory를 **행 그룹**으로 끌어옵니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-164">On the **Arrange fields** page, drag Subcategory to **Row groups**.</span></span>  
  
2.  <span data-ttu-id="5f394-165">StoreID를 **열 그룹**으로 끌어옵니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-165">Drag StoreID to **Column groups**.</span></span>  
  
3.  <span data-ttu-id="5f394-166">Quantity를 **값**으로 끌어옵니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-166">Drag Quantity to **Values**.</span></span>  
  
     <span data-ttu-id="5f394-167">하위 범주로 그룹화된 행에 판매 수량 값을 구성했습니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-167">You have organized the quantity sold values in rows grouped by subcategory.</span></span> <span data-ttu-id="5f394-168">각 상점마다 하나의 열이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-168">There will be one column for each store.</span></span>  
  
4.  <span data-ttu-id="5f394-169">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-169">Click **Next**.</span></span>  
  
5.  <span data-ttu-id="5f394-170">**레이아웃 선택** 페이지의 **옵션**에서 **부분합 및 총합계 표시** 가 선택 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-170">On the **Choose a Layout** page, under **Options**, verify that **Show subtotals and grand totals** is selected.</span></span>  
  
     <span data-ttu-id="5f394-171">보고서를 실행하면 마지막 열에 모든 상점에 대한 각 하위 범주의 총 수량이 표시되고 마지막 행에 각 상점에 대한 모든 하위 범주의 총 수량이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-171">When you run the report, the last column will show the total quantity of each subcategory for all stores, and the last row will show the total quantity for all subcategories for each store.</span></span>  
  
6.  <span data-ttu-id="5f394-172">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-172">Click **Next**.</span></span>  
  
7.  <span data-ttu-id="5f394-173">스타일 **선택** 페이지의 스타일 창에서 스타일을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-173">On the **Choose a Style** page, in the Styles pane, select a style.</span></span>  
  
8.  <span data-ttu-id="5f394-174">**Finish**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-174">Click **Finish**.</span></span>  
  
     <span data-ttu-id="5f394-175">디자인 화면에 행렬이 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-175">The matrix is added to the design surface.</span></span> <span data-ttu-id="5f394-176">행렬에는 열 3개와 행 3개가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-176">The matrix displays three columns and three rows.</span></span> <span data-ttu-id="5f394-177">첫 번째 행의 셀 내용은 Subcategory, [StoreID] 및 Total입니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-177">The contents of the cells in the first row are Subcategory, [StoreID], and Total.</span></span> <span data-ttu-id="5f394-178">두 번째 행의 셀 내용에는 하위 범주, 각 상점의 판매 항목 수량 및 모든 상점에 대한 각 하위 범주의 총 수량을 나타내는 식이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-178">The contents of the cells in the second row contain expressions that represent the subcategory, the quantity of items sold for each store, and the total quantity for each subcategory for all stores.</span></span> <span data-ttu-id="5f394-179">마지막 행의 셀에는 각 상점의 총합계가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-179">The cells in the final row display the grand total for each store.</span></span>  
  
9. <span data-ttu-id="5f394-180">행렬을 클릭하고 첫 번째 열의 가장자리로 마우스를 이동한 후 핸들을 잡고 열 너비를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-180">Click in the matrix, hover over the edge of the first column, grab the handle, and expand the column width.</span></span>  
  
10. <span data-ttu-id="5f394-181">**실행** 을 클릭하여 보고서를 미리 봅니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-181">Click **Run** to preview the report.</span></span>  
  
 <span data-ttu-id="5f394-182">보고서가 보고서 서버에서 실행되고 보고서 처리가 수행된 시간과 제목이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-182">The report runs on the report server and displays the title and the time the report processing occurred.</span></span>  
  
 <span data-ttu-id="5f394-183">이 경우 열 머리글에는 상점 이름이 아닌 상점 식별자가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-183">In this scenario, the column headings display the store identifier but not the store name.</span></span> <span data-ttu-id="5f394-184">나중에 상점 식별자/상점 이름 쌍이 포함된 데이터 세트에서 상점 이름을 조회하는 식을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-184">Later, you will add an expression to look up the store name in a dataset that contains store identifier/store name pairs.</span></span>  
  
##  <a name="3-add-a-query-parameter-to-create-a-report-parameter"></a><a name="Query"></a><span data-ttu-id="5f394-185">3. 쿼리 매개 변수를 추가 하 여 보고서 매개 변수 만들기</span><span class="sxs-lookup"><span data-stu-id="5f394-185">3. Add a Query Parameter to Create a Report Parameter</span></span>  
 <span data-ttu-id="5f394-186">쿼리 매개 변수를 쿼리에 추가하면 보고서 작성기가 이름, 프롬프트 및 데이터 형식에 대한 기본 속성을 사용하여 단일 값 보고서 매개 변수를 자동으로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-186">When you add a query parameter to a query, Report Builder automatically creates a single-valued report parameter with default properties for name, prompt, and data type.</span></span>  
  
#### <a name="to-add-a-query-parameter"></a><span data-ttu-id="5f394-187">쿼리 매개 변수를 추가하려면</span><span class="sxs-lookup"><span data-stu-id="5f394-187">To add a query parameter</span></span>  
  
1.  <span data-ttu-id="5f394-188">디자인 뷰로 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-188">Switch to Design view.</span></span>  
  
2.  <span data-ttu-id="5f394-189">보고서 데이터 창에서 **데이터 세트** 폴더를 확장하고 **DataSet1**을 마우스 오른쪽 단추로 클릭한 다음, **쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-189">In the Report Data pane, expand the **Datasets** folder, right-click **DataSet1**, and then click **Query**.</span></span>  
  
3.  <span data-ttu-id="5f394-190">다음 절을 [!INCLUDE[tsql](../includes/tsql-md.md)] `WHERE` 쿼리의 마지막 줄로 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-190">Add the following [!INCLUDE[tsql](../includes/tsql-md.md)] `WHERE` clause as the last line in the query:</span></span>  
  
    ```  
    WHERE StoreID = (@StoreID)  
    ```  
  
     <span data-ttu-id="5f394-191">`WHERE`절은 검색 된 데이터를 쿼리 매개 변수로 지정 된 저장소 식별자로 제한 합니다 *@StoreID* .</span><span class="sxs-lookup"><span data-stu-id="5f394-191">The `WHERE` clause limits the retrieved data to the store identifier that is specified by the query parameter *@StoreID*.</span></span>  
  
4.  <span data-ttu-id="5f394-192">쿼리 디자이너 도구 모음에서 **실행** (**!**)을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-192">On the query designer toolbar, click **Run** (**!**).</span></span> <span data-ttu-id="5f394-193">**쿼리 매개 변수 정의** 대화 상자가 열리고 쿼리 매개 변수 *@StoreID*의 값을 입력하라는 메시지가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-193">The **Define Query Parameters** dialog box opens and prompts for a value for the query parameter *@StoreID*.</span></span>  
  
5.  <span data-ttu-id="5f394-194">**매개 변수 값**에 **200**을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-194">In **Parameter Value**, type **200**.</span></span>  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
     <span data-ttu-id="5f394-195">결과 집합에는 상점 식별자 **200**에 대한 Accessories, Camcorders 및 Digital SLR Cameras의 판매 수량이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-195">The result set displays the quantities sold for Accessories, Camcorders, and Digital SLR Cameras for the store identifier **200**.</span></span>  
  
7.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
8.  <span data-ttu-id="5f394-196">보고서 데이터 창에서 **매개 변수** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-196">In the Report Data pane, expand the **Parameters** folder.</span></span>  
  
 <span data-ttu-id="5f394-197">이제 라는 보고서 매개 변수가 있습니다 *@StoreID* .</span><span class="sxs-lookup"><span data-stu-id="5f394-197">Notice that there is now a report parameter named *@StoreID*.</span></span> <span data-ttu-id="5f394-198">기본적으로 매개 변수의 데이터 형식은 **Text**입니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-198">By default, the parameter has data type **Text**.</span></span> <span data-ttu-id="5f394-199">상점 식별자가 정수이므로 다음 절차에서 데이터 형식을 Integer로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-199">Because the store identifier is an integer, you will change the data type to Integer in the next procedure.</span></span>  
  
##  <a name="4-change-default-data-type-and-other-properties-for-a-report-parameter"></a><a name="ChangeDefaultProperties"></a><span data-ttu-id="5f394-200">4. 보고서 매개 변수의 기본 데이터 형식 및 기타 속성 변경</span><span class="sxs-lookup"><span data-stu-id="5f394-200">4. Change Default Data Type and Other Properties for a Report Parameter</span></span>  
 <span data-ttu-id="5f394-201">보고서 매개 변수를 만든 후 속성의 기본값을 조정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-201">After a report parameter is created, you can adjust the default values for properties.</span></span>  
  
#### <a name="to-change-the-default-data-type-for-a-report-parameter"></a><span data-ttu-id="5f394-202">보고서 매개 변수의 기본 데이터 형식을 변경하려면</span><span class="sxs-lookup"><span data-stu-id="5f394-202">To change the default data type for a report parameter</span></span>  
  
1.  <span data-ttu-id="5f394-203">보고서 데이터 창의 **매개 변수** 노드 아래에서을 마우스 오른쪽 단추로 클릭 한 *@StoreID* 다음 **매개 변수 속성**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-203">In the Report Data pane under the **Parameters** node, right-click *@StoreID*, and then click **Parameter Properties**.</span></span>  
  
2.  <span data-ttu-id="5f394-204">프롬프트에 **Store identifier?** 를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-204">In Prompt, type **Store identifier?**</span></span> <span data-ttu-id="5f394-205">보고서를 실행할 때 이 텍스트가 보고서 뷰어 도구 모음에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-205">This text appears on the report viewer toolbar when you run the report.</span></span>  
  
3.  <span data-ttu-id="5f394-206">**데이터 형식**의 드롭다운 목록에서 **정수**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-206">In **Data type**, from the drop-down list, select **Integer**.</span></span>  
  
4.  <span data-ttu-id="5f394-207">대화 상자의 나머지 기본값을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-207">Accept the remaining default values in the dialog box.</span></span>  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
6.  <span data-ttu-id="5f394-208">보고서를 미리 봅니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-208">Preview the report.</span></span> <span data-ttu-id="5f394-209">보고서 뷰어는에 대 한 프롬프트를 표시 합니다 *@StoreID* .</span><span class="sxs-lookup"><span data-stu-id="5f394-209">The report viewer displays the prompt for *@StoreID*.</span></span>  
  
7.  <span data-ttu-id="5f394-210">보고서 뷰어 도구 모음에서 Store ID 옆에 **200**을 입력한 다음 **보고서 보기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-210">On the report viewer toolbar, next to Store ID, type **200**, and then click **View Report**.</span></span>  
  
##  <a name="4a-add-a-dataset-to-provide-available-values-and-display-names"></a><a name="AddDataset"></a><span data-ttu-id="5f394-211">4a.</span><span class="sxs-lookup"><span data-stu-id="5f394-211">4a.</span></span> <span data-ttu-id="5f394-212">사용 가능한 값과 표시 이름을 제공하는 데이터 세트 추가</span><span class="sxs-lookup"><span data-stu-id="5f394-212">Add a Dataset to Provide Available Values and Display Names</span></span>  
 <span data-ttu-id="5f394-213">선택할 값에 대한 드롭다운 목록을 만들어 사용자가 매개 변수에 대한 유효한 값만 입력하도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-213">To ensure a user can type only valid values for a parameter, you can create a drop-down list of values to choose from.</span></span> <span data-ttu-id="5f394-214">지정한 목록이나 데이터 세트의 값을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-214">The values can come from a dataset or from a list that you specify.</span></span> <span data-ttu-id="5f394-215">쿼리에 매개 변수에 대한 참조가 포함되지 않은 데이터 세트에서 사용 가능한 값을 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-215">Available values must be supplied from a dataset that has a query that does not contain a reference to the parameter.</span></span>  
  
#### <a name="to-create-a-dataset-for-valid-values-for-a-parameter"></a><span data-ttu-id="5f394-216">매개 변수에 대한 유효한 값의 데이터 세트를 만들려면</span><span class="sxs-lookup"><span data-stu-id="5f394-216">To create a dataset for valid values for a parameter</span></span>  
  
1.  <span data-ttu-id="5f394-217">디자인 뷰로 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-217">Switch to Design view.</span></span>  
  
2.  <span data-ttu-id="5f394-218">보고서 데이터 창에서 **데이터 세트** 폴더를 마우스 오른쪽 단추로 클릭한 다음, **데이터 세트 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-218">In the Report Data pane, right-click the **Datasets** folder, and then click **Add Dataset**.</span></span>  
  
3.  <span data-ttu-id="5f394-219">**이름**에 **Stores**를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-219">In **Name**, type **Stores**.</span></span>  
  
4.  <span data-ttu-id="5f394-220">**내 보고서에 포함 된 데이터 집합 사용** 옵션을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-220">Select the **Use a dataset embedded in my report** option.</span></span>  
  
5.  <span data-ttu-id="5f394-221">**데이터 원본**의 드롭다운 목록에서 첫 번째 절차에서 만든 데이터 원본을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-221">In **Data source**, from the drop-down list, choose the data source you created in the first procedure.</span></span>  
  
6.  <span data-ttu-id="5f394-222">**쿼리 유형**에서 **텍스트** 가 선택되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-222">In **Query type**, verify that **Text** is selected.</span></span>  
  
7.  <span data-ttu-id="5f394-223">**쿼리**에 다음 텍스트를 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-223">In **Query**, paste the following text:</span></span>  
  
    ```  
    SELECT 200 AS StoreID, 'Contoso Catalog Store' as StoreName  
    UNION SELECT 199 AS StoreID, 'Contoso North America Online Store' as StoreName  
    UNION SELECT 307 AS StoreID, 'Contoso Asia Online Store' as StoreName  
    UNION SELECT 306 AS StoreID, 'Contoso Europe Online Store' as StoreName  
    ```  
  
8.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
     <span data-ttu-id="5f394-224">보고서 데이터 창의 **Stores** 데이터 세트 노드 아래에 StoreID 및 StoreName 필드가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-224">The Report Data pane displays the fields StoreID and StoreName under the **Stores** dataset node.</span></span>  
  
##  <a name="4b-specify-available-values-to-create-a-drop-down-list-of-values"></a><a name="AvailableValues"></a><span data-ttu-id="5f394-225">4b.</span><span class="sxs-lookup"><span data-stu-id="5f394-225">4b.</span></span> <span data-ttu-id="5f394-226">드롭다운 값 목록을 만드는 데 사용 가능한 값 지정</span><span class="sxs-lookup"><span data-stu-id="5f394-226">Specify Available Values to Create a Drop-down List of Values</span></span>  
 <span data-ttu-id="5f394-227">사용 가능한 값을 제공하는 데이터 세트을 만든 후 보고서 속성을 변경하여 보고서 뷰어 도구 모음의 유효한 값의 드롭다운 목록을 채우는 데 사용할 데이터 세트과 필드를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-227">After you create a dataset to provide available values, you must change the report properties to specify which dataset and which field to use to populate the drop-down list of valid values on the reportviewer toolbar.</span></span>  
  
#### <a name="to-provide-available-values-for-a-parameter-from-a-dataset"></a><span data-ttu-id="5f394-228">데이터 세트의 매개 변수에 사용 가능한 값을 제공하려면</span><span class="sxs-lookup"><span data-stu-id="5f394-228">To provide available values for a parameter from a dataset</span></span>  
  
1.  <span data-ttu-id="5f394-229">보고서 데이터 창에서 매개 변수를 마우스 오른쪽 단추로 클릭 한 *@StoreID* 다음 **매개 변수 속성**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-229">In the Report Data pane, right-click the parameter *@StoreID*, and then click **Parameter Properties**.</span></span>  
  
2.  <span data-ttu-id="5f394-230">**사용 가능한 값**을 클릭한 다음 **쿼리에서 값 가져오기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-230">Click **Available Values**, and then click **Get values from a query**.</span></span>  
  
3.  <span data-ttu-id="5f394-231">**데이터 세트**의 드롭다운 목록에서 **Stores**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-231">In **Dataset**, from the drop-down list, click **Stores**.</span></span>  
  
4.  <span data-ttu-id="5f394-232">**값 필드**의 드롭다운 목록에서 StoreID를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-232">In **Value field**, from the drop-down list, click StoreID.</span></span>  
  
5.  <span data-ttu-id="5f394-233">**레이블 필드**의 드롭다운 목록에서 StoreName을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-233">In **Label field**, from the drop-down list, click StoreName.</span></span> <span data-ttu-id="5f394-234">이 레이블 필드는 값의 표시 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-234">The label field specifies the display name for the value.</span></span>  
  
6.  <span data-ttu-id="5f394-235">**일반**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-235">Click **General**.</span></span>  
  
7.  <span data-ttu-id="5f394-236">프롬프트에 **Store name?** 을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-236">In Prompt, type **Store name?**</span></span>  
  
     <span data-ttu-id="5f394-237">사용자가 이제 상점 식별자 대신 상점 이름의 목록에서 선택하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-237">The user will now select from a list of store names instead of store identifiers.</span></span> <span data-ttu-id="5f394-238">매개 변수가 상점 이름이 아닌 상점 식별자를 기반으로 하기 때문에 매개 변수 데이터 형식은 **Integer** 로 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-238">Note that the parameter data type remains **Integer** because the parameter is based on the store identifier, not the store name.</span></span>  
  
8.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
9. <span data-ttu-id="5f394-239">보고서를 미리 봅니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-239">Preview the report.</span></span>  
  
     <span data-ttu-id="5f394-240">보고서 뷰어 도구 모음에서 매개 변수 입력란은 이제를 표시 하는 드롭다운 목록입니다 **\<Select a Value>** .</span><span class="sxs-lookup"><span data-stu-id="5f394-240">In the report viewer toolbar, the parameter text box is now a drop-down list that displays **\<Select a Value>**.</span></span>  
  
10. <span data-ttu-id="5f394-241">드롭다운 목록에서 Contoso Catalog Store를 선택한 다음 **보고서 보기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-241">From the drop-down list, select Contoso Catalog Store, and then click **View Report**.</span></span>  
  
 <span data-ttu-id="5f394-242">보고서에는 상점 식별자 **200**에 대한 Accessories, Camcorders 및 Digital SLR Cameras의 판매 수량이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-242">The report displays the quantity sold for Accessories, Camcorders, and Digital SLR Cameras for the store identifier **200**.</span></span>  
  
##  <a name="4c-specify-default-values-so-the-report-runs-automatically"></a><a name="DefaultValues"></a><span data-ttu-id="5f394-243">4c.</span><span class="sxs-lookup"><span data-stu-id="5f394-243">4c.</span></span> <span data-ttu-id="5f394-244">보고서가 자동으로 실행되도록 기본값 지정</span><span class="sxs-lookup"><span data-stu-id="5f394-244">Specify Default Values so the Report Runs Automatically</span></span>  
 <span data-ttu-id="5f394-245">보고서가 자동으로 실행되도록 각 매개 변수의 기본값을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-245">You can specify a default value for each parameter so the report runs automatically.</span></span>  
  
#### <a name="to-specify-a-default-value-from-a-dataset"></a><span data-ttu-id="5f394-246">데이터 세트에서 기본값을 지정하려면</span><span class="sxs-lookup"><span data-stu-id="5f394-246">To specify a default value from a dataset</span></span>  
  
1.  <span data-ttu-id="5f394-247">디자인 뷰로 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-247">Switch to Design view.</span></span>  
  
2.  <span data-ttu-id="5f394-248">보고서 데이터 창에서를 마우스 오른쪽 단추로 클릭 한 *@StoreID* 다음 **매개 변수 속성**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-248">In the Report Data pane, right-click *@StoreID*, and then click **Parameter Properties**.</span></span>  
  
3.  <span data-ttu-id="5f394-249">**기본값**을 클릭 한 다음 **쿼리에서 값 가져오기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-249">Click **Default Values**, and then click **Get values from a query**.</span></span>  
  
4.  <span data-ttu-id="5f394-250">**데이터 세트**의 드롭다운 목록에서 **Stores**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-250">In **Dataset**, from the drop-down list, click **Stores**.</span></span>  
  
5.  <span data-ttu-id="5f394-251">**값 필드**의 드롭다운 목록에서 StoreID를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-251">In **Value field**, from the drop-down list, click StoreID.</span></span>  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
7.  <span data-ttu-id="5f394-252">보고서를 미리 봅니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-252">Preview the report.</span></span>  
  
 <span data-ttu-id="5f394-253">의 경우 *@StoreID* 보고서 뷰어에 "Contoso 북아메리카 Online Store" 값이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-253">For *@StoreID*, the report viewer displays the value "Contoso North America Online Store".</span></span> <span data-ttu-id="5f394-254">데이터 집합 **저장소**에 대 한 결과 집합의 첫 번째 값입니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-254">This is the first value from the result set for the dataset **Stores**.</span></span> <span data-ttu-id="5f394-255">보고서에는 상점 식별자 **199**에 대한 Digital Cameras의 판매 수량이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-255">The report displays the quantity sold for Digital Cameras for store identifier **199**.</span></span>  
  
#### <a name="to-specify-a-custom-default-value"></a><span data-ttu-id="5f394-256">사용자 지정 기본값을 지정하려면</span><span class="sxs-lookup"><span data-stu-id="5f394-256">To specify a custom default value</span></span>  
  
1.  <span data-ttu-id="5f394-257">디자인 뷰로 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-257">Switch to Design view.</span></span>  
  
2.  <span data-ttu-id="5f394-258">보고서 데이터 창에서를 마우스 오른쪽 단추로 클릭 한 *@StoreID* 다음 **매개 변수 속성**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-258">In the Report Data pane, right-click *@StoreID*, and then click **Parameter Properties**.</span></span>  
  
3.  <span data-ttu-id="5f394-259">**기본값**을 클릭 하 고 **값 지정**을 클릭 한 다음 **추가**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-259">Click **Default Values**, and click **Specify values**, and then click **Add**.</span></span> <span data-ttu-id="5f394-260">새 값 행이 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-260">A new value row is added.</span></span>  
  
4.  <span data-ttu-id="5f394-261">**값**에 **200**을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-261">In **Value**, type **200**.</span></span>  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
6.  <span data-ttu-id="5f394-262">보고서를 미리 봅니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-262">Preview the report.</span></span>  
  
 <span data-ttu-id="5f394-263">의 경우 *@StoreID* 보고서 뷰어에 "Contoso Catalog Store" 값이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-263">For *@StoreID*, the report viewer displays the value "Contoso Catalog Store".</span></span> <span data-ttu-id="5f394-264">저장소 식별자 **200**에 대 한 표시 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-264">This is the display name for store identifier **200**.</span></span> <span data-ttu-id="5f394-265">보고서에는 상점 식별자 **200**에 대한 Accessories, Camcorders 및 Digital SLR Cameras의 판매 수량이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-265">The report displays the quantity sold for Accessories, Camcorders, and Digital SLR Cameras for the store identifier **200**.</span></span>  
  
##  <a name="4d-look-up-a-value-from-a-dataset-that-has-namevalue-pairs"></a><a name="NameValue"></a><span data-ttu-id="5f394-266">4.</span><span class="sxs-lookup"><span data-stu-id="5f394-266">4d.</span></span> <span data-ttu-id="5f394-267">이름/값 쌍이 있는 데이터 세트에서 값 조회</span><span class="sxs-lookup"><span data-stu-id="5f394-267">Look up a Value from a Dataset that has Name/Value Pairs</span></span>  
 <span data-ttu-id="5f394-268">데이터 세트에는 식별자 및 해당 이름 필드가 포함되어 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-268">A dataset might contain both the identifier and the corresponding name field.</span></span> <span data-ttu-id="5f394-269">식별자만 있는 경우 이름/값 쌍이 포함된 만든 데이터 세트에서 해당 이름을 조회할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-269">When you only have an identifier, you can look up the corresponding name in a dataset that you created that includes name/value pairs.</span></span>  
  
#### <a name="to-look-up-a-value-from-a-dataset"></a><span data-ttu-id="5f394-270">데이터 세트에서 값을 조회하려면</span><span class="sxs-lookup"><span data-stu-id="5f394-270">To look up a value from a dataset</span></span>  
  
1.  <span data-ttu-id="5f394-271">디자인 뷰로 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-271">Switch to Design view.</span></span>  
  
2.  <span data-ttu-id="5f394-272">디자인 화면에서 행렬에 있는 첫 번째 행의 열 머리글에서 `[StoreID]` 를 마우스 오른쪽 단추로 클릭한 다음 **식**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-272">On the design surface, in the matrix, in the first row column header, right-click `[StoreID]` and then click **Expression**.</span></span>  
  
3.  <span data-ttu-id="5f394-273">식 창에서 시작 부분의 `equals`(=)를 제외한 텍스트를 모두 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-273">In the expression pane, delete all text except the beginning `equals` (=).</span></span>  
  
4.  <span data-ttu-id="5f394-274">**범주**에서 **일반 함수**를 확장하고 **기타**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-274">In **Category**, expand **Common Functions**, and click **Miscellaneous**.</span></span> <span data-ttu-id="5f394-275">항목 창에 함수 집합이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-275">The Item pane displays a set of functions.</span></span>  
  
5.  <span data-ttu-id="5f394-276">항목에서 **조회**를 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-276">In Item, double-click **Lookup**.</span></span> <span data-ttu-id="5f394-277">식 창에 `=Lookup(`이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-277">The expression pane displays `=Lookup(`.</span></span> <span data-ttu-id="5f394-278">예제 창에 Lookup 구문 예가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-278">The Example pane displays an example of Lookup syntax.</span></span>  
  
6.  <span data-ttu-id="5f394-279">다음 식을 입력합니다. `=Lookup(Fields!StoreID.Value,Fields!StoreID.Value,Fields!StoreName.Value,"Stores")`</span><span class="sxs-lookup"><span data-stu-id="5f394-279">Type the following expression: `=Lookup(Fields!StoreID.Value,Fields!StoreID.Value,Fields!StoreName.Value,"Stores")`</span></span>  
  
     <span data-ttu-id="5f394-280">Lookup 함수가 StoreID의 값을 사용하여 "Stores" 데이터 세트에서 조회하고 StoreName 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-280">The Lookup function takes the value for StoreID, looks it up in the "Stores" dataset, and returns the StoreName value.</span></span>  
  
7.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
     <span data-ttu-id="5f394-281">저장소 열 머리글은 복합 식에 대 한 표시 텍스트를 포함 합니다 **<\<Expr>>** .</span><span class="sxs-lookup"><span data-stu-id="5f394-281">The store column header contains the display text for a complex expression: **<\<Expr>>**.</span></span>  
  
8.  <span data-ttu-id="5f394-282">보고서를 미리 봅니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-282">Preview the report.</span></span>  
  
 <span data-ttu-id="5f394-283">각 페이지의 맨 위 입력란에 상점 식별자 대신 상점 이름이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-283">The text box at the top of each page displays the store name instead of the store identifier.</span></span>  
  
##  <a name="5-display-the-selected-parameter-value-in-the-report"></a><a name="Expression"></a><span data-ttu-id="5f394-284">5. 보고서에 선택한 매개 변수 값 표시</span><span class="sxs-lookup"><span data-stu-id="5f394-284">5. Display the Selected Parameter Value in the Report</span></span>  
 <span data-ttu-id="5f394-285">사용자가 보고서에 대해 궁금한 사항이 있는 경우 사용자가 선택한 매개 변수 값을 알면 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-285">When a user has questions about a report, it helps to know which parameter values they chose.</span></span> <span data-ttu-id="5f394-286">각 매개 변수에 대해 사용자가 선택한 값을 보고서에 유지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-286">You can preserve user-selected values for each parameter in the report.</span></span> <span data-ttu-id="5f394-287">입력란의 매개 변수를 페이지 바닥글에 표시하는 것이 한 가지 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-287">One way is to display the parameters in a text box in the page footer.</span></span>  
  
#### <a name="to-display-the-selected-parameter-value-and-label-on-a-page-footer"></a><span data-ttu-id="5f394-288">선택한 매개 변수 값 및 레이블을 페이지 바닥글에 표시하려면</span><span class="sxs-lookup"><span data-stu-id="5f394-288">To display the selected parameter value and label on a page footer</span></span>  
  
1.  <span data-ttu-id="5f394-289">디자인 뷰로 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-289">Switch to Design view.</span></span>  
  
2.  <span data-ttu-id="5f394-290">페이지 바닥글을 마우스 오른쪽 단추로 클릭 하 고 **삽입**을 가리킨 다음 **텍스트 상자**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-290">Right-click the page footer, point to **Insert**, and then click **Text Box**.</span></span> <span data-ttu-id="5f394-291">입력란을 타임스탬프가 있는 입력란 옆으로 끌어옵니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-291">Drag the text box next to the text box with the time stamp.</span></span> <span data-ttu-id="5f394-292">입력란의 측면 핸들을 잡고 너비를 확장합니다</span><span class="sxs-lookup"><span data-stu-id="5f394-292">Grab the side handle of the text box and expand the width.</span></span>  
  
3.  <span data-ttu-id="5f394-293">보고서 데이터 창에서 매개 변수를 *@StoreID* 입력란으로 끌어 옵니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-293">From the Report Data pane, drag the parameter *@StoreID* to the text box.</span></span> <span data-ttu-id="5f394-294">입력란에 `[@StoreID]`가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-294">The text box displays `[@StoreID]`.</span></span>  
  
4.  <span data-ttu-id="5f394-295">매개 변수 레이블을 표시하려면 삽입 커서가 기존 식 뒤에 나타날 때까지 입력란을 클릭하고 공백을 입력한 다음 매개 변수의 또 다른 복사본을 보고서 데이터 창에서 입력란으로 끌어옵니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-295">To display the parameter label, click in the text box until the insert cursor appears after the existing expression, type a space, and then drag another copy of the parameter from the Report Data pane to the text box.</span></span> <span data-ttu-id="5f394-296">입력란에 `[@StoreID] [@StoreID]`가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-296">The text box displays `[@StoreID] [@StoreID]`.</span></span>  
  
5.  <span data-ttu-id="5f394-297">첫 번째 식을 마우스 오른쪽 단추로 클릭 하 고 **식**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-297">Right-click the first expression and click **Expression**.</span></span> <span data-ttu-id="5f394-298">**식** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-298">The **Expression** dialog box opens.</span></span> <span data-ttu-id="5f394-299">`Value` 텍스트를 `Label`로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-299">Replace the text `Value` by `Label`.</span></span>  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
     <span data-ttu-id="5f394-300">`[@StoreID.Label] [@StoreID]`텍스트가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-300">The text displays: `[@StoreID.Label] [@StoreID]`.</span></span>  
  
7.  <span data-ttu-id="5f394-301">보고서를 미리 봅니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-301">Preview the report.</span></span>  
  
##  <a name="6-use-the-report-parameter-in-a-filter"></a><a name="Filter"></a><span data-ttu-id="5f394-302">6. 필터에서 보고서 매개 변수 사용</span><span class="sxs-lookup"><span data-stu-id="5f394-302">6. Use the Report Parameter in a Filter</span></span>  
 <span data-ttu-id="5f394-303">필터를 사용하면 외부 데이터 원본에서 검색된 데이터 중 보고서에 사용할 데이터를 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-303">Filters help control which data to use in a report after it is retrieved from an external data source.</span></span> <span data-ttu-id="5f394-304">사용자가 표시할 데이터를 제어할 수 있도록 하기 위해 행렬에 대한 필터에 보고서 매개 변수를 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-304">To let a user help control the data they want to see, you can include the report parameter in a filter for the matrix.</span></span>  
  
#### <a name="to-specify-a-parameter-in-a-matrix-filter"></a><span data-ttu-id="5f394-305">행렬 필터에서 매개 변수를 지정하려면</span><span class="sxs-lookup"><span data-stu-id="5f394-305">To specify a parameter in a matrix filter</span></span>  
  
1.  <span data-ttu-id="5f394-306">디자인 뷰로 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-306">Switch to Design view.</span></span>  
  
2.  <span data-ttu-id="5f394-307">행렬에서 행 또는 열 머리글 핸들을 마우스 오른쪽 단추로 클릭한 다음 **테이블릭스 속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-307">Right-click a row or column header handle on the matrix, and then click **Tablix Properties**.</span></span>  
  
3.  <span data-ttu-id="5f394-308">**필터**를 클릭한 다음 **추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-308">Click **Filters**, and then click **Add**.</span></span> <span data-ttu-id="5f394-309">새 필터 행이 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-309">A new filter row appears.</span></span>  
  
4.  <span data-ttu-id="5f394-310">**식**의 드롭다운 목록에서 데이터 세트 필드 StoreID를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-310">In **Expression**, from the drop-down list, select the dataset field StoreID.</span></span> <span data-ttu-id="5f394-311">데이터 형식에 **Integer**가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-311">The data type displays **Integer**.</span></span> <span data-ttu-id="5f394-312">식 값이 데이터 세트 필드이면 데이터 형식이 자동으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-312">When the expression value is a dataset field, the data type is set automatically.</span></span>  
  
5.  <span data-ttu-id="5f394-313">**연산자**에서 `equals` (=)가 선택 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-313">In **Operator**, verify that `equals` (=) is selected.</span></span>  
  
6.  <span data-ttu-id="5f394-314">**값**에서`[@StoreID]`을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-314">In **Value**, type `[@StoreID]`.</span></span> <span data-ttu-id="5f394-315">`[@StoreID]` 는 `=Parameters!StoreID.Value`를 나타내는 단순 식 구문입니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-315">`[@StoreID]` is the simple expression syntax that represents `=Parameters!StoreID.Value`.</span></span>  
  
7.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
8.  <span data-ttu-id="5f394-316">보고서를 미리 봅니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-316">Preview the report.</span></span>  
  
     <span data-ttu-id="5f394-317">행렬에 "Contoso Catalog Store"에 대한 데이터만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-317">The matrix displays data only for "Contoso Catalog Store".</span></span>  
  
9. <span data-ttu-id="5f394-318">보고서 뷰어 도구 모음에서 **Store name?** 으로 **Contoso Asia Online Store**를 선택한 다음 **보고서 보기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-318">On the report viewer toolbar, for **Store name?**, select **Contoso Asia Online Store**, and then click **View Report**.</span></span>  
  
 <span data-ttu-id="5f394-319">행렬에 선택한 상점에 해당하는 데이터가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-319">The matrix displays data that corresponds to the store that you selected.</span></span>  
  
##  <a name="7-change-the-report-parameter-to-accept-multiple-values"></a><a name="Multivalued"></a><span data-ttu-id="5f394-320">7. 여러 값을 허용 하도록 보고서 매개 변수 변경</span><span class="sxs-lookup"><span data-stu-id="5f394-320">7. Change the Report Parameter to Accept Multiple Values</span></span>  
 <span data-ttu-id="5f394-321">매개 변수를 단일 값 매개 변수에서 다중값 매개 변수로 변경하려면 필터를 비롯해 매개 변수에 대한 참조가 포함된 모든 식과 쿼리를 변경해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-321">To change a parameter from single to multivalued, you must change the query, and all expressions that contain a reference to the parameter, including filters.</span></span> <span data-ttu-id="5f394-322">다중값 매개 변수는 값 배열입니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-322">A multivalued parameter is an array of values.</span></span> <span data-ttu-id="5f394-323">데이터 세트 쿼리에서 쿼리 구문을 통해 한 값의 값 집합 포함 여부를 테스트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-323">In a dataset query, query syntax must test for inclusion of one value in a set of values.</span></span> <span data-ttu-id="5f394-324">보고서 식에서 식 구문은 개별 값이 아닌 값 배열에 액세스해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-324">In a report expression, expression syntax must access an array of values instead of an individual value.</span></span>  
  
#### <a name="to-change-a-parameter-from-single-to-multivalued"></a><span data-ttu-id="5f394-325">매개 변수를 단일 값 매개 변수에서 다중값 매개 변수로 변경하려면</span><span class="sxs-lookup"><span data-stu-id="5f394-325">To change a parameter from single to multivalued</span></span>  
  
1.  <span data-ttu-id="5f394-326">디자인 뷰로 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-326">Switch to Design view.</span></span>  
  
2.  <span data-ttu-id="5f394-327">보고서 데이터 창에서를 마우스 오른쪽 단추로 클릭 한 *@StoreID* 다음 **매개 변수 속성**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-327">In the Report Data pane, right-click *@StoreID*, and then click **Parameter Properties**.</span></span>  
  
3.  <span data-ttu-id="5f394-328">**다중 값 허용**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-328">Select **Allow multiple values**.</span></span>  
  
4.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
5.  <span data-ttu-id="5f394-329">보고서 데이터 창에서 **데이터 세트** 폴더를 확장하고 **DataSet1**을 마우스 오른쪽 단추로 클릭한 다음, **쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-329">In the Report Data pane, expand the **Datasets** folder, right-click **DataSet1**, and then click **Query**.</span></span>  
  
6.  <span data-ttu-id="5f394-330">`equals` `IN` [!INCLUDE[tsql](../includes/tsql-md.md)] 쿼리의 마지막 줄에 있는 절에서 (=)를로 변경 합니다 `WHERE` .</span><span class="sxs-lookup"><span data-stu-id="5f394-330">Change `equals` (=) to `IN` in the [!INCLUDE[tsql](../includes/tsql-md.md)] `WHERE` clause in the last line in the query:</span></span>  
  
    ```  
    WHERE StoreID IN (@StoreID)  
    ```  
  
     <span data-ttu-id="5f394-331">`IN` 연산자는 값의 값 집합 포함 여부를 테스트합니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-331">The `IN` operator tests a value for inclusion in a set of values.</span></span>  
  
7.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
8.  <span data-ttu-id="5f394-332">행렬에서 행 또는 열 머리글 핸들을 마우스 오른쪽 단추로 클릭한 다음 **테이블릭스 속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-332">Right-click a row or column header handle on the matrix, and then click **Tablix Properties**.</span></span>  
  
9. <span data-ttu-id="5f394-333">**필터**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-333">Click **Filters**.</span></span>  
  
10. <span data-ttu-id="5f394-334">**연산자**에서 **In**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-334">In **Operator**, select **In**.</span></span>  
  
11. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
12. <span data-ttu-id="5f394-335">페이지 바닥글에 매개 변수가 표시되는 입력란에서 모든 텍스트를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-335">In the text box that displays the parameter in the page footer, delete all text.</span></span>  
  
13. <span data-ttu-id="5f394-336">입력란을 마우스 오른쪽 단추로 클릭한 다음 **식**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-336">Right-click the text box, and then click **Expression**.</span></span> <span data-ttu-id="5f394-337">다음 식을 입력합니다. `=Join(Parameters!StoreID.Label, ", ")`</span><span class="sxs-lookup"><span data-stu-id="5f394-337">Type the following expression: `=Join(Parameters!StoreID.Label, ", ")`</span></span>  
  
     <span data-ttu-id="5f394-338">이 식은 사용자가 선택한 모든 상점 이름을 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-338">This expression concatenates all store names that the user selected.</span></span>  
  
14. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
15. <span data-ttu-id="5f394-339">방금 만든 식 앞의 텍스트 상자를 클릭 하 고 다음을 입력 합니다. 매개 변수 값 선택:.</span><span class="sxs-lookup"><span data-stu-id="5f394-339">Click in the text box in front of the expression that you just created, and then type the following: Parameter Values Selected:.</span></span>  
  
16. <span data-ttu-id="5f394-340">보고서를 미리 봅니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-340">Preview the report.</span></span>  
  
17. <span data-ttu-id="5f394-341">Store Name? 옆의 드롭다운 목록을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-341">Click the drop-down list next to Store Name?</span></span>  
  
     <span data-ttu-id="5f394-342">각각의 유효한 값이 확인란 옆에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-342">Each valid value appears next to a check box.</span></span>  
  
18. <span data-ttu-id="5f394-343">**모두 선택**을 클릭한 다음 **보고서 보기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-343">Click **Select All**, and then click **View Report**.</span></span>  
  
     <span data-ttu-id="5f394-344">보고서에 모든 상점에 대한 모든 하위 범주의 판매 수량이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-344">The report displays the quantity sold for all subcategories for all stores.</span></span>  
  
19. <span data-ttu-id="5f394-345">드롭다운 목록에서 **모두 선택** 을 클릭하여 목록을 지우고 "Contoso Catalog Store"와 "Contoso Asia Online Store"를 차례로 클릭한 다음 **보고서 보기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-345">From the drop-down list, click **Select All** to clear the list, click "Contoso Catalog Store" and "Contoso Asia Online Store", and then click **View Report**.</span></span>  
  
##  <a name="8-add-a-boolean-parameter-for-conditional-visibility"></a><a name="Boolean"></a><span data-ttu-id="5f394-346">8. 조건부 표시에 대 한 부울 매개 변수 추가</span><span class="sxs-lookup"><span data-stu-id="5f394-346">8. Add a Boolean Parameter for Conditional Visibility</span></span>  
  
#### <a name="to-add-a-boolean-parameter"></a><span data-ttu-id="5f394-347">부울 매개 변수를 추가하려면</span><span class="sxs-lookup"><span data-stu-id="5f394-347">To add a boolean parameter</span></span>  
  
1.  <span data-ttu-id="5f394-348">디자인 화면의 보고서 데이터 창에서 **매개 변수**를 마우스 오른쪽 단추로 클릭한 다음 **매개 변수 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-348">On the design surface, in the Report Data pane, right-click **Parameters**, and click **Add Parameter**.</span></span>  
  
2.  <span data-ttu-id="5f394-349">**이름**에 ShowSelections를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-349">In **Name**, type ShowSelections.</span></span>  
  
3.  <span data-ttu-id="5f394-350">**프롬프트**에 Show selections?를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-350">In **Prompt**, type Show selections?</span></span>  
  
4.  <span data-ttu-id="5f394-351">**데이터 형식**의 드롭다운 목록에서 **부울**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-351">In **Data type**, from the drop-down list, click **Boolean**.</span></span>  
  
5.  <span data-ttu-id="5f394-352">**기본값**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-352">Click **Default Values**.</span></span>  
  
6.  <span data-ttu-id="5f394-353">**값 지정**을 클릭한 다음 **추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-353">Click **Specify value**, and then click **Add**.</span></span>  
  
7.  <span data-ttu-id="5f394-354">**값**에 **False**를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-354">In **Value**, type **False**.</span></span>  
  
8.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
#### <a name="to-set-visibility-based-on-a-boolean-parameter"></a><span data-ttu-id="5f394-355">부울 매개 변수에 따라 표시 유형을 설정하려면</span><span class="sxs-lookup"><span data-stu-id="5f394-355">To set visibility based on a boolean parameter</span></span>  
  
1.  <span data-ttu-id="5f394-356">디자인 화면에서 매개 변수 값이 표시되는 페이지 바닥글의 입력란을 마우스 오른쪽 단추로 클릭한 다음 **입력란 속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-356">On the design surface, right-click the text box in the page footer that displays the parameter values, and then click **Text Box Properties**.</span></span>  
  
2.  <span data-ttu-id="5f394-357">**표시 유형**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-357">Click **Visibility**.</span></span>  
  
3.  <span data-ttu-id="5f394-358">**식에 따라 표시 또는 숨기기**옵션을 선택한 다음 **Fx**식 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-358">Select the option **Show or hide based on an expression**, and then click the expression button **Fx**.</span></span>  
  
4.  <span data-ttu-id="5f394-359">다음 식을 입력합니다. `=Not Parameters!ShowSelections.Value`</span><span class="sxs-lookup"><span data-stu-id="5f394-359">Type the following expression: `=Not Parameters!ShowSelections.Value`</span></span>  
  
     <span data-ttu-id="5f394-360">입력란의 표시 유형 옵션은 Hidden 속성을 사용하여 제어됩니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-360">The text box Visibility option is controlled by the property Hidden.</span></span> <span data-ttu-id="5f394-361">매개 변수를 선택할 경우 Hidden 속성이 False이고 입력란이 표시되도록 `Not` 연산자를 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-361">Apply the `Not` operator so that when the parameter is selected, the Hidden property is false, and the text box will be displayed.</span></span>  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
7.  <span data-ttu-id="5f394-362">보고서를 미리 봅니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-362">Preview the report.</span></span>  
  
     <span data-ttu-id="5f394-363">매개 변수 선택 항목이 표시되는 입력란이 나타나지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-363">The text box that displays the parameter choices does not appear.</span></span>  
  
8.  <span data-ttu-id="5f394-364">보고서 뷰어 도구 모음에서 **선택 항목 표시**옆의을 클릭 `True` 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-364">In the report viewer toolbar, next to **Show selections**, click `True`.</span></span>  
  
9. <span data-ttu-id="5f394-365">보고서를 미리 봅니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-365">Preview the report.</span></span>  
  
 <span data-ttu-id="5f394-366">페이지 바닥글의 입력란에 선택한 모든 상점 이름이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-366">The text box in the page footer displays all the store names that you selected.</span></span>  
  
##  <a name="9-add-a-report-title"></a><a name="Title"></a><span data-ttu-id="5f394-367">9. 보고서 제목 추가</span><span class="sxs-lookup"><span data-stu-id="5f394-367">9. Add a Report Title</span></span>  
  
#### <a name="to-add-a-report-title"></a><span data-ttu-id="5f394-368">보고서 제목을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="5f394-368">To add a report title</span></span>  
  
1.  <span data-ttu-id="5f394-369">디자인 화면에서 **제목을 추가하려면 클릭하십시오.** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-369">On the design surface, click **Click to add title**.</span></span>  
  
2.  <span data-ttu-id="5f394-370">Parameterized Product Sales를 입력한 다음 입력란 바깥쪽을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-370">Type Parameterized Product Sales, and then click outside the text box.</span></span>  
  
##  <a name="10-save-the-report"></a><a name="Save"></a><span data-ttu-id="5f394-371">10. 보고서 저장</span><span class="sxs-lookup"><span data-stu-id="5f394-371">10. Save the Report</span></span>  
  
#### <a name="to-save-the-report-on-a-report-server"></a><span data-ttu-id="5f394-372">보고서를 보고서 서버에 저장하려면</span><span class="sxs-lookup"><span data-stu-id="5f394-372">To save the report on a report server</span></span>  
  
1.  <span data-ttu-id="5f394-373">**보고서 작성기** 단추에서 다른 **이름으로 저장**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-373">From the **Report Builder** button, click **Save As**.</span></span>  
  
2.  <span data-ttu-id="5f394-374">**최근에 사용한 사이트 및 서버**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-374">Click **Recent Sites and Servers**.</span></span>  
  
3.  <span data-ttu-id="5f394-375">보고서를 저장할 수 있는 권한을 가진 보고서 서버의 이름을 선택하거나 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-375">Select or type the name of the report server where you have permission to save reports.</span></span>  
  
     <span data-ttu-id="5f394-376">**보고서 서버에 연결하는 중**이라는 메시지가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-376">The message **Connecting to report server appears**.</span></span> <span data-ttu-id="5f394-377">연결되면 보고서 서버 관리자가 보고서의 기본 위치로 지정한 보고서 폴더의 내용이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-377">When the connection is complete, you see the contents of the report folder that the report server administrator specified as the default location for reports.</span></span>  
  
4.  <span data-ttu-id="5f394-378">**이름**에서 기본 이름을 Parameterized Sales Report로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-378">In **Name**, replace the default name with Parameterized Sales Report.</span></span>  
  
5.  <span data-ttu-id="5f394-379">**저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-379">Click **Save**.</span></span>  
  
 <span data-ttu-id="5f394-380">보고서가 보고서 서버에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-380">The report is saved to the report server.</span></span> <span data-ttu-id="5f394-381">연결된 보고서 서버는 창 아래쪽에 있는 상태 표시줄에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-381">The report server that you are connected to appears in the status bar at the bottom of the window.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="5f394-382">다음 단계</span><span class="sxs-lookup"><span data-stu-id="5f394-382">Next Steps</span></span>  
 <span data-ttu-id="5f394-383">보고서에 매개 변수를 추가하는 방법에 대한 연습을 완료했습니다.</span><span class="sxs-lookup"><span data-stu-id="5f394-383">This concludes the walkthrough for how to add a parameter to your report.</span></span> <span data-ttu-id="5f394-384">매개 변수에 대한 자세한 내용은 [보고서 매개 변수&#40;보고서 작성기 및 보고서 디자이너&#41;](report-design/report-parameters-report-builder-and-report-designer.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5f394-384">To learn more about parameters, see [Report Parameters &#40;Report Builder and Report Designer&#41;](report-design/report-parameters-report-builder-and-report-designer.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f394-385">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5f394-385">See Also</span></span>  
 <span data-ttu-id="5f394-386">[자습서 &#40;보고서 작성기&#41;](report-builder-tutorials.md) </span><span class="sxs-lookup"><span data-stu-id="5f394-386">[Tutorials &#40;Report Builder&#41;](report-builder-tutorials.md) </span></span>  
 [<span data-ttu-id="5f394-387">SQL Server 2014의 보고서 작성기</span><span class="sxs-lookup"><span data-stu-id="5f394-387">Report Builder in SQL Server 2014</span></span>](report-builder/report-builder-in-sql-server-2016.md)  
  
  
