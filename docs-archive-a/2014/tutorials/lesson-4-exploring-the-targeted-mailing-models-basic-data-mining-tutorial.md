---
title: '4 단원: 타겟 메일링 모델 탐색 (기본 데이터 마이닝 자습서) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 1e00c5b9-a9f8-4503-99ee-377c9cc02d7f
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 8659350b126164e06550acdbecec04bb07499c55
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735623"
---
# <a name="lesson-4-exploring-the-targeted-mailing-models-basic-data-mining-tutorial"></a><span data-ttu-id="6086a-102">4단원: 타겟 메일링 모델 탐색(기본 데이터 마이닝 자습서)</span><span class="sxs-lookup"><span data-stu-id="6086a-102">Lesson 4: Exploring the Targeted Mailing Models (Basic Data Mining Tutorial)</span></span>
  <span data-ttu-id="6086a-103">프로젝트의 모델이 처리되면 이러한 모델을 탐색하여 관심 있는 추세를 찾아볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6086a-103">After the models in your project have been processed, you can explore them to look for interesting trends.</span></span> <span data-ttu-id="6086a-104">숫자만 보는 경우 패턴이 복잡하고 어려울 수 있기 때문에 SQL Server 데이터 마이닝은 데이터를 조사하고 알고리즘이 데이터 내에서 발견한 규칙과 관계를 이해하는 데 도움을 주는 몇 가지 시각적 도구를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="6086a-104">Because patterns can be complex and difficult simply by looking at numbers, SQL Server Data Mining provides some visual tools that help you investigate the data and understand the rules and relationships that the algorithms have discovered within the data.</span></span> <span data-ttu-id="6086a-105">또한 다양한 정확도 테스트를 사용하여 데이터 세트의 유효성을 검사하거나 모델을 배포하기 전에 성능이 가장 뛰어난 모델을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6086a-105">You can also use a variety of accuracy tests to validate your dataset or discover which model performs best before you deploy it.</span></span>  
  
 <span data-ttu-id="6086a-106">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 를 사용하여 모델을 탐색하는 경우 만들어진 각 모델은 데이터 마이닝 디자이너의 **마이닝 모델 뷰어** 탭에 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="6086a-106">When you use [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] to explore your models, each model you created is listed in the **Mining Model Viewer** tab in Data Mining Designer.</span></span> <span data-ttu-id="6086a-107">뷰어를 사용하여 모델을 탐색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6086a-107">You can use the viewers to explore the models.</span></span> <span data-ttu-id="6086a-108">이러한 뷰는 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]에서도 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6086a-108">These viewers are also available in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="6086a-109">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 에서 모델을 작성하는 데 사용하는 각 알고리즘에 따라 다른 유형의 결과가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="6086a-109">Each algorithm that you used to build a model in [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] returns a different type of result.</span></span> <span data-ttu-id="6086a-110">따라서 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 는 각 유형의 시스템 학습 모델에 대한 사용자 지정 뷰어를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="6086a-110">Therefore, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] provides custom viewers for each type of machine learning model.</span></span>  
  
 <span data-ttu-id="6086a-111">세부 사항을 보려는 경우 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 는 **일반 콘텐츠 트리 뷰어**라는 HTML 뷰어도 제공합니다. 이 뷰어에는 모델 데이터와 발견된 모든 패턴에 대한 자세한 정보가 절반 정도는 표 형식으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="6086a-111">If you want to get into details, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] also provides an HTML viewer, called the **Generic Content Tree Viewer**, that displays detailed information about the model data and any patterns that were found, in a semi-tabular format.</span></span> <span data-ttu-id="6086a-112">자세한 내용은 [Microsoft 일반 콘텐츠 트리 뷰어를 사용하여 모델 찾아보기](../../2014/analysis-services/data-mining/browse-a-model-using-the-microsoft-generic-content-tree-viewer.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6086a-112">For more information, see [Browse a Model Using the Microsoft Generic Content Tree Viewer](../../2014/analysis-services/data-mining/browse-a-model-using-the-microsoft-generic-content-tree-viewer.md).</span></span>  
  
 <span data-ttu-id="6086a-113">이 단원에서는 세 모델에서 결과를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="6086a-113">In this lesson you will look at the results from your three models.</span></span> <span data-ttu-id="6086a-114">각 모델 형식은 다른 알고리즘을 기반으로 하며 데이터에 대한 다른 관점을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="6086a-114">Each model type is based on a different algorithm and provides different insights into the data.</span></span>  
  
-   <span data-ttu-id="6086a-115">의사 결정 트리 모델은 자전거 구매에 영향을 주는 요소에 대해 알려줍니다.</span><span class="sxs-lookup"><span data-stu-id="6086a-115">The Decision Tree model tells you about factors that influence bike buying.</span></span>  
  
-   <span data-ttu-id="6086a-116">클러스터링 모델은 자전거 구매 동작 및 기타 선택한 특성을 포함하는 특성별로 고객을 그룹화합니다.</span><span class="sxs-lookup"><span data-stu-id="6086a-116">The Clustering model groups your customers by attributes that include their bike buying behavior and other selected attributes.</span></span>  
  
-   <span data-ttu-id="6086a-117">Naive Bayes 모델을 통해 다른 특성 간 관계를 탐색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6086a-117">The Naive Bayes model enables you to explore the relationship between different attributes.</span></span>  
  
 <span data-ttu-id="6086a-118">각 마이닝 모델 뷰어에 대해 자세히 알아보려면 다음 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="6086a-118">See the following topics to learn more about each of the mining model viewers.</span></span>  
  
-   [<span data-ttu-id="6086a-119">기본 데이터 마이닝 자습서 &#40;의사 결정 트리 모델 탐색&#41;</span><span class="sxs-lookup"><span data-stu-id="6086a-119">Exploring the Decision Tree Model &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/exploring-the-decision-tree-model-basic-data-mining-tutorial.md)  
  
-   [<span data-ttu-id="6086a-120">기본 데이터 마이닝 자습서 &#40;클러스터링 모델 탐색&#41;</span><span class="sxs-lookup"><span data-stu-id="6086a-120">Exploring the Clustering Model &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/exploring-the-clustering-model-basic-data-mining-tutorial.md)  
  
-   [<span data-ttu-id="6086a-121">Naive Bayes 모델 &#40;기본 데이터 마이닝 자습서 살펴보기&#41;</span><span class="sxs-lookup"><span data-stu-id="6086a-121">Exploring the Naive Bayes Model &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/exploring-the-naive-bayes-model-basic-data-mining-tutorial.md)  
  
 <span data-ttu-id="6086a-122">수식, 데이터 값 등을 추출하기 위해 세 모델을 모두 **일반 콘텐츠 트리 뷰어**를 사용하여 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6086a-122">All three models can be viewed using the **Generic Content Tree Viewer**, to extract formulas, data values, and so forth.</span></span>  
  
## <a name="first-task-in-lesson"></a><span data-ttu-id="6086a-123">단원의 첫 번째 태스크</span><span class="sxs-lookup"><span data-stu-id="6086a-123">First Task in Lesson</span></span>  
 [<span data-ttu-id="6086a-124">기본 데이터 마이닝 자습서 &#40;의사 결정 트리 모델 탐색&#41;</span><span class="sxs-lookup"><span data-stu-id="6086a-124">Exploring the Decision Tree Model &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/exploring-the-decision-tree-model-basic-data-mining-tutorial.md)  
  
## <a name="previous-lesson"></a><span data-ttu-id="6086a-125">이전 단원</span><span class="sxs-lookup"><span data-stu-id="6086a-125">Previous Lesson</span></span>  
 [<span data-ttu-id="6086a-126">3단원: 모델 추가 및 처리</span><span class="sxs-lookup"><span data-stu-id="6086a-126">Lesson 3: Adding and Processing Models</span></span>](../../2014/tutorials/lesson-3-adding-and-processing-models.md)  
  
## <a name="next-lesson"></a><span data-ttu-id="6086a-127">다음 단원</span><span class="sxs-lookup"><span data-stu-id="6086a-127">Next Lesson</span></span>  
 [<span data-ttu-id="6086a-128">5 단원: 모델 테스트 &#40;기본 데이터 마이닝 자습서&#41;</span><span class="sxs-lookup"><span data-stu-id="6086a-128">Lesson 5: Testing Models &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-5-testing-models-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="6086a-129">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6086a-129">See Also</span></span>  
 <span data-ttu-id="6086a-130">[마이닝 모델 뷰어 태스크 및 방법](../../2014/analysis-services/data-mining/mining-model-viewer-tasks-and-how-tos.md) </span><span class="sxs-lookup"><span data-stu-id="6086a-130">[Mining Model Viewer Tasks and How-tos](../../2014/analysis-services/data-mining/mining-model-viewer-tasks-and-how-tos.md) </span></span>  
 [<span data-ttu-id="6086a-131">데이터 마이닝 모델 뷰어</span><span class="sxs-lookup"><span data-stu-id="6086a-131">Data Mining Model Viewers</span></span>](../../2014/analysis-services/data-mining/data-mining-model-viewers.md)  
  
  
