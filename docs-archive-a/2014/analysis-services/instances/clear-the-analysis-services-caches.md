---
title: Analysis Services 캐시 지우기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 6bf66fdd-6a03-4cea-b7e2-eb676ff276ff
author: minewiskan
ms.author: owend
ms.openlocfilehash: e4890dd322406dcf48bc6b8eca89f292cfe132a3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729963"
---
# <a name="clear-the-analysis-services-caches"></a><span data-ttu-id="0d8f9-102">Analysis Services 캐시 지우기</span><span class="sxs-lookup"><span data-stu-id="0d8f9-102">Clear the Analysis Services Caches</span></span>
  <span data-ttu-id="0d8f9-103">Analysis Services는 데이터를 캐시하여 쿼리 성능을 향상시킵니다.</span><span class="sxs-lookup"><span data-stu-id="0d8f9-103">Analysis Services caches data to boost query performance.</span></span> <span data-ttu-id="0d8f9-104">이 항목에서는 XMLA ClearCache 명령을 사용하여 MDX 쿼리에 대한 응답으로 만들어진 캐시를 지우는 데 대한 권장 사항을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="0d8f9-104">This topic provides recommendations for using the XMLA ClearCache command to clear caches that were created in response to an MDX query.</span></span> <span data-ttu-id="0d8f9-105">ClearCache의 실행 효과는 테이블 형식 모델을 사용하는지 다차원 모델을 사용하는지에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="0d8f9-105">The effects of running ClearCache vary depending on whether you are using a tabular or multidimensional model.</span></span>  
  
 <span data-ttu-id="0d8f9-106">**다차원 모델에 대한 캐시를 지우는 경우**</span><span class="sxs-lookup"><span data-stu-id="0d8f9-106">**When to clear the cache for multidimensional models**</span></span>  
  
 <span data-ttu-id="0d8f9-107">다차원 데이터베이스의 경우 Analysis Services는 계산을 평가할 때의 수식 엔진과 차원 쿼리 및 측정값 그룹 쿼리의 결과를 위한 스토리지 엔진에 캐시를 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="0d8f9-107">For multidimensional databases, Analysis Services builds caches in the formula engine when evaluating a calculation, and in the storage engine for the results of dimension queries and measure group queries.</span></span> <span data-ttu-id="0d8f9-108">측정값 그룹 쿼리는 수식 엔진에 셀 좌표 또는 하위 큐브에 대한 측정값 데이터가 필요한 경우 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="0d8f9-108">Measure group queries occur when the formula engine needs measure data for a cell coordinate or subcube.</span></span> <span data-ttu-id="0d8f9-109">차원 쿼리는 비자연 계층을 쿼리할 때와 Autoexists를 적용할 때 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="0d8f9-109">Dimension queries occur when querying unnatural hierarchies and when applying autoexists.</span></span>  
  
 <span data-ttu-id="0d8f9-110">성능 테스트를 수행할 때 캐시를 지우는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="0d8f9-110">Clearing the cache is recommended when conducting performance testing.</span></span> <span data-ttu-id="0d8f9-111">테스트 실행 간에 캐시를 지움으로써 쿼리 디자인 변경으로 인한 영향을 측정한 테스트 결과가 캐시 때문에 왜곡되지 않도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0d8f9-111">By clearing the cache between test runs, you ensure that caching does not skew any test results that measure the impact of a query design change.</span></span>  
  
 <span data-ttu-id="0d8f9-112">**테이블 형식 모델에 대한 캐시를 지우는 경우**</span><span class="sxs-lookup"><span data-stu-id="0d8f9-112">**When to clear the cache for tabular models**</span></span>  
  
 <span data-ttu-id="0d8f9-113">테이블 형식 모델은 일반적으로 메모리에 저장되며, 쿼리가 실행될 때 집계 및 기타 계산이 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="0d8f9-113">Tabular models are generally stored in memory, where aggregations and other calculations are performed at the time a query is executed.</span></span> <span data-ttu-id="0d8f9-114">따라서 ClearCache 명령을 사용할 경우 테이블 형식 모델에 대한 효과는 제한적입니다.</span><span class="sxs-lookup"><span data-stu-id="0d8f9-114">As such, the ClearCache command has a limited effect on tabular models.</span></span> <span data-ttu-id="0d8f9-115">테이블 형식 모델에 대해 MDX 쿼리를 실행할 경우 Analysis Services 캐시에 데이터가 추가될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0d8f9-115">For a tabular model, data may be added to the Analysis Services caches if MDX queries are run against it.</span></span> <span data-ttu-id="0d8f9-116">특히 MDX 및 Autoexists 작업에서 참조하는 DAX 측정값은 수식 캐시와 차원 캐시 각각의 결과를 캐시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0d8f9-116">In particular, DAX measures referenced by MDX and autoexists operations can cache results in the formula cache and dimension cache respectively.</span></span> <span data-ttu-id="0d8f9-117">그러나 비자연 계층 및 측정값 그룹 쿼리는 스토리지 엔진의 결과를 캐시하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0d8f9-117">Note however, that unnatural hierarchies and measure group queries do not cache results in the storage engine.</span></span> <span data-ttu-id="0d8f9-118">또한 DAX 쿼리는 수식 엔진 및 스토리지 엔진의 결과를 캐시하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0d8f9-118">Additionally, it is important to recognize that DAX queries do not cache results in the formula and storage engine.</span></span> <span data-ttu-id="0d8f9-119">MDX 쿼리 결과로 캐시가 존재하는 범위까지는 테이블 형식 모델에 대해 ClearCache를 실행하면 시스템에서 캐시된 데이터가 모두 무효화됩니다.</span><span class="sxs-lookup"><span data-stu-id="0d8f9-119">To the extent that caches exist as a result of MDX queries, running ClearCache against a tabular model will invalidate any cached data from the system.</span></span>  
  
 <span data-ttu-id="0d8f9-120">ClearCache를 실행하면 xVelocity 메모리 내 분석 엔진(VertiPaq)의 메모리 내 캐시도 지워집니다.</span><span class="sxs-lookup"><span data-stu-id="0d8f9-120">Running ClearCache will also clear in-memory caches in the xVelocity in-memory analytics engine (VertiPaq).</span></span> <span data-ttu-id="0d8f9-121">xVelocity 엔진에서는 작은 캐시 결과 집합을 유지합니다.</span><span class="sxs-lookup"><span data-stu-id="0d8f9-121">The xVelocity engine maintains a small set of cached results.</span></span> <span data-ttu-id="0d8f9-122">ClearCache를 실행하면 xVelocity 엔진의 이러한 캐시가 무효화됩니다.</span><span class="sxs-lookup"><span data-stu-id="0d8f9-122">Running ClearCache will invalidate these caches in the xVelocity engine.</span></span>  
  
 <span data-ttu-id="0d8f9-123">마지막으로, ClearCache를 실행하면 `DirectQuery` 모드용으로 테이블 형식 모델이 다시 구성될 때 메모리에 남아 있던 잔여 데이터도 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="0d8f9-123">Finally, running ClearCache will also remove residual data that is left in memory when a tabular model is reconfigured for `DirectQuery` mode.</span></span> <span data-ttu-id="0d8f9-124">이 사실은 모델에 포함되어 있는 중요한 데이터가 엄격하게 제어될 수 있는 경우에 특히 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="0d8f9-124">This is particularly important if the model contains sensitive data that is subject to tight controls.</span></span> <span data-ttu-id="0d8f9-125">이 경우에는 중요한 데이터가 필요한 위치에만 존재하도록 하기 위해 수행할 수 있는 예방 조치로 ClearCache를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="0d8f9-125">In this case, running ClearCache is a precautionary action that you can take to ensure that sensitive data exists only where you expect it to be.</span></span> <span data-ttu-id="0d8f9-126">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 를 사용하여 모델을 배포하고 쿼리 모드를 변경하는 경우에는 캐시를 수동으로 지워야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d8f9-126">Clearing the cache manually is necessary if you are using [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] to deploy the model and change the query mode.</span></span> <span data-ttu-id="0d8f9-127">반대로 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]를 사용하여 모델과 파티션에 `DirectQuery`를 지정하면 해당 쿼리 모드를 사용하도록 모드를 전환할 때 캐시가 자동으로 지워집니다.</span><span class="sxs-lookup"><span data-stu-id="0d8f9-127">In contrast, using [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] to specify `DirectQuery` on the model and partitions will automatically clear the cache when you switch the model to use that query mode.</span></span>  
  
 <span data-ttu-id="0d8f9-128">성능을 테스트하는 중에 다차원 모델 캐시를 지우기 위한 권장 사항과 비교했을 때 테이블 형식 모델 캐시를 지우기 위한 광범위한 권장 사항은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0d8f9-128">Compared with recommendations for clearing multidimensional model caches during performance testing, there is no broad recommendation for clearing tabular model caches.</span></span> <span data-ttu-id="0d8f9-129">중요한 데이터가 포함된 테이블 형식 모델에 대한 배포를 관리하는 경우가 아니면 캐시를 지우는 특정 관리 태스크가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0d8f9-129">If you are not managing the deployment of a tabular model that contains sensitive data, there is no specific administrative task that calls for clearing the cache.</span></span>  
  
