---
title: '4 단원: 자전거 구매자 마이닝 모델 찾아보기 | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 8de3c500-f881-42da-a096-b6c03300d58d
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 709df371d840d4b24e420b4fcd08750fd31e8075
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649876"
---
# <a name="lesson-4-browsing-the-bike-buyer-mining-models"></a><span data-ttu-id="594cd-102">4단원: Bike Buyer 마이닝 모델 찾아보기</span><span class="sxs-lookup"><span data-stu-id="594cd-102">Lesson 4: Browsing the Bike Buyer Mining Models</span></span>
  <span data-ttu-id="594cd-103">이 단원에서는 [SELECT (DMX)](/sql/dmx/select-dmx) 문을 사용 하 여 [2 단원: 예측 마이닝 구조에 마이닝 모델 추가](../../2014/tutorials/lesson-2-adding-mining-models-to-the-bike-buyer-mining-structure.md)에서 만든 의사 결정 트리의 내용과 클러스터링 마이닝 모델을 탐색 합니다.</span><span class="sxs-lookup"><span data-stu-id="594cd-103">In this lesson, you will use the [SELECT (DMX)](/sql/dmx/select-dmx) statement to explore the content in the decision tree and clustering mining models that you created in [Lesson 2: Adding Mining Models to the Predictive Mining Structure](../../2014/tutorials/lesson-2-adding-mining-models-to-the-bike-buyer-mining-structure.md).</span></span>  
  
 <span data-ttu-id="594cd-104">마이닝 모델에 포함된 열은 마이닝 구조에서 정의한 열이 아니라 알고리즘에서 찾은 경향 및 패턴을 설명하는 특정 열 집합입니다.</span><span class="sxs-lookup"><span data-stu-id="594cd-104">The columns contained in a mining model are not the columns defined by the mining structure, but instead are a specific set of columns that describe the trends and patterns that are found by the algorithm.</span></span> <span data-ttu-id="594cd-105">이러한 마이닝 모델 열은 [DMSCHEMA_MINING_MODEL_CONTENT 행 집합](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/dmschema-mining-model-content-rowset) 스키마 행 집합에 설명 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="594cd-105">These mining model columns are described in the [DMSCHEMA_MINING_MODEL_CONTENT Rowset](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/dmschema-mining-model-content-rowset) schema rowset.</span></span> <span data-ttu-id="594cd-106">예를 들어 내용 스키마 행 집합의 MODEL_NAME 열에는 마이닝 모델의 이름이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="594cd-106">For example, the MODEL_NAME column in the content schema rowset contains the name of the mining model.</span></span> <span data-ttu-id="594cd-107">클러스터링 마이닝 모델의 경우 NODE_CAPTION 열에는 각 클러스터의 이름이 포함되어 있으며 NODE_DESCRIPTION 열에는 각 클러스터의 특징에 대한 설명이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="594cd-107">For a clustering mining model, the NODE_CAPTION column contains the name of each cluster, and the NODE_DESCRIPTION column contains a description of the characteristics of each cluster.</span></span> <span data-ttu-id="594cd-108">SELECT FROM을 사용 하 여 이러한 열을 찾아볼 수 있습니다 \<model> . DMX의 CONTENT 문입니다.</span><span class="sxs-lookup"><span data-stu-id="594cd-108">You can browse these columns by using the SELECT FROM \<model>.CONTENT statement in DMX.</span></span> <span data-ttu-id="594cd-109">이 문을 사용하여 마이닝 모델 생성에 사용된 데이터도 탐색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="594cd-109">You can also use this statement to explore the data that was used to create the mining model.</span></span> <span data-ttu-id="594cd-110">이 문을 사용하려면 마이닝 구조에 드릴스루를 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="594cd-110">Drillthrough must be enabled on the mining structure in order to use this statement.</span></span> <span data-ttu-id="594cd-111">문에 대 한 자세한 내용은 [SELECT FROM &#60;model&#62;을 참조 하세요. DMX&#41;사례를 &#40;](/sql/dmx/select-from-model-content-dmx)합니다.</span><span class="sxs-lookup"><span data-stu-id="594cd-111">For more information about the statement, see [SELECT FROM &#60;model&#62;.CASES &#40;DMX&#41;](/sql/dmx/select-from-model-content-dmx).</span></span>  
  
 <span data-ttu-id="594cd-112">또한 SELECT DISTINCT 문을 사용하여 불연속 열의 모든 상태를 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="594cd-112">You can also return all the states of a discrete column by using the SELECT DISTINCT statement.</span></span> <span data-ttu-id="594cd-113">예를 들어 Gender 열에서 이 작업을 수행하면 쿼리는 `male` 및 `female`을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="594cd-113">For example, if you perform this operation on a gender column, the query will return `male` and `female`.</span></span>  
  
## <a name="lesson-tasks"></a><span data-ttu-id="594cd-114">단원 태스크</span><span class="sxs-lookup"><span data-stu-id="594cd-114">Lesson Tasks</span></span>  
 <span data-ttu-id="594cd-115">이 단원에서는 다음 태스크를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="594cd-115">You will perform the following tasks in this lesson:</span></span>  
  
-   <span data-ttu-id="594cd-116">마이닝 모델 내에 포함된 내용 탐색</span><span class="sxs-lookup"><span data-stu-id="594cd-116">Explore the content contained within the mining models</span></span>  
  
-   <span data-ttu-id="594cd-117">마이닝 모델의 학습에 사용된 원본 데이터에서 사례 반환</span><span class="sxs-lookup"><span data-stu-id="594cd-117">Return the cases from the source data that was used to train the mining models</span></span>  
  
-   <span data-ttu-id="594cd-118">특정 불연속 열에 가능한 다양한 상태 탐색</span><span class="sxs-lookup"><span data-stu-id="594cd-118">Explore the different states available for a specific discrete column</span></span>  
  
## <a name="returning-the-content-of-a-mining-model"></a><span data-ttu-id="594cd-119">마이닝 모델의 내용 반환</span><span class="sxs-lookup"><span data-stu-id="594cd-119">Returning the Content of a Mining Model</span></span>  
 <span data-ttu-id="594cd-120">이 단원에서는 [SELECT FROM &#60;모델&#62;를 사용 합니다. ](/sql/dmx/select-from-model-dimension-content-dmx)클러스터링 모델의 내용을 반환 하는 CONTENT &#40;DMX&#41;문입니다.</span><span class="sxs-lookup"><span data-stu-id="594cd-120">In this lesson, you use the [SELECT FROM &#60;model&#62;.CONTENT &#40;DMX&#41;](/sql/dmx/select-from-model-dimension-content-dmx) statement to return the contents of the clustering model.</span></span>  
  
 <span data-ttu-id="594cd-121">다음은 SELECT FROM의 일반적인 예입니다 \<model> . 콘텐츠 문:</span><span class="sxs-lookup"><span data-stu-id="594cd-121">The following is a generic example of the SELECT FROM \<model>.CONTENT statement:</span></span>  
  
```  
SELECT <select list> FROM [<mining model>].CONTENT  
WHERE <where clause>  
```  
  
 <span data-ttu-id="594cd-122">코드의 첫 번째 줄에서는 마이닝 모델 내용에서 반환할 열과 이 열이 연결된 마이닝 모델을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="594cd-122">The first line of the code defines the columns to return from the mining model content, and the mining model they are associated with:</span></span>  
  
```  
SELECT <select list> FROM [<mining model].CONTENT  
```  
  
 <span data-ttu-id="594cd-123">마이닝 모델 이름 옆에 있는 .CONTENT 절은 해당 마이닝 모델에서 내용을 반환함을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="594cd-123">The .CONTENT clause next to the name of the mining model specifies that you are returning content from the mining model.</span></span> <span data-ttu-id="594cd-124">마이닝 모델에 포함 된 열에 대 한 자세한 내용은 [DMSCHEMA_MINING_MODEL_CONTENT 행 집합](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/dmschema-mining-model-content-rowset)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="594cd-124">For more information about the columns contained in the mining model, see [DMSCHEMA_MINING_MODEL_CONTENT Rowset](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/dmschema-mining-model-content-rowset).</span></span>  
  
 <span data-ttu-id="594cd-125">필요에 따라 코드의 마지막 줄을 사용하여 문에서 반환한 결과를 필터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="594cd-125">You can optionally use the final line of the code to filter the results returned by the statement:</span></span>  
  
```  
WHERE <where clause>  
```  
  
 <span data-ttu-id="594cd-126">예를 들어 쿼리 결과를 사례 수가 많은 클러스터만으로 제한하려는 경우 SELECT 문에 다음 WHERE 절을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="594cd-126">For example, if you want to restrict the results of the query to only the clusters that contain a high number of cases, you can add the following WHERE clause to the SELECT statement:</span></span>  
  
```  
WHERE NODE_SUPPORT > 100  
```  
  
 <span data-ttu-id="594cd-127">WHERE 문을 사용 하는 방법에 대 한 자세한 내용은 [SELECT &#40;DMX&#41;](/sql/dmx/select-dmx)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="594cd-127">For more information about using the WHERE statement, see [SELECT &#40;DMX&#41;](/sql/dmx/select-dmx).</span></span>  
  
#### <a name="to-return-the-content-of-the-clustering-mining-model"></a><span data-ttu-id="594cd-128">클러스터링 마이닝 모델의 내용을 반환하려면</span><span class="sxs-lookup"><span data-stu-id="594cd-128">To return the content of the clustering mining model</span></span>  
  
1.  <span data-ttu-id="594cd-129">**개체 탐색기**에서 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]인스턴스를 마우스 오른쪽 단추로 클릭하고 **새 쿼리**를 가리킨 다음 **DMX**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="594cd-129">In **Object Explorer**, right-click the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], point to **New Query**, and then click **DMX**.</span></span>  
  
     <span data-ttu-id="594cd-130">비어 있는 새 쿼리가 포함된 쿼리 편집기가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="594cd-130">Query Editor opens and contains a new, blank query.</span></span>  
  
2.  <span data-ttu-id="594cd-131">SELECT FROM의 일반적인 예를 복사 \<model> 합니다. 빈 쿼리에 대 한 CONTENT 문입니다.</span><span class="sxs-lookup"><span data-stu-id="594cd-131">Copy the generic example of the SELECT FROM \<model>.CONTENT statement into the blank query.</span></span>  
  
3.  <span data-ttu-id="594cd-132">다음 내용을</span><span class="sxs-lookup"><span data-stu-id="594cd-132">Replace the following:</span></span>  
  
    ```  
    <select list>   
    ```  
  
     <span data-ttu-id="594cd-133">다음으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="594cd-133">with:</span></span>  
  
    ```  
    *  
    ```  
  
     <span data-ttu-id="594cd-134">\*를 [DMSCHEMA_MINING_MODEL_CONTENT 행 집합](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/dmschema-mining-model-content-rowset)에 포함 된 열 목록으로 바꿀 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="594cd-134">You can also replace \* with a list of any of the columns contained within the [DMSCHEMA_MINING_MODEL_CONTENT Rowset](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/dmschema-mining-model-content-rowset).</span></span>  
  
4.  <span data-ttu-id="594cd-135">다음 내용을</span><span class="sxs-lookup"><span data-stu-id="594cd-135">Replace the following:</span></span>  
  
    ```  
    [<mining model>]   
    ```  
  
     <span data-ttu-id="594cd-136">다음으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="594cd-136">with:</span></span>  
  
    ```  
    [Clustering]  
    ```  
  
     <span data-ttu-id="594cd-137">이제 전체 문이 다음과 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="594cd-137">The complete statement should now be as follows:</span></span>  
  
    ```  
    SELECT * FROM [Clustering].CONTENT  
    ```  
  
5.  <span data-ttu-id="594cd-138">**파일** 메뉴에서 **다른 이름으로 DMXQuery1.dmx 저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="594cd-138">On the **File** menu, click **Save DMXQuery1.dmx As**.</span></span>  
  
6.  <span data-ttu-id="594cd-139">다른 이름 **으로 저장** 대화 상자에서 해당 폴더로 이동한 다음 파일 이름을로 `SELECT_CONTENT.dmx` 합니다.</span><span class="sxs-lookup"><span data-stu-id="594cd-139">In the **Save As** dialog box, browse to the appropriate folder, and name the file `SELECT_CONTENT.dmx`.</span></span>  
  
7.  <span data-ttu-id="594cd-140">도구 모음에서 **실행** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="594cd-140">On the toolbar, click the **Execute** button.</span></span>  
  
     <span data-ttu-id="594cd-141">쿼리에서 마이닝 모델의 내용이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="594cd-141">The query returns the content of the mining model.</span></span>  
  
## <a name="use-drillthrough"></a><span data-ttu-id="594cd-142">드릴스루 사용</span><span class="sxs-lookup"><span data-stu-id="594cd-142">Use Drillthrough</span></span>  
 <span data-ttu-id="594cd-143">다음 단계는 드릴스루 문을 사용하여 의사 결정 트리 마이닝 모델의 학습에 사용된 사례의 샘플링을 반환하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="594cd-143">The next step is to use the drillthrough statement to return a sampling of the cases that were used to train the decision tree mining model.</span></span> <span data-ttu-id="594cd-144">이 단원에서는 [SELECT FROM &#60;모델&#62;를 사용 합니다. 사례는 DMX&#41;문을 &#40;](/sql/dmx/select-from-model-content-dmx) 하 여 의사 결정 트리 모델의 콘텐츠를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="594cd-144">In this lesson, you use the [SELECT FROM &#60;model&#62;.CASES &#40;DMX&#41;](/sql/dmx/select-from-model-content-dmx) statement to return the contents of the decision tree model.</span></span>  
  
 <span data-ttu-id="594cd-145">다음은 SELECT FROM의 일반적인 예입니다 \<model> . CASE 문:</span><span class="sxs-lookup"><span data-stu-id="594cd-145">The following is a generic example of the SELECT FROM \<model>.CASES statement:</span></span>  
  
```  
SELECT <select list>   
FROM [<mining model>].CASES  
WHERE IsInNode('<node id>')  
```  
  
 <span data-ttu-id="594cd-146">코드의 첫 번째 줄에서는 원본 데이터에서 반환할 열과 이 열이 포함된 마이닝 모델을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="594cd-146">The first line of the code defines the columns to return from the source data, and the mining model they are contained within:</span></span>  
  
```  
SELECT <select list> FROM [<mining model>].CASES  
```  
  
 <span data-ttu-id="594cd-147">.CASES 절은 드릴스루 쿼리를 수행함을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="594cd-147">The .CASES clause specifies that you are performing a drillthrough query.</span></span> <span data-ttu-id="594cd-148">드릴스루를 사용하려면 마이닝 모델을 만들 때 드릴스루를 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="594cd-148">In order to use drillthrough you must enable drillthrough when you create the mining model.</span></span>  
  
 <span data-ttu-id="594cd-149">코드의 마지막 줄은 선택 사항이며 사례를 요청할 마이닝 모델의 노드를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="594cd-149">The final line of the code is optional and specifies the node in the mining model that you are requesting cases from:</span></span>  
  
```  
WHERE IsInNode('<node id>')  
```  
  
 <span data-ttu-id="594cd-150">WHERE 문을 IsInNode와 함께 사용 하는 방법에 대 한 자세한 내용은 [SELECT FROM &#60;model&#62;을 참조 하세요. DMX&#41;사례를 &#40;](/sql/dmx/select-from-model-content-dmx)합니다.</span><span class="sxs-lookup"><span data-stu-id="594cd-150">For more information about using the WHERE statement with IsInNode, see [SELECT FROM &#60;model&#62;.CASES &#40;DMX&#41;](/sql/dmx/select-from-model-content-dmx).</span></span>  
  
#### <a name="to-return-the-cases-that-were-used-to-train-the-mining-model"></a><span data-ttu-id="594cd-151">마이닝 모델의 학습에 사용된 사례를 반환하려면</span><span class="sxs-lookup"><span data-stu-id="594cd-151">To return the cases that were used to train the mining model</span></span>  
  
1.  <span data-ttu-id="594cd-152">**개체 탐색기**에서 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]인스턴스를 마우스 오른쪽 단추로 클릭하고 **새 쿼리**를 가리킨 다음 **DMX**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="594cd-152">In **Object Explorer**, right-click the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], point to **New Query**, and then click **DMX**.</span></span>  
  
     <span data-ttu-id="594cd-153">비어 있는 새 쿼리가 포함된 쿼리 편집기가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="594cd-153">Query Editor opens and contains a new, blank query.</span></span>  
  
2.  <span data-ttu-id="594cd-154">SELECT FROM의 일반적인 예를 복사 \<model> 합니다. CASE 문을 빈 쿼리로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="594cd-154">Copy the generic example of the SELECT FROM \<model>.CASES statement into the blank query.</span></span>  
  
3.  <span data-ttu-id="594cd-155">다음 내용을</span><span class="sxs-lookup"><span data-stu-id="594cd-155">Replace the following:</span></span>  
  
    ```  
    <select list>   
    ```  
  
     <span data-ttu-id="594cd-156">다음으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="594cd-156">with:</span></span>  
  
    ```  
    *  
    ```  
  
     <span data-ttu-id="594cd-157">\*를 [Bike Buyer]와 같은 원본 데이터 내에 있는 임의의 열 목록으로 바꿀 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="594cd-157">You can also replace \* with a list of any of the columns contained within the source data (such as [Bike Buyer]).</span></span>  
  
4.  <span data-ttu-id="594cd-158">다음 내용을</span><span class="sxs-lookup"><span data-stu-id="594cd-158">Replace the following:</span></span>  
  
    ```  
    [<mining model>]   
    ```  
  
     <span data-ttu-id="594cd-159">다음으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="594cd-159">with:</span></span>  
  
    ```  
    [Decision Tree]  
    ```  
  
     <span data-ttu-id="594cd-160">이제 전체 문이 다음과 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="594cd-160">The complete statement should now be as follows:</span></span>  
  
    ```  
    SELECT *   
    FROM [Decision Tree].CASES  
    ```  
  
5.  <span data-ttu-id="594cd-161">**파일** 메뉴에서 **다른 이름으로 DMXQuery1.dmx 저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="594cd-161">On the **File** menu, click **Save DMXQuery1.dmx As**.</span></span>  
  
6.  <span data-ttu-id="594cd-162">다른 이름 **으로 저장** 대화 상자에서 해당 폴더로 이동한 다음 파일 이름을로 `SELECT_DRILLTHROUGH.dmx` 합니다.</span><span class="sxs-lookup"><span data-stu-id="594cd-162">In the **Save As** dialog box, browse to the appropriate folder, and name the file `SELECT_DRILLTHROUGH.dmx`.</span></span>  
  
7.  <span data-ttu-id="594cd-163">도구 모음에서 **실행** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="594cd-163">On the toolbar, click the **Execute** button.</span></span>  
  
     <span data-ttu-id="594cd-164">쿼리에서 의사 결정 트리 마이닝 모델의 학습에 사용된 원본 데이터가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="594cd-164">The query returns the source data that was used to train the decision tree mining model.</span></span>  
  
## <a name="return-the-states-of-a-discrete-mining-model-column"></a><span data-ttu-id="594cd-165">불연속 마이닝 모델 열의 상태 반환</span><span class="sxs-lookup"><span data-stu-id="594cd-165">Return the States of a Discrete Mining Model Column</span></span>  
 <span data-ttu-id="594cd-166">다음 단계는 SELECT DISTINCT 문을 사용하여 지정된 마이닝 모델 열에 가능한 다양한 상태를 반환하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="594cd-166">The next step is to use the SELECT DISTINCT statement to return the different possible states in the specified mining model column.</span></span>  
  
 <span data-ttu-id="594cd-167">다음은 SELECT DISTINCT 문의 일반적인 예입니다.</span><span class="sxs-lookup"><span data-stu-id="594cd-167">The following is a generic example of the SELECT DISTINCT statement:</span></span>  
  
```  
SELECT DISTINCT [<column>]   
FROM [<mining model>]  
```  
  
 <span data-ttu-id="594cd-168">코드의 첫 번째 줄에서는 상태가 반환된 마이닝 모델 열을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="594cd-168">The first line of the code defines the mining model columns for which the states are returned:</span></span>  
  
```  
SELECT DISTINCT [<column>]   
```  
  
 <span data-ttu-id="594cd-169">열의 모든 상태를 반환하려면 DISTINCT를 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="594cd-169">You must include DISTINCT in order to return all of the states of the column.</span></span> <span data-ttu-id="594cd-170">DISTINCT를 제외하면 전체 문이 예측의 바로 가기가 되며 지정된 열이 있을 가능성이 가장 높은 상태를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="594cd-170">If you exclude DISTINCT, then the full statement becomes a shortcut for a prediction and returns the most likely state of the specified column.</span></span> <span data-ttu-id="594cd-171">자세한 내용은 [SELECT&#40;DMX&#41;](/sql/dmx/select-dmx)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="594cd-171">For more information, see [SELECT &#40;DMX&#41;](/sql/dmx/select-dmx).</span></span>  
  
#### <a name="to-return-the-states-of-a-discrete-column"></a><span data-ttu-id="594cd-172">불연속 열의 상태를 반환하려면</span><span class="sxs-lookup"><span data-stu-id="594cd-172">To return the states of a discrete column</span></span>  
  
1.  <span data-ttu-id="594cd-173">**개체 탐색기**에서 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]인스턴스를 마우스 오른쪽 단추로 클릭하고 **새 쿼리**를 가리킨 다음 **DMX**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="594cd-173">In **Object Explorer**, right-click the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], point to **New Query**, and then click **DMX**.</span></span>  
  
     <span data-ttu-id="594cd-174">비어 있는 새 쿼리가 포함된 쿼리 편집기가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="594cd-174">Query Editor opens and contains a new, blank query.</span></span>  
  
