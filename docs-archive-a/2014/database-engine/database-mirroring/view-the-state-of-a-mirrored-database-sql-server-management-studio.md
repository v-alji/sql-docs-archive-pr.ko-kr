---
title: 미러된 데이터베이스 상태 보기(SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- states [SQL Server], database mirroring
- database mirroring [SQL Server], states
ms.assetid: 544f4194-253e-4c57-96ca-31c16301434f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: fc691e8b746a816ab88448e3399aebad6d8844e9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649671"
---
# <a name="view-the-state-of-a-mirrored-database-sql-server-management-studio"></a><span data-ttu-id="719c5-102">미러된 데이터베이스의 상태 보기(SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="719c5-102">View the State of a Mirrored Database (SQL Server Management Studio)</span></span>
  <span data-ttu-id="719c5-103">데이터베이스 미러링 세션 동안 **데이터베이스 속성** 대화 상자의 **미러링** 페이지에서 상태를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="719c5-103">During a database mirroring session, you can view the status on the **Mirroring** page of the **Database Properties** dialog box.</span></span>  
  
### <a name="to-view-the-status-of-a-database-mirroring-session"></a><span data-ttu-id="719c5-104">데이터베이스 미러링 세션 상태를 보려면</span><span class="sxs-lookup"><span data-stu-id="719c5-104">To view the status of a database mirroring session</span></span>  
  
1.  <span data-ttu-id="719c5-105">주 서버 인스턴스에 연결한 다음 개체 탐색기에서 서버 이름을 클릭하여 서버 트리를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="719c5-105">After connecting to the principal server instance, in Object Explorer, click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="719c5-106">**데이터베이스**를 확장하고 미러링할 데이터베이스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="719c5-106">Expand **Databases**, and select the database to be mirrored.</span></span>  
  
3.  <span data-ttu-id="719c5-107">데이터베이스를 마우스 오른쪽 단추로 클릭하고 **태스크**를 선택한 다음 **미러**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="719c5-107">Right-click the database, select **Tasks**, and then click **Mirror**.</span></span> <span data-ttu-id="719c5-108">**데이터베이스 속성** 대화 상자의 **미러링** 페이지가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="719c5-108">This opens the **Mirroring** page of the **Database Properties** dialog box.</span></span>  
  
4.  <span data-ttu-id="719c5-109">미러링이 시작된 다음 **상태** 패널에는 **미러링** 페이지를 선택하거나 **새로 고침** 단추를 클릭한 경우와 같은 데이터베이스 미러링 세션 상태가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="719c5-109">After mirroring begins, the **Status** panel displays the status of the database mirroring session as of when you selected the **Mirroring** page or clicked the **Refresh** button.</span></span> <span data-ttu-id="719c5-110">가능한 상태는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="719c5-110">The possible states are as follows:</span></span>  
  
    |<span data-ttu-id="719c5-111">상태</span><span class="sxs-lookup"><span data-stu-id="719c5-111">States</span></span>|<span data-ttu-id="719c5-112">설명</span><span class="sxs-lookup"><span data-stu-id="719c5-112">Explanation</span></span>|  
    |------------|-----------------|  
    |\<blank>|<span data-ttu-id="719c5-113">데이터베이스 미러링 세션이 없으며 **미러링** 페이지에 대해 보고할 활동이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="719c5-113">No database mirroring session exists and there is no activity to report on the **Mirroring** page.</span></span>|  
    |<span data-ttu-id="719c5-114">일시 중지됨</span><span class="sxs-lookup"><span data-stu-id="719c5-114">Paused</span></span>|<span data-ttu-id="719c5-115">주 데이터베이스가 실행되고 있지만 미러 서버로 로그를 보내지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="719c5-115">The principal database is running but is not sending any logs to the mirror server.</span></span> <span data-ttu-id="719c5-116">데이터베이스의 미러 복사본을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="719c5-116">The mirror copy of the database is not available.</span></span>|  
    |<span data-ttu-id="719c5-117">연결 없음</span><span class="sxs-lookup"><span data-stu-id="719c5-117">No connection</span></span>|<span data-ttu-id="719c5-118">주 서버 인스턴스는 해당 파트너나 미러링 모니터 서버 인스턴스(있는 경우)에 연결할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="719c5-118">The principal server instance cannot connect to its partner or to the witness server instance (if any)</span></span>|  
    |<span data-ttu-id="719c5-119">동기화 중</span><span class="sxs-lookup"><span data-stu-id="719c5-119">Synchronizing</span></span>|<span data-ttu-id="719c5-120">미러 데이터베이스의 내용이 주 데이터베이스의 내용보다 오래된 것입니다.</span><span class="sxs-lookup"><span data-stu-id="719c5-120">The contents of the mirror database are lagging behind the contents of the principal database.</span></span> <span data-ttu-id="719c5-121">주 서버 인스턴스에서 로그 레코드를 미러 서버 인스턴스로 보내면 미러 서버 인스턴스에서 변경 사항을 미러 데이터베이스에 적용하여 롤포워드합니다.</span><span class="sxs-lookup"><span data-stu-id="719c5-121">The principal server instance is sending log records to the mirror server instance, which is applying the changes to the mirror database to roll it forward.</span></span><br /><br /> <span data-ttu-id="719c5-122">데이터베이스 미러링 세션을 시작할 때는 미러 데이터베이스와 주 데이터베이스가 동기화하는 중입니다.</span><span class="sxs-lookup"><span data-stu-id="719c5-122">At the start of a database mirroring session, the mirror and principal databases are in the synchronizing state.</span></span>|  
    |<span data-ttu-id="719c5-123">장애 조치</span><span class="sxs-lookup"><span data-stu-id="719c5-123">Failover</span></span>|<span data-ttu-id="719c5-124">주 서버 인스턴스에서 수동 장애 조치(역할 교체)가 시작되었지만 미러 서버 인스턴스에서 아직 수락하지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="719c5-124">On the principal server instance, a manual failover (role swap) has begun but has not yet accepted by the mirror.</span></span>|  
    |<span data-ttu-id="719c5-125">동기화됨</span><span class="sxs-lookup"><span data-stu-id="719c5-125">Synchronized</span></span>|<span data-ttu-id="719c5-126">미러 데이터베이스에 주 데이터베이스와 동일한 데이터가 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="719c5-126">The mirror database contains the same data as the principal database.</span></span> <span data-ttu-id="719c5-127">수동 장애 조치와 자동 장애 조치는 동기화 *상태에서만* 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="719c5-127">Manual and automatic failover are possible *only* in the synchronized state.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="719c5-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="719c5-128">See Also</span></span>  
 [<span data-ttu-id="719c5-129">미러링 상태&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="719c5-129">Mirroring States &#40;SQL Server&#41;</span></span>](mirroring-states-sql-server.md)  
  
  
