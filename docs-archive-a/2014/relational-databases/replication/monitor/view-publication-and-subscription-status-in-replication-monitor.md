---
title: 복제 모니터에서 게시 및 구독 상태 보기 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Log Reader Agent, monitoring
- Merge Agent, monitoring
- Queue Reader Agent, monitoring
- publications [SQL Server replication], viewing information
- Snapshot Agent, monitoring
- Distribution Agent, monitoring
- monitoring performance [SQL Server replication], publication status
- monitoring performance [SQL Server replication], subscription status
- subscriptions [SQL Server replication], viewing status
- Replication Monitor, publication and subscription status
ms.assetid: 16590771-9867-463e-a973-36a5c145ac16
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 4f1f714e18a961546a4e5a7f6709beca8d525800
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741812"
---
# <a name="view-publication-and-subscription-status-in-replication-monitor"></a><span data-ttu-id="c7120-102">복제 모니터에서 게시 및 구독 상태 보기</span><span class="sxs-lookup"><span data-stu-id="c7120-102">View Publication and Subscription Status in Replication Monitor</span></span>
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)]<span data-ttu-id="c7120-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]복제 모니터는 게시 및 구독에 대 한 상태 정보를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7120-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Replication Monitor displays status information for publications and subscriptions:</span></span>  
  
-   <span data-ttu-id="c7120-104">게시 상태는 해당 구독의 가장 높은 우선 순위 상태에 의해 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7120-104">The status of a publication is determined by the highest priority status of its subscriptions.</span></span> <span data-ttu-id="c7120-105">예를 들어 게시에 대한 특정 구독에 오류가 있고 다른 구독에 성능 문제가 있으면 해당 게시에 대해 오류 상태가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7120-105">For example, if one subscription to a publication has an error and another has a performance issue, a status of error is displayed for the publication.</span></span>  
  
-   <span data-ttu-id="c7120-106">구독 상태는 해당 구독을 처리하는 에이전트의 상태에 의해 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7120-106">The status of a subscription is determined by the status of the agents that service the subscription.</span></span> <span data-ttu-id="c7120-107">병합 복제의 경우 병합 에이전트가 상태를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="c7120-107">For merge replication, this is the Merge Agent.</span></span> <span data-ttu-id="c7120-108">트랜잭션 복제의 경우 로그 판독기 에이전트나 배포 에이전트가 상태를 결정하며 우선 순위가 높은 상태가 표시됩니다. 지연 업데이트 구독을 사용하는 경우 큐 판독기 에이전트에 의해 상태가 결정될 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7120-108">For transactional replication, this is either the Log Reader Agent or the Distribution Agent (the higher priority status is displayed; the status can also be determined by the Queue Reader Agent if queued updating subscriptions are used).</span></span> <span data-ttu-id="c7120-109">스냅샷 복제의 경우 스냅샷 에이전트나 배포 에이전트가 상태를 결정하며 우선 순위가 높은 상태가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7120-109">For snapshot replication, this is the Snapshot Agent or the Distribution Agent (the higher priority status is displayed).</span></span>  
  
 <span data-ttu-id="c7120-110">다음 섹션의 표에서는 게시와 구독에 사용 가능한 상태 값을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="c7120-110">Tables in the following sections list the possible status values for publications and subscriptions.</span></span> <span data-ttu-id="c7120-111">다음 3가지 상태 값은 임계값에 도달하거나 초과한 경우에만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7120-111">Three of the status values are displayed only if a threshold is met or exceeded:</span></span>  
  
-   <span data-ttu-id="c7120-112">구독 만료</span><span class="sxs-lookup"><span data-stu-id="c7120-112">Expiring subscription</span></span>  
  
     <span data-ttu-id="c7120-113">이 상태 값은 모든 유형의 복제에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7120-113">This status value applies to all types of replication.</span></span> <span data-ttu-id="c7120-114">자세한 내용은 [Set Thresholds and Warnings in Replication Monitor](set-thresholds-and-warnings-in-replication-monitor.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c7120-114">For more information, see [Set Thresholds and Warnings in Replication Monitor](set-thresholds-and-warnings-in-replication-monitor.md).</span></span>  
  
