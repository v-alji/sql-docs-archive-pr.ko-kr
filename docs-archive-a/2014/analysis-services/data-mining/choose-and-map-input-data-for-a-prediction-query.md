---
title: 예측 쿼리에 대 한 입력 데이터 선택 및 매핑 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- tables [Analysis Services], prediction queries
- Mining Model Prediction [Analysis Services], input tables
ms.assetid: 00d330a0-879d-4da0-9f29-53c288116f4d
author: minewiskan
ms.author: owend
ms.openlocfilehash: 54e11752d6278e01e50a379bf7bb57521ff9bb29
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649846"
---
# <a name="choose-and-map-input-data-for-a-prediction-query"></a><span data-ttu-id="295ec-102">예측 쿼리에 대한 입력 데이터 선택 및 매핑</span><span class="sxs-lookup"><span data-stu-id="295ec-102">Choose and Map Input Data for a Prediction Query</span></span>
  <span data-ttu-id="295ec-103">마이닝 모델에서 예측을 만드는 경우 일반적으로 모델에 새 데이터를 제공하여 예측을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="295ec-103">When you create predictions from a mining model, you generally do this by feeding new data into the model.</span></span> <span data-ttu-id="295ec-104">기록 데이터만 기반으로 하여 예측을 만들 수 있는 시계열 모델은 예외입니다. 모델에 새 데이터를 제공하려면 해당 데이터를 데이터 원본 뷰의 일부로 사용할 수 있는지 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="295ec-104">(The exception is time series models, which can make predictions based on historical data only.) To provide the model with new data, you must make sure that the data is available as part of a data source view.</span></span> <span data-ttu-id="295ec-105">예측에 사용할 데이터를 미리 알아보려는 경우 모델을 만드는 데 사용한 데이터 원본 뷰에 해당 데이터를 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="295ec-105">If you know in advance which data you will use for prediction, you can include it in the data source view that you used to create the model.</span></span> <span data-ttu-id="295ec-106">그렇지 않으면 새 데이터 원본 뷰를 만들어야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="295ec-106">Otherwise, you might have to create a new data source view.</span></span> <span data-ttu-id="295ec-107">자세한 내용은 [다차원 모델의 데이터 원본 뷰](../multidimensional-models/data-source-views-in-multidimensional-models.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="295ec-107">For more information, see [Data Source Views in Multidimensional Models](../multidimensional-models/data-source-views-in-multidimensional-models.md).</span></span>  
  
 <span data-ttu-id="295ec-108">필요한 데이터가 일 대 다 조인에서 두 개 이상의 테이블에 포함되는 경우도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="295ec-108">Sometimes the data that you need might be contained within more than one table in a one-to-many join.</span></span> <span data-ttu-id="295ec-109">제품 또는 트랜잭션 세부 정보가 포함된 중첩 테이블에 연결된 사례 테이블을 사용하는 연결 모델 또는 시퀀스 클러스터링 모델에 사용되는 데이터의 경우에 해당됩니다.</span><span class="sxs-lookup"><span data-stu-id="295ec-109">This is the case with data used for association models or sequence clustering models, which use a case table linked to a nested table that contains product or transaction details.</span></span> <span data-ttu-id="295ec-110">모델에서 사례 중첩 테이블 구조를 사용하는 경우에는 예측에 사용하는 데이터에도 사례 중첩 테이블 구조가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="295ec-110">If your model uses a case-nested table structure, the data that you use for prediction must also have a case-nested table structure.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="295ec-111">새 열을 추가하거나 다른 데이터 원본 뷰의 열을 매핑할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="295ec-111">You cannot add new columns or map columns that are in a different data source view.</span></span> <span data-ttu-id="295ec-112">선택하는 데이터 원본 뷰에는 예측 쿼리에 필요한 모든 열이 포함되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="295ec-112">The data source view that you select must contain all the columns that you need for the prediction query.</span></span>  
  
 <span data-ttu-id="295ec-113">예측에 사용할 데이터가 포함된 테이블을 식별한 후에는 외부 데이터의 열을 마이닝 모델의 열에 매핑해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="295ec-113">After you have identified the tables that contain the data you will use for predictions, you must map the columns in the external data to the columns in the mining model.</span></span> <span data-ttu-id="295ec-114">예를 들어 모델에서 통계 및 설문 조사 응답을 기반으로 고객의 구매 행동을 예측하는 경우 일반적으로 모델에 있는 정보에 해당하는 정보가 입력 데이터에 포함되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="295ec-114">For example, if your model predicts customer purchasing behavior based on demographics and survey responses, your input data should contains information that generally corresponds to what is in the model.</span></span> <span data-ttu-id="295ec-115">각각의 모든 열에 대해 일치하는 데이터가 있을 필요는 없지만 일치시킬 수 있는 열이 많을수록 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="295ec-115">You do not need to have matching data for every single column, but the more columns you can match, the better.</span></span> <span data-ttu-id="295ec-116">여러 다른 데이터 형식이 있는 열을 매핑하려고 시도하면 오류가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="295ec-116">If you try to map columns that have different data types, you might get an error.</span></span> <span data-ttu-id="295ec-117">이러한 경우에는 데이터 원본 뷰에 명명된 계산을 정의하여 새 열 데이터를 모델에 필요한 데이터 형식으로 캐스팅하거나 변환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="295ec-117">In that case, you could define a named calculation in the data source view to cast or convert the new column data to the data type required by the model.</span></span> <span data-ttu-id="295ec-118">자세한 내용은 [데이터 원본 뷰에서 명명 된 계산 정의 &#40;Analysis Services&#41;](../multidimensional-models/define-named-calculations-in-a-data-source-view-analysis-services.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="295ec-118">For more information, see [Define Named Calculations in a Data Source View &#40;Analysis Services&#41;](../multidimensional-models/define-named-calculations-in-a-data-source-view-analysis-services.md).</span></span>  
  
 <span data-ttu-id="295ec-119">예측에 사용할 데이터를 선택하면 이름의 유사성과 일치하는 데이터 형식을 기반으로 선택한 데이터 원본의 일부 열이 마이닝 모델 열에 자동으로 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="295ec-119">When you choose the data to use for prediction, some columns in the selected data source might be automatically mapped to the mining model columns, based on name similarity and matching data type.</span></span> <span data-ttu-id="295ec-120">**마이닝 모델 예측** 에서 **매핑 수정** 대화 상자를 사용하여 매핑된 열을 변경하거나 부적절한 매핑을 삭제하거나 기존 열에 대한 새 매핑을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="295ec-120">You can use the **Modify Mapping** dialog box in the **Mining Model Prediction** to change the columns that are mapped, delete inappropriate mappings, or create new mappings for existing columns.</span></span> <span data-ttu-id="295ec-121">**마이닝 모델 예측** 디자인 화면에서는 연결의 끌어서 놓기 편집도 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="295ec-121">The **Mining Model Prediction** design surface also supports drag-and-drop editing of connections.</span></span>  
  
-   <span data-ttu-id="295ec-122">새 연결을 만들려면 **마이닝 모델** 테이블의 열을 선택하고 **입력 테이블 선택** 테이블의 해당 열로 끌기만 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="295ec-122">To create a new connection, just select a column in the **Mining Model** table and drag it to the corresponding column in the **SelectInput Table(s)** table.</span></span>  
  
-   <span data-ttu-id="295ec-123">연결을 제거하려면 연결선을 선택하고 Delete 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="295ec-123">To remove a connection, select the connection line and press the DELETE key.</span></span>  
  
 <span data-ttu-id="295ec-124">다음 절차에서는 **중첩 조인 지정** 대화 상자를 사용하여 예측 쿼리의 입력으로 사용되는 사례 테이블과 중첩 테이블 간에 만들어진 조인을 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="295ec-124">The following procedure describes how you can modify the joins that have been created between the case table and a nested table used as inputs to a prediction query, using the **Specify Nested Join** dialog box.</span></span>  
  
### <a name="select-an-input-table"></a><span data-ttu-id="295ec-125">입력 테이블 선택</span><span class="sxs-lookup"><span data-stu-id="295ec-125">Select an input table</span></span>  
  
1.  <span data-ttu-id="295ec-126">**의 데이터 마이닝 디자이너에 있는** 마이닝 정확도 차트 **탭의** 입력 테이블 선택 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]테이블에서 **사례 테이블 선택**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="295ec-126">On the **Select Input Table(s)** table of the **Mining Accuracy Chart** tab in Data Mining Designer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], click **Select Case Table**.</span></span>  
  
     <span data-ttu-id="295ec-127">쿼리의 기반으로 사용할 데이터가 포함된 테이블을 선택할 수 있는 **테이블 선택** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="295ec-127">The **Select Table** dialog box opens, in which you can select the table that contains the data on which to base your queries.</span></span>  
  
