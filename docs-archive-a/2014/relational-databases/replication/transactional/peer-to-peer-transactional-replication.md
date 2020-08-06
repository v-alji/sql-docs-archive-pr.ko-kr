---
title: 피어 투 피어 트랜잭션 복제 | Microsoft 문서
ms.custom: ''
ms.date: 08/29/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- bidirectional replication
- transactional replication, bidirectional replication
- bidirectional transactional replication
- transactional replication, peer-to-peer replication
- peer-to-peer transactional replication
ms.assetid: 23e7e8c1-002f-4e69-8c99-d63e4100de64
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f61db9a8e7cecb107fd1b27fae966d133e043c8b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651627"
---
# <a name="peer-to-peer-transactional-replication"></a><span data-ttu-id="0a73d-102">@loopback_detection</span><span class="sxs-lookup"><span data-stu-id="0a73d-102">Peer-to-Peer Transactional Replication</span></span>
  <span data-ttu-id="0a73d-103">피어 투 피어 복제는 *노드*라고도 하는 여러 서버 인스턴스에 걸쳐 데이터 복사본을 유지 관리함으로써 확장성 및 고가용성 솔루션을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="0a73d-103">Peer-to-peer replication provides a scale-out and high-availability solution by maintaining copies of data across multiple server instances, also referred to as *nodes*.</span></span> <span data-ttu-id="0a73d-104">트랜잭션 복제를 기반으로 구축된 피어 투 피어 복제는 트랜잭션 측면에서 일관적인 변경 내용을 거의 실시간으로 전파합니다.</span><span class="sxs-lookup"><span data-stu-id="0a73d-104">Built on the foundation of transactional replication, peer-to-peer replication propagates transactionally consistent changes in near real-time.</span></span> <span data-ttu-id="0a73d-105">따라서 읽기 작업을 확장해야 하는 애플리케이션은 클라이언트의 읽기 작업을 여러 노드에 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a73d-105">This enables applications that require scale-out of read operations to distribute the reads from clients across multiple nodes.</span></span> <span data-ttu-id="0a73d-106">여러 노드의 데이터가 거의 실시간으로 유지 관리되므로 피어 투 피어 복제는 데이터 중복을 제공하며 이러한 중복은 데이터의 가용성을 높여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="0a73d-106">Because data is maintained across the nodes in near real-time, peer-to-peer replication provides data redundancy, which increases the availability of data.</span></span>  
  
 <span data-ttu-id="0a73d-107">웹 애플리케이션의 경우를 살펴 보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="0a73d-107">Consider a Web application.</span></span> <span data-ttu-id="0a73d-108">피어 투 피어 복제를 사용하는 웹 응용 프로그램은 다음과 같은 이점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a73d-108">This can benefit from peer-to-peer replication in the following ways:</span></span>  
  
-   <span data-ttu-id="0a73d-109">카탈로그 쿼리 및 그 밖의 읽기 작업이 여러 노드에 분산되므로</span><span class="sxs-lookup"><span data-stu-id="0a73d-109">Catalog queries and other reads are spread across multiple nodes.</span></span> <span data-ttu-id="0a73d-110">읽기 작업이 증가해도 성능이 일정하게 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a73d-110">This enables performance to remain consistent as reads increase.</span></span>  
  
-   <span data-ttu-id="0a73d-111">시스템의 노드 중 하나에 오류가 발생하는 경우 애플리케이션 계층에서 해당 노드에 대한 쓰기 작업을 다른 노드로 리디렉션할 수 있으므로</span><span class="sxs-lookup"><span data-stu-id="0a73d-111">If one of the nodes in the system fails, an application layer can redirect the writes for that node to another node.</span></span> <span data-ttu-id="0a73d-112">가용성이 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a73d-112">This maintains availability.</span></span>  
  
