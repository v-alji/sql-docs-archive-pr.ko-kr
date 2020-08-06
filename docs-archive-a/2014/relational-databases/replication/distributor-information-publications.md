---
title: "' 배포자 정보 ' 대화 상자 SQL Server 복제 | Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.Distributor.Publications.f1
- sql12.rep.monitor.Distributor.commonjobs..f1
- sql12.rep.monitor.Distributor.SubscriptionSummary.merge.f1
- sql12.rep.monitor.Distributor.SubscriptionSummary.snapshot.f1
- sql12.rep.monitor.Distributor.SubscriptionSummary.tran.f1
ms.assetid: 1f499277-7f12-42ba-8cf4-52b683434944
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8ca0717a63c9660c225ec238e1e4d2423f7d01ba
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646918"
---
# <a name="distributor-information-dialog-box"></a><span data-ttu-id="070db-102">배포자 정보 대화 상자</span><span class="sxs-lookup"><span data-stu-id="070db-102">Distributor Information Dialog Box</span></span> 
<span data-ttu-id="070db-103">이 항목에서는 **배포자** 대화 상자에 대 한 정보를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="070db-103">This topic provides information on the **Distributor** dialog box</span></span> 

## <a name="publications"></a><span data-ttu-id="070db-104">게시</span><span class="sxs-lookup"><span data-stu-id="070db-104">Publications</span></span>

  <span data-ttu-id="070db-105">**게시** 탭은 왼쪽 창에서 선택한 배포자에서의 모든 게시에 대한 요약 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="070db-105">The **Publications** tab provides summary information for all publications at the Distributor that is selected in the left pane.</span></span>  
  
