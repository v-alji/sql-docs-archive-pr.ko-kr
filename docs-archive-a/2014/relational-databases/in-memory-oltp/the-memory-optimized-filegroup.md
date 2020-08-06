---
title: 메모리 액세스에 최적화된 파일 그룹 | Microsoft 문서
ms.custom: ''
ms.date: 11/19/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 14106cc9-816b-493a-bcb9-fe66a1cd4630
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: a4ab6423159d0ba5a27af152cc5578905f57eec6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660573"
---
# <a name="the-memory-optimized-filegroup"></a><span data-ttu-id="c9a64-102">메모리 액세스에 최적화된 파일 그룹</span><span class="sxs-lookup"><span data-stu-id="c9a64-102">The Memory Optimized Filegroup</span></span>
  <span data-ttu-id="c9a64-103">메모리 최적화 테이블을 만들려면 먼저 메모리 최적화 파일 그룹을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9a64-103">To create memory-optimized tables, you must first create a memory-optimized filegroup.</span></span> <span data-ttu-id="c9a64-104">메모리 최적화 파일 그룹에는 컨테이너가 하나 이상 포함되어 있고,</span><span class="sxs-lookup"><span data-stu-id="c9a64-104">The memory-optimized filegroup holds one or more containers.</span></span> <span data-ttu-id="c9a64-105">각 컨테이너에는 데이터 파일이나 델타 파일, 또는 둘 다 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c9a64-105">Each container contains data files or delta files or both.</span></span>  
  
 <span data-ttu-id="c9a64-106">`SCHEMA_ONLY` 테이블의 데이터 행이 유지되지 않고 메모리 최적화 테이블의 메타데이터와 고유하게 컴파일된 저장 프로시저가 기존 카탈로그에 저장되지만 [!INCLUDE[hek_2](../../includes/hek-2-md.md)] 엔진에는 메모리 최적화 테이블이 있는 데이터베이스에 대한 균일한 환경을 제공하기 위해 `SCHEMA_ONLY` 메모리 최적화 테이블에 대해 메모리 최적화 파일 그룹이 여전히 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="c9a64-106">Even though data rows from `SCHEMA_ONLY` tables are not persisted and the metadata for memory-optimized tables and natively compiled stored procedures is stored in the traditional catalogs, the [!INCLUDE[hek_2](../../includes/hek-2-md.md)] engine still requires a memory-optimized filegroup for `SCHEMA_ONLY` memory-optimized tables to provide a uniform experience for databases with memory-optimized tables.</span></span>  
  
 <span data-ttu-id="c9a64-107">메모리 최적화 파일 그룹은 다음과 같은 차이를 두고 파일 스트림 파일 그룹을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9a64-107">The memory-optimized filegroup is based on filestream filegroup, with the following differences:</span></span>  
  
-   <span data-ttu-id="c9a64-108">데이터베이스당 하나의 메모리 최적화 파일 그룹만 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c9a64-108">You can only create one memory-optimized filegroup per database.</span></span> <span data-ttu-id="c9a64-109">파일 그룹을 포함된 memory_optimized_data로 명시적으로 표시해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9a64-109">You need to explicitly mark the filegroup as containing memory_optimized_data.</span></span> <span data-ttu-id="c9a64-110">데이터베이스를 만들 때 파일 그룹을 만들거나 나중에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c9a64-110">You can create the filegroup when you create the database or you can add it later:</span></span>  
  
    ```sql  
    ALTER DATABASE imoltp ADD FILEGROUP imoltp_mod CONTAINS MEMORY_OPTIMIZED_DATA  
    ```  
  
-   <span data-ttu-id="c9a64-111">MEMORY_OPTIMIZED_DATA 파일 그룹에 하나 이상의 컨테이너를 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9a64-111">You need to add one or more containers to the MEMORY_OPTIMIZED_DATA filegroup.</span></span> <span data-ttu-id="c9a64-112">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="c9a64-112">For example:</span></span>  
  
    ```sql  
    ALTER DATABASE imoltp ADD FILE (name='imoltp_mod1', filename='c:\data\imoltp_mod1') TO FILEGROUP imoltp_mod  
    ```  
  
