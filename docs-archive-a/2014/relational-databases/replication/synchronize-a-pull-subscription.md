---
title: 끌어오기 구독 동기화 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- pull subscriptions [SQL Server replication], synchronizing
- synchronization [SQL Server replication], pull subscriptions
- subscriptions [SQL Server replication], pull
ms.assetid: 3ca24b23-fdc3-408e-8208-a2ace48fc8e3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 826622cd17862c0535e60c01baab756af2b2996b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651643"
---
# <a name="synchronize-a-pull-subscription"></a><span data-ttu-id="2b084-102">끌어오기 구독 동기화</span><span class="sxs-lookup"><span data-stu-id="2b084-102">Synchronize a Pull Subscription</span></span>
  <span data-ttu-id="2b084-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] , [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]복제 에이전트 [또는 RMO(복제 관리 개체)를 사용하여](agents/replication-agents-overview.md)에서 끌어오기 구독을 동기화하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="2b084-103">This topic describes how to synchronize a pull subscription in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [replication agents](agents/replication-agents-overview.md), or Replication Management Objects (RMO).</span></span>  
  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="2b084-104">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="2b084-104">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="2b084-105">구독은 배포 에이전트(스냅샷 및 트랜잭션 복제의 경우) 또는 병합 에이전트(병합 복제의 경우)에 의해 동기화됩니다.</span><span class="sxs-lookup"><span data-stu-id="2b084-105">Subscriptions are synchronized by the Distribution Agent (for snapshot and transactional replication) or the Merge Agent (for merge replication).</span></span> <span data-ttu-id="2b084-106">에이전트는 지속적으로 실행하거나 수요에 따라 실행하거나 일정에 따라 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b084-106">Agents can run continuously, run on demand, or run on a schedule.</span></span> <span data-ttu-id="2b084-107">동기화 일정을 설정하는 방법은 [동기화 일정 지정](specify-synchronization-schedules.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2b084-107">For more information about specifying synchronization schedules, see [Specify Synchronization Schedules](specify-synchronization-schedules.md).</span></span>  
  
 <span data-ttu-id="2b084-108">**의** 로컬 구독 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]폴더에서 요청 시 구독을 동기화합니다.</span><span class="sxs-lookup"><span data-stu-id="2b084-108">Synchronize a subscription on demand from the **Local Subscriptions** folder in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
#### <a name="to-synchronize-a-pull-subscription-on-demand-in-management-studio"></a><span data-ttu-id="2b084-109">Management Studio에서 요청 시 끌어오기 구독을 동기화하려면</span><span class="sxs-lookup"><span data-stu-id="2b084-109">To synchronize a pull subscription on demand in Management Studio</span></span>  
  
1.  <span data-ttu-id="2b084-110">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]에서 구독자에 연결한 다음 해당 서버 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="2b084-110">Connect to the Subscriber in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="2b084-111">**복제** 폴더를 확장한 다음 **로컬 구독** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="2b084-111">Expand the **Replication** folder, and then expand the **Local Subscriptions** folder.</span></span>  
  
3.  <span data-ttu-id="2b084-112">동기화할 구독을 마우스 오른쪽 단추로 클릭한 다음 **동기화 상태 보기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2b084-112">Right-click the subscription you want to synchronize, and then click **View Synchronization Status**.</span></span>  
  
4.  <span data-ttu-id="2b084-113">**동기화 상태 보기 - \<Subscriber>:\<SubscriptionDatabase>** 대화 상자에서 **시작**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2b084-113">In the **View Synchronization Status - \<Subscriber>:\<SubscriptionDatabase>** dialog box, click **Start**.</span></span> <span data-ttu-id="2b084-114">동기화가 완료되면 **동기화 완료** 라는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="2b084-114">When synchronization is complete, the message **Synchronization completed** is displayed.</span></span>  
  
5.  <span data-ttu-id="2b084-115">**닫기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2b084-115">Click **Close**.</span></span>  
  
