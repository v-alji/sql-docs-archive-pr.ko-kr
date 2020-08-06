---
title: 복제 모니터 인터페이스 개요 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Replication Monitor
- Replication Monitor, about Replication Monitor
ms.assetid: 078f0e34-7153-45c4-8725-778b5bef88da
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 4d9b7edbd76153f23168ec9bcf4a286d5f7cbe9b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648929"
---
# <a name="overview-of-the-replication-monitor-interface"></a><span data-ttu-id="07198-102">복제 모니터 인터페이스 개요</span><span class="sxs-lookup"><span data-stu-id="07198-102">Overview of the Replication Monitor Interface</span></span>
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] <span data-ttu-id="07198-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 복제 모니터는 모든 복제 작업을 게시자 관점 또는 배포자 관점으로 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="07198-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Replication Monitor presents a Publisher-focused view or Distributor-focused view of all replication activity in a two pane format.</span></span> <span data-ttu-id="07198-104">왼쪽 창에서 모니터에 게시자를 추가하면 오른쪽 창에 게시자, 해당 게시, 게시에 대한 구독 및 다양한 복제 에이전트 정보가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="07198-104">You add a Publisher to the monitor in the left pane, and in the right pane the monitor displays information on the Publisher, its publications, the subscriptions to those publications, and the various replication agents.</span></span> <span data-ttu-id="07198-105">복제 토폴로지에 대한 정보를 제공하는 것 외에도 복제 모니터를 사용하여 에이전트 시작 및 중지, 데이터 유효성 검사 등 다양한 태스크를 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07198-105">In addition to presenting information for the replication topology, Replication Monitor allows you to perform a number of tasks, such as starting and stopping agents, and validating data.</span></span>  
  
## <a name="viewing-information-for-the-entire-topology"></a><span data-ttu-id="07198-106">전체 토폴로지 정보 보기</span><span class="sxs-lookup"><span data-stu-id="07198-106">Viewing Information for the Entire Topology</span></span>  
 <span data-ttu-id="07198-107">복제 모니터 화면의 왼쪽 창</span><span class="sxs-lookup"><span data-stu-id="07198-107">The left pane of Replication Monitor displays</span></span>  
  
-   <span data-ttu-id="07198-108">게시자 그룹, 게시자 및 게시</span><span class="sxs-lookup"><span data-stu-id="07198-108">Publisher groups, Publishers, and publications.</span></span>  
  
