---
title: 가용성 데이터베이스가 일시 중지됨 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.agdashboard.drp1notsuspended.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: 6baee70f-848c-4e86-b20d-78875c0f82cb
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 07a547f217367f13df739348325461c862d831f9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646674"
---
# <a name="availability-database-is-suspended"></a><span data-ttu-id="8c3ab-102">가용성 데이터베이스가 일시 중지됨</span><span class="sxs-lookup"><span data-stu-id="8c3ab-102">Availability database is suspended</span></span>
    
## <a name="introduction"></a><span data-ttu-id="8c3ab-103">소개</span><span class="sxs-lookup"><span data-stu-id="8c3ab-103">Introduction</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8c3ab-104">**정책 이름**</span><span class="sxs-lookup"><span data-stu-id="8c3ab-104">**Policy Name**</span></span>|<span data-ttu-id="8c3ab-105">가용성 데이터베이스 일시 중지 상태</span><span class="sxs-lookup"><span data-stu-id="8c3ab-105">Availability Database Suspension State</span></span>|  
|<span data-ttu-id="8c3ab-106">**문제점**</span><span class="sxs-lookup"><span data-stu-id="8c3ab-106">**Issue**</span></span>|<span data-ttu-id="8c3ab-107">가용성 데이터베이스가 일시 중지됨</span><span class="sxs-lookup"><span data-stu-id="8c3ab-107">Availability database is suspended.</span></span>|  
|<span data-ttu-id="8c3ab-108">**범주**</span><span class="sxs-lookup"><span data-stu-id="8c3ab-108">**Category**</span></span>|<span data-ttu-id="8c3ab-109">**경고**</span><span class="sxs-lookup"><span data-stu-id="8c3ab-109">**Warning**</span></span>|  
|<span data-ttu-id="8c3ab-110">**패싯**</span><span class="sxs-lookup"><span data-stu-id="8c3ab-110">**Facet**</span></span>|<span data-ttu-id="8c3ab-111">가용성 데이터베이스</span><span class="sxs-lookup"><span data-stu-id="8c3ab-111">Availability database</span></span>|  
  
## <a name="description"></a><span data-ttu-id="8c3ab-112">Description</span><span class="sxs-lookup"><span data-stu-id="8c3ab-112">Description</span></span>  
 <span data-ttu-id="8c3ab-113">이 정책은 보조 데이터베이스("보조 데이터베이스 복제본"이라고도 함)의 데이터 이동 상태를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="8c3ab-113">This policy checks the state of data movement of the secondary database (also known as a "secondary database replica").</span></span> <span data-ttu-id="8c3ab-114">데이터 이동이 일시 중지되는 경우 정책은 비정상 상태에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8c3ab-114">The policy is in an unhealthy state when the data movement is suspended.</span></span> <span data-ttu-id="8c3ab-115">그렇지 않으면 정책은 정상 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="8c3ab-115">The policy is otherwise in a healthy state.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8c3ab-116"> 이 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]릴리스의 경우 가능한 원인 및 해결 방법에 대한 자세한 내용은 TechNet Wiki의 [가용성 데이터베이스가 일시 중지됨](https://go.microsoft.com/fwlink/p/?LinkId=220860) 을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="8c3ab-116">For this release of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], information about possible causes and solutions is located at [Availability database is suspended](https://go.microsoft.com/fwlink/p/?LinkId=220860) on the TechNet Wiki.</span></span>  
  
## <a name="possible-causes"></a><span data-ttu-id="8c3ab-117">가능한 원인</span><span class="sxs-lookup"><span data-stu-id="8c3ab-117">Possible Causes</span></span>  
 <span data-ttu-id="8c3ab-118">이 가용성 데이터베이스의 데이터 동기화는 다음과 같은 이유로 일시 중지되었을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8c3ab-118">Data synchronization on this availability database might have been suspended because of the following:</span></span>  
  
-   <span data-ttu-id="8c3ab-119">오류가 발생하여 시스템에서 데이터 동기화를 일시 중지했을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8c3ab-119">Due to an error, the system might have suspended data synchronization.</span></span>  
  
-   <span data-ttu-id="8c3ab-120">데이터베이스 관리자가 유지 보수를 위해 데이터 동기화를 일시 중지했을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8c3ab-120">The database administrator might have suspended data synchronization for maintenance purposes.</span></span>  
  
## <a name="possible-solution"></a><span data-ttu-id="8c3ab-121">가능한 해결 방법</span><span class="sxs-lookup"><span data-stu-id="8c3ab-121">Possible Solution</span></span>  
 <span data-ttu-id="8c3ab-122">데이터 동기화를 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="8c3ab-122">Resume data synchronization.</span></span> <span data-ttu-id="8c3ab-123">문제가 계속되면 이벤트 로그에서 가용성 그룹을 확인하여 시스템에서 데이터 이동이 일시 중지된 이유를 진단합니다.</span><span class="sxs-lookup"><span data-stu-id="8c3ab-123">If the issue persists, check the availability group in the Event log, and then diagnose why the system suspended data movement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c3ab-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8c3ab-124">See Also</span></span>  
 <span data-ttu-id="8c3ab-125">[AlwaysOn 가용성 그룹 &#40;SQL Server 개요&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="8c3ab-125">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="8c3ab-126">AlwaysOn 대시보드 사용&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="8c3ab-126">Use the AlwaysOn Dashboard &#40;SQL Server Management Studio&#41;</span></span>](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
