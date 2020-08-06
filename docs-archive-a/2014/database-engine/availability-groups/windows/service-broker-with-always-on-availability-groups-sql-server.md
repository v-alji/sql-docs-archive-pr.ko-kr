---
title: AlwaysOn 가용성 그룹로 Service Broker (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Service Broker, AlwaysOn Availability Groups
- Availability Groups [SQL Server], interoperability
ms.assetid: 881c20e5-1c99-44eb-b393-09fc5ea0f122
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: da179219363422c4ec242d29be61f35dd1609823
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651281"
---
# <a name="service-broker-with-alwayson-availability-groups-sql-server"></a><span data-ttu-id="1f6c7-102">AlwaysOn 가용성 그룹이 포함된 Service Broker(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="1f6c7-102">Service Broker with AlwaysOn Availability Groups (SQL Server)</span></span>
  <span data-ttu-id="1f6c7-103">이 항목에서는 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 에서 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]과 함께 작동하도록 Service Broker를 구성하는 방법에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="1f6c7-103">This topic contains information about configuring Service Broker to work with [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span>  
  
 <span data-ttu-id="1f6c7-104">**항목 내용:**</span><span class="sxs-lookup"><span data-stu-id="1f6c7-104">**In This Topic:**</span></span>  
  
-   [<span data-ttu-id="1f6c7-105">가용성 그룹의 서비스가 원격 메시지를 받기 위한 요구 사항</span><span class="sxs-lookup"><span data-stu-id="1f6c7-105">Requirements for a Service in an Availability Group to Receive Remote Messages</span></span>](#ReceiveRemoteMessages)  
  
-   [<span data-ttu-id="1f6c7-106">가용성 그룹의 원격 서비스에 메시지를 보내기 위한 요구 사항</span><span class="sxs-lookup"><span data-stu-id="1f6c7-106">Requirements for Sending Messages to a Remote Service in an Availability Group</span></span>](#SendRemoteMessages)  
  
##  <a name="requirements-for-a-service-in-an-availability-group-to-receive-remote-messages"></a><a name="ReceiveRemoteMessages"></a> <span data-ttu-id="1f6c7-107">가용성 그룹의 서비스가 원격 메시지를 받기 위한 요구 사항</span><span class="sxs-lookup"><span data-stu-id="1f6c7-107">Requirements for a Service in an Availability Group to Receive Remote Messages</span></span>  
  
1.  <span data-ttu-id="1f6c7-108">**가용성 그룹에 수신기가 있는지 확인합니다.**</span><span class="sxs-lookup"><span data-stu-id="1f6c7-108">**Ensure that the availability group possesses a listener.**</span></span>  
  
     <span data-ttu-id="1f6c7-109">자세한 내용은 [가용성 그룹 수신기 만들기 또는 구성&#40;SQL Server&#41;](create-or-configure-an-availability-group-listener-sql-server.md)가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f6c7-109">For more information, see [Create or Configure an Availability Group Listener &#40;SQL Server&#41;](create-or-configure-an-availability-group-listener-sql-server.md).</span></span>  
  
2.  <span data-ttu-id="1f6c7-110">**Service Broker 엔드포인트가 존재하고 올바르게 구성되어 있는지 확인합니다.**</span><span class="sxs-lookup"><span data-stu-id="1f6c7-110">**Ensure that the Service Broker endpoint exists and is correctly configured.**</span></span>  
  
     <span data-ttu-id="1f6c7-111">가용성 그룹에 대한 가용성 복제본을 호스팅하는 모든 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스에서 다음과 같이 Service Broker 엔드포인트를 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f6c7-111">On every instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that hosts an availability replica for the availability group, configure the Service Broker endpoint, as follows:</span></span>  
  
    -   <span data-ttu-id="1f6c7-112">LISTENER_IP를 'ALL'로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="1f6c7-112">Set LISTENER_IP to 'ALL'.</span></span> <span data-ttu-id="1f6c7-113">이 설정을 사용하면 가용성 그룹 수신기에 바인딩된 모든 유효한 IP 주소에서 연결이 가능해집니다.</span><span class="sxs-lookup"><span data-stu-id="1f6c7-113">This setting enables connections on any valid IP address that is bound to the availability group listener.</span></span>  
  
    -   <span data-ttu-id="1f6c7-114">모든 호스트 서버 인스턴스에서 Service Broker 포트를 동일한 포트 번호로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="1f6c7-114">Set the Service Broker PORT to the same port number on all the host server instances.</span></span>  
  
        > [!TIP]  
        >  <span data-ttu-id="1f6c7-115">특정 서버 인스턴스에서 Service Broker 엔드포인트의 포트 번호를 보려면 **sys.tcp_endpoints** 카탈로그 뷰의 [port](/sql/relational-databases/system-catalog-views/sys-tcp-endpoints-transact-sql) 열을 쿼리합니다. 여기서 **type_desc** = 'SERVICE_BROKER'입니다.</span><span class="sxs-lookup"><span data-stu-id="1f6c7-115">To view the port number of the Service Broker endpoint on a given server instance, query the **port** column of the [sys.tcp_endpoints](/sql/relational-databases/system-catalog-views/sys-tcp-endpoints-transact-sql) catalog view, where **type_desc** = 'SERVICE_BROKER'.</span></span>  
  
     <span data-ttu-id="1f6c7-116">다음 예에서는 기본 Service Broker 포트(4022)를 사용하며 모든 유효한 IP 주소를 수신하는 Windows 인증 Service Broker 엔드포인트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1f6c7-116">The following example creates a Windows authenticated Service Broker endpoint that uses the default Service Broker port (4022) and listens to all valid IP addresses.</span></span>  
  
    ```  
    CREATE ENDPOINT [SSBEndpoint]  
        STATE = STARTED  
        AS TCP  (LISTENER_PORT = 4022, LISTENER_IP = ALL )  
        FOR SERVICE_BROKER (AUTHENTICATION = WINDOWS)  
    ```  
  
     <span data-ttu-id="1f6c7-117">자세한 내용은 [CREATE ENDPOINT&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-endpoint-transact-sql)과 함께 작동하도록 Service Broker를 구성하는 방법에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="1f6c7-117">For more information, see [CREATE ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-endpoint-transact-sql).</span></span>  
  
3.  <span data-ttu-id="1f6c7-118">**엔드포인트에 대한 CONNECT 권한을 부여합니다.**</span><span class="sxs-lookup"><span data-stu-id="1f6c7-118">**Grant CONNECT permission on the endpoint.**</span></span>  
  
     <span data-ttu-id="1f6c7-119">Service Broker 엔드포인트에 대한 CONNECT 권한을 PUBLIC 또는 로그인으로 부여합니다.</span><span class="sxs-lookup"><span data-stu-id="1f6c7-119">Grant CONNECT permission on the Service Broker endpoint either to PUBLIC or to a login.</span></span>  
  
     <span data-ttu-id="1f6c7-120">다음 예에서는 `broker_endpoint`라는 Service Broker 엔드포인트에 대한 연결을 PUBLIC으로 부여합니다.</span><span class="sxs-lookup"><span data-stu-id="1f6c7-120">The following example grants the connection on a Service Broker endpoint named `broker_endpoint` to PUBLIC.</span></span>  
  
    ```  
    GRANT CONNECT ON ENDPOINT::[broker_endpoint] TO [PUBLIC]  
    ```  
  
     <span data-ttu-id="1f6c7-121">자세한 내용은 [GRANT&#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-transact-sql)과 함께 작동하도록 Service Broker를 구성하는 방법에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="1f6c7-121">For more information, see [GRANT &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-transact-sql).</span></span>  
  
4.  <span data-ttu-id="1f6c7-122">**msdb에 AutoCreatedLocal 경로 또는 특정 서비스에 대한 경로가 포함되어 있는지 확인합니다.**</span><span class="sxs-lookup"><span data-stu-id="1f6c7-122">**Ensure that msdb contains either an AutoCreatedLocal route or a route to the specific service.**</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="1f6c7-123">기본적으로 **msdb**를 비롯하여 각 사용자 데이터베이스에는 **AutoCreatedLocal**경로가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f6c7-123">By default, each user database, including **msdb**, contains the route **AutoCreatedLocal**.</span></span> <span data-ttu-id="1f6c7-124">이 경로는 임의의 서비스 이름 및 Broker 인스턴스와 일치하며 메시지가 현재 인스턴스 내에 배달되도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1f6c7-124">This route matches any service name and broker instance and specifies that the message should be delivered within the current instance.</span></span> <span data-ttu-id="1f6c7-125">**AutoCreatedLocal** 의 우선 순위는 원격 인스턴스와 통신하는 특정 서비스를 명시적으로 지정하는 경로의 우선 순위보다 낮습니다.</span><span class="sxs-lookup"><span data-stu-id="1f6c7-125">**AutoCreatedLocal** has lower priority than routes that explicitly specify a specific service that communicates with a remote instance.</span></span>  
  
     <span data-ttu-id="1f6c7-126">경로를 만드는 방법은 [버전의 온라인 설명서에 있는](https://msdn.microsoft.com/library/ms166090\(SQL.105\).aspx) Service Broker 라우팅 예 [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] 및 [CREATE ROUTE&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-route-transact-sql)과 함께 작동하도록 Service Broker를 구성하는 방법에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="1f6c7-126">For information about creating routes, see [Service Broker Routing Examples](https://msdn.microsoft.com/library/ms166090\(SQL.105\).aspx) (in the [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] version of Books Online) and [CREATE ROUTE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-route-transact-sql).</span></span>  
  
##  <a name="requirements-for-sending-messages-to-a-remote-service-in-an-availability-group"></a><a name="SendRemoteMessages"></a> <span data-ttu-id="1f6c7-127">가용성 그룹의 원격 서비스에 메시지를 보내기 위한 요구 사항</span><span class="sxs-lookup"><span data-stu-id="1f6c7-127">Requirements for Sending Messages to a Remote Service in an Availability Group</span></span>  
  
1.  <span data-ttu-id="1f6c7-128">**대상 서비스에 대한 경로를 만듭니다.**</span><span class="sxs-lookup"><span data-stu-id="1f6c7-128">**Create a route to the target service.**</span></span>  
  
     <span data-ttu-id="1f6c7-129">다음과 같이 경로를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="1f6c7-129">Configure the route as follows:</span></span>  
  
    -   <span data-ttu-id="1f6c7-130">ADDRESS를 서비스 데이터베이스를 호스팅하는 가용성 그룹의 수신기 IP 주소로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="1f6c7-130">Set ADDRESS to the listener IP address of availability group that hosts the service database.</span></span>  
  
    -   <span data-ttu-id="1f6c7-131">PORT를 각 원격 SQL Server 인스턴스의 Service Broker 엔드포인트에 지정한 포트로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="1f6c7-131">Set PORT to the port that you specified in the Service Broker endpoint of each of the remote SQL Server instances.</span></span>  
  
     <span data-ttu-id="1f6c7-132">다음 예에서는 `RouteToTargetService` 서비스에 대해 `ISBNLookupRequestService` 라는 경로를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1f6c7-132">The following example creates a route named `RouteToTargetService` for the `ISBNLookupRequestService` service.</span></span> <span data-ttu-id="1f6c7-133">이 경로는 포트 4022를 사용하는 가용성 그룹 수신기 `MyAgListener`를 대상으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f6c7-133">The route targets the availability group listener, `MyAgListener`, which uses port 4022.</span></span>  
  
    ```  
    CREATE ROUTE [RouteToTargetService] WITH   
    SERVICE_NAME = 'ISBNLookupRequestService',   
    ADDRESS = 'TCP://MyAgListener:4022';  
  
    ```  
  
     <span data-ttu-id="1f6c7-134">자세한 내용은 [CREATE ROUTE&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-route-transact-sql)과 함께 작동하도록 Service Broker를 구성하는 방법에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="1f6c7-134">For more information, see [CREATE ROUTE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-route-transact-sql).</span></span>  
  
2.  <span data-ttu-id="1f6c7-135">**msdb에 AutoCreatedLocal 경로 또는 특정 서비스에 대한 경로가 포함되어 있는지 확인합니다.**</span><span class="sxs-lookup"><span data-stu-id="1f6c7-135">**Ensure that msdb contains either an AutoCreatedLocal route or a route to the specific service.**</span></span> <span data-ttu-id="1f6c7-136">자세한 내용은 이 항목의 앞부분에 나오는 [가용성 그룹의 서비스가 원격 메시지를 받기 위한 요구 사항](#ReceiveRemoteMessages)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1f6c7-136">(For more information, see [Requirements for a Service in an Availability Group to Receive Remote Messages](#ReceiveRemoteMessages), earlier in this topic.)</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="1f6c7-137">관련 작업</span><span class="sxs-lookup"><span data-stu-id="1f6c7-137">Related Tasks</span></span>  
  
-   [<span data-ttu-id="1f6c7-138">CREATE ENDPOINT&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="1f6c7-138">CREATE ENDPOINT &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-endpoint-transact-sql)  
  
-   [<span data-ttu-id="1f6c7-139">CREATE ROUTE&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="1f6c7-139">CREATE ROUTE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-route-transact-sql)  
  
-   [<span data-ttu-id="1f6c7-140">GRANT&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="1f6c7-140">GRANT &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/grant-transact-sql)  
  
-   <span data-ttu-id="1f6c7-141">[가용성 그룹 수신기 만들기 또는 구성&#40;SQL Server&#41;](create-or-configure-an-availability-group-listener-sql-server.md)</span><span class="sxs-lookup"><span data-stu-id="1f6c7-141">[Create or Configure an Availability Group Listener &#40;SQL Server&#41;](create-or-configure-an-availability-group-listener-sql-server.md).</span></span>  
  
-   [<span data-ttu-id="1f6c7-142">가용성 그룹의 생성 및 구성&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="1f6c7-142">Creation and Configuration of Availability Groups &#40;SQL Server&#41;</span></span>](creation-and-configuration-of-availability-groups-sql-server.md)  
  
-   [<span data-ttu-id="1f6c7-143">데이터베이스 미러링을 위한 로그인 계정을 설정 하거나 &#40;SQL Server를 AlwaysOn 가용성 그룹&#41;</span><span class="sxs-lookup"><span data-stu-id="1f6c7-143">Set Up Login Accounts for Database Mirroring or AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](../../database-mirroring/set-up-login-accounts-database-mirroring-always-on-availability.md)  
  
## <a name="see-also"></a><span data-ttu-id="1f6c7-144">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1f6c7-144">See Also</span></span>  
 <span data-ttu-id="1f6c7-145">[AlwaysOn 가용성 그룹 &#40;SQL Server 개요&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="1f6c7-145">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="1f6c7-146">[가용성 그룹 수신기, 클라이언트 연결 및 애플리케이션 장애 조치(failover)&#40;SQL Server&#41;](../../listeners-client-connectivity-application-failover.md) </span><span class="sxs-lookup"><span data-stu-id="1f6c7-146">[Availability Group Listeners, Client Connectivity, and Application Failover &#40;SQL Server&#41;](../../listeners-client-connectivity-application-failover.md) </span></span>  
 [<span data-ttu-id="1f6c7-147">SQL Server Service Broker</span><span class="sxs-lookup"><span data-stu-id="1f6c7-147">SQL Server Service Broker</span></span>](../../configure-windows/sql-server-service-broker.md)  
  
  
