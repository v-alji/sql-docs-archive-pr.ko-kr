---
title: 배달 확장 프로그램 배포 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- delivery extensions [Reporting Services], deploying
- Extension element
- deploying [Reporting Services], extensions
ms.assetid: 4436ce48-397d-42c7-9b5d-2a267e2a1b2c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f4a4e33266c8d3a27ce2a4ab5f568bdee349720f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661557"
---
# <a name="deploying-a-delivery-extension"></a><span data-ttu-id="18b9b-102">배달 확장 프로그램 배포</span><span class="sxs-lookup"><span data-stu-id="18b9b-102">Deploying a Delivery Extension</span></span>
  <span data-ttu-id="18b9b-103">배달 확장 프로그램은 XML 구성 파일 형식으로 구성 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="18b9b-103">Delivery extensions supply their configuration information in the form of an XML configuration file.</span></span> <span data-ttu-id="18b9b-104">XML 파일은 배달 확장 프로그램에 대해 정의된 XML 스키마를 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="18b9b-104">The XML file conforms to the XML schema defined for delivery extensions.</span></span> <span data-ttu-id="18b9b-105">배달 확장 프로그램은 구성 파일을 설정하고 수정하기 위한 인프라를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="18b9b-105">Delivery extensions provide infrastructure for setting and modifying the configuration file.</span></span>  
  
 <span data-ttu-id="18b9b-106">배달 확장 프로그램이 교체되거나 업그레이드되어도 배달 확장 프로그램을 참조하는 모든 구독은 유효합니다.</span><span class="sxs-lookup"><span data-stu-id="18b9b-106">If a delivery extension is replaced or upgraded, all subscriptions that reference the delivery extension remain valid.</span></span>  
  
 <span data-ttu-id="18b9b-107">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 배달 확장 프로그램을 작성하고 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 라이브러리에 컴파일한 후 확장 프로그램을 적절한 디렉터리에 복사하고 해당하는 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 구성 파일에 항목을 추가하여 보고서 서버에서 찾을 수 있도록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="18b9b-107">After you have written and compiled your [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] delivery extension into a [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] library, you must copy the extension to the appropriate directory and add an entry to the appropriate [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] configuration file so the report server can locate it.</span></span>  
  
## <a name="configuration-file-extension-element"></a><span data-ttu-id="18b9b-108">구성 파일 확장 프로그램 요소</span><span class="sxs-lookup"><span data-stu-id="18b9b-108">Configuration-File Extension Element</span></span>  
 <span data-ttu-id="18b9b-109">보고서 서버에 배포하는 배달 확장 프로그램은 구성 파일에서 `Extension` 요소로 입력되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="18b9b-109">Delivery extensions that you deploy to the report server need to be entered as `Extension` elements in the configuration file.</span></span> <span data-ttu-id="18b9b-110">보고서 서버에 대한 구성 파일은 RSReportServer.config입니다.</span><span class="sxs-lookup"><span data-stu-id="18b9b-110">The configuration file for the report server is RSReportServer.config.</span></span>  
  
 <span data-ttu-id="18b9b-111">다음 표는 배달 확장 프로그램에 대한 `Extension` 요소의 특성을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="18b9b-111">The following table describes the attributes for the `Extension` element for delivery extensions.</span></span>  
  
