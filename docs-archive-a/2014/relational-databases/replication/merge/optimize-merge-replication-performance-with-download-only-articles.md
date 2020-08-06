---
title: 다운로드 전용 아티클로 병합 복제 성능 최적화 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- merge replication [SQL Server replication], download-only articles
- articles [SQL Server replication], download-only
- download-only articles
ms.assetid: 8851faa6-e6df-4ea5-a6ea-2a3471680fa3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8414174971792f8a2c256cd564dd1ea224527463
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638693"
---
# <a name="optimize-merge-replication-performance-with-download-only-articles"></a><span data-ttu-id="b3a65-102">다운로드 전용 아티클로 병합 복제 성능 최적화</span><span class="sxs-lookup"><span data-stu-id="b3a65-102">Optimize Merge Replication Performance with Download-Only Articles</span></span>
  <span data-ttu-id="b3a65-103">병합 복제에서는 다양한 애플리케이션의 요구 사항을 해결할 수 있도록 두 가지 아티클 유형을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="b3a65-103">Merge replication offers two different article types to address different application needs.</span></span> <span data-ttu-id="b3a65-104">게시에는 이러한 아티클 유형 중 해당 애플리케이션에 적합한 하나 이상의 아티클 유형이 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b3a65-104">Publications can contain one or more of each of these article types as appropriate for the application:</span></span>  
  
-   <span data-ttu-id="b3a65-105">표준 아티클</span><span class="sxs-lookup"><span data-stu-id="b3a65-105">Standard articles</span></span>  
  
-   <span data-ttu-id="b3a65-106">다운로드 전용 아티클</span><span class="sxs-lookup"><span data-stu-id="b3a65-106">Download-only articles</span></span>  
  
 <span data-ttu-id="b3a65-107">적절한 상황에서 다운로드 전용 아티클을 사용하면 표준 아티클과 비교하여 성능상의 이점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b3a65-107">Download-only articles provide performance advantages over standard articles and should be used where appropriate.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b3a65-108">다운로드 전용 아티클을 사용하려면 게시의 호환성 수준이 적어도 90RTM 이상이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3a65-108">To use download-only articles, the compatibility level of the publication must be at least 90RTM.</span></span>  
  
## <a name="standard-articles"></a><span data-ttu-id="b3a65-109">표준 아티클</span><span class="sxs-lookup"><span data-stu-id="b3a65-109">Standard Articles</span></span>  
 <span data-ttu-id="b3a65-110">기본값인 표준 아티클은 뛰어난 충돌 감지 및 해결 기능을 비롯하여 병합 복제의 모든 기능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="b3a65-110">Standard articles are the default, offering the full range of merge replication features, including rich conflict detection and resolution.</span></span> <span data-ttu-id="b3a65-111">표준 아티클은 여러 구독자가 업데이트하는 테이블에 적합하며 저장 프로시저 및 뷰와 같은 테이블 이외의 개체는 항상 표준 아티클로 게시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b3a65-111">Standard articles are appropriate for tables that are updated by multiple Subscribers; objects other than tables, such as stored procedures and views, are always published as standard articles.</span></span>  
  
