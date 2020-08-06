---
title: '6 단원: 예측 만들기 및 작업 (기본 데이터 마이닝 자습서) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: b213cb58-2c40-4c89-b08b-d3c36a4afad3
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: d0a8bfdf83e96622a19ac72490e8602d12afc9df
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648708"
---
# <a name="lesson-6-creating-and-working-with-predictions-basic-data-mining-tutorial"></a><span data-ttu-id="339e9-102">6단원: 예측 만들기 및 작업(기본 데이터 마이닝 자습서)</span><span class="sxs-lookup"><span data-stu-id="339e9-102">Lesson 6: Creating and Working with Predictions (Basic Data Mining Tutorial)</span></span>
  <span data-ttu-id="339e9-103">만든 데이터 마이닝 모델을 학습, 테스트 및 탐색했습니다.</span><span class="sxs-lookup"><span data-stu-id="339e9-103">You have trained, tested, and explored the data mining models you created.</span></span> <span data-ttu-id="339e9-104">이제 모델을 사용하여 새로운 타겟 메일링 캠페인에 응답할 가능성이 가장 높은 사람을 식별할 준비가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="339e9-104">Now you are ready to use the models to identify the people most likely to respond to the new targeted mailing campaign.</span></span>  
  
 <span data-ttu-id="339e9-105">이 단원에서는 자전거를 구매할 가능성이 가장 높은 고객을 예측하는 쿼리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="339e9-105">In this lesson you will create a query to predict which customers are most likely to purchase a bike.</span></span> <span data-ttu-id="339e9-106">또한 마케팅 부서에서 예측을 사용할지 여부를 결정할 수 있도록 예측의 정확성에 대한 *확률* 을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="339e9-106">You will also retrieve the *probability* that the prediction is correct, so the marketing department can decide whether to you can decide whether to use the prediction or not.</span></span>  
  
 <span data-ttu-id="339e9-107">자전거를 구매할 확률이 높은 고객을 식별하면 마이닝 모델에 있는 사례의 세부 정보 및 이러한 고객에 대한 연락처 정보로 드릴스루합니다.</span><span class="sxs-lookup"><span data-stu-id="339e9-107">Once you have identified customers with a high probability of purchasing a bike, you will drill through to the details of the cases in the mining model to retrieve names and contact information for these customers.</span></span>  
  
 <span data-ttu-id="339e9-108">이 단원에서는 다음 항목을 다룹니다.</span><span class="sxs-lookup"><span data-stu-id="339e9-108">This lesson contains the following topics:</span></span>  
  
 [<span data-ttu-id="339e9-109">예측 만들기&#40;기본 데이터 마이닝 자습서&#41;</span><span class="sxs-lookup"><span data-stu-id="339e9-109">Creating Predictions &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/creating-predictions-basic-data-mining-tutorial.md)  
  
 [<span data-ttu-id="339e9-110">구조 데이터에 드릴스루 사용 &#40;기본 데이터 마이닝 자습서&#41;</span><span class="sxs-lookup"><span data-stu-id="339e9-110">Using Drillthrough on Structure Data &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/using-drillthrough-on-structure-data-basic-data-mining-tutorial.md)  
  
## <a name="next-lesson"></a><span data-ttu-id="339e9-111">다음 단원</span><span class="sxs-lookup"><span data-stu-id="339e9-111">Next Lesson</span></span>  
 [<span data-ttu-id="339e9-112">Analysis Services 데이터 마이닝&#41;&#40;중급 데이터 마이닝 자습서</span><span class="sxs-lookup"><span data-stu-id="339e9-112">Intermediate Data Mining Tutorial &#40;Analysis Services - Data Mining&#41;</span></span>](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md)  
  
## <a name="previous-lesson"></a><span data-ttu-id="339e9-113">이전 단원</span><span class="sxs-lookup"><span data-stu-id="339e9-113">Previous Lesson</span></span>  
 [<span data-ttu-id="339e9-114">5 단원: 모델 테스트 &#40;기본 데이터 마이닝 자습서&#41;</span><span class="sxs-lookup"><span data-stu-id="339e9-114">Lesson 5: Testing Models &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-5-testing-models-basic-data-mining-tutorial.md)  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="339e9-115">단원의 다음 태스크</span><span class="sxs-lookup"><span data-stu-id="339e9-115">Next Task in Lesson</span></span>  
 [<span data-ttu-id="339e9-116">예측 만들기&#40;기본 데이터 마이닝 자습서&#41;</span><span class="sxs-lookup"><span data-stu-id="339e9-116">Creating Predictions &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/creating-predictions-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="339e9-117">참고 항목</span><span class="sxs-lookup"><span data-stu-id="339e9-117">See Also</span></span>  
 <span data-ttu-id="339e9-118">[의사 결정 트리 모델에 대 한 마이닝 모델 콘텐츠 &#40;Analysis Services 데이터 마이닝&#41;](../../2014/analysis-services/data-mining/mining-model-content-for-decision-tree-models-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="339e9-118">[Mining Model Content for Decision Tree Models &#40;Analysis Services - Data Mining&#41;](../../2014/analysis-services/data-mining/mining-model-content-for-decision-tree-models-analysis-services-data-mining.md) </span></span>  
 [<span data-ttu-id="339e9-119">예측 쿼리 작성기를 사용하여 예측 쿼리 만들기</span><span class="sxs-lookup"><span data-stu-id="339e9-119">Create a Prediction Query Using the Prediction Query Builder</span></span>](../../2014/analysis-services/data-mining/create-a-prediction-query-using-the-prediction-query-builder.md)  
  
  