|<span data-ttu-id="18b9b-112">attribute</span><span class="sxs-lookup"><span data-stu-id="18b9b-112">Attribute</span></span>|<span data-ttu-id="18b9b-113">Description</span><span class="sxs-lookup"><span data-stu-id="18b9b-113">Description</span></span>|  
|---------------|-----------------|  
|`Name`|<span data-ttu-id="18b9b-114">확장 프로그램에 대한 고유한 이름으로서 예를 들면 전자 메일 배달 확장 프로그램의 경우 "Report Server E-Mail", 파일 공유 배달 확장 프로그램의 경우 "Report Server FileShare" 등입니다.</span><span class="sxs-lookup"><span data-stu-id="18b9b-114">A unique name for the extension (for example, "Report Server E-Mail" for the e-mail delivery extension or "Report Server FileShare" for the file share delivery extension).</span></span> <span data-ttu-id="18b9b-115">`Name` 특성의 최대 길이는 255자입니다.</span><span class="sxs-lookup"><span data-stu-id="18b9b-115">The maximum length for the `Name` attribute is 255 characters.</span></span> <span data-ttu-id="18b9b-116">이름은 구성 파일의 `Extension` 요소에 있는 모든 항목 중에서 고유해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="18b9b-116">The name must be unique among all entries within the `Extension` element of a configuration file.</span></span> <span data-ttu-id="18b9b-117">중복된 이름이 있을 경우 보고서 서버에서 오류를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="18b9b-117">If a duplicate name is present, the report server returns an error.</span></span>|  
|`Type`|<span data-ttu-id="18b9b-118">정규화된 네임스페이스와 어셈블리 이름을 포함하는 쉼표로 구분된 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="18b9b-118">A comma-separated list that includes the fully qualified namespace along with the name of the assembly.</span></span>|  
|`Visible`|<span data-ttu-id="18b9b-119">`false` 값은 배달 확장 프로그램이 사용자 인터페이스에 표시되지 않음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="18b9b-119">A value of `false` indicates that the delivery extension should not be visible in user interfaces.</span></span> <span data-ttu-id="18b9b-120">이 특성이 포함되지 않을 경우 기본값은 `true`입니다.</span><span class="sxs-lookup"><span data-stu-id="18b9b-120">If the attribute is not included, the default value is `true`.</span></span>|  
  
 <span data-ttu-id="18b9b-121">RSReportServer.config 파일에 대한 자세한 내용은 [Reporting Services 구성 파일](../../report-server/reporting-services-configuration-files.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="18b9b-121">For more information about the RSReportServer.config file, see [Reporting Services Configuration Files](../../report-server/reporting-services-configuration-files.md).</span></span>  
  
## <a name="deploying-the-extension-to-the-report-server"></a><span data-ttu-id="18b9b-122">보고서 서버에 확장 프로그램 배포</span><span class="sxs-lookup"><span data-stu-id="18b9b-122">Deploying the Extension to the Report Server</span></span>  
 <span data-ttu-id="18b9b-123">보고서 서버에서는 알림이나 보고서의 처리 및 배달을 위해 배달 확장 프로그램을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="18b9b-123">The report server uses delivery extensions for processing and delivering notifications or reports.</span></span> <span data-ttu-id="18b9b-124">배달 확장 프로그램 어셈블리를 프라이빗 어셈블리 형태로 보고서 서버에 배포해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="18b9b-124">You should deploy your delivery extension assembly to the report server as a private assembly.</span></span> <span data-ttu-id="18b9b-125">또한 보고서 서버 구성 파일 RSReportServer.config에서 항목을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="18b9b-125">You also need to make an entry in the report server configuration file, RSReportServer.config.</span></span>  
  
#### <a name="to-deploy-a-deliver-extension-assembly-to-a-report-server"></a><span data-ttu-id="18b9b-126">보고서 서버에 배달 확장 프로그램 어셈블리를 배포하려면</span><span class="sxs-lookup"><span data-stu-id="18b9b-126">To deploy a deliver extension assembly to a report server</span></span>  
  
1.  <span data-ttu-id="18b9b-127">준비 위치에서 배달 확장 프로그램을 사용할 보고서 서버의 bin 디렉터리로 어셈블리를 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="18b9b-127">Copy your assembly from your staging location to the bin directory of the report server on which you want to use the delivery extension.</span></span> <span data-ttu-id="18b9b-128">보고서 서버 bin 디렉터리의 기본 위치 는%ProgramFiles%\Microsoft SQL Server \ MSRS10_50입니다. \<InstanceName> \Reporting Services\reportserver\bin입니다.</span><span class="sxs-lookup"><span data-stu-id="18b9b-128">The default location of the report server bin directory is %ProgramFiles%\Microsoft SQL Server\MSRS10_50.\<InstanceName>\Reporting Services\ReportServer\bin.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="18b9b-129">기존 배달 확장 프로그램 어셈블리를 덮어쓰려는 경우 업데이트된 어셈블리를 복사하기 전에 먼저 보고서 서버 서비스를 중지해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="18b9b-129">If you are attempting to overwrite an existing delivery extension assembly, you must first stop the Report Server service before copying the updated assembly.</span></span> <span data-ttu-id="18b9b-130">어셈블리 복사가 완료된 후 서비스를 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="18b9b-130">Restart your service after the assembly is through copying.</span></span>  
  
2.  <span data-ttu-id="18b9b-131">어셈블리 파일이 복사된 후 RSReportServer.config 파일을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="18b9b-131">After the assembly file is copied, open the RSReportServer.config file.</span></span> <span data-ttu-id="18b9b-132">RSReportServer.config 파일 은%ProgramFiles%\Microsoft SQL Server \ MSRS10_50에 있습니다. \<InstanceName> \Reporting Services\ReportServer 디렉터리입니다.</span><span class="sxs-lookup"><span data-stu-id="18b9b-132">The RSReportServer.config file is located in the %ProgramFiles%\Microsoft SQL Server\MSRS10_50.\<InstanceName>\Reporting Services\ReportServer directory.</span></span> <span data-ttu-id="18b9b-133">구성 파일에서 배달 확장 프로그램 어셈블리 파일에 대한 항목을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="18b9b-133">You need to make an entry in the configuration file for your delivery extension assembly file.</span></span> <span data-ttu-id="18b9b-134">[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 또는 메모장과 같은 간단한 텍스트 편집기를 사용 하 여 구성 파일을 열 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="18b9b-134">You can open the configuration file with [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] or a simple text editor, such as Notepad.</span></span>  
  
3.  <span data-ttu-id="18b9b-135">RSReportServer.config 파일에서 `Delivery` 요소를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="18b9b-135">Locate the `Delivery` element in the RSReportServer.config file.</span></span> <span data-ttu-id="18b9b-136">새로 만든 배달 확장 프로그램에 대한 항목이 다음 위치에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="18b9b-136">An entry for your newly created delivery extension should be made in the following location:</span></span>  
  
    ```  
    <Extensions>  
       <Delivery>  
          <Your extension configuration information goes here>  
       </Delivery>  
    </Extensions>  
    ```  
  
4.  <span data-ttu-id="18b9b-137">배달 확장 프로그램에 대한 항목을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="18b9b-137">Add an entry for your delivery extension.</span></span> <span data-ttu-id="18b9b-138">항목에 `Extension` 및 `Name`에 대한 값이 있는 `Type` 요소가 포함되어야 하며 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="18b9b-138">Your entry should include an `Extension` element with values for `Name` and `Type`, and might look like the following:</span></span>  
  
    ```  
    <Extension Name="My Delivery Extension Name" Type="CompanyName.ExtensionName.MyDeliveryExtensionClass, AssemblyName" />  
    ```  
  
     <span data-ttu-id="18b9b-139">`Name`에 대한 값은 배달 확장 프로그램의 고유한 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="18b9b-139">The value for `Name` is the unique name of the delivery extension.</span></span> <span data-ttu-id="18b9b-140">`Type`의 값은 <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension> 인터페이스를 구현하는 클래스의 정규화된 네임스페이스에 대한 항목과 그 다음에 어셈블리의 이름(.dll 파일 확장명 포함 안 함)이 따라오는 형태가 포함되며 쉼표로 구분된 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="18b9b-140">The value for `Type` is a comma-separated list that includes an entry for the fully qualified namespace of your class that implements the <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension> interface, followed by the name of your assembly (not including the .dll file extension).</span></span> <span data-ttu-id="18b9b-141">기본적으로 배달 확장 프로그램은 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="18b9b-141">By default, delivery extensions are visible.</span></span> <span data-ttu-id="18b9b-142">보고서 관리자와 같은 사용자 인터페이스에서 확장 프로그램을 숨기려면 `Visible` 특성을 `Extension` 요소에 추가하고 `false`로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="18b9b-142">To hide an extension from user interfaces, such as Report Manager, add a `Visible` attribute to the `Extension` element, and set it to `false`.</span></span>  
  
5.  <span data-ttu-id="18b9b-143">마지막으로 배달 확장 프로그램에 대해 `FullTrust` 권한을 부여하는 사용자 지정 어셈블리에 대한 코드 그룹을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="18b9b-143">Finally, add a code group for your custom assembly that grants `FullTrust` permission for your delivery extension.</span></span> <span data-ttu-id="18b9b-144">%ProgramFiles%\Microsoft SQL Server \ MSRS10_50에서 기본적으로 rssrvpolicy.config 파일에 코드 그룹을 추가 하 여이 작업을 수행할 수 있습니다. \<InstanceName> \Reporting Services\reportserver</span><span class="sxs-lookup"><span data-stu-id="18b9b-144">You do this by adding the code group to the rssrvpolicy.config file located by default in %ProgramFiles%\Microsoft SQL Server\MSRS10_50.\<InstanceName>\Reporting Services\ReportServer.</span></span> <span data-ttu-id="18b9b-145">코드 그룹은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="18b9b-145">Your code group might look like the following:</span></span>  
  
    ```  
    <CodeGroup class="UnionCodeGroup"  
       version="1"  
       PermissionSetName="FullTrust"  
       Name="MyExtensionCodeGroup"  
       Description="Code group for my delivery extension">  
          <IMembershipCondition class="UrlMembershipCondition"  
             version="1"  
             Url="C:\Program Files\Microsoft SQL Server\MSRS10_50.<InstanceName>\Reporting Services\ReportServer\bin\MyExtensionAssembly.dll"  
           />  
    </CodeGroup>  
    ```  
  
     <span data-ttu-id="18b9b-146">URL 멤버 자격은 배달 확장 프로그램에 대해 선택할 수 있는 많은 멤버 자격 조건 중 하나일 뿐입니다.</span><span class="sxs-lookup"><span data-stu-id="18b9b-146">URL membership is only one of many membership conditions you might choose for your delivery extension.</span></span> <span data-ttu-id="18b9b-147">[!INCLUDE[ssRS](../../../includes/ssrs.md)]의 코드 액세스 보안에 대한 자세한 내용은 [보안 개발&#40;Reporting Services&#41;](../secure-development/secure-development-reporting-services.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="18b9b-147">For more information about code access security in [!INCLUDE[ssRS](../../../includes/ssrs.md)], see.[Secure Development &#40;Reporting Services&#41;](../secure-development/secure-development-reporting-services.md)</span></span>  
  
## <a name="deploying-the-extension-to-report-manager"></a><span data-ttu-id="18b9b-148">보고서 관리자에 확장 프로그램 배포</span><span class="sxs-lookup"><span data-stu-id="18b9b-148">Deploying the Extension to Report Manager</span></span>  
 <span data-ttu-id="18b9b-149">배달 확장 프로그램에서 <xref:Microsoft.ReportingServices.Interfaces.ISubscriptionBaseUIUserControl> 인터페이스를 구현하는 경우 배달 확장 프로그램을 보고서 관리자 구독 페이지에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="18b9b-149">If your delivery extension implements the <xref:Microsoft.ReportingServices.Interfaces.ISubscriptionBaseUIUserControl> interface, your delivery extension can be used with the Report Manager Subscription page.</span></span> <span data-ttu-id="18b9b-150">구독 사용자 인터페이스를 사용할 수 있도록 하려면 확장 프로그램을 보고서 관리자에 배포해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="18b9b-150">To make the subscription user interface available, you need to deploy your extension to Report Manager.</span></span>  
  
#### <a name="to-deploy-a-deliver-extension-assembly-to-report-manager"></a><span data-ttu-id="18b9b-151">보고서 관리자에 배달 확장 프로그램 어셈블리를 배포하려면</span><span class="sxs-lookup"><span data-stu-id="18b9b-151">To deploy a deliver extension assembly to Report Manager</span></span>  
  
1.  <span data-ttu-id="18b9b-152">준비 위치에서 보고서 관리자의 bin 디렉터리로 어셈블리를 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="18b9b-152">Copy your assembly from your staging location to the bin directory of Report Manager.</span></span> <span data-ttu-id="18b9b-153">보고서 관리자 bin 디렉터리의 기본 위치 는%ProgramFiles%\Microsoft SQL Server \ MSRS10_50입니다. \<InstanceName> \Reporting Services\reportmanager\bin입니다.</span><span class="sxs-lookup"><span data-stu-id="18b9b-153">The default location of the Report Manager bin directory is %ProgramFiles%\Microsoft SQL Server\MSRS10_50.\<InstanceName>\Reporting Services\ReportManager\bin.</span></span>  
  
2.  <span data-ttu-id="18b9b-154">어셈블리 파일이 복사된 후 RSReportServer.config 파일을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="18b9b-154">After the assembly file is copied, open the RSReportServer.config file.</span></span> <span data-ttu-id="18b9b-155">RSReportServer.config 파일 은%ProgramFiles%\Microsoft SQL Server \ MSRS10_50에 있습니다. \<InstanceName> \Reporting Services\ReportServer 디렉터리입니다.</span><span class="sxs-lookup"><span data-stu-id="18b9b-155">The RSReportServer.config file is located in the %ProgramFiles%\Microsoft SQL Server\MSRS10_50.\<InstanceName>\Reporting Services\ReportServer directory.</span></span> <span data-ttu-id="18b9b-156">구성 파일에서 배달 확장 프로그램 어셈블리 파일에 대한 항목을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="18b9b-156">You need to make an entry in the configuration file for your delivery extension assembly file.</span></span> <span data-ttu-id="18b9b-157">구성 파일은 Visual Studio .NET 또는 메모장과 같은 간단한 텍스트 편집기를 사용하여 열 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="18b9b-157">You can open the configuration file with Visual Studio .NET or a simple text editor, such as Notepad.</span></span>  
  
3.  <span data-ttu-id="18b9b-158">RSReportServer.config 파일에서 `DeliveryUI` 요소를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="18b9b-158">Locate the `DeliveryUI` element in the RSReportServer.config file.</span></span> <span data-ttu-id="18b9b-159">새로 만든 배달 확장 프로그램에 대한 항목이 다음 위치에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="18b9b-159">An entry for your newly created delivery extension should be made in the following location:</span></span>  
  
    ```  
    <Extensions>  
       <DeliveryUI>  
          <Your extension configuration information goes here>  
       </DeliveryUI>  
    </Extensions>  
    ```  
  
4.  <span data-ttu-id="18b9b-160">배달 확장 프로그램에 대한 항목을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="18b9b-160">Add an entry for your delivery extension.</span></span> <span data-ttu-id="18b9b-161">항목에 `Extension` 및 `Name`에 대한 값과 함께 `Type` 요소가 포함되어야 하며 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="18b9b-161">Your entry should include an `Extension` element with values for `Name` and `Type` and might look like the following:</span></span>  
  
    ```  
    <Extension Name="My Delivery Extension Name" Type="CompanyName.ExtensionName.MyDeliveryUIExtensionClass, AssemblyName" />  
    ```  
  
     <span data-ttu-id="18b9b-162">`Name`에 대한 값은 배달 확장 프로그램의 고유한 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="18b9b-162">The value for `Name` is the unique name of the delivery extension.</span></span> <span data-ttu-id="18b9b-163">`Type`의 값은 <xref:Microsoft.ReportingServices.Interfaces.ISubscriptionBaseUIUserControl> 인터페이스를 구현하는 클래스의 정규화된 네임스페이스에 대한 항목과 그 다음에 어셈블리의 이름(.dll 파일 확장명 포함 안 함)이 따라오는 형태가 포함되며 쉼표로 구분된 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="18b9b-163">The value for `Type` is a comma-separated list that includes an entry for the fully qualified namespace of your class that implements the <xref:Microsoft.ReportingServices.Interfaces.ISubscriptionBaseUIUserControl> interface, followed by the name of your assembly (not including the .dll file extension).</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="18b9b-164">`Name` 특성의 값은 보고서 서버와 보고서 관리자 구성 파일 항목에 대해 동일해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="18b9b-164">The value of the `Name` attribute must be identical for both the Report Server and Report Manager configuration file entries.</span></span> <span data-ttu-id="18b9b-165">동일하지 않은 경우 서버 구성이 잘못된 것입니다.</span><span class="sxs-lookup"><span data-stu-id="18b9b-165">If they are not identical, your server configuration is not valid.</span></span>  
  
     <span data-ttu-id="18b9b-166">마지막으로 배달 확장 프로그램에 대해 `FullTrust` 권한을 부여하는 사용자 지정 어셈블리에 대한 코드 그룹을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="18b9b-166">Finally, add a code group for your custom assembly that grants `FullTrust` permission for your delivery extension.</span></span> <span data-ttu-id="18b9b-167">기본적으로 C:\Program Files\Microsoft SQL Server \ MSRS10_50에 있는 RSmgrpolicy.config 파일에 코드 그룹을 추가 하 여이 작업을 수행할 수 있습니다. \<InstanceName> \Reporting Services\reportmanager</span><span class="sxs-lookup"><span data-stu-id="18b9b-167">You do this by adding the code group to the RSmgrpolicy.config file located by default in C:\Program Files\Microsoft SQL Server\MSRS10_50.\<InstanceName>\Reporting Services\ReportManager.</span></span> <span data-ttu-id="18b9b-168">코드 그룹은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="18b9b-168">Your code group might look like the following:</span></span>  
  
    ```  
    <CodeGroup class="UnionCodeGroup"  
       version="1"  
       PermissionSetName="FullTrust"  
       Name="MyExtensionCodeGroup"  
       Description="Code group for my delivery UI extension">  
          <IMembershipCondition class="UrlMembershipCondition"  
             version="1"  
             Url="C:\Program Files\Microsoft SQL Server\MSRS10_50.<InstanceName>\Reporting Services\ReportManager\bin\MyExtensionAssembly.dll"  
           />  
    </CodeGroup>  
    ```  
  
     <span data-ttu-id="18b9b-169">URL 멤버 자격은 배달 확장 프로그램에 대해 선택할 수 있는 많은 멤버 자격 조건 중 하나일 뿐입니다.</span><span class="sxs-lookup"><span data-stu-id="18b9b-169">URL membership is only one of many membership conditions you might choose for your delivery extension.</span></span> <span data-ttu-id="18b9b-170">의 코드 액세스 보안에 대 한 자세한 내용은 [!INCLUDE[ssRS](../../../includes/ssrs.md)] [보안 개발 &#40;Reporting Services](../secure-development/secure-development-reporting-services.md) 를 참조 하세요&#41;</span><span class="sxs-lookup"><span data-stu-id="18b9b-170">For more information about code access security in [!INCLUDE[ssRS](../../../includes/ssrs.md)], see [Secure Development &#40;Reporting Services&#41;](../secure-development/secure-development-reporting-services.md)</span></span>  
  
## <a name="verifying-the-deployment"></a><span data-ttu-id="18b9b-171">배포 확인</span><span class="sxs-lookup"><span data-stu-id="18b9b-171">Verifying the Deployment</span></span>  
 <span data-ttu-id="18b9b-172">웹 서비스 <xref:ReportService2010.ReportingService2010.ListExtensions%2A> 메서드를 사용하여 배달 확장 프로그램이 보고서 서버에 성공적으로 배포되었는지 여부를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="18b9b-172">You can verify whether your delivery extension was deployed successfully to the report server by using the Web service <xref:ReportService2010.ReportingService2010.ListExtensions%2A> method.</span></span> <span data-ttu-id="18b9b-173">보고서 관리자를 열고 확장 프로그램이 구독에 대해 사용 가능한 배달 확장 프로그램 목록에 포함되어 있는지 확인할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="18b9b-173">You can also open Report Manager and verify that your extension is included in the list of available delivery extensions for a subscription.</span></span> <span data-ttu-id="18b9b-174">보고서 관리자 및 구독에 대 한 자세한 내용은 [구독 및 배달 &#40;Reporting Services&#41;](../../subscriptions/subscriptions-and-delivery-reporting-services.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="18b9b-174">For more information about Report Manager and subscriptions, see [Subscriptions and Delivery &#40;Reporting Services&#41;](../../subscriptions/subscriptions-and-delivery-reporting-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18b9b-175">참고 항목</span><span class="sxs-lookup"><span data-stu-id="18b9b-175">See Also</span></span>  
 <span data-ttu-id="18b9b-176">[배달 확장 프로그램 구현](implementing-a-delivery-extension.md) </span><span class="sxs-lookup"><span data-stu-id="18b9b-176">[Implementing a Delivery Extension](implementing-a-delivery-extension.md) </span></span>  
 [<span data-ttu-id="18b9b-177">Reporting Services 확장 프로그램 라이브러리</span><span class="sxs-lookup"><span data-stu-id="18b9b-177">Reporting Services Extension Library</span></span>](../reporting-services-extension-library.md)  
  
  
