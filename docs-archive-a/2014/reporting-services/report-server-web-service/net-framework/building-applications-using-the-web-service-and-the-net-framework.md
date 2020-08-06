---
title: 웹 서비스 및 .NET Framework를 사용하여 애플리케이션 작성 | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- Report Server Web service, application building
- .NET Framework [Reporting Services]
- XML Web service [Reporting Services], client creation
- reports [Reporting Services], building
- Web service [Reporting Services], application building
- Report Server Web service, client creation
- client configuration [Reporting Services]
- XML Web service [Reporting Services], application building
- Web service [Reporting Services], client creation
ms.assetid: 92a9678c-bc4f-4d7a-ba44-85989bfe27ca
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 5f14a0f2d231d54d12129852b6226c02afd211d4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730140"
---
# <a name="building-applications-using-the-web-service-and-the-net-framework"></a><span data-ttu-id="61e96-102">웹 서비스 및 .NET Framework를 사용하여 애플리케이션 작성</span><span class="sxs-lookup"><span data-stu-id="61e96-102">Building Applications Using the Web Service and the .NET Framework</span></span>
  <span data-ttu-id="61e96-103">를 사용 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 하면 메서드, 기본 형식 및 사용자 정의 복합 형식과 같은 익숙한 프로그래밍 구문을 사용 하 여 웹 서비스 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="61e96-103">With the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], you can use familiar programming constructs, such as methods, primitive types, and user-defined complex types to work with Web services.</span></span> <span data-ttu-id="61e96-104">[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]에는 모든 W3C(World Wide Web 컨소시엄) 표준 호환 웹 서비스를 호출할 수 있는 웹 서비스 클라이언트를 만드는 데 사용할 수 있는 인프라와 도구가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="61e96-104">The [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] contains an infrastructure and tools you can use to create Web service clients that can call any World Wide Web Consortium (W3C) standards-compliant Web service.</span></span>  
  
 <span data-ttu-id="61e96-105">보고서 서버 웹 서비스 클라이언트는 SOAP(Simple Object Access Protocol) 메시지를 사용하여 보고서 서버와 통신하는 구성 요소 또는 애플리케이션입니다.</span><span class="sxs-lookup"><span data-stu-id="61e96-105">A Report Server Web service client is any component or application that communicates with a report server using Simple Object Access Protocol (SOAP) messages.</span></span>  
  
 <span data-ttu-id="61e96-106">**.NET Framework를 사용하여 보고서 서버 웹 서비스 클라이언트를 만들려면 다음 기본 단계를 수행하십시오.**</span><span class="sxs-lookup"><span data-stu-id="61e96-106">**To create a Report Server Web service client using the .NET Framework, follow these basic steps:**</span></span>  
  
