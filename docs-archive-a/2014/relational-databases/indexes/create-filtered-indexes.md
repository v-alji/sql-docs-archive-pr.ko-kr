---
title: 필터링된 인덱스 만들기 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- filtered indexes [SQL Server], about filtered indexes
- designing indexes [SQL Server], filtered
- filtered indexes [SQL Server]
- nonclustered indexes [SQL Server], filtered
- indexes [SQL Server], filtered
ms.assetid: 25e1fcc5-45d7-4c53-8c79-5493dfaa1c74
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 77cf641ca84181496f26a995244029d0525ade63
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740963"
---
# <a name="create-filtered-indexes"></a><span data-ttu-id="8ec97-102">필터링된 인덱스 만들기</span><span class="sxs-lookup"><span data-stu-id="8ec97-102">Create Filtered Indexes</span></span>
  <span data-ttu-id="8ec97-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 을 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)]에서 필터링된 인덱스를 만드는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec97-103">This topic describes how to create a filtered index in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="8ec97-104">필터링된 인덱스는 특히 데이터의 잘 정의된 하위 집합에서 선택하는 쿼리를 처리하는 데 적합한 최적화된 비클러스터형 인덱스입니다.</span><span class="sxs-lookup"><span data-stu-id="8ec97-104">A filtered index is an optimized nonclustered index especially suited to cover queries that select from a well-defined subset of data.</span></span> <span data-ttu-id="8ec97-105">이 인덱스에서는 필터 조건자를 사용하여 테이블의 일부 행을 인덱싱합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec97-105">It uses a filter predicate to index a portion of rows in the table.</span></span> <span data-ttu-id="8ec97-106">잘 디자인된 필터링된 인덱스는 전체 테이블 인덱스에 비해 쿼리 성능을 개선하고 인덱스 유지 관리 및 스토리지 비용을 줄일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ec97-106">A well-designed filtered index can improve query performance as well as reduce index maintenance and storage costs compared with full-table indexes.</span></span>  
  
 <span data-ttu-id="8ec97-107">필터링된 인덱스는 전체 테이블 인덱스에 비해 다음과 같은 이점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ec97-107">Filtered indexes can provide the following advantages over full-table indexes:</span></span>  
  
-   <span data-ttu-id="8ec97-108">**향상된 쿼리 성능 및 계획 품질**</span><span class="sxs-lookup"><span data-stu-id="8ec97-108">**Improved query performance and plan quality**</span></span>  
  
     <span data-ttu-id="8ec97-109">잘 디자인된 필터링된 인덱스는 전체 테이블 비클러스터형 인덱스보다 크기가 작고 필터링된 통계가 있기 때문에 쿼리 성능 및 실행 계획 품질이 향상됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ec97-109">A well-designed filtered index improves query performance and execution plan quality because it is smaller than a full-table nonclustered index and has filtered statistics.</span></span> <span data-ttu-id="8ec97-110">필터링된 통계는 필터링된 인덱스의 행만 처리하기 때문에 전체 테이블 통계보다 정확합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec97-110">The filtered statistics are more accurate than full-table statistics because they cover only the rows in the filtered index.</span></span>  
  
-   <span data-ttu-id="8ec97-111">**줄어든 인덱스 유지 관리 비용**</span><span class="sxs-lookup"><span data-stu-id="8ec97-111">**Reduced index maintenance costs**</span></span>  
  
     <span data-ttu-id="8ec97-112">인덱스의 DML(데이터 조작 언어) 문이 데이터에 영향을 줄 때에만 인덱스가 유지 관리됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ec97-112">An index is maintained only when data manipulation language (DML) statements affect the data in the index.</span></span> <span data-ttu-id="8ec97-113">필터링된 인덱스는 크기가 더 작고 인덱스의 데이터가 변경될 때에만 유지 관리되기 때문에 전체 테이블 비클러스터형 인덱스에 비해 인덱스 유지 관리 비용이 줄어듭니다.</span><span class="sxs-lookup"><span data-stu-id="8ec97-113">A filtered index reduces index maintenance costs compared with a full-table nonclustered index because it is smaller and is only maintained when the data in the index is changed.</span></span> <span data-ttu-id="8ec97-114">자주 변경되지 않는 데이터를 포함하는 경우 필터링된 인덱스 수가 많을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ec97-114">It is possible to have a large number of filtered indexes, especially when they contain data that is changed infrequently.</span></span> <span data-ttu-id="8ec97-115">마찬가지로 필터링된 인덱스에 자주 수정되는 데이터만 들어 있을 경우 인덱스 크기가 작으므로 통계를 업데이트하는 비용이 줄어듭니다.</span><span class="sxs-lookup"><span data-stu-id="8ec97-115">Similarly, if a filtered index contains only the frequently modified data, the smaller size of the index reduces the cost of updating the statistics.</span></span>  
  
