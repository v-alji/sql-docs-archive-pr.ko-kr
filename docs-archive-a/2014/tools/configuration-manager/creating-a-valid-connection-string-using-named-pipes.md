---
title: 명명 된 파이프를 사용 하 여 유효한 연결 문자열 만들기 | Microsoft Docs
description: 명명 된 파이프 프로토콜을 사용 하 여 SQL Server 인스턴스에 연결할 때 유효한 연결 문자열을 만드는 방법에 대해 알아봅니다. 올바른 파이프 이름의 예를 봅니다.
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- connection strings [Database Engine], named pipes
- pipes [SQL Server]
- pipes [SQL Server], connecting to
- aliases [SQL Server], named pipes
- Named Pipes [SQL Server], connection strings
ms.assetid: 90930ff2-143b-4651-8ae3-297103600e4f
author: rothja
ms.author: jroth
ms.openlocfilehash: 10f3e1d01e9e5b7b1d1c0d1bb822bf233ceee636
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650340"
---
# <a name="creating-a-valid-connection-string-using-named-pipes"></a><span data-ttu-id="4ad83-104">명명된 파이프를 사용하여 유효한 연결 문자열 만들기</span><span class="sxs-lookup"><span data-stu-id="4ad83-104">Creating a Valid Connection String Using Named Pipes</span></span>
  <span data-ttu-id="4ad83-105">사용자가 변경 하지 않은 경우의 기본 인스턴스는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 명명 된 파이프 프로토콜에서 수신 하는 경우를 `\\.\pipe\sql\query` 파이프 이름으로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="4ad83-105">Unless changed by the user, when the default instance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] listens on the named pipes protocol, it uses `\\.\pipe\sql\query` as the pipe name.</span></span> <span data-ttu-id="4ad83-106">마침표는 컴퓨터가 로컬 컴퓨터임을 나타내고 `pipe` 는 연결이 명명된 파이프임을 나타내며 `sql\query` 는 파이프의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="4ad83-106">The period indicates that the computer is the local computer, `pipe` indicates that the connection is a named pipe, and `sql\query` is the name of the pipe.</span></span> <span data-ttu-id="4ad83-107">기본 파이프에 연결하려면 별칭의 파이프 이름으로 `\\<computer_name>\pipe\sql\query` 를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4ad83-107">To connect to the default pipe, the alias must have `\\<computer_name>\pipe\sql\query` as the pipe name.</span></span> <span data-ttu-id="4ad83-108">다른 파이프에서 수신하도록 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 를 구성한 경우 파이프 이름으로 해당 파이프를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4ad83-108">If [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] has been configured to listen on a different pipe, the pipe name must use that pipe.</span></span> <span data-ttu-id="4ad83-109">예를 들어, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가 `\\.\pipe\unit\app` 를 파이프로 사용하는 경우 별칭의 파이프 이름은 `\\<computer_name>\pipe\unit\app` 여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4ad83-109">For instance, if [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is using `\\.\pipe\unit\app` as the pipe, the alias must use `\\<computer_name>\pipe\unit\app` as the pipe name.</span></span>  
  
 <span data-ttu-id="4ad83-110">올바른 파이프 이름을 만들려면 다음을 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4ad83-110">To create a valid pipe name, you must:</span></span>  
  
-   <span data-ttu-id="4ad83-111">**별칭**을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4ad83-111">Specify an **Alias Name**.</span></span>  
  
-   <span data-ttu-id="4ad83-112">**명명된 파이프** 를 **프로토콜**로 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4ad83-112">Select **Named Pipes** as the **Protocol**.</span></span>  
  
-   <span data-ttu-id="4ad83-113">**파이프 이름**을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="4ad83-113">Enter the **Pipe Name**.</span></span> <span data-ttu-id="4ad83-114">또는 **파이프 이름** 을 비워 놓을 수 있습니다. 이 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 프로토콜 **과** 서버 **를 지정하면**구성 관리자에서 적절한 파이프 이름을 완성합니다.</span><span class="sxs-lookup"><span data-stu-id="4ad83-114">Alternatively, you can leave **Pipe Name** blank and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager will complete the appropriate pipe name after you specify the **Protocol** and **Server**</span></span>  
  
