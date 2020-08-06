---
title: 보고서 서버 웹 서비스 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- SSIS, Web service
- Web service [Reporting Services]
- Reporting Services, extending
- SQL Server Reporting Services, Web service
- Reporting Services, Web service
- XML Web service [Reporting Services]
- Report Server Web service
ms.assetid: 16c21dec-6b46-4497-9a0c-1b0f2b6ab8fc
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 8bb43a0fa52a243bd250f70fac16e18d949f8197
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650640"
---
# <a name="report-server-web-service"></a><span data-ttu-id="8b328-102">보고서 서버 웹 서비스</span><span class="sxs-lookup"><span data-stu-id="8b328-102">Report Server Web Service</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="8b328-103">보고서 서버 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 웹 서비스를 통해 보고서 서버의 전체 기능에 대 한 액세스를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b328-103">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] provides access to the full functionality of the report server through the Report Server Web service.</span></span> <span data-ttu-id="8b328-104">보고서 서버 웹 서비스는 SOAP API를 사용하는 XML 웹 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="8b328-104">The Report Server Web service is an XML Web service with a SOAP API.</span></span> <span data-ttu-id="8b328-105">HTTP를 통한 SOAP을 사용하고 클라이언트 프로그램과 보고서 서버 간의 통신 인터페이스로 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="8b328-105">It uses SOAP over HTTP and acts as a communications interface between client programs and the report server.</span></span> <span data-ttu-id="8b328-106">웹 서비스는 보고서 실행용과 보고서 관리용으로 엔드포인트를 두 개 제공하며, 여기에는 보고서 서버의 기능을 표시하고 보고서 수명 주기 중 임의의 부분에 대해 사용자 지정 도구를 만들 수 있는 메서드가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="8b328-106">The Web service provides two endpoints - one for report execution and one for report management - with methods that expose the functionality of the report server and enable you to create custom tools for any part of the report life cycle.</span></span>  
  
 <span data-ttu-id="8b328-107">웹 서비스를 기반으로 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 애플리케이션을 개발하는 데 기본적인 세 가지 방법이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8b328-107">There are three primary ways to develop [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] applications based on the Web service.</span></span> <span data-ttu-id="8b328-108">다음을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8b328-108">You can:</span></span>  
  
-   <span data-ttu-id="8b328-109">및 SDK를 사용 하 여 응용 프로그램을 개발 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b328-109">Develop applications using [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] and the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK.</span></span> <span data-ttu-id="8b328-110">[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]을(를) 사용하여 웹 서비스 애플리케이션 작성에 자세한 내용은 [웹 서비스 및 .NET Framework를 사용하여 애플리케이션 작성](../report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8b328-110">For more information about using the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] to build Web service applications, see [Building Applications Using the Web Service and the .NET Framework](../report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md).</span></span>  
  
-   <span data-ttu-id="8b328-111">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 스크립트 환경인 **rs** 유틸리티(RS.exe)를 사용하여 애플리케이션을 개발합니다.</span><span class="sxs-lookup"><span data-stu-id="8b328-111">Develop applications using the **rs** utility (RS.exe), the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] script environment.</span></span> <span data-ttu-id="8b328-112">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 및 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 스크립트를 사용하여 모든 보고서 서버 웹 서비스 작업을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8b328-112">With [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] and [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] scripts, you can run any of the Report Server Web service operations.</span></span> <span data-ttu-id="8b328-113">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]에서 스크립팅에 대한 자세한 내용은 [rs.exe 유틸리티 및 웹 서비스를 사용한 스크립팅](../tools/script-with-the-rs-exe-utility-and-the-web-service.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8b328-113">For more information about scripting in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], see [Script with the rs.exe Utility and the Web Service](../tools/script-with-the-rs-exe-utility-and-the-web-service.md).</span></span>  
  
