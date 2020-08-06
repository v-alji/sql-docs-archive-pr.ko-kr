---
title: 시간 기반 행 필터에 대한 모범 사례 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- best practices
ms.assetid: 773c5c62-fd44-44ab-9c6b-4257dbf8ffdb
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ccaafe71d4137fd4b31eec412c1e35595861bdd0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638712"
---
# <a name="best-practices-for-time-based-row-filters"></a><span data-ttu-id="8a9f3-102">시간 기반 행 필터에 대한 최상의 구현 방법</span><span class="sxs-lookup"><span data-stu-id="8a9f3-102">Best Practices for Time-Based Row Filters</span></span>
  <span data-ttu-id="8a9f3-103">애플리케이션 사용자가 테이블의 시간 기반 데이터 하위 집합을 필요로 하는 경우가 종종 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8a9f3-103">Users of applications often require a time-based subset of data from a table.</span></span> <span data-ttu-id="8a9f3-104">예를 들어 영업 사원이 지난 주의 주문 데이터를 필요로 하거나, 행사 계획자가 다음 주의 행사 데이터를 필요로 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8a9f3-104">For instance, a salesperson might require data for orders in the last week, or an event planner might require data for events in the upcoming week.</span></span> <span data-ttu-id="8a9f3-105">대부분의 경우 애플리케이션에서는 `GETDATE()` 함수가 들어 있는 쿼리를 사용하여 이 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="8a9f3-105">In many cases, applications use queries containing the `GETDATE()` function to accomplish this.</span></span> <span data-ttu-id="8a9f3-106">예를 들어 다음과 같은 행 필터 문을 사용한다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="8a9f3-106">Consider the following row filter statement:</span></span>  
  
```  
WHERE SalesPersonID = CONVERT(INT,HOST_NAME()) AND OrderDate >= (GETDATE()-6)  
```  
  
 <span data-ttu-id="8a9f3-107">이 유형의 필터를 사용하면 일반적으로 병합 에이전트가 실행될 때 항상 두 가지 작업이 실행됩니다. 즉, 이 필터를 만족하는 행은 구독자에 복제되고 이 필터를 더 이상 만족하지 않는 행은 구독자에서 정리됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a9f3-107">With a filter of this type, it is usually assumed that two things always occur when the Merge Agent runs: rows that satisfy this filter are replicated to Subscribers; and rows that no longer satisfy this filter are cleaned up at Subscribers.</span></span> <span data-ttu-id="8a9f3-108">로 필터링 하는 방법에 대 한 자세한 내용은 `HOST_NAME()` [매개 변수가 있는 행 필터](parameterized-filters-parameterized-row-filters.md)를 참조 하세요. 그러나 병합 복제는 데이터에 대 한 행 필터를 정의 하는 방법에 관계 없이 마지막 동기화 이후 변경 된 데이터만 복제 하 고 정리 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a9f3-108">(For more information about filtering with `HOST_NAME()`, see [Parameterized Row Filters](parameterized-filters-parameterized-row-filters.md).) However, merge replication only replicates and cleans up data that has changed since the last synchronization, regardless of how you define a row filter for that data.</span></span>  
  
 <span data-ttu-id="8a9f3-109">행을 처리하는 병합 복제의 경우 행에 있는 데이터는 행 필터를 만족하고 마지막 동기화 이후에 변경된 데이터여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a9f3-109">For merge replication to process a row, the data in the row must satisfy the row filter, and it must have changed since the last synchronization.</span></span> <span data-ttu-id="8a9f3-110">**SalesOrderHeader** 테이블의 경우 행이 삽입될 때 **OrderDate** 가 입력됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a9f3-110">In the case of the **SalesOrderHeader** table, **OrderDate** is entered when a row is inserted.</span></span> <span data-ttu-id="8a9f3-111">행 삽입은 데이터 변경에 해당하므로 해당 행은 구독자에 예상대로 복제됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a9f3-111">Rows are replicated to the Subscriber as expected because the insert is a data change.</span></span> <span data-ttu-id="8a9f3-112">그러나 구독자에 필터를 더 이상 만족하지 않는 행(예: 7일 이상 경과된 주문)이 있는 경우 해당 행은 다른 이유로 업데이트되지 않았으면 구독자에서 제거되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8a9f3-112">However, if there are rows at the Subscriber that no longer satisfy the filter (they are for orders older than seven days), they are not removed from the Subscriber unless they were updated for some other reason.</span></span>  
  
 <span data-ttu-id="8a9f3-113">행사 계획자의 경우 이 유형의 필터링을 사용하여 원하는 항목을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8a9f3-113">The case of the event planner further highlights the issue with this type of filtering.</span></span> <span data-ttu-id="8a9f3-114">예를 들어 **Events** 테이블에 대해 다음과 같은 필터를 사용한다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="8a9f3-114">Consider the following filter for an **Events** table:</span></span>  
  
