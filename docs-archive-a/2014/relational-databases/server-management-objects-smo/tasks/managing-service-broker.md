---
title: Service Broker 관리 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- Service Broker [SMO]
ms.assetid: b29d7432-d1e5-4bb6-b544-57b3a9430f95
author: stevestein
ms.author: sstein
ms.openlocfilehash: ce166825bb7adea241bac13defeca1a78b4f29cd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728152"
---
# <a name="managing-service-broker"></a><span data-ttu-id="fb6a8-102">Service Broker 관리</span><span class="sxs-lookup"><span data-stu-id="fb6a8-102">Managing Service Broker</span></span>
  <span data-ttu-id="fb6a8-103">SMO에서 [!INCLUDE[ssSB](../../../includes/sssb-md.md)] 개체는 `Microsoft.SqlServer.Management.Smo.Broker` 네임스페이스에 있기 때문에 Microsoft.SqlServer.Smo.dll에 대한 참조가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="fb6a8-103">In SMO, the [!INCLUDE[ssSB](../../../includes/sssb-md.md)] objects are found in the `Microsoft.SqlServer.Management.Smo.Broker` namespace, which requires a reference to the Microsoft.SqlServer.Smo.dll.</span></span> <span data-ttu-id="fb6a8-104">클래스 정보를 지원하려면 Microsoft.SqlServer.ServiceBrokerEnum.dll에 대한 참조도 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="fb6a8-104">A reference to the Microsoft.SqlServer.ServiceBrokerEnum.dll is also required for supporting class information.</span></span>  
  
 <span data-ttu-id="fb6a8-105">SMO는 [!INCLUDE[ssSB](../../../includes/sssb-md.md)] 구현에 대한 프로그래밍 방식 관리(DDL)를 허용하는 일련의 [!INCLUDE[ssSB](../../../includes/sssb-md.md)] 개체를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="fb6a8-105">SMO provides a set of [!INCLUDE[ssSB](../../../includes/sssb-md.md)] objects that permit programmatic management (DDL) of the [!INCLUDE[ssSB](../../../includes/sssb-md.md)] implementation.</span></span> <span data-ttu-id="fb6a8-106">프로그래밍 방식 관리에는 메시지 유형, 계약, 큐 및 서비스를 정의하는 작업이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="fb6a8-106">This includes defining the message types, contracts, queues, and services.</span></span> <span data-ttu-id="fb6a8-107">SMO는 데이터 조작용 도구가 아니라 관리 도구이므로 [!INCLUDE[ssSB](../../../includes/sssb-md.md)] 메시지를 보내고 받는 것은 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fb6a8-107">Because SMO is a management tool that is not intended for data manipulation, sending and receiving [!INCLUDE[ssSB](../../../includes/sssb-md.md)] messages is not supported by SMO.</span></span>  
  
 <span data-ttu-id="fb6a8-108">SMO에서 <xref:Microsoft.SqlServer.Management.Smo.Database.ServiceBroker%2A> 개체는 최상위 클래스이고 이 클래스 아래에 모든 [!INCLUDE[ssSB](../../../includes/sssb-md.md)] 기능이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="fb6a8-108">In SMO, the <xref:Microsoft.SqlServer.Management.Smo.Database.ServiceBroker%2A> object is the top-level class under which all the [!INCLUDE[ssSB](../../../includes/sssb-md.md)] functionality resides.</span></span> <span data-ttu-id="fb6a8-109">분산 메시징 애플리케이션에 참여하는 각 데이터베이스에 대해서는 [!INCLUDE[ssSB](../../../includes/sssb-md.md)] 를 구현해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fb6a8-109">A [!INCLUDE[ssSB](../../../includes/sssb-md.md)] implementation is required for each database that is participating in the distributed messaging application.</span></span> <span data-ttu-id="fb6a8-110">따라서 <xref:Microsoft.SqlServer.Management.Smo.Broker.ServiceBroker> 개체는 <xref:Microsoft.SqlServer.Management.Smo.Database> 개체의 자식이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fb6a8-110">Therefore, the <xref:Microsoft.SqlServer.Management.Smo.Broker.ServiceBroker> object is a child of the <xref:Microsoft.SqlServer.Management.Smo.Database> object.</span></span>  
  
 <span data-ttu-id="fb6a8-111"><xref:Microsoft.SqlServer.Management.Smo.Broker.ServiceBroker> 개체는 [!INCLUDE[ssSB](../../../includes/sssb-md.md)] 구현을 정의하는 데 사용되는 다음 개체의 컬렉션을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="fb6a8-111">The <xref:Microsoft.SqlServer.Management.Smo.Broker.ServiceBroker> object contains collections of the following objects that are used to define the [!INCLUDE[ssSB](../../../includes/sssb-md.md)] implementation:</span></span>  
  
