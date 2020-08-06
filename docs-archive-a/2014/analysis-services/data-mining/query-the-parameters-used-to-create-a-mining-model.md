---
title: 마이닝 모델을 만드는 데 사용 되는 매개 변수 쿼리 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- content queries [DMX]
ms.assetid: ce7719e0-6127-4d9c-a753-0e0a3db065e1
author: minewiskan
ms.author: owend
ms.openlocfilehash: a3802a0d70579f613accbe6abd310da909751b23
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87733327"
---
# <a name="query-the-parameters-used-to-create-a-mining-model"></a><span data-ttu-id="adcb5-102">마이닝 모델을 만드는 데 사용한 매개 변수 쿼리</span><span class="sxs-lookup"><span data-stu-id="adcb5-102">Query the Parameters Used to Create a Mining Model</span></span>
  <span data-ttu-id="adcb5-103">마이닝 모델의 컴퍼지션은 학습 사례의 영향을 받을 뿐만 아니라 모델을 만들 때 설정한 매개 변수의 영향도 받습니다.</span><span class="sxs-lookup"><span data-stu-id="adcb5-103">The composition of a mining model is affected not only by the training cases, but by the parameters that were set when the model was created.</span></span> <span data-ttu-id="adcb5-104">따라서 기존 모델의 매개 변수 설정을 검색하면 모델의 동작을 보다 잘 이해할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="adcb5-104">Therefore, you might find it useful to retrieve the parameter settings of an existing model to better understand the behavior of the model.</span></span> <span data-ttu-id="adcb5-105">매개 변수 검색은 해당 모델의 특정 버전을 문서화하는 데도 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="adcb5-105">Retrieving parameters is also useful when documenting a particular version of that model.</span></span>  
  
 <span data-ttu-id="adcb5-106">모델을 만들 때 사용한 매개 변수를 찾으려면 마이닝 모델 스키마 행 집합 중 하나에 대한 쿼리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="adcb5-106">To find the parameters that were used when the model was created, you create a query against one of the mining model schema rowsets.</span></span> <span data-ttu-id="adcb5-107">[!INCLUDE[ssASCurrent](../../includes/ssascurrent-md.md)]에서 이러한 스키마 행 집합은 Transact-SQL 구문을 사용하여 쉽게 쿼리할 수 있는 시스템 뷰 집합으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="adcb5-107">In [!INCLUDE[ssASCurrent](../../includes/ssascurrent-md.md)], these schema rowsets are exposed as a set of system views that you can query easily by using Transact-SQL syntax.</span></span> <span data-ttu-id="adcb5-108">이 절차에서는 지정된 마이닝 모델을 만드는 데 사용한 매개 변수를 반환하는 쿼리를 만드는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="adcb5-108">This procedure describes how to create a query that returns the parameters that were used to create the specified mining model.</span></span>  
  
### <a name="to-open-a-query-window-for-a-schema-rowset-query"></a><span data-ttu-id="adcb5-109">스키마 행 집합 쿼리에 대한 쿼리 창을 열려면</span><span class="sxs-lookup"><span data-stu-id="adcb5-109">To open a Query window for a schema rowset query</span></span>  
  
1.  <span data-ttu-id="adcb5-110">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 쿼리할 모델이 들어 있는 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="adcb5-110">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], open the instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] that contains the model you want to query.</span></span>  
  
2.  <span data-ttu-id="adcb5-111">인스턴스 이름을 마우스 오른쪽 단추로 클릭하여 **새 쿼리**를 선택한 다음 **DMX**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="adcb5-111">Right-click the instance name, select **New Query**, and then select **DMX**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="adcb5-112">**MDX** 템플릿을 사용하여 데이터 마이닝 모델에 대한 쿼리를 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="adcb5-112">You can also create a query against a data mining model by using the **MDX** template.</span></span>  
  
3.  <span data-ttu-id="adcb5-113">인스턴스에 여러 개의 데이터베이스가 포함되어 있는 경우 도구 모음의 **사용 가능한 데이터베이스** 목록에서 쿼리할 모델을 포함하는 데이터베이스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="adcb5-113">If the instance contains multiple databases, select the database that contains the model you want to query from the **Available Databases** list in the toolbar.</span></span>  
  
