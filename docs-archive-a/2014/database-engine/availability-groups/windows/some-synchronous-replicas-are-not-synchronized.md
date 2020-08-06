---
title: 일부 동기 복제본이 동기화되지 않음 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.agdashboard.agp5synchronized.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: e58ed56e-4c30-42e6-a9fc-a8c401620e02
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ecef2d16e80e128834a71e1f1f112096f8ccc9cb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651274"
---
# <a name="some-synchronous-replicas-are-not-synchronized"></a><span data-ttu-id="55240-102">일부 동기 복제본이 동기화되지 않음</span><span class="sxs-lookup"><span data-stu-id="55240-102">Some synchronous replicas are not synchronized</span></span>
    
## <a name="introduction"></a><span data-ttu-id="55240-103">소개</span><span class="sxs-lookup"><span data-stu-id="55240-103">Introduction</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="55240-104">**정책 이름**</span><span class="sxs-lookup"><span data-stu-id="55240-104">**Policy Name**</span></span>|<span data-ttu-id="55240-105">동기 복제본 데이터 동기화 상태</span><span class="sxs-lookup"><span data-stu-id="55240-105">Synchronous Replicas Data Synchronization State</span></span>|  
|<span data-ttu-id="55240-106">**문제점**</span><span class="sxs-lookup"><span data-stu-id="55240-106">**Issue**</span></span>|<span data-ttu-id="55240-107">일부 동기 복제본이 동기화되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="55240-107">Some synchronous replicas are not synchronized.</span></span>|  
|<span data-ttu-id="55240-108">**범주**</span><span class="sxs-lookup"><span data-stu-id="55240-108">**Category**</span></span>|<span data-ttu-id="55240-109">**경고**</span><span class="sxs-lookup"><span data-stu-id="55240-109">**Warning**</span></span>|  
|<span data-ttu-id="55240-110">**패싯**</span><span class="sxs-lookup"><span data-stu-id="55240-110">**Facet**</span></span>|<span data-ttu-id="55240-111">가용성 그룹</span><span class="sxs-lookup"><span data-stu-id="55240-111">Availability group</span></span>|  
  
## <a name="description"></a><span data-ttu-id="55240-112">Description</span><span class="sxs-lookup"><span data-stu-id="55240-112">Description</span></span>  
 <span data-ttu-id="55240-113">이 정책은 모든 가용성 복제본의 데이터 동기화 상태를 롤업하여 예상되는 동기화 상태가 아닌 가용성 복제본이 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="55240-113">This policy rolls up the data synchronization state of all availability replicas and checks for any availability replicas that are not in the expected synchronization state.</span></span> <span data-ttu-id="55240-114">SYNCHRONIZING 상태가 아닌 비동기 복제본이 있거나 SYNCHRONIZED 상태가 아닌 동기 복제본이 있으면 정책은 비정상 상태에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="55240-114">The policy is in an unhealthy state when any asynchronous replica is not in a SYNCHRONIZING state and any synchronous replica is not in a SYNCHRONIZED state.</span></span> <span data-ttu-id="55240-115">그렇지 않으면 정책은 정상 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="55240-115">The policy state is otherwise healthy.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="55240-116">이 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]릴리스의 경우 가능한 원인 및 해결 방법에 대한 자세한 내용은 TechNet Wiki의 [일부 동기 복제본이 동기화되지 않음](https://go.microsoft.com/fwlink/p/?LinkId=220853) 을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="55240-116">For this release of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], information about possible causes and solutions is located at [Some synchronous replicas are not synchronized](https://go.microsoft.com/fwlink/p/?LinkId=220853) on the TechNet Wiki.</span></span>  
  
## <a name="possible-causes"></a><span data-ttu-id="55240-117">가능한 원인</span><span class="sxs-lookup"><span data-stu-id="55240-117">Possible Causes</span></span>  
 <span data-ttu-id="55240-118">이 가용성 그룹에서 하나 이상의 동기 복제본이 현재 동기화되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="55240-118">In this availability group, at least one synchronous replica is not currently synchronized.</span></span> <span data-ttu-id="55240-119">복제본 동기화 상태는 SYNCHONIZING 또는 NOT SYNCHRONIZING일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="55240-119">The replica synchronization state could be either SYNCHONIZING or NOT SYNCHRONIZING.</span></span>  
  
## <a name="possible-solution"></a><span data-ttu-id="55240-120">가능한 해결 방법</span><span class="sxs-lookup"><span data-stu-id="55240-120">Possible Solution</span></span>  
 <span data-ttu-id="55240-121">가용성 복제본 정책 상태를 사용하여 잘못된 동기화 상태의 가용성 복제본을 찾은 다음 가용성 복제본에서 문제를 해결합니다.</span><span class="sxs-lookup"><span data-stu-id="55240-121">Use the availability replica policy state to find the availability replica with the incorrect synchronization state, and then resolve the issue at the availability replica.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55240-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="55240-122">See Also</span></span>  
 <span data-ttu-id="55240-123">[AlwaysOn 가용성 그룹 &#40;SQL Server 개요&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="55240-123">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="55240-124">AlwaysOn 대시보드 사용&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="55240-124">Use the AlwaysOn Dashboard &#40;SQL Server Management Studio&#41;</span></span>](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
