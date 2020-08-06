---
title: 가용성 데이터베이스의 데이터 동기화 상태가 정상이 아님 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.agdashboard.arp3datasynchealthy.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: 4fd003e7-808e-4b0e-b28a-47d9f2616f06
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: a179008c20b108a2f6aaefd5dd80b22708e94a8b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743447"
---
# <a name="data-synchronization-state-of-availability-database-is-not-healthy"></a><span data-ttu-id="1802f-102">가용성 데이터베이스의 데이터 동기화 상태가 정상이 아님</span><span class="sxs-lookup"><span data-stu-id="1802f-102">Data synchronization state of availability database is not healthy</span></span>
    
## <a name="introduction"></a><span data-ttu-id="1802f-103">소개</span><span class="sxs-lookup"><span data-stu-id="1802f-103">Introduction</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1802f-104">**정책 이름**</span><span class="sxs-lookup"><span data-stu-id="1802f-104">**Policy Name**</span></span>|<span data-ttu-id="1802f-105">가용성 데이터베이스 데이터 동기화 상태</span><span class="sxs-lookup"><span data-stu-id="1802f-105">Availability Database Data Synchronization State</span></span>|  
|<span data-ttu-id="1802f-106">**문제점**</span><span class="sxs-lookup"><span data-stu-id="1802f-106">**Issue**</span></span>|<span data-ttu-id="1802f-107">가용성 데이터베이스의 데이터 동기화 상태가 정상이 아님</span><span class="sxs-lookup"><span data-stu-id="1802f-107">Data synchronization state of availability database is not healthy.</span></span>|  
|<span data-ttu-id="1802f-108">**범주**</span><span class="sxs-lookup"><span data-stu-id="1802f-108">**Category**</span></span>|<span data-ttu-id="1802f-109">**경고**</span><span class="sxs-lookup"><span data-stu-id="1802f-109">**Warning**</span></span>|  
|<span data-ttu-id="1802f-110">**패싯**</span><span class="sxs-lookup"><span data-stu-id="1802f-110">**Facet**</span></span>|<span data-ttu-id="1802f-111">가용성 데이터베이스</span><span class="sxs-lookup"><span data-stu-id="1802f-111">Availability database</span></span>|  
  
## <a name="description"></a><span data-ttu-id="1802f-112">Description</span><span class="sxs-lookup"><span data-stu-id="1802f-112">Description</span></span>  
 <span data-ttu-id="1802f-113">이 정책은 가용성 복제본에서 모든 가용성 데이터베이스("데이터베이스 복제본"이라고도 함)의 데이터 동기화 상태를 롤업합니다.</span><span class="sxs-lookup"><span data-stu-id="1802f-113">This policy rolls up the data synchronization state of all availability databases (also known as "database replicas") in the availability replica.</span></span> <span data-ttu-id="1802f-114">예상되는 데이터 동기화 상태가 아닌 데이터베이스 복제본이 있으면 정책이 비정상 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="1802f-114">The policy is in an unhealthy sate when any database replica is not in the expected data synchronization state.</span></span> <span data-ttu-id="1802f-115">그렇지 않으면 정책은 정상 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="1802f-115">The policy is otherwise in a healthy state.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1802f-116">이 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]릴리스의 경우 가능한 원인 및 해결 방법에 대한 자세한 내용은 TechNet Wiki의 [일부 가용성 데이터베이스의 데이터 동기화 상태가 정상이 아님](https://go.microsoft.com/fwlink/p/?LinkId=220858) 을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1802f-116">For this release of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], information about possible causes and solutions is located at [Data synchronization state of some availability database is not healthy](https://go.microsoft.com/fwlink/p/?LinkId=220858) on the TechNet Wiki.</span></span>  
  
## <a name="possible-causes"></a><span data-ttu-id="1802f-117">가능한 원인</span><span class="sxs-lookup"><span data-stu-id="1802f-117">Possible Causes</span></span>  
 <span data-ttu-id="1802f-118">이 가용성 데이터베이스의 데이터 동기화 상태가 정상이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="1802f-118">The data synchronization state of this availability database is unhealthy.</span></span> <span data-ttu-id="1802f-119">비동기 커밋 가용성 복제본에서 모든 가용성 데이터베이스는 SYNCHRONIZING 상태여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1802f-119">On an asynchronous-commit availability replica, every availability database should be in the SYNCHRONIZING state.</span></span> <span data-ttu-id="1802f-120">동기 커밋 복제본에서 모든 가용성 데이터베이스는 SYNCHRONIZED 상태에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1802f-120">On a synchronous-commit replica, every availability database must be in the SYNCHRONIZED state.</span></span>  
  
## <a name="possible-solution"></a><span data-ttu-id="1802f-121">가능한 해결 방법</span><span class="sxs-lookup"><span data-stu-id="1802f-121">Possible Solution</span></span>  
 <span data-ttu-id="1802f-122">데이터베이스 복제본 정책을 사용하여 비정상 데이터 동기화 상태의 데이터베이스 복제본을 찾은 다음 해당 데이터베이스 복제본에서 이 문제를 해결합니다.</span><span class="sxs-lookup"><span data-stu-id="1802f-122">Use the database replica policy to find the database replica with an unhealthy data synchronization state, and then resolve the issue at the database replica.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1802f-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1802f-123">See Also</span></span>  
 <span data-ttu-id="1802f-124">[AlwaysOn 가용성 그룹 &#40;SQL Server 개요&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="1802f-124">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="1802f-125">AlwaysOn 대시보드 사용&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="1802f-125">Use the AlwaysOn Dashboard &#40;SQL Server Management Studio&#41;</span></span>](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
