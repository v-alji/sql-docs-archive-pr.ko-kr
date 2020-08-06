---
title: 메모리 사용량 모니터링 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- tuning databases [SQL Server], memory
- monitoring server performance [SQL Server], memory usage
- isolating memory [SQL Server]
- paging rate [SQL Server]
- memory [SQL Server], monitoring usage
- monitoring [SQL Server], memory usage
- low-memory conditions
- database monitoring [SQL Server], memory usage
- available memory [SQL Server]
- page faults [SQL Server]
- monitoring performance [SQL Server], memory usage
- server performance [SQL Server], memory
ms.assetid: 1aee3933-a11c-4b87-91b7-32f5ea38c87f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 1986d9576f9b067cad18f27d4febbf097ed52703
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739741"
---
# <a name="monitor-memory-usage"></a><span data-ttu-id="f8c7b-102">메모리 사용량 모니터링</span><span class="sxs-lookup"><span data-stu-id="f8c7b-102">Monitor Memory Usage</span></span>
  <span data-ttu-id="f8c7b-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 의 인스턴스를 주기적으로 모니터링하여 메모리 사용이 일반적인 범위를 벗어나지 않는지 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f8c7b-103">Monitor an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] periodically to confirm that memory usage is within typical ranges.</span></span>  
  
 <span data-ttu-id="f8c7b-104">메모리 부족 상태를 모니터링하려면 다음 개체 카운터를 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="f8c7b-104">To monitor for a low-memory condition, use the following object counters:</span></span>  
  
-   <span data-ttu-id="f8c7b-105">**메모리: Available Bytes**</span><span class="sxs-lookup"><span data-stu-id="f8c7b-105">**Memory: Available Bytes**</span></span>  
  
-   <span data-ttu-id="f8c7b-106">**메모리: Pages/sec**</span><span class="sxs-lookup"><span data-stu-id="f8c7b-106">**Memory: Pages/sec**</span></span>  
  
 <span data-ttu-id="f8c7b-107">**Available Bytes** 카운터는 현재 프로세스에 사용할 수 있는 메모리의 바이트 수를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="f8c7b-107">The **Available Bytes** counter indicates how many bytes of memory are currently available for use by processes.</span></span> <span data-ttu-id="f8c7b-108">**Pages/sec** 카운터는 하드 페이지 폴트 때문에 디스크에서 가져오거나 작업 집합 내의 디스크 여유 공간에 쓴 페이지 수를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="f8c7b-108">The **Pages/sec** counter indicates the number of pages that either were retrieved from disk due to hard page faults or written to disk to free space in the working set due to page faults.</span></span>  
  
 <span data-ttu-id="f8c7b-109">**Available Bytes** 카운터 값이 작으면 컴퓨터 전체 메모리가 부족하거나 애플리케이션이 메모리를 해제하지 않는다는 의미입니다.</span><span class="sxs-lookup"><span data-stu-id="f8c7b-109">Low values for the **Available Bytes** counter can indicate that there is an overall shortage of memory on the computer or that an application is not releasing memory.</span></span> <span data-ttu-id="f8c7b-110">**Pages/sec** 카운터의 비율이 높으면 페이징이 과도하다는 의미입니다.</span><span class="sxs-lookup"><span data-stu-id="f8c7b-110">A high rate for the **Pages/sec** counter could indicate excessive paging.</span></span> <span data-ttu-id="f8c7b-111">디스크 작업의 원인이 페이징이 아닌지 확인하려면 **Memory: Page Faults/sec** 카운터를 모니터링하세요.</span><span class="sxs-lookup"><span data-stu-id="f8c7b-111">Monitor the **Memory: Page Faults/sec** counter to make sure that the disk activity is not caused by paging.</span></span>  
  
 <span data-ttu-id="f8c7b-112">컴퓨터에 사용 가능한 메모리가 충분하더라도 페이징 및 그로 인한 페이지 폴트 비율은 낮은 것이 일반적입니다.</span><span class="sxs-lookup"><span data-stu-id="f8c7b-112">A low rate of paging (and hence page faults) is typical, even if the computer has plenty of available memory.</span></span> <span data-ttu-id="f8c7b-113">Microsoft Windows VMM(Virtual Memory Manager)은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 및 다른 프로세스의 작업 집합 크기를 줄일 때 이러한 프로세스에서 페이지를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="f8c7b-113">The Microsoft Windows Virtual Memory Manager (VMM) takes pages from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and other processes as it trims the working-set sizes of those processes.</span></span> <span data-ttu-id="f8c7b-114">이 VMM 작업으로 인해 페이지 폴트가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f8c7b-114">This VMM activity tends to cause page faults.</span></span> <span data-ttu-id="f8c7b-115">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]나 다른 프로세스가 과도한 페이징의 원인인지 확인하려면 **Process: Page Faults/sec** 카운터([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 프로세스 인스턴스)를 모니터링하세요.</span><span class="sxs-lookup"><span data-stu-id="f8c7b-115">To determine whether [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] or another process is the cause of excessive paging, monitor the **Process: Page Faults/sec** counter for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] process instance.</span></span>  
  
 <span data-ttu-id="f8c7b-116">과도한 페이징을 해결하는 방법은 Windows 운영 체제 설명서를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f8c7b-116">For more information about resolving excessive paging, see the Windows operating system documentation.</span></span>  
  