## <a name="clear-the-cache-for-analysis-services-models"></a><span data-ttu-id="0d8f9-130">Analysis Services 모델에 대한 캐시 지우기</span><span class="sxs-lookup"><span data-stu-id="0d8f9-130">Clear the cache for Analysis Services models</span></span>  
 <span data-ttu-id="0d8f9-131">캐시를 지우려면 XMLA와 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="0d8f9-131">To clear the cache, use XMLA and [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="0d8f9-132">데이터베이스, 큐브, 차원이나 테이블 또는 측정값 그룹 수준에서 캐시를 지울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0d8f9-132">You can clear the cache at the database, cube, dimension or table, or measure group level.</span></span> <span data-ttu-id="0d8f9-133">데이터베이스 수준에서 캐시를 지우는 데 필요한 다음 단계는 다차원 모델과 테이블 형식 모델 모두에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="0d8f9-133">The following steps for clearing the cache at the database level apply to both multidimensional models and tabular models.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0d8f9-134">엄격한 성능 테스트를 위해서는 캐시를 지우는 데 대한 더욱 포괄적인 접근이 필요할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0d8f9-134">Rigorous performance testing might require a more comprehensive approach to clearing the cache.</span></span> <span data-ttu-id="0d8f9-135">Analysis Services 및 파일 시스템 캐시를 플러시하는 방법은 [SQL Server 2008 R2 Analysis Services 작업 가이드](https://go.microsoft.com/fwlink/?linkID=https://go.microsoft.com/fwlink/?LinkID=225539)에서 캐시 지우기에 대한 섹션을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="0d8f9-135">For instructions on how to flush Analysis Services and file system caches, see the section on clearing caches in the [SQL Server 2008 R2 Analysis Services Operations Guide](https://go.microsoft.com/fwlink/?linkID=https://go.microsoft.com/fwlink/?LinkID=225539).</span></span>  
  
 <span data-ttu-id="0d8f9-136">다차원 모델과 테이블 형식 모델 모두 두 단계의 프로세스를 통해 이러한 캐시를 지울 수 있습니다. 이 프로세스는 ClearCache를 실행할 때 캐시를 무효화하고 다음 쿼리를 받을 때 캐시를 지우는 단계로 구성되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0d8f9-136">For both multidimensional and tabular models, clearing some of these caches can be a two-step process that consists of invalidating the cache when ClearCache executes, followed by emptying the cache when the next query is received.</span></span> <span data-ttu-id="0d8f9-137">실제로 캐시를 비운 후에만 메모리 사용량의 감소가 확실히 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="0d8f9-137">A reduction in memory consumption will be evident only after the cache is actually emptied.</span></span>  
  
 <span data-ttu-id="0d8f9-138">캐시를 지우려면 XMLA 쿼리의 `ClearCache` 문에 개체 식별자를 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d8f9-138">Clearing the cache requires that you provide an object identifier to the `ClearCache` statement in an XMLA query.</span></span> <span data-ttu-id="0d8f9-139">이 항목의 첫 번째 단계에서는 개체 식별자를 가져오는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="0d8f9-139">The first step in this topic explains how to get an object identifier.</span></span>  
  
#### <a name="step-1-get-the-object-identifier"></a><span data-ttu-id="0d8f9-140">1단계: 개체 식별자 가져오기</span><span class="sxs-lookup"><span data-stu-id="0d8f9-140">Step 1: Get the object identifier</span></span>  
  
1.  <span data-ttu-id="0d8f9-141">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]에서 개체를 마우스 오른쪽 단추로 클릭하고 **속성**을 선택한 다음 **속성** 창에서 ID 속성 값을 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="0d8f9-141">In [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], right-click an object, select **Properties**, and copy the value from the ID property in the **Properties** pane.</span></span> <span data-ttu-id="0d8f9-142">이 방법은 데이터베이스, 큐브, 차원 또는 테이블에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0d8f9-142">This approach works for the database, cube, dimension, or table.</span></span>  
  
