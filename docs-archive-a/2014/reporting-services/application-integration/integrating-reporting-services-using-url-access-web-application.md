---
title: 웹 애플리케이션에서 URL 액세스 사용 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- links [Reporting Services], URL access
- URL access [Reporting Services], Web applications
- POST requests
- direct addressing [Reporting Services]
- Web applications [Reporting Services]
- hyperlinks [Reporting Services]
ms.assetid: 39e7918c-ad2d-4ca6-b099-2dd4dbdb83dc
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: cd31f76658f8160cbb2a576debc335588f77e72c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638561"
---
# <a name="using-url-access-in-a-web-application"></a><span data-ttu-id="fc508-102">웹 애플리케이션에서 URL 액세스 사용</span><span class="sxs-lookup"><span data-stu-id="fc508-102">Using URL Access in a Web Application</span></span>
  <span data-ttu-id="fc508-103">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]의 URL 액세스는 네트워크를 통해 개별 보고서에 액세스할 수 있도록 특별히 디자인되었습니다.</span><span class="sxs-lookup"><span data-stu-id="fc508-103">URL access in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] is specifically designed to enable access to individual reports over a network.</span></span> <span data-ttu-id="fc508-104">이런 유형의 액세스는 보고서 보기와 탐색을 사용자 지정 웹 애플리케이션으로 통합하는 데 알맞습니다.</span><span class="sxs-lookup"><span data-stu-id="fc508-104">This type of access is best for integrating report viewing and navigation into a custom Web application.</span></span> <span data-ttu-id="fc508-105">웹 애플리케이션에서 URL 액세스를 사용하려면 다음 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc508-105">To use URL access in Web applications, you can:</span></span>  
  
-   <span data-ttu-id="fc508-106">URL을 웹 사이트 또는 포털의 특정 보고서 서버로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="fc508-106">Address a URL to a specific report server from a Web site or portal.</span></span>  
  
-   <span data-ttu-id="fc508-107">폼 POST 메서드를 사용하고 양식 필드를 사용하여 쿼리 문자열 매개 변수를 보고서 서버 URL에 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="fc508-107">Use a form POST method and pass query string parameters to a report server URL using form fields.</span></span>  
  
## <a name="url-access-through-direct-addressing"></a><span data-ttu-id="fc508-108">직접 주소 지정을 통한 URL 액세스</span><span class="sxs-lookup"><span data-stu-id="fc508-108">URL Access Through Direct Addressing</span></span>  
 <span data-ttu-id="fc508-109">URL을 사용하여 보고서 서버 또는 보고서 서버 데이터베이스 항목에 액세스하려면 웹 브라우저나 애플리케이션 내에서 URL 주소를 제공하기만 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fc508-109">To access a report server or report server database item using a URL, simply provide the URL address from within a Web browser or application.</span></span> <span data-ttu-id="fc508-110">또한 액세스할 보고서 또는 리소스의 모양에 영향을 줄 수 있는 매개 변수를 URL에 제공할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc508-110">You can also supply parameters to the URL that can affect the appearance of the report or resource that is being accessed.</span></span> <span data-ttu-id="fc508-111">URL은 웹 브라우저의 주소 표시줄을 통해 보고서 서버를 대상으로 지정할 수 있으며 또는 더 큰 규모의 웹 애플리케이션이나 포털의 일부인 **IFrame**의 원본이 될 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc508-111">A URL can target a report server through the address bar of a Web browser, or a URL can be the source of an **IFrame** that is part of a larger Web application or portal.</span></span> <span data-ttu-id="fc508-112">포털의 다양한 웹 페이지에 보고서 하이퍼링크를 포함시키거나 보고서에 대해 특정 프레임을 대상으로 지정하거나 프로세스 도중에 새 브라우저 창을 열 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc508-112">You can include hyperlinks to reports on various Web pages of your portal, as well as target a specific frame for the report or open a new browser window in the process.</span></span>  
  
 <span data-ttu-id="fc508-113">다음 예에서 하이퍼링크는 "main"이라는 프레임을 대상으로 지정하며 이 프레임은 하이퍼링크를 포함하는 프레임과 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc508-113">In the following example, the hyperlink targets a frame named "main", which might be different from the one that includes the hyperlink.</span></span> <span data-ttu-id="fc508-114">하이퍼링크는 웹 포털의 일부일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc508-114">The hyperlink might be part of Web portal.</span></span>  
  
