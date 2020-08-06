---
title: 마이닝 모델의 중첩 테이블 필터링 (중급 데이터 마이닝 자습서) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 0a3ae0e5-897b-4898-a60d-5455eec3d305
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: a1e6ce2936a3c6763ea41999b2724c0fe8c79301
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739015"
---
# <a name="filtering-a-nested-table-in-a-mining-model-intermediate-data-mining-tutorial"></a><span data-ttu-id="67859-102">마이닝 모델의 중첩 테이블 필터링(중급 데이터 마이닝 자습서)</span><span class="sxs-lookup"><span data-stu-id="67859-102">Filtering a Nested Table in a Mining Model (Intermediate Data Mining Tutorial)</span></span>
  <span data-ttu-id="67859-103">모델을 만들고 탐색한 후 고객 데이터의 하위 집합에 초점을 맞추기로 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="67859-103">After you have created and explored the model, you decide that you want to focus on a subset of the customer data.</span></span> <span data-ttu-id="67859-104">예를 들어 특정 항목을 포함하는 바구니만 분석하거나 특정 기간 동안 아무 것도 구매하지 않은 고객에 대한 인구 통계를 분석할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67859-104">For example, you might want to analyze only the baskets that contain a specific item, or to analyze the demographics of customers who have not purchased anything in a certain period.</span></span>  
  
 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]<span data-ttu-id="67859-105">에서는 마이닝 모델에 사용되는 데이터를 필터링하는 기능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="67859-105">provides the ability to filter the data that is used in a mining model.</span></span> <span data-ttu-id="67859-106">이 기능은 다른 데이터를 사용 하기 위해 새 데이터 원본 뷰를 설정할 필요가 없기 때문에 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="67859-106">This feature is useful because you do not need to set up a new data source view to use different data.</span></span> <span data-ttu-id="67859-107">기본 데이터 마이닝 자습서에서는 사례 테이블에 조건을 적용하여 플랫 테이블의 데이터를 필터링하는 방법을 배웠습니다.</span><span class="sxs-lookup"><span data-stu-id="67859-107">In the Basic Data Mining Tutorial, you learned how to filter data from a flat table by applying conditions to the case table.</span></span> <span data-ttu-id="67859-108">이 태스크에서는 중첩 테이블에 적용되는 필터를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="67859-108">In this task, you create a filter that applies to a nested table.</span></span>  
  
## <a name="filters-on-nested-vs-case-tables"></a><span data-ttu-id="67859-109">중첩 테이블 및 사례 테이블에 대한 필터</span><span class="sxs-lookup"><span data-stu-id="67859-109">Filters on Nested vs. Case Tables</span></span>  
 <span data-ttu-id="67859-110">Association 모델에 사용되는 데이터 원본 뷰와 같이 데이터 원본 뷰에 사례 테이블 및 중첩 테이블이 포함되어 있는 경우 사례 테이블의 값, 중첩 테이블에서의 값 존재 여부 또는 이 둘을 조합한 조건을 기준으로 필터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67859-110">If your data source view contains a case table and a nested table, like the data source view used in the Association model, you can filter on values from the case table, the presence or absence of a value in the nested table, or some combination of both.</span></span>  
  
 <span data-ttu-id="67859-111">이 태스크에서는 먼저 Association 모델의 복사본을 만든 다음 사례 테이블에서 IncomeGroup 및 Region 특성을 기준으로 필터링할 수 있도록 해당 특성을 새 관련 모델에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="67859-111">In this task, you will first make a copy of the Association model and then add the IncomeGroup and Region attributes to the new related model, so that you can filter on those attributes in the case table.</span></span>  
  
#### <a name="to-create-and-modify-a-copy-of-the-association-model"></a><span data-ttu-id="67859-112">Association 모델의 복사본을 만들고 수정하려면</span><span class="sxs-lookup"><span data-stu-id="67859-112">To create and modify a copy of the Association model</span></span>  
  
1.  <span data-ttu-id="67859-113">의 **마이닝 모델** 탭에서 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 모델을 마우스 오른쪽 단추로 클릭 `Association` 하 고 **새 마이닝 모델**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="67859-113">In the **Mining Models** tab of [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], right-click the `Association` model, and select **New Mining Model**.</span></span>  
  
