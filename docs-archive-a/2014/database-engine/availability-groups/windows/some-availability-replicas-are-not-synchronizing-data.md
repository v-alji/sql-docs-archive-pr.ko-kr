---
title: 일부 가용성 복제본에서 데이터 동기화가 수행되지 않음 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.agdashboard.agp4synchronizing.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: 3db6a569-e942-4321-a0dd-c4ab002087c8
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 762b7da1f7b8a07257c2a900307eb1bb10408653
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651280"
---
# <a name="some-availability-replicas-are-not-synchronizing-data"></a><span data-ttu-id="ba8f0-102">일부 가용성 복제본에서 데이터 동기화가 수행되지 않음</span><span class="sxs-lookup"><span data-stu-id="ba8f0-102">Some availability replicas are not synchronizing data</span></span>
    
## <a name="introduction"></a><span data-ttu-id="ba8f0-103">소개</span><span class="sxs-lookup"><span data-stu-id="ba8f0-103">Introduction</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ba8f0-104">**정책 이름**</span><span class="sxs-lookup"><span data-stu-id="ba8f0-104">**Policy Name**</span></span>|<span data-ttu-id="ba8f0-105">가용성 복제본 데이터 동기화 상태</span><span class="sxs-lookup"><span data-stu-id="ba8f0-105">Availability Replicas Data Synchronization State</span></span>|  
|<span data-ttu-id="ba8f0-106">**문제점**</span><span class="sxs-lookup"><span data-stu-id="ba8f0-106">**Issue**</span></span>|<span data-ttu-id="ba8f0-107">일부 가용성 복제본에서 데이터 동기화가 수행되지 않음</span><span class="sxs-lookup"><span data-stu-id="ba8f0-107">Some availability replicas are not synchronizing data.</span></span>|  
|<span data-ttu-id="ba8f0-108">**범주**</span><span class="sxs-lookup"><span data-stu-id="ba8f0-108">**Category**</span></span>|<span data-ttu-id="ba8f0-109">**경고**</span><span class="sxs-lookup"><span data-stu-id="ba8f0-109">**Warning**</span></span>|  
|<span data-ttu-id="ba8f0-110">**패싯**</span><span class="sxs-lookup"><span data-stu-id="ba8f0-110">**Facet**</span></span>|<span data-ttu-id="ba8f0-111">가용성 그룹</span><span class="sxs-lookup"><span data-stu-id="ba8f0-111">Availability group</span></span>|  
  
## <a name="description"></a><span data-ttu-id="ba8f0-112">Description</span><span class="sxs-lookup"><span data-stu-id="ba8f0-112">Description</span></span>  
 <span data-ttu-id="ba8f0-113">이 정책은 가용성 그룹에 있는 모든 가용성 복제본의 데이터 동기화 상태를 롤업하여 가용성 복제본의 동기화가 작동 중이 아닌지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="ba8f0-113">This policy rolls up the data synchronization state of all availability replicas in the availability group and checks if the synchronization of any availability replica is not operational.</span></span> <span data-ttu-id="ba8f0-114">데이터 동기화 상태가 NOT SYNCRONIZING인 가용성 복제본이 있으면 정책이 비정상 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="ba8f0-114">The policy is in an unhealthy state if any of the data synchronization states of the availability replica is NOT SYNCRONIZING.</span></span>  
  
 <span data-ttu-id="ba8f0-115">데이터 동기화 상태가 NOT SYNCRONIZING인 가용성 복제본이 없으면 정책이 정상 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="ba8f0-115">This policy is in a healthy state if none of the data synchronization states of the availability replica is NOT SYNCHRONIZING.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ba8f0-116">이 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]릴리스의 경우 가능한 원인 및 해결 방법은 TechNet Wiki의 [일부 가용성 복제본에서 데이터 동기화가 수행되지 않음](https://go.microsoft.com/fwlink/p/?LinkId=220852) 을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ba8f0-116">For this release of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], information about possible causes and solutions is located at [Some availability replicas are not synchronizing data](https://go.microsoft.com/fwlink/p/?LinkId=220852) on the TechNet Wiki.</span></span>  
  
## <a name="possible-causes"></a><span data-ttu-id="ba8f0-117">가능한 원인</span><span class="sxs-lookup"><span data-stu-id="ba8f0-117">Possible Causes</span></span>  
 <span data-ttu-id="ba8f0-118">이 가용성 그룹에서 하나 이상의 보조 복제본이 NOT SYNCHRONIZING 동기화 상태에 있으며 주 복제본에서 데이터를 받고 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ba8f0-118">In this availability group, at least one secondary replica has a NOT SYNCHRONIZING synchronization state and is not receiving data from the primary replica.</span></span>  
  
## <a name="possible-solution"></a><span data-ttu-id="ba8f0-119">가능한 해결 방법</span><span class="sxs-lookup"><span data-stu-id="ba8f0-119">Possible Solution</span></span>  
 <span data-ttu-id="ba8f0-120">가용성 복제본 정책 상태를 사용하여 상태가 NOT SYNCHROINIZING인 가용성 복제본을 찾은 다음 해당 가용성 복제본에서 문제를 해결합니다.</span><span class="sxs-lookup"><span data-stu-id="ba8f0-120">Use the availability replica policy state to find the availability replica with a NOT SYNCHROINIZING state, and then resolve the issue at the availability replica.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba8f0-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ba8f0-121">See Also</span></span>  
 <span data-ttu-id="ba8f0-122">[AlwaysOn 가용성 그룹 &#40;SQL Server 개요&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="ba8f0-122">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="ba8f0-123">AlwaysOn 대시보드 사용&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="ba8f0-123">Use the AlwaysOn Dashboard &#40;SQL Server Management Studio&#41;</span></span>](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
