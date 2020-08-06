---
title: '백업 및 복원: 상호 운용성 및 공존성(SQL Server) | Microsoft 문서'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- file restores [SQL Server], related features
- restoring [SQL Server], files
- restoring files [SQL Server], related features
- backups [SQL Server], files or filegroups
- file backups [SQL Server], related features
ms.assetid: 69f212b8-edcd-4c5d-8a8a-679ced33c128
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: cd78e5f1e85510ec7a14548280a616a9b32aec55
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638863"
---
# <a name="backup-and-restore-interoperability-and-coexistence-sql-server"></a><span data-ttu-id="489ed-102">백업 및 복원: 상호 운용성 및 공존성(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="489ed-102">Backup and Restore: Interoperability and Coexistence (SQL Server)</span></span>
  <span data-ttu-id="489ed-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]의 몇 가지 기능에 대한 백업 및 복원 고려 사항에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="489ed-103">This topic describes backup-and-restore considerations for several features in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="489ed-104">이러한 기능에는 파일 복원 및 데이터베이스 시작, 온라인 복원 및 비활성 인덱스, 데이터베이스 미러링, 증분 복원 및 전체 텍스트 인덱스가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="489ed-104">These features include: file restore and database startup, online restore and disabled indexes, database mirroring, and piecemeal restore and full-text indexes.</span></span>  
  
 <span data-ttu-id="489ed-105">**항목 내용:**</span><span class="sxs-lookup"><span data-stu-id="489ed-105">**In this Topic:**</span></span>  
  
