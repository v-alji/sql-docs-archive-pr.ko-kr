---
title: 게시자 보안 설정 | Microsoft 문서
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- logins [SQL Server replication], publication access list
- publications [SQL Server replication], publication access lists
- publication access list (PAL)
- PAL (publication access list)
- Publishers [SQL Server replication], security
- publications [SQL Server replication], security
ms.assetid: 4513a18d-dd6e-407a-b009-49dc9432ec7e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: dca3f704c43a97c2c34921007341b9bd613676ea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653270"
---
# <a name="secure-the-publisher"></a><span data-ttu-id="efd06-102">게시자 보안 설정</span><span class="sxs-lookup"><span data-stu-id="efd06-102">Secure the Publisher</span></span>
  <span data-ttu-id="efd06-103">게시자에 연결하는 복제 에이전트는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="efd06-103">The following replication agents connect to the Publisher:</span></span>  
  
-   <span data-ttu-id="efd06-104">로그 판독기 에이전트</span><span class="sxs-lookup"><span data-stu-id="efd06-104">Log Reader Agent</span></span>  
  
-   <span data-ttu-id="efd06-105">스냅샷 에이전트</span><span class="sxs-lookup"><span data-stu-id="efd06-105">Snapshot Agent</span></span>  
  
-   <span data-ttu-id="efd06-106">큐 판독기 에이전트</span><span class="sxs-lookup"><span data-stu-id="efd06-106">Queue Reader Agent</span></span>  
  
