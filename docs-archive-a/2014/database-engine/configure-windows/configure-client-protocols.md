---
title: 클라이언트 프로토콜 구성 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- default protocols
- network protocols [SQL Server], client configuration
- TCP/IP [SQL Server], client protocols
- disabling client protocols
- ordering protocols [SQL Server]
- protocols [SQL Server], order for client computers
- configure client protocols
- client protocols [SQL Server]
- protocols [SQL Server], client configuration
ms.assetid: 3dfa2702-ba65-43b4-a777-6727846e133a
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 2eb223815c3e3af50813e02d3ded60573c327155
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661362"
---
# <a name="configure-client-protocols"></a><span data-ttu-id="1702c-102">클라이언트 프로토콜 구성</span><span class="sxs-lookup"><span data-stu-id="1702c-102">Configure Client Protocols</span></span>
  <span data-ttu-id="1702c-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 구성 관리자를 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 클라이언트 애플리케이션이 사용하는 클라이언트 프로토콜을 구성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="1702c-103">This topic describes how to configure client protocols used by client applications in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager.</span></span> <span data-ttu-id="1702c-104">Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]는 TCP/IP 네트워크 프로토콜 및 명명된 파이프 프로토콜을 통한 클라이언트 통신을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="1702c-104">Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] supports client communication with the TCP/IP network protocol and the named pipes protocol.</span></span> <span data-ttu-id="1702c-105">클라이언트가 동일 컴퓨터의 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 인스턴스에 연결하고 있는 경우 공유 메모리 프로토콜도 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1702c-105">The shared memory protocol is also available if the client is connecting to an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] on the same computer.</span></span> <span data-ttu-id="1702c-106">일반적으로 프로토콜을 선택하는 방법에는 3가지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1702c-106">There are three common methods of selecting the protocol.</span></span>  
  
-   <span data-ttu-id="1702c-107">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구성 관리자에 프로토콜 순서를 설정하여 모든 클라이언트 애플리케이션이 동일한 네트워크 프로토콜을 사용하도록 구성하십시오.</span><span class="sxs-lookup"><span data-stu-id="1702c-107">Configure all client applications to use the same network protocol by setting the protocol order in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager.</span></span>  
  
