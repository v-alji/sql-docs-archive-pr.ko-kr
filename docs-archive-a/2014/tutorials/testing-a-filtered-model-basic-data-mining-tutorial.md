---
title: 필터링 된 모델 테스트 (기본 데이터 마이닝 자습서) | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: f0d74f8c-600d-4df5-a742-695e6947a071
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: a97b5ca3523d1fc73405baba52b179a9bef04767
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639138"
---
# <a name="testing-a-filtered-model-basic-data-mining-tutorial"></a><span data-ttu-id="b3f85-102">필터링된 모델 테스트(기본 데이터 마이닝 자습서)</span><span class="sxs-lookup"><span data-stu-id="b3f85-102">Testing a Filtered Model (Basic Data Mining Tutorial)</span></span>
  <span data-ttu-id="b3f85-103">이제 모델이 가장 정확 하다 고 판단 되 `TM_Decision_Tree` 면 [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] 타겟 메일링 캠페인의 요구에 맞게 모델을 사용자 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3f85-103">Now that you have determined that the `TM_Decision_Tree` model is the most accurate, you will customize the model to better suit the needs of the [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] targeted mailing campaign.</span></span> <span data-ttu-id="b3f85-104">특히 마케팅 부서는 남성와 여성 고객 간에 차이가 있는지 알고 싶습니다.</span><span class="sxs-lookup"><span data-stu-id="b3f85-104">Specifically, the Marketing department would like to know if there are any differences between male and female customers.</span></span> <span data-ttu-id="b3f85-105">이 정보를 통해 광고에 사용할 잡지를 결정 하는 데 도움이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b3f85-105">The information could help them decide which magazines to use for advertising and which products to feature in their mailings.</span></span>  
  
## <a name="using-filters"></a><span data-ttu-id="b3f85-106">필터 사용</span><span class="sxs-lookup"><span data-stu-id="b3f85-106">Using Filters</span></span>  
 <span data-ttu-id="b3f85-107">필터링을 사용하면 데이터의 하위 집합을 기반으로 하는 모델을 쉽게 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b3f85-107">Filtering enables you to easily create models built on subsets of your data.</span></span> <span data-ttu-id="b3f85-108">필터는 모델에만 적용되고 기본 데이터 원본을 변경하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b3f85-108">The filter is applied only to the model and does not change the underlying data source.</span></span>  
  
 <span data-ttu-id="b3f85-109">이 단원에서는 세임 및 여성의 구매 동작에 가장 영향을 주는 특성을 예측 하기 위해 성별에 대해 필터링 된 모델을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b3f85-109">In this lesson, you will create a model that is filtered on gender, to predict the characteristics that most influence buying behavior in males and female.</span></span>  
  
 <span data-ttu-id="b3f85-110">먼저 모델의 복사본을 만듭니다 `TM_Decision_Tree` .</span><span class="sxs-lookup"><span data-stu-id="b3f85-110">First you will make a copy of the `TM_Decision_Tree` model.</span></span>  
  
#### <a name="to-copy-the-decision-tree-model"></a><span data-ttu-id="b3f85-111">의사 결정 트리 모델을 복사하려면</span><span class="sxs-lookup"><span data-stu-id="b3f85-111">To copy the Decision Tree Model</span></span>  
  
1.  <span data-ttu-id="b3f85-112">의 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 솔루션 탐색기에서 **BasicDataMining**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3f85-112">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], in Solution Explorer, select **BasicDataMining**.</span></span>  
  
2.  <span data-ttu-id="b3f85-113">**마이닝 모델** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b3f85-113">Click the **Mining Models** tab.</span></span>  
  
3.  <span data-ttu-id="b3f85-114">모델을 마우스 오른쪽 단추로 클릭 `TM_Decision_Tree` 하 고 **새 마이닝 모델을 선택 합니다.**</span><span class="sxs-lookup"><span data-stu-id="b3f85-114">Right click the `TM_Decision_Tree` model, and select **New Mining Model.**</span></span>  
  
4.  <span data-ttu-id="b3f85-115">**모델 이름** 필드에을 입력 `TM_Decision_Tree_Male` 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3f85-115">In the **Model name** field, type `TM_Decision_Tree_Male`.</span></span>  
  
