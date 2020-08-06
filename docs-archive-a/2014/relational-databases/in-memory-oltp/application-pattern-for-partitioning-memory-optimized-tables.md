---
title: 메모리 액세스에 최적화된 테이블 분할을 위한 애플리케이션 패턴 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 3f867763-a8e6-413a-b015-20e9672cc4d1
author: rothja
ms.author: jroth
ms.openlocfilehash: d2633cdf1b631a1d9209adf26f4773e27c4c44c4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647005"
---
# <a name="application-pattern-for-partitioning-memory-optimized-tables"></a><span data-ttu-id="4fe64-102">메모리 액세스에 최적화된 테이블 분할을 위한 애플리케이션 패턴</span><span class="sxs-lookup"><span data-stu-id="4fe64-102">Application Pattern for Partitioning Memory-Optimized Tables</span></span>
  [!INCLUDE[hek_2](../../includes/hek-2-md.md)]<span data-ttu-id="4fe64-103">는 디스크에서 자주 액세스하지 않는 데이터를 처리하는 동안 제한된 양의 활성 데이터를 메모리 최적화 테이블에 유지하는 패턴을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="4fe64-103">supports a pattern where a limited amount of active data is kept in a memory-optimized table, while less-frequently accessed data is processed on disk.</span></span> <span data-ttu-id="4fe64-104">일반적으로, 이는 `datetime` 키를 기준으로 데이터가 저장되는 시나리오가 될 것입니다.</span><span class="sxs-lookup"><span data-stu-id="4fe64-104">Typically, this would be a scenario where data is stored based on a `datetime` key.</span></span>  
  
 <span data-ttu-id="4fe64-105">분할된 테이블과 메모리 최적화 테이블을 공통 스키마로 유지하여 분할된 테이블을 메모리 최적화 테이블로 에뮬레이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4fe64-105">You can emulate partitioned tables with memory-optimized tables by maintaining a partitioned table and a memory-optimized table with a common schema.</span></span> <span data-ttu-id="4fe64-106">현재 데이터는 메모리 최적화 테이블에 삽입되고 업데이트되는 반면, 자주 액세스하지 않는 데이터는 기존의 분할된 테이블에 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="4fe64-106">Current data would be inserted and updated in the memory-optimized table, while less-frequently accessed data would be maintained in the traditional partitioned table.</span></span>  
  
 <span data-ttu-id="4fe64-107">활성 데이터가 메모리 최적화 테이블에 있음을 알고 있는 애플리케이션은 고유하게 컴파일된 저장 프로시저를 사용하여 데이터에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4fe64-107">An application that knows that the active data is in a memory-optimized table can use natively compiled stored procedures to access the data.</span></span> <span data-ttu-id="4fe64-108">전체 데이터에 액세스해야 하거나 어떤 테이블에 관련 데이터가 유지되는지 모를 수 있는 작업은 해석된 [!INCLUDE[tsql](../../includes/tsql-md.md)]을 사용하여 메모리 최적화 테이블을 분할된 테이블과 조인합니다.</span><span class="sxs-lookup"><span data-stu-id="4fe64-108">Operations that need to access the entire span of data, or which may not know which table holds relevant data, use interpreted [!INCLUDE[tsql](../../includes/tsql-md.md)] to join the memory-optimized table with the partitioned table.</span></span>  
  
 <span data-ttu-id="4fe64-109">이 파티션 전환은 다음과 같이 설명됩니다.</span><span class="sxs-lookup"><span data-stu-id="4fe64-109">This partition switch is described as follows:</span></span>  
  
-   <span data-ttu-id="4fe64-110">메모리 내 OLTP 테이블의 데이터를 준비 테이블에 삽입합니다. 가능하면 구분 날짜를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="4fe64-110">Insert data from the In-Memory OLTP table into a staging table, possibly using a cutoff date.</span></span>  
  
-   <span data-ttu-id="4fe64-111">메모리 최적화 테이블에서 같은 데이터를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="4fe64-111">Delete the same data from the memory-optimized table.</span></span>  
  
-   <span data-ttu-id="4fe64-112">준비 테이블을 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="4fe64-112">Swap in the staging table.</span></span>  
  
-   <span data-ttu-id="4fe64-113">활성 파티션을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="4fe64-113">Add the active partition.</span></span>  
  
 <span data-ttu-id="4fe64-114">![파티션 전환.](../../database-engine/media/hekaton-partitioned-tables.gif "파티션 전환.")</span><span class="sxs-lookup"><span data-stu-id="4fe64-114">![Partition switch.](../../database-engine/media/hekaton-partitioned-tables.gif "Partition switch.")</span></span>  
