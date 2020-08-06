---
title: 모델에 예측 함수 적용 | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Mining Model Prediction [Analysis Services], selecting mining models
ms.assetid: cf9a97e2-c249-441b-af12-c977c1a91c44
author: minewiskan
ms.author: owend
ms.openlocfilehash: fde9de00adaa1712a9db6e18aabc6a83dd660efb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646727"
---
# <a name="apply-prediction-functions-to-a-model"></a><span data-ttu-id="dab84-102">모델에 예측 함수 적용</span><span class="sxs-lookup"><span data-stu-id="dab84-102">Apply Prediction Functions to a Model</span></span>
  <span data-ttu-id="dab84-103">예측 쿼리를 만들려면 먼저 쿼리의 기반이 될 마이닝 모델을 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dab84-103">To create a prediction query, you must first select the mining model on which the query will be based.</span></span> <span data-ttu-id="dab84-104">현재 프로젝트에 있는 모든 마이닝 모델을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dab84-104">You can select any mining model that exists in the current project.</span></span>  
  
 <span data-ttu-id="dab84-105">모델을 선택한 후에는 쿼리에 *예측 함수* 를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="dab84-105">After you have selected a model, add a *prediction function* to the query.</span></span> <span data-ttu-id="dab84-106">예측 함수는 다양 한 용도에 사용 된다는 점을 이해 하기 위해 가져옵니다. 예, 값을 예측할 수는 있지만 예측을 생성 하는 데 사용 된 정보 뿐만 아니라 관련 통계만 가져올 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dab84-106">It is import to understand that prediction functions are used for many purposes-yes, you can predict values, but you can also get related statistics, as well as information that was used in generating the prediction.</span></span> <span data-ttu-id="dab84-107">예측 함수는 다음과 같은 유형의 값을 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dab84-107">Prediction functions can return the following types of values:</span></span>  
  
-   <span data-ttu-id="dab84-108">예측 가능한 특성의 이름과 예측된 값</span><span class="sxs-lookup"><span data-stu-id="dab84-108">The name of the predictable attribute, and the value that is predicted.</span></span>  
  
-   <span data-ttu-id="dab84-109">예측된 값의 분포 및 편차에 대한 통계</span><span class="sxs-lookup"><span data-stu-id="dab84-109">Statistics about the distribution and variance of the predicted values.</span></span>  
  
-   <span data-ttu-id="dab84-110">지정된 결과 또는 가능한 모든 결과의 확률</span><span class="sxs-lookup"><span data-stu-id="dab84-110">The probability of a specified outcome, or of all possible outcomes.</span></span>  
  
-   <span data-ttu-id="dab84-111">최상위/최하위 점수 또는 값</span><span class="sxs-lookup"><span data-stu-id="dab84-111">The top or bottom scores or values.</span></span>  
  
-   <span data-ttu-id="dab84-112">지정된 노드, 개체 또는 특성과 연관된 값</span><span class="sxs-lookup"><span data-stu-id="dab84-112">Values associated with a specified node, object, or attribute.</span></span>  
  
 <span data-ttu-id="dab84-113">다양한 예측 함수를 사용할 수 있지만 작성한 모델의 유형에 적합한 함수를 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dab84-113">There is a wide variety of prediction functions that you can use, but you must choose the function that suits the type of model you created.</span></span> <span data-ttu-id="dab84-114">일반적으로 함수 선택은 모델을 만드는 데 사용된 알고리즘에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="dab84-114">Usually this choice depends on the algorithm used to create the model.</span></span>  
  
