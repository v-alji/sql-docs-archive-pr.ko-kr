---
title: 고급 병합 복제 충돌 감지 및 해결 | Microsoft 문서
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- merge replication conflict resolution [SQL Server replication], about conflict resolution
- default conflict resolver
- column-level conflict tracking
- row-level conflict tracking
- viewing merge replication conflicts
- resolving merge replication conflicts
- logical record-level conflict tracking [SQL Server replication]
- conflict resolution [SQL Server replication], merge replication
ms.assetid: 063d3d9c-ccb5-4fab-9d0c-c675997428b4
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 9122f0d704db948a0a8134da2b86e34ea6426dac
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638728"
---
# <a name="advanced-merge-replication-conflict-detection-and-resolution"></a><span data-ttu-id="21b1e-102">Advanced Merge Replication Conflict Detection and Resolution</span><span class="sxs-lookup"><span data-stu-id="21b1e-102">Advanced Merge Replication Conflict Detection and Resolution</span></span>
  <span data-ttu-id="21b1e-103">게시자와 구독자가 연결되고 동기화가 이루어지면 병합 에이전트는 충돌이 있는지 감지합니다.</span><span class="sxs-lookup"><span data-stu-id="21b1e-103">When a Publisher and a Subscriber are connected and synchronization occurs, the Merge Agent detects if there are any conflicts.</span></span> <span data-ttu-id="21b1e-104">충돌이 감지되면 병합 에이전트는 게시에 아티클을 추가할 때 지정한 충돌 해결 프로그램을 사용해서 수락하여 다른 사이트로 전파할 데이터를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="21b1e-104">If conflicts are detected, the Merge Agent uses a conflict resolver (which is specified when an article is added to a publication) to determine which data is accepted and propagated to other sites.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="21b1e-105">구독자와 게시자가 동기화되는 경우에도 충돌은 대체로 구독자 및 게시자에서 수행되는 업데이트가 아닌 여러 구독자에서 수행되는 업데이트 사이에서 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="21b1e-105">Although a Subscriber synchronizes with the Publisher, conflicts typically occur between updates that are made at different Subscribers, instead of updates being made at a Subscriber and at the Publisher.</span></span>  
  
 <span data-ttu-id="21b1e-106">충돌 감지 및 해결 동작은 다음 옵션에 따라 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="21b1e-106">The behavior of conflict detection and resolution depends on the following options, which are described in this topic:</span></span>  
  
-   <span data-ttu-id="21b1e-107">열 수준 추적, 행 수준 추적 또는 논리적 레코드 수준 추적 지정</span><span class="sxs-lookup"><span data-stu-id="21b1e-107">Whether you specify column-level tracking, row-level tracking, or logical record-level tracking.</span></span>  
  
-   <span data-ttu-id="21b1e-108">기본 우선 순위 기반 해결 메커니즘 또는 아티클 해결 프로그램 지정.</span><span class="sxs-lookup"><span data-stu-id="21b1e-108">Whether you specify the default priority-based resolution mechanism or specify an article resolver.</span></span> <span data-ttu-id="21b1e-109">아티클 해결 프로그램은 다음 중 하나일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="21b1e-109">An article resolver can be:</span></span>  
  
    -   <span data-ttu-id="21b1e-110">관리 코드로 작성된 *비즈니스 논리 처리기*</span><span class="sxs-lookup"><span data-stu-id="21b1e-110">A *business logic handler* written in managed code.</span></span>  
  
    -   <span data-ttu-id="21b1e-111">COM 기반 *사용자 지정 해결 프로그램*</span><span class="sxs-lookup"><span data-stu-id="21b1e-111">A COM-based *custom resolver*.</span></span>  
  
    -   <span data-ttu-id="21b1e-112">[!INCLUDE[msCoName](../../../includes/msconame-md.md)]에서 제공하는 COM 기반 해결 프로그램</span><span class="sxs-lookup"><span data-stu-id="21b1e-112">A COM-based resolver supplied by [!INCLUDE[msCoName](../../../includes/msconame-md.md)].</span></span>  
  
     <span data-ttu-id="21b1e-113">기본 해결 메커니즘을 사용하는 경우 구독 유형이 클라이언트인지 또는 서버인지에 따라 동작이 추가로 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="21b1e-113">If the default resolution mechanism is used, behavior is further determined by the type of subscription used: client or server.</span></span>  
  
