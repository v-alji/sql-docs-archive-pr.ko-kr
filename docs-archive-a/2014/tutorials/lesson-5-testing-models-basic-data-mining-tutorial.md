---
title: '5 단원: 모델 테스트 (기본 데이터 마이닝 자습서) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: e9a7ddcf-2b01-485f-bbb5-62638b303bc6
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: fcfd9a9e90d9c6800af4dfd1599bbdd62d9520ea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734687"
---
# <a name="lesson-5-testing-models-basic-data-mining-tutorial"></a><span data-ttu-id="71e78-102">5단원: 모델 테스트(기본 데이터 마이닝 자습서)</span><span class="sxs-lookup"><span data-stu-id="71e78-102">Lesson 5: Testing Models (Basic Data Mining Tutorial)</span></span>
  <span data-ttu-id="71e78-103">타겟 메일링 시나리오 학습 집합을 사용하여 모델을 처리했으므로 이제 학습 집합에 대해 모델을 테스트합니다.</span><span class="sxs-lookup"><span data-stu-id="71e78-103">Now that you have processed the model by using the targeted mailing scenario training set, you will test your models against the testing set.</span></span> <span data-ttu-id="71e78-104">유효성 검사는 데이터 마이닝 프로세스에서 중요한 단계입니다.</span><span class="sxs-lookup"><span data-stu-id="71e78-104">Validation is an important step in the data mining process.</span></span> <span data-ttu-id="71e78-105">타겟 메일링 마이닝 모델을 프로덕션 환경에 배포하기 전에 실제 데이터에 대한 타겟 메일링 마이닝 모델의 성능을 아는 것이 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="71e78-105">Knowing how well your targeted mailing mining models perform against real data is important before you deploy the models into a production environment.</span></span>  
  
 <span data-ttu-id="71e78-106">테스트 집합의 데이터에는 자전거 구매에 대한 알려진 값이 이미 포함되어 있으므로 모델의 예측이 올바른지 여부를 쉽게 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="71e78-106">Because the data in the testing set already contains known values for bike buying, it is easy to determine whether the model's predictions are correct.</span></span> <span data-ttu-id="71e78-107">[!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] 마케팅 부서에서는 최상의 성능을 제공하는 모델을 사용하여 타겟 메일링 캠페인을 받을 고객을 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="71e78-107">The model that performs the best will be used by the [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] marketing department to identify the customers for their targeted mailing campaign.</span></span>  
  
 <span data-ttu-id="71e78-108">이 단원에서는 다음과 같은 여러 방법을 사용하여 모델의 유효성을 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="71e78-108">In this lesson you will validate your models using multiple methods:</span></span>  
  
