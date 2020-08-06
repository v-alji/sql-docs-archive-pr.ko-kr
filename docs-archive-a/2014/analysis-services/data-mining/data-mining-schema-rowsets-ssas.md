---
title: 데이터 마이닝 스키마 행 집합 쿼리 (Analysis Services 데이터 마이닝) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- schema rowsets [Analysis Services], data mining
- data mining [Analysis Services], queries
- mining model content
- data mining [Analysis Services], schema rowsets
- schema rowsets [Analysis Services], retrieving
- data mining [Analysis Services], troubleshooting
ms.assetid: 442d8c29-07c7-45de-9a15-d556059f68d7
author: minewiskan
ms.author: owend
ms.openlocfilehash: d60c802256454ee68d04392e685fa4acabf6c12e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653674"
---
# <a name="querying-the-data-mining-schema-rowsets-analysis-services---data-mining"></a><span data-ttu-id="7874c-102">데이터 마이닝 스키마 행 집합 쿼리(Analysis Services - 데이터 마이닝)</span><span class="sxs-lookup"><span data-stu-id="7874c-102">Querying the Data Mining Schema Rowsets (Analysis Services - Data Mining)</span></span>
  <span data-ttu-id="7874c-103">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]에는 기존 OLE DB 데이터 마이닝 스키마 행 집합 대부분이 DMX(Data Mining Extensions) 문을 사용하여 쿼리할 수 있는 시스템 테이블 집합으로 노출됩니다.</span><span class="sxs-lookup"><span data-stu-id="7874c-103">In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], many of the existing OLE DB data mining schema rowsets are exposed as a set of system tables that you can query by using Data Mining Extensions (DMX) statements.</span></span> <span data-ttu-id="7874c-104">데이터 마이닝 스키마 행 집합을 대상으로 쿼리를 작성하면 사용할 수 있는 서비스를 식별하고, 모델과 구조의 상태에 대한 업데이트를 가져오고, 모델 콘텐츠나 매개 변수에 대한 정보를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7874c-104">By creating queries against the data mining schema rowset, you can identify the services that are available, get updates on the status of your models and structures, and find out details about the model content or parameters.</span></span> <span data-ttu-id="7874c-105">데이터 마이닝 스키마 행 집합에 대한 설명은 [Data Mining Schema Rowsets](../../relational-databases/native-client-ole-db-rowsets/rowsets.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="7874c-105">For a description of the data mining schema rowsets, see [Data Mining Schema Rowsets](../../relational-databases/native-client-ole-db-rowsets/rowsets.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7874c-106">XMLA를 사용하여 데이터 마이닝 스키마 행 집합을 쿼리할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7874c-106">You can also query the data mining schema rowsets by using XMLA.</span></span> <span data-ttu-id="7874c-107">SQL Server Management Studio에서 이 작업을 수행하는 방법에 대한 자세한 내용은 [XMLA를 사용하여 데이터 마이닝 쿼리 만들기](create-a-data-mining-query-by-using-xmla.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7874c-107">For more information about how to do this in SQL Server Management Studio, see [Create a Data Mining Query by Using XMLA](create-a-data-mining-query-by-using-xmla.md).</span></span>  
  
## <a name="list-of-data-mining-schema-rowsets"></a><span data-ttu-id="7874c-108">데이터 마이닝 스키마 행 집합 목록</span><span class="sxs-lookup"><span data-stu-id="7874c-108">List of Data Mining Schema Rowsets</span></span>  
 <span data-ttu-id="7874c-109">다음 표에서는 쿼리 및 모니터링하는 데 유용한 데이터 마이닝 스키마 행 집합의 목록을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7874c-109">The following table lists the data mining schema rowsets that may be useful for querying and monitoring.</span></span>  
  
