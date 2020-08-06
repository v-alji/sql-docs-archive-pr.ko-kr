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
- stopping database mirroring [SQL Server]
- removing database mirroring [SQL Server]
ms.assetid: 40c72091-8f03-4037-8b55-5e95309fe145
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 8044fcef9d9f9bfc1fb41c1faa17b76c827da5a2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87733071"
---
# <a name="removing-database-mirroring-sql-server"></a><span data-ttu-id="3faaa-102">데이터베이스 미러링 제거(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="3faaa-102">Removing Database Mirroring (SQL Server)</span></span>
  <span data-ttu-id="3faaa-103">데이터베이스 소유자는 언제든지 파트너에서 데이터베이스 미러링 세션을 수동으로 중지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3faaa-103">The database owner can manually stop a database mirroring session at any time, at either partner.</span></span>  
  
## <a name="impact-of-removing-mirroring"></a><span data-ttu-id="3faaa-104">미러링 제거의 영향</span><span class="sxs-lookup"><span data-stu-id="3faaa-104">Impact of Removing Mirroring</span></span>  
 <span data-ttu-id="3faaa-105">미러링을 제거하면 다음과 같은 결과가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="3faaa-105">When mirroring is removed, the following occurs:</span></span>  
  
-   <span data-ttu-id="3faaa-106">파트너 간의 관계 및 각 파트너와 미러링 모니터 서버 간의 관계가 영구적으로 해제됩니다(관계가 있는 경우).</span><span class="sxs-lookup"><span data-stu-id="3faaa-106">The relationship between the partners and between each partner and the witness breaks permanently, if any relationship exists.</span></span>  
  
     <span data-ttu-id="3faaa-107">세션이 중지될 때 파트너가 서로 통신하고 있으면 두 컴퓨터에서 해당 관계가 즉시 해제됩니다.</span><span class="sxs-lookup"><span data-stu-id="3faaa-107">If the partners are communicating with each other when the session is stopped, their relationship is immediately broken on both computers.</span></span> <span data-ttu-id="3faaa-108">파트너가 서로 통신하고 있지 않으면(세션 중지 시 데이터베이스는 DISCONNECTED 상태임) 미러링이 중지된 파트너에서 해당 관계가 즉시 해제됩니다. 상대 파트너가 다시 연결을 시도할 경우 데이터베이스 미러링 세션이 종료되었음을 확인하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3faaa-108">If the partners are not communicating (the database is in a DISCONNECTED state at the time of stopping), the relationship is broken immediately on the partner from which mirroring is stopped; when the other partner tries to reconnect, it discovers that the database mirroring session has ended.</span></span>  
  
