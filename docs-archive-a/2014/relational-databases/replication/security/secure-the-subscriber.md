---
title: 구독자 보안 설정 | Microsoft 문서
ms.custom: ''
ms.date: 04/26/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- subscriptions [SQL Server replication], security
- Subscribers [SQL Server replication], security
- security [SQL Server replication], Subscribers
ms.assetid: c8f0d62a-8b5d-4a21-9aec-223da52bb708
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 1f03b9a202c3c49f147368460518a579f28dc850
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653266"
---
# <a name="secure-the-subscriber"></a><span data-ttu-id="ef77d-102">구독자 보안 설정</span><span class="sxs-lookup"><span data-stu-id="ef77d-102">Secure the Subscriber</span></span>
  <span data-ttu-id="ef77d-103">병합 에이전트 및 배포 에이전트는 구독자에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="ef77d-103">Merge Agents and Distribution Agents connect to the Subscriber.</span></span> <span data-ttu-id="ef77d-104">이러한 연결은 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 로그인 또는 Windows 로그인의 컨텍스트에서 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="ef77d-104">These connections can be made under the context of a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] login or a Windows login.</span></span> <span data-ttu-id="ef77d-105">필요한 최소 권한만 부여하는 원칙을 따르고 모든 암호 스토리지를 보호하면서 이러한 에이전트에 적절한 로그인을 제공하는 것이 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="ef77d-105">It is important to provide an appropriate login for these agents while following the principle of granting the minimal rights necessary and also protecting the storage of all passwords.</span></span> <span data-ttu-id="ef77d-106">각 에이전트에 필요한 사용 권한에 대한 자세한 내용은 [Replication Agent Security Model](replication-agent-security-model.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="ef77d-106">For information about the permissions required for each agent, see [Replication Agent Security Model](replication-agent-security-model.md).</span></span>  
  
## <a name="distribution-agent"></a><span data-ttu-id="ef77d-107">배포 에이전트</span><span class="sxs-lookup"><span data-stu-id="ef77d-107">Distribution Agent</span></span>  
 <span data-ttu-id="ef77d-108">구독당 배포 에이전트가 하나씩(독립 에이전트 - 새 게시 마법사에서 생성된 게시의 기본값임) 또는 한 쌍의 게시 데이터베이스와 구독 데이터베이스당 배포 에이전트가 하나씩(공유 에이전트) 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ef77d-108">There is either one Distribution Agent per subscription (an independent agent, the default for publications created in the New Publication Wizard) or one Distribution Agent per publication database and subscription database pair (a shared agent).</span></span> <span data-ttu-id="ef77d-109">T</span><span class="sxs-lookup"><span data-stu-id="ef77d-109">T</span></span>  
  
 <span data-ttu-id="ef77d-110">밀어넣기 구독에 대한 연결 정보를 지정하려면 [밀어넣기 구독 만들기](../create-a-push-subscription.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ef77d-110">To specify connection information for push subscriptions, see [Create a Push Subscription](../create-a-push-subscription.md).</span></span>  
  
 <span data-ttu-id="ef77d-111">끌어오기 구독에 대한 연결 정보를 지정하려면 [끌어오기 구독 만들기](../create-a-pull-subscription.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ef77d-111">To specify connection information for pull subscriptions, see [Create a Pull Subscription](../create-a-pull-subscription.md)</span></span>  
  
## <a name="merge-agent"></a><span data-ttu-id="ef77d-112">병합 에이전트</span><span class="sxs-lookup"><span data-stu-id="ef77d-112">Merge Agent</span></span>  
 <span data-ttu-id="ef77d-113">각 병합 구독에는 게시자 및 구독자 모두에 연결되고 모두를 업데이트하는 자체 병합 에이전트가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ef77d-113">Each merge subscription has its own Merge Agent that connects to and updates both the Publisher and the Subscriber.</span></span>  
  
 <span data-ttu-id="ef77d-114">밀어넣기 구독에 대한 연결 정보를 지정하려면 [밀어넣기 구독 만들기](../create-a-push-subscription.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ef77d-114">To specify connection information for push subscriptions, see [Create a Push Subscription](../create-a-push-subscription.md).</span></span>  
  
 <span data-ttu-id="ef77d-115">끌어오기 구독에 대한 연결 정보를 지정하려면 [끌어오기 구독 만들기](../create-a-pull-subscription.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ef77d-115">To specify connection information for pull subscriptions, see [Create a Pull Subscription](../create-a-pull-subscription.md).</span></span>  
  
## <a name="immediate-updating-subscriptions"></a><span data-ttu-id="ef77d-116">즉시 업데이트 구독</span><span class="sxs-lookup"><span data-stu-id="ef77d-116">Immediate Updating Subscriptions</span></span>  
 <span data-ttu-id="ef77d-117">즉시 업데이트 구독을 구성할 때는 게시자에 연결할 때 사용할 계정을 구독자에서 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ef77d-117">When you configure an immediate updating subscription, you specify an account at the Subscriber under which connections to the Publisher are made.</span></span> <span data-ttu-id="ef77d-118">이 연결은 구독자에서 발생되는 트리거에 사용되고 게시자로 변경 내용을 전파합니다.</span><span class="sxs-lookup"><span data-stu-id="ef77d-118">Connections are used by the triggers that fire at the Subscriber and propagate changes to the Publisher.</span></span> <span data-ttu-id="ef77d-119">연결 유형에 대해 3가지 옵션을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ef77d-119">There are three options available for the type of connection:</span></span>  
  
-   <span data-ttu-id="ef77d-120">복제가 만드는 연결된 서버 - 구성 시 지정하는 자격 증명으로 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="ef77d-120">A linked server that replication creates; the connection is made with the credentials you specify at configuration time.</span></span>  
  
-   <span data-ttu-id="ef77d-121">복제가 만드는 연결된 서버 - 구독자에서 변경 내용을 적용하는 사용자의 자격 증명으로 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="ef77d-121">A linked server that replication creates; the connection is made with the credentials of the user making the change at the Subscriber.</span></span>  
  
-   <span data-ttu-id="ef77d-122">이미 정의한 연결된 서버나 원격 서버</span><span class="sxs-lookup"><span data-stu-id="ef77d-122">A linked server or remote server that you have already defined.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="ef77d-123">연결 정보를 지정하려면 저장 프로시저 [sp_link_publication&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-link-publication-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ef77d-123">To specify connection information, use the stored procedure [sp_link_publication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-link-publication-transact-sql).</span></span> <span data-ttu-id="ef77d-124">또한 **sp_link_publication** 을 호출하는 새 구독 마법사의 **업데이트할 수 있는 구독에 대한 로그인**페이지를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ef77d-124">You can also use the **Login for Updatable Subscriptions** page of the New Subscription Wizard, which calls **sp_link_publication**.</span></span> <span data-ttu-id="ef77d-125">특정 상황에서는 구독자가 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] SP1(서비스 팩 1) 이상을 실행하고 게시자가 이전 버전을 실행할 경우 이 저장 프로시저가 실패할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ef77d-125">Under certain conditions, this stored procedure can fail if the Subscriber is running [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] Service Pack 1 (SP1) or later, and the Publisher is running an earlier version.</span></span> <span data-ttu-id="ef77d-126">이 시나리오에서 저장 프로시저가 실패할 경우 게시자를 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] SP1 이상으로 업그레이드합니다.</span><span class="sxs-lookup"><span data-stu-id="ef77d-126">If the stored procedure fails in this scenario, upgrade the Publisher to [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] SP1 or later.</span></span>  
  
 <span data-ttu-id="ef77d-127">자세한 내용은 [트랜잭션 게시에 대해 업데이트할 수 있는 구독 만들기](../publish/create-an-updatable-subscription-to-a-transactional-publication.md) 및 [복제 보안 설정 보기 및 수정](view-and-modify-replication-security-settings.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ef77d-127">For more information, see [Create an Updatable Subscription to a Transactional Publication](../publish/create-an-updatable-subscription-to-a-transactional-publication.md) and [View and Modify Replication Security Settings](view-and-modify-replication-security-settings.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="ef77d-128">연결에 대해 지정된 계정에는 복제가 게시 데이터베이스에 만드는 뷰에서 데이터를 삽입, 업데이트 및 삭제할 수 있는 사용 권한만 부여하고 다른 추가 사용 권한은 부여하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ef77d-128">The account specified for the connection should only be granted permission to insert, update, and delete data on the views that replication creates in the publication database; it should not be given any additional permissions.</span></span> <span data-ttu-id="ef77d-129">각 구독자에서 구성한 계정에 이름이 **syncobj_** _\<HexadecimalNumber>_ 형식으로 지정된 게시 데이터베이스의 뷰에 대한 사용 권한을 부여합니다.</span><span class="sxs-lookup"><span data-stu-id="ef77d-129">Grant permissions on views in the publication database that are named in the form **syncobj_**_\<HexadecimalNumber>_ to the account you configured at each Subscriber.</span></span>  
  
## <a name="queued-updating-subscriptions"></a><span data-ttu-id="ef77d-130">지연 업데이트 구독</span><span class="sxs-lookup"><span data-stu-id="ef77d-130">Queued Updating Subscriptions</span></span>  
 <span data-ttu-id="ef77d-131">지연 업데이트 구독 구성 시 보안과 관련된 다음 두 가지 영역을 유의하십시오.</span><span class="sxs-lookup"><span data-stu-id="ef77d-131">When you configure queued updating subscriptions, there are two areas to keep in mind that relate to security:</span></span>  
  
-   <span data-ttu-id="ef77d-132">각 배포자에 대해 하나의 큐 판독기 에이전트만 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ef77d-132">There is only one Queue Reader Agent for each Distributor.</span></span> <span data-ttu-id="ef77d-133">각 배포자에 대해 지연 업데이트 구독이 설정된 하나의 게시를 구성하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="ef77d-133">It is recommended that for each Distributor, you configure at most one publication that is enabled for queued updating subscriptions.</span></span>  
  
-   <span data-ttu-id="ef77d-134">큐 판독기 에이전트는 배포자, 게시자 및 각 구독자에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="ef77d-134">The Queue Reader agent makes connections to the Distributor, Publisher, and each Subscriber:</span></span>  
  
    -   <span data-ttu-id="ef77d-135">에이전트를 만들 때 에이전트가 실행되고 배포자 연결에 사용되는 계정이 지정됩니다. 새 게시 마법사를 사용하는 경우에는 구독 업데이트가 설정된 게시를 만들 때 에이전트가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="ef77d-135">The account under which the agent runs and makes connections to the Distributor is specified when you create the agent (if you use the New Publication Wizard, the agent is created when you create a publication that is enabled for updating subscriptions).</span></span>  
  
    -   <span data-ttu-id="ef77d-136">게시자에 대한 배포를 구성할 때 에이전트가 게시자 연결에 사용하는 계정이 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="ef77d-136">The account under which the agent makes connections to the Publisher is specified when you configure distribution for a Publisher.</span></span> <span data-ttu-id="ef77d-137">에이전트가 실행되는 Windows 계정 또는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 계정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ef77d-137">Specify the Windows account under which the agent runs or a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] account.</span></span>  
  
    -   <span data-ttu-id="ef77d-138">구독을 만들 때 에이전트가 구독자 연결에 사용하는 계정이 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="ef77d-138">The account under which the agent makes connections to the Subscriber is specified when you create the subscription.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="ef77d-139">구독자 연결에 대해서는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인증을 사용하고 각 구독자 연결에는 서로 다른 계정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ef77d-139">Use [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication for connections to Subscribers, and specify a different account for the connection to each Subscriber.</span></span> <span data-ttu-id="ef77d-140">끌어오기 구독을 사용하는 경우 복제는 항상 Windows 인증을 사용하도록 연결을 설정합니다. 끌어오기 구독에서 복제는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인증을 사용하는 데 필요한 메타데이터를 구독자에서 액세스할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ef77d-140">If you use a pull subscription, replication always sets the connection to use Windows Authentication (for pull subscriptions, replication cannot access metadata at the Subscriber required to use [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication).</span></span> <span data-ttu-id="ef77d-141">이 경우 구독을 구성한 후 연결에서 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인증을 사용하도록 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="ef77d-141">In this case, change the connection to use [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication after the subscription is configured.</span></span>  
  
     <span data-ttu-id="ef77d-142">자세한 내용은 방법: 트랜잭션 게시에 대해 업데이트할 수 있는 구독 만들기(SQL Server Management Studio) 및 [복제 보안 설정 보기 및 수정](view-and-modify-replication-security-settings.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ef77d-142">For more information, see How to: Create an Updating Subscription to a Transactional Publication (SQL Server Management Studio) and [View and Modify Replication Security Settings](view-and-modify-replication-security-settings.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef77d-143">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ef77d-143">See Also</span></span>  
 <span data-ttu-id="ef77d-144">[데이터베이스 엔진에 암호화 연결 사용&#40;SQL Server 구성 관리자&#41;](../../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md) </span><span class="sxs-lookup"><span data-stu-id="ef77d-144">[Enable Encrypted Connections to the Database Engine &#40;SQL Server Configuration Manager&#41;](../../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md) </span></span>  
 <span data-ttu-id="ef77d-145">[Replication Security Best Practices](replication-security-best-practices.md) </span><span class="sxs-lookup"><span data-stu-id="ef77d-145">[Replication Security Best Practices](replication-security-best-practices.md) </span></span>  
 [<span data-ttu-id="ef77d-146">SQL Server 복제 보안</span><span class="sxs-lookup"><span data-stu-id="ef77d-146">SQL Server Replication Security</span></span>](view-and-modify-replication-security-settings.md)  
  
  