-   [<span data-ttu-id="489ed-106">파일 복원 및 데이터베이스 시작</span><span class="sxs-lookup"><span data-stu-id="489ed-106">File Restore and Database Startup</span></span>](#FileRestoreAndDbStartup)  
  
-   [<span data-ttu-id="489ed-107">온라인 복원 및 비활성화된 인덱스</span><span class="sxs-lookup"><span data-stu-id="489ed-107">Online Restore and Disabled Indexes</span></span>](#OnlineRestoreAndDisabledIndexes)  
  
-   [<span data-ttu-id="489ed-108">데이터베이스 미러링, 백업 및 복원</span><span class="sxs-lookup"><span data-stu-id="489ed-108">Database Mirroring and Backup and Restore</span></span>](#DbMandBnR)  
  
-   [<span data-ttu-id="489ed-109">증분 복원 및 전체 텍스트 인덱스</span><span class="sxs-lookup"><span data-stu-id="489ed-109">Piecemeal Restore and Full-Text Indexes</span></span>](#PiecemealAndFTIndexes)  
  
-   [<span data-ttu-id="489ed-110">파일 백업과 복원 및 압축</span><span class="sxs-lookup"><span data-stu-id="489ed-110">File Backup and Restore and Compression</span></span>](#FileBnRandCompression)  
  
-   [<span data-ttu-id="489ed-111">관련 작업</span><span class="sxs-lookup"><span data-stu-id="489ed-111">Related Tasks</span></span>](#RelatedTasks)  
  
##  <a name="file-restore-and-database-startup"></a><a name="FileRestoreAndDbStartup"></a> <span data-ttu-id="489ed-112">파일 복원 및 데이터베이스 시작</span><span class="sxs-lookup"><span data-stu-id="489ed-112">File Restore and Database Startup</span></span>  
 <span data-ttu-id="489ed-113">이 섹션에서는 여러 개의 파일 그룹이 있는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스와 관련된 내용을 다룹니다.</span><span class="sxs-lookup"><span data-stu-id="489ed-113">This section is relevant only for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases that have multiple filegroups.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="489ed-114">데이터베이스를 시작하면 데이터베이스를 닫았을 때 온라인 상태였던 파일을 포함하는 파일 그룹만 복구되고 온라인 상태가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="489ed-114">When a database is started, only filegroups whose files were online when the database was closed are recovered and brought online.</span></span>  
  
 <span data-ttu-id="489ed-115">데이터베이스 시작 중에 문제가 발생하면 복구에 실패하고 데이터베이스가 주의 대상으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="489ed-115">If a problem is encountered during database startup, recovery fails, and the database is marked as SUSPECT.</span></span> <span data-ttu-id="489ed-116">문제를 한 파일이나 몇 개의 파일로 격리시킬 수 있는 경우 데이터베이스 관리자는 해당 파일을 오프라인 상태로 만들고 데이터베이스를 다시 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="489ed-116">If the problem can be isolated to a file or files, the database administrator can take the files offline and try to restart the database.</span></span> <span data-ttu-id="489ed-117">파일을 오프라인 상태로 만들려면 다음 [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql) 문을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="489ed-117">To take a file offline, you can use the following [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql) statement:</span></span>  
  
 <span data-ttu-id="489ed-118">ALTER database *database_name* MODIFY 파일 (이름 **= ' *`filename`* '**, 오프 라인)</span><span class="sxs-lookup"><span data-stu-id="489ed-118">ALTER DATABASE *database_name* MODIFY FILE (NAME **='*`filename`*'**, OFFLINE)</span></span>  
  
 <span data-ttu-id="489ed-119">데이터베이스가 성공적으로 시작되면 오프라인 파일을 포함하는 모든 파일 그룹은 오프라인 상태로 남게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="489ed-119">If startup succeeds, any filegroup that contains an offline file remains offline.</span></span>  
  
##  <a name="online-restore-and-disabled-indexes"></a><a name="OnlineRestoreAndDisabledIndexes"></a> <span data-ttu-id="489ed-120">온라인 복원 및 비활성화된 인덱스</span><span class="sxs-lookup"><span data-stu-id="489ed-120">Online Restore and Disabled Indexes</span></span>  
 <span data-ttu-id="489ed-121">이 섹션에서는 여러 개의 파일 그룹이 있는 데이터베이스와 관련된 내용 및 단순 복구 모델의 경우 하나 이상의 읽기 전용 파일 그룹과 관련된 내용을 다룹니다.</span><span class="sxs-lookup"><span data-stu-id="489ed-121">This section is relevant only for databases that have multiple filegroups and, for the simple recovery model, at least one read-only filegroup.</span></span>  
  
 <span data-ttu-id="489ed-122">이러한 경우 데이터베이스가 온라인 상태이면 인덱스를 생성, 삭제, 활성화 또는 비활성화하기 위해서는 일부라도 인덱스를 보유하는 모든 파일 그룹이 온라인 상태여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="489ed-122">In these cases, when a database is online, the index can be created, dropped, enabled or disabled only if all filegroups holding any part of the index are online.</span></span>  
  
 <span data-ttu-id="489ed-123">오프라인 파일 그룹을 복원하는 방법은 [온라인 복원&#40;SQL Server&#41;](online-restore-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="489ed-123">For information about restoring offline filegroups, see [Online Restore &#40;SQL Server&#41;](online-restore-sql-server.md).</span></span>  
  
##  <a name="database-mirroring-and-backup-and-restore"></a><a name="DbMandBnR"></a> <span data-ttu-id="489ed-124">데이터베이스 미러링, 백업 및 복원</span><span class="sxs-lookup"><span data-stu-id="489ed-124">Database Mirroring and Backup and Restore</span></span>  
 <span data-ttu-id="489ed-125">이 섹션에서는 여러 개의 파일 그룹이 있는 전체 모델 데이터베이스와 관련된 내용을 다룹니다.</span><span class="sxs-lookup"><span data-stu-id="489ed-125">This section is relevant only for full-model databases that have multiple filegroups.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="489ed-126">이후 버전의 Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서는 데이터베이스 미러링 기능이 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="489ed-126">The database mirroring feature will be removed in a future version of Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="489ed-127">새 개발 작업에서는 이 기능을 사용하지 않도록 하고, 현재 이 기능을 사용하는 애플리케이션은 수정하세요.</span><span class="sxs-lookup"><span data-stu-id="489ed-127">Avoid using this feature in new development work, and plan to modify applications that currently use this feature.</span></span> <span data-ttu-id="489ed-128">대신 [!INCLUDE[ssHADR](../../includes/sshadr-md.md)]를 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="489ed-128">Use [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] instead.</span></span>  
  
 <span data-ttu-id="489ed-129">데이터베이스 미러링은 데이터베이스의 가용성을 높이기 위한 솔루션입니다.</span><span class="sxs-lookup"><span data-stu-id="489ed-129">Database mirroring is a solution for increasing database availability.</span></span> <span data-ttu-id="489ed-130">미러링은 데이터베이스 단위로 구현되며 전체 복구 모델을 사용하는 데이터베이스에서만 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="489ed-130">Mirroring is implemented on a per-database basis and works only with databases that use the full recovery model.</span></span> <span data-ttu-id="489ed-131">자세한 내용은 [데이터베이스 미러링&#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="489ed-131">For more information, see [Database Mirroring &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="489ed-132">데이터베이스에서 파일 그룹의 하위 집합 복사본을 배포하려면 복제를 이용하세요. 다른 서버로 복사할 파일 그룹의 개체만 복제해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="489ed-132">To distribute copies of a subset of the filegroups in a database, use replication: replicate only those objects in the filegroups you want to copy to other servers.</span></span> <span data-ttu-id="489ed-133">복제에 대한 자세한 내용은 [SQL Server 복제](../../relational-databases/replication/sql-server-replication.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="489ed-133">For more information about replication, see [SQL Server Replication](../../relational-databases/replication/sql-server-replication.md).</span></span>  
  
### <a name="creating-the-mirror-database"></a><span data-ttu-id="489ed-134">미러 데이터베이스 만들기</span><span class="sxs-lookup"><span data-stu-id="489ed-134">Creating the Mirror Database</span></span>  
 <span data-ttu-id="489ed-135">미러 데이터베이스는 미러 서버에서 주 데이터베이스의 백업을 복구하지 않고 복원함으로써 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="489ed-135">The mirror database is created by restoring, WITH NORECOVERY, backups of the principal database on the mirror server.</span></span> <span data-ttu-id="489ed-136">복원 시 동일한 데이터베이스 이름을 유지해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="489ed-136">The restore must keep the same database name.</span></span> <span data-ttu-id="489ed-137">자세한 내용은 [미러 데이터베이스의 미러링 준비&#40;SQL Server&#41;](../../database-engine/database-mirroring/prepare-a-mirror-database-for-mirroring-sql-server.md)을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="489ed-137">For more information, see [Prepare a Mirror Database for Mirroring &#40;SQL Server&#41;](../../database-engine/database-mirroring/prepare-a-mirror-database-for-mirroring-sql-server.md).</span></span>  
  
 <span data-ttu-id="489ed-138">지원되는 경우 증분 복원 시퀀스를 사용하여 미러 데이터베이스를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="489ed-138">You can create the mirror database by using use a piecemeal restore sequence, where supported.</span></span> <span data-ttu-id="489ed-139">그러나 파일 그룹을 모두 복원하기 전까지는 미러링을 시작할 수 없으며 일반적으로 미러 데이터베이스를 가져오기 위한 복원된 로그 백업은 주 데이터베이스에 의해 지정 시간 내에 닫을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="489ed-139">However, you cannot start mirroring until you have restored all the filegroups and, typically, restored log backups to get the mirror database close enough in time with the principal database.</span></span> <span data-ttu-id="489ed-140">자세한 내용은 [증분 복원&#40;SQL Server&#41;](piecemeal-restores-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="489ed-140">For more information, see [Piecemeal Restores &#40;SQL Server&#41;](piecemeal-restores-sql-server.md).</span></span>  
  
### <a name="restrictions-on-backup-and-restore-during-mirroring"></a><span data-ttu-id="489ed-141">미러링 도중 백업 및 복원에 대한 제한 사항</span><span class="sxs-lookup"><span data-stu-id="489ed-141">Restrictions on Backup and Restore During Mirroring</span></span>  
 <span data-ttu-id="489ed-142">데이터베이스 미러링 세션이 활성화되어 있는 동안에는 다음과 같은 제한 사항이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="489ed-142">While a database mirroring session is active, the following restrictions apply:</span></span>  
  
-   <span data-ttu-id="489ed-143">미러 데이터베이스의 백업 및 복원이 허용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="489ed-143">Backup and restore of the mirror database are not allowed.</span></span>  
  
-   <span data-ttu-id="489ed-144">주 데이터베이스의 백업은 허용되지만 BACKUP LOG WITH NORECOVERY는 허용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="489ed-144">Backup of the principal database is allowed, but BACKUP LOG WITH NORECOVERY is not allowed.</span></span>  
  
-   <span data-ttu-id="489ed-145">주 데이터베이스 복원이 허용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="489ed-145">Restoring the principal database is not allowed.</span></span>  
  
##  <a name="piecemeal-restore-and-full-text-indexes"></a><a name="PiecemealAndFTIndexes"></a> <span data-ttu-id="489ed-146">증분 복원 및 전체 텍스트 인덱스</span><span class="sxs-lookup"><span data-stu-id="489ed-146">Piecemeal Restore and Full-Text Indexes</span></span>  
 <span data-ttu-id="489ed-147">이 섹션에서는 여러 개의 파일 그룹이 있는 데이터베이스와 관련된 내용 및 단순 모델 데이터베이스의 경우 읽기 전용 파일 그룹과 관련된 내용을 다룹니다.</span><span class="sxs-lookup"><span data-stu-id="489ed-147">This section is relevant only for databases that contain multiple filegroups and, for the simple-model databases, only for read-only filegroups.</span></span>  
  
 <span data-ttu-id="489ed-148">전체 텍스트 인덱스는 데이터베이스 파일 그룹에 저장되며 증분 복원의 영향을 받을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="489ed-148">Full-text indexes are stored in database filegroups and can be affected by a piecemeal restore.</span></span> <span data-ttu-id="489ed-149">전체 텍스트 인덱스가 관련 테이블 데이터와 동일한 파일 그룹에 있는 경우 증분 복원은 올바르게 동작합니다.</span><span class="sxs-lookup"><span data-stu-id="489ed-149">If the full-text index resides in the same filegroup as any of the associated table data, piecemeal restore works as expected.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="489ed-150">전체 텍스트 인덱스가 포함된 파일 그룹의 파일 그룹 ID를 보려면 [sys.fulltext_indexes](/sql/relational-databases/system-catalog-views/sys-fulltext-indexes-transact-sql)의 data_space_id 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="489ed-150">To view the filegroup ID of the filegroup that contains a full-text index, select the data_space_id column of [sys.fulltext_indexes](/sql/relational-databases/system-catalog-views/sys-fulltext-indexes-transact-sql).</span></span>  
  
### <a name="full-text-indexes-and-tables-in-separate-filegroups"></a><span data-ttu-id="489ed-151">분리된 파일 그룹 내의 전체 텍스트 인덱스 및 테이블</span><span class="sxs-lookup"><span data-stu-id="489ed-151">Full-Text Indexes and Tables in Separate Filegroups</span></span>  
 <span data-ttu-id="489ed-152">전체 텍스트 인덱스가 모든 관련 테이블 데이터와 별개의 파일 그룹에 존재하는 경우 증분 복원의 동작은 어느 파일 그룹이 먼저 복원되어 온라인 상태가 되는지에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="489ed-152">If a full-text index resides in a separate filegroup from all of the associated table data, the behavior of piecemeal restore depends on which of the filegroups is restored and brought online first:</span></span>  
  
-   <span data-ttu-id="489ed-153">전체 텍스트 인덱스가 포함된 파일 그룹이 관련 테이블 데이터가 포함된 파일 그룹보다 먼저 복원되어 온라인 상태가 되는 경우 전체 텍스트 검색은 전체 텍스트 인덱스가 온라인 상태가 된 직후부터 올바르게 동작합니다.</span><span class="sxs-lookup"><span data-stu-id="489ed-153">If the filegroup that contains the full-text index is restored and brought online before the filegroups that contain the associated table data, full-text search works as expected as soon as the full-text index is online.</span></span>  
  
-   <span data-ttu-id="489ed-154">테이블 데이터가 포함된 파일 그룹이 전체 텍스트 인덱스가 포함된 파일 그룹보다 먼저 복원되어 온라인 상태가 되는 경우 전체 텍스트 동작이 영향을 받을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="489ed-154">If the filegroup that contains the table data is restored and brought online before the filegroup that contains the full-text index, full-text behavior might be affected.</span></span> <span data-ttu-id="489ed-155">이는 채우기를 트리거하고 카탈로그를 다시 작성하거나 카탈로그를 인식하는 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문은 인덱스가 온라인 상태가 될 때까지 실패하기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="489ed-155">This is because [!INCLUDE[tsql](../../includes/tsql-md.md)] statements that trigger a population, rebuild the catalog, or reorganize the catalog fail until the index is brought online.</span></span> <span data-ttu-id="489ed-156">이러한 문에는 CREATE FULLTEXT INDEX, ALTER FULLTEXT INDEX, DROP FULLTEXT INDEX 및 ALTER FULLTEXT CATALOG가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="489ed-156">These statements include CREATE FULLTEXT INDEX, ALTER FULLTEXT INDEX, DROP FULLTEXT INDEX, and ALTER FULLTEXT CATALOG.</span></span>  
  
     <span data-ttu-id="489ed-157">이 경우 다음과 같은 사항이 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="489ed-157">In this case, the following factors are significant:</span></span>  
  
    -   <span data-ttu-id="489ed-158">전체 텍스트 인덱스에 변경 내용 추적이 있는 경우 사용자 DML은 인덱스 파일 그룹이 온라인 상태가 될 때까지 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="489ed-158">If the full-text index has change tracking, user DML will fail until the index filegroup is brought online.</span></span> <span data-ttu-id="489ed-159">삭제 작업도 인덱스 파일 그룹이 온라인 상태가 될 때까지 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="489ed-159">Delete operation will also fail until the index filegroup is online.</span></span>  
  
    -   <span data-ttu-id="489ed-160">인덱스를 사용할 수 없으므로 변경 내용 추적에 관계 없이 전체 텍스트 쿼리는 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="489ed-160">Regardless of change tracking, full-text queries fail because the index is not available.</span></span> <span data-ttu-id="489ed-161">전체 텍스트 인덱스가 포함된 파일 그룹이 오프라인일 때 전체 텍스트 쿼리를 시도하면 오류가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="489ed-161">If a full-text query is tried when the filegroup that contains the full-text index is offline, an error is returned.</span></span>  
  
    -   <span data-ttu-id="489ed-162">상태 함수(예: FULLTEXTCATALOGPROPERTY)는 전체 텍스트 인덱스에 액세스할 필요가 없을 때에만 성공합니다.</span><span class="sxs-lookup"><span data-stu-id="489ed-162">Status functions (such as FULLTEXTCATALOGPROPERTY) succeed only when they do not have to access full-text index.</span></span> <span data-ttu-id="489ed-163">예를 들어 온라인 전체 텍스트 메타데이터에 대한 액세스는 성공하지만 **uniquekeycount, itemcount** 는 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="489ed-163">For example, access to any online full-text metadata would succeed, but **uniquekeycount, itemcount** would fail.</span></span>  
  
     <span data-ttu-id="489ed-164">전체 텍스트 인덱스 파일 그룹을 복원하여 온라인 상태로 만든 후에는 인덱스 데이터와 테이블 데이터가 일치합니다.</span><span class="sxs-lookup"><span data-stu-id="489ed-164">After the full-text index filegroup is restored and brought online, the index data and table data are consistent.</span></span>  
  
 <span data-ttu-id="489ed-165">기본 테이블 파일 그룹과 전체 텍스트 인덱스 파일 그룹이 모두 온라인 상태가 된 직후부터 일시 중지된 전체 텍스트 채우기가 재개됩니다.</span><span class="sxs-lookup"><span data-stu-id="489ed-165">As soon as both the base table filegroup and the full-text index filegroup are online, any paused full-text population is resumed.</span></span>  
  
##  <a name="file-backup-and-restore-and-compression"></a><a name="FileBnRandCompression"></a> <span data-ttu-id="489ed-166">파일 백업과 복원 및 압축</span><span class="sxs-lookup"><span data-stu-id="489ed-166">File Backup and Restore and Compression</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="489ed-167">에서는 읽기 전용 파일 그룹과 읽기 전용 데이터베이스에 대한 NTFS 파일 시스템 데이터 압축을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="489ed-167">supports NTFS file system data compression of read-only filegroups and read-only databases.</span></span>  
  
 <span data-ttu-id="489ed-168">압축된 NTFS 파일에 대해 읽기 전용 파일 그룹의 파일 복원이 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="489ed-168">Restoring files in a read-only filegroup is supported on compressed NTFS files.</span></span> <span data-ttu-id="489ed-169">이러한 파일 그룹의 백업 및 복원은 기본적으로 모든 읽기 전용 파일 그룹에서와 동일하게 동작하지만 다음과 같은 예외가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="489ed-169">Backup and restore of these filegroups works essentially as it would for any read-only filegroup, with the following exceptions:</span></span>  
  
-   <span data-ttu-id="489ed-170">읽기/쓰기 파일(읽기/쓰기 데이터베이스의 기본 또는 로그 파일 포함)을 압축된 볼륨으로 복원하는 경우 실패하고 오류 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="489ed-170">Restoring a read-write file (including the primary or log files of a read-write database) to a compressed volume fails and displays an error.</span></span>  
  
-   <span data-ttu-id="489ed-171">읽기 전용 데이터베이스의 경우 압축된 볼륨으로 복원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="489ed-171">Restoring a read-only database to a compressed volume is allowed.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="489ed-172">읽기/쓰기 데이터베이스의 로그 파일은 압축 파일 시스템에 저장할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="489ed-172">Log files of read/write databases should never be placed on compressed file systems.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="489ed-173">관련 작업</span><span class="sxs-lookup"><span data-stu-id="489ed-173">Related Tasks</span></span>  
  
-   [<span data-ttu-id="489ed-174">미러 데이터베이스의 미러링 준비&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="489ed-174">Prepare a Mirror Database for Mirroring &#40;SQL Server&#41;</span></span>](../../database-engine/database-mirroring/prepare-a-mirror-database-for-mirroring-sql-server.md)  
  
-   [<span data-ttu-id="489ed-175">전체 텍스트 카탈로그와 인덱스 백업 및 복원</span><span class="sxs-lookup"><span data-stu-id="489ed-175">Back Up and Restore Full-Text Catalogs and Indexes</span></span>](../search/back-up-and-restore-full-text-catalogs-and-indexes.md)  
  
## <a name="see-also"></a><span data-ttu-id="489ed-176">참고 항목</span><span class="sxs-lookup"><span data-stu-id="489ed-176">See Also</span></span>  
 <span data-ttu-id="489ed-177">[SQL Server 데이터베이스 백업 및 복원](back-up-and-restore-of-sql-server-databases.md) </span><span class="sxs-lookup"><span data-stu-id="489ed-177">[Back Up and Restore of SQL Server Databases](back-up-and-restore-of-sql-server-databases.md) </span></span>  
 <span data-ttu-id="489ed-178">[복제된 데이터베이스 백업 및 복원](../replication/administration/back-up-and-restore-replicated-databases.md) </span><span class="sxs-lookup"><span data-stu-id="489ed-178">[Back Up and Restore Replicated Databases](../replication/administration/back-up-and-restore-replicated-databases.md) </span></span>  
 [<span data-ttu-id="489ed-179">활성 보조: 보조 복제본에 대 한 백업 &#40;AlwaysOn 가용성 그룹&#41;</span><span class="sxs-lookup"><span data-stu-id="489ed-179">Active Secondaries: Backup on Secondary Replicas &#40;AlwaysOn Availability Groups&#41;</span></span>](../../database-engine/availability-groups/windows/active-secondaries-backup-on-secondary-replicas-always-on-availability-groups.md)  
  
  
