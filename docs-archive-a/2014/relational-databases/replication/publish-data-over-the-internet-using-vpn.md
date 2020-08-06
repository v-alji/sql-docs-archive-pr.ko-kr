---
title: VPN을 사용하여 인터넷을 통해 데이터 게시 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- VPNs [SQL Server replication]
- Web publishing [SQL Server replication], VPNs
- Internet [SQL Server replication], VPNs
ms.assetid: 9ffb6546-9973-4574-aaa0-8fe0017e3601
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 7a477e70031053a9563c2f3ed3740091d632febe
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661035"
---
# <a name="publish-data-over-the-internet-using-vpn"></a><span data-ttu-id="de5c0-102">VPN을 사용하여 인터넷을 통해 데이터 게시</span><span class="sxs-lookup"><span data-stu-id="de5c0-102">Publish Data over the Internet Using VPN</span></span>
  <span data-ttu-id="de5c0-103">VPN(가상 프라이빗 네트워크) 기술을 사용하면 집, 지점, 원격 클라이언트 및 다른 회사에서 사용자가 인터넷을 통해 회사 네트워크에 연결하여 안전하게 통신할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="de5c0-103">Virtual Private Networking (VPN) technology allows users working at home, branch offices, remote clients, and other companies to connect to a corporate network over the Internet, while maintaining secure communications.</span></span> <span data-ttu-id="de5c0-104">사용자는 LAN(근거리 통신망)에서처럼 Windows 인증을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="de5c0-104">Users can use Windows Authentication as though they were on a Local Area Network (LAN).</span></span> <span data-ttu-id="de5c0-105">모든 유형의 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 복제는 VPN을 통해 데이터를 복제할 수 있지만, 웹 동기화에는 VPN이 필요하지 않으므로 병합 복제를 사용할 경우 웹 동기화 사용을 고려해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="de5c0-105">All types of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] replication can replicate data over a VPN, but consider using Web synchronization if you are using merge replication, because Web synchronization eliminates the need for a VPN.</span></span> <span data-ttu-id="de5c0-106">자세한 내용은 [Web Synchronization for Merge Replication](web-synchronization-for-merge-replication.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="de5c0-106">For more information, see [Web Synchronization for Merge Replication](web-synchronization-for-merge-replication.md).</span></span>  
  
 <span data-ttu-id="de5c0-107">VPN에는 클라이언트 소프트웨어가 포함되어 있어 컴퓨터에서 인터넷이나 인트라넷(특별한 경우)으로 전용 컴퓨터 또는 서버의 소프트웨어에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="de5c0-107">A VPN includes client software so that computers connect over the Internet (or in special cases, even an intranet) to software in a dedicated computer or a server.</span></span> <span data-ttu-id="de5c0-108">사용자 인증 방법 외에도 양쪽 모두에서 암호화할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="de5c0-108">Optionally, encryption at both ends, as well as user authentication methods, are used.</span></span> <span data-ttu-id="de5c0-109">인터넷을 통한 VPN 연결은 논리적으로 사이트 간에 WAN(광역 통신망)으로 운영됩니다.</span><span class="sxs-lookup"><span data-stu-id="de5c0-109">The VPN connection over the Internet logically operates as a Wide Area Network (WAN) link between the sites.</span></span>  
  
 <span data-ttu-id="de5c0-110">VPN은 다른 네트워크를 사용하여 네트워크의 구성 요소를 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="de5c0-110">A VPN connects the components of a network using another network.</span></span> <span data-ttu-id="de5c0-111">사용자는 인터넷이나 다른 공용 네트워크( [!INCLUDE[msCoName](../../includes/msconame-md.md)] Point-to-Point Tunneling Protocol(PPTP) 또는 Layer Two Tunneling Protocol(L2TP)과 같은 프로토콜 사용)를 통해 터널을 만들어 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="de5c0-111">To connect, the user tunnels through the Internet or another public network using a protocol such as [!INCLUDE[msCoName](../../includes/msconame-md.md)] Point-to-Point Tunneling Protocol (PPTP) or Layer Two Tunneling Protocol (L2TP).</span></span> <span data-ttu-id="de5c0-112">이 과정은 프라이빗 네트워크에서만 사용할 수 있었던 같은 수준의 보안 및 기능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="de5c0-112">This process provides the same security and features previously available only in a private network.</span></span> <span data-ttu-id="de5c0-113">PPTP는 Microsoft Windows NT 4.0 및 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 2000 이상의 운영 체제에서 사용할 수 있으며 L2TP는 Windows 2000 이상에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="de5c0-113">PPTP is available with the Microsoft Windows NT version 4.0 and [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 2000 (and later) operating systems; L2TP is available with Windows 2000 and later.</span></span>  
  
 <span data-ttu-id="de5c0-114">사용자는 인터넷의 중간 라우팅 인프라를 볼 수 없고 데이터는 전용 프라이빗 링크로 전달되는 것처럼 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="de5c0-114">For the user, the intermediate routing infrastructure of the Internet is not visible and it appears as though the data is being sent over a dedicated private link.</span></span> <span data-ttu-id="de5c0-115">사용자가 연결되어 있는 동안 VPN은 사용자 컴퓨터와 회사 서버간에 지점간 연결입니다.</span><span class="sxs-lookup"><span data-stu-id="de5c0-115">As far as users are concerned, the VPN is a point-to-point connection between the user computer and a corporate server.</span></span>  
  
 <span data-ttu-id="de5c0-116">원격 클라이언트가 VPN을 사용하여 연결하도록 구성하고 클라이언트에 인터넷 액세스 권한이 있어 회사 LAN에 로그인하면 원격 클라이언트가 LAN으로 직접 연결된 것처럼 복제를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="de5c0-116">After you have your remote client configured to connect using a VPN, and the client has Internet access and is logged in to the corporate LAN, you can configure replication as though the remote client is connected directly on the LAN.</span></span> <span data-ttu-id="de5c0-117">보안상의 이유로 VPN을 통해 연결한 사용자와 LAN을 통해 직접 연결한 사용자 간에 서로 다른 네트워크 리소스를 사용하도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="de5c0-117">For security reasons, it is possible to have different network resources available to users connected over VPN and to those connected directly on the LAN.</span></span>  
  
 <span data-ttu-id="de5c0-118">VPN 설정 방법은 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="de5c0-118">For more information about setting up a VPN, see the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de5c0-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="de5c0-119">See Also</span></span>  
 [<span data-ttu-id="de5c0-120">인터넷을 통한 복제</span><span class="sxs-lookup"><span data-stu-id="de5c0-120">Replication over the Internet</span></span>](replication-over-the-internet.md)  
  
  