-   <span data-ttu-id="1702c-108">별칭을 만들어 단일 클라이언트 애플리케이션이 다른 네트워크 프로토콜을 사용하도록 구성하십시오.</span><span class="sxs-lookup"><span data-stu-id="1702c-108">Configure a single client application to use a different network protocol by creating an alias.</span></span> <span data-ttu-id="1702c-109">자세한 내용은 [클라이언트에서 사용할 서버 별칭 만들기 또는 삭제&#40;SQL Server 구성 관리자&#41;](create-or-delete-a-server-alias-for-use-by-a-client.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1702c-109">For more information, see [Create or Delete a Server Alias for Use by a Client &#40;SQL Server Configuration Manager&#41;](create-or-delete-a-server-alias-for-use-by-a-client.md).</span></span>  
  
-   <span data-ttu-id="1702c-110">sqlcmd.exe 같은 일부 클라이언트 애플리케이션은 연결 문자열의 일부로 프로토콜을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1702c-110">Some client applications, such as sqlcmd.exe, can specify the protocol as part of the connection string.</span></span> <span data-ttu-id="1702c-111">자세한 내용은 [sqlcmd를 사용하여 데이터베이스 엔진에 연결](../../relational-databases/scripting/sqlcmd-connect-to-the-database-engine.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1702c-111">For more information, see [Connect to the Database Engine With sqlcmd](../../relational-databases/scripting/sqlcmd-connect-to-the-database-engine.md).</span></span>  
  
##  <a name="using-sql-server-configuration-manager"></a><a name="SSMSProcedure"></a> <span data-ttu-id="1702c-112">SQL Server 구성 관리자 사용</span><span class="sxs-lookup"><span data-stu-id="1702c-112">Using SQL Server Configuration Manager</span></span>  
  
###  <a name="to-enable-or-disable-a-client-protocol"></a><a name="EnableDisable"></a> <span data-ttu-id="1702c-113">클라이언트 프로토콜을 사용하거나 사용하지 않으려면</span><span class="sxs-lookup"><span data-stu-id="1702c-113">To enable or disable a client protocol</span></span>  
  
1.  <span data-ttu-id="1702c-114">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구성 관리자에서 **SQL Server Native Client 구성**을 확장하고 **클라이언트 프로토콜**을 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1702c-114">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, expand **SQL Server Native Client Configuration**, right-click **Client Protocols**, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="1702c-115">**사용할 수 없는 프로토콜** 상자에서 프로토콜을 클릭한 다음 **사용**을 클릭하여 프로토콜을 사용할 수 있게 합니다.</span><span class="sxs-lookup"><span data-stu-id="1702c-115">Click a protocol in the **Disabled Protocols** box, and then click **Enable**, to enable a protocol.</span></span>  
  
3.  <span data-ttu-id="1702c-116">**사용할 수 있는 프로토콜** 상자에서 프로토콜을 클릭한 다음 **사용 안 함**을 클릭하여 프로토콜을 사용할 수 없게 합니다.</span><span class="sxs-lookup"><span data-stu-id="1702c-116">Click a protocol in the **Enabled Protocols** box, and then click **Disable**, to disable a protocol.</span></span>  
  
###  <a name="to-change-the-default-protocol-or-the-protocol-order-for-client-computers"></a><a name="ChangeDefault"></a> <span data-ttu-id="1702c-117">클라이언트 컴퓨터의 기본 프로토콜이나 프로토콜 순서를 변경하려면</span><span class="sxs-lookup"><span data-stu-id="1702c-117">To change the default protocol or the protocol order for client computers</span></span>  
  
1.  <span data-ttu-id="1702c-118">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구성 관리자에서 **SQL Server Native Client 구성**을 확장하고 **클라이언트 프로토콜**을 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1702c-118">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, expand **SQL Server Native Client Configuration**, right-click **Client Protocols**, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="1702c-119">**사용할 수 있는 프로토콜** 상자에서 **위로 이동** 이나 **아래로 이동**을 클릭하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에 연결을 시도할 때 사용되는 프로토콜 순서를 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="1702c-119">In the **Enabled Protocols** box, click **Move Up** or **Move Down**, to change the order in which protocols are tried, when attempting to connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="1702c-120">**사용할 수 있는 프로토콜** 상자의 가장 위에 있는 프로토콜은 기본 프로토콜입니다.</span><span class="sxs-lookup"><span data-stu-id="1702c-120">The top protocol in the **Enabled Protocols** box is the default protocol.</span></span>  
  
    > [!IMPORTANT]  
    >  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="1702c-121">구성 관리자는 서버 별칭 구성과 기본 클라이언트 네트워크 라이브러리에 대한 레지스트리 항목을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1702c-121">Configuration Manager creates registry entries for the server alias configurations and default client network library.</span></span> <span data-ttu-id="1702c-122">하지만 애플리케이션은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 클라이언트 네트워크 라이브러리 또는 네트워크 프로토콜을 설치하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1702c-122">However, the application does not install either the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] client network libraries or the network protocols.</span></span> <span data-ttu-id="1702c-123">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 클라이언트 네트워크 라이브러리는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 설치 중에 함께 설치되며 네트워크 프로토콜은 Microsoft Windows 설치 프로그램의 일부로 설치되거나 **제어판**의 **네트워크**를 통해 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="1702c-123">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] client network libraries are installed during [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup; the network protocols are installed as part of Microsoft Windows Setup (or through **Networks** in **Control Panel**).</span></span> <span data-ttu-id="1702c-124">특정 네트워크 프로토콜은 Windows 설치 프로그램의 일부로 제공되지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1702c-124">A particular network protocol may not be available as part of Windows Setup.</span></span> <span data-ttu-id="1702c-125">이러한 네트워크 프로토콜을 설치하는 방법은 공급업체 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="1702c-125">For more information about installing these network protocols, see the vendor documentation.</span></span>  
  
###  <a name="to-configure-a-client-to-use-tcpip"></a><a name="Configure"></a> <span data-ttu-id="1702c-126">클라이언트에서 TCP/IP를 사용하도록 구성하려면</span><span class="sxs-lookup"><span data-stu-id="1702c-126">To configure a client to use TCP/IP</span></span>  
  
1.  <span data-ttu-id="1702c-127">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구성 관리자에서 **SQL Server Native Client 구성**을 확장하고 **클라이언트 프로토콜**을 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1702c-127">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, expand **SQL Server Native Client Configuration**, right-click **Client Protocols**, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="1702c-128">**사용할 수 있는 프로토콜** 상자에서 아래 또는 위로 화살표를 클릭하여 SQL Server에 연결할 때 사용할 프로토콜의 순서를 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="1702c-128">In the **Enabled Protocols** box, click the up and down arrows to change the order in which protocols are tried, when attempting to connect to SQL Server.</span></span> <span data-ttu-id="1702c-129">**사용할 수 있는 프로토콜** 상자의 가장 위에 있는 프로토콜은 기본 프로토콜입니다.</span><span class="sxs-lookup"><span data-stu-id="1702c-129">The top protocol in the **Enabled Protocols** box is the default protocol.</span></span>  
  
 <span data-ttu-id="1702c-130">공유 메모리 프로토콜은 **공유 메모리 프로토콜 사용** 확인란을 선택하여 별도로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="1702c-130">The shared memory protocol is enabled separately by checking the **Enabled Shared Memory Protocol** box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1702c-131">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1702c-131">See Also</span></span>  
 [<span data-ttu-id="1702c-132">원격 로그인 제한 시간 서버 구성 옵션 구성</span><span class="sxs-lookup"><span data-stu-id="1702c-132">Configure the remote login timeout Server Configuration Option</span></span>](configure-the-remote-login-timeout-server-configuration-option.md)  
  
  
