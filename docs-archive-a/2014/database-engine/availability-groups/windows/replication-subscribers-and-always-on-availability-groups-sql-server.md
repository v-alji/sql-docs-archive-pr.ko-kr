---
title: 복제 구독자 및 AlwaysOn 가용성 그룹 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 01/16/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- failover subscribers with AlwaysOn
- Availability Groups [SQL Server], interoperability
- replication [SQL Server], AlwaysOn Availability Groups
ms.assetid: 0995f269-0580-43ed-b8bf-02b9ad2d7ee6
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 449b5ac416f2ae86395c40a984678ed4258b3b85
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651903"
---
# <a name="replication-subscribers-and-alwayson-availability-groups-sql-server"></a><span data-ttu-id="0da20-102">복제 구독자 및 AlwaysOn 가용성 그룹(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="0da20-102">Replication Subscribers and AlwaysOn Availability Groups (SQL Server)</span></span>
  <span data-ttu-id="0da20-103">복제 구독자인 데이터베이스를 포함하는 AlwaysOn 가용성 그룹이 장애 조치(Failover)되면 복제 구독은 실패할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0da20-103">When an AlwaysOn availability group containing a database that is a replication subscriber fails over, the replication subscription might fail.</span></span> <span data-ttu-id="0da20-104">트랜잭션 복제 밀어넣기 구독자의 경우 AG 수신기 이름을 사용하여 구독이 생성되었다면 장애 조치(failover) 후에 배포 에이전트가 자동으로 계속 복제합니다.</span><span class="sxs-lookup"><span data-stu-id="0da20-104">For transactional replication push subscribers, the distribution agent will continue to replicate automatically after a failover if the subscription was created using the AG listener name.</span></span> <span data-ttu-id="0da20-105">트랜잭션 복제 풀 구독자의 경우 AG 수신기 이름을 사용하여 구독이 생성되었고 원래 구독자 서버가 실행 중이라면 장애 조치(failover) 후에 배포 에이전트가 자동으로 계속 복제합니다.</span><span class="sxs-lookup"><span data-stu-id="0da20-105">For transactional replication pull subscribers, the distribution agent will continue to replicate automatically after a failover, if the subscription was created using the AG listener name and the original subscriber server is up and running.</span></span> <span data-ttu-id="0da20-106">이는 배포 에이전트 작업이 원래 구독자 서버(AG의 주 복제본)에서만 생성되기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="0da20-106">This is because the distribution agent jobs only get created on the original subscriber (primary replica of the AG).</span></span> <span data-ttu-id="0da20-107">병합 구독자의 경우 복제 관리자가 복제를 다시 만들어 수동으로 구독자를 다시 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0da20-107">For merge subscribers, a replication administrator must manually reconfigure the subscriber, by recreating the subscription.</span></span>  
  
## <a name="what-is-supported"></a><span data-ttu-id="0da20-108">지원되는 기능</span><span class="sxs-lookup"><span data-stu-id="0da20-108">What is Supported</span></span>  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="0da20-109">복제는 게시자에 대한 자동 장애 조치, 트랜잭션 구독자에 대한 자동 장애 조치 및 병합 구독자에 대한 수동 장애 조치를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="0da20-109">replication supports the automatic failover of the publisher, the automatic failover of transactional subscribers, and the manual failover of merge subscribers.</span></span> <span data-ttu-id="0da20-110">가용성 데이터베이스의 배포자에 대한 장애 조치는 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0da20-110">The failover of a distributor on an availability database is not supported.</span></span> <span data-ttu-id="0da20-111">AlwaysOn은 Websync 및 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Compact 시나리오와 함께 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0da20-111">AlwaysOn cannot be combined with Websync and [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Compact scenarios.</span></span>  
  
 <span data-ttu-id="0da20-112">**병합 끌어오기 구독의 장애 조치**</span><span class="sxs-lookup"><span data-stu-id="0da20-112">**Failover of a Merge Pull Subscription**</span></span>  
  
 <span data-ttu-id="0da20-113">서버 인스턴스가 실패하여 사용할 수 없으므로 끌어오기 에이전트가 주 복제본을 호스팅하는 서버 인스턴스의 **msdb** 데이터베이스에 저장된 작업을 찾을 수 없어 가용성 그룹 장애 조치 시 끌어오기 구독이 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="0da20-113">A pull subscription fails upon availability group failover, because pull agent cannot find the jobs stored in the **msdb** database of the server instance that hosts the primary replica; which is not available because the server instance has failed.</span></span>  
  
 <span data-ttu-id="0da20-114">**병합 밀어넣기 구독의 장애 조치**</span><span class="sxs-lookup"><span data-stu-id="0da20-114">**Failover of a Merge Push Subscription**</span></span>  
  
 <span data-ttu-id="0da20-115">밀어넣기 에이전트가 더 이상 원래 구독자의 원래 구독 데이터베이스에 연결할 수 없으므로 가용성 그룹 장애 조치 시 밀어넣기 구독이 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="0da20-115">A push subscription fails upon availability group failover, because the push agent can no longer connect to original subscription database on original subscriber.</span></span>  
  
