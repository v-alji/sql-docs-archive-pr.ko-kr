---
title: 가용성 복제본이 조인되어 있지 않음 | Microsoft Docs
ms.custom: ''
ms.date: 01/09/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.agdashboard.arp4joined.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: 9c0d10b1-9e12-430c-83b9-ca2bd0a3afc4
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 7c4f76e98d373e50124f5ca2b135a9fad8f34226
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87733152"
---
# <a name="availability-replica-is-not-joined"></a><span data-ttu-id="8719a-102">가용성 복제본이 조인되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8719a-102">Availability replica is not joined</span></span>
    
## <a name="introduction"></a><span data-ttu-id="8719a-103">소개</span><span class="sxs-lookup"><span data-stu-id="8719a-103">Introduction</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8719a-104">**정책 이름**</span><span class="sxs-lookup"><span data-stu-id="8719a-104">**Policy Name**</span></span>|<span data-ttu-id="8719a-105">가용성 복제본 조인 상태</span><span class="sxs-lookup"><span data-stu-id="8719a-105">Availability Replica Join State</span></span>|  
|<span data-ttu-id="8719a-106">**문제점**</span><span class="sxs-lookup"><span data-stu-id="8719a-106">**Issue**</span></span>|<span data-ttu-id="8719a-107">가용성 복제본이 조인되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8719a-107">Availability Replica is not joined.</span></span>|  
|<span data-ttu-id="8719a-108">**범주**</span><span class="sxs-lookup"><span data-stu-id="8719a-108">**Category**</span></span>|<span data-ttu-id="8719a-109">**경고**</span><span class="sxs-lookup"><span data-stu-id="8719a-109">**Warning**</span></span>|  
|<span data-ttu-id="8719a-110">**패싯**</span><span class="sxs-lookup"><span data-stu-id="8719a-110">**Facet**</span></span>|<span data-ttu-id="8719a-111">가용성 복제본</span><span class="sxs-lookup"><span data-stu-id="8719a-111">Availability replica</span></span>|  
  
## <a name="description"></a><span data-ttu-id="8719a-112">설명</span><span class="sxs-lookup"><span data-stu-id="8719a-112">Description</span></span>  
 <span data-ttu-id="8719a-113">이 정책은 가용성 복제본의 조인 상태를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="8719a-113">This policy checks the join state of the availability replica.</span></span> <span data-ttu-id="8719a-114">가용성 복제본이 가용성 그룹에 추가되었지만 제대로 조인되지 않은 경우 정책은 비정상 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="8719a-114">The policy is in an unhealthy state when the availability replica is added to the availability group, but is not joined properly.</span></span> <span data-ttu-id="8719a-115">그렇지 않으면 정책은 정상 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="8719a-115">The policy is otherwise in a healthy state.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8719a-116">이 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]릴리스에서의 가능한 원인 및 해결 방법은 TechNet Wiki의 [가용성 복제본이 조인되어 있지 않음](https://go.microsoft.com/fwlink/p/?LinkId=220859) 을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8719a-116">For this release of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], information about possible causes and solutions is located at [Availability replica is not joined](https://go.microsoft.com/fwlink/p/?LinkId=220859) on the TechNet Wiki.</span></span>  
  
## <a name="possible-causes"></a><span data-ttu-id="8719a-117">가능한 원인</span><span class="sxs-lookup"><span data-stu-id="8719a-117">Possible Causes</span></span>  
 <span data-ttu-id="8719a-118">보조 복제본이 가용성 그룹에 조인되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8719a-118">The secondary replica is not joined to the availability group.</span></span> <span data-ttu-id="8719a-119">가용성 복제본을 가용성 그룹에 성공적으로 조인하려면 조인 상태가 조인된 독립 실행형 인스턴스(1) 또는 조인된 장애 조치(Failover) 클러스터(2)여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8719a-119">For an availability replica to be successfully joined to the availability group, the join state must be Joined Standalone Instance (1) or Joined Failover Cluster (2).</span></span>  
  
## <a name="possible-solution"></a><span data-ttu-id="8719a-120">가능한 해결 방법</span><span class="sxs-lookup"><span data-stu-id="8719a-120">Possible Solution</span></span>  
 <span data-ttu-id="8719a-121">Transact-SQL, PowerShell 또는 SQL Server Management Studio를 사용하여 보조 복제본을 가용성 그룹에 조인합니다.</span><span class="sxs-lookup"><span data-stu-id="8719a-121">Use Transact-SQL, PowerShell, or SQL Server Management Studio to join the secondary replica to the availability group.</span></span> <span data-ttu-id="8719a-122">보조 복제본을 가용성 그룹에 조인하는 방법은 [가용성 그룹에 보조 복제본 조인(SQL Server)](https://msdn.microsoft.com/library/ff878473\(en-us,SQL.110\).aspx)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8719a-122">For more information about joining secondary replicas to availability groups, see [Joining a Secondary Replica to an Availability Group (SQL Server)](https://msdn.microsoft.com/library/ff878473\(en-us,SQL.110\).aspx).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8719a-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8719a-123">See Also</span></span>  
 <span data-ttu-id="8719a-124">[AlwaysOn 가용성 그룹 &#40;SQL Server 개요&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="8719a-124">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="8719a-125">AlwaysOn 대시보드 사용&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="8719a-125">Use the AlwaysOn Dashboard &#40;SQL Server Management Studio&#41;</span></span>](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