-   <span data-ttu-id="efd06-107">병합 에이전트</span><span class="sxs-lookup"><span data-stu-id="efd06-107">Merge Agent</span></span>  
  
 <span data-ttu-id="efd06-108">이러한 에이전트에 적절한 로그인을 제공하고 필요한 최소 권한만 부여하는 원칙을 따르며 모든 암호 스토리지를 보호하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="efd06-108">We recommend that you provide an appropriate login for these agents, follow the principle of granting the minimal rights that are required, and protect the storage of all passwords.</span></span> <span data-ttu-id="efd06-109">각 에이전트에 필요한 사용 권한에 대한 자세한 내용은 [Replication Agent Security Model](replication-agent-security-model.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="efd06-109">For information about the permissions that are required for each agent, see [Replication Agent Security Model](replication-agent-security-model.md).</span></span>  
  
 <span data-ttu-id="efd06-110">로그인과 암호를 적절하게 관리하는 것 외에도 PAL(게시 액세스 목록)의 역할을 이해해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="efd06-110">Besides appropriately managing logins and passwords, you should understand the role of the publication access list (PAL).</span></span> <span data-ttu-id="efd06-111">PAL은 게시자에서 데이터베이스에 대한 임의 액세스를 제한하면서 로그인에 게시 데이터에 대한 액세스 권한을 설정하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="efd06-111">The PAL is used to enable logins to access to publication data while restricting ad hoc access to the database at the Publisher.</span></span>  
  
## <a name="publication-access-list"></a><span data-ttu-id="efd06-112">게시 액세스 목록</span><span class="sxs-lookup"><span data-stu-id="efd06-112">Publication Access List</span></span>  
 <span data-ttu-id="efd06-113">PAL은 게시자의 게시 보안을 유지하는 기본 메커니즘입니다.</span><span class="sxs-lookup"><span data-stu-id="efd06-113">The PAL is the primary mechanism for securing publications at the Publisher.</span></span> <span data-ttu-id="efd06-114">PAL 기능은 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows 액세스 제어 목록과 유사하게 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="efd06-114">The PAL functions similarly to a [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows access control list.</span></span> <span data-ttu-id="efd06-115">게시를 만들면 복제에서 게시에 대한 PAL을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="efd06-115">When you create a publication, replication creates a PAL for the publication.</span></span> <span data-ttu-id="efd06-116">게시에 대한 액세스 권한이 부여된 로그인 및 그룹 목록을 포함하도록 PAL을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="efd06-116">The PAL can be configured to contain a list of logins and groups that are granted access to the publication.</span></span> <span data-ttu-id="efd06-117">에이전트가 게시자나 배포자에 연결한 다음 게시에 대한 액세스를 요청하면 PAL의 인증 정보가 에이전트에서 제공한 게시자 로그인과 비교됩니다.</span><span class="sxs-lookup"><span data-stu-id="efd06-117">When an agent connects to the Publisher or Distributor and requests access to a publication, the authentication information in the PAL is compared to the Publisher login that the agent provides.</span></span> <span data-ttu-id="efd06-118">이 프로세스는 클라이언트 도구가 게시자에서 직접 수정 작업을 수행하는 데 게시자 및 배포자 로그인을 사용하지 못하도록 방지하여 게시자에 대한 보안을 강화합니다.</span><span class="sxs-lookup"><span data-stu-id="efd06-118">This process provides additional security for the Publisher by preventing the Publisher and Distributor login from being used by a client tool to perform modifications on the Publisher directly.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="efd06-119">복제는 각 게시의 게시자에 PAL 멤버 자격을 적용할 역할을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="efd06-119">Replication creates a role on the Publisher for each publication to enforce PAL membership.</span></span> <span data-ttu-id="efd06-120">역할 이름은 병합 복제의 경우 **Msmerge_** _\<PublicationID>_ 형식으로 지정되고 트랜잭션 및 스냅샷 복제의 경우 **MSReplPAL_** _\<PublicationDatabaseID>_ **_** _\<PublicationID>_ 형식으로 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="efd06-120">The role has a name in the form **Msmerge_**_\<PublicationID>_ for merge replication and **MSReplPAL_**_\<PublicationDatabaseID>_**_**_\<PublicationID>_ for transactional and snapshot replication.</span></span>  
  
 <span data-ttu-id="efd06-121">기본적으로 PAL에는 게시 생성 시의 **sysadmin** 고정 서버 역할의 멤버와 게시를 만드는 데 사용된 로그인이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="efd06-121">By default, the following logins are included in the PAL: the members of the **sysadmin** fixed server role at the time the publication is created and the login that is used to create the publication.</span></span> <span data-ttu-id="efd06-122">기본적으로 게시 데이터베이스에서 **sysadmin** 고정 서버 역할이나 **db_owner** 고정 데이터베이스 역할의 멤버인 모든 로그인은 PAL에 명시적으로 추가하지 않아도 게시를 구독할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="efd06-122">By default, all logins that are members of the **sysadmin** fixed server role or the **db_owner** fixed database role on the publication database can subscribe to a publication without being explicitly added to the PAL.</span></span>  
  
 <span data-ttu-id="efd06-123">PAL을 사용하는 경우에는 다음 지침을 유의하십시오.</span><span class="sxs-lookup"><span data-stu-id="efd06-123">When you are using the PAL, consider the following guidelines:</span></span>  
  
-   <span data-ttu-id="efd06-124">PAL에 로그인을 추가하려면 먼저 게시 데이터베이스의 데이터베이스 사용자와 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 로그인을 연결해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="efd06-124">You must associate the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] login with a database user in the publication database before adding the login to the PAL.</span></span>  
  
-   <span data-ttu-id="efd06-125">PAL의 로그인에 복제 태스크 수행에 필요한 권한만 허용하는 최소 권한 원칙을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="efd06-125">Follow the principle of least privilege by allowing logins in the PAL only the permissions the logins must have to perform replication tasks.</span></span> <span data-ttu-id="efd06-126">복제 시 필요 없는 고정 데이터베이스 역할이나 서버 역할에 로그인을 추가하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="efd06-126">Do not add the logins to any fixed database roles or server roles that are not required for replication.</span></span> <span data-ttu-id="efd06-127">필요한 사용 권한에 대한 자세한 내용은 [Replication Agent Security Model](replication-agent-security-model.md) 및 [Replication Security Best Practices](replication-security-best-practices.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="efd06-127">For more information about the permissions that are required, see [Replication Agent Security Model](replication-agent-security-model.md) and [Replication Security Best Practices](replication-security-best-practices.md).</span></span>  
  
-   <span data-ttu-id="efd06-128">원격 배포자를 사용할 경우 PAL의 계정을 게시자와 배포자에서 모두 사용할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="efd06-128">If a remote Distributor is used, accounts in the PAL must be available at both the Publisher and the Distributor.</span></span> <span data-ttu-id="efd06-129">이 계정은 두 서버 모두에 정의된 도메인 계정이나 로컬 계정이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="efd06-129">The account must be either a domain account or a local account that is defined at both servers.</span></span> <span data-ttu-id="efd06-130">또한 두 로그인과 연결된 암호는 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="efd06-130">The passwords associated with both logins must be the same.</span></span>  
  
-   <span data-ttu-id="efd06-131">PAL에 Windows 계정이 포함되어 있고 도메인에서 Active Directory를 사용할 경우 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 를 실행하는 계정에 Active Directory에서 읽을 수 있는 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="efd06-131">If the PAL contains Windows accounts and the domain uses Active Directory, the account under which [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] runs must have permissions to read from Active Directory.</span></span> <span data-ttu-id="efd06-132">Windows 계정에 문제가 발생하면 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 를 실행하는 계정에 충분한 사용 권한이 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="efd06-132">If you experience issues with Windows accounts, make sure that the account under which [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] runs has sufficient permissions.</span></span> <span data-ttu-id="efd06-133">자세한 내용은 Windows 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="efd06-133">For more information, see the Windows documentation.</span></span>  
  
 <span data-ttu-id="efd06-134">PAL을 관리하려면 [게시 액세스 목록에서 로그인 관리](manage-logins-in-the-publication-access-list.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="efd06-134">To manage the PAL, see [Manage Logins in the Publication Access List](manage-logins-in-the-publication-access-list.md).</span></span>  
  
## <a name="snapshot-agent"></a><span data-ttu-id="efd06-135">스냅샷 에이전트</span><span class="sxs-lookup"><span data-stu-id="efd06-135">Snapshot Agent</span></span>  
 <span data-ttu-id="efd06-136">각 게시에 하나의 스냅샷 에이전트가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="efd06-136">There is one Snapshot Agent for each publication.</span></span> <span data-ttu-id="efd06-137">자세한 내용은 [게시 만들기](../publish/create-a-publication.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="efd06-137">For more information, see [Create a Publication](../publish/create-a-publication.md).</span></span>  
  
## <a name="ftp-snapshot-delivery"></a><span data-ttu-id="efd06-138">FTP 스냅샷 배달</span><span class="sxs-lookup"><span data-stu-id="efd06-138">FTP Snapshot Delivery</span></span>  
 <span data-ttu-id="efd06-139">UNC 공유가 아닌 FTP 공유를 통해서만 스냅샷을 사용할 수 있도록 지정한 경우 FTP 액세스를 구성할 때 로그인과 암호를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="efd06-139">If you specify that snapshots should be made available through an FTP share rather than a UNC share, you must specify a login and password when configuring FTP access.</span></span> <span data-ttu-id="efd06-140">자세한 내용은 [FTP를 통해 스냅샷 배달](../publish/deliver-a-snapshot-through-ftp.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="efd06-140">For more information, see [Deliver a Snapshot Through FTP](../publish/deliver-a-snapshot-through-ftp.md).</span></span>  
  
## <a name="log-reader-agent"></a><span data-ttu-id="efd06-141">로그 판독기 에이전트</span><span class="sxs-lookup"><span data-stu-id="efd06-141">Log Reader Agent</span></span>  
 <span data-ttu-id="efd06-142">트랜잭션 복제에 대해 게시된 각 데이터베이스에 하나의 로그 판독기 에이전트가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="efd06-142">There is one Log Reader Agent for each database published for transactional replication.</span></span> <span data-ttu-id="efd06-143">자세한 내용은 [게시 만들기](../publish/create-a-publication.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="efd06-143">For more information, see [Create a Publication](../publish/create-a-publication.md).</span></span>  
  
## <a name="queue-reader-agent"></a><span data-ttu-id="efd06-144">큐 판독기 에이전트</span><span class="sxs-lookup"><span data-stu-id="efd06-144">Queue Reader Agent</span></span>  
 <span data-ttu-id="efd06-145">지정된 배포자와 관련된 모든 게시자와 게시(지연 업데이트 구독 허용)에 하나의 큐 판독기 에이전트가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="efd06-145">There is one Queue Reader Agent for all Publishers and publications (that allow queued updating subscriptions) associated with a given Distributor.</span></span> <span data-ttu-id="efd06-146">자세한 내용은 [트랜잭션 게시에 대해 업데이트할 수 있는 구독 설정](../publish/enable-updating-subscriptions-for-transactional-publications.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="efd06-146">For more information, see [Enable Updating Subscriptions for Transactional Publications](../publish/enable-updating-subscriptions-for-transactional-publications.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="efd06-147">참고 항목</span><span class="sxs-lookup"><span data-stu-id="efd06-147">See Also</span></span>  
 <span data-ttu-id="efd06-148">[데이터베이스 엔진에 암호화 연결 사용&#40;SQL Server 구성 관리자&#41;](../../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md) </span><span class="sxs-lookup"><span data-stu-id="efd06-148">[Enable Encrypted Connections to the Database Engine &#40;SQL Server Configuration Manager&#41;](../../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md) </span></span>  
 <span data-ttu-id="efd06-149">[Replication Security Best Practices](replication-security-best-practices.md) </span><span class="sxs-lookup"><span data-stu-id="efd06-149">[Replication Security Best Practices](replication-security-best-practices.md) </span></span>  
 [<span data-ttu-id="efd06-150">SQL Server 복제 보안</span><span class="sxs-lookup"><span data-stu-id="efd06-150">SQL Server Replication Security</span></span>](view-and-modify-replication-security-settings.md)  
  
  