-   <span data-ttu-id="0a73d-113">노드를 유지 관리해야 하거나 전체 시스템을 업그레이드해야 하는 경우 애플리케이션의 가용성에 영향을 주지 않고 각 노드를 오프라인 상태로 만들었다가 다시 시스템에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a73d-113">If a node requires maintenance or the whole system requires an upgrade, each node can be taken offline and added back to the system without affecting the availability of the application.</span></span>  
  
 <span data-ttu-id="0a73d-114">피어 투 피어 복제를 사용하면 읽기 작업을 확장할 수 있지만 토폴로지에 대한 쓰기 성능은 단일 노드의 경우와 유사합니다.</span><span class="sxs-lookup"><span data-stu-id="0a73d-114">Although peer-to-peer replication enables scaling out of read operations, write performance for the topology is like that for a single node.</span></span> <span data-ttu-id="0a73d-115">이는 모든 삽입, 업데이트 및 삭제가 모든 노드에 전파되기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="0a73d-115">This is because ultimately all inserts, updates, and deletes are propagated to all nodes.</span></span> <span data-ttu-id="0a73d-116">변경 내용이 지정된 노드에 적용되면 복제에서 이를 인식하여 변경 내용이 두 번 이상 노드에서 순환되지 않도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a73d-116">Replication recognizes when a change has been applied to a given node and prevents changes from cycling through the nodes more than one time.</span></span> <span data-ttu-id="0a73d-117">다음과 같은 이유로 인해 각 행에 대한 쓰기 작업은 하나의 노드에서만 수행하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="0a73d-117">We strongly recommend that write operations for each row be performed at only node, for the following reasons:</span></span>  
  
-   <span data-ttu-id="0a73d-118">두 개 이상의 노드에서 행이 수정되면 이 행이 다른 노드에 전파될 때 충돌이 발생하거나 업데이트가 손실될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a73d-118">If a row is modified at more than one node, it can cause a conflict or even a lost update when the row is propagated to other nodes.</span></span>  
  