1.  <span data-ttu-id="61e96-107">웹 서비스에 대한 프록시 클래스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="61e96-107">Create a proxy class for the Web service.</span></span>  
  
     <span data-ttu-id="61e96-108">이 작업을 수행하려면 프록시 클래스 또는 웹 참조를 개발 프로젝트에 추가하고 클라이언트 코드에서 프록시 클래스를 참조한 다음 해당 프록시의 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="61e96-108">To do this, add a proxy class or Web reference to your development project, reference the proxy class in your client code, and create an instance of that proxy.</span></span> <span data-ttu-id="61e96-109">자세한 내용은 [웹 서비스 프록시 만들기](creating-the-web-service-proxy.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="61e96-109">For more information, see [Creating the Web Service Proxy](creating-the-web-service-proxy.md).</span></span>  
  
2.  <span data-ttu-id="61e96-110">보고서 서버에서 웹 서비스 클라이언트를 인증합니다.</span><span class="sxs-lookup"><span data-stu-id="61e96-110">Authenticate the Web service client with the report server.</span></span>  
  
     <span data-ttu-id="61e96-111">이 작업을 수행하려면 서비스 개체의 <xref:System.Web.Services.Protocols.WebClientProtocol.Credentials%2A> 속성을 보고서 서버에서 인증된 사용자의 자격 증명과 동일하게 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="61e96-111">To do this, set the service object's <xref:System.Web.Services.Protocols.WebClientProtocol.Credentials%2A> property equal to the credentials of an authenticated user on the report server.</span></span> <span data-ttu-id="61e96-112">자세한 내용은 [웹 서비스 인증](web-service-authentication.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="61e96-112">For more information, see [Web Service Authentication](web-service-authentication.md).</span></span>  
  
3.  <span data-ttu-id="61e96-113">호출하려는 웹 서비스 작업과 일치하는 프록시 클래스의 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="61e96-113">Call the method of the proxy class corresponding to the Web service operation that you want to invoke.</span></span>  
  
     <span data-ttu-id="61e96-114">이 작업을 수행하려면 웹 서비스 메서드를 호출하고 필요한 인수를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="61e96-114">To do this, call a Web service method and supply the necessary arguments.</span></span> <span data-ttu-id="61e96-115">웹 서비스 메서드에 대한 자세한 내용은 [보고서 서버 웹 서비스 메서드](../methods/report-server-web-service-methods.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="61e96-115">For more information about the Web service methods, see [Report Server Web Service Methods](../methods/report-server-web-service-methods.md).</span></span> <span data-ttu-id="61e96-116">호출에 대한 자세한 내용은 [웹 서비스 메서드 호출](calling-web-service-methods.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="61e96-116">For more information about calling, see [Calling Web Service Methods](calling-web-service-methods.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="61e96-117">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="61e96-117">In This Section</span></span>  
  
|<span data-ttu-id="61e96-118">항목</span><span class="sxs-lookup"><span data-stu-id="61e96-118">Topic</span></span>|<span data-ttu-id="61e96-119">Description</span><span class="sxs-lookup"><span data-stu-id="61e96-119">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="61e96-120">웹 서비스 프록시 만들기</span><span class="sxs-lookup"><span data-stu-id="61e96-120">Creating the Web Service Proxy</span></span>](creating-the-web-service-proxy.md)|<span data-ttu-id="61e96-121">를 사용 하 여 프로젝트에 프록시 클래스를 추가 하는 방법을 설명 합니다 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="61e96-121">Describes the ways to add a proxy class to your project using [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].</span></span>|  
|[<span data-ttu-id="61e96-122">웹 서비스 인증</span><span class="sxs-lookup"><span data-stu-id="61e96-122">Web Service Authentication</span></span>](web-service-authentication.md)|<span data-ttu-id="61e96-123">보고서 서버 웹 서비스에 대한 호출의 인증 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="61e96-123">Describes how calls to the Report Server Web service are authenticated.</span></span>|  
|[<span data-ttu-id="61e96-124">웹 서비스 메서드 호출</span><span class="sxs-lookup"><span data-stu-id="61e96-124">Calling Web Service Methods</span></span>](calling-web-service-methods.md)|<span data-ttu-id="61e96-125">에서 SOAP API를 사용 하 여 웹 서비스 메서드를 호출 하는 방법을 설명 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="61e96-125">Describes how to use the SOAP API to call Web service methods in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].</span></span>|  
|[<span data-ttu-id="61e96-126">웹 서비스의 URL 속성 설정</span><span class="sxs-lookup"><span data-stu-id="61e96-126">Setting the Url Property of the Web Service</span></span>](setting-the-url-property-of-the-web-service.md)|<span data-ttu-id="61e96-127">웹 참조를 만든 다음 프로그래밍 방식으로 웹 서비스 프록시를 새 서버 URL에 지정하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="61e96-127">Explains how to programmatically direct your Web service proxy to a new server URL after you have created your Web reference.</span></span>|  
|[<span data-ttu-id="61e96-128">웹 서비스 메서드 인수 제공</span><span class="sxs-lookup"><span data-stu-id="61e96-128">Supplying Web Service Method Arguments</span></span>](supplying-web-service-method-arguments.md)|<span data-ttu-id="61e96-129">웹 서비스 메서드를 호출하고 메서드 인수를 제공하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="61e96-129">Describes how to invoke a Web service method and supply method arguments.</span></span>|  
|[<span data-ttu-id="61e96-130">선택적 웹 서비스 개체에 대한 값 생략</span><span class="sxs-lookup"><span data-stu-id="61e96-130">Omitting Values for Optional Web Service Objects</span></span>](omitting-values-for-optional-web-service-objects.md)|<span data-ttu-id="61e96-131">선택적 웹 서비스 개체에 대한 값을 생략하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="61e96-131">Describes how to omit values for optional Web service objects.</span></span>|  
|[<span data-ttu-id="61e96-132">보안 웹 서비스 메서드 사용</span><span class="sxs-lookup"><span data-stu-id="61e96-132">Using Secure Web Service Methods</span></span>](using-secure-web-service-methods.md)|<span data-ttu-id="61e96-133">**SecureConnectionLevel** 설정 및 이러한 설정이 Reporting Services SOAP API의 사용에 영향을 미치는 방식에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="61e96-133">Describes the **SecureConnectionLevel** setting and the way in which it affects the use of the Reporting Services SOAP API.</span></span>|  
|[<span data-ttu-id="61e96-134">디바이스 정보 설정을 렌더링 확장 프로그램에 전달</span><span class="sxs-lookup"><span data-stu-id="61e96-134">Passing Device Information Settings to Rendering Extensions</span></span>](passing-device-information-settings-to-rendering-extensions.md)|<span data-ttu-id="61e96-135">보고서를 다양한 형식으로 렌더링하는 데 사용되는 디바이스 정보 설정을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="61e96-135">Describes the device information settings that are used to render reports to different formats.</span></span>|  
|[<span data-ttu-id="61e96-136">Reporting Services 배달 확장 프로그램 설정</span><span class="sxs-lookup"><span data-stu-id="61e96-136">Reporting Services Delivery Extension Settings</span></span>](reporting-services-delivery-extension-settings.md)|<span data-ttu-id="61e96-137">보고서 서버 전자 메일을 사용하여 보고서를 배달하는 데 사용되는 설정을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="61e96-137">Describes the settings that are used to deliver reports using report server e-mail.</span></span>|  
|[<span data-ttu-id="61e96-138">Reporting Services SOAP 헤더 사용</span><span class="sxs-lookup"><span data-stu-id="61e96-138">Using Reporting Services SOAP Headers</span></span>](../../report-server-web-service-net-framework-soap-headers/using-reporting-services-soap-headers.md)|<span data-ttu-id="61e96-139">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]에서 SOAP 헤더의 사용에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="61e96-139">Explains the use of SOAP headers in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span>|  
|[<span data-ttu-id="61e96-140">Reporting Services의 예외 처리 소개</span><span class="sxs-lookup"><span data-stu-id="61e96-140">Introducing Exception Handling in Reporting Services</span></span>](../../report-server-web-service-net-framework-exception-handling/introducing-exception-handling-in-reporting-services.md)|<span data-ttu-id="61e96-141">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]에서 오류를 처리하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="61e96-141">Provides information about the way in which [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] handles errors.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="61e96-142">참고 항목</span><span class="sxs-lookup"><span data-stu-id="61e96-142">See Also</span></span>  
 <span data-ttu-id="61e96-143">[보고서 서버 웹 서비스](../report-server-web-service.md) </span><span class="sxs-lookup"><span data-stu-id="61e96-143">[Report Server Web Service](../report-server-web-service.md) </span></span>  
 [<span data-ttu-id="61e96-144">기술 참조&#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="61e96-144">Technical Reference &#40;SSRS&#41;</span></span>](../../technical-reference-ssrs.md)  
  
  
