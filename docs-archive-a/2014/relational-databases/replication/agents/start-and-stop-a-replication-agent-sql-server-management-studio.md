---
title: 복제 에이전트 시작 및 중지(SQL Server Management Studio) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- agents [SQL Server replication], stopping
- agents [SQL Server replication], starting
ms.assetid: 97977c4a-8c7c-4a22-9480-69aa812bd1e5
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b40e329e0f04e8a54a2d5a40c30aff418da2cd65
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646945"
---
# <a name="start-and-stop-a-replication-agent-sql-server-management-studio"></a><span data-ttu-id="32327-102">복제 에이전트 시작 및 중지(SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="32327-102">Start and Stop a Replication Agent (SQL Server Management Studio)</span></span>
  <span data-ttu-id="32327-103">[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 및 복제 모니터에 있는 **작업** 폴더와 **복제** 폴더에서 에이전트를 시작하고 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="32327-103">Start and stop agents from the **Jobs** folder and the **Replication** folder in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] and from Replication Monitor.</span></span> <span data-ttu-id="32327-104">다음 에이전트 및 작업을 시작하고 중지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="32327-104">Start and stop the following agents and jobs:</span></span>  
  
-   <span data-ttu-id="32327-105">스냅샷 에이전트 - 모든 게시에서 사용</span><span class="sxs-lookup"><span data-stu-id="32327-105">The Snapshot Agent, which is used by all publications.</span></span>  
  
-   <span data-ttu-id="32327-106">로그 판독기 에이전트 - 모든 트랜잭션 게시에서 사용</span><span class="sxs-lookup"><span data-stu-id="32327-106">The Log Reader Agent, which is used by all transactional publications.</span></span>  
  
-   <span data-ttu-id="32327-107">큐 판독기 에이전트 - 지연 업데이트 구독이 활성화된 트랜잭션 게시에서 사용</span><span class="sxs-lookup"><span data-stu-id="32327-107">The Queue Reader Agent, which is used by transactional publications enabled for queued updating subscriptions.</span></span>  
  
-   <span data-ttu-id="32327-108">배포 에이전트 - 구독을 트랜잭션 및 스냅샷 게시와 동기화함</span><span class="sxs-lookup"><span data-stu-id="32327-108">The Distribution Agent, which synchronizes subscriptions to transactional and snapshot publications.</span></span>  
  
-   <span data-ttu-id="32327-109">병합 에이전트 - 구독을 병합 게시와 동기화함</span><span class="sxs-lookup"><span data-stu-id="32327-109">The Merge Agent, which synchronizes subscriptions to merge publications.</span></span>  
  