## <a name="conflict-detection"></a><span data-ttu-id="21b1e-114">충돌 감지</span><span class="sxs-lookup"><span data-stu-id="21b1e-114">Conflict Detection</span></span>  
 <span data-ttu-id="21b1e-115">데이터 변경의 충돌 여부는 아티클에 대해 설정한 충돌 추적 유형에 따라 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="21b1e-115">Whether a data change qualifies as a conflict or not depends on the type of conflict tracking you set for an article:</span></span>  
  
-   <span data-ttu-id="21b1e-116">열 수준 충돌 추적을 선택하면 둘 이상의 복제 노드에서 동일한 행의 동일한 열이 변경되는 경우 충돌로 간주됩니다.</span><span class="sxs-lookup"><span data-stu-id="21b1e-116">If you select column-level conflict tracking, it is considered a conflict if changes are made to the same column in the same row at more than one replication node.</span></span>  
  
-   <span data-ttu-id="21b1e-117">행 수준 추적을 선택하면 둘 이상의 복제 노드에서 동일한 행의 임의 열이 변경되는 경우 충돌로 간주됩니다. 해당 행에서 영향을 받는 열이 동일할 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="21b1e-117">If you select row-level tracking, it is considered a conflict if changes are made to any columns in the same row at more than one replication node (the columns affected in the corresponding rows need not be the same).</span></span>  
  
