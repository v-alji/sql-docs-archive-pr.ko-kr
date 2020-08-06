---
title: 해결 프로그램 선택 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- default conflict resolver
- articles [SQL Server replication], conflict resolution
- conflict resolution [SQL Server replication], merge replication
ms.assetid: b7dec3fa-d9d9-409d-b946-f9b9a3202829
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0db289e923cab72bf175b172f039ea228c991110
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647624"
---
# <a name="choose-a-resolver"></a><span data-ttu-id="2ec20-102">해결 프로그램 선택</span><span class="sxs-lookup"><span data-stu-id="2ec20-102">Choose a Resolver</span></span>
  <span data-ttu-id="2ec20-103">해결 프로그램을 선택할 때는 애플리케이션에서 충돌 해결의 중요성을 고려하고 우선 순위를 기반으로 하는 기본 충돌 해결 프로그램을 사용할 수 있는지 또는 아티클 해결 프로그램을 사용해야 하는지 여부를 고려해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2ec20-103">When choosing a resolver, consider the importance of conflict resolution in your application and whether you can use the default priority-based conflict resolver or need to use an article resolver.</span></span>  
  
 <span data-ttu-id="2ec20-104">같은 파티션에 기록하는 여러 사용자가 없는 상황에서 데이터가 분할되고 복제 토폴로지가 상대적으로 간단한 경우에는(단일 게시자 및 소수의 구독자) 충돌이 드물게 발생하거나 아예 발생하지 않을 것입니다.</span><span class="sxs-lookup"><span data-stu-id="2ec20-104">If your data is partitioned without multiple users writing to the same partitions, and your replication topology is relatively basic (one Publisher and a few Subscribers), conflicts should be rare or nonexistent.</span></span> <span data-ttu-id="2ec20-105">이러한 환경에서는 복잡한 충돌 해결 전략이 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2ec20-105">In these environments, you probably do not need a complex conflict resolution strategy.</span></span> <span data-ttu-id="2ec20-106">따라서 충돌 해결에 기본 설정을 사용하는 전략과 클라이언트 구독자 및 최초 변경 내용을 적용하는 정책을 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="2ec20-106">A strategy using the default settings for conflict resolution, using client subscriptions and a first change in wins policy, is recommended.</span></span> <span data-ttu-id="2ec20-107">토폴로지가 재게시 구독자를 사용하는 경우와 같이 복잡한 경우에는 서버 구독에 우선 순위를 지정하는 것이 더 적합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2ec20-107">If the topology is more complex (using republishing Subscribers, for example), server subscriptions with specific priorities might be more appropriate.</span></span>  
  
 <span data-ttu-id="2ec20-108">비즈니스에 기본 해결 프로그램에서 제공하는 것 보다 더 세밀하게 조정된 솔루션이 필요한 경우에는 아티클 해결 프로그램을 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="2ec20-108">An article resolver is recommended if your business needs require a more finely tuned solution than is available with the default resolver.</span></span> <span data-ttu-id="2ec20-109">아티클 해결 프로그램을 사용할 때는 비즈니스 논리 처리기를 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="2ec20-109">If you choose to use an article resolver, it is recommended that you use a business logic handler.</span></span> <span data-ttu-id="2ec20-110">자세한 내용은 [병합 동기화 중 비즈니스 논리 실행](execute-business-logic-during-merge-synchronization.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2ec20-110">For more information, see [Execute Business Logic During Merge Synchronization](execute-business-logic-during-merge-synchronization.md).</span></span>  
  
 <span data-ttu-id="2ec20-111">따라서 기본 해결 프로그램을 사용할지 또는 아티클 해결 프로그램을 사용할지 여부는 데이터와 애플리케이션의 비즈니스 논리 필요 사항을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="2ec20-111">Ultimately, choosing whether to use the default resolver or an article resolver should be based on the data and the business logic needs of the application.</span></span> <span data-ttu-id="2ec20-112">예를 들어 다양한 작업 범주(지점장, 라인 관리자 및 판매 담당자)에 걸쳐 있는 여러 직원이 서로 다른 구독자에 있는 분할되지 않은 테이블 집합에 고객 순위 데이터를 입력하고 작업 범주에 의해 데이터의 우선 순위가 결정되는 경우를 고려해 봅시다.</span><span class="sxs-lookup"><span data-stu-id="2ec20-112">For example, consider employees who enter customer ranking data into a set of non-partitioned tables at different Subscribers; the employees span various job categories (branch managers, line managers, sales staff), and job category determines whose data should be given priority.</span></span> <span data-ttu-id="2ec20-113">이 경우 충돌 발생 시 변경 내용을 적용할 항목을 결정하는 데 아티클의 작업 범주 데이터를 사용하는 아티클 해결 프로그램을 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2ec20-113">In this case, an article resolver can be built that uses job category data from the article to determine the winner if a conflict occurs.</span></span>  
  
 <span data-ttu-id="2ec20-114">충돌이 자주 발생할 것으로 예측되면 충돌 해결 전략을 구현할 때 다음과 같은 매우 중요한 사항을 고려하십시오.</span><span class="sxs-lookup"><span data-stu-id="2ec20-114">If conflicts are likely to occur with some frequency, here are the most important decisions you should consider when implementing a conflict resolution strategy.</span></span>  
  
|<span data-ttu-id="2ec20-115">충돌 해결 문제</span><span class="sxs-lookup"><span data-stu-id="2ec20-115">Conflict resolution issue</span></span>|<span data-ttu-id="2ec20-116">권장</span><span class="sxs-lookup"><span data-stu-id="2ec20-116">Recommendation</span></span>|  
|-------------------------------|--------------------|  
|<span data-ttu-id="2ec20-117">서로 다른 사용자 범주에 다른 우선 순위 값이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="2ec20-117">Different categories of users require different priority values.</span></span>|<span data-ttu-id="2ec20-118">기본 해결 프로그램을 사용하고 다른 우선 순위 값을 가진 서버 구독을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2ec20-118">Use the default resolver and create server subscriptions with different priority values.</span></span><br /><br /> <span data-ttu-id="2ec20-119">-또는-</span><span class="sxs-lookup"><span data-stu-id="2ec20-119">-Or-</span></span><br /><br /> <span data-ttu-id="2ec20-120">아티클의 권한 값 열을 인식하여 충돌 해결을 돕는 아티클 해결 프로그램을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="2ec20-120">Use an article resolver that recognizes an authority value column in the article to help resolve a conflict.</span></span>|  
|<span data-ttu-id="2ec20-121">최초 변경 내용을 적용하는 충돌 솔루션이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="2ec20-121">First change in wins conflict solution wanted.</span></span>|<span data-ttu-id="2ec20-122">기본 해결 프로그램을 사용하고 클라이언트 구독을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2ec20-122">Use the default resolver and create client subscriptions.</span></span>|  
|<span data-ttu-id="2ec20-123">같은 열에 충돌하는 변경 내용을 적용하지 않는 한 여러 사용자가 같은 데이터 행을 변경할 수 있도록 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="2ec20-123">Multiple users changing the same data row is acceptable, as long as no conflicting changes are made to the same column.</span></span>|<span data-ttu-id="2ec20-124">기본 해결 프로그램 또는 열 수준 추적을 설정한 아티클 해결 프로그램을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="2ec20-124">Use either the default resolver or an article resolver with column-level tracking enabled.</span></span>|  
|<span data-ttu-id="2ec20-125">행 값의 여러 변경 내용을 충돌로 플래그 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2ec20-125">Flag multiple changes to any value in a row as a conflict.</span></span>|<span data-ttu-id="2ec20-126">기본 해결 프로그램 또는 행 수준 추적을 설정한 아티클 해결 프로그램을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="2ec20-126">Use either the default resolver or an article resolver with row-level tracking.</span></span>|  
|<span data-ttu-id="2ec20-127">논리적 레코드 값의 여러 변경 내용을 충돌로 플래그 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2ec20-127">Flag multiple changes to any value in a logical record as a conflict.</span></span>|<span data-ttu-id="2ec20-128">논리적 레코드 수준 추적을 설정한 기본 해결 프로그램을 사용합니다. 논리적 레코드 기능은 사용자 지정 해결 프로그램 또는 비즈니스 논리 처리기를 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2ec20-128">Use the default resolver with logical record-level tracking (the logical records feature does not support custom resolvers or business logic handlers).</span></span>|  
|<span data-ttu-id="2ec20-129">충돌 결과 데이터가 원본 충돌 데이터와 달라야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2ec20-129">Conflict outcome data needs to be different from original conflict data.</span></span>|<span data-ttu-id="2ec20-130">새 값을 계산하는 아티클 해결 프로그램을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="2ec20-130">Use an article resolver that calculates new values.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2ec20-131">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2ec20-131">See Also</span></span>  
 <span data-ttu-id="2ec20-132">[Detecting and Resolving Conflicts in Logical Records](advanced-merge-replication-conflict-resolving-in-logical-record.md) </span><span class="sxs-lookup"><span data-stu-id="2ec20-132">[Detecting and Resolving Conflicts in Logical Records](advanced-merge-replication-conflict-resolving-in-logical-record.md) </span></span>  
 <span data-ttu-id="2ec20-133">[Advanced Merge Replication Conflict Detection and Resolution](advanced-merge-replication-conflict-detection-and-resolution.md) </span><span class="sxs-lookup"><span data-stu-id="2ec20-133">[Advanced Merge Replication Conflict Detection and Resolution](advanced-merge-replication-conflict-detection-and-resolution.md) </span></span>  
 [<span data-ttu-id="2ec20-134">데이터 다시 게시</span><span class="sxs-lookup"><span data-stu-id="2ec20-134">Republish Data</span></span>](../republish-data.md)  
  
  
