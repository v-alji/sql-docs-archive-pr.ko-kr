---
title: 가용성 그룹이 오프라인 상태임 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.agdashboard.agp2online.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: 093c5208-bf7a-49f4-a546-72b48197cadf
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b25e5b22a09783c8dfcad862500b5c0dfcb2c319
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646667"
---
# <a name="availability-group-is-offline"></a><span data-ttu-id="b62be-102">가용성 그룹이 오프라인 상태임</span><span class="sxs-lookup"><span data-stu-id="b62be-102">Availability group is offline</span></span>
    
## <a name="introduction"></a><span data-ttu-id="b62be-103">소개</span><span class="sxs-lookup"><span data-stu-id="b62be-103">Introduction</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b62be-104">**정책 이름**</span><span class="sxs-lookup"><span data-stu-id="b62be-104">**Policy Name**</span></span>|<span data-ttu-id="b62be-105">가용성 그룹 온라인 상태</span><span class="sxs-lookup"><span data-stu-id="b62be-105">Availability Group Online State</span></span>|  
|<span data-ttu-id="b62be-106">**문제점**</span><span class="sxs-lookup"><span data-stu-id="b62be-106">**Issue**</span></span>|<span data-ttu-id="b62be-107">가용성 그룹이 오프라인 상태임</span><span class="sxs-lookup"><span data-stu-id="b62be-107">Availability group is offline.</span></span>|  
|<span data-ttu-id="b62be-108">**범주**</span><span class="sxs-lookup"><span data-stu-id="b62be-108">**Category**</span></span>|<span data-ttu-id="b62be-109">**심각**</span><span class="sxs-lookup"><span data-stu-id="b62be-109">**Critical**</span></span>|  
|<span data-ttu-id="b62be-110">**패싯**</span><span class="sxs-lookup"><span data-stu-id="b62be-110">**Facet**</span></span>|<span data-ttu-id="b62be-111">가용성 그룹</span><span class="sxs-lookup"><span data-stu-id="b62be-111">Availability group</span></span>|  
  
## <a name="description"></a><span data-ttu-id="b62be-112">Description</span><span class="sxs-lookup"><span data-stu-id="b62be-112">Description</span></span>  
 <span data-ttu-id="b62be-113">이 정책은 가용성 그룹의 온라인 또는 오프라인 상태를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="b62be-113">This policy checks the online or offline state of the availability group.</span></span> <span data-ttu-id="b62be-114">가용성 그룹의 클러스터 리소스가 오프라인이거나 가용성 그룹에 주 복제본이 없으면 정책이 비정상 상태이며 경고가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="b62be-114">The policy is in an unhealthy state and an alert is raised when the cluster resource of the availability group is offline or the availability group does not have a primary replica.</span></span>  
  
 <span data-ttu-id="b62be-115">가용성 그룹의 클러스터 리소스가 온라인이고 가용성 그룹에 주 복제본이 있으면 정책 상태가 정상입니다.</span><span class="sxs-lookup"><span data-stu-id="b62be-115">The policy state is healthy when the cluster resource of the availability group is online and the availability group has a primary replica.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b62be-116"> 이 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]릴리스의 경우 가능한 원인 및 해결 방법에 대한 자세한 내용은 TechNet Wiki의 [가용성 그룹이 오프라인 상태임](https://go.microsoft.com/fwlink/p/?LinkId=220850) 을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="b62be-116">For this release of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], information about possible causes and solutions is located at [Availability group is offline](https://go.microsoft.com/fwlink/p/?LinkId=220850) on the TechNet Wiki.</span></span>  
  
## <a name="possible-causes"></a><span data-ttu-id="b62be-117">가능한 원인</span><span class="sxs-lookup"><span data-stu-id="b62be-117">Possible Causes</span></span>  
 <span data-ttu-id="b62be-118">이 문제는 주 복제본을 호스팅하는 서버 인스턴스에 장애가 있거나 WSFC(Windows Server 장애 조치(Failover) 클러스터) 가용성 그룹 리소스가 오프라인 상태가 되어 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b62be-118">This issue can be caused by a failure in the server instance that hosts the primary replica or by the Windows Server Failover Cluster (WSFC) availability group resource going offline.</span></span> <span data-ttu-id="b62be-119">다음과 같은 경우 가용성 그룹이 오프라인 상태가 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b62be-119">Following are possible causes for the availability group to be offline:</span></span>  
  
-   <span data-ttu-id="b62be-120">가용성 그룹이 자동 장애 조치(Failover) 모드로 구성되지 않은 경우.</span><span class="sxs-lookup"><span data-stu-id="b62be-120">The availability group is not configured with automatic failover mode.</span></span> <span data-ttu-id="b62be-121">주 복제본을 사용할 수 없게 되고 가용성 그룹에 있는 모든 복제본의 역할이 RESOLVING이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b62be-121">The primary replica becomes unavailable and the role of all replicas in the availability group become RESOLVING.</span></span>  
  
    -   <span data-ttu-id="b62be-122">주 복제본 인스턴스 서비스가 다운되거나 응답하지 않는 경우</span><span class="sxs-lookup"><span data-stu-id="b62be-122">The primary replica instance service is down or unresponsive.</span></span>  
  
    -   <span data-ttu-id="b62be-123">가용성 그룹에 클러스터와의 연결 문제가 있는 경우</span><span class="sxs-lookup"><span data-stu-id="b62be-123">The availability group has a connectivity issue with the cluster.</span></span>  
  
