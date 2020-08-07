---
title: 증분 복원(SQL Server) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- partial updates [SQL Server]
- staged restores [SQL Server]
- piecemeal restores [SQL Server]
- restoring [SQL Server], piecemeal restore scenario
ms.assetid: 208f55e0-0762-4cfb-85c4-d36a76ea0f5b
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: ebc4ea11780908f847946a01338571211b57678a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731751"
---
# <a name="piecemeal-restores-sql-server"></a><span data-ttu-id="de8a1-102">증분 복원(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="de8a1-102">Piecemeal Restores (SQL Server)</span></span>
  <span data-ttu-id="de8a1-103">이 항목에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 엔터프라이즈 버전의 데이터베이스에 여러 개의 파일 또는 파일 그룹이 있는 경우, 그리고 단순 모델에서 파일 그룹이 읽기 전용인 경우에 대해서만 다룹니다.</span><span class="sxs-lookup"><span data-stu-id="de8a1-103">This topic is relevant only for databases in the Enterprise edition of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that contain multiple files or filegroups; and, under the simple model, only for read-only filegroups.</span></span>  
  
 <span data-ttu-id="de8a1-104">증분 복원과 메모리 최적화 테이블에 대한 자세한 내용은 [메모리 최적화 테이블이 있는 데이터베이스의 증분 복원](../in-memory-oltp/memory-optimized-tables.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="de8a1-104">For information about piecemeal restore and memory-optimized tables, see [Piecemeal Restore of Databases With Memory-Optimized Tables](../in-memory-oltp/memory-optimized-tables.md).</span></span>  
  
 <span data-ttu-id="de8a1-105">*증분 복원* 을 사용하면 여러 파일 그룹을 포함하는 데이터베이스를 단계별로 복원 및 복구할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="de8a1-105">*Piecemeal restore* allows databases that contain multiple filegroups to be restored and recovered in stages.</span></span> <span data-ttu-id="de8a1-106">증분 복원에는 주 파일 그룹에서 시작하여 경우에 따라 하나 이상의 보조 파일 그룹까지 단계별로 복원하는 일련의 복원 순서가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="de8a1-106">Piecemeal restore involves a series of restore sequences, starting with the primary filegroup and, in some cases, one or more secondary filegroups.</span></span> <span data-ttu-id="de8a1-107">증분 복원에서는 데이터베이스가 최종적으로 일관성 있는 상태가 되도록 검사를 유지 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="de8a1-107">Piecemeal restore maintains checks to ensure that the database will be consistent in the end.</span></span> <span data-ttu-id="de8a1-108">복원 순서가 완료되었을 때 복구된 파일이 유효하고 데이터베이스와 일치하는 경우 이 파일을 즉시 온라인 상태로 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="de8a1-108">After the restore sequence is completed, recovered files, if they are valid and consistent with the database, can be brought online directly.</span></span>  
  
 <span data-ttu-id="de8a1-109">증분 복원 작업은 모든 복구 모델에서 가능하지만 단순 모델보다는 전체 및 대량 로그 모델에 대해 더 융통성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="de8a1-109">Piecemeal restore works with all recovery models, but is more flexible for the full and bulk-logged models than for the simple model.</span></span>  
  
 <span data-ttu-id="de8a1-110">모든 증분 복원은 *부분 복원 순서*라는 초기 복원 순서로 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="de8a1-110">Every piecemeal restore starts with an initial restore sequence called the *partial-restore sequence*.</span></span> <span data-ttu-id="de8a1-111">최소한 부분 복원 순서에서는 주 파일 그룹을 복원 및 복구하고 단순 복구 모델을 사용할 경우 모든 읽기/쓰기 파일 그룹을 복원 및 복구합니다.</span><span class="sxs-lookup"><span data-stu-id="de8a1-111">Minimally, the partial-restore sequence restores and recovers the primary filegroup and, under the simple recovery model, all read/write filegroups.</span></span> <span data-ttu-id="de8a1-112">증분 복원 순서 중에 전체 데이터베이스는 오프라인 상태가 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="de8a1-112">During the piecemeal-restore sequence, the whole database must go offline.</span></span> <span data-ttu-id="de8a1-113">그 후에 데이터베이스가 온라인 상태가 되고 복원된 파일 그룹을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="de8a1-113">Thereafter, the database is online and restored filegroups are available.</span></span> <span data-ttu-id="de8a1-114">그러나 복원되지 않은 파일 그룹은 오프라인으로 유지되고 액세스할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="de8a1-114">However, any unrestored filegroups remain offline and are not accessible.</span></span> <span data-ttu-id="de8a1-115">나중에 파일 복원을 수행하여 오프라인 파일 그룹을 복원하고 온라인 상태로 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="de8a1-115">Any offline filegroups, however, can be restored and brought online later by a file restore.</span></span>  
  
 <span data-ttu-id="de8a1-116">데이터베이스에서 사용하는 복구 모델에 관계없이 부분 복원 순서는 전체 백업을 복원하고 PARTIAL 옵션을 지정하는 RESTORE DATABASE 문으로 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="de8a1-116">Regardless of the recovery model that is used by the database, the partial-restore sequence starts with a RESTORE DATABASE statement that restores a full backup and specifies the PARTIAL option.</span></span> <span data-ttu-id="de8a1-117">PARTIAL 옵션은 항상 새로운 증분 복원을 시작하므로 부분 복원 순서의 맨 처음 문에서 한 번만 PARTIAL 옵션을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="de8a1-117">The PARTIAL option always starts a new piecemeal restore; therefore, you must specify PARTIAL only one time in the initial statement of the partial-restore sequence.</span></span> <span data-ttu-id="de8a1-118">부분 복원 순서가 완료되고 데이터베이스가 온라인 상태가 되면 파일의 복구가 연기되므로 나머지 파일은 "복구 보류" 상태가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="de8a1-118">When the partial restore sequence finishes and the database is brought online, the state of the remaining files becomes "recovery pending" because their recovery has been postponed.</span></span>  
  
 <span data-ttu-id="de8a1-119">그 후 증분 복원은 일반적으로 하나 이상의 복원 순서를 포함하게 되며 이를 *파일 그룹 복원 순서*라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="de8a1-119">Subsequently, a piecemeal restore typically includes one or more restore sequences, which are called *filegroup-restore sequences*.</span></span> <span data-ttu-id="de8a1-120">특정 파일 그룹 복원 순서의 경우 원하는 기간 동안 수행을 대기할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="de8a1-120">You can wait to perform a specific filegroup-restore sequence for as long as you want.</span></span> <span data-ttu-id="de8a1-121">각 파일 그룹 복원 순서는 하나 이상의 오프라인 파일 그룹을 데이터베이스와 일치하는 지점으로 복원 및 복구합니다.</span><span class="sxs-lookup"><span data-stu-id="de8a1-121">Each filegroup-restore sequence restores and recovers one or more offline filegroups to a point consistent with the database.</span></span> <span data-ttu-id="de8a1-122">파일 그룹 복원 순서의 타이밍과 개수는 복구 목표, 복원할 오프라인 파일 그룹 수 및 파일 그룹 복원 순서당 복원할 오프라인 파일 그룹 수에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="de8a1-122">The timing and number of filegroup-restore sequences depends on your recovery goal, the number of offline filegroups you want to restore, and on how many of them you restore per filegroup-restore sequence.</span></span>  
  
 <span data-ttu-id="de8a1-123">증분 복원을 수행하기 위한 정확한 요구 사항은 데이터베이스의 복구 모델에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="de8a1-123">The exact requirements for performing a piecemeal restore depend on the recovery model of the database.</span></span> <span data-ttu-id="de8a1-124">자세한 내용은 이 항목의 뒷부분에 나오는 "단순 복구 모델에서의 증분 복원" 및 "전체 복구 모델에서의 증분 복원"을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="de8a1-124">For more information, see "Piecemeal Restore Under the Simple Recovery Model" and "Piecemeal Restore Under the Full Recovery Model," later in this topic.</span></span>  
  
## <a name="piecemeal-restore-scenarios"></a><span data-ttu-id="de8a1-125">증분 복원 시나리오</span><span class="sxs-lookup"><span data-stu-id="de8a1-125">Piecemeal Restore Scenarios</span></span>  
 <span data-ttu-id="de8a1-126">모든 버전의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 는 오프라인 증분 복원을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="de8a1-126">All editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] support offline piecemeal restores.</span></span> <span data-ttu-id="de8a1-127">엔터프라이즈 버전에서는 온라인 또는 오프라인 상태에서 증분 복원을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="de8a1-127">In the Enterprise edition, a piecemeal restore can be either online or offline.</span></span> <span data-ttu-id="de8a1-128">오프라인 및 온라인 증분 복원의 의미는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="de8a1-128">The implications of offline and online piecemeal restores are as follows:</span></span>  
  