2.  <span data-ttu-id="0d8f9-143">측정값 그룹 ID를 가져오려면 측정값 그룹을 마우스 오른쪽 단추로 클릭하고 **측정값 그룹 스크립팅**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0d8f9-143">To get the measure group ID, right-click the measure group and select **Script Measure Group As**.</span></span> <span data-ttu-id="0d8f9-144">**만들기** 또는 **변경**을 선택하고 창에 쿼리를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="0d8f9-144">Choose either **Create** or **Alter**, and send the query to a window.</span></span> <span data-ttu-id="0d8f9-145">측정값 그룹의 ID가 개체 정의에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="0d8f9-145">The ID of the measure group will be visible in the object definition.</span></span> <span data-ttu-id="0d8f9-146">개체 정의의 ID를 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="0d8f9-146">Copy the ID of the object definition.</span></span>  
  
#### <a name="step-2-run-the-query"></a><span data-ttu-id="0d8f9-147">2단계: 쿼리 실행</span><span class="sxs-lookup"><span data-stu-id="0d8f9-147">Step 2: Run the query</span></span>  
  
1.  <span data-ttu-id="0d8f9-148">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]에서 데이터베이스를 마우스 오른쪽 단추로 클릭하고 **새 쿼리**를 가리킨 다음 **XMLA**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0d8f9-148">In [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], right-click a database, point to **New Query**, and select **XMLA**.</span></span>  
  
