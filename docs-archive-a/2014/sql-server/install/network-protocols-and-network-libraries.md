---
title: 네트워크 프로토콜 및 네트워크 라이브러리 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- protocols [SQL Server]
- configuration options [SQL Server], protocols
- network libraries [SQL Server]
- protocols [SQL Server], about network protocols
- pipes [SQL Server]
- network protocols [SQL Server]
- default SQL Server configurations
- library [SQL Server]
- network protocols [SQL Server], about network protocols
- configuration options [SQL Server], libraries
ms.assetid: 8cd437f6-9af1-44ce-9cb0-4d10c83da9ce
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8be012ea2bc9499a99ca7763446c6f26cf219a18
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660291"
---
# <a name="network-protocols-and-network-libraries"></a><span data-ttu-id="47018-102">네트워크 프로토콜 및 네트워크 라이브러리</span><span class="sxs-lookup"><span data-stu-id="47018-102">Network Protocols and Network Libraries</span></span>
  <span data-ttu-id="47018-103">서버는 한 번에 여러 네트워크 프로토콜을 수신하거나 모니터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47018-103">A server can listen on, or monitor, multiple network protocols at one time.</span></span> <span data-ttu-id="47018-104">이때 각각의 프로토콜을 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="47018-104">However, each protocol must be configured.</span></span> <span data-ttu-id="47018-105">특정 프로토콜을 구성하지 않으면 서버가 해당 프로토콜에서 수신할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47018-105">If a particular protocol is not configured, the server cannot listen on that protocol.</span></span> <span data-ttu-id="47018-106">설치 후 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구성 관리자를 사용하여 프로토콜 구성을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47018-106">After installation, you can change the protocol configurations using the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager.</span></span>  
  
