---
title: 가용성 그룹을 오프 라인으로 변경
description: Always On 가용성 그룹을 오프 라인으로 설정 하는 단계
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], take offline
ms.assetid: 50f5aad8-0dff-45ef-8350-f9596d3db898
author: rothja
ms.author: jroth
ms.openlocfilehash: db2f56befe6905b9c3de6bd1ab6a2e5a4a00b1b3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651874"
---
# <a name="take-an-availability-group-offline-sql-server"></a><span data-ttu-id="6b8c3-103">가용성 그룹을 오프라인 상태로 만들기(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="6b8c3-103">Take an Availability Group Offline (SQL Server)</span></span>
  <span data-ttu-id="6b8c3-104">이 항목에서는 [!INCLUDE[tsql](../includes/tsql-md.md)] 이상 버전에서 [!INCLUDE[ssSQL11SP1](../includes/sssql11sp1-md.md)] 을 사용하여 AlwaysOn 가용성 그룹을 ONLINE 상태에서 OFFLINE 상태로 변경하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="6b8c3-104">This topic describes how to take an AlwaysOn availability group from the ONLINE state to the OFFLINE state by using [!INCLUDE[tsql](../includes/tsql-md.md)] in [!INCLUDE[ssSQL11SP1](../includes/sssql11sp1-md.md)] and later versions.</span></span> <span data-ttu-id="6b8c3-105">동기 커밋 복제본이 동기화되지 않을 경우 OFFLINE 작업이 오류를 발생시키고 가용성 그룹을 ONLINE 상태로 유지하기 때문에 동기 커밋 데이터베이스의 데이터는 손실되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6b8c3-105">There is no data loss for synchronous-commit databases because if any synchronous-commit replica is not synchronized, the OFFLINE operation raises an error and leaves the availability group ONLINE.</span></span> <span data-ttu-id="6b8c3-106">가용성 그룹을 온라인 상태로 유지하면 데이터 손실이 발생하지 않도록 동기화되지 않은 동기화 커밋 데이터베이스가 보호됩니다.</span><span class="sxs-lookup"><span data-stu-id="6b8c3-106">Keeping the availability group online protects unsynchronized synchronous-commit databases from possible data loss.</span></span> <span data-ttu-id="6b8c3-107">가용성 그룹이 오프라인 상태로 전환된 후에는 클라이언트에서 해당 데이터베이스를 사용할 수 없게 되고 사용자가 가용성 그룹을 다시 온라인 상태로 전환할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6b8c3-107">After an availability group goes offline, its databases become unavailable to clients and you cannot bring the availability group back online.</span></span> <span data-ttu-id="6b8c3-108">따라서 WSFC 클러스터 간에 가용성 그룹 리소스를 마이그레이션하려는 경우에만 가용성 그룹을 오프라인으로 전환해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b8c3-108">Therefore, take an availability group offline only to migrate the availability group resources from one WSFC cluster to another.</span></span>  
  
 <span data-ttu-id="6b8c3-109">[!INCLUDE[ssHADR](../includes/sshadr-md.md)]의 클러스터 간 마이그레이션 중에 애플리케이션이 가용성 그룹의 주 복제본에 직접 연결할 경우 가용성 그룹을 오프라인 상태로 전환해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b8c3-109">During a cross-cluster migration of [!INCLUDE[ssHADR](../includes/sshadr-md.md)], if any applications connect directly to the primary replica of an availability group, the availability group must be taken offline.</span></span> <span data-ttu-id="6b8c3-110">[!INCLUDE[ssHADR](../includes/sshadr-md.md)] 의 클러스터 간 마이그레이션은 가용성 그룹의 작동 중단 시간을 최소화하면서 OS 업그레이드를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="6b8c3-110">Cross-cluster migration of [!INCLUDE[ssHADR](../includes/sshadr-md.md)] supports OS upgrade with minimal downtime of availability groups.</span></span> <span data-ttu-id="6b8c3-111">일반적으로 [!INCLUDE[ssHADR](../includes/sshadr-md.md)] 의 클러스터 간 마이그레이션은 OS를 [!INCLUDE[win8](../includes/win8-md.md)] 또는 [!INCLUDE[win8srv](../includes/win8srv-md.md)]로 업그레이드하려는 경우에 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6b8c3-111">The typical scenario is to use cross-cluster migration of [!INCLUDE[ssHADR](../includes/sshadr-md.md)] for OS upgrade to [!INCLUDE[win8](../includes/win8-md.md)] or [!INCLUDE[win8srv](../includes/win8srv-md.md)].</span></span> <span data-ttu-id="6b8c3-112">자세한 내용은 [OS 업그레이드를 위한 AlwaysOn 가용성 그룹의 클러스터 간 마이그레이션](https://msdn.microsoft.com/library/jj873730.aspx)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="6b8c3-112">For more information, see [Cross-Cluster Migration of AlwaysOn Availability Groups for OS Upgrade](https://msdn.microsoft.com/library/jj873730.aspx).</span></span>  
  

  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="6b8c3-113">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="6b8c3-113">Before You Begin</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="6b8c3-114">OFFLINE 옵션은 가용성 그룹 리소스의 클러스터 간 마이그레이션에만 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6b8c3-114">Use the OFFLINE option only for a cross-cluster migration of availability group resources.</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="6b8c3-115">필수 조건</span><span class="sxs-lookup"><span data-stu-id="6b8c3-115">Prerequisites</span></span>  
  
-   <span data-ttu-id="6b8c3-116">OFFLINE 명령을 입력하는 서버 인스턴스에서 [!INCLUDE[ssSQL11SP1](../includes/sssql11sp1-md.md)] 이상(Enterprise Edition 이상)을 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b8c3-116">The server instance on which you enter the OFFLINE command must be running [!INCLUDE[ssSQL11SP1](../includes/sssql11sp1-md.md)] or above (Enterprise edition or above).</span></span>  
  
-   <span data-ttu-id="6b8c3-117">가용성 그룹이 현재 온라인 상태여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b8c3-117">The availability group must currently be online.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="6b8c3-118">권장 사항</span><span class="sxs-lookup"><span data-stu-id="6b8c3-118">Recommendations</span></span>  
 <span data-ttu-id="6b8c3-119">가용성 그룹을 오프라인 상태로 전환하기 전에 가용성 그룹 수신기를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="6b8c3-119">Before you take the availability group offline, delete the availability group listener or listeners.</span></span> <span data-ttu-id="6b8c3-120">자세한 내용은 [가용성 그룹 수신기 제거&#40;SQL Server&#41;](availability-groups/windows/remove-an-availability-group-listener-sql-server.md)로 업그레이드하려는 경우에 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6b8c3-120">For more information, see [Remove an Availability Group Listener &#40;SQL Server&#41;](availability-groups/windows/remove-an-availability-group-listener-sql-server.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="6b8c3-121">보안</span><span class="sxs-lookup"><span data-stu-id="6b8c3-121">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="6b8c3-122">권한</span><span class="sxs-lookup"><span data-stu-id="6b8c3-122">Permissions</span></span>  
 <span data-ttu-id="6b8c3-123">가용성 그룹에 대한 ALTER AVAILABILITY GROUP 권한, CONTROL AVAILABILITY GROUP 권한, ALTER ANY AVAILABILITY GROUP 권한 또는 CONTROL SERVER 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="6b8c3-123">Requires ALTER AVAILABILITY GROUP permission on the availability group, CONTROL AVAILABILITY GROUP permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="6b8c3-124">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="6b8c3-124">Using Transact-SQL</span></span>  
 <span data-ttu-id="6b8c3-125">**가용성 그룹을 오프라인 상태로 전환하려면**</span><span class="sxs-lookup"><span data-stu-id="6b8c3-125">**To take an availability group offline**</span></span>  
  
1.  <span data-ttu-id="6b8c3-126">가용성 그룹의 가용성 복제본을 호스팅하는 서버 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="6b8c3-126">Connect to a server instance that hosts an availability replica for the availability group.</span></span> <span data-ttu-id="6b8c3-127">이 복제본은 주 복제본일 수도 있고 보조 복제본일 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6b8c3-127">This replica can be the primary replica or a secondary replica.</span></span>  
  
2.  <span data-ttu-id="6b8c3-128">다음과 같은 [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql) 문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6b8c3-128">Use the [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql) statement, as follows:</span></span>  
  
     <span data-ttu-id="6b8c3-129">ALTER AVAILABILITY GROUP *group_name* OFFLINE</span><span class="sxs-lookup"><span data-stu-id="6b8c3-129">ALTER AVAILABILITY GROUP *group_name* OFFLINE</span></span>  
  
     <span data-ttu-id="6b8c3-130">여기서 *group_name* 은 가용성 그룹의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="6b8c3-130">where *group_name* is the name of the availability group.</span></span>  
  
### <a name="example"></a><span data-ttu-id="6b8c3-131">예제</span><span class="sxs-lookup"><span data-stu-id="6b8c3-131">Example</span></span>  
 <span data-ttu-id="6b8c3-132">다음 예에서는 `AccountsAG` 가용성 그룹을 오프라인 상태로 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="6b8c3-132">The following example takes the `AccountsAG` availability group offline.</span></span>  
  
```sql
ALTER AVAILABILITY GROUP AccountsAG OFFLINE;  
```  
  
##  <a name="follow-up-after-the-availability-group-goes-offline"></a><a name="FollowUp"></a> <span data-ttu-id="6b8c3-133">후속 작업: 가용성 그룹을 오프라인 상태로 전환한 후</span><span class="sxs-lookup"><span data-stu-id="6b8c3-133">Follow Up: After the Availability Group Goes Offline</span></span>  
  
-   <span data-ttu-id="6b8c3-134">**OFFLINE 작업의 로깅:**  OFFLINE 작업이 시작된 WSFC 노드의 ID는 WSFC 클러스터 로그와 SQL ERRORLOG에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="6b8c3-134">**Logging of OFFLINE operation:**  The identity of the WSFC node where the OFFLINE operation was initiated is stored in both the WSFC cluster log and the SQL ERRORLOG.</span></span>  
  
-   <span data-ttu-id="6b8c3-135">**그룹을 오프라인으로 전환하기 전에 가용성 그룹 수신기를 삭제하지 않은 경우:**  가용성 그룹을 다른 WSFC 클러스터에 마이그레이션할 경우 수신기의 VNN과 VIP를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="6b8c3-135">**If you did not delete the availability group listener before taking the group offline:**  If you are migrating the availability group to another WSFC cluster, delete the VNN and VIP of the listener.</span></span> <span data-ttu-id="6b8c3-136">수신기의 VNN 및 VIP는 장애 조치(Failover) 클러스터 관리자 콘솔, [Remove-ClusterResource](https://technet.microsoft.com/library/ee461015\(WS.10\).aspx) PowerShell Cmdlet 또는 [cluster.exe](https://technet.microsoft.com/library/ee461015\(WS.10\).aspx)를 사용하여 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6b8c3-136">You can delete them by using either the Failover Cluster Management console, the [Remove-ClusterResource](https://technet.microsoft.com/library/ee461015\(WS.10\).aspx) PowerShell cmdlet, or [cluster.exe](https://technet.microsoft.com/library/ee461015\(WS.10\).aspx).</span></span> <span data-ttu-id="6b8c3-137">cluster.exe는 Windows 8에서 더 이상 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6b8c3-137">Note that cluster.exe is deprecated on Windows 8.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="6b8c3-138">관련 작업</span><span class="sxs-lookup"><span data-stu-id="6b8c3-138">Related Tasks</span></span>  
  
-   [<span data-ttu-id="6b8c3-139">가용성 그룹 수신기 제거&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="6b8c3-139">Remove an Availability Group Listener &#40;SQL Server&#41;</span></span>](availability-groups/windows/remove-an-availability-group-listener-sql-server.md)  
  
-   [<span data-ttu-id="6b8c3-140">서버 인스턴스의 HADR 클러스터 컨텍스트 변경&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="6b8c3-140">Change the HADR Cluster Context of Server Instance &#40;SQL Server&#41;</span></span>](availability-groups/windows/change-the-hadr-cluster-context-of-server-instance-sql-server.md)  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> <span data-ttu-id="6b8c3-141">관련 내용</span><span class="sxs-lookup"><span data-stu-id="6b8c3-141">Related Content</span></span>  
  
-   <span data-ttu-id="6b8c3-142">[SQL Server 2012 기술 문서](https://msdn.microsoft.com/library/bb418445\(SQL.10\).aspx)</span><span class="sxs-lookup"><span data-stu-id="6b8c3-142">[SQL Server 2012 Technical Articles](https://msdn.microsoft.com/library/bb418445\(SQL.10\).aspx)</span></span>  
  
-   [<span data-ttu-id="6b8c3-143">SQL Server AlwaysOn 팀 블로그: 공식 SQL Server AlwaysOn 팀 블로그</span><span class="sxs-lookup"><span data-stu-id="6b8c3-143">SQL Server AlwaysOn Team Blog: The official SQL Server AlwaysOn Team Blog</span></span>](https://blogs.msdn.com/b/sqlalwayson/)  
  
## <a name="see-also"></a><span data-ttu-id="6b8c3-144">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6b8c3-144">See Also</span></span>  
 [<span data-ttu-id="6b8c3-145">AlwaysOn 가용성 그룹 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="6b8c3-145">AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](availability-groups/windows/always-on-availability-groups-sql-server.md)  