<span data-ttu-id="4fe64-115">활성 데이터 유지 관리</span><span class="sxs-lookup"><span data-stu-id="4fe64-115">Active Data Maintenance</span></span>  
  
 <span data-ttu-id="4fe64-116">데이터 삭제와 준비 테이블 전환 사이의 시간 중에 누락된 데이터 쿼리가 수행되지 않도록 하려면 활성 주문 삭제로 시작되는 작업을 유지 관리 시간 중에 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4fe64-116">The actions starting with Deleting ActiveOrders need to be done during a maintenance window to avoid queries missing data during the time between deleting data and switching in the staging table.</span></span>  
  
 <span data-ttu-id="4fe64-117">관련 샘플을 보려면 [애플리케이션 수준 분할](application-level-partitioning.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4fe64-117">For a related sample, see [Application-Level Partitioning](application-level-partitioning.md).</span></span>  
  
## <a name="code-sample"></a><span data-ttu-id="4fe64-118">코드 예제</span><span class="sxs-lookup"><span data-stu-id="4fe64-118">Code Sample</span></span>  
 <span data-ttu-id="4fe64-119">다음 예제에서는 분할된 디스크 기반 테이블과 함께 메모리 최적화 테이블을 사용하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="4fe64-119">The following sample shows how to use a memory-optimized table with a partitioned disk-based table.</span></span> <span data-ttu-id="4fe64-120">자주 사용되는 데이터는 메모리에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="4fe64-120">Frequently-used data is stored in memory.</span></span> <span data-ttu-id="4fe64-121">데이터를 디스크에 저장하려면 새 파티션을 만들고 분할된 테이블에 데이터를 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="4fe64-121">To save the data to disk, create a new partition and copy the data to the partitioned table.</span></span>  
  
 <span data-ttu-id="4fe64-122">이 예제의 첫 번째 부분에서는 데이터베이스와 필요한 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="4fe64-122">The first part of this sample creates the database and necessary objects.</span></span> <span data-ttu-id="4fe64-123">예제의 두 번째 부분에서는 메모리 최적화 테이블에서 분할된 테이블로 데이터를 이동하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="4fe64-123">The second part of the sample shows how to move data from a memory-optimized table into a partitioned table.</span></span>  
  
```sql  
CREATE DATABASE partitionsample;  
GO  
  
-- enable for In-Memory OLTP - change file path as needed  
ALTER DATABASE partitionsample ADD FILEGROUP partitionsample_mod CONTAINS MEMORY_OPTIMIZED_DATA  
ALTER DATABASE partitionsample ADD FILE( NAME = 'partitionsample_mod' , FILENAME = 'c:\data\partitionsample_mod') TO FILEGROUP partitionsample_mod;  
GO  
  
USE partitionsample;  
GO  
  
-- frequently used portion of the SalesOrders - memory-optimized  
  
CREATE TABLE dbo.SalesOrders_hot (  
   so_id INT IDENTITY PRIMARY KEY NONCLUSTERED,  
   cust_id INT NOT NULL,  
   so_date DATETIME2 NOT NULL INDEX ix_date NONCLUSTERED,  
   so_total MONEY NOT NULL,  
   INDEX ix_date_total NONCLUSTERED (so_date desc, so_total desc)  
) WITH (MEMORY_OPTIMIZED=ON)  
GO  
  
-- cold portion of the SalesOrders - partitioned disk-based table  
CREATE PARTITION FUNCTION [ByDatePF](datetime2) AS RANGE RIGHT   
   FOR VALUES();  
GO  
  
CREATE PARTITION SCHEME [ByDateRange]   
   AS PARTITION [ByDatePF]   
   ALL TO ([PRIMARY]);  
GO  
  
CREATE TABLE dbo.SalesOrders_cold (  
   so_id INT NOT NULL,  
   cust_id INT NOT NULL,  
   so_date DATETIME2 NOT NULL,  
   so_total MONEY NOT NULL,  
   CONSTRAINT PK_SalesOrders_cold PRIMARY KEY (so_id, so_date),  
   INDEX ix_date_total NONCLUSTERED (so_date desc, so_total desc)  
) ON [ByDateRange](so_date)  
GO  
  
-- table for temporary partitions  
CREATE TABLE dbo.SalesOrders_cold_staging (  
   so_id INT NOT NULL,  
   cust_id INT NOT NULL,  
   so_date datetime2 NOT NULL,  
   so_total MONEY NOT NULL,  
   CONSTRAINT PK_SalesOrders_cold_staging PRIMARY KEY (so_id, so_date),  
   INDEX ix_date_total NONCLUSTERED (so_date desc, so_total desc),  
   CONSTRAINT CHK_SalesOrders_cold_staging CHECK (so_date >= '1900-01-01')  
)  
GO  
  
-- aggregate view of the hot and cold data  
CREATE VIEW dbo.SalesOrders  
AS SELECT so_id,  
   cust_id,  
   so_date,  
   so_total,  
   1 AS 'is_hot'  
   FROM dbo.SalesOrders_hot  
   UNION ALL  
   SELECT so_id,  
          cust_id,  
          so_date,  
          so_total,  
          0 AS 'is_hot'  
          FROM dbo.SalesOrders_cold;  
GO  
  
-- move all sales orders up to the split date to cold storage  
CREATE PROCEDURE dbo.usp_SalesOrdersOffloadToCold @splitdate datetime2  
   AS  
   BEGIN  
      BEGIN TRANSACTION;  
      -- create new heap based on the hot data to be moved to cold storage  
      INSERT INTO dbo.SalesOrders_cold_staging WITH( TABLOCKX)  
      SELECT so_id , cust_id , so_date , so_total  
         FROM dbo.SalesOrders_hot WITH ( serializable)  
         WHERE so_date <= @splitdate;  
  
      -- remove moved data  
      DELETE FROM dbo.SalesOrders_hot WITH( SERIALIZABLE)  
         WHERE so_date <= @splitdate;  
  
      -- update partition function, and switch in new partition  
      ALTER PARTITION SCHEME [ByDateRange] NEXT USED [PRIMARY];  
  
      DECLARE @p INT = ( SELECT MAX( partition_number) FROM sys.partitions WHERE object_id = OBJECT_ID( 'dbo.SalesOrders_cold'));  
      EXEC sp_executesql N'alter table dbo.SalesOrders_cold_staging  
         SWITCH TO dbo.SalesOrders_cold partition @i' , N'@i int' , @i = @p;  
  
      ALTER PARTITION FUNCTION [ByDatePF]()  
      SPLIT RANGE( @splitdate);  
  
      -- modify constraint on staging table to align with new partition  
      ALTER TABLE dbo.SalesOrders_cold_staging DROP CONSTRAINT CHK_SalesOrders_cold_staging;  
  
      DECLARE @s nvarchar( 100) = CONVERT( nvarchar( 100) , @splitdate , 121);  
      DECLARE @sql nvarchar( 1000) = N'alter table dbo.SalesOrders_cold_staging   
         add constraint CHK_SalesOrders_cold_staging check (so_date > ''' + @s + ''')';  
      PRINT @sql;  
      EXEC sp_executesql @sql;  
  
      COMMIT;  
END;  
GO  
  
-- insert sample values in the hot table  
INSERT INTO dbo.SalesOrders_hot VALUES(1,SYSDATETIME(), 1);   
GO  
  
INSERT INTO dbo.SalesOrders_hot VALUES(1, SYSDATETIME(), 1);  
GO  
  
INSERT INTO dbo.SalesOrders_hot VALUES(1, SYSDATETIME(), 1);  
GO  
  
-- verify contents of the table  
SELECT *  FROM dbo.SalesOrders;  
GO  
  
-- offload all sales orders to date to cold storage  
DECLARE  @t datetime2 = SYSDATETIME();  
EXEC dbo.usp_SalesOrdersOffloadToCold @t;  
  
-- verify contents of the tables  
SELECT * FROM dbo.SalesOrders;  
GO  
  
-- verify partitions  
SELECT OBJECT_NAME( object_id) , * FROM sys.dm_db_partition_stats ps  
   WHERE object_id = OBJECT_ID( 'dbo.SalesOrders_cold');  
  
-- insert more rows in the hot table  
INSERT INTO dbo.SalesOrders_hot VALUES(2, SYSDATETIME(), 1);  
GO  
  
INSERT INTO dbo.SalesOrders_hot VALUES(2, SYSDATETIME(), 1);  
GO  
  
INSERT INTO dbo.SalesOrders_hot VALUES(2, SYSDATETIME(), 1);  
GO  
  
-- verify contents of the tables  
SELECT * FROM dbo.SalesOrders;  
GO  
  
-- offload all sales orders to date to cold storage  
DECLARE @t datetime2 = SYSDATETIME();  
EXEC dbo.usp_SalesOrdersOffloadToCold @t;  
  
-- verify contents of the tables  
SELECT * FROM dbo.SalesOrders;  
GO  
  
-- verify partitions  
SELECT OBJECT_NAME( object_id) , partition_number , row_count  FROM sys.dm_db_partition_stats ps  
  WHERE object_id = OBJECT_ID( 'dbo.SalesOrders_cold') AND index_id = 1;  
```  
  
## <a name="see-also"></a><span data-ttu-id="4fe64-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4fe64-124">See Also</span></span>  
 [<span data-ttu-id="4fe64-125">메모리 최적화 테이블</span><span class="sxs-lookup"><span data-stu-id="4fe64-125">Memory-Optimized Tables</span></span>](memory-optimized-tables.md)  
  
  