```  
WHERE EventCoordID = CONVERT(INT,HOST_NAME()) AND EventDate <= (GETDATE()+6)  
```  
  
 <span data-ttu-id="8a9f3-115">행사가 포함되는 테이블의 경우 행사 날짜 전에 행사를 삽입할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8a9f3-115">For a table that contains events, inserts might be made well ahead of the event date.</span></span> <span data-ttu-id="8a9f3-116">다음 주 행사를 한 달 전에 삽입하고 해당 행을 업데이트하지 않았으면 해당 행은 행 필터를 만족하더라도 구독자에 복제되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8a9f3-116">If the insert for an event in the coming week was made a month ago and the row was not updated for another reason, the row is not replicated to the Subscriber even if it satisfies the row filter.</span></span>  
  
 <span data-ttu-id="8a9f3-117">또한 병합 복제에서 필터가 평가되는 시기는 다음과 같이 게시가 구성된 방식에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="8a9f3-117">In addition, depending on how the publication is configured, merge replication evaluates filters at different times:</span></span>  
  
-   <span data-ttu-id="8a9f3-118">게시에서 사전 계산 파티션(기본값)을 사용하면 행을 삽입하거나 업데이트할 때 필터가 평가됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a9f3-118">If a publication uses precomputed partitions (the default), filters are evaluated when a row is inserted or updated.</span></span>  
  
