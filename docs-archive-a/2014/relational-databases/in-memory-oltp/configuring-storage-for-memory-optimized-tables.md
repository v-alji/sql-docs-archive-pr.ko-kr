---
title: 메모리 액세스에 최적화된 테이블 스토리지 구성 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 6e005de0-3a77-4b91-b497-14cc0f9f6605
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 4e6e5f5a931669e2fc07cb957e60fd9c77b9b735
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741008"
---
# <a name="configuring-storage-for-memory-optimized-tables"></a><span data-ttu-id="d52dc-102">메모리 액세스에 최적화된 테이블 스토리지 구성</span><span class="sxs-lookup"><span data-stu-id="d52dc-102">Configuring Storage for Memory-Optimized Tables</span></span>
  <span data-ttu-id="d52dc-103">스토리지 용량 및 IOPS(초당 입력/출력 작업)를 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d52dc-103">You need to configure storage capacity and input/output operations per second (IOPS).</span></span>  
  
## <a name="storage-capacity"></a><span data-ttu-id="d52dc-104">스토리지 용량</span><span class="sxs-lookup"><span data-stu-id="d52dc-104">Storage Capacity</span></span>  
 <span data-ttu-id="d52dc-105">데이터베이스의 메모리 최적화 내구성 있는 테이블의 메모리 내 크기를 측정하려면 [메모리 최적화 테이블에 필요한 메모리 예측](memory-optimized-tables.md) 의 정보를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="d52dc-105">Use the information in [Estimate Memory Requirements for Memory-Optimized Tables](memory-optimized-tables.md) to estimate the in-memory size of the database's durable memory-optimized tables.</span></span> <span data-ttu-id="d52dc-106">인덱스가 메모리 최적화 테이블에 유지되지 않으므로 인덱스 크기를 포함하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="d52dc-106">Because indexes are not persisted for memory-optimized tables, do not include the size of indexes.</span></span> <span data-ttu-id="d52dc-107">크기를 결정했으면 내구성이 있는 메모리 내 테이블 크기의 4배에 해당하는 디스크 공간을 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d52dc-107">Once you determine the size, you need to provide disk space that is four times the size of durable, in-memory tables.</span></span>  
  
## <a name="storage-performance"></a><span data-ttu-id="d52dc-108">스토리지 성능</span><span class="sxs-lookup"><span data-stu-id="d52dc-108">Storage Performance</span></span>  
 [!INCLUDE[hek_2](../../includes/hek-2-md.md)] <span data-ttu-id="d52dc-109">는 작업 처리량을 크게 증가시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d52dc-109">can significantly increase your workload throughput.</span></span> <span data-ttu-id="d52dc-110">따라서 IO가 병목 상태가 아니어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d52dc-110">Therefore, it is important to ensure that IO is not a bottleneck.</span></span>  
  
-   <span data-ttu-id="d52dc-111">디스크 기반 테이블을 메모리 최적화 테이블에 마이그레이션하는 경우 트랜잭션 로그가 증가된 트랜잭션 로그 작업을 지원할 수 있는 스토리지 미디어에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d52dc-111">When migrating disk-based tables to memory-optimized tables, make sure that the transaction log is on a storage media that can support increased transaction log activity.</span></span> <span data-ttu-id="d52dc-112">예를 들어 스토리지 미디어가 100MB/초로 트랜잭션 로그 작업을 지원하고 메모리 최적화 테이블이 5배 뛰어난 성능을 발휘하는 경우 트랜잭션 로그의 스토리지 미디어는 트랜잭션 로그 작업에 성능 병목 상태가 발생하지 않도록 5배의 성능 향상을 지원할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d52dc-112">For example, if your storage media supports transaction log operations at 100 MB/sec, and memory-optimized tables result in five times greater performance, the transaction log's storage media must be able to also support five times performance improvement, to prevent the transaction log activity from becoming a performance bottleneck.</span></span>  
  
