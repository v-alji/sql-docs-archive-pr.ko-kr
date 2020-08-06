---
title: 데이터베이스 미러링 및 데이터베이스 스냅샷(SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- database mirroring [SQL Server], interoperability
- snapshots [SQL Server database snapshots], database mirroring
- database snapshots [SQL Server], database mirroring
ms.assetid: 0bf1be90-7ce4-484c-aaa7-f8a782f57c5f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 9df0b74270280bf2315c6a35a80d4b009b75a908
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648570"
---
# <a name="database-mirroring-and-database-snapshots-sql-server"></a><span data-ttu-id="8c14d-102">데이터베이스 미러링 및 데이터베이스 스냅샷(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="8c14d-102">Database Mirroring and Database Snapshots (SQL Server)</span></span>
  <span data-ttu-id="8c14d-103">가용성 목적으로 유지 관리 중인 미러 데이터베이스를 활용하여 보고 작업을 오프로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8c14d-103">You can take advantage of a mirror database that you are maintaining for availability purposes to offload reporting.</span></span> <span data-ttu-id="8c14d-104">미러 데이터베이스를 보고 용도로 사용하려면 미러 데이터베이스에서 데이터베이스 스냅샷을 만들고 클라이언트 연결 요청을 가장 최근의 스냅샷으로 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8c14d-104">To use a mirror database for reporting, you can create a database snapshot on the mirror database and direct client connection requests to the most recent snapshot.</span></span> <span data-ttu-id="8c14d-105">데이터베이스 스냅샷은 스냅샷이 만들어진 시점에 존재하던 원본 데이터베이스의 정적, 읽기 전용, 트랜잭션 일치 스냅샷입니다.</span><span class="sxs-lookup"><span data-stu-id="8c14d-105">A database snapshot is a static, read-only, transaction-consistent snapshot of its source database as it existed at the moment of the snapshot's creation.</span></span> <span data-ttu-id="8c14d-106">미러 데이터베이스에서 데이터베이스 스냅샷을 만들려면 데이터베이스가 동기화된 미러링 상태여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8c14d-106">To create a database snapshot on a mirror database, the database must be in the synchronized mirroring state.</span></span>  
  
 <span data-ttu-id="8c14d-107">미러 데이터베이스와 달리 데이터베이스 스냅샷은 클라이언트에서 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8c14d-107">Unlike the mirror database itself, a database snapshot is accessible to clients.</span></span> <span data-ttu-id="8c14d-108">미러 서버가 주 서버와 통신하고 있는 한, 보고 클라이언트를 스냅샷에 연결하도록 지시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8c14d-108">As long as the mirror server is communicating with the principal server, you can direct reporting clients to connect to a snapshot.</span></span> <span data-ttu-id="8c14d-109">데이터베이스 스냅샷은 정적이기 때문에 새로운 데이터를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8c14d-109">Note that because a database snapshot is static, new data is not available.</span></span> <span data-ttu-id="8c14d-110">사용자가 비교적 최근 데이터를 사용하려면 정기적으로 새 데이터베이스 스냅샷을 만들고 애플리케이션에서 들어오는 클라이언트 연결을 최신 스냅샷으로 지정하도록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8c14d-110">To make relatively recent data available to your users, you must create a new database snapshot periodically and have applications direct incoming client connections to the newest snapshot.</span></span>  
  
 <span data-ttu-id="8c14d-111">새 데이터베이스 스냅샷은 거의 비어 있지만 시간이 경과하면서 점점 더 많은 데이터베이스 페이지가 처음으로 업데이트됨에 따라 확장됩니다.</span><span class="sxs-lookup"><span data-stu-id="8c14d-111">A new database snapshot is almost empty, but it grows over time as more and more database pages are updated for the first time.</span></span> <span data-ttu-id="8c14d-112">데이터베이스의 모든 스냅샷이 이렇게 증분 방식으로 증가하기 때문에 각 데이터베이스 스냅샷에서 일반 데이터베이스만큼 많은 리소스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="8c14d-112">Because every snapshot on a database grows incrementally in this way, each database snapshot consumes as much resources as a normal database.</span></span> <span data-ttu-id="8c14d-113">미러 서버와 주 서버의 구성에 따라 미러 데이터베이스에 있는 데이터베이스 스냅샷의 수가 너무 많으면 주 데이터베이스의 성능이 느려질 수 있으므로</span><span class="sxs-lookup"><span data-stu-id="8c14d-113">Depending on the configurations of the mirror server and principal server, having an excessive number of database snapshots on a mirror database might decrease performance on the principal database.</span></span> <span data-ttu-id="8c14d-114">몇 개의 최근 스냅샷만 미러 데이터베이스에 보관하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="8c14d-114">Therefore, we recommend that you keep only a few relatively recent snapshots on your mirror databases.</span></span> <span data-ttu-id="8c14d-115">대체 스냅샷을 만든 후 들어오는 쿼리를 새 스냅샷으로 리디렉션하고 현재 쿼리가 완료된 후에는 이전 스냅샷을 삭제해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8c14d-115">Typically, after you create a replacement snapshot, you should redirect incoming queries to the new snapshot and drop the earlier snapshot after any current queries complete.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8c14d-116">데이터베이스 스냅샷에 대한 자세한 내용은 [데이터베이스 스냅샷&#40;SQL Server&#41;](../../relational-databases/databases/database-snapshots-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8c14d-116">For more information about database snapshots, see [Database Snapshots &#40;SQL Server&#41;](../../relational-databases/databases/database-snapshots-sql-server.md).</span></span>  
  
 <span data-ttu-id="8c14d-117">역할이 전환되면 데이터베이스와 해당 스냅샷이 다시 시작되고 일시적으로 사용자와의 연결을 끊습니다.</span><span class="sxs-lookup"><span data-stu-id="8c14d-117">If role switching occurs, the database and its snapshots are restarted, temporarily disconnecting users.</span></span> <span data-ttu-id="8c14d-118">그런 후 데이터베이스 스냅샷은 자신이 만들어진 서버 인스턴스에서 새로운 주 데이터베이스가 되어 그대로 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="8c14d-118">Afterwards, the database snapshots remain on the server instance where they were created, which has become the new principal database.</span></span> <span data-ttu-id="8c14d-119">사용자는 장애 조치(Failover) 후에도 스냅샷을 계속 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8c14d-119">Users can continue to use the snapshots after the failover.</span></span> <span data-ttu-id="8c14d-120">그러나 이렇게 하면 새로운 주 서버에 추가 로드가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="8c14d-120">However, this places an additional load on the new principal server.</span></span> <span data-ttu-id="8c14d-121">환경에서 성능이 중요한 경우 새 미러 데이터베이스를 사용할 수 있게 되면 스냅샷을 만들어 클라이언트를 새 스냅샷으로 리디렉션하고 이전 미러 데이터베이스에서 모든 데이터베이스 스냅샷을 삭제하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="8c14d-121">If performance is a concern in your environment, we recommend that you create a snapshot on the new mirror database when it becomes available, redirect clients to the new snapshot, and drop all of the database snapshots from the former mirror database.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8c14d-122">확장이 용이한 전용 보고 솔루션의 경우에는 복제하십시오.</span><span class="sxs-lookup"><span data-stu-id="8c14d-122">For a dedicated reporting solution that scales out well, consider replication.</span></span> <span data-ttu-id="8c14d-123">자세한 내용은 [SQL Server Replication](../install-windows/install-sql-server-replication.md)을(를) 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8c14d-123">For more information, see [SQL Server Replication](../install-windows/install-sql-server-replication.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8c14d-124">예제</span><span class="sxs-lookup"><span data-stu-id="8c14d-124">Example</span></span>  
 <span data-ttu-id="8c14d-125">이 예에서는 미러된 데이터베이스의 스냅샷을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8c14d-125">This example creates snapshots on a mirrored database.</span></span>  
  
 <span data-ttu-id="8c14d-126">데이터베이스 미러링 세션에 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]데이터베이스가 있다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="8c14d-126">Assume that the database of a database mirroring session is [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].</span></span> <span data-ttu-id="8c14d-127">이 예에서는 `AdventureWorks` 드라이브에 있는 `F` 데이터베이스의 미러 복사본에 대해 3개의 데이터베이스 스냅샷을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8c14d-127">This example creates three database snapshots on the mirror copy of the `AdventureWorks` database, which resides on the `F` drive.</span></span> <span data-ttu-id="8c14d-128">스냅샷의 이름은 대략적인 생성 시간에 따라 각각 `AdventureWorks_0600`, `AdventureWorks_1200`및 `AdventureWorks_1800` 으로 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="8c14d-128">The snapshots are named `AdventureWorks_0600`, `AdventureWorks_1200`, and `AdventureWorks_1800` to identify their approximate creation times.</span></span>  
  
1.  <span data-ttu-id="8c14d-129">[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]미러의 첫 번째 데이터베이스 스냅샷을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8c14d-129">Create the first database snapshot on the mirror of [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].</span></span>  
  
    ```  
    CREATE DATABASE AdventureWorks_0600  
    ON (NAME = 'datafile', FILENAME = 'F:\AdventureWorks_0600.SNP')  
       AS SNAPSHOT OF AdventureWorks2012  
    ```  
  
2.  <span data-ttu-id="8c14d-130">[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]미러의 두 번째 데이터베이스 스냅샷을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8c14d-130">Create the second database snapshot on the mirror of [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].</span></span> <span data-ttu-id="8c14d-131">`AdventureWorks_0600` 사용자는 계속 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8c14d-131">Users who are still using `AdventureWorks_0600` can continue to use it.</span></span>  
  
    ```  
    CREATE DATABASE AdventureWorks_1200  
    ON (NAME = 'datafile', FILENAME = 'F:\AdventureWorks_1200.SNP')  
       AS SNAPSHOT OF AdventureWorks2012  
    ```  
  
     <span data-ttu-id="8c14d-132">이 시점에서 프로그래밍 방식으로 새 클라이언트 연결을 최신 스냅샷으로 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8c14d-132">At this point, new client connections can be programmatically directed to the latest snapshot.</span></span>  
  
3.  <span data-ttu-id="8c14d-133">[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]미러의 세 번째 스냅샷을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8c14d-133">Create the third snapshot on the mirror [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].</span></span> <span data-ttu-id="8c14d-134">`AdventureWorks_0600` 또는 `AdventureWorks_1200` 사용자는 계속 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8c14d-134">Users who are still using `AdventureWorks_0600` or `AdventureWorks_1200` can continue to use them.</span></span>  
  
    ```  
    CREATE DATABASE AdventureWorks_1800  
    ON (NAME = 'datafile', FILENAME = 'F:\AdventureWorks_1800.SNP')  
        AS SNAPSHOT OF AdventureWorks2012  
    ```  
  
     <span data-ttu-id="8c14d-135">이 시점에서 프로그래밍 방식으로 새 클라이언트 연결을 최신 스냅샷으로 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8c14d-135">At this point, new client connections can be programmatically directed to the latest snapshot.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="8c14d-136">관련 작업</span><span class="sxs-lookup"><span data-stu-id="8c14d-136">Related Tasks</span></span>  
  
-   [<span data-ttu-id="8c14d-137">데이터베이스 스냅샷 만들기&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="8c14d-137">Create a Database Snapshot &#40;Transact-SQL&#41;</span></span>](../../relational-databases/databases/create-a-database-snapshot-transact-sql.md)  
  
-   [<span data-ttu-id="8c14d-138">데이터베이스 스냅샷 보기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="8c14d-138">View a Database Snapshot &#40;SQL Server&#41;</span></span>](../../relational-databases/databases/view-a-database-snapshot-sql-server.md)  
  
-   [<span data-ttu-id="8c14d-139">데이터베이스 스냅샷 삭제&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="8c14d-139">Drop a Database Snapshot &#40;Transact-SQL&#41;</span></span>](../../relational-databases/databases/drop-a-database-snapshot-transact-sql.md)  

  
## <a name="see-also"></a><span data-ttu-id="8c14d-140">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8c14d-140">See Also</span></span>  
 <span data-ttu-id="8c14d-141">[데이터베이스 스냅샷&#40;SQL Server&#41;](../../relational-databases/databases/database-snapshots-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="8c14d-141">[Database Snapshots &#40;SQL Server&#41;](../../relational-databases/databases/database-snapshots-sql-server.md) </span></span>  
 [<span data-ttu-id="8c14d-142">데이터베이스 미러링 세션에 클라이언트 연결&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="8c14d-142">Connect Clients to a Database Mirroring Session &#40;SQL Server&#41;</span></span>](connect-clients-to-a-database-mirroring-session-sql-server.md)  
  
  