## <a name="isolating-memory-used-by-sql-server"></a><span data-ttu-id="f8c7b-117">SQL Server가 사용하는 메모리 격리</span><span class="sxs-lookup"><span data-stu-id="f8c7b-117">Isolating Memory Used by SQL Server</span></span>  
 <span data-ttu-id="f8c7b-118">기본적으로 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 는 사용할 수 있는 시스템 리소스에 따라 메모리 요구 사항을 동적으로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="f8c7b-118">By default, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] changes its memory requirements dynamically, on the basis of available system resources.</span></span> <span data-ttu-id="f8c7b-119">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 는 메모리가 더 필요할 경우 운영 체제를 쿼리하여 실제 여유 메모리가 사용 가능한지 확인하고 사용 가능한 메모리를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f8c7b-119">If [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] needs more memory, it queries the operating system to determine whether free physical memory is available and uses the available memory.</span></span> <span data-ttu-id="f8c7b-120">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서는 현재 할당된 메모리가 필요하지 않은 경우 운영 체제에서 사용할 수 있도록 해당 메모리를 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="f8c7b-120">If [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] does not need the memory currently allocated to it, it releases the memory to the operating system.</span></span> <span data-ttu-id="f8c7b-121">그러나 **minservermemory**및 **maxservermemory** 서버 구성 옵션을 사용하여 메모리를 동적으로 사용하도록 옵션을 재정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f8c7b-121">However, you can override the option to dynamically use memory by using the **minservermemory**, and **maxservermemory** server configuration options.</span></span> <span data-ttu-id="f8c7b-122">자세한 내용은 [서버 메모리 옵션](../../database-engine/configure-windows/server-memory-server-configuration-options.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f8c7b-122">For more information, see [Server Memory Options](../../database-engine/configure-windows/server-memory-server-configuration-options.md).</span></span>  
  
 <span data-ttu-id="f8c7b-123">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 사용하는 메모리의 양을 모니터링하려면 다음 성능 카운터를 검사하세요.</span><span class="sxs-lookup"><span data-stu-id="f8c7b-123">To monitor the amount of memory that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] uses, examine the following performance counters:</span></span>  
  
-   <span data-ttu-id="f8c7b-124">**프로세스: Working Set**</span><span class="sxs-lookup"><span data-stu-id="f8c7b-124">**Process: Working Set**</span></span>  
  
