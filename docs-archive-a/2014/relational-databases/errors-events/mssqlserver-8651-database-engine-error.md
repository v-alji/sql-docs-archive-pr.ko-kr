---
title: MSSQLSERVER_8651 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 8651 (Database Engine error)
ms.assetid: 4cc3498d-5449-4c4e-b1f9-3271831c725a
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 43a385350a05edee3759ab83d318e365f5b4f3e4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730696"
---
# <a name="mssqlserver_8651"></a><span data-ttu-id="843f7-102">MSSQLSERVER_8651</span><span class="sxs-lookup"><span data-stu-id="843f7-102">MSSQLSERVER_8651</span></span>
    
## <a name="details"></a><span data-ttu-id="843f7-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="843f7-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="843f7-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="843f7-104">Product Name</span></span>|<span data-ttu-id="843f7-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="843f7-105">SQL Server</span></span>|  
|<span data-ttu-id="843f7-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="843f7-106">Event ID</span></span>|<span data-ttu-id="843f7-107">8651</span><span class="sxs-lookup"><span data-stu-id="843f7-107">8651</span></span>|  
|<span data-ttu-id="843f7-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="843f7-108">Event Source</span></span>|<span data-ttu-id="843f7-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="843f7-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="843f7-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="843f7-110">Component</span></span>|<span data-ttu-id="843f7-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="843f7-111">SQLEngine</span></span>|  
|<span data-ttu-id="843f7-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="843f7-112">Symbolic Name</span></span>|<span data-ttu-id="843f7-113">MEMGRANT_ERR</span><span class="sxs-lookup"><span data-stu-id="843f7-113">MEMGRANT_ERR</span></span>|  
|<span data-ttu-id="843f7-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="843f7-114">Message Text</span></span>|<span data-ttu-id="843f7-115">최소 쿼리 메모리를 사용할 수 없어서 요청한 작업을 수행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="843f7-115">Could not perform the requested operation because the minimum query memory is not available.</span></span> <span data-ttu-id="843f7-116">'쿼리 당 최소 메모리' 서버 구성 옵션의 구성 값을 줄이십시오.</span><span class="sxs-lookup"><span data-stu-id="843f7-116">Decrease the configured value for the 'min memory per query' server configuration option.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="843f7-117">설명</span><span class="sxs-lookup"><span data-stu-id="843f7-117">Explanation</span></span>  
 <span data-ttu-id="843f7-118">다른 프로세스에서 서버 메모리를 사용하고 있어 서버의 메모리가 부족합니다.</span><span class="sxs-lookup"><span data-stu-id="843f7-118">Other processes are consuming server memory (exerting memory pressure in the server).</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="843f7-119">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="843f7-119">User Action</span></span>  
 <span data-ttu-id="843f7-120">'쿼리 당 최소 메모리' 서버 구성 옵션의 구성 값을 줄이거나 서버에 대한 쿼리 로드를 줄이십시오.</span><span class="sxs-lookup"><span data-stu-id="843f7-120">Either decrease the configured value for the min memory per query' server configuration option or reduce the query load to the server.</span></span>  
  
 <span data-ttu-id="843f7-121">다음 목록은 메모리 오류 문제를 해결하는 데 도움이 되는 일반적인 단계를 간략히 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="843f7-121">The following list outlines general steps that will help in troubleshooting memory errors:</span></span>  
  
1.  <span data-ttu-id="843f7-122">다른 애플리케이션 또는 서비스가 현재 서버의 메모리를 사용 중인지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="843f7-122">Verify whether other applications or services are consuming memory on this server.</span></span> <span data-ttu-id="843f7-123">중요도가 낮은 애플리케이션이나 서비스에서 메모리를 덜 사용하도록 다시 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="843f7-123">Reconfigure less critical applications or services to consume less memory.</span></span>  
  
2.  <span data-ttu-id="843f7-124">**SQL Server: Buffer Manager**, **SQL Server: Memory Manager**에 대한 성능 모니터 카운터 수집을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="843f7-124">Start collecting performance monitor counters for **SQL Server: Buffer Manager**, **SQL Server: Memory Manager**.</span></span>  
  
