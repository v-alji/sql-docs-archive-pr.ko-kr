---
title: CPU Threshold Exceeded 이벤트 클래스 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- CPU Threshold Exceeded Event Class
ms.assetid: eb106f7d-baa3-4a2b-96b2-f9fe0844057d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 07b51e1a6f08f48c601b00d2dcb67bc6d09006f6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647049"
---
# <a name="cpu-threshold-exceeded-event-class"></a><span data-ttu-id="2cc4a-102">CPU Threshold Exceeded 이벤트 클래스</span><span class="sxs-lookup"><span data-stu-id="2cc4a-102">CPU Threshold Exceeded Event Class</span></span>
  <span data-ttu-id="2cc4a-103">CPU Threshold Exceeded 이벤트 클래스는 리소스 관리자가 REQUEST_MAX_CPU_TIME_SEC에 지정된 CPU 임계값을 초과하는 쿼리를 감지했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="2cc4a-103">The CPU Threshold Exceeded event class indicates that Resource Governor detects a query that exceeds the CPU threshold specified for REQUEST_MAX_CPU_TIME_SEC.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2cc4a-104">이 이벤트의 검색 간격은 5초입니다.</span><span class="sxs-lookup"><span data-stu-id="2cc4a-104">The detection interval for this event is five seconds.</span></span> <span data-ttu-id="2cc4a-105">이는 최소 5초 단위로 쿼리가 지정된 제한을 초과할 경우 이벤트가 생성되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="2cc4a-105">It is guaranteed that an event will be generated if a query exceeds the specified limit by at least five seconds.</span></span> <span data-ttu-id="2cc4a-106">그러나 쿼리가 5초 이내로 지정된 임계값을 초과하는 경우에는 쿼리 타이밍과 마지막 검색 스윕 시간에 따라 이러한 쿼리가 검색되지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2cc4a-106">However, if a query exceeds the specified threshold by less than five seconds, its detection might be missed depending on the timing of the query and the time of last detection sweep.</span></span>  
  
## <a name="cpu-threshold-exceeded-data-columns"></a><span data-ttu-id="2cc4a-107">CPU Threshold Exceeded 데이터 열</span><span class="sxs-lookup"><span data-stu-id="2cc4a-107">CPU Threshold Exceeded Data Columns</span></span>  
  
