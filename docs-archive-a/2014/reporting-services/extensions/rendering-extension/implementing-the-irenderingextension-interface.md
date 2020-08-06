---
title: IRenderingExtension 인터페이스 구현 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- IRenderingExtension interface
- rendering extensions [Reporting Services], IRenderingExtension interface
ms.assetid: 74b2f2b7-6796-42da-ab7d-b05891ad4001
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f57c4aa41ccfed165b69581cbf3917e4dfbb4960
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651527"
---
# <a name="implementing-the-irenderingextension-interface"></a><span data-ttu-id="87da7-102">IRenderingExtension 인터페이스 구현</span><span class="sxs-lookup"><span data-stu-id="87da7-102">Implementing the IRenderingExtension Interface</span></span>
  <span data-ttu-id="87da7-103">렌더링 확장 프로그램은 실제 데이터와 결합된 보고서 정의에서 결과를 가져오고 결과 데이터를 사용 가능한 형식으로 렌더링합니다.</span><span class="sxs-lookup"><span data-stu-id="87da7-103">The rendering extension takes the results from a report definition that is combined with the actual data and renders the resulting data to a format that is useable.</span></span> <span data-ttu-id="87da7-104">결합된 데이터의 변환과 형식 지정은 <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension>을 구현하는 CLR(공용 언어 런타임) 클래스를 사용하여 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="87da7-104">The transformation of the combined data and formatting is done by using a common language runtime (CLR) class that implements <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension>.</span></span> <span data-ttu-id="87da7-105">이것은 개체 모델을 뷰어, 프린터 또는 기타 출력 대상에서 사용할 수 있는 출력 형식으로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="87da7-105">This transforms the object model into an output format that is consumable by a viewer, printer, or other output target.</span></span>  
  
 <span data-ttu-id="87da7-106"><xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension>에는 코딩해야 하는 메서드가 세 개 있습니다.</span><span class="sxs-lookup"><span data-stu-id="87da7-106">The <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension> has three methods that must be coded:</span></span>  
  
-   <span data-ttu-id="87da7-107"><xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.Render%2A> - 보고서를 렌더링합니다.</span><span class="sxs-lookup"><span data-stu-id="87da7-107"><xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.Render%2A> - renders the report.</span></span>  
  
-   <span data-ttu-id="87da7-108"><xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.RenderStream%2A> - 보고서에서 특정 스트림을 렌더링합니다.</span><span class="sxs-lookup"><span data-stu-id="87da7-108"><xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.RenderStream%2A> - renders a specific stream from the report.</span></span>  
  
-   <span data-ttu-id="87da7-109"><xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.GetRenderingResource%2A> - 보고서에 필요한 추가 정보(예: 아이콘)를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="87da7-109"><xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.GetRenderingResource%2A> - gets additional information, such as icons, that are required for the report.</span></span>  
  
 <span data-ttu-id="87da7-110">다음 섹션에서는 이러한 메서드에 대해 자세히 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="87da7-110">The following sections discuss these methods in more detail.</span></span>  
  
## <a name="render-method"></a><span data-ttu-id="87da7-111">Render 메서드</span><span class="sxs-lookup"><span data-stu-id="87da7-111">Render Method</span></span>  
 <span data-ttu-id="87da7-112"><xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.Render%2A> 메서드에는 다음 개체를 나타내는 인수가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="87da7-112">The <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.Render%2A> method contains arguments that represent the following objects:</span></span>  
  
-   <span data-ttu-id="87da7-113">렌더링할 *보고서* 자체.</span><span class="sxs-lookup"><span data-stu-id="87da7-113">The *report* that you want to render.</span></span> <span data-ttu-id="87da7-114">이 개체에는 보고서에 대한 속성, 데이터 및 레이아웃 정보가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="87da7-114">This object contains properties, data, and layout information for the report.</span></span> <span data-ttu-id="87da7-115">보고서는 보고서 개체 모델 트리의 루트입니다.</span><span class="sxs-lookup"><span data-stu-id="87da7-115">The report is the root of the report object model tree.</span></span>  
  
-   <span data-ttu-id="87da7-116">보고서 서버에 대한 매개 변수(있는 경우)와 함께 문자열 사전 개체를 포함하는 *ServerParameters*.</span><span class="sxs-lookup"><span data-stu-id="87da7-116">The *ServerParameters* that contain the string dictionary object, with the parameters for the report server, if any.</span></span>  
  