## <a name="default-sql-server-network-configuration"></a><span data-ttu-id="47018-107">기본 SQL Server 네트워크 구성</span><span class="sxs-lookup"><span data-stu-id="47018-107">Default SQL Server Network Configuration</span></span>  
 <span data-ttu-id="47018-108">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 의 기본 인스턴스는 TCP/IP 포트 1433 및 명명된 파이프 \\\\.\pipe\sql\query에 대해 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="47018-108">A default instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is configured for TCP/IP port 1433, and named pipe \\\\.\pipe\sql\query.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="47018-109">명명된 인스턴스는 포트 번호가 운영 체제에서 할당되는 TCP 동적 포트로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="47018-109">named instances are configured for TCP dynamic ports, with a port number assigned by the operating system.</span></span>  
  
 <span data-ttu-id="47018-110">예를 들어 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 연결이 특정 포트 주소를 통과하도록 구성된 방화벽 서버를 통과해야 하는 경우와 같이 동적 포트 주소를 사용할 수 없는 경우에는</span><span class="sxs-lookup"><span data-stu-id="47018-110">If you cannot use dynamic port addresses (for example, when [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connections must pass through a firewall server configured to pass through specific port addresses).</span></span> <span data-ttu-id="47018-111">할당되지 않은 포트 번호를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="47018-111">Select an unassigned port number.</span></span> <span data-ttu-id="47018-112">포트 번호 할당은 Internet Assigned Numbers Authority에서 관리하며 [http://www.iana.org](https://go.microsoft.com/fwlink/?LinkId=48844)에 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="47018-112">Port number assignments are managed by the Internet Assigned Numbers Authority and are listed at [http://www.iana.org](https://go.microsoft.com/fwlink/?LinkId=48844).</span></span>  
  
 <span data-ttu-id="47018-113">보안을 향상시키기 위해 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가 설치될 때 네트워크 연결이 부분적으로만 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="47018-113">To enhance security, network connectivity is not fully enabled when [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is installed.</span></span> <span data-ttu-id="47018-114">설치가 완료된 후 네트워크 프로토콜을 설정, 해제 및 구성하려면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구성 관리자의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 네트워크 구성 영역을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="47018-114">To enable, disable, and configure network protocols after Setup is complete, use the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Network Configuration area of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager.</span></span>  
  
## <a name="server-message-block-protocol"></a><span data-ttu-id="47018-115">서버 메시지 블록 프로토콜</span><span class="sxs-lookup"><span data-stu-id="47018-115">Server Message Block Protocol</span></span>  
 <span data-ttu-id="47018-116">경계 네트워크에 연결된 서버는 SMB(서버 메시지 블록)를 포함해 불필요한 모든 프로토콜을 비활성화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="47018-116">Servers in the perimeter network should have all unnecessary protocols disabled, including server message block (SMB).</span></span> <span data-ttu-id="47018-117">웹 서버 및 DNS(Domain Name System) 서버에는 SMB가 필요 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47018-117">Web servers and Domain Name System (DNS) servers do not require SMB.</span></span> <span data-ttu-id="47018-118">이 프로토콜은 사용자 목록 노출 위협에 대비하여 비활성화되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="47018-118">This protocol should be disabled to counter the threat of user enumeration.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="47018-119">서버 메시지 블록을 사용하지 않도록 설정하면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 또는 Windows 클러스터 서비스가 원격 파일 공유에 액세스할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47018-119">Disabling Server Message Block will block the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] or Windows Cluster service from accessing the remote file share.</span></span> <span data-ttu-id="47018-120">다음 중 하나를 수행하거나 계획 중인 경우 SMB를 사용하지 않도록 설정하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="47018-120">Do not disable SMB if you do or plan to do one of the following:</span></span>  
> 
>  -   <span data-ttu-id="47018-121">Windows 클러스터 노드 및 파일 공유 주 쿼럼 모드 사용</span><span class="sxs-lookup"><span data-stu-id="47018-121">Use Windows Cluster Node and File Share Majority Quorum mode</span></span>  
> -   <span data-ttu-id="47018-122">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 설치 중에 SMB 파일 공유를 데이터 디렉터리로 지정</span><span class="sxs-lookup"><span data-stu-id="47018-122">Specify an SMB file share as the data directory during [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installation</span></span>  
> -   <span data-ttu-id="47018-123">SMB 파일 공유에 데이터베이스 파일 만들기</span><span class="sxs-lookup"><span data-stu-id="47018-123">Create a database file on an SMB file share</span></span>  
  
#### <a name="to-disable-smb"></a><span data-ttu-id="47018-124">SMB를 비활성화하려면</span><span class="sxs-lookup"><span data-stu-id="47018-124">To disable SMB</span></span>  
  
1.  <span data-ttu-id="47018-125">**시작** 메뉴에서 **설정**을 가리킨 다음 **네트워크 및 전화 접속 연결**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="47018-125">On the **Start** menu, point to **Settings**, and then click **Network and Dial-up Connections**.</span></span>  
  
     <span data-ttu-id="47018-126">인터넷 연결을 마우스 오른쪽 단추로 클릭한 후 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="47018-126">Right-click the Internet-facing connection, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="47018-127">**Microsoft 네트워크용 클라이언트** 확인란을 선택한 다음 **제거**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="47018-127">Select the **Client for Microsoft Networks** check box, and then click **Uninstall**.</span></span>  
  
3.  <span data-ttu-id="47018-128">제거 단계를 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="47018-128">Follow the uninstall steps.</span></span>  
  
4.  <span data-ttu-id="47018-129">**Microsoft 네트워크용 파일 및 프린터 공유**를 선택한 다음 **제거**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="47018-129">Select **File and Printer Sharing for Microsoft Networks**, and then click **Uninstall**.</span></span>  
  
5.  <span data-ttu-id="47018-130">제거 단계를 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="47018-130">Follow the uninstall steps.</span></span>  
  
#### <a name="to-disable-smb-on-servers-accessible-from-the-internet"></a><span data-ttu-id="47018-131">인터넷에서 액세스 가능한 서버의 SMB를 비활성화하려면</span><span class="sxs-lookup"><span data-stu-id="47018-131">To disable SMB on servers accessible from the Internet</span></span>  
  
-   <span data-ttu-id="47018-132">로컬 영역 연결 속성에서 **인터넷 프로토콜(TCP/IP) 속성** 대화 상자를 사용하여 **Microsoft 네트워크용 파일 및 프린터 공유** 및 **Microsoft 네트워크용 클라이언트**를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="47018-132">In the Local Area Connection properties, use the **Transmission Control Protocol/Internet Protocol (TCP/IP) properties** dialog box to remove **File and Printer Sharing for Microsoft Networks** and **Client for Microsoft Networks**.</span></span>  
  
## <a name="endpoints"></a><span data-ttu-id="47018-133">엔드포인트</span><span class="sxs-lookup"><span data-stu-id="47018-133">Endpoints</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="47018-134">에는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 연결에 대한 새로운 개념이 도입되었습니다. 즉, 연결이 서버 끝에서 [!INCLUDE[tsql](../../includes/tsql-md.md)]*엔드포인트*로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="47018-134">introduces a new concept for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connections; the connection is represented on the server end by a [!INCLUDE[tsql](../../includes/tsql-md.md)]*endpoint*.</span></span> <span data-ttu-id="47018-135">[!INCLUDE[tsql](../../includes/tsql-md.md)] 엔드포인트에 대해 사용 권한을 부여, 취소 및 거부할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47018-135">Permissions can be granted, revoked, and denied for [!INCLUDE[tsql](../../includes/tsql-md.md)] endpoints.</span></span> <span data-ttu-id="47018-136">기본적으로 모든 사용자는 sysadmin 그룹의 멤버나 엔드포인트 소유자에 의해 사용 권한이 거부 또는 취소되지 않은 한 엔드포인트에 액세스할 권한이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47018-136">By default, all users have permissions to access an endpoint unless the permissions are denied or revoked by a member of the sysadmin group or by the endpoint owner.</span></span> <span data-ttu-id="47018-137">GRANT, REVOKE 및 DENY ENDPOINT 구문에는 관리자가 엔드포인트의 카탈로그 뷰에서 가져와야 하는 엔드포인트 ID가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="47018-137">The GRANT, REVOKE, and DENY ENDPOINT syntax uses an endpoint ID that the administrator must get from the endpoint's catalog view.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="47018-138">설치 프로그램에서는 지원되는 모든 네트워크 프로토콜뿐만 아니라 관리자 전용 연결에 대해서도 [!INCLUDE[tsql](../../includes/tsql-md.md)] 엔드포인트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="47018-138">Setup creates [!INCLUDE[tsql](../../includes/tsql-md.md)] endpoints for all supported network protocols, as well as for the dedicated administrator connection.</span></span>  
  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] <span data-ttu-id="47018-139">설치 프로그램에서 만드는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 엔드포인트는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="47018-139">endpoints created by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup are as follows:</span></span>  
  
-   [!INCLUDE[tsql](../../includes/tsql-md.md)] <span data-ttu-id="47018-140">로컬 컴퓨터</span><span class="sxs-lookup"><span data-stu-id="47018-140">local machine</span></span>  
  
-   [!INCLUDE[tsql](../../includes/tsql-md.md)] <span data-ttu-id="47018-141">명명된 파이프</span><span class="sxs-lookup"><span data-stu-id="47018-141">named pipes</span></span>  
  
-   [!INCLUDE[tsql](../../includes/tsql-md.md)] <span data-ttu-id="47018-142">기본 TCP</span><span class="sxs-lookup"><span data-stu-id="47018-142">default TCP</span></span>  
  
 <span data-ttu-id="47018-143">엔드포인트에 대한 자세한 내용은 [여러 TCP 포트에서 수신하도록 데이터베이스 엔진 구성](../../database-engine/configure-windows/configure-the-database-engine-to-listen-on-multiple-tcp-ports.md) 및 [엔드포인트 카탈로그 뷰&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/endpoints-catalog-views-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="47018-143">For more information about endpoints, see [Configure the Database Engine to Listen on Multiple TCP Ports](../../database-engine/configure-windows/configure-the-database-engine-to-listen-on-multiple-tcp-ports.md) and [Endpoints Catalog Views &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/endpoints-catalog-views-transact-sql).</span></span>  
  
 <span data-ttu-id="47018-144">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 네트워크 구성에 대한 자세한 내용은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 온라인 설명서에서 다음 항목을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="47018-144">For more information about [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] network configurations, see the following topic in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online:</span></span>  
  
-   [<span data-ttu-id="47018-145">서버 네트워크 구성</span><span class="sxs-lookup"><span data-stu-id="47018-145">Server Network Configuration</span></span>](../../database-engine/configure-windows/server-network-configuration.md)  
  
## <a name="see-also"></a><span data-ttu-id="47018-146">참고 항목</span><span class="sxs-lookup"><span data-stu-id="47018-146">See Also</span></span>  
 <span data-ttu-id="47018-147">[노출 영역 구성](../../relational-databases/security/surface-area-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="47018-147">[Surface Area Configuration](../../relational-databases/security/surface-area-configuration.md) </span></span>  
 <span data-ttu-id="47018-148">[SQL Server 설치에 대한 보안 고려 사항](../../../2014/sql-server/install/security-considerations-for-a-sql-server-installation.md) </span><span class="sxs-lookup"><span data-stu-id="47018-148">[Security Considerations for a SQL Server Installation](../../../2014/sql-server/install/security-considerations-for-a-sql-server-installation.md) </span></span>  
 [<span data-ttu-id="47018-149">SQL Server 설치 계획</span><span class="sxs-lookup"><span data-stu-id="47018-149">Planning a SQL Server Installation</span></span>](../../../2014/sql-server/install/planning-a-sql-server-installation.md)  
  
  
