---
title: 개발자&#39;s 가이드 (Reporting Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- developer's guide [Reporting Services]
- Reporting Services, programming
- programming [Reporting Services]
ms.assetid: d8afa405-1012-4349-a72d-e10d94f8453d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: bcf880db543c891a0ffccab932fddc614df34e17
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734960"
---
# <a name="developer39s-guide-reporting-services"></a><span data-ttu-id="ef551-102">개발자&#39;s 가이드 (Reporting Services)</span><span class="sxs-lookup"><span data-stu-id="ef551-102">Developer&#39;s Guide (Reporting Services)</span></span>
  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="ef551-103">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]는 애플리케이션에서 활용할 수 있는 프로그래밍 인터페이스를 다수 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="ef551-103">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] offers several programming interfaces that you can leverage in your own applications.</span></span> <span data-ttu-id="ef551-104">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 의 기존 기능을 사용하여 웹 사이트와 Windows 애플리케이션에 사용자 지정 보고 및 관리 도구를 작성할 수 있으며 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 플랫폼을 확장할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ef551-104">You can use the existing features and capabilities of [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] to build custom reporting and management tools into Web sites and Windows applications, or you can extend the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] platform.</span></span>  
  
 <span data-ttu-id="ef551-105">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 플랫폼 확장에는 데이터 액세스, 보고서 배달 등에 사용할 수 있는 새 구성 요소 및 리소스를 만드는 작업이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="ef551-105">Extending the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] platform includes creating new components and resources that can be used for data access, report delivery and more.</span></span> <span data-ttu-id="ef551-106">조직에서 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 를 사용하는 회사를 대상으로 이러한 구성 요소 및 리소스를 마케팅할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ef551-106">You can market these components and resources to companies that are using [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] in their organization.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ef551-107">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="ef551-107">In This Section</span></span>  
 [<span data-ttu-id="ef551-108">애플리케이션에 Reporting Services 통합</span><span class="sxs-lookup"><span data-stu-id="ef551-108">Integrating Reporting Services into Applications</span></span>](application-integration/integrating-reporting-services-into-applications.md)  
 <span data-ttu-id="ef551-109">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 를 사용하여 사용자 지정 애플리케이션에 보고 기능을 통합하는 방법을 개략적으로 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="ef551-109">Provides an overview of how to use [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] to integrate reporting into custom applications.</span></span> <span data-ttu-id="ef551-110">보고서 서버에 액세스하기 위해 언제 직접 URL 액세스를 사용하고 언제 웹 서비스를 사용하는지를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="ef551-110">Describes when to use direct URL access and when to use the Web service to access the report server.</span></span>  
  
 [<span data-ttu-id="ef551-111">보고서 서버 웹 서비스</span><span class="sxs-lookup"><span data-stu-id="ef551-111">Report Server Web Service</span></span>](report-server-web-service/report-server-web-service.md)  
 <span data-ttu-id="ef551-112">보고서 서버 웹 서비스는 보고서 서버의 전체 기능에 대한 액세스를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="ef551-112">The Report Server Web service provides access to the full functionality of the report server.</span></span> <span data-ttu-id="ef551-113">웹 서비스는 HTTP를 통한 SOAP을 사용하며 클라이언트 프로그램과 보고서 서버 간의 통신 인터페이스 역할을 하도록 디자인되었습니다.</span><span class="sxs-lookup"><span data-stu-id="ef551-113">The Web service uses SOAP over HTTP and is designed to act as a communications interface between client programs and the report server.</span></span> <span data-ttu-id="ef551-114">웹 서비스 및 해당 메서드는 보고서 서버의 기능을 표시하며, 작업자는 이를 사용하여 관리부터 실행까지 보고서 수명 주기 중 임의의 부분에 대해 사용자 지정 도구를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ef551-114">The Web service and its methods expose the functionality of the report server and allow you to create custom tools for any part of the report life cycle, from management to execution.</span></span>  
  
 [<span data-ttu-id="ef551-115">URL 액세스&#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="ef551-115">URL Access &#40;SSRS&#41;</span></span>](url-access-ssrs.md)  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]<span data-ttu-id="ef551-116">는 보고서 탐색 및 보기를 위한 빠르고 쉬운 액세스 지점으로 사용할 수 있는 전체 URL 기반 요청 집합을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="ef551-116">supports a complete set of URL-based requests that you can use as a quick and easy access point for report navigation and viewing.</span></span> <span data-ttu-id="ef551-117">보고서 서버 웹 서비스와 함께 이 기술을 사용하여 전체 보고 솔루션을 사용자 지정 비즈니스 애플리케이션에 통합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ef551-117">You can use this technology in conjunction with the Report Server Web service to integrate a complete reporting solution into your custom business applications.</span></span> <span data-ttu-id="ef551-118">URL 액세스는 보고서를 웹 포털의 일부로 통합하거나 웹 브라우저에서 보고서를 볼 때 특히 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="ef551-118">URL access is particularly useful when integrating reports as part of a Web portal or when viewing reports from a Web browser.</span></span>  
  
 [<span data-ttu-id="ef551-119">Reporting Services 확장 프로그램</span><span class="sxs-lookup"><span data-stu-id="ef551-119">Reporting Services Extensions</span></span>](extensions/reporting-services-extensions.md)  
 <span data-ttu-id="ef551-120">확장성을 위해 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 의 모듈식 아키텍처를 디자인했습니다.</span><span class="sxs-lookup"><span data-stu-id="ef551-120">The modular architecture of [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] is designed for extensibility.</span></span> <span data-ttu-id="ef551-121">다양한 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 구성 요소에서 사용되는 확장 프로그램을 쉽게 개발, 설치 및 관리할 수 있도록 관리 코드 API를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ef551-121">A managed code API is available so that you can easily develop, install, and manage extensions consumed by many [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] components.</span></span> <span data-ttu-id="ef551-122">를 사용 하 여 어셈블리를 만들고 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 새로운 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 렌더링, 보안, 배달 및 데이터 처리 기능을 추가 하 여 변화 하는 비즈니스 요구를 충족할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ef551-122">You can create assemblies using the [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] and add new [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] rendering, security, delivery, and data processing functionality to meet your evolving business needs.</span></span>  
  
 [<span data-ttu-id="ef551-123">사용자 지정 보고서 항목</span><span class="sxs-lookup"><span data-stu-id="ef551-123">Custom Report Items</span></span>](custom-report-items/custom-report-items.md)  
 <span data-ttu-id="ef551-124">사용자 지정 보고서 항목을 만들어 RDL에 기능을 추가하거나 기존 컨트롤의 기능을 확장하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="ef551-124">Describes how to create Custom Report Items to add functionality to RDL or extend functionality of existing controls.</span></span>  
  
 [<span data-ttu-id="ef551-125">보고서에서 사용자 지정 어셈블리 사용</span><span class="sxs-lookup"><span data-stu-id="ef551-125">Using Custom Assemblies with Reports</span></span>](custom-assemblies/using-custom-assemblies-with-reports.md)  
 <span data-ttu-id="ef551-126">보고서 정의 내에 코드 참조를 포함시켜 보고서에 사용자 지정 어셈블리를 사용하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="ef551-126">Describes how to use custom assemblies with Reports by including code references within the report definition.</span></span>  
  
 [<span data-ttu-id="ef551-127">Reporting Services WMI 공급자 액세스</span><span class="sxs-lookup"><span data-stu-id="ef551-127">Access the Reporting Services WMI Provider</span></span>](tools/access-the-reporting-services-wmi-provider.md)  
 <span data-ttu-id="ef551-128">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] WMI 공급자를 사용하여 보고서 서버 배포를 관리하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="ef551-128">Describes how to use the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] WMI Provider to manage report server deployments.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef551-129">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ef551-129">See Also</span></span>  
 <span data-ttu-id="ef551-130">[SSRS를 &#40;Reporting Services&#41;](create-deploy-and-manage-mobile-and-paginated-reports.md) </span><span class="sxs-lookup"><span data-stu-id="ef551-130">[Reporting Services &#40;SSRS&#41;](create-deploy-and-manage-mobile-and-paginated-reports.md) </span></span>  
 <span data-ttu-id="ef551-131">[SSRS&#41;&#40;보고서 정의 언어](reports/report-definition-language-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="ef551-131">[Report Definition Language &#40;SSRS&#41;](reports/report-definition-language-ssrs.md) </span></span>  
 <span data-ttu-id="ef551-132">[SSRS&#41;&#40;기술 참조](technical-reference-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="ef551-132">[Technical Reference &#40;SSRS&#41;](technical-reference-ssrs.md) </span></span>  
 [<span data-ttu-id="ef551-133">안전한 개발&#40;Reporting Services&#41;</span><span class="sxs-lookup"><span data-stu-id="ef551-133">Secure Development &#40;Reporting Services&#41;</span></span>](extensions/secure-development/secure-development-reporting-services.md)  
  
  
