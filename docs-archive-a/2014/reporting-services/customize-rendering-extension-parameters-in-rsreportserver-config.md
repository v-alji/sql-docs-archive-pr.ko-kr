---
title: RSReportServer.Config의 렌더링 확장 프로그램 매개 변수를 사용자 지정 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- configuration options [Reporting Services]
- DeviceInfo settings
- rendering extensions [Reporting Services], overriding behaviors
- parameters [Reporting Services], report rendering
- overriding report rendering behavior
- extensions [Reporting Services], rendering
ms.assetid: 3bf7ab2b-70bb-41c8-acda-227994d15aed
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 35a01e12fa4016d03717b008e4241c3be5e55236
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741636"
---
# <a name="customize-rendering-extension-parameters-in-rsreportserverconfig"></a><span data-ttu-id="875de-102">RSReportServer.Config의 렌더링 확장 프로그램 매개 변수 사용자 지정</span><span class="sxs-lookup"><span data-stu-id="875de-102">Customize Rendering Extension Parameters in RSReportServer.Config</span></span>
  <span data-ttu-id="875de-103">RSReportServer 구성 파일에서 렌더링 확장 프로그램 매개 변수를 지정하여 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 보고서 서버에서 실행되는 보고서의 기본 보고서 렌더링 동작을 재정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="875de-103">You can specify rendering extension parameters in the RSReportServer configuration file to override default report rendering behavior for reports that run on a [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] report server.</span></span> <span data-ttu-id="875de-104">다음과 같은 목적으로 렌더링 확장 프로그램 매개 변수를 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="875de-104">You can modify rendering extension parameters to achieve the following objectives:</span></span>  
  
-   <span data-ttu-id="875de-105">보고서 도구 모음의 내보내기 목록에 렌더링 확장 프로그램 이름이 표시되는 방식을 변경하거나(예: "웹 보관 파일"을 "MHTML"로 변경) 이 이름을 기본 언어로 지역화합니다.</span><span class="sxs-lookup"><span data-stu-id="875de-105">Change how the rendering extension name appears in the Export list of the report toolbar (for example, to change "Web archive" to "MHTML"), or localize the name to a different language.</span></span>  
  
-   <span data-ttu-id="875de-106">같은 렌더링 확장 프로그램의 여러 인스턴스를 만들어 각기 다른 보고서 표시 옵션(예: 이미지 렌더링 확장 프로그램의 세로 및 가로 모드 버전)을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="875de-106">Create multiple instances of the same rendering extension to support different report presentation options (for example, a portrait and landscape mode version of the Image rendering extension).</span></span>  
  
