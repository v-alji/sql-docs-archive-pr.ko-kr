---
title: 배포 에이전트 보안(피어 투 피어 복제) | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.p2pwizard.DA.f1
ms.assetid: def6bf26-c640-4caf-ad30-05d1e649541d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 72b5a52fbb3ddc11d0ea6f2c0b26786463e08eaf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646922"
---
# <a name="distribution-agent-security-peer-to-peer-replication"></a><span data-ttu-id="20f19-102">배포 에이전트 보안(피어 투 피어 복제)</span><span class="sxs-lookup"><span data-stu-id="20f19-102">Distribution Agent Security (Peer-to-Peer Replication)</span></span>
  <span data-ttu-id="20f19-103">**배포 에이전트 보안** 페이지를 사용하여 배포 에이전트를 실행하고 피어 투 피어 토폴로지의 컴퓨터에 연결하는 계정을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="20f19-103">The **Distribution Agent Security** page allows you to specify the accounts under which the Distribution Agent runs and makes connections to the computers in a peer-to-peer topology.</span></span> <span data-ttu-id="20f19-104">에이전트에 필요한 사용 권한 및 복제 보안을 위한 최선의 구현 방법은 [Replication Agent Security Model(복제 에이전트 보안 모델)](security/replication-agent-security-model.md) 및 [Replication Security Best Practices](security/replication-security-best-practices.md)(복제 보안 모범 사례)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="20f19-104">For information on permissions required by agents and best practices for replication security, see [Replication Agent Security Model](security/replication-agent-security-model.md) and [Replication Security Best Practices](security/replication-security-best-practices.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="20f19-105">이전에 이 마법사를 실행하여 구독에 대한 배포 에이전트를 구성한 경우에는 해당 배포 에이전트에서 사용하는 자격 증명을 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="20f19-105">If the Distribution Agent for a subscription has already been configured in a previous run of this wizard, you cannot change the credentials it uses in this wizard.</span></span> <span data-ttu-id="20f19-106">새 자격 증명을 지정하면 이 자격 증명은 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="20f19-106">If you specify new credentials, they are ignored.</span></span> <span data-ttu-id="20f19-107">자격 증명을 변경하려면 **구독 속성** 대화 상자를 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="20f19-107">To change credentials, use the **Subscription Properties** dialog box.</span></span> <span data-ttu-id="20f19-108">자세한 내용은 [View and Modify Replication Security Settings](security/view-and-modify-replication-security-settings.md)을(를) 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="20f19-108">For more information, see [View and Modify Replication Security Settings](security/view-and-modify-replication-security-settings.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="20f19-109">옵션</span><span class="sxs-lookup"><span data-stu-id="20f19-109">Options</span></span>  
 <span data-ttu-id="20f19-110">각 구독자에 대한 행에서 속성 단추 ( **...** )를 클릭하여 **배포 에이전트 보안** 대화 상자에 액세스합니다.</span><span class="sxs-lookup"><span data-stu-id="20f19-110">Click the properties button (**...**) in the row for each Subscriber to access the **Distribution Agent Security** dialog box.</span></span> <span data-ttu-id="20f19-111">에이전트가 사용하는 계정에 필요한 사용 권한에 대한 자세한 내용을 보려면 시작한 **배포 에이전트 보안** 대화 상자에서 **도움말** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="20f19-111">Click **Help** on the **Distribution Agent Security** dialog box that is launched for more information on the permissions required for accounts used by the agents.</span></span>  
  
 <span data-ttu-id="20f19-112">대화 상자에서 설정을 입력하면 구독자에 대한 연결 정보가 표에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="20f19-112">After settings have been entered in one of the dialog boxes, connection information for the Subscriber is displayed in the grid.</span></span>  
  
 <span data-ttu-id="20f19-113">**구독자 에이전트**</span><span class="sxs-lookup"><span data-stu-id="20f19-113">**Agent for Subscriber**</span></span>  
 <span data-ttu-id="20f19-114">각 피어의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="20f19-114">The name of each peer.</span></span>  
  
 <span data-ttu-id="20f19-115">**피어 데이터베이스**</span><span class="sxs-lookup"><span data-stu-id="20f19-115">**Peer Database**</span></span>  
 <span data-ttu-id="20f19-116">게시 데이터베이스와 구독 데이터베이스 역할을 모두 수행하는 피어의 데이터베이스입니다.</span><span class="sxs-lookup"><span data-stu-id="20f19-116">The database at the peer that will serve as both a publication database and subscription database.</span></span>  
  
 <span data-ttu-id="20f19-117">**배포자에 대한 연결**</span><span class="sxs-lookup"><span data-stu-id="20f19-117">**Connection to Distributor**</span></span>  
 <span data-ttu-id="20f19-118">배포자에 대한 연결이 설정되는 컨텍스트입니다.</span><span class="sxs-lookup"><span data-stu-id="20f19-118">The context under which the connection to the Distributor is made.</span></span> <span data-ttu-id="20f19-119">로컬 연결은 항상 에이전트를 실행하는 Windows 계정의 컨텍스트를 사용하여 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="20f19-119">Local connections are always made using the context of the Windows account under which the agent runs.</span></span> <span data-ttu-id="20f19-120">이 마법사는 로컬 연결이 배포자에 대한 연결인 밀어넣기 구독을 만들기 때문에 이 필드에 항상 **Impersonate '\<Domain>\\<Login\>'** or **Impersonate '\<Computer>\\<Login\>'** 이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="20f19-120">This wizard creates push subscriptions (the local connection is the connection to the Distributor), so this field will always display: **Impersonate '\<Domain>\\<Login\>'** or **Impersonate '\<Computer>\\<Login\>'**.</span></span>  
  
 <span data-ttu-id="20f19-121">**구독자에 대한 연결**</span><span class="sxs-lookup"><span data-stu-id="20f19-121">**Connection to Subscriber**</span></span>  
 <span data-ttu-id="20f19-122">구독자에 대한 연결이 설정되는 컨텍스트입니다.</span><span class="sxs-lookup"><span data-stu-id="20f19-122">The context under which the connection to the Subscriber is made.</span></span> <span data-ttu-id="20f19-123">에이전트를 실행하는 Windows 계정의 컨텍스트 또는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그인의 컨텍스트에서 연결을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="20f19-123">The connection can be made using the context of the Windows account under which the agent runs or under the context of a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login.</span></span> <span data-ttu-id="20f19-124">이 필드는 **로그인 '\<Login>'** , **Impersonate '\<Domain>\\<Login\>'** or **Impersonate '\<Computer>\\<Login\>'** 을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="20f19-124">The field displays one of the following: **Use login '\<Login>'**, **Impersonate '\<Domain>\\<Login\>'** or **Impersonate '\<Computer>\\<Login\>'**.</span></span> [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="20f19-125">에서는 Windows 계정의 컨텍스트를 사용하여 모든 연결을 설정할 것을 권장합니다.</span><span class="sxs-lookup"><span data-stu-id="20f19-125">recommends that all connections be made using the context of the Windows account.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20f19-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="20f19-126">See Also</span></span>  
 <span data-ttu-id="20f19-127">[피어 투 피어 토폴로지 관리&#40;복제 Transact-SQL 프로그래밍&#41;](administration/administer-a-peer-to-peer-topology-replication-transact-sql-programming.md) </span><span class="sxs-lookup"><span data-stu-id="20f19-127">[Administer a Peer-to-Peer Topology &#40;Replication Transact-SQL Programming&#41;](administration/administer-a-peer-to-peer-topology-replication-transact-sql-programming.md) </span></span>  
 [<span data-ttu-id="20f19-128">@loopback_detection</span><span class="sxs-lookup"><span data-stu-id="20f19-128">Peer-to-Peer Transactional Replication</span></span>](transactional/peer-to-peer-transactional-replication.md)  
  
  
