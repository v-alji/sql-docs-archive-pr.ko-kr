---
title: 렌더링 확장 프로그램 배포 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- deploying [Reporting Services], extensions
- rendering extensions [Reporting Services], deploying
ms.assetid: 9fb8c887-5cb2-476e-895a-7b0e2dd11398
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d1c70d9cdc947134c682132b0baea02274ddf4b7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651530"
---
# <a name="deploying-a-rendering-extension"></a><span data-ttu-id="472b6-102">렌더링 확장 프로그램 배포</span><span class="sxs-lookup"><span data-stu-id="472b6-102">Deploying a Rendering Extension</span></span>
  <span data-ttu-id="472b6-103">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 보고서 렌더링 확장 프로그램을 작성하고 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 라이브러리에 컴파일한 후에는 보고서 서버 및 보고서 디자이너에서 이를 찾을 수 있도록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="472b6-103">After you have written and compiled your [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] report rendering extension into a [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] library, you need to make it discoverable by the report server and by Report Designer.</span></span> <span data-ttu-id="472b6-104">이 작업을 수행하려면 확장 프로그램을 적절한 디렉터리에 복사하고 해당하는 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 구성 파일에 항목을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="472b6-104">To do so, copy the extension to the appropriate directory and add entries to the appropriate [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] configuration files.</span></span>  
  
## <a name="configuration-file-rendering-extension-element"></a><span data-ttu-id="472b6-105">구성 파일 렌더링 확장 프로그램 요소</span><span class="sxs-lookup"><span data-stu-id="472b6-105">Configuration File Rendering Extension Element</span></span>  
 <span data-ttu-id="472b6-106">렌더링 확장 프로그램이 .DLL로 컴파일되었으면 항목을 rsreportserver.config 파일에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="472b6-106">Once a rendering extension has been compiled into a .DLL, you add an entry into the rsreportserver.config file.</span></span> <span data-ttu-id="472b6-107">기본적으로이 위치 는%ProgramFiles%\Microsoft SQL Server \ MSRS10_50입니다. \<InstanceName> \Reporting Services\reportserver</span><span class="sxs-lookup"><span data-stu-id="472b6-107">By default, the location is %ProgramFiles%\Microsoft SQL Server\MSRS10_50.\<InstanceName>\Reporting Services\ReportServer.</span></span> <span data-ttu-id="472b6-108">부모 요소가 \<Render>인 경우</span><span class="sxs-lookup"><span data-stu-id="472b6-108">The parent element is \<Render>.</span></span> <span data-ttu-id="472b6-109">Render 요소 아래에 각 렌더링 확장 프로그램에 대한 Extension 요소가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="472b6-109">Under the Render element is an Extension element for each rendering extension.</span></span> <span data-ttu-id="472b6-110">`Extension` 요소에는 Name 및 Type의 두 가지 특성이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="472b6-110">The `Extension` element contains two attributes, Name and Type.</span></span>  
  
 <span data-ttu-id="472b6-111">다음 표에서는 `Extension` 렌더링 확장 프로그램의 요소에 대 한 특성을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="472b6-111">The following table describes the attributes for the `Extension` element for rendering extensions:</span></span>  
  