### <a name="options"></a><span data-ttu-id="070db-106">옵션</span><span class="sxs-lookup"><span data-stu-id="070db-106">Options</span></span>  
 <span data-ttu-id="070db-107">배포자에서 지원하는 게시에 대해 표시되는 정보에는 게시자의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스가 있는 열이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="070db-107">The information that is displayed about the publications supported by the Distributor includes a column that contains the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance of the Publisher.</span></span> <span data-ttu-id="070db-108">그 밖에 표시되는 게시 정보는 복제 모니터의 게시자 뷰에서 게시를 볼 때 제공되는 게시 정보와 같습니다.</span><span class="sxs-lookup"><span data-stu-id="070db-108">Otherwise, the publication information is the same as the publication information that is provided when you view publications in the Publisher view of Replication Monitor.</span></span> <span data-ttu-id="070db-109">**게시** 탭의 열에 대한 자세한 내용은 [Publisher Information, Publications](publisher-information-publications.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="070db-109">For more information about the columns in the **Publications** tab, see [Publisher Information, Publications](publisher-information-publications.md).</span></span>  

## <a name="subscription-watch-list"></a><span data-ttu-id="070db-110">구독 조사 목록</span><span class="sxs-lookup"><span data-stu-id="070db-110">Subscription watch list</span></span>

### <a name="transactional-replication"></a><span data-ttu-id="070db-111">트랜잭션 복제</span><span class="sxs-lookup"><span data-stu-id="070db-111">Transactional replication</span></span> 
  <span data-ttu-id="070db-112">트랜잭션 구독 정보는 게시자 이름을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="070db-112">Information for transactional subscriptions includes the name of the Publisher.</span></span> <span data-ttu-id="070db-113">그 밖에 이 대화 상자에 제공되는 기능 및 정보는 게시자 뷰와 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="070db-113">Otherwise, the functionality and the information that is provided in this dialog box is the same as in the Publisher view.</span></span> <span data-ttu-id="070db-114">이 대화 상자를 사용하는 방법은 [게시자 정보, 구독 조사 목록&#40;트랜잭션 게시, SQL Server 2005 이상&#41;](publisher-information-subscription-watch-list-transactional.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="070db-114">For more information about how to use this dialog box, see [Publisher Information, Subscription Watch List &#40;Transactional Publication, SQL Server 2005 and Later&#41;](publisher-information-subscription-watch-list-transactional.md).</span></span>  

### <a name="merge-replication"></a><span data-ttu-id="070db-115">병합 복제</span><span class="sxs-lookup"><span data-stu-id="070db-115">Merge replication</span></span>
  <span data-ttu-id="070db-116">병합 게시 구독 정보는 게시자 이름을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="070db-116">Information for merge publication subscriptions includes the name of the Publisher.</span></span> <span data-ttu-id="070db-117">그 밖에 이 대화 상자에 제공되는 기능 및 정보는 게시자 뷰와 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="070db-117">Otherwise, the functionality and the information that is provided in this dialog box is the same as in the Publisher view.</span></span> <span data-ttu-id="070db-118">이 대화 상자를 사용하는 방법은 [게시자 정보, 구독 조사 목록&#40;병합 게시, SQL Server 2005 이상&#41;](publisher-information-subscription-watch-list-merge-publication.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="070db-118">For more information about how to use this dialog box, see [Publisher Information, Subscription Watch List &#40;Merge Publication, SQL Server 2005 and Later&#41;](publisher-information-subscription-watch-list-merge-publication.md).</span></span> 

### <a name="snapshot-replication"></a><span data-ttu-id="070db-119">스냅샷 복제</span><span class="sxs-lookup"><span data-stu-id="070db-119">Snapshot replication</span></span>
  <span data-ttu-id="070db-120">스냅샷 게시 구독 정보는 게시자 이름을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="070db-120">Information for snapshot publication subscriptions includes the name of the Publisher.</span></span> <span data-ttu-id="070db-121">그 밖에 이 대화 상자에 제공되는 기능 및 정보는 게시자 뷰와 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="070db-121">Otherwise, the functionality and the information that is provided in this dialog box is the same as in the Publisher view.</span></span> <span data-ttu-id="070db-122">이 대화 상자를 사용하는 방법은 [게시자 정보, 구독 조사 목록&#40;스냅샷 게시, SQL Server 2005 이상&#41;](publisher-information-subscription-watch-list-snapshot.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="070db-122">For more information about how to use this dialog box, see [Publisher Information, Subscription Watch List &#40;Snapshot Publication, SQL Server 2005 and Later&#41;](publisher-information-subscription-watch-list-snapshot.md).</span></span>  

## <a name="agents"></a><span data-ttu-id="070db-123">에이전트</span><span class="sxs-lookup"><span data-stu-id="070db-123">Agents</span></span>
  <span data-ttu-id="070db-124">**에이전트** 탭에는 게시자 및 구독자와 연결된 에이전트 및 유지 관리 작업에 대한 정보가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="070db-124">The **Agents** tab displays information about the agents and maintenance jobs that are associated with the Publisher and Subscriber.</span></span>  
  
 <span data-ttu-id="070db-125">배포자 뷰의 배포자에 대한 **에이전트** 탭에서 사용할 수 있는 에이전트에는 게시자에 대한 **에이전트** 탭에서 사용할 수 있는 모든 에이전트가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="070db-125">The agents that are available in the **Agents** tab for a Distributor in Distributor view include all the agents that are available in the **Agents** tab for a Publisher.</span></span> <span data-ttu-id="070db-126">그러나 배포자 뷰의 배포자에 대한 **에이전트** 탭에는 배포자 에이전트와 병합 에이전트도 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="070db-126">However, the **Agents** tab for a Distributor in Distributor view also includes a Distributor Agent and a Merge Agent.</span></span>  
  
 <span data-ttu-id="070db-127">스냅샷, 로그 판독기 및 큐 판독기 에이전트와 유지 관리 작업에 대한 자세한 내용은 [Publisher Information, Agents](publisher-information-agents.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="070db-127">For more information about the Snapshot, Log Reader, and Queue Reader agents, and maintenance jobs, see [Publisher Information, Agents](publisher-information-agents.md).</span></span> <span data-ttu-id="070db-128">배포자에 대한 **에이전트** 탭에 있는 에이전트 정보를 표시하면 스냅샷 및 로그 판독기 에이전트에 대한 게시자 정보가 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="070db-128">Notice that when you are viewing agent information on the **Agents** tab for a Distributor, Publisher information is present for the Snapshot and Log Reader agents.</span></span> <span data-ttu-id="070db-129">그러나 배포자 뷰의 배포자에 대한 **에이전트** 탭에서는 **배포자 에이전트** 및 **병합 에이전트**를 선택할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="070db-129">However, in the **Agents** tab for a Distributor in Distributor view, you can also select **Distributor Agent** and **Merge Agent**.</span></span>  
  
### <a name="options"></a><span data-ttu-id="070db-130">옵션</span><span class="sxs-lookup"><span data-stu-id="070db-130">Options</span></span>  
 <span data-ttu-id="070db-131">다음 섹션에서는 이 탭에서 배포자 에이전트 및 병합 에이전트에 대해 표시되는 데이터를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="070db-131">The following sections describe the data that is displayed on this tab for the Distributor Agent and Merge Agent.</span></span>  
  
### <a name="distributor-agent"></a><span data-ttu-id="070db-132">배포자 에이전트</span><span class="sxs-lookup"><span data-stu-id="070db-132">Distributor Agent</span></span>  
 <span data-ttu-id="070db-133">**상태**</span><span class="sxs-lookup"><span data-stu-id="070db-133">**Status**</span></span>  
 <span data-ttu-id="070db-134">에이전트의 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="070db-134">The status of the agent.</span></span> <span data-ttu-id="070db-135">다음 목록에서는 가능한 상태 값을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="070db-135">The following list shows the possible status values:</span></span>  
  
-   <span data-ttu-id="070db-136">오류</span><span class="sxs-lookup"><span data-stu-id="070db-136">Error</span></span>    
-   <span data-ttu-id="070db-137">다시 시도</span><span class="sxs-lookup"><span data-stu-id="070db-137">Retry</span></span>    
-   <span data-ttu-id="070db-138">실행 중</span><span class="sxs-lookup"><span data-stu-id="070db-138">Running</span></span>    
-   <span data-ttu-id="070db-139">실행 중이 아님</span><span class="sxs-lookup"><span data-stu-id="070db-139">Not Running</span></span>    
-   <span data-ttu-id="070db-140">시작한 적 없음</span><span class="sxs-lookup"><span data-stu-id="070db-140">Never started</span></span>  
  
 <span data-ttu-id="070db-141">**게시자**</span><span class="sxs-lookup"><span data-stu-id="070db-141">**Publisher**</span></span>  
 <span data-ttu-id="070db-142">게시자의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="070db-142">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance of the Publisher.</span></span>  
  
 <span data-ttu-id="070db-143">**게시**</span><span class="sxs-lookup"><span data-stu-id="070db-143">**Publication**</span></span>  
 <span data-ttu-id="070db-144">에이전트와 연결된 게시의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="070db-144">The name of the publication with which the agent is associated.</span></span>  
  
 <span data-ttu-id="070db-145">**구독**</span><span class="sxs-lookup"><span data-stu-id="070db-145">**Subscription**</span></span>  
 <span data-ttu-id="070db-146">[*SubscriberName*].[*Database*]와(과) 같은 형식의 구독 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="070db-146">The name of the subscription, in the form: [*SubscriberName*].[*Database*].</span></span>  
  
 <span data-ttu-id="070db-147">**형식**</span><span class="sxs-lookup"><span data-stu-id="070db-147">**Type**</span></span>  
 <span data-ttu-id="070db-148">복제 유형(밀어넣기, 끌어오기 또는 익명)입니다.</span><span class="sxs-lookup"><span data-stu-id="070db-148">Type of replication: push, pull, or Anonymous.</span></span>  
  
 <span data-ttu-id="070db-149">**마지막 시작 시간**</span><span class="sxs-lookup"><span data-stu-id="070db-149">**Last Start Time**</span></span>  
 <span data-ttu-id="070db-150">마지막으로 에이전트가 시작된 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="070db-150">The last time at which the agent started.</span></span>  
  
 <span data-ttu-id="070db-151">**기간**</span><span class="sxs-lookup"><span data-stu-id="070db-151">**Duration**</span></span>  
 <span data-ttu-id="070db-152">에이전트가 실행된 기간입니다.</span><span class="sxs-lookup"><span data-stu-id="070db-152">The length of time that the agent has run.</span></span> <span data-ttu-id="070db-153">에이전트가 현재 실행되고 있는 경우 이 시간은 경과된 시간을 나타내고 에이전트가 이전에 실행된 경우에는 총 시간을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="070db-153">The time represents elapsed time if the agent is currently running, and total time if the agent has run previously.</span></span>  
  
 <span data-ttu-id="070db-154">**마지막 동작**</span><span class="sxs-lookup"><span data-stu-id="070db-154">**Last Action**</span></span>  
 <span data-ttu-id="070db-155">가장 최근의 에이전트 실행에서 수행된 마지막 동작입니다.</span><span class="sxs-lookup"><span data-stu-id="070db-155">The last action that was performed during the most recent run of the agent.</span></span>  
  
 <span data-ttu-id="070db-156">**배달 속도**</span><span class="sxs-lookup"><span data-stu-id="070db-156">**Delivery Rate**</span></span>  
 <span data-ttu-id="070db-157">가장 최근에 에이전트를 실행할 때 배포 데이터베이스에서 초기화 명령이 커밋된 속도(초당 명령 수)입니다.</span><span class="sxs-lookup"><span data-stu-id="070db-157">The rate, in commands per second, at which initialization commands are committed in the distribution database during the most recent run of the agent.</span></span>  
  
 <span data-ttu-id="070db-158">**대기 시간**</span><span class="sxs-lookup"><span data-stu-id="070db-158">**Latency**</span></span>  
 <span data-ttu-id="070db-159">게시 데이터베이스에서 가장 최근의 변경 내용이 커밋된 후 배포 데이터베이스에서 해당 명령이 커밋될 때까지 경과된 시간(초)입니다.</span><span class="sxs-lookup"><span data-stu-id="070db-159">The time, in seconds, that has elapsed between the most recent change being committed in the publication database, and the corresponding command being committed in the distribution database.</span></span>  
  
 <span data-ttu-id="070db-160">**#Trans**</span><span class="sxs-lookup"><span data-stu-id="070db-160">**#Trans**</span></span>  
 <span data-ttu-id="070db-161">가장 최근에 에이전트를 실행할 때 배포 데이터베이스에서 커밋된 트랜잭션의 수입니다.</span><span class="sxs-lookup"><span data-stu-id="070db-161">The number of transactions committed in the distribution database during the most recent run of the agent.</span></span>  
  
 <span data-ttu-id="070db-162">**#Cmds**</span><span class="sxs-lookup"><span data-stu-id="070db-162">**#Cmds**</span></span>  
 <span data-ttu-id="070db-163">가장 최근에 에이전트를 실행할 때 배포 데이터베이스에서 커밋된 명령의 수입니다.</span><span class="sxs-lookup"><span data-stu-id="070db-163">The number of commands committed in the distribution database during the most recent run of the agent.</span></span> <span data-ttu-id="070db-164">명령은 업데이트와 같은 데이터 변경과 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="070db-164">A command is the same as a data change, such as an update.</span></span>  
  
 <span data-ttu-id="070db-165">**평균 명령 수**</span><span class="sxs-lookup"><span data-stu-id="070db-165">**Avg. #Cmds**</span></span>  
 <span data-ttu-id="070db-166">가장 최근에 에이전트를 실행할 때의 트랜잭션당 평균 명령 수입니다.</span><span class="sxs-lookup"><span data-stu-id="070db-166">The average number of commands per transaction during the most recent run of the agent.</span></span>  
  
### <a name="merge-agent"></a><span data-ttu-id="070db-167">병합 에이전트</span><span class="sxs-lookup"><span data-stu-id="070db-167">Merge Agent</span></span>  
 <span data-ttu-id="070db-168">**상태**</span><span class="sxs-lookup"><span data-stu-id="070db-168">**Status**</span></span>  
 <span data-ttu-id="070db-169">에이전트의 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="070db-169">The status of the agent.</span></span> <span data-ttu-id="070db-170">다음 목록에서는 가능한 상태 값을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="070db-170">The following list shows the possible status values:</span></span>  
  
-   <span data-ttu-id="070db-171">오류</span><span class="sxs-lookup"><span data-stu-id="070db-171">Error</span></span>    
-   <span data-ttu-id="070db-172">다시 시도</span><span class="sxs-lookup"><span data-stu-id="070db-172">Retry</span></span>    
-   <span data-ttu-id="070db-173">실행 중</span><span class="sxs-lookup"><span data-stu-id="070db-173">Running</span></span>    
-   <span data-ttu-id="070db-174">실행 중이 아님</span><span class="sxs-lookup"><span data-stu-id="070db-174">Not Running</span></span>    
-   <span data-ttu-id="070db-175">시작한 적 없음</span><span class="sxs-lookup"><span data-stu-id="070db-175">Never started</span></span>  
  
 <span data-ttu-id="070db-176">**게시자**</span><span class="sxs-lookup"><span data-stu-id="070db-176">**Publisher**</span></span>  
 <span data-ttu-id="070db-177">게시자의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="070db-177">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance of the Publisher.</span></span>  
  
 <span data-ttu-id="070db-178">**게시**</span><span class="sxs-lookup"><span data-stu-id="070db-178">**Publication**</span></span>  
 <span data-ttu-id="070db-179">에이전트와 연결된 게시의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="070db-179">The name of the publication with which the agent is associated.</span></span>  
  
 <span data-ttu-id="070db-180">**구독**</span><span class="sxs-lookup"><span data-stu-id="070db-180">**Subscription**</span></span>  
 <span data-ttu-id="070db-181">[*SubscriberName*].[*Database*]와(과) 같은 형식의 구독 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="070db-181">The name of the subscription, in the form: [*SubscriberName*].[*Database*].</span></span>  
  
 <span data-ttu-id="070db-182">**형식**</span><span class="sxs-lookup"><span data-stu-id="070db-182">**Type**</span></span>  
 <span data-ttu-id="070db-183">복제 유형(밀어넣기, 끌어오기 또는 익명)입니다.</span><span class="sxs-lookup"><span data-stu-id="070db-183">Type of replication: push, pull, or Anonymous.</span></span>  
  
 <span data-ttu-id="070db-184">**마지막 시작 시간**</span><span class="sxs-lookup"><span data-stu-id="070db-184">**Last Start Time**</span></span>  
 <span data-ttu-id="070db-185">마지막으로 에이전트가 시작된 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="070db-185">The last time at which the agent started.</span></span>  
  
 <span data-ttu-id="070db-186">**기간**</span><span class="sxs-lookup"><span data-stu-id="070db-186">**Duration**</span></span>  
 <span data-ttu-id="070db-187">에이전트가 실행된 기간입니다.</span><span class="sxs-lookup"><span data-stu-id="070db-187">The length of time that the agent has run.</span></span> <span data-ttu-id="070db-188">에이전트가 현재 실행되고 있는 경우 이 시간은 경과된 시간을 나타내고 에이전트가 이전에 실행된 경우에는 총 시간을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="070db-188">The time represents elapsed time if the agent is currently running, and total time if the agent has run previously.</span></span>  
  
 <span data-ttu-id="070db-189">**마지막 동작**</span><span class="sxs-lookup"><span data-stu-id="070db-189">**Last Action**</span></span>  
 <span data-ttu-id="070db-190">가장 최근의 에이전트 실행에서 수행된 마지막 동작입니다.</span><span class="sxs-lookup"><span data-stu-id="070db-190">The last action that was performed during the most recent run of the agent.</span></span>  
  
 <span data-ttu-id="070db-191">**배달 속도**</span><span class="sxs-lookup"><span data-stu-id="070db-191">**Delivery Rate**</span></span>  
 <span data-ttu-id="070db-192">배포 데이터베이스에서 변경 내용이 커밋된 속도(초당 명령 수)입니다.</span><span class="sxs-lookup"><span data-stu-id="070db-192">The rate, in commands per second, at which changes are committed in the distribution database.</span></span>  
  
 <span data-ttu-id="070db-193">**게시자 삽입**</span><span class="sxs-lookup"><span data-stu-id="070db-193">**Publisher Inserts**</span></span>  
 <span data-ttu-id="070db-194">게시자에서 적용된 INSERT 명령 수입니다.</span><span class="sxs-lookup"><span data-stu-id="070db-194">Number of INSERT commands applied at the Publisher.</span></span>  
  
 <span data-ttu-id="070db-195">**게시자 업데이트**</span><span class="sxs-lookup"><span data-stu-id="070db-195">**Publisher Updates**</span></span>  
 <span data-ttu-id="070db-196">게시자에서 적용된 UPDATE 명령 수입니다.</span><span class="sxs-lookup"><span data-stu-id="070db-196">Number of UPDATE commands applied at the Publisher.</span></span>  
  
 <span data-ttu-id="070db-197">**게시자 삭제**</span><span class="sxs-lookup"><span data-stu-id="070db-197">**Publisher Deletes**</span></span>  
 <span data-ttu-id="070db-198">게시자에서 적용된 DELETE 명령 수입니다.</span><span class="sxs-lookup"><span data-stu-id="070db-198">Number of DELETE commands applied at the Publisher.</span></span>  
  
 <span data-ttu-id="070db-199">**게시자 충돌**</span><span class="sxs-lookup"><span data-stu-id="070db-199">**Publisher Conflicts**</span></span>  
 <span data-ttu-id="070db-200">병합 프로세스 중에 게시자에서 발생한 충돌 수입니다.</span><span class="sxs-lookup"><span data-stu-id="070db-200">The number of conflicts occurring at the Publisher during the merge process.</span></span>  
  
 <span data-ttu-id="070db-201">**구독자 삽입**</span><span class="sxs-lookup"><span data-stu-id="070db-201">**Subscriber Inserts**</span></span>  
 <span data-ttu-id="070db-202">구독자에서 적용된 INSERT 명령 수입니다.</span><span class="sxs-lookup"><span data-stu-id="070db-202">Number of INSERT commands applied at the Subscriber.</span></span>  
  
 <span data-ttu-id="070db-203">**구독자 업데이트**</span><span class="sxs-lookup"><span data-stu-id="070db-203">**Subscriber Updates**</span></span>  
 <span data-ttu-id="070db-204">구독자에서 적용된 UPDATE 명령 수입니다.</span><span class="sxs-lookup"><span data-stu-id="070db-204">Number of UPDATE commands applied at the Subscriber.</span></span>  
  
 <span data-ttu-id="070db-205">**구독자 삭제**</span><span class="sxs-lookup"><span data-stu-id="070db-205">**Subscriber Deletes**</span></span>  
 <span data-ttu-id="070db-206">구독자에서 적용된 DELETE 명령 수입니다.</span><span class="sxs-lookup"><span data-stu-id="070db-206">Number of DELETE commands applied at the Subscriber.</span></span>  
  
 <span data-ttu-id="070db-207">**구독자 충돌**</span><span class="sxs-lookup"><span data-stu-id="070db-207">**Subscriber Conflicts**</span></span>  
 <span data-ttu-id="070db-208">병합 프로세스 중에 구독자에서 발생한 충돌 수입니다.</span><span class="sxs-lookup"><span data-stu-id="070db-208">The number of conflicts occurring at the Subscriber during the merge process.</span></span>  
  
 
## <a name="see-also"></a><span data-ttu-id="070db-209">참고 항목</span><span class="sxs-lookup"><span data-stu-id="070db-209">See Also</span></span>  
 <span data-ttu-id="070db-210">[복제 모니터 시작](monitor/start-the-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="070db-210">[Start the Replication Monitor](monitor/start-the-replication-monitor.md) </span></span>  
 [<span data-ttu-id="070db-211">복제 모니터링</span><span class="sxs-lookup"><span data-stu-id="070db-211">Monitoring Replication</span></span>](monitoring-replication.md)  
  
  
