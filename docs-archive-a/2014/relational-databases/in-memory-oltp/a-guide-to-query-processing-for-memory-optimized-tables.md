---
title: 메모리 액세스에 최적화된 테이블에 대한 쿼리 처리 가이드 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 065296fe-6711-4837-965e-252ef6c13a0f
author: rothja
ms.author: jroth
ms.openlocfilehash: 93489e5dea295964826005e081bcffe889cb7586
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653871"
---
# <a name="a-guide-to-query-processing-for-memory-optimized-tables"></a><span data-ttu-id="6d829-102">메모리 액세스에 최적화된 테이블에 대한 쿼리 처리 가이드</span><span class="sxs-lookup"><span data-stu-id="6d829-102">A Guide to Query Processing for Memory-Optimized Tables</span></span>
  <span data-ttu-id="6d829-103">메모리 내 OLTP는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에서 메모리 최적화 테이블과 고유하게 컴파일된 저장 프로시저를 도입합니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-103">In-Memory OLTP introduces memory-optimized tables and natively compiled stored procedures in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="6d829-104">이 문서에서는 메모리 최적화 테이블 및 고유하게 컴파일된 저장 프로시저 모두의 쿼리 처리에 대한 개요를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-104">This article gives an overview of query processing for both memory-optimized tables and natively compiled stored procedures.</span></span>  
  
 <span data-ttu-id="6d829-105">이 문서에서는 다음 내용을 포함하여 메모리 최적화 테이블에 대한 쿼리를 컴파일하고 실행하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-105">The document explains how queries on memory-optimized tables are compiled and executed, including:</span></span>  
  
-   <span data-ttu-id="6d829-106">디스크 기반 테이블에 대한 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 의 쿼리 처리 파이프라인입니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-106">The query processing pipeline in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] for disk-based tables.</span></span>  
  
-   <span data-ttu-id="6d829-107">쿼리 최적화: 메모리 최적화 테이블에 대한 통계의 역할 및 잘못된 쿼리 계획의 문제 해결을 위한 지침</span><span class="sxs-lookup"><span data-stu-id="6d829-107">Query optimization; the role of statistics on memory-optimized tables as well as guidelines for troubleshooting bad query plans.</span></span>  
  
-   <span data-ttu-id="6d829-108">메모리 최적화 테이블에 액세스하기 위한 해석된 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 사용입니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-108">The use of interpreted [!INCLUDE[tsql](../../../includes/tsql-md.md)] to access memory-optimized tables.</span></span>  
  
-   <span data-ttu-id="6d829-109">메모리 최적화 테이블 액세스를 위한 쿼리 최적화 관련 고려 사항</span><span class="sxs-lookup"><span data-stu-id="6d829-109">Considerations about query optimization for memory-optimized table access.</span></span>  
  
-   <span data-ttu-id="6d829-110">고유하게 컴파일된 저장 프로시저 컴파일 및 처리</span><span class="sxs-lookup"><span data-stu-id="6d829-110">Natively compiled stored procedure compilation and processing.</span></span>  
  
-   <span data-ttu-id="6d829-111">최적화 프로그램에서 비용 예측을 위해 사용되는 통계</span><span class="sxs-lookup"><span data-stu-id="6d829-111">Statistics that are used for cost estimation by the optimizer.</span></span>  
  
-   <span data-ttu-id="6d829-112">잘못된 쿼리 계획을 수정하는 방법</span><span class="sxs-lookup"><span data-stu-id="6d829-112">Ways to fix bad query plans.</span></span>  
  
## <a name="example-query"></a><span data-ttu-id="6d829-113">예제 쿼리</span><span class="sxs-lookup"><span data-stu-id="6d829-113">Example Query</span></span>  
 <span data-ttu-id="6d829-114">다음 예는 이 문서에서 설명하는 쿼리 처리 개념을 설명하기 위해 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-114">The following example will be used to illustrate the query processing concepts discussed in this article.</span></span>  
  
 <span data-ttu-id="6d829-115">여기에서는 두 가지 테이블인 Customer 및 Order 테이블을 살펴봅니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-115">We consider two tables, Customer and Order.</span></span> <span data-ttu-id="6d829-116">다음 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 스크립트에는 기존의 디스크 기반 형태로 이러한 두 테이블과 관련 인덱스에 대한 정의가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-116">The following [!INCLUDE[tsql](../../../includes/tsql-md.md)] script contains the definitions for these two tables and associated indexes, in their (traditional) disk-based form:</span></span>  
  
```sql  
CREATE TABLE dbo.[Customer] (  
  CustomerID nchar (5) NOT NULL PRIMARY KEY,  
  ContactName nvarchar (30) NOT NULL   
)  
GO  
  
CREATE TABLE dbo.[Order] (  
  OrderID int NOT NULL PRIMARY KEY,  
  CustomerID nchar (5) NOT NULL,  
  OrderDate date NOT NULL  
)  
GO  
CREATE INDEX IX_CustomerID ON dbo.[Order](CustomerID)  
GO  
CREATE INDEX IX_OrderDate ON dbo.[Order](OrderDate)  
GO  
```  
  
 <span data-ttu-id="6d829-117">이 문서에 표시된 쿼리 계획을 생성하기 위해 두 테이블에는 Northwind 샘플 데이터베이스의 샘플 데이터가 입력되었습니다. 이 데이터베이스는 [SQL Server 2000의 Northwind 및 pubs 샘플 데이터베이스](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/northwind-pubs)에서 다운로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-117">For constructing the query plans shown in this article, the two tables were populated with sample data from the Northwind sample database, which you can download from [Northwind and pubs Sample Databases for SQL Server 2000](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/northwind-pubs).</span></span>  
  
 <span data-ttu-id="6d829-118">다음 쿼리를 살펴보십시오. 이 쿼리는 Customer 및 Order 테이블을 조인하고 주문 ID와 연관된 고객 정보를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-118">Consider the following query, which joins the tables Customer and Order and returns the ID of the order and the associated customer information:</span></span>  
  
