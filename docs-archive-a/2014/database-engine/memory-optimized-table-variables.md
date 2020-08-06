---
title: 메모리 액세스에 최적화 된 테이블 변수 | Microsoft Docs
ms.custom: ''
ms.date: 07/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: bd102e95-53e2-4da6-9b8b-0e4f02d286d3
author: stevestein
ms.author: sstein
ms.openlocfilehash: bec720c53c257240ee92274a6391ebc3f17faa25
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651876"
---
# <a name="memory-optimized-table-variables"></a><span data-ttu-id="9140f-102">메모리 액세스에 최적화된 테이블 변수</span><span class="sxs-lookup"><span data-stu-id="9140f-102">Memory-Optimized Table Variables</span></span>
  <span data-ttu-id="9140f-103">효율적인 데이터 액세스를 위한 메모리 최적화 테이블 및 효율적인 쿼리 처리 및 비즈니스 논리 실행을 위한 고유하게 컴파일된 저장 프로시저 이외에 [!INCLUDE[hek_2](../includes/hek-2-md.md)]은 메모리 최적화 테이블 형식이라는 세 번째 개체를 도입했습니다.</span><span class="sxs-lookup"><span data-stu-id="9140f-103">In addition to memory-optimized tables (for efficient data access) and natively compiled stored procedures (for efficient query processing and business logic execution) [!INCLUDE[hek_2](../includes/hek-2-md.md)] introduces a third kind of object: the memory-optimized table type.</span></span> <span data-ttu-id="9140f-104">메모리 최적화 테이블 형식을 사용하여 만든 테이블 변수가 메모리 최적화 테이블 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="9140f-104">A table variable created using a memory-optimized table type is a memory-optimized table variable.</span></span>  
  
 <span data-ttu-id="9140f-105">메모리 액세스에 최적화된 테이블 변수는 디스크 기반 테이블 변수에 비해 다음과 같은 이점을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="9140f-105">Memory-optimized table variables offer the following advantages when compared to disk-based table variables:</span></span>  
  
-   <span data-ttu-id="9140f-106">변수가 메모리에만 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="9140f-106">The variables are only stored in memory.</span></span> <span data-ttu-id="9140f-107">특히 변수가 고유하게 컴파일된 저장 프로시저에서 사용될 경우, 메모리 최적화 테이블 형식은 메모리 최적화 테이블에 사용된 것과 동일한 메모리 최적화 알고리즘 및 데이터 구조를 사용하므로 데이터 액세스가 더 효율적입니다.</span><span class="sxs-lookup"><span data-stu-id="9140f-107">Data access is more efficient because memory-optimized table type use the same memory-optimized algorithm and data structures used for memory-optimized tables, especially when the variables are used in natively compiled stored procedures.</span></span>  
  
-   <span data-ttu-id="9140f-108">메모리 최적화 테이블 변수를 사용하면 tempdb가 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9140f-108">With memory-optimized table variables, there is no tempdb utilization.</span></span> <span data-ttu-id="9140f-109">테이블 변수는 tempdb에 저장되지 않으므로 tempdb에서 리소스를 사용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9140f-109">Table variables are not stored in tempdb and do not use any resources in tempdb.</span></span>  
  
 <span data-ttu-id="9140f-110">메모리 최적화 테이블 변수에 대한 일반적인 사용 시나리오는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="9140f-110">The typical usage scenarios for memory-optimized table variables are:</span></span>  
  
-   <span data-ttu-id="9140f-111">중간 결과를 저장하고 고유하게 컴파일된 저장 프로시저에 있는 여러 쿼리를 기반으로 단일 결과 집합을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="9140f-111">Storing intermediate results and creating single result sets based on multiple queries in natively compiled stored procedures.</span></span>  
  
-   <span data-ttu-id="9140f-112">테이블 반환 매개 변수를 고유하게 컴파일된 저장 프로시저와 해석된 저장 프로시저에 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="9140f-112">Passing table-valued parameters into natively compiled stored procedures and interpreted stored procedures.</span></span>  
  
-   <span data-ttu-id="9140f-113">디스크 기반 테이블 변수를 바꾸고 경우에 따라 저장 프로시저에 로컬인 #temp 테이블을 교체합니다.</span><span class="sxs-lookup"><span data-stu-id="9140f-113">Replacing disk-based table variables, and in some cases #temp tables that are local to a stored procedure.</span></span> <span data-ttu-id="9140f-114">시스템에서 tempdb 경합이 많은 경우에 특히 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="9140f-114">This is particularly useful if there is a lot of tempdb contention in the system.</span></span>  
  
