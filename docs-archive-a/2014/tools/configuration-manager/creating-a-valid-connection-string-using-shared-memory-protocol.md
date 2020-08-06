---
title: 공유 메모리 프로토콜을 사용하여 유효한 연결 문자열 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- connection strings [Database Engine], shared memory
- aliases [SQL Server], shared memory
ms.assetid: 5fff42e8-377f-4b40-b0c8-b02393f8a1af
author: stevestein
ms.author: sstein
ms.openlocfilehash: ca97332a09a33fcfc15a3dbb2599af27dbe0e1db
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727696"
---
# <a name="creating-a-valid-connection-string-using-shared-memory-protocol"></a><span data-ttu-id="d747e-102">공유 메모리 프로토콜을 사용하여 유효한 연결 문자열 만들기</span><span class="sxs-lookup"><span data-stu-id="d747e-102">Creating a Valid Connection String Using Shared Memory Protocol</span></span>
  <span data-ttu-id="d747e-103">클라이언트가 클라이언트와 동일한 컴퓨터에서 실행되는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에 연결할 때는 공유 메모리 프로토콜을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="d747e-103">Connections to [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] from a client running on the same computer use the shared memory protocol.</span></span> <span data-ttu-id="d747e-104">공유 메모리의 속성은 구성할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d747e-104">Shared memory has no configurable properties.</span></span> <span data-ttu-id="d747e-105">공유 메모리는 항상 가장 먼저 사용하려고 시도하며 **클라이언트 프로토콜 속성** 목록의 **사용할 수 있는 프로토콜** 목록 맨 위에서 다른 위치로 이동할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d747e-105">Shared memory is always tried first, and cannot be moved from the top position of the **Enabled Protocols** list in the **Client Protocols Properties** list.</span></span> <span data-ttu-id="d747e-106">공유 메모리 프로토콜을 사용하지 않으면 다른 프로토콜의 문제를 해결할 때 편리합니다.</span><span class="sxs-lookup"><span data-stu-id="d747e-106">The Shared Memory protocol can be disabled, which is useful when troubleshooting one of the other protocols.</span></span>  
  
 <span data-ttu-id="d747e-107">공유 메모리 프로토콜을 사용하여 별칭을 만들 수는 없지만 공유 메모리를 사용하는 경우 이름으로 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 에 연결하면 공유 메모리 연결이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="d747e-107">You cannot create an alias using the shared memory protocol, but if shared memory is enabled, then connecting to the [!INCLUDE[ssDE](../../includes/ssde-md.md)] by name, creates a shared memory connection.</span></span> <span data-ttu-id="d747e-108">공유 메모리 연결 문자열은 `lpc:<servername>[\instancename]`형식을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="d747e-108">A shared memory connection string uses the format `lpc:<servername>[\instancename]`.</span></span>  
  
## <a name="connecting-to-the-local-server"></a><span data-ttu-id="d747e-109">로컬 서버에 연결</span><span class="sxs-lookup"><span data-stu-id="d747e-109">Connecting to the Local Server</span></span>  
 <span data-ttu-id="d747e-110">클라이언트와 동일한 컴퓨터에서 실행되는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에 연결할 때는 서버 이름으로 **(local)** 을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d747e-110">When connecting to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] running on the same computer as the client, you can use **(local)** as the server name.</span></span> <span data-ttu-id="d747e-111">이 방법은 모호성을 유발하므로 권장되지 않지만 클라이언트가 어떤 컴퓨터에서 실행될지 알고 있는 경우에는 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d747e-111">This is not encouraged as it leads to ambiguity, however it can be useful when the client is known to be running on the intended computer.</span></span> <span data-ttu-id="d747e-112">예를 들어 영업 사원과 같이 네트워크에 연결되지 않은 모바일 사용자를 위해 애플리케이션을 만들 때 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가 랩톱 컴퓨터에서 실행되고 프로젝트 데이터를 저장하는 경우 **(local)** 에 연결하는 클라이언트는 항상 랩톱에서 실행되는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에 연결됩니다.</span><span class="sxs-lookup"><span data-stu-id="d747e-112">For instance, when creating an application for mobile disconnected users, such as a sales force, where [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will run on laptop computers and store project data, a client connecting to **(local)** would always connect to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] running on the laptop.</span></span> <span data-ttu-id="d747e-113">단어 **localhost** 또는 마침표( **.** )를 **(local)** 대신 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d747e-113">The word **localhost** or a period (**.**) can be used in place of **(local)**.</span></span>  
  
## <a name="verifying-your-connection-protocol"></a><span data-ttu-id="d747e-114">연결 프로토콜 확인</span><span class="sxs-lookup"><span data-stu-id="d747e-114">Verifying your Connection Protocol</span></span>  
 <span data-ttu-id="d747e-115">다음 쿼리는 현재 연결에 사용된 프로토콜을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="d747e-115">The following query will return the protocol used for the current connection.</span></span>  
  
```  
SELECT net_transport   
FROM sys.dm_exec_connections   
WHERE session_id = @@SPID;  
  
```  
  
## <a name="examples"></a><span data-ttu-id="d747e-116">예제:</span><span class="sxs-lookup"><span data-stu-id="d747e-116">Examples:</span></span>  
 <span data-ttu-id="d747e-117">다음 이름은 로컬 컴퓨터에 연결할 때 공유 메모리 프로토콜을 사용합니다(사용하는 경우).</span><span class="sxs-lookup"><span data-stu-id="d747e-117">The following names will connect to the local computer with the shared memory protocol if it is enabled:</span></span>  
  
 `<servername>`  
  
 `<servername>\<instancename>`  
  
 `(local)`  
  
 `localhost`  
  
 <span data-ttu-id="d747e-118">공유 메모리 연결에 대해서는 별칭을 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d747e-118">You cannot create an alias for a shared memory connection.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d747e-119">**서버** 상자에 IP 주소를 지정하면 TCP/IP 연결이 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="d747e-119">Specifying an IP Address in the **Server** box will result in a TCP/IP connection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d747e-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d747e-120">See Also</span></span>  
 <span data-ttu-id="d747e-121">[TCP/IP를 사용하여 유효한 연결 문자열 만들기](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-tcp-ip.md) </span><span class="sxs-lookup"><span data-stu-id="d747e-121">[Creating a Valid Connection String Using TCP IP](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-tcp-ip.md) </span></span>  
 <span data-ttu-id="d747e-122">[명명된 파이프를 사용하여 유효한 연결 문자열 만들기](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-named-pipes.md) </span><span class="sxs-lookup"><span data-stu-id="d747e-122">[Creating a Valid Connection String Using Named Pipes](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-named-pipes.md) </span></span>  
 [<span data-ttu-id="d747e-123">네트워크 프로토콜 선택</span><span class="sxs-lookup"><span data-stu-id="d747e-123">Choosing a Network Protocol</span></span>](../../../2014/tools/configuration-manager/choosing-a-network-protocol.md)  
  
  