-   <span data-ttu-id="07198-109">배포자, 게시자 및 게시</span><span class="sxs-lookup"><span data-stu-id="07198-109">Distributors, Publishers, and publications.</span></span>  
  
 <span data-ttu-id="07198-110">복제 모니터에서 정보를 보려면 먼저 게시자를 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="07198-110">To view any information in Replication Monitor, you must first add a Publisher.</span></span> <span data-ttu-id="07198-111">자세한 내용은 [복제 모니터에서 게시자 추가 및 제거](add-and-remove-publishers-from-replication-monitor.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="07198-111">For more information, see [Add and Remove Publishers from Replication Monitor](add-and-remove-publishers-from-replication-monitor.md).</span></span>  
  
 <span data-ttu-id="07198-112">왼쪽 창에서 다음 질문의 대답을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07198-112">The left pane helps answer the following questions:</span></span>  
  
-   <span data-ttu-id="07198-113">복제 시스템이 정상적으로 작동 중인가?</span><span class="sxs-lookup"><span data-stu-id="07198-113">Is my replication system healthy?</span></span>  
  
     <span data-ttu-id="07198-114">왼쪽 창의 노드에 오류 아이콘이 없으면 복제 시스템이 비교적 양호한 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="07198-114">The replication system is relatively healthy if there are no error icons on nodes in the left pane.</span></span> <span data-ttu-id="07198-115">시스템 상태를 더 자세히 보려면 주의가 필요한 구독 정보가 표시되는 **구독 조사 목록** 탭도 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="07198-115">To get a more complete view of system health, you should also check the **Subscription Watch List** tab, which displays information on subscriptions that might require attention.</span></span>  
  
-   <span data-ttu-id="07198-116">에이전트가 실행되지 않는 이유는 무엇인가?</span><span class="sxs-lookup"><span data-stu-id="07198-116">Why is an agent not running?</span></span>  
  
     <span data-ttu-id="07198-117">에이전트가 실행되도록 예약하지 않았거나 오류가 발생하여 특정 시간에 에이전트가 실행되고 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="07198-117">An agent is not running at a particular time either because it is not scheduled to run or because an error has occurred.</span></span> <span data-ttu-id="07198-118">오류가 발생한 경우에는 왼쪽 창의 해당 노드에 오류 아이콘이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="07198-118">If an error has occurred, an error icon is displayed on the appropriate nodes in the left pane.</span></span> <span data-ttu-id="07198-119">예를 들어 게시에 대한 스냅샷 에이전트가 오류로 인해 중지되면 게시자 그룹, 게시자 및 게시 노드에 오류 아이콘이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="07198-119">For example, if the Snapshot Agent for a publication stopped because of an error, an error icon is displayed on the Publisher group, Publisher, and publication nodes.</span></span> <span data-ttu-id="07198-120">스냅샷 에이전트의 요약 정보가 해당 게시에 대한 **에이전트** 탭에 표시됩니다. 자세한 오류 정보를 보려면 이 탭에서 스냅샷 에이전트를 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="07198-120">Summary information for the Snapshot Agent is displayed on the **Agents** tab for the publication; double click the Snapshot Agent on this tab for detailed error information.</span></span>  
  
## <a name="viewing-information-and-performing-tasks-related-to-distributors"></a><span data-ttu-id="07198-121">배포자 관련 정보 보기 및 태스크 수행</span><span class="sxs-lookup"><span data-stu-id="07198-121">Viewing Information and Performing Tasks Related to Distributors</span></span>  
 <span data-ttu-id="07198-122">복제 모니터는 다음 3개의 탭에 배포자 정보를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="07198-122">Replication Monitor displays information about Distributors on three tabs:</span></span>  
  
-   <span data-ttu-id="07198-123">**게시** 탭</span><span class="sxs-lookup"><span data-stu-id="07198-123">**Publications** tab</span></span>  
  
     <span data-ttu-id="07198-124">이 탭은 배포자의 모든 게시에 대한 요약 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="07198-124">This tab provides summary information for all publications of a Distributor.</span></span>  
  
-   <span data-ttu-id="07198-125">**구독 조사 목록** 탭</span><span class="sxs-lookup"><span data-stu-id="07198-125">**Subscription Watch List** tab</span></span>  
  
     <span data-ttu-id="07198-126">이 탭은 선택한 배포자에 대한 모든 구독 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="07198-126">This tab provides information about subscriptions for the selected Distributor.</span></span> <span data-ttu-id="07198-127">구독 목록을 필터링하여 오류, 경고 및 성능이 저조한 구독을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07198-127">You can filter the list of subscriptions to see errors, warnings, and any poorly performing subscriptions.</span></span> <span data-ttu-id="07198-128">또한 이 탭에서는 구독 속성에 액세스하거나, 구독과 연결된 에이전트에 대한 자세한 정보에 액세스하거나, 구독을 다시 초기화하거나, 구독의 유효성을 검사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07198-128">The tab also lets you to perform the following tasks: access subscription properties, access detailed information about the agent or agents associated with a subscription, reinitialize subscriptions, and validate subscriptions.</span></span>  
  
     <span data-ttu-id="07198-129">**구독 조사 목록** 탭에서 다음 질문의 대답을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07198-129">The **Subscription Watch List** tab helps answer the following questions:</span></span>  
  
    -   <span data-ttu-id="07198-130">어떤 구독이 느린가?</span><span class="sxs-lookup"><span data-stu-id="07198-130">Which subscriptions are slow?</span></span>  
  
         <span data-ttu-id="07198-131">표에 상대적인 성능순으로 구독을 표시하도록 이 탭에서 옵션을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="07198-131">Set options on this tab so that the grid displays subscriptions in order by their relative performance.</span></span>  
  
    -   <span data-ttu-id="07198-132">복제 시스템이 정상적으로 작동 중인가?</span><span class="sxs-lookup"><span data-stu-id="07198-132">Is my replication system healthy?</span></span>  
  
         <span data-ttu-id="07198-133">이 탭의 표에는 주의가 필요한 구독에 대한 오류 및 경고 아이콘이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="07198-133">The grid on this tab displays error and warning icons for any subscriptions that require your attention.</span></span>  
  
     <span data-ttu-id="07198-134">이 탭은 [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] 이하 버전을 실행하는 배포자에서 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="07198-134">This tab is not available for Distributors that are running versions of [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] or earlier.</span></span>  
  
-   <span data-ttu-id="07198-135">**에이전트** 탭</span><span class="sxs-lookup"><span data-stu-id="07198-135">**Agents** tab</span></span>  
  
     <span data-ttu-id="07198-136">이 탭에는 모든 복제 유형에 사용되는 에이전트 및 작업에 대한 세부 정보가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="07198-136">This tab displays detailed information about the agents and jobs that are used by all types of replication.</span></span> <span data-ttu-id="07198-137">이 탭에서는 각 에이전트 및 작업을 시작하고 중지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07198-137">The tab also let you start and stop each agent and job.</span></span>  
  
 <span data-ttu-id="07198-138">복제 모니터는 배포자 노드에 대한 상황에 맞는 메뉴도 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="07198-138">Replication Monitor also provides a context menu for the Distributor node.</span></span> <span data-ttu-id="07198-139">왼쪽 창에서 배포자를 마우스 오른쪽 단추로 클릭하여 다음 태스크를 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07198-139">Right-click a Distributor in the left pane to perform the following tasks:</span></span>  
  
-   <span data-ttu-id="07198-140">복제 모니터에 게시자 추가</span><span class="sxs-lookup"><span data-stu-id="07198-140">Add a Publisher to Replication Monitor.</span></span>  
  
-   <span data-ttu-id="07198-141">배포자에 대한 복제 모니터 설정 편집</span><span class="sxs-lookup"><span data-stu-id="07198-141">Edit Replication Monitor settings for the Distributor.</span></span>  
  
-   <span data-ttu-id="07198-142">게시자 그룹 뷰로 전환</span><span class="sxs-lookup"><span data-stu-id="07198-142">Switch to the Publisher Group view.</span></span>  
  
## <a name="viewing-information-and-performing-tasks-related-to-publishers"></a><span data-ttu-id="07198-143">게시자 관련 정보 보기 및 태스크 수행</span><span class="sxs-lookup"><span data-stu-id="07198-143">Viewing Information and Performing Tasks Related to Publishers</span></span>  
 <span data-ttu-id="07198-144">복제 모니터는 다음 3개의 탭에 게시자 정보를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="07198-144">Replication Monitor displays information about Publishers on three tabs:</span></span>  
  
-   <span data-ttu-id="07198-145">**게시** 탭</span><span class="sxs-lookup"><span data-stu-id="07198-145">**Publications** tab</span></span>  
  
     <span data-ttu-id="07198-146">이 탭은 게시자에 있는 모든 게시의 요약 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="07198-146">This tab provides summary information for all publications at a Publisher.</span></span>  
  
-   <span data-ttu-id="07198-147">**구독 조사 목록** 탭</span><span class="sxs-lookup"><span data-stu-id="07198-147">**Subscription Watch List** tab</span></span>  
  
     <span data-ttu-id="07198-148">이 탭에는 선택한 게시자에서 사용 가능한 모든 게시의 구독 정보가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="07198-148">This tab is intended to display information on subscriptions from all publications available at the selected Publisher.</span></span> <span data-ttu-id="07198-149">구독 목록을 필터링하여 오류, 경고 및 성능이 저조한 구독을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07198-149">You can filter the list of subscriptions to see errors, warnings, and any poorly performing subscriptions.</span></span> <span data-ttu-id="07198-150">또한 이 탭에서는 구독 속성에 액세스하거나, 구독과 연결된 에이전트에 대한 자세한 정보에 액세스하거나, 구독을 다시 초기화하거나, 구독의 유효성을 검사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07198-150">The tab also allows you to: access subscription properties; access detailed information about the agent or agents associated with a subscription; reinitialize subscriptions; and validate subscriptions.</span></span>  
  
     <span data-ttu-id="07198-151">**구독 조사 목록** 탭에서 다음 질문의 대답을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07198-151">The **Subscription Watch List** tab helps answer the following questions:</span></span>  
  
    -   <span data-ttu-id="07198-152">어떤 구독이 느린가?</span><span class="sxs-lookup"><span data-stu-id="07198-152">Which subscriptions are slow?</span></span>  
  
         <span data-ttu-id="07198-153">표에 상대적인 성능순으로 구독을 표시하도록 이 탭에서 옵션을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="07198-153">Set options on this tab so that the grid displays subscriptions in order by their relative performance.</span></span>  
  
    -   <span data-ttu-id="07198-154">복제 시스템이 정상적으로 작동 중인가?</span><span class="sxs-lookup"><span data-stu-id="07198-154">Is my replication system healthy?</span></span>  
  
         <span data-ttu-id="07198-155">이 탭의 표에는 주의가 필요한 구독에 대한 오류 및 경고 아이콘이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="07198-155">The grid on this tab displays error and warning icons for any subscriptions that require your attention.</span></span>  
  
     <span data-ttu-id="07198-156">[!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]이전 버전을 실행하는 배포자의 경우 이 탭이 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="07198-156">This tab is not displayed for Distributors running versions prior to [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)].</span></span>  
  
