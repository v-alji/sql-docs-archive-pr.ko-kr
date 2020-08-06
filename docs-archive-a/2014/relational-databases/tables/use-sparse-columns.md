---
title: 스파스 열 사용 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- sparse columns, described
- null columns
- sparse columns
ms.assetid: ea7ddb87-f50b-46b6-9f5a-acab222a2ede
author: stevestein
ms.author: sstein
ms.openlocfilehash: b3068ac7a3094605bb809ac84c63766b64fda486
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650860"
---
# <a name="use-sparse-columns"></a><span data-ttu-id="c2da6-102">스파스 열 사용</span><span class="sxs-lookup"><span data-stu-id="c2da6-102">Use Sparse Columns</span></span>
  <span data-ttu-id="c2da6-103">스파스 열은 Null 값에 대해 최적화된 스토리지가 있는 일반 열입니다.</span><span class="sxs-lookup"><span data-stu-id="c2da6-103">Sparse columns are ordinary columns that have an optimized storage for null values.</span></span> <span data-ttu-id="c2da6-104">스파스 열을 사용하면 Null 값에 대한 공간 요구 사항이 줄어드는 반면 Null이 아닌 값을 검색하는 데 더 많은 오버헤드가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="c2da6-104">Sparse columns reduce the space requirements for null values at the cost of more overhead to retrieve nonnull values.</span></span> <span data-ttu-id="c2da6-105">최소 20%에서 40% 사이의 공간이 절약되는 경우에는 스파스 열을 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="c2da6-105">Consider using sparse columns when the space saved is at least 20 percent to 40 percent.</span></span> <span data-ttu-id="c2da6-106">스파스 열 및 열 집합은 [CREATE TABLE](/sql/t-sql/statements/create-table-transact-sql) 또는 [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql) 문을 사용하여 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="c2da6-106">Sparse columns and column sets are defined by using the [CREATE TABLE](/sql/t-sql/statements/create-table-transact-sql) or [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql) statements.</span></span>  
  
 <span data-ttu-id="c2da6-107">스파스 열은 열 집합 및 필터링된 인덱스와 함께 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2da6-107">Sparse columns can be used with column sets and filtered indexes:</span></span>  
  
-   <span data-ttu-id="c2da6-108">열 집합</span><span class="sxs-lookup"><span data-stu-id="c2da6-108">Column sets</span></span>  
  
     <span data-ttu-id="c2da6-109">INSERT, UPDATE 및 DELETE 문은 이름별로 스파스 열을 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2da6-109">INSERT, UPDATE, and DELETE statements can reference the sparse columns by name.</span></span> <span data-ttu-id="c2da6-110">그러나 단일 XML 열에 결합된 테이블의 모든 스파스 열을 보고 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2da6-110">However, you can also view and work with all the sparse columns of a table that are combined into a single XML column.</span></span> <span data-ttu-id="c2da6-111">이러한 열을 열 집합이라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2da6-111">This column is called a column set.</span></span> <span data-ttu-id="c2da6-112">열 집합에 대한 자세한 내용은 [열 집합 사용](../tables/use-column-sets.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c2da6-112">For more information about column sets, see [Use Column Sets](../tables/use-column-sets.md).</span></span>  
  
-   <span data-ttu-id="c2da6-113">필터링된 인덱스</span><span class="sxs-lookup"><span data-stu-id="c2da6-113">Filtered indexes</span></span>  
  
     <span data-ttu-id="c2da6-114">스파스 열은 Null 값 행을 많이 포함하므로 필터링된 인덱스에 특히 적합합니다.</span><span class="sxs-lookup"><span data-stu-id="c2da6-114">Because sparse columns have many null-valued rows, they are especially appropriate for filtered indexes.</span></span> <span data-ttu-id="c2da6-115">스파스 열에 대한 필터링된 인덱스는 채워진 값을 포함하는 행만 인덱싱할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2da6-115">A filtered index on a sparse column can index only the rows that have populated values.</span></span> <span data-ttu-id="c2da6-116">따라서 보다 작고 효율적인 인덱스가 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="c2da6-116">This creates a smaller and more efficient index.</span></span> <span data-ttu-id="c2da6-117">자세한 내용은 [Create Filtered Indexes](../indexes/indexes.md)을(를) 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c2da6-117">For more information, see [Create Filtered Indexes](../indexes/indexes.md).</span></span>  
  
 <span data-ttu-id="c2da6-118">스파스 열 및 필터링된 인덱스를 통해 [!INCLUDE[winSPServ](../../includes/winspserv-md.md)]와 같은 애플리케이션에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]을 사용하여 많은 수의 사용자 정의 속성을 효율적으로 저장하고 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2da6-118">Sparse columns and filtered indexes enable applications, such as [!INCLUDE[winSPServ](../../includes/winspserv-md.md)], to efficiently store and access a large number of user-defined properties by using [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
## <a name="properties-of-sparse-columns"></a><span data-ttu-id="c2da6-119">스파스 열 속성</span><span class="sxs-lookup"><span data-stu-id="c2da6-119">Properties of Sparse Columns</span></span>  
 <span data-ttu-id="c2da6-120">스파스 열에는 다음과 같은 특징이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2da6-120">Sparse columns have the following characteristics:</span></span>  
  
