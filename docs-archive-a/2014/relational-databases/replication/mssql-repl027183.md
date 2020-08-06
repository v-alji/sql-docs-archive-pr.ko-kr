---
title: MSSQL_REPL027183 | Microsoft 문서
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_REPL027183 error
ms.assetid: 52c271ac-1a0e-43d5-85d4-35886d1efd32
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 4484318cd6ec6ff4f0b201be69dc9b7544dd2c2f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741795"
---
# <a name="mssql_repl027183"></a><span data-ttu-id="16306-102">MSSQL_REPL027183</span><span class="sxs-lookup"><span data-stu-id="16306-102">MSSQL_REPL027183</span></span>
    
## <a name="message-details"></a><span data-ttu-id="16306-103">메시지 정보</span><span class="sxs-lookup"><span data-stu-id="16306-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="16306-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="16306-104">Product Name</span></span>|<span data-ttu-id="16306-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="16306-105">SQL Server</span></span>|  
|<span data-ttu-id="16306-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="16306-106">Event ID</span></span>|<span data-ttu-id="16306-107">27183</span><span class="sxs-lookup"><span data-stu-id="16306-107">27183</span></span>|  
|<span data-ttu-id="16306-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="16306-108">Event Source</span></span>|<span data-ttu-id="16306-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="16306-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="16306-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="16306-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="16306-111">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="16306-111">Symbolic Name</span></span>||  
|<span data-ttu-id="16306-112">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="16306-112">Message Text</span></span>|<span data-ttu-id="16306-113">병합 프로세스에서 매개 변수가 있는 행 필터를 사용하여 아티클의 변경 내용을 열거하지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="16306-113">The merge process failed to enumerate changes in articles with parameterized row filters.</span></span> <span data-ttu-id="16306-114">이 오류가 계속되면 이 프로세스에 대한 쿼리 제한 시간을 늘리고 게시 보존 기간을 줄인 다음 게시된 테이블의 인덱스를 향상시키십시오.</span><span class="sxs-lookup"><span data-stu-id="16306-114">If this failure continues, increase the query timeout for this process, reduce the retention period for the publication, and improve indexes on published tables.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="16306-115">설명</span><span class="sxs-lookup"><span data-stu-id="16306-115">Explanation</span></span>  
 <span data-ttu-id="16306-116">이 오류는 필터링된 게시에서 변경 내용을 처리하는 동안 병합 에이전트 제한 시간에 도달한 경우 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="16306-116">This error is raised if a Merge Agent timeout occurs while processing changes in a filtered publication.</span></span> <span data-ttu-id="16306-117">다음 문제 중 하나로 인해 제한 시간에 도달했을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="16306-117">The timeout might be caused by one of the following issues:</span></span>  
  
-   <span data-ttu-id="16306-118">사전 계산 파티션 최적화를 사용하지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="16306-118">Not using the precomputed partitions optimization.</span></span>  
  
-   <span data-ttu-id="16306-119">열의 인덱스 조각화가 필터링에 사용되었습니다.</span><span class="sxs-lookup"><span data-stu-id="16306-119">Index fragmentation on columns used for filtering.</span></span>  
  
-   <span data-ttu-id="16306-120">**MSmerge_tombstone**, **MSmerge_contents**, **MSmerge_genhistory**와 같은 큰 병합 메타데이터 테이블이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="16306-120">Large merge metadata tables, such as **MSmerge_tombstone**, **MSmerge_contents**, and **MSmerge_genhistory**.</span></span>  
  
-   <span data-ttu-id="16306-121">필터링된 테이블이 고유 키에 조인되어 있지 않고 많은 테이블이 조인 필터와 관련되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="16306-121">Filtered tables that are not joined on a unique key and join filters that involve a large number of tables.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="16306-122">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="16306-122">User Action</span></span>  
 <span data-ttu-id="16306-123">이 문제를 해결하려면</span><span class="sxs-lookup"><span data-stu-id="16306-123">To resolve the issue:</span></span>  
  
