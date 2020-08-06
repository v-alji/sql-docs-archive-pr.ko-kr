---
title: 데이터베이스를 복원하여 리소스 풀에 바인딩 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 0d20a569-8a27-409c-bcab-0effefb48013
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 0b518c93ca9d5e7157ceaa20d9548d7b6061017d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638773"
---
# <a name="restore-a-database-and-bind-it-to-a-resource-pool"></a><span data-ttu-id="87094-102">데이터베이스를 복원하여 리소스 풀에 바인딩</span><span class="sxs-lookup"><span data-stu-id="87094-102">Restore a Database and Bind it to a Resource Pool</span></span>
  <span data-ttu-id="87094-103">메모리 최적화 테이블이 포함된 데이터베이스를 복원하기에 충분한 메모리가 있더라도 최선의 구현 방법에 따라 데이터베이스를 명명된 리소스 풀에 바인딩하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="87094-103">Even though you have enough memory to restore a database with memory-optimized tables, you want to follow best practices and bind the database to a named resource pool.</span></span> <span data-ttu-id="87094-104">데이터베이스가 있어야 풀에 바인딩할 수 있기 때문에 데이터베이스를 복원하려면 여러 단계를 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="87094-104">Since the database must exist before you can bind it to the pool restoring your database is a multi-step process.</span></span> <span data-ttu-id="87094-105">이 항목에서는 각 단계를 안내합니다.</span><span class="sxs-lookup"><span data-stu-id="87094-105">This topic walks you through that process.</span></span>  
  
##  <a name="restore-with-norecovery"></a><span data-ttu-id="87094-106">NORECOVERY를 사용하여 복원</span><span class="sxs-lookup"><span data-stu-id="87094-106">Restore with NORECOVERY</span></span>  
 <span data-ttu-id="87094-107">데이터베이스를 복원할 때 NORECOVERY 를 사용하면 메모리를 사용하지 않고 데이터베이스가 만들어지고 디스크 이미지가 복원됩니다.</span><span class="sxs-lookup"><span data-stu-id="87094-107">When you restore a database, NORECOVERY causes the database to be created and the disk image restored without consuming memory.</span></span>  
  
```sql  
RESTORE DATABASE IMOLTP_DB   
   FROM DISK = 'C:\IMOLTP_test\IMOLTP_DB.bak'  
   WITH NORECOVERY  
```  
  
##  <a name="create-the-resource-pool"></a><span data-ttu-id="87094-108">리소스 풀 만들기</span><span class="sxs-lookup"><span data-stu-id="87094-108">Create the resource pool</span></span>  
 <span data-ttu-id="87094-109">다음 [!INCLUDE[tsql](../../includes/tsql-md.md)] 에서는 메모리의 50%를 사용할 수 있는 Pool_IMOLTP라는 리소스 풀을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="87094-109">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] creates a resource pool named Pool_IMOLTP with 50% of memory available for its use.</span></span>  <span data-ttu-id="87094-110">풀이 만들어진 후 Pool_IMOLTP를 포함하도록 리소스 관리자가 다시 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="87094-110">After the pool is created, the Resource Governor is reconfigured to include Pool_IMOLTP.</span></span>  
  
```sql  
CREATE RESOURCE POOL Pool_IMOLTP WITH (MAX_MEMORY_PERCENT = 50);  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
```  
  
