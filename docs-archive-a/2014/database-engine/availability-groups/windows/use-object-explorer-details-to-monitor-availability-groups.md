---
title: 개체 탐색기 세부 정보를 사용 하 여 가용성 그룹을 모니터링 합니다 (SQL Server Management Studio). Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.availabilitygroup.OEdetails.f1
helpviewer_keywords:
- Availability Groups [SQL Server], monitoring
- Availability Groups [SQL Server], databases
- Availability Groups [SQL Server]
ms.assetid: 84affc47-40e0-43d9-855e-468967068c35
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 419f1cd22e0a7aa314f6a1036793091bb7b385fc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647239"
---
# <a name="use-the-object-explorer-details-to-monitor-availability-groups-sql-server-management-studio"></a><span data-ttu-id="5d171-102">개체 탐색기 정보를 사용하여 가용성 그룹 모니터링(SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="5d171-102">Use the Object Explorer Details to Monitor Availability Groups (SQL Server Management Studio)</span></span>
  <span data-ttu-id="5d171-103">이 항목에서는 **의** 개체 탐색기 정보 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 창을 사용하여 기존 AlwaysOn 가용성 그룹, 가용성 복제본 및 가용성 데이터베이스를 모니터링하고 관리하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="5d171-103">This topic describes how to use the **Object Explorer Details** pane of [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] to monitor and manage existing AlwaysOn availability groups, availability replicas, and availability databases.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5d171-104">개체 탐색기 정보 창을 사용하는 방법은 [개체 탐색기 정보 창](../../../ssms/object/object-explorer-details-pane.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5d171-104">For information about using the Object Explorer Details pane, see [Object Explorer Details Pane](../../../ssms/object/object-explorer-details-pane.md).</span></span>  
  
