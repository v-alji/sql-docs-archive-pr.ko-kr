---
title: 데이터베이스 미러링 세션에서 미러링 모니터 서버 제거(SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- witness [SQL Server], turning off
- witness [SQL Server], removing
- database mirroring [SQL Server], witness
ms.assetid: f3ce7afc-8936-4d35-80ce-d0f8fbc318d3
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: d5ede54aca3588a6fcd7cee8759112b606eac752
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87733072"
---
# <a name="remove-the-witness-from-a-database-mirroring-session-sql-server"></a><span data-ttu-id="b9da4-102">데이터베이스 미러링 세션에서 미러링 모니터 서버 제거(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="b9da4-102">Remove the Witness from a Database Mirroring Session (SQL Server)</span></span>
  <span data-ttu-id="b9da4-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 에서 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 또는 [!INCLUDE[tsql](../../includes/tsql-md.md)]을 사용하여 데이터베이스 미러링 세션에서 미러링 모니터 서버를 제거하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="b9da4-103">This topic describes how to remove a witness from a database mirroring session in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="b9da4-104">데이터베이스 소유자는 데이터베이스 미러링 세션 중에 언제든지 미러링 모니터를 해제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b9da4-104">At any time during a database mirroring session, the database owner can turn off the witness for a database mirroring session.</span></span>  
  
 <span data-ttu-id="b9da4-105">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="b9da4-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="b9da4-106">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="b9da4-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="b9da4-107">보안</span><span class="sxs-lookup"><span data-stu-id="b9da4-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="b9da4-108">**미러링 모니터 서버를 제거하려면:**</span><span class="sxs-lookup"><span data-stu-id="b9da4-108">**To Replace remove the witness, using:**</span></span>  
  
     [<span data-ttu-id="b9da4-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="b9da4-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="b9da4-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="b9da4-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="b9da4-111">**후속 작업:**  [미러링 모니터 서버를 제거한 후](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="b9da4-111">**Follow Up:**  [After Removing the Witness](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="b9da4-112">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="b9da4-112">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="b9da4-113">보안</span><span class="sxs-lookup"><span data-stu-id="b9da4-113">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="b9da4-114">권한</span><span class="sxs-lookup"><span data-stu-id="b9da4-114">Permissions</span></span>  
 <span data-ttu-id="b9da4-115">데이터베이스에 대한 ALTER 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="b9da4-115">Requires ALTER permission on the database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="b9da4-116">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="b9da4-116">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-remove-the-witness"></a><span data-ttu-id="b9da4-117">미러링 모니터를 제거하려면</span><span class="sxs-lookup"><span data-stu-id="b9da4-117">To remove the witness</span></span>  
  
1.  <span data-ttu-id="b9da4-118">주 서버 인스턴스에 연결한 다음 **개체 탐색기** 창에서 서버 이름을 클릭하여 서버 트리를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="b9da4-118">Connect to the principal server instance and, in the **Object Explorer** pane, click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="b9da4-119">**데이터베이스**를 확장한 다음 미러링 모니터 서버를 제거할 데이터베이스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b9da4-119">Expand **Databases**, and select the database whose witness you want to remove.</span></span>  
  
3.  <span data-ttu-id="b9da4-120">데이터베이스를 마우스 오른쪽 단추로 클릭하고 **태스크**를 선택한 다음 **미러**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b9da4-120">Right-click the database, select **Tasks**, and then click **Mirror**.</span></span> <span data-ttu-id="b9da4-121">**데이터베이스 속성** 대화 상자의 **미러링** 페이지가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="b9da4-121">This opens the **Mirroring** page of the **Database Properties** dialog box.</span></span>  
  
4.  <span data-ttu-id="b9da4-122">미러링 모니터 서버를 제거하려면 **미러링 모니터 서버** 필드에서 서버 네트워크 주소를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="b9da4-122">To remove the witness, delete its server network address from the **Witness** field.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="b9da4-123">자동 장애 조치(failover)가 있는 보호 우선 모드에서 성능 우선 모드로 전환하면 **미러링 모니터 서버** 필드가 자동으로 지워집니다.</span><span class="sxs-lookup"><span data-stu-id="b9da4-123">If you switch from high-safety mode with automatic failover to high-performance mode, the **Witness** field is automatically cleared.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="b9da4-124">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="b9da4-124">Using Transact-SQL</span></span>  
  
#### <a name="to-remove-the-witness"></a><span data-ttu-id="b9da4-125">미러링 모니터를 제거하려면</span><span class="sxs-lookup"><span data-stu-id="b9da4-125">To remove the witness</span></span>  
  
1.  <span data-ttu-id="b9da4-126">한 파트너 서버 인스턴스의 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="b9da4-126">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)] on either partner server instance.</span></span>  
  
2.  <span data-ttu-id="b9da4-127">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b9da4-127">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="b9da4-128">다음 문을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="b9da4-128">Issue the following statement:</span></span>  
  
     <span data-ttu-id="b9da4-129">[ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring) *database_name* SET WITNESS OFF</span><span class="sxs-lookup"><span data-stu-id="b9da4-129">[ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring) *database_name* SET WITNESS OFF</span></span>  
  
     <span data-ttu-id="b9da4-130">여기서 *database_name* 은 미러된 데이터베이스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="b9da4-130">where *database_name* is the name of the mirrored database.</span></span>  
  
     <span data-ttu-id="b9da4-131">다음 예에서는 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 데이터베이스에서 미러링 모니터 서버를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="b9da4-131">The following example removes the witness from the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database.</span></span>  
  
    ```  
    ALTER DATABASE AdventureWorks2012 SET WITNESS OFF ;  
    ```  
  
##  <a name="follow-up-after-removing-the-witness"></a><a name="FollowUp"></a><span data-ttu-id="b9da4-132">후속 작업: 미러링 모니터 서버를 제거한 후</span><span class="sxs-lookup"><span data-stu-id="b9da4-132">Follow Up: After Removing the Witness</span></span>  
 <span data-ttu-id="b9da4-133">미러링 모니터 서버를 해제하면 트랜잭션 보안 설정에 따라 [운영 모드](database-mirroring-operating-modes.md)가 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="b9da4-133">Turning off the witness changes the [operating mode](database-mirroring-operating-modes.md)in accordance with the transaction-safety setting:</span></span>  
  
-   <span data-ttu-id="b9da4-134">트랜잭션 보안을 FULL(기본값)로 설정하면 해당 세션은 자동 장애 조치(Failover)가 없는 보호 우선 동기 모드를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b9da4-134">If transaction safety is set to FULL (the default), the session uses high-safety, synchronous mode without automatic failover.</span></span>  
  
-   <span data-ttu-id="b9da4-135">트랜잭션 보안을 OFF로 설정하면 해당 세션은 쿼럼을 필요로 하지 않고 비동기적으로 작동합니다(성능 우선 모드).</span><span class="sxs-lookup"><span data-stu-id="b9da4-135">If transaction safety is set to OFF, the session operates asynchronously (in high-performance mode) without requiring quorum.</span></span> <span data-ttu-id="b9da4-136">트랜잭션 보안을 해제할 때마다 미러링 모니터도 해제하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="b9da4-136">Whenever transaction safety is turned off, we strongly recommend also turning the witness off.</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="b9da4-137">각 파트너의 데이터베이스 트랜잭션 보안 설정은 [sys.database_mirroring](/sql/relational-databases/system-catalog-views/sys-database-mirroring-transact-sql) 카탈로그 뷰의 **mirroring_safety_level** 및 **mirroring_safety_level_desc** 열에 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="b9da4-137">The transaction safety setting of the database is recorded on each partner in the [sys.database_mirroring](/sql/relational-databases/system-catalog-views/sys-database-mirroring-transact-sql) catalog view in the **mirroring_safety_level** and **mirroring_safety_level_desc** columns.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="b9da4-138">관련 작업</span><span class="sxs-lookup"><span data-stu-id="b9da4-138">Related Tasks</span></span>  
  
-   [<span data-ttu-id="b9da4-139">Windows 인증을 사용하여 데이터베이스 미러링 모니터 추가&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="b9da4-139">Add a Database Mirroring Witness Using Windows Authentication &#40;Transact-SQL&#41;</span></span>](add-a-database-mirroring-witness-using-windows-authentication-transact-sql.md)  
  
-   [<span data-ttu-id="b9da4-140">데이터베이스 미러링 모니터 서버 추가 또는 바꾸기&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="b9da4-140">Add or Replace a Database Mirroring Witness &#40;SQL Server Management Studio&#41;</span></span>](../database-mirroring/add-or-replace-a-database-mirroring-witness-sql-server-management-studio.md)  
  
## <a name="see-also"></a><span data-ttu-id="b9da4-141">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b9da4-141">See Also</span></span>  
 <span data-ttu-id="b9da4-142">[ALTER DATABASE 데이터베이스 미러링&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring) </span><span class="sxs-lookup"><span data-stu-id="b9da4-142">[ALTER DATABASE Database Mirroring &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring) </span></span>  
 <span data-ttu-id="b9da4-143">[Transact-sql&#41;&#40;데이터베이스 미러링 세션에서 트랜잭션 보안 변경](change-transaction-safety-in-a-database-mirroring-session-transact-sql.md) </span><span class="sxs-lookup"><span data-stu-id="b9da4-143">[Change Transaction Safety in a Database Mirroring Session &#40;Transact-SQL&#41;](change-transaction-safety-in-a-database-mirroring-session-transact-sql.md) </span></span>  
 <span data-ttu-id="b9da4-144">[Transact-sql&#41;&#40;Windows 인증을 사용 하 여 데이터베이스 미러링 모니터 서버 추가](add-a-database-mirroring-witness-using-windows-authentication-transact-sql.md) </span><span class="sxs-lookup"><span data-stu-id="b9da4-144">[Add a Database Mirroring Witness Using Windows Authentication &#40;Transact-SQL&#41;](add-a-database-mirroring-witness-using-windows-authentication-transact-sql.md) </span></span>  
 [<span data-ttu-id="b9da4-145">데이터베이스 미러링 모니터 서버</span><span class="sxs-lookup"><span data-stu-id="b9da4-145">Database Mirroring Witness</span></span>](database-mirroring-witness.md)  
  
  
