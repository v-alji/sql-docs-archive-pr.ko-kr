---
title: 데이터 마이닝 시작 (Excel 용 데이터 마이닝 추가 기능) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: cbe10a19-e194-408e-a65b-5fdf3fb1e880
author: minewiskan
ms.author: owend
ms.openlocfilehash: 066fc72fa0570d56376cc73478a68e42d20ffbc4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647964"
---
# <a name="getting-started-with-data-mining-data-mining-add-ins-for-excel"></a><span data-ttu-id="bd61c-102">데이터 마이닝 시작하기(Excel용 데이터 마이닝 추가 기능)</span><span class="sxs-lookup"><span data-stu-id="bd61c-102">Getting Started with Data Mining (Data Mining Add-ins for Excel)</span></span>
  <span data-ttu-id="bd61c-103">데이터 마이닝은 데이터에서 의미 있는 패턴을 발견하기 위한 프로세스입니다.</span><span class="sxs-lookup"><span data-stu-id="bd61c-103">Data mining is the process of discovering meaningful patterns in data.</span></span> <span data-ttu-id="bd61c-104">데이터 마이닝은 기존의 BI를 통해 데이터를 탐색 및 파악하는 프로세스를 자연스럽게 보완합니다.</span><span class="sxs-lookup"><span data-stu-id="bd61c-104">Data mining is a natural complement to the process of exploring and understanding your data through traditional BI.</span></span> <span data-ttu-id="bd61c-105">컴퓨터 알고리즘을 사용해서 매우 많은 양의 데이터를 처리하고 숨겨져 있는 패턴 및 추세를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd61c-105">Machine algorithms can process very large amounts of data and discover patterns and trends that would otherwise be hidden.</span></span>  
  
 <span data-ttu-id="bd61c-106">데이터 마이닝을 수행 하려면 특정 질문과 관련 된 데이터를 수집 합니다 (예: "고객은 누구 인가요?").</span><span class="sxs-lookup"><span data-stu-id="bd61c-106">To do data mining, you collect data that is relevant to a specific question, such as "Who are my customers?"</span></span> <span data-ttu-id="bd61c-107">또는 "구매한 제품은 무엇 인가요?"</span><span class="sxs-lookup"><span data-stu-id="bd61c-107">or "what products were purchased?"</span></span> <span data-ttu-id="bd61c-108">그런 다음 알고리즘을 적용 하 여 데이터에서 통계 상관 관계를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="bd61c-108">and then apply an algorithm to find statistical correlations in the data.</span></span> <span data-ttu-id="bd61c-109">분석을 통해 발견된 패턴과 추세는 마이닝 모델로 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="bd61c-109">The patterns and trends found through analysis are stored as a mining model.</span></span> <span data-ttu-id="bd61c-110">그런 후 다음과 같이 비즈니스 시나리오에서 새로운 데이터에 마이닝 모델을 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd61c-110">You can then apply the mining model to new data, in business scenarios such as these:</span></span>  
  
-   <span data-ttu-id="bd61c-111">이전의 추세를 사용해서 다음 분기에 대한 매출, 재고 요구 사항 또는 고객 만족도를 예측합니다.</span><span class="sxs-lookup"><span data-stu-id="bd61c-111">Use past trends to forecast sales for the next quarter, inventory requirements, or customer satisfaction.</span></span>  
  
-   <span data-ttu-id="bd61c-112">현재 고객에 대한 지식을 적용해서 새로운 고객을 프로파일링하고 새로운 제품 또는 기회를 제안합니다.</span><span class="sxs-lookup"><span data-stu-id="bd61c-112">Apply knowledge of current customers to profile new customers and recommend new products or opportunities.</span></span>  
  
-   <span data-ttu-id="bd61c-113">이전 이벤트 사이의 상관 관계를 찾아서 서버 오류 또는 가동 중지 시간을 예측합니다.</span><span class="sxs-lookup"><span data-stu-id="bd61c-113">Find correlations among past events to predict server failures or downtime.</span></span>  
  
-   <span data-ttu-id="bd61c-114">고객이 함께 주문한 제품을 분석하고 이 정보를 사용해서 묶음 상품을 제안하거나 제품 배치를 계획합니다.</span><span class="sxs-lookup"><span data-stu-id="bd61c-114">Analyze which products customers purchase together and use the information to recommend bundles or plan product placement.</span></span>  
  
 <span data-ttu-id="bd61c-115">분석 방법 선택은 목표에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="bd61c-115">The method of analysis you choose depends on your goals.</span></span> <span data-ttu-id="bd61c-116">데이터 마이닝 추가 기능은 다음과 같은 유형의 분석을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="bd61c-116">The Data Mining Add-ins support these types of analysis:</span></span>  
  
