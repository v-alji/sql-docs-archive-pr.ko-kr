---
title: 가용성 복제본 속성(일반 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 10/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.availabilityreplicaproperties.general.f1
ms.assetid: 8318fefb-e045-4fab-8507-e1951fc7cec6
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 313314baf009cdfb6109e63e9b65e369ac314f60
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741327"
---
# <a name="availability-replica-properties-general-page"></a><span data-ttu-id="575a6-102">가용성 복제본 속성(일반 페이지)</span><span class="sxs-lookup"><span data-stu-id="575a6-102">Availability Replica Properties (General Page)</span></span>
  <span data-ttu-id="575a6-103">이 대화 상자를 사용하여 가용성 복제본의 속성을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="575a6-103">Use this dialog box to viewthe properties of an availability replica.</span></span>  
  
## <a name="task-list"></a><span data-ttu-id="575a6-104">작업 목록</span><span class="sxs-lookup"><span data-stu-id="575a6-104">Task List</span></span>  
 <span data-ttu-id="575a6-105">**가용성 복제본 속성을 보려면**</span><span class="sxs-lookup"><span data-stu-id="575a6-105">**To view availability replica properties**</span></span>  
  
-   [<span data-ttu-id="575a6-106">가용성 복제본 속성 보기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="575a6-106">View Availability Replica Properties &#40;SQL Server&#41;</span></span>](view-availability-replica-properties-sql-server.md)  
  
-   [<span data-ttu-id="575a6-107">AlwaysOn 대시보드 사용&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="575a6-107">Use the AlwaysOn Dashboard &#40;SQL Server Management Studio&#41;</span></span>](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
## <a name="ui-element-list"></a><span data-ttu-id="575a6-108">UI 요소 목록</span><span class="sxs-lookup"><span data-stu-id="575a6-108">UI element list</span></span>  
 <span data-ttu-id="575a6-109">**가용성 그룹 이름**</span><span class="sxs-lookup"><span data-stu-id="575a6-109">**Availability group name**</span></span>  
 <span data-ttu-id="575a6-110">가용성 그룹의 이름으로,</span><span class="sxs-lookup"><span data-stu-id="575a6-110">Name of the availability group.</span></span> <span data-ttu-id="575a6-111">WSFC(Windows Server 장애 조치(failover) 클러스터) 내에서 고유해야 하는 사용자 지정 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="575a6-111">This is a user-specified name that must be unique within the Windows Server Failover Cluster (WSFC).</span></span>  
  
 <span data-ttu-id="575a6-112">**서버 인스턴스**</span><span class="sxs-lookup"><span data-stu-id="575a6-112">**Server instance**</span></span>  
 <span data-ttu-id="575a6-113">이 복제본을 호스팅하는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스의 서버 이름(기본 인스턴스가 아닌 경우에는 인스턴스 이름)입니다.</span><span class="sxs-lookup"><span data-stu-id="575a6-113">Server name of the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that is hosting this replica and, for a non-default instance, its instance name.</span></span>  
  
 <span data-ttu-id="575a6-114">**역할**</span><span class="sxs-lookup"><span data-stu-id="575a6-114">**Role**</span></span>  
 <span data-ttu-id="575a6-115">**주**</span><span class="sxs-lookup"><span data-stu-id="575a6-115">**Primary**</span></span>  
 <span data-ttu-id="575a6-116">현재 주 복제본입니다.</span><span class="sxs-lookup"><span data-stu-id="575a6-116">Currently the primary replica.</span></span>  
  
 <span data-ttu-id="575a6-117">**보조**</span><span class="sxs-lookup"><span data-stu-id="575a6-117">**Secondary**</span></span>  
 <span data-ttu-id="575a6-118">현재 보조 복제본입니다.</span><span class="sxs-lookup"><span data-stu-id="575a6-118">Currently a secondary replica.</span></span>  
  
 <span data-ttu-id="575a6-119">**확인**</span><span class="sxs-lookup"><span data-stu-id="575a6-119">**Resolving**</span></span>  
 <span data-ttu-id="575a6-120">현재 복제본 역할이 주 역할 또는 보조 역할로 확인 중입니다.</span><span class="sxs-lookup"><span data-stu-id="575a6-120">Currently the replica role is in the process of being resolved to either the primary or secondary role.</span></span>  
  
 <span data-ttu-id="575a6-121">**가용성 모드**</span><span class="sxs-lookup"><span data-stu-id="575a6-121">**Availability mode**</span></span>  
 <span data-ttu-id="575a6-122">복제본의 가용성 모드로,  다음 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="575a6-122">The availability mode of the replica, one of:</span></span>  
  
 <span data-ttu-id="575a6-123">**비동기 커밋**</span><span class="sxs-lookup"><span data-stu-id="575a6-123">**Asynchronous commit**</span></span>  
 <span data-ttu-id="575a6-124">주 복제본은 보조 복제본이 로그를 디스크에 쓸 때까지 기다리지 않고 트랜잭션을 커밋할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="575a6-124">The primary replica can commit transactions without waiting for the secondary to write the log to disk.</span></span>  
  
 <span data-ttu-id="575a6-125">**동기 커밋**</span><span class="sxs-lookup"><span data-stu-id="575a6-125">**Synchronous commit**</span></span>  
 <span data-ttu-id="575a6-126">주 복제본은 보조 복제본이 트랜잭션을 디스크에 쓸 때까지 기다렸다가 지정된 트랜잭션을 커밋합니다.</span><span class="sxs-lookup"><span data-stu-id="575a6-126">The primary replica waits to commit a given transaction until the secondary replica has written the transaction to disk.</span></span>  
  
 <span data-ttu-id="575a6-127">자세한 내용은 [가용성 모드 (AlwaysOn 가용성 그룹)](availability-modes-always-on-availability-groups.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="575a6-127">For more information, see [Availability Modes (AlwaysOn Availability Groups)](availability-modes-always-on-availability-groups.md).</span></span>  
  
 <span data-ttu-id="575a6-128">**Failover mode**</span><span class="sxs-lookup"><span data-stu-id="575a6-128">**Failover mode**</span></span>  
 <span data-ttu-id="575a6-129">복제본의 장애 조치(failover) 모드로, 다음 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="575a6-129">The failover mode of the replica, one of:</span></span>  
  
 <span data-ttu-id="575a6-130">**자동**</span><span class="sxs-lookup"><span data-stu-id="575a6-130">**Automatic**</span></span>  
 <span data-ttu-id="575a6-131">자동 장애 조치(failover).</span><span class="sxs-lookup"><span data-stu-id="575a6-131">Automatic failover.</span></span> <span data-ttu-id="575a6-132">복제본이 자동 장애 조치(failover)의 대상입니다.</span><span class="sxs-lookup"><span data-stu-id="575a6-132">The replica is a target for automatic failovers.</span></span> <span data-ttu-id="575a6-133">이 옵션은 가용성 모드가 동기 커밋으로 설정된 경우에만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="575a6-133">This is supported only if the availability mode is set to synchronous commit.</span></span>  
  
 <span data-ttu-id="575a6-134">**수동**</span><span class="sxs-lookup"><span data-stu-id="575a6-134">**Manual**</span></span>  
 <span data-ttu-id="575a6-135">수동 장애 조치(failover).</span><span class="sxs-lookup"><span data-stu-id="575a6-135">Manual failover.</span></span> <span data-ttu-id="575a6-136">데이터베이스 관리자가 복제본을 수동으로만 장애 조치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="575a6-136">The replica can only be failed over to manually by the database administrator.</span></span>  
  
 <span data-ttu-id="575a6-137">**주 역할의 연결 모드**</span><span class="sxs-lookup"><span data-stu-id="575a6-137">**Connections in primary role**</span></span>  
 <span data-ttu-id="575a6-138">복제본이 주 역할을 소유한 경우에 지원되는 클라이언트 연결 유형입니다.</span><span class="sxs-lookup"><span data-stu-id="575a6-138">The type of client connections supported when the replica owns the primary role.</span></span>  
  
 <span data-ttu-id="575a6-139">**모든 연결 허용**</span><span class="sxs-lookup"><span data-stu-id="575a6-139">**Allow all connections**</span></span>  
 <span data-ttu-id="575a6-140">주 복제본의 데이터베이스에 대한 모든 연결이 허용됩니다.</span><span class="sxs-lookup"><span data-stu-id="575a6-140">All connections are allowed to the databases in the primary replica.</span></span> <span data-ttu-id="575a6-141">이 값은 기본 설정입니다.</span><span class="sxs-lookup"><span data-stu-id="575a6-141">This is the default setting.</span></span>  
  
 <span data-ttu-id="575a6-142">**읽기/쓰기 연결 허용**</span><span class="sxs-lookup"><span data-stu-id="575a6-142">**Allow read/write connections**</span></span>  
 <span data-ttu-id="575a6-143">애플리케이션 의도 연결 속성이 **ReadOnly** 로 설정된 연결은 허용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="575a6-143">Connections where the Application Intent connection property is set to **ReadOnly** are disallowed.</span></span> <span data-ttu-id="575a6-144">애플리케이션 의도 속성이 **ReadWrite** 로 설정되었거나 애플리케이션 의도 연결 속성이 설정되지 않은 경우에는 연결이 허용됩니다.</span><span class="sxs-lookup"><span data-stu-id="575a6-144">When the Application Intent property is set to **ReadWrite** or the application intent connection property is not set, the connection is allowed.</span></span>  
  
 <span data-ttu-id="575a6-145">**읽기용 보조**</span><span class="sxs-lookup"><span data-stu-id="575a6-145">**Readable Secondary**</span></span>  
 <span data-ttu-id="575a6-146">보조 역할을 수행하는 가용성 복제본,  즉 보조 복제본이 클라이언트로부터의 연결을 허용할 수 있는지 여부를 나타내며,  다음 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="575a6-146">Whether an availability replica that is performing the secondary role (that is, a secondary replica) can accept connections from clients, one of:</span></span>  
  
 <span data-ttu-id="575a6-147">**아니요**</span><span class="sxs-lookup"><span data-stu-id="575a6-147">**No**</span></span>  
 <span data-ttu-id="575a6-148">이 복제본의 보조 데이터베이스에 대한 직접 연결이 허용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="575a6-148">No direct connections are allowed to secondary databases of this replica.</span></span> <span data-ttu-id="575a6-149">즉, 읽기 액세스가 가능하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="575a6-149">They are not available for read access.</span></span> <span data-ttu-id="575a6-150">이 값은 기본 설정입니다.</span><span class="sxs-lookup"><span data-stu-id="575a6-150">This is the default setting.</span></span>  
  
 <span data-ttu-id="575a6-151">**읽기 전용만**</span><span class="sxs-lookup"><span data-stu-id="575a6-151">**Read-intent only**</span></span>  
 <span data-ttu-id="575a6-152">이 복제본의 보조 데이터베이스에 대한 직접 읽기 전용 연결만 허용됩니다.</span><span class="sxs-lookup"><span data-stu-id="575a6-152">Only direct read-only connections are allowed to secondary databases of this replica.</span></span> <span data-ttu-id="575a6-153">즉, 모든 보조 데이터베이스에 대한 읽기 액세스가 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="575a6-153">The secondary database(s) are all available for read access.</span></span>  
  
 <span data-ttu-id="575a6-154">**예**</span><span class="sxs-lookup"><span data-stu-id="575a6-154">**Yes**</span></span>  
 <span data-ttu-id="575a6-155">이 복제본의 보조 데이터베이스에 대한 모든 연결이 허용되지만 읽기 액세스만 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="575a6-155">All connections are allowed to secondary databases of this replica, but only for read access.</span></span> <span data-ttu-id="575a6-156">즉, 모든 보조 데이터베이스에 대한 읽기 액세스가 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="575a6-156">The secondary database(s) are all available for read access.</span></span>  
  
 <span data-ttu-id="575a6-157">자세한 내용은 [활성 보조: 읽기 가능한 보조 복제본 (AlwaysOn 가용성 그룹)](active-secondaries-readable-secondary-replicas-always-on-availability-groups.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="575a6-157">For more information, see [Active Secondaries: Readable Secondary Replicas (AlwaysOn Availability Groups)](active-secondaries-readable-secondary-replicas-always-on-availability-groups.md).</span></span>  
  
 <span data-ttu-id="575a6-158">**세션 제한 시간(초)**</span><span class="sxs-lookup"><span data-stu-id="575a6-158">**Session timeout (seconds)**</span></span>  
 <span data-ttu-id="575a6-159">제한 시간(초)입니다.</span><span class="sxs-lookup"><span data-stu-id="575a6-159">The time-out period, in seconds.</span></span> <span data-ttu-id="575a6-160">제한 시간은 복제본이 주 복제본과 보조 복제본 간의 연결이 실패한 것으로 간주하기 전에 복제본에서 다른 복제본의 메시지를 받기 위해 기다리는 최대 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="575a6-160">The time-out period is the maximum time that the replica waits to receive a message from another replica before considering connection between the primary and secondary replica have failed.</span></span> <span data-ttu-id="575a6-161">세션 제한 시간은 보조 복제본이 주 복제본에 연결되어 있는지 여부를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="575a6-161">Session timeout detects whether secondaries are connected the primary replica.</span></span> <span data-ttu-id="575a6-162">실패한 보조 복제본 연결을 검색한 경우 주 복제본은 보조 복제본을 NOT_SYNCHRONIZED로 간주합니다.</span><span class="sxs-lookup"><span data-stu-id="575a6-162">On detecting a failed connection with a secondary replica, the primary replica considers the secondary replica to be NOT_SYNCHRONIZED.</span></span> <span data-ttu-id="575a6-163">주 복제본과의 실패한 연결을 검색할 경우 보조 복제본에서는 단순히 다시 연결을 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="575a6-163">On detecting a failed connection with the primary replica, a secondary replica simply attempts to reconnect.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="575a6-164">세션 제한 시간은 자동 장애 조치(failover)를 발생시키지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="575a6-164">Session timeouts do not cause automatic failovers.</span></span>  
  
 <span data-ttu-id="575a6-165">**엔드포인트 URL**</span><span class="sxs-lookup"><span data-stu-id="575a6-165">**Endpoint URL**</span></span>  
 <span data-ttu-id="575a6-166">데이터 동기화를 위해 주 복제본과 보조 복제본 간의 연결에 사용되는 사용자 지정 데이터베이스 미러링 엔드포인트의 문자열 표현입니다.</span><span class="sxs-lookup"><span data-stu-id="575a6-166">String representation of the user-specified database mirroring endpoint that is used by connections between primary and secondary replicas for data synchronization.</span></span> <span data-ttu-id="575a6-167">엔드포인트 URL의 구문에 대한 자세한 내용은 [가용성 복제본 추가 또는 수정 시 엔드포인트 URL 지정&#40;SQL Server&#41;](specify-endpoint-url-adding-or-modifying-availability-replica.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="575a6-167">For information about the syntax of endpoint URLs, see [Specify the Endpoint URL When Adding or Modifying an Availability Replica &#40;SQL Server&#41;](specify-endpoint-url-adding-or-modifying-availability-replica.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="575a6-168">참고 항목</span><span class="sxs-lookup"><span data-stu-id="575a6-168">See Also</span></span>  
 [<span data-ttu-id="575a6-169">AlwaysOn 가용성 그룹 &#40;SQL Server 개요&#41;</span><span class="sxs-lookup"><span data-stu-id="575a6-169">Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](overview-of-always-on-availability-groups-sql-server.md)  
  
  