2.  <span data-ttu-id="0d8f9-149">다음 코드 예제를 XMLA 쿼리 창에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="0d8f9-149">Copy the following code example into the XMLA query window.</span></span> <span data-ttu-id="0d8f9-150">`DatabaseID`를 현재 연결 데이터베이스의 ID로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="0d8f9-150">Change `DatabaseID` to the ID of the database on the current connection.</span></span>  
  
    ```  
    <ClearCache xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">  
      <Object>  
        <DatabaseID> Adventure Works DW Multidimensional</DatabaseID>  
      </Object>  
    </ClearCache>  
  
    ```  
  
     <span data-ttu-id="0d8f9-151">또는 측정값 그룹과 같은 자식 개체의 경로를 지정하여 해당 개체에 대한 캐시만 지울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0d8f9-151">Alternatively, you can specify a path of a child object, such as a measure group, to clear the cache for just that object.</span></span>  
  
    ```  
    <ClearCache xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">  
      <Object>  
        <DatabaseID>Adventure Works DW Multidimensional</DatabaseID>  
            <CubeID>Adventure Works</CubeID>  
            <MeasureGroupID>Fact Currency Rate</MeasureGroupID>  
      </Object>  
    </ClearCache>  
    ```  
  
3.  <span data-ttu-id="0d8f9-152">F5 키를 눌러 쿼리를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="0d8f9-152">Press F5 to execute the query.</span></span> <span data-ttu-id="0d8f9-153">다음 결과가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="0d8f9-153">You should see the following result:</span></span>  
  
    ```  
    <return xmlns="urn:schemas-microsoft-com:xml-analysis">  
      <root xmlns="urn:schemas-microsoft-com:xml-analysis:empty" />  
    </return>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="0d8f9-154">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0d8f9-154">See Also</span></span>  
 <span data-ttu-id="0d8f9-155">[Analysis Services에서 관리 태스크 스크립팅](../script-administrative-tasks-in-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="0d8f9-155">[Script Administrative Tasks in Analysis Services](../script-administrative-tasks-in-analysis-services.md) </span></span>  
 [<span data-ttu-id="0d8f9-156">Analysis Services 인스턴스 모니터</span><span class="sxs-lookup"><span data-stu-id="0d8f9-156">Monitor an Analysis Services Instance</span></span>](monitor-an-analysis-services-instance.md)  
  
  