-   <span data-ttu-id="f8c7b-125">**SQL Server: 버퍼 관리자: 버퍼 캐시 적중률**</span><span class="sxs-lookup"><span data-stu-id="f8c7b-125">**SQL Server: Buffer Manager: Buffer Cache Hit Ratio**</span></span>  
  
-   <span data-ttu-id="f8c7b-126">**SQL Server: 버퍼 관리자: Database pages**</span><span class="sxs-lookup"><span data-stu-id="f8c7b-126">**SQL Server: Buffer Manager: Database Pages**</span></span>  
  
-   <span data-ttu-id="f8c7b-127">**SQL Server: 메모리 관리자: 총 서버 메모리(KB)**</span><span class="sxs-lookup"><span data-stu-id="f8c7b-127">**SQL Server: Memory Manager: Total Server Memory (KB)**</span></span>  
  
 <span data-ttu-id="f8c7b-128">**WorkingSet** 카운터는 프로세스에서 사용하는 메모리의 양을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="f8c7b-128">The **WorkingSet** counter shows the amount of memory that is used by a process.</span></span> <span data-ttu-id="f8c7b-129">이 숫자가 계속 **min server memory** 및 **max server memory** 서버 옵션에 설정된 메모리의 양보다 작으면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가 메모리를 너무 많이 사용하도록 구성된 것입니다.</span><span class="sxs-lookup"><span data-stu-id="f8c7b-129">If this number is consistently below the amount of memory that is set by the **min server memory** and **max server memory** server options, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is configured to use too much memory.</span></span>  
  
 <span data-ttu-id="f8c7b-130">**Buffer Cache Hit Ratio** 카운터는 애플리케이션에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="f8c7b-130">The **Buffer Cache Hit Ratio** counter is specific to an application.</span></span> <span data-ttu-id="f8c7b-131">그러나 90% 이상의 비율이 알맞습니다.</span><span class="sxs-lookup"><span data-stu-id="f8c7b-131">However, a rate of 90 percent or higher is desirable.</span></span> <span data-ttu-id="f8c7b-132">이 값이 90%보다 크게 유지될 때까지 메모리를 추가하세요.</span><span class="sxs-lookup"><span data-stu-id="f8c7b-132">Add more memory until the value is consistently greater than 90 percent.</span></span> <span data-ttu-id="f8c7b-133">값이 90%보다 크면 데이터 캐시를 통해 모든 데이터 요청의 90% 이상이 충족된 것입니다.</span><span class="sxs-lookup"><span data-stu-id="f8c7b-133">A value greater than 90 percent indicates that more than 90 percent of all requests for data were satisfied from the data cache.</span></span>  
  
 <span data-ttu-id="f8c7b-134">**TotalServerMemory (KB)** 카운터가 컴퓨터의 실제 메모리 양과 비교하여 계속 높게 나타나면 메모리를 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8c7b-134">If the **TotalServerMemory (KB)** counter is consistently high compared to the amount of physical memory in the computer, it may indicate that more memory is required.</span></span>  
  
## <a name="determining-current-memory-allocation"></a><span data-ttu-id="f8c7b-135">현재 메모리 할당 확인</span><span class="sxs-lookup"><span data-stu-id="f8c7b-135">Determining Current Memory Allocation</span></span>  
 <span data-ttu-id="f8c7b-136">다음 쿼리는 현재 할당된 메모리에 대한 정보를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="f8c7b-136">The following query returns information about currently allocated memory.</span></span>  
  
```  
SELECT  
(physical_memory_in_use_kb/1024) AS Memory_usedby_Sqlserver_MB,  
(locked_page_allocations_kb/1024) AS Locked_pages_used_Sqlserver_MB,  
(total_virtual_address_space_kb/1024) AS Total_VAS_in_MB,  
process_physical_memory_low,  
process_virtual_memory_low  
FROM sys.dm_os_process_memory;  
```  
  
  
