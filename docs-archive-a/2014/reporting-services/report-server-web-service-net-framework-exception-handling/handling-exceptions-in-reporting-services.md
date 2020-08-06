---
title: Reporting Services의 예외 처리 | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- SOAP [Reporting Services], exceptions
- .NET Framework [Reporting Services]
- exceptions [Reporting Services], about exception handling
- SoapException object
ms.assetid: 1a443432-2db5-48c5-bc29-433b4688082f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 1d887853b475f7b4d673d7b04343ae9bc71644d3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735003"
---
# <a name="handling-exceptions-in-reporting-services"></a><span data-ttu-id="8195f-102">Reporting Services의 예외 처리</span><span class="sxs-lookup"><span data-stu-id="8195f-102">Handling Exceptions in Reporting Services</span></span>
  <span data-ttu-id="8195f-103">Reporting Services SOAP API 클라이언트 요청을 완료할 수 없는 경우 보고서 서버에서는 호출에 대해 예상된 결과가 아니라 오류를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="8195f-103">When a Reporting Services SOAP API client request cannot be completed, the report server returns an error rather than the expected results of the call.</span></span> <span data-ttu-id="8195f-104">호출을 완료할 수 없는 경우 보고서 서버 웹 서비스에 대한 오류가 SOAP **Fault** XML 요소로 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="8195f-104">When a call cannot complete, an error for the Report Server Web service is returned as a SOAP **Fault** XML element.</span></span> <span data-ttu-id="8195f-105">오류의 주요 설명 요소는 보고서 서버에서 제공하는 모든 오류 정보와 추가 웹 서비스 오류 정보를 포함하는 **detail** 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="8195f-105">The key descriptive element of the fault is the **detail** element, which includes all of the error information provided by the report server as well as any additional Web service error information.</span></span> <span data-ttu-id="8195f-106">**detail** 요소의 주요 정보는 보고서 서버 오류 코드입니다.</span><span class="sxs-lookup"><span data-stu-id="8195f-106">The key information in the **detail** element is the report server error code.</span></span> <span data-ttu-id="8195f-107">메시지 및 오류 코드를 기준으로 애플리케이션에서 수행할 적절한 다음 동작을 결정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8195f-107">Based on the message and error code, you can determine the next appropriate action to take in your applications.</span></span> <span data-ttu-id="8195f-108">SOAP 오류에 대한 자세한 내용은 W3C(World Wide Web 컨소시엄) 웹 사이트 http://www.w3.org/TR/SOAP을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="8195f-108">For more information about SOAP faults, see the World Wide Web Consortium (W3C) Web site at http://www.w3.org/TR/SOAP.</span></span>  
  
## <a name="soap-faults-and-the-net-framework"></a><span data-ttu-id="8195f-109">SOAP 오류 및 .NET Framework</span><span class="sxs-lookup"><span data-stu-id="8195f-109">SOAP Faults and the .NET Framework</span></span>  
 <span data-ttu-id="8195f-110">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]에서 웹 서비스에 대한 클라이언트 요청에 오류가 발생할 경우 보고서 서버에서 **SoapException** 개체를 throw하여 웹 서비스를 호출하는 클라이언트 코드에 오류를 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="8195f-110">In the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], if an error occurs in a client request to the Web service, the report server communicates the error to the client code that calls the Web service by throwing a **SoapException** object.</span></span> <span data-ttu-id="8195f-111">**SoapException**은 SOAP 오류에 포함된 정보를 래핑합니다.</span><span class="sxs-lookup"><span data-stu-id="8195f-111">The **SoapException** wraps the information contained in a SOAP fault.</span></span> <span data-ttu-id="8195f-112">**SoapException**의 **Detail** 속성은 SOAP 오류의 **detail** 요소에 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="8195f-112">The **Detail** property of the **SoapException** maps to the **detail** element in the SOAP fault.</span></span> <span data-ttu-id="8195f-113">애플리케이션에서는 try/catch 블록으로 **SoapException** 개체를 catch하고 **SoapException**의 **Detail** 속성을 사용하여 올바른 조치를 취해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8195f-113">Applications should catch the **SoapException** object with a try/catch block and use the **Detail** property of the **SoapException** to take appropriate action.</span></span> <span data-ttu-id="8195f-114">**SoapException** 클래스 및 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]의 **Detail** 속성에 대한 자세한 내용은 [Reporting Services SoapException 클래스](soapexception-class/reporting-services-soapexception-class.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8195f-114">For more information about the **SoapException** class and the **Detail** property in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], see [Reporting Services SoapException Class](soapexception-class/reporting-services-soapexception-class.md).</span></span> <span data-ttu-id="8195f-115">**SoapException** 클래스에 대한 자세한 내용은 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK 설명서를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8195f-115">For more information about the **SoapException** class, see the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8195f-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8195f-116">See Also</span></span>  
 <span data-ttu-id="8195f-117">[Detail 속성](soapexception-class/detail-property.md) </span><span class="sxs-lookup"><span data-stu-id="8195f-117">[Detail Property](soapexception-class/detail-property.md) </span></span>  
 <span data-ttu-id="8195f-118">[Reporting Services에서 예외 처리 소개](introducing-exception-handling-in-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="8195f-118">[Introducing Exception Handling in Reporting Services](introducing-exception-handling-in-reporting-services.md) </span></span>  
 [<span data-ttu-id="8195f-119">Reporting Services SoapException 클래스</span><span class="sxs-lookup"><span data-stu-id="8195f-119">Reporting Services SoapException Class</span></span>](soapexception-class/reporting-services-soapexception-class.md)  
  
  
