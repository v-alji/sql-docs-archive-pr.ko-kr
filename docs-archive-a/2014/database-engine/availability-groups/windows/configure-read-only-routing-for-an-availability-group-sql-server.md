---
title: 가용성 그룹에 대한 읽기 전용 라우팅 구성(SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 10/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- read-only routing
- Availability Groups [SQL Server], readable secondary replicas
- Availability Groups [SQL Server], read-only routing
- readable secondary replicas
- Availability Groups [SQL Server], client connectivity
- Availability Groups [SQL Server], active secondary replicas
ms.assetid: 7bd89ddd-0403-4930-a5eb-3c78718533d4
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 2d51d1db75caa29814a01fc1f49bfdd49b403c3d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652996"
---
# <a name="configure-read-only-routing-for-an-availability-group-sql-server"></a><span data-ttu-id="39dda-102">가용성 그룹에 대한 읽기 전용 라우팅 구성(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="39dda-102">Configure Read-Only Routing for an Availability Group (SQL Server)</span></span>
  <span data-ttu-id="39dda-103">[!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]에서 읽기 전용 라우팅을 지원하도록 AlwaysOn 가용성 그룹을 구성하려면 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 이나 PowerShell을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="39dda-103">To configure an AlwaysOn availability group to support read-only routing in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], you can use either [!INCLUDE[tsql](../../../includes/tsql-md.md)] or PowerShell.</span></span> <span data-ttu-id="39dda-104">*읽기 전용 라우팅* 이란 특정 읽기 전용 연결 요청을 AlwaysOn의 사용 가능하고 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 읽기 가능한 보조 복제본 [(즉, 보조 역할로 실행될 때 읽기 전용 작업을 허용하도록 구성된 복제본)으로 라우팅하는](active-secondaries-readable-secondary-replicas-always-on-availability-groups.md) 기능을 말합니다.</span><span class="sxs-lookup"><span data-stu-id="39dda-104">*Read-only routing* refers to the ability of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] to route qualifying read-only connection requests to an available AlwaysOn [readable secondary replica](active-secondaries-readable-secondary-replicas-always-on-availability-groups.md) (that is, a replica that is configured to allow read-only workloads when running under the secondary role).</span></span> <span data-ttu-id="39dda-105">읽기 전용 라우팅을 지원하려면 가용성 그룹에 [가용성 그룹 수신기](../../listeners-client-connectivity-application-failover.md)가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="39dda-105">To support read-only routing, the availability group must possess an [availability group listener](../../listeners-client-connectivity-application-failover.md).</span></span> <span data-ttu-id="39dda-106">읽기 전용 클라이언트는 해당 연결 요청을 이 수신기에 전달해야 하며, 클라이언트의 연결 문자열에서는 애플리케이션 의도를 "읽기 전용"으로 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="39dda-106">Read-only clients must direct their connection requests to this listener, and the client's connection strings must specify the application intent as "read-only."</span></span> <span data-ttu-id="39dda-107">즉, 해당 연결 요청은 *읽기 전용 연결 요청*이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="39dda-107">That is, they must be *read-intent connection requests*.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="39dda-108">읽기 가능한 보조 복제본을 구성하는 방법은 [가용성 복제본에 대한 읽기 전용 액세스 구성&#40;SQL Server&#41;](configure-read-only-access-on-an-availability-replica-sql-server.md)가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="39dda-108">For information about how to configure a readable secondary replica, see [Configure Read-Only Access on an Availability Replica &#40;SQL Server&#41;](configure-read-only-access-on-an-availability-replica-sql-server.md).</span></span>

> [!NOTE]
>  <span data-ttu-id="39dda-109">[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]에서는 읽기 전용 라우팅 구성이 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="39dda-109">Configuring read-only routing is not supported by [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)].</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="39dda-110">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="39dda-110">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="39dda-111">필수 조건</span><span class="sxs-lookup"><span data-stu-id="39dda-111">Prerequisites</span></span>  
  
