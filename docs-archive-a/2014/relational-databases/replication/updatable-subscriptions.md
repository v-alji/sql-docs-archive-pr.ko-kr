---
title: 업데이트할 수 있는 구독 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newsubwizard.updatablesubscriptions.f1
ms.assetid: 8e9a13a0-6b24-47c6-9d83-3cbaf08f673d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 447114152365e098420f46d4b7e880e8f2907864
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730464"
---
# <a name="updatable-subscriptions"></a><span data-ttu-id="cb1ea-102">업데이트할 수 있는 구독</span><span class="sxs-lookup"><span data-stu-id="cb1ea-102">Updatable Subscriptions</span></span>
  <span data-ttu-id="cb1ea-103">복제된 데이터는 읽기 전용으로 취급되어야 하지만 트랜잭션 복제를 사용하면 업데이트할 수 있는 구독을 사용하여 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구독자에서 복제된 데이터를 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb1ea-103">With transactional replication, replicated data should be treated as read-only; however, you can modify replicated data at a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Subscriber by using updatable subscriptions.</span></span> <span data-ttu-id="cb1ea-104">구독자에서 데이터를 수정해야 하는 경우 요구 사항에 따라 다음 옵션 중 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="cb1ea-104">If you need to modify data at the Subscriber, choose one of the following options depending on your requirements.</span></span>  
  
|<span data-ttu-id="cb1ea-105">업데이트할 수 있는 구독 유형</span><span class="sxs-lookup"><span data-stu-id="cb1ea-105">Updatable Subscription Type</span></span>|<span data-ttu-id="cb1ea-106">요구 사항</span><span class="sxs-lookup"><span data-stu-id="cb1ea-106">Requirements</span></span>|  
|---------------------------------|------------------|  
|<span data-ttu-id="cb1ea-107">즉시 업데이트</span><span class="sxs-lookup"><span data-stu-id="cb1ea-107">Immediate Updating</span></span>|<span data-ttu-id="cb1ea-108">구독자에서 데이터를 업데이트하기 위해 게시자 및 구독자를 연결해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb1ea-108">Publisher and Subscriber must be connected to update data at the Subscriber.</span></span>|  
|<span data-ttu-id="cb1ea-109">지연 업데이트</span><span class="sxs-lookup"><span data-stu-id="cb1ea-109">Queued Updating</span></span>|<span data-ttu-id="cb1ea-110">구독자에서 데이터를 업데이트하기 위해 게시자 및 구독자를 연결할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="cb1ea-110">Publisher and Subscriber do not have to be connected to update data at the Subscriber.</span></span> <span data-ttu-id="cb1ea-111">오프라인 상태에서 업데이트한 다음 나중에 게시자와 구독자 간에 동기화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb1ea-111">Updates can be made while offline, and later synchronized between the Publisher and Subscriber.</span></span>|  
  
## <a name="options"></a><span data-ttu-id="cb1ea-112">옵션</span><span class="sxs-lookup"><span data-stu-id="cb1ea-112">Options</span></span>  
 <span data-ttu-id="cb1ea-113">**구독자 변경 내용 복제**</span><span class="sxs-lookup"><span data-stu-id="cb1ea-113">**Replicate Subscriber changes**</span></span>  
 <span data-ttu-id="cb1ea-114">업데이트할 수 있어야 하는 각 구독자에 대한 **복제** 열에서 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="cb1ea-114">Select the check box in the **Replicate** column for each Subscriber that should be able to make updates.</span></span> <span data-ttu-id="cb1ea-115">**게시자에서 커밋** 열의 드롭다운 목록 상자에서 업데이트할 수 있는 구독자에 대한 적절한 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="cb1ea-115">For those Subscribers that can make updates, select the appropriate option from the drop-down list box in the **Commit at Publisher** column:</span></span>  
  
-   <span data-ttu-id="cb1ea-116">즉시 업데이트 구독에 대해 **동시에 변경 내용 커밋** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="cb1ea-116">Select **Simultaneously commit changes** for an immediate updating subscription.</span></span>  
  
-   <span data-ttu-id="cb1ea-117">지연 업데이트 구독에 대해 **변경 내용 대기 및 가능 시 커밋** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="cb1ea-117">Select **Queue changes and commit when possible** for a queued updating subscription.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb1ea-118">참고 항목</span><span class="sxs-lookup"><span data-stu-id="cb1ea-118">See Also</span></span>  
 <span data-ttu-id="cb1ea-119">[Create a Pull Subscription](create-a-pull-subscription.md) </span><span class="sxs-lookup"><span data-stu-id="cb1ea-119">[Create a Pull Subscription](create-a-pull-subscription.md) </span></span>  
 <span data-ttu-id="cb1ea-120">[ssSDSFull](create-a-push-subscription.md) </span><span class="sxs-lookup"><span data-stu-id="cb1ea-120">[Create a Push Subscription](create-a-push-subscription.md) </span></span>  
 <span data-ttu-id="cb1ea-121">[Subscribe to Publications](subscribe-to-publications.md) </span><span class="sxs-lookup"><span data-stu-id="cb1ea-121">[Subscribe to Publications](subscribe-to-publications.md) </span></span>  
 [<span data-ttu-id="cb1ea-122">Updatable Subscriptions for Transactional Replication</span><span class="sxs-lookup"><span data-stu-id="cb1ea-122">Updatable Subscriptions for Transactional Replication</span></span>](transactional/updatable-subscriptions-for-transactional-replication.md)  
  
  
