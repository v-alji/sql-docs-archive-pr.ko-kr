---
title: 병합 구독자의 파티션 정보 유효성 검사 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- merge replication data validation [SQL Server replication], partitions
- parameterized filters [SQL Server replication], validating partition information
- validating partition information
ms.assetid: c059553e-df2c-4333-ba79-e8d6e2890c34
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 3032ff13af69a0690e1f81f08f7b3fb17aae0ee1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646302"
---
# <a name="validate-partition-information-for-a-merge-subscriber"></a><span data-ttu-id="85c51-102">병합 구독자의 파티션 정보 유효성 검사</span><span class="sxs-lookup"><span data-stu-id="85c51-102">Validate Partition Information for a Merge Subscriber</span></span>
  <span data-ttu-id="85c51-103">병합 게시에 대해 매개 변수가 있는 행 필터를 정의할 때는 구독자의 로그인 이름과 같이 구독자 정보를 참조하는 기능을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="85c51-103">When you define a parameterized row filter for a merge publication, you use a function that references Subscriber information, such as the Subscriber's login name.</span></span> <span data-ttu-id="85c51-104">기본적으로 복제는 각 동기화 전과 스냅샷이 구독자에 적용될 때마다 이러한 기능에 기반하여 구독자 정보의 유효성을 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="85c51-104">By default, replication validates Subscriber information based on that function before each synchronization and whenever a snapshot is applied at the Subscriber.</span></span> <span data-ttu-id="85c51-105">유효성 검사 프로세스는 데이터가 각 구독자에 대해 올바르게 분할되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="85c51-105">The validation process ensures that data is partitioned correctly for each Subscriber.</span></span> <span data-ttu-id="85c51-106">유효성 검사 동작은 **validate_subscriber_info** 게시 속성으로 제어할 수 있으며 이 속성은 [sp_changemergepublication&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql)을 사용하거나 **게시 속성** 대화 상자의 **구독 옵션** 페이지에서 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="85c51-106">Validation behavior is controlled by the **validate_subscriber_info** publication property, which can be changed using [sp_changemergepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql) or on the **Subscription Options** page of the **Publication Properties** dialog box.</span></span> <span data-ttu-id="85c51-107">게시 속성 변경 방법은 [View and Modify Publication Properties](publish/view-and-modify-publication-properties.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="85c51-107">For more information about changing publication properties, see [View and Modify Publication Properties](publish/view-and-modify-publication-properties.md).</span></span>  
  
## <a name="how-partition-validation-works"></a><span data-ttu-id="85c51-108">파티션 유효성 검사 작동 방법</span><span class="sxs-lookup"><span data-stu-id="85c51-108">How Partition Validation Works</span></span>  
 <span data-ttu-id="85c51-109">예를 들어 **SUSER_SNAME()** 함수를 사용하여 게시를 필터링할 때 병합 에이전트는 **SUSER_SNAME()** 식에 유효한 데이터를 기준으로 초기 스냅샷을 각 구독자에 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="85c51-109">When a publication is filtered, for example, using the function **SUSER_SNAME()**, the Merge Agent applies the initial snapshot to each Subscriber based on data that is valid for the **SUSER_SNAME()** expression.</span></span>  
  
 <span data-ttu-id="85c51-110">유효성 검사를 활성화하면 구독자가 다음 동기화를 위해 게시자에 다시 연결할 때 병합 에이전트가 구독자에서 정보의 유효성을 검사하고 각 구독자의 파티션이 초기 스냅샷에서 수신한 파티션과 동일한지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="85c51-110">If validation is enabled, when the Subscriber reconnects to the Publisher for the next synchronization, the Merge Agent validates the information at the Subscriber and ensures that each Subscriber's partition is the same as the one received in the initial snapshot.</span></span> <span data-ttu-id="85c51-111">각 후속 병합 또는 스냅샷 애플리케이션의 경우에는 병합 에이전트가 각 구독자 파티션의 유효성을 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="85c51-111">For each subsequent merge or snapshot application, the Merge Agent validates each Subscriber's partition.</span></span>  
  
 <span data-ttu-id="85c51-112">필터링 식에 사용된 함수에서 반환된 값이 초기 스냅샷에 반환된 값과 다른 것을 병합 에이전트가 감지하면 병합 또는 스냅샷 애플리케이션이 실패하고 해당 구독자의 구독을 다시 초기화해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="85c51-112">If the Merge Agent detects that the function used in the filtering expression returns a different value than it did at the initial snapshot, the merge or snapshot application fails, and that Subscriber's subscription might require reinitialization.</span></span> <span data-ttu-id="85c51-113">구독자의 병합 설정을 변경할 때 문제가 발생하지 않도록 하기 위해 재초기화가 필요할 수 있지만 로그인 이름과 같은 구독자의 정보를 원래 스냅샷에서 사용된 값으로 다시 변경만 해도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="85c51-113">Reinitialization might be necessary to prevent problems that can arise if the merge settings of a Subscriber are changed, but it might be sufficient to change information at the Subscriber, such as the login name, back to the value used at the time of the original snapshot.</span></span>  
  
 <span data-ttu-id="85c51-114">병합 에이전트가 파티션의 유효성을 검사할 때 필터링 식에 사용된 함수에서 반환한 값에 대해 파티션의 유효성을 검사하는 것 외에도 에이전트는 메타데이터 정리 작업 또는 스키마 변경과 같이 스냅샷을 무효화한 변경 작업 이전에 스냅샷이 생성되었는지 여부도 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="85c51-114">When the Merge Agent validates a partition, in addition to validating the partition against the values returned by any functions used in filtering expressions, the agent also checks whether the snapshot was generated prior to changes that invalidate it, such as metadata cleanup operations or schema changes.</span></span> <span data-ttu-id="85c51-115">분할된 스냅샷이 너무 오래된 경우 병합 에이전트는 오류를 표시하고 이로 인해 현재 일반 스냅샷에 기반하여 해당 구독자에 대해 분할된 스냅샷을 다시 생성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="85c51-115">If a partitioned snapshot is too old, the Merge Agent will return an error and you must regenerate a partitioned snapshot for that Subscriber based on a current regular snapshot.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85c51-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="85c51-116">See Also</span></span>  
 <span data-ttu-id="85c51-117">[복제 관리 FAQ](administration/frequently-asked-questions-for-replication-administrators.md) </span><span class="sxs-lookup"><span data-stu-id="85c51-117">[Replication Administration FAQ](administration/frequently-asked-questions-for-replication-administrators.md) </span></span>  
 <span data-ttu-id="85c51-118">[복제 관리에 대 한 모범 사례](administration/best-practices-for-replication-administration.md) </span><span class="sxs-lookup"><span data-stu-id="85c51-118">[Best Practices for Replication Administration](administration/best-practices-for-replication-administration.md) </span></span>  
 <span data-ttu-id="85c51-119">[구독 다시 초기화](reinitialize-subscriptions.md) </span><span class="sxs-lookup"><span data-stu-id="85c51-119">[Reinitialize Subscriptions](reinitialize-subscriptions.md) </span></span>  
 [<span data-ttu-id="85c51-120">복제된 데이터의 유효성 검사</span><span class="sxs-lookup"><span data-stu-id="85c51-120">Validate Replicated Data</span></span>](validate-data-at-the-subscriber.md)  
  
  
