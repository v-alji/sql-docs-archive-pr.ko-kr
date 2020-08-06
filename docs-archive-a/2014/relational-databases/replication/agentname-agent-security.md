---
title: '&lt;AgentName&gt; 에이전트 보안 | Microsoft 문서'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newsubwizard.agentnameagentsecurity.f1
ms.assetid: d34c7ef8-cf77-4ffd-887f-3c4214dfd71e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: fc72d4380b4d1980da30b8445596e1919a859e31
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661064"
---
# <a name="ltagentnamegt-agent-security"></a><span data-ttu-id="ca01c-102">&lt;AgentName&gt; 에이전트 보안</span><span class="sxs-lookup"><span data-stu-id="ca01c-102">&lt;AgentName&gt; Agent Security</span></span>
  <span data-ttu-id="ca01c-103">**\<AgentName> 에이전트 보안** 페이지를 사용하여 배포 에이전트(트랜잭션 및 스냅샷 복제의 경우) 또는 병합 에이전트(병합 복제의 경우)를 실행하고 복제 토폴로지의 컴퓨터에 연결하는 계정을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ca01c-103">The **\<AgentName> Agent Security** page allows you to specify the accounts under which the Distribution Agent (for transactional and snapshot replication) or Merge Agent (for merge replication) run and make connections to the computers in a replication topology.</span></span> <span data-ttu-id="ca01c-104">에이전트에 필요한 사용 권한 및 복제 보안을 위한 최선의 구현 방법은 [Replication Agent Security Model(복제 에이전트 보안 모델)](security/replication-agent-security-model.md) 및 [Replication Security Best Practices](security/replication-security-best-practices.md)(복제 보안 모범 사례)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ca01c-104">For information on permissions required by agents and best practices for replication security, see [Replication Agent Security Model](security/replication-agent-security-model.md) and [Replication Security Best Practices](security/replication-security-best-practices.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="ca01c-105">옵션</span><span class="sxs-lookup"><span data-stu-id="ca01c-105">Options</span></span>  
 <span data-ttu-id="ca01c-106">각 구독자에 대한 행의 속성 단추 ( **...** )를 클릭하여 **배포 에이전트 보안** 또는 **병합 에이전트 보안** 대화 상자에 액세스합니다.</span><span class="sxs-lookup"><span data-stu-id="ca01c-106">Click the properties button (**...**) in the row for each Subscriber to access the **Distribution Agent Security** or **Merge Agent Security** dialog box.</span></span> <span data-ttu-id="ca01c-107">해당 에이전트에서 사용하는 계정에 필요한 사용 권한에 대한 자세한 내용을 보려면 대화 상자에서 **도움말** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ca01c-107">Click **Help** on the dialog box that is launched for more information on the permissions required for accounts used by the agents.</span></span>  
  
 <span data-ttu-id="ca01c-108">대화 상자에서 설정을 입력하면 구독자에 대한 연결 정보가 표에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="ca01c-108">After settings have been entered in one of the dialog boxes, connection information for the Subscriber is displayed in the grid.</span></span>  
  
 <span data-ttu-id="ca01c-109">**구독자 에이전트**</span><span class="sxs-lookup"><span data-stu-id="ca01c-109">**Agent for Subscriber**</span></span>  
 <span data-ttu-id="ca01c-110">각 구독자의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="ca01c-110">The name of each Subscriber.</span></span>  
  
 <span data-ttu-id="ca01c-111">**배포자에 대한 연결**</span><span class="sxs-lookup"><span data-stu-id="ca01c-111">**Connection to Distributor**</span></span>  
 <span data-ttu-id="ca01c-112">트랜잭션 및 스냅샷 복제에 대해 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="ca01c-112">Displayed for transactional and snapshot replication.</span></span> <span data-ttu-id="ca01c-113">배포자에 대한 연결이 설정되는 컨텍스트입니다.</span><span class="sxs-lookup"><span data-stu-id="ca01c-113">The context under which the connection to the Distributor is made.</span></span> <span data-ttu-id="ca01c-114">로컬 연결은 항상 에이전트가 실행되는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 계정의 컨텍스트를 사용하여 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="ca01c-114">Local connections are always made using the context of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows account under which the agent runs:</span></span>  
  
-   <span data-ttu-id="ca01c-115">밀어넣기 구독의 경우 로컬 연결은 배포자에 대한 연결이므로 이 필드는 항상 푸시 구독에 대한 **Impersonate '\<Domain>\\<Login\>'** 또는 **Impersonate '\<Computer>\\<Login\>'** 을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="ca01c-115">For push subscriptions, the local connection is the connection to the Distributor, so this field will always display: **Impersonate '\<Domain>\\<Login\>'** or **Impersonate '\<Computer>\\<Login\>'** for push subscriptions.</span></span>  
  
-   <span data-ttu-id="ca01c-116">끌어오기 구독의 경우 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그인의 컨텍스트로 연결할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ca01c-116">For pull subscriptions, the connection can also be made under the context of a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login.</span></span> <span data-ttu-id="ca01c-117">이 필드는 **로그인 '\<Login>'** , **Impersonate '\<Domain>\\<Login\>'** or **Impersonate '\<Computer>\\<Login\>'** 을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ca01c-117">The field displays one of the following: **Use login '\<Login>'**, **Impersonate '\<Domain>\\<Login\>'** or **Impersonate '\<Computer>\\<Login\>'**.</span></span> [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="ca01c-118">에서는 Windows 계정의 컨텍스트를 사용하여 모든 연결을 설정할 것을 권장합니다.</span><span class="sxs-lookup"><span data-stu-id="ca01c-118">recommends that all connections be made using the context of the Windows account.</span></span>  
  
 <span data-ttu-id="ca01c-119">**게시자 및 배포자에 연결**</span><span class="sxs-lookup"><span data-stu-id="ca01c-119">**Connection to Publisher & Distributor**</span></span>  
 <span data-ttu-id="ca01c-120">병합 복제에 대해 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="ca01c-120">Displayed for merge replication.</span></span> <span data-ttu-id="ca01c-121">게시자 및 배포자에 대한 연결이 설정되는 컨텍스트입니다.</span><span class="sxs-lookup"><span data-stu-id="ca01c-121">The context under which the connections to the Publisher and Distributor are made.</span></span> <span data-ttu-id="ca01c-122">로컬 연결은 항상 에이전트가 실행되는 Windows 계정의 컨텍스트를 사용하여 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="ca01c-122">Local connections are always made using the context of the Windows account under which the agent runs:</span></span>  
  
-   <span data-ttu-id="ca01c-123">밀어넣기 구독의 경우 로컬 연결은 게시자 및 배포자에 대한 연결이므로 이 필드는 항상 푸시 구독에 대한 **Impersonate '\<Domain>\\<Login\>'** 또는 **Impersonate '\<Computer>\\<Login\>'** 을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="ca01c-123">For push subscriptions, the local connection is the connection to the Publisher and Distributor, so this field will always display: **Impersonate '\<Domain>\\<Login\>'** or **Impersonate '\<Computer>\\<Login\>'** for push subscriptions.</span></span>  
  
-   <span data-ttu-id="ca01c-124">끌어오기 구독의 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그인의 컨텍스트로 연결할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ca01c-124">For pull subscriptions, the connection can also be made under the context of a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login.</span></span> <span data-ttu-id="ca01c-125">이 필드는 **로그인 '\<Login>'** , **Impersonate '\<Domain>\\<Login\>'** or **Impersonate '\<Computer>\\<Login\>'** 을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ca01c-125">The field displays one of the following: **Use login '\<Login>'**, **Impersonate '\<Domain>\\<Login\>'** or **Impersonate '\<Computer>\\<Login\>'**.</span></span> [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="ca01c-126">에서는 Windows 계정의 컨텍스트를 사용하여 모든 연결을 설정할 것을 권장합니다.</span><span class="sxs-lookup"><span data-stu-id="ca01c-126">recommends that all connections be made using the context of the Windows account.</span></span>  
  
 <span data-ttu-id="ca01c-127">**구독자에 대한 연결**</span><span class="sxs-lookup"><span data-stu-id="ca01c-127">**Connection to Subscriber**</span></span>  
 <span data-ttu-id="ca01c-128">구독자에 대한 연결이 설정되는 컨텍스트입니다.</span><span class="sxs-lookup"><span data-stu-id="ca01c-128">The context under which the connection to the Subscriber is made.</span></span> <span data-ttu-id="ca01c-129">로컬 연결은 항상 에이전트가 실행되는 Windows 계정의 컨텍스트를 사용하여 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="ca01c-129">Local connections are always made using the context of the Windows account under which the agent runs:</span></span>  
  
-   <span data-ttu-id="ca01c-130">끌어오기 구독의 경우 로컬 연결은 구독자에 대한 연결이므로 이 필드는 항상 푸시 구독에 대한 **Impersonate '\<Domain>\\<Login\>'** 또는 **Impersonate '\<Computer>\\<Login\>'** 을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="ca01c-130">For pull subscriptions, the local connection is the connection to the Subscriber, so this field will always display: **Impersonate '\<Domain>\\<Login\>'** or **Impersonate '\<Computer>\\<Login\>'** for push subscriptions.</span></span>  
  
-   <span data-ttu-id="ca01c-131">밀어넣기 구독의 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그인의 컨텍스트로 연결할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ca01c-131">For push subscriptions, the connection can also be made under the context of a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login.</span></span> <span data-ttu-id="ca01c-132">이 필드는 **로그인 '\<Login>'** , **Impersonate '\<Domain>\\<Login\>'** or **Impersonate '\<Computer>\\<Login\>'** 을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ca01c-132">The field displays one of the following: **Use login '\<Login>'**, **Impersonate '\<Domain>\\<Login\>'** or **Impersonate '\<Computer>\\<Login\>'**.</span></span> [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="ca01c-133">에서는 Windows 계정의 컨텍스트를 사용하여 모든 연결을 설정할 것을 권장합니다.</span><span class="sxs-lookup"><span data-stu-id="ca01c-133">recommends that all connections be made using the context of the Windows account.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca01c-134">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ca01c-134">See Also</span></span>  
 <span data-ttu-id="ca01c-135">[끌어오기 구독 속성 보기 및 수정](view-and-modify-pull-subscription-properties.md) </span><span class="sxs-lookup"><span data-stu-id="ca01c-135">[View and Modify Pull Subscription Properties](view-and-modify-pull-subscription-properties.md) </span></span>  
 <span data-ttu-id="ca01c-136">[밀어넣기 구독 속성 보기 및 수정](view-and-modify-push-subscription-properties.md) </span><span class="sxs-lookup"><span data-stu-id="ca01c-136">[View and Modify Push Subscription Properties](view-and-modify-push-subscription-properties.md) </span></span>  
 <span data-ttu-id="ca01c-137">[복제의 로그인 및 암호 관리](security/identity-and-access-control-replication.md#manage-logins-and-passwords-in-replication) </span><span class="sxs-lookup"><span data-stu-id="ca01c-137">[Manage Logins and Passwords in Replication](security/identity-and-access-control-replication.md#manage-logins-and-passwords-in-replication) </span></span>  
 <span data-ttu-id="ca01c-138">[복제 에이전트 보안 모델](security/replication-agent-security-model.md) </span><span class="sxs-lookup"><span data-stu-id="ca01c-138">[Replication Agent Security Model](security/replication-agent-security-model.md) </span></span>  
 [<span data-ttu-id="ca01c-139">SQL Server 복제 보안</span><span class="sxs-lookup"><span data-stu-id="ca01c-139">SQL Server Replication Security</span></span>](security/view-and-modify-replication-security-settings.md)  
  
  