-   <span data-ttu-id="c9a64-113">메모리 최적화 파일 그룹을 만들기 위해 파일 스트림을 사용할 필요가 없습니다([FILESTREAM 사용 및 구성](../blob/enable-and-configure-filestream.md)).</span><span class="sxs-lookup"><span data-stu-id="c9a64-113">You do not need to enable filestream ([Enable and Configure FILESTREAM](../blob/enable-and-configure-filestream.md)) to create a memory-optimized filegroup.</span></span> <span data-ttu-id="c9a64-114">파일 스트림에 대한 매핑을 [!INCLUDE[hek_2](../../includes/hek-2-md.md)] 엔진이 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="c9a64-114">The mapping to filestream is done by the [!INCLUDE[hek_2](../../includes/hek-2-md.md)] engine.</span></span>  
  
-   <span data-ttu-id="c9a64-115">새 컨테이너를 메모리 최적화 파일 그룹에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c9a64-115">You can add new containers to a memory-optimized filegroup.</span></span> <span data-ttu-id="c9a64-116">메모리 최적화 내구성이 있는 테이블에 필요한 저장소를 확장 하 고 여러 컨테이너 간에 i/o를 분산 하기 위해 새 컨테이너가 필요할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c9a64-116">You may need a new container to expand the storage needed for durable memory-optimized table and also to distribute I/O across multiple containers.</span></span>  
  
-   <span data-ttu-id="c9a64-117">메모리 최적화 파일 그룹이 포함된 데이터 이동은 AlwaysOn 가용성 그룹 구성에 최적화되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c9a64-117">Data movement with a memory-optimized filegroup is optimized in an AlwaysOn Availability Group configuration.</span></span> <span data-ttu-id="c9a64-118">보조 복제본에 전송되는 파일 스트림 파일과는 달리 메모리 최적화 파일 그룹 내에 있는 검사점 파일(데이터 및 델타)은 보조 복제본에 전송되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c9a64-118">Unlike filestream files that are sent to secondary replicas, the checkpoint files (both data and delta) within the memory-optimized filegroup are not sent to secondary replicas.</span></span> <span data-ttu-id="c9a64-119">보조 복제본에서 트랜잭션 로그를 사용하여 데이터 및 델타 파일이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="c9a64-119">The data and delta files are constructed using the transaction log on the secondary replica.</span></span>  
  
<span data-ttu-id="c9a64-120">다음은 메모리 최적화 파일 그룹의 제한 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="c9a64-120">The following limitations of memory-optimized filegroup,</span></span>  
  
-   <span data-ttu-id="c9a64-121">메모리 최적화 파일 그룹을 만들었으면 데이터베이스를 삭제하는 방식으로만 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c9a64-121">Once you create a memory-optimized filegroup, you can only remove it by dropping the database.</span></span> <span data-ttu-id="c9a64-122">프로덕션 환경에서 메모리 최적화 파일 그룹을 제거하지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c9a64-122">In a production environment, it is unlikely that you will need to remove the memory-optimized filegroup.</span></span>  
  
-   <span data-ttu-id="c9a64-123">비어 있지 않은 컨테이너를 제거하거나 데이터 및 델타 파일 쌍을 메모리 최적화 파일 그룹의 다른 컨테이너로 이동할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c9a64-123">You cannot drop a non-empty container or move data and delta file pairs to another container in the memory-optimized filegroup.</span></span>  
  
