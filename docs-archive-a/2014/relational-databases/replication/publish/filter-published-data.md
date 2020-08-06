---
title: 게시된 데이터 필터링 | Microsoft 문서
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- filters [SQL Server replication]
- filters [SQL Server replication], about filtering
- filtering [SQL Server replication]
- static row filters
- transactional replication, filtering published data
- replication [SQL Server], filtering published data
- filtering published data [SQL Server replication]
- snapshot replication [SQL Server], filtering published data
- column filters [SQL Server replication]
ms.assetid: 8a914947-72dc-4119-b631-b39c8070c71b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 525e90cecbc4cd6ee817b8fd07748abaf651b524
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647606"
---
# <a name="filter-published-data"></a><span data-ttu-id="d63fe-102">게시된 데이터 필터링</span><span class="sxs-lookup"><span data-stu-id="d63fe-102">Filter Published Data</span></span>
  <span data-ttu-id="d63fe-103">테이블 아티클을 필터링하여 게시할 데이터 파티션을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d63fe-103">Filtering table articles enables you to create partitions of data to be published.</span></span> <span data-ttu-id="d63fe-104">게시된 데이터를 필터링하여 다음 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d63fe-104">By filtering published data, you can:</span></span>  
  
-   <span data-ttu-id="d63fe-105">네트워크로 보내지는 데이터 양을 최소화합니다.</span><span class="sxs-lookup"><span data-stu-id="d63fe-105">Minimize the amount of data sent over the network.</span></span>  
  
-   <span data-ttu-id="d63fe-106">구독자에 필요한 스토리지 공간을 줄입니다.</span><span class="sxs-lookup"><span data-stu-id="d63fe-106">Reduce the amount of storage space required at the Subscriber.</span></span>  
  
-   <span data-ttu-id="d63fe-107">개별 구독자 요구 사항에 기초하여 게시 및 애플리케이션을 사용자 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d63fe-107">Customize publications and applications based on individual Subscriber requirements.</span></span>  
  
-   <span data-ttu-id="d63fe-108">서로 다른 구독자에 서로 다른 데이터 파티션을 보낼 수 있으므로 구독자가 데이터를 업데이트할 때 충돌을 방지하거나 충돌 횟수를 줄일 수 있습니다. 즉, 두 개의 구독자가 같은 데이터 값을 업데이트하지 않게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d63fe-108">Avoid or reduce conflicts if Subscribers are updating data, because different data partitions can be sent to different Subscribers (no two Subscribers will be updating the same data values).</span></span>  
  
-   <span data-ttu-id="d63fe-109">중요한 데이터를 전송하지 못하게 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d63fe-109">Avoid transmitting sensitive data.</span></span> <span data-ttu-id="d63fe-110">행 필터와 열 필터를 사용하여 구독자의 데이터 액세스를 제한할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d63fe-110">Row filters and column filters can be used to restrict a Subscriber's access to data.</span></span> <span data-ttu-id="d63fe-111">병합 복제에서 HOST_NAME()을 포함하는 매개 변수가 있는 필터를 사용할 경우 보안 고려 사항이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d63fe-111">For merge replication, there are security considerations if you use a parameterized filter that includes HOST_NAME().</span></span> <span data-ttu-id="d63fe-112">자세한 내용은 [Parameterized Row Filters](../merge/parameterized-filters-parameterized-row-filters.md)의 "HOST_NAME()으로 필터링" 섹션을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="d63fe-112">For more information, see the section "Filtering with HOST_NAME()" in [Parameterized Row Filters](../merge/parameterized-filters-parameterized-row-filters.md).</span></span>  
  
 <span data-ttu-id="d63fe-113">복제는 다음 4가지 형식의 필터를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="d63fe-113">Replication offers four types of filters:</span></span>  
  
-   <span data-ttu-id="d63fe-114">정적 행 필터 - 모든 복제 유형에 사용할 수 있음</span><span class="sxs-lookup"><span data-stu-id="d63fe-114">Static row filters, which are available with all types of replication.</span></span>  
  
     <span data-ttu-id="d63fe-115">정적 행 필터를 사용하여 게시할 행의 하위 집합을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d63fe-115">Using static row filters, you can choose a subset of rows to be published.</span></span> <span data-ttu-id="d63fe-116">필터링된 게시에 대한 모든 구독자는 필터링된 테이블 행의 동일한 하위 집합을 받습니다.</span><span class="sxs-lookup"><span data-stu-id="d63fe-116">All Subscribers to a filtered publication receive the same subset of rows for the filtered table.</span></span> <span data-ttu-id="d63fe-117">자세한 내용은 이 항목의 "정적 행 필터" 섹션을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="d63fe-117">For more information, see the section "Static Row Filters" in this topic.</span></span>  
  
