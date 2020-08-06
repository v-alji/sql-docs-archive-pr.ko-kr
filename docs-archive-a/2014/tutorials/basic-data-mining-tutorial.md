---
title: 기본 데이터 마이닝 자습서 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- databases [Analysis Services], tutorials
- data mining [Analysis Services], tutorials
- tutorials [Data Mining]
ms.assetid: 6602edb6-d160-43fb-83c8-9df5dddfeb9c
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: ed557ffb5b8592be4d4375aca40e461d699d6ba7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735663"
---
# <a name="basic-data-mining-tutorial"></a><span data-ttu-id="9e9f6-102">기본 데이터 마이닝 자습서</span><span class="sxs-lookup"><span data-stu-id="9e9f6-102">Basic Data Mining Tutorial</span></span>
  <span data-ttu-id="9e9f6-103">[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 기본 데이터 마이닝 자습서를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e9f6-103">Welcome to the [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Basic Data Mining Tutorial.</span></span> [!INCLUDE[msCoName](../includes/msconame-md.md)]<span data-ttu-id="9e9f6-104">는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 데이터 마이닝 모델을 만들고 예측 하기 위한 통합 환경을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e9f6-104">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] provides an integrated environment for creating data mining models and making predictions.</span></span> <span data-ttu-id="9e9f6-105">이 자습서에서는 시스템 학습을 사용하여 고객 구매 행동을 분석하고 예측하는 타겟 메일링 캠페인 시나리오를 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="9e9f6-105">In this tutorial, you will complete a scenario for a targeted mailing campaign in which you use machine learning to analyze and predict customer purchasing behavior.</span></span> <span data-ttu-id="9e9f6-106">이 자습서에서는 가장 중요한 세 가지 데이터 마이닝 알고리즘인 클러스터링, 의사 결정 트리 및 Naive Bayes를 사용하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="9e9f6-106">The tutorial demonstrates how to use three of the most important data mining algorithms: clustering, decision trees, and Naive Bayes.</span></span> <span data-ttu-id="9e9f6-107">또한 마이닝 모델 뷰어를 사용 하 여 결과를 분석 하는 방법과에 포함 된 데이터 마이닝 도구를 사용 하 여 예측 및 정확도 차트를 만드는 방법도 알아봅니다 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="9e9f6-107">You will also learn how to analyze your findings using the mining model viewers, and to create predictions and accuracy charts using the data mining tools that are included in [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="9e9f6-108">모든 예에 가상 회사인 [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)]가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e9f6-108">The fictitious company, [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)], is used for all examples.</span></span>  
  
 <span data-ttu-id="9e9f6-109">데이터 마이닝 도구를 사용 하는 것이 어려우면 [Analysis Services 데이터 마이닝&#41;&#40;중급 데이터 마이닝 자습서 ](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md)도 완료 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="9e9f6-109">When you are comfortable using the data mining tools, we recommend that you also complete the [Intermediate Data Mining Tutorial &#40;Analysis Services - Data Mining&#41;](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md).</span></span> <span data-ttu-id="9e9f6-110">해당 단원에서는 예측, 시장 바구니 분석, 시계열, 연결 모델, 중첩 테이블 및 시퀀스 클러스터링을 사용하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="9e9f6-110">The lessons demonstrate how to use forecasting, market basket analysis, time series, association models, nested tables, and sequence clustering.</span></span>  
  
## <a name="tutorial-scenario"></a><span data-ttu-id="9e9f6-111">자습서 시나리오</span><span class="sxs-lookup"><span data-stu-id="9e9f6-111">Tutorial Scenario</span></span>  
 <span data-ttu-id="9e9f6-112">이 자습서에서는 사용자가 구매 기록을 기반으로 회사의 고객에 대해 학습한 다음 해당 기록 데이터를 사용하여 마케팅에 사용할 수 있는 예측을 만드는 태스크를 수행하는 [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] 의 직원이라고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="9e9f6-112">In this tutorial, you are an employee of [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] who has been tasked with learning more about the company's customers based on historical purchases, and then using that historical data to make predictions that can be used in marketing.</span></span> <span data-ttu-id="9e9f6-113">이 회사는 이전에 데이터 마이닝을 수행한 적이 없기 때문에 사용자는 특히 데이터 마이닝을 위한 새 데이터베이스를 만들고 여러 데이터 마이닝 모델을 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e9f6-113">The company has never done data mining before, so you must create a new database specifically for data mining and set up several data mining models.</span></span>  
  
## <a name="what-you-will-learn"></a><span data-ttu-id="9e9f6-114">학습 내용</span><span class="sxs-lookup"><span data-stu-id="9e9f6-114">What You Will Learn</span></span>  
 <span data-ttu-id="9e9f6-115">이 자습서에서는 여러 종류의 시스템 학습 방법을 만들고 작업하는 방법을 배웁니다.</span><span class="sxs-lookup"><span data-stu-id="9e9f6-115">This tutorial teaches you how to create and work with several different types of machine learning methods.</span></span> <span data-ttu-id="9e9f6-116">또한 마이닝 모델의 복사본을 만들고 입력 데이터에 필터를 적용하여 여러 가지 결과를 얻는 방법도 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="9e9f6-116">You will also learn how to create a copy of a mining model, and apply a filter to the input data to get different results.</span></span> <span data-ttu-id="9e9f6-117">이후에 리프트 차트를 사용하여 두 모델의 결과를 비교할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e9f6-117">Afterwards you can compare the results of both models using a lift chart.</span></span> <span data-ttu-id="9e9f6-118">마지막으로 드릴스루를 사용하여 기본 마이닝 구조에서 추가 데이터를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="9e9f6-118">Finally, you will use drillthrough to retrieve additional data from the underlying mining structure.</span></span>  
  
 [!INCLUDE[msCoName](../includes/msconame-md.md)]<span data-ttu-id="9e9f6-119">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]데이터 마이닝에는 여러 예측 모델을 쉽게 개발 하 고 비교한 다음 결과에 대 한 작업을 수행 하는 데 도움이 되는 다음과 같은 기능이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e9f6-119">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Data Mining includes the following features that help you easily develop and compare multiple predictive models and then take actions on the results :</span></span>  
  
