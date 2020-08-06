---
title: I p v 6를 사용 하 여 연결 Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- Internet Protocol
- IPv4
- IPv6
ms.assetid: 2669098c-f5f1-43da-aec6-e91003ac89f6
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0f2ecd605f67446fade262cfe795f344dfb165c0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735755"
---
# <a name="connecting-using-ipv6"></a><span data-ttu-id="32bfc-102">IPv6을 사용하여 연결</span><span class="sxs-lookup"><span data-stu-id="32bfc-102">Connecting Using IPv6</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="32bfc-103">및 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client는 인터넷 프로토콜 버전 4(IPv4)와 인터넷 프로토콜 버전 6(IPv6)을 둘 다 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="32bfc-103">and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client fully support both Internet Protocol version 4 (IPv4) and Internet Protocol version 6 (IPv6).</span></span> <span data-ttu-id="32bfc-104">Windows가 IPv6 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]로 구성되어 있으면 구성 요소가 자동으로 IPv6을 인식합니다.</span><span class="sxs-lookup"><span data-stu-id="32bfc-104">When Windows is configured with IPv6 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], components automatically recognize the existence of IPv6.</span></span> <span data-ttu-id="32bfc-105">특별한 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구성은 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="32bfc-105">No special [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] configuration is necessary.</span></span>  
  
 <span data-ttu-id="32bfc-106">지원은 다음을 포함하지만 이에 제한되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="32bfc-106">Support includes but is not limited to the following:</span></span>  
  
-   <span data-ttu-id="32bfc-107">[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 과 다른 서버 구성 요소는 IPv4 및 IPv6 주소에서 동시에 수신할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="32bfc-107">The [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] and the other server components can listen on both IPv4 and IPv6 addresses at the same time.</span></span> <span data-ttu-id="32bfc-108">IPv4와 IPv6이 둘 다 있는 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구성 관리자를 사용하여 IPv4 주소에서만 수신하거나 IPv6 주소에서만 수신하도록 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="32bfc-108">When both IPv4 and IPv6 are present, you can use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager to configure the [!INCLUDE[ssDE](../../includes/ssde-md.md)] to listen only on IPv4 addresses or only on IPv6 addresses.</span></span>  
  
-   <span data-ttu-id="32bfc-109">IPv4와 IPv6을 둘 다 지원하는 컴퓨터에서 실행되는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser 서비스를 IPv4 주소에서 쿼리하면 이 서비스는 IPv4 주소 및 해당 목록에 있는 첫 번째 IPv4 TCP 포트를 사용하여 응답합니다.</span><span class="sxs-lookup"><span data-stu-id="32bfc-109">When the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser service running on a machine that supports both IPv4 and IPv6 is queried on an IPv4 address, it responds with an IPv4 address and the first IPv4 TCP port in its list.</span></span> <span data-ttu-id="32bfc-110">IPv6 주소에서 쿼리하면 IPv6 주소 및 해당 목록에 있는 첫 번째 IPv6 TCP 포트를 사용하여 응답합니다.</span><span class="sxs-lookup"><span data-stu-id="32bfc-110">When queried on an IPv6 address, it responds with an IPv6 address and the first IPv6 TCP port in its list.</span></span> <span data-ttu-id="32bfc-111">불일치를 방지하려면 IPv4 및 IPv6 수신기가 동일한 포트를 수신하도록 구성하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="32bfc-111">To avoid inconsistency, we recommend that the IPv4 and IPv6 listeners be configured to listen to the same port.</span></span>  
  
-   <span data-ttu-id="32bfc-112">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 및 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구성 관리자 같은 도구는 IP 주소에 대한 IPv4 및 IPv6 형식을 둘 다 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="32bfc-112">Tools such as [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager accept both IPv4 and IPv6 formats for IP addresses.</span></span> <span data-ttu-id="32bfc-113">\<*computer_name*> \\ < 서버 호스트 이름 또는 FQDN (정규화 된 도메인 이름)을 사용 하 여 *instance_name*> 지정 하는 경우 대부분의 경우 연결 문자열을 수정할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="32bfc-113">In most cases, the connection string does not need to be modified if the \<*computer_name*>\\<*instance_name*> is specified using server hostname or fully qualified domain name (FQDN).</span></span> <span data-ttu-id="32bfc-114">서버 컴퓨터에 IPv4와 IPv6이 둘 다 있으면 해당 호스트 이름이나 FQDN이 하나 이상의 IPv4 주소 및 여러 개의 IPv6 주소를 포함하여 여러 IP 주소로 확인됩니다.</span><span class="sxs-lookup"><span data-stu-id="32bfc-114">If the server computer has both IPv4 and IPv6, its hostname or FQDN will be resolved into multiple IP addresses, including at least one IPv4 address and multiple IPv6 addresses.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="32bfc-115">Native Client는 TCP/IP로부터 받은 순서대로 이러한 IP 주소를 사용하여 연결을 시도하고 첫 번째로 성공한 연결을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="32bfc-115">Native Client attempts to establish connections using these IP addresses in the order received from TCP/IP and uses the first connection that succeeds.</span></span> <span data-ttu-id="32bfc-116">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client에서 순서를 예측할 수 없는 경우에는 임의의 순서로 간주됩니다.</span><span class="sxs-lookup"><span data-stu-id="32bfc-116">Because the order cannot be predicted by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client, this should be regarded as random order.</span></span> <span data-ttu-id="32bfc-117">IPv4 주소와 IPv6 주소가 둘 다 있으면 IPv4 주소를 먼저 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="32bfc-117">IPv4 addresses are attempted first if both IPv4 and IPv6 addresses are present.</span></span> <span data-ttu-id="32bfc-118">ODBC, OLE DB 또는 ADO.NET 사용자는 이 논리를 인식하지 못합니다.</span><span class="sxs-lookup"><span data-stu-id="32bfc-118">This logic is transparent to the users of ODBC, OLE DB, or ADO.NET.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="32bfc-119">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 이 IPv4에서 수신하지 않는 경우 시도된 IPv4 연결은 IPv6 주소가 시도될 때까지 제한 시간 동안 대기해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="32bfc-119">If the [!INCLUDE[ssDE](../../includes/ssde-md.md)] is not listening on IPv4, the attempted IPv4 connection must wait for the time-out period before the IPv6 address is attempted.</span></span> <span data-ttu-id="32bfc-120">이를 방지하려면 IPv6 IP 주소에 직접 연결하거나 IPv6 주소를 가진 클라이언트에서 별칭을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="32bfc-120">To avoid this, connect directly to the IPv6 IP address or configure an alias on the client with the IPv6 address.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32bfc-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="32bfc-121">See Also</span></span>  
 [<span data-ttu-id="32bfc-122">SQL Server 구성 관리자</span><span class="sxs-lookup"><span data-stu-id="32bfc-122">SQL Server Configuration Manager</span></span>](../../relational-databases/sql-server-configuration-manager.md)  
  
  
