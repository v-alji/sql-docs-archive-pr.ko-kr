---
title: 메모리 액세스에 최적화된 테이블이 있는 데이터베이스를 리소스 풀에 연결 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: f222b1d5-d2fa-4269-8294-4575a0e78636
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: cd163c5d3bc7a2cd9051b8d37b8127a1cc88c30b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661654"
---
# <a name="bind-a-database-with-memory-optimized-tables-to-a-resource-pool"></a><span data-ttu-id="67d20-102">메모리 액세스에 최적화된 테이블이 있는 데이터베이스를 리소스 풀에 바인딩</span><span class="sxs-lookup"><span data-stu-id="67d20-102">Bind a Database with Memory-Optimized Tables to a Resource Pool</span></span>
  <span data-ttu-id="67d20-103">리소스 풀은 관리할 수 있는 물리적 리소스의 하위 집합을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="67d20-103">A resource pool represents a subset of physical resources that can be governed.</span></span> <span data-ttu-id="67d20-104">기본적으로 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스는 기본 리소스 풀의 리소스에 바인딩되고 이 리소스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="67d20-104">By default, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases are bound to and consume the resources of the default resource pool.</span></span> <span data-ttu-id="67d20-105">하나 이상의 메모리 최적화 테이블에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 리소스를 사용하지 않고 다른 메모리 사용자가 메모리 최적화 테이블에 필요한 메모리를 사용하지 않게 하려면 별도의 리소스 풀을 만들어 메모리 최적화 테이블이 있는 데이터베이스의 메모리 사용을 관리해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="67d20-105">To protect [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] from having its resources consumed by one or more memory-optimized tables, and to prevent other memory users from consuming memory needed by memory-optimized tables, you should create a separate resource pool to manage memory consumption for the database with memory-optimized tables.</span></span>  
  
 <span data-ttu-id="67d20-106">하나의 리소스 풀에서만 데이터베이스를 바인딩할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67d20-106">A database can be bound on only one resource pool.</span></span> <span data-ttu-id="67d20-107">하지만 동일한 풀에 여러 데이터베이스를 바인딩할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67d20-107">However, you can bind multiple databases to the same pool.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="67d20-108">에서는 메모리 최적화 테이블을 리소스 풀에 바인딩할 수 있지만 이렇게 하는 것은 아무 효과도 없습니다.</span><span class="sxs-lookup"><span data-stu-id="67d20-108">allows binding a database without memory-optimized tables to a resource pool but it has no effect.</span></span> <span data-ttu-id="67d20-109">나중에 데이터베이스에 메모리 최적화 테이블을 만들려면 명명된 리소스 풀에 데이터베이스를 바인딩합니다.</span><span class="sxs-lookup"><span data-stu-id="67d20-109">You may want to bind a database to a named resource pool if, in future, you may want to create memory-optimized tables in the database.</span></span>  
  
 <span data-ttu-id="67d20-110">데이터베이스를 리소스 풀에 바인딩하려면 먼저 데이터베이스와 리소스 풀이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="67d20-110">Before you can bind a database to a resource pool both the database and the resource pool must exist.</span></span> <span data-ttu-id="67d20-111">다음에 데이터베이스를 온라인 상태로 전환할 때 바인딩이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="67d20-111">The binding takes effect the next time the database is brought online.</span></span> <span data-ttu-id="67d20-112">자세한 내용은 [Database States](../databases/database-states.md) 을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="67d20-112">See [Database States](../databases/database-states.md) for more information.</span></span>  
  
 <span data-ttu-id="67d20-113">리소스 풀에 대한 자세한 내용은 [Resource Governor Resource Pool](../resource-governor/resource-governor-resource-pool.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="67d20-113">For information about resource pools, see [Resource Governor Resource Pool](../resource-governor/resource-governor-resource-pool.md).</span></span>  
  
  
## <a name="create-the-database-and-resource-pool"></a><span data-ttu-id="67d20-114">데이터베이스 및 리소스 풀 만들기</span><span class="sxs-lookup"><span data-stu-id="67d20-114">Create the database and resource pool</span></span>  
 <span data-ttu-id="67d20-115">어떤 순서로든 데이터베이스와 리소스 풀을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67d20-115">You can create the database and resource pool in any order.</span></span> <span data-ttu-id="67d20-116">중요한 점은 데이터베이스를 리소스 풀에 바인딩하기 전에 데이터베이스와 리소스 풀이 모두 있는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="67d20-116">What matters is that they both exist prior to binding the database to the resource pool.</span></span>  
  
### <a name="create-the-database"></a><span data-ttu-id="67d20-117">데이터베이스 만들기</span><span class="sxs-lookup"><span data-stu-id="67d20-117">Create the database</span></span>  
 <span data-ttu-id="67d20-118">다음 [!INCLUDE[tsql](../../includes/tsql-md.md)]은 하나 이상의 메모리 최적화 테이블이 포함되는 IMOLTP_DB라는 데이터베이스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="67d20-118">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] creates a database named IMOLTP_DB which will contain one or more memory-optimized tables.</span></span> <span data-ttu-id="67d20-119">이 명령을 실행하기 전에 \<driveAndPath> 경로가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="67d20-119">The path \<driveAndPath> must exist prior to running this command.</span></span>  
  