-   <span data-ttu-id="c2da6-121">[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 은 열 정의에 SPARSE 키워드를 사용하여 해당 열의 값 스토리지를 최적화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2da6-121">The [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] uses the SPARSE keyword in a column definition to optimize the storage of values in that column.</span></span> <span data-ttu-id="c2da6-122">따라서 테이블에 있는 행에 대해 열 값이 NULL인 경우 값을 스토리지할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c2da6-122">Therefore, when the column value is NULL for any row in the table, the values require no storage.</span></span>  
  
-   <span data-ttu-id="c2da6-123">스파스 열을 포함하는 테이블에 대한 카탈로그 뷰는 일반적인 테이블에 대한 카탈로그 뷰와 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="c2da6-123">Catalog views for a table that has sparse columns are the same as for a typical table.</span></span> <span data-ttu-id="c2da6-124">sys.columns 카탈로그 뷰는 테이블의 각 열에 대한 행을 포함하고 열 집합(정의된 경우)을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="c2da6-124">The sys.columns catalog view contains a row for each column in the table and includes a column set if one is defined.</span></span>  
  
-   <span data-ttu-id="c2da6-125">스파스 열은 논리적 테이블이 아닌 스토리지 계층의 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="c2da6-125">Sparse columns are a property of the storage layer, rather than the logical table.</span></span> <span data-ttu-id="c2da6-126">따라서 SELECT...INTO 문은 스파스 열 속성을 새 테이블에 복사하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c2da6-126">Therefore a SELECT...INTO statement does not copy over the sparse column property into a new table.</span></span>  
  
-   <span data-ttu-id="c2da6-127">COLUMNS_UPDATED 함수는 `varbinary` 값을 반환하여 DML 동작을 수행하는 동안 업데이트된 모든 열을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c2da6-127">The COLUMNS_UPDATED function returns a `varbinary` value to indicate all the columns that were updated during a DML action.</span></span> <span data-ttu-id="c2da6-128">COLUMNS_UPDATED 함수에 의해 반환된 비트는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="c2da6-128">The bits that are returned by the COLUMNS_UPDATED function are as follows:</span></span>  
  
    -   <span data-ttu-id="c2da6-129">스파스 열이 명시적으로 업데이트되면 해당 스파스 열에 대한 비트가 1로 설정되고 열 집합에 대한 비트가 1로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="c2da6-129">When a sparse column is explicitly updated, the corresponding bit for that sparse column is set to 1, and the bit for the column set is set to 1.</span></span>  
  
    -   <span data-ttu-id="c2da6-130">열 집합이 명시적으로 업데이트되면 열 집합에 대한 비트가 1로 설정되고 해당 테이블의 모든 스파스 열에 대한 비트가 1로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="c2da6-130">When a column set is explicitly updated, the bit for the column set is set to 1, and the bits for all the sparse columns in that table are set to 1.</span></span>  
  
    -   <span data-ttu-id="c2da6-131">삽입 작업의 경우 모든 비트가 1로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="c2da6-131">For insert operations, all bits are set to 1.</span></span>  
  
     <span data-ttu-id="c2da6-132">열 집합에 대한 자세한 내용은 [열 집합 사용](../tables/use-column-sets.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c2da6-132">For more information about columns sets, see [Use Column Sets](../tables/use-column-sets.md).</span></span>  
  
 <span data-ttu-id="c2da6-133">다음 데이터 형식은 SPARSE로 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c2da6-133">The following data types cannot be specified as SPARSE:</span></span>  
  
|||  
|-|-|  
|`geography`|`text`|  
|`geometry`|`timestamp`|  
|`image`|`user-defined data types`|  
|`ntext`||  
  
## <a name="estimated-space-savings-by-data-type"></a><span data-ttu-id="c2da6-134">데이터 형식별 예상 공간 절약</span><span class="sxs-lookup"><span data-stu-id="c2da6-134">Estimated Space Savings by Data Type</span></span>  
 <span data-ttu-id="c2da6-135">스파스 열을 사용하면 SPARSE로 표시되지 않은 동일한 데이터에 대해 필요한 공간보다 Null이 아닌 값에 더 많은 스토리지 공간이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="c2da6-135">Sparse columns require more storage space for nonnull values than the space required for identical data that is not marked SPARSE.</span></span> <span data-ttu-id="c2da6-136">다음 표에서는 각 데이터 형식에 대한 공간 사용률을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c2da6-136">The following tables show the space usage for each data type.</span></span> <span data-ttu-id="c2da6-137">**NULL 백분율** 열은 40%의 순 공간 절약을 위해 NULL이어야 하는 데이터 비율을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c2da6-137">The **NULL Percentage** column indicates what percent of the data must be NULL for a net space savings of 40 percent.</span></span>  
  
 <span data-ttu-id="c2da6-138">**고정 길이 데이터 형식**</span><span class="sxs-lookup"><span data-stu-id="c2da6-138">**Fixed-Length Data Types**</span></span>  
  
|<span data-ttu-id="c2da6-139">데이터 형식</span><span class="sxs-lookup"><span data-stu-id="c2da6-139">Data type</span></span>|<span data-ttu-id="c2da6-140">비-스파스 바이트</span><span class="sxs-lookup"><span data-stu-id="c2da6-140">Nonsparse bytes</span></span>|<span data-ttu-id="c2da6-141">스파스 바이트</span><span class="sxs-lookup"><span data-stu-id="c2da6-141">Sparse bytes</span></span>|<span data-ttu-id="c2da6-142">NULL 백분율</span><span class="sxs-lookup"><span data-stu-id="c2da6-142">NULL percentage</span></span>|  
|---------------|---------------------|------------------|---------------------|  
|`bit`|<span data-ttu-id="c2da6-143">0.125</span><span class="sxs-lookup"><span data-stu-id="c2da6-143">0.125</span></span>|<span data-ttu-id="c2da6-144">5</span><span class="sxs-lookup"><span data-stu-id="c2da6-144">5</span></span>|<span data-ttu-id="c2da6-145">98%</span><span class="sxs-lookup"><span data-stu-id="c2da6-145">98%</span></span>|  
|`tinyint`|<span data-ttu-id="c2da6-146">1</span><span class="sxs-lookup"><span data-stu-id="c2da6-146">1</span></span>|<span data-ttu-id="c2da6-147">5</span><span class="sxs-lookup"><span data-stu-id="c2da6-147">5</span></span>|<span data-ttu-id="c2da6-148">86%</span><span class="sxs-lookup"><span data-stu-id="c2da6-148">86%</span></span>|  
|`smallint`|<span data-ttu-id="c2da6-149">2</span><span class="sxs-lookup"><span data-stu-id="c2da6-149">2</span></span>|<span data-ttu-id="c2da6-150">6</span><span class="sxs-lookup"><span data-stu-id="c2da6-150">6</span></span>|<span data-ttu-id="c2da6-151">76%</span><span class="sxs-lookup"><span data-stu-id="c2da6-151">76%</span></span>|  
|`int`|<span data-ttu-id="c2da6-152">4</span><span class="sxs-lookup"><span data-stu-id="c2da6-152">4</span></span>|<span data-ttu-id="c2da6-153">8</span><span class="sxs-lookup"><span data-stu-id="c2da6-153">8</span></span>|<span data-ttu-id="c2da6-154">64%</span><span class="sxs-lookup"><span data-stu-id="c2da6-154">64%</span></span>|  
|`bigint`|<span data-ttu-id="c2da6-155">8</span><span class="sxs-lookup"><span data-stu-id="c2da6-155">8</span></span>|<span data-ttu-id="c2da6-156">12</span><span class="sxs-lookup"><span data-stu-id="c2da6-156">12</span></span>|<span data-ttu-id="c2da6-157">52%</span><span class="sxs-lookup"><span data-stu-id="c2da6-157">52%</span></span>|  
|`real`|<span data-ttu-id="c2da6-158">4</span><span class="sxs-lookup"><span data-stu-id="c2da6-158">4</span></span>|<span data-ttu-id="c2da6-159">8</span><span class="sxs-lookup"><span data-stu-id="c2da6-159">8</span></span>|<span data-ttu-id="c2da6-160">64%</span><span class="sxs-lookup"><span data-stu-id="c2da6-160">64%</span></span>|  
|`float`|<span data-ttu-id="c2da6-161">8</span><span class="sxs-lookup"><span data-stu-id="c2da6-161">8</span></span>|<span data-ttu-id="c2da6-162">12</span><span class="sxs-lookup"><span data-stu-id="c2da6-162">12</span></span>|<span data-ttu-id="c2da6-163">52%</span><span class="sxs-lookup"><span data-stu-id="c2da6-163">52%</span></span>|  
|`smallmoney`|<span data-ttu-id="c2da6-164">4</span><span class="sxs-lookup"><span data-stu-id="c2da6-164">4</span></span>|<span data-ttu-id="c2da6-165">8</span><span class="sxs-lookup"><span data-stu-id="c2da6-165">8</span></span>|<span data-ttu-id="c2da6-166">64%</span><span class="sxs-lookup"><span data-stu-id="c2da6-166">64%</span></span>|  
|`money`|<span data-ttu-id="c2da6-167">8</span><span class="sxs-lookup"><span data-stu-id="c2da6-167">8</span></span>|<span data-ttu-id="c2da6-168">12</span><span class="sxs-lookup"><span data-stu-id="c2da6-168">12</span></span>|<span data-ttu-id="c2da6-169">52%</span><span class="sxs-lookup"><span data-stu-id="c2da6-169">52%</span></span>|  
|`smalldatetime`|<span data-ttu-id="c2da6-170">4</span><span class="sxs-lookup"><span data-stu-id="c2da6-170">4</span></span>|<span data-ttu-id="c2da6-171">8</span><span class="sxs-lookup"><span data-stu-id="c2da6-171">8</span></span>|<span data-ttu-id="c2da6-172">64%</span><span class="sxs-lookup"><span data-stu-id="c2da6-172">64%</span></span>|  
|`datetime`|<span data-ttu-id="c2da6-173">8</span><span class="sxs-lookup"><span data-stu-id="c2da6-173">8</span></span>|<span data-ttu-id="c2da6-174">12</span><span class="sxs-lookup"><span data-stu-id="c2da6-174">12</span></span>|<span data-ttu-id="c2da6-175">52%</span><span class="sxs-lookup"><span data-stu-id="c2da6-175">52%</span></span>|  
|`uniqueidentifier`|<span data-ttu-id="c2da6-176">16</span><span class="sxs-lookup"><span data-stu-id="c2da6-176">16</span></span>|<span data-ttu-id="c2da6-177">20</span><span class="sxs-lookup"><span data-stu-id="c2da6-177">20</span></span>|<span data-ttu-id="c2da6-178">43%</span><span class="sxs-lookup"><span data-stu-id="c2da6-178">43%</span></span>|  
|`date`|<span data-ttu-id="c2da6-179">3</span><span class="sxs-lookup"><span data-stu-id="c2da6-179">3</span></span>|<span data-ttu-id="c2da6-180">7</span><span class="sxs-lookup"><span data-stu-id="c2da6-180">7</span></span>|<span data-ttu-id="c2da6-181">69%</span><span class="sxs-lookup"><span data-stu-id="c2da6-181">69%</span></span>|  
  
 <span data-ttu-id="c2da6-182">**전체 자릿수 종속 길이 데이터 형식**</span><span class="sxs-lookup"><span data-stu-id="c2da6-182">**Precision-Dependent-Length Data Types**</span></span>  
  
|<span data-ttu-id="c2da6-183">데이터 형식</span><span class="sxs-lookup"><span data-stu-id="c2da6-183">Data type</span></span>|<span data-ttu-id="c2da6-184">비-스파스 바이트</span><span class="sxs-lookup"><span data-stu-id="c2da6-184">Nonsparse bytes</span></span>|<span data-ttu-id="c2da6-185">스파스 바이트</span><span class="sxs-lookup"><span data-stu-id="c2da6-185">Sparse bytes</span></span>|<span data-ttu-id="c2da6-186">NULL 백분율</span><span class="sxs-lookup"><span data-stu-id="c2da6-186">NULL percentage</span></span>|  
|---------------|---------------------|------------------|---------------------|  
|`datetime2(0)`|<span data-ttu-id="c2da6-187">6</span><span class="sxs-lookup"><span data-stu-id="c2da6-187">6</span></span>|<span data-ttu-id="c2da6-188">10</span><span class="sxs-lookup"><span data-stu-id="c2da6-188">10</span></span>|<span data-ttu-id="c2da6-189">57%</span><span class="sxs-lookup"><span data-stu-id="c2da6-189">57%</span></span>|  
|`datetime2(7)`|<span data-ttu-id="c2da6-190">8</span><span class="sxs-lookup"><span data-stu-id="c2da6-190">8</span></span>|<span data-ttu-id="c2da6-191">12</span><span class="sxs-lookup"><span data-stu-id="c2da6-191">12</span></span>|<span data-ttu-id="c2da6-192">52%</span><span class="sxs-lookup"><span data-stu-id="c2da6-192">52%</span></span>|  
|`time(0)`|<span data-ttu-id="c2da6-193">3</span><span class="sxs-lookup"><span data-stu-id="c2da6-193">3</span></span>|<span data-ttu-id="c2da6-194">7</span><span class="sxs-lookup"><span data-stu-id="c2da6-194">7</span></span>|<span data-ttu-id="c2da6-195">69%</span><span class="sxs-lookup"><span data-stu-id="c2da6-195">69%</span></span>|  
|`time(7)`|<span data-ttu-id="c2da6-196">5</span><span class="sxs-lookup"><span data-stu-id="c2da6-196">5</span></span>|<span data-ttu-id="c2da6-197">9</span><span class="sxs-lookup"><span data-stu-id="c2da6-197">9</span></span>|<span data-ttu-id="c2da6-198">60%</span><span class="sxs-lookup"><span data-stu-id="c2da6-198">60%</span></span>|  
|`datetimetoffset(0)`|<span data-ttu-id="c2da6-199">8</span><span class="sxs-lookup"><span data-stu-id="c2da6-199">8</span></span>|<span data-ttu-id="c2da6-200">12</span><span class="sxs-lookup"><span data-stu-id="c2da6-200">12</span></span>|<span data-ttu-id="c2da6-201">52%</span><span class="sxs-lookup"><span data-stu-id="c2da6-201">52%</span></span>|  
|`datetimetoffset (7)`|<span data-ttu-id="c2da6-202">10</span><span class="sxs-lookup"><span data-stu-id="c2da6-202">10</span></span>|<span data-ttu-id="c2da6-203">14</span><span class="sxs-lookup"><span data-stu-id="c2da6-203">14</span></span>|<span data-ttu-id="c2da6-204">49%</span><span class="sxs-lookup"><span data-stu-id="c2da6-204">49%</span></span>|  
|`decimal/numeric(1,s)`|<span data-ttu-id="c2da6-205">5</span><span class="sxs-lookup"><span data-stu-id="c2da6-205">5</span></span>|<span data-ttu-id="c2da6-206">9</span><span class="sxs-lookup"><span data-stu-id="c2da6-206">9</span></span>|<span data-ttu-id="c2da6-207">60%</span><span class="sxs-lookup"><span data-stu-id="c2da6-207">60%</span></span>|  
|`decimal/numeric(38,s)`|<span data-ttu-id="c2da6-208">17</span><span class="sxs-lookup"><span data-stu-id="c2da6-208">17</span></span>|<span data-ttu-id="c2da6-209">21</span><span class="sxs-lookup"><span data-stu-id="c2da6-209">21</span></span>|<span data-ttu-id="c2da6-210">42%</span><span class="sxs-lookup"><span data-stu-id="c2da6-210">42%</span></span>|  
|`vardecimal(p,s)`|<span data-ttu-id="c2da6-211">`decimal` 형식을 일반적인 예상치로 사용</span><span class="sxs-lookup"><span data-stu-id="c2da6-211">Use the `decimal` type as a conservative estimate.</span></span>|||  
  
 <span data-ttu-id="c2da6-212">**데이터 종속 길이 데이터 형식**</span><span class="sxs-lookup"><span data-stu-id="c2da6-212">**Data-Dependent-Length Data Types**</span></span>  
  
|<span data-ttu-id="c2da6-213">데이터 형식</span><span class="sxs-lookup"><span data-stu-id="c2da6-213">Data type</span></span>|<span data-ttu-id="c2da6-214">비-스파스 바이트</span><span class="sxs-lookup"><span data-stu-id="c2da6-214">Nonsparse bytes</span></span>|<span data-ttu-id="c2da6-215">스파스 바이트</span><span class="sxs-lookup"><span data-stu-id="c2da6-215">Sparse bytes</span></span>|<span data-ttu-id="c2da6-216">NULL 백분율</span><span class="sxs-lookup"><span data-stu-id="c2da6-216">NULL percentage</span></span>|  
|---------------|---------------------|------------------|---------------------|  
|`sql_variant`|<span data-ttu-id="c2da6-217">기본 데이터 형식에 따라 다름</span><span class="sxs-lookup"><span data-stu-id="c2da6-217">Varies with the underlying data type</span></span>|||  
|<span data-ttu-id="c2da6-218">`varchar` 또는 `char`</span><span class="sxs-lookup"><span data-stu-id="c2da6-218">`varchar` or `char`</span></span>|<span data-ttu-id="c2da6-219">2\*</span><span class="sxs-lookup"><span data-stu-id="c2da6-219">2\*</span></span>|<span data-ttu-id="c2da6-220">4\*</span><span class="sxs-lookup"><span data-stu-id="c2da6-220">4\*</span></span>|<span data-ttu-id="c2da6-221">60%</span><span class="sxs-lookup"><span data-stu-id="c2da6-221">60%</span></span>|  
|<span data-ttu-id="c2da6-222">`nvarchar` 또는 `nchar`</span><span class="sxs-lookup"><span data-stu-id="c2da6-222">`nvarchar` or `nchar`</span></span>|<span data-ttu-id="c2da6-223">2\*</span><span class="sxs-lookup"><span data-stu-id="c2da6-223">2\*</span></span>|<span data-ttu-id="c2da6-224">4\*+</span><span class="sxs-lookup"><span data-stu-id="c2da6-224">4\*+</span></span>|<span data-ttu-id="c2da6-225">60%</span><span class="sxs-lookup"><span data-stu-id="c2da6-225">60%</span></span>|  
|<span data-ttu-id="c2da6-226">`varbinary` 또는 `binary`</span><span class="sxs-lookup"><span data-stu-id="c2da6-226">`varbinary` or `binary`</span></span>|<span data-ttu-id="c2da6-227">2\*</span><span class="sxs-lookup"><span data-stu-id="c2da6-227">2\*</span></span>|<span data-ttu-id="c2da6-228">4\*</span><span class="sxs-lookup"><span data-stu-id="c2da6-228">4\*</span></span>|<span data-ttu-id="c2da6-229">60%</span><span class="sxs-lookup"><span data-stu-id="c2da6-229">60%</span></span>|  
|`xml`|<span data-ttu-id="c2da6-230">2\*</span><span class="sxs-lookup"><span data-stu-id="c2da6-230">2\*</span></span>|<span data-ttu-id="c2da6-231">4\*</span><span class="sxs-lookup"><span data-stu-id="c2da6-231">4\*</span></span>|<span data-ttu-id="c2da6-232">60%</span><span class="sxs-lookup"><span data-stu-id="c2da6-232">60%</span></span>|  
|`hierarchyid`|<span data-ttu-id="c2da6-233">2\*</span><span class="sxs-lookup"><span data-stu-id="c2da6-233">2\*</span></span>|<span data-ttu-id="c2da6-234">4\*</span><span class="sxs-lookup"><span data-stu-id="c2da6-234">4\*</span></span>|<span data-ttu-id="c2da6-235">60%</span><span class="sxs-lookup"><span data-stu-id="c2da6-235">60%</span></span>|  
  
 <span data-ttu-id="c2da6-236">\*길이는 형식에 포함된 데이터의 평균에 2바이트 또는 4바이트를 더한 값과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="c2da6-236">\*The length is equal to the average of the data that is contained in the type, plus 2 or 4 bytes.</span></span>  
  
## <a name="in-memory-overhead-required-for-updates-to-sparse-columns"></a><span data-ttu-id="c2da6-237">스파스 열을 업데이트하려면 메모리 내 오버헤드가 필요함</span><span class="sxs-lookup"><span data-stu-id="c2da6-237">In-Memory Overhead Required for Updates to Sparse Columns</span></span>  
 <span data-ttu-id="c2da6-238">스파스 열을 사용하여 테이블을 디자인하는 경우 행이 업데이트될 때 테이블에서 null이 아닌 스파스 열 각각에 대해 2바이트의 추가 오버헤드가 필요함에 유의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2da6-238">When designing tables with sparse columns, keep in mind that an additional 2 bytes of overhead are required for each non-null sparse column in the table when a row is being updated.</span></span> <span data-ttu-id="c2da6-239">이러한 추가 메모리 요구 사항으로 인해 이 메모리 오버헤드를 포함한 총 행 크기가 8019를 초과하여 열을 행에 밀어넣을 수 없으므로 예기치 않게 576 오류가 발생하여 업데이트가 실패할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2da6-239">As a result of this additional memory requirement, updates can fail unexpectedly with error 576 when the total row size, including this memory overhead, exceeds 8019, and no columns can be pushed off the row.</span></span>  
  
 <span data-ttu-id="c2da6-240">bigint 형식의 600개 스파스 열을 가진 테이블의 예를 살펴 보십시오.</span><span class="sxs-lookup"><span data-stu-id="c2da6-240">Consider the example of a table that has 600 sparse columns of type bigint.</span></span> <span data-ttu-id="c2da6-241">571개의 null이 아닌 열이 있는 경우 디스크의 총 크기는 571 \* 12 = 6852바이트입니다.</span><span class="sxs-lookup"><span data-stu-id="c2da6-241">If there are 571 non-null columns, then the total size on disk is 571 \* 12 = 6852 bytes.</span></span> <span data-ttu-id="c2da6-242">추가 행 오버로드와 스파스 열 머리글을 포함하면 약 6895바이트로 증가합니다.</span><span class="sxs-lookup"><span data-stu-id="c2da6-242">After including additional row overhead and the sparse column header, this increases to around 6895 bytes.</span></span> <span data-ttu-id="c2da6-243">페이지에는 여전히 디스크에서 사용 가능한 1124바이트가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2da6-243">The page still has around 1124 bytes available on disk.</span></span> <span data-ttu-id="c2da6-244">그러면 추가 열을 업데이트할 수 있는 것처럼 보일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2da6-244">This can give the impression that additional columns can be updated successfully.</span></span> <span data-ttu-id="c2da6-245">하지만 업데이트 중에 메모리에 2\*(null이 아닌 스파스 열의 수)에 해당하는 추가 오버헤드가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="c2da6-245">However, during the update, there is additional overhead in memory which is 2\*(number of non-null sparse columns).</span></span> <span data-ttu-id="c2da6-246">이 예제에서 추가 오버헤드(2 \* 571 = 1142바이트)를 포함하면 디스크의 행 크기가 약 8037바이트로 증가합니다.</span><span class="sxs-lookup"><span data-stu-id="c2da6-246">In this example, including the additional overhead - 2 \* 571 = 1142 bytes - increases the row size on disk to around 8037 bytes.</span></span> <span data-ttu-id="c2da6-247">이는 최대 허용 크기인 8019바이트를 초과합니다.</span><span class="sxs-lookup"><span data-stu-id="c2da6-247">This size exceeds the maximum allowed size of 8019 bytes.</span></span> <span data-ttu-id="c2da6-248">모든 열은 고정 길이 데이터 형식이므로 행에 밀어넣을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c2da6-248">Since all the columns are fixed-length data types, they cannot be pushed off the row.</span></span> <span data-ttu-id="c2da6-249">따라서 576 오류가 발생하여 업데이트가 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="c2da6-249">As a result, the update fails with the 576 error.</span></span>  
  
## <a name="restrictions-for-using-sparse-columns"></a><span data-ttu-id="c2da6-250">스파스 열 사용에 대한 제한 사항</span><span class="sxs-lookup"><span data-stu-id="c2da6-250">Restrictions for Using Sparse Columns</span></span>  
 <span data-ttu-id="c2da6-251">스파스 열은 모든 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터 형식을 사용할 수 있으며 다른 모든 열처럼 작동하지만 다음과 같은 제한 사항의 적용을 받습니다.</span><span class="sxs-lookup"><span data-stu-id="c2da6-251">Sparse columns can be of any [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data type and behave like any other column with the following restrictions:</span></span>  
  
-   <span data-ttu-id="c2da6-252">스파스 열은 Null을 허용해야 하며 ROWGUIDCOL 또는 IDENTITY 속성을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c2da6-252">A sparse column must be nullable and cannot have the ROWGUIDCOL or IDENTITY properties.</span></span> <span data-ttu-id="c2da6-253">스파스 열의 데이터 형식은 `text`, `ntext`, `image`, `timestamp`, 사용자 정의 데이터 형식, `geometry` 또는 `geography`일 수 없으며, 스파스 열에 FILESTREAM 특성을 가질 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c2da6-253">A sparse column cannot be of the following data types: `text`, `ntext`, `image`, `timestamp`, user-defined data type, `geometry`, or `geography`; or have the FILESTREAM attribute.</span></span>  
  
-   <span data-ttu-id="c2da6-254">스파스 열은 기본값을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c2da6-254">A sparse column cannot have a default value.</span></span>  
  
-   <span data-ttu-id="c2da6-255">스파스 열은 규칙에 바인딩할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c2da6-255">A sparse column cannot be bound to a rule.</span></span>  
  
-   <span data-ttu-id="c2da6-256">계산 열은 스파스 열을 포함할 수 있지만 이런 경우에도 계산 열을 SPARSE로 표시할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c2da6-256">Although a computed column can contain a sparse column, a computed column cannot be marked as SPARSE.</span></span>  
  
-   <span data-ttu-id="c2da6-257">스파스 열은 클러스터형 인덱스 또는 고유 기본 키 인덱스의 일부가 될 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c2da6-257">A sparse column cannot be part of a clustered index or a unique primary key index.</span></span> <span data-ttu-id="c2da6-258">그러나 스파스 열에 정의된 지속형 계산 열과 비지속형 계산 열 모두 클러스터형 키의 일부가 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2da6-258">However, both persisted and nonpersisted computed columns that are defined on sparse columns can be part of a clustered key.</span></span>  
  
-   <span data-ttu-id="c2da6-259">스파스 열은 클러스터형 인덱스 또는 힙의 파티션 키로 사용될 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c2da6-259">A sparse column cannot be used as a partition key of a clustered index or heap.</span></span> <span data-ttu-id="c2da6-260">그러나 스파스 열은 비클러스터형 인덱스의 파티션 키로 사용될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2da6-260">However, a sparse column can be used as the partition key of a nonclustered index.</span></span>  
  
-   <span data-ttu-id="c2da6-261">스파스 열은 테이블 변수 및 테이블 반환 매개 변수에 사용되는 사용자 정의 테이블 형식의 일부가 될 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c2da6-261">A sparse column cannot be part of a user-defined table type, which are used in table variables and table-valued parameters.</span></span>  
  
-   <span data-ttu-id="c2da6-262">스파스 열은 데이터 압축과 호환되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c2da6-262">Sparse columns are incompatible with data compression.</span></span> <span data-ttu-id="c2da6-263">따라서 스파스 열을 압축된 테이블에 추가할 수 없을 뿐만 아니라 스파스 열을 포함하는 테이블을 압축할 수도 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c2da6-263">Therefore sparse columns cannot be added to compressed tables, nor can any tables containing sparse columns be compressed.</span></span>  
  
-   <span data-ttu-id="c2da6-264">스파스 열에서 스파스가 아닌 열로 또는 스파스가 아닌 열에서 스파스 열로 열을 변경하려면 열의 스토리지 형식을 변경해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2da6-264">Changing a column from sparse to nonsparse or nonsparse to sparse requires changing the storage format of the column.</span></span> <span data-ttu-id="c2da6-265">SQL Server 데이터베이스 엔진에서는 다음 절차를 통해 이러한 변경을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="c2da6-265">The SQL Server Database Engine uses the following procedure to accomplish this change:</span></span>  
  
    1.  <span data-ttu-id="c2da6-266">새 스토리지 크기 및 형식으로 테이블에 새 열을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="c2da6-266">Adds a new column to the table in the new storage size and format.</span></span>  
  
    2.  <span data-ttu-id="c2da6-267">테이블의 각 행에 대해 기존 열에 저장된 값을 업데이트하고 새 열로 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="c2da6-267">For each row in the table, updates and copies the value stored in the old column to the new column.</span></span>  
  
    3.  <span data-ttu-id="c2da6-268">기존 열을 테이블 스키마에서 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="c2da6-268">Removes the old column from the table schema.</span></span>  
  
    4.  <span data-ttu-id="c2da6-269">테이블을 다시 작성하거나(클러스터형 인덱스가 없는 경우) 클러스터형 인덱스를 다시 작성하여 이전 열에 사용된 공간을 회수합니다.</span><span class="sxs-lookup"><span data-stu-id="c2da6-269">Rebuilds the table (if there is no clustered index) or rebuilds the clustered index to reclaim space used by the old column.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c2da6-270">행에 허용된 최대 행 크기를 초과하는 데이터가 있으면 2단계가 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="c2da6-270">Step 2 can fail when the size of the data in the row exceeds the maximum allowable row size.</span></span> <span data-ttu-id="c2da6-271">이 데이터 크기에는 기존 열에 저장된 데이터 및 업데이트되어 새 열에 저장된 데이터의 크기가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="c2da6-271">This size includes the size of the data stored in the old column and the updated data stored in the new column.</span></span> <span data-ttu-id="c2da6-272">스파스 열이 포함되지 않은 테이블의 경우 8060바이트, 스파스 열이 포함된 테이블의 경우 8018바이트로 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="c2da6-272">This limit is 8060 bytes for tables that do not contain any sparse columns or 8018 bytes for tables that contain sparse columns.</span></span> <span data-ttu-id="c2da6-273">데이터 크기로 인한 이 오류는 적합한 열을 행 외부로 밀어낸 경우에도 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="c2da6-273">This error can occur even if all eligible columns have been pushed off-row.</span></span>  
  
-   <span data-ttu-id="c2da6-274">스파스가 아닌 열을 스파스 열로 변경하면 스파스 열이 Null이 아닌 값에 대해 더 많은 공간을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="c2da6-274">When you change a non-sparse column to a sparse column, the sparse column will consume more space for non-null values.</span></span> <span data-ttu-id="c2da6-275">행이 최대 행 크기 제한에 가까우면 작업이 실패할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2da6-275">When a row is close to the maximum row size limit, the operation can fail.</span></span>  
  
## <a name="sql-server-technologies-that-support-sparse-columns"></a><span data-ttu-id="c2da6-276">스파스 열을 지원하는 SQL Server 기술</span><span class="sxs-lookup"><span data-stu-id="c2da6-276">SQL Server Technologies That Support Sparse Columns</span></span>  
 <span data-ttu-id="c2da6-277">이 섹션에서는 다음 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 기술에서 스파스 열을 지원하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="c2da6-277">This section describes how sparse columns are supported in the following [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] technologies:</span></span>  
  
-   <span data-ttu-id="c2da6-278">트랜잭션 복제</span><span class="sxs-lookup"><span data-stu-id="c2da6-278">Transactional replication</span></span>  
  
     <span data-ttu-id="c2da6-279">트랜잭션 복제는 스파스 열을 지원하지만 스파스 열에서 사용할 수 있는 열 집합은 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c2da6-279">Transactional replication supports sparse columns, but it does not support column sets, which can be used with sparse columns.</span></span> <span data-ttu-id="c2da6-280">열 집합에 대한 자세한 내용은 [열 집합 사용](../tables/use-column-sets.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c2da6-280">For more information about column sets, see [Use Column Sets](../tables/use-column-sets.md).</span></span>  
  
     <span data-ttu-id="c2da6-281">SPARSE 특성 복제는 [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql) 을 사용하거나 **에서** 아티클 속성 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]대화 상자를 사용하여 지정되는 스키마 옵션에 의해 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="c2da6-281">The replication of the SPARSE attribute is determined by a schema option that is specified by using [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql) or by using the **Article Properties** dialog box in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="c2da6-282">이전 버전의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서는 스파스 열이 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c2da6-282">Earlier versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] do not support sparse columns.</span></span> <span data-ttu-id="c2da6-283">데이터를 이전 버전으로 복제해야 하는 경우 SPARSE 특성을 복제하지 않도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c2da6-283">If you must replicate data to an earlier version, specify that the SPARSE attribute should not be replicated.</span></span>  
  
     <span data-ttu-id="c2da6-284">게시된 테이블의 경우 새 스파스 열을 테이블에 추가하거나 기존 열의 스파스 속성을 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c2da6-284">For tables that are published, you cannot add any new sparse columns to a table or change the sparse property of an existing column.</span></span> <span data-ttu-id="c2da6-285">이러한 작업이 필요한 경우 게시를 삭제한 다음 다시 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c2da6-285">If such an operation is required, drop and re-create the publication.</span></span>  
  
-   <span data-ttu-id="c2da6-286">병합 복제</span><span class="sxs-lookup"><span data-stu-id="c2da6-286">Merge replication</span></span>  
  
     <span data-ttu-id="c2da6-287">병합 복제는 스파스 열 또는 열 집합을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c2da6-287">Merge replication does not support sparse columns or column sets.</span></span>  
  
-   <span data-ttu-id="c2da6-288">Change tracking</span><span class="sxs-lookup"><span data-stu-id="c2da6-288">Change tracking</span></span>  
  
     <span data-ttu-id="c2da6-289">변경 내용 추적은 스파스 열 및 열 집합을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="c2da6-289">Change tracking supports sparse columns and column sets.</span></span> <span data-ttu-id="c2da6-290">테이블에서 열 집합이 업데이트되면 변경 내용 추적이 이를 전체 행에 대한 업데이트로 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="c2da6-290">When a column set is updated in a table, change tracking treats this as an update to the whole row.</span></span> <span data-ttu-id="c2da6-291">열 집합 업데이트 작업을 통해 업데이트되는 정확한 스파스 열 집합을 알 수 있는 자세한 변경 내용 추적은 제공되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c2da6-291">No detailed change tracking is provided to obtain the exact set of sparse columns that are updated through the column set update operation.</span></span> <span data-ttu-id="c2da6-292">스파스 열이 DML 문을 통해 명시적으로 업데이트되는 경우에는 해당 열에 대한 변경 내용 추적이 일반적으로 작동하여 변경된 정확한 열 집합을 식별할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2da6-292">If the sparse columns are updated explicitly through a DML statement, change tracking on them will work ordinarily and can identify the exact set of changed columns.</span></span>  
  
-   <span data-ttu-id="c2da6-293">변경 데이터 캡처</span><span class="sxs-lookup"><span data-stu-id="c2da6-293">Change data capture</span></span>  
  
     <span data-ttu-id="c2da6-294">변경 데이터 캡처는 스파스 열을 지원하지만 열 집합은 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c2da6-294">Change data capture supports sparse columns, but it does not support column sets.</span></span>  
  
-   <span data-ttu-id="c2da6-295">열의 스파스 속성은 테이블을 복사할 때 보존되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c2da6-295">The sparse property of a column is not preserved when the table is copied.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="c2da6-296">예</span><span class="sxs-lookup"><span data-stu-id="c2da6-296">Examples</span></span>  
 <span data-ttu-id="c2da6-297">이 예의 Document 테이블에는 `DocID` 및 `Title`열을 사용하는 공통 집합이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2da6-297">In this example, a document table contains a common set that has the columns `DocID` and `Title`.</span></span> <span data-ttu-id="c2da6-298">Production 그룹은 모든 생산 문서에 대한 `ProductionSpecification` 및 `ProductionLocation` 열을 원하며,</span><span class="sxs-lookup"><span data-stu-id="c2da6-298">The Production group wants a `ProductionSpecification` and `ProductionLocation` column for all production documents.</span></span> <span data-ttu-id="c2da6-299">Marketing 그룹은 마케팅 문서에 대한 `MarketingSurveyGroup` 열을 원합니다.</span><span class="sxs-lookup"><span data-stu-id="c2da6-299">The Marketing group wants a `MarketingSurveyGroup` column for marketing documents.</span></span> <span data-ttu-id="c2da6-300">이 예의 코드에서는 스파스 열을 사용하는 테이블을 만들고, 테이블에 두 개의 행을 삽입한 다음 테이블에서 데이터를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c2da6-300">The code in this example creates a table that uses sparse columns, inserts two rows into the table, and then selects data from the table.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c2da6-301">이 테이블에는 테이블을 보다 잘 표시하고 읽을 수 있도록 열이 5개만 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2da6-301">This table has only five columns to make it easier to display and read.</span></span> <span data-ttu-id="c2da6-302">ANSI_NULL_DFLT_ON 옵션이 설정된 경우 스파스 열을 Null 허용으로 선언하는 작업은 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="c2da6-302">Declaring the sparse columns to be nullable is optional if the ANSI_NULL_DFLT_ON option is set.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
  
CREATE TABLE DocumentStore  
    (DocID int PRIMARY KEY,  
     Title varchar(200) NOT NULL,  
     ProductionSpecification varchar(20) SPARSE NULL,  
     ProductionLocation smallint SPARSE NULL,  
     MarketingSurveyGroup varchar(20) SPARSE NULL ) ;  
GO  
  
INSERT DocumentStore(DocID, Title, ProductionSpecification, ProductionLocation)  
VALUES (1, 'Tire Spec 1', 'AXZZ217', 27);  
GO  
  
INSERT DocumentStore(DocID, Title, MarketingSurveyGroup)  
VALUES (2, 'Survey 2142', 'Men 25 - 35');  
GO  
```  
  
 <span data-ttu-id="c2da6-303">테이블에서 모든 열을 선택하려면 일반 쿼리 집합을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="c2da6-303">To select all the columns from the table returns an ordinary result set.</span></span>  
  
```  
SELECT * FROM DocumentStore ;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `DocID  Title        ProductionSpecification  ProductionLocation  MarketingSurveyGroup`  
  
 `1      Tire Spec 1  AXZZ217                  27                  NULL`  
  
 `2      Survey 2142  NULL                     NULL                Men 25-35`  
  
 <span data-ttu-id="c2da6-304">Production 부서는 마케팅 데이터에 관심이 없으므로 다음 쿼리에서처럼 관심 있는 열만 반환하는 열 목록을 사용하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2da6-304">Because the Production department is not interested in the marketing data, they want to use a column list that returns only columns of interest, as shown in the following query.</span></span>  
  
```  
SELECT DocID, Title, ProductionSpecification, ProductionLocation   
FROM DocumentStore   
WHERE ProductionSpecification IS NOT NULL ;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `DocID  Title        ProductionSpecification  ProductionLocation`  
  
 `1      Tire Spec 1  AXZZ217                  27`  
  
## <a name="see-also"></a><span data-ttu-id="c2da6-305">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c2da6-305">See Also</span></span>  
 <span data-ttu-id="c2da6-306">[열 집합 사용](../tables/use-column-sets.md) </span><span class="sxs-lookup"><span data-stu-id="c2da6-306">[Use Column Sets](../tables/use-column-sets.md) </span></span>  
 <span data-ttu-id="c2da6-307">[CREATE TABLE&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c2da6-307">[CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql) </span></span>  
 <span data-ttu-id="c2da6-308">[ALTER TABLE&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c2da6-308">[ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql) </span></span>  
 [<span data-ttu-id="c2da6-309">sys.columns&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="c2da6-309">sys.columns &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-columns-transact-sql)  
  
  
