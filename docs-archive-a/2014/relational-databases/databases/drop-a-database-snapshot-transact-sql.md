---
title: 데이터베이스 스냅샷 삭제(Transact-SQL) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- removing database snapshots
- deleting database snapshots
- database snapshots [SQL Server], deleting
ms.assetid: ad70ec97-d5fb-41aa-b72a-915e74b61b76
author: stevestein
ms.author: sstein
ms.openlocfilehash: e0d9d912a092e581fad7d3d53504309f63ba1806
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638827"
---
# <a name="drop-a-database-snapshot-transact-sql"></a><span data-ttu-id="db423-102">데이터베이스 스냅샷 삭제(Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="db423-102">Drop a Database Snapshot (Transact-SQL)</span></span>
  <span data-ttu-id="db423-103">데이터베이스 스냅샷을 삭제하면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 데이터베이스 스냅샷이 삭제되고 스냅샷에 사용된 스파스 파일도 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="db423-103">Dropping a database snapshot deletes the database snapshot from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and deletes the sparse files that are used by the snapshot.</span></span> <span data-ttu-id="db423-104">또한 데이터베이스 스냅샷에 대한 모든 사용자 연결이 종료됩니다.</span><span class="sxs-lookup"><span data-stu-id="db423-104">When you drop a database snapshot, all user connections to it are terminated.</span></span>  
  
## <a name="security"></a><span data-ttu-id="db423-105">보안</span><span class="sxs-lookup"><span data-stu-id="db423-105">Security</span></span>  
  
###  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="db423-106">권한</span><span class="sxs-lookup"><span data-stu-id="db423-106">Permissions</span></span>  
 <span data-ttu-id="db423-107">DROP DATABASE 권한을 가진 사용자는 누구든지 데이터베이스 스냅샷을 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db423-107">Any user with DROP DATABASE permissions can drop a database snapshot.</span></span>  
  
##  <a name="how-to-drop-a-database-snapshot-using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="db423-108">데이터베이스 스냅샷을 삭제하는 방법(Transact-SQL 사용)</span><span class="sxs-lookup"><span data-stu-id="db423-108">How to Drop a Database Snapshot (Using Transact-SQL)</span></span>  
 <span data-ttu-id="db423-109">**데이터베이스 스냅샷을 삭제하려면**</span><span class="sxs-lookup"><span data-stu-id="db423-109">**To drop a database snapshot**</span></span>  
  
1.  <span data-ttu-id="db423-110">삭제할 데이터베이스 스냅샷을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="db423-110">Identify the database snapshot that you want to drop.</span></span> <span data-ttu-id="db423-111">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 데이터베이스의 스냅샷을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db423-111">You can view the snapshots on a database in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="db423-112">자세한 내용은 [View a Database Snapshot &#40;SQL Server&#41;](view-a-database-snapshot-sql-server.md).</span><span class="sxs-lookup"><span data-stu-id="db423-112">For more information, see [View a Database Snapshot &#40;SQL Server&#41;](view-a-database-snapshot-sql-server.md).</span></span>  
  
2.  <span data-ttu-id="db423-113">삭제할 데이터베이스 스냅샷의 이름을 지정하여 [DROP DATABASE](/sql/t-sql/statements/drop-database-audit-specification-transact-sql) 문을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="db423-113">Issue a [DROP DATABASE](/sql/t-sql/statements/drop-database-audit-specification-transact-sql) statement, specifying the name of the database snapshot to be dropped.</span></span> <span data-ttu-id="db423-114">구문은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="db423-114">The syntax is as follows:</span></span>  
  
     <span data-ttu-id="db423-115">DROP DATABASE *database_snapshot_name* [ **,** ...*n* ]</span><span class="sxs-lookup"><span data-stu-id="db423-115">DROP DATABASE *database_snapshot_name* [ **,**...*n* ]</span></span>  
  
     <span data-ttu-id="db423-116">여기서 *database_snapshot_name* 은 삭제할 데이터베이스 스냅샷의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="db423-116">Where *database_snapshot_name* is the name of the database snapshot to be dropped.</span></span>  
  
####  <a name="example-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="db423-117">예(Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="db423-117">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="db423-118">이 예에서는 원본 데이터베이스에 영향을 주지 않고 SalesSnapshot0600이라는 데이터베이스 스냅샷을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="db423-118">This example drops a database snapshot named SalesSnapshot0600, without affecting the source database.</span></span>  
  
```  
DROP DATABASE SalesSnapshot0600 ;  
```  
  
 <span data-ttu-id="db423-119">SalesSnapshot0600에 대한 사용자 연결이 모두 종료되고 스냅샷에 사용되는 NTFS 파일 시스템 스파스 파일이 모두 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="db423-119">Any user connections to SalesSnapshot0600 are terminated, and all of the NTFS file system sparse files used by the snapshot are deleted.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="db423-120">데이터베이스 스냅샷이 사용하는 스파스 파일에 대한 자세한 내용은 [데이터베이스 스냅샷&#40;SQL Server&#41;](database-snapshots-sql-server.md)에서 데이터베이스의 스냅샷을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db423-120">For information about the use of sparse files by database snapshots, see [Database Snapshots &#40;SQL Server&#41;](database-snapshots-sql-server.md).</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="db423-121">관련 작업</span><span class="sxs-lookup"><span data-stu-id="db423-121">Related Tasks</span></span>  
  
-   [<span data-ttu-id="db423-122">데이터베이스 스냅샷 만들기&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="db423-122">Create a Database Snapshot &#40;Transact-SQL&#41;</span></span>](create-a-database-snapshot-transact-sql.md)  
  
-   [<span data-ttu-id="db423-123">데이터베이스 스냅샷 보기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="db423-123">View a Database Snapshot &#40;SQL Server&#41;</span></span>](view-a-database-snapshot-sql-server.md)  
  
-   [<span data-ttu-id="db423-124">데이터베이스를 데이터베이스 스냅샷으로 되돌리기</span><span class="sxs-lookup"><span data-stu-id="db423-124">Revert a Database to a Database Snapshot</span></span>](revert-a-database-to-a-database-snapshot.md)  
  

  
## <a name="see-also"></a><span data-ttu-id="db423-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="db423-125">See Also</span></span>  
 <span data-ttu-id="db423-126">[DROP DATABASE&#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-database-audit-specification-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="db423-126">[DROP DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-database-audit-specification-transact-sql) </span></span>  
 [<span data-ttu-id="db423-127">데이터베이스 스냅샷&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="db423-127">Database Snapshots &#40;SQL Server&#41;</span></span>](database-snapshots-sql-server.md)  
  
  
