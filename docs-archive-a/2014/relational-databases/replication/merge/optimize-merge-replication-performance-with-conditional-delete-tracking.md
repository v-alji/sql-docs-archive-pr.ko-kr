---
title: 조건부 삭제 추적으로 병합 복제 성능 최적화 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- conditional delete tracking [SQL Server replication]
- merge replication [SQL Server replication], conditional delete tracking
- articles [SQL Server replication], conditional delete tracking
ms.assetid: 58f120a3-ea3a-4e97-93f0-0eb4e580ecf2
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 46fc189d2a2e0ebf5ea44775585a69d52783a7e3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638696"
---
# <a name="optimize-merge-replication-performance-with-conditional-delete-tracking"></a><span data-ttu-id="87866-102">조건부 삭제 추적으로 병합 복제 성능 최적화</span><span class="sxs-lookup"><span data-stu-id="87866-102">Optimize Merge Replication Performance with Conditional Delete Tracking</span></span>
    
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]  
  
 <span data-ttu-id="87866-103">병합 복제를 사용하여 하나 이상의 아티클에 대한 삭제를 복제 트리거 및 시스템 테이블에서 추적할 수 없도록 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="87866-103">With merge replication you can specify that deletes for one or more articles should not be tracked by replication triggers and system tables.</span></span> <span data-ttu-id="87866-104">아티클에 대해 이 옵션을 지정하면 게시자나 구독자에서 삭제가 추적되거나 복제되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="87866-104">If you specify this option for an article, deletes are not tracked or replicated from the Publisher or any Subscribers.</span></span> <span data-ttu-id="87866-105">이 옵션은 다양한 애플리케이션 시나리오를 지원하며 삭제를 복제할 필요가 없거나 삭제를 복제하는 것이 바람직하지 않은 상황에 대해 최적화된 성능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="87866-105">This option is available to support a number of application scenarios and to provide a performance optimization for cases in which the replication of deletes is not necessary or desirable.</span></span> <span data-ttu-id="87866-106">성능을 향상시키는 방법으로는 삭제에 대한 메타데이터를 저장하지 않는 방법, 동기화 중 삭제를 열거하지 않는 방법, 삭제가 구독자에 복제 및 적용되지 않게 하는 방법의 3가지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="87866-106">Performance is enhanced in three ways: metadata for deletes is not stored; deletes are not enumerated during synchronization; deletes are not replicated to and applied at the Subscriber.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="87866-107">다운로드 전용 아티클을 사용하려면 게시의 호환성 수준이 적어도 90RTM 이상이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="87866-107">To use download-only articles, the compatibility level of the publication must be at least 90RTM.</span></span>  
  
 <span data-ttu-id="87866-108">옵션은 게시 생성 시 지정할 수 있으며 애플리케이션에서 일부 삭제 내용은 복제하고 나머지 삭제 내용은 복제하지 않아야 하는 경우(예: 일괄 삭제) 옵션을 설정 또는 해제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="87866-108">The option can be specified when a publication is created or it can be toggled on and off if an application requires that some deletes be replicated and that others not be replicated, such as batch deletes.</span></span> <span data-ttu-id="87866-109">다음 예에서는 애플리케이션에서 이 옵션을 사용하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="87866-109">The following examples illustrate ways in which this option might be used in an application:</span></span>  
  
-   <span data-ttu-id="87866-110">이동이 잦은 영업 사원이 사용하는 애플리케이션에는 일반적으로 **SalesOrderHeader**, **SalesOrderDetail** 및 **Product**와 같은 테이블이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="87866-110">An application for a mobile sales force typically has tables such as **SalesOrderHeader**, **SalesOrderDetail** and **Product**.</span></span> <span data-ttu-id="87866-111">구독자에서 입력한 주문은 게시자로 복제되고 게시자에서는 이 데이터를 주문 수행 시스템에 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="87866-111">Orders are entered at the Subscriber and then replicated to the Publisher, which often supplies data to an order fulfillment system.</span></span> <span data-ttu-id="87866-112">이동이 잦은 영업 사원 중 많은 수가 스토리지가 제한된 핸드헬드 디바이스를 사용하므로 게시자에서 주문을 받으면 해당 주문을 구독자에서 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="87866-112">Many mobile workers use handheld devices which have limited storage: after the order is received at the Publisher, it can be deleted at the Subscriber.</span></span> <span data-ttu-id="87866-113">해당 주문은 시스템 내에서 계속 활성 상태이므로 삭제가 게시자에 전파되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="87866-113">The delete is not propagated to the Publisher, because the order is still active in the system.</span></span>  
  
     <span data-ttu-id="87866-114">이 시나리오에서 **SalesOrderHeader** 및 **SalesOrderDetail** 테이블에 대해 삭제를 추적할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="87866-114">In this scenario, deletes would not be tracked for the **SalesOrderHeader** and **SalesOrderDetail** tables.</span></span> <span data-ttu-id="87866-115">제품이 게시자에서 삭제되면 제품 목록을 최신 내용으로 유지할 수 있게 삭제 내용을 구독자로 보내야 하므로 **Product** 테이블에 대한 삭제는 추적할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="87866-115">Deletes would be tracked for the **Product** table, because if a product is deleted at the Publisher, the delete should be sent to the Subscriber to keep the product list up to date.</span></span>  
  
