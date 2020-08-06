---
title: 파일 상태 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- restoring file state [SQL Server]
- verifying file states
- current file states
- verifying filegroup states
- file states [SQL Server]
- online file state
- offline file state [SQL Server]
- viewing filegroup states
- viewing file states
- suspect file state
- recovering file state [SQL Server]
- current filegroup state
- recovery pending file state [SQL Server]
- displaying file states
- states [SQL Server], files
- displaying filegroup states
- defunct file state
ms.assetid: b426474d-8954-4df0-b78b-887becfbe8d6
author: stevestein
ms.author: sstein
ms.openlocfilehash: b7cad94527d9191609a6920b5dfa200a98cd8bbd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659452"
---
# <a name="file-states"></a><span data-ttu-id="31f33-102">파일 상태</span><span class="sxs-lookup"><span data-stu-id="31f33-102">File States</span></span>
  <span data-ttu-id="31f33-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 데이터베이스 파일의 상태는 데이터베이스 상태와는 별도로 유지 관리됩니다.</span><span class="sxs-lookup"><span data-stu-id="31f33-103">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the state of a database file is maintained independently from the state of the database.</span></span> <span data-ttu-id="31f33-104">파일은 항상 하나의 특정 상태에 있습니다. 예를 들어 ONLINE이나 OFFLINE 상태일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="31f33-104">A file is always in one specific state, such as ONLINE or OFFLINE.</span></span> <span data-ttu-id="31f33-105">파일의 현재 상태를 보려면 [sys.master_files](/sql/relational-databases/system-catalog-views/sys-master-files-transact-sql) 또는 [sys.database_files](/sql/relational-databases/system-catalog-views/sys-database-files-transact-sql) 카탈로그 뷰를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="31f33-105">To view the current state of a file, use the [sys.master_files](/sql/relational-databases/system-catalog-views/sys-master-files-transact-sql) or [sys.database_files](/sql/relational-databases/system-catalog-views/sys-database-files-transact-sql) catalog view.</span></span> <span data-ttu-id="31f33-106">데이터베이스가 오프라인 상태일 경우 [sys.master_files](/sql/relational-databases/system-catalog-views/sys-master-files-transact-sql) 카탈로그 뷰에서 파일 상태를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="31f33-106">If the database is offline, the state of the files can be viewed from the [sys.master_files](/sql/relational-databases/system-catalog-views/sys-master-files-transact-sql) catalog view.</span></span>  
  
 <span data-ttu-id="31f33-107">파일 그룹의 파일 상태에 따라 전체 파일 그룹의 사용 가능 여부가 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="31f33-107">The state of the files in a filegroup determines the availability of the whole filegroup.</span></span> <span data-ttu-id="31f33-108">파일 그룹을 사용하려면 파일 그룹 내의 모든 파일이 온라인 상태여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="31f33-108">For a filegroup to be available, all files within the filegroup must be online.</span></span> <span data-ttu-id="31f33-109">파일 그룹의 현재 상태를 보려면 [sys.filegroups](/sql/relational-databases/system-catalog-views/sys-filegroups-transact-sql) 카탈로그 뷰를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="31f33-109">To view the current state of a filegroup, use the [sys.filegroups](/sql/relational-databases/system-catalog-views/sys-filegroups-transact-sql) catalog view.</span></span> <span data-ttu-id="31f33-110">[!INCLUDE[tsql](../../includes/tsql-md.md)] 문으로 오프라인 상태의 파일 그룹에 액세스하려고 하면 오류가 발생하여 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="31f33-110">If a filegroup is offline and you try to access the filegroup by a [!INCLUDE[tsql](../../includes/tsql-md.md)] statement, it will fail with an error.</span></span> <span data-ttu-id="31f33-111">쿼리 최적화 프로그램에서 SELECT 문에 대한 쿼리 계획을 작성할 때 문이 성공하도록 오프라인 파일 그룹에 있는 비클러스터형 인덱스와 인덱싱된 뷰는 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="31f33-111">When the query optimizer builds query plans for SELECT statements, it avoids nonclustered indexes and indexed views that reside in offline filegroups, letting these statements to succeed.</span></span> <span data-ttu-id="31f33-112">그러나 오프라인 파일 그룹에 대상 테이블의 힙이나 클러스터형 인덱스가 있는 경우 SELECT 문은 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="31f33-112">However, if the offline filegroup contains the heap or clustered index of the target table, the SELECT statements fail.</span></span> <span data-ttu-id="31f33-113">오프라인 파일 그룹의 인덱스를 사용하여 테이블을 수정하는 INSERT, UPDATE 또는 DELETE 문도 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="31f33-113">Additionally, any INSERT, UPDATE, or DELETE statement that modifies a table with any index in an offline filegroup will fail.</span></span>  
  
