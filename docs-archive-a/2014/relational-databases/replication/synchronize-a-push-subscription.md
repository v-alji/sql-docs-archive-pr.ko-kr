---
title: 밀어넣기 구독 동기화 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- synchronization [SQL Server replication], push subscriptions
- subscriptions [SQL Server replication], push
- push subscriptions [SQL Server replication], synchronizing
ms.assetid: 0cfa7ae5-91d3-4a4f-9edf-a852d45783b5
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5fb2f7bd961748272d6cd67e3412b09d9370a6f3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732559"
---
# <a name="synchronize-a-push-subscription"></a><span data-ttu-id="90a75-102">밀어넣기 구독 동기화</span><span class="sxs-lookup"><span data-stu-id="90a75-102">Synchronize a Push Subscription</span></span>
  <span data-ttu-id="90a75-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] , [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]복제 에이전트 [또는 RMO(복제 관리 개체)를 사용하여](agents/replication-agents-overview.md)에서 밀어넣기 구독을 동기화하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="90a75-103">This topic describes how to synchronize a push subscription in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [replication agents](agents/replication-agents-overview.md), or Replication Management Objects (RMO).</span></span>  
  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="90a75-104">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="90a75-104">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="90a75-105">구독은 배포 에이전트(스냅샷 및 트랜잭션 복제의 경우) 또는 병합 에이전트(병합 복제의 경우)에 의해 동기화됩니다.</span><span class="sxs-lookup"><span data-stu-id="90a75-105">Subscriptions are synchronized by the Distribution Agent (for snapshot and transactional replication) or the Merge Agent (for merge replication).</span></span> <span data-ttu-id="90a75-106">에이전트는 지속적으로 실행하거나 수요에 따라 실행하거나 일정에 따라 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="90a75-106">Agents can run continuously, run on demand, or run on a schedule.</span></span> <span data-ttu-id="90a75-107">동기화 일정을 설정하는 방법은 [동기화 일정 지정](specify-synchronization-schedules.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="90a75-107">For more information about specifying synchronization schedules, see [Specify Synchronization Schedules](specify-synchronization-schedules.md).</span></span>  
  
 <span data-ttu-id="90a75-108">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]의 **로컬 게시** 및 **로컬 구독** 폴더와 복제 모니터의 **모든 구독** 탭에서 요청 시 구독을 동기화합니다.</span><span class="sxs-lookup"><span data-stu-id="90a75-108">Synchronize a subscription on demand from the **Local Publications** and **Local Subscriptions** folders in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] and the **All Subscriptions** tab in Replication Monitor.</span></span> <span data-ttu-id="90a75-109">Oracle 게시에 대한 구독은 구독자에서 요청 시 동기화할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="90a75-109">Subscriptions to Oracle publications cannot be synchronized on demand from the Subscriber.</span></span> <span data-ttu-id="90a75-110">복제 모니터를 시작하는 방법은 [복제 모니터 시작](monitor/start-the-replication-monitor.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="90a75-110">For information about starting Replication Monitor, see [Start the Replication Monitor](monitor/start-the-replication-monitor.md).</span></span>  
  
#### <a name="to-synchronize-a-push-subscription-on-demand-in-management-studio-at-the-publisher"></a><span data-ttu-id="90a75-111">Management Studio에서 요청 시 밀어넣기 구독을 동기화하려면(게시자)</span><span class="sxs-lookup"><span data-stu-id="90a75-111">To synchronize a push subscription on demand in Management Studio (at the Publisher)</span></span>  
  
1.  <span data-ttu-id="90a75-112">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]에서 게시자에 연결한 다음 해당 서버 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="90a75-112">Connect to the Publisher in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="90a75-113">**복제** 폴더를 확장한 다음 **로컬 게시** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="90a75-113">Expand the **Replication** folder, and then expand the **Local Publications** folder.</span></span>  
  
3.  <span data-ttu-id="90a75-114">구독을 동기화할 게시를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="90a75-114">Expand the publication for which you want to synchronize subscriptions.</span></span>  
  
4.  <span data-ttu-id="90a75-115">동기화할 구독을 마우스 오른쪽 단추로 클릭한 다음 **동기화 상태 보기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="90a75-115">Right-click the subscription you want to synchronize, and then click **View Synchronization Status**.</span></span>  
  
