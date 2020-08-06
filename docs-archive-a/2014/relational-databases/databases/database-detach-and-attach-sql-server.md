---
title: 데이터베이스 분리 및 연결(SQL Server) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- upgrading databases
- databases [SQL Server], detaching
- detach database [SQL Server]
- databases [SQL Server], attaching
- removing databases
- transaction logs [SQL Server], detaching
- databases [SQL Server], removing
- restoring [SQL Server], attached databases
- transaction logs [SQL Server], attaching
- differential backups, after detaching
- moving databases
- attach database [SQL Server]
- detaching databases [SQL Server]
- differential base [SQL Server]
- attaching databases [SQL Server]
- databases [SQL Server], moving
ms.assetid: d0de0639-bc54-464e-98b1-6af22a27eb86
author: stevestein
ms.author: sstein
ms.openlocfilehash: 54eeeec995e390b71ce8871b680c26138fc88783
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650113"
---
# <a name="database-detach-and-attach-sql-server"></a><span data-ttu-id="97d82-102">데이터베이스 분리 및 연결(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="97d82-102">Database Detach and Attach (SQL Server)</span></span>
  <span data-ttu-id="97d82-103">데이터베이스의 데이터 및 트랜잭션 로그 파일은 분리할 수 있으며 동일한 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스나 다른 인스턴스에 다시 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="97d82-103">The data and transaction log files of a database can be detached and then reattached to the same or another instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="97d82-104">데이터베이스 분리 및 연결은 데이터베이스를 같은 컴퓨터의 다른 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스로 변경하거나 데이터베이스를 이동하는 경우 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="97d82-104">Detaching and attaching a database is useful if you want to change the database to a different instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on the same computer or to move the database.</span></span>  
  
 <span data-ttu-id="97d82-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 디스크상 스토리지 형식은 64비트 및 32비트 환경에서 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="97d82-105">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on-disk storage format is the same in the 64-bit and 32-bit environments.</span></span> <span data-ttu-id="97d82-106">따라서 32비트 및 64비트 환경에서 연결 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="97d82-106">Therefore, attach works across 32-bit and 64-bit environments.</span></span>  <span data-ttu-id="97d82-107">한 환경에서 실행 중인 서버 인스턴스에서 분리된 데이터베이스를 다른 환경에서 실행하는 서버 인스턴스에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="97d82-107">A database detached from a server instance running in one environment can be attached on a server instance that runs in another environment.</span></span>  
  
  
  
##  <a name="security"></a><a name="Security"></a> <span data-ttu-id="97d82-108">보안</span><span class="sxs-lookup"><span data-stu-id="97d82-108">Security</span></span>  
 <span data-ttu-id="97d82-109">파일 액세스 권한은 데이터베이스 분리, 연결 등의 여러 데이터베이스 작업 중에 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="97d82-109">File access permissions are set during a number of database operations, including detaching or attaching a database.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="97d82-110">알 수 없거나 신뢰할 수 없는 출처의 데이터베이스는 연결 또는 복원하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="97d82-110">We recommend that you do not attach or restore databases from unknown or untrusted sources.</span></span> <span data-ttu-id="97d82-111">이러한 데이터베이스에 포함된 악성 코드가 의도하지 않은 [!INCLUDE[tsql](../../includes/tsql-md.md)] 코드를 실행하거나 스키마 또는 물리적 데이터베이스 구조를 수정하여 오류가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="97d82-111">Such databases could contain malicious code that might execute unintended [!INCLUDE[tsql](../../includes/tsql-md.md)] code or cause errors by modifying the schema or the physical database structure.</span></span> <span data-ttu-id="97d82-112">알 수 없거나 신뢰할 수 없는 소스의 데이터베이스를 사용하기 전에 비프로덕션 서버의 데이터베이스에서 [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) 를 실행하여 데이터베이스에서 코드(예: 저장 프로시저 또는 다른 사용자 정의 코드)를 시험해 보세요.</span><span class="sxs-lookup"><span data-stu-id="97d82-112">Before you use a database from an unknown or untrusted source, run [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) on the database on a nonproduction server and also examine the code, such as stored procedures or other user-defined code, in the database.</span></span>  
  