5.  <span data-ttu-id="b3f85-116">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b3f85-116">Click **OK**.</span></span>  
  
 <span data-ttu-id="b3f85-117">다음으로 해당 성을 기반으로 하는 모델에 대한 고객을 선택하는 필터를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b3f85-117">Next, create a filter to select customers for the model based on their gender.</span></span>  
  
#### <a name="to-create-a-case-filter-on-a-mining-model"></a><span data-ttu-id="b3f85-118">마이닝 모델에 사례 필터를 만들려면</span><span class="sxs-lookup"><span data-stu-id="b3f85-118">To create a case filter on a mining model</span></span>  
  
1.  <span data-ttu-id="b3f85-119">마이닝 모델을 마우스 오른쪽 단추로 클릭 `TM_Decision_Tree_Male` 하 여 바로 가기 메뉴를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="b3f85-119">Right-click the `TM_Decision_Tree_Male` mining model to open the shortcut menu.</span></span>  
  
     <span data-ttu-id="b3f85-120">-- 또는 --</span><span class="sxs-lookup"><span data-stu-id="b3f85-120">-- or --</span></span>  
  
     <span data-ttu-id="b3f85-121">모델을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b3f85-121">Select the model.</span></span> <span data-ttu-id="b3f85-122">**마이닝 모델** 메뉴에서 **모델 필터 설정**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b3f85-122">On the **Mining Model** menu, select **Set Model Filter**.</span></span>  
  
2.  <span data-ttu-id="b3f85-123">**모델 필터** 대화 상자의 **마이닝 구조 열** 입력란에서 표의 첫 행을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b3f85-123">In the **Model Filter** dialog box, click the top row in the grid, in the **Mining Structure Column** text box.</span></span>  
  
     <span data-ttu-id="b3f85-124">드롭다운 목록에서 해당 테이블에 있는 열의 이름만 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="b3f85-124">The drop-down list displays only the names of the columns in that table.</span></span>  
  
3.  <span data-ttu-id="b3f85-125">마이닝 구조 열 입력란에서 **성별**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3f85-125">In the Mining Structure Column text box, select **Gender**.</span></span>  
  
     <span data-ttu-id="b3f85-126">입력란의 왼쪽에 있는 아이콘이 변경되어 선택한 항목이 테이블인지 또는 열인지를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b3f85-126">The icon at the left side of the text box changes to indicate that the selected item is a table or a column.</span></span>  
  
4.  <span data-ttu-id="b3f85-127">**연산자** 입력란을 클릭 하 고 목록에서 등호 (=) 연산자를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3f85-127">Click the **Operator** text box and select the equal (=) operator from the list.</span></span>  
  
5.  <span data-ttu-id="b3f85-128">**값** 입력란을 클릭 하 고 **M**을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3f85-128">Click the **Value** text box, and type **M**.</span></span>  
  
6.  <span data-ttu-id="b3f85-129">표에서 다음 행을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b3f85-129">Click the next row in the grid.</span></span>  
  
7.  <span data-ttu-id="b3f85-130">**확인** 을 클릭 하 여 **모델 필터** 대화 상자를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="b3f85-130">Click **OK** to close the **Model Filter** dialog box.</span></span>  
  
     <span data-ttu-id="b3f85-131">필터가 **속성** 창에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b3f85-131">The filter displays in the **Properties** window.</span></span> <span data-ttu-id="b3f85-132">또는 **속성** 창에서 **모델 필터** 대화 상자를 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b3f85-132">Alternately, you can launch the **Model Filter** dialog from the **Properties** window.</span></span>  
  
8.  <span data-ttu-id="b3f85-133">위의 단계를 반복 하 되 이번에는 모델 이름을로, `TM_Decision_Tree_Female` **값** 텍스트 상자에 **F** 를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3f85-133">Repeat the above steps, but this time name the model `TM_Decision_Tree_Female` and type **F** in the **Value** text box.</span></span>  
  