## <a name="how-to-create-transactional-subscription-in-an-alwayson-environment"></a><span data-ttu-id="0da20-116">AlwaysOn 환경에서 트랜잭션 구독을 만드는 방법</span><span class="sxs-lookup"><span data-stu-id="0da20-116">How to Create Transactional Subscription in an AlwaysOn Environment</span></span>  
 <span data-ttu-id="0da20-117">트랜잭션 복제의 경우 다음 단계를 사용하여 구독자 가용성 그룹을 구성 및 장애 조치(Failover)합니다.</span><span class="sxs-lookup"><span data-stu-id="0da20-117">For transactional replication, use the following steps to configure and failover a subscriber availability group:</span></span>  
  
1.  <span data-ttu-id="0da20-118">구독을 만들기 전에 구독자 데이터베이스를 적절한 AlwaysOn 가용성 그룹에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="0da20-118">Before creating the subscription, add the subscriber database to the appropriate AlwaysOn availability group.</span></span>  
  
2.  <span data-ttu-id="0da20-119">가용성 그룹의 모든 노드에 구독자의 가용성 그룹 수신기를 연결된 서버로 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="0da20-119">Add the subscriber's availability group Listener as a linked server to all nodes of the availability group.</span></span> <span data-ttu-id="0da20-120">이 단계를 수행하면 모든 잠재적인 장애 조치(Failover) 파트너가 수신기를 인식하고 수신기에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0da20-120">This step ensures that all potential failover partners are aware of and can connect to the listener.</span></span>  
  
3.  <span data-ttu-id="0da20-121">아래 **트랜잭션 복제 밀어넣기 구독 만들기** 섹션의 스크립트를 사용하여 구독자의 가용성 그룹 수신기 이름으로 구독을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0da20-121">Using the script in the **Creating a Transactional Replication Push Subscription** section below, create the subscription using the name of the availability group listener of the subscriber.</span></span> <span data-ttu-id="0da20-122">장애 조치(Failover) 후 수신기 이름은 항상 유효하게 유지되지만 구독자의 실제 서버 이름은 새로운 주 서버가 된 실제 노드에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="0da20-122">After a failover, the listener name will always remain valid, whereas the actual server name of the subscriber will depend on the actual node that became the new primary.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="0da20-123">구독은 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 스크립트를 사용하여 만들어야 하며 [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]를 사용해서는 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0da20-123">The subscription must be created by using a [!INCLUDE[tsql](../../../includes/tsql-md.md)] script and cannot be created using [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)].</span></span>  
  
