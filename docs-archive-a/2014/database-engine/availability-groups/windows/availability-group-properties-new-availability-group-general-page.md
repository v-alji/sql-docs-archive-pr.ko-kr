---
title: 가용성 그룹 속성 및 새 가용성 그룹 (일반 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.availabilitygroupproperties.general.f1
ms.assetid: 9af5379f-91b8-4729-9f75-4a80242a30e9
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 876b9d0948b7cd0d01c21b0ec1d64c51a55fa157
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646656"
---
# <a name="availability-group-properties-and-new-availability-group-general-page"></a><span data-ttu-id="357ca-102">가용성 그룹 속성 및 새 가용성 그룹(일반 페이지)</span><span class="sxs-lookup"><span data-stu-id="357ca-102">Availability Group Properties and New Availability Group (General Page)</span></span>
  <span data-ttu-id="357ca-103">이 항목은 **새 가용성 그룹** 대화 상자 및 **가용성 그룹 속성** 대화 상자의 **일반** 탭에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="357ca-103">This topic applies to the **General** tab of both the **New Availability Group** dialog box and the **Availability Group Properties** dialog box.</span></span>  <span data-ttu-id="357ca-104">**를 사용하지 않고** 새 가용성 그룹 [!INCLUDE[ssAoNewAgWiz](../../../includes/ssaonewagwiz-md.md)]대화 상자를 사용하여 새 가용성 그룹을 만들 수 있으며,</span><span class="sxs-lookup"><span data-stu-id="357ca-104">The **New Availability Group** dialog box enables you to create a new availability group without using the [!INCLUDE[ssAoNewAgWiz](../../../includes/ssaonewagwiz-md.md)].</span></span> <span data-ttu-id="357ca-105">**가용성 그룹 속성** 대화 상자를 사용하여 기존 가용성 그룹의 구성을 확인하고 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="357ca-105">The **Availability Group Properties** dialog box enables you to view and alter the configuration of an existing availability group.</span></span>  
  
 <span data-ttu-id="357ca-106">**가용성 그룹 속성을 보려면**</span><span class="sxs-lookup"><span data-stu-id="357ca-106">**To view availability group properties**</span></span>  
  
-   [<span data-ttu-id="357ca-107">가용성 그룹 속성 보기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="357ca-107">View Availability Group Properties &#40;SQL Server&#41;</span></span>](view-availability-group-properties-sql-server.md)  
  
-   [<span data-ttu-id="357ca-108">AlwaysOn 대시보드 사용&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="357ca-108">Use the AlwaysOn Dashboard &#40;SQL Server Management Studio&#41;</span></span>](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
## <a name="ui-element-list"></a><span data-ttu-id="357ca-109">UI 요소 목록</span><span class="sxs-lookup"><span data-stu-id="357ca-109">UI element list</span></span>  
 <span data-ttu-id="357ca-110">**가용성 그룹 이름**</span><span class="sxs-lookup"><span data-stu-id="357ca-110">**Availability group name**</span></span>  
 <span data-ttu-id="357ca-111">가용성 그룹의 이름으로,</span><span class="sxs-lookup"><span data-stu-id="357ca-111">Name of the availability group.</span></span> <span data-ttu-id="357ca-112">WSFC(Windows Server 장애 조치(failover) 클러스터) 내에서 고유해야 하는 사용자 지정 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="357ca-112">This is a user-specified name that must be unique within the Windows Server Failover Cluster (WSFC).</span></span>  
  
## <a name="availability-databases"></a><span data-ttu-id="357ca-113">가용성 데이터베이스</span><span class="sxs-lookup"><span data-stu-id="357ca-113">Availability Databases</span></span>  
 <span data-ttu-id="357ca-114">**데이터베이스 이름**</span><span class="sxs-lookup"><span data-stu-id="357ca-114">**Database Name**</span></span>  
 <span data-ttu-id="357ca-115">가용성 그룹에 추가된 데이터베이스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="357ca-115">Name of a database that has been added to the availability group.</span></span>  
  
 <span data-ttu-id="357ca-116">**추가**</span><span class="sxs-lookup"><span data-stu-id="357ca-116">**Add**</span></span>  
 <span data-ttu-id="357ca-117">가용성 그룹에 데이터베이스를 추가하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="357ca-117">Click to add a database to the availability group.</span></span>  
  
 <span data-ttu-id="357ca-118">**제거**</span><span class="sxs-lookup"><span data-stu-id="357ca-118">**Remove**</span></span>  
 <span data-ttu-id="357ca-119">가용성 그룹에서 선택된 데이터베이스를 제거하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="357ca-119">Click to remove a selected database from the availability group.</span></span>  
  
## <a name="availability-replicas"></a><span data-ttu-id="357ca-120">가용성 복제본</span><span class="sxs-lookup"><span data-stu-id="357ca-120">Availability Replicas</span></span>  
 <span data-ttu-id="357ca-121">**서버 인스턴스**</span><span class="sxs-lookup"><span data-stu-id="357ca-121">**Server instance**</span></span>  
 <span data-ttu-id="357ca-122">이 복제본을 호스팅하는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스의 서버 이름(기본 인스턴스가 아닌 경우에는 인스턴스 이름)입니다.</span><span class="sxs-lookup"><span data-stu-id="357ca-122">Server name of the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that is hosting this replica and, for a non-default instance, its instance name.</span></span>  
  
 <span data-ttu-id="357ca-123">**역할**</span><span class="sxs-lookup"><span data-stu-id="357ca-123">**Role**</span></span>  
 <span data-ttu-id="357ca-124">**주**</span><span class="sxs-lookup"><span data-stu-id="357ca-124">**Primary**</span></span>  
 <span data-ttu-id="357ca-125">현재 주 복제본입니다.</span><span class="sxs-lookup"><span data-stu-id="357ca-125">Currently the primary replica.</span></span>  
  
 <span data-ttu-id="357ca-126">**보조**</span><span class="sxs-lookup"><span data-stu-id="357ca-126">**Secondary**</span></span>  
 <span data-ttu-id="357ca-127">현재 보조 복제본입니다.</span><span class="sxs-lookup"><span data-stu-id="357ca-127">Currently a secondary replica.</span></span>  
  
 <span data-ttu-id="357ca-128">**확인**</span><span class="sxs-lookup"><span data-stu-id="357ca-128">**Resolving**</span></span>  
 <span data-ttu-id="357ca-129">현재 복제본 역할이 주 역할 또는 보조 역할로 확인 중입니다.</span><span class="sxs-lookup"><span data-stu-id="357ca-129">Currently the replica role is in the process of being resolved to either the primary or secondary role.</span></span>  
  
 <span data-ttu-id="357ca-130">**가용성 모드**</span><span class="sxs-lookup"><span data-stu-id="357ca-130">**Availability Mode**</span></span>  
 <span data-ttu-id="357ca-131">복제본의 가용성 모드로,  다음 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="357ca-131">The availability mode of the replica, one of:</span></span>  
  
 <span data-ttu-id="357ca-132">**비동기 커밋**</span><span class="sxs-lookup"><span data-stu-id="357ca-132">**Asynchronous commit**</span></span>  
 <span data-ttu-id="357ca-133">주 복제본은 보조 복제본이 로그를 디스크에 쓸 때까지 기다리지 않고 트랜잭션을 커밋할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="357ca-133">The primary replica can commit transactions without waiting for the secondary to write the log to disk.</span></span>  
  
 <span data-ttu-id="357ca-134">**동기 커밋**</span><span class="sxs-lookup"><span data-stu-id="357ca-134">**Synchronous commit**</span></span>  
 <span data-ttu-id="357ca-135">주 복제본은 보조 복제본이 트랜잭션을 디스크에 쓸 때까지 기다렸다가 지정된 트랜잭션을 커밋합니다.</span><span class="sxs-lookup"><span data-stu-id="357ca-135">The primary replica waits to commit a given transaction until the secondary replica has written the transaction to disk.</span></span>  
  
 <span data-ttu-id="357ca-136">자세한 내용은 [가용성 모드 (AlwaysOn 가용성 그룹)](availability-modes-always-on-availability-groups.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="357ca-136">For more information, see [Availability Modes (AlwaysOn Availability Groups)](availability-modes-always-on-availability-groups.md).</span></span>  
  
 <span data-ttu-id="357ca-137">**장애 조치(Failover) 모드**</span><span class="sxs-lookup"><span data-stu-id="357ca-137">**Failover Mode**</span></span>  
 <span data-ttu-id="357ca-138">복제본의 장애 조치(failover) 모드로, 다음 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="357ca-138">The failover mode of the replica, one of:</span></span>  
  
 <span data-ttu-id="357ca-139">**자동**</span><span class="sxs-lookup"><span data-stu-id="357ca-139">**Automatic**</span></span>  
 <span data-ttu-id="357ca-140">자동 장애 조치(failover).</span><span class="sxs-lookup"><span data-stu-id="357ca-140">Automatic failover.</span></span> <span data-ttu-id="357ca-141">복제본이 자동 장애 조치(failover)의 대상입니다.</span><span class="sxs-lookup"><span data-stu-id="357ca-141">The replica is a target for automatic failovers.</span></span> <span data-ttu-id="357ca-142">이 옵션은 가용성 모드가 동기 커밋으로 설정된 경우에만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="357ca-142">This is supported only if the availability mode is set to synchronous commit.</span></span>  
  
 <span data-ttu-id="357ca-143">**수동**</span><span class="sxs-lookup"><span data-stu-id="357ca-143">**Manual**</span></span>  
 <span data-ttu-id="357ca-144">수동 장애 조치(failover).</span><span class="sxs-lookup"><span data-stu-id="357ca-144">Manual failover.</span></span> <span data-ttu-id="357ca-145">데이터베이스 관리자가 복제본을 수동으로만 장애 조치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="357ca-145">The replica can only be failed over to manually by the database administrator.</span></span>  
  
 <span data-ttu-id="357ca-146">**주 역할의 연결 모드**</span><span class="sxs-lookup"><span data-stu-id="357ca-146">**Connections in Primary Role**</span></span>  
 <span data-ttu-id="357ca-147">복제본이 주 역할을 소유한 경우에 지원되는 클라이언트 연결 유형입니다.</span><span class="sxs-lookup"><span data-stu-id="357ca-147">The type of client connections supported when the replica owns the primary role.</span></span>  
  
 <span data-ttu-id="357ca-148">**모든 연결 허용**</span><span class="sxs-lookup"><span data-stu-id="357ca-148">**Allow all connections**</span></span>  
 <span data-ttu-id="357ca-149">주 복제본의 데이터베이스에 대한 모든 연결이 허용됩니다.</span><span class="sxs-lookup"><span data-stu-id="357ca-149">All connections are allowed to the databases in the primary replica.</span></span> <span data-ttu-id="357ca-150">이 값은 기본 설정입니다.</span><span class="sxs-lookup"><span data-stu-id="357ca-150">This is the default setting.</span></span>  
  
 <span data-ttu-id="357ca-151">**읽기/쓰기 연결 허용**</span><span class="sxs-lookup"><span data-stu-id="357ca-151">**Allow read/write connections**</span></span>  
 <span data-ttu-id="357ca-152">애플리케이션 의도 연결 속성이 **ReadOnly** 로 설정된 연결은 허용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="357ca-152">Connections where the Application Intent connection property is set to **ReadOnly** are disallowed.</span></span> <span data-ttu-id="357ca-153">애플리케이션 의도 속성이 **ReadWrite** 로 설정되었거나 애플리케이션 의도 연결 속성이 설정되지 않은 경우에는 연결이 허용됩니다.</span><span class="sxs-lookup"><span data-stu-id="357ca-153">When the Application Intent property is set to **ReadWrite** or the Application Intent connection property is not set, the connection is allowed.</span></span> <span data-ttu-id="357ca-154">애플리케이션 의도 연결 속성에 대한 자세한 내용은 [Using Connection String Keywords with SQL Server Native Client](../../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="357ca-154">For more information about Application Intent connection property, see [Using Connection String Keywords with SQL Server Native Client](../../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md).</span></span>  
  
 <span data-ttu-id="357ca-155">**읽기용 보조**</span><span class="sxs-lookup"><span data-stu-id="357ca-155">**Readable Secondary**</span></span>  
 <span data-ttu-id="357ca-156">보조 역할을 수행하는 가용성 복제본,  즉 보조 복제본이 클라이언트로부터의 연결을 허용할 수 있는지 여부를 나타내며,  다음 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="357ca-156">Whether an availability replica that is performing the secondary role (that is, a secondary replica) can accept connections from clients, one of:</span></span>  
  
 <span data-ttu-id="357ca-157">**아니요**</span><span class="sxs-lookup"><span data-stu-id="357ca-157">**No**</span></span>  
 <span data-ttu-id="357ca-158">이 복제본의 보조 데이터베이스에 대한 직접 연결이 허용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="357ca-158">No direct connections are allowed to secondary databases of this replica.</span></span> <span data-ttu-id="357ca-159">즉, 읽기 액세스가 가능하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="357ca-159">They are not available for read access.</span></span> <span data-ttu-id="357ca-160">이 값은 기본 설정입니다.</span><span class="sxs-lookup"><span data-stu-id="357ca-160">This is the default setting.</span></span>  
  
 <span data-ttu-id="357ca-161">**읽기 전용만**</span><span class="sxs-lookup"><span data-stu-id="357ca-161">**Read-intent only**</span></span>  
 <span data-ttu-id="357ca-162">이 복제본의 보조 데이터베이스에 대한 직접 읽기 전용 연결만 허용됩니다.</span><span class="sxs-lookup"><span data-stu-id="357ca-162">Only direct read-only connections are allowed to secondary databases of this replica.</span></span> <span data-ttu-id="357ca-163">즉, 모든 보조 데이터베이스에 대한 읽기 액세스가 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="357ca-163">The secondary database(s) are all available for read access.</span></span>  
  
 <span data-ttu-id="357ca-164">**예**</span><span class="sxs-lookup"><span data-stu-id="357ca-164">**Yes**</span></span>  
 <span data-ttu-id="357ca-165">이 복제본의 보조 데이터베이스에 대한 모든 연결이 허용되지만 읽기 액세스만 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="357ca-165">All connections are allowed to secondary databases of this replica, but only for read access.</span></span> <span data-ttu-id="357ca-166">즉, 모든 보조 데이터베이스에 대한 읽기 액세스가 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="357ca-166">The secondary database(s) are all available for read access.</span></span>  
  
 <span data-ttu-id="357ca-167">**세션 제한 시간(초)**</span><span class="sxs-lookup"><span data-stu-id="357ca-167">**Session Timeout (seconds)**</span></span>  
 <span data-ttu-id="357ca-168">이 복제본에 대한 세션 제한 시간(초)입니다.</span><span class="sxs-lookup"><span data-stu-id="357ca-168">The number of seconds for the session-timeout period on this replica.</span></span>  
  
 <span data-ttu-id="357ca-169">**엔드포인트 URL**</span><span class="sxs-lookup"><span data-stu-id="357ca-169">**Endpoint URL**</span></span>  
 <span data-ttu-id="357ca-170">엔드포인트의 URL입니다.</span><span class="sxs-lookup"><span data-stu-id="357ca-170">The URL of the endpoint.</span></span> <span data-ttu-id="357ca-171">이러한 URL 형식에 대한 자세한 내용은 [가용성 복제본 추가 또는 수정 시 엔드포인트 URL 지정&#40;SQL Server&#41;](specify-endpoint-url-adding-or-modifying-availability-replica.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="357ca-171">For information the format of these URLs, see [Specify the Endpoint URL When Adding or Modifying an Availability Replica &#40;SQL Server&#41;](specify-endpoint-url-adding-or-modifying-availability-replica.md).</span></span>  
  
 <span data-ttu-id="357ca-172">**추가**</span><span class="sxs-lookup"><span data-stu-id="357ca-172">**Add**</span></span>  
 <span data-ttu-id="357ca-173">가용성 그룹에 보조 복제본을 추가하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="357ca-173">Click to add a secondary replica to the availability group.</span></span>  
  
 <span data-ttu-id="357ca-174">**제거**</span><span class="sxs-lookup"><span data-stu-id="357ca-174">**Remove**</span></span>  
 <span data-ttu-id="357ca-175">보조 복제본을 가용성 그룹에서 제거하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="357ca-175">Click to remove a secondary replica from the availability group.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="357ca-176">참고 항목</span><span class="sxs-lookup"><span data-stu-id="357ca-176">See Also</span></span>  
 [<span data-ttu-id="357ca-177">AlwaysOn 가용성 그룹 &#40;SQL Server 개요&#41;</span><span class="sxs-lookup"><span data-stu-id="357ca-177">Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](overview-of-always-on-availability-groups-sql-server.md)  
  
  
