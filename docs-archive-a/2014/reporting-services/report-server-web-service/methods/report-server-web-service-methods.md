---
title: 보고서 서버 웹 서비스 메서드 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- Report Server Web service, methods
- Web service [Reporting Services], methods
- XML Web service [Reporting Services], features
- Web service [Reporting Services], features
- Report Server Web service, features
- XML Web service [Reporting Services], methods
ms.assetid: ce5afa27-e90c-44a7-b204-098a065b3665
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 37d0031ebfb4ec6d31da6aad9a8842c0623cb75b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647426"
---
# <a name="report-server-web-service-methods"></a><span data-ttu-id="7c8aa-102">보고서 서버 웹 서비스 메서드</span><span class="sxs-lookup"><span data-stu-id="7c8aa-102">Report Server Web Service Methods</span></span>
  <span data-ttu-id="7c8aa-103">보고서 서버 웹 서비스에는 구성 요소 기능에 따라 여러 범주의 메서드가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7c8aa-103">The Report Server Web services include several categories of methods that are based on component features.</span></span> <span data-ttu-id="7c8aa-104">이러한 메서드는 <xref:ReportService2010.ReportingService2010> 및 <xref:ReportExecution2005.ReportExecutionService> 클래스의 멤버로 노출되는 여러 개의 웹 서비스 엔드포인트(세 개는 보고서 관리용, 하나는 보고서 실행용)를 통해 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="7c8aa-104">These methods are provided through several Web service endpoints (three for report management and one for report execution) which are exposed as members of the <xref:ReportService2010.ReportingService2010> and <xref:ReportExecution2005.ReportExecutionService> classes.</span></span> <span data-ttu-id="7c8aa-105">이러한 클래스는 SDK에 포함 된 wsdl.exe와 같은 프록시 클래스 도구를 통해 생성할 수 있습니다 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="7c8aa-105">These classes can be generated through a proxy class tool such as wsdl.exe, which is included with the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] SDK.</span></span> <span data-ttu-id="7c8aa-106">보고서 서버 웹 서비스 및 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]에 대한 자세한 내용은 [웹 서비스와 .NET Framework를 사용하여 애플리케이션 빌드](../net-framework/building-applications-using-the-web-service-and-the-net-framework.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7c8aa-106">For more information about the Report Server Web services and the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], see [Building Applications Using the Web Service and the .NET Framework](../net-framework/building-applications-using-the-web-service-and-the-net-framework.md).</span></span>  
  
