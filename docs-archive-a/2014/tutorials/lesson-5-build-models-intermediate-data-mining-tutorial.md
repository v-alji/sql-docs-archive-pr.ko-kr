---
title: '5 단원: 신경망 및 로지스틱 회귀 모델 작성 (중급 데이터 마이닝 자습서) | Microsoft Docs'
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- logistic regression [Analysis Services]
- data mining [Analysis Services], tutorials
- neural networks
- tutorials [Data Mining]
- neural network model [Analysis Services]
ms.assetid: 42c3701a-1fd2-44ff-b7de-377345bbbd6b
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: a8c9fcf0380582f15fa2bf30d6fdeb97bb2ab1fe
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649862"
---
# <a name="lesson-5-building-neural-network-and-logistic-regression-models-intermediate-data-mining-tutorial"></a><span data-ttu-id="a37ff-102">5단원: 신경망 및 로지스틱 회귀 모델 작성(중급 데이터 마이닝 자습서)</span><span class="sxs-lookup"><span data-stu-id="a37ff-102">Lesson 5: Building Neural Network and Logistic Regression Models (Intermediate Data Mining Tutorial)</span></span>
  
  
 <span data-ttu-id="a37ff-103">[!INCLUDE[ssSampleDBCoShort](../includes/sssampledbcoshort-md.md)] 의 운영 부서가 콜 센터에서 고객 만족도를 향상시키는 프로젝트를 수행하고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a37ff-103">The Operations department of [!INCLUDE[ssSampleDBCoShort](../includes/sssampledbcoshort-md.md)] is engaged in a project to improve customer satisfaction with their call center.</span></span> <span data-ttu-id="a37ff-104">이 부서에서는 콜 센터를 관리하고 콜 센터 효율성에 대한 메트릭을 보고할 한 업체를 선정하고 여러분에게 이 업체가 제공한 일부 예비 정보를 분석하는 업무를 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="a37ff-104">They hired a vendor to manage the call center and to report metrics on call center effectiveness, and have asked you to analyze some preliminary data provided by the vendor.</span></span> <span data-ttu-id="a37ff-105">이 부서에서는 업체가 보고한 정보에 관심이 갈 만한 내용이 있는지 알고 싶습니다.</span><span class="sxs-lookup"><span data-stu-id="a37ff-105">They want to know if there are any interesting findings.</span></span> <span data-ttu-id="a37ff-106">특히 이 데이터에서 직원 배치의 문제점 또는 고객 만족도를 개선하는 방법을 제안하는지 알고 싶습니다.</span><span class="sxs-lookup"><span data-stu-id="a37ff-106">In particular, they would like to know if the data suggests any staffing problems with staffing or ways to improve customer satisfaction.</span></span>  
  
 <span data-ttu-id="a37ff-107">데이터 집합은 작으며 30일간의 콜 센터 운영 기간만 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="a37ff-107">The data set is small and covers only a 30-day period in the operation of the call center.</span></span> <span data-ttu-id="a37ff-108">데이터는 각 교대조의 신규 및 경력 전화 상담원 수, 수신 전화 수, 주문 수는 물론 해결해야 할 문제 및 고객의 평균 통화 응답 대기 시간을 추적합니다.</span><span class="sxs-lookup"><span data-stu-id="a37ff-108">The data tracks the number of new and experienced operators in each shift, the number of incoming calls, the number of orders as well as issues that must be resolved, and the average time a customer waits for someone to respond to a call.</span></span> <span data-ttu-id="a37ff-109">또한 데이터에는 고객 불만 지표인 *중단율*을 기반으로 한 서비스 품질 메트릭도 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="a37ff-109">The data also includes a service quality metric based on *abandon rate*, which is an indicator of customer frustration.</span></span>  
  
 <span data-ttu-id="a37ff-110">데이터가 나타내는 내용에 대해 사전에 어떠한 예측도 하지 않았으므로 신경망 모델을 사용하여 가능한 상관 관계를 탐색하기로 결정했습니다.</span><span class="sxs-lookup"><span data-stu-id="a37ff-110">Because you do not have any prior expectations about what the data will show, you decide to use a neural network model to explore possible correlations.</span></span> <span data-ttu-id="a37ff-111">신경망 모델은 많은 입력과 출력 간의 복잡한 관계를 분석하기 때문에 자주 탐색에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="a37ff-111">Neural network models are often used for exploration because they can analyze complex relationships between many inputs and outputs.</span></span>  
  
## <a name="what-you-will-learn"></a><span data-ttu-id="a37ff-112">학습 내용</span><span class="sxs-lookup"><span data-stu-id="a37ff-112">What You Will Learn</span></span>  
 <span data-ttu-id="a37ff-113">이 단원에서는 신경망 알고리즘을 사용하여 여러분과 운영 팀이 데이터의 추세를 이해하는 데 사용할 수 있는 모델을 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="a37ff-113">In this lesson, you will use the neural network algorithm to build a model that you and the Operations team can use to understand the trends in the data.</span></span> <span data-ttu-id="a37ff-114">이 단원을 통해 다음 질문에 답할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a37ff-114">As part of this lesson, you will try to answer the following questions:</span></span>  
  
-   <span data-ttu-id="a37ff-115">고객 만족에 영향을 주는 요인은 무엇입니까?</span><span class="sxs-lookup"><span data-stu-id="a37ff-115">What factors affect customer satisfaction?</span></span>  
  