-   <span data-ttu-id="bd61c-117">감독 및 자율 학습</span><span class="sxs-lookup"><span data-stu-id="bd61c-117">Supervised and unsupervised learning</span></span>  
  
-   <span data-ttu-id="bd61c-118">클러스터링(세그먼트화)</span><span class="sxs-lookup"><span data-stu-id="bd61c-118">Clustering (segmentation)</span></span>  
  
-   <span data-ttu-id="bd61c-119">요인 분석(Bayesian 및 신경망 사용)</span><span class="sxs-lookup"><span data-stu-id="bd61c-119">Factor analysis, using Bayesian and neural networks</span></span>  
  
-   <span data-ttu-id="bd61c-120">시계열 분석</span><span class="sxs-lookup"><span data-stu-id="bd61c-120">Time series analysis</span></span>  
  
-   <span data-ttu-id="bd61c-121">협회 분석, 권장 사항 및 시장 바구니 분석</span><span class="sxs-lookup"><span data-stu-id="bd61c-121">Association analysis, recommendations, and shopping basket analysis</span></span>  
  
-   <span data-ttu-id="bd61c-122">이진 결과 채점</span><span class="sxs-lookup"><span data-stu-id="bd61c-122">Scoring binary outcomes</span></span>  
  
-   <span data-ttu-id="bd61c-123">선형 회귀</span><span class="sxs-lookup"><span data-stu-id="bd61c-123">Linear regression</span></span>  
  
 <span data-ttu-id="bd61c-124">또한 추가 기능은 데이터 준비 단계에 대 한 도움말을 제공 합니다. 데이터 선택, 탐색 및 데이터 정리를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd61c-124">In addition, the add-ins provide help the data preparation phase: data selection, exploration, and data cleansing.</span></span>  
  
## <a name="define-your-goal"></a><span data-ttu-id="bd61c-125">목표 정의</span><span class="sxs-lookup"><span data-stu-id="bd61c-125">Define Your Goal</span></span>  
 <span data-ttu-id="bd61c-126">시작하기 전에 답을 구하고자 하는 질문을 고려합니다.</span><span class="sxs-lookup"><span data-stu-id="bd61c-126">Before you get started, take a minute to consider the question you really want to answer.</span></span> <span data-ttu-id="bd61c-127">탐색은 그 자체로도 통찰을 얻는 데 효과적이지만 발견한 결과를 새로운 데이터에 적용하고 싶은 경우, 해당 모델이 생성할 것이 무엇인지 그리고 해당 모델을 통해 달성되는 목표를 어떻게 측정할 수 있는지 명확하게 규정할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd61c-127">Exploration for its own sake is illuminating, but if you want to apply your findings to new data, you should be able to state clearly what you expect the model to produce, and how you will measure whether the model accomplishes your goals.</span></span>  
  
 <span data-ttu-id="bd61c-128">예를 들어 "새 고객 찾기"의 목표 보다는 "제품을 구매할 가능성이 높은 고객의 인구 통계를 확인 하 고, 최소 65%의 확률을 사용 하 여"와 같은 구체적인 항목에 대 한 목표를 명확 하 게 파악할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd61c-128">For example, rather than a goal of "finding new customers", clarify your objective to something more concrete, such as "identify the demographics of customers that are likely to buy our product, with a probability of at least 65%".</span></span>  
  
-   <span data-ttu-id="bd61c-129">데이터 집합은 학습 및 예측에 사용할 수 있는 "결과" 특성을 하나 이상 포함 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd61c-129">Your dataset should contain at least one "result" attribute that you can use for training and prediction.</span></span> <span data-ttu-id="bd61c-130">그러한 특성이 없으면 일부 학습 데이터를 수동으로 분류하거나 다른 열을 사용해서 결과에 대한 대안 특성을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd61c-130">If there is no such attribute, you can manually label some training data, or use other columns to create a proxy for the outcome.</span></span>  
  
     <span data-ttu-id="bd61c-131">예를 들어 "최고의 잠재 고객"을 예측 하려는 경우 기존 고객에 게 레이블을 지정 하기 위해 일부 비즈니스 규칙을 미리 적용 하 여 사용자가 제공 하는 예제에서 데이터 마이닝을 학습할 수 있도록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd61c-131">For example, if you want to predict "the best prospects", you should apply some business rule beforehand to label existing customers, so that data mining can learn from the examples you provide.</span></span>  
  
