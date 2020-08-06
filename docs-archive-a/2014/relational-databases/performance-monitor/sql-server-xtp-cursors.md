---
title: XTP 커서 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
ms.assetid: 84bf4654-3ef7-4d7f-a269-c8bb4ed4acad
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 217a1196717492cb92adb24eaf7c06c8867abc2a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735215"
---
# <a name="xtp-cursors"></a><span data-ttu-id="dda01-102">XTP 커서</span><span class="sxs-lookup"><span data-stu-id="dda01-102">XTP Cursors</span></span>
  <span data-ttu-id="dda01-103">XTP 커서 성능 개체에는 내부 XTP 엔진 커서와 관련된 카운터가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="dda01-103">The XTP Cursors performance object contains counters related to internal XTP engine cursors.</span></span> <span data-ttu-id="dda01-104">커서는 XTP 엔진이 [!INCLUDE[tsql](../../includes/tsql-md.md)] 쿼리를 처리하기 위해 사용하는 하위 수준의 기본 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="dda01-104">Cursors are the low-level building blocks the XTP engine uses to process [!INCLUDE[tsql](../../includes/tsql-md.md)] queries.</span></span> <span data-ttu-id="dda01-105">따라서 사용자는 일반적으로 이를 직접 제어하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="dda01-105">As such, you do not typically have direct control over them.</span></span>  
  
 <span data-ttu-id="dda01-106">이 표에서는 **XTP 커서** 카운터에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="dda01-106">This table describes the **XTP Cursors** counters.</span></span>  
  