5.  <span data-ttu-id="90a75-116">**동기화 상태 보기 - \<Subscriber>:\<SubscriptionDatabase>** 대화 상자에서 **시작**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="90a75-116">In the **View Synchronization Status - \<Subscriber>:\<SubscriptionDatabase>** dialog box, click **Start**.</span></span> <span data-ttu-id="90a75-117">동기화가 완료되면 **동기화 완료** 라는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="90a75-117">When synchronization is complete, the message **Synchronization completed** is displayed.</span></span>  
  
6.  <span data-ttu-id="90a75-118">**닫기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="90a75-118">Click **Close**.</span></span>  
  
#### <a name="to-synchronize-a-push-subscription-on-demand-in-management-studio-at-the-subscriber"></a><span data-ttu-id="90a75-119">Management Studio에서 요청 시 밀어넣기 구독을 동기화하려면(구독자)</span><span class="sxs-lookup"><span data-stu-id="90a75-119">To synchronize a push subscription on demand in Management Studio (at the Subscriber)</span></span>  
  
1.  <span data-ttu-id="90a75-120">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]에서 구독자에 연결한 다음 해당 서버 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="90a75-120">Connect to the Subscriber in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="90a75-121">**복제** 폴더를 확장한 다음 **로컬 구독** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="90a75-121">Expand the **Replication** folder, and then expand the **Local Subscriptions** folder.</span></span>  
  
3.  <span data-ttu-id="90a75-122">동기화할 구독을 마우스 오른쪽 단추로 클릭한 다음 **동기화 상태 보기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="90a75-122">Right-click the subscription you want to synchronize, and then click **View Synchronization Status**.</span></span>  
  
4.  <span data-ttu-id="90a75-123">배포자 연결 설정에 대한 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="90a75-123">A message is displayed about establishing a connection to the Distributor.</span></span> <span data-ttu-id="90a75-124">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="90a75-124">Click **OK**.</span></span>  
  
5.  <span data-ttu-id="90a75-125">**동기화 상태 보기 - \<Subscriber>:\<SubscriptionDatabase>** 대화 상자에서 **시작**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="90a75-125">In the **View Synchronization Status - \<Subscriber>:\<SubscriptionDatabase>** dialog box, click **Start**.</span></span> <span data-ttu-id="90a75-126">동기화가 완료되면 **동기화 완료** 라는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="90a75-126">When synchronization is complete, the message **Synchronization completed** is displayed.</span></span>  
  
6.  <span data-ttu-id="90a75-127">**닫기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="90a75-127">Click **Close**.</span></span>  
  
#### <a name="to-synchronize-a-push-subscription-on-demand-in-replication-monitor"></a><span data-ttu-id="90a75-128">복제 모니터에서 요청 시 밀어넣기 구독을 동기화하려면</span><span class="sxs-lookup"><span data-stu-id="90a75-128">To synchronize a push subscription on demand in Replication Monitor</span></span>  
  
1.  <span data-ttu-id="90a75-129">복제 모니터에서 왼쪽 창의 게시자 그룹을 확장하고 해당 게시자를 확장한 다음 해당 게시를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="90a75-129">In Replication Monitor, expand a Publisher group in the left pane, expand a Publisher, and then click a publication.</span></span>  
  
2.  <span data-ttu-id="90a75-130">**모든 구독** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="90a75-130">Click the **All Subscriptions** tab.</span></span>  
  
3.  <span data-ttu-id="90a75-131">동기화할 구독을 마우스 오른쪽 단추로 클릭한 다음 **동기화 시작**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="90a75-131">Right-click the subscription you want to synchronize, and then click **Start Synchronizing**.</span></span>  
  
4.  <span data-ttu-id="90a75-132">동기화 진행률을 보려면 해당 구독을 마우스 오른쪽 단추로 클릭한 다음 **자세히 보기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="90a75-132">To view synchronization progress, right-click the subscription, and then click **View Details**.</span></span>  
  
##  <a name="using-replication-agents"></a><a name="ReplProg"></a> <span data-ttu-id="90a75-133">복제 에이전트 사용</span><span class="sxs-lookup"><span data-stu-id="90a75-133">Using Replication Agents</span></span>  
 <span data-ttu-id="90a75-134">밀어넣기 구독은 명령 프롬프트에서 적합한 복제 에이전트 실행 파일을 호출하여 프로그래밍 방식으로 요청 시 동기화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="90a75-134">Push subscriptions can be synchronized programmatically and on-demand by invoking the appropriate replication agent executable file from the command prompt.</span></span> <span data-ttu-id="90a75-135">호출한 복제 에이전트 실행 파일은 밀어넣기 구독이 속한 게시 유형에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="90a75-135">The replication agent executable file that is invoked will depend on the type of publication to which the push subscription belongs.</span></span>  
  