-   <span data-ttu-id="bd61c-132">시간에 따라 변경되는 값을 사용할 경우, 미래 추세를 예측하려면 필요한 결과의 세분성을 고려해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd61c-132">If you are working with a value that changes over time, and want to predict future trends, think about the granularity of the results you need.</span></span> <span data-ttu-id="bd61c-133">일별, 월별 또는 연도별 예측을 원합니까?</span><span class="sxs-lookup"><span data-stu-id="bd61c-133">Do you want predictions for a month, day, or yearly basis?</span></span> <span data-ttu-id="bd61c-134">분석할 데이터는 예측과 동일한 단위를 사용해서 처리되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd61c-134">Your data has to be analyzed using the same units that you want to predict.</span></span>  
  
     <span data-ttu-id="bd61c-135">순환 패턴을 사용 하는 경우 매일 데이터를 사용 하 여 좋은 결과를 얻지 못하는 경우 다른 시간 조각을 시도 하거나 주, 월 또는 휴일을 사용해 보세요.</span><span class="sxs-lookup"><span data-stu-id="bd61c-135">With cyclical patterns, if you don't get good results with daily data, try different time slices, or try using week days, months, or even holidays.</span></span>  
  
-   <span data-ttu-id="bd61c-136">마법사를 사용해서 데이터에서 새로운 상관 관계를 찾기 전에, 데이터를 다시 한 번 살펴보고 데이터 세트에 어떤 기존 관계가 존재할 수 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="bd61c-136">Before you launch a wizard to find new correlations in your data, take one more look at your data and consider what sort of existing relationships might be present in the dataset.</span></span> <span data-ttu-id="bd61c-137">혼동되는 변수가 있습니까?</span><span class="sxs-lookup"><span data-stu-id="bd61c-137">Are there confounding variables?</span></span> <span data-ttu-id="bd61c-138">중복 항목이나 프록시가 있습니까?</span><span class="sxs-lookup"><span data-stu-id="bd61c-138">Are there duplicates or proxies?</span></span>  
  
-   <span data-ttu-id="bd61c-139">모델의 성공을 평가 하는 메트릭은 무엇 인가요?</span><span class="sxs-lookup"><span data-stu-id="bd61c-139">What are the metrics by which the model's success will be evaluated?</span></span> <span data-ttu-id="bd61c-140">모델이 "충분히 양호" 하다는 것을 어떻게 알 수 있나요?</span><span class="sxs-lookup"><span data-stu-id="bd61c-140">How will you know that the model is "good enough"?</span></span>  
  
-   <span data-ttu-id="bd61c-141">데이터 마이닝 모델을 사용하여 예측을 만들 것입니까 아니면 주목할 만한 패턴 및 관계만 찾을 것입니까?</span><span class="sxs-lookup"><span data-stu-id="bd61c-141">Do you want to make predictions from the data mining model or just look for interesting patterns and associations?</span></span>  
  
## <a name="explore-your-data-and-explore-the-model"></a><span data-ttu-id="bd61c-142">데이터 탐색 및 모델 탐색</span><span class="sxs-lookup"><span data-stu-id="bd61c-142">Explore Your Data and Explore the Model</span></span>  
 <span data-ttu-id="bd61c-143">이미 데이터와 영역을 완전히 파악했을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd61c-143">Perhaps you already thoroughly understand the data and the domain.</span></span> <span data-ttu-id="bd61c-144">그렇더라도 모델링을 염두에 두고 충분한 시간을 들여 데이터를 프로파일링해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd61c-144">Even if you do, you should take some time to profile your data with modeling in mind.</span></span>  
  
 <span data-ttu-id="bd61c-145">값 분포를 충분히 확인하고 누락된 값이나 자리 표시자와 같은 잠재적인 문제가 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="bd61c-145">Take a minute to view the distribution of values, and identify potential problems such as missing values or placeholders.</span></span>  
  
 <span data-ttu-id="bd61c-146">다른 방법으로 분석할 수 없는 너무 크거나 복잡 한 데이터 집합에 대해 데이터 마이닝을 수행 하려는 경우 샘플링 또는 데이터 축소를 고려 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd61c-146">If you are planning to perform data mining against a data set that was so large or complex that you couldn't analyze it with other methods, consider sampling or data reduction.</span></span>  
  