2.  <span data-ttu-id="295ec-128">**테이블 선택** 대화 상자의 **데이터 원본** 목록에서 데이터 원본을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="295ec-128">In the **Select Table** dialog box, select a data source from the **Data Source** list.</span></span>  
  
3.  <span data-ttu-id="295ec-129">**테이블/뷰 이름**에서 모델 테스트에 사용할 데이터가 포함된 테이블을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="295ec-129">Under **Table/View Name**, select the table that contains the data you want to use to test the models.</span></span>  
  
4.  <span data-ttu-id="295ec-130">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="295ec-130">Click **OK**.</span></span>  
  
     <span data-ttu-id="295ec-131">마이닝 구조의 열이 입력 테이블에 있는 동일한 이름의 열에 자동으로 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="295ec-131">The columns in the mining structure are automatically mapped to the columns that have the same name in the input table.</span></span>  
  
### <a name="change-the-way-that-input-data-is-mapped-to-the-model"></a><span data-ttu-id="295ec-132">입력 데이터가 모델에 매핑되는 방식 변경</span><span class="sxs-lookup"><span data-stu-id="295ec-132">Change the way that input data is mapped to the model</span></span>  
  
1.  <span data-ttu-id="295ec-133">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]의 데이터 마이닝 디자이너에서 **마이닝 모델 예측** 탭을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="295ec-133">In Data Mining Designer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], select the **Mining Model Prediction** tab.</span></span>  
  
