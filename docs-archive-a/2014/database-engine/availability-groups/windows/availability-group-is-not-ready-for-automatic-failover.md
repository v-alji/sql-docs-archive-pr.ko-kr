---
title: 가용성 그룹에 대해 자동 장애 조치가 준비되지 않음 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.agdashboard.agp3autofailover.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: 28261014-342c-442a-bd89-6d04b8d4e8b7
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 2995ddec51cd70d8a3f209229d0ecb9b0132c79e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646670"
---
# <a name="availability-group-is-not-ready-for-automatic-failover"></a><span data-ttu-id="49cc1-102">가용성 그룹에 대해 자동 장애 조치(Failover)가 준비되지 않음</span><span class="sxs-lookup"><span data-stu-id="49cc1-102">Availability group is not ready for automatic failover</span></span>
    
## <a name="introduction"></a><span data-ttu-id="49cc1-103">소개</span><span class="sxs-lookup"><span data-stu-id="49cc1-103">Introduction</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="49cc1-104">**정책 이름**</span><span class="sxs-lookup"><span data-stu-id="49cc1-104">**Policy Name**</span></span>|<span data-ttu-id="49cc1-105">가용성 그룹 자동 장애 조치(Failover) 준비</span><span class="sxs-lookup"><span data-stu-id="49cc1-105">Availability Group Automatic Failover Readiness</span></span>|  
|<span data-ttu-id="49cc1-106">**문제점**</span><span class="sxs-lookup"><span data-stu-id="49cc1-106">**Issue**</span></span>|<span data-ttu-id="49cc1-107">가용성 그룹에 대해 자동 장애 조치(Failover)가 준비되지 않음</span><span class="sxs-lookup"><span data-stu-id="49cc1-107">Availability group is not ready for automatic failover.</span></span>|  
|<span data-ttu-id="49cc1-108">**범주**</span><span class="sxs-lookup"><span data-stu-id="49cc1-108">**Category**</span></span>|<span data-ttu-id="49cc1-109">**심각**</span><span class="sxs-lookup"><span data-stu-id="49cc1-109">**Critical**</span></span>|  
|<span data-ttu-id="49cc1-110">**패싯**</span><span class="sxs-lookup"><span data-stu-id="49cc1-110">**Facet**</span></span>|<span data-ttu-id="49cc1-111">가용성 그룹</span><span class="sxs-lookup"><span data-stu-id="49cc1-111">Availability group</span></span>|  
  
## <a name="description"></a><span data-ttu-id="49cc1-112">Description</span><span class="sxs-lookup"><span data-stu-id="49cc1-112">Description</span></span>  
 <span data-ttu-id="49cc1-113">이 정책은 가용성 그룹에 장애 조치(failover)가 준비된 보조 복제본이 하나 이상 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="49cc1-113">This policy checks to verify that the availability group has at least one secondary replica that is failover ready.</span></span> <span data-ttu-id="49cc1-114">주 복제본의 장애 조치(Failover) 모드가 자동이지만 가용성 그룹에 장애 조치(Failover)가 준비된 보조 복제본이 하나도 없는 경우 이 정책은 비정상 상태이며 경고가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="49cc1-114">The policy is in an unhealthy state and an alert is raised when the failover mode of the primary replica is automatic, however none of the secondary replicas in the availability group are failover ready.</span></span>  
  
 <span data-ttu-id="49cc1-115">적어도 하나의 보조 복제본이 자동 장애 조치(Failover)가 준비된 상태이면 정책은 정상 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="49cc1-115">The policy is in a healthy state when at least one secondary replica is automatic failover ready.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="49cc1-116"> 이 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]릴리스의 경우 가능한 원인 및 해결 방법에 대한 자세한 내용은 TechNet Wiki의 [가용성 그룹에 대해 자동 장애 조치(Failover)가 준비되지 않음](https://go.microsoft.com/fwlink/p/?LinkId=220851) 을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="49cc1-116">For this release of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], information about possible causes and solutions is located at [Availability group is not ready for automatic failover](https://go.microsoft.com/fwlink/p/?LinkId=220851) on the TechNet Wiki.</span></span>  
  
## <a name="possible-causes"></a><span data-ttu-id="49cc1-117">가능한 원인</span><span class="sxs-lookup"><span data-stu-id="49cc1-117">Possible Causes</span></span>  
 <span data-ttu-id="49cc1-118">가용성 그룹에 대해 자동 장애 조치(Failover)가 준비되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="49cc1-118">The availability group is not ready for automatic failover.</span></span> <span data-ttu-id="49cc1-119">주 복제본은 자동 장애 조치(Failover)를 사용하도록 구성되어 있지만 보조 복제본은 자동 장애 조치(Failover)를 사용하도록 구성되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="49cc1-119">The primary replica is configured for automatic failover; however, the secondary replica is not ready for automatic failover.</span></span> <span data-ttu-id="49cc1-120">자동 장애 조치(Failover)를 사용하도록 구성된 보조 복제본을 사용할 수 없거나 해당 데이터 동기화 상태가 현재 SYNCHRONIZED가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="49cc1-120">The secondary replica that is configured for automatic failover might be unavailable or its data synchronization state is currently not SYNCHRONIZED.</span></span>  
  
## <a name="possible-solutions"></a><span data-ttu-id="49cc1-121">가능한 해결 방법</span><span class="sxs-lookup"><span data-stu-id="49cc1-121">Possible Solutions</span></span>  
 <span data-ttu-id="49cc1-122">이 문제에 대한 해결 방법은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="49cc1-122">Following are possible solutions for this issue:</span></span>  
  
-   <span data-ttu-id="49cc1-123">적어도 하나의 보조 복제본이 자동 장애 조치(Failover)를 사용하도록 구성되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="49cc1-123">Verify that at least one secondary replica is configured as automatic failover.</span></span> <span data-ttu-id="49cc1-124">자동 장애 조치(Failover)를 사용하도록 구성되어 있는 보조 복제본이 없으면 동기 커밋을 사용하여 자동 장애 조치(Failover) 대상이 되도록 보조 복제본의 구성을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="49cc1-124">If there is not a secondary replica configured as automatic failover, update the configuration of a secondary replica to be the automatic failover target with synchronous commit.</span></span>  
  
-   <span data-ttu-id="49cc1-125">정책을 사용하여 데이터가 동기화 상태에 있는지, 그리고 자동 장애 조치(failover) 대상이 SYNCHRONIZED인지 확인한 다음 가용성 복제본에서 문제를 해결합니다.</span><span class="sxs-lookup"><span data-stu-id="49cc1-125">Use the policy to verify that the data is in a synchronization state and the automatic failover target is SYNCHRONIZED, and then resolve the issue at the availability replica.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49cc1-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="49cc1-126">See Also</span></span>  
 <span data-ttu-id="49cc1-127">[AlwaysOn 가용성 그룹 &#40;SQL Server 개요&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="49cc1-127">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="49cc1-128">AlwaysOn 대시보드 사용&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="49cc1-128">Use the AlwaysOn Dashboard &#40;SQL Server Management Studio&#41;</span></span>](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
