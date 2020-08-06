---
title: 배포자 보안 설정 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- security [SQL Server replication], Distributors
- Distributors [SQL Server replication], security
ms.assetid: 76d78229-0ff2-4aa4-9b4e-ad97534c5296
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d55f5e214f89b678367124da8342ec9801ab686a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638642"
---
# <a name="secure-the-distributor"></a><span data-ttu-id="252d6-102">배포자 보안 설정</span><span class="sxs-lookup"><span data-stu-id="252d6-102">Secure the Distributor</span></span>
  <span data-ttu-id="252d6-103">배포자에 연결하는 병합 에이전트에는 로그 판독기 에이전트, 스냅샷 에이전트, 큐 판독기 에이전트, 배포 에이전트 및 병합 에이전트가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="252d6-103">The following replication agents connect to the Distributor: the Log Reader Agent, Snapshot Agent, Queue Reader Agent, Distribution Agent, and Merge Agent.</span></span> <span data-ttu-id="252d6-104">필요한 최소 권한만 부여하는 원칙을 따르고 모든 암호 스토리지를 보호하면서 이러한 에이전트에 적절한 로그인을 제공하는 것이 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="252d6-104">It is important to provide an appropriate login for each of these agents while following the principle of granting the minimal rights necessary and also protecting the storage of all passwords:</span></span>  
  
-   <span data-ttu-id="252d6-105">로그인 및 암호 관리에 대한 자세한 내용은 [복제의 로그인 및 암호 관리](identity-and-access-control-replication.md#manage-logins-and-passwords-in-replication)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="252d6-105">For information about managing logins and passwords, see [Manage Logins and Passwords in Replication](identity-and-access-control-replication.md#manage-logins-and-passwords-in-replication).</span></span>  
  
-   <span data-ttu-id="252d6-106">각 에이전트에 필요한 사용 권한에 대한 자세한 내용은 [Replication Agent Security Model](replication-agent-security-model.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="252d6-106">For detailed information about the permissions required for each agent, see [Replication Agent Security Model](replication-agent-security-model.md).</span></span>  
  
 <span data-ttu-id="252d6-107">적절한 로그인 및 암호 관리를 비롯하여 **repl_distributor** 원격 서버 링크 및 **distributor_admin** 계정의 역할도 이해해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="252d6-107">In addition to managing logins and passwords appropriately, it is important to understand the role of the **repl_distributor** remote server link and the **distributor_admin** account.</span></span>  
  
## <a name="securing-the-connection-from-the-publisher-to-the-distributor"></a><span data-ttu-id="252d6-108">게시자에서 배포자로의 연결 보안</span><span class="sxs-lookup"><span data-stu-id="252d6-108">Securing the Connection from the Publisher to the Distributor</span></span>  
 <span data-ttu-id="252d6-109">관리 저장 프로시저가 게시자에서 실행되고 배포자에서 정보를 업데이트할 때 필요한 통신을 지원하기 위해 복제는 자동으로 **repl_distributor**원격 서버를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="252d6-109">To support the communication necessary when administrative stored procedures execute at the Publisher and update information at the Distributor, replication automatically configures the remote server **repl_distributor**.</span></span> <span data-ttu-id="252d6-110">**repl_distributor** 원격 서버 항목은 배포 데이터베이스가 게시자 인스턴스(로컬 배포자) 내에 포함되어 있는지 또는 원격 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스(원격 배포자) 내에 상주하는지 여부에 관계없이 배포 데이터베이스에 대한 통신에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="252d6-110">The **repl_distributor** remote server entry is used for communication to the distribution database regardless of whether the distribution database is contained within the Publisher instance (a local Distributor) or resides within a remote [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance (a remote Distributor).</span></span>  
  
 <span data-ttu-id="252d6-111">배포 데이터베이스가 로컬 인스턴스에 포함되어 있는 경우 임의의 암호가 생성되고 자동으로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="252d6-111">When the distribution database is contained on a local instance, a random password is generated and configured automatically.</span></span> <span data-ttu-id="252d6-112">배포 데이터베이스가 원격 인스턴스에 있는 경우 관리자는 게시자 및 배포자를 설치하는 동안 공유 암호를 구성합니다. 그런 다음 이 암호는 **repl_distributor** 링크를 통과하는 트래픽의 인증을 제공하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="252d6-112">When the distribution database is located on a remote instance, the administrator configures a shared password during setup of the Publisher and Distributor; this password is then used to provide authentication of traffic that traverses the **repl_distributor** link.</span></span>  
  
 <span data-ttu-id="252d6-113">배포자는 **repl_distributor** 원격 서버 항목을 사용하여 호출하는 서버가 배포자에서 게시자로 구성되었는지 확인하고 게시자가 제공한 암호의 유효성을 검사하며 실행 중에 저장 프로시저가 복제 저장 프로시저인지를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="252d6-113">The Distributor uses the **repl_distributor** remote server entry to verify that the calling server is configured as a Publisher at the Distributor, validates the password supplied by the Publisher, and validates that the stored procedure is a replication stored procedure during execution.</span></span>  
  
 <span data-ttu-id="252d6-114">설치하는 동안 **repl_distributor** 원격 서버 항목에 대해 구성된 암호는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 로그인인 **distributor_admin**과 연결되어 있으며 이 로그인은 배포자에서 **sysadmin** 고정 서버 역할에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="252d6-114">The password configured for the **repl_distributor** remote server entry during setup is associated with a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] login, **distributor_admin**, which is added to the **sysadmin** fixed server role at the Distributor.</span></span> <span data-ttu-id="252d6-115">**distributor_admin** 로그인은 복제 저장 프로시저가 배포자에 연결할 때 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="252d6-115">The **distributor_admin** login is used by replication stored procedures when connecting to the Distributor.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="252d6-116">**distributor_admin** 에 대한 암호를 수동으로 변경하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="252d6-116">Do not change the password for the **distributor_admin** manually.</span></span> <span data-ttu-id="252d6-117">암호를 변경할 때는 항상 **sp_changedistributor_password** 저장 프로시저 또는 **의** 배포자 속성 **이나** 복제 암호 업데이트 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]대화 상자를 사용하십시오. 그러면 암호 변경 내용이 로컬 게시에 자동으로 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="252d6-117">Always use the **sp_changedistributor_password** stored procedure, or the **Distributor Properties** or **Update Replication Passwords** dialog boxes in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], because password changes are then applied to local publications automatically.</span></span>  
  