### <a name="to-return-model-parameters-for-an-existing-mining-model"></a><span data-ttu-id="adcb5-114">기존 마이닝 모델에 대한 모델 매개 변수를 반환하려면</span><span class="sxs-lookup"><span data-stu-id="adcb5-114">To return model parameters for an existing mining model</span></span>  
  
1.  <span data-ttu-id="adcb5-115">DMX 쿼리 창에서 다음 텍스트를 입력하거나 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="adcb5-115">In the DMX query pane, type or paste the following text:</span></span>  
  
    ```  
    SELECT MINING_PARAMETERS  
    FROM $system.DMSCHEMA_MINING_MODELS  
    WHERE MODEL_NAME = ''  
    ```  
  
2.  <span data-ttu-id="adcb5-116">개체 탐색기에서 원하는 마이닝 모델을 선택한 다음 DMX 쿼리 창의 작은따옴표 사이로 끌어 옵니다.</span><span class="sxs-lookup"><span data-stu-id="adcb5-116">In Object Explorer, select the mining model you want, and then drag it into the DMX Query pane, between the single quotation marks.</span></span>  
  
3.  <span data-ttu-id="adcb5-117">F5 키를 누르거나 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="adcb5-117">Press F5, or click **Execute**.</span></span>  
  
## <a name="example"></a><span data-ttu-id="adcb5-118">예제</span><span class="sxs-lookup"><span data-stu-id="adcb5-118">Example</span></span>  
 <span data-ttu-id="adcb5-119">다음 코드는 [Basic Data Mining Tutorial](../../tutorials/basic-data-mining-tutorial.md)에서 생성한 마이닝 모델을 만드는 데 사용한 매개 변수 목록을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="adcb5-119">The following code returns a list of the parameters that were used to create the mining model that you build in the [Basic Data Mining Tutorial](../../tutorials/basic-data-mining-tutorial.md).</span></span> <span data-ttu-id="adcb5-120">이러한 매개 변수에는 서버의 공급자가 제공하는 마이닝 서비스에 사용되는 기본값에 대한 명시적 값이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="adcb5-120">These parameters include the explicit values for any defaults used by the mining services available from providers on the server.</span></span>  
  
```  
SELECT MINING_PARAMETERS   
FROM $system.DMSCHEMA_MINING_MODELS  
WHERE MODEL_NAME = 'TM Clustering'  
```  
  
 <span data-ttu-id="adcb5-121">이 코드 예는 클러스터링 모델에 대해 다음 매개 변수를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="adcb5-121">The code example returns the following parameters for the clustering model:</span></span>  
  
 <span data-ttu-id="adcb5-122">예 결과:</span><span class="sxs-lookup"><span data-stu-id="adcb5-122">eExample Results:</span></span>  
  
 <span data-ttu-id="adcb5-123">MINING_PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="adcb5-123">MINING_PARAMETERS</span></span>  
  
 <span data-ttu-id="adcb5-124">CLUSTER_COUNT=10,CLUSTER_SEED=0,CLUSTERING_METHOD=1,MAXIMUM_INPUT_ATTRIBUTES=255,MAXIMUM_STATES=100,MINIMUM_SUPPORT=1,MODELLING_CARDINALITY=10,SAMPLE_SIZE=50000,STOPPING_TOLERANCE=10</span><span class="sxs-lookup"><span data-stu-id="adcb5-124">CLUSTER_COUNT=10,CLUSTER_SEED=0,CLUSTERING_METHOD=1,MAXIMUM_INPUT_ATTRIBUTES=255,MAXIMUM_STATES=100,MINIMUM_SUPPORT=1,MODELLING_CARDINALITY=10,SAMPLE_SIZE=50000,STOPPING_TOLERANCE=10</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="adcb5-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="adcb5-125">See Also</span></span>  
 <span data-ttu-id="adcb5-126">[데이터 마이닝 쿼리 태스크 및 방법](data-mining-query-tasks-and-how-tos.md) </span><span class="sxs-lookup"><span data-stu-id="adcb5-126">[Data Mining Query Tasks and How-tos](data-mining-query-tasks-and-how-tos.md) </span></span>  
 [<span data-ttu-id="adcb5-127">데이터 마이닝 쿼리</span><span class="sxs-lookup"><span data-stu-id="adcb5-127">Data Mining Queries</span></span>](data-mining-queries.md)  
  
  
