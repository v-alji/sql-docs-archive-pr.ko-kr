---
title: Microsoft 일반 콘텐츠 트리 뷰어를 사용 하 여 모델 찾아보기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining model content, viewing
ms.assetid: 4a5f7c51-c704-4214-b05d-21cf735e6d96
author: minewiskan
ms.author: owend
ms.openlocfilehash: 90d47262a09060a11020e50b3724753799d2d188
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660791"
---
# <a name="browse-a-model-using-the-microsoft-generic-content-tree-viewer"></a><span data-ttu-id="7ac0b-102">Microsoft 일반 콘텐츠 트리 뷰어를 사용하여 모델 찾아보기</span><span class="sxs-lookup"><span data-stu-id="7ac0b-102">Browse a Model Using the Microsoft Generic Content Tree Viewer</span></span>
  <span data-ttu-id="7ac0b-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 일반 마이닝 모델 콘텐츠 뷰어는 마이닝 알고리즘을 통해 발견된 패턴에 대한 자세한 정보를 제공하며, 분석 프로세스 중에 생성된 다양한 통계에 대한 액세스도 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="7ac0b-103">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Generic Mining Model Content Viewer provides detailed information about the patterns found by the mining algorithm, and also provides access to various statistics generated during the analysis process.</span></span> <span data-ttu-id="7ac0b-104">정보의 양과 유형은 사용된 알고리즘에 따라 다르지만 다음과 같은 범주가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ac0b-104">The amount and type of information depends on the algorithm that was used, but can include the following categories:</span></span>  
  
-   <span data-ttu-id="7ac0b-105">데이터 세그먼트 및 특징</span><span class="sxs-lookup"><span data-stu-id="7ac0b-105">Segments of data, and their characteristics.</span></span>  
  
-   <span data-ttu-id="7ac0b-106">각 그룹 또는 전체 데이터 집합에 대한 기술 통계</span><span class="sxs-lookup"><span data-stu-id="7ac0b-106">Descriptive statistics about each group or about the whole set of data.</span></span>  
  
-   <span data-ttu-id="7ac0b-107">트리의 분기 또는 자식 노드 수</span><span class="sxs-lookup"><span data-stu-id="7ac0b-107">The number of branches or child nodes in a tree.</span></span>  
  
-   <span data-ttu-id="7ac0b-108">클러스터 또는 전체 데이터 집합에 대한 계산(예: 분산 또는 평균)</span><span class="sxs-lookup"><span data-stu-id="7ac0b-108">Calculations, such as variance and mean, for a cluster or a whole set of data.</span></span>  
  
 <span data-ttu-id="7ac0b-109">이러한 정보를 보면 분석 결과를 보다 잘 이해하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ac0b-109">Viewing this information can help you better understand the results of your analysis.</span></span> <span data-ttu-id="7ac0b-110">또한 모델을 미세 조정한 다음 다시 학습하는 방법도 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ac0b-110">You can also identify ways to fine-tune, and then retrain, your model.</span></span> <span data-ttu-id="7ac0b-111">또는 다른 알고리즘을 사용하여 다시 학습하도록 결정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ac0b-111">Or, you might decide to retrain by using a different algorithm.</span></span>  
  