-   <span data-ttu-id="32327-110">복제 유지 관리 작업</span><span class="sxs-lookup"><span data-stu-id="32327-110">Replication maintenance jobs.</span></span>  
  
 <span data-ttu-id="32327-111">병합 에이전트 및 배포 에이전트를 시작하는 방법은 [밀어넣기 구독 동기화](../synchronize-a-push-subscription.md) 및 [끌어오기 구독 동기화](../synchronize-a-pull-subscription.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="32327-111">For more information about starting the Merge Agent and the Distribution Agent, see [Synchronize a Push Subscription](../synchronize-a-push-subscription.md) and [Synchronize a Pull Subscription](../synchronize-a-pull-subscription.md).</span></span> <span data-ttu-id="32327-112">유지 관리 작업에 대한 자세한 내용은 [복제 유지 관리 작업 실행&#40;SQL Server Management Studio&#41;](../../../ssms/sql-server-management-studio-ssms.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="32327-112">For more information about maintenance jobs, see [Run Replication Maintenance Jobs &#40;SQL Server Management Studio&#41;](../../../ssms/sql-server-management-studio-ssms.md).</span></span>  
  
 <span data-ttu-id="32327-113">복제 모니터를 시작하는 방법은 [복제 모니터 시작](../monitor/start-the-replication-monitor.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="32327-113">For information about starting Replication Monitor, see [Start the Replication Monitor](../monitor/start-the-replication-monitor.md).</span></span>  
  
### <a name="to-start-and-stop-a-snapshot-agent-or-log-reader-agent-from-management-studio"></a><span data-ttu-id="32327-114">Management Studio에서 스냅샷 에이전트 또는 로그 판독기 에이전트를 시작하고 중지하려면</span><span class="sxs-lookup"><span data-stu-id="32327-114">To start and stop a Snapshot Agent or Log Reader Agent from Management Studio</span></span>  
  
1.  <span data-ttu-id="32327-115">[!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]에서 게시자에 연결한 다음 해당 서버 노드 및 **복제** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="32327-115">Connect to the Publisher in [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)], and then expand the server node and the **Replication** folder.</span></span>  
  
2.  <span data-ttu-id="32327-116">**로컬 게시** 폴더를 확장한 다음 게시를 마우스 오른쪽 단추로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="32327-116">Expand the **Local Publications** folder, and then right-click a publication.</span></span>  
  
3.  <span data-ttu-id="32327-117">**스냅샷 에이전트 상태 보기** 또는 **로그 판독기 에이전트 상태 보기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="32327-117">Click **View Snapshot Agent Status** or **View Log Reader Agent Status**.</span></span>  
  
4.  <span data-ttu-id="32327-118">**시작** 또는 **중지**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="32327-118">Click **Start** or **Stop**.</span></span>  
  
### <a name="to-start-and-stop-a-queue-reader-agent-from-management-studio"></a><span data-ttu-id="32327-119">Management Studio에서 큐 판독기 에이전트를 시작하고 중지하려면</span><span class="sxs-lookup"><span data-stu-id="32327-119">To start and stop a Queue Reader Agent from Management Studio</span></span>  
  
1.  <span data-ttu-id="32327-120">[!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]에서 배포자에 연결한 다음 해당 서버 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="32327-120">Connect to the Distributor in [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="32327-121">**SQL Server 에이전트** 폴더를 확장한 다음 **작업** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="32327-121">Expand the **SQL Server Agent** folder, and then expand the **Jobs** folder.</span></span>  
  
3.  <span data-ttu-id="32327-122">에이전트에 대한 작업을 마우스 오른쪽 단추로 클릭한 다음 **작업 시작** 또는 **작업 중지**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="32327-122">Right-click the job for the agent, and then click **Start Job** or **Stop Job**.</span></span> <span data-ttu-id="32327-123">큐 판독기 에이전트에 대한 작업 이름의 형식은 **[\<Distributor>].\<integer>** 입니다.</span><span class="sxs-lookup"><span data-stu-id="32327-123">The name of the job for the Queue Reader Agent is in the form **[\<Distributor>].\<integer>**.</span></span>  
  
### <a name="to-start-and-stop-a-snapshot-agent-log-reader-agent-or-queue-reader-agent-from-replication-monitor"></a><span data-ttu-id="32327-124">복제 모니터에서 스냅샷 에이전트, 로그 판독기 에이전트 또는 큐 판독기 에이전트를 시작하고 중지하려면</span><span class="sxs-lookup"><span data-stu-id="32327-124">To start and stop a Snapshot Agent, Log Reader Agent, or Queue Reader Agent from Replication Monitor</span></span>  
  
1.  <span data-ttu-id="32327-125">왼쪽 창에서 게시자 그룹을 확장하고 해당 게시자를 확장한 다음 해당 게시를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="32327-125">Expand a Publisher group in the left pane, expand a Publisher, and then click a publication.</span></span>  
  
2.  <span data-ttu-id="32327-126">**에이전트** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="32327-126">Click the **Agents** tab.</span></span>  
  
3.  <span data-ttu-id="32327-127">에이전트를 마우스 오른쪽 단추로 클릭한 다음 **에이전트 시작** 또는 **에이전트 중지**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="32327-127">Right-click an agent, and then click **Start Agent** or **Stop Agent**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32327-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="32327-128">See Also</span></span>  
 <span data-ttu-id="32327-129">[복제 모니터링](../monitoring-replication.md) </span><span class="sxs-lookup"><span data-stu-id="32327-129">[Monitoring Replication](../monitoring-replication.md) </span></span>  
 <span data-ttu-id="32327-130">[복제 에이전트 실행 파일 개념](../concepts/replication-agent-executables-concepts.md) </span><span class="sxs-lookup"><span data-stu-id="32327-130">[Replication Agent Executables Concepts](../concepts/replication-agent-executables-concepts.md) </span></span>  
 [<span data-ttu-id="32327-131">복제 에이전트 개요</span><span class="sxs-lookup"><span data-stu-id="32327-131">Replication Agents Overview</span></span>](replication-agents-overview.md)  
  
  