-   <span data-ttu-id="87da7-117">디바이스 설정을 포함하는 *deviceInfo* 매개 변수.</span><span class="sxs-lookup"><span data-stu-id="87da7-117">The *deviceInfo* parameter that contain the device settings.</span></span> <span data-ttu-id="87da7-118">자세한 내용은 [디바이스 정보 설정을 렌더링 확장 프로그램에 전달](../../report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="87da7-118">For more information, see [Passing Device Information Settings to Rendering Extensions](../../report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md).</span></span>  
  
-   <span data-ttu-id="87da7-119">렌더링하는 클라이언트에 대한 정보가 들어 있는 <xref:System.Collections.Specialized.NameValueCollection> 사전 개체를 포함하는 *clientCapabilities* 매개 변수.</span><span class="sxs-lookup"><span data-stu-id="87da7-119">The *clientCapabilities* parameter that contains a <xref:System.Collections.Specialized.NameValueCollection> dictionary object that has information about the client to which you are rendering.</span></span>  
  
-   <span data-ttu-id="87da7-120">렌더링 결과에 대한 정보가 들어 있는 *RenderProperties*.</span><span class="sxs-lookup"><span data-stu-id="87da7-120">The *RenderProperties* that contains information about the rendering result.</span></span>  
  
-   <span data-ttu-id="87da7-121">*createAndRegisterStream*은 렌더링할 스트림을 가져오기 위해 호출되는 대리자 함수입니다.</span><span class="sxs-lookup"><span data-stu-id="87da7-121">The *createAndRegisterStream* is a delegate function to be called to get a stream to render into.</span></span>  
  
### <a name="deviceinfo-parameter"></a><span data-ttu-id="87da7-122">deviceInfo 매개 변수</span><span class="sxs-lookup"><span data-stu-id="87da7-122">deviceInfo Parameter</span></span>  
 <span data-ttu-id="87da7-123">*deviceInfo* 매개 변수에는 보고서 매개 변수가 아니라 렌더링 매개 변수가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="87da7-123">The *deviceInfo* parameter contains rendering parameters, not report parameters.</span></span> <span data-ttu-id="87da7-124">이러한 렌더링 매개 변수는 렌더링 확장 프로그램에 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="87da7-124">These rendering parameters are passed to the rendering extension.</span></span> <span data-ttu-id="87da7-125">*deviceInfo* 값은 보고서 서버에서 <xref:System.Collections.Specialized.NameValueCollection> 개체로 변환됩니다.</span><span class="sxs-lookup"><span data-stu-id="87da7-125">The *deviceInfo* values are converted into a <xref:System.Collections.Specialized.NameValueCollection> object by the report server.</span></span> <span data-ttu-id="87da7-126">*deviceInfo* 매개 변수의 항목은 대소문자를 구분하지 않는 값으로 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="87da7-126">Items in the *deviceInfo* parameter are treated as case-insensitive values.</span></span> <span data-ttu-id="87da7-127">렌더링 요청이 URL 액세스 결과로 이루어진 경우 `rc:key=value` 형식의 URL 매개 변수가 *deviceInfo* 사전 개체의 키/값 쌍으로 변환됩니다.</span><span class="sxs-lookup"><span data-stu-id="87da7-127">If the render request came as a result of URL access, the URL parameters in the form `rc:key=value` are converted to key/value pairs in the *deviceInfo* dictionary object.</span></span> <span data-ttu-id="87da7-128">브라우저 감지 코드는 *clientCapabilities* 사전에 EcmaScriptVersion, JavaScript, MajorVersion, MinorVersion, Win32, Type 및 AcceptLanguage 항목을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="87da7-128">The browser detection code also provides the following items in the *clientCapabilities* dictionary: EcmaScriptVersion, JavaScript, MajorVersion, MinorVersion, Win32, Type, and AcceptLanguage.</span></span> <span data-ttu-id="87da7-129">렌더링 확장 프로그램에서 인식할 수 없는 *deviceInfo* 매개 변수의 이름/값 쌍은 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="87da7-129">Any name/value pair in the *deviceInfo* parameter that is not understood by the rendering extension is ignored.</span></span> <span data-ttu-id="87da7-130">다음 코드 예제는 아이콘을 검색하는 예제 <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.GetRenderingResource%2A> 메서드를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="87da7-130">The following code sample shows a sample <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.GetRenderingResource%2A> method that retrieves icons:</span></span>  
  
```csharp  
public void GetRenderingResource (CreateStream createStreamCallback, NameValueCollection deviceInfo)  
{  
    string[] iconTagValues = deviceInfo.GetValues("Icon");  
    if ((iconTagValues != null) && (iconTagValues.Length > 0) )  
    {  
        // Create a stream to output to.  
        Stream outputStream = createStreamCallback(m_iconResourceName, "gif", null, "image/gif", false);  
        // Get the GIF image for one of the buttons on the toolbar  
        Image requiredImage = (Image) m_resourcemanager.GetObject(m_iconResourceName  
        // Write the image to the output stream  
        requiredImage.Save(outputStream, requiredImage.RawFormat);  
    }  
    return;  
}  
```  
  
## <a name="renderstream-method"></a><span data-ttu-id="87da7-131">RenderStream 메서드</span><span class="sxs-lookup"><span data-stu-id="87da7-131">RenderStream Method</span></span>  
 <span data-ttu-id="87da7-132"><xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.RenderStream%2A> 메서드는 보고서에서 특정 스트림을 렌더링합니다.</span><span class="sxs-lookup"><span data-stu-id="87da7-132">The <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.RenderStream%2A> method renders a particular stream from the report.</span></span> <span data-ttu-id="87da7-133">모든 스트림은 최초 <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.Render%2A> 호출 중에 만들어지지만, 이 스트림이 처음에 클라이언트에 반환되지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="87da7-133">All streams are created during the initial <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.Render%2A> call, but the streams are not returned to the client initially.</span></span> <span data-ttu-id="87da7-134">이 메서드는 보조 스트림(예: HTML 렌더링의 이미지) 또는 다중 페이지 렌더링 확장 프로그램의 추가 페이지(예: 이미지/EMF)에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="87da7-134">This method is used for secondary streams, such as images in HTML rendering, or additional pages of a multi-page rendering extension, such as Image/EMF.</span></span>  
  
## <a name="getrenderingresource-method"></a><span data-ttu-id="87da7-135">GetRenderingResource 메서드</span><span class="sxs-lookup"><span data-stu-id="87da7-135">GetRenderingResource Method</span></span>  
 <span data-ttu-id="87da7-136"><xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.GetRenderingResource%2A> 메서드는 보고서의 전체 렌더링을 실행하지 않고 정보를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="87da7-136">The <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.GetRenderingResource%2A> method retrieves the information without executing an entire rendering of the report.</span></span> <span data-ttu-id="87da7-137">보고서에서 보고서 자체가 렌더링되지 않아도 되는 정보가 필요할 때가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="87da7-137">There are times when the report requires information that does not require the report itself to be rendered.</span></span> <span data-ttu-id="87da7-138">예를 들어 렌더링 확장 프로그램과 연결 된 아이콘이 필요한 경우 단일 태그를 포함 하는 *deviceInfo* 매개 변수를 사용 합니다 **\<Icon>** .</span><span class="sxs-lookup"><span data-stu-id="87da7-138">For example, if you need the icon associated with the rendering extension, use the *deviceInfo* parameter containing the single tag **\<Icon>**.</span></span> <span data-ttu-id="87da7-139">이러한 경우 <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.GetRenderingResource%2A> 메서드를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="87da7-139">In these cases, you can use the <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.GetRenderingResource%2A> method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87da7-140">참고 항목</span><span class="sxs-lookup"><span data-stu-id="87da7-140">See Also</span></span>  
 <span data-ttu-id="87da7-141">[렌더링 확장 프로그램 구현](implementing-a-rendering-extension.md) </span><span class="sxs-lookup"><span data-stu-id="87da7-141">[Implementing a Rendering Extension](implementing-a-rendering-extension.md) </span></span>  
 [<span data-ttu-id="87da7-142">렌더링 확장 프로그램 개요</span><span class="sxs-lookup"><span data-stu-id="87da7-142">Rendering Extensions Overview</span></span>](rendering-extensions-overview.md)  
  
  
