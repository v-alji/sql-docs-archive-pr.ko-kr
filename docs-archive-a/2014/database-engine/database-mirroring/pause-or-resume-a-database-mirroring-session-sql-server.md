---
title: 데이터베이스 미러링 세션 일시 중지 또는 재개(SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- resuming database mirroring
- database mirroring [SQL Server], sessions
- database mirroring [SQL Server], pausing
- database mirroring [SQL Server], resuming
- pausing database mirroring
ms.assetid: 05ede3b4-6abe-4442-abb7-9f5aee1d6bc0
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: b8a9e30bed3ff268fcfdc6e352ad15ebedfe4e8e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87733115"
---
# <a name="pause-or-resume-a-database-mirroring-session-sql-server"></a><span data-ttu-id="bb882-102">데이터베이스 미러링 세션 일시 중지 또는 재개(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="bb882-102">Pause or Resume a Database Mirroring Session (SQL Server)</span></span>
  <span data-ttu-id="bb882-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 에서 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 또는 [!INCLUDE[tsql](../../includes/tsql-md.md)]을 사용하여 데이터베이스 미러링을 일시 중지하거나 재개하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="bb882-103">This topic describes how to pause or resume database mirroring in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="bb882-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="bb882-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="bb882-105">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="bb882-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="bb882-106">보안</span><span class="sxs-lookup"><span data-stu-id="bb882-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="bb882-107">**ReplaceThisText를 수행하려면:**</span><span class="sxs-lookup"><span data-stu-id="bb882-107">**To ReplaceThisText, using:**</span></span>  
  
     [<span data-ttu-id="bb882-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="bb882-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="bb882-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="bb882-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="bb882-110">**후속 작업:**  [데이터베이스 미러링을 일시 중지하거나 재개한 후](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="bb882-110">**Follow Up:**  [After Pausing or Resuming Database Mirroring](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="bb882-111">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="bb882-111">Before You Begin</span></span>  
 <span data-ttu-id="bb882-112">언제든지 데이터베이스 미러링 세션을 일시 중지하여 병목 상태에서 성능을 향상시킬 수 있으며, 일시 중지된 세션을 언제든지 재개할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb882-112">At any time, you can suspend a database mirroring session, which might improve performance during bottlenecks, and you can resume a suspended session at any time.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="bb882-113">강제 서비스 이후에 원래 주 서버가 다시 연결되면 미러링이 일시 중지됩니다.</span><span class="sxs-lookup"><span data-stu-id="bb882-113">After a forced service, when the original principal server reconnects, mirroring is suspended.</span></span> <span data-ttu-id="bb882-114">이 경우 미러링을 재개하면 원래 주 서버의 데이터가 손실될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb882-114">Resuming mirroring in this situation could possibly cause data loss on the original principal server.</span></span> <span data-ttu-id="bb882-115">데이터 손실 위험을 관리하는 방법은 [데이터베이스 미러링 세션 중 역할 전환&#40;SQL Server&#41;](role-switching-during-a-database-mirroring-session-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="bb882-115">For information about managing the potential data loss, see [Role Switching During a Database Mirroring Session &#40;SQL Server&#41;](role-switching-during-a-database-mirroring-session-sql-server.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="bb882-116">보안</span><span class="sxs-lookup"><span data-stu-id="bb882-116">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="bb882-117">권한</span><span class="sxs-lookup"><span data-stu-id="bb882-117">Permissions</span></span>  
 <span data-ttu-id="bb882-118">데이터베이스에 대한 ALTER 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="bb882-118">Requires ALTER permission on the database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="bb882-119">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="bb882-119">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="bb882-120">데이터베이스 미러링 세션을 일시 중지하거나 재개하려면 **데이터베이스 속성 미러링** 페이지를 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="bb882-120">To pause or resume a database mirroring session use the **Database Properties Mirroring** page.</span></span>  
  
#### <a name="to-pause-or-resume-database-mirroring"></a><span data-ttu-id="bb882-121">데이터베이스 미러링을 일시 중지 또는 재개하려면</span><span class="sxs-lookup"><span data-stu-id="bb882-121">To pause or resume database mirroring</span></span>  
  
1.  <span data-ttu-id="bb882-122">데이터베이스 미러링 세션 중에 주 서버 인스턴스에 연결하고 개체 탐색기에서 서버 이름을 클릭하여 서버 트리를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="bb882-122">During a database mirroring session, connect to the principal server instance, in Object Explorer, click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="bb882-123">**데이터베이스**를 확장하고 해당 데이터베이스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="bb882-123">Expand **Databases**, and select the database.</span></span>  
  
3.  <span data-ttu-id="bb882-124">데이터베이스를 마우스 오른쪽 단추로 클릭하고 **태스크**를 선택한 다음 **미러**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bb882-124">Right-click the database, select **Tasks**, and then click **Mirror**.</span></span> <span data-ttu-id="bb882-125">**데이터베이스 속성** 대화 상자의 **미러링** 페이지가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="bb882-125">This opens the **Mirroring** page of the **Database Properties** dialog box.</span></span>  
  
4.  <span data-ttu-id="bb882-126">세션을 일시 중지하려면 **일시 중지**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bb882-126">To pause the session, click **Pause**.</span></span>  
  
     <span data-ttu-id="bb882-127">확인 메시지가 나타납니다. **예**를 클릭하면 세션이 일시 중지되고 단추가 **재개**로 바뀝니다.</span><span class="sxs-lookup"><span data-stu-id="bb882-127">A prompt asks for confirmation; if you click **Yes**, the session is paused, and the button changes to **Resume**.</span></span>  
  
     <span data-ttu-id="bb882-128">세션의 일시 중지에 따른 영향에 대한 자세한 내용은 [데이터베이스 미러링 일시 중지 및 재개&#40;SQL Server&#41;](database-mirroring-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="bb882-128">For more information about the impact of pausing a session, see [Pausing and Resuming Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md).</span></span>  
  
5.  <span data-ttu-id="bb882-129">세션을 재개하려면 **재개**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bb882-129">To resume the session, click **Resume**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="bb882-130">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="bb882-130">Using Transact-SQL</span></span>  
  
#### <a name="to-pause-database-mirroring"></a><span data-ttu-id="bb882-131">데이터베이스 미러링을 일시 중지하려면</span><span class="sxs-lookup"><span data-stu-id="bb882-131">To pause database mirroring</span></span>  
  
1.  <span data-ttu-id="bb882-132">한 파트너에 대한 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="bb882-132">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)] for either partner.</span></span>  
  
2.  <span data-ttu-id="bb882-133">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bb882-133">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="bb882-134">다음 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="bb882-134">Issue the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement:</span></span>  
  
     <span data-ttu-id="bb882-135">ALTER DATABASE *database_name* SET PARTNER SUSPEND</span><span class="sxs-lookup"><span data-stu-id="bb882-135">ALTER DATABASE *database_name* SET PARTNER SUSPEND</span></span>  
  
     <span data-ttu-id="bb882-136">여기서 *database_name* 은 일시 중지할 세션이 있는 미러된 데이터베이스입니다.</span><span class="sxs-lookup"><span data-stu-id="bb882-136">where *database_name* is the mirrored database whose session you want to you want to suspend.</span></span>  
  
     <span data-ttu-id="bb882-137">다음 예에서는 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 예제 데이터베이스를 일시 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="bb882-137">The following example pauses the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] sample database.</span></span>  
  
    ```  
    ALTER DATABASE AdventureWorks2012 SET PARTNER SUSPEND;  
    ```  
  
##### <a name="to-resume-database-mirroring"></a><span data-ttu-id="bb882-138">데이터베이스 미러링을 재개하려면</span><span class="sxs-lookup"><span data-stu-id="bb882-138">To resume database mirroring</span></span>  
  
1.  <span data-ttu-id="bb882-139">한 파트너에 대한 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="bb882-139">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)] for either partner.</span></span>  
  
2.  <span data-ttu-id="bb882-140">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bb882-140">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="bb882-141">다음 Transact-SQL 문을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="bb882-141">Issue the following Transact-SQL statement:</span></span>  
  
     <span data-ttu-id="bb882-142">ALTER DATABASE *database_name* SET PARTNER RESUME</span><span class="sxs-lookup"><span data-stu-id="bb882-142">ALTER DATABASE *database_name* SET PARTNER RESUME</span></span>  
  
     <span data-ttu-id="bb882-143">여기서 *database_name* 은 세션을 재개하려는 미러된 데이터베이스입니다.</span><span class="sxs-lookup"><span data-stu-id="bb882-143">where *database_name* is the mirrored database whose session you want to resume.</span></span>  
  
     <span data-ttu-id="bb882-144">다음 예에서는 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 예제 데이터베이스를 일시 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="bb882-144">The following example pauses the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] sample database.</span></span>  
  
    ```  
    ALTER DATABASE AdventureWorks2012 SET PARTNER RESUME;  
    ```  
  