-   <span data-ttu-id="0a73d-119">변경 내용이 복제될 때에는 항상 약간의 지연이 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="0a73d-119">There is always some latency involved when changes are replicated.</span></span> <span data-ttu-id="0a73d-120">최신 변경 내용을 즉시 확인해야 하는 애플리케이션에서는 여러 노드에 걸쳐 동적으로 애플리케이션 부하를 분산할 경우 문제가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a73d-120">For applications that require the latest change to be seen immediately, dynamically load balancing the application across multiple nodes can be problematic.</span></span>  
  
 <span data-ttu-id="0a73d-121">피어 투 피어 복제에는 피어 투 피어 토폴로지에서 충돌을 검색할 수 있는 옵션이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a73d-121">Peer-to-peer replication includes the option to enable conflict detection across a peer-to-peer topology.</span></span> <span data-ttu-id="0a73d-122">이 옵션을 사용하면 일관성 없는 애플리케이션 동작, 업데이트 손실과 같은 검색되지 않는 충돌로 인해 발생하는 문제를 방지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a73d-122">This option helps prevent the issues that are caused from undetected conflicts, including inconsistent application behavior and lost updates.</span></span> <span data-ttu-id="0a73d-123">이 옵션을 설정하면 기본적으로 충돌을 일으키는 변경이 배포 에이전트 오류를 유발하는 치명적 오류로 취급됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a73d-123">By enabling this option, by default a conflicting change is treated as a critical error that causes the failure of the Distribution Agent.</span></span> <span data-ttu-id="0a73d-124">충돌이 발생하면 충돌이 수동으로 해결되고 데이터가 토폴로지 전체에서 일관성을 가질 때까지 토폴로지가 일관성 없는 상태로 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a73d-124">In the event of a conflict, the topology remains in an inconsistent state until the conflict is resolved manually and the data is made consistent across the topology.</span></span> <span data-ttu-id="0a73d-125">자세한 내용은 [Conflict Detection in Peer-to-Peer Replication](peer-to-peer-conflict-detection-in-peer-to-peer-replication.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0a73d-125">For more information, see [Conflict Detection in Peer-to-Peer Replication](peer-to-peer-conflict-detection-in-peer-to-peer-replication.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0a73d-126">데이터 불일치의 가능성을 배제하려면 충돌 검색이 설정되어 있는 경우라도 피어 투 피어 토폴로지에서 충돌이 발생하지 않도록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a73d-126">To avoid potential data inconsistency, make sure that you avoid conflicts in a peer-to-peer topology, even with conflict detection enabled.</span></span> <span data-ttu-id="0a73d-127">특정 행에 대한 쓰기 작업이 하나의 노드에서만 수행되도록 하려면 데이터에 액세스하여 변경하는 애플리케이션에서 삽입, 업데이트 및 삭제 작업을 분할해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a73d-127">To ensure that write operations for a particular row are performed at only one node, applications that access and change data must partition insert, update, and delete operations.</span></span> <span data-ttu-id="0a73d-128">이렇게 분할하면 한 노드에서 발생한 지정된 행에 대한 수정이 다른 노드에서 해당 행을 수정하기 전에 토폴로지의 모든 노드와 동기화됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a73d-128">This partitioning ensures that modifications to a given row originating at one node are synchronized with all other nodes in the topology before the row is modified by a different node.</span></span> <span data-ttu-id="0a73d-129">애플리케이션에 정교한 충돌 검색 및 해결 기능이 필요한 경우 병합 복제를 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="0a73d-129">If an application requires sophisticated conflict detection and resolution capabilities, use merge replication.</span></span> <span data-ttu-id="0a73d-130">자세한 내용은 [병합 복제](../merge/merge-replication.md) 및 [병합 복제 충돌 감지 및 해결](../merge/advanced-merge-replication-conflict-detection-and-resolution.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0a73d-130">For more information, see [Merge Replication](../merge/merge-replication.md) and [Detect and Resolve Merge Replication Conflicts](../merge/advanced-merge-replication-conflict-detection-and-resolution.md).</span></span>  
  
## <a name="peer-to-peer-topologies"></a><span data-ttu-id="0a73d-131">피어 투 피어 토폴로지</span><span class="sxs-lookup"><span data-stu-id="0a73d-131">Peer-to-Peer Topologies</span></span>  
 <span data-ttu-id="0a73d-132">다음 시나리오에서는 피어 투 피어 복제의 일반적 사용을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="0a73d-132">The following scenarios illustrate typical uses for peer-to-peer replication.</span></span>  
  
### <a name="topology-that-has-two-participating-databases"></a><span data-ttu-id="0a73d-133">참여하는 데이터베이스가 두 개인 토폴로지</span><span class="sxs-lookup"><span data-stu-id="0a73d-133">Topology That Has Two Participating Databases</span></span>  
 <span data-ttu-id="0a73d-134">![피어 투 피어 복제, 2노드](../media/repl-multinode-01.gif "피어 투 피어 복제, 2노드")</span><span class="sxs-lookup"><span data-stu-id="0a73d-134">![Peer-to-peer replication, two nodes](../media/repl-multinode-01.gif "Peer-to-peer replication, two nodes")</span></span>  
  
 <span data-ttu-id="0a73d-135">위의 두 그림에서는 참여하는 두 데이터베이스를 보여 주며 여기에서는 사용자 트래픽이 애플리케이션 서버를 통해 데이터베이스로 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a73d-135">Both of the preceding illustrations show two participating databases, with user traffic directed to the databases through an application server.</span></span> <span data-ttu-id="0a73d-136">이러한 구성은 웹 사이트에서 작업 그룹 애플리케이션에 이르기까지 다양한 애플리케이션에 사용할 수 있으며 다음과 같은 이점을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="0a73d-136">This configuration can be used for a variety of applications, from Web sites to workgroup applications, and provides the following benefits:</span></span>  
  
-   <span data-ttu-id="0a73d-137">두 개 이상의 서버에서 분산하여 읽게 되므로 읽기 성능이 향상됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a73d-137">Improved read performance, because reads are spread out over two servers.</span></span>  
  
-   <span data-ttu-id="0a73d-138">유지 관리가 필요하거나 한 노드에서 오류가 발생하는 경우에도 가용성이 높습니다.</span><span class="sxs-lookup"><span data-stu-id="0a73d-138">Higher availability if maintenance is required or in case of failure at one node.</span></span>  
  
 <span data-ttu-id="0a73d-139">두 그림에서는 참여하는 데이터베이스 간에 읽기 작업 로드의 균형이 조정되지만 업데이트는 다르게 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a73d-139">In both illustrations, read activity is load-balanced between the participating databases, but updates are handled differently:</span></span>  
  
-   <span data-ttu-id="0a73d-140">왼쪽 그림에서 업데이트는 두 서버 사이에 분할됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a73d-140">On the left, updates are partitioned between the two servers.</span></span> <span data-ttu-id="0a73d-141">예를 들어 데이터베이스에 제품 카탈로그가 포함된 경우 사용자 지정 애플리케이션을 지정하여 A-M으로 시작하는 제품 이름에 대해서는 노드 **A** 로, N-Z로 시작하는 제품 이름에 대해서는 노드 **B** 로 업데이트를 전송하도록 할 수 있습니다. 그러면 이후 업데이트가 노드 간에 상호 복제됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a73d-141">If the database contained a product catalog, you could, for example, have a custom application direct updates to node **A** for product names that start with A through M, and direct updates to node **B** for product names that start with N through Z. Updates are then replicated to the other node.</span></span>  
  
-   <span data-ttu-id="0a73d-142">오른쪽 그림에서는 업데이트 내용이 모두 노드 **B**로 전송된 다음 여기에서 노드 **A**로 복제됩니다. **B**가 유지 관리 등의 이유로 오프라인 상태인 경우 애플리케이션 서버는 모든 작업을 **A**로 전달할 수 있습니다. **B**가 다시 온라인 상태가 되면 업데이트 내용을 이동할 수 있으며, 애플리케이션 서버는 모든 업데이트 내용을 다시 **B**로 옮기거나 계속해서 **A**로 전송할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a73d-142">On the right, all updates are directed to node **B**. From there, updates are replicated to node **A**. If **B** is offline (for example, for maintenance), the application server can direct all activity to **A**. When **B** is back online, updates can flow to it, and the application server can move all updates back to **B** or keep directing them to **A**.</span></span>  
  
 <span data-ttu-id="0a73d-143">피어 투 피어 복제에는 두 가지 방법이 모두 지원되지만 표준 트랜잭션 복제에서는 오른쪽의 중앙 업데이트 예가 주로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a73d-143">Peer-to-peer replication can support either approach, but the central update example on the right is also often used with standard transactional replication.</span></span>  
  
### <a name="topologies-that-have-three-or-more-participating-databases"></a><span data-ttu-id="0a73d-144">참여하는 데이터베이스가 3개 이상인 토폴로지</span><span class="sxs-lookup"><span data-stu-id="0a73d-144">Topologies That Have Three or More Participating Databases</span></span>  
 <span data-ttu-id="0a73d-145">![여러 위치로 피어 투 피어 복제](../media/repl-multinode-02.gif "여러 위치로 피어 투 피어 복제")</span><span class="sxs-lookup"><span data-stu-id="0a73d-145">![Peer-to-peer replication to dispersed locations](../media/repl-multinode-02.gif "Peer-to-peer replication to dispersed locations")</span></span>  
  
 <span data-ttu-id="0a73d-146">위의 그림에서는 LA, 런던 및 타이베이에 지사가 있는 전세계적 소프트웨어 기술 지원 업체에 데이터를 제공하는 3개의 참여 데이터베이스를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="0a73d-146">The preceding illustration shows three participating databases that provide data for a worldwide software support organization, with offices in Los Angeles, London, and Taipei.</span></span> <span data-ttu-id="0a73d-147">각 지사의 기술 지원 엔지니어는 고객의 전화를 받으며 각 통화에 대한 정보를 입력하고 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="0a73d-147">The support engineers at each office take customer calls and enter and update information about each customer call.</span></span> <span data-ttu-id="0a73d-148">세 지사의 표준 시간대는 8시간씩 차이가 나므로 업무 시간이 중복되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0a73d-148">The time zones for the three offices are eight hours apart, so there is no overlap in the workday.</span></span> <span data-ttu-id="0a73d-149">타이베이 지사가 업무를 마감하면 런던 지사가 업무를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="0a73d-149">As the Taipei office closes, the London office is opening for the day.</span></span> <span data-ttu-id="0a73d-150">한 지사가 업무를 마감할 때 진행 중인 통화가 있으면 해당 통화는 다음으로 업무가 시작되는 지사의 담당자에게 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a73d-150">If a call is still in progress as one office is closing, the call is transferred to a representative at the next office to open.</span></span>  
  
 <span data-ttu-id="0a73d-151">각 위치에는 데이터베이스와 애플리케이션 서버가 있어 기술 지원 엔지니어가 고객 통화에 대한 정보를 입력하고 업데이트할 때 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a73d-151">Each location has a database and an application server, which are used by the support engineers as they enter and update information about customer calls.</span></span> <span data-ttu-id="0a73d-152">토폴로지는 시간별로 분할되므로</span><span class="sxs-lookup"><span data-stu-id="0a73d-152">The topology is partitioned by time.</span></span> <span data-ttu-id="0a73d-153">현재 업무를 진행 중인 노드에서만 업데이트가 발생하며 이후 다른 참여 데이터베이스로 업데이트 내용이 이동됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a73d-153">Therefore, updates occur only at the node that is currently open for business, and then the updates flow to the other participating databases.</span></span> <span data-ttu-id="0a73d-154">이러한 토폴로지를 사용하면 다음과 같은 이점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a73d-154">This topology provides the following benefits:</span></span>  
  
-   <span data-ttu-id="0a73d-155">격리하지 않아도 독립적으로 운영될 수 있습니다. 각 지사에서는 데이터를 독립적으로 삽입, 업데이트 또는 삭제할 수 있지만 참여하는 다른 모든 데이터베이스에 데이터가 복제되므로 데이터를 공유할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a73d-155">Independence without isolation: Each office can insert, update, or delete data independently but can also share the data because it is replicated to all other participating databases.</span></span>  
  
-   <span data-ttu-id="0a73d-156">참여하는 데이터베이스 중 하나 이상에서 오류가 발생하거나 유지 관리가 필요한 경우에도 높은 가용성을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="0a73d-156">Higher availability in case of failure or to allow maintenance at one or more of the participating databases.</span></span>  
  
     <span data-ttu-id="0a73d-157">![피어 투 피어 복제, 3-4노드](../media/repl-multinode-04.gif "피어 투 피어 복제, 3-4노드")</span><span class="sxs-lookup"><span data-stu-id="0a73d-157">![Peer-to-peer replication, three and four nodes](../media/repl-multinode-04.gif "Peer-to-peer replication, three and four nodes")</span></span>  
  
 <span data-ttu-id="0a73d-158">위의 그림에서는 3노드 토폴로지에 노드를 하나 더 추가하는 것을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="0a73d-158">The preceding illustration shows the addition of a node to the three-node topology.</span></span> <span data-ttu-id="0a73d-159">이 시나리오에서는 다음과 같은 이유로 노드를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a73d-159">A node could be added in this scenario for the following reasons:</span></span>  
  
-   <span data-ttu-id="0a73d-160">다른 지사가 개설되었습니다.</span><span class="sxs-lookup"><span data-stu-id="0a73d-160">Because another office is opened.</span></span>  
  
-   <span data-ttu-id="0a73d-161">디스크 오류나 그 밖의 주요한 오류 발생 시 내결함성을 높이기 위해 또는 유지 관리를 지원하기 위해 더 높은 가용성을 제공하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a73d-161">To provide higher availability to support maintenance or increase fault tolerance if a disk failure or other major failure occurs.</span></span>  
  
 <span data-ttu-id="0a73d-162">3노드 토폴로지와 4노드 토폴로지에서는 모든 데이터베이스가 다른 데이터베이스에 게시하고 다른 데이터베이스를 구독합니다.</span><span class="sxs-lookup"><span data-stu-id="0a73d-162">Notice that in both the three- and four-node topologies, all databases publish and subscribe to all other databases.</span></span> <span data-ttu-id="0a73d-163">따라서 하나 이상의 노드에 오류가 발생하거나 유지 관리가 필요한 경우 최대 가용성이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a73d-163">This provides maximum availability in case of maintenance needs or failure of one or more nodes.</span></span> <span data-ttu-id="0a73d-164">노드를 추가한 다음에는 성능과 배포 및 관리의 복잡성과 가용성 및 확장성 요구 사이에서 균형을 유지해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a73d-164">As nodes are added, you must balance availability and scalability needs against performance and the complexity of deployment and administration.</span></span>  
  
## <a name="configuring-peer-to-peer-replication"></a><span data-ttu-id="0a73d-165">피어 투 피어 복제 구성</span><span class="sxs-lookup"><span data-stu-id="0a73d-165">Configuring Peer-to-Peer Replication</span></span>  
 <span data-ttu-id="0a73d-166">피어 투 피어 복제 토폴로지의 구성은 일련의 표준 트랜잭션 게시 및 구독을 구성하는 것과 매우 유사합니다.</span><span class="sxs-lookup"><span data-stu-id="0a73d-166">Configuring a peer-to-peer replication topology is very similar to configuring a series of standard transactional publications and subscriptions.</span></span> <span data-ttu-id="0a73d-167">다음 항목에서 설명하는 단계에서는 피어 투 피어 토폴로지를 보여 주는 이전 그림의 왼쪽 구성과 유사한, 3개의 노드로 이루어진 시스템 구성을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="0a73d-167">The steps described in the following topics show the configuration of a three-node system, similar to the configuration shown on the left in the previous illustration that shows peer-to-peer topology.</span></span>  
  
## <a name="considerations-for-using-peer-to-peer-replication"></a><span data-ttu-id="0a73d-168">피어 투 피어 복제 사용 시 고려 사항</span><span class="sxs-lookup"><span data-stu-id="0a73d-168">Considerations for Using Peer-to-Peer Replication</span></span>  
 <span data-ttu-id="0a73d-169">이 섹션에서는 피어 투 피어 복제를 사용할 때 고려해야 할 정보와 지침을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="0a73d-169">This section provides information and guidelines to consider when you use peer-to-peer replication.</span></span>  
  
### <a name="general-considerations"></a><span data-ttu-id="0a73d-170">일반적인 고려 사항</span><span class="sxs-lookup"><span data-stu-id="0a73d-170">General Considerations</span></span>  
  
-   <span data-ttu-id="0a73d-171">피어 투 피어 복제는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]의 엔터프라이즈 버전에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a73d-171">Peer-to-peer replication is available only in Enterprise versions of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="0a73d-172">피어 투 피어 복제에 참여하는 모든 데이터베이스에는 동일한 스키마 및 데이터가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a73d-172">All databases that participate in peer-to-peer replication should contain identical schema and data:</span></span>  
  
    -   <span data-ttu-id="0a73d-173">개체 이름, 개체 스키마 및 게시 이름이 동일해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a73d-173">Object names, object schema, and publication names should be identical.</span></span>  
  
    -   <span data-ttu-id="0a73d-174">게시에서 스키마 변경 내용의 복제를 허용해야 합니다(게시 속성</span><span class="sxs-lookup"><span data-stu-id="0a73d-174">Publications must allow schema changes to be replicated.</span></span> <span data-ttu-id="0a73d-175">**replicate_ddl**에 대해 기본값인 **1** 설정. 자세한 내용은 [게시 데이터베이스의 스키마 변경](../publish/make-schema-changes-on-publication-databases.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0a73d-175">(This is a setting of **1** for the publication property **replicate_ddl**, which is the default setting.) For more information, see [Make Schema Changes on Publication Databases](../publish/make-schema-changes-on-publication-databases.md).</span></span>  
  
    -   <span data-ttu-id="0a73d-176">행 및 열 필터링은 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0a73d-176">Row and column filtering are not supported.</span></span>  
  
-   <span data-ttu-id="0a73d-177">각 노드가 고유한 배포 데이터베이스를 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="0a73d-177">We recommend that each node use its own distribution database.</span></span> <span data-ttu-id="0a73d-178">이렇게 하면 단일 지점에서 오류가 발생할 가능성이 없어집니다.</span><span class="sxs-lookup"><span data-stu-id="0a73d-178">This eliminates the potential of having a single point of failure.</span></span>  
  
-   <span data-ttu-id="0a73d-179">테이블 및 기타 개체는 단일 게시 데이터베이스 내의 여러 피어 투 피어 게시에 포함될 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0a73d-179">Tables and other objects cannot be included in multiple peer-to-peer publications in a single publication database.</span></span>  
  
-   <span data-ttu-id="0a73d-180">구독을 만들려면 먼저 게시에 피어 투 피어 복제를 사용할 수 있도록 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a73d-180">A publication must be enabled for peer-to-peer replication before any subscriptions are created.</span></span>  
  
-   <span data-ttu-id="0a73d-181">백업이나 **'replication support only'** 옵션을 사용하여 구독을 초기화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a73d-181">Subscriptions must be initialized by using a backup or with the **'replication support only'** option.</span></span> <span data-ttu-id="0a73d-182">자세한 내용은 [스냅샷 없이 트랜잭션 구독 초기화](../initialize-a-transactional-subscription-without-a-snapshot.md)에서 수동으로 구독을 초기화하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="0a73d-182">For more information, see [Initialize a Transactional Subscription Without a Snapshot](../initialize-a-transactional-subscription-without-a-snapshot.md).</span></span>  
  
-   <span data-ttu-id="0a73d-183">ID 열은 사용하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="0a73d-183">We do not recommend the use of identity columns.</span></span> <span data-ttu-id="0a73d-184">ID를 사용하는 경우 참여하는 각 데이터베이스에서 테이블에 할당된 범위를 수동으로 관리해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a73d-184">When using identities, you must manually manage the ranges assigned to the tables at each participating database.</span></span> <span data-ttu-id="0a73d-185">자세한 내용은 [ID 열 복제](../publish/replicate-identity-columns.md)에서 "ID 범위 수동 관리를 위한 범위 할당" 섹션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0a73d-185">For more information, see the section "Assigning Ranges for Manual Identity Range Management" in [Replicate Identity Columns](../publish/replicate-identity-columns.md).</span></span>  
  
### <a name="feature-restrictions"></a><span data-ttu-id="0a73d-186">기능 제한</span><span class="sxs-lookup"><span data-stu-id="0a73d-186">Feature Restrictions</span></span>  
 <span data-ttu-id="0a73d-187">피어 투 피어 복제는 트랜잭션 복제의 주요 기능을 지원하지만 다음 옵션은 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0a73d-187">Peer-to-peer replication supports the core features of transactional replication, but does not support the following options:</span></span>  
  
-   <span data-ttu-id="0a73d-188">스냅샷을 사용하여 초기화 및 다시 초기화</span><span class="sxs-lookup"><span data-stu-id="0a73d-188">Initialization and reinitialization with a snapshot.</span></span>  
  
-   <span data-ttu-id="0a73d-189">행 및 열 필터</span><span class="sxs-lookup"><span data-stu-id="0a73d-189">Row and column filters.</span></span>  
  
-   <span data-ttu-id="0a73d-190">타임스탬프 열</span><span class="sxs-lookup"><span data-stu-id="0a73d-190">Timestamp columns.</span></span>  
  
-   <span data-ttu-id="0a73d-191">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 이외 게시자 및 구독자</span><span class="sxs-lookup"><span data-stu-id="0a73d-191">Non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Publishers and Subscribers.</span></span>  
  
-   <span data-ttu-id="0a73d-192">즉시 업데이트 구독 및 지연 업데이트 구독</span><span class="sxs-lookup"><span data-stu-id="0a73d-192">Immediate updating and queued updating subscriptions.</span></span>  
  
-   <span data-ttu-id="0a73d-193">익명 구독</span><span class="sxs-lookup"><span data-stu-id="0a73d-193">Anonymous subscriptions.</span></span>  
  
-   <span data-ttu-id="0a73d-194">부분 구독</span><span class="sxs-lookup"><span data-stu-id="0a73d-194">Partial subscriptions.</span></span>  
  
-   <span data-ttu-id="0a73d-195">연결 가능한 구독 및 변환 가능한 구독</span><span class="sxs-lookup"><span data-stu-id="0a73d-195">Attachable subscriptions and transformable subscriptions.</span></span> <span data-ttu-id="0a73d-196">(두 옵션 모두 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]에서 사용되지 않습니다.)</span><span class="sxs-lookup"><span data-stu-id="0a73d-196">(Both of these options were deprecated in [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)].)</span></span>  
  