-   <span data-ttu-id="d52dc-113">메모리 액세스에 최적화된 테이블은 하나 이상의 컨테이너 간에 분산된 파일에서 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="d52dc-113">Memory-optimized tables are persisted in files distributed across one or more containers.</span></span> <span data-ttu-id="d52dc-114">각각의 컨테이너는 일반적으로 자체 스핀들에 매핑되고 증가된 스토리지 용량 및 향상된 성능을 위해 모두 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="d52dc-114">Each container should typically be mapped to its own spindle and is used both for increased storage capacity and improved performance.</span></span> <span data-ttu-id="d52dc-115">저장소 미디어의 순차 IOPS가 트랜잭션 로그 처리량의 3 배 증가를 지원할 수 있는지 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d52dc-115">You need to ensure that sequential IOPS of the storage media can support a 3 times increase in transaction log throughput.</span></span>  
  
     <span data-ttu-id="d52dc-116">예를 들어 메모리 최적화 테이블이 트랜잭션 로그에서 500MB/sec 활동을 생성 하는 경우 메모리 최적화 테이블의 저장소는 1.5 g b/초를 지원 해야 합니다. 트랜잭션 로그 처리량의 3 배 증가를 지원 해야 하는 것은 데이터 및 델타 파일 쌍을 초기 데이터에 먼저 쓴 다음 병합 작업의 일부로 읽고 다시 써야 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="d52dc-116">For example, if memory-optimized tables generate 500MB/sec of activity in the transaction log, the storage for memory-optimized tables must support 1.5GB/sec. The need to support a 3 times increase in transaction log throughput comes from the observation that the data and delta file pairs are first written with the initial data and then need to be read/re-written as part of a merge operation.</span></span>  
  
     <span data-ttu-id="d52dc-117">스토리지 처리량을 측정하는 다른 요소는 메모리 최적화 테이블의 복구 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="d52dc-117">Another factor in estimating throughput for storage is the recovery time for memory-optimized tables.</span></span> <span data-ttu-id="d52dc-118">애플리케이션에서 데이터베이스를 사용할 수 있으려면 먼저 내구성이 있는 테이블의 데이터를 메모리에서 읽어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d52dc-118">Data from durable tables must be read into memory before a database is made available to applications.</span></span> <span data-ttu-id="d52dc-119">일반적으로 메모리 최적화 테이블로 데이터 로드는 IOPS의 속도로 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d52dc-119">Commonly, loading data into memory-optimized tables can be done at the speed of IOPS.</span></span> <span data-ttu-id="d52dc-120">메모리 최적화 내구성 있는 테이블의 전체 스토리지가 60GB이고 이 데이터를 1분 내에 로드할 수 있으려면 스토리지의 IOPS를 1GB/초로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d52dc-120">So if the total storage for durable, memory-optimized tables is 60 GB and you want to be able to load this data in 1 minute, the IOPS for the storage must be set at 1 GB/sec.</span></span>  
  
-   <span data-ttu-id="d52dc-121">짝수 개의 스핀들이 있는 경우 컨테이너 개수의 두 배를 만들어야 하고 각 쌍은 같은 스핀들에 매핑되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d52dc-121">If you have even number of spindles, you should create two times the number of containers, each pair mapped to the same spindle.</span></span> <span data-ttu-id="d52dc-122">이는 IOPS 및 스토리지를 전파하는 데 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="d52dc-122">This is needed to spread the IOPS and the storage.</span></span> <span data-ttu-id="d52dc-123">자세한 내용은 메모리 액세스에 [최적화 된 파일 그룹](the-memory-optimized-filegroup.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d52dc-123">For more information, see [The Memory Optimized Filegroup](the-memory-optimized-filegroup.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d52dc-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d52dc-124">See Also</span></span>  
 [<span data-ttu-id="d52dc-125">메모리 최적화 개체에 대한 스토리지 만들기 및 관리</span><span class="sxs-lookup"><span data-stu-id="d52dc-125">Creating and Managing Storage for Memory-Optimized Objects</span></span>](creating-and-managing-storage-for-memory-optimized-objects.md)  
  
  