|<span data-ttu-id="7874c-110">행 집합 이름</span><span class="sxs-lookup"><span data-stu-id="7874c-110">Rowset name</span></span>|<span data-ttu-id="7874c-111">Description</span><span class="sxs-lookup"><span data-stu-id="7874c-111">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="7874c-112">DMSCHEMA_MINING_MODELS</span><span class="sxs-lookup"><span data-stu-id="7874c-112">DMSCHEMA_MINING_MODELS</span></span>|<span data-ttu-id="7874c-113">현재 컨텍스트의 모든 마이닝 모델을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="7874c-113">Lists all mining models in the current context.</span></span><br /><br /> <span data-ttu-id="7874c-114">여기에는 만든 날짜, 모델을 만드는 데 사용된 매개 변수 및 학습 집합의 크기와 같은 정보가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="7874c-114">Includes such information as the date created, parameters used to create the model, and the size of the training set.</span></span>|  
|<span data-ttu-id="7874c-115">DMSCHEMA_MINING_COLUMNS</span><span class="sxs-lookup"><span data-stu-id="7874c-115">DMSCHEMA_MINING_COLUMNS</span></span>|<span data-ttu-id="7874c-116">현재 컨텍스트의 마이닝 모델에 사용된 모든 열을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="7874c-116">Lists all columns used in mining models in the current context.</span></span><br /><br /> <span data-ttu-id="7874c-117">마이닝 구조 원본 열에 대한 매핑, 데이터 형식, 전체 자릿수, 열에 사용할 수 있는 예측 함수 등의 정보가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="7874c-117">Information includes mapping to mining structure source column, data type, precision, and prediction functions that can be used with the column.</span></span>|  
|<span data-ttu-id="7874c-118">DMSCHEMA_MINING_STRUCTURES</span><span class="sxs-lookup"><span data-stu-id="7874c-118">DMSCHEMA_MINING_STRUCTURES</span></span>|<span data-ttu-id="7874c-119">현재 컨텍스트의 모든 마이닝 구조를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="7874c-119">Lists all mining structure in the current context.</span></span><br /><br /> <span data-ttu-id="7874c-120">구조가 채워졌는지 여부, 구조가 마지막으로 처리된 날짜, 구조에 대해 지정된 홀드아웃 데이터 집합 정의(있는 경우) 등의 정보가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="7874c-120">Information includes whether the structure is populated, the date the structure was last processed, and the definition of the holdout data set for the structure, if any.</span></span>|  
|<span data-ttu-id="7874c-121">DMSCHEMA_MINING_STRUCTURE_COLUMNS</span><span class="sxs-lookup"><span data-stu-id="7874c-121">DMSCHEMA_MINING_STRUCTURE_COLUMNS</span></span>|<span data-ttu-id="7874c-122">현재 컨텍스트의 마이닝 구조에 사용된 모든 열을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="7874c-122">Lists all columns used in mining structures in the current context.</span></span><br /><br /> <span data-ttu-id="7874c-123">내용 유형과 데이터 형식, null 허용 여부, 열에 중첩 테이블 데이터가 포함되었는지 여부 등의 정보가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="7874c-123">Information includes content type and data type, nullability, and whether the column contains nested table data.</span></span>|  
|<span data-ttu-id="7874c-124">DMSCHEMA_MINING_SERVICES</span><span class="sxs-lookup"><span data-stu-id="7874c-124">DMSCHEMA_MINING_SERVICES</span></span>|<span data-ttu-id="7874c-125">지정된 서버에서 사용할 수 있는 모든 마이닝 서비스나 알고리즘을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="7874c-125">Lists all mining services, or algorithms, that are available on the specified server.</span></span><br /><br /> <span data-ttu-id="7874c-126">지원되는 모델링 플래그, 입력 유형, 지원되는 데이터 원본 유형 등의 정보가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="7874c-126">Information includes supported modeling flags, input types, and supported data source types.</span></span>|  
|<span data-ttu-id="7874c-127">DMSCHEMA_MINING_SERVICE_PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="7874c-127">DMSCHEMA_MINING_SERVICE_PARAMETERS</span></span>|<span data-ttu-id="7874c-128">현재 인스턴스에서 사용할 수 있는 마이닝 서비스의 모든 매개 변수를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="7874c-128">Lists all parameters for the mining services that are available on the current instance.</span></span><br /><br /> <span data-ttu-id="7874c-129">각 매개 변수의 데이터 형식, 기본값, 상한 및 하한 등의 정보가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="7874c-129">Information includes the data type for each parameter, the default values, and the upper and lower limits.</span></span>|  
|<span data-ttu-id="7874c-130">DMSCHEMA_MODEL_CONTENT</span><span class="sxs-lookup"><span data-stu-id="7874c-130">DMSCHEMA_MODEL_CONTENT</span></span>|<span data-ttu-id="7874c-131">모델이 처리된 경우 모델의 내용을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="7874c-131">Returns the content of the model if the model has been processed.</span></span><br /><br /> <span data-ttu-id="7874c-132">자세한 내용은 [마이닝 모델 콘텐츠&#40;Analysis Services - 데이터 마이닝&#41;](mining-model-content-analysis-services-data-mining.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7874c-132">For more information, see [Mining Model Content &#40;Analysis Services - Data Mining&#41;](mining-model-content-analysis-services-data-mining.md).</span></span>|  
|<span data-ttu-id="7874c-133">DBSCHEMA_CATALOGS</span><span class="sxs-lookup"><span data-stu-id="7874c-133">DBSCHEMA_CATALOGS</span></span>|<span data-ttu-id="7874c-134">Analysis Services의 현재 인스턴스에 포함된 모든 데이터베이스(카탈로그)를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="7874c-134">Lists all databases (catalogs) in the current instance of Analysis Services.</span></span>|  
|<span data-ttu-id="7874c-135">MDSCHEMA_INPUT_DATASOURCES</span><span class="sxs-lookup"><span data-stu-id="7874c-135">MDSCHEMA_INPUT_DATASOURCES</span></span>|<span data-ttu-id="7874c-136">Analysis Services의 현재 인스턴스에 포함된 모든 데이터 원본을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="7874c-136">Lists all data sources in the current instance of Analysis Services.</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="7874c-137">이 표의 목록에 포함된 행 집합은 일부에 불과하며 여기에는 문제 해결에 가장 도움이 될 수 있는 행 집합만 나열되었습니다.</span><span class="sxs-lookup"><span data-stu-id="7874c-137">The list in the table is not comprehensive; it shows only those rowsets that may be of most interest for troubleshooting.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="7874c-138">예</span><span class="sxs-lookup"><span data-stu-id="7874c-138">Examples</span></span>  
 <span data-ttu-id="7874c-139">다음 섹션에서는 데이터 마이닝 스키마 행 집합에 대한 몇 가지 쿼리 예를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="7874c-139">The following section provides some examples of queries against the data mining schema rowsets.</span></span>  
  
### <a name="example-1-list-data-mining-services"></a><span data-ttu-id="7874c-140">예 1: 데이터 마이닝 서비스 나열</span><span class="sxs-lookup"><span data-stu-id="7874c-140">Example 1: List Data Mining Services</span></span>  
 <span data-ttu-id="7874c-141">다음 쿼리는 현재 서버에서 사용할 수 있는 마이닝 서비스, 즉 설정되어 있는 알고리즘의 목록을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="7874c-141">The following query returns a list of the mining services that are available on the current server, meaning the algorithms that are enabled.</span></span> <span data-ttu-id="7874c-142">각 마이닝 서비스에 대해 제공되는 열에는 각 알고리즘에 사용될 수 있는 모델링 플래그와 내용 유형, 각 서비스의 GUID 및 각 서비스에 추가되었을 수 있는 예측 제한이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="7874c-142">The columns provided for each mining service include the modeling flags and content types that can be used by each algorithm, the GUID for each service, and any prediction limits that may have been added for each service.</span></span>  
  
```  
SELECT *  
FROM $system.DMSCHEMA_MINING_SERVICES  
```  
  
### <a name="example-2-list-mining-model-parameters"></a><span data-ttu-id="7874c-143">예 2: 마이닝 모델 매개 변수 나열</span><span class="sxs-lookup"><span data-stu-id="7874c-143">Example 2: List Mining Model Parameters</span></span>  
 <span data-ttu-id="7874c-144">다음 예는 특정 마이닝 모델을 만드는 데 사용된 매개 변수를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="7874c-144">The following example returns the parameters that were used to create a specific mining model:</span></span>  
  
```  
SELECT MINING_PARAMETERS   
FROM $system.DMSCHEMA_MINING_MODELS  
WHERE MODEL_NAME = 'TM Clustering'  
```  
  
### <a name="example-3-list-all-rowsets"></a><span data-ttu-id="7874c-145">예 3: 모든 행 집합 나열</span><span class="sxs-lookup"><span data-stu-id="7874c-145">Example 3: List All Rowsets</span></span>  
 <span data-ttu-id="7874c-146">다음 예에서는 현재 서버에서 사용할 수 있는 행 집합의 전체 목록을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="7874c-146">The following example returns a comprehensive list of the rowsets that are available on the current server:</span></span>  
  
```  
SELECT *   
FROM $system.DBSCHEMA_TABLES  
```  
  
## <a name="see-also"></a><span data-ttu-id="7874c-147">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7874c-147">See Also</span></span>  
 [<span data-ttu-id="7874c-148">문제 해결 개념(Analysis Services - 데이터 마이닝)</span><span class="sxs-lookup"><span data-stu-id="7874c-148">Troubleshooting Concepts (Analysis Services - Data Mining)</span></span>](https://msdn.microsoft.com/library/cc645881.aspx)  
  
  