#### <a name="to-start-the-distribution-agent-to-synchronize-a-push-subscription-to-a-transactional-publication"></a><span data-ttu-id="90a75-136">배포 에이전트를 시작하여 트랜잭션 게시에 밀어넣기 구독을 동기화하려면</span><span class="sxs-lookup"><span data-stu-id="90a75-136">To start the Distribution Agent to synchronize a push subscription to a transactional publication</span></span>  
  
1.  <span data-ttu-id="90a75-137">배포자의 명령 프롬프트나 배치 파일에서 **distrib.exe**를 실행하고</span><span class="sxs-lookup"><span data-stu-id="90a75-137">From the command prompt or in a batch file at the Distributor, execute **distrib.exe**.</span></span> <span data-ttu-id="90a75-138">다음 명령줄 인수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="90a75-138">Specify the following command-line arguments:</span></span>  
  
    -   <span data-ttu-id="90a75-139">**-Publisher**</span><span class="sxs-lookup"><span data-stu-id="90a75-139">**-Publisher**</span></span>  
  
    -   <span data-ttu-id="90a75-140">**-PublisherDB**</span><span class="sxs-lookup"><span data-stu-id="90a75-140">**-PublisherDB**</span></span>  
  
    -   <span data-ttu-id="90a75-141">**-Distributor**</span><span class="sxs-lookup"><span data-stu-id="90a75-141">**-Distributor**</span></span>  
  
    -   <span data-ttu-id="90a75-142">**-Subscriber**</span><span class="sxs-lookup"><span data-stu-id="90a75-142">**-Subscriber**</span></span>  
  
    -   <span data-ttu-id="90a75-143">**-SubscriberDB**</span><span class="sxs-lookup"><span data-stu-id="90a75-143">**-SubscriberDB**</span></span>  
  
    -   <span data-ttu-id="90a75-144">**-SubscriptionType = 0**</span><span class="sxs-lookup"><span data-stu-id="90a75-144">**-SubscriptionType = 0**</span></span>  
  
     <span data-ttu-id="90a75-145">SQL Server 인증을 사용하는 경우 다음 인수도 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="90a75-145">If you are using SQL Server Authentication, you must also specify the following arguments:</span></span>  
  
    -   <span data-ttu-id="90a75-146">**-DistributorLogin**</span><span class="sxs-lookup"><span data-stu-id="90a75-146">**-DistributorLogin**</span></span>  
  
    -   <span data-ttu-id="90a75-147">**-DistributorPassword**</span><span class="sxs-lookup"><span data-stu-id="90a75-147">**-DistributorPassword**</span></span>  
  
    -   <span data-ttu-id="90a75-148">**-DistributorSecurityMode = 0**</span><span class="sxs-lookup"><span data-stu-id="90a75-148">**-DistributorSecurityMode = 0**</span></span>  
  
    -   <span data-ttu-id="90a75-149">**-PublisherLogin**</span><span class="sxs-lookup"><span data-stu-id="90a75-149">**-PublisherLogin**</span></span>  
  
    -   <span data-ttu-id="90a75-150">**-PublisherPassword**</span><span class="sxs-lookup"><span data-stu-id="90a75-150">**-PublisherPassword**</span></span>  
  
    -   <span data-ttu-id="90a75-151">**-PublisherSecurityMode = 0**</span><span class="sxs-lookup"><span data-stu-id="90a75-151">**-PublisherSecurityMode = 0**</span></span>  
  
    -   <span data-ttu-id="90a75-152">**-SubscriberLogin**</span><span class="sxs-lookup"><span data-stu-id="90a75-152">**-SubscriberLogin**</span></span>  
  
    -   <span data-ttu-id="90a75-153">**-SubscriberPassword**</span><span class="sxs-lookup"><span data-stu-id="90a75-153">**-SubscriberPassword**</span></span>  
  
    -   <span data-ttu-id="90a75-154">**-SubscriberSecurityMode = 0**</span><span class="sxs-lookup"><span data-stu-id="90a75-154">**-SubscriberSecurityMode = 0**</span></span>  
  
        > [!IMPORTANT]  
        >  [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
#### <a name="to-start-the-merge-agent-to-synchronize-a-push-subscription-to-a-merge-publication"></a><span data-ttu-id="90a75-155">병합 에이전트를 시작하여 병합 게시에 밀어넣기 구독을 동기화하려면</span><span class="sxs-lookup"><span data-stu-id="90a75-155">To start the Merge Agent to synchronize a push subscription to a merge publication</span></span>  
  
1.  <span data-ttu-id="90a75-156">배포자의 명령 프롬프트나 배치 파일에서 **replmerg.exe**를 실행하고</span><span class="sxs-lookup"><span data-stu-id="90a75-156">From the command prompt or in a batch file at the Distributor, execute **replmerg.exe**.</span></span> <span data-ttu-id="90a75-157">다음 명령줄 인수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="90a75-157">Specify the following command-line arguments:</span></span>  
  
    -   <span data-ttu-id="90a75-158">**-Publisher**</span><span class="sxs-lookup"><span data-stu-id="90a75-158">**-Publisher**</span></span>  
  
    -   <span data-ttu-id="90a75-159">**-PublisherDB**</span><span class="sxs-lookup"><span data-stu-id="90a75-159">**-PublisherDB**</span></span>  
  
    -   <span data-ttu-id="90a75-160">**-Publication**</span><span class="sxs-lookup"><span data-stu-id="90a75-160">**-Publication**</span></span>  
  
    -   <span data-ttu-id="90a75-161">**-Distributor**</span><span class="sxs-lookup"><span data-stu-id="90a75-161">**-Distributor**</span></span>  
  
    -   <span data-ttu-id="90a75-162">**-Subscriber**</span><span class="sxs-lookup"><span data-stu-id="90a75-162">**-Subscriber**</span></span>  
  
    -   <span data-ttu-id="90a75-163">**-SubscriberDB**</span><span class="sxs-lookup"><span data-stu-id="90a75-163">**-SubscriberDB**</span></span>  
  
    -   <span data-ttu-id="90a75-164">**-SubscriptionType = 0**</span><span class="sxs-lookup"><span data-stu-id="90a75-164">**-SubscriptionType = 0**</span></span>  
  
     <span data-ttu-id="90a75-165">SQL Server 인증을 사용하는 경우 다음 인수도 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="90a75-165">If you are using SQL Server Authentication, you must also specify the following arguments:</span></span>  
  
    -   <span data-ttu-id="90a75-166">**-DistributorLogin**</span><span class="sxs-lookup"><span data-stu-id="90a75-166">**-DistributorLogin**</span></span>  
  
    -   <span data-ttu-id="90a75-167">**-DistributorPassword**</span><span class="sxs-lookup"><span data-stu-id="90a75-167">**-DistributorPassword**</span></span>  
  
    -   <span data-ttu-id="90a75-168">**-DistributorSecurityMode = 0**</span><span class="sxs-lookup"><span data-stu-id="90a75-168">**-DistributorSecurityMode = 0**</span></span>  
  
    -   <span data-ttu-id="90a75-169">**-PublisherLogin**</span><span class="sxs-lookup"><span data-stu-id="90a75-169">**-PublisherLogin**</span></span>  
  
    -   <span data-ttu-id="90a75-170">**-PublisherPassword**</span><span class="sxs-lookup"><span data-stu-id="90a75-170">**-PublisherPassword**</span></span>  
  
    -   <span data-ttu-id="90a75-171">**-PublisherSecurityMode = 0**</span><span class="sxs-lookup"><span data-stu-id="90a75-171">**-PublisherSecurityMode = 0**</span></span>  
  
    -   <span data-ttu-id="90a75-172">**-SubscriberLogin**</span><span class="sxs-lookup"><span data-stu-id="90a75-172">**-SubscriberLogin**</span></span>  
  
    -   <span data-ttu-id="90a75-173">**-SubscriberPassword**</span><span class="sxs-lookup"><span data-stu-id="90a75-173">**-SubscriberPassword**</span></span>  
  
    -   <span data-ttu-id="90a75-174">**-SubscriberSecurityMode = 0**</span><span class="sxs-lookup"><span data-stu-id="90a75-174">**-SubscriberSecurityMode = 0**</span></span>  
  
        > [!IMPORTANT]  
        >  [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
###  <a name="examples-replication-agents"></a><a name="TsqlExample"></a> <span data-ttu-id="90a75-175">예(복제 에이전트)</span><span class="sxs-lookup"><span data-stu-id="90a75-175">Examples (Replication Agents)</span></span>  
 <span data-ttu-id="90a75-176">다음 예에서는 배포 에이전트를 시작하여 밀어넣기 구독을 동기화합니다.</span><span class="sxs-lookup"><span data-stu-id="90a75-176">The following example starts the Distribution Agent to synchronize a push subscription.</span></span>  
  
 
```
REM -- Declare the variables.  
SET Publisher=%instancename%  
SET Subscriber=%instancename%  
SET PublicationDB=AdventureWorks2012  
SET SubscriptionDB=AdventureWorks2012Replica   
SET Publication=AdvWorksProductsTran  
  
REM -- Start the Distribution Agent with four subscription streams.  
REM -- The following command must be supplied without line breaks.  
"C:\Program Files\Microsoft SQL Server\120\COM\DISTRIB.EXE" -Subscriber %Subscriber%   
-SubscriberDB %SubscriptionDB% -SubscriberSecurityMode 1 -Publication %Publication%   
-Publisher %Publisher% -PublisherDB %PublicationDB% -Distributor %Publisher%   
-DistributorSecurityMode 1 -Continuous -SubscriptionType 0 -SubscriptionStreams 4
```
  
 <span data-ttu-id="90a75-177">다음 예에서는 병합 에이전트를 시작하여 밀어넣기 구독을 동기화합니다.</span><span class="sxs-lookup"><span data-stu-id="90a75-177">The following example starts the Merge Agent to synchronize a push subscription.</span></span>  

```
REM -- Declare the variables.  
SET Publisher=%instancename%  
SET Subscriber=%instancename%  
SET PublicationDB=AdventureWorks2012  
SET SubscriptionDB=AdventureWorks2012Replica   
SET Publication=AdvWorksSalesOrdersMerge  
  
REM -- Start the Merge Agent.  
REM -- The following command must be supplied without line breaks.  
"C:\Program Files\Microsoft SQL Server\120\COM\REPLMERG.EXE"  -Publisher %Publisher%   
-Subscriber  %Subscriber%  -Distributor %Publisher% -PublisherDB  %PublicationDB%   
-SubscriberDB %SubscriptionDB% -Publication %Publication% -PublisherSecurityMode 1   
-OutputVerboseLevel 3  -Output -SubscriberSecurityMode 1  -SubscriptionType 0   
-DistributorSecurityMode 1
```
  
  
##  <a name="using-replication-management-objects-rmo"></a><a name="RMOProcedure"></a> <span data-ttu-id="90a75-178">RMO(복제 관리 개체) 사용</span><span class="sxs-lookup"><span data-stu-id="90a75-178">Using Replication Management Objects (RMO)</span></span>  
 <span data-ttu-id="90a75-179">RMO(복제 관리 개체) 및 관리 코드 액세스를 사용하여 복제 에이전트 기능에 프로그래밍 방식으로 밀어넣기 구독을 동기화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="90a75-179">You can synchronize push subscriptions programmatically by using Replication Management Objects (RMO) and managed code access to replication agent functionalities.</span></span> <span data-ttu-id="90a75-180">밀어넣기 구독을 동기화하는 데 사용하는 클래스는 구독이 속한 게시 유형에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="90a75-180">The classes that you use to synchronize a push subscription depend on the type of publication to which the subscription belongs.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="90a75-181">동기화가 애플리케이션에 영향을 미치지 않고 자율적으로 실행하도록 하려면 에이전트를 비동기적으로 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="90a75-181">If you want to start a synchronization that runs autonomously without affecting your application, start the agent asynchronously.</span></span> <span data-ttu-id="90a75-182">그러나 진행률 표시줄을 표시하기 위해 동기화 프로세스 동안 동기화 결과를 모니터링하고 에이전트에서 콜백을 받으려면 에이전트를 동기적으로 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="90a75-182">However, if you want to monitor the outcome of the synchronization and receive callbacks from the agent during the synchronization process (for example, if you want to display a progress bar), you should start the agent synchronously.</span></span> <span data-ttu-id="90a75-183">For [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssExpressEd2005](../../includes/ssexpressed2005-md.md)] 구독자의 경우 에이전트를 동기적으로 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="90a75-183">For [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssExpressEd2005](../../includes/ssexpressed2005-md.md)] Subscribers, you must start the agent synchronously.</span></span>  
  