-   <span data-ttu-id="21b1e-118">논리적 레코드 수준 추적을 선택하면 둘 이상의 복제 노드에서 동일한 논리적 레코드의 임의 행이 변경되는 경우 충돌로 간주됩니다. 해당 행에서 영향을 받는 열이 동일할 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="21b1e-118">If you select logical record-level tracking, it is considered a conflict if changes are made to any row in the same logical record at more than one replication node (the columns affected in the corresponding rows need not be the same).</span></span>  
  
 <span data-ttu-id="21b1e-119">자세한 내용은 [논리적 레코드에서 충돌 감지 및 해결](advanced-merge-replication-conflict-resolving-in-logical-record.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="21b1e-119">For more information, see [Detecting and Resolving Conflicts in Logical Records](advanced-merge-replication-conflict-resolving-in-logical-record.md).</span></span>  
  
 <span data-ttu-id="21b1e-120">아티클의 충돌 추적 및 해결 수준을 지정하려면 [병합 아티클에 대 한 충돌 추적 및 해결 수준 지정](../publish/specify-merge-replication-properties.md#interactive-conflict-resolution)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="21b1e-120">To specify the conflict tracking and resolution level for an article, see [Specify the Conflict Tracking and Resolution Level for Merge Articles](../publish/specify-merge-replication-properties.md#interactive-conflict-resolution).</span></span>  
  
## <a name="conflict-resolution"></a><span data-ttu-id="21b1e-121">충돌 해결</span><span class="sxs-lookup"><span data-stu-id="21b1e-121">Conflict Resolution</span></span>  
 <span data-ttu-id="21b1e-122">충돌이 감지되면 병합 에이전트는 선택한 충돌 해결 프로그램을 시작하고 해결 프로그램을 사용하여 충돌 시 적용되는 내용을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="21b1e-122">After a conflict is detected, the Merge Agent launches the selected conflict resolver and uses the resolver to determine the conflict winner.</span></span> <span data-ttu-id="21b1e-123">적용되는 행이 게시자 및 구독자에서 적용되며 무시되는 행의 데이터는 충돌 테이블에 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="21b1e-123">The winning row is applied at the Publisher and Subscriber, and the data from the losing row is written to a conflict table.</span></span> <span data-ttu-id="21b1e-124">대화형으로 충돌을 해결하도록 선택하지 않으면 해결 프로그램이 실행된 후 즉시 충돌이 해결됩니다.</span><span class="sxs-lookup"><span data-stu-id="21b1e-124">Conflicts are resolved immediately after the resolver executes, unless you select to resolve conflicts interactively.</span></span>  
  
### <a name="resolver-types"></a><span data-ttu-id="21b1e-125">해결 프로그램 유형</span><span class="sxs-lookup"><span data-stu-id="21b1e-125">Resolver Types</span></span>  
 <span data-ttu-id="21b1e-126">병합 복제에서 충돌 해결은 아티클 수준에서 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="21b1e-126">In merge replication, conflict resolution takes place at the article level.</span></span> <span data-ttu-id="21b1e-127">여러 아티클로 구성된 게시의 경우 아티클별로 서로 다른 충돌 해결 프로그램을 사용할 수도 있고 게시를 구성하는 모든 아티클, 여러 아티클 또는 하나의 아티클에 대해 같은 충돌 해결 프로그램을 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="21b1e-127">For publications composed of several articles, you can have different conflict resolvers serving different articles, or the same conflict resolver serving one article, several articles, or all the articles comprising a publication.</span></span>  
  
 <span data-ttu-id="21b1e-128">기본 우선 순위 기반 충돌 해결 프로그램을 사용할 경우에는 아티클의 해결 프로그램 속성을 설정할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="21b1e-128">If you plan to use the default priority-based conflict resolver, you do not have to set the resolver property of an article.</span></span> <span data-ttu-id="21b1e-129">기본 해결 프로그램 대신 아티클 해결 프로그램을 사용하려면 게시자에서 사용 가능한 해결 프로그램을 선택하여 해당 해결 프로그램이 사용될 아티클에 대해 해결 프로그램 속성을 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="21b1e-129">If you want to use an article resolver instead of the default resolver, you must set the resolver property for the article that will use it by selecting an available resolver on the Publisher.</span></span> <span data-ttu-id="21b1e-130">해결 프로그램으로 전달되어야 하는 모든 특정 정보는 해결 프로그램 정보 속성에서 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="21b1e-130">Any specific information that needs to be passed to the resolver can also be specified in the resolver information property.</span></span>  
  
 <span data-ttu-id="21b1e-131">병합 복제는 다음 4가지 유형의 충돌 해결 프로그램을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="21b1e-131">Merge replication offers four types of conflict resolvers:</span></span>  
  
-   <span data-ttu-id="21b1e-132">기본 우선 순위 기반 충돌 해결 프로그램</span><span class="sxs-lookup"><span data-stu-id="21b1e-132">The default priority-based conflict resolver</span></span>  
  
     <span data-ttu-id="21b1e-133">기본 해결 메커니즘은 구독이 클라이언트 구독인지 서버 구독인지에 따라 다르게 동작합니다.</span><span class="sxs-lookup"><span data-stu-id="21b1e-133">The default resolution mechanism behaves differently, depending on whether a subscription is a client subscription or a server subscription.</span></span> <span data-ttu-id="21b1e-134">서버 구독을 사용하는 개별 구독자에게 우선 순위 값을 할당하며 우선 순위가 가장 높은 노드의 변경 내용이 충돌 시 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="21b1e-134">You assign priority values to individual Subscribers that use server subscriptions; changes made at the node with the highest priority win any conflicts.</span></span> <span data-ttu-id="21b1e-135">클라이언트 구독의 경우 게시자에 작성된 첫 번째 변경 내용이 충돌 시 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="21b1e-135">For client subscriptions, the first change written to the Publisher wins the conflict.</span></span>  
  
     <span data-ttu-id="21b1e-136">구독을 만든 후에는 해당 유형을 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="21b1e-136">After a subscription is created, it cannot be changed from one type to another.</span></span>  
  
-   <span data-ttu-id="21b1e-137">비즈니스 논리 처리기</span><span class="sxs-lookup"><span data-stu-id="21b1e-137">A business logic handler</span></span>  
  
     <span data-ttu-id="21b1e-138">비즈니스 논리 처리기 프레임워크를 사용하면 병합 동기화 과정 동안 호출되는 관리 코드 어셈블리를 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="21b1e-138">The business logic handler framework allows you to write a managed code assembly that is called during the merge synchronization process.</span></span> <span data-ttu-id="21b1e-139">이 어셈블리에는 동기화 중에 충돌과 다른 많은 조건에 응답할 수 있는 비즈니스 논리가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="21b1e-139">The assembly includes business logic that can respond to conflicts and a number of other conditions during synchronization.</span></span> <span data-ttu-id="21b1e-140">자세한 내용은 [병합 동기화 중 비즈니스 논리 실행](execute-business-logic-during-merge-synchronization.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="21b1e-140">For more information, see [Execute Business Logic During Merge Synchronization](execute-business-logic-during-merge-synchronization.md).</span></span>  
  
-   <span data-ttu-id="21b1e-141">COM 기반 사용자 지정 해결 프로그램</span><span class="sxs-lookup"><span data-stu-id="21b1e-141">A COM-based custom resolver</span></span>  
  
     <span data-ttu-id="21b1e-142">병합 복제는 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vcprvc](../../../includes/vcprvc-md.md)] 또는 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]과 같은 언어를 사용하여 해결 프로그램을 COM 개체로 작성하기 위한 API를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="21b1e-142">Merge replication provides an API for writing resolvers as COM objects in languages such as [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vcprvc](../../../includes/vcprvc-md.md)] or [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)].</span></span> <span data-ttu-id="21b1e-143">자세한 내용은 [COM-Based Custom Resolvers](advanced-merge-replication-conflict-com-based-custom-resolvers.md)을(를) 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="21b1e-143">For more information, see [COM-Based Custom Resolvers](advanced-merge-replication-conflict-com-based-custom-resolvers.md).</span></span>  
  