-   <span data-ttu-id="bd61c-147">데이터가 어떻게 배포되어 있습니까?</span><span class="sxs-lookup"><span data-stu-id="bd61c-147">How is the data distributed?</span></span>  
  
-   <span data-ttu-id="bd61c-148">열이 서로 어떻게 연결되어 있습니까? 테이블이 여러 개인 경우 테이블이 서로 어떻게 연결되어 있습니까?</span><span class="sxs-lookup"><span data-stu-id="bd61c-148">How are the columns related, or if there are multiple tables, how are the tables related?</span></span>  
  
-   <span data-ttu-id="bd61c-149">값이 누락되었습니까?</span><span class="sxs-lookup"><span data-stu-id="bd61c-149">Are any values missing?</span></span> <span data-ttu-id="bd61c-150">변환하거나 전처리해야 하는 값이 있습니까?</span><span class="sxs-lookup"><span data-stu-id="bd61c-150">Are there values that need conversion or preprocessing?</span></span>  
  
-   <span data-ttu-id="bd61c-151">데이터가 대부분 텍스트나 숫자입니까 아니면 섞여 있습니까?</span><span class="sxs-lookup"><span data-stu-id="bd61c-151">Is the data mostly text, mostly numbers, or a mix?</span></span>  
  
-   <span data-ttu-id="bd61c-152">목표 결과에 대한 분석을 뒷받침할 만큼 데이터가 충분합니까?</span><span class="sxs-lookup"><span data-stu-id="bd61c-152">Do you have enough data to support analysis of the targeted outcomes?</span></span> <span data-ttu-id="bd61c-153">제품 간의 연결을 분석하는 경우 훨씬 더 많은 데이터가 필요할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd61c-153">If you are analyzing associations among products, you might need lots more data.</span></span> <span data-ttu-id="bd61c-154">이진 결과를 예측하려는 경우 데이터 세트에 균형이 있으면 훨씬 적은 데이터로 결과를 구할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd61c-154">If you are predicting a binary outcome, you can get by with much less, assuming the dataset is balanced.</span></span>  
  
 <span data-ttu-id="bd61c-155">모델이 완료되었으면 충분한 시간을 들여 결과를 검토하고 데이터를 수정하거나 더 나은 결과를 가져올 수 있는 방법이 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="bd61c-155">After your model is complete, take some time to review the results and identify ways to amend the data or get better results.</span></span> <span data-ttu-id="bd61c-156">첫 번째 모델로 모든 답변을 제공할 수 있을 확률은 극히 희박합니다.</span><span class="sxs-lookup"><span data-stu-id="bd61c-156">It is exceedingly rare that your first model provides all the answers.</span></span> <span data-ttu-id="bd61c-157">데이터 마이닝은 일반적으로 반복된 프로세스입니다.</span><span class="sxs-lookup"><span data-stu-id="bd61c-157">Data mining is typically an iterative process.</span></span>  
  
 <span data-ttu-id="bd61c-158">데이터를 다른 방식으로 범주화 하거나 새 열을 추가 하는 경우 **모델 문서화** 마법사를 사용 하 여 각 모델의 메타 데이터 및 결과에 대 한 스냅숏을 캡처해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd61c-158">As you try binning your data different ways, or adding new columns, remember to use the **Document Model** wizard to capture a snapshot of each model's metadata and results.</span></span> <span data-ttu-id="bd61c-159">기록은 탐색을 진행하는 데 유용한 도구로 활용될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd61c-159">Having a record will make it easier to track progress in your exploration.</span></span>  
  
 [<span data-ttu-id="bd61c-160">데이터 탐색 및 지우기</span><span class="sxs-lookup"><span data-stu-id="bd61c-160">Exploring and Cleaning Data</span></span>](exploring-and-cleaning-data.md)  
  
