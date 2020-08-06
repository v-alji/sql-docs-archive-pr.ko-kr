---
title: 웹 서비스 프록시 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- Report Server Web service, proxies
- proxies [Reporting Services]
- XML Web service [Reporting Services], proxies
- Web service [Reporting Services], proxies
- Web references [Reporting Services]
ms.assetid: b1217843-8d3d-49f3-a0d2-d35b0db5b2df
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 0d080b96fa29e906c044561a684d58275af9f61e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730139"
---
# <a name="creating-the-web-service-proxy"></a><span data-ttu-id="e475c-102">웹 서비스 프록시 만들기</span><span class="sxs-lookup"><span data-stu-id="e475c-102">Creating the Web Service Proxy</span></span>
  <span data-ttu-id="e475c-103">클라이언트와 웹 서비스는 입력 및 출력 매개 변수를 XML로 캡슐화하는 SOAP 메시지를 사용하여 통신할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e475c-103">A client and a Web service can communicate using SOAP messages, which encapsulate the input and output parameters as XML.</span></span> <span data-ttu-id="e475c-104">프록시 클래스는 매개 변수를 XML 요소에 매핑한 다음 네트워크를 통해 SOAP 메시지를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="e475c-104">A proxy class maps parameters to XML elements and then sends the SOAP messages over a network.</span></span> <span data-ttu-id="e475c-105">이와 같이 프록시 클래스 덕분에 SOAP 수준에서 웹 서비스와 통신할 필요가 없으며 SOAP 및 웹 프록시를 지원하는 임의의 개발 환경에서 웹 서비스 메서드를 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e475c-105">In this way, the proxy class frees you from having to communicate with the Web service at the SOAP level and allows you to invoke Web service methods in any development environment that supports SOAP and Web service proxies.</span></span>  
  
 <span data-ttu-id="e475c-106">에서 WSDL 도구를 사용 하 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 고에서 웹 참조를 추가 하 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 여를 사용 하 여 개발 프로젝트에 프록시 클래스를 추가 하는 방법에는 두 가지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e475c-106">There are two ways to add a proxy class to your development project using the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]: with the WSDL tool in the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], and by adding a Web reference in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].</span></span> <span data-ttu-id="e475c-107">다음 섹션에서는 이 두 가지 방법에 대해 자세히 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="e475c-107">The following sections discuss this subject in further detail.</span></span>  
  
## <a name="adding-the-proxy-using-the-wsdl-tool"></a><span data-ttu-id="e475c-108">WSDL 도구를 사용하여 프록시 추가</span><span class="sxs-lookup"><span data-stu-id="e475c-108">Adding the Proxy Using the WSDL Tool</span></span>  
 <span data-ttu-id="e475c-109">[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] SDK에는 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 개발 환경에서 사용할 웹 서비스 프록시를 생성할 수 있는 WSDL(웹 서비스 기술 언어) 도구(Wsdl.exe)가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e475c-109">The [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] SDK includes the Web Services Description Language tool (Wsdl.exe), which enables you to generate a Web service proxy for use in the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] development environment.</span></span> <span data-ttu-id="e475c-110">웹 서비스를 지 원하는 언어 (현재 c # 및)로 클라이언트 프록시를 만드는 가장 일반적인 방법은 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] WSDL 도구를 사용 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="e475c-110">The most common way to create a client proxy in languages that support Web services (currently C# and [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) is to use the WSDL tool.</span></span>  
  
 <span data-ttu-id="e475c-111">**Wsdl.exe를 사용하여 프록시 클래스를 프로젝트에 추가하려면**</span><span class="sxs-lookup"><span data-stu-id="e475c-111">**To add a proxy class to your project using Wsdl.exe**</span></span>  
  