-   <span data-ttu-id="4ad83-115">**서버**를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4ad83-115">Specify a **Server**.</span></span> <span data-ttu-id="4ad83-116">명명된 인스턴스의 경우 서버 이름과 인스턴스 이름을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ad83-116">For a named instance you can provide a server name and instance name.</span></span>  
  
 <span data-ttu-id="4ad83-117">연결할 때 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 구성 요소는 지정 된 별칭 이름에 대 한 서버, 프로토콜 및 파이프 이름 값을 레지스트리에서 읽고 또는 형식으로 파이프 이름을 만듭니다 `np:\\<computer_name>\pipe\<pipename>` `np:\\<IPAddress>\pipe\<pipename>` . 명명 된 인스턴스의 경우 기본 파이프 이름은 `\\<computer_name>\pipe\MSSQL$<instance_name>\sql\query` 입니다.</span><span class="sxs-lookup"><span data-stu-id="4ad83-117">At the time of connection, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client component reads the server, protocol, and pipe name values from the registry for the specified alias name, and creates a pipe name in the format `np:\\<computer_name>\pipe\<pipename>` or `np:\\<IPAddress>\pipe\<pipename>`.For a named instance, the default pipe name is `\\<computer_name>\pipe\MSSQL$<instance_name>\sql\query`.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4ad83-118">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 방화벽에서는 포트 445가 기본적으로 닫힙니다.</span><span class="sxs-lookup"><span data-stu-id="4ad83-118">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Firewall closes port 445 by default.</span></span> <span data-ttu-id="4ad83-119">[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]는 포트 445에서 통신하므로 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]가 명명된 파이프를 사용하여 들어오는 클라이언트 연결을 수신하도록 구성된 경우 이 포트를 다시 열어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4ad83-119">Because [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] communicates over port 445, you must reopen the port if [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is configured to listen for incoming client connections using named pipes.</span></span> <span data-ttu-id="4ad83-120">방화벽 구성에 대한 자세한 내용은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 온라인 설명서의 "방법: SQL Server 액세스를 허용하도록 방화벽 구성"을 참조하거나 해당 방화벽 설명서를 검토하세요.</span><span class="sxs-lookup"><span data-stu-id="4ad83-120">For information on configuring a firewall, see "How to: Configure a Firewall for SQL Server Access" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online or review your firewall documentation.</span></span>  
  
## <a name="connecting-to-the-local-server"></a><span data-ttu-id="4ad83-121">로컬 서버에 연결</span><span class="sxs-lookup"><span data-stu-id="4ad83-121">Connecting to the Local Server</span></span>  
 <span data-ttu-id="4ad83-122">클라이언트와 동일한 컴퓨터에서 실행되는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에 연결할 때는 서버 이름으로 `(local)`을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ad83-122">When connecting to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] running on the same computer as the client, you can use `(local)`as the server name.</span></span> <span data-ttu-id="4ad83-123">`(local)` 을 사용하면 모호해질 수 있으므로 권장되지는 않지만 클라이언트가 어떤 컴퓨터에서 실행될지 알고 있는 경우에는 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ad83-123">Using `(local)` is not encouraged because it leads to ambiguity; however it can be useful when the client is known to be running on the intended computer.</span></span> <span data-ttu-id="4ad83-124">예를 들어 영업 사원과 같이 네트워크에 연결되지 않은 모바일 사용자를 위해 애플리케이션을 만들 때 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가 랩톱 컴퓨터에서 실행되고 프로젝트 데이터를 저장하는 경우 (local)에 연결하는 클라이언트는 항상 랩톱에서 실행되는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에 연결됩니다.</span><span class="sxs-lookup"><span data-stu-id="4ad83-124">For instance, when creating an application for mobile disconnected users, such as a sales force, where [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will run on laptop computers and store project data, a client connecting to (local) would always connect to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] running on the laptop.</span></span> <span data-ttu-id="4ad83-125">`localhost`라는 단어나 마침표(.)를 `(local)` 대신 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ad83-125">The word `localhost` or a period (.) can be used in place of `(local)`.</span></span>  
  
## <a name="verifying-your-connection-protocol"></a><span data-ttu-id="4ad83-126">연결 프로토콜 확인</span><span class="sxs-lookup"><span data-stu-id="4ad83-126">Verifying Your Connection Protocol</span></span>  
 <span data-ttu-id="4ad83-127">다음 쿼리는 현재 연결에 사용된 프로토콜을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="4ad83-127">The following query will return the protocol used for the current connection.</span></span>  
  
```  
SELECT net_transport   
FROM sys.dm_exec_connections   
WHERE session_id = @@SPID;  
  
```  
  
## <a name="examples"></a><span data-ttu-id="4ad83-128">예</span><span class="sxs-lookup"><span data-stu-id="4ad83-128">Examples</span></span>  
 <span data-ttu-id="4ad83-129">서버 이름으로 기본 파이프에 연결</span><span class="sxs-lookup"><span data-stu-id="4ad83-129">Connecting by server name to the default pipe:</span></span>  
  
```  
Alias Name         <serveralias>  
Pipe Name          <blank>  
Protocol           Named Pipes  
Server             <servername>  
  
```  
  
 <span data-ttu-id="4ad83-130">IP 주소로 기본 파이프에 연결</span><span class="sxs-lookup"><span data-stu-id="4ad83-130">Connecting by IP Address to the default pipe:</span></span>  
  
```  
Alias Name         <serveralias>  
Pipe Name          <leave blank>  
Protocol           Named Pipes  
Server             <IPAddress>  
  
```  
  
 <span data-ttu-id="4ad83-131">서버 이름으로 기본이 아닌 파이프에 연결</span><span class="sxs-lookup"><span data-stu-id="4ad83-131">Connecting by server name to a non-default pipe:</span></span>  
  
```  
Alias Name         <serveralias>  
Pipe Name          \\<servername>\pipe\unit\app  
Protocol           Named Pipes  
Server             <servername>  
  
```  
  
 <span data-ttu-id="4ad83-132">서버 이름으로 명명된 인스턴스에 연결</span><span class="sxs-lookup"><span data-stu-id="4ad83-132">Connecting by server name to a named instance:</span></span>  
  
```  
Alias Name         <serveralias>  
Pipe Name          \\<servername>\pipe\MSSQL$<instancename>\SQL\query  
Protocol           Named Pipes  
Server             <servername>  
  
```  
  
 <span data-ttu-id="4ad83-133">`localhost`를 사용하여 로컬 컴퓨터에 연결</span><span class="sxs-lookup"><span data-stu-id="4ad83-133">Connecting to the local computer using `localhost`:</span></span>  
  
```  
Alias Name         <serveralias>  
Pipe Name          <blank>  
Protocol           Named Pipes  
Server             localhost  
  
```  
  
 <span data-ttu-id="4ad83-134">마침표를 사용하여 로컬 컴퓨터에 연결</span><span class="sxs-lookup"><span data-stu-id="4ad83-134">Connecting to the local computer using a period:</span></span>  
  
```  
Alias Name         <serveralias>  
Pipe Name          <left blank>  
Protocol           Named Pipes  
Server             .  
  
```  
  
> [!NOTE]  
>  <span data-ttu-id="4ad83-135">네트워크 프로토콜을 **sqlcmd** 매개 변수로 지정하려면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 온라인 설명서의 "방법: sqlcmd.exe를 사용하여 데이터베이스 엔진에 연결"을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="4ad83-135">To specify the network protocol as a **sqlcmd** parameter, see "How to: Connect to the Database Engine Using sqlcmd.exe" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ad83-136">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4ad83-136">See Also</span></span>  
 <span data-ttu-id="4ad83-137">[공유 메모리 프로토콜을 사용 하 여 유효한 연결 문자열 만들기](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-shared-memory-protocol.md) </span><span class="sxs-lookup"><span data-stu-id="4ad83-137">[Creating a Valid Connection String Using Shared Memory Protocol](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-shared-memory-protocol.md) </span></span>  
 <span data-ttu-id="4ad83-138">[TCP IP를 사용 하 여 유효한 연결 문자열 만들기](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-tcp-ip.md) </span><span class="sxs-lookup"><span data-stu-id="4ad83-138">[Creating a Valid Connection String Using TCP IP](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-tcp-ip.md) </span></span>  
 [<span data-ttu-id="4ad83-139">네트워크 프로토콜 선택</span><span class="sxs-lookup"><span data-stu-id="4ad83-139">Choosing a Network Protocol</span></span>](../../../2014/tools/configuration-manager/choosing-a-network-protocol.md)  
  
  