2.  <span data-ttu-id="67859-114">**모델 이름**에을 입력 `Association Filtered` 합니다.</span><span class="sxs-lookup"><span data-stu-id="67859-114">For **Model Name**, type `Association Filtered`.</span></span> <span data-ttu-id="67859-115">**알고리즘 이름**에서 **Microsoft 연결 규칙**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="67859-115">For **Algorithm Name**, select **Microsoft Association Rules**.</span></span> <span data-ttu-id="67859-116">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="67859-116">Click **OK**.</span></span>  
  
3.  <span data-ttu-id="67859-117">연결 필터링 된 모델의 열에서 IncomeGroup 행을 클릭 하 고 값을 **무시** 에서 **입력**으로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="67859-117">In the column for the Association Filtered model, click the IncomeGroup row and change the value from **Ignore** to **Input**.</span></span>  
  
 <span data-ttu-id="67859-118">다음으로 새 연결 모델의 사례 테이블에 대한 필터를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="67859-118">Next, you will create a filter on the case table in the new association model.</span></span> <span data-ttu-id="67859-119">모델에서 대상 지역에 있거나 대상 소득 수준을 가진 고객만 필터를 통과하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="67859-119">The filter will pass to the model only the customers in the target region or with the target income level.</span></span> <span data-ttu-id="67859-120">그런 다음 두 번째 필터 조건 집합을 추가하여 시장 바구니에 하나 이상의 항목이 포함된 고객만 모델에 사용되도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="67859-120">Then, you will add a second set of filter conditions to specify that the model uses only customers whose shopping baskets contained at least one item.</span></span>  
  
#### <a name="to-add-a-filter-to-a-mining-model"></a><span data-ttu-id="67859-121">마이닝 모델에 필터를 추가하려면</span><span class="sxs-lookup"><span data-stu-id="67859-121">To add a filter to a mining model</span></span>  
  
1.  <span data-ttu-id="67859-122">**마이닝 모델** 탭에서 필터링 된 모델 연결을 마우스 오른쪽 단추로 클릭 하 고 **모델 필터 설정**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="67859-122">In the **Mining Models** tab, right-click the model Association Filtered, and select **Set Model Filter**.</span></span>  
  
2.  <span data-ttu-id="67859-123">**모델 필터** 대화 상자의 **마이닝 구조 열** 입력란에서 표의 첫 행을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="67859-123">In the **Model Filter** dialog box, click the top row in the grid, in the **Mining Structure Column** text box.</span></span>  
  
3.  <span data-ttu-id="67859-124">**마이닝 구조 열** 텍스트 상자에서 IncomeGroup를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="67859-124">In the **Mining Structure Column** text box, select IncomeGroup.</span></span>  
  
     <span data-ttu-id="67859-125">입력란 왼쪽에 있는 아이콘이 변경되어 선택한 항목이 열임을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="67859-125">The icon at the left side of the text box changes to indicate that the selected item is a column.</span></span>  
  
4.  <span data-ttu-id="67859-126">**연산자** 텍스트 상자를 클릭 하 고 **=** 목록에서 연산자를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="67859-126">Click the **Operator** text box and select the **=** operator from the list.</span></span>  
  
5.  <span data-ttu-id="67859-127">**값** 입력란을 클릭 하 고 `High` 상자에를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="67859-127">Click the **Value** text box, and type `High` in the box.</span></span>  
  
6.  <span data-ttu-id="67859-128">표에서 다음 행을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="67859-128">Click the next row in the grid.</span></span>  
  
7.  <span data-ttu-id="67859-129">표의 다음 행에서 **AND/OR** 입력란을 클릭 하 고 **또는**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="67859-129">Click the **AND/OR** text box in the next row of the grid and select **OR**.</span></span>  
  
8.  <span data-ttu-id="67859-130">**마이닝 구조 열** 텍스트 상자에서 IncomeGroup를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="67859-130">In the **Mining Structure Column** text box, select IncomeGroup.</span></span> <span data-ttu-id="67859-131">**값** 텍스트 상자에을 입력 `Moderate` 합니다.</span><span class="sxs-lookup"><span data-stu-id="67859-131">In the **Value** text box, type `Moderate`.</span></span>  
  
     <span data-ttu-id="67859-132">만든 필터 조건이 **식** 입력란에 자동으로 추가 되 고 다음과 같이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="67859-132">The filter condition that you created is automatically added to the **Expression** text box, and should appears as follows:</span></span>  
  
     `[IncomeGroup] = 'High' OR [IncomeGroup] = 'Moderate'`  
  