##  <a name="detaching-a-database"></a><a name="DetachDb"></a> <span data-ttu-id="97d82-113">데이터베이스 분리</span><span class="sxs-lookup"><span data-stu-id="97d82-113">Detaching a Database</span></span>  
 <span data-ttu-id="97d82-114">데이터베이스를 분리하면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에서 해당 데이터베이스가 제거되지만 데이터베이스의 데이터 파일 및 트랜잭션 로그 파일은 그대로 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="97d82-114">Detaching a database removes it from the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] but leaves the database intact within its data files and transaction log files.</span></span> <span data-ttu-id="97d82-115">이 파일은 데이터베이스가 분리된 해당 서버뿐 아니라 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스가 실행되는 모든 컴퓨터에 데이터베이스를 연결하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="97d82-115">These files can then be used to attach the database to any instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], including the server from which the database was detached.</span></span>  
  
 <span data-ttu-id="97d82-116">다음 중 하나라도 해당하는 경우 데이터베이스를 분리할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="97d82-116">You cannot detach a database if any of the following are true:</span></span>  
  
-   <span data-ttu-id="97d82-117">데이터베이스를 복제하여 게시한 경우.</span><span class="sxs-lookup"><span data-stu-id="97d82-117">The database is replicated and published.</span></span> <span data-ttu-id="97d82-118">데이터베이스가 복제된 경우 해당 데이터베이스의 게시를 해제해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="97d82-118">If replicated, the database must be unpublished.</span></span> <span data-ttu-id="97d82-119">따라서 데이터베이스를 분리하려면 먼저 [sp_replicationdboption](/sql/relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql)을 실행하여 게시를 해제해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="97d82-119">Before you can detach it, you must disable publishing by running [sp_replicationdboption](/sql/relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="97d82-120">**sp_replicationdboption**을 사용할 수 없는 경우 [sp_removedbreplication](/sql/relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql)을 실행하여 복제를 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="97d82-120">If you cannot use **sp_replicationdboption**, you can remove replication by running [sp_removedbreplication](/sql/relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql).</span></span>  
  
-   <span data-ttu-id="97d82-121">데이터베이스에 데이터베이스 스냅샷이 있는 경우</span><span class="sxs-lookup"><span data-stu-id="97d82-121">A database snapshot exists on the database.</span></span>  
  
     <span data-ttu-id="97d82-122">데이터베이스를 분리하려면 먼저 해당 데이터베이스의 모든 스냅샷을 삭제해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="97d82-122">Before you can detach the database, you must drop all of its snapshots.</span></span> <span data-ttu-id="97d82-123">자세한 내용은 [Drop a Database Snapshot &#40;Transact-SQL&#41;](drop-a-database-snapshot-transact-sql.md).</span><span class="sxs-lookup"><span data-stu-id="97d82-123">For more information, see [Drop a Database Snapshot &#40;Transact-SQL&#41;](drop-a-database-snapshot-transact-sql.md).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="97d82-124">데이터베이스 스냅샷은 분리하거나 연결할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="97d82-124">A database snapshot cannot be detached or attached.</span></span>  
  
-   <span data-ttu-id="97d82-125">데이터베이스가 데이터베이스 미러링 세션에서 미러되고 있는 경우.</span><span class="sxs-lookup"><span data-stu-id="97d82-125">The database is being mirrored in a database mirroring session.</span></span>  
  
     <span data-ttu-id="97d82-126">데이터베이스는 세션이 종료된 후에야 분리될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="97d82-126">The database cannot be detached unless the session is terminated.</span></span> <span data-ttu-id="97d82-127">자세한 내용은 [데이터베이스 미러링 제거&#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="97d82-127">For more information, see [Removing Database Mirroring &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md).</span></span>  
  
-   <span data-ttu-id="97d82-128">주의 대상 데이터베이스인 경우</span><span class="sxs-lookup"><span data-stu-id="97d82-128">The database is suspect.</span></span> <span data-ttu-id="97d82-129">주의 대상 데이터베이스는 분리할 수 없습니다. 분리하려면 먼저 데이터베이스를 응급 모드로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="97d82-129">A suspect database cannot be detached; before you can detach it, you must put it into emergency mode.</span></span> <span data-ttu-id="97d82-130">데이터베이스를 응급 모드로 설정하는 방법은 [ALTER DATABASE&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="97d82-130">For more information about how to put a database into emergency mode, see [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql).</span></span>  
  
-   <span data-ttu-id="97d82-131">데이터베이스가 시스템 데이터베이스인 경우</span><span class="sxs-lookup"><span data-stu-id="97d82-131">The database is a system database.</span></span>  
  
### <a name="backup-and-restore-and-detach"></a><span data-ttu-id="97d82-132">백업, 복원 및 분리</span><span class="sxs-lookup"><span data-stu-id="97d82-132">Backup and Restore and Detach</span></span>  
 <span data-ttu-id="97d82-133">읽기 전용 데이터베이스를 분리하면 차등 백업의 차등 기반에 대한 정보가 손실됩니다.</span><span class="sxs-lookup"><span data-stu-id="97d82-133">Detaching a read-only database loses information about the differential bases of differential backups.</span></span> <span data-ttu-id="97d82-134">자세한 내용은 [차등 백업&#40;SQL Server&#41;](../backup-restore/differential-backups-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="97d82-134">For more information, see [Differential Backups &#40;SQL Server&#41;](../backup-restore/differential-backups-sql-server.md).</span></span>  
  
### <a name="responding-to-detach-errors"></a><span data-ttu-id="97d82-135">분리 오류에 대한 대처 방법</span><span class="sxs-lookup"><span data-stu-id="97d82-135">Responding to Detach Errors</span></span>  
 <span data-ttu-id="97d82-136">데이터베이스를 분리하는 동안 발생한 오류로 인해 데이터를 완전히 닫지 못하고 트랜잭션 로그를 다시 작성하지 못할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="97d82-136">Errors produced while detaching a database can prevent the database from closing cleanly and the transaction log from being rebuilt.</span></span> <span data-ttu-id="97d82-137">오류 메시지가 표시되면 다음의 수정 동작을 수행하세요.</span><span class="sxs-lookup"><span data-stu-id="97d82-137">If you receive an error message, perform the following corrective actions:</span></span>  
  
1.  <span data-ttu-id="97d82-138">주 파일뿐 아니라 데이터베이스와 관련된 모든 파일을 다시 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="97d82-138">Reattach all files associated with the database, not just the primary file.</span></span>  
  
2.  <span data-ttu-id="97d82-139">오류 메시지를 발생시킨 문제를 해결합니다.</span><span class="sxs-lookup"><span data-stu-id="97d82-139">Resolve the problem that caused the error message.</span></span>  
  
3.  <span data-ttu-id="97d82-140">데이터베이스를 다시 분리합니다.</span><span class="sxs-lookup"><span data-stu-id="97d82-140">Detach the database again.</span></span>  
  
##  <a name="attaching-a-database"></a><a name="AttachDb"></a> <span data-ttu-id="97d82-141">데이터베이스 연결</span><span class="sxs-lookup"><span data-stu-id="97d82-141">Attaching a Database</span></span>  
 <span data-ttu-id="97d82-142">복사 또는 분리한 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스를 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="97d82-142">You can attach a copied or detached [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database.</span></span> <span data-ttu-id="97d82-143">서버 인스턴스를 연결 하는 경우 [!INCLUDE[ssVersion2005](../../includes/sscurrent-md.md)] 에서와 같이 다른 데이터베이스 파일과 함께 이전 위치에서 카탈로그 파일이 연결 됩니다 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="97d82-143">When you attach a [!INCLUDE[ssVersion2005](../../includes/sscurrent-md.md)] server instance, the catalog files are attached from their previous location along with the other database files, the same as in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].</span></span> <span data-ttu-id="97d82-144">자세한 내용은 [전체 텍스트 검색 업그레이드](../search/upgrade-full-text-search.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="97d82-144">For more information, see [Upgrade Full-Text Search](../search/upgrade-full-text-search.md).</span></span>  
  
 <span data-ttu-id="97d82-145">데이터베이스를 연결할 경우 모든 데이터 파일(MDF 및 NDF 파일)이 사용 가능해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="97d82-145">When you attach a database, all data files (MDF and NDF files) must be available.</span></span> <span data-ttu-id="97d82-146">데이터베이스가 처음 생성되었을 때 또는 마지막으로 연결되었을 때와 경로가 다른 데이터 파일이 있으면 해당 파일의 현재 경로를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="97d82-146">If any data file has a different path from when the database was first created or last attached, you must specify the current path of the file.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="97d82-147">연결되는 주 데이터 파일이 읽기 전용일 경우 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 은 해당 데이터베이스를 읽기 전용으로 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="97d82-147">If the primary data file being attached is read-only, the [!INCLUDE[ssDE](../../includes/ssde-md.md)] assumes that the database is read-only.</span></span>  
  
 <span data-ttu-id="97d82-148">암호화 된 데이터베이스가 인스턴스에 처음 연결 된 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스 소유자는 OPEN MASTER KEY 해독은 BY PASSWORD = **' *`password`* '** 문을 실행 하 여 데이터베이스의 마스터 키를 열어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="97d82-148">When an encrypted database is first attached to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the database owner must open the master key of the database by executing the following statement: OPEN MASTER KEY DECRYPTION BY PASSWORD = **'*`password`*'**.</span></span> <span data-ttu-id="97d82-149">그런 다음 ALTER MASTER KEY ADD ENCRYPTION BY SERVICE MASTER KEY 문을 실행하여 데이터베이스 마스터 키의 자동 암호 해독을 설정하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="97d82-149">We recommend that you enable automatic decryption of the master key by executing the following statement: ALTER MASTER KEY ADD ENCRYPTION BY SERVICE MASTER KEY.</span></span> <span data-ttu-id="97d82-150">자세한 내용은 [CREATE MASTER KEY&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-master-key-transact-sql) 및 [ALTER MASTER KEY&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-master-key-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="97d82-150">For more information, see [CREATE MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-master-key-transact-sql) and [ALTER MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-master-key-transact-sql).</span></span>  
  
 <span data-ttu-id="97d82-151">로그 파일 연결 요구 사항은 데이터베이스가 읽기/쓰기인지 아니면 읽기 전용인지에 따라 다음과 같이 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="97d82-151">The requirement for attaching log files depends partly on whether the database is read-write or read-only, as follows:</span></span>  
  
-   <span data-ttu-id="97d82-152">읽기 전용 데이터베이스에서는 보통 새 위치에 로그 파일을 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="97d82-152">For a read-write database, you can usually attach a log file in a new location.</span></span> <span data-ttu-id="97d82-153">그러나 경우에 따라 데이터베이스를 다시 연결하려면 기존 로그 파일이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="97d82-153">However, in some cases, reattaching a database requires its existing log files.</span></span> <span data-ttu-id="97d82-154">따라서 데이터베이스가 분리된 로그 파일 없이도 성공적으로 연결될 때까지 모든 분리된 로그 파일을 항상 보존하는 것이 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="97d82-154">Therefore, it is important to always keep all the detached log files until the database has been successfully attached without them.</span></span>  
  
     <span data-ttu-id="97d82-155">읽기/쓰기 데이터베이스에 로그 파일이 하나고 이 로그 파일에 새 위치를 지정하지 않은 경우 연결 작업에서 해당 파일의 이전 위치를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="97d82-155">If a read-write database has a single log file and you do not specify a new location for the log file, the attach operation looks in the old location for the file.</span></span> <span data-ttu-id="97d82-156">로그 파일을 발견하면 데이터베이스가 완전히 종료되었는지 여부에 관계없이 이전 로그 파일을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="97d82-156">If it is found, the old log file is used, regardless of whether the database was shut down cleanly.</span></span> <span data-ttu-id="97d82-157">하지만 이전 로그 파일을 찾지 못하고 데이터베이스가 완전히 종료되었으며 활성 로그 체인이 없는 경우 연결 작업에서 해당 데이터베이스의 로그 파일을 새로 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="97d82-157">However, if the old log file is not found and if the database was shut down cleanly and has no active log chain, the attach operation attempts to build a new log file for the database.</span></span>  
  
-   <span data-ttu-id="97d82-158">연결 되는 주 데이터 파일이 읽기 전용일 경우에서 [!INCLUDE[ssDE](../../includes/ssnoversion-md.md)] 주 파일에 저장 된 로그 위치를 업데이트할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="97d82-158">If the primary data file being attached is read-only, the [!INCLUDE[ssDE](../../includes/ssnoversion-md.md)] cannot update the log location stored in the primary file.</span></span>  
  
  
  
###  <a name="metadata-changes-on-attaching-a-database"></a><a name="Metadata"></a> <span data-ttu-id="97d82-159">데이터베이스 연결 시 메타데이터 변경</span><span class="sxs-lookup"><span data-stu-id="97d82-159">Metadata Changes on Attaching a Database</span></span>  
 <span data-ttu-id="97d82-160">읽기 전용 데이터베이스를 분리한 다음 다시 연결하는 경우 현재 차등 기반에 대한 백업 정보는 손실됩니다.</span><span class="sxs-lookup"><span data-stu-id="97d82-160">When a read-only database is detached and then reattached, the backup information about the current differential base is lost.</span></span> <span data-ttu-id="97d82-161">*차등 기반* 은 데이터베이스나 데이터베이스에 있는 파일 또는 파일 그룹의 하위 집합에 있는 모든 데이터에 대한 최신 전체 백업입니다.</span><span class="sxs-lookup"><span data-stu-id="97d82-161">The *differential base* is the most recent full backup of all the data in the database or in a subset of the files or filegroups of the database.</span></span> <span data-ttu-id="97d82-162">기반 백업 정보가 없는 경우 **master** 데이터베이스는 읽기 전용 데이터베이스와 동기화되지 않으므로 이후에 수행되는 차등 백업에서 예기치 않은 결과가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="97d82-162">Without the base-backup information, the **master** database becomes unsynchronized with the read-only database, so differential backups taken thereafter may provide unexpected results.</span></span> <span data-ttu-id="97d82-163">그러므로 읽기 전용 데이터베이스를 차등 백업하는 경우에는 데이터베이스를 다시 연결한 다음 전체 백업을 수행하여 새로운 차등 기반을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="97d82-163">Therefore, if you are using differential backups with a read-only database, you should establish a new differential base by taking a full backup after you reattach the database.</span></span> <span data-ttu-id="97d82-164">차등 백업에 대한 자세한 내용은 [차등 백업&#40;SQL Server&#41;](../backup-restore/differential-backups-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="97d82-164">For information about differential backups, see [Differential Backups &#40;SQL Server&#41;](../backup-restore/differential-backups-sql-server.md).</span></span>  
  
 <span data-ttu-id="97d82-165">연결 시 데이터베이스가 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="97d82-165">On attach, database startup occurs.</span></span> <span data-ttu-id="97d82-166">일반적으로 데이터베이스를 연결하면 데이터베이스를 분리 또는 복사한 시점과 동일한 상태가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="97d82-166">Generally, attaching a database places it in the same state that it was in when it was detached or copied.</span></span> <span data-ttu-id="97d82-167">그러나 연결 및 분리 작업을 수행하면 해당 데이터베이스의 데이터베이스 간 소유권 체인을 사용할 수 없게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="97d82-167">However, attach-and-detach operations both disable cross-database ownership chaining for the database.</span></span> <span data-ttu-id="97d82-168">체인을 사용하도록 설정하는 방법은 [cross db ownership chaining 서버 구성 옵션](../../database-engine/configure-windows/cross-db-ownership-chaining-server-configuration-option.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="97d82-168">For information about how to enable chaining, see [cross db ownership chaining Server Configuration Option](../../database-engine/configure-windows/cross-db-ownership-chaining-server-configuration-option.md).</span></span> <span data-ttu-id="97d82-169">또한 데이터베이스를 연결할 때마다 TRUSTWORTHY는 OFF로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="97d82-169">Also, TRUSTWORTHY is set to OFF whenever the database is attached.</span></span> <span data-ttu-id="97d82-170">TRUSTWORTHY를 ON으로 설정하는 방법은 [ALTER DATABASE&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="97d82-170">For information about how to set TRUSTWORTHY to ON, see [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql).</span></span>  
  
### <a name="backup-and-restore-and-attach"></a><span data-ttu-id="97d82-171">백업, 복원 및 연결</span><span class="sxs-lookup"><span data-stu-id="97d82-171">Backup and Restore and Attach</span></span>  
 <span data-ttu-id="97d82-172">완전히 또는 부분적으로 오프라인 상태인 데이터베이스와 마찬가지로 파일을 복원 중인 데이터베이스에는 연결될 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="97d82-172">Like any database that is fully or partially offline, a database with restoring files cannot be attached.</span></span> <span data-ttu-id="97d82-173">이때 복원 시퀀스를 중지하면 데이터베이스를 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="97d82-173">If you stop the restore sequence, you can attach the database.</span></span> <span data-ttu-id="97d82-174">그런 다음 복원 시퀀스를 다시 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="97d82-174">Then, you can restart the restore sequence.</span></span>  
  
###  <a name="attaching-a-database-to-another-server-instance"></a><a name="OtherServerInstance"></a> <span data-ttu-id="97d82-175">다른 서버 인스턴스에 데이터베이스 연결</span><span class="sxs-lookup"><span data-stu-id="97d82-175">Attaching a Database to Another Server Instance</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="97d82-176">최신 버전의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 만든 데이터베이스를 이전 버전에서 연결할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="97d82-176">A database created by a more recent version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cannot be attached in earlier versions.</span></span>  
  
 <span data-ttu-id="97d82-177">데이터베이스를 다른 서버 인스턴스에 연결하는 경우 사용자와 애플리케이션에 일관된 환경을 제공하려면 로그인, 작업 등 데이터베이스의 일부 또는 모든 메타데이터를 다른 서버 인스턴스에서 다시 만들어야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="97d82-177">When you attach a database onto another server instance, to provide a consistent experience to users and applications, you might have to re-create some or all of the metadata for the database, such as logins and jobs, on the other server instance.</span></span> <span data-ttu-id="97d82-178">자세한 내용은 [다른 서버 인스턴스에서 데이터베이스를 사용할 수 있도록 할 때 메타데이터 관리&#40;SQL Server&#41;](manage-metadata-when-making-a-database-available-on-another-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="97d82-178">For more information, see [Manage Metadata When Making a Database Available on Another Server Instance &#40;SQL Server&#41;](manage-metadata-when-making-a-database-available-on-another-server.md).</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="97d82-179">관련 작업</span><span class="sxs-lookup"><span data-stu-id="97d82-179">Related Tasks</span></span>  
 <span data-ttu-id="97d82-180">**데이터베이스를 분리하려면**</span><span class="sxs-lookup"><span data-stu-id="97d82-180">**To detach a database**</span></span>  
  
-   [<span data-ttu-id="97d82-181">sp_detach_db&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="97d82-181">sp_detach_db &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-detach-db-transact-sql)  
  
-   [<span data-ttu-id="97d82-182">데이터베이스 분리</span><span class="sxs-lookup"><span data-stu-id="97d82-182">Detach a Database</span></span>](detach-a-database.md)  
  
 <span data-ttu-id="97d82-183">**데이터베이스를 연결하려면**</span><span class="sxs-lookup"><span data-stu-id="97d82-183">**To attach a database**</span></span>  
  
-   [<span data-ttu-id="97d82-184">CREATE DATABASE&#40;SQL Server Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="97d82-184">CREATE DATABASE &#40;SQL Server Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-database-sql-server-transact-sql)  
  
-   [<span data-ttu-id="97d82-185">데이터베이스 연결</span><span class="sxs-lookup"><span data-stu-id="97d82-185">Attach a Database</span></span>](attach-a-database.md)  
  
-   [<span data-ttu-id="97d82-186">sp_attach_db&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="97d82-186">sp_attach_db &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-attach-db-transact-sql)  
  
-   [<span data-ttu-id="97d82-187">sp_attach_single_file_db&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="97d82-187">sp_attach_single_file_db &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-attach-single-file-db-transact-sql)  
  
 <span data-ttu-id="97d82-188">**분리 및 연결 작업을 사용하여 데이터베이스를 업그레이드하려면**</span><span class="sxs-lookup"><span data-stu-id="97d82-188">**To upgrade a database using detach and attach operations**</span></span>  
  
-   [<span data-ttu-id="97d82-189">분리 및 연결을 사용하여 데이터베이스 업그레이드&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="97d82-189">Upgrade a Database Using Detach and Attach &#40;Transact-SQL&#41;</span></span>](upgrade-a-database-using-detach-and-attach-transact-sql.md)  
  
 <span data-ttu-id="97d82-190">**분리 및 연결 작업을 사용하여 데이터베이스를 이동하려면**</span><span class="sxs-lookup"><span data-stu-id="97d82-190">**To move a database using detach and attach operations**</span></span>  
  
-   [<span data-ttu-id="97d82-191">분리 및 연결을 사용하여 데이터베이스 이동&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="97d82-191">Move a Database Using Detach and Attach &#40;Transact-SQL&#41;</span></span>](move-a-database-using-detach-and-attach-transact-sql.md)  
  
 <span data-ttu-id="97d82-192">**데이터베이스 스냅샷을 삭제하려면**</span><span class="sxs-lookup"><span data-stu-id="97d82-192">**To delete a database snapshot**</span></span>  
  
-   [<span data-ttu-id="97d82-193">데이터베이스 스냅샷 삭제&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="97d82-193">Drop a Database Snapshot &#40;Transact-SQL&#41;</span></span>](drop-a-database-snapshot-transact-sql.md)  
  
## <a name="see-also"></a><span data-ttu-id="97d82-194">참고 항목</span><span class="sxs-lookup"><span data-stu-id="97d82-194">See Also</span></span>  
 [<span data-ttu-id="97d82-195">데이터베이스 파일 및 파일 그룹</span><span class="sxs-lookup"><span data-stu-id="97d82-195">Database Files and Filegroups</span></span>](database-files-and-filegroups.md)  
  
  