-   <span data-ttu-id="fb6a8-112"><xref:Microsoft.SqlServer.Management.Smo.Broker.MessageType> 개체는 메시지의 내용을 정의하는 메시지 유형을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="fb6a8-112"><xref:Microsoft.SqlServer.Management.Smo.Broker.MessageType> objects represent message types that define the content of messages.</span></span>  
  
-   <span data-ttu-id="fb6a8-113"><xref:Microsoft.SqlServer.Management.Smo.Broker.MessageTypeMapping> 개체는 특정 대화의 메시지 방향 및 유형을 지정하는 계약을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="fb6a8-113"><xref:Microsoft.SqlServer.Management.Smo.Broker.MessageTypeMapping> objects represent contracts that specify the direction and type of messages in a given conversation.</span></span>  
  
-   <span data-ttu-id="fb6a8-114"><xref:Microsoft.SqlServer.Management.Smo.Broker.ServiceQueue> 개체는 메시지를 보내기 전과 메시지가 수신된 후 메시지를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="fb6a8-114"><xref:Microsoft.SqlServer.Management.Smo.Broker.ServiceQueue> objects store messages prior to sending and after they are received.</span></span> <span data-ttu-id="fb6a8-115">이 개체는 서비스 간의 비동기 통신을 지원하며 같은 대화 그룹의 메시지를 자동으로 잠그는 등의 기타 유용한 기능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="fb6a8-115">They provide asynchronous communication between services, as well as other benefits, such as automatically locking messages in the same conversation group.</span></span>  
  
-   <span data-ttu-id="fb6a8-116"><xref:Microsoft.SqlServer.Management.Smo.Broker.BrokerService> 개체는 대화에 대한 주소 지정 가능 엔드포인트인 [!INCLUDE[ssSB](../../../includes/sssb-md.md)] 서비스를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="fb6a8-116"><xref:Microsoft.SqlServer.Management.Smo.Broker.BrokerService> objects represent [!INCLUDE[ssSB](../../../includes/sssb-md.md)] services, which are the addressable endpoints for conversations.</span></span> [!INCLUDE[ssSB](../../../includes/sssb-md.md)] <span data-ttu-id="fb6a8-117">메시지는 한 서비스에서 다른 서비스로 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="fb6a8-117">messages are sent from one service to another service.</span></span> <span data-ttu-id="fb6a8-118">서비스는 메시지를 보관할 큐를 지정하고 대상이 될 수 있는 서비스에 계약을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="fb6a8-118">A service specifies a queue to hold messages, and specifies the contracts for which the service can be the target.</span></span>  
  
-   <span data-ttu-id="fb6a8-119"><xref:Microsoft.SqlServer.Management.Smo.Broker.RemoteServiceBinding> 개체는 [!INCLUDE[ssSB](../../../includes/sssb-md.md)]가 원격 서비스와의 통신 시 사용하는 보안 및 인증 설정을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="fb6a8-119"><xref:Microsoft.SqlServer.Management.Smo.Broker.RemoteServiceBinding> objects represent the settings that [!INCLUDE[ssSB](../../../includes/sssb-md.md)] uses for security and authentication when communicating with a remote service.</span></span>  
  
-   <span data-ttu-id="fb6a8-120"><xref:Microsoft.SqlServer.Management.Smo.Broker.ServiceRoute> 개체는 서비스 및 서비스가 정의된 데이터베이스에 대한 위치 정보가 포함된 [!INCLUDE[ssSB](../../../includes/sssb-md.md)] 경로를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="fb6a8-120"><xref:Microsoft.SqlServer.Management.Smo.Broker.ServiceRoute> objects represents a [!INCLUDE[ssSB](../../../includes/sssb-md.md)] route, which contains the location information for the service and the database on which it is defined.</span></span> <span data-ttu-id="fb6a8-121">메시지를 배달하려면 경로가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fb6a8-121">A route is required for message delivery.</span></span> <span data-ttu-id="fb6a8-122">각 데이터베이스에는 현재 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]인스턴스를 위치로 지정하는 경로가 기본적으로 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fb6a8-122">By default, each database contains a route that specifies the location as the current instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb6a8-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="fb6a8-123">See Also</span></span>  
 <xref:Microsoft.SqlServer.Management.Smo.Broker>   
 [<span data-ttu-id="fb6a8-124">SQL Server Service Broker</span><span class="sxs-lookup"><span data-stu-id="fb6a8-124">SQL Server Service Broker</span></span>](../../../database-engine/configure-windows/sql-server-service-broker.md)  
  
  
