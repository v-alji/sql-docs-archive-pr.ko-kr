---
title: 디바이스 정보 설정을 렌더링 확장 프로그램에 전달 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- device information settings [Reporting Services]
- Render method
- Report Server Web service, device information settings
- Web service [Reporting Services], device information settings
- XML Web service [Reporting Services], device information settings
- passing device information [Reporting Services]
- rendering extensions [Reporting Services], device information settings
- rendering [Reporting Services], settings
- device information settings [Reporting Services], about device information settings
- extensions [Reporting Services], device information settings
ms.assetid: fe718939-7efe-4c7f-87cb-5f5b09caeff4
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ea50de3955ab152cbd92d5fd50ef8b2281a67eb7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730131"
---
# <a name="passing-device-information-settings-to-rendering-extensions"></a><span data-ttu-id="abf5f-102">디바이스 정보 설정을 렌더링 확장 프로그램에 전달</span><span class="sxs-lookup"><span data-stu-id="abf5f-102">Passing Device Information Settings to Rendering Extensions</span></span>
  <span data-ttu-id="abf5f-103">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]에서 디바이스 정보 설정을 사용하여 렌더링 매개 변수를 렌더링 확장 프로그램으로 전달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="abf5f-103">In [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], device information settings are used to pass rendering parameters to a rendering extension.</span></span> <span data-ttu-id="abf5f-104">보고서 서버 웹 서비스의 설정이 **DeviceInfo** XML 요소로 전달되고 보고서 서버에서 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="abf5f-104">Settings in the Report Server Web service are passed as a **DeviceInfo** XML element and processed by the report server.</span></span> <span data-ttu-id="abf5f-105">디바이스 정보 설정은 기본값을 가지므로 렌더링 프로세스에서 선택적 인수로 간주됩니다.</span><span class="sxs-lookup"><span data-stu-id="abf5f-105">Because device information settings have default values, they are considered optional arguments in the rendering process.</span></span> <span data-ttu-id="abf5f-106">그러나 디바이스 정보 설정을 사용하여 렌더링을 사용자 지정하고 서버에서 공급한 기본값을 무효화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="abf5f-106">However, you can use device information settings to customize rendering and to override the default values that are supplied by the server.</span></span>  
  
 <span data-ttu-id="abf5f-107">다양한 방법으로 디바이스 정보 설정을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="abf5f-107">You can specify device information settings in a variety of ways.</span></span> <span data-ttu-id="abf5f-108">프로그래밍 방식에서는 Render 메서드를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="abf5f-108">Programmatically, you can use the Render method.</span></span> <span data-ttu-id="abf5f-109">URL을 통해 보고서에 액세스하는 경우 디바이스 정보를 URL 매개 변수로 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="abf5f-109">If you are accessing a report through its URL, you can specify device information as URL parameters.</span></span> <span data-ttu-id="abf5f-110">또한 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 구성 파일에서 디바이스 정보 설정을 편집하여 렌더링 매개 변수를 전역으로 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="abf5f-110">You can also edit the device information settings in the [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] configuration files to specify rendering parameters globally.</span></span> <span data-ttu-id="abf5f-111">렌더링 매개 변수를 전역으로 지정하는 방법에 대한 자세한 내용은 [RSReportServer.Config의 렌더링 확장 프로그램 매개 변수 사용자 지정](../../customize-rendering-extension-parameters-in-rsreportserver-config.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="abf5f-111">For more information about specifying rendering parameters globally, see [Customize Rendering Extension Parameters in RSReportServer.Config](../../customize-rendering-extension-parameters-in-rsreportserver-config.md).</span></span>  
  
## <a name="passing-device-information-using-the-render-method"></a><span data-ttu-id="abf5f-112">Render 메서드를 사용하여 디바이스 정보 전달</span><span class="sxs-lookup"><span data-stu-id="abf5f-112">Passing Device Information Using the Render Method</span></span>  
 <span data-ttu-id="abf5f-113">디바이스 정보 설정을 렌더링 확장 프로그램으로 전달하려면 <xref:ReportExecution2005.ReportExecutionService.Render%2A> 메서드를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="abf5f-113">To pass device information settings to a rendering extension, use the <xref:ReportExecution2005.ReportExecutionService.Render%2A> method.</span></span> <span data-ttu-id="abf5f-114">예를 들어, 다음 XML 문자열을 <xref:ReportExecution2005.ReportExecutionService.Render%2A> 메서드로 전달하여 HTML에 렌더링할 때 HTML 조각을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="abf5f-114">For example, the following XML string can be passed to the <xref:ReportExecution2005.ReportExecutionService.Render%2A> method to create an HTML fragment when rendering to HTML.</span></span>  
  
```  
<DeviceInfo>  
   <HTMLFragment>True</HTMLFragment>  
</DeviceInfo>  
```  
  
 <span data-ttu-id="abf5f-115">보고서가 HTML 조각으로 렌더링되면 HTML 또는 BODY 요소를 사용하지 않고 TABLE 요소 안에 보고서의 내용이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="abf5f-115">When a report is rendered as an HTML fragment, the content of the report is contained within a TABLE element without the use of an HTML or BODY element.</span></span> <span data-ttu-id="abf5f-116">HTML 조각을 사용하여 보고서를 기존 HTML 문서로 통합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="abf5f-116">You can use the HTML fragment to incorporate the report into an existing HTML document.</span></span> <span data-ttu-id="abf5f-117">HTML 출력용 디바이스 정보 설정에 대한 자세한 내용은 [HTML Device Information Settings](../../html-device-information-settings.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="abf5f-117">For more information about device information settings for HTML output, see [HTML Device Information Settings](../../html-device-information-settings.md).</span></span>  
  
## <a name="passing-device-information-using-url-access"></a><span data-ttu-id="abf5f-118">URL 액세스를 사용하여 디바이스 정보 전달</span><span class="sxs-lookup"><span data-stu-id="abf5f-118">Passing Device Information Using URL Access</span></span>  
 <span data-ttu-id="abf5f-119">URL 액세스를 통해서도 디바이스 정보 설정을 전달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="abf5f-119">You can also pass device information settings through URL access.</span></span> <span data-ttu-id="abf5f-120">디바이스 정보 설정이 URL 매개 변수로 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="abf5f-120">Device information settings are passed as URL parameters.</span></span> <span data-ttu-id="abf5f-121">다음 URL 액세스 문자열을 보고서 서버로 전달하여 HTML 뷰어 도구 모음 없이 렌더링된 보고서를 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="abf5f-121">The following URL access string can be passed to the report server to generate a rendered report without the HTML viewer toolbar.</span></span>  
  
```  
http://<Server Name>/reportserver?/SampleReports/Sales Order Detail&rs:Command=Render&rs:Format=HTML4.0&rc:Toolbar=False  
```  
  
 <span data-ttu-id="abf5f-122">자세한 내용은 [URL에 디바이스 정보 설정 지정](../../specify-device-information-settings-in-a-url.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="abf5f-122">For more information, see [Specify Device Information Settings in a URL](../../specify-device-information-settings-in-a-url.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abf5f-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="abf5f-123">See Also</span></span>  
 <span data-ttu-id="abf5f-124">[Reporting Services&#41;&#40;렌더링 확장 프로그램에 대 한 장치 정보 설정](../../device-information-settings-for-rendering-extensions-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="abf5f-124">[Device Information Settings for Rendering Extensions &#40;Reporting Services&#41;](../../device-information-settings-for-rendering-extensions-reporting-services.md) </span></span>  
 <span data-ttu-id="abf5f-125">[RSReportServer.Config에서 렌더링 확장 프로그램 매개 변수 사용자 지정](../../customize-rendering-extension-parameters-in-rsreportserver-config.md) </span><span class="sxs-lookup"><span data-stu-id="abf5f-125">[Customize Rendering Extension Parameters in RSReportServer.Config](../../customize-rendering-extension-parameters-in-rsreportserver-config.md) </span></span>  
 [<span data-ttu-id="abf5f-126">웹 서비스와 .NET Framework를 사용하여 애플리케이션 빌드</span><span class="sxs-lookup"><span data-stu-id="abf5f-126">Building Applications Using the Web Service and the .NET Framework</span></span>](building-applications-using-the-web-service-and-the-net-framework.md)  
  
  
