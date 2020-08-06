---
title: 업데이트할 수 있는 구독에 대한 로그인 | Microsoft 문서
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newsubwizard.updatablesubscriptionslogin.f1
ms.assetid: 301ea227-0455-40ba-9009-d38f8676b325
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6a5cc9190c77f506b13ba8b5fba0e32d5a925570
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739687"
---
# <a name="login-for-updatable-subscriptions"></a><span data-ttu-id="ac892-102">업데이트할 수 있는 구독에 대한 로그인</span><span class="sxs-lookup"><span data-stu-id="ac892-102">Login for Updatable Subscriptions</span></span>
  <span data-ttu-id="ac892-103">이 마법사의 **업데이트할 수 있는 구독** 페이지에서 **복제** 를 선택한 경우 즉시 업데이트 구독을 위해 게시자에 연결할 때 사용할 계정을 구독자에 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac892-103">If you selected **Replicate** on the **Updatable Subscriptions** page of this wizard, you must specify an account at the Subscriber under which connections to the Publisher are made for immediate updating subscriptions.</span></span> <span data-ttu-id="ac892-104">이 연결은 구독자에서 발생되는 트리거에 사용되고 게시자로 변경 내용을 전파합니다.</span><span class="sxs-lookup"><span data-stu-id="ac892-104">Connections are used by the triggers that fire at the Subscriber and propagate changes to the Publisher.</span></span> <span data-ttu-id="ac892-105">기본적으로 새 구독 마법사는 필요에 따라 즉시 업데이트로 전환할 수 있는 기능을 사용하여 지연 업데이트를 구성하기 때문에 이 계정은 **업데이트할 수 있는 구독** 페이지에서 **변경 내용 대기 및 가능 시 커밋** 을 선택한 경우에도 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="ac892-105">This account is required even if you selected **Queue changes and commit when possible** on the **Updatable Subscriptions** page, because by default the New Subscription Wizard configures queued updating with the ability to switch to immediate updating if required.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="ac892-106">연결에 대해 지정된 계정에는 복제가 게시 데이터베이스에 만드는 뷰에서 데이터를 삽입, 업데이트 및 삭제할 수 있는 사용 권한만 부여하고 다른 추가 사용 권한은 부여하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ac892-106">The account specified for the connection should only be granted permission to insert, update, and delete data on the views that replication creates in the publication database; it should not be given any additional permissions.</span></span> <span data-ttu-id="ac892-107">각 구독자에서 구성한 계정에 이름이 **syncobj_** _\<HexadecimalNumber>_ 형식으로 지정된 게시 데이터베이스의 뷰에 대한 사용 권한을 부여합니다.</span><span class="sxs-lookup"><span data-stu-id="ac892-107">Grant permissions on views in the publication database that are named in the form **syncobj_**_\<HexadecimalNumber>_ to the account you configured at each Subscriber.</span></span>  
  
 <span data-ttu-id="ac892-108">연결 유형에 대해 3가지 옵션을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac892-108">There are three options available for the type of connection:</span></span>  
  
-   <span data-ttu-id="ac892-109">이미 정의한 연결된 서버나 원격 서버</span><span class="sxs-lookup"><span data-stu-id="ac892-109">A linked server or remote server that you have already defined.</span></span>  
  
-   <span data-ttu-id="ac892-110">복제가 만드는 연결된 서버 - 이 마법사에서 지정하는 자격 증명으로 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="ac892-110">A linked server that replication creates; the connection is made with the credentials you specify in this wizard.</span></span>  
  
