---
title: 메모리 액세스에 최적화된 테이블이 있는 데이터베이스의 증분 복원 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 732c9721-8dd4-481d-8ff9-1feaaa63f84f
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: ed23f08d40e23b1d43c1b642f4089fe77646b675
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738374"
---
# <a name="piecemeal-restore-of-databases-with-memory-optimized-tables"></a><span data-ttu-id="27d36-102">메모리 액세스에 최적화된 테이블이 있는 데이터베이스의 증분 복원</span><span class="sxs-lookup"><span data-stu-id="27d36-102">Piecemeal Restore of Databases With Memory-Optimized Tables</span></span>
  <span data-ttu-id="27d36-103">증분 복원은 아래에 설명된 한 가지 제한 사항을 제외하고 메모리 최적화 테이블이 있는 데이터베이스에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="27d36-103">Piecemeal restore is supported on databases with memory-optimized tables except for one restriction described below.</span></span> <span data-ttu-id="27d36-104">증분 백업 및 복원에 대한 자세한 내용은 [RESTORE&#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) 및 [증분 복원&#40;SQL Server&#41;](../backup-restore/piecemeal-restores-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="27d36-104">For more information about piecemeal backup and restore, see [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) and [Piecemeal Restores &#40;SQL Server&#41;](../backup-restore/piecemeal-restores-sql-server.md).</span></span>  
  
 <span data-ttu-id="27d36-105">메모리 최적화 파일 그룹은 주 파일 그룹과 함께 백업하고 복원해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="27d36-105">A memory-optimized filegroup must be backed up and restored together with the primary filegroup:</span></span>  
  
-   <span data-ttu-id="27d36-106">주 파일 그룹을 백업(또는 복원)하는 경우 메모리 최적화 파일 그룹을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="27d36-106">If you back up (or restore) the primary filegroup you must specify the memory-optimized filegroup.</span></span>  
  
-   <span data-ttu-id="27d36-107">메모리 최적화 파일 그룹을 백업(또는 복원)하는 경우 주 파일 그룹을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="27d36-107">If you backup (or restore) the memory-optimized filegroup you must specify the primary filegroup.</span></span>  
  
 <span data-ttu-id="27d36-108">증분 백업 및 복원에 대한 주요 시나리오는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="27d36-108">Key scenarios for piecemeal backup and restore are,</span></span>  
  
-   <span data-ttu-id="27d36-109">증분 백업을 사용하면 백업 크기를 줄일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="27d36-109">Piecemeal backup allows you to reduce the size of backup.</span></span> <span data-ttu-id="27d36-110">몇 가지 예는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="27d36-110">Some examples:</span></span>  
  
    -   <span data-ttu-id="27d36-111">작업에 미치는 영향을 최소화하기 위해 데이터베이스 백업이 몇 차례에 걸쳐 서로 다른 시간이나 서로 다른 날에 수행되도록 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="27d36-111">Configure the database backup to occur at different times or days to minimize the impact on the workload.</span></span> <span data-ttu-id="27d36-112">한 가지 예는 전체 데이터베이스 백업을 데이터베이스 유지 관리에 할당된 시간 안에 완료할 수 없을 정도로 매우 큰 데이터베이스(1TB 이상)입니다.</span><span class="sxs-lookup"><span data-stu-id="27d36-112">One example is a very large database (greater than 1 TB) where a full database backup cannot complete in the time allocated for database maintenance.</span></span> <span data-ttu-id="27d36-113">이 경우 증분 백업을 사용하여 전체 데이터베이스를 여러 증분 백업에서 백업할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="27d36-113">In that situation, you can use piecemeal backup to backup the full database in multiple piecemeal backups.</span></span>  
  
    -   <span data-ttu-id="27d36-114">파일 그룹이 읽기 전용으로 표시된 경우 읽기 전용으로 표시된 후에는 트랜잭션 로그 백업이 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="27d36-114">If a filegroup is marked read-only, it does not require a transaction log backup after it was marked read-only.</span></span> <span data-ttu-id="27d36-115">읽기 전용으로 표시한 후에 한 번만 파일 그룹을 백업하도록 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="27d36-115">You can choose to back up the filegroup only once after marking it read-only.</span></span>  
  
-   <span data-ttu-id="27d36-116">증분 복원</span><span class="sxs-lookup"><span data-stu-id="27d36-116">Piecemeal restore.</span></span>  
  
    -   <span data-ttu-id="27d36-117">증분 복원의 목표는 모든 데이터를 기다리지 않고 데이터베이스의 중요한 부분을 온라인 상태로 만드는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="27d36-117">The goal of a piecemeal restore is to bring the critical parts of database online without waiting for all the data.</span></span> <span data-ttu-id="27d36-118">한 가지 예는 데이터베이스에 분할된 데이터가 있고 이전 파티션이 드물게만 사용되는 경우입니다.</span><span class="sxs-lookup"><span data-stu-id="27d36-118">One example is if a database has partitioned data, such that older partitions are only used rarely.</span></span> <span data-ttu-id="27d36-119">필요한 경우에만 이전 파티션을 복원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="27d36-119">You can restore them only on an as-needed basis.</span></span> <span data-ttu-id="27d36-120">기록 데이터 등을 포함하는 파일 그룹의 경우에도 이와 유사합니다.</span><span class="sxs-lookup"><span data-stu-id="27d36-120">Similar for filegroups that contain, for example, historical data.</span></span>  
  
    -   <span data-ttu-id="27d36-121">페이지 복구를 사용하면 페이지를 특정하게 복원하여 페이지 손상을 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="27d36-121">Using page repair, you can fix page corruption by specifically restoring the page.</span></span> <span data-ttu-id="27d36-122">자세한 내용은 [페이지 복원&#40;SQL Server&#41;](../backup-restore/restore-pages-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="27d36-122">For more information, see [Restore Pages &#40;SQL Server&#41;](../backup-restore/restore-pages-sql-server.md).</span></span>  
  
## <a name="samples"></a><span data-ttu-id="27d36-123">샘플</span><span class="sxs-lookup"><span data-stu-id="27d36-123">Samples</span></span>  
 <span data-ttu-id="27d36-124">다음 예에서는 아래의 스키마를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="27d36-124">The examples use the following schema:</span></span>  
  
```  
CREATE DATABASE imoltp  
ON PRIMARY (name = imoltp_primary1, filename = 'c:\data\imoltp_data1.mdf')  
LOG ON (name = imoltp_log, filename = 'c:\data\imoltp_log.ldf')  
GO  
  
ALTER DATABASE imoltp ADD FILE (name = imoltp_primary2, filename = 'c:\data\imoltp_data2.ndf')  
GO  
  
ALTER DATABASE imoltp ADD FILEGROUP imoltp_secondary  
ALTER DATABASE imoltp ADD FILE (name = imoltp_secondary, filename = 'c:\data\imoltp_secondary.ndf') TO FILEGROUP imoltp_secondary  
GO  
  
ALTER DATABASE imoltp ADD FILEGROUP imoltp_mod CONTAINS MEMORY_OPTIMIZED_DATA   
ALTER DATABASE imoltp ADD FILE (name='imoltp_mod1', filename='c:\data\imoltp_mod1') TO FILEGROUP imoltp_mod   
ALTER DATABASE imoltp ADD FILE (name='imoltp_mod2', filename='c:\data\imoltp_mod2') TO FILEGROUP imoltp_mod   
GO  
```  
  
### <a name="backup"></a><span data-ttu-id="27d36-125">Backup</span><span class="sxs-lookup"><span data-stu-id="27d36-125">Backup</span></span>  
 <span data-ttu-id="27d36-126">이 예제에서는 주 파일 그룹과 메모리 최적화 파일 그룹을 백업하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="27d36-126">This sample shows how to backup the primary filegroup and the memory-optimized filegroup.</span></span> <span data-ttu-id="27d36-127">주 파일 그룹과 메모리 최적화 파일 그룹을 함께 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="27d36-127">You must specify both primary and memory-optimized filegroup together.</span></span>  
  
```  
backup database imoltp filegroup='primary', filegroup='imoltp_mod' to disk='c:\data\imoltp.dmp' with init  
```  
  
 <span data-ttu-id="27d36-128">다음 예제에서는 주 파일 그룹과 메모리 최적화 파일 그룹을 제외한 파일 그룹의 백업이 메모리 최적화 테이블이 없는 데이터베이스와 유사하게 수행되는 것을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="27d36-128">The following sample shows that a back up of filegroup(s) other than primary and memory-optimized filegroup works similar to the databases without memory-optimized tables.</span></span> <span data-ttu-id="27d36-129">다음 명령은 보조 파일 그룹을 백업합니다.</span><span class="sxs-lookup"><span data-stu-id="27d36-129">The following command backups up the secondary filegroup</span></span>  
  
```  
backup database imoltp filegroup='imoltp_secondary' to disk='c:\data\imoltp_secondary.dmp' with init  
```  
  
### <a name="restore"></a><span data-ttu-id="27d36-130">복원</span><span class="sxs-lookup"><span data-stu-id="27d36-130">Restore</span></span>  
 <span data-ttu-id="27d36-131">다음 예제에서는 주 파일 그룹과 메모리 최적화 파일 그룹을 함께 복원하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="27d36-131">The following sample shows how to restore the primary filegroup and memory-optimized filegroup together.</span></span>  
  
```  
restore database imoltp filegroup = 'primary', filegroup = 'imoltp_mod'   
from disk='c:\data\imoltp.dmp' with partial, norecovery  
  
--restore the transaction log  
 RESTORE LOG [imoltp] FROM DISK = N'c:\data\imoltp_log.dmp' WITH  FILE = 1,  NOUNLOAD,  STATS = 10  
GO  
```  
  
 <span data-ttu-id="27d36-132">다음 예제에서는 주 파일 그룹과 메모리 최적화 파일 그룹을 제외한 파일 그룹의 복원이 메모리 최적화 테이블이 없는 데이터베이스와 유사하게 수행되는 것을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="27d36-132">The next sample shows that restoring filegroup(s) other than the primary and memory-optimized filegroup works similar to the databases without memory-optimized tables</span></span>  
  
```  
RESTORE DATABASE [imoltp] FILE = N'imoltp_secondary'   
FROM  DISK = N'c:\data\imoltp_secondary.dmp' WITH  FILE = 1,  RECOVERY,  NOUNLOAD,  STATS = 10  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="27d36-133">참고 항목</span><span class="sxs-lookup"><span data-stu-id="27d36-133">See Also</span></span>  
 [<span data-ttu-id="27d36-134">메모리 액세스에 최적화된 테이블의 백업, 복원 및 복구</span><span class="sxs-lookup"><span data-stu-id="27d36-134">Backup, Restore, and Recovery of Memory-Optimized Tables</span></span>](../../database-engine/backup-restore-and-recovery-of-memory-optimized-tables.md)  
  
  
