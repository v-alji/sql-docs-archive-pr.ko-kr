---
title: '3 단원: 시장 바구니 시나리오 구축 (중급 데이터 마이닝 자습서) | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data mining [Analysis Services], tutorials
- association algorithms [Analysis Services]
- nested tables
- tutorials [Data Mining]
ms.assetid: 651eef38-772e-4d97-af51-075b1b27fc5a
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: a281aa62fbf08393c95f12ded9886ac212b3165f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735631"
---
# <a name="lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial"></a><span data-ttu-id="fbf01-102">3단원: 시장 바구니 시나리오 구축(중급 데이터 마이닝 자습서)</span><span class="sxs-lookup"><span data-stu-id="fbf01-102">Lesson 3: Building a Market Basket Scenario (Intermediate Data Mining Tutorial)</span></span>
  <span data-ttu-id="fbf01-103">[!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] 의 마케팅 부서에서 회사 웹 사이트를 개선하여 교차 판매 기회를 늘리고자 합니다.</span><span class="sxs-lookup"><span data-stu-id="fbf01-103">The marketing department of [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] wants to improve the company Web site to promote cross-selling.</span></span> <span data-ttu-id="fbf01-104">사이트 업데이트의 일부로 이 부서에서는 고객의 온라인 시장 바구니에 이미 있는 다른 제품을 기반으로 고객이 구매할 제품을 예측하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="fbf01-104">As part of the site update, they would like the ability to predict products that a customer might want to purchase, based on the other products that are already in the customer's online shopping basket.</span></span> <span data-ttu-id="fbf01-105">또한 구매될 가능성이 높은 항목이 함께 배열되도록 웹 사이트를 디자인하여 고객의 구매 행동을 더 잘 파악하고자 합니다.</span><span class="sxs-lookup"><span data-stu-id="fbf01-105">The marketing department also wants to understand customer purchasing behavior better, so that they can design the Web site so that the items that tend to be purchased together appear together.</span></span> <span data-ttu-id="fbf01-106">이 부서에서는 데이터 마이닝이 이러한 종류의 *시장 바구니 분석* 에 특히 유용하다는 것을 알게 되었으며 데이터 마이닝 모델 개발을 요구해 왔습니다.</span><span class="sxs-lookup"><span data-stu-id="fbf01-106">They have learned that data mining is especially useful for this kind of *market basket analysis* and have asked you to develop a data mining model.</span></span>  
  
 <span data-ttu-id="fbf01-107">이 단원의 태스크를 마치면 고객의 거래 내역에서 항목 그룹을 보여 주는 마이닝 모델이 마련됩니다.</span><span class="sxs-lookup"><span data-stu-id="fbf01-107">After you complete the tasks in this lesson, you will have a mining model that shows groups of items from historical customer transactions.</span></span> <span data-ttu-id="fbf01-108">또한 이 마이닝 모델을 사용하여 고객이 구매할 수 있는 추가 항목을 예측할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fbf01-108">Additionally, you can use the mining model to predict additional items that a customer may want to purchase.</span></span>  
  
 <span data-ttu-id="fbf01-109">이 단원의 태스크를 완료 하려면 [Analysis Services 데이터 마이닝&#41;&#40;중급 데이터 마이닝 자습서 ](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md)의 첫 번째 단원에서 만든 솔루션과 데이터 원본을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="fbf01-109">To complete the tasks in this lesson, you will use the solution and data source that you created in the first lesson of the [Intermediate Data Mining Tutorial &#40;Analysis Services - Data Mining&#41;](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md).</span></span> <span data-ttu-id="fbf01-110">고객 구매에 대한 중첩 테이블을 비롯하여 고객에 대한 테이블이 포함된 데이터 원본 뷰를 추가하여 이 솔루션을 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="fbf01-110">You will modify this solution by adding a data source view that contains tables about the customer, including a nested table of customer purchases.</span></span>  <span data-ttu-id="fbf01-111">그런 다음 시장 바구니 시나리오에 적합한 Microsoft 연결 규칙 알고리즘을 사용하는 마이닝 모델을 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="fbf01-111">You will then build a mining model that uses the Microsoft Association Rules algorithm, which is suited to market basket scenarios.</span></span>  
  
 <span data-ttu-id="fbf01-112">이 단원에서는 다음 항목을 다룹니다.</span><span class="sxs-lookup"><span data-stu-id="fbf01-112">This lesson contains the following topics:</span></span>  
  
-   [<span data-ttu-id="fbf01-113">중첩 테이블이 포함 된 데이터 원본 뷰 추가 &#40;중급 데이터 마이닝 자습서&#41;</span><span class="sxs-lookup"><span data-stu-id="fbf01-113">Adding a Data Source View with Nested Tables &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/adding-a-data-source-view-with-nested-tables-intermediate-data-mining-tutorial.md)  
  
-   [<span data-ttu-id="fbf01-114">&#40;중급 데이터 마이닝 자습서&#41;시장 바구니 구조 및 모델 만들기</span><span class="sxs-lookup"><span data-stu-id="fbf01-114">Creating a Market Basket Structure and Model &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/creating-a-market-basket-structure-and-model-intermediate-data-mining-tutorial.md)  
  
-   [<span data-ttu-id="fbf01-115">중급 데이터 마이닝 자습서 &#40;시장 바구니 모델 수정 및 처리&#41;</span><span class="sxs-lookup"><span data-stu-id="fbf01-115">Modifying and Processing the Market Basket Model &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/modify-process-market-basket-model-intermediate-data-mining-tutorial.md)  
  
-   [<span data-ttu-id="fbf01-116">시장 바구니 모델 탐색 &#40;중급 데이터 마이닝 자습서&#41;</span><span class="sxs-lookup"><span data-stu-id="fbf01-116">Exploring the Market Basket Models &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/exploring-the-market-basket-models-intermediate-data-mining-tutorial.md)  
  
-   [<span data-ttu-id="fbf01-117">마이닝 모델의 중첩 테이블 필터링 &#40;중급 데이터 마이닝 자습서&#41;</span><span class="sxs-lookup"><span data-stu-id="fbf01-117">Filtering a Nested Table in a Mining Model &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/filtering-a-nested-table-in-a-mining-model-intermediate-data-mining-tutorial.md)  
  
-   [<span data-ttu-id="fbf01-118">&#40;중급 데이터 마이닝 자습서의 연결 예측&#41;</span><span class="sxs-lookup"><span data-stu-id="fbf01-118">Predicting Associations &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/predicting-associations-intermediate-data-mining-tutorial.md)  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="fbf01-119">단원의 다음 태스크</span><span class="sxs-lookup"><span data-stu-id="fbf01-119">Next Task in Lesson</span></span>  
 [<span data-ttu-id="fbf01-120">중첩 테이블이 포함 된 데이터 원본 뷰 추가 &#40;중급 데이터 마이닝 자습서&#41;</span><span class="sxs-lookup"><span data-stu-id="fbf01-120">Adding a Data Source View with Nested Tables &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/adding-a-data-source-view-with-nested-tables-intermediate-data-mining-tutorial.md)  
  
## <a name="all-lessons"></a><span data-ttu-id="fbf01-121">모든 단원</span><span class="sxs-lookup"><span data-stu-id="fbf01-121">All Lessons</span></span>  
 [<span data-ttu-id="fbf01-122">1 단원: 중급 데이터 마이닝 자습서를 &#40;중급 데이터 마이닝 솔루션 만들기&#41;</span><span class="sxs-lookup"><span data-stu-id="fbf01-122">Lesson 1: Creating the Intermediate Data Mining Solution &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-1-create-solution-intermediate-data-mining-tutorial.md)  
  
 [<span data-ttu-id="fbf01-123">2 단원: 중급 데이터 마이닝 자습서 &#40;예측 시나리오 구축&#41;</span><span class="sxs-lookup"><span data-stu-id="fbf01-123">Lesson 2: Building a Forecasting Scenario &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md)  
  
 <span data-ttu-id="fbf01-124">3단원: 시장 바구니 시나리오(중급 데이터 마이닝 자습서)</span><span class="sxs-lookup"><span data-stu-id="fbf01-124">Lesson 3: Market Basket Scenario (Intermediate Data Mining Tutorial)</span></span>  
  
 [<span data-ttu-id="fbf01-125">4 단원: 중간 데이터 마이닝 자습서 &#40;시퀀스 클러스터링 시나리오 빌드&#41;</span><span class="sxs-lookup"><span data-stu-id="fbf01-125">Lesson 4: Building a Sequence Clustering Scenario &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-4-build-sequence-clustering-scenario-intermediate-data-mining.md)  
  
 [<span data-ttu-id="fbf01-126">5단원: 신경망 및 로지스틱 회귀 모델 작성&#40;중급 데이터 마이닝 자습서&#41;</span><span class="sxs-lookup"><span data-stu-id="fbf01-126">Lesson 5: Building Neural Network and Logistic Regression Models &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-5-build-models-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="fbf01-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="fbf01-127">See Also</span></span>  
 <span data-ttu-id="fbf01-128">[기본 데이터 마이닝 자습서](../../2014/tutorials/basic-data-mining-tutorial.md) </span><span class="sxs-lookup"><span data-stu-id="fbf01-128">[Basic Data Mining Tutorial](../../2014/tutorials/basic-data-mining-tutorial.md) </span></span>  
 <span data-ttu-id="fbf01-129">[2 단원: 중급 데이터 마이닝 자습서 &#40;예측 시나리오 구축&#41;](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md) </span><span class="sxs-lookup"><span data-stu-id="fbf01-129">[Lesson 2: Building a Forecasting Scenario &#40;Intermediate Data Mining Tutorial&#41;](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md) </span></span>  
 [<span data-ttu-id="fbf01-130">4 단원: 중간 데이터 마이닝 자습서 &#40;시퀀스 클러스터링 시나리오 빌드&#41;</span><span class="sxs-lookup"><span data-stu-id="fbf01-130">Lesson 4: Building a Sequence Clustering Scenario &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-4-build-sequence-clustering-scenario-intermediate-data-mining.md)  
  
  
