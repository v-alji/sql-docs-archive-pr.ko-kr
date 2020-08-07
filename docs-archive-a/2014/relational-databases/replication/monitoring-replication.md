---
title: 복제 모니터링 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- monitoring performance [SQL Server replication], about monitoring replication
- transactional replication, monitoring
- monitoring [SQL Server replication]
- merge replication monitoring [SQL Server replication]
- snapshot replication [SQL Server], monitoring
- replication [SQL Server], monitoring
- administering replication, monitoring
ms.assetid: f182f43a-6af8-45bc-a708-08d5f7a6984a
author: rothja
ms.author: jroth
ms.openlocfilehash: df2760e4ce04c95f38ceb9dfe9fa9f79c4c467f3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87733979"
---
# <a name="monitoring-replication"></a><span data-ttu-id="69d3b-102">모니터링(복제)</span><span class="sxs-lookup"><span data-stu-id="69d3b-102">Monitoring (Replication)</span></span>
  <span data-ttu-id="69d3b-103">복제 토폴로지의 모니터링은 복제 배포의 중요한 부분입니다.</span><span class="sxs-lookup"><span data-stu-id="69d3b-103">Monitoring a replication topology is an important aspect of deploying replication.</span></span> <span data-ttu-id="69d3b-104">복제 작업이 배포되므로 복제에 관련된 모든 컴퓨터에서 활동 및 상태를 추적해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="69d3b-104">Because replication activity is distributed, it is essential to track activity and status across all computers involved in replication.</span></span> <span data-ttu-id="69d3b-105">다음 도구를 사용하여 복제를 모니터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="69d3b-105">The following tools can be used to monitor replication:</span></span>  
  
-   [!INCLUDE[msCoName](../../includes/msCoName-md.md)]<span data-ttu-id="69d3b-106">[!INCLUDE[ssNoVersion](../../includes/ssNoVersion-md.md)]복제 모니터</span><span class="sxs-lookup"><span data-stu-id="69d3b-106">[!INCLUDE[ssNoVersion](../../includes/ssNoVersion-md.md)] Replication Monitor</span></span>  
  
     <span data-ttu-id="69d3b-107">복제 모니터는 복제를 모니터링하기 위한 가장 중요한 도구이며 모두 복제 작업을 게시자 관점으로 볼 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="69d3b-107">Replication Monitor is the most important tool for monitoring replication, presenting a Publisher-focused view of all replication activity.</span></span> <span data-ttu-id="69d3b-108">자세한 내용은 [복제 모니터를 사용 하 여 성능 모니터링](monitor/monitor-performance-with-replication-monitor.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="69d3b-108">For more information, see [Monitor performance with Replication Monitor](monitor/monitor-performance-with-replication-monitor.md).</span></span>  
  
-   [!INCLUDE[msCoName](../../includes/msCoName-md.md)] <span data-ttu-id="69d3b-109">[!INCLUDE[ssManStudioFull](../../includes/ssManStudioFull-md.md)]</span><span class="sxs-lookup"><span data-stu-id="69d3b-109">[!INCLUDE[ssManStudioFull](../../includes/ssManStudioFull-md.md)]</span></span>  
  
     [!INCLUDE[ssManStudio](../../includes/ssManStudio-md.md)] <span data-ttu-id="69d3b-110">는 복제 모니터에 대한 액세스를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="69d3b-110">provides access to Replication Monitor.</span></span> <span data-ttu-id="69d3b-111">또한 로그 판독기 에이전트, 스냅샷 에이전트, 병합 에이전트 및 배포 에이전트에 의해 기록된 현재 상태 및 마지막 메시지를 보고 각 에이전트를 시작 및 중지할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="69d3b-111">It also allows you to view the current status and last message logged by the following agents and allows you start and stop each agent: Log Reader Agent, Snapshot Agent, Merge Agent, and Distribution Agent.</span></span> <span data-ttu-id="69d3b-112">자세한 내용은 [Monitor Replication Agents](monitor/monitor-replication-agents.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="69d3b-112">For more information, see [Monitor Replication Agents](monitor/monitor-replication-agents.md).</span></span>  
  
-   [!INCLUDE[tsql](../../includes/tsql-md.md)] <span data-ttu-id="69d3b-113">및 RMO(복제 관리 개체)</span><span class="sxs-lookup"><span data-stu-id="69d3b-113">and Replication Management Objects (RMO)</span></span>  
  
     <span data-ttu-id="69d3b-114">두 인터페이스 모두 배포자의 모든 복제 유형을 모니터링할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="69d3b-114">Both interfaces allow you to monitor all types of replication from the Distributor.</span></span> <span data-ttu-id="69d3b-115">또한 병합 복제는 구독자의 복제를 모니터링하는 기능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="69d3b-115">Merge replication also provides the ability to monitor replication from the Subscriber.</span></span>  
  
-   <span data-ttu-id="69d3b-116">복제 에이전트 이벤트에 대한 경고</span><span class="sxs-lookup"><span data-stu-id="69d3b-116">Alerts for replication agent events</span></span>  
  
     <span data-ttu-id="69d3b-117">복제는 복제 에이전트 이벤트에 대해 미리 정의된 다양한 경고를 제공하고 필요한 경우 추가 경고를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="69d3b-117">Replication provides a number of predefined alerts for replication agent events, and you can create additional alerts if necessary.</span></span> <span data-ttu-id="69d3b-118">경고를 사용하여 이벤트에 대한 자동 응답을 수행하거나 관리자에게 이벤트 상태를 알릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="69d3b-118">Alerts can be used to trigger an automated response to an event and/or notify an administrator.</span></span> <span data-ttu-id="69d3b-119">자세한 내용은 [복제 에이전트 이벤트에 대한 경고 사용](agents/use-alerts-for-replication-agent-events.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="69d3b-119">For more information, see [Use Alerts for Replication Agent Events](agents/use-alerts-for-replication-agent-events.md).</span></span>  
  
-   <span data-ttu-id="69d3b-120">시스템 모니터</span><span class="sxs-lookup"><span data-stu-id="69d3b-120">System Monitor</span></span>  
  
     <span data-ttu-id="69d3b-121">시스템 모니터는 복제에 대한 카운터 수를 제공하여 성능을 모니터링하는 데 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="69d3b-121">System Monitor can be useful for monitoring performance, providing a number of counters for replication.</span></span> <span data-ttu-id="69d3b-122">자세한 내용은 [Monitoring Replication with System Monitor](monitor/monitoring-replication-with-system-monitor.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="69d3b-122">For more information, see [Monitoring Replication with System Monitor](monitor/monitoring-replication-with-system-monitor.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69d3b-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="69d3b-123">See Also</span></span>  
 <span data-ttu-id="69d3b-124">[복제 관리 FAQ](administration/frequently-asked-questions-for-replication-administrators.md) </span><span class="sxs-lookup"><span data-stu-id="69d3b-124">[Replication Administration FAQ](administration/frequently-asked-questions-for-replication-administrators.md) </span></span>  
 [<span data-ttu-id="69d3b-125">Best Practices for Replication Administration</span><span class="sxs-lookup"><span data-stu-id="69d3b-125">Best Practices for Replication Administration</span></span>](administration/best-practices-for-replication-administration.md)   

  
  