-   <span data-ttu-id="21b1e-144">[!INCLUDE[msCoName](../../../includes/msconame-md.md)]에서 제공하는 COM 기반 해결 프로그램</span><span class="sxs-lookup"><span data-stu-id="21b1e-144">A COM-based resolver supplied by [!INCLUDE[msCoName](../../../includes/msconame-md.md)]</span></span>  
  
     [!INCLUDE[msCoName](../../../includes/msconame-md.md)] <span data-ttu-id="21b1e-145">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에는 많은 COM 기반 해결 프로그램이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="21b1e-145">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] includes a number of COM-based resolvers.</span></span> <span data-ttu-id="21b1e-146">자세한 내용은 [Microsoft COM 기반 해결 프로그램](advanced-merge-replication-conflict-com-based-resolvers.md)을(를) 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="21b1e-146">For more information, see [Microsoft COM-Based Resolvers](advanced-merge-replication-conflict-com-based-resolvers.md).</span></span>  
  
 <span data-ttu-id="21b1e-147">적절한 유형의 해결 프로그램을 선택하는 방법에 대한 자세한 내용은 [해결 프로그램 선택](advanced-merge-replication-conflict-choose-a-resolver.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="21b1e-147">For information about how to select the appropriate type of resolver, see [Choose a Resolver](advanced-merge-replication-conflict-choose-a-resolver.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="21b1e-148">일부 아티클 해결 프로그램은 특정 작업에 대해서만 충돌을 처리하도록 작성됩니다.</span><span class="sxs-lookup"><span data-stu-id="21b1e-148">Some article resolvers are written to handle conflicts only for certain operations.</span></span> <span data-ttu-id="21b1e-149">예를 들어 특정 해결 프로그램은 삽입 또는 삭제는 처리하지 않고 업데이트만 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="21b1e-149">For example a resolver might handle updates, but not inserts or deletes.</span></span> <span data-ttu-id="21b1e-150">기본 우선 순위 기반 충돌 해결 프로그램은 아티클 해결 프로그램이 처리하지 못한 모든 충돌을 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="21b1e-150">The default priority-based conflict resolver handles any conflicts not handled by the article resolver.</span></span>  
  
 <span data-ttu-id="21b1e-151">병합 구독 유형 및 충돌 해결 우선 순위를 지정하려면 다음을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="21b1e-151">To specify a merge subscription type and conflict resolution priority, see</span></span>  
  
-   [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]<span data-ttu-id="21b1e-152">: [병합 구독 유형 및 충돌 해결 우선순위 지정 &#40;SQL Server Management Studio&#41;](../specify-a-merge-subscription-type-and-conflict-resolution-priority.md)</span><span class="sxs-lookup"><span data-stu-id="21b1e-152">: [Specify a Merge Subscription Type and Conflict Resolution Priority &#40;SQL Server Management Studio&#41;](../specify-a-merge-subscription-type-and-conflict-resolution-priority.md)</span></span>  
  
-   <span data-ttu-id="21b1e-153">[!INCLUDE[tsql](../../../includes/tsql-md.md)] 복제 프로그래밍 및 RMO(복제 관리 개체) 프로그래밍: [끌어오기 구독 만들기](../create-a-pull-subscription.md) 및 [밀어넣기 구독 만들기](../create-a-push-subscription.md)</span><span class="sxs-lookup"><span data-stu-id="21b1e-153">Replication [!INCLUDE[tsql](../../../includes/tsql-md.md)] programming and Replication Management Objects (RMO) programming: [Create a Pull Subscription](../create-a-pull-subscription.md) and [Create a Push Subscription](../create-a-push-subscription.md)</span></span>  
  
### <a name="interactive-resolver"></a><span data-ttu-id="21b1e-154">대화형 해결 프로그램</span><span class="sxs-lookup"><span data-stu-id="21b1e-154">Interactive Resolver</span></span>  
 <span data-ttu-id="21b1e-155">복제는 기본 우선 순위 기반 충돌 해결 프로그램이나 아티클 해결 프로그램과 함께 사용할 수 있는 대화형 해결 프로그램 사용자 인터페이스를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="21b1e-155">Replication supplies an Interactive Resolver user interface that can be used in conjunction with either the default priority-based conflict resolver or an article resolver.</span></span> <span data-ttu-id="21b1e-156">[!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows 동기화 관리자를 통해 요청 시 동기화를 수행할 때 대화형 해결 프로그램은 런타임 시 충돌 데이터를 표시하고 충돌 해결 방법을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="21b1e-156">When performing on-demand synchronization through [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows Synchronization Manager, the Interactive Resolver displays conflict data at run-time, and lets you choose how to resolve conflicts.</span></span> <span data-ttu-id="21b1e-157">대화형 해결 기능 설정 방법 및 대화형 해결 프로그램 시작 방법은 [Interactive Conflict Resolution](advanced-merge-replication-conflict-interactive-resolution.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="21b1e-157">For more information about how to enable interactive resolution and launch the Interactive Resolver, see [Interactive Conflict Resolution](advanced-merge-replication-conflict-interactive-resolution.md).</span></span>  
  
## <a name="viewing-conflicts"></a><span data-ttu-id="21b1e-158">충돌 보기</span><span class="sxs-lookup"><span data-stu-id="21b1e-158">Viewing Conflicts</span></span>  
 <span data-ttu-id="21b1e-159">가장 간단한 방법으로 충돌을 보려면 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 에서 제공하는 복제 충돌 뷰어를 사용합니다.[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 는 충돌 테이블을 쿼리할 저장 프로시저도 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="21b1e-159">The most straightforward way to view conflicts is to use the Replication Conflict Viewer, available from [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] ([!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] also provides stored procedures that allow the conflict tables to be queried.).</span></span> <span data-ttu-id="21b1e-160">충돌 뷰어와 대화형 해결 프로그램은 유사한 도구이지만, 대화형 해결 프로그램은 동기화가 이루어지는 동안 충돌을 해결하는데 사용하는 반면 충돌 뷰어는 충돌이 해결된 후 충돌을 보는 데 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="21b1e-160">The Conflict Viewer and Interactive Resolver are similar tools, but the Interactive Resolver allows you to resolve conflicts as synchronization occurs, whereas the Conflict Viewer is designed for viewing conflicts after they have been resolved.</span></span> <span data-ttu-id="21b1e-161">시스템 테이블에서 충돌 메타데이터를 사용할 수 있는 경우(충돌 메타데이터는 기본적으로 14일 동안 유지됨) 충돌 뷰어에서 충돌 해결 결과를 무시할 수 있지만 정기적으로 직접적인 사용자 작업이 필요한 경우 대화형 해결 프로그램을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="21b1e-161">If the conflict metadata is still available in the system tables (conflict metadata is retained for 14 days by default), you can override conflict resolution outcomes in the Conflict Viewer, but if direct intervention is regularly required, consider using the Interactive Resolver.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="21b1e-162">논리적 레코드와 관련된 충돌은 충돌 뷰어에 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="21b1e-162">Conflicts that involve logical records are not displayed in Conflict Viewer.</span></span> <span data-ttu-id="21b1e-163">이러한 충돌에 대한 정보를 보려면 복제 저장 프로시저를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="21b1e-163">To view information about these conflicts, use replication stored procedures.</span></span> <span data-ttu-id="21b1e-164">자세한 내용은 [병합 게시에 대한 충돌 정보 보기&#40;복제 Transact-SQL 프로그래밍&#41;](../view-conflict-information-for-merge-publications.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="21b1e-164">For more information, see [View Conflict Information for Merge Publications &#40;Replication Transact-SQL Programming&#41;](../view-conflict-information-for-merge-publications.md).</span></span>  
  
 <span data-ttu-id="21b1e-165">충돌 뷰어는 3개의 시스템 테이블에 대한 정보를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="21b1e-165">The Conflict Viewer displays information from three system tables:</span></span>  
  
-   <span data-ttu-id="21b1e-166">복제는 병합 아티클의 각 테이블에 대해 **MSmerge_conflict_\<PublicationName>_\<ArticleName>** 형식의 이름으로 충돌 테이블을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="21b1e-166">Replication creates a conflict table for each table in a merge article, with a name in the form **MSmerge_conflict_\<PublicationName>_\<ArticleName>**.</span></span>  
  
     <span data-ttu-id="21b1e-167">충돌 테이블의 구조는 기준이 되는 테이블의 구조와 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="21b1e-167">Conflict tables have the same structure as the tables on which they are based.</span></span> <span data-ttu-id="21b1e-168">이 테이블 중 한 테이블의 행은 충돌 행의 삭제된 버전으로 구성되어 있습니다. 행의 적용되는 버전은 실제 사용자 테이블에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="21b1e-168">A row in one of these tables consists of the losing version of a conflict row (the winning version of the row is in the actual user table).</span></span>  
  
-   <span data-ttu-id="21b1e-169">**MSmerge_conflicts_info** 테이블은 충돌 유형을 포함하여 각 충돌에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="21b1e-169">The **MSmerge_conflicts_info** table provides information about each conflict, including the conflict type.</span></span>  
  
-   <span data-ttu-id="21b1e-170">**sysmergearticles** 테이블은 충돌 테이블이 있는 사용자 테이블을 식별하고 충돌 테이블에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="21b1e-170">The **sysmergearticles** table identifies which user tables have conflict tables and provides information about the conflict tables.</span></span>  
  
 <span data-ttu-id="21b1e-171">기본적으로 충돌 정보는 다음 위치에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="21b1e-171">By default, conflict information is stored:</span></span>  
  
-   <span data-ttu-id="21b1e-172">게시 호환성 수준이 90RTM 이상일 경우 게시자 및 구독자.</span><span class="sxs-lookup"><span data-stu-id="21b1e-172">At the Publisher and Subscriber if the publication compatibility level is 90RTM or higher.</span></span>  
  
-   <span data-ttu-id="21b1e-173">게시 호환성 수준이 80RTM 미만일 경우 게시자</span><span class="sxs-lookup"><span data-stu-id="21b1e-173">At the Publisher if the publication compatibility level is lower than 80RTM.</span></span>  
  
-   <span data-ttu-id="21b1e-174">구독자가 [!INCLUDE[ssEW](../../../includes/ssew-md.md)]을 실행하는 경우 게시자.</span><span class="sxs-lookup"><span data-stu-id="21b1e-174">At the Publisher if Subscribers are running [!INCLUDE[ssEW](../../../includes/ssew-md.md)].</span></span> <span data-ttu-id="21b1e-175">충돌 데이터는 [!INCLUDE[ssEW](../../../includes/ssew-md.md)] 구독자에 저장할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="21b1e-175">Conflict data cannot be stored on [!INCLUDE[ssEW](../../../includes/ssew-md.md)] Subscribers.</span></span>  
  
 <span data-ttu-id="21b1e-176">**충돌을 보려면**</span><span class="sxs-lookup"><span data-stu-id="21b1e-176">**To view conflicts**</span></span>  
  
-   [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]<span data-ttu-id="21b1e-177">: [병합 게시에 대한 데이터 충돌 보기 및 해결&#40;SQL Server Management Studio&#41;](../view-and-resolve-data-conflicts-for-merge-publications.md)</span><span class="sxs-lookup"><span data-stu-id="21b1e-177">: [View and Resolve Data Conflicts for Merge Publications &#40;SQL Server Management Studio&#41;](../view-and-resolve-data-conflicts-for-merge-publications.md)</span></span>  
  
-   <span data-ttu-id="21b1e-178">복제 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 프로그래밍: [병합 게시에 대한 충돌 정보 보기&#40;복제 Transact-SQL 프로그래밍&#41;](../view-conflict-information-for-merge-publications.md)</span><span class="sxs-lookup"><span data-stu-id="21b1e-178">Replication [!INCLUDE[tsql](../../../includes/tsql-md.md)] Programming: [View Conflict Information for Merge Publications &#40;Replication Transact-SQL Programming&#41;](../view-conflict-information-for-merge-publications.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21b1e-179">참고 항목</span><span class="sxs-lookup"><span data-stu-id="21b1e-179">See Also</span></span>  
 [<span data-ttu-id="21b1e-180">데이터 동기화</span><span class="sxs-lookup"><span data-stu-id="21b1e-180">Synchronize Data</span></span>](../synchronize-data.md)  
  
  