-   <span data-ttu-id="07198-157">**에이전트** 탭</span><span class="sxs-lookup"><span data-stu-id="07198-157">**Agents** tab</span></span>  
  
     <span data-ttu-id="07198-158">이 탭에는 모든 복제 유형에 사용되는 에이전트 및 작업에 대한 세부 정보가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="07198-158">This tab displays detailed information about the agents and jobs used by all types of replication.</span></span> <span data-ttu-id="07198-159">이 탭에서는 각 에이전트 및 작업을 시작하고 중지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07198-159">The tab also allows you to start and stop each agent and job.</span></span>  
  
 <span data-ttu-id="07198-160">자세한 내용은 [복제 모니터를 사용하여 정보 보기 및 태스크 수행](view-information-and-perform-tasks-replication-monitor.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="07198-160">For more information, see [View Information and Perform Tasks using Replication Monitor](view-information-and-perform-tasks-replication-monitor.md).</span></span>  
  
 <span data-ttu-id="07198-161">복제 모니터는 게시자 노드에 대한 상황에 맞는 메뉴도 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="07198-161">Replication Monitor also provides a context menu for the Publisher node.</span></span> <span data-ttu-id="07198-162">왼쪽 창에서 게시자를 마우스 오른쪽 단추로 클릭하여 다음 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07198-162">Right-click a Publisher in the left pane to:</span></span>  
  
-   <span data-ttu-id="07198-163">게시자에 대한 복제 모니터 설정 편집</span><span class="sxs-lookup"><span data-stu-id="07198-163">Edit Replication Monitor settings for the Publisher</span></span>  
  
-   <span data-ttu-id="07198-164">복제 모니터에서 게시자 제거</span><span class="sxs-lookup"><span data-stu-id="07198-164">Remove the Publisher from Replication Monitor</span></span>  
  
-   <span data-ttu-id="07198-165">에이전트 프로필 보기 및 편집</span><span class="sxs-lookup"><span data-stu-id="07198-165">View and edit agent profiles</span></span>  
  
-   <span data-ttu-id="07198-166">게시자 정보를 저장하는 배포자에 연결 또는 연결 끊기</span><span class="sxs-lookup"><span data-stu-id="07198-166">Connect to or disconnect from the Distributor that stores information about the Publisher</span></span>  
  
## <a name="viewing-information-and-performing-tasks-related-to-publications"></a><span data-ttu-id="07198-167">게시 관련 정보 보기 및 태스크 수행</span><span class="sxs-lookup"><span data-stu-id="07198-167">Viewing Information and Performing Tasks Related to Publications</span></span>  
 <span data-ttu-id="07198-168">복제 모니터는 다음 3개의 탭에 게시 정보를 표시하며 많은 세부 정보 창을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="07198-168">Replication Monitor displays information about publications on three tabs and a number of detail windows:</span></span>  
  
-   <span data-ttu-id="07198-169">**모든 구독** 탭</span><span class="sxs-lookup"><span data-stu-id="07198-169">**All Subscriptions** tab</span></span>  
  
     <span data-ttu-id="07198-170">이 탭에는 선택한 게시에 대한 모든 구독 정보가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="07198-170">This tab displays information about all subscriptions to the selected publication.</span></span> <span data-ttu-id="07198-171">기본적으로 이 탭은 우선 순위순으로 정렬됩니다. 오류, 경고가 표시된 후 성능의 오름차순으로 성능이 저조한 구독이 맨 위에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="07198-171">By default, this tab is sorted in priority order: errors, then warnings, then in increasing order of performance, with any poorly performing subscriptions at the top.</span></span>  
  
     <span data-ttu-id="07198-172">**모든 구독** 탭에서 다음 질문의 대답을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07198-172">The **All Subscriptions** tab helps answer the following questions:</span></span>  
  
    -   <span data-ttu-id="07198-173">어떤 구독이 느린가?</span><span class="sxs-lookup"><span data-stu-id="07198-173">Which subscriptions are slow?</span></span>  
  
         <span data-ttu-id="07198-174">표에 상대적인 성능순으로 구독을 표시하도록 이 탭에서 옵션을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="07198-174">Set options on this tab so that the grid displays subscriptions in order by their relative performance.</span></span>  
  
    -   <span data-ttu-id="07198-175">복제 시스템이 정상적으로 작동 중인가?</span><span class="sxs-lookup"><span data-stu-id="07198-175">Is my replication system healthy?</span></span>  
  
         <span data-ttu-id="07198-176">이 탭의 표에는 주의가 필요한 구독에 대한 오류 및 경고 아이콘이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="07198-176">The grid on this tab displays error and warning icons for any subscriptions that require your attention.</span></span>  
  
-   <span data-ttu-id="07198-177">**에이전트** 탭</span><span class="sxs-lookup"><span data-stu-id="07198-177">**Agents** tab</span></span>  
  
     <span data-ttu-id="07198-178">이 탭에는 복제에 사용되는 다음 에이전트에 대한 작업 정보가</span><span class="sxs-lookup"><span data-stu-id="07198-178">This tab displays information about the agents that are used by replication.</span></span> <span data-ttu-id="07198-179">이 탭에는 다음 에이전트에 대한 정보가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="07198-179">This tab displays information about the following agents:</span></span>  
  
    -   <span data-ttu-id="07198-180">스냅샷 에이전트 - 모든 게시에서 사용</span><span class="sxs-lookup"><span data-stu-id="07198-180">The Snapshot Agent, which is used by all publications.</span></span>  
  
    -   <span data-ttu-id="07198-181">로그 판독기 에이전트 - 모든 트랜잭션 게시에서 사용</span><span class="sxs-lookup"><span data-stu-id="07198-181">The Log Reader Agent, which is used by all transactional publications.</span></span>  
  
    -   <span data-ttu-id="07198-182">큐 판독기 에이전트 - 지연 업데이트 구독이 활성화된 트랜잭션 게시에서 사용</span><span class="sxs-lookup"><span data-stu-id="07198-182">The Queue Reader Agent, which is used by transactional publications enabled for queued updating subscriptions.</span></span>  
  
     <span data-ttu-id="07198-183">또한 이 탭에서는 각 에이전트에 대한 자세한 정보에 액세스하고 각 에이전트를 시작 및 중지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07198-183">The tab also allows for you to perform the following tasks: access detailed information about each agent, and start and stop each agent.</span></span> <span data-ttu-id="07198-184">구독과 연결된 에이전트(배포 에이전트 및 병합 에이전트)에 대한 자세한 내용은 이 항목의 "구독 관련 정보 보기 및 태스크 수행" 섹션을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="07198-184">For information about agents that are associated with subscriptions (the Distribution Agent and Merge Agent), see the section "Viewing Information and Performing Tasks Related to Subscriptions" in this topic.</span></span>  
  
-   <span data-ttu-id="07198-185">**경고** 탭</span><span class="sxs-lookup"><span data-stu-id="07198-185">**Warnings** tab</span></span>  
  
     <span data-ttu-id="07198-186">이 탭에서는 에이전트에 대한 경고를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07198-186">This tab enables you to specify warnings and alerts for agents.</span></span> <span data-ttu-id="07198-187">자세한 내용은 [Set Thresholds and Warnings in Replication Monitor](set-thresholds-and-warnings-in-replication-monitor.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="07198-187">For more information, see [Set Thresholds and Warnings in Replication Monitor](set-thresholds-and-warnings-in-replication-monitor.md).</span></span>  
  
-   <span data-ttu-id="07198-188">**추적 프로그램 토큰** 탭(트랜잭션 복제에만 해당)</span><span class="sxs-lookup"><span data-stu-id="07198-188">**Tracer Tokens** tab (transactional replication only)</span></span>  
  
     <span data-ttu-id="07198-189">이 탭에서는 대기 시간(게시자에서 커밋될 트랜잭션과 구독자에서 상응하는 커밋될 트랜잭션 사이에 경과된 시간)을 측정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07198-189">This tab allows you to measure latency, the amount of time that elapses between a transaction being committed at the Publisher and the corresponding transaction being committed at the Subscriber.</span></span>  
  
     <span data-ttu-id="07198-190">이 탭에서 다음 질문의 대답을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07198-190">This tab helps answers the following question:</span></span>  
  
    -   <span data-ttu-id="07198-191">트랜잭션 복제 시 지금 커밋된 트랜잭션이 구독자에 도달하기까지 얼마나 걸리는가?</span><span class="sxs-lookup"><span data-stu-id="07198-191">How long will it take a transaction committed now to reach a Subscriber in transactional replication?</span></span>  
  
         <span data-ttu-id="07198-192">트랜잭션이 시스템을 통과하는 총 시간을 보고 이전 시간과 비교합니다.</span><span class="sxs-lookup"><span data-stu-id="07198-192">View the total time for a transaction to travel through the system and also compare it to previous times.</span></span>  
  
     <span data-ttu-id="07198-193">[!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] 이하 버전을 실행하는 배포자의 경우 이 탭이 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="07198-193">This tab is not displayed for Distributors running [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] or earlier.</span></span> <span data-ttu-id="07198-194">추적 프로그램 토큰에 대한 자세한 내용은 [트랜잭션 복제에 대한 대기 시간 측정 및 연결 유효성 검사](measure-latency-and-validate-connections-for-transactional-replication.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="07198-194">For more information on tracer tokens, see [Measure Latency and Validate Connections for Transactional Replication](measure-latency-and-validate-connections-for-transactional-replication.md).</span></span>  
  
-   <span data-ttu-id="07198-195">게시와 연결된 에이전트에 대한 세부 정보 창.</span><span class="sxs-lookup"><span data-stu-id="07198-195">Detail windows for the agents associated with a publication.</span></span> <span data-ttu-id="07198-196">다음 에이전트는 게시와 연결되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07198-196">The following agents are associated with publications:</span></span>  
  
    -   <span data-ttu-id="07198-197">스냅샷 에이전트 - 모든 게시에서 사용</span><span class="sxs-lookup"><span data-stu-id="07198-197">The Snapshot Agent, which is used by all publications.</span></span>  
  
    -   <span data-ttu-id="07198-198">로그 판독기 에이전트 - 모든 트랜잭션 게시에서 사용</span><span class="sxs-lookup"><span data-stu-id="07198-198">The Log Reader Agent, which is used by all transactional publications.</span></span>  
  
    -   <span data-ttu-id="07198-199">큐 판독기 에이전트 - 지연 업데이트 구독이 활성화된 트랜잭션 게시에서 사용</span><span class="sxs-lookup"><span data-stu-id="07198-199">The Queue Reader Agent, which is used by transactional publications enabled for queued updating subscriptions.</span></span>  
  
     <span data-ttu-id="07198-200">세부 정보 창의 정보에 액세스하려면 복제 모니터에서 에이전트를 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="07198-200">Double-click an agent in Replication Monitor to access information in a detail window.</span></span> <span data-ttu-id="07198-201">위에 나열된 에이전트 외에도 구독과 연결된 에이전트가 있습니다. 배포 에이전트는 스냅샷에 대한 구독 및 트랜잭션 게시에 사용되고 병합 에이전트는 병합 게시에 대한 구독에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="07198-201">In addition to the agents listed above, there are agents associated with subscriptions: the Distribution Agent for subscriptions to snapshot and transactional publications; and the Merge Agent for subscriptions to merge publications.</span></span> <span data-ttu-id="07198-202">자세한 내용은 이 항목의 "구독 관련 정보 보기 및 태스크 수행" 섹션을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="07198-202">For more information, see the section "Viewing Information and Performing Tasks Related to Subscriptions" in this topic.</span></span>  
  
     <span data-ttu-id="07198-203">에이전트 세부 정보 창은 시작 시간, 종료 시간, 지속 기간 및 세션에서 수행된 동작을 포함하여 에이전트 세션에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="07198-203">The agent detail windows provide information about agent sessions, including start time, end time, duration, and the actions performed in a session.</span></span> <span data-ttu-id="07198-204">이 창에서 다음 질문의 대답을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07198-204">They help to answer the following question:</span></span>  
  
    -   <span data-ttu-id="07198-205">에이전트가 실행되지 않는 이유는 무엇인가?</span><span class="sxs-lookup"><span data-stu-id="07198-205">Why is an agent not running?</span></span>  
  
         <span data-ttu-id="07198-206">제공되는 오류 메시지를 통해 에이전트가 실행되지 않는 이유를 자세히 확인할 수 있습니다. 이 오류 메시지는 게시와 연결된 에이전트의 문제 해결을 위한 출발점입니다.</span><span class="sxs-lookup"><span data-stu-id="07198-206">The error messages available provide detailed information on why an agent is not running and provide a starting point for troubleshooting issues with the agents associated with a publication.</span></span>  
  
 <span data-ttu-id="07198-207">자세한 내용은 [복제 모니터를 사용하여 정보 보기 및 태스크 수행](view-information-and-perform-tasks-replication-monitor.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="07198-207">For more information, see [View Information and Perform Tasks using Replication Monitor](view-information-and-perform-tasks-replication-monitor.md).</span></span>  
  
 <span data-ttu-id="07198-208">복제 모니터는 게시 노드에 대한 상황에 맞는 메뉴도 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="07198-208">Replication Monitor also provides a context menu for the publications node.</span></span> <span data-ttu-id="07198-209">왼쪽 창에서 게시를 마우스 오른쪽 단추로 클릭하여 다음 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07198-209">Right-click a publication in the left pane to:</span></span>  
  
-   <span data-ttu-id="07198-210">게시에 대한 모든 구독 다시 초기화</span><span class="sxs-lookup"><span data-stu-id="07198-210">Reinitialize all subscriptions to a publication</span></span>  
  
-   <span data-ttu-id="07198-211">게시에 대한 모든 구독의 유효성 검사</span><span class="sxs-lookup"><span data-stu-id="07198-211">Validate all subscriptions to a publication</span></span>  
  
-   <span data-ttu-id="07198-212">게시에 대한 스냅샷 생성</span><span class="sxs-lookup"><span data-stu-id="07198-212">Generate a snapshot for a publication</span></span>  
  
-   <span data-ttu-id="07198-213">게시 속성 보기 및 편집</span><span class="sxs-lookup"><span data-stu-id="07198-213">View and edit publication properties</span></span>  
  
## <a name="viewing-information-and-performing-tasks-related-to-subscriptions"></a><span data-ttu-id="07198-214">구독 관련 정보 보기 및 태스크 수행</span><span class="sxs-lookup"><span data-stu-id="07198-214">Viewing Information and Performing Tasks Related to Subscriptions</span></span>  
 <span data-ttu-id="07198-215">복제 모니터는 많은 탭에 구독 정보를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="07198-215">Replication Monitor displays information about subscriptions on a number of different tabs.</span></span> <span data-ttu-id="07198-216">세부 정보 창에 있는 이러한 탭에 액세스하려면 복제 모니터에서 구독을 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="07198-216">Double-click a subscription in Replication Monitor to access these tabs in a detail window.</span></span> <span data-ttu-id="07198-217">이 모든 탭에서 "에이전트가 실행되지 않는 이유는 무엇인가?"란 질문의 대답을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07198-217">All of the tabs are useful in answering the question "Why is an agent not running?"</span></span> <span data-ttu-id="07198-218">제공되는 오류 메시지를 통해 에이전트가 실행되지 않는 이유를 자세히 확인할 수 있습니다. 이 오류 메시지는 구독과 연결된 에이전트의 문제 해결을 위한 출발점입니다.</span><span class="sxs-lookup"><span data-stu-id="07198-218">The error messages available provide detailed information on why an agent is not running and provide a starting point for troubleshooting issues with the agents associated with a subscription.</span></span>  
  
-   <span data-ttu-id="07198-219">**모든 구독** 및 **구독 조사 목록**</span><span class="sxs-lookup"><span data-stu-id="07198-219">**All Subscriptions tab** and **Subscription Watch List tab.**</span></span>  
  
     <span data-ttu-id="07198-220">두 탭에 대해서는 이 항목의 앞 부분에서 설명했습니다.</span><span class="sxs-lookup"><span data-stu-id="07198-220">These tabs are described earlier in this topic.</span></span>  
  
-   <span data-ttu-id="07198-221">**게시자에서 배포자로의 연결 기록** 탭(트랜잭션 복제에만 해당)</span><span class="sxs-lookup"><span data-stu-id="07198-221">**Publisher to Distributor History** tab (transactional replication only)</span></span>  
  
     <span data-ttu-id="07198-222">이 탭에는 게시에 대한 로그 판독기 에이전트 정보가 표시됩니다. 이 탭은 로그 판독기 에이전트 세부 정보 창과 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="07198-222">This tab displays information on the Log Reader Agent for a publication (the tab is identical to the Log Reader Agent details window).</span></span>  
  
-   <span data-ttu-id="07198-223">**배포자에서 구독자로의 연결 기록** 탭(스냅샷 복제 및 트랜잭션 복제)</span><span class="sxs-lookup"><span data-stu-id="07198-223">**Distributor to Subscriber History** tab (snapshot replication and transactional replication)</span></span>  
  
     <span data-ttu-id="07198-224">이 탭에는 구독에 대한 배포 에이전트 정보가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="07198-224">This tab displays information on the Distribution Agent for a subscription.</span></span>  
  
-   <span data-ttu-id="07198-225">**배포되지 않은 명령** 탭(트랜잭션 복제에만 해당)</span><span class="sxs-lookup"><span data-stu-id="07198-225">**Undistributed Commands** tab (transactional replication only)</span></span>  
  
     <span data-ttu-id="07198-226">이 탭에는 선택한 구독자에게 배달되지 않은 배포 데이터베이스의 명령 수와 해당 명령의 예상 배달 시간에 대한 정보가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="07198-226">This tab displays information about the number of commands in the distribution database that have not been delivered to the selected Subscriber, and the estimated time to deliver those commands.</span></span> <span data-ttu-id="07198-227">이 탭에서 "내 구독이 얼마나 지연되었는가?"란 질문의 대답을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07198-227">The tab helps answer the question, "How far behind is my subscription?"</span></span> <span data-ttu-id="07198-228">SQL Server 2005 이전 버전을 실행하는 배포자의 경우 이 탭이 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="07198-228">This tab is not displayed for Distributors running versions prior to SQL Server 2005.</span></span>  
  
-   <span data-ttu-id="07198-229">**동기화 기록** 탭(병합 복제에만 해당)</span><span class="sxs-lookup"><span data-stu-id="07198-229">**Synchronization History** tab (merge replication only)</span></span>  
  
     <span data-ttu-id="07198-230">이 탭에는 구독에 대한 병합 에이전트 정보가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="07198-230">This tab displays information on the Merge Agent for a subscription.</span></span> <span data-ttu-id="07198-231">이 탭에서 다음 질문의 대답을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07198-231">This tab helps answer the following question:</span></span>  
  
    -   <span data-ttu-id="07198-232">내 병합 구독이 왜 느린가?</span><span class="sxs-lookup"><span data-stu-id="07198-232">Why is my merge subscription slow?</span></span>  
  
         <span data-ttu-id="07198-233">이 탭에서는 각 처리 단계(변경 내용 업로드, 변경 내용 다운로드 등)에 소요된 시간을 포함하여 동기화 중에 처리된 각 아티클에 대한 자세한 통계를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="07198-233">This tab provides detailed statistics for each article processed during synchronization, including the amount of time spent in each processing phase (uploading changes, downloading changes, and so on).</span></span> <span data-ttu-id="07198-234">이 통계는 속도 저하의 원인이 되고 병합 구독의 성능 문제를 해결하기에 가장 적합한 특정 테이블을 정확히 찾아내는 데 도움이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07198-234">It can help pinpoint specific tables that are causing slowdowns and is the best place to troubleshoot performance issues with merge subscriptions.</span></span>  
  
 <span data-ttu-id="07198-235">자세한 내용은 [복제 모니터를 사용하여 정보 보기 및 태스크 수행](view-information-and-perform-tasks-replication-monitor.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="07198-235">For more information, see [View Information and Perform Tasks using Replication Monitor](view-information-and-perform-tasks-replication-monitor.md).</span></span>
  
## <a name="viewing-information-and-performing-tasks-related-to-agent-profiles"></a><span data-ttu-id="07198-236">에이전트 프로필 관련 정보 보기 및 태스크 수행</span><span class="sxs-lookup"><span data-stu-id="07198-236">Viewing Information and Performing Tasks Related to Agent Profiles</span></span>  
 <span data-ttu-id="07198-237">복제 모니터에는 에이전트 프로필을 관리하기 위한 많은 대화 상자가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07198-237">Replication Monitor includes a number of dialog boxes for managing agent profiles.</span></span> <span data-ttu-id="07198-238">에이전트 프로필은 에이전트 동작을 결정하는 에이전트에 대한 매개 변수 집합입니다.</span><span class="sxs-lookup"><span data-stu-id="07198-238">Agent profiles are sets of parameters for an agent that determine agent behavior.</span></span> <span data-ttu-id="07198-239">자세한 내용은 [Replication Agent Profiles](../agents/replication-agent-profiles.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="07198-239">For more information, see [Replication Agent Profiles](../agents/replication-agent-profiles.md).</span></span> <span data-ttu-id="07198-240">다음과 같은 대화 상자가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07198-240">The dialog boxes are:</span></span>  
  
-   <span data-ttu-id="07198-241">**에이전트 프로필**</span><span class="sxs-lookup"><span data-stu-id="07198-241">**Agent Profiles**</span></span>  
  
     <span data-ttu-id="07198-242">이 대화 상자에서는 프로필 속성 변경, 프로필 만들기 및 삭제, 기본 프로필 지정, 특정 유형(예: 스냅샷 에이전트)의 모든 에이전트가 지정된 프로필을 사용하도록 지정 등의 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07198-242">This dialog box allows you to: change the properties of profiles; create and delete profiles; specify a default profile; and specify that all agents of a specific type (such as Snapshot Agents) should use a given profile.</span></span>  
  
-   <span data-ttu-id="07198-243">**\<AgentProfileName>속성**</span><span class="sxs-lookup"><span data-stu-id="07198-243">**\<AgentProfileName> Properties**</span></span>  
  
     <span data-ttu-id="07198-244">이 대화 상자에서는 프로필의 매개 변수 설정을 보고 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07198-244">This dialog box allows you to view and edit the parameter settings in a profile.</span></span>  
  
-   <span data-ttu-id="07198-245">**새 에이전트 프로필**</span><span class="sxs-lookup"><span data-stu-id="07198-245">**New Agent Profile**</span></span>  
  
     <span data-ttu-id="07198-246">이 대화 상자에서는 선택적으로 기존 프로필의 값이 포함된 새 프로필을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07198-246">This dialog box allows you to create a new profile, optionally including the values from an existing profile.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07198-247">참고 항목</span><span class="sxs-lookup"><span data-stu-id="07198-247">See Also</span></span>  
 [<span data-ttu-id="07198-248">복제 모니터링</span><span class="sxs-lookup"><span data-stu-id="07198-248">Monitoring Replication</span></span>](../monitoring-replication.md)  
  
  
