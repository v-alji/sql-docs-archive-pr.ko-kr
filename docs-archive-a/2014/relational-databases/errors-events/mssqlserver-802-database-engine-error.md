---
title: MSSQLSERVER_802 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 802 (Database Engine error)
ms.assetid: 5892ed24-4dcb-4bf9-a8a4-a7ca898832d5
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 9edcdda1410d7651f7c7531ef98c64c85741f15a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661679"
---
# <a name="mssqlserver_802"></a><span data-ttu-id="3b398-102">MSSQLSERVER_802</span><span class="sxs-lookup"><span data-stu-id="3b398-102">MSSQLSERVER_802</span></span>
    
## <a name="details"></a><span data-ttu-id="3b398-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="3b398-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3b398-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="3b398-104">Product Name</span></span>|<span data-ttu-id="3b398-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="3b398-105">SQL Server</span></span>|  
|<span data-ttu-id="3b398-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="3b398-106">Event ID</span></span>|<span data-ttu-id="3b398-107">802</span><span class="sxs-lookup"><span data-stu-id="3b398-107">802</span></span>|  
|<span data-ttu-id="3b398-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="3b398-108">Event Source</span></span>|<span data-ttu-id="3b398-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="3b398-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="3b398-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="3b398-110">Component</span></span>|<span data-ttu-id="3b398-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="3b398-111">SQLEngine</span></span>|  
|<span data-ttu-id="3b398-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="3b398-112">Symbolic Name</span></span>|<span data-ttu-id="3b398-113">NO_BUFS</span><span class="sxs-lookup"><span data-stu-id="3b398-113">NO_BUFS</span></span>|  
|<span data-ttu-id="3b398-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="3b398-114">Message Text</span></span>|<span data-ttu-id="3b398-115">버퍼 풀에 사용할 수 있는 메모리가 부족합니다.</span><span class="sxs-lookup"><span data-stu-id="3b398-115">There is insufficient memory available in the buffer pool.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="3b398-116">설명</span><span class="sxs-lookup"><span data-stu-id="3b398-116">Explanation</span></span>  
 <span data-ttu-id="3b398-117">버퍼 풀이 가득 찼고 버퍼 풀을 더 이상 늘릴 수 없을 때 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="3b398-117">This is caused when the buffer pool is full and the buffer pool can not grow any larger.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="3b398-118">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="3b398-118">User Action</span></span>  
 <span data-ttu-id="3b398-119">다음 목록은 메모리 오류 문제를 해결하는 데 도움이 되는 일반적인 단계를 간략히 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="3b398-119">The following list outlines general steps that will help in troubleshooting memory errors:</span></span>  
  
1.  <span data-ttu-id="3b398-120">다른 애플리케이션 또는 서비스가 현재 서버의 메모리를 사용 중인지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="3b398-120">Verify whether other applications or services are consuming memory on this server.</span></span> <span data-ttu-id="3b398-121">중요도가 낮은 애플리케이션이나 서비스에서 메모리를 덜 사용하도록 다시 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="3b398-121">Reconfigure less critical applications or services to consume less memory.</span></span>  
  
2.  <span data-ttu-id="3b398-122">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **: 버퍼 관리자**, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **: Memory Manager**에 대한 성능 모니터 카운터 수집을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="3b398-122">Start collecting performance monitor counters for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**: Buffer Manager**, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**: Memory Manager**.</span></span>  
  
3.  <span data-ttu-id="3b398-123">다음 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 메모리 구성 매개 변수를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="3b398-123">Check the following [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] memory configuration parameters:</span></span>  
  
    -   <span data-ttu-id="3b398-124">**max server memory**</span><span class="sxs-lookup"><span data-stu-id="3b398-124">**max server memory**</span></span>  
  
    -   <span data-ttu-id="3b398-125">**min server memory**</span><span class="sxs-lookup"><span data-stu-id="3b398-125">**min server memory**</span></span>  
  
    -   <span data-ttu-id="3b398-126">**min memory per query**</span><span class="sxs-lookup"><span data-stu-id="3b398-126">**min memory per query**</span></span>  
  
     <span data-ttu-id="3b398-127">비정상적인 설정이 있는지 확인하고 필요할 경우 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="3b398-127">Notice any unusual settings and correct them as necessary.</span></span> <span data-ttu-id="3b398-128">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 향상된 메모리 요구 사항을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="3b398-128">Account for increased memory requirements for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="3b398-129">기본 설정은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 온라인 설명서의 "서버 구성 옵션 설정"을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="3b398-129">Default settings are listed in "Setting Server Configuration Options" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
4.  <span data-ttu-id="3b398-130">DBCC MEMORYSTATUS 출력 결과를 확인하고 이러한 오류 메시지가 표시될 때 이 값이 어떻게 변경되는지 관찰합니다.</span><span class="sxs-lookup"><span data-stu-id="3b398-130">Observe DBCC MEMORYSTATUS output and the way it changes when you see these error messages.</span></span>  
  
5.  <span data-ttu-id="3b398-131">동시 세션 및 현재 실행 중인 쿼리 수와 같은 작업을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="3b398-131">Check the workload (number of concurrent sessions, currently executing queries).</span></span>  
  
 <span data-ttu-id="3b398-132">다음 동작으로 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 사용할 수 있는 메모리를 늘릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3b398-132">The following actions may make more memory available to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="3b398-133">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 외에 다른 애플리케이션이 리소스를 사용 중인 경우 이 애플리케이션을 중지하거나 별도의 서버에서 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="3b398-133">If applications besides [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] are consuming resources, try stopping these applications or running them on a separate server.</span></span>  
  
-   <span data-ttu-id="3b398-134">**max server memory**를 구성한 경우 설정값을 늘립니다.</span><span class="sxs-lookup"><span data-stu-id="3b398-134">If you have configured **max server memory,** increase the setting.</span></span>  
  
 <span data-ttu-id="3b398-135">다음 DBCC 명령을 실행하여 몇 가지 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 메모리 캐시를 비웁니다.</span><span class="sxs-lookup"><span data-stu-id="3b398-135">Run the following DBCC commands to free several [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] memory caches.</span></span>  
  
-   <span data-ttu-id="3b398-136">DBCC FREESYSTEMCACHE</span><span class="sxs-lookup"><span data-stu-id="3b398-136">DBCC FREESYSTEMCACHE</span></span>  
  
-   <span data-ttu-id="3b398-137">DBCC FREESESSIONCACHE</span><span class="sxs-lookup"><span data-stu-id="3b398-137">DBCC FREESESSIONCACHE</span></span>  
  
-   <span data-ttu-id="3b398-138">DBCC FREEPROCCACHE</span><span class="sxs-lookup"><span data-stu-id="3b398-138">DBCC FREEPROCCACHE</span></span>  
  
 <span data-ttu-id="3b398-139">문제가 지속되면 추가적인 조사를 수행하고 작업을 줄여야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3b398-139">If the problem continues, you will need to investigate further and possibly reduce workload.</span></span>  
  
  
