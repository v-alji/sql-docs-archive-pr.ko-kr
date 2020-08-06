---
title: 복제 에이전트 모니터링 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- monitoring performance [SQL Server replication], agents
- Log Reader Agent, monitoring
- Replication Monitor, agents
- Merge Agent, monitoring
- Queue Reader Agent, monitoring
- Snapshot Agent, monitoring
- agents [SQL Server replication], monitoring
- Distribution Agent, monitoring
ms.assetid: d06ed24f-82d7-4b9e-9e40-cc9780476a71
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: baa22ef9e9f7c4621f76838e82c309d17f1e12a6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648934"
---
# <a name="monitor-replication-agents"></a><span data-ttu-id="6c120-102">복제 에이전트 모니터링</span><span class="sxs-lookup"><span data-stu-id="6c120-102">Monitor Replication Agents</span></span>
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] <span data-ttu-id="6c120-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 복제 모니터는 복제 작업에 대한 구조적 뷰를 제공할 뿐만 아니라 특정 에이전트에서 정보를 간단하게 찾을 수 있게 해줍니다.</span><span class="sxs-lookup"><span data-stu-id="6c120-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Replication Monitor provides a systemic view of replication activity, but also makes it straightforward to find information on a specific agent.</span></span> <span data-ttu-id="6c120-104">다음 목록에는 각 에이전트, 에이전트를 찾을 수 있는 복제 모니터의 탭 및 이러한 탭에 액세스하는 방법을 설명하는 항목에 대한 링크가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c120-104">The following list includes each agent, the tabs in the Replication Monitor on which it can be found, and a link to a topic that explains how to access these tabs:</span></span>  
  
-   <span data-ttu-id="6c120-105">다음 에이전트는 복제 모니터에서 게시와 연결됩니다.</span><span class="sxs-lookup"><span data-stu-id="6c120-105">The following agents are associated with publications in Replication Monitor:</span></span>  
  
    -   <span data-ttu-id="6c120-106">스냅샷 에이전트</span><span class="sxs-lookup"><span data-stu-id="6c120-106">Snapshot Agent</span></span>  
  
    -   <span data-ttu-id="6c120-107">로그 판독기 에이전트</span><span class="sxs-lookup"><span data-stu-id="6c120-107">Log Reader Agent</span></span>  
  
    -   <span data-ttu-id="6c120-108">큐 판독기 에이전트</span><span class="sxs-lookup"><span data-stu-id="6c120-108">Queue Reader Agent</span></span>  
  
     <span data-ttu-id="6c120-109">이러한 에이전트와 연결된 정보 및 작업은 **에이전트**(각 게시자 및 구독에 대해 사용 가능) 및 **경고**(각 게시에 대해 사용 가능) 탭을 통해 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c120-109">Access information and tasks associated with these agents through the following tabs: **Agents** (available for each Publisher and publication) and **Warnings** (available for each publication).</span></span> <span data-ttu-id="6c120-110">자세한 내용은 [복제 모니터를 사용하여 정보 보기 및 태스크 수행](view-information-and-perform-tasks-replication-monitor.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6c120-110">For more information, see [View Information and Perform Tasks using Replication Monitor](view-information-and-perform-tasks-replication-monitor.md).</span></span>  
  
-   <span data-ttu-id="6c120-111">다음 에이전트는 복제 모니터에서 구독과 연결됩니다.</span><span class="sxs-lookup"><span data-stu-id="6c120-111">The following agents are associated with subscriptions in Replication Monitor:</span></span>  
  
    -   <span data-ttu-id="6c120-112">배포 에이전트</span><span class="sxs-lookup"><span data-stu-id="6c120-112">Distribution Agent</span></span>  
  
    -   <span data-ttu-id="6c120-113">병합 에이전트</span><span class="sxs-lookup"><span data-stu-id="6c120-113">Merge Agent</span></span>  
  
     <span data-ttu-id="6c120-114">이러한 에이전트와 연결된 정보 및 작업은 **구독 조사 목록**(각 게시자에 대해 사용 가능) 또는 **모든 구독** 탭(각 게시에 대해 사용 가능)을 통해 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c120-114">Access information and tasks associated with these agents through the following tabs: **Subscription Watch List** (available for each Publisher) or the **All Subscriptions** tab (available for each publication).</span></span> <span data-ttu-id="6c120-115">자세한 내용은 [복제 모니터를 사용하여 정보 보기 및 태스크 수행](view-information-and-perform-tasks-replication-monitor.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6c120-115">For more information, see [View Information and Perform Tasks using Replication Monitor](view-information-and-perform-tasks-replication-monitor.md).</span></span>  
  
