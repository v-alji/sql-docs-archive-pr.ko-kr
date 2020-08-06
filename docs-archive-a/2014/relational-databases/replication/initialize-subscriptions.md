---
title: 구독 초기화 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newsubwizard.initializesubscriptions.f1
ms.assetid: 7b170e4e-470d-4828-a9ed-7435b0b03514
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f8c9388138ddec275dc1abd2b75e0b0c7fc99de4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646867"
---
# <a name="initialize-subscriptions"></a><span data-ttu-id="81043-102">구독 초기화</span><span class="sxs-lookup"><span data-stu-id="81043-102">Initialize Subscriptions</span></span>
  <span data-ttu-id="81043-103">구독자는 초기화되어야만 복제된 데이터를 받을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="81043-103">Subscribers must be initialized before they can begin receiving replicated data.</span></span> <span data-ttu-id="81043-104">초기 데이터 세트는 필요 없지만 구독자에는 적어도 복제된 각 개체에 대한 스키마와 복제에 필요한 메타데이터 테이블 및 프로시저가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="81043-104">An initial dataset is not required, but the Subscriber must at least have the schema for each replicated object and any metadata tables and procedures required by replication.</span></span>  
  
## <a name="options"></a><span data-ttu-id="81043-105">옵션</span><span class="sxs-lookup"><span data-stu-id="81043-105">Options</span></span>  
 <span data-ttu-id="81043-106">**구독 속성**</span><span class="sxs-lookup"><span data-stu-id="81043-106">**Subscription properties**</span></span>  
 <span data-ttu-id="81043-107">초기 데이터 집합이 필요한 각 구독자의 **초기화** 열에서 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="81043-107">Select the check box in the **Initialize** column for each Subscriber that requires an initial data set.</span></span> <span data-ttu-id="81043-108">확인란 선택을 취소하면 복제 메타데이터 및 프로시저만 초기화됩니다.</span><span class="sxs-lookup"><span data-stu-id="81043-108">If the check box is cleared, only the replication metadata and procedures will be initialized.</span></span> <span data-ttu-id="81043-109">스냅샷 없이 구독 초기화에 대한 자세한 내용은 [스냅샷 없이 트랜잭션 구독 초기화](initialize-a-transactional-subscription-without-a-snapshot.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="81043-109">For more information about initializing a subscription without a snapshot, see [Initialize a Transactional Subscription Without a Snapshot](initialize-a-transactional-subscription-without-a-snapshot.md).</span></span>  
  
 <span data-ttu-id="81043-110">이 마법사가 완료된 다음 병합 에이전트 또는 배포 에이전트가 스냅샷 파일을 구독자에게 전송하게 하려면 **초기화 시기** 열의 드롭다운 목록 상자에서 **즉시** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="81043-110">Select **Immediately** from the drop-down list box in the **Initialize When** column to have the Merge Agent or Distribution Agent transfer snapshot files to the Subscriber after this wizard is completed.</span></span> <span data-ttu-id="81043-111">에이전트가 다음 실행 일정에 파일을 전송하게 하려면 **첫 번째 동기화 시** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="81043-111">Select **At first synchronization** to have the agent transfer the files the next time it is scheduled to run.</span></span> <span data-ttu-id="81043-112">**즉시** 옵션은 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]에 대한 끌어오기 구독에 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="81043-112">The **Immediately** option is not available for pull subscriptions to [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)].</span></span> <span data-ttu-id="81043-113">병합 에이전트 및 배포 에이전트는 [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]인스턴스에서 실행되지 않으므로 다른 방법으로 구독을 초기화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="81043-113">The Merge Agent and Distribution Agent do not run on instances of [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]; therefore the subscription must be initialized through another method.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="81043-114">마법사에서 배포 에이전트 또는 병합 에이전트에 대해 해당 작업을 시작하려면 배포자에 연결하라는 메시지를 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="81043-114">The wizard might prompt for a connection to the Distributor in order to start the appropriate job for the Distribution Agent or Merge Agent.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81043-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="81043-115">See Also</span></span>  
 <span data-ttu-id="81043-116">[Create a Pull Subscription](create-a-pull-subscription.md) </span><span class="sxs-lookup"><span data-stu-id="81043-116">[Create a Pull Subscription](create-a-pull-subscription.md) </span></span>  
 <span data-ttu-id="81043-117">[ssSDSFull](create-a-push-subscription.md) </span><span class="sxs-lookup"><span data-stu-id="81043-117">[Create a Push Subscription](create-a-push-subscription.md) </span></span>  
 <span data-ttu-id="81043-118">[구독 초기화](initialize-a-subscription.md) </span><span class="sxs-lookup"><span data-stu-id="81043-118">[Initialize a Subscription](initialize-a-subscription.md) </span></span>  
 [<span data-ttu-id="81043-119">게시 구독</span><span class="sxs-lookup"><span data-stu-id="81043-119">Subscribe to Publications</span></span>](subscribe-to-publications.md)  
  
  