-   <span data-ttu-id="9e9f6-120">*홀드아웃 테스트 집합 -* 마이닝 구조를 만들 때 이제는 마이닝 구조의 데이터를 학습 집합과 테스트 집합으로 나눌 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e9f6-120">*Holdout Test Sets -* When you create a mining structure, you can now divide the data in the mining structure into training and testing sets.</span></span> <span data-ttu-id="9e9f6-121">이렇게 하면 비슷한 데이터 집합에서 모델을 테스트하고 관련 모델의 정확도를 비교할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e9f6-121">This lets you test models on similar data sets, and compare the accuracy of related models.</span></span>  
  
-   <span data-ttu-id="9e9f6-122">*마이닝 모델 필터 -* 이제 마이닝 모델에 필터를 연결하고 학습 및 테스트 중에 해당 필터를 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e9f6-122">*Mining model filters -* You can now attach filters to a mining model, and apply the filter during both training and testing.</span></span> <span data-ttu-id="9e9f6-123">이렇게 하면 데이터의 여러 하위 집합을 기반으로 관련 모델을 쉽게 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e9f6-123">This lets you easily build related models on different subsets of the data.</span></span>  
  
-   <span data-ttu-id="9e9f6-124">*구조 사례 및 구조 열로 드릴스루 -* 이제 마이닝 모델의 일반적인 패턴에서 데이터 원본의 후속 조치 가능한 세부 정보로 쉽게 전환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e9f6-124">*Drillthrough to Structure Cases and Structure Columns -* You can now easily move from the general patterns in the mining model to actionable detail in the data source.</span></span>  
  
 <span data-ttu-id="9e9f6-125">이 자습서는 다음 단원으로 이루어져 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e9f6-125">This tutorial is divided into the following lessons:</span></span>  
  
 [<span data-ttu-id="9e9f6-126">1 단원: 기본 데이터 마이닝 자습서 &#40;Analysis Services 데이터베이스 준비&#41;</span><span class="sxs-lookup"><span data-stu-id="9e9f6-126">Lesson 1: Preparing the Analysis Services Database &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-1-preparing-the-analysis-services-database-basic-data-mining-tutorial.md)  
 <span data-ttu-id="9e9f6-127">이 단원에서는 새 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 데이터베이스를 만들고 데이터 원본과 데이터 원본 뷰를 추가하며 데이터 마이닝에 사용할 새 데이터베이스를 준비하는 방법을 배웁니다.</span><span class="sxs-lookup"><span data-stu-id="9e9f6-127">In this lesson, you will learn how to create a new [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database, add a data source and data source view, and prepare the new database to be used with data mining.</span></span>  
  
 [<span data-ttu-id="9e9f6-128">2 단원: 기본 데이터 마이닝 자습서 &#40;대상 메일링 구조 구축&#41;</span><span class="sxs-lookup"><span data-stu-id="9e9f6-128">Lesson 2: Building a Targeted Mailing Structure &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-2-building-a-targeted-mailing-structure-basic-data-mining-tutorial.md)  
 <span data-ttu-id="9e9f6-129">이 단원에서는 대상 메일 시나리오의 일부로 사용할 수 있는 마이닝 모델 구조를 만드는 방법을 배웁니다.</span><span class="sxs-lookup"><span data-stu-id="9e9f6-129">In this lesson, you will learn how to create a mining model structure that can be used as part of a targeted mailing scenario.</span></span>  
  
 [<span data-ttu-id="9e9f6-130">3단원: 모델 추가 및 처리</span><span class="sxs-lookup"><span data-stu-id="9e9f6-130">Lesson 3: Adding and Processing Models</span></span>](../../2014/tutorials/lesson-3-adding-and-processing-models.md)  
 <span data-ttu-id="9e9f6-131">이 단원에서는 구조에 모델을 추가하는 방법을 배웁니다.</span><span class="sxs-lookup"><span data-stu-id="9e9f6-131">In this lesson you will learn how to add models to a structure.</span></span> <span data-ttu-id="9e9f6-132">사용자가 만드는 모델은 다음 알고리즘을 사용하여 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e9f6-132">The models you create are built with the following algorithms:</span></span>  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] <span data-ttu-id="9e9f6-133">의사 결정 트리</span><span class="sxs-lookup"><span data-stu-id="9e9f6-133">Decision Trees</span></span>  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] <span data-ttu-id="9e9f6-134">클러스터링</span><span class="sxs-lookup"><span data-stu-id="9e9f6-134">Clustering</span></span>  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] <span data-ttu-id="9e9f6-135">Naive Bayes</span><span class="sxs-lookup"><span data-stu-id="9e9f6-135">Naive Bayes</span></span>  
  
 [<span data-ttu-id="9e9f6-136">4 단원: 기본 데이터 마이닝 자습서 &#40;대상 메일링 모델 탐색&#41;</span><span class="sxs-lookup"><span data-stu-id="9e9f6-136">Lesson 4: Exploring the Targeted Mailing Models &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-4-exploring-the-targeted-mailing-models-basic-data-mining-tutorial.md)  
 <span data-ttu-id="9e9f6-137">이 단원에서는 뷰어를 사용하여 각 모델의 결과를 탐색하고 해석하는 방법을 배웁니다.</span><span class="sxs-lookup"><span data-stu-id="9e9f6-137">In this lesson you will learn how to explore and interpret the findings of each model using the Viewers.</span></span>  
  
 [<span data-ttu-id="9e9f6-138">5 단원: 모델 테스트 &#40;기본 데이터 마이닝 자습서&#41;</span><span class="sxs-lookup"><span data-stu-id="9e9f6-138">Lesson 5: Testing Models &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-5-testing-models-basic-data-mining-tutorial.md)  
 <span data-ttu-id="9e9f6-139">이 단원에서는 대상 메일 모델 중 하나의 복사본을 만들고, 마이닝 모델 필터를 추가하여 학습 데이터를 특정 고객 집합으로 제한한 다음 모델의 실행 가능성을 평가합니다.</span><span class="sxs-lookup"><span data-stu-id="9e9f6-139">In this lesson, you make a copy of one of the targeted mailing models, add a mining model filter to restrict the training data to a particular set of customers, and then assess the viability of the model.</span></span>  
  
 [<span data-ttu-id="9e9f6-140">6단원: 예측 만들기 및 작업&#40;기본 데이터 마이닝 자습서&#41;</span><span class="sxs-lookup"><span data-stu-id="9e9f6-140">Lesson 6: Creating and Working with Predictions &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-6-creating-and-working-with-predictions-basic-data-mining-tutorial.md)  
 <span data-ttu-id="9e9f6-141">기본 데이터 마이닝 자습서의 이 마지막 단원에서는 모델을 사용하여 자전거를 구매할 가능성이 가장 높은 고객을 예측합니다.</span><span class="sxs-lookup"><span data-stu-id="9e9f6-141">In this final lesson of the Basic Data Mining Tutorial, you use the model to predict which customers are most likely to purchase a bike.</span></span> <span data-ttu-id="9e9f6-142">그런 다음 기본 사례로 드릴스루하여 연락처 정보를 얻습니다.</span><span class="sxs-lookup"><span data-stu-id="9e9f6-142">You then drill through to the underlying cases to obtain contact information.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9e9f6-143">요구 사항</span><span class="sxs-lookup"><span data-stu-id="9e9f6-143">Requirements</span></span>  
 <span data-ttu-id="9e9f6-144">다음이 설치되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e9f6-144">Make sure that the following are installed:</span></span>  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] <span data-ttu-id="9e9f6-145">[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9e9f6-145">[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]</span></span>  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)]<span data-ttu-id="9e9f6-146">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 다차원 모드</span><span class="sxs-lookup"><span data-stu-id="9e9f6-146">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] in multidimensional mode</span></span>  
  
-   <span data-ttu-id="9e9f6-147">[!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] 데이터베이스.</span><span class="sxs-lookup"><span data-stu-id="9e9f6-147">The [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] database.</span></span>  
  
 <span data-ttu-id="9e9f6-148">보안을 위해 예제 데이터베이스는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]과 함께 설치되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9e9f6-148">To enhance security, the sample databases are not installed with [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="9e9f6-149">[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]의 공식 데이터베이스를 설치하려면 [Microsoft SQL 예제 데이터베이스](https://go.microsoft.com/fwlink/?LinkId=88417) 페이지에서 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="9e9f6-149">To install the official databases for [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], visit the [Microsoft SQL Sample Databases](https://go.microsoft.com/fwlink/?LinkId=88417) page and select [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9e9f6-150"> 문서 뷰어 도구 모음에 **다음 항목** 단추 및 **이전 항목** 단추를 추가하면 단계의 앞뒤로 편리하게 이동할 수 있어 자습서를 더 쉽게 진행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e9f6-150">When you are working through a tutorial, you might find it easier to move back and forth between the steps if you add the **Next topic** and **Previous topic** buttons to the document viewer toolbar.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e9f6-151">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9e9f6-151">See Also</span></span>  
 <span data-ttu-id="9e9f6-152">[데이터 마이닝 솔루션](../../2014/analysis-services/data-mining/data-mining-solutions.md) </span><span class="sxs-lookup"><span data-stu-id="9e9f6-152">[Data Mining Solutions](../../2014/analysis-services/data-mining/data-mining-solutions.md) </span></span>  
 <span data-ttu-id="9e9f6-153">[마이닝 모델 태스크 및 방법](../../2014/analysis-services/data-mining/mining-model-tasks-and-how-tos.md) </span><span class="sxs-lookup"><span data-stu-id="9e9f6-153">[Mining Model Tasks and How-tos](../../2014/analysis-services/data-mining/mining-model-tasks-and-how-tos.md) </span></span>  
 [<span data-ttu-id="9e9f6-154">DMX를 사용하여 데이터 마이닝 모델 만들기 및 쿼리: 자습서&#40;Analysis Services - 데이터 마이닝&#41;</span><span class="sxs-lookup"><span data-stu-id="9e9f6-154">Creating and Querying Data Mining Models with DMX: Tutorials &#40;Analysis Services - Data Mining&#41;</span></span>](../../2014/tutorials/create-query-data-mining-models-dmx-tutorials.md)  
  
  