-   <span data-ttu-id="8a9f3-119">게시에서 사전 계산 파티션을 사용하지 않으면 병합 에이전트가 실행할 때 필터가 평가됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a9f3-119">If the publication does not use precomputed partitions, filters are evaluated when the Merge Agent runs.</span></span>  
  
 <span data-ttu-id="8a9f3-120">사전 계산 파티션에 대한 자세한 내용은 [사전 계산 파티션으로 매개 변수가 있는 필터 성능 최적화](parameterized-filters-optimize-for-precomputed-partitions.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8a9f3-120">For more information about precomputed partitions, see [Optimize Parameterized Filter Performance with Precomputed Partitions](parameterized-filters-optimize-for-precomputed-partitions.md).</span></span> <span data-ttu-id="8a9f3-121">필터가 평가되는 시기는 필터를 만족하는 데이터에 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8a9f3-121">The time at which the filter is evaluated affects what data satisfies the filter.</span></span> <span data-ttu-id="8a9f3-122">예를 들어 게시에서 사전 계산 파티션을 사용하는 경우 데이터를 2일마다 동기화하면 영업 사원의 데이터 하위 집합에는 예상보다 최대 2일이 더 오래된 행이 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8a9f3-122">For example, if a publication uses precomputed partitions, and you synchronize data every two days, the subset of data for the salesperson could include rows up to two days older than expected.</span></span>  
  
## <a name="recommendations-for-using-time-based-row-filters"></a><span data-ttu-id="8a9f3-123">시간 기반 행 필터 사용에 대한 권장 사항</span><span class="sxs-lookup"><span data-stu-id="8a9f3-123">Recommendations for Using Time-Based Row Filters</span></span>  
 <span data-ttu-id="8a9f3-124">시간을 기반으로 필터링하기 위한 강력하고 간단한 방법은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="8a9f3-124">The following method provides a robust and straightforward approach to filtering based on time:</span></span>  
  
-   <span data-ttu-id="8a9f3-125">`bit` 데이터 형식의 테이블에 열을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="8a9f3-125">Add a column to the table of data type `bit`.</span></span> <span data-ttu-id="8a9f3-126">이 열은 행이 복제되는지 여부를 나타내는 데 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="8a9f3-126">This column is used to indicate whether a row should be replicated.</span></span>  
  
-   <span data-ttu-id="8a9f3-127">시간 기반 열 이외의 새 열을 참조하는 행 필터를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="8a9f3-127">Use a row filter that references the new column rather than a time-based column.</span></span>  
  
-   <span data-ttu-id="8a9f3-128">병합 에이전트의 예약된 실행 시간 전에 열을 업데이트하는 SQL Server 에이전트 작업(또는 다른 메커니즘을 통해 예약된 작업)을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8a9f3-128">Create a SQL Server Agent job (or a job scheduled through another mechanism) that updates the column before the Merge Agent is scheduled to run.</span></span>  
  
 <span data-ttu-id="8a9f3-129">이 방법을 사용하면 `GETDATE()`나 다른 시간 기반 메서드를 사용할 때의 문제를 해결할 수 있으며 파티션에 대해 필터가 평가되는 시기를 지정하지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a9f3-129">This approach addresses the shortcomings of using `GETDATE()` or another time-based method and avoids the problem of having to determine when filters are evaluated for partitions.</span></span> <span data-ttu-id="8a9f3-130">예를 들어 다음과 같은 **Events** 테이블이 있다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="8a9f3-130">Consider the following example of an **Events** table:</span></span>  
  
|<span data-ttu-id="8a9f3-131">**EventID**</span><span class="sxs-lookup"><span data-stu-id="8a9f3-131">**EventID**</span></span>|<span data-ttu-id="8a9f3-132">**EventName**</span><span class="sxs-lookup"><span data-stu-id="8a9f3-132">**EventName**</span></span>|<span data-ttu-id="8a9f3-133">**EventCoordID**</span><span class="sxs-lookup"><span data-stu-id="8a9f3-133">**EventCoordID**</span></span>|<span data-ttu-id="8a9f3-134">**EventDate**</span><span class="sxs-lookup"><span data-stu-id="8a9f3-134">**EventDate**</span></span>|<span data-ttu-id="8a9f3-135">**복제**</span><span class="sxs-lookup"><span data-stu-id="8a9f3-135">**Replicate**</span></span>|  
|-----------------|-------------------|----------------------|-------------------|-------------------|  
|<span data-ttu-id="8a9f3-136">1</span><span class="sxs-lookup"><span data-stu-id="8a9f3-136">1</span></span>|<span data-ttu-id="8a9f3-137">Reception</span><span class="sxs-lookup"><span data-stu-id="8a9f3-137">Reception</span></span>|<span data-ttu-id="8a9f3-138">112</span><span class="sxs-lookup"><span data-stu-id="8a9f3-138">112</span></span>|<span data-ttu-id="8a9f3-139">2006-10-04</span><span class="sxs-lookup"><span data-stu-id="8a9f3-139">2006-10-04</span></span>|<span data-ttu-id="8a9f3-140">1</span><span class="sxs-lookup"><span data-stu-id="8a9f3-140">1</span></span>|  
|<span data-ttu-id="8a9f3-141">2</span><span class="sxs-lookup"><span data-stu-id="8a9f3-141">2</span></span>|<span data-ttu-id="8a9f3-142">저녁</span><span class="sxs-lookup"><span data-stu-id="8a9f3-142">Dinner</span></span>|<span data-ttu-id="8a9f3-143">112</span><span class="sxs-lookup"><span data-stu-id="8a9f3-143">112</span></span>|<span data-ttu-id="8a9f3-144">2006-10-10</span><span class="sxs-lookup"><span data-stu-id="8a9f3-144">2006-10-10</span></span>|<span data-ttu-id="8a9f3-145">0</span><span class="sxs-lookup"><span data-stu-id="8a9f3-145">0</span></span>|  
|<span data-ttu-id="8a9f3-146">3</span><span class="sxs-lookup"><span data-stu-id="8a9f3-146">3</span></span>|<span data-ttu-id="8a9f3-147">Party</span><span class="sxs-lookup"><span data-stu-id="8a9f3-147">Party</span></span>|<span data-ttu-id="8a9f3-148">112</span><span class="sxs-lookup"><span data-stu-id="8a9f3-148">112</span></span>|<span data-ttu-id="8a9f3-149">2006-10-11</span><span class="sxs-lookup"><span data-stu-id="8a9f3-149">2006-10-11</span></span>|<span data-ttu-id="8a9f3-150">0</span><span class="sxs-lookup"><span data-stu-id="8a9f3-150">0</span></span>|  
|<span data-ttu-id="8a9f3-151">4</span><span class="sxs-lookup"><span data-stu-id="8a9f3-151">4</span></span>|<span data-ttu-id="8a9f3-152">Wedding</span><span class="sxs-lookup"><span data-stu-id="8a9f3-152">Wedding</span></span>|<span data-ttu-id="8a9f3-153">112</span><span class="sxs-lookup"><span data-stu-id="8a9f3-153">112</span></span>|<span data-ttu-id="8a9f3-154">2006-10-12</span><span class="sxs-lookup"><span data-stu-id="8a9f3-154">2006-10-12</span></span>|<span data-ttu-id="8a9f3-155">0</span><span class="sxs-lookup"><span data-stu-id="8a9f3-155">0</span></span>|  
  
 <span data-ttu-id="8a9f3-156">이 테이블에 다음과 같은 행 필터를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8a9f3-156">The row filter for this table would then look like this:</span></span>  
  
```  
WHERE EventCoordID = CONVERT(INT,HOST_NAME()) AND Replicate = 1  
```  
  
 <span data-ttu-id="8a9f3-157">각 병합 에이전트가 실행되기 전에 SQL Server 에이전트 작업은 다음과 유사한 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 문을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8a9f3-157">The SQL Server Agent job could execute [!INCLUDE[tsql](../../../includes/tsql-md.md)] statements similar to the following before each Merge Agent run:</span></span>  
  
```  
UPDATE Events SET Replicate = 0 WHERE Replicate = 1  
GO  
UPDATE Events SET Replicate = 1 WHERE EventDate <= GETDATE()+6  
GO  
```  
  
 <span data-ttu-id="8a9f3-158">첫째 줄은 **Replicate** 열을 **0**으로 다시 설정하고 둘째 줄은 다음 7일 안에 개최되는 행사에 대해 이 열을 **1** 로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8a9f3-158">The first line resets the **Replicate** column to **0**, and the second line sets the column to **1** for events that occur in the next seven days.</span></span> <span data-ttu-id="8a9f3-159">2006년 10월 7일에 이 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 문을 실행하면 해당 테이블은 다음과 같이 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a9f3-159">If this [!INCLUDE[tsql](../../../includes/tsql-md.md)] statement runs on 10/07/2006, the table is updated to:</span></span>  
  
|<span data-ttu-id="8a9f3-160">**EventID**</span><span class="sxs-lookup"><span data-stu-id="8a9f3-160">**EventID**</span></span>|<span data-ttu-id="8a9f3-161">**EventName**</span><span class="sxs-lookup"><span data-stu-id="8a9f3-161">**EventName**</span></span>|<span data-ttu-id="8a9f3-162">**EventCoordID**</span><span class="sxs-lookup"><span data-stu-id="8a9f3-162">**EventCoordID**</span></span>|<span data-ttu-id="8a9f3-163">**EventDate**</span><span class="sxs-lookup"><span data-stu-id="8a9f3-163">**EventDate**</span></span>|<span data-ttu-id="8a9f3-164">**복제**</span><span class="sxs-lookup"><span data-stu-id="8a9f3-164">**Replicate**</span></span>|  
|-----------------|-------------------|----------------------|-------------------|-------------------|  
|<span data-ttu-id="8a9f3-165">1</span><span class="sxs-lookup"><span data-stu-id="8a9f3-165">1</span></span>|<span data-ttu-id="8a9f3-166">Reception</span><span class="sxs-lookup"><span data-stu-id="8a9f3-166">Reception</span></span>|<span data-ttu-id="8a9f3-167">112</span><span class="sxs-lookup"><span data-stu-id="8a9f3-167">112</span></span>|<span data-ttu-id="8a9f3-168">2006-10-04</span><span class="sxs-lookup"><span data-stu-id="8a9f3-168">2006-10-04</span></span>|<span data-ttu-id="8a9f3-169">0</span><span class="sxs-lookup"><span data-stu-id="8a9f3-169">0</span></span>|  
|<span data-ttu-id="8a9f3-170">2</span><span class="sxs-lookup"><span data-stu-id="8a9f3-170">2</span></span>|<span data-ttu-id="8a9f3-171">저녁</span><span class="sxs-lookup"><span data-stu-id="8a9f3-171">Dinner</span></span>|<span data-ttu-id="8a9f3-172">112</span><span class="sxs-lookup"><span data-stu-id="8a9f3-172">112</span></span>|<span data-ttu-id="8a9f3-173">2006-10-10</span><span class="sxs-lookup"><span data-stu-id="8a9f3-173">2006-10-10</span></span>|<span data-ttu-id="8a9f3-174">1</span><span class="sxs-lookup"><span data-stu-id="8a9f3-174">1</span></span>|  
|<span data-ttu-id="8a9f3-175">3</span><span class="sxs-lookup"><span data-stu-id="8a9f3-175">3</span></span>|<span data-ttu-id="8a9f3-176">Party</span><span class="sxs-lookup"><span data-stu-id="8a9f3-176">Party</span></span>|<span data-ttu-id="8a9f3-177">112</span><span class="sxs-lookup"><span data-stu-id="8a9f3-177">112</span></span>|<span data-ttu-id="8a9f3-178">2006-10-11</span><span class="sxs-lookup"><span data-stu-id="8a9f3-178">2006-10-11</span></span>|<span data-ttu-id="8a9f3-179">1</span><span class="sxs-lookup"><span data-stu-id="8a9f3-179">1</span></span>|  
|<span data-ttu-id="8a9f3-180">4</span><span class="sxs-lookup"><span data-stu-id="8a9f3-180">4</span></span>|<span data-ttu-id="8a9f3-181">Wedding</span><span class="sxs-lookup"><span data-stu-id="8a9f3-181">Wedding</span></span>|<span data-ttu-id="8a9f3-182">112</span><span class="sxs-lookup"><span data-stu-id="8a9f3-182">112</span></span>|<span data-ttu-id="8a9f3-183">2006-10-12</span><span class="sxs-lookup"><span data-stu-id="8a9f3-183">2006-10-12</span></span>|<span data-ttu-id="8a9f3-184">1</span><span class="sxs-lookup"><span data-stu-id="8a9f3-184">1</span></span>|  
  
 <span data-ttu-id="8a9f3-185">이제 다음 주의 행사가 복제할 행사로 플래그가 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a9f3-185">The events for the next week are now flagged as being ready to replicate.</span></span> <span data-ttu-id="8a9f3-186">다음에 행사 코디네이터 112가 사용하는 구독에 대해 병합 에이전트가 실행되면 행 2, 3 및 4는 구독자에 다운로드되고 행 1은 구독자에서 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a9f3-186">The next time the Merge Agent runs for the subscription that event coordinator 112 uses, rows 2, 3, and 4 will be downloaded to the Subscriber and row 1 will be removed from the Subscriber.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a9f3-187">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8a9f3-187">See Also</span></span>  
 <span data-ttu-id="8a9f3-188">[GETDATE&#40;Transact-SQL&#41;](/sql/t-sql/functions/getdate-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="8a9f3-188">[GETDATE &#40;Transact-SQL&#41;](/sql/t-sql/functions/getdate-transact-sql) </span></span>  
 <span data-ttu-id="8a9f3-189">[작업 구현](../../../ssms/agent/implement-jobs.md) </span><span class="sxs-lookup"><span data-stu-id="8a9f3-189">[Implement Jobs](../../../ssms/agent/implement-jobs.md) </span></span>  
 [<span data-ttu-id="8a9f3-190">매개 변수가 있는 행 필터</span><span class="sxs-lookup"><span data-stu-id="8a9f3-190">Parameterized Row Filters</span></span>](parameterized-filters-parameterized-row-filters.md)  
  
  