4.  <span data-ttu-id="0da20-124">끌어오기 구독을 만드는 경우:</span><span class="sxs-lookup"><span data-stu-id="0da20-124">If creating a pull subscription:</span></span>  
  
    1.  <span data-ttu-id="0da20-125">[!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]의 주 구독자 노드에서 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 에이전트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="0da20-125">In [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)], on the primary subscriber node, open the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent tree.</span></span>  
  
    2.  <span data-ttu-id="0da20-126">**끌어오기 배포 에이전트** 작업을 식별하고 작업을 편집합니다.</span><span class="sxs-lookup"><span data-stu-id="0da20-126">Identify the **Pull Distribution Agent** job and edit the job.</span></span>  
  
    3.  <span data-ttu-id="0da20-127">**에이전트 실행** 작업 단계에서 `-Publisher` 및 `-Distributor` 매개 변수를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="0da20-127">On the **Run Agent** job step, check the `-Publisher` and `-Distributor` parameters.</span></span> <span data-ttu-id="0da20-128">이러한 매개 변수에 올바른 직접 서버 및 게시자 및 배포자의 인스턴스 이름이 포함되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="0da20-128">Make sure that these parameters contain the correct direct server and instance names of the publisher and distributor server.</span></span>  
  
    4.  <span data-ttu-id="0da20-129">`-Subscriber` 매개 변수를 구독자의 가용성 그룹 수신기 이름으로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="0da20-129">Change the `-Subscriber` parameter to the subscriber's availability group listener name.</span></span>  
  
 <span data-ttu-id="0da20-130">다음 단계에 따라 구독을 만드는 경우 장애 조치 이후 아무 것도 수행하지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0da20-130">When you create your subscription following these steps, then you won't have to do anything after a failover.</span></span>  
  
## <a name="creating-a-transactional-replication-push-subscription"></a><span data-ttu-id="0da20-131">트랜잭션 복제 밀어넣기 구독 만들기</span><span class="sxs-lookup"><span data-stu-id="0da20-131">Creating a Transactional Replication Push Subscription</span></span>  
  
```  
-- commands to execute at the publisher, in the publisher database:  
use [<publisher database name>]  
EXEC sp_addsubscription @publication = N'<publication name>',   
       @subscriber = N'<availability group listener name>',   
       @destination_db = N'<subscriber database name>',   
       @subscription_type = N'Push',   
       @sync_type = N'automatic', @article = N'all', @update_mode = N'read only', @subscriber_type = 0;  
GO  
  
EXEC sp_addpushsubscription_agent @publication = N'<publication name>',   
       @subscriber = N'<availability group listener name>',   
       @subscriber_db = N'<subscriber database name>',   
       @job_login = null, @job_password = null, @subscriber_security_mode = 1;  
GO  
```  
  
## <a name="to-resume-the-merge-agents-after-the-availability-group-of-the-subscriber-fails-over"></a><span data-ttu-id="0da20-132">구독자의 가용성 그룹 장애 조치 이후 병합 에이전트를 다시 시작하려면</span><span class="sxs-lookup"><span data-stu-id="0da20-132">To Resume the Merge Agents After the Availability Group of the Subscriber Fails Over</span></span>  
 <span data-ttu-id="0da20-133">병합 복제의 경우 복제 관리자가 다음 단계에 따라 수동으로 구독자를 다시 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0da20-133">For merge replication, a replication administrator must manually reconfigure the subscriber with the following steps:</span></span>  
  
1.  <span data-ttu-id="0da20-134">`sp_subscription_cleanup`을 실행하여 구독자의 이전 구독을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="0da20-134">Execute `sp_subscription_cleanup` to remove the old subscription for the subscriber.</span></span> <span data-ttu-id="0da20-135">새로운 주 복제본(이전에 보조 복제본이었음)에서 이 동작을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="0da20-135">Perform this action on the new primary replica (which was formerly the secondary replica).</span></span>  
  
2.  <span data-ttu-id="0da20-136">새 구독을 만들고 새 스냅샷부터 시작하여 구독을 다시 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0da20-136">Recreate the subscription by creating a new subscription, beginning with a new snapshot.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0da20-137">현재 프로세스는 병합 복제 구독자에는 불편하지만 병합 복제의 기본 시나리오는 구독자에서 AlwaysOn 가용성 그룹을 사용하지 않는 연결이 끊긴 사용자(데스크톱, 랩톱, 핸드셋 디바이스)입니다.</span><span class="sxs-lookup"><span data-stu-id="0da20-137">The current process is inconvenient for merge replication subscribers, however the main scenario for merge replication is disconnected users (desktops, laptops, handset devices) which will not use AlwaysOn availability groups on the subscriber.</span></span>  
  
  