-   <span data-ttu-id="87866-116">애플리케이션에서는 1년을 초과하는 레코드를 주기적으로 제거하는 **TransactionHistory**와 같은 테이블에 기록 데이터를 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="87866-116">An application could store historical data in a table such as **TransactionHistory**, which is periodically purged of records older than a year.</span></span> <span data-ttu-id="87866-117">이 테이블을 구독자가 현재 달의 트랜잭션에 있는 데이터만 받도록 필터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="87866-117">The table could be filtered such that Subscribers only receive data on transactions within the current month.</span></span> <span data-ttu-id="87866-118">이전 데이터를 제거하는 게시자에서 매월 수행하는 일괄 삭제는 구독자와 아무 관련이 없지만 기본적으로 이 삭제를 계속 추적하고 열거합니다.</span><span class="sxs-lookup"><span data-stu-id="87866-118">Monthly batch deletes at the Publisher that purge older data are not relevant to Subscribers, but they would still be tracked and enumerated by default.</span></span>  
  
     <span data-ttu-id="87866-119">이 시나리오에서는 일괄 처리가 발생하기 전에 시스템에서 작업을 중지할 수 있으며 애플리케이션에서 삭제 추적을 해제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="87866-119">In this scenario, before the batch processing occurred, activity could be stopped on the system, and the application could disable the tracking of deletes.</span></span> <span data-ttu-id="87866-120">처리가 완료되면 추적을 다시 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="87866-120">After the processing has finished, tracking could again be enabled.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="87866-121">게시자에서 다른 작업이 계속되는 경우 삭제 추적이 해제되어 있는 동안은 구독자로 전파되어야 하는 삭제가 발생하지 않도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="87866-121">If other activity continues at the Publisher, you must ensure that deletes that should be propagated to Subscribers do not occur while delete tracking is disabled.</span></span>  
  
 <span data-ttu-id="87866-122">**삭제가 추적되지 않게 지정하려면**</span><span class="sxs-lookup"><span data-stu-id="87866-122">**To specify that deletes should not be tracked**</span></span>  
  
-   <span data-ttu-id="87866-123">복제 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 프로그래밍: [병합 아티클에 대해 삭제가 추적되지 않도록 지정&#40;복제 Transact-SQL 프로그래밍&#41;](..//publish/specify-merge-replication-properties.md#tracking-deletes)</span><span class="sxs-lookup"><span data-stu-id="87866-123">Replication [!INCLUDE[tsql](../../../includes/tsql-md.md)] programming: [Specify That Deletes Should Not Be Tracked For Merge Articles &#40;Replication Transact-SQL Programming&#41;](..//publish/specify-merge-replication-properties.md#tracking-deletes)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87866-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="87866-124">See Also</span></span>  
 <span data-ttu-id="87866-125">[병합 복제에 대 한 아티클 옵션](article-options-for-merge-replication.md) </span><span class="sxs-lookup"><span data-stu-id="87866-125">[Article Options for Merge Replication](article-options-for-merge-replication.md) </span></span>  
 [<span data-ttu-id="87866-126">다운로드 전용 아티클로 병합 복제 성능 최적화</span><span class="sxs-lookup"><span data-stu-id="87866-126">Optimize Merge Replication Performance with Download-Only Articles</span></span>](optimize-merge-replication-performance-with-download-only-articles.md)  
  
  
