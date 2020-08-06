---
title: MSSQLSERVER_1457 | Microsoft 문서
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 1457 (Database Engine error)
ms.assetid: 28434ba1-b033-4866-ab41-111fccef45a2
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c30ee6149c95d93bdaf1d2877f5fe1871a575ec1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653954"
---
# <a name="mssqlserver_1457"></a><span data-ttu-id="8d7fe-102">MSSQLSERVER_1457</span><span class="sxs-lookup"><span data-stu-id="8d7fe-102">MSSQLSERVER_1457</span></span>
    
## <a name="details"></a><span data-ttu-id="8d7fe-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="8d7fe-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8d7fe-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="8d7fe-104">Product Name</span></span>|<span data-ttu-id="8d7fe-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="8d7fe-105">SQL Server</span></span>|  
|<span data-ttu-id="8d7fe-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="8d7fe-106">Event ID</span></span>|<span data-ttu-id="8d7fe-107">1457</span><span class="sxs-lookup"><span data-stu-id="8d7fe-107">1457</span></span>|  
|<span data-ttu-id="8d7fe-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="8d7fe-108">Event Source</span></span>|<span data-ttu-id="8d7fe-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="8d7fe-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="8d7fe-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="8d7fe-110">Component</span></span>|<span data-ttu-id="8d7fe-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="8d7fe-111">SQLEngine</span></span>|  
|<span data-ttu-id="8d7fe-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="8d7fe-112">Symbolic Name</span></span>|<span data-ttu-id="8d7fe-113">DBM_PAGE_UNDO_PENDING</span><span class="sxs-lookup"><span data-stu-id="8d7fe-113">DBM_PAGE_UNDO_PENDING</span></span>|  
|<span data-ttu-id="8d7fe-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="8d7fe-114">Message Text</span></span>|<span data-ttu-id="8d7fe-115">미러 데이터베이스 '%.\*ls'의 동기화가 중단되어 데이터베이스가 일관성이 없는 상태가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="8d7fe-115">Synchronization of the mirror database, '%.\*ls', was interrupted, leaving the database in an inconsistent state.</span></span> <span data-ttu-id="8d7fe-116">ALTER DATABASE 명령이 실패했습니다.</span><span class="sxs-lookup"><span data-stu-id="8d7fe-116">The ALTER DATABASE command failed.</span></span> <span data-ttu-id="8d7fe-117">미러 데이터베이스가 다시 켜져 온라인 상태인지 확인한 다음 미러 서버 인스턴스를 다시 연결하여 미러 데이터베이스의 동기화를 완료하십시오.</span><span class="sxs-lookup"><span data-stu-id="8d7fe-117">Ensure that the mirror database is back up and online, and then reconnect the mirror server instance and allow the mirror database to finish synchronizing.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="8d7fe-118">설명</span><span class="sxs-lookup"><span data-stu-id="8d7fe-118">Explanation</span></span>  
 <span data-ttu-id="8d7fe-119">이 메시지는 ALTER DATABASE *database_name* SET PARTNER OFF 문이 실패했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="8d7fe-119">This messages indicates that the ALTER DATABASE *database_name* SET PARTNER OFF statement has failed.</span></span> <span data-ttu-id="8d7fe-120">데이터베이스 미러링을 제거하려는 시도가 실패하여 미러 데이터베이스의 동기화가 중단되었습니다.</span><span class="sxs-lookup"><span data-stu-id="8d7fe-120">The failed attempt to remove database mirroring interrupted synchronization of the mirror database.</span></span> <span data-ttu-id="8d7fe-121">데이터베이스가 일관성이 없는 상태에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d7fe-121">The database is in an inconsistent state.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="8d7fe-122">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="8d7fe-122">User Action</span></span>  
 <span data-ttu-id="8d7fe-123">이 오류를 해결하려면 다음 동작 중 하나를 수행하십시오.</span><span class="sxs-lookup"><span data-stu-id="8d7fe-123">To resolve this error, you can take either of the following actions:</span></span>  
  
-   <span data-ttu-id="8d7fe-124">미러 데이터베이스가 동기화되도록 미러 서버와 주 서버 간의 연결을 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="8d7fe-124">Restore contact between the mirror server and the principal server to allow for the mirror database to synchronize.</span></span>  
  
-   <span data-ttu-id="8d7fe-125">미러 데이터베이스를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="8d7fe-125">Drop the mirror database.</span></span>  
  
     <span data-ttu-id="8d7fe-126">미러 데이터베이스를 삭제한 후 백업에서 새 미러 데이터베이스를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d7fe-126">After you drop the mirror database, you can create a new mirror database from backups.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="8d7fe-127">SET PARTNER OFF 문이 실패한 후 미러링이 계속 활성화된 경우에만 미러 데이터베이스를 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d7fe-127">You can drop the mirror database when mirroring is still enabled only after a failed SET PARTNER OFF statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d7fe-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8d7fe-128">See Also</span></span>  
 <span data-ttu-id="8d7fe-129">[데이터베이스 미러링&#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="8d7fe-129">[Database Mirroring &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md) </span></span>  
 <span data-ttu-id="8d7fe-130">[ALTER DATABASE &#40;Transact-SQL &#41;](/sql/t-sql/statements/alter-database-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="8d7fe-130">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span></span>  
 <span data-ttu-id="8d7fe-131">[데이터베이스 미러링 설정&#40;SQL Server&#41;](../../database-engine/database-mirroring/setting-up-database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="8d7fe-131">[Setting Up Database Mirroring &#40;SQL Server&#41;](../../database-engine/database-mirroring/setting-up-database-mirroring-sql-server.md) </span></span>  
 <span data-ttu-id="8d7fe-132">[데이터베이스 미러링 제거&#40;SQL Server&#41;](../../database-engine/database-mirroring/removing-database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="8d7fe-132">[Removing Database Mirroring &#40;SQL Server&#41;](../../database-engine/database-mirroring/removing-database-mirroring-sql-server.md) </span></span>  
 [<span data-ttu-id="8d7fe-133">미러 데이터베이스의 미러링 준비&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="8d7fe-133">Prepare a Mirror Database for Mirroring &#40;SQL Server&#41;</span></span>](../../database-engine/database-mirroring/prepare-a-mirror-database-for-mirroring-sql-server.md)  
  
  
