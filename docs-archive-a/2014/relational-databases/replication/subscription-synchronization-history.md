---
title: 구독, 동기화 기록 (병합 구독, SQL Server 2005 이상) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.subscription.synchhistory.f1
- sql12.rep.monitor.subscription.downlevelsynchhistory.f1
ms.assetid: 85f666f6-14ee-4f19-b385-e5cc508aabe4
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 49fe19f22976116813ac2454b2d08fc1fe47d8de
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653810"
---
# <a name="subscription-synchronization-history-merge-subscription-sql-server-2005-and-later"></a><span data-ttu-id="473aa-102">구독, 동기화 기록(병합 구독, SQL Server 2005 이상)</span><span class="sxs-lookup"><span data-stu-id="473aa-102">Subscription, Synchronization History (Merge Subscription, SQL Server 2005 and Later)</span></span>
  <span data-ttu-id="473aa-103">**동기화 기록** 탭은 상태, 아티클 통계, 기록, 정보 메시지, 모든 오류 메시지 등 병합 에이전트에 대한 자세한 정보를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="473aa-103">The **Synchronization History** tab displays detailed information on the Merge Agent, including status, article statistics, history, informational messages, and any error messages.</span></span>  
  
## <a name="options"></a><span data-ttu-id="473aa-104">옵션</span><span class="sxs-lookup"><span data-stu-id="473aa-104">Options</span></span>  
 <span data-ttu-id="473aa-105">**보기** 메뉴에서 보려는 병합 에이전트 세션을 선택한 다음 **병합 에이전트의 세션**표에서 특정 세션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="473aa-105">Select which Merge Agent sessions to view from the **View** menu, and then select a specific session in the grid labeled **Sessions of the Merge Agent**.</span></span> <span data-ttu-id="473aa-106">**선택한 세션에서 처리한 아티클**표에 이 세션에 대한 자세한 정보가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="473aa-106">Detailed information on this session is displayed in the grid labeled **Articles processed in the selected session**.</span></span>  
  
 <span data-ttu-id="473aa-107">**보기**</span><span class="sxs-lookup"><span data-stu-id="473aa-107">**View**</span></span>  
 <span data-ttu-id="473aa-108">확인할 병합 에이전트 세션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="473aa-108">Select which Merge Agent sessions to view.</span></span>  
  
 <span data-ttu-id="473aa-109">**상태**</span><span class="sxs-lookup"><span data-stu-id="473aa-109">**Status**</span></span>  
 <span data-ttu-id="473aa-110">세션 종료 시 병합 에이전트의 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="473aa-110">The status of the Merge Agent at the end of the session.</span></span> <span data-ttu-id="473aa-111">다음 목록에서는 가능한 상태 값을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="473aa-111">The following list shows the possible status values:</span></span>  
  
-   <span data-ttu-id="473aa-112">Error</span><span class="sxs-lookup"><span data-stu-id="473aa-112">Error</span></span>  
  
-   <span data-ttu-id="473aa-113">Completed</span><span class="sxs-lookup"><span data-stu-id="473aa-113">Completed</span></span>  
  
-   <span data-ttu-id="473aa-114">다시 시도 중</span><span class="sxs-lookup"><span data-stu-id="473aa-114">Retrying</span></span>  
  
