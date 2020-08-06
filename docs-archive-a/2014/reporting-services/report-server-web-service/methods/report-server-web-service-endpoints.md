---
title: 보고서 서버 웹 서비스 엔드포인트 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- management endpoints [Reporting Services]
- Web service [Reporting Services], endpoints
- endpoints [Reporting Services]
- execution endpoints [Reporting Services]
- Report Server Web service, endpoints
ms.assetid: f3f5d85f-9359-4508-bc5a-7f78a3cf7421
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 70281c5171eb37d9888d663542a7850820c81bea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87733548"
---
# <a name="report-server-web-service-endpoints"></a><span data-ttu-id="508e3-102">보고서 서버 웹 서비스 엔드포인트</span><span class="sxs-lookup"><span data-stu-id="508e3-102">Report Server Web Service Endpoints</span></span>
  <span data-ttu-id="508e3-103">보고서 서버 웹 서비스는 보고서 서버 관리 및 보고서의 실행과 탐색을 위한 엔드포인트를 다수 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="508e3-103">The Report Server Web service provides several endpoints for managing a report server as well as executing and navigating reports.</span></span>  
  
## <a name="the-management-endpoints"></a><span data-ttu-id="508e3-104">관리 엔드포인트</span><span class="sxs-lookup"><span data-stu-id="508e3-104">The Management Endpoints</span></span>  
 <span data-ttu-id="508e3-105">보고서 서버에서 개체 관리를 위해 사용할 수 있는 세 가지 엔드포인트에는 <xref:ReportService2005>, <xref:ReportService2006> 및 <xref:ReportService2010>이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="508e3-105">There are three endpoints available for managing objects on a report server, <xref:ReportService2005>, <xref:ReportService2006>, and <xref:ReportService2010>.</span></span> <span data-ttu-id="508e3-106"><xref:ReportService2005> 엔드포인트는 기본 모드로 구성된 보고서 서버에서 개체를 관리하는 데 사용되며,</span><span class="sxs-lookup"><span data-stu-id="508e3-106">The <xref:ReportService2005> endpoint is used for managing objects on a report server that is configured for native mode.</span></span> <span data-ttu-id="508e3-107"><xref:ReportService2006> 엔드포인트는 SharePoint 통합 모드로 구성된 보고서 서버에서 개체를 관리하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="508e3-107">The <xref:ReportService2006> endpoint is used for managing objects on a report server that is configured for SharePoint integrated mode.</span></span> <span data-ttu-id="508e3-108"><xref:ReportService2010> 엔드포인트는 <xref:ReportService2005> 및 <xref:ReportService2006>의 기능을 병합하며, 기본 모드 또는 SharePoint 통합 모드용으로 구성된 보고서 서버의 개체를 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="508e3-108">The <xref:ReportService2010> endpoint merges the functionalities of <xref:ReportService2005> and <xref:ReportService2006> and can manage objects on a report server that are configured for either native or SharePoint integrated mode.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="508e3-109">보고서 서버가 SharePoint 통합 모드로 구성된 경우 <xref:ReportService2005> API는 `rsOperationNotSupportedSharePointMode` 오류를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="508e3-109">When a report server is configured for SharePoint integrated mode, the <xref:ReportService2005> APIs will return an `rsOperationNotSupportedSharePointMode` error.</span></span> <span data-ttu-id="508e3-110">보고서 서버가 기본 모드로 구성된 경우 <xref:ReportService2006> API는 `rsOperationNotSupportedNativeMode` 오류를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="508e3-110">If the report server is configured for native mode, the <xref:ReportService2006> APIs will return an `rsOperationNotSupportedNativeMode` error.</span></span> <span data-ttu-id="508e3-111">마찬가지로 <xref:ReportService2010>의 모드별 API를 잘못된 모드에 사용하면 API에서 해당 오류를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="508e3-111">Similarly, when mode-specific APIs in <xref:ReportService2010> are used on unintended modes, the APIs will return the respective errors.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="508e3-112"><xref:ReportService2005> 및 <xref:ReportService2006> 엔드포인트는 [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)]에서 더 이상 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="508e3-112">The <xref:ReportService2005> and <xref:ReportService2006> endpoints are deprecated in [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)].</span></span> <span data-ttu-id="508e3-113"><xref:ReportService2010>엔드포인트에는 두 엔드포인트의 기능이 모두 포함되어 있으며 추가 관리 기능도 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="508e3-113">The <xref:ReportService2010> endpoint includes the functionalities of both endpoints and contains additional management features.</span></span>  
  
 <span data-ttu-id="508e3-114">보고서 서버가 기본 모드 또는 SharePoint 통합 모드로 구성된 경우 관리 엔드포인트용 WSDL은 다음 URL 중 하나를 사용하여 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="508e3-114">If the report server is configured for native mode or SharePoint integrate mode, the WSDL for the management endpoint can be accessed using one of the following URL:</span></span>  
  
