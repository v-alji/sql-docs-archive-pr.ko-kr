---
title: 게시 정보, 추적 프로그램 토큰 (트랜잭션 게시, SQL Server 2005 이상) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.publicationinfo.tracertokens.f1
ms.assetid: a115ba95-17ae-45df-91bd-5a1a35f3745f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: af84ab9b9122a55367780976056ce95aa597f62a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736176"
---
# <a name="publication-information-tracer-tokens-transactional-publication-sql-server-2005-and-later"></a><span data-ttu-id="7d1f6-102">게시 정보, 추적 프로그램 토큰(트랜잭션 게시, SQL Server 2005 이상)</span><span class="sxs-lookup"><span data-stu-id="7d1f6-102">Publication Information, Tracer Tokens (Transactional Publication, SQL Server 2005 and Later)</span></span>
  <span data-ttu-id="7d1f6-103">**추적 프로그램 토큰** 탭을 사용하여 연결 유효성을 검사하고 트랜잭션 복제를 사용하는 시스템의 대기 시간을 측정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d1f6-103">The **Tracer Tokens** tab allows you to validate connections and to measure the latency of a system that uses transactional replication.</span></span> <span data-ttu-id="7d1f6-104">토큰(적은 양의 데이터)은 게시 데이터베이스의 트랜잭션 로그에 기록되고, 일반적인 복제된 트랜잭션인 것처럼 표시되고, 시스템을 통해 전달되며 다음을 계산할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d1f6-104">A token (a small amount of data) is written to the transaction log of the publication database, marked as though it were a typical replicated transaction, and sent through the system, allowing a calculation of:</span></span>  
  
-   <span data-ttu-id="7d1f6-105">게시자에서 커밋된 트랜잭션과 배포자의 배포 데이터베이스에서 삽입된 해당 명령 사이의 경과 시간</span><span class="sxs-lookup"><span data-stu-id="7d1f6-105">How much time elapses between a transaction being committed at the Publisher and the corresponding command being inserted in the distribution database at the Distributor.</span></span>  
  
-   <span data-ttu-id="7d1f6-106">배포 데이터베이스에 삽입된 명령과 구독자에서 커밋된 해당 트랜잭션 사이의 경과 시간</span><span class="sxs-lookup"><span data-stu-id="7d1f6-106">How much time elapses between a command being inserted in the distribution database and the corresponding transaction being committed at a Subscriber.</span></span>  
  
 <span data-ttu-id="7d1f6-107">이러한 계산을 잘 검토하면 다음을 비롯한 여러 가지 질문에 대답할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d1f6-107">From these calculations, you can answer a number of questions, including:</span></span>  
  
-   <span data-ttu-id="7d1f6-108">게시자의 변경 내용을 받는 데 가장 오래 걸리는 구독자는 무엇입니까?</span><span class="sxs-lookup"><span data-stu-id="7d1f6-108">Which Subscribers take the longest to receive a change from the Publisher?</span></span>  
  
-   <span data-ttu-id="7d1f6-109">추적 프로그램 토큰을 받아야 할 구독자가 있습니까? 있다면 아직 추적 프로그램 토큰을 받지 못한 구독자는 무엇입니까?</span><span class="sxs-lookup"><span data-stu-id="7d1f6-109">Of the Subscribers expected to receive the tracer token, which, if any, have not received it?</span></span>  
  
## <a name="options"></a><span data-ttu-id="7d1f6-110">옵션</span><span class="sxs-lookup"><span data-stu-id="7d1f6-110">Options</span></span>  
 <span data-ttu-id="7d1f6-111">표에서 데이터를 표시하는 방식을 변경하려면 표를 마우스 오른쪽 단추로 클릭한 후 다음 옵션 중 하나를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7d1f6-111">To change the way that the grid displays data, right-click the grid, and then click one of the following options:</span></span>  
  
-   <span data-ttu-id="7d1f6-112">**정렬**: **열 정렬** 대화 상자에서 한 개 이상의 열에 대해 정렬합니다.</span><span class="sxs-lookup"><span data-stu-id="7d1f6-112">**Sort**: Sort on one or more columns in the **Sort Columns** dialog box.</span></span>  
  
