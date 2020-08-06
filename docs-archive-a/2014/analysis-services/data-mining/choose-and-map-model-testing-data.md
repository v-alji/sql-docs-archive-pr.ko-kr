---
title: 모델 테스트 데이터 선택 및 매핑 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- columns [data mining], mining accuracy charts
- Mining Accuracy Chart [Analysis Services], column mappings
- input column mapping [Analysis Services]
- mapping input columns [Analysis Services]
ms.assetid: be0d9f20-40c3-4dac-81da-281cfe724126
author: minewiskan
ms.author: owend
ms.openlocfilehash: 84f1d01c40070069d610bb028ab003223c5afbcd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649842"
---
# <a name="choose-and-map-model-testing-data"></a><span data-ttu-id="8e7cf-102">모델 테스트 데이터 선택 및 매핑</span><span class="sxs-lookup"><span data-stu-id="8e7cf-102">Choose and Map Model Testing Data</span></span>
  <span data-ttu-id="8e7cf-103">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]에서 정확도 차트를 만들려면 모델을 테스트하는 데 사용할 데이터를 선택하고 데이터를 모델에 매핑해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8e7cf-103">To create an accuracy chart in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], you must choose the data that will be used to test the model, and map the data to the model.</span></span>  
  
 <span data-ttu-id="8e7cf-104">마이닝 구조를 작성할 때 홀드아웃 데이터 집합을 만든 경우 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 에서는 기본적으로 마이닝 모델 테스트 데이터가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="8e7cf-104">By default, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] will use the mining model testing data, provided that you created a holdout data set when you built the mining structure.</span></span> <span data-ttu-id="8e7cf-105">홀드아웃 테스트 집합은 열 이름 및 데이터 형식이 항상 모델과 일치하고 데이터 분포도 유사하므로 홀드아웃 테스트 집합을 만드는 것은 동일한 마이닝 구조를 기반으로 하는 모델을 테스트하는 가장 쉬운 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="8e7cf-105">Creating a holdout test set is the easiest way to test models that are based on the same mining structure, because the column names and data types will always match the model, and you can be reasonably assured that the distribution of the data is similar.</span></span> <span data-ttu-id="8e7cf-106">또한 디자이너에서는 입력 열과 모델 열 간의 관계를 자동으로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8e7cf-106">Also, the designer will automatically create the relationships between the input and model columns.</span></span>  
  
 <span data-ttu-id="8e7cf-107">사용자가 외부 데이터 원본을 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8e7cf-107">Alternatively, you can specify an external source of data.</span></span> <span data-ttu-id="8e7cf-108">외부 데이터의 경우 다음과 같은 몇 가지 추가 요구 사항이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8e7cf-108">For external data, there are some additional requirements:</span></span>  
  
-   <span data-ttu-id="8e7cf-109">외부 데이터 집합은 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]인스턴스에서 데이터 원본 뷰로 정의되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8e7cf-109">The external data set must be defined as a data source view in an instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="8e7cf-110">외부 데이터 집합에는 마이닝 모델의 예측 가능한 열에 매핑할 수 있는 열이 하나 이상 포함되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8e7cf-110">The external data set must at least contain one column that can be mapped to the predictable column in the mining model.</span></span> <span data-ttu-id="8e7cf-111">일부 열은 무시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8e7cf-111">You can choose to ignore some columns.</span></span>  
  
-   <span data-ttu-id="8e7cf-112">새 열을 추가하거나 다른 데이터 원본 뷰의 열을 매핑할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8e7cf-112">You cannot add new columns or map columns in a different data source view.</span></span> <span data-ttu-id="8e7cf-113">선택하는 데이터 원본 뷰에는 예측 쿼리에 필요한 모든 열이 포함되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8e7cf-113">The data source view that you select must contain all the columns that you need for the prediction query.</span></span>  
  
