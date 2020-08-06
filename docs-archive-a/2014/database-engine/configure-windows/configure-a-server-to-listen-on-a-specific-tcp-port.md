---
title: 특정 TCP 포트에서 수신 하도록 서버 구성 (SQL Server 구성 관리자) | Microsoft Docs
ms.custom: ''
ms.date: 06/22/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- fixed port
- static ports
- ports [SQL Server], assigning numbers
- assigning port numbers
- dynamic ports [SQL Server]
- TCP/IP [SQL Server], port numbers
ms.assetid: 2276a5ed-ae3f-4855-96d8-f5bf01890640
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 4feb740910c65580e8ea3170d03481e6cb628860
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646648"
---
# <a name="configure-a-server-to-listen-on-a-specific-tcp-port-sql-server-configuration-manager"></a><span data-ttu-id="bd137-102">특정 TCP 포트로 수신하도록 서버 구성(SQL Server 구성 관리자)</span><span class="sxs-lookup"><span data-stu-id="bd137-102">Configure a Server to Listen on a Specific TCP Port (SQL Server Configuration Manager)</span></span>
  <span data-ttu-id="bd137-103">이 항목에서는 SQL Server 구성 관리자를 사용하여 특정 고정 포트에서 수신할 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 인스턴스를 구성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="bd137-103">This topic describes how to configure an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] to listen on a specific fixed port by using the SQL Server Configuration Manager.</span></span> <span data-ttu-id="bd137-104">설정된 경우 기본 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 인스턴스는 TCP 포트 1433에서 수신합니다.</span><span class="sxs-lookup"><span data-stu-id="bd137-104">If enabled, the default instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] listens on TCP port 1433.</span></span> <span data-ttu-id="bd137-105">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 및 [!INCLUDE[ssEW](../../includes/ssew-md.md)] 의 명명된 인스턴스는 동적 포트로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="bd137-105">Named instances of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] and [!INCLUDE[ssEW](../../includes/ssew-md.md)] are configured for dynamic ports.</span></span> <span data-ttu-id="bd137-106">이는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 서비스가 시작되면 해당 인스턴스가 사용 가능한 포트를 선택함을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="bd137-106">This means they select an available port when the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service is started.</span></span> <span data-ttu-id="bd137-107">방화벽을 통해 명명된 인스턴스에 연결할 경우 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 을 특정 포트에서 수신하도록 구성하면 방화벽에서 해당 포트를 열 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd137-107">When you are connecting to a named instance through a firewall, configure the [!INCLUDE[ssDE](../../includes/ssde-md.md)] to listen on a specific port, so that the appropriate port can be opened in the firewall.</span></span>  
  
 <span data-ttu-id="bd137-108">기본 Windows 방화벽 설정 방법과 데이터베이스 엔진, Analysis Services, Reporting Services 및 Integration Services에 영향을 주는 TCP 포트에 대한 설명은 [SQL Server 액세스를 허용하도록 Windows 방화벽 구성](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="bd137-108">For more information about the default Windows firewall settings, and a description of the TCP ports that affect the Database Engine, Analysis Services, Reporting Services, and Integration Services, see [Configure the Windows Firewall to Allow SQL Server Access](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md).</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="bd137-109">포트 번호를 선택할 때 특정 애플리케이션에 할당된 포트 번호 목록을 보려면 [http://www.iana.org/assignments/port-numbers](http://www.iana.org/assignments/port-numbers)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="bd137-109">When selecting a port number, consult [http://www.iana.org/assignments/port-numbers](http://www.iana.org/assignments/port-numbers) for a list of port numbers that are assigned to specific applications.</span></span> <span data-ttu-id="bd137-110">할당되지 않은 포트 번호를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="bd137-110">Select an unassigned port number.</span></span> <span data-ttu-id="bd137-111">자세한 내용은 [TCP/IP에 대한 기본 동적 포트 범위는 Windows Vista 및 Windows Server 2008에서 변경](https://support.microsoft.com/kb/929851)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="bd137-111">For more information, see [The default dynamic port range for TCP/IP has changed in Windows Vista and in Windows Server 2008](https://support.microsoft.com/kb/929851).</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="bd137-112">다시 시작할 때 데이터베이스 엔진은 새 포트에서 수신을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="bd137-112">The Database Engine begins listening on a new port when restarted.</span></span> <span data-ttu-id="bd137-113">그러나 데이터베이스 엔진이 사용하지 않을 수 있는 경우에도 구성을 변경하는 즉시 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 브라우저 서비스가 레지스트리를 모니터링하고 새 포트 번호를 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="bd137-113">However the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser service monitors the registry and reports the new port number as soon as the configuration is changed, even though the Database Engine might not be using it.</span></span> <span data-ttu-id="bd137-114">데이터베이스 엔진을 다시 시작하여 일관성을 확인하고 연결 실패를 방지합니다.</span><span class="sxs-lookup"><span data-stu-id="bd137-114">Restart the Database Engine to ensure consistency and avoid connection failures.</span></span>  
  
 <span data-ttu-id="bd137-115">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="bd137-115">**In This Topic**</span></span>  
  
-   <span data-ttu-id="bd137-116">**서버가 특정 TCP 포트에서 수신하도록 구성하려면:**</span><span class="sxs-lookup"><span data-stu-id="bd137-116">**To configure a server to listen on a specific TCP port, using:**</span></span>  
  
     [<span data-ttu-id="bd137-117">SQL Server 구성 관리자</span><span class="sxs-lookup"><span data-stu-id="bd137-117">SQL Server Configuration Manager</span></span>](#SSMSProcedure)  
  
##  <a name="using-sql-server-configuration-manager"></a><a name="SSMSProcedure"></a> <span data-ttu-id="bd137-118">SQL Server 구성 관리자 사용</span><span class="sxs-lookup"><span data-stu-id="bd137-118">Using SQL Server Configuration Manager</span></span>  
  
#### <a name="to-assign-a-tcpip-port-number-to-the-sql-server-database-engine"></a><span data-ttu-id="bd137-119">SQL Server 데이터베이스 엔진에 TCP/IP 포트 번호를 할당하려면</span><span class="sxs-lookup"><span data-stu-id="bd137-119">To assign a TCP/IP port number to the SQL Server Database Engine</span></span>  
  
1.  <span data-ttu-id="bd137-120">SQL Server 구성 관리자의 콘솔 창에서 **SQL Server 네트워크 구성**, **\<instance name>에 대한 프로토콜**을 차례로 펼친 다음 **TCP/IP**를 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bd137-120">In SQL Server Configuration Manager, in the console pane, expand **SQL Server Network Configuration**, expand **Protocols for \<instance name>**, and then double-click **TCP/IP**.</span></span>  
  
2.  <span data-ttu-id="bd137-121">**TCP/IP 속성** 대화 상자의 **IP 주소** 탭에 여러 개의 IP 주소가 **IP1**, **IP2**의 형식으로 **IPAll**까지 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="bd137-121">In the **TCP/IP Properties** dialog box, on the **IP Addresses** tab, several IP addresses appear in the format **IP1**, **IP2**, up to **IPAll**.</span></span> <span data-ttu-id="bd137-122">이러한 주소에는 루프백 어댑터의 IP 주소인 127.0.0.1이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="bd137-122">One of these is for the IP address of the loopback adapter, 127.0.0.1.</span></span> <span data-ttu-id="bd137-123">컴퓨터의 각 IP 주소에 대한 추가 IP 주소가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="bd137-123">Additional IP addresses appear for each IP Address on the computer.</span></span> <span data-ttu-id="bd137-124">각 주소를 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭하여 구성할 IP 주소를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="bd137-124">Right-click each address, and then click **Properties** to identify the IP address that you want to configure.</span></span>  
  
3.  <span data-ttu-id="bd137-125">**TCP 동적 포트** 대화 상자에 **0**이 있으면 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 이 동적 포트에서 수신한다는 표시이므로 0을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="bd137-125">If the **TCP Dynamic Ports** dialog box contains **0**, indicating the [!INCLUDE[ssDE](../../includes/ssde-md.md)] is listening on dynamic ports, delete the 0.</span></span>  
  
4.  <span data-ttu-id="bd137-126">**IP**_n_ **속성** 영역 상자의 **TCP 포트** 상자에 이 IP 주소가 수신할 포트 번호를 입력하고 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bd137-126">In the **IP**_n_ **Properties** area box, in the **TCP Port** box, type the port number you want this IP address to listen on, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="bd137-127">콘솔 창에서 **SQL Server 서비스**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bd137-127">In the console pane, click **SQL Server Services**.</span></span>  
  
6.  <span data-ttu-id="bd137-128">세부 정보 창에서 **SQL Server(** \<instance name> **)** 를 마우스 오른쪽 단추로 클릭한 다음 **다시 시작**을 클릭하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]를 중지하고 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="bd137-128">In the details pane, right-click **SQL Server (**\<instance name>**)** and then click **Restart**, to stop and restart [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="bd137-129">특정 포트에서 수신하도록 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 를 구성한 후에 특정 포트를 통해 클라이언트 애플리케이션과 연결하는 세 가지 방법은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="bd137-129">After you have configured [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to listen on a specific port, there are three ways to connect to a specific port with a client application:</span></span>  
  
-   <span data-ttu-id="bd137-130">서버에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser 서비스를 실행하여 이름을 기준으로 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="bd137-130">Run the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser service on the server to connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)] instance by name.</span></span>  
  
-   <span data-ttu-id="bd137-131">클라이언트에서 별칭을 만들어 포트 번호를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="bd137-131">Create an alias on the client, specifying the port number.</span></span>  
  
-   <span data-ttu-id="bd137-132">클라이언트가 사용자 지정 연결 문자열을 사용하여 연결하도록 프로그래밍합니다.</span><span class="sxs-lookup"><span data-stu-id="bd137-132">Program the client to connect using a custom connection string.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd137-133">참고 항목</span><span class="sxs-lookup"><span data-stu-id="bd137-133">See Also</span></span>  
 [<span data-ttu-id="bd137-134">클라이언트에서 사용할 서버 별칭 만들기 또는 삭제&#40;SQL Server 구성 관리자&#41;</span><span class="sxs-lookup"><span data-stu-id="bd137-134">Create or Delete a Server Alias for Use by a Client &#40;SQL Server Configuration Manager&#41;</span></span>](create-or-delete-a-server-alias-for-use-by-a-client.md)  
  
  
