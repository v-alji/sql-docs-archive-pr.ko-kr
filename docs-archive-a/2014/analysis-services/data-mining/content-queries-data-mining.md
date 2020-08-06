---
title: 내용 쿼리 (데이터 마이닝) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: c4f4a5a8-a230-4222-bece-9d563501f65f
author: minewiskan
ms.author: owend
ms.openlocfilehash: 44b162c34f5f505462a713205d8434484473afa4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661430"
---
# <a name="content-queries-data-mining"></a><span data-ttu-id="bd903-102">내용 쿼리(데이터 마이닝)</span><span class="sxs-lookup"><span data-stu-id="bd903-102">Content Queries (Data Mining)</span></span>
  <span data-ttu-id="bd903-103">내용 쿼리는 마이닝 모델의 내부 통계와 구조에 대한 정보를 추출하는 한 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="bd903-103">A content query is a way of extracting information about the internal statistics and structure of the mining model.</span></span> <span data-ttu-id="bd903-104">내용 쿼리는 때때로 뷰어에서 쉽게 사용할 수 없는 세부 정보를 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd903-104">Sometimes a content query can provide details that are not readily available in the viewer.</span></span> <span data-ttu-id="bd903-105">내용 쿼리의 결과를 사용하여 다른 용도로 사용할 정보를 프로그래밍 방식으로 추출할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd903-105">You can also use the results of a content query to extract information programmatically for other uses.</span></span>  
  
 <span data-ttu-id="bd903-106">이 섹션에서는 내용 쿼리 및 내용 쿼리에 대한 일반 DMX 구문을 사용하여 검색할 수 있는 정보의 유형에 대한 일반적인 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="bd903-106">This section provides general information about the types of information that you can retrieve by using a content query, and the general DMX syntax for content queries.</span></span>  
  
 [<span data-ttu-id="bd903-107">기본 내용 쿼리</span><span class="sxs-lookup"><span data-stu-id="bd903-107">Basic Content Queries</span></span>](#bkmk_ContentQuery)  
  
-   [<span data-ttu-id="bd903-108">구조 및 사례 데이터에 대 한 쿼리</span><span class="sxs-lookup"><span data-stu-id="bd903-108">Queries on Structure and Case Data</span></span>](#bkmk_Structure)  
  
-   [<span data-ttu-id="bd903-109">모델 패턴에 대한 쿼리</span><span class="sxs-lookup"><span data-stu-id="bd903-109">Queries on Model Patterns</span></span>](#bkmk_Patterns)  
  
 [<span data-ttu-id="bd903-110">예</span><span class="sxs-lookup"><span data-stu-id="bd903-110">Examples</span></span>](#bkmk_Examples)  
  
-   [<span data-ttu-id="bd903-111">연결 모델에 대한 내용 쿼리</span><span class="sxs-lookup"><span data-stu-id="bd903-111">Content Query on an Association Model</span></span>](#bkmk_Assoc)  
  
-   [<span data-ttu-id="bd903-112">의사 결정 트리 모델에 대한 내용 쿼리</span><span class="sxs-lookup"><span data-stu-id="bd903-112">Content Query on a Decision Trees Model</span></span>](#bkmk_DecTree)  
  
 [<span data-ttu-id="bd903-113">쿼리 결과 작업</span><span class="sxs-lookup"><span data-stu-id="bd903-113">Working with the Query Results</span></span>](#bkmk_Results)  
  
##  <a name="basic-content-queries"></a><a name="bkmk_ContentQuery"></a><span data-ttu-id="bd903-114">기본 내용 쿼리</span><span class="sxs-lookup"><span data-stu-id="bd903-114">Basic Content Queries</span></span>  
 <span data-ttu-id="bd903-115">예측 쿼리 작성기를 사용하여 내용 쿼리를 만들거나, SQL Server Management Studio에 제공되는 DMX 내용 쿼리 템플릿을 사용하거나, DMX에서 쿼리를 직접 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd903-115">You can create content queries by using the Prediction Query Builder, use the DMX content query templates that are provided in SQL Server Management Studio, or write queries directly in DMX.</span></span> <span data-ttu-id="bd903-116">예측 쿼리와 달리 외부 데이터를 조인할 필요가 없으므로 내용 쿼리를 쉽게 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd903-116">Unlike prediction queries you do not need to join external data, so content queries are easy to write.</span></span>  
  
 <span data-ttu-id="bd903-117">이 섹션에서는 만들 수 있는 내용 쿼리의 유형에 대한 개요를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="bd903-117">This section provides an overview of the types of content queries you can create.</span></span>  
  
-   <span data-ttu-id="bd903-118">마이닝 구조 또는 사례 데이터에 대한 쿼리를 통해 학습에 사용된 세부 데이터를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd903-118">Queries on the mining structure or case data let you view the detailed data that was used for training.</span></span>  
  
-   <span data-ttu-id="bd903-119">모델에 대한 쿼리는 패턴, 특성 목록, 수식 등을 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd903-119">Queries on the model can return patterns, lists of attributes, formulas, and so forth.</span></span>  
  
###  <a name="queries-on-structure-and-case-data"></a><a name="bkmk_Structure"></a> <span data-ttu-id="bd903-120">구조 및 사례 데이터에 대한 쿼리</span><span class="sxs-lookup"><span data-stu-id="bd903-120">Queries on Structure and Case Data</span></span>  
 <span data-ttu-id="bd903-121">DMX는 마이닝 구조와 마이닝 모델을 작성하는 데 사용되는 캐시된 데이터에 대한 쿼리를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="bd903-121">DMX supports queries on the cached data that is used to build mining structures and models.</span></span> <span data-ttu-id="bd903-122">기본적으로 이 캐시는 마이닝 구조를 정의할 때 만들어지고 구조 또는 모델을 처리할 때 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="bd903-122">By default, this cache is created when you define the mining structure, and is populated when you process the structure or model.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="bd903-123">데이터를 학습 및 테스트 집합으로 분리해야 할 경우 이 캐시를 지우거나 삭제할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="bd903-123">This cache cannot be cleared or deleted if you need to separate data into training and testing sets.</span></span> <span data-ttu-id="bd903-124">캐시를 지울 경우 사례 데이터를 쿼리할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="bd903-124">If the cache is cleared, you cannot query the case data.</span></span>  
  
 <span data-ttu-id="bd903-125">다음 예에서는 사례 데이터에 대한 쿼리나 마이닝 구조의 데이터에 대한 쿼리를 만들기 위한 일반적인 패턴을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="bd903-125">The following examples show the common patterns for creating queries on the case data, or queries on the data in the mining structure:</span></span>  
  
 <span data-ttu-id="bd903-126">**모델에 대한 모든 사례 가져오기**</span><span class="sxs-lookup"><span data-stu-id="bd903-126">**Get all the cases for a model**</span></span>  
 `SELECT FROM <model>.CASES`  
  
 <span data-ttu-id="bd903-127">이 문을 사용하여 모델을 작성하는 데 사용되는 사례 데이터에서 지정된 열을 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd903-127">Use this statement to retrieve specified columns from the case data used to build a model.</span></span> <span data-ttu-id="bd903-128">이 쿼리를 실행하려면 모델에 대한 드릴스루 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd903-128">You must have drillthrough permissions on the model to run this query.</span></span>  
  
 <span data-ttu-id="bd903-129">**구조에 포함된 모든 데이터 보기**</span><span class="sxs-lookup"><span data-stu-id="bd903-129">**View all the data that is included in the structure**</span></span>  
 `SELECT FROM <structure>.CASES`  
  
 <span data-ttu-id="bd903-130">이 문을 사용하면 특정 마이닝 모델에 포함되지 않은 열을 포함하여 구조에 포함된 모든 데이터를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd903-130">Use this statement to view all the data that is included in the structure, including columns that are not included in a particular mining model.</span></span> <span data-ttu-id="bd903-131">마이닝 구조에서 데이터를 검색하려면 모델과 구조 모두에 대한 드릴스루 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd903-131">You must have drillthrough permissions on the model, as well as on the structure, to retrieve data from the mining structure.</span></span>  
  
 <span data-ttu-id="bd903-132">**값 범위 가져오기**</span><span class="sxs-lookup"><span data-stu-id="bd903-132">**Get range of values**</span></span>  
 `SELECT DISTINCT RangeMin(<column>), RangeMax(<column>) FROM <model>`  
  
 <span data-ttu-id="bd903-133">이 문을 사용하여 연속 열 또는 불연속화 열 버킷의 최소값, 최대값 및 평균을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd903-133">Use this statement to find the minimum value, maximum value, and mean of a continuous column, or of the buckets of a DISCRETIZED column.</span></span>  
  
 <span data-ttu-id="bd903-134">**고유 값 가져오기**</span><span class="sxs-lookup"><span data-stu-id="bd903-134">**Get distinct values**</span></span>  
 `SELECT DISTINCT <column>FROM <model>`  
  
 <span data-ttu-id="bd903-135">이 문을 사용하여 불연속 열의 모든 값을 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd903-135">Use this statement to retrieve all the values of a DISCRETE column.</span></span>  <span data-ttu-id="bd903-136">불연속화 열에 이 문을 사용하지 마십시오. 대신 `RangeMin` 및 `RangeMax` 함수를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd903-136">Do not use this statement for DISCRETIZED columns; use the `RangeMin` and `RangeMax` functions instead.</span></span>  
  
 <span data-ttu-id="bd903-137">**모델 또는 구조를 학습하는 데 사용된 사례 찾기**</span><span class="sxs-lookup"><span data-stu-id="bd903-137">**Find the cases that were used to train a model or structure**</span></span>  
 `SELECT  FROM <mining structure.CASES WHERE IsTrainingCase()`  
  
 <span data-ttu-id="bd903-138">이 문을 사용하여 모델을 학습하는 데 사용된 전체 데이터 집합을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd903-138">Use this statement to get the complete set of data that was used in a training a model.</span></span>  
  
 <span data-ttu-id="bd903-139">**모델 또는 구조를 테스트하는 데 사용되는 사례 찾기**</span><span class="sxs-lookup"><span data-stu-id="bd903-139">**Find the cases that are used for testing a model or structure**</span></span>  
 `SELECT  FROM <mining structure.CASES WHERE IsTestingCase()`  
  
 <span data-ttu-id="bd903-140">이 문을 사용하여 특정 구조와 관련된 마이닝 모델의 테스트를 위해 따로 설정된 데이터를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd903-140">Use this statement to get the data that has been set aside for testing mining models related to a specific structure.</span></span>  
  
 <span data-ttu-id="bd903-141">**특정 모델 패턴에서 기본 사례 데이터로 드릴스루**</span><span class="sxs-lookup"><span data-stu-id="bd903-141">**Drillthrough from a specific model pattern to underlying case data**</span></span>  
 `SELECT FROM <model>.CASESWHERE IsTrainingCase() AND IsInNode(<node>)`  
  
 <span data-ttu-id="bd903-142">이 문을 사용하여 학습된 모델에서 자세한 사례 데이터를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd903-142">Use this statement to retrieve detailed case data from a trained model.</span></span> <span data-ttu-id="bd903-143">특정 노드를 지정해야 합니다. 예를 들어 클러스터, 의사 결정 트리의 특정 분기 등의 노드 ID를 알아야 합니다. 이뿐만 아니라 이 쿼리를 실행하려면 모델에 대한 드릴스루 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd903-143">You must specify a specific node: for example, you must know the node ID of the cluster, the specific branch of the decision tree, etc. Moreover, you must have drillthrough permissions on the model to run this query.</span></span>  
  
###  <a name="queries-on-model-patterns-statistics-and-attributes"></a><a name="bkmk_Patterns"></a><span data-ttu-id="bd903-144">모델 패턴, 통계 및 특성에 대 한 쿼리</span><span class="sxs-lookup"><span data-stu-id="bd903-144">Queries on Model Patterns, Statistics, and Attributes</span></span>  
 <span data-ttu-id="bd903-145">데이터 마이닝 모델의 콘텐츠는 다양한 용도로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="bd903-145">The content of a data mining model is useful for many purposes.</span></span> <span data-ttu-id="bd903-146">모델 내용 쿼리를 사용하여 다음을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd903-146">With a model content query, you can:</span></span>  
  
-   <span data-ttu-id="bd903-147">사용자 고유의 계산을 만들기 위해 수식 또는 확률 추출</span><span class="sxs-lookup"><span data-stu-id="bd903-147">Extract formulas or probabilities for making your own calculations.</span></span>  
  
-   <span data-ttu-id="bd903-148">연결 모델의 경우 예측을 생성하는 데 사용되는 규칙 검색</span><span class="sxs-lookup"><span data-stu-id="bd903-148">For an association model, retrieve the rules that are used to generate a prediction.</span></span>  
  
-   <span data-ttu-id="bd903-149">사용자 지정 애플리케이션에서 규칙을 사용할 수 있도록 특정 규칙에 대한 설명 검색</span><span class="sxs-lookup"><span data-stu-id="bd903-149">Retrieve the descriptions of specific rules so that you can use the rules in a custom application.</span></span>  
  
-   <span data-ttu-id="bd903-150">시계열 모델에 의해 검색되는 이동 평균 보기</span><span class="sxs-lookup"><span data-stu-id="bd903-150">View the moving averages detected by a time series model.</span></span>  
  
-   <span data-ttu-id="bd903-151">추세 선의 일부 세그먼트에 대한 회귀 수식 구하기</span><span class="sxs-lookup"><span data-stu-id="bd903-151">Obtain the regression formula for some segment of the trend line.</span></span>  
  
-   <span data-ttu-id="bd903-152">특정 클러스터의 일부로 식별되는 고객에 대한 동작 가능한 정보 검색</span><span class="sxs-lookup"><span data-stu-id="bd903-152">Retrieve actionable information about customers identified as being part of a specific cluster.</span></span>  
  
 <span data-ttu-id="bd903-153">다음 예에서는 모델 콘텐츠에 대한 쿼리를 만들기 위한 일반적인 패턴을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="bd903-153">The following examples show some of the common patterns for creating queries on the model content:</span></span>  
  
 <span data-ttu-id="bd903-154">**모델에서 패턴 가져오기**</span><span class="sxs-lookup"><span data-stu-id="bd903-154">**Get patterns from the model**</span></span>  
 `SELECT FROM <model>.CONTENT`  
  
 <span data-ttu-id="bd903-155">이 문을 사용하여 모델의 특정 노드에 대한 자세한 정보를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd903-155">Use this statement to retrieve detailed information about specific nodes in the model.</span></span> <span data-ttu-id="bd903-156">알고리즘 유형에 따라 노드는 규칙과 수식, 지지도 및 분산 통계 등을 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd903-156">Depending on the algorithm type, the node can contain rules and formulas, support and variance statistics, and so forth.</span></span>  
  
 <span data-ttu-id="bd903-157">**훈련된 모델에 사용된 특성 검색**</span><span class="sxs-lookup"><span data-stu-id="bd903-157">**Retrieve attributes used in a trained model**</span></span>  
 `CALL System.GetModelAttributes(<model>)`  
  
 <span data-ttu-id="bd903-158">이 저장 프로시저를 사용하여 모델에 사용된 특성 목록을 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd903-158">Use this stored procedure to retrieve the list of attributes that were used by a model.</span></span> <span data-ttu-id="bd903-159">예를 들어 이 정보는 기능 선택의 결과로 제거된 특성을 결정하는 데 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="bd903-159">This information is useful for determining attributes that were eliminated as a result of feature selection, for example.</span></span>  
  
 <span data-ttu-id="bd903-160">**데이터 마이닝 차원에 저장된 콘텐츠 검색**</span><span class="sxs-lookup"><span data-stu-id="bd903-160">**Retrieve content stored in a data mining dimension**</span></span>  
 `SELECT FROM <model>.DIMENSIONCONTENT`  
  
 <span data-ttu-id="bd903-161">이 문을 사용하여 데이터 마이닝 차원에서 데이터를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd903-161">Use this statement to retrieve the data from a data mining dimension.</span></span>  
  
 <span data-ttu-id="bd903-162">이 쿼리 유형은 주로 내부용입니다.</span><span class="sxs-lookup"><span data-stu-id="bd903-162">This query type is principally for internal use.</span></span> <span data-ttu-id="bd903-163">이 기능을 지원하지 않는 알고리즘도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd903-163">However, not all algorithms support this functionality.</span></span> <span data-ttu-id="bd903-164">지원 여부는 MINING_SERVICES 스키마 행 집합에 플래그로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="bd903-164">Support is indicated by a flag in the MINING_SERVICES schema rowset.</span></span>  
  
 <span data-ttu-id="bd903-165">사용자 고유의 플러그 인 알고리즘을 개발할 경우 이 문을 사용하여 테스트할 모델의 콘텐츠를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd903-165">If you develop your own plug-in algorithm, you might use this statement to verify the content of your model for testing.</span></span>  
  
 <span data-ttu-id="bd903-166">**모델의 PMML 표현 가져오기**</span><span class="sxs-lookup"><span data-stu-id="bd903-166">**Get the PMML representation of a model**</span></span>  
 `SELECT * FROM <model>.PMML`  
  
 <span data-ttu-id="bd903-167">PMML 형식으로 모델을 표현하는 XML 문서를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="bd903-167">Gets an XML document that represents the model in PMML format.</span></span> <span data-ttu-id="bd903-168">일부 모델 유형은 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bd903-168">Not all model types are supported.</span></span>  
  
##  <a name="examples"></a><a name="bkmk_Examples"></a> <span data-ttu-id="bd903-169">예</span><span class="sxs-lookup"><span data-stu-id="bd903-169">Examples</span></span>  
 <span data-ttu-id="bd903-170">일부 모델 콘텐츠는 모든 알고리즘에 적용되는 표준이지만, 콘텐츠의 일부 부분은 모델을 작성하는 데 사용한 알고리즘에 따라 크게 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="bd903-170">Although some model content is standard across algorithms, some parts of the content vary greatly depending on the algorithm that you used to build the model.</span></span> <span data-ttu-id="bd903-171">따라서 내용 쿼리를 만들 때 특정 모델에 가장 유용한 정보를 알고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd903-171">Therefore, when you create a content query, you must understand what information in the model is most useful to your specific model.</span></span>  
  
 <span data-ttu-id="bd903-172">선택한 알고리즘이 모델에 저장된 정보의 종류에 어떠한 영향을 미치는지를 보여 주는 몇 가지 예가 이 섹션에서 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="bd903-172">A few examples are provided in this section to illustrate how the choice of algorithm affects the kind of information that is stored in the model.</span></span> <span data-ttu-id="bd903-173">마이닝 모델 콘텐츠 및 각 모델 유형에 지정된 콘텐츠에 대한 자세한 내용은 [마이닝 모델 콘텐츠&#40;Analysis Services - 데이터 마이닝&#41;](mining-model-content-analysis-services-data-mining.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="bd903-173">For more information about mining model content, and the content that is specific to each model type, see [Mining Model Content &#40;Analysis Services - Data Mining&#41;](mining-model-content-analysis-services-data-mining.md).</span></span>  
  
###  <a name="example-1-content-query-on-an-association-model"></a><a name="bkmk_Assoc"></a> <span data-ttu-id="bd903-174">예 1: 연결 모델에 대한 내용 쿼리</span><span class="sxs-lookup"><span data-stu-id="bd903-174">Example 1: Content Query on an Association Model</span></span>  
 <span data-ttu-id="bd903-175">`SELECT FROM <model>.CONTENT`문은 쿼리하는 모델의 유형에 따라 서로 다른 종류의 정보를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="bd903-175">The statement, `SELECT FROM <model>.CONTENT`, returns different kinds of information, depending on the type of model you are querying.</span></span> <span data-ttu-id="bd903-176">연결 모델의 경우 주요 정보는 *노드 유형*입니다.</span><span class="sxs-lookup"><span data-stu-id="bd903-176">For an association model, a key piece of information is the *node type*.</span></span> <span data-ttu-id="bd903-177">노드는 모델 콘텐츠의 정보에 대한 컨테이너와 같습니다.</span><span class="sxs-lookup"><span data-stu-id="bd903-177">Nodes are like containers for information in the model content.</span></span> <span data-ttu-id="bd903-178">연결 모델에서 규칙을 나타내는 노드에는 NODE_TYPE 값 8이 있지만 항목 집합을 나타내는 노드에는 NODE_TYPE 값 7이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd903-178">In an association model, nodes that represent rules have a NODE_TYPE value of 8, whereas nodes that represent itemsets have a NODE_TYPE value of 7.</span></span>  
  
 <span data-ttu-id="bd903-179">따라서 다음 쿼리는 지지도 순으로 순위가 지정된(기본 순서) 상위 10개 항목 집합을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="bd903-179">Thus, the following query returns the top 10 itemsets, ranked by support (the default ordering).</span></span>  
  
```  
SELECT TOP 10 NODE_DESCRIPTION, NODE_PROBABILITY, SUPPORT  
FROM <model>.CONTENT WHERE NODE_TYPE = 7  
```  
  
 <span data-ttu-id="bd903-180">다음 쿼리는 이 정보를 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd903-180">The following query builds on this information.</span></span> <span data-ttu-id="bd903-181">이 쿼리는 노드의 ID, 전체 규칙, 항목 집합의 오른쪽에 있는 제품 즉, 항목 집합의 일부로 서 일부 다른 제품과 연결 될 것으로 예측 되는 제품의 세 열을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd903-181">The query returns three columns: the ID of the node, the complete rule, and the product on the right-hand side of the itemset-that is, the product that is predicted to be associated with some other products as part of an itemset.</span></span>  
  
```  
SELECT FLATTENED NODE_UNIQUE_NAME, NODE_DESCRIPTION,  
     (SELECT RIGHT(ATTRIBUTE_NAME, (LEN(ATTRIBUTE_NAME)-LEN('Association model name')))   
FROM NODE_DISTRIBUTION  
WHERE LEN(ATTRIBUTE_NAME)>2  
)   
AS RightSideProduct  
FROM [<Association model name>].CONTENT  
WHERE NODE_TYPE = 8   
ORDER BY NODE_SUPPORT DESC  
```  
  
 <span data-ttu-id="bd903-182">FLATTENED 키워드는 중첩 행 집합을 플랫 테이블로 변환해야 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="bd903-182">The FLATTENED keyword indicates that the nested rowset should be converted into a flattened table.</span></span> <span data-ttu-id="bd903-183">규칙의 오른쪽에 있는 제품을 나타내는 특성은 NODE_DISTRIBUTION 테이블에 포함되어 있습니다. 따라서 길이가 2보다 커야 한다는 요구 사항을 추가하여 특성 이름을 포함하는 행만 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="bd903-183">The attribute that represents the product on the right-hand side of the rule is contained in the NODE_DISTRIBUTION table; therefore, we retrieve only the row that contains an attribute name, by adding a requirement that the length be greater than 2.</span></span>  
  
 <span data-ttu-id="bd903-184">단순 문자열 함수는 세 번째 열에서 모델 이름을 제거하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="bd903-184">A simple string function is used to remove the name of the model from the third column.</span></span> <span data-ttu-id="bd903-185">일반적으로 모델 이름은 중첩 열 값의 앞에 옵니다.</span><span class="sxs-lookup"><span data-stu-id="bd903-185">(Usually the model name is prefixed to the values of nested columns.)</span></span>  
  
 <span data-ttu-id="bd903-186">WHERE 절은 규칙만 검색하기 위해 NODE_TYPE 값을 8로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="bd903-186">The WHERE clause specifies that the value of NODE_TYPE should be 8, to retrieve only rules.</span></span>  
  
 <span data-ttu-id="bd903-187">자세한 내용은 [연결 모델 쿼리 예제](association-model-query-examples.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="bd903-187">For more examples, see [Association Model Query Examples](association-model-query-examples.md).</span></span>  
  
###  <a name="example-2-content-query-on-a-decision-trees-model"></a><a name="bkmk_DecTree"></a> <span data-ttu-id="bd903-188">예 2: 의사 결정 트리 모델에 대한 내용 쿼리</span><span class="sxs-lookup"><span data-stu-id="bd903-188">Example 2: Content Query on a Decision Trees Model</span></span>  
 <span data-ttu-id="bd903-189">의사 결정 트리 모델은 예측뿐만 아니라 분류에도 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd903-189">A decision tree model can be used for prediction as well as for classification.</span></span>  <span data-ttu-id="bd903-190">이 예에서는 모델을 사용하여 결과를 예측한다고 가정하지만 결과를 분류하는 데 사용할 수 있는 요소나 규칙을 찾으려고 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd903-190">This example assumes that you are using the model to predict an outcome, but you also want to find out which factors or rules can be used to classify the outcome.</span></span>  
  
 <span data-ttu-id="bd903-191">의사 결정 트리 모델에서 노드는 트리 및 리프 노드를 나타내는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="bd903-191">In a decision tree model, nodes are used to represent both trees and leaf nodes.</span></span> <span data-ttu-id="bd903-192">각 노드에 대한 캡션에는 결과 경로에 대한 설명이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd903-192">The caption for each node contains the description of the path to the outcome.</span></span> <span data-ttu-id="bd903-193">따라서 특정 결과에 대한 경로를 추적하려면 해당 결과가 포함된 노드를 식별하고 해당 노드에 대한 세부 정보를 얻어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd903-193">Therefore, to trace the path for any particular outcome, you need to identify the node that contains it, and get the details for that node.</span></span>  
  
 <span data-ttu-id="bd903-194">다음 예와 같이 예측 쿼리에서 예측 함수 [PredictNodeId&#40;DMX&#41;](/sql/dmx/predictnodeid-dmx)를 추가하여 관련 노드의 ID를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="bd903-194">In your prediction query, you add the prediction function [PredictNodeId &#40;DMX&#41;](/sql/dmx/predictnodeid-dmx), to get the ID of the related node, as shown in the following example:</span></span>  
  
```  
SELECT  Predict([Bike Buyer]), PredictNodeID([Bike Buyer])   
FROM [<decision tree model name>]  
PREDICTION JOIN   
<input rowset>   
```  
  
 <span data-ttu-id="bd903-195">결과가 포함된 노드의 ID가 있으면 다음과 같이 NODE_CAPTION을 포함하는 내용 쿼리를 만들어 예측에 대해 설명하는 규칙이나 경로를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd903-195">Once you have the ID of the node that contains the outcome, you can retrieve the rule or path that explains the prediction by creating a content query that includes the NODE_CAPTION, as follows:</span></span>  
  
```  
SELECT NODE_CAPTION  
FROM [<decision tree model name>]   
WHERE NODE_UNIQUE_NAME= '<node id>'  
```  
  
 <span data-ttu-id="bd903-196">자세한 내용은 [의사 결정 트리 모델 쿼리 예제](decision-trees-model-query-examples.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="bd903-196">For more examples, see [Decision Trees Model Query Examples](decision-trees-model-query-examples.md).</span></span>  
  
##  <a name="working-with-the-query-results"></a><a name="bkmk_Results"></a><span data-ttu-id="bd903-197">쿼리 결과 작업</span><span class="sxs-lookup"><span data-stu-id="bd903-197">Working with the Query Results</span></span>  
 <span data-ttu-id="bd903-198">예에서 설명한 것처럼 내용 쿼리는 일반적으로 테이블 형식의 행 집합을 반환하지만, 중첩 열의 정보를 포함할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd903-198">As the examples demonstrate, content queries mostly return tabular rowsets, but can also include information from nested columns.</span></span> <span data-ttu-id="bd903-199">반환되는 행 집합을 평면화할 수 있지만, 그러면 결과 작업이 더 복잡해질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd903-199">You can flatten the rowset that is returned, but this can make working with results more complex.</span></span> <span data-ttu-id="bd903-200">특히 NODE_DISTRIBUTION 노드의 콘텐츠는 중첩되지만 모델에 대한 매우 유용한 정보를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="bd903-200">The content of the NODE_DISTRIBUTION node in particular is nested, but contains much interesting information about the model.</span></span>  
  
 <span data-ttu-id="bd903-201">계층적 행 집합으로 작업하는 방법은 MSDN에서 OLEDB 사양을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="bd903-201">For more information about how to work with hierarchical rowsets, see the OLEDB specification on MSDN.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd903-202">참고 항목</span><span class="sxs-lookup"><span data-stu-id="bd903-202">See Also</span></span>  
 <span data-ttu-id="bd903-203">[DMX Select 문 이해](/sql/dmx/understanding-the-dmx-select-statement) </span><span class="sxs-lookup"><span data-stu-id="bd903-203">[Understanding the DMX Select Statement](/sql/dmx/understanding-the-dmx-select-statement) </span></span>  
 [<span data-ttu-id="bd903-204">데이터 마이닝 쿼리</span><span class="sxs-lookup"><span data-stu-id="bd903-204">Data Mining Queries</span></span>](data-mining-queries.md)  
  
  
