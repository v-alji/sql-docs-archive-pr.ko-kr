---
title: 원격 파티션 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- storage [Analysis Services], partitions
- archiving remote partitions [Analysis Services]
- partitions [Analysis Services], remote
- restoring remote partitions [Analysis Services]
- backing up remote partitions [Analysis Services]
- partitions [Analysis Services], storage
- storing data [Analysis Services], partitions
- remote partitions [Analysis Services]
ms.assetid: 63f5d9f5-c6b6-4ceb-94fe-7b6c396d10bb
author: minewiskan
ms.author: owend
ms.openlocfilehash: 32fdf05d061d4e1c1da6ec0ef9179ecd12bda172
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87733239"
---
# <a name="remote-partitions"></a><span data-ttu-id="7d644-102">원격 파티션</span><span class="sxs-lookup"><span data-stu-id="7d644-102">Remote Partitions</span></span>
  <span data-ttu-id="7d644-103">원격 파티션의 데이터는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 파티션과 해당 부모 큐브의 정의 (메타 데이터)가 포함 된 인스턴스와 다른 Microsoft 인스턴스에 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7d644-103">The data of a remote partition is stored on a different instance of Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] than the instance that contains the definitions (metadata) of the partition and its parent cube.</span></span> <span data-ttu-id="7d644-104">원격 파티션은 파티션과 해당 부모 큐브가 정의된 것과 동일한 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스에서 관리됩니다.</span><span class="sxs-lookup"><span data-stu-id="7d644-104">A remote partition is administered on the same instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] where the partition and its parent cube are defined.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7d644-105">원격 파티션을 저장 하려면 컴퓨터에가 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 설치 되어 있어야 하며 파티션이 정의 된 인스턴스와 동일한 Service Pack 수준을 실행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d644-105">To store a remote partition, the computer must have an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] installed and be running the same service pack level as the instance where the partition was defined.</span></span> <span data-ttu-id="7d644-106">이전 버전의 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스에서는 원격 파티션이 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7d644-106">Remote partitions on instances of an earlier version of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] are not supported.</span></span>  
  
 <span data-ttu-id="7d644-107">측정값 그룹에 원격 파티션이 포함되어 있는 경우 큐브의 메모리 및 CPU 사용률이 측정값 그룹의 모든 파티션에 분산됩니다.</span><span class="sxs-lookup"><span data-stu-id="7d644-107">When remote partitions are included in a measure group, the memory and CPU utilization of the cube is distributed across all the partitions in the measure group.</span></span> <span data-ttu-id="7d644-108">예를 들어 원격 파티션을 단독으로 또는 부모 큐브 처리의 일부로 처리하는 경우 해당 파티션의 메모리와 CPU가 대부분 원격 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스에서 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="7d644-108">For example, when a remote partition is processed, either alone or as part of parent cube processing, most of the memory and CPU utilization for that partition occurs on the remote instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7d644-109">원격 파티션을 포함하는 큐브는 쓰기 가능 차원을 포함할 수 있지만 이로 인해 큐브 성능이 저하될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d644-109">A cube that contains remote partitions can contain write-enabled dimensions; however, this may affect performance for the cube.</span></span> <span data-ttu-id="7d644-110">쓰기 가능 차원에 대 한 자세한 내용은 [쓰기 가능 차원](../multidimensional-models-olap-logical-dimension-objects/write-enabled-dimensions.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="7d644-110">For more information about write-enabled dimensions, see [Write-Enabled Dimensions](../multidimensional-models-olap-logical-dimension-objects/write-enabled-dimensions.md).</span></span>  
  
## <a name="storage-modes-for-remote-partitions"></a><span data-ttu-id="7d644-111">원격 파티션에 대한 스토리지 모드</span><span class="sxs-lookup"><span data-stu-id="7d644-111">Storage Modes for Remote Partitions</span></span>  
 <span data-ttu-id="7d644-112">원격 파티션에서는 로컬 파티션에 사용되는 MOLAP(다차원 OLAP), HOLAP(하이브리드 OLAP) 또는 ROLAP(관계형 OLAP) 등의 스토리지 유형을 모두 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d644-112">Remote partitions may use any of the storage types used by local partitions: multidimensional OLAP (MOLAP), hybrid OLAP (HOLAP), or relational OLAP (ROLAP).</span></span> <span data-ttu-id="7d644-113">원격 파티션에서 자동 관리 캐싱을 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d644-113">Remote partitions may also use proactive caching.</span></span> <span data-ttu-id="7d644-114">원격 파티션의 스토리지 모드에 따라 원격 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스에 저장되는 데이터가 다음과 같이 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="7d644-114">Depending on the storage mode of a remote partition, the following data is stored on the remote instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7d644-115">스토리지 유형</span><span class="sxs-lookup"><span data-stu-id="7d644-115">Storage Type</span></span>|<span data-ttu-id="7d644-116">데이터</span><span class="sxs-lookup"><span data-stu-id="7d644-116">Data</span></span>|  
|<span data-ttu-id="7d644-117">MOLAP</span><span class="sxs-lookup"><span data-stu-id="7d644-117">MOLAP</span></span>|<span data-ttu-id="7d644-118">파티션의 집계 및 파티션의 원본 데이터에 대한 복사본</span><span class="sxs-lookup"><span data-stu-id="7d644-118">The partition's aggregations and a copy of the partition's source data</span></span>|  
|<span data-ttu-id="7d644-119">HOLAP</span><span class="sxs-lookup"><span data-stu-id="7d644-119">HOLAP</span></span>|<span data-ttu-id="7d644-120">파티션 집계</span><span class="sxs-lookup"><span data-stu-id="7d644-120">The partitions aggregations</span></span>|  
|<span data-ttu-id="7d644-121">ROLAP</span><span class="sxs-lookup"><span data-stu-id="7d644-121">ROLAP</span></span>|<span data-ttu-id="7d644-122">파티션 데이터가 저장되지 않음</span><span class="sxs-lookup"><span data-stu-id="7d644-122">No partition data</span></span>|  
  
 <span data-ttu-id="7d644-123">측정값 그룹에 여러 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스에 저장된 MOLAP 또는 HOLAP 파티션이 여러 개 포함되어 있으면 큐브가 측정값 그룹의 데이터를 해당 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스 간에 분산합니다.</span><span class="sxs-lookup"><span data-stu-id="7d644-123">If a measure group contains multiple MOLAP or HOLAP partitions stored on multiple instances of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], the cube distributes the data in the measure group data among those instances of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>  
  
