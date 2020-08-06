---
title: 페이지 복원(SQL Server) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- sql12.swb.restorepage.general.f1
helpviewer_keywords:
- restoring pages [SQL Server]
- pages [SQL Server], restoring
- databases [SQL Server], damaged
- page restores [SQL Server]
- pages [SQL Server], damaged
- restoring [SQL Server], pages
ms.assetid: 07e40950-384e-4d84-9ac5-84da6dd27a91
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 6fb008314b9cb156f1cc575bda71b6364eca6e3a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730755"
---
# <a name="restore-pages-sql-server"></a><span data-ttu-id="eede2-102">페이지 복원(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="eede2-102">Restore Pages (SQL Server)</span></span>
  <span data-ttu-id="eede2-103">이 항목에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 을 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)]에서 페이지를 복원하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="eede2-103">This topic describes how to restore pages in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="eede2-104">페이지 복원의 목표는 전체 데이터베이스를 복원하지 않고 하나 이상의 손상된 페이지를 복원하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="eede2-104">The goal of a page restore is to restore one or more damaged pages without restoring the whole database.</span></span> <span data-ttu-id="eede2-105">일반적으로 복원 후보 페이지는 페이지에 액세스할 때 발생한 오류 때문에 "주의 대상"으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="eede2-105">Typically, pages that are candidates for restore have been marked as "suspect" because of an error that is encountered when accessing the page.</span></span> <span data-ttu-id="eede2-106">주의 대상 페이지는 [msdb](/sql/relational-databases/system-tables/suspect-pages-transact-sql) 데이터베이스의 **suspect_pages** 테이블에서 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eede2-106">Suspect pages are identified in the [suspect_pages](/sql/relational-databases/system-tables/suspect-pages-transact-sql) table in the **msdb** database.</span></span>  
  
 <span data-ttu-id="eede2-107">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="eede2-107">**In This Topic**</span></span>  
  
