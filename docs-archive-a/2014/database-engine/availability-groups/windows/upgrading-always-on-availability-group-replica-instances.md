---
title: 가동 중지 시간 및 데이터 손실을 최소화 하 여 가용성 그룹 서버 업그레이드 및 업데이트 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
ms.assetid: f670af56-dbcc-4309-9119-f919dcad8a65
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6bac882b93016a430fbcace2d590e6cc087123d2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741272"
---
# <a name="upgrade-and-update-of-availability-group-servers-with-minimal-downtime-and-data-loss"></a><span data-ttu-id="1097a-102">최소 작동 중지 및 데이터 손실로 가용성 그룹 서버 업그레이드 및 업데이트</span><span class="sxs-lookup"><span data-stu-id="1097a-102">Upgrade and Update of Availability Group Servers with Minimal Downtime and Data Loss</span></span>
  <span data-ttu-id="1097a-103">서버 인스턴스를 SQL Server 2012에서 서비스 팩 또는 최신 버전으로 업데이트하거나 업그레이드할 때 순차적 업데이트 또는 업그레이드를 수행하면 가용성 그룹의 작동 중단을 단 한 번의 수동 장애 조치(Failover)로 줄일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1097a-103">When updating or upgrading server instances from SQL Server 2012 to a service pack or a newer version, you can reduce downtime for an availability group to only a single manual failover by performing a sequential update or upgrade.</span></span> <span data-ttu-id="1097a-104">SQL Server 버전을 업그레이드하는 경우 롤링 업그레이드라고 하고, 핫픽스 또는 서비스 팩이 포함된 현재 SQL Server 버전을 업데이트하는 것을 롤링 업데이트라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="1097a-104">For upgrading SQL Server versions, it is known as rolling upgrade; for updating the current SQL Server version with hotfixes or service packs, it is known as rolling update.</span></span>  
  
 <span data-ttu-id="1097a-105">이 항목은 SQL Server 업그레이드/업데이트에 대한 설명에 한해 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="1097a-105">This topic limits the discussion to SQL Server upgrades/updates only.</span></span> <span data-ttu-id="1097a-106">항상 사용 가능한 SQL Server 인스턴스가 실행 되는 운영 체제 관련 업그레이드/업데이트는 [운영 체제 업그레이드에 대 한 AlwaysOn 가용성 그룹의 클러스터 간 마이그레이션](https://msdn.microsoft.com/library/jj873730.aspx) 을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1097a-106">For operating system-related upgrades/updates that the highly-available SQL Server instances are running on, see [Cross-cluster Migration of AlwaysOn Availability Groups for Operating System Upgrades](https://msdn.microsoft.com/library/jj873730.aspx)</span></span>  
  
## <a name="rolling-upgradeupdate-best-practices-for-alwayson-availability-groups"></a><span data-ttu-id="1097a-107">AlwaysOn 가용성 그룹의 롤링 업그레이드/업데이트를 위한 최상의 방법</span><span class="sxs-lookup"><span data-stu-id="1097a-107">Rolling Upgrade/Update Best Practices for AlwaysOn Availability Groups</span></span>  
 <span data-ttu-id="1097a-108">서버 업그레이드/업데이트를 수행할 때 가용성 그룹에 대한 가동 중단 시간 및 데이터 손실을 최소화하기 위해 다음과 같은 최상의 방법을 구현해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1097a-108">The following best practices should be observed when performing server upgrades/updates in order to minimize downtime and data loss for your availability groups:</span></span>  
  
-   <span data-ttu-id="1097a-109">롤링 업그레이드/업데이트를 시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="1097a-109">Before starting the rolling upgrade/update,</span></span>  
  
    -   <span data-ttu-id="1097a-110">동기-커밋 복제본 중 하나 이상에서 수동 장애 조치(Failover)를 연습해 봅니다.</span><span class="sxs-lookup"><span data-stu-id="1097a-110">Perform a practice manual failover on at least one of your synchronous-commit replicas</span></span>  
  
    -   <span data-ttu-id="1097a-111">모든 가용성 데이터베이스에 대해 전체 데이터베이스 백업을 수행하여 데이터를 보호합니다.</span><span class="sxs-lookup"><span data-stu-id="1097a-111">Protect your data by performing a full database backup on every availability database</span></span>  
  
    -   <span data-ttu-id="1097a-112">모든 가용성 데이터베이스에서 DBCC CHECKDB를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="1097a-112">Run DBCC CHECKDB on every availability database</span></span>  
  
-   <span data-ttu-id="1097a-113">항상 원격 보조 복제본을 먼저 업그레이드/업데이트한 후 로컬 보조 복제본 노드와 주 복제본 노드 순으로 업그레이드/업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="1097a-113">Always upgrade/update the remote secondary replica nodes first, then local secondary replica nodes next, and the primary replica node last.</span></span>  
  
-   <span data-ttu-id="1097a-114">업그레이드되고 있는 데이터베이스에 대한 백업은 발생할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1097a-114">Backups cannot occur on a database that is in the process of being upgraded.</span></span>  <span data-ttu-id="1097a-115">보조 복제본을 업그레이드하기 전에 주 복제본에 대해서만 백업을 실행하도록 자동화된 백업 기본 설정을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="1097a-115">Prior to upgrading the secondary replicas, configure the automated backup preference to run backups only on the primary replica.</span></span>  <span data-ttu-id="1097a-116">주 복제본을 업그레이드하기 전에 보조 복제본에 대해서만 백업을 실행하도록 이 설정을 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="1097a-116">Prior to upgrading the primary replica, modify this setting to run backups only on the secondary replicas.</span></span>  
  
-   <span data-ttu-id="1097a-117">업그레이드/업데이트 프로세스 동안 가용성 그룹에서 의도하지 않은 장애 조치(failover)를 수행하지 않도록 시작하기 전에 모든 동기-커밋에서 가용성 장애 조치(failover)를 제거하십시오.</span><span class="sxs-lookup"><span data-stu-id="1097a-117">To prevent the availability group from unintended failovers during the upgrade/update process, remove availability failover from all synchronous-commit replicas before you begin.</span></span>  
  
-   <span data-ttu-id="1097a-118">가용성 그룹을 보조 복제본이 포함된 업그레이드된 노드로 장애 조치하기 전에 주 복제본 노드를 업그레이드해서는 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1097a-118">Do not upgrade the primary replica node before failing over the availability group to an upgraded node with a secondary replica first.</span></span> <span data-ttu-id="1097a-119">그렇지 않으면 주 복제본에서 업그레이드/업데이트를 진행하는 동안 클라이언트 애플리케이션의 작동 중단 시간이 길어질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1097a-119">Otherwise, client applications may suffer extended downtime during the upgrade/update on the primary replica.</span></span>  
  
-   <span data-ttu-id="1097a-120">항상 가용성 그룹을 동기-커밋 보조 복제본 노드로 장애 조치(failover)합니다.</span><span class="sxs-lookup"><span data-stu-id="1097a-120">Always fail over the availability group to a synchronous-commit secondary replica node.</span></span> <span data-ttu-id="1097a-121">비동기-커밋 보조 복제본으로 장애 조치(failover)하는 경우 데이터베이스의 데이터가 손실되고, 데이터 이동을 수동으로 다시 시작할 때까지 데이터 이동이 자동으로 중지됩니다.</span><span class="sxs-lookup"><span data-stu-id="1097a-121">If you fail over to an asynchronous-commit secondary replica, the databases will suffer data loss, and data movement is automatically suspended until you manually resume data movement.</span></span>  
  
-   <span data-ttu-id="1097a-122">다른 보조 복제본 노드를 업그레이드/업데이트하기 전에 주 복제본 노드를 업그레이드/업데이트해서는 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1097a-122">Do not upgrade/update the primary replica node before upgrading/updating any other secondary replica nodes.</span></span> <span data-ttu-id="1097a-123">업그레이드된 주 복제본은 아직 같은 버전으로 업그레이드되지 않은 보조 복제본에 로그를 더 이상 전달할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1097a-123">An upgraded primary replica can no longer ship logs to any secondary replica that has not yet been upgraded to the same version.</span></span> <span data-ttu-id="1097a-124">보조 복제본으로 데이터 이동이 일시 중지된 경우 해당 복제본에 대한 자동 장애 조치(failover)를 수행할 수 없고 가용성 데이터베이스의 데이터가 손실될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1097a-124">When data movement to a secondary replica is suspended, no automatic failover can occur for that replica, and your availability databases are vulnerable to data loss.</span></span>  
  
-   <span data-ttu-id="1097a-125">가용성 그룹을 장애 조치(failover)하기 전에 장애 조치(failover) 대상의 동기화 상태가 SYNCHRONIZED인지 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="1097a-125">Before failing over an availability group, verify that the synchronization state of the failover target is SYNCHRONIZED.</span></span>  
  
## <a name="rolling-upgradeupdate-process"></a><span data-ttu-id="1097a-126">롤링 업그레이드/업데이트 프로세스</span><span class="sxs-lookup"><span data-stu-id="1097a-126">Rolling Upgrade/Update Process</span></span>  
 <span data-ttu-id="1097a-127">실제로 정확한 프로세스는 가용성 그룹의 배포 토폴로지 및 각 복제본의 커밋 모드와 같은 요소에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="1097a-127">In practice, the exact process will depend on factors such as the deployment topology of your availability groups and the commit mode of each replica.</span></span> <span data-ttu-id="1097a-128">가장 간단한 시나리오는 다음 단계가 포함된 가장 간단한 형식의 다단계 프로세스로 롤링 업그레이드/업데이트를 수행하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="1097a-128">But in the simplest scenario, a rolling upgrade/update is a multi-stage process that in its simplest form involves the following steps:</span></span>  
  
 <span data-ttu-id="1097a-129">![HADR 시나리오의 가용성 그룹 업그레이드](../../media/alwaysonupgrade-ag-hadr.gif "HADR 시나리오의 가용성 그룹 업그레이드")</span><span class="sxs-lookup"><span data-stu-id="1097a-129">![Availability Group Upgrade in HADR Scenario](../../media/alwaysonupgrade-ag-hadr.gif "Availability Group Upgrade in HADR Scenario")</span></span>  
  
1.  <span data-ttu-id="1097a-130">모든 동기-커밋 복제본에서 자동 장애 조치(failover)를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="1097a-130">Remove automatic failover on all synchronous-commit replicas</span></span>  
  
2.  <span data-ttu-id="1097a-131">비동기-커밋 보조 복제본을 실행하는 모든 원격 서버 인스턴스를 업그레이드/업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="1097a-131">Upgrade/update all remote server instances running asynchronous-commit secondary replicas</span></span>  
  
3.  <span data-ttu-id="1097a-132">현재 주 복제본을 실행하지 않는 모든 로컬 서버 인스턴스를 업그레이드/업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="1097a-132">Upgrade/update the all local server instances that are not currently running the primary replica</span></span>  
  
4.  <span data-ttu-id="1097a-133">수동으로 가용성 그룹을 동기-커밋 보조 복제본으로 장애 조치(failover)합니다.</span><span class="sxs-lookup"><span data-stu-id="1097a-133">Manually fail over the availability group to a synchronous-commit secondary replica</span></span>  
  
5.  <span data-ttu-id="1097a-134">이전에 주 복제본을 호스팅한 서버 인스턴스를 업그레이드/업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="1097a-134">Upgrade/update the server instance that formerly hosted the primary replica</span></span>  
  
6.  <span data-ttu-id="1097a-135">자동 장애 조치(Failover) 파트너를 원하는 대로 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="1097a-135">Configure automatic failover partners as desired</span></span>  
  
 <span data-ttu-id="1097a-136">필요한 경우 추가 수동 장애 조치(failover)를 수행하여 가용성 그룹을 원래 구성으로 되돌릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1097a-136">If necessary, you can perform an extra manual failover to return the availability group to its original configuration.</span></span>  
  
## <a name="availability-group-with-one-remote-secondary-replica"></a><span data-ttu-id="1097a-137">원격 보조 복제본 하나가 포함된 가용성 그룹</span><span class="sxs-lookup"><span data-stu-id="1097a-137">Availability Group with One Remote Secondary Replica</span></span>  
 <span data-ttu-id="1097a-138">재해 복구용으로만 가용성 그룹을 배포한 경우 가용성 그룹을 비동기-커밋 보조 복제본으로 장애 조치(failover)해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1097a-138">If you have deployed an availability group only for disaster recovery, you may need to fail over the availability group to an asynchronous-commit secondary replica.</span></span> <span data-ttu-id="1097a-139">다음 그림에서는 이 구성을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="1097a-139">Such configuration is illustrated by the following figure:</span></span>  
  
 <span data-ttu-id="1097a-140">![DR 시나리오의 가용성 그룹 업그레이드](../../media/agupgrade-ag-dr.gif "DR 시나리오의 가용성 그룹 업그레이드")</span><span class="sxs-lookup"><span data-stu-id="1097a-140">![Availability Group Upgrade in DR Scenario](../../media/agupgrade-ag-dr.gif "Availability Group Upgrade in DR Scenario")</span></span>  
  
 <span data-ttu-id="1097a-141">이 경우 롤링 업그레이드/업데이트 동안 가용성 그룹을 비동기-커밋 보조 복제본으로 장애 조치(failover)해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1097a-141">In this situation, you must fail over the availability group to the asynchronous-commit secondary replica during the rolling upgrade/update.</span></span> <span data-ttu-id="1097a-142">데이터 손실을 방지하려면 가용성 그룹을 장애 조치(failover)하기 전에 커밋 모드를 동기 커밋으로 변경하고 보조 복제본이 동기화될 때까지 기다리십시오.</span><span class="sxs-lookup"><span data-stu-id="1097a-142">To prevent data loss, change the commit mode to synchronous commit and wait for the secondary replica to be synchronized before you fail over the availability group.</span></span> <span data-ttu-id="1097a-143">즉 롤링 업그레이드/업데이트 프로세스는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="1097a-143">Therefore, the rolling upgrade/update process may look as follows:</span></span>  
  
1.  <span data-ttu-id="1097a-144">원격 서버 업그레이드/업데이트</span><span class="sxs-lookup"><span data-stu-id="1097a-144">Upgrade/update the remote server</span></span>  
  
2.  <span data-ttu-id="1097a-145">커밋 모드를 동기 커밋으로 변경</span><span class="sxs-lookup"><span data-stu-id="1097a-145">Change the commit mode to synchronous commit</span></span>  
  
3.  <span data-ttu-id="1097a-146">동기화 상태가 SYNCHRONIZED가 될 때까지 대기</span><span class="sxs-lookup"><span data-stu-id="1097a-146">Wait until synchronization state is SYNCHRONIZED</span></span>  
  
4.  <span data-ttu-id="1097a-147">가용성 그룹을 원격 사이트로 장애 조치(failover)</span><span class="sxs-lookup"><span data-stu-id="1097a-147">Fail over the availability group to the remote site</span></span>  
  
5.  <span data-ttu-id="1097a-148">로컬(주 사이트) 서버 업그레이드/업데이트</span><span class="sxs-lookup"><span data-stu-id="1097a-148">Upgrade/update the local (primary site) server</span></span>  
  
6.  <span data-ttu-id="1097a-149">가용성 그룹을 주 사이트로 장애 조치(failover)</span><span class="sxs-lookup"><span data-stu-id="1097a-149">Fail over the availability group to the primary site</span></span>  
  
7.  <span data-ttu-id="1097a-150">커밋 모드를 비동기 커밋으로 변경</span><span class="sxs-lookup"><span data-stu-id="1097a-150">Change the commit mode to asynchronous commit</span></span>  
  
 <span data-ttu-id="1097a-151">동기-커밋 모드는 원격 사이트로 데이터 동기화에 권장되는 설정이 아니므로 설정 변경 후 클라이언트 애플리케이션에서 데이터베이스 대기 시간이 증가됨을 즉각적으로 알릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1097a-151">Since the synchronous-commit mode is not a recommended setting for data synchronization to a remote site, client applications may notice an immediate increase in database latency after the setting change.</span></span> <span data-ttu-id="1097a-152">또한 장애 조치(failover)를 수행하면 승인되지 않은 모든 로그 메시지가 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="1097a-152">Moreover, performing a failover will cause all unacknowledged log messages to be discarded.</span></span> <span data-ttu-id="1097a-153">두 사이트 간 긴 네트워크 지연 시간으로 인해 삭제된 로그 메시지의 양이 상당히 커질 수 있고 이에 따라 방대한 양의 트랜잭션이 실패할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1097a-153">The amount of discarded log messages can be quite large due to the high network latency between the two sites, causing clients to experience a high volume of transactional failure.</span></span> <span data-ttu-id="1097a-154">다음을 수행하여 클라이언트 애플리케이션에 대한 영향을 최소화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1097a-154">You can minimize impact to client applications by doing the following:</span></span>  
  
-   <span data-ttu-id="1097a-155">클라이언트 트래픽이 낮을 때 유지 관리 기간을 신중하게 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1097a-155">Carefully select a maintenance window during low client traffic</span></span>  
  
-   <span data-ttu-id="1097a-156">주 사이트에서 SQL Server를 업그레이드/업데이트하는 동안 가용성 모드를 비동기 커밋으로 변경한 다음 주 사이트에 대한 장애 조치(failover)를 수행할 준비가 되면 동기 커밋으로 되돌립니다.</span><span class="sxs-lookup"><span data-stu-id="1097a-156">While upgrading/updating SQL Server on the primary site, change the availability mode back to asynchronous commit, then revert to synchronous commit when you are ready to fail over to the primary site again</span></span>  
  
## <a name="availability-group-with-failover-cluster-instance-nodes"></a><span data-ttu-id="1097a-157">장애 조치(Failover) 클러스터 인스턴스 노드가 포함된 가용성 그룹</span><span class="sxs-lookup"><span data-stu-id="1097a-157">Availability Group with Failover Cluster Instance Nodes</span></span>  
 <span data-ttu-id="1097a-158">가용성 그룹에 FCI(장애 조치(failover) 클러스터 인스턴스) 노드가 포함된 경우 활성 노드를 업그레이드/업데이트하기 전에 비활성 노드를 업그레이드/업데이트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1097a-158">If an availability group contains failover cluster instance (FCI) nodes, you should upgrade/update the inactive nodes before you upgrade/update the active nodes.</span></span> <span data-ttu-id="1097a-159">아래 그림에서는 로컬 고가용성을 위한 FCI 및 원격 재해 복구용 FCI 간 비동기 커밋과 함께 일반적인 가용성 그룹 시나리오와 업그레이드 시퀀스를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="1097a-159">The figure below illustrates a common availability group scenario with FCIs for local high availability and asynchronous commit between the FCIs for remote disaster recovery, and the upgrade sequence.</span></span>  
  
 <span data-ttu-id="1097a-160">![FCI가 포함된 가용성 그룹 업그레이드](../../media/agupgrade-ag-fci-dr.gif "FCI가 포함된 가용성 그룹 업그레이드")</span><span class="sxs-lookup"><span data-stu-id="1097a-160">![Availability Group Upgrade with FCIs](../../media/agupgrade-ag-fci-dr.gif "Availability Group Upgrade with FCIs")</span></span>  
  
1.  <span data-ttu-id="1097a-161">REMOTE2 업그레이드/업데이트</span><span class="sxs-lookup"><span data-stu-id="1097a-161">Upgrade/update REMOTE2</span></span>  
  
2.  <span data-ttu-id="1097a-162">FCI2를 REMOTE2로 장애 조치(Failover)</span><span class="sxs-lookup"><span data-stu-id="1097a-162">Fail over FCI2 to REMOTE2</span></span>  
  
3.  <span data-ttu-id="1097a-163">REMOTE1 업그레이드/업데이트</span><span class="sxs-lookup"><span data-stu-id="1097a-163">Upgrade/update REMOTE1</span></span>  
  
4.  <span data-ttu-id="1097a-164">PRIMARY2 업그레이드/업데이트</span><span class="sxs-lookup"><span data-stu-id="1097a-164">Upgrade/update PRIMARY2</span></span>  
  
5.  <span data-ttu-id="1097a-165">FCI1을 PRIMARY2로 장애 조치(Failover)</span><span class="sxs-lookup"><span data-stu-id="1097a-165">Fail over FCI1 to PRIMARY2</span></span>  
  
6.  <span data-ttu-id="1097a-166">PRIMARY1 업그레이드/업데이트</span><span class="sxs-lookup"><span data-stu-id="1097a-166">Upgrade/update PRIMARY1</span></span>  
  
## <a name="upgradeupdate-sql-server-instances-with-multiple-availability-groups"></a><span data-ttu-id="1097a-167">여러 가용성 그룹이 있는 SQL Server 인스턴스 업그레이드/업데이트</span><span class="sxs-lookup"><span data-stu-id="1097a-167">Upgrade/Update SQL Server Instances with Multiple Availability Groups</span></span>  
 <span data-ttu-id="1097a-168">별도의 서버 노드(활성/비활성 구성)에서 주 복제본이 있는 여러 가용성 그룹을 실행 중인 경우 프로세스 중에 고가용성을 유지하기 위해 업그레이드/업데이트 경로에 더 많은 장애 조치(failover) 단계가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="1097a-168">If you are running multiple availability groups with primary replicas on separate server nodes (an Active/Active configuration), the upgrade/update path involves more failover steps to preserve high availability in the process.</span></span> <span data-ttu-id="1097a-169">다음 표와 같이 3개의 서버 노드에서 3개의 가용성 그룹을 실행하고 모든 보조 복제본이 동기-커밋 모드에서 실행 중이라고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="1097a-169">Suppose you are running three availability groups on three server nodes as shown in the following table, and all secondary replicas are running in synchronous-commit mode.</span></span>  
  
|<span data-ttu-id="1097a-170">가용성 그룹</span><span class="sxs-lookup"><span data-stu-id="1097a-170">Availability Group</span></span>|<span data-ttu-id="1097a-171">Node1</span><span class="sxs-lookup"><span data-stu-id="1097a-171">Node1</span></span>|<span data-ttu-id="1097a-172">Node2</span><span class="sxs-lookup"><span data-stu-id="1097a-172">Node2</span></span>|<span data-ttu-id="1097a-173">Node3</span><span class="sxs-lookup"><span data-stu-id="1097a-173">Node3</span></span>|  
|------------------------|-----------|-----------|-----------|  
|<span data-ttu-id="1097a-174">AG1</span><span class="sxs-lookup"><span data-stu-id="1097a-174">AG1</span></span>|<span data-ttu-id="1097a-175">주</span><span class="sxs-lookup"><span data-stu-id="1097a-175">Primary</span></span>|||  
|<span data-ttu-id="1097a-176">AG2</span><span class="sxs-lookup"><span data-stu-id="1097a-176">AG2</span></span>||<span data-ttu-id="1097a-177">주</span><span class="sxs-lookup"><span data-stu-id="1097a-177">Primary</span></span>||  
|<span data-ttu-id="1097a-178">AG3</span><span class="sxs-lookup"><span data-stu-id="1097a-178">AG3</span></span>|||<span data-ttu-id="1097a-179">주</span><span class="sxs-lookup"><span data-stu-id="1097a-179">Primary</span></span>|  
  
 <span data-ttu-id="1097a-180">다음 시퀀스에서 부하 분산 롤링 업그레이드/업데이트를 실행하기 위한 상황에 적합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1097a-180">It may be appropriate in your situation to perform a load-balanced rolling upgrade/update in the following sequence:</span></span>  
  
1.  <span data-ttu-id="1097a-181">AG2를 Node3으로 장애 조치(Failover)(Node2를 확보하기 위함)</span><span class="sxs-lookup"><span data-stu-id="1097a-181">Fail over AG2 to Node3 (to free up Node2)</span></span>  
  
2.  <span data-ttu-id="1097a-182">Node2 업그레이드/업데이트</span><span class="sxs-lookup"><span data-stu-id="1097a-182">Upgrade/update Node2</span></span>  
  
3.  <span data-ttu-id="1097a-183">AG1을 Node2로 장애 조치(Failover)(Node1을 확보하기 위함)</span><span class="sxs-lookup"><span data-stu-id="1097a-183">Fail over AG1 to Node2 (to free up Node1)</span></span>  
  
4.  <span data-ttu-id="1097a-184">Node1 업그레이드/업데이트</span><span class="sxs-lookup"><span data-stu-id="1097a-184">Upgrade/update Node1</span></span>  
  
5.  <span data-ttu-id="1097a-185">AG2 및 AG3을 Node1로 장애 조치(Failover)(Node3을 확보하기 위함)</span><span class="sxs-lookup"><span data-stu-id="1097a-185">Fail over both AG2 and AG3 to Node1 (to free up Node3)</span></span>  
  
6.  <span data-ttu-id="1097a-186">Node3 업그레이드/업데이트</span><span class="sxs-lookup"><span data-stu-id="1097a-186">Upgrade/update Node3</span></span>  
  
7.  <span data-ttu-id="1097a-187">AG3을 Node3으로 장애 조치(Failover)</span><span class="sxs-lookup"><span data-stu-id="1097a-187">Fail over AG3 to Node3</span></span>  
  
 <span data-ttu-id="1097a-188">이 업그레이드/업데이트 시퀀스에는 가용성 그룹당 2번의 장애 조치(Failover)보다 적은 평균적인 작동 중단 시간이 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="1097a-188">This upgrade/update sequence has an average downtime of less than two failovers per availability group.</span></span> <span data-ttu-id="1097a-189">결과적인 구성이 아래 표에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="1097a-189">The resulting configuration is shown in the table below.</span></span>  
  
|<span data-ttu-id="1097a-190">가용성 그룹</span><span class="sxs-lookup"><span data-stu-id="1097a-190">Availability Group</span></span>|<span data-ttu-id="1097a-191">Node1</span><span class="sxs-lookup"><span data-stu-id="1097a-191">Node1</span></span>|<span data-ttu-id="1097a-192">Node2</span><span class="sxs-lookup"><span data-stu-id="1097a-192">Node2</span></span>|<span data-ttu-id="1097a-193">Node3</span><span class="sxs-lookup"><span data-stu-id="1097a-193">Node3</span></span>|  
|------------------------|-----------|-----------|-----------|  
|<span data-ttu-id="1097a-194">AG1</span><span class="sxs-lookup"><span data-stu-id="1097a-194">AG1</span></span>||<span data-ttu-id="1097a-195">주</span><span class="sxs-lookup"><span data-stu-id="1097a-195">Primary</span></span>||  
|<span data-ttu-id="1097a-196">AG2</span><span class="sxs-lookup"><span data-stu-id="1097a-196">AG2</span></span>|<span data-ttu-id="1097a-197">주</span><span class="sxs-lookup"><span data-stu-id="1097a-197">Primary</span></span>|||  
|<span data-ttu-id="1097a-198">AG3</span><span class="sxs-lookup"><span data-stu-id="1097a-198">AG3</span></span>|||<span data-ttu-id="1097a-199">주</span><span class="sxs-lookup"><span data-stu-id="1097a-199">Primary</span></span>|  
  
 <span data-ttu-id="1097a-200">특정 구현에 따라 업그레이드/업데이트 경로가 달라질 수 있으며 클라이언트 애플리케이션에 발생하는 작동 중지 시간도 달라질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1097a-200">Based on your specific implementation, your upgrade/update path may vary, and the downtime that client applications experience may vary as well.</span></span>  
  
  