```sql  
SELECT o.OrderID, c.* FROM dbo.[Customer] c INNER JOIN dbo.[Order] o ON c.CustomerID = o.CustomerID  
```  
  
 <span data-ttu-id="6d829-119">[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 에서 표시되는 예상 실행 계획은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-119">The estimated execution plan as displayed by [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] is as follows</span></span>  
  
 <span data-ttu-id="6d829-120">![디스크 기반 테이블 조인을 위한 쿼리 계획.](../../database-engine/media/hekaton-query-plan-1.gif "디스크 기반 테이블 조인을 위한 쿼리 계획.")</span><span class="sxs-lookup"><span data-stu-id="6d829-120">![Query plan for join of disk-based tables.](../../database-engine/media/hekaton-query-plan-1.gif "Query plan for join of disk-based tables.")</span></span>  
<span data-ttu-id="6d829-121">디스크 기반 테이블 조인을 위한 쿼리 계획.</span><span class="sxs-lookup"><span data-stu-id="6d829-121">Query plan for join of disk-based tables.</span></span>  
  
 <span data-ttu-id="6d829-122">이 쿼리 계획 정보:</span><span class="sxs-lookup"><span data-stu-id="6d829-122">About this query plan:</span></span>  
  
-   <span data-ttu-id="6d829-123">Customer 테이블의 행은 기본 데이터 구조이며 전체 테이블 데이터를 포함하는 클러스터형 인덱스로부터 검색됩니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-123">The rows from the Customer table are retrieved from the clustered index, which is the primary data structure and has the full table data.</span></span>  
  
-   <span data-ttu-id="6d829-124">Order 테이블의 데이터는 CustomerID 열에 있는 비클러스터형 인덱스를 사용해서 검색됩니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-124">Data from the Order table is retrieved using the nonclustered index on the CustomerID column.</span></span> <span data-ttu-id="6d829-125">이 인덱스에는 조인에 사용되는 CustomerID 열과 사용자에게 반환되는 기본 키 열인 OrderID가 모두 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-125">This index contains both the CustomerID column, which is used for the join, and the primary key column OrderID, which is returned to the user.</span></span> <span data-ttu-id="6d829-126">Order 테이블에서 추가 열을 반환하려면 Order 테이블에 대한 클러스터형 인덱스에서 조회가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-126">Returning additional columns from the Order table would require lookups in the clustered index for the Order table.</span></span>  
  
-   <span data-ttu-id="6d829-127">논리 연산자 `Inner Join`은 물리 연산자 `Merge Join`에 의해 구현됩니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-127">The logical operator `Inner Join` is implemented by the physical operator `Merge Join`.</span></span> <span data-ttu-id="6d829-128">다른 물리적 조인 유형은 `Nested Loops` 및 `Hash Join`입니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-128">The other physical join types are `Nested Loops` and `Hash Join`.</span></span> <span data-ttu-id="6d829-129">`Merge Join` 연산자는 두 인덱스가 모두 조인 열 CustomerID에 정렬되어 있다는 사실을 활용합니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-129">The `Merge Join` operator takes advantage of the fact that both indexes are sorted on the join column CustomerID.</span></span>  
  
 <span data-ttu-id="6d829-130">이제 이 쿼리를 약간 변형하여 OrderID만 아니라 Order 테이블의 모든 행을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-130">Consider a slight variation on this query, which returns all rows from the Order table, not only OrderID:</span></span>  
  
```sql  
SELECT o.*, c.* FROM dbo.[Customer] c INNER JOIN dbo.[Order] o ON c.CustomerID = o.CustomerID  
```  
  
 <span data-ttu-id="6d829-131">이 쿼리의 예상 계획은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-131">The estimated plan for this query is:</span></span>  
  
 <span data-ttu-id="6d829-132">![디스크 기반 테이블의 해시 조인을 위한 쿼리 계획.](../../database-engine/media/hekaton-query-plan-2.gif "디스크 기반 테이블의 해시 조인을 위한 쿼리 계획.")</span><span class="sxs-lookup"><span data-stu-id="6d829-132">![Query plan for a hash join of disk-based tables.](../../database-engine/media/hekaton-query-plan-2.gif "Query plan for a hash join of disk-based tables.")</span></span>  
<span data-ttu-id="6d829-133">디스크 기반 테이블의 해시 조인을 위한 쿼리 계획.</span><span class="sxs-lookup"><span data-stu-id="6d829-133">Query plan for a hash join of disk-based tables.</span></span>  
  
 <span data-ttu-id="6d829-134">이 쿼리에서 Order 테이블의 행은 클러스터형 인덱스를 사용해서 검색됩니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-134">In this query, rows from the Order table are retrieved using the clustered index.</span></span> <span data-ttu-id="6d829-135">`Hash Match` 물리 연산자는 이제 `Inner Join`에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-135">The `Hash Match` physical operator is now used for the `Inner Join`.</span></span> <span data-ttu-id="6d829-136">Order에 대한 클러스터형 인덱스가 CustomerID로 정렬되지 않았으므로 `Merge Join`을 위해 sort 연산자가 필요하지만, 이는 성능에 영향을 줄 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-136">The clustered index on Order is not sorted on CustomerID, and so a `Merge Join` would require a sort operator, which would affect performance.</span></span> <span data-ttu-id="6d829-137">이전 예에서 `Hash Match` 연산자의 비용(46%)에 대비해서 `Merge Join` 연산자의 상대적 비용(75%)에 주의하십시오.</span><span class="sxs-lookup"><span data-stu-id="6d829-137">Note the relative cost of the `Hash Match` operator (75%) compared with the cost of the `Merge Join` operator in the previous example (46%).</span></span> <span data-ttu-id="6d829-138">이전 예에서 최적화 프로그램에는 `Hash Match` 연산자도 고려되었겠지만 `Merge Join` 연산자가 더 나은 성능을 제공하는 것으로 결정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-138">The optimizer would have considered the `Hash Match` operator also in the previous example, but concluded that the `Merge Join` operator gave better performance.</span></span>  
  
## <a name="ssnoversion-query-processing-for-disk-based-tables"></a>[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="6d829-139">디스크 기반 테이블에 대한 쿼리 처리</span><span class="sxs-lookup"><span data-stu-id="6d829-139">Query Processing for Disk-Based Tables</span></span>  
 <span data-ttu-id="6d829-140">다음 다이어그램에서는 임시 쿼리를 위한 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 의 쿼리 처리 흐름을 간단히 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-140">The following diagram outlines the query processing flow in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] for ad hoc queries:</span></span>  
  
 <span data-ttu-id="6d829-141">![SQL Server 쿼리 처리 파이프라인.](../../database-engine/media/hekaton-query-plan-3.gif "SQL Server 쿼리 처리 파이프라인.")</span><span class="sxs-lookup"><span data-stu-id="6d829-141">![SQL Server query processing pipeline.](../../database-engine/media/hekaton-query-plan-3.gif "SQL Server query processing pipeline.")</span></span>  
<span data-ttu-id="6d829-142">SQL Server 쿼리 처리 파이프라인.</span><span class="sxs-lookup"><span data-stu-id="6d829-142">SQL Server query processing pipeline.</span></span>  
  
 <span data-ttu-id="6d829-143">이 시나리오에서는</span><span class="sxs-lookup"><span data-stu-id="6d829-143">In this scenario:</span></span>  
  
1.  <span data-ttu-id="6d829-144">사용자가 쿼리를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-144">The user issues a query.</span></span>  
  
2.  <span data-ttu-id="6d829-145">파서 및 algebrizer가 사용자가 제출한 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 텍스트 기반의 논리 연산자를 사용해서 쿼리 트리를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-145">The parser and algebrizer construct a query tree with logical operators based on the [!INCLUDE[tsql](../../../includes/tsql-md.md)] text submitted by the user.</span></span>  
  
3.  <span data-ttu-id="6d829-146">최적화 프로그램이 물리 연산자가 포함된 최적화된 쿼리 계획을 만듭니다(예: 중첩 루프 조인).</span><span class="sxs-lookup"><span data-stu-id="6d829-146">The optimizer creates an optimized query plan containing physical operators (for example, nested-loops join).</span></span> <span data-ttu-id="6d829-147">최적화 후 계획은 계획 캐시에 저장될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-147">After optimization, the plan may be stored in the plan cache.</span></span> <span data-ttu-id="6d829-148">계획 캐시에 이미 이 쿼리에 대한 계획이 포함된 경우 이 단계는 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-148">This step is bypassed if the plan cache already contains a plan for this query.</span></span>  
  
4.  <span data-ttu-id="6d829-149">쿼리 실행 엔진이 쿼리 계획 해석을 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-149">The query execution engine processes an interpretation of the query plan.</span></span>  
  
5.  <span data-ttu-id="6d829-150">각 index seek, index scan 및 table scan 연산자에 대해 실행 엔진이 Access Methods의 해당 인덱스 및 테이블 구조로부터 행을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-150">For each index seek, index scan, and table scan operator, the execution engine requests rows from the respective index and table structures from Access Methods.</span></span>  
  
6.  <span data-ttu-id="6d829-151">Access Methods는 버퍼 풀에 있는 인덱스 및 데이터 페이지로부터 행을 검색하고 필요에 따라 디스크에서 버퍼 풀로 페이지를 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-151">Access Methods retrieves the rows from the index and data pages in the buffer pool and loads pages from disk into the buffer pool as needed.</span></span>  
  
 <span data-ttu-id="6d829-152">첫 번째 예제 쿼리에서 실행 엔진은 Access Methods에서 Customer의 클러스터형 인덱스 및 Order의 비클러스터형 인덱스에 있는 행을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-152">For the first example query, the execution engine requests rows in the clustered index on Customer and the nonclustered index on Order from Access Methods.</span></span> <span data-ttu-id="6d829-153">Access Methods는 B-트리 인덱스 구조를 통과하여 요청된 행을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-153">Access Methods traverses the B-tree index structures to retrieve the requested rows.</span></span> <span data-ttu-id="6d829-154">이 경우에는 계획이 전체 인덱스 검색을 호출하므로 모든 행이 검색됩니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-154">In this case all rows are retrieved as the plan calls for full index scans.</span></span>  
  
## <a name="interpreted-tsql-access-to-memory-optimized-tables"></a><span data-ttu-id="6d829-155">메모리 액세스에 최적화된 테이블에 대한 해석된 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 액세스</span><span class="sxs-lookup"><span data-stu-id="6d829-155">Interpreted [!INCLUDE[tsql](../../../includes/tsql-md.md)] Access to Memory-Optimized Tables</span></span>  
 [!INCLUDE[tsql](../../../includes/tsql-md.md)] <span data-ttu-id="6d829-156">임시 일괄 처리 및 저장 프로시저는 해석된 [!INCLUDE[tsql](../../../includes/tsql-md.md)]이라고도 부릅니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-156">ad hoc batches and stored procedures are also referred to as interpreted [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span> <span data-ttu-id="6d829-157">해석되었다는 용어는 쿼리 실행 엔진에서 쿼리 계획의 각 연산자에 대해 쿼리 계획이 해석되었음을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-157">Interpreted refers to the fact that the query plan is interpreted by the query execution engine for each operator in the query plan.</span></span> <span data-ttu-id="6d829-158">실행 엔진은 연산자 및 해당 매개 변수를 읽고 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-158">The execution engine reads the operator and its parameters and performs the operation.</span></span>  
  
 <span data-ttu-id="6d829-159">해석된 [!INCLUDE[tsql](../../../includes/tsql-md.md)]을 사용하면 메모리 최적화 테이블 및 디스크 기반 테이블에 모두 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-159">Interpreted [!INCLUDE[tsql](../../../includes/tsql-md.md)] can be used to access both memory-optimized and disk-based tables.</span></span> <span data-ttu-id="6d829-160">다음 그림에서는 메모리 최적화 테이블에 대한 해석된 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 액세스를 위한 쿼리 처리를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-160">The following figure illustrates query processing for interpreted [!INCLUDE[tsql](../../../includes/tsql-md.md)] access to memory-optimized tables:</span></span>  
  
 <span data-ttu-id="6d829-161">![해석된 tsql을 위한 쿼리 처리 파이프라인](../../database-engine/media/hekaton-query-plan-4.gif "해석된 tsql을 위한 쿼리 처리 파이프라인.")</span><span class="sxs-lookup"><span data-stu-id="6d829-161">![Query processing pipeline for interpreted tsql.](../../database-engine/media/hekaton-query-plan-4.gif "Query processing pipeline for interpreted tsql.")</span></span>  
<span data-ttu-id="6d829-162">메모리 최적화 테이블에 대한 해석된 Transact-SQL 액세스를 위한 쿼리 처리 파이프라인</span><span class="sxs-lookup"><span data-stu-id="6d829-162">Query processing pipeline for interpreted Transact-SQL access to memory-optimized tables.</span></span>  
  
 <span data-ttu-id="6d829-163">그림에 표시된 것처럼 쿼리 처리 파이프라인은 대부분 변경되지 않은 상태로 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-163">As illustrated by the figure, the query processing pipeline remains mostly unchanged:</span></span>  
  
-   <span data-ttu-id="6d829-164">파서 및 algebrizer가 쿼리 트리를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-164">The parser and algebrizer construct the query tree.</span></span>  
  
-   <span data-ttu-id="6d829-165">최적화 프로그램이 실행 계획을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-165">The optimizer creates the execution plan.</span></span>  
  
-   <span data-ttu-id="6d829-166">쿼리 실행 엔진이 실행 계획을 해석합니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-166">The query execution engine interprets the execution plan.</span></span>  
  
 <span data-ttu-id="6d829-167">기존의 쿼리 처리 파이프라인(그림 2)과 기본적으로 다른 점은 메모리 최적화 테이블의 행이 Access Methods를 사용하여 버퍼 풀에서 검색되지 않는다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-167">The main difference with the traditional query processing pipeline (figure 2) is that rows for memory-optimized tables are not retrieved from the buffer pool using Access Methods.</span></span> <span data-ttu-id="6d829-168">대신 메모리 내 OLTP 엔진을 통해 메모리 내 데이터 구조에서 행이 검색됩니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-168">Instead, rows are retrieved from the in-memory data structures through the In-Memory OLTP engine.</span></span> <span data-ttu-id="6d829-169">데이터 구조의 차이점으로 인해 다음 예에 표시된 것처럼 경우에 따라 최적화 프로그램이 서로 다른 계획을 선택하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-169">Differences in data structures cause the optimizer to pick different plans in some cases, as illustrated by the following example.</span></span>  
  
 <span data-ttu-id="6d829-170">다음 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 스크립트에는 해시 인덱스를 사용하는 Order 및 Customer 테이블의 메모리 최적화 버전이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-170">The following [!INCLUDE[tsql](../../../includes/tsql-md.md)] script contains memory-optimized versions of the Order and Customer tables, using hash indexes:</span></span>  
  
```sql  
CREATE TABLE dbo.[Customer] (  
  CustomerID nchar (5) NOT NULL PRIMARY KEY NONCLUSTERED,  
  ContactName nvarchar (30) NOT NULL   
) WITH (MEMORY_OPTIMIZED=ON)  
GO  
  
CREATE TABLE dbo.[Order] (  
  OrderID int NOT NULL PRIMARY KEY NONCLUSTERED,  
  CustomerID nchar (5) NOT NULL INDEX IX_CustomerID HASH(CustomerID) WITH (BUCKET_COUNT=100000),  
  OrderDate date NOT NULL INDEX IX_OrderDate HASH(OrderDate) WITH (BUCKET_COUNT=100000)  
) WITH (MEMORY_OPTIMIZED=ON)  
GO  
```  
  
 <span data-ttu-id="6d829-171">다음과 같이 메모리 최적화 테이블에서 동일한 쿼리를 실행한다고 가정해보세요.</span><span class="sxs-lookup"><span data-stu-id="6d829-171">Consider the same query executed on memory-optimized tables:</span></span>  
  
```sql  
SELECT o.OrderID, c.* FROM dbo.[Customer] c INNER JOIN dbo.[Order] o ON c.CustomerID = o.CustomerID  
```  
  
 <span data-ttu-id="6d829-172">예상 계획은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-172">The estimated plan is as follows:</span></span>  
  
 <span data-ttu-id="6d829-173">![메모리 액세스에 최적화된 테이블의 조인을 위한 쿼리 계획](../../database-engine/media/hekaton-query-plan-5.gif "메모리 최적화 테이블의 조인을 위한 쿼리 계획.")</span><span class="sxs-lookup"><span data-stu-id="6d829-173">![Query plan for join of memory optimized tables.](../../database-engine/media/hekaton-query-plan-5.gif "Query plan for join of memory optimized tables.")</span></span>  
<span data-ttu-id="6d829-174">메모리 최적화 테이블의 조인을 위한 쿼리 계획</span><span class="sxs-lookup"><span data-stu-id="6d829-174">Query plan for join of memory-optimized tables.</span></span>  
  
 <span data-ttu-id="6d829-175">디스크 기반 테이블에서 동일한 쿼리를 계획에 사용해서 다음과 같은 차이점을 관찰합니다(그림 1).</span><span class="sxs-lookup"><span data-stu-id="6d829-175">Observe the following differences with the plan for the same query on disk-based tables (figure 1):</span></span>  
  
-   <span data-ttu-id="6d829-176">이 계획에는 Customer 테이블에 대해 클러스터형 인덱스 검색이 아닌 테이블 검색이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-176">This plan contains a table scan rather than a clustered index scan for the table Customer:</span></span>  
  
    -   <span data-ttu-id="6d829-177">테이블 정의에는 클러스터형 인덱스가 포함되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-177">The definition of the table does not contain a clustered index.</span></span>  
  
    -   <span data-ttu-id="6d829-178">클러스터형 인덱스는 메모리 최적화 테이블에서 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-178">Clustered indexes are not supported with memory-optimized tables.</span></span> <span data-ttu-id="6d829-179">대신 메모리 최적화 모든 테이블에 적어도 하나 이상의 비클러스터형 인덱스가 있어야 하고 메모리 최적화 테이블의 모든 인덱스는 인덱스에 행을 저장하거나 클러스터형 인덱스를 참조할 필요 없이 테이블의 모든 열에 효율적으로 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-179">Instead, every memory-optimized table must have at least one nonclustered index and all indexes on memory-optimized tables can efficiently access all columns in the table without having to store them in the index or refer to a clustered index.</span></span>  
  
-   <span data-ttu-id="6d829-180">이 계획에는 `Hash Match`이 아니라 `Merge Join`가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-180">This plan contains a `Hash Match` rather than a `Merge Join`.</span></span> <span data-ttu-id="6d829-181">Order 및 Customer 테이블에 모두 있는 인덱스는 해시 인덱스이므로 정렬되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-181">The indexes on both the Order and the Customer table are hash indexes, and are thus not ordered.</span></span> <span data-ttu-id="6d829-182">`Merge Join`을 사용하기 위해서는 성능 저하가 발생하는 sort 연산자가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-182">A `Merge Join` would require sort operators that would decrease performance.</span></span>  
  
## <a name="natively-compiled-stored-procedures"></a><span data-ttu-id="6d829-183">Natively Compiled Stored Procedures</span><span class="sxs-lookup"><span data-stu-id="6d829-183">Natively Compiled Stored Procedures</span></span>  
 <span data-ttu-id="6d829-184">고유하게 컴파일된 저장 프로시저는 쿼리 실행 엔진에서 해석되지 않고 기계어 코드로 컴파일된 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 저장 프로시저입니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-184">Natively compiled stored procedures are [!INCLUDE[tsql](../../../includes/tsql-md.md)] stored procedures compiled to machine code, rather than interpreted by the query execution engine.</span></span> <span data-ttu-id="6d829-185">다음 스크립트는 예제 쿼리(예제 쿼리 섹션 참조)를 실행하는 기본적으로 컴파일되는 저장 프로시저를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-185">The following script creates a natively compiled stored procedure that runs the example query (from the Example Query section).</span></span>  
  
```sql  
CREATE PROCEDURE usp_SampleJoin  
WITH NATIVE_COMPILATION, SCHEMABINDING, EXECUTE AS OWNER  
AS BEGIN ATOMIC WITH   
(  TRANSACTION ISOLATION LEVEL = SNAPSHOT,  
  LANGUAGE = 'english')  
  
  SELECT o.OrderID, c.CustomerID, c.ContactName   
FROM dbo.[Order] o INNER JOIN dbo.[Customer] c   
  ON c.CustomerID = o.CustomerID  
  
END  
```  
  
 <span data-ttu-id="6d829-186">고유하게 컴파일된 저장 프로시저는 프로시저를 만들 때 컴파일되지만 해석된 저장 프로시저는 처음 실행할 때 컴파일됩니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-186">Natively compiled stored procedures are compiled at create time, whereas interpreted stored procedures are compiled at first execution time.</span></span> <span data-ttu-id="6d829-187">컴파일 중 특히 구문 분석과 대수 부분은 생성 시에 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-187">(A portion of the compilation, particularly parsing and algebrization, take place at create.</span></span> <span data-ttu-id="6d829-188">하지만 해석된 저장 프로시저의 경우 처음 실행할 때 쿼리 계획의 최적화가 발생합니다. 다시 컴파일 논리도 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-188">However, for interpreted stored procedures, optimization of the query plans takes place at first execution.) The recompilation logic is similar.</span></span> <span data-ttu-id="6d829-189">고유하게 컴파일된 저장 프로시저는 서버를 다시 시작한 경우 프로시저를 처음 실행할 때 다시 컴파일됩니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-189">Natively compiled stored procedures are recompiled on first execution of the procedure if the server is restarted.</span></span> <span data-ttu-id="6d829-190">해석된 저장 프로시저는 계획 캐시에 계획이 더 이상 없는 경우에 다시 컴파일됩니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-190">Interpreted stored procedures are recompiled if the plan is no longer in the plan cache.</span></span> <span data-ttu-id="6d829-191">다음 표에서는 고유하게 컴파일된 저장 프로시저와 해석된 저장 프로시저 모두의 컴파일 및 다시 컴파일 사례를 요약해서 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-191">The following table summarizes compilation and recompilation cases for both natively compiled and interpreted stored procedures:</span></span>  
  
||<span data-ttu-id="6d829-192">네이티브 컴파일</span><span class="sxs-lookup"><span data-stu-id="6d829-192">Natively compiled</span></span>|<span data-ttu-id="6d829-193">메모리 액세스에 최적화된 테이블에 대한 해석된</span><span class="sxs-lookup"><span data-stu-id="6d829-193">Interpreted</span></span>|  
|-|-----------------------|-----------------|  
|<span data-ttu-id="6d829-194">초기 컴파일</span><span class="sxs-lookup"><span data-stu-id="6d829-194">Initial compilation</span></span>|<span data-ttu-id="6d829-195">생성 시</span><span class="sxs-lookup"><span data-stu-id="6d829-195">At create time.</span></span>|<span data-ttu-id="6d829-196">처음 실행 시</span><span class="sxs-lookup"><span data-stu-id="6d829-196">At first execution.</span></span>|  
|<span data-ttu-id="6d829-197">자동 다시 컴파일</span><span class="sxs-lookup"><span data-stu-id="6d829-197">Automatic recompilation</span></span>|<span data-ttu-id="6d829-198">데이터베이스나 서버를 다시 시작한 후 프로시저를 처음 실행할 때</span><span class="sxs-lookup"><span data-stu-id="6d829-198">Upon first execution of the procedure after a database or server restart.</span></span>|<span data-ttu-id="6d829-199">서버를 다시 시작할 때</span><span class="sxs-lookup"><span data-stu-id="6d829-199">On server restart.</span></span> <span data-ttu-id="6d829-200">또는 일반적으로 스키마 또는 통계 변경이나 메모리 압력에 따라 계획 캐시에서 계획이 제거될 때</span><span class="sxs-lookup"><span data-stu-id="6d829-200">Or, eviction from the plan cache, usually based on schema or stats changes, or memory pressure.</span></span>|  
|<span data-ttu-id="6d829-201">수동 다시 컴파일</span><span class="sxs-lookup"><span data-stu-id="6d829-201">Manual recompilation</span></span>|<span data-ttu-id="6d829-202">지원 안 됨</span><span class="sxs-lookup"><span data-stu-id="6d829-202">Not supported.</span></span> <span data-ttu-id="6d829-203">해결을 위해서는 저장 프로시저를 삭제하고 다시 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-203">The workaround is to drop and recreate the stored procedure.</span></span>|<span data-ttu-id="6d829-204">`sp_recompile`을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="6d829-204">Use `sp_recompile`.</span></span> <span data-ttu-id="6d829-205">캐시에서 계획을 수동으로 제거할 수 있습니다(예: DBCC FREEPROCCACHE 사용).</span><span class="sxs-lookup"><span data-stu-id="6d829-205">You can manually evict the plan from the cache, for example through DBCC FREEPROCCACHE.</span></span> <span data-ttu-id="6d829-206">또한 WITH RECOMPILE로 저장 프로시저를 만들면 실행할 때마다 저장 프로시저가 다시 컴파일됩니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-206">You can also create the stored procedure WITH RECOMPILE and the stored procedure will be recompiled at every execution.</span></span>|  
  
### <a name="compilation-and-query-processing"></a><span data-ttu-id="6d829-207">컴파일 및 쿼리 처리</span><span class="sxs-lookup"><span data-stu-id="6d829-207">Compilation and Query Processing</span></span>  
 <span data-ttu-id="6d829-208">다음 다이어그램은 고유하게 컴파일된 저장 프로시저의 컴파일 프로세스를 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-208">The following diagram illustrates the compilation process for natively compiled stored procedures:</span></span>  
  
 <span data-ttu-id="6d829-209">![저장 프로시저의 고유 컴파일](../../database-engine/media/hekaton-query-plan-6.gif "저장 프로시저의 고유 컴파일")</span><span class="sxs-lookup"><span data-stu-id="6d829-209">![Native compilation of stored procedures.](../../database-engine/media/hekaton-query-plan-6.gif "Native compilation of stored procedures.")</span></span>  
<span data-ttu-id="6d829-210">저장 프로시저의 고유 컴파일</span><span class="sxs-lookup"><span data-stu-id="6d829-210">Native compilation of stored procedures.</span></span>  
  
 <span data-ttu-id="6d829-211">프로세스에 대한 설명은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-211">The process is described as,</span></span>  
  
1.  <span data-ttu-id="6d829-212">사용자가 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에 대해 `CREATE PROCEDURE` 문을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-212">The user issues a `CREATE PROCEDURE` statement to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
2.  <span data-ttu-id="6d829-213">파서 및 algebrizer가 프로시저에 대한 처리 흐름과 저장 프로시저에 있는 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 쿼리에 대한 쿼리 트리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-213">The parser and algebrizer create the processing flow for the procedure, as well as query trees for the [!INCLUDE[tsql](../../../includes/tsql-md.md)] queries in the stored procedure.</span></span>  
  
3.  <span data-ttu-id="6d829-214">최적화 프로그램이 저장 프로시저에 있는 모든 쿼리에 대한 최적화된 쿼리 실행 계획을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-214">The optimizer creates optimized query execution plans for all the queries in the stored procedure.</span></span>  
  
4.  <span data-ttu-id="6d829-215">메모리 내 OLTP 컴파일러가 포함된 최적화된 쿼리 계획에 처리 흐름을 사용해서 저장 프로시저 실행을 위한 기계어 코드가 포함된 DLL을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-215">The In-Memory OLTP compiler takes the processing flow with the embedded optimized query plans and generates a DLL that contains the machine code for executing the stored procedure.</span></span>  
  
5.  <span data-ttu-id="6d829-216">생성된 DLL이 메모리에 로드됩니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-216">The generated DLL is loaded into memory.</span></span>  
  
 <span data-ttu-id="6d829-217">고유하게 컴파일된 저장 프로시저의 호출은 DLL의 함수 호출과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-217">Invocation of a natively compiled stored procedure translates to calling a function in the DLL.</span></span>  
  
 <span data-ttu-id="6d829-218">![고유하게 컴파일된 저장 프로시저의 실행](../../database-engine/media/hekaton-query-plan-7.gif "고유하게 컴파일된 저장 프로시저의 실행")</span><span class="sxs-lookup"><span data-stu-id="6d829-218">![Execution of natively compiled stored procedures.](../../database-engine/media/hekaton-query-plan-7.gif "Execution of natively compiled stored procedures.")</span></span>  
<span data-ttu-id="6d829-219">고유하게 컴파일된 저장 프로시저의 실행</span><span class="sxs-lookup"><span data-stu-id="6d829-219">Execution of natively compiled stored procedures.</span></span>  
  
 <span data-ttu-id="6d829-220">고유하게 컴파일된 저장 프로시저의 호출에 대한 설명은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-220">Invocation of a natively compiled stored procedure is described as follows:</span></span>  
  
1.  <span data-ttu-id="6d829-221">사용자가 `EXEC` *usp_myproc* 문을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-221">The user issues an `EXEC`*usp_myproc* statement.</span></span>  
  
2.  <span data-ttu-id="6d829-222">파서가 이름 및 저장 프로시저 매개 변수를 추출합니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-222">The parser extracts the name and stored procedure parameters.</span></span>  
  
     <span data-ttu-id="6d829-223">`sp_prep_exec` 등을 사용해서 문이 준비되었으면 파서가 실행 시에 프로시저 이름과 매개 변수를 추출할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-223">If the statement was prepared, for example using `sp_prep_exec`, the parser does not need to extract the procedure name and parameters at execution time.</span></span>  
  
3.  <span data-ttu-id="6d829-224">메모리 내 OLTP 런타임이 저장 프로시저에 대한 DLL 진입점을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-224">The In-Memory OLTP runtime locates the DLL entry point for the stored procedure.</span></span>  
  
4.  <span data-ttu-id="6d829-225">DLL의 기계어 코드가 실행되고 결과가 클라이언트에 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-225">The machine code in the DLL is executed and the results of are returned to the client.</span></span>  
  
 <span data-ttu-id="6d829-226">**매개 변수 스니핑**</span><span class="sxs-lookup"><span data-stu-id="6d829-226">**Parameter sniffing**</span></span>  
  
 <span data-ttu-id="6d829-227">생성 시에 컴파일되는 고유하게 컴파일된 저장 프로시저와 달리 해석된 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 저장 프로시저는 첫 실행 시 컴파일됩니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-227">Interpreted [!INCLUDE[tsql](../../../includes/tsql-md.md)] stored procedures are compiled at first execution, in contrast to natively compiled stored procedures, which are compiled at create time.</span></span> <span data-ttu-id="6d829-228">호출 시에 해석된 저장 프로시저가 컴파일될 때 이 호출을 위해 제공된 매개 변수의 값은 최적화 프로그램이 실행 계획을 생성할 때 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-228">When interpreted stored procedures are compiled at invocation, the values of the parameters supplied for this invocation are used by the optimizer when generating the execution plan.</span></span> <span data-ttu-id="6d829-229">이렇게 컴파일 중 매개 변수의 사용을 매개 변수 스니핑이라고 부릅니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-229">This use of parameters during compilation is called parameter sniffing.</span></span>  
  
 <span data-ttu-id="6d829-230">고유하게 컴파일된 저장 프로시저를 컴파일하는 데에는 매개 변수 스니핑이 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-230">Parameter sniffing is not used for compiling natively compiled stored procedures.</span></span> <span data-ttu-id="6d829-231">이 저장 프로시저에 대한 모든 매개 변수는 UNKNOWN 값을 갖는 것으로 간주됩니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-231">All parameters to the stored procedure are considered to have UNKNOWN values.</span></span> <span data-ttu-id="6d829-232">해석된 저장 프로시저처럼 고유하게 컴파일된 저장 프로시저도 `OPTIMIZE FOR` 힌트를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-232">Like interpreted stored procedures, natively compiled stored procedures also support the `OPTIMIZE FOR` hint.</span></span> <span data-ttu-id="6d829-233">자세한 내용은 [쿼리 힌트&#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-query)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6d829-233">For more information, see [Query Hints &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-query).</span></span>  
  
### <a name="retrieving-a-query-execution-plan-for-natively-compiled-stored-procedures"></a><span data-ttu-id="6d829-234">고유하게 컴파일된 저장 프로시저에 대한 쿼리 실행 검색</span><span class="sxs-lookup"><span data-stu-id="6d829-234">Retrieving a Query Execution Plan for Natively Compiled Stored Procedures</span></span>  
 <span data-ttu-id="6d829-235">고유하게 컴파일된 저장 프로시저에 대한 쿼리 실행 계획은 **에서** 예상 실행 계획 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]을 사용하거나 [!INCLUDE[tsql](../../../includes/tsql-md.md)]에서 SHOWPLAN_XML 옵션을 사용하여 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-235">The query execution plan for a natively compiled stored procedure can be retrieved using **Estimated Execution Plan** in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], or using the SHOWPLAN_XML option in [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span> <span data-ttu-id="6d829-236">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-236">For example:</span></span>  
  
```sql  
SET SHOWPLAN_XML ON  
GO  
EXEC dbo.usp_myproc  
GO  
SET SHOWPLAN_XML OFF  
GO  
```  
  
 <span data-ttu-id="6d829-237">쿼리 최적화 프로그램에서 생성되는 실행 계획은 트리의 노드 및 리프에 대한 쿼리 연산자가 포함된 트리로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-237">The execution plan generated by the query optimizer consists of a tree with query operators on the nodes and leaves of the tree.</span></span> <span data-ttu-id="6d829-238">트리 구조에 따라 연산자 사이의 상호 작용(한 연산자에서 다른 연산자로의 행 흐름)이 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-238">The structure of the tree determines the interaction (the flow of rows from one operator to another) between the operators.</span></span> <span data-ttu-id="6d829-239">[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]의 그래픽 보기에서 흐름은 오른쪽에서 왼쪽의 방향으로 진행됩니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-239">In the graphical view of [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], the flow is from right to left.</span></span> <span data-ttu-id="6d829-240">예를 들어, 그림 1의 쿼리 계획에는 merge join 연산자에 행을 제공하는 2개의 index scan 연산자가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-240">For example, the query plan in figure 1 contains two index scan operators, which supplies rows to a merge join operator.</span></span> <span data-ttu-id="6d829-241">merge join 연산자는 select 연산자에 행을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-241">The merge join operator supplies rows to a select operator.</span></span> <span data-ttu-id="6d829-242">select 연산자가 마지막으로 클라이언트에 행을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-242">The select operator, finally, returns the rows to the client.</span></span>  
  
### <a name="query-operators-in-natively-compiled-stored-procedures"></a><span data-ttu-id="6d829-243">고유하게 컴파일된 저장 프로시저의 쿼리 연산자</span><span class="sxs-lookup"><span data-stu-id="6d829-243">Query Operators in Natively Compiled Stored Procedures</span></span>  
 <span data-ttu-id="6d829-244">다음 표에서는 고유하게 컴파일 저장 프로시저 내부에서 지원되는 쿼리 연산자를 요약해서 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-244">The following table summarizes the query operators supported inside natively compiled stored procedures:</span></span>  
  
|<span data-ttu-id="6d829-245">연산자</span><span class="sxs-lookup"><span data-stu-id="6d829-245">Operator</span></span>|<span data-ttu-id="6d829-246">샘플 쿼리</span><span class="sxs-lookup"><span data-stu-id="6d829-246">Sample query</span></span>|  
|--------------|------------------|  
|<span data-ttu-id="6d829-247">SELECT</span><span class="sxs-lookup"><span data-stu-id="6d829-247">SELECT</span></span>|`SELECT OrderID FROM dbo.[Order]`|  
|<span data-ttu-id="6d829-248">INSERT</span><span class="sxs-lookup"><span data-stu-id="6d829-248">INSERT</span></span>|`INSERT dbo.Customer VALUES ('abc', 'def')`|  
|<span data-ttu-id="6d829-249">UPDATE</span><span class="sxs-lookup"><span data-stu-id="6d829-249">UPDATE</span></span>|`UPDATE dbo.Customer SET ContactName='ghi' WHERE CustomerID='abc'`|  
|<span data-ttu-id="6d829-250">Delete</span><span class="sxs-lookup"><span data-stu-id="6d829-250">DELETE</span></span>|`DELETE dbo.Customer WHERE CustomerID='abc'`|  
|<span data-ttu-id="6d829-251">Compute Scalar</span><span class="sxs-lookup"><span data-stu-id="6d829-251">Compute Scalar</span></span>|<span data-ttu-id="6d829-252">이 연산자는 내장 함수 및 형식 변환에 모두 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-252">This operator is used both for intrinsic functions and type conversions.</span></span> <span data-ttu-id="6d829-253">고유하게 컴파일된 저장 프로시저 내에서 모든 함수 및 형식 변환이 지원되는 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-253">Not all functions and type conversions are supported inside natively compiled stored procedures.</span></span><br /><br /> `SELECT OrderID+1 FROM dbo.[Order]`|  
|<span data-ttu-id="6d829-254">중첩 루프 조인</span><span class="sxs-lookup"><span data-stu-id="6d829-254">Nested Loops Join</span></span>|<span data-ttu-id="6d829-255">Nested Loops는 고유하게 컴파일된 저장 프로시저에서 지원되는 유일한 조인 연산자입니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-255">Nested Loops is the only join operator supported in natively compiled stored procedures.</span></span> <span data-ttu-id="6d829-256">해석된 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 로 실행된 것과 동일한 쿼리에 대한 계획에 해시 또는 병합 조인이 포함되더라도 조인을 포함하는 모든 계획에는 Nested Loops 연산자가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-256">All plans that contain joins will use the Nested Loops operator, even if the plan for same query executed as interpreted [!INCLUDE[tsql](../../../includes/tsql-md.md)] contains a hash or merge join.</span></span><br /><br /> `SELECT o.OrderID, c.CustomerID`  <br /> `FROM dbo.[Order] o INNER JOIN dbo.[Customer] c`|  
|<span data-ttu-id="6d829-257">정렬</span><span class="sxs-lookup"><span data-stu-id="6d829-257">Sort</span></span>|`SELECT ContactName FROM dbo.Customer`  <br /> `ORDER BY ContactName`|  
|<span data-ttu-id="6d829-258">상위</span><span class="sxs-lookup"><span data-stu-id="6d829-258">Top</span></span>|`SELECT TOP 10 ContactName FROM dbo.Customer`|  
|<span data-ttu-id="6d829-259">Top-sort</span><span class="sxs-lookup"><span data-stu-id="6d829-259">Top-sort</span></span>|<span data-ttu-id="6d829-260">`TOP` 식(반환할 행의 수)은 8,000행을 초과할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-260">The `TOP` expression (the number of rows to be returned) cannot exceed 8,000 rows.</span></span> <span data-ttu-id="6d829-261">쿼리에 조인 및 집계 연산자도 있을 경우 이보다 적습니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-261">Fewer if there are also join and aggregation operators in the query.</span></span> <span data-ttu-id="6d829-262">일반적으로 조인과 집계는 기본 테이블의 행 개수와 비교할 때 정렬될 행 수를 줄입니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-262">Joins and aggregation do typically reduce the number of rows to be sorted, compared with the row count of the base tables.</span></span><br /><br /> `SELECT TOP 10 ContactName FROM dbo.Customer`  <br /> `ORDER BY ContactName`|  
|<span data-ttu-id="6d829-263">Stream Aggregate</span><span class="sxs-lookup"><span data-stu-id="6d829-263">Stream Aggregate</span></span>|<span data-ttu-id="6d829-264">Hash Match 연산자는 집계가 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-264">Note that the Hash Match operator is not supported for aggregation.</span></span> <span data-ttu-id="6d829-265">따라서 해석된 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 의 동일 쿼리에 대한 계획에 Hash Match 연산자가 사용되더라도 고유하게 컴파일된 저장 프로시저의 모든 집계에는 Stream Aggregate 연산자가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-265">Therefore, all aggregation in natively compiled stored procedures uses the Stream Aggregate operator, even if the plan for the same query in interpreted [!INCLUDE[tsql](../../../includes/tsql-md.md)] uses the Hash Match operator.</span></span><br /><br /> `SELECT count(CustomerID) FROM dbo.Customer`|  
  
## <a name="column-statistics-and-joins"></a><span data-ttu-id="6d829-266">열 통계 및 조인</span><span class="sxs-lookup"><span data-stu-id="6d829-266">Column Statistics and Joins</span></span>  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="6d829-267">는 index scan 및 index seek와 같은 특정 작업의 비용을 예측할 수 있도록 인덱스 키 열에 값 통계를 유지 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-267">maintains statistics on values in index key columns to help estimate the cost of certain operations, such as index scan and index seeks.</span></span> <span data-ttu-id="6d829-268">(인덱스가 아닌 키 열을 사용자가 명시적으로 만들거나 쿼리 최적화 프로그램에서 조건자가 있는 쿼리에 대한 응답으로 만드는 경우 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에서 그에 대한 통계도 만듭니다.) 비용 예측의 기본 메트릭은 단일 연산자에서 처리되는 행 수입니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-268">( [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] also creates statistics on non-index key columns if you explicitly create them or if the query optimizer creates them in response to a query with a predicate.) The main metric in cost estimation is the number of rows processed by a single operator.</span></span> <span data-ttu-id="6d829-269">디스크 기반 테이블의 경우에는 특정 연산자에서 액세스되는 페이지 수가 비용 예측에서 중요한 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-269">Note that for disk-based tables, the number of pages accessed by a particular operator is significant in cost estimation.</span></span> <span data-ttu-id="6d829-270">하지만 메모리 최적화 테이블의 경우에는 페이지 수가 항상 0이므로 중요하지 않습니다. 이 문서에서는 행 수에 대해 중점적으로 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-270">However, as page count is not important for memory-optimized tables (it is always zero), this discussion focuses on row count.</span></span> <span data-ttu-id="6d829-271">예측은 계획에서 index seek 및 scan 연산자로 시작해서 조인 연산자와 같은 다른 연산자를 포함하도록 확장됩니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-271">The estimation starts with the index seek and scan operators in the plan, and is then extended to include the other operators, like the join operator.</span></span> <span data-ttu-id="6d829-272">조인 연산자에서 처리될 것으로 예상되는 행 수는 기본 index, seek 및 scan 연산자의 예측을 기반으로 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-272">The estimated number of rows to be processed by a join operator is based on the estimation for the underlying index, seek, and scan operators.</span></span> <span data-ttu-id="6d829-273">메모리 최적화 테이블에 대한 해석된 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 액세스의 경우 실제 실행 계획을 관찰하면 계획에서 연산자에 대한 예측 및 실제 행 수 간의 차이를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-273">For interpreted [!INCLUDE[tsql](../../../includes/tsql-md.md)] access to memory-optimized tables, you can observe the actual execution plan to see the difference between the estimated and actual row counts for the operators in the plan.</span></span>  
  
 <span data-ttu-id="6d829-274">그림 1 예의 경우,</span><span class="sxs-lookup"><span data-stu-id="6d829-274">For the example in figure 1,</span></span>  
  
-   <span data-ttu-id="6d829-275">Customer에 대한 클러스터형 인덱스 검색의 예측은 91이고, 실제도 91입니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-275">The clustered index scan on Customer has estimated 91; actual 91.</span></span>  
  
-   <span data-ttu-id="6d829-276">CustomerID에 대한 비클러스터형 인덱스 검색의 예측은 830이고 실제도 830입니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-276">The nonclustered index scan on CustomerID has estimated 830; actual 830.</span></span>  
  
-   <span data-ttu-id="6d829-277">Merge Join 연산자의 예측은 815이고 실제는 830입니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-277">The Merge Join operator has estimated 815; actual 830.</span></span>  
  
 <span data-ttu-id="6d829-278">인덱스 검색에 대한 예측은 정확합니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-278">The estimates for the index scans are accurate.</span></span> [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="6d829-279">는 디스크 기반 테이블에 대한 행 수를 유지 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-279">maintains the row count for disk-based tables.</span></span> <span data-ttu-id="6d829-280">전체 테이블 및 인덱스 검색에 대한 예측은 항상 정확합니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-280">Estimates for full table and index scans are always accurate.</span></span> <span data-ttu-id="6d829-281">조인에 대한 예측도 상당히 정확한 편입니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-281">The estimate for the join is fairly accurate, too.</span></span>  
  
 <span data-ttu-id="6d829-282">이러한 예측이 변경될 경우 각각의 계획 대안에 대한 비용 고려도 함께 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-282">If these estimates change, the cost considerations for different plan alternatives change as well.</span></span> <span data-ttu-id="6d829-283">예를 들어, 조인의 어느 한쪽에 대한 예측 행 수가 1개 또는 몇 개 정도뿐이라면 중첩 루프 조인을 사용하는 것이 비용이 낮습니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-283">For example, if one of the sides of the join has an estimated row count of 1 or just a few rows, using a nested loops joins is less expensive.</span></span>  
  
 <span data-ttu-id="6d829-284">다음은 쿼리에 대한 계획입니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-284">The following is the plan for the query:</span></span>  
  
```  
SELECT o.OrderID, c.* FROM dbo.[Customer] c INNER JOIN dbo.[Order] o ON c.CustomerID = o.CustomerID  
```  
  
 <span data-ttu-id="6d829-285">Customer 테이블에서 행을 하나만 남겨두고 모두 삭제한 후에는 다음과 같이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-285">After deleting all rows but one in the table Customer:</span></span>  
  
 <span data-ttu-id="6d829-286">![열 통계 및 조인.](../../database-engine/media/hekaton-query-plan-9.gif "열 통계 및 조인.")</span><span class="sxs-lookup"><span data-stu-id="6d829-286">![Column statistics and joins.](../../database-engine/media/hekaton-query-plan-9.gif "Column statistics and joins.")</span></span>  
  
 <span data-ttu-id="6d829-287">이 쿼리 계획에 대한 설명은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-287">Regarding this query plan:</span></span>  
  
-   <span data-ttu-id="6d829-288">Hash Match가 Nested Loops 물리적 조인 연산자로 바뀌었습니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-288">The Hash Match has been replaced with a Nested Loops physical join operator.</span></span>  
  
-   <span data-ttu-id="6d829-289">IX_CustomerID에 대한 전체 인덱스 검색은 index seek로 바뀌었습니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-289">The full index scan on IX_CustomerID has been replaced with an index seek.</span></span> <span data-ttu-id="6d829-290">그 결과 전체 인덱스 검색에 필요한 830개 행 대신 5개 행이 검색되었습니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-290">This resulted in scanning 5 rows, instead of the 830 rows required for the full index scan.</span></span>  
  
### <a name="statistics-and-cardinality-for-memory-optimized-tables"></a><span data-ttu-id="6d829-291">메모리 액세스에 최적화된 테이블에 대한 통계 및 카디널리티</span><span class="sxs-lookup"><span data-stu-id="6d829-291">Statistics and Cardinality for Memory-Optimized Tables</span></span>  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]<span data-ttu-id="6d829-292">는 메모리 최적화 테이블에 대해 열 수준의 통계를 유지 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-292">maintains column-level statistics for memory-optimized tables.</span></span> <span data-ttu-id="6d829-293">또한 테이블의 실제 행 개수도 유지 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-293">In addition, it maintains the actual row count of the table.</span></span> <span data-ttu-id="6d829-294">그러나 디스크 기반 테이블과 달리 메모리 최적화 테이블에 대한 통계는 자동으로 업데이트되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-294">However, in contrast to disk-based tables, the statistics for memory-optimized tables are not automatically updated.</span></span> <span data-ttu-id="6d829-295">따라서 테이블이 크게 변경된 후 통계를 수동으로 업데이트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6d829-295">Therefore, statistics need to be manually updated after significant changes in the tables.</span></span> <span data-ttu-id="6d829-296">자세한 내용은 [메모리 액세스에 최적화된 테이블에 대한 통계](memory-optimized-tables.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6d829-296">For more information, see [Statistics for Memory-Optimized Tables](memory-optimized-tables.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d829-297">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6d829-297">See Also</span></span>  
 [<span data-ttu-id="6d829-298">메모리 최적화 테이블</span><span class="sxs-lookup"><span data-stu-id="6d829-298">Memory-Optimized Tables</span></span>](memory-optimized-tables.md)  
  
  