## <a name="merging-remote-partitions"></a><span data-ttu-id="7d644-124">원격 파티션 병합</span><span class="sxs-lookup"><span data-stu-id="7d644-124">Merging Remote Partitions</span></span>  
 <span data-ttu-id="7d644-125">원격 파티션은 동일한 원격 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스에 저장된 다른 원격 파티션과만 병합될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d644-125">Remote partitions can be merged only with other remote partitions that are stored on the same remote instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="7d644-126">파티션 병합에 대 한 자세한 내용은 [Analysis Services &#40;SSAS-다차원&#41;병합 파티션 ](../multidimensional-models/merge-partitions-in-analysis-services-ssas-multidimensional.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="7d644-126">For more information about merging partitions, see [Merge Partitions in Analysis Services &#40;SSAS - Multidimensional&#41;](../multidimensional-models/merge-partitions-in-analysis-services-ssas-multidimensional.md).</span></span>  
  
## <a name="archiving-and-restoring-remote-partitions"></a><span data-ttu-id="7d644-127">원격 파티션 보관 및 복원</span><span class="sxs-lookup"><span data-stu-id="7d644-127">Archiving and Restoring Remote Partitions</span></span>  
 <span data-ttu-id="7d644-128">원격 파티션을 저장하는 데이터베이스를 보관하거나 복원하는 경우 원격 파티션의 데이터를 보관하거나 복원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d644-128">Data in remote partitions can be archived or restored when the database that stores the remote partition is archived or restored.</span></span> <span data-ttu-id="7d644-129">원격 파티션을 복원하지 않고 데이터베이스를 복원하는 경우에는 먼저 원격 파티션을 처리해야 파티션에서 데이터를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d644-129">If you restore a database without restoring a remote partition, you must process the remote partition before you can use the data in the partition.</span></span> <span data-ttu-id="7d644-130">데이터베이스를 보관 및 복원 하는 방법에 대 한 자세한 내용은 [Analysis Services 데이터베이스의 백업 및 복원](../multidimensional-models/backup-and-restore-of-analysis-services-databases.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="7d644-130">For more information about archiving and restoring databases, see [Backup and Restore of Analysis Services Databases](../multidimensional-models/backup-and-restore-of-analysis-services-databases.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d644-131">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7d644-131">See Also</span></span>  
 <span data-ttu-id="7d644-132">[Analysis Services&#41;&#40;원격 파티션 만들기 및 관리](../multidimensional-models/create-and-manage-a-remote-partition-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="7d644-132">[Create and Manage a Remote Partition &#40;Analysis Services&#41;](../multidimensional-models/create-and-manage-a-remote-partition-analysis-services.md) </span></span>  
 [<span data-ttu-id="7d644-133">Analysis Services 개체 처리</span><span class="sxs-lookup"><span data-stu-id="7d644-133">Processing Analysis Services Objects</span></span>](../multidimensional-models/processing-analysis-services-objects.md)  
  
  
