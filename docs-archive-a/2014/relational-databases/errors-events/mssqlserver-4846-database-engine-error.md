---
title: MSSQLSERVER_4846 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 4846 (Database Engine error)
ms.assetid: a455e809-1883-4c7d-b3e3-835ee5bfe258
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 923137645aae72476fb4b2ae33f0cbbf3e81c2a3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730703"
---
# <a name="mssqlserver_4846"></a><span data-ttu-id="f239f-102">MSSQLSERVER_4846</span><span class="sxs-lookup"><span data-stu-id="f239f-102">MSSQLSERVER_4846</span></span>
    
## <a name="details"></a><span data-ttu-id="f239f-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="f239f-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f239f-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="f239f-104">Product Name</span></span>|<span data-ttu-id="f239f-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="f239f-105">SQL Server</span></span>|  
|<span data-ttu-id="f239f-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="f239f-106">Event ID</span></span>|<span data-ttu-id="f239f-107">4846</span><span class="sxs-lookup"><span data-stu-id="f239f-107">4846</span></span>|  
|<span data-ttu-id="f239f-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="f239f-108">Event Source</span></span>|<span data-ttu-id="f239f-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="f239f-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="f239f-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="f239f-110">Component</span></span>|<span data-ttu-id="f239f-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="f239f-111">SQLEngine</span></span>|  
|<span data-ttu-id="f239f-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="f239f-112">Symbolic Name</span></span>|<span data-ttu-id="f239f-113">BULKPROV_MEMORY</span><span class="sxs-lookup"><span data-stu-id="f239f-113">BULKPROV_MEMORY</span></span>|  
|<span data-ttu-id="f239f-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="f239f-114">Message Text</span></span>|<span data-ttu-id="f239f-115">대량 데이터 공급자가 메모리를 할당하지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="f239f-115">The bulk data provider failed to allocate memory.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="f239f-116">설명</span><span class="sxs-lookup"><span data-stu-id="f239f-116">Explanation</span></span>  
 <span data-ttu-id="f239f-117">메모리 할당이 실패했습니다.</span><span class="sxs-lookup"><span data-stu-id="f239f-117">Memory allocation failed.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="f239f-118">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="f239f-118">User Action</span></span>  
 <span data-ttu-id="f239f-119">메모리 오류 문제를 해결하려면 다음과 같은 일반적인 단계를 따르십시오.</span><span class="sxs-lookup"><span data-stu-id="f239f-119">Follow these general steps to troubleshoot memory errors:</span></span>  
  
1.  <span data-ttu-id="f239f-120">다른 애플리케이션 또는 서비스가 현재 서버의 메모리를 사용 중인지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="f239f-120">Verify whether other applications or services are consuming memory on this server.</span></span> <span data-ttu-id="f239f-121">중요도가 낮은 애플리케이션이나 서비스에서 메모리를 덜 사용하도록 다시 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="f239f-121">Reconfigure less critical applications or services to consume less memory.</span></span>  
  
2.  <span data-ttu-id="f239f-122">**SQL Server: Buffer Manager**, **SQL Server: Memory Manager**에 대한 성능 모니터 카운터 수집을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="f239f-122">Start collecting performance monitor counters for **SQL Server: Buffer Manager**, **SQL Server: Memory Manager**.</span></span>  
  
3.  <span data-ttu-id="f239f-123">다음 SQL Server 메모리 구성 매개 변수를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="f239f-123">Check the following SQL Server memory configuration parameters:</span></span>  
  
    -   <span data-ttu-id="f239f-124">**max server memory**</span><span class="sxs-lookup"><span data-stu-id="f239f-124">**max server memory**</span></span>  
  
    -   <span data-ttu-id="f239f-125">**min server memory**</span><span class="sxs-lookup"><span data-stu-id="f239f-125">**min server memory**</span></span>  
  
    -   <span data-ttu-id="f239f-126">**min memory per query**</span><span class="sxs-lookup"><span data-stu-id="f239f-126">**min memory per query**</span></span>  
  
     <span data-ttu-id="f239f-127">비정상적인 설정이 있는지 확인하고</span><span class="sxs-lookup"><span data-stu-id="f239f-127">Notice any unusual settings.</span></span> <span data-ttu-id="f239f-128">필요할 경우 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="f239f-128">Correct them as necessary.</span></span> <span data-ttu-id="f239f-129">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]의 메모리 요구 사항을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="f239f-129">Account for memory requirements for [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="f239f-130">기본 설정은 SQL Server 온라인 설명서의 "서버 구성 옵션 설정"을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="f239f-130">Default settings are listed in "Setting Server Configuration Options" in SQL Server Books Online.</span></span>  
  
4.  <span data-ttu-id="f239f-131">DBCC MEMORYSTATUS 출력 결과를 확인하고 이러한 오류 메시지가 표시될 때 이 값이 어떻게 변경되는지 관찰합니다.</span><span class="sxs-lookup"><span data-stu-id="f239f-131">Observe DBCC MEMORYSTATUS output and the way it changes when you see these error messages.</span></span>  
  
5.  <span data-ttu-id="f239f-132">동시 세션 및 현재 실행 중인 쿼리 수와 같은 작업을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="f239f-132">Check the workload (for example, number of concurrent sessions, currently executing queries).</span></span>  
  
 <span data-ttu-id="f239f-133">다음 동작으로 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 사용할 수 있는 메모리를 늘릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f239f-133">The following actions may make more memory available to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="f239f-134">SQL Server 외에 다른 애플리케이션이 리소스를 사용 중인 경우 이 애플리케이션을 중지하거나 별도의 서버에서 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="f239f-134">If applications besides SQL Server are consuming resources, try stopping running these applications or consider running them on a separate server.</span></span> <span data-ttu-id="f239f-135">이렇게 하면 외부 메모리 가중을 없앨 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f239f-135">This will remove external memory pressure.</span></span>  
  
-   <span data-ttu-id="f239f-136">**max server memory**를 구성한 경우 설정값을 늘립니다.</span><span class="sxs-lookup"><span data-stu-id="f239f-136">If you have configured **max server memory,** increase its setting.</span></span>  
  
 <span data-ttu-id="f239f-137">다음 DBCC 명령을 실행하여 몇 가지 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 메모리 캐시를 비웁니다.</span><span class="sxs-lookup"><span data-stu-id="f239f-137">Run the following DBCC commands to free several [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] memory caches.</span></span>  
  
-   <span data-ttu-id="f239f-138">DBCC FREESYSTEMCACHE</span><span class="sxs-lookup"><span data-stu-id="f239f-138">DBCC FREESYSTEMCACHE</span></span>  
  
-   <span data-ttu-id="f239f-139">DBCC FREESESSIONCACHE</span><span class="sxs-lookup"><span data-stu-id="f239f-139">DBCC FREESESSIONCACHE</span></span>  
  
-   <span data-ttu-id="f239f-140">DBCC FREEPROCCACHE</span><span class="sxs-lookup"><span data-stu-id="f239f-140">DBCC FREEPROCCACHE</span></span>  
  
 <span data-ttu-id="f239f-141">문제가 지속되면 추가적인 조사를 수행하고 작업을 줄여야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f239f-141">If the problem continues, you will need to investigate further and possibly reduce workload.</span></span>  
  
  
