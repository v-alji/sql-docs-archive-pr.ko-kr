---
title: 병합 에이전트 보안 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.security.MA.f1
helpviewer_keywords:
- Merge Agent Security dialog box
ms.assetid: 9b86171a-4381-4b39-869a-cdc161e7cd15
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ecbb044ca87ccfc74c5cb39a016667d15cf7a859
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734015"
---
# <a name="merge-agent-security"></a><span data-ttu-id="f5c53-102">병합 에이전트 보안</span><span class="sxs-lookup"><span data-stu-id="f5c53-102">Merge Agent Security</span></span>
  <span data-ttu-id="f5c53-103">**병합 에이전트 보안** 대화 상자를 사용하여 병합 에이전트를 실행하는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 계정을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f5c53-103">The **Merge Agent Security** dialog box allows you to specify the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows account under which the Merge Agent runs.</span></span> <span data-ttu-id="f5c53-104">병합 에이전트는 밀어넣기 구독의 경우에는 배포자에서, 끌어오기 구독의 경우에는 구독자에서 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="f5c53-104">The Merge Agent runs at the Distributor for push subscriptions and at the Subscriber for pull subscriptions.</span></span> <span data-ttu-id="f5c53-105">Windows 계정으로 에이전트 프로세스가 실행되기 때문에 이 계정을 *프로세스 계정*이라고도 합니다.</span><span class="sxs-lookup"><span data-stu-id="f5c53-105">The Windows account is also referred to as the *process account*, because the agent process runs under this account.</span></span> <span data-ttu-id="f5c53-106">이 대화 상자에서 사용 가능한 추가 옵션은 대화 상자에 액세스하는 방법에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="f5c53-106">Additional options available in the dialog box depend on how you access it:</span></span>  
  
-   <span data-ttu-id="f5c53-107">새 구독 마법사에서 이 대화 상자에 액세스하는 경우에는 구독자(밀어넣기 구독의 경우) 또는 게시자 및 배포자(끌어오기 구독의 경우)에 병합 에이전트를 연결하는 컨텍스트도 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f5c53-107">If the dialog box is accessed from the New Subscription Wizard, it also allows you to specify the context under which the Merge Agent makes connections to the Subscriber (for push subscriptions) or the Publisher and Distributor (for pull subscriptions).</span></span> <span data-ttu-id="f5c53-108">Windows 계정을 사용하거나 지정한 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 계정의 컨텍스트에서 연결을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f5c53-108">The connection can be made using the Windows account or under the context of a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account you specify.</span></span>  
  
-   <span data-ttu-id="f5c53-109">**구독 속성** 대화 상자에서 이 대화 상자에 액세스하는 경우에는 해당 대화 상자의**구독자 연결**또는 **게시자 연결** 행의 속성 단추 ( **...** )를 클릭하여 병합 에이전트를 연결하는 컨텍스트를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f5c53-109">If the dialog box is accessed from the **Subscription Properties** dialog box, specify the context under which the Merge Agent makes connections by clicking the properties button (**...**) in the **Subscriber Connection** or **Publisher Connection** row of that dialog box.</span></span> <span data-ttu-id="f5c53-110">**구독 속성** 대화 상자에 액세스하는 방법은 [밀어넣기 구독 속성 보기 및 수정](view-and-modify-push-subscription-properties.md) 및 방법: [끌어오기 구독 속성 보기 및 수정](view-and-modify-pull-subscription-properties.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f5c53-110">For more information about accessing the **Subscription Properties** dialog box, see [View and Modify Push Subscription Properties](view-and-modify-push-subscription-properties.md) and how to: [View and Modify Pull Subscription Properties](view-and-modify-pull-subscription-properties.md).</span></span>  
  
 <span data-ttu-id="f5c53-111">모든 계정이 유효해야 하며 각 계정에 대해 올바른 암호를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f5c53-111">All accounts must be valid, with the correct password specified for each account.</span></span> <span data-ttu-id="f5c53-112">계정 및 암호의 유효성은 에이전트를 실행할 때 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="f5c53-112">Accounts and passwords are not validated until an agent runs.</span></span>  
  
