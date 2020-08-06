---
title: Windows 애플리케이션에서 SOAP API 사용 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- rendered reports [Reporting Services]
- Windows applications [Reporting Services]
- Windows Forms [Reporting Services]
- SOAP [Reporting Services], Windows applications
ms.assetid: e4804792-20cd-4df2-9257-fb958ff447b4
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 115ce02da69a8adb2c7a3de4175e528f281eb2b2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638566"
---
# <a name="using-the-soap-api-in-a-windows-application"></a><span data-ttu-id="14628-102">Windows 애플리케이션에서 SOAP API 사용</span><span class="sxs-lookup"><span data-stu-id="14628-102">Using the SOAP API in a Windows Application</span></span>
  <span data-ttu-id="14628-103">Reporting Services SOAP API를 통해 보고서 서버의 전체 기능에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="14628-103">You can access the full functionality of the report server through the Reporting Services SOAP API.</span></span> <span data-ttu-id="14628-104">SOAP API는 웹 서비스이므로 쉽게 액세스하여 사용자 지정 비즈니스 애플리케이션에 엔터프라이즈 보고 기능을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="14628-104">The SOAP API is a Web service and, as such, can be easily accessed to provide enterprise reporting features to your custom business applications.</span></span> <span data-ttu-id="14628-105">서비스를 호출하는 코드를 작성하기만 하면 Windows 애플리케이션에서 웹 서비스에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="14628-105">You can access the Web service in a Windows application simply by writing code that makes calls to the service.</span></span> <span data-ttu-id="14628-106">를 사용 하 여 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 웹 서비스의 속성 및 메서드를 표시 하는 프록시 클래스를 생성할 수 있으며, 친숙 한 인프라와 도구를 사용 하 여 기술을 기반으로 구축 된 비즈니스 응용 프로그램을 빌드할 수 있습니다 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="14628-106">Using the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], you can generate a proxy class that exposes the properties and methods of the Web service and enables you to use a familiar infrastructure and tools to build business applications built on [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] technology.</span></span>  
  
## <a name="integrating-report-management-functionality-using-windows-forms"></a><span data-ttu-id="14628-107">Windows Forms를 사용하여 보고서 관리 기능 통합</span><span class="sxs-lookup"><span data-stu-id="14628-107">Integrating Report Management Functionality Using Windows Forms</span></span>  
 <span data-ttu-id="14628-108">URL 액세스와 달리 SOAP API는 보고서 서버를 통해 사용 가능한 전체 관리 기능 집합을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="14628-108">Unlike URL access, the SOAP API exposes the complete set of management functions that are available through the report server.</span></span> <span data-ttu-id="14628-109">다시 말해서 개발자가 SOAP을 통해 보고서 관리자의 전체 관리 기능을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="14628-109">This means that the entire administrative functionality of Report Manager is available to developers through SOAP.</span></span> <span data-ttu-id="14628-110">그러므로 Windows Forms를 사용하여 완전한 관리 도구를 개발할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="14628-110">As such, you can develop a complete management and administration tool using Windows Forms.</span></span> <span data-ttu-id="14628-111">예를 들어 Windows 애플리케이션에서 사용자들이 보고서 서버 네임스페이스의 내용을 검색할 수 있도록 설정해야 할 경우가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="14628-111">For example, in your Windows application, you might want to enable your users to retrieve the contents of the report server namespace.</span></span> <span data-ttu-id="14628-112">이런 경우 웹 서비스 <xref:ReportService2010.ReportingService2010.ListChildren%2A> 메서드를 사용하여 보고서 서버 데이터베이스의 모든 항목을 나열한 다음 Listview, Treeview 또는 Combobox 컨트롤을 사용하여 이러한 항목을 사용자에게 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="14628-112">To do this, you could use the Web service <xref:ReportService2010.ReportingService2010.ListChildren%2A> method to list all the items in the report server database and then use a Listview, Treeview, or Combobox control to display those items to your users.</span></span> <span data-ttu-id="14628-113">다음 웹 서비스 코드를 사용하면 사용자가 폼에서 단추를 클릭할 때 사용자의 내 보고서 폴더에서 사용 가능한 보고서의 현재 목록을 검색하도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="14628-113">The following Web service code might be used to retrieve the current list of available reports in a user's My Reports folder when a user clicks a button on a form:</span></span>  
  
