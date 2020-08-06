---
title: 복제된 데이터베이스 업그레이드 | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- merge replication database upgrades [SQL Server replication]
- replication [SQL Server], upgrading
- transactional replication, upgrading databases
- snapshot replication [SQL Server], upgrading databases
- upgrading replicated databases
ms.assetid: 9926a4f7-bcd8-4b9b-9dcf-5426a5857116
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 326a94820876b40128428aac58e47c650ce122b8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649142"
---
# <a name="upgrade-replicated-databases"></a><span data-ttu-id="573aa-102">복제된 데이터베이스 업그레이드</span><span class="sxs-lookup"><span data-stu-id="573aa-102">Upgrade Replicated Databases</span></span>
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<span data-ttu-id="573aa-103">은 이전 버전의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 복제된 데이터베이스를 업그레이드할 수 있도록 지원합니다. 따라서 노드 업그레이드 중에 다른 노드의 작업을 중지할 필요가 없으며</span><span class="sxs-lookup"><span data-stu-id="573aa-103">supports upgrading replicated databases from previous versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]; it is not required to stop activity at other nodes while a node is being upgraded.</span></span> <span data-ttu-id="573aa-104">한 토폴로지 내에서 지원되는 버전과 관련된 규칙만 잘 지키면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="573aa-104">Ensure that you adhere to the rules regarding which versions are supported in a topology:</span></span>  
  
-   <span data-ttu-id="573aa-105">배포자는 게시자 버전 이상인 모든 버전일 수 있습니다. 많은 경우에 배포자는 게시자와 동일한 인스턴스에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="573aa-105">A Distributor can be any version as long as it is greater than or equal to the Publisher version (in many cases the Distributor is the same instance as the Publisher).</span></span>  
  
-   <span data-ttu-id="573aa-106">게시자는 배포자 버전 이하인 모든 버전일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="573aa-106">A Publisher can be any version as long as it less than or equal to the Distributor version.</span></span>  
  
-   <span data-ttu-id="573aa-107">구독자 버전은 게시 유형에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="573aa-107">Subscriber version depends on the type of publication:</span></span>  
  
    -   <span data-ttu-id="573aa-108">트랜잭션 게시에 대한 구독자는 게시자의 두 가지 버전 중 어떤 버전이든 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="573aa-108">A Subscriber to a transactional publication can be any version within two versions of the Publisher version.</span></span> <span data-ttu-id="573aa-109">예를 들어 실행 중인 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 게시자는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 구독자를 가질 수 있으며 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 게시자는 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 구독자를 가질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="573aa-109">For example: a [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] Publisher running can have [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Subscribers; and a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Publisher can have [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] Subscribers.</span></span>  
  
    -   <span data-ttu-id="573aa-110">병합 게시에 대한 구독자는 게시자 버전 이하인 모든 버전일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="573aa-110">A Subscriber to a merge publication can be any version less than or equal to the Publisher version.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="573aa-111">이 항목은 설치 도움말 설명서와 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 온라인 설명서에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="573aa-111">This topic is available in the Setup Help documentation and in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span> <span data-ttu-id="573aa-112">설치 도움말 설명서에서 굵게 표시된 항목 링크는 온라인 설명서에만 제공되는 항목을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="573aa-112">Topic links that appear as bold text in the Setup Help documentation refer to topics that are only available in Books Online.</span></span>  
  
## <a name="run-the-log-reader-agent-for-transactional-replication-before-upgrade"></a><span data-ttu-id="573aa-113">업그레이드 전에 트랜잭션 복제용 로그 판독기 에이전트 실행</span><span class="sxs-lookup"><span data-stu-id="573aa-113">Run the Log Reader Agent for Transactional Replication Before Upgrade</span></span>  
 <span data-ttu-id="573aa-114">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]로 업그레이드하기 전에 게시된 테이블의 커밋된 모든 트랜잭션을 로그 판독기 에이전트가 처리했는지 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="573aa-114">Before you upgrade to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], you must make sure that all committed transactions from published tables have been processed by the Log Reader Agent.</span></span> <span data-ttu-id="573aa-115">모든 트랜잭션이 처리되었는지 확인하려면 트랜잭션 게시를 포함하는 각 데이터베이스에 대해 다음 단계를 수행하십시오.</span><span class="sxs-lookup"><span data-stu-id="573aa-115">To make sure that all transactions have been processed, perform the following steps for each database that contains transactional publications:</span></span>  
  