-   <span data-ttu-id="dab84-115">거의 모든 모델 유형에 대해 지원되는 예측 함수 목록은 [일반 예측 함수&#40;DMX&#41;](/sql/dmx/general-prediction-functions-dmx)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="dab84-115">For a list of the prediction functions that are supported for almost all model types, see [General Prediction Functions &#40;DMX&#41;](/sql/dmx/general-prediction-functions-dmx).</span></span>  
  
-   <span data-ttu-id="dab84-116">또한 개별 알고리즘에서 다양한 특수 함수를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="dab84-116">Additionally, individual algorithms support a variety of specialized functions.</span></span> <span data-ttu-id="dab84-117">예를 들어 Microsoft 클러스터링 알고리즘을 기반으로 하는 마이닝 모델을 만드는 경우 특수 예측 함수를 사용하여 데이터 값에서 클러스터 중심까지의 거리와 같은 클러스터 관련 정보를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dab84-117">For example, if you create a mining model based on the Microsoft Clustering algorithm, you can use specialized prediction functions to find information about the clusters, such as the distance from a data value to the cluster centroid.</span></span>  
  
     <span data-ttu-id="dab84-118">특정 유형의 마이닝 모델을 쿼리하는 방법에 대한 예제는 [데이터 마이닝 알고리즘&#40;Analysis Services - 데이터 마이닝&#41;](data-mining-algorithms-analysis-services-data-mining.md)에서 알고리즘 참조 항목을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="dab84-118">For examples of how to query a specific type of mining model, see the algorithm reference topic, in [Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](data-mining-algorithms-analysis-services-data-mining.md).</span></span>  
  
### <a name="choose-a-mining-model-to-use-for-prediction"></a><span data-ttu-id="dab84-119">예측에 사용할 마이닝 모델 선택</span><span class="sxs-lookup"><span data-stu-id="dab84-119">Choose a mining model to use for prediction</span></span>  
  
1.  <span data-ttu-id="dab84-120">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 모델을 마우스 오른쪽 단추로 클릭하고 **예측 쿼리 작성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="dab84-120">From [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], right-click the model, and select **Build Prediction Query**.</span></span>  
  
     <span data-ttu-id="dab84-121">--또는--</span><span class="sxs-lookup"><span data-stu-id="dab84-121">--OR --</span></span>  
  
     <span data-ttu-id="dab84-122">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]에서 **마이닝 모델 예측**탭을 클릭한 다음 **마이닝 모델** 테이블에서  **모델 선택** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="dab84-122">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], click the tab, **Mining Model Prediction**, and then click **Select Model** in the  **Mining Model** table.</span></span>  
  
2.  <span data-ttu-id="dab84-123">**마이닝 모델 선택** 대화 상자에서 마이닝 모델을 선택한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="dab84-123">In the **Select Mining Model** dialog box, select a mining model, and then click **OK**.</span></span>  
  
     <span data-ttu-id="dab84-124">현재 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 데이터베이스 내의 모든 모델을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dab84-124">You can choose any model within the current [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database.</span></span> <span data-ttu-id="dab84-125">다른 데이터베이스의 모델을 사용하여 쿼리를 만들려면 해당 데이터베이스의 컨텍스트에서 새 쿼리 창을 열거나 해당 모델이 포함된 솔루션 파일을 열어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dab84-125">To create a query using a model in a different database, you must either open a new query window in the context of that database, or open the solution file that contains that model.</span></span>  
  
### <a name="add-prediction-functions-to-a-query"></a><span data-ttu-id="dab84-126">쿼리에 예측 함수 추가</span><span class="sxs-lookup"><span data-stu-id="dab84-126">Add prediction functions to a query</span></span>  
  