2.  <span data-ttu-id="594cd-175">SELECT Distinct 문의 일반적인 예를 빈 쿼리에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="594cd-175">Copy the generic example of the SELECT Distinct statement into the blank query.</span></span>  
  
3.  <span data-ttu-id="594cd-176">다음 내용을</span><span class="sxs-lookup"><span data-stu-id="594cd-176">Replace the following:</span></span>  
  
    ```  
    [<column,name>   
    ```  
  
     <span data-ttu-id="594cd-177">다음으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="594cd-177">with:</span></span>  
  
    ```  
    [Bike Buyer]  
    ```  
  
4.  <span data-ttu-id="594cd-178">다음 내용을</span><span class="sxs-lookup"><span data-stu-id="594cd-178">Replace the following:</span></span>  
  
    ```  
    [<mining model>]   
    ```  
  
     <span data-ttu-id="594cd-179">다음으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="594cd-179">with:</span></span>  
  
    ```  
    [Decision Tree]  
    ```  
  
     <span data-ttu-id="594cd-180">이제 전체 문이 다음과 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="594cd-180">The complete statement should now be as follows:</span></span>  
  
    ```  
    SELECT DISTINCT [Bike Buyer]   
    FROM [Decision Tree]  
    ```  
  
5.  <span data-ttu-id="594cd-181">**파일** 메뉴에서 **다른 이름으로 DMXQuery1.dmx 저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="594cd-181">On the **File** menu, click **Save DMXQuery1.dmx As**.</span></span>  
  
