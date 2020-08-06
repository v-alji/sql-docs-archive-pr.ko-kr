---
title: 미러링 상태(SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- states [SQL Server], database mirroring
- PENDING_FAILOVER state
- mirroring states [SQL Server]
- DISCONNECTED state
- SYNCHRONIZING state
- SYNCHRONIZED state
- SUSPENDED state
- database mirroring [SQL Server], states
ms.assetid: 90062917-74f9-471b-b49e-bc153ae1a468
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: d458939ba233bdfe7a99edd38afc74b5433ae061
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647192"
---
# <a name="mirroring-states-sql-server"></a><span data-ttu-id="b7e97-102">미러링 상태(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="b7e97-102">Mirroring States (SQL Server)</span></span>
  <span data-ttu-id="b7e97-103">데이터베이스 미러링 세션 동안 미러된 데이터베이스는 항상 특정 상태( *미러링 상태*)가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b7e97-103">During a database mirroring session, the mirrored database is always in a specific state (the *mirroring state*).</span></span> <span data-ttu-id="b7e97-104">이러한 데이터베이스의 상태는 통신 상태, 데이터 흐름 및 파트너 간의 데이터 차이를 반영합니다.</span><span class="sxs-lookup"><span data-stu-id="b7e97-104">The state of the database reflects the communication status, data flow, and the difference in data between the partners.</span></span> <span data-ttu-id="b7e97-105">데이터베이스 미러링 세션은 주 데이터베이스와 같은 상태가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b7e97-105">The database mirroring session adopts the same state as the principal database.</span></span>  
  
 <span data-ttu-id="b7e97-106">데이터베이스 미러링 세션 동안 서버 인스턴스는 서로를 모니터링합니다.</span><span class="sxs-lookup"><span data-stu-id="b7e97-106">Throughout a database mirroring session, the server instances monitor each other.</span></span> <span data-ttu-id="b7e97-107">파트너는 미러링 상태를 사용하여 데이터베이스를 모니터링합니다.</span><span class="sxs-lookup"><span data-stu-id="b7e97-107">The partners use the mirroring state to monitor the database.</span></span> <span data-ttu-id="b7e97-108">PENDING_FAILOVER 상태를 제외하고 주 데이터베이스와 미러 데이터베이스는 항상 동일한 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="b7e97-108">With the exception of the PENDING_FAILOVER state, the principal and mirror database are always in the same state.</span></span> <span data-ttu-id="b7e97-109">세션에 미러링 모니터 서버가 설정되어 있으면 각 파트너는 연결 상태(CONNECTED 또는 DISCONNECTED)를 사용하여 미러링 모니터 서버를 모니터링합니다.</span><span class="sxs-lookup"><span data-stu-id="b7e97-109">If a witness is set for the session, each of the partners monitors the witness using its connection state (CONNECTED or DISCONNECTED).</span></span>  
  
 <span data-ttu-id="b7e97-110">가능한 데이터베이스 미러링 상태는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="b7e97-110">The possible mirroring states of the database are as follows:</span></span>  
  
|<span data-ttu-id="b7e97-111">미러링 상태</span><span class="sxs-lookup"><span data-stu-id="b7e97-111">Mirroring state</span></span>|<span data-ttu-id="b7e97-112">Description</span><span class="sxs-lookup"><span data-stu-id="b7e97-112">Description</span></span>|  
|---------------------|-----------------|  
|<span data-ttu-id="b7e97-113">SYNCHRONIZING</span><span class="sxs-lookup"><span data-stu-id="b7e97-113">SYNCHRONIZING</span></span>|<span data-ttu-id="b7e97-114">미러 데이터베이스의 내용이 주 데이터베이스의 내용보다 오래된 것입니다.</span><span class="sxs-lookup"><span data-stu-id="b7e97-114">The contents of the mirror database are lagging behind the contents of the principal database.</span></span> <span data-ttu-id="b7e97-115">주 서버에서 로그 레코드를 미러 서버로 보내면 미러 서버에서 변경 내용을 미러 데이터베이스에 적용하여 롤포워드합니다.</span><span class="sxs-lookup"><span data-stu-id="b7e97-115">The principal server is sending log records to the mirror server, which is applying the changes to the mirror database to roll it forward.</span></span><br /><br /> <span data-ttu-id="b7e97-116">데이터베이스 미러링 세션의 시작 부분에서는 데이터베이스가 SYNCHRONIZING 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="b7e97-116">At the start of a database mirroring session, the database is in the SYNCHRONIZING state.</span></span> <span data-ttu-id="b7e97-117">주 서버에서 데이터베이스를 제공하고 미러 서버는 계속 동기화를 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="b7e97-117">The principal server is serving the database, and the mirror is trying to catch up.</span></span>|  
|<span data-ttu-id="b7e97-118">SYNCHRONIZED</span><span class="sxs-lookup"><span data-stu-id="b7e97-118">SYNCHRONIZED</span></span>|<span data-ttu-id="b7e97-119">미러 서버가 주 서버와 충분히 동기화되면 미러링 상태가 SYNCHRONIZED로 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="b7e97-119">When the mirror server becomes sufficiently caught up to the principal server, the mirroring state changes to SYNCHRONIZED.</span></span> <span data-ttu-id="b7e97-120">주 서버에서 계속 변경 내용을 미러 서버로 보내고 미러 서버에서 계속 변경 내용을 미러 데이터베이스에 적용하면 데이터베이스는 이 상태로 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="b7e97-120">The database remains in this state as long as the principal server continues to send changes to the mirror server and the mirror server continues to apply changes to the mirror database.</span></span><br /><br /> <span data-ttu-id="b7e97-121">트랜잭션 보안을 FULL로 설정하면 SYNCHRONIZED 상태에서 자동 장애 조치(Failover)와 수동 장애 조치가 모두 지원되며 장애 조치 후 데이터가 손실되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b7e97-121">If transaction safety is set to FULLautomatic failover and manual failover are both supported in the SYNCHRONIZED state, there is no data loss after a failover.</span></span><br /><br /> <span data-ttu-id="b7e97-122">트랜잭션 보안을 해제하면 SYNCHRONIZED 상태에서도 항상 일부 데이터가 손실될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b7e97-122">If transaction safety is off, some data loss is always possible, even in the SYNCHRONIZED state.</span></span>|  
|<span data-ttu-id="b7e97-123">SUSPENDED</span><span class="sxs-lookup"><span data-stu-id="b7e97-123">SUSPENDED</span></span>|<span data-ttu-id="b7e97-124">데이터베이스의 미러 복사본을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b7e97-124">The mirror copy of the database is not available.</span></span> <span data-ttu-id="b7e97-125">주 데이터베이스가 미러 서버에 로그를 보내지 않은 상태로 실행되고 있으며 이러한 상태를 *노출 실행*이라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7e97-125">The principal database is running without sending any logs to the mirror server, a condition known as *running exposed*.</span></span> <span data-ttu-id="b7e97-126">이는 장애 조치(Failover) 이후의 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="b7e97-126">This is the state after a failover.</span></span><br /><br /> <span data-ttu-id="b7e97-127">다시 실행 오류가 발생하거나 관리자가 세션을 일시 중지한 경우에도 세션이 SUSPENDED 상태가 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b7e97-127">A session can also become SUSPENDED as a result of redo errors or if the administrator pauses the session.</span></span><br /><br /> <span data-ttu-id="b7e97-128">SUSPENDED는 파트너 종료 및 시작 후에도 유지되는 영구 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="b7e97-128">SUSPENDED is a persistent state that survives partner shutdowns and startups.</span></span>|  
|<span data-ttu-id="b7e97-129">PENDING_FAILOVER</span><span class="sxs-lookup"><span data-stu-id="b7e97-129">PENDING_FAILOVER</span></span>|<span data-ttu-id="b7e97-130">이 상태는 장애 조치가 시작되었지만 미러 역할로 전환되지 않은 주 서버에서만 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="b7e97-130">This state is found only on the principal server after a failover has begun, but the server has not transitioned into the mirror role.</span></span><br /><br /> <span data-ttu-id="b7e97-131">장애 조치가 시작되면 주 데이터베이스는 PENDING_FAILOVER 상태가 되고 모든 사용자 연결을 신속하게 종료한 후 즉시 미러 역할을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="b7e97-131">When the failover is initiated, the principal database goes into the PENDING_FAILOVER state, quickly terminates any user connections, and takes over the mirror role soon thereafter.</span></span>|  
|<span data-ttu-id="b7e97-132">DISCONNECTED</span><span class="sxs-lookup"><span data-stu-id="b7e97-132">DISCONNECTED</span></span>|<span data-ttu-id="b7e97-133">해당 파트너와 다른 파트너의 통신이 끊어진 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="b7e97-133">The partner has lost communication with the other partner.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b7e97-134">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b7e97-134">See Also</span></span>  
 [<span data-ttu-id="b7e97-135">데이터베이스 미러링 모니터링&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="b7e97-135">Monitoring Database Mirroring &#40;SQL Server&#41;</span></span>](database-mirroring-sql-server.md)  
  
  
