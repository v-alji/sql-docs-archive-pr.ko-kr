---
title: 일부 가용성 복제본에 상태 역할이 없음 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.agdashboard.agp6allroleshealthy.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: 7ec5b337-7201-4a66-a541-7560f8b18784
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 801fe20edf6f2dbe09bc800722cf4210988ebc69
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651279"
---
# <a name="some-availability-replicas-do-not-have-a-healthy-role"></a><span data-ttu-id="14fde-102">일부 가용성 복제본에 정상 상태의 역할이 없음</span><span class="sxs-lookup"><span data-stu-id="14fde-102">Some availability replicas do not have a healthy role</span></span>
    
## <a name="introduction"></a><span data-ttu-id="14fde-103">소개</span><span class="sxs-lookup"><span data-stu-id="14fde-103">Introduction</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="14fde-104">**정책 이름**</span><span class="sxs-lookup"><span data-stu-id="14fde-104">**Policy Name**</span></span>|<span data-ttu-id="14fde-105">가용성 복제본 역할 상태</span><span class="sxs-lookup"><span data-stu-id="14fde-105">Availability Replicas Role State</span></span>|  
|<span data-ttu-id="14fde-106">**문제점**</span><span class="sxs-lookup"><span data-stu-id="14fde-106">**Issue**</span></span>|<span data-ttu-id="14fde-107">일부 가용성 복제본에 정상 상태의 역할이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="14fde-107">Some availability replicas do not have a healthy role.</span></span>|  
|<span data-ttu-id="14fde-108">**범주**</span><span class="sxs-lookup"><span data-stu-id="14fde-108">**Category**</span></span>|<span data-ttu-id="14fde-109">**경고**</span><span class="sxs-lookup"><span data-stu-id="14fde-109">**Warning**</span></span>|  
|<span data-ttu-id="14fde-110">**패싯**</span><span class="sxs-lookup"><span data-stu-id="14fde-110">**Facet**</span></span>|<span data-ttu-id="14fde-111">가용성 그룹</span><span class="sxs-lookup"><span data-stu-id="14fde-111">Availability group</span></span>|  
  
## <a name="description"></a><span data-ttu-id="14fde-112">Description</span><span class="sxs-lookup"><span data-stu-id="14fde-112">Description</span></span>  
 <span data-ttu-id="14fde-113">이 정책은 모든 가용성 복제본의 연결 상태를 롤업하며 정상 상태의 역할에 없는 가용성 복제본이 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="14fde-113">This policy rolls up the connection state of all availability replicas and checks if there are any availability replicas that are not in a healthy role.</span></span> <span data-ttu-id="14fde-114">가용성 복제본이 주 복제본이나 보조 복제본이 아닌 경우 정책은 비정상 상태에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="14fde-114">The policy is in an unhealthy state when any availability replica is neither primary nor secondary.</span></span> <span data-ttu-id="14fde-115">그렇지 않으면 정책은 정상 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="14fde-115">The policy is otherwise in a healthy state.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="14fde-116">이 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]릴리스의 경우 가능한 원인 및 해결 방법은 TechNet Wiki의 [일부 가용성 복제본에 정상 상태의 역할이 없음](https://go.microsoft.com/fwlink/p/?LinkId=220854) 을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="14fde-116">For this release of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], information about possible causes and solutions is located at [Some availability replicas do not have a healthy role](https://go.microsoft.com/fwlink/p/?LinkId=220854) on the TechNet Wiki.</span></span>  
  
## <a name="possible-causes"></a><span data-ttu-id="14fde-117">가능한 원인</span><span class="sxs-lookup"><span data-stu-id="14fde-117">Possible Causes</span></span>  
 <span data-ttu-id="14fde-118">이 가용성 그룹의 하나 이상의 가용성 복제본에는 현재 주 역할이나 보조 역할이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="14fde-118">In this availability group, at least one availability replica does not currently have the primary or secondary role.</span></span>  
  
## <a name="possible-solution"></a><span data-ttu-id="14fde-119">가능한 해결 방법</span><span class="sxs-lookup"><span data-stu-id="14fde-119">Possible Solution</span></span>  
 <span data-ttu-id="14fde-120">가용성 복제본 정책 상태를 사용하여 역할이 주 역할이나 보조 역할이 아닌 가용성 복제본을 찾은 다음 가용성 복제본에서 문제를 해결합니다.</span><span class="sxs-lookup"><span data-stu-id="14fde-120">Use the availability replica policy state to find the availability replica whose role is not primary or secondary, and then resolve the issue at the availability replica.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14fde-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="14fde-121">See Also</span></span>  
 <span data-ttu-id="14fde-122">[AlwaysOn 가용성 그룹 &#40;SQL Server 개요&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="14fde-122">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="14fde-123">AlwaysOn 대시보드 사용&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="14fde-123">Use the AlwaysOn Dashboard &#40;SQL Server Management Studio&#41;</span></span>](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