-   <span data-ttu-id="d63fe-118">열 필터 - 모든 복제 유형에 사용할 수 있음</span><span class="sxs-lookup"><span data-stu-id="d63fe-118">Column filters, which are available with all types of replication.</span></span>  
  
     <span data-ttu-id="d63fe-119">열 필터를 사용하여 게시할 열의 하위 집합을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d63fe-119">Using column filters, you can choose a subset of columns to be published.</span></span> <span data-ttu-id="d63fe-120">자세한 내용은 이 항목의 "열 필터" 섹션을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="d63fe-120">For more information, see the section "Column Filters" in this topic.</span></span>  
  
-   <span data-ttu-id="d63fe-121">매개 변수가 있는 행 필터 - 병합 복제에만 사용할 수 있음</span><span class="sxs-lookup"><span data-stu-id="d63fe-121">Parameterized row filters, which are available only with merge replication.</span></span>  
  
     <span data-ttu-id="d63fe-122">매개 변수가 있는 행 필터를 사용하여 게시할 행의 하위 집합을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d63fe-122">Using parameterized row filters, you can choose a subset of rows to be published.</span></span> <span data-ttu-id="d63fe-123">모든 구독자에게 행의 동일한 하위 집합을 보내는 정적 필터와 달리 매개 변수가 있는 행 필터는 구독자가 제공한 데이터 값을 사용하여 구독자에게 행의 다른 하위 집합을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="d63fe-123">Unlike static filters that send the same subset of rows to every Subscriber, parameterized row filters use a data value supplied by the Subscriber to send Subscribers different subsets of rows.</span></span> <span data-ttu-id="d63fe-124">자세한 내용은 [매개 변수가 있는 행 필터](../merge/parameterized-filters-parameterized-row-filters.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="d63fe-124">For more information, see [Parameterized Row Filters](../merge/parameterized-filters-parameterized-row-filters.md).</span></span>  
  
-   <span data-ttu-id="d63fe-125">조인 필터 - 병합 복제에만 사용할 수 있음</span><span class="sxs-lookup"><span data-stu-id="d63fe-125">Join filters, which are available only with merge replication.</span></span>  
  
     <span data-ttu-id="d63fe-126">조인 필터를 사용하여 다른 게시된 테이블로 행 필터를 확장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d63fe-126">Using join filters, you can extend a row filter from one published table to another.</span></span> <span data-ttu-id="d63fe-127">자세한 내용은 [Join Filters](../merge/join-filters.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d63fe-127">For more information, see [Join Filters](../merge/join-filters.md).</span></span>  
  
