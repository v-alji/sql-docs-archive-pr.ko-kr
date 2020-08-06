---
title: 트랜잭션 복제에 대한 대기 시간 측정 및 연결 유효성 검사 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Replication Monitor, performance
- tracer tokens [SQL Server replication]
- latency [SQL Server replication]
- transactional replication, tracer tokens
- monitoring performance [SQL Server replication], tracer tokens
ms.assetid: 4addd426-7523-4067-8d7d-ca6bae4c9e34
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 3ba1e5eddfdcffa5fbefdea323f110ba9d15ca8c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648936"
---
# <a name="measure-latency-and-validate-connections-for-transactional-replication"></a><span data-ttu-id="4372c-102">트랜잭션 복제에 대한 대기 시간 측정 및 연결 유효성 검사</span><span class="sxs-lookup"><span data-stu-id="4372c-102">Measure Latency and Validate Connections for Transactional Replication</span></span>
  <span data-ttu-id="4372c-103">이 항목에서는 복제 모니터, [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 또는 RMO(복제 관리 개체)를 사용하여 [!INCLUDE[tsql](../../../includes/tsql-md.md)]에서 트랜잭션 복제에 대한 대기 시간을 측정하고 연결의 유효성을 검사하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="4372c-103">This topic describes how to measure latency and validate connections for transactional replication in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using Replication Monitor, [!INCLUDE[tsql](../../../includes/tsql-md.md)], or Replication Management Objects (RMO).</span></span> <span data-ttu-id="4372c-104">트랜잭션 복제는 트랜잭션 복제 토폴로지에서 대기 시간을 측정하고 게시자, 배포자 및 구독자 간 연결의 유효성을 검사하는 편리한 방법을 제공하는 추적 프로그램 토큰 기능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="4372c-104">Transactional replication provides the tracer token feature, which provides a convenient way to measure latency in transactional replication topologies and to validate the connections between the Publisher, Distributor and Subscribers.</span></span> <span data-ttu-id="4372c-105">토큰(적은 양의 데이터)은 게시 데이터베이스의 트랜잭션 로그에 기록되고, 일반적인 복제된 트랜잭션인 것처럼 표시되고, 시스템을 통해 전달되며 다음을 계산할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4372c-105">A token (a small amount of data) is written to the transaction log of the publication database, marked as though it were a typical replicated transaction, and sent through the system, allowing a calculation of:</span></span>  
  
-   <span data-ttu-id="4372c-106">게시자에서 커밋된 트랜잭션과 배포자의 배포 데이터베이스에서 삽입된 해당 명령 사이의 경과 시간</span><span class="sxs-lookup"><span data-stu-id="4372c-106">How much time elapses between a transaction being committed at the Publisher and the corresponding command being inserted in the distribution database at the Distributor.</span></span>  
  
-   <span data-ttu-id="4372c-107">배포 데이터베이스에 삽입된 명령과 구독자에서 커밋된 해당 트랜잭션 사이의 경과 시간</span><span class="sxs-lookup"><span data-stu-id="4372c-107">How much time elapses between a command being inserted in the distribution database and the corresponding transaction being committed at a Subscriber.</span></span>  
  
 <span data-ttu-id="4372c-108">이러한 계산을 잘 검토하면 다음을 비롯한 여러 가지 질문에 대답할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4372c-108">From these calculations, you can answer a number of questions, including:</span></span>  
  
-   <span data-ttu-id="4372c-109">게시자의 변경 내용을 받는 데 가장 오래 걸리는 구독자는 무엇입니까?</span><span class="sxs-lookup"><span data-stu-id="4372c-109">Which Subscribers take the longest to receive a change from the Publisher?</span></span>  
  
-   <span data-ttu-id="4372c-110">추적 프로그램 토큰을 받아야 할 구독자가 있습니까? 있다면 아직 추적 프로그램 토큰을 받지 못한 구독자는 무엇입니까?</span><span class="sxs-lookup"><span data-stu-id="4372c-110">Of the Subscribers expected to receive the tracer token, which, if any, have not received it?</span></span>  
  
 <span data-ttu-id="4372c-111">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="4372c-111">**In This Topic**</span></span>  
  
-   <span data-ttu-id="4372c-112">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="4372c-112">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="4372c-113">제한 사항</span><span class="sxs-lookup"><span data-stu-id="4372c-113">Limitations and Restrictions</span></span>](#Restrictions)  
  
-   <span data-ttu-id="4372c-114">**대기 시간을 측정하고 연결의 유효성을 검사하려면:**</span><span class="sxs-lookup"><span data-stu-id="4372c-114">**To measure latency and validate connections, using:**</span></span>  
  
     [<span data-ttu-id="4372c-115">SQL Server 복제 모니터</span><span class="sxs-lookup"><span data-stu-id="4372c-115">SQL Server Replication Monitor</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="4372c-116">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="4372c-116">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="4372c-117">RMO(복제 관리 개체)</span><span class="sxs-lookup"><span data-stu-id="4372c-117">Replication Management Objects</span></span>](#RMOProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="4372c-118">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="4372c-118">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="4372c-119">제한 사항</span><span class="sxs-lookup"><span data-stu-id="4372c-119">Limitations and Restrictions</span></span>  
 <span data-ttu-id="4372c-120">또한 추적 프로그램 토큰은 모든 작업을 중지하고 모든 노드가 처리 중인 변경 내용을 모두 받았는지 확인하므로 시스템을 중지시킬 때 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4372c-120">Tracer tokens can also be useful when quiescing a system, which involves stopping all activity and verifying that all nodes have received all outstanding changes.</span></span> <span data-ttu-id="4372c-121">자세한 내용은 [복제 토폴로지 정지&#40;복제 Transact-SQL 프로그래밍&#41;](../administration/quiesce-a-replication-topology-replication-transact-sql-programming.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4372c-121">For more information, see [Quiesce a Replication Topology &#40;Replication Transact-SQL Programming&#41;](../administration/quiesce-a-replication-topology-replication-transact-sql-programming.md).</span></span>  
  
 <span data-ttu-id="4372c-122">추적 프로그램 토큰을 사용 하려면 다음의 특정 버전을 사용 해야 합니다 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="4372c-122">To use tracer tokens, you must use certain versions of [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="4372c-123">배포자는 이상 이어야 합니다 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="4372c-123">The Distributor must be [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] or later.</span></span>  
  
-   <span data-ttu-id="4372c-124">게시자는 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 이후 버전이거나 Oracle 게시자여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4372c-124">The Publisher must be [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] or later or be an Oracle Publisher.</span></span>  
  
-   <span data-ttu-id="4372c-125">밀어넣기 구독의 경우 구독자가 7.0 이상인 경우 추적 프로그램 토큰 통계가 게시자, 배포자 및 구독자에서 수집 됩니다 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="4372c-125">For push subscriptions, tracer token statistics are gathered from the Publisher, Distributor, and Subscribers if the Subscriber is [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 7.0 or later.</span></span>  
  
-   <span data-ttu-id="4372c-126">끌어오기 구독의 경우 구독자가 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 이후 버전이면 추적 프로그램 토큰 통계는 구독자에서만 수집됩니다.</span><span class="sxs-lookup"><span data-stu-id="4372c-126">For pull subscriptions, tracer token statistics are gathered from Subscribers only if the Subscriber is [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] or later.</span></span> <span data-ttu-id="4372c-127">구독자가 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 7.0 또는 인 경우 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)] 게시자와 배포자 에서만 통계가 수집 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4372c-127">If the Subscriber is [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 7.0 or [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)], statistics are gathered only from the Publisher and Distributor.</span></span>  
  
 <span data-ttu-id="4372c-128">또한 다음과 같이 주의해야 할 다른 문제 및 제한 사항이 많이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4372c-128">There are also a number of other issues and restrictions to be aware of:</span></span>  
  
-   <span data-ttu-id="4372c-129">추적 프로그램 토큰을 받으려면 구독이 활성 상태여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4372c-129">Subscriptions must be active to receive a tracer token.</span></span> <span data-ttu-id="4372c-130">구독이 초기화되었다면 활성 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="4372c-130">A subscription is active if it has been initialized.</span></span>  
  
-   <span data-ttu-id="4372c-131">다시 초기화는 관련 구독에 대해 보류 중인 추적 프로그램 토큰을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="4372c-131">Reinitialization removes any pending tracer tokens for the relevant subscriptions.</span></span>  
  
-   <span data-ttu-id="4372c-132">구독자는 자신의 초기 동기화 이후에 생성된 추적 프로그램 토큰만 받습니다.</span><span class="sxs-lookup"><span data-stu-id="4372c-132">Subscribers only receive tracer tokens that were created after their initial synchronization.</span></span>  
  
-   <span data-ttu-id="4372c-133">구독자를 다시 게시하면 추적 프로그램 토큰이 전달되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4372c-133">Tracer tokens are not forwarded by republishing Subscribers.</span></span>  
  
-   <span data-ttu-id="4372c-134">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 의 보조 인스턴스에 대한 장애 조치(failover) 후에 복제 모니터는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]의 게시 인스턴스 이름을 조정할 수 없으며 계속해서 원래 주 인스턴스 이름으로 복제 정보를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="4372c-134">After failover to a secondary, Replication Monitor is unable to adjust the name of the publishing instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] and will continue to display replication information under the name of the original primary instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="4372c-135">장애 조치(Failover) 후 복제 모니터를 사용하여 추적 프로그램 토큰을 입력할 수 없지만 새 게시자가 [!INCLUDE[tsql](../../../includes/tsql-md.md)]을 사용하여 입력한 추적 프로그램 토큰은 복제 모니터에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="4372c-135">After failover, a tracer token cannot be entered by using the Replication Monitor, however a tracer token entered on the new publisher by using [!INCLUDE[tsql](../../../includes/tsql-md.md)], is visible in Replication Monitor.</span></span>  
  
##  <a name="using-sql-server-replication-monitor"></a><a name="SSMSProcedure"></a><span data-ttu-id="4372c-136">SQL Server 복제 모니터 사용</span><span class="sxs-lookup"><span data-stu-id="4372c-136">Using SQL Server Replication Monitor</span></span>  
 <span data-ttu-id="4372c-137">복제 모니터를 시작하는 방법은 [복제 모니터 시작](start-the-replication-monitor.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4372c-137">For information about starting Replication Monitor, see [Start the Replication Monitor](start-the-replication-monitor.md).</span></span>  
  
#### <a name="to-insert-a-tracer-token-and-view-information-on-the-token"></a><span data-ttu-id="4372c-138">추적 프로그램 토큰을 삽입하고 이 토큰에 대한 정보를 보려면</span><span class="sxs-lookup"><span data-stu-id="4372c-138">To insert a tracer token and view information on the token</span></span>  
  
1.  <span data-ttu-id="4372c-139">왼쪽 창에서 게시자 그룹을 확장하고 해당 게시자를 확장한 다음 해당 게시를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4372c-139">Expand a Publisher group in the left pane, expand a Publisher, and then click a publication.</span></span>  
  
2.  <span data-ttu-id="4372c-140">**추적 프로그램 토큰** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4372c-140">Click the **Tracer Tokens** tab.</span></span>  
  
3.  <span data-ttu-id="4372c-141">**추적 프로그램 삽입**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4372c-141">Click **Insert Tracer**.</span></span>  
  
4.  <span data-ttu-id="4372c-142">**게시자에서 배포자로 연결 시 대기 시간**, **배포자에서 구독자로 연결 시 대기 시간**, **총 대기 시간**열에서 추적 프로그램 토큰에 대한 경과 시간을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="4372c-142">View elapsed time for the tracer token in the following columns: **Publisher to Distributor**, **Distributor to Subscriber**, **Total Latency**.</span></span> <span data-ttu-id="4372c-143">**보류** 중 값은 토큰이 지정 된 지점에 도달 하지 않았음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="4372c-143">A value of **Pending** indicates that the token has not reached a given point.</span></span>  
  
#### <a name="to-view-information-on-a-tracer-token-inserted-previously"></a><span data-ttu-id="4372c-144">이전에 삽입한 추적 프로그램 토큰에 대한 정보를 보려면</span><span class="sxs-lookup"><span data-stu-id="4372c-144">To view information on a tracer token inserted previously</span></span>  
  
1.  <span data-ttu-id="4372c-145">왼쪽 창에서 게시자 그룹을 확장하고 해당 게시자를 확장한 다음 해당 게시를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4372c-145">Expand a Publisher group in the left pane, expand a Publisher, and then click a publication.</span></span>  
  
2.  <span data-ttu-id="4372c-146">**추적 프로그램 토큰** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4372c-146">Click the **Tracer Tokens** tab.</span></span>  
  
3.  <span data-ttu-id="4372c-147">**삽입된 시간** 드롭다운 목록에서 시간을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4372c-147">Select a time from the **Time inserted** drop-down list.</span></span>  
  
4.  <span data-ttu-id="4372c-148">**게시자에서 배포자로 연결 시 대기 시간**, **배포자에서 구독자로 연결 시 대기 시간**, **총 대기 시간**열에서 추적 프로그램 토큰에 대한 경과 시간을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="4372c-148">View elapsed time for the tracer token in the following columns: **Publisher to Distributor**, **Distributor to Subscriber**, **Total Latency**.</span></span> <span data-ttu-id="4372c-149">**보류** 중 값은 토큰이 지정 된 지점에 도달 하지 않았음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="4372c-149">A value of **Pending** indicates that the token has not reached a given point.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="4372c-150">추적 프로그램 토큰 정보는 배포 데이터베이스의 기록 보존 기간에 의해 제어되는 다른 기록 데이터와 같은 시간 동안 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="4372c-150">Tracer token information is retained for the same time period as other historical data, which is governed by the history retention period of the distribution database.</span></span> <span data-ttu-id="4372c-151">배포 데이터베이스 속성 변경에 대한 자세한 내용은 [게시자 및 배포자 속성 보기 및 수정](../view-and-modify-distributor-and-publisher-properties.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4372c-151">For information about changing distribution database properties, see [View and Modify Distributor and Publisher Properties](../view-and-modify-distributor-and-publisher-properties.md).</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="4372c-152">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="4372c-152">Using Transact-SQL</span></span>  
  
#### <a name="to-post-a-tracer-token-to-a-transactional-publication"></a><span data-ttu-id="4372c-153">트랜잭션 게시에 추적 프로그램 토큰을 게시하려면</span><span class="sxs-lookup"><span data-stu-id="4372c-153">To post a tracer token to a transactional publication</span></span>  
  
1.  <span data-ttu-id="4372c-154">(옵션) 게시 데이터베이스의 게시자에서 [sp_helppublication&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql)을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="4372c-154">(Optional) At the Publisher on the publication database, execute [sp_helppublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql).</span></span> <span data-ttu-id="4372c-155">해당 게시가 있는지 그리고 상태가 활성 상태인지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="4372c-155">Verify that the publication exists and that the status is active.</span></span>  
  
2.  <span data-ttu-id="4372c-156">(옵션) 게시 데이터베이스의 게시자에서 [sp_helpsubscription&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql)을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="4372c-156">(Optional) At the Publisher on the publication database, execute [sp_helpsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql).</span></span> <span data-ttu-id="4372c-157">해당 구독이 있는지 그리고 상태가 활성 상태인지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="4372c-157">Verify that the subscription exists and that the status is active.</span></span>  
  
3.  <span data-ttu-id="4372c-158">게시 데이터베이스의 게시자에서 [sp_posttracertoken&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-posttracertoken-transact-sql)을 실행하여 **@publication**을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4372c-158">At the Publisher on the publication database, execute [sp_posttracertoken &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-posttracertoken-transact-sql), specifying **@publication**.</span></span> <span data-ttu-id="4372c-159">**@tracer_token_id**출력 매개 변수의 값을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="4372c-159">Note the value of the **@tracer_token_id** output parameter.</span></span>  
  
#### <a name="to-determine-latency-and-validate-connections-for-a-transactional-publication"></a><span data-ttu-id="4372c-160">트랜잭션 복제에 대한 대기 시간을 확인하고 연결 유효성을 검사하려면</span><span class="sxs-lookup"><span data-stu-id="4372c-160">To determine latency and validate connections for a transactional publication</span></span>  
  
1.  <span data-ttu-id="4372c-161">이전 절차를 따라 게시에 추적 프로그램 토큰을 게시합니다.</span><span class="sxs-lookup"><span data-stu-id="4372c-161">Post a tracer token to the publication using the previous procedure.</span></span>  
  
2.  <span data-ttu-id="4372c-162">게시 데이터베이스의 게시자에서 [sp_helptracertokens&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helptracertokens-transact-sql)를 실행하여 **@publication**을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4372c-162">At the Publisher on the publication database, execute [sp_helptracertokens &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helptracertokens-transact-sql), specifying **@publication**.</span></span> <span data-ttu-id="4372c-163">그러면 해당 게시에 게시된 모든 추적 프로그램 토큰의 목록이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="4372c-163">This returns a list of all tracer tokens posted to the publication.</span></span> <span data-ttu-id="4372c-164">결과 집합에서 원하는 **tracer_id** 를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="4372c-164">Note the desired **tracer_id** in the result set.</span></span>  
  
3.  <span data-ttu-id="4372c-165">게시 데이터베이스의 게시자에서 [sp_helptracertokenhistory&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helptracertokenhistory-transact-sql)를 실행하여 **@publication**을 지정하고 **@tracer_id**에 대해 2단계에서 얻은 추적 프로그램 토큰 ID를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4372c-165">At the Publisher on the publication database, execute [sp_helptracertokenhistory &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helptracertokenhistory-transact-sql), specifying **@publication** and the tracer token ID from step 2 for **@tracer_id**.</span></span> <span data-ttu-id="4372c-166">그러면 선택한 추적 프로그램 토큰에 대한 대기 시간 정보가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="4372c-166">This returns latency information for the selected tracer token.</span></span>  
  
#### <a name="to-remove-tracer-tokens"></a><span data-ttu-id="4372c-167">추적 프로그램 토큰을 제거하려면</span><span class="sxs-lookup"><span data-stu-id="4372c-167">To remove tracer tokens</span></span>  
  
1.  <span data-ttu-id="4372c-168">게시 데이터베이스의 게시자에서 [sp_helptracertokens&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helptracertokens-transact-sql)를 실행하여 **@publication**을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4372c-168">At the Publisher on the publication database, execute [sp_helptracertokens &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helptracertokens-transact-sql), specifying **@publication**.</span></span> <span data-ttu-id="4372c-169">그러면 해당 게시에 게시된 모든 추적 프로그램 토큰의 목록이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="4372c-169">This returns a list of all tracer tokens posted to the publication.</span></span> <span data-ttu-id="4372c-170">결과 집합에서 삭제할 추적 프로그램 토큰의 **tracer_id** 를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="4372c-170">Note the **tracer_id** for the tracer token to delete in the result set.</span></span>  
  
2.  <span data-ttu-id="4372c-171">게시 데이터베이스의 게시자에서 [sp_deletetracertokenhistory&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-deletetracertokenhistory-transact-sql)를 실행하여 **@publication**을 지정하고 **@tracer_id**에 대해 2단계에서 얻은 삭제할 추적 프로그램의 ID를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4372c-171">At the Publisher on the publication database, execute [sp_deletetracertokenhistory &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-deletetracertokenhistory-transact-sql), specifying **@publication** and the ID of the tracer to delete from step 2 for **@tracer_id**.</span></span>  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="4372c-172">예(Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="4372c-172">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="4372c-173">이 예제에서는 추적 프로그램 토큰 레코드를 게시하고 게시된 추적 프로그램 토큰의 반환된 ID를 사용하여 대기 시간 정보를 봅니다.</span><span class="sxs-lookup"><span data-stu-id="4372c-173">This example posts a tracer token record and uses the returned ID of the posted tracer token to view latency information.</span></span>  
  
 [!code-sql[HowTo#sp_tracertokens](../../../snippets/tsql/SQL15/replication/howto/tsql/createtracertokens.sql#sp_tracertokens)]  
  
##  <a name="using-replication-management-objects-rmo"></a><a name="RMOProcedure"></a> <span data-ttu-id="4372c-174">RMO(복제 관리 개체) 사용</span><span class="sxs-lookup"><span data-stu-id="4372c-174">Using Replication Management Objects (RMO)</span></span>  
  
#### <a name="to-post-a-tracer-token-to-a-transactional-publication"></a><span data-ttu-id="4372c-175">트랜잭션 게시에 추적 프로그램 토큰을 게시하려면</span><span class="sxs-lookup"><span data-stu-id="4372c-175">To post a tracer token to a transactional publication</span></span>  
  
1.  <span data-ttu-id="4372c-176"><xref:Microsoft.SqlServer.Management.Common.ServerConnection> 클래스를 사용하여 게시자 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="4372c-176">Create a connection to the Publisher by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="4372c-177"><xref:Microsoft.SqlServer.Replication.TransPublication> 클래스의 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="4372c-177">Create an instance of the <xref:Microsoft.SqlServer.Replication.TransPublication> class.</span></span>  
  
3.  <span data-ttu-id="4372c-178">게시에 대해 <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> 및 <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> 속성을 설정하고 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> 속성을 1단계에서 만든 연결로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="4372c-178">Set the <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> and <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> properties for the publication, and set the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property to the connection created in step 1.</span></span>  
  
4.  <span data-ttu-id="4372c-179"><xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> 메서드를 호출하여 개체 속성을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="4372c-179">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method to get the properties of the object.</span></span> <span data-ttu-id="4372c-180">이 메서드가 `false`를 반환하는 경우 3단계에서 게시 속성이 올바르게 정의되지 않았거나 게시가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4372c-180">If this method returns `false`, either the publication properties in step 3 were defined incorrectly or the publication does not exist.</span></span>  
  
5.  <span data-ttu-id="4372c-181"><xref:Microsoft.SqlServer.Replication.TransPublication.PostTracerToken%2A> 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="4372c-181">Call the <xref:Microsoft.SqlServer.Replication.TransPublication.PostTracerToken%2A> method.</span></span> <span data-ttu-id="4372c-182">이 메서드는 게시의 트랜잭션 로그에 추적 프로그램 토큰을 삽입합니다.</span><span class="sxs-lookup"><span data-stu-id="4372c-182">This method inserts a tracer token into the publication's transaction log.</span></span>  
  
#### <a name="to-determine-latency-and-validate-connections-for-a-transactional-publication"></a><span data-ttu-id="4372c-183">트랜잭션 복제에 대한 대기 시간을 확인하고 연결 유효성을 검사하려면</span><span class="sxs-lookup"><span data-stu-id="4372c-183">To determine latency and validate connections for a transactional publication</span></span>  
  
1.  <span data-ttu-id="4372c-184"><xref:Microsoft.SqlServer.Management.Common.ServerConnection> 클래스를 사용하여 배포자 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="4372c-184">Create a connection to the Distributor by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="4372c-185"><xref:Microsoft.SqlServer.Replication.PublicationMonitor> 클래스의 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="4372c-185">Create an instance of the <xref:Microsoft.SqlServer.Replication.PublicationMonitor> class.</span></span>  
  
3.  <span data-ttu-id="4372c-186"><xref:Microsoft.SqlServer.Replication.PublicationMonitor.Name%2A>, <xref:Microsoft.SqlServer.Replication.PublicationMonitor.DistributionDBName%2A>, <xref:Microsoft.SqlServer.Replication.PublicationMonitor.PublisherName%2A>및 <xref:Microsoft.SqlServer.Replication.PublicationMonitor.PublicationDBName%2A> 속성을 설정하고 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> 속성을 1단계에서 만든 연결로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="4372c-186">Set the <xref:Microsoft.SqlServer.Replication.PublicationMonitor.Name%2A>, <xref:Microsoft.SqlServer.Replication.PublicationMonitor.DistributionDBName%2A>, <xref:Microsoft.SqlServer.Replication.PublicationMonitor.PublisherName%2A>, and <xref:Microsoft.SqlServer.Replication.PublicationMonitor.PublicationDBName%2A> properties, and set the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property to the connection created in step 1.</span></span>  
  
4.  <span data-ttu-id="4372c-187"><xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> 메서드를 호출하여 개체 속성을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="4372c-187">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method to get the properties of the object.</span></span> <span data-ttu-id="4372c-188">이 메서드가 `false`를 반환하는 경우 3단계에서 게시 모니터 속성이 올바르게 정의되지 않았거나 해당 게시가 없는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="4372c-188">If this method returns `false`, either the publication monitor properties in step 3 were defined incorrectly or the publication does not exist.</span></span>  
  
5.  <span data-ttu-id="4372c-189"><xref:Microsoft.SqlServer.Replication.PublicationMonitor.EnumTracerTokens%2A> 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="4372c-189">Call the <xref:Microsoft.SqlServer.Replication.PublicationMonitor.EnumTracerTokens%2A> method.</span></span> <span data-ttu-id="4372c-190">반환된 <xref:System.Collections.ArrayList> 개체를 <xref:Microsoft.SqlServer.Replication.TracerToken> 개체의 배열로 캐스팅합니다.</span><span class="sxs-lookup"><span data-stu-id="4372c-190">Cast the returned <xref:System.Collections.ArrayList> object to an array of <xref:Microsoft.SqlServer.Replication.TracerToken> objects.</span></span>  
  
6.  <span data-ttu-id="4372c-191"><xref:Microsoft.SqlServer.Replication.PublicationMonitor.EnumTracerTokenHistory%2A> 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="4372c-191">Call the <xref:Microsoft.SqlServer.Replication.PublicationMonitor.EnumTracerTokenHistory%2A> method.</span></span> <span data-ttu-id="4372c-192">5단계에서 삽입한 추적 프로그램 토큰에 대한 <xref:Microsoft.SqlServer.Replication.TracerToken.TracerTokenId%2A> 값을 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="4372c-192">Pass a value of <xref:Microsoft.SqlServer.Replication.TracerToken.TracerTokenId%2A> for a tracer token from step 5.</span></span> <span data-ttu-id="4372c-193">그러면 선택한 추적 프로그램 토큰에 대한 대기 시간 정보가 <xref:System.Data.DataSet> 개체로 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="4372c-193">This returns latency information for the selected tracer token as a <xref:System.Data.DataSet> object.</span></span> <span data-ttu-id="4372c-194">모든 추적 프로그램 토큰 정보가 반환되면 게시자와 배포자 간의 연결 및 배포자와 구독자 간의 연결이 모두 있으며 복제 토폴로지가 작동하고 있는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="4372c-194">If all tracer token information is returned, the connection between the Publisher and Distributor and the connection between the Distributor and the Subscriber both exist and the replication topology is functioning.</span></span>  
  
#### <a name="to-remove-tracer-tokens"></a><span data-ttu-id="4372c-195">추적 프로그램 토큰을 제거하려면</span><span class="sxs-lookup"><span data-stu-id="4372c-195">To remove tracer tokens</span></span>  
  
1.  <span data-ttu-id="4372c-196"><xref:Microsoft.SqlServer.Management.Common.ServerConnection> 클래스를 사용하여 배포자 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="4372c-196">Create a connection to the Distributor by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="4372c-197"><xref:Microsoft.SqlServer.Replication.PublicationMonitor> 클래스의 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="4372c-197">Create an instance of the <xref:Microsoft.SqlServer.Replication.PublicationMonitor> class.</span></span>  
  
3.  <span data-ttu-id="4372c-198"><xref:Microsoft.SqlServer.Replication.PublicationMonitor.Name%2A>, <xref:Microsoft.SqlServer.Replication.PublicationMonitor.DistributionDBName%2A>, <xref:Microsoft.SqlServer.Replication.PublicationMonitor.PublisherName%2A>및 <xref:Microsoft.SqlServer.Replication.PublicationMonitor.PublicationDBName%2A> 속성을 설정하고 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> 속성을 1단계에서 만든 연결로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="4372c-198">Set the <xref:Microsoft.SqlServer.Replication.PublicationMonitor.Name%2A>, <xref:Microsoft.SqlServer.Replication.PublicationMonitor.DistributionDBName%2A>, <xref:Microsoft.SqlServer.Replication.PublicationMonitor.PublisherName%2A>, and <xref:Microsoft.SqlServer.Replication.PublicationMonitor.PublicationDBName%2A> properties, and set the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property to the connection created in step 1.</span></span>  
  
4.  <span data-ttu-id="4372c-199"><xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> 메서드를 호출하여 개체 속성을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="4372c-199">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method to get the properties of the object.</span></span> <span data-ttu-id="4372c-200">이 메서드가 `false`를 반환하는 경우 3단계에서 게시 모니터 속성이 올바르게 정의되지 않았거나 해당 게시가 없는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="4372c-200">If this method returns `false`, either the publication monitor properties in step 3 were defined incorrectly or the publication does not exist.</span></span>  
  
5.  <span data-ttu-id="4372c-201"><xref:Microsoft.SqlServer.Replication.PublicationMonitor.EnumTracerTokens%2A> 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="4372c-201">Call the <xref:Microsoft.SqlServer.Replication.PublicationMonitor.EnumTracerTokens%2A> method.</span></span> <span data-ttu-id="4372c-202">반환된 <xref:System.Collections.ArrayList> 개체를 <xref:Microsoft.SqlServer.Replication.TracerToken> 개체의 배열로 캐스팅합니다.</span><span class="sxs-lookup"><span data-stu-id="4372c-202">Cast the returned <xref:System.Collections.ArrayList> object to an array of <xref:Microsoft.SqlServer.Replication.TracerToken> objects.</span></span>  
  
6.  <span data-ttu-id="4372c-203"><xref:Microsoft.SqlServer.Replication.PublicationMonitor.CleanUpTracerTokenHistory%2A> 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="4372c-203">Call the <xref:Microsoft.SqlServer.Replication.PublicationMonitor.CleanUpTracerTokenHistory%2A> method.</span></span> <span data-ttu-id="4372c-204">다음 값 중 하나를 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="4372c-204">Pass one of the following values:</span></span>  
  
    -   <span data-ttu-id="4372c-205">5단계에서 삽입한 추적 프로그램 토큰에 대한 <xref:Microsoft.SqlServer.Replication.TracerToken.TracerTokenId%2A> 입니다.</span><span class="sxs-lookup"><span data-stu-id="4372c-205">The <xref:Microsoft.SqlServer.Replication.TracerToken.TracerTokenId%2A> for a tracer token from step 5.</span></span> <span data-ttu-id="4372c-206">그러면 선택한 토큰에 대한 정보가 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="4372c-206">This deletes information for a selected token.</span></span>  
  
    -   <span data-ttu-id="4372c-207"><xref:System.DateTime> 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="4372c-207">A <xref:System.DateTime> object.</span></span> <span data-ttu-id="4372c-208">그러면 지정한 날짜보다 오래된 모든 토큰에 대한 정보가 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="4372c-208">This deletes information for all tokens older than the specified date and time.</span></span>  
  
###  <a name="PShellExample"></a>  
