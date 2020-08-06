---
title: 데이터베이스 미러링 제거(SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- database mirroring [SQL Server], removing
- removing database mirroring [SQL Server]
ms.assetid: bbc4d7f7-3bc7-40d6-a822-af195fe7f8c0
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 19c1d0449fa1c7434aeaf9c51e3b2dc7bc6b68c0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87733075"
---
# <a name="remove-database-mirroring-sql-server"></a><span data-ttu-id="e4ffd-102">데이터베이스 미러링 제거(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="e4ffd-102">Remove Database Mirroring (SQL Server)</span></span>
  <span data-ttu-id="e4ffd-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 에서 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 또는 [!INCLUDE[tsql](../../includes/tsql-md.md)]을 사용하여 데이터베이스에서 데이터베이스 미러링을 제거하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="e4ffd-103">This topic describes how to remove database mirroring from a database in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  <span data-ttu-id="e4ffd-104">데이터베이스 소유자는 언제든지 데이터베이스에서 미러링을 제거하여 수동으로 데이터베이스 미러링 세션을 중지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4ffd-104">At any time, the database owner can manually stop a database mirroring session by removing mirroring from the database.</span></span>  
  
 
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="e4ffd-105">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="e4ffd-105">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="e4ffd-106">보안</span><span class="sxs-lookup"><span data-stu-id="e4ffd-106">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="e4ffd-107">권한</span><span class="sxs-lookup"><span data-stu-id="e4ffd-107">Permissions</span></span>  
 <span data-ttu-id="e4ffd-108">데이터베이스에 대한 ALTER 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="e4ffd-108">Requires ALTER permission on the database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="e4ffd-109">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="e4ffd-109">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-remove-database-mirroring"></a><span data-ttu-id="e4ffd-110">데이터베이스 미러링을 제거하려면</span><span class="sxs-lookup"><span data-stu-id="e4ffd-110">To remove database mirroring</span></span>  
  
1.  <span data-ttu-id="e4ffd-111">데이터베이스 미러링 세션 중에 주 서버 인스턴스에 연결하고 개체 탐색기에서 서버 이름을 클릭하여 서버 트리를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="e4ffd-111">During a database mirroring session, connect to the principal server instance, in Object Explorer, click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="e4ffd-112">**데이터베이스**를 확장하고 해당 데이터베이스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e4ffd-112">Expand **Databases**, and select the database.</span></span>  
  
3.  <span data-ttu-id="e4ffd-113">데이터베이스를 마우스 오른쪽 단추로 클릭하고 **태스크**를 선택한 다음 **미러**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e4ffd-113">Right-click the database, select **Tasks**, and then click **Mirror**.</span></span> <span data-ttu-id="e4ffd-114">**데이터베이스 속성** 대화 상자의 **미러링** 페이지가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="e4ffd-114">This opens the **Mirroring** page of the **Database Properties** dialog box.</span></span>  
  
4.  <span data-ttu-id="e4ffd-115">**페이지 선택** 창에서 **미러링**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e4ffd-115">In the **Select a Page** pane, click **Mirroring**.</span></span>  
  
5.  <span data-ttu-id="e4ffd-116">미러링을 제거하려면 **미러링 제거**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e4ffd-116">To remove mirroring, click **Remove Mirroring**.</span></span> <span data-ttu-id="e4ffd-117">확인 메시지가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="e4ffd-117">A prompt asks for confirmation.</span></span> <span data-ttu-id="e4ffd-118">**예**를 클릭하면 세션이 중지되고 미러링이 데이터베이스에서 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="e4ffd-118">If you click **Yes**, the session is stopped and mirroring is removed from the database.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="e4ffd-119">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="e4ffd-119">Using Transact-SQL</span></span>  
 <span data-ttu-id="e4ffd-120">데이터베이스 미러링을 제거하려면 **데이터베이스 속성**을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="e4ffd-120">To remove database mirroring, use the **Database Properties**.</span></span> <span data-ttu-id="e4ffd-121">**데이터베이스 속성** 대화 상자의 **미러링** 페이지를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="e4ffd-121">use the **Mirroring** page of the **Database Properties** dialog box.</span></span>  
  
#### <a name="to-remove-database-mirroring"></a><span data-ttu-id="e4ffd-122">데이터베이스 미러링을 제거하려면</span><span class="sxs-lookup"><span data-stu-id="e4ffd-122">To remove database mirroring</span></span>  
  
1.  <span data-ttu-id="e4ffd-123">한 미러링 파트너의 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="e4ffd-123">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)] of either mirroring partner.</span></span>  
  
2.  <span data-ttu-id="e4ffd-124">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e4ffd-124">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="e4ffd-125">다음 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="e4ffd-125">Issue the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement:</span></span>  
  
    ```  
    ALTER DATABASE database_name SET PARTNER OFF  
    ```  
  
     <span data-ttu-id="e4ffd-126">여기서 *database_name* 은 세션을 제거하려는 미러된 데이터베이스입니다.</span><span class="sxs-lookup"><span data-stu-id="e4ffd-126">where *database_name* is the mirrored database whose session you want to remove.</span></span>  
  
     <span data-ttu-id="e4ffd-127">다음 예에서는 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 예제 데이터베이스에서 데이터베이스 미러링을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="e4ffd-127">The following example removes database mirroring from the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] sample database.</span></span>  
  
    ```  
    ALTER DATABASE AdventureWorks2012 SET PARTNER OFF;  
    ```  
  
