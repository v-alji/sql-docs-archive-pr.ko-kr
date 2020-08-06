---
title: SOAP API 액세스 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- XML Web service [Reporting Services], WSDL
- Web service [Reporting Services], SOAP
- calling Web service
- SOAP [Reporting Services], accessing
- Report Server Web service, SOAP
- Web service [Reporting Services], WSDL
- WSDL [Reporting Services]
- XML Web service [Reporting Services], SOAP
- Report Server Web service, WSDL
- referencing WSDL
ms.assetid: 63bb870a-4dbf-46bd-8921-78f8ebe5fd75
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 6e8a0c21bb53deff746cfd916b6ae2c96fa0de19
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659800"
---
# <a name="accessing-the-soap-api"></a><span data-ttu-id="9b137-102">SOAP API 액세스</span><span class="sxs-lookup"><span data-stu-id="9b137-102">Accessing the SOAP API</span></span>
  <span data-ttu-id="9b137-103">보고서 서버 웹 서비스는 HTTP를 통한 SOAP(Simple Object Access Protocol)을 사용하며 클라이언트 프로그램과 보고서 서버 간의 통신 인터페이스 역할을 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b137-103">The Report Server Web service uses Simple Object Access Protocol (SOAP) over HTTP and acts as a communications interface between client programs and the report server.</span></span> <span data-ttu-id="9b137-104">웹 서비스는 보고서 실행용과 보고서 관리용으로 엔드포인트를 두 개 제공하며 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]의 전체 기능에 액세스하는 데 사용할 수 있는 메서드 및 복합 형식 개체 집합으로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="9b137-104">The Web service provides two endpoints - one for report execution and one for report management - and consists of methods and a set of complex type objects that you can use to access the complete functionality of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="9b137-105">서비스를 호출하려면 Reporting Services WSDL(웹 서비스 기술 언어)을 참조해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b137-105">To call the service, you must reference the Reporting Services Web Services Description Language (WSDL).</span></span>  
  
## <a name="referencing-the-reporting-services-wsdl"></a><span data-ttu-id="9b137-106">Reporting Services WSDL 참조</span><span class="sxs-lookup"><span data-stu-id="9b137-106">Referencing the Reporting Services WSDL</span></span>  
 <span data-ttu-id="9b137-107">웹 서비스를 성공적으로 호출하려면 서비스에 액세스하는 방법, 서비스에서 지원하는 작업, 서비스에 필요한 매개 변수, 서비스에서 반환하는 내용 등에 대해 알고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b137-107">To call a Web service successfully, you must know how to access the service, what operations the service supports, what parameters the service expects, and what the service returns.</span></span> <span data-ttu-id="9b137-108">WSDL은 이러한 정보를 컴퓨터에서 읽거나 처리할 수 있는 XML 문서로 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="9b137-108">WSDL provides this information in an XML document that can be read or processed by a computer.</span></span>  
  
 <span data-ttu-id="9b137-109">보고서 서버 웹 서비스는 세 가지 엔드포인트로 표시되며,</span><span class="sxs-lookup"><span data-stu-id="9b137-109">The Report Server Web services are exposed in three different endpoints.</span></span> <span data-ttu-id="9b137-110">WSDL 파일의 이름은 각 엔드포인트에 대해 서로 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="9b137-110">The name of the WSDL file is different for each endpoint.</span></span> <span data-ttu-id="9b137-111"><xref:ReportService2010> 엔드포인트는 기본 모드 또는 SharePoint 통합 모드에서 보고서 서버의 개체를 관리하는 메서드를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="9b137-111">The <xref:ReportService2010> endpoint contains methods for managing objects in a Report Server in either native or SharePoint integrated mode.</span></span> <span data-ttu-id="9b137-112">이 엔드포인트에 대한 WSDL은 `ReportService2010.asmx?wsdl.`을 통해 액세스됩니다.</span><span class="sxs-lookup"><span data-stu-id="9b137-112">The WSDL for this endpoint is accessed through `ReportService2010.asmx?wsdl.`</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9b137-113"><xref:ReportService2005> 및 <xref:ReportService2006> 엔드포인트는 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]에서 더 이상 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9b137-113">The <xref:ReportService2005> and <xref:ReportService2006> endpoints are deprecated in [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)].</span></span> <span data-ttu-id="9b137-114"><xref:ReportService2010>엔드포인트에는 두 엔드포인트의 기능이 모두 포함되어 있으며 추가 관리 기능도 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9b137-114">The <xref:ReportService2010> endpoint includes the functionalities of both endpoints and contains additional management features.</span></span>  
  