```sql  
CREATE DATABASE IMOLTP_DB  
GO  
ALTER DATABASE IMOLTP_DB ADD FILEGROUP IMOLTP_DB_fg CONTAINS MEMORY_OPTIMIZED_DATA  
ALTER DATABASE IMOLTP_DB ADD FILE( NAME = 'IMOLTP_DB_fg' , FILENAME = 'c:\data\IMOLTP_DB_fg') TO FILEGROUP IMOLTP_DB_fg;  
GO  
```  
  
### <a name="determine-the-minimum-value-for-min_memory_percent-and-max_memory_percent"></a><span data-ttu-id="67d20-120">MIN_MEMORY_PERCENT 및 MAX_MEMORY_PERCENT의 최소값 결정</span><span class="sxs-lookup"><span data-stu-id="67d20-120">Determine the minimum value for MIN_MEMORY_PERCENT and MAX_MEMORY_PERCENT</span></span>  
 <span data-ttu-id="67d20-121">메모리 최적화 테이블에 필요한 메모리를 결정한 후에는 필요한 사용 가능 메모리 비율을 결정하고 해당 값 이상으로 메모리 비율을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="67d20-121">Once you determine the memory needs for your memory-optimized tables, you need to determine what percentage of available memory you need, and set the memory percentages to that value or higher.</span></span>  
  
 <span data-ttu-id="67d20-122">**예제:**  </span><span class="sxs-lookup"><span data-stu-id="67d20-122">**Example:** </span></span>  
