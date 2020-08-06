---
title: 개체 처리 (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- errors [XML for Analysis]
- objects [XML for Analysis]
- XML for Analysis, objects
- XMLA, partitions
- partitions [Analysis Services], XML for Analysis
- XML for Analysis, partitions
- writeback [Analysis Services], XML for Analysis
- out-of-line bindings
- processing objects [XML for Analysis]
- XMLA, objects
ms.assetid: a65b3249-303d-49c6-98af-6ac6eed11a03
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2e59c7953ae8fc7d3cfceafa7b0e9d8c7186daf8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738937"
---
# <a name="processing-objects-xmla"></a><span data-ttu-id="9fa4b-102">개체 처리(XMLA)</span><span class="sxs-lookup"><span data-stu-id="9fa4b-102">Processing Objects (XMLA)</span></span>
  <span data-ttu-id="9fa4b-103">에서 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 처리는 비즈니스 분석을 위해 데이터를 정보로 변환 하는 단계 또는 일련의 단계입니다.</span><span class="sxs-lookup"><span data-stu-id="9fa4b-103">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], processing is the step or series of steps that turn data into information for business analysis.</span></span> <span data-ttu-id="9fa4b-104">처리 방법은 개체 유형에 따라 달라지지만 처리는 항상 데이터를 정보로 변환하는 과정의 일부입니다.</span><span class="sxs-lookup"><span data-stu-id="9fa4b-104">Processing is different depending on the type of object, but processing is always part of turning data into information.</span></span>  
  
 <span data-ttu-id="9fa4b-105">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]개체를 처리 하려면 [process](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/process-element-xmla) 명령을 사용 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9fa4b-105">To process an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] object, you can use the [Process](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/process-element-xmla) command.</span></span> <span data-ttu-id="9fa4b-106">`Process` 명령이 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스에서 처리할 수 있는 개체는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="9fa4b-106">The `Process` command can process the following objects on an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance:</span></span>  
  
-   <span data-ttu-id="9fa4b-107">큐브</span><span class="sxs-lookup"><span data-stu-id="9fa4b-107">Cubes</span></span>  
  
-   <span data-ttu-id="9fa4b-108">데이터베이스</span><span class="sxs-lookup"><span data-stu-id="9fa4b-108">Databases</span></span>  
  
-   <span data-ttu-id="9fa4b-109">차원</span><span class="sxs-lookup"><span data-stu-id="9fa4b-109">Dimensions</span></span>  
  
-   <span data-ttu-id="9fa4b-110">측정값 그룹</span><span class="sxs-lookup"><span data-stu-id="9fa4b-110">Measure groups</span></span>  
  
-   <span data-ttu-id="9fa4b-111">마이닝 모델</span><span class="sxs-lookup"><span data-stu-id="9fa4b-111">Mining models</span></span>  
  
-   <span data-ttu-id="9fa4b-112">마이닝 구조</span><span class="sxs-lookup"><span data-stu-id="9fa4b-112">Mining structures</span></span>  
  
-   <span data-ttu-id="9fa4b-113">파티션</span><span class="sxs-lookup"><span data-stu-id="9fa4b-113">Partitions</span></span>  
  
 <span data-ttu-id="9fa4b-114">`Process` 명령에는 개체 처리를 제어하기 위해 설정할 수 있는 다양한 속성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9fa4b-114">To control the processing of objects, the `Process` command has various properties that can be set.</span></span> <span data-ttu-id="9fa4b-115">제어할 수 있는 `Process` 명령의 속성으로는 처리량, 처리할 개체, 아웃오브 라인 바인딩 사용 여부, 오류 해결 방법 및 쓰기 저장(writeback) 테이블 관리 방법이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9fa4b-115">The `Process` command has properties that control: how much processing will be done, which objects will be processed, whether to use out-of-line bindings, how to handle errors, and how to manage writeback tables.</span></span>  
  