## <a name="process-the-filtered-models"></a><span data-ttu-id="b3f85-134">필터링된 모델 처리</span><span class="sxs-lookup"><span data-stu-id="b3f85-134">Process the Filtered Models</span></span>  
 <span data-ttu-id="b3f85-135">모델은 배포 및 처리될 때까지 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b3f85-135">Models cannot be used until they have been deployed and processed.</span></span> <span data-ttu-id="b3f85-136">모델 처리에 대 한 자세한 내용은 [기본 데이터 마이닝 자습서 &#40;대상 메일 구조에서 모델 처리 ](../../2014/tutorials/processing-models-in-the-targeted-mailing-structure-basic-data-mining-tutorial.md)를 참조 하세요&#41;.</span><span class="sxs-lookup"><span data-stu-id="b3f85-136">For more information on processing models, see [Processing Models in the Targeted Mailing Structure &#40;Basic Data Mining Tutorial&#41;](../../2014/tutorials/processing-models-in-the-targeted-mailing-structure-basic-data-mining-tutorial.md).</span></span>  
  
#### <a name="to-process-the-filtered-model"></a><span data-ttu-id="b3f85-137">필터링된 모델을 처리하려면</span><span class="sxs-lookup"><span data-stu-id="b3f85-137">To process the filtered model</span></span>  
  
1.  <span data-ttu-id="b3f85-138">모델을 마우스 오른쪽 단추로 클릭 `TM_Decision_Tree_Male` 하 고 **마이닝 구조 및 모든 모델 처리를**선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3f85-138">Right-click the `TM_Decision_Tree_Male` model and select **Process Mining Structure and all Model**s</span></span>  
  
2.  <span data-ttu-id="b3f85-139">**실행** 을 클릭 하 여 새 모델을 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3f85-139">Click **Run** to process the new models.</span></span>  
  
3.  <span data-ttu-id="b3f85-140">처리가 완료 되 면 두 처리 창에서 **닫기** 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3f85-140">After processing is complete, click **Close** on both processing windows.</span></span>  
  
     <span data-ttu-id="b3f85-141">**마이닝 모델** 탭에 새 모델이 두 개 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b3f85-141">You now have two new models displayed in the **Mining Models** tab.</span></span>  
  