-   <span data-ttu-id="8b328-114">SOAP 사용 개발 도구를 사용하여 애플리케이션을 개발합니다.</span><span class="sxs-lookup"><span data-stu-id="8b328-114">Develop applications using any SOAP-enabled set of development tools.</span></span> <span data-ttu-id="8b328-115">자세한 내용은 [Reporting Services에서 SOAP의 역할](../report-server-web-service/the-role-of-soap-in-reporting-services.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8b328-115">For more information, see [The Role of SOAP in Reporting Services](../report-server-web-service/the-role-of-soap-in-reporting-services.md).</span></span>  
  
## <a name="programming-diagram"></a><span data-ttu-id="8b328-116">프로그래밍 다이어그램</span><span class="sxs-lookup"><span data-stu-id="8b328-116">Programming Diagram</span></span>  
 <span data-ttu-id="8b328-117">![보고서 서버 웹 서비스 개발 옵션](../../../2014/reporting-services/media/reportserviceswebserviceprog-01.gif "보고서 서버 웹 서비스 개발 옵션")</span><span class="sxs-lookup"><span data-stu-id="8b328-117">![Report Server Web service development options](../../../2014/reporting-services/media/reportserviceswebserviceprog-01.gif "Report Server Web service development options")</span></span>  
<span data-ttu-id="8b328-118">Reporting Services 사용 가능한 웹 서비스 개발 옵션</span><span class="sxs-lookup"><span data-stu-id="8b328-118">Reporting Services available Web service development options</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8b328-119">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="8b328-119">In This Section</span></span>  
 [<span data-ttu-id="8b328-120">보고서 서버 웹 서비스 메서드</span><span class="sxs-lookup"><span data-stu-id="8b328-120">Report Server Web Service Methods</span></span>](../report-server-web-service/methods/report-server-web-service-methods.md)  
 <span data-ttu-id="8b328-121">각 보고서 서버 웹 서비스의 기능 및 메서드를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="8b328-121">Describes the features and methods of each Report Server Web service.</span></span>  
  
 [<span data-ttu-id="8b328-122">The Role of SOAP in Reporting Services</span><span class="sxs-lookup"><span data-stu-id="8b328-122">The Role of SOAP in Reporting Services</span></span>](../report-server-web-service/the-role-of-soap-in-reporting-services.md)  
 <span data-ttu-id="8b328-123">SOAP에 대한 개요를 제공하며 SOAP이 보고서 서버 웹 서비스에서 어떻게 사용되는지를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="8b328-123">Provides an overview of SOAP and how it is used in the Report Server Web services.</span></span>  
  
 [<span data-ttu-id="8b328-124">SOAP API 액세스</span><span class="sxs-lookup"><span data-stu-id="8b328-124">Accessing the SOAP API</span></span>](../report-server-web-service/accessing-the-soap-api.md)  
 <span data-ttu-id="8b328-125">WSDL(Web Service Description Language)에 대해 설명하고 Reporting Services WSDL 파일 액세스를 위한 URL을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="8b328-125">Describes the Web Service Description Language (WSDL) and provides URLs for accessing a Reporting Services WSDL file.</span></span>  
  
 [<span data-ttu-id="8b328-126">웹 서비스와 .NET Framework를 사용하여 애플리케이션 빌드</span><span class="sxs-lookup"><span data-stu-id="8b328-126">Building Applications Using the Web Service and the .NET Framework</span></span>](../report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)  
 <span data-ttu-id="8b328-127">Reporting Services SOAP API를 호출하는 애플리케이션 및 웹 서비스 개발에 대한 정보를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="8b328-127">Contains information about developing applications and Web services that call the Reporting Services SOAP API.</span></span>  
  
 [<span data-ttu-id="8b328-128">rs.exe 유틸리티 및 웹 서비스를 사용한 스크립팅</span><span class="sxs-lookup"><span data-stu-id="8b328-128">Script with the rs.exe Utility and the Web Service</span></span>](../tools/script-with-the-rs-exe-utility-and-the-web-service.md)  
 <span data-ttu-id="8b328-129">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 스크립팅 환경에 대해 개략적으로 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="8b328-129">Provides an overview of the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] scripting environment.</span></span>  
  
 [<span data-ttu-id="8b328-130">기술 참조&#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="8b328-130">Technical Reference &#40;SSRS&#41;</span></span>](../../../2014/reporting-services/technical-reference-ssrs.md)  
 <span data-ttu-id="8b328-131">보고서 서버 웹 서비스 메서드 및 해당하는 복합 형식에 대한 특정 참조 자료를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="8b328-131">Contains reference material specific to Report Server Web services methods and corresponding complex types.</span></span>  
  
## <a name="user-requirements-for-web-service-development"></a><span data-ttu-id="8b328-132">웹 서비스 개발을 위한 사용자 요구 사항</span><span class="sxs-lookup"><span data-stu-id="8b328-132">User Requirements for Web Service Development</span></span>  
 <span data-ttu-id="8b328-133">보고서 서버 웹 서비스를 사용하여 애플리케이션을 개발하려면 다음이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="8b328-133">To develop applications using the Report Server Web service, you need:</span></span>  
  
-   [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="8b328-134">Internet Explorer 5.5 이상이 설치되어 있고 인터넷으로 보고서 서버에 연결하여 액세스할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b328-134">Internet Explorer 5.5 or later installed on a computer with an Internet connection to and access to the report server.</span></span>  
  
-   [!INCLUDE[msCoName](../../includes/msconame-md.md)]<span data-ttu-id="8b328-135">[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] [!INCLUDE[msCoName](../../includes/msconame-md.md)] 또는 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]를 사용 하 여 응용 프로그램을 개발 하 고 배포 하려면 컴퓨터에 SDK가 설치 되어 있어야 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b328-135">[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] or the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK installed on a computer if you want to develop and deploy [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] applications using the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)].</span></span>  
  
-   <span data-ttu-id="8b328-136">기능 및 기능에 대해 자세히 알고 있어야 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b328-136">An in-depth understanding of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] features and capabilities.</span></span>  
  
-   <span data-ttu-id="8b328-137">SOAP 및 [!INCLUDE[vstecwebservices](../../includes/vstecwebservices-md.md)]를 잘 알고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b328-137">A firm understanding of SOAP and [!INCLUDE[vstecwebservices](../../includes/vstecwebservices-md.md)].</span></span>  
  
-   <span data-ttu-id="8b328-138">[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[csprcs](../../includes/csprcs-md.md)] [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 를 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 개발 플랫폼으로 사용 하려는 경우 또는과 같은 호환 언어의 개발 환경</span><span class="sxs-lookup"><span data-stu-id="8b328-138">Development experience in a [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]-compatible language such as [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[csprcs](../../includes/csprcs-md.md)] or [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)], if you plan to use the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] as your development platform.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b328-139">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8b328-139">See Also</span></span>  
 [<span data-ttu-id="8b328-140">보고서 서버 웹 서비스</span><span class="sxs-lookup"><span data-stu-id="8b328-140">Report Server Web Service</span></span>](../report-server-web-service/report-server-web-service.md)  
  
  