## <a name="snapshot-folder-security"></a><span data-ttu-id="252d6-118">스냅샷 폴더 보안</span><span class="sxs-lookup"><span data-stu-id="252d6-118">Snapshot Folder Security</span></span>  
 <span data-ttu-id="252d6-119">스냅샷 공유에 병합 에이전트(병합 게시의 경우)나 배포 에이전트(스냅샷 또는 트랜잭션 복제의 경우)가 실행되는 계정에 대한 읽기 권한이 있고 스냅샷 에이전트가 실행되는 계정에 대한 쓰기 권한이 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="252d6-119">Ensure that the snapshot share has read access granted to the account under which the Merge Agent (for merge replication) or Distribution Agent (for snapshot or transactional replication) runs and write access granted to the account under which the Snapshot Agent runs.</span></span> <span data-ttu-id="252d6-120">스냅샷 폴더에 대한 자세한 내용은 [스냅샷 폴더 보안 설정](secure-the-snapshot-folder.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="252d6-120">For more information about the snapshot folder, see [Secure the Snapshot Folder](secure-the-snapshot-folder.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="252d6-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="252d6-121">See Also</span></span>  
 <span data-ttu-id="252d6-122">[복제 보안 설정 보기 및 수정](view-and-modify-replication-security-settings.md) </span><span class="sxs-lookup"><span data-stu-id="252d6-122">[View and Modify Replication Security Settings](view-and-modify-replication-security-settings.md) </span></span>  
 <span data-ttu-id="252d6-123">[데이터베이스 엔진에 암호화 연결 사용&#40;SQL Server 구성 관리자&#41;](../../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md) </span><span class="sxs-lookup"><span data-stu-id="252d6-123">[Enable Encrypted Connections to the Database Engine &#40;SQL Server Configuration Manager&#41;](../../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md) </span></span>  
 <span data-ttu-id="252d6-124">[Replication Security Best Practices](replication-security-best-practices.md) </span><span class="sxs-lookup"><span data-stu-id="252d6-124">[Replication Security Best Practices](replication-security-best-practices.md) </span></span>  
 [<span data-ttu-id="252d6-125">SQL Server 복제 보안</span><span class="sxs-lookup"><span data-stu-id="252d6-125">SQL Server Replication Security</span></span>](view-and-modify-replication-security-settings.md)  
  
  