-   <span data-ttu-id="c7120-115">성능 심각</span><span class="sxs-lookup"><span data-stu-id="c7120-115">Performance critical</span></span>  
  
     <span data-ttu-id="c7120-116">이 상태 값은 트랜잭션 복제와 병합 복제에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7120-116">This status value applies to transactional replication and merge replication.</span></span> <span data-ttu-id="c7120-117">자세한 내용은 [복제 모니터로 성능 모니터링](monitor-performance-with-replication-monitor.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c7120-117">For more information, see [Monitor Performance with Replication Monitor](monitor-performance-with-replication-monitor.md).</span></span>  
  
-   <span data-ttu-id="c7120-118">장기 실행 트랜잭션 병합</span><span class="sxs-lookup"><span data-stu-id="c7120-118">Long-running merge</span></span>  
  
     <span data-ttu-id="c7120-119">이 상태 값은 병합 복제에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7120-119">This status value applies to merge replication.</span></span> <span data-ttu-id="c7120-120">자세한 내용은 [복제 모니터로 성능 모니터링](monitor-performance-with-replication-monitor.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c7120-120">For more information, see [Monitor Performance with Replication Monitor](monitor-performance-with-replication-monitor.md).</span></span>  
  
 <span data-ttu-id="c7120-121">게시 및 구독 상태 외에도 병합 복제는 아티클 수준의 통계를 제공합니다. 이 통계를 사용하여 병합 단계가 완료되기까지 남은 시간, 지정된 아티클 처리에 소요된 시간, 구독자가 사용 중인 연결 유형 및 기타 중요한 정보를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7120-121">In addition to publication and subscription status, merge replication provides article-level statistics, which give detailed information about: how much longer a merge phase will take to complete; how much time was spent processing a given article; the type of connection a Subscriber is using; and other important information.</span></span> <span data-ttu-id="c7120-122">이 통계는 복제 모니터의 병합 에이전트 창에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7120-122">The statistics are displayed in the Merge Agent window in Replication Monitor.</span></span> <span data-ttu-id="c7120-123">스냅샷 및 트랜잭션 복제는 배포 에이전트 처리에 대한 자세한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="c7120-123">Snapshot and transactional replication provide detailed information on Distribution Agent processing.</span></span>  
  
 <span data-ttu-id="c7120-124">**게시 및 구독 상태를 보려면**</span><span class="sxs-lookup"><span data-stu-id="c7120-124">**To view publication and subscription status**</span></span>  
  