## <a name="configuring-a-memory-optimized-filegroup"></a><span data-ttu-id="c9a64-124">메모리 액세스에 최적화된 파일 그룹 구성</span><span class="sxs-lookup"><span data-stu-id="c9a64-124">Configuring a Memory-Optimized Filegroup</span></span>  
<span data-ttu-id="c9a64-125">메모리 최적화 파일 그룹에 여러 컨테이너를 만들고 다른 드라이브에 분산하여 메모리에 데이터를 스트리밍하는 더 많은 대역폭을 얻어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9a64-125">Consider creating multiple containers in the memory-optimized filegroup and distribute them on different drives to achieve more bandwidth to stream the data into memory.</span></span>  
  
<span data-ttu-id="c9a64-126">스토리지를 구성할 때 메모리 최적화 내구성이 있는 테이블 크기의 4배 정도의 여유 디스크 공간을 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9a64-126">When configuring storage, you must provide free disk space that is four times the size of durable memory-optimized tables.</span></span> <span data-ttu-id="c9a64-127">I/o 하위 시스템이 작업에 필요한 IOPS를 지원 하는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9a64-127">Ensure that your I/O subsystem supports the required IOPS for your workload.</span></span> <span data-ttu-id="c9a64-128">제공된 IOPS에 데이터 및 델타 파일 쌍이 채워지는 경우 저장 및 병합 작업 계정에 대한 IOPS의 3배가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="c9a64-128">If data and delta file pairs are populated at a given IOPS, you need three times that IOPS to account for storing and merge operations.</span></span> <span data-ttu-id="c9a64-129">메모리 최적화 파일 그룹에 하나 이상의 컨테이너를 추가하여 스토리지 용량 및 IOPS를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c9a64-129">You can add storage capacity and IOPS by adding one or more containers to the memory-optimized filegroup.</span></span>  
  
<span data-ttu-id="c9a64-130">여러 컨테이너에서 여러 드라이브 시나리오, 데이터 및 델타 파일이 라운드 로빈 방식으로 컨테이너에 할당됩니다.</span><span class="sxs-lookup"><span data-stu-id="c9a64-130">In a multiple container, multiple drive scenario, data and delta files are allocated in a round-robin fashion into containers.</span></span> <span data-ttu-id="c9a64-131">첫 번째 데이터 파일이 첫 번째 컨테이너에서 할당되고 델타 파일이 다음 컨테이너에서 할당되고 이러한 할당 방식이 반복됩니다.</span><span class="sxs-lookup"><span data-stu-id="c9a64-131">The first data file is allocated from the first container and the delta file is allocated from the next container and this allocation pattern repeats.</span></span> <span data-ttu-id="c9a64-132">홀수 개수의 드라이브가 있고 각각이 한 컨테이너에 매핑된 경우 이러한 할당 체계가 데이터 및 델타 파일을 컨테이너에 동등하게 배포합니다.</span><span class="sxs-lookup"><span data-stu-id="c9a64-132">This allocation scheme distributes data and delta files evenly across containers if you have an odd number of drives, each mapped to one container.</span></span> <span data-ttu-id="c9a64-133">그러나 짝수 개수의 드라이브가 있고 각각이 컨테이너에 매핑된 경우 홀수 개 드라이브에 매핑된 데이터 파일과 짝수 개 드라이브에 매핑된 델타 파일 스토리지가 불균형을 이룰 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c9a64-133">However, if you have an even number of drives, each mapped to a container, it can result in imbalanced storage with data files mapped to odd drives and delta files mapped to even drives.</span></span> <span data-ttu-id="c9a64-134">복구 시 분산 된 i/o 스트림을 얻으려면 아래 예제에 설명 된 것과 같이 데이터 및 델타 파일 쌍을 동일한 스핀 들/저장소에 배치 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="c9a64-134">To obtain a balanced stream of I/O on recovery, consider placing pairs of data and delta files on the same spindles/storage as described in the example below.</span></span>  

