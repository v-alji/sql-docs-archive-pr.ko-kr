---
title: 서버 인스턴스의 HADR 클러스터 컨텍스트 변경(SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], WSFC clusters
- Availability replicas [SQL Server], change WSFC cluster context
ms.assetid: ecd99f91-b9a2-4737-994e-507065a12f80
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: cbc29fa2ebaaf2bbc9e577b5bd303e8a0dd0ec4c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741316"
---
# <a name="change-the-hadr-cluster-context-of-server-instance-sql-server"></a><span data-ttu-id="ce41e-102">서버 인스턴스의 HADR 클러스터 컨텍스트 변경(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="ce41e-102">Change the HADR Cluster Context of Server Instance (SQL Server)</span></span>
  <span data-ttu-id="ce41e-103">이 항목에서는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 이상 버전에서 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 을 사용하여 [!INCLUDE[ssSQL11SP1](../../../includes/sssql11sp1-md.md)] 인스턴스의 HADR 클러스터 컨텍스트를 전환하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="ce41e-103">This topic describes how to switch the HADR cluster context of an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] by using [!INCLUDE[tsql](../../../includes/tsql-md.md)] in [!INCLUDE[ssSQL11SP1](../../../includes/sssql11sp1-md.md)] and later versions.</span></span> <span data-ttu-id="ce41e-104">*HADR 클러스터 컨텍스트* 는 서버 인스턴스에서 호스트하는 가용성 복제본에 대한 메타데이터를 관리하는 WSFC(Windows Server 장애 조치(failover) 클러스터링) 클러스터를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="ce41e-104">The *HADR cluster context* determines which Windows Server Failover Clustering (WSFC) cluster manages the metadata for availability replicas hosted by the server instance.</span></span>  
  
 <span data-ttu-id="ce41e-105">새 WSFC 클러스터에서 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 인스턴스로의 클러스터 간 [!INCLUDE[ssSQL11SP1](../../../includes/sssql11sp1-md.md)] 마이그레이션을 수행하는 동안에만 HADR 클러스터 컨텍스트를 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="ce41e-105">Switch the HADR cluster context only during a cross-cluster migration of [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] to an instance of [!INCLUDE[ssSQL11SP1](../../../includes/sssql11sp1-md.md)] on a new WSFC cluster.</span></span> <span data-ttu-id="ce41e-106">[!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 의 클러스터 간 마이그레이션은 가용성 그룹의 작동 중단 시간을 최소화하면서 [!INCLUDE[win8](../../../includes/win8-md.md)] 또는 [!INCLUDE[win8srv](../../../includes/win8srv-md.md)] 로의 OS 업그레이드를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="ce41e-106">Cross-cluster migration of [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] supports OS upgrade to [!INCLUDE[win8](../../../includes/win8-md.md)] or [!INCLUDE[win8srv](../../../includes/win8srv-md.md)] with minimal downtime of availability groups.</span></span> <span data-ttu-id="ce41e-107">자세한 내용은 [OS 업그레이드를 위한 AlwaysOn 가용성 그룹의 클러스터 간 마이그레이션](https://msdn.microsoft.com/library/jj873730.aspx)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="ce41e-107">For more information, see [Cross-Cluster Migration of AlwaysOn Availability Groups for OS Upgrade](https://msdn.microsoft.com/library/jj873730.aspx).</span></span>  
  

  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="ce41e-108">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="ce41e-108">Before You Begin</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="ce41e-109">[!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 배포의 클러스터 간 마이그레이션 중에만 HADR 클러스터 컨텍스트를 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="ce41e-109">Switch the HADR cluster context only during cross-cluster migration of [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] deployments.</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="ce41e-110">제한 사항</span><span class="sxs-lookup"><span data-stu-id="ce41e-110">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="ce41e-111">HADR 클러스터 컨텍스트는 로컬 WSFC 클러스터에서 원격 클러스터로 전환한 다음 다시 원격 클러스터에서 로컬 클러스터로만 전환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce41e-111">You can switch the HADR cluster context only from the local WSFC cluster to a remote cluster and then back from the remote cluster to the local cluster.</span></span> <span data-ttu-id="ce41e-112">HADR 클러스터 컨텍스트를 원격 클러스터 간에 전환할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ce41e-112">You cannot switch the HADR cluster context from one remote cluster to another remote cluster.</span></span>  
  
-   <span data-ttu-id="ce41e-113">HADR 클러스터 컨텍스트는 SQL Server 인스턴스에서 가용성 복제본을 호스팅하지 않을 때만 원격 클러스터로 전환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce41e-113">The HADR cluster context can be switched to a remote cluster only when the instance of SQL Server is not hosting any availability replicas.</span></span>  
  
-   <span data-ttu-id="ce41e-114">원격 HADR 클러스터 컨텍스트는 언제든지 로컬 클러스터로 다시 전환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce41e-114">A remote HADR cluster context can be switched back to the local cluster at any time.</span></span> <span data-ttu-id="ce41e-115">그러나 서버 인스턴스에서 가용성 복제본을 호스팅하는 동안에는 컨텍스트를 다시 전환할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ce41e-115">However, the context cannot be switched again as long as the server instance is hosting any availability replicas.</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="ce41e-116">필수 조건</span><span class="sxs-lookup"><span data-stu-id="ce41e-116">Prerequisites</span></span>  
  
-   <span data-ttu-id="ce41e-117">HADR 클러스터 컨텍스트를 변경하는 서버 인스턴스에서는 [!INCLUDE[ssSQL11SP1](../../../includes/sssql11sp1-md.md)] 이상(Enterprise Edition 이상)을 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce41e-117">The server instance on which you change the HADR cluster context must be running [!INCLUDE[ssSQL11SP1](../../../includes/sssql11sp1-md.md)] or above (Enterprise edition or above).</span></span>  
  
-   <span data-ttu-id="ce41e-118">서버 인스턴스는 AlwaysOn을 사용하도록 설정되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce41e-118">The server instance must be enabled for AlwaysOn.</span></span> <span data-ttu-id="ce41e-119">자세한 내용은 [AlwaysOn 가용성 그룹 활성화 및 비활성화&#40;SQL Server&#41;](enable-and-disable-always-on-availability-groups-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ce41e-119">For more information, see [Enable and Disable AlwaysOn Availability Groups &#40;SQL Server&#41;](enable-and-disable-always-on-availability-groups-sql-server.md).</span></span>  
  
-   <span data-ttu-id="ce41e-120">로컬 클러스터 컨텍스트에서 원격 클러스터 컨텍스트로 전환하려면 서버 인스턴스에서 가용성 복제본을 호스팅해서는 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ce41e-120">To be eligible to be switched from the local cluster context to a remote cluster cluster, a server instance cannot be hosting any availability replicas.</span></span> <span data-ttu-id="ce41e-121">[sys.availability_replicas](/sql/relational-databases/system-catalog-views/sys-availability-replicas-transact-sql) 카탈로그 뷰는 행을 반환해서는 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ce41e-121">The [sys.availability_replicas](/sql/relational-databases/system-catalog-views/sys-availability-replicas-transact-sql) catalog view should not return any rows.</span></span>  
  
     <span data-ttu-id="ce41e-122">서버 인스턴스에 가용성 복제본이 있을 경우 HADR 클러스터 컨텍스트를 변경하려면 먼저 다음 중 하나를 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce41e-122">If any availability replicas exist on the server instance, before you can change the HADR cluster context, you must do one of the following:</span></span>  
  
    |<span data-ttu-id="ce41e-123">복제본 역할</span><span class="sxs-lookup"><span data-stu-id="ce41e-123">Replica Role</span></span>|<span data-ttu-id="ce41e-124">작업</span><span class="sxs-lookup"><span data-stu-id="ce41e-124">Action</span></span>|<span data-ttu-id="ce41e-125">링크</span><span class="sxs-lookup"><span data-stu-id="ce41e-125">Link</span></span>|  
    |------------------|------------|----------|  
    |<span data-ttu-id="ce41e-126">주</span><span class="sxs-lookup"><span data-stu-id="ce41e-126">Primary</span></span>|<span data-ttu-id="ce41e-127">가용성 그룹을 오프라인 상태로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ce41e-127">Take the availability group offline.</span></span>|[<span data-ttu-id="ce41e-128">가용성 그룹을 오프라인 상태로 만들기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="ce41e-128">Take an Availability Group Offline &#40;SQL Server&#41;</span></span>](../../take-an-availability-group-offline-sql-server.md)|  
    |<span data-ttu-id="ce41e-129">보조</span><span class="sxs-lookup"><span data-stu-id="ce41e-129">Secondary</span></span>|<span data-ttu-id="ce41e-130">가용성 그룹에서 복제본 제거</span><span class="sxs-lookup"><span data-stu-id="ce41e-130">Remove the replica from its availability group</span></span>|[<span data-ttu-id="ce41e-131">가용성 그룹에서 보조 복제본 제거&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="ce41e-131">Remove a Secondary Replica from an Availability Group &#40;SQL Server&#41;</span></span>](remove-a-secondary-replica-from-an-availability-group-sql-server.md)|  
  
-   <span data-ttu-id="ce41e-132">원격 클러스터에서 로컬 클러스터로 전환하려면 먼저 모든 동기 커밋 복제본을 동기화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce41e-132">Before you can switch from a remote cluster to the local cluster, all synchronous-commit replicas must be SYNCHRONIZED.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="ce41e-133">권장 사항</span><span class="sxs-lookup"><span data-stu-id="ce41e-133">Recommendations</span></span>  
  
-   <span data-ttu-id="ce41e-134">전체 도메인 이름을 지정하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="ce41e-134">We recommend that you specify the full domain name.</span></span> <span data-ttu-id="ce41e-135">이는 짧은 이름의 대상 IP 주소를 찾기 위해 ALTER SERVER CONFIGURATION에서 DNS 확인을 사용하기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="ce41e-135">This is because to find the target IP address of a short name, ALTER SERVER CONFIGURATION uses DNS resolution.</span></span> <span data-ttu-id="ce41e-136">경우에 따라 짧은 이름을 사용하면 DNS 검색 순서로 인해 혼동이 생길 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce41e-136">Under some situations, depending on the DNS searching order, using a short name could cause confusion.</span></span> <span data-ttu-id="ce41e-137">예를 들어 `abc` 도메인의 노드(`node1.abc.com`)에서 다음 명령을 실행한다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="ce41e-137">For example, consider the following command, which is executed on a node in the `abc` domain, (`node1.abc.com`).</span></span> <span data-ttu-id="ce41e-138">의도한 대상 클러스터는 `CLUS01` 도메인의 `xyz` 클러스터(`clus01.xyz.com`)입니다.</span><span class="sxs-lookup"><span data-stu-id="ce41e-138">The intended destination cluster is the `CLUS01` cluster in the `xyz` domain (`clus01.xyz.com`).</span></span> <span data-ttu-id="ce41e-139">그러나 로컬 도메인 호스트는 이름이 `CLUS01` 인 클러스터(`clus01.abc.com`)도 호스팅합니다.</span><span class="sxs-lookup"><span data-stu-id="ce41e-139">However, the local  domain hosts also hosts a cluster named `CLUS01` (`clus01.abc.com`).</span></span>  
  
     <span data-ttu-id="ce41e-140">대상 클러스터의 짧은 이름인 `CLUS01`이 지정된 경우 DNS 이름 확인이 잘못된 클러스터의 IP 주소인 `clus01.abc.com`을 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce41e-140">If the short name of the target cluster, `CLUS01`, were specified, DNS name resolution could return the IP address of the wrong cluster, `clus01.abc.com`.</span></span> <span data-ttu-id="ce41e-141">이러한 혼동을 방지하려면 다음 예와 같은 대상 클러스터의 전체 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ce41e-141">To avoid such confusion, specify the full name of the target cluster, as in the following example:</span></span>  
  
    ```  
    ALTER SERVER CONFIGURATION SET HADR CLUSTER CONTEXT = 'clus01.xyz.com'  
    ```  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="ce41e-142">보안</span><span class="sxs-lookup"><span data-stu-id="ce41e-142">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="ce41e-143">권한</span><span class="sxs-lookup"><span data-stu-id="ce41e-143">Permissions</span></span>  
  
-   <span data-ttu-id="ce41e-144">**SQL Server 로그인(SQL Server login)**</span><span class="sxs-lookup"><span data-stu-id="ce41e-144">**SQL Server login**</span></span>  
  
     <span data-ttu-id="ce41e-145">CONTROL SERVER 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="ce41e-145">Requires CONTROL SERVER permission.</span></span>  
  
-   <span data-ttu-id="ce41e-146">**SQL Server 서비스 계정**</span><span class="sxs-lookup"><span data-stu-id="ce41e-146">**SQL Server service account**</span></span>  
  
     <span data-ttu-id="ce41e-147">서버 인스턴스의 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 서버스 계정에는 다음이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce41e-147">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] service account of the server instance must have:</span></span>  
  
    -   <span data-ttu-id="ce41e-148">대상 WSFC 클러스터를 열 수 있는 권한</span><span class="sxs-lookup"><span data-stu-id="ce41e-148">Permission to open the destination WSFC cluster.</span></span>  
  
    -   <span data-ttu-id="ce41e-149">원격 WSFC 읽기/쓰기 액세스</span><span class="sxs-lookup"><span data-stu-id="ce41e-149">Remote WSFC read-write access.</span></span>  
  
 
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="ce41e-150">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="ce41e-150">Using Transact-SQL</span></span>  
 <span data-ttu-id="ce41e-151">**가용성 복제본의 WSFC 클러스터 컨텍스트를 변경하려면**</span><span class="sxs-lookup"><span data-stu-id="ce41e-151">**To change the WSFC cluster context of an availability replica**</span></span>  
  
1.  <span data-ttu-id="ce41e-152">가용성 그룹의 주 복제본 또는 보조 복제본을 호스팅하는 서버 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="ce41e-152">Connect to the server instance that hosts either the primary replica or a secondary replica of the availability group.</span></span>  
  
2.  <span data-ttu-id="ce41e-153">다음과 같이 [ALTER SERVER CONFIGURATION](/sql/t-sql/statements/alter-server-configuration-transact-sql) 문의 SET HADR CLUSTER CONTEXT 절을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ce41e-153">Use the SET HADR CLUSTER CONTEXT clause of the [ALTER SERVER CONFIGURATION](/sql/t-sql/statements/alter-server-configuration-transact-sql) statement, as follows:</span></span>  
  
     <span data-ttu-id="ce41e-154">ALTER SERVER CONFIGURATION SET HADR CLUSTER CONTEXT **=** { **' *`windows_cluster`* '** | 로컬</span><span class="sxs-lookup"><span data-stu-id="ce41e-154">ALTER SERVER CONFIGURATION SET HADR CLUSTER CONTEXT **=** { **'*`windows_cluster`*'** | LOCAL }</span></span>  
  
     <span data-ttu-id="ce41e-155">각 항목이 나타내는 의미는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="ce41e-155">where,</span></span>  
  
     <span data-ttu-id="ce41e-156">*windows_cluster*</span><span class="sxs-lookup"><span data-stu-id="ce41e-156">*windows_cluster*</span></span>  
     <span data-ttu-id="ce41e-157">WSFC 클러스터의 CON(클러스터 개체 이름)</span><span class="sxs-lookup"><span data-stu-id="ce41e-157">The cluster object name (CON) of a WSFC cluster.</span></span> <span data-ttu-id="ce41e-158">짧은 이름 또는 전체 도메인 이름을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce41e-158">You can specify either the short name or the full domain name.</span></span> <span data-ttu-id="ce41e-159">전체 도메인 이름을 지정하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="ce41e-159">We recommend that you specify the full domain name.</span></span> <span data-ttu-id="ce41e-160">자세한 내용은이 항목의 앞부분에 나오는 [권장 사항](#Recommendations)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ce41e-160">For more information, see [Recommendations](#Recommendations), earlier in this topic.</span></span>  
  
     <span data-ttu-id="ce41e-161">LOCAL</span><span class="sxs-lookup"><span data-stu-id="ce41e-161">LOCAL</span></span>  
     <span data-ttu-id="ce41e-162">로컬 WSFC 클러스터입니다.</span><span class="sxs-lookup"><span data-stu-id="ce41e-162">The local WSFC cluster.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="ce41e-163">예</span><span class="sxs-lookup"><span data-stu-id="ce41e-163">Examples</span></span>  
 <span data-ttu-id="ce41e-164">다음 예에서는 HARD 클러스터 컨텍스트를 다른 클러스터로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="ce41e-164">The following example changes the HADR cluster context to a different cluster.</span></span> <span data-ttu-id="ce41e-165">이 예에서는 대상 WSFC 클러스터( `clus01`)를 식별하기 위해 전체 클러스터 개체 이름( `clus01.xyz.com`)을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ce41e-165">To identify the destination WSFC cluster, `clus01`, the example specifies the full cluster object name, `clus01.xyz.com`.</span></span>  
  
```  
ALTER SERVER CONFIGURATION SET HADR CLUSTER CONTEXT = 'clus01.xyz.com';  
```  
  
 <span data-ttu-id="ce41e-166">다음 예에서는 HARD 클러스터 컨텍스트를 로컬 WSFC 클러스터로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="ce41e-166">The following example changes the HADR cluster context to the local WSFC cluster.</span></span>  
  
```  
ALTER SERVER CONFIGURATION SET HADR CLUSTER CONTEXT = LOCAL;  
```  
  

  
##  <a name="follow-up-after-switching-the-cluster-context-of-an-availability-replica"></a><a name="FollowUp"></a> <span data-ttu-id="ce41e-167">후속 작업: 가용성 복제본의 클러스터 컨텍스트를 전환한 후</span><span class="sxs-lookup"><span data-stu-id="ce41e-167">Follow Up: After Switching the Cluster Context of an Availability Replica</span></span>  
 <span data-ttu-id="ce41e-168">새 HADR 클러스터 컨텍스트는 서버 인스턴스를 다시 시작하지 않아도 즉시 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="ce41e-168">The new HADR cluster context takes effect immediately, without restarting the server instance.</span></span> <span data-ttu-id="ce41e-169">HADR 클러스터 컨텍스트 설정은 서버 인스턴스를 다시 시작해도 변경되지 않은 영구 인스턴스 수준 설정입니다.</span><span class="sxs-lookup"><span data-stu-id="ce41e-169">The HADR cluster context setting is a persistent instance-level setting that remains unchanged if the server instance restarts.</span></span>  
  
 <span data-ttu-id="ce41e-170">다음과 같이 [sys.dm_hadr_cluster](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-cluster-transact-sql) 동적 관리 뷰를 쿼리하여 새 HADR 클러스터 컨텍스트를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="ce41e-170">Confirm the new HADR cluster context by querying the [sys.dm_hadr_cluster](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-cluster-transact-sql) dynamic management view, as follows:</span></span>  
  
```  
SELECT cluster_name FROM sys.dm_hadr_cluster  
```  
  
 <span data-ttu-id="ce41e-171">이 쿼리는 HADR 클러스터 컨텍스트를 설정한 클러스터의 이름을 반환해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce41e-171">This query should return the name of the cluster to which you set the HADR cluster context.</span></span>  
  
 <span data-ttu-id="ce41e-172">HADR 클러스터 컨텍스트가 새 클러스터로 전환될 경우:</span><span class="sxs-lookup"><span data-stu-id="ce41e-172">When the HADR cluster context is switched to a new cluster:</span></span>  
  
-   <span data-ttu-id="ce41e-173">현재 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]인스턴스에서 호스팅하는 가용성 복제본에 대한 메타데이터가 정리됩니다.</span><span class="sxs-lookup"><span data-stu-id="ce41e-173">The metadata is cleaned up for any availability replicas that are currently hosted by the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="ce41e-174">이전에 가용성 복제본에 속한 모든 데이터베이스가 RESTORING 상태가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ce41e-174">All the databases that previously belonged to an availability replica are now in the RESTORING state.</span></span>  
  
 
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="ce41e-175">관련 작업</span><span class="sxs-lookup"><span data-stu-id="ce41e-175">Related Tasks</span></span>  
  
-   [<span data-ttu-id="ce41e-176">가용성 그룹 수신기 제거&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="ce41e-176">Remove an Availability Group Listener &#40;SQL Server&#41;</span></span>](remove-an-availability-group-listener-sql-server.md)  
  
-   [<span data-ttu-id="ce41e-177">가용성 그룹을 오프라인 상태로 만들기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="ce41e-177">Take an Availability Group Offline &#40;SQL Server&#41;</span></span>](../../take-an-availability-group-offline-sql-server.md)  
  
-   [<span data-ttu-id="ce41e-178">가용성 그룹에 보조 복제본 추가&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="ce41e-178">Add a Secondary Replica to an Availability Group &#40;SQL Server&#41;</span></span>](add-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="ce41e-179">가용성 그룹에서 보조 복제본 제거&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="ce41e-179">Remove a Secondary Replica from an Availability Group &#40;SQL Server&#41;</span></span>](remove-a-secondary-replica-from-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="ce41e-180">가용성 그룹 수신기 만들기 또는 구성&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="ce41e-180">Create or Configure an Availability Group Listener &#40;SQL Server&#41;</span></span>](create-or-configure-an-availability-group-listener-sql-server.md)  
  
-   [<span data-ttu-id="ce41e-181">가용성 그룹에 보조 데이터베이스 조인&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="ce41e-181">Join a Secondary Database to an Availability Group &#40;SQL Server&#41;</span></span>](join-a-secondary-database-to-an-availability-group-sql-server.md)  
  
 
  
##  <a name="related-content"></a><a name="RelatedContent"></a> <span data-ttu-id="ce41e-182">관련 내용</span><span class="sxs-lookup"><span data-stu-id="ce41e-182">Related Content</span></span>  
  
-   <span data-ttu-id="ce41e-183">[SQL Server 2012 기술 문서](https://msdn.microsoft.com/library/bb418445\(SQL.10\).aspx)</span><span class="sxs-lookup"><span data-stu-id="ce41e-183">[SQL Server 2012 Technical Articles](https://msdn.microsoft.com/library/bb418445\(SQL.10\).aspx)</span></span>  
  
-   [<span data-ttu-id="ce41e-184">SQL Server AlwaysOn 팀 블로그: 공식 SQL Server AlwaysOn 팀 블로그</span><span class="sxs-lookup"><span data-stu-id="ce41e-184">SQL Server AlwaysOn Team Blog: The official SQL Server AlwaysOn Team Blog</span></span>](https://blogs.msdn.com/b/sqlalwayson/)  
  
  
  
## <a name="see-also"></a><span data-ttu-id="ce41e-185">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ce41e-185">See Also</span></span>  
 <span data-ttu-id="ce41e-186">[AlwaysOn Availability Groups (SQL Server)](always-on-availability-groups-sql-server.md) [WSFC&#41; &#40;SQL Server) Windows Server 장애 조치 (Failover) 클러스터링 AlwaysOn 가용성 그룹 SQL Server](../../../sql-server/failover-clusters/windows/windows-server-failover-clustering-wsfc-with-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="ce41e-186">[AlwaysOn Availability Groups (SQL Server)](always-on-availability-groups-sql-server.md) [Windows Server Failover Clustering &#40;WSFC&#41; with SQL Server](../../../sql-server/failover-clusters/windows/windows-server-failover-clustering-wsfc-with-sql-server.md) </span></span>  
 [<span data-ttu-id="ce41e-187">ALTER SERVER CONFIGURATION&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="ce41e-187">ALTER SERVER CONFIGURATION &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-server-configuration-transact-sql)  
  
  