-   <span data-ttu-id="0a73d-197">공유 배포 에이전트</span><span class="sxs-lookup"><span data-stu-id="0a73d-197">Shared Distribution Agents.</span></span>  
  
-   <span data-ttu-id="0a73d-198">배포 에이전트 매개 변수 **-SubscriptionStreams** 및 로그 판독기 에이전트 매개 변수 **-MaxCmdsInTran**</span><span class="sxs-lookup"><span data-stu-id="0a73d-198">The Distribution Agent parameter **-SubscriptionStreams** and the Log Reader Agent parameter **-MaxCmdsInTran**.</span></span>  
  
-   <span data-ttu-id="0a73d-199">아티클 속성 \*\* \@ destination_owner\*\* 및 \*\* \@ destination_table\*\*.</span><span class="sxs-lookup"><span data-stu-id="0a73d-199">The article properties **\@destination_owner** and **\@destination_table**.</span></span>  

-   <span data-ttu-id="0a73d-200">피어 투 피어 트랜잭션 복제에서는 피어 투 피어 게시에 대한 단방향 트랜잭션 구독을 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0a73d-200">Peer-to-Peer transactional replication does not support creating a one-way transactional subscription to a Peer-to-Peer publication</span></span>
  
 <span data-ttu-id="0a73d-201">다음 속성에는 특별히 고려할 사항이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a73d-201">The following properties have special considerations:</span></span>  
  