1.  <span data-ttu-id="e475c-112">명령 프롬프트에서 Wsdl.exe를 사용하여 (최소한) URL을 보고서 서버 웹 서비스에 지정함으로써 프록시 클래스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e475c-112">From a command prompt, use Wsdl.exe to create a proxy class, specifying (at a minimum) the URL to the Report Server Web service.</span></span>  
  
     <span data-ttu-id="e475c-113">예를 들어 다음 명령 프롬프트 문은 보고서 서버 웹 서비스의 관리 엔드포인트에 대한 URL을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e475c-113">For example, the following command prompt statement specifies a URL for the management endpoint of the Report Server Web service:</span></span>  
  
    ```  
    wsdl /language:CS /n:"Microsoft.SqlServer.ReportingServices2010" http://<Server Name>/reportserver/reportservice2010.asmx?wsdl  
    ```  
  
     <span data-ttu-id="e475c-114">WSDL 도구에서는 프록시 생성을 위해 다수의 명령 프롬프트 인수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="e475c-114">The WSDL tool accepts a number of command-prompt arguments for generating a proxy.</span></span> <span data-ttu-id="e475c-115">위의 예에서는 C# 언어 및 웹 서비스 엔드포인트를 두 개 이상 사용하는 경우 이름 충돌 방지를 위해 프록시에 사용하도록 제안된 네임스페이스를 지정하고 ReportingService2010.cs라는 C# 파일을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="e475c-115">The preceding example specifies the language C#, a suggested namespace to use in the proxy (to prevent name collision if using more than one Web service endpoint), and generates a C# file called ReportingService2010.cs.</span></span> <span data-ttu-id="e475c-116">이 예에서 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]을 지정한다면 이름이 ReportingService2010.vb인 프록시 파일을 생성하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e475c-116">If the example had specified [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)], the example would have generated a proxy file with the name ReportingService2010.vb.</span></span> <span data-ttu-id="e475c-117">이 파일은 명령을 실행하는 위치인 디렉터리에 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="e475c-117">This file is created in the directory from which you run the command.</span></span>  
  
2.  <span data-ttu-id="e475c-118">프록시 클래스를 어셈블리 파일(확장명 .dll)에 컴파일하고 이 클래스를 프로젝트에서 참조하거나 프로젝트 항목으로 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="e475c-118">Compile the proxy class into an assembly file (with the extension .dll) and reference it in your project, or add the class as a project item.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e475c-119">프록시 클래스를 수동으로 프로젝트에 추가할 경우 System.Web.Services.dll에 대한 참조를 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e475c-119">When you add a proxy class to your project manually, you need to add a reference to System.Web.Services.dll.</span></span> <span data-ttu-id="e475c-120">Visual Studio .NET에서 웹 참조를 사용하여 프록시를 추가하는 경우에는 참조가 자동으로 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="e475c-120">If you add the proxy using a Web reference in Visual Studio .NET, the reference is automatically created for you.</span></span> <span data-ttu-id="e475c-121">자세한 내용은 이 항목의 후반에 나오는 "Visual Studio에서 웹 참조를 사용하여 프록시 추가"를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="e475c-121">For more information, see "Adding the Proxy Using a Web Reference in Visual Studio" later in this topic.</span></span>  
  
     <span data-ttu-id="e475c-122">프록시 클래스를 프로젝트에 항목으로 추가하면 연결된 파일이 솔루션 탐색기에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="e475c-122">After you add the proxy class as an item to your project, the associated file appears in Solution Explorer.</span></span>  
  
3.  <span data-ttu-id="e475c-123">서비스를 프로그래밍 방식으로 호출하려면 프록시 클래스의 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e475c-123">To call the service programmatically, create an instance of the proxy class.</span></span>  
  
     <span data-ttu-id="e475c-124">다음 코드 예제는 프로젝트에서 <xref:ReportService2010.ReportingService2010> 프록시 클래스의 인스턴스를 만들기 위한 구문을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="e475c-124">The following code example shows the syntax for creating an instance of the <xref:ReportService2010.ReportingService2010> proxy class in a project:</span></span>  
  
```vb  
Dim service As New ReportingService2010()  
```  
  
```csharp  
ReportingService2010 service = new ReportingService2010();  
  
```  
  
 <span data-ttu-id="e475c-125">전체 구문을 포함하여 Wsdl.exe 도구에 대한 자세한 내용은 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] SDK 설명서의 "WDSL 도구(Web Services Description Language Tool)"를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="e475c-125">For more information about the Wsdl.exe tool, including its full syntax, see "Web Services Description Language Tool" in the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] SDK documentation.</span></span> <span data-ttu-id="e475c-126">웹 서비스 프록시에 대한 자세한 내용은 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] SDK 설명서의 "XML 웹 서비스 프록시 만들기(Creating an XML Web Service Proxy)"를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="e475c-126">For a full explanation of Web service proxies, see "Creating an XML Web Service Proxy" in the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] SDK documentation.</span></span>  
  
