---
title: 웹 서비스 메서드 인수 제공 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- Report Server Web service, methods
- Web service [Reporting Services], methods
- methods [Reporting Services], arguments
- XML Web service [Reporting Services], methods
ms.assetid: f7b9ca05-fc4c-4b30-8e5d-172dd0f4a832
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3ef5188934628589751fe92d1839da0efb265766
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739213"
---
# <a name="supplying-web-service-method-arguments"></a><span data-ttu-id="1d51e-102">웹 서비스 메서드 인수 제공</span><span class="sxs-lookup"><span data-stu-id="1d51e-102">Supplying Web Service Method Arguments</span></span>
  <span data-ttu-id="1d51e-103">보고서 서버 웹 서비스 메서드는 HTTP를 통해 SOAP을 사용하여 주어진 URL에 있는 서비스에 요청을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="1d51e-103">A Report Server Web service method sends a request to the service at a given URL using SOAP over HTTP.</span></span> <span data-ttu-id="1d51e-104">서비스에서는 요청을 수신하고 처리한 다음 응답을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="1d51e-104">The service receives the request, processes it, and then returns a response.</span></span> <span data-ttu-id="1d51e-105">이러한 요청과 응답은 XML 문서 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="1d51e-105">These requests and responses are in the form of XML documents.</span></span>  
  
## <a name="optional-parameters"></a><span data-ttu-id="1d51e-106">선택적 매개 변수</span><span class="sxs-lookup"><span data-stu-id="1d51e-106">Optional Parameters</span></span>  
 <span data-ttu-id="1d51e-107">경우에 따라 웹 서비스 메서드에는 선택적인 입력 매개 변수가 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1d51e-107">In some cases, a Web service method can have optional input parameters.</span></span> <span data-ttu-id="1d51e-108">웹 서비스 메서드에 대한 입력 매개 변수가 선택 사항인 경우에도 해당 매개 변수를 포함시키고 매개 변수 값을 `null`([!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]의 경우 `Nothing`)로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1d51e-108">Even if an input parameter for a Web service method is optional, you must still include it and set the parameter value to `null` (`Nothing` in [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]).</span></span> <span data-ttu-id="1d51e-109">매개 변수 값을 `null`로 설정하면 SOAP 요청에서 해당 매개 변수에 대한 요소 값이 `null`로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="1d51e-109">Setting a parameter value to `null` sets the element value for that parameter in the SOAP request to `null`.</span></span>  
  
 <span data-ttu-id="1d51e-110">다음 예에서는 <xref:ReportService2010.ReportingService2010.CreateFolder%2A> 메서드를 사용하여 Sales 폴더에 Product Sales라는 새 폴더를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1d51e-110">The following example uses the <xref:ReportService2010.ReportingService2010.CreateFolder%2A> method to create a new folder named Product Sales in the Sales folder.</span></span> <span data-ttu-id="1d51e-111">폴더 속성에 대해 `null` 값을 제공하여 폴더에 대한 사용자별 속성을 제공하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1d51e-111">By supplying a `null` value for the folder properties, no user-specific properties are supplied for the folder:</span></span>  
  
```  
// C#  
rs.CreateFolder("Product Sales", "/Sales", null);  
```  
  
## <a name="complex-data-types"></a><span data-ttu-id="1d51e-112">복합 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="1d51e-112">Complex Data Types</span></span>  
 <span data-ttu-id="1d51e-113">보고서 웹 서비스의 핵심 클래스는 <xref:ReportService2010.ReportingService2010>이며, 이를 사용하여 프록시 클래스의 SOAP 작업 또는 웹 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="1d51e-113">The core class of the Report Server Web service is <xref:ReportService2010.ReportingService2010>, which you use to invoke the SOAP operations or Web methods of the proxy class.</span></span> <span data-ttu-id="1d51e-114">이 클래스와 해당 메서드를 지원하기 위해 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]에 웹 서비스 메서드의 입출력 매개 변수를 위한 특정 사용자 정의 복합 데이터 형식이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1d51e-114">To support this class and its methods, [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] includes user-defined, complex data types that are specific to the input and output parameters of the Web service methods.</span></span> <span data-ttu-id="1d51e-115">이러한 복합 데이터 형식은 생성 된 프록시 클래스의 일부 이며, 환경에서 개발할 때 사용할 수 있습니다 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="1d51e-115">These complex data types are part of the generated proxy class, which you can use when developing in the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] environment.</span></span>  
  
 <span data-ttu-id="1d51e-116">프록시 클래스를 생성하면 WSDL 파일에 정의된 복합 데이터 형식이 해당 프록시의 클래스에 의해 나타나며, 여기에는 복합 데이터 형식의 다양한 SOAP 요소에 해당하는 속성이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="1d51e-116">When you generate a proxy class, the complex data types that are defined in the WSDL file are represented by the classes of the proxy, which include properties that correspond to the various SOAP elements of the complex data types.</span></span> <span data-ttu-id="1d51e-117">이러한 데이터 형식의 시퀀스는 코드에서 열거할 수 있는 개체 배열이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1d51e-117">Sequences of these data types become arrays of objects that you can enumerate through in your code.</span></span> <span data-ttu-id="1d51e-118">그러면 SOAP 메시지로 전송된 XML 구조를 직접 사용하여 작업할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1d51e-118">This eliminates the need to work directly with the XML structures sent in SOAP messages.</span></span> <span data-ttu-id="1d51e-119">[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]에서 자동으로 변환이 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="1d51e-119">The [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] handles that translation for you.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d51e-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1d51e-120">See Also</span></span>  
 <span data-ttu-id="1d51e-121">[웹 서비스와 .NET Framework를 사용하여 애플리케이션 빌드](building-applications-using-the-web-service-and-the-net-framework.md) </span><span class="sxs-lookup"><span data-stu-id="1d51e-121">[Building Applications Using the Web Service and the .NET Framework](building-applications-using-the-web-service-and-the-net-framework.md) </span></span>  
 <span data-ttu-id="1d51e-122">[보고서 서버 웹 서비스](../report-server-web-service.md) </span><span class="sxs-lookup"><span data-stu-id="1d51e-122">[Report Server Web Service](../report-server-web-service.md) </span></span>  
 [<span data-ttu-id="1d51e-123">기술 참조&#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="1d51e-123">Technical Reference &#40;SSRS&#41;</span></span>](../../technical-reference-ssrs.md)  
  
  