```vb  
' Button click event that retrieves a list of reports from  
' the My Reports folder and displays them in a combo box  
Private Sub listReportsButton_Click(sender As Object, e As System.EventArgs)  
   ' Create a new Web service object and set credentials  
   ' to Windows Authentication  
   Dim rs As New ReportingService2010()  
   rs.Credentials = System.Net.CredentialCache.DefaultCredentials  
  
   ' Return the list of items in My Reports  
   Dim items As CatalogItem() = rs.ListChildren("/Adventureworks 2008 Sample Reports", False)  
  
   Dim ci As CatalogItem  
   For Each ci In  items  
      ' If the item is a report, add it to   
      ' a combo box  
      If ci.TypeName = "Report" Then  
         catalogComboBox.Items.Add(ci.Name)  
      End If  
   Next ci  
End Sub 'listReportsButton_Click  
```  
  
```csharp  
// Button click event that retrieves a list of reports from  
// the My Reports folder and displays them in a combo box  
private void listReportsButton_Click(object sender, System.EventArgs e)  
{  
   // Create a new Web service object and set credentials  
   // to Windows Authentication  
   ReportingService2010 rs = new ReportingService2010();  
   rs.Credentials = System.Net.CredentialCache.DefaultCredentials;  
  
   // Return the list of items in My Reports  
   CatalogItem[] items = rs.ListChildren("/Adventureworks 2008 Sample Reports", false);  
  
   foreach (CatalogItem ci in items)  
   {  
      // If the item is a report, add it to   
      // a combo box  
      if (ci.TypeName == "Report")  
         catalogComboBox.Items.Add(ci.Name);  
   }  
}  
```  
  
 <span data-ttu-id="14628-114">여기서 사용자가 콤보 상자에서 보고서를 선택하고 웹 브라우저 컨트롤이나 이미지 컨트롤을 사용하여 폼에서 보고서를 미리 볼 수 있도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="14628-114">From there, you might enable users to select the report from the Combo box and preview the report on the form either using a Web browser control or an image control.</span></span>  
  
## <a name="enabling-report-viewing-and-navigation-using-windows-forms"></a><span data-ttu-id="14628-115">Windows Forms를 사용하여 보고서 보기 및 탐색 사용</span><span class="sxs-lookup"><span data-stu-id="14628-115">Enabling Report Viewing and Navigation Using Windows Forms</span></span>  
 <span data-ttu-id="14628-116">보고서를 Windows Forms 애플리케이션에 통합하는 데 사용할 수 있는 두 가지 메서드가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="14628-116">There are two methods available for integrating reports into your Windows Forms applications.</span></span>  
  
 <span data-ttu-id="14628-117">SOAP API를 사용하여 지원되는 모든 <xref:ReportExecution2005.ReportExecutionService.Render%2A> 메서드 사용 렌더링 형식으로 보고서를 렌더링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="14628-117">You can use the SOAP API to render reports to any of the supported rendering formats using the <xref:ReportExecution2005.ReportExecutionService.Render%2A> method.</span></span> <span data-ttu-id="14628-118">SOAP을 통해 보고서 보기 및 탐색을 사용하면 다음과 같이 약간의 단점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="14628-118">There are slight disadvantages to enabling report viewing and navigation through SOAP:</span></span>  
  
-   <span data-ttu-id="14628-119">URL 액세스를 통한 HTML 뷰어에 포함된 보고서 도구 모음의 기본 제공 기능을 활용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="14628-119">You cannot take advantage of the built-in functionality of the report toolbar that is included with the HTML Viewer through URL access.</span></span>  
  
-   <span data-ttu-id="14628-120">HTML로 렌더링할 경우 <xref:ReportExecution2005.ReportExecutionService.RenderStream%2A> 메서드를 사용하여 이미지나 리소스를 추가 스트림 형태로 별도로 렌더링해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="14628-120">If you render to HTML, you must separately render any images or resources as additional streams using the <xref:ReportExecution2005.ReportExecutionService.RenderStream%2A> method.</span></span>  
  
