---
title: sqlcmd를 사용하여 데이터베이스 엔진에 연결
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- sqlcmd utility, Database Engine connections
- Named Pipes [SQL Server], sqlcmd utility
- TCP/IP [SQL Server], client protocols
- network protocols [SQL Server], sqlcmd utility
- protocols [SQL Server], sqlcmd utility
- VIA
- client protocols [SQL Server]
ms.assetid: 74b0fb71-7f8e-4171-9431-d07528532524
author: rothja
ms.author: jroth
ms.openlocfilehash: 3b409683b651e3e6508baced5eb3bc9fcc631e2c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647587"
---
# <a name="connect-to-the-database-engine-with-sqlcmd"></a><span data-ttu-id="ca617-102">sqlcmd를 사용하여 데이터베이스 엔진에 연결</span><span class="sxs-lookup"><span data-stu-id="ca617-102">Connect to the Database Engine With sqlcmd</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="ca617-103">는 TCP/IP 네트워크 프로토콜(기본값) 및 명명된 파이프 프로토콜을 통한 클라이언트 통신을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="ca617-103">supports client communication with the TCP/IP network protocol (the default), and the named pipes protocol.</span></span> <span data-ttu-id="ca617-104">클라이언트가 동일 컴퓨터의 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 인스턴스에 연결하고 있는 경우 공유 메모리 프로토콜도 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ca617-104">The shared memory protocol is also available if the client is connecting to an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] on the same computer.</span></span> <span data-ttu-id="ca617-105">일반적으로 프로토콜을 선택하는 방법에는 3가지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ca617-105">There are three common methods of selecting the protocol.</span></span> <span data-ttu-id="ca617-106">**sqlcmd** 유틸리티에서 사용하는 프로토콜은 다음과 같은 순서로 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="ca617-106">The protocol used by the **sqlcmd** utility is determined in the following order:</span></span>  
  
-   <span data-ttu-id="ca617-107">**sqlcmd** 는 다음 설명과 같이 연결 문자열의 일부로 지정된 프로토콜을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ca617-107">**sqlcmd** uses the protocol specified as part of the connection string as described below.</span></span>  
  
-   <span data-ttu-id="ca617-108">프로토콜을 연결 문자열의 일부로 지정하지 않으면 **sqlcmd** 는 연결하고 있는 별칭의 일부로 정의된 프로토콜을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ca617-108">If no protocol is specified as part the connection string, **sqlcmd** will use the protocol defined as part of the alias that it is connecting to.</span></span> <span data-ttu-id="ca617-109">별칭을 만들어 특정 네트워크 프로토콜을 사용하도록 **sqlcmd**를 구성하려면 [클라이언트에서 사용할 서버 별칭 만들기 또는 삭제&#40;SQL Server 구성 관리자&#41;](../../database-engine/configure-windows/create-or-delete-a-server-alias-for-use-by-a-client.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ca617-109">To configure **sqlcmd** to use a specific network protocol by creating an alias, see [Create or Delete a Server Alias for Use by a Client &#40;SQL Server Configuration Manager&#41;](../../database-engine/configure-windows/create-or-delete-a-server-alias-for-use-by-a-client.md).</span></span>  
  
-   <span data-ttu-id="ca617-110">기타 다른 방법으로 프로토콜을 지정하지 않으면 **sqlcmd** 는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구성 관리자에서 프로토콜 순서에 따라 결정되는 네트워크 프로토콜을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ca617-110">If the protocol is not specified in some other way, **sqlcmd** will use the network protocol determined by the protocol order in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager.</span></span>  
  
 <span data-ttu-id="ca617-111">다음 예에서는 포트 1433에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 의 기본 인스턴스에 연결하고 포트 1691에서 수신하는 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 의 명명된 인스턴스에 연결하는 여러 가지 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ca617-111">The following examples show various ways of connecting to the default instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)] on port 1433, and named instances of [!INCLUDE[ssDE](../../includes/ssde-md.md)] presumed to be listening on port 1691.</span></span> <span data-ttu-id="ca617-112">일부 예에서는 루프백 어댑터의 IP 주소(127.0.0.1)를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ca617-112">Some of these examples use the IP address of the loopback adapter (127.0.0.1).</span></span> <span data-ttu-id="ca617-113">컴퓨터의 네트워크 인터페이스 카드의 IP 주소를 사용하여 테스트합니다.</span><span class="sxs-lookup"><span data-stu-id="ca617-113">Test using the IP address of your computer network interface card.</span></span>  
  
 <span data-ttu-id="ca617-114">인스턴스 이름을 지정하여 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="ca617-114">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)] by specifying the instance name:</span></span>  
  