-   <span data-ttu-id="8ec97-116">**줄어든 인덱스 스토리지 비용**</span><span class="sxs-lookup"><span data-stu-id="8ec97-116">**Reduced index storage costs**</span></span>  
  
     <span data-ttu-id="8ec97-117">필터링된 인덱스를 만들면 전체 테이블 인덱스가 필요하지 않은 경우 비클러스터형 인덱스의 디스크 스토리지를 줄일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ec97-117">Creating a filtered index can reduce disk storage for nonclustered indexes when a full-table index is not necessary.</span></span> <span data-ttu-id="8ec97-118">스토리지 요구 사항을 크게 증가시키지 않고 전체 테이블 비클러스터형 인덱스를 여러 필터링된 인덱스로 바꿀 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ec97-118">You can replace a full-table nonclustered index with multiple filtered indexes without significantly increasing the storage requirements.</span></span>  
  
 <span data-ttu-id="8ec97-119">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="8ec97-119">**In This Topic**</span></span>  
  
-   <span data-ttu-id="8ec97-120">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="8ec97-120">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="8ec97-121">디자인 고려 사항</span><span class="sxs-lookup"><span data-stu-id="8ec97-121">Design Considerations</span></span>](#Design)  
  
     [<span data-ttu-id="8ec97-122">제한 사항</span><span class="sxs-lookup"><span data-stu-id="8ec97-122">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="8ec97-123">보안</span><span class="sxs-lookup"><span data-stu-id="8ec97-123">Security</span></span>](#Security)  
  
-   <span data-ttu-id="8ec97-124">**필터링된 인덱스를 만들려면:**</span><span class="sxs-lookup"><span data-stu-id="8ec97-124">**To create a filtered index, using:**</span></span>  
  
     [<span data-ttu-id="8ec97-125">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="8ec97-125">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="8ec97-126">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="8ec97-126">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="8ec97-127">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="8ec97-127">Before You Begin</span></span>  
  
###  <a name="design-considerations"></a><a name="Design"></a> <span data-ttu-id="8ec97-128">디자인 고려 사항</span><span class="sxs-lookup"><span data-stu-id="8ec97-128">Design Considerations</span></span>  
  
-   <span data-ttu-id="8ec97-129">열에 적은 수의 쿼리 관련 값만 있는 경우 값의 하위 집합에 필터링된 인덱스를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ec97-129">When a column only has a small number of relevant values for queries, you can create a filtered index on the subset of values.</span></span> <span data-ttu-id="8ec97-130">예를 들어 열에 있는 값이 대부분 NULL이고 쿼리는 NULL이 아닌 값에서만 선택하는 경우 NULL이 아닌 데이터 행에 대한 필터링된 인덱스를 만들 수 잇습니다.</span><span class="sxs-lookup"><span data-stu-id="8ec97-130">For example, when the values in a column are mostly NULL and the query selects only from the non-NULL values, you can create a filtered index for the non-NULL data rows.</span></span> <span data-ttu-id="8ec97-131">결과 인덱스는 같은 키 열에서 정의된 전체 테이블 비클러스터형 인덱스에 비해 크기가 더 작고 유지 관리하는 비용이 더 적게 듭니다.</span><span class="sxs-lookup"><span data-stu-id="8ec97-131">The resulting index will be smaller and cost less to maintain than a full-table nonclustered index defined on the same key columns.</span></span>  
  
-   <span data-ttu-id="8ec97-132">테이블에 다른 유형의 데이터 행이 있는 경우 하나 이상의 데이터 범주에 대한 필터링된 인덱스를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ec97-132">When a table has heterogeneous data rows, you can create a filtered index for one or more categories of data.</span></span> <span data-ttu-id="8ec97-133">이렇게 하면 쿼리의 초점이 테이블의 특정 영역으로 제한되므로 이러한 데이터에 대한 쿼리 성능이 향상될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ec97-133">This can improve the performance of queries on these data rows by narrowing the focus of a query to a specific area of the table.</span></span> <span data-ttu-id="8ec97-134">결과 인덱스는 전체 테이블 비클러스터형 인덱스에 비해 크기가 더 작고 유지 관리하는 비용이 더 적게 듭니다.</span><span class="sxs-lookup"><span data-stu-id="8ec97-134">Again, the resulting index will be smaller and cost less to maintain than a full-table nonclustered index.</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="8ec97-135">제한 사항</span><span class="sxs-lookup"><span data-stu-id="8ec97-135">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="8ec97-136">뷰에서 필터링된 인덱스를 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8ec97-136">You cannot create a filtered index on a view.</span></span> <span data-ttu-id="8ec97-137">그러나 쿼리 최적화 프로그램에는 뷰에서 참조되는 테이블에 정의되는 필터링된 인덱스에 성능상 이점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ec97-137">However, the query optimizer can benefit from a filtered index defined on a table that is referenced in a view.</span></span> <span data-ttu-id="8ec97-138">쿼리 최적화 프로그램에서는 쿼리 결과가 수정될 경우 뷰에서 선택하는 쿼리에 대한 필터링된 인덱스를 검토합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec97-138">The query optimizer considers a filtered index for a query that selects from a view if the query results will be correct.</span></span>  
  
-   <span data-ttu-id="8ec97-139">필터링된 인덱스에는 인덱싱된 뷰에 비해 다음과 같은 이점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ec97-139">Filtered indexes have the following advantages over indexed views:</span></span>  
  
    -   <span data-ttu-id="8ec97-140">줄어든 인덱스 유지 관리 비용.</span><span class="sxs-lookup"><span data-stu-id="8ec97-140">Reduced index maintenance costs.</span></span> <span data-ttu-id="8ec97-141">예를 들어 쿼리 프로세서에서 필터링된 인덱스를 업데이트하는 데 인덱싱된 뷰보다 적은 CPU 리소스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec97-141">For example, the query processor uses fewer CPU resources to update a filtered index than an indexed view.</span></span>  
  
    -   <span data-ttu-id="8ec97-142">향상된 계획 품질.</span><span class="sxs-lookup"><span data-stu-id="8ec97-142">Improved plan quality.</span></span> <span data-ttu-id="8ec97-143">예를 들어 쿼리 컴파일 중에 쿼리 최적화 프로그램이 인덱싱된 뷰보다 더 많은 경우에 필터링된 인덱스의 사용을 고려합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec97-143">For example, during query compilation, the query optimizer considers using a filtered index in more situations than the equivalent indexed view.</span></span>  
  
    -   <span data-ttu-id="8ec97-144">온라인 인덱스 다시 작성.</span><span class="sxs-lookup"><span data-stu-id="8ec97-144">Online index rebuilds.</span></span> <span data-ttu-id="8ec97-145">필터링된 인덱스를 쿼리에 사용할 수 있는 동시에 다시 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ec97-145">You can rebuild filtered indexes while they are available for queries.</span></span> <span data-ttu-id="8ec97-146">인덱싱된 뷰에 대해서는 온라인 인덱스 다시 작성이 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8ec97-146">Online index rebuilds are not supported for indexed views.</span></span> <span data-ttu-id="8ec97-147">자세한 내용은 [ALTER INDEX&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql)에 대한 REBUILD 옵션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8ec97-147">For more information, see the REBUILD option for [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql).</span></span>  
  
    -   <span data-ttu-id="8ec97-148">고유하지 않은 인덱스.</span><span class="sxs-lookup"><span data-stu-id="8ec97-148">Non-unique indexes.</span></span> <span data-ttu-id="8ec97-149">필터링된 인덱스는 고유하지 않아도 되지만 인덱싱된 뷰는 반드시 고유해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec97-149">Filtered indexes can be non-unique, whereas indexed views must be unique.</span></span>  
  
-   <span data-ttu-id="8ec97-150">필터링된 인덱스는 하나의 테이블에서 정의되고 간단한 비교 논리만 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec97-150">Filtered indexes are defined on one table and only support simple comparison operators.</span></span> <span data-ttu-id="8ec97-151">여러 테이블을 참조하거나 복잡한 논리를 사용하는 필터 식이 필요할 경우 뷰를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec97-151">If you need a filter expression that references multiple tables or has complex logic, you should create a view.</span></span>  
  
-   <span data-ttu-id="8ec97-152">필터링된 인덱스 식이 쿼리 조건자와 같고 쿼리가 쿼리 결과로 필터링된 인덱스 식의 열을 반환하지 않는다면 필터링된 인덱스 식의 열이 필터링된 인덱스 정의의 포괄 열 또는 키여야 할 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8ec97-152">A column in the filtered index expression does not need to be a key or included column in the filtered index definition if the filtered index expression is equivalent to the query predicate and the query does not return the column in the filtered index expression with the query results.</span></span>  
  
-   <span data-ttu-id="8ec97-153">쿼리 조건자가 필터링된 인덱스 식과 다른 비교에 필터링된 인덱스 식의 열을 사용하면 해당 열은 필터링된 인덱스 정의의 포괄 열 또는 키여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec97-153">A column in the filtered index expression should be a key or included column in the filtered index definition if the query predicate uses the column in a comparison that is not equivalent to the filtered index expression.</span></span>  
  
-   <span data-ttu-id="8ec97-154">필터링된 인덱스 식의 열이 쿼리 결과 집합에 있으면 해당 열은 필터링된 인덱스 정의의 포괄 열 또는 키여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec97-154">A column in the filtered index expression should be a key or included column in the filtered index definition if the column is in the query result set.</span></span>  
  
-   <span data-ttu-id="8ec97-155">테이블의 클러스터형 인덱스 키가 필터링된 인덱스 정의의 포괄 열 또는 키여야 할 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8ec97-155">The clustered index key of the table does not need to be a key or included column in the filtered index definition.</span></span> <span data-ttu-id="8ec97-156">클러스터형 인덱스 키는 필터링된 인덱스를 비롯하여 모든 비클러스터형 인덱스에 자동으로 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ec97-156">The clustered index key is automatically included in all nonclustered indexes, including filtered indexes.</span></span>  
  
-   <span data-ttu-id="8ec97-157">필터링된 인덱스의 필터링된 인덱스 식에 지정된 비교 연산자로 인해 암시적 또는 명시적 데이터 변환이 발생할 경우 비교 연산자의 왼쪽에서 변환이 일어나면 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec97-157">If the comparison operator specified in the filtered index expression of the filtered index results in an implicit or explicit data conversion, an error will occur if the conversion occurs on the left side of a comparison operator.</span></span> <span data-ttu-id="8ec97-158">이에 대한 해결 방법은 비교 연산자의 오른쪽에 데이터 변환 연산자(CAST 또는 CONVERT)를 사용하여 필터링된 인덱스 식을 작성하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="8ec97-158">A solution is to write the filtered index expression with the data conversion operator (CAST or CONVERT) on the right side of the comparison operator.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="8ec97-159">보안</span><span class="sxs-lookup"><span data-stu-id="8ec97-159">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="8ec97-160">권한</span><span class="sxs-lookup"><span data-stu-id="8ec97-160">Permissions</span></span>  
 <span data-ttu-id="8ec97-161">테이블이나 뷰에 대한 ALTER 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec97-161">Requires ALTER permission on the table or view.</span></span> <span data-ttu-id="8ec97-162">사용자는 **sysadmin** 고정 서버 역할의 멤버 또는 **db_ddladmin** 및 **db_owner** 고정 데이터베이스 역할의 멤버여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec97-162">User must be a member of the **sysadmin** fixed server role or the **db_ddladmin** and **db_owner** fixed database roles.</span></span> <span data-ttu-id="8ec97-163">필터링된 인덱스를 수정하려면 CREATE INDEX WITH DROP_EXISTING을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec97-163">To modify the filtered index expression, use CREATE INDEX WITH DROP_EXISTING.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="8ec97-164">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="8ec97-164">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-a-filtered-index"></a><span data-ttu-id="8ec97-165">필터링된 인덱스를 만들려면</span><span class="sxs-lookup"><span data-stu-id="8ec97-165">To create a filtered index</span></span>  
  
1.  <span data-ttu-id="8ec97-166">개체 탐색기에서 더하기 기호를 클릭하여 필터링된 인덱스를 만들 테이블이 포함된 데이터베이스를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec97-166">In Object Explorer, click the plus sign to expand the database that contains the table on which you want to create a filtered index.</span></span>  
  
2.  <span data-ttu-id="8ec97-167">더하기 기호를 클릭하여 **테이블** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec97-167">Click the plus sign to expand the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="8ec97-168">더하기 기호를 클릭하여 필터링된 인덱스를 만들 테이블을 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec97-168">Click the plus sign to expand the table on which you want to create a filtered index.</span></span>  
  
4.  <span data-ttu-id="8ec97-169">**인덱스** 폴더를 마우스 오른쪽 단추로 클릭하고 **새 인덱스**를 가리킨 다음, **비클러스터형 인덱스...** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec97-169">Right-click the **Indexes** folder, point to **New Index**, and select **Non-Clustered Index...**.</span></span>  
  
5.  <span data-ttu-id="8ec97-170">**새 인덱스** 대화 상자의 **일반** 페이지에서 **인덱스 이름** 상자에 새 인덱스의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec97-170">In the **New Index** dialog box, on the **General** page, enter the name of the new index in the **Index name** box.</span></span>  
  
6.  <span data-ttu-id="8ec97-171">**인덱스 키 열** 아래에서 **추가...** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec97-171">Under **Index key columns**, click **Add...**.</span></span>  
  
7.  <span data-ttu-id="8ec97-172">_Table_name_ **에서 열 선택**대화 상자에서 고유 인덱스에 추가할 테이블 열의 확인란을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec97-172">In the **Select Columns from**_table_name_ dialog box, select the check box or check boxes of the table column or columns to be added to the unique index.</span></span>  
  
8.  <span data-ttu-id="8ec97-173">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec97-173">Click **OK**.</span></span>  
  
9. <span data-ttu-id="8ec97-174">**필터** 페이지의 **필터 식**에 필터링된 인덱스를 만드는 데 사용할 SQL 식을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec97-174">On the **Filter** page, under **Filter Expression**, enter SQL expression that you'll use to create the filtered index.</span></span>  
  
10. <span data-ttu-id="8ec97-175">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec97-175">Click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="8ec97-176">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="8ec97-176">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-filtered-index"></a><span data-ttu-id="8ec97-177">필터링된 인덱스를 만들려면</span><span class="sxs-lookup"><span data-stu-id="8ec97-177">To create a filtered index</span></span>  
  
1.  <span data-ttu-id="8ec97-178">**개체 탐색기**에서 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec97-178">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="8ec97-179">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec97-179">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="8ec97-180">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec97-180">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- Looks for an existing filtered index named "FIBillOfMaterialsWithEndDate"  
    -- and deletes it from the table Production.BillOfMaterials if found.   
    IF EXISTS (SELECT name FROM sys.indexes  
        WHERE name = N'FIBillOfMaterialsWithEndDate'  
        AND object_id = OBJECT_ID (N'Production.BillOfMaterials'))  
    DROP INDEX FIBillOfMaterialsWithEndDate  
        ON Production.BillOfMaterials  
    GO  
    -- Creates a filtered index "FIBillOfMaterialsWithEndDate"  
    -- on the table Production.BillOfMaterials   
    -- using the columms ComponentID and StartDate.  
  
    CREATE NONCLUSTERED INDEX FIBillOfMaterialsWithEndDate  
        ON Production.BillOfMaterials (ComponentID, StartDate)  
        WHERE EndDate IS NOT NULL ;  
    GO  
    ```  
  
     <span data-ttu-id="8ec97-181">위 필터링된 인덱스 는 다음 쿼리에 적합합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec97-181">The filtered index above is valid for the following query.</span></span> <span data-ttu-id="8ec97-182">이 필터링된 인덱스가 쿼리 최적화 프로그램에서 사용되는지 확인하기 위해 쿼리 실행 계획을 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ec97-182">You can display the query execution plan to determine if the query optimizer used the filtered index.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT ProductAssemblyID, ComponentID, StartDate   
    FROM Production.BillOfMaterials  
    WHERE EndDate IS NOT NULL   
        AND ComponentID = 5   
        AND StartDate > '01/01/2008' ;  
    GO  
    ```  
  
#### <a name="to-ensure-that-a-filtered-index-is-used-in-a-sql-query"></a><span data-ttu-id="8ec97-183">필터링된 인덱스가 SQL 쿼리에 사용되도록 하려면</span><span class="sxs-lookup"><span data-stu-id="8ec97-183">To ensure that a filtered index is used in a SQL query</span></span>  
  
1.  <span data-ttu-id="8ec97-184">**개체 탐색기**에서 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec97-184">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="8ec97-185">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec97-185">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="8ec97-186">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec97-186">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT ComponentID, StartDate FROM Production.BillOfMaterials  
        WITH ( INDEX ( FIBillOfMaterialsWithEndDate ) )   
    WHERE EndDate IN ('20000825', '20000908', '20000918');   
    GO  
    ```  
  
 <span data-ttu-id="8ec97-187">자세한 내용은 [CREATE INDEX&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8ec97-187">For more information, see  [CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql).</span></span>  
  
  
