---
title: SOAP을 사용하여 Reporting Services 통합 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- Report Server Web service, application integration
- SOAP [Reporting Services]
- SOAP [Reporting Services], about report integration
- integrating reports [Reporting Services]
- Web service [Reporting Services], application integration
ms.assetid: 6bc17af5-883c-4bfa-87d9-48cd7056d145
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 7b6fffd65b22900d7c505c4b50ec290b95fe9ab4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639419"
---
# <a name="integrating-reporting-services-using-soap"></a><span data-ttu-id="5a2d5-102">SOAP을 사용하여 Reporting Services 통합</span><span class="sxs-lookup"><span data-stu-id="5a2d5-102">Integrating Reporting Services Using SOAP</span></span>
  <span data-ttu-id="5a2d5-103">[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SOAP API는 사용자 지정 보고 솔루션을 개발 하기 위한 여러 웹 서비스 끝점을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="5a2d5-103">The [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SOAP API provides several Web service endpoints for developing custom reporting solutions.</span></span> <span data-ttu-id="5a2d5-104">엔드포인트는 현재 관리와 실행의 두 범주로 나누어집니다.</span><span class="sxs-lookup"><span data-stu-id="5a2d5-104">The endpoints currently fall into two categories: management and execution.</span></span> <span data-ttu-id="5a2d5-105">관리 기능은 <xref:ReportService2005>, <xref:ReportService2006> 및 <xref:ReportService2010> 엔드포인트를 통해 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="5a2d5-105">The management functionality is exposed through the <xref:ReportService2005>, <xref:ReportService2006>, and <xref:ReportService2010> endpoints.</span></span> <span data-ttu-id="5a2d5-106"><xref:ReportService2005> 엔드포인트는 기본 모드로 구성된 보고서 서버를 관리하는 데 사용되고, <xref:ReportService2006> 엔드포인트는 SharePoint 통합 모드에 대해 구성된 보고서 서버를 관리하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="5a2d5-106">The <xref:ReportService2005> endpoint is used for managing a report server that is configured in native mode and the <xref:ReportService2006> endpoint is used for managing a report server that is configured for SharePoint integrated mode.</span></span> <span data-ttu-id="5a2d5-107"><xref:ReportService2010>은 <xref:ReportService2005> 및 <xref:ReportService2006>의 기능을 병합하며, 기본 모드 또는 SharePoint 통합 모드용으로 구성된 보고서 서버를 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5a2d5-107">The <xref:ReportService2010> merges the functionalities of <xref:ReportService2005> and <xref:ReportService2006> and can manage a report server that is configured for either native or SharePoint integrated mode.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5a2d5-108"><xref:ReportService2005> 및 <xref:ReportService2006> 엔드포인트는 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]에서 더 이상 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5a2d5-108">The <xref:ReportService2005> and <xref:ReportService2006> endpoints are deprecated in [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)].</span></span> <span data-ttu-id="5a2d5-109"><xref:ReportService2010>엔드포인트에는 두 엔드포인트의 기능이 모두 포함되어 있으며 추가 관리 기능도 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5a2d5-109">The <xref:ReportService2010> endpoint includes the functionalities of both endpoints and contains additional management features.</span></span>  
  
 <span data-ttu-id="5a2d5-110">실행 기능은 <xref:ReportExecution2005> 엔드포인트를 통해 표시되며 보고서 서버가 기본 또는 SharePoint 통합 모드로 구성된 경우에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="5a2d5-110">The execution functionality is exposed through the <xref:ReportExecution2005> endpoint and it is used when the report server is configured in native or SharePoint integrated mode.</span></span> <span data-ttu-id="5a2d5-111">다음 항목에서는 이러한 엔드포인트를 사용하여 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows, SharePoint 및 웹 애플리케이션에서 보고 솔루션을 개발하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="5a2d5-111">The following topics show how these endpoints can be used for developing reporting solutions in [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows, SharePoint, and Web applications.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5a2d5-112">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="5a2d5-112">In This Section</span></span>  
 [<span data-ttu-id="5a2d5-113">Windows 애플리케이션에서 SOAP API 사용</span><span class="sxs-lookup"><span data-stu-id="5a2d5-113">Using the SOAP API in a Windows Application</span></span>](integrating-reporting-services-using-soap-windows-application.md)  
 <span data-ttu-id="5a2d5-114">SOAP API를 사용하여 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]를 Windows 환경에 통합하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="5a2d5-114">Describes how to use the SOAP API to integrate [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] into a Windows environment.</span></span>  
  
 [<span data-ttu-id="5a2d5-115">웹 애플리케이션에서 SOAP API 사용</span><span class="sxs-lookup"><span data-stu-id="5a2d5-115">Using the SOAP API in a Web Application</span></span>](integrating-reporting-services-using-soap-web-application.md)  
 <span data-ttu-id="5a2d5-116">SOAP API를 사용하여 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]를 웹 환경에 통합하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="5a2d5-116">Describes how to use the SOAP API to integrate [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] into a Web environment.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a2d5-117">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5a2d5-117">See Also</span></span>  
 <span data-ttu-id="5a2d5-118">[응용 프로그램에 Reporting Services 통합](../application-integration/integrating-reporting-services-into-applications.md) </span><span class="sxs-lookup"><span data-stu-id="5a2d5-118">[Integrating Reporting Services into Applications](../application-integration/integrating-reporting-services-into-applications.md) </span></span>  
 <span data-ttu-id="5a2d5-119">[보고서 서버 웹 서비스](../report-server-web-service/report-server-web-service.md) </span><span class="sxs-lookup"><span data-stu-id="5a2d5-119">[Report Server Web Service](../report-server-web-service/report-server-web-service.md) </span></span>  
 [<span data-ttu-id="5a2d5-120">웹 서비스와 .NET Framework를 사용하여 애플리케이션 빌드</span><span class="sxs-lookup"><span data-stu-id="5a2d5-120">Building Applications Using the Web Service and the .NET Framework</span></span>](../report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)  
  
  
