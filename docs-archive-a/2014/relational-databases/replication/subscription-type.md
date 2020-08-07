---
title: 구독 유형 | Microsoft 문서
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newsubwizard.subscriptiontype.f1
ms.assetid: 9a50f588-ee45-4a87-826f-372ff0798587
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 614ff910b13706485ee9466c884243ff1c9027ea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731507"
---
# <a name="subscription-type"></a><span data-ttu-id="d9e21-102">구독 유형</span><span class="sxs-lookup"><span data-stu-id="d9e21-102">Subscription Type</span></span>
  <span data-ttu-id="d9e21-103">병합 복제는 서버와 클라이언트라는 구독 유형을 제공합니다. 이전 버전의 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서는 각각 전역 및 로컬이라고 불렀습니다.</span><span class="sxs-lookup"><span data-stu-id="d9e21-103">Merge replication offers two subscription types: server and client (referred to in previous versions of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] as global and local, respectively).</span></span> <span data-ttu-id="d9e21-104">서버 구독이 있는 구독자는 다음을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9e21-104">Subscribers with a server subscription can:</span></span>  
  
-   <span data-ttu-id="d9e21-105">데이터를 다른 구독자에 다시 게시합니다.</span><span class="sxs-lookup"><span data-stu-id="d9e21-105">Republish data to other Subscribers.</span></span>  
  
-   <span data-ttu-id="d9e21-106">대체 동기화 파트너 역할을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="d9e21-106">Serve as alternate synchronization partners.</span></span>  
  
-   <span data-ttu-id="d9e21-107">설정한 우선 순위에 따라 충돌을 해결합니다.</span><span class="sxs-lookup"><span data-stu-id="d9e21-107">Resolve conflicts according to a priority you set.</span></span>  
  
 <span data-ttu-id="d9e21-108">대부분의 구독자는 이 기능이 필요하지 않으며 클라이언트 구독을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9e21-108">Most Subscribers do not require this functionality and can use a client subscription.</span></span> <span data-ttu-id="d9e21-109">클라이언트 구독을 사용하면 충돌 감지 및 해결이 가능하지만 구독자에게 우선 순위가 할당되지 않습니다. 변경 내용을 게시자에 전송할 첫 번째 구독자는 해당 변경 내용으로 인해 발생하는 모든 충돌에서 우선 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="d9e21-109">Client subscriptions still allow conflict detection and resolution, but Subscribers are not assigned a priority: the first Subscriber to submit a change to the Publisher wins any conflicts that might arise from that change.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d9e21-110">구독 유형은 구독을 만든 후에는 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d9e21-110">Subscription type cannot be changed after a subscription is created.</span></span>  
  
## <a name="options"></a><span data-ttu-id="d9e21-111">옵션</span><span class="sxs-lookup"><span data-stu-id="d9e21-111">Options</span></span>  
 <span data-ttu-id="d9e21-112">**구독 속성**</span><span class="sxs-lookup"><span data-stu-id="d9e21-112">**Subscription properties**</span></span>  
 <span data-ttu-id="d9e21-113">각 구독자에 대해 **구독 유형** 열의 드롭다운 목록 상자에서 **클라이언트** 또는 **서버** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d9e21-113">For each Subscriber, select **Client** or **Server** from the drop-down list box in the **Subscription Type** column.</span></span> <span data-ttu-id="d9e21-114">서버 구독이 있는 구독자의 경우 **충돌 해결의 우선 순위** 열에 0에서 99.99 사이의 숫자를 입력합니다. 숫자가 클수록 구독자에 대한 우선 순위가 높습니다.</span><span class="sxs-lookup"><span data-stu-id="d9e21-114">For Subscribers with server subscriptions, enter a number between 0 and 99.99 in the **Priority for Conflict Resolution** column (the higher the number, the higher the priority for the Subscriber).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9e21-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d9e21-115">See Also</span></span>  
 <span data-ttu-id="d9e21-116">[Create a Pull Subscription](create-a-pull-subscription.md) </span><span class="sxs-lookup"><span data-stu-id="d9e21-116">[Create a Pull Subscription](create-a-pull-subscription.md) </span></span>  
 <span data-ttu-id="d9e21-117">[ssSDSFull](create-a-push-subscription.md) </span><span class="sxs-lookup"><span data-stu-id="d9e21-117">[Create a Push Subscription](create-a-push-subscription.md) </span></span>  
 [<span data-ttu-id="d9e21-118">게시 구독</span><span class="sxs-lookup"><span data-stu-id="d9e21-118">Subscribe to Publications</span></span>](subscribe-to-publications.md)  
  
  