-   <span data-ttu-id="473aa-115">실행 중</span><span class="sxs-lookup"><span data-stu-id="473aa-115">Running</span></span>  
  
 <span data-ttu-id="473aa-116">**Start Time**</span><span class="sxs-lookup"><span data-stu-id="473aa-116">**Start Time**</span></span>  
 <span data-ttu-id="473aa-117">세션의 시작 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="473aa-117">The start time of the session.</span></span>  
  
 <span data-ttu-id="473aa-118">**종료 시간**</span><span class="sxs-lookup"><span data-stu-id="473aa-118">**End Time**</span></span>  
 <span data-ttu-id="473aa-119">세션의 종료 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="473aa-119">The end time of the session.</span></span> <span data-ttu-id="473aa-120">에이전트가 중지되지 않은 경우 이 필드는 비어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="473aa-120">If the agent has not stopped, this field is empty.</span></span>  
  
 <span data-ttu-id="473aa-121">**Duration**</span><span class="sxs-lookup"><span data-stu-id="473aa-121">**Duration**</span></span>  
 <span data-ttu-id="473aa-122">세션에서 병합 에이전트가 실행된 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="473aa-122">The amount of time the Merge Agent has run in a session.</span></span> <span data-ttu-id="473aa-123">에이전트가 현재 실행되고 있는 경우 이 시간은 경과된 시간을 나타내고 에이전트가 이전에 실행된 경우에는 총 시간을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="473aa-123">The time represents elapsed time if the agent is currently running and total time if the agent has run previously.</span></span>  
  
 <span data-ttu-id="473aa-124">**업로드된 명령**</span><span class="sxs-lookup"><span data-stu-id="473aa-124">**Uploaded Commands**</span></span>  
 <span data-ttu-id="473aa-125">병합 에이전트 세션 중 업로드된 행 수입니다.</span><span class="sxs-lookup"><span data-stu-id="473aa-125">The number of rows uploaded during the Merge Agent session.</span></span>  
  
 <span data-ttu-id="473aa-126">**다운로드한 명령**</span><span class="sxs-lookup"><span data-stu-id="473aa-126">**Downloaded Commands**</span></span>  
 <span data-ttu-id="473aa-127">병합 에이전트 세션 중 다운로드된 행 수입니다.</span><span class="sxs-lookup"><span data-stu-id="473aa-127">The number of rows downloaded during the Merge Agent session.</span></span>  
  
 <span data-ttu-id="473aa-128">**오류 메시지**</span><span class="sxs-lookup"><span data-stu-id="473aa-128">**Error Message**</span></span>  
 <span data-ttu-id="473aa-129">세션이 오류로 인해 종료된 경우 이 필드는 병합 에이전트에서 기록한 마지막 오류 메시지를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="473aa-129">If a session ended in an error, this field displays the last error message logged by the Merge Agent.</span></span> <span data-ttu-id="473aa-130">세션이 오류 없이 종료된 경우에는 필드가 비어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="473aa-130">If a session did not end in an error, this field is blank.</span></span>  
  
 <span data-ttu-id="473aa-131">**문서**</span><span class="sxs-lookup"><span data-stu-id="473aa-131">**Article**</span></span>  
 <span data-ttu-id="473aa-132">게시에 있는 각 아티클의 이름입니다. 다음은 전체 게시의 처리 단계입니다.</span><span class="sxs-lookup"><span data-stu-id="473aa-132">The name of each article in the publication, and the following processing phases for the entire publication:</span></span>  
  
-   <span data-ttu-id="473aa-133">**초기화**.</span><span class="sxs-lookup"><span data-stu-id="473aa-133">**Initialization**.</span></span> <span data-ttu-id="473aa-134">병합 에이전트를 시작한다는 의미이며 스냅샷 적용과 관련된 구독 초기화와는 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="473aa-134">This refers to starting the Merge Agent; this is not synonymous with initializing a subscription, which involves applying a snapshot.</span></span>  
  
-   <span data-ttu-id="473aa-135">**스키마 변경 및 대량 삽입**</span><span class="sxs-lookup"><span data-stu-id="473aa-135">**Schema changes and bulk inserts**.</span></span>  
  
-   <span data-ttu-id="473aa-136">**게시자에 변경 내용 업로드**</span><span class="sxs-lookup"><span data-stu-id="473aa-136">**Upload changes to Publisher**.</span></span>  
  