-   <span data-ttu-id="8e7cf-114">외부 열 이름이 모델의 열 이름과 정확하게 일치하는 경우 디자이너에서는 외부 열 이름을 자동으로 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="8e7cf-114">If the external column names exactly match those in the model, the designer will map them for you.</span></span> <span data-ttu-id="8e7cf-115">매핑이 잘못된 경우 매핑을 변경 또는 삭제하거나 기존 열에 대한 새 매핑을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8e7cf-115">If the mappings are wrong, you can change them, or delete and create new mappings for existing columns.</span></span>  
  
-   <span data-ttu-id="8e7cf-116">외부 데이터 원본을 사용하는 경우 필터를 적용하여 테스트 데이터를 관련된 사례 하위 집합으로 제한할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8e7cf-116">If you use an external data source, you can apply filters to restrict the testing data to a relevant subset of cases.</span></span>  
  
-   <span data-ttu-id="8e7cf-117">홀드아웃 테스트 집합을 사용하더라도 필터로 인해 마이닝 구조에 연결된 테스트 데이터와 마이닝 모델 테스트 사례 간에 차이가 있을 수 있다는 것을 알고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8e7cf-117">Even when you use the holdout test set, you should be aware that filters can cause differences between the testing data associated with a mining structure and the mining model test cases.</span></span>  
  
 <span data-ttu-id="8e7cf-118">이 항목에서는 테스트 데이터를 선택하고 매핑하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="8e7cf-118">This topic describes how to choose and map the testing data:</span></span>  
  
 [<span data-ttu-id="8e7cf-119">마이닝 모델의 정확도 테스트에 사용할 입력 테이블 선택</span><span class="sxs-lookup"><span data-stu-id="8e7cf-119">Select input tables to test the accuracy of a mining model</span></span>](#bkmk_SelectInputs)  
  
 [<span data-ttu-id="8e7cf-120">모델 열을 테스트 데이터의 열에 매핑</span><span class="sxs-lookup"><span data-stu-id="8e7cf-120">Map model columns to the columns in the testing data</span></span>](#bkmk_MapColumns)  
  
 [<span data-ttu-id="8e7cf-121">테스트 데이터의 열이 모델에 매핑되는 방식 변경</span><span class="sxs-lookup"><span data-stu-id="8e7cf-121">Change the way that columns in the testing data are mapped to the model</span></span>](#bkmk_ChangeMappings)  
  
##  <a name="to-select-input-tables-to-test-the-accuracy-of-a-mining-model"></a><a name="bkmk_SelectInputs"></a> <span data-ttu-id="8e7cf-122">마이닝 모델의 정확도 테스트에 사용할 입력 테이블을 선택하려면</span><span class="sxs-lookup"><span data-stu-id="8e7cf-122">To select input tables to test the accuracy of a mining model</span></span>  
  
1.  <span data-ttu-id="8e7cf-123">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]의 데이터 마이닝 디자이너에서 차트로 나타낼 모델을 포함하는 마이닝 구조를 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8e7cf-123">In Data Mining Designer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], double-click the mining structure that contains the models you want to chart.</span></span>  
  
2.  <span data-ttu-id="8e7cf-124">**마이닝 정확도 차트** 탭을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8e7cf-124">Select the **Mining Accuracy Chart** tab.</span></span>  
  
3.  <span data-ttu-id="8e7cf-125">**마이닝 정확도 차트** 뷰의 **입력 선택** 탭에서 다음 옵션 중 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8e7cf-125">On the **Input Selection Tab** of the **Mining Accuracy Chart** view, select one of the following options:</span></span>  
  
     <span data-ttu-id="8e7cf-126">**마이닝 모델 테스트 사례 사용**</span><span class="sxs-lookup"><span data-stu-id="8e7cf-126">**Use mining model test cases**</span></span>  
  
     <span data-ttu-id="8e7cf-127">**마이닝 구조 테스트 사례 사용**</span><span class="sxs-lookup"><span data-stu-id="8e7cf-127">**Use mining structure test cases**</span></span>  
  
     <span data-ttu-id="8e7cf-128">**다른 데이터 집합 지정**</span><span class="sxs-lookup"><span data-stu-id="8e7cf-128">**Specify a different data set**</span></span>  
  
4.  <span data-ttu-id="8e7cf-129">**다른 데이터 집합 지정**을 선택한 경우 **필터 편집기 열기** 를 클릭하여 입력 데이터 집합에 대한 필터 조건을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8e7cf-129">If you selected **Specify a different data set**, optionally click **Open Filter Editor** to create filter conditions on the input data set.</span></span> [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
5.  <span data-ttu-id="8e7cf-130">지정한 테스트 데이터를 사용하여 차트를 자동으로 작성하려면 **리프트 차트** 탭 또는 **분류표** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8e7cf-130">Click the **Lift Chart** tab or the **Classification Matrix** tab to automatically build the chart by using the testing data you specified.</span></span>  
  
##  <a name="to-map-model-columns-to-the-columns-in-the-testing-data"></a><a name="bkmk_MapColumns"></a> <span data-ttu-id="8e7cf-131">모델 열을 테스트 데이터의 열에 매핑하려면</span><span class="sxs-lookup"><span data-stu-id="8e7cf-131">To map model columns to the columns in the testing data</span></span>  
  
1.  <span data-ttu-id="8e7cf-132">데이터 마이닝 디자이너에서 차트로 나타낼 모델을 포함하는 마이닝 구조를 두 번 클릭하여 해당 구조 및 모델을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="8e7cf-132">Double-click the mining structure that contains the models you want to chart, to open the structure and models in Data Mining Designer.</span></span>  
  
2.  <span data-ttu-id="8e7cf-133">**마이닝 정확도 차트** 탭을 선택한 다음 **입력 선택** 탭을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8e7cf-133">Select the **Mining Accuracy Chart** tab, and then select the **Input Selection** tab.</span></span>  
  
3.  <span data-ttu-id="8e7cf-134">**입력 선택** 탭의 **정확도 차트에 사용할 데이터 집합을 선택하십시오.** 에서 **다른 데이터 집합 지정**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8e7cf-134">In the **Input Selection** tab, under **Select data set to be used for Accuracy Chart**, select **Specify a different data set**.</span></span>  
  
4.  <span data-ttu-id="8e7cf-135">찾아보기 단추 **(...)** 를 클릭 하 여 대화 상자를 열고 외부 데이터 집합의 정의를 작성 합니다.</span><span class="sxs-lookup"><span data-stu-id="8e7cf-135">Click the browse button **(...)** to open a dialog box and build the definition of the external data set.</span></span>  
  
5.  <span data-ttu-id="8e7cf-136">**마이닝 구조 선택** 대화 상자에서 작업할 모델이 포함된 마이닝 구조를 선택한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8e7cf-136">In the **Select Mining Structure** dialog box, select the mining structure that contains the models you want to work with, and then click **OK**.</span></span>  
  
6.  <span data-ttu-id="8e7cf-137">**마이닝 정확도 차트** 탭의 **입력 테이블 선택** 테이블에서 **사례 테이블 선택** 을 클릭하여 **테이블 선택** 대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="8e7cf-137">On the **Select Input Table(s)** table of the **Mining Accuracy Chart** tab, click **Select Case Table** to open the **Select Table** dialog box.</span></span>  
  
7.  <span data-ttu-id="8e7cf-138">**테이블 선택** 대화 상자의 **데이터 원본** 목록에서 데이터 원본을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8e7cf-138">In the **Select Table** dialog box, select a data source from the **Data Source** list.</span></span> <span data-ttu-id="8e7cf-139">모델 정확도를 확인하기 위해 예측 쿼리에 사용할 데이터가 포함된 테이블을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8e7cf-139">Choose a table that contains the data that you want to use in the prediction queries to determine the accuracy of the models.</span></span>  
  
8.  <span data-ttu-id="8e7cf-140">**테이블/뷰 이름** 상자에서 모델 테스트에 사용할 데이터가 포함된 테이블을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8e7cf-140">In the **Table/View Name** box, select the table that contains the data that you want to use to test the models.</span></span>  
  
9. <span data-ttu-id="8e7cf-141">필요한 경우 매핑을 편집합니다.</span><span class="sxs-lookup"><span data-stu-id="8e7cf-141">Edit the mappings, if necessary.</span></span> <span data-ttu-id="8e7cf-142">마이닝 구조의 열이 입력 테이블에 있는 동일한 이름의 열에 자동으로 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="8e7cf-142">Columns in the mining structure are automatically mapped to the columns with the same name in the input table.</span></span> <span data-ttu-id="8e7cf-143">매핑을 수동으로 만들려면 **입력 테이블 선택** 테이블의 열을 클릭한 다음 **마이닝 구조** 테이블의 해당 열로 끌어 옵니다.</span><span class="sxs-lookup"><span data-stu-id="8e7cf-143">To manually create mappings, click a column in the **Select Input Table(s)** table and drag it onto the corresponding column in the **Mining Structure** table.</span></span> <span data-ttu-id="8e7cf-144">매핑을 삭제하려면 **마이닝 구조** 테이블의 열을 **입력 테이블 선택** 테이블의 매핑된 열에 연결하는 선을 클릭한 다음 Delete 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="8e7cf-144">To delete a mapping, click the line that links the column in the **Mining Structure** table to the mapped column in the **Select Input Table(s)** table, and then press DELETE.</span></span>  
  
10. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
##  <a name="to-modify-the-way-input-data-is-mapped-to-the-model"></a><a name="bkmk_ChangeMappings"></a><span data-ttu-id="8e7cf-145">입력 데이터가 모델에 매핑되는 방식을 수정 하려면</span><span class="sxs-lookup"><span data-stu-id="8e7cf-145">To modify the way input data is mapped to the model</span></span>  
  
1.  <span data-ttu-id="8e7cf-146">데이터 마이닝 디자이너에서 차트로 나타낼 모델을 포함하는 구조를 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8e7cf-146">In Data Mining Designer, double-click the structure that contains the models you want to chart.</span></span>  
  
2.  <span data-ttu-id="8e7cf-147">**마이닝 정확도 차트** 탭을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8e7cf-147">Select the **Mining Accuracy Chart** tab.</span></span>  
  
3.  <span data-ttu-id="8e7cf-148">**입력 선택** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8e7cf-148">Click the **Input Selection** tab.</span></span>  
  
4.  <span data-ttu-id="8e7cf-149">**정확도 차트에 사용할 데이터 집합을 선택**하십시오 .에서 **다른 데이터 집합 지정**옵션을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="8e7cf-149">In **Select data set to be used for Accuracy Chart**, select the option **Specify a different data set**.</span></span>  
  
5.  <span data-ttu-id="8e7cf-150">찾아보기 단추 **(...)** 를 클릭 하 여 대화 상자를 열고 외부 데이터 원본의 정의를 작성 합니다.</span><span class="sxs-lookup"><span data-stu-id="8e7cf-150">Click the browse button **(...)** to open a dialog box and build the definition of the external data source.</span></span>  
  
6.  <span data-ttu-id="8e7cf-151">**열 매핑 지정** 대화 상자에서 **사례 테이블 선택**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8e7cf-151">In the **Specify Column Mapping** dialog box, click **Select Case Table**.</span></span>  
  
7.  <span data-ttu-id="8e7cf-152">테이블 선택 대화 상자의 목록에서 데이터 원본 뷰를 선택하고 사례 데이터를 포함하는 테이블을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8e7cf-152">In the Select Table dialog box, Select a data source view from the list, and select the table that contains the case data.</span></span> [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
8.  <span data-ttu-id="8e7cf-153">필요한 테이블을 사용할 수 없으면 대화 상자를 닫고 해당 테이블을 포함하는 새 데이터 원본 뷰를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8e7cf-153">If the tables you need are not available, close the dialog box and create a new data source view that contains the table.</span></span> <span data-ttu-id="8e7cf-154">데이터 원본 뷰를 만드는 방법은 [데이터 원본 뷰 정의&#40;Analysis Services&#41;](../multidimensional-models/defining-a-data-source-view-analysis-services.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8e7cf-154">For information about how to create a data source view, see [Defining a Data Source View &#40;Analysis Services&#41;](../multidimensional-models/defining-a-data-source-view-analysis-services.md).</span></span>  
  
9. <span data-ttu-id="8e7cf-155">마이닝 모델에 중첩 테이블이 포함되어 있으면 **중첩 테이블 선택**을 클릭하고 데이터 원본 뷰의 테이블 목록에서 중첩 테이블을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8e7cf-155">If the mining model contains a nested table, click **Select Nested Table**, and select the nested table from the list of tables in the data source view.</span></span> [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
10. <span data-ttu-id="8e7cf-156">수정할 매핑의 조인 선을 선택하고 **연결 수정**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8e7cf-156">Select the join line of the mapping you want to modify, and select **Modify Connections**.</span></span>  
  
     <span data-ttu-id="8e7cf-157">**매핑 수정** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="8e7cf-157">The **Modify Mapping** dialog box opens.</span></span> <span data-ttu-id="8e7cf-158">이 대화 상자의 테이블에서 **마이닝 구조 열** 에는 선택한 마이닝 구조에 포함된 각 열이 나열되고 **테이블 열** 에는 마이닝 구조의 열에 매핑되는 입력 테이블의 열이 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="8e7cf-158">In the table in this dialog box, **Mining Structure Column** lists each column that the selected mining structure contains, and **Table Column** lists the columns from input tables that are mapped to columns in the mining structure.</span></span>  
  
11. <span data-ttu-id="8e7cf-159">**테이블 열**아래에서 관계를 수정할 **마이닝 구조 열** 아래의 행에 해당하는 행을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8e7cf-159">Under **Table Column**, select the row that corresponds to the row under **Mining Structure Column** for which you want to modify a relationship.</span></span> <span data-ttu-id="8e7cf-160">목록에서 새 열을 선택하거나 목록에서 빈 항목을 선택하여 열을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="8e7cf-160">Select a new column from the list, or select the blank entry from the list to delete the column.</span></span>  
  
12. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
     <span data-ttu-id="8e7cf-161">**열 매핑 지정** 대화 상자에 새 열 매핑이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="8e7cf-161">The new column mappings are displayed in the **Specify Column Mapping** dialog box.</span></span> <span data-ttu-id="8e7cf-162">열 사이의 선을 선택하고 Delete 키를 눌러 매핑을 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8e7cf-162">You can remove a mapping by selecting the line between the columns and pressing the DELETE key.</span></span> <span data-ttu-id="8e7cf-163">**마이닝 구조** 테이블의 열을 선택하고 **입력 테이블 선택** 테이블의 해당 열로 끌어 새 연결을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8e7cf-163">You can create a new connection by selecting a column in the **Mining Structure** table and dragging it to the corresponding column in the **SelectInput Table(s)** table.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e7cf-164">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8e7cf-164">See Also</span></span>  
 [<span data-ttu-id="8e7cf-165">테스트 및 유효성 검사 태스크 및 방법&#40;데이터 마이닝&#41;</span><span class="sxs-lookup"><span data-stu-id="8e7cf-165">Testing and Validation Tasks and How-tos &#40;Data Mining&#41;</span></span>](testing-and-validation-tasks-and-how-tos-data-mining.md)  
  
  