3.  <span data-ttu-id="843f7-125">다음 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 메모리 구성 매개 변수를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="843f7-125">Check the following [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] memory configuration parameters:</span></span>  
  
    -   <span data-ttu-id="843f7-126">**max server memory**</span><span class="sxs-lookup"><span data-stu-id="843f7-126">**max server memory**</span></span>  
  
    -   <span data-ttu-id="843f7-127">**min server memory**</span><span class="sxs-lookup"><span data-stu-id="843f7-127">**min server memory**</span></span>  
  
    -   <span data-ttu-id="843f7-128">**min memory per query**</span><span class="sxs-lookup"><span data-stu-id="843f7-128">**min memory per query**</span></span>  
  
     <span data-ttu-id="843f7-129">비정상적인 설정이 있는지 확인하고</span><span class="sxs-lookup"><span data-stu-id="843f7-129">Notice unusual settings.</span></span> <span data-ttu-id="843f7-130">필요할 경우 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="843f7-130">Correct them as necessary.</span></span> <span data-ttu-id="843f7-131">기본 설정은 SQL Server 온라인 설명서의 "서버 구성 옵션 설정"을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="843f7-131">Default settings are listed in "Setting Server Configuration Options" in SQL Server Books Online.</span></span>  
  
4.  <span data-ttu-id="843f7-132">동시 세션 및 현재 실행 중인 쿼리 수와 같은 작업을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="843f7-132">Check the workload (for example, number of concurrent sessions, currently executing queries).</span></span>  
  
 <span data-ttu-id="843f7-133">다음 동작으로 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 사용할 수 있는 메모리를 늘릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="843f7-133">The following actions may make more memory available to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="843f7-134">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 외에 다른 애플리케이션이 리소스를 사용 중인 경우 이 애플리케이션을 중지하거나 별도의 서버에서 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="843f7-134">If applications besides [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] are consuming resources, try stopping running these applications or consider running them on a separate server.</span></span> <span data-ttu-id="843f7-135">이렇게 하면 외부 메모리 가중을 없앨 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="843f7-135">This will remove external memory pressure.</span></span>  
  
-   <span data-ttu-id="843f7-136">**max server memory**를 구성한 경우 설정값을 늘립니다.</span><span class="sxs-lookup"><span data-stu-id="843f7-136">If you have configured **max server memory,** increase its setting.</span></span>  
  
 <span data-ttu-id="843f7-137">다음 DBCC 명령을 실행하여 몇 가지 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 메모리 캐시를 비웁니다.</span><span class="sxs-lookup"><span data-stu-id="843f7-137">Run the following DBCC commands to free several [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] memory caches.</span></span>  
  
-   <span data-ttu-id="843f7-138">DBCC FREESYSTEMCACHE</span><span class="sxs-lookup"><span data-stu-id="843f7-138">DBCC FREESYSTEMCACHE</span></span>  
  
-   <span data-ttu-id="843f7-139">DBCC FREESESSIONCACHE</span><span class="sxs-lookup"><span data-stu-id="843f7-139">DBCC FREESESSIONCACHE</span></span>  
  
-   <span data-ttu-id="843f7-140">DBCC FREEPROCCACHE</span><span class="sxs-lookup"><span data-stu-id="843f7-140">DBCC FREEPROCCACHE</span></span>  
  
 <span data-ttu-id="843f7-141">문제가 지속되면 추가적인 조사를 수행하고 작업을 줄여야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="843f7-141">If the problem continues, you will need to investigate further and possibly reduce workload.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="843f7-142">참고 항목</span><span class="sxs-lookup"><span data-stu-id="843f7-142">See Also</span></span>  
 <span data-ttu-id="843f7-143">[DBCC FREESYSTEMCACHE &#40;Transact-sql&#41;](/sql/t-sql/database-console-commands/dbcc-freesystemcache-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="843f7-143">[DBCC FREESYSTEMCACHE &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-freesystemcache-transact-sql) </span></span>  
 <span data-ttu-id="843f7-144">[DBCC FREESESSIONCACHE &#40;Transact-sql&#41;](/sql/t-sql/database-console-commands/dbcc-freesessioncache-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="843f7-144">[DBCC FREESESSIONCACHE &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-freesessioncache-transact-sql) </span></span>  
 <span data-ttu-id="843f7-145">[DBCC FREEPROCCACHE &#40;Transact-sql&#41;](/sql/t-sql/database-console-commands/dbcc-freeproccache-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="843f7-145">[DBCC FREEPROCCACHE &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-freeproccache-transact-sql) </span></span>  
 <span data-ttu-id="843f7-146">[서버 구성 옵션&#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="843f7-146">[Server Configuration Options &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md) </span></span>  
 <span data-ttu-id="843f7-147">[SQL Server, Buffer Manager 개체](../performance-monitor/sql-server-buffer-manager-object.md) </span><span class="sxs-lookup"><span data-stu-id="843f7-147">[SQL Server, Buffer Manager Object](../performance-monitor/sql-server-buffer-manager-object.md) </span></span>  
 [<span data-ttu-id="843f7-148">SQL Server, Memory Manager 개체</span><span class="sxs-lookup"><span data-stu-id="843f7-148">SQL Server, Memory Manager Object</span></span>](../performance-monitor/sql-server-memory-manager-object.md)  
  
  
