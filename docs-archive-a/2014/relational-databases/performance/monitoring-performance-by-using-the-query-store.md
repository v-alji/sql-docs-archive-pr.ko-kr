---
title: 쿼리 저장소를 사용하여 성능 모니터링 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
ms.assetid: e06344a4-22a5-4c67-b6c6-a7060deb5de6
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: e5d74b9c4def9c0314569a8d0bd87939cdcb11b2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660506"
---
# <a name="monitoring-performance-by-using-the-query-store"></a><span data-ttu-id="56863-102">쿼리 저장소를 사용하여 성능 모니터링</span><span class="sxs-lookup"><span data-stu-id="56863-102">Monitoring Performance By Using the Query Store</span></span>
  <span data-ttu-id="56863-103">쿼리 저장소 기능을 통해 DBA는 쿼리 계획 선택 및 성능에 대한 정보를 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="56863-103">The query store feature provides DBAs with insight on query plan choice and performance.</span></span> <span data-ttu-id="56863-104">쿼리 계획 변경으로 인해 발생하는 성능 차이를 신속하게 찾을 수 있도록 하여 성능 문제 해결을 간소화합니다.</span><span class="sxs-lookup"><span data-stu-id="56863-104">It simplifies performance troubleshooting by enabling you to quickly find performance differences caused by changes in query plans.</span></span> <span data-ttu-id="56863-105">이 기능은 쿼리, 계획 및 런타임 통계의 기록을 자동으로 캡처하고 검토할 수 있도록 이 기록을 유지합니다.</span><span class="sxs-lookup"><span data-stu-id="56863-105">The feature automatically captures a history of queries, plans, and runtime statistics, and retains these for your review.</span></span> <span data-ttu-id="56863-106">데이터를 기간별로 구분하여 데이터베이스 사용 패턴을 파악하고 서버에서 쿼리 계획 변경이 발생한 시기를 이해할 수 있게 해줍니다.</span><span class="sxs-lookup"><span data-stu-id="56863-106">It separates data by time windows, allowing you to see database usage patterns and understand when query plan changes happened on the server.</span></span> <span data-ttu-id="56863-107">쿼리 저장소는 [ALTER DATABASE SET](/sql/t-sql/statements/alter-database-transact-sql-set-options) 옵션을 사용하여 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="56863-107">The query store can be configured by using the [ALTER DATABASE SET](/sql/t-sql/statements/alter-database-transact-sql-set-options) option.</span></span>