## <a name="using-sql-server-management-studio-to-monitor-replication-agents"></a><span data-ttu-id="6c120-116">SQL Server Management Studio를 사용하여 복제 에이전트 모니터링</span><span class="sxs-lookup"><span data-stu-id="6c120-116">Using SQL Server Management Studio to Monitor Replication Agents</span></span>  
 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] <span data-ttu-id="6c120-117">[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]는 복제 에이전트 모니터링을 위한 다음 대화 상자를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="6c120-117">[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] provides the following dialog boxes for monitoring replication agents:</span></span>  
  
-   <span data-ttu-id="6c120-118">**스냅샷 에이전트 상태 보기** (모든 게시용)</span><span class="sxs-lookup"><span data-stu-id="6c120-118">**View Snapshot Agent Status** (for all publications)</span></span>  
  
-   <span data-ttu-id="6c120-119">**로그 판독기 에이전트 상태 보기** (모든 트랜잭션 게시용)</span><span class="sxs-lookup"><span data-stu-id="6c120-119">**View Log Reader Agent Status** (for all transactional publications)</span></span>  
  
-   <span data-ttu-id="6c120-120">**동기화 상태 보기** (모든 구독용. 이 대화 상자로 배포 에이전트 및 병합 에이전트에 액세스할 수 있음)</span><span class="sxs-lookup"><span data-stu-id="6c120-120">**View Synchronization Status** (for all subscriptions; this dialog box allows access to the Distribution Agent and the Merge Agent)</span></span>  
  
 <span data-ttu-id="6c120-121">복제 모니터는 각 에이전트에 대한 추가 정보를 제공하고 큐 판독기 에이전트 사용 시 해당 에이전트를 모니터링합니다.</span><span class="sxs-lookup"><span data-stu-id="6c120-121">Replication Monitor provides additional information about each agent and provides monitoring for the Queue Reader Agent, if it is used.</span></span> <span data-ttu-id="6c120-122">자세한 내용은 [복제 모니터를 사용하여 정보 보기 및 태스크 수행](view-information-and-perform-tasks-replication-monitor.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6c120-122">For more information, see [View Information and Perform Tasks using Replication Monitor](view-information-and-perform-tasks-replication-monitor.md).</span></span>  
  
#### <a name="to-monitor-the-snapshot-agent-and-log-reader-agent"></a><span data-ttu-id="6c120-123">스냅샷 에이전트 및 로그 판독기 에이전트를 모니터링하려면</span><span class="sxs-lookup"><span data-stu-id="6c120-123">To monitor the Snapshot Agent and Log Reader Agent</span></span>  
  
1.  <span data-ttu-id="6c120-124">[!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]에서 게시자에 연결한 다음 해당 서버 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="6c120-124">Connect to the Publisher in [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="6c120-125">**복제** 폴더를 확장한 다음 **로컬 게시** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="6c120-125">Expand the **Replication** folder, and then expand the **Local Publications** folder.</span></span>  
  
3.  <span data-ttu-id="6c120-126">게시를 마우스 오른쪽 단추로 클릭한 다음 **로그 판독기 에이전트 상태 보기** 또는 **스냅샷 에이전트 상태 보기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6c120-126">Right-click a publication, and then click **View Log Reader Agent Status** or **View Snapshot Agent Status**.</span></span>  
  
4.  <span data-ttu-id="6c120-127">**로그 판독기 에이전트 상태 보기** 또는 **스냅샷 에이전트 상태 보기** 대화 상자에서 다음을 수행하십시오.</span><span class="sxs-lookup"><span data-stu-id="6c120-127">In the **View Log Reader Agent Status** or **View Snapshot Agent Status** dialog box:</span></span>  
  
    -   <span data-ttu-id="6c120-128">에이전트 상태를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="6c120-128">View agent status.</span></span>  
  
    -   <span data-ttu-id="6c120-129">필요에 맞게 에이전트를 시작 또는 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="6c120-129">Start or stop the agent if necessary.</span></span>  
  
    -   <span data-ttu-id="6c120-130">**모니터** 를 클릭하여 **복제 모니터**를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="6c120-130">Click **Monitor** to launch **Replication Monitor**.</span></span>  
  
5.  <span data-ttu-id="6c120-131">**닫기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6c120-131">Click **Close**.</span></span>  
  
#### <a name="to-monitor-the-distribution-agent-and-merge-agent-from-the-publisher"></a><span data-ttu-id="6c120-132">게시자에서 배포 에이전트 및 병합 에이전트를 모니터링하려면</span><span class="sxs-lookup"><span data-stu-id="6c120-132">To monitor the Distribution Agent and Merge Agent (from the Publisher)</span></span>  
  
1.  <span data-ttu-id="6c120-133">[!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]에서 게시자에 연결한 다음 해당 서버 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="6c120-133">Connect to the Publisher in [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="6c120-134">**복제** 폴더를 확장한 다음 **로컬 게시** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="6c120-134">Expand the **Replication** folder, and then expand the **Local Publications** folder.</span></span>  
  
3.  <span data-ttu-id="6c120-135">모니터링할 구독에 대한 게시를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="6c120-135">Expand the publication for the subscription you want to monitor.</span></span>  
  
4.  <span data-ttu-id="6c120-136">해당 구독을 마우스 오른쪽 단추로 클릭한 다음 **동기화 상태 보기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6c120-136">Right-click the subscription, and then click **View Synchronization Status**.</span></span>  
  
5.  <span data-ttu-id="6c120-137">**동기화 상태 보기** 대화 상자에서 다음을 수행하십시오.</span><span class="sxs-lookup"><span data-stu-id="6c120-137">In the **View Synchronization Status** dialog box:</span></span>  
  
    -   <span data-ttu-id="6c120-138">에이전트 상태를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="6c120-138">View agent status.</span></span>  
  
    -   <span data-ttu-id="6c120-139">필요에 맞게 에이전트를 시작 또는 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="6c120-139">Start or stop the agent if necessary.</span></span>  
  
    -   <span data-ttu-id="6c120-140">밀어넣기 구독의 경우 **모니터** 를 클릭하여 **복제 모니터**를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="6c120-140">For push subscriptions, click **Monitor** to launch **Replication Monitor**.</span></span>  
  
    -   <span data-ttu-id="6c120-141">끌어오기 구독의 경우 **작업 기록 보기** 를 클릭하여 에이전트 로그의 출력을 표시하는 **로그 파일 뷰어**를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="6c120-141">For pull subscriptions, click **View Job History** to launch the **Log File Viewer**, which displays output from the agent log.</span></span>  
  
6.  <span data-ttu-id="6c120-142">**닫기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6c120-142">Click **Close**.</span></span>  
  
#### <a name="to-monitor-the-distribution-agent-and-merge-agent-from-the-subscriber"></a><span data-ttu-id="6c120-143">구독자에서 배포 에이전트 및 병합 에이전트를 모니터링하려면</span><span class="sxs-lookup"><span data-stu-id="6c120-143">To monitor the Distribution Agent and Merge Agent (from the Subscriber)</span></span>  
  
1.  <span data-ttu-id="6c120-144">[!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]에서 구독자에 연결한 다음 해당 서버 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="6c120-144">Connect to the Subscriber in [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="6c120-145">**복제** 폴더를 확장한 다음 **로컬 구독** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="6c120-145">Expand the **Replication** folder, and then expand the **Local Subscriptions** folder.</span></span>  
  
3.  <span data-ttu-id="6c120-146">모니터링할 구독을 마우스 오른쪽 단추로 클릭한 다음 **동기화 상태 보기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6c120-146">Right-click the subscription you want to monitor, and then click **View Synchronization Status**.</span></span>  
  
4.  <span data-ttu-id="6c120-147">**동기화 상태 보기** 대화 상자에서 다음을 수행하십시오.</span><span class="sxs-lookup"><span data-stu-id="6c120-147">In the **View Synchronization Status** dialog box:</span></span>  
  
    -   <span data-ttu-id="6c120-148">에이전트 상태를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="6c120-148">View agent status.</span></span>  
  
    -   <span data-ttu-id="6c120-149">필요에 맞게 에이전트를 시작 또는 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="6c120-149">Start or stop the agent if necessary.</span></span>  
  
    -   <span data-ttu-id="6c120-150">**작업 기록 보기** 를 클릭하여 에이전트 로그의 출력을 표시하는 **로그 파일 뷰어**를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="6c120-150">Click **View Job History** to launch the **Log File Viewer**, which displays output from the agent log.</span></span>  
  
5.  <span data-ttu-id="6c120-151">**닫기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6c120-151">Click **Close**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c120-152">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6c120-152">See Also</span></span>  
 <span data-ttu-id="6c120-153">[복제 모니터링](../monitoring-replication.md) </span><span class="sxs-lookup"><span data-stu-id="6c120-153">[Monitoring Replication](../monitoring-replication.md) </span></span>  
 [<span data-ttu-id="6c120-154">복제 에이전트 개요</span><span class="sxs-lookup"><span data-stu-id="6c120-154">Replication Agents Overview</span></span>](../agents/replication-agents-overview.md)  
  
  