##  <a name="replication-agents"></a><a name="ReplProg"></a> <span data-ttu-id="2b084-116">Replication Agents</span><span class="sxs-lookup"><span data-stu-id="2b084-116">Replication Agents</span></span>  
 <span data-ttu-id="2b084-117">끌어오기 구독은 명령 프롬프트에서 적합한 복제 에이전트 실행 파일을 호출하여 프로그래밍 방식으로 요청 시 동기화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b084-117">Pull subscriptions can be synchronized programmatically and on-demand by invoking the appropriate replication agent executable file from the command prompt.</span></span> <span data-ttu-id="2b084-118">호출한 복제 에이전트 실행 파일은 끌어오기 구독이 속한 게시 유형에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="2b084-118">The replication agent executable file that is invoked will depend on the type of publication to which the pull subscription belongs.</span></span> <span data-ttu-id="2b084-119">자세한 내용은 [Replication Agents](agents/replication-agents-overview.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2b084-119">For more information, see [Replication Agents](agents/replication-agents-overview.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2b084-120">복제 에이전트는 명령 프롬프트에서 에이전트를 시작한 사용자의 Windows 인증 자격 증명을 사용하여 로컬 서버에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="2b084-120">Replication agents connect to the local server using the Windows Authentication credentials of the user who started the agent from the command prompt.</span></span> <span data-ttu-id="2b084-121">이러한 자격 증명은 Windows 통합 인증을 사용하여 원격 서버에 연결할 때도 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="2b084-121">These Windows credentials are also used when connecting to remote servers using Windows Integrated Authentication.</span></span>  
  
#### <a name="to-start-the-distribution-agent-from-the-command-prompt-or-from-a-batch-file"></a><span data-ttu-id="2b084-122">명령 프롬프트 또는 배치 파일에서 배포 에이전트를 시작하려면</span><span class="sxs-lookup"><span data-stu-id="2b084-122">To start the distribution agent from the command prompt or from a batch file</span></span>  
  
1.  <span data-ttu-id="2b084-123">_명령 프롬프트 또는 배치 파일에서 [distrib.exe](agents/replication-distribution-agent.md) 를 실행하여 **복제 배포 에이전트**를 시작하고 다음 명령줄 인수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2b084-123">From the command prompt or in a batch file, start the [Replication Distribution Agent](agents/replication-distribution-agent.md) by running **distrib.exe**, specifying the following command-line arguments:</span></span>  
  
    -   <span data-ttu-id="2b084-124">**-Publisher**</span><span class="sxs-lookup"><span data-stu-id="2b084-124">**-Publisher**</span></span>  
  
    -   <span data-ttu-id="2b084-125">**-PublisherDB**</span><span class="sxs-lookup"><span data-stu-id="2b084-125">**-PublisherDB**</span></span>  
  
    -   <span data-ttu-id="2b084-126">**-Distributor**</span><span class="sxs-lookup"><span data-stu-id="2b084-126">**-Distributor**</span></span>  
  
    -   <span data-ttu-id="2b084-127">**-DistributorSecurityMode** = **1**</span><span class="sxs-lookup"><span data-stu-id="2b084-127">**-DistributorSecurityMode** = **1**</span></span>  
  
    -   <span data-ttu-id="2b084-128">**-Subscriber**</span><span class="sxs-lookup"><span data-stu-id="2b084-128">**-Subscriber**</span></span>  
  
    -   <span data-ttu-id="2b084-129">**-SubscriberDB**</span><span class="sxs-lookup"><span data-stu-id="2b084-129">**-SubscriberDB**</span></span>  
  
    -   <span data-ttu-id="2b084-130">**-SubscriberSecurityMode** = **1**</span><span class="sxs-lookup"><span data-stu-id="2b084-130">**-SubscriberSecurityMode** = **1**</span></span>  
  
    -   <span data-ttu-id="2b084-131">**-SubscriptionType** = **1**</span><span class="sxs-lookup"><span data-stu-id="2b084-131">**-SubscriptionType** = **1**</span></span>  
  
     <span data-ttu-id="2b084-132">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인증을 사용하는 경우 다음 인수도 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2b084-132">If you are using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication, you must also specify the following arguments:</span></span>  
  
    -   <span data-ttu-id="2b084-133">**-DistributorLogin**</span><span class="sxs-lookup"><span data-stu-id="2b084-133">**-DistributorLogin**</span></span>  
  
    -   <span data-ttu-id="2b084-134">**-DistributorPassword**</span><span class="sxs-lookup"><span data-stu-id="2b084-134">**-DistributorPassword**</span></span>  
  
    -   <span data-ttu-id="2b084-135">**-DistributorSecurityMode** = **0**</span><span class="sxs-lookup"><span data-stu-id="2b084-135">**-DistributorSecurityMode** = **0**</span></span>  
  
    -   <span data-ttu-id="2b084-136">**-PublisherLogin**</span><span class="sxs-lookup"><span data-stu-id="2b084-136">**-PublisherLogin**</span></span>  
  
    -   <span data-ttu-id="2b084-137">**-PublisherPassword**</span><span class="sxs-lookup"><span data-stu-id="2b084-137">**-PublisherPassword**</span></span>  
  
    -   <span data-ttu-id="2b084-138">**-PublisherSecurityMode** =  **\@publisher_security_mode**</span><span class="sxs-lookup"><span data-stu-id="2b084-138">**-PublisherSecurityMode** = **0**</span></span>  
  
    -   <span data-ttu-id="2b084-139">**-SubscriberLogin**</span><span class="sxs-lookup"><span data-stu-id="2b084-139">**-SubscriberLogin**</span></span>  
  
    -   <span data-ttu-id="2b084-140">**-SubscriberPassword**</span><span class="sxs-lookup"><span data-stu-id="2b084-140">**-SubscriberPassword**</span></span>  
  
    -   <span data-ttu-id="2b084-141">**-SubscriberSecurityMode** = **0**</span><span class="sxs-lookup"><span data-stu-id="2b084-141">**-SubscriberSecurityMode** = **0**</span></span>  
  
#### <a name="to-start-the-merge-agent-from-the-command-prompt-or-from-a-batch-file"></a><span data-ttu-id="2b084-142">명령 프롬프트 또는 배치 파일에서 병합 에이전트를 시작하려면</span><span class="sxs-lookup"><span data-stu-id="2b084-142">To start the merge agent from the command prompt or from a batch file</span></span>  
  
1.  <span data-ttu-id="2b084-143">명령 프롬프트 또는 배치 파일에서 [replmerg.exe](agents/replication-merge-agent.md) 를 실행하여 **복제 병합 에이전트**를 시작하고 다음 명령줄 인수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2b084-143">From the command prompt or in a batch file, start the [Replication Merge Agent](agents/replication-merge-agent.md) by running **replmerg.exe**, specifying the following command-line arguments:</span></span>  
  
    -   <span data-ttu-id="2b084-144">**-Publisher**</span><span class="sxs-lookup"><span data-stu-id="2b084-144">**-Publisher**</span></span>  
  
    -   <span data-ttu-id="2b084-145">**-PublisherDB**</span><span class="sxs-lookup"><span data-stu-id="2b084-145">**-PublisherDB**</span></span>  
  
    -   <span data-ttu-id="2b084-146">**-PublisherSecurityMode** = **1**</span><span class="sxs-lookup"><span data-stu-id="2b084-146">**-PublisherSecurityMode** = **1**</span></span>  
  
    -   <span data-ttu-id="2b084-147">**-Publication**</span><span class="sxs-lookup"><span data-stu-id="2b084-147">**-Publication**</span></span>  
  
    -   <span data-ttu-id="2b084-148">**-Distributor**</span><span class="sxs-lookup"><span data-stu-id="2b084-148">**-Distributor**</span></span>  
  
    -   <span data-ttu-id="2b084-149">**-DistributorSecurityMode** = **1**</span><span class="sxs-lookup"><span data-stu-id="2b084-149">**-DistributorSecurityMode** = **1**</span></span>  
  
    -   <span data-ttu-id="2b084-150">**-Subscriber**</span><span class="sxs-lookup"><span data-stu-id="2b084-150">**-Subscriber**</span></span>  
  
    -   <span data-ttu-id="2b084-151">**-SubscriberSecurityMode** = **1**</span><span class="sxs-lookup"><span data-stu-id="2b084-151">**-SubscriberSecurityMode** = **1**</span></span>  
  
    -   <span data-ttu-id="2b084-152">**-SubscriberDB**</span><span class="sxs-lookup"><span data-stu-id="2b084-152">**-SubscriberDB**</span></span>  
  
    -   <span data-ttu-id="2b084-153">**-SubscriptionType** = **1**</span><span class="sxs-lookup"><span data-stu-id="2b084-153">**-SubscriptionType** = **1**</span></span>  
  
     <span data-ttu-id="2b084-154">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인증을 사용하는 경우 다음 인수도 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2b084-154">If you are using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication, you must also specify the following arguments:</span></span>  
  
    -   <span data-ttu-id="2b084-155">**-DistributorLogin**</span><span class="sxs-lookup"><span data-stu-id="2b084-155">**-DistributorLogin**</span></span>  
  
    -   <span data-ttu-id="2b084-156">**-DistributorPassword**</span><span class="sxs-lookup"><span data-stu-id="2b084-156">**-DistributorPassword**</span></span>  
  
    -   <span data-ttu-id="2b084-157">**-DistributorSecurityMode** = **0**</span><span class="sxs-lookup"><span data-stu-id="2b084-157">**-DistributorSecurityMode** = **0**</span></span>  
  
    -   <span data-ttu-id="2b084-158">**-PublisherLogin**</span><span class="sxs-lookup"><span data-stu-id="2b084-158">**-PublisherLogin**</span></span>  
  
    -   <span data-ttu-id="2b084-159">**-PublisherPassword**</span><span class="sxs-lookup"><span data-stu-id="2b084-159">**-PublisherPassword**</span></span>  
  
    -   <span data-ttu-id="2b084-160">**-PublisherSecurityMode** =  **\@publisher_security_mode**</span><span class="sxs-lookup"><span data-stu-id="2b084-160">**-PublisherSecurityMode** = **0**</span></span>  
  
    -   <span data-ttu-id="2b084-161">**-SubscriberLogin**</span><span class="sxs-lookup"><span data-stu-id="2b084-161">**-SubscriberLogin**</span></span>  
  
    -   <span data-ttu-id="2b084-162">**-SubscriberPassword**</span><span class="sxs-lookup"><span data-stu-id="2b084-162">**-SubscriberPassword**</span></span>  
  
    -   <span data-ttu-id="2b084-163">**-SubscriberSecurityMode** = **0**</span><span class="sxs-lookup"><span data-stu-id="2b084-163">**-SubscriberSecurityMode** = **0**</span></span>  
  
###  <a name="examples-replication-agents"></a><a name="TsqlExample"></a> <span data-ttu-id="2b084-164">예(복제 에이전트)</span><span class="sxs-lookup"><span data-stu-id="2b084-164">Examples (Replication Agents)</span></span>  
 <span data-ttu-id="2b084-165">다음 예에서는 배포 에이전트를 시작하여 끌어오기 구독을 동기화합니다.</span><span class="sxs-lookup"><span data-stu-id="2b084-165">The following example starts the Distribution Agent to synchronize a pull subscription.</span></span> <span data-ttu-id="2b084-166">모든 연결은 Windows 인증을 사용하여 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2b084-166">All connections are made using Windows Authentication.</span></span>  
  
 [!code-sql[HowTo#bat_synctranpullsub_10](../../snippets/tsql/SQL15/replication/howto/tsql/synctranpullsub_10.bat)]  
  
 <span data-ttu-id="2b084-167">다음 예에서는 병합 에이전트를 시작하여 끌어오기 구독을 동기화합니다.</span><span class="sxs-lookup"><span data-stu-id="2b084-167">The following example starts the Merge Agent to synchronize a pull subscription.</span></span> <span data-ttu-id="2b084-168">모든 연결은 Windows 인증을 사용하여 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2b084-168">All connections are made using Windows Authentication.</span></span>  
  
 [!code-sql[HowTo#bat_syncmergepullsub_10](../../snippets/tsql/SQL15/replication/howto/tsql/syncmergepullsub_10.bat)]  
  
##  <a name="using-replication-management-objects-rmo"></a><a name="RMOProcedure"></a> <span data-ttu-id="2b084-169">RMO(복제 관리 개체) 사용</span><span class="sxs-lookup"><span data-stu-id="2b084-169">Using Replication Management Objects (RMO)</span></span>  
 <span data-ttu-id="2b084-170">RMO(복제 관리 개체) 및 관리 코드 액세스를 사용하여 복제 에이전트 기능에 프로그래밍 방식으로 끌어오기 구독을 동기화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b084-170">You can synchronize pull subscriptions programmatically by using Replication Management Objects (RMO) and managed code access to replication agent functionalities.</span></span> <span data-ttu-id="2b084-171">끌어오기 구독을 동기화하는 데 사용하는 클래스는 구독이 속한 게시 유형에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="2b084-171">The classes you use to synchronize a pull subscription depend on the type of publication to which the subscription belongs.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2b084-172">동기화가 애플리케이션에 영향을 미치지 않고 자율적으로 실행하도록 하려면 에이전트를 비동기적으로 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="2b084-172">If you want to start a synchronization that runs autonomously without affecting your application, start the agent asynchronously.</span></span> <span data-ttu-id="2b084-173">그러나 진행률 표시줄을 표기하기 위해 동기화 프로세스 동안 동기화 결과를 모니터링하고 에이전트에서 콜백을 받으려면 에이전트를 동기적으로 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2b084-173">However, if you want to monitor the outcome of the synchronization and receive callbacks from the agent during the synchronization process (for example, to display a progress bar), you should start the agent synchronously.</span></span> <span data-ttu-id="2b084-174">For [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssExpressEd2005](../../includes/ssexpressed2005-md.md)] 구독자의 경우 에이전트를 동기적으로 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2b084-174">For [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssExpressEd2005](../../includes/ssexpressed2005-md.md)] Subscribers, you must start the agent synchronously.</span></span>  
  
#### <a name="to-synchronize-a-pull-subscription-to-a-snapshot-or-transactional-publication"></a><span data-ttu-id="2b084-175">스냅샷 또는 트랜잭션 게시에 끌어오기 구독을 동기화하려면</span><span class="sxs-lookup"><span data-stu-id="2b084-175">To synchronize a pull subscription to a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="2b084-176"><xref:Microsoft.SqlServer.Management.Common.ServerConnection> 클래스를 사용하여 구독자 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2b084-176">Create a connection to the Subscriber by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="2b084-177"><xref:Microsoft.SqlServer.Replication.TransPullSubscription> 클래스의 인스턴스를 만들고 다음 속성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="2b084-177">Create an instance of the <xref:Microsoft.SqlServer.Replication.TransPullSubscription> class, and set the following properties:</span></span>  
  
    -   <span data-ttu-id="2b084-178"><xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>에 대한 구독 데이터베이스 이름</span><span class="sxs-lookup"><span data-stu-id="2b084-178">The subscription database name for <xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>.</span></span>  
  
    -   <span data-ttu-id="2b084-179"><xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>에 대해 구독이 속한 게시 이름</span><span class="sxs-lookup"><span data-stu-id="2b084-179">The name of the publication to which the subscription belongs for <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>.</span></span>  
  
    -   <span data-ttu-id="2b084-180"><xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A>에 대한 게시 데이터베이스의 이름</span><span class="sxs-lookup"><span data-stu-id="2b084-180">The name of the publication database for <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A>.</span></span>  
  
    -   <span data-ttu-id="2b084-181"><xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>에 대한 게시자 이름</span><span class="sxs-lookup"><span data-stu-id="2b084-181">The name of the Publisher for <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>.</span></span>  
  
    -   <span data-ttu-id="2b084-182"><xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>에 대해 1단계에서 만든 연결</span><span class="sxs-lookup"><span data-stu-id="2b084-182">The connection created in step 1 for <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.</span></span>  
  
3.  <span data-ttu-id="2b084-183"><xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> 메서드를 호출하여 나머지 구독 속성을 얻습니다.</span><span class="sxs-lookup"><span data-stu-id="2b084-183">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method to get the remaining subscription properties.</span></span> <span data-ttu-id="2b084-184">이 메서드가 `false`를 반환하는 경우 구독이 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="2b084-184">If this method returns `false`, verify that the subscription exists.</span></span>  
  
4.  <span data-ttu-id="2b084-185">다음 방법 중 하나로 구독자에서 배포 에이전트를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="2b084-185">Start the Distribution Agent at the Subscriber in one of the following ways:</span></span>  
  
    -   <span data-ttu-id="2b084-186">2단계에서 만든 <xref:Microsoft.SqlServer.Replication.TransPullSubscription.SynchronizeWithJob%2A> 의 인스턴스에서 <xref:Microsoft.SqlServer.Replication.TransPullSubscription> 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="2b084-186">Call the <xref:Microsoft.SqlServer.Replication.TransPullSubscription.SynchronizeWithJob%2A> method on the instance of <xref:Microsoft.SqlServer.Replication.TransPullSubscription> from step 2.</span></span> <span data-ttu-id="2b084-187">이 메서드는 배포 에이전트를 비동기적으로 시작하고 에이전트 작업이 실행되는 동안 애플리케이션에 대한 반환을 즉시 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="2b084-187">This method starts the Distribution Agent asynchronously, and control immediately returns to your application while the agent job is running.</span></span> <span data-ttu-id="2b084-188">[!INCLUDE[ssExpressEd2005](../../includes/ssexpressed2005-md.md)] 구독자인 경우 또는 <xref:Microsoft.SqlServer.Replication.PullSubscription.CreateSyncAgentByDefault%2A>에 `false` 값(기본값)을 사용하여 구독을 만든 경우 이 메서드를 호출할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2b084-188">You cannot call this method for [!INCLUDE[ssExpressEd2005](../../includes/ssexpressed2005-md.md)] Subscribers or if the subscription was created with a value of `false` for <xref:Microsoft.SqlServer.Replication.PullSubscription.CreateSyncAgentByDefault%2A> (the default).</span></span>  
  
    -   <span data-ttu-id="2b084-189"><xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent> 속성에서 <xref:Microsoft.SqlServer.Replication.TransPullSubscription.SynchronizationAgent%2A> 클래스의 인스턴스를 가져오고 <xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent.Synchronize%2A> 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="2b084-189">Get an instance of the <xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent> class from the <xref:Microsoft.SqlServer.Replication.TransPullSubscription.SynchronizationAgent%2A> property, and call the <xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent.Synchronize%2A> method.</span></span> <span data-ttu-id="2b084-190">이 메서드는 에이전트를 동기적으로 시작하고 실행 중인 에이전트 작업에 대한 제어는 그대로 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="2b084-190">This method starts the agent synchronously, and control remains with the running agent job.</span></span> <span data-ttu-id="2b084-191">동기화 실행 중에는 에이전트를 실행하면서 <xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent.Status> 이벤트를 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b084-191">During synchronous execution, you can handle the <xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent.Status> event while the agent is running.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="2b084-192">`false`끌어오기 구독을 만들 때에 값 (기본값)을 지정한 경우에는 <xref:Microsoft.SqlServer.Replication.PullSubscription.CreateSyncAgentByDefault%2A> , 및도 지정 해야 합니다 <xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent.Distributor%2A> <xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent.DistributorSecurityMode%2A> <xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent.DistributorLogin%2A> <xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent.DistributorPassword%2A> . 구독에 대 한 에이전트 작업 관련 메타 데이터는 [MSsubscription_properties](/sql/relational-databases/system-tables/mssubscription-properties-transact-sql)에서 사용할 수 없기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="2b084-192">If you specified a value of `false` for <xref:Microsoft.SqlServer.Replication.PullSubscription.CreateSyncAgentByDefault%2A> (the default) when you created the pull subscription, you also need to specify <xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent.Distributor%2A>, <xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent.DistributorSecurityMode%2A>, and optionally <xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent.DistributorLogin%2A> and <xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent.DistributorPassword%2A> because the agent job related metadata for the subscription is not available in [MSsubscription_properties](/sql/relational-databases/system-tables/mssubscription-properties-transact-sql).</span></span>  
  
#### <a name="to-synchronize-a-pull-subscription-to-a-merge-publication"></a><span data-ttu-id="2b084-193">병합 게시에 끌어오기 구독을 동기화하려면</span><span class="sxs-lookup"><span data-stu-id="2b084-193">To synchronize a pull subscription to a merge publication</span></span>  
  
1.  <span data-ttu-id="2b084-194"><xref:Microsoft.SqlServer.Management.Common.ServerConnection> 클래스를 사용하여 구독자 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2b084-194">Create a connection to the Subscriber by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="2b084-195"><xref:Microsoft.SqlServer.Replication.MergePullSubscription> 클래스의 인스턴스를 만들고 다음 속성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="2b084-195">Create an instance of the <xref:Microsoft.SqlServer.Replication.MergePullSubscription> class, and set the following properties:</span></span>  
  
    -   <span data-ttu-id="2b084-196"><xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>에 대한 구독 데이터베이스 이름</span><span class="sxs-lookup"><span data-stu-id="2b084-196">The subscription database name for <xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>.</span></span>  
  
    -   <span data-ttu-id="2b084-197"><xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>에 대해 구독이 속한 게시 이름</span><span class="sxs-lookup"><span data-stu-id="2b084-197">The name of the publication to which the subscription belongs for <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>.</span></span>  
  
    -   <span data-ttu-id="2b084-198"><xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A>에 대한 게시 데이터베이스의 이름</span><span class="sxs-lookup"><span data-stu-id="2b084-198">The name of the published database for <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A>.</span></span>  
  
    -   <span data-ttu-id="2b084-199"><xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>에 대한 게시자 이름</span><span class="sxs-lookup"><span data-stu-id="2b084-199">The name of the Publisher for <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>.</span></span>  
  
    -   <span data-ttu-id="2b084-200"><xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>에 대해 1단계에서 만든 연결</span><span class="sxs-lookup"><span data-stu-id="2b084-200">The connection created in step 1 for <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.</span></span>  
  
3.  <span data-ttu-id="2b084-201"><xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> 메서드를 호출하여 나머지 구독 속성을 얻습니다.</span><span class="sxs-lookup"><span data-stu-id="2b084-201">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method to get the remaining subscription properties.</span></span> <span data-ttu-id="2b084-202">이 메서드가 `false`를 반환하는 경우 구독이 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="2b084-202">If this method returns `false`, verify that the subscription exists.</span></span>  
  
4.  <span data-ttu-id="2b084-203">다음 방법 중 하나로 구독자에서 병합 에이전트를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="2b084-203">Start the Merge Agent at the Subscriber in one of the following ways:</span></span>  
  
    -   <span data-ttu-id="2b084-204">2단계에서 만든 <xref:Microsoft.SqlServer.Replication.MergePullSubscription.SynchronizeWithJob%2A> 의 인스턴스에서 <xref:Microsoft.SqlServer.Replication.MergePullSubscription> 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="2b084-204">Call the <xref:Microsoft.SqlServer.Replication.MergePullSubscription.SynchronizeWithJob%2A> method on the instance of <xref:Microsoft.SqlServer.Replication.MergePullSubscription> from step 2.</span></span> <span data-ttu-id="2b084-205">이 메서드는 병합 에이전트를 비동기적으로 시작하고 에이전트 작업이 실행되는 동안 애플리케이션에 대한 반환을 즉시 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="2b084-205">This method starts the Merge Agent asynchronously, and control immediately returns to your application while the agent job is running.</span></span> <span data-ttu-id="2b084-206">[!INCLUDE[ssExpressEd2005](../../includes/ssexpressed2005-md.md)] 구독자인 경우 또는 <xref:Microsoft.SqlServer.Replication.PullSubscription.CreateSyncAgentByDefault%2A>에 `false` 값(기본값)을 사용하여 구독을 만든 경우 이 메서드를 호출할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2b084-206">You cannot call this method for [!INCLUDE[ssExpressEd2005](../../includes/ssexpressed2005-md.md)] Subscribers or if the subscription was created with a value of `false` for <xref:Microsoft.SqlServer.Replication.PullSubscription.CreateSyncAgentByDefault%2A> (the default).</span></span>  
  
    -   <span data-ttu-id="2b084-207"><xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent> 속성에서 <xref:Microsoft.SqlServer.Replication.MergePullSubscription.SynchronizationAgent%2A> 클래스의 인스턴스를 가져오고 <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.Synchronize%2A> 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="2b084-207">Obtain an instance of the <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent> class from the <xref:Microsoft.SqlServer.Replication.MergePullSubscription.SynchronizationAgent%2A> property, and call the <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.Synchronize%2A> method.</span></span> <span data-ttu-id="2b084-208">이 메서드는 병합 에이전트를 동기적으로 시작하고 실행 중인 에이전트 작업에 대한 제어는 그대로 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="2b084-208">This method starts the Merge Agent synchronously, and control remains with the running agent job.</span></span> <span data-ttu-id="2b084-209">동기화 실행 중에는 에이전트를 실행하면서 <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.Status> 이벤트를 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b084-209">During synchronous execution, you can handle the <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.Status> event while the agent is running.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="2b084-210">끌어오기 구독을 만들 때에 값 (기본값)을 지정한 경우에는,,,,, 및를 `false` <xref:Microsoft.SqlServer.Replication.PullSubscription.CreateSyncAgentByDefault%2A> 지정 해야 합니다 <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.Distributor%2A> <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.DistributorSecurityMode%2A> <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.PublisherSecurityMode%2A> <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.HostName%2A> <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.SubscriptionType%2A> <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.ExchangeType%2A> <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.DistributorLogin%2A> <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.DistributorPassword%2A> <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.PublisherLogin%2A> <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.PublisherPassword%2A> . 구독에 대 한 에이전트 작업 관련 메타 데이터는 [MSsubscription_properties](/sql/relational-databases/system-tables/mssubscription-properties-transact-sql)에서 사용할 수 없기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="2b084-210">If you specified a value of `false` for <xref:Microsoft.SqlServer.Replication.PullSubscription.CreateSyncAgentByDefault%2A> (the default) when you created the pull subscription, you also need to specify <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.Distributor%2A>, <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.DistributorSecurityMode%2A>, <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.PublisherSecurityMode%2A>, <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.HostName%2A>, <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.SubscriptionType%2A>, <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.ExchangeType%2A>, and optionally <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.DistributorLogin%2A>, <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.DistributorPassword%2A>, <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.PublisherLogin%2A>, and <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.PublisherPassword%2A> because the agent job related metadata for the subscription is not available in [MSsubscription_properties](/sql/relational-databases/system-tables/mssubscription-properties-transact-sql).</span></span>  
  
###  <a name="examples-rmo"></a><a name="PShellExample"></a> <span data-ttu-id="2b084-211">예(RMO)</span><span class="sxs-lookup"><span data-stu-id="2b084-211">Examples (RMO)</span></span>  
 <span data-ttu-id="2b084-212">다음은 트랜잭션 게시에 끌어오기 구독을 동기화하는 예로, 에이전트 작업을 사용하여 에이전트를 비동기적으로 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="2b084-212">This example synchronizes a pull subscription to a transactional publication, where the agent is started asynchronously using the agent job.</span></span>  
  
 [!code-csharp[HowTo#rmo_SyncTranPullSub_WithJob](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_synctranpullsub_withjob)]  
  
 [!code-vb[HowTo#rmo_vb_SyncTranPullSub_WithJob](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_synctranpullsub_withjob)]  
  
 <span data-ttu-id="2b084-213">다음은 트랜잭션 게시에 끌어오기 구독을 동기화하는 예로, 에이전트를 동기적으로 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="2b084-213">This example synchronizes a pull subscription to a transactional publication, where the agent is started synchronously.</span></span>  
  
 [!code-csharp[HowTo#rmo_SyncTranPullSub](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_synctranpullsub)]  
  
 [!code-vb[HowTo#rmo_vb_SyncTranPullSub](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_synctranpullsub)]  
  
 <span data-ttu-id="2b084-214">다음은 병합 게시에 끌어오기 구독을 동기화하는 예로, 에이전트 작업을 사용하여 에이전트를 비동기적으로 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="2b084-214">This example synchronizes a pull subscription to a merge publication, where the agent is started asynchronously using the agent job.</span></span>  
  
 [!code-csharp[HowTo#rmo_SyncMergePullSub_WithJob](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_syncmergepullsub_withjob)]  
  
 [!code-vb[HowTo#rmo_vb_SyncMergePullSub_WithJob](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_syncmergepullsub_withjob)]  
  
 <span data-ttu-id="2b084-215">다음은 병합 게시에 끌어오기 구독을 동기화하는 예로, 에이전트를 동기적으로 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="2b084-215">This example synchronizes a pull subscription to a merge publication, where the agent is started synchronously.</span></span>  
  
 [!code-csharp[HowTo#rmo_SyncMergePullSub](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_syncmergepullsub)]  
  
 [!code-vb[HowTo#rmo_vb_SyncMergePullSub](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_syncmergepullsub)]  
  
 <span data-ttu-id="2b084-216">다음은 웹 동기화를 사용하여 병합 게시에 끌어오기 구독을 동기화하는 예입니다.</span><span class="sxs-lookup"><span data-stu-id="2b084-216">This example synchronizes a pull subscription to a merge publication using Web synchronization.</span></span> <span data-ttu-id="2b084-217">에이전트 작업 및 관련 구독 메타데이터를 사용하지 않고 구독을 만들었으므로 에이전트를 동기적으로 시작한 다음 추가 구독 정보를 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2b084-217">The subscription was created without the agent job and related subscription metadata, so the agent must be started synchronously and additional subscription information is supplied.</span></span>  
  
 [!code-csharp[HowTo#rmo_SyncMergePullSub_NoJobWebSync](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_syncmergepullsub_nojobwebsync)]  
  
 [!code-vb[HowTo#rmo_vb_SyncMergePullSub_NoJobWebSync](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_syncmergepullsub_nojobwebsync)]  
  
## <a name="see-also"></a><span data-ttu-id="2b084-218">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2b084-218">See Also</span></span>  
 <span data-ttu-id="2b084-219">[데이터 동기화](synchronize-data.md) </span><span class="sxs-lookup"><span data-stu-id="2b084-219">[Synchronize Data](synchronize-data.md) </span></span>  
 <span data-ttu-id="2b084-220">[Create a Pull Subscription](create-a-pull-subscription.md) </span><span class="sxs-lookup"><span data-stu-id="2b084-220">[Create a Pull Subscription](create-a-pull-subscription.md) </span></span>  
 [<span data-ttu-id="2b084-221">복제 보안을 위한 최선의 구현 방법</span><span class="sxs-lookup"><span data-stu-id="2b084-221">Replication Security Best Practices</span></span>](security/replication-security-best-practices.md)  
  
  
