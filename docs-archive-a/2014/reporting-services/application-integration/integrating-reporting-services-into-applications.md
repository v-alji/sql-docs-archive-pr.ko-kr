---
title: 애플리케이션에 Reporting Services 통합 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- integrating reports [Reporting Services]
- custom applications [SSRS]
- Reporting Services, application integration
- application integration [Reporting Services]
- reports [Reporting Services], integrating
ms.assetid: 49eb539c-d89b-4291-839a-0ec1a65cd270
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3ab92008c5beb4d931e8e781857d766bb56a1efd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639425"
---
# <a name="integrating-reporting-services-into-applications"></a><span data-ttu-id="39568-102">애플리케이션에 Reporting Services 통합</span><span class="sxs-lookup"><span data-stu-id="39568-102">Integrating Reporting Services into Applications</span></span>
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]<span data-ttu-id="39568-103">는 개발자에게 솔루션 개발을 위한 포괄적인 API 집합을 제공하도록 디자인된 개방형의 확장 가능한 보고 플랫폼입니다.</span><span class="sxs-lookup"><span data-stu-id="39568-103">is an open and extensible reporting platform designed to provide developers with a comprehensive set of APIs for developing solutions.</span></span>  
  
 <span data-ttu-id="39568-104">사용자 지정 응용 프로그램에 통합 하기 위한 세 가지 옵션이 있습니다 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . 보고서 서버 웹 서비스 (SOAP API 라고도 함), [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 용 ReportViewer 컨트롤 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsOrcas](../../includes/vsorcas-md.md)] , URL 액세스 등이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39568-104">There are three options for integrating [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] into custom applications: the Report Server Web service, also known as the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SOAP API, the ReportViewer controls for [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsOrcas](../../includes/vsorcas-md.md)], and URL access.</span></span> <span data-ttu-id="39568-105">각 옵션에서는 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]를 애플리케이션에 통합하기 위한 서로 다른 방법을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="39568-105">Each option provides a different approach for integrating [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] into your applications.</span></span>  
  
## <a name="report-server-web-service"></a><span data-ttu-id="39568-106">보고서 서버 웹 서비스</span><span class="sxs-lookup"><span data-stu-id="39568-106">Report Server Web Service</span></span>  
 <span data-ttu-id="39568-107">보고서 서버 웹 서비스는 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]에 대해 개발하기 위한 기본 인터페이스입니다.</span><span class="sxs-lookup"><span data-stu-id="39568-107">The Report Server Web service is the primary interface for developing against [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="39568-108">보고서 카탈로그를 관리할 코드를 개발하든 아니면 보고서를 지원되는 형식으로 렌더링하는 코드를 개발하는 경우이든 웹 서비스는 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]를 애플리케이션에 통합하는 데 필요한 모든 방법을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="39568-108">Whether you are developing code to manage your report catalog or developing code to render reports to a supported format, the Web service exposes all the necessary methods to integrate [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] into your applications.</span></span> <span data-ttu-id="39568-109">이러한 애플리케이션의 예는 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]에 포함되어 있는 보고서 관리자로서 여기서는 웹 서비스를 사용하여 보고서 서버 데이터베이스를 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="39568-109">An example of one such application is Report Manager, which is included with [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]; it uses the Web service to manage the report server database.</span></span>  
  
## <a name="reportviewer-controls-for-visual-studio"></a><span data-ttu-id="39568-110">Visual Studio용 ReportViewer 컨트롤</span><span class="sxs-lookup"><span data-stu-id="39568-110">ReportViewer Controls for Visual Studio</span></span>  
 <span data-ttu-id="39568-111">[!INCLUDE[vsOrcas](../../includes/vsorcas-md.md)]에 포함된 ReportViewer 컨트롤은 보고서 보기를 애플리케이션에 통합하는 데 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="39568-111">The ReportViewer controls included with [!INCLUDE[vsOrcas](../../includes/vsorcas-md.md)] are used for integrating report viewing into your applications.</span></span> <span data-ttu-id="39568-112">컨트롤에는 Windows Forms 기반 애플리케이션용과 Web Forms 애플리케이션용 두 가지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39568-112">There are two controls: one for Windows Forms-based applications and one for Web Forms applications.</span></span> <span data-ttu-id="39568-113">각 컨트롤은 보고서 서버에 배포된 보고서를 보기 위한 기능뿐만 아니라 보고서 서버가 설치되지 않은 환경에 있는 보고서를 렌더링하는 기능도 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="39568-113">Each control provides the capability for viewing reports that have been deployed to a report server as well as the ability to render reports that exist in an environment where a report server has not been installed.</span></span>  
  