-   <span data-ttu-id="a37ff-116">콜 센터가 서비스 품질을 개선하기 위해 할 수 있는 일은 무엇입니까?</span><span class="sxs-lookup"><span data-stu-id="a37ff-116">What can the call center do to improve service quality?</span></span>  
  
 <span data-ttu-id="a37ff-117">결과에 따라 예측에 사용할 수 있는 로지스틱 회귀 모델을 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="a37ff-117">Based on the results, you will then build a logistic regression model that you can use for predictions.</span></span> <span data-ttu-id="a37ff-118">운영 팀에서는 예측을 통해 호출 센터 운영을 보다 쉽게 계획할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a37ff-118">The predictions will be used by the Operations team as an aid in planning call center operation.</span></span>  
  
 <span data-ttu-id="a37ff-119">이 단원에서는 다음 항목을 다룹니다.</span><span class="sxs-lookup"><span data-stu-id="a37ff-119">This lesson contains the following topics:</span></span>  
  
-   [<span data-ttu-id="a37ff-120">중급 데이터 마이닝 자습서를 &#40;콜 센터 데이터에 대 한 데이터 원본 뷰 추가&#41;</span><span class="sxs-lookup"><span data-stu-id="a37ff-120">Adding a Data Source View for Call Center Data &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/add-data-source-view-call-center-data-intermediate-data-mining.md)  
  
-   [<span data-ttu-id="a37ff-121">&#40;중급 데이터 마이닝 자습서&#41;신경망 구조 및 모델 만들기</span><span class="sxs-lookup"><span data-stu-id="a37ff-121">Creating a Neural Network Structure and Model &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/creating-a-neural-network-structure-and-model-intermediate-data-mining-tutorial.md)  
  
-   [<span data-ttu-id="a37ff-122">중급 데이터 마이닝 자습서 &#40;콜 센터 모델 탐색&#41;</span><span class="sxs-lookup"><span data-stu-id="a37ff-122">Exploring the Call Center Model &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/exploring-the-call-center-model-intermediate-data-mining-tutorial.md)  
  
-   [<span data-ttu-id="a37ff-123">로지스틱 회귀 모델을 콜 센터 구조에 추가 &#40;중급 데이터 마이닝 자습서&#41;</span><span class="sxs-lookup"><span data-stu-id="a37ff-123">Adding a Logistic Regression Model to the Call Center Structure &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/add-logistic-regression-model-to-call-center-intermediate-data-mining.md)  
  
-   [<span data-ttu-id="a37ff-124">중급 데이터 마이닝 자습서 &#40;콜 센터 모델에 대 한 예측 만들기&#41;</span><span class="sxs-lookup"><span data-stu-id="a37ff-124">Creating Predictions for the Call Center Models &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/create-predictions-call-center-models-intermediate-data-mining-tutorial.md)  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="a37ff-125">단원의 다음 태스크</span><span class="sxs-lookup"><span data-stu-id="a37ff-125">Next Task in Lesson</span></span>  
 [<span data-ttu-id="a37ff-126">중급 데이터 마이닝 자습서를 &#40;콜 센터 데이터에 대 한 데이터 원본 뷰 추가&#41;</span><span class="sxs-lookup"><span data-stu-id="a37ff-126">Adding a Data Source View for Call Center Data &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/add-data-source-view-call-center-data-intermediate-data-mining.md)  
  
## <a name="all-lessons"></a><span data-ttu-id="a37ff-127">모든 단원</span><span class="sxs-lookup"><span data-stu-id="a37ff-127">All Lessons</span></span>  
 [<span data-ttu-id="a37ff-128">1 단원: 중급 데이터 마이닝 자습서를 &#40;중급 데이터 마이닝 솔루션 만들기&#41;</span><span class="sxs-lookup"><span data-stu-id="a37ff-128">Lesson 1: Creating the Intermediate Data Mining Solution &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-1-create-solution-intermediate-data-mining-tutorial.md)  
  
 [<span data-ttu-id="a37ff-129">2 단원: 중급 데이터 마이닝 자습서 &#40;예측 시나리오 구축&#41;</span><span class="sxs-lookup"><span data-stu-id="a37ff-129">Lesson 2: Building a Forecasting Scenario &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md)  
  
 [<span data-ttu-id="a37ff-130">3단원: 시장 바구니 시나리오 구축&#40;중급 데이터 마이닝 자습서&#41;</span><span class="sxs-lookup"><span data-stu-id="a37ff-130">Lesson 3: Building a Market Basket Scenario &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial.md)  
  
 [<span data-ttu-id="a37ff-131">4 단원: 중간 데이터 마이닝 자습서 &#40;시퀀스 클러스터링 시나리오 빌드&#41;</span><span class="sxs-lookup"><span data-stu-id="a37ff-131">Lesson 4: Building a Sequence Clustering Scenario &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-4-build-sequence-clustering-scenario-intermediate-data-mining.md)  
  
 <span data-ttu-id="a37ff-132">5단원: 신경망 및 로지스틱 회귀 시나리오(중급 데이터 마이닝 자습서)</span><span class="sxs-lookup"><span data-stu-id="a37ff-132">Lesson 5: Neural Network and Logistic Regression Scenario (Intermediate Data Mining Tutorial)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a37ff-133">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a37ff-133">See Also</span></span>  
 <span data-ttu-id="a37ff-134">[기본 데이터 마이닝 자습서](../../2014/tutorials/basic-data-mining-tutorial.md) </span><span class="sxs-lookup"><span data-stu-id="a37ff-134">[Basic Data Mining Tutorial](../../2014/tutorials/basic-data-mining-tutorial.md) </span></span>  
 [<span data-ttu-id="a37ff-135">Analysis Services 데이터 마이닝&#41;&#40;중급 데이터 마이닝 자습서</span><span class="sxs-lookup"><span data-stu-id="a37ff-135">Intermediate Data Mining Tutorial &#40;Analysis Services - Data Mining&#41;</span></span>](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md)  
  
  
