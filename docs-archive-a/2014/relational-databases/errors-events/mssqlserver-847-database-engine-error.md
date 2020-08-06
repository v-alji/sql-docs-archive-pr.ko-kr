---
title: MSSQLSERVER_847 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 847 (Database Engine error)
ms.assetid: 67208b7c-bd8d-48a1-9f70-a6488e0f5f9b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6b2d5c0a35533700606a44867d2a51cf9087e399
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652859"
---
# <a name="mssqlserver_847"></a><span data-ttu-id="daac1-102">MSSQLSERVER_847</span><span class="sxs-lookup"><span data-stu-id="daac1-102">MSSQLSERVER_847</span></span>
    
## <a name="details"></a><span data-ttu-id="daac1-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="daac1-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="daac1-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="daac1-104">Product Name</span></span>|<span data-ttu-id="daac1-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="daac1-105">SQL Server</span></span>|  
|<span data-ttu-id="daac1-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="daac1-106">Event ID</span></span>|<span data-ttu-id="daac1-107">847</span><span class="sxs-lookup"><span data-stu-id="daac1-107">847</span></span>|  
|<span data-ttu-id="daac1-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="daac1-108">Event Source</span></span>|<span data-ttu-id="daac1-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="daac1-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="daac1-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="daac1-110">Component</span></span>|<span data-ttu-id="daac1-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="daac1-111">SQLEngine</span></span>|  
|<span data-ttu-id="daac1-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="daac1-112">Symbolic Name</span></span>|<span data-ttu-id="daac1-113">해당 없음</span><span class="sxs-lookup"><span data-stu-id="daac1-113">N/A</span></span>|  
|<span data-ttu-id="daac1-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="daac1-114">Message Text</span></span>|<span data-ttu-id="daac1-115">래치를 기다리는 동안 시간이 초과되었습니다. 클래스 '%ls', ID %p, 유형 %d, 태스크 0x%p : %d, 대기 시간 %d, 플래그 0x%I64x, 소유 태스크 0x%p.</span><span class="sxs-lookup"><span data-stu-id="daac1-115">Time-out occurred while waiting for latch: class '%ls', id %p, type %d, Task 0x%p : %d, waittime %d, flags 0x%I64x, owning task 0x%p.</span></span> <span data-ttu-id="daac1-116">계속 대기합니다.</span><span class="sxs-lookup"><span data-stu-id="daac1-116">Continuing to wait.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="daac1-117">설명</span><span class="sxs-lookup"><span data-stu-id="daac1-117">Explanation</span></span>  
 <span data-ttu-id="daac1-118">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]가 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 오류 로그에 버퍼 래치 오류를 쓸 때 컴퓨터가 응답하지 않거나, 시간이 초과되거나, 일반 작업의 다른 장애가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="daac1-118">A computer might stop responding, or a time-out or some other disruption of regular operations might occur at the same time that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] writes buffer latch errors to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log.</span></span>  
  
 <span data-ttu-id="daac1-119">메시지의 상태 필드에 값 0x04가 설정되어 있는 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]가 I/O 작업을 기다리고 있는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="daac1-119">If the stat field in the message has the value of 0x04 on, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is waiting for an I/O operation.</span></span> <span data-ttu-id="daac1-120">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 오류 로그에 [MSSQLSERVER_833](mssqlserver-833-database-engine-error.md) 메시지가 표시될 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="daac1-120">You may also receive message [MSSQLSERVER_833](mssqlserver-833-database-engine-error.md) in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log.</span></span>  
  
 <span data-ttu-id="daac1-121">메시지의 상태 필드에 값 0x04가 해제되어 있는 경우 페이지에 경합 문제가 있는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="daac1-121">If the stat field in the message has the value 0x04 off, there is heavy contention for a page.</span></span> <span data-ttu-id="daac1-122">개체가 데이터 페이지인 경우 이 오류는 비효율적인 코드 디자인으로 인해 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="daac1-122">If the object is a data page, this can be caused by inefficient code design.</span></span> <span data-ttu-id="daac1-123">페이지가 데이터가 아닌 경우에는 부족한 하드웨어 리소스 등으로 인해 서버 병목 현상이 일어나 이 오류가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="daac1-123">If the page is nondata, the error might be caused by server bottlenecks, such as insufficient hardware resources.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="daac1-124">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="daac1-124">User Action</span></span>  
 <span data-ttu-id="daac1-125">이 문제를 해결하려면 사용자 환경에 따라 다음 단계 중 하나 이상을 수행하여 오류 메시지를 줄이거나 오류 메시지가 표시되지 않도록 하십시오.</span><span class="sxs-lookup"><span data-stu-id="daac1-125">To work around this problem, depending on your environment, one or more of the following steps might reduce or eliminate the error messages:</span></span>  
  