#### <a name="to-synchronize-a-push-subscription-to-a-snapshot-or-transactional-publication"></a><span data-ttu-id="90a75-184">스냅샷 또는 트랜잭션 게시에 밀어넣기 구독을 동기화하려면</span><span class="sxs-lookup"><span data-stu-id="90a75-184">To synchronize a push subscription to a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="90a75-185"><xref:Microsoft.SqlServer.Management.Common.ServerConnection> 클래스를 사용하여 배포자 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="90a75-185">Create a connection to the Distributor by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="90a75-186"><xref:Microsoft.SqlServer.Replication.TransSubscription> 클래스의 인스턴스를 만들고 다음 속성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="90a75-186">Create an instance of the <xref:Microsoft.SqlServer.Replication.TransSubscription> class and set the following properties:</span></span>  
  
    -   <span data-ttu-id="90a75-187"><xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A>에 대한 게시 데이터베이스 이름</span><span class="sxs-lookup"><span data-stu-id="90a75-187">The publication database name for <xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A>.</span></span>  
  
    -   <span data-ttu-id="90a75-188"><xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>에 대해 구독이 속한 게시 이름</span><span class="sxs-lookup"><span data-stu-id="90a75-188">The name of the publication to which the subscription belongs for <xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>.</span></span>  
  
    -   <span data-ttu-id="90a75-189"><xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A>에 대한 구독 데이터베이스 이름</span><span class="sxs-lookup"><span data-stu-id="90a75-189">The name of the subscription database for <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A>.</span></span>  
  
    -   <span data-ttu-id="90a75-190"><xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>에 대한 구독자 이름</span><span class="sxs-lookup"><span data-stu-id="90a75-190">The name of the Subscriber for <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>.</span></span>  
  
    -   <span data-ttu-id="90a75-191"><xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>에 대해 1단계에서 만든 연결</span><span class="sxs-lookup"><span data-stu-id="90a75-191">The connection created in step 1 for <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.</span></span>  
  