-   <span data-ttu-id="3faaa-109">세션을 일시 중지하는 경우와 달리 미러링 세션에 대한 정보가 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="3faaa-109">Information about the mirroring session is dropped, unlike when pausing a session.</span></span> <span data-ttu-id="3faaa-110">미러링은 주 데이터베이스와 미러 데이터베이스에서 모두 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="3faaa-110">Mirroring is removed on both the principal database and the mirror database.</span></span> <span data-ttu-id="3faaa-111">**sys.databases**에서 **mirroring_state** 열과 다른 모든 미러링 열은 NULL로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="3faaa-111">In **sys.databases**, the **mirroring_state** column and all other mirroring columns are set to NULL.</span></span> <span data-ttu-id="3faaa-112">자세한 내용은 [sys.database_mirroring&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-mirroring-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3faaa-112">For more information, see [sys.database_mirroring &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-mirroring-transact-sql).</span></span>  
  
-   <span data-ttu-id="3faaa-113">각 파트너 서버 인스턴스는 별도의 데이터베이스 복사본으로 남겨집니다.</span><span class="sxs-lookup"><span data-stu-id="3faaa-113">Each partner server instance is left with a separate copy of the database.</span></span>  
  
-   <span data-ttu-id="3faaa-114">미러 데이터베이스가 RESTORE WITH NORECOVERY를 사용하여 생성되었기 때문에 RESTORING 상태( **sys.databases** 의 **state**열 참조)로 남게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3faaa-114">The mirror database is left in the RESTORING state (see the **state** column of **sys.databases**), because the mirror database was created by using RESTORE WITH NORECOVERY.</span></span> <span data-ttu-id="3faaa-115">따라서 이전 미러 데이터베이스를 삭제하거나 WITH RECOVERY를 사용하여 복원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3faaa-115">At this point, you can drop the former mirror database or restore it using WITH RECOVERY.</span></span> <span data-ttu-id="3faaa-116">데이터베이스를 복구할 때 새로운 복구 분기 지점에서 복구를 시작하므로 이전 주 데이터베이스에서 갈라져 나옵니다.</span><span class="sxs-lookup"><span data-stu-id="3faaa-116">When you recover the database, it will have diverged from the former principal database because the recovery starts a new recovery fork.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3faaa-117">세션을 중지한 후에 미러링을 계속하려면 데이터베이스 미러링 세션을 새로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3faaa-117">To continue mirroring after stopping a session, you must establish a new database mirroring session.</span></span> <span data-ttu-id="3faaa-118">미러링을 중지한 후에 로그 백업을 만들 경우 이 로그 백업을 미러 데이터베이스에 적용한 후에 미러링을 다시 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3faaa-118">If you create a log backup after stopping mirroring, you must apply it to the mirror database before restarting mirroring.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="3faaa-119">관련 작업</span><span class="sxs-lookup"><span data-stu-id="3faaa-119">Related Tasks</span></span>  
 <span data-ttu-id="3faaa-120">**데이터베이스 미러링을 제거하려면**</span><span class="sxs-lookup"><span data-stu-id="3faaa-120">**To remove database mirroring**</span></span>  
  
-   [<span data-ttu-id="3faaa-121">데이터베이스 미러링 제거&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="3faaa-121">Remove Database Mirroring &#40;SQL Server&#41;</span></span>](database-mirroring-sql-server.md)  
  
 <span data-ttu-id="3faaa-122">**데이터베이스 미러링을 시작하려면**</span><span class="sxs-lookup"><span data-stu-id="3faaa-122">**To start database mirroring**</span></span>  
  
-   [<span data-ttu-id="3faaa-123">Windows 인증을 사용하여 데이터베이스 미러링 세션 구성&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="3faaa-123">Establish a Database Mirroring Session Using Windows Authentication &#40;SQL Server Management Studio&#41;</span></span>](establish-database-mirroring-session-windows-authentication.md)  
  
-   [<span data-ttu-id="3faaa-124">Windows 인증을 사용하여 데이터베이스 미러링 세션 구성&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="3faaa-124">Establish a Database Mirroring Session Using Windows Authentication &#40;Transact-SQL&#41;</span></span>](database-mirroring-establish-session-windows-authentication.md)  
  

  
## <a name="see-also"></a><span data-ttu-id="3faaa-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3faaa-125">See Also</span></span>  
 <span data-ttu-id="3faaa-126">[ALTER DATABASE 데이터베이스 미러링&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring) </span><span class="sxs-lookup"><span data-stu-id="3faaa-126">[ALTER DATABASE Database Mirroring &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring) </span></span>  
 <span data-ttu-id="3faaa-127">[데이터베이스 미러링&#40;SQL Server&#41;](database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="3faaa-127">[Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span></span>  
 <span data-ttu-id="3faaa-128">[데이터베이스 미러링 일시 중지 및 재개&#40;SQL Server&#41;](pausing-and-resuming-database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="3faaa-128">[Pausing and Resuming Database Mirroring &#40;SQL Server&#41;](pausing-and-resuming-database-mirroring-sql-server.md) </span></span>  
 [<span data-ttu-id="3faaa-129">sys.databases&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="3faaa-129">sys.databases &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql)  
  
  
