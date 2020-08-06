---
title: 캐싱, 새로 고침 및 복제 모니터 성능 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- monitoring performance [SQL Server replication], Replication Monitor
- cache [SQL Server], replication
- Replication Monitor, caching
- refreshing data
- Replication Monitor, refreshing
ms.assetid: a2d8b666-ed41-4f86-b2b8-c8e118416ab7
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b04a91e971e65d19c66cc36f142d8c4764b1b05a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648935"
---
# <a name="caching-refresh-and-replication-monitor-performance"></a><span data-ttu-id="1beba-102">캐싱, 새로 고침 및 복제 모니터 성능</span><span class="sxs-lookup"><span data-stu-id="1beba-102">Caching, Refresh, and Replication Monitor Performance</span></span>
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)]<span data-ttu-id="1beba-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]복제 모니터는 프로덕션 시스템에서 많은 수의 컴퓨터를 효율적으로 모니터링 하도록 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="1beba-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Replication Monitor is designed to efficiently monitor a large number of computers in a production system.</span></span> <span data-ttu-id="1beba-104">계산을 수행하고 데이터를 수집하기 위해 복제 모니터가 사용하는 쿼리는 정기적으로 캐시되며 새로 고쳐집니다.</span><span class="sxs-lookup"><span data-stu-id="1beba-104">The queries that Replication Monitor uses to perform calculations and gather data are cached and refreshed on a periodic basis.</span></span> <span data-ttu-id="1beba-105">캐싱을 사용하면 복제 모니터에서 여러 페이지를 볼 때 필요한 쿼리 및 계산의 수를 줄일 수 있고 여러 사용자에 대해 모니터링을 확장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1beba-105">Caching reduces the number of queries and calculations required as you view different pages in Replication Monitor and allows monitoring to scale well for multiple users.</span></span>  
  
 <span data-ttu-id="1beba-106">캐시 새로 고침은 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 에이전트 작업, 즉 **배포에 대한 복제 모니터링 리프레셔**로 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="1beba-106">Cache refresh is handled by a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent job, the **Replication monitoring refresher for distribution**.</span></span> <span data-ttu-id="1beba-107">이 작업은 계속 실행되지만 캐시 새로 고침 일정은 이전 새로 고침 후 일정 시간 동안 대기한 다음 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="1beba-107">The job runs continuously, but the cache refresh schedule is based on waiting a certain amount time after the previous refresh:</span></span>  
  
-   <span data-ttu-id="1beba-108">마지막으로 캐시를 만든 이후에 에이전트 기록을 변경한 경우 대기 시간은 최소 4초 또는 이전 캐시를 만드는 데 소요된 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="1beba-108">If there were agent history changes since the cache was last created, the wait time is the minimum of: 4 seconds; or the amount of time taken to create the previous cache.</span></span>  
  
-   <span data-ttu-id="1beba-109">마지막으로 캐시를 만든 이후에 에이전트 기록을 변경하지 않은 경우(다른 변경 내용은 있을 수 있음) 대기 시간은 최대 30초 또는 이전 캐시를 만드는 데 소요된 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="1beba-109">If there were no agent history changes since the cache was last created (there could have been other changes), the wait time is the maximum of: 30 seconds; or the amount of time taken to create the previous cache.</span></span>  
  
## <a name="refreshing-the-replication-monitor-user-interface"></a><span data-ttu-id="1beba-110">복제 모니터 사용자 인터페이스 새로 고침</span><span class="sxs-lookup"><span data-stu-id="1beba-110">Refreshing the Replication Monitor User Interface</span></span>  
 <span data-ttu-id="1beba-111">다음과 같은 방법으로 복제 모니터 사용자 인터페이스를 새로 고칠 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1beba-111">The Replication Monitor user interface can be refreshed in the following ways:</span></span>  
  