|<span data-ttu-id="dda01-107">카운터</span><span class="sxs-lookup"><span data-stu-id="dda01-107">Counter</span></span>|<span data-ttu-id="dda01-108">Description</span><span class="sxs-lookup"><span data-stu-id="dda01-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="dda01-109">**Cursor deletes/sec**</span><span class="sxs-lookup"><span data-stu-id="dda01-109">**Cursor deletes/sec**</span></span>|<span data-ttu-id="dda01-110">초당 커서 삭제 수입니다(평균).</span><span class="sxs-lookup"><span data-stu-id="dda01-110">The number of cursor deletes (on average), per second.</span></span>|  
|<span data-ttu-id="dda01-111">**Cursor inserts/sec**</span><span class="sxs-lookup"><span data-stu-id="dda01-111">**Cursor inserts/sec**</span></span>|<span data-ttu-id="dda01-112">초당 커서 삽입 수입니다(평균).</span><span class="sxs-lookup"><span data-stu-id="dda01-112">The number of cursor inserts (on average), per second.</span></span>|  
|<span data-ttu-id="dda01-113">**Cursor scans started /sec**</span><span class="sxs-lookup"><span data-stu-id="dda01-113">**Cursor scans started /sec**</span></span>|<span data-ttu-id="dda01-114">초당 시작된 커서 검사 수입니다(평균).</span><span class="sxs-lookup"><span data-stu-id="dda01-114">The number of cursor scans started (on average), per second.</span></span>|  
|<span data-ttu-id="dda01-115">**Cursor unique violations/sec**</span><span class="sxs-lookup"><span data-stu-id="dda01-115">**Cursor unique violations/sec**</span></span>|<span data-ttu-id="dda01-116">초당 고유 제약 조건 위반 수입니다(평균).</span><span class="sxs-lookup"><span data-stu-id="dda01-116">The number of unique-constraint violations (on average), per second.</span></span>|  
|<span data-ttu-id="dda01-117">**Cursor updates/sec**</span><span class="sxs-lookup"><span data-stu-id="dda01-117">**Cursor updates/sec**</span></span>|<span data-ttu-id="dda01-118">초당 커서 업데이트 수입니다(평균).</span><span class="sxs-lookup"><span data-stu-id="dda01-118">The number of cursor updates (on average), per second.</span></span>|  
|<span data-ttu-id="dda01-119">**Cursor write   conflicts/sec**</span><span class="sxs-lookup"><span data-stu-id="dda01-119">**Cursor write   conflicts/sec**</span></span>|<span data-ttu-id="dda01-120">동일 행 버전에 대한 초당 쓰기-쓰기 충돌 수입니다(평균).</span><span class="sxs-lookup"><span data-stu-id="dda01-120">The number of write-write conflicts to the same row version (on average), per second.</span></span>|  
|<span data-ttu-id="dda01-121">**Dusty corner scan retries/sec (user-issued)**</span><span class="sxs-lookup"><span data-stu-id="dda01-121">**Dusty corner scan retries/sec (user-issued)**</span></span>|<span data-ttu-id="dda01-122">사용자의 전체 테이블 검사에 의해 실행된 불량 영역 청소(dusty corner sweeps) 중 발생한 초당 검색 재시도 횟수입니다(평균).</span><span class="sxs-lookup"><span data-stu-id="dda01-122">The number of scan retries due to write conflicts during dusty corner sweeps issued by a user's full-table scan (on average), per second.</span></span> <span data-ttu-id="dda01-123">이 카운터는 사용자용이 아닌 매우 낮은 수준의 카운터입니다.</span><span class="sxs-lookup"><span data-stu-id="dda01-123">This is a very low-level counter, not intended for customer use.</span></span>|  
|<span data-ttu-id="dda01-124">**Expired rows removed/sec**</span><span class="sxs-lookup"><span data-stu-id="dda01-124">**Expired rows removed/sec**</span></span>|<span data-ttu-id="dda01-125">커서에 의해 제거된 만료된 초당 행 수입니다(평균).</span><span class="sxs-lookup"><span data-stu-id="dda01-125">The number of expired rows removed by cursors (on average), per second.</span></span>|  
|<span data-ttu-id="dda01-126">**Expired rows touched/sec**</span><span class="sxs-lookup"><span data-stu-id="dda01-126">**Expired rows touched/sec**</span></span>|<span data-ttu-id="dda01-127">커서에 의해 처리된 만료된 초당 행 수입니다(평균).</span><span class="sxs-lookup"><span data-stu-id="dda01-127">The number of expired rows touched by cursors (on average), per second.</span></span>|  
|<span data-ttu-id="dda01-128">**Rows returned/sec**</span><span class="sxs-lookup"><span data-stu-id="dda01-128">**Rows returned/sec**</span></span>|<span data-ttu-id="dda01-129">커서에 의해 반환된 초당 행 수입니다(평균).</span><span class="sxs-lookup"><span data-stu-id="dda01-129">The number of rows returned by cursors (on average), per second.</span></span>|  
|<span data-ttu-id="dda01-130">**Rows touched/sec**</span><span class="sxs-lookup"><span data-stu-id="dda01-130">**Rows touched/sec**</span></span>|<span data-ttu-id="dda01-131">커서에 의해 처리된 초당 행 수입니다(평균).</span><span class="sxs-lookup"><span data-stu-id="dda01-131">The number of rows touched by cursors (on average), per second.</span></span>|  
|<span data-ttu-id="dda01-132">**Tentatively-deleted rows touched/sec**</span><span class="sxs-lookup"><span data-stu-id="dda01-132">**Tentatively-deleted rows touched/sec**</span></span>|<span data-ttu-id="dda01-133">커서에 의해 처리된 만료되는 초당 행 수입니다(평균).</span><span class="sxs-lookup"><span data-stu-id="dda01-133">The number of expiring rows touched by cursors (on average), per second.</span></span> <span data-ttu-id="dda01-134">만료되는 행은 행을 삭제한 트랜잭션이 여전히 활성 상태인 경우의 행을 의미합니다(즉, 아직 커밋되거나 중단되지 않음).</span><span class="sxs-lookup"><span data-stu-id="dda01-134">A row is expiring if the transaction that deleted it is still active (i.e. has not yet committed or aborted.)</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="dda01-135">참고 항목</span><span class="sxs-lookup"><span data-stu-id="dda01-135">See Also</span></span>  
 [<span data-ttu-id="dda01-136">XTP &#40;메모리 내 OLTP&#41; 성능 카운터</span><span class="sxs-lookup"><span data-stu-id="dda01-136">XTP &#40;In-Memory OLTP&#41; Performance Counters</span></span>](../../integration-services/performance/performance-counters.md)  
  
  
