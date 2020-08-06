---
title: 게시자 정보, 에이전트 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.publisherinfo.commonjobs.f1
ms.assetid: 2346c00d-c269-45a1-af14-68e7fd7ebd7e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: bdd2055ed022257524bc4d2784bdc333537be855
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646329"
---
# <a name="publisher-information-agents"></a><span data-ttu-id="c3f9f-102">게시자 정보, 에이전트</span><span class="sxs-lookup"><span data-stu-id="c3f9f-102">Publisher Information, Agents</span></span>
  <span data-ttu-id="c3f9f-103">**에이전트** 탭에는 게시자와 연결된 에이전트 및 유지 관리 작업에 대한 정보가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c3f9f-103">The **Agents** tab displays information about the agents and maintenance jobs that are associated with the Publisher:</span></span>  
  
-   <span data-ttu-id="c3f9f-104">스냅샷 에이전트 - 모든 게시에 대해 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c3f9f-104">Snapshot Agent, which is displayed for all publications.</span></span>  
  
-   <span data-ttu-id="c3f9f-105">로그 판독기 에이전트 - 모든 트랜잭션 게시에 대해 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c3f9f-105">Log Reader Agent, which is displayed for all transactional publications.</span></span>  
  
-   <span data-ttu-id="c3f9f-106">큐 판독기 에이전트 - 지연 업데이트 구독이 설정된 트랜잭션 게시에 대해 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c3f9f-106">Queue Reader Agent, which is displayed for those transactional publications that are enabled for queued updating subscriptions.</span></span>  
  
