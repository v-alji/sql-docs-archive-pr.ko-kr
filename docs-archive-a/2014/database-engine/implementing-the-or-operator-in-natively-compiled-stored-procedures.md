---
title: 고유 하 게 컴파일된 저장 프로시저에서 OR 연산자 구현 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: f2528e74-2b1c-48cb-861b-c4e57b51ac35
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7ed762e062cbc6831eb46784ef71fc7889850676
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734451"
---
# <a name="implementing-the-or-operator-in-natively-compiled-stored-procedures"></a><span data-ttu-id="99b47-102">고유하게 컴파일된 저장 프로시저에서 OR 연산자 구현</span><span class="sxs-lookup"><span data-stu-id="99b47-102">Implementing the OR Operator in Natively Compiled Stored Procedures</span></span>
  <span data-ttu-id="99b47-103">OR 연산자는 고유하게 컴파일된 저장 프로시저의 쿼리 조건자에서 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="99b47-103">OR operators are not supported in query predicates in natively compiled stored procedures.</span></span> <span data-ttu-id="99b47-104">NOT 연산자도 고유하게 컴파일된 저장 프로시저의 쿼리 조건자에서 지원되지 않으므로 동등한 논리 연산자만 사용하여 OR 연산자를 시뮬레이션할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="99b47-104">Because NOT operators are also not supported in query predicates in natively compiled stored procedures, the effects of OR operators cannot be simulated through the use of equivalent logical operators alone.</span></span> <span data-ttu-id="99b47-105">그러나 메모리 최적화 테이블 변수를 통해 OR 연산자의 효과를 시뮬레이션할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="99b47-105">However, the effects of an OR operator may be simulated with memory-optimized table variables.</span></span>  
  
## <a name="or-operator-in-where-clause"></a><span data-ttu-id="99b47-106">WHERE 절의 OR 연산자</span><span class="sxs-lookup"><span data-stu-id="99b47-106">OR Operator in WHERE Clause</span></span>  
 <span data-ttu-id="99b47-107">WHERE 절에 OR 연산자가 있는 경우 다음 방법을 사용하여 해당 동작을 시뮬레이션할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="99b47-107">If you have an OR operator in a WHERE clause, you can use the following approach to simulate its behavior:</span></span>  
  
1.  <span data-ttu-id="99b47-108">적합한 스키마를 사용하여 메모리 최적화 테이블 변수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="99b47-108">Create a memory-optimized table variable with the appropriate schema.</span></span> <span data-ttu-id="99b47-109">이렇게 하려면 미리 정의된 메모리 최적화 테이블 형식이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="99b47-109">This requires a predefined memory-optimized table type.</span></span>  
  
2.  <span data-ttu-id="99b47-110">최상위 OR 연산자로 시작하여 OR 연산자로 조인된 조건자에 따라 WHERE 절을 두 부분으로 나눕니다.</span><span class="sxs-lookup"><span data-stu-id="99b47-110">Starting with the top level OR operator, separate the WHERE clause into two parts according to the predicates joined by the OR operator.</span></span> <span data-ttu-id="99b47-111">WHERE 절에 둘 이상의 OR 연산자가 있는 경우 두 번 이상 이 동작을 수행해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="99b47-111">If you have more than one OR operator in a WHERE clause, you may need to do this more than once.</span></span> <span data-ttu-id="99b47-112">OR 연산자가 남아 있지 않을 때까지 이 단계를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="99b47-112">Repeat this step until no OR operators remain.</span></span> <span data-ttu-id="99b47-113">예를 들어 다음 조건자가 있는 경우</span><span class="sxs-lookup"><span data-stu-id="99b47-113">For example, if you have the following predicate:</span></span>  
  
    ```  
    pred1 OR (pred2 AND (pred3 OR pred4)) OR (pred5 AND pred6)  
    ```  
  
     <span data-ttu-id="99b47-114">이 단계 후에 다음 조건자가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="99b47-114">After this step, you should have the following predicates:</span></span>  
  
    ```  
    pred1  
    pred5 AND pred6  
    pred2 AND pred3  
    pred2 AND pred4  
    ```  
  
