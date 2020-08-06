---
title: 데이터 마이닝 개체 처리 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- processing objects [Analysis Services]
- mining structures [Analysis Services]
- process [Analysis Services]
- mining structures [Analysis Services], creating
- mining structures [Analysis Services], how-to topics
- mining structures [Analysis Services], processing
ms.assetid: 0f6993c0-0917-4935-82f9-7b8a8a7cc627
author: minewiskan
ms.author: owend
ms.openlocfilehash: a4a6693a46679badc068111a311bb82219e752cd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734607"
---
# <a name="processing-data-mining-objects"></a><span data-ttu-id="1b183-102">데이터 마이닝 개체 처리</span><span class="sxs-lookup"><span data-stu-id="1b183-102">Processing Data Mining Objects</span></span>
  <span data-ttu-id="1b183-103">데이터 마이닝 개체는 처리되기 전까지는 단순히 빈 컨테이너입니다.</span><span class="sxs-lookup"><span data-stu-id="1b183-103">A data mining object is only an empty container until it has been processed.</span></span> <span data-ttu-id="1b183-104">데이터 마이닝 모델을*처리* 하는 작업을 *학습*이라고도 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b183-104">*Processing* a data mining model is also called *training*.</span></span>  
  
 <span data-ttu-id="1b183-105">**마이닝 구조 처리:** 마이닝 구조는 외부 데이터 원본에서 열 바인딩 및 사용법 메타데이터에 의해 정의된 데이터를 가져와서 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="1b183-105">**Processing mining structures:** A mining structure gets data from an external data source, as defined by the column bindings and usage metadata, and reads the data.</span></span> <span data-ttu-id="1b183-106">이 데이터 전체를 읽은 다음 분석하여 다양한 통계를 추출합니다.</span><span class="sxs-lookup"><span data-stu-id="1b183-106">This data is read in full and then analyzed to extract various statistics.</span></span> <span data-ttu-id="1b183-107">Analysis Services에서는 데이터 마이닝 알고리즘으로 분석하는 데 적합한 데이터의 압축된 표현을 로컬 캐시에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="1b183-107">Analysis Services stores a compact representation of the data, which is suitable for analysis by data mining algorithms, in a local cache.</span></span> <span data-ttu-id="1b183-108">이 캐시는 보관하거나 모델 처리 후 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b183-108">You can either keep this cache or delete it after your models have been processed.</span></span> <span data-ttu-id="1b183-109">기본적으로 캐시는 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b183-109">By default, the cache is stored.</span></span> <span data-ttu-id="1b183-110">자세한 내용은 [Process a Mining Structure](process-a-mining-structure.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1b183-110">For more information, see [Process a Mining Structure](process-a-mining-structure.md).</span></span>  
  
 <span data-ttu-id="1b183-111">**마이닝 모델 처리:** 마이닝 모델은 처리되기 전까지는 정의만 들어 있는 빈 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="1b183-111">**Processing mining models:** A mining model is empty, containing definitions only, until it is processed.</span></span> <span data-ttu-id="1b183-112">마이닝 모델을 처리하려면 먼저 해당 모델의 기반이 되는 마이닝 구조를 처리해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b183-112">To process a mining model, the mining structure that it is based on must have been processed.</span></span> <span data-ttu-id="1b183-113">마이닝 모델은 마이닝 구조 캐시에서 데이터를 가져오고, 모델에 필터가 만들어진 경우 이를 적용한 다음, 알고리즘을 통해 데이터 집합을 전달하여 패턴을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="1b183-113">The mining model gets the data from the mining structure cache, applies any filters that may have been created on the model, and then passes the data set through the algorithm to detect patterns.</span></span> <span data-ttu-id="1b183-114">모델이 처리된 후 모델에는 데이터 자체가 아니라 처리 결과만 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b183-114">After the model is processed, the model stores only the results of processing, not the data itself.</span></span> <span data-ttu-id="1b183-115">자세한 내용은 [마이닝 모델 처리](process-a-mining-model.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1b183-115">For more information, see [Process a Mining Model](process-a-mining-model.md).</span></span>  
  
 <span data-ttu-id="1b183-116">다음 다이어그램에서는 마이닝 구조가 처리될 때와 마이닝 모델이 처리될 때의 데이터 흐름을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="1b183-116">The following diagram illustrates the flow of data when a mining structure is processed, and when a mining model is processed.</span></span>  
  
 <span data-ttu-id="1b183-117">![데이터 처리: 원본, 구조, 모델 순으로 처리](../media/dmcon-modelarch.gif "데이터 처리: 원본, 구조, 모델 순으로 처리")</span><span class="sxs-lookup"><span data-stu-id="1b183-117">![Processing of data: source to structure to model](../media/dmcon-modelarch.gif "Processing of data: source to structure to model")</span></span>  
  
## <a name="viewing-the-results-of-processing"></a><span data-ttu-id="1b183-118">처리 결과 보기</span><span class="sxs-lookup"><span data-stu-id="1b183-118">Viewing the Results of Processing</span></span>  
 <span data-ttu-id="1b183-119">마이닝 구조가 처리된 후 해당 마이닝 구조에는 통계 분석에 사용할 데이터의 압축된 표현이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b183-119">After a mining structure has been processed, it contains a compact representation of the data for use in statistical analysis.</span></span> <span data-ttu-id="1b183-120">캐시가 지워지지 않은 경우 다음 방법으로 이 캐시의 데이터에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b183-120">If the cache has not been cleared, you can access the data in this cache in the following ways:</span></span>  
  
-   <span data-ttu-id="1b183-121">모델에 대한 DMX(Data Mining Extensions) 쿼리를 만들고 구조로 드릴스루합니다.</span><span class="sxs-lookup"><span data-stu-id="1b183-121">Creating a Data Mining Extensions (DMX) query on the model and drilling through to the structure.</span></span> <span data-ttu-id="1b183-122">자세한 내용은 [SELECT FROM &#60;model&#62;.CASES&#40;DMX&#41;](/sql/dmx/select-from-model-content-dmx)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1b183-122">For more information, see [SELECT FROM &#60;model&#62;.CASES &#40;DMX&#41;](/sql/dmx/select-from-model-content-dmx).</span></span>  
  
-   <span data-ttu-id="1b183-123">해당 구조를 기반으로 하는 모델을 찾아보고 사용자 인터페이스의 옵션 중 하나를 사용하여 구조 사례로 드릴스루합니다.</span><span class="sxs-lookup"><span data-stu-id="1b183-123">Browsing a model based on the structure, and using one of the options in the user interface to drill through to structure cases.</span></span> <span data-ttu-id="1b183-124">자세한 내용은 [데이터 마이닝 모델 뷰어](data-mining-model-viewers.md)또는 [마이닝 모델에서 사례 데이터로 드릴스루](drill-through-to-case-data-from-a-mining-model.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1b183-124">For more information, see [Data Mining Model Viewers](data-mining-model-viewers.md), or [Drill Through to Case Data from a Mining Model](drill-through-to-case-data-from-a-mining-model.md).</span></span>  
  
-   <span data-ttu-id="1b183-125">구조 사례에 대한 DMX 쿼리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1b183-125">Creating a DMX query on the structure cases.</span></span> <span data-ttu-id="1b183-126">자세한 내용은 [SELECT FROM &#60;structure&#62;.CASES](/sql/dmx/select-from-structure-cases)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1b183-126">For more information, see [SELECT FROM &#60;structure&#62;.CASES](/sql/dmx/select-from-structure-cases).</span></span>  
  
 <span data-ttu-id="1b183-127">마이닝 모델이 처리된 후 해당 마이닝 모델에는 분석에서 얻은 패턴과 모델 결과에서 캐시된 학습 데이터로의 매핑만 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b183-127">After a mining model has been processed, it contains only the patterns that were derived from analysis, and mappings from the model results to the cached training data.</span></span> <span data-ttu-id="1b183-128">*모델 콘텐츠*라는 모델 결과를 찾아보거나 쿼리할 수도 있고, 모델 결과가 캐시된 경우 모델 및 구조 사례를 쿼리할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b183-128">You can browse or query the model results, called *model content*, or you can query the model and structure cases, if they have been cached.</span></span>  
  
 <span data-ttu-id="1b183-129">각 마이닝 모델의 모델 콘텐츠는 마이닝 모델을 만드는 데 사용된 알고리즘에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="1b183-129">The model content for each mining model depends on the algorithm that was used to create it.</span></span> <span data-ttu-id="1b183-130">예를 들어 한 모델은 클러스터링 모델이고 다른 모델은 의사 결정 트리 모델인 경우 모델이 동일한 데이터를 사용하더라도 모델 콘텐츠는 매우 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="1b183-130">For example, if one model is a clustering model and another is a decision trees model, the model content is very different even though the models use exactly the same data.</span></span> <span data-ttu-id="1b183-131">자세한 내용은 [마이닝 모델 콘텐츠&#40;Analysis Services - 데이터 마이닝&#41;](mining-model-content-analysis-services-data-mining.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1b183-131">For more information, see [Mining Model Content &#40;Analysis Services - Data Mining&#41;](mining-model-content-analysis-services-data-mining.md).</span></span>  
  
## <a name="processing-requirements"></a><span data-ttu-id="1b183-132">처리 요구 사항</span><span class="sxs-lookup"><span data-stu-id="1b183-132">Processing Requirements</span></span>  
 <span data-ttu-id="1b183-133">처리 요구 사항은 마이닝 모델이 전적으로 관계형 데이터를 기반으로 하는지 아니면 다차원 데이터 원본을 기반으로 하는지 여부에 따라 달라질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b183-133">Processing requirements may differ depending on whether your mining models are based solely on relational data, or on multidimensional data source.</span></span>  
  
 <span data-ttu-id="1b183-134">관계형 데이터 원본을 처리하기 위해서는 학습 데이터를 만들고 해당 데이터에 대해 마이닝 알고리즘을 실행하기만 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b183-134">For relational data source, processing requires only that you create training data and run mining algorithms on that data.</span></span> <span data-ttu-id="1b183-135">그러나 차원 및 측정값과 같은 OLAP 개체를 기반으로 하는 마이닝 모델의 경우에는 기본 데이터가 처리된 상태에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b183-135">However, mining models that are based on OLAP objects, such as dimensions and measures, require that the underlying data be in a processed state.</span></span> <span data-ttu-id="1b183-136">이를 위해 다차원 개체를 처리하여 마이닝 모델을 채워야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b183-136">This may requires that the multidimensional objects be processed to populate the mining model.</span></span>  
  
 <span data-ttu-id="1b183-137">자세한 내용은 [처리 요구 사항 및 고려 사항&#40;데이터 마이닝&#41;](processing-requirements-and-considerations-data-mining.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1b183-137">For more information, see [Processing Requirements and Considerations &#40;Data Mining&#41;](processing-requirements-and-considerations-data-mining.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b183-138">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1b183-138">See Also</span></span>  
 <span data-ttu-id="1b183-139">[드릴스루 쿼리 &#40;데이터 마이닝&#41;](drillthrough-queries-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="1b183-139">[Drillthrough Queries &#40;Data Mining&#41;](drillthrough-queries-data-mining.md) </span></span>  
 <span data-ttu-id="1b183-140">[마이닝 구조 &#40;Analysis Services 데이터 마이닝&#41;](mining-structures-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="1b183-140">[Mining Structures &#40;Analysis Services - Data Mining&#41;](mining-structures-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="1b183-141">[마이닝 모델 &#40;Analysis Services 데이터 마이닝&#41;](mining-models-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="1b183-141">[Mining Models &#40;Analysis Services - Data Mining&#41;](mining-models-analysis-services-data-mining.md) </span></span>  
 [<span data-ttu-id="1b183-142">논리적 아키텍처&#40;Analysis Services - 데이터 마이닝&#41;</span><span class="sxs-lookup"><span data-stu-id="1b183-142">Logical Architecture &#40;Analysis Services - Data Mining&#41;</span></span>](logical-architecture-analysis-services-data-mining.md)  
  
  