<span data-ttu-id="67d20-123">이 예에서는 메모리 최적화 테이블 및 인덱스에 16GB의 메모리가 필요하며,</span><span class="sxs-lookup"><span data-stu-id="67d20-123">For this example we will assume that from your calculations you determined that your memory-optimized tables and indexes need 16 GB of memory.</span></span> <span data-ttu-id="67d20-124">32GB의 메모리를 사용할 수 있게 커밋했다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="67d20-124">Assume that you have 32 GB of memory committed for your use.</span></span>  
  
 <span data-ttu-id="67d20-125">얼핏 보기에는 MIN_MEMORY_PERCENT와 MAX_MEMORY_PERCENT를 50(16은 32의 50%)으로 설정하면 될 것 같습니다.</span><span class="sxs-lookup"><span data-stu-id="67d20-125">At first glance it could seem that you need to set MIN_MEMORY_PERCENT and MAX_MEMORY_PERCENT to 50 (16 is 50% of 32).</span></span>  <span data-ttu-id="67d20-126">그러나 이렇게 설정하면 메모리 최적화 테이블에서 사용할 수 있는 메모리가 부족합니다.</span><span class="sxs-lookup"><span data-stu-id="67d20-126">However, that would not give your memory-optimized tables sufficient memory.</span></span> <span data-ttu-id="67d20-127">아래 표([메모리 최적화 테이블 및 인덱스에 사용 가능한 메모리 비율](#percent-of-memory-available-for-memory-optimized-tables-and-indexes))에서 커밋된 메모리가 32GB인 경우 이 중 80%는 메모리 최적화 테이블과 인덱스에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67d20-127">Looking at the table below ([Percent of memory available for memory-optimized tables and indexes](#percent-of-memory-available-for-memory-optimized-tables-and-indexes)) we see that if there is 32 GB of committed memory, only 80% of that is available for memory-optimized tables and indexes.</span></span>  <span data-ttu-id="67d20-128">따라서 커밋된 메모리가 아니라 사용 가능한 메모리를 기준으로 최소 및 최대 비율을 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="67d20-128">Therefore, we calculate the min and max percentages based upon the available memory, not the committed memory.</span></span>  
  
 `memoryNeedeed = 16`   
 `memoryCommitted = 32`   
 `availablePercent = 0.8`   
 `memoryAvailable = memoryCommitted * availablePercent`   
 `percentNeeded = memoryNeeded / memoryAvailable`  
  
 <span data-ttu-id="67d20-129">실수 연결:</span><span class="sxs-lookup"><span data-stu-id="67d20-129">Plugging in real numbes:</span></span>   
`percentNeeded = 16 / (32 * 0.8) = 16 / 25.6 = 0.625`  
  
 <span data-ttu-id="67d20-130">따라서 메모리 최적화 테이블 및 인덱스의 16GB 요구 사항을 충족하려면 사용 가능한 메모리의 62.5% 이상이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="67d20-130">Thus you need at least 62.5% of the available memory to meet the 16 GB requirement of your memory-optimized tables and indexes.</span></span>  <span data-ttu-id="67d20-131">MIN_MEMORY_PERCENT 맟 MAX_MEMORY_PERCENT 값은 정수여야 하므로 63% 이상으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="67d20-131">Since the values for MIN_MEMORY_PERCENT and MAX_MEMORY_PERCENT must be integers, we set them to at least 63%.</span></span>  
  
### <a name="create-a-resource-pool-and-configure-memory"></a><span data-ttu-id="67d20-132">리소스 풀 만들기 및 메모리 구성</span><span class="sxs-lookup"><span data-stu-id="67d20-132">Create a resource pool and configure memory</span></span>  
 <span data-ttu-id="67d20-133">메모리 최적화 테이블의 메모리를 구성할 때 용량 계획은 MAX_MEMORY_PERCENT가 아니라 MIN_MEMORY_PERCENT를 기준으로 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="67d20-133">When configuring memory for memory-optimized tables, the capacity planning should be done based on MIN_MEMORY_PERCENT, not on MAX_MEMORY_PERCENT.</span></span>  <span data-ttu-id="67d20-134">MIN_MEMORY_PERCENT 및 MAX_MEMORY_PERCENT에 대한 자세한 내용은 [ALTER RESOURCE POOL&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-resource-pool-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="67d20-134">See [ALTER RESOURCE POOL &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-resource-pool-transact-sql) for information on MIN_MEMORY_PERCENT and MAX_MEMORY_PERCENT.</span></span> <span data-ttu-id="67d20-135">이렇게 하면 MIN_MEMORY_PERCENT로 인해 다른 리소스 풀에 대한 메모리 압력이 발생하여 메모리가 확실히 적용되므로 메모리 최적화 테이블의 메모리 가용성을 보다 효율적으로 예측할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67d20-135">This provides more predictable memory availability for memory-optimized tables as MIN_MEMORY_PERCENT causes memory pressure to other resource pools to make sure it is honored.</span></span> <span data-ttu-id="67d20-136">메모리를 사용할 수 있고 OOM(메모리 부족) 조건을 방지할 수 있도록 하려면 MIN_MEMORY_PERCENT 및 MAX_MEMORY_PERCENT 값이 동일해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="67d20-136">To ensure that memory is available and help avoid out-of-memory conditions, the values for MIN_MEMORY_PERCENT and MAX_MEMORY_PERCENT should be the same.</span></span> <span data-ttu-id="67d20-137">커밋된 메모리의 양에 따라 메모리 최적화 테이블에 사용 가능한 메모리의 비율은 아래 [메모리 최적화 테이블 및 인덱스에 사용 가능한 메모리 비율](#percent-of-memory-available-for-memory-optimized-tables-and-indexes) 을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="67d20-137">See [Percent of memory available for memory-optimized tables and indexes](#percent-of-memory-available-for-memory-optimized-tables-and-indexes) below for the percent of memory available for memory-optimized tables based on the amount of committed memory.</span></span>  
  
 <span data-ttu-id="67d20-138">VM 환경에서 작업하는 경우에 대한 자세한 내용은 [모범 사례: VM 환경에서 메모리 내 OLTP 사용](../../database-engine/using-in-memory-oltp-in-a-vm-environment.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="67d20-138">See [Best Practices: Using In-Memory OLTP in a VM environment](../../database-engine/using-in-memory-oltp-in-a-vm-environment.md) for more information when working in a VM environment.</span></span>  
  
 <span data-ttu-id="67d20-139">다음 [!INCLUDE[tsql](../../includes/tsql-md.md)] 코드에서는 메모리의 절반을 사용할 수 있는 Pool_IMOLTP라는 리소스 풀을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="67d20-139">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] code creates a resource pool named Pool_IMOLTP with half of the memory available for its use.</span></span>  <span data-ttu-id="67d20-140">풀이 만들어진 후 Pool_IMOLTP를 포함하도록 리소스 관리자가 다시 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="67d20-140">After the pool is created Resource Governor is reconfigured to include Pool_IMOLTP.</span></span>  
  
```sql  
-- set MIN_MEMORY_PERCENT and MAX_MEMORY_PERCENT to the same value  
CREATE RESOURCE POOL Pool_IMOLTP   
  WITH   
    ( MIN_MEMORY_PERCENT = 63,   
    MAX_MEMORY_PERCENT = 63 );  
GO  
  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
```  
  
## <a name="bind-the-database-to-the-pool"></a><span data-ttu-id="67d20-141">풀에 데이터베이스 바인딩</span><span class="sxs-lookup"><span data-stu-id="67d20-141">Bind the database to the pool</span></span>  
 <span data-ttu-id="67d20-142">시스템 함수 `sp_xtp_bind_db_resource_pool` 을 사용하여 리소스 풀에 데이터베이스를 바인딩합니다.</span><span class="sxs-lookup"><span data-stu-id="67d20-142">Use the system function `sp_xtp_bind_db_resource_pool` to bind the database to the resource pool.</span></span> <span data-ttu-id="67d20-143">이 함수는 데이터베이스 이름과 리소스 풀 이름의 2개의 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="67d20-143">The function takes two parameters: the database name and the resource pool name.</span></span>  
  
 <span data-ttu-id="67d20-144">다음 [!INCLUDE[tsql](../../includes/tsql-md.md)] 에서는 리소스 풀 Pool_IMOLTP와 데이터베이스 IMOLTP_DB의 바인딩을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="67d20-144">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] defines a binding of the database IMOLTP_DB to the resource pool Pool_IMOLTP.</span></span> <span data-ttu-id="67d20-145">데이터베이스를 온라인 상태로 전환할 때까지 바인딩이 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="67d20-145">The binding does not become effective until you bring the database online.</span></span>  
  
```sql  
EXEC sp_xtp_bind_db_resource_pool 'IMOLTP_DB', 'Pool_IMOLTP'  
GO  
```  
  
 <span data-ttu-id="67d20-146">시스템 함수 sp_xtp_bind_db_resourece_pool은 database_name과 pool_name이라는 두 개의 문자열 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="67d20-146">The system function sp_xtp_bind_db_resourece_pool takes two string parameters: database_name and pool_name.</span></span>  
  
## <a name="confirm-the-binding"></a><span data-ttu-id="67d20-147">바인딩 확인</span><span class="sxs-lookup"><span data-stu-id="67d20-147">Confirm the binding</span></span>  
 <span data-ttu-id="67d20-148">IMOLTP_DB의 리소스 풀 ID에 주의하여 바인딩을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="67d20-148">Confirm the binding, noting the resource pool id for IMOLTP_DB.</span></span> <span data-ttu-id="67d20-149">값이 NULL이면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="67d20-149">It should not be NULL.</span></span>  
  
```sql  
SELECT d.database_id, d.name, d.resource_pool_id  
FROM sys.databases d  
GO  
```  
  
## <a name="make-the-binding-effective"></a><span data-ttu-id="67d20-150">바인딩 적용</span><span class="sxs-lookup"><span data-stu-id="67d20-150">Make the binding effective</span></span>  
 <span data-ttu-id="67d20-151">바인딩을 리소스 풀에 바인딩한 후 바인딩을 적용하려면 데이터베이스를 오프라인 상태로 만들었다가 다시 온라인 상태로 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="67d20-151">You must take the database offline and back online after binding it to the resource pool for binding to take effect.</span></span> <span data-ttu-id="67d20-152">데이터베이스가 다른 풀에 바인딩된 경우 이전 리소스 풀에서 할당된 메모리가 제거되고 이제 데이터베이스로 새로 바인딩된 리소스 풀에서 메모리 최적화 테이블과 인덱스에 대한 메모리 할당이 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="67d20-152">If your database was bound to an a different pool earlier, this removes the allocated memory from the previous resource pool and memory allocations for your memory-optimized table and indexes will now come from the resource pool newly bound with the database.</span></span>  
  
```sql  
USE master  
GO  
  
ALTER DATABASE IMOLTP_DB SET OFFLINE  
GO  
ALTER DATABASE IMOLTP_DB SET ONLINE  
GO  
  
USE IMOLTP_DB  
GO  
```  
  
 <span data-ttu-id="67d20-153">이제 데이터베이스가 리소스 풀에 바인딩됩니다.</span><span class="sxs-lookup"><span data-stu-id="67d20-153">And now, the database is bound to the resource pool.</span></span>  
  
## <a name="change-min-memory-percent-and-max-memory-percent-on-an-existing-pool"></a><span data-ttu-id="67d20-154">기존 풀에서 최소 메모리% 및 최대 메모리 비율 변경</span><span class="sxs-lookup"><span data-stu-id="67d20-154">Change MIN MEMORY PERCENT and MAX MEMORY PERCENT on an existing pool</span></span>  
 <span data-ttu-id="67d20-155">서버에 메모리를 더 추가하거나 메모리 최적화 테이블에 필요한 메모리 양이 변경되면 MIN_MEMORY_PERCENT 및 MAX_MEMORY_PERCENT 값을 수정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="67d20-155">If you add additional memory to the server or the amount of memory needed for your memory-optimized tables changes, you may need to alter the value of MIN_MEMORY_PERCENT and MAX_MEMORY_PERCENT.</span></span> <span data-ttu-id="67d20-156">다음 단계에서는 리소스 풀에서 MIN_MEMORY_PERCENT 및 MAX_MEMORY_PERCENT의 값을 변경하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="67d20-156">The following steps show you how to alter the value of MIN_MEMORY_PERCENT and MAX_MEMORY_PERCENT on a resource pool.</span></span> <span data-ttu-id="67d20-157">MIN_MEMORY_PERCENT 및 MAX_MEMORY_PERCENT에 사용할 값에 대한 지침은 아래 섹션을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="67d20-157">See the section below, for guidance on what values to use for MIN_MEMORY_PERCENT and MAX_MEMORY_PERCENT.</span></span>  <span data-ttu-id="67d20-158">자세한 내용은 [모범 사례: VM 환경에서 메모리 내 OLTP 사용](../../database-engine/using-in-memory-oltp-in-a-vm-environment.md) 항목을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="67d20-158">See the topic [Best Practices: Using In-Memory OLTP in a VM environment](../../database-engine/using-in-memory-oltp-in-a-vm-environment.md) for more information.</span></span>  
  
1.  <span data-ttu-id="67d20-159">`ALTER RESOURCE POOL` 을 사용해서 MIN_MEMORY_PERCENT 및 MAX_MEMORY_PERCENT 값을 모두 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="67d20-159">Use `ALTER RESOURCE POOL` to change the value of both MIN_MEMORY_PERCENT and MAX_MEMORY_PERCENT.</span></span>  
  
2.  <span data-ttu-id="67d20-160">`ALTER RESURCE GOVERNOR` 를 사용하여 새 값으로 리소스 관리자를 다시 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="67d20-160">Use `ALTER RESURCE GOVERNOR` to reconfigure the Resource Governor with the new values.</span></span>  
  
 <span data-ttu-id="67d20-161">**예제 코드**</span><span class="sxs-lookup"><span data-stu-id="67d20-161">**Sample Code**</span></span>  
  
```sql  
ALTER RESOURCE POOL Pool_IMOLTP  
WITH  
     ( MIN_MEMORY_PERCENT = 70,  
       MAX_MEMORY_PERCENT = 70 )   
GO  
  
-- reconfigure the Resource Governor  
ALTER RESOURCE GOVERNOR RECONFIGURE  
GO  
```  
  
## <a name="percent-of-memory-available-for-memory-optimized-tables-and-indexes"></a><span data-ttu-id="67d20-162">메모리 최적화 테이블 및 인덱스에 사용 가능한 메모리 비율</span><span class="sxs-lookup"><span data-stu-id="67d20-162">Percent of memory available for memory-optimized tables and indexes</span></span>  
 <span data-ttu-id="67d20-163">메모리 최적화 테이블과 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 작업을 동일한 리소스 풀에 매핑하면 리소스 관리자는 풀 사용자가 풀 사용에서 충돌을 일으키지 않도록 [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] 사용에 대한 내부 임계값을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="67d20-163">If you map a database with memory-optimized tables and a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] workload to the same resource pool, the Resource Governor sets an internal threshold for [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] use so that the users of the pool do not have conflicts over pool usage.</span></span> <span data-ttu-id="67d20-164">일반적으로 [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] 사용에 대한 임계값은 풀의 약 80%입니다.</span><span class="sxs-lookup"><span data-stu-id="67d20-164">Generally speaking, the threshold for [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] use is about 80% of the pool.</span></span> <span data-ttu-id="67d20-165">다음 표에서는 다양한 메모리 크기에 대한 실제 임계값을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="67d20-165">The following table shows actual thresholds for various memory sizes.</span></span>  
  
 <span data-ttu-id="67d20-166">[!INCLUDE[hek_2](../../../includes/hek-2-md.md)] 데이터베이스의 전용 리소스 풀을 만드는 경우 행 버전과 데이터 증가율을 고려한 후 메모리 내 테이블에 필요한 물리적 메모리 양을 추정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="67d20-166">When you create a dedicated resource pool for the [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] database, you need to estimate how much physical memory you need for the in-memory tables after accounting for row versions and data growth.</span></span> <span data-ttu-id="67d20-167">필요한 메모리를 추정했으면 DMV `sys.dm_os_sys_info`에서 ‘committed_target_kb’ 열에 반영된 대로 SQL 인스턴스의 커밋 대상 메모리 비율을 사용하여 리소스 풀을 만듭니다([sys.dm_os_sys_info](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-sys-info-transact-sql) 참조).</span><span class="sxs-lookup"><span data-stu-id="67d20-167">Once estimate the memory needed, you create a resource pool with a percent of the commit target memory for SQL Instance as reflected by column 'committed_target_kb' in the DMV `sys.dm_os_sys_info` (see [sys.dm_os_sys_info](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-sys-info-transact-sql)).</span></span> <span data-ttu-id="67d20-168">예를 들어, 인스턴스에 사용할 수 있는 총 메모리의 40%로 리소스 풀 P1을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67d20-168">For example, you can create a resource pool P1 with 40% of the total memory available to the instance.</span></span> <span data-ttu-id="67d20-169">이 40%에서 [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] 엔진은 더 적은 비율을 사용하여 [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] 데이터를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="67d20-169">Out of this 40%, the [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] engine gets a smaller percent to store [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] data.</span></span>  <span data-ttu-id="67d20-170">이는 [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] 에서 이 풀의 메모리를 모두 사용하지 않도록 하기 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="67d20-170">This is done to make sure [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] does not consume all the memory from this pool.</span></span>  <span data-ttu-id="67d20-171">이 비율 값은 대상에 커밋된 메모리에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="67d20-171">This value of the smaller percent depends upon the Target committed Memory.</span></span> <span data-ttu-id="67d20-172">다음 테이블은 OOM 오류가 발생하기 전 리소스 풀(명명된 또는 기본값)의 [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] 데이터베이스에서 사용할 수 있는 메모리에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="67d20-172">The following table describes memory available to [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] database in a resource pool (named or default) before an OOM error is raised.</span></span>  
  
|<span data-ttu-id="67d20-173">대상에 커밋된 메모리</span><span class="sxs-lookup"><span data-stu-id="67d20-173">Target Committed Memory</span></span>|<span data-ttu-id="67d20-174">메모리 내 테이블에서 사용할 수 있는 비율</span><span class="sxs-lookup"><span data-stu-id="67d20-174">Percent available for in-memory tables</span></span>|  
|-----------------------------|---------------------------------------------|  
|<span data-ttu-id="67d20-175"><= 8GB</span><span class="sxs-lookup"><span data-stu-id="67d20-175"><= 8 GB</span></span>|<span data-ttu-id="67d20-176">70%</span><span class="sxs-lookup"><span data-stu-id="67d20-176">70%</span></span>|  
|<span data-ttu-id="67d20-177"><= 16GB</span><span class="sxs-lookup"><span data-stu-id="67d20-177"><= 16 GB</span></span>|<span data-ttu-id="67d20-178">75%</span><span class="sxs-lookup"><span data-stu-id="67d20-178">75%</span></span>|  
|<span data-ttu-id="67d20-179"><= 32GB</span><span class="sxs-lookup"><span data-stu-id="67d20-179"><= 32 GB</span></span>|<span data-ttu-id="67d20-180">80%</span><span class="sxs-lookup"><span data-stu-id="67d20-180">80%</span></span>|  
|<span data-ttu-id="67d20-181">\<= 96GB</span><span class="sxs-lookup"><span data-stu-id="67d20-181">\<= 96 GB</span></span>|<span data-ttu-id="67d20-182">85%</span><span class="sxs-lookup"><span data-stu-id="67d20-182">85%</span></span>|  
|<span data-ttu-id="67d20-183">>96GB</span><span class="sxs-lookup"><span data-stu-id="67d20-183">>96 GB</span></span>|<span data-ttu-id="67d20-184">90%</span><span class="sxs-lookup"><span data-stu-id="67d20-184">90%</span></span>|  
  
 <span data-ttu-id="67d20-185">예를 들어, ‘대상에 커밋된 메모리’가 100GB인 경우 메모리 최적화 테이블과 인덱스에 60GB의 메모리가 필요한 것으로 추정한 다음, MAX_MEMORY_PERCENT = 67(60GB의 필요량/0.90 = 66.667GB – 67GB로 반올림됨. 67GB/100GB의 설치량 = 67%)의 리소스 풀을 만들어 [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] 개체에 필요한 60GB를 확보하도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67d20-185">For example, if your 'target committed memory' is 100 GB, and you estimate your memory-optimized tables and indexes need 60GBof memory, then you can create a resource pool with MAX_MEMORY_PERCENT = 67 (60GB needed / 0.90 = 66.667GB - round up to 67GB; 67GB / 100GB installed = 67%) to ensure that your [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] objects have the 60GB they need.</span></span>  
  
 <span data-ttu-id="67d20-186">데이터베이스가 명명된 리소스 풀에 바인딩되면 다음 쿼리를 사용하여 다른 리소스 풀 전반의 메모리 할당량을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="67d20-186">Once a database has been bound to a named resource pool, use the following query to see memory allocations across different resource pools.</span></span>  
  
```sql  
SELECT pool_id  
     , Name  
     , min_memory_percent  
     , max_memory_percent  
     , max_memory_kb/1024 AS max_memory_mb  
     , used_memory_kb/1024 AS used_memory_mb   
     , target_memory_kb/1024 AS target_memory_mb  
   FROM sys.dm_resource_governor_resource_pools  
```  
  
 <span data-ttu-id="67d20-187">이 샘플 출력은 리소스 풀(PoolIMOLTP)에서 메모리 최적화 개체가 가져온 메모리가 1356MB이고 상한이 2307MB임을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="67d20-187">This sample output shows that the memory taken by memory-optimized objects is 1356 MB in resource pool, PoolIMOLTP, with an upper bound of 2307 MB.</span></span> <span data-ttu-id="67d20-188">이 상한은 사용자와 이 풀에 매핑된 시스템 메모리 최적화 개체에서 가져올 수 있는 총 메모리를 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="67d20-188">This upper bound controls the total memory that can be taken by user and system memory-optimized objects mapped to this pool.</span></span>  
  
 <span data-ttu-id="67d20-189">**샘플 출력** </span><span class="sxs-lookup"><span data-stu-id="67d20-189">**Sample Output** </span></span>  
<span data-ttu-id="67d20-190">다음은 위에서 만든 데이터베이스 및 테이블의 결과입니다.</span><span class="sxs-lookup"><span data-stu-id="67d20-190">This output is from the database and tables we created above.</span></span>  
  
```  
pool_id     Name        min_memory_percent max_memory_percent max_memory_mb used_memory_mb target_memory_mb  
----------- ----------- ------------------ ------------------ ------------- -------------- ----------------   
1           internal    0                  100                3845          125            3845  
2           default     0                  100                3845          32             3845  
259         PoolIMOLTP 0                  100                3845          1356           2307  
```  
  
 <span data-ttu-id="67d20-191">자세한 내용은 [sys.dm_resource_governor_resource_pools(Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-resource-governor-resource-pools-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="67d20-191">For more information see [sys.dm_resource_governor_resource_pools (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-resource-governor-resource-pools-transact-sql).</span></span>  
  
 <span data-ttu-id="67d20-192">데이터베이스를 명명된 리소스 풀에 바인딩하지 않으면 ‘기본’ 풀에 바인딩됩니다.</span><span class="sxs-lookup"><span data-stu-id="67d20-192">If you do not bind your database to a named resource pool, it is bound to the 'default' pool.</span></span> <span data-ttu-id="67d20-193">기본 리소스 풀은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 대다수의 다른 할당에 사용되므로 DMV sys.dm_resource_governor_resource_pools를 사용하여 원하는 데이터베이스에 대해 메모리 최적화 테이블에서 사용하는 메모리를 모니터링할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="67d20-193">Since default resource pool is used by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] for most other allocations, you will not be able to monitor memory consumed by memory-optimized tables using the DMV sys.dm_resource_governor_resource_pools accurately for the database of interest.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67d20-194">참고 항목</span><span class="sxs-lookup"><span data-stu-id="67d20-194">See Also</span></span>  
 <span data-ttu-id="67d20-195">[sys.sp_xtp_bind_db_resource_pool&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sys-sp-xtp-bind-db-resource-pool-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="67d20-195">[sys.sp_xtp_bind_db_resource_pool &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sys-sp-xtp-bind-db-resource-pool-transact-sql) </span></span>  
 <span data-ttu-id="67d20-196">[sys.sp_xtp_unbind_db_resource_pool&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sys-sp-xtp-unbind-db-resource-pool-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="67d20-196">[sys.sp_xtp_unbind_db_resource_pool &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sys-sp-xtp-unbind-db-resource-pool-transact-sql) </span></span>  
 <span data-ttu-id="67d20-197">[리소스 관리자](../resource-governor/resource-governor.md) </span><span class="sxs-lookup"><span data-stu-id="67d20-197">[Resource Governor](../resource-governor/resource-governor.md) </span></span>  
 <span data-ttu-id="67d20-198">[리소스 관리자 리소스 풀](../resource-governor/resource-governor-resource-pool.md) </span><span class="sxs-lookup"><span data-stu-id="67d20-198">[Resource Governor Resource Pool](../resource-governor/resource-governor-resource-pool.md) </span></span>  
 <span data-ttu-id="67d20-199">[리소스 풀 만들기](../resource-governor/create-a-resource-pool.md) </span><span class="sxs-lookup"><span data-stu-id="67d20-199">[Create a Resource Pool](../resource-governor/create-a-resource-pool.md) </span></span>  
 <span data-ttu-id="67d20-200">[리소스 풀 설정 변경](../resource-governor/change-resource-pool-settings.md) </span><span class="sxs-lookup"><span data-stu-id="67d20-200">[Change Resource Pool Settings](../resource-governor/change-resource-pool-settings.md) </span></span>  
 [<span data-ttu-id="67d20-201">리소스 풀 삭제</span><span class="sxs-lookup"><span data-stu-id="67d20-201">Delete a Resource Pool</span></span>](../resource-governor/delete-a-resource-pool.md)  
  
  
