---
title: Reporting Services 구성 파일 수정(RSreportserver.config) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 958ef51f-2699-4cb2-a92e-3b4322e36a30
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 75ff276a0ba43cb89393466bf40a71b7acd21368
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650639"
---
# <a name="modify-a-reporting-services-configuration-file-rsreportserverconfig"></a><span data-ttu-id="35862-102">Reporting Services 구성 파일 수정(RSreportserver.config)</span><span class="sxs-lookup"><span data-stu-id="35862-102">Modify a Reporting Services Configuration File (RSreportserver.config)</span></span>
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="35862-103">는 애플리케이션 설정을 구성 파일 집합에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="35862-103">stores application settings in a set of configuration files.</span></span> <span data-ttu-id="35862-104">설치 프로그램은 사용자가 설치하는 각 보고서 서버 인스턴스에 대한 구성 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="35862-104">Setup creates the configuration files for each report server instance you install.</span></span> <span data-ttu-id="35862-105">각 파일 내에서 값은 설치 중 설정되거나 도구 및 애플리케이션을 사용하여 작업을 위해 서버를 구성할 때 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="35862-105">Within each file, values are either set during installation or when you use tools and applications to configure a server for operation.</span></span> <span data-ttu-id="35862-106">경우에 따라 파일을 직접 수정하여 고급 설정을 추가하거나 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="35862-106">In some cases, you must modify a file directly to add or configure advanced settings.</span></span> <span data-ttu-id="35862-107">구성 설정은 XML 요소나 특성으로 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="35862-107">Configuration settings are specified as either XML elements or attributes.</span></span> <span data-ttu-id="35862-108">XML과 구성 파일에 대해 이해하고 있으면 텍스트나 코드 편집기를 사용하여 사용자 정의 가능한 설정을 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35862-108">If you understand XML and configuration files, you can use a text or code editor to modify user-definable settings.</span></span>  
  
 <span data-ttu-id="35862-109">일부 구성 설정은 도구를 통해서만 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35862-109">Some configuration settings can be set only through a tool.</span></span> <span data-ttu-id="35862-110">암호화된 값이 포함된 설정은 Reporting Services 구성 도구, 설치 프로그램 또는 **rsconfig** 명령줄 유틸리티를 통해 수정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="35862-110">Settings that contain encrypted values must be modified through the Reporting Services Configuration tool, the Setup program, or the **rsconfig** command line utility.</span></span> <span data-ttu-id="35862-111">이러한 도구를 실행하려면 로컬 관리자 그룹의 멤버여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="35862-111">You must be a member of the local Administrators group to run these tools.'</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="35862-112">구성 파일을 수정할 때는 주의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="35862-112">Use caution when modifying configuration files.</span></span> <span data-ttu-id="35862-113">내부용으로 예약된 설정을 수정할 경우 설치가 불가능할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35862-113">If you modify a setting that is reserved for internal use, you may disable your installation.</span></span> <span data-ttu-id="35862-114">일반적으로 특정 문제를 해결하려는 경우 외에는 구성 설정을 수정하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="35862-114">Generally, modifying configuration settings is not recommended unless you are trying to solve a specific problem.</span></span> <span data-ttu-id="35862-115">변경해도 문제가 없는 설정에 대한 자세한 내용은 [RSReportServer Configuration File](rsreportserver-config-configuration-file.md) 또는 [RSReportDesigner Configuration File](rsreportdesigner-configuration-file.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="35862-115">For more information about which settings are safe to change, see [RSReportServer Configuration File](rsreportserver-config-configuration-file.md) or [RSReportDesigner Configuration File](rsreportdesigner-configuration-file.md).</span></span> <span data-ttu-id="35862-116">구성 파일에 대한 자세한 내용은 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 제품 설명서를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="35862-116">For more information about configuration files, see the [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] product documentation.</span></span>  
  
 <span data-ttu-id="35862-117">이 항목의 내용:</span><span class="sxs-lookup"><span data-stu-id="35862-117">In this topic:</span></span>  
  
-   [<span data-ttu-id="35862-118">구성 값 읽기 및 사용</span><span class="sxs-lookup"><span data-stu-id="35862-118">Reading and Using Configuration Values</span></span>](#bkmk_read_values)  
  
-   [<span data-ttu-id="35862-119">기본값 정보</span><span class="sxs-lookup"><span data-stu-id="35862-119">About Default Values</span></span>](#bkmk_default_values)  
  
-   [<span data-ttu-id="35862-120">구성 설정 삭제</span><span class="sxs-lookup"><span data-stu-id="35862-120">Deleting Configuration Settings</span></span>](#bkmk_delete_config_settings)  
  
-   [<span data-ttu-id="35862-121">Reporting Services 구성 파일을 편집하려면</span><span class="sxs-lookup"><span data-stu-id="35862-121">To Edit a Reporting Services Configuration File</span></span>](#bkmk_edit_configuation_file)  
  
##  <a name="reading-and-using-configuration-values"></a><a name="bkmk_read_values"></a> <span data-ttu-id="35862-122">구성 값 읽기 및 사용</span><span class="sxs-lookup"><span data-stu-id="35862-122">Reading and Using Configuration Values</span></span>  
 <span data-ttu-id="35862-123">보고서 서버는 서비스가 시작될 때 및 구성 파일이 저장될 때마다 구성 파일을 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="35862-123">A report server reads the configuration files when the service starts and whenever the configuration file is saved.</span></span> <span data-ttu-id="35862-124">새 값 및 수정된 값은 현재 애플리케이션 도메인이 만료된 후 새 애플리케이션 도메인에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="35862-124">New and revised values take effect in a new application domain after the current application domain expires.</span></span> <span data-ttu-id="35862-125">가능하면 현재 애플리케이션 도메인에서 아직 처리 중인 요청이 완료되도록 허용됩니다.</span><span class="sxs-lookup"><span data-stu-id="35862-125">Whenever possible, requests that are still processing in the current application domain are allowed to complete.</span></span> <span data-ttu-id="35862-126">그러나 일부 설정의 경우 애플리케이션 도메인 재활용 작업을 바로 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="35862-126">However, a few settings require an immediate application domain recycle operation.</span></span> <span data-ttu-id="35862-127">이 경우 처리 중인 모든 요청이 새 애플리케이션 도메인에서 다시 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="35862-127">In this case, all requests that are in process are restarted in a new application domain.</span></span>  
  
 <span data-ttu-id="35862-128">잘못된 값이 감지되면 보고서 서버는 Windows 애플리케이션 로그에 오류를 기록하고 오류에 따라 시작되지 못하거나 기본값을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="35862-128">If the report server detects an invalid value, the report server logs an error to the Windows application log and either fails to start or uses a default value, depending on the error:</span></span>  
  
-   <span data-ttu-id="35862-129">XML 형식이 잘못되었음을 나타내는 오류인 경우 보고서 서버는 시작되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="35862-129">If the error is malformed XML, the report server will not start.</span></span> <span data-ttu-id="35862-130">오류가 발생할 때 보고서 서버가 실행 중이면 보고서 서버는 다시 시작되거나 애플리케이션 도메인이 재활용될 때까지 잘못된 구성 파일을 무시합니다.</span><span class="sxs-lookup"><span data-stu-id="35862-130">If the report server is running when you introduce the error, the report server ignores the invalid configuration file until the report server restarts or the application domain is recycled.</span></span> <span data-ttu-id="35862-131">오류가 감지되면 보고서 서버는 더 이상 시작되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="35862-131">Once the error is detected, the report server will no longer start.</span></span>  
  
-   <span data-ttu-id="35862-132">잘못된 구성 값 오류인 경우 서버는 내부 기본값을 사용하고 추적 로그 파일에 오류를 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="35862-132">If the error is an invalid configuration value, the server will use internal default values and log an error to the trace log files.</span></span> <span data-ttu-id="35862-133">내부 기본값을 사용할 수 없는 드문 경우 잘못된 구성 설정이 서버 작업에 중요하면 서버가 rsServerConfigurationError 오류를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="35862-133">In the few cases where internal default values are not available, the server will return the rsServerConfigurationError error if the invalid configuration setting is critical to server operations.</span></span> <span data-ttu-id="35862-134">누락되었거나 잘못된 중요한 설정에 대한 오류는 클라이언트 애플리케이션의 HTML 오류 페이지에 반환되고 이벤트 로그에 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="35862-134">Errors about missing or invalid critical settings are returned to the client application in an HTML error page and logged to the event log.</span></span>  
  
 <span data-ttu-id="35862-135">성공적으로 적용된 변경 내용을 비롯하여 모든 구성 파일 변경 내용은 보고서 서버 추적 로그 파일에 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="35862-135">All configuration file changes, including successful changes, are recorded in the report server trace log file.</span></span> <span data-ttu-id="35862-136">오류만 애플리케이션 이벤트 로그에 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="35862-136">Only errors are logged to the application event log.</span></span>  
  
##  <a name="about-default-values"></a><a name="bkmk_default_values"></a> <span data-ttu-id="35862-137">기본값 정보</span><span class="sxs-lookup"><span data-stu-id="35862-137">About Default Values</span></span>  
 <span data-ttu-id="35862-138">대부분의 구성 설정에는 보고서 서버에서 내부적으로 지정된 기본값이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35862-138">Most configuration settings have default values that are specified internally in the report server.</span></span> <span data-ttu-id="35862-139">사용자 정의 값이 올바르지 않거나 지정되지 않은 경우 보고서 서버는 이러한 값을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="35862-139">The report server will use these values if a user-defined value is invalid or not specified.</span></span> <span data-ttu-id="35862-140">잘못된 구성 설정으로 인해 기본값을 사용해야 하는 경우 추적 로그 파일에 오류가 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="35862-140">If a default value must be used due to an invalid configuration setting, an error is written to the trace log file.</span></span>  
  
##  <a name="deleting-configuration-settings"></a><a name="bkmk_delete_config_settings"></a> <span data-ttu-id="35862-141">구성 설정 삭제</span><span class="sxs-lookup"><span data-stu-id="35862-141">Deleting Configuration Settings</span></span>  
 <span data-ttu-id="35862-142">기본값이 지정된 구성 설정의 경우 구성 파일에서 해당 설정을 제거해도 아무런 영향이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="35862-142">For configuration settings that have default values, removing the setting from the configuration file has no effect.</span></span> <span data-ttu-id="35862-143">실제로 대부분의 구성 설정은 내부적으로 정의되고 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="35862-143">Most configuration settings are actually defined and configured internally.</span></span> <span data-ttu-id="35862-144">구성 파일에서 항목을 삭제해도 내부 복사본은 계속 사용할 수 있으며 해당 항목에 대해 정의된 기본값이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="35862-144">If you delete an item from the configuration file, the internal copy is still available and uses the default value that is defined for it.</span></span>  
  
##  <a name="to-edit-a-reporting-services-configuration-file"></a><a name="bkmk_edit_configuation_file"></a> <span data-ttu-id="35862-145">Reporting Services 구성 파일을 편집하려면</span><span class="sxs-lookup"><span data-stu-id="35862-145">To Edit a Reporting Services Configuration File</span></span>  
  
1.  <span data-ttu-id="35862-146">편집할 구성 파일을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="35862-146">Find the configuration file you want to edit:</span></span>  
  
    -   <span data-ttu-id="35862-147">**RSReportServer.config** 는 다음 디렉터리에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35862-147">**RSReportServer.config** is located in the following folder:</span></span>  
  
        ```  
        C:\Program Files\Microsoft SQL Server\MSRS11.MSSQLSERVER\Reporting Services\ReportServer  
        ```  
  
    -   <span data-ttu-id="35862-148">**RSReportServerServices.exe.config** 는 다음 디렉터리에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35862-148">**RSReportServerServices.exe.config** is located in the following folder:</span></span>  
  
        ```  
        C:\Program Files\Microsoft SQL Server\MSRS11.MSSQLSERVER\Reporting Services\ReportServer\bin  
        ```  
  
    -   <span data-ttu-id="35862-149">**RSReportDesigner.config** 는 다음 디렉터리에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35862-149">**RSReportDesigner.config** is located in the following folder:</span></span>  
  
        ```  
        C:\Program Files\Microsoft Visual Studio 10.0\Common7\IDE\PrivateAssemblies  
        ```  
  
2.  <span data-ttu-id="35862-150">변경 내용을 롤백해야 하는 경우에 대비하여 파일의 복사본을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="35862-150">Save a copy of the file in case you need to roll back your changes.</span></span>  
  
3.  <span data-ttu-id="35862-151">메모장 또는 코드 편집기에서 원래 파일을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="35862-151">Open the original file in Notepad or a code editor.</span></span> <span data-ttu-id="35862-152">Textpad는 파일이 저장되기 전에 파일 길이를 설정하여 추적 로그 파일에 잘못된 문자 오류가 기록되게 하므로 사용하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="35862-152">Do not use Textpad; it sets the file length before the file is saved, causing an invalid character error to be written to the trace log file.</span></span>  
  
4.  <span data-ttu-id="35862-153">추가 또는 사용할 요소나 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="35862-153">Type the element or value that you want to add or use.</span></span> <span data-ttu-id="35862-154">요소는 대/소문자를 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="35862-154">Elements are case-sensitive.</span></span> <span data-ttu-id="35862-155">요소를 추가하는 경우 올바른 대/소문자를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="35862-155">If you are adding an element, be sure to use the correct upper and lower case letters.</span></span> <span data-ttu-id="35862-156">렌더링 확장 프로그램, 인증 확장 프로그램 또는 데이터 처리 확장 프로그램을 사용자 지정하는 경우 구성 파일 편집에 대한 특정 지침을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35862-156">Specific instructions for editing configuration files are available if you are customizing rendering extension, authentication extensions, or data processing extensions:</span></span>  
  
    -   [<span data-ttu-id="35862-157">보고서 서버 인증</span><span class="sxs-lookup"><span data-stu-id="35862-157">Authentication with the Report Server</span></span>](../security/authentication-with-the-report-server.md)  
  
    -   [<span data-ttu-id="35862-158">보고서 관리자에서 사용자 지정 인증 쿠키를 전달하도록 구성</span><span class="sxs-lookup"><span data-stu-id="35862-158">Configure Report Manager to Pass Custom Authentication Cookies</span></span>](../security/configure-the-web-portal-to-pass-custom-authentication-cookies.md)  
  
    -   [<span data-ttu-id="35862-159">RSReportServer.Config의 렌더링 확장 프로그램 매개 변수 사용자 지정</span><span class="sxs-lookup"><span data-stu-id="35862-159">Customize Rendering Extension Parameters in RSReportServer.Config</span></span>](../customize-rendering-extension-parameters-in-rsreportserver-config.md)  
  
5.  <span data-ttu-id="35862-160">파일을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="35862-160">Save the file.</span></span>  
  
6.  <span data-ttu-id="35862-161">추적 로그 파일에서 오류가 발생하지 않았는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="35862-161">Check the trace log files to verify that errors did not occur.</span></span> <span data-ttu-id="35862-162">오류 상태가 표시되는 경우 설정 또는 해당 값이 잘못 지정된 것입니다.</span><span class="sxs-lookup"><span data-stu-id="35862-162">If you see error conditions, a setting or its value is specified incorrectly.</span></span> <span data-ttu-id="35862-163">오류를 발생시키는 설정에 대한 유효한 값을 보려면 [RSReportServer Configuration File](rsreportserver-config-configuration-file.md) 을 검토하세요.</span><span class="sxs-lookup"><span data-stu-id="35862-163">Review the [RSReportServer Configuration File](rsreportserver-config-configuration-file.md) for valid values for any setting that is causing an error.</span></span> <span data-ttu-id="35862-164">추적 로그를 보는 방법은 [보고서 서버 서비스 추적 로그](report-server-service-trace-log.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="35862-164">For more information about how to view the trace log, see [Report Server Service Trace Log](report-server-service-trace-log.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35862-165">참고 항목</span><span class="sxs-lookup"><span data-stu-id="35862-165">See Also</span></span>  
 <span data-ttu-id="35862-166">[Rsreportserver.config 구성 파일](rsreportserver-config-configuration-file.md) </span><span class="sxs-lookup"><span data-stu-id="35862-166">[RSReportServer Configuration File](rsreportserver-config-configuration-file.md) </span></span>  
 <span data-ttu-id="35862-167">[ReportingServicesService 구성 파일](reportingservicesservice-configuration-file.md) </span><span class="sxs-lookup"><span data-stu-id="35862-167">[ReportingServicesService Configuration File](reportingservicesservice-configuration-file.md) </span></span>  
 <span data-ttu-id="35862-168">[Rsreportdesigner.config 구성 파일](rsreportdesigner-configuration-file.md) </span><span class="sxs-lookup"><span data-stu-id="35862-168">[RSReportDesigner Configuration File](rsreportdesigner-configuration-file.md) </span></span>  
 <span data-ttu-id="35862-169">[데이터 처리 확장 프로그램 배포](../extensions/data-processing/deploying-a-data-processing-extension.md) </span><span class="sxs-lookup"><span data-stu-id="35862-169">[Deploying a Data Processing Extension](../extensions/data-processing/deploying-a-data-processing-extension.md) </span></span>  
 <span data-ttu-id="35862-170">[배달 확장 프로그램 배포](../extensions/delivery-extension/deploying-a-delivery-extension.md) </span><span class="sxs-lookup"><span data-stu-id="35862-170">[Deploying a Delivery Extension](../extensions/delivery-extension/deploying-a-delivery-extension.md) </span></span>  
 <span data-ttu-id="35862-171">[렌더링 확장 프로그램 배포](../extensions/rendering-extension/deploying-a-rendering-extension.md) </span><span class="sxs-lookup"><span data-stu-id="35862-171">[Deploying a Rendering Extension](../extensions/rendering-extension/deploying-a-rendering-extension.md) </span></span>  
 <span data-ttu-id="35862-172">[방법: 사용자 지정 보고서 항목 배포](../custom-report-items/how-to-deploy-a-custom-report-item.md) </span><span class="sxs-lookup"><span data-stu-id="35862-172">[How to: Deploy a Custom Report Item](../custom-report-items/how-to-deploy-a-custom-report-item.md) </span></span>  
 [<span data-ttu-id="35862-173">Reporting Services 구성 파일</span><span class="sxs-lookup"><span data-stu-id="35862-173">Reporting Services Configuration Files</span></span>](reporting-services-configuration-files.md)  
  
  