```  
http://<Server Name>/ReportServer/ReportService2010.asmx?wsdl  
```  
  
 <span data-ttu-id="508e3-115">자세한 내용은 [SOAP API 액세스](../accessing-the-soap-api.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="508e3-115">For more information, see [Accessing the SOAP API](../accessing-the-soap-api.md).</span></span>  
  
## <a name="the-execution-endpoint"></a><span data-ttu-id="508e3-116">실행 엔드포인트</span><span class="sxs-lookup"><span data-stu-id="508e3-116">The Execution Endpoint</span></span>  
 <span data-ttu-id="508e3-117"><xref:ReportExecution2005> 엔드포인트를 통해 개발자는 기본 모드 및 SharePoint 통합 모드로 보고서 서버에서 보고서 처리 및 렌더링을 쉽게 사용자 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="508e3-117">The <xref:ReportExecution2005> endpoint makes it easy for developers to customize report processing and rendering from a report server in both native and SharePoint integrated modes.</span></span> <span data-ttu-id="508e3-118">이 엔드포인트에는 이전 버전의 보고서 서버 웹 서비스에 있던 클래스 및 메서드가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="508e3-118">The endpoint includes classes and methods that existed in earlier versions of the Report Server Web service.</span></span> <span data-ttu-id="508e3-119">또한 실행 엔드포인트를 통해 제공되는 다수의 새 클래스 및 메서드가 보고서 서버 웹 서비스에 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="508e3-119">In addition, many new classes and methods have been added to the Report Server Web service that are exposed through the execution endpoint.</span></span>  
  
 <span data-ttu-id="508e3-120">관리 엔드포인트에 대한 WSDL은 다음 URL을 사용하여 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="508e3-120">The WSDL for the management endpoint can be accessed using the following URL:</span></span>  
  
```  
http://<Server Name>/ReportServer/ReportExecution2005.asmx?wsdl  
```  
  
 <span data-ttu-id="508e3-121">보고서 서버가 SharePoint 통합 모드로 구성된 경우 WSDL은 다음 URL을 사용하여 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="508e3-121">If the report server is configured for SharePoint integrate mode, the WSDL can be accessed using the following URL:</span></span>  
  
```  
http://<Server Name>/<Site Name>/_vti_bin/ReportServer/ReportExecution2005.asmx?wsdl  
```  
  
 <span data-ttu-id="508e3-122">자세한 내용은 [SOAP API 액세스](../accessing-the-soap-api.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="508e3-122">For more information, please see [Accessing the SOAP API](../accessing-the-soap-api.md).</span></span>  
  
## <a name="sharepoint-proxy-endpoints"></a><span data-ttu-id="508e3-123">SharePoint 프록시 엔드포인트</span><span class="sxs-lookup"><span data-stu-id="508e3-123">SharePoint Proxy Endpoints</span></span>  
 <span data-ttu-id="508e3-124">보고서 서버가 SharePoint 통합 모드로 구성되고 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 추가 기능이 설치된 경우 프록시 엔드포인트 집합이 SharePoint 서버에 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="508e3-124">When a report server is configured for SharePoint integrated mode and the [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] Add-in has been installed, a set of proxy endpoints are installed on the SharePoint server.</span></span> <span data-ttu-id="508e3-125">프록시 엔드포인트는 보고서 서버가 SharePoint 통합 모드로 구성된 경우 보고서 솔루션을 개발하기 위한 기본 API입니다.</span><span class="sxs-lookup"><span data-stu-id="508e3-125">The proxy endpoints are the primary API for developing report solutions when a report server is configured for SharePoint integrated mode.</span></span> <span data-ttu-id="508e3-126">프록시 엔드포인트에 대해 개발할 때 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 추가 기능은 SharePoint 서버와 트러스트된 계정 인증 모드 보고서 서버 간의 자격 증명 교환을 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="508e3-126">When developing against the proxy endpoints, the [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] Add-in manages the exchange of credentials between the SharePoint server and the report server in Trusted account authentication mode.</span></span> <span data-ttu-id="508e3-127">보고서 서버 엔드포인트에 대해 개발할 때는 호출하는 애플리케이션이 트러스트된 계정 인증 모드에서 자격 증명 교환을 관리해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="508e3-127">When developing against the report server endpoints, the calling application will have to manage the credential exchange in Trusted account authentication mode.</span></span> <span data-ttu-id="508e3-128">다음 표는 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 추가 기능과 함께 설치되는 엔드포인트를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="508e3-128">The following table lists the endpoints that are installed with the [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] Add-in.</span></span>  
  
|<span data-ttu-id="508e3-129">프록시 엔드포인트</span><span class="sxs-lookup"><span data-stu-id="508e3-129">Proxy Endpoint</span></span>|<span data-ttu-id="508e3-130">설명</span><span class="sxs-lookup"><span data-stu-id="508e3-130">Description</span></span>|  
|--------------------|-----------------|  
|<xref:ReportService2006>|<span data-ttu-id="508e3-131">SharePoint 통합 모드로 구성된 보고서 서버를 관리하기 위한 API를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="508e3-131">Provides the APIs for managing a report server that is configured for SharePoint integrate mode.</span></span> <span data-ttu-id="508e3-132">**참고:**  이 끝점은에서 더 이상 사용 되지 않습니다 [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="508e3-132">**Note:**  This endpoint is deprecated in [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)].</span></span>|  
|<xref:ReportService2010>|<span data-ttu-id="508e3-133">기본 모드 또는 SharePoint 통합 모드로 구성된 보고서 서버를 관리하기 위한 API를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="508e3-133">Provides the APIs for managing a report server that is configured for either native or SharePoint integrated mode.</span></span>|  
|<xref:ReportExecution2005>|<span data-ttu-id="508e3-134">보고서 실행 및 탐색을 위한 API를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="508e3-134">Provides the APIs for running and navigating reports.</span></span>|  
|<xref:ReportServiceAuthentication>|<span data-ttu-id="508e3-135">폼 인증을 위해 SharePoint 웹 애플리케이션이 구성된 경우 보고서 서버에 대해 사용자를 인증하기 위한 API를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="508e3-135">Provides the APIs for authenticating users against a report server when the SharePoint Web application is configured for Forms Authentication.</span></span>|  
  
 <span data-ttu-id="508e3-136">다음은 SharePoint 사이트에서 프록시 엔드포인트를 참조하기 위한 URL의 예입니다.</span><span class="sxs-lookup"><span data-stu-id="508e3-136">The following are example URLs for referencing the proxy endpoints on a SharePoint site.</span></span>  
  
```  
http://<Server Name>/<Site Name>/_vti_bin/ReportServer/ReportService2010.asmx  
```  
  
```  
http://<Server Name>/<Site Name>/_vti_bin/ReportServer/ReportExecution2005.asmx  
```  
  
```  
http://<Server Name>/<Site Name>/_vti_bin/ReportServer/ReportServiceAuthentication.asmx  
```  
  
## <a name="see-also"></a><span data-ttu-id="508e3-137">참고 항목</span><span class="sxs-lookup"><span data-stu-id="508e3-137">See Also</span></span>  
 [<span data-ttu-id="508e3-138">웹 서비스와 .NET Framework를 사용하여 애플리케이션 빌드</span><span class="sxs-lookup"><span data-stu-id="508e3-138">Building Applications Using the Web Service and the .NET Framework</span></span>](../net-framework/building-applications-using-the-web-service-and-the-net-framework.md)  
  
  