3.  <span data-ttu-id="90a75-192"><xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> 메서드를 호출하여 나머지 구독 속성을 얻습니다.</span><span class="sxs-lookup"><span data-stu-id="90a75-192">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method to get the remaining subscription properties.</span></span> <span data-ttu-id="90a75-193">이 메서드가 `false`를 반환하는 경우 구독이 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="90a75-193">If this method returns `false`, verify that the subscription exists.</span></span>  
  
4.  <span data-ttu-id="90a75-194">다음 방법 중 하나로 배포자에서 배포 에이전트를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="90a75-194">Start the Distribution Agent at the Distributor in one of the following ways:</span></span>  
  
    -   <span data-ttu-id="90a75-195">2단계에서 만든 <xref:Microsoft.SqlServer.Replication.TransSubscription.SynchronizeWithJob%2A> 의 인스턴스에서 <xref:Microsoft.SqlServer.Replication.TransSubscription> 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="90a75-195">Call the <xref:Microsoft.SqlServer.Replication.TransSubscription.SynchronizeWithJob%2A> method on the instance of <xref:Microsoft.SqlServer.Replication.TransSubscription> from step 2.</span></span> <span data-ttu-id="90a75-196">이 메서드는 배포 에이전트를 비동기적으로 시작하고 에이전트 작업이 실행되는 동안 애플리케이션에 대한 반환을 즉시 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="90a75-196">This method starts the Distribution Agent asynchronously, and control immediately returns to your application while the agent job is running.</span></span> <span data-ttu-id="90a75-197"><xref:Microsoft.SqlServer.Replication.Subscription.CreateSyncAgentByDefault%2A>에 `false` 값을 사용하여 구독을 만든 경우 이 메서드를 호출할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="90a75-197">You cannot call this method if the subscription was created with a value of `false` for <xref:Microsoft.SqlServer.Replication.Subscription.CreateSyncAgentByDefault%2A>.</span></span>  
  
    -   <span data-ttu-id="90a75-198"><xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent> 속성에서 <xref:Microsoft.SqlServer.Replication.TransSubscription.SynchronizationAgent%2A> 클래스의 인스턴스를 가져오고 <xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent.Synchronize%2A> 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="90a75-198">Obtain an instance of the <xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent> class from the <xref:Microsoft.SqlServer.Replication.TransSubscription.SynchronizationAgent%2A> property, and call the <xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent.Synchronize%2A> method.</span></span> <span data-ttu-id="90a75-199">이 메서드는 에이전트를 동기적으로 시작하고 실행 중인 에이전트 작업에 대한 제어는 그대로 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="90a75-199">This method starts the agent synchronously, and control remains with the running agent job.</span></span> <span data-ttu-id="90a75-200">동기화 실행 중에는 에이전트를 실행하면서 <xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent.Status> 이벤트를 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="90a75-200">During synchronous execution you can handle the <xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent.Status> event while the agent is running.</span></span>  
  
