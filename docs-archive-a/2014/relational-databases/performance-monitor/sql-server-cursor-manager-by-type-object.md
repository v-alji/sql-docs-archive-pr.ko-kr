---
title: SQL Server, Cursor Manager by Type 개체 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Cursor Manager by Type object
- SQLServer:Cursor Manager by Type
ms.assetid: d67fbd8a-7554-4a16-96f1-d9ee857a95e3
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 7bee15aa2917f7b8890e6c1d3f26cc0e210208a7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647642"
---
# <a name="sql-server-cursor-manager-by-type-object"></a><span data-ttu-id="8f4fd-102">SQL Server, Cursor Manager by Type 개체</span><span class="sxs-lookup"><span data-stu-id="8f4fd-102">SQL Server, Cursor Manager by Type Object</span></span>
  <span data-ttu-id="8f4fd-103">**SQLServer:Cursor Manager by Type** 개체는 커서 모니터링에 사용되는 카운터를 유형별로 그룹화하여 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="8f4fd-103">The **SQLServer:Cursor Manager by Type** object provides counters to monitor cursors, grouped by type.</span></span>  
  
 <span data-ttu-id="8f4fd-104">다음 표에서는 SQL Server **Cursor Manager by Type** 카운터에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="8f4fd-104">This table describes the SQL Server **Cursor Manager by Type** counters.</span></span>  
  
|<span data-ttu-id="8f4fd-105">Cursor Manager by Type 카운터</span><span class="sxs-lookup"><span data-stu-id="8f4fd-105">Cursor Manager by Type counters</span></span>|<span data-ttu-id="8f4fd-106">Description</span><span class="sxs-lookup"><span data-stu-id="8f4fd-106">Description</span></span>|  
|-------------------------------------|-----------------|  
|<span data-ttu-id="8f4fd-107">**Active cursors**</span><span class="sxs-lookup"><span data-stu-id="8f4fd-107">**Active cursors**</span></span>|<span data-ttu-id="8f4fd-108">활성 커서 수입니다.</span><span class="sxs-lookup"><span data-stu-id="8f4fd-108">Number of active cursors.</span></span>|  
|<span data-ttu-id="8f4fd-109">**Cache Hit Ratio**</span><span class="sxs-lookup"><span data-stu-id="8f4fd-109">**Cache Hit Ratio**</span></span>|<span data-ttu-id="8f4fd-110">캐시 적중 횟수와 조회 간 비율입니다.</span><span class="sxs-lookup"><span data-stu-id="8f4fd-110">Ratio between cache hits and lookups.</span></span>|  
|<span data-ttu-id="8f4fd-111">**Cached Cursor Counts**</span><span class="sxs-lookup"><span data-stu-id="8f4fd-111">**Cached Cursor Counts**</span></span>|<span data-ttu-id="8f4fd-112">캐시에 있는 특정 유형의 커서 수입니다.</span><span class="sxs-lookup"><span data-stu-id="8f4fd-112">Number of cursors of a given type in the cache.</span></span>|  
|<span data-ttu-id="8f4fd-113">**Cursor Cache Use Count/sec**</span><span class="sxs-lookup"><span data-stu-id="8f4fd-113">**Cursor Cache Use Count/sec**</span></span>|<span data-ttu-id="8f4fd-114">각 유형의 캐시된 커서가 사용된 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="8f4fd-114">Times each type of cached cursor has been used.</span></span>|  
|<span data-ttu-id="8f4fd-115">**Cursor memory usage**</span><span class="sxs-lookup"><span data-stu-id="8f4fd-115">**Cursor memory usage**</span></span>|<span data-ttu-id="8f4fd-116">커서가 사용한 메모리 양입니다(KB).</span><span class="sxs-lookup"><span data-stu-id="8f4fd-116">Amount of memory consumed by cursors in kilobytes (KB).</span></span>|  
|<span data-ttu-id="8f4fd-117">**Cursor Requests/sec**</span><span class="sxs-lookup"><span data-stu-id="8f4fd-117">**Cursor Requests/sec**</span></span>|<span data-ttu-id="8f4fd-118">서버에서 받은 SQL 커서 요청 수입니다.</span><span class="sxs-lookup"><span data-stu-id="8f4fd-118">Number of SQL cursor requests received by server.</span></span>|  
|<span data-ttu-id="8f4fd-119">**Cursor worktable usage**</span><span class="sxs-lookup"><span data-stu-id="8f4fd-119">**Cursor worktable usage**</span></span>|<span data-ttu-id="8f4fd-120">커서에 사용되는 작업 테이블 수입니다.</span><span class="sxs-lookup"><span data-stu-id="8f4fd-120">Number of worktables used by cursors.</span></span>|  
|<span data-ttu-id="8f4fd-121">**Number of active cursor plans**</span><span class="sxs-lookup"><span data-stu-id="8f4fd-121">**Number of active cursor plans**</span></span>|<span data-ttu-id="8f4fd-122">커서 계획 수입니다.</span><span class="sxs-lookup"><span data-stu-id="8f4fd-122">Number of cursor plans.</span></span>|  
  
 <span data-ttu-id="8f4fd-123">개체의 각 카운터는 다음 인스턴스를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="8f4fd-123">Each counter in the object contains the following instances:</span></span>  
  
