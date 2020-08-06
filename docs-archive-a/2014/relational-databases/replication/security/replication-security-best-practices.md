---
title: 복제 보안을 위한 최선의 구현 방법 | Microsoft 문서
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- security [SQL Server replication], best practices
- security [SQL Server replication], between domains
- authentication [SQL Server replication]
- Internet [SQL Server replication], security
ms.assetid: 1ab2635d-0992-4c99-b17d-041d02ec9a7c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8e5918bfed52a6ed1befd81d2fdb7910062060e6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638643"
---
# <a name="replication-security-best-practices"></a><span data-ttu-id="d5487-102">복제 보안을 위한 최선의 구현 방법</span><span class="sxs-lookup"><span data-stu-id="d5487-102">Replication Security Best Practices</span></span>
  <span data-ttu-id="d5487-103">단일 도메인의 인트라넷에서부터 트러스트되지 않은 도메인 간이나 인터넷을 통해 데이터에 액세스하는 애플리케이션에 이르기까지의 분산 환경에서 복제는 데이터를 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="d5487-103">Replication moves data in distributed environments ranging from intranets on a single domain to applications that access data between untrusted domains and over the Internet.</span></span> <span data-ttu-id="d5487-104">따라서 이러한 다양한 환경에서 복제 연결의 보안을 유지하는 최선의 방법을 이해하는 것이 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="d5487-104">It is important to understand the best approach for securing replication connections under these different circumstances.</span></span>  
  
 <span data-ttu-id="d5487-105">다음 정보는 모든 환경에서의 복제와 관련이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d5487-105">The following information is relevant to replication in all environments:</span></span>  
  