-   <span data-ttu-id="875de-107">기본 렌더링 확장 프로그램 매개 변수를 다른 값으로 변경합니다. 예를 들어 이미지 렌더링 확장 프로그램에서 TIFF를 기본 출력 형식으로 사용하는 경우 EMF를 대신 사용하도록 확장 프로그램 매개 변수를 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="875de-107">Change the default rendering extension parameters to use different values (for example, the Image rendering extension uses TIFF as the default output format; you can modify the extension parameters to use EMF instead).</span></span>  
  
 <span data-ttu-id="875de-108">렌더링 확장 프로그램 매개 변수를 변경하면 보고서 서버의 렌더링 작업에만 영향이 미칩니다.</span><span class="sxs-lookup"><span data-stu-id="875de-108">Changing the rendering extension parameters only affects rendering operations on the report server.</span></span> <span data-ttu-id="875de-109">보고서 디자이너의 보고서 미리 보기에서는 렌더링 확장 프로그램 설정을 재정의할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="875de-109">You cannot override rendering extension settings in report preview in Report Designer.</span></span>  
  
 <span data-ttu-id="875de-110">구성 파일에서 렌더링 확장 프로그램 매개 변수를 지정하면 렌더링 확장 프로그램에 전체적으로 영향이 미칩니다.</span><span class="sxs-lookup"><span data-stu-id="875de-110">Specifying rendering extension parameters in the configuration files affects rendering extensions globally.</span></span> <span data-ttu-id="875de-111">특정 렌더링 확장 프로그램을 사용하는 경우 구성 파일의 설정이 기본값 대신 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="875de-111">The settings in the configuration files are used in place of default values whenever a particular rendering extension is used.</span></span> <span data-ttu-id="875de-112">특정 보고서 또는 렌더링 작업에 대한 렌더링 확장 프로그램 매개 변수를 설정하려면 <xref:ReportExecution2005.ReportExecutionService.Render%2A> 메서드를 사용하여 프로그래밍 방식으로 또는 보고서 URL에 디바이스 정보 설정을 지정하여 디바이스 정보를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="875de-112">If you want to set rendering extension parameters for a specific report or render operation, you must specify device information programmatically using the <xref:ReportExecution2005.ReportExecutionService.Render%2A> method or by specifying device information settings on a report URL.</span></span> <span data-ttu-id="875de-113">렌더링 작업에 대한 디바이스 정보 설정을 지정하고 전체 디바이스 정보 설정 목록을 보는 방법에 대한 자세한 내용은 [디바이스 정보 설정을 렌더링 확장 프로그램에 전달](report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="875de-113">For more information about specifying device information settings for a render operation, and to view the complete list of device information settings, see [Passing Device Information Settings to Rendering Extensions](report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md).</span></span>  
  
## <a name="finding-and-modifying-rsreportserverconfig"></a><span data-ttu-id="875de-114">RSReportServer.config 찾기 및 수정</span><span class="sxs-lookup"><span data-stu-id="875de-114">Finding and Modifying RSReportServer.config</span></span>  
 <span data-ttu-id="875de-115">보고서 출력 형식에 대한 구성 설정은 RSReportServer.config 파일에서 렌더링 확장 프로그램 매개 변수로 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="875de-115">Configuration settings for report output formats are specified as rendering extension parameters in the RSReportServer.config file.</span></span> <span data-ttu-id="875de-116">구성 파일에서 렌더링 확장 프로그램 매개 변수를 지정하려면 렌더링 매개 변수를 설정하는 XML 구조의 정의 방법을 알고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="875de-116">To specify rendering extension parameters in the configuration files, you must know how to define the XML structures that set rendering parameters.</span></span> <span data-ttu-id="875de-117">다음 두 가지 XML 구조를 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="875de-117">There are two XML structures that you can modify:</span></span>  
  
-   <span data-ttu-id="875de-118">`OverrideNames` 요소는 렌더링 확장 프로그램의 표시 이름과 언어를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="875de-118">The `OverrideNames` element defines the display name and language of the rendering extension.</span></span>  
  
-   <span data-ttu-id="875de-119">`DeviceInfo` XML 구조는 렌더링 확장 프로그램에서 사용하는 디바이스 정보 설정을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="875de-119">The `DeviceInfo` XML structure defines the device information settings that are used by a rendering extension.</span></span> <span data-ttu-id="875de-120">대부분의 렌더링 확장 프로그램 매개 변수는 디바이스 정보 설정으로 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="875de-120">Most rendering extension parameters are specified as device information settings.</span></span>  
  
 <span data-ttu-id="875de-121">이 파일은 텍스트 편집기를 사용하여 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="875de-121">You can use a text editor to modify the file.</span></span> <span data-ttu-id="875de-122">RSReportServer.config 파일은 \Reporting Services\Report Server\Bin 폴더에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="875de-122">The RSReportServer.config file can be found in the \Reporting Services\Report Server\Bin folder.</span></span> <span data-ttu-id="875de-123">구성 파일을 수정하는 방법에 대한 자세한 내용은 [Reporting Services 구성 파일 수정&#40;RSreportserver.config&#41;](report-server/modify-a-reporting-services-configuration-file-rsreportserver-config.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="875de-123">For more information about modifying configuration files, see [Modify a Reporting Services Configuration File &#40;RSreportserver.config&#41;](report-server/modify-a-reporting-services-configuration-file-rsreportserver-config.md).</span></span>  
  
## <a name="changing-the-display-name"></a><span data-ttu-id="875de-124">표시 이름 변경</span><span class="sxs-lookup"><span data-stu-id="875de-124">Changing the Display Name</span></span>  
 <span data-ttu-id="875de-125">렌더링 확장 프로그램의 표시 이름은 보고서 도구 모음의 내보내기 목록에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="875de-125">The display name for a rendering extension appears in the Export list of the report toolbar.</span></span> <span data-ttu-id="875de-126">기본 표시 이름의 예로는 웹 보관 파일, TIFF 파일 및 Acrobat(PDF) 파일이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="875de-126">Examples of default display names include Web archive, TIFF file, and Acrobat (PDF) file.</span></span> <span data-ttu-id="875de-127">구성 파일에서 `OverrideNames` 요소를 지정하여 기본 표시 이름을 사용자 지정 값으로 바꿀 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="875de-127">You can replace the default display name with a custom value by specifying the `OverrideNames` element in the configuration files.</span></span> <span data-ttu-id="875de-128">또한 단일 렌더링 확장 프로그램의 인스턴스를 두 개 정의하는 경우 `OverrideNames` 요소를 사용하여 내보내기 목록의 각 인스턴스를 구별할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="875de-128">In addition, if you are defining two instances of a single rendering extension, you can use the `OverrideNames` element to distinguish each instance in the Export list.</span></span>  
  
 <span data-ttu-id="875de-129">표시 이름은 지역화되므로 기본 표시 이름을 사용자 지정 값으로 바꿀 경우 `Language` 특성을 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="875de-129">Because display names are localized, you must set the `Language` attribute if you are replacing the default display name with a custom value.</span></span> <span data-ttu-id="875de-130">그렇지 않으면 사용자가 지정한 이름이 모두 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="875de-130">Otherwise, any name that you specify will be ignored.</span></span> <span data-ttu-id="875de-131">설정하는 언어 값은 보고서 서버 컴퓨터에 유효한 값이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="875de-131">The language value that you set must be valid for the report server computer.</span></span> <span data-ttu-id="875de-132">예를 들어 보고서 서버가 프랑스어 운영 체제에서 실행되고 있으면 "fr-FR"을 특성 값으로 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="875de-132">For example, if the report server is running on a French operating system, you should specify "fr-FR" as the attribute value.</span></span>  
  
 <span data-ttu-id="875de-133">다음 예에서는 영어 버전 보고서 서버에 사용자 지정 이름을 제공하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="875de-133">The following example illustrates how to provide a custom name on an English report server:</span></span>  
  
```  
<Extension Name="XML" Type="Microsoft.ReportingServices.Rendering.DataRenderer.XmlDataReport,Microsoft.ReportingServices.DataRendering">  
   <OverrideNames>  
     <Name Language="en-US">My Custom Display Name for XML Rendering</Name>  
   </OverrideNames>  
</Extension>  
```  
  
## <a name="changing-device-information-settings"></a><span data-ttu-id="875de-134">디바이스 정보 설정 변경</span><span class="sxs-lookup"><span data-stu-id="875de-134">Changing Device Information Settings</span></span>  
 <span data-ttu-id="875de-135">보고서 서버에 이미 배포된 렌더링 확장 프로그램에서 사용하는 기본 디바이스 정보 설정을 수정하려면 `DeviceInfo` XML 구조를 구성 파일에 입력해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="875de-135">To modify default device information settings that are used by a rendering extension that is already deployed on your report server, you must type the `DeviceInfo` XML structure into the configuration files.</span></span> <span data-ttu-id="875de-136">각 렌더링 확장 프로그램은 해당 확장 프로그램에 고유한 디바이스 정보 설정을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="875de-136">Every rendering extension supports device information settings that are unique to that extension.</span></span> <span data-ttu-id="875de-137">디바이스 정보 설정의 전체 목록을 보려면 [디바이스 정보 설정을 렌더링 확장 프로그램에 전달](report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="875de-137">To view the complete list of device information settings, see [Passing Device Information Settings to Rendering Extensions](report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md).</span></span>  
  
 <span data-ttu-id="875de-138">다음 예에서는 이미지 렌더링 확장 프로그램의 기본 설정을 수정하는 XML 구조와 구문을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="875de-138">The following example provides an illustration of the XML structure and syntax that modifies the default settings of the Image rendering extension:</span></span>  
  
```  
<Render>  
    <Extension Name="IMAGE (EMF)" Type="Microsoft.ReportingServices.Rendering.ImageRenderer.ImageRenderer,Microsoft.ReportingServices.ImageRendering">  
        <OverrideNames>  
            <Name Language="en-US">Image (EMF)</Name>  
        </OverrideNames>  
        <Configuration>  
            <DeviceInfo>  
                <ColorDepth>32</ColorDepth>  
                <DpiX>300</DpiX>  
                <DpiY>300</DpiY>  
                <OutputFormat>EMF</OutputFormat>  
            </DeviceInfo>  
        </Configuration>  
    </Extension>  
</Render>  
```  
  
## <a name="configuring-multiple-entries-for-a-rendering-extension"></a><span data-ttu-id="875de-139">렌더링 확장 프로그램에 대해 여러 개의 항목 구성</span><span class="sxs-lookup"><span data-stu-id="875de-139">Configuring Multiple Entries for a Rendering Extension</span></span>  
 <span data-ttu-id="875de-140">같은 렌더링 확장 프로그램의 인스턴스를 여러 개 만들어 각기 다른 보고서 표시 옵션을 지원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="875de-140">You can create multiple instances of the same rendering extension to support different report presentation options.</span></span> <span data-ttu-id="875de-141">정의한 인스턴스마다 여러 매개 변수 값 조합을 가질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="875de-141">Each instance that you define can have a different combination of parameter values.</span></span> <span data-ttu-id="875de-142">기존 렌더링 확장 프로그램의 새 인스턴스를 정의할 때는 다음을 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="875de-142">When defining new instances of an existing rendering extension, be sure to do the following:</span></span>  
  
-   <span data-ttu-id="875de-143">확장 프로그램에 고유 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="875de-143">Specify a unique name for the extension.</span></span>  
  
     <span data-ttu-id="875de-144">인스턴스마다 `Name` 특성에 대한 고유 값이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="875de-144">Each instance must have a unique value for the `Name` attribute.</span></span> <span data-ttu-id="875de-145">다음 예에서는 "IMAGE (EMF Landscape)" 및 "IMAGE (EMF Portrait)"라는 이름을 사용하여 두 인스턴스를 구별합니다.</span><span class="sxs-lookup"><span data-stu-id="875de-145">The following example uses the names "IMAGE (EMF Landscape)" and "IMAGE (EMF Portrait)" to distinguish between the two instances.</span></span>  
  
     <span data-ttu-id="875de-146">이미 배포된 렌더링 확장 프로그램의 이름을 변경하는 경우에는 주의하십시오.</span><span class="sxs-lookup"><span data-stu-id="875de-146">Use caution when changing the name of a rendering extension that is already deployed.</span></span> <span data-ttu-id="875de-147">프로그래밍 방식으로 렌더링 확장 프로그램을 지정하는 개발자는 이 확장 프로그램 이름을 사용하여 특정 렌더링 작업에 사용할 인스턴스를 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="875de-147">Developers who specify rendering extensions programmatically use the extension name to identify which instance to use for a particular render operation.</span></span> <span data-ttu-id="875de-148">보고서 서버에서 사용자 지정 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 애플리케이션을 실행하고 있는 경우 개발자는 사용자가 기존 확장 프로그램 이름을 수정하거나 새 확장 프로그램 이름을 추가할 경우 이를 알고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="875de-148">If you are running custom [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] applications on your report server, make sure that the developer knows if you modify an existing extension name or add a new one.</span></span>  
  
-   <span data-ttu-id="875de-149">사용자가 각 출력 형식의 차이를 이해할 수 있도록 고유한 표시 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="875de-149">Specify a unique display name so that users can understand the differences for each output format.</span></span>  
  
     <span data-ttu-id="875de-150">같은 확장 프로그램의 여러 버전을 구성하는 경우에는 `OverrideNames`에 값을 제공하여 각 버전에 고유한 이름을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="875de-150">If you are configuring multiple versions of the same extension, you can give each version a unique name by providing a value for `OverrideNames`.</span></span> <span data-ttu-id="875de-151">그렇지 않으면 확장 프로그램의 모든 버전이 보고서 도구 모음의 내보내기 옵션 목록에 같은 이름으로 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="875de-151">Otherwise, all versions of the extension will appear to have the same name in the Export options list on the report toolbar.</span></span>  
  
 <span data-ttu-id="875de-152">다음 예에서는 TIFF 출력을 생성하는 기본 이미지 렌더링 확장 프로그램을 사용하여 보고서를 세로 모드에서 EMF를 출력하고 동시에 두 번째 인스턴스에서는 가로 모드에서 EMF로 출력하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="875de-152">The following example illustrates how to use the default Image rendering extension (which produces TIFF output) to output EMF in Portrait mode alongside a second instance that outputs reports in EMF in Landscape mode.</span></span> <span data-ttu-id="875de-153">각 확장 프로그램 이름은 고유합니다.</span><span class="sxs-lookup"><span data-stu-id="875de-153">Notice that each extension name is unique.</span></span> <span data-ttu-id="875de-154">이 예를 테스트하려면 표시/숨기기 옵션, 행렬 또는 드릴스루 링크와 같은 대화형 기능이 포함되지 않은 보고서를 선택하십시오. 대화형 기능은 이미지 렌더링 확장 프로그램에서 작동하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="875de-154">When testing this example, remember to choose reports that do not contain interactive features such as show/hide options, matrices, or drillthrough links (interactive features do not work in the Image rendering extension):</span></span>  
  
```  
<Render>  
    <Extension Name="IMAGE (EMF Landscape)" Type="Microsoft.ReportingServices.Rendering.ImageRenderer.ImageRenderer,Microsoft.ReportingServices.ImageRendering">  
        <OverrideNames>  
            <Name Language="en-US">EMF in Landscape Mode</Name>  
        </OverrideNames>  
        <Configuration>  
            <DeviceInfo>  
                <OutputFormat>EMF</OutputFormat>  
                <PageHeight>8.5in</PageHeight>  
                <PageWidth>11in</PageWidth>  
            </DeviceInfo>  
        </Configuration>  
    </Extension>  
    <Extension Name="IMAGE (EMF Portrait)" Type="Microsoft.ReportingServices.Rendering.ImageRenderer.ImageRenderer,Microsoft.ReportingServices.ImageRendering">  
        <OverrideNames>  
            <Name Language="en-US">EMF in Portait Mode</Name>  
        </OverrideNames>  
        <Configuration>  
            <DeviceInfo>  
                <OutputFormat>EMF</OutputFormat>  
                <PageHeight>11in</PageHeight>  
                <PageWidth>8.5in</PageWidth>  
            </DeviceInfo>  
        </Configuration>  
    </Extension>  
</Render>  
```  
  
## <a name="see-also"></a><span data-ttu-id="875de-155">참고 항목</span><span class="sxs-lookup"><span data-stu-id="875de-155">See Also</span></span>  
 <span data-ttu-id="875de-156">[Rsreportserver.config 구성 파일](report-server/rsreportserver-config-configuration-file.md) </span><span class="sxs-lookup"><span data-stu-id="875de-156">[RSReportServer Configuration File](report-server/rsreportserver-config-configuration-file.md) </span></span>  
 <span data-ttu-id="875de-157">[RSReportDesigner 구성 파일](report-server/rsreportdesigner-configuration-file.md) </span><span class="sxs-lookup"><span data-stu-id="875de-157">[RSReportDesigner Configuration File](report-server/rsreportdesigner-configuration-file.md) </span></span>  
 <span data-ttu-id="875de-158">[CSV 디바이스 정보 설정](csv-device-information-settings.md) </span><span class="sxs-lookup"><span data-stu-id="875de-158">[CSV Device Information Settings](csv-device-information-settings.md) </span></span>  
 <span data-ttu-id="875de-159">[Excel 디바이스 정보 설정](excel-device-information-settings.md) </span><span class="sxs-lookup"><span data-stu-id="875de-159">[Excel Device Information Settings](excel-device-information-settings.md) </span></span>  
 <span data-ttu-id="875de-160">[HTML 디바이스 정보 설정](html-device-information-settings.md) </span><span class="sxs-lookup"><span data-stu-id="875de-160">[HTML Device Information Settings](html-device-information-settings.md) </span></span>  
 <span data-ttu-id="875de-161">[이미지 디바이스 정보 설정](image-device-information-settings.md) </span><span class="sxs-lookup"><span data-stu-id="875de-161">[Image Device Information Settings](image-device-information-settings.md) </span></span>  
 <span data-ttu-id="875de-162">[MHTML 디바이스 정보 설정](mhtml-device-information-settings.md) </span><span class="sxs-lookup"><span data-stu-id="875de-162">[MHTML Device Information Settings](mhtml-device-information-settings.md) </span></span>  
 <span data-ttu-id="875de-163">[PDF 디바이스 정보 설정](pdf-device-information-settings.md) </span><span class="sxs-lookup"><span data-stu-id="875de-163">[PDF Device Information Settings](pdf-device-information-settings.md) </span></span>  
 [<span data-ttu-id="875de-164">XML 디바이스 정보 설정</span><span class="sxs-lookup"><span data-stu-id="875de-164">XML Device Information Settings</span></span>](xml-device-information-settings.md)  
  
  