## <a name="viewing-mining-model-content"></a><span data-ttu-id="7ac0b-112">마이닝 모델 콘텐츠 보기</span><span class="sxs-lookup"><span data-stu-id="7ac0b-112">Viewing Mining Model Content</span></span>  
 <span data-ttu-id="7ac0b-113">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 일반 콘텐츠 뷰어에는 마이닝 모델 *콘텐츠 스키마 행 집합* 의 열, 규칙, 속성, 특성, 노드 및 기타 콘텐츠가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ac0b-113">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Generic Content Viewer displays the columns, rules, properties, attributes, nodes, and other content from the *content schema rowset* of the mining model.</span></span> <span data-ttu-id="7ac0b-114">콘텐츠 스키마 행 집합은 데이터 마이닝 모델의 콘텐츠에 대한 세부 정보를 나타내는 일반 프레임워크입니다.</span><span class="sxs-lookup"><span data-stu-id="7ac0b-114">The content schema rowset is a generic framework for presenting detailed information about the content of a data mining model.</span></span>  
  
 <span data-ttu-id="7ac0b-115">이 자세한 정보는 모델의 패턴, 클러스터 또는 트리를 노드로 나타내는 HTML 테이블에 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ac0b-115">This detailed information is contained in an HTML table that represents the patterns, clusters, or trees in the model as nodes.</span></span> <span data-ttu-id="7ac0b-116">각 노드를 클릭하고 확장하여 숫자 특성의 고유 값 개수 또는 수식과 같은 자세한 세부 정보를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ac0b-116">You can click on each node and expand it to see more detail, such as the formulas or the count of distinct values for a numeric attribute.</span></span> <span data-ttu-id="7ac0b-117">노드 간의 자식-부모 관계를 탐색할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ac0b-117">You can also explore the child-parent relationships among the nodes.</span></span>  
  
 <span data-ttu-id="7ac0b-118">마이닝 모델 콘텐츠에 사용된 용어의 일반적인 의미에 대한 자세한 내용은 [마이닝 모델 콘텐츠&#40;Analysis Services - 데이터 마이닝&#41;](mining-model-content-analysis-services-data-mining.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7ac0b-118">For more information about the general meaning of the terms used in the mining model content, see [Mining Model Content &#40;Analysis Services - Data Mining&#41;](mining-model-content-analysis-services-data-mining.md).</span></span> <span data-ttu-id="7ac0b-119">항목에는 특정 모델 유형의 마이닝 모델 콘텐츠에 대한 정보를 볼 수 있는 링크도 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ac0b-119">The topic also contains links to information about mining model content for specific types of models.</span></span> <span data-ttu-id="7ac0b-120">각 마이닝 모델 유형에 데이터에서 찾은 알고리즘 및 패턴과 관련성이 매우 높은 정보가 포함되어 있으므로 각 모델 유형을 완전히 이해하기 위해 각 모델 유형에 대해 기술 참조 항목을 검토하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="7ac0b-120">Each type of mining model contains information that is highly specific to the algorithm and the patterns found in the data, so we recommend that you consult the technical reference topic for each model type in order to fully understand each model type.</span></span>  
  
## <a name="querying-mining-model-content"></a><span data-ttu-id="7ac0b-121">마이닝 모델 내용 쿼리</span><span class="sxs-lookup"><span data-stu-id="7ac0b-121">Querying Mining Model Content</span></span>  
 <span data-ttu-id="7ac0b-122">마이닝 모델을 쿼리하면 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 일반 콘텐츠 트리 뷰어에서 제공하는 것과 동일한 정보를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ac0b-122">The same information that is provided by the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Generic Content Tree Viewer is also available by querying the mining model.</span></span> <span data-ttu-id="7ac0b-123">마이닝 모델 콘텐츠에 대한 쿼리는 DMX(Data Mining Extensions) 문을 사용하여 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ac0b-123">You can create queries against mining model content by using Data Mining Extensions (DMX) statements.</span></span> <span data-ttu-id="7ac0b-124">예를 들어 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 다음 DMX 문을 실행하여 내용 쿼리를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ac0b-124">For example, in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], you can run a content query by executing the following DMX statement:</span></span>  
  
```  
SELECT * FROM [<mining model name>].CONTENT  
```  
  
 <span data-ttu-id="7ac0b-125">자세한 내용은 [데이터 마이닝 쿼리](data-mining-queries.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7ac0b-125">For more information, see [Data Mining Queries](data-mining-queries.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ac0b-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7ac0b-126">See Also</span></span>  
 <span data-ttu-id="7ac0b-127">[Microsoft 일반 콘텐츠 트리 뷰어 &#40;데이터 마이닝&#41;](../microsoft-generic-content-tree-viewer-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="7ac0b-127">[Microsoft Generic Content Tree Viewer &#40;Data Mining&#41;](../microsoft-generic-content-tree-viewer-data-mining.md) </span></span>  
 [<span data-ttu-id="7ac0b-128">데이터 마이닝 알고리즘&#40;Analysis Services - 데이터 마이닝&#41;</span><span class="sxs-lookup"><span data-stu-id="7ac0b-128">Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;</span></span>](data-mining-algorithms-analysis-services-data-mining.md)  
  
  