-   <span data-ttu-id="39dda-112">가용성 그룹에 가용성 그룹 수신기가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="39dda-112">The availability group must possess an availability group listener.</span></span> <span data-ttu-id="39dda-113">자세한 내용은 [가용성 그룹 수신기 만들기 또는 구성&#40;SQL Server&#41;](create-or-configure-an-availability-group-listener-sql-server.md)가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="39dda-113">For more information, see [Create or Configure an Availability Group Listener &#40;SQL Server&#41;](create-or-configure-an-availability-group-listener-sql-server.md).</span></span>  
  
-   <span data-ttu-id="39dda-114">하나 이상의 가용성 복제본이 보조 역할에서 읽기 전용 (즉, 읽기 가능한 [보조 복제본](active-secondaries-readable-secondary-replicas-always-on-availability-groups.md)(AlwaysOn% 20Availability% 20availability))을 허용 하도록 구성 되어야 합니다 \) .</span><span class="sxs-lookup"><span data-stu-id="39dda-114">One or more availability replicas must be configured to accept read-only in the secondary role (that is, to be [readable secondary replicas](active-secondaries-readable-secondary-replicas-always-on-availability-groups.md)(AlwaysOn%20Availability%20Groups\).md)).</span></span> <span data-ttu-id="39dda-115">자세한 내용은 [가용성 복제본에 대한 읽기 전용 액세스 구성&#40;SQL Server&#41;](configure-read-only-access-on-an-availability-replica-sql-server.md)가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="39dda-115">For more information, see [Configure Read-Only Access on an Availability Replica &#40;SQL Server&#41;](configure-read-only-access-on-an-availability-replica-sql-server.md).</span></span>  
  
-   <span data-ttu-id="39dda-116">현재 주 복제본을 호스팅하는 서버 인스턴스에 연결되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="39dda-116">You must be connected to the server instance that hosts the current primary replica.</span></span>  
  
###  <a name="what-replica-properties-do-you-need-to-configure-to-support-read-only-routing"></a><a name="RORReplicaProperties"></a><span data-ttu-id="39dda-117">읽기 전용 라우팅을 지원 하도록 구성 하는 데 필요한 복제본 속성은 무엇 인가요?</span><span class="sxs-lookup"><span data-stu-id="39dda-117">What Replica Properties Do you Need to Configure to Support Read-Only Routing?</span></span>  
  
-   <span data-ttu-id="39dda-118">읽기 전용 라우팅을 지원할 읽기 가능한 보조 복제본 각각에 대해 *읽기 전용 라우팅 URL*을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="39dda-118">For each readable secondary replica that is to support read-only routing, you need to specify a *read-only routing URL*.</span></span> <span data-ttu-id="39dda-119">이 URL은 로컬 복제본이 보조 역할로 실행되는 경우에만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="39dda-119">This URL takes effect only when the local replica is running under the secondary role.</span></span> <span data-ttu-id="39dda-120">필요에 따라 복제본별로 읽기 전용 라우팅 URL을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="39dda-120">The read-only routing URL must be specified on a replica-by-replica basis, as needed.</span></span> <span data-ttu-id="39dda-121">각 읽기 전용 라우팅 URL은 읽기 전용 연결 요청을 지정된 읽기 가능한 보조 복제본으로 라우팅하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="39dda-121">Each read-only routing URL is used for routing read-intent connection requests to a specific readable secondary replica.</span></span> <span data-ttu-id="39dda-122">일반적으로 모든 읽기 가능한 보조 복제본에는 읽기 전용 라우팅 URL이 할당됩니다.</span><span class="sxs-lookup"><span data-stu-id="39dda-122">Typically, every readable secondary replica is assigned a read-only routing URL.</span></span>  
  
     <span data-ttu-id="39dda-123">가용성 복제본에 대한 읽기 전용 라우팅 URL을 계산하는 방법에 대한 자세한 내용은 [AlwaysOn에 대한 read_only_routing_url 계산](https://docs.microsoft.com/archive/blogs/mattn/calculating-read_only_routing_url-for-alwayson)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="39dda-123">For information about calculating the read-only routing URL for an availability replica, see [Calculating read_only_routing_url for AlwaysOn](https://docs.microsoft.com/archive/blogs/mattn/calculating-read_only_routing_url-for-alwayson).</span></span>  
  
-   <span data-ttu-id="39dda-124">주 복제본으로 사용될 때 읽기 전용 라우팅을 지원하도록 할 각 가용성 복제본에 대해 *읽기 전용 라우팅 목록*을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="39dda-124">For each availability replica that you want to support read-only routing when it is the primary replica, you need to specify a *read-only routing list*.</span></span> <span data-ttu-id="39dda-125">지정된 읽기 전용 라우팅 목록은 로컬 복제본이 주 역할로 실행되는 경우에만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="39dda-125">A given read-only routing list takes effect only when the local replica is running under the primary role.</span></span> <span data-ttu-id="39dda-126">필요에 따라 복제본별로 이 목록을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="39dda-126">This list must be specified on a replica-by-replica basis, as needed.</span></span> <span data-ttu-id="39dda-127">일반적으로 각 읽기 전용 라우팅 목록의 끝에는 로컬 복제본의 URL과 함께 모든 읽기 전용 라우팅 URL이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="39dda-127">Typically, each read-only routing list would contain every read-only routing URL, with the URL of the local replica at the end of the list.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="39dda-128">읽기 전용 연결 요청은 현재 주 복제본의 읽기 전용 라우팅 목록에 있는 사용 가능하고 읽기 가능한 첫 번째 보조 복제본으로 라우팅됩니다.</span><span class="sxs-lookup"><span data-stu-id="39dda-128">Read-intent connection requests are routed to the first available readable secondary on the read-only routing list of the current primary replica.</span></span> <span data-ttu-id="39dda-129">부하 분산은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="39dda-129">There is no load balancing.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="39dda-130">가용성 그룹 수신기 및 읽기 전용 라우팅에 대한 자세한 내용은 [가용성 그룹 수신기, 클라이언트 연결 및 애플리케이션 장애 조치(failover)&#40;SQL Server&#41;](../../listeners-client-connectivity-application-failover.md)가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="39dda-130">For information about availability group listeners and more information about read-only routing, see [Availability Group Listeners, Client Connectivity, and Application Failover &#40;SQL Server&#41;](../../listeners-client-connectivity-application-failover.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="39dda-131">보안</span><span class="sxs-lookup"><span data-stu-id="39dda-131">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="39dda-132">권한</span><span class="sxs-lookup"><span data-stu-id="39dda-132">Permissions</span></span>  
  
|<span data-ttu-id="39dda-133">Task</span><span class="sxs-lookup"><span data-stu-id="39dda-133">Task</span></span>|<span data-ttu-id="39dda-134">사용 권한</span><span class="sxs-lookup"><span data-stu-id="39dda-134">Permissions</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="39dda-135">가용성 그룹을 만들 때 복제본을 구성하려면</span><span class="sxs-lookup"><span data-stu-id="39dda-135">To configure replicas when creating an availability group</span></span>|<span data-ttu-id="39dda-136">CREATE AVAILABILITY GROUP 서버 권한, ALTER ANY AVAILABILITY GROUP 권한, CONTROL SERVER 권한 중 하나와 **sysadmin** 고정 서버 역할의 멤버 자격이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="39dda-136">Requires membership in the **sysadmin** fixed server role and either CREATE AVAILABILITY GROUP server permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>|  
|<span data-ttu-id="39dda-137">가용성 복제본을 수정하려면</span><span class="sxs-lookup"><span data-stu-id="39dda-137">To modify an availability replica</span></span>|<span data-ttu-id="39dda-138">가용성 그룹에 대한 ALTER AVAILABILITY GROUP 권한, CONTROL AVAILABILITY GROUP 권한, ALTER ANY AVAILABILITY GROUP 권한 또는 CONTROL SERVER 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="39dda-138">Requires ALTER AVAILABILITY GROUP permission on the availability group, CONTROL AVAILABILITY GROUP permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>|  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="39dda-139">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="39dda-139">Using Transact-SQL</span></span>  
 <span data-ttu-id="39dda-140">**읽기 전용 라우팅을 구성하려면**</span><span class="sxs-lookup"><span data-stu-id="39dda-140">**To Configure read-only routing**</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="39dda-141">코드 예제를 보려면 이 섹션의 뒷부분에 나오는 [예(Transact-SQL)](#TsqlExample)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="39dda-141">For a code example, see [Example (Transact-SQL)](#TsqlExample), later in this section.</span></span>  
  
1.  <span data-ttu-id="39dda-142">주 복제본을 호스팅하는 서버 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="39dda-142">Connect to the server instance that hosts the primary replica.</span></span>  
  
2.  <span data-ttu-id="39dda-143">새 가용성 그룹에 대한 복제본을 지정하려는 경우 [CREATE AVAILABILITY GROUP](/sql/t-sql/statements/create-availability-group-transact-sql)[!INCLUDE[tsql](../../../includes/tsql-md.md)] 문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="39dda-143">If you are specifying a replica for a new availability group, use the [CREATE AVAILABILITY GROUP](/sql/t-sql/statements/create-availability-group-transact-sql)[!INCLUDE[tsql](../../../includes/tsql-md.md)] statement.</span></span> <span data-ttu-id="39dda-144">기존 가용성 그룹에 대 한 복제본을 추가 하거나 수정 하는 경우 [ALTER AVAILABILITY group](/sql/t-sql/statements/alter-availability-group-transact-sql) [!INCLUDE[tsql](../../../includes/tsql-md.md)] 문을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="39dda-144">If you are adding or modifying a replica for an existing availability group, use the [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql)[!INCLUDE[tsql](../../../includes/tsql-md.md)] statement.</span></span>  
  
    -   <span data-ttu-id="39dda-145">보조 역할에 대한 읽기 전용 라우팅을 구성하려면 ADD REPLICA 또는 MODIFY REPLICA WITH 절에서 다음과 같이 SECONDARY_ROLE 옵션을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="39dda-145">To configure read-only routing for the secondary role, in the ADD REPLICA or MODIFY REPLICA WITH clause, specify the SECONDARY_ROLE option, as follows:</span></span>  
  
         <span data-ttu-id="39dda-146">SECONDARY_ROLE **(** READ_ONLY_ROUTING_URL **= '** TCP **:// *`system-address`* : *`port`* ')**</span><span class="sxs-lookup"><span data-stu-id="39dda-146">SECONDARY_ROLE **(** READ_ONLY_ROUTING_URL **='** TCP **://*`system-address`*:*`port`*')**</span></span>  
  
         <span data-ttu-id="39dda-147">읽기 전용 라우팅 URL의 매개 변수는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="39dda-147">The parameters of the read-only routing URL are as follows:</span></span>  
  
         <span data-ttu-id="39dda-148">*system-address*</span><span class="sxs-lookup"><span data-stu-id="39dda-148">*system-address*</span></span>  
         <span data-ttu-id="39dda-149">대상 컴퓨터 시스템을 명확하게 식별하는 시스템 이름, 정규화된 도메인 이름 또는 IP 주소 등의 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="39dda-149">Is a string, such as a system name, a fully qualified domain name, or an IP address, that unambiguously identifies the destination computer system.</span></span>  
  
         <span data-ttu-id="39dda-150">*port*</span><span class="sxs-lookup"><span data-stu-id="39dda-150">*port*</span></span>  
         <span data-ttu-id="39dda-151">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스의 데이터베이스 엔진에서 사용하는 포트 번호입니다.</span><span class="sxs-lookup"><span data-stu-id="39dda-151">Is a port number that is used by the Database Engine of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance.</span></span>  
  
         <span data-ttu-id="39dda-152">예를 들어   `SECONDARY_ROLE (READ_ONLY_ROUTING_URL = N'TCP://COMPUTER01.contoso.com:1433')`</span><span class="sxs-lookup"><span data-stu-id="39dda-152">For example:   `SECONDARY_ROLE (READ_ONLY_ROUTING_URL = N'TCP://COMPUTER01.contoso.com:1433')`</span></span>  
  
         <span data-ttu-id="39dda-153">복제본이 읽기 전용 연결을 허용하도록 이미 구성되어 있는 경우 MODIFY REPLICA 절에서 ALLOW_CONNECTIONS는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="39dda-153">In a MODIFY REPLICA clause the ALLOW_CONNECTIONS is optional if the replica is already configured to allow read-only connections.</span></span>  
  
         <span data-ttu-id="39dda-154">자세한 내용은 [AlwaysOn에 대한 read_only_routing_url 계산](https://docs.microsoft.com/archive/blogs/mattn/calculating-read_only_routing_url-for-alwayson)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="39dda-154">For more information, see [Calculating read_only_routing_url for AlwaysOn](https://docs.microsoft.com/archive/blogs/mattn/calculating-read_only_routing_url-for-alwayson).</span></span>  
  
    -   <span data-ttu-id="39dda-155">주 역할에 대한 읽기 전용 라우팅을 구성하려면 ADD REPLICA 또는 MODIFY REPLICA WITH 절에서 다음과 같이 PRIMARY_ROLE 옵션을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="39dda-155">To configure read-only routing for the primary role, in the ADD REPLICA or MODIFY REPLICA WITH clause, specify the PRIMARY_ROLE option, as follows:</span></span>  
  
         <span data-ttu-id="39dda-156">PRIMARY_ROLE **(** READ_ONLY_ROUTING_LIST **= (' *`server`* '** [ **,**... *n* ] **))**</span><span class="sxs-lookup"><span data-stu-id="39dda-156">PRIMARY_ROLE **(** READ_ONLY_ROUTING_LIST **=('*`server`*'** [ **,**...*n* ] **))**</span></span>  
  
         <span data-ttu-id="39dda-157">여기서 *server* 는 가용성 그룹의 읽기 전용 보조 복제본을 호스트하는 서버 인스턴스를 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="39dda-157">where, *server* identifies a server instance that hosts a read-only secondary replica in the availability group.</span></span>  
  
         <span data-ttu-id="39dda-158">예를 들어   `PRIMARY_ROLE (READ_ONLY_ROUTING_LIST=('Server1','Server2'))`</span><span class="sxs-lookup"><span data-stu-id="39dda-158">For example:   `PRIMARY_ROLE (READ_ONLY_ROUTING_LIST=('Server1','Server2'))`</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="39dda-159">읽기 전용 라우팅 목록을 구성하기 전에 읽기 전용 라우팅 URL을 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="39dda-159">You must set the read-only routing URL before configuring the read-only routing list.</span></span>  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="39dda-160">예(Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="39dda-160">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="39dda-161">다음 예에서는 기존 가용성 그룹 `AG1` 의 두 가용성 복제본 중 하나가 현재 주 역할을 소유하고 있는 경우 가용성 복제본이 읽기 전용 라우팅을 지원하도록 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="39dda-161">The following example modifies two availability replicas of an existing availability group, `AG1` to support read-only routing if one of these replicas currently owns the primary role.</span></span> <span data-ttu-id="39dda-162">가용성 복제본을 호스팅하는 서버 인스턴스를 식별하려면 이 예제에서는 `COMPUTER01` 및 `COMPUTER02` 인스턴스 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="39dda-162">To identify the server instances that host the availability replica, this example specifies the instance names-`COMPUTER01` and `COMPUTER02`.</span></span>  
  
```sql
ALTER AVAILABILITY GROUP [AG1]  
 MODIFY REPLICA ON  
N'COMPUTER01' WITH   
(SECONDARY_ROLE (ALLOW_CONNECTIONS = READ_ONLY));  
ALTER AVAILABILITY GROUP [AG1]  
 MODIFY REPLICA ON  
N'COMPUTER01' WITH   
(SECONDARY_ROLE (READ_ONLY_ROUTING_URL = N'TCP://COMPUTER01.contoso.com:1433'));  
  
ALTER AVAILABILITY GROUP [AG1]  
 MODIFY REPLICA ON  
N'COMPUTER02' WITH   
(SECONDARY_ROLE (ALLOW_CONNECTIONS = READ_ONLY));  
ALTER AVAILABILITY GROUP [AG1]  
 MODIFY REPLICA ON  
N'COMPUTER02' WITH   
(SECONDARY_ROLE (READ_ONLY_ROUTING_URL = N'TCP://COMPUTER02.contoso.com:1433'));  
  
ALTER AVAILABILITY GROUP [AG1]   
MODIFY REPLICA ON  
N'COMPUTER01' WITH   
(PRIMARY_ROLE (READ_ONLY_ROUTING_LIST=('COMPUTER02','COMPUTER01')));  
  
ALTER AVAILABILITY GROUP [AG1]   
MODIFY REPLICA ON  
N'COMPUTER02' WITH   
(PRIMARY_ROLE (READ_ONLY_ROUTING_LIST=('COMPUTER01','COMPUTER02')));  
GO
```  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> <span data-ttu-id="39dda-163">PowerShell 사용</span><span class="sxs-lookup"><span data-stu-id="39dda-163">Using PowerShell</span></span>  

### <a name="to-configure-read-only-routing"></a><span data-ttu-id="39dda-164">읽기 전용 라우팅을 구성하려면</span><span class="sxs-lookup"><span data-stu-id="39dda-164">To Configure read-only routing</span></span>
  
> [!NOTE]  
>  <span data-ttu-id="39dda-165">코드 예제를 보려면 이 섹션의 뒷부분에 나오는 [예제(PowerShell)](#PSExample)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="39dda-165">For a code example, see [Example (PowerShell)](#PSExample), later in this section.</span></span>  
  
1.  <span data-ttu-id="39dda-166">기본값(`cd`)을 주 복제본을 호스팅하는 서버 인스턴스로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="39dda-166">Set default (`cd`) to the server instance that hosts the primary replica.</span></span>  
  
2.  <span data-ttu-id="39dda-167">가용성 그룹에 가용성 복제본을 추가하는 경우 `New-SqlAvailabilityReplica` cmdlet을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="39dda-167">When adding an availability replica to an availability group, use the `New-SqlAvailabilityReplica` cmdlet.</span></span> <span data-ttu-id="39dda-168">기존 가용성 복제본을 수정하는 경우 `Set-SqlAvailabilityReplica` cmdlet을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="39dda-168">When modifying an existing availability replica, use the `Set-SqlAvailabilityReplica` cmdlet.</span></span> <span data-ttu-id="39dda-169">관련 매개 변수는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="39dda-169">The relevant parameters are as follows:</span></span>  
  
    -   <span data-ttu-id="39dda-170">보조 역할에 대 한 읽기 전용 라우팅을 구성 하려면 **하려면 readonlyroutingconnectionurl " *`url`* "** 매개 변수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="39dda-170">To configure read-only routing for the secondary role, specify the **ReadonlyRoutingConnectionUrl"*`url`*"** parameter.</span></span>  
  
         <span data-ttu-id="39dda-171">여기서 *url* 은 읽기 전용 연결을 위해 복제본으로 라우팅할 때 사용할 연결 FQDN(정규화된 도메인 이름) 및 포트입니다.</span><span class="sxs-lookup"><span data-stu-id="39dda-171">where, *url* is the connectivity fully-qualified domain name (FQDN) and port to use when routing to the replica for read-only connections.</span></span> <span data-ttu-id="39dda-172">예: `-ReadonlyRoutingConnectionUrl "TCP://DBSERVER8.manufacturing.Adventure-Works.com:7024"`</span><span class="sxs-lookup"><span data-stu-id="39dda-172">For example:  `-ReadonlyRoutingConnectionUrl "TCP://DBSERVER8.manufacturing.Adventure-Works.com:7024"`</span></span>  
  
         <span data-ttu-id="39dda-173">자세한 내용은 [AlwaysOn에 대한 read_only_routing_url 계산](https://docs.microsoft.com/archive/blogs/mattn/calculating-read_only_routing_url-for-alwayson)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="39dda-173">For more information, see [Calculating read_only_routing_url for AlwaysOn](https://docs.microsoft.com/archive/blogs/mattn/calculating-read_only_routing_url-for-alwayson).</span></span>  
  
    -   <span data-ttu-id="39dda-174">주 역할에 대 한 연결 액세스를 구성 하려면 **" *`server`* "** [ **,**... ReadonlyRoutingList를 지정 합니다. *n* ]. 여기서 *server* 는 가용성 그룹의 읽기 전용 보조 복제본을 호스팅하는 서버 인스턴스를 식별 합니다.</span><span class="sxs-lookup"><span data-stu-id="39dda-174">To configure connection access for the primary role, specify **ReadonlyRoutingList"*`server`*"** [ **,**...*n* ], where *server* identifies a server instance that hosts a read-only secondary replica in the availability group.</span></span> <span data-ttu-id="39dda-175">예: `-ReadOnlyRoutingList "SecondaryServer","PrimaryServer"`</span><span class="sxs-lookup"><span data-stu-id="39dda-175">For example:  `-ReadOnlyRoutingList "SecondaryServer","PrimaryServer"`</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="39dda-176">복제본의 읽기 전용 라우팅 목록을 구성하기 전에 읽기 전용 라우팅 URL을 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="39dda-176">You must set the read-only routing URL of a replica before configuring its read-only routing list.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="39dda-177">cmdlet의 구문을 보려면 `Get-Help` PowerShell 환경에서 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] cmdlet을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="39dda-177">To view the syntax of a cmdlet, use the `Get-Help` cmdlet in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell environment.</span></span> <span data-ttu-id="39dda-178">자세한 내용은 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="39dda-178">For more information, see [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).</span></span>  
  
<span data-ttu-id="39dda-179">SQL Server PowerShell 공급자를 설정 하 고 사용 하려면 [SQL Server PowerShell 공급자](../../../powershell/sql-server-powershell-provider.md) 를 참조 하 고 [SQL Server PowerShell 도움을 받으세요](../../../powershell/sql-server-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="39dda-179">To set up and use the SQL Server PowerShell provider, see [SQL Server PowerShell Provider](../../../powershell/sql-server-powershell-provider.md) and [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).</span></span>
  
###  <a name="example-powershell"></a><a name="PSExample"></a> <span data-ttu-id="39dda-180">예제(PowerShell)</span><span class="sxs-lookup"><span data-stu-id="39dda-180">Example (PowerShell)</span></span>  
 <span data-ttu-id="39dda-181">다음 예에서는 읽기 전용 라우팅을 위해 가용성 그룹에 주 복제본과 보조 복제본 하나를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="39dda-181">The following example configures the primary replica and one secondary replica in an availability group for read-only routing.</span></span> <span data-ttu-id="39dda-182">먼저, 이 예에서는 각 복제본에 읽기 전용 라우팅 URL을 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="39dda-182">First, the example assigns a read-only routing URL to each replica.</span></span> <span data-ttu-id="39dda-183">그런 다음 주 복제본에 읽기 전용 라우팅 목록을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="39dda-183">Then it sets the read-only routing list on the primary replica.</span></span> <span data-ttu-id="39dda-184">연결 문자열에 "ReadOnly" 속성이 설정된 연결은 보조 복제본으로 리디렉션됩니다.</span><span class="sxs-lookup"><span data-stu-id="39dda-184">Connections with the "ReadOnly" property set in the connection string will be redirected to the secondary replica.</span></span> <span data-ttu-id="39dda-185">이 보조 복제본을 읽을 수 없는 경우(`ConnectionModeInSecondaryRole` 설정으로 확인) 연결이 다시 주 복제본으로 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="39dda-185">If this secondary replica is not readable (as determined by the `ConnectionModeInSecondaryRole` setting), the connection will be directed back to the primary replica.</span></span>  
  
```powershell
Set-Location SQLSERVER:\SQL\PrimaryServer\default\AvailabilityGroups\MyAg  
$primaryReplica = Get-Item "AvailabilityReplicas\PrimaryServer"  
$secondaryReplica = Get-Item "AvailabilityReplicas\SecondaryServer"  
  
Set-SqlAvailabilityReplica -ReadOnlyRoutingConnectionUrl "TCP://PrimaryServer.domain.com:1433" -InputObject $primaryReplica  
Set-SqlAvailabilityReplica -ReadOnlyRoutingConnectionUrl "TCP://SecondaryServer.domain.com:1433" -InputObject $secondaryReplica  
Set-SqlAvailabilityReplica -ReadOnlyRoutingList "SecondaryServer","PrimaryServer" -InputObject $primaryReplica  
```  
  
##  <a name="follow-up-after-configuring-read-only-routing"></a><a name="FollowUp"></a> <span data-ttu-id="39dda-186">후속 작업: 읽기 전용 라우팅을 구성한 후의 작업</span><span class="sxs-lookup"><span data-stu-id="39dda-186">Follow Up: After Configuring Read-Only Routing</span></span>  
 <span data-ttu-id="39dda-187">현재 주 복제본과 읽기 가능한 보조 복제본 두 역할 모두가 읽기 전용 라우팅을 지원하도록 구성되고 나면 읽기 가능한 보조 복제본은 가용성 그룹 수신기를 통해 연결한 클라이언트로부터 읽기 전용 연결 요청을 받을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39dda-187">Once the current primary replica and the readable secondary replicas are configured to support read-only routing in both roles, the readable secondary replicas can receive read read-intent connection requests from clients that connect via the availability group listener.</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="39dda-188">[Bcp 유틸리티](../../../tools/bcp-utility.md) 또는 [sqlcmd 유틸리티](../../../tools/sqlcmd-utility.md)를 사용 하는 경우 스위치를 지정 하 여 읽기 전용 액세스를 사용 하도록 설정 된 보조 복제본에 대 한 읽기 전용 액세스를 지정할 수 있습니다 `-K ReadOnly` .</span><span class="sxs-lookup"><span data-stu-id="39dda-188">When using the [bcp Utility](../../../tools/bcp-utility.md) or [sqlcmd Utility](../../../tools/sqlcmd-utility.md), you can specify read-only access to any secondary replica that is enabled for read-only access by specifying the `-K ReadOnly` switch.</span></span>  
  
###  <a name="requirements-and-recommendations-for-client-connection-strings"></a><a name="ConnStringReqsRecs"></a> <span data-ttu-id="39dda-189">클라이언트 연결 문자열에 대한 요구 사항 및 권장 사항</span><span class="sxs-lookup"><span data-stu-id="39dda-189">Requirements and Recommendations for Client Connection-Strings</span></span>  
 <span data-ttu-id="39dda-190">클라이언트 애플리케이션에서 읽기 전용 라우팅을 사용하려면 해당 연결 문자열이 다음 요구 사항을 충족해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="39dda-190">For a client application to use read-only routing, its connection string must satisfy the following requirements:</span></span>  
  
-   <span data-ttu-id="39dda-191">TCP 프로토콜을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="39dda-191">Use the TCP protocol.</span></span>  
  
-   <span data-ttu-id="39dda-192">애플리케이션 의도 특성/속성을 읽기 전용으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="39dda-192">Set the application intent attribute/property to readonly.</span></span>  
  
-   <span data-ttu-id="39dda-193">읽기 전용 라우팅을 지원하도록 구성된 가용성 그룹의 수신기를 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="39dda-193">Reference the listener of an availability group that is configured to support read-only routing.</span></span>  
  
-   <span data-ttu-id="39dda-194">해당 가용성 그룹의 데이터베이스를 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="39dda-194">Reference a database in that availability group.</span></span>  
  
 <span data-ttu-id="39dda-195">또한 연결 문자열에서 각 서브넷의 각 복제본에 대해 병렬 클라이언트 스레드를 지원하는 다중 서브넷 장애 조치(Failover)를 설정하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="39dda-195">In addition, we recommend that connection strings enable multi-subnet failover, which supports a parallel client thread for each replica on each subnet.</span></span> <span data-ttu-id="39dda-196">이렇게 하면 장애 조치 후 클라이언트 재연결 시간이 최소화됩니다.</span><span class="sxs-lookup"><span data-stu-id="39dda-196">This minimizes client reconnection time after a failover.</span></span>  
  
 <span data-ttu-id="39dda-197">연결 문자열 구문은 애플리케이션에서 사용하는 SQL Server 공급자에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="39dda-197">The syntax for a connection string depends on the SQL Server provider an application is using.</span></span> <span data-ttu-id="39dda-198">다음 예에 나온 .NET Framework Data Provider 4.0.2 for SQL Server용 연결 문자열은 읽기 전용 라우팅에 사용해야 하며 권장되는 연결 문자열을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="39dda-198">The following example connection string for the .NET Framework Data Provider 4.0.2 for SQL Server illustrates the parts of a connection string that are required and recommended to work for read-only routing.</span></span>  
  
```  
Server=tcp:MyAgListener,1433;Database=Db1;IntegratedSecurity=SSPI;ApplicationIntent=ReadOnly;MultiSubnetFailover=True  
```  
  
 <span data-ttu-id="39dda-199">읽기 전용 애플리케이션 방식 및 읽기 전용 라우팅에 대한 자세한 내용은 [가용성 그룹 수신기, 클라이언트 연결 및 애플리케이션 장애 조치(failover)&#40;SQL Server&#41;](../../listeners-client-connectivity-application-failover.md)가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="39dda-199">For more information about read-only application intent and read-only routing, see [Availability Group Listeners, Client Connectivity, and Application Failover &#40;SQL Server&#41;](../../listeners-client-connectivity-application-failover.md).</span></span>  
  
### <a name="if-read-only-routing-is-not-working-correctly"></a><span data-ttu-id="39dda-200">읽기 전용 라우팅이 올바르게 작동하지 않는 경우</span><span class="sxs-lookup"><span data-stu-id="39dda-200">If Read-Only Routing is Not Working Correctly</span></span>  
 <span data-ttu-id="39dda-201">읽기 전용 라우팅 구성 문제를 해결하는 방법은 [읽기 전용 라우팅이 올바르게 작동하지 않음](troubleshoot-always-on-availability-groups-configuration-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="39dda-201">For information about troubleshooting a read-only routing configuration, see [Read-Only Routing is Not Working Correctly](troubleshoot-always-on-availability-groups-configuration-sql-server.md).</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="39dda-202">관련 작업</span><span class="sxs-lookup"><span data-stu-id="39dda-202">Related Tasks</span></span>  

### <a name="to-view-read-only-routing-configurations"></a><span data-ttu-id="39dda-203">읽기 전용 라우팅 구성을 보려면</span><span class="sxs-lookup"><span data-stu-id="39dda-203">To view read-only routing configurations</span></span>
  
-   [<span data-ttu-id="39dda-204">sys.availability_read_only_routing_lists&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="39dda-204">sys.availability_read_only_routing_lists &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-availability-read-only-routing-lists-transact-sql)  
  
-   <span data-ttu-id="39dda-205">[sys.availability_replicas&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-availability-replicas-transact-sql)(**read_only_routing_url** column)</span><span class="sxs-lookup"><span data-stu-id="39dda-205">[sys.availability_replicas &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-availability-replicas-transact-sql) (**read_only_routing_url** column)</span></span>  
  
### <a name="to-configure-client-connection-access"></a><span data-ttu-id="39dda-206">클라이언트 연결 액세스를 구성하려면</span><span class="sxs-lookup"><span data-stu-id="39dda-206">To configure client connection access</span></span>
  
-   [<span data-ttu-id="39dda-207">가용성 그룹 수신기 만들기 또는 구성&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="39dda-207">Create or Configure an Availability Group Listener &#40;SQL Server&#41;</span></span>](create-or-configure-an-availability-group-listener-sql-server.md)  
  
-   [<span data-ttu-id="39dda-208">가용성 복제본에 대한 읽기 전용 액세스 구성&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="39dda-208">Configure Read-Only Access on an Availability Replica &#40;SQL Server&#41;</span></span>](configure-read-only-access-on-an-availability-replica-sql-server.md)  
  
### <a name="to-use-connection-strings-in-applications"></a><span data-ttu-id="39dda-209">애플리케이션에서 연결 문자열을 사용하려면</span><span class="sxs-lookup"><span data-stu-id="39dda-209">To use connection strings in applications</span></span>
  
-   [<span data-ttu-id="39dda-210">고가용성 재해 복구를 위한 SQL Server Native Client 지원</span><span class="sxs-lookup"><span data-stu-id="39dda-210">SQL Server Native Client Support for High Availability, Disaster Recovery</span></span>](../../../relational-databases/native-client/features/sql-server-native-client-support-for-high-availability-disaster-recovery.md)  
  
-   [<span data-ttu-id="39dda-211">SQL Server Native Client에서 연결 문자열 키워드 사용</span><span class="sxs-lookup"><span data-stu-id="39dda-211">Using Connection String Keywords with SQL Server Native Client</span></span>](../../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md)  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> <span data-ttu-id="39dda-212">관련 내용</span><span class="sxs-lookup"><span data-stu-id="39dda-212">Related Content</span></span>  
  
-   <span data-ttu-id="39dda-213">**블로그:**</span><span class="sxs-lookup"><span data-stu-id="39dda-213">**Blogs:**</span></span>  
  
     [<span data-ttu-id="39dda-214">AlwaysOn에 대한 read_only_routing_url 계산</span><span class="sxs-lookup"><span data-stu-id="39dda-214">Calculating read_only_routing_url for AlwaysOn</span></span>](https://docs.microsoft.com/archive/blogs/mattn/calculating-read_only_routing_url-for-alwayson)  
  
     [<span data-ttu-id="39dda-215">SQL Server AlwaysOn 팀 블로그: 공식 SQL Server AlwaysOn 팀 블로그</span><span class="sxs-lookup"><span data-stu-id="39dda-215">SQL Server AlwaysOn Team Blogs: The official SQL Server AlwaysOn Team Blog</span></span>](https://blogs.msdn.com/b/sqlalwayson/)  
  
     [<span data-ttu-id="39dda-216">CSS SQL Server 엔지니어 블로그</span><span class="sxs-lookup"><span data-stu-id="39dda-216">CSS SQL Server Engineers Blogs</span></span>](https://blogs.msdn.com/b/psssql/)  
  
-   <span data-ttu-id="39dda-217">**백서:**</span><span class="sxs-lookup"><span data-stu-id="39dda-217">**White papers:**</span></span>  
  
     [<span data-ttu-id="39dda-218">SQL Server 2012에 대한 Microsoft 백서</span><span class="sxs-lookup"><span data-stu-id="39dda-218">Microsoft White Papers for SQL Server 2012</span></span>](https://msdn.microsoft.com/library/hh403491.aspx)  
  
     [<span data-ttu-id="39dda-219">SQL Server 고객 자문 팀 백서</span><span class="sxs-lookup"><span data-stu-id="39dda-219">SQL Server Customer Advisory Team Whitepapers</span></span>](http://sqlcat.com/)  
  
## <a name="see-also"></a><span data-ttu-id="39dda-220">참고 항목</span><span class="sxs-lookup"><span data-stu-id="39dda-220">See Also</span></span>  
 <span data-ttu-id="39dda-221">[AlwaysOn 가용성 그룹 &#40;SQL Server 개요&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="39dda-221">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="39dda-222">[AlwaysOn 가용성 그룹 &#40;SQL Server 개요&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="39dda-222">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="39dda-223">[활성 보조: 읽기 가능한 보조 복제본 (AlwaysOn 가용성 그룹)](active-secondaries-readable-secondary-replicas-always-on-availability-groups.md) </span><span class="sxs-lookup"><span data-stu-id="39dda-223">[Active Secondaries: Readable Secondary Replicas (AlwaysOn Availability Groups)](active-secondaries-readable-secondary-replicas-always-on-availability-groups.md) </span></span>  
 <span data-ttu-id="39dda-224">[가용성 복제본에 대한 클라이언트 연결 액세스 정보&#40;SQL Server&#41;](about-client-connection-access-to-availability-replicas-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="39dda-224">[About Client Connection Access to Availability Replicas &#40;SQL Server&#41;](about-client-connection-access-to-availability-replicas-sql-server.md) </span></span>  
 [<span data-ttu-id="39dda-225">가용성 그룹 수신기, 클라이언트 연결 및 애플리케이션 장애 조치(failover)&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="39dda-225">Availability Group Listeners, Client Connectivity, and Application Failover &#40;SQL Server&#41;</span></span>](../../listeners-client-connectivity-application-failover.md)  
