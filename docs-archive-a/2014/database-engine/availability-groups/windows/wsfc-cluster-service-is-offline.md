---
title: WSFC 클러스터 서비스가 오프라인 상태임 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.agdashboard.agp1WSFCquorum.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: d502548d-ece6-4a42-9ded-2157d33e3d21
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e6e7b48f96eb09638291b1d0655d385d606b1666
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87733144"
---
# <a name="wsfc-cluster-service-is-offline"></a><span data-ttu-id="db684-102">WSFC 클러스터 서비스가 오프라인 상태임</span><span class="sxs-lookup"><span data-stu-id="db684-102">WSFC cluster service is offline</span></span>
    
## <a name="introduction"></a><span data-ttu-id="db684-103">소개</span><span class="sxs-lookup"><span data-stu-id="db684-103">Introduction</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="db684-104">**정책 이름**</span><span class="sxs-lookup"><span data-stu-id="db684-104">**Policy Name**</span></span>|<span data-ttu-id="db684-105">WSFC 클러스터 상태</span><span class="sxs-lookup"><span data-stu-id="db684-105">WSFC Cluster State</span></span>|  
|<span data-ttu-id="db684-106">**문제점**</span><span class="sxs-lookup"><span data-stu-id="db684-106">**Issue**</span></span>|<span data-ttu-id="db684-107">WSFC 클러스터 서비스가 오프라인 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="db684-107">WSFC cluster service is offline.</span></span>|  
|<span data-ttu-id="db684-108">**범주**</span><span class="sxs-lookup"><span data-stu-id="db684-108">**Category**</span></span>|<span data-ttu-id="db684-109">**심각**</span><span class="sxs-lookup"><span data-stu-id="db684-109">**Critical**</span></span>|  
|<span data-ttu-id="db684-110">**패싯**</span><span class="sxs-lookup"><span data-stu-id="db684-110">**Facet**</span></span>|<span data-ttu-id="db684-111">SQL Server 인스턴스</span><span class="sxs-lookup"><span data-stu-id="db684-111">Instance of SQL Server</span></span>|  
  
## <a name="description"></a><span data-ttu-id="db684-112">Description</span><span class="sxs-lookup"><span data-stu-id="db684-112">Description</span></span>  
 <span data-ttu-id="db684-113">이 정책은 WSFC(Windows Server Failover Cluster)의 상태를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="db684-113">This policy checks the state of the Windows Server Failover Cluster (WSFC).</span></span> <span data-ttu-id="db684-114">WSFC 클러스터가 오프라인 상태이거나 강제 쿼럼 상태에 있는 경우 정책은 비정상 상태에 있으며 경고가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="db684-114">The policy is in an unhealthy state and an alert is raised when the WSFC cluster is offline or in the forced quorum state.</span></span> <span data-ttu-id="db684-115">이 클러스터 내에서 호스팅되는 모든 가용성 그룹이 오프라인이거나 재해 복구 동작이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="db684-115">All availability groups hosted within this cluster are offline or a disaster recovery action is required.</span></span>  
  
 <span data-ttu-id="db684-116">정책 상태는 클러스터 상태가 정상 쿼럼 상태에 있을 때 정상입니다.</span><span class="sxs-lookup"><span data-stu-id="db684-116">The policy state is healthy when the cluster state is in the normal quorum.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="db684-117">이 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]릴리스의 경우 가능한 원인 및 해결 방법은 TechNet Wiki의 [WSFC 클러스터 서비스가 오프라인 상태임](https://go.microsoft.com/fwlink/p/?LinkId=220849) 을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="db684-117">For this release of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], information about possible causes and solutions is located at [WSFC cluster service is offline](https://go.microsoft.com/fwlink/p/?LinkId=220849) on the TechNet Wiki.</span></span>  
  
## <a name="possible-causes"></a><span data-ttu-id="db684-118">가능한 원인</span><span class="sxs-lookup"><span data-stu-id="db684-118">Possible Causes</span></span>  
 <span data-ttu-id="db684-119">이 문제는 클러스터 서비스 문제 또는 클러스터의 쿼럼 손실로 인해 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db684-119">This issue can be caused by a cluster service issue or by the loss of the quorum in the cluster.</span></span>  
  
## <a name="possible-solution"></a><span data-ttu-id="db684-120">가능한 해결 방법</span><span class="sxs-lookup"><span data-stu-id="db684-120">Possible Solution</span></span>  
 <span data-ttu-id="db684-121">클러스터 관리자 도구를 사용하여 강제 쿼럼 또는 재해 복구 워크플로를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="db684-121">Use the Cluster Administrator tool to perform the forced quorum or disaster recovery workflow.</span></span> <span data-ttu-id="db684-122">강제 쿼럼 또는 재해 복구 워크플로를 수행하여 문제를 해결할 수 없는 경우 클러스터 관리자에게 이 문제의 해결 방법을 문의하십시오.</span><span class="sxs-lookup"><span data-stu-id="db684-122">If you cannot resolve the issue by performing the forced quorum or disaster recovery, contact your cluster administrator to help resolve this issue.</span></span> <span data-ttu-id="db684-123">자세한 내용은 [온라인 설명서의](../../../sql-server/failover-clusters/windows/force-a-wsfc-cluster-to-start-without-a-quorum.md) 쿼럼 없이 WSFC 클러스터 강제 시작 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="db684-123">For more information, see [Force a WSFC Cluster to Start Without a Quorum](../../../sql-server/failover-clusters/windows/force-a-wsfc-cluster-to-start-without-a-quorum.md) in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db684-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="db684-124">See Also</span></span>  
 <span data-ttu-id="db684-125">[AlwaysOn 가용성 그룹 &#40;SQL Server 개요&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="db684-125">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="db684-126">AlwaysOn 대시보드 사용&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="db684-126">Use the AlwaysOn Dashboard &#40;SQL Server Management Studio&#41;</span></span>](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
