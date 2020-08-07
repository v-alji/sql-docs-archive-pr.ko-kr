---
title: Reporting Services의 예외 처리 소개 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- Web service [Reporting Services], exception handling
- errors [Reporting Services]
- exceptions [Reporting Services]
- Report Server Web service, exception handling
- XML Web service [Reporting Services], exception handling
ms.assetid: 54381870-ce67-482b-aa83-6a838cdbf9b9
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 091b1f40d293515617e369b750a5f18dfe12951b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731420"
---
# <a name="introducing-exception-handling-in-reporting-services"></a><span data-ttu-id="54dbb-102">Reporting Services의 예외 처리 소개</span><span class="sxs-lookup"><span data-stu-id="54dbb-102">Introducing Exception Handling in Reporting Services</span></span>
  <span data-ttu-id="54dbb-103">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 애플리케이션이 보고서 서버 웹 서비스에서 처리할 수 없는 요청을 보낼 경우 이 서비스는 SOAP 예외를 클라이언트에 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="54dbb-103">If your [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] application sends a request to the Report Server Web service that the service is unable to process, the service returns a SOAP exception to the client.</span></span> <span data-ttu-id="54dbb-104">보고서 서버 웹 서비스에서 throw된 예외에 대한 처리는 개발하는 애플리케이션에서 중요한 부분입니다. 이러한 처리를 통해 오류 발생 시 사용자에게 유용한 정보를 반환할 수 있기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="54dbb-104">Handling exceptions thrown by the Report Server Web service is an important part of the applications that you develop because you can return useful information to users when errors occur.</span></span>  
  
 <span data-ttu-id="54dbb-105">이 섹션에는 예외 처리, 유효하지 않은 사용자 입력 방지, 사용자에게 의미 있는 오류 정보 반환 등에 대한 정보가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54dbb-105">This section contains specific information about handling exceptions, preventing user input that is not valid, and returning meaningful error information to users.</span></span> <span data-ttu-id="54dbb-106">예외 처리에 대 한 일반적인 내용은 SDK 설명서의 "예외 처리 및 Throw"를 참조 하십시오 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="54dbb-106">For general information about exception handling, see "Handling and Throwing Exceptions" in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK documentation.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="54dbb-107">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="54dbb-107">In This Section</span></span>  
  
|<span data-ttu-id="54dbb-108">항목</span><span class="sxs-lookup"><span data-stu-id="54dbb-108">Topic</span></span>|<span data-ttu-id="54dbb-109">설명</span><span class="sxs-lookup"><span data-stu-id="54dbb-109">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="54dbb-110">Reporting Services의 예외 처리</span><span class="sxs-lookup"><span data-stu-id="54dbb-110">Handling Exceptions in Reporting Services</span></span>](handling-exceptions-in-reporting-services.md)|<span data-ttu-id="54dbb-111">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]에서의 예외에 대해 개략적으로 설명하고 웹 서비스 반환 오류에서 SOAP의 역할에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="54dbb-111">Provides an overview of exceptions in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] and the role of SOAP in returning errors from a Web service.</span></span>|  
|[<span data-ttu-id="54dbb-112">Reporting Services 예외 처리를 위한 최상의 방법</span><span class="sxs-lookup"><span data-stu-id="54dbb-112">Best Practices for Reporting Services Exception Handling</span></span>](best-practices/best-practices-for-reporting-services-exception-handling.md)|<span data-ttu-id="54dbb-113">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]에서 예외를 처리하는 방법에 대한 권장 사항을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="54dbb-113">Provides recommendations on how to handle exceptions in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span>|  
|[<span data-ttu-id="54dbb-114">Reporting Services SoapException 클래스</span><span class="sxs-lookup"><span data-stu-id="54dbb-114">Reporting Services SoapException Class</span></span>](soapexception-class/reporting-services-soapexception-class.md)|<span data-ttu-id="54dbb-115">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]의 **SoapException** 클래스에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="54dbb-115">Describes the **SoapException** class in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="54dbb-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="54dbb-116">See Also</span></span>  
 [<span data-ttu-id="54dbb-117">웹 서비스와 .NET Framework를 사용하여 애플리케이션 빌드</span><span class="sxs-lookup"><span data-stu-id="54dbb-117">Building Applications Using the Web Service and the .NET Framework</span></span>](../report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)  
  
  
