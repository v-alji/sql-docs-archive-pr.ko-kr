---
title: Windows 동기화 관리자를 사용 하 여 구독 동기화 (Windows 동기화 관리자) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- synchronization [SQL Server replication], Windows Synchronization Manager
- Windows Synchronization Manager
ms.assetid: 80f15dd6-e84d-4f96-9866-5b34ea531f1e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: bb31c344f91c68b04e03dd218f22b09bec44830b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732556"
---
# <a name="synchronize-a-subscription-using-windows-synchronization-manager-windows-synchronization-manager"></a><span data-ttu-id="b5af9-102">Windows 동기화 관리자를 사용하여 구독 동기화(Windows 동기화 관리자)</span><span class="sxs-lookup"><span data-stu-id="b5af9-102">Synchronize a Subscription Using Windows Synchronization Manager (Windows Synchronization Manager)</span></span>
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="b5af9-103">가 동기화 관리자와 같은 컴퓨터에서 실행 중인 경우에는 구독을 Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 게시와 동기화하는 데만 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Windows 동기화 관리자를 사용할 수 있습니다. 동기화 관리자를 사용하면 오프라인 파일과 웹 페이지를 동기화할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b5af9-103">Windows Synchronization Manager can only be used to synchronize subscriptions to Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] publications if [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is running on the same computer as Synchronization Manager (it can also be used to synchronize offline files and Web pages).</span></span> <span data-ttu-id="b5af9-104">동기화 관리자를 사용하려면 다음을 수행하십시오.</span><span class="sxs-lookup"><span data-stu-id="b5af9-104">To use Synchronization Manager:</span></span>  
  