#### <a name="to-synchronize-a-push-subscription-to-a-merge-publication"></a><span data-ttu-id="90a75-201">병합 게시에 밀어넣기 구독을 동기화하려면</span><span class="sxs-lookup"><span data-stu-id="90a75-201">To synchronize a push subscription to a merge publication</span></span>  
  
1.  <span data-ttu-id="90a75-202"><xref:Microsoft.SqlServer.Management.Common.ServerConnection> 클래스를 사용하여 배포자 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="90a75-202">Create a connection to the Distributor by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="90a75-203"><xref:Microsoft.SqlServer.Replication.MergeSubscription> 클래스의 인스턴스를 만들고 다음 속성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="90a75-203">Create an instance of the <xref:Microsoft.SqlServer.Replication.MergeSubscription> class, and set the following properties:</span></span>  
  
    -   <span data-ttu-id="90a75-204"><xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A>에 대한 게시 데이터베이스 이름</span><span class="sxs-lookup"><span data-stu-id="90a75-204">The publication database name for <xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A>.</span></span>  
  
    -   <span data-ttu-id="90a75-205"><xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>에 대해 구독이 속한 게시 이름</span><span class="sxs-lookup"><span data-stu-id="90a75-205">The name of the publication to which the subscription belongs for <xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>.</span></span>  
  
    -   <span data-ttu-id="90a75-206"><xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A>에 대한 구독 데이터베이스 이름</span><span class="sxs-lookup"><span data-stu-id="90a75-206">The name of the subscription database for <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A>.</span></span>  
  
    -   <span data-ttu-id="90a75-207"><xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>에 대한 구독자 이름</span><span class="sxs-lookup"><span data-stu-id="90a75-207">The name of the Subscriber for <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>.</span></span>  
  
    -   <span data-ttu-id="90a75-208"><xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>에 대해 1단계에서 만든 연결</span><span class="sxs-lookup"><span data-stu-id="90a75-208">The connection created in step 1 for <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.</span></span>  
  
