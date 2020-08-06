---
title: 가용성 그룹 수신기 속성 보기(SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 07/11/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.availabilitygrouplistenerproperties.general.f1
helpviewer_keywords:
- Availability Groups [SQL Server], monitoring
ms.assetid: aca0d016-3228-40b8-bdc3-285ed6d9b280
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ef7fe316394a030350ceb12a0d1b8e2d48ee1d34
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646652"
---
# <a name="view-availability-group-listener-properties-sql-server"></a><span data-ttu-id="e977e-102">가용성 그룹 수신기 속성 보기(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="e977e-102">View Availability Group Listener Properties (SQL Server)</span></span>
  <span data-ttu-id="e977e-103">이 항목에서는 *또는* 의 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 을 사용하여 [!INCLUDE[tsql](../../../includes/tsql-md.md)] AlwaysOn 가용성 그룹 수신기 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]의 속성을 보는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="e977e-103">This topic describes how to view the properties of an AlwaysOn *availability group listener* by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../../includes/tsql-md.md)] in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span>  
  
-   <span data-ttu-id="e977e-104">**수신기 속성을 보려면:**</span><span class="sxs-lookup"><span data-stu-id="e977e-104">**To view listener properties, using:**</span></span>  
  
     [<span data-ttu-id="e977e-105">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="e977e-105">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="e977e-106">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="e977e-106">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="e977e-107">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="e977e-107">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="e977e-108">**수신기 속성을 보려면**</span><span class="sxs-lookup"><span data-stu-id="e977e-108">**To view listener properties**</span></span>  
  
1.  <span data-ttu-id="e977e-109">개체 탐색기에서 수신기를 볼 가용성 그룹의 가용성 복제본을 호스팅하는 서버 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="e977e-109">In Object Explorer, connect to a server instance that hosts any availability replica of the availability group whose listener you want to view.</span></span> <span data-ttu-id="e977e-110">서버 이름을 클릭하여 서버 트리를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="e977e-110">Click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="e977e-111">**AlwaysOn 고가용성** 및 **가용성 그룹** 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="e977e-111">Expand the **AlwaysOn High Availability** node and the **Availability Groups** node.</span></span>  
  
3.  <span data-ttu-id="e977e-112">가용성 그룹의 노드를 확장하고 **가용성 그룹 수신기** 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="e977e-112">Expand the node of the availability group, and expand the **Availability Groups Listeners** node.</span></span>  
  
4.  <span data-ttu-id="e977e-113">보려는 수신기를 마우스 오른쪽 단추로 클릭하고 **속성** 명령을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e977e-113">Right-click the listener that you want to view, and select the **Properties** command.</span></span>  
  
5.  <span data-ttu-id="e977e-114">**가용성 그룹 수신기 속성** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="e977e-114">This opens the **Availability Group Listener Properties** dialog box.</span></span> <span data-ttu-id="e977e-115">자세한 내용은 이 항목의 뒷부분에 나와 있는 [가용성 그룹 수신기 속성(대화 상자)](#AgListenerPropertiesDialog)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e977e-115">For more information, see [Availability Group Listener Properties (Dialog Box)](#AgListenerPropertiesDialog), later in this topic.</span></span>  
  
###  <a name="availability-group-listener-properties-dialog-box"></a><a name="AgListenerPropertiesDialog"></a> <span data-ttu-id="e977e-116">가용성 그룹 수신기 속성(대화 상자)</span><span class="sxs-lookup"><span data-stu-id="e977e-116">Availability Group Listener Properties (Dialog Box)</span></span>  
 <span data-ttu-id="e977e-117">**수신기 DNS 이름**</span><span class="sxs-lookup"><span data-stu-id="e977e-117">**Listener DNS Name**</span></span>  
 <span data-ttu-id="e977e-118">가용성 그룹 수신기의 네트워크 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="e977e-118">The network name of the availability group listener.</span></span>  
  
 <span data-ttu-id="e977e-119">**포트**</span><span class="sxs-lookup"><span data-stu-id="e977e-119">**Port**</span></span>  
 <span data-ttu-id="e977e-120">이 수신기에서 사용되는 TPC 포트입니다.</span><span class="sxs-lookup"><span data-stu-id="e977e-120">The TCP port used by this listener.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e977e-121">주 복제본을 연결한 경우 이 필드를 사용하여 수신기의 포트 번호를 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e977e-121">If you are connected the primary replica, you can use this field to modify the port number of the listener.</span></span> <span data-ttu-id="e977e-122">이렇게 하려면 가용성 그룹에 대한 ALTER AVAILABILITY GROUP 권한, CONTROL AVAILABILITY GROUP 권한, ALTER ANY AVAILABILITY GROUP 권한 또는 CONTROL SERVER 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="e977e-122">This requires ALTER AVAILABILITY GROUP permission on the availability group, CONTROL AVAILABILITY GROUP permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>  
  
 <span data-ttu-id="e977e-123">**네트워크 모드**</span><span class="sxs-lookup"><span data-stu-id="e977e-123">**Network Mode**</span></span>  
 <span data-ttu-id="e977e-124">수신기에 사용되는 TCP 프로토콜을 나타내며 다음 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="e977e-124">Indicates the TCP protocol used by the listener, one of:</span></span>  
  
 <span data-ttu-id="e977e-125">**DHCP**</span><span class="sxs-lookup"><span data-stu-id="e977e-125">**DHCP**</span></span>  
 <span data-ttu-id="e977e-126">수신기는 DHCP(동적 호스트 구성 프로토콜)를 실행하는 서버에 의해 할당되는 동적 IP 주소를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="e977e-126">The listener uses an dynamic IP address that is assigned by a server running the Dynamic Host Configuration Protocol (DHCP).</span></span>  
  
 <span data-ttu-id="e977e-127">**고정 IP**</span><span class="sxs-lookup"><span data-stu-id="e977e-127">**Static IP**</span></span>  
 <span data-ttu-id="e977e-128">수신기는 하나 이상의 고정 IP 주소를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="e977e-128">The listener uses one or more Static IP addresses.</span></span> <span data-ttu-id="e977e-129">다른 서브넷에 액세스하려면 가용성 그룹 수신기가 정적 고정 IP 주소를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e977e-129">To access the different subnets, an availability group listener must use static IP addresses.</span></span>  
  
 <span data-ttu-id="e977e-130">표에는 수신기가 수신하는 각 서브넷 및 해당 서브넷과 연결된 IP 주소가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e977e-130">The grid displays each of the subnets on which the listener listens and the IP address associated with that subnet.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="e977e-131">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="e977e-131">Using Transact-SQL</span></span>  
 <span data-ttu-id="e977e-132">**수신기 속성을 보려면**</span><span class="sxs-lookup"><span data-stu-id="e977e-132">**To view listener properties**</span></span>  
  
 <span data-ttu-id="e977e-133">가용성 그룹 수신기를 모니터링하려면 다음 뷰를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="e977e-133">To monitor the availability group listeners, use the following views:</span></span>  
  
 [<span data-ttu-id="e977e-134">sys.availability_group_listener_ip_addresses</span><span class="sxs-lookup"><span data-stu-id="e977e-134">sys.availability_group_listener_ip_addresses</span></span>](/sql/relational-databases/system-catalog-views/sys-availability-group-listener-ip-addresses-transact-sql)  
 <span data-ttu-id="e977e-135">가용성 그룹 수신기에 대해 현재 온라인인 규칙에 부합하는 모든 가상 IP 주소에 대해 하나의 행을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="e977e-135">Returns a row for every conformant virtual IP address that is currently online for an availability group listener.</span></span>  
  
 <span data-ttu-id="e977e-136">**열 이름:** listener_id, ip_address, ip_subnet_mask, is_dhcp, network_subnet_ip, network_subnet_prefix_length, network_subnet_ipv4_mask, state, state_desc</span><span class="sxs-lookup"><span data-stu-id="e977e-136">**Column names:** listener_id, ip_address, ip_subnet_mask, is_dhcp, network_subnet_ip, network_subnet_prefix_length, network_subnet_ipv4_mask, state, state_desc</span></span>  
  
 [<span data-ttu-id="e977e-137">sys.availability_group_listeners</span><span class="sxs-lookup"><span data-stu-id="e977e-137">sys.availability_group_listeners</span></span>](/sql/relational-databases/system-catalog-views/sys-availability-group-listeners-transact-sql)  
 <span data-ttu-id="e977e-138">지정된 가용성 그룹에 대해 0개의 행을 반환하여 가용성 그룹에 연결된 네트워크 이름이 없음을 나타내거나 WSFC 클러스터의 각 가용성 그룹 수신기 구성에 대해 하나의 행을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="e977e-138">For a given availability group, returns either zero rows indicating that no network name is associated with the availability group, or returns a row for each availability-group listener configuration in the WSFC cluster.</span></span>  
  
 <span data-ttu-id="e977e-139">**열 이름:** group_id, listener_id, dns_name, port, is_conformant, ip_configuration_string_from_cluster</span><span class="sxs-lookup"><span data-stu-id="e977e-139">**Column names:** group_id, listener_id, dns_name, port, is_conformant, ip_configuration_string_from_cluster</span></span>  
  
 [<span data-ttu-id="e977e-140">sys.dm_tcp_listener_states</span><span class="sxs-lookup"><span data-stu-id="e977e-140">sys.dm_tcp_listener_states</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-tcp-listener-states-transact-sql)  
 <span data-ttu-id="e977e-141">각 TCP 수신기에 대한 동적 상태 정보를 포함하는 행을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="e977e-141">Returns a row containing dynamic-state information for each TCP listener.</span></span>  
  
 <span data-ttu-id="e977e-142">**열 이름:** listener_id, ip_address, is_ipv4, port, type, type_desc, state, state_desc, start_time</span><span class="sxs-lookup"><span data-stu-id="e977e-142">**Column names:** listener_id, ip_address, is_ipv4, port, type, type_desc, state, state_desc, start_time</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e977e-143">[!INCLUDE[tsql](../../../includes/tsql-md.md)]을 사용하여 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 환경을 모니터링하는 방법은 [가용성 그룹 모니터링&#40;Transact-SQL&#41;](monitor-availability-groups-transact-sql.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e977e-143">For more information about using [!INCLUDE[tsql](../../../includes/tsql-md.md)] to monitor your [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] environment, see [Monitor Availability Groups &#40;Transact-SQL&#41;](monitor-availability-groups-transact-sql.md).</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="e977e-144">관련 작업</span><span class="sxs-lookup"><span data-stu-id="e977e-144">Related Tasks</span></span>  
  
-   [<span data-ttu-id="e977e-145">가용성 그룹 수신기 만들기 또는 구성&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="e977e-145">Create or Configure an Availability Group Listener &#40;SQL Server&#41;</span></span>](create-or-configure-an-availability-group-listener-sql-server.md)  
  
-   [<span data-ttu-id="e977e-146">가용성 그룹 수신기 제거&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="e977e-146">Remove an Availability Group Listener &#40;SQL Server&#41;</span></span>](remove-an-availability-group-listener-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="e977e-147">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e977e-147">See Also</span></span>  
 <span data-ttu-id="e977e-148">[AlwaysOn 가용성 그룹 &#40;SQL Server 개요&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="e977e-148">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="e977e-149">[가용성 그룹 수신기, 클라이언트 연결 및 애플리케이션 장애 조치(failover)&#40;SQL Server&#41;](../../listeners-client-connectivity-application-failover.md) </span><span class="sxs-lookup"><span data-stu-id="e977e-149">[Availability Group Listeners, Client Connectivity, and Application Failover &#40;SQL Server&#41;](../../listeners-client-connectivity-application-failover.md) </span></span>  
 [<span data-ttu-id="e977e-150">가용성 그룹 모니터링&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="e977e-150">Monitor Availability Groups &#40;Transact-SQL&#41;</span></span>](monitor-availability-groups-transact-sql.md)  
  
  