-   <span data-ttu-id="daac1-126">하드웨어에 병목 상태가 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="daac1-126">Determine whether you have any hardware bottlenecks.</span></span> <span data-ttu-id="daac1-127">필요한 경우 사용자 환경의 구성, 쿼리 및 부하 요구 사항을 지원할 수 있도록 하드웨어를 업그레이드합니다.</span><span class="sxs-lookup"><span data-stu-id="daac1-127">If it is necessary, upgrade your hardware so that it can support the configuration, query, and load requirements of your environment.</span></span> <span data-ttu-id="daac1-128">병목 상태에 대한 자세한 내용은 [병목 상태 식별](../performance/identify-bottlenecks.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="daac1-128">For more information about bottlenecks, see [Identify Bottlenecks](../performance/identify-bottlenecks.md).</span></span>  
  
-   <span data-ttu-id="daac1-129">기록된 오류를 확인하고 하드웨어 공급업체에서 제공받은 진단 프로그램을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="daac1-129">Check for any logged errors and run any diagnostics provided by your hardware vendor.</span></span>  
  
-   <span data-ttu-id="daac1-130">디스크 드라이브가 압축되어 있지 않은지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="daac1-130">Make sure that your disk drives are not compressed.</span></span> <span data-ttu-id="daac1-131">압축된 드라이브에는 데이터 또는 로그 파일을 저장할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="daac1-131">Storing data or log files on compressed drives is not supported.</span></span> <span data-ttu-id="daac1-132">물리적 파일에 대한 자세한 내용은 [데이터베이스 파일 및 파일 그룹](../databases/database-files-and-filegroups.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="daac1-132">For more information about physical files, see [Database Files and Filegroups](../databases/database-files-and-filegroups.md).</span></span>  
  
-   <span data-ttu-id="daac1-133">다음 옵션 설정을 해제하는 경우 오류 메시지가 사라지는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="daac1-133">See whether the error messages disappear when you set the following options to off:</span></span>  
  
    -   <span data-ttu-id="daac1-134">SQL Server priority boost 구성 옵션</span><span class="sxs-lookup"><span data-stu-id="daac1-134">SQL Server priority boost configuration option</span></span>  
  
    -   <span data-ttu-id="daac1-135">lightweight pooling(파이버 모드) 옵션</span><span class="sxs-lookup"><span data-stu-id="daac1-135">Lightweight pooling (fiber mode) option</span></span>  
  
    -   <span data-ttu-id="daac1-136">set working set size 옵션</span><span class="sxs-lookup"><span data-stu-id="daac1-136">Set working set size option</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="daac1-137">기본 설정인 OFF에서 다른 값으로 변경하면 이전 설정의 성능이 저하될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="daac1-137">The previous settings can frequently be counter-productive if you change them from their default setting of OFF.</span></span> <span data-ttu-id="daac1-138">설정에 대한 자세한 내용은 [서버 구성 옵션&#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="daac1-138">For more information about the settings, see [Server Configuration Options &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md).</span></span>  
  
-   <span data-ttu-id="daac1-139">쿼리를 튜닝하여 시스템에 사용되는 리소스를 줄입니다.</span><span class="sxs-lookup"><span data-stu-id="daac1-139">Tune queries to reduce resources used on the system.</span></span> <span data-ttu-id="daac1-140">성능을 튜닝하면 시스템의 스트레스가 줄어들고 개별 쿼리에 대한 응답 시간이 개선됩니다.</span><span class="sxs-lookup"><span data-stu-id="daac1-140">Performance tuning will help reduce the stress on a system and improve response time for individual queries.</span></span>  
  
-   <span data-ttu-id="daac1-141">AUTO_SHRINK 옵션을 OFF로 설정하여 데이터베이스 크기 변경으로 인한 오버헤드를 줄입니다.</span><span class="sxs-lookup"><span data-stu-id="daac1-141">Set the AUTO_SHRINK option to OFF to reduce the overhead of changes to the database size.</span></span>  
  
-   <span data-ttu-id="daac1-142">FILEGROWTH 옵션을 파일 증가가 자주 발생하지 않을 증가값으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="daac1-142">Make sure that you set the FILEGROWTH option to increments that are large enough to be infrequent.</span></span> <span data-ttu-id="daac1-143">또한 데이터베이스에서 사용 가능한 공간을 확인하는 작업을 예약한 다음 사용률이 낮은 시간에 데이터베이스 크기를 늘립니다.</span><span class="sxs-lookup"><span data-stu-id="daac1-143">Schedule a job to check the available space in the databases, and then increase the database size during nonpeak hours.</span></span>  
  
  
