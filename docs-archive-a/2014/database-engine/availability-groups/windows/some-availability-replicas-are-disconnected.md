---
title: 일부 가용성 복제본의 연결이 해제됨 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.agdashboard.agp7allconnected.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: aea808be-6f0f-40c2-9aa2-a2a435ec6443
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 1bb6535b513770b9b4718a0e8372c0a5bc3cba84
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651283"
---
# <a name="some-availability-replicas-are-disconnected"></a><span data-ttu-id="09fd3-102">일부 가용성 복제본의 연결이 해제됨</span><span class="sxs-lookup"><span data-stu-id="09fd3-102">Some availability replicas are disconnected</span></span>
    
## <a name="introduction"></a><span data-ttu-id="09fd3-103">소개</span><span class="sxs-lookup"><span data-stu-id="09fd3-103">Introduction</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="09fd3-104">**정책 이름**</span><span class="sxs-lookup"><span data-stu-id="09fd3-104">**Policy Name**</span></span>|<span data-ttu-id="09fd3-105">가용성 복제본 연결 상태</span><span class="sxs-lookup"><span data-stu-id="09fd3-105">Availability Replicas Connection State</span></span>|  
|<span data-ttu-id="09fd3-106">**문제점**</span><span class="sxs-lookup"><span data-stu-id="09fd3-106">**Issue**</span></span>|<span data-ttu-id="09fd3-107">일부 가용성 복제본의 연결이 해제됩니다.</span><span class="sxs-lookup"><span data-stu-id="09fd3-107">Some availability replicas are disconnected.</span></span>|  
|<span data-ttu-id="09fd3-108">**범주**</span><span class="sxs-lookup"><span data-stu-id="09fd3-108">**Category**</span></span>|<span data-ttu-id="09fd3-109">**경고**</span><span class="sxs-lookup"><span data-stu-id="09fd3-109">**Warning**</span></span>|  
|<span data-ttu-id="09fd3-110">**패싯**</span><span class="sxs-lookup"><span data-stu-id="09fd3-110">**Facet**</span></span>|<span data-ttu-id="09fd3-111">가용성 그룹</span><span class="sxs-lookup"><span data-stu-id="09fd3-111">Availability group</span></span>|  
  
## <a name="description"></a><span data-ttu-id="09fd3-112">Description</span><span class="sxs-lookup"><span data-stu-id="09fd3-112">Description</span></span>  
 <span data-ttu-id="09fd3-113">이 정책은 모든 가용성 복제본의 연결 상태를 롤업하며 연결이 해제된 가용성 복제본이 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="09fd3-113">This policy rolls up the connection state of all availability replicas and checks for any availability replicas that are DISCONENCTED.</span></span> <span data-ttu-id="09fd3-114">가용성 복제본의 연결이 해제된 경우 정책은 비정상 상태에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="09fd3-114">The policy is in an unhealthy state when any availability replica is DISCONNECTED.</span></span> <span data-ttu-id="09fd3-115">그렇지 않으면 정책은 정상 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="09fd3-115">The policy is otherwise in a healthy state.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="09fd3-116"> 이 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]릴리스의 경우 가능한 원인 및 해결 방법에 대한 자세한 내용은 TechNet Wiki의 [일부 가용성 복제본의 연결이 해제됨](https://go.microsoft.com/fwlink/p/?LinkId=220855) 을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="09fd3-116">For this release of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], information about possible causes and solutions is located at [Some availability replicas are disconnected](https://go.microsoft.com/fwlink/p/?LinkId=220855) on the TechNet Wiki.</span></span>  
  
## <a name="possible-causes"></a><span data-ttu-id="09fd3-117">가능한 원인</span><span class="sxs-lookup"><span data-stu-id="09fd3-117">Possible Causes</span></span>  
 <span data-ttu-id="09fd3-118">이 가용성 그룹의 하나 이상의 보조 복제본이 주 복제본에 연결되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="09fd3-118">In this availability group, at least one secondary replica is not connected to the primary replica.</span></span> <span data-ttu-id="09fd3-119">연결 상태가 DISCONNECTED입니다.</span><span class="sxs-lookup"><span data-stu-id="09fd3-119">The connected state is DISCONNECTED.</span></span>  
  
## <a name="possible-solution"></a><span data-ttu-id="09fd3-120">가능한 해결 방법</span><span class="sxs-lookup"><span data-stu-id="09fd3-120">Possible Solution</span></span>  
 <span data-ttu-id="09fd3-121">가용성 복제본 정책 상태를 사용하여 DISCONNECTED 상태인 가용성 복제본을 찾은 다음 가용성 복제본에서 문제를 해결합니다.</span><span class="sxs-lookup"><span data-stu-id="09fd3-121">Use the availability replica policy state to find the availability replica that is DISCONNECTED, and then resolve the issue at the availability replica.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09fd3-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="09fd3-122">See Also</span></span>  
 <span data-ttu-id="09fd3-123">[AlwaysOn 가용성 그룹 &#40;SQL Server 개요&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="09fd3-123">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="09fd3-124">AlwaysOn 대시보드 사용&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="09fd3-124">Use the AlwaysOn Dashboard &#40;SQL Server Management Studio&#41;</span></span>](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
