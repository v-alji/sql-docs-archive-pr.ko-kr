---
title: Reporting Services에서 SOAP의 역할 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- Web service [Reporting Services], SOAP
- SOAP [Reporting Services], role in Reporting Services
- Report Server Web service, SOAP
- XML Web service [Reporting Services], SOAP
ms.assetid: f229c3ef-f2ca-448f-98f1-b8df350b9992
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 05445eb1c95c5761595944867b6d0c20a6f1a412
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732416"
---
# <a name="the-role-of-soap-in-reporting-services"></a><span data-ttu-id="d445d-102">The Role of SOAP in Reporting Services</span><span class="sxs-lookup"><span data-stu-id="d445d-102">The Role of SOAP in Reporting Services</span></span>
  <span data-ttu-id="d445d-103">웹 서버 웹 서비스에서는 SOAP(Simple Object Access Protocol) 메시징을 사용하여 네트워크를 통해 텍스트 기반 명령을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="d445d-103">The Report Server Web service uses Simple Object Access Protocol (SOAP) messaging to send text-based commands over a network.</span></span> <span data-ttu-id="d445d-104">이러한 명령은 HTTP를 사용하여 World Wide Web을 통해 전송되는 XML 텍스트 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="d445d-104">These commands take the form of XML text that is sent over the World Wide Web using HTTP.</span></span> <span data-ttu-id="d445d-105">SOAP을 통신 프로토콜로 사용하면 보고서 서버 웹 서비스에서는 폭넓게 활용되는 개방형 인프라를 사용하여 애플리케이션 및 구성 요소와 보고서 서버 간에 데이터 교환이 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="d445d-105">By using SOAP as its communication protocol, the Report Server Web service allows applications and components to exchange data with the report server using an open and widely accepted infrastructure.</span></span> <span data-ttu-id="d445d-106">SOAP 표준은 www.w3.org/TR/SOAP에 정의되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d445d-106">The SOAP standard is defined at www.w3.org/TR/SOAP.</span></span>  
  
 <span data-ttu-id="d445d-107">SOAP을 인식하고 SOAP 요청을 보낼 수 있으면 모든 클라이언트 애플리케이션이 SOAP 클라이언트가 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d445d-107">Any client application can act as a SOAP client as long as it is SOAP-aware and can send SOAP requests.</span></span> <span data-ttu-id="d445d-108">보고서 관리자는 이러한 SOAP 클라이언트 중 하나이며</span><span class="sxs-lookup"><span data-stu-id="d445d-108">Report Manager is one such SOAP client.</span></span> <span data-ttu-id="d445d-109">모든 보고서 및 보고서 관련 내용이 저장되는 보고서 서버 데이터베이스에 대한 인터페이스를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="d445d-109">It provides an interface to the report server database in which all reports and report-related content is stored.</span></span> <span data-ttu-id="d445d-110">최종 사용자는 이 애플리케이션을 사용하여 보고서 서버 네임스페이스에서 보고서 및 폴더를 탐색하고 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d445d-110">End users can use the application to browse through and manage reports and folders in the report server namespace.</span></span> <span data-ttu-id="d445d-111">보고서 관리자는 보고서 서버 웹 서비스 인프라를 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="d445d-111">Report Manager is built on the Report Server Web service infrastructure.</span></span>  
  
 <span data-ttu-id="d445d-112">보고서 서버는 SOAP 서버의 역할을 하며, SOAP 클라이언트로부터 요청을 수신하고 적절한 응답을 만들 수 있는 SOAP 인식 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="d445d-112">A report server acts as a SOAP server, a SOAP-aware service that can accept requests from SOAP clients and create appropriate responses.</span></span> <span data-ttu-id="d445d-113">서버에서는 요청을 처리하고 인코딩된 응답을 다시 클라이언트로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="d445d-113">The server handles the requests and sends encoded responses back to the client.</span></span>  
  
 <span data-ttu-id="d445d-114">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]의 SOAP 메시지의 형태는 클라이언트의 요청 유형에 따라 다양합니다.</span><span class="sxs-lookup"><span data-stu-id="d445d-114">SOAP messages in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] take many different forms, depending on the type of request made by the client.</span></span> <span data-ttu-id="d445d-115">다음 예는 보고서 서버 데이터베이스에서 항목을 제거하는 간단한 SOAP 클라이언트 요청을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="d445d-115">The following example represents a simple SOAP client request to remove an item from the report server database.</span></span>  
  
```  
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
    <soap:Body>  
        <DeleteItem xmlns="https://www.microsoft.com/sql/ReportingServer">  
            <item>/Samples/Report1</item>  
        </DeleteItem>  
    </soap:Body>  
</soap:Envelope>  
```  
  
 <span data-ttu-id="d445d-116">SOAP 자체의 경우 전체 메시지를 `Envelope` 요소 내에 두며 메시지 중 많은 부분을 `Body` 요소에 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="d445d-116">The SOAP itself requires that messages be put into an `Envelope` element, with the bulk of the message inside a `Body` element.</span></span> <span data-ttu-id="d445d-117">이 예에서 본문에는 삭제할 항목의 경로를 나타내는 문자열 매개 변수를 가지는 <xref:ReportService2010.ReportingService2010.DeleteItem%2A> 메서드 호출이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d445d-117">In this example, the body contains a call to the <xref:ReportService2010.ReportingService2010.DeleteItem%2A> method, which takes a string parameter representing the path of the item to delete.</span></span> <span data-ttu-id="d445d-118">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 모든 SOAP 작업을 메서드로 캡슐화 하는 클라이언트 프록시 클래스를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d445d-118">You can create a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] client proxy class that encapsulates all SOAP operations into methods.</span></span> <span data-ttu-id="d445d-119">다음 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[csprcs](../../includes/csprcs-md.md)] 메서드는 이전에 제공 된 SOAP 예제를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="d445d-119">The following [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[csprcs](../../includes/csprcs-md.md)] method represents the SOAP example given earlier.</span></span>  
  
```  
public void DeleteItem(string item);  
```  
  
 <span data-ttu-id="d445d-120">서버의 응답은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="d445d-120">The response from the server might look like the following:</span></span>  
  
```  
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
    <soap:Body>  
        <DeleteItemResponse xmlns="https://www.microsoft.com/sql/ReportingServer" />  
    </soap:Body>  
</soap:Envelope>  
```  
  
 <span data-ttu-id="d445d-121"><xref:ReportService2010.ReportingService2010.DeleteItem%2A> 메서드에는 반환 값이 없으므로 빈 응답이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="d445d-121">The <xref:ReportService2010.ReportingService2010.DeleteItem%2A> method has no return value, so an empty response is returned.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d445d-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d445d-122">See Also</span></span>  
 <span data-ttu-id="d445d-123">[SOAP API 액세스](accessing-the-soap-api.md) </span><span class="sxs-lookup"><span data-stu-id="d445d-123">[Accessing the SOAP API](accessing-the-soap-api.md) </span></span>  
 <span data-ttu-id="d445d-124">[보고서 관리자&#40;SSRS 기본 모드&#41;](../report-manager-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="d445d-124">[Report Manager  &#40;SSRS Native Mode&#41;](../report-manager-ssrs-native-mode.md) </span></span>  
 <span data-ttu-id="d445d-125">[Reporting Services 보고서 서버](../reporting-services-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="d445d-125">[Reporting Services Report Server](../reporting-services-report-server.md) </span></span>  
 [<span data-ttu-id="d445d-126">보고서 서버 웹 서비스</span><span class="sxs-lookup"><span data-stu-id="d445d-126">Report Server Web Service</span></span>](report-server-web-service.md)  
  
  
