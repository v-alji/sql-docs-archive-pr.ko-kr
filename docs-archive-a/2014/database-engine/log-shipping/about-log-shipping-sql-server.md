---
title: 로그 전달 정보(SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- secondary servers [SQL Server]
- log shipping [SQL Server], jobs
- copy jobs [SQL Server]
- primary databases [SQL Server]
- log shipping [SQL Server], monitoring
- log shipping [SQL Server], about log shipping
- alert jobs [SQL Server]
- availability [SQL Server]
- jobs [SQL Server], log shipping
- monitor servers [SQL Server]
- restore jobs [SQL Server]
- log shipping [SQL Server]
- backup jobs [SQL Server]
- primary servers [SQL Server]
ms.assetid: 55da6b94-3a4b-4bae-850f-4bf7f6e918ca
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: cbf36e0ddd94ec0ab0a40a448e50602decfc0645
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730871"
---
# <a name="about-log-shipping-sql-server"></a><span data-ttu-id="58021-102">로그 전달 정보(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="58021-102">About Log Shipping (SQL Server)</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="58021-103">로그 전달을 사용하면 *주 서버* 인스턴스의 *주 데이터베이스* 에서 별도의 *보조 서버* 인스턴스에 있는 하나 이상의 *보조 데이터베이스* 로 트랜잭션 로그 백업을 자동으로 보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58021-103">Log shipping allows you to automatically send transaction log backups from a *primary database* on a *primary server* instance to one or more *secondary databases* on separate *secondary server* instances.</span></span> <span data-ttu-id="58021-104">트랜잭션 로그 백업은 각 보조 데이터베이스에 개별적으로 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="58021-104">The transaction log backups are applied to each of the secondary databases individually.</span></span> <span data-ttu-id="58021-105">*모니터 서버*라는 선택적인 세 번째 서버 인스턴스는 백업 및 복원 작업의 기록과 상태를 기록하고 예약된 대로 작업이 실행되지 않으면 선택적으로 경고를 발생시킵니다.</span><span class="sxs-lookup"><span data-stu-id="58021-105">An optional third server instance, known as the *monitor server*, records the history and status of backup and restore operations and, optionally, raises alerts if these operations fail to occur as scheduled.</span></span>  
  
 <span data-ttu-id="58021-106">**항목 내용:**</span><span class="sxs-lookup"><span data-stu-id="58021-106">**In this Topic:**</span></span>  
  
-   [<span data-ttu-id="58021-107">이점</span><span class="sxs-lookup"><span data-stu-id="58021-107">Benefits</span></span>](#Benefits)  
  
-   [<span data-ttu-id="58021-108">용어 및 정의</span><span class="sxs-lookup"><span data-stu-id="58021-108">Terms and Definitions</span></span>](#TermsAndDefinitions)  
  
-   [<span data-ttu-id="58021-109">로그 전달 개요</span><span class="sxs-lookup"><span data-stu-id="58021-109">Log Shipping Overview</span></span>](#ComponentsAndConcepts)  
  
-   [<span data-ttu-id="58021-110">상호 운용성</span><span class="sxs-lookup"><span data-stu-id="58021-110">Interoperability</span></span>](#Interoperability)  
  
-   [<span data-ttu-id="58021-111">관련 작업</span><span class="sxs-lookup"><span data-stu-id="58021-111">Related Tasks</span></span>](#RelatedTasks)  
  
##  <a name="benefits"></a><a name="Benefits"></a> <span data-ttu-id="58021-112">이점</span><span class="sxs-lookup"><span data-stu-id="58021-112">Benefits</span></span>  
  
-   <span data-ttu-id="58021-113">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 개별 인스턴스에서 각각 단일 주 데이터베이스와 하나 이상의 보조 데이터베이스에 대한 재해 복구 솔루션을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="58021-113">Provides a disaster-recovery solution for a single primary database and one or more secondary databases, each on a separate instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="58021-114">보조 데이터베이스에 대해 제한된 읽기 전용 액세스를 지원합니다(복원 작업 간의 간격 동안).</span><span class="sxs-lookup"><span data-stu-id="58021-114">Supports limited read-only access to secondary databases (during the interval between restore jobs).</span></span>  
  
-   <span data-ttu-id="58021-115">주 서버가 주 데이터베이스의 로그를 백업하는 시점과 보조 서버가 로그 백업을 복원(적용)해야 할 시점 사이에 사용자 지정 지연을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58021-115">Allows a user-specified delay between when the primary server backs up the log of the primary database and when the secondary servers must restore (apply) the log backup.</span></span> <span data-ttu-id="58021-116">예를 들어 주 데이터베이스에서 데이터가 실수로 변경된 경우 지연이 더 길면 도움이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58021-116">A longer delay can be useful, for example, if data is accidentally changed on the primary database.</span></span> <span data-ttu-id="58021-117">실수로 변경된 내용을 빨리 발견하면 변경 내용이 반영되기 전에 보조 데이터베이스에서 아직 변경되지 않은 데이터를 지연 덕분에 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58021-117">If the accidental change is noticed quickly, a delay can let you retrieve still unchanged data from a secondary database before the change is reflected there.</span></span>  
  
##  <a name="terms-and-definitions"></a><a name="TermsAndDefinitions"></a> <span data-ttu-id="58021-118">용어 및 정의</span><span class="sxs-lookup"><span data-stu-id="58021-118">Terms and Definitions</span></span>  
 <span data-ttu-id="58021-119">주 데이터베이스</span><span class="sxs-lookup"><span data-stu-id="58021-119">primary server</span></span>  
 <span data-ttu-id="58021-120">프로덕션 서버인 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 의 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="58021-120">The instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that is your production server.</span></span>  
  
 <span data-ttu-id="58021-121">주 데이터베이스</span><span class="sxs-lookup"><span data-stu-id="58021-121">primary database</span></span>  
 <span data-ttu-id="58021-122">다른 서버에 백업할 주 서버의 데이터베이스입니다.</span><span class="sxs-lookup"><span data-stu-id="58021-122">The database on the primary server that you want to back up to another server.</span></span> <span data-ttu-id="58021-123">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 를 통한 로그 전달 구성의 모든 관리는 주 데이터베이스에서 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="58021-123">All administration of the log shipping configuration through [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] is performed from the primary database.</span></span>  
  
 <span data-ttu-id="58021-124">보조 데이터베이스</span><span class="sxs-lookup"><span data-stu-id="58021-124">secondary server</span></span>  
 <span data-ttu-id="58021-125">주 데이터베이스의 웜 대기 복사본을 보관할 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 의 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="58021-125">The instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] where you want to keep a warm standby copy of your primary database.</span></span>  
  
 <span data-ttu-id="58021-126">보조 데이터베이스</span><span class="sxs-lookup"><span data-stu-id="58021-126">secondary database</span></span>  
 <span data-ttu-id="58021-127">주 데이터베이스의 웜 대기 복사본입니다.</span><span class="sxs-lookup"><span data-stu-id="58021-127">The warm standby copy of the primary database.</span></span> <span data-ttu-id="58021-128">보조 데이터베이스는 제한된 읽기 전용 액세스에 사용 가능한 데이터베이스를 유지하는 RECOVERING 상태 또는 STANDBY 상태에 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58021-128">The secondary database may be in either the RECOVERING state or the STANDBY state, which leaves the database available for limited read-only access.</span></span>  
  
 <span data-ttu-id="58021-129">모니터 서버</span><span class="sxs-lookup"><span data-stu-id="58021-129">monitor server</span></span>  
 <span data-ttu-id="58021-130">로그 전달의 자세한 내용을 모두 추적하는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 의 선택적 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="58021-130">An optional instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that tracks all of the details of log shipping, including:</span></span>  
  
-   <span data-ttu-id="58021-131">주 데이터베이스의 트랜잭션 로그가 마지막으로 백업된 시간</span><span class="sxs-lookup"><span data-stu-id="58021-131">When the transaction log on the primary database was last backed up.</span></span>  
  
-   <span data-ttu-id="58021-132">보조 서버가 백업 파일을 마지막으로 복사하고 복원한 시간</span><span class="sxs-lookup"><span data-stu-id="58021-132">When the secondary servers last copied and restored the backup files.</span></span>  
  
-   <span data-ttu-id="58021-133">백업 오류 경고 정보</span><span class="sxs-lookup"><span data-stu-id="58021-133">Information about any backup failure alerts.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="58021-134">모니터 서버를 구성한 후에는 로그 전달을 먼저 제거하지 않으면 모니터 서버를 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="58021-134">Once the monitor server has been configured, it cannot be changed without removing log shipping first.</span></span>  
  
 <span data-ttu-id="58021-135">백업 작업</span><span class="sxs-lookup"><span data-stu-id="58021-135">backup job</span></span>  
 <span data-ttu-id="58021-136">백업 작업을 수행하고 로컬 서버와 모니터 서버에 작업을 기록하며 오래된 백업 파일과 기록 정보를 삭제하는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 작업입니다.</span><span class="sxs-lookup"><span data-stu-id="58021-136">A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job that  performs the backup operation, logs history to the local server and the monitor server, and deletes old backup files and history information.</span></span> <span data-ttu-id="58021-137">로그 전달을 설정하면 주 서버 인스턴스에 "로그 전달 백업" 작업 범주가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="58021-137">When log shipping is enabled, the job category "Log Shipping Backup" is created on the primary server instance.</span></span>  
  
 <span data-ttu-id="58021-138">복사 작업</span><span class="sxs-lookup"><span data-stu-id="58021-138">copy job</span></span>  
 <span data-ttu-id="58021-139">주 서버에서 보조 서버의 구성 가능한 대상으로 백업 파일을 복사하고 보조 서버와 모니터 서버에 내역을 기록하는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 작업입니다.</span><span class="sxs-lookup"><span data-stu-id="58021-139">A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job that copies the backup files from the primary server to a configurable destination on the secondary server and logs history on the secondary server and the monitor server.</span></span> <span data-ttu-id="58021-140">데이터베이스에서 로그 전달을 설정하면 로그 전달 구성의 각 보조 서버에 "로그 전달 복사" 작업 범주가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="58021-140">When log shipping is enabled on a database, the job category "Log Shipping Copy" is created on each secondary server in a log shipping configuration.</span></span>  
  
 <span data-ttu-id="58021-141">복원 작업</span><span class="sxs-lookup"><span data-stu-id="58021-141">restore job</span></span>  
 <span data-ttu-id="58021-142">복사된 백업 파일을 보조 데이터베이스에 복원하는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 작업입니다.</span><span class="sxs-lookup"><span data-stu-id="58021-142">A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job that restores the copied backup files to the secondary databases.</span></span> <span data-ttu-id="58021-143">로컬 서버와 모니터 서버에 작업을 기록하고 오래된 파일과 기록 정보를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="58021-143">It logs history on the local server and the monitor server, and deletes old files and old history information.</span></span> <span data-ttu-id="58021-144">데이터베이스에서 로그 전달을 설정하면 보조 서버 인스턴스에 "로그 전달 복원" 작업 범주가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="58021-144">When log shipping is enabled on a database, the job category "Log Shipping Restore" is created on the secondary server instance.</span></span>  
  
 <span data-ttu-id="58021-145">경고 작업</span><span class="sxs-lookup"><span data-stu-id="58021-145">alert job</span></span>  
 <span data-ttu-id="58021-146">지정한 임계값 내에 백업 및 복원 작업이 완료되지 않을 때 주 데이터베이스 및 보조 데이터베이스에 대한 경고를 생성하는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 작업입니다.</span><span class="sxs-lookup"><span data-stu-id="58021-146">A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job that raises alerts for primary and secondary databases when a backup or restore operation does not complete successfully within a specified threshold.</span></span> <span data-ttu-id="58021-147">데이터베이스에서 로그 전달이 설정되면 모니터 서버 인스턴스에 "로그 전달 경고" 작업 범주가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="58021-147">When log shipping is enabled on a database, job category "Log Shipping Alert" is created on the monitor server instance.</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="58021-148">각 경고에 대해 경고 번호를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="58021-148">For each alert, you need to specify an alert number.</span></span> <span data-ttu-id="58021-149">또한 경고가 발생할 때 운영자에게 알릴 경고를 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="58021-149">Also, be sure to configure the alert to notify an operator when an alert is raised.</span></span>  
  
##  <a name="log-shipping-overview"></a><a name="ComponentsAndConcepts"></a> <span data-ttu-id="58021-150">로그 전달 개요</span><span class="sxs-lookup"><span data-stu-id="58021-150">Log Shipping Overview</span></span>  
 <span data-ttu-id="58021-151">로그 전달은 다음 세 가지 작업으로 구성되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58021-151">Log shipping consists of three operations:</span></span>  
  
1.  <span data-ttu-id="58021-152">주 서버 인스턴스에서 트랜잭션 로그를 백업합니다.</span><span class="sxs-lookup"><span data-stu-id="58021-152">Back up the transaction log at the primary server instance.</span></span>  
  
2.  <span data-ttu-id="58021-153">보조 서버 인스턴스에 트랜잭션 로그 파일을 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="58021-153">Copy the transaction log file to the secondary server instance.</span></span>  
  
3.  <span data-ttu-id="58021-154">보조 서버 인스턴스에 로그 백업을 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="58021-154">Restore the log backup on the secondary server instance.</span></span>  
  
 <span data-ttu-id="58021-155">다수의 보조 서버 인스턴스에 로그를 전달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58021-155">The log can be shipped to multiple secondary server instances.</span></span> <span data-ttu-id="58021-156">이 경우 두 번째 작업과 세 번째 작업은 각 보조 서버 인스턴스에 대해 중복됩니다.</span><span class="sxs-lookup"><span data-stu-id="58021-156">In such cases, operations 2 and 3 are duplicated for each secondary server instance.</span></span>  
  
 <span data-ttu-id="58021-157">로그 전달 구성은 자동으로 주 서버에서 보조 서버로 장애 조치(Failover)되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="58021-157">A log shipping configuration does not automatically fail over from the primary server to the secondary server.</span></span> <span data-ttu-id="58021-158">주 데이터베이스를 사용할 수 없을 경우 수동으로 임의의 보조 데이터베이스를 온라인 상태로 전환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58021-158">If the primary database becomes unavailable, any of the secondary databases can be brought online manually.</span></span>  
  
 <span data-ttu-id="58021-159">보조 데이터베이스를 보고 용도로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58021-159">You can use a secondary database for reporting purposes.</span></span>  
  
 <span data-ttu-id="58021-160">또한 로그 전달 구성에 대해 경고를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58021-160">In addition, you can configure alerts for your log shipping configuration.</span></span>  
  
### <a name="a-typical-log-shipping-configuration"></a><span data-ttu-id="58021-161">일반적인 로그 전달 구성</span><span class="sxs-lookup"><span data-stu-id="58021-161">A Typical Log Shipping Configuration</span></span>  
 <span data-ttu-id="58021-162">다음 그림에서는 주 서버 인스턴스, 보조 서버 인스턴스 3개 및 모니터 서버 인스턴스로 이루어진 로그 전달 구성을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="58021-162">The following figure shows a log shipping configuration with the primary server instance, three secondary server instances, and a monitor server instance.</span></span> <span data-ttu-id="58021-163">이 그림에서는 백업, 복사 및 복원 작업에서 수행된 단계를 다음과 같이 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="58021-163">The figure illustrates the steps performed by backup, copy, and restorejobs, as follows:</span></span>  
  
1.  <span data-ttu-id="58021-164">주 서버 인스턴스는 백업 작업을 실행하여 주 데이터베이스의 트랜잭션 로그를 백업합니다.</span><span class="sxs-lookup"><span data-stu-id="58021-164">The primary server instance runs the backup job to back up the transaction log on the primary database.</span></span> <span data-ttu-id="58021-165">그런 다음 로그 백업을 주 로그 백업 파일에 저장하고 해당 파일을 백업 폴더로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="58021-165">This server instance then places the log backup into a primary log-backup file, which it sends to the backup folder.</span></span>  <span data-ttu-id="58021-166">이 그림에서 백업 폴더는 공유 디렉터리인 *백업 공유*에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58021-166">In this figure, the backup folder is on a shared directory-the *backup share*.</span></span>  
  
2.  <span data-ttu-id="58021-167">3개의 보조 서버 인스턴스는 각각 자체 복사 작업을 실행하여 주 로그 백업 파일을 로컬 대상 폴더로 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="58021-167">Each of the three secondary server instances runs its own copy job to copy the primary log-backup file to its own local destination folder.</span></span>  
  
3.  <span data-ttu-id="58021-168">각 보조 서버 인스턴스는 자체 복원 작업을 실행하여 로그 백업을 로컬 대상 폴더에서 로컬 보조 데이터베이스로 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="58021-168">Each secondary server instance runs its own restore job to restore the log backup from the local destination folder onto the local secondary database.</span></span>  
  
 <span data-ttu-id="58021-169">주 서버 인스턴스와 보조 서버 인스턴스는 자체 기록 및 상태를 모니터 서버 인스턴스로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="58021-169">The primary and secondary server instances send their own history and status to the monitor server instance.</span></span>  
  
 <span data-ttu-id="58021-170">![백업, 복사 및 복원 작업을 보여 주는 구성](../media/ls-typical-configuration.gif "백업, 복사 및 복원 작업을 보여 주는 구성")</span><span class="sxs-lookup"><span data-stu-id="58021-170">![Configuration showing backup, copy, & restore jobs](../media/ls-typical-configuration.gif "Configuration showing backup, copy, & restore jobs")</span></span>  
  
##  <a name="interoperability"></a><a name="Interoperability"></a> <span data-ttu-id="58021-171">상호 운용성</span><span class="sxs-lookup"><span data-stu-id="58021-171">Interoperability</span></span>  
 <span data-ttu-id="58021-172">로그 전달은 다음의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]기능 또는 구성 요소와 함께 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58021-172">Log shipping can be used with the following features or components of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:</span></span>  
  
-   [<span data-ttu-id="58021-173">로그 전달에서 AlwaysOn 가용성 그룹 &#40;SQL Server로 마이그레이션하기 위한 필수 구성 요소&#41;</span><span class="sxs-lookup"><span data-stu-id="58021-173">Prerequisites for Migrating from Log Shipping to AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](../availability-groups/windows/prereqs-migrating-log-shipping-to-always-on-availability-groups.md)  
  
-   [<span data-ttu-id="58021-174">데이터베이스 미러링 및 로그 전달&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="58021-174">Database Mirroring and Log Shipping &#40;SQL Server&#41;</span></span>](../database-mirroring/database-mirroring-and-log-shipping-sql-server.md)  
  
-   [<span data-ttu-id="58021-175">로그 전달 및 복제&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="58021-175">Log Shipping and Replication &#40;SQL Server&#41;</span></span>](log-shipping-and-replication-sql-server.md)  
  
> [!NOTE]  
>  [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] <span data-ttu-id="58021-176">및 데이터베이스 미러링은 함께 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="58021-176">and database mirroring are mutually exclusive.</span></span> <span data-ttu-id="58021-177">이러한 기능 중 하나를 위해 구성된 데이터베이스는 다른 기능을 위해 구성할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="58021-177">A database that is configured for one of these features cannot be configured for the other.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="58021-178">관련 작업</span><span class="sxs-lookup"><span data-stu-id="58021-178">Related Tasks</span></span>  
  
-   [<span data-ttu-id="58021-179">SQL Server 2014 &#40;Transact-sql&#41;로그 전달 업그레이드</span><span class="sxs-lookup"><span data-stu-id="58021-179">Upgrade Log Shipping to SQL Server 2014 &#40;Transact-SQL&#41;</span></span>](upgrading-log-shipping-to-sql-server-2016-transact-sql.md)  
  
-   [<span data-ttu-id="58021-180">로그 전달 구성&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="58021-180">Configure Log Shipping &#40;SQL Server&#41;</span></span>](configure-log-shipping-sql-server.md)  
  
-   [<span data-ttu-id="58021-181">로그 전달 구성에 보조 데이터베이스 추가&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="58021-181">Add a Secondary Database to a Log Shipping Configuration &#40;SQL Server&#41;</span></span>](add-a-secondary-database-to-a-log-shipping-configuration-sql-server.md)  
  
-   [<span data-ttu-id="58021-182">로그 전달 구성에서 보조 데이터베이스 제거&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="58021-182">Remove a Secondary Database from a Log Shipping Configuration &#40;SQL Server&#41;</span></span>](remove-a-secondary-database-from-a-log-shipping-configuration-sql-server.md)  
  
-   [<span data-ttu-id="58021-183">로그 전달 제거&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="58021-183">Remove Log Shipping &#40;SQL Server&#41;</span></span>](remove-log-shipping-sql-server.md)  
  
-   [<span data-ttu-id="58021-184">로그 전달 보고서 보기&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="58021-184">View the Log Shipping Report &#40;SQL Server Management Studio&#41;</span></span>](view-the-log-shipping-report-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="58021-185">로그 전달 모니터링&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="58021-185">Monitor Log Shipping &#40;Transact-SQL&#41;</span></span>](monitor-log-shipping-transact-sql.md)  
  
-   [<span data-ttu-id="58021-186">로그 전달 보조 데이터베이스로 장애 조치(failover)&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="58021-186">Fail Over to a Log Shipping Secondary &#40;SQL Server&#41;</span></span>](fail-over-to-a-log-shipping-secondary-sql-server.md)  
  
-   [<span data-ttu-id="58021-187">로그 전달 보조 데이터베이스로 장애 조치(failover)&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="58021-187">Fail Over to a Log Shipping Secondary &#40;SQL Server&#41;</span></span>](fail-over-to-a-log-shipping-secondary-sql-server.md)  
  
-   [<span data-ttu-id="58021-188">역할 전환 후 로그인 및 작업 관리&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="58021-188">Management of Logins and Jobs After Role Switching &#40;SQL Server&#41;</span></span>](../../sql-server/failover-clusters/management-of-logins-and-jobs-after-role-switching-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="58021-189">참고 항목</span><span class="sxs-lookup"><span data-stu-id="58021-189">See Also</span></span>  
 [<span data-ttu-id="58021-190">AlwaysOn 가용성 그룹 &#40;SQL Server 개요&#41;</span><span class="sxs-lookup"><span data-stu-id="58021-190">Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](../availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)  
  
  