## <a name="static-row-filters"></a><span data-ttu-id="d63fe-128">정적 행 필터</span><span class="sxs-lookup"><span data-stu-id="d63fe-128">Static Row Filters</span></span>  
 <span data-ttu-id="d63fe-129">다음 그림에서는 2행, 3행, 6행만 게시에 포함되도록 필터링된 게시된 테이블을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d63fe-129">The following illustration shows a published table that is filtered so that only rows 2, 3, and 6 are included in the publication.</span></span>  
  
 <span data-ttu-id="d63fe-130">![행 필터링](../media/repl-16.gif "행 필터링")</span><span class="sxs-lookup"><span data-stu-id="d63fe-130">![Row filtering](../media/repl-16.gif "Row filtering")</span></span>  
  
 <span data-ttu-id="d63fe-131">정적 행 필터는 WHERE 절을 사용하여 게시에 적합한 데이터를 선택합니다. WHERE 절의 마지막 부분은 사용자가 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d63fe-131">A static row filter uses a WHERE clause to select the appropriate data to be published; you specify the final part of the WHERE clause.</span></span> <span data-ttu-id="d63fe-132">**ProductLine** 열이 포함된 Adventure Works 예제 데이터베이스의 **Product 테이블**을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="d63fe-132">Consider the **Product Table** in the Adventure Works sample database, which contains the column **ProductLine**.</span></span> <span data-ttu-id="d63fe-133">산악 자전거 관련 제품에 대한 데이터가 있는 행만 게시하려면 `ProductLine = 'M'`을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d63fe-133">To publish only the rows with data on products related to mountain bikes, specify `ProductLine = 'M'`.</span></span>  
  
 <span data-ttu-id="d63fe-134">정적 행 필터를 사용하면 각 게시에 대해 단일 데이터 집합이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="d63fe-134">A static row filter results in a single set of data for each publication.</span></span> <span data-ttu-id="d63fe-135">위의 예에서는 모든 구독자가 산악 자전거 관련 제품에 대한 데이터가 있는 행만 받게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d63fe-135">In the previous example, all Subscribers would receive only the rows with data on products related to mountain bikes.</span></span> <span data-ttu-id="d63fe-136">일반 자전거 관련 제품에 대한 데이터가 있는 행만을 필요로 하는 다른 구독자가 있는 경우 다음을 수행하십시오.</span><span class="sxs-lookup"><span data-stu-id="d63fe-136">If you have another Subscriber that requires only the rows with data on products related to road bikes:</span></span>  
  
-   <span data-ttu-id="d63fe-137">스냅샷 또는 트랜잭션 복제를 사용하여 다른 게시를 만들고 두 게시에 해당 테이블을 포함시킵니다. 해당 게시에 있는 아티클에 대한 필터 절에는 `ProductLine = 'R')`을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d63fe-137">With snapshot or transactional replication, you can create another publication and include the table in both publications (in the filter clause for the article in that publication, specify `ProductLine = 'R')`.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d63fe-138">행을 복제해야 하는지 여부를 결정하도록 게시된 테이블에 대해 기록된 각 로그 행에 대해 아티클 필터 절이 평가되기 때문에 행 필터는 트랜잭션 게시에서 중요한 오버헤드를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d63fe-138">Row filters in transactional publications can add significant overhead because the article filter clause is evaluated for each log row written for a published table, to determine whether the row should be replicated.</span></span> <span data-ttu-id="d63fe-139">각 복제 노드가 전체 데이터 로드를 지원할 수 있고 데이터 집합의 크기가 전체적으로 작은 경우 트랜잭션 게시에 행 필터를 사용하지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d63fe-139">Row filters in transactional publications should be avoided if each replication node can support the full data load, and the overall data set is reasonably small.</span></span>  
  
