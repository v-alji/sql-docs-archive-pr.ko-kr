---
title: '데모: 메모리 내 OLTP 성능 향상 | Microsoft 문서'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: c6def45d-d2d4-4d24-8068-fab4cd94d8cc
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 4858e4c35263ab3dd1d9fdcf55a2b136dd8eeaf2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650977"
---
# <a name="demonstration-performance-improvement-of-in-memory-oltp"></a><span data-ttu-id="f9f20-102">데모: 메모리 내 OLTP의 성능 향상</span><span class="sxs-lookup"><span data-stu-id="f9f20-102">Demonstration: Performance Improvement of In-Memory OLTP</span></span>
  <span data-ttu-id="f9f20-103">이 예제는 메모리 최적화된 테이블과 디스크 기반 테이블에 대해 동일한 Transact-SQL 쿼리를 실행하는 경우 응답 시간의 차이를 비교하여 메모리 내 OLTP 사용 시 성능 향상을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="f9f20-103">This example shows performance improvements when using In-Memory OLTP by comparing differences in response times when running an identical Transact-SQL query against memory-optimized and traditional disk-based tables.</span></span> <span data-ttu-id="f9f20-104">또한 고유하게 컴파일된 저장 프로시저가 생성되고(동일한 쿼리를 기반으로) 고유하게 컴파일된 저장 프로시저로 메모리 최적화 테이블을 쿼리하는 경우 일반적으로 최고의 응답 시간을 갖는다는 것을 설명하기 위해 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="f9f20-104">Additionally, a natively-compiled stored procedure is also created (based on the same query) and then run to demonstrate that you typically get the best response times when querying a memory-optimized table with a natively-compiled stored procedure.</span></span> <span data-ttu-id="f9f20-105">이 샘플은 메모리 최적화 테이블에 포함된 데이터에 액세스 하는 경우 성능 향상의 한 가지 측면 즉, 삽입 수행 시 데이터 액세스 효율성만을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="f9f20-105">This sample only shows one aspect of performance improvements when accessing data in memory-optimized tables; data access efficiency when performing inserts.</span></span> <span data-ttu-id="f9f20-106">이 예제는 단일 스레드이며 메모리 내 OLTP의 동시성 이점을 활용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f9f20-106">This sample is single-threaded and does not take advantage of the concurrency benefits of In-Memory OLTP.</span></span> <span data-ttu-id="f9f20-107">동시성을 사용하는 작업에서는 더 큰 성능 향상이 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="f9f20-107">A workload that uses concurrency will see a greater performance gain.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f9f20-108">메모리 최적화 테이블을 보여 주는 다른 예제는 [SQL Server 2014 메모리 내 OLTP 예제](https://msftdbprodsamples.codeplex.com/releases/view/114491)에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f9f20-108">Another sample demonstrating memory-optimized tables is available at [SQL Server 2014 In-Memory OLTP Sample](https://msftdbprodsamples.codeplex.com/releases/view/114491).</span></span>  
  
 <span data-ttu-id="f9f20-109">이 샘플을 완료하려면 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="f9f20-109">To complete this sample you will perform the following:</span></span>  
  
1.  <span data-ttu-id="f9f20-110">**imoltp** 라는 데이터베이스를 만들고 메모리 내 OLTP를 사용하여 설정하려는 파일 세부 정보를 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="f9f20-110">Create a database named **imoltp** and alter its file details to set it up for using In-Memory OLTP.</span></span>  
  
2.  <span data-ttu-id="f9f20-111">샘플에 대한 데이터베이스 개체 즉, 세 테이블 및 고유하게 컴파일된 저장 프로시저를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f9f20-111">Create the database objects for our sample: three tables and a natively-compiled stored procedure.</span></span>  
  
3.  <span data-ttu-id="f9f20-112">다른 쿼리를 실행하고 각 쿼리에 대한 응답 시간을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="f9f20-112">Run the different queries and display the response times for each query.</span></span>  
  
 <span data-ttu-id="f9f20-113">예제에 대한 **imoltp** 데이터베이스를 설치하려면 우선 빈 폴더 **c:\imoltp_data**를 만든 후 다음 코드를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="f9f20-113">To setup the **imoltp** database for our example, first create an empty folder: **c:\imoltp_data**, and then run the following code:</span></span>  
  
```sql  
USE master  
GO  
  
-- Create a new database.  
CREATE DATABASE imoltp  
GO  
  
-- Prepare the database for In-Memory OLTP by  
-- adding a memory-optimized filegroup to the database.  
ALTER DATABASE imoltp ADD FILEGROUP imoltp_file_group  
    CONTAINS MEMORY_OPTIMIZED_DATA;  
  
-- Add a file (to hold the memory-optimized data) to the new filegroup.  
ALTER DATABASE imoltp ADD FILE (name='imoltp_file', filename='c:\imoltp_data\imoltp_file')  
    TO FILEGROUP imoltp_file_group;  
GO  
  
```  
  
 <span data-ttu-id="f9f20-114">그 후, 다음 코드를 실행하여 디스크 기반 테이블, 2개의 (2) 메모리 최적화 테이블, 다른 데이터 액세스 메서드를 보여주는데 사용될 고유하게 컴파일된 저장 프로시를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f9f20-114">Next, run the following code to create the disk-based table, two (2) memory-optimized tables, and the natively-compiled stored procedure that will be used to demonstrate the different data access methods:</span></span>  
  
```sql  
USE imoltp  
GO  
  
-- If the tables or stored procedure already exist, drop them to start clean.  
IF EXISTS (SELECT NAME FROM sys.objects WHERE NAME = 'DiskBasedTable')  
   DROP TABLE [dbo].[DiskBasedTable]  
GO  
  
IF EXISTS (SELECT NAME FROM sys.objects WHERE NAME = 'InMemTable')  
   DROP TABLE [dbo].[InMemTable]  
GO  
  
IF EXISTS (SELECT NAME FROM sys.objects  WHERE NAME = 'InMemTable2')  
   DROP TABLE [dbo].[InMemTable2]  
GO  
  
IF EXISTS (SELECT NAME FROM sys.objects  WHERE NAME = 'usp_InsertData')  
   DROP PROCEDURE [dbo].[usp_InsertData]  
GO  
  
-- Create a traditional disk-based table.  
CREATE TABLE [dbo].[DiskBasedTable] (  
  c1 INT NOT NULL PRIMARY KEY,  
  c2 NCHAR(48) NOT NULL  
)  
GO  
  
-- Create a memory-optimized table.  
CREATE TABLE [dbo].[InMemTable] (  
  c1 INT NOT NULL PRIMARY KEY NONCLUSTERED HASH WITH (BUCKET_COUNT=1000000),  
  c2 NCHAR(48) NOT NULL  
) WITH (MEMORY_OPTIMIZED=ON, DURABILITY = SCHEMA_AND_DATA);  
GO  
  
-- Create a 2nd memory-optimized table.  
CREATE TABLE [dbo].[InMemTable2] (  
  c1 INT NOT NULL PRIMARY KEY NONCLUSTERED HASH WITH (BUCKET_COUNT=1000000),  
  c2 NCHAR(48) NOT NULL  
) WITH (MEMORY_OPTIMIZED=ON, DURABILITY = SCHEMA_AND_DATA);  
GO  
  
-- Create a natively-compiled stored procedure.  
CREATE PROCEDURE [dbo].[usp_InsertData]   
  @rowcount INT,  
  @c NCHAR(48)  
  WITH NATIVE_COMPILATION, SCHEMABINDING, EXECUTE AS OWNER  
  AS   
  BEGIN ATOMIC   
  WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'us_english')  
  DECLARE @i INT = 1;  
  WHILE @i <= @rowcount  
  BEGIN  
    INSERT INTO [dbo].[inMemTable2](c1,c2) VALUES (@i, @c);  
    SET @i += 1;  
  END  
END  
GO  
  
```  
  
 <span data-ttu-id="f9f20-115">설치가 완료되고 데이터 액세스 메서드 사이의 성능을 비교하여 응답 시간을 표시하는 쿼리를 실행할 준비가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f9f20-115">The setup is complete and we are ready to execute the queries that will display the response times comparing the performance between the data access methods.</span></span>  
  
 <span data-ttu-id="f9f20-116">예제를 완료하려면 다음 코드를 여러 번 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="f9f20-116">To complete the example run the following code multiple times.</span></span> <span data-ttu-id="f9f20-117">초기 메모리 할당에 의해 부정적인 영향을 받는 첫 번째 실행의 결과를 무시합니다.</span><span class="sxs-lookup"><span data-stu-id="f9f20-117">Ignore the results from the first run which is negatively affected by initial memory allocation.</span></span>  
  
```sql  
SET STATISTICS TIME OFF;  
SET NOCOUNT ON;  
  
-- Delete data from all tables to reset the example.  
DELETE FROM [dbo].[DiskBasedTable]   
    WHERE [c1]>0  
GO  
DELETE FROM [dbo].[inMemTable]   
    WHERE [c1]>0  
GO  
DELETE FROM [dbo].[InMemTable2]   
    WHERE [c1]>0  
GO  
  
-- Declare parameters for the test queries.  
DECLARE @i INT = 1;  
DECLARE @rowcount INT = 100000;  
DECLARE @c NCHAR(48) = N'12345678901234567890123456789012345678';  
DECLARE @timems INT;  
DECLARE @starttime datetime2 = sysdatetime();  
  
-- Disk-based table queried with interpreted Transact-SQL.  
BEGIN TRAN  
  WHILE @I <= @rowcount  
  BEGIN  
    INSERT INTO [dbo].[DiskBasedTable](c1,c2) VALUES (@i, @c);  
    SET @i += 1;  
  END  
COMMIT  
  
SET @timems = datediff(ms, @starttime, sysdatetime());  
SELECT CAST(@timems AS VARCHAR(10)) + ' ms (disk-based table with interpreted Transact-SQL).';  
  
-- Memory-optimized table queried with interpreted Transact-SQL.  
SET @i = 1;  
SET @starttime = sysdatetime();  
  
BEGIN TRAN  
  WHILE @i <= @rowcount  
    BEGIN  
      INSERT INTO [dbo].[InMemTable](c1,c2) VALUES (@i, @c);  
      SET @i += 1;  
    END  
COMMIT  
  
SET @timems = datediff(ms, @starttime, sysdatetime());  
SELECT CAST(@timems AS VARCHAR(10)) + ' ms (memory-optimized table with interpreted Transact-SQL).';  
  
-- Memory-optimized table queried with a natively-compiled stored procedure.  
SET @starttime = sysdatetime();  
  
EXEC usp_InsertData @rowcount, @c;  
  
SET @timems = datediff(ms, @starttime, sysdatetime());  
SELECT CAST(@timems AS VARCHAR(10)) + ' ms (memory-optimized table with natively-compiled stored procedure).';  
  
```  
  
 <span data-ttu-id="f9f20-118">예상 결과는 메모리 최적화 테이블과 고유하게 컴파일된 저장 프로시저가 기존의 디스크 기반 테이블에 대해 실행되는 동일한 작업보다 지속적으로 빠른 응답 시간을 보여주는 실제 응답 시간을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="f9f20-118">The expected results provide actual response times showing how using memory-optimized tables and natively-compiled stored procedures typically provides consistently faster response times than the same workloads running against traditional disk-based tables.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9f20-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f9f20-119">See Also</span></span>  
 <span data-ttu-id="f9f20-120">[메모리 내 OLTP를 보여 주는 AdventureWorks 확장](../../database-engine/extensions-to-adventureworks-to-demonstrate-in-memory-oltp.md) </span><span class="sxs-lookup"><span data-stu-id="f9f20-120">[Extensions to AdventureWorks to Demonstrate In-Memory OLTP](../../database-engine/extensions-to-adventureworks-to-demonstrate-in-memory-oltp.md) </span></span>  
 <span data-ttu-id="f9f20-121">[메모리 내 OLTP&#40;메모리 내 최적화&#41;](in-memory-oltp-in-memory-optimization.md) </span><span class="sxs-lookup"><span data-stu-id="f9f20-121">[In-Memory OLTP &#40;In-Memory Optimization&#41;](in-memory-oltp-in-memory-optimization.md) </span></span>  
 <span data-ttu-id="f9f20-122">[메모리 액세스에 최적화 된 테이블](memory-optimized-tables.md) </span><span class="sxs-lookup"><span data-stu-id="f9f20-122">[Memory-Optimized Tables](memory-optimized-tables.md) </span></span>  
 <span data-ttu-id="f9f20-123">[고유하게 컴파일된 저장 프로시저](natively-compiled-stored-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="f9f20-123">[Natively Compiled Stored Procedures](natively-compiled-stored-procedures.md) </span></span>  
 <span data-ttu-id="f9f20-124">[메모리 액세스에 최적화된 테이블 사용을 위한 요구 사항](requirements-for-using-memory-optimized-tables.md) </span><span class="sxs-lookup"><span data-stu-id="f9f20-124">[Requirements for Using Memory-Optimized Tables](requirements-for-using-memory-optimized-tables.md) </span></span>  
 <span data-ttu-id="f9f20-125">[CREATE DATABASE&#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f9f20-125">[CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) </span></span>  
 <span data-ttu-id="f9f20-126">[ALTER DATABASE 파일 및 파일 그룹 옵션&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-file-and-filegroup-options) </span><span class="sxs-lookup"><span data-stu-id="f9f20-126">[ALTER DATABASE File and Filegroup Options &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-file-and-filegroup-options) </span></span>  
 [<span data-ttu-id="f9f20-127">프로시저 및 메모리 액세스에 최적화 된 테이블 만들기</span><span class="sxs-lookup"><span data-stu-id="f9f20-127">CREATE PROCEDURE and Memory-Optimized Tables</span></span>](/sql/t-sql/statements/create-procedure-transact-sql)  
  
  