## <a name="validate-your-model"></a><span data-ttu-id="bd61c-161">모델의 유효성 검사</span><span class="sxs-lookup"><span data-stu-id="bd61c-161">Validate Your Model</span></span>  
 <span data-ttu-id="bd61c-162">각 마법사 또는 도구를 실행할 때마다 해당 알고리즘은 데이터 콘텐츠를 분석하고 통계적으로 유효한 패턴이 존재하는지 여부를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="bd61c-162">As you run each wizard or tool, the algorithm analyzes the contents of the data and determines whether a statistically valid pattern exists.</span></span> <span data-ttu-id="bd61c-163">알고리즘이 유효한 패턴을 찾을 수 없으면 오류 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bd61c-163">If the algorithm cannot find valid patterns, you'll get an error message.</span></span> <span data-ttu-id="bd61c-164">그러나 모델이 성공적으로 생성 된 경우에도 모델을 테스트 하 여 가정의 유효성을 검사 하는지 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd61c-164">However, even if a model was successfully created, you'll want to test the model to see if it validates your assumptions.</span></span> <span data-ttu-id="bd61c-165">정확도 차트와 같은 도구를 사용 하 여 [데이터 마이닝 추가 기능을 SQL Server &#40;&#41;](accuracy-chart-sql-server-data-mining-add-ins.md) 하거나 [교차 유효성 검사 &#40;SQL Server 데이터 마이닝 추가 기능&#41;](cross-validation-sql-server-data-mining-add-ins.md) 를 사용 하 여 모델 품질의 통계 측정값을 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd61c-165">You can use tools such as the [Accuracy Chart &#40;SQL Server Data Mining Add-ins&#41;](accuracy-chart-sql-server-data-mining-add-ins.md) or [Cross-Validation &#40;SQL Server Data Mining Add-ins&#41;](cross-validation-sql-server-data-mining-add-ins.md) to produce statistical measures of model quality.</span></span>  
  
 <span data-ttu-id="bd61c-166">첫 번째 모델의 결과를 평가할 때는 다음과 같은 질문을 스스로 해볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd61c-166">As you assess the results of your first model, ask yourself questions such as these:</span></span>  
  
-   <span data-ttu-id="bd61c-167">어떤 종류의 패턴이 발견되었습니까?</span><span class="sxs-lookup"><span data-stu-id="bd61c-167">What kinds of patterns were found?</span></span> <span data-ttu-id="bd61c-168">확률 및 지원 값은 무엇인가?</span><span class="sxs-lookup"><span data-stu-id="bd61c-168">What are the probabilities and support values?</span></span>  
  
-   <span data-ttu-id="bd61c-169">추세에 대한 추측이 맞았습니까? 아니면 놀라운 상관 관계가 있습니까?</span><span class="sxs-lookup"><span data-stu-id="bd61c-169">Were our guesses about trends correct, or were there surprising correlations?</span></span>  
  
-   <span data-ttu-id="bd61c-170">데이터를 충분히 수집했는가?</span><span class="sxs-lookup"><span data-stu-id="bd61c-170">Did we collect enough data?</span></span> <span data-ttu-id="bd61c-171">데이터를 묶음으로써 더 명확한 패턴을 얻을 수 있는가?</span><span class="sxs-lookup"><span data-stu-id="bd61c-171">Would binning the data produce clearer patterns?</span></span>  
  