||
|-|
|<span data-ttu-id="56863-108">**적용 대상**: [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)] ([가져오기](http://azure.micosoft.com/documentation/articles/sql-database-preview-whats-new/?WT.mc_id=TSQL_GetItTag)).</span><span class="sxs-lookup"><span data-stu-id="56863-108">**Applies to**: [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)] ([Get it](http://azure.micosoft.com/documentation/articles/sql-database-preview-whats-new/?WT.mc_id=TSQL_GetItTag)).</span></span>|

> [!IMPORTANT]
>  <span data-ttu-id="56863-109">현재 미리 보기 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="56863-109">This is currently a preview feature.</span></span> <span data-ttu-id="56863-110">쿼리 저장소를 사용하려면 쿼리 저장소 구현에는 사용권 계약(예: 기업계약, Microsoft Azure 계약 또는 Microsoft 온라인 정기가입 계약)의 미리 보기 약관과 해당 [Microsoft Azure 미리 보기 추가 사용 약관](https://azure.microsoft.com/support/legal/preview-supplemental-terms/)이 적용됨을 확인하고 이에 동의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="56863-110">To use the Query Store you must acknowledge and agree that implementation of Query Store is subject to the preview terms in your license agreement (e.g. the Enterprise Agreement, Microsoft Azure Agreement, or Microsoft Online Subscription Agreement), as well as any applicable [Supplemental Terms of Use for Microsoft Azure Preview](https://azure.microsoft.com/support/legal/preview-supplemental-terms/).</span></span>

##  <a name="enabling-the-query-store"></a><a name="Enabling"></a> <span data-ttu-id="56863-111">쿼리 저장소 사용</span><span class="sxs-lookup"><span data-stu-id="56863-111">Enabling the Query Store</span></span>
 <span data-ttu-id="56863-112">새 데이터베이스에서는 기본적으로 쿼리 저장소가 활성 상태가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="56863-112">Query Store is not active for new databases by default.</span></span>

#### <a name="by-using-the-query-store-page-in-management-studio"></a><span data-ttu-id="56863-113">Management Studio에서 쿼리 저장소 페이지 사용</span><span class="sxs-lookup"><span data-stu-id="56863-113">By Using the Query Store Page in Management Studio</span></span>

1.  <span data-ttu-id="56863-114">개체 탐색기에서 데이터베이스를 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="56863-114">In Object Explorer, right-click a database, and then click **Properties**.</span></span> <span data-ttu-id="56863-115">( [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 의 [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]2016 버전이 필요합니다.)</span><span class="sxs-lookup"><span data-stu-id="56863-115">(Requires [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 2016 version of [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)].)</span></span>

2.  <span data-ttu-id="56863-116">**데이터베이스 속성** 대화 상자에서 **쿼리 저장소** 페이지를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="56863-116">In the **Database Properties** dialog box, select the **Query Store** page.</span></span>

3.  <span data-ttu-id="56863-117">**사용** 상자에서 **True**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="56863-117">In the **Enable** box, select **True**.</span></span>

#### <a name="by-using-transact-sql-statements"></a><span data-ttu-id="56863-118">Transact-SQL 문 사용</span><span class="sxs-lookup"><span data-stu-id="56863-118">By Using Transact-SQL Statements</span></span>

1.  <span data-ttu-id="56863-119">`ALTER DATABASE` 문을 사용하여 쿼리 저장소를 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="56863-119">Use the `ALTER DATABASE` statement to enable the query store.</span></span> <span data-ttu-id="56863-120">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="56863-120">For example:</span></span>

    ```
    ALTER DATABASE AdventureWorks2012 SET QUERY_STORE = ON;
    ```

     <span data-ttu-id="56863-121">쿼리 저장소와 관련 된 구문 옵션에 대 한 자세한 내용은 [ALTER DATABASE SET options &#40;transact-sql&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="56863-121">For more syntax options related to the query store, see [ALTER DATABASE SET Options &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options).</span></span>

> [!NOTE]
>  <span data-ttu-id="56863-122">마스터 데이터베이스에 대해서는 쿼리 저장소를 사용하도록 설정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="56863-122">You cannot enable the query store for the master database.</span></span>



##  <a name="information-in-the-query-store"></a><a name="About"></a> <span data-ttu-id="56863-123">쿼리 저장소에 있는 정보</span><span class="sxs-lookup"><span data-stu-id="56863-123">Information in the Query Store</span></span>
 <span data-ttu-id="56863-124">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에서 특정 쿼리에 대한 실행 계획은 일반적으로 통계 변경, 스키마 변경, 인덱스 생성/삭제 등과 같은 여러 이유로 인해 시간에 따라 변경됩니다. 프로시저 캐시(캐시된 쿼리 계획이 저장되는 위치)에는 최신 실행 계획만 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="56863-124">Execution plans for any specific query in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] typically evolve over time due to a number of different reasons such as statistics changes, schema changes, creation/deletion of indexes, etc. The procedure cache (where cached query plans are stored) only stores the latest execution plan.</span></span> <span data-ttu-id="56863-125">또한 메모리 부족으로 인해 계획 캐시에서 계획이 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="56863-125">Plans also get evicted from the plan cache due to memory pressure.</span></span> <span data-ttu-id="56863-126">따라서 실행 계획 변경으로 인한 쿼리 성능 저하는 간단한 문제가 아니며 해결하는 데 시간이 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="56863-126">As a result, query performance regressions caused by execution plan changes can be non-trivial and time consuming to resolve.</span></span>

 <span data-ttu-id="56863-127">쿼리 저장소에서는 쿼리당 여러 실행 계획을 유지하므로 쿼리 프로세서가 쿼리에 대해 특정 실행 계획을 사용하도록 하는 정책을 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="56863-127">Since the query store retains multiple execution plans per query, it can enforce policies to direct the query processor to use a specific execution plan for a query.</span></span> <span data-ttu-id="56863-128">이를 계획 강제 적용이라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="56863-128">This is referred to as plan forcing.</span></span> <span data-ttu-id="56863-129">쿼리 저장소의 계획 강제 적용은 [USE PLAN](/sql/t-sql/queries/hints-transact-sql-query) 쿼리 힌트와 유사한 메커니즘을 사용하여 제공되지만 사용자 애플리케이션을 변경할 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="56863-129">Plan forcing in Query Store is provided by using a mechanism similar to the [USE PLAN](/sql/t-sql/queries/hints-transact-sql-query) query hint, but it does not require any change in user applications.</span></span> <span data-ttu-id="56863-130">계획 강제 적용은 계획 변경으로 인한 쿼리 성능 저하를 짧은 시간 내에 해결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="56863-130">Plan forcing can resolve a query performance regression caused by a plan change in a very short period of time.</span></span>

 <span data-ttu-id="56863-131">쿼리 저장소 기능을 사용하는 일반적인 시나리오는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="56863-131">Common scenarios for using the Query Store feature are:</span></span>

-   <span data-ttu-id="56863-132">이전 쿼리 계획을 적용하여 계획 성능 저하를 빠르게 찾고 해결합니다.</span><span class="sxs-lookup"><span data-stu-id="56863-132">Quickly find and fix a plan performance regression by forcing the previous query plan.</span></span> <span data-ttu-id="56863-133">실행 계획 변경으로 최근에 성능이 저하된 쿼리를 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="56863-133">Fix queries that have recently regressed in performance due to execution plan changes.</span></span>

-   <span data-ttu-id="56863-134">지정된 기간 내에 쿼리가 실행된 횟수를 확인하여 DBA의 성능 리소스 문제 해결을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="56863-134">Determine the number of times a query was executed in a given time window, assisting a DBA in troubleshooting performance resource problems.</span></span>

-   <span data-ttu-id="56863-135">실행 시간, 메모리 사용 등을 기준으로 이전 *x* 시간 동안의 상위 *n* 개 쿼리를 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="56863-135">Identify top *n* queries (by execution time, memory consumption, etc.) in the past *x* hours.</span></span>

-   <span data-ttu-id="56863-136">지정된 쿼리에 대한 쿼리 계획의 기록을 감사합니다.</span><span class="sxs-lookup"><span data-stu-id="56863-136">Audit the history of query plans for a given query.</span></span>

-   <span data-ttu-id="56863-137">특정 데이터베이스에 대한 리소스(CPU, I/O 및 메모리) 사용 패턴을 분석합니다.</span><span class="sxs-lookup"><span data-stu-id="56863-137">Analyze the resource (CPU, I/O, and Memory) usage patterns for a particular database.</span></span>

 <span data-ttu-id="56863-138">쿼리 저장소에는 실행 계획 정보를 유지하는 **계획 저장소** 와 실행 통계 정보를 유지하기 위한 **런타임 통계 저장소** 라는 두 가지 저장소가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="56863-138">The query store contains two stores; a **plan store** for persisting the execution plan information, and a **runtime stats store** for persisting the execution statistics information.</span></span> <span data-ttu-id="56863-139">쿼리 저장소에서 쿼리에 대해 저장할 수 있는 고유한 계획의 수는 `max_plans_per_query` 구성 옵션으로 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="56863-139">The number of unique plans that can be stored for a query in the plan store is limited by the `max_plans_per_query` configuration option.</span></span> <span data-ttu-id="56863-140">성능 향상을 위해 두 저장소에 비동기적으로 정보가 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="56863-140">To enhance performance, the information is written to the two stores asynchronously.</span></span> <span data-ttu-id="56863-141">공간 사용을 최소화하기 위해 런타임 통계 저장소의 런타임 실행 통계는 고정된 기간 동안 집계됩니다.</span><span class="sxs-lookup"><span data-stu-id="56863-141">To minimize space usage, the runtime execution statistics in the runtime stats store are aggregated over a fixed time window.</span></span> <span data-ttu-id="56863-142">이러한 저장소의 정보는 쿼리 저장소 카탈로그 뷰를 쿼리하여 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="56863-142">The information in these stores is visible by querying the query store catalog views.</span></span>

 <span data-ttu-id="56863-143">다음 쿼리는 쿼리 저장소의 쿼리 및 계획에 대한 정보를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="56863-143">The following query returns information about queries and plans in the query store.</span></span>

```
SELECT Txt.query_text_id, Txt.query_sql_text, Pl.plan_id, Qry.*
FROM sys.query_store_plan AS Pl
JOIN sys.query_store_query AS Qry
    ON Pl.query_id = Qry.query_id
JOIN sys.query_store_query_text AS Txt
    ON Qry.query_text_id = Txt.query_text_id ;
```



## <a name="using-the-regressed-queries-feature"></a><span data-ttu-id="56863-144">재발된 쿼리 기능 사용</span><span class="sxs-lookup"><span data-stu-id="56863-144">Using the Regressed Queries Feature</span></span>
 <span data-ttu-id="56863-145">쿼리 저장소를 사용 하도록 설정한 후 개체 탐색기 창의 데이터베이스 부분을 새로 고쳐 **쿼리 저장소** 섹션을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="56863-145">After enabling the query store, refresh the database portion of the Object Explorer pane to add the **Query Store** section.</span></span>

 <span data-ttu-id="56863-146">![QueryStore](../../database-engine/media/querystore.PNG "QueryStore")</span><span class="sxs-lookup"><span data-stu-id="56863-146">![QueryStore](../../database-engine/media/querystore.PNG "QueryStore")</span></span>

 <span data-ttu-id="56863-147">**재발된 쿼리**를 선택하면 **에서** 재발된 쿼리 [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]창이 열립니다.</span><span class="sxs-lookup"><span data-stu-id="56863-147">Selecting **Regressed Queries**, opens the **Regressed Queries** pane in [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)].</span></span> <span data-ttu-id="56863-148">재발된 쿼리 창에는 쿼리 저장소의 쿼리 및 계획이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="56863-148">The Regressed Queries pane shows you the queries, and plans in the query store.</span></span> <span data-ttu-id="56863-149">위쪽의 드롭다운 상자를 사용하여 다양한 기준에 따라 쿼리를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="56863-149">Drop down boxes at the top allow you to select queries based on various criteria.</span></span> <span data-ttu-id="56863-150">계획을 선택하면 그래픽 쿼리 계획이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="56863-150">Select a plan to see the graphical query plan.</span></span> <span data-ttu-id="56863-151">단추를 사용하여 원본 쿼리를 보고, 쿼리 계획을 강제 적용 및 적용 취소하고 표시를 새로 고칠 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="56863-151">Buttons are available to view the source query, force, and unforce a query plan, and refresh the display.</span></span>

 <span data-ttu-id="56863-152">![RegressedQueries](../../database-engine/media/regressedqueries.PNG "RegressedQueries")</span><span class="sxs-lookup"><span data-stu-id="56863-152">![RegressedQueries](../../database-engine/media/regressedqueries.PNG "RegressedQueries")</span></span>

 <span data-ttu-id="56863-153">계획을 강제 적용 하려면 쿼리 및 계획을 선택한 다음 **계획 강제 적용을 클릭 합니다.**</span><span class="sxs-lookup"><span data-stu-id="56863-153">To force a plan, select a query and plan, and then click **Force Plan.**</span></span> <span data-ttu-id="56863-154">쿼리 계획 기능으로 저장하고 쿼리 계획 캐시에 아직 보존되어 있는 계획만 강제 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="56863-154">You can only force plans that were saved by the query plan feature and are still retained in the query plan cache.</span></span>



##  <a name="configuration-options"></a><a name="Options"></a> <span data-ttu-id="56863-155">구성 옵션</span><span class="sxs-lookup"><span data-stu-id="56863-155">Configuration Options</span></span>
 <span data-ttu-id="56863-156">OPERATION_MODE READ_WRITE 또는 READ_ONLY 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="56863-156">OPERATION_MODE Can be READ_WRITE or READ_ONLY.</span></span>

 <span data-ttu-id="56863-157">CLEANUP_POLICY STALE_QUERY_THRESHOLD_DAYS 인수를 구성 하 여 쿼리 저장소에 데이터를 보존할 일 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="56863-157">CLEANUP_POLICY Configure the STALE_QUERY_THRESHOLD_DAYS argument to specify the number of days to retain data in the query store.</span></span>

 <span data-ttu-id="56863-158">DATA_FLUSH_INTERVAL_SECONDS 쿼리 저장소에 기록된 데이터가 디스크에 유지되는 빈도를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="56863-158">DATA_FLUSH_INTERVAL_SECONDS Determines the frequency at which data written to the query store is persisted to disk.</span></span> <span data-ttu-id="56863-159">성능 최적화를 위해 쿼리 저장소에서 수집한 데이터는 디스크에 비동기적으로 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="56863-159">To optimize for performance, data collected by the query store is asynchronously written to the disk.</span></span> <span data-ttu-id="56863-160">이 비동기 전송이 발생하는 빈도는 DATA_FLUSH_INTERVAL_SECONDS를 통해 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="56863-160">The frequency at which this asynchronous transfer occurs is configured via DATA_FLUSH_INTERVAL_SECONDS.</span></span>

 <span data-ttu-id="56863-161">MAX_SIZE_MB는 쿼리 저장소의 최대 크기를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="56863-161">MAX_SIZE_MB Configures the maximum size of the query store.</span></span> <span data-ttu-id="56863-162">쿼리 저장소의 데이터가 MAX_SIZE_MB 제한에 도달하는 경우 쿼리 저장소에서는 자동으로 상태를 읽기/쓰기에서 읽기 전용으로 변경하고 새 데이터 수집을 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="56863-162">If the data in the query store hits the MAX_SIZE_MB limit, the query store automatically changes the state from read-write to read-only and stops collecting new data.</span></span>

 <span data-ttu-id="56863-163">INTERVAL_LENGTH_MINUTES 런타임 실행 통계 데이터가 쿼리 저장소로 집계되는 간격을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="56863-163">INTERVAL_LENGTH_MINUTES Determines the time interval at which runtime execution statistics data is aggregated into the query store.</span></span> <span data-ttu-id="56863-164">공간 사용을 최적화하기 위해 런타임 통계 저장소의 런타임 실행 통계는 고정된 기간 동안 집계됩니다.</span><span class="sxs-lookup"><span data-stu-id="56863-164">To optimize for space usage, the runtime execution statistics in the Runtime Stats Store are aggregated over a fixed time window.</span></span> <span data-ttu-id="56863-165">이 고정된 기간은 INTERVAL_LENGTH_MINUTES를 통해 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="56863-165">This fixed time window is configured via INTERVAL_LENGTH_MINUTES.</span></span>

 <span data-ttu-id="56863-166">`sys.database_query_store_options` 뷰를 쿼리하여 쿼리 저장소의 현재 옵션을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="56863-166">Query the `sys.database_query_store_options` view to determine the current options of the query store.</span></span>

 <span data-ttu-id="56863-167">[!INCLUDE[tsql](../../includes/tsql-md.md)] 문을 사용하여 옵션을 설정하는 방법에 대한 자세한 내용은 [옵션 관리](#OptionMgmt)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="56863-167">For more information about setting options by using [!INCLUDE[tsql](../../includes/tsql-md.md)] statements, see [Option Management](#OptionMgmt).</span></span>

 

##  <a name="related-views-functions-and-procedures"></a><a name="Related"></a> <span data-ttu-id="56863-168">관련된 뷰, 함수 및 프로시저</span><span class="sxs-lookup"><span data-stu-id="56863-168">Related Views, Functions, and Procedures</span></span>
 <span data-ttu-id="56863-169">쿼리 저장소는 [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)] 를 통해 또는 다음과 같은 뷰 및 프로시저를 사용하여 보고 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="56863-169">The Query Store can be viewed and managed through [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)] or by using the following views and procedures.</span></span>

-   [<span data-ttu-id="56863-170">sys.fn_stmt_sql_handle_from_sql_stmt&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="56863-170">sys.fn_stmt_sql_handle_from_sql_stmt &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-functions/sys-fn-stmt-sql-handle-from-sql-stmt-transact-sql)

### <a name="query-store-catalog-views"></a><span data-ttu-id="56863-171">쿼리 저장소 카탈로그 뷰</span><span class="sxs-lookup"><span data-stu-id="56863-171">Query Store Catalog Views</span></span>
 <span data-ttu-id="56863-172">7개의 카탈로그 뷰에 쿼리 저장소에 대한 정보가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="56863-172">Seven catalog views present information about the Query Store.</span></span>

-   [<span data-ttu-id="56863-173">sys.database_query_store_options&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="56863-173">sys.database_query_store_options &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-database-query-store-options-transact-sql)

-   [<span data-ttu-id="56863-174">sys.query_context_settings&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="56863-174">sys.query_context_settings &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-query-context-settings-transact-sql)

-   [<span data-ttu-id="56863-175">sys.query_store_plan&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="56863-175">sys.query_store_plan &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-query-store-plan-transact-sql)

-   [<span data-ttu-id="56863-176">sys.query_store_query&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="56863-176">sys.query_store_query &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-query-store-query-transact-sql)

-   [<span data-ttu-id="56863-177">sys.query_store_query_text&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="56863-177">sys.query_store_query_text &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-query-store-query-text-transact-sql)

-   [<span data-ttu-id="56863-178">sys.query_store_runtime_stats&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="56863-178">sys.query_store_runtime_stats &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-query-store-runtime-stats-transact-sql)

-   [<span data-ttu-id="56863-179">sys.query_store_runtime_stats_interval&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="56863-179">sys.query_store_runtime_stats_interval &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-query-store-runtime-stats-interval-transact-sql)

### <a name="query-store-stored-procedures"></a><span data-ttu-id="56863-180">쿼리 저장소 저장 프로시저</span><span class="sxs-lookup"><span data-stu-id="56863-180">Query Store Stored Procedures</span></span>
 <span data-ttu-id="56863-181">6개의 저장 프로시저로 쿼리 저장소를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="56863-181">Six stored procedures configure the Query Store.</span></span>

-   [<span data-ttu-id="56863-182">sp_query_store_flush_db&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="56863-182">sp_query_store_flush_db &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-query-store-flush-db-transact-sql)

-   [<span data-ttu-id="56863-183">sp_query_store_reset_exec_stats&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="56863-183">sp_query_store_reset_exec_stats &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-query-store-reset-exec-stats-transact-sql)

-   [<span data-ttu-id="56863-184">sp_query_store_force_plan&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="56863-184">sp_query_store_force_plan &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-query-store-force-plan-transact-sql)

-   [<span data-ttu-id="56863-185">sp_query_store_unforce_plan&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="56863-185">sp_query_store_unforce_plan &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-query-store-unforce-plan-transact-sql)

-   [<span data-ttu-id="56863-186">sp_query_store_remove_plan&#40;Transct-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="56863-186">sp_query_store_remove_plan &#40;Transct-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-query-store-remove-plan-transct-sql)

-   [<span data-ttu-id="56863-187">sp_query_store_remove_query&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="56863-187">sp_query_store_remove_query &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-query-store-remove-query-transact-sql)



##  <a name="key-usage-scenarios"></a><a name="Scenarios"></a> <span data-ttu-id="56863-188">주요 사용 시나리오</span><span class="sxs-lookup"><span data-stu-id="56863-188">Key Usage Scenarios</span></span>

###  <a name="option-management"></a><a name="OptionMgmt"></a> <span data-ttu-id="56863-189">옵션 관리</span><span class="sxs-lookup"><span data-stu-id="56863-189">Option Management</span></span>
 <span data-ttu-id="56863-190">이 섹션에서는 쿼리 저장소 기능 자체를 관리하는 데 대한 지침을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="56863-190">This section provides some guidelines on managing Query Store feature itself.</span></span>

 <span data-ttu-id="56863-191">**쿼리 저장소가 현재 활성 상태인가요?**</span><span class="sxs-lookup"><span data-stu-id="56863-191">**Is Query Store currently active?**</span></span>

 <span data-ttu-id="56863-192">쿼리 저장소는 데이터를 사용자 데이터베이스 내에 저장하며 이 때문에 쿼리 저장소에는 크기 제한(`MAX_STORAGE_SIZE_MB`로 구성)이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="56863-192">Query Store stores its data inside the user database and that is why it has size limit (configured  with `MAX_STORAGE_SIZE_MB`).</span></span> <span data-ttu-id="56863-193">쿼리 저장소의 데이터가 이 제한에 도달하면 쿼리 저장소는 자동으로 상태를 읽기/쓰기에서 읽기 전용으로 변경하고 새 데이터 수집을 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="56863-193">If data in Query Store hits that limit Query Store will automatically change state from read-write to read-only and stop collecting new data.</span></span>

 <span data-ttu-id="56863-194">다음 스크립트를 실행하여 쿼리 저장소가 현재 활성 상태인지 여부와 현재 런타임 통계를 수집하는지 여부를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="56863-194">Execute the following script to determine if Query Store is currently active, and whether it is currently collects runtime stats or not.</span></span>

```
DECLARE @x nvarchar(100) = CAST(newid() AS nvarchar(100));
DECLARE @query nvarchar(max) = 
N'IF EXISTS
(
    SELECT * 
    FROM sys.query_store_query_text 
    WHERE query_sql_text LIKE ''%' + @x + N'%''
)
SELECT ''Query Store is active'' ;
ELSE SELECT ''Query Store is NOT active''' ;
EXEC sp_executesql @query;
```

 <span data-ttu-id="56863-195">**쿼리 저장소 옵션 가져오기**</span><span class="sxs-lookup"><span data-stu-id="56863-195">**Get Query Store options**</span></span>

 <span data-ttu-id="56863-196">쿼리 저장소 상태에 대한 자세한 정보를 찾으려면 사용자 데이터베이스에서 다음을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="56863-196">To find out detailed information about Query Store status, execute following in a user database.</span></span>

```
SELECT * FROM sys.database_query_store_options;
```

 <span data-ttu-id="56863-197">**쿼리 저장소 간격 설정**</span><span class="sxs-lookup"><span data-stu-id="56863-197">**Setting Query Store interval**</span></span>

 <span data-ttu-id="56863-198">쿼리 런타임 통계를 집계하는 간격(기본값은 60분)을 재정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="56863-198">You can override interval for aggregating query runtime statistics (default is 60 minutes).</span></span>

```

      USE master;
GO

ALTER DATABASE <database_name> 
SET QUERY_STORE (INTERVAL_LENGTH_MINUTES = 15);
```

 <span data-ttu-id="56863-199">임의의 값을 사용할 수는 없고 1, 5, 10, 15, 30 및 60 중에서 하나를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="56863-199">Note that arbitrary values are not allowed - you should use one of the following: 1, 5, 10, 15, 30 and 60.</span></span>

 <span data-ttu-id="56863-200">새 간격 값은 `sys.database_query_store_options` 뷰를 통해 노출됩니다.</span><span class="sxs-lookup"><span data-stu-id="56863-200">New value for interval is exposed through `sys.database_query_store_options` view.</span></span>

 <span data-ttu-id="56863-201">쿼리 스토리지 저장 공간이 꽉 차는 경우 다음 문을 사용하여 스토리지를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="56863-201">If the Query Store storage is full use the following statement to extend the storage.</span></span>

```
ALTER DATABASE <database_name> 
SET QUERY_STORE (MAX_STORAGE_SIZE_MB = <new_size>);
```

 <span data-ttu-id="56863-202">**모든 쿼리 저장소 옵션 설정**</span><span class="sxs-lookup"><span data-stu-id="56863-202">**Set all Query Store options**</span></span>

 <span data-ttu-id="56863-203">단일 ALTER DATABASE 문 사용하여 여러 쿼리 저장소 옵션을 한 번에 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="56863-203">You can set multiple Query Store options at once with a single ALTER DATABASE statement.</span></span>

```
ALTER DATABASE <database name> 
SET QUERY_STORE (
    OPERATION_MODE = READ_WRITE,
    CLEANUP_POLICY = 
    (STALE_QUERY_THRESHOLD_DAYS = 30),
    DATA_FLUSH_INTERVAL_SECONDS = 3000,
    MAX_STORAGE_SIZE_MB = 500,
    INTERVAL_LENGTH_MINUTES = 15
);
```

 <span data-ttu-id="56863-204">**공간 정리**</span><span class="sxs-lookup"><span data-stu-id="56863-204">**Cleaning up the space**</span></span>

 <span data-ttu-id="56863-205">데이터베이스 생성 중 쿼리 저장소 내부 테이블이 PRIMARY 파일 그룹에 만들어지며 해당 구성은 나중에 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="56863-205">Query Store internal tables are created in the PRIMARY filegroup during database creation and that configuration cannot be changed later.</span></span> <span data-ttu-id="56863-206">공간이 부족한 경우 다음 문을 사용하여 이전 쿼리 저장소 데이터를 지울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="56863-206">If you are running out of space you might want to clear older Query Store data by using the following statement.</span></span>

```
ALTER DATABASE <db_name> SET QUERY_STORE CLEAR;
```

 <span data-ttu-id="56863-207">또는 임시 쿼리 데이터는 쿼리 최적화 및 계획 분석과 관련성이 적고 공간만 많이 차지하므로 임시 쿼리 데이터만 지울 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="56863-207">Alternatively, you might want to clear up only ad-hoc query data, since it is less relevant for query optimizations and plan analysis but takes up just as much space.</span></span>

 <span data-ttu-id="56863-208">**임시 쿼리 삭제** 한번만 실행되고 24시간 이상 지난 쿼리를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="56863-208">**Delete ad-hoc queries** This deletes the queries that were only executed only once and that are more than 24 hours old.</span></span>

```
DECLARE @id int
DECLARE adhoc_queries_cursor CURSOR 
FOR 
SELECT q.query_id
FROM sys.query_store_query_text AS qt
JOIN sys.query_store_query AS q 
    ON q.query_text_id = qt.query_text_id
JOIN sys.query_store_plan AS p 
    ON p.query_id = q.query_id
JOIN sys.query_store_runtime_stats AS rs 
    ON rs.plan_id = p.plan_id
GROUP BY q.query_id
HAVING SUM(rs.count_executions) < 2 
AND MAX(rs.last_execution_time) < DATEADD (hour, -24, GETUTCDATE())
ORDER BY q.query_id ;

OPEN adhoc_queries_cursor ;
FETCH NEXT FROM adhoc_queries_cursor INTO @id;
WHILE @@fetch_status = 0
    BEGIN 
        PRINT @id
        EXEC sp_query_store_remove_query @id
        FETCH NEXT FROM adhoc_queries_cursor INTO @id
    END 
CLOSE adhoc_queries_cursor ;
DEALLOCATE adhoc_queries_cursor;
```

 <span data-ttu-id="56863-209">더 이상 중요하지 않은 데이터를 지우는 다른 논리를 사용하여 프로시저를 직접 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="56863-209">You can define your own procedure with different logic for clearing up the data that is no longer important for you.</span></span>

 <span data-ttu-id="56863-210">위의 예제에서는 필요 없는 데이터를 제거하는 `sp_query_store_remove_query` 확장 저장 프로시저를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="56863-210">The example above uses the `sp_query_store_remove_query` extended stored procedure for removing unnecessary data.</span></span> <span data-ttu-id="56863-211">다른 두 프로시저를 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="56863-211">You can also use two other procedures.</span></span>

-   <span data-ttu-id="56863-212">`sp_query_store_reset_exec_stats`-지정 된 계획에 대 한 런타임 통계를 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="56863-212">`sp_query_store_reset_exec_stats` - clear runtime statistics for a given plan.</span></span>

-   <span data-ttu-id="56863-213">`sp_query_store_remove_plan`-단일 계획을 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="56863-213">`sp_query_store_remove_plan` - removes a single plan.</span></span>



###  <a name="performance-auditing-and-troubleshooting"></a><a name="Peformance"></a> <span data-ttu-id="56863-214">성능 감사 및 문제해결</span><span class="sxs-lookup"><span data-stu-id="56863-214">Performance Auditing and Troubleshooting</span></span>
 <span data-ttu-id="56863-215">쿼리 저장소에서는 전체 쿼리 실행 중에 컴파일 및 런타임 메트릭에 대한 기록을 유지하므로 작업과 관련된 다양한 질문에 쉽게 답할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="56863-215">Because Query Store keeps history of compilation and runtime metrics throughout query executions there are many different questions you can easily answer with regards to your workload.</span></span>

 <span data-ttu-id="56863-216">**데이터베이스에서 실행 된 마지막 *n* 개의 쿼리**</span><span class="sxs-lookup"><span data-stu-id="56863-216">**Last *n* queries executed on the database.**</span></span>

```
SELECT TOP 10 qt.query_sql_text, q.query_id, 
    qt.query_text_id, p.plan_id, rs.last_execution_time
FROM sys.query_store_query_text AS qt 
JOIN sys.query_store_query AS q 
    ON qt.query_text_id = q.query_text_id 
JOIN sys.query_store_plan AS p 
    ON q.query_id = p.query_id 
JOIN sys.query_store_runtime_stats AS rs 
    ON p.plan_id = rs.plan_id
ORDER BY rs.last_execution_time DESC;
```

 <span data-ttu-id="56863-217">**각 쿼리에 대 한 실행 수입니다.**</span><span class="sxs-lookup"><span data-stu-id="56863-217">**Number of executions for each query.**</span></span>

```
SELECT q.query_id, qt.query_text_id, qt.query_sql_text, 
    SUM(rs.count_executions) AS total_execution_count
FROM sys.query_store_query_text AS qt 
JOIN sys.query_store_query AS q 
    ON qt.query_text_id = q.query_text_id 
JOIN sys.query_store_plan AS p 
    ON q.query_id = p.query_id 
JOIN sys.query_store_runtime_stats AS rs 
    ON p.plan_id = rs.plan_id
GROUP BY q.query_id, qt.query_text_id, qt.query_sql_text
ORDER BY total_execution_count DESC;
```

 <span data-ttu-id="56863-218">**지난 1 시간 내에 평균 실행 시간이 가장 긴 쿼리 수입니다.**</span><span class="sxs-lookup"><span data-stu-id="56863-218">**The number of queries with the longest average execution time within last hour.**</span></span>

```
SELECT TOP 10 rs.avg_duration, qt.query_sql_text, q.query_id,
    qt.query_text_id, p.plan_id, GETUTCDATE() AS CurrentUTCTime, 
    rs.last_execution_time 
FROM sys.query_store_query_text AS qt 
JOIN sys.query_store_query AS q 
    ON qt.query_text_id = q.query_text_id 
JOIN sys.query_store_plan AS p 
    ON q.query_id = p.query_id 
JOIN sys.query_store_runtime_stats AS rs 
    ON p.plan_id = rs.plan_id
WHERE rs.last_execution_time > DATEADD(hour, -1, GETUTCDATE())
ORDER BY rs.avg_duration DESC;
```

 <span data-ttu-id="56863-219">**지난 24 시간 동안 평균 물리적 IO 읽기가 가장 큰 쿼리 수 및 해당 하는 평균 행 수 및 실행 수**</span><span class="sxs-lookup"><span data-stu-id="56863-219">**The number of queries that had the biggest average physical IO reads in last 24 hours, with corresponding average row count and execution count.**</span></span>

```
SELECT TOP 10 rs.avg_physical_io_reads, qt.query_sql_text, 
    q.query_id, qt.query_text_id, p.plan_id, rs.runtime_stats_id, 
    rsi.start_time, rsi.end_time, rs.avg_rowcount, rs.count_executions
FROM sys.query_store_query_text AS qt 
JOIN sys.query_store_query AS q 
    ON qt.query_text_id = q.query_text_id 
JOIN sys.query_store_plan AS p 
    ON q.query_id = p.query_id 
JOIN sys.query_store_runtime_stats AS rs 
    ON p.plan_id = rs.plan_id 
JOIN sys.query_store_runtime_stats_interval AS rsi 
    ON rsi.runtime_stats_interval_id = rs.runtime_stats_interval_id
WHERE rsi.start_time >= DATEADD(hour, -24, GETUTCDATE()) 
ORDER BY rs.avg_physical_io_reads DESC;
```

 <span data-ttu-id="56863-220">**여러 계획을 사용 하는 쿼리**</span><span class="sxs-lookup"><span data-stu-id="56863-220">**Queries with multiple plans.**</span></span> <span data-ttu-id="56863-221">이러한 쿼리는 계획 선택 변경으로 인한 재발을 일으킬 수 있으므로 특히 흥미롭습니다.</span><span class="sxs-lookup"><span data-stu-id="56863-221">These queries are especially interesting because they are candidates for regressions due to plan choice change.</span></span> <span data-ttu-id="56863-222">다음 쿼리는 이러한 쿼리와 함께 모든 계획을 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="56863-222">The following query identifies these queries along with all plans:</span></span>

```
WITH Query_MultPlans
AS
(
    SELECT COUNT(*) AS cnt, q.query_id 
    FROM sys.query_store_query_text AS qt
    JOIN sys.query_store_query AS q
        ON qt.query_text_id = q.query_text_id
    JOIN sys.query_store_plan AS p
        ON p.query_id = q.query_id
    GROUP BY q.query_id
    HAVING COUNT(distinct plan_id) > 1
)

SELECT q.query_id, object_name(object_id) AS ContainingObject, query_sql_text,
plan_id, p.query_plan AS plan_xml,
p.last_compile_start_time, p.last_execution_time
FROM Query_MultPlans AS qm
JOIN sys.query_store_query AS q
    ON qm.query_id = q.query_id
JOIN sys.query_store_plan AS p
    ON q.query_id = p.query_id
JOIN sys.query_store_query_text qt 
    ON qt.query_text_id = q.query_text_id
ORDER BY query_id, plan_id;
```

 <span data-ttu-id="56863-223">**최근에 성능이 저하 된 쿼리 (다른 시점 비교)**</span><span class="sxs-lookup"><span data-stu-id="56863-223">**Queries that recently regressed in performance (comparing different point in time).**</span></span> <span data-ttu-id="56863-224">다음 쿼리 예제는 지난 48 시간에 계획 선택 변경으로 인해 실행 시간이 두 배가 된 모든 쿼리를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="56863-224">The following query example returns all queries for which execution time doubled in last 48 hours due to a plan choice change.</span></span> <span data-ttu-id="56863-225">쿼리에서는 모든 런타임 통계 간격을 나란히 비교합니다.</span><span class="sxs-lookup"><span data-stu-id="56863-225">Query compares all runtime stat intervals side by side.</span></span>

```
SELECT 
    qt.query_sql_text, 
    q.query_id, 
    qt.query_text_id, 
    rs1.runtime_stats_id AS runtime_stats_id_1,
    rsi1.start_time AS interval_1, 
    p1.plan_id AS plan_1, 
    rs1.avg_duration AS avg_duration_1, 
    rs2.avg_duration AS avg_duration_2,
    p2.plan_id AS plan_2, 
    rsi2.start_time AS interval_2, 
    rs2.runtime_stats_id AS runtime_stats_id_2
FROM sys.query_store_query_text AS qt 
JOIN sys.query_store_query AS q 
    ON qt.query_text_id = q.query_text_id 
JOIN sys.query_store_plan AS p1 
    ON q.query_id = p1.query_id 
JOIN sys.query_store_runtime_stats AS rs1 
    ON p1.plan_id = rs1.plan_id 
JOIN sys.query_store_runtime_stats_interval AS rsi1 
    ON rsi1.runtime_stats_interval_id = rs1.runtime_stats_interval_id 
JOIN sys.query_store_plan AS p2 
    ON q.query_id = p2.query_id 
JOIN sys.query_store_runtime_stats AS rs2 
    ON p2.plan_id = rs2.plan_id 
JOIN sys.query_store_runtime_stats_interval AS rsi2 
    ON rsi2.runtime_stats_interval_id = rs2.runtime_stats_interval_id
WHERE rsi1.start_time > DATEADD(hour, -48, GETUTCDATE()) 
    AND rsi2.start_time > rsi1.start_time 
    AND p1.plan_id <> p2.plan_id
    AND rs2.avg_duration > 2*rs1.avg_duration
ORDER BY q.query_id, rsi1.start_time, rsi2.start_time;
```

 <span data-ttu-id="56863-226">계획 선택 변경과 관련된 성능 저하뿐 아니라 성능 저하를 모두 확인하려면 이전 쿼리에서 `AND p1.plan_id <> p2.plan_id` 조건을 제거하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="56863-226">If you want to see performance all regressions (not only those related to plan choice change) than just remove condition `AND p1.plan_id <> p2.plan_id` from the previous query.</span></span>

 <span data-ttu-id="56863-227">**최근에 성능이 저하 된 쿼리 (최근 및 기록 실행 비교).**</span><span class="sxs-lookup"><span data-stu-id="56863-227">**Queries that recently regressed in performance (comparing recent vs. history execution).**</span></span> <span data-ttu-id="56863-228">다음 쿼리는 실행 기간을 기준으로 쿼리 실행을 비교합니다.</span><span class="sxs-lookup"><span data-stu-id="56863-228">The next query compares query execution based periods of execution.</span></span> <span data-ttu-id="56863-229">이 특정 예제의 쿼리는 최근 기간(1시간) 및 기록 기간(어제)의 실행을 비교하고 additional_duration_workload를 초래한 쿼리를 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="56863-229">In this particular example the query compares execution in recent period (1 hour) vs. history period (last day) and identifies those that introduced additional_duration_workload.</span></span> <span data-ttu-id="56863-230">이 메트릭은 최근 평균 실행 기간과 기록 평균 실행 간의 차이에 최근 실행 수를 곱한 값으로 계산됩니다.</span><span class="sxs-lookup"><span data-stu-id="56863-230">This metrics is calculated as a difference between recent average execution and history average execution multiplied by the number of recent executions.</span></span> <span data-ttu-id="56863-231">이 값은 실제로 기록에 비해 최근 실행으로 초래된 추가 기간을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="56863-231">It actually represents how much of additional duration recent executions introduced compared to history:</span></span>

```
--- "Recent" workload - last 1 hour
DECLARE @recent_start_time datetimeoffset;
DECLARE @recent_end_time datetimeoffset;
SET @recent_start_time = DATEADD(hour, -1, SYSUTCDATETIME());
SET @recent_end_time = SYSUTCDATETIME();

--- "History" workload
DECLARE @history_start_time datetimeoffset;
DECLARE @history_end_time datetimeoffset;
SET @history_start_time = DATEADD(hour, -24, SYSUTCDATETIME());
SET @history_end_time = SYSUTCDATETIME();

WITH
hist AS
(
    SELECT 
        p.query_id query_id, 
        CONVERT(float, SUM(rs.avg_duration*rs.count_executions)) total_duration, 
        SUM(rs.count_executions) count_executions,
        COUNT(distinct p.plan_id) num_plans 
     FROM sys.query_store_runtime_stats AS rs
        JOIN sys.query_store_plan p ON p.plan_id = rs.plan_id
    WHERE  (rs.first_execution_time >= @history_start_time AND rs.last_execution_time < @history_end_time)
        OR (rs.first_execution_time <= @history_start_time AND rs.last_execution_time > @history_start_time)
        OR (rs.first_execution_time <= @history_end_time AND rs.last_execution_time > @history_end_time)
    GROUP BY p.query_id
),
recent AS
(
    SELECT 
        p.query_id query_id, 
        CONVERT(float, SUM(rs.avg_duration*rs.count_executions)) total_duration, 
        SUM(rs.count_executions) count_executions,
        COUNT(distinct p.plan_id) num_plans 
    FROM sys.query_store_runtime_stats AS rs
        JOIN sys.query_store_plan p ON p.plan_id = rs.plan_id
    WHERE  (rs.first_execution_time >= @recent_start_time AND rs.last_execution_time < @recent_end_time)
        OR (rs.first_execution_time <= @recent_start_time AND rs.last_execution_time > @recent_start_time)
        OR (rs.first_execution_time <= @recent_end_time AND rs.last_execution_time > @recent_end_time)
    GROUP BY p.query_id
)
SELECT 
    results.query_id query_id,
    results.query_text query_text,
    results.additional_duration_workload additional_duration_workload,
    results.total_duration_recent total_duration_recent,
    results.total_duration_hist total_duration_hist,
    ISNULL(results.count_executions_recent, 0) count_executions_recent,
    ISNULL(results.count_executions_hist, 0) count_executions_hist 
FROM
(
    SELECT
        hist.query_id query_id,
        qt.query_sql_text query_text,
        ROUND(CONVERT(float, recent.total_duration/recent.count_executions-hist.total_duration/hist.count_executions)*(recent.count_executions), 2) AS additional_duration_workload,
        ROUND(recent.total_duration, 2) total_duration_recent, 
        ROUND(hist.total_duration, 2) total_duration_hist,
        recent.count_executions count_executions_recent,
        hist.count_executions count_executions_hist   
    FROM hist 
        JOIN recent 
            ON hist.query_id = recent.query_id 
        JOIN sys.query_store_query AS q 
            ON q.query_id = hist.query_id
        JOIN sys.query_store_query_text AS qt 
            ON q.query_text_id = qt.query_text_id    
) AS results
WHERE additional_duration_workload > 0
ORDER BY additional_duration_workload DESC
OPTION (MERGE JOIN);
```



###  <a name="maintaining-query-performance-stability"></a><a name="Stability"></a><span data-ttu-id="56863-232">쿼리 성능 안정성 유지 관리</span><span class="sxs-lookup"><span data-stu-id="56863-232">Maintaining Query Performance Stability</span></span>
 <span data-ttu-id="56863-233">여러 번 실행되는 쿼리의 경우 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 에서 다른 계획을 사용하여 리소스 사용률 및 기간이 달라짐을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="56863-233">For queries that are executed multiple times you may notice that [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] used different plans which resulted in different resource utilization and duration.</span></span> <span data-ttu-id="56863-234">쿼리 저장소를 사용하면 쿼리 성능이 저하되는 시기를 쉽게 확인하고 관심 있는 기간 내에 최적의 계획을 결정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="56863-234">With Query Store you can easily detect when the query performance regressed and determine the optimal plan within a period of interest.</span></span> <span data-ttu-id="56863-235">그런 다음 향후 쿼리 실행에 해당하는 최적의 계획을 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="56863-235">Then you can force that optimal plan for future query execution.</span></span>

 <span data-ttu-id="56863-236">또한 자동으로 매개 변수화되거나 수동으로 매개 변수화되는 매개 변수를 사용하여 일관성이 없는 쿼리 성능도 식별할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="56863-236">You can also identify inconsistent query performance for a query with parameters (either auto- parameterized or manually parameterized).</span></span> <span data-ttu-id="56863-237">여러 계획 중에 대부분의 매개 변수 값에 대해 빠르고 최적화된 계획을 식별하고 해당 계획을 강제 적용할 수 있습니다. 이를 통해 다양한 사용자 시나리오에 대해 예측 가능한 성능을 유지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="56863-237">Among different plans you can identify plan which is fast and optimal enough for all or most of the parameter values and force that plan; keeping predictable performance for the wider set of user scenarios.</span></span>

 <span data-ttu-id="56863-238">**쿼리에 대 한 계획 강제 적용(강제 적용 정책 적용)**</span><span class="sxs-lookup"><span data-stu-id="56863-238">**Force or a plan for a query (apply forcing policy).**</span></span> <span data-ttu-id="56863-239">특정 쿼리에 계획을 ;강제 적용하는 경우 쿼리를 실행할 때마다 강제 적용된 계획이 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="56863-239">When a plan is forced for a certain query, every time a query comes to execution it will be executed with the plan that is forced.</span></span>

```
EXEC sp_query_store_force_plan @query_id = 48, @plan_id = 49;
```

 <span data-ttu-id="56863-240">`sp_query_store_force_plan`을 사용할 경우 쿼리 저장소에서 해당 쿼리에 대한 계획으로 기록된 계획만 강제로 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="56863-240">When using `sp_query_store_force_plan` you can only force plans that were recorded by Query Store as a plan for that query.</span></span> <span data-ttu-id="56863-241">즉, 쿼리 저장소가 활성 상태일 때 Q1을 실행하는 데 이미 사용된 계획만 쿼리에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="56863-241">In other words, the only plans available for a query are those that were already used to execute Q1 while Query Store was active.</span></span>

 <span data-ttu-id="56863-242">**쿼리에 대 한 계획 강제 적용을 제거 합니다.**</span><span class="sxs-lookup"><span data-stu-id="56863-242">**Remove plan forcing for a query.**</span></span> <span data-ttu-id="56863-243">쿼리 최적화 프로그램을 다시 사용 하 여 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 최적의 쿼리 계획을 계산 하려면를 사용 하 여 `sp_query_store_unforce_plan` 쿼리에 대해 선택한 계획의 강제 적용을 해제 합니다.</span><span class="sxs-lookup"><span data-stu-id="56863-243">To rely again on the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] query optimizer to calculate the optimal query plan, use `sp_query_store_unforce_plan` to unforce the plan that was selected for the query.</span></span>

```
EXEC sp_query_store_unforce_plan @query_id = 48, @plan_id = 49;
```



## <a name="see-also"></a><span data-ttu-id="56863-244">참고 항목</span><span class="sxs-lookup"><span data-stu-id="56863-244">See Also</span></span>
 <span data-ttu-id="56863-245">[성능 성능 모니터링 및 조정](../performance/monitor-and-tune-for-performance.md) [도구 모니터링 및 조정 도구](../performance/performance-monitoring-and-tuning-tools.md) [&#40;작업 모니터 열기&#41;](../performance-monitor/open-activity-monitor-sql-server-management-studio.md) [작업 모니터](../performance-monitor/activity-monitor.md) SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="56863-245">[Monitor and Tune for Performance](../performance/monitor-and-tune-for-performance.md) [Performance Monitoring and Tuning Tools](../performance/performance-monitoring-and-tuning-tools.md) [Open Activity Monitor &#40;SQL Server Management Studio&#41;](../performance-monitor/open-activity-monitor-sql-server-management-studio.md) [Activity Monitor](../performance-monitor/activity-monitor.md)</span></span>