-   <span data-ttu-id="c3f9f-107">유지 관리 작업 - 모든 게시에 대해 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c3f9f-107">Maintenance jobs, displayed for all publications:</span></span>  
  
    -   <span data-ttu-id="c3f9f-108">데이터 유효성 검사에 실패한 구독 다시 초기화</span><span class="sxs-lookup"><span data-stu-id="c3f9f-108">Reinitialize subscriptions that have data validation failures</span></span>  
  
    -   <span data-ttu-id="c3f9f-109">에이전트 기록 정리: 배포</span><span class="sxs-lookup"><span data-stu-id="c3f9f-109">Agent history cleanup: distribution</span></span>  
  
    -   <span data-ttu-id="c3f9f-110">배포에 대한 복제 모니터링 리프레셔</span><span class="sxs-lookup"><span data-stu-id="c3f9f-110">Replication monitoring refresher for distribution</span></span>  
  
    -   <span data-ttu-id="c3f9f-111">복제 에이전트 점검</span><span class="sxs-lookup"><span data-stu-id="c3f9f-111">Replication agents checkup</span></span>  
  
    -   <span data-ttu-id="c3f9f-112">배포 정리: 배포</span><span class="sxs-lookup"><span data-stu-id="c3f9f-112">Distribution cleanup: distribution</span></span>  
  
    -   <span data-ttu-id="c3f9f-113">만료된 구독 정리</span><span class="sxs-lookup"><span data-stu-id="c3f9f-113">Expired subscription cleanup</span></span>  
  
 <span data-ttu-id="c3f9f-114">이러한 작업에 대한 자세한 내용은 [복제 에이전트 관리](agents/replication-agent-administration.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c3f9f-114">For more information about these jobs, see [Replication Agent Administration](agents/replication-agent-administration.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="c3f9f-115">옵션</span><span class="sxs-lookup"><span data-stu-id="c3f9f-115">Options</span></span>  
 <span data-ttu-id="c3f9f-116">에이전트 또는 작업에 대한 정보를 표시하려면 **Agent and Job Types** 드롭다운 메뉴에서 해당 정보를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c3f9f-116">To display information about an agent or job, select from the **Agent and Job Types** drop-down menu.</span></span> <span data-ttu-id="c3f9f-117">자세한 내용 및 에이전트 또는 작업과 관련된 태스크를 보려면 해당 에이전트 또는 작업에 대한 행을 마우스 오른쪽 단추로 클릭한 다음 바로 가기 메뉴에서 옵션을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c3f9f-117">For more detailed information and tasks that are related to an agent or job, right-click the row for that agent or job, and then click an option on the shortcut menu.</span></span> <span data-ttu-id="c3f9f-118">표에서 데이터를 표시하는 방식을 변경하려면 표를 마우스 오른쪽 단추로 클릭한 후 다음 옵션 중 하나를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c3f9f-118">To change the way that the grid displays data, right-click the grid, and then click one of the following options:</span></span>  
  
-   <span data-ttu-id="c3f9f-119">**정렬**: **열 정렬** 대화 상자에서 한 개 이상의 열에 대해 정렬합니다.</span><span class="sxs-lookup"><span data-stu-id="c3f9f-119">**Sort**: Sort on one or more columns in the **Sort Columns** dialog box.</span></span>  
  
-   <span data-ttu-id="c3f9f-120">**표시할 열 선택**: **열 선택** 대화 상자에서 표시할 열 및 해당 열이 표시되는 순서를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c3f9f-120">**Choose Columns to Show**: Select which columns to display and the order in which to display them in the **Choose Columns** dialog box.</span></span>  
  
-   <span data-ttu-id="c3f9f-121">**필터**: **필터 설정** 대화 상자의 열 값에 따라 표의 행을 필터링합니다.</span><span class="sxs-lookup"><span data-stu-id="c3f9f-121">**Filter**: Filter rows in the grid based on column values in the **Filter Settings** dialog box.</span></span>  
  
-   <span data-ttu-id="c3f9f-122">**필터 지우기**: 표에 대한 모든 필터 설정을 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="c3f9f-122">**Clear Filter**: Clear any filter settings for the grid.</span></span>  
  
 <span data-ttu-id="c3f9f-123">필터 설정은 각 표에 대해 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="c3f9f-123">Filter settings are specific to each grid.</span></span> <span data-ttu-id="c3f9f-124">열 선택 및 정렬은 각 게시자에 대한 게시 표와 같이 동일한 유형의 모든 표에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="c3f9f-124">Column selection and sorting are applied to all grids of the same type, such as the publications grid for each Publisher.</span></span>  
  
 <span data-ttu-id="c3f9f-125">다음 섹션에서는 이 탭에서 각 에이전트 또는 작업에 대해 표시되는 데이터를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="c3f9f-125">The following sections describe the data that is displayed on this tab for each agent or job.</span></span>  
  
### <a name="snapshot-agent"></a><span data-ttu-id="c3f9f-126">스냅샷 에이전트</span><span class="sxs-lookup"><span data-stu-id="c3f9f-126">Snapshot Agent</span></span>  
 <span data-ttu-id="c3f9f-127">**상태**</span><span class="sxs-lookup"><span data-stu-id="c3f9f-127">**Status**</span></span>  
 <span data-ttu-id="c3f9f-128">에이전트의 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="c3f9f-128">The status of the agent.</span></span> <span data-ttu-id="c3f9f-129">다음 목록에서는 가능한 상태 값을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c3f9f-129">The following list shows the possible status values:</span></span>  
  
-   <span data-ttu-id="c3f9f-130">Error</span><span class="sxs-lookup"><span data-stu-id="c3f9f-130">Error</span></span>  
  
-   <span data-ttu-id="c3f9f-131">다시 시도</span><span class="sxs-lookup"><span data-stu-id="c3f9f-131">Retry</span></span>  
  
-   <span data-ttu-id="c3f9f-132">실행 중</span><span class="sxs-lookup"><span data-stu-id="c3f9f-132">Running</span></span>  
  
-   <span data-ttu-id="c3f9f-133">Completed</span><span class="sxs-lookup"><span data-stu-id="c3f9f-133">Completed</span></span>  
  
 <span data-ttu-id="c3f9f-134">**게시**</span><span class="sxs-lookup"><span data-stu-id="c3f9f-134">**Publication**</span></span>  
 <span data-ttu-id="c3f9f-135">에이전트와 연결된 게시의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="c3f9f-135">The name of the publication with which the agent is associated.</span></span>  
  
 <span data-ttu-id="c3f9f-136">**마지막 시작 시간**</span><span class="sxs-lookup"><span data-stu-id="c3f9f-136">**Last Start Time**</span></span>  
 <span data-ttu-id="c3f9f-137">마지막으로 에이전트가 시작된 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="c3f9f-137">The last time at which the agent started.</span></span>  
  
 <span data-ttu-id="c3f9f-138">**Duration**</span><span class="sxs-lookup"><span data-stu-id="c3f9f-138">**Duration**</span></span>  
 <span data-ttu-id="c3f9f-139">에이전트가 실행된 기간입니다.</span><span class="sxs-lookup"><span data-stu-id="c3f9f-139">The length of time the agent has run.</span></span> <span data-ttu-id="c3f9f-140">에이전트가 현재 실행되고 있는 경우 이 시간은 경과된 시간을 나타내고 에이전트가 이전에 실행된 경우에는 총 시간을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c3f9f-140">The time represents elapsed time if the agent is currently running, and total time if the agent has run previously.</span></span>  
  
 <span data-ttu-id="c3f9f-141">**마지막 동작**</span><span class="sxs-lookup"><span data-stu-id="c3f9f-141">**Last Action**</span></span>  
 <span data-ttu-id="c3f9f-142">가장 최근의 에이전트 실행에서 수행된 마지막 동작입니다.</span><span class="sxs-lookup"><span data-stu-id="c3f9f-142">The last action performed during the most recent run of the agent.</span></span>  
  
 <span data-ttu-id="c3f9f-143">**배달 속도**</span><span class="sxs-lookup"><span data-stu-id="c3f9f-143">**Delivery Rate**</span></span>  
 <span data-ttu-id="c3f9f-144">가장 최근에 에이전트를 실행할 때 배포 데이터베이스에서 초기화 명령이 커밋된 속도(초당 명령 수)입니다.</span><span class="sxs-lookup"><span data-stu-id="c3f9f-144">The rate, in commands per second, at which initialization commands are committed in the distribution database during the most recent run of the agent.</span></span>  
  
 <span data-ttu-id="c3f9f-145">**#Trans**</span><span class="sxs-lookup"><span data-stu-id="c3f9f-145">**#Trans**</span></span>  
 <span data-ttu-id="c3f9f-146">가장 최근에 에이전트를 실행할 때 배포 데이터베이스에서 커밋된 트랜잭션의 수입니다.</span><span class="sxs-lookup"><span data-stu-id="c3f9f-146">The number of transactions committed in the distribution database during the most recent run of the agent.</span></span>  
  
 <span data-ttu-id="c3f9f-147">**#Cmds**</span><span class="sxs-lookup"><span data-stu-id="c3f9f-147">**#Cmds**</span></span>  
 <span data-ttu-id="c3f9f-148">가장 최근에 에이전트를 실행할 때 배포 데이터베이스에서 커밋된 명령의 수입니다.</span><span class="sxs-lookup"><span data-stu-id="c3f9f-148">The number of commands committed in the distribution database during the most recent run of the agent.</span></span> <span data-ttu-id="c3f9f-149">명령은 업데이트와 같은 데이터 변경에 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="c3f9f-149">A command is equivalent to a data change, such as an update.</span></span>  
  
### <a name="log-reader-agent"></a><span data-ttu-id="c3f9f-150">로그 판독기 에이전트</span><span class="sxs-lookup"><span data-stu-id="c3f9f-150">Log Reader Agent</span></span>  
 <span data-ttu-id="c3f9f-151">**상태**</span><span class="sxs-lookup"><span data-stu-id="c3f9f-151">**Status**</span></span>  
 <span data-ttu-id="c3f9f-152">에이전트의 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="c3f9f-152">The status of the agent.</span></span> <span data-ttu-id="c3f9f-153">다음 목록에서는 가능한 상태 값을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c3f9f-153">The following list shows the possible status values:</span></span>  
  
-   <span data-ttu-id="c3f9f-154">Error</span><span class="sxs-lookup"><span data-stu-id="c3f9f-154">Error</span></span>  
  
-   <span data-ttu-id="c3f9f-155">다시 시도</span><span class="sxs-lookup"><span data-stu-id="c3f9f-155">Retry</span></span>  
  
-   <span data-ttu-id="c3f9f-156">실행 중</span><span class="sxs-lookup"><span data-stu-id="c3f9f-156">Running</span></span>  
  
-   <span data-ttu-id="c3f9f-157">실행 중이 아님</span><span class="sxs-lookup"><span data-stu-id="c3f9f-157">Not running</span></span>  
  
 <span data-ttu-id="c3f9f-158">**게시 데이터베이스**</span><span class="sxs-lookup"><span data-stu-id="c3f9f-158">**Publication Database**</span></span>  
 <span data-ttu-id="c3f9f-159">에이전트와 연결된 게시의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="c3f9f-159">The name of the publication with which the agent is associated.</span></span>  
  
 <span data-ttu-id="c3f9f-160">**마지막 시작 시간**</span><span class="sxs-lookup"><span data-stu-id="c3f9f-160">**Last Start Time**</span></span>  
 <span data-ttu-id="c3f9f-161">마지막으로 에이전트가 시작된 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="c3f9f-161">The last time at which the agent started.</span></span>  
  
 <span data-ttu-id="c3f9f-162">**Duration**</span><span class="sxs-lookup"><span data-stu-id="c3f9f-162">**Duration**</span></span>  
 <span data-ttu-id="c3f9f-163">에이전트가 실행된 기간입니다.</span><span class="sxs-lookup"><span data-stu-id="c3f9f-163">The length of time the agent has run.</span></span> <span data-ttu-id="c3f9f-164">에이전트가 현재 실행되고 있는 경우 이 시간은 경과된 시간을 나타내고 에이전트가 이전에 실행된 경우에는 총 시간을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c3f9f-164">The time represents elapsed time if the agent is currently running, and total time if the agent has run previously.</span></span>  
  
 <span data-ttu-id="c3f9f-165">**마지막 동작**</span><span class="sxs-lookup"><span data-stu-id="c3f9f-165">**Last Action**</span></span>  
 <span data-ttu-id="c3f9f-166">가장 최근의 에이전트 실행에서 수행된 마지막 동작입니다.</span><span class="sxs-lookup"><span data-stu-id="c3f9f-166">The last action performed during the most recent run of the agent.</span></span>  
  
 <span data-ttu-id="c3f9f-167">**배달 속도**</span><span class="sxs-lookup"><span data-stu-id="c3f9f-167">**Delivery Rate**</span></span>  
 <span data-ttu-id="c3f9f-168">배포 데이터베이스에서 변경 내용이 커밋된 속도(초당 명령 수)입니다.</span><span class="sxs-lookup"><span data-stu-id="c3f9f-168">The rate, in commands per second, at which changes are committed in the distribution database.</span></span>  
  
 <span data-ttu-id="c3f9f-169">**대기 시간**</span><span class="sxs-lookup"><span data-stu-id="c3f9f-169">**Latency**</span></span>  
 <span data-ttu-id="c3f9f-170">게시 데이터베이스에서 가장 최근의 변경 내용이 커밋된 후 배포 데이터베이스에서 해당 명령이 커밋될 때까지 경과된 시간(초)입니다.</span><span class="sxs-lookup"><span data-stu-id="c3f9f-170">The amount of time, in seconds, that has elapsed between the most recent change being committed in the publication database, and the corresponding command being committed in the distribution database.</span></span>  
  
 <span data-ttu-id="c3f9f-171">**#Trans**</span><span class="sxs-lookup"><span data-stu-id="c3f9f-171">**#Trans**</span></span>  
 <span data-ttu-id="c3f9f-172">가장 최근에 에이전트를 실행할 때 배포 데이터베이스에서 커밋된 트랜잭션의 수입니다.</span><span class="sxs-lookup"><span data-stu-id="c3f9f-172">The number of transactions committed in the distribution database during the most recent run of the agent.</span></span>  
  
 <span data-ttu-id="c3f9f-173">**#Cmds**</span><span class="sxs-lookup"><span data-stu-id="c3f9f-173">**#Cmds**</span></span>  
 <span data-ttu-id="c3f9f-174">가장 최근에 에이전트를 실행할 때 배포 데이터베이스에서 커밋된 명령의 수입니다.</span><span class="sxs-lookup"><span data-stu-id="c3f9f-174">The number of commands committed in the distribution database during the most recent run of the agent.</span></span> <span data-ttu-id="c3f9f-175">명령은 업데이트와 같은 데이터 변경에 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="c3f9f-175">A command is equivalent to a data change, such as an update.</span></span>  
  
 <span data-ttu-id="c3f9f-176">**평균 명령 수**</span><span class="sxs-lookup"><span data-stu-id="c3f9f-176">**Avg. #Cmds**</span></span>  
 <span data-ttu-id="c3f9f-177">가장 최근에 에이전트를 실행할 때의 트랜잭션당 평균 명령 수입니다.</span><span class="sxs-lookup"><span data-stu-id="c3f9f-177">The average number of commands per transaction during the most recent run of the agent.</span></span>  
  
### <a name="queue-reader-agent"></a><span data-ttu-id="c3f9f-178">큐 판독기 에이전트</span><span class="sxs-lookup"><span data-stu-id="c3f9f-178">Queue Reader Agent</span></span>  
 <span data-ttu-id="c3f9f-179">**상태**</span><span class="sxs-lookup"><span data-stu-id="c3f9f-179">**Status**</span></span>  
 <span data-ttu-id="c3f9f-180">에이전트의 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="c3f9f-180">The status of the agent.</span></span> <span data-ttu-id="c3f9f-181">다음 목록에서는 가능한 상태 값을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c3f9f-181">The following list shows the possible status values:</span></span>  
  
-   <span data-ttu-id="c3f9f-182">Error</span><span class="sxs-lookup"><span data-stu-id="c3f9f-182">Error</span></span>  
  
-   <span data-ttu-id="c3f9f-183">다시 시도</span><span class="sxs-lookup"><span data-stu-id="c3f9f-183">Retry</span></span>  
  
-   <span data-ttu-id="c3f9f-184">실행 중</span><span class="sxs-lookup"><span data-stu-id="c3f9f-184">Running</span></span>  
  
-   <span data-ttu-id="c3f9f-185">실행 중이 아님</span><span class="sxs-lookup"><span data-stu-id="c3f9f-185">Not running</span></span>  
  
 <span data-ttu-id="c3f9f-186">**배포 데이터베이스**</span><span class="sxs-lookup"><span data-stu-id="c3f9f-186">**Distribution Database**</span></span>  
 <span data-ttu-id="c3f9f-187">에이전트와 연결된 배포 데이터베이스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="c3f9f-187">The name of the distribution database with which the agent is associated.</span></span>  
  
 <span data-ttu-id="c3f9f-188">**마지막 시작 시간**</span><span class="sxs-lookup"><span data-stu-id="c3f9f-188">**Last Start Time**</span></span>  
 <span data-ttu-id="c3f9f-189">마지막으로 에이전트가 시작된 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="c3f9f-189">The last time at which the agent started.</span></span>  
  
 <span data-ttu-id="c3f9f-190">**Duration**</span><span class="sxs-lookup"><span data-stu-id="c3f9f-190">**Duration**</span></span>  
 <span data-ttu-id="c3f9f-191">에이전트가 실행된 기간입니다.</span><span class="sxs-lookup"><span data-stu-id="c3f9f-191">The length of time the agent has run.</span></span> <span data-ttu-id="c3f9f-192">에이전트가 현재 실행되고 있는 경우 이 시간은 경과된 시간을 나타내고 에이전트가 이전에 실행된 경우에는 총 시간을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c3f9f-192">The time represents elapsed time if the agent is currently running and total time if the agent has run previously.</span></span>  
  
 <span data-ttu-id="c3f9f-193">**마지막 동작**</span><span class="sxs-lookup"><span data-stu-id="c3f9f-193">**Last Action**</span></span>  
 <span data-ttu-id="c3f9f-194">가장 최근의 에이전트 실행에서 수행된 마지막 동작입니다.</span><span class="sxs-lookup"><span data-stu-id="c3f9f-194">The last action performed during the most recent run of the agent.</span></span>  
  
 <span data-ttu-id="c3f9f-195">**배달 속도**</span><span class="sxs-lookup"><span data-stu-id="c3f9f-195">**Delivery Rate**</span></span>  
 <span data-ttu-id="c3f9f-196">배포 데이터베이스에서 변경 내용이 커밋된 속도(초당 명령 수)입니다.</span><span class="sxs-lookup"><span data-stu-id="c3f9f-196">The rate, in commands per second, at which changes are committed in the distribution database.</span></span>  
  
 <span data-ttu-id="c3f9f-197">**대기 시간**</span><span class="sxs-lookup"><span data-stu-id="c3f9f-197">**Latency**</span></span>  
 <span data-ttu-id="c3f9f-198">구독 데이터베이스에서 가장 최근의 변경 내용이 커밋된 후 게시 데이터베이스에서 해당 명령이 커밋될 때까지 경과된 시간(초)입니다.</span><span class="sxs-lookup"><span data-stu-id="c3f9f-198">The amount of time, in seconds, that has elapsed between the most recent change being committed in a subscription database, and the corresponding command being committed in the publication database.</span></span>  
  
 <span data-ttu-id="c3f9f-199">**#Trans**</span><span class="sxs-lookup"><span data-stu-id="c3f9f-199">**#Trans**</span></span>  
 <span data-ttu-id="c3f9f-200">가장 최근에 에이전트를 실행할 때 게시 데이터베이스에서 커밋된 트랜잭션의 수입니다.</span><span class="sxs-lookup"><span data-stu-id="c3f9f-200">The number of transactions committed in the publication database during the most recent run of the agent.</span></span>  
  
 <span data-ttu-id="c3f9f-201">**#Cmds**</span><span class="sxs-lookup"><span data-stu-id="c3f9f-201">**#Cmds**</span></span>  
 <span data-ttu-id="c3f9f-202">가장 최근에 에이전트를 실행할 때 게시 데이터베이스에서 커밋된 명령의 수입니다.</span><span class="sxs-lookup"><span data-stu-id="c3f9f-202">The number of commands committed in the publication database during the most recent run of the agent.</span></span> <span data-ttu-id="c3f9f-203">명령은 업데이트와 같은 데이터 변경에 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="c3f9f-203">A command is equivalent to a data change, such as an update.</span></span>  
  
 <span data-ttu-id="c3f9f-204">**평균 명령 수**</span><span class="sxs-lookup"><span data-stu-id="c3f9f-204">**Avg. #Cmds**</span></span>  
 <span data-ttu-id="c3f9f-205">가장 최근에 에이전트를 실행할 때의 트랜잭션당 평균 명령 수입니다.</span><span class="sxs-lookup"><span data-stu-id="c3f9f-205">The average number of commands per transaction during the most recent run of the agent.</span></span>  
  
### <a name="maintenance-jobs"></a><span data-ttu-id="c3f9f-206">유리 관리 작업</span><span class="sxs-lookup"><span data-stu-id="c3f9f-206">Maintenance Jobs</span></span>  
 <span data-ttu-id="c3f9f-207">**상태**</span><span class="sxs-lookup"><span data-stu-id="c3f9f-207">**Status**</span></span>  
 <span data-ttu-id="c3f9f-208">각 작업의 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="c3f9f-208">The status of each job.</span></span> <span data-ttu-id="c3f9f-209">다음 목록에서는 가능한 상태 값을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c3f9f-209">The following list shows the possible status values:</span></span>  
  
-   <span data-ttu-id="c3f9f-210">Error</span><span class="sxs-lookup"><span data-stu-id="c3f9f-210">Error</span></span>  
  
-   <span data-ttu-id="c3f9f-211">다시 시도</span><span class="sxs-lookup"><span data-stu-id="c3f9f-211">Retry</span></span>  
  
-   <span data-ttu-id="c3f9f-212">실행 중</span><span class="sxs-lookup"><span data-stu-id="c3f9f-212">Running</span></span>  
  
-   <span data-ttu-id="c3f9f-213">실행 중이 아님</span><span class="sxs-lookup"><span data-stu-id="c3f9f-213">Not running</span></span>  
  
 <span data-ttu-id="c3f9f-214">**작업**</span><span class="sxs-lookup"><span data-stu-id="c3f9f-214">**Job**</span></span>  
 <span data-ttu-id="c3f9f-215">작업의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="c3f9f-215">The name of the job.</span></span>  
  
 <span data-ttu-id="c3f9f-216">**마지막 시작 시간**</span><span class="sxs-lookup"><span data-stu-id="c3f9f-216">**Last Start Time**</span></span>  
 <span data-ttu-id="c3f9f-217">마지막으로 작업이 시작된 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="c3f9f-217">The last time at which the job started.</span></span>  
  
 <span data-ttu-id="c3f9f-218">**Duration**</span><span class="sxs-lookup"><span data-stu-id="c3f9f-218">**Duration**</span></span>  
 <span data-ttu-id="c3f9f-219">작업이 실행된 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="c3f9f-219">The length of time the job has run.</span></span> <span data-ttu-id="c3f9f-220">이 시간은 작업이 현재 실행되고 있는 경우에는 경과된 시간을 나타내고 작업이 이전에 실행된 경우에는 총 시간을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c3f9f-220">The time represents elapsed time if the job is currently running, and total time if the job has run previously.</span></span>  
  
 <span data-ttu-id="c3f9f-221">**마지막 동작**</span><span class="sxs-lookup"><span data-stu-id="c3f9f-221">**Last Action**</span></span>  
 <span data-ttu-id="c3f9f-222">가장 최근의 작업 실행에서 수행된 마지막 동작입니다.</span><span class="sxs-lookup"><span data-stu-id="c3f9f-222">The last action performed during the most recent run of the job.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3f9f-223">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c3f9f-223">See Also</span></span>  
 <span data-ttu-id="c3f9f-224">[복제 모니터 시작](monitor/start-the-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="c3f9f-224">[Start the Replication Monitor](monitor/start-the-replication-monitor.md) </span></span>  
 <span data-ttu-id="c3f9f-225">[복제 모니터를 사용하여 정보 보기 및 태스크 수행](monitor/view-information-and-perform-tasks-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="c3f9f-225">[View Information and Perform Tasks using Replication Monitor](monitor/view-information-and-perform-tasks-replication-monitor.md) </span></span>  
 [<span data-ttu-id="c3f9f-226">복제 모니터링</span><span class="sxs-lookup"><span data-stu-id="c3f9f-226">Monitoring Replication</span></span>](monitoring-replication.md)  
  
  
