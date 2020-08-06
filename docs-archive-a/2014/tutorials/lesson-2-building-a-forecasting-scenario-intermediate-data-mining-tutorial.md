---
title: '2 단원: 예측 시나리오 구축 (중급 데이터 마이닝 자습서) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- time series [Analysis Services]
- data mining [Analysis Services], tutorials
- tutorials [Data Mining]
ms.assetid: 9a988156-c900-4c22-97fa-f6b0c1aea9e2
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: c81d5846df0a37c2b4182cb92fea86ce6f3417a7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639183"
---
# <a name="lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial"></a><span data-ttu-id="701ef-102">2단원: 예측 시나리오 구축(중급 데이터 마이닝 자습서)</span><span class="sxs-lookup"><span data-stu-id="701ef-102">Lesson 2: Building a Forecasting Scenario (Intermediate Data Mining Tutorial)</span></span>
  <span data-ttu-id="701ef-103">[!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)]의 판매 분석가가 제품의 내년 판매액을 예측해 달라는 요청을 받았습니다.</span><span class="sxs-lookup"><span data-stu-id="701ef-103">As the sales analyst for [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)], you have been asked to forecast the sales of products for the next year.</span></span> <span data-ttu-id="701ef-104">특히 지역 및 제품 라인별 예측을 비교해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="701ef-104">In particular, you have been asked to compare forecasts for the different regions and product lines.</span></span> <span data-ttu-id="701ef-105">또한 시간에 따라 여러 제품의 판매 방식이 달라지는지 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="701ef-105">Additionally, you have been asked to determine whether sales of different products vary depending on the time of the year.</span></span>  
  
 <span data-ttu-id="701ef-106">요청된 정보를 찾기 위해 이 단원에서 월별 수준으로 회사의 판매 데이터를 요약하고 판매 수치를 유럽, 북아메리카 및 태평양 세 지역으로 요약합니다.</span><span class="sxs-lookup"><span data-stu-id="701ef-106">To find the requested information, in this lesson you will summarize the company's sales data at the monthly level, and you will also summarize sales figures by three regions: Europe, North America, and the Pacific.</span></span>  
  
 <span data-ttu-id="701ef-107">이 단원의 태스크를 완료하면 다음 질문에 대답할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="701ef-107">After you complete the tasks in this lesson, you will be able to answer the following questions:</span></span>  
  
-   <span data-ttu-id="701ef-108">시간에 따라 여러 자전거 모델의 판매가 어떻게 변경됩니까?</span><span class="sxs-lookup"><span data-stu-id="701ef-108">How do the sales of different bike models change over time?</span></span>  
  
-   <span data-ttu-id="701ef-109">세 지역의 판매 패턴 간에 차이가 있습니까?</span><span class="sxs-lookup"><span data-stu-id="701ef-109">Are there differences between the patterns for sales in the three regions?</span></span>  
  
-   <span data-ttu-id="701ef-110">최고 매출을 예측할 수 있습니까?</span><span class="sxs-lookup"><span data-stu-id="701ef-110">Can we forecast sales peaks?</span></span>  
  
 <span data-ttu-id="701ef-111">이 단원을 두 부분으로 완료할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="701ef-111">The lesson can be completed in two parts:</span></span>  
  
-   <span data-ttu-id="701ef-112">1부에서는 시계열 모델을 만들고 사용하는 방법에 대한 기본 사항을 소개합니다.</span><span class="sxs-lookup"><span data-stu-id="701ef-112">Part One introduces the basics of how to create and use a time series model.</span></span>  
  
