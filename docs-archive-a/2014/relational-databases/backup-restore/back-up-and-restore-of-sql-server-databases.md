---
title: SQL Server 데이터베이스 백업 및 복원 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- disaster recovery [SQL Server], see restoring [SQL Server]
- backups [SQL Server]
- restoring databases [SQL Server]
- backup [SQL Server], see backing up [SQL Server]
- databases [SQL Server], restoring
- backing up databases [SQL Server]
- restore [SQL Server], see restoring [SQL Server]
- disaster recovery [SQL Server], see backing up [SQL Server]
- backing up [SQL Server]
- Database Engine [SQL Server], backups
- databases [SQL Server], backups
ms.assetid: 570a21b3-ad29-44a9-aa70-deb2fbd34f27
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: ec2104219d98ed3cb97bfbb8993a3c28d45841c6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661203"
---
# <a name="back-up-and-restore-of-sql-server-databases"></a><span data-ttu-id="fbbc0-102">SQL Server 데이터베이스 백업 및 복원</span><span class="sxs-lookup"><span data-stu-id="fbbc0-102">Back Up and Restore of SQL Server Databases</span></span>
  <span data-ttu-id="fbbc0-103">이 항목에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스 백업의 이점과 기본 백업 및 복원 용어에 대해 설명하고 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에 대한 백업 및 복원 전략과 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 백업 및 복원을 위한 보안 고려 사항에 대해 소개합니다.</span><span class="sxs-lookup"><span data-stu-id="fbbc0-103">This topic describes the benefits of backing up [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases, basic backup and restore terms, and introduces backup and restore strategies for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and security considerations for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backup and restore.</span></span>  
  
 <span data-ttu-id="fbbc0-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 백업 및 복원 구성 요소는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스에 저장된 중요한 데이터를 보호하기 위한 필수 보호 방법을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="fbbc0-104">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backup and restore component provides an essential safeguard for protecting critical data stored in your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases.</span></span> <span data-ttu-id="fbbc0-105">치명적인 데이터 손실 위험을 최소화하려면 정기적으로 데이터베이스를 백업하여 수정 내용을 보존해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fbbc0-105">To minimize the risk of catastrophic data loss, you need to back up your databases to preserve modifications to your data on a regular basis.</span></span> <span data-ttu-id="fbbc0-106">잘 계획된 백업 및 복원 전략은 다양한 오류로 인한 데이터 손실을 막아줍니다.</span><span class="sxs-lookup"><span data-stu-id="fbbc0-106">A well-planned backup and restore strategy helps protect databases against data loss caused by a variety of failures.</span></span> <span data-ttu-id="fbbc0-107">백업 세트를 복원하고 데이터베이스를 복구하는 방법으로 전략을 테스트하여 재해에 효과적으로 대응할 수 있도록 준비하세요.</span><span class="sxs-lookup"><span data-stu-id="fbbc0-107">Test your strategy by restoring a set of backups and then recovering your database to prepare you to respond effectively to a disaster.</span></span>  
  
 <span data-ttu-id="fbbc0-108">백업을 저장하기 위한 로컬 스토리지 외에도 SQL Server는 Azure Blob Storage 서비스로의 백업 및 복원도 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="fbbc0-108">In addition to local storage for storing the backups, SQL Server also supports backup to and restore from the Azure Blob Storage Service.</span></span> <span data-ttu-id="fbbc0-109">자세한 내용은 [Azure Blob Storage 서비스로 SQL Server 백업 및 복원](sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fbbc0-109">For more information, see [SQL Server Backup and Restore with Azure Blob Storage Service](sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md).</span></span>  
  

  
##  <a name="benefits"></a><a name="Benefits"></a> <span data-ttu-id="fbbc0-110">이점</span><span class="sxs-lookup"><span data-stu-id="fbbc0-110">Benefits</span></span>  
  
-   <span data-ttu-id="fbbc0-111">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스를 백업하고 백업에 대한 테스트 복원 절차를 실행한 다음 안전한 오프 사이트 위치에 백업을 저장하여 치명적인 데이터 손실을 방지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fbbc0-111">Backing up your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases, running test restores procedures on your backups, and storing copies of backups in a safe, off-site location protects you from potentially catastrophic data loss.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="fbbc0-112">이렇게 하는 것이 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터를 안정적으로 보호하는 유일한 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="fbbc0-112">This is the only way to reliably protect your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data.</span></span>  
  
     <span data-ttu-id="fbbc0-113">유효한 데이터베이스 백업을 사용하여 다음의 여러 오류로부터 데이터를 복구할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fbbc0-113">With valid backups of a database, you can recover your data from many failures, such as:</span></span>  
  
    -   <span data-ttu-id="fbbc0-114">미디어 오류</span><span class="sxs-lookup"><span data-stu-id="fbbc0-114">Media failure.</span></span>  
  
    -   <span data-ttu-id="fbbc0-115">사용자 오류(예: 실수로 테이블 삭제)</span><span class="sxs-lookup"><span data-stu-id="fbbc0-115">User errors, for example, dropping a table by mistake.</span></span>  
  
    -   <span data-ttu-id="fbbc0-116">하드웨어 오류(예: 손상된 디스크 드라이브 또는 서버의 영구적 손실)</span><span class="sxs-lookup"><span data-stu-id="fbbc0-116">Hardware failures, for example, a damaged disk drive or permanent loss of a server.</span></span>  
  
    -   <span data-ttu-id="fbbc0-117">자연 재해</span><span class="sxs-lookup"><span data-stu-id="fbbc0-117">Natural disasters.</span></span> <span data-ttu-id="fbbc0-118">Azure Blob Storage 서비스로 SQL Server 백업을 사용하면 온-프레미스 위치에 영향을 미치는 자연 재해가 발생할 경우에 사용할 오프사이트 백업을 온-프레미스 위치와 다른 영역에 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fbbc0-118">By using SQL Server Backup to Azure Blob storage service, you can create an off-site backup in a different region than your on-premises location, to use in the event of a natural disaster affecting your on-premises location.</span></span>  
  
-   <span data-ttu-id="fbbc0-119">또한 데이터베이스 백업은 서버 간 데이터베이스 복사, [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] 또는 데이터베이스 미러링 설정, 보관 등의 일상적인 관리 용도로 유용하게 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fbbc0-119">Additionally, backups of a database are useful for routine administrative purposes, such as copying a database from one server to another, setting up [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] or database mirroring, and archiving.</span></span>  
  

  
##  <a name="components-and-concepts"></a><a name="TermsAndDefinitions"></a> <span data-ttu-id="fbbc0-120">구성 요소 및 개념</span><span class="sxs-lookup"><span data-stu-id="fbbc0-120">Components and Concepts</span></span>  
 <span data-ttu-id="fbbc0-121">백업[동사]</span><span class="sxs-lookup"><span data-stu-id="fbbc0-121">back up [verb]</span></span>  
 <span data-ttu-id="fbbc0-122">데이터 또는 로그 레코드를 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스 또는 해당 트랜잭션 로그에서 백업 디바이스(예: 디스크)로 복사하여 데이터 백업 또는 로그 백업을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fbbc0-122">Copies the data or log records from a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database or its transaction log to a backup device, such as a disk, to create a data backup or log backup.</span></span>  
  
 <span data-ttu-id="fbbc0-123">백업[명사]</span><span class="sxs-lookup"><span data-stu-id="fbbc0-123">backup [noun]</span></span>  
 <span data-ttu-id="fbbc0-124">오류가 발생한 이후에 데이터를 복원 및 복구하는 데 사용할 수 있는 데이터 복사본입니다.</span><span class="sxs-lookup"><span data-stu-id="fbbc0-124">A copy of data that can be used to restore and recover the data after a failure.</span></span> <span data-ttu-id="fbbc0-125">데이터베이스 백업을 사용하여 데이터베이스 복사본을 새 위치에 복원할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fbbc0-125">Backups of a database can also be used to restore a copy the database to a new location.</span></span>  
  
 <span data-ttu-id="fbbc0-126">백업 디바이스(backup device)</span><span class="sxs-lookup"><span data-stu-id="fbbc0-126">backup device</span></span>  
 <span data-ttu-id="fbbc0-127">SQL Server 백업이 기록되는 대상이자 백업을 복원하는 원본이 되는 디스크 또는 테이프 디바이스입니다.</span><span class="sxs-lookup"><span data-stu-id="fbbc0-127">A disk or tape device to which SQL Server backups are written and from which they can be restored.</span></span> <span data-ttu-id="fbbc0-128">SQL Server 백업은 Azure Blob Storage 서비스에 기록할 수도 있으며 백업 파일의 대상과 이름을 지정하기 위해 **URL** 형식이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="fbbc0-128">SQL Server backups can also be written to an Azure Blob storage service, and **URL** format is used to specify the destination and the name of the backup file..</span></span> <span data-ttu-id="fbbc0-129">자세한 내용은 [Azure Blob Storage 서비스로 SQL Server 백업 및 복원](sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fbbc0-129">For more information, see [SQL Server Backup and Restore with Azure Blob Storage Service](sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md).</span></span>  
  
 <span data-ttu-id="fbbc0-130">백업 미디어</span><span class="sxs-lookup"><span data-stu-id="fbbc0-130">backup media</span></span>  
 <span data-ttu-id="fbbc0-131">하나 이상의 백업이 기록된 하나 이상의 테이프 또는 디스크 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="fbbc0-131">One or more tapes or disk files to which one or more backup have been written.</span></span>  
  
 <span data-ttu-id="fbbc0-132">데이터 백업(data backup)</span><span class="sxs-lookup"><span data-stu-id="fbbc0-132">data backup</span></span>  
 <span data-ttu-id="fbbc0-133">전체 데이터베이스(데이터베이스 백업), 부분 데이터베이스(부분 백업) 또는 파일 집합이나 파일 그룹(파일 백업)의 데이터 백업입니다.</span><span class="sxs-lookup"><span data-stu-id="fbbc0-133">A backup of data in a complete database (a database backup), a partial database ( a partial backup), or a set of data files or filegroups (a file backup).</span></span>  
  
 <span data-ttu-id="fbbc0-134">데이터베이스 백업(database backup)</span><span class="sxs-lookup"><span data-stu-id="fbbc0-134">database backup</span></span>  
 <span data-ttu-id="fbbc0-135">데이터베이스 백업입니다.</span><span class="sxs-lookup"><span data-stu-id="fbbc0-135">A backup of a database.</span></span> <span data-ttu-id="fbbc0-136">전체 데이터베이스 백업은 백업이 완료된 시점의 전체 데이터베이스를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="fbbc0-136">Full database backups represent the whole database at the time the backup finished.</span></span> <span data-ttu-id="fbbc0-137">차등 데이터베이스 백업은 가장 최근의 전체 데이터베이스 백업 이후에 데이터베이스에 수행된 변경 내용만 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="fbbc0-137">Differential database backups contain only changes made to the database since its most recent full database backup.</span></span>  
  
 <span data-ttu-id="fbbc0-138">차등 백업(differential backup)</span><span class="sxs-lookup"><span data-stu-id="fbbc0-138">differential backup</span></span>  
 <span data-ttu-id="fbbc0-139">전체 또는 부분 데이터베이스, 데이터 파일 집합 또는 파일 그룹(차등 기반)에 대한 최신 전체 백업을 기반으로 하고, 해당 기준 이후에 변경된 데이터만 포함하는 데이터 백업입니다.</span><span class="sxs-lookup"><span data-stu-id="fbbc0-139">A data backup that is based on the latest full backup of a complete or partial database or a set of data files or filegroups (the differential base) and that contains only the data that has changed since that base.</span></span>  
  
 <span data-ttu-id="fbbc0-140">전체 백업(full backup)</span><span class="sxs-lookup"><span data-stu-id="fbbc0-140">full backup</span></span>  
 <span data-ttu-id="fbbc0-141">특정 데이터베이스나 파일 그룹 또는 파일 집합에 있는 모든 데이터와 그러한 데이터를 복구할 수 있을 만큼의 로그를 포함하는 데이터 백업입니다.</span><span class="sxs-lookup"><span data-stu-id="fbbc0-141">A data backup that contains all the data in a specific database or set of filegroups or files, and also enough log to allow for recovering that data.</span></span>  
  
 <span data-ttu-id="fbbc0-142">로그 백업(log backup)</span><span class="sxs-lookup"><span data-stu-id="fbbc0-142">log backup</span></span>  
 <span data-ttu-id="fbbc0-143">이전 로그 백업에서 백업되지 않은 모든 로그 레코드를 포함하는 트랜잭션 로그 백업입니다.</span><span class="sxs-lookup"><span data-stu-id="fbbc0-143">A backup of transaction logs that includes all log records that were not backed up in a previous log backup.</span></span> <span data-ttu-id="fbbc0-144">(전체 복구 모델)</span><span class="sxs-lookup"><span data-stu-id="fbbc0-144">(full recovery model)</span></span>  
  
 <span data-ttu-id="fbbc0-145">recover</span><span class="sxs-lookup"><span data-stu-id="fbbc0-145">recover</span></span>  
 <span data-ttu-id="fbbc0-146">데이터베이스를 안정적이고 일관된 상태로 되돌립니다.</span><span class="sxs-lookup"><span data-stu-id="fbbc0-146">To return a database to a stable and consistent state.</span></span>  
  
 <span data-ttu-id="fbbc0-147">recovery</span><span class="sxs-lookup"><span data-stu-id="fbbc0-147">recovery</span></span>  
 <span data-ttu-id="fbbc0-148">데이터베이스를 일관된 트랜잭션 상태로 가져오는 데이터베이스 시작 단계 또는 restore with recovery 단계입니다.</span><span class="sxs-lookup"><span data-stu-id="fbbc0-148">A phase of database startup or of a restore with recovery that brings the database into a transaction-consistent state.</span></span>  
  
 <span data-ttu-id="fbbc0-149">복구 모델</span><span class="sxs-lookup"><span data-stu-id="fbbc0-149">recovery model</span></span>  
 <span data-ttu-id="fbbc0-150">데이터베이스에서 트랜잭션 로그 유지 관리를 제어하는 데이터베이스 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="fbbc0-150">A database property that controls transaction log maintenance on a database.</span></span> <span data-ttu-id="fbbc0-151">사용할 수 있는 복구 모델은 3가지로 단순, 전체 및 대량 로그 복구 모델입니다.</span><span class="sxs-lookup"><span data-stu-id="fbbc0-151">Three recovery models exist: simple, full, and bulk-logged.</span></span> <span data-ttu-id="fbbc0-152">데이터베이스의 복구 모델에 따라 백업 및 복원 요구 사항이 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="fbbc0-152">The recovery model of database determines its backup and restore requirements.</span></span>  
  
 <span data-ttu-id="fbbc0-153">복원</span><span class="sxs-lookup"><span data-stu-id="fbbc0-153">restore</span></span>  
 <span data-ttu-id="fbbc0-154">지정된 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 백업에서 지정된 데이터베이스로 모든 데이터 및 로그 페이지를 복사하고 기록된 변경 사항을 적용하여 데이터를 최신 상태로 전환함으로써 백업에 기록된 모든 트랜잭션을 롤포워드하는 다단계 프로세스입니다.</span><span class="sxs-lookup"><span data-stu-id="fbbc0-154">A multi-phase process that copies all the data and log pages from a specified [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backup to a specified database, and then rolls forward all the transactions that are logged in the backup by applying logged changes to bring the data forward in time.</span></span>  
  

  
##  <a name="introduction-to-backup-and-restore-strategies"></a><a name="BnrStrategies"></a><span data-ttu-id="fbbc0-155">백업 및 복원 전략 소개</span><span class="sxs-lookup"><span data-stu-id="fbbc0-155">Introduction to Backup and Restore Strategies</span></span>  
 <span data-ttu-id="fbbc0-156">데이터 백업 및 복원은 특정 환경에 맞게 사용자 지정되어야 하며 적절한 리소스도 마련되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fbbc0-156">Backing up and restoring data must be customized to a particular environment and must work with the available resources.</span></span> <span data-ttu-id="fbbc0-157">따라서 복구를 위해 백업 및 복원을 안정적으로 사용하려면 백업 및 복원 전략이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="fbbc0-157">Therefore, a reliable use of backup and restore for recovery requires a backup and restore strategy.</span></span> <span data-ttu-id="fbbc0-158">잘 디자인된 백업 및 복원 전략은 사용자의 특정 비즈니스 요구 사항을 감안해 데이터 가용성을 극대화하고 데이터 손실을 최소화합니다.</span><span class="sxs-lookup"><span data-stu-id="fbbc0-158">A well-designed backup and restore strategy maximizes data availability and minimizes data loss, while considering your particular business requirements.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="fbbc0-159">데이터베이스와 백업을 서로 다른 디바이스에 배치하십시오.</span><span class="sxs-lookup"><span data-stu-id="fbbc0-159">Place the database and backups on separate devices.</span></span> <span data-ttu-id="fbbc0-160">그렇지 않으면 데이터베이스가 들어 있는 디바이스가 실패할 경우 백업을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="fbbc0-160">Otherwise, if the device containing the database fails, your backups will be unavailable.</span></span> <span data-ttu-id="fbbc0-161">데이터와 백업을 서로 다른 디바이스에 배치하면 백업 작성 및 데이터베이스의 프로덕션 사용에 대한 I/O 성능도 향상됩니다.</span><span class="sxs-lookup"><span data-stu-id="fbbc0-161">Placing the data and backups on separate devices also enhances the I/O performance for both writing backups and the production use of the database.</span></span>  
  
 <span data-ttu-id="fbbc0-162">백업 및 복원 전략은 백업에 관련된 부분과 복원에 관련된 부분으로 이루어집니다.</span><span class="sxs-lookup"><span data-stu-id="fbbc0-162">A backup and restore strategy contains a backup portion and a restore portion.</span></span> <span data-ttu-id="fbbc0-163">전략의 백업 관련 부분에서는 백업 유형 및 빈도, 백업에 필요한 하드웨어의 특성 및 속도, 백업 테스트 방법 및 백업 미디어 보관 위치 및 보관 방법(보안 고려 사항 포함)을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="fbbc0-163">The backup part of the strategy defines the type and frequency of backups, the nature and speed of the hardware that is required for them, how backups are to be tested, and where and how backup media is to be stored (including security considerations).</span></span> <span data-ttu-id="fbbc0-164">전략의 복원 관련 부분에서는 누가 복원을 담당할 것이며 어떻게 데이터베이스 가용성 목표를 충족시키고 데이터 손실을 최소화할 것인가를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="fbbc0-164">The restore part of the strategy defines who is responsible for performing restores and how restores should be performed to meet your goals for availability of the database and for minimizing data loss.</span></span> <span data-ttu-id="fbbc0-165">백업 및 복원 절차를 문서화하고 실행 문서에 사본을 보관하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="fbbc0-165">We recommend that you document your backup and restore procedures and keep a copy of the documentation in your run book.</span></span>  
  
 <span data-ttu-id="fbbc0-166">효과적인 백업 및 복원 전략 설계를 위해서는 신중한 계획, 구현 및 테스트가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="fbbc0-166">Designing an effective backup and restore strategy requires careful planning, implementation, and testing.</span></span> <span data-ttu-id="fbbc0-167">테스트는 반드시 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="fbbc0-167">Testing is required.</span></span> <span data-ttu-id="fbbc0-168">복원 전략에 포함된 모든 조합의 백업을 성공적으로 복원해야만 백업 전략을 갖추게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fbbc0-168">You do not have a backup strategy until you have successfully restored backups in all the combinations that are included in your restore strategy.</span></span> <span data-ttu-id="fbbc0-169">다음과 같은 다양한 요소를</span><span class="sxs-lookup"><span data-stu-id="fbbc0-169">You must consider a variety of factors.</span></span> <span data-ttu-id="fbbc0-170">여기에는 다음과 같은 옵션이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="fbbc0-170">These include the following:</span></span>  
  
-   <span data-ttu-id="fbbc0-171">데이터베이스에 대한 사용자 조직의 생산성 목표(특히 가용성 및 데이터 손실 방지 요구 사항)</span><span class="sxs-lookup"><span data-stu-id="fbbc0-171">The production goals of your organization for the databases, especially the requirements for availability and protection of data from loss.</span></span>  
  
-   <span data-ttu-id="fbbc0-172">크기, 사용 패턴, 내용의 특성, 데이터 요구 사항 등과 같은 각 데이터베이스의 특성</span><span class="sxs-lookup"><span data-stu-id="fbbc0-172">The nature of each of your databases: its size, its usage patterns, the nature of its content, the requirements for its data, and so on.</span></span>  
  
-   <span data-ttu-id="fbbc0-173">하드웨어, 인력, 백업 미디어 저장 공간, 저장된 미디어의 물리적 보안 등과 같은 리소스의 제약 요건</span><span class="sxs-lookup"><span data-stu-id="fbbc0-173">Constraints on resources, such as: hardware, personnel, space for storing backup media, the physical security of the stored media, and so on.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="fbbc0-174">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 디스크상 스토리지 형식은 64비트 및 32비트 환경에서 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="fbbc0-174">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on-disk storage format is the same in the 64-bit and 32-bit environments.</span></span> <span data-ttu-id="fbbc0-175">따라서 32비트 및 64비트 환경에서 백업 및 복원 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fbbc0-175">Therefore, backup and restore work across 32-bit and 64-bit environments.</span></span> <span data-ttu-id="fbbc0-176">한 환경에서 실행 중인 서버 인스턴스에서 만든 백업을 다른 환경에서 실행하는 서버 인스턴스에서 복원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fbbc0-176">A backup created on a server instance running in one environment can be restored on a server instance that runs in the other environment.</span></span>  
  

  
### <a name="impact-of-the-recovery-model-on-backup-and-restore"></a><span data-ttu-id="fbbc0-177">백업 및 복원에 대한 복구 모델의 영향</span><span class="sxs-lookup"><span data-stu-id="fbbc0-177">Impact of the Recovery Model on Backup and Restore</span></span>  
 <span data-ttu-id="fbbc0-178">백업 및 복원 작업은 복구 모델의 컨텍스트에서 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="fbbc0-178">Backup and restore operations occur within the context of a recovery model.</span></span> <span data-ttu-id="fbbc0-179">복구 모델은 트랜잭션 로그의 관리 방법을 제어하는 데이터베이스 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="fbbc0-179">A recovery model is a database property that controls how the transaction log is managed.</span></span> <span data-ttu-id="fbbc0-180">또한 데이터베이스의 복구 모델은 데이터베이스에 지원되는 복원 시나리오 및 백업 유형을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="fbbc0-180">Also, the recovery model of a database determines what types of backups and what restore scenarios are supported for the database.</span></span> <span data-ttu-id="fbbc0-181">일반적으로 데이터베이스는 단순 복구 모델 또는 전체 복구 모델 모두 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="fbbc0-181">Typically a database uses either the simple recovery model or the full recovery model.</span></span> <span data-ttu-id="fbbc0-182">전체 복구 모델은 대량 작업 이전에 대량 로그 복구 모델로 전환하여 보완될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fbbc0-182">The full recovery model can be supplemented by switching to the bulk-logged recovery model before bulk operations.</span></span> <span data-ttu-id="fbbc0-183">이러한 복구 모델 및 이러한 복구 모델이 트랜잭션 로그 관리에 미치는 영향에 대한 자세한 내용은 [트랜잭션 로그&#40;SQL Server&#41;](../logs/the-transaction-log-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fbbc0-183">For an introduction to these recovery models and how they affect transaction log management, see [The Transaction Log &#40;SQL Server&#41;](../logs/the-transaction-log-sql-server.md).</span></span>  
  
 <span data-ttu-id="fbbc0-184">데이터베이스에 가장 적합한 복구 모델은 비즈니스 요구 사항에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="fbbc0-184">The best choice of recovery model for the database depends on your business requirements.</span></span> <span data-ttu-id="fbbc0-185">트랜잭션 로그 관리를 방지하고 백업 및 복원을 단순화하려면 단순 복구 모델을 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="fbbc0-185">To avoid transaction log management and simplify backup and restore, use the simple recovery model.</span></span> <span data-ttu-id="fbbc0-186">관리 오버헤드가 증가하더라도 작업 손실 가능성을 최소화하려면 전체 복구 모델을 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="fbbc0-186">To minimize work-loss exposure, at the cost of administrative overhead, use the full recovery model.</span></span> <span data-ttu-id="fbbc0-187">백업 및 복원에 미치는 복구 모델의 영향에 대한 자세한 내용은 [백업 개요&#40;SQL Server&#41;](backup-overview-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fbbc0-187">For information about the effect of recovery models on backup and restore, see [Backup Overview &#40;SQL Server&#41;](backup-overview-sql-server.md).</span></span>  
  
### <a name="design-the-backup-strategy"></a><span data-ttu-id="fbbc0-188">백업 전략 디자인</span><span class="sxs-lookup"><span data-stu-id="fbbc0-188">Design the Backup Strategy</span></span>  
 <span data-ttu-id="fbbc0-189">지정한 데이터베이스에 대해 비즈니스 요구 사항에 맞는 복구 모델을 선택한 후에는 해당 백업 전략을 계획 및 구현해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fbbc0-189">After you have selected a recovery model that meets your business requirements for a specific database, you have to plan and implement a corresponding backup strategy.</span></span> <span data-ttu-id="fbbc0-190">백업 전략을 최적화하는 요소는 다양합니다. 그 중에서도 특히 다음과 같은 요소에 의해 주로 영향을 받습니다.</span><span class="sxs-lookup"><span data-stu-id="fbbc0-190">The optimal backup strategy depends on a variety of factors, of which the following are especially significant:</span></span>  
  
-   <span data-ttu-id="fbbc0-191">애플리케이션이 하루에 몇 시간 데이터베이스에 액세스해야 합니까?</span><span class="sxs-lookup"><span data-stu-id="fbbc0-191">How many hours a day do applications have to access the database?</span></span>  
  
     <span data-ttu-id="fbbc0-192">사용량이 적은 기간을 예측할 수 있는 경우 해당 기간에 전체 데이터베이스 백업을 예약하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="fbbc0-192">If there is a predictable off-peak period, we recommend that you schedule full database backups for that period.</span></span>  
  
-   <span data-ttu-id="fbbc0-193">얼마나 자주 변경과 업데이트가 발생합니까?</span><span class="sxs-lookup"><span data-stu-id="fbbc0-193">How frequently are changes and updates likely to occur?</span></span>  
  
     <span data-ttu-id="fbbc0-194">자주 변경하는 경우 다음을 고려하십시오.</span><span class="sxs-lookup"><span data-stu-id="fbbc0-194">If changes are frequent, consider the following:</span></span>  
  
    -   <span data-ttu-id="fbbc0-195">단순 복구 모델에서는 전체 데이터베이스 백업 사이에 차등 백업을 예약하십시오.</span><span class="sxs-lookup"><span data-stu-id="fbbc0-195">Under the simple recovery model, consider scheduling differential backups between full database backups.</span></span> <span data-ttu-id="fbbc0-196">차등 백업은 마지막 전체 데이터베이스 백업 이후의 변경 내용만 캡처합니다.</span><span class="sxs-lookup"><span data-stu-id="fbbc0-196">A differential backup captures only the changes since the last full database backup.</span></span>  
  
    -   <span data-ttu-id="fbbc0-197">전체 복구 모델에서는 자주 로그 백업을 예약해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fbbc0-197">Under the full recovery model, you should schedule frequent log backups.</span></span> <span data-ttu-id="fbbc0-198">전체 백업 사이에 차등 백업을 예약하면 데이터를 복원한 후 복원해야 하는 로그 백업 수가 감소하므로 복원 시간이 줄어들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fbbc0-198">Scheduling differential backups between full backups can reduce restore time by reducing the number of log backups you have to restore after restoring the data.</span></span>  
  
-   <span data-ttu-id="fbbc0-199">변경이 데이터베이스의 일부분에서만 발생합니까? 아니면 데이터베이스의 대부분에서 발생합니까?</span><span class="sxs-lookup"><span data-stu-id="fbbc0-199">Are changes likely to occur in only a small part of the database or in a large part of the database?</span></span>  
  
     <span data-ttu-id="fbbc0-200">변경 내용이 파일 또는 파일 그룹의 일부분에만 집중되어 있는 큰 데이터베이스의 경우 부분 백업이나 파일 백업이 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fbbc0-200">For a large database in which changes are concentrated in a part of the files or filegroups, partial backups and or file backups can be useful.</span></span> <span data-ttu-id="fbbc0-201">자세한 내용은 [부분 백업&#40;SQL Server&#41;](partial-backups-sql-server.md) 및 [전체 파일 백업&#40;SQL Server&#41;](full-file-backups-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fbbc0-201">For more information, see [Partial Backups &#40;SQL Server&#41;](partial-backups-sql-server.md) and [Full File Backups &#40;SQL Server&#41;](full-file-backups-sql-server.md).</span></span>  
  
-   <span data-ttu-id="fbbc0-202">전체 데이터베이스 백업에 필요한 디스크 공간은 어느 정도입니까?</span><span class="sxs-lookup"><span data-stu-id="fbbc0-202">How much disk space will a full database backup require?</span></span>  
  
     <span data-ttu-id="fbbc0-203">자세한 내용은 이 항목의 뒷부분에 나오는 [전체 데이터베이스 백업의 크기 예측](#EstimateDbBuSize)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="fbbc0-203">For more information, see [Estimating the Size of a Full Database Backup](#EstimateDbBuSize), later in this section.</span></span>  
  
####  <a name="estimate-the-size-of-a-full-database-backup"></a><a name="EstimateDbBuSize"></a><span data-ttu-id="fbbc0-204">전체 데이터베이스 백업의 크기 예측</span><span class="sxs-lookup"><span data-stu-id="fbbc0-204">Estimate the Size of a Full Database Backup</span></span>  
 <span data-ttu-id="fbbc0-205">백업 및 복원을 구현하기 전에 전체 데이터베이스 백업에 어느 정도의 디스크 공간이 필요한지 예측해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fbbc0-205">Before you implement a backup and restore strategy, you should estimate how much disk space a full database backup will use.</span></span> <span data-ttu-id="fbbc0-206">백업 작업은 데이터베이스의 데이터를 백업 파일로 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="fbbc0-206">The backup operation copies the data in the database to the backup file.</span></span> <span data-ttu-id="fbbc0-207">백업에는 데이터베이스의 실제 데이터만 포함되고 사용하지 않은 공간은 포함되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fbbc0-207">The backup contains only the actual data in the database and not any unused space.</span></span> <span data-ttu-id="fbbc0-208">따라서 백업은 일반적으로 데이터베이스 자체의 크기보다 작습니다.</span><span class="sxs-lookup"><span data-stu-id="fbbc0-208">Therefore, the backup is usually smaller than the database itself.</span></span> <span data-ttu-id="fbbc0-209">**sp_spaceused** 시스템 저장 프로시저를 사용하여 전체 데이터베이스 백업의 크기를 예측할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fbbc0-209">You can estimate the size of a full database backup by using the **sp_spaceused** system stored procedure.</span></span> <span data-ttu-id="fbbc0-210">자세한 내용은 [sp_spaceused&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-spaceused-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fbbc0-210">For more information, see [sp_spaceused &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-spaceused-transact-sql).</span></span>  
  
### <a name="schedule-backups"></a><span data-ttu-id="fbbc0-211">백업 예약</span><span class="sxs-lookup"><span data-stu-id="fbbc0-211">Schedule Backups</span></span>  
 <span data-ttu-id="fbbc0-212">백업 작업을 수행해도 실행 중인 트랜잭션에는 큰 영향을 미치지 않으므로 일반 작업을 수행할 때도 백업 작업을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fbbc0-212">Performing a backup operation has minimal effect on transactions that are running; therefore, backup operations can be run during regular operations.</span></span> <span data-ttu-id="fbbc0-213">프로덕션 작업에 거의 영향을 주지 않고 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 백업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fbbc0-213">You can perform a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backup with minimal effect on production workloads.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fbbc0-214">백업 중 동시성 제한 사항에 대한 자세한 내용은 [백업 개요&#40;SQL Server&#41;](backup-overview-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fbbc0-214">For information about concurrency restrictions during backup, see [Backup Overview &#40;SQL Server&#41;](backup-overview-sql-server.md).</span></span>  
  
 <span data-ttu-id="fbbc0-215">각 경우에 필요한 백업 유형과 수행 빈도를 결정한 후 데이터베이스 유지 관리 계획의 일부로 데이터베이스에 대한 정기 백업을 예약하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="fbbc0-215">After you decide what types of backups you require and how frequently you have to perform each type, we recommend that you schedule regular backups as part of a database maintenance plan for the database.</span></span> <span data-ttu-id="fbbc0-216">유지 관리 계획에 대한 정보와 데이터베이스 백업 및 로그 백업에 대한 유지 관리 계획을 만드는 방법은 [Use the Maintenance Plan Wizard](../maintenance-plans/use-the-maintenance-plan-wizard.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="fbbc0-216">For information about maintenance plans and how to create them for database backups and log backups, see [Use the Maintenance Plan Wizard](../maintenance-plans/use-the-maintenance-plan-wizard.md).</span></span>  
  
### <a name="test-your-backups"></a><span data-ttu-id="fbbc0-217">백업 테스트</span><span class="sxs-lookup"><span data-stu-id="fbbc0-217">Test Your Backups</span></span>  
 <span data-ttu-id="fbbc0-218">백업을 테스트해야만 복원 전략을 갖추게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fbbc0-218">You do not have a restore strategy until you have tested your backups.</span></span> <span data-ttu-id="fbbc0-219">데이터베이스 복사본을 테스트 시스템으로 복원하여 각 데이터베이스에 대한 백업 전략을 철저히 테스트하는 것이 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="fbbc0-219">It is very important to thoroughly test your backup strategy for each of your databases by restoring a copy of the database onto a test system.</span></span> <span data-ttu-id="fbbc0-220">사용할 모든 유형의 백업 복원을 테스트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fbbc0-220">You must test restoring every type of backup that you intend to use.</span></span>  
  
 <span data-ttu-id="fbbc0-221">각 데이터베이스에 대한 작업 매뉴얼을 작성하여 관리하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="fbbc0-221">We recommend that you maintain an operations manual for each database.</span></span> <span data-ttu-id="fbbc0-222">이 작업 매뉴얼에는 백업 위치, 백업 디바이스 이름(있는 경우) 및 테스트 백업을 복원하는 데 필요한 시간 등이 수록되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fbbc0-222">This operations manual should document the location of the backups, backup device names (if any), and the amount of time that is required to restore the test backups.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="fbbc0-223">관련 작업</span><span class="sxs-lookup"><span data-stu-id="fbbc0-223">Related Tasks</span></span>  
  
### <a name="scheduling-backup-jobs"></a><span data-ttu-id="fbbc0-224">백업 작업 예약</span><span class="sxs-lookup"><span data-stu-id="fbbc0-224">Scheduling Backup Jobs</span></span>  
  
-   [<span data-ttu-id="fbbc0-225">유지 관리 계획 만들기</span><span class="sxs-lookup"><span data-stu-id="fbbc0-225">Create a Maintenance Plan</span></span>](../maintenance-plans/create-a-maintenance-plan.md)  
  
-   [<span data-ttu-id="fbbc0-226">작업 만들기</span><span class="sxs-lookup"><span data-stu-id="fbbc0-226">Create a Job</span></span>](../../ssms/agent/create-a-job.md)  
  
-   [<span data-ttu-id="fbbc0-227">작업 예약</span><span class="sxs-lookup"><span data-stu-id="fbbc0-227">Schedule a Job</span></span>](../../ssms/agent/schedule-a-job.md)  
  
### <a name="working-with-backup-devices-and-backup-media"></a><span data-ttu-id="fbbc0-228">백업 디바이스 및 백업 미디어 사용</span><span class="sxs-lookup"><span data-stu-id="fbbc0-228">Working with Backup Devices and Backup Media</span></span>  
  
-   [<span data-ttu-id="fbbc0-229">디스크 파일에 대한 논리적 백업 디바이스 정의&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="fbbc0-229">Define a Logical Backup Device for a Disk File &#40;SQL Server&#41;</span></span>](define-a-logical-backup-device-for-a-disk-file-sql-server.md)  
  
-   [<span data-ttu-id="fbbc0-230">테이프 드라이브에 대한 논리적 백업 디바이스 정의&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="fbbc0-230">Define a Logical Backup Device for a Tape Drive &#40;SQL Server&#41;</span></span>](define-a-logical-backup-device-for-a-tape-drive-sql-server.md)  
  
-   [<span data-ttu-id="fbbc0-231">디스크 또는 테이프를 백업 대상으로 지정&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="fbbc0-231">Specify a Disk or Tape As a Backup Destination &#40;SQL Server&#41;</span></span>](specify-a-disk-or-tape-as-a-backup-destination-sql-server.md)  
  
-   [<span data-ttu-id="fbbc0-232">백업 디바이스 삭제&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="fbbc0-232">Delete a Backup Device &#40;SQL Server&#41;</span></span>](delete-a-backup-device-sql-server.md)  
  
-   [<span data-ttu-id="fbbc0-233">백업의 만료 날짜 설정&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="fbbc0-233">Set the Expiration Date on a Backup &#40;SQL Server&#41;</span></span>](set-the-expiration-date-on-a-backup-sql-server.md)  
  
-   [<span data-ttu-id="fbbc0-234">백업 테이프 또는 파일의 내용 보기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="fbbc0-234">View the Contents of a Backup Tape or File &#40;SQL Server&#41;</span></span>](view-the-contents-of-a-backup-tape-or-file-sql-server.md)  
  
-   [<span data-ttu-id="fbbc0-235">백업 세트의 데이터와 로그 파일 보기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="fbbc0-235">View the Data and Log Files in a Backup Set &#40;SQL Server&#41;</span></span>](view-the-data-and-log-files-in-a-backup-set-sql-server.md)  
  
-   [<span data-ttu-id="fbbc0-236">논리적 백업 디바이스의 속성 및 내용 보기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="fbbc0-236">View the Properties and Contents of a Logical Backup Device &#40;SQL Server&#41;</span></span>](view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md)  
  
-   [<span data-ttu-id="fbbc0-237">디바이스에서 백업 복원&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="fbbc0-237">Restore a Backup from a Device &#40;SQL Server&#41;</span></span>](restore-a-backup-from-a-device-sql-server.md)  
  
### <a name="creating-backups"></a><span data-ttu-id="fbbc0-238">백업 만들기</span><span class="sxs-lookup"><span data-stu-id="fbbc0-238">Creating Backups</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fbbc0-239">부분 또는 복사 전용 백업의 경우 각각 PARTIAL 또는 COPY_ONLY 옵션과 함께 [!INCLUDE[tsql](../../includes/tsql-md.md)][BACKUP](/sql/t-sql/statements/backup-transact-sql) 문을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fbbc0-239">For partial or copy-only backups, you must use the [!INCLUDE[tsql](../../includes/tsql-md.md)][BACKUP](/sql/t-sql/statements/backup-transact-sql) statement with the PARTIAL or COPY_ONLY option, respectively.</span></span>  
  
 <span data-ttu-id="fbbc0-240">**SQL Server Management Studio 사용**</span><span class="sxs-lookup"><span data-stu-id="fbbc0-240">**Using SQL Server Management Studio**</span></span>  
  
-   [<span data-ttu-id="fbbc0-241">전체 데이터베이스 백업 만들기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="fbbc0-241">Create a Full Database Backup &#40;SQL Server&#41;</span></span>](create-a-full-database-backup-sql-server.md)  
  
-   [<span data-ttu-id="fbbc0-242">트랜잭션 로그 백업&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="fbbc0-242">Back Up a Transaction Log &#40;SQL Server&#41;</span></span>](back-up-a-transaction-log-sql-server.md)  
  
-   [<span data-ttu-id="fbbc0-243">파일 및 파일 그룹 백업&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="fbbc0-243">Back Up Files and Filegroups &#40;SQL Server&#41;</span></span>](back-up-files-and-filegroups-sql-server.md)  
  
-   [<span data-ttu-id="fbbc0-244">차등 데이터베이스 백업 만들기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="fbbc0-244">Create a Differential Database Backup &#40;SQL Server&#41;</span></span>](create-a-differential-database-backup-sql-server.md)  
  
 <span data-ttu-id="fbbc0-245">**Transact-SQL 사용**</span><span class="sxs-lookup"><span data-stu-id="fbbc0-245">**Using Transact-SQL**</span></span>  
  
-   [<span data-ttu-id="fbbc0-246">Resource Governor를 사용하여 백업 압축을 통해 CPU 사용량 제한&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="fbbc0-246">Use Resource Governor to Limit CPU Usage by Backup Compression &#40;Transact-SQL&#41;</span></span>](use-resource-governor-to-limit-cpu-usage-by-backup-compression-transact-sql.md)  
  
-   [<span data-ttu-id="fbbc0-247">데이터베이스가 손상된 경우 트랜잭션 로그 백업&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="fbbc0-247">Back Up the Transaction Log When the Database Is Damaged &#40;SQL Server&#41;</span></span>](back-up-the-transaction-log-when-the-database-is-damaged-sql-server.md)  
  
-   [<span data-ttu-id="fbbc0-248">백업 또는 복원 중 백업 체크섬 설정 또는 해제&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="fbbc0-248">Enable or Disable Backup Checksums During Backup or Restore &#40;SQL Server&#41;</span></span>](enable-or-disable-backup-checksums-during-backup-or-restore-sql-server.md)  
  
-   [<span data-ttu-id="fbbc0-249">오류 발생 후 백업 또는 복원 작업 계속 또는 중지 여부 지정&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="fbbc0-249">Specify Whether a Backup or Restore Operation Continues or Stops After Encountering an Error &#40;SQL Server&#41;</span></span>](specify-if-backup-or-restore-continues-or-stops-after-error.md)  
  

  
### <a name="restoring-data-backups"></a><span data-ttu-id="fbbc0-250">데이터 백업 복원</span><span class="sxs-lookup"><span data-stu-id="fbbc0-250">Restoring Data Backups</span></span>  
 <span data-ttu-id="fbbc0-251">**SQL Server Management Studio 사용**</span><span class="sxs-lookup"><span data-stu-id="fbbc0-251">**Using SQL Server Management Studio**</span></span>  
  
-   [<span data-ttu-id="fbbc0-252">데이터베이스 백업 복원 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="fbbc0-252">Restore a Database Backup &#40;SQL Server Management Studio&#41;</span></span>](restore-a-database-backup-using-ssms.md)  
  
-   [<span data-ttu-id="fbbc0-253">데이터베이스를 새 위치로 복원&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="fbbc0-253">Restore a Database to a New Location &#40;SQL Server&#41;</span></span>](restore-a-database-to-a-new-location-sql-server.md)  
  
-   [<span data-ttu-id="fbbc0-254">차등 데이터베이스 백업 복원&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="fbbc0-254">Restore a Differential Database Backup &#40;SQL Server&#41;</span></span>](restore-a-differential-database-backup-sql-server.md)  
  
-   [<span data-ttu-id="fbbc0-255">파일 및 파일 그룹 복원&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="fbbc0-255">Restore Files and Filegroups &#40;SQL Server&#41;</span></span>](restore-files-and-filegroups-sql-server.md)  
  
 <span data-ttu-id="fbbc0-256">**Transact-SQL 사용**</span><span class="sxs-lookup"><span data-stu-id="fbbc0-256">**Using Transact-SQL**</span></span>  
  
-   [<span data-ttu-id="fbbc0-257">단순 복구 모델에서 데이터베이스 백업 복원&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="fbbc0-257">Restore a Database Backup Under the Simple Recovery Model &#40;Transact-SQL&#41;</span></span>](restore-a-database-backup-under-the-simple-recovery-model-transact-sql.md)  
  
-   [<span data-ttu-id="fbbc0-258">전체 복구 모델에서 특정 오류 지점으로 데이터베이스 복원&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="fbbc0-258">Restore a Database to the Point of Failure Under the Full Recovery Model &#40;Transact-SQL&#41;</span></span>](restore-database-to-point-of-failure-full-recovery.md)  
  
-   [<span data-ttu-id="fbbc0-259">기존 파일에서 파일 및 파일 그룹 복원&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="fbbc0-259">Restore Files and Filegroups over Existing Files &#40;SQL Server&#41;</span></span>](restore-files-and-filegroups-over-existing-files-sql-server.md)  
  
-   [<span data-ttu-id="fbbc0-260">새 위치로 파일 복원&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="fbbc0-260">Restore Files to a New Location &#40;SQL Server&#41;</span></span>](restore-files-to-a-new-location-sql-server.md)  
  
-   [<span data-ttu-id="fbbc0-261">master 데이터베이스 복원&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="fbbc0-261">Restore the master Database &#40;Transact-SQL&#41;</span></span>](restore-the-master-database-transact-sql.md)  
  

  
### <a name="restoring-transaction-logs-full-recovery-model"></a><span data-ttu-id="fbbc0-262">트랜잭션 로그 복원(전체 복구 모델)</span><span class="sxs-lookup"><span data-stu-id="fbbc0-262">Restoring Transaction Logs (Full Recovery Model)</span></span>  
 <span data-ttu-id="fbbc0-263">**SQL Server Management Studio 사용**</span><span class="sxs-lookup"><span data-stu-id="fbbc0-263">**Using SQL Server Management Studio**</span></span>  
  
-   [<span data-ttu-id="fbbc0-264">데이터베이스를 표시된 트랜잭션으로 복원&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="fbbc0-264">Restore a Database to a Marked Transaction &#40;SQL Server Management Studio&#41;</span></span>](restore-a-database-to-a-marked-transaction-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="fbbc0-265">트랜잭션 로그 백업 복원&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="fbbc0-265">Restore a Transaction Log Backup &#40;SQL Server&#41;</span></span>](restore-a-transaction-log-backup-sql-server.md)  
  
-   [<span data-ttu-id="fbbc0-266">SQL Server 데이터베이스를 지정 시간으로 복원&#40;전체 복구 모델&#41;</span><span class="sxs-lookup"><span data-stu-id="fbbc0-266">Restore a SQL Server Database to a Point in Time &#40;Full Recovery Model&#41;</span></span>](restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md)  
  
 <span data-ttu-id="fbbc0-267">**Transact-SQL 사용**</span><span class="sxs-lookup"><span data-stu-id="fbbc0-267">**Using Transact-SQL**</span></span>  
  
-   [<span data-ttu-id="fbbc0-268">SQL Server 데이터베이스를 지정 시간으로 복원&#40;전체 복구 모델&#41;</span><span class="sxs-lookup"><span data-stu-id="fbbc0-268">Restore a SQL Server Database to a Point in Time &#40;Full Recovery Model&#41;</span></span>](restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md)  
  

  
### <a name="additional-restore-tasks"></a><span data-ttu-id="fbbc0-269">추가 복원 태스크</span><span class="sxs-lookup"><span data-stu-id="fbbc0-269">Additional Restore Tasks</span></span>  
 <span data-ttu-id="fbbc0-270">**Transact-SQL 사용**</span><span class="sxs-lookup"><span data-stu-id="fbbc0-270">**Using Transact-SQL**</span></span>  
  
-   [<span data-ttu-id="fbbc0-271">중단된 복원 작업 다시 시작&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="fbbc0-271">Restart an Interrupted Restore Operation &#40;Transact-SQL&#41;</span></span>](restart-an-interrupted-restore-operation-transact-sql.md)  
  
-   [<span data-ttu-id="fbbc0-272">데이터를 복원하지 않고 데이터베이스 복구&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="fbbc0-272">Recover a Database Without Restoring Data &#40;Transact-SQL&#41;</span></span>](recover-a-database-without-restoring-data-transact-sql.md)  
  

  
## <a name="see-also"></a><span data-ttu-id="fbbc0-273">참고 항목</span><span class="sxs-lookup"><span data-stu-id="fbbc0-273">See Also</span></span>  
 <span data-ttu-id="fbbc0-274">[백업 개요&#40;SQL Server&#41;](backup-overview-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="fbbc0-274">[Backup Overview &#40;SQL Server&#41;](backup-overview-sql-server.md) </span></span>  
 <span data-ttu-id="fbbc0-275">[복원 및 복구 개요&#40;SQL Server&#41;](restore-and-recovery-overview-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="fbbc0-275">[Restore and Recovery Overview &#40;SQL Server&#41;](restore-and-recovery-overview-sql-server.md) </span></span>  
 <span data-ttu-id="fbbc0-276">[BACKUP&#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="fbbc0-276">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="fbbc0-277">[RESTORE&#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="fbbc0-277">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 <span data-ttu-id="fbbc0-278">[Analysis Services 데이터베이스 백업 및 복원](https://docs.microsoft.com/analysis-services/multidimensional-models/backup-and-restore-of-analysis-services-databases) </span><span class="sxs-lookup"><span data-stu-id="fbbc0-278">[Backup and Restore of Analysis Services Databases](https://docs.microsoft.com/analysis-services/multidimensional-models/backup-and-restore-of-analysis-services-databases) </span></span>  
 <span data-ttu-id="fbbc0-279">[전체 텍스트 카탈로그와 인덱스 백업 및 복원](../search/back-up-and-restore-full-text-catalogs-and-indexes.md) </span><span class="sxs-lookup"><span data-stu-id="fbbc0-279">[Back Up and Restore Full-Text Catalogs and Indexes](../search/back-up-and-restore-full-text-catalogs-and-indexes.md) </span></span>  
 <span data-ttu-id="fbbc0-280">[복제된 데이터베이스 백업 및 복원](../replication/administration/back-up-and-restore-replicated-databases.md) </span><span class="sxs-lookup"><span data-stu-id="fbbc0-280">[Back Up and Restore Replicated Databases](../replication/administration/back-up-and-restore-replicated-databases.md) </span></span>  
 <span data-ttu-id="fbbc0-281">[트랜잭션 로그&#40;SQL Server&#41;](../logs/the-transaction-log-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="fbbc0-281">[The Transaction Log &#40;SQL Server&#41;](../logs/the-transaction-log-sql-server.md) </span></span>  
 <span data-ttu-id="fbbc0-282">[복구 모델&#40;SQL Server&#41;](recovery-models-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="fbbc0-282">[Recovery Models &#40;SQL Server&#41;](recovery-models-sql-server.md) </span></span>  
 [<span data-ttu-id="fbbc0-283">미디어 세트, 미디어 패밀리 및 백업 세트&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="fbbc0-283">Media Sets, Media Families, and Backup Sets &#40;SQL Server&#41;</span></span>](media-sets-media-families-and-backup-sets-sql-server.md)  
  
  
