---
title: MSSQLSERVER_32040 | Microsoft 문서
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 32040 (Database Engine error)
ms.assetid: 709219b1-f8b2-4696-8923-dd2e91492eb8
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 05692e2f20b0719c1ca8f48282c3b7aaed8e2341
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650072"
---
# <a name="mssqlserver_32040"></a><span data-ttu-id="935ef-102">MSSQLSERVER_32040</span><span class="sxs-lookup"><span data-stu-id="935ef-102">MSSQLSERVER_32040</span></span>
    
## <a name="details"></a><span data-ttu-id="935ef-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="935ef-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="935ef-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="935ef-104">Product Name</span></span>|<span data-ttu-id="935ef-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="935ef-105">SQL Server</span></span>|  
|<span data-ttu-id="935ef-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="935ef-106">Event ID</span></span>|<span data-ttu-id="935ef-107">32040</span><span class="sxs-lookup"><span data-stu-id="935ef-107">32040</span></span>|  
|<span data-ttu-id="935ef-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="935ef-108">Event Source</span></span>|<span data-ttu-id="935ef-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="935ef-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="935ef-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="935ef-110">Component</span></span>|<span data-ttu-id="935ef-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="935ef-111">SQLEngine</span></span>|  
|<span data-ttu-id="935ef-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="935ef-112">Symbolic Name</span></span>|<span data-ttu-id="935ef-113">SQLErrorNum32040</span><span class="sxs-lookup"><span data-stu-id="935ef-113">SQLErrorNum32040</span></span>|  
|<span data-ttu-id="935ef-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="935ef-114">Message Text</span></span>|<span data-ttu-id="935ef-115">'보내지 않은 가장 오래된 트랜잭션'에 대한 경고가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="935ef-115">The alert for 'oldest unsent transaction' has been raised.</span></span> <span data-ttu-id="935ef-116">'%d'의 현재 값이 임계값 '%d'을(를) 초과합니다.</span><span class="sxs-lookup"><span data-stu-id="935ef-116">The current value of '%d' surpasses the threshold '%d'.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="935ef-117">설명</span><span class="sxs-lookup"><span data-stu-id="935ef-117">Explanation</span></span>  
 <span data-ttu-id="935ef-118">이 데이터베이스 미러링 이벤트는 주 서버 인스턴스에서 발생하며 보내지 않은 가장 오래된 트랜잭션 기간이 사용자 지정 임계값에 도달했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="935ef-118">This database mirroring event is issued on the principal server instance to indicate that the age of the oldest unsent transaction has reached a user-specified threshold value.</span></span> <span data-ttu-id="935ef-119">일반적으로 이 이벤트는 두 시스템 간 대역폭이 감소했거나 로드가 증가한 경우와 같은</span><span class="sxs-lookup"><span data-stu-id="935ef-119">Typically, this event occurs because the performance of the system has changed.</span></span> <span data-ttu-id="935ef-120">시스템 성능의 변경으로 인해 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="935ef-120">Either the bandwidth between the two systems has decreased, or the load has increased.</span></span>  
  
 <span data-ttu-id="935ef-121">보내지 않은 가장 오래된 트랜잭션 기간은 보내지 않은 트랜잭션의 시간(분)을 기준으로 잠재적 데이터 손실을 측정하는 데 유용한 성능 메트릭입니다.</span><span class="sxs-lookup"><span data-stu-id="935ef-121">The age of the oldest unsent transaction is a performance metric that can help you evaluate the potential for data loss as measured by the number of minutes of unsent transactions.</span></span> <span data-ttu-id="935ef-122">이 메트릭은 성능 우선 모드 세션과 특히 관련이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="935ef-122">This metric is especially relevant for high-performance mode sessions.</span></span> <span data-ttu-id="935ef-123">그러나 파트너의 연결이 끊어져 미러링이 일시 중지되거나 일시 중단되면 이 메트릭은 보호 우선 모드 세션과도 관련이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="935ef-123">However, this metric is also relevant for high-safety mode session when mirroring is paused or suspended because the partners become disconnected.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="935ef-124">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="935ef-124">User Action</span></span>  
 <span data-ttu-id="935ef-125">주 서버 인스턴스 및 미러 서버 인스턴스의 로드를 확인하고 문제의 원인이 된 해당 네트워크 연결을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="935ef-125">Check the loads on the principal and mirror server instances and their network connection for the cause.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="935ef-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="935ef-126">See Also</span></span>  
 <span data-ttu-id="935ef-127">[데이터베이스 미러링&#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="935ef-127">[Database Mirroring &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md) </span></span>  
 [<span data-ttu-id="935ef-128">미러링 성능 메트릭에 대해 경고 임계값 및 경고 사용&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="935ef-128">Use Warning Thresholds and Alerts on Mirroring Performance Metrics &#40;SQL Server&#41;</span></span>](../../database-engine/database-mirroring/use-warning-thresholds-and-alerts-on-mirroring-performance-metrics-sql-server.md)  
  
  
