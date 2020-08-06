---
title: 데이터베이스 속성(쿼리 저장소 페이지) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- sql13.swb.databaseproperties.querystore.f1
ms.assetid: da47d75e-291a-4305-acef-4b0aaf5215da
author: stevestein
ms.author: sstein
ms.openlocfilehash: bab0d9b697e9ad9ec4b27f320d26b9b9edb5944e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734124"
---
# <a name="database-properties-query-store-page"></a><span data-ttu-id="86958-102">데이터베이스 속성(쿼리 저장소 페이지)</span><span class="sxs-lookup"><span data-stu-id="86958-102">Database Properties (Query Store Page)</span></span>
  <span data-ttu-id="86958-103">이 페이지는 주 데이터베이스에서 액세스하며 데이터베이스 쿼리 저장소의 속성을 구성하고 수정하는 데 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="86958-103">Access this page from the principal database, and use it to configure and to modify the properties of the database query store.</span></span> <span data-ttu-id="86958-104">[ALTER DATABASE SET 옵션](/sql/t-sql/statements/alter-database-transact-sql-set-options)을 사용하여 이러한 옵션을 구성할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="86958-104">These options can also be configure by using the [ALTER DATABASE SET options](/sql/t-sql/statements/alter-database-transact-sql-set-options).</span></span> <span data-ttu-id="86958-105">쿼리 저장소에 대한 자세한 내용은 [Monitoring Performance By Using the Query Store](../performance/monitoring-performance-by-using-the-query-store.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="86958-105">For information about the query store, see [Monitoring Performance By Using the Query Store](../performance/monitoring-performance-by-using-the-query-store.md).</span></span>  
  
||  
|-|  
|<span data-ttu-id="86958-106">**적용 대상**: [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)].</span><span class="sxs-lookup"><span data-stu-id="86958-106">**Applies to**: [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)].</span></span>|  
  
