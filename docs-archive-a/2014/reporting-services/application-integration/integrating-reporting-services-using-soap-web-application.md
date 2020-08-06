---
title: 웹 애플리케이션에서 SOAP API 사용 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- SOAP [Reporting Services], Web applications
- impersonation [Reporting Services]
- user impersonation [Reporting Services]
- report servers [Reporting Services], SOAP
- Web applications [Reporting Services]
ms.assetid: e8ca4455-0dc3-4741-8872-3636114938ad
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: e228f01915df633f50b23bf93e892446863c28ad
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729148"
---
# <a name="using-the-soap-api-in-a-web-application"></a><span data-ttu-id="dce1e-102">웹 애플리케이션에서 SOAP API 사용</span><span class="sxs-lookup"><span data-stu-id="dce1e-102">Using the SOAP API in a Web Application</span></span>
  <span data-ttu-id="dce1e-103">Reporting Services SOAP API를 통해 보고서 서버의 전체 기능에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dce1e-103">You can access the full functionality of the report server through the Reporting Services SOAP API.</span></span> <span data-ttu-id="dce1e-104">SOAP API는 웹 서비스이므로 쉽게 액세스하여 사용자 지정 비즈니스 애플리케이션에 엔터프라이즈 보고 기능을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dce1e-104">Because it's a Web service, the SOAP API can be easily accessed to provide enterprise reporting features to your custom business applications.</span></span> <span data-ttu-id="dce1e-105">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 애플리케이션에서 SOAP API에 액세스하는 것과 동일한 방법으로 웹 애플리케이션에서 보고서 서버 웹 서비스에 액세스합니다.</span><span class="sxs-lookup"><span data-stu-id="dce1e-105">You access the Report Server Web service from a Web application in much the same way that you access the SOAP API from a [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows application.</span></span> <span data-ttu-id="dce1e-106">를 사용 하 여 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 보고서 서버 웹 서비스의 속성 및 메서드를 표시 하는 프록시 클래스를 생성할 수 있으며 친숙 한 인프라와 도구를 사용 하 여 기술에서 비즈니스 응용 프로그램을 빌드할 수 있습니다 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="dce1e-106">Using the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], you can generate a proxy class that exposes the properties and methods of the Report Server Web service and enables you to use a familiar infrastructure and tools to build business applications on [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] technology.</span></span>  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="dce1e-107">보고서 관리 기능은 Windows 애플리케이션에서 액세스하는 것과 마찬가지로 웹 애플리케이션에서도 쉽게 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dce1e-107">report management functionality is just as easily accessed from a Web application as from a Windows application.</span></span> <span data-ttu-id="dce1e-108">웹 애플리케이션에서는 보고서 서버 데이터베이스에서 항목 추가 및 제거, 항목 보안 설정, 보고서 서버 데이터베이스 항목 수정, 일정 예약 및 배달 관리 등을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dce1e-108">From a Web application, you can add and remove items from the report server database, set item security, modify report server database items, manage scheduling and delivery, and more.</span></span>  
  
## <a name="enabling-impersonation"></a><span data-ttu-id="dce1e-109">가장 사용</span><span class="sxs-lookup"><span data-stu-id="dce1e-109">Enabling Impersonation</span></span>  
 <span data-ttu-id="dce1e-110">웹 애플리케이션 구성의 첫 단계는 웹 서비스 클라이언트에서 가장을 사용하도록 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="dce1e-110">The first step in configuring your Web application is to enable impersonation from the Web service client.</span></span> <span data-ttu-id="dce1e-111">가장을 사용하면 [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] 애플리케이션은 대신 작업할 다른 클라이언트의 ID로 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dce1e-111">With impersonation, [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] applications can execute with the identity of the client on whose behalf they are operating.</span></span> [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)]<span data-ttu-id="dce1e-112">은 [!INCLUDE[msCoName](../../includes/msconame-md.md)] IIS(인터넷 정보 서비스)에 의존하여 사용자를 인증하고 인증된 토큰을 [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] 애플리케이션에 전달하거나 사용자를 인증할 수 없는 경우 인증되지 않은 토큰을 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="dce1e-112">relies on [!INCLUDE[msCoName](../../includes/msconame-md.md)] Internet Information Services (IIS) to authenticate the user and either pass an authenticated token to the [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] application or, if unable to authenticate the user, pass an unauthenticated token.</span></span> <span data-ttu-id="dce1e-113">가장을 사용한다면 두 경우 모두 어떤 토큰이 수신되든지 [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] 애플리케이션은 이 토큰을 가장합니다.</span><span class="sxs-lookup"><span data-stu-id="dce1e-113">In either case, the [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] application impersonates whichever token is received if impersonation is enabled.</span></span> <span data-ttu-id="dce1e-114">클라이언트 애플리케이션의 Web.config 파일을 다음과 같이 수정하여 클라이언트에서 가장을 사용하도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dce1e-114">You can enable impersonation on the client, by modifying the Web.config file of the client application as follows:</span></span>  
  
```  
<!-- Web.config file. -->  
<identity impersonate="true"/>  
```  
  