-   <span data-ttu-id="16306-124">오류를 일으킨 기본 문제를 해결하는 동안 병합 에이전트에서 계속 처리 작업을 수행하려면 **-QueryTimeOut** 매개 변수의 값을 늘립니다.</span><span class="sxs-lookup"><span data-stu-id="16306-124">Increase the value of the **-QueryTimeOut** parameter for the Merge Agent to allow processing to continue while you address the underlying issues causing the error.</span></span> <span data-ttu-id="16306-125">에이전트 프로필 및 명령줄에서 에이전트 매개 변수를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="16306-125">Agent parameters can be specified in agent profiles and on the command line.</span></span> <span data-ttu-id="16306-126">자세한 내용은 다음을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="16306-126">For more information, see:</span></span>  
  
    -   [<span data-ttu-id="16306-127">복제 에이전트 프로필 작업</span><span class="sxs-lookup"><span data-stu-id="16306-127">Work with Replication Agent Profiles</span></span>](agents/replication-agent-profiles.md)  
  
    -   [<span data-ttu-id="16306-128">복제 에이전트의 명령 프롬프트 매개 변수 보기 및 수정&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="16306-128">View and Modify Replication Agent Command Prompt Parameters &#40;SQL Server Management Studio&#41;</span></span>](agents/view-and-modify-replication-agent-command-prompt-parameters.md)  
  
    -   <span data-ttu-id="16306-129">[Replication Agent Executables Concepts](concepts/replication-agent-executables-concepts.md)에 할당될 최소 및 최대 메모리 양을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="16306-129">[Replication Agent Executables Concepts](concepts/replication-agent-executables-concepts.md).</span></span>  
  
-   <span data-ttu-id="16306-130">사전 계산 파티션 최적화를 사용합니다(가능한 경우).</span><span class="sxs-lookup"><span data-stu-id="16306-130">Use the precomputed partitions optimization if possible.</span></span> <span data-ttu-id="16306-131">많은 게시 요구 사항이 충족되면 이 최적화가 기본적으로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="16306-131">This optimization is used by default if a number of publication requirements are met.</span></span> <span data-ttu-id="16306-132">이러한 요구 사항에 대한 자세한 내용은 [사전 계산 파티션으로 매개 변수가 있는 필터 성능 최적화](merge/parameterized-filters-optimize-for-precomputed-partitions.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="16306-132">For more information about these requirements, see [Optimize Parameterized Filter Performance with Precomputed Partitions](merge/parameterized-filters-optimize-for-precomputed-partitions.md).</span></span> <span data-ttu-id="16306-133">게시가 이러한 요구 사항을 충족하지 않는 경우 게시를 다시 디자인하십시오.</span><span class="sxs-lookup"><span data-stu-id="16306-133">If the publication does not meet these requirements, consider redesigning the publication.</span></span>  
  
-   <span data-ttu-id="16306-134">복제는 보존 기간에 도달할 때까지 게시 및 구독 데이터베이스의 메타데이터를 정리할 수 없으므로 게시 보존 기간에 대해 가능한 가장 낮은 설정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="16306-134">Specify the lowest setting possible for the publication retention period, because replication cannot clean up metadata in the publication and subscription databases until the retention period is reached.</span></span> <span data-ttu-id="16306-135">자세한 내용은 [Subscription Expiration and Deactivation](subscription-expiration-and-deactivation.md)을(를) 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="16306-135">For more information, see [Subscription Expiration and Deactivation](subscription-expiration-and-deactivation.md).</span></span>  
  
-   <span data-ttu-id="16306-136">병합 복제 유지 관리의 한 부분으로 병합 복제와 연결된 **MSmerge_contents**, **MSmerge_genhistory**및 **MSmerge_tombstone**, **MSmerge_current_partition_mappings**및 **MSmerge_past_partition_mappings**시스템 테이블의 증가를 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="16306-136">As part of maintenance for merge replication, occasionally check the growth of the system tables associated with merge replication: **MSmerge_contents**, **MSmerge_genhistory**, and **MSmerge_tombstone**, **MSmerge_current_partition_mappings**, and **MSmerge_past_partition_mappings**.</span></span> <span data-ttu-id="16306-137">이러한 테이블의 인덱스를 주기적으로 다시 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="16306-137">Periodically re-index these tables.</span></span> <span data-ttu-id="16306-138">자세한 내용은 [인덱스 다시 구성 및 다시 작성](../indexes/indexes.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="16306-138">For more information, see [Reorganize and Rebuild Indexes](../indexes/indexes.md).</span></span>  
  
-   <span data-ttu-id="16306-139">필터링에 사용된 열이 올바로 인덱싱되는지 확인하고 이러한 인덱스를 다시 작성합니다(필요한 경우).</span><span class="sxs-lookup"><span data-stu-id="16306-139">Ensure that columns used for filtering are properly indexed and rebuild such indexes if necessary.</span></span> <span data-ttu-id="16306-140">자세한 내용은 [인덱스 다시 구성 및 다시 작성](../indexes/indexes.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="16306-140">For more information, see [Reorganize and Rebuild Indexes](../indexes/indexes.md).</span></span>  
  
-   <span data-ttu-id="16306-141">고유 열을 기반으로 하는 조인 필터에 대해 **join_unique_key** 속성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="16306-141">Set the **join_unique_key** property for join filters that are based on unique columns.</span></span> <span data-ttu-id="16306-142">자세한 내용은 [Join Filters](merge/join-filters.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="16306-142">For more information, see [Join Filters](merge/join-filters.md).</span></span>  
  
-   <span data-ttu-id="16306-143">조인 필터 계층에서 테이블의 수를 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="16306-143">Limit the number of tables in the join filter hierarchy.</span></span> <span data-ttu-id="16306-144">5개 이상의 테이블을 가진 조인 필터를 생성하는 경우 다른 해결책을 고려하는 것이 좋습니다. 크기가 작거나, 변경될 가능성이 없거나, 기본적으로 조회 테이블에 해당하는 테이블은 필터링하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="16306-144">If you are generating join filters of five or more tables, consider other solutions: do not filter tables that are small, not subject to change, or are primarily lookup tables.</span></span> <span data-ttu-id="16306-145">구독 간에 분할해야 하는 테이블 사이에서만 조인 필터를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="16306-145">Use join filters only between tables that must be partitioned among subscriptions.</span></span>  
  
-   <span data-ttu-id="16306-146">동기화 사이에 있는 필터링된 테이블에 대한 변경 횟수를 줄이거나 병합 에이전트를 더 자주 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="16306-146">Make a smaller number of changes on filtered tables between synchronizations, or run the Merge Agent more frequently.</span></span> <span data-ttu-id="16306-147">동기화 일정 설정 방법은 [Specify Synchronization Schedules](specify-synchronization-schedules.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="16306-147">For more information about setting synchronization schedules, see [Specify Synchronization Schedules](specify-synchronization-schedules.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16306-148">참고 항목</span><span class="sxs-lookup"><span data-stu-id="16306-148">See Also</span></span>  
 [<span data-ttu-id="16306-149">오류 및 이벤트 참조&#40;복제&#41;</span><span class="sxs-lookup"><span data-stu-id="16306-149">Errors and Events Reference &#40;Replication&#41;</span></span>](errors-and-events-reference-replication.md)  
  
  
