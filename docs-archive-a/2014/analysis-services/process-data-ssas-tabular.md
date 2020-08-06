---
title: 데이터 처리 (SSAS 테이블 형식) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: d88f2dc9-2933-4be5-9bf3-48ffbc2d0a1a
author: minewiskan
ms.author: owend
ms.openlocfilehash: e2066cb6d871f43dda719cab3539253db97bfca7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741359"
---
# <a name="process-data-ssas-tabular"></a><span data-ttu-id="0e764-102">데이터 처리(SSAS 테이블 형식)</span><span class="sxs-lookup"><span data-stu-id="0e764-102">Process Data (SSAS Tabular)</span></span>
  <span data-ttu-id="0e764-103">데이터를 테이블 형식 모델로 가져올 경우 캐시된 모드에서 가져오는 시점에 해당 데이터의 스냅샷을 캡처하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0e764-103">When you import data into a tabular model, in Cached mode, you are capturing a snapshot of that data at the time of import.</span></span> <span data-ttu-id="0e764-104">경우에 따라 이 데이터가 변경되지 않을 수 있으며 모델에서 데이터를 업데이트할 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0e764-104">In some cases, that data may never change and it does not need to be updated in the model.</span></span> <span data-ttu-id="0e764-105">하지만 가져오는 데이터가 정기적으로 변경될 수 있으므로 모델이 데이터 원본의 최신 데이터를 반영하려면 데이터를 처리(새로 고침)하고 계산된 데이터를 다시 계산해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e764-105">However, it is more likely that the data you are importing from changes regularly, and in order for your model to reflect the most recent data from the data sources, it is necessary to process (refresh) the data and re-calculate calculated data.</span></span> <span data-ttu-id="0e764-106">모델에서 데이터를 업데이트하려면 모든 테이블에 대해, 개별 테이블에 대해, 파티션별로 또는 데이터 원본 연결별로 처리 동작을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="0e764-106">To update the data in your model, you perform a process action on all tables, on an individual table, by a partition, or by a data source connection.</span></span>  
  
 <span data-ttu-id="0e764-107">모델 프로젝트를 제작할 때는 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]에서 처리 동작을 수동으로 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e764-107">When authoring your model project, process actions must be initiated manually in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="0e764-108">모델을 배포한 후 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 를 사용하여 처리 작업을 수행하거나 스크립트를 사용하여 처리 작업을 예약할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0e764-108">After a model has been deployed, process operations can be performed by using [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] or scheduled by using a script.</span></span> <span data-ttu-id="0e764-109">여기서 설명하는 태스크는 모두 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]에서 모델 제작 중에 수행할 수 있는 처리 동작과 관련됩니다.</span><span class="sxs-lookup"><span data-stu-id="0e764-109">Tasks described here all pertain to process actions that you can do during model authoring in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="0e764-110">배포된 모델의 처리 동작에 대한 자세한 내용은 [Process Database, Table, or Partition](tabular-models/process-database-table-or-partition-analysis-services.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="0e764-110">For more information about process actions for a deployed model, see [Process Database, Table, or Partition](tabular-models/process-database-table-or-partition-analysis-services.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="0e764-111">관련 작업</span><span class="sxs-lookup"><span data-stu-id="0e764-111">Related Tasks</span></span>  
  
|<span data-ttu-id="0e764-112">항목</span><span class="sxs-lookup"><span data-stu-id="0e764-112">Topic</span></span>|<span data-ttu-id="0e764-113">설명</span><span class="sxs-lookup"><span data-stu-id="0e764-113">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="0e764-114">수동으로 데이터 처리&#40;SSAS 테이블 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="0e764-114">Manually Process Data &#40;SSAS Tabular&#41;</span></span>](manually-process-data-ssas-tabular.md)|<span data-ttu-id="0e764-115">모델 작업 영역 데이터를 수동으로 처리하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="0e764-115">Describes how to manually process model workspace data.</span></span>|  
|[<span data-ttu-id="0e764-116">데이터 처리 문제 해결&#40;SSAS 테이블 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="0e764-116">Troubleshoot Process Data &#40;SSAS Tabular&#41;</span></span>](troubleshoot-process-data-ssas-tabular.md)|<span data-ttu-id="0e764-117">처리 작업의 문제를 해결하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="0e764-117">Describes how to troubleshoot process operations.</span></span>|  
  
  