```  
sqlcmd -S ComputerA  
sqlcmd -S ComputerA\instanceB  
```  
  
 <span data-ttu-id="ca617-115">IP 주소를 지정하여 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="ca617-115">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)] by specifying the IP address:</span></span>  
  
```  
sqlcmd -S 127.0.0.1  
sqlcmd -S 127.0.0.1\instanceB  
```  
  
 <span data-ttu-id="ca617-116">TCP\IP 포트 번호를 지정하여 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="ca617-116">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)] by specifying the TCP\IP port number:</span></span>  
  
```  
sqlcmd -S ComputerA,1433  
sqlcmd -S ComputerA,1691  
sqlcmd -S 127.0.0.1,1433  
sqlcmd -S 127.0.0.1,1691  
```  
  
### <a name="to-connect-using-tcpip"></a><span data-ttu-id="ca617-117">TCP/IP를 사용하여 연결하려면</span><span class="sxs-lookup"><span data-stu-id="ca617-117">To connect using TCP/IP</span></span>  
  
-   <span data-ttu-id="ca617-118">다음 일반 구문을 사용하여 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="ca617-118">Connect using the following general syntax:</span></span>  
  
    ```  
    sqlcmd -S tcp:<computer name>,<port number>  
    ```  
  
-   <span data-ttu-id="ca617-119">기본 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="ca617-119">Connect to the default instance:</span></span>  
  
    ```  
    sqlcmd -S tcp:ComputerA,1433  
    sqlcmd -S tcp:127.0.0.1,1433  
    ```  
  
-   <span data-ttu-id="ca617-120">명명된 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="ca617-120">Connect to a named instance:</span></span>  
  
    ```  
    sqlcmd -S tcp:ComputerA,1691  
    sqlcmd -S tcp:127.0.0.1,1691  
    ```  
  
### <a name="to-connect-using-named-pipes"></a><span data-ttu-id="ca617-121">명명된 파이프를 사용하여 연결하려면</span><span class="sxs-lookup"><span data-stu-id="ca617-121">To connect using named pipes</span></span>  
  
-   <span data-ttu-id="ca617-122">다음 일반적인 구문 중 하나를 사용하여 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="ca617-122">Connect using one of the following general syntax:</span></span>  
  
    ```  
    sqlcmd -S np:\\<computer name>\<pipe name>  
    ```  
  
-   <span data-ttu-id="ca617-123">기본 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="ca617-123">Connect to the default instance:</span></span>  
  
    ```  
    sqlcmd -S np:\\ComputerA\pipe\sql\query  
    sqlcmd -S np:\\127.0.0.1\pipe\sql\query  
    ```  
  
-   <span data-ttu-id="ca617-124">명명된 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="ca617-124">Connect to a named instance instance:</span></span>  
  
    ```  
    sqlcmd -S np:\\ComputerA\pipe\MSSQL$<instancename>\sql\query  
    sqlcmd -S np:\\127.0.0.1\pipe\MSSQL$<instancename>\sql\query  
    ```  
  
### <a name="to-connect-using-shared-memory-a-local-procedure-call-from-a-client-on-the-server"></a><span data-ttu-id="ca617-125">서버에 있는 클라이언트에서 공유 메모리(로컬 프로시저 호출)를 사용하여 연결하려면</span><span class="sxs-lookup"><span data-stu-id="ca617-125">To connect using shared memory (a local procedure call) from a client on the server</span></span>  
  
-   <span data-ttu-id="ca617-126">다음 일반적인 구문 중 하나를 사용하여 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="ca617-126">Connect using one of the following general syntax:</span></span>  
  
    ```  
    sqlcmd -S lpc:<computer name>  
    ```  
  
-   <span data-ttu-id="ca617-127">기본 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="ca617-127">Connect to the default instance:</span></span>  
  
    ```  
    sqlcmd -S lpc:ComputerA  
    ```  
  
-   <span data-ttu-id="ca617-128">명명된 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="ca617-128">Connect to a named instance:</span></span>  
  
    ```  
    sqlcmd -S lpc:ComputerA\<instancename>  
    ```  
  
  
