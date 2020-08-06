---
title: 전체 텍스트 인덱스 성능 향상 | Microsoft 문서
ms.custom: ''
ms.date: 04/26/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- performance [SQL Server], full-text search
- full-text queries [SQL Server], performance
- crawls [full-text search]
- full-text indexes [SQL Server], performance
- full-text search [SQL Server], performance
- batches [SQL Server], full-text search
ms.assetid: ef39ef1f-f0b7-4582-8e9c-31d4bd0ad35d
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 51b5913e9c3ce65faa5a1fddc5846cc7c94d149f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87733804"
---
# <a name="improve-the-performance-of-full-text-indexes"></a><span data-ttu-id="631e8-102">전체 텍스트 인덱스 성능 향상</span><span class="sxs-lookup"><span data-stu-id="631e8-102">Improve the Performance of Full-Text Indexes</span></span>
  <span data-ttu-id="631e8-103">전체 텍스트 인덱싱 및 전체 텍스트 쿼리의 성능은 메모리, 디스크 속도, CPU 속도 및 컴퓨터 아키텍처와 같은 하드웨어 리소스의 영향을 받습니다.</span><span class="sxs-lookup"><span data-stu-id="631e8-103">Performance for full-text indexing and full-text queries is influenced by hardware resources, such as memory, disk speed, CPU speed, and machine architecture.</span></span>  
  
##  <a name="common-causes-of-performance-issues"></a><a name="causes"></a><span data-ttu-id="631e8-104">성능 문제의 일반적인 원인</span><span class="sxs-lookup"><span data-stu-id="631e8-104">Common Causes of Performance Issues</span></span>  
 <span data-ttu-id="631e8-105">전체 텍스트 인덱싱 성능이 저하되는 주요 원인으로는 다음과 같은 하드웨어 리소스 제한을 들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="631e8-105">The main cause for reduced full-text indexing performance is hardware-resource limits:</span></span>  
  
-   <span data-ttu-id="631e8-106">필터 데몬 호스트 프로세스(fdhost.exe) 또는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 프로세스(sqlservr.exe)에 의한 CPU 사용률이 100%에 가까운 경우 CPU는 병목 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="631e8-106">If CPU usage by the filter daemon host process (fdhost.exe) or the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] process (sqlservr.exe) is close to 100 percent, the CPU is the bottleneck.</span></span>  
  
-   <span data-ttu-id="631e8-107">평균 디스크 대기 큐 길이가 디스크 헤드 수보다 두 배 이상 많은 경우 디스크에 병목 상태가 존재합니다.</span><span class="sxs-lookup"><span data-stu-id="631e8-107">If the average disk-waiting queue length is more than two times the number of disk heads, there is a bottleneck on the disk.</span></span> <span data-ttu-id="631e8-108">기본적인 해결 방법은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스 파일 및 로그와 별개인 전체 텍스트 카탈로그를 만드는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="631e8-108">The primary workaround is to create full-text catalogs that are separate from the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database files and logs.</span></span> <span data-ttu-id="631e8-109">로그, 데이터베이스 파일 및 전체 텍스트 카탈로그를 서로 다른 디스크에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="631e8-109">Put the logs, database files, and full-text catalogs on separate disks.</span></span> <span data-ttu-id="631e8-110">또한 더 빠른 디스크를 구입하고 RAID를 사용하면 인덱싱 성능을 향상시키는 데 도움이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="631e8-110">Buying faster disks and using RAID can also help improve indexing performance.</span></span>  
  
-   <span data-ttu-id="631e8-111">실제 메모리(3GB 한도)가 부족할 경우 메모리가 병목 상태일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="631e8-111">If there is a shortage of physical memory (3-GB limit), memory might be the bottleneck.</span></span> <span data-ttu-id="631e8-112">실제 메모리 제한은 모든 시스템에서 발생 가능하며 32비트 시스템의 경우 가상 메모리 가중으로 인해 전체 텍스트 인덱싱 속도가 느려질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="631e8-112">Physical memory limitations are possible on all systems, and on 32-bit systems, virtual memory pressure can slow down full-text indexing.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="631e8-113">[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]부터는 전체 텍스트 엔진이 sqlservr.exe에 속하기 때문에 AWE 메모리가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="631e8-113">Beginning in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], the Full-Text Engine can use AWE memory because the Full-Text Engine is part of the sqlservr.exe.</span></span>  
  
 <span data-ttu-id="631e8-114">시스템에 하드웨어 병목 상태가 존재하지 않을 경우 전체 텍스트 검색의 인덱싱 성능은 주로 다음 사항에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="631e8-114">If the system has no hardware bottlenecks, the indexing performance of full-text search mostly depends on the following:</span></span>  
  