|<span data-ttu-id="2cc4a-108">데이터 열 이름</span><span class="sxs-lookup"><span data-stu-id="2cc4a-108">Data column name</span></span>|<span data-ttu-id="2cc4a-109">데이터 형식</span><span class="sxs-lookup"><span data-stu-id="2cc4a-109">Data type</span></span>|<span data-ttu-id="2cc4a-110">Description</span><span class="sxs-lookup"><span data-stu-id="2cc4a-110">Description</span></span>|<span data-ttu-id="2cc4a-111">열 ID</span><span class="sxs-lookup"><span data-stu-id="2cc4a-111">Column ID</span></span>|<span data-ttu-id="2cc4a-112">필터 가능</span><span class="sxs-lookup"><span data-stu-id="2cc4a-112">Filterable</span></span>|  
|----------------------|---------------|-----------------|---------------|----------------|  
|<span data-ttu-id="2cc4a-113">CPU</span><span class="sxs-lookup"><span data-stu-id="2cc4a-113">CPU</span></span>|`int`|<span data-ttu-id="2cc4a-114">CPU 사용량(밀리초)입니다.</span><span class="sxs-lookup"><span data-stu-id="2cc4a-114">CPU usage in milliseconds.</span></span>|<span data-ttu-id="2cc4a-115">18</span><span class="sxs-lookup"><span data-stu-id="2cc4a-115">18</span></span>|<span data-ttu-id="2cc4a-116">예</span><span class="sxs-lookup"><span data-stu-id="2cc4a-116">Yes</span></span>|  
|<span data-ttu-id="2cc4a-117">EventClass</span><span class="sxs-lookup"><span data-stu-id="2cc4a-117">EventClass</span></span>|`int`|<span data-ttu-id="2cc4a-118">214</span><span class="sxs-lookup"><span data-stu-id="2cc4a-118">214</span></span>|<span data-ttu-id="2cc4a-119">27</span><span class="sxs-lookup"><span data-stu-id="2cc4a-119">27</span></span>|<span data-ttu-id="2cc4a-120">예</span><span class="sxs-lookup"><span data-stu-id="2cc4a-120">No</span></span>|  
|<span data-ttu-id="2cc4a-121">EventSubClass</span><span class="sxs-lookup"><span data-stu-id="2cc4a-121">EventSubClass</span></span>|`int`|<span data-ttu-id="2cc4a-122">CPU 제한 위반입니다.</span><span class="sxs-lookup"><span data-stu-id="2cc4a-122">CPU limit violation.</span></span>|<span data-ttu-id="2cc4a-123">21</span><span class="sxs-lookup"><span data-stu-id="2cc4a-123">21</span></span>|<span data-ttu-id="2cc4a-124">예</span><span class="sxs-lookup"><span data-stu-id="2cc4a-124">Yes</span></span>|  
|<span data-ttu-id="2cc4a-125">GroupID</span><span class="sxs-lookup"><span data-stu-id="2cc4a-125">GroupID</span></span>|`int`|<span data-ttu-id="2cc4a-126">위반이 발생한 그룹 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="2cc4a-126">Group ID where the violation occurred.</span></span>|<span data-ttu-id="2cc4a-127">66</span><span class="sxs-lookup"><span data-stu-id="2cc4a-127">66</span></span>|<span data-ttu-id="2cc4a-128">예</span><span class="sxs-lookup"><span data-stu-id="2cc4a-128">Yes</span></span>|  
|<span data-ttu-id="2cc4a-129">OwnerID</span><span class="sxs-lookup"><span data-stu-id="2cc4a-129">OwnerID</span></span>|`int`|<span data-ttu-id="2cc4a-130">위반을 발생시킨 프로세스의 SPID입니다.</span><span class="sxs-lookup"><span data-stu-id="2cc4a-130">SPID of the process that caused the violation.</span></span>|<span data-ttu-id="2cc4a-131">58</span><span class="sxs-lookup"><span data-stu-id="2cc4a-131">58</span></span>|<span data-ttu-id="2cc4a-132">yes</span><span class="sxs-lookup"><span data-stu-id="2cc4a-132">Yes</span></span>|  
|<span data-ttu-id="2cc4a-133">SPID</span><span class="sxs-lookup"><span data-stu-id="2cc4a-133">SPID</span></span>|`int`|<span data-ttu-id="2cc4a-134">이 이벤트를 발생시키는 서버 프로세스의 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="2cc4a-134">ID of the server process that fires this event.</span></span><br /><br /> <span data-ttu-id="2cc4a-135">참고: 이 ID는 시스템 스레드가 CPU 사용량의 유효성을 백그라운드 태스크로 검사할 경우 실제 사용자 SPID와 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2cc4a-135">Note: This can differ from the actual user SPID if a system thread validates CPU usage as a background task.</span></span>|<span data-ttu-id="2cc4a-136">12</span><span class="sxs-lookup"><span data-stu-id="2cc4a-136">12</span></span>|<span data-ttu-id="2cc4a-137">yes</span><span class="sxs-lookup"><span data-stu-id="2cc4a-137">Yes</span></span>|  
|<span data-ttu-id="2cc4a-138">StartTime</span><span class="sxs-lookup"><span data-stu-id="2cc4a-138">StartTime</span></span>|`datetime`|<span data-ttu-id="2cc4a-139">이 이벤트가 발생한 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="2cc4a-139">The time when this event fired.</span></span>|<span data-ttu-id="2cc4a-140">14</span><span class="sxs-lookup"><span data-stu-id="2cc4a-140">14</span></span>|<span data-ttu-id="2cc4a-141">예</span><span class="sxs-lookup"><span data-stu-id="2cc4a-141">Yes</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2cc4a-142">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2cc4a-142">See Also</span></span>  
 [<span data-ttu-id="2cc4a-143">sp_trace_setevent&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="2cc4a-143">sp_trace_setevent &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)  
  
  
