---
title: 웹 동기화를 위한 토폴로지 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Web synchronization, topologies
- IIS server configuration [SQL Server replication]
ms.assetid: 59444faf-bcb6-4421-a3df-8715753e453b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5e28ca5a222e2286d154c16ef41d3147dc56e25a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651639"
---
# <a name="topologies-for-web-synchronization"></a><span data-ttu-id="0e065-102">Topologies for Web Synchronization</span><span class="sxs-lookup"><span data-stu-id="0e065-102">Topologies for Web Synchronization</span></span>
  <span data-ttu-id="0e065-103">다양한 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 웹 동기화 복제 토폴로지를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0e065-103">You can choose from a variety of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Web synchronization replication topologies.</span></span> <span data-ttu-id="0e065-104">웹 동기화를 구성하는 일반적인 방법은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="0e065-104">Common ways to configure Web synchronization include:</span></span>  
  
-   <span data-ttu-id="0e065-105">단일 서버</span><span class="sxs-lookup"><span data-stu-id="0e065-105">Single server</span></span>  
  
-   <span data-ttu-id="0e065-106">두 대의 서버</span><span class="sxs-lookup"><span data-stu-id="0e065-106">Two servers</span></span>  
  
-   <span data-ttu-id="0e065-107">여러 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 인터넷 정보 서비스(IIS) 시스템 및 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 재게시</span><span class="sxs-lookup"><span data-stu-id="0e065-107">Multiple [!INCLUDE[msCoName](../../includes/msconame-md.md)] Internet Information Services (IIS) systems and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] republishing</span></span>  
  
 <span data-ttu-id="0e065-108">웹 동기화를 구성하는 방법은 [웹 동기화 구성](configure-web-synchronization.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0e065-108">For information about configuring Web synchronization, see [Configure Web Synchronization](configure-web-synchronization.md).</span></span>  
  
## <a name="single-server"></a><span data-ttu-id="0e065-109">단일 서버</span><span class="sxs-lookup"><span data-stu-id="0e065-109">Single Server</span></span>  
 <span data-ttu-id="0e065-110">가장 간단한 토폴로지에서 IIS, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 게시자 및 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 배포자는 모두 단일 서버에 상주합니다.</span><span class="sxs-lookup"><span data-stu-id="0e065-110">In the simplest topology, IIS, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Publisher, and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributor all reside on a single server.</span></span> <span data-ttu-id="0e065-111">구독자는 게시자의 IIS에 연결하여 동기화합니다.</span><span class="sxs-lookup"><span data-stu-id="0e065-111">Subscribers synchronize by connecting to IIS on the Publisher.</span></span> <span data-ttu-id="0e065-112">게시자는 방화벽 뒤에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0e065-112">The Publisher can be located behind a firewall.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0e065-113">이 구성은 인트라넷 시나리오에만 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="0e065-113">This configuration is recommended only for intranet scenarios.</span></span> <span data-ttu-id="0e065-114">다른 시나리오에서는 IIS 서버와 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 게시자/배포자를 별도의 컴퓨터에 두는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="0e065-114">For other scenarios, it is recommended that the IIS server and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Publisher/Distributor be on separate computers.</span></span>  
  
 <span data-ttu-id="0e065-115">![단일 서버를 사용한 웹 동기화](media/web-sync02.gif "단일 서버를 사용한 웹 동기화")</span><span class="sxs-lookup"><span data-stu-id="0e065-115">![Web synchronization with a single server](media/web-sync02.gif "Web synchronization with a single server")</span></span>  
  
## <a name="two-servers"></a><span data-ttu-id="0e065-116">두 대의 서버</span><span class="sxs-lookup"><span data-stu-id="0e065-116">Two Servers</span></span>  
 <span data-ttu-id="0e065-117">한 서버에는 IIS를 두고 다른 서버에는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 게시자와 배포자를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0e065-117">You can place IIS on one server and configure the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Publisher and Distributor on another server.</span></span> <span data-ttu-id="0e065-118">IIS를 실행하는 서버는 방화벽에 의해 인터넷에서 격리될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0e065-118">The server running IIS can be isolated from the Internet by a firewall.</span></span> <span data-ttu-id="0e065-119">구독자는 IIS에 연결하여 동기화합니다.</span><span class="sxs-lookup"><span data-stu-id="0e065-119">Subscribers synchronize by connecting to IIS.</span></span>  
  
 <span data-ttu-id="0e065-120">![2대의 서버를 사용한 웹 동기화](media/web-sync03.gif "2대의 서버를 사용한 웹 동기화")</span><span class="sxs-lookup"><span data-stu-id="0e065-120">![Web synchronization with two servers](media/web-sync03.gif "Web synchronization with two servers")</span></span>  
  
## <a name="multiple-iis-systems-and-sql-server-republishing"></a><span data-ttu-id="0e065-121">여러 IIS 시스템 및 SQL Server 재게시</span><span class="sxs-lookup"><span data-stu-id="0e065-121">Multiple IIS Systems and SQL Server Republishing</span></span>  
 <span data-ttu-id="0e065-122">동시에 동기화하는 많은 수의 구독자를 지원해야 하는 경우 IIS를 실행하는 여러 개의 컴퓨터에 작업을 분할할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0e065-122">If you need to support very large numbers of Subscribers that synchronize at the same time, you can partition the work across multiple computers running IIS.</span></span>  
  
 <span data-ttu-id="0e065-123">![여러 대의 IIS 서버를 사용한 웹 동기화](media/web-sync04.gif "여러 대의 IIS 서버를 사용한 웹 동기화")</span><span class="sxs-lookup"><span data-stu-id="0e065-123">![Web synchronization with multiple IIS servers](media/web-sync04.gif "Web synchronization with multiple IIS servers")</span></span>  
  
 <span data-ttu-id="0e065-124">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]를 실행하는 컴퓨터에서 로드 균형 조정이 필요한 경우 여러 컴퓨터에 재게시 계층을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0e065-124">If further load balancing is required on the computer running [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], you can create a republishing hierarchy on multiple computers.</span></span> <span data-ttu-id="0e065-125">최상위 게시자에서 데이터를 구독자에 게시하면 구독자에서는 데이터를 다시 게시하고 최상위 게시자에서는 구독자의 로드 균형 조정 요청을 게시합니다.</span><span class="sxs-lookup"><span data-stu-id="0e065-125">The top-level Publisher publishes data to Subscribers, which in turn republish the data, load balancing requests from the Subscribers.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0e065-126">구독자는 특정 게시자하고만 동기화될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0e065-126">Subscribers can only synchronize with a specific Publisher.</span></span> <span data-ttu-id="0e065-127">예를 들어 재게시자 A의 구독자는 A를 사용할 수 없는 경우 재게시자 B와도 동기화될 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0e065-127">For example, a Subscriber to republisher A cannot synchronize with republisher B when A is not available.</span></span>  
  
 <span data-ttu-id="0e065-128">![다시 게시를 사용한 웹 동기화](media/web-sync05.gif "다시 게시를 사용한 웹 동기화")</span><span class="sxs-lookup"><span data-stu-id="0e065-128">![Web synchronization with republishing](media/web-sync05.gif "Web synchronization with republishing")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e065-129">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0e065-129">See Also</span></span>  
 <span data-ttu-id="0e065-130">[Configure Web Synchronization](configure-web-synchronization.md) </span><span class="sxs-lookup"><span data-stu-id="0e065-130">[Configure Web Synchronization](configure-web-synchronization.md) </span></span>  
 [<span data-ttu-id="0e065-131">병합 복제에 대한 웹 동기화</span><span class="sxs-lookup"><span data-stu-id="0e065-131">Web Synchronization for Merge Replication</span></span>](web-synchronization-for-merge-replication.md)  
  
  