-   <span data-ttu-id="631e8-115">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 전체 텍스트 일괄 처리를 만드는 데 걸리는 시간</span><span class="sxs-lookup"><span data-stu-id="631e8-115">How long it takes [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to create full-text batches.</span></span>  
  
-   <span data-ttu-id="631e8-116">필터 데몬에서 이러한 일괄 처리를 완료할 수 있는 시간</span><span class="sxs-lookup"><span data-stu-id="631e8-116">How quickly the filter daemon can consume those batches.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="631e8-117">전체 채우기와 달리 증분, 수동 및 자동 변경 내용 추적 채우기는 하드웨어 리소스를 극대화하여 더 빠른 속도를 낼 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="631e8-117">Unlike full population, incremental, manual, and auto change tracking population are not designed to maximize hardware resources to achieve faster speed.</span></span> <span data-ttu-id="631e8-118">따라서 이러한 튜닝 제안이 전체 텍스트 인덱싱의 성능을 향상시키지 않을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="631e8-118">Therefore, these tuning suggestions may not enhance performance for full-text indexing.</span></span>  
  
 <span data-ttu-id="631e8-119">채우기가 완료되면 인덱스 조각을 하나의 마스터 전체 텍스트 인덱스로 병합하는 최종 병합 프로세스가 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="631e8-119">When a population has completed, a final merge process is triggered that merges the index fragments together into one master full-text index.</span></span> <span data-ttu-id="631e8-120">이렇게 하면 많은 인덱스 조각 대신 마스터 인덱스만 쿼리하면 되기 때문에 쿼리 성능이 향상되며 개선된 평가 통계를 사용하여 관련성 등급을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="631e8-120">This results in improved query performance since only the master index needs to be queried rather than a number of index fragments, and better scoring statistics may be used for relevance ranking.</span></span> <span data-ttu-id="631e8-121">인덱스 조각을 병합할 때 많은 양의 데이터를 읽고 써야 하기 때문에 마스터 병합에 많은 I/O 사용량이 필요할 수 있지만 이로 인해 들어오는 쿼리가 차단되지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="631e8-121">Note that the master merge can be I/O intensive, because large amounts of data must be written and read when index fragments are merged, though it does not block incoming queries.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="631e8-122">많은 양의 데이터를 마스터 병합하면 장기 실행 트랜잭션이 생성될 수 있으며 이로 인해 검사점이 사용되는 동안 트랜잭션 로그의 잘림이 지연될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="631e8-122">Master merging a large amount of data can create a long running transaction, delaying truncation of the transaction log during checkpoint.</span></span> <span data-ttu-id="631e8-123">이 경우 전체 복구 모델에서 트랜잭션 로그의 크기가 대폭 증가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="631e8-123">In this case, under the full recovery model, the transaction log might grow significantly.</span></span> <span data-ttu-id="631e8-124">전체 복구 모델이 사용되는 데이터베이스에서 큰 전체 텍스트 인덱스를 다시 구성하기 전에 장기 실행 트랜잭션에 대비하여 트랜잭션 로그에 충분한 공간을 확보하는 것이 가장 좋은 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="631e8-124">As a best practice, before reorganizing a large full-text index in a database that uses the full recovery model, ensure that your transaction log contains sufficient space for a long-running transaction.</span></span> <span data-ttu-id="631e8-125">자세한 내용은 [트랜잭션 로그 파일의 크기 관리](../logs/manage-the-size-of-the-transaction-log-file.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="631e8-125">For more information, see [Manage the Size of the Transaction Log File](../logs/manage-the-size-of-the-transaction-log-file.md).</span></span>  
  
  
  
##  <a name="tuning-the-performance-of-full-text-indexes"></a><a name="tuning"></a><span data-ttu-id="631e8-126">전체 텍스트 인덱스의 성능 튜닝</span><span class="sxs-lookup"><span data-stu-id="631e8-126">Tuning the Performance of Full-Text Indexes</span></span>  
 <span data-ttu-id="631e8-127">전체 텍스트 인덱스의 성능을 극대화하려면 다음과 같은 방법을 구현하는 것이 가장 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="631e8-127">To maximize the performance of your full-text indexes, implement the following best practices:</span></span>  
  
-   <span data-ttu-id="631e8-128">모든 프로세서 또는 코어를 최대로 사용 하려면 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)' `max full-text crawl ranges` '를 시스템의 cpu 수로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="631e8-128">To use all processors or cores to the maximum, set [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)'`max full-text crawl ranges`' to the number of CPUs on the system.</span></span> <span data-ttu-id="631e8-129">이 구성 옵션에 대한 자세한 내용은 [max full-text crawl range 서버 구성 옵션](../../database-engine/configure-windows/max-full-text-crawl-range-server-configuration-option.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="631e8-129">For information about this configuration option, see [max full-text crawl range Server Configuration Option](../../database-engine/configure-windows/max-full-text-crawl-range-server-configuration-option.md).</span></span>  
  
-   <span data-ttu-id="631e8-130">기본 테이블에 클러스터형 인덱스가 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="631e8-130">Make sure that the base table has a clustered index.</span></span> <span data-ttu-id="631e8-131">클러스터형 인덱스의 첫 번째 열에 정수 데이터 형식을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="631e8-131">Use an integer data type for the first column of the clustered index.</span></span> <span data-ttu-id="631e8-132">클러스터형 인덱스의 첫 번째 열에 GUID를 사용하지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="631e8-132">Avoid using GUIDs in the first column of the clustered index.</span></span> <span data-ttu-id="631e8-133">클러스터형 인덱스에 다중 범위 채우기가 있을 경우 채우기 속도가 가장 빨라질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="631e8-133">A multi-range population on a clustered index can produce the highest population speed.</span></span> <span data-ttu-id="631e8-134">전체 텍스트 키로 사용하는 열을 정수 데이터 형식으로 설정하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="631e8-134">We recommend that the column serving as the full-text key be an integer data type.</span></span>  
  
-   <span data-ttu-id="631e8-135">[UPDATE STATISTICS](/sql/t-sql/statements/update-statistics-transact-sql) 문을 사용하여 기본 테이블의 통계를 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="631e8-135">Update the statistics of the base table by using the [UPDATE STATISTICS](/sql/t-sql/statements/update-statistics-transact-sql) statement.</span></span> <span data-ttu-id="631e8-136">더욱 중요한 것은 전체 채우기에 대한 클러스터형 인덱스 또는 전체 텍스트 키의 통계를 업데이트하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="631e8-136">More important, update the statistics on the clustered index or the full-text key for a full population.</span></span> <span data-ttu-id="631e8-137">이렇게 하면 다중 범위 채우기에서 테이블에 적절한 파티션을 생성하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="631e8-137">This helps a multi-range population to generate good partitions on the table.</span></span>  
  
-   <span data-ttu-id="631e8-138">증분 채우기의 성능을 향상시키려면 `timestamp` 열에 보조 인덱스를 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="631e8-138">Build a secondary index on a `timestamp` column if you want to improve the performance of incremental population.</span></span>  
  
-   <span data-ttu-id="631e8-139">대형 다중 CPU 컴퓨터에 대해 전체 채우기를 수행하려면 fdhost.exe 프로세스 및 운영 체제 용도로 메모리를 충분히 남기도록 `max server memory` 값을 설정하여 버퍼 풀 크기를 임시로 제한하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="631e8-139">Before you perform a full population on a large multi-CPU computer, we recommend that you temporarily limit the size of the buffer pool by setting the `max server memory` value to leave enough memory for the fdhost.exe process and operating system use.</span></span> <span data-ttu-id="631e8-140">자세한 내용은 이 항목 후반에 나오는 "필터 데몬 호스트 프로세스(fdhost.exe)의 메모리 요구 사항 예상"을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="631e8-140">For more information, see "Estimating the Memory Requirements of the Filter Daemon Host Process (fdhost.exe)," later in this topic.</span></span>  
  
  
  
##  <a name="troubleshooting-the-performance-of-full-populations"></a><a name="full"></a><span data-ttu-id="631e8-141">전체 채우기 성능 문제 해결</span><span class="sxs-lookup"><span data-stu-id="631e8-141">Troubleshooting the Performance of Full Populations</span></span>  
 <span data-ttu-id="631e8-142">성능 문제를 진단하려면 전체 텍스트 탐색 로그를 검토합니다.</span><span class="sxs-lookup"><span data-stu-id="631e8-142">To diagnose performance problems, look at the full-text crawl logs.</span></span> <span data-ttu-id="631e8-143">탐색 로그에 대한 자세한 내용은 [전체 텍스트 인덱스 채우기](../indexes/indexes.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="631e8-143">For information about crawl logs, see [Populate Full-Text Indexes](../indexes/indexes.md).</span></span>  
  
 <span data-ttu-id="631e8-144">전체 채우기 성능이 만족스럽지 못할 경우 다음 문제 해결 과정을 순서대로 따르는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="631e8-144">It is recommended that the following order of troubleshooting be followed if the performance of full populations is not satisfactory.</span></span>  
  
### <a name="physical-memory-usage"></a><span data-ttu-id="631e8-145">실제 메모리 사용률</span><span class="sxs-lookup"><span data-stu-id="631e8-145">Physical Memory Usage</span></span>  
 <span data-ttu-id="631e8-146">전체 텍스트 채우기를 수행하는 동안 fdhost.exe 또는 sqlservr.exe의 메모리가 부족하거나 아예 없을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="631e8-146">During a full-text population, it is possible for fdhost.exe or sqlservr.exe to run low on memory or to run out of memory.</span></span> <span data-ttu-id="631e8-147">전체 텍스트 탐색 로그에 fdhost.exe가 자주 다시 시작되는 것으로 나타나거나 오류 코드 8007008이 반환된 것으로 나타날 경우 이러한 프로세스 중 하나에 메모리 부족 문제가 발생한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="631e8-147">If the full-text crawl log shows that fdhost.exe is being restarted often or that error code 8007008 is being returned it means one of these processes is running out of memory.</span></span> <span data-ttu-id="631e8-148">fdhost.exe가 특히 대형 다중 CPU 컴퓨터에서 덤프를 생성하는 경우 이는 메모리 부족 때문일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="631e8-148">If fdhost.exe is producing dumps, particularly on large, multi-CPU computers, it might be running out of memory.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="631e8-149">전체 텍스트 탐색에 사용되는 메모리 버퍼에 대한 자세한 내용은 [sys.dm_fts_memory_buffers&#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-memory-buffers-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="631e8-149">To obtain information about memory buffers used by a full-text crawl, see [sys.dm_fts_memory_buffers &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-memory-buffers-transact-sql).</span></span>  
  
 <span data-ttu-id="631e8-150">가능한 원인은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="631e8-150">The possible causes are as follows:</span></span>  
  
-   <span data-ttu-id="631e8-151">전체 채우기 과정 중에 사용할 수 있는 실제 메모리 양이 0바이트인 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 버퍼 풀이 시스템의 실제 메모리를 대부분 사용 중일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="631e8-151">If amount of physical memory that is available during a full population is zero, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] buffer pool might be consuming most of the physical memory on the system.</span></span>  
  
     <span data-ttu-id="631e8-152">sqlservr.exe 프로세스는 버퍼 풀에 가능한 메모리를 구성된 최대 서버 메모리까지 모두 사용하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="631e8-152">The sqlservr.exe process tries to grab all available memory for the buffer pool, up to the configured maximum server memory.</span></span> <span data-ttu-id="631e8-153">`max server memory`에 할당된 양이 너무 많은 경우 메모리가 부족하여 fdhost.exe 프로세스에 공유 메모리를 할당할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="631e8-153">If the `max server memory` allocation is too large, out-of-memory conditions and failure to allocate shared memory can occur for the fdhost.exe process.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="631e8-154">다중 CPU 컴퓨터에서 전체 텍스트 채우기를 수행하는 과정에서 fdhost.exe와 sqlservr.exe 사이에 버퍼 풀 메모리를 위한 경합이 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="631e8-154">During a full-text population on a multi-CPU computer, contention for the buffer pool memory can occur between fdhost.exe or sqlservr.exe.</span></span> <span data-ttu-id="631e8-155">이로 인한 공유 메모리 부족으로 일괄 처리가 다시 시도되고, 메모리 스레시가 발생하며, fdhost.exe 프로세스에서 덤프가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="631e8-155">The resulting lack of shared memory causes batch retries, memory thrashing, and dumps by the fdhost.exe process.</span></span>  
  
     <span data-ttu-id="631e8-156">이 문제는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 버퍼 풀의 `max server memory` 값을 적절히 설정하면 해결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="631e8-156">You can solve this problem by setting the `max server memory` value of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] buffer pool appropriately.</span></span> <span data-ttu-id="631e8-157">자세한 내용은 이 항목 후반에 나오는 "필터 데몬 호스트 프로세스(fdhost.exe)의 메모리 요구 사항 예상"을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="631e8-157">For more information, see "Estimating the Memory Requirements of the Filter Daemon Host Process (fdhost.exe)," later in this topic.</span></span> <span data-ttu-id="631e8-158">전체 텍스트 인덱싱에 사용되는 일괄 처리 크기를 줄여도 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="631e8-158">Reducing the batch size used for full-text indexing may also help.</span></span>  
  
-   <span data-ttu-id="631e8-159">페이징 문제</span><span class="sxs-lookup"><span data-stu-id="631e8-159">A paging issue</span></span>  
  
     <span data-ttu-id="631e8-160">페이지 파일 크기가 충분하지 않은 경우(예: 증가가 제한된 소형 페이지 파일이 있는 시스템에서)에도 fdhost.exe 또는 sqlservr.exe 실행 시 메모리 부족이 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="631e8-160">Insufficient page-file size, such as on a system that has a small page file with restricted growth, can also cause the fdhost.exe or sqlservr.exe to run out of memory.</span></span>  
  
     <span data-ttu-id="631e8-161">탐색 로그에 메모리 관련 오류가 표시되지 않은 경우 과도한 페이징으로 인한 성능 저하 상태일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="631e8-161">If the crawl logs do not indicate any memory-related failures, it is likely that performance is slow due to excessive paging.</span></span>  
  
  
  
### <a name="estimating-the-memory-requirements-of-the-filter-daemon-host-process-fdhostexe"></a><span data-ttu-id="631e8-162">필터 데몬 호스트 프로세스(fdhost.exe)의 메모리 요구 사항 예상</span><span class="sxs-lookup"><span data-stu-id="631e8-162">Estimating the Memory Requirements of the Filter Daemon Host Process (fdhost.exe)</span></span>  
 <span data-ttu-id="631e8-163">채우기용으로 fdhost.exe 프로세스에서 필요로 하는 메모리 양은 사용되는 전체 텍스트 탐색 범위 수, ISM(인바운드 공유 메모리) 크기, 최대 ISM 인스턴스 수 등에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="631e8-163">The amount of memory required by the fdhost.exe process for a population depends mainly on the number of full-text crawl ranges it uses, the size of inbound shared memory (ISM), and the maximum number of ISM instances.</span></span>  
  
 <span data-ttu-id="631e8-164">필터 데몬 호스트에서 사용되는 메모리(바이트)는 다음 수식을 사용하여 대략적으로 계산할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="631e8-164">The amount of memory (in bytes) consumed by the filter daemon host can be roughly estimated by using the following formula:</span></span>  
  
 <span data-ttu-id="631e8-165">*number_of_crawl_ranges* \` ism_size '*max_outstanding_isms* \* 2</span><span class="sxs-lookup"><span data-stu-id="631e8-165">*number_of_crawl_ranges* \`ism_size\`*max_outstanding_isms*\* 2</span></span>  
  
 <span data-ttu-id="631e8-166">이 수식에서 변수 기본값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="631e8-166">The default values of the variables in the preceding formula are as follows:</span></span>  
  
|<span data-ttu-id="631e8-167">**변수**</span><span class="sxs-lookup"><span data-stu-id="631e8-167">**Variable**</span></span>|<span data-ttu-id="631e8-168">**기본값**</span><span class="sxs-lookup"><span data-stu-id="631e8-168">**Default value**</span></span>|  
|------------------|-----------------------|  
|<span data-ttu-id="631e8-169">*number_of_crawl_ranges*</span><span class="sxs-lookup"><span data-stu-id="631e8-169">*number_of_crawl_ranges*</span></span>|<span data-ttu-id="631e8-170">CPU 수</span><span class="sxs-lookup"><span data-stu-id="631e8-170">The number of CPUs</span></span>|  
|<span data-ttu-id="631e8-171">*ism_size*</span><span class="sxs-lookup"><span data-stu-id="631e8-171">*ism_size*</span></span>|<span data-ttu-id="631e8-172">x86 컴퓨터의 경우 1MB</span><span class="sxs-lookup"><span data-stu-id="631e8-172">1 MB for x86 computers</span></span><br /><br /> <span data-ttu-id="631e8-173">x64 컴퓨터의 경우 4MB, 8MB 또는 16MB(총 실제 메모리에 따라 다름)</span><span class="sxs-lookup"><span data-stu-id="631e8-173">4 MB, 8 MB, or 16MB for x64 computers, depending on the total physical memory</span></span>|  
|<span data-ttu-id="631e8-174">*max_outstanding_isms*</span><span class="sxs-lookup"><span data-stu-id="631e8-174">*max_outstanding_isms*</span></span>|<span data-ttu-id="631e8-175">x86 컴퓨터의 경우 25</span><span class="sxs-lookup"><span data-stu-id="631e8-175">25 for x86 computers</span></span><br /><br /> <span data-ttu-id="631e8-176">x64 컴퓨터의 경우 5</span><span class="sxs-lookup"><span data-stu-id="631e8-176">5 for x64 computers</span></span>|  
  
 <span data-ttu-id="631e8-177">다음 표에서는 fdhost.exe의 메모리 요구 사항을 계산하는 방법에 대한 지침을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="631e8-177">The following table presents guidelines about how to estimate the memory requirements of fdhost.exe.</span></span> <span data-ttu-id="631e8-178">이 표의 수식에 사용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="631e8-178">The formulas in this table use the following values:</span></span>  
  
-   <span data-ttu-id="631e8-179">*F*는 fdhost.exe에 필요한 예상 메모리(MB)입니다.</span><span class="sxs-lookup"><span data-stu-id="631e8-179">*F*, which is an estimate of memory needed by fdhost.exe (in MB).</span></span>  
  
-   <span data-ttu-id="631e8-180">*T*는 시스템에서 사용 가능한 실제 총 메모리(MB)입니다.</span><span class="sxs-lookup"><span data-stu-id="631e8-180">*T*, which is the total physical memory available on the system (in MB).</span></span>  
  
-   <span data-ttu-id="631e8-181">*M*-최적 `max server memory` 설정입니다.</span><span class="sxs-lookup"><span data-stu-id="631e8-181">*M*, which is the optimal `max server memory` setting.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="631e8-182">수식에 대 한 필수 정보는 아래의 <sup>1</sup>, <sup>2</sup>, <sup>3</sup>을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="631e8-182">For essential information about the formulas, see <sup>1</sup>, <sup>2</sup>, and <sup>3</sup>, below.</span></span>  
  
|<span data-ttu-id="631e8-183">플랫폼</span><span class="sxs-lookup"><span data-stu-id="631e8-183">Platform</span></span>|<span data-ttu-id="631e8-184">MB 단위로 fdhost.exe 메모리 요구 사항 예측-*F*<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="631e8-184">Estimating fdhost.exe memory requirements in MB-*F*<sup>1</sup></span></span>|<span data-ttu-id="631e8-185">최대 서버 메모리 계산 수식-*M*<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="631e8-185">Formula for calculating max server memory-*M*<sup>2</sup></span></span>|  
|--------------|---------------------------------------------------------------------|---------------------------------------------------------------|  
|<span data-ttu-id="631e8-186">x86</span><span class="sxs-lookup"><span data-stu-id="631e8-186">x86</span></span>|<span data-ttu-id="631e8-187">_F_ **=** _탐색 범위 수_ **&#42;** 50</span><span class="sxs-lookup"><span data-stu-id="631e8-187">_F_ **=** _Number of crawl ranges_ **&#42;** 50</span></span>|<span data-ttu-id="631e8-188">_M_ **= 최소 (** _T_ **,** 2000 \*\*)- *`F`* - \*\* 500</span><span class="sxs-lookup"><span data-stu-id="631e8-188">_M_ **=minimum(** _T_ **,** 2000 **)-*`F`*-** 500</span></span>|  
|<span data-ttu-id="631e8-189">X64</span><span class="sxs-lookup"><span data-stu-id="631e8-189">x64</span></span>|<span data-ttu-id="631e8-190">_F_ **=** _탐색 범위 수_ **&#42;** 10 **&#42;** 8</span><span class="sxs-lookup"><span data-stu-id="631e8-190">_F_ **=** _Number of crawl ranges_ **&#42;** 10 **&#42;** 8</span></span>|<span data-ttu-id="631e8-191">_M_ **=** _T_ **-** _F_ **-** 500</span><span class="sxs-lookup"><span data-stu-id="631e8-191">_M_ **=** _T_ **-** _F_ **-** 500</span></span>|  
  
 <span data-ttu-id="631e8-192"><sup>1</sup> 전체 채우기가 여러 개 있는 경우 각각의 fdhost.exe 메모리 요구 사항을 *F1*, *F2*등으로 개별적으로 계산 합니다.</span><span class="sxs-lookup"><span data-stu-id="631e8-192"><sup>1</sup> If multiple full populations are in progress, calculate the fdhost.exe memory requirements of each separately, as *F1*, *F2*, and so forth.</span></span> <span data-ttu-id="631e8-193">그런 다음, *M*을 _T_ **-** sigma **(** _F_i **)** 로 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="631e8-193">Then calculate *M* as _T_**-** sigma **(**_F_i **)**.</span></span>  
  
 <span data-ttu-id="631e8-194"><sup>2</sup> 500는 시스템의 다른 프로세스에 필요한 예상 메모리 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="631e8-194"><sup>2</sup> 500 MB is an estimate of the memory required by other processes in the system.</span></span> <span data-ttu-id="631e8-195">시스템이 추가 작업을 수행 중인 경우 그에 따라 이 값을 늘리십시오.</span><span class="sxs-lookup"><span data-stu-id="631e8-195">If the system is doing additional work, increase this value accordingly.</span></span>  
  
 <span data-ttu-id="631e8-196"><sup>3</sup> . *ism_size* 은 x64 플랫폼의 경우 8mb로 가정 합니다.</span><span class="sxs-lookup"><span data-stu-id="631e8-196"><sup>3</sup> .*ism_size* is assumed to be 8 MB for x64 platforms.</span></span>  
  
 <span data-ttu-id="631e8-197">**예: fdhost.exe에 필요한 예상 메모리**</span><span class="sxs-lookup"><span data-stu-id="631e8-197">**Example: Estimating the Memory Requirements of fdhost.exe**</span></span>  
  
 <span data-ttu-id="631e8-198">이 예는 8GB RAM과 4개의 듀얼 코어 프로세서가 장착된 AMD64 컴퓨터에 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="631e8-198">This example is for an AMD64 computer that has 8GM of RAM and 4 dual core processors.</span></span> <span data-ttu-id="631e8-199">첫 번째 계산에서는 fdhost.exe에 필요한 메모리인*F*를 예측합니다.</span><span class="sxs-lookup"><span data-stu-id="631e8-199">The first calculation estimates of memory needed by fdhost.exe-*F*.</span></span> <span data-ttu-id="631e8-200">탐색 범위 수는 `8`입니다.</span><span class="sxs-lookup"><span data-stu-id="631e8-200">The number of crawl ranges is `8`.</span></span>  
  
 `F = 8*10*8=640`  
  
 <span data-ttu-id="631e8-201">다음 계산은 M에 대 한 최적 값을 구합니다 `max server memory` - *M*.</span><span class="sxs-lookup"><span data-stu-id="631e8-201">The next calculation obtains the optimal value for `max server memory`-*M*.</span></span> <span data-ttu-id="631e8-202">*T*이 시스템에서 사용 가능한 총 실제 메모리 (*MB)입니다* `8192` .</span><span class="sxs-lookup"><span data-stu-id="631e8-202">*T*he total physical memory available on this system in MB-*T*-is `8192`.</span></span>  
  
 `M = 8192-640-500=7052`  
  
 <span data-ttu-id="631e8-203">**예제: 최대 서버 메모리 설정**</span><span class="sxs-lookup"><span data-stu-id="631e8-203">**Example: Setting max server memory**</span></span>  
  
 <span data-ttu-id="631e8-204">이 예에서는 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) 및 [RECONFIGURE](/sql/t-sql/language-elements/reconfigure-transact-sql) 문을 사용 하 여를 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 앞의 `max server memory` 예제에서 *M* 에 대해 계산 된 값으로 설정 합니다 `7052` .</span><span class="sxs-lookup"><span data-stu-id="631e8-204">This example uses the [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) and [RECONFIGURE](/sql/t-sql/language-elements/reconfigure-transact-sql)[!INCLUDE[tsql](../../../includes/tsql-md.md)] statements to set `max server memory` to the value calculated for *M* in the preceding example, `7052`:</span></span>  
  
```  
USE master;  
GO  
EXEC sp_configure 'max server memory', 7052;  
GO  
RECONFIGURE;  
GO  
```  
  
 <span data-ttu-id="631e8-205">**최대 서버 메모리 구성 옵션을 설정하려면**</span><span class="sxs-lookup"><span data-stu-id="631e8-205">**To set the max server memory configuration option**</span></span>  
  
-   [<span data-ttu-id="631e8-206">서버 메모리 서버 구성 옵션</span><span class="sxs-lookup"><span data-stu-id="631e8-206">Server Memory Server Configuration Options</span></span>](../../database-engine/configure-windows/server-memory-server-configuration-options.md)  
  
  
  
### <a name="factors-that-can-reduce-cpu-consumption"></a><span data-ttu-id="631e8-207">CPU 사용량을 줄일 수 있는 요소</span><span class="sxs-lookup"><span data-stu-id="631e8-207">Factors that Can Reduce CPU Consumption</span></span>  
 <span data-ttu-id="631e8-208">평균 CPU 사용량이 30% 미만이면 전체 채우기 성능이 최적의 상태가 아닌 것으로 간주됩니다.</span><span class="sxs-lookup"><span data-stu-id="631e8-208">We expect that the performance of full populations is not optimal when the average CPU consumption is lower than about 30 percent.</span></span> <span data-ttu-id="631e8-209">이 섹션에서는 CPU 사용량에 영향을 주는 몇 가지 요소에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="631e8-209">This section discusses some factors that affect CPU consumption.</span></span>  
  
-   <span data-ttu-id="631e8-210">긴 페이지 대기 시간</span><span class="sxs-lookup"><span data-stu-id="631e8-210">High wait for pages</span></span>  
  
     <span data-ttu-id="631e8-211">페이지 대기 시간이 긴지 확인하려면 다음 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 문을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="631e8-211">To find out whether a page wait time is high, execute the following [!INCLUDE[tsql](../../../includes/tsql-md.md)] statement:</span></span>  
  
    ```  
    Execute SELECT TOP 10 * FROM sys.dm_os_wait_stats ORDER BY wait_time_ms DESC;  
    ```  
  
     <span data-ttu-id="631e8-212">다음 표에서는 몇 가지 흥미로운 대기 유형을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="631e8-212">The following table describes the wait types of interest here.</span></span>  
  
    |<span data-ttu-id="631e8-213">대기 유형</span><span class="sxs-lookup"><span data-stu-id="631e8-213">Wait type</span></span>|<span data-ttu-id="631e8-214">Description</span><span class="sxs-lookup"><span data-stu-id="631e8-214">Description</span></span>|<span data-ttu-id="631e8-215">가능한 해결 방법</span><span class="sxs-lookup"><span data-stu-id="631e8-215">Possible resolution</span></span>|  
    |---------------|-----------------|-------------------------|  
    |<span data-ttu-id="631e8-216">PAGEIO_LATCH_SH(_EX 또는 _UP)</span><span class="sxs-lookup"><span data-stu-id="631e8-216">PAGEIO_LATCH_SH (_EX or _UP)</span></span>|<span data-ttu-id="631e8-217">IO 병목 상태를 나타내며, 이 경우 일반적으로 평균 디스크 큐 길이가 깁니다.</span><span class="sxs-lookup"><span data-stu-id="631e8-217">This could indicate an IO bottleneck, in which case you would typically also see a high average disk-queue length.</span></span>|<span data-ttu-id="631e8-218">전체 텍스트 인덱스를 다른 디스크의 다른 파일 그룹으로 이동하면 IO 병목 상태가 줄어들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="631e8-218">Moving the full-text index to a different filegroup on a different disk could help reduce the IO bottleneck.</span></span>|  
    |<span data-ttu-id="631e8-219">PAGELATCH_EX(또는 _UP)</span><span class="sxs-lookup"><span data-stu-id="631e8-219">PAGELATCH_EX (or _UP)</span></span>|<span data-ttu-id="631e8-220">동일한 데이터베이스 파일에 쓰기를 시도하고 있는 스레드 간에 경합이 많이 발생하고 있음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="631e8-220">This could indicate a lot of contention among threads that are trying to write to the same database file.</span></span>|<span data-ttu-id="631e8-221">전체 텍스트 인덱스가 상주하는 파일 그룹에 파일을 추가하면 이러한 경합을 완화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="631e8-221">Adding files to the filegroup on which the fulltext index resides could help alleviate such contention.</span></span>|  
  
     <span data-ttu-id="631e8-222">자세한 내용은 [sys.dm_os_wait_stats&#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-wait-stats-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="631e8-222">For more information, see [sys.dm_os_wait_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-wait-stats-transact-sql).</span></span>  
  
-   <span data-ttu-id="631e8-223">비효율적인 기본 테이블 검색</span><span class="sxs-lookup"><span data-stu-id="631e8-223">Inefficiencies in scanning the base table</span></span>  
  
     <span data-ttu-id="631e8-224">전체 채우기는 기본 테이블을 검색하여 일괄 처리를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="631e8-224">A full population scans the base table to produce batches.</span></span> <span data-ttu-id="631e8-225">이러한 테이블 검색은 다음과 같은 경우 비효율적일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="631e8-225">This table scanning could be inefficient in the following scenarios:</span></span>  
  
    -   <span data-ttu-id="631e8-226">기본 테이블에 전체 텍스트 인덱싱을 수행 중인 행 외부 열의 비율이 높을 경우 일괄 처리를 생성하기 위해 기본 테이블을 검색하면 병목 상태가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="631e8-226">If the base table has a high percentage of out-of-row columns that are being full-text indexed, scanning the base table to produce batches might be the bottleneck.</span></span> <span data-ttu-id="631e8-227">이 경우에는 `varchar(max)` 또는 `nvarchar(max)`를 사용하여 비교적 작은 행 내부 데이터를 이동하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="631e8-227">In this case, moving the smaller data in-row using `varchar(max)` or `nvarchar(max)` might help.</span></span>  
  
    -   <span data-ttu-id="631e8-228">기본 테이블이 심하게 조각화된 경우 검색이 비효율적일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="631e8-228">If the base table is very fragmented, scanning might be inefficient.</span></span> <span data-ttu-id="631e8-229">행 외부 데이터 및 인덱스 조각화를 계산하는 방법은 [sys.dm_db_partition_stats&#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-partition-stats-transact-sql) 및 [sys.dm_db_index_physical_stats&#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="631e8-229">For information about computing out-of-row data and index fragmentation, see [sys.dm_db_partition_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-partition-stats-transact-sql) and [sys.dm_db_index_physical_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql).</span></span>  
  
         <span data-ttu-id="631e8-230">조각화를 완화하기 위해 클러스터형 인덱스를 다시 구성하거나 다시 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="631e8-230">To reduce fragmentation, you can reorganize or rebuild the clustered index.</span></span> <span data-ttu-id="631e8-231">자세한 내용은 [인덱스 다시 구성 및 다시 작성](../indexes/reorganize-and-rebuild-indexes.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="631e8-231">For more information, see [Reorganize and Rebuild Indexes](../indexes/reorganize-and-rebuild-indexes.md).</span></span>  
  
  
  
##  <a name="troubleshooting-slow-indexing-performance-due-to-filters"></a><a name="filters"></a><span data-ttu-id="631e8-232">필터로 인 한 인덱싱 성능 저하 문제 해결</span><span class="sxs-lookup"><span data-stu-id="631e8-232">Troubleshooting Slow Indexing Performance Due to Filters</span></span>  
 <span data-ttu-id="631e8-233">전체 텍스트 엔진은 전체 텍스트 인덱스를 채울 때 다중 스레드 및 단일 스레드라는 두 가지 필터 유형을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="631e8-233">When populating a full-text index, the Full-Text Engine uses two types of filters: multithreaded and single-threaded.</span></span> <span data-ttu-id="631e8-234">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Word 문서와 같은 일부 문서는 다중 스레드 필터를 사용하여 필터링됩니다.</span><span class="sxs-lookup"><span data-stu-id="631e8-234">Some documents, such as [!INCLUDE[msCoName](../../includes/msconame-md.md)] Word documents, are filtered using a multithreaded filter.</span></span> <span data-ttu-id="631e8-235">그러나 Adobe Acrobat PDF(Portable Document Format) 문서와 같은 다른 문서는 단일 스레드 필터를 사용하여 필터링됩니다.</span><span class="sxs-lookup"><span data-stu-id="631e8-235">Other documents, such as Adobe Acrobat Portable Document Format (PDF) documents, are filtered using a single-threaded filter.</span></span>  
  
 <span data-ttu-id="631e8-236">보안상의 이유로 필터는 필터 데몬 호스트 프로세스에 의해 로드됩니다.</span><span class="sxs-lookup"><span data-stu-id="631e8-236">For security reasons, filters are loaded by filter daemon host processes.</span></span> <span data-ttu-id="631e8-237">서버 인스턴스는 모든 다중 스레드 필터에 대해 다중 스레드 프로세스를 사용하고 모든 단일 스레드 필터에 대해 단일 스레드 프로세스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="631e8-237">A server instance uses a multithreaded process for all multithreaded filters and a single-threaded process for all single-threaded filters.</span></span> <span data-ttu-id="631e8-238">다중 스레드 필터를 사용하는 문서에 단일 스레드 필터를 사용하는 포함 문서가 있을 경우 전체 텍스트 엔진은 해당 포함 문서에 대해 단일 스레드 프로세스를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="631e8-238">When a document that uses a multithreaded filter contains an embedded document that uses a single-threaded filter, the Full-Text Engine launches a single-threaded process for the embedded document.</span></span> <span data-ttu-id="631e8-239">예를 들어 PDF 문서가 포함된 Word 문서가 있을 경우 전체 텍스트 엔진은 Word 콘텐츠에 대해 다중 스레드 프로세스를 사용하고 PDF 콘텐츠에 대해 단일 스레드 프로세스를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="631e8-239">For example, on encountering a Word document that contains a PDF document, the Full-Text Engine uses the multithreaded process for the Word content and launches a single-threaded process for the PDF content.</span></span> <span data-ttu-id="631e8-240">그러나 이러한 환경에서는 단일 스레드 필터가 제대로 작동하지 않을 수 있으며 이로 인해 필터링 프로세스가 불안정해질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="631e8-240">A single-threaded filter might not work well in this environment, however, and could destabilize the filtering process.</span></span> <span data-ttu-id="631e8-241">이러한 포함 작업이 자주 수행되는 특정 환경에서는 필터링 프로세스 불안정화로 인해 해당 프로세스가 충돌할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="631e8-241">In certain circumstances where such embedding is common, destabilization might lead to filtering-process crashes.</span></span> <span data-ttu-id="631e8-242">충돌이 발생하면 전체 텍스트 엔진은 실패한 문서(예: 포함된 PDF 콘텐츠가 있는 Word 문서)를 단일 스레드 필터링 프로세스로 모두 다시 라우팅합니다.</span><span class="sxs-lookup"><span data-stu-id="631e8-242">When this occurs, the Full-Text Engine re-routes any failed document (for example, a Word document that contains embedded PDF content) to the single-threaded filtering process.</span></span> <span data-ttu-id="631e8-243">다시 라우팅 작업이 자주 발생하면 전체 텍스트 인덱싱 프로세스의 성능이 저하됩니다.</span><span class="sxs-lookup"><span data-stu-id="631e8-243">If re-routing occurs frequently, it results in performance degradation of the full-text indexing process.</span></span>  
  
 <span data-ttu-id="631e8-244">이 문제를 해결하려면 컨테이너 문서(이 경우 Word)의 필터를 단일 스레드 필터로 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="631e8-244">To work around this problem, mark the filter for the container document (Word in this case) as a single-threaded filter.</span></span> <span data-ttu-id="631e8-245">필터 레지스트리 값을 변경하여 지정된 필터를 단일 스레드 필터로 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="631e8-245">You can change the filter registry value to mark a given filter as a single-threaded filter.</span></span> <span data-ttu-id="631e8-246">필터를 단일 스레드 필터로 표시 하려면 필터에 대 한 **ThreadingModel** 레지스트리 값을로 설정 해야 `Apartment Threaded` 합니다.</span><span class="sxs-lookup"><span data-stu-id="631e8-246">To mark a filter as a single-threaded filter, you need to set the **ThreadingModel** registry value for the filter to `Apartment Threaded`.</span></span> <span data-ttu-id="631e8-247">단일 스레드 아파트에 대한 자세한 내용은 [COM 스레딩 모델 이해 및 사용](https://go.microsoft.com/fwlink/?LinkId=209159)백서를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="631e8-247">For information about single-threaded apartments, see the white paper [Understanding and Using COM Threading Models](https://go.microsoft.com/fwlink/?LinkId=209159).</span></span>  
  
  
  
## <a name="see-also"></a><span data-ttu-id="631e8-248">참고 항목</span><span class="sxs-lookup"><span data-stu-id="631e8-248">See Also</span></span>  
 <span data-ttu-id="631e8-249">[서버 메모리 서버 구성 옵션](../../database-engine/configure-windows/server-memory-server-configuration-options.md) </span><span class="sxs-lookup"><span data-stu-id="631e8-249">[Server Memory Server Configuration Options](../../database-engine/configure-windows/server-memory-server-configuration-options.md) </span></span>  
 <span data-ttu-id="631e8-250">[max full-text crawl range 서버 구성 옵션](../../database-engine/configure-windows/max-full-text-crawl-range-server-configuration-option.md) </span><span class="sxs-lookup"><span data-stu-id="631e8-250">[max full-text crawl range Server Configuration Option](../../database-engine/configure-windows/max-full-text-crawl-range-server-configuration-option.md) </span></span>  
 <span data-ttu-id="631e8-251">[전체 텍스트 인덱스 채우기](populate-full-text-indexes.md) </span><span class="sxs-lookup"><span data-stu-id="631e8-251">[Populate Full-Text Indexes](populate-full-text-indexes.md) </span></span>  
 <span data-ttu-id="631e8-252">[전체 텍스트 인덱스 만들기 및 관리](create-and-manage-full-text-indexes.md) </span><span class="sxs-lookup"><span data-stu-id="631e8-252">[Create and Manage Full-Text Indexes](create-and-manage-full-text-indexes.md) </span></span>  
 <span data-ttu-id="631e8-253">[sys.dm_fts_memory_buffers&#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-memory-buffers-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="631e8-253">[sys.dm_fts_memory_buffers &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-memory-buffers-transact-sql) </span></span>  
 <span data-ttu-id="631e8-254">[sys.dm_fts_memory_pools&#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-memory-pools-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="631e8-254">[sys.dm_fts_memory_pools &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-memory-pools-transact-sql) </span></span>  
 [<span data-ttu-id="631e8-255">전체 텍스트 인덱싱 문제 해결</span><span class="sxs-lookup"><span data-stu-id="631e8-255">Troubleshoot Full-Text Indexing</span></span>](troubleshoot-full-text-indexing.md)  
  
  