6.  <span data-ttu-id="594cd-182">다른 이름 **으로 저장** 대화 상자에서 해당 폴더로 이동한 다음 파일 이름을로 `SELECT_DISCRETE.dmx` 합니다.</span><span class="sxs-lookup"><span data-stu-id="594cd-182">In the **Save As** dialog box, browse to the appropriate folder, and name the file `SELECT_DISCRETE.dmx`.</span></span>  
  
7.  <span data-ttu-id="594cd-183">도구 모음에서 **실행** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="594cd-183">On the toolbar, click the **Execute** button.</span></span>  
  
     <span data-ttu-id="594cd-184">쿼리에서 Bike Buyer 열의 가능한 상태가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="594cd-184">The query returns the possible states of the Bike Buyer column.</span></span>  
  
 <span data-ttu-id="594cd-185">다음 단원에서는 의사 결정 트리 마이닝 모델을 사용하여 잠재 고객이 자전거 구매자가 될 것인지 여부를 예측합니다.</span><span class="sxs-lookup"><span data-stu-id="594cd-185">In the next lesson, you will predict whether potential customers will be bike buyers by using the decision tree mining model.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="594cd-186">다음 단원</span><span class="sxs-lookup"><span data-stu-id="594cd-186">Next Lesson</span></span>  
 [<span data-ttu-id="594cd-187">5단원: 예측 쿼리 실행</span><span class="sxs-lookup"><span data-stu-id="594cd-187">Lesson 5: Executing Prediction Queries</span></span>](../../2014/tutorials/lesson-5-executing-prediction-queries.md)  
  
  