-   <span data-ttu-id="eede2-108">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="eede2-108">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="eede2-109">페이지 복원이 유용한 경우</span><span class="sxs-lookup"><span data-stu-id="eede2-109">When is a Page Restore Useful?</span></span>](#WhenUseful)  
  
     [<span data-ttu-id="eede2-110">제한 사항</span><span class="sxs-lookup"><span data-stu-id="eede2-110">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="eede2-111">권장 사항</span><span class="sxs-lookup"><span data-stu-id="eede2-111">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="eede2-112">보안</span><span class="sxs-lookup"><span data-stu-id="eede2-112">Security</span></span>](#Security)  
  
-   <span data-ttu-id="eede2-113">**페이지를 복원하려면**</span><span class="sxs-lookup"><span data-stu-id="eede2-113">**To restore pages, using:**</span></span>  
  
     [<span data-ttu-id="eede2-114">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="eede2-114">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="eede2-115">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="eede2-115">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="eede2-116">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="eede2-116">Before You Begin</span></span>  
  
###  <a name="when-is-a-page-restore-useful"></a><a name="WhenUseful"></a> <span data-ttu-id="eede2-117">페이지 복원이 유용한 경우</span><span class="sxs-lookup"><span data-stu-id="eede2-117">When is a Page Restore Useful?</span></span>  
 <span data-ttu-id="eede2-118">페이지 복원은 격리된 손상 페이지를 복구하기 위한 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="eede2-118">A page restore is intended for repairing isolated damaged pages.</span></span> <span data-ttu-id="eede2-119">몇몇 페이지를 각각 복원하고 복구하면 복원 작업 도중 오프라인 상태인 데이터의 양이 줄어들어 파일 복원보다 빠를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eede2-119">Restoring and recovering a few individual pages might be faster than a file restore, reducing the amount of data that is offline during a restore operation.</span></span> <span data-ttu-id="eede2-120">그러나 파일에 있는 여러 페이지를 복원할 경우에는 일반적으로 전체 파일을 복원하는 것이 효율적입니다.</span><span class="sxs-lookup"><span data-stu-id="eede2-120">However, if you have to restore more than a few pages in a file, it is generally more efficient to restore the whole file.</span></span> <span data-ttu-id="eede2-121">예를 들어 디바이스의 여러 페이지에서 디바이스 오류의 가능성을 나타내는 경우 파일을 다른 위치로 복원한 다음 해당 디바이스를 복구해 보세요.</span><span class="sxs-lookup"><span data-stu-id="eede2-121">For example, if lots of pages on a device indicate a pending device failure, consider restoring the file, possibly to another location, and repairing the device.</span></span>  
  
 <span data-ttu-id="eede2-122">또한 모든 페이지 오류를 복원해야 하는 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="eede2-122">Furthermore, not all page errors require a restore.</span></span> <span data-ttu-id="eede2-123">보조 인덱스와 같은 캐시 데이터에서 발생한 문제는 데이터를 다시 계산하여 해결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eede2-123">A problem can occur in cached data, such as a secondary index, that can be resolved by recalculating the data.</span></span> <span data-ttu-id="eede2-124">예를 들어 데이터베이스 관리자가 보조 인덱스를 삭제하고 다시 작성하면 손상된 데이터는 수정되었더라도 [suspect_pages](/sql/relational-databases/system-tables/suspect-pages-transact-sql) 테이블에 이러한 수정 내용이 반영되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eede2-124">For example, if the database administrator drops a secondary index and rebuilds it, the corrupted data, although fixed, is not indicated as such in the [suspect_pages](/sql/relational-databases/system-tables/suspect-pages-transact-sql) table.</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="eede2-125">제한 사항</span><span class="sxs-lookup"><span data-stu-id="eede2-125">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="eede2-126">페이지 복원은 전체 복구 모델 또는 대량 로그 복구 모델을 사용하는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="eede2-126">Page restore applies to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases that are using the full or bulk-logged recovery models.</span></span> <span data-ttu-id="eede2-127">페이지 복원은 읽기/쓰기 파일 그룹에 대해서만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="eede2-127">Page restore is supported only for read/write filegroups.</span></span>  
  
-   <span data-ttu-id="eede2-128">데이터베이스 페이지만 복원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eede2-128">Only database pages can be restored.</span></span> <span data-ttu-id="eede2-129">다음 항목은 페이지 복원을 사용하여 복원할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="eede2-129">Page restore cannot be used to restore the following:</span></span>  
  
    -   <span data-ttu-id="eede2-130">트랜잭션 로그</span><span class="sxs-lookup"><span data-stu-id="eede2-130">Transaction log</span></span>  
  
    -   <span data-ttu-id="eede2-131">할당 페이지: GAM(글로벌 할당 맵) 페이지, SGAM(공유 글로벌 할당 맵) 페이지 및 PFS(페이지 여유 공간) 페이지.</span><span class="sxs-lookup"><span data-stu-id="eede2-131">Allocation pages: Global Allocation Map (GAM) pages, Shared Global Allocation Map (SGAM) pages, and Page Free Space (PFS) pages.</span></span>  
  
    -   <span data-ttu-id="eede2-132">모든 데이터 파일의 0페이지(파일 부트 페이지)</span><span class="sxs-lookup"><span data-stu-id="eede2-132">Page 0 of all data files (the file boot page)</span></span>  
  
    -   <span data-ttu-id="eede2-133">1:9페이지(데이터베이스 부트 페이지)</span><span class="sxs-lookup"><span data-stu-id="eede2-133">Page 1:9 (the database boot page)</span></span>  
  
    -   <span data-ttu-id="eede2-134">전체 텍스트 카탈로그</span><span class="sxs-lookup"><span data-stu-id="eede2-134">Full-text catalog</span></span>  
  
-   <span data-ttu-id="eede2-135">대량 로그 복구 모델을 사용하는 데이터베이스의 경우 페이지 복원에는 다음의 추가 조건이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eede2-135">For a database that uses the bulk-logged recovery model, page restore has the following additional conditions:</span></span>  
  
    -   <span data-ttu-id="eede2-136">파일 그룹 또는 페이지 데이터가 오프라인 상태인 동안 백업하는 것은 오프라인 데이터가 로그에 기록되지 않으므로 대량 로그 데이터의 경우 문제가 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eede2-136">Backing up while filegroup or page data is offline is problematic for bulk-logged data, because the offline data is not recorded in the log.</span></span> <span data-ttu-id="eede2-137">오프라인 페이지가 있으면 로그를 백업하지 못할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eede2-137">Any offline page can prevent backing up the log.</span></span> <span data-ttu-id="eede2-138">이 경우 가장 최근의 백업으로 복원하는 것보다 데이터가 적게 손실될 수 있으므로 DBCC REPAIR를 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="eede2-138">In this cases, consider using DBCC REPAIR, because this might cause less data loss than restoring to the most recent backup.</span></span>  
  
    -   <span data-ttu-id="eede2-139">대량 로그 데이터베이스의 로그 백업에서 잘못된 페이지가 나타나면 WITH CONTINUE_AFTER_ERROR가 지정되지 않는 경우 로그 백업은 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="eede2-139">If a log backup of a bulk-logged database encounters a bad page, it fails unless WITH CONTINUE_AFTER_ERROR is specified.</span></span>  
  
    -   <span data-ttu-id="eede2-140">일반적으로 페이지 복원은 대량 로그 복구에서 작동하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eede2-140">Page restore generally does not work with bulk-logged recovery.</span></span>  
  
         <span data-ttu-id="eede2-141">페이지 복원을 수행하는 최선의 구현 방법은 데이터베이스를 전체 복구 모델로 설정하고 로그 백업을 시도하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="eede2-141">A best practice for performing page restore is to set the database to the full recovery model, and try a log backup.</span></span> <span data-ttu-id="eede2-142">로그 백업이 성공하면 페이지 복원을 계속 진행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eede2-142">If the log backup works, you can continue with the page restore.</span></span> <span data-ttu-id="eede2-143">로그 백업이 실패하면 이전 로그 백업 이후의 작업을 잃게 되거나 REPAIR_ALLOW_DATA_LOSS 옵션을 사용하여 DBCC를 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="eede2-143">If the log backup fails, you either have to lose work since the previous log backup or you have to try running DBCC must be run with the REPAIR_ALLOW_DATA_LOSS option.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="eede2-144">권장 사항</span><span class="sxs-lookup"><span data-stu-id="eede2-144">Recommendations</span></span>  
  
-   <span data-ttu-id="eede2-145">페이지 복원 시나리오:</span><span class="sxs-lookup"><span data-stu-id="eede2-145">Page restore scenarios:</span></span>  
  
     <span data-ttu-id="eede2-146">오프라인 페이지 복원</span><span class="sxs-lookup"><span data-stu-id="eede2-146">Offline page restore</span></span>  
     <span data-ttu-id="eede2-147">모든 버전의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서는 데이터베이스가 오프라인 상태일 때에도 페이지를 복원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eede2-147">All editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] support restoring pages when the database is offline.</span></span> <span data-ttu-id="eede2-148">오프라인 페이지 복원에서 손상된 페이지가 복원되는 동안 데이터베이스는 오프라인 상태가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="eede2-148">In an offline page restore, the database is offline while damaged pages are restored.</span></span> <span data-ttu-id="eede2-149">복원 시퀀스의 마지막에 데이터베이스는 온라인 상태가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="eede2-149">At the end of the restore sequence, the database comes online.</span></span>  
  
     <span data-ttu-id="eede2-150">온라인 페이지 복원</span><span class="sxs-lookup"><span data-stu-id="eede2-150">Online page restore</span></span>  
     [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="eede2-151">Enterprise Edition에서는 온라인 페이지 복원을 지원하며, 데이터베이스가 현재 오프라인 상태인 경우에는 오프라인 복원을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="eede2-151">Enterprise edition supports online page restores, though they use offline restore if the database is currently offline.</span></span> <span data-ttu-id="eede2-152">대부분의 경우 손상된 페이지는 페이지가 복원될 파일 그룹을 비롯한 데이터베이스가 온라인 상태로 유지되는 동안 복원될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eede2-152">In most cases, a damaged page can be restored while the database remains online, including the filegroup to which a page is being restored.</span></span> <span data-ttu-id="eede2-153">주 파일 그룹이 온라인 상태이면 하나 이상의 보조 파일 그룹이 오프라인 상태이더라도 페이지 복원은 대개 온라인 상태로 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="eede2-153">When the primary filegroup is online, even if one or more of its secondary filegroups are offline, page restores are usually performed online.</span></span> <span data-ttu-id="eede2-154">그러나 손상된 페이지를 오프라인으로 복원해야 하는 경우도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eede2-154">Occasionally, however, a damaged page can require an offline restore.</span></span> <span data-ttu-id="eede2-155">예를 들어 중요한 특정 페이지가 손상되어 데이터베이스를 시작할 수 없는 경우가 이에 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="eede2-155">For example, damage to certain critical pages might prevent the database from starting.</span></span>  
  
    > [!WARNING]  
    >  <span data-ttu-id="eede2-156">손상된 페이지에 중요한 데이터베이스 메타데이터가 저장되어 있으면 온라인 페이지 복원을 시도하는 동안 메타데이터에 필요한 업데이트가 실패할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eede2-156">If damaged pages are storing critical database metadata, required updates to metadata might fail during an online page restore attempt.</span></span> <span data-ttu-id="eede2-157">이 경우 오프라인 페이지 복원을 수행할 수 있지만 이를 위해서는 먼저 RESTORE WITH NORECOVERY로 트랜잭션 로그를 백업하여 [비상 로그 백업](tail-log-backups-sql-server.md) 을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="eede2-157">In this case, you can perform an offline page restore, but first you must create a [tail log backup](tail-log-backups-sql-server.md) (by backing up the transaction log using RESTORE WITH NORECOVERY).</span></span>  
  
-   <span data-ttu-id="eede2-158">페이지 복원은 페이지 체크섬을 포함하여 향상된 페이지 수준 오류 보고와 추적을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="eede2-158">Page restore takes advantage of the improved page-level error reporting (including page checksums) and tracking.</span></span> <span data-ttu-id="eede2-159">페이지가 체크섬이나 조각난 쓰기에 의해 손상된 것으로 확인될 경우 이러한 *손상된 페이지*는 페이지 복원 작업을 통해 복원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eede2-159">Pages that are detected as corrupted by check-summing or a torn write, *damaged pages*, can be restored by a page restore operation.</span></span> <span data-ttu-id="eede2-160">이때 명시적으로 지정한 페이지만 복원됩니다.</span><span class="sxs-lookup"><span data-stu-id="eede2-160">Only explicitly specified pages are restored.</span></span> <span data-ttu-id="eede2-161">지정한 각 페이지는 지정한 데이터 백업의 해당 페이지 복사본으로 대체됩니다.</span><span class="sxs-lookup"><span data-stu-id="eede2-161">Each specified page is replaced by the copy of that page from the specified data backup.</span></span>  
  
     <span data-ttu-id="eede2-162">후속 로그 백업을 복원하는 경우 복구할 페이지가 하나 이상 포함된 데이터베이스 파일에만 백업이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="eede2-162">When you restore the subsequent log backups, they are applied only to database files that contain at least one page that is being recovered.</span></span> <span data-ttu-id="eede2-163">해당 페이지를 포함하는 파일 그룹을 현재 로그 파일로 가져오려면 손상되지 않은 로그 백업 체인을 마지막 전체 복원 또는 차등 복원에 적용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="eede2-163">An unbroken chain of log backups must be applied to the last full or differential restore to bring the filegroup that contains the page forward to the current log file.</span></span> <span data-ttu-id="eede2-164">파일 복원의 경우와 같이 롤포워드 세트는 단일 로그 다시 실행 과정을 사용하여 진행됩니다.</span><span class="sxs-lookup"><span data-stu-id="eede2-164">As in a file restore, the roll forward set is advanced with a single log redo pass.</span></span> <span data-ttu-id="eede2-165">페이지 복원이 성공하기 위해서는 복원된 페이지가 데이터베이스와 동일한 상태로 복구되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="eede2-165">For a page restore to succeed, the restored pages must be recovered to a state consistent with the database.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="eede2-166">보안</span><span class="sxs-lookup"><span data-stu-id="eede2-166">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="eede2-167">권한</span><span class="sxs-lookup"><span data-stu-id="eede2-167">Permissions</span></span>  
 <span data-ttu-id="eede2-168">복원할 데이터베이스가 없으면 CREATE DATABASE 권한이 있어야 RESTORE를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eede2-168">If the database being restored does not exist, the user must have CREATE DATABASE permissions to be able to execute RESTORE.</span></span> <span data-ttu-id="eede2-169">데이터베이스가 있으면 RESTORE 권한은 기본적으로 **sysadmin** 및 **dbcreator** 고정 서버 역할의 멤버와 데이터베이스의 소유자(**dbo**)에 설정됩니다. FROM DATABASE_SNAPSHOT 옵션의 경우 데이터베이스가 항상 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eede2-169">If the database exists, RESTORE permissions default to members of the **sysadmin** and **dbcreator** fixed server roles and the owner (**dbo**) of the database (for the FROM DATABASE_SNAPSHOT option, the database always exists).</span></span>  
  
 <span data-ttu-id="eede2-170">멤버 자격 정보를 서버에서 항상 사용할 수 있는 역할에 RESTORE 권한이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="eede2-170">RESTORE permissions are given to roles in which membership information is always readily available to the server.</span></span> <span data-ttu-id="eede2-171">고정 데이터베이스 역할의 멤버 자격은 데이터베이스가 액세스 가능한 상태이며 손상되지 않은 경우에만 확인할 수 있는데, RESTORE 실행 시 데이터베이스가 항상 이러한 상태인 것은 아니므로 **db_owner** 고정 데이터베이스 역할의 멤버에게는 RESTORE 권한이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="eede2-171">Because fixed database role membership can be checked only when the database is accessible and undamaged, which is not always the case when RESTORE is executed, members of the **db_owner** fixed database role do not have RESTORE permissions.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="eede2-172">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="eede2-172">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="eede2-173">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]부터는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 에서 페이지 복원을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="eede2-173">Starting in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] supports page restores.</span></span>  
  
#### <a name="to-restore-pages"></a><span data-ttu-id="eede2-174">페이지를 복원하려면</span><span class="sxs-lookup"><span data-stu-id="eede2-174">To restore pages</span></span>  
  
1.  <span data-ttu-id="eede2-175">[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]의 해당 인스턴스에 연결하고 개체 탐색기에서 서버 이름을 클릭하여 서버 트리를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="eede2-175">Connect to the appropriate instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], in Object Explorer, click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="eede2-176">**데이터베이스**를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="eede2-176">Expand **Databases**.</span></span> <span data-ttu-id="eede2-177">데이터베이스에 따라 사용자 데이터베이스를 선택하거나 **시스템 데이터베이스**를 확장한 다음 시스템 데이터베이스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="eede2-177">Depending on the database, either select a user database or expand **System Databases**, and then select a system database.</span></span>  
  
3.  <span data-ttu-id="eede2-178">데이터베이스를 마우스 오른쪽 단추로 클릭하고 **태스크**, **복원**을 차례로 가리킨 다음 **페이지**를 클릭하여 **페이지 복원** 대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="eede2-178">Right-click the database, point to **Tasks**, point to **Restore**, and then click **Page**, which opens the **Restore Page** dialog box.</span></span>  
  
     <span data-ttu-id="eede2-179">**복원**</span><span class="sxs-lookup"><span data-stu-id="eede2-179">**Restore**</span></span>  
     <span data-ttu-id="eede2-180">이 섹션은 **데이터베이스 복원(일반 페이지)** 의 [복원 위치](../../integration-services/general-page-of-integration-services-designers-options.md)와 동일한 기능을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="eede2-180">This section performs the same function as that of **Restore to** on the [Restore Database (General Page)](../../integration-services/general-page-of-integration-services-designers-options.md).</span></span>  
  
     <span data-ttu-id="eede2-181">**Database**</span><span class="sxs-lookup"><span data-stu-id="eede2-181">**Database**</span></span>  
     <span data-ttu-id="eede2-182">복원할 데이터베이스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="eede2-182">Specifies the database to restore.</span></span> <span data-ttu-id="eede2-183">새 데이터베이스를 입력하거나 드롭다운 목록에서 기존 데이터베이스를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eede2-183">You can enter a new database or select an existing database from the drop-down list.</span></span> <span data-ttu-id="eede2-184">이 목록에는 시스템 데이터베이스인 **master** 및 **tempdb**를 제외한 서버의 모든 데이터베이스가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eede2-184">The list includes all databases on the server, except the system databases **master** and **tempdb**.</span></span>  
  
    > [!WARNING]  
    >  <span data-ttu-id="eede2-185">암호로 보호된 백업을 복원하려면 [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) 문을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="eede2-185">To restore a password-protected backup, you must use the [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) statement.</span></span>  
  
     <span data-ttu-id="eede2-186">**비상 로그 백업**</span><span class="sxs-lookup"><span data-stu-id="eede2-186">**Tail-Log backup**</span></span>  
     <span data-ttu-id="eede2-187">**백업 디바이스** 에서 데이터베이스에 대한 비상 로그 백업이 저장될 파일 이름을 입력하거나 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="eede2-187">Enter or select a file name in **Backup device** where there tail-log backup will be stored for the database.</span></span>  
  
     <span data-ttu-id="eede2-188">**백업 세트**</span><span class="sxs-lookup"><span data-stu-id="eede2-188">**Backup Sets**</span></span>  
     <span data-ttu-id="eede2-189">이 섹션에는 복원에 관련된 백업 세트가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="eede2-189">This section displays the backup sets involved in the restoration.</span></span>  
  
    |<span data-ttu-id="eede2-190">헤더</span><span class="sxs-lookup"><span data-stu-id="eede2-190">Header</span></span>|<span data-ttu-id="eede2-191">값</span><span class="sxs-lookup"><span data-stu-id="eede2-191">Values</span></span>|  
    |------------|------------|  
    |<span data-ttu-id="eede2-192">**이름**</span><span class="sxs-lookup"><span data-stu-id="eede2-192">**Name**</span></span>|<span data-ttu-id="eede2-193">백업 세트의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="eede2-193">The name of the backup set.</span></span>|  
    |<span data-ttu-id="eede2-194">**구성 요소**</span><span class="sxs-lookup"><span data-stu-id="eede2-194">**Component**</span></span>|<span data-ttu-id="eede2-195">백업된 구성 요소: **데이터베이스**, **파일** 또는 **\<blank>** (트랜잭션 로그의 경우)가 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eede2-195">The backed-up component: **Database**, **File**, or **\<blank>** (for transaction logs).</span></span>|  
    |<span data-ttu-id="eede2-196">**형식**</span><span class="sxs-lookup"><span data-stu-id="eede2-196">**Type**</span></span>|<span data-ttu-id="eede2-197">수행된 백업 유형: **전체**, **차등** 또는 **트랜잭션 로그**가 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eede2-197">The type of backup performed: **Full**, **Differential**, or **Transaction Log**.</span></span>|  
    |<span data-ttu-id="eede2-198">**Server**</span><span class="sxs-lookup"><span data-stu-id="eede2-198">**Server**</span></span>|<span data-ttu-id="eede2-199">백업 작업을 수행한 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 인스턴스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="eede2-199">The name of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] instance that performed the backup operation.</span></span>|  
    |<span data-ttu-id="eede2-200">**Database**</span><span class="sxs-lookup"><span data-stu-id="eede2-200">**Database**</span></span>|<span data-ttu-id="eede2-201">백업 작업과 관련된 데이터베이스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="eede2-201">The name of the database involved in the backup operation.</span></span>|  
    |<span data-ttu-id="eede2-202">**위치**</span><span class="sxs-lookup"><span data-stu-id="eede2-202">**Position**</span></span>|<span data-ttu-id="eede2-203">볼륨에 있는 백업 세트의 위치입니다.</span><span class="sxs-lookup"><span data-stu-id="eede2-203">The position of the backup set in the volume.</span></span>|  
    |<span data-ttu-id="eede2-204">**첫 번째 LSN**</span><span class="sxs-lookup"><span data-stu-id="eede2-204">**First LSN**</span></span>|<span data-ttu-id="eede2-205">백업 세트에 있는 첫 번째 트랜잭션의 LSN(로그 시퀀스 번호)입니다.</span><span class="sxs-lookup"><span data-stu-id="eede2-205">The log sequence number (LSN) of the first transaction in the backup set.</span></span> <span data-ttu-id="eede2-206">파일 백업의 경우 비워 둡니다.</span><span class="sxs-lookup"><span data-stu-id="eede2-206">Blank for file backups.</span></span>|  
    |<span data-ttu-id="eede2-207">**마지막 LSN**</span><span class="sxs-lookup"><span data-stu-id="eede2-207">**Last LSN**</span></span>|<span data-ttu-id="eede2-208">백업 세트에 있는 마지막 트랜잭션의 LSN(로그 시퀀스 번호)입니다.</span><span class="sxs-lookup"><span data-stu-id="eede2-208">The log sequence number (LSN) of the last transaction in the backup set.</span></span> <span data-ttu-id="eede2-209">파일 백업의 경우 비워 둡니다.</span><span class="sxs-lookup"><span data-stu-id="eede2-209">Blank for file backups.</span></span>|  
    |<span data-ttu-id="eede2-210">**검사점 LSN**</span><span class="sxs-lookup"><span data-stu-id="eede2-210">**Checkpoint LSN**</span></span>|<span data-ttu-id="eede2-211">백업을 만들 때 가장 최근 검사점의 로그 시퀀스 번호입니다.</span><span class="sxs-lookup"><span data-stu-id="eede2-211">The log sequence number (LSN) of the most recent checkpoint at the time the backup was created.</span></span>|  
    |<span data-ttu-id="eede2-212">**전체 LSN**</span><span class="sxs-lookup"><span data-stu-id="eede2-212">**Full LSN**</span></span>|<span data-ttu-id="eede2-213">가장 최근에 수행한 전체 데이터베이스 백업의 LSN(로그 시퀀스 번호)입니다.</span><span class="sxs-lookup"><span data-stu-id="eede2-213">The log sequence number (LSN) of the most recent full database backup.</span></span>|  
    |<span data-ttu-id="eede2-214">**Start Date**</span><span class="sxs-lookup"><span data-stu-id="eede2-214">**Start Date**</span></span>|<span data-ttu-id="eede2-215">클라이언트의 국가별 설정으로 표시되는 백업 작업 시작 날짜 및 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="eede2-215">The date and time when the backup operation began, presented in the regional setting of the client.</span></span>|  
    |<span data-ttu-id="eede2-216">**완료 날짜**</span><span class="sxs-lookup"><span data-stu-id="eede2-216">**Finish Date**</span></span>|<span data-ttu-id="eede2-217">클라이언트의 국가별 설정으로 표시되는 백업 작업 완료 날짜 및 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="eede2-217">The date and time when the backup operation finished, presented in the regional setting of the client.</span></span>|  
    |<span data-ttu-id="eede2-218">**크기**</span><span class="sxs-lookup"><span data-stu-id="eede2-218">**Size**</span></span>|<span data-ttu-id="eede2-219">백업 세트의 크기를 바이트 단위로 표시한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="eede2-219">The size of the backup set in bytes.</span></span>|  
    |<span data-ttu-id="eede2-220">**사용자 이름**</span><span class="sxs-lookup"><span data-stu-id="eede2-220">**User Name**</span></span>|<span data-ttu-id="eede2-221">백업 작업을 수행한 사용자의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="eede2-221">The name of the user who performed the backup operation.</span></span>|  
    |<span data-ttu-id="eede2-222">**만료**</span><span class="sxs-lookup"><span data-stu-id="eede2-222">**Expiration**</span></span>|<span data-ttu-id="eede2-223">백업 세트가 만료되는 날짜 및 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="eede2-223">The date and time the backup set expires.</span></span>|  
  
     <span data-ttu-id="eede2-224">페이지 복원 작업을 수행하는 데 필요한 백업 파일의 무결성을 확인하려면 **확인** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="eede2-224">Click **Verify** to check the integrity of the backup files needed to perform the page restore operation.</span></span>  
  