-   <span data-ttu-id="9b137-115"><xref:ReportExecution2005> 엔드포인트를 통해 개발자는 보고서 서버의 보고서를 프로그래밍 방식으로 처리하고 렌더링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9b137-115">The <xref:ReportExecution2005> endpoint allows developers to programmatically process and render reports in a Report Server.</span></span> <span data-ttu-id="9b137-116">이 엔드포인트에 대한 WSDL은 `ReportExecution2005.asmx?wsdl`을 통해 액세스됩니다.</span><span class="sxs-lookup"><span data-stu-id="9b137-116">The WSDL for this endpoint is accessed through `ReportExecution2005.asmx?wsdl`.</span></span>  
  
 <span data-ttu-id="9b137-117">WSDL은 SDK와 같이 SOAP 및 웹 서비스를 지 원하는 개발 키트에서 사용할 수 있습니다 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="9b137-117">WSDL can be consumed by development kits that support SOAP and Web services, such as the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK.</span></span>  
  
 <span data-ttu-id="9b137-118">다음 예는 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 관리 WSDL 파일에 대한 URL의 형식을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="9b137-118">The following example shows the format of the URL to the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] management WSDL file:</span></span>  
  
```  
http://server/reportserver/ReportService2010.asmx?wsdl  
```  
  
 <span data-ttu-id="9b137-119">다음 표에서는 URL의 각 요소에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="9b137-119">The following table describes each element in the URL.</span></span>  
  
|<span data-ttu-id="9b137-120">URL 요소</span><span class="sxs-lookup"><span data-stu-id="9b137-120">URL element</span></span>|<span data-ttu-id="9b137-121">Description</span><span class="sxs-lookup"><span data-stu-id="9b137-121">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="9b137-122">*server*</span><span class="sxs-lookup"><span data-stu-id="9b137-122">*server*</span></span>|<span data-ttu-id="9b137-123">보고서 서버가 배포된 서버의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="9b137-123">The name of the server on which the report server is deployed.</span></span>|  
|<span data-ttu-id="9b137-124">*reportserver*</span><span class="sxs-lookup"><span data-stu-id="9b137-124">*reportserver*</span></span>|<span data-ttu-id="9b137-125">XML 웹 서비스가 포함된 폴더의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="9b137-125">The name of the folder that contains the XML Web service.</span></span> <span data-ttu-id="9b137-126">이 폴더는 설치 중 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="9b137-126">This is configured during setup.</span></span>|  
|<span data-ttu-id="9b137-127">*\<endpoint name>.asmx*</span><span class="sxs-lookup"><span data-stu-id="9b137-127">*\<endpoint name>.asmx*</span></span>|<span data-ttu-id="9b137-128">웹 서비스 엔드포인트의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="9b137-128">The name of the web service endpoint.</span></span>|  
  
 <span data-ttu-id="9b137-129">WSDL 형식에 대한 자세한 내용은 http://www.w3.org/TR/wsdl에서 W3C(World Wide Web 컨소시엄) WSDL 사양을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="9b137-129">For more information about the WSDL format, see the World Wide Web Consortium (W3C) WSDL specification at http://www.w3.org/TR/wsdl.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b137-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9b137-130">See Also</span></span>  
 <span data-ttu-id="9b137-131">[웹 서비스와 .NET Framework를 사용하여 애플리케이션 빌드](net-framework/building-applications-using-the-web-service-and-the-net-framework.md) </span><span class="sxs-lookup"><span data-stu-id="9b137-131">[Building Applications Using the Web Service and the .NET Framework](net-framework/building-applications-using-the-web-service-and-the-net-framework.md) </span></span>  
 [<span data-ttu-id="9b137-132">보고서 서버 웹 서비스</span><span class="sxs-lookup"><span data-stu-id="9b137-132">Report Server Web Service</span></span>](report-server-web-service.md)  
  
  