9. <span data-ttu-id="67859-133">표에서 다음 행을 클릭 하 **고**연산자를 기본값 ()으로 그대로 둡니다.</span><span class="sxs-lookup"><span data-stu-id="67859-133">Click the next row in the grid, leaving the operator as the default, **AND**.</span></span>  
  
10. <span data-ttu-id="67859-134">**연산자**에 대해 기본값인 **Contains**를 그대로 둡니다.</span><span class="sxs-lookup"><span data-stu-id="67859-134">For **Operator**, leave the default value, **Contains**.</span></span> <span data-ttu-id="67859-135">**값** 텍스트 상자를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="67859-135">Click the **Value** text box.</span></span>  
  
11. <span data-ttu-id="67859-136">**필터** 대화 상자의 **마이닝 구조 열**아래에 있는 첫 번째 행에서을 선택 `Model` 합니다.</span><span class="sxs-lookup"><span data-stu-id="67859-136">In the **Filter** dialog box, in the first row under **Mining Structure Column**, select `Model`.</span></span>  
  
12. <span data-ttu-id="67859-137">**연산자**에 대해 **not NULL**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="67859-137">For **Operator**, select **IS NOT NULL**.</span></span> <span data-ttu-id="67859-138">**값** 텍스트 상자를 비워 둡니다.</span><span class="sxs-lookup"><span data-stu-id="67859-138">Leave the **Value** text box blank.</span></span> <span data-ttu-id="67859-139">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="67859-139">Click **OK**.</span></span>  
  
     <span data-ttu-id="67859-140">**모델 필터** 대화 상자의 **식** 텍스트 상자에 있는 필터 조건은 중첩 테이블에 새 조건을 포함 하도록 자동으로 업데이트 됩니다.</span><span class="sxs-lookup"><span data-stu-id="67859-140">The filter condition in the **Expression** text box of the **Model Filter** dialog box is automatically updated to include the new condition on the nested table.</span></span> <span data-ttu-id="67859-141">전체 식은</span><span class="sxs-lookup"><span data-stu-id="67859-141">The completed expression is as follows:</span></span>  
  
     `[IncomeGroup] = 'High' OR [IncomeGroup] = 'Moderate' AND EXISTS SELECT * FROM [vAssocSeqLineItems] WHERE [Model] <> NULL).`  
  
13. [!INCLUDE[clickOK](../includes/clickok-md.md)] ``  
  
#### <a name="to-enable-drillthrough-and-to-process-the-filtered-model"></a><span data-ttu-id="67859-142">드릴스루를 사용하고 필터링된 모델을 처리하려면</span><span class="sxs-lookup"><span data-stu-id="67859-142">To enable drillthrough and to process the filtered model</span></span>  
  
1.  <span data-ttu-id="67859-143">**마이닝 모델** 탭에서 모델을 마우스 오른쪽 단추로 클릭 `Association Filtered` 하 고 **속성**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="67859-143">In the **Mining Models** tab, right-click the `Association Filtered` model, and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="67859-144">**Allowdrillthrough** 속성을 **True**로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="67859-144">Change the **AllowDrillThrough** property to **True**.</span></span>  
  
3.  <span data-ttu-id="67859-145">마이닝 모델을 마우스 오른쪽 단추로 클릭 `Association Filtered` 하 고 **모델 처리**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="67859-145">Right-click the `Association Filtered` mining model, and select **Process Model**.</span></span>  
  
4.  <span data-ttu-id="67859-146">오류 메시지에서 **예** 를 클릭 하 여 데이터베이스에 새 모델을 배포 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="67859-146">Click **Yes** in the error message to deploy the new model to the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database.</span></span>  
  
5.  <span data-ttu-id="67859-147">**마이닝 구조 처리** 대화 상자에서 **실행**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="67859-147">In the **Process Mining Structure** dialog box, click **Run**.</span></span>  
  
