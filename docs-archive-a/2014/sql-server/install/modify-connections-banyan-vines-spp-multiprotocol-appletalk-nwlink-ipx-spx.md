---
title: Banyan SPP (VINES 시퀀싱 Packet Protocol), 멀티 프로토콜, AppleTalk 또는 NWLink IPX SPX 네트워크 프로토콜을 사용 하는 연결을 수정 합니다. Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- network protocols [SQL Server], modifying connections
- SPP [SQL Server]
- NWLink IPX/SPX [SQL Server]
- connections [SQL Server]
- AppleTalk [SQL Server]
- Sequenced Packet Protocol [SQL Server]
- Multiprotocol Net-Library [SQL Server]
- Banyan VINES Sequenced Package Protocol [SQL Server]
- IPX/SPX [SQL Server]
- protocols [SQL Server], modifying connections
- RPC [SQL Server]
ms.assetid: 5c5ae453-cc5b-4898-95c7-ad34157b1f60
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 750b9c0b76ab6c3b43908ecb8454f31ac1a25b1a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740695"
---
# <a name="modify-connections-that-use-banyan-vines-sequenced-packet-protocol-spp-multiprotocol-appletalk-or-nwlink-ipx-spx-network-protocols"></a><span data-ttu-id="aee29-102">Banyan VINES SPP(Sequenced Packet Protocol), 멀티프로토콜, AppleTalk 또는 NWLink IPX/SPX 네트워크 프로토콜을 사용하는 연결을 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="aee29-102">Modify connections that use Banyan VINES Sequenced Packet Protocol (SPP), Multiprotocol, AppleTalk, or NWLink IPX SPX network protocols</span></span>
  <span data-ttu-id="aee29-103">업그레이드 관리자가 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]에서 지원되지 않는 클라이언트 서버 연결 프로토콜을 검색했습니다.</span><span class="sxs-lookup"><span data-stu-id="aee29-103">The Upgrade Advisor has detected client server connectivity protocols that are not supported in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="aee29-104">Banyan VINES SPP(Sequenced Packet Protocol), 멀티프로토콜(RPC), AppleTalk 또는 NWLink IPX/SPX 네트워크 프로토콜을 사용하는 클라이언트 애플리케이션은 지원되는 프로토콜을 사용하여 연결해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="aee29-104">Client applications that use Banyan VINES Sequenced Packet Protocol (SPP), Multiprotocol (RPC), AppleTalk, or NWLink IPX/SPX network protocols must connect using a supported protocol.</span></span>  
  
## <a name="component"></a><span data-ttu-id="aee29-105">구성 요소</span><span class="sxs-lookup"><span data-stu-id="aee29-105">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a><span data-ttu-id="aee29-106">Description</span><span class="sxs-lookup"><span data-stu-id="aee29-106">Description</span></span>  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<span data-ttu-id="aee29-107">에서는 Banyan VINES SPP(Sequenced Packet Protocol), 멀티프로토콜, AppleTalk 또는 NWLink IPX/SPX 네트워크 프로토콜을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="aee29-107">does not support the Banyan VINES Sequenced Packet Protocol (SPP), Multiprotocol, AppleTalk, or NWLink IPX/SPX network protocols.</span></span> <span data-ttu-id="aee29-108">이전에 이러한 프로토콜을 사용하여 연결된 클라이언트는 다른 프로토콜을 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="aee29-108">Clients previously connecting with these protocols must select a different protocol.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="aee29-109">수정 동작</span><span class="sxs-lookup"><span data-stu-id="aee29-109">Corrective Action</span></span>  
 <span data-ttu-id="aee29-110">서버에 연결할 때 지원되는 프로토콜을 사용하도록 클라이언트 애플리케이션을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="aee29-110">Change the client applications to use a supported protocol when connecting to the server.</span></span> <span data-ttu-id="aee29-111">지원되지 않는 프로토콜 중 하나를 사용하는 별칭이 설정된 경우 지원되는 프로토콜 중 하나를 사용하도록 해당 별칭을 수정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="aee29-111">If you have an alias setup that uses one of the unsupported protocols then the alias must be modified to use one of the supported protocols.</span></span>  
  
 <span data-ttu-id="aee29-112">응용 프로그램 연결 문자열에서 이러한 프로토콜 중 하나를 사용 하는 경우, RPC에 대해 NETWORK = DBMSRPCN을 지정 하 고, 네트워크 = DBMSRPCN을 지정 하 여 Appletalk를 사용 합니다. 또는 네트워크 = DBMSVINN for Banyan VINES 속성에 대해 또는 "spx: 서버 \ 인스턴스" (예: SPX의 경우 "spx:*server\instance*"), "*bv: Server*" (banyan VINES), "adsp:*server*" (Appletalk의 경우) 또는 "*RPC: server"의*경우 지원 되는 프로토콜 중 하나를 사용 하도록 응용 프로그램을 수정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="aee29-112">If your application connection string specifically uses or loads one of these protocols, by either specifying NETWORK=DBMSRPCN for RPC, NETWORK=DBMSADSN for Appletalk, or NETWORK=DBMSVINN for Banyan VINES property, or by using an explicit prefix such as "spx:*server\instance*" for SPX, "bv:*server*" for Banyan VINES, "adsp:*server*" for AppleTalk, or "rpc:*server*" for multiprotocol, then you must modify your application to use one of the supported protocols.</span></span>  
  
 <span data-ttu-id="aee29-113">자세한 내용은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 온라인 설명서에서 "네트워크 프로토콜 선택"을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="aee29-113">For more information, see "Choosing a Network Protocol" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aee29-114">참고 항목</span><span class="sxs-lookup"><span data-stu-id="aee29-114">See Also</span></span>  
 <span data-ttu-id="aee29-115">[업그레이드 문제 데이터베이스 엔진](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="aee29-115">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="aee29-116">SQL Server 2014 업그레이드 관리자 &#91;새&#93;</span><span class="sxs-lookup"><span data-stu-id="aee29-116">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