-   <span data-ttu-id="14628-121">URL 액세스를 사용하면 SOAP API에 비해 보고서 렌더링 성능이 약간 높아집니다.</span><span class="sxs-lookup"><span data-stu-id="14628-121">There is a slight performance advantage to rendering reports using URL access over using the SOAP API.</span></span>  
  
 <span data-ttu-id="14628-122">하지만 SOAP API의 <xref:ReportExecution2005.ReportExecutionService.Render%2A> 메서드를 사용하면 보고서를 렌더링하여 프로그래밍 방식으로 다양한 출력 형식으로 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="14628-122">However, the <xref:ReportExecution2005.ReportExecutionService.Render%2A> method of the SOAP API can be used to render reports and save them to various output formats programmatically.</span></span> <span data-ttu-id="14628-123">이 점을 사용자 개입이 필요한 URL 액세스에 비해 이점으로 손꼽을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="14628-123">This is an advantage over URL access, which requires user interaction.</span></span> <span data-ttu-id="14628-124">SOAP API <xref:ReportExecution2005.ReportExecutionService.Render%2A> 메서드를 사용하여 보고서를 렌더링하는 경우 지원되는 모든 출력 형식으로 렌더링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="14628-124">When you render a report using the SOAP API <xref:ReportExecution2005.ReportExecutionService.Render%2A> method, you can render to any of the supported output formats.</span></span>  
  
 <span data-ttu-id="14628-125">에 포함 된 무료로 배포 가능한 ReportViewer 컨트롤을 사용할 수도 있습니다 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsOrcas](../../includes/vsorcas-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="14628-125">You can also use the freely distributable ReportViewer controls that are included with [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsOrcas](../../includes/vsorcas-md.md)].</span></span> <span data-ttu-id="14628-126">ReportViewer 컨트롤을 통해 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 기능을 사용자 지정 애플리케이션에 쉽게 포함시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="14628-126">The ReportViewer controls make it easy to embed [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] functionality into custom applications.</span></span> <span data-ttu-id="14628-127">ReportViewer 컨트롤은 사전 디자인을 갖추어 완전히 제작된 보고서를 애플리케이션 기능 집합의 일부로 제공하려는 개발자에게 적합합니다. 예를 들어 웹 사이트 관리 애플리케이션에 회사 웹 사이트에서의 클릭 동향 분석을 보여 주는 보고서를 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="14628-127">The ReportViewer controls are intended for developers who want to provide predesigned, fully authored reports as part of an application feature set (for example, a Web site management application might include reports that show click-stream analysis on company Web sites).</span></span> <span data-ttu-id="14628-128">애플리케이션에 컨트롤을 포함하는 것은 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 서버 구성 요소를 애플리케이션 배포에 포함하는 대신 사용할 수 있는 간소화된 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="14628-128">Embedding the controls in an application provides a streamlined alternative to including the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] server components in your application deployment.</span></span> <span data-ttu-id="14628-129">이러한 컨트롤은 보고서 기능을 제공하며 단, [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]에서 제공되는 보고서 제작, 게시, 배포 및 배달에 대한 추가 지원은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="14628-129">The controls provide report functionality, but without the additional report authoring, publication, or distribution and delivery support that you find in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="14628-130">ReportViewer 컨트롤에는 기능이 풍부한 Windows 클라이언트 애플리케이션용과 [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] 애플리케이션용의 두 가지 버전이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="14628-130">There are two versions of the ReportViewer controls, one for rich Windows client applications and one for [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] applications.</span></span> <span data-ttu-id="14628-131">이러한 컨트롤은 로컬 처리 및 원격 처리 모드를 모두 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="14628-131">The controls support both local processing and remote processing modes.</span></span> <span data-ttu-id="14628-132">로컬 처리 모드의 경우 애플리케이션은 보고서 정의 및 데이터 세트을 제공하고 보고서 처리를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="14628-132">In local processing mode, your application provides the report definition and datasets and triggers report processing.</span></span> <span data-ttu-id="14628-133">원격 처리 모드의 경우에는 데이터 검색 및 보고서 처리는 보고서 서버에서 수행되며 컨트롤은 표시 및 보고서 탐색에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="14628-133">In remote processing mode, data retrieval and report processing happen on the report server and the control is used for display and report navigation.</span></span> <span data-ttu-id="14628-134">이 모델에서는 데스크톱에서 엔터프라이즈 수준까지 확장될 수 있는 기능이 풍부한 애플리케이션을 구축할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="14628-134">This model allows you to build rich applications that can be scaled from desktop to the enterprise.</span></span>  
  
 <span data-ttu-id="14628-135">ReportViewer 컨트롤은 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 온라인 도움말에 설명되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="14628-135">ReportViewer controls are documented in [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] online Help.</span></span> <span data-ttu-id="14628-136">자세한 내용은 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 제품 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="14628-136">For more information, see the [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] product documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14628-137">참고 항목</span><span class="sxs-lookup"><span data-stu-id="14628-137">See Also</span></span>  
 <span data-ttu-id="14628-138">[웹 서비스와 .NET Framework를 사용하여 애플리케이션 빌드](../report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md) </span><span class="sxs-lookup"><span data-stu-id="14628-138">[Building Applications Using the Web Service and the .NET Framework](../report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md) </span></span>  
 <span data-ttu-id="14628-139">[응용 프로그램에 Reporting Services 통합](../application-integration/integrating-reporting-services-into-applications.md) </span><span class="sxs-lookup"><span data-stu-id="14628-139">[Integrating Reporting Services into Applications](../application-integration/integrating-reporting-services-into-applications.md) </span></span>  
 [<span data-ttu-id="14628-140">웹 애플리케이션에서 SOAP API 사용</span><span class="sxs-lookup"><span data-stu-id="14628-140">Using the SOAP API in a Web Application</span></span>](integrating-reporting-services-using-soap-web-application.md)  
  
  