-   <span data-ttu-id="1beba-112">기본적으로 주 복제 모니터 창(모든 탭 포함)은 자동으로 5초마다 새로 고쳐집니다.</span><span class="sxs-lookup"><span data-stu-id="1beba-112">The main Replication Monitor window (including all tabs), automatically refreshes by default every five seconds.</span></span> <span data-ttu-id="1beba-113">자동 새로 고침으로 인해 캐시가 새로 고쳐지지는 않으며 사용자 인터페이스는 캐시에서 가장 최신 버전의 데이터를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="1beba-113">Automatic refreshes do not force a refresh of the cache; the user interface displays the most recent version of the data from the cache.</span></span> <span data-ttu-id="1beba-114">게시자 설정을 편집하여 게시자와 연결된 모든 창에 사용되는 새로 고침 빈도를 사용자 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1beba-114">You can customize the refresh rate used for all windows associated with a Publisher by editing the Publisher settings.</span></span> <span data-ttu-id="1beba-115">또한 게시자에 대한 자동 새로 고침을 해제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1beba-115">You can also disable automatic refreshes for a Publisher.</span></span>  
  
-   <span data-ttu-id="1beba-116">복제 모니터에 표시되는 세부 정보 창은 동기화를 수행 중인 병합 구독에 관련된 창을 제외하고 기본적으로 자동 새로 고침되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1beba-116">The detail windows that are launched from Replication Monitor are not automatically refreshed by default, with the exception of windows related to merge subscriptions that are synchronizing.</span></span> <span data-ttu-id="1beba-117">세부 정보 창이 자동으로 새로 고쳐지도록 지정한 경우 이 창은 주 복제 모니터 창과 같은 일정으로 새로 고쳐집니다.</span><span class="sxs-lookup"><span data-stu-id="1beba-117">If you specify that detail windows should automatically refresh, they refresh on the same schedule as the main Replication Monitor window.</span></span>  
  
-   <span data-ttu-id="1beba-118">F5 키를 누르거나 복제 모니터 트리의 노드를 마우스 오른쪽 단추로 클릭하고 **새로 고침**을 클릭하여 모든 창을 수동으로 새로 고칠 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1beba-118">All windows can be manually refreshed by pressing F5 or by right-clicking a node in the Replication Monitor tree and clicking **Refresh**.</span></span> <span data-ttu-id="1beba-119">수동으로 새로 고침을 수행하면 캐시도 새로 고쳐집니다.</span><span class="sxs-lookup"><span data-stu-id="1beba-119">Manual refreshes force a refresh of the cache.</span></span>  
  
 <span data-ttu-id="1beba-120">자세한 내용은 [복제 모니터에서 데이터 새로 고침](refresh-data-in-replication-monitor.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1beba-120">For more information, see [Refresh Data in Replication Monitor](refresh-data-in-replication-monitor.md).</span></span>  
  
## <a name="performance-considerations"></a><span data-ttu-id="1beba-121">성능 고려 사항</span><span class="sxs-lookup"><span data-stu-id="1beba-121">Performance Considerations</span></span>  
 <span data-ttu-id="1beba-122">복제 모니터는 효율적으로 실행되도록 설계되었지만 다음 사항에 유의하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="1beba-122">Although Replication Monitor is designed to run efficiently, be aware of the following:</span></span>  
  
-   <span data-ttu-id="1beba-123">게시 또는 구독의 수가 많은 경우 사용자 인터페이스에 대한 자동 새로 고침 횟수를 줄이십시오.</span><span class="sxs-lookup"><span data-stu-id="1beba-123">If you have a large number of publications or subscriptions, consider setting a less frequent automatic refresh schedule for the user interface.</span></span>  
  
-   <span data-ttu-id="1beba-124">여러 복제 모니터 인스턴스를 동시에 실행하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="1beba-124">Avoid concurrently running multiple instances of Replication Monitor.</span></span>  
  
-   <span data-ttu-id="1beba-125">많은 배포자를 등록한 다음 복제 모니터가 자동으로 이러한 모든 배포자에 연결하도록 설정하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="1beba-125">Avoid registering a large number of Distributors and setting Replication Monitor to automatically connect to all of them.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1beba-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1beba-126">See Also</span></span>  
 <span data-ttu-id="1beba-127">[복제 유지 관리 작업 실행&#40;SQL Server Management Studio&#41;](../../../ssms/sql-server-management-studio-ssms.md) </span><span class="sxs-lookup"><span data-stu-id="1beba-127">[Run Replication Maintenance Jobs &#40;SQL Server Management Studio&#41;](../../../ssms/sql-server-management-studio-ssms.md) </span></span>  
 [<span data-ttu-id="1beba-128">복제 모니터링</span><span class="sxs-lookup"><span data-stu-id="1beba-128">Monitoring Replication</span></span>](../monitoring-replication.md)  
  
  
