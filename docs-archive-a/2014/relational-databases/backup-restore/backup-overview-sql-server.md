---
title: 백업 개요(SQL Server) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- tables [SQL Server], backing up data
- backups [SQL Server]
- database backups [SQL Server]
- backup types [SQL Server]
- data backups [SQL Server]
- backing up tables [SQL Server]
- database restores [SQL Server], backups
- backing up [SQL Server], about backing up
- restoring [SQL Server], backup types
- backups [SQL Server], about
- backups [SQL Server], table-level backups unsupported
ms.assetid: 09a6e0c2-d8fd-453f-9aac-4ff24a97dc1f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 60fbd0341c4e29c6f98cc4d5fe5a2cfabc9b703f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661195"
---
# <a name="backup-overview-sql-server"></a><span data-ttu-id="30515-102">Backup Overview (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="30515-102">Backup Overview (SQL Server)</span></span>
  <span data-ttu-id="30515-103">이 항목에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 백업 구성 요소에 대해 소개합니다.</span><span class="sxs-lookup"><span data-stu-id="30515-103">This topic introduces the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backup component.</span></span> <span data-ttu-id="30515-104">데이터를 보호하려면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스를 백업해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="30515-104">Backing up your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database is essential for protecting your data.</span></span> <span data-ttu-id="30515-105">여기서는 백업 유형과 백업 제한 사항에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="30515-105">This discussion covers backup types, and backup restrictions.</span></span> <span data-ttu-id="30515-106">또한 이 항목에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 백업 디바이스와 백업 미디어를 소개합니다.</span><span class="sxs-lookup"><span data-stu-id="30515-106">The topic also introduces [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backup devices and backup media.</span></span>  
  
 <span data-ttu-id="30515-107">**항목 내용:**</span><span class="sxs-lookup"><span data-stu-id="30515-107">**In this Topic:**</span></span>  
  
-   [<span data-ttu-id="30515-108">구성 요소 및 개념</span><span class="sxs-lookup"><span data-stu-id="30515-108">Components and Concepts</span></span>](#TermsAndDefinitions)  
  
-   [<span data-ttu-id="30515-109">백업 압축</span><span class="sxs-lookup"><span data-stu-id="30515-109">Backup Compression</span></span>](#BackupCompression)  
  
-   [<span data-ttu-id="30515-110">SQL Server에서의 백업 작업에 대한 제한 사항</span><span class="sxs-lookup"><span data-stu-id="30515-110">Restrictions on Backup Operations in SQL Server</span></span>](#Restrictions)  
  
-   [<span data-ttu-id="30515-111">관련 작업</span><span class="sxs-lookup"><span data-stu-id="30515-111">Related Tasks</span></span>](#RelatedTasks)  
  
##  <a name="components-and-concepts"></a><a name="TermsAndDefinitions"></a> <span data-ttu-id="30515-112">구성 요소 및 개념</span><span class="sxs-lookup"><span data-stu-id="30515-112">Components and Concepts</span></span>  
 <span data-ttu-id="30515-113">백업[동사]</span><span class="sxs-lookup"><span data-stu-id="30515-113">back up [verb]</span></span>  
 <span data-ttu-id="30515-114">데이터 또는 로그 레코드를 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스 또는 해당 트랜잭션 로그에서 백업 디바이스(예: 디스크)로 복사하여 데이터 백업 또는 로그 백업을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30515-114">Copies the data or log records from a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database or its transaction log to a backup device, such as a disk, to create a data backup or log backup.</span></span>  
  
 <span data-ttu-id="30515-115">백업[명사]</span><span class="sxs-lookup"><span data-stu-id="30515-115">backup [noun]</span></span>  
 <span data-ttu-id="30515-116">오류가 발생한 이후에 데이터를 복원 및 복구하는 데 사용할 수 있는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터 복사본입니다.</span><span class="sxs-lookup"><span data-stu-id="30515-116">A copy of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data that can be used to restore and recover the data after a failure.</span></span> <span data-ttu-id="30515-117">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터 백업은 데이터베이스나 데이터베이스에 있는 하나 이상의 파일 또는 파일 그룹 수준에서 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="30515-117">A backup of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data is created at the level of a database or one or more of its files or filegroups.</span></span> <span data-ttu-id="30515-118">테이블 수준 백업은 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="30515-118">Table-level backups cannot be created.</span></span> <span data-ttu-id="30515-119">데이터 백업뿐만 아니라 전체 복구 모델에서는 트랜잭션 로그 백업도 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="30515-119">In addition to data backups, the full recovery model requires creating backups of the transaction log.</span></span>  
  
 [<span data-ttu-id="30515-120">복구 모델</span><span class="sxs-lookup"><span data-stu-id="30515-120">recovery model</span></span>](recovery-models-sql-server.md)  
 <span data-ttu-id="30515-121">데이터베이스에서 트랜잭션 로그 유지 관리를 제어하는 데이터베이스 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="30515-121">A database property that controls transaction log maintenance on a database.</span></span> <span data-ttu-id="30515-122">사용할 수 있는 복구 모델은 3가지로 단순, 전체 및 대량 로그 복구 모델입니다.</span><span class="sxs-lookup"><span data-stu-id="30515-122">Three recovery models exist: simple, full, and bulk-logged.</span></span> <span data-ttu-id="30515-123">데이터베이스의 복구 모델에 따라 백업 및 복원 요구 사항이 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="30515-123">The recovery model of database determines its backup and restore requirements.</span></span>  
  
 [<span data-ttu-id="30515-124">복원(restore)</span><span class="sxs-lookup"><span data-stu-id="30515-124">restore</span></span>](restore-and-recovery-overview-sql-server.md)  
 <span data-ttu-id="30515-125">지정된 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 백업에서 지정된 데이터베이스로 모든 데이터 및 로그 페이지를 복사하고 기록된 변경 사항을 적용하여 데이터를 최신 상태로 전환함으로써 백업에 기록된 모든 트랜잭션을 롤포워드하는 다단계 프로세스입니다.</span><span class="sxs-lookup"><span data-stu-id="30515-125">A multi-phase process that copies all the data and log pages from a specified [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backup to a specified database, and then rolls forward all the transactions that are logged in the backup by applying logged changes to bring the data forward in time.</span></span>  
  
 <span data-ttu-id="30515-126">**백업 유형**</span><span class="sxs-lookup"><span data-stu-id="30515-126">**Types of Backups**</span></span>  
  
 [<span data-ttu-id="30515-127">복사 전용 백업</span><span class="sxs-lookup"><span data-stu-id="30515-127">copy-only backup</span></span>](copy-only-backups-sql-server.md)  
 <span data-ttu-id="30515-128">정기적인 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 백업 시퀀스와 독립적인 특수 백업입니다.</span><span class="sxs-lookup"><span data-stu-id="30515-128">A special-use backup that is independent of the regular sequence of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backups.</span></span>  
  
 <span data-ttu-id="30515-129">데이터 백업(data backup)</span><span class="sxs-lookup"><span data-stu-id="30515-129">data backup</span></span>  
 <span data-ttu-id="30515-130">전체 데이터베이스(데이터베이스 백업), 부분 데이터베이스(부분 백업) 또는 데이터 파일 집합이나 파일 그룹(파일 백업)의 데이터 백업입니다.</span><span class="sxs-lookup"><span data-stu-id="30515-130">A backup of data in a complete database (a database backup), a partial database (a partial backup), or a set of data files or filegroups (a file backup).</span></span>  
  
 [<span data-ttu-id="30515-131">데이터베이스 백업(database backup)</span><span class="sxs-lookup"><span data-stu-id="30515-131">database backup</span></span>](full-database-backups-sql-server.md)  
 <span data-ttu-id="30515-132">데이터베이스 백업입니다.</span><span class="sxs-lookup"><span data-stu-id="30515-132">A backup of a database.</span></span> <span data-ttu-id="30515-133">전체 데이터베이스 백업은 백업이 완료된 시점의 전체 데이터베이스를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="30515-133">Full database backups represent the whole database at the time the backup finished.</span></span> <span data-ttu-id="30515-134">차등 데이터베이스 백업은 가장 최근의 전체 데이터베이스 백업 이후에 데이터베이스에 수행된 변경 내용만 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="30515-134">Differential database backups contain only changes made to the database since its most recent full database backup.</span></span>  
  
 [<span data-ttu-id="30515-135">차등 백업(differential backup)</span><span class="sxs-lookup"><span data-stu-id="30515-135">differential backup</span></span>](full-database-backups-sql-server.md)  
 <span data-ttu-id="30515-136">전체 또는 부분 데이터베이스, 데이터 파일 집합 또는 파일 그룹( *차등 기반*)에 대한 최신 전체 백업을 기반으로 하고, 해당 차등 기준 이후에 변경된 데이터 범위만 포함하는 데이터 백업입니다.</span><span class="sxs-lookup"><span data-stu-id="30515-136">A data backup that is based on the latest full backup of a complete or partial database or a set of data files or filegroups (the *differential base*) and that contains only the data extents that have changed since the differential base.</span></span>  
  
 <span data-ttu-id="30515-137">차등 부분 백업은 차등 기반이라고 하는 이전 부분 백업 이후에 파일 그룹에서 변경된 데이터 익스텐트만 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="30515-137">A differential partial backup records only the data extents that have changed in the filegroups since the previous partial backup, known as the base for the differential.</span></span>  
  
 <span data-ttu-id="30515-138">전체 백업(full backup)</span><span class="sxs-lookup"><span data-stu-id="30515-138">full backup</span></span>  
 <span data-ttu-id="30515-139">특정 데이터베이스나 파일 그룹 또는 파일 집합에 있는 모든 데이터와 그러한 데이터를 복구할 수 있을 만큼의 로그를 포함하는 데이터 백업입니다.</span><span class="sxs-lookup"><span data-stu-id="30515-139">A data backup that contains all the data in a specific database or set of filegroups or files, and also enough log to allow for recovering that data.</span></span>  
  
 [<span data-ttu-id="30515-140">로그 백업(log backup)</span><span class="sxs-lookup"><span data-stu-id="30515-140">log backup</span></span>](transaction-log-backups-sql-server.md)  
 <span data-ttu-id="30515-141">이전 로그 백업에서 백업되지 않은 모든 로그 레코드를 포함하는 트랜잭션 로그 백업입니다.</span><span class="sxs-lookup"><span data-stu-id="30515-141">A backup of transaction logs that includes all log records that were not backed up in a previous log backup.</span></span> <span data-ttu-id="30515-142">(전체 복구 모델)</span><span class="sxs-lookup"><span data-stu-id="30515-142">(full recovery model)</span></span>  
  
 [<span data-ttu-id="30515-143">파일 백업(file backup)</span><span class="sxs-lookup"><span data-stu-id="30515-143">file backup</span></span>](full-file-backups-sql-server.md)  
 <span data-ttu-id="30515-144">하나 이상의 데이터베이스 파일 또는 파일 그룹에 대한 백업입니다.</span><span class="sxs-lookup"><span data-stu-id="30515-144">A backup of one or more database files or filegroups.</span></span>  
  
 [<span data-ttu-id="30515-145">부분 백업(partial backup)</span><span class="sxs-lookup"><span data-stu-id="30515-145">partial backup</span></span>](partial-backups-sql-server.md)  
 <span data-ttu-id="30515-146">주 파일 그룹, 모든 읽기/쓰기 파일 그룹 및 필요에 따라 지정된 읽기 전용 파일을 비롯하여 데이터베이스에 있는 일부 파일 그룹의 데이터만 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="30515-146">Contains data from only some of the filegroups in a database, including the data in the primary filegroup, every read/write filegroup, and any optionally-specified read-only files.</span></span>  
  
 <span data-ttu-id="30515-147">**백업 미디어 용어 및 정의**</span><span class="sxs-lookup"><span data-stu-id="30515-147">**Backup Media Terms and Definitions**</span></span>  
  
 [<span data-ttu-id="30515-148">백업 디바이스(backup device)</span><span class="sxs-lookup"><span data-stu-id="30515-148">backup device</span></span>](backup-devices-sql-server.md)  
 <span data-ttu-id="30515-149">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 백업이 기록되는 대상이자 백업을 복원하는 원본이 되는 디스크 또는 테이프 디바이스입니다.</span><span class="sxs-lookup"><span data-stu-id="30515-149">A disk or tape device to which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backups are written and from which they can be restored.</span></span> <span data-ttu-id="30515-150">SQL Server 백업은 Azure Blob Storage 서비스에 기록할 수도 있으며 백업 파일의 대상과 이름을 지정하기 위해 **URL** 형식이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="30515-150">SQL Server backups can also be written to an Azure Blob storage service, and **URL** format is used to specify the destination and the name of the backup file..</span></span> <span data-ttu-id="30515-151">자세한 내용은 [Azure Blob Storage 서비스로 SQL Server 백업 및 복원](sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="30515-151">For more information, see [SQL Server Backup and Restore with Azure Blob Storage Service](sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md).</span></span>  
  
 [<span data-ttu-id="30515-152">백업 미디어</span><span class="sxs-lookup"><span data-stu-id="30515-152">backup media</span></span>](media-sets-media-families-and-backup-sets-sql-server.md)  
 <span data-ttu-id="30515-153">하나 이상의 백업이 기록된 하나 이상의 테이프 또는 디스크 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="30515-153">One or more tapes or disk files to which one or more backup have been written.</span></span>  
  
 [<span data-ttu-id="30515-154">백업 세트(backup set)</span><span class="sxs-lookup"><span data-stu-id="30515-154">backup set</span></span>](media-sets-media-families-and-backup-sets-sql-server.md)  
 <span data-ttu-id="30515-155">백업 작업이 성공할 때 미디어 세트에 추가되는 백업 내용입니다.</span><span class="sxs-lookup"><span data-stu-id="30515-155">The backup content that is added to a media set by a successful backup operation.</span></span>  
  
 [<span data-ttu-id="30515-156">미디어 패밀리(media family)</span><span class="sxs-lookup"><span data-stu-id="30515-156">media family</span></span>](media-sets-media-families-and-backup-sets-sql-server.md)  
 <span data-ttu-id="30515-157">미디어 세트의 미러되지 않은 단일 디바이스나 일련의 미러된 디바이스에 생성된 백업입니다.</span><span class="sxs-lookup"><span data-stu-id="30515-157">Backups created on a single nonmirrored device or a set of mirrored devices in a media set</span></span>  
  
 [<span data-ttu-id="30515-158">미디어 세트(media set)</span><span class="sxs-lookup"><span data-stu-id="30515-158">media set</span></span>](media-sets-media-families-and-backup-sets-sql-server.md)  
 <span data-ttu-id="30515-159">하나 이상의 백업 작업에서 고정된 유형과 개수의 백업 디바이스를 사용하여 기록한 백업 미디어, 테이프 또는 디스크 파일의 모음입니다.</span><span class="sxs-lookup"><span data-stu-id="30515-159">An ordered collection of backup media, tapes or disk files, to which one or more backup operations have written using a fixed type and number of backup devices.</span></span>  
  
 [<span data-ttu-id="30515-160">미러링된 미디어 세트(mirrored media set)</span><span class="sxs-lookup"><span data-stu-id="30515-160">mirrored media set</span></span>](mirrored-backup-media-sets-sql-server.md)  
 <span data-ttu-id="30515-161">미디어 세트의 여러 복사본(미러)입니다.</span><span class="sxs-lookup"><span data-stu-id="30515-161">Multiple copies (mirrors) of a media set.</span></span>  
  
##  <a name="backup-compression"></a><a name="BackupCompression"></a><span data-ttu-id="30515-162">백업 압축</span><span class="sxs-lookup"><span data-stu-id="30515-162">Backup Compression</span></span>  
 [!INCLUDE[ssEnterpriseEd10](../../includes/ssenterpriseed10-md.md)] <span data-ttu-id="30515-163">이상 버전에서 압축 백업을 지원하며, [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 이상 버전에서 압축된 백업을 복원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30515-163">and later versions support compressing backups, and [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] and later versions can restore a compressed backup.</span></span> <span data-ttu-id="30515-164">자세한 내용은 [백업 압축&#40;SQL Server&#41;](backup-compression-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="30515-164">For more information, see [Backup Compression &#40;SQL Server&#41;](backup-compression-sql-server.md).</span></span>  
  
##  <a name="restrictions-on-backup-operations-in-sql-server"></a><a name="Restrictions"></a><span data-ttu-id="30515-165">SQL Server의 백업 작업에 대 한 제한 사항</span><span class="sxs-lookup"><span data-stu-id="30515-165">Restrictions on Backup Operations in SQL Server</span></span>  
 <span data-ttu-id="30515-166">백업은 데이터베이스가 온라인 상태이며 사용 중인 경우 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30515-166">Backup can occur while the database is online and being used.</span></span> <span data-ttu-id="30515-167">그러나 다음과 같은 제한 사항이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30515-167">However, the following restrictions exist.</span></span>  
  
### <a name="offline-data-cannot-be-backed-up"></a><span data-ttu-id="30515-168">오프라인 데이터는 백업할 수 없음</span><span class="sxs-lookup"><span data-stu-id="30515-168">Offline Data Cannot Be Backed Up</span></span>  
 <span data-ttu-id="30515-169">오프라인 데이터를 암시적으로 또는 명시적으로 참조하는 백업 작업은 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="30515-169">Any backup operation that implicitly or explicitly references data that is offline fails.</span></span> <span data-ttu-id="30515-170">그러한 경우를 몇 가지 예로 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="30515-170">Some typical examples include the following:</span></span>  
  
-   <span data-ttu-id="30515-171">전체 데이터베이스 백업을 요청하지만 데이터베이스의 파일 그룹 한 개가 오프라인입니다.</span><span class="sxs-lookup"><span data-stu-id="30515-171">You request a full database backup, but one filegroup of the database is offline.</span></span> <span data-ttu-id="30515-172">모든 파일 그룹이 암시적으로 전체 데이터베이스 백업에 포함되므로 이 작업은 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="30515-172">Because all filegroups are implicitly included in a full database backup, this operation fails.</span></span>  
  
     <span data-ttu-id="30515-173">이 데이터베이스를 백업하려면 파일 백업을 사용하고 온라인 파일 그룹만 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="30515-173">To back up this database, you can use a file backup and specify only the filegroups that are online.</span></span>  
  
-   <span data-ttu-id="30515-174">부분 백업을 요청하지만 읽기/쓰기 파일 그룹이 오프라인입니다.</span><span class="sxs-lookup"><span data-stu-id="30515-174">You request a partial backup, but a read/write filegroup is offline.</span></span> <span data-ttu-id="30515-175">부분 백업에는 모든 읽기/쓰기 파일 그룹이 필요하므로 작업은 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="30515-175">Because all read/write filegroups are required for a partial backup, the operation fails.</span></span>  
  
-   <span data-ttu-id="30515-176">특정 파일의 파일 백업을 요청하지만 파일 중 하나가 온라인이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="30515-176">You request a file backup of specific files, but one of the files is not online.</span></span> <span data-ttu-id="30515-177">작업은 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="30515-177">The operation fails.</span></span> <span data-ttu-id="30515-178">온라인 파일을 백업하려면 파일 목록에서 오프라인 파일을 생략하고 작업을 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="30515-178">To back up the online files, you can omit the offline file from the file list and repeat the operation.</span></span>  
  
 <span data-ttu-id="30515-179">일반적으로 로그 백업은 하나 이상의 데이터 파일을 사용할 수 없더라도 성공적으로 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="30515-179">Typically, a log backup succeeds even if one or more data files are unavailable.</span></span> <span data-ttu-id="30515-180">그러나 일부 파일에 대량 로그 복구 모델에서 수행된 대량 로그 변경 내용이 포함되어 있는 경우 모든 파일이 온라인 상태에 있어야 백업이 성공합니다.</span><span class="sxs-lookup"><span data-stu-id="30515-180">However, if any file contains bulk-logged changes made under the bulk-logged recovery model, all the files must be online for the backup to succeed.</span></span>  
  
### <a name="concurrency-restrictions-during-backup"></a><span data-ttu-id="30515-181">백업 중 동시성 제한 사항</span><span class="sxs-lookup"><span data-stu-id="30515-181">Concurrency Restrictions During Backup</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="30515-182">에서는 온라인 백업 프로세스를 사용하여 데이터베이스가 사용 중일 때도 데이터베이스 백업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30515-182">uses an online backup process to allow for a database backup while the database is still being used.</span></span> <span data-ttu-id="30515-183">백업 시 대부분의 작업을 수행할 수 있습니다. 예를 들어 INSERT, UPDATE 또는 DELETE 문은 백업 작업 시에도 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30515-183">During a backup, most operations are possible; for example, INSERT, UPDATE, or DELETE statements are allowed during a backup operation.</span></span> <span data-ttu-id="30515-184">그러나 데이터베이스 파일을 만들거나 삭제하는 동안 백업 작업을 시작하려고 하면 만들기 또는 삭제 작업이 완료되거나 백업 시간 제한이 초과될 때까지 백업 작업이 대기합니다.</span><span class="sxs-lookup"><span data-stu-id="30515-184">However, if you try to start a backup operation while a database file is being created or deleted, the backup operation waits until the create or delete operation is finished or the backup times out.</span></span>  
  
 <span data-ttu-id="30515-185">데이터베이스 백업 또는 트랜잭션 로그 백업 시에 실행할 수 없는 작업은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="30515-185">Operations that cannot run during a database backup or transaction log backup include the following:</span></span>  
  
-   <span data-ttu-id="30515-186">ADD FILE이나 REMOVE FILE 옵션과 함께 사용되는 ALTER DATABASE 문 등의 파일 관리 작업</span><span class="sxs-lookup"><span data-stu-id="30515-186">File-management operations such as the ALTER DATABASE statement with either the ADD FILE or REMOVE FILE options.</span></span>  
  
-   <span data-ttu-id="30515-187">데이터베이스 축소 또는 파일 축소 작업.</span><span class="sxs-lookup"><span data-stu-id="30515-187">Shrink database or shrink file operations.</span></span> <span data-ttu-id="30515-188">자동 축소 작업도 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="30515-188">This includes auto-shrink operations.</span></span>  
  
-   <span data-ttu-id="30515-189">백업 작업이 진행 중일 때는 데이터베이스 파일을 만들거나 삭제하려고 해도 해당 작업이 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="30515-189">If you try to create or delete a database file while a backup operation is in progress, the create or delete operation fails.</span></span>  
  
 <span data-ttu-id="30515-190">백업 작업이 파일 관리 작업 또는 축소 작업과 겹치면 충돌이 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="30515-190">If a backup operation overlaps with a file-management operation or shrink operation, a conflict occurs.</span></span> <span data-ttu-id="30515-191">충돌하는 작업 중 어떤 작업이 먼저 시작되었는지에 관계없이 두 번째 작업은 첫 번째 작업에서 설정한 잠금 제한 시간이 초과될 때까지 대기합니다. 제한 시간은 세션 제한 시간 설정에서 제어합니다. 제한 시간 동안에 잠금이 해제되면 두 번째 작업이 계속됩니다.</span><span class="sxs-lookup"><span data-stu-id="30515-191">Regardless of which of the conflicting operation began first, the second operation waits for the lock set by the first operation to time out. (The time-out period is controlled by a session time-out setting.) If the lock is released during the time-out period, the second operation continues.</span></span> <span data-ttu-id="30515-192">잠금 제한 시간이 초과되면 두 번째 작업이 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="30515-192">If the lock times out, the second operation fails.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="30515-193">관련 작업</span><span class="sxs-lookup"><span data-stu-id="30515-193">Related Tasks</span></span>  
 <span data-ttu-id="30515-194">**백업 디바이스 및 백업 미디어를 사용하려면**</span><span class="sxs-lookup"><span data-stu-id="30515-194">**To work with backup devices and backup media**</span></span>  
  
-   [<span data-ttu-id="30515-195">디스크 파일에 대한 논리적 백업 디바이스 정의&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="30515-195">Define a Logical Backup Device for a Disk File &#40;SQL Server&#41;</span></span>](define-a-logical-backup-device-for-a-disk-file-sql-server.md)  
  
-   [<span data-ttu-id="30515-196">테이프 드라이브에 대한 논리적 백업 디바이스 정의&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="30515-196">Define a Logical Backup Device for a Tape Drive &#40;SQL Server&#41;</span></span>](define-a-logical-backup-device-for-a-tape-drive-sql-server.md)  
  
-   [<span data-ttu-id="30515-197">디스크 또는 테이프를 백업 대상으로 지정&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="30515-197">Specify a Disk or Tape As a Backup Destination &#40;SQL Server&#41;</span></span>](specify-a-disk-or-tape-as-a-backup-destination-sql-server.md)  
  
-   [<span data-ttu-id="30515-198">백업 디바이스 삭제&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="30515-198">Delete a Backup Device &#40;SQL Server&#41;</span></span>](delete-a-backup-device-sql-server.md)  
  
-   [<span data-ttu-id="30515-199">백업의 만료 날짜 설정&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="30515-199">Set the Expiration Date on a Backup &#40;SQL Server&#41;</span></span>](set-the-expiration-date-on-a-backup-sql-server.md)  
  
-   [<span data-ttu-id="30515-200">백업 테이프 또는 파일의 내용 보기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="30515-200">View the Contents of a Backup Tape or File &#40;SQL Server&#41;</span></span>](view-the-contents-of-a-backup-tape-or-file-sql-server.md)  
  
-   [<span data-ttu-id="30515-201">백업 세트의 데이터와 로그 파일 보기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="30515-201">View the Data and Log Files in a Backup Set &#40;SQL Server&#41;</span></span>](view-the-data-and-log-files-in-a-backup-set-sql-server.md)  
  
-   [<span data-ttu-id="30515-202">논리적 백업 디바이스의 속성 및 내용 보기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="30515-202">View the Properties and Contents of a Logical Backup Device &#40;SQL Server&#41;</span></span>](view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md)  
  
-   [<span data-ttu-id="30515-203">디바이스에서 백업 복원&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="30515-203">Restore a Backup from a Device &#40;SQL Server&#41;</span></span>](restore-a-backup-from-a-device-sql-server.md)  
  
-   [<span data-ttu-id="30515-204">자습서: Azure Blob Storage 서비스로 SQL Server 백업 및 복원</span><span class="sxs-lookup"><span data-stu-id="30515-204">Tutorial: SQL Server Backup and Restore to Azure Blob Storage Service</span></span>](../tutorial-sql-server-backup-and-restore-to-azure-blob-storage-service.md)  
  
 <span data-ttu-id="30515-205">**백업을 만들려면**</span><span class="sxs-lookup"><span data-stu-id="30515-205">**To create a backup**</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="30515-206">부분 또는 복사 전용 백업의 경우 각각 PARTIAL 또는 COPY_ONLY 옵션과 함께 [!INCLUDE[tsql](../../includes/tsql-md.md)][BACKUP](/sql/t-sql/statements/backup-transact-sql) 문을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="30515-206">For partial or copy-only backups, you must use the [!INCLUDE[tsql](../../includes/tsql-md.md)][BACKUP](/sql/t-sql/statements/backup-transact-sql) statement with the PARTIAL or COPY_ONLY option, respectively.</span></span>  
  
-   [<span data-ttu-id="30515-207">전체 데이터베이스 백업 만들기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="30515-207">Create a Full Database Backup &#40;SQL Server&#41;</span></span>](create-a-full-database-backup-sql-server.md)  
  
-   [<span data-ttu-id="30515-208">트랜잭션 로그 백업&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="30515-208">Back Up a Transaction Log &#40;SQL Server&#41;</span></span>](back-up-a-transaction-log-sql-server.md)  
  
-   [<span data-ttu-id="30515-209">파일 및 파일 그룹 백업&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="30515-209">Back Up Files and Filegroups &#40;SQL Server&#41;</span></span>](back-up-files-and-filegroups-sql-server.md)  
  
-   [<span data-ttu-id="30515-210">차등 데이터베이스 백업 만들기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="30515-210">Create a Differential Database Backup &#40;SQL Server&#41;</span></span>](create-a-differential-database-backup-sql-server.md)  
  
-   [<span data-ttu-id="30515-211">데이터베이스가 손상된 경우 트랜잭션 로그 백업&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="30515-211">Back Up the Transaction Log When the Database Is Damaged &#40;SQL Server&#41;</span></span>](back-up-the-transaction-log-when-the-database-is-damaged-sql-server.md)  
  
-   [<span data-ttu-id="30515-212">백업 또는 복원 중 백업 체크섬 설정 또는 해제&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="30515-212">Enable or Disable Backup Checksums During Backup or Restore &#40;SQL Server&#41;</span></span>](enable-or-disable-backup-checksums-during-backup-or-restore-sql-server.md)  
  
-   [<span data-ttu-id="30515-213">오류 발생 후 백업 또는 복원 작업 계속 또는 중지 여부 지정&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="30515-213">Specify Whether a Backup or Restore Operation Continues or Stops After Encountering an Error &#40;SQL Server&#41;</span></span>](specify-if-backup-or-restore-continues-or-stops-after-error.md)  
  
-   [<span data-ttu-id="30515-214">Resource Governor를 사용하여 백업 압축을 통해 CPU 사용량 제한&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="30515-214">Use Resource Governor to Limit CPU Usage by Backup Compression &#40;Transact-SQL&#41;</span></span>](use-resource-governor-to-limit-cpu-usage-by-backup-compression-transact-sql.md)  
  
-   [<span data-ttu-id="30515-215">자습서: Azure Blob Storage 서비스로 SQL Server 백업 및 복원</span><span class="sxs-lookup"><span data-stu-id="30515-215">Tutorial: SQL Server Backup and Restore to Azure Blob Storage Service</span></span>](../tutorial-sql-server-backup-and-restore-to-azure-blob-storage-service.md)  
  
## <a name="see-also"></a><span data-ttu-id="30515-216">참고 항목</span><span class="sxs-lookup"><span data-stu-id="30515-216">See Also</span></span>  
 <span data-ttu-id="30515-217">[SQL Server 데이터베이스 백업 및 복원](back-up-and-restore-of-sql-server-databases.md) </span><span class="sxs-lookup"><span data-stu-id="30515-217">[Back Up and Restore of SQL Server Databases](back-up-and-restore-of-sql-server-databases.md) </span></span>  
 <span data-ttu-id="30515-218">[복원 및 복구 개요&#40;SQL Server&#41;](restore-and-recovery-overview-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="30515-218">[Restore and Recovery Overview &#40;SQL Server&#41;](restore-and-recovery-overview-sql-server.md) </span></span>  
 <span data-ttu-id="30515-219">[유지 관리 계획](../maintenance-plans/maintenance-plans.md) </span><span class="sxs-lookup"><span data-stu-id="30515-219">[Maintenance Plans](../maintenance-plans/maintenance-plans.md) </span></span>  
 <span data-ttu-id="30515-220">[트랜잭션 로그&#40;SQL Server&#41;](../logs/the-transaction-log-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="30515-220">[The Transaction Log &#40;SQL Server&#41;](../logs/the-transaction-log-sql-server.md) </span></span>  
 [<span data-ttu-id="30515-221">복구 모델&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="30515-221">Recovery Models &#40;SQL Server&#41;</span></span>](recovery-models-sql-server.md)  
  
  
