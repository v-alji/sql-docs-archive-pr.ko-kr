---
title: 일부 가용성 데이터베이스의 데이터 동기화 상태가 정상이 아님 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.agdashboard.drp3datasynchealthy.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: 89f95d15-33c6-4768-bccd-9dbf8c4f49a9
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 221f25a1ee7e4a8719acc133372c742ca4a79303
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743436"
---
# <a name="data-synchronization-state-of-some-availability-database-is-not-healthy"></a><span data-ttu-id="28dbd-102">일부 가용성 데이터베이스의 데이터 동기화 상태가 정상이 아님</span><span class="sxs-lookup"><span data-stu-id="28dbd-102">Data synchronization state of some availability database is not healthy</span></span>
    
## <a name="introduction"></a><span data-ttu-id="28dbd-103">소개</span><span class="sxs-lookup"><span data-stu-id="28dbd-103">Introduction</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="28dbd-104">**정책 이름**</span><span class="sxs-lookup"><span data-stu-id="28dbd-104">**Policy Name**</span></span>|<span data-ttu-id="28dbd-105">가용성 복제본 데이터 동기화 상태</span><span class="sxs-lookup"><span data-stu-id="28dbd-105">Availability Replica Data Synchronization State</span></span>|  
|<span data-ttu-id="28dbd-106">**문제점**</span><span class="sxs-lookup"><span data-stu-id="28dbd-106">**Issue**</span></span>|<span data-ttu-id="28dbd-107">일부 가용성 데이터베이스의 데이터 동기화 상태가 정상이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="28dbd-107">Data synchronization state of some availability database is not healthy.</span></span>|  
|<span data-ttu-id="28dbd-108">**범주**</span><span class="sxs-lookup"><span data-stu-id="28dbd-108">**Category**</span></span>|<span data-ttu-id="28dbd-109">**경고**</span><span class="sxs-lookup"><span data-stu-id="28dbd-109">**Warning**</span></span>|  
|<span data-ttu-id="28dbd-110">**패싯**</span><span class="sxs-lookup"><span data-stu-id="28dbd-110">**Facet**</span></span>|<span data-ttu-id="28dbd-111">가용성 복제본</span><span class="sxs-lookup"><span data-stu-id="28dbd-111">Availability replica</span></span>|  
  
## <a name="description"></a><span data-ttu-id="28dbd-112">설명</span><span class="sxs-lookup"><span data-stu-id="28dbd-112">Description</span></span>  
 <span data-ttu-id="28dbd-113">이 정책은 가용성 데이터베이스("데이터베이스 복제본"이라고도 함)의 데이터 동기화 상태를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="28dbd-113">This policy checks the data synchronization state of the availability database (also known as a "database replica").</span></span> <span data-ttu-id="28dbd-114">데이터 동기화 상태가 NOT SYNCHRONIZING이거나 동기 커밋 데이터베이스 복제본에 대한 상태가 SYNCHRONIZED 상태가 아닌 경우 정책은 비정상 상태에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="28dbd-114">The policy is in an unhealthy state when the data synchronization state is NOT SYNCHRONIZING or the state is not SYNCHRONIZED for the synchronous-commit database replica.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="28dbd-115"> 이 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]릴리스의 경우 가능한 원인 및 해결 방법에 대한 자세한 내용은 TechNet Wiki의 [가용성 데이터베이스의 데이터 동기화 상태가 정상이 아님](https://go.microsoft.com/fwlink/p/?LinkId=220863) 을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="28dbd-115">For this release of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], information about possible causes and solutions is located at [Data synchronization state of availability database is not healthy](https://go.microsoft.com/fwlink/p/?LinkId=220863) on the TechNet Wiki.</span></span>  
  
## <a name="possible-causes"></a><span data-ttu-id="28dbd-116">가능한 원인</span><span class="sxs-lookup"><span data-stu-id="28dbd-116">Possible Causes</span></span>  
 <span data-ttu-id="28dbd-117">복제본의 가용성 데이터베이스 중 하나 이상의 상태가 비정상 데이터 동기화 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="28dbd-117">At least one availability database on the replica has an unhealthy data synchronization state.</span></span> <span data-ttu-id="28dbd-118">비동기 커밋 가용성 복제본인 경우 모든 가용성 데이터베이스를 SYNCHRONIZING 상태로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="28dbd-118">If this is an asynchronous-commit availability replica, all availability databases should be in the SYNCHRONIZING state.</span></span> <span data-ttu-id="28dbd-119">이 복제본이 동기 커밋 가용성 복제본이면 모든 가용성 데이터베이스가 SYNCHRONIZED 상태에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="28dbd-119">If this is a synchronous-commit availability replica, all availability databases should be in the SYNCHRONIZED state.</span></span> <span data-ttu-id="28dbd-120">이 문제는 다음에 의해 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="28dbd-120">This issue can be caused by the following:</span></span>  
  
-   <span data-ttu-id="28dbd-121">가용성 복제본의 연결이 끊어졌을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="28dbd-121">The availability replica might be disconnected.</span></span>  
  
-   <span data-ttu-id="28dbd-122">데이터 이동이 일시 중지되었을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="28dbd-122">The data movement might be suspended.</span></span>  
  
-   <span data-ttu-id="28dbd-123">데이터베이스에 액세스할 수 없는 상태일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="28dbd-123">The database might not be accessible.</span></span>  
  
-   <span data-ttu-id="28dbd-124">주 복제본이나 보조 복제본의 부하와 네트워크 대기 시간으로 인해 일시적인 지연 문제가 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="28dbd-124">There might be a temporary delay issue due to network latency or the load on the primary or secondary replica.</span></span>  
  
## <a name="possible-solution"></a><span data-ttu-id="28dbd-125">가능한 해결 방법</span><span class="sxs-lookup"><span data-stu-id="28dbd-125">Possible Solution</span></span>  
 <span data-ttu-id="28dbd-126">모든 연결 또는 데이터 이동 일시 중지 문제를 해결합니다.</span><span class="sxs-lookup"><span data-stu-id="28dbd-126">Resolve any connection or data movement suspend issues.</span></span> <span data-ttu-id="28dbd-127">SQL Server Management Studio를 사용하여 이벤트에서 이 문제를 확인하고 데이터베이스 오류를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="28dbd-127">Check the events for this issue using SQL Server Management Studio, and find the database error.</span></span> <span data-ttu-id="28dbd-128">특정 오류에 대한 문제 해결 단계를 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="28dbd-128">Follow the troubleshooting steps for the specific error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28dbd-129">참고 항목</span><span class="sxs-lookup"><span data-stu-id="28dbd-129">See Also</span></span>  
 <span data-ttu-id="28dbd-130">[AlwaysOn 가용성 그룹 &#40;SQL Server 개요&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="28dbd-130">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="28dbd-131">AlwaysOn 대시보드 사용&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="28dbd-131">Use the AlwaysOn Dashboard &#40;SQL Server Management Studio&#41;</span></span>](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
