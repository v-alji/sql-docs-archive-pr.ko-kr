---
title: XTP 가비지 수집 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
ms.assetid: 64ae91e5-b420-44b4-af1a-f8bca83d7f41
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 341a45c1c103f154672bb01a0648339562ee9750
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730580"
---
# <a name="xtp-garbage-collection"></a><span data-ttu-id="9063a-102">XTP 가비지 수집</span><span class="sxs-lookup"><span data-stu-id="9063a-102">XTP Garbage Collection</span></span>
  <span data-ttu-id="9063a-103">XTP 가비지 수집 성능 개체에는 XTP 엔진의 가비지 수집기와 관련된 카운터가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="9063a-103">The XTP Garbage Collection performance object contains counters related to the XTP engine's garbage collector.</span></span>  
  
 <span data-ttu-id="9063a-104">이 표에서는 **XTP 가비지 수집** 카운터에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="9063a-104">This table describes the **XTP garbage Collection** counters.</span></span>  
  
|<span data-ttu-id="9063a-105">카운터</span><span class="sxs-lookup"><span data-stu-id="9063a-105">Counter</span></span>|<span data-ttu-id="9063a-106">Description</span><span class="sxs-lookup"><span data-stu-id="9063a-106">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9063a-107">**Dusty corner scan retries/sec (GC-issued)**</span><span class="sxs-lookup"><span data-stu-id="9063a-107">**Dusty corner scan retries/sec (GC-issued)**</span></span>|<span data-ttu-id="9063a-108">가비지 수집기에 의해 실행된 불량 영역 청소(dusty corner sweeps) 중 발생한 초당 검색 재시도 횟수입니다(평균).</span><span class="sxs-lookup"><span data-stu-id="9063a-108">The number of scan retries due to write conflicts during dusty corner sweeps issued by the garbage collector (on average), per second.</span></span> <span data-ttu-id="9063a-109">이 카운터는 사용자용이 아닌 매우 낮은 수준의 카운터입니다.</span><span class="sxs-lookup"><span data-stu-id="9063a-109">This is a very low-level counter, not intended for customer use.</span></span>|  
|<span data-ttu-id="9063a-110">**Main GC work items/sec**</span><span class="sxs-lookup"><span data-stu-id="9063a-110">**Main GC work items/sec**</span></span>|<span data-ttu-id="9063a-111">기본 GC 스레드에서 처리되는 작업 항목 수입니다.</span><span class="sxs-lookup"><span data-stu-id="9063a-111">The number of work items processed by the main GC thread.</span></span>|  
|<span data-ttu-id="9063a-112">**Parallel GC work item/sec**</span><span class="sxs-lookup"><span data-stu-id="9063a-112">**Parallel GC work item/sec**</span></span>|<span data-ttu-id="9063a-113">병렬 스레드가 GC 작업 항목을 실행한 횟수입니다.</span><span class="sxs-lookup"><span data-stu-id="9063a-113">The number of times a parallel thread has executed a GC work item.</span></span>|  
|<span data-ttu-id="9063a-114">**Rows processed/sec**</span><span class="sxs-lookup"><span data-stu-id="9063a-114">**Rows processed/sec**</span></span>|<span data-ttu-id="9063a-115">가비지 수집기에서 처리된 초당 행 수입니다(평균).</span><span class="sxs-lookup"><span data-stu-id="9063a-115">The number of rows processed by the garbage collector (on average), per second.</span></span>|  
|<span data-ttu-id="9063a-116">**Rows processed/sec (first in bucket and removed)**</span><span class="sxs-lookup"><span data-stu-id="9063a-116">**Rows processed/sec (first in bucket and removed)**</span></span>|<span data-ttu-id="9063a-117">처음에 해당 해시 버킷에 포함되었고 즉시 제거할 수 있었던 가비지 수집기에서 처리된 초당 행 수입니다(평균).</span><span class="sxs-lookup"><span data-stu-id="9063a-117">The number of rows processed by the garbage collector that were first in the corresponding hash bucket, and were able to be removed immediately (on average), per second.</span></span>|  
|<span data-ttu-id="9063a-118">**Rows processed/sec (first in bucket)**</span><span class="sxs-lookup"><span data-stu-id="9063a-118">**Rows processed/sec (first in bucket)**</span></span>|<span data-ttu-id="9063a-119">처음에 해당 해시 버킷에 포함되었던 가비지 수집기에서 처리된 초당 행 수입니다(평균).</span><span class="sxs-lookup"><span data-stu-id="9063a-119">The number of rows processed by the garbage collector that were first in the corresponding hash bucket (on average), per second.</span></span>|  
|<span data-ttu-id="9063a-120">**Rows processed/sec (marked for unlink)**</span><span class="sxs-lookup"><span data-stu-id="9063a-120">**Rows processed/sec (marked for unlink)**</span></span>|<span data-ttu-id="9063a-121">이미 연결 해제로 표시된 가비지 수집기에서 처리된 초당 행 수입니다(평균).</span><span class="sxs-lookup"><span data-stu-id="9063a-121">The number of rows processed by the garbage collector that were already marked for unlink (on average), per second.</span></span>|  
|<span data-ttu-id="9063a-122">**Rows processed/sec (no sweep needed)**</span><span class="sxs-lookup"><span data-stu-id="9063a-122">**Rows processed/sec (no sweep needed)**</span></span>|<span data-ttu-id="9063a-123">불량 영역 청소(dusty corner sweep)가 필요하지 않은 가비지 수집기에 의해 처리된 초당 행 수입니다(평균).</span><span class="sxs-lookup"><span data-stu-id="9063a-123">The number of rows processed by the garbage collector that will not require a dusty corner sweep (on average), per second.</span></span>|  
|<span data-ttu-id="9063a-124">**Sweep expired rows removed/sec**</span><span class="sxs-lookup"><span data-stu-id="9063a-124">**Sweep expired rows removed/sec**</span></span>|<span data-ttu-id="9063a-125">불량 영역 청소(dusty corner sweeps) 중 제거된 만료된 초당 행 수입니다(평균).</span><span class="sxs-lookup"><span data-stu-id="9063a-125">The number of expired rows removed during dusty corner sweeps (on average), per second.</span></span>|  
|<span data-ttu-id="9063a-126">**Sweep expired rows touched/sec**</span><span class="sxs-lookup"><span data-stu-id="9063a-126">**Sweep expired rows touched/sec**</span></span>|<span data-ttu-id="9063a-127">불량 영역 청소(dusty corner sweeps) 중 처리된 만료된 초당 행 수입니다(평균).</span><span class="sxs-lookup"><span data-stu-id="9063a-127">The number of expired rows touched during dusty corner sweeps (on average), per second.</span></span>|  
|<span data-ttu-id="9063a-128">**Sweep expiring rows touched/sec**</span><span class="sxs-lookup"><span data-stu-id="9063a-128">**Sweep expiring rows touched/sec**</span></span>|<span data-ttu-id="9063a-129">불량 영역 청소(dusty corner sweeps) 중 처리된 만료되는 초당 행 수입니다(평균).</span><span class="sxs-lookup"><span data-stu-id="9063a-129">The number of expiring rows touched during dusty corner sweeps (on average), per second.</span></span>|  
|<span data-ttu-id="9063a-130">**Sweep rows touched/sec**</span><span class="sxs-lookup"><span data-stu-id="9063a-130">**Sweep rows touched/sec**</span></span>|<span data-ttu-id="9063a-131">불량 영역 청소(dusty corner sweeps) 중 처리된 초당 행 수입니다(평균).</span><span class="sxs-lookup"><span data-stu-id="9063a-131">The number of rows touched during dusty corner sweeps (on average), per second.</span></span>|  
|<span data-ttu-id="9063a-132">**Sweep scans started/sec**</span><span class="sxs-lookup"><span data-stu-id="9063a-132">**Sweep scans started/sec**</span></span>|<span data-ttu-id="9063a-133">시작된 초당 불량 영역 청소(dusty corner sweeps) 검사 수입니다(평균).</span><span class="sxs-lookup"><span data-stu-id="9063a-133">The number of dusty corner sweep scans started (on average), per second.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9063a-134">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9063a-134">See Also</span></span>  
 [<span data-ttu-id="9063a-135">XTP &#40;메모리 내 OLTP&#41; 성능 카운터</span><span class="sxs-lookup"><span data-stu-id="9063a-135">XTP &#40;In-Memory OLTP&#41; Performance Counters</span></span>](../../integration-services/performance/performance-counters.md)  
  
  