## <a name="options"></a><span data-ttu-id="86958-107">옵션</span><span class="sxs-lookup"><span data-stu-id="86958-107">Options</span></span>  
 <span data-ttu-id="86958-108">사용</span><span class="sxs-lookup"><span data-stu-id="86958-108">Enable</span></span>  
 <span data-ttu-id="86958-109">쿼리 저장소를 사용하거나 사용하지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="86958-109">Enables and disables the query store.</span></span>  
  
 <span data-ttu-id="86958-110">작업 모드</span><span class="sxs-lookup"><span data-stu-id="86958-110">Operation Mode</span></span>  
 <span data-ttu-id="86958-111">유효한 값은 READ_ONLY 및 READ_WRITE입니다.</span><span class="sxs-lookup"><span data-stu-id="86958-111">Valid values are READ_ONLY and READ_WRITE.</span></span> <span data-ttu-id="86958-112">READ_WRITE 모드에서 쿼리 저장소는  쿼리 계획 및 런타임 실행 통계 정보를 수집하고 유지합니다.</span><span class="sxs-lookup"><span data-stu-id="86958-112">In READ_WRITE mode, the query store collects and persists query plan and runtime execution statistics information.</span></span> <span data-ttu-id="86958-113">READ_ONLY 모드에서는 쿼리 저장소에서 정보를 읽을 수 있지만 새 정보는 추가되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="86958-113">In READ_ONLY mode, information can be read from the query store, but new information is not added.</span></span> <span data-ttu-id="86958-114">쿼리 저장소의 최대 할당 공간이 모두 사용되면 쿼리 저장소는 작업 모드를 READ_ONLY로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="86958-114">If the maximum allocated space of the query store has been exhausted, the query store will change its operation mode to READ_ONLY.</span></span>  
  
 <span data-ttu-id="86958-115">작업 모드(실제)</span><span class="sxs-lookup"><span data-stu-id="86958-115">Operation Mode (Actual)</span></span>  
 <span data-ttu-id="86958-116">쿼리 저장소의 작업 모드를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="86958-116">Gets the actual operation mode of the query store.</span></span>  
  
 <span data-ttu-id="86958-117">작업 모드(요청)</span><span class="sxs-lookup"><span data-stu-id="86958-117">Operation Mode (Requested)</span></span>  
 <span data-ttu-id="86958-118">쿼리 저장소의 원하는 작업 모드를 가져오거나 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="86958-118">Gets and sets the desired operation mode of the query store.</span></span>  
  
 <span data-ttu-id="86958-119">데이터 플러시 간격(분)</span><span class="sxs-lookup"><span data-stu-id="86958-119">Data Flush Interval (Minutes)</span></span>  
 <span data-ttu-id="86958-120">쿼리 저장소에 기록된 데이터가 디스크에 유지되는 빈도를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="86958-120">Determines the frequency at which data written to the query store is persisted to disk.</span></span> <span data-ttu-id="86958-121">성능 최적화를 위해 쿼리 저장소에서 수집한 데이터는 디스크에 비동기적으로 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="86958-121">To optimize for performance, data collected by the query store is asynchronously written to the disk.</span></span> <span data-ttu-id="86958-122">이 비동기 전송이 발생되는 빈도가 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="86958-122">The frequency at which this asynchronous transfer occurs is configured.</span></span>  
  
 <span data-ttu-id="86958-123">통계 수집 간격</span><span class="sxs-lookup"><span data-stu-id="86958-123">Statistics Collection Interval</span></span>  
 <span data-ttu-id="86958-124">통계 수집 간격 값을 가져오거나 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="86958-124">Gets and sets the statistics collection interval value.</span></span>  
  
 <span data-ttu-id="86958-125">최대 크기(MB)</span><span class="sxs-lookup"><span data-stu-id="86958-125">Max Size (MB)</span></span>  
 <span data-ttu-id="86958-126">쿼리 저장소에 할당된 총 공간을 가져오거나 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="86958-126">Gets and sets the total space allocated to the query store.</span></span>  
  
 <span data-ttu-id="86958-127">오래된 쿼리 임계값(일)</span><span class="sxs-lookup"><span data-stu-id="86958-127">Stale Query Threshold (Days)</span></span>  
 <span data-ttu-id="86958-128">오래된 쿼리 임계값을 가져오거나 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="86958-128">Gets and sets the stale query threshold.</span></span> <span data-ttu-id="86958-129">STALE_QUERY_THRESHOLD_DAYS 인수를 구성하여 쿼리 저장소에 데이터를 보존할 일수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="86958-129">Configure the STALE_QUERY_THRESHOLD_DAYS argument to specify the number of days to retain data in the query store.</span></span>  
  
 <span data-ttu-id="86958-130">쿼리 데이터 삭제</span><span class="sxs-lookup"><span data-stu-id="86958-130">Purge Query Data</span></span>  
 <span data-ttu-id="86958-131">쿼리 저장소의 내용을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="86958-131">Removes the contents of the query store.</span></span>  
  
 <span data-ttu-id="86958-132">원형 차트</span><span class="sxs-lookup"><span data-stu-id="86958-132">Pie Charts</span></span>  
 <span data-ttu-id="86958-133">왼쪽 차트에는 디스크의 총 데이터베이스 파일 사용 및 쿼리 저장소 데이터로 채워진 파일 부분이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="86958-133">The left chart shows the total database file consumption on the disk, and the portion of the file which is filled with the query store data.</span></span>  
  
 <span data-ttu-id="86958-134">오른쪽 차트에는 현재 사용된 쿼리 저장소 할당량 부분이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="86958-134">The right chart shows the portion of the query store quota which is currently used up.</span></span> <span data-ttu-id="86958-135">왼쪽 차트에는 할당량이 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="86958-135">Note that the quota is not shown in the left chart.</span></span> <span data-ttu-id="86958-136">할당량이 데이터베이스의 현재 크기를 초과할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="86958-136">The quota may exceed the current size of the database.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="86958-137">설명</span><span class="sxs-lookup"><span data-stu-id="86958-137">Remarks</span></span>  
 <span data-ttu-id="86958-138">쿼리 저장소 기능을 통해 DBA는 쿼리 계획 선택 및 성능에 대한 정보를 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="86958-138">The query store feature provides DBAs with insight on query plan choice and performance.</span></span> <span data-ttu-id="86958-139">쿼리 계획 변경으로 인해 발생하는 성능 차이를 신속하게 찾을 수 있도록 하여 성능 문제 해결을 간소화합니다.</span><span class="sxs-lookup"><span data-stu-id="86958-139">It simplifies performance troubleshooting by enabling you to quickly find performance differences caused by changes in query plans.</span></span> <span data-ttu-id="86958-140">이 기능은 쿼리, 계획 및 런타임 통계의 기록을 자동으로 캡처하고 검토할 수 있도록 이 기록을 유지합니다.</span><span class="sxs-lookup"><span data-stu-id="86958-140">The feature automatically captures a history of queries, plans, and runtime statistics, and retains these for your review.</span></span> <span data-ttu-id="86958-141">데이터를 기간별로 구분하여 데이터베이스 사용 패턴을 파악하고 서버에서 쿼리 계획 변경이 발생한 시기를 이해할 수 있게 해줍니다.</span><span class="sxs-lookup"><span data-stu-id="86958-141">It separates data by time windows, allowing you to see database usage patterns and understand when query plan changes happened on the server.</span></span> <span data-ttu-id="86958-142">쿼리 저장소는 이 쿼리 저장소 데이터베이스 속성 페이지를 사용하거나 [ALTER DATABASE SET](/sql/t-sql/statements/alter-database-transact-sql-set-options) 옵션을 사용하여 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="86958-142">The query store can be configured by using this query store database property page, or by using the [ALTER DATABASE SET](/sql/t-sql/statements/alter-database-transact-sql-set-options) option.</span></span> <span data-ttu-id="86958-143">쿼리 저장소는 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 대화 상자를 사용하여 정보를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="86958-143">The query store presents information by using a [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] dialog box.</span></span> <span data-ttu-id="86958-144">쿼리 저장소에 대한 자세한 내용은 [Monitoring Performance By Using the Query Store](../performance/monitoring-performance-by-using-the-query-store.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="86958-144">For more information about query store, see [Monitoring Performance By Using the Query Store](../performance/monitoring-performance-by-using-the-query-store.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86958-145">참고 항목</span><span class="sxs-lookup"><span data-stu-id="86958-145">See Also</span></span>  
 <span data-ttu-id="86958-146">[쿼리 저장소 저장 프로시저&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/query-store-stored-procedures-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="86958-146">[Query Store Stored Procedures &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/query-store-stored-procedures-transact-sql) </span></span>  
 [<span data-ttu-id="86958-147">쿼리 저장소 카탈로그 뷰&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="86958-147">Query Store Catalog Views &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/query-store-catalog-views-transact-sql)  
  
  