6.  <span data-ttu-id="67859-148">처리가 완료 되 면 **닫기** 를 클릭 하 여 **처리 진행률** 대화 상자를 종료 하 고 **닫기** 를 다시 클릭 하 여 **마이닝 구조 처리** 대화 상자를 종료 합니다.</span><span class="sxs-lookup"><span data-stu-id="67859-148">When processing is complete click **Close** to exit the **Process Progress** dialog box, and click **Close** again to exit the **Process Mining Structure** dialog box.</span></span>  
  
 <span data-ttu-id="67859-149">Microsoft 일반 콘텐츠 트리 뷰어를 사용하여 NODE_SUPPORT에 대한 값을 확인함으로써 필터링된 모델에 원래 모델보다 적은 사례가 포함되어 있음을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67859-149">You can verify by using the Microsoft Generic Content Tree viewer and looking at the value for NODE_SUPPORT that the filtered model contains fewer cases than the original model.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="67859-150">설명</span><span class="sxs-lookup"><span data-stu-id="67859-150">Remarks</span></span>  
 <span data-ttu-id="67859-151">방금 만든 중첩 테이블 필터는 중첩 테이블에 하나 이상의 행이 있는지 여부만 확인하지만 특정 제품이 있는지 여부를 확인하는 필터 조건을 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67859-151">The nested table filter that you just created checks only for the presence of at least one row in the nested table; however, you can also create filter conditions that check for the presence of specific products.</span></span>  <span data-ttu-id="67859-152">예를 들어 다음과 같은 필터를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67859-152">For example, you could create the following filter:</span></span>  
  
```  
[IncomeGroup] = 'High' AND  
 EXISTS (SELECT * FROM [<nested table name>] WHERE [Model] = 'Water Bottle' )   
```  
  
 <span data-ttu-id="67859-153">이 문은 사례 테이블의 고객을 물병을 구매한 고객으로만 제한함을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="67859-153">This statement means that you are restricting the customers from the case table to only those who have purchased a water bottle.</span></span> <span data-ttu-id="67859-154">그러나 중첩 테이블 특성의 수는 잠재적으로 제한이 없기 때문에 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]는 선택 가능한 값 목록을 제공하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="67859-154">However, because the number of nested table attributes is potentially unlimited, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] does not supply a list of possible values from which to select.</span></span> <span data-ttu-id="67859-155">대신 정확한 값을 입력해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="67859-155">Instead, you must type the exact value.</span></span>  
  
 <span data-ttu-id="67859-156">**쿼리 편집** 을 클릭 하 여 필터 식을 수동으로 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67859-156">You can click **Edit Query** to manually change the filter expression.</span></span> <span data-ttu-id="67859-157">그러나 필터 식의 임의 부분을 수동으로 변경하면 표가 비활성화되어 텍스트 편집 모드에서만 필터 식 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67859-157">However, if you change any part of a filter expression manually, the grid will be disabled and thereafter you must work with the filter expression in text edit mode only.</span></span> <span data-ttu-id="67859-158">표 편집 모드를 복원하려면 해당 필터 식을 지우고 다시 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="67859-158">To restore grid editing mode, you must clear the filter expression and start over.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="67859-159">중첩 테이블 필터에는 LIKE 연산자를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="67859-159">You cannot use the LIKE operator in a nested table filter.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="67859-160">단원의 다음 태스크</span><span class="sxs-lookup"><span data-stu-id="67859-160">Next Task in Lesson</span></span>  
 [<span data-ttu-id="67859-161">&#40;중급 데이터 마이닝 자습서의 연결 예측&#41;</span><span class="sxs-lookup"><span data-stu-id="67859-161">Predicting Associations &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/predicting-associations-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="67859-162">참고 항목</span><span class="sxs-lookup"><span data-stu-id="67859-162">See Also</span></span>  
 <span data-ttu-id="67859-163">[모델 필터 구문 및 예제 &#40;Analysis Services 데이터 마이닝&#41;](../../2014/analysis-services/data-mining/model-filter-syntax-and-examples-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="67859-163">[Model Filter Syntax and Examples &#40;Analysis Services - Data Mining&#41;](../../2014/analysis-services/data-mining/model-filter-syntax-and-examples-analysis-services-data-mining.md) </span></span>  
 [<span data-ttu-id="67859-164">마이닝 모델에 대한 필터&#40;Analysis Services - 데이터 마이닝&#41;</span><span class="sxs-lookup"><span data-stu-id="67859-164">Filters for Mining Models &#40;Analysis Services - Data Mining&#41;</span></span>](../../2014/analysis-services/data-mining/filters-for-mining-models-analysis-services-data-mining.md)  
  
  
