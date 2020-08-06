---
title: SQL Server, Wait Statistics 개체 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Wait Statistics object
- SQLServer:Wait Statistics
ms.assetid: cb7f917d-4291-4115-9b78-ee7692ebbb2d
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 5cfd2f1309cb118896ff7951b7f82feb38de60e7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729388"
---
# <a name="sql-server-wait-statistics-object"></a><span data-ttu-id="200d4-102">SQL Server, Wait Statistics 개체</span><span class="sxs-lookup"><span data-stu-id="200d4-102">SQL Server, Wait Statistics Object</span></span>
  <span data-ttu-id="200d4-103">**SQLServer:Wait Statistics** 성능 개체는 대기 상태에 대한 정보를 보고하는 성능 카운터를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="200d4-103">The **SQLServer:Wait Statistics** performance object contains performance counters that report information about wait status.</span></span>  
  
 <span data-ttu-id="200d4-104">다음 표에서는 Wait Statistics 개체가 포함하는 카운터를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="200d4-104">The table below lists the counters that the Wait Statistics object contains.</span></span>  
  
|<span data-ttu-id="200d4-105">SQL Server Wait Statistics 카운터</span><span class="sxs-lookup"><span data-stu-id="200d4-105">SQL Server Wait Statistics counters</span></span>|<span data-ttu-id="200d4-106">Description</span><span class="sxs-lookup"><span data-stu-id="200d4-106">Description</span></span>|  
|-----------------------------------------|-----------------|  
|<span data-ttu-id="200d4-107">**Lock waits**</span><span class="sxs-lookup"><span data-stu-id="200d4-107">**Lock waits**</span></span>|<span data-ttu-id="200d4-108">잠금을 기다리는 프로세스에 대한 통계입니다.</span><span class="sxs-lookup"><span data-stu-id="200d4-108">Statistics for processes waiting on a lock.</span></span>|  
|<span data-ttu-id="200d4-109">**Log buffer waits**</span><span class="sxs-lookup"><span data-stu-id="200d4-109">**Log buffer waits**</span></span>|<span data-ttu-id="200d4-110">로그 버퍼 사용을 기다리는 프로세스에 대한 통계입니다.</span><span class="sxs-lookup"><span data-stu-id="200d4-110">Statistics for processes waiting for log buffer to be available.</span></span>|  
|<span data-ttu-id="200d4-111">**Log write waits**</span><span class="sxs-lookup"><span data-stu-id="200d4-111">**Log write waits**</span></span>|<span data-ttu-id="200d4-112">로그 버퍼 작성을 기다리는 프로세스에 대한 통계입니다.</span><span class="sxs-lookup"><span data-stu-id="200d4-112">Statistics for processes waiting for log buffer to be written.</span></span>|  
|<span data-ttu-id="200d4-113">**Memory grant queue waits**</span><span class="sxs-lookup"><span data-stu-id="200d4-113">**Memory grant queue waits**</span></span>|<span data-ttu-id="200d4-114">메모리 부여를 기다리는 프로세스에 대한 통계입니다.</span><span class="sxs-lookup"><span data-stu-id="200d4-114">Statistics for processes waiting for memory grant to become available.</span></span>|  
|<span data-ttu-id="200d4-115">**Network IO waits**</span><span class="sxs-lookup"><span data-stu-id="200d4-115">**Network IO waits**</span></span>|<span data-ttu-id="200d4-116">네트워크 I/O 대기와 관련된 통계입니다.</span><span class="sxs-lookup"><span data-stu-id="200d4-116">Statistics relevant to wait on network I/O.</span></span>|  
|<span data-ttu-id="200d4-117">**Non-Page latch waits**</span><span class="sxs-lookup"><span data-stu-id="200d4-117">**Non-Page latch waits**</span></span>|<span data-ttu-id="200d4-118">비페이지 래치와 관련된 통계입니다.</span><span class="sxs-lookup"><span data-stu-id="200d4-118">Statistics relevant to non-page latches.</span></span>|  
|<span data-ttu-id="200d4-119">**Page IO latch waits**</span><span class="sxs-lookup"><span data-stu-id="200d4-119">**Page IO latch waits**</span></span>|<span data-ttu-id="200d4-120">페이지 I/O 래치와 관련된 통계입니다.</span><span class="sxs-lookup"><span data-stu-id="200d4-120">Statistics relevant to page I/O latches.</span></span>|  
|<span data-ttu-id="200d4-121">**Page latch waits**</span><span class="sxs-lookup"><span data-stu-id="200d4-121">**Page latch waits**</span></span>|<span data-ttu-id="200d4-122">I/O 래치를 제외한 페이지 래치와 관련된 통계입니다.</span><span class="sxs-lookup"><span data-stu-id="200d4-122">Statistics relevant to page latches, not including I/O latches.</span></span>|  
|<span data-ttu-id="200d4-123">**Thread-safe memory objects waits**</span><span class="sxs-lookup"><span data-stu-id="200d4-123">**Thread-safe memory objects waits**</span></span>|<span data-ttu-id="200d4-124">스레드로부터 안전한 메모리 할당자를 기다리는 프로세스에 대한 통계입니다.</span><span class="sxs-lookup"><span data-stu-id="200d4-124">Statistics for processes waiting on thread-safe memory allocators.</span></span>|  
|<span data-ttu-id="200d4-125">**Transaction ownership waits**</span><span class="sxs-lookup"><span data-stu-id="200d4-125">**Transaction ownership waits**</span></span>|<span data-ttu-id="200d4-126">트랜잭션에 대한 액세스를 동기화하는 프로세스와 관련된 통계입니다.</span><span class="sxs-lookup"><span data-stu-id="200d4-126">Statistics relevant to processes synchronizing access to transaction.</span></span>|  
|<span data-ttu-id="200d4-127">**Wait for the worker**</span><span class="sxs-lookup"><span data-stu-id="200d4-127">**Wait for the worker**</span></span>|<span data-ttu-id="200d4-128">작업자 활성화를 기다리는 프로세스와 관련된 통계입니다.</span><span class="sxs-lookup"><span data-stu-id="200d4-128">Statistics relevant to processes waiting for worker to become available.</span></span>|  
|<span data-ttu-id="200d4-129">**Workspace synchronization waits**</span><span class="sxs-lookup"><span data-stu-id="200d4-129">**Workspace synchronization waits**</span></span>|<span data-ttu-id="200d4-130">작업 영역에 대한 액세스를 동기화하는 프로세스와 관련된 통계입니다.</span><span class="sxs-lookup"><span data-stu-id="200d4-130">Statistics relevant to processes synchronizing access to workspace.</span></span>|  
  
 <span data-ttu-id="200d4-131">개체의 각 카운터는 다음 인스턴스를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="200d4-131">Each counter in the object contains the following instances:</span></span>  
  
