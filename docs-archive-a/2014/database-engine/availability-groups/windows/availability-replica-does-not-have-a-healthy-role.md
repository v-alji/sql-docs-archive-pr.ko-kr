---
title: 가용성 복제본에 정상 상태의 역할이 없음 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.agdashboard.arp1rolehealthy.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: ebb2c9f4-2097-4688-b4fb-8f0571047317
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f7be26945903a5e3b602ef4a99c269de6a58b04a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87733160"
---
# <a name="availability-replica-does-not-have-a-healthy-role"></a><span data-ttu-id="3ddb0-102">가용성 복제본에 정상 상태의 역할이 없음</span><span class="sxs-lookup"><span data-stu-id="3ddb0-102">Availability replica does not have a healthy role</span></span>
    
## <a name="introduction"></a><span data-ttu-id="3ddb0-103">소개</span><span class="sxs-lookup"><span data-stu-id="3ddb0-103">Introduction</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3ddb0-104">**정책 이름**</span><span class="sxs-lookup"><span data-stu-id="3ddb0-104">**Policy Name**</span></span>|<span data-ttu-id="3ddb0-105">가용성 복제본 역할 상태</span><span class="sxs-lookup"><span data-stu-id="3ddb0-105">Availability Replica Role State</span></span>|  
|<span data-ttu-id="3ddb0-106">**문제점**</span><span class="sxs-lookup"><span data-stu-id="3ddb0-106">**Issue**</span></span>|<span data-ttu-id="3ddb0-107">가용성 복제본에 정상 상태의 역할이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3ddb0-107">Availability replica does not have a healthy role.</span></span>|  
|<span data-ttu-id="3ddb0-108">**범주**</span><span class="sxs-lookup"><span data-stu-id="3ddb0-108">**Category**</span></span>|<span data-ttu-id="3ddb0-109">**심각**</span><span class="sxs-lookup"><span data-stu-id="3ddb0-109">**Critical**</span></span>|  
|<span data-ttu-id="3ddb0-110">**패싯**</span><span class="sxs-lookup"><span data-stu-id="3ddb0-110">**Facet**</span></span>|<span data-ttu-id="3ddb0-111">가용성 복제본</span><span class="sxs-lookup"><span data-stu-id="3ddb0-111">Availability replica</span></span>|  
  
## <a name="description"></a><span data-ttu-id="3ddb0-112">설명</span><span class="sxs-lookup"><span data-stu-id="3ddb0-112">Description</span></span>  
 <span data-ttu-id="3ddb0-113">이 정책은 가용성 복제본의 역할 상태를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="3ddb0-113">This policy checks the state of the role of the availability replica.</span></span> <span data-ttu-id="3ddb0-114">가용성 복제본의 역할이 주 역할이나 보조 역할이 아닌 경우 정책은 비정상 상태에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3ddb0-114">The policy is in an unhealthy state when the role of the availability replica is neither primary nor secondary.</span></span> <span data-ttu-id="3ddb0-115">그렇지 않으면 정책은 정상 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="3ddb0-115">The policy is otherwise in a healthy state.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3ddb0-116">이 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]릴리스의 경우 가능한 원인 및 해결 방법에 대한 자세한 내용은 TechNet Wiki의 [가용성 복제본에 정상 상태의 역할이 없음](https://go.microsoft.com/fwlink/p/?LinkId=220856) 을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3ddb0-116">For this release of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], information about possible causes and solutions is located at [Availability replica does not have a healthy role](https://go.microsoft.com/fwlink/p/?LinkId=220856) on the TechNet Wiki.</span></span>  
  
## <a name="possible-causes"></a><span data-ttu-id="3ddb0-117">가능한 원인</span><span class="sxs-lookup"><span data-stu-id="3ddb0-117">Possible Causes</span></span>  
 <span data-ttu-id="3ddb0-118">이 가용성 복제본의 역할이 비정상 상태에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3ddb0-118">The role of this availability replica is unhealthy.</span></span> <span data-ttu-id="3ddb0-119">복제본에 주 역할 또는 보조 역할이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3ddb0-119">The replica does not have either the primary or secondary role.</span></span>  
  
## <a name="possible-solution-information_still_to_come"></a><span data-ttu-id="3ddb0-120">가능한 해결 방법: Information_still_to_come</span><span class="sxs-lookup"><span data-stu-id="3ddb0-120">Possible Solution: Information_still_to_come</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ddb0-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3ddb0-121">See Also</span></span>  
 <span data-ttu-id="3ddb0-122">[AlwaysOn 가용성 그룹 &#40;SQL Server 개요&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="3ddb0-122">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="3ddb0-123">AlwaysOn 대시보드 사용&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="3ddb0-123">Use the AlwaysOn Dashboard &#40;SQL Server Management Studio&#41;</span></span>](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