## <a name="specifying-processing-options"></a><span data-ttu-id="9fa4b-116">처리 옵션 지정</span><span class="sxs-lookup"><span data-stu-id="9fa4b-116">Specifying Processing Options</span></span>  
 <span data-ttu-id="9fa4b-117">명령의 [Type](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/type-element-xmla) 속성은 `Process` 개체를 처리할 때 사용할 처리 옵션을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fa4b-117">The [Type](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/type-element-xmla) property of the `Process` command specifies the processing option to use when processing the object.</span></span> <span data-ttu-id="9fa4b-118">처리 옵션에 대한 자세한 내용은 [처리 옵션 및 설정&#40;Analysis Services&#41;](../multidimensional-models/processing-options-and-settings-analysis-services.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9fa4b-118">For more information about processing options, see [Processing Options and Settings &#40;Analysis Services&#41;](../multidimensional-models/processing-options-and-settings-analysis-services.md).</span></span>  
  
 <span data-ttu-id="9fa4b-119">다음 표에서는 `Type` 속성에 대한 상수와 각 상수를 사용하여 처리할 수 있는 다양한 개체를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="9fa4b-119">The following table lists the constants for the `Type` property and the various objects that can be processed using each constant.</span></span>  
  
|<span data-ttu-id="9fa4b-120">`Type` 값</span><span class="sxs-lookup"><span data-stu-id="9fa4b-120">`Type` value</span></span>|<span data-ttu-id="9fa4b-121">적용 가능한 개체</span><span class="sxs-lookup"><span data-stu-id="9fa4b-121">Applicable objects</span></span>|  
|--------------------|------------------------|  
|<span data-ttu-id="9fa4b-122">*ProcessFull*</span><span class="sxs-lookup"><span data-stu-id="9fa4b-122">*ProcessFull*</span></span>|<span data-ttu-id="9fa4b-123">큐브, 데이터베이스, 차원, 측정값 그룹, 마이닝 모델, 마이닝 구조, 파티션</span><span class="sxs-lookup"><span data-stu-id="9fa4b-123">Cube, database, dimension, measure group, mining model, mining structure, partition</span></span>|  
|<span data-ttu-id="9fa4b-124">*ProcessAdd*</span><span class="sxs-lookup"><span data-stu-id="9fa4b-124">*ProcessAdd*</span></span>|<span data-ttu-id="9fa4b-125">차원, 파티션</span><span class="sxs-lookup"><span data-stu-id="9fa4b-125">Dimension, partition</span></span>|  
|<span data-ttu-id="9fa4b-126">*ProcessUpdate*</span><span class="sxs-lookup"><span data-stu-id="9fa4b-126">*ProcessUpdate*</span></span>|<span data-ttu-id="9fa4b-127">차원</span><span class="sxs-lookup"><span data-stu-id="9fa4b-127">Dimension</span></span>|  
|<span data-ttu-id="9fa4b-128">*ProcessIndexes*</span><span class="sxs-lookup"><span data-stu-id="9fa4b-128">*ProcessIndexes*</span></span>|<span data-ttu-id="9fa4b-129">차원, 큐브, 측정값 그룹, 파티션</span><span class="sxs-lookup"><span data-stu-id="9fa4b-129">Dimension, cube, measure group, partition</span></span>|  
|<span data-ttu-id="9fa4b-130">*ProcessData*</span><span class="sxs-lookup"><span data-stu-id="9fa4b-130">*ProcessData*</span></span>|<span data-ttu-id="9fa4b-131">차원, 큐브, 측정값 그룹, 파티션</span><span class="sxs-lookup"><span data-stu-id="9fa4b-131">Dimension, cube, measure group, partition</span></span>|  
|<span data-ttu-id="9fa4b-132">*ProcessDefault*</span><span class="sxs-lookup"><span data-stu-id="9fa4b-132">*ProcessDefault*</span></span>|<span data-ttu-id="9fa4b-133">큐브, 데이터베이스, 차원, 측정값 그룹, 마이닝 모델, 마이닝 구조, 파티션</span><span class="sxs-lookup"><span data-stu-id="9fa4b-133">Cube, database, dimension, measure group, mining model, mining structure, partition</span></span>|  
|<span data-ttu-id="9fa4b-134">*ProcessClear*</span><span class="sxs-lookup"><span data-stu-id="9fa4b-134">*ProcessClear*</span></span>|<span data-ttu-id="9fa4b-135">큐브, 데이터베이스, 차원, 측정값 그룹, 마이닝 모델, 마이닝 구조, 파티션</span><span class="sxs-lookup"><span data-stu-id="9fa4b-135">Cube, database, dimension, measure group, mining model, mining structure, partition</span></span>|  
|<span data-ttu-id="9fa4b-136">*ProcessStructure*</span><span class="sxs-lookup"><span data-stu-id="9fa4b-136">*ProcessStructure*</span></span>|<span data-ttu-id="9fa4b-137">큐브, 마이닝 구조</span><span class="sxs-lookup"><span data-stu-id="9fa4b-137">Cube, mining structure</span></span>|  
|<span data-ttu-id="9fa4b-138">*ProcessClearStructureOnly*</span><span class="sxs-lookup"><span data-stu-id="9fa4b-138">*ProcessClearStructureOnly*</span></span>|<span data-ttu-id="9fa4b-139">마이닝 구조</span><span class="sxs-lookup"><span data-stu-id="9fa4b-139">Mining structure</span></span>|  
|<span data-ttu-id="9fa4b-140">*ProcessScriptCache*</span><span class="sxs-lookup"><span data-stu-id="9fa4b-140">*ProcessScriptCache*</span></span>|<span data-ttu-id="9fa4b-141">큐브</span><span class="sxs-lookup"><span data-stu-id="9fa4b-141">Cube</span></span>|  
  
 <span data-ttu-id="9fa4b-142">개체를 처리 하는 방법에 대 한 자세한 내용은 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] [다차원 모델 개체 처리](../multidimensional-models/processing-a-multidimensional-model-analysis-services.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9fa4b-142">For more information about processing [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] objects, see [Multidimensional Model Object Processing](../multidimensional-models/processing-a-multidimensional-model-analysis-services.md).</span></span>  
  
## <a name="specifying-objects-to-be-processed"></a><span data-ttu-id="9fa4b-143">처리할 개체 지정</span><span class="sxs-lookup"><span data-stu-id="9fa4b-143">Specifying Objects to be Processed</span></span>  
 <span data-ttu-id="9fa4b-144">명령의 [object](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla) 속성에는 `Process` 처리할 개체의 개체 식별자가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9fa4b-144">The [Object](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla) property of the `Process` command contains the object identifier of the object to be processed.</span></span> <span data-ttu-id="9fa4b-145">`Process` 명령에는 한 개체만 지정할 수 있지만 개체를 처리할 때 모든 자식 개체도 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="9fa4b-145">Only one object can be specified in a `Process` command, but processing an object also processes any child objects.</span></span> <span data-ttu-id="9fa4b-146">예를 들어 큐브의 측정값 그룹을 처리하면 해당 측정 그룹의 모든 파티션이 처리되고, 데이터베이스를 처리하면 데이터베이스에 포함된 큐브, 차원 및 마이닝 구조 등의 모든 개체가 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="9fa4b-146">For example, processing a measure group in a cube processes all the partitions for that measure group, while processing a database processes all the objects, including cubes, dimensions, and mining structures, that are contained by the database.</span></span>  
  
 <span data-ttu-id="9fa4b-147">`ProcessAffectedObjects` 명령의 `Process` 특성을 true로 설정하면 지정된 개체 처리 작업의 영향을 받는 관련 개체도 모두 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="9fa4b-147">If you set the `ProcessAffectedObjects` attribute of the `Process` command to true, any related object affected by processing the specified object is also processed.</span></span> <span data-ttu-id="9fa4b-148">예를 들어, 명령의 *ProcessUpdate* 처리 옵션을 사용 하 여 차원을 증분 업데이트 하는 경우 `Process` [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] `ProcessAffectedObjects` 이 true로 설정 된 경우에도 추가 되거나 삭제 되는 멤버로 인해 집계가 무효화 되는 파티션이 처리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9fa4b-148">For example, if a dimension is incrementally updated by using the *ProcessUpdate* processing option in the `Process` command, any partition whose aggregations are invalidated because of members being added or deleted is also processed by [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] if `ProcessAffectedObjects` is set to true.</span></span> <span data-ttu-id="9fa4b-149">이 경우 단일 `Process` 명령이 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스의 여러 개체를 처리할 수 있지만 `Process` 명령에 지정된 단일 개체 이외에 추가로 처리되어야 하는 개체는 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]에서 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="9fa4b-149">In this case, a single `Process` command can process multiple objects on an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance, but [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] determines which objects besides the single object specified in the `Process` command must also be processed.</span></span>  
  
 <span data-ttu-id="9fa4b-150">하지만 `Process` 명령 내에서 `Batch` 명령을 여러 개 사용하면 차원과 같은 여러 개체를 동시에 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9fa4b-150">However, you can process multiple objects, such as dimensions, at the same time by using multiple `Process` commands within a `Batch` command.</span></span> <span data-ttu-id="9fa4b-151">일괄 처리 작업을 수행하면 `ProcessAffectedObjects` 특성을 사용할 때보다 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스에서 수행되는 개체의 순차 및 병렬 처리를 보다 세부적으로 제어할 수 있으며 대규모 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 데이터베이스의 처리 방법을 조정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9fa4b-151">Batch operations provide a finer level of control for serial or parallel processing of objects on an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance than using the `ProcessAffectedObjects` attribute, and let you to tune your processing approach for larger [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] databases.</span></span> <span data-ttu-id="9fa4b-152">일괄 처리 작업을 수행 하는 방법에 대 한 자세한 내용은 [XMLA&#41;&#40;일괄 처리 작업 수행 ](performing-batch-operations-xmla.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9fa4b-152">For more information about performing batch operations, see [Performing Batch Operations &#40;XMLA&#41;](performing-batch-operations-xmla.md).</span></span>  
  
## <a name="specifying-out-of-line-bindings"></a><span data-ttu-id="9fa4b-153">아웃오브 라인 바인딩 지정</span><span class="sxs-lookup"><span data-stu-id="9fa4b-153">Specifying Out-of-Line Bindings</span></span>  
 <span data-ttu-id="9fa4b-154">명령이 `Process` 명령에 포함 되지 않은 경우 `Batch` 처리할 개체에 대 한 명령의 [바인딩](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/bindings-element-xmla), [DataSource](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/source-element-xmla)및 [DataSourceView](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/datasourceview-element-xmla) 속성에서 아웃오브 라인 바인딩을 선택적으로 지정할 수 있습니다 `Process` .</span><span class="sxs-lookup"><span data-stu-id="9fa4b-154">If the `Process` command is not contained by a `Batch` command, you can optionally specify out-of-line bindings in the [Bindings](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/bindings-element-xmla), [DataSource](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/source-element-xmla), and [DataSourceView](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/datasourceview-element-xmla) properties of the `Process` command for the objects to be processed.</span></span> <span data-ttu-id="9fa4b-155">아웃오브 라인 바인딩은 `Process` 명령이 실행되는 동안에만 바인딩이 존재하는 데이터 원본, 데이터 원본 뷰 및 기타 개체에 대한 참조로, 처리되는 개체에 연결된 기존 바인딩을 모두 재정의합니다.</span><span class="sxs-lookup"><span data-stu-id="9fa4b-155">Out-of-line bindings are references to data sources, data source views, and other objects in which the binding exists only during the execution of the `Process` command, and which override any existing bindings associated with the objects being processed.</span></span> <span data-ttu-id="9fa4b-156">아웃오브 라인 바인딩을 지정하지 않으면 처리할 개체에 현재 연결되어 있는 바인딩이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="9fa4b-156">If out-of-line bindings are not specified, the bindings currently associated with the objects to be processed are used.</span></span>  
  
 <span data-ttu-id="9fa4b-157">아웃오브 라인 바인딩은 다음과 같은 경우에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="9fa4b-157">Out-of-line bindings are used in the following circumstances:</span></span>  
  
-   <span data-ttu-id="9fa4b-158">행이 두 번 계산되지 않도록 기존 팩트 테이블에 대한 필터나 대체 팩트 테이블을 지정해야 하는 파티션을 증분 처리하는 경우</span><span class="sxs-lookup"><span data-stu-id="9fa4b-158">Incrementally processing a partition, in which an alternative fact table or a filter on the existing fact table must be specified to make sure that rows are not counted twice.</span></span>  
  
-   <span data-ttu-id="9fa4b-159">에서 데이터 흐름 태스크를 사용 하 여 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 차원, 마이닝 모델 또는 파티션을 처리 하는 동안 데이터를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fa4b-159">Using a data flow task in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] to provide data while processing a dimension, mining model, or partition.</span></span>  
  
 <span data-ttu-id="9fa4b-160">아웃오브 라인 바인딩은 ASSL(Analysis Services Scripting Language)의 일부로 설명됩니다.</span><span class="sxs-lookup"><span data-stu-id="9fa4b-160">Out-of-line bindings are described as part of the Analysis Services Scripting Language (ASSL).</span></span> <span data-ttu-id="9fa4b-161">로의 아웃오브 라인 바인딩에 대 한 자세한 내용은 [SSAS 다차원&#41;&#40;데이터 원본 및 바인딩 ](../multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9fa4b-161">For more information about out-of-line bindings in ASSL, see [Data Sources and Bindings &#40;SSAS Multidimensional&#41;](../multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).</span></span>  
  
### <a name="incrementally-updating-partitions"></a><span data-ttu-id="9fa4b-162">파티션 증분 업데이트</span><span class="sxs-lookup"><span data-stu-id="9fa4b-162">Incrementally Updating Partitions</span></span>  
 <span data-ttu-id="9fa4b-163">파티션에 대해 지정된 바인딩은 파티션 내에서 이미 집계된 팩트 테이블 데이터를 참조하기 때문에 이미 처리된 파티션을 증분 업데이트하려면 아웃오브 라인 바인딩이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="9fa4b-163">Incrementally updating an already processed partition typically requires an out-of-line binding because the binding specified for the partition references fact table data already aggregated within the partition.</span></span> <span data-ttu-id="9fa4b-164">`Process` 명령을 사용하여 이미 처리된 파티션을 증분 업데이트하는 경우 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]에서는 다음과 같은 동작을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="9fa4b-164">When incrementally updating an already processed partition by using the `Process` command, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] performs the following actions:</span></span>  
  
-   <span data-ttu-id="9fa4b-165">증분 업데이트할 파티션과 동일한 구조의 임시 파티션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="9fa4b-165">Creates a temporary partition with a structure identical to that of the partition to be incrementally updated.</span></span>  
  
-   <span data-ttu-id="9fa4b-166">`Process` 명령에 지정된 아웃오브 라인 바인딩을 사용하여 임시 파티션을 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="9fa4b-166">Processes the temporary partition, using the out-of-line binding specified in the `Process` command.</span></span>  
  
-   <span data-ttu-id="9fa4b-167">임시 파티션을 선택된 기존 파티션과 병합합니다.</span><span class="sxs-lookup"><span data-stu-id="9fa4b-167">Merges the temporary partition with the existing selected partition.</span></span>  
  
 <span data-ttu-id="9fa4b-168">XMLA (XML for Analysis를 사용 하 여 파티션을 병합 하는 방법에 대 한 자세한 내용은 [xmla&#41;&#40;파티션 병합 ](merging-partitions-xmla.md)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="9fa4b-168">For more information about merging partitions using XML for Analysis (XMLA), see [Merging Partitions &#40;XMLA&#41;](merging-partitions-xmla.md).</span></span>  
  
## <a name="handling-processing-errors"></a><span data-ttu-id="9fa4b-169">처리 오류 해결</span><span class="sxs-lookup"><span data-stu-id="9fa4b-169">Handling Processing Errors</span></span>  
 <span data-ttu-id="9fa4b-170">명령의 [Errorconfiguration](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/errorconfiguration-element-xmla) 속성을 `Process` 사용 하면 개체를 처리 하는 동안 발생 한 오류를 처리 하는 방법을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9fa4b-170">The [ErrorConfiguration](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/errorconfiguration-element-xmla) property of the `Process` command lets you specify how to handle errors encountered while processing an object.</span></span> <span data-ttu-id="9fa4b-171">예를 들어 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]에서 차원을 처리하는 동안 키 특성의 키 열에 중복 값이 있는 경우</span><span class="sxs-lookup"><span data-stu-id="9fa4b-171">For example, while processing a dimension, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] encounters a duplicate value in the key column of the key attribute.</span></span> <span data-ttu-id="9fa4b-172">특성 키는 고유해야 하므로 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 에서는 중복 레코드를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="9fa4b-172">Because attribute keys must be unique, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] discards the duplicate records.</span></span> <span data-ttu-id="9fa4b-173">의 [Keyduplicate](https://docs.microsoft.com/bi-reference/assl/properties/keyduplicate-element-assl) 속성을 기반으로 `ErrorConfiguration` [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 다음을 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9fa4b-173">Based on the [KeyDuplicate](https://docs.microsoft.com/bi-reference/assl/properties/keyduplicate-element-assl) property of `ErrorConfiguration`, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] could:</span></span>  
  
-   <span data-ttu-id="9fa4b-174">오류를 무시하고 차원을 계속 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="9fa4b-174">Ignore the error and continue processing the dimension.</span></span>  
  
-   <span data-ttu-id="9fa4b-175">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]에서 중복 키가 있음을 알리는 메시지를 반환하고 처리를 계속합니다.</span><span class="sxs-lookup"><span data-stu-id="9fa4b-175">Return a message that states [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] encountered a duplicate key and continue processing.</span></span>  
  
 <span data-ttu-id="9fa4b-176">`ErrorConfiguration` 명령을 실행하는 동안 `Process`에서 옵션을 제공하는 유사한 경우가 많이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9fa4b-176">There are many similar conditions for which `ErrorConfiguration` provides options during a `Process` command.</span></span>  
  
## <a name="managing-writeback-tables"></a><span data-ttu-id="9fa4b-177">쓰기 저장(writeback) 테이블 관리</span><span class="sxs-lookup"><span data-stu-id="9fa4b-177">Managing Writeback Tables</span></span>  
 <span data-ttu-id="9fa4b-178">`Process` 명령을 실행하는 동안 아직 완전히 처리되지 않은 쓰기 가능한 파티션이나 그러한 파티션에 대한 큐브 또는 측정값 그룹이 발생한다면 해당 파티션에 대한 쓰기 저장(writeback) 테이블이 아직 존재하지 않는 것일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9fa4b-178">If the `Process` command encounters a write-enabled partition, or a cube or measure group for such a partition, that is not already fully processed, a writeback table may not already exist for that partition.</span></span> <span data-ttu-id="9fa4b-179">명령의 [WritebackTableCreation](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/writebacktablecreation-element-xmla) 속성은가 `Process` [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 쓰기 저장 (writeback) 테이블을 만들어야 하는지 여부를 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fa4b-179">The [WritebackTableCreation](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/writebacktablecreation-element-xmla) property of the `Process` command determines whether [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] should create a writeback table.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="9fa4b-180">예</span><span class="sxs-lookup"><span data-stu-id="9fa4b-180">Examples</span></span>  
  
### <a name="description"></a><span data-ttu-id="9fa4b-181">Description</span><span class="sxs-lookup"><span data-stu-id="9fa4b-181">Description</span></span>  
 <span data-ttu-id="9fa4b-182">다음 예제에서는 [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)] 예제 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 데이터베이스를 완전히 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="9fa4b-182">The following example fully processes the [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)] sample [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database.</span></span>  
  
### <a name="code"></a><span data-ttu-id="9fa4b-183">코드</span><span class="sxs-lookup"><span data-stu-id="9fa4b-183">Code</span></span>  
  
```  
<Process xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">  
  <Object>  
    <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
  </Object>  
  <Type>ProcessFull</Type>  
  <WriteBackTableCreation>UseExisting</WriteBackTableCreation>  
</Process>  
```  
  
### <a name="description"></a><span data-ttu-id="9fa4b-184">Description</span><span class="sxs-lookup"><span data-stu-id="9fa4b-184">Description</span></span>  
 <span data-ttu-id="9fa4b-185">다음 예에서는 예제 데이터베이스에 있는 **놀이 WORKS DW** 큐브의 **Internet Sales** 측정값 그룹에서 **Internet_Sales_2004** 파티션을 증분 처리 합니다 [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="9fa4b-185">The following example incrementally processes the **Internet_Sales_2004** partition in the **Internet Sales** measure group of the **Adventure Works DW** cube in the [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)] sample [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database.</span></span> <span data-ttu-id="9fa4b-186">`Process`명령은 `Bindings` `Process` 파티션에 추가할 집계를 생성할 팩트 테이블 행을 검색 하기 위해 명령의 속성에 있는 아웃오브 라인 쿼리 바인딩을 사용 하 여 2006 년 12 월 31 일 이후의 주문 날짜에 대 한 집계를 파티션에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fa4b-186">The `Process` command is adding aggregations for order dates later than December 31, 2006 to the partition by using an out-of-line query binding in the `Bindings` property of the `Process` command to retrieve the fact table rows from which to generate aggregations to add to the partition.</span></span>  
  
### <a name="code"></a><span data-ttu-id="9fa4b-187">코드</span><span class="sxs-lookup"><span data-stu-id="9fa4b-187">Code</span></span>  
  
```  
<Process ProcessAffectedObjects="true" xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">  
  <Object>  
    <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
    <CubeID>Adventure Works DW</CubeID>  
    <MeasureGroupID>Fact Internet Sales 1</MeasureGroupID>  
    <PartitionID>Internet_Sales_2006</PartitionID>  
  </Object>  
  <Bindings>  
    <Binding>  
      <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
      <CubeID>Adventure Works DW</CubeID>  
      <MeasureGroupID>Fact Internet Sales 1</MeasureGroupID>  
      <PartitionID>Internet_Sales_2006</PartitionID>  
      <Source xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:type="QueryBinding">  
        <DataSourceID>Adventure Works DW</DataSourceID>  
        <QueryDefinition>  
          SELECT  
            [dbo].[FactInternetSales].[ProductKey],  
            [dbo].[FactInternetSales].[OrderDateKey],  
            [dbo].[FactInternetSales].[DueDateKey],  
            [dbo].[FactInternetSales].[ShipDateKey],   
            [dbo].[FactInternetSales].[CustomerKey],   
            [dbo].[FactInternetSales].[PromotionKey],  
            [dbo].[FactInternetSales].[CurrencyKey],  
            [dbo].[FactInternetSales].[SalesTerritoryKey],  
            [dbo].[FactInternetSales].[SalesOrderNumber],  
            [dbo].[FactInternetSales].[SalesOrderLineNumber],  
            [dbo].[FactInternetSales].[RevisionNumber],  
            [dbo].[FactInternetSales].[OrderQuantity],  
            [dbo].[FactInternetSales].[UnitPrice],  
            [dbo].[FactInternetSales].[ExtendedAmount],  
            [dbo].[FactInternetSales].[UnitPriceDiscountPct],  
            [dbo].[FactInternetSales].[DiscountAmount],  
            [dbo].[FactInternetSales].[ProductStandardCost],  
            [dbo].[FactInternetSales].[TotalProductCost],  
            [dbo].[FactInternetSales].[SalesAmount],  
            [dbo].[FactInternetSales].[TaxAmt],  
            [dbo].[FactInternetSales].[Freight],  
            [dbo].[FactInternetSales].[CarrierTrackingNumber],  
            [dbo].[FactInternetSales].[CustomerPONumber]  
          FROM [dbo].[FactInternetSales]  
          WHERE OrderDateKey > '1280'  
        </QueryDefinition>  
      </Source>  
    </Binding>  
  </Bindings>  
  <Type>ProcessAdd</Type>  
  <WriteBackTableCreation>UseExisting</WriteBackTableCreation>  
</Process>  
```  
  
  
