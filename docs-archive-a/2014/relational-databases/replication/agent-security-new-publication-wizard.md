---
title: 에이전트 보안(새 게시 마법사) | Microsoft 문서
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.agentsecurity.articles.f1
ms.assetid: 05ae44df-8e9f-46ea-95f6-972ad109c6c0
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6a0da30cb49a73024ca83d8587a4f6477d21c49c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648959"
---
# <a name="agent-security-new-publication-wizard"></a><span data-ttu-id="84454-102">에이전트 보안(새 게시 마법사)</span><span class="sxs-lookup"><span data-stu-id="84454-102">Agent Security (New Publication Wizard)</span></span>
  <span data-ttu-id="84454-103">**에이전트 보안** 페이지를 사용하여 다음 에이전트를 실행하고 복제 토폴로지의 컴퓨터에 연결할 때 사용되는 계정을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84454-103">The **Agent Security** page allows you to specify the accounts under which the following agents run and make connections to the computers in a replication topology:</span></span>  
  
-   <span data-ttu-id="84454-104">모든 게시에 대한 스냅샷 에이전트입니다.</span><span class="sxs-lookup"><span data-stu-id="84454-104">The Snapshot Agent for all publications.</span></span>  
  
-   <span data-ttu-id="84454-105">모든 트랜잭션 게시에 대한 로그 판독기 에이전트입니다.</span><span class="sxs-lookup"><span data-stu-id="84454-105">The Log Reader Agent for all transactional publications.</span></span>  
  