-   <span data-ttu-id="c7120-125">복제 모니터: [복제 모니터를 사용 하 여 정보를 보고 태스크를 수행](view-information-and-perform-tasks-replication-monitor.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="c7120-125">Replication Monitor: [View Information and Perform Tasks using Replication Monitor](view-information-and-perform-tasks-replication-monitor.md).</span></span>
  
  
## <a name="publication-status-values"></a><span data-ttu-id="c7120-126">게시 상태 값</span><span class="sxs-lookup"><span data-stu-id="c7120-126">Publication Status Values</span></span>  
 <span data-ttu-id="c7120-127">다음 표에서는 게시 상태 값과 해당 아이콘을 우선 순위순으로 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c7120-127">The following table shows publication status values and their corresponding icons in priority order.</span></span>  
  
|<span data-ttu-id="c7120-128">상태</span><span class="sxs-lookup"><span data-stu-id="c7120-128">Status</span></span>|<span data-ttu-id="c7120-129">아이콘</span><span class="sxs-lookup"><span data-stu-id="c7120-129">Icon</span></span>|  
|------------|----------|  
|<span data-ttu-id="c7120-130">오류</span><span class="sxs-lookup"><span data-stu-id="c7120-130">Error</span></span>|<span data-ttu-id="c7120-131">![UI 아이콘: 오류](../media/repl-icon-error.gif "UI 아이콘: 오류")</span><span class="sxs-lookup"><span data-stu-id="c7120-131">![UI icon: error](../media/repl-icon-error.gif "UI icon: error")</span></span>|  
|<span data-ttu-id="c7120-132">성능 심각</span><span class="sxs-lookup"><span data-stu-id="c7120-132">Performance critical</span></span>|<span data-ttu-id="c7120-133">![UI 아이콘: 경고](../media/repl-icon-warn.gif "UI 아이콘: 경고")</span><span class="sxs-lookup"><span data-stu-id="c7120-133">![UI icon: warning](../media/repl-icon-warn.gif "UI icon: warning")</span></span>|  
|<span data-ttu-id="c7120-134">실패한 명령 다시 시도 중</span><span class="sxs-lookup"><span data-stu-id="c7120-134">Retrying failed command</span></span>|<span data-ttu-id="c7120-135">![UI 아이콘: 복제 에이전트 다시 시도](../media/repl-icon-retry.gif "UI 아이콘: 복제 에이전트 다시 시도")</span><span class="sxs-lookup"><span data-stu-id="c7120-135">![UI icon: replication agent retry](../media/repl-icon-retry.gif "UI icon: replication agent retry")</span></span>|  
|<span data-ttu-id="c7120-136">정상</span><span class="sxs-lookup"><span data-stu-id="c7120-136">OK</span></span>|<span data-ttu-id="c7120-137">none</span><span class="sxs-lookup"><span data-stu-id="c7120-137">none</span></span>|  
  
## <a name="subscription-status-values"></a><span data-ttu-id="c7120-138">구독 상태 값</span><span class="sxs-lookup"><span data-stu-id="c7120-138">Subscription Status Values</span></span>  
 <span data-ttu-id="c7120-139">다음 표에서는 구독 상태 값과 해당 아이콘을 우선 순위순으로 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c7120-139">The following tables show subscription status values and their corresponding icons in priority order.</span></span> <span data-ttu-id="c7120-140">한 구독이 동시에 두 가지 상태에 있을 수 있습니다(예: **곧 만료됨/만료됨** 및 **실패한 명령 다시 시도 중**). 이 경우 우선 순위가 가장 높은 상태가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7120-140">It is possible for a subscription to be in two states at the same time, such as **Expiring soon/Expired** and **Retrying failed command**; the highest priority status is displayed.</span></span>  
  
 <span data-ttu-id="c7120-141">**성능 심각**, **곧 만료됨/만료됨**및 **초기화되지 않음** 의 상태 값은 경고입니다.</span><span class="sxs-lookup"><span data-stu-id="c7120-141">The status values **Performance critical**, **Expiring soon/Expired**, and **Uninitialized** are warnings.</span></span> <span data-ttu-id="c7120-142">경고를 표시할 때 복제 모니터는 에이전트가 실행되고 있는지 여부도 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="c7120-142">When a warning is displayed, Replication Monitor also displays whether an agent is running.</span></span> <span data-ttu-id="c7120-143">예를 들어 상태가 **실행 중, 성능 심각**과 같이 표시될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7120-143">For example, the status could be **Running, Performance critical**.</span></span>  
  
### <a name="transactional-subscriptions"></a><span data-ttu-id="c7120-144">트랜잭션 구독</span><span class="sxs-lookup"><span data-stu-id="c7120-144">Transactional subscriptions</span></span>  
  
|<span data-ttu-id="c7120-145">상태</span><span class="sxs-lookup"><span data-stu-id="c7120-145">Status</span></span>|<span data-ttu-id="c7120-146">아이콘</span><span class="sxs-lookup"><span data-stu-id="c7120-146">Icon</span></span>|  
|------------|----------|  
|<span data-ttu-id="c7120-147">오류</span><span class="sxs-lookup"><span data-stu-id="c7120-147">Error</span></span>|<span data-ttu-id="c7120-148">![UI 아이콘: 오류](../media/repl-icon-error.gif "UI 아이콘: 오류")</span><span class="sxs-lookup"><span data-stu-id="c7120-148">![UI icon: error](../media/repl-icon-error.gif "UI icon: error")</span></span>|  
|<span data-ttu-id="c7120-149">성능 심각</span><span class="sxs-lookup"><span data-stu-id="c7120-149">Performance critical</span></span>|<span data-ttu-id="c7120-150">![UI 아이콘: 경고](../media/repl-icon-warn.gif "UI 아이콘: 경고")</span><span class="sxs-lookup"><span data-stu-id="c7120-150">![UI icon: warning](../media/repl-icon-warn.gif "UI icon: warning")</span></span>|  
|<span data-ttu-id="c7120-151">곧 만료됨/만료됨</span><span class="sxs-lookup"><span data-stu-id="c7120-151">Expiring soon/Expired</span></span>|<span data-ttu-id="c7120-152">![UI 아이콘: 경고](../media/repl-icon-warn.gif "UI 아이콘: 경고")</span><span class="sxs-lookup"><span data-stu-id="c7120-152">![UI icon: warning](../media/repl-icon-warn.gif "UI icon: warning")</span></span>|  
|<span data-ttu-id="c7120-153">초기화되지 않은 구독</span><span class="sxs-lookup"><span data-stu-id="c7120-153">Uninitialized subscription</span></span>|<span data-ttu-id="c7120-154">![UI 아이콘: 경고](../media/repl-icon-warn.gif "UI 아이콘: 경고")</span><span class="sxs-lookup"><span data-stu-id="c7120-154">![UI icon: warning](../media/repl-icon-warn.gif "UI icon: warning")</span></span>|  
|<span data-ttu-id="c7120-155">실패한 명령 다시 시도 중</span><span class="sxs-lookup"><span data-stu-id="c7120-155">Retrying failed command</span></span>|<span data-ttu-id="c7120-156">![UI 아이콘: 복제 에이전트 다시 시도](../media/repl-icon-retry.gif "UI 아이콘: 복제 에이전트 다시 시도")</span><span class="sxs-lookup"><span data-stu-id="c7120-156">![UI icon: replication agent retry](../media/repl-icon-retry.gif "UI icon: replication agent retry")</span></span>|  
|<span data-ttu-id="c7120-157">실행 중이 아님</span><span class="sxs-lookup"><span data-stu-id="c7120-157">Not running</span></span>|<span data-ttu-id="c7120-158">![UI 아이콘: 복제 에이전트 중지됨](../media/repl-icon-stopped.gif "UI 아이콘: 복제 에이전트 중지됨")</span><span class="sxs-lookup"><span data-stu-id="c7120-158">![UI icon: replication agent stopped](../media/repl-icon-stopped.gif "UI icon: replication agent stopped")</span></span>|  
|<span data-ttu-id="c7120-159">실행 중</span><span class="sxs-lookup"><span data-stu-id="c7120-159">Running</span></span>|<span data-ttu-id="c7120-160">![UI 아이콘: 복제 에이전트 실행 중](../media/repl-icon-running.gif "UI 아이콘: 복제 에이전트 실행 중")</span><span class="sxs-lookup"><span data-stu-id="c7120-160">![UI icon: replication agent running](../media/repl-icon-running.gif "UI icon: replication agent running")</span></span>|  
  
### <a name="merge-subscriptions"></a><span data-ttu-id="c7120-161">병합 구독</span><span class="sxs-lookup"><span data-stu-id="c7120-161">Merge subscriptions</span></span>  
  
|<span data-ttu-id="c7120-162">상태</span><span class="sxs-lookup"><span data-stu-id="c7120-162">Status</span></span>|<span data-ttu-id="c7120-163">아이콘</span><span class="sxs-lookup"><span data-stu-id="c7120-163">Icon</span></span>|  
|------------|----------|  
|<span data-ttu-id="c7120-164">오류</span><span class="sxs-lookup"><span data-stu-id="c7120-164">Error</span></span>|<span data-ttu-id="c7120-165">![UI 아이콘: 오류](../media/repl-icon-error.gif "UI 아이콘: 오류")</span><span class="sxs-lookup"><span data-stu-id="c7120-165">![UI icon: error](../media/repl-icon-error.gif "UI icon: error")</span></span>|  
|<span data-ttu-id="c7120-166">성능 심각</span><span class="sxs-lookup"><span data-stu-id="c7120-166">Performance critical</span></span>|<span data-ttu-id="c7120-167">![UI 아이콘: 경고](../media/repl-icon-warn.gif "UI 아이콘: 경고")</span><span class="sxs-lookup"><span data-stu-id="c7120-167">![UI icon: warning](../media/repl-icon-warn.gif "UI icon: warning")</span></span>|  
|<span data-ttu-id="c7120-168">장기 실행 트랜잭션 병합</span><span class="sxs-lookup"><span data-stu-id="c7120-168">Long-running merge</span></span>|<span data-ttu-id="c7120-169">![UI 아이콘: 경고](../media/repl-icon-warn.gif "UI 아이콘: 경고")</span><span class="sxs-lookup"><span data-stu-id="c7120-169">![UI icon: warning](../media/repl-icon-warn.gif "UI icon: warning")</span></span>|  
|<span data-ttu-id="c7120-170">곧 만료됨/만료됨</span><span class="sxs-lookup"><span data-stu-id="c7120-170">Expiring soon/Expired</span></span>|<span data-ttu-id="c7120-171">![UI 아이콘: 경고](../media/repl-icon-warn.gif "UI 아이콘: 경고")</span><span class="sxs-lookup"><span data-stu-id="c7120-171">![UI icon: warning](../media/repl-icon-warn.gif "UI icon: warning")</span></span>|  
|<span data-ttu-id="c7120-172">초기화되지 않은 구독</span><span class="sxs-lookup"><span data-stu-id="c7120-172">Uninitialized subscription</span></span>|<span data-ttu-id="c7120-173">![UI 아이콘: 경고](../media/repl-icon-warn.gif "UI 아이콘: 경고")</span><span class="sxs-lookup"><span data-stu-id="c7120-173">![UI icon: warning](../media/repl-icon-warn.gif "UI icon: warning")</span></span>|  
|<span data-ttu-id="c7120-174">실패한 명령 다시 시도 중</span><span class="sxs-lookup"><span data-stu-id="c7120-174">Retrying failed command</span></span>|<span data-ttu-id="c7120-175">![UI 아이콘: 복제 에이전트 다시 시도](../media/repl-icon-retry.gif "UI 아이콘: 복제 에이전트 다시 시도")</span><span class="sxs-lookup"><span data-stu-id="c7120-175">![UI icon: replication agent retry](../media/repl-icon-retry.gif "UI icon: replication agent retry")</span></span>|  
|<span data-ttu-id="c7120-176">동기화 중</span><span class="sxs-lookup"><span data-stu-id="c7120-176">Synchronizing</span></span>|<span data-ttu-id="c7120-177">![UI 아이콘: 복제 에이전트 실행 중](../media/repl-icon-running.gif "UI 아이콘: 복제 에이전트 실행 중")</span><span class="sxs-lookup"><span data-stu-id="c7120-177">![UI icon: replication agent running](../media/repl-icon-running.gif "UI icon: replication agent running")</span></span>|  
|<span data-ttu-id="c7120-178">비동기화 중</span><span class="sxs-lookup"><span data-stu-id="c7120-178">Not Synchronizing</span></span>|<span data-ttu-id="c7120-179">![UI 아이콘: 복제 에이전트 중지됨](../media/repl-icon-stopped.gif "UI 아이콘: 복제 에이전트 중지됨")</span><span class="sxs-lookup"><span data-stu-id="c7120-179">![UI icon: replication agent stopped](../media/repl-icon-stopped.gif "UI icon: replication agent stopped")</span></span>|  
  
### <a name="snapshot-subscriptions"></a><span data-ttu-id="c7120-180">스냅샷 구독</span><span class="sxs-lookup"><span data-stu-id="c7120-180">Snapshot subscriptions</span></span>  
  
|<span data-ttu-id="c7120-181">상태</span><span class="sxs-lookup"><span data-stu-id="c7120-181">Status</span></span>|<span data-ttu-id="c7120-182">아이콘</span><span class="sxs-lookup"><span data-stu-id="c7120-182">Icon</span></span>|  
|------------|----------|  
|<span data-ttu-id="c7120-183">오류</span><span class="sxs-lookup"><span data-stu-id="c7120-183">Error</span></span>|<span data-ttu-id="c7120-184">![UI 아이콘: 오류](../media/repl-icon-error.gif "UI 아이콘: 오류")</span><span class="sxs-lookup"><span data-stu-id="c7120-184">![UI icon: error](../media/repl-icon-error.gif "UI icon: error")</span></span>|  
|<span data-ttu-id="c7120-185">곧 만료됨/만료됨</span><span class="sxs-lookup"><span data-stu-id="c7120-185">Expiring soon/Expired</span></span>|<span data-ttu-id="c7120-186">![UI 아이콘: 경고](../media/repl-icon-warn.gif "UI 아이콘: 경고")</span><span class="sxs-lookup"><span data-stu-id="c7120-186">![UI icon: warning](../media/repl-icon-warn.gif "UI icon: warning")</span></span>|  
|<span data-ttu-id="c7120-187">초기화되지 않은 구독</span><span class="sxs-lookup"><span data-stu-id="c7120-187">Uninitialized subscription</span></span>|<span data-ttu-id="c7120-188">![UI 아이콘: 경고](../media/repl-icon-warn.gif "UI 아이콘: 경고")</span><span class="sxs-lookup"><span data-stu-id="c7120-188">![UI icon: warning](../media/repl-icon-warn.gif "UI icon: warning")</span></span>|  
|<span data-ttu-id="c7120-189">실패한 명령 다시 시도 중</span><span class="sxs-lookup"><span data-stu-id="c7120-189">Retrying failed command</span></span>|<span data-ttu-id="c7120-190">![UI 아이콘: 복제 에이전트 다시 시도](../media/repl-icon-retry.gif "UI 아이콘: 복제 에이전트 다시 시도")</span><span class="sxs-lookup"><span data-stu-id="c7120-190">![UI icon: replication agent retry](../media/repl-icon-retry.gif "UI icon: replication agent retry")</span></span>|  
|<span data-ttu-id="c7120-191">동기화 중</span><span class="sxs-lookup"><span data-stu-id="c7120-191">Synchronizing</span></span>|<span data-ttu-id="c7120-192">![UI 아이콘: 복제 에이전트 실행 중](../media/repl-icon-running.gif "UI 아이콘: 복제 에이전트 실행 중")</span><span class="sxs-lookup"><span data-stu-id="c7120-192">![UI icon: replication agent running](../media/repl-icon-running.gif "UI icon: replication agent running")</span></span>|  
|<span data-ttu-id="c7120-193">비동기화 중</span><span class="sxs-lookup"><span data-stu-id="c7120-193">Not Synchronizing</span></span>|<span data-ttu-id="c7120-194">![UI 아이콘: 복제 에이전트 중지됨](../media/repl-icon-stopped.gif "UI 아이콘: 복제 에이전트 중지됨")</span><span class="sxs-lookup"><span data-stu-id="c7120-194">![UI icon: replication agent stopped](../media/repl-icon-stopped.gif "UI icon: replication agent stopped")</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c7120-195">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c7120-195">See Also</span></span>  
 [<span data-ttu-id="c7120-196">복제 모니터링</span><span class="sxs-lookup"><span data-stu-id="c7120-196">Monitoring Replication</span></span>](../monitoring-replication.md)  
  
  