-   <span data-ttu-id="d63fe-140">병합 복제의 경우 정적 행 필터가 있는 여러 게시를 만드는 대신 매개 변수가 있는 행 필터를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="d63fe-140">With merge replication, use parameterized row filters rather than creating multiple publications with static row filters.</span></span> <span data-ttu-id="d63fe-141">자세한 내용은 [매개 변수가 있는 행 필터](../merge/parameterized-filters-parameterized-row-filters.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="d63fe-141">For more information, see [Parameterized Row Filters](../merge/parameterized-filters-parameterized-row-filters.md).</span></span>  
  
 <span data-ttu-id="d63fe-142">정적 행 필터를 정의하거나 수정하려면 [Define and Modify a Static Row Filter](define-and-modify-a-static-row-filter.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="d63fe-142">To define or modify a static row filter, see [Define and Modify a Static Row Filter](define-and-modify-a-static-row-filter.md).</span></span>  
  
## <a name="column-filters"></a><span data-ttu-id="d63fe-143">열 필터</span><span class="sxs-lookup"><span data-stu-id="d63fe-143">Column Filters</span></span>  
 <span data-ttu-id="d63fe-144">다음 그림에서는 C 열을 필터링하여 제외하는 게시를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d63fe-144">The following illustration shows a publication that filters out column C.</span></span>  
  
 <span data-ttu-id="d63fe-145">![열 필터링](../media/repl-17.gif "열 필터링")</span><span class="sxs-lookup"><span data-stu-id="d63fe-145">![Column filtering](../media/repl-17.gif "Column filtering")</span></span>  
  
 <span data-ttu-id="d63fe-146">다음 그림처럼 행 필터링과 열 필터링을 함께 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d63fe-146">You can also use row and column filtering together, as illustrated here.</span></span>  
  
 <span data-ttu-id="d63fe-147">![행 및 열 필터링](../media/repl-18.gif "행 및 열 필터링")</span><span class="sxs-lookup"><span data-stu-id="d63fe-147">![Row and column filtering](../media/repl-18.gif "Row and column filtering")</span></span>  
  
 <span data-ttu-id="d63fe-148">게시가 생성된 다음에는 열 필터링을 사용하여 열을 기존 게시에서는 삭제하고 게시자에서는 테이블에 유지할 수 있고 게시에 기존 열을 포함시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d63fe-148">After a publication is created, you can use column filtering to drop a column from an existing publication, but retain the column in the table at the Publisher, and also to include an existing column in the publication.</span></span> <span data-ttu-id="d63fe-149">테이블에 새 열을 추가한 다음 이 열을 게시된 아티클에 추가하는 것과 같은 다른 변경에 대해서는 스키마 변경 복제를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="d63fe-149">For other changes, such as adding a new column to a table and then adding it to the published article, use schema change replication.</span></span> <span data-ttu-id="d63fe-150">자세한 내용은 [게시 데이터베이스의 스키마 변경](make-schema-changes-on-publication-databases.md) 항목의 "열 추가" 및 "열 삭제" 섹션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d63fe-150">For more information, see the "Adding Columns" and "Dropping Columns" sections in the topic [Make Schema Changes on Publication Databases](make-schema-changes-on-publication-databases.md).</span></span>  
  
 <span data-ttu-id="d63fe-151">다음 표에 나열된 특정 게시의 특정 열 유형은 필터링하여 제외시킬 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d63fe-151">The types of columns listed in the following table cannot be filtered out of certain types of publications.</span></span>  
  
|<span data-ttu-id="d63fe-152">열 유형</span><span class="sxs-lookup"><span data-stu-id="d63fe-152">Column type</span></span>|<span data-ttu-id="d63fe-153">게시 유형 및 옵션</span><span class="sxs-lookup"><span data-stu-id="d63fe-153">Type of publication and options</span></span>|  
|-----------------|-------------------------------------|  
|<span data-ttu-id="d63fe-154">기본 키 열</span><span class="sxs-lookup"><span data-stu-id="d63fe-154">Primary key column</span></span>|<span data-ttu-id="d63fe-155">기본 키 열은 트랜잭션 게시의 모든 테이블에 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="d63fe-155">Primary key columns are required for all tables in transactional publications.</span></span> <span data-ttu-id="d63fe-156">기본 키는 병합 게시의 테이블에 필요하지 않지만 기본 키 열이 있는 경우 필터링할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d63fe-156">Primary keys are not required for tables in merge publications, but if a primary key column is present, it cannot be filtered.</span></span>|  
|<span data-ttu-id="d63fe-157">외래 키 열</span><span class="sxs-lookup"><span data-stu-id="d63fe-157">Foreign key column</span></span>|<span data-ttu-id="d63fe-158">새 게시 마법사를 사용하여 생성된 모든 게시입니다.</span><span class="sxs-lookup"><span data-stu-id="d63fe-158">All publications created using the New Publication wizard.</span></span> <span data-ttu-id="d63fe-159">Transact-SQL 저장 프로시저를 사용하여 외래 키 열을 필터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d63fe-159">You can filter foreign key columns using Transact-SQL stored procedures.</span></span> <span data-ttu-id="d63fe-160">자세한 내용은 [Define and Modify a Column Filter](define-and-modify-a-column-filter.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="d63fe-160">For more information, [Define and Modify a Column Filter](define-and-modify-a-column-filter.md).</span></span>|  
|<span data-ttu-id="d63fe-161">**rowguid** 열</span><span class="sxs-lookup"><span data-stu-id="d63fe-161">The **rowguid** column</span></span>|<span data-ttu-id="d63fe-162">병합 게시<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="d63fe-162">Merge publications<sup>1</sup></span></span>|  
|<span data-ttu-id="d63fe-163">**msrepl_tran_version** 열</span><span class="sxs-lookup"><span data-stu-id="d63fe-163">The **msrepl_tran_version** column</span></span>|<span data-ttu-id="d63fe-164">업데이트할 수 있는 구독을 허용하는 스냅샷 게시나 트랜잭션 게시</span><span class="sxs-lookup"><span data-stu-id="d63fe-164">Snapshot or transactional publications that allow updatable subscriptions</span></span>|  
|<span data-ttu-id="d63fe-165">NULL을 허용하지 않고 기본값 또는 IDENTITY 속성 설정이 없는 열</span><span class="sxs-lookup"><span data-stu-id="d63fe-165">Columns that do not allow NULL and do not have default values or the IDENTITY property set.</span></span>|<span data-ttu-id="d63fe-166">업데이트할 수 있는 구독을 허용하는 스냅샷 게시나 트랜잭션 게시</span><span class="sxs-lookup"><span data-stu-id="d63fe-166">Snapshot or transactional publications that allow updatable subscriptions</span></span>|  
|<span data-ttu-id="d63fe-167">UNIQUE 제약 조건 또는 인덱스가 있는 열</span><span class="sxs-lookup"><span data-stu-id="d63fe-167">Columns with unique constraints or indexes</span></span>|<span data-ttu-id="d63fe-168">업데이트할 수 있는 구독을 허용하는 스냅샷 게시나 트랜잭션 게시</span><span class="sxs-lookup"><span data-stu-id="d63fe-168">Snapshot or transactional publications that allow updatable subscriptions</span></span>|  
|<span data-ttu-id="d63fe-169">SQL Server 7.0 병합 게시의 모든 열</span><span class="sxs-lookup"><span data-stu-id="d63fe-169">All columns in a SQL Server 7.0 merge publication</span></span>|<span data-ttu-id="d63fe-170">SQL Server 7.0 병합 게시에서는 열을 필터링할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d63fe-170">Columns cannot be filtered in SQL Server 7.0 merge publications.</span></span>|  
|<span data-ttu-id="d63fe-171">타임스탬프</span><span class="sxs-lookup"><span data-stu-id="d63fe-171">Timestamp</span></span>|<span data-ttu-id="d63fe-172">업데이트할 수 있는 구독을 허용하는 SQL Server 7.0 스냅샷 또는 트랜잭션 게시</span><span class="sxs-lookup"><span data-stu-id="d63fe-172">SQL Server 7.0 snapshot or transactional publications that allow updatable subscriptions</span></span>|  
  
 <span data-ttu-id="d63fe-173"><sup>1</sup> 병합 게시에 테이블을 게시 하는 경우 해당 테이블에 이미 속성이 설정 된 데이터 형식의 열 `uniqueidentifier` 이 있는 경우 `ROWGUIDCOL` 복제는 **rowguid**라는 추가 열을 만드는 대신이 열을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d63fe-173"><sup>1</sup> If you are publishing a table in a merge publication and that table already contains a column of data type `uniqueidentifier` with the `ROWGUIDCOL` property set, replication can use this column instead of creating an additional column named **rowguid**.</span></span> <span data-ttu-id="d63fe-174">이 경우 기존 열을 게시해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d63fe-174">In this case, the existing column must be published.</span></span>  
  
 <span data-ttu-id="d63fe-175">열 필터를 정의하거나 수정하려면 [Define and Modify a Column Filter](define-and-modify-a-column-filter.md)의 "HOST_NAME()으로 필터링" 섹션을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="d63fe-175">To define or modify a column filter, see [Define and Modify a Column Filter](define-and-modify-a-column-filter.md).</span></span>  
  
## <a name="filtering-considerations"></a><span data-ttu-id="d63fe-176">필터링 고려 사항</span><span class="sxs-lookup"><span data-stu-id="d63fe-176">Filtering Considerations</span></span>  
 <span data-ttu-id="d63fe-177">데이터 필터링 시 다음 사항을 고려하십시오.</span><span class="sxs-lookup"><span data-stu-id="d63fe-177">Keep the following considerations in mind when filtering data:</span></span>  
  
-   <span data-ttu-id="d63fe-178">행 필터에 참조되는 모든 열은 게시에 포함되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d63fe-178">All columns referenced in row filters must be included in the publication.</span></span> <span data-ttu-id="d63fe-179">즉, 열 필터를 사용하여 행 필터에 사용되는 열을 제외할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d63fe-179">In other words, you cannot use a column filter to exclude a column that is used in a row filter.</span></span>  
  
-   <span data-ttu-id="d63fe-180">구독이 초기화된 후 필터를 추가하거나 변경한 경우에는 구독을 다시 초기화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d63fe-180">If a filter is added or changed after subscriptions have been initialized, the subscriptions must be reinitialized.</span></span>  
  
-   <span data-ttu-id="d63fe-181">필터에 사용되는 열에 허용되는 최대 바이트 수는 병합 게시의 아티클의 경우에는1024, 트랜잭션 게시의 아티클의 경우에는 8000입니다.</span><span class="sxs-lookup"><span data-stu-id="d63fe-181">The maximum number of bytes allowed for a column used in a filter is 1024 for an article in a merge publication and 8000 for an article in a transactional publication.</span></span>  
  
-   <span data-ttu-id="d63fe-182">다음과 같은 데이터 형식이 있는 열은 행 필터나 조인 필터에 참조될 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d63fe-182">Columns with the following data types cannot be referenced in row filters or join filters:</span></span>  
  
    -   `varchar(max) and nvarchar(max)`  
  
    -   `varbinary(max)`  
  
    -   `text and ntext`  
  
    -   `image`  
  
    -   `XML`  
  
    -   `UDT`  
  
-   <span data-ttu-id="d63fe-183">트랜잭션 복제를 사용하면 인덱싱된 뷰를 뷰나 테이블로 복제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d63fe-183">Transactional replication allows you to replicate an indexed view as a view or as a table.</span></span> <span data-ttu-id="d63fe-184">뷰를 테이블로 복제하면 테이블의 열을 필터링할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d63fe-184">If you replicate the view as a table, you cannot filter columns from the table.</span></span>  
  
 <span data-ttu-id="d63fe-185">행 필터는 데이터베이스에서 작동하도록 설계되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="d63fe-185">Row filters are not designed to work across databases.</span></span> [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]<span data-ttu-id="d63fe-186">는 `sp_replcmds` 실행(필터 실행 대상)을 의도적으로 데이터베이스 소유자(`dbo`)로 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="d63fe-186">intentionally restricts the execution of `sp_replcmds` (which filters execute under) to the database owner (`dbo`).</span></span> <span data-ttu-id="d63fe-187">`dbo`에는 데이터베이스 간 권한이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d63fe-187">The `dbo` does not have cross database privileges.</span></span> <span data-ttu-id="d63fe-188">`sp_replcmds` 논리는 [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]에 CDC(변경 데이터 캡처)를 추가하여 변경 내용 추적 테이블을 사용자가 반환하고 쿼리할 수 있는 정보로 채웁니다.</span><span class="sxs-lookup"><span data-stu-id="d63fe-188">With the addition of CDC (Change Data Capture) in [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] the `sp_replcmds` logic populates the change tracking tables with information that the user can return to and query.</span></span> <span data-ttu-id="d63fe-189">보안상의 이유로는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 악성이 실행 경로를 활용할 수 없도록이 논리의 실행을 제한 합니다 `dbo` .</span><span class="sxs-lookup"><span data-stu-id="d63fe-189">For security reasons, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] restricts the execution of this logic so that a malicious `dbo` can't highjack this execution path.</span></span> <span data-ttu-id="d63fe-190">예를 들어, 악성 `dbo`는 `sp_replcmds`를 호출하는 사용자의 컨텍스트에서 실행될 수 있는 트리거를 CDC 테이블에 추가할 수 있으며, 이 경우 logreader 에이전트입니다.</span><span class="sxs-lookup"><span data-stu-id="d63fe-190">For example, a malicious `dbo` could add triggers on CDC tables which would then get executed under the context of the user calling `sp_replcmds`, in this case the logreader agent.</span></span>  <span data-ttu-id="d63fe-191">에이전트가 실행 중인 계정의 권한이 더 높은 경우 악성 `dbo`가 자신의 권한을 에스컬레이션할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d63fe-191">If the account the agent is running under has higher privilege the malicious `dbo` could escalate his privileges.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d63fe-192">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d63fe-192">See Also</span></span>  
 [<span data-ttu-id="d63fe-193">데이터 및 데이터베이스 개체 게시</span><span class="sxs-lookup"><span data-stu-id="d63fe-193">Publish Data and Database Objects</span></span>](publish-data-and-database-objects.md)  
  
  