3.  <span data-ttu-id="99b47-115">2단계에 있는 두 부분의 각각을 조건자로 사용하여 쿼리를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="99b47-115">Execute a query with each of the two parts found in Step 2 as the predicate.</span></span> <span data-ttu-id="99b47-116">각 쿼리의 결과를 1단계에서 만든 메모리 최적화 테이블 변수에 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="99b47-116">Insert the result for each query into the memory-optimized table variable created in Step 1.</span></span>  
  
4.  <span data-ttu-id="99b47-117">필요한 경우 메모리 최적화 테이블 변수에서 중복 항목을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="99b47-117">If necessary, remove duplicates from the memory-optimized table variable.</span></span>  
  
5.  <span data-ttu-id="99b47-118">메모리 최적화 테이블 변수를 쿼리의 결과로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="99b47-118">Use the content of the memory-optimized table variable as the result from the query.</span></span>  
  
 <span data-ttu-id="99b47-119">다음 샘플에서는 [!INCLUDE[hek_2](../includes/hek-2-md.md)]에 대해 업데이트된 AdventureWorks2012 데이터베이스에서 테이블을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="99b47-119">The following sample uses tables from the AdventureWorks2012 database that were updated for [!INCLUDE[hek_2](../includes/hek-2-md.md)].</span></span> <span data-ttu-id="99b47-120">이 샘플에 대 한 파일을 다운로드 하려면 [AdventureWorks 데이터베이스-2012, 2008 r2 및 2008](https://msftdbprodsamples.codeplex.com/releases/view/93587)로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="99b47-120">To download the files for this sample, goto [AdventureWorks Databases - 2012, 2008R2 and 2008](https://msftdbprodsamples.codeplex.com/releases/view/93587).</span></span> <span data-ttu-id="99b47-121">AdventureWorks2012에 [!INCLUDE[hek_2](../includes/hek-2-md.md)] 코드 샘플을 적용하려면 [SQL Server 2014 메모리 내 OLTP 샘플](https://msftdbprodsamples.codeplex.com/releases/view/114491)로 이동하십시오.</span><span class="sxs-lookup"><span data-stu-id="99b47-121">To apply [!INCLUDE[hek_2](../includes/hek-2-md.md)] code sample to AdventureWorks2012, go to [SQL Server 2014 In-Memory OLTP Sample](https://msftdbprodsamples.codeplex.com/releases/view/114491).</span></span>  
  
 <span data-ttu-id="99b47-122">다음 저장 프로시저를 데이터베이스에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="99b47-122">Add the following stored procedure to the database.</span></span> <span data-ttu-id="99b47-123">네이티브 컴파일을 사용하도록 이 저장 프로시저를 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="99b47-123">We will convert this stored procedure to use native compilation.</span></span>  
  
```  
CREATE PROCEDURE Sales.usp_fuzzySearchSalesOrderDetail_ondisk  
  @SalesOrderId int = 0, @SalesOrderDetailId int = 0,   
  @CarrierTrackingNumber nvarchar(25) = N'', @ProductId int = 0,   
  @minUnitPrice money = 0, @maxUnitPrice money = 0  
AS BEGIN  
  SELECT SalesOrderId, SalesOrderDetailId, ModifiedDate  
  FROM Sales.SalesOrderDetail_ondisk s  
  WHERE  s.SalesOrderId = @SalesOrderId  
      OR s.SalesOrderDetailId = @SalesOrderDetailId  
      OR s.CarrierTrackingNumber = @CarrierTrackingNumber  
      OR s.ProductID = @ProductId  
      OR (s.UnitPrice > @minUnitPrice AND s.UnitPrice < @maxUnitPrice)  
END  
GO  
```  
  
 <span data-ttu-id="99b47-124">변환 후 테이블 및 저장 프로시저 스키마는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="99b47-124">After conversion, the table and stored procedure schema is as follows,</span></span>  
  
```  
CREATE TYPE Sales.fuzzySearchSalesOrderDetailType AS TABLE  
(  
  SalesOrderId int not null,  
  SalesOrderDetailId int not null,  
  ModifiedDate datetime2(7) not null  
  INDEX ix_fuzzySearchSalesOrderDetailType NONCLUSTERED (SalesOrderId, SalesOrderDetailId)  
) WITH (MEMORY_OPTIMIZED = ON)  
GO  
  
CREATE TYPE Sales.fuzzySearchSalesOrderDetailTempType AS TABLE  
(  
  SalesOrderId int not null,  
  SalesOrderDetailId int not null,  
  recordcount int not null  
  INDEX ix_fuzzySearchSalesOrderDetailTempType NONCLUSTERED (SalesOrderId, SalesOrderDetailId)  
) WITH (MEMORY_OPTIMIZED = ON)  
GO  
  
CREATE PROCEDURE Sales.usp_fuzzySearchSalesOrderDetail_inmem  
  @SalesOrderId int = 0, @SalesOrderDetailId int = 0,   
  @CarrierTrackingNumber nvarchar(25) = N'', @ProductId int = 0,   
  @minUnitPrice money = 0, @maxUnitPrice money = 0  
WITH NATIVE_COMPILATION, SCHEMABINDING, EXECUTE AS OWNER  
AS BEGIN ATOMIC WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'ENGLISH')  
  
  DECLARE @retValue Sales.fuzzySearchSalesOrderDetailType  
  
  INSERT INTO @retValue (SalesOrderId, SalesOrderDetailId, ModifiedDate)  
  SELECT SalesOrderId, SalesOrderDetailId, ModifiedDate  
  FROM Sales.SalesOrderDetail_inmem s  
  WHERE s.SalesOrderId = @SalesOrderId  
  
  INSERT INTO @retValue (SalesOrderId, SalesOrderDetailId, ModifiedDate)  
  SELECT SalesOrderId, SalesOrderDetailId, ModifiedDate  
  FROM Sales.SalesOrderDetail_inmem s  
  WHERE s.SalesOrderDetailId = @SalesOrderDetailId  
  
  INSERT INTO @retValue (SalesOrderId, SalesOrderDetailId, ModifiedDate)  
  SELECT SalesOrderId, SalesOrderDetailId, ModifiedDate  
  FROM Sales.SalesOrderDetail_inmem s  
  WHERE s.CarrierTrackingNumber COLLATE Latin1_General_BIN2 = @CarrierTrackingNumber COLLATE Latin1_General_BIN2   
  
  INSERT INTO @retValue (SalesOrderId, SalesOrderDetailId, ModifiedDate)  
  SELECT SalesOrderId, SalesOrderDetailId, ModifiedDate  
  FROM Sales.SalesOrderDetail_inmem s  
  WHERE s.ProductID = @ProductId  
  
  INSERT INTO @retValue (SalesOrderId, SalesOrderDetailId, ModifiedDate)  
  SELECT SalesOrderId, SalesOrderDetailId, ModifiedDate  
  FROM Sales.SalesOrderDetail_inmem s  
  WHERE (s.UnitPrice > @minUnitPrice AND s.UnitPrice < @maxUnitPrice)  
  
  -- After the above statements, there will be duplicates inside @retValue  
  -- Delete the duplicates from @retValue  
  DECLARE @duplicates Sales.fuzzySearchSalesOrderDetailTempType  
  
  INSERT INTO @duplicates (SalesOrderId, SalesOrderDetailId, recordcount)   
  SELECT SalesOrderId, SalesOrderDetailId, COUNT(*) AS recordCount  
  FROM @retValue  
  GROUP BY SalesOrderId, SalesOrderDetailId  
  
  -- Now we have one row per pair  
  -- clear and rebuild the result set  
  DELETE FROM @retValue  
  
  INSERT INTO @retValue  
  SELECT s.SalesOrderId, s.SalesOrderDetailId, s.ModifiedDate  
  FROM Sales.SalesOrderDetail_inmem s  
  JOIN @duplicates d ON s.SalesOrderId = d.SalesOrderId AND s.SalesOrderDetailId = d.SalesOrderDetailId  
  
  -- After this every pair of (SalesOrderId, SalesOrderDetailId) in @retValue should be unique.  
  SELECT SalesorderId, SalesOrderDetailId, ModifiedDate FROM @retValue  
END  
GO  
```  
  
## <a name="or-operator-in-join-condition"></a><span data-ttu-id="99b47-125">JOIN 조건의 OR 연산자</span><span class="sxs-lookup"><span data-stu-id="99b47-125">OR Operator in JOIN Condition</span></span>  
 <span data-ttu-id="99b47-126">SELECT 문의 JOIN 조건에 OR 연산자가 있는 경우 다음 방법을 사용하여 해당 동작을 시뮬레이션할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="99b47-126">If you have an OR operator in a JOIN condition of a SELECT statement, you may use the following approach to simulate its behavior.</span></span> <span data-ttu-id="99b47-127">JOIN 조건에 둘 이상의 OR 연산자가 있거나 OR 연산자가 포함된 여러 JOIN 조건이 있는 경우 이 동작을 두 번 이상 수행해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="99b47-127">If you have more than one OR operator in a JOIN condition or you have multiple JOIN condition with OR operators, you may need to do this more than once.</span></span>  
  
 <span data-ttu-id="99b47-128">OUTER JOIN 조건이 있는 경우 OUTER JOIN 조건 해결 방법과 이 해결 방법을 결합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="99b47-128">If you have OUTER JOIN conditions, you may combine this workaround with the workaround for OUTER JOIN conditions.</span></span>  
  
1.  <span data-ttu-id="99b47-129">적합한 스키마를 사용하여 메모리 최적화 테이블 변수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="99b47-129">Create a memory-optimized table variable with the appropriate schema.</span></span> <span data-ttu-id="99b47-130">이렇게 하려면 미리 정의된 메모리 최적화 테이블 형식이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="99b47-130">This requires a predefined memory-optimized table type.</span></span>  
  
2.  <span data-ttu-id="99b47-131">OR 연산자로 조인된 조건자에 따라 JOIN 조건의 조건자를 두 부분으로 나눕니다.</span><span class="sxs-lookup"><span data-stu-id="99b47-131">Separate the predicate in the JOIN condition into two parts according to the predicates joined by the OR operator.</span></span> <span data-ttu-id="99b47-132">JOIN 조건이 여러 개 있는 경우 각 JOIN 조건에 대해 이를 수행한 후 결과 조각 조합 집합을 만들어야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="99b47-132">If you have multiple JOIN conditions, you may need to do this for each JOIN condition and then create a set of combinations of the resulting fragments.</span></span> <span data-ttu-id="99b47-133">예를 들어 각 JOIN 조건에 OR 연산자가 하나 있는 JOIN 조건이 세 개인 경우 2x2x2=8 조건자를 가질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="99b47-133">For example, if you have three JOIN conditions with one OR operator in each JOIN condition, you may have 2x2x2=8 predicates.</span></span>  
  
3.  <span data-ttu-id="99b47-134">2단계에서 생성된 각 조건자의 경우 해당 결과를 1단계에서 만든 메모리 최적화 테이블 변수에 삽입하는 쿼리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="99b47-134">For each predicate produced by Step 2, create a query that will insert its result into the memory-optimized table variable created in Step 1.</span></span>  
  
4.  <span data-ttu-id="99b47-135">필요한 경우 메모리 최적화 테이블 변수에서 중복 항목을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="99b47-135">If necessary, remove duplicates from the memory-optimized table variable.</span></span>  
  
5.  <span data-ttu-id="99b47-136">메모리 최적화 테이블 변수를 쿼리의 결과로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="99b47-136">Use the content of the memory-optimized table variable as the result from the query.</span></span>  
  
 <span data-ttu-id="99b47-137">다음 샘플에서는 [!INCLUDE[hek_2](../includes/hek-2-md.md)]에 대해 업데이트된 AdventureWorks2012 데이터베이스에서 테이블을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="99b47-137">The following sample uses tables from the AdventureWorks2012 database that were updated for [!INCLUDE[hek_2](../includes/hek-2-md.md)].</span></span> <span data-ttu-id="99b47-138">이 샘플에 대 한 파일을 다운로드 하려면 [AdventureWorks 데이터베이스-2012, 2008 r2 및 2008](https://msftdbprodsamples.codeplex.com/releases/view/93587)로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="99b47-138">To download the files for this sample, goto [AdventureWorks Databases - 2012, 2008R2 and 2008](https://msftdbprodsamples.codeplex.com/releases/view/93587).</span></span> <span data-ttu-id="99b47-139">AdventureWorks2012에 [!INCLUDE[hek_2](../includes/hek-2-md.md)] 코드 샘플을 적용하려면 [SQL Server 2014 메모리 내 OLTP 샘플](https://msftdbprodsamples.codeplex.com/releases/view/114491)로 이동하십시오.</span><span class="sxs-lookup"><span data-stu-id="99b47-139">To apply [!INCLUDE[hek_2](../includes/hek-2-md.md)] code sample to AdventureWorks2012, go to [SQL Server 2014 In-Memory OLTP Sample](https://msftdbprodsamples.codeplex.com/releases/view/114491).</span></span>  
  
 <span data-ttu-id="99b47-140">다음 저장 프로시저를 데이터베이스에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="99b47-140">Add the following stored procedure to the database.</span></span> <span data-ttu-id="99b47-141">네이티브 컴파일을 사용하도록 이 저장 프로시저를 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="99b47-141">We will convert this stored procedure to use native compilation.</span></span> <span data-ttu-id="99b47-142">이 샘플에서는 INNER JOIN 조건을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="99b47-142">This sample uses INNER JOIN conditions.</span></span>  
  
```  
CREATE PROCEDURE Sales.usp_fuzzySearchSalesSpecialOffers_ondisk  
  @SpecialOfferId int  
AS BEGIN  
  
  SELECT s.SalesOrderId, s.SalesOrderDetailId, s.SpecialOfferID, s.ModifiedDate  
  FROM Sales.SalesOrderDetail_ondisk s  
  JOIN Sales.SpecialOffer_onDisk offer   
    ON s.SpecialOfferID = offer.SpecialOfferID   
    OR s.ProductID IN (SELECT ProductId FROM Sales.SpecialOfferProduct sop WHERE sop.SpecialOfferID = @SpecialOfferId)  
END  
```  
  
 <span data-ttu-id="99b47-143">변환 후 테이블 및 저장 프로시저 스키마는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="99b47-143">After conversion, the table and stored procedure schema is as follows,</span></span>  
  
```  
CREATE TYPE Sales.fuzzySearchSalesSpecialOffers_Type AS TABLE  
(  
  SalesOrderId int not null,  
  SalesOrderDetailId int not null,  
  SpecialOfferId int not null,  
  ModifiedDate datetime2(7) not null  
  INDEX ix_fuzzySearchSalesSpecialOffers_Type NONCLUSTERED (SalesOrderId, SalesOrderDetailId)  
) WITH (MEMORY_OPTIMIZED = ON)  
GO  
  
CREATE TYPE Sales.fuzzySearchSalesSpecialOffers_TempType AS TABLE  
(  
  SalesOrderId int not null,  
  SalesOrderDetailId int not null,  
  SpecialOfferId int not null,  
  recordcount int null  
  INDEX ix_fuzzySearchSalesSpecialOffers_TempType NONCLUSTERED (SalesOrderId, SalesOrderDetailId)  
) WITH (MEMORY_OPTIMIZED = ON)  
GO  
  
CREATE PROCEDURE Sales.usp_fuzzySearchSalesSpecialOffers_inmem  
  @SpecialOfferId int  
WITH NATIVE_COMPILATION, SCHEMABINDING, EXECUTE AS OWNER  
AS BEGIN ATOMIC WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'ENGLISH')  
  
  DECLARE @retValue Sales.FuzzySearchSalesSpecialOffers_Type  
  
  -- Find all special offers matching the conditions  
  
  INSERT INTO @retValue (SalesOrderId, SalesOrderDetailId, SpecialOfferid, ModifiedDate)  
  SELECT s.SalesOrderId, s.SalesOrderDetailId, s.SpecialOfferID, s.ModifiedDate  
  FROM Sales.SalesOrderDetail_inmem s  
  JOIN Sales.SpecialOffer_inmem offer   
    ON s.SpecialOfferID = offer.SpecialOfferID  
  
  INSERT INTO @retValue (SalesOrderId, SalesOrderDetailId, SpecialOfferid, ModifiedDate)  
  SELECT s.SalesOrderId, s.SalesOrderDetailId, s.SpecialOfferID, s.ModifiedDate  
  FROM Sales.SalesOrderDetail_inmem s  
  JOIN Sales.SpecialOfferProduct_inmem sop   
    ON sop.SpecialOfferId = @SpecialOfferId AND s.ProductID = sop.ProductId  
  
  -- Now we need to remove the duplicates from @matchingSpecialOffers  
  DECLARE @duplicates Sales.fuzzySearchSalesSpecialOffers_TempType  
  
  INSERT INTO @duplicates (SalesOrderId, SalesOrderDetailId, SpecialOfferid, recordcount)  
  SELECT SalesOrderId, SalesOrderDetailId, SpecialOfferId, COUNT(*)   
  FROM @retValue  
  GROUP BY SalesOrderId, SalesOrderDetailId, SpecialOfferId  
  
  -- now there should be no duplicates within @duplicate  
  -- use @duplicate for join.  
  SELECT s.SalesOrderId, s.SalesOrderDetailId, s.SpecialOfferID, s.ModifiedDate  
  FROM Sales.SalesOrderDetail_inmem s  
  JOIN @duplicates offer   
    ON    s.SalesOrderId = offer.SalesOrderId   
      AND s.SalesOrderDetailId = offer.SalesOrderDetailID   
      AND s.SpecialOfferId = offer.SpecialOfferId  
END  
GO  
```  
  
## <a name="side-effects"></a><span data-ttu-id="99b47-144">부작용</span><span class="sxs-lookup"><span data-stu-id="99b47-144">Side Effects</span></span>  
 <span data-ttu-id="99b47-145">WHERE 절 또는 JOIN 조건에 OR 연산자가 둘 이상 있는 경우 동작을 시뮬레이션하는 데 실행해야 하는 쿼리 수가 기하급수적으로 증가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="99b47-145">If you have more than one OR operator in the WHERE clause or JOIN condition, the number of queries you need to execute to simulate the behavior may increase exponentially.</span></span> <span data-ttu-id="99b47-146">이로 인해 쿼리 성능이 저하되고, 메모리 최적화 테이블 변수를 사용해야 하므로 메모리 사용량이 증가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="99b47-146">This may slow down query performance and may increase memory usage due to the need to use memory-optimized table variables.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99b47-147">참고 항목</span><span class="sxs-lookup"><span data-stu-id="99b47-147">See Also</span></span>  
 [<span data-ttu-id="99b47-148">고유하게 컴파일된 저장 프로시저의 마이그레이션 문제</span><span class="sxs-lookup"><span data-stu-id="99b47-148">Migration Issues for Natively Compiled Stored Procedures</span></span>](../relational-databases/in-memory-oltp/migration-issues-for-natively-compiled-stored-procedures.md)  
  
