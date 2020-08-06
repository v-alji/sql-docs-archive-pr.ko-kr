---
title: 스냅샷 에이전트(새 게시 마법사) | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newpubwizard.configuresnapshotagent.f1
ms.assetid: 0257d4ee-1f7b-49fd-b4ef-65bfc1ef6951
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c45fa3444fb2f81436a40a2bfb80519aea105c47
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661010"
---
# <a name="snapshot-agent-new-publication-wizard"></a><span data-ttu-id="66702-102">스냅샷 에이전트(새 게시 마법사)</span><span class="sxs-lookup"><span data-stu-id="66702-102">Snapshot Agent (New Publication Wizard)</span></span>
  <span data-ttu-id="66702-103">스냅샷 에이전트는 새 구독을 초기화하는 데 사용되는 게시 스키마와 데이터가 포함된 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="66702-103">The Snapshot Agent creates files containing the publication schema and data that are used to initialize new subscriptions.</span></span> <span data-ttu-id="66702-104">기본적으로 스냅샷 에이전트는 새 게시 마법사에서 게시가 생성된 후 즉시 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="66702-104">By default, the Snapshot Agent runs immediately after the publication is created in the New Publication Wizard.</span></span> <span data-ttu-id="66702-105">이후에는 사용자가 지정한 일정에 따라 에이전트가 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="66702-105">Subsequently, the agent runs according to a schedule you specify.</span></span> <span data-ttu-id="66702-106">에이전트가 실행될 때마다 새 스냅샷 파일을 만들지 여부는 선택한 복제 유형 및 옵션에 따라 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="66702-106">Whether the agent creates new snapshot files each time it runs depends on the type of replication and options chosen.</span></span> <span data-ttu-id="66702-107">자세한 내용은 [스냅샷 만들기 및 적용](create-and-apply-the-snapshot.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="66702-107">For more information, see [Create and Apply the Snapshot](create-and-apply-the-snapshot.md).</span></span>  
  
 <span data-ttu-id="66702-108">매개 변수가 있는 필터를 사용하는 병합 게시의 경우 게시 스냅샷이 완료된 후 각 데이터 파티션의 스냅샷을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="66702-108">For merge publications that use parameterized filters, you must create a snapshot for each partition of data after the publication snapshot has completed.</span></span> <span data-ttu-id="66702-109">자세한 내용은 [Snapshots for Merge Publications with Parameterized Filters](snapshots-for-merge-publications-with-parameterized-filters.md)을(를) 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="66702-109">For more information, see [Snapshots for Merge Publications with Parameterized Filters](snapshots-for-merge-publications-with-parameterized-filters.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="66702-110">옵션</span><span class="sxs-lookup"><span data-stu-id="66702-110">Options</span></span>  
 <span data-ttu-id="66702-111">**즉시 스냅샷 만들기** (병합 복제) 또는 **즉시 스냅샷을 만들고 구독 초기화에 사용할 수 있도록 유지합니다** (트랜잭션 복제)</span><span class="sxs-lookup"><span data-stu-id="66702-111">**Create a snapshot immediately** (merge replication) or **Create a snapshot immediately and keep the snapshot available to initialize subscriptions** (transactional replication)</span></span>  
 <span data-ttu-id="66702-112">새 게시 마법사가 완료된 후 즉시 스냅샷을 만들려면 이 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="66702-112">Select this check box to create a snapshot immediately after the New Publication Wizard is completed.</span></span> <span data-ttu-id="66702-113">스냅샷을 생성하기 전에 **게시 속성** 대화 상자에서 스냅샷 속성을 변경하거나 스냅샷 없이 구독자를 초기화하려면 이 확인란의 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="66702-113">Clear this check box if you plan to change snapshot properties in the **Publication Properties** dialog box before generating a snapshot, or if you will initialize the Subscriber without a snapshot.</span></span> <span data-ttu-id="66702-114">자세한 내용은 [스냅샷 없이 트랜잭션 구독 초기화](initialize-a-transactional-subscription-without-a-snapshot.md)에서 수동으로 구독을 초기화하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="66702-114">For more information, see [Initialize a Transactional Subscription Without a Snapshot](initialize-a-transactional-subscription-without-a-snapshot.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="66702-115">마법사에서 배포 에이전트 또는 병합 에이전트에 대해 해당 작업을 시작하려면 배포자에 연결하라는 메시지를 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="66702-115">The wizard might prompt for a connection to the Distributor in order to start the appropriate job for the Distribution Agent or Merge Agent.</span></span>  
  
 <span data-ttu-id="66702-116">**스냅샷 에이전트 실행 시간 예약**</span><span class="sxs-lookup"><span data-stu-id="66702-116">**Schedule the Snapshot Agent to run at the following times**</span></span>  
 <span data-ttu-id="66702-117">스냅샷 에이전트 실행에 대한 기본 일정을 적용하거나 **변경** 을 클릭하여 다른 일정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="66702-117">Accept the default schedule for running the Snapshot Agent, or click **Change** to specify a schedule.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66702-118">참고 항목</span><span class="sxs-lookup"><span data-stu-id="66702-118">See Also</span></span>  
 <span data-ttu-id="66702-119">[Create a Publication](publish/create-a-publication.md) </span><span class="sxs-lookup"><span data-stu-id="66702-119">[Create a Publication](publish/create-a-publication.md) </span></span>  
 <span data-ttu-id="66702-120">[초기 스냅샷 만들기 및 적용](create-and-apply-the-initial-snapshot.md) </span><span class="sxs-lookup"><span data-stu-id="66702-120">[Create and Apply the Initial Snapshot](create-and-apply-the-initial-snapshot.md) </span></span>  
 <span data-ttu-id="66702-121">[게시 속성 보기 및 수정](publish/view-and-modify-publication-properties.md) </span><span class="sxs-lookup"><span data-stu-id="66702-121">[View and Modify Publication Properties](publish/view-and-modify-publication-properties.md) </span></span>  
 <span data-ttu-id="66702-122">[스냅샷으로 구독 초기화](initialize-a-subscription-with-a-snapshot.md) </span><span class="sxs-lookup"><span data-stu-id="66702-122">[Initialize a Subscription with a Snapshot](initialize-a-subscription-with-a-snapshot.md) </span></span>  
 <span data-ttu-id="66702-123">[데이터 및 데이터베이스 개체 게시](publish/publish-data-and-database-objects.md) </span><span class="sxs-lookup"><span data-stu-id="66702-123">[Publish Data and Database Objects](publish/publish-data-and-database-objects.md) </span></span>  
 [<span data-ttu-id="66702-124">복제 에이전트 개요</span><span class="sxs-lookup"><span data-stu-id="66702-124">Replication Agents Overview</span></span>](agents/replication-agents-overview.md)  
  
  