-   <span data-ttu-id="0a73d-202">게시 속성 \*\* \@ allow_initialize_from_backup\*\* 에는 값이 필요 `true` 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a73d-202">The publication property **\@allow_initialize_from_backup** requires a value of `true`.</span></span>  
  
-   <span data-ttu-id="0a73d-203">아티클 속성 \*\* \@ replicate_ddl\*\* 에는 값이 필요 합니다 `true` . \*\* \@ identityrangemanagementoption\*\* 에는 값이 필요 합니다 `manual` . 및 \*\* \@ 상태\*\* 에는 옵션 **24** 가 설정 되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a73d-203">The article property **\@replicate_ddl** requires a value of `true`; **\@identityrangemanagementoption** requires a value of `manual`; and **\@status** requires that option **24** is set.</span></span>  
  
-   <span data-ttu-id="0a73d-204">아티클 속성 \*\* \@ ins_cmd**, \*\* \@ del_cmd**및 \*\* \@ upd_cmd\*\* 값은로 설정할 수 없습니다 `SQL` .</span><span class="sxs-lookup"><span data-stu-id="0a73d-204">The value for article properties **\@ins_cmd**, **\@del_cmd**, and **\@upd_cmd** cannot be set to `SQL`.</span></span>  
  
-   <span data-ttu-id="0a73d-205">Subscription 속성 \*\* \@ sync_type\*\* 에는 또는 값이 필요 합니다 `none` `automatic` .</span><span class="sxs-lookup"><span data-stu-id="0a73d-205">The subscription property **\@sync_type** requires a value of `none` or `automatic`.</span></span>  
  