## <a name="options"></a><span data-ttu-id="f5c53-113">옵션</span><span class="sxs-lookup"><span data-stu-id="f5c53-113">Options</span></span>  
 <span data-ttu-id="f5c53-114">**Process Account**</span><span class="sxs-lookup"><span data-stu-id="f5c53-114">**Process Account**</span></span>  
 <span data-ttu-id="f5c53-115">병합 에이전트를 실행하는 Windows 계정을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="f5c53-115">Enter a Windows account under which the Merge Agent runs.</span></span>  
  
-   <span data-ttu-id="f5c53-116">밀어넣기 구독의 경우 계정이 다음 조건을 만족해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f5c53-116">For push subscriptions, the account must:</span></span>  
  
    -   <span data-ttu-id="f5c53-117">적어도 배포 데이터베이스에 포함된 **db_owner** 고정 데이터베이스 역할의 멤버여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f5c53-117">At minimum be a member of the **db_owner** fixed database role in the distribution database.</span></span>  
  
    -   <span data-ttu-id="f5c53-118">PAL의 멤버여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f5c53-118">Be a member of the PAL.</span></span>  
  
    -   <span data-ttu-id="f5c53-119">게시 데이터베이스의 사용자와 연결된 로그인이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f5c53-119">Be a login associated with a user in the publication database.</span></span>  
  
    -   <span data-ttu-id="f5c53-120">스냅샷 공유에 대해 읽기 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f5c53-120">Have read permissions on the snapshot share.</span></span>  
  
-   <span data-ttu-id="f5c53-121">끌어오기 구독의 경우 계정이 적어도 구독 데이터베이스에 포함된 **db_owner** 고정 데이터베이스 역할의 멤버여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f5c53-121">For pull subscriptions, the account must at minimum be a member of the **db_owner** fixed database role in the subscription database.</span></span>  
  
 <span data-ttu-id="f5c53-122">연결을 설정할 때 프로세스 계정을 가장하면 추가 사용 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="f5c53-122">Additional permissions are required if the process account is impersonated when connections are made.</span></span> <span data-ttu-id="f5c53-123">아래의 **게시자 및 배포자에 연결** 섹션과 **구독자에 연결** 섹션을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="f5c53-123">See the **Connect to the Publisher and Distributor** and **Connect to the Subscriber** sections below.</span></span>  
  
 <span data-ttu-id="f5c53-124">병합 에이전트가 **인스턴스에서 실행되지 않기 때문에** [!INCLUDE[msCoName](../../includes/msconame-md.md)]에 대한 끌어오기 구독에 [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]프로세스 계정[!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]을 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f5c53-124">**Process Account** cannot be specified for pull subscriptions to [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)], because the Merge Agent does not run on instances of [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)].</span></span>  
  
 <span data-ttu-id="f5c53-125">**암호** 및 **암호 확인**</span><span class="sxs-lookup"><span data-stu-id="f5c53-125">**Password** and **Confirm Password**</span></span>  
 <span data-ttu-id="f5c53-126">Windows 계정의 암호를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="f5c53-126">Enter the password for the Windows account.</span></span>  
  
 <span data-ttu-id="f5c53-127">**게시자 및 배포자에 연결**</span><span class="sxs-lookup"><span data-stu-id="f5c53-127">**Connect to the Publisher and Distributor**</span></span>  
 <span data-ttu-id="f5c53-128">밀어넣기 구독의 경우 항상 **프로세스 계정** 입력란에 지정한 계정을 가장하여 게시자 및 배포자에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="f5c53-128">For push subscriptions, connections to the Publisher and Distributor are always made by impersonating the account specified in the **Process account** text box.</span></span>  
  
 <span data-ttu-id="f5c53-129">끌어오기 구독의 경우 병합 에이전트를 게시자 및 배포자에 연결할 때 **프로세스 계정** 입력란에 지정한 계정을 가장할지, 아니면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 계정을 사용할 것인지를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f5c53-129">For pull subscriptions, select whether the Merge Agent should make connections to the Publisher and Distributor by impersonating the account specified in the **Process account** text box or by using a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account.</span></span> <span data-ttu-id="f5c53-130">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 계정을 사용하도록 선택한 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그인과 암호를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="f5c53-130">If you select to use a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account, enter a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login and password.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="f5c53-131">에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 계정을 사용하는 대신 Windows 계정을 가장하도록 선택할 것을 권장합니다.</span><span class="sxs-lookup"><span data-stu-id="f5c53-131">recommends that you select to impersonate the Windows account rather than using a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account.</span></span>  
  
 <span data-ttu-id="f5c53-132">연결에 사용할 Windows 계정 또는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 계정은 다음 조건을 만족해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f5c53-132">The Windows account or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account used for the connection must:</span></span>  
  
