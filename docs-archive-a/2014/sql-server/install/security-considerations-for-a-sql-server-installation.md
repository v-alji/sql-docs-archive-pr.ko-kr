---
title: SQL Server 설치에 대한 보안 고려 사항 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- firewall systems [SQL Server]
- server message blocks [SQL Server]
- disabling protocols
- security [SQL Server], installations
- protocols [SQL Server], disabling
- NetBIOS [SQL Server]
- services [SQL Server], security
- SMB [SQL Server]
- isolating services [SQL Server]
- Setup [SQL Server], security
- low SQL Server installation privileges
- NTFS [SQL Server]
- physical security [SQL Server]
- file system security [SQL Server]
- installing SQL Server, security
ms.assetid: cf96155f-30a8-48b7-8d6b-24ce90dafdc7
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ed0cd42d51c2b4db96778182c60f1ad3d13a098c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653133"
---
# <a name="security-considerations-for-a-sql-server-installation"></a><span data-ttu-id="abd43-102">SQL Server 설치에 대한 보안 고려 사항</span><span class="sxs-lookup"><span data-stu-id="abd43-102">Security Considerations for a SQL Server Installation</span></span>
  <span data-ttu-id="abd43-103">보안은 모든 제품과 모든 비즈니스에서 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="abd43-103">Security is important for every product and every business.</span></span> <span data-ttu-id="abd43-104">간단한 권장 사항을 따르면 많은 보안상의 취약점을 방지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="abd43-104">By following simple best practices, you can avoid many security vulnerabilities.</span></span> <span data-ttu-id="abd43-105">이 항목에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 를 설치하기 전과 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]를 설치한 후에 모두 고려해야 하는 보안 권장 사항에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="abd43-105">This topic discusses some security best practices that you should consider both before you install [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and after you install [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="abd43-106">특정 기능에 대한 보안 지침은 해당 기능에 대한 참조 항목에 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="abd43-106">Security guidance for specific features is included in the reference topics for those features.</span></span>  
  
## <a name="before-installing-ssnoversion"></a><span data-ttu-id="abd43-107">다음 설치 전 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="abd43-107">Before Installing [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span></span>  
 <span data-ttu-id="abd43-108">서버 환경을 설정하는 경우 다음 권장 사항을 따르십시오.</span><span class="sxs-lookup"><span data-stu-id="abd43-108">Follow these best practices when you set up the server environment:</span></span>  
  
-   [<span data-ttu-id="abd43-109">물리적 보안 강화</span><span class="sxs-lookup"><span data-stu-id="abd43-109">Enhance physical security</span></span>](#physical_security)  
  
-   [<span data-ttu-id="abd43-110">방화벽 사용</span><span class="sxs-lookup"><span data-stu-id="abd43-110">Use firewalls</span></span>](#firewalls)  
  
-   [<span data-ttu-id="abd43-111">서비스 격리</span><span class="sxs-lookup"><span data-stu-id="abd43-111">Isolate services</span></span>](#isolated_services)  
  
-   [<span data-ttu-id="abd43-112">보안 파일 시스템 구성</span><span class="sxs-lookup"><span data-stu-id="abd43-112">Configure a secure file system</span></span>](#sa_with_least_privileges)  
  
-   [<span data-ttu-id="abd43-113">NetBIOS 및 서버 메시지 블록 비활성화</span><span class="sxs-lookup"><span data-stu-id="abd43-113">Disable NetBIOS and server message block</span></span>](#disabled_protocols)  
  
-   [<span data-ttu-id="abd43-114">도메인 컨트롤러에 SQL Server 설치</span><span class="sxs-lookup"><span data-stu-id="abd43-114">Installing SQL Server on a domain controller</span></span>](../../../2014/sql-server/install/security-considerations-for-a-sql-server-installation.md#Install_DC)  
  
###  <a name="enhance-physical-security"></a><a name="physical_security"></a> <span data-ttu-id="abd43-115">Enhance Physical Security</span><span class="sxs-lookup"><span data-stu-id="abd43-115">Enhance Physical Security</span></span>  
 <span data-ttu-id="abd43-116">물리적 및 논리적 격리는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 보안의 기반이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="abd43-116">Physical and logical isolation make up the foundation of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] security.</span></span> <span data-ttu-id="abd43-117">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 설치의 물리적 보안을 강화하려면 다음 태스크를 수행하십시오.</span><span class="sxs-lookup"><span data-stu-id="abd43-117">To enhance the physical security of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installation, do the following tasks:</span></span>  
  
-   <span data-ttu-id="abd43-118">허가받은 사람만 출입할 수 있는 공간에 서버를 둡니다.</span><span class="sxs-lookup"><span data-stu-id="abd43-118">Place the server in a room accessible only to authorized persons.</span></span>  
  
-   <span data-ttu-id="abd43-119">데이터베이스를 호스팅하는 컴퓨터를 물리적으로 보호된 위치에 둡니다. 누수 및 화재 감지 또는 억제 시스템을 갖춘 밀폐된 컴퓨터실이 가장 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="abd43-119">Place computers that host a database in a physically protected location, ideally a locked computer room with monitored flood detection and fire detection or suppression systems.</span></span>  
  
-   <span data-ttu-id="abd43-120">데이터베이스를 기업 인트라넷의 보안 영역에 설치하고 SQL Server를 인터넷에 직접 연결하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="abd43-120">Install databases in the secure zone of the corporate intranet and do not connect your SQL Servers directly to the Internet.</span></span>  
  
-   <span data-ttu-id="abd43-121">모든 데이터를 정기적으로 백업하고 멀리 떨어진 지역에 백업을 안전하게 보관합니다.</span><span class="sxs-lookup"><span data-stu-id="abd43-121">Back up all data regularly and secure the backups in an off-site location.</span></span>  
  
###  <a name="use-firewalls"></a><a name="firewalls"></a> <span data-ttu-id="abd43-122">Use Firewalls</span><span class="sxs-lookup"><span data-stu-id="abd43-122">Use Firewalls</span></span>  
 <span data-ttu-id="abd43-123">방화벽은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 설치의 보안에 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="abd43-123">Firewalls are important to help secure the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installation.</span></span> <span data-ttu-id="abd43-124">방화벽의 효율적인 작동을 위해 지켜야 할 지침은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="abd43-124">Firewalls will be most effective if you follow these guidelines:</span></span>  
  
-   <span data-ttu-id="abd43-125">방화벽을 서버와 인터넷 사이에 둡니다.</span><span class="sxs-lookup"><span data-stu-id="abd43-125">Put a firewall between the server and the Internet.</span></span> <span data-ttu-id="abd43-126">방화벽을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="abd43-126">Enable your firewall.</span></span> <span data-ttu-id="abd43-127">방화벽이 해제되어 있으면 설정하고</span><span class="sxs-lookup"><span data-stu-id="abd43-127">If your firewall is turned off, turn it on.</span></span> <span data-ttu-id="abd43-128">방화벽이 설정되어 있으면 해제하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="abd43-128">If your firewall is turned on, do not turn it off.</span></span>  
  
-   <span data-ttu-id="abd43-129">네트워크를 방화벽으로 분리된 여러 보안 영역으로 나눕니다.</span><span class="sxs-lookup"><span data-stu-id="abd43-129">Divide the network into security zones separated by firewalls.</span></span> <span data-ttu-id="abd43-130">모든 트래픽을 차단한 다음 필요한 것만 선택적으로 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="abd43-130">Block all traffic, and then selectively admit only what is required.</span></span>  
  
-   <span data-ttu-id="abd43-131">다중 계층 환경에서는 여러 방화벽을 사용하여 스크린된 서브넷을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="abd43-131">In a multi-tier environment, use multiple firewalls to create screened subnets.</span></span>  
  
-   <span data-ttu-id="abd43-132">Windows 도메인 내에 서버를 설치할 경우 Windows 인증을 허용하도록 내부 방화벽을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="abd43-132">When you are installing the server inside a Windows domain, configure interior firewalls to allow Windows Authentication.</span></span>  
  
-   <span data-ttu-id="abd43-133">애플리케이션에서 분산 트랜잭션을 사용하는 경우 MS DTC( [!INCLUDE[msCoName](../../includes/msconame-md.md)] Distributed Transaction Coordinator) 트래픽이 개별 MS DTC 인스턴스 간에 전달될 수 있도록 방화벽을 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="abd43-133">If your application uses distributed transactions, you might have to configure the firewall to allow [!INCLUDE[msCoName](../../includes/msconame-md.md)] Distributed Transaction Coordinator (MS DTC) traffic to flow between separate MS DTC instances.</span></span> <span data-ttu-id="abd43-134">또한 MS DTC와 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]와 같은 리소스 관리자 간에도 트래픽이 전달되도록 방화벽을 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="abd43-134">You will also have to configure the firewall to allow traffic to flow between the MS DTC and resource managers such as [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="abd43-135">기본 Windows 방화벽 설정 방법과 [!INCLUDE[ssDE](../../includes/ssde-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]및 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]에 영향을 주는 TCP 포트에 대한 자세한 내용은 [SQL Server 액세스를 허용하도록 Windows 방화벽 구성](../../../2014/sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="abd43-135">For more information about the default Windows firewall settings, and a description of the TCP ports that affect the [!INCLUDE[ssDE](../../includes/ssde-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], and [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], see [Configure the Windows Firewall to Allow SQL Server Access](../../../2014/sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md).</span></span>  
  
###  <a name="isolate-services"></a><a name="isolated_services"></a> <span data-ttu-id="abd43-136">Isolate Services</span><span class="sxs-lookup"><span data-stu-id="abd43-136">Isolate Services</span></span>  
 <span data-ttu-id="abd43-137">서비스를 격리하면 하나의 손상된 서비스가 다른 서비스를 손상시키는 위험을 줄일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="abd43-137">Isolating services reduces the risk that one compromised service could be used to compromise others.</span></span> <span data-ttu-id="abd43-138">서비스를 격리하려면 다음 지침을 따르십시오.</span><span class="sxs-lookup"><span data-stu-id="abd43-138">To isolate services, consider the following guidelines:</span></span>  
  
-   <span data-ttu-id="abd43-139">별도의 Windows 계정으로 별도의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 서비스를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="abd43-139">Run separate [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services under separate Windows accounts.</span></span> <span data-ttu-id="abd43-140">가능하면 각 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 서비스에 별도의 낮은 권한의 Windows 또는 로컬 사용자 계정을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="abd43-140">Whenever possible, use separate, low-rights Windows or Local user accounts for each [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service.</span></span> <span data-ttu-id="abd43-141">자세한 내용은 [Windows 서비스 계정 및 권한 구성](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="abd43-141">For more information, see [Configure Windows Service Accounts and Permissions](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).</span></span>  
  
###  <a name="configure-a-secure-file-system"></a><a name="sa_with_least_privileges"></a> <span data-ttu-id="abd43-142">Configure a Secure File System</span><span class="sxs-lookup"><span data-stu-id="abd43-142">Configure a Secure File System</span></span>  
 <span data-ttu-id="abd43-143">올바른 파일 시스템을 사용하면 보안이 강화됩니다.</span><span class="sxs-lookup"><span data-stu-id="abd43-143">Using the correct file system increases security.</span></span> <span data-ttu-id="abd43-144">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 설치의 경우 다음 태스크를 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="abd43-144">For [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installations, you should do the following tasks:</span></span>  
  
-   <span data-ttu-id="abd43-145">NTFS 파일 시스템(NTFS)을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="abd43-145">Use the NTFS file system (NTFS).</span></span> <span data-ttu-id="abd43-146">NTFS는 FAT 파일 시스템에 비해 안정적이고 복구 가능하기 때문에 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 설치에 적합한 파일 시스템입니다.</span><span class="sxs-lookup"><span data-stu-id="abd43-146">NTFS is the preferred file system for installations of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] because it is more stable and recoverable than FAT file systems.</span></span> <span data-ttu-id="abd43-147">NTFS에서는 또한 파일 및 디렉터리 ACL(액세스 제어 목록) 및 EFS(파일 시스템 암호화) 파일 암호화와 같은 보안 옵션도 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="abd43-147">NTFS also enables security options like file and directory access control lists (ACLs) and Encrypting File System (EFS) file encryption.</span></span> <span data-ttu-id="abd43-148">설치 중 NTFS가 감지되면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 는 적절한 ACL을 레지스트리 키와 파일에 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="abd43-148">During installation, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will set appropriate ACLs on registry keys and files if it detects NTFS.</span></span> <span data-ttu-id="abd43-149">이러한 사용 권한은 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="abd43-149">These permissions should not be changed.</span></span> <span data-ttu-id="abd43-150">이후 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 릴리스에서는 FAT 파일 시스템이 있는 컴퓨터에 대한 설치를 지원하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="abd43-150">Future releases of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] might not support installation on computers with FAT file systems.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="abd43-151">EFS를 사용할 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]를 실행하는 계정의 ID로 데이터베이스 파일이 암호화됩니다.</span><span class="sxs-lookup"><span data-stu-id="abd43-151">If you use EFS, database files will be encrypted under the identity of the account running [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="abd43-152">파일 해독도 이 계정으로만 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="abd43-152">Only this account will be able to decrypt the files.</span></span> <span data-ttu-id="abd43-153">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]를 실행하는 계정을 변경해야 하는 경우 먼저 이전 계정으로 파일을 해독한 다음 새 계정으로 파일을 다시 암호화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="abd43-153">If you must change the account that runs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], you should first decrypt the files under the old account and then re-encrypt them under the new account.</span></span>  
  
-   <span data-ttu-id="abd43-154">중요한 데이터 파일에는 RAID(Redundant Array of Independent Disks)를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="abd43-154">Use a redundant array of independent disks (RAID) for critical data files.</span></span>  
  
###  <a name="disable-netbios-and-server-message-block"></a><a name="disabled_protocols"></a> <span data-ttu-id="abd43-155">Disable NetBIOS and Server Message Block</span><span class="sxs-lookup"><span data-stu-id="abd43-155">Disable NetBIOS and Server Message Block</span></span>  
 <span data-ttu-id="abd43-156">경계 네트워크에 있는 서버에는 NetBIOS 및 SMB(서버 메시지 블록) 등의 불필요한 모든 프로토콜이 비활성화되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="abd43-156">Servers in the perimeter network should have all unnecessary protocols disabled, including NetBIOS and server message block (SMB).</span></span>  
  
 <span data-ttu-id="abd43-157">NetBIOS는 다음 포트를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="abd43-157">NetBIOS uses the following ports:</span></span>  
  
-   <span data-ttu-id="abd43-158">UDP/137(NetBIOS 이름 서비스)</span><span class="sxs-lookup"><span data-stu-id="abd43-158">UDP/137 (NetBIOS name service)</span></span>  
  
-   <span data-ttu-id="abd43-159">UDP/138(NetBIOS 데이터그램 서비스)</span><span class="sxs-lookup"><span data-stu-id="abd43-159">UDP/138 (NetBIOS datagram service)</span></span>  
  
-   <span data-ttu-id="abd43-160">TCP/139(NetBIOS 세션 서비스)</span><span class="sxs-lookup"><span data-stu-id="abd43-160">TCP/139 (NetBIOS session service)</span></span>  
  
 <span data-ttu-id="abd43-161">SMB는 다음 포트를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="abd43-161">SMB uses the following ports:</span></span>  
  
-   <span data-ttu-id="abd43-162">TCP/139</span><span class="sxs-lookup"><span data-stu-id="abd43-162">TCP/139</span></span>  
  
-   <span data-ttu-id="abd43-163">TCP/445</span><span class="sxs-lookup"><span data-stu-id="abd43-163">TCP/445</span></span>  
  
 <span data-ttu-id="abd43-164">웹 서버 및 DNS(Domain Name System) 서버에는 NetBIOS 또는 SMB가 필요 없습니다.</span><span class="sxs-lookup"><span data-stu-id="abd43-164">Web servers and Domain Name System (DNS) servers do not require NetBIOS or SMB.</span></span> <span data-ttu-id="abd43-165">이러한 서버에서 두 프로토콜을 모두 비활성화하여 사용자 목록 노출 위협을 줄이십시오.</span><span class="sxs-lookup"><span data-stu-id="abd43-165">On these servers, disable both protocols to reduce the threat of user enumeration.</span></span>  
  
###  <a name="installing-ssnoversion-on-a-domain-controller"></a><a name="Install_DC"></a> <span data-ttu-id="abd43-166">도메인 컨트롤러에 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 설치</span><span class="sxs-lookup"><span data-stu-id="abd43-166">Installing [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on a domain controller</span></span>  
 <span data-ttu-id="abd43-167">보안상의 이유로 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 는 도메인 컨트롤러에 설치하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="abd43-167">For security reasons, we recommend that you do not install [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] on a domain controller.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="abd43-168">설치 프로그램은 도메인 컨트롤러 컴퓨터에 설치하는 것을 차단하지는 않지만 다음과 같은 제한 사항을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="abd43-168">Setup will not block installation on a computer that is a domain controller, but the following limitations apply:</span></span>  
  
-   <span data-ttu-id="abd43-169">도메인 컨트롤러에서는 로컬 서비스 계정으로 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 서비스를 실행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="abd43-169">You cannot run [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services on a domain controller under a local service account.</span></span>  
  
-   <span data-ttu-id="abd43-170">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 를 컴퓨터에 설치한 후에는 도메인 멤버에서 도메인 컨트롤러로 컴퓨터를 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="abd43-170">After [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is installed on a computer, you cannot change the computer from a domain member to a domain controller.</span></span> <span data-ttu-id="abd43-171">호스트 컴퓨터를 도메인 컨트롤러로 변경하려면 먼저 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 를 제거해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="abd43-171">You must uninstall [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] before you change the host computer to a domain controller.</span></span>  
  
-   <span data-ttu-id="abd43-172">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 를 컴퓨터에 설치한 후에는 도메인 컨트롤러에서 도메인 멤버로 컴퓨터를 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="abd43-172">After [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is installed on a computer, you cannot change the computer from a domain controller to a domain member.</span></span> <span data-ttu-id="abd43-173">호스트 컴퓨터를 도메인 멤버로 변경하려면 먼저 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 를 제거해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="abd43-173">You must uninstall [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] before you change the host computer to a domain member.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="abd43-174">장애 조치(failover) 클러스터 인스턴스는 클러스터 노드가 도메인 컨트롤러인 경우 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="abd43-174">failover cluster instances are not supported where cluster nodes are domain controllers.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="abd43-175">설치 프로그램은 읽기 전용 도메인 컨트롤러에서 보안 그룹을 만들거나 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 서비스 계정을 프로비전할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="abd43-175">Setup cannot create security groups or provision [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service accounts on a read-only domain controller.</span></span> <span data-ttu-id="abd43-176">이 경우 설치 프로그램에서 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="abd43-176">In this scenario, Setup will fail.</span></span>  
  
## <a name="during-or-after-installation-of-ssnoversion"></a><span data-ttu-id="abd43-177">다음 설치 도중 또는 설치 후 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="abd43-177">During or After Installation of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span></span>  
 <span data-ttu-id="abd43-178">설치 후에도 계정 및 인증 모드에 대한 권장 사항을 수행하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 의 보안을 강화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="abd43-178">After installation, you can enhance the security of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installation by following these best practices regarding accounts and authentication modes:</span></span>  
  
 <span data-ttu-id="abd43-179">**서비스 계정**</span><span class="sxs-lookup"><span data-stu-id="abd43-179">**Service accounts**</span></span>  
  
-   <span data-ttu-id="abd43-180">가장 낮은 사용자 권한을 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 서비스를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="abd43-180">Run [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services by using the lowest possible permissions.</span></span>  
  
-   <span data-ttu-id="abd43-181">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 서비스를 낮은 권한을 가진 Windows 로컬 사용자 계정 또는 도메인 사용자 계정과 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="abd43-181">Associate [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services with low privileged Windows local user accounts, or domain user accounts.</span></span>  
  
-   <span data-ttu-id="abd43-182">자세한 내용은 [Windows 서비스 계정 및 권한 구성](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="abd43-182">For more information, see [Configure Windows Service Accounts and Permissions](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).</span></span>  
  
 <span data-ttu-id="abd43-183">**인증 모드**</span><span class="sxs-lookup"><span data-stu-id="abd43-183">**Authentication mode**</span></span>  
  
-   <span data-ttu-id="abd43-184">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]연결을 위해 Windows 인증이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="abd43-184">Require Windows Authentication for connections to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="abd43-185">Kerberos 인증 사용</span><span class="sxs-lookup"><span data-stu-id="abd43-185">Use Kerberos authentication.</span></span> <span data-ttu-id="abd43-186">자세한 내용은 [Kerberos 연결의 서비스 사용자 이름 등록](../../database-engine/configure-windows/register-a-service-principal-name-for-kerberos-connections.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="abd43-186">For more information, see [Register a Service Principal Name for Kerberos Connections](../../database-engine/configure-windows/register-a-service-principal-name-for-kerberos-connections.md).</span></span>  
  
 <span data-ttu-id="abd43-187">**강력한 암호**</span><span class="sxs-lookup"><span data-stu-id="abd43-187">**Strong passwords**</span></span>  
  
-   <span data-ttu-id="abd43-188">`sa` 계정에는 항상 강력한 암호를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="abd43-188">Always assign a strong password to the `sa` account.</span></span>  
  
-   <span data-ttu-id="abd43-189">암호 강도 및 만료를 검사하는 암호 정책을 항상 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="abd43-189">Always enable password policy checking for password strength and expiration.</span></span>  
  
-   <span data-ttu-id="abd43-190">모든 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그인에 대해 항상 강력한 암호를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="abd43-190">Always use strong passwords for all [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] logins.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="abd43-191">[!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] 설치 중에 BUILTIN\Users 그룹에 대한 로그인이 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="abd43-191">During setup of [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] a login is added for the BUILTIN\Users group.</span></span> <span data-ttu-id="abd43-192">이 로그인을 사용하면 컴퓨터의 모든 인증된 사용자가 public 역할의 멤버로 [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] 인스턴스에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="abd43-192">This allows all authenticated users of the computer to access the instance of [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] as a member of the public role.</span></span> <span data-ttu-id="abd43-193">BUILTIN\Users 로그인은 개별 로그인이 있거나 로그인이 있는 기타 Windows 그룹의 멤버인 컴퓨터 사용자에 대한 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 액세스를 제한하기 위해 안전하게 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="abd43-193">The BUILTIN\Users login can be safely removed to restrict [!INCLUDE[ssDE](../../includes/ssde-md.md)] access to computer users who have individual logins or are members of other Windows groups with logins.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abd43-194">참고 항목</span><span class="sxs-lookup"><span data-stu-id="abd43-194">See Also</span></span>  
 <span data-ttu-id="abd43-195">[SQL Server 2014를 설치 하기 위한 하드웨어 및 소프트웨어 요구 사항](hardware-and-software-requirements-for-installing-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="abd43-195">[Hardware and Software Requirements for Installing SQL Server 2014](hardware-and-software-requirements-for-installing-sql-server.md) </span></span>  
 <span data-ttu-id="abd43-196">[네트워크 프로토콜 및 네트워크 라이브러리](../../../2014/sql-server/install/network-protocols-and-network-libraries.md) </span><span class="sxs-lookup"><span data-stu-id="abd43-196">[Network Protocols and Network Libraries](../../../2014/sql-server/install/network-protocols-and-network-libraries.md) </span></span>  
 [<span data-ttu-id="abd43-197">Kerberos 연결의 서비스 사용자 이름 등록</span><span class="sxs-lookup"><span data-stu-id="abd43-197">Register a Service Principal Name for Kerberos Connections</span></span>](../../database-engine/configure-windows/register-a-service-principal-name-for-kerberos-connections.md)  
  
  
