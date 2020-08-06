---
title: 공유 데이터 세트 캐시(SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 4acb1bbe-1c04-4979-b893-dc1b1c5039b6
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 5b08149b075ae3fd267baf2dad0ca342457958c5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652610"
---
# <a name="cache-shared-datasets-ssrs"></a><span data-ttu-id="80ee9-102">공유 데이터 세트 캐시(SSRS)</span><span class="sxs-lookup"><span data-stu-id="80ee9-102">Cache Shared Datasets (SSRS)</span></span>
  <span data-ttu-id="80ee9-103">공유 데이터 세트에 대한 쿼리 결과를 캐시로 복사하여 여러 보고서에 일관성 있는 데이터를 제공하고 데이터 세트 쿼리에 대한 응답 시간을 향상시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80ee9-103">Query results for a shared dataset can be copied to a cache to provide consistent data for multiple reports and to improve response time for the dataset query.</span></span> <span data-ttu-id="80ee9-104">보고서와 마찬가지로 공유 데이터 세트를 처음 사용할 때 또는 일정을 지정하여 공유 데이터 세트가 캐시되도록 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80ee9-104">Like reports, you can configure a shared dataset to be cached on first use or by specifying a schedule.</span></span>  
  
 <span data-ttu-id="80ee9-105">공유 데이터 세트를 여러 보고서에 포함하거나 구성 요소 정의의 일부로 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80ee9-105">A shared dataset can be included in multiple reports or as part of component definitions.</span></span> <span data-ttu-id="80ee9-106">공유 데이터 세트를 캐시하여 이를 사용하는 모든 보고서에 대해 일관성 있는 데이터 세트를 제공하고 외부 데이터 원본에 대해 데이터 세트 쿼리가 실행되는 시간을 줄일 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80ee9-106">By caching the shared dataset, you provide a consistent set of data for all reports that use it, and also reduce the number of times that the dataset query runs against the external data source.</span></span>  
  
 <span data-ttu-id="80ee9-107">다음 목록에서는 공유 데이터 세트를 캐시해야 하는 경우에 대한 예를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="80ee9-107">The following list provides examples of when to cache a shared dataset:</span></span>  
  
-   <span data-ttu-id="80ee9-108">쿼리 실행 시간이 오래 걸리는 경우</span><span class="sxs-lookup"><span data-stu-id="80ee9-108">The query takes a substantial amount of time to run.</span></span>  
  
-   <span data-ttu-id="80ee9-109">쿼리에서 매개 변수가 사용되나 대부분의 경우 매개 변수 조합 수가 적은 경우.</span><span class="sxs-lookup"><span data-stu-id="80ee9-109">The query takes parameters, but most of the time, the number of parameter combinations is small.</span></span> <span data-ttu-id="80ee9-110">각 조합은 캐시된 쿼리 결과를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="80ee9-110">Each combination creates cached query results.</span></span>  
  
-   <span data-ttu-id="80ee9-111">쿼리가 날짜, 주 또는 월의 예측 가능한 시간에 실행되는 경우</span><span class="sxs-lookup"><span data-stu-id="80ee9-111">The query runs at predictable times of the day, week, or month.</span></span>  
  
-   <span data-ttu-id="80ee9-112">쿼리가 이메일을 통해 전달되는 보고서의 공유 데이터 세트 참조의 결과로 실행되어 많은 사람이 짧은 기간 내에 링크를 클릭할 가능성이 있는 경우.</span><span class="sxs-lookup"><span data-stu-id="80ee9-112">The query runs as the result of a shared dataset reference in a report that is delivered via e-mail, where a large number of people are likely to click the link in a short span of time.</span></span>  
  
-   <span data-ttu-id="80ee9-113">다음 목록에서는 공유 데이터 세트를 캐시하지 않아야 하는 경우에 대한 예를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="80ee9-113">The following list provides examples of when not to cache a shared dataset:</span></span>  
  
-   <span data-ttu-id="80ee9-114">쿼리 결과에 항상 최신 데이터가 포함되어야 하는 경우</span><span class="sxs-lookup"><span data-stu-id="80ee9-114">The query results must always include the most recent data.</span></span>  
  
-   <span data-ttu-id="80ee9-115">쿼리가 빠르게 실행되는 경우</span><span class="sxs-lookup"><span data-stu-id="80ee9-115">The query runs quickly.</span></span>  
  
-   <span data-ttu-id="80ee9-116">쿼리가 자주 실행되지 않는 경우</span><span class="sxs-lookup"><span data-stu-id="80ee9-116">The query runs infrequently.</span></span>  
  
-   <span data-ttu-id="80ee9-117">쿼리에서 매개 변수가 사용되고 매개 변수 조합 수가 큰 경우로 어떤 조합도 다른 조합보다 많이 사용되지 않는 경우</span><span class="sxs-lookup"><span data-stu-id="80ee9-117">The query takes parameters, the number of parameter combinations is large, and no combination is more likely than another.</span></span>  
  
-   <span data-ttu-id="80ee9-118">공유 데이터 세트의 기반이 되는 데이터 원본에 프롬프트 또는 Windows 통합 자격 증명이 있는 경우.</span><span class="sxs-lookup"><span data-stu-id="80ee9-118">The data source that the shared dataset is based on has Prompt or Windows Integrated credentials.</span></span>  
  
-   <span data-ttu-id="80ee9-119">공유 데이터 세트 필터 또는 쿼리에 글로벌 컬렉션 User에 대한 참조가 있는 식이 포함되는 경우.</span><span class="sxs-lookup"><span data-stu-id="80ee9-119">The shared dataset filter or the query contains an expression with a reference to the global collection User.</span></span>  
  
 <span data-ttu-id="80ee9-120">사용자가 캐시된 결과 집합에 대해 지정된 기본값과 다른 보고서 매개 변수 값을 선택하는 경우 현재 데이터 세트 쿼리가 실행되고 해당 쿼리에 캐시된 결과 집합이 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="80ee9-120">If a user chooses report parameter values that differ from the default values that are specified for the cached result set, the dataset query runs actively and the cached results are not used for that query.</span></span>  
  
## <a name="caching-shared-datasets"></a><span data-ttu-id="80ee9-121">공유 데이터 세트 캐싱</span><span class="sxs-lookup"><span data-stu-id="80ee9-121">Caching Shared Datasets</span></span>  
 <span data-ttu-id="80ee9-122">공유 데이터 세트에 대해 캐싱을 설정하려면 공유 데이터 세트에서 캐시 옵션을 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="80ee9-122">To enable caching for a shared dataset, you must select the cache option on the shared dataset.</span></span> <span data-ttu-id="80ee9-123">캐싱을 설정한 후에는 공유 데이터 세트에 대한 쿼리 결과가 처음 쿼리 사용 시 캐시에 복사됩니다.</span><span class="sxs-lookup"><span data-stu-id="80ee9-123">After caching is enabled, the query results for a shared dataset are copied to the cache on first use.</span></span> <span data-ttu-id="80ee9-124">공유 데이터 세트에 매개 변수가 있는 경우 각 매개 변수 조합이 캐시에 새 항목을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="80ee9-124">If the shared dataset has parameters, each combination of parameters creates a new entry in the cache.</span></span>  
  
 <span data-ttu-id="80ee9-125">특정 매개 변수 조합에 대한 쿼리 결과가 캐시에 있는 동안 처리를 위해 실행되는 각 보고서에 해당 매개 변수 값이 지정되어 있는 공유 데이터 세트에 대한 참조가 포함되어 있는 경우 이 보고서는 캐시된 데이터를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="80ee9-125">While the query results for a specific parameter combination are in the cache, each report that is launched for processing and that includes a reference to the shared dataset with those parameter values will use the cached data.</span></span>  
  
 <span data-ttu-id="80ee9-126">캐시에 있는 데이터가 만료되기 전까지의 보관 기간을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80ee9-126">You can specify how long to keep data in the cache before it expires.</span></span> <span data-ttu-id="80ee9-127">자세한 내용은 [캐싱 페이지, 공유 데이터 세트&#40;보고서 관리자&#41;](../caching-page-shared-datasets-report-manager.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="80ee9-127">For more information, see [Caching Page, Shared Datasets &#40;Report Manager&#41;](../caching-page-shared-datasets-report-manager.md).</span></span>  
  
## <a name="preloading-the-cache"></a><span data-ttu-id="80ee9-128">캐시 미리 로드</span><span class="sxs-lookup"><span data-stu-id="80ee9-128">Preloading the Cache</span></span>  
 <span data-ttu-id="80ee9-129">캐시 새로 고침 계획을 만들어 캐시를 미리 로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80ee9-129">You can preload the cache by creating a cache refresh plan.</span></span> <span data-ttu-id="80ee9-130">새로 고침 계획을 만들면 항목별 일정 또는 공유 일정을 사용하여 캐시를 새로 고칠 빈도를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80ee9-130">With a refresh plan, you can specify how often to refresh the cache by using an item-specific schedule or a shared schedule.</span></span> <span data-ttu-id="80ee9-131">동일한 항목에 대해 여러 캐시 항목이 생성되는 것을 방지하려면 지정하는 일정에서 외부 데이터 원본에 대한 쿼리 처리 시간이 충분해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="80ee9-131">To avoid multiple cache entries for the same item, the schedule that you specify should allow enough time for query processing on the external data source.</span></span> <span data-ttu-id="80ee9-132">예를 들어 쿼리 실행에 20분이 걸리는 경우 새로 고침 일정은 20분보다 커야 합니다.</span><span class="sxs-lookup"><span data-stu-id="80ee9-132">For example, if the query takes 20 minutes to run, the refresh schedule should be greater than 20 minutes.</span></span> <span data-ttu-id="80ee9-133">자세한 내용은 [Schedules](../subscriptions/schedules.md)을(를) 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="80ee9-133">For more information, see [Schedules](../subscriptions/schedules.md).</span></span>  
  
 <span data-ttu-id="80ee9-134">공유 데이터 세트에 대한 캐시 새로 고침 계획을 만들려는 경우 다음 조건이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="80ee9-134">To create a cache refresh plan for a shared dataset, the following conditions apply.</span></span>  
  
-   <span data-ttu-id="80ee9-135">공유 데이터 세트에 캐싱이 설정되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="80ee9-135">The shared dataset must be enabled for caching.</span></span>  
  
-   <span data-ttu-id="80ee9-136">공유 데이터 세트가 종속되는 공유 데이터 원본에 프롬프트 또는 Windows 통합 자격 증명을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="80ee9-136">The shared data source that the shared dataset depends on cannot use Prompt or Windows Integrated credentials.</span></span>  
  
-   <span data-ttu-id="80ee9-137">공유 데이터 세트에 매개 변수가 있는 경우 읽기 전용으로 표시되지 않은 각 매개 변수에 대해 정적 기본값을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="80ee9-137">If the shared dataset has parameters, you must specify static default values for each parameter that is not marked read-only.</span></span> <span data-ttu-id="80ee9-138">읽기 전용 매개 변수는 항상 기본값을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="80ee9-138">Read-only parameters will always use the default value.</span></span> <span data-ttu-id="80ee9-139">여러 매개 변수 조합에 대해 공유 데이터 세트를 캐시하려면 각 값 조합에 대해 별도의 캐시 새로 고침 계획을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="80ee9-139">To cache a shared dataset for multiple combinations of parameters, you must create a separate cache refresh plan for each combination of values.</span></span> <span data-ttu-id="80ee9-140">매개 변수에는 다른 데이터 세트에 대한 참조가 포함될 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="80ee9-140">Parameters cannot contain references to other datasets.</span></span>  
  
-   <span data-ttu-id="80ee9-141">각 캐시 새로 고침 계획은 하나의 공유 데이터 세트나 보고서와만 연결됩니다.</span><span class="sxs-lookup"><span data-stu-id="80ee9-141">Each cache refresh plan is associated with only one shared dataset or report.</span></span>  
  
-   <span data-ttu-id="80ee9-142">공유 데이터 세트에 대해 ReadPolicy 및 UpdatePolicy 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="80ee9-142">You must have ReadPolicy and UpdatePolicy permissions on the shared dataset.</span></span>  
  
 <span data-ttu-id="80ee9-143">캐시 새로 고침 계획은 공유 데이터 세트 및 보고서에 모두 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="80ee9-143">Cache refresh plans apply to both shared datasets and reports.</span></span> <span data-ttu-id="80ee9-144">자세한 내용은 [캐시 새로 고침 옵션&#40;보고서 관리자&#41;](../cache-refresh-options-report-manager.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="80ee9-144">For more information, see [Cache Refresh Options &#40;Report Manager&#41;](../cache-refresh-options-report-manager.md).</span></span>  
  
## <a name="conditions-that-cause-cache-expiration"></a><span data-ttu-id="80ee9-145">캐시 만료 조건</span><span class="sxs-lookup"><span data-stu-id="80ee9-145">Conditions that Cause Cache Expiration</span></span>  
 <span data-ttu-id="80ee9-146">다음 조건에서는 공유 데이터 세트 캐시가 유효하지 않게 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80ee9-146">The following conditions can cause a shared dataset cache to become not valid.</span></span>  
  
-   <span data-ttu-id="80ee9-147">일정 조건이 만료되는 경우.</span><span class="sxs-lookup"><span data-stu-id="80ee9-147">A schedule condition expires.</span></span> <span data-ttu-id="80ee9-148">캐시 시간이 초과되거나 만료 시간이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="80ee9-148">The cache times out or the expiration time occurs.</span></span>  
  
-   <span data-ttu-id="80ee9-149">공유 일정이 삭제되는 경우</span><span class="sxs-lookup"><span data-stu-id="80ee9-149">A shared schedule is deleted.</span></span>  
  
-   <span data-ttu-id="80ee9-150">공유 일정이 변경되는 경우.</span><span class="sxs-lookup"><span data-stu-id="80ee9-150">Changes to a shared schedule.</span></span> <span data-ttu-id="80ee9-151">공유 일정을 일지 중지할 수 있으며 이 경우 캐시 만료 시기에도 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="80ee9-151">Shared schedules can be paused, which also affects when a cache expires.</span></span>  
  
-   <span data-ttu-id="80ee9-152">공유 데이터 세트에 대한 쿼리 정의가 변경되는 경우.</span><span class="sxs-lookup"><span data-stu-id="80ee9-152">The query definition for the shared dataset changes.</span></span>  
  
-   <span data-ttu-id="80ee9-153">공유 데이터 세트가 종속되는 공유 데이터 원본에 대한 자격 증명이 변경되는 경우.</span><span class="sxs-lookup"><span data-stu-id="80ee9-153">The credentials for the shared data source that the shared dataset depends on change.</span></span>  
  
-   <span data-ttu-id="80ee9-154">공유 데이터 세트에 대한 캐시 옵션이 변경되는 경우.</span><span class="sxs-lookup"><span data-stu-id="80ee9-154">The cache options for the shared dataset change.</span></span>  
  
-   <span data-ttu-id="80ee9-155">공유 데이터 세트의 읽기 전용 매개 변수에 대한 기본값이 변경되는 경우.</span><span class="sxs-lookup"><span data-stu-id="80ee9-155">The default values for read-only parameters for the shared dataset change.</span></span>  
  
-   <span data-ttu-id="80ee9-156">공유 데이터 세트 정의의 일부인 필터가 변경되는 경우.</span><span class="sxs-lookup"><span data-stu-id="80ee9-156">The filters that are part of the shared dataset definition change.</span></span>  
  
-   <span data-ttu-id="80ee9-157">보고서 서버에서 공유 데이터 세트가 삭제되는 경우.</span><span class="sxs-lookup"><span data-stu-id="80ee9-157">The shared dataset is deleted from the report server.</span></span> <span data-ttu-id="80ee9-158">공유 데이터 세트가 삭제되면 연결된 캐시 복사본 및 캐시 새로 고침 계획도 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="80ee9-158">When a shared dataset is deleted, associated cached copies and cache refresh plans are also deleted.</span></span>  
  
 <span data-ttu-id="80ee9-159">공유 데이터 세트에 대한 캐시 새로 고침 계획을 업데이트해도 이미 처리된 보고서에는 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="80ee9-159">Updates to cache refresh plans for shared datasets do not affect reports that are already being processed.</span></span> <span data-ttu-id="80ee9-160">캐시 새로 고침 계획을 업데이트하는 경우 나중에 해당 공유 데이터 세트를 참조하는 보고서를 실행하는 경우에만 영향이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80ee9-160">Updating a cache refresh plan affects only future launches of reports that reference the shared dataset.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80ee9-161">참고 항목</span><span class="sxs-lookup"><span data-stu-id="80ee9-161">See Also</span></span>  
 [<span data-ttu-id="80ee9-162">공유 데이터 세트 관리</span><span class="sxs-lookup"><span data-stu-id="80ee9-162">Manage Shared Datasets</span></span>](../report-data/manage-shared-datasets.md)  
  
  