-   <span data-ttu-id="5d171-105">**시작하기 전 주의 사항:**  [필수 구성 요소](#Prerequisites)</span><span class="sxs-lookup"><span data-stu-id="5d171-105">**Before you begin:**  [Prerequisites](#Prerequisites)</span></span>  
  
-   <span data-ttu-id="5d171-106">**가용성 그룹을 모니터링하려면**  [SQL Server Management Studio](#SSMSProcedure)</span><span class="sxs-lookup"><span data-stu-id="5d171-106">**To Monitor an Availability Group, using:**  [SQL Server Management Studio](#SSMSProcedure)</span></span>  
  
-   <span data-ttu-id="5d171-107">**개체 탐색기 세부 정보:**</span><span class="sxs-lookup"><span data-stu-id="5d171-107">**Object Explorer Details:**</span></span>  
  
     [<span data-ttu-id="5d171-108">가용성 그룹 정보</span><span class="sxs-lookup"><span data-stu-id="5d171-108">Availability Group Details</span></span>](#AvGroupsDetails)  
  
     [<span data-ttu-id="5d171-109">가용성 복제본 정보</span><span class="sxs-lookup"><span data-stu-id="5d171-109">Availability Replica Details</span></span>](#AvReplicaDetails)  
  
     [<span data-ttu-id="5d171-110">가용성 데이터베이스 정보</span><span class="sxs-lookup"><span data-stu-id="5d171-110">Availability Database Details</span></span>](#AvDbDetails)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="5d171-111">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="5d171-111">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="5d171-112">필수 조건</span><span class="sxs-lookup"><span data-stu-id="5d171-112">Prerequisites</span></span>  
 <span data-ttu-id="5d171-113">주 복제본 또는 보조 복제본을 호스팅하는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스(서버 인스턴스)에 연결해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5d171-113">You must be connected to the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (server instance) that hosts either the primary replica or a secondary replica.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="5d171-114">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="5d171-114">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="5d171-115">**가용성 그룹, 가용성 복제본 및 가용성 데이터베이스를 모니터링하려면**</span><span class="sxs-lookup"><span data-stu-id="5d171-115">**To monitor availability groups, availability replicas, and availability databases**</span></span>  
  
1.  <span data-ttu-id="5d171-116">보기 메뉴에서 **개체 탐색기 정보**를 클릭하거나 **F7** 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="5d171-116">On the View menu, click **Object Explorer Details**, or press the **F7** key.</span></span>  
  
2.  <span data-ttu-id="5d171-117">개체 탐색기에서 가용성 그룹을 모니터링할 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 의 인스턴스에 연결하고 서버 이름을 클릭하여 서버 트리를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="5d171-117">In Object Explorer, connect to the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] on which you want to monitor an availability group, and click the server name to expand the server tree.</span></span>  
  
3.  <span data-ttu-id="5d171-118">**AlwaysOn 고가용성** 및 **가용성 그룹** 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="5d171-118">Expand the **AlwaysOn High Availability** node and the **Availability Groups** node.</span></span>  
  
4.  <span data-ttu-id="5d171-119">**개체 탐색기 정보** 창에 연결된 서버 인스턴스에서 복제본을 호스팅하는 모든 가용성 그룹이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="5d171-119">The **Object Explorer Details** pane displays every availability group for which the connected server instance hosts a replica.</span></span> <span data-ttu-id="5d171-120">각 가용성 그룹에 대해 **서버 인스턴스(기본)** 열에 주 복제본을 현재 호스트 중인 서버 인스턴스의 이름이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="5d171-120">For each availability group, the **Server Instance (Primary)** column displays the name of the server instance that is currently hosting the primary replica.</span></span>  <span data-ttu-id="5d171-121">지정된 가용성 그룹에 대한 자세한 정보를 표시하려면 개체 탐색기에서 해당 가용성 그룹을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5d171-121">To display more information about a given availability group, select it in Object Explorer.</span></span>  
  
5.  <span data-ttu-id="5d171-122">그러면 **개체 탐색기 정보** 창에 이 가용성 그룹에 대한 **가용성 복제본** 및 **가용성 데이터베이스** 노드가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="5d171-122">The **Object Explorer Details** pane then displays the **Availability Replicas** and **Availability Databases** nodes for this availability group:</span></span>  
  
    -   <span data-ttu-id="5d171-123">개체 탐색기에서 **가용성 그룹** 노드를 확장하고 **가용성 복제본** 노드를 선택하면 **개체 탐색기 정보** 창에 그룹의 각 가용성 복제본에 대한 정보가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="5d171-123">When you expand the **Availability Group** node in Object Explorer and select the **Availability Replicas** node, the **Object Explorer Details** pane displays information about each of the availability replicas in the group.</span></span> <span data-ttu-id="5d171-124">자세한 내용은 이 항목 뒷부분에 나오는 [가용성 복제본 정보](#AvReplicaDetails)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5d171-124">For more information, see [Availability Replica Details](#AvReplicaDetails), later in this topic.</span></span>  
  
         <span data-ttu-id="5d171-125">여러 가용성 복제본에 대해 작업을 수행하려면 원하는 가용성 복제본을 선택한 후 마우스 오른쪽 단추로 클릭하여 사용 가능한 명령을 나열하는 상황에 맞는 메뉴를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="5d171-125">To perform operations on multiple availability replicas, select them, and right-click them to open up a context menu that lists the available commands.</span></span>  
  
    -   <span data-ttu-id="5d171-126">개체 탐색기에서 **가용성 그룹** 노드를 확장하고 **가용성 데이터베이스** 노드를 선택하면 **개체 탐색기 정보** 창에 그룹에 있는 각 가용성 데이터베이스에 대한 정보가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="5d171-126">When you expand the **Availability Group** node in Object Explorer and select the **Availability Databases** node, the **Object Explorer Details** pane displays information about each of the availability databases in the group.</span></span> <span data-ttu-id="5d171-127">자세한 내용은 이 항목 뒷부분의 [가용성 데이터베이스 정보](#AvDbDetails)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5d171-127">For more information, see [Availability Database Details](#AvDbDetails), later in this topic.</span></span>  
  
         <span data-ttu-id="5d171-128">여러 가용성 데이터베이스에 대해 작업을 수행하려면 원하는 가용성 데이터베이스를 선택한 후 마우스 오른쪽 단추로 클릭하여 사용 가능한 명령을 나열하는 상황에 맞는 메뉴를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="5d171-128">To perform operations on multiple availability databases, select them, and right-click them to open up a context menu that lists the available commands.</span></span>  
  
##  <a name="availability-groups-details"></a><a name="AvGroupsDetails"></a> <span data-ttu-id="5d171-129">가용성 그룹 정보</span><span class="sxs-lookup"><span data-stu-id="5d171-129">Availability Groups Details</span></span>  
 <span data-ttu-id="5d171-130">**가용성 그룹** 정보 화면에 다음 열이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="5d171-130">The **Availability Groups** details screen displays the following columns:</span></span>  
  
 <span data-ttu-id="5d171-131">**이름**</span><span class="sxs-lookup"><span data-stu-id="5d171-131">**Name**</span></span>  
 <span data-ttu-id="5d171-132">선택한 가용성 그룹의 **가용성 복제본**, **가용성 데이터베이스**및 **가용성 그룹** 수신기 폴더를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="5d171-132">Lists the **Availability Replicas**, **Availability Databases**, and **Availability Group** Listeners folders of the selected availability group.</span></span>  
  
##  <a name="availability-replica-details"></a><a name="AvReplicaDetails"></a> <span data-ttu-id="5d171-133">가용성 복제본 정보</span><span class="sxs-lookup"><span data-stu-id="5d171-133">Availability Replica Details</span></span>  
 <span data-ttu-id="5d171-134">**가용성 복제본** 정보 화면에 다음 열이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="5d171-134">The **Availability Replica** details screen displays the following columns:</span></span>  
  
 <span data-ttu-id="5d171-135">**서버 인스턴스**</span><span class="sxs-lookup"><span data-stu-id="5d171-135">**Server Instance**</span></span>  
 <span data-ttu-id="5d171-136">가용성 복제본을 호스팅하는 서버 인스턴스 이름을 로컬 서버 인스턴스에 대한 서버 인스턴스의 현재 연결 상태를 나타내는 아이콘과 함께 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="5d171-136">Displays the name of the server instance that hosts the availability replica, along with an icon that indicates the current connection state of the server instance to the local server instance.</span></span>  
  
 <span data-ttu-id="5d171-137">**역할**</span><span class="sxs-lookup"><span data-stu-id="5d171-137">**Role**</span></span>  
 <span data-ttu-id="5d171-138">가용성 복제본의 현재 역할( **주** 또는 **보조**)을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5d171-138">Indicates the current role of the availability replica, either **Primary** or **Secondary**.</span></span> <span data-ttu-id="5d171-139">[!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 역할에 대한 자세한 내용은 [AlwaysOn 가용성 그룹 개요&#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5d171-139">For information about [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] roles, see [Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md).</span></span>  
  
 <span data-ttu-id="5d171-140">**보조 역할의 연결 모드**</span><span class="sxs-lookup"><span data-stu-id="5d171-140">**Connection Mode in Secondary Role**</span></span>  
 <span data-ttu-id="5d171-141">보조 역할, 즉 보조 복제본의 역할을 수행하는 지정된 가용성 복제본의 데이터베이스에서 클라이언트의 연결을 허용할 수 있는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5d171-141">Indicates whether the databases of a given availability replica that is performing the secondary role (that is, is acting as a secondary replica) can accept connections from clients.</span></span>  
  
 <span data-ttu-id="5d171-142">가능한 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="5d171-142">The possible values are as follows:</span></span>  
  
|<span data-ttu-id="5d171-143">값</span><span class="sxs-lookup"><span data-stu-id="5d171-143">Value</span></span>|<span data-ttu-id="5d171-144">Description</span><span class="sxs-lookup"><span data-stu-id="5d171-144">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="5d171-145">**연결 허용 안 함**</span><span class="sxs-lookup"><span data-stu-id="5d171-145">**Disallow Connections**</span></span>|<span data-ttu-id="5d171-146">이 가용성 복제본이 보조 복제본 역할을 하는 동안 가용성 데이터베이스에 직접 연결할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5d171-146">No direct connections are allowed to the availability databases when this availability replica is acting as a secondary replica.</span></span> <span data-ttu-id="5d171-147">보조 데이터베이스를 읽기 액세스에 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5d171-147">Secondary databases are not available for read access.</span></span>|  
|<span data-ttu-id="5d171-148">**읽기 전용 연결만 허용**</span><span class="sxs-lookup"><span data-stu-id="5d171-148">**Allow Only Read Intent Connections**</span></span>|<span data-ttu-id="5d171-149">이 복제본이 보조 복제본 역할을 하는 경우 직접 읽기 전용 연결만 허용됩니다.</span><span class="sxs-lookup"><span data-stu-id="5d171-149">Only direct read-only connections are allowed  when this replica acting as a secondary replica.</span></span> <span data-ttu-id="5d171-150">복제본의 모든 데이터베이스에 대한 읽기 액세스가 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="5d171-150">All database(s) in the replica are available for read access.</span></span>|  
|<span data-ttu-id="5d171-151">**모든 연결 허용**</span><span class="sxs-lookup"><span data-stu-id="5d171-151">**Allow All Connections**</span></span>|<span data-ttu-id="5d171-152">이 복제본이 보조 복제본 역할을 하는 동안 읽기 전용 액세스를 위한 모든 데이터베이스 연결이 허용됩니다.</span><span class="sxs-lookup"><span data-stu-id="5d171-152">All connections are allowed to these databases for read-only access when this replica acting as a secondary replica.</span></span>|  
  
 <span data-ttu-id="5d171-153">**연결 상태**</span><span class="sxs-lookup"><span data-stu-id="5d171-153">**Connection State**</span></span>  
 <span data-ttu-id="5d171-154">보조 복제본이 주 복제본에 현재 연결되어 있는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5d171-154">Indicates whether a secondary replica is currently connected to the primary replica.</span></span> <span data-ttu-id="5d171-155">가능한 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="5d171-155">The possible values are as follows:</span></span>  
  
|<span data-ttu-id="5d171-156">값</span><span class="sxs-lookup"><span data-stu-id="5d171-156">Value</span></span>|<span data-ttu-id="5d171-157">Description</span><span class="sxs-lookup"><span data-stu-id="5d171-157">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="5d171-158">**연결 끊김**</span><span class="sxs-lookup"><span data-stu-id="5d171-158">**Disconnected**</span></span>|<span data-ttu-id="5d171-159">원격 가용성 복제본의 경우 로컬 가용성 복제본에서 연결이 끊어져 있는지를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5d171-159">For a remote availability replica, indicates that it is disconnected from the local availability replica.</span></span> <span data-ttu-id="5d171-160">연결이 끊긴 상태에 대한 로컬 복제본의 응답은 역할별로 다음과 같이 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="5d171-160">The response of the local replica to the Disconnected state depends on its role, as follows:</span></span><br /><br /> <span data-ttu-id="5d171-161">주 복제본에서 보조 복제본의 연결이 끊어지면 보조 데이터베이스는 주 복제본에 **동기화되지 않음** 으로 표시되고 주 복제본은 보조 복제본이 다시 연결될 때까지 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="5d171-161">On the primary replica, if a secondary replica is disconnected, the secondary databases are marked as **Not Synchronized** on the primary replica, and the primary replica waits for the secondary to reconnect.</span></span><br /><br /> <span data-ttu-id="5d171-162">보조 복제본에서 보조 복제본의 연결이 끊어지면 보조 복제본은 주 복제본에 다시 연결하려고 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="5d171-162">On the secondary replica, upon detecting that it is disconnected, the secondary replica attempts to reconnect to the primary replica.</span></span>|  
|<span data-ttu-id="5d171-163">**연결됨**</span><span class="sxs-lookup"><span data-stu-id="5d171-163">**Connected**</span></span>|<span data-ttu-id="5d171-164">로컬 복제본에 현재 연결되어 있는 원격 가용성 복제본입니다.</span><span class="sxs-lookup"><span data-stu-id="5d171-164">A remote availability replica that is currently connected to the local replica.</span></span>|  
|<span data-ttu-id="5d171-165">**NULL**</span><span class="sxs-lookup"><span data-stu-id="5d171-165">**NULL**</span></span>|<span data-ttu-id="5d171-166">로컬 복제본이 보조 복제본인 경우 이 값은 다른 보조 복제본에 대해 NULL입니다.</span><span class="sxs-lookup"><span data-stu-id="5d171-166">If the local replica is a secondary replica, this value is NULL for other secondary replicas.</span></span>|  
  
 <span data-ttu-id="5d171-167">**동기화 상태**</span><span class="sxs-lookup"><span data-stu-id="5d171-167">**Synchronization State**</span></span>  
 <span data-ttu-id="5d171-168">보조 복제본이 주 복제본에 현재 동기화되어 있는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5d171-168">Indicates whether a secondary replica is currently synchronized with primary replica.</span></span> <span data-ttu-id="5d171-169">가능한 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="5d171-169">The possible values are as follows:</span></span>  
  
|<span data-ttu-id="5d171-170">값</span><span class="sxs-lookup"><span data-stu-id="5d171-170">Value</span></span>|<span data-ttu-id="5d171-171">Description</span><span class="sxs-lookup"><span data-stu-id="5d171-171">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="5d171-172">**동기화되지 않음**</span><span class="sxs-lookup"><span data-stu-id="5d171-172">**Not Synchronized**</span></span>|<span data-ttu-id="5d171-173">데이터베이스가 동기화되지 않았거나 가용성 그룹에 아직 조인되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="5d171-173">The database is not synchronized or has not yet been joined to the availability group.</span></span>|  
|<span data-ttu-id="5d171-174">**동기화됨**</span><span class="sxs-lookup"><span data-stu-id="5d171-174">**Synchronized**</span></span>|<span data-ttu-id="5d171-175">데이터베이스가 현재 주 복제본 또는 마지막 주 복제본(있는 경우)의 주 데이터베이스와 동기화되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5d171-175">The database is synchronized with the primary database on the current primary replica, if any, or on the last primary replica.</span></span><br /><br /> <span data-ttu-id="5d171-176">참고: 성능 모드에서는 데이터베이스가 절대 Synchronized 상태로 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5d171-176">Note: In performance mode, the database is never in the Synchronized state.</span></span>|  
|<span data-ttu-id="5d171-177">**NULL**</span><span class="sxs-lookup"><span data-stu-id="5d171-177">**NULL**</span></span>|<span data-ttu-id="5d171-178">알 수 없는 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="5d171-178">Unknown state.</span></span> <span data-ttu-id="5d171-179">이 값은 로컬 서버 인스턴스가 WSFC 장애 조치(Failover) 클러스터와 통신할 수 없는 경우(즉, 로컬 노드가 WSFC 쿼럼의 일부가 아닌 경우)에 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="5d171-179">This value occurs when the local server instance cannot communicate with the WSFC failover cluster (that is the local node is not part of WSFC quorum).</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="5d171-180">가용성 복제본의 성능 카운터에 대한 자세한 내용은 [SQL Server, 가용성 복제본](../../../relational-databases/performance-monitor/sql-server-availability-replica.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5d171-180">For information about performance counters for availability replicas, see [SQL Server, Availability Replica](../../../relational-databases/performance-monitor/sql-server-availability-replica.md).</span></span>  
  
##  <a name="availability-database-details"></a><a name="AvDbDetails"></a> <span data-ttu-id="5d171-181">가용성 데이터베이스 정보</span><span class="sxs-lookup"><span data-stu-id="5d171-181">Availability Database Details</span></span>  
 <span data-ttu-id="5d171-182">**가용성 데이터베이스** 정보 화면에는 지정된 가용성 그룹의 다음 가용성 데이터베이스 속성이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="5d171-182">The **Availability Database** details screen displays the following properties of the availability databases in a given availability group:</span></span>  
  
 <span data-ttu-id="5d171-183">**이름**</span><span class="sxs-lookup"><span data-stu-id="5d171-183">**Name**</span></span>  
 <span data-ttu-id="5d171-184">가용성 데이터베이스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="5d171-184">The name of the availability database.</span></span>  
  
 <span data-ttu-id="5d171-185">**동기화 상태**</span><span class="sxs-lookup"><span data-stu-id="5d171-185">**Synchronization State**</span></span>  
 <span data-ttu-id="5d171-186">가용성 데이터베이스가 주 복제본에 현재 동기화되어 있는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5d171-186">Indicates whether the availability database is currently synchronized with primary replica.</span></span>  
  
 <span data-ttu-id="5d171-187">가능한 동기화 상태는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="5d171-187">The possible synchronization states are as follows:</span></span>  
  
|<span data-ttu-id="5d171-188">값</span><span class="sxs-lookup"><span data-stu-id="5d171-188">Value</span></span>|<span data-ttu-id="5d171-189">Description</span><span class="sxs-lookup"><span data-stu-id="5d171-189">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="5d171-190">동기화 중</span><span class="sxs-lookup"><span data-stu-id="5d171-190">Synchronizing</span></span>|<span data-ttu-id="5d171-191">보조 데이터베이스가 디스크에 아직 기록(확정)되지 않은 주 데이터베이스에 대한 트랜잭션 로그 기록을 수신했습니다.</span><span class="sxs-lookup"><span data-stu-id="5d171-191">The secondary database has received the transaction log records for the primary database that are not yet written to disk (hardened).</span></span><br /><br /> <span data-ttu-id="5d171-192">참고: 비동기 커밋 모드에서 동기화 상태는 항상 **동기화 중**입니다.</span><span class="sxs-lookup"><span data-stu-id="5d171-192">Note: In asynchronous-commit mode, the synchronization state is always **Synchronizing**.</span></span>|  
  
 <span data-ttu-id="5d171-193">**일시 중지됨**</span><span class="sxs-lookup"><span data-stu-id="5d171-193">**Suspended**</span></span>  
 <span data-ttu-id="5d171-194">가용성 데이터베이스가 현재 온라인 상태인지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5d171-194">Indicates whether the availability database is currently online.</span></span> <span data-ttu-id="5d171-195">가능한 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="5d171-195">The possible values are as follows:</span></span>  
  
|<span data-ttu-id="5d171-196">값</span><span class="sxs-lookup"><span data-stu-id="5d171-196">Value</span></span>|<span data-ttu-id="5d171-197">Description</span><span class="sxs-lookup"><span data-stu-id="5d171-197">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="5d171-198">**일시 중지됨**</span><span class="sxs-lookup"><span data-stu-id="5d171-198">**Suspended**</span></span>|<span data-ttu-id="5d171-199">이 상태는 데이터베이스를 로컬로 일시 중지하여 수동으로 다시 시작해야 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5d171-199">This state indicates that the database is suspended locally and needs to be manually resumed.</span></span><br /><br /> <span data-ttu-id="5d171-200">주 복제본에서 보조 데이터베이스에 대한 값을 읽을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5d171-200">On the primary replica, the value is unreliable for a secondary database.</span></span> <span data-ttu-id="5d171-201">보조 데이터베이스가 일시 중지되었는지 여부를 안정적으로 결정하려면 데이터베이스를 호스팅하는 보조 복제본에서 보조 데이터베이스를 쿼리합니다.</span><span class="sxs-lookup"><span data-stu-id="5d171-201">To reliably determine whether a secondary database is suspended, query it on the secondary replica that hosts the database.</span></span>|  
|<span data-ttu-id="5d171-202">**조인되지 않음**</span><span class="sxs-lookup"><span data-stu-id="5d171-202">**Not Joined**</span></span>|<span data-ttu-id="5d171-203">보조 데이터베이스가 가용성 그룹에 조인되지 않았거나 그룹에서 제거되었음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5d171-203">Indicates that the secondary database either has not been joined to the availability group or has been removed from the group.</span></span>|  
|<span data-ttu-id="5d171-204">**온라인**</span><span class="sxs-lookup"><span data-stu-id="5d171-204">**Online**</span></span>|<span data-ttu-id="5d171-205">데이터베이스가 로컬 가용성 복제본에서 일시 중지되지 않고 연결되어 있음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5d171-205">Indicates that the database is not suspended on the local availability replica and that the database is connected.</span></span>|  
|<span data-ttu-id="5d171-206">**연결되지 않음**</span><span class="sxs-lookup"><span data-stu-id="5d171-206">**Not Connected**</span></span>|<span data-ttu-id="5d171-207">보조 복제본이 주 복제본에 현재 연결할 수 없음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5d171-207">Indicates that the secondary replica is currently unable to connect to the primary replica.</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="5d171-208">가용성 데이터베이스의 성능 카운터에 대한 자세한 내용은 [SQL Server, 데이터베이스 복제본](../../../relational-databases/performance-monitor/sql-server-database-replica.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5d171-208">For information about performance counters for availability databases, see [SQL Server, Database Replica](../../../relational-databases/performance-monitor/sql-server-database-replica.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d171-209">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5d171-209">See Also</span></span>  
 <span data-ttu-id="5d171-210">[sys.dm_os_performance_counters&#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-performance-counters-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="5d171-210">[sys.dm_os_performance_counters &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-performance-counters-transact-sql) </span></span>  
 <span data-ttu-id="5d171-211">[AlwaysOn 대시보드 &#40;SQL Server Management Studio를 사용&#41;](use-the-always-on-dashboard-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="5d171-211">[Use the AlwaysOn Dashboard &#40;SQL Server Management Studio&#41;](use-the-always-on-dashboard-sql-server-management-studio.md) </span></span>  
 <span data-ttu-id="5d171-212">[가용성 그룹 속성 보기&#40;SQL Server&#41;](view-availability-group-properties-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="5d171-212">[View Availability Group Properties &#40;SQL Server&#41;](view-availability-group-properties-sql-server.md) </span></span>  
 [<span data-ttu-id="5d171-213">가용성 복제본 속성 보기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="5d171-213">View Availability Replica Properties &#40;SQL Server&#41;</span></span>](view-availability-replica-properties-sql-server.md)  
  
  