1.  <span data-ttu-id="71e78-109">테스트 집합에 대 한 예측을 수행 하 여 알려진 결과에 대 한 모델의 정확도를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="71e78-109">You'll make predictions against the testing set to see how accurate the model is on known results.</span></span> <span data-ttu-id="71e78-110">*리프트 차트* 를 사용 하 여 효과를 측정 합니다.</span><span class="sxs-lookup"><span data-stu-id="71e78-110">You'll use a *lift chart* to measure its effectiveness.</span></span>  
  
     [<span data-ttu-id="71e78-111">리프트 차트를 사용하여 정확도 테스트&#40;기본 데이터 마이닝 자습서&#41;</span><span class="sxs-lookup"><span data-stu-id="71e78-111">Testing Accuracy with Lift Charts &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/testing-accuracy-with-lift-charts-basic-data-mining-tutorial.md)  
  
2.  <span data-ttu-id="71e78-112">데이터의 필터링된 하위 집합에 대해 모델을 테스트합니다.</span><span class="sxs-lookup"><span data-stu-id="71e78-112">You will test your models on a filtered subset of the data.</span></span> <span data-ttu-id="71e78-113">동일한 리프트 차트에서 여러 모델을 비교할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="71e78-113">You can compare multiple models in the same lift chart.</span></span>  
  
     [<span data-ttu-id="71e78-114">기본 데이터 마이닝 자습서를 &#40;필터링 된 모델 테스트&#41;</span><span class="sxs-lookup"><span data-stu-id="71e78-114">Testing a Filtered Model &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/testing-a-filtered-model-basic-data-mining-tutorial.md)  
  
 <span data-ttu-id="71e78-115">일반적인 모델 유효성 검사에 대 한 자세한 내용은 [데이터 마이닝 개념](../../2014/analysis-services/data-mining/data-mining-concepts.md)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="71e78-115">For more information about how model validation in general, see [Data Mining Concepts](../../2014/analysis-services/data-mining/data-mining-concepts.md).</span></span>  
  
## <a name="first-task-in-lesson"></a><span data-ttu-id="71e78-116">단원의 첫 번째 태스크</span><span class="sxs-lookup"><span data-stu-id="71e78-116">First Task in Lesson</span></span>  
 [<span data-ttu-id="71e78-117">리프트 차트를 사용하여 정확도 테스트&#40;기본 데이터 마이닝 자습서&#41;</span><span class="sxs-lookup"><span data-stu-id="71e78-117">Testing Accuracy with Lift Charts &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/testing-accuracy-with-lift-charts-basic-data-mining-tutorial.md)  
  
## <a name="previous-lesson"></a><span data-ttu-id="71e78-118">이전 단원</span><span class="sxs-lookup"><span data-stu-id="71e78-118">Previous Lesson</span></span>  
 [<span data-ttu-id="71e78-119">4 단원: 기본 데이터 마이닝 자습서 &#40;대상 메일링 모델 탐색&#41;</span><span class="sxs-lookup"><span data-stu-id="71e78-119">Lesson 4: Exploring the Targeted Mailing Models &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-4-exploring-the-targeted-mailing-models-basic-data-mining-tutorial.md)  
  
## <a name="next-lesson"></a><span data-ttu-id="71e78-120">다음 단원</span><span class="sxs-lookup"><span data-stu-id="71e78-120">Next Lesson</span></span>  
 [<span data-ttu-id="71e78-121">6단원: 예측 만들기 및 작업&#40;기본 데이터 마이닝 자습서&#41;</span><span class="sxs-lookup"><span data-stu-id="71e78-121">Lesson 6: Creating and Working with Predictions &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-6-creating-and-working-with-predictions-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="71e78-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="71e78-122">See Also</span></span>  
 <span data-ttu-id="71e78-123">[리프트 차트 탭 &#40;마이닝 정확도 차트 뷰&#41;](../../2014/analysis-services/lift-chart-tab-mining-accuracy-chart-view.md) </span><span class="sxs-lookup"><span data-stu-id="71e78-123">[Lift Chart Tab &#40;Mining Accuracy Chart View&#41;](../../2014/analysis-services/lift-chart-tab-mining-accuracy-chart-view.md) </span></span>  
 <span data-ttu-id="71e78-124">[리프트 차트 &#40;Analysis Services-데이터 마이닝&#41;](../../2014/analysis-services/data-mining/lift-chart-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="71e78-124">[Lift Chart &#40;Analysis Services - Data Mining&#41;](../../2014/analysis-services/data-mining/lift-chart-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="71e78-125">[데이터 마이닝&#41;&#40;테스트 및 유효성 검사](../../2014/analysis-services/data-mining/testing-and-validation-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="71e78-125">[Testing and Validation &#40;Data Mining&#41;](../../2014/analysis-services/data-mining/testing-and-validation-data-mining.md) </span></span>  
 <span data-ttu-id="71e78-126">[마이닝 정확도 차트 뷰를 &#40;분류표 탭&#41;](../../2014/analysis-services/classification-matrix-tab-mining-accuracy-chart-view.md) </span><span class="sxs-lookup"><span data-stu-id="71e78-126">[Classification Matrix Tab &#40;Mining Accuracy Chart View&#41;](../../2014/analysis-services/classification-matrix-tab-mining-accuracy-chart-view.md) </span></span>  
 [<span data-ttu-id="71e78-127">분류표&#40;Analysis Services - 데이터 마이닝&#41;</span><span class="sxs-lookup"><span data-stu-id="71e78-127">Classification Matrix &#40;Analysis Services - Data Mining&#41;</span></span>](../../2014/analysis-services/data-mining/classification-matrix-analysis-services-data-mining.md)  
  
  
