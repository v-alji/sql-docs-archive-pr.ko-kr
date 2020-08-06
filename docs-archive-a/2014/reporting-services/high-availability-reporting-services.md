---
title: 고가용성 (Reporting Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- high availability [SQL Server], Reporting Services
- high availability [Reporting Services]
- Reporting Services, high availability
ms.assetid: 50e0813f-f591-4688-9cd1-e6389a3808e5
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: dfa0548bc526b007c4301572cd1a8e47a2851e18
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661529"
---
# <a name="high-availability-reporting-services"></a><span data-ttu-id="60802-102">고가용성(Reporting Services)</span><span class="sxs-lookup"><span data-stu-id="60802-102">High Availability (Reporting Services)</span></span>
  <span data-ttu-id="60802-103">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 보고서 서버는 애플리케이션 데이터, 내용, 속성 및 세션 정보를 두 개의 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 관계형 데이터베이스에 저장하는 상태 비저장 서버입니다.</span><span class="sxs-lookup"><span data-stu-id="60802-103">A [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] report server is a stateless server that stores application data, content, properties, and session information in two [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] relational databases.</span></span> <span data-ttu-id="60802-104">따라서 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 기능의 가용성을 보장하는 가장 좋은 방법은 다음을 수행하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="60802-104">As such, the best way to ensure the availability of [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] functionality is to do the following:</span></span>  
  
-   <span data-ttu-id="60802-105">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../includes/ssde-md.md)]의 고가용성 기능을 사용하여 보고서 서버 데이터베이스의 작동 시간을 최대화합니다.</span><span class="sxs-lookup"><span data-stu-id="60802-105">Use the high availability features of the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../includes/ssde-md.md)] to maximize the uptime of the report server databases.</span></span> <span data-ttu-id="60802-106">장애 조치(Failover) 클러스터에서 실행되도록 [!INCLUDE[ssDE](../includes/ssde-md.md)] 인스턴스를 구성하는 경우 보고서 서버 데이터베이스를 만들 때 해당 인스턴스를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="60802-106">If you configure a [!INCLUDE[ssDE](../includes/ssde-md.md)] instance to run in a failover cluster, you can select that instance when you create a report server database.</span></span>  
  
-   <span data-ttu-id="60802-107">가능하면 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 데이터베이스 및 데이터 원본에서 [!INCLUDE[ssHADR](../includes/sshadr-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="60802-107">Use [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssHADR](../includes/sshadr-md.md)] with the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] databases and for data sources, as possible.</span></span> <span data-ttu-id="60802-108">자세한 내용은 [AlwaysOn 가용성 그룹이 포함된 Reporting Services&#40;SQL Server&#41;](../database-engine/availability-groups/windows/reporting-services-with-always-on-availability-groups-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="60802-108">For more information, see [Reporting Services with AlwaysOn Availability Groups &#40;SQL Server&#41;](../database-engine/availability-groups/windows/reporting-services-with-always-on-availability-groups-sql-server.md).</span></span>  
  
-   <span data-ttu-id="60802-109">모든 서버가 단일 보고서 서버 데이터베이스를 공유하는 스케일 아웃 배포에서 여러 보고서 서버가 실행되도록 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="60802-109">Configure multiple report servers to run in a scale-out deployment, where all the servers share a single report server database.</span></span> <span data-ttu-id="60802-110">스케일 아웃 배포에서 서로 다른 서버에 여러 보고서 서버 인스턴스를 배포하면 보고서 서버 인스턴스 중 하나가 작동이 중단되는 경우에도 중단되지 않는 서비스를 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="60802-110">Deploying multiple report server instances, preferably on different servers, in a scale-out deployment can help provide uninterrupted service in the event one of the report server instances goes down.</span></span>  
  
 <span data-ttu-id="60802-111">스케일 아웃 배포를 사용하면 데이터베이스를 공유할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="60802-111">A scale-out deployment provides a way to share a database.</span></span> <span data-ttu-id="60802-112">한 보고서 서버가 작동이 중단되는 경우에도 같은 배포에 있는 다른 서버는 계속 작동됩니다.</span><span class="sxs-lookup"><span data-stu-id="60802-112">If one report server goes down, other servers in the same deployment will continue to work.</span></span>  
  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] <span data-ttu-id="60802-113">는 클러스터 인식형이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="60802-113">is not cluster-aware.</span></span> <span data-ttu-id="60802-114">스케일 아웃 배포는 단독으로 로드 균형 조정 기능을 제공하지 않습니다. 즉, 보고서 서버의 처리 부하를 감지하고 새 처리 요청을 사용량이 가장 적은 서버로 라우팅하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="60802-114">By itself, a scale-out deployment does not provide load balancing; it does not detect the processing loads on a report server and route new processing requests to the least busy server.</span></span> <span data-ttu-id="60802-115">또한 완료 전에 실패한 처리 요청을 다시 라우팅하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="60802-115">It does not re-route processing requests that failed before completion.</span></span> <span data-ttu-id="60802-116">로드 균형 조정 기능을 사용하려면 보고서 서버를 호스팅하는 웹 서버에 대해 로드 균형 조정을 구성한 다음 스케일 아웃 배포의 보고서 서버를 구성하여 이러한 보고서 서버가 모두 같은 보고서 서버 데이터베이스를 공유하도록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="60802-116">To get load balancing features, you must configure load balancing for the Web servers that host the report servers, and then configure the report servers in a scale-out deployment so that they share the same report server database.</span></span>  
  
 <span data-ttu-id="60802-117">보고서 서버 웹 서비스 및 Windows 서비스는 완벽하게 통합되어 있으며 단일 보고서 서버 인스턴스로 함께 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="60802-117">The Report Server Web service and Windows service are tightly integrated and run together as a single report server instance.</span></span> <span data-ttu-id="60802-118">한 서비스에 대한 가용성을 다른 서비스와 별도로 구성할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="60802-118">You cannot configure availability for one service separately from the other.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60802-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="60802-119">See Also</span></span>  
 <span data-ttu-id="60802-120">[고가용성 솔루션&#40;SQL Server&#41;](../sql-server/failover-clusters/high-availability-solutions-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="60802-120">[High Availability Solutions &#40;SQL Server&#41;](../sql-server/failover-clusters/high-availability-solutions-sql-server.md) </span></span>  
 [<span data-ttu-id="60802-121">기본 모드 보고서 서버 스케일 아웃 배포 구성&#40;SSRS Configuration Manager&#41;</span><span class="sxs-lookup"><span data-stu-id="60802-121">Configure a Native Mode Report Server Scale-Out Deployment &#40;SSRS Configuration Manager&#41;</span></span>](install-windows/configure-a-native-mode-report-server-scale-out-deployment.md)  
  
  