## <a name="endpoints-and-methods"></a><span data-ttu-id="7c8aa-107">엔드포인트 및 메서드</span><span class="sxs-lookup"><span data-stu-id="7c8aa-107">Endpoints and Methods</span></span>  
 <span data-ttu-id="7c8aa-108">다음 표는 보고서 서버 웹 서비스의 엔드포인트와 <xref:ReportService2010.ReportingService2010> 엔드포인트에서 제공하는 메서드의 범주를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="7c8aa-108">The following table lists the endpoints of the Report Server Web service, and the categories of methods provided by the <xref:ReportService2010.ReportingService2010> endpoint.</span></span> <span data-ttu-id="7c8aa-109">다른 엔드포인트에서 사용할 수 있는 메서드에 대한 자세한 내용은 [기술 참조&#40;SSRS&#41;](../../technical-reference-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7c8aa-109">For information on the methods available in the other endpoints, see [Technical Reference &#40;SSRS&#41;](../../technical-reference-ssrs.md).</span></span>  
  
|<span data-ttu-id="7c8aa-110">항목</span><span class="sxs-lookup"><span data-stu-id="7c8aa-110">Topic</span></span>|<span data-ttu-id="7c8aa-111">Description</span><span class="sxs-lookup"><span data-stu-id="7c8aa-111">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="7c8aa-112">보고서 서버 웹 서비스 엔드포인트</span><span class="sxs-lookup"><span data-stu-id="7c8aa-112">Report Server Web Service Endpoints</span></span>](report-server-web-service-endpoints.md)|<span data-ttu-id="7c8aa-113">보고서 서버 웹 서비스의 관리 및 실행 엔드포인트를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="7c8aa-113">Describes the management and execution endpoints of the Report Server Web service.</span></span>|  
|[<span data-ttu-id="7c8aa-114">보고서 서버 네임스페이스 관리 메서드</span><span class="sxs-lookup"><span data-stu-id="7c8aa-114">Report Server Namespace Management Methods</span></span>](report-server-namespace-management-methods.md)|<span data-ttu-id="7c8aa-115">보고서 서버 데이터베이스를 관리하는 데 사용할 수 있는 메서드를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="7c8aa-115">Describes methods that you can use to manage the report server database.</span></span> <span data-ttu-id="7c8aa-116">특히 폴더 및 리소스를 관리하고 항목 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7c8aa-116">Specifically you can manage folders and resources and set item properties.</span></span>|  
|[<span data-ttu-id="7c8aa-117">권한 부여 방법</span><span class="sxs-lookup"><span data-stu-id="7c8aa-117">Authorization Methods</span></span>](authorization-methods.md)|<span data-ttu-id="7c8aa-118">태스크, 역할 및 정책을 관리하는 데 사용할 수 있는 메서드를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="7c8aa-118">Describes methods that you can use to manage tasks, roles, and policies.</span></span>|  
|[<span data-ttu-id="7c8aa-119">데이터 원본 및 연결 메서드</span><span class="sxs-lookup"><span data-stu-id="7c8aa-119">Data Sources and Connection Methods</span></span>](data-sources-and-connection-methods.md)|<span data-ttu-id="7c8aa-120">보고서에 대한 데이터 원본 연결과 자격 증명 정보를 설정하고 관리하는 데 사용할 수 있는 메서드를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="7c8aa-120">Describes methods that you can use to set and manage data source connection and credential information for reports.</span></span>|  
|[<span data-ttu-id="7c8aa-121">보고서 매개 변수 메서드</span><span class="sxs-lookup"><span data-stu-id="7c8aa-121">Report Parameters Methods</span></span>](report-parameters-methods.md)|<span data-ttu-id="7c8aa-122">보고서의 매개 변수를 설정하고 검색하는 데 사용할 수 있는 메서드를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="7c8aa-122">Describes methods that you can use to set and retrieve parameters for reports.</span></span>|  
|[<span data-ttu-id="7c8aa-123">모델 메서드</span><span class="sxs-lookup"><span data-stu-id="7c8aa-123">Model Methods</span></span>](../report-server-web-service.md)|<span data-ttu-id="7c8aa-124">모델을 관리하는 데 사용할 수 있는 메서드를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="7c8aa-124">Describes methods that you can use to manage models.</span></span>|  
|[<span data-ttu-id="7c8aa-125">렌더링 및 실행 메서드</span><span class="sxs-lookup"><span data-stu-id="7c8aa-125">Rendering and Execution Methods</span></span>](rendering-and-execution-methods.md)|<span data-ttu-id="7c8aa-126">보고서 실행, 렌더링 및 캐싱을 관리하는 데 사용할 수 있는 메서드를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="7c8aa-126">Describes methods that you can use to manage report execution, rendering, and caching.</span></span>|  
|[<span data-ttu-id="7c8aa-127">보고서 기록 메서드</span><span class="sxs-lookup"><span data-stu-id="7c8aa-127">Report History Methods</span></span>](report-history-methods.md)|<span data-ttu-id="7c8aa-128">보고서 기록 스냅샷을 만들고 관리하는 데 사용할 수 있는 메서드를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="7c8aa-128">Describes methods that you can use to create and manage report history snapshots.</span></span>|  
|[<span data-ttu-id="7c8aa-129">일정 예약 메서드</span><span class="sxs-lookup"><span data-stu-id="7c8aa-129">Scheduling Methods</span></span>](scheduling-methods.md)|<span data-ttu-id="7c8aa-130">보고서 서버에서 사용되는 공유 일정 및 캐시 새로 고침 계획을 만들고 관리하는 데 사용할 수 있는 메서드를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="7c8aa-130">Describes methods that you can use to create and manage shared schedules and cache refresh plans that are used by the report server.</span></span>|  
|[<span data-ttu-id="7c8aa-131">구독 및 배달 메서드</span><span class="sxs-lookup"><span data-stu-id="7c8aa-131">Subscription and Delivery Methods</span></span>](subscription-and-delivery-methods.md)|<span data-ttu-id="7c8aa-132">구독 및 보고서 배달을 만들고 관리하는 데 사용할 수 있는 메서드를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="7c8aa-132">Describes methods that you can use to create and manage subscriptions and report delivery.</span></span>|  
|[<span data-ttu-id="7c8aa-133">링크된 보고서 메서드</span><span class="sxs-lookup"><span data-stu-id="7c8aa-133">Linked Reports Methods</span></span>](linked-reports-methods.md)|<span data-ttu-id="7c8aa-134">링크된 보고서를 만들고 관리하는 데 사용할 수 있는 메서드를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="7c8aa-134">Describes methods that you can use to create and manage linked reports.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7c8aa-135">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7c8aa-135">See Also</span></span>  
 <span data-ttu-id="7c8aa-136">[SOAP API 액세스](../accessing-the-soap-api.md) </span><span class="sxs-lookup"><span data-stu-id="7c8aa-136">[Accessing the SOAP API](../accessing-the-soap-api.md) </span></span>  
 <span data-ttu-id="7c8aa-137">[웹 서비스와 .NET Framework를 사용하여 애플리케이션 빌드](../net-framework/building-applications-using-the-web-service-and-the-net-framework.md) </span><span class="sxs-lookup"><span data-stu-id="7c8aa-137">[Building Applications Using the Web Service and the .NET Framework](../net-framework/building-applications-using-the-web-service-and-the-net-framework.md) </span></span>  
 <span data-ttu-id="7c8aa-138">[보고서 서버 웹 서비스](../report-server-web-service.md) </span><span class="sxs-lookup"><span data-stu-id="7c8aa-138">[Report Server Web Service](../report-server-web-service.md) </span></span>  
 [<span data-ttu-id="7c8aa-139">기술 참조&#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="7c8aa-139">Technical Reference &#40;SSRS&#41;</span></span>](../../technical-reference-ssrs.md)  
  
  