## <a name="url-access"></a><span data-ttu-id="39568-114">URL 액세스</span><span class="sxs-lookup"><span data-stu-id="39568-114">URL Access</span></span>  
 <span data-ttu-id="39568-115">URL 액세스는 ReportViewer 컨트롤을 사용하지 않을 경우 보고서 보기를 애플리케이션에 통합하기 위한 또 다른 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="39568-115">URL access is another option for integrating report viewing into your applications if the ReportViewer controls are not an option.</span></span> <span data-ttu-id="39568-116">그 외에도 URL 액세스는 전자 메일을 통해 사용자에게 보고서에 대한 링크를 보내는 데도 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="39568-116">In addition, URL access is useful for sending links to reports to users via e-mail.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="39568-117">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="39568-117">In This Section</span></span>  
 [<span data-ttu-id="39568-118">SOAP을 사용하여 Reporting Services 통합</span><span class="sxs-lookup"><span data-stu-id="39568-118">Integrating Reporting Services Using SOAP</span></span>](../application-integration/integrating-reporting-services-using-soap.md)  
 <span data-ttu-id="39568-119">보고서 서버 웹 서비스를 사용하여 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 보고서 탐색 및 관리를 기존 비즈니스 애플리케이션에 통합하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="39568-119">Describes how to integrate [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] report navigation and management into your existing business applications using the Report Server Web service.</span></span>  
  
 [<span data-ttu-id="39568-120">ReportViewer 컨트롤을 사용하여 Reporting Services 통합</span><span class="sxs-lookup"><span data-stu-id="39568-120">Integrating Reporting Services Using the ReportViewer Controls</span></span>](../application-integration/integrating-reporting-services-using-reportviewer-controls.md)  
 <span data-ttu-id="39568-121">ReportViewer 컨트롤을 사용하여 보고서 보기를 기존 애플리케이션에 통합하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="39568-121">Describes how to integrate report viewing into your existing applications using the ReportViewer controls.</span></span>  
  
 [<span data-ttu-id="39568-122">URL 액세스를 사용하여 Reporting Services 통합</span><span class="sxs-lookup"><span data-stu-id="39568-122">Integrating Reporting Services Using URL Access</span></span>](../application-integration/integrating-reporting-services-using-url-access.md)  
 <span data-ttu-id="39568-123">URL 액세스를 사용하여 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 보고서 탐색을 기존 비즈니스 애플리케이션에 통합하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="39568-123">Describes how to integrate [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] report navigation into your existing business applications using URL access.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39568-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="39568-124">See Also</span></span>  
 <span data-ttu-id="39568-125">[보고서 관리자&#40;SSRS 기본 모드&#41;](../../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="39568-125">[Report Manager  &#40;SSRS Native Mode&#41;](../../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span></span>  
 <span data-ttu-id="39568-126">[URL 액세스와 SOAP 중에서 선택](../../../2014/reporting-services/application-integration/choosing-between-url-access-and-soap.md) </span><span class="sxs-lookup"><span data-stu-id="39568-126">[Choosing Between URL Access and SOAP](../../../2014/reporting-services/application-integration/choosing-between-url-access-and-soap.md) </span></span>  
 <span data-ttu-id="39568-127">[SSRS&#41;&#40;기술 참조](../../../2014/reporting-services/technical-reference-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="39568-127">[Technical Reference &#40;SSRS&#41;](../../../2014/reporting-services/technical-reference-ssrs.md) </span></span>  
 [<span data-ttu-id="39568-128">보고서 서버 웹 서비스</span><span class="sxs-lookup"><span data-stu-id="39568-128">Report Server Web Service</span></span>](../report-server-web-service/report-server-web-service.md)  
  
  