-   <span data-ttu-id="f5c53-133">PAL의 멤버여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f5c53-133">Be a member of the PAL.</span></span>  
  
-   <span data-ttu-id="f5c53-134">게시 데이터베이스의 사용자와 연결된 로그인이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f5c53-134">Be a login associated with a user in the publication database.</span></span>  
  
-   <span data-ttu-id="f5c53-135">배포 데이터베이스의 사용자와 연결된 로그인이어야 합니다. 사용자는 게스트 사용자일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f5c53-135">Be a login associated with a user in the distribution database (the user can be the Guest user).</span></span>  
  
-   <span data-ttu-id="f5c53-136">스냅샷 공유에 대해 읽기 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f5c53-136">Have read permissions on the snapshot share.</span></span>  
  
 <span data-ttu-id="f5c53-137">**구독자에 연결**</span><span class="sxs-lookup"><span data-stu-id="f5c53-137">**Connect to the Subscriber**</span></span>  
 <span data-ttu-id="f5c53-138">끌어오기 구독의 경우 항상 **프로세스 계정** 입력란에 지정한 계정을 가장하여 구독자에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="f5c53-138">For pull subscriptions, connections to the Subscriber are always made by impersonating the account specified in the **Process account** text box.</span></span>  
  
 <span data-ttu-id="f5c53-139">밀어넣기 구독의 경우 병합 에이전트를 게시자 및 배포자에 연결할 때 **프로세스 계정** 입력란에 지정한 계정을 가장할지, 아니면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 계정을 사용할 것인지를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f5c53-139">For push subscriptions, select whether the Merge Agent should make connections to the Publisher and Distributor by impersonating the account specified in the **Process account** text box or by using a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account.</span></span> <span data-ttu-id="f5c53-140">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 계정을 사용하도록 선택한 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그인과 암호를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="f5c53-140">If you select to use a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account, enter a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login and password.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f5c53-141">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 계정을 사용하는 것보다 Windows 계정을 가장하도록 선택하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="f5c53-141">It is recommended that you select to impersonate the Windows account rather than using a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account.</span></span>  
  
 <span data-ttu-id="f5c53-142">구독자 연결에 사용되는 Windows 계정 또는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 계정은 적어도 구독 데이터베이스에 포함된 **db_owner** 고정 데이터베이스 역할의 멤버여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f5c53-142">The Windows account or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account used for the connection to the Subscriber must at minimum be a member of the **db_owner** fixed database role in the subscription database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5c53-143">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f5c53-143">See Also</span></span>  
 <span data-ttu-id="f5c53-144">[복제의 로그인 및 암호 관리](security/identity-and-access-control-replication.md#manage-logins-and-passwords-in-replication) </span><span class="sxs-lookup"><span data-stu-id="f5c53-144">[Manage Logins and Passwords in Replication](security/identity-and-access-control-replication.md#manage-logins-and-passwords-in-replication) </span></span>  
 <span data-ttu-id="f5c53-145">[복제 에이전트 보안 모델](security/replication-agent-security-model.md) </span><span class="sxs-lookup"><span data-stu-id="f5c53-145">[Replication Agent Security Model](security/replication-agent-security-model.md) </span></span>  
 <span data-ttu-id="f5c53-146">[복제 에이전트 개요](agents/replication-agents-overview.md) </span><span class="sxs-lookup"><span data-stu-id="f5c53-146">[Replication Agents Overview](agents/replication-agents-overview.md) </span></span>  
 <span data-ttu-id="f5c53-147">[Replication Security Best Practices](security/replication-security-best-practices.md) </span><span class="sxs-lookup"><span data-stu-id="f5c53-147">[Replication Security Best Practices](security/replication-security-best-practices.md) </span></span>  
 [<span data-ttu-id="f5c53-148">게시 구독</span><span class="sxs-lookup"><span data-stu-id="f5c53-148">Subscribe to Publications</span></span>](subscribe-to-publications.md)  
  
  