## <a name="evaluate-the-results"></a><span data-ttu-id="b3f85-142">결과 평가</span><span class="sxs-lookup"><span data-stu-id="b3f85-142">Evaluate the Results</span></span>  
 <span data-ttu-id="b3f85-143">이전 세 개의 모델에 대해 수행했던 방식과 거의 동일한 방식으로 결과를 검토하고 필터링된 모델의 정확도를 평가합니다.</span><span class="sxs-lookup"><span data-stu-id="b3f85-143">View the results and assess the accuracy of the filtered models in much the same way as you did for the previous three models.</span></span> <span data-ttu-id="b3f85-144">자세한 내용은 다음을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b3f85-144">For more information, see:</span></span>  
  
 [<span data-ttu-id="b3f85-145">기본 데이터 마이닝 자습서 &#40;의사 결정 트리 모델 탐색&#41;</span><span class="sxs-lookup"><span data-stu-id="b3f85-145">Exploring the Decision Tree Model &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/exploring-the-decision-tree-model-basic-data-mining-tutorial.md)  
  
 [<span data-ttu-id="b3f85-146">리프트 차트를 사용하여 정확도 테스트&#40;기본 데이터 마이닝 자습서&#41;</span><span class="sxs-lookup"><span data-stu-id="b3f85-146">Testing Accuracy with Lift Charts &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/testing-accuracy-with-lift-charts-basic-data-mining-tutorial.md)  
  
#### <a name="to-explore-the-filtered-models"></a><span data-ttu-id="b3f85-147">필터링된 모델을 탐색하려면</span><span class="sxs-lookup"><span data-stu-id="b3f85-147">To explore the filtered models</span></span>  
  
1.  <span data-ttu-id="b3f85-148">**데이터 마이닝 디자이너**에서 **마이닝 모델 뷰어** 탭을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3f85-148">Select the **Mining Model Viewer** tab in **Data Mining Designer**.</span></span>  
  
2.  <span data-ttu-id="b3f85-149">마이닝 모델 상자에서를 선택 `TM_Decision_Tree_Male` 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3f85-149">In the Mining Model box, select `TM_Decision_Tree_Male`.</span></span>  
  
3.  <span data-ttu-id="b3f85-150">**쇼 수준** 을로 이동 `3` 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3f85-150">Slide **Show Level** to `3`.</span></span>  
  
4.  <span data-ttu-id="b3f85-151">**배경** 값을로 변경 `1` 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3f85-151">Change the **Background** value to `1`.</span></span>  
  
5.  <span data-ttu-id="b3f85-152">**모두** 레이블이 지정 된 노드에 커서를 놓아 자전거 구매자와 비 자전거 구매자의 수를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3f85-152">Place your cursor over the node labeled **All** to see the number of bike buyers versus non-bike buyers.</span></span>  
  
6.  <span data-ttu-id="b3f85-153">에 대해 1-5 단계를 반복 `TM_Decision_Tree_Female` 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3f85-153">Repeat steps 1 - 5 for `TM_Decision_Tree_Female`.</span></span>  
  
7.  <span data-ttu-id="b3f85-154">및 성별에 대해 필터링 된 모델에 대 한 결과를 살펴봅니다 `TM_Decision_Tree` .</span><span class="sxs-lookup"><span data-stu-id="b3f85-154">Explore the results for the `TM_Decision_Tree` and the models filtered for gender.</span></span> <span data-ttu-id="b3f85-155">모든 자전거 구매자와 비교해 볼 때 남성 자전거 구매자와 여성 자전거 구매자는 필터링되지 않은 자전거 구매자와 동일한 특징을 일부 공유하지만 이 세 범주의 구매자에게는 흥미로운 차이점도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b3f85-155">Compared to all bike buyers, male and female bike buyers share some of the same characteristics as the unfiltered bike buyers but all three have interesting differences as well.</span></span> <span data-ttu-id="b3f85-156">이는 [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] 마케팅 캠페인을 개발 하는 데 사용할 수 있는 유용한 정보입니다.</span><span class="sxs-lookup"><span data-stu-id="b3f85-156">This is useful information that [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] can use to develop their marketing campaign.</span></span>  
  
#### <a name="to-test-the-lift-of-the-filtered-models"></a><span data-ttu-id="b3f85-157">필터링된 모델의 리프트를 테스트하려면</span><span class="sxs-lookup"><span data-stu-id="b3f85-157">To test the lift of the filtered models</span></span>  
  
1.  <span data-ttu-id="b3f85-158">의 데이터 마이닝 디자이너에서 **마이닝 정확도 차트** 탭으로 전환 하 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 고 **입력 선택** 탭을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3f85-158">Switch to the **Mining Accuracy Chart** tab in Data Mining Designer in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] and select the **Input Selection** tab.</span></span>  
  
2.  <span data-ttu-id="b3f85-159">**정확도 차트에 사용할 데이터 집합을 선택** 하십시오. 그룹 상자에서 **마이닝 구조 테스트 사례 사용**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3f85-159">In the **Select data set to be used for Accuracy Chart** group box, select **Use mining structure test cases**.</span></span>  
  
3.  <span data-ttu-id="b3f85-160">데이터 마이닝 디자이너의 **입력 선택** 탭에 있는 **리프트 차트에 표시할 예측 가능한 마이닝 모델 열을 선택**하십시오 .에서 **예측 열과 값 동기화**에 대 한 확인란을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3f85-160">On the **Input Selection** tab of Data Mining Designer, under **Select predictable mining model columns to show in the lift chart**, select the checkbox for **Synchronize Prediction Columns and Values**.</span></span>  
  
4.  <span data-ttu-id="b3f85-161">**예측 가능한 열 이름** 열에서 각 모델에 대해 **자전거 구매자** 가 선택 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3f85-161">In the **Predictable Column Name** column, verify that **Bike Buyer** is selected for each model.</span></span>  
  
5.  <span data-ttu-id="b3f85-162">**표시** 열에서 각 모델을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3f85-162">In the **Show** column, select each of the models.</span></span>  
  
6.  <span data-ttu-id="b3f85-163">**예측 값** 열에서을 선택 `1` 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3f85-163">In the **Predict Value** column, select `1`.</span></span>  
  
7.  <span data-ttu-id="b3f85-164">**리프트 차트 탭을** 선택 하 여 리프트 차트를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3f85-164">Select the **Lift Chart** tab to display the lift chart.</span></span>  
  
     <span data-ttu-id="b3f85-165">세 가지 의사 결정 트리 모델은 모두 임의 추측 모델과 비교했을 때 유효한 리프트를 제공할 뿐만 아니라 클러스터링 및 Naive-Bayes 모델보다 성능이 뛰어납니다.</span><span class="sxs-lookup"><span data-stu-id="b3f85-165">You will now notice that all three Decision Tree models provide significant lift compared to the random guess model, and also outperform the Clustering and Naive-Bayes models.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="b3f85-166">관련 작업</span><span class="sxs-lookup"><span data-stu-id="b3f85-166">Related Tasks</span></span>  
 <span data-ttu-id="b3f85-167">필터에 대 한 자세한 내용은 [데이터 마이닝&#41;Analysis Services &#40;마이닝 모델에 대 한 필터 ](../../2014/analysis-services/data-mining/filters-for-mining-models-analysis-services-data-mining.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b3f85-167">For more information on filters, see [Filters for Mining Models &#40;Analysis Services - Data Mining&#41;](../../2014/analysis-services/data-mining/filters-for-mining-models-analysis-services-data-mining.md).</span></span>  
  
 <span data-ttu-id="b3f85-168">중첩 테이블에 필터를 적용 하는 방법에 대 한 예는 [Analysis Services-데이터 마이닝&#41;&#40;중급 데이터 마이닝 자습서 ](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b3f85-168">For an example of how to apply filters to nested tables, see [Intermediate Data Mining Tutorial &#40;Analysis Services - Data Mining&#41;](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md).</span></span>  
  
## <a name="previous-task-in-lesson"></a><span data-ttu-id="b3f85-169">단원의 이전 태스크</span><span class="sxs-lookup"><span data-stu-id="b3f85-169">Previous Task in Lesson</span></span>  
 [<span data-ttu-id="b3f85-170">리프트 차트를 사용하여 정확도 테스트&#40;기본 데이터 마이닝 자습서&#41;</span><span class="sxs-lookup"><span data-stu-id="b3f85-170">Testing Accuracy with Lift Charts &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/testing-accuracy-with-lift-charts-basic-data-mining-tutorial.md)  
  
## <a name="next-lesson"></a><span data-ttu-id="b3f85-171">다음 단원</span><span class="sxs-lookup"><span data-stu-id="b3f85-171">Next Lesson</span></span>  
 [<span data-ttu-id="b3f85-172">6단원: 예측 만들기 및 작업&#40;기본 데이터 마이닝 자습서&#41;</span><span class="sxs-lookup"><span data-stu-id="b3f85-172">Lesson 6: Creating and Working with Predictions &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-6-creating-and-working-with-predictions-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="b3f85-173">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b3f85-173">See Also</span></span>  
 <span data-ttu-id="b3f85-174">[Analysis Services 데이터 마이닝&#41;&#40;중급 데이터 마이닝 자습서](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="b3f85-174">[Intermediate Data Mining Tutorial &#40;Analysis Services - Data Mining&#41;](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="b3f85-175">[마이닝 모델 태스크 및 방법](../../2014/analysis-services/data-mining/mining-model-tasks-and-how-tos.md) </span><span class="sxs-lookup"><span data-stu-id="b3f85-175">[Mining Model Tasks and How-tos](../../2014/analysis-services/data-mining/mining-model-tasks-and-how-tos.md) </span></span>  
 <span data-ttu-id="b3f85-176">[마이닝 모델에서 필터 삭제](../../2014/analysis-services/data-mining/delete-a-filter-from-a-mining-model.md) </span><span class="sxs-lookup"><span data-stu-id="b3f85-176">[Delete a Filter from a Mining Model](../../2014/analysis-services/data-mining/delete-a-filter-from-a-mining-model.md) </span></span>  
 [<span data-ttu-id="b3f85-177">마이닝 모델에 대한 필터&#40;Analysis Services - 데이터 마이닝&#41;</span><span class="sxs-lookup"><span data-stu-id="b3f85-177">Filters for Mining Models &#40;Analysis Services - Data Mining&#41;</span></span>](../../2014/analysis-services/data-mining/filters-for-mining-models-analysis-services-data-mining.md)  
  
  