-   <span data-ttu-id="7d1f6-113">**표시할 열 선택**: **열 선택** 대화 상자에서 표시할 열 및 해당 열이 표시되는 순서를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="7d1f6-113">**Choose Columns to Show**: Select which columns to display and the order in which to display them in the **Choose Columns** dialog box.</span></span>  
  
-   <span data-ttu-id="7d1f6-114">**필터**: **필터 설정** 대화 상자의 열 값에 따라 표의 행을 필터링합니다.</span><span class="sxs-lookup"><span data-stu-id="7d1f6-114">**Filter**: Filter rows in the grid based on column values in the **Filter Settings** dialog box.</span></span>  
  
-   <span data-ttu-id="7d1f6-115">**필터 지우기**: 표에 대한 모든 필터 설정을 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="7d1f6-115">**Clear Filter**: Clear any filter settings for the grid.</span></span>  
  
 <span data-ttu-id="7d1f6-116">필터 설정은 각 표에 대해 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="7d1f6-116">Filter settings are specific to each grid.</span></span> <span data-ttu-id="7d1f6-117">열 선택 및 정렬은 각 게시자에 대한 게시 표와 같이 동일한 유형의 모든 표에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="7d1f6-117">Column selection and sorting are applied to all grids of the same type, such as the publications grid for each Publisher.</span></span>  
  
 <span data-ttu-id="7d1f6-118">**추적 프로그램 삽입**</span><span class="sxs-lookup"><span data-stu-id="7d1f6-118">**Insert Tracer**</span></span>  
 <span data-ttu-id="7d1f6-119">게시자에서 트랜잭션 로그에 추적 프로그램 토큰을 삽입하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7d1f6-119">Click to insert a tracer token in the transaction log at the Publisher.</span></span>  
  
 <span data-ttu-id="7d1f6-120">**삽입된 시간**</span><span class="sxs-lookup"><span data-stu-id="7d1f6-120">**Time inserted**</span></span>  
 <span data-ttu-id="7d1f6-121">추적 프로그램 토큰이 삽입된 시간을 선택하여 해당 시간의 대기 시간 정보를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="7d1f6-121">Select a time at which a tracer token was inserted to display latency information from that time.</span></span> <span data-ttu-id="7d1f6-122">기본적으로 가장 최근 시간의 정보가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="7d1f6-122">By default, information from the most recent time is displayed.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7d1f6-123">추적 프로그램 토큰 정보는 배포 데이터베이스의 기록 보존 기간에 의해 제어되는 다른 기록 데이터와 같은 시간 동안 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="7d1f6-123">Tracer token information is retained for the same time period as other historical data, which is governed by the history retention period of the distribution database.</span></span> <span data-ttu-id="7d1f6-124">배포 데이터베이스 속성 변경에 대한 자세한 내용은 [게시자 및 배포자 속성 보기 및 수정](view-and-modify-distributor-and-publisher-properties.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7d1f6-124">For information about changing distribution database properties, see [View and Modify Distributor and Publisher Properties](view-and-modify-distributor-and-publisher-properties.md).</span></span>  
  
 <span data-ttu-id="7d1f6-125">**구독**</span><span class="sxs-lookup"><span data-stu-id="7d1f6-125">**Subscription**</span></span>  
 <span data-ttu-id="7d1f6-126">게시에 대한 각 구독의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="7d1f6-126">The name of each subscription to the publication.</span></span>  
  
 <span data-ttu-id="7d1f6-127">**게시자에서 배포자로 연결**</span><span class="sxs-lookup"><span data-stu-id="7d1f6-127">**Publisher to Distributor**</span></span>  
 <span data-ttu-id="7d1f6-128">게시자에서 트랜잭션이 커밋되는 시점과 배포자에서 배포 데이터베이스에 해당 명령이 삽입되는 시점 간에 경과한 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="7d1f6-128">The elapsed time between a transaction being committed at the Publisher and the corresponding command being inserted in the distribution database at the Distributor.</span></span> <span data-ttu-id="7d1f6-129">값 **보류 중** 은 토큰이 배포자에 아직 도달하지 않았음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="7d1f6-129">A value of **Pending** indicates that the token has not yet reached the Distributor.</span></span> <span data-ttu-id="7d1f6-130">보류 상태가 지속되면 로그 판독기 에이전트가 실행 중인지 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="7d1f6-130">If the pending state persists, ensure that the Log Reader Agent is running.</span></span>  
  
 <span data-ttu-id="7d1f6-131">**배포자에서 구독자로 연결**</span><span class="sxs-lookup"><span data-stu-id="7d1f6-131">**Distributor to Subscriber**</span></span>  
 <span data-ttu-id="7d1f6-132">배포 데이터베이스에 명령이 삽입되는 시점과 구독자에서 해당 트랜잭션이 커밋되는 시점 간에 경과한 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="7d1f6-132">The elapsed time between a command being inserted in the distribution database and the corresponding transaction being committed at a Subscriber.</span></span> <span data-ttu-id="7d1f6-133">값 **보류 중** 은 토큰이 구독자에 아직 도달하지 않았음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="7d1f6-133">A value of **Pending** indicates that the token has not yet reached the Subscriber.</span></span> <span data-ttu-id="7d1f6-134">보류 상태가 지속되면 배포 에이전트가 실행 중인지 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="7d1f6-134">If the pending state persists, ensure that the Distribution Agent is running.</span></span>  
  
 <span data-ttu-id="7d1f6-135">**총 대기 시간**</span><span class="sxs-lookup"><span data-stu-id="7d1f6-135">**Total Latency**</span></span>  
 <span data-ttu-id="7d1f6-136">게시자에서 트랜잭션이 커밋되는 시점과 구독자에서 해당 트랜잭션이 커밋되는 시점 간에 경과한 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="7d1f6-136">The elapsed time between a transaction being committed at the Publisher and the corresponding transaction being committed at the Subscriber.</span></span> <span data-ttu-id="7d1f6-137">이 시간은 현재 이 구독자에 대한 복제 시스템의 엔드투엔드 대기 시간을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="7d1f6-137">This represents the end-to-end latency of the replication system for this Subscriber at this time.</span></span> <span data-ttu-id="7d1f6-138">값 **보류 중** 은 토큰이 구독자에 아직 도달하지 않았음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="7d1f6-138">A value of **Pending** indicates that the token has not yet reached the Subscriber.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d1f6-139">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7d1f6-139">See Also</span></span>  
 <span data-ttu-id="7d1f6-140">[복제 에이전트 시작 및 중지&#40;SQL Server Management Studio&#41;](agents/start-and-stop-a-replication-agent-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="7d1f6-140">[Start and Stop a Replication Agent &#40;SQL Server Management Studio&#41;](agents/start-and-stop-a-replication-agent-sql-server-management-studio.md) </span></span>  
 <span data-ttu-id="7d1f6-141">[복제 모니터 시작](monitor/start-the-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="7d1f6-141">[Start the Replication Monitor](monitor/start-the-replication-monitor.md) </span></span>  
 <span data-ttu-id="7d1f6-142">[트랜잭션 복제에 대 한 대기 시간 측정 및 연결 유효성 검사](monitor/measure-latency-and-validate-connections-for-transactional-replication.md) </span><span class="sxs-lookup"><span data-stu-id="7d1f6-142">[Measure Latency and Validate Connections for Transactional Replication](monitor/measure-latency-and-validate-connections-for-transactional-replication.md) </span></span>  
 <span data-ttu-id="7d1f6-143">[복제 모니터를 사용 하 여 성능 모니터링](monitor/monitor-performance-with-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="7d1f6-143">[Monitor Performance with Replication Monitor](monitor/monitor-performance-with-replication-monitor.md) </span></span>  
 <span data-ttu-id="7d1f6-144">[복제 모니터링](monitoring-replication.md) </span><span class="sxs-lookup"><span data-stu-id="7d1f6-144">[Monitoring Replication](monitoring-replication.md) </span></span>  
 [<span data-ttu-id="7d1f6-145">복제 에이전트 개요</span><span class="sxs-lookup"><span data-stu-id="7d1f6-145">Replication Agents Overview</span></span>](agents/replication-agents-overview.md)  
  
  
