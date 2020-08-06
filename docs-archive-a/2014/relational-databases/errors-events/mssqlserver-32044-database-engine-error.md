---
title: MSSQLSERVER_32044 | Microsoft 문서
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 32044 (Database Engine error)
ms.assetid: f2d073be-d9a1-4837-8a38-028d3e3403bd
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 27d9655c3a908f1302f048c6f68159d4f610367a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650070"
---
# <a name="mssqlserver_32044"></a><span data-ttu-id="e6fc8-102">MSSQLSERVER_32044</span><span class="sxs-lookup"><span data-stu-id="e6fc8-102">MSSQLSERVER_32044</span></span>
    
## <a name="details"></a><span data-ttu-id="e6fc8-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="e6fc8-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e6fc8-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="e6fc8-104">Product Name</span></span>|<span data-ttu-id="e6fc8-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="e6fc8-105">SQL Server</span></span>|  
|<span data-ttu-id="e6fc8-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="e6fc8-106">Event ID</span></span>|<span data-ttu-id="e6fc8-107">32044</span><span class="sxs-lookup"><span data-stu-id="e6fc8-107">32044</span></span>|  
|<span data-ttu-id="e6fc8-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="e6fc8-108">Event Source</span></span>|<span data-ttu-id="e6fc8-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="e6fc8-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="e6fc8-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="e6fc8-110">Component</span></span>|<span data-ttu-id="e6fc8-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="e6fc8-111">SQLEngine</span></span>|  
|<span data-ttu-id="e6fc8-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="e6fc8-112">Symbolic Name</span></span>|<span data-ttu-id="e6fc8-113">SQLErrorNum32044</span><span class="sxs-lookup"><span data-stu-id="e6fc8-113">SQLErrorNum32044</span></span>|  
|<span data-ttu-id="e6fc8-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="e6fc8-114">Message Text</span></span>|<span data-ttu-id="e6fc8-115">'미러 커밋 오버헤드'에 대한 경고가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="e6fc8-115">The alert for 'mirror commit overhead' has been raised.</span></span> <span data-ttu-id="e6fc8-116">'%d'의 현재 값이 임계값 '%d'을(를) 초과합니다.</span><span class="sxs-lookup"><span data-stu-id="e6fc8-116">The current value of '%d' surpasses the threshold '%d'.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="e6fc8-117">설명</span><span class="sxs-lookup"><span data-stu-id="e6fc8-117">Explanation</span></span>  
 <span data-ttu-id="e6fc8-118">이 데이터베이스 미러링 이벤트는 주 서버 인스턴스에서 실행되어 집계 커밋 대기 시간이 데이터베이스 미러링으로 인해 사용자 지정 임계값에 도달했거나 초과했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="e6fc8-118">This database mirroring event is issued on the principal server instance to indicate that the aggregate commit wait time reached or exceeded a user-specified threshold value because of database mirroring.</span></span> <span data-ttu-id="e6fc8-119">대기 시간은 트랜잭션의 수와 각 트랜잭션에 걸린 시간의 곱입니다.</span><span class="sxs-lookup"><span data-stu-id="e6fc8-119">The wait time is the product of the number of transactions and the time of each.</span></span> <span data-ttu-id="e6fc8-120">예를 들어 1000개의 트랜잭션 \* 1밀리초의 경우와 1개의 트랜잭션 \* 1000밀리초의경우 모두 1000밀리초의 대기 시간이 계산됩니다.</span><span class="sxs-lookup"><span data-stu-id="e6fc8-120">For example, the following cases both produce 1000 milliseconds of wait time: 1000 transactions \* 1 millisecond, and 1 transaction \* 1000 milliseconds.</span></span> <span data-ttu-id="e6fc8-121">커밋 대기 시간의 증가는 트랜잭션 개수의 급증, 로그 전송 지연, 미러 서버 인스턴스에 대한 로그 플러시 지연에 의해 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6fc8-121">An increased commit wait time can be caused by a surge in the transaction count, delays in sending the log, or delays in flushing the log on the mirror server instance.</span></span>  
  
 <span data-ttu-id="e6fc8-122">미러 커밋 오버헤드의 양은 동기화 작업의 현재 성능에 미치는 영향을 평가하는 데 도움이 되는 성능 메트릭입니다.</span><span class="sxs-lookup"><span data-stu-id="e6fc8-122">The amount of mirror commit overhead is a performance metric that can help you evaluate the current performance impact of synchronous operation.</span></span> <span data-ttu-id="e6fc8-123">이 메트릭은 보호 우선 모드에만 해당됩니다.</span><span class="sxs-lookup"><span data-stu-id="e6fc8-123">This metric is relevant only in high-safety mode.</span></span> <span data-ttu-id="e6fc8-124">보호 우선 모드는 동기적이므로 주 서버 인스턴스는 미러 서버 인스턴스로 로그 레코드를 보낸 후 미러 서버 인스턴스에서 디스크에 로그 레코드를 기록했음을 확인할 때까지 트랜잭션에 대한 커밋을 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="e6fc8-124">Because high-safety mode is synchronous, the principal server instance waits to commit the transaction after it sends a log record to the mirror server instance until it receives confirmation that the mirror server instance has written the log record to disk.</span></span> <span data-ttu-id="e6fc8-125">로그 레코드는 미러 데이터베이스로 복원되기를 기다리는 동안 미러 서버 인스턴스의 디스크에 남아 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6fc8-125">The log record remains on disk on the mirror server instance while it waits to be restored to the mirror database.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="e6fc8-126">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="e6fc8-126">User Action</span></span>  
 <span data-ttu-id="e6fc8-127">주 서버 인스턴스 및 미러 서버 인스턴스의 로드를 확인하고 문제의 원인이 된 해당 네트워크 연결을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="e6fc8-127">Check the loads on the principal and mirror server instances and their network connection for the cause.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6fc8-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e6fc8-128">See Also</span></span>  
 <span data-ttu-id="e6fc8-129">[데이터베이스 미러링&#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="e6fc8-129">[Database Mirroring &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md) </span></span>  
 [<span data-ttu-id="e6fc8-130">미러링 성능 메트릭에 대해 경고 임계값 및 경고 사용&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="e6fc8-130">Use Warning Thresholds and Alerts on Mirroring Performance Metrics &#40;SQL Server&#41;</span></span>](../../database-engine/database-mirroring/use-warning-thresholds-and-alerts-on-mirroring-performance-metrics-sql-server.md)  
  
  