##  <a name="follow-up-removing-database-mirroring"></a><a name="FollowUp"></a> <span data-ttu-id="e4ffd-128">후속 작업: 데이터베이스 미러링 제거</span><span class="sxs-lookup"><span data-stu-id="e4ffd-128">Follow Up: Removing Database Mirroring</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e4ffd-129">미러링 제거의 영향에 대한 자세한 내용은 [데이터베이스 미러링 제거&#40;SQL Server&#41;](database-mirroring-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e4ffd-129">For information about the impact of removing mirroring, see [Removing Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md).</span></span>  
  
-   <span data-ttu-id="e4ffd-130">**데이터베이스에서 미러링을 다시 시작하려는 경우**</span><span class="sxs-lookup"><span data-stu-id="e4ffd-130">**If you intend to restart mirroring on the database**</span></span>  
  
     <span data-ttu-id="e4ffd-131">미러링이 제거된 후 주 데이터베이스에서 수행된 모든 로그 백업을 미러 데이터베이스에 모두 적용해야만 미러링을 다시 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4ffd-131">Any log backups taken on the principal database after mirroring was removed must all be applied to the mirror database before you can restart mirroring.</span></span>  
  
-   <span data-ttu-id="e4ffd-132">**미러링을 다시 시작하지 않으려는 경우**</span><span class="sxs-lookup"><span data-stu-id="e4ffd-132">**If you do not intent to restart mirroring**</span></span>  
  
     <span data-ttu-id="e4ffd-133">필요한 경우 이전 미러 데이터베이스를 복구할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4ffd-133">Optionally, you can recover the former mirror database.</span></span> <span data-ttu-id="e4ffd-134">미러 서버로 사용했던 서버 인스턴스에 다음 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4ffd-134">On the server instance that was the mirror server, you can use the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement:</span></span>  
  
    ```  
    RESTORE DATABASE database_name WITH RECOVERY;  
    ```  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="e4ffd-135">이 데이터베이스를 복구하면 같은 이름의 두 분기 데이터베이스가 온라인 상태가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e4ffd-135">If you recover this database, two divergent databases with the same name are online.</span></span> <span data-ttu-id="e4ffd-136">따라서 클라이언트가 두 데이터베이스 중 하나(일반적으로 가장 최근의 주 데이터베이스)에만 액세스할 수 있는지 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4ffd-136">Therefore, you need to ensure that clients can access only one of them-typically the most recent principal database.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="e4ffd-137">관련 작업</span><span class="sxs-lookup"><span data-stu-id="e4ffd-137">Related Tasks</span></span>  
  
-   [<span data-ttu-id="e4ffd-138">데이터베이스 미러링 세션 일시 중지 또는 재개&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="e4ffd-138">Pause or Resume a Database Mirroring Session &#40;SQL Server&#41;</span></span>](pause-or-resume-a-database-mirroring-session-sql-server.md)  
  
-   [<span data-ttu-id="e4ffd-139">데이터베이스 미러링 세션에서 미러링 모니터 서버 제거&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="e4ffd-139">Remove the Witness from a Database Mirroring Session &#40;SQL Server&#41;</span></span>](remove-the-witness-from-a-database-mirroring-session-sql-server.md)  
  
-   [<span data-ttu-id="e4ffd-140">Windows 인증을 사용하여 데이터베이스 미러링 세션 구성&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="e4ffd-140">Establish a Database Mirroring Session Using Windows Authentication &#40;SQL Server Management Studio&#41;</span></span>](establish-database-mirroring-session-windows-authentication.md)  
  
-   [<span data-ttu-id="e4ffd-141">Windows 인증을 사용하여 데이터베이스 미러링 세션 구성&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="e4ffd-141">Establish a Database Mirroring Session Using Windows Authentication &#40;Transact-SQL&#41;</span></span>](database-mirroring-establish-session-windows-authentication.md)  
  
-   [<span data-ttu-id="e4ffd-142">예: 인증서를 사용하여 데이터베이스 미러링 설정&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="e4ffd-142">Example: Setting Up Database Mirroring Using Certificates &#40;Transact-SQL&#41;</span></span>](example-setting-up-database-mirroring-using-certificates-transact-sql.md)  
  
## <a name="see-also"></a><span data-ttu-id="e4ffd-143">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e4ffd-143">See Also</span></span>  
 <span data-ttu-id="e4ffd-144">[데이터베이스 미러링&#40;SQL Server&#41;](database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="e4ffd-144">[Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span></span>  
 <span data-ttu-id="e4ffd-145">[데이터베이스 미러링 설정&#40;SQL Server&#41;](setting-up-database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="e4ffd-145">[Setting Up Database Mirroring &#40;SQL Server&#41;](setting-up-database-mirroring-sql-server.md) </span></span>  
 [<span data-ttu-id="e4ffd-146">AlwaysOn 가용성 그룹(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="e4ffd-146">AlwaysOn Availability Groups (SQL Server)</span></span>](../availability-groups/windows/always-on-availability-groups-sql-server.md)  
  
  
