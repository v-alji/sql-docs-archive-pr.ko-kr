---
title: 보고서에 연계 매개 변수 추가(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 3a22eec3-57a7-478e-b6fc-102a9dbe0591
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 5419d448b2fa9526224e1bccd80d5c195e2763d7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729048"
---
# <a name="add-cascading-parameters-to-a-report-report-builder-and-ssrs"></a><span data-ttu-id="bd2b8-102">보고서에 연계 매개 변수 추가(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="bd2b8-102">Add Cascading Parameters to a Report (Report Builder and SSRS)</span></span>
  <span data-ttu-id="bd2b8-103">연계 매개 변수를 사용하면 대량의 보고서 데이터를 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-103">Cascading parameters provide a way of managing large amounts of report data.</span></span> <span data-ttu-id="bd2b8-104">한 매개 변수의 값 목록이 다른 매개 변수에서 선택한 값에 따라 달라지는 관련 매개 변수 집합을 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-104">You can define a set of related parameters so that the list of values for one parameter depends on the value chosen in another parameter.</span></span> <span data-ttu-id="bd2b8-105">예를 들어 첫 번째 매개 변수가 제품 범주 목록을 나타내는 독립적인 매개 변수이고</span><span class="sxs-lookup"><span data-stu-id="bd2b8-105">For example, the first parameter is independent and might present a list of product categories.</span></span> <span data-ttu-id="bd2b8-106">사용자가 범주를 선택하면 두 번째 매개 변수가 첫 번째 매개 변수의 값에 종속됩니다.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-106">When the user selects a category, the second parameter is dependent on the value of the first parameter.</span></span> <span data-ttu-id="bd2b8-107">즉, 두 번째 매개 변수의 값이 선택된 범위 내 하위 범주의 목록으로 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-107">Its values are updated with a list of subcategories within the chosen category.</span></span> <span data-ttu-id="bd2b8-108">사용자가 보고서를 볼 때 범주 및 하위 범주 매개 변수 모두에 대한 값으로 보고서 데이터가 필터링됩니다.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-108">When the user views the report, the values for both the category and subcategory parameters are used to filter report data.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
 <span data-ttu-id="bd2b8-109">연계 매개 변수를 만들려면 먼저 데이터 세트 쿼리를 정의하고 필요한 각 연계 매개 변수에 대한 쿼리 매개 변수를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-109">To create cascading parameters, you define the dataset query first and include a query parameter for each cascading parameter that you need.</span></span> <span data-ttu-id="bd2b8-110">또한 각 연계 매개 변수마다 별도의 데이터 세트를 만들어 사용 가능한 값을 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-110">You must also create a separate dataset for each cascading parameter to provide available values.</span></span> <span data-ttu-id="bd2b8-111">자세한 내용은 [보고서 매개 변수의 사용 가능한 값 추가, 변경 또는 삭제&#40;보고서 작성기 및 SSRS&#41;](add-change-or-delete-available-values-for-a-report-parameter.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-111">For more information, see [Add, Change, or Delete Available Values for a Report Parameter &#40;Report Builder and SSRS&#41;](add-change-or-delete-available-values-for-a-report-parameter.md).</span></span>  
  
 <span data-ttu-id="bd2b8-112">목록 뒷부분의 매개 변수에 대한 데이터 세트 쿼리에는 목록 앞부분의 각 매개 변수에 대한 참조가 포함되므로 연계 매개 변수에서는 순서가 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-112">Order is important for cascading parameters because the dataset query for a parameter later in the list includes a reference to each parameter that is earlier in the list.</span></span> <span data-ttu-id="bd2b8-113">보고서 데이터 창의 매개 변수 순서에 따라 런타임에 보고서에 매개 변수 쿼리가 나타나는 순서가 결정되며 따라서 사용자가 각각의 연속된 매개 변수 값을 선택하는 순서가 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-113">At run time, the order of the parameters in the Report Data pane determines the order in which the parameter queries appear in the report, and therefore, the order in which a user chooses each successive parameter value.</span></span>  
  
 <span data-ttu-id="bd2b8-114">여러 값을 갖는 연계 매개 변수를 만들고 모두 선택 기능을 포함하는 방법은 [모두 선택 다중값 연계 매개 변수를 만드는 방법](https://go.microsoft.com/fwlink/?LinkId=184757)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-114">For information about creating cascading parameters with multiple values and including the Select All feature, see [How to have a Select All Multivalue Cascading Parameter](https://go.microsoft.com/fwlink/?LinkId=184757).</span></span>  
  
### <a name="to-create-the-main-dataset-with-a-query-that-includes-multiple-related-parameters"></a><span data-ttu-id="bd2b8-115">관련된 여러 매개 변수가 포함된 쿼리가 있는 기본 데이터 세트를 만들려면</span><span class="sxs-lookup"><span data-stu-id="bd2b8-115">To create the main dataset with a query that includes multiple related parameters</span></span>  
  
1.  <span data-ttu-id="bd2b8-116">보고서 데이터 창에서 데이터 원본을 마우스 오른쪽 단추로 클릭한 다음, **데이터 세트 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-116">In the Report Data pane, right-click a data source, and then click **Add Dataset**.</span></span>  
  
2.  <span data-ttu-id="bd2b8-117">**이름**에 데이터 세트의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-117">In **Name**, type the name of the dataset.</span></span>  
  
3.  <span data-ttu-id="bd2b8-118">**데이터 원본**에서 데이터 원본의 이름을 선택하거나 **새로 만들기** 를 클릭하여 데이터 원본을 새로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-118">In **Data source**, choose the name of the data source or click **New** to create one.</span></span>  
  
4.  <span data-ttu-id="bd2b8-119">**쿼리 유형**에서 선택된 데이터 원본에 대한 쿼리 유형을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-119">In **Query type**, choose the type of query for the selected data source.</span></span> <span data-ttu-id="bd2b8-120">이 항목에서는 **텍스트** 쿼리 유형을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-120">In this topic, query type **Text** is assumed.</span></span>  
  
5.  <span data-ttu-id="bd2b8-121">**쿼리**에서 이 보고서의 데이터를 검색하는 데 사용할 쿼리를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-121">In **Query**, type the query to use to retrieve data for this report.</span></span> <span data-ttu-id="bd2b8-122">쿼리에는 다음 부분이 포함되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-122">The query must include the following parts:</span></span>  
  
    1.  <span data-ttu-id="bd2b8-123">데이터 원본 필드의 목록.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-123">A list of data source fields.</span></span> <span data-ttu-id="bd2b8-124">예를 들어 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문에서 SELECT 문은 해당 테이블 또는 뷰의 데이터베이스 열 이름 목록을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-124">For example, in a [!INCLUDE[tsql](../../includes/tsql-md.md)] statement, the SELECT statement specifies a list of database column names from a given table or view.</span></span>  
  
    2.  <span data-ttu-id="bd2b8-125">각 연계 매개 변수당 하나의 쿼리 매개 변수.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-125">One query parameter for each cascading parameter.</span></span> <span data-ttu-id="bd2b8-126">쿼리 매개 변수는 쿼리에서 포함하거나 제외할 값을 지정하여 데이터 원본에서 검색되는 데이터를 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-126">A query parameter limits the data retrieved from the data source by specifying certain values to include or exclude from the query.</span></span> <span data-ttu-id="bd2b8-127">일반적으로 쿼리 매개 변수는 쿼리의 제약 조건 절에 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-127">Typically, query parameters occur in a restriction clause in the query.</span></span> <span data-ttu-id="bd2b8-128">예를 들어 [!INCLUDE[tsql](../../includes/tsql-md.md)] SELECT 문에서는 WHERE 절에 쿼리 매개 변수를 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-128">For example, in a [!INCLUDE[tsql](../../includes/tsql-md.md)] SELECT statement, query parameters occur in the WHERE clause.</span></span> <span data-ttu-id="bd2b8-129">자세한 내용은 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SQL Server 온라인 설명서 [의](https://go.microsoft.com/fwlink/?linkid=120955)설명서에 있는 "WHERE 및 HAVING을 사용하여 행 필터링"을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-129">For more information, see "Filtering Rows by Using WHERE and HAVING" in the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] documentation in [SQL Server Books Online](https://go.microsoft.com/fwlink/?linkid=120955).</span></span>  
  
6.  <span data-ttu-id="bd2b8-130">**실행** (**!**)을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-130">Click **Run** (**!**).</span></span> <span data-ttu-id="bd2b8-131">쿼리 매개 변수를 넣은 다음 쿼리를 실행하면 쿼리 매개 변수에 해당하는 보고서 매개 변수가 자동으로 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-131">After you include query parameters and then run the query, report parameters that correspond to the query parameters are automatically created.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="bd2b8-132">처음 쿼리를 실행할 때 쿼리 매개 변수의 순서에 따라 보고서에서 매개 변수가 생성되는 순서가 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-132">The order of query parameters the first time you run a query determines the order that they are created in the report.</span></span> <span data-ttu-id="bd2b8-133">순서를 변경하려면 [보고서 매개 변수의 순서 변경&#40;보고서 작성기 및 SSRS&#41;](change-the-order-of-a-report-parameter-report-builder-and-ssrs.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-133">To change the order, see [Change the Order of a Report Parameter &#40;Report Builder and SSRS&#41;](change-the-order-of-a-report-parameter-report-builder-and-ssrs.md)</span></span>  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
 <span data-ttu-id="bd2b8-134">다음으로는 독립 매개 변수에 대한 값을 제공하는 데이터 세트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-134">Next, you will create a dataset that provides the values for the independent parameter.</span></span>  
  
### <a name="to-create-a-dataset-to-provide-values-for-an-independent-parameter"></a><span data-ttu-id="bd2b8-135">독립 매개 변수에 대한 값을 제공하는 데이터 세트를 만들려면</span><span class="sxs-lookup"><span data-stu-id="bd2b8-135">To create a dataset to provide values for an independent parameter</span></span>  
  
1.  <span data-ttu-id="bd2b8-136">보고서 데이터 창에서 데이터 원본을 마우스 오른쪽 단추로 클릭한 다음, **데이터 세트 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-136">In the Report Data pane, right-click a data source, and then click **Add Dataset**.</span></span>  
  
2.  <span data-ttu-id="bd2b8-137">**이름**에 데이터 세트의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-137">In **Name**, type the name of the dataset.</span></span>  
  
3.  <span data-ttu-id="bd2b8-138">**데이터 원본**에서 이름이 1단계에서 선택한 데이터 원본의 이름인지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-138">In **Data source**, verify the name is the name of the data source you chose in step 1.</span></span>  
  
4.  <span data-ttu-id="bd2b8-139">**쿼리 유형**에서 선택된 데이터 원본에 대한 쿼리 유형을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-139">In **Query type**, choose the type of query for the selected data source.</span></span> <span data-ttu-id="bd2b8-140">이 항목에서는 **텍스트** 쿼리 유형을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-140">In this topic, query type **Text** is assumed.</span></span>  
  
5.  <span data-ttu-id="bd2b8-141">**쿼리**에서 이 매개 변수에 대한 값을 검색하는 데 사용할 쿼리를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-141">In **Query**, type the query to use to retrieve values for this parameter.</span></span> <span data-ttu-id="bd2b8-142">독립 매개 변수에 대한 쿼리에는 일반적으로 쿼리 매개 변수가 포함되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-142">Queries for independent parameters typically do not contain query parameters.</span></span> <span data-ttu-id="bd2b8-143">예를 들어 모든 범주 값을 제공하는 매개 변수에 대한 쿼리를 만들려면 다음과 비슷한 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-143">For example, to create a query for a parameter that provides all category values, you might use a [!INCLUDE[tsql](../../includes/tsql-md.md)] statement similar to the following:</span></span>  
  
    ```  
    SELECT DISTINCT <column name> FROM <table>  
    ```  
  
     <span data-ttu-id="bd2b8-144">SELECT DISTINCT 명령은 지정된 테이블의 지정된 열에서 각각의 고유값을 가져올 수 있도록 결과 집합에서 중복 값을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-144">The SELECT DISTINCT command removes duplicate values from the result set so that you get each unique value from the specified column in the specified table.</span></span>  
  
     <span data-ttu-id="bd2b8-145">**실행** (**!**)을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-145">Click **Run** (**!**).</span></span> <span data-ttu-id="bd2b8-146">결과 집합은 이 첫 번째 매개 변수에 사용 가능한 값을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-146">The result set shows the values that are available for this first parameter.</span></span>  
  
6.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
 <span data-ttu-id="bd2b8-147">다음으로는 이 데이터 세트를 사용하여 런타임에 사용 가능한 값을 채우는 첫 번째 매개 변수의 속성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-147">Next, you will set the properties of the first parameter to use this dataset to populate its available values at run-time.</span></span>  
  
### <a name="to-set-available-values-for-a-report-parameter"></a><span data-ttu-id="bd2b8-148">보고서 매개 변수에 사용 가능한 값을 설정하려면</span><span class="sxs-lookup"><span data-stu-id="bd2b8-148">To set available values for a report parameter</span></span>  
  
1.  <span data-ttu-id="bd2b8-149">보고서 데이터 창의 매개 변수 폴더에서 첫 번째 매개 변수를 마우스 오른쪽 단추로 클릭한 다음 **매개 변수 속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-149">In the Report Data pane, in the Parameters folder, right-click the first parameter, and then click **Parameter Properties**.</span></span>  
  
2.  <span data-ttu-id="bd2b8-150">**이름**에서 매개 변수 이름이 올바른지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-150">In **Name**, verify that the name of the parameter is correct.</span></span>  
  
3.  <span data-ttu-id="bd2b8-151">**사용 가능한 값**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-151">Click **Available Values**.</span></span>  
  
4.  <span data-ttu-id="bd2b8-152">**쿼리에서 값 가져오기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-152">Click **Get values from a query**.</span></span> <span data-ttu-id="bd2b8-153">세 개의 필드가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-153">Three fields appear.</span></span>  
  
5.  <span data-ttu-id="bd2b8-154">**데이터 세트**의 드롭다운 목록에서, 이전 절차에서 만든 데이터 세트의 이름을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-154">In **Dataset**, from the drop-down list, click the name of the dataset you created in the previous procedure.</span></span>  
  
6.  <span data-ttu-id="bd2b8-155">**값** 필드에서 매개 변수 값을 제공하는 필드의 이름을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-155">In **Value** field, click the name of the field that provides the parameter value.</span></span>  
  
7.  <span data-ttu-id="bd2b8-156">**레이블** 필드에서 매개 변수 레이블을 제공하는 필드의 이름을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-156">In **Label** field, click the name of the field that provides the parameter label.</span></span>  
  
8.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
 <span data-ttu-id="bd2b8-157">다음으로, 종속 매개 변수의 값을 제공하는 데이터 세트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-157">Next, you will create a dataset that provides the values for a dependent parameter.</span></span>  
  
### <a name="to-create-a-dataset-to-provide-values-for-a-dependent-parameter"></a><span data-ttu-id="bd2b8-158">종속 매개 변수의 값을 제공하는 데이터 세트를 만들려면</span><span class="sxs-lookup"><span data-stu-id="bd2b8-158">To create a dataset to provide values for a dependent parameter</span></span>  
  
1.  <span data-ttu-id="bd2b8-159">보고서 데이터 창에서 데이터 원본을 마우스 오른쪽 단추로 클릭한 다음, **데이터 세트 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-159">In the Report Data pane, right-click a data source, and then click **Add Dataset**.</span></span>  
  
2.  <span data-ttu-id="bd2b8-160">**이름**에 데이터 세트의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-160">In **Name**, type the name of the dataset.</span></span>  
  
3.  <span data-ttu-id="bd2b8-161">**데이터 원본**에서 이름이 1단계에서 선택한 데이터 원본의 이름인지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-161">In **Data source**, verify the name is the name of the data source you chose in step 1.</span></span>  
  
4.  <span data-ttu-id="bd2b8-162">**쿼리 유형**에서 선택된 데이터 원본에 대한 쿼리 유형을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-162">In **Query type**, choose the type of query for the selected data source.</span></span> <span data-ttu-id="bd2b8-163">이 항목에서는 **텍스트** 쿼리 유형을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-163">In this topic, query type **Text** is assumed.</span></span>  
  
5.  <span data-ttu-id="bd2b8-164">**쿼리**에서 이 매개 변수에 대한 값을 검색하는 데 사용할 쿼리를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-164">In **Query**, type the query to use to retrieve values for this parameter.</span></span> <span data-ttu-id="bd2b8-165">종속 매개 변수에 대한 쿼리에는 일반적으로 이 매개 변수가 종속된 각 매개 변수에 대한 쿼리 매개 변수가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-165">Queries for dependent parameters typically include query parameters for each parameter that this parameter is dependent on.</span></span> <span data-ttu-id="bd2b8-166">예를 들어 범주(독립 매개 변수)에 대해 모든 하위 범주(종속 매개 변수) 값을 제공하는 매개 변수에 대한 쿼리를 만들려면 다음과 비슷한 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-166">For example, to create a query for a parameter that provides all subcategory (dependent parameter) values for a category (independent parameter), you might use a [!INCLUDE[tsql](../../includes/tsql-md.md)] statement similar to the following:</span></span>  
  
    ```  
    SELECT DISTINCT Subcategory FROM <table>   
    WHERE (Category = @Category)  
    ```  
  
     <span data-ttu-id="bd2b8-167">WHERE 절에서 Category는의 필드 이름이 \<table> 고 @Category 는 쿼리 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-167">In the WHERE clause, Category is the name of a field from \<table> and @Category is a query parameter.</span></span> <span data-ttu-id="bd2b8-168">이 문은 @Category에 지정된 범주에 대한 하위 범주의 목록을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-168">This statement produces a list of subcategories for the category specified in @Category.</span></span> <span data-ttu-id="bd2b8-169">런타임에 이 값은 사용자가 동일한 이름의 보고서 매개 변수에 대해 선택한 값으로 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-169">At run time, this value will be filled in with the value that the user chooses for the report parameter that has the same name.</span></span>  
  
6.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
 <span data-ttu-id="bd2b8-170">그런 다음, 이 데이터 세트를 사용하여 런타임에 사용 가능한 값을 채우는 두 번째 매개 변수의 속성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-170">Next, you will set the properties of the second parameter to use this dataset to populate its available values at run time.</span></span>  
  
### <a name="to-set-available-values-for-a-report-parameter"></a><span data-ttu-id="bd2b8-171">보고서 매개 변수에 사용 가능한 값을 설정하려면</span><span class="sxs-lookup"><span data-stu-id="bd2b8-171">To set available values for a report parameter</span></span>  
  
1.  <span data-ttu-id="bd2b8-172">보고서 데이터 창의 매개 변수 폴더에서 첫 번째 매개 변수를 마우스 오른쪽 단추로 클릭한 다음 **매개 변수 속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-172">In the Report Data pane, in the Parameters folder, right-click the first parameter, and then click **Parameter Properties**.</span></span>  
  
2.  <span data-ttu-id="bd2b8-173">**이름**에서 매개 변수 이름이 올바른지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-173">In **Name**, verify that the name of the parameter is correct.</span></span>  
  
3.  <span data-ttu-id="bd2b8-174">**사용 가능한 값**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-174">Click **Available Values**.</span></span>  
  
4.  <span data-ttu-id="bd2b8-175">**쿼리에서 값 가져오기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-175">Click **Get values from a query**.</span></span>  
  
5.  <span data-ttu-id="bd2b8-176">**데이터 세트**의 드롭다운 목록에서, 이전 절차에서 만든 데이터 세트의 이름을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-176">In **Dataset**, from the drop-down list, click the name of the dataset you created in the previous procedure.</span></span>  
  
6.  <span data-ttu-id="bd2b8-177">**값** 필드에서 매개 변수 값을 제공하는 필드의 이름을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-177">In **Value** field, click the name of the field that provides the parameter value.</span></span>  
  
7.  <span data-ttu-id="bd2b8-178">**레이블** 필드에서 매개 변수 레이블을 제공하는 필드의 이름을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-178">In **Label** field, click the name of the field that provides the parameter label.</span></span>  
  
8.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-test-the-cascading-parameters"></a><span data-ttu-id="bd2b8-179">연계 매개 변수를 테스트하려면</span><span class="sxs-lookup"><span data-stu-id="bd2b8-179">To test the cascading parameters</span></span>  
  
1.  <span data-ttu-id="bd2b8-180">**실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-180">Click **Run**.</span></span>  
  
2.  <span data-ttu-id="bd2b8-181">첫 번째 매개 변수인 독립 매개 변수의 드롭다운 목록에서 값을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-181">From the drop-down list for the first, independent parameter, choose a value.</span></span>  
  
     <span data-ttu-id="bd2b8-182">보고서 처리기가 다음 매개 변수에 대한 데이터 세트 쿼리를 실행하고 첫 번째 매개 변수에 선택한 값을 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-182">The report processor runs the dataset query for the next parameter and passes it the value you chose for the first parameter.</span></span> <span data-ttu-id="bd2b8-183">두 번째 매개 변수의 드롭다운 목록이 첫 번째 매개 변수 값에 따라 선택된 사용 가능한 값으로 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-183">The drop-down list for the second parameter is populated with the available values based on the first parameter value.</span></span>  
  
3.  <span data-ttu-id="bd2b8-184">두 번째 매개 변수인 종속 매개 변수의 드롭다운 목록에서 값을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-184">From the drop-down list for the second, dependent parameter, choose a value.</span></span>  
  
     <span data-ttu-id="bd2b8-185">마지막 매개 변수를 선택한 뒤에는 사용자가 선택 사항을 변경할 수 있도록 보고서가 자동으로 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-185">The report does not run automatically after you choose the last parameter so that you can change your choice.</span></span>  
  
4.  <span data-ttu-id="bd2b8-186">**보고서 보기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-186">Click **View Report**.</span></span> <span data-ttu-id="bd2b8-187">선택한 매개 변수에 따라 보고서가 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="bd2b8-187">The report updates the display based on the parameters you have chosen.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd2b8-188">참고 항목</span><span class="sxs-lookup"><span data-stu-id="bd2b8-188">See Also</span></span>  
 <span data-ttu-id="bd2b8-189">[보고서 매개 변수를 추가, 변경 또는 삭제 &#40;보고서 작성기 및 SSRS&#41;](add-change-or-delete-a-report-parameter-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="bd2b8-189">[Add, Change, or Delete a Report Parameter &#40;Report Builder and SSRS&#41;](add-change-or-delete-a-report-parameter-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="bd2b8-190">[보고서 매개 변수 &#40;보고서 작성기 및 보고서 디자이너&#41;](report-parameters-report-builder-and-report-designer.md) </span><span class="sxs-lookup"><span data-stu-id="bd2b8-190">[Report Parameters &#40;Report Builder and Report Designer&#41;](report-parameters-report-builder-and-report-designer.md) </span></span>  
 <span data-ttu-id="bd2b8-191">[자습서: 보고서에 매개 변수를 추가 &#40;보고서 작성기&#41;](../tutorial-add-a-parameter-to-your-report-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="bd2b8-191">[Tutorial: Add a Parameter to Your Report &#40;Report Builder&#41;](../tutorial-add-a-parameter-to-your-report-report-builder.md) </span></span>  
 <span data-ttu-id="bd2b8-192">[자습서 &#40;보고서 작성기&#41;](../report-builder-tutorials.md) </span><span class="sxs-lookup"><span data-stu-id="bd2b8-192">[Tutorials &#40;Report Builder&#41;](../report-builder-tutorials.md) </span></span>  
 <span data-ttu-id="bd2b8-193">[데이터 집합 필터, 데이터 영역 필터 및 그룹 필터를 추가 하 여 보고서 작성기 및 SSRS &#40;&#41;](add-dataset-filters-data-region-filters-and-group-filters.md) </span><span class="sxs-lookup"><span data-stu-id="bd2b8-193">[Add Dataset Filters, Data Region Filters, and Group Filters &#40;Report Builder and SSRS&#41;](add-dataset-filters-data-region-filters-and-group-filters.md) </span></span>  
 [<span data-ttu-id="bd2b8-194">보고서 포함된 데이터 세트 및 공유 데이터 세트&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="bd2b8-194">Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;</span></span>](../report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)  
  
  