> [!NOTE]  
>  <span data-ttu-id="dce1e-115">가장은 기본적으로 사용 안 함으로 설정되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dce1e-115">Impersonation is disabled by default.</span></span>  
  
 <span data-ttu-id="dce1e-116">가장에 대 한 자세한 내용은 [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK 설명서를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="dce1e-116">For more information about [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] impersonation, see the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK documentation.</span></span>  
  
## <a name="managing-the-report-server-using-soap-api"></a><span data-ttu-id="dce1e-117">SOAP API를 사용하여 보고서 서버 관리</span><span class="sxs-lookup"><span data-stu-id="dce1e-117">Managing the Report Server using SOAP API</span></span>  
 <span data-ttu-id="dce1e-118">웹 애플리케이션을 사용하여 보고서 서버 및 콘텐츠를 관리할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dce1e-118">You can also use your Web application to manage a report server and its contents.</span></span> <span data-ttu-id="dce1e-119">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]에 포함된 보고서 관리자는 [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] 및 Reporting Services SOAP API를 사용하여 작성된 웹 애플리케이션의 예입니다.</span><span class="sxs-lookup"><span data-stu-id="dce1e-119">Report Manager, included with [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], is an example of a Web application that is completely built using [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] and the Reporting Services SOAP API.</span></span> <span data-ttu-id="dce1e-120">보고서 관리자의 보고서 관리 기능을 사용자 지정 웹 애플리케이션에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dce1e-120">You can add the report management functionality of Report Manager to your custom Web applications.</span></span> <span data-ttu-id="dce1e-121">예를 들어 보고서 서버 데이터베이스에서 사용 가능한 보고서 목록을 반환 하 고 [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] 사용자가 선택할 수 있도록 컨트롤에 표시 하는 것이 좋습니다 `Listbox` .</span><span class="sxs-lookup"><span data-stu-id="dce1e-121">For example, you might want to return a list of available reports in the report server database and display them in a [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] `Listbox` control for your users to choose from.</span></span> <span data-ttu-id="dce1e-122">다음 코드는 보고서 서버 데이터베이스에 연결하고 보고서 서버 데이터베이스의 항목 목록을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="dce1e-122">The following code connects to the report server database and returns a list of items in the report server database.</span></span> <span data-ttu-id="dce1e-123">그러면 사용 가능한 보고서가 Listbox 컨트롤에 추가되고 각 보고서의 경로가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="dce1e-123">The available reports are then added to a Listbox control, which displays the path of each report.</span></span>  
  
```vb  
Private Sub Page_Load(sender As Object, e As System.EventArgs)  
   ' Create a Web service proxy object and set credentials  
   Dim rs As New ReportingService2005()  
   rs.Credentials = System.Net.CredentialCache.DefaultCredentials  
  
   ' Return a list of catalog items in the report server database  
   Dim items As CatalogItem() = rs.ListChildren("/", True)  
  
   ' For each report, display the path of the report in a Listbox  
   Dim ci As CatalogItem  
   For Each ci In  items  
      If ci.Type = ItemTypeEnum.Report Then  
         catalogListBox.Items.Add(ci.Path)  
      End If  
   Next ci  
End Sub ' Page_Load   
```  
  
```csharp  
private void Page_Load(object sender, System.EventArgs e)  
{  
   // Create a Web service proxy object and set credentials  
   ReportingService2005 rs = new ReportingService2005();  
   rs.Credentials = System.Net.CredentialCache.DefaultCredentials;  
  
   // Return a list of catalog items in the report server database  
   CatalogItem[] items = rs.ListChildren("/", true);  
  
   // For each report, display the path of the report in a Listbox  
   foreach(CatalogItem ci in items)  
   {  
      if (ci.Type == ItemTypeEnum.Report)  
         catalogListBox.Items.Add(ci.Path);  
   }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="dce1e-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="dce1e-124">See Also</span></span>  
 <span data-ttu-id="dce1e-125">[웹 서비스와 .NET Framework를 사용하여 애플리케이션 빌드](../report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md) </span><span class="sxs-lookup"><span data-stu-id="dce1e-125">[Building Applications Using the Web Service and the .NET Framework](../report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md) </span></span>  
 <span data-ttu-id="dce1e-126">[응용 프로그램에 Reporting Services 통합](../application-integration/integrating-reporting-services-into-applications.md) </span><span class="sxs-lookup"><span data-stu-id="dce1e-126">[Integrating Reporting Services into Applications](../application-integration/integrating-reporting-services-into-applications.md) </span></span>  
 <span data-ttu-id="dce1e-127">[보고서 관리자&#40;SSRS 기본 모드&#41;](../report-manager-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="dce1e-127">[Report Manager  &#40;SSRS Native Mode&#41;](../report-manager-ssrs-native-mode.md) </span></span>  
 [<span data-ttu-id="dce1e-128">Windows 애플리케이션에서 SOAP API 사용</span><span class="sxs-lookup"><span data-stu-id="dce1e-128">Using the SOAP API in a Windows Application</span></span>](integrating-reporting-services-using-soap-windows-application.md)  
  
  