4.  <span data-ttu-id="eede2-225">손상된 페이지를 확인하려면 **데이터베이스** 상자에서 올바른 데이터베이스를 선택한 상태에서 **데이터베이스 페이지 확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="eede2-225">To identify corrupted pages, with the correct database selected in the **Database** box, click **Check Database Pages**.</span></span> <span data-ttu-id="eede2-226">이 작업을 실행하는 데는 오랜 시간이 소요됩니다.</span><span class="sxs-lookup"><span data-stu-id="eede2-226">This is a long running operation.</span></span>  
  
    > [!WARNING]  
    >  <span data-ttu-id="eede2-227">손상되지 않은 특정 페이지를 복원하려면 **추가** 를 클릭하고 복원할 페이지의 **파일 ID** 와 **페이지 ID** 를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="eede2-227">To restore specific pages that are not corrupted, click **Add** and enter the **File ID** and **Page ID** of the pages to be restored.</span></span>  
  
5.  <span data-ttu-id="eede2-228">복원할 페이지를 확인하는 데는 페이지 표가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="eede2-228">The pages grid is used to identify the pages to be restored.</span></span> <span data-ttu-id="eede2-229">처음에는 이 표가 [suspect_pages](/sql/relational-databases/system-tables/suspect-pages-transact-sql) 시스템 테이블의 내용으로 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="eede2-229">Initially, this grid is populated from the [suspect_pages](/sql/relational-databases/system-tables/suspect-pages-transact-sql) system table.</span></span> <span data-ttu-id="eede2-230">표에서 페이지를 추가하거나 제거하려면 **추가** 또는 **제거**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="eede2-230">To add or remove pages from the grid, click **Add** or **Remove**.</span></span> <span data-ttu-id="eede2-231">자세한 내용은 [suspect_pages 테이블 관리&#40;SQL Server&#41;](manage-the-suspect-pages-table-sql-server.md)에서 페이지를 복원하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="eede2-231">For more information, see [Manage the suspect_pages Table &#40;SQL Server&#41;](manage-the-suspect-pages-table-sql-server.md).</span></span>  
  
6.  <span data-ttu-id="eede2-232">**백업 세트** 표에는 기본 복원 계획의 백업 세트가 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="eede2-232">The **Backup sets** grid lists the backup sets in the default restore plan.</span></span> <span data-ttu-id="eede2-233">필요할 경우 **확인** 을 클릭하여 복원은 수행하지 않고 백업을 읽을 수 있는지와 백업 세트가 완전한지만 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eede2-233">Optionally, click **Verify** to verify that the backups are readable and that the backup sets are complete, without restoring them.</span></span> <span data-ttu-id="eede2-234">자세한 내용은 [RESTORE VERIFYONLY&#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-verifyonly-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="eede2-234">For more information, see [RESTORE VERIFYONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-verifyonly-transact-sql).</span></span>  
  
     <span data-ttu-id="eede2-235">**페이지**</span><span class="sxs-lookup"><span data-stu-id="eede2-235">**Pages**</span></span>  
  
7.  <span data-ttu-id="eede2-236">페이지 표에 나열된 페이지를 복원하려면 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="eede2-236">To restore the pages listed in the pages grid, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="eede2-237">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="eede2-237">Using Transact-SQL</span></span>  
 <span data-ttu-id="eede2-238">RESTORE DATABASE 문에서 페이지를 지정하려면 페이지를 포함하는 파일의 파일 ID와 해당 페이지의 페이지 ID가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="eede2-238">To specify a page in a RESTORE DATABASE statement, you need the file ID of the file containing the page and the page ID of the page.</span></span> <span data-ttu-id="eede2-239">필요한 구문은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="eede2-239">The required syntax is as follows:</span></span>  
  
 `RESTORE DATABASE <database_name>`  
  
 `PAGE = '<file: page> [ ,... n ] ' [ ,... n ]`  
  
 `FROM <backup_device> [ ,... n ]`  
  
 `WITH NORECOVERY`  
  
 <span data-ttu-id="eede2-240">PAGE 옵션의 매개 변수에 대한 자세한 내용은 [RESTORE 인수&#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-arguments-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="eede2-240">For more information about the parameters of the PAGE option, see [RESTORE Arguments &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-arguments-transact-sql).</span></span> <span data-ttu-id="eede2-241">RESTORE DATABASE 구문에 대한 자세한 내용은 [RESTORE&#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="eede2-241">For more information about the RESTORE DATABASE syntax, see [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql).</span></span>  
  
#### <a name="to-restore-pages"></a><span data-ttu-id="eede2-242">페이지를 복원하려면</span><span class="sxs-lookup"><span data-stu-id="eede2-242">To restore pages</span></span>  
  
1.  <span data-ttu-id="eede2-243">복원하려는 손상된 페이지의 페이지 ID를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="eede2-243">Obtain the page IDs of the damaged pages to be restored.</span></span> <span data-ttu-id="eede2-244">체크섬 또는 조각난 쓰기 오류가 페이지 ID를 반환하고 페이지를 지정하는 데 필요한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="eede2-244">A checksum or torn write error returns page ID, providing the information required for specifying the pages.</span></span> <span data-ttu-id="eede2-245">손상된 페이지의 페이지 ID를 조회하려면 다음 원본 중 하나를 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="eede2-245">To look up page ID of a damaged page, use any of the following sources.</span></span>  
  
    |<span data-ttu-id="eede2-246">페이지 ID의 원본</span><span class="sxs-lookup"><span data-stu-id="eede2-246">Source of page ID</span></span>|<span data-ttu-id="eede2-247">항목</span><span class="sxs-lookup"><span data-stu-id="eede2-247">Topic</span></span>|  
    |-----------------------|-----------|  
    |<span data-ttu-id="eede2-248">**msdb..suspect_pages**</span><span class="sxs-lookup"><span data-stu-id="eede2-248">**msdb..suspect_pages**</span></span>|[<span data-ttu-id="eede2-249">suspect_pages 테이블 관리&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="eede2-249">Manage the suspect_pages Table &#40;SQL Server&#41;</span></span>](manage-the-suspect-pages-table-sql-server.md)|  
    |<span data-ttu-id="eede2-250">오류 로그</span><span class="sxs-lookup"><span data-stu-id="eede2-250">Error log</span></span>|[<span data-ttu-id="eede2-251">SQL Server 오류 로그 보기&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="eede2-251">View the SQL Server Error Log &#40;SQL Server Management Studio&#41;</span></span>](../../ssms/sql-server-management-studio-ssms.md)|  
    |<span data-ttu-id="eede2-252">이벤트 추적</span><span class="sxs-lookup"><span data-stu-id="eede2-252">Event traces</span></span>|[<span data-ttu-id="eede2-253">이벤트 모니터링 및 응답</span><span class="sxs-lookup"><span data-stu-id="eede2-253">Monitor and Respond to Events</span></span>](../../ssms/agent/monitor-and-respond-to-events.md)|  
    |<span data-ttu-id="eede2-254">DBCC</span><span class="sxs-lookup"><span data-stu-id="eede2-254">DBCC</span></span>|[<span data-ttu-id="eede2-255">DBCC&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="eede2-255">DBCC &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/database-console-commands/dbcc-transact-sql)|  
    |<span data-ttu-id="eede2-256">WMI 공급자</span><span class="sxs-lookup"><span data-stu-id="eede2-256">WMI provider</span></span>|[<span data-ttu-id="eede2-257">서버 이벤트용 WMI 공급자 개념</span><span class="sxs-lookup"><span data-stu-id="eede2-257">WMI Provider for Server Events Concepts</span></span>](../wmi-provider-server-events/wmi-provider-for-server-events-concepts.md)|  
  
2.  <span data-ttu-id="eede2-258">페이지가 들어 있는 전체 데이터베이스, 파일 또는 파일 그룹 백업으로 페이지 복원을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="eede2-258">Start a page restore with a full database, file, or filegroup backup that contains the page.</span></span> <span data-ttu-id="eede2-259">RESTORE DATABASE 문에서 PAGE 절을 사용하여 복원할 모든 페이지의 페이지 ID를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="eede2-259">In the RESTORE DATABASE statement, use the PAGE clause to list the page IDs of all of the pages to be restored.</span></span>  
  
3.  <span data-ttu-id="eede2-260">가장 최근의 차등 백업을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="eede2-260">Apply the most recent differentials .</span></span>  
  
4.  <span data-ttu-id="eede2-261">후속 로그 백업을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="eede2-261">Apply the subsequent log backups.</span></span>  
  
5.  <span data-ttu-id="eede2-262">복원된 페이지의 최종 LSN, 즉 마지막으로 복원된 페이지가 오프라인 상태로 된 시점을 포함하는 데이터베이스의 새 로그 백업을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="eede2-262">Create a new log backup of the database that includes the final LSN of the restored pages, that is, the point at which the last restored page is taken offline.</span></span> <span data-ttu-id="eede2-263">시퀀스에서 첫 번째 복원의 일부로 설정되는 최종 LSN은 다시 실행 대상 LSN입니다.</span><span class="sxs-lookup"><span data-stu-id="eede2-263">The final LSN, which is set as part of the first restore in the sequence, is the redo target LSN.</span></span> <span data-ttu-id="eede2-264">이 페이지를 포함하는 파일의 온라인 롤포워드는 다시 실행 대상 LSN에서 중지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eede2-264">Online roll forward of the file containing the page is able to stop at the redo target LSN.</span></span> <span data-ttu-id="eede2-265">파일의 현재 다시 실행 대상 LSN을 알아보려면 **sys.master_files**의 **redo_target_lsn** 열을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="eede2-265">To learn the current redo target LSN of a file, see the **redo_target_lsn** column of **sys.master_files**.</span></span> <span data-ttu-id="eede2-266">자세한 내용은 [sys.master_files&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-master-files-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="eede2-266">For more information, see [sys.master_files &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-master-files-transact-sql).</span></span>  
  
6.  <span data-ttu-id="eede2-267">새 로그 백업을 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="eede2-267">Restore the new log backup.</span></span> <span data-ttu-id="eede2-268">새로운 이 로그 백업을 적용하면 페이지 복원이 완료되며 페이지를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eede2-268">After this new log backup is applied, the page restore is completed and the pages are now usable.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="eede2-269">이 시퀀스는 파일 복원 시퀀스와 유사하며</span><span class="sxs-lookup"><span data-stu-id="eede2-269">This sequence is analogous to a file restore sequence.</span></span> <span data-ttu-id="eede2-270">동일한 시퀀스의 일부로 페이지 복원과 파일 복원을 모두 수행할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eede2-270">In fact, page restore and file restores can both be performed as part of the same sequence.</span></span>  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="eede2-271">예(Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="eede2-271">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="eede2-272">다음 예에서는 `B` 로 `NORECOVERY`파일의 손상된 4페이지를 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="eede2-272">The following example restores four damaged pages of file `B` with `NORECOVERY`.</span></span> <span data-ttu-id="eede2-273">그런 다음 두 개의 로그 백업에 `NORECOVERY`를 적용하고 `RECOVERY`로 복원되는 비상 로그 백업을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="eede2-273">Next, two log backups are applied with `NORECOVERY`, followed with the tail-log backup, which is restored with `RECOVERY`.</span></span> <span data-ttu-id="eede2-274">이 예에서는 온라인 복원을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="eede2-274">This example performs an online restore.</span></span> <span data-ttu-id="eede2-275">이 예에서 `B` 파일의 파일 ID는 `1`이고 손상된 페이지의 페이지 ID는 각각 `57`, `202`, `916`및 `1016`입니다.</span><span class="sxs-lookup"><span data-stu-id="eede2-275">In the example, the file ID of file `B` is `1`, and the page IDs of the damaged pages are `57`, `202`, `916`, and `1016`.</span></span>  
  
```sql  
RESTORE DATABASE <database> PAGE='1:57, 1:202, 1:916, 1:1016'  
   FROM <file_backup_of_file_B>   
   WITH NORECOVERY;  
RESTORE LOG <database> FROM <log_backup>   
   WITH NORECOVERY;  
RESTORE LOG <database> FROM <log_backup>   
   WITH NORECOVERY;   
BACKUP LOG <database> TO <new_log_backup>;   
RESTORE LOG <database> FROM <new_log_backup> WITH RECOVERY;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="eede2-276">참고 항목</span><span class="sxs-lookup"><span data-stu-id="eede2-276">See Also</span></span>  
 <span data-ttu-id="eede2-277">[RESTORE&#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="eede2-277">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 <span data-ttu-id="eede2-278">[트랜잭션 로그 백업 적용&#40;SQL Server&#41;](transaction-log-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="eede2-278">[Apply Transaction Log Backups &#40;SQL Server&#41;](transaction-log-backups-sql-server.md) </span></span>  
 <span data-ttu-id="eede2-279">[suspect_pages 테이블 관리&#40;SQL Server&#41;](manage-the-suspect-pages-table-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="eede2-279">[Manage the suspect_pages Table &#40;SQL Server&#41;](manage-the-suspect-pages-table-sql-server.md) </span></span>  
 [<span data-ttu-id="eede2-280">SQL Server 데이터베이스 백업 및 복원</span><span class="sxs-lookup"><span data-stu-id="eede2-280">Back Up and Restore of SQL Server Databases</span></span>](back-up-and-restore-of-sql-server-databases.md)  
  
  
