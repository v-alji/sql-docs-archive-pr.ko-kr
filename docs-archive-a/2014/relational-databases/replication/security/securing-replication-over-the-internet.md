---
title: 인터넷을 통한 복제 보안 설정 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- security [SQL Server replication], Internet
- Internet [SQL Server replication], security
ms.assetid: 25b7af05-2721-4b24-9083-fb671e8bf4e0
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 47408b2b9559d33da4563c6fc9560d20338ee01d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740807"
---
# <a name="securing-replication-over-the-internet"></a><span data-ttu-id="63bd0-102">Securing Replication Over the Internet</span><span class="sxs-lookup"><span data-stu-id="63bd0-102">Securing Replication Over the Internet</span></span>
  <span data-ttu-id="63bd0-103">인터넷을 통한 복제는 특히 모바일 구독자에게 유용하지만 적절한 보안을 유지하려면 인터넷 복제를 알맞게 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="63bd0-103">Replication over the Internet can provide flexibility, particularly for mobile Subscribers, but you must configure Internet replication appropriately to ensure adequate security.</span></span> [!INCLUDE[msCoName](../../../includes/msconame-md.md)] <span data-ttu-id="63bd0-104">에서는 다음 두 가지 기술 중 하나를 통해 인터넷에서 정보를 안전하게 공유할 것을 권장합니다.</span><span class="sxs-lookup"><span data-stu-id="63bd0-104">recommends using one of two techniques for securely sharing information over the Internet:</span></span>  
  
-   <span data-ttu-id="63bd0-105">VPN(가상 프라이빗 네트워크)</span><span class="sxs-lookup"><span data-stu-id="63bd0-105">Virtual private network (VPN)</span></span>  
  
-   <span data-ttu-id="63bd0-106">병합 복제를 위한 웹 동기화 옵션</span><span class="sxs-lookup"><span data-stu-id="63bd0-106">The Web synchronization option for merge replication</span></span>  
  
## <a name="virtual-private-network"></a><span data-ttu-id="63bd0-107">가상 프라이빗 네트워크</span><span class="sxs-lookup"><span data-stu-id="63bd0-107">Virtual Private Network</span></span>  
 <span data-ttu-id="63bd0-108">가상 프라이빗 네트워크는 인터넷을 통해 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 데이터를 복제하는 경우 간단하고 안전한 계층 방식을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="63bd0-108">Virtual private networks provide a simple and secure layered approach to replicating [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] data over the Internet.</span></span> <span data-ttu-id="63bd0-109">인터넷을 통한 VPN 연결은 논리적으로 사이트 간에 WAN(광역 통신망)으로 운영됩니다.</span><span class="sxs-lookup"><span data-stu-id="63bd0-109">The VPN connection over the Internet logically operates as a Wide Area Network (WAN) link between the sites.</span></span>  
  
 <span data-ttu-id="63bd0-110">그러기 위해서는 사용자가 인터넷이나 다른 공용 네트워크( [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows NT 버전 4.0 또는 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows 2000 운영 체제에서 사용할 수 있는 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] 지점 간 터널링 프로토콜(PPTP)이나 Windows 2000 운영 체제에서 사용할 수 있는 계층 2 터널링 프로토콜(L2TP)과 같은 프로토콜을 사용하는 네트워크)를 통해 터널링할 수 있도록 허용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="63bd0-110">This is achieved by allowing the user to tunnel through the Internet or another public network using a protocol such as [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Point-to-Point Tunneling Protocol (PPTP) available with the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows NT version 4.0 or [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows 2000 operating system, or Layer Two Tunneling Protocol (L2TP) available with the Windows 2000 operating system.</span></span> <span data-ttu-id="63bd0-111">이 프로세스는 프라이빗 네트워크에서 사용할 수 있는 것과 유사한 보안 및 기능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="63bd0-111">This process provides security and features similar to those available in a private network.</span></span>  
  
 <span data-ttu-id="63bd0-112">VPN 설정 방법은 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="63bd0-112">For more information about setting up a VPN, see the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows documentation.</span></span>  
  
## <a name="web-synchronization-through-iis"></a><span data-ttu-id="63bd0-113">IIS를 통한 웹 동기화</span><span class="sxs-lookup"><span data-stu-id="63bd0-113">Web Synchronization Through IIS</span></span>  
 <span data-ttu-id="63bd0-114">병합 복제를 위한 웹 동기화 옵션은 HTTPS 프로토콜을 사용하여 데이터를 복제하는 기능을 제공하며 이 기능은 방화벽을 통해 데이터를 복제하는 편리한 방법이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63bd0-114">The web synchronization option for merge replication provides the ability to replicate data using the HTTPS protocol, which can be a convenient approach to replicating data through a firewall.</span></span> <span data-ttu-id="63bd0-115">웹 동기화 보안에 대한 자세한 내용은 [웹 동기화 구성](../configure-web-synchronization.md) 및 [웹 동기화를 위한 보안 아키텍처](security-architecture-for-web-synchronization.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="63bd0-115">For more information, see [Configure Web Synchronization](../configure-web-synchronization.md) and [Security Architecture for Web Synchronization](security-architecture-for-web-synchronization.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63bd0-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="63bd0-116">See Also</span></span>  
 <span data-ttu-id="63bd0-117">[Replication Security Best Practices](replication-security-best-practices.md) </span><span class="sxs-lookup"><span data-stu-id="63bd0-117">[Replication Security Best Practices](replication-security-best-practices.md) </span></span>  
 [<span data-ttu-id="63bd0-118">SQL Server 복제 보안</span><span class="sxs-lookup"><span data-stu-id="63bd0-118">SQL Server Replication Security</span></span>](view-and-modify-replication-security-settings.md)  
  
  