-   <span data-ttu-id="9140f-115">테이블 변수를 사용하여 고유하게 컴파일된 저장 프로시저에서 커서를 시뮬레이트할 수 있으며, 이를 통해 고유하게 컴파일된 저장 프로시저에서 화면 영역 제한을 해결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9140f-115">Table variables can be used to simulate cursors in natively compiled stored procedures, which can help you work around surface area limitations in natively compiled stored procedures.</span></span>  
  
 <span data-ttu-id="9140f-116">메모리 최적화 테이블과 마찬가지로 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]에서는 메모리 최적화 테이블 형식별로 하나의 DLL을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="9140f-116">Like memory-optimized tables, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] generates a DLL for each memory-optimized table type.</span></span> <span data-ttu-id="9140f-117">메모리 최적화 테이블 형식을 만들 때 컴파일이 호출 되며 메모리 최적화 테이블 변수를 만드는 데 사용 되지 않습니다. 이 DLL에는 인덱스에 액세스 하 고 테이블 변수에서 데이터를 검색 하는 함수가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9140f-117">(Compilation is invoked when the memory-optimized table type is created and not when used to create memory-optimized table variables.) This DLL includes the functions for accessing indexes and retrieving data from the table variables.</span></span> <span data-ttu-id="9140f-118">테이블 형식을 기반으로 메모리 최적화 테이블 변수를 선언할 경우 테이블 형식에 따라 테이블 및 인덱스 구조의 인스턴스가 사용자 세션에 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="9140f-118">When a memory-optimized table variable is declared based on the table type, an instance of the table and index structures corresponding to the table type is created in the user session.</span></span> <span data-ttu-id="9140f-119">이 테이블 변수는 디스크 기반 테이블 변수와 동일한 방법으로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9140f-119">The table variable can then be used in the same way as disk-based table variables.</span></span> <span data-ttu-id="9140f-120">테이블 변수에서 행을 삽입, 업데이트 및 삭제하고 [!INCLUDE[tsql](../includes/tsql-md.md)] 쿼리에서 변수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9140f-120">You can insert, update, and delete rows in the table variable, and you can use the variables in [!INCLUDE[tsql](../includes/tsql-md.md)] queries.</span></span> <span data-ttu-id="9140f-121">변수를 고유하게 컴파일된 저장 프로시저와 해석된 저장 프로시저에 TVP(테이블 반환 매개 변수)로 전달할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9140f-121">You can also pass the variables into natively compiled and interpreted stored procedures, as table-valued parameters (TVP).</span></span>  
  
 <span data-ttu-id="9140f-122">다음 샘플은 AdventureWorks 기반 메모리 내 OLTP 샘플 ([SQL Server 2014 메모리 내 Oltp 샘플](https://msftdbprodsamples.codeplex.com/releases/view/114491))의 메모리 최적화 테이블 형식을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="9140f-122">The following sample shows a memory-optimized table type from the AdventureWorks-based In-Memory OLTP sample ([SQL Server 2014 In-Memory OLTP Sample](https://msftdbprodsamples.codeplex.com/releases/view/114491)).</span></span>  
  
```sql
CREATE TYPE Sales.SalesOrderDetailType_inmem
   AS TABLE
(
   OrderQty         smallint   NOT NULL,
   ProductID        int        NOT NULL,

   SpecialOfferID   int        NOT NULL
      INDEX  IX_SpecialOfferID  NONCLUSTERED,

   LocalID          int        NOT NULL,

   INDEX IX_ProductID HASH (ProductID)
      WITH ( BUCKET_COUNT = 8 )
)
WITH ( MEMORY_OPTIMIZED = ON );
```  
  
 <span data-ttu-id="9140f-123">이 예제에서는 다음 사항을 제외하고 메모리 최적화 테이블 형식의 구문이 디스크 기반 테이블 형식과 비슷함을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="9140f-123">The sample shows that the syntax of memory-optimized table types is similar to disk-based table types, with the following exceptions:</span></span>  
  
-   <span data-ttu-id="9140f-124">`MEMORY_OPTIMIZED=ON`은 테이블 형식이 메모리 최적화 형식인지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="9140f-124">`MEMORY_OPTIMIZED=ON` indicates that the table type is memory-optimized.</span></span>  
  
-   <span data-ttu-id="9140f-125">이 형식에 적어도 한 개의 인덱스가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9140f-125">The type must have at least one index.</span></span> <span data-ttu-id="9140f-126">메모리 최적화 테이블과 마찬가지로 해시 및 비클러스터형 인덱스를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9140f-126">As with memory-optimized tables, you can use hash and nonclustered indexes.</span></span>  
  
     <span data-ttu-id="9140f-127">해시 인덱스의 경우 버킷 수는 예상 고유 인덱스 키 개수의 약 1~2배 사이여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9140f-127">For a hash index, the bucket count should be about one to two times the number of expected unique index keys.</span></span> <span data-ttu-id="9140f-128">자세한 내용은 [Determining the Correct Bucket Count for Hash Indexes](../relational-databases/indexes/indexes.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9140f-128">For more information, see [Determining the Correct Bucket Count for Hash Indexes](../relational-databases/indexes/indexes.md).</span></span>  
  
-   <span data-ttu-id="9140f-129">메모리 최적화 테이블에 대한 데이터 형식 및 제약 조건 제한은 메모리 최적화 테이블 형식에도 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="9140f-129">The data type and constraint restrictions on memory-optimized tables also apply to memory-optimized table types.</span></span> <span data-ttu-id="9140f-130">예를 들어, [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] 기본 제약 조건은 지원되지만 CHECK 제약 조건은 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9140f-130">For example, in [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] default constraints are supported, but check constraints are not.</span></span>  
  
 <span data-ttu-id="9140f-131">메모리 최적화 테이블과 마찬가지로 메모리 최적화 테이블 변수에는 다음과 같은 특징이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9140f-131">Like memory-optimized tables, memory-optimized table variables,</span></span>  
  
-   <span data-ttu-id="9140f-132">병렬 계획을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9140f-132">Do not support parallel plans.</span></span>  
  
-   <span data-ttu-id="9140f-133">메모리 크기에 맞아야 하고 디스크 리소스를 사용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9140f-133">Must fit in memory and do not use disk resources.</span></span>  
  
 <span data-ttu-id="9140f-134">디스크 기반 테이블 변수는 tempdb에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9140f-134">Disk-based table variables exist in tempdb.</span></span> <span data-ttu-id="9140f-135">메모리 액세스에 최적화된 테이블 변수는 사용자 데이터베이스에 있지만, 스토리지를 사용하지 않으므로 복구되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9140f-135">Memory-optimized table variables exist in the user database (but they do not consume storage and are not recovered).</span></span>  
  
 <span data-ttu-id="9140f-136">인라인 구문을 사용하여 메모리 최적화 테이블 변수를 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9140f-136">You cannot create a memory-optimized table variable using in-line syntax.</span></span> <span data-ttu-id="9140f-137">디스크 기반 테이블 변수와 달리 먼저 형식을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9140f-137">Unlike disk-based table variables, you must create a type first.</span></span>  
  
## <a name="table-valued-parameters"></a><span data-ttu-id="9140f-138">테이블 반환 매개 변수</span><span class="sxs-lookup"><span data-stu-id="9140f-138">Table-Valued Parameters</span></span>  
 <span data-ttu-id="9140f-139">다음 예제 스크립트는 메모리 최적화 테이블 형식 `Sales.SalesOrderDetailType_inmem`으로 테이블 변수를 선언하고, 변수에 세 행을 삽입하고, 변수를 `Sales.usp_InsertSalesOrder_inmem`에 TVP로 전달하는 과정을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="9140f-139">The following sample script shows the declaration of a table variable as the memory-optimized table type `Sales.SalesOrderDetailType_inmem`, the insert of three rows into the variable, and passing the variable as a TVP into `Sales.usp_InsertSalesOrder_inmem`.</span></span>  
  
```sql  
DECLARE @od Sales.SalesOrderDetailType_inmem,  
  @SalesOrderID uniqueidentifier,  
  @DueDate datetime2 = SYSDATETIME()  
  
INSERT @od (LocalID, ProductID, OrderQty, SpecialOfferID) VALUES  
  (1, 888, 2, 1),  
  (2, 450, 13, 1),  
  (3, 841, 1, 1)  
  
EXEC Sales.usp_InsertSalesOrder_inmem  
  @SalesOrderID = @SalesOrderID,  
  @DueDate = @DueDate,  
 @OnlineOrderFlag = 1,  
  @SalesOrderDetails = @od  
```  
  
 <span data-ttu-id="9140f-140">메모리 액세스에 최적화된 테이블 형식을 저장 프로시저 TVP(테이블 반환 매개 변수)에 대한 형식으로 사용하고 디스크 기반 테이블 형식 및 TVP와 동일한 클라이언트에서 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9140f-140">Memory-optimized table types can be used as the type for stored procedure table-valued parameters (TVPs) and can be referenced by clients exactly the same as disk-based table types and TVPs.</span></span> <span data-ttu-id="9140f-141">따라서 메모리 최적화 TVP를 통한 저장 프로시저 호출 및 고유하게 컴파일된 저장 프로시저 호출 작업은 디스크 기반 TVP를 통한 해석된 저장 프로시저 호출 작업과 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="9140f-141">Therefore, the invocation of stored procedures with memory-optimized TVPs, and natively compiled stored procedures works exactly the same as the invocation of interpreted stored procedures with disk-based TVPs.</span></span>  
  
## <a name="temp-table-replacement"></a><span data-ttu-id="9140f-142">#temp 테이블 바꾸기</span><span class="sxs-lookup"><span data-stu-id="9140f-142">#temp Table Replacement</span></span>  
 <span data-ttu-id="9140f-143">다음 예제에서는 메모리 최적화 테이블 형식 및 테이블 변수를 저장 프로시저에 로컬인 #temp 테이블에 대한 대체 값으로 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="9140f-143">The following sample shows memory-optimized table types and table variables as a replacement for #temp tables that are local to a stored procedure.</span></span>  
  
```sql  
-- Using SQL procedure and temp table  
CREATE TABLE #tempTable (c INT NOT NULL PRIMARY KEY NONCLUSTERED)  
  
CREATE PROCEDURE sqlProc  
AS  
BEGIN  
  TRUNCATE TABLE #tempTable  
  
  INSERT #tempTable VALUES (1)  
  INSERT #tempTable VALUES (2)  
  INSERT #tempTable VALUES (3)  
  SELECT * FROM #tempTable  
END  
GO  
  
-- Using natively compiled stored procedure and table variable  
CREATE TYPE TT AS TABLE (c INT NOT NULL PRIMARY KEY NONCLUSTERED)  
GO  
  
CREATE PROCEDURE NCSPProc  
WITH NATIVE_COMPILATION, SCHEMABINDING, EXECUTE AS OWNER  
AS  
BEGIN ATOMIC WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'us_english')  
  DECLARE @tableVariable TT  
  INSERT @tableVariable VALUES (1)  
  INSERT @tableVariable VALUES (2)  
  INSERT @tableVariable VALUES (3)  
  SELECT c FROM @tableVariable  
END  
GO  
```  
  
## <a name="creating-a-single-result-set"></a><span data-ttu-id="9140f-144">단일 결과 집합 만들기</span><span class="sxs-lookup"><span data-stu-id="9140f-144">Creating a Single Result Set</span></span>  
 <span data-ttu-id="9140f-145">다음 예제에서는 중간 결과를 저장하고 고유하게 컴파일된 저장 프로시저에 있는 여러 쿼리를 기반으로 단일 결과 집합을 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="9140f-145">The following sample shows how to store intermediate results and create single result sets based on multiple queries in natively compiled stored procedures.</span></span> <span data-ttu-id="9140f-146">이 예제는 통합 `SELECT c1 FROM dbo.t1 UNION SELECT c1 FROM dbo.t2`를 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="9140f-146">The sample is computing the union `SELECT c1 FROM dbo.t1 UNION SELECT c1 FROM dbo.t2`.</span></span>  
  
```sql  
CREATE DATABASE hk  
GO  
ALTER DATABASE hk ADD FILEGROUP hk_mod CONTAINS MEMORY_OPTIMIZED_DATA  
ALTER DATABASE hk ADD FILE( NAME = 'hk_mod' , FILENAME = 'c:\data\hk_mod') TO FILEGROUP hk_mod;  
  
USE hk  
GO  
  
CREATE TYPE tab1 AS TABLE (c1 INT NOT NULL, INDEX idx NONCLUSTERED(c1)) WITH (MEMORY_OPTIMIZED = ON)  
  
CREATE TABLE dbo.t1 (c1 INT NOT NULL, INDEX idx NONCLUSTERED(c1)) WITH (MEMORY_OPTIMIZED = ON, DURABILITY = SCHEMA_ONLY)  
CREATE TABLE dbo.t2 (c1 INT NOT NULL, INDEX idx NONCLUSTERED(c1)) WITH (MEMORY_OPTIMIZED = ON, DURABILITY = SCHEMA_ONLY)  
  
INSERT INTO dbo.t1 VALUES (1), (2)  
INSERT INTO dbo.t2 VALUES (3), (4)  
GO  
  
CREATE PROCEDURE dbo.p1  
  WITH NATIVE_COMPILATION, SCHEMABINDING, EXECUTE AS OWNER  
  AS  
  BEGIN ATOMIC WITH ( TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'us_english' )  
  
    DECLARE @t dbo.tab1  
    INSERT @t (c1)  
    SELECT c1 FROM dbo.t1;  
  
    INSERT @t (c1)  
    SELECT c1 FROM dbo.t2;  
  
    SELECT c1 FROM @t;  
  END  
GO  
  
EXEC dbo.p1  
GO  
```  
  
## <a name="memory-consumption-for-table-variables"></a><span data-ttu-id="9140f-147">테이블 변수에 대한 메모리 사용</span><span class="sxs-lookup"><span data-stu-id="9140f-147">Memory Consumption for Table Variables</span></span>  
 <span data-ttu-id="9140f-148">테이블 변수에 대한 메모리 사용은 비클러스터형 인덱스를 제외하고 메모리 최적화 테이블과 유사합니다.</span><span class="sxs-lookup"><span data-stu-id="9140f-148">Memory consumption for table variables is similar to memory-optimized tables, with the exception of nonclustered indexes.</span></span> <span data-ttu-id="9140f-149">비클러스터형 인덱스를 포함한 메모리 최적화 테이블 변수에 대량의 행을 삽입하고 인덱스 키가 클 경우, 이러한 테이블 변수에는 잘못된 양의 메모리가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="9140f-149">If you insert a lot of rows into memory-optimized table variables with nonclustered indexes and if the index keys are large, these table variables will use a disproportionate amount of memory.</span></span> <span data-ttu-id="9140f-150">큰 테이블 변수에 대한 비클러스터형 인덱스는 테이블(인덱스 페이지의 추가 메모리)에 삽입된 동일한 행 수에 대해 비클러스터형 인덱스에 필요한 것보다 더 많은 메모리가 그에 비례하여 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="9140f-150">Nonclustered indexes on large table variables require proportionately more memory than a nonclustered index would require for the same number of rows inserted into a table (more memory in the index pages).</span></span>  
  
 <span data-ttu-id="9140f-151">테이블 변수에 대한 메모리는 데이터베이스의 리소스 관리자 리소스 풀에서 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="9140f-151">Memory for table variables comes from the database's Resource Governor resource pool.</span></span>  
  
 <span data-ttu-id="9140f-152">메모리 최적화 테이블과는 달리 테이블 변수에 의해 (삭제된 행을 포함하여) 사용되는 메모리는 테이블 변수가 범위를 벗어날 때 해제됩니다.</span><span class="sxs-lookup"><span data-stu-id="9140f-152">Unlike memory-optimized tables, the memory consumed (including deleted rows) by table variables is freed when the table variable goes out of scope.</span></span>  
  
 <span data-ttu-id="9140f-153">메모리는 데이터베이스의 단일 PGPOOL 메모리 소비자의 일부로 계산됩니다.</span><span class="sxs-lookup"><span data-stu-id="9140f-153">Memory is accounted for as part of the single PGPOOL memory consumer of the database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9140f-154">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9140f-154">See Also</span></span>  
 [<span data-ttu-id="9140f-155">메모리 내 OLTP에 대한 Transact-SQL 지원</span><span class="sxs-lookup"><span data-stu-id="9140f-155">Transact-SQL Support for In-Memory OLTP</span></span>](../relational-databases/in-memory-oltp/transact-sql-support-for-in-memory-oltp.md)  
  
  