-   <span data-ttu-id="d5487-106">VPN(가상 프라이빗 네트워크), SSL(Secure Sockets Layer) 또는 IPSEC(IP 보안)과 같은 산업 표준 방법을 사용하여 복제 토폴로지의 컴퓨터 간 연결을 암호화합니다.</span><span class="sxs-lookup"><span data-stu-id="d5487-106">Encrypt the connections between computers in a replication topology using an industry standard method, such as Virtual Private Networks (VPN), Secure Sockets Layer (SSL), or IP Security (IPSEC).</span></span> <span data-ttu-id="d5487-107">자세한 내용은 [데이터베이스 엔진에 암호화 연결 사용&#40;SQL Server 구성 관리자&#41;](../../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d5487-107">For more information, see [Enable Encrypted Connections to the Database Engine &#40;SQL Server Configuration Manager&#41;](../../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md).</span></span> <span data-ttu-id="d5487-108">VPN 및 SSL을 사용하여 인터넷에서 데이터를 복제하는 방법은 [Securing Replication Over the Internet](securing-replication-over-the-internet.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="d5487-108">For information about using VPN and SSL for replicating data over the Internet, see [Securing Replication Over the Internet](securing-replication-over-the-internet.md).</span></span>  
  
     <span data-ttu-id="d5487-109">SSL을 사용하여 복제 토폴로지에서 컴퓨터 간의 연결 보안을 유지하는 경우 각 복제 에이전트의 **-EncryptionLevel** 매개 변수 값을 **1** 또는 **2** 로 지정합니다(값 **2** 가 권장됨).</span><span class="sxs-lookup"><span data-stu-id="d5487-109">If you use SSL to secure the connections between computers in a replication topology, specify a value of **1** or **2** for the **-EncryptionLevel** parameter of each replication agent (a value of **2** is recommended).</span></span> <span data-ttu-id="d5487-110">값 **1** 을 지정하면 암호화가 사용되지만 에이전트에서 SSL 서버 인증서가 신뢰할 수 있는 발급자에 의해 서명된 것인지 확인하지는 않습니다. 값 **2** 를 지정하면 인증서가 확인됩니다.</span><span class="sxs-lookup"><span data-stu-id="d5487-110">A value of **1** specifies that encryption is used, but the agent does not verify that the SSL server certificate is signed by a trusted issuer; a value of **2** specifies that the certificate is verified.</span></span> <span data-ttu-id="d5487-111">에이전트 프로필 및 명령줄에서 에이전트 매개 변수를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d5487-111">Agent parameters can be specified in agent profiles and on the command line.</span></span> <span data-ttu-id="d5487-112">자세한 내용은 다음을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d5487-112">For more information, see:</span></span>  
  
    -   [<span data-ttu-id="d5487-113">복제 에이전트 프로필 작업</span><span class="sxs-lookup"><span data-stu-id="d5487-113">Work with Replication Agent Profiles</span></span>](../agents/replication-agent-profiles.md)  
  
    -   [<span data-ttu-id="d5487-114">복제 에이전트의 명령 프롬프트 매개 변수 보기 및 수정&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="d5487-114">View and Modify Replication Agent Command Prompt Parameters &#40;SQL Server Management Studio&#41;</span></span>](../agents/view-and-modify-replication-agent-command-prompt-parameters.md)  
  
    -   [<span data-ttu-id="d5487-115">Replication Agent Executables Concepts</span><span class="sxs-lookup"><span data-stu-id="d5487-115">Replication Agent Executables Concepts</span></span>](../concepts/replication-agent-executables-concepts.md)  
  
-   <span data-ttu-id="d5487-116">각 복제 에이전트를 서로 다른 Windows 계정으로 실행하고 모든 복제 에이전트 연결에 Windows 인증을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="d5487-116">Run each replication agent under a different Windows account, and use Windows Authentication for all replication agent connections.</span></span> <span data-ttu-id="d5487-117">계정 지정에 대한 자세한 내용은 [복제의 로그인 및 암호 관리](identity-and-access-control-replication.md#manage-logins-and-passwords-in-replication)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d5487-117">For more information about specifying accounts, see [Manage Logins and Passwords in Replication](identity-and-access-control-replication.md#manage-logins-and-passwords-in-replication).</span></span>  
  
-   <span data-ttu-id="d5487-118">각 에이전트에 필요한 사용 권한만 부여합니다.</span><span class="sxs-lookup"><span data-stu-id="d5487-118">Grant only the required permissions to each agent.</span></span> <span data-ttu-id="d5487-119">자세한 내용은 [Replication Agent Security Model](replication-agent-security-model.md)의 "에이전트에 필요한 사용 권한" 섹션을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="d5487-119">For more information, see the "Permissions Required by Agents" section of [Replication Agent Security Model](replication-agent-security-model.md).</span></span>  
  
-   <span data-ttu-id="d5487-120">모든 병합 에이전트 및 배포 에이전트 계정이 PAL(게시 액세스 목록)에 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="d5487-120">Ensure all Merge Agent and Distribution Agent accounts are in the publication access list (PAL).</span></span> <span data-ttu-id="d5487-121">자세한 내용은 [게시자 보안 설정](secure-the-publisher.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d5487-121">For more information, see [Secure the Publisher](secure-the-publisher.md).</span></span>  
  
-   <span data-ttu-id="d5487-122">PAL의 각 계정에 복제 태스크를 수행하는 데 필요한 사용 권한만 허용하여 최소 권한의 원칙을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="d5487-122">Follow the principle of least privilege by allowing accounts in the PAL only the permissions they need to perform replication tasks.</span></span> <span data-ttu-id="d5487-123">복제에 필요하지 않은 고정 서버 역할에 로그인을 추가하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="d5487-123">Do not add the logins to any fixed server roles that are not required for replication.</span></span>  
  
-   <span data-ttu-id="d5487-124">스냅샷 공유에서 모든 병합 에이전트와 배포 에이전트의 읽기 권한을 허용하도록 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="d5487-124">Configure the snapshot share to allow read access by all Merge Agents and Distribution Agents.</span></span> <span data-ttu-id="d5487-125">매개 변수가 있는 필터를 포함한 게시에 대한 스냅샷의 경우 각 폴더에서 해당 병합 에이전트 계정에만 액세스를 허용하도록 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d5487-125">In the case of snapshots for publications with parameterized filters, ensure that each folder is configured to allow access only to the appropriate Merge Agent accounts.</span></span>  
  
-   <span data-ttu-id="d5487-126">스냅샷 공유에서 스냅샷 에이전트의 쓰기 권한을 허용하도록 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="d5487-126">Configure the snapshot share to allow write access by the Snapshot Agent.</span></span>  
  
-   <span data-ttu-id="d5487-127">끌어오기 구독을 사용하는 경우 스냅샷 폴더에 로컬 경로가 아닌 네트워크 공유를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="d5487-127">If you use pull subscriptions, use a network share rather than a local path for the snapshot folder.</span></span>  
  
 <span data-ttu-id="d5487-128">복제 토폴로지에 동일한 도메인에 있지 않거나 서로 트러스트 관계가 구축되지 않은 도메인에 있는 컴퓨터가 포함되어 있으면 에이전트 연결에 대해 Windows 인증이나 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인증을 사용할 수 있습니다. 도메인에 대한 자세한 내용은 Windows 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="d5487-128">If your replication topology includes computers that are not in the same domain or are in domains that do not have trust relationships with each other, you can use Windows Authentication or [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication for the connections made by agents (For more information about domains, see the Windows documentation).</span></span> <span data-ttu-id="d5487-129">최상의 권장 보안 방법은 Windows 인증을 사용하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="d5487-129">It is recommended as a security best practice that you use Windows Authentication.</span></span>  
  
-   <span data-ttu-id="d5487-130">Windows 인증을 사용하려면</span><span class="sxs-lookup"><span data-stu-id="d5487-130">To use Windows Authentication:</span></span>  
  
    -   <span data-ttu-id="d5487-131">각 에이전트에 대한 로컬 Windows 계정(도메인 계정 아님)을 해당 노드에 추가합니다. 각 노드에서 동일한 이름과 암호를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="d5487-131">Add a local Windows account (not a domain account) for each agent at the appropriate nodes (use the same name and password at each node).</span></span> <span data-ttu-id="d5487-132">예를 들어 밀어넣기 구독의 배포 에이전트는 배포자에서 실행되며 배포자와 구독자에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="d5487-132">For example, the Distribution Agent for a push subscription runs at the Distributor and makes connections to the Distributor and Subscriber.</span></span> <span data-ttu-id="d5487-133">배포 에이전트에 대한 Windows 계정은 배포자와 구독자에 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d5487-133">The Windows account for the Distribution Agent should be added to the Distributor and Subscriber.</span></span>  
  
    -   <span data-ttu-id="d5487-134">지정된 에이전트(예: 구독에 대한 배포 에이전트)가 각 컴퓨터에서 동일한 계정으로 실행되는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="d5487-134">Ensure that a given agent (for example the Distribution Agent for a subscription) runs under the same account at each computer.</span></span>  
  
-   <span data-ttu-id="d5487-135">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인증을 사용하려면</span><span class="sxs-lookup"><span data-stu-id="d5487-135">To use [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication:</span></span>  
  
    -   <span data-ttu-id="d5487-136">각 에이전트에 대한 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 계정을 해당 노드에 추가합니다. 각 노드에서 동일한 계정 이름과 암호를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="d5487-136">Add a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] account for each agent at the appropriate nodes (use the same account name and password at each node).</span></span> <span data-ttu-id="d5487-137">예를 들어 밀어넣기 구독의 배포 에이전트는 배포자에서 실행되며 배포자와 구독자에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="d5487-137">For example, the Distribution Agent for a push subscription runs at the Distributor and makes connections to the Distributor and Subscriber.</span></span> <span data-ttu-id="d5487-138">배포 에이전트에 대한 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 계정은 배포자와 구독자에 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d5487-138">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] account for the Distribution Agent should be added to the Distributor and Subscriber.</span></span>  
  
    -   <span data-ttu-id="d5487-139">지정된 에이전트(예: 구독에 대한 배포 에이전트)가 각 컴퓨터에서 동일한 계정으로 연결하는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="d5487-139">Ensure that a given agent (for example the Distribution Agent for a subscription) makes connections under the same account at each computer.</span></span>  
  
    -   <span data-ttu-id="d5487-140">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인증이 필요한 환경에서는 UNC 스냅샷 공유에 액세스할 수 없는 경우가 많습니다. 예를 들어 방화벽에서 액세스를 차단할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d5487-140">In situations that require [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication, access to UNC snapshot shares is often not available (for example access might be blocked by a firewall).</span></span> <span data-ttu-id="d5487-141">이 경우 FTP(파일 전송 프로토콜)를 통해 스냅샷을 구독자에게 전송할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d5487-141">In this case, you can transfer the snapshot to Subscribers through file transfer protocol (FTP).</span></span> <span data-ttu-id="d5487-142">자세한 내용은 [FTP를 통해 스냅샷 전송](../transfer-snapshots-through-ftp.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d5487-142">For more information, see [Transfer Snapshots Through FTP](../transfer-snapshots-through-ftp.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5487-143">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d5487-143">See Also</span></span>  
 <span data-ttu-id="d5487-144">[데이터베이스 엔진에 암호화 연결 사용&#40;SQL Server 구성 관리자&#41;](../../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md) </span><span class="sxs-lookup"><span data-stu-id="d5487-144">[Enable Encrypted Connections to the Database Engine &#40;SQL Server Configuration Manager&#41;](../../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md) </span></span>  
 <span data-ttu-id="d5487-145">[인터넷을 통한 복제](../replication-over-the-internet.md) </span><span class="sxs-lookup"><span data-stu-id="d5487-145">[Replication over the Internet](../replication-over-the-internet.md) </span></span>  
 <span data-ttu-id="d5487-146">[구독자 보안 설정](secure-the-subscriber.md) </span><span class="sxs-lookup"><span data-stu-id="d5487-146">[Secure the Subscriber](secure-the-subscriber.md) </span></span>  
 <span data-ttu-id="d5487-147">[배포자 보안 설정](secure-the-distributor.md) </span><span class="sxs-lookup"><span data-stu-id="d5487-147">[Secure the Distributor](secure-the-distributor.md) </span></span>  
 <span data-ttu-id="d5487-148">[게시자 보안 설정](secure-the-publisher.md) </span><span class="sxs-lookup"><span data-stu-id="d5487-148">[Secure the Publisher](secure-the-publisher.md) </span></span>  
 [<span data-ttu-id="d5487-149">SQL Server 복제 보안</span><span class="sxs-lookup"><span data-stu-id="d5487-149">SQL Server Replication Security</span></span>](view-and-modify-replication-security-settings.md)  
  
  
