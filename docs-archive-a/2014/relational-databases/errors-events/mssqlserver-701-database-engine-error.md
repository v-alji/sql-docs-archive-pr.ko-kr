---
title: MSSQLSERVER_701 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 701 (Database Engine error)
ms.assetid: 3b975000-63a1-43c2-a40f-89d0a8a36bef
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 542535223d3e394c72079092411add143de61545
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649079"
---
# <a name="mssqlserver_701"></a><span data-ttu-id="38943-102">MSSQLSERVER_701</span><span class="sxs-lookup"><span data-stu-id="38943-102">MSSQLSERVER_701</span></span>
    
## <a name="details"></a><span data-ttu-id="38943-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="38943-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="38943-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="38943-104">Product Name</span></span>|<span data-ttu-id="38943-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="38943-105">SQL Server</span></span>|  
|<span data-ttu-id="38943-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="38943-106">Event ID</span></span>|<span data-ttu-id="38943-107">701</span><span class="sxs-lookup"><span data-stu-id="38943-107">701</span></span>|  
|<span data-ttu-id="38943-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="38943-108">Event Source</span></span>|<span data-ttu-id="38943-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="38943-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="38943-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="38943-110">Component</span></span>|<span data-ttu-id="38943-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="38943-111">SQLEngine</span></span>|  
|<span data-ttu-id="38943-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="38943-112">Symbolic Name</span></span>|<span data-ttu-id="38943-113">NOSYSMEM</span><span class="sxs-lookup"><span data-stu-id="38943-113">NOSYSMEM</span></span>|  
|<span data-ttu-id="38943-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="38943-114">Message Text</span></span>|<span data-ttu-id="38943-115">시스템 메모리가 부족하여 이 쿼리를 실행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="38943-115">There is insufficient system memory to run this query.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="38943-116">설명</span><span class="sxs-lookup"><span data-stu-id="38943-116">Explanation</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="38943-117">에서 쿼리를 실행할 충분한 메모리를 할당하지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="38943-117">has failed to allocate sufficient memory to run the query.</span></span> <span data-ttu-id="38943-118">운영 체제 설정, 실제 메모리 가용성, 현재 워크로드의 메모리 제한을 비롯한 다양한 이유로 이 오류가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38943-118">This can be caused by a variety of reasons including operating system settings, physical memory availability, or memory limits on the current workload.</span></span> <span data-ttu-id="38943-119">대부분의 경우 실패한 트랜잭션은 이 오류의 원인이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="38943-119">In most cases, the transaction that failed is not the cause of this error.</span></span>  
  
 <span data-ttu-id="38943-120">서버에 충분한 메모리가 없으므로 DBCC 문 같은 진단 쿼리는 실패할 가능성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38943-120">Diagnostic queries, such as DBCC statements, may fail because server the does not have sufficient memory.</span></span>  
  
 <span data-ttu-id="38943-121">리소스 풀 'default'에서 메모리 리소스가 쿼리를 실행하기를 기다리는 동안 시간이 초과되었습니다.</span><span class="sxs-lookup"><span data-stu-id="38943-121">A timeout occurred while waiting for memory resources to execute the query in the resource pool 'default'.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="38943-122">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="38943-122">User Action</span></span>  
 <span data-ttu-id="38943-123">리소스 관리자를 사용하지 않는 경우 전체 서버 상태 및 부하를 확인하고 리소스 풀 또는 작업 그룹 설정을 확인하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="38943-123">If you are not using Resource Governor, we recommend that you verify the overall server state and load, or check the resource pool or workload group settings.</span></span>  
  
 <span data-ttu-id="38943-124">다음 목록은 메모리 오류 문제를 해결하는 데 도움이 되는 일반적인 단계를 간략히 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="38943-124">The following list outlines general steps that will help in troubleshooting memory errors:</span></span>  
  
1.  <span data-ttu-id="38943-125">다른 애플리케이션 또는 서비스가 현재 서버의 메모리를 사용 중인지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="38943-125">Verify whether other applications or services are consuming memory on this server.</span></span> <span data-ttu-id="38943-126">중요도가 낮은 애플리케이션이나 서비스에서 메모리를 덜 사용하도록 다시 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="38943-126">Reconfigure less critical applications or services to consume less memory.</span></span>  
  
