---
title: 데이터 마이닝 속성 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- ClusterCount property
- AllowedProvidersInOpenRowset property
- MinimumSeriesValue property
- ScoreMethod property
- MinimumImportance property
- ModellingCardinality property
- BrentTolerance property
- ComplexityPenalty property
- MaximumItemsetCount property
- MinimumSupport property
- AllowSessionMiningModels property
- HoldoutPercentage property
- ClusterCountPrior property
- MaximumSequenceStates property
- OptimizedPredictionCount property
- data mining [Analysis Services], properties
- MaximumStates property
- MaximumContinuousInputAttributes property
- MaximumOutputAttributes property
- AllowAdHocOpenRowsetQueries property
- Enabled property
- HistoricModelGap property
- SampleSize property
- MaximumInputAttributes property
- PeriodicityHint property
- MissingValueSubstitution property
- SplitMethod property
- ForceRegressor property
- MaximumBucketsForContinuousSplit property
- MaxConcurrentPredictionQueries property
- MinimumItemsetSize property
- AcyclicGraph property
- HoldoutMethod property
- StoppingTolerance property
- properties [data mining]
- AutoDetectPeriodicity property
- HoldoutTolerance property
- MinimumLeafCases property
- HoldoutSeed property
- MinimumClusterCases property
- ClusterCountDeviation property
- MinimumDependencyProbability property
- ClusteringMethod property
- MaximumItemsetSize property
- HiddenNodeRatio property
- MaximumSeriesValue property
ms.assetid: 9bc9abed-180a-4bd8-b2eb-89c62fa88110
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5ed1c47faafeb0c680e6afb6f8e509c426760da2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743508"
---
# <a name="data-mining-properties"></a><span data-ttu-id="d7cef-102">데이터 마이닝 속성</span><span class="sxs-lookup"><span data-stu-id="d7cef-102">Data Mining Properties</span></span>
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="d7cef-103">에서는 다음 표에 나열된 데이터 마이닝 서버 속성을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="d7cef-103">supports the data mining server properties listed in the following tables.</span></span> <span data-ttu-id="d7cef-104">추가 서버 속성 및 해당 속성 설정 방법은 [Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d7cef-104">For more information about additional server properties and how to set them, see [Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md).</span></span>  
  
 <span data-ttu-id="d7cef-105">**적용 대상:** 다차원 서버 모드에만 해당</span><span class="sxs-lookup"><span data-stu-id="d7cef-105">**Applies to:** Multidimensional server mode only</span></span>  
  
## <a name="non-specific-category"></a><span data-ttu-id="d7cef-106">일반 범주</span><span class="sxs-lookup"><span data-stu-id="d7cef-106">Non-Specific Category</span></span>  
 `AllowSessionMiningModels`  
 <span data-ttu-id="d7cef-107">세션 마이닝 모델을 만들 수 있는지 여부를 나타내는 부울 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="d7cef-107">A Boolean property that indicates whether session mining models can be created.</span></span>  
  
 <span data-ttu-id="d7cef-108">이 속성의 기본값은 False로 세션 마이닝 모델을 만들 수 없음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="d7cef-108">The default value for this property is false, which indicates that session mining models cannot be created.</span></span>  
  
 `AllowAdHocOpenRowsetQueries`  
 <span data-ttu-id="d7cef-109">임시로 열린 행 집합 쿼리가 허용되는지 여부를 나타내는 부울 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="d7cef-109">A Boolean property that indicates whether adhoc open rowset queries are allowed.</span></span>  
  
 <span data-ttu-id="d7cef-110">이 속성의 기본값은 False로 열린 행 집합 쿼리가 세션 중에는 허용되지 않음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="d7cef-110">The default value for this property is false, which indicates that open rowset queries are not allowed during a session.</span></span>  
  
 `AllowedProvidersInOpenRowset`  
 <span data-ttu-id="d7cef-111">쉼표/세미콜론으로 구분된 공급자 ProgID 또는 그 외 경우 [All] 목록으로 구성된 열린 행 집합에서 어떤 공급자가 허용되는지를 식별하는 문자열 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="d7cef-111">A string property that identifies which providers are allowed in an open rowset, consisting of a comma/semi-colon separated list of provider ProgIDs, or else [All].</span></span>  
  
 `MaxConcurrentPredictionQueries`  
 <span data-ttu-id="d7cef-112">최대 동시 예측 쿼리 수를 정의하는 부호 있는 32비트 정수 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="d7cef-112">A signed 32-bit integer property that defines the maximum number of concurrent prediction queries.</span></span>  
  
## <a name="algorithms-category"></a><span data-ttu-id="d7cef-113">알고리즘 범주</span><span class="sxs-lookup"><span data-stu-id="d7cef-113">Algorithms Category</span></span>  
 `Microsoft_Association_Rules\ Enabled`  
 <span data-ttu-id="d7cef-114">Microsoft_Association_Rules 알고리즘이 설정되어 있는지 여부를 나타내는 부울 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="d7cef-114">A Boolean property that indicates whether the Microsoft_Association_Rules algorithm is enabled.</span></span>  
  
 `Microsoft_Clustering\ Enabled`  
 <span data-ttu-id="d7cef-115">Microsoft_Clustering 알고리즘이 설정되어 있는지 여부를 나타내는 부울 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="d7cef-115">A Boolean property that indicates whether the Microsoft_Clustering algorithm is enabled.</span></span>  
  
 `Microsoft_Decision_Trees\ Enabled`  
 <span data-ttu-id="d7cef-116">Microsoft_DecisionTrees 알고리즘이 설정되어 있는지 여부를 나타내는 부울 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="d7cef-116">A Boolean property that indicates whether the Microsoft_DecisionTrees algorithm is enabled.</span></span>  
  
 `Microsoft_Naive_Bayes\ Enabled`  
 <span data-ttu-id="d7cef-117">Microsoft_Naive_Bayes 알고리즘이 설정되어 있는지 여부를 나타내는 부울 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="d7cef-117">A Boolean property that indicates whether the Microsoft_ Naive_Bayes algorithm is enabled.</span></span>  
  
 `Microsoft_Neural_Network\ Enabled`  
 <span data-ttu-id="d7cef-118">Microsoft_Neural_Network 알고리즘이 설정되어 있는지 여부를 나타내는 부울 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="d7cef-118">A Boolean property that indicates whether the Microsoft_Neural_Network algorithm is enabled.</span></span>  
  
 `Microsoft_Sequence_Clustering\ Enabled`  
 <span data-ttu-id="d7cef-119">Microsoft_Sequence_Clustering 알고리즘이 설정되어 있는지 여부를 나타내는 부울 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="d7cef-119">A Boolean property that indicates whether the Microsoft_Sequence_Clustering algorithm is enabled.</span></span>  
  
 `Microsoft_Time_Series\ Enabled`  
 <span data-ttu-id="d7cef-120">Microsoft_Time_Series 알고리즘이 설정되어 있는지 여부를 나타내는 부울 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="d7cef-120">A Boolean property that indicates whether the Microsoft_Time_Series algorithm is enabled.</span></span>  
  
 `Microsoft_Linear_Regression\ Enabled`  
 <span data-ttu-id="d7cef-121">Microsoft_Linear_Regression 알고리즘이 설정되어 있는지 여부를 나타내는 부울 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="d7cef-121">A Boolean property that indicates whether the Microsoft_Linear_Regression algorithm is enabled.</span></span>  
  
 `Microsoft_Logistic_Regression\ Enabled`  
 <span data-ttu-id="d7cef-122">Microsoft_Logistic_Regression 알고리즘이 설정되어 있는지 여부를 나타내는 부울 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="d7cef-122">A Boolean property that indicates whether the Microsoft_Logistic_Regression algorithm is enabled.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d7cef-123">서버에서 사용할 수 있는 데이터 마이닝 서비스를 정의하는 속성 외에 특정 알고리즘의 동작을 정의하는 데이터 마이닝 속성도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d7cef-123">In addition to properties that define the data mining services available on the server, there are data mining properties that define the behavior of specific algorithms.</span></span> <span data-ttu-id="d7cef-124">이러한 속성은 서버 수준에서 데이터 마이닝 모델을 만들 때가 아니라 개별 데이터 마이닝 모델을 만들 때 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="d7cef-124">You configure these properties when you create an individual data mining model, not at the server level.</span></span> <span data-ttu-id="d7cef-125">자세한 내용은 [데이터 마이닝 알고리즘&#40;Analysis Services - 데이터 마이닝&#41;](../data-mining/data-mining-algorithms-analysis-services-data-mining.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d7cef-125">For more information, see [Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](../data-mining/data-mining-algorithms-analysis-services-data-mining.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7cef-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d7cef-126">See Also</span></span>  
 <span data-ttu-id="d7cef-127">[물리적 아키텍처 &#40;Analysis Services 데이터 마이닝&#41;](../data-mining/physical-architecture-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="d7cef-127">[Physical Architecture &#40;Analysis Services - Data Mining&#41;](../data-mining/physical-architecture-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="d7cef-128">[Analysis Services에서 서버 속성 구성](server-properties-in-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="d7cef-128">[Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md) </span></span>  
 [<span data-ttu-id="d7cef-129">Analysis Services 인스턴스의 서버 모드 확인</span><span class="sxs-lookup"><span data-stu-id="d7cef-129">Determine the Server Mode of an Analysis Services Instance</span></span>](../instances/determine-the-server-mode-of-an-analysis-services-instance.md)  
  
  