## <a name="file-state-definitions"></a><span data-ttu-id="31f33-114">파일 상태 정의</span><span class="sxs-lookup"><span data-stu-id="31f33-114">File State Definitions</span></span>  
 <span data-ttu-id="31f33-115">다음 표에서는 파일 상태를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="31f33-115">The following table defines the file states.</span></span>  
  
|<span data-ttu-id="31f33-116">시스템 상태</span><span class="sxs-lookup"><span data-stu-id="31f33-116">State</span></span>|<span data-ttu-id="31f33-117">정의</span><span class="sxs-lookup"><span data-stu-id="31f33-117">Definition</span></span>|  
|-----------|----------------|  
|<span data-ttu-id="31f33-118">ONLINE</span><span class="sxs-lookup"><span data-stu-id="31f33-118">ONLINE</span></span>|<span data-ttu-id="31f33-119">모든 작업에 파일을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="31f33-119">The file is available for all operations.</span></span> <span data-ttu-id="31f33-120">데이터베이스가 온라인 상태일 경우 주 파일 그룹의 파일은 항상 온라인 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="31f33-120">Files in the primary filegroup are always online if the database itself is online.</span></span> <span data-ttu-id="31f33-121">주 파일 그룹의 파일이 온라인 상태가 아니면 데이터베이스가 온라인 상태가 아니고 보조 파일의 상태가 정의되어 있지 않은 것입니다.</span><span class="sxs-lookup"><span data-stu-id="31f33-121">If a file in the primary filegroup is not online, the database is not online and the states of the secondary files are undefined.</span></span>|  
|<span data-ttu-id="31f33-122">OFFLINE</span><span class="sxs-lookup"><span data-stu-id="31f33-122">OFFLINE</span></span>|<span data-ttu-id="31f33-123">파일에 액세스할 수 없으며 디스크에 파일이 없을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="31f33-123">The file is not available for access and may not be present on the disk.</span></span> <span data-ttu-id="31f33-124">명시적 사용자 동작으로 인해 파일이 오프라인 상태가 되면 추가 사용자 작업이 수행될 때까지 오프라인 상태로 있습니다.</span><span class="sxs-lookup"><span data-stu-id="31f33-124">Files become offline by explicit user action and remain offline until additional user action is taken.</span></span><br /><br /> <span data-ttu-id="31f33-125">주의 파일이 손상 되 면 파일을 오프 라인 으로만 설정 해야 합니다 .이 경우 파일을 복원할 수 있습니다. \*\* \* \* \* \* \*\*</span><span class="sxs-lookup"><span data-stu-id="31f33-125">**\*\* Caution \*\*** A file should only be set offline when the file is corrupted, but it can be restored.</span></span> <span data-ttu-id="31f33-126">오프라인으로 설정된 파일을 온라인으로 설정할 수 있는 유일한 방법은 백업에서 파일을 복원하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="31f33-126">A file set to offline can only be set online by restoring the file from backup.</span></span> <span data-ttu-id="31f33-127">단일 파일 복원 방법은 [RESTORE&#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="31f33-127">For more information about restoring a single file, see [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql).</span></span>|  
|<span data-ttu-id="31f33-128">RESTORING</span><span class="sxs-lookup"><span data-stu-id="31f33-128">RESTORING</span></span>|<span data-ttu-id="31f33-129">파일이 복원되고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="31f33-129">The file is being restored.</span></span> <span data-ttu-id="31f33-130">페이지 복원이 아닌 전체 파일에 영향을 주는 복원 명령으로 인해 파일이 복원 중 상태가 되어 복원이 완료되고 파일이 복구될 때까지 이 상태로 있습니다.</span><span class="sxs-lookup"><span data-stu-id="31f33-130">Files enter the restoring state because of a restore command affecting the whole file, not just a page restore, and remain in this state until the restore is completed and the file is recovered.</span></span>|  
|<span data-ttu-id="31f33-131">RECOVERY PENDING</span><span class="sxs-lookup"><span data-stu-id="31f33-131">RECOVERY PENDING</span></span>|<span data-ttu-id="31f33-132">파일 복구가 연기되었습니다.</span><span class="sxs-lookup"><span data-stu-id="31f33-132">The recovery of the file has been postponed.</span></span> <span data-ttu-id="31f33-133">파일이 복원 및 복구되지 않는 증분 복원 프로세스로 인해 파일이 자동으로 복구 보류 상태가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="31f33-133">A file enters this state automatically because of a piecemeal restore process in which the file is not restored and recovered.</span></span> <span data-ttu-id="31f33-134">오류를 해결하고 복구 프로세스를 완료하기 위한 사용자의 추가적인 동작이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="31f33-134">Additional action by the user is required to resolve the error and allow for the recovery process to be completed.</span></span> <span data-ttu-id="31f33-135">자세한 내용은 [증분 복원&#40;SQL Server&#41;](../backup-restore/piecemeal-restores-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="31f33-135">For more information, see [Piecemeal Restores &#40;SQL Server&#41;](../backup-restore/piecemeal-restores-sql-server.md).</span></span>|  
|<span data-ttu-id="31f33-136">SUSPECT</span><span class="sxs-lookup"><span data-stu-id="31f33-136">SUSPECT</span></span>|<span data-ttu-id="31f33-137">온라인 복원 프로세스 중에 파일 복구가 실패했습니다.</span><span class="sxs-lookup"><span data-stu-id="31f33-137">Recovery of the file failed during an online restore process.</span></span> <span data-ttu-id="31f33-138">파일이 주 파일 그룹에 속하면 데이터베이스도 주의 대상으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="31f33-138">If the file is in the primary filegroup, the database is also marked as suspect.</span></span> <span data-ttu-id="31f33-139">파일이 주 파일 그룹이 아니면 해당 파일만 주의 대상 상태이고 데이터베이스는 계속 온라인 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="31f33-139">Otherwise, only the file is suspect and the database is still online.</span></span><br /><br /> <span data-ttu-id="31f33-140">다음 방법 중 하나를 사용하여 파일을 사용 가능하게 설정할 때까지 파일이 주의 대상 상태로 있습니다.</span><span class="sxs-lookup"><span data-stu-id="31f33-140">The file will remain in the suspect state until it is made available by one of the following methods:</span></span><br /><br /> <span data-ttu-id="31f33-141">복원 및 복구</span><span class="sxs-lookup"><span data-stu-id="31f33-141">Restore and recovery</span></span><br /><br /> <span data-ttu-id="31f33-142">DBCC CHECKDB에 REPAIR_ALLOW_DATA_LOSS 사용</span><span class="sxs-lookup"><span data-stu-id="31f33-142">DBCC CHECKDB with REPAIR_ALLOW_DATA_LOSS</span></span>|  
|<span data-ttu-id="31f33-143">DEFUNCT</span><span class="sxs-lookup"><span data-stu-id="31f33-143">DEFUNCT</span></span>|<span data-ttu-id="31f33-144">온라인 상태가 아닐 때 파일이 삭제되었습니다.</span><span class="sxs-lookup"><span data-stu-id="31f33-144">The file was dropped when it was not online.</span></span> <span data-ttu-id="31f33-145">오프라인 파일 그룹이 제거되면 파일 그룹의 모든 파일이 존재하지 않음 상태가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="31f33-145">All files in a filegroup become defunct when an offline filegroup is removed.</span></span>|  
  
## <a name="related-content"></a><span data-ttu-id="31f33-146">관련 내용</span><span class="sxs-lookup"><span data-stu-id="31f33-146">Related Content</span></span>  
 [<span data-ttu-id="31f33-147">ALTER DATABASE&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="31f33-147">ALTER DATABASE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-database-transact-sql)  
  
 [<span data-ttu-id="31f33-148">데이터베이스 상태</span><span class="sxs-lookup"><span data-stu-id="31f33-148">Database States</span></span>](database-states.md)  
  
 [<span data-ttu-id="31f33-149">미러링 상태&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="31f33-149">Mirroring States &#40;SQL Server&#41;</span></span>](../../database-engine/database-mirroring/mirroring-states-sql-server.md)  
  
 [<span data-ttu-id="31f33-150">DBCC CHECKDB&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="31f33-150">DBCC CHECKDB &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql)  
  
 [<span data-ttu-id="31f33-151">데이터베이스 파일 및 파일 그룹</span><span class="sxs-lookup"><span data-stu-id="31f33-151">Database Files and Filegroups</span></span>](database-files-and-filegroups.md)  
  
  