-   <span data-ttu-id="bd61c-172">데이터 집합이 균형적인가?</span><span class="sxs-lookup"><span data-stu-id="bd61c-172">Is the data set balanced?</span></span> <span data-ttu-id="bd61c-173">교차 유효성 검사를 통해 데이터의 대표성을 테스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd61c-173">Cross-validation can test the representativeness of your data.</span></span>  
  
 [<span data-ttu-id="bd61c-174">Excel용 테이블 분석 도구</span><span class="sxs-lookup"><span data-stu-id="bd61c-174">Table Analysis Tools for Excel</span></span>](table-analysis-tools-for-excel.md)  
  
 [<span data-ttu-id="bd61c-175">Excel 용 데이터 마이닝 클라이언트 &#40;SQL Server 데이터 마이닝 추가 기능&#41;</span><span class="sxs-lookup"><span data-stu-id="bd61c-175">Data Mining Client for Excel &#40;SQL Server Data Mining Add-ins&#41;</span></span>](data-mining-client-for-excel-sql-server-data-mining-add-ins.md)  
  
 [<span data-ttu-id="bd61c-176">모델 선택</span><span class="sxs-lookup"><span data-stu-id="bd61c-176">Choosing a Model</span></span>](choosing-a-model.md)  
  
## <a name="explore-and-refine"></a><span data-ttu-id="bd61c-177">탐색 및 수정</span><span class="sxs-lookup"><span data-stu-id="bd61c-177">Explore and Refine</span></span>  
 <span data-ttu-id="bd61c-178">모델이 유효한 것으로 파악되면 이 모델을 예측, 제안, 통찰 얻기 또는 비즈니스 전략 계획에 활용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd61c-178">If the model appears to be valid, you can use the model for prediction, recommendation, deriving insights, or planning business strategies..</span></span>  
  
-   <span data-ttu-id="bd61c-179">Excel용 데이터 마이닝 클라이언트에서 데이터 마이닝 브라우저를 사용해서 모델을 탐색하고 모델과 상호 작용합니다.</span><span class="sxs-lookup"><span data-stu-id="bd61c-179">Use the data mining browser in the Data Mining Client for Excel to explore and interact with the model.</span></span>  
  
-   <span data-ttu-id="bd61c-180">Excel을 사용해서 결과를 다시 정렬하고 필터링합니다.</span><span class="sxs-lookup"><span data-stu-id="bd61c-180">Use Excel to rearrange and filter the results.</span></span>  
  
-   <span data-ttu-id="bd61c-181">Visio를 사용해서 프레젠테이션을 작성하고 데이터에서 발견된 관계를 강조 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="bd61c-181">Use Visio to create presentations and highlight the relationships found in the data.</span></span>  
  
 <span data-ttu-id="bd61c-182">대개 분석의 첫 번째 결과를 보면 분석을 개선할 여러 가지 방법이나 새 데이터를 구해야 한다는 사실을 알게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bd61c-182">Often, the first result of analysis is that you see ways to improve the analysis, or realize that you need to get new and better data.</span></span> <span data-ttu-id="bd61c-183">Excel용 데이터 마이닝 추가 기능을 사용하여 만든 모델을 Analysis Service 인스턴스에 저장할 수 있으므로 간편하게 새 데이터로 모델을 업데이트할 수 있으며 성공적인 모델을 수정하여 재사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd61c-183">Because the models that you create using the Data Mining Add-ins for Excel can be saved to an instance of Analysis Service, it is relatively easy to update the model with new data, and continue to refine and re-use successful models.</span></span>  
  
 <span data-ttu-id="bd61c-184">데이터 마이닝 모델의 중요한 용도는 예측 및 권장 사항을 만드는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="bd61c-184">An important use of data mining models is to create predictions and recommendations.</span></span> <span data-ttu-id="bd61c-185">Excel용 데이터 마이닝 추가 기능에는 발견한 정보를 실행 가능한 결과로 바꾸기 위해 복잡한 예측 쿼리도 쉽게 생성할 수 있는 도구가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd61c-185">The Data Mining Add-ins for Excel includes tools that make it easy to generate even complex prediction queries, for converting insights into actionable results.</span></span> <span data-ttu-id="bd61c-186">이러한 도구는 모두 Excel과 완벽하게 통합되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd61c-186">All of these tools are fully integrated with Excel.</span></span>  
  
 [<span data-ttu-id="bd61c-187">Office&#41;용 데이터 마이닝 추가 기능 &#40;모델 보기</span><span class="sxs-lookup"><span data-stu-id="bd61c-187">Viewing Models &#40;Data Mining Add-ins for Office&#41;</span></span>](viewing-models-data-mining-add-ins-for-office.md)  
  
 [<span data-ttu-id="bd61c-188">Excel 용 데이터 마이닝 추가 기능에 대 한 예측 &#40;모델 유효성 검사 및 모델 사용&#41;</span><span class="sxs-lookup"><span data-stu-id="bd61c-188">Validating Models and Using Models for Prediction &#40;Data Mining Add-ins for Excel&#41;</span></span>](validating-models-and-using-models-for-prediction-data-mining-add-ins-for-excel.md)  
  
## <a name="see-also"></a><span data-ttu-id="bd61c-189">참고 항목</span><span class="sxs-lookup"><span data-stu-id="bd61c-189">See Also</span></span>  
 <span data-ttu-id="bd61c-190">[Office 용 데이터 마이닝 추가 기능에 포함 된 내용](what-s-included-in-the-data-mining-add-ins-for-office.md) </span><span class="sxs-lookup"><span data-stu-id="bd61c-190">[What's Included in the Data Mining Add-Ins for Office](what-s-included-in-the-data-mining-add-ins-for-office.md) </span></span>  
 [<span data-ttu-id="bd61c-191">Excel 용 데이터 마이닝 추가 기능에 대 한 기술 참조 &#40;&#41;</span><span class="sxs-lookup"><span data-stu-id="bd61c-191">Technical Reference &#40;Data Mining Add-ins for Excel&#41;</span></span>](technical-reference-data-mining-add-ins-for-excel.md)  
  
  