## <a name="download-only-articles"></a><span data-ttu-id="b3a65-112">다운로드 전용 아티클</span><span class="sxs-lookup"><span data-stu-id="b3a65-112">Download-Only Articles</span></span>  
 <span data-ttu-id="b3a65-113">다운로드 전용 아티클은 제품 카탈로그에 포함된 아티클 집합처럼 구독자에서 업데이트되지 않는 데이터가 있는 애플리케이션에 적합하게 디자인되었습니다.</span><span class="sxs-lookup"><span data-stu-id="b3a65-113">Download-only articles are designed for applications with data that is not updated at Subscribers, such as a set of articles that are contained in a product catalog.</span></span> <span data-ttu-id="b3a65-114">일반적으로 제품 카탈로그는 게시자에서는 업데이트되지만 구독자에서는 업데이트되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b3a65-114">A product catalog is typically updated at the Publisher, but not at the Subscribers.</span></span> <span data-ttu-id="b3a65-115">다운로드 전용 아티클은 구독자에서 업데이트할 수 없으므로 추적 메타데이터가 구독자로 전송되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b3a65-115">Because download-only articles cannot be updated at the Subscriber, tracking metadata is not sent to Subscribers.</span></span> <span data-ttu-id="b3a65-116">이로 인해 구독자의 스토리지 용량 및 성능상 이점이 줄어들 수 있으며 특히 네트워크 연결 속도가 느릴 경우 더욱 그렇습니다.</span><span class="sxs-lookup"><span data-stu-id="b3a65-116">This can lead to reduced storage on the Subscribers and a performance benefit, especially if the network connection is slow.</span></span>  
  
 <span data-ttu-id="b3a65-117">다운로드 전용 아티클은 클라이언트 구독과 함께 작동합니다. 아티클을 다운로드 전용으로 지정할 경우 해당 아티클에 대한 행은 클라이언트 구독을 사용하는 구독자에 삽입, 업데이트 또는 삭제할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b3a65-117">Download-only articles work in conjunction with client subscriptions: if an article is designated as download-only, rows for that article cannot be inserted, updated, or deleted at Subscribers who use client subscriptions.</span></span> <span data-ttu-id="b3a65-118">서버 구독 유형을 사용하는 게시자와 구독자(일반적으로 데이터를 다른 구독자로 다시 게시하는 구독자)는 데이터를 삽입, 업데이트 및 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b3a65-118">Publishers and Subscribers that use the server subscription type (typically Subscribers that republish data to other Subscribers) can insert, update, and delete data.</span></span> <span data-ttu-id="b3a65-119">클라이언트 구독에 대한 자세한 내용은 [게시 구독](../subscribe-to-publications.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b3a65-119">For more information about client subscriptions, see [Subscribe to Publications](../subscribe-to-publications.md).</span></span>  
  
 <span data-ttu-id="b3a65-120">아티클을 다운로드 전용으로 지정하려면 [새 병합 테이블 아티클을 다운로드 전용으로 지정](../publish/specify-merge-replication-properties.md#download-only)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="b3a65-120">To specify that an article is download-only, see [Specify That a Merge Table Article is Download-Only](../publish/specify-merge-replication-properties.md#download-only).</span></span>  
  
## <a name="using-different-article-types-in-your-applications"></a><span data-ttu-id="b3a65-121">애플리케이션에서 다른 아티클 유형 사용</span><span class="sxs-lookup"><span data-stu-id="b3a65-121">Using Different Article Types in Your Applications</span></span>  
 <span data-ttu-id="b3a65-122">애플리케이션의 요구 사항을 이해하면 최대 유연성과 최적 성능 간 균형을 유지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b3a65-122">By understanding the requirements of your application, you can make tradeoffs between maximum flexibility and optimal performance.</span></span> <span data-ttu-id="b3a65-123">예를 들어 게시자와 구독자에서 충돌이 자주 발생하고 내용이 자주 변경되는 애플리케이션의 경우 표준 아티클로 구성된 애플리케이션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b3a65-123">For example, applications with numerous conflicts and changes at both the Publisher and Subscribers will use a publication made up of standard articles.</span></span> <span data-ttu-id="b3a65-124">SFA(Sales Force Automation) 애플리케이션과 같은 일부 애플리케이션에는 충돌 가능성이 있는 아티클과 다운로드 전용으로 지정할 수 있는 조회 테이블의 기능을 하는 다른 아티클이 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b3a65-124">Some applications, such as a sales force automation application, might have articles with a potential for conflicts, and other articles that function as lookup tables, which can be specified as download-only.</span></span> <span data-ttu-id="b3a65-125">POS(Point of Sale) 시스템 및 FFA(Field Force Automation) 애플리케이션과 같은 데이터 항목 애플리케이션은 충돌을 제거하고 한 구독자의 데이터가 다른 구독자로 이동하지 않는 방식으로 데이터를 엄격하게 분할하는 경우가 많습니다.</span><span class="sxs-lookup"><span data-stu-id="b3a65-125">Data entry applications, such as point of sales systems and field force automation applications, often strictly partition data in a way that conflicts are eliminated, and data from one Subscriber never goes to another.</span></span> <span data-ttu-id="b3a65-126">이러한 경우 겹치지 않는 파티션, 다운로드 전용 아티클 및 사전 계산 파티션을 잘 조합하여 성능과 확장성을 최적화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b3a65-126">In these situations, a combination of nonoverlapping partitions, download-only articles and precomputed partitions provides maximum performance and scalability.</span></span> <span data-ttu-id="b3a65-127">겹치지 않는 파티션 및 사전 계산 파티션에 대한 자세한 내용은 [매개 변수가있는 행 필터](parameterized-filters-parameterized-row-filters.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="b3a65-127">For more information about nonoverlapping partitions and precomputed partitions, see [Parameterized Row Filters](parameterized-filters-parameterized-row-filters.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3a65-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b3a65-128">See Also</span></span>  
 <span data-ttu-id="b3a65-129">[병합 복제에 대 한 아티클 옵션](article-options-for-merge-replication.md) </span><span class="sxs-lookup"><span data-stu-id="b3a65-129">[Article Options for Merge Replication](article-options-for-merge-replication.md) </span></span>  
 [<span data-ttu-id="b3a65-130">조건부 삭제 추적으로 병합 복제 성능 최적화</span><span class="sxs-lookup"><span data-stu-id="b3a65-130">Optimize Merge Replication Performance with Conditional Delete Tracking</span></span>](optimize-merge-replication-performance-with-conditional-delete-tracking.md)  
  
  