2.  <span data-ttu-id="295ec-134">**마이닝 모델** 메뉴에서 **연결 수정**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="295ec-134">On the **Mining Model** menu, select **Modify Connections**.</span></span>  
  
     <span data-ttu-id="295ec-135">**매핑 수정** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="295ec-135">The **Modify Mapping** dialog box opens.</span></span> <span data-ttu-id="295ec-136">이 대화 상자의 **마이닝 모델 열** 열에는 선택한 마이닝 구조의 열이 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="295ec-136">In this dialog box, the column **Mining Model Column** lists the columns in the selected mining structure.</span></span> <span data-ttu-id="295ec-137">**테이블 열** 열에는 **입력 테이블 선택** 대화 상자에서 선택한 외부 데이터 원본의 열이 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="295ec-137">The column **Table Column** lists the columns in the external data source that you chose in the **SelectInput Table(s)** dialog box.</span></span> <span data-ttu-id="295ec-138">외부 데이터 원본의 열은 마이닝 모델의 열에 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="295ec-138">The columns in the external data source are mapped to columns in the mining model.</span></span>  
  
3.  <span data-ttu-id="295ec-139">**테이블 열**에서 매핑할 마이닝 모델 열에 해당하는 행을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="295ec-139">Under **Table Column**, select the row that corresponds to the mining model column that you want to map to.</span></span>  
  
4.  <span data-ttu-id="295ec-140">외부 데이터 원본의 사용 가능한 열 목록에서 새 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="295ec-140">Select a new column from the list of available columns in the external data source.</span></span> <span data-ttu-id="295ec-141">목록에서 빈 항목을 선택하여 열 매핑을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="295ec-141">Select the blank item in the list to delete the column mapping.</span></span>  
  
5.  <span data-ttu-id="295ec-142">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="295ec-142">Click **OK**.</span></span>  
  
     <span data-ttu-id="295ec-143">디자이너에 새 열 매핑이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="295ec-143">The new column mappings are displayed in the designer.</span></span>  
  
### <a name="remove-a-relationship-between-input-tables"></a><span data-ttu-id="295ec-144">입력 테이블 간의 관계 제거</span><span class="sxs-lookup"><span data-stu-id="295ec-144">Remove a relationship between input tables</span></span>  
  
1.  <span data-ttu-id="295ec-145">**의 데이터 마이닝 디자이너에 있는** 마이닝 모델 예측 **탭의** 입력 테이블 선택 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]테이블에서 **조인 수정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="295ec-145">On the **Select Input Table(s)** table of the **Mining Model Prediction** tab in Data Mining Designer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], click **Modify Join**.</span></span>  
  
     <span data-ttu-id="295ec-146">**중첩 조인 지정** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="295ec-146">The **Specify Nested Join** dialog box opens.</span></span>  
  
2.  <span data-ttu-id="295ec-147">관계를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="295ec-147">Select a relationship.</span></span>  
  
3.  <span data-ttu-id="295ec-148">**관계 제거**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="295ec-148">Click **Remove Relationship**.</span></span>  
  
4.  <span data-ttu-id="295ec-149">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="295ec-149">Click **OK**.</span></span>  
  
     <span data-ttu-id="295ec-150">사례 테이블과 중첩 테이블 간의 관계가 제거되었습니다.</span><span class="sxs-lookup"><span data-stu-id="295ec-150">The relationship between the case table and the nested table has been removed.</span></span>  
  
### <a name="create-a-new-relationship-between-input-tables"></a><span data-ttu-id="295ec-151">입력 테이블 간에 새 관계 만들기</span><span class="sxs-lookup"><span data-stu-id="295ec-151">Create a new relationship between input tables</span></span>  
  