|<span data-ttu-id="8f4fd-124">Cursor Manager 인스턴스</span><span class="sxs-lookup"><span data-stu-id="8f4fd-124">Cursor Manager instance</span></span>|<span data-ttu-id="8f4fd-125">Description</span><span class="sxs-lookup"><span data-stu-id="8f4fd-125">Description</span></span>|  
|-----------------------------|-----------------|  
|<span data-ttu-id="8f4fd-126">**_Total**</span><span class="sxs-lookup"><span data-stu-id="8f4fd-126">**_Total**</span></span>|<span data-ttu-id="8f4fd-127">모든 커서에 대한 정보입니다.</span><span class="sxs-lookup"><span data-stu-id="8f4fd-127">Information for all cursors.</span></span>|  
|<span data-ttu-id="8f4fd-128">**API Cursor**</span><span class="sxs-lookup"><span data-stu-id="8f4fd-128">**API Cursor**</span></span>|<span data-ttu-id="8f4fd-129">API 커서 정보만 해당됩니다.</span><span class="sxs-lookup"><span data-stu-id="8f4fd-129">Only the API cursor information.</span></span>|  
|<span data-ttu-id="8f4fd-130">**TSQL Global Cursor**</span><span class="sxs-lookup"><span data-stu-id="8f4fd-130">**TSQL Global Cursor**</span></span>|<span data-ttu-id="8f4fd-131">[!INCLUDE[tsql](../../includes/tsql-md.md)] 전역 커서 정보만 해당됩니다.</span><span class="sxs-lookup"><span data-stu-id="8f4fd-131">Only the [!INCLUDE[tsql](../../includes/tsql-md.md)] global cursor information.</span></span>|  
|<span data-ttu-id="8f4fd-132">**TSQL Local Cursor**</span><span class="sxs-lookup"><span data-stu-id="8f4fd-132">**TSQL Local Cursor**</span></span>|<span data-ttu-id="8f4fd-133">[!INCLUDE[tsql](../../includes/tsql-md.md)] 로컬 커서 정보만 해당됩니다.</span><span class="sxs-lookup"><span data-stu-id="8f4fd-133">Only the [!INCLUDE[tsql](../../includes/tsql-md.md)] local cursor information.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8f4fd-134">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8f4fd-134">See Also</span></span>  
 [<span data-ttu-id="8f4fd-135">리소스 사용 모니터링&#40;시스템 모니터&#41;</span><span class="sxs-lookup"><span data-stu-id="8f4fd-135">Monitor Resource Usage &#40;System Monitor&#41;</span></span>](monitor-resource-usage-system-monitor.md)  
  
  