##  <a name="bind-the-database-and-resource-pool"></a><span data-ttu-id="87094-111">데이터베이스와 리소스 풀 바인딩</span><span class="sxs-lookup"><span data-stu-id="87094-111">Bind the database and resource pool</span></span>  
 <span data-ttu-id="87094-112">시스템 함수 `sp_xtp_bind_db_resource_pool` 을 사용하여 리소스 풀에 데이터베이스를 바인딩합니다.</span><span class="sxs-lookup"><span data-stu-id="87094-112">Use the system function `sp_xtp_bind_db_resource_pool` to bind the database to the resource pool.</span></span> <span data-ttu-id="87094-113">이 함수는 데이터베이스 이름과 리소스 풀 이름의 2개의 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="87094-113">The function takes two parameters: the database name followed by the resource pool name.</span></span>  
  
 <span data-ttu-id="87094-114">다음 [!INCLUDE[tsql](../../includes/tsql-md.md)] 에서는 리소스 풀 Pool_IMOLTP와 데이터베이스 IMOLTP_DB의 바인딩을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="87094-114">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] defines a binding of the database IMOLTP_DB to the resource pool Pool_IMOLTP.</span></span> <span data-ttu-id="87094-115">다음 단계를 완료해야 바인딩이 유효해집니다.</span><span class="sxs-lookup"><span data-stu-id="87094-115">The binding does not become effective until you complete the next step.</span></span>  
  
```sql  
EXEC sp_xtp_bind_db_resource_pool 'IMOLTP_DB', 'Pool_IMOLTP'  
GO  
```  
  
##  <a name="restore-with-recovery"></a><span data-ttu-id="87094-116">RECOVERY를 사용하여 복원</span><span class="sxs-lookup"><span data-stu-id="87094-116">Restore with RECOVERY</span></span>  
 <span data-ttu-id="87094-117">복구를 사용하여 데이터베이스를 복원하면 데이터베이스가 온라인 상태가 되고 모든 데이터가 복원됩니다.</span><span class="sxs-lookup"><span data-stu-id="87094-117">When you restore the database with recovery the database is brought online and all the data restored.</span></span>  
  
```sql  
RESTORE DATABASE IMOLTP_DB   
   WITH RECOVERY  
```  
  
##  <a name="monitor-the-resource-pool-performance"></a><span data-ttu-id="87094-118">리소스 풀 성능 모니터링</span><span class="sxs-lookup"><span data-stu-id="87094-118">Monitor the resource pool performance</span></span>  
 <span data-ttu-id="87094-119">데이터베이스가 명명된 리소스 풀에 바인딩되고 복구를 통해 복원되면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], Resource Pool Stats 개체를 모니터링합니다.</span><span class="sxs-lookup"><span data-stu-id="87094-119">Once the database is bound to the named resource pool and restored with recovery, monitor the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], Resource Pool Stats Object.</span></span> <span data-ttu-id="87094-120">자세한 내용은 [SQL Server, Resource Pool Stats 개체](../performance-monitor/sql-server-resource-pool-stats-object.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="87094-120">For more information see [SQL Server, Resource Pool Stats Object](../performance-monitor/sql-server-resource-pool-stats-object.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87094-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="87094-121">See Also</span></span>  
 <span data-ttu-id="87094-122">[데이터베이스를 리소스 풀에 바인딩하는 방법에 대한 지침은](bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md) </span><span class="sxs-lookup"><span data-stu-id="87094-122">[Bind a Database with Memory-Optimized Tables to a Resource Pool](bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md) </span></span>  
 <span data-ttu-id="87094-123">[sys.sp_xtp_bind_db_resource_pool&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sys-sp-xtp-bind-db-resource-pool-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="87094-123">[sys.sp_xtp_bind_db_resource_pool &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sys-sp-xtp-bind-db-resource-pool-transact-sql) </span></span>  
 <span data-ttu-id="87094-124">[SQLServer, Resource Pool Stats 개체](../performance-monitor/sql-server-resource-pool-stats-object.md) </span><span class="sxs-lookup"><span data-stu-id="87094-124">[SQL Server, Resource Pool Stats Object](../performance-monitor/sql-server-resource-pool-stats-object.md) </span></span>  
 [<span data-ttu-id="87094-125">sys.dm_resource_governor_resource_pools</span><span class="sxs-lookup"><span data-stu-id="87094-125">sys.dm_resource_governor_resource_pools</span></span>](/sql/relational-databases/system-stored-procedures/sys-sp-xtp-unbind-db-resource-pool-transact-sql)  
  
  