1.  <span data-ttu-id="dab84-127">**예측 쿼리 작성기**에서 **단일 쿼리 입력** 대화 상자에 값을 제공하거나 외부 데이터 원본에 모델을 매핑하여 예측에 사용할 입력 데이터를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="dab84-127">In the **Prediction Query Builder**, configure the input data used for prediction, either by providing values in the **Singleton Query Input** dialog box, or by mapping the model to an external data source.</span></span>  
  
     <span data-ttu-id="dab84-128">자세한 내용은 [예측 쿼리에 대한 입력 데이터 선택 및 매핑](choose-and-map-input-data-for-a-prediction-query.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="dab84-128">For more information, see [Choose and Map Input Data for a Prediction Query](choose-and-map-input-data-for-a-prediction-query.md).</span></span>  
  
    > [!WARNING]  
    >  <span data-ttu-id="dab84-129">입력을 제공하지 않아도 예측을 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dab84-129">It is not required that you provide inputs to generate predictions.</span></span> <span data-ttu-id="dab84-130">입력이 없으면 일반적으로 알고리즘에서 가능한 모든 입력 중 가능성이 가장 높은 예측 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="dab84-130">When there is no input, the algorithm will typically return the mostly likely predicted value across all possible inputs.</span></span>  
  
2.  <span data-ttu-id="dab84-131">**원본** 열을 클릭하고 목록에서 값을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="dab84-131">Click the **Source** column, and choose a value from the list:</span></span>  
  
    |||  
    |-|-|  
    |**\<model name>**|<span data-ttu-id="dab84-132">마이닝 모델의 값을 출력에 포함하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="dab84-132">Select this option to include values from the mining model in the output.</span></span> <span data-ttu-id="dab84-133">예측 가능한 열만 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dab84-133">You can only add predictable columns.</span></span><br /><br /> <span data-ttu-id="dab84-134">모델에서 열을 추가하면 해당 열의 고유하지 않은 값 목록이 결과로 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="dab84-134">When you add a column from the model, the result returned is the non-distinct list of values in that column.</span></span><br /><br /> <span data-ttu-id="dab84-135">이 옵션을 사용하여 추가한 열은 결과 DMX 문의 SELECT 부분에 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="dab84-135">The columns that you add with this option are included in the SELECT portion of the resulting DMX statement.</span></span>|  
    |<span data-ttu-id="dab84-136">**Prediction Function**</span><span class="sxs-lookup"><span data-stu-id="dab84-136">**Prediction Function**</span></span>|<span data-ttu-id="dab84-137">예측 함수 목록을 찾아보려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="dab84-137">Select this option to browse a list of prediction functions.</span></span><br /><br /> <span data-ttu-id="dab84-138">선택한 값 또는 함수는 결과 DMX 문의 SELECT 부분에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="dab84-138">The values or functions you select are added to the SELECT portion of the resulting DMX statement.</span></span><br /><br /> <span data-ttu-id="dab84-139">예측 함수 목록은 선택한 모델 유형에 의해 제한되거나 필터링되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="dab84-139">The list of prediction functions is not filtered or constrained by the type of model you have selected.</span></span> <span data-ttu-id="dab84-140">따라서 함수가 현재 모델 유형에 대해 지원되는지 잘 모를 경우 해당 함수를 목록에 추가하고 오류가 발생하는지 확인하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dab84-140">Therefore, if you have any doubt about whether the function is supported for the current model type, you can just add the function to the list and see if there is an error.</span></span><br /><br /> <span data-ttu-id="dab84-141">$가 앞에 오는 목록 항목(예: $AdjustedProbability)은 `PredictHistogram` 함수를 사용할 때의 출력인 중첩 테이블의 열을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="dab84-141">List items that are preceded by $ (such as $AdjustedProbability) represent columns from the nested table that is output when you use the function, `PredictHistogram`.</span></span> <span data-ttu-id="dab84-142">이는 중첩 테이블이 아니라 단일 열을 반환하는 데 사용할 수 있는 간편한 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="dab84-142">These are shortcuts that you can use to return a single column and not a nested table.</span></span>|  
    |<span data-ttu-id="dab84-143">**사용자 지정 식**</span><span class="sxs-lookup"><span data-stu-id="dab84-143">**Custom Expression**</span></span>|<span data-ttu-id="dab84-144">사용자 지정 식을 입력한 다음 출력에 별칭을 할당하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="dab84-144">Select this option to type a custom expression and then assign an alias to the output.</span></span><br /><br /> <span data-ttu-id="dab84-145">사용자 지정 식은 결과 DMX 예측 쿼리의 SELECT 부분에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="dab84-145">The custom expression is added to the SELECT portion of the resulting DMX prediction query.</span></span><br /><br /> <span data-ttu-id="dab84-146">이 옵션은 각 행과 함께 출력 텍스트를 추가하거나, VB 함수를 호출하거나, 사용자 지정 저장 프로시저를 호출하려는 경우에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="dab84-146">This option is useful if you want to add text for output with each row, to call VB functions, or to call custom stored procedures.</span></span><br /><br /> <span data-ttu-id="dab84-147">DMX에서 VBA 및 Excel 함수를 사용하는 방법은 [MDX 및 DAX의 VBA 함수](/sql/mdx/vba-functions-in-mdx-and-dax)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="dab84-147">For information about using VBA and Excel functions from DMX, see [VBA functions in MDX and DAX](/sql/mdx/vba-functions-in-mdx-and-dax).</span></span>|  
  
3.  <span data-ttu-id="dab84-148">각 함수나 식을 추가한 후에는 DMX 뷰로 전환하여 함수가 DMX 문 내에 어떻게 추가되었는지를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="dab84-148">After adding each function or expression, switch to DMX view to see how the function is added within the DMX statement.</span></span>  
  
    > [!WARNING]  
    >  <span data-ttu-id="dab84-149">예측 쿼리 작성기는 **결과**를 클릭할 때까지 DMX에 대한 유효성을 검사하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="dab84-149">The Prediction Query Builder does not validate the DMX until you click **Results**.</span></span> <span data-ttu-id="dab84-150">쿼리 작성기에서 생성된 식이 유효한 DMX가 아닌 경우를 종종 발견하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dab84-150">Often, you will find that the expression that is produced by the query builder is not valid DMX.</span></span> <span data-ttu-id="dab84-151">일반적으로 이는 예측 가능한 열과 관련되지 않은 열을 참조하거나 중첩 테이블에서 열을 예측(하위 SELECT 문이 필요함)하려는 경우에 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="dab84-151">Typical causes are referencing a column that is not related to the predictable column, or trying to predict a column in a nested table, which requires a sub-SELECT statement.</span></span> <span data-ttu-id="dab84-152">이제 DMX 뷰로 전환하여 문을 계속 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dab84-152">At this point, you can switch to DMX view and continue editing the statement.</span></span>  
  
### <a name="example-create-a-query-on-a-clustering-model"></a><span data-ttu-id="dab84-153">예: 클러스터링 모델에서 쿼리 만들기</span><span class="sxs-lookup"><span data-stu-id="dab84-153">Example: Create a query on a clustering model</span></span>  
  
1.  <span data-ttu-id="dab84-154">이 예제 쿼리를 작성하는 데 사용할 수 있는 클러스터링 모델이 없는 경우 [기본 데이터 마이닝 자습서](../../tutorials/basic-data-mining-tutorial.md)를 사용하여 [TM_Clustering] 모델을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="dab84-154">If you do not have a clustering model available for building this sample query, create the model, [TM_Clustering], using the [Basic Data Mining Tutorial](../../tutorials/basic-data-mining-tutorial.md).</span></span>  
  
2.  <span data-ttu-id="dab84-155">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 [TM_Clustering] 모델을 마우스 오른쪽 단추로 클릭하고 **예측 쿼리 작성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="dab84-155">From [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], right-click the model, [TM_Clustering], and select **Build Prediction Query**.</span></span>  
  
3.  <span data-ttu-id="dab84-156">**마이닝 모델** 메뉴에서 **단일 쿼리**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="dab84-156">From the **Mining Model** menu, select **Singleton Query**.</span></span>  
  
4.  <span data-ttu-id="dab84-157">**단일 쿼리 입력** 대화 상자에서 다음 값을 입력으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="dab84-157">In the **Singleton Query Input** dialog box, set the following values as inputs:</span></span>  
  
    -   <span data-ttu-id="dab84-158">Gender = M</span><span class="sxs-lookup"><span data-stu-id="dab84-158">Gender = M</span></span>  
  
    -   <span data-ttu-id="dab84-159">Commute Distance = 5-10 miles</span><span class="sxs-lookup"><span data-stu-id="dab84-159">Commute Distance = 5-10 miles</span></span>  
  
5.  <span data-ttu-id="dab84-160">표 형태 창에서 **원본**에 대해 TM_Clustering 마이닝 모델을 선택하고 [Bike Buyer] 열을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="dab84-160">In the query grid, for **Source**, select TM_Clustering mining model, and add the column, [Bike Buyer].</span></span>  
  
6.  <span data-ttu-id="dab84-161">**원본**에 대해 **예측 함수**를 선택 하 고 함수를 추가 `Cluster` 합니다.</span><span class="sxs-lookup"><span data-stu-id="dab84-161">For **Source**, select **Prediction Function**, and add the function, `Cluster`.</span></span>  
  
7.  <span data-ttu-id="dab84-162">**원본**에 대해 **예측 함수**를 선택 하 고 함수를 추가한 `PredictSupport` 다음 모델 열 [자전거 구매자]를 **조건/인수** 상자로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="dab84-162">For **Source**, select **Prediction Function**, add the function, `PredictSupport`, and drag the model column [Bike Buyer] into the **Criteria/Argument** box.</span></span> <span data-ttu-id="dab84-163">**별칭** 열에 **Support** 를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="dab84-163">Type **Support** in the **Alias** column.</span></span>  
  
     <span data-ttu-id="dab84-164">**조건/인수** 상자에서 예측 함수 및 열 참조를 나타내는 식을 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="dab84-164">Copy the expression representing the prediction function and column reference from the **Criteria/Argument** box.</span></span>  
  
8.  <span data-ttu-id="dab84-165">**원본**에 대해 **사용자 지정 식**을 선택하고 별칭을 입력한 후 다음 구문을 사용하여 Excel CEILING 함수를 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="dab84-165">For **Source**, select **Custom Expression**, type an alias, and then reference the Excel CEILING function by using the following syntax:</span></span>  
  
    ```  
    Excel![CEILING](<arguments) as <return type>  
    ```  
  
     <span data-ttu-id="dab84-166">열 참조를 함수의 인수로 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="dab84-166">Paste the column reference in as the argument to the function.</span></span>  
  
     <span data-ttu-id="dab84-167">예를 들어 다음 식은 지원 값의 CEILING을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="dab84-167">For example, the following expression returns the CEILING of the support value:</span></span>  
  
    ```  
    EXCEL!CEILING(PredictSupport([TM_Clustering].[Bike Buyer]),2)  
    ```  
  
     <span data-ttu-id="dab84-168">**별칭** 열에 CEILING을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="dab84-168">Type CEILING in the **Alias** column.</span></span>  
  
9. <span data-ttu-id="dab84-169">**쿼리 텍스트 뷰로 전환** 을 클릭하여 생성된 DMX 문을 검토한 다음 **쿼리 결과 뷰로 전환** 을 클릭하여 예측 쿼리에서 출력된 열을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="dab84-169">Click **Switch to query text view** to review the DMX statement that was generated, and then click **Switch to query result view** to see the columns output by the prediction query.</span></span>  
  
     <span data-ttu-id="dab84-170">다음 표에는 예상 결과가 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dab84-170">The following table shows the expected results:</span></span>  
  
    |<span data-ttu-id="dab84-171">Bike Buyer</span><span class="sxs-lookup"><span data-stu-id="dab84-171">Bike Buyer</span></span>|<span data-ttu-id="dab84-172">$Cluster</span><span class="sxs-lookup"><span data-stu-id="dab84-172">$Cluster</span></span>|<span data-ttu-id="dab84-173">별칭</span><span class="sxs-lookup"><span data-stu-id="dab84-173">SUPPORT</span></span>|<span data-ttu-id="dab84-174">CEILING</span><span class="sxs-lookup"><span data-stu-id="dab84-174">CEILING</span></span>|  
    |----------------|--------------|-------------|-------------|  
    |<span data-ttu-id="dab84-175">0</span><span class="sxs-lookup"><span data-stu-id="dab84-175">0</span></span>|<span data-ttu-id="dab84-176">클러스터 8</span><span class="sxs-lookup"><span data-stu-id="dab84-176">Cluster 8</span></span>|<span data-ttu-id="dab84-177">954</span><span class="sxs-lookup"><span data-stu-id="dab84-177">954</span></span>|<span data-ttu-id="dab84-178">953.948638926372</span><span class="sxs-lookup"><span data-stu-id="dab84-178">953.948638926372</span></span>|  
  
 <span data-ttu-id="dab84-179">문의 다른 위치에 다른 절을 추가 하려는 경우 (예: WHERE 절을 추가 하려는 경우) 그리드를 사용 하 여 추가할 수 없습니다. 먼저 DMX 뷰로 전환 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dab84-179">If you want to add other clauses elsewhere in the statement-for example, if you want to add a WHERE clause-you cannot add it by using the grid; you must switch to DMX view first.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dab84-180">참고 항목</span><span class="sxs-lookup"><span data-stu-id="dab84-180">See Also</span></span>  
 [<span data-ttu-id="dab84-181">데이터 마이닝 쿼리</span><span class="sxs-lookup"><span data-stu-id="dab84-181">Data Mining Queries</span></span>](data-mining-queries.md)  
  
  