3.  <span data-ttu-id="90a75-209"><xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> 메서드를 호출하여 나머지 구독 속성을 얻습니다.</span><span class="sxs-lookup"><span data-stu-id="90a75-209">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method to get the remaining subscription properties.</span></span> <span data-ttu-id="90a75-210">이 메서드가 `false`를 반환하는 경우 구독이 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="90a75-210">If this method returns `false`, verify that the subscription exists.</span></span>  
  
4.  <span data-ttu-id="90a75-211">다음 방법 중 하나로 배포자에서 병합 에이전트를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="90a75-211">Start the Merge Agent at the Distributor in one of the following ways:</span></span>  
  
    -   <span data-ttu-id="90a75-212">2단계에서 만든 <xref:Microsoft.SqlServer.Replication.MergeSubscription.SynchronizeWithJob%2A> 의 인스턴스에서 <xref:Microsoft.SqlServer.Replication.MergeSubscription> 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="90a75-212">Call the <xref:Microsoft.SqlServer.Replication.MergeSubscription.SynchronizeWithJob%2A> method on the instance of <xref:Microsoft.SqlServer.Replication.MergeSubscription> from step 2.</span></span> <span data-ttu-id="90a75-213">이 메서드는 병합 에이전트를 비동기적으로 시작하고 에이전트 작업이 실행되는 동안 애플리케이션에 대한 반환을 즉시 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="90a75-213">This method starts the Merge Agent asynchronously, and control immediately returns to your application while the agent job is running.</span></span> <span data-ttu-id="90a75-214"><xref:Microsoft.SqlServer.Replication.Subscription.CreateSyncAgentByDefault%2A>에 `false` 값을 사용하여 구독을 만든 경우 이 메서드를 호출할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="90a75-214">You cannot call this method if the subscription was created with a value of `false` for <xref:Microsoft.SqlServer.Replication.Subscription.CreateSyncAgentByDefault%2A>.</span></span>  
  
    -   <span data-ttu-id="90a75-215"><xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent> 속성에서 <xref:Microsoft.SqlServer.Replication.MergeSubscription.SynchronizationAgent%2A> 클래스의 인스턴스를 가져오고 <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.Synchronize%2A> 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="90a75-215">Obtain an instance of the <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent> class from the <xref:Microsoft.SqlServer.Replication.MergeSubscription.SynchronizationAgent%2A> property, and call the <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.Synchronize%2A> method.</span></span> <span data-ttu-id="90a75-216">이 메서드는 병합 에이전트를 동기적으로 시작하고 실행 중인 에이전트 작업에 대한 제어는 그대로 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="90a75-216">This method starts the Merge Agent synchronously, and control remains with the running agent job.</span></span> <span data-ttu-id="90a75-217">동기화 실행 중에는 에이전트를 실행하면서 <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.Status> 이벤트를 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="90a75-217">During synchronous execution, you can handle the <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.Status> event while the agent is running.</span></span>  
  