|<span data-ttu-id="472b6-112">attribute</span><span class="sxs-lookup"><span data-stu-id="472b6-112">Attribute</span></span>|<span data-ttu-id="472b6-113">Description</span><span class="sxs-lookup"><span data-stu-id="472b6-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="472b6-114">**이름**</span><span class="sxs-lookup"><span data-stu-id="472b6-114">**Name**</span></span>|<span data-ttu-id="472b6-115">확장 프로그램의 고유한 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="472b6-115">A unique name for the extension.</span></span> <span data-ttu-id="472b6-116">**Name** 특성의 최대 길이는 255자입니다.</span><span class="sxs-lookup"><span data-stu-id="472b6-116">The maximum length for the **Name** attribute is 255 characters.</span></span> <span data-ttu-id="472b6-117">이름은 구성 파일의 **Extensions** 요소 내 모든 항목에서 고유해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="472b6-117">The name must be unique among all entries within the **Extensions** element of a configuration file.</span></span> <span data-ttu-id="472b6-118">중복된 이름이 있을 경우 보고서 서버에서 오류를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="472b6-118">If a duplicate name is present, the report server returns an error.</span></span>|  
|<span data-ttu-id="472b6-119">**형식**</span><span class="sxs-lookup"><span data-stu-id="472b6-119">**Type**</span></span>|<span data-ttu-id="472b6-120">정규화된 네임스페이스와 어셈블리 이름을 포함하는 쉼표로 구분된 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="472b6-120">A comma-separated list that includes the fully qualified namespace along with the name of the assembly.</span></span>|  
|<span data-ttu-id="472b6-121">**Visible**</span><span class="sxs-lookup"><span data-stu-id="472b6-121">**Visible**</span></span>|<span data-ttu-id="472b6-122">`false` 값은 렌더링 확장 프로그램이 사용자 인터페이스에 표시되지 않음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="472b6-122">A value of `false` indicates that the rendering extension should not be visible in user interfaces.</span></span> <span data-ttu-id="472b6-123">이 특성이 포함되지 않을 경우 기본값은 `true`입니다.</span><span class="sxs-lookup"><span data-stu-id="472b6-123">If the attribute is not included, the default value is `true`.</span></span>|  
|<span data-ttu-id="472b6-124">**LogAllExecutionRequests**</span><span class="sxs-lookup"><span data-stu-id="472b6-124">**LogAllExecutionRequests**</span></span>|<span data-ttu-id="472b6-125">`false` 값은 세션의 첫 번째 보고서 실행에 대해서만 로그 항목이 기록됨을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="472b6-125">A value of `false` indicates that an entry is logged for only the first report execution in a session.</span></span> <span data-ttu-id="472b6-126">이 특성이 포함되지 않을 경우 기본값은 `true`입니다.</span><span class="sxs-lookup"><span data-stu-id="472b6-126">If the attribute is not included, the default value is `true`.</span></span><br /><br /> <span data-ttu-id="472b6-127">예를 들어 이 설정은 보고서에서 렌더링되는 첫 페이지에 대해서만 로그 항목을 기록할지(`false`인 경우) 또는 보고서에서 렌더링되는 각 페이지에 대해 로그 항목을 기록할지(`true`인 경우) 여부를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="472b6-127">For example, this setting determines whether to log an entry for only the first page rendered in a report (when `false`) or an entry for each page rendered in the report (when `true`).</span></span>|  
  
 <span data-ttu-id="472b6-128">자세한 내용은 [RSReportServer Configuration File](../../report-server/rsreportserver-config-configuration-file.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="472b6-128">For more information, see [RSReportServer Configuration File](../../report-server/rsreportserver-config-configuration-file.md).</span></span>  
  
## <a name="deploying-the-extension-to-the-report-server"></a><span data-ttu-id="472b6-129">보고서 서버에 확장 프로그램 배포</span><span class="sxs-lookup"><span data-stu-id="472b6-129">Deploying the Extension to the Report Server</span></span>  
 <span data-ttu-id="472b6-130">보고서 서버에서는 보고서를 다른 형식으로 내보내기 위해 렌더링 확장 프로그램을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="472b6-130">The report server uses rendering extensions to export reports to other formats.</span></span> <span data-ttu-id="472b6-131">렌더링 확장 프로그램 어셈블리를 프라이빗 어셈블리 형태로 보고서 서버에 배포해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="472b6-131">You should deploy your rendering extension assembly to the report server as a private assembly.</span></span> <span data-ttu-id="472b6-132">또한 보고서 서버 구성 파일 rsreportserver.config에서 항목을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="472b6-132">You also need to make an entry in the report server configuration file, rsreportserver.config.</span></span>  
  
### <a name="to-deploy-the-assembly"></a><span data-ttu-id="472b6-133">어셈블리를 배포하려면</span><span class="sxs-lookup"><span data-stu-id="472b6-133">To deploy the assembly</span></span>  
  
1.  <span data-ttu-id="472b6-134">준비 위치에서 렌더링 확장 프로그램을 사용할 보고서 서버의 bin 디렉터리로 어셈블리를 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="472b6-134">Copy your assembly from your staging location to the bin directory of the report server on which you want to use the rendering extension.</span></span> <span data-ttu-id="472b6-135">보고서 서버 Bin 디렉터리의 기본 위치 는%ProgramFiles%\Microsoft SQL Server \ MSRS10_50입니다. \<InstanceName> \Reporting Services\reportserver\bin입니다.</span><span class="sxs-lookup"><span data-stu-id="472b6-135">The default location of the report server Bin directory is %ProgramFiles%\Microsoft SQL Server\MSRS10_50.\<InstanceName>\Reporting Services\ReportServer\Bin.</span></span>  
  
2.  <span data-ttu-id="472b6-136">어셈블리 파일이 복사된 후 rsreportserver.config 파일을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="472b6-136">After the assembly file is copied, open the rsreportserver.config file.</span></span> <span data-ttu-id="472b6-137">rsreportserver.config 파일도 보고서 서버 bin 디렉터리에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="472b6-137">The rsreportserver.config file is also located in the report server bin directory.</span></span> <span data-ttu-id="472b6-138">구성 파일에서 확장 프로그램 어셈블리 파일에 대한 항목을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="472b6-138">You need to make an entry in the configuration file for your extension assembly file.</span></span> <span data-ttu-id="472b6-139">이 파일은 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 또는 간단한 텍스트 편집기에서 열 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="472b6-139">You can open the file with [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] or a simple text editor.</span></span>  
  
     <span data-ttu-id="472b6-140">자세한 내용은 [RSReportServer Configuration File](../../report-server/rsreportserver-config-configuration-file.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="472b6-140">For more information, see [RSReportServer Configuration File](../../report-server/rsreportserver-config-configuration-file.md).</span></span>  
  
3.  <span data-ttu-id="472b6-141">Rsreportserver.config 파일에서 **Render** 요소를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="472b6-141">Locate the **Render** element in the Rsreportserver.config file.</span></span> <span data-ttu-id="472b6-142">새로 만든 확장 프로그램에 대한 항목이 다음 위치에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="472b6-142">An entry for your newly created extension should be made in the following location:</span></span>  
  
    ```  
    <Extensions>  
       <Render>  
          <extension configuration>  
       </Render>  
    </Extensions>  
    ```  
  
4.  <span data-ttu-id="472b6-143">렌더링 확장 프로그램에 대한 항목을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="472b6-143">Add an entry for your rendering extension.</span></span> <span data-ttu-id="472b6-144">항목에 **Name** 및 **Type**에 대한 값이 있는 요소가 포함되어야 하며 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="472b6-144">Your entry should include an element that has values for **Name** and **Type**, and might look like the following:</span></span>  
  
    ```  
    <Extension Name="My Rendering Extension Name" Type="CompanyName.ExtensionName.MyRenderingProvider, AssemblyName" />  
    ```  
  
     <span data-ttu-id="472b6-145">**Name** 에 대한 값은 렌더링 확장 프로그램의 고유한 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="472b6-145">The value for **Name** is the unique name of the rendering extension.</span></span> <span data-ttu-id="472b6-146">**Type**의 값은 <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension> 구현의 정규화된 네임스페이스에 대한 항목과 그 다음에 어셈블리의 이름(.dll 파일 확장명 포함 안 함)이 따라오는 형태가 포함되며 쉼표로 구분된 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="472b6-146">The value for **Type** is a comma-separated list that includes an entry for the fully qualified namespace of your <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension> implementation, followed by the name of your assembly (not including the .dll file extension).</span></span> <span data-ttu-id="472b6-147">기본적으로 렌더링 확장 프로그램은 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="472b6-147">By default, rendering extensions are visible.</span></span> <span data-ttu-id="472b6-148">보고서 관리자와 같은 사용자 인터페이스에서 확장을 숨기려면 요소에 **표시 되** 는 특성을 추가 하 `Extension` 고로 설정 `false` 합니다.</span><span class="sxs-lookup"><span data-stu-id="472b6-148">To hide an extension from user interfaces, such as Report Manager, add a **Visible** attribute to the `Extension` element, and set it to `false`.</span></span>  
  
## <a name="verifying-the-deployment"></a><span data-ttu-id="472b6-149">배포 확인</span><span class="sxs-lookup"><span data-stu-id="472b6-149">Verifying the deployment</span></span>  
 <span data-ttu-id="472b6-150">보고서 관리자를 열고 확장 프로그램이 보고서에 대해 사용 가능한 내보내기 유형 목록에 포함되어 있는지 확인할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="472b6-150">You can also open Report Manager and verify that your extension is included in the list of available export types for a report.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="472b6-151">참고 항목</span><span class="sxs-lookup"><span data-stu-id="472b6-151">See Also</span></span>  
 <span data-ttu-id="472b6-152">[렌더링 확장 프로그램 구현](implementing-a-rendering-extension.md) </span><span class="sxs-lookup"><span data-stu-id="472b6-152">[Implementing a Rendering Extension](implementing-a-rendering-extension.md) </span></span>  
 <span data-ttu-id="472b6-153">[렌더링 확장 프로그램 개요](rendering-extensions-overview.md) </span><span class="sxs-lookup"><span data-stu-id="472b6-153">[Rendering Extensions Overview](rendering-extensions-overview.md) </span></span>  
 <span data-ttu-id="472b6-154">[IRenderingExtension 인터페이스 구현](implementing-the-irenderingextension-interface.md) </span><span class="sxs-lookup"><span data-stu-id="472b6-154">[Implementing the IRenderingExtension Interface](implementing-the-irenderingextension-interface.md) </span></span>  
 [<span data-ttu-id="472b6-155">확장에 대한 보안 고려 사항</span><span class="sxs-lookup"><span data-stu-id="472b6-155">Security Considerations for Extensions</span></span>](../security-considerations-for-extensions.md)  
  
  