1.  <span data-ttu-id="573aa-116">데이터베이스에서 로그 판독기 에이전트가 실행 중인지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="573aa-116">Make sure that the Log Reader Agent is running for the database.</span></span> <span data-ttu-id="573aa-117">기본적으로 에이전트는 계속 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="573aa-117">By default, the agent runs continuously.</span></span>  
  
2.  <span data-ttu-id="573aa-118">게시된 테이블에 대한 사용자 동작을 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="573aa-118">Stop user activity on published tables.</span></span>  
  
3.  <span data-ttu-id="573aa-119">로그 판독기 에이전트가 배포 데이터베이스로 트랜잭션을 복사할 때까지 기다린 다음 에이전트를 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="573aa-119">Allow time for the Log Reader Agent to copy transactions to the distribution database, and then stop the agent.</span></span>  
  
4.  <span data-ttu-id="573aa-120">[sp_replcmds](/sql/relational-databases/system-stored-procedures/sp-replcmds-transact-sql) 를 실행하여 모든 트랜잭션이 처리되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="573aa-120">Execute [sp_replcmds](/sql/relational-databases/system-stored-procedures/sp-replcmds-transact-sql) to verify that all transactions have been processed.</span></span> <span data-ttu-id="573aa-121">이 프로시저의 결과 집합은 비어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="573aa-121">The result set from this procedure should be empty.</span></span>  
  
5.  <span data-ttu-id="573aa-122">[sp_replflush](/sql/relational-databases/system-stored-procedures/sp-replflush-transact-sql) 를 실행하여 sp_replcmds의 연결을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="573aa-122">Execute [sp_replflush](/sql/relational-databases/system-stored-procedures/sp-replflush-transact-sql) to close the connection from sp_replcmds.</span></span>  
  
6.  <span data-ttu-id="573aa-123">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]로 서버를 업그레이드합니다.</span><span class="sxs-lookup"><span data-stu-id="573aa-123">Perform the server upgrade to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
7.  <span data-ttu-id="573aa-124">업그레이드 후에 자동으로 시작되지 않는 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 및 로그 판독기 에이전트를 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="573aa-124">Restart [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent and the Log Reader Agent if they do not start automatically after the upgrade.</span></span>  
  
## <a name="run-agents-for-merge-replication-after-upgrade"></a><span data-ttu-id="573aa-125">업그레이드 후 병합 복제를 위한 에이전트 실행</span><span class="sxs-lookup"><span data-stu-id="573aa-125">Run Agents for Merge Replication After Upgrade</span></span>  
 <span data-ttu-id="573aa-126">업그레이드 후에 각 병합 게시에 대해 스냅샷 에이전트를 실행하고 각 구독에 대해 병합 에이전트를 실행하여 복제 메타데이터를 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="573aa-126">After upgrade, run the Snapshot Agent for each merge publication and the Merge Agent for each subscription to update replication metadata.</span></span> <span data-ttu-id="573aa-127">구독을 다시 초기화할 필요가 없으므로 새 스냅샷을 적용하지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="573aa-127">You do not have to apply the new snapshot, because it is not necessary to reinitialize subscriptions.</span></span> <span data-ttu-id="573aa-128">구독 메타데이터는 업그레이드 후에 병합 에이전트가 처음 실행될 때 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="573aa-128">Subscription metadata is updated the first time the Merge Agent is run after upgrade.</span></span> <span data-ttu-id="573aa-129">즉, 게시자를 업그레이드하는 동안 구독 데이터베이스를 온라인 활성 상태로 유지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="573aa-129">This means that the subscription database can remain online and active during the Publisher upgrade.</span></span>  
  
 <span data-ttu-id="573aa-130">병합 복제는 게시 및 구독 데이터베이스의 많은 시스템 테이블에 게시 및 구독 메타데이터를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="573aa-130">Merge replication stores publication and subscription metadata in a number of system tables in the publication and subscription databases.</span></span> <span data-ttu-id="573aa-131">스냅샷 에이전트를 실행하면 게시 메타데이터가 업데이트되고 병합 에이전트를 실행하면 구독 메타데이터가 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="573aa-131">Running the Snapshot Agent updates publication metadata and running the Merge Agent updates subscription metadata.</span></span> <span data-ttu-id="573aa-132">따라서 게시 스냅샷을 생성하기만 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="573aa-132">It is only required to generate a publication snapshot.</span></span> <span data-ttu-id="573aa-133">병합 게시에 매개 변수가 있는 필터가 사용되면 각 파티션은 스냅샷도 갖게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="573aa-133">If a merge publication uses parameterized filters, each partition also has a snapshot.</span></span> <span data-ttu-id="573aa-134">이러한 분할된 스냅샷은 업데이트하지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="573aa-134">It is not necessary to update these partitioned snapshots.</span></span>  
  
 <span data-ttu-id="573aa-135">에이전트는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], 복제 모니터 또는 명령줄에서 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="573aa-135">Run the agents from [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], Replication Monitor, or from the command line.</span></span> <span data-ttu-id="573aa-136">스냅샷 에이전트를 실행하는 방법은 다음 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="573aa-136">For more information about running the Snapshot Agent, see the following topics:</span></span>  
  