##  <a name="follow-up-after-pausing-or-resuming-database-mirroring"></a><a name="FollowUp"></a><span data-ttu-id="bb882-145">후속 작업: 데이터베이스 미러링을 일시 중지 하거나 재개 한 후</span><span class="sxs-lookup"><span data-stu-id="bb882-145">Follow Up: After Pausing or Resuming Database Mirroring</span></span>  
  
-   <span data-ttu-id="bb882-146">**데이터베이스 미러링을 일시 중지한 후**</span><span class="sxs-lookup"><span data-stu-id="bb882-146">**After pausing database mirroring**</span></span>  
  
     <span data-ttu-id="bb882-147">주 데이터베이스에서 전체 트랜잭션 로그를 피하기 위해 예방 조치를 취해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb882-147">On the primary database, take precautions to avoid a full transaction log.</span></span> <span data-ttu-id="bb882-148">자세한 내용은 [트랜잭션 로그&#40;SQL Server&#41;](../../relational-databases/logs/the-transaction-log-sql-server.md)을(를) 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="bb882-148">For more information, see [The Transaction Log &#40;SQL Server&#41;](../../relational-databases/logs/the-transaction-log-sql-server.md).</span></span>  
  
-   <span data-ttu-id="bb882-149">**데이터베이스 미러링을 재개한 후**</span><span class="sxs-lookup"><span data-stu-id="bb882-149">**After resuming database mirroring**</span></span>  
  
     <span data-ttu-id="bb882-150">데이터베이스 미러링을 재개하면 미러 데이터베이스는 SYNCHRONIZING 상태가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bb882-150">Resuming database mirroring places the mirror database in the SYNCHRONIZING state.</span></span> <span data-ttu-id="bb882-151">보안 수준이 FULL인 경우 미러 데이터베이스는 주 데이터베이스와 동기화되고 SYNCHRONIZED 상태가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bb882-151">If the safety level is FULL, the mirror catches up with the principal and the mirror database enters the SYNCHRONIZED state.</span></span> <span data-ttu-id="bb882-152">이 시점에서 장애 조치(Failover)가 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="bb882-152">At this point, failover becomes possible.</span></span> <span data-ttu-id="bb882-153">미러링 모니터가 있고 ON 상태인 경우 자동 장애 조치가 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="bb882-153">If the witness is present and ON, automatic failover is possible.</span></span> <span data-ttu-id="bb882-154">미러링 모니터가 없는 경우 수동 장애 조치가 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="bb882-154">In the absence of a witness, manual failover is possible.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="bb882-155">관련 작업</span><span class="sxs-lookup"><span data-stu-id="bb882-155">Related Tasks</span></span>  
  
-   [<span data-ttu-id="bb882-156">데이터베이스 미러링 제거&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="bb882-156">Remove Database Mirroring &#40;SQL Server&#41;</span></span>](remove-database-mirroring-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="bb882-157">참고 항목</span><span class="sxs-lookup"><span data-stu-id="bb882-157">See Also</span></span>  
 [<span data-ttu-id="bb882-158">데이터베이스 미러링&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="bb882-158">Database Mirroring &#40;SQL Server&#41;</span></span>](database-mirroring-sql-server.md)  
  
  
