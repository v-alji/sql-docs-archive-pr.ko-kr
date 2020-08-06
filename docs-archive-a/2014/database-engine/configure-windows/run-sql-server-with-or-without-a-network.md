---
title: 네트워크 유무에 관계없이 SQL Server 실행 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- verifying Server service has been started
- net start [SQL Server]
- command prompt [SQL Server], connections
- SQL Server services, networks
- status information [SQL Server], Server service
- running SQL Server
- networking [SQL Server], SQL Server with or without
- services [SQL Server], networks
- starting Server service
- SQL Server, running
ms.assetid: 54eac961-5c7a-4481-982d-f93a64b5c2f4
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: a80e7e4d42f322bc42d0c67c57e3a1f9bddb87a0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651264"
---
# <a name="run-sql-server-with-or-without-a-network"></a><span data-ttu-id="7fd48-102">네트워크에서 또는 네트워크 없이 SQL Server 실행</span><span class="sxs-lookup"><span data-stu-id="7fd48-102">Run SQL Server With or Without a Network</span></span>
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="7fd48-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]는 네트워크에서 실행되거나 네트워크 없이 작동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7fd48-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] can run on a network, or it can function without a network.</span></span>  
  
## <a name="running-sql-server-on-a-network"></a><span data-ttu-id="7fd48-104">네트워크에서 SQL Server 실행</span><span class="sxs-lookup"><span data-stu-id="7fd48-104">Running SQL Server on a Network</span></span>  
 <span data-ttu-id="7fd48-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가 네트워크에서 통신하려면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 서비스가 실행 중이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7fd48-105">For [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to communicate over a network, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service must be running.</span></span> <span data-ttu-id="7fd48-106">기본적으로 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows는 기본 제공 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 서비스를 자동으로 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="7fd48-106">By default, [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows automatically starts the built-in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service.</span></span> <span data-ttu-id="7fd48-107">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 서비스의 시작 여부를 확인하려면 명령 프롬프트에서 다음을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="7fd48-107">To find out whether the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service has been started, at the command prompt, type the following:</span></span>  
  
 <span data-ttu-id="7fd48-108">**net start**</span><span class="sxs-lookup"><span data-stu-id="7fd48-108">**net start**</span></span>  
  
 <span data-ttu-id="7fd48-109">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에 연결된 서비스가 시작되었으면 **net start** 출력 시 다음 서비스가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="7fd48-109">If the services associated with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] have been started, the following services will appear in the **net start** output:</span></span>  
  
-   <span data-ttu-id="7fd48-110">Analysis Services (MSSQLSERVER)</span><span class="sxs-lookup"><span data-stu-id="7fd48-110">Analysis Services (MSSQLSERVER)</span></span>  
  
-   <span data-ttu-id="7fd48-111">SQL Server(MSSQLSERVER)</span><span class="sxs-lookup"><span data-stu-id="7fd48-111">SQL Server (MSSQLSERVER)</span></span>  
  
-   <span data-ttu-id="7fd48-112">SQL Server Agent(MSSQLSERVER)</span><span class="sxs-lookup"><span data-stu-id="7fd48-112">SQL Server Agent (MSSQLSERVER)</span></span>  
  
## <a name="running-sql-server-without-a-network"></a><span data-ttu-id="7fd48-113">네트워크 없이 SQL Server 실행</span><span class="sxs-lookup"><span data-stu-id="7fd48-113">Running SQL Server Without a Network</span></span>  
 <span data-ttu-id="7fd48-114">네트워크 없이 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 의 인스턴스를 실행하면 기본 제공 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 서비스를 시작하지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7fd48-114">When running an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] without a network, you do not need to start the built-in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service.</span></span> <span data-ttu-id="7fd48-115">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], SQL Server 구성 관리자, **net start** 및 **net stop** 명령은 네트워크 없이도 작동하므로 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스 시작 및 중지 절차는 네트워크나 독립 실행형 작업의 경우에 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="7fd48-115">Because [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], SQL Server Configuration Manager, and the **net start** and **net stop** commands are functional even without a network, the procedures for starting and stopping an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] are identical for a network or stand-alone operation.</span></span>  
  
 <span data-ttu-id="7fd48-116">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sqlcmd **와 같은 로컬 클라이언트에서 독립 실행형**인스턴스에 연결할 때는 네트워크를 사용하지 않고 로컬 파이프를 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 직접 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="7fd48-116">When connecting to an instance of a stand-alone [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] from a local client such as **sqlcmd**, you bypass the network and connect directly to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by using a local pipe.</span></span> <span data-ttu-id="7fd48-117">로컬 파이프와 네트워크 파이프 간의 차이는 네트워크의 사용 여부에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7fd48-117">The difference between a local pipe and a network pipe is whether you are using a network.</span></span> <span data-ttu-id="7fd48-118">달리 지정하지 않는 한, 표준 파이프( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .\pipe\sql\query)를 사용하여 로컬 파이프와 네트워크 파이프에서\\\\인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="7fd48-118">Both local and network pipes establish a connection with an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by using the standard pipe (\\\\.\pipe\sql\query), unless otherwise directed.</span></span>  
  
 <span data-ttu-id="7fd48-119">서버 이름을 지정하지 않고 로컬 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 연결하면 로컬 파이프를 사용하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7fd48-119">When you connect to an instance of a local [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] without specifying a server name, you are using a local pipe.</span></span> <span data-ttu-id="7fd48-120">로컬 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 연결하고 서버 이름을 정확하게 지정하면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]를 구성하여 다중 네트워크를 사용했을 경우 IPX/SPX와 같이 다른 네트워크 IPC 메커니즘이나 네트워크 파이프를 사용하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7fd48-120">When you connect to an instance of a local [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and specify a server name explicitly, you are using either a network pipe or another network interprocess communication (IPC) mechanism, such as Internetwork Packet Exchange/Sequenced Packet Exchange (IPX/SPX) (assuming you have configured [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to use multiple networks).</span></span> <span data-ttu-id="7fd48-121">독립 실행형 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]는 네트워크 파이프를 지원하지 않으므로 클라이언트에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 연결할 때는 불필요한 **/** _<Server_name>_ 인수를 제외해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7fd48-121">Because a stand-alone [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] does not support network pipes, you must omit the unnecessary **/**_<Server_name>_ argument when connecting to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] from a client.</span></span> <span data-ttu-id="7fd48-122">예를 들어 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] osql **에서 독립 실행형**인스턴스에 연결하려면 다음을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="7fd48-122">For example, to connect to a stand-alone instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] from **osql**, type:</span></span>  
  
 <span data-ttu-id="7fd48-123">**osql /Usa /P** _\<saPassword>_</span><span class="sxs-lookup"><span data-stu-id="7fd48-123">**osql /Usa /P** _\<saPassword>_</span></span>  
  
  