-   <span data-ttu-id="ac892-111">복제가 만드는 연결된 서버 - 구독자에서 변경 내용을 적용하는 사용자의 자격 증명으로 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="ac892-111">A linked server that replication creates; the connection is made with the credentials of the user making the change at the Subscriber.</span></span>  
  
 <span data-ttu-id="ac892-112">처음 두 가지 옵션은 이 마법사에서 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac892-112">The first two options can be specified in this wizard.</span></span> <span data-ttu-id="ac892-113">마지막 옵션은 [sp_link_publication &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-link-publication-transact-sql)사용 하는 경우에만 지정할 수 있습니다. 매개 변수의 값을 **1** 로 지정 **@security_mode** 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac892-113">The last option can only be specified using [sp_link_publication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-link-publication-transact-sql); specify a value of **1** for the parameter **@security_mode**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="ac892-114">옵션</span><span class="sxs-lookup"><span data-stu-id="ac892-114">Options</span></span>  
 <span data-ttu-id="ac892-115">**다음 SQL Server 인증을 사용하여 연결되는 연결된 서버 만들기**</span><span class="sxs-lookup"><span data-stu-id="ac892-115">**Create a linked server that connects using the following SQL Server Authentication login:**</span></span>  
 <span data-ttu-id="ac892-116">복제는 **로그인** 및 **암호** 필드에 지정된 자격 증명을 사용하여 연결된 서버를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ac892-116">Replication creates a linked server using the credentials specified in the **Login** and **Password** fields.</span></span>  
  
 <span data-ttu-id="ac892-117">**로그인**</span><span class="sxs-lookup"><span data-stu-id="ac892-117">**Login**</span></span>  
 <span data-ttu-id="ac892-118">이 토픽에 설명된 사용 권한만 있는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그인을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="ac892-118">Enter a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login that has only the permissions described in this topic.</span></span>  
  
 <span data-ttu-id="ac892-119">**암호**</span><span class="sxs-lookup"><span data-stu-id="ac892-119">**Password**</span></span>  
 <span data-ttu-id="ac892-120">**로그인**에서 지정한 로그인에 대한 강력한 암호를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="ac892-120">Enter a strong password for the login specified in **Login**.</span></span>  
  
 <span data-ttu-id="ac892-121">**암호 확인**</span><span class="sxs-lookup"><span data-stu-id="ac892-121">**Confirm Password**</span></span>  
 <span data-ttu-id="ac892-122">암호를 다시 입력하여 올바로 입력되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="ac892-122">Re-enter the password to confirm that it was entered correctly.</span></span>  
  
 <span data-ttu-id="ac892-123">**이미 정의한 연결된 서버나 원격 서버 사용**</span><span class="sxs-lookup"><span data-stu-id="ac892-123">**Use a linked server or remote server that you have already defined.**</span></span>  
 <span data-ttu-id="ac892-124">이 옵션을 사용하려면 이미 정의한 연결된 서버나 원격 서버가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="ac892-124">This option requires a linked server or remote server that you have already defined.</span></span> <span data-ttu-id="ac892-125">자세한 내용은 [연결된 서버&#40;데이터베이스 엔진&#41;](../linked-servers/linked-servers-database-engine.md) 및 [원격 서버](../../database-engine/configure-windows/remote-servers.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ac892-125">For more information, see [Linked Servers &#40;Database Engine&#41;](../linked-servers/linked-servers-database-engine.md) and [Remote Servers](../../database-engine/configure-windows/remote-servers.md).</span></span> <span data-ttu-id="ac892-126">연결된 서버나 원격 서버에 사용된 로그인에 강력한 암호가 있고 이 항목에 설명된 사용 권한만 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="ac892-126">Ensure that the login used for the linked server or remote server has a strong password and has only the permissions described in this topic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac892-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ac892-127">See Also</span></span>  
 <span data-ttu-id="ac892-128">[Create an Updatable Subscription to a Transactional Publication](publish/create-an-updatable-subscription-to-a-transactional-publication.md) </span><span class="sxs-lookup"><span data-stu-id="ac892-128">[Create an Updatable Subscription to a Transactional Publication](publish/create-an-updatable-subscription-to-a-transactional-publication.md) </span></span>  
 <span data-ttu-id="ac892-129">[복제 보안 설정 보기 및 수정](security/view-and-modify-replication-security-settings.md) </span><span class="sxs-lookup"><span data-stu-id="ac892-129">[View and Modify Replication Security Settings](security/view-and-modify-replication-security-settings.md) </span></span>  
 <span data-ttu-id="ac892-130">[Updatable Subscriptions for Transactional Replication](transactional/updatable-subscriptions-for-transactional-replication.md) </span><span class="sxs-lookup"><span data-stu-id="ac892-130">[Updatable Subscriptions for Transactional Replication](transactional/updatable-subscriptions-for-transactional-replication.md) </span></span>  
 [<span data-ttu-id="ac892-131">게시 구독</span><span class="sxs-lookup"><span data-stu-id="ac892-131">Subscribe to Publications</span></span>](subscribe-to-publications.md)  
  
  