1.  <span data-ttu-id="295ec-152">데이터 마이닝 디자이너에 있는 **마이닝 모델 예측** 탭의 **입력 테이블 선택** 테이블에서 **조인 수정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="295ec-152">On the **Select Input Table(s)** table of the **Mining Model Prediction** tab in Data Mining Designer, click **Modify Join**.</span></span>  
  
     <span data-ttu-id="295ec-153">**중첩 조인 지정** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="295ec-153">The **Specify Nested Join** dialog box opens.</span></span>  
  
2.  <span data-ttu-id="295ec-154">**관계 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="295ec-154">Click **Add Relationship**.</span></span>  
  
     <span data-ttu-id="295ec-155">**관계 만들기** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="295ec-155">The **Create Relationship** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="295ec-156">**원본 열**에서 중첩 테이블의 키를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="295ec-156">Select the key of the nested table in **Source Columns**.</span></span>  
  
4.  <span data-ttu-id="295ec-157">**대상 열**에서 사례 테이블의 키를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="295ec-157">Select the key of the case table in **Destination Columns**.</span></span>  
  
5.  <span data-ttu-id="295ec-158">**관계 만들기** 대화 상자에서 **확인** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="295ec-158">Click **OK** in the **Create Relationship** dialog box.</span></span>  
  
6.  <span data-ttu-id="295ec-159">**중첩 조인 지정** 대화 상자에서 **확인** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="295ec-159">Click **OK** in the **Specify Nested Join** dialog box.</span></span>  
  
     <span data-ttu-id="295ec-160">사례 테이블과 중첩 테이블 간에 새 관계가 생성되었습니다.</span><span class="sxs-lookup"><span data-stu-id="295ec-160">A new relationship has been created between the case table and the nested table.</span></span>  
  
### <a name="add-a-nested-table-to-the-input-tables-of-a-prediction-query"></a><span data-ttu-id="295ec-161">예측 쿼리의 입력 테이블에 중첩 테이블 추가</span><span class="sxs-lookup"><span data-stu-id="295ec-161">Add a nested table to the input tables of a prediction query</span></span>  
  
1.  <span data-ttu-id="295ec-162">데이터 마이닝 디자이너의 **마이닝 모델 예측** 탭에서 **사례 테이블 선택** 을 클릭하여 **테이블 선택** 대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="295ec-162">On the **Mining Model Prediction** tab in Data Mining Designer, click **Select Case Table** to open the **Select Table** dialog box.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="295ec-163">사례 테이블을 지정하기 전까지는 중첩 테이블을 입력에 추가할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="295ec-163">You cannot add a nested table to the inputs unless you have specified a case table.</span></span> <span data-ttu-id="295ec-164">중첩 테이블을 사용하려면 예측에 사용할 마이닝 모델에서도 중첩 테이블을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="295ec-164">Use of a nested table requires that the mining model you are using for prediction also uses a nested table.</span></span>  
  
2.  <span data-ttu-id="295ec-165">**테이블 선택** 대화 상자의 **데이터 원본** 목록에서 데이터 원본을 선택하고 데이터 원본 뷰에서 사례 데이터가 들어 있는 테이블을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="295ec-165">In the **Select Table** dialog box, select a data source from the **Data Source** list, and select the table in the data source view that contains the case data.</span></span> [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
3.  <span data-ttu-id="295ec-166">**중첩 테이블 선택** 을 클릭하여 **테이블 선택** 대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="295ec-166">Click **Select Nested Table** to open the **Select Table** dialog box.</span></span>  
  
4.  <span data-ttu-id="295ec-167">**테이블 선택** 대화 상자의 **데이터 원본** 목록에서 데이터 원본을 선택하고 데이터 원본 뷰에서 중첩된 데이터가 들어 있는 테이블을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="295ec-167">In the **Select Table** dialog box, select a data source from the **Data Source** list, and select the table in the data source view that contains the nested data.</span></span> [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
     <span data-ttu-id="295ec-168">관계가 이미 존재한다면 마이닝 모델의 열이 입력 테이블에 있는 동일한 이름의 열에 자동으로 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="295ec-168">If a relationship already exists, the columns in the mining model are automatically mapped to the columns that have the same name in the input table.</span></span> <span data-ttu-id="295ec-169">**조인 수정**을 클릭하면 열리는 **관계 만들기** 대화 상자를 사용하여 중첩 테이블과 사례 테이블 간의 관계를 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="295ec-169">You can modify the relationship between the nested table and the case table by clicking **Modify Join**, which opens the **Create Relationship** dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="295ec-170">참고 항목</span><span class="sxs-lookup"><span data-stu-id="295ec-170">See Also</span></span>  
 [<span data-ttu-id="295ec-171">예측 쿼리&#40;데이터 마이닝&#41;</span><span class="sxs-lookup"><span data-stu-id="295ec-171">Prediction Queries &#40;Data Mining&#41;</span></span>](prediction-queries-data-mining.md)  
  
  