###  <a name="examples-rmo"></a><a name="PShellExample"></a> <span data-ttu-id="90a75-218">예(RMO)</span><span class="sxs-lookup"><span data-stu-id="90a75-218">Examples (RMO)</span></span>  
 <span data-ttu-id="90a75-219">다음은 트랜잭션 게시에 밀어넣기 구독을 동기화하는 예로, 에이전트 작업을 사용하여 에이전트를 비동기적으로 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="90a75-219">This example synchronizes a push subscription to a transactional publication, where the agent is started asynchronously using the agent job.</span></span>  
  
 [!code-csharp[HowTo#rmo_SyncTranPushSub_WithJob](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_synctranpushsub_withjob)]  
  
 [!code-vb[HowTo#rmo_vb_SyncTranPushSub_WithJob](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_synctranpushsub_withjob)]  
  
 <span data-ttu-id="90a75-220">다음은 트랜잭션 게시에 밀어넣기 구독을 동기화하는 예로, 에이전트를 동기적으로 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="90a75-220">This example synchronizes a push subscription to a transactional publication, where the agent is started synchronously.</span></span>  
  
 [!code-csharp[HowTo#rmo_SyncTranPushSub](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_synctranpushsub)]  
  
 [!code-vb[HowTo#rmo_vb_SyncTranPushSub](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_synctranpushsub)]  
  
 <span data-ttu-id="90a75-221">다음은 병합 게시에 밀어넣기 구독을 동기화하는 예로, 에이전트 작업을 사용하여 에이전트를 비동기적으로 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="90a75-221">This example synchronizes a push subscription to a merge publication, where the agent is started asynchronously using the agent job.</span></span>  
  
 [!code-csharp[HowTo#rmo_SyncMergePushSub_WithJob](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_syncmergepushsub_withjob)]  
  
 [!code-vb[HowTo#rmo_vb_SyncMergePushSub_WithJob](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_syncmergepushsub_withjob)]  
  
 <span data-ttu-id="90a75-222">다음은 병합 게시에 밀어넣기 구독을 동기화하는 예로, 에이전트를 동기적으로 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="90a75-222">This example synchronizes a push subscription to a merge publication, where the agent is started synchronously.</span></span>  
  
 [!code-csharp[HowTo#rmo_SyncMergePushSub](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_syncmergepushsub)]  
  
 [!code-vb[HowTo#rmo_vb_SyncMergePushSub](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_syncmergepushsub)]  
  
## <a name="see-also"></a><span data-ttu-id="90a75-223">참고 항목</span><span class="sxs-lookup"><span data-stu-id="90a75-223">See Also</span></span>  
 <span data-ttu-id="90a75-224">[Replication Management Objects Concepts](concepts/replication-management-objects-concepts.md) </span><span class="sxs-lookup"><span data-stu-id="90a75-224">[Replication Management Objects Concepts](concepts/replication-management-objects-concepts.md) </span></span>  
 <span data-ttu-id="90a75-225">[데이터 동기화](synchronize-data.md) </span><span class="sxs-lookup"><span data-stu-id="90a75-225">[Synchronize Data](synchronize-data.md) </span></span>  
 [<span data-ttu-id="90a75-226">복제 보안을 위한 최선의 구현 방법</span><span class="sxs-lookup"><span data-stu-id="90a75-226">Replication Security Best Practices</span></span>](security/replication-security-best-practices.md)  
  
  