-   <span data-ttu-id="de8a1-129">오프라인 증분 복원 시나리오</span><span class="sxs-lookup"><span data-stu-id="de8a1-129">Offline piecemeal restore scenario</span></span>  
  
     <span data-ttu-id="de8a1-130">오프라인 증분 복원 시 데이터베이스는 부분 복원 순서 후에 온라인 상태가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="de8a1-130">In an offline piecemeal restore, the database is online after the partial-restore sequence.</span></span> <span data-ttu-id="de8a1-131">복원되지 않은 파일 그룹은 오프라인 상태로 남지만 필요한 경우 데이터베이스를 오프라인 상태로 만든 후 해당 파일 그룹을 복원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="de8a1-131">Filegroups that have not yet been restored remain offline, but they can be restored as you need them after taking the database offline.</span></span>  
  
-   <span data-ttu-id="de8a1-132">온라인 증분 복원 시나리오</span><span class="sxs-lookup"><span data-stu-id="de8a1-132">Online piecemeal restore scenario</span></span>  
  
     <span data-ttu-id="de8a1-133">온라인 증분 복원 시에는 부분 복원 순서 후 데이터베이스가 온라인 상태가 되고 주 파일 그룹과 복구된 모든 보조 파일 그룹을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="de8a1-133">In an online piecemeal restore, after the partial-restore sequence, the database is online, and the primary filegroup and any recovered secondary filegroups are available.</span></span> <span data-ttu-id="de8a1-134">복원되지 않은 파일 그룹은 오프라인 상태로 남지만 필요한 경우 데이터베이스를 온라인으로 유지한 상태에서 해당 파일을 복원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="de8a1-134">Filegroups that have not yet been restored remain offline, but they can be restored as needed while the database remains online.</span></span>  
  
     <span data-ttu-id="de8a1-135">온라인 증분 복원에는 지연된 트랜잭션이 사용될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="de8a1-135">Online piecemeal restores can involve deferred transactions.</span></span> <span data-ttu-id="de8a1-136">파일 그룹의 하위 집합만 복원된 경우 온라인 파일 그룹에 종속된 데이터베이스의 트랜잭션이 지연될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="de8a1-136">When only a subset of filegroups has been restored, transactions in the database that depend on online filegroups might become deferred.</span></span> <span data-ttu-id="de8a1-137">이것은 전체 데이터베이스가 일치해야 하므로 정상적인 현상입니다.</span><span class="sxs-lookup"><span data-stu-id="de8a1-137">This is typical, because the whole database must be consistent.</span></span> <span data-ttu-id="de8a1-138">자세한 내용은 [지연된 트랜잭션&#40;SQL Server&#41;](deferred-transactions-sql-server.md)에서 존재하지 않는 파일 그룹을 제거하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="de8a1-138">For more information, see [Deferred Transactions &#40;SQL Server&#41;](deferred-transactions-sql-server.md).</span></span>  
  
-   [!INCLUDE[hek_1](../../includes/hek-1-md.md)] <span data-ttu-id="de8a1-139">증분 복원 시나리오</span><span class="sxs-lookup"><span data-stu-id="de8a1-139">piecemeal restore scenario</span></span>  
  
     <span data-ttu-id="de8a1-140">메모리 내 OLTP 데이터베이스의 증분 복원에 대한 자세한 내용은 [메모리 액세스에 최적화된 테이블이 포함된 데이터베이스의 증분 백업 및 복원](../in-memory-oltp/memory-optimized-tables.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="de8a1-140">For information on Piecemeal Restores of In-Memory OLTP databases see [Piecemeal Backup and Restore of Databases With Memory-Optimized Tables](../in-memory-oltp/memory-optimized-tables.md).</span></span>  
  
## <a name="restrictions"></a><span data-ttu-id="de8a1-141">제한</span><span class="sxs-lookup"><span data-stu-id="de8a1-141">Restrictions</span></span>  
 <span data-ttu-id="de8a1-142">부분 복원 순서에서 [FILESTREAM](../blob/filestream-sql-server.md) 파일 그룹이 제외될 경우 지정 시간 복원은 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="de8a1-142">If a partial restore sequence excludes any [FILESTREAM](../blob/filestream-sql-server.md) filegroup, point-in-time restore is not supported.</span></span> <span data-ttu-id="de8a1-143">복원 순서를 강제로 계속할 수 있지만</span><span class="sxs-lookup"><span data-stu-id="de8a1-143">You can force the restore sequence to continue.</span></span> <span data-ttu-id="de8a1-144">RESTORE 문에서 누락된 FILESTREAM 파일 그룹은 복원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="de8a1-144">However the FILESTREAM filegroups that are omitted from your RESTORE statement can never be restored.</span></span> <span data-ttu-id="de8a1-145">지정 시간 복원을 강제로 수행하려면 후속 RESTORE LOG 문에도 지정해야 하는 STOPAT, STOPATMARK 또는 STOPBEFOREMARK 옵션과 함께 CONTINUE_AFTER_ERROR 옵션을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="de8a1-145">To force a point-in-time restore, specify the CONTINUE_AFTER_ERROR option together with the STOPAT, STOPATMARK, or STOPBEFOREMARK option, which you must also specify in your subsequent RESTORE LOG statements.</span></span> <span data-ttu-id="de8a1-146">CONTINUE_AFTER_ERROR를 지정하면 부분 복원 순서가 성공하고 FILESTREAM 파일 그룹이 복구 불가능한 상태가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="de8a1-146">If you specify CONTINUE_AFTER_ERROR, the partial restore sequence succeeds and the FILESTREAM filegroup becomes unrecoverable.</span></span>  
  
## <a name="piecemeal-restore-under-the-simple-recovery-model"></a><span data-ttu-id="de8a1-147">단순 복구 모델에서의 증분 복원</span><span class="sxs-lookup"><span data-stu-id="de8a1-147">Piecemeal Restore Under the Simple Recovery Model</span></span>  
 <span data-ttu-id="de8a1-148">단순 복구 모델에서 증분 복원 순서는 전체 데이터베이스 백업 또는 부분 백업으로 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="de8a1-148">Under the simple recovery model, the piecemeal restore sequence must start with a full database or partial backup.</span></span> <span data-ttu-id="de8a1-149">그런 다음 복원된 백업이 차등 기반일 경우 최근의 차등 백업을 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="de8a1-149">Then, if the restored backup is a differential base, restore the latest differential backup next.</span></span>  
  
 <span data-ttu-id="de8a1-150">첫 번째 부분 복원 순서 중에 읽기/쓰기 파일 그룹의 하위 집합만 복원할 경우 복원되지 않은 파일 그룹은 부분 복원된 데이터베이스를 복구할 때 존재하지 않는 상태가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="de8a1-150">During the first partial restore sequence, if you restore only a subset of read/write filegroups, any unrestored filegroups become defunct when you recover the partially restored database.</span></span> <span data-ttu-id="de8a1-151">다음과 같은 경우에만 부분 복원 순서에서 읽기/쓰기 파일 그룹을 제외할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="de8a1-151">Omitting a read/write filegroup from the partial-restore sequence is appropriate only in the following cases:</span></span>  
  
-   <span data-ttu-id="de8a1-152">복원되지 않은 파일 그룹을 존재하지 않는 상태로 만들려는 경우</span><span class="sxs-lookup"><span data-stu-id="de8a1-152">You intend for the unrestored filegroups to become defunct.</span></span>  
  
-   <span data-ttu-id="de8a1-153">부분 복원 순서의 이전 복원 중에 복원되지 않은 각 파일 그룹이 읽기 전용, 삭제 또는 존재하지 않게 된 복구 지점에 복원 순서가 도달하는 경우</span><span class="sxs-lookup"><span data-stu-id="de8a1-153">The restore sequence will arrive at a recovery point at which each unrestored filegroup has become read-only, dropped, or defunct (during a previous restore in the partial-restore sequence).</span></span>  
  
-   <span data-ttu-id="de8a1-154">데이터베이스가 단순 복구 모델을 사용하는 동안 전체 백업이 수행되었으나 복구 지점은 데이터베이스가 전체 복구 모델을 사용 중인 시점에 있는 경우.</span><span class="sxs-lookup"><span data-stu-id="de8a1-154">The full backup was taken while the database was using the simple recovery model, but the recovery point is at a time when the database is using the full recovery model.</span></span> <span data-ttu-id="de8a1-155">자세한 내용은 이 항목의 뒷부분에 있는 "단순 복구 모델에서 전체 복구 모델로 전환된 데이터베이스의 증분 복원 수행"을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="de8a1-155">For more information, see "Performing a Piecemeal Restore of a Database Whose Recovery Model Has Been Switched from Simple to Full," later in this topic.</span></span>  
  
### <a name="requirements-for-piecemeal-restore-under-the-simple-recovery-model"></a><span data-ttu-id="de8a1-156">단순 복구 모델에서의 증분 복원에 대한 요구 사항</span><span class="sxs-lookup"><span data-stu-id="de8a1-156">Requirements for Piecemeal Restore Under the Simple Recovery Model</span></span>  
 <span data-ttu-id="de8a1-157">단순 복구 모델에서 초기 단계는 주 파일 그룹과 모든 읽기/쓰기 보조 파일 그룹을 복원 및 복구합니다.</span><span class="sxs-lookup"><span data-stu-id="de8a1-157">Under the simple recovery model, the initial stage restores and recovers the primary filegroup and all read/write secondary filegroups.</span></span> <span data-ttu-id="de8a1-158">초기 단계가 완료되었을 때 복구된 파일이 유효하고 데이터베이스와 일치하는 경우 이 파일을 온라인 상태로 직접 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="de8a1-158">After the initial stage is completed, recovered files, if they are valid and consistent with the database, can be brought online directly.</span></span>  
  
 <span data-ttu-id="de8a1-159">그 후에 하나 이상의 추가 단계로 읽기 전용 파일 그룹을 복원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="de8a1-159">Thereafter, read-only filegroups can be restored in one or more additional stages.</span></span>  
  
 <span data-ttu-id="de8a1-160">증분 복원은 다음 조건을 만족하는 경우 읽기 전용 보조 파일 그룹에 대해 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="de8a1-160">Piecemeal restore is available for a read-only secondary filegroup only if the following are true:</span></span>  
  
-   <span data-ttu-id="de8a1-161">백업 시 읽기 전용이었던 파일 그룹</span><span class="sxs-lookup"><span data-stu-id="de8a1-161">Was read-only when backed up.</span></span>  
  
-   <span data-ttu-id="de8a1-162">읽기 전용으로 남아 있는 파일 그룹(논리적으로 주 파일 그룹과 일관성 유지)</span><span class="sxs-lookup"><span data-stu-id="de8a1-162">Has remained read-only (keeping it logically consistent with the primary filegroup).</span></span>  
  
 <span data-ttu-id="de8a1-163">증분 복원을 수행하려면 다음 지침을 따라야 합니다.</span><span class="sxs-lookup"><span data-stu-id="de8a1-163">To perform a piecemeal restore, the following guidelines must be followed:</span></span>  
  
-   <span data-ttu-id="de8a1-164">단순 복구 모델 데이터베이스의 증분 복원을 위한 전체 백업 세트에 다음이 포함되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="de8a1-164">A complete set of backups for the piecemeal restore of a simple recovery model database must contain the following:</span></span>  
  
    -   <span data-ttu-id="de8a1-165">주 파일 그룹과 백업 당시 읽기/쓰기 상태였던 모든 파일 그룹을 포함하는 부분 또는 전체 데이터베이스 백업</span><span class="sxs-lookup"><span data-stu-id="de8a1-165">A partial or full database backup that contains the primary filegroup and all filegroups that were read/write at the time of the backup.</span></span>  
  
    -   <span data-ttu-id="de8a1-166">각 읽기 전용 파일의 백업</span><span class="sxs-lookup"><span data-stu-id="de8a1-166">A backup of each read-only file.</span></span>  
  
-   <span data-ttu-id="de8a1-167">읽기 전용 파일의 백업이 주 파일 그룹의 백업과 일치하려면 보조 파일 그룹은 백업된 당시부터 주 파일 그룹을 포함하는 백업이 완료될 때까지 읽기 전용 상태여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="de8a1-167">For the backup of a read-only file to be consistent with the primary filegroup, the secondary filegroup must have been read-only from when it was backed up until the backup that contains the primary filegroup was completed.</span></span> <span data-ttu-id="de8a1-168">파일 그룹이 읽기 전용 상태가 된 후 차등 파일 백업을 가져온 경우 차등 파일 백업을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="de8a1-168">You can use differential file backups, if they were taken after the filegroup became read-only.</span></span>  
  
### <a name="piecemeal-restore-stages-simple-recovery-model"></a><span data-ttu-id="de8a1-169">증분 복원 단계(단순 복구 모델)</span><span class="sxs-lookup"><span data-stu-id="de8a1-169">Piecemeal Restore Stages (Simple Recovery Model)</span></span>  
 <span data-ttu-id="de8a1-170">증분 복원 시나리오에는 다음 단계가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="de8a1-170">The piecemeal restore scenario involves the following stages:</span></span>  
  
-   <span data-ttu-id="de8a1-171">초기 단계(주 파일 그룹과 모든 읽기/쓰기 파일 그룹 복원 및 복구)</span><span class="sxs-lookup"><span data-stu-id="de8a1-171">Initial stage (restore and recover the primary filegroup and all read/write filegroups)</span></span>  
  
     <span data-ttu-id="de8a1-172">초기 상태에서는 부분 복원을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="de8a1-172">The initial stage performs a partial restore.</span></span> <span data-ttu-id="de8a1-173">부분 복원 순서에서는 주 파일 그룹과 모든 읽기/쓰기 보조 파일 그룹을 복원하고 선택적으로 읽기 전용 파일 그룹의 일부를 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="de8a1-173">The partial restore sequence restores the primary filegroup, all read/write secondary filegroups, and (optionally) some of the read-only filegroups.</span></span> <span data-ttu-id="de8a1-174">초기 단계에서 전체 데이터베이스는 오프라인 상태가 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="de8a1-174">During the initial stage, the whole database must go offline.</span></span> <span data-ttu-id="de8a1-175">초기 단계 후에 데이터베이스가 온라인 상태가 되고 복원된 파일 그룹을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="de8a1-175">After the initial stage, the database is online, and restored filegroups are available.</span></span> <span data-ttu-id="de8a1-176">하지만 복원되지 않은 모든 읽기 전용 파일 그룹은 오프라인 상태를 유지합니다.</span><span class="sxs-lookup"><span data-stu-id="de8a1-176">However, any read-only filegroups that have not yet been restored, remain offline.</span></span>  
  
     <span data-ttu-id="de8a1-177">초기 단계에서 첫 번째 RESTORE 문은 다음을 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="de8a1-177">The first RESTORE statement in the initial stage must do the following:</span></span>  
  
    -   <span data-ttu-id="de8a1-178">주 파일 그룹과 백업 당시 읽기/쓰기 상태였던 모든 파일 그룹을 포함하는 부분 또는 전체 데이터베이스 백업을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="de8a1-178">Use a partial or full database backup that contains the primary filegroup and all filegroups that were read/write at the time of the backup.</span></span> <span data-ttu-id="de8a1-179">일반적으로 부분 복원 순서는 부분 백업을 복원하여 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="de8a1-179">It is common to start a partial restore sequence by restoring a partial backup.</span></span>  
  
    -   <span data-ttu-id="de8a1-180">증분 복원의 시작을 나타내는 PARTIAL 옵션을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="de8a1-180">Specify the PARTIAL option, which indicates the start of a piecemeal restore.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="de8a1-181">PARTIAL 옵션은 보안 검사를 수행하므로 결과 데이터베이스를 프로덕션 데이터베이스로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="de8a1-181">The PARTIAL option performs safety checks that ensure that the resulting database is suited for use as a production database.</span></span>  
  
    -   <span data-ttu-id="de8a1-182">백업이 전체 데이터베이스 백업인 경우 READ_WRITE_FILEGROUPS 옵션을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="de8a1-182">Specify the READ_WRITE_FILEGROUPS option if the backup is a full database backup.</span></span>  
  
-   <span data-ttu-id="de8a1-183">데이터베이스가 온라인 상태이면 하나 이상의 온라인 파일 복원을 사용하여 백업 당시 읽기 전용이었던 오프라인 읽기 전용 파일을 복원 및 복구할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="de8a1-183">While the database is online, you can use one or more online file restores to restore and recover offline read-only files that were read-only at the time of backup.</span></span> <span data-ttu-id="de8a1-184">온라인 파일 복원의 타이밍은 데이터가 온라인 상태가 되어야 하는 시기에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="de8a1-184">The timing of the online file restores depends on when you want to have the data online.</span></span>  
  
     <span data-ttu-id="de8a1-185">데이터를 파일로 복원해야 하는지 여부는 다음에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="de8a1-185">Whether you must restore data to a file depends on the following:</span></span>  
  
    -   <span data-ttu-id="de8a1-186">데이터베이스와 일치하는 유효한 읽기 전용 파일은 데이터를 복원하지 않고 복구하여 즉시 온라인 상태로 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="de8a1-186">Valid read-only files that are consistent with the database can be brought online directly by recovering them without restoring any data.</span></span>  
  
    -   <span data-ttu-id="de8a1-187">손상되거나 데이터베이스와 일치하지 않는 파일은 복구하기 전에 복원해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="de8a1-187">Files that are damaged or inconsistent with the database must be restored before they are recovered.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="de8a1-188">예</span><span class="sxs-lookup"><span data-stu-id="de8a1-188">Examples</span></span>  
  
-   [<span data-ttu-id="de8a1-189">예: 데이터베이스의 증분 복원&#40;단순 복구 모델&#41;</span><span class="sxs-lookup"><span data-stu-id="de8a1-189">Example: Piecemeal Restore of Database &#40;Simple Recovery Model&#41;</span></span>](example-piecemeal-restore-of-database-simple-recovery-model.md)  
  
-   [<span data-ttu-id="de8a1-190">예: 일부 파일 그룹만 증분 복원&#40;단순 복구 모델&#41;</span><span class="sxs-lookup"><span data-stu-id="de8a1-190">Example: Piecemeal Restore of Only Some Filegroups &#40;Simple Recovery Model&#41;</span></span>](example-piecemeal-restore-of-only-some-filegroups-simple-recovery-model.md)  
  
## <a name="piecemeal-restore-under-the-full-recovery-model"></a><span data-ttu-id="de8a1-191">전체 복구 모델에서의 증분 복원</span><span class="sxs-lookup"><span data-stu-id="de8a1-191">Piecemeal Restore Under the Full Recovery Model</span></span>  
 <span data-ttu-id="de8a1-192">전체 복구 모델 또는 대량 로그 복구 모델에서는 여러 파일 그룹이 있는 모든 데이터베이스에 대해 증분 복원을 사용하여 해당 데이터베이스를 임의의 시점으로 복원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="de8a1-192">Under the full recovery model or bulk-logged recovery model, piecemeal restore is available for any database that contains multiple filegroups and you can restore a database to any point in time.</span></span> <span data-ttu-id="de8a1-193">증분 복원의 복원 순서는 다음과 같이 동작합니다.</span><span class="sxs-lookup"><span data-stu-id="de8a1-193">The restore sequences of a piecemeal restore behave as follows:</span></span>  
  
-   <span data-ttu-id="de8a1-194">부분 복원 순서</span><span class="sxs-lookup"><span data-stu-id="de8a1-194">Partial-restore sequence</span></span>  
  
     <span data-ttu-id="de8a1-195">부분 복원 순서에서는 주 파일 그룹과 필요할 경우 보조 파일 그룹을 일부 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="de8a1-195">The partial restore sequence restores the primary filegroup and, optionally, some of the secondary filegroups.</span></span>  
  
     <span data-ttu-id="de8a1-196">첫 번째 RESTORE DATABASE 문은 다음을 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="de8a1-196">The first RESTORE DATABASE statement must do the following:</span></span>  
  
    -   <span data-ttu-id="de8a1-197">PARTIAL 옵션을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="de8a1-197">Specify the PARTIAL option.</span></span> <span data-ttu-id="de8a1-198">이는 증분 복원의 시작을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="de8a1-198">This indicates the start of a piecemeal restore.</span></span>  
  
    -   <span data-ttu-id="de8a1-199">주 파일 그룹을 포함하는 전체 데이터베이스 백업을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="de8a1-199">Use any full database backup that contains the primary filegroup.</span></span> <span data-ttu-id="de8a1-200">일반적으로 부분 복원 순서는 부분 백업을 복원하여 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="de8a1-200">The common practice is to start a partial restore sequence by restoring a partial backup.</span></span>  
  
    -   <span data-ttu-id="de8a1-201">특정 시점으로 복원하려면 부분 복원 순서에서 시간을 지정해야 하며</span><span class="sxs-lookup"><span data-stu-id="de8a1-201">To restore to a specific point in time, you must specify the time in the partial restore sequence.</span></span> <span data-ttu-id="de8a1-202">복원 순서의 모든 연속 단계에서 동일한 시간을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="de8a1-202">Every successive step of the restore sequence must specify the same point in time.</span></span>  
  
-   <span data-ttu-id="de8a1-203">파일 그룹 복원 순서는 추가 파일 그룹을 데이터베이스와 일치하는 온라인 시점으로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="de8a1-203">Filegroup-restore sequences bring additional filegroups online to a point consistent with the database.</span></span>  
  
     <span data-ttu-id="de8a1-204">엔터프라이즈 버전에서 데이터베이스가 온라인 상태인 동안에는 오프라인 보조 파일 그룹을 복원 및 복구할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="de8a1-204">In the Enterprise edition, any offline secondary filegroup can be restored and recovered while the database remains online.</span></span> <span data-ttu-id="de8a1-205">특정 읽기 전용 파일이 손상되지 않았고 데이터베이스와 일치하면 해당 파일을 복원할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="de8a1-205">If a specific read-only file is undamaged and consistent with the database, the file does not have to be restored.</span></span> <span data-ttu-id="de8a1-206">자세한 내용은 [데이터를 복원하지 않고 데이터베이스 복구&#40;Transact-SQL&#41;](recover-a-database-without-restoring-data-transact-sql.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="de8a1-206">For more information, see [Recover a Database Without Restoring Data &#40;Transact-SQL&#41;](recover-a-database-without-restoring-data-transact-sql.md).</span></span>  
  
### <a name="applying-log-backups"></a><span data-ttu-id="de8a1-207">로그 백업 적용</span><span class="sxs-lookup"><span data-stu-id="de8a1-207">Applying Log Backups</span></span>  
 <span data-ttu-id="de8a1-208">파일 백업이 생성되기 이전부터 읽기 전용 파일 그룹이 읽기 전용이었으면 로그 백업을 파일 그룹에 적용할 필요가 없으며 파일 복원 시 이 작업은 생략됩니다.</span><span class="sxs-lookup"><span data-stu-id="de8a1-208">If a read-only filegroup has been read-only since before the file backup was created, applying log backups to the filegroup is unnecessary and is skipped by file restore.</span></span> <span data-ttu-id="de8a1-209">읽기/쓰기가 가능한 파일 그룹의 경우 파일 그룹을 현재 로그 파일로 전달하려면 손상되지 않은 로그 백업 체인을 마지막 전체 복원 또는 차등 복원에 적용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="de8a1-209">If the filegroup is read/write, an unbroken chain of log backups must be applied to the last full or differential restore to bring the filegroup forward to the current log file.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="de8a1-210">예</span><span class="sxs-lookup"><span data-stu-id="de8a1-210">Examples</span></span>  
  
-   [<span data-ttu-id="de8a1-211">예: 데이터베이스의 증분 복원&#40;전체 복구 모델&#41;</span><span class="sxs-lookup"><span data-stu-id="de8a1-211">Example: Piecemeal Restore of Database &#40;Full Recovery Model&#41;</span></span>](example-piecemeal-restore-of-database-full-recovery-model.md)  
  
-   [<span data-ttu-id="de8a1-212">예: 일부 파일 그룹만 증분 복원&#40;전체 복구 모델&#41;</span><span class="sxs-lookup"><span data-stu-id="de8a1-212">Example: Piecemeal Restore of Only Some Filegroups &#40;Full Recovery Model&#41;</span></span>](example-piecemeal-restore-of-only-some-filegroups-full-recovery-model.md)  
  
## <a name="performing-a-piecemeal-restore-of-a-database-whose-recovery-model-has-been-switched-from-simple-to-full"></a><span data-ttu-id="de8a1-213">단순 복구 모델에서 전체 복구 모델로 전환된 데이터베이스의 증분 복원 수행</span><span class="sxs-lookup"><span data-stu-id="de8a1-213">Performing a Piecemeal Restore of a Database Whose Recovery Model Has Been Switched from Simple to Full</span></span>  
 <span data-ttu-id="de8a1-214">전체 또는 부분 데이터베이스 백업 이후 단순 복구 모델에서 전체 복구 모델로 전환된 데이터베이스의 증분 복원을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="de8a1-214">You can perform a piecemeal restore of a database that has been switched from the simple recovery model to the full recovery model since the full partial or database backup.</span></span> <span data-ttu-id="de8a1-215">예를 들어 다음 단계를 수행할 데이터베이스가 있다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="de8a1-215">For example, consider a database for which you take the following steps:</span></span>  
  
1.  <span data-ttu-id="de8a1-216">단순 모델 데이터베이스의 부분 백업(backup_1)을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="de8a1-216">Create a partial backup (backup_1) of a simple-model database.</span></span>  
  
2.  <span data-ttu-id="de8a1-217">조만간 복구 모델을 전체 모델로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="de8a1-217">After some time, change the recovery model to full.</span></span>  
  
3.  <span data-ttu-id="de8a1-218">차등 백업을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="de8a1-218">Create a differential backup.</span></span>  
  
4.  <span data-ttu-id="de8a1-219">로그 백업을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="de8a1-219">Start taking log backups.</span></span>  
  
 <span data-ttu-id="de8a1-220">이제 다음 순서를 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="de8a1-220">Thereafter, the following sequence is valid:</span></span>  
  
1.  <span data-ttu-id="de8a1-221">일부 보조 파일 그룹을 생략한 부분 복원</span><span class="sxs-lookup"><span data-stu-id="de8a1-221">A partial restore that omits some secondary filegroups.</span></span>  
  
2.  <span data-ttu-id="de8a1-222">다른 필수 복원 후 이어지는 차등 복원</span><span class="sxs-lookup"><span data-stu-id="de8a1-222">A differential restore followed by any other needed restores.</span></span>  
  
3.  <span data-ttu-id="de8a1-223">나중에 backup_1 부분 백업에서 읽기/쓰기 보조 파일 그룹의 파일을 WITH NORECOVERY 옵션을 사용하여 복원</span><span class="sxs-lookup"><span data-stu-id="de8a1-223">Later, a file restore of a read/write secondary filegroup WITH NORECOVERY from the backup_1 partial backup</span></span>  
  
4.  <span data-ttu-id="de8a1-224">데이터를 원래 복구 지점으로 복원하기 위한 원래 증분 복원으로 다른 모든 백업이 복원된 후 이어지는 차등 백업</span><span class="sxs-lookup"><span data-stu-id="de8a1-224">The differential backup followed by any other backups that were restored in the original piecemeal restore sequence to restore the data up to the original recovery point.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de8a1-225">참고 항목</span><span class="sxs-lookup"><span data-stu-id="de8a1-225">See Also</span></span>  
 <span data-ttu-id="de8a1-226">[트랜잭션 로그 백업 적용&#40;SQL Server&#41;](transaction-log-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="de8a1-226">[Apply Transaction Log Backups &#40;SQL Server&#41;](transaction-log-backups-sql-server.md) </span></span>  
 <span data-ttu-id="de8a1-227">[RESTORE&#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="de8a1-227">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 <span data-ttu-id="de8a1-228">[SQL Server 데이터베이스를 지정 시간으로 복원&#40;전체 복구 모델&#41;](restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="de8a1-228">[Restore a SQL Server Database to a Point in Time &#40;Full Recovery Model&#41;](restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md) </span></span>  
 <span data-ttu-id="de8a1-229">[복원 및 복구 개요&#40;SQL Server&#41;](restore-and-recovery-overview-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="de8a1-229">[Restore and Recovery Overview &#40;SQL Server&#41;](restore-and-recovery-overview-sql-server.md) </span></span>  
 [<span data-ttu-id="de8a1-230">복원 시퀀스 계획 및 수행&#40;전체 복구 모델&#41;</span><span class="sxs-lookup"><span data-stu-id="de8a1-230">Plan and Perform Restore Sequences &#40;Full Recovery Model&#41;</span></span>](plan-and-perform-restore-sequences-full-recovery-model.md)  
  
  