### <a name="maintenance-considerations"></a><span data-ttu-id="0a73d-206">유지 관리 고려 사항</span><span class="sxs-lookup"><span data-stu-id="0a73d-206">Maintenance Considerations</span></span>  
 <span data-ttu-id="0a73d-207">다음 동작을 수행하려면 시스템을 정지해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a73d-207">The following actions require the system to be quiesced.</span></span> <span data-ttu-id="0a73d-208">즉, 모든 노드에서 게시된 테이블에 대한 작업을 중지하고 각 노드가 다른 모든 노드의 변경 내용을 모두 받았는지 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a73d-208">This means stopping activity on published tables at all nodes and making sure that each node has received all changes from all other nodes.</span></span>  
  
-   <span data-ttu-id="0a73d-209">[!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]기존 토폴로지에 노드 추가</span><span class="sxs-lookup"><span data-stu-id="0a73d-209">Adding a [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] node to an existing topology</span></span>  
  
-   <span data-ttu-id="0a73d-210">기존 게시에 아티클 추가</span><span class="sxs-lookup"><span data-stu-id="0a73d-210">Adding an article to an existing publication</span></span>  
  
-   <span data-ttu-id="0a73d-211">스키마 변경</span><span class="sxs-lookup"><span data-stu-id="0a73d-211">Making schema changes</span></span>  
  
