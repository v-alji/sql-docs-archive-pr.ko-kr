---
title: MSSQLSERVER_32043 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 32043 (Database Engine error)
ms.assetid: a0c48ae3-4c8c-419c-afb5-579fcefac01d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 2febc7173c8144451c7a9b0576f2293d5594c6df
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646520"
---
# <a name="mssqlserver_32043"></a><span data-ttu-id="a4f0c-102">MSSQLSERVER_32043</span><span class="sxs-lookup"><span data-stu-id="a4f0c-102">MSSQLSERVER_32043</span></span>
    
## <a name="details"></a><span data-ttu-id="a4f0c-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="a4f0c-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a4f0c-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="a4f0c-104">Product Name</span></span>|<span data-ttu-id="a4f0c-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="a4f0c-105">SQL Server</span></span>|  
|<span data-ttu-id="a4f0c-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="a4f0c-106">Event ID</span></span>|<span data-ttu-id="a4f0c-107">32043</span><span class="sxs-lookup"><span data-stu-id="a4f0c-107">32043</span></span>|  
|<span data-ttu-id="a4f0c-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="a4f0c-108">Event Source</span></span>|<span data-ttu-id="a4f0c-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="a4f0c-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="a4f0c-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="a4f0c-110">Component</span></span>|<span data-ttu-id="a4f0c-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="a4f0c-111">SQLEngine</span></span>|  
|<span data-ttu-id="a4f0c-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="a4f0c-112">Symbolic Name</span></span>|<span data-ttu-id="a4f0c-113">SQLErrorNum32043</span><span class="sxs-lookup"><span data-stu-id="a4f0c-113">SQLErrorNum32043</span></span>|  
|<span data-ttu-id="a4f0c-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="a4f0c-114">Message Text</span></span>|<span data-ttu-id="a4f0c-115">'복원되지 않은 로그'에 대한 경고가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="a4f0c-115">The alert for 'unrestored log' has been raised.</span></span> <span data-ttu-id="a4f0c-116">'%d'의 현재 값이 임계값 '%d'을(를) 초과합니다.</span><span class="sxs-lookup"><span data-stu-id="a4f0c-116">The current value of '%d' surpasses the threshold '%d'.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="a4f0c-117">설명</span><span class="sxs-lookup"><span data-stu-id="a4f0c-117">Explanation</span></span>  
 <span data-ttu-id="a4f0c-118">이 데이터베이스 미러링 이벤트는 미러 서버 인스턴스에서 발생하며 복원되지 않은 로그의 양이 사용자 지정 임계값에 도달했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a4f0c-118">This database mirroring event is issued on the mirror server instance to indicate that the amount of unrestored log reached a user-specified threshold value.</span></span> <span data-ttu-id="a4f0c-119">일반적으로 이 이벤트는 두 시스템 간 대역폭이 감소했거나 로드가 증가한 경우와 같은</span><span class="sxs-lookup"><span data-stu-id="a4f0c-119">Typically, this event occurs because the performance of the system has changed.</span></span> <span data-ttu-id="a4f0c-120">시스템 성능의 변경으로 인해 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="a4f0c-120">Either the bandwidth between the two systems has decreased, or the load has increased.</span></span>  
  
 <span data-ttu-id="a4f0c-121">복원되지 않은 로그는 미러 서버 인스턴스에서 수신하여 디스크에 기록되었지만 미러 데이터베이스를 복원하기 위해 대기 중인 로그입니다.</span><span class="sxs-lookup"><span data-stu-id="a4f0c-121">An unrestored log is a log that has been received by the mirror server instance and written to disk but is waiting to be restored to the mirror database.</span></span> <span data-ttu-id="a4f0c-122">복원되지 않은 로그의 양(KB)은 현재 장애 조치(Failover) 시간을 계산하는 데 유용한 성능 메트릭입니다.</span><span class="sxs-lookup"><span data-stu-id="a4f0c-122">The amount of unrestored log in kilobytes (KB) is a performance metric that can help you evaluate the current failover time.</span></span> <span data-ttu-id="a4f0c-123">이 시간은 데이터베이스를 복구하고 이 데이터베이스를 온라인 상태로 만드는 데 필요한 짧은 추가 시간과 더불어 복원되지 않은 로그에 적용할 때 필요하며 장애 조치 시간의 주요 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="a4f0c-123">The time that is required to apply the unrestored log is the main factor in failover time, along with a short additional time that is required to recover the database and bring it online.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a4f0c-124">자동 장애 조치의 경우 시스템이 오류를 감지하는 데 걸리는 시간은 장애 조치 시간과 관계가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a4f0c-124">For an automatic failover, the time for the system to notice the failure is independent of the failover time.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="a4f0c-125">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="a4f0c-125">User Action</span></span>  
 <span data-ttu-id="a4f0c-126">주 서버 인스턴스 및 미러 서버 인스턴스의 로드를 확인하고 문제의 원인이 된 해당 네트워크 연결을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="a4f0c-126">Check the loads on the principal and mirror server instances and their network connection for the cause.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4f0c-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a4f0c-127">See Also</span></span>  
 <span data-ttu-id="a4f0c-128">[데이터베이스 미러링&#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="a4f0c-128">[Database Mirroring &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md) </span></span>  
 [<span data-ttu-id="a4f0c-129">미러링 성능 메트릭에 대해 경고 임계값 및 경고 사용&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a4f0c-129">Use Warning Thresholds and Alerts on Mirroring Performance Metrics &#40;SQL Server&#41;</span></span>](../../database-engine/database-mirroring/use-warning-thresholds-and-alerts-on-mirroring-performance-metrics-sql-server.md)  
  
  
