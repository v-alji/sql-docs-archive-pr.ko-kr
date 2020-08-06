---
title: TCP/IP를 사용하여 유효한 연결 문자열 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- connection strings [Database Engine]
- ports [SQL Server], connecting to
- TCP/IP [SQL Server], connection strings
- connection strings [Database Engine], TCP/IP
- aliases [SQL Server], TCP/IP
ms.assetid: ee5dbc2c-1fc6-42bd-bdf5-efa792557934
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5f761fa86ec4ed09c13bf4807489754c10b979ea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650338"
---
# <a name="creating-a-valid-connection-string-using-tcp-ip"></a><span data-ttu-id="91638-102">TCP/IP를 사용하여 유효한 연결 문자열 만들기</span><span class="sxs-lookup"><span data-stu-id="91638-102">Creating a Valid Connection String Using TCP IP</span></span>
  <span data-ttu-id="91638-103">TCP/IP를 사용하여 유효한 연결 문자열을 만들려면 다음을 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="91638-103">To create a valid connection string using TCP/IP, you must:</span></span>  
  
-   <span data-ttu-id="91638-104">**별칭**을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="91638-104">Specify an **Alias Name**.</span></span>  
  
-   <span data-ttu-id="91638-105">**서버**에 **PING** 유틸리티를 사용하여 연결할 수 있는 서버 이름을 입력하거나 **PING** 유틸리티를 사용하여 연결할 수 있는 IP 주소를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="91638-105">For the **Server**, enter either a server name to which you can connect using the **PING** utility, or an IP address to which you can connect using the **PING** utility.</span></span> <span data-ttu-id="91638-106">명명된 인스턴트에 인스턴트 이름을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="91638-106">For a named instance append the instance name.</span></span>  
  
-   <span data-ttu-id="91638-107">**프로토콜** 로 **TCP/IP**를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="91638-107">Specify **TCP/IP** for the **Protocol**.</span></span>  
  
