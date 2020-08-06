---
title: Reporting Services 스크립트 파일 형식 지정 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- scripts [Reporting Services], formats
- formats [Reporting Services], script files
ms.assetid: 85a207dd-4e0f-4d40-a41e-0c75f65d719c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c98a2f6561c3242fec34f7ca11c8304286ccebae
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732359"
---
# <a name="format-a-reporting-services-script-file"></a><span data-ttu-id="febd8-102">Reporting Services 스크립트 파일 형식 지정</span><span class="sxs-lookup"><span data-stu-id="febd8-102">Format a Reporting Services Script File</span></span>
  <span data-ttu-id="febd8-103">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 스크립트는 WSDL(Web Service Description Language)을 기반으로 하는 프록시에 대해 작성된 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic .NET 코드 파일로, Reporting Services SOAP API를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="febd8-103">A [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] script is a [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic .NET code file, written against a proxy that is built on Web Service Description Language (WSDL), which defines the Reporting Services SOAP API.</span></span> <span data-ttu-id="febd8-104">스크립트 파일은 확장명이 .rss인 유니코드 또는 UTF-8 텍스트 파일로 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="febd8-104">A script file is stored as a Unicode or UTF-8 text file with the extension .rss.</span></span>  
  
 <span data-ttu-id="febd8-105">이 스크립트 파일은 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 모듈로 사용되며 사용자 정의 프로시저 및 모듈 수준 변수를 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="febd8-105">The script file acts as a [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] module and can contain user-defined procedures and module-level variables.</span></span> <span data-ttu-id="febd8-106">스크립트 파일이 성공적으로 실행되려면 Main 프로시저를 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="febd8-106">For the script file to run successfully, it must contain a Main procedure.</span></span> <span data-ttu-id="febd8-107">Main 프로시저는 스크립트 파일이 실행될 때 액세스되는 첫 번째 프로시저입니다.</span><span class="sxs-lookup"><span data-stu-id="febd8-107">The Main procedure is the first procedure that is accessed when your script file runs.</span></span> <span data-ttu-id="febd8-108">Main은 웹 서비스 작업을 추가하고 사용자 정의 하위 프로시저를 실행할 수 있는 위치입니다.</span><span class="sxs-lookup"><span data-stu-id="febd8-108">Main is where you can add your Web service operations and run your user defined subprocedures.</span></span> <span data-ttu-id="febd8-109">다음 코드에서는 Main 프로시저를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="febd8-109">The following code creates a Main procedure:</span></span>  
  
```  
Public Sub Main()  
    ' Your code goes here.  
End Sub  
```  
  
 <span data-ttu-id="febd8-110">스크립트 환경에서는 자동으로 보고서 서버에 연결하고, 웹 프록시 클래스를 만들고, 웹 서비스 프록시 개체에 대한 참조 변수(*rs*)를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="febd8-110">The script environment automatically connects to the report server, creates the Web proxy class, and generates a reference variable (*rs*) to the Web service proxy object.</span></span> <span data-ttu-id="febd8-111">직접 만드는 개별 문은 웹 서비스 라이브러리에서 사용할 수 있는 웹 서비스 작업 중 원하는 작업을 수행하기 위해 *rs* 모듈 수준 변수만 참조하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="febd8-111">Individual statements that you create need only refer to the *rs* module-level variable to perform any of the Web service operations that are available in the Web service library.</span></span> <span data-ttu-id="febd8-112">다음 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 코드는 스크립트 파일 내에서 웹 서비스 <xref:ReportService2010.ReportingService2010.ListChildren%2A> 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="febd8-112">The following [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] code calls the Web service <xref:ReportService2010.ReportingService2010.ListChildren%2A> method from within a script file:</span></span>  
  
```  
Public Sub Main()  
    Dim items() As CatalogItem  
    items = rs.ListChildren("/", True)  
  
    Dim item As CatalogItem  
    For Each item In items  
        Console.WriteLine(item.Name)  
    Next item  
End Sub   
```  
  
> [!IMPORTANT]  
>  <span data-ttu-id="febd8-113">사용자 자격 증명은 스크립트 환경에서 관리되며 RS.exe를 사용하여 명령 프롬프트 인수를 통해 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="febd8-113">User credentials are managed by the script environment and passed through command prompt arguments through the use of RS.exe.</span></span> <span data-ttu-id="febd8-114">*rs* 변수를 사용하여 웹 서비스의 인증을 설정할 수도 있지만 스크립트 환경을 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="febd8-114">Although you can use the *rs* variable to set the authentication of the Web service, it is recommended that you use the script environment.</span></span> <span data-ttu-id="febd8-115">스크립트 파일 자체에서 웹 서비스를 인증하지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="febd8-115">You do not need to authenticate the Web service in the script file itself.</span></span> <span data-ttu-id="febd8-116">스크립트 환경 인증에 대한 자세한 내용은 [RS.exe 유틸리티&#40;SSRS&#41;](rs-exe-utility-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="febd8-116">For more information about authenticating the script environment, see [RS.exe Utility &#40;SSRS&#41;](rs-exe-utility-ssrs.md).</span></span>  
  
 <span data-ttu-id="febd8-117">스크립트 파일 내에서는 네임스페이스를 선언하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="febd8-117">You do not declare namespaces within the script file.</span></span> <span data-ttu-id="febd8-118">스크립팅 환경에서는 유용한 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 네임스페이스인 **System.Web.Services**, **System.Web.Services.Protocols**, **System.Xml** 및 **System.IO**를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="febd8-118">The scripting environment makes several useful [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] namespaces available to you: **System.Web.Services**, **System.Web.Services.Protocols**, **System.Xml**, and **System.IO**.</span></span>  
  
 <span data-ttu-id="febd8-119">스크립트 예제는 [SQL Server Reporting Services 제품 예제(SQL Server Reporting Services Product Samples)](https://go.microsoft.com/fwlink/?LinkId=177889)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="febd8-119">For script samples, see [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="febd8-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="febd8-120">See Also</span></span>  
 <span data-ttu-id="febd8-121">[보고서 서버 웹 서비스](../report-server-web-service/report-server-web-service.md) </span><span class="sxs-lookup"><span data-stu-id="febd8-121">[Report Server Web Service](../report-server-web-service/report-server-web-service.md) </span></span>  
 <span data-ttu-id="febd8-122">[기술 참조&#40;SSRS&#41;](../technical-reference-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="febd8-122">[Technical Reference &#40;SSRS&#41;](../technical-reference-ssrs.md) </span></span>  
 [<span data-ttu-id="febd8-123">RS.exe 유틸리티&#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="febd8-123">RS.exe Utility &#40;SSRS&#41;</span></span>](rs-exe-utility-ssrs.md)  
  
  