-   <span data-ttu-id="84454-106">업데이트할 수 있는 구독을 허용하는 트랜잭션 게시에 대한 큐 판독기 에이전트입니다.</span><span class="sxs-lookup"><span data-stu-id="84454-106">The Queue Reader Agent for transactional publications that allow updatable subscriptions.</span></span> <span data-ttu-id="84454-107">**게시 유형** 페이지에서 **업데이트할 수 있는 구독이 있는 트랜잭션 게시**를 지정하면 사용하는 업데이트할 수 있는 구독 유형과 관계없이 이 에이전트에 대해 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 작업이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="84454-107">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job for this agent is created if you specified **Transactional publication with updatable subscriptions** on the **Publication Type** page, regardless of the type of updatable subscriptions you use.</span></span> <span data-ttu-id="84454-108">업데이트할 수 있는 구독에 대한 자세한 내용은 [Updatable Subscriptions for Transactional Replication](transactional/updatable-subscriptions-for-transactional-replication.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="84454-108">For more information about updatable subscriptions, see [Updatable Subscriptions for Transactional Replication](transactional/updatable-subscriptions-for-transactional-replication.md).</span></span>  
  
 <span data-ttu-id="84454-109">에이전트에 필요한 사용 권한 및 복제 보안을 위한 최선의 구현 방법은 [Replication Agent Security Model](security/replication-agent-security-model.md) 및 [Replication Security Best Practices](security/replication-security-best-practices.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="84454-109">For information about permissions required by agents and best practices for replication security, see [Replication Agent Security Model](security/replication-agent-security-model.md) and [Replication Security Best Practices](security/replication-security-best-practices.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="84454-110">옵션</span><span class="sxs-lookup"><span data-stu-id="84454-110">Options</span></span>  
 <span data-ttu-id="84454-111">**스냅샷 에이전트**</span><span class="sxs-lookup"><span data-stu-id="84454-111">**Snapshot Agent**</span></span>  
 <span data-ttu-id="84454-112">모든 게시에 대해 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="84454-112">Displayed for all publications.</span></span> <span data-ttu-id="84454-113">**보안 설정** 을 클릭하여 **스냅샷 에이전트 보안** 대화 상자에서 보안 설정을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84454-113">Click **Security Settings** to specify security settings in the **Snapshot Agent Security** dialog box.</span></span>  
  
 <span data-ttu-id="84454-114">스냅샷 에이전트에서 사용하는 계정에 필요한 사용 권한을 보려면 **스냅샷 에이전트 보안** 대화 상자에서 **도움말** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="84454-114">Click **Help** on the **Snapshot Agent Security** dialog box for more information about the permissions required for accounts used by the Snapshot Agent.</span></span>  
  
 <span data-ttu-id="84454-115">**로그 판독기 에이전트**</span><span class="sxs-lookup"><span data-stu-id="84454-115">**Log Reader Agent**</span></span>  
 <span data-ttu-id="84454-116">모든 트랜잭션 게시에 대해 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="84454-116">Displayed for all transactional publications.</span></span> <span data-ttu-id="84454-117">**보안 설정** 을 클릭하여 **로그 판독기 에이전트 보안** 대화 상자에서 보안 설정을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84454-117">Click **Security Settings** to specify security settings in the **Log Reader Agent Security** dialog box.</span></span>  
  
 <span data-ttu-id="84454-118">로그 판독기 에이전트에서 사용하는 계정에 필요한 사용 권한을 보려면 **로그 판독기 에이전트 보안** 대화 상자에서 **도움말** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="84454-118">Click **Help** on the **Log Reader Agent Security** dialog box for more information about the permissions required for accounts used by the Log Reader Agent.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="84454-119">트랜잭션 복제를 사용하여 게시된 각 데이터베이스에 대해 하나의 로그 판독기 에이전트가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84454-119">There is one Log Reader Agent for each database that is published using transactional replication.</span></span> <span data-ttu-id="84454-120">데이터베이스에 트랜잭션 게시가 이미 있으면 보안 설정은 읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="84454-120">If a transactional publication already exists in the database, the security settings are read-only.</span></span> <span data-ttu-id="84454-121">**게시 속성** 대화 상자에서 설정을 변경할 수 있지만 이 변경 내용은 데이터베이스의 모든 트랜잭션 게시에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="84454-121">You can change the settings in the **Publication Properties** dialog box, but changes affect all transactional publications in the database.</span></span>  
  
 <span data-ttu-id="84454-122">**큐 판독기 에이전트**</span><span class="sxs-lookup"><span data-stu-id="84454-122">**Queue Reader Agent**</span></span>  
 <span data-ttu-id="84454-123">업데이트할 수 있는 구독을 허용하는 트랜잭션 게시에 대해 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="84454-123">Displayed for transactional publications that allow updatable subscriptions.</span></span> <span data-ttu-id="84454-124">**보안 설정** 을 클릭하여 **큐 판독기 에이전트 보안** 대화 상자에서 보안 설정을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84454-124">Click **Security Settings** to specify security settings in the **Queue Reader Agent Security** dialog box.</span></span> <span data-ttu-id="84454-125">이 마법사를 완료하면 큐 판독기 에이전트 작업이 생성됩니다. 지연 업데이트 구독의 생성 여부와는 관계가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="84454-125">A Queue Reader Agent job is created when this wizard completes; it does not depend on you creating any queued updating subscriptions.</span></span> <span data-ttu-id="84454-126">지연 업데이트 구독을 만들지 않으려면 이 작업을 해제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84454-126">If you do not plan to create any queued updating subscriptions, you can disable the job.</span></span> <span data-ttu-id="84454-127">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 **Jobs** 폴더에서 작업( *[\<Publisher>].\<integer>* . 형식의 이름)을 마우스 오른쪽 단추로 클릭한 다음 **사용 안 함**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="84454-127">Right-click the job (named in the form: *[\<Publisher>].\<integer>*.) in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent **Jobs** folder, and then click **Disable**.</span></span>  
  
 <span data-ttu-id="84454-128">큐 판독기 에이전트에서 사용하는 계정에 필요한 사용 권한을 보려면 **큐 판독기 에이전트 보안** 대화 상자에서 **도움말** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="84454-128">Click **Help** on the **Queue Reader Agent Security** dialog box for more information about the permissions required for accounts used by the Queue Reader Agent.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="84454-129">각 배포 데이터베이스 및 이 데이터베이스에서 처리하는 모든 게시자에 대해 하나의 큐 판독기 에이전트가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84454-129">There is one Queue Reader Agent for each distribution database (and all Publishers that it serves).</span></span> <span data-ttu-id="84454-130">지정된 배포 데이터베이스를 사용하는 게시자에 지연 업데이트 구독을 허용하는 트랜잭션 게시가 이미 있으면 보안 설정은 읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="84454-130">If a transactional publication that allows queued updating subscriptions already exists on any of the Publishers that use a given distribution database, the security settings are read-only.</span></span> <span data-ttu-id="84454-131">**배포자 속성** 대화 상자에서 큐 판독기 에이전트를 실행 및 연결할 때 사용되는 계정을 변경할 수 있지만 이 변경 내용은 해당 배포 데이터베이스를 사용하는 모든 게시자에서의 게시에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="84454-131">You can change the account under which the Queue Reader Agent runs and makes connections in the **Distributor Properties** dialog box, but changes affect publications at all Publishers that use the distribution database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84454-132">참고 항목</span><span class="sxs-lookup"><span data-stu-id="84454-132">See Also</span></span>  
 <span data-ttu-id="84454-133">[Create a Publication](publish/create-a-publication.md) </span><span class="sxs-lookup"><span data-stu-id="84454-133">[Create a Publication](publish/create-a-publication.md) </span></span>  
 <span data-ttu-id="84454-134">[Create an Updatable Subscription to a Transactional Publication](publish/create-an-updatable-subscription-to-a-transactional-publication.md) </span><span class="sxs-lookup"><span data-stu-id="84454-134">[Create an Updatable Subscription to a Transactional Publication](publish/create-an-updatable-subscription-to-a-transactional-publication.md) </span></span>  
 <span data-ttu-id="84454-135">[배포자 및 게시자 속성 보기 및 수정](view-and-modify-distributor-and-publisher-properties.md) </span><span class="sxs-lookup"><span data-stu-id="84454-135">[View and Modify Distributor and Publisher Properties](view-and-modify-distributor-and-publisher-properties.md) </span></span>  
 <span data-ttu-id="84454-136">[게시 속성 보기 및 수정](publish/view-and-modify-publication-properties.md) </span><span class="sxs-lookup"><span data-stu-id="84454-136">[View and Modify Publication Properties](publish/view-and-modify-publication-properties.md) </span></span>  
 <span data-ttu-id="84454-137">[복제의 로그인 및 암호 관리](security/identity-and-access-control-replication.md#manage-logins-and-passwords-in-replication) </span><span class="sxs-lookup"><span data-stu-id="84454-137">[Manage Logins and Passwords in Replication](security/identity-and-access-control-replication.md#manage-logins-and-passwords-in-replication) </span></span>  
 <span data-ttu-id="84454-138">[데이터 및 데이터베이스 개체 게시](publish/publish-data-and-database-objects.md) </span><span class="sxs-lookup"><span data-stu-id="84454-138">[Publish Data and Database Objects](publish/publish-data-and-database-objects.md) </span></span>  
 [<span data-ttu-id="84454-139">복제 에이전트 개요</span><span class="sxs-lookup"><span data-stu-id="84454-139">Replication Agents Overview</span></span>](agents/replication-agents-overview.md)  
  
  