-   <span data-ttu-id="91638-108">필요에 따라 **포트 번호**에 포트 번호를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="91638-108">Optionally, enter a port number for the **Port No**.</span></span> <span data-ttu-id="91638-109">기본값은 1433으로, 서버에 있는 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 기본 인스턴스의 포트 번호입니다.</span><span class="sxs-lookup"><span data-stu-id="91638-109">The default is 1433, which is the port number of the default instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] on a server.</span></span> <span data-ttu-id="91638-110">포트 1433에서 수신하지 않는 기본 인스턴스나 명명된 인스턴스에 연결하려면 해당 포트 번호를 제공하거나 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser 서비스를 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="91638-110">To connect to a named instance or a default instance that is not listening on port 1433, you must provide the port number, or start the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser service.</span></span> <span data-ttu-id="91638-111">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser 서비스를 구성하는 방법은 [SQL Server Browser 서비스](../../../2014/tools/configuration-manager/sql-server-browser-service.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="91638-111">For information on configuring the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser service, see [SQL Server Browser Service](../../../2014/tools/configuration-manager/sql-server-browser-service.md).</span></span>  
  
 <span data-ttu-id="91638-112">연결할 때 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 구성 요소는 지정한 별칭에 대한 서버, 프로토콜 및 포트 값을 레지스트리에서 읽어온 후 `tcp:<servername>[\<instancename>],<port>` 또는 `tcp:<IPAddress>[\<instancename>],<port>`형식으로 연결 문자열을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="91638-112">At the time of connection, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client component reads the server, protocol, and port values from the registry for the specified alias name, and creates a connection string in the format `tcp:<servername>[\<instancename>],<port>` or `tcp:<IPAddress>[\<instancename>],<port>`.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="91638-113">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 방화벽에서는 포트 1433이 기본적으로 닫힙니다.</span><span class="sxs-lookup"><span data-stu-id="91638-113">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Firewall closes port 1433 by default.</span></span> <span data-ttu-id="91638-114">[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 는 포트 1433에서 통신하므로 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가 TCP/IP를 사용하여 들어오는 클라이언트 연결을 수신하도록 구성된 경우 이 포트를 다시 열어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="91638-114">Because [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] communicates over port 1433, you must reopen the port if [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is configured to listen for incoming client connections using TCP/IP.</span></span> <span data-ttu-id="91638-115">방화벽 구성에 대한 자세한 내용은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 온라인 설명서의 "방법: SQL Server 액세스를 허용하도록 방화벽 구성"을 참조하거나 해당 방화벽 설명서를 검토하세요.</span><span class="sxs-lookup"><span data-stu-id="91638-115">For information on configuring a firewall, see "How to: Configure a Firewall for SQL Server Access" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online or review your firewall documentation.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="91638-116">및 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client는 인터넷 프로토콜 버전 4(IPv4)와 인터넷 프로토콜 버전 6(IPv6)을 둘 다 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="91638-116">and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client fully support both Internet Protocol version 4 (IPv4) and Internet Protocol version 6 (IPv6).</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="91638-117">구성 관리자는 IP 주소로 IPv4 및 IPv6 형식을 둘 다 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="91638-117">Configuration Manager accepts both IPv4 and IPv6 formats for IP addresses.</span></span> <span data-ttu-id="91638-118">IPv6에 대한 자세한 내용은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 온라인 설명서의 "IPv6을 사용하여 연결"을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="91638-118">For information on IPv6, see "Connecting Using IPv6" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="connecting-to-the-local-server"></a><span data-ttu-id="91638-119">로컬 서버에 연결</span><span class="sxs-lookup"><span data-stu-id="91638-119">Connecting to the Local Server</span></span>  
 <span data-ttu-id="91638-120">클라이언트와 동일한 컴퓨터에서 실행되는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에 연결할 때는 서버 이름으로 `(local)` 을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="91638-120">When connecting to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] running on the same computer as the client, you can use `(local)` as the server name.</span></span> <span data-ttu-id="91638-121">이 방법은 모호성을 유발하므로 권장되지 않지만 클라이언트가 어떤 컴퓨터에서 실행될지 알고 있는 경우에는 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="91638-121">This is not encouraged as it leads to ambiguity, however it can be useful when the client is known to be running on the intended computer.</span></span> <span data-ttu-id="91638-122">예를 들어 영업 사원과 같이 네트워크에 연결되지 않은 모바일 사용자를 위해 애플리케이션을 만들 때 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가 랩톱 컴퓨터에서 실행되고 프로젝트 데이터를 저장하는 경우 `(local)` 에 연결하는 클라이언트는 항상 랩톱에서 실행되는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에 연결됩니다.</span><span class="sxs-lookup"><span data-stu-id="91638-122">For instance, when creating an application for mobile disconnected users, such as a sales force, where [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will run on laptop computers and store project data, a client connecting to `(local)` would always connect to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] running on the laptop.</span></span> <span data-ttu-id="91638-123">`localhost` 라는 단어나 마침표( **.** )를 `(local)`대신 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="91638-123">The word `localhost` or a period (**.**) can be used in place of `(local)`.</span></span>  
  
## <a name="verifying-your-connection-protocol"></a><span data-ttu-id="91638-124">연결 프로토콜 확인</span><span class="sxs-lookup"><span data-stu-id="91638-124">Verifying Your Connection Protocol</span></span>  
 <span data-ttu-id="91638-125">다음 쿼리는 현재 연결에 사용된 프로토콜을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="91638-125">The following query returns the protocol used for the current connection.</span></span>  
  
```  
SELECT net_transport   
FROM sys.dm_exec_connections   
WHERE session_id = @@SPID;  
  
```  
  
## <a name="examples"></a><span data-ttu-id="91638-126">예</span><span class="sxs-lookup"><span data-stu-id="91638-126">Examples</span></span>  
 <span data-ttu-id="91638-127">서버 이름으로 연결</span><span class="sxs-lookup"><span data-stu-id="91638-127">Connecting by server name:</span></span>  
  
```  
Alias Name         <serveralias>  
Port No            <blank>  
Protocol           TCP/IP  
Server             <servername>  
  
```  
  
 <span data-ttu-id="91638-128">서버 이름으로 명명된 인스턴스에 연결</span><span class="sxs-lookup"><span data-stu-id="91638-128">Connecting by server name to a named instance:</span></span>  
  
```  
Alias Name         <serveralias>  
Port No            <blank>  
Protocol           TCP/IP  
Server             <servername>\<instancename>  
  
```  
  
 <span data-ttu-id="91638-129">서버 이름으로 지정한 포트에 연결</span><span class="sxs-lookup"><span data-stu-id="91638-129">Connecting by server name to a specified port:</span></span>  
  
```  
Alias Name         <serveralias>  
Port No            <port>  
Protocol           TCP/IP  
Server             <servername>  
  
```  
  
 <span data-ttu-id="91638-130">IP 주소로 연결</span><span class="sxs-lookup"><span data-stu-id="91638-130">Connecting by IP address:</span></span>  
  
```  
Alias Name         <serveralias>  
Port No            <blank>  
Protocol           TCP/IP  
Server             <IPAddress>  
  
```  
  
 <span data-ttu-id="91638-131">IP 주소로 명명된 인스턴스에 연결</span><span class="sxs-lookup"><span data-stu-id="91638-131">Connecting by IP address to a named instance:</span></span>  
  
```  
Alias Name         <serveralias>  
Port No            <blank>  
Protocol           TCP/IP  
Server             <IPAddress>\<instancename>  
  
```  
  
 <span data-ttu-id="91638-132">IP 주소로 지정한 포트에 연결</span><span class="sxs-lookup"><span data-stu-id="91638-132">Connecting by IP address to a specified port:</span></span>  
  
```  
Alias Name         <serveralias>  
Port No            <port number>  
Protocol           TCP/IP  
Server             <IPAddress>  
  
```  
  
 <span data-ttu-id="91638-133">`(local)`를 사용하여 로컬 컴퓨터에 연결</span><span class="sxs-lookup"><span data-stu-id="91638-133">Connecting to the local computer using `(local)`:</span></span>  
  
```  
Alias Name         <serveralias>  
Port No            <blank>  
Protocol           TCP/IP  
Server             (local)  
  
```  
  
 <span data-ttu-id="91638-134">`localhost`를 사용하여 로컬 컴퓨터에 연결</span><span class="sxs-lookup"><span data-stu-id="91638-134">Connecting to the local computer using `localhost`:</span></span>  
  
```  
Alias Name         <serveralias>  
Port No            <blank>  
Protocol           TCP/IP  
Server             localhost  
  
```  
  
 <span data-ttu-id="91638-135">로컬 컴퓨터 `localhost`의 명명된 인스턴스에 연결</span><span class="sxs-lookup"><span data-stu-id="91638-135">Connecting to a named instance on the local computer `localhost`:</span></span>  
  
```  
Alias Name         <serveralias>  
Port No            <blank>  
Protocol           TCP/IP  
Server             localhost\<instancename>  
  
```  
  
 <span data-ttu-id="91638-136">마침표를 사용하여 로컬 컴퓨터에 연결</span><span class="sxs-lookup"><span data-stu-id="91638-136">Connecting to the local computer using a period:</span></span>  
  
```  
Alias Name         <serveralias>  
Port No            <blank>  
Protocol           TCP/IP  
Server             .  
  
```  
  
 <span data-ttu-id="91638-137">마침표를 사용하여 로컬 컴퓨터의 명명된 인스턴스에 연결</span><span class="sxs-lookup"><span data-stu-id="91638-137">Connecting to a named instance on the local computer using a period:</span></span>  
  
```  
Alias Name         <serveralias>  
Port No            <blank>  
Protocol           TCP/IP  
Server             .\<instancename>  
  
```  
  
> [!NOTE]  
>  <span data-ttu-id="91638-138">**sqlcmd** 매개 변수로 네트워크 프로토콜을 지정하는 방법은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 온라인 설명서의 "방법: sqlcmd.exe를 사용하여 데이터베이스 엔진에 연결"을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="91638-138">For information on specifying the network protocol as a **sqlcmd** parameter, see "How to: Connect to the Database Engine Using sqlcmd.exe" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91638-139">참고 항목</span><span class="sxs-lookup"><span data-stu-id="91638-139">See Also</span></span>  
 <span data-ttu-id="91638-140">[공유 메모리 프로토콜을 사용하여 유효한 연결 문자열 만들기](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-shared-memory-protocol.md) </span><span class="sxs-lookup"><span data-stu-id="91638-140">[Creating a Valid Connection String Using Shared Memory Protocol](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-shared-memory-protocol.md) </span></span>  
 <span data-ttu-id="91638-141">[명명된 파이프를 사용하여 유효한 연결 문자열 만들기](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-named-pipes.md) </span><span class="sxs-lookup"><span data-stu-id="91638-141">[Creating a Valid Connection String Using Named Pipes](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-named-pipes.md) </span></span>  
 [<span data-ttu-id="91638-142">네트워크 프로토콜 선택</span><span class="sxs-lookup"><span data-stu-id="91638-142">Choosing a Network Protocol</span></span>](../../../2014/tools/configuration-manager/choosing-a-network-protocol.md)  
  
  