-   [<span data-ttu-id="573aa-137">초기 스냅샷 만들기 및 적용</span><span class="sxs-lookup"><span data-stu-id="573aa-137">Create and Apply the Initial Snapshot</span></span>](../../../2014/relational-databases/replication/create-and-apply-the-initial-snapshot.md)  
  
-   [<span data-ttu-id="573aa-138">복제 에이전트 시작 및 중지&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="573aa-138">Start and Stop a Replication Agent &#40;SQL Server Management Studio&#41;</span></span>](../../relational-databases/replication/agents/start-and-stop-a-replication-agent-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="573aa-139">초기 스냅샷 만들기 및 적용</span><span class="sxs-lookup"><span data-stu-id="573aa-139">Create and Apply the Initial Snapshot</span></span>](../../../2014/relational-databases/replication/create-and-apply-the-initial-snapshot.md)  
  
-   [<span data-ttu-id="573aa-140">Replication Agent Executables Concepts</span><span class="sxs-lookup"><span data-stu-id="573aa-140">Replication Agent Executables Concepts</span></span>](../../../2014/relational-databases/replication/concepts/replication-agent-executables-concepts.md)  
  
 <span data-ttu-id="573aa-141">병합 에이전트를 실행하는 방법은 다음 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="573aa-141">For more information about running the Merge Agent, see the following topics:</span></span>  
  
-   [<span data-ttu-id="573aa-142">끌어오기 구독 동기화</span><span class="sxs-lookup"><span data-stu-id="573aa-142">Synchronize a Pull Subscription</span></span>](../../../2014/relational-databases/replication/synchronize-a-pull-subscription.md)  
  
-   [<span data-ttu-id="573aa-143">밀어넣기 구독 동기화</span><span class="sxs-lookup"><span data-stu-id="573aa-143">Synchronize a Push Subscription</span></span>](../../../2014/relational-databases/replication/synchronize-a-push-subscription.md)  
  
 <span data-ttu-id="573aa-144">병합 복제를 사용하는 토폴로지에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 를 업그레이드한 후에 새 기능을 사용하려면 모든 게시의 게시 호환성 수준을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="573aa-144">After upgrading [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in a topology that uses merge replication, change the publication compatibility level of any publications if you want to use new features.</span></span>  
  
## <a name="upgrading-to-standard-workgroup-or-express-editions"></a><span data-ttu-id="573aa-145">Standard, Workgroup 또는 Express Edition으로 업그레이드</span><span class="sxs-lookup"><span data-stu-id="573aa-145">Upgrading to Standard, Workgroup, or Express Editions</span></span>  
 <span data-ttu-id="573aa-146">한 에디션의 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 에서 다른 에디션으로 업그레이드하기 전에 현재 사용 중인 기능이 업그레이드할 에디션에서 지원되는지 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="573aa-146">Before upgrading from one edition of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] to another, verify that the functionality you are currently using is supported in the edition to which you are upgrading.</span></span> <span data-ttu-id="573aa-147">자세한 내용은 [SQL Server 2014 버전에서 지 원하는 기능](../../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md)에서 복제에 대 한 섹션을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="573aa-147">For more information, see the section on Replication in [Features Supported by the Editions of SQL Server 2014](../../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
## <a name="web-synchronization-for-merge-replication"></a><span data-ttu-id="573aa-148">병합 복제에 대한 웹 동기화</span><span class="sxs-lookup"><span data-stu-id="573aa-148">Web Synchronization for Merge Replication</span></span>  
 <span data-ttu-id="573aa-149">병합 복제에 대한 웹 동기화 옵션을 사용하려면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 복제 수신기(replisapi.dll)를 동기화에 사용되는 인터넷 정보 서비스(IIS) 서버의 가상 디렉터리에 복사해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="573aa-149">The Web synchronization option for merge replication requires that the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Replication Listener (replisapi.dll) be copied to the virtual directory on the Internet Information Services (IIS) server used for synchronization.</span></span> <span data-ttu-id="573aa-150">웹 동기화를 구성할 때는 웹 동기화 구성 마법사를 실행하여 가상 디렉터리에 파일을 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="573aa-150">When you configure Web synchronization, the file is copied to the virtual directory by the Configure Web Synchronization Wizard.</span></span> <span data-ttu-id="573aa-151">IIS 서버에 설치된 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구성 요소를 업그레이드하는 경우에는 COM 디렉터리의 replisapi.dll을 IIS 서버의 가상 디렉터리에 수동으로 복사해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="573aa-151">If you upgrade the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] components installed on the IIS server, you must manually copy replisapi.dll from the COM directory to the virtual directory on the IIS server.</span></span> <span data-ttu-id="573aa-152">웹 동기화를 구성하는 방법은 [웹 동기화 구성](../../../2014/relational-databases/replication/configure-web-synchronization.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="573aa-152">For more information about configuring Web synchronization, see [Configure Web Synchronization](../../../2014/relational-databases/replication/configure-web-synchronization.md).</span></span>  
  
## <a name="restoring-a-replicated-database-from-an-earlier-version"></a><span data-ttu-id="573aa-153">이전 버전에서 복제된 데이터베이스 복원</span><span class="sxs-lookup"><span data-stu-id="573aa-153">Restoring a Replicated Database from an Earlier Version</span></span>  
 <span data-ttu-id="573aa-154">이전 버전에서 복제된 데이터베이스의 백업을 복원할 때 복제 설정이 유지되게 하려면 백업 당시의 서버 및 데이터베이스와 같은 이름의 서버 및 데이터베이스에 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="573aa-154">To ensure replication settings are retained when restoring a backup of a replicated database from a previous version: restore to a server and database with the same names as the server and database at which the backup was taken.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="573aa-155">참고 항목</span><span class="sxs-lookup"><span data-stu-id="573aa-155">See Also</span></span>  
 <span data-ttu-id="573aa-156">[복제 관리 FAQ](../../relational-databases/replication/administration/frequently-asked-questions-for-replication-administrators.md) </span><span class="sxs-lookup"><span data-stu-id="573aa-156">[Replication Administration FAQ](../../relational-databases/replication/administration/frequently-asked-questions-for-replication-administrators.md) </span></span>  
 <span data-ttu-id="573aa-157">[복제의 이전 버전과의 호환성](../../../2014/relational-databases/replication/replication-backward-compatibility.md) </span><span class="sxs-lookup"><span data-stu-id="573aa-157">[Replication Backward Compatibility](../../../2014/relational-databases/replication/replication-backward-compatibility.md) </span></span>  
 <span data-ttu-id="573aa-158">[지원되는 버전 및 에디션 업그레이드](../../database-engine/install-windows/supported-version-and-edition-upgrades.md) </span><span class="sxs-lookup"><span data-stu-id="573aa-158">[Supported Version and Edition Upgrades](../../database-engine/install-windows/supported-version-and-edition-upgrades.md) </span></span>  
 [<span data-ttu-id="573aa-159">SQL Server 2014로 업그레이드</span><span class="sxs-lookup"><span data-stu-id="573aa-159">Upgrade to SQL Server 2014</span></span>](upgrade-sql-server.md)  
  
  