-   <span data-ttu-id="b62be-124">가용성 그룹이 자동 장애 조치(Failover) 모드로 구성되었지만 성공적으로 완료되지 않은 경우</span><span class="sxs-lookup"><span data-stu-id="b62be-124">The availability group is configured with automatic failover mode and does not complete successfully.</span></span>  
  
    -   <span data-ttu-id="b62be-125">자동 장애 조치(Failover) 중 대상 복제본에서 주 복제본 준비 상태 검사가 실패하고 새 주 복제본이 될 수 있는 복제본이 없는 경우</span><span class="sxs-lookup"><span data-stu-id="b62be-125">During the automatic failover, the primary readiness check on the target replica fails, and there is no replica available to become the new primary.</span></span>  
  
-   <span data-ttu-id="b62be-126">클러스터의 가용성 그룹 리소스가 오프라인 상태가 되는 경우</span><span class="sxs-lookup"><span data-stu-id="b62be-126">The availability group resource in the cluster becomes offline.</span></span>  
  
    -   <span data-ttu-id="b62be-127">종속 클러스터 리소스에 심각한 문제가 발생하여 오프라인이 되는 경우.</span><span class="sxs-lookup"><span data-stu-id="b62be-127">Any dependent cluster resource encounters a critical issue and becomes offline.</span></span> <span data-ttu-id="b62be-128">종속 리소스가 온라인 상태가 될 때까지 가용성 그룹 리소스도 오프라인 상태가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b62be-128">The availability group resource is also offline until the dependent resource becomes online.</span></span>  
  
    -   <span data-ttu-id="b62be-129">클러스터의 심각한 문제로 인해 가용성 그룹 리소스가 해제된 경우</span><span class="sxs-lookup"><span data-stu-id="b62be-129">A critical issue in the cluster turns off the availability group resource.</span></span>  
  
-   <span data-ttu-id="b62be-130">가용성 그룹에 대해 자동, 수동 또는 강제 장애 조치(Failover)가 진행 중인 경우</span><span class="sxs-lookup"><span data-stu-id="b62be-130">There is an automatic, manual, or forced failover in progress for the availability group.</span></span>  
  
## <a name="possible-solutions"></a><span data-ttu-id="b62be-131">가능한 해결 방법</span><span class="sxs-lookup"><span data-stu-id="b62be-131">Possible Solutions</span></span>  
 <span data-ttu-id="b62be-132">이 문제에 대한 해결 방법은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="b62be-132">Following are possible solutions for this issue:</span></span>  
  
-   <span data-ttu-id="b62be-133">주 복제본의 SQL Server 인스턴스가 다운된 경우 서버를 다시 시작한 다음 가용성 그룹이 정상 상태로 복구되는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="b62be-133">If the SQL Server instance of the primary replica is down, restart the server and then verify that the availability group recovers to a healthy state.</span></span>  
  
-   <span data-ttu-id="b62be-134">자동 장애 조치(Failover)가 실패한 것으로 보이면 복제본의 데이터베이스가 이전에 알려진 주 복제본과 동기화되었는지 확인한 다음 주 복제본으로 장애 조치(Failover)를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="b62be-134">If the automatic failover appears to have failed, verify that the databases on the replica are synchronized with the previously known primary replica, and then failover to the primary replica.</span></span> <span data-ttu-id="b62be-135">데이터베이스가 동기화되지 않은 경우 데이터 손실이 가장 적은 복제본을 선택한 다음 장애 조치(Failover) 모드로 복구합니다.</span><span class="sxs-lookup"><span data-stu-id="b62be-135">If the databases are not synchronized, select a replica with a minimum loss of data, and then recover to failover mode.</span></span>  
  
-   <span data-ttu-id="b62be-136">SQL Server 인스턴스가 정상으로 보이지만 클러스터의 리소스가 오프라인 상태인 경우 장애 조치(Failover) 클러스터 관리자를 사용하여 클러스터 상태 또는 서버의 다른 클러스터 문제를 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="b62be-136">If the resource in the cluster is offline while the instances of SQL Server appear to be healthy, use Failover Cluster Manager to check the cluster health or other cluster issues on the server.</span></span> <span data-ttu-id="b62be-137">장애 조치(Failover) 클러스터 관리자를 사용하여 가용성 그룹 리소스의 온라인 전환을 시도해 볼 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b62be-137">You can also use the Failover Cluster Manager to attempt to turn the availability group resource online.</span></span>  
  
-   <span data-ttu-id="b62be-138">장애 조치(Failover)가 진행 중인 경우 해당 장애 조치가 완료될 때까지 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="b62be-138">If there is a failover in progress, wait for the failover to complete.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b62be-139">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b62be-139">See Also</span></span>  
 <span data-ttu-id="b62be-140">[AlwaysOn 가용성 그룹 &#40;SQL Server 개요&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="b62be-140">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="b62be-141">AlwaysOn 대시보드 사용&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="b62be-141">Use the AlwaysOn Dashboard &#40;SQL Server Management Studio&#41;</span></span>](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