> [!CAUTION]
> <span data-ttu-id="c9a64-135">`MAXSIZE` 값이 메모리 최적화 파일 그룹에 대해 설정되고 검사점 파일이 컨테이너의 최대 크기를 초과하는 경우 데이터베이스는 주의 대상 상태가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c9a64-135">If a `MAXSIZE` value is set for the memory-optimized filegroup, and checkpoint files exceed the max size of the container, then the database will become SUSPECT.</span></span>   
> <span data-ttu-id="c9a64-136">이 경우 데이터베이스가 RECOVERY_PENDING 상태에 유지될 수 있으므로 데이터베이스를 OFFLINE 및 ONLINE으로 설정하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="c9a64-136">In this case do not attempt to set the database OFFLINE and ONLINE, causing the database to stay in RECOVERY_PENDING state.</span></span>
  
### <a name="example"></a><span data-ttu-id="c9a64-137">예제</span><span class="sxs-lookup"><span data-stu-id="c9a64-137">Example</span></span> 
<span data-ttu-id="c9a64-138">메모리 최적화 파일 그룹은 X 드라이브의 컨테이너 1 컨테이너와 드라이브 Y의 컨테이너 2를 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="c9a64-138">Consider a memory-optimized filegroup with two containers: container 1 on drive X and container 2 on drives Y.</span></span>  
<span data-ttu-id="c9a64-139">데이터 및 델타 파일 할당이 라운드 로빈 방식으로 수행되므로 컨테이너 1에는 데이터 파일만 있고 컨테이너 2에는 델타 파일만 있게 되는데 데이터 파일이 델타 파일보다 훨씬 크므로 이로 인해 초당 입력/출력 작업뿐만 아니라 스토리지가 불균형 상태에 이릅니다.</span><span class="sxs-lookup"><span data-stu-id="c9a64-139">Since the allocation of data and delta files is done in round-robin fashion, container 1 will only have data files and container 2 will only have delta files, which leads to imbalanced persistence for storage as well as input/output operations per second, as data files are significantly larger than the delta files.</span></span>    
<span data-ttu-id="c9a64-140">X 및 Y 드라이브에 걸쳐 일관 되 게 데이터 및 델타 파일을 배포 하려면 2 대신 4 개의 컨테이너를 만든 다음 처음 두 컨테이너를 X 드라이브에 매핑하고 다음 두 컨테이너를 Y 드라이브에 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="c9a64-140">To distribute data and delta files uniformly across drives X and Y, create four containers instead of two, and map the first two containers to drive X and the next two containers to drive Y.</span></span>  
<span data-ttu-id="c9a64-141">라운드 로빈 할당을 사용 하는 경우 첫 번째 데이터와 첫 번째 델타 파일은 X 드라이브에 매핑되는 컨테이너-1과 컨테이너-2에서 각각 할당 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c9a64-141">With round-robin allocation, the first data and first delta file will be allocated from container-1 and container-2 respectively, which are mapped to drive X.</span></span>   
<span data-ttu-id="c9a64-142">마찬가지로 다음 데이터 및 델타 파일은 Y 드라이브에 매핑된 컨테이너-3 및 컨테이너-4에서 할당 됩니다. 이를 통해 두 드라이브에 데이터 및 델타 파일을 균등 하 게 분산할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c9a64-142">Similarly, the next data and delta file will be allocated from container-3 and container-4 which are mapped to drive Y. This allows distributing data and delta files across two drives uniformly.</span></span>  
 
  
## <a name="see-also"></a><span data-ttu-id="c9a64-143">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c9a64-143">See Also</span></span>  
<span data-ttu-id="c9a64-144">[메모리 액세스에 최적화된 개체의 스토리지 만들기 및 관리](creating-and-managing-storage-for-memory-optimized-objects.md)   </span><span class="sxs-lookup"><span data-stu-id="c9a64-144">[Creating and Managing Storage for Memory-Optimized Objects](creating-and-managing-storage-for-memory-optimized-objects.md)   </span></span>  
[<span data-ttu-id="c9a64-145">데이터베이스 파일 및 파일 그룹</span><span class="sxs-lookup"><span data-stu-id="c9a64-145">Database Files and Filegroups</span></span>](../../relational-databases/databases/database-files-and-filegroups.md)    
  
