---
title: 보조 데이터베이스가 조인되지 않음 | Microsoft Docs
ms.custom: ''
ms.date: 01/09/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.agdashboard.drp2joined.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: 10817e5e-75fa-42dd-baa2-359bea3ad051
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 81275e85fd865924778f6d6f985e170a5bda9f9a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740473"
---
# <a name="secondary-database-is-not-joined"></a><span data-ttu-id="b5071-102">보조 데이터베이스에 조인되어 있지 않음</span><span class="sxs-lookup"><span data-stu-id="b5071-102">Secondary database is not joined</span></span>
    
## <a name="introduction"></a><span data-ttu-id="b5071-103">소개</span><span class="sxs-lookup"><span data-stu-id="b5071-103">Introduction</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b5071-104">**정책 이름**</span><span class="sxs-lookup"><span data-stu-id="b5071-104">**Policy Name**</span></span>|<span data-ttu-id="b5071-105">가용성 데이터베이스 조인 상태</span><span class="sxs-lookup"><span data-stu-id="b5071-105">Availability Database Join State</span></span>|  
|<span data-ttu-id="b5071-106">**문제점**</span><span class="sxs-lookup"><span data-stu-id="b5071-106">**Issue**</span></span>|<span data-ttu-id="b5071-107">보조 데이터베이스가 조인되지 않음</span><span class="sxs-lookup"><span data-stu-id="b5071-107">Secondary database is not joined.</span></span>|  
|<span data-ttu-id="b5071-108">**범주**</span><span class="sxs-lookup"><span data-stu-id="b5071-108">**Category**</span></span>|<span data-ttu-id="b5071-109">**경고**</span><span class="sxs-lookup"><span data-stu-id="b5071-109">**Warning**</span></span>|  
|<span data-ttu-id="b5071-110">**패싯**</span><span class="sxs-lookup"><span data-stu-id="b5071-110">**Facet**</span></span>|<span data-ttu-id="b5071-111">가용성 데이터베이스</span><span class="sxs-lookup"><span data-stu-id="b5071-111">Availability database</span></span>|  
  
## <a name="description"></a><span data-ttu-id="b5071-112">Description</span><span class="sxs-lookup"><span data-stu-id="b5071-112">Description</span></span>  
 <span data-ttu-id="b5071-113">이 정책은 보조 데이터베이스("보조 데이터베이스 복제본"이라고도 함)의 조인 상태를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="b5071-113">This policy checks the join state of the secondary database (also known as a "secondary database replica").</span></span> <span data-ttu-id="b5071-114">데이터 세트 복제본이 조인되지 않은 경우 정책은 비정상 상태에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b5071-114">The policy is in an unhealthy state when the dataset replica is not joined.</span></span> <span data-ttu-id="b5071-115">그렇지 않으면 정책은 정상 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="b5071-115">The policy is otherwise in a healthy state.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b5071-116">이 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]릴리스의 경우 가능한 원인 및 해결 방법에 대한 자세한 내용은 TechNet Wiki의 [보조 데이터베이스가 조인되지 않음](https://go.microsoft.com/fwlink/p/?LinkId=220862) 을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b5071-116">For this release of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], information about possible causes and solutions is located at [Secondary database is not joined](https://go.microsoft.com/fwlink/p/?LinkId=220862) on the TechNet Wiki.</span></span>  
  
## <a name="possible-causes"></a><span data-ttu-id="b5071-117">가능한 원인</span><span class="sxs-lookup"><span data-stu-id="b5071-117">Possible Causes</span></span>  
 <span data-ttu-id="b5071-118">보조 데이터베이스가 가용성 그룹에 조인되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b5071-118">This secondary database is not joined to the availability group.</span></span> <span data-ttu-id="b5071-119">이 보조 데이터베이스의 구성이 완료되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="b5071-119">The configuration of this secondary database is incomplete.</span></span>  
  
## <a name="possible-solution"></a><span data-ttu-id="b5071-120">가능한 해결 방법</span><span class="sxs-lookup"><span data-stu-id="b5071-120">Possible Solution</span></span>  
 <span data-ttu-id="b5071-121">Transact-SQL, PowerShell 또는 SQL Server Management Studio를 사용하여 보조 복제본을 가용성 그룹에 조인합니다.</span><span class="sxs-lookup"><span data-stu-id="b5071-121">Use Transact-SQL, PowerShell, or SQL Server Management Studio to join the secondary replica to the availability group.</span></span> <span data-ttu-id="b5071-122">보조 복제본을 가용성 그룹에 조인하는 방법은 [가용성 그룹에 보조 복제본 조인(SQL Server)](https://msdn.microsoft.com/library/ff878473\(en-us,SQL.110\).aspx)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b5071-122">For more information about joining secondary replicas to availability groups, see [Joining a Secondary Replica to an Availability Group (SQL Server)](https://msdn.microsoft.com/library/ff878473\(en-us,SQL.110\).aspx).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5071-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b5071-123">See Also</span></span>  
 <span data-ttu-id="b5071-124">[AlwaysOn 가용성 그룹 &#40;SQL Server 개요&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="b5071-124">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="b5071-125">AlwaysOn 대시보드 사용&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="b5071-125">Use the AlwaysOn Dashboard &#40;SQL Server Management Studio&#41;</span></span>](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
