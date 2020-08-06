---
title: 로그 판독기 에이전트 보안(피어 투 피어 복제) | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.p2pwizard.LRA.f1
ms.assetid: 6575e2a8-16bb-449c-bdca-4a4202d0972f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: dfef98adb622f9da922af0c1cdbb1cf8b7a07da5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653289"
---
# <a name="log-reader-agent-security-peer-to-peer-replication"></a><span data-ttu-id="3c8bb-102">로그 판독기 에이전트 보안(피어 투 피어 복제)</span><span class="sxs-lookup"><span data-stu-id="3c8bb-102">Log Reader Agent Security (Peer-to-Peer Replication)</span></span>
  <span data-ttu-id="3c8bb-103">**로그 판독기 에이전트 보안** 페이지를 사용하여 각 피어에서 로그 판독기 에이전트를 실행 및 연결하는 계정을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3c8bb-103">The **Log Reader Agent Security** page allows you to specify the accounts under which the Log Reader Agent at each peer runs and makes connections.</span></span> <span data-ttu-id="3c8bb-104">에이전트에 필요한 사용 권한 및 복제 보안을 위한 최선의 구현 방법은 [Replication Agent Security Model(복제 에이전트 보안 모델)](security/replication-agent-security-model.md) 및 [Replication Security Best Practices](security/replication-security-best-practices.md)(복제 보안 모범 사례)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3c8bb-104">For information on permissions required by agents and best practices for replication security, see [Replication Agent Security Model](security/replication-agent-security-model.md) and [Replication Security Best Practices](security/replication-security-best-practices.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3c8bb-105">트랜잭션 복제를 사용하여 게시된 각 데이터베이스에 대해 하나의 로그 판독기 에이전트가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3c8bb-105">There is one Log Reader Agent for each database that is published using transactional replication.</span></span> <span data-ttu-id="3c8bb-106">데이터베이스에 대한 로그 판독기 에이전트가 이미 구성된 경우(이 마법사의 이전 실행에서 게시에 대해 구성했거나 동일한 데이터베이스의 다른 트랜잭션 게시에 대해 구성한 경우) 이 마법사를 통해 데이터베이스가 사용하는 자격 증명을 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3c8bb-106">If the Log Reader Agent for a database has already been configured (either for a publication in a previous run of this wizard or for another transactional publication in the same database), you cannot change the credentials it uses in this wizard.</span></span> <span data-ttu-id="3c8bb-107">새 자격 증명을 지정하면 이 자격 증명은 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c8bb-107">If you specify new credentials, they are ignored.</span></span> <span data-ttu-id="3c8bb-108">자격 증명을 변경하려면 **게시 속성** 대화 상자를 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="3c8bb-108">To change credentials, use the **Publication Properties** dialog box.</span></span> <span data-ttu-id="3c8bb-109">자세한 내용은 [View and Modify Replication Security Settings](security/view-and-modify-replication-security-settings.md)을(를) 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3c8bb-109">For more information, see [View and Modify Replication Security Settings](security/view-and-modify-replication-security-settings.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="3c8bb-110">옵션</span><span class="sxs-lookup"><span data-stu-id="3c8bb-110">Options</span></span>  
 <span data-ttu-id="3c8bb-111">각 피어에 대한 행에서 속성 단추 ( **...** )를 클릭하여 **로그 판독기 에이전트 보안** 대화 상자에 액세스합니다.</span><span class="sxs-lookup"><span data-stu-id="3c8bb-111">Click the properties button (**...**) in the row for each peer to access the **Log Reader Agent Security** dialog box.</span></span> <span data-ttu-id="3c8bb-112">에이전트가 사용하는 계정에 필요한 사용 권한에 대한 자세한 내용을 보려면 시작한 **로그 판독기 에이전트 보안** 대화 상자에서 **도움말** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3c8bb-112">Click **Help** on the **Log Reader Agent Security** dialog box that is launched for more information on the permissions required for accounts used by the agents.</span></span>  
  
 <span data-ttu-id="3c8bb-113">대화 상자에서 설정을 입력하면 구독자에 대한 연결 정보가 표에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c8bb-113">After settings have been entered in the dialog box, connection information for the Subscriber is displayed in the grid.</span></span>  
  
 <span data-ttu-id="3c8bb-114">**게시자 에이전트**</span><span class="sxs-lookup"><span data-stu-id="3c8bb-114">**Agents for Publisher**</span></span>  
 <span data-ttu-id="3c8bb-115">각 피어 서버 인스턴스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="3c8bb-115">The name of each peer server instance.</span></span>  
  
 <span data-ttu-id="3c8bb-116">**피어 데이터베이스**</span><span class="sxs-lookup"><span data-stu-id="3c8bb-116">**Peer Database**</span></span>  
 <span data-ttu-id="3c8bb-117">각 피어에서 게시 데이터베이스 및 구독 데이터베이스 역할을 하는 데이터베이스입니다.</span><span class="sxs-lookup"><span data-stu-id="3c8bb-117">The database that serves as the publication database and subscription database at each peer.</span></span>  
  
 <span data-ttu-id="3c8bb-118">**배포자에 대한 연결**</span><span class="sxs-lookup"><span data-stu-id="3c8bb-118">**Connection to Distributor**</span></span>  
 <span data-ttu-id="3c8bb-119">배포자에 대한 연결이 설정되는 컨텍스트입니다.</span><span class="sxs-lookup"><span data-stu-id="3c8bb-119">The context under which the connection to the Distributor is made.</span></span> <span data-ttu-id="3c8bb-120">배포자에 대한 로컬 연결은 항상 에이전트를 실행하는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 계정의 컨텍스트를 사용하여 설정되므로 이 필드는 항상 **Impersonate '\<Domain>\\<Login\>'** 또는 **Impersonate '\<Computer>\\<Login\>'** 을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="3c8bb-120">The local connection to the Distributor is always made using the context of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows account under which the agent runs, so this field will always display **Impersonate '\<Domain>\\<Login\>'** or **Impersonate '\<Computer>\\<Login\>'**.</span></span>  
  
 <span data-ttu-id="3c8bb-121">**게시자에 대한 연결**</span><span class="sxs-lookup"><span data-stu-id="3c8bb-121">**Connection to Publisher**</span></span>  
 <span data-ttu-id="3c8bb-122">게시자에 대한 연결을 설정하는 컨텍스트입니다.</span><span class="sxs-lookup"><span data-stu-id="3c8bb-122">The context under which the connection to the Publisher is made.</span></span> <span data-ttu-id="3c8bb-123">에이전트를 실행하는 Windows 계정의 컨텍스트 또는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그인을 사용하여 게시자에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3c8bb-123">The connection to the Publisher can be made using a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login or using the context of the Windows account under which the agent runs.</span></span> <span data-ttu-id="3c8bb-124">이 필드는 **로그인 '\<Login>'** , **Impersonate '\<Domain>\\<Login\>'** or **Impersonate '\<Computer>\\<Login\>'** 을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="3c8bb-124">The field displays one of the following: **Use login '\<Login>'**, **Impersonate '\<Domain>\\<Login\>'** or **Impersonate '\<Computer>\\<Login\>'**.</span></span> [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="3c8bb-125">에서는 Windows 계정의 컨텍스트를 사용하여 모든 연결을 설정할 것을 권장합니다.</span><span class="sxs-lookup"><span data-stu-id="3c8bb-125">recommends that all connections be made using the context of the Windows account.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c8bb-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3c8bb-126">See Also</span></span>  
 <span data-ttu-id="3c8bb-127">[피어 투 피어 토폴로지 관리&#40;복제 Transact-SQL 프로그래밍&#41;](administration/administer-a-peer-to-peer-topology-replication-transact-sql-programming.md) </span><span class="sxs-lookup"><span data-stu-id="3c8bb-127">[Administer a Peer-to-Peer Topology &#40;Replication Transact-SQL Programming&#41;](administration/administer-a-peer-to-peer-topology-replication-transact-sql-programming.md) </span></span>  
 [<span data-ttu-id="3c8bb-128">@loopback_detection</span><span class="sxs-lookup"><span data-stu-id="3c8bb-128">Peer-to-Peer Transactional Replication</span></span>](transactional/peer-to-peer-transactional-replication.md)  
  
  