-   <span data-ttu-id="0a73d-212">백업에서 노드 복원</span><span class="sxs-lookup"><span data-stu-id="0a73d-212">Restoring a node from a backup</span></span>  
  
 <span data-ttu-id="0a73d-213">자세한 내용은 [복제 토폴로지 정지&#40;복제 Transact-SQL 프로그래밍&#41;](../administration/quiesce-a-replication-topology-replication-transact-sql-programming.md) 및 [피어 투 피어 토폴로지 관리&#40;복제 Transact-SQL 프로그래밍&#41;](../administration/administer-a-peer-to-peer-topology-replication-transact-sql-programming.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0a73d-213">For more information, see [Quiesce a Replication Topology &#40;Replication Transact-SQL Programming&#41;](../administration/quiesce-a-replication-topology-replication-transact-sql-programming.md) and [Administer a Peer-to-Peer Topology &#40;Replication Transact-SQL Programming&#41;](../administration/administer-a-peer-to-peer-topology-replication-transact-sql-programming.md).</span></span>  
  
-   <span data-ttu-id="0a73d-214">피어 투 피어 토폴로지에 새 노드를 추가하는 경우 새 노드가 추가된 후 만들어진 백업에서만 복원해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a73d-214">If you add a new node to a peer-to-peer topology, you should restore only from backups that were created after the new node was added.</span></span>  
  
-   <span data-ttu-id="0a73d-215">피어 투 피어 토폴로지에서 구독을 다시 초기화할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0a73d-215">You cannot reinitialize subscriptions in a peer-to-peer topology.</span></span> <span data-ttu-id="0a73d-216">노드에 새로운 데이터 복사본을 유지하려면 해당 노드에서 백업을 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="0a73d-216">If you have to ensure that a node has a new copy of the data, restore a backup at the node.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a73d-217">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0a73d-217">See Also</span></span>  
 <span data-ttu-id="0a73d-218">[피어 투 피어 토폴로지 관리&#40;복제 Transact-SQL 프로그래밍&#41;](../administration/administer-a-peer-to-peer-topology-replication-transact-sql-programming.md) </span><span class="sxs-lookup"><span data-stu-id="0a73d-218">[Administer a Peer-to-Peer Topology &#40;Replication Transact-SQL Programming&#41;](../administration/administer-a-peer-to-peer-topology-replication-transact-sql-programming.md) </span></span>  
 <span data-ttu-id="0a73d-219">[스냅샷 및 트랜잭션 복제의 백업 및 복원을 위한 전략](../administration/strategies-for-backing-up-and-restoring-snapshot-and-transactional-replication.md) </span><span class="sxs-lookup"><span data-stu-id="0a73d-219">[Strategies for Backing Up and Restoring Snapshot and Transactional Replication](../administration/strategies-for-backing-up-and-restoring-snapshot-and-transactional-replication.md) </span></span>  
 [<span data-ttu-id="0a73d-220">트랜잭션 복제에 대한 게시 유형</span><span class="sxs-lookup"><span data-stu-id="0a73d-220">Publication Types for Transactional Replication</span></span>](transactional-replication.md)  
  
  