-   <span data-ttu-id="701ef-113">2부에서는 모든 지역을 기반으로 일반 시계열 모델을 만드는 과정을 안내합니다.</span><span class="sxs-lookup"><span data-stu-id="701ef-113">Part Two walks you through creation of a general time series model, based on all regions.</span></span> <span data-ttu-id="701ef-114">이 일반 모델을 *교차 예측*에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="701ef-114">You can use this general model for *cross-prediction*.</span></span>  
  
 <span data-ttu-id="701ef-115">아래에 나열 된이 단원의 태스크를 완료 하려면 [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] [1 단원: 중급 데이터 마이닝 솔루션 &#40;중급 데이터 마이닝 자습서&#41;](../../2014/tutorials/lesson-1-create-solution-intermediate-data-mining-tutorial.md)에서 만든 데이터 원본을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="701ef-115">To complete the tasks in this lesson, which are listed below, you will use the [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] data source that you created in [Lesson 1: Creating the Intermediate Data Mining Solution &#40;Intermediate Data Mining Tutorial&#41;](../../2014/tutorials/lesson-1-create-solution-intermediate-data-mining-tutorial.md).</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="701ef-116">[!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] 예제 데이터베이스에서의 날짜가 이 릴리스에 맞게 업데이트되었습니다.</span><span class="sxs-lookup"><span data-stu-id="701ef-116">The dates in the [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] sample database have been updated for this release.</span></span> <span data-ttu-id="701ef-117">이전 버전의 [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)]를 사용하는 경우 다음 단계에 따라 모델을 작성할 수 있지만 나타나는 결과가 달라질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="701ef-117">If you use an earlier version of [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)], you can build the model following these steps, but you might see different results.</span></span>  
  
 <span data-ttu-id="701ef-118">**간단한 예측 모델 만들기**</span><span class="sxs-lookup"><span data-stu-id="701ef-118">**Creating a Simple Forecasting Model**</span></span>  
  
-   [<span data-ttu-id="701ef-119">예측을 위한 데이터 원본 뷰 추가 &#40;중급 데이터 마이닝 자습서&#41;</span><span class="sxs-lookup"><span data-stu-id="701ef-119">Adding a Data Source View for Forecasting &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/adding-a-data-source-view-for-forecasting-intermediate-data-mining-tutorial.md)  
  
-   [<span data-ttu-id="701ef-120">&#40;중급 데이터 마이닝 자습서&#41;예측 구조 및 모델 만들기</span><span class="sxs-lookup"><span data-stu-id="701ef-120">Creating a Forecasting Structure and Model &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/creating-a-forecasting-structure-and-model-intermediate-data-mining-tutorial.md)  
  
-   [<span data-ttu-id="701ef-121">&#40;중급 데이터 마이닝 자습서&#41;예측 구조 수정</span><span class="sxs-lookup"><span data-stu-id="701ef-121">Modifying the Forecasting Structure &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/modifying-the-forecasting-structure-intermediate-data-mining-tutorial.md)  
  
-   [<span data-ttu-id="701ef-122">&#40;중급 데이터 마이닝 자습서를 통해 예측 모델 사용자 지정 및 처리&#41;</span><span class="sxs-lookup"><span data-stu-id="701ef-122">Customizing and Processing the Forecasting Model &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/customize-process-forecasting-model-intermediate-data-mining-tutorial.md)  
  
-   [<span data-ttu-id="701ef-123">예측 모델 탐색 &#40;중급 데이터 마이닝 자습서&#41;</span><span class="sxs-lookup"><span data-stu-id="701ef-123">Exploring the Forecasting Model &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/exploring-the-forecasting-model-intermediate-data-mining-tutorial.md)  
  
-   [<span data-ttu-id="701ef-124">&#40;중급 데이터 마이닝 자습서&#41;시계열 예측 만들기</span><span class="sxs-lookup"><span data-stu-id="701ef-124">Creating Time Series Predictions &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/creating-time-series-predictions-intermediate-data-mining-tutorial.md)  
  
 <span data-ttu-id="701ef-125">**교차 예측을 위한 일반 예측 모델 만들기**</span><span class="sxs-lookup"><span data-stu-id="701ef-125">**Creating a General Forecasting Model for Cross-Prediction**</span></span>  
  
-   [<span data-ttu-id="701ef-126">고급 시계열 예측 &#40;중급 데이터 마이닝 자습서&#41;</span><span class="sxs-lookup"><span data-stu-id="701ef-126">Advanced Time Series Predictions &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/advanced-time-series-predictions-intermediate-data-mining-tutorial.md)  
  
-   [<span data-ttu-id="701ef-127">업데이트 된 데이터를 사용한 시계열 예측 &#40;중급 데이터 마이닝 자습서&#41;</span><span class="sxs-lookup"><span data-stu-id="701ef-127">Time Series Predictions using Updated Data &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/time-series-predictions-using-updated-data-intermediate-data-mining-tutorial.md)  
  
-   [<span data-ttu-id="701ef-128">대체 데이터를 사용한 시계열 예측 &#40;중급 데이터 마이닝 자습서&#41;</span><span class="sxs-lookup"><span data-stu-id="701ef-128">Time Series Predictions using Replacement Data &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/time-series-predictions-replacement-data-intermediate-data-mining.md)  
  
-   [<span data-ttu-id="701ef-129">예측 모델에 대 한 예측 비교 &#40;중급 데이터 마이닝 자습서&#41;</span><span class="sxs-lookup"><span data-stu-id="701ef-129">Comparing Predictions for Forecasting Models &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/comparing-predictions-for-forecasting-models-intermediate-data-mining-tutorial.md)  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="701ef-130">단원의 다음 태스크</span><span class="sxs-lookup"><span data-stu-id="701ef-130">Next Task in Lesson</span></span>  
 [<span data-ttu-id="701ef-131">예측을 위한 데이터 원본 뷰 추가 &#40;중급 데이터 마이닝 자습서&#41;</span><span class="sxs-lookup"><span data-stu-id="701ef-131">Adding a Data Source View for Forecasting &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/adding-a-data-source-view-for-forecasting-intermediate-data-mining-tutorial.md)  
  
 [<span data-ttu-id="701ef-132">시계열 모델에 대 한 요구 사항 이해 &#40;중급 데이터 마이닝 자습서&#41;</span><span class="sxs-lookup"><span data-stu-id="701ef-132">Understanding the Requirements for a Time Series Model &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/time-series-model-requirements-intermediate-data-mining-tutorial.md)  
  
## <a name="all-lessons"></a><span data-ttu-id="701ef-133">모든 단원</span><span class="sxs-lookup"><span data-stu-id="701ef-133">All Lessons</span></span>  
 [<span data-ttu-id="701ef-134">1 단원: 중급 데이터 마이닝 자습서를 &#40;중급 데이터 마이닝 솔루션 만들기&#41;</span><span class="sxs-lookup"><span data-stu-id="701ef-134">Lesson 1: Creating the Intermediate Data Mining Solution &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-1-create-solution-intermediate-data-mining-tutorial.md)  
  
 <span data-ttu-id="701ef-135">2단원: 예측 시나리오 구축(중급 데이터 마이닝 자습서)</span><span class="sxs-lookup"><span data-stu-id="701ef-135">Lesson 2: Forecasting Scenario (Intermediate Data Mining Tutorial)</span></span>  
  
 [<span data-ttu-id="701ef-136">3단원: 시장 바구니 시나리오 구축&#40;중급 데이터 마이닝 자습서&#41;</span><span class="sxs-lookup"><span data-stu-id="701ef-136">Lesson 3: Building a Market Basket Scenario &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial.md)  
  
 [<span data-ttu-id="701ef-137">4 단원: 중간 데이터 마이닝 자습서 &#40;시퀀스 클러스터링 시나리오 빌드&#41;</span><span class="sxs-lookup"><span data-stu-id="701ef-137">Lesson 4: Building a Sequence Clustering Scenario &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-4-build-sequence-clustering-scenario-intermediate-data-mining.md)  
  
 [<span data-ttu-id="701ef-138">5단원: 신경망 및 로지스틱 회귀 모델 작성&#40;중급 데이터 마이닝 자습서&#41;</span><span class="sxs-lookup"><span data-stu-id="701ef-138">Lesson 5: Building Neural Network and Logistic Regression Models &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-5-build-models-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="701ef-139">참고 항목</span><span class="sxs-lookup"><span data-stu-id="701ef-139">See Also</span></span>  
 <span data-ttu-id="701ef-140">[기본 데이터 마이닝 자습서](../../2014/tutorials/basic-data-mining-tutorial.md) </span><span class="sxs-lookup"><span data-stu-id="701ef-140">[Basic Data Mining Tutorial](../../2014/tutorials/basic-data-mining-tutorial.md) </span></span>  
 <span data-ttu-id="701ef-141">[Analysis Services 데이터 마이닝&#41;&#40;중급 데이터 마이닝 자습서](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="701ef-141">[Intermediate Data Mining Tutorial &#40;Analysis Services - Data Mining&#41;](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md) </span></span>  
 [<span data-ttu-id="701ef-142">Microsoft Time Series 알고리즘</span><span class="sxs-lookup"><span data-stu-id="701ef-142">Microsoft Time Series Algorithm</span></span>](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm.md)  
  
  