-   <span data-ttu-id="473aa-137">**구독자에 변경 내용 다운로드**</span><span class="sxs-lookup"><span data-stu-id="473aa-137">**Download changes to Subscriber**.</span></span>  
  
 <span data-ttu-id="473aa-138">선택한 세션에서 각 단계가 차지하는 시간 및 전체 시간 비율을 표에 표시할 수 있도록 단계를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="473aa-138">The phases are included so that the grid can display the amount of time and percentage of total time that each phase accounts for in the selected session.</span></span>  
  
 <span data-ttu-id="473aa-139">**총 %**</span><span class="sxs-lookup"><span data-stu-id="473aa-139">**% of total**</span></span>  
 <span data-ttu-id="473aa-140">선택한 세션에서 각 단계가 차지하는 처리 시간 비율입니다.</span><span class="sxs-lookup"><span data-stu-id="473aa-140">The percentage of total processing time that each phase accounts for in the selected session.</span></span>  
  
 <span data-ttu-id="473aa-141">**Duration**</span><span class="sxs-lookup"><span data-stu-id="473aa-141">**Duration**</span></span>  
 <span data-ttu-id="473aa-142">각 처리 단계에서 소요된 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="473aa-142">The amount of time spent in each processing phase.</span></span> <span data-ttu-id="473aa-143">병합 에이전트가 현재 세션에 대해 실행 중이면 이 시간은 경과된 시간을 나타내고 병합 에이전트가 이전에 실행된 경우에는 총 시간을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="473aa-143">The time represents elapsed time if the Merge Agent is currently running for the session and total time if the Merge Agent has run previously.</span></span>  
  
 <span data-ttu-id="473aa-144">**Inserts**</span><span class="sxs-lookup"><span data-stu-id="473aa-144">**Inserts**</span></span>  
 <span data-ttu-id="473aa-145">선택한 세션의 이 단계에서 삽입된 행 수입니다.</span><span class="sxs-lookup"><span data-stu-id="473aa-145">The number of rows inserted in this phase of the selected session.</span></span>  
  
 <span data-ttu-id="473aa-146">**업데이트**</span><span class="sxs-lookup"><span data-stu-id="473aa-146">**Updates**</span></span>  
 <span data-ttu-id="473aa-147">선택한 세션의 이 단계에서 업데이트된 행 수입니다.</span><span class="sxs-lookup"><span data-stu-id="473aa-147">The number of rows updated in this phase of the selected session.</span></span>  
  
 <span data-ttu-id="473aa-148">**Deletes**</span><span class="sxs-lookup"><span data-stu-id="473aa-148">**Deletes**</span></span>  
 <span data-ttu-id="473aa-149">선택한 세션의 이 단계에서 삭제된 행 수입니다.</span><span class="sxs-lookup"><span data-stu-id="473aa-149">The number of rows deleted in this phase of the selected session.</span></span>  
  
 <span data-ttu-id="473aa-150">**충돌**</span><span class="sxs-lookup"><span data-stu-id="473aa-150">**Conflicts**</span></span>  
 <span data-ttu-id="473aa-151">선택한 세션의 충돌 수입니다.</span><span class="sxs-lookup"><span data-stu-id="473aa-151">The number of conflicts in the selected session.</span></span>  
  
 <span data-ttu-id="473aa-152">**스키마 변경**</span><span class="sxs-lookup"><span data-stu-id="473aa-152">**Schema Changes**</span></span>  
 <span data-ttu-id="473aa-153">선택한 세션의 스키마 변경 수입니다.</span><span class="sxs-lookup"><span data-stu-id="473aa-153">The number of schema changes in the selected session.</span></span> <span data-ttu-id="473aa-154">구독 데이터베이스에서 스키마 변경 내용이 복제되고, 아티클이 추가 또는 삭제되고, 아티클 또는 구독 속성이 변경될 경우 스키마가 변경될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="473aa-154">Schema changes can result from: schema changes being replicated from the publication database; adding or dropping articles; and changes to article or publication properties.</span></span>  
  
 <span data-ttu-id="473aa-155">**선택한 세션에 대한 마지막 메시지**</span><span class="sxs-lookup"><span data-stu-id="473aa-155">**Last message of the selected session**</span></span>  
 <span data-ttu-id="473aa-156">이 텍스트 영역은 선택한 세션의 마지막 메시지를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="473aa-156">This text area displays the last message in the selected session.</span></span> <span data-ttu-id="473aa-157">오류가 발생하면 오류 발생 시 시도한 명령과 자세한 오류 정보를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="473aa-157">If an error has occurred, it displays detailed error information and the command that was attempted at the time of the error.</span></span> <span data-ttu-id="473aa-158">오류와 관련된 추가 내용으로 연결되는 링크도 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="473aa-158">It also includes links to additional content related to the error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="473aa-159">참고 항목</span><span class="sxs-lookup"><span data-stu-id="473aa-159">See Also</span></span>  
 <span data-ttu-id="473aa-160">[복제 모니터 시작](monitor/start-the-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="473aa-160">[Start the Replication Monitor](monitor/start-the-replication-monitor.md) </span></span>  
 <span data-ttu-id="473aa-161">[복제 모니터를 사용하여 정보 보기 및 태스크 수행](monitor/view-information-and-perform-tasks-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="473aa-161">[View Information and Perform Tasks using Replication Monitor](monitor/view-information-and-perform-tasks-replication-monitor.md) </span></span>  
 <span data-ttu-id="473aa-162">[복제 모니터링](monitoring-replication.md) </span><span class="sxs-lookup"><span data-stu-id="473aa-162">[Monitoring Replication](monitoring-replication.md) </span></span>  
 [<span data-ttu-id="473aa-163">복제 에이전트 개요</span><span class="sxs-lookup"><span data-stu-id="473aa-163">Replication Agents Overview</span></span>](agents/replication-agents-overview.md)  
  
  