2.  <span data-ttu-id="38943-127">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **: Buffer Manager**, **SQL Server: Memory Manager**에 대한 성능 모니터 카운터 수집을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="38943-127">Start collecting performance monitor counters for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**: Buffer Manager**, **SQL Server: Memory Manager**.</span></span>  
  
3.  <span data-ttu-id="38943-128">다음 SQL Server 메모리 구성 매개 변수를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="38943-128">Check the following SQL Server memory configuration parameters:</span></span>  
  
    -   <span data-ttu-id="38943-129">**max server memory**</span><span class="sxs-lookup"><span data-stu-id="38943-129">**max server memory**</span></span>  
  
    -   <span data-ttu-id="38943-130">**min server memory**</span><span class="sxs-lookup"><span data-stu-id="38943-130">**min server memory**</span></span>  
  
    -   <span data-ttu-id="38943-131">**min memory per query**</span><span class="sxs-lookup"><span data-stu-id="38943-131">**min memory per query**</span></span>  
  
     <span data-ttu-id="38943-132">비정상적인 설정이 있는지 확인하고</span><span class="sxs-lookup"><span data-stu-id="38943-132">Notice unusual settings.</span></span> <span data-ttu-id="38943-133">필요할 경우 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="38943-133">Correct them as necessary.</span></span> <span data-ttu-id="38943-134">늘어난 메모리 요구 사항을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="38943-134">Account for increased memory requirements.</span></span> <span data-ttu-id="38943-135">기본 설정은 SQL Server 온라인 설명서의 "서버 구성 옵션 설정"을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="38943-135">Default settings are listed in "Setting Server Configuration Options" in SQL Server Books Online.</span></span>  
  
4.  <span data-ttu-id="38943-136">DBCC MEMORYSTATUS 출력 결과를 확인하고 이러한 오류 메시지가 표시될 때 이 값이 어떻게 변경되는지 관찰합니다.</span><span class="sxs-lookup"><span data-stu-id="38943-136">Observe DBCC MEMORYSTATUS output and the way it changes when you see these error messages.</span></span>  
  
5.  <span data-ttu-id="38943-137">동시 세션 및 현재 실행 중인 쿼리 수와 같은 작업을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="38943-137">Check the workload (for example, number of concurrent sessions, currently executing queries).</span></span>  
  
 <span data-ttu-id="38943-138">다음 동작으로 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 사용할 수 있는 메모리를 늘릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38943-138">The following actions may make more memory available to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="38943-139">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 외에 다른 애플리케이션이 리소스를 사용 중인 경우 이 애플리케이션을 중지하거나 별도의 서버에서 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="38943-139">If applications besides [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] are consuming resources, try stopping running these applications or consider running them on a separate server.</span></span> <span data-ttu-id="38943-140">이렇게 하면 외부 메모리 가중을 없앨 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38943-140">This will remove external memory pressure.</span></span>  
  
-   <span data-ttu-id="38943-141">**max server memory**를 구성한 경우 설정값을 늘립니다.</span><span class="sxs-lookup"><span data-stu-id="38943-141">If you have configured **max server memory,** increase its setting.</span></span>  
  
 <span data-ttu-id="38943-142">다음 DBCC 명령을 실행하여 몇 가지 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 메모리 캐시를 비웁니다.</span><span class="sxs-lookup"><span data-stu-id="38943-142">Run the following DBCC commands to free several [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] memory caches.</span></span>  
  
-   <span data-ttu-id="38943-143">DBCC FREESYSTEMCACHE</span><span class="sxs-lookup"><span data-stu-id="38943-143">DBCC FREESYSTEMCACHE</span></span>  
  
-   <span data-ttu-id="38943-144">DBCC FREESESSIONCACHE</span><span class="sxs-lookup"><span data-stu-id="38943-144">DBCC FREESESSIONCACHE</span></span>  
  
-   <span data-ttu-id="38943-145">DBCC FREEPROCCACHE</span><span class="sxs-lookup"><span data-stu-id="38943-145">DBCC FREEPROCCACHE</span></span>  
  
 <span data-ttu-id="38943-146">문제가 지속되면 추가적인 조사를 수행하고 작업을 줄여야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38943-146">If the problem continues, you will need to investigate further and possibly reduce workload.</span></span>  
  
  