1.  <span data-ttu-id="b5af9-105">**구독 속성 - \<Subscriber>: \<SubscriptionDatabase>** 대화 상자에서 Windows 동기화 관리자를 통한 끌어오기 구독 동기화를 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="b5af9-105">Enable the synchronization of pull subscriptions with Windows Synchronization Manager in the **Subscription Properties - \<Subscriber>: \<SubscriptionDatabase>** dialog box.</span></span> <span data-ttu-id="b5af9-106">이 대화 상자에 액세스하는 방법은 [끌어오기 구독 속성 보기 및 수정](view-and-modify-pull-subscription-properties.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b5af9-106">For more information about accessing this dialog box, see [View and Modify Pull Subscription Properties](view-and-modify-pull-subscription-properties.md).</span></span>  
  
2.  <span data-ttu-id="b5af9-107">Windows의 **시작** 메뉴를 통해 동기화 관리자에 액세스합니다.</span><span class="sxs-lookup"><span data-stu-id="b5af9-107">Access Synchronization Manager through the **Start** menu in Windows.</span></span>  
  
 <span data-ttu-id="b5af9-108">동기화 관리자를 사용하면 병합 구독에 대해 대화형 해결 프로그램을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b5af9-108">Synchronization Manager allows you to use the Interactive Resolver for merge subscriptions.</span></span> <span data-ttu-id="b5af9-109">일반적으로 동기화하는 동안 감지된 충돌은 자동으로 해결되지만 대화형 해결이 설정된 경우에는 동기화하는 동안 사용자가 충돌을 해결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b5af9-109">Typically, conflicts detected during synchronization are resolved automatically, but if interactive resolution is enabled, conflicts can be resolved by a user during synchronization.</span></span> <span data-ttu-id="b5af9-110">동기화가 Windows 동기화 관리자 외부(예: [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 또는 복제 모니터의 예약 동기화 또는 요청 시 동기화)에서 수행된 경우 아티클에 지정된 해결 프로그램에 따라 사용자 개입 없이도 자동으로 충돌이 해결됩니다.</span><span class="sxs-lookup"><span data-stu-id="b5af9-110">If a synchronization is performed outside of Windows Synchronization Manager (as a scheduled synchronization or an on demand synchronization in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or Replication Monitor), conflicts are resolved automatically without user intervention, according to the resolver specified for the article.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b5af9-111">[!INCLUDE[firstref_longhorn](../../includes/firstref-longhorn-md.md)] 및 [!INCLUDE[wiprlhlong](../../includes/wiprlhlong-md.md)]부터 64비트 버전의 Windows 동기화 관리자는 32비트 구독을 검색할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b5af9-111">Beginning with [!INCLUDE[firstref_longhorn](../../includes/firstref-longhorn-md.md)] and [!INCLUDE[wiprlhlong](../../includes/wiprlhlong-md.md)], 64-bit versions of the Windows Synchronization Manager cannot detect 32-bit subscriptions.</span></span>  
  
### <a name="to-enable-the-synchronization-of-pull-subscriptions-with-windows-synchronization-manager"></a><span data-ttu-id="b5af9-112">Windows 동기화 관리자를 통한 끌어오기 구독 동기화가 가능하도록 설정하려면</span><span class="sxs-lookup"><span data-stu-id="b5af9-112">To enable the synchronization of pull subscriptions with Windows Synchronization Manager</span></span>  
  
1.  <span data-ttu-id="b5af9-113">**구독 속성 - \<Subscriber>: \<SubscriptionDatabase>** 대화 상자의 **일반** 페이지에서 **Windows 동기화 관리자 사용** 옵션에 **사용** 값을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b5af9-113">On the **General** page of the **Subscription Properties - \<Subscriber>: \<SubscriptionDatabase>** dialog box, select a value of **Enable** for the **Use Windows Synchronization Manager** option.</span></span>  
  
2.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-synchronize-a-pull-subscription-with-synchronization-manager"></a><span data-ttu-id="b5af9-114">동기화 관리자로 끌어오기 구독을 동기화하려면</span><span class="sxs-lookup"><span data-stu-id="b5af9-114">To synchronize a pull subscription with Synchronization Manager</span></span>  
  
1.  <span data-ttu-id="b5af9-115">다음 중 한 가지 방법을 사용하여 동기화 관리자를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="b5af9-115">Launch Synchronization Manager using one of the following methods:</span></span>  
  
    -   <span data-ttu-id="b5af9-116">Internet Explorer에서 **도구**, **동기화**를 차례로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b5af9-116">In Internet Explorer, click **Tools**, and then click **Synchronize**.</span></span>  
  
    -   <span data-ttu-id="b5af9-117">**시작**을 클릭하고 **프로그램** 또는 **모든 프로그램**, **보조프로그램**을 차례로 가리킨 다음 **동기화**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b5af9-117">Click **Start**, point to **Programs** or **All Programs**, point to **Accessories**, and then click **Synchronize**.</span></span>  
  
    -   <span data-ttu-id="b5af9-118">**시작**, **실행**</span><span class="sxs-lookup"><span data-stu-id="b5af9-118">Click **Start**, and then click **Run.**</span></span> <span data-ttu-id="b5af9-119">**실행** 대화 상자에서 `mobsync.exe` **열기** 필드에를 입력 한 다음 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="b5af9-119">In the **Run** dialog box, type `mobsync.exe` in the **Open** field, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="b5af9-120">**동기화할 항목** 대화 상자에서 동기화할 구독을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b5af9-120">In the **Items to Synchronize** dialog box, select the subscriptions to synchronize.</span></span> <span data-ttu-id="b5af9-121">구독은 컴퓨터에 설치된 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스 아래에 나열되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b5af9-121">Subscriptions are listed under the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instances installed on the computer.</span></span>  
  
3.  <span data-ttu-id="b5af9-122">**동기화**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b5af9-122">Click **Synchronize**.</span></span>  
  
### <a name="to-reinitialize-a-pull-subscription-with-synchronization-manager"></a><span data-ttu-id="b5af9-123">동기화 관리자로 끌어오기 구독을 다시 초기화하려면</span><span class="sxs-lookup"><span data-stu-id="b5af9-123">To reinitialize a pull subscription with Synchronization Manager</span></span>  
  
1.  <span data-ttu-id="b5af9-124">**동기화할 항목** 대화 상자에서 구독을 선택한 다음 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b5af9-124">In the **Items to Synchronize** dialog box, select a subscription, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="b5af9-125">**SQL Server 구독 속성** 대화 상자에서 **구독 다시 초기화**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b5af9-125">In the **SQL Server Subscription Properties** dialog box, click **Reinitialize Subscription**.</span></span>  
  
3.  <span data-ttu-id="b5af9-126">**예**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b5af9-126">Click **Yes**.</span></span>  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
     <span data-ttu-id="b5af9-127">다음에 구독이 동기화되면 기본적으로 새 스냅샷이 구독 데이터베이스에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="b5af9-127">The next time the subscription is synchronized, by default a new snapshot is applied to the subscription database.</span></span> <span data-ttu-id="b5af9-128">자세한 내용은 [구독 다시 초기화](reinitialize-subscriptions.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b5af9-128">For more information, see [Reinitialize Subscriptions](reinitialize-subscriptions.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b5af9-129">병합 복제를 사용하면 스냅샷이 적용되기 전에 처리 중인 변경 내용이 게시자로 업로드되지만 동기화 관리자에서는 이 옵션을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b5af9-129">Merge replication allows any outstanding changes to be uploaded to the Publisher before the snapshot is applied, but this option is not available from Synchronization Manager.</span></span> <span data-ttu-id="b5af9-130">변경 내용을 업로드하려면 구독을 다시 초기화하기 전에 동기화합니다.</span><span class="sxs-lookup"><span data-stu-id="b5af9-130">To upload changes, synchronize the subscription before reinitializing it.</span></span>  
  
### <a name="to-set-properties-for-a-pull-subscription-in-synchronization-manager"></a><span data-ttu-id="b5af9-131">동기화 관리자에서 끌어오기 구독에 대한 속성을 설정하려면</span><span class="sxs-lookup"><span data-stu-id="b5af9-131">To set properties for a pull subscription in Synchronization Manager</span></span>  
  
1.  <span data-ttu-id="b5af9-132">**동기화할 항목** 대화 상자에서 구독을 선택한 다음 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b5af9-132">In the **Items to Synchronize** dialog box, select a subscription, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="b5af9-133">다음 탭에서 속성을 보고 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="b5af9-133">View and modify properties on the following tabs:</span></span>  
  
    -   <span data-ttu-id="b5af9-134">**ID**</span><span class="sxs-lookup"><span data-stu-id="b5af9-134">**Identification**</span></span>  
  
    -   <span data-ttu-id="b5af9-135">**구독자 로그인**, **배포자 로그인**및 **게시자 로그인** (병합 복제의 경우만 해당)</span><span class="sxs-lookup"><span data-stu-id="b5af9-135">**Subscriber Login**, **Distributor Login**, and **Publisher Login** (for merge replication only)</span></span>  
  
    -   <span data-ttu-id="b5af9-136">**웹 서버 정보** (SQL Server 2005 이상을 실행하는 구독자에서 병합 구독의 경우)</span><span class="sxs-lookup"><span data-stu-id="b5af9-136">**Web Server Information** (for merge subscriptions on Subscribers running SQL Server 2005 or later)</span></span>  
  
    -   <span data-ttu-id="b5af9-137">**기타**</span><span class="sxs-lookup"><span data-stu-id="b5af9-137">**Other**</span></span>  
  
     <span data-ttu-id="b5af9-138">모든 연결에 대해 Windows 인증을 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="b5af9-138">It is recommended to use Windows Authentication for all connections.</span></span> <span data-ttu-id="b5af9-139">배포 에이전트 및 병합 에이전트에 필요한 사용 권한에 대한 자세한 내용은 [Replication Agent Security Model](security/replication-agent-security-model.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="b5af9-139">For information about the permissions required by the Distribution Agent and the Merge Agent, see [Replication Agent Security Model](security/replication-agent-security-model.md).</span></span>  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-remove-a-pull-subscription-from-synchronization-manager"></a><span data-ttu-id="b5af9-140">동기화 관리자에서 끌어오기 구독을 제거하려면</span><span class="sxs-lookup"><span data-stu-id="b5af9-140">To remove a pull subscription from Synchronization Manager</span></span>  
  
1.  <span data-ttu-id="b5af9-141">**동기화할 항목** 대화 상자에서 구독을 선택한 다음 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b5af9-141">In the **Items to Synchronize** dialog box, select a subscription, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="b5af9-142">**SQL Server 구독 속성** 대화 상자에서 **구독 제거**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b5af9-142">In the **SQL Server Subscription Properties** dialog box, click **Remove Subscription**.</span></span>  
  
3.  <span data-ttu-id="b5af9-143">**구독 제거** 대화 상자에서 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b5af9-143">Select an option in the **Remove Subscription** dialog box.</span></span>  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-use-the-interactive-resolver"></a><span data-ttu-id="b5af9-144">대화형 해결 프로그램을 사용하려면</span><span class="sxs-lookup"><span data-stu-id="b5af9-144">To use the Interactive Resolver</span></span>  
  
1.  <span data-ttu-id="b5af9-145">대화형 해결을 사용할 아티클과 구독을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="b5af9-145">Enable the article and subscription to use interactive resolution.</span></span> <span data-ttu-id="b5af9-146">자세한 내용은 [병합 아티클에 대한 상호 충돌 해결 지정](../../relational-databases/replication/publish/specify-merge-replication-properties.md#interactive-conflict-resolution)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b5af9-146">For more information, see [Specify Interactive Conflict Resolution for Merge Articles](../../relational-databases/replication/publish/specify-merge-replication-properties.md#interactive-conflict-resolution).</span></span>
  
2.  <span data-ttu-id="b5af9-147">동기화 관리자에서 구독이 동기화를 시작하면 대화형 충돌 해결이 설정되어 있고 하나 이상의 아티클에 대한 충돌이 있는 경우 대화형 해결 프로그램이 자동으로 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="b5af9-147">After the subscription begins synchronizing in Synchronization Manager, the Interactive Resolver launches automatically if interactive conflict resolution is enabled and there are conflicts for one or more articles.</span></span> <span data-ttu-id="b5af9-148">대화형 해결 프로그램은 권장 해결 방법(게시 및 구독을 만들 때 지정한 해결 프로그램에 기반함)과 함께 한 번에 하나의 충돌을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="b5af9-148">The Interactive Resolver displays conflicts one at a time, with a suggested resolution for each conflict (based on the resolver specified when the publication and subscription were created).</span></span>  
  
3.  <span data-ttu-id="b5af9-149">선택적으로 대화형 해결 프로그램에 표시된 열을 편집한 다음 다음 단추 중 하나를 클릭하여 충돌을 해결합니다.</span><span class="sxs-lookup"><span data-stu-id="b5af9-149">Optionally edit any of the columns displayed in the Interactive Resolver, and then click one of the following buttons to resolve the conflict:</span></span>  
  
    -   <span data-ttu-id="b5af9-150">**제안 허용**</span><span class="sxs-lookup"><span data-stu-id="b5af9-150">**Accept Suggested**</span></span>  
  
    -   <span data-ttu-id="b5af9-151">**게시자 허용**</span><span class="sxs-lookup"><span data-stu-id="b5af9-151">**Accept Publisher**</span></span>  
  
    -   <span data-ttu-id="b5af9-152">**구독자 허용**</span><span class="sxs-lookup"><span data-stu-id="b5af9-152">**Accept Subscriber**</span></span>  
  
    -   <span data-ttu-id="b5af9-153">**모든 충돌 자동 해결** - 추가 입력 없이 현재 모든 충돌이 해결됩니다.</span><span class="sxs-lookup"><span data-stu-id="b5af9-153">**Resolve All Automatically** (all current conflicts are resolved without further input)</span></span>  
  
     <span data-ttu-id="b5af9-154">그러면 선택한 행이 게시자 및/또는 구독자에 적용되고 후속 동기화 중에 토폴로지에 있는 다른 노드로 전파됩니다.</span><span class="sxs-lookup"><span data-stu-id="b5af9-154">The selected row is then applied to the Publisher and/or Subscriber; it is propagated to other nodes in the topology during subsequent synchronizations.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b5af9-155">편집을 수행한 경우에는 편집 내용이 해결을 위해 선택한 행의 일부인 경우에만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="b5af9-155">Edits are only applied if they are part of the row that is chosen for resolution.</span></span> <span data-ttu-id="b5af9-156">예를 들어 **게시자**에서 편집을 수행한 다음 **구독자 허용**을 클릭하면 편집 내용이 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b5af9-156">For example, if you make edits under **Publisher**, and then click **Accept Subscriber**, the edits are discarded.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5af9-157">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b5af9-157">See Also</span></span>  
 [<span data-ttu-id="b5af9-158">Interactive Conflict Resolution</span><span class="sxs-lookup"><span data-stu-id="b5af9-158">Interactive Conflict Resolution</span></span>](merge/advanced-merge-replication-conflict-interactive-resolution.md)  
  
