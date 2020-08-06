---
title: 다차원 모델의 파티션 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 26e01dc7-fa49-4b1f-99eb-7799d1b4dcd2
author: minewiskan
ms.author: owend
ms.openlocfilehash: 60d14551344e6898d7bb0add41b5931282c8861d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648650"
---
# <a name="partitions-in-multidimensional-models"></a><span data-ttu-id="655e1-102">다차원 모델의 파티션</span><span class="sxs-lookup"><span data-stu-id="655e1-102">Partitions in Multidimensional Models</span></span>
  <span data-ttu-id="655e1-103">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]에서 *파티션* 은 로드된 팩트 데이터의 실제 스토리지를 측정값 그룹에 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="655e1-103">In [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], a *partition* provides the physical storage of fact data loaded into a measure group.</span></span> <span data-ttu-id="655e1-104">각 측정값 그룹에 대해 단일 파티션이 자동으로 만들어지지만 더욱 효율적으로 처리하고 쿼리 성능이 빨라지도록 데이터를 추가로 분할하는 추가 파티션을 만드는 것이 일반적입니다.</span><span class="sxs-lookup"><span data-stu-id="655e1-104">A single partition is created for each measure group automatically, but it is common to create additional partitions that further segment the data, resulting in more efficient processing and faster query performance.</span></span>  
  
 <span data-ttu-id="655e1-105">파티션을 하나 이상의 서버에서 독립적으로 병렬 처리할 수 있기 때문에 더 효율적으로 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="655e1-105">Processing is more efficient because partitions can be processed independently and in parallel, on one or more servers.</span></span> <span data-ttu-id="655e1-106">스토리지 모드와 집계 최적화를 사용하여 응답 시간이 짧아지도록 각 파티션을 구성할 수 있기 때문에 쿼리가 더 빨리 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="655e1-106">Queries run faster because each partition can be configured to have storage modes and aggregation optimizations that result in shorter response times.</span></span> <span data-ttu-id="655e1-107">예를 들어 최신 데이터를 포함하는 파티션에 대해 MOLAP 스토리지를 선택하는 것이 ROLAP를 선택하는 경우보다 일반적으로 빠릅니다.</span><span class="sxs-lookup"><span data-stu-id="655e1-107">For example, choosing MOLAP storage for partitions containing newer data is typically faster than ROLAP.</span></span> <span data-ttu-id="655e1-108">마찬가지로, 날짜별로 분할하는 경우 최신 데이터가 들어 있는 파티션의 최적화가 액세스 빈도가 낮은 오래된 데이터가 들어 있는 파티션의 최적화보다 더 많을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="655e1-108">Likewise, if you partition by date, partitions containing newer data can have more optimizations than partitions containing older data that is accessed less frequently.</span></span> <span data-ttu-id="655e1-109">파티션을 통해 스토리지 및 집계 디자인이 바뀌면 앞으로의 병합 작업에 부정적인 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="655e1-109">Note that varying storage and aggregation design by partition will have a negative impact on future merge operations.</span></span> <span data-ttu-id="655e1-110">개별 파티션을 최적화하기 전에 병합이 파티션 관리 전략의 필수 구성 요소인지 여부를 고려해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="655e1-110">Be sure to consider whether merging is an essential component of your partition management strategy before optimizing individual partitions.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="655e1-111">여러 파티션에 대한 지원은 비즈니스 인텔리전스 버전 및 엔터프라이즈 버전에서 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="655e1-111">Support for multiple partitions is available in the business intelligence edition and enterprise edition.</span></span> <span data-ttu-id="655e1-112">스탠더드 버전에서는 여러 파티션을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="655e1-112">The standard edition does not support multiple partitions.</span></span> <span data-ttu-id="655e1-113">자세한 내용은 [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="655e1-113">For more information, see [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
## <a name="important-considerations-when-designing-a-partitioning-strategy"></a><span data-ttu-id="655e1-114">분할 전략을 디자인할 때 중요한 고려 사항</span><span class="sxs-lookup"><span data-stu-id="655e1-114">Important considerations when designing a partitioning strategy</span></span>  
 <span data-ttu-id="655e1-115">큐브 데이터의 무결성이 보장되려면 파티션 사이에 중복된 데이터가 없도록 큐브의 파티션에 데이터가 분산되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="655e1-115">The integrity of a cube's data relies on the data being distributed among the partitions of the cube such that no data is duplicated among the partitions.</span></span> <span data-ttu-id="655e1-116">파티션에서 데이터가 요약되는 경우 둘 이상의 파티션에 있는 모든 데이터 요소는 서로 다른 데이터 요소인 것처럼 요약됩니다.</span><span class="sxs-lookup"><span data-stu-id="655e1-116">When data is summarized from the partitions, any data elements that are present in more than one partition will be summarized as if they were different data elements.</span></span> <span data-ttu-id="655e1-117">따라서 이런 경우 최종 사용자에게 잘못된 요약과 오류가 있는 데이터가 제공될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="655e1-117">This can result in incorrect summaries and erroneous data provided to the end user.</span></span> <span data-ttu-id="655e1-118">예를 들어 제품 X의 판매 트랜잭션이 두 파티션의 팩트 테이블에서 중복될 경우 제품 X 판매 요약에 중복된 트랜잭션이 이중으로 계산될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="655e1-118">For example, if a sales transaction for Product X is duplicated in the fact tables for two partitions, summaries of Product X sales can include a double accounting of the duplicated transaction.</span></span>  
  
 <span data-ttu-id="655e1-119">파티션은 병합할 수 있으므로 전체적인 스토리지 및 데이터 업데이트 전략에서 이 기능을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="655e1-119">Partitions can be merged; you can use this feature in your overall storage and data update strategy.</span></span> <span data-ttu-id="655e1-120">파티션은 스토리지 모드와 집계 디자인이 동일한 경우에만 병합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="655e1-120">Partitions can be merged only if they have the same storage mode and aggregation design.</span></span> <span data-ttu-id="655e1-121">나중에 병합할 파티션을 만들려면 파티션을 만들 때 다른 파티션의 집계 디자인을 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="655e1-121">To create partitions that are candidates for later merging, you can copy the aggregation design of another partition when you create partitions.</span></span> <span data-ttu-id="655e1-122">파티션을 만든 후 이를 편집하여 다른 파티션의 집계 디자인을 복사할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="655e1-122">You can also edit a partition after it has been created to copy the aggregation design of another partition.</span></span> <span data-ttu-id="655e1-123">파티션 병합은 결과 파티션에 데이터가 중복되지 않도록 주의해서 수행해야 합니다. 데이터가 중복될 경우 정확하지 않은 큐브 데이터가 만들어질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="655e1-123">Merging partitions must also be performed carefully to avoid duplication of data in the resulting partition, which can cause cube data to be inaccurate.</span></span>  
  
## <a name="local-partitions"></a><span data-ttu-id="655e1-124">로컬 파티션</span><span class="sxs-lookup"><span data-stu-id="655e1-124">Local Partitions</span></span>  
 <span data-ttu-id="655e1-125">로컬 파티션은 한 서버에서 정의되어 처리되고 저장되는 파티션입니다.</span><span class="sxs-lookup"><span data-stu-id="655e1-125">Local partitions are partitions that are defined, processed, and stored on one server.</span></span> <span data-ttu-id="655e1-126">큐브에 큰 측정값 그룹이 있는 경우 파티션 전체에서 병렬 처리되도록 해당 측정값 그룹을 분할할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="655e1-126">If you have large measure groups in a cube, you might want to partition them out so that processing occurs in parallel across the partitions.</span></span> <span data-ttu-id="655e1-127">병렬 처리를 수행하면 실행 속도가 빨라집니다.</span><span class="sxs-lookup"><span data-stu-id="655e1-127">The advantage is that parallel processing provides faster execution.</span></span> <span data-ttu-id="655e1-128">작업을 처리 중인 파티션을 다른 파티션이 시작되기 전에 종료할 필요가 없기 때문에 두 파티션이 병렬로 실행될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="655e1-128">Because one partition processing job does not have to finish before another starts, they can run in parallel.</span></span> <span data-ttu-id="655e1-129">자세한 내용은 [로컬 파티션 만들기 및 관리&#40;Analysis Services&#41;](create-and-manage-a-local-partition-analysis-services.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="655e1-129">For more information, see [Create and Manage a Local Partition &#40;Analysis Services&#41;](create-and-manage-a-local-partition-analysis-services.md).</span></span>  
  
## <a name="remote-partitions"></a><span data-ttu-id="655e1-130">원격 파티션</span><span class="sxs-lookup"><span data-stu-id="655e1-130">Remote Partitions</span></span>  
 <span data-ttu-id="655e1-131">원격 파티션은 한 서버에서 정의되어 다른 서버에서 처리되고 저장되는 파티션입니다.</span><span class="sxs-lookup"><span data-stu-id="655e1-131">Remote partitions are partitions that are defined on one server, but are processed and stored on another.</span></span> <span data-ttu-id="655e1-132">데이터 및 메타데이터의 스토리지를 여러 서버로 분산시키려는 경우 원격 파티션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="655e1-132">If you want to distribute storage of your data and metadata across multiple servers, use remote partitions.</span></span> <span data-ttu-id="655e1-133">일반적으로 개발에서 프로덕션으로 전환하면 분석 중인 데이터의 크기가 몇 배 이상 증가합니다.</span><span class="sxs-lookup"><span data-stu-id="655e1-133">Ordinarily, when you transition from development to production, the size of data under analysis grows several times over.</span></span> <span data-ttu-id="655e1-134">이렇게 큰 데이터 청크의 경우 해당 데이터를 여러 컴퓨터로 분산할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="655e1-134">With such large chunks of data, one possible alternative is to distribute that data over multiple computers.</span></span> <span data-ttu-id="655e1-135">이는 한 컴퓨터가 모든 데이터를 보유할 수 없기 때문이기도 하지만 두 개 이상의 컴퓨터에서 데이터를 병렬로 처리할 수 있기 때문이기도 합니다.</span><span class="sxs-lookup"><span data-stu-id="655e1-135">This is not just because one computer cannot hold all the data, but because you will want more than one computer processing the data in parallel.</span></span> <span data-ttu-id="655e1-136">자세한 내용은 [원격 파티션 만들기 및 관리&#40;Analysis Services&#41;](create-and-manage-a-remote-partition-analysis-services.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="655e1-136">For more information, see [Create and Manage a Remote Partition &#40;Analysis Services&#41;](create-and-manage-a-remote-partition-analysis-services.md).</span></span>  
  
## <a name="aggregations"></a><span data-ttu-id="655e1-137">집계</span><span class="sxs-lookup"><span data-stu-id="655e1-137">Aggregations</span></span>  
 <span data-ttu-id="655e1-138">집계는 큐브 데이터의 미리 계산된 요약으로 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 에서 신속한 쿼리 응답을 제공할 수 있도록 도와 줍니다.</span><span class="sxs-lookup"><span data-stu-id="655e1-138">Aggregations are precalculated summaries of cube data that help enable [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] to provide rapid query responses.</span></span> <span data-ttu-id="655e1-139">스토리지 성능 향상에 대한 제한을 설정하거나 집계 빌드 프로세스가 얼마 동안 실행된 후 이를 임의로 중지하여 측정값 그룹에 대해 만들어지는 집계 수를 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="655e1-139">You can control the number of aggregations created for a measure group by setting limits on storage, performance gains, or arbitrarily stopping the aggregation build process after it has been running for a while.</span></span> <span data-ttu-id="655e1-140">집계 수가 많을수록 더 좋은 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="655e1-140">More aggregations are not necessarily better.</span></span> <span data-ttu-id="655e1-141">모든 새로운 집계는 디스크 공간과 처리 시간 모두에서 비용을 초래합니다.</span><span class="sxs-lookup"><span data-stu-id="655e1-141">Every new aggregation comes at a cost, both in terms of disk space and processing time.</span></span> <span data-ttu-id="655e1-142">30% 성능 향상이 되도록 집계를 만든 다음 테스트 또는 환경에서 보장하는 경우에만 집계 수를 늘리는 것이 좋습니다. 자세한 내용은 [집계 디자인&#40;Analysis Services - 다차원&#41;](designing-aggregations-analysis-services-multidimensional.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="655e1-142">We recommend creating aggregations for a thirty percent performance gain, and then raising the number only if testing or experience warrants it.For more information, see [Designing Aggregations &#40;Analysis Services - Multidimensional&#41;](designing-aggregations-analysis-services-multidimensional.md).</span></span>  
  
## <a name="partition-merging-and-editing"></a><span data-ttu-id="655e1-143">파티션 병합 및 편집</span><span class="sxs-lookup"><span data-stu-id="655e1-143">Partition Merging and Editing</span></span>  
 <span data-ttu-id="655e1-144">두 개의 파티션이 동일한 집계 디자인을 사용하는 경우 이러한 두 파티션을 하나로 병합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="655e1-144">If two partitions use the same aggregation design, you can merge those two partitions into one.</span></span> <span data-ttu-id="655e1-145">예를 들어 월별로 분할된 재고 차원이 있는 경우 월말마다 해당 월 파티션을 기존 연간 파티션에 병합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="655e1-145">For example, if you have an inventory dimension that is partitioned by month, then at the end of each calendar month, you can merge that month partition with the existing year-to-date partition.</span></span> <span data-ttu-id="655e1-146">이렇게 하면 현재 월 파티션을 신속하게 처리 및 분석할 수 있으며 해당 연도의 나머지 달은 병합될 때만 다시 처리해도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="655e1-146">This way, the current month partition can be processed and analyzed quickly, while the rest of the year in months only has to be reprocessed when merged.</span></span> <span data-ttu-id="655e1-147">이러한 다시 처리 작업은 시간이 오래 걸리며 낮은 빈도로 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="655e1-147">That reprocess requires longer processing time, and can be run less frequently.</span></span> <span data-ttu-id="655e1-148">파티션 병합 프로세스 관리 방법에 대한 자세한 내용은 [Analysis Services의 파티션 병합&#40;SSAS - 다차원 데이터&#41;](merge-partitions-in-analysis-services-ssas-multidimensional.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="655e1-148">For more information about managing the partition merging process, see [Merge Partitions in Analysis Services &#40;SSAS - Multidimensional&#41;](merge-partitions-in-analysis-services-ssas-multidimensional.md).</span></span> <span data-ttu-id="655e1-149">큐브 디자이너의 **파티션** 탭을 사용 하 여 큐브 파티션을 편집 하려면 [파티션 편집 또는 삭제 &#40;Analysis Services-다차원&#41;](edit-or-delete-partitions-analyisis-services-multidimensional.md)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="655e1-149">To edit cube partitions by using the **Partitions** tab in Cube Designer, see [Edit or Delete Partitions &#40;Analysis Services - Multidimensional&#41;](edit-or-delete-partitions-analyisis-services-multidimensional.md).</span></span>  
  
## <a name="related-topics"></a><span data-ttu-id="655e1-150">관련 항목</span><span class="sxs-lookup"><span data-stu-id="655e1-150">Related Topics</span></span>  
  
|<span data-ttu-id="655e1-151">항목</span><span class="sxs-lookup"><span data-stu-id="655e1-151">Topic</span></span>|<span data-ttu-id="655e1-152">Description</span><span class="sxs-lookup"><span data-stu-id="655e1-152">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="655e1-153">로컬 파티션 만들기 및 관리&#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="655e1-153">Create and Manage a Local Partition &#40;Analysis Services&#41;</span></span>](create-and-manage-a-local-partition-analysis-services.md)|<span data-ttu-id="655e1-154">필터 또는 다른 팩트 테이블을 사용하여 데이터가 중복되지 않도록 데이터를 분할하는 방법에 대한 정보가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="655e1-154">Contains information about how to partition data using filters or different fact tables without duplicating data.</span></span>|  
|[<span data-ttu-id="655e1-155">파티션 스토리지 설정&#40;Analysis Services - 다차원&#41;</span><span class="sxs-lookup"><span data-stu-id="655e1-155">Set Partition Storage &#40;Analysis Services - Multidimensional&#41;</span></span>](set-partition-storage-analysis-services-multidimensional.md)|<span data-ttu-id="655e1-156">파티션 스토리지를 구성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="655e1-156">Describes how to configure storage for partitions.</span></span>|  
|[<span data-ttu-id="655e1-157">파티션 편집 또는 삭제 &#40;Analysis Services-다차원&#41;</span><span class="sxs-lookup"><span data-stu-id="655e1-157">Edit or Delete Partitions &#40;Analysis Services - Multidimensional&#41;</span></span>](edit-or-delete-partitions-analyisis-services-multidimensional.md)|<span data-ttu-id="655e1-158">파티션을 보고 편집하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="655e1-158">Describes how to view and edit partitions.</span></span>|  
|[<span data-ttu-id="655e1-159">Analysis Services의 파티션 병합&#40;SSAS - 다차원 데이터&#41;</span><span class="sxs-lookup"><span data-stu-id="655e1-159">Merge Partitions in Analysis Services &#40;SSAS - Multidimensional&#41;</span></span>](merge-partitions-in-analysis-services-ssas-multidimensional.md)|<span data-ttu-id="655e1-160">데이터가 중복되지 않도록 서로 다른 팩트 테이블 또는 서로 다른 데이터 조각이 있는 파티션을 병합하는 방법에 대한 정보가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="655e1-160">Contains information about how to merge partitions that have different fact tables or different data slices without duplicating data.</span></span>|  
|[<span data-ttu-id="655e1-161">파티션 쓰기 저장(writeback) 설정</span><span class="sxs-lookup"><span data-stu-id="655e1-161">Set Partition Writeback</span></span>](set-partition-writeback.md)|<span data-ttu-id="655e1-162">파티션을 쓰기가 가능하도록 설정하는 방법을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="655e1-162">Provides instructions on write-enabling a partition.</span></span>|  
|[<span data-ttu-id="655e1-163">원격 파티션 만들기 및 관리&#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="655e1-163">Create and Manage a Remote Partition &#40;Analysis Services&#41;</span></span>](create-and-manage-a-remote-partition-analysis-services.md)|<span data-ttu-id="655e1-164">원격 파티션을 만들고 관리하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="655e1-164">Describes how to create and manage a remote partition.</span></span>|  
  
  