|<span data-ttu-id="200d4-132">항목</span><span class="sxs-lookup"><span data-stu-id="200d4-132">Item</span></span>|<span data-ttu-id="200d4-133">Description</span><span class="sxs-lookup"><span data-stu-id="200d4-133">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="200d4-134">**평균 대기 시간(밀리초)**</span><span class="sxs-lookup"><span data-stu-id="200d4-134">**Average wait time (ms)**</span></span>|<span data-ttu-id="200d4-135">선택한 유형에 대한 평균 대기 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="200d4-135">Average time for the selected type of wait.</span></span>|  
|<span data-ttu-id="200d4-136">**초당 누적 대기 시간(밀리초)**</span><span class="sxs-lookup"><span data-stu-id="200d4-136">**Cumulative wait time (ms) per second**</span></span>|<span data-ttu-id="200d4-137">선택한 유형에 대한 초당 대기 시간 집계입니다.</span><span class="sxs-lookup"><span data-stu-id="200d4-137">Aggregated wait time per second, for the selected type of wait.</span></span>|  
|<span data-ttu-id="200d4-138">**진행 중인 대기 작업**</span><span class="sxs-lookup"><span data-stu-id="200d4-138">**Waits in progress**</span></span>|<span data-ttu-id="200d4-139">선택한 유형에 대한 현재 대기 중인 프로세스의 수입니다.</span><span class="sxs-lookup"><span data-stu-id="200d4-139">Number of processes currently waiting on the following type.</span></span>|  
|<span data-ttu-id="200d4-140">**초당 시작된 대기 작업**</span><span class="sxs-lookup"><span data-stu-id="200d4-140">**Waits started per second**</span></span>|<span data-ttu-id="200d4-141">선택한 대기 유형에 대한 초당 시작된 대기 작업의 수입니다.</span><span class="sxs-lookup"><span data-stu-id="200d4-141">Number of waits started per second of the selected type of wait.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="200d4-142">참고 항목</span><span class="sxs-lookup"><span data-stu-id="200d4-142">See Also</span></span>  
 [<span data-ttu-id="200d4-143">리소스 사용 모니터링&#40;시스템 모니터&#41;</span><span class="sxs-lookup"><span data-stu-id="200d4-143">Monitor Resource Usage &#40;System Monitor&#41;</span></span>](monitor-resource-usage-system-monitor.md)  
  
  
