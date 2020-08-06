---
title: 가용성 복제본 연결 해제됨 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.agdashboard.arp2connected.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: 1a2162d3-54fb-4356-b349-effbdc15a5a4
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 1db92b8e73b6daaee7edf5042b1d73cfeb471d1d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87733155"
---
# <a name="availability-replica-is-disconnected"></a><span data-ttu-id="8b191-102">가용성 복제본 연결 해제됨</span><span class="sxs-lookup"><span data-stu-id="8b191-102">Availability replica is disconnected</span></span>
    
## <a name="introduction"></a><span data-ttu-id="8b191-103">소개</span><span class="sxs-lookup"><span data-stu-id="8b191-103">Introduction</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8b191-104">**정책 이름**</span><span class="sxs-lookup"><span data-stu-id="8b191-104">**Policy Name**</span></span>|<span data-ttu-id="8b191-105">가용성 복제본 연결 상태</span><span class="sxs-lookup"><span data-stu-id="8b191-105">Availability Replica Connection State</span></span>|  
|<span data-ttu-id="8b191-106">**문제점**</span><span class="sxs-lookup"><span data-stu-id="8b191-106">**Issue**</span></span>|<span data-ttu-id="8b191-107">가용성 복제본의 연결이 끊어짐</span><span class="sxs-lookup"><span data-stu-id="8b191-107">Availability replica is disconnected.</span></span>|  
|<span data-ttu-id="8b191-108">**범주**</span><span class="sxs-lookup"><span data-stu-id="8b191-108">**Category**</span></span>|<span data-ttu-id="8b191-109">**심각**</span><span class="sxs-lookup"><span data-stu-id="8b191-109">**Critical**</span></span>|  
|<span data-ttu-id="8b191-110">**패싯**</span><span class="sxs-lookup"><span data-stu-id="8b191-110">**Facet**</span></span>|<span data-ttu-id="8b191-111">가용성 복제본</span><span class="sxs-lookup"><span data-stu-id="8b191-111">Availability replica</span></span>|  
  
## <a name="description"></a><span data-ttu-id="8b191-112">설명</span><span class="sxs-lookup"><span data-stu-id="8b191-112">Description</span></span>  
 <span data-ttu-id="8b191-113">이 정책은 가용성 복제본 간의 연결 상태를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="8b191-113">This policy checks the connection state between availability replicas.</span></span> <span data-ttu-id="8b191-114">가용성 복제본의 연결 상태가 DISCONNECTED인 경우 정책은 비정상 상태에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8b191-114">The policy is in an unhealthy state when the connection state of the availability replica is DISCONNECTED.</span></span> <span data-ttu-id="8b191-115">그렇지 않으면 정책은 정상 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="8b191-115">The policy is otherwise in a healthy state.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8b191-116"> 이 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]릴리스의 경우 가능한 원인 및 해결 방법에 대한 자세한 내용은 TechNet Wiki의 [가용성 복제본의 연결이 끊어짐](https://go.microsoft.com/fwlink/p/?LinkId=220857) 을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="8b191-116">For this release of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], information about possible causes and solutions is located at [Availability replica is disconnected](https://go.microsoft.com/fwlink/p/?LinkId=220857) on the TechNet Wiki.</span></span>  
  
## <a name="possible-causes"></a><span data-ttu-id="8b191-117">가능한 원인</span><span class="sxs-lookup"><span data-stu-id="8b191-117">Possible Causes</span></span>  
 <span data-ttu-id="8b191-118">보조 복제본이 주 복제본에 연결되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8b191-118">The secondary replica is not connected to the primary replica.</span></span> <span data-ttu-id="8b191-119">연결 상태가 DISCONNECTED입니다.</span><span class="sxs-lookup"><span data-stu-id="8b191-119">The connected state is DISCONNECTED.</span></span> <span data-ttu-id="8b191-120">이 문제는 다음에 의해 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8b191-120">This issue can be caused by the following:</span></span>  
  
-   <span data-ttu-id="8b191-121">연결 포트가 다른 애플리케이션과 충돌했을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8b191-121">The connection port might be in conflict with another application.</span></span>  
  
-   <span data-ttu-id="8b191-122">암호화 유형 또는 알고리즘이 일치하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8b191-122">The encryption type or algorithm is mismatched.</span></span>  
  
-   <span data-ttu-id="8b191-123">연결 엔드포인트가 삭제되었거나 시작되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="8b191-123">The connection endpoint has been deleted or has not been started.</span></span>  
  
-   <span data-ttu-id="8b191-124">전송 연결이 끊어졌습니다.</span><span class="sxs-lookup"><span data-stu-id="8b191-124">The transport is disconnected.</span></span>  
  
## <a name="possible-solutions"></a><span data-ttu-id="8b191-125">가능한 해결 방법</span><span class="sxs-lookup"><span data-stu-id="8b191-125">Possible Solutions</span></span>  
 <span data-ttu-id="8b191-126">이 문제에 대한 해결 방법은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="8b191-126">Following are possible solutions for this issue:</span></span>  
  
-   <span data-ttu-id="8b191-127">주 복제본 및 보조 복제본 인스턴스의 데이터베이스 미러링 엔드포인트 구성을 확인하여 일치하지 않는 구성을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="8b191-127">Check the database mirroring endpoint configuration for the instances of the primary and secondary replica and update the mismatched configuration.</span></span>  
  
-   <span data-ttu-id="8b191-128">포트가 충돌하는 경우 포트 번호를 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="8b191-128">Check if the port is conflicting, and if so, change the port number.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b191-129">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8b191-129">See Also</span></span>  
 <span data-ttu-id="8b191-130">[AlwaysOn 가용성 그룹 &#40;SQL Server 개요&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="8b191-130">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="8b191-131">AlwaysOn 대시보드 사용&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="8b191-131">Use the AlwaysOn Dashboard &#40;SQL Server Management Studio&#41;</span></span>](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
