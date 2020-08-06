---
title: 웹 서비스 인증 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- Web service [Reporting Services], authentication
- XML Web service [Reporting Services], authentication
- Report Server Web service, authentication
ms.assetid: 852b4947-a090-4e54-8555-5a503945ceab
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 0c7836d6eba8c6ab3f0a8e705ebb79c7ed73eb17
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739202"
---
# <a name="web-service-authentication"></a><span data-ttu-id="40836-102">웹 서비스 인증</span><span class="sxs-lookup"><span data-stu-id="40836-102">Web Service Authentication</span></span>
  <span data-ttu-id="40836-103">Windows 인증 또는 기본 인증을 사용하여 보고서 서버 웹 서비스에 대한 호출을 인증할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40836-103">You can use either Windows Authentication or Basic authentication to authenticate the calls made to the Report Server Web service.</span></span> <span data-ttu-id="40836-104">보고서 서버에 SOAP 요청을 하는 클라이언트는 지원되는 인증 프로토콜 중 하나의 클라이언트 부분을 구현해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="40836-104">Any client that makes SOAP requests to the report server must implement the client portion of one of the supported authentication protocols.</span></span> <span data-ttu-id="40836-105">를 사용 하는 경우 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 관리 코드 HTTP 클래스를 사용 하 여 인증을 구현할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40836-105">If you are using the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], you can use the managed code HTTP classes to implement authentication.</span></span> <span data-ttu-id="40836-106">이러한 API를 사용하면 SOAP 요청과 함께 인증 정보를 쉽게 보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40836-106">Using these APIs makes it easy to send authentication information along with the SOAP requests.</span></span>  
  
 <span data-ttu-id="40836-107">보고서 서버 웹 서비스에 호출하기 전에 적절한 자격 증명이 없는 경우 호출이 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="40836-107">If you do not have appropriate credentials before you make a call to the Report Server Web service, the call fails.</span></span> <span data-ttu-id="40836-108">런타임에 해당 메서드를 호출하기 전에 웹 서비스를 나타내는 클라이언트 쪽 개체의 **Credentials** 속성을 설정하여 웹 서비스에 자격 증명을 전달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40836-108">At run time, you can pass credentials to the Web service by setting the **Credentials** property of the client-side object that represents the Web service before you call its methods.</span></span>  
  
 <span data-ttu-id="40836-109">다음 섹션에는 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]를 사용하여 자격 증명을 보내는 예제 코드가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40836-109">The following sections contain example code that sends credentials using the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].</span></span>  
  
## <a name="windows-authentication"></a><span data-ttu-id="40836-110">Windows 인증</span><span class="sxs-lookup"><span data-stu-id="40836-110">Windows Authentication</span></span>  
 <span data-ttu-id="40836-111">다음 코드는 Windows 자격 증명을 웹 서비스에 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="40836-111">The following code passes Windows credentials to the Web service.</span></span>  
  
```vb  
Dim rs As New ReportingService()  
rs.Credentials = System.Net.CredentialCache.DefaultCredentials  
```  
  
```csharp  
ReportingService rs = new ReportingService();  
rs.Credentials = System.Net.CredentialCache.DefaultCredentials;  
```  
  
## <a name="basic-authentication"></a><span data-ttu-id="40836-112">기본 인증</span><span class="sxs-lookup"><span data-stu-id="40836-112">Basic Authentication</span></span>  
 <span data-ttu-id="40836-113">다음 코드는 기본 자격 증명을 웹 서비스에 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="40836-113">The following code passes Basic credentials to the Web service.</span></span>  
  
```vb  
Dim rs As New ReportingService()  
rs.Credentials = New System.Net.NetworkCredential("username", "password", "domain")  
```  
  
```csharp  
ReportingService service = new ReportingService();  
service.Credentials = new System.Net.NetworkCredential("username", "password", "domain");  
```  
  
 <span data-ttu-id="40836-114">보고서 서버 웹 서비스의 메서드를 호출하기 전에 먼저 자격 증명을 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="40836-114">The credentials must be set before you call any of the methods of the Report Server Web service.</span></span> <span data-ttu-id="40836-115">자격 증명을 설정하지 않을 경우 오류 코드(HTTP 401 오류:액세스가 거부되었습니다.)를 받습니다.</span><span class="sxs-lookup"><span data-stu-id="40836-115">If you do not set the credentials, you receive the error code an HTTP 401 Error: Access Denied.</span></span> <span data-ttu-id="40836-116">서비스를 사용하기 전에 인증해야 하지만, 자격 증명을 설정한 후에는 동일한 서비스 변수(*rs* 등)를 계속 사용한다면 다시 설정할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="40836-116">You must authenticate the service before you use it, but after you have set the credentials, you do not need to set them again as long as you continue to use the same service variable (such as *rs*).</span></span>  
  
## <a name="custom-authentication"></a><span data-ttu-id="40836-117">사용자 지정 인증</span><span class="sxs-lookup"><span data-stu-id="40836-117">Custom Authentication</span></span>  
 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]<span data-ttu-id="40836-118">에는 개발자가 보안 확장 프로그램이라고 하는 사용자 지정 인증 확장 프로그램을 디자인하고 개발할 수 있도록 프로그래밍 API가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40836-118">includes a programming API that provides developers with the opportunity to design and develop custom authentication extensions, known as security extensions.</span></span> <span data-ttu-id="40836-119">자세한 내용은 [Implementing a Security Extension](../../extensions/security-extension/implementing-a-security-extension.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="40836-119">For more information, see [Implementing a Security Extension](../../extensions/security-extension/implementing-a-security-extension.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40836-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="40836-120">See Also</span></span>  
 <span data-ttu-id="40836-121">[웹 서비스와 .NET Framework를 사용하여 애플리케이션 빌드](building-applications-using-the-web-service-and-the-net-framework.md) </span><span class="sxs-lookup"><span data-stu-id="40836-121">[Building Applications Using the Web Service and the .NET Framework](building-applications-using-the-web-service-and-the-net-framework.md) </span></span>  
 [<span data-ttu-id="40836-122">보고서 서버 웹 서비스</span><span class="sxs-lookup"><span data-stu-id="40836-122">Report Server Web Service</span></span>](../report-server-web-service.md)  
  
  