## <a name="adding-the-proxy-using-a-web-reference-in-visual-studio"></a><span data-ttu-id="e475c-127">Visual Studio에서 웹 참조를 사용하여 프록시 추가</span><span class="sxs-lookup"><span data-stu-id="e475c-127">Adding the Proxy Using a Web Reference in Visual Studio</span></span>  
 <span data-ttu-id="e475c-128">웹 참조를 통해 프로젝트에서 웹 서비스를 하나 이상 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e475c-128">A Web reference enables a project to consume one or more Web services.</span></span> [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]<span data-ttu-id="e475c-129">에서는 사용자가 다음의 간단한 단계를 수행하여 웹 서비스 참조를 프로젝트에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e475c-129">enables users to add Web service references to projects by following a few simple steps.</span></span>  
  
 <span data-ttu-id="e475c-130">**프로젝트에 웹 참조를 추가하려면**</span><span class="sxs-lookup"><span data-stu-id="e475c-130">**To add a Web reference to a project**</span></span>  
  
1.  <span data-ttu-id="e475c-131">**솔루션 탐색기**에서 웹 서비스가 사용될 프로젝트를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e475c-131">In **Solution Explorer**, select the project that will consume the Web service.</span></span>  
  
2.  <span data-ttu-id="e475c-132">**프로젝트** 메뉴에서 **웹 참조 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e475c-132">On the **Project** menu, click **Add Web Reference**.</span></span>  
  
     <span data-ttu-id="e475c-133">**웹 참조 추가** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="e475c-133">The **Add Web Reference** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="e475c-134">**URL** 필드에 보고서 서버 웹 서비스에 대한 전체 경로를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="e475c-134">In the **URL** field, enter the complete path to the Report Server Web service.</span></span>  
  
     <span data-ttu-id="e475c-135">보고서 서버 웹 서비스의 보고서 실행 엔드포인트에 대한 간단한 URL은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="e475c-135">A simplified URL for the report execution endpoint of the Report Server Web service might look like this:</span></span>  
  
    ```  
    http://<Server Name>/reportserver/reportexecution2005.asmx  
    ```  
  
     <span data-ttu-id="e475c-136">URL에는 보고서 서버 웹 서비스가 배포된 도메인, 서비스가 포함된 폴더의 이름 및 서비스에 대한 검색 파일의 이름이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="e475c-136">The URL contains the domain in which the Report Server Web service is deployed, the name of the folder containing the service, and the name of the discovery file for the service.</span></span> <span data-ttu-id="e475c-137">다양한 URL 요소에 대한 자세한 내용은 [SOAP API 액세스](../accessing-the-soap-api.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e475c-137">For a complete description of the different URL elements, see [Accessing the SOAP API](../accessing-the-soap-api.md).</span></span>  
  
     <span data-ttu-id="e475c-138">웹 서비스에서 제공하는 메서드 및 속성에 대한 설명은 왼쪽의 브라우저 창에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="e475c-138">A description of the methods and properties provided by the Web service appears in the Browser pane on the left.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e475c-139">보고서 서버 웹 서비스와 연관된 항목에 대한 자세한 내용은 [보고서 서버 웹 서비스 메서드](../methods/report-server-web-service-methods.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e475c-139">For more information about the items associated with the Report Server Web service, see [Report Server Web Service Methods](../methods/report-server-web-service-methods.md).</span></span>  
  
4.  <span data-ttu-id="e475c-140">프로젝트에서 보고서 서버 웹 서비스를 사용할 수 있고 보고서 서버에 액세스할 수 있는 충분한 권한이 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="e475c-140">Verify that your project can use the Report Server Web service, and that you have appropriate permission to access the report server.</span></span>  
  
5.  <span data-ttu-id="e475c-141">보고서 서버 웹 서비스에 프로그래밍 방식으로 액세스하기 위해 코드에 사용할 이름을 **웹 참조 이름** 필드에 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="e475c-141">In the **Web reference name** field, enter a name that you will use in your code to access the Report Server Web service programmatically.</span></span>  
  
6.  <span data-ttu-id="e475c-142">**참조 추가** 단추를 선택하여 웹 서비스에 대한 애플리케이션의 참조를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e475c-142">Select the **Add Reference** button to create a reference in your application to the Web service.</span></span>  
  
     <span data-ttu-id="e475c-143">새 참조가 **솔루션 탐색기**에서 활성 프로젝트에 대한 Web References 노드 아래에 **웹 참조 이름** 필드에 지정한 이름으로 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="e475c-143">The new reference appears in **Solution Explorer** under the Web References node for the active project, named as specified in the **Web reference name** field.</span></span>  
  
7.  <span data-ttu-id="e475c-144">**솔루션 탐색기**에서 Web References 폴더를 확장하여 프로젝트의 항목에서 사용 가능한 웹 참조 클래스에 대한 네임스페이스를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="e475c-144">In **Solution Explorer**, expand the Web References folder to note the namespace for the Web reference classes that are available to the items in your project.</span></span>  
  
     <span data-ttu-id="e475c-145">프로젝트에 웹 참조를 추가하면 연결된 파일이 **솔루션 탐색기** Web References 폴더 내의 폴더에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e475c-145">After adding a Web reference to your project, the associated files are displayed in a folder within the Web References folder of **Solution Explorer**.</span></span>  
  
 <span data-ttu-id="e475c-146">웹 참조를 추가한 후 다음 구문을 사용하여 프록시 클래스의 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e475c-146">After you add the Web reference, use the following syntax to create an instance of the proxy class:</span></span>  
  
```vb  
Dim rs As New myNamespace.myReferenceName.ReportExecutionService()  
rs.Url = "http://<Server Name>/reportserver/reportexecution2005.asmx?wsdl"  
rs.Credentials = System.Net.CredentialCache.DefaultCredentials  
```  
  
```csharp  
myNamespace.myReferenceName.ReportExecutionService rs = new myNamespace.myReferenceName.ReportExecutionService();  
rs.Url = "http://<Server Name>/reportserver/reportexecution2005.asmx?wsdl"  
rs.Credentials = System.Net.CredentialCache.DefaultCredentials  
  
```  
  
 <span data-ttu-id="e475c-147">**using**([!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]의 경우 **Import**) 지시문을 보고서 서버 웹 서비스 참조에 추가할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e475c-147">You can also add a **using** (**Import** in [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) directive to the Report Server Web service reference.</span></span> <span data-ttu-id="e475c-148">이 지시문을 사용할 경우에는 네임스페이스에서 형식을 정규화하지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e475c-148">If you use this directive, you do not need to fully qualify the types in the namespace.</span></span> <span data-ttu-id="e475c-149">이렇게 하려면 다음 코드를 파일에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="e475c-149">To do this, add the following code to your file:</span></span>  
  
```vb  
Import myNamespace.myReferenceName  
```  
  
```csharp  
using myNamespace.myReferenceName;  
```  
  
## <a name="see-also"></a><span data-ttu-id="e475c-150">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e475c-150">See Also</span></span>  
 <span data-ttu-id="e475c-151">[보고서 서버 웹 서비스](../report-server-web-service.md) </span><span class="sxs-lookup"><span data-stu-id="e475c-151">[Report Server Web Service](../report-server-web-service.md) </span></span>  
 <span data-ttu-id="e475c-152">[웹 서비스와 .NET Framework를 사용하여 애플리케이션 빌드](building-applications-using-the-web-service-and-the-net-framework.md) </span><span class="sxs-lookup"><span data-stu-id="e475c-152">[Building Applications Using the Web Service and the .NET Framework](building-applications-using-the-web-service-and-the-net-framework.md) </span></span>  
 [<span data-ttu-id="e475c-153">기술 참조&#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="e475c-153">Technical Reference &#40;SSRS&#41;</span></span>](../../technical-reference-ssrs.md)  
  
  