```  
<a href="http://server/reportserver?/SampleReports/Territory Sales   
Drilldown&rs:Command=Render&rc:LinkTarget=main" target="main" >  
   Click here for the Territory Sales Drilldown sample report  
</a>  
```  
  
 <span data-ttu-id="fc508-115">위의 예제에서 디바이스 정보 설정 **LinkTarget**은 URL 쿼리 문자열 내의 "main" 값과 함께 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="fc508-115">In the previous example, the device information setting **LinkTarget** is passed with a value of "main" in the query string of the URL.</span></span> <span data-ttu-id="fc508-116">그러면 보고서의 드릴스루 하이퍼링크도 이름이 "main"인 프레임을 대상으로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="fc508-116">This ensures that any drillthrough hyperlinks in the report also target the frame named "main".</span></span>  
  
 <span data-ttu-id="fc508-117">디바이스 정보 설정에 대한 자세한 내용은 [디바이스 정보 설정을 렌더링 확장 프로그램에 전달](../report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fc508-117">For more information about device information settings, see [Passing Device Information Settings to Rendering Extensions](../report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md).</span></span>  
  
 <span data-ttu-id="fc508-118">상당수의 서버와 브라우저에서는 URL에 허용되는 문자 수를 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="fc508-118">Note that many servers and browsers limit the number of characters allowed in a URL.</span></span> <span data-ttu-id="fc508-119">일부의 경우 256자 제한이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="fc508-119">In some cases, a 256-character limit is imposed.</span></span> <span data-ttu-id="fc508-120">이 제한을 해결하려면 폼 제출을 사용하여 POST 요청을 사용하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fc508-120">To get around this limitation, you can use POST requests using form submission.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fc508-121">Internet Explorer의 URL 길이는 최대 2,083자입니다.</span><span class="sxs-lookup"><span data-stu-id="fc508-121">Internet Explorer has a maximum URL length of 2,083 characters.</span></span> <span data-ttu-id="fc508-122">이 제한은 POST 및 GET 요청 URL 모두에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="fc508-122">This limit applies to both POST and GET request URLs.</span></span> <span data-ttu-id="fc508-123">하지만 POST는 이름/값 쌍을 폼의 일부로 제출하는 경우 URL이 아닌 머리글로 전송되기 때문에 URL 크기에 제한받지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fc508-123">POST, however, is not limited by the size of the URL for submitting name/value pairs as part of a form, because they are transferred in the header and not the URL.</span></span>  
  
## <a name="url-access-through-a-form-post-method"></a><span data-ttu-id="fc508-124">폼 POST 메서드를 통한 URL 액세스</span><span class="sxs-lookup"><span data-stu-id="fc508-124">URL Access Through a Form POST Method</span></span>  
 <span data-ttu-id="fc508-125">사용자가 URL 액세스를 사용하여 보고서 서버에서 데이터를 요청하면 HTTP 요청에 GET 메서드가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="fc508-125">When a user requests data from a report server using URL access, the HTTP request uses the GET method.</span></span> <span data-ttu-id="fc508-126">이것은 METHOD="GET"인 폼 제출과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="fc508-126">This is equivalent to a form submission where METHOD="GET".</span></span> <span data-ttu-id="fc508-127">METHOD="GET"을 사용하는 URL 요청 또는 폼 제출은 서버나 웹 브라우저에서 처리할 수 있는 최대 문자 수의 제한을 받습니다.</span><span class="sxs-lookup"><span data-stu-id="fc508-127">URL requests or form submissions that use METHOD="GET" are limited by the maximum number of characters that a server or Web browser can process.</span></span>  
  
 <span data-ttu-id="fc508-128">POST 요청(METHOD="POST" 및 입력 필드)의 경우 이름/값 쌍이 URL이 아닌 머리글로 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="fc508-128">With POST requests (METHOD="POST" and input fields), the name/value pairs are transferred in the header and not the URL.</span></span> <span data-ttu-id="fc508-129">따라서 쿼리 문자열의 이름/값 쌍은 URL의 일부가 아니므로 더 길고 복잡한 매개 변수 목록을 제공할 수 있게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fc508-129">Therefore, the name/value pairs of the query string are not part of the URL, thus enabling you to provide much longer and more complex parameter lists.</span></span>  
  
 <span data-ttu-id="fc508-130">사용자는 직접 액세스를 사용하면 보고서 서버에 대한 URL을 볼 수 있으며 쿼리 문자열을 수정하거나 특정 URL 요청 및 보고서 서버 매개 변수를 나중에 사용하도록 메모할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc508-130">Using direct access, a user can see the URL for the report server, and may be able to modify the  query string or note the particular URL request and report server parameters for later use.</span></span>  
  
 <span data-ttu-id="fc508-131">다음 예제 HTML은 특정 URL로 보고서 서버를 대상으로 지정하고 쿼리 문자열 매개 변수를 폼 입력 필드의 일부로 전달하는 데 사용할 수 있는 폼의 사용을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="fc508-131">The following sample HTML demonstrates the use of a form that you can use to target a report server with a specific URL and pass query string parameters as part of the form's input fields.</span></span>  
  
```  
<FORM id="frmRender" action="http://server/reportserver?/SampleReports/  
   Territory Sales Drilldown" method="post" target="_self">  
   <INPUT type="hidden" name="rs:Command" value="Render">   
   <INPUT type="hidden" name="rc:LinkTarget" value="main">  
   <INPUT type="hidden" name="rs:Format" value="HTML4.0">  
   <INPUT type="submit" value="Button">  
</FORM>  
```  
  
 <span data-ttu-id="fc508-132">위의 예에서 사용자가 폼에 있는 단추를 클릭하면 보고서 서버가 현재 프레임에서 대상으로 지정된 HTML 렌더링 보고서를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="fc508-132">In the previous example, if a user clicks the button on the form, the report server returns an HTML-rendered report targeted at the current frame.</span></span> <span data-ttu-id="fc508-133">비슷한 URL 액세스 문자열은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="fc508-133">A comparable URL access string might look like the following:</span></span>  
  
```  
http://server/reportserver?/SampleReports/Territory Sales   
Drilldown&rs:Command=Render&rc:LinkTarget=main&rs:Format=HTML4.0  
```  
  
## <a name="see-also"></a><span data-ttu-id="fc508-134">참고 항목</span><span class="sxs-lookup"><span data-stu-id="fc508-134">See Also</span></span>  
 <span data-ttu-id="fc508-135">[응용 프로그램에 Reporting Services 통합](../application-integration/integrating-reporting-services-into-applications.md) </span><span class="sxs-lookup"><span data-stu-id="fc508-135">[Integrating Reporting Services into Applications](../application-integration/integrating-reporting-services-into-applications.md) </span></span>  
 <span data-ttu-id="fc508-136">[URL 액세스를 사용 하 여 Reporting Services 통합](integrating-reporting-services-using-url-access.md) </span><span class="sxs-lookup"><span data-stu-id="fc508-136">[Integrating Reporting Services Using URL Access](integrating-reporting-services-using-url-access.md) </span></span>  
 <span data-ttu-id="fc508-137">[Windows 응용 프로그램에서 URL 액세스 사용](integrating-reporting-services-using-url-access-windows-application.md) </span><span class="sxs-lookup"><span data-stu-id="fc508-137">[Using URL Access in a Windows Application](integrating-reporting-services-using-url-access-windows-application.md) </span></span>  
 [<span data-ttu-id="fc508-138">URL 액세스&#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="fc508-138">URL Access &#40;SSRS&#41;</span></span>](../url-access-ssrs.md)  
  
  
