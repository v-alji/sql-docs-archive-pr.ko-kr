---
title: ReportingServicesService 구성 파일| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- traces [Reporting Services]
- Report Server Windows service, ReportingServicesService configuration file
- ReportingServicesService configuration file
ms.assetid: 40f4a401-cb61-4c42-b1ec-01acdacdacd1
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 5124631db9635211827dd3b1abbff7116101a61d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651484"
---
# <a name="reportingservicesservice-configuration-file"></a><span data-ttu-id="3b797-102">ReportingServicesService 구성 파일</span><span class="sxs-lookup"><span data-stu-id="3b797-102">ReportingServicesService Configuration File</span></span>
  <span data-ttu-id="3b797-103">ReportingServicesService.exe.config 파일에는 추적을 구성하는 설정이 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3b797-103">The ReportingServicesService.exe.config file includes settings that configure tracing.</span></span>  
  
## <a name="file-location"></a><span data-ttu-id="3b797-104">파일 위치</span><span class="sxs-lookup"><span data-stu-id="3b797-104">File Location</span></span>  
 <span data-ttu-id="3b797-105">이 파일은 \Reporting Services\Report Server\Bin 폴더에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3b797-105">This file is located in the \Reporting Services\Report Server\Bin folder.</span></span>  
  
## <a name="editing-guidelines"></a><span data-ttu-id="3b797-106">편집 지침</span><span class="sxs-lookup"><span data-stu-id="3b797-106">Editing Guidelines</span></span>  
 <span data-ttu-id="3b797-107">로그 파일 이름을 바꾸거나 추적 수준을 올리거나 내리기 위해 이 파일을 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3b797-107">You can modify this file to rename the log file or to increase or decrease trace levels.</span></span> <span data-ttu-id="3b797-108">다른 설정은 수정하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="3b797-108">Do not modify any of the other settings.</span></span> <span data-ttu-id="3b797-109">자세한 내용은 [Reporting Services 구성 파일 수정&#40;RSreportserver.config&#41;](modify-a-reporting-services-configuration-file-rsreportserver-config.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3b797-109">For instructions, see [Modify a Reporting Services Configuration File &#40;RSreportserver.config&#41;](modify-a-reporting-services-configuration-file-rsreportserver-config.md).</span></span> <span data-ttu-id="3b797-110">추적 로그에 대한 자세한 내용은 [보고서 서버 서비스 추적 로그](report-server-service-trace-log.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3b797-110">For more information about trace logs, see [Report Server Service Trace Log](report-server-service-trace-log.md).</span></span>  
  
## <a name="example-configuration"></a><span data-ttu-id="3b797-111">예제 구성</span><span class="sxs-lookup"><span data-stu-id="3b797-111">Example Configuration</span></span>  
 <span data-ttu-id="3b797-112">다음 예에서는 ReportingServicesService.exe.config 파일에 나오는 설정 및 기본값을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="3b797-112">The following example shows the settings and default values found in the ReportingServicesService.exe.config file.</span></span>  
  
```  
<configSections>  
      <section name="RStrace" type="Microsoft.ReportingServices.Diagnostics.RSTraceSectionHandler,Microsoft.ReportingServices.Diagnostics" />  
</configSections>  
<system.diagnostics>  
      <switches>  
          <add name="DefaultTraceSwitch" value="3" />  
      </switches>  
</system.diagnostics>  
<RStrace>  
      <add name="FileName" value="ReportServerService_" />  
      <add name="FileSizeLimitMb" value="32" />  
      <add name="KeepFilesForDays" value="14" />  
      <add name="Prefix" value="tid, time" />  
      <add name="TraceListeners" value="debugwindow, file" />  
      <add name="TraceFileMode" value="unique" />  
      <add name="Components" value="all" />  
</RStrace>  
<runtime>  
      <alwaysFlowImpersonationPolicy enabled="true"/>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
             <dependentAssembly>  
                    <assemblyIdentity name="Microsoft.ReportingServices.Interfaces"  
                        publicKeyToken="89845dcd8080cc91"  
                        culture="neutral" />  
                    <bindingRedirect oldVersion="8.0.242.0"  
                                     newVersion="10.0.0.0"/>  
                    <bindingRedirect oldVersion="9.0.242.0"  
                                     newVersion="10.0.0.0"/>  
             </dependentAssembly>  
      </assemblyBinding>  
      <gcServer enabled="true" />  
</runtime>  
```  
  
## <a name="configuration-settings"></a><span data-ttu-id="3b797-113">구성 설정</span><span class="sxs-lookup"><span data-stu-id="3b797-113">Configuration Settings</span></span>  
 <span data-ttu-id="3b797-114">다음 표는 특정 설정에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="3b797-114">The following table provides information about specific settings.</span></span> <span data-ttu-id="3b797-115">설정은 구성 파일에 나타나는 순서로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3b797-115">Settings are presented in the order in which they appear in the configuration file.</span></span>  
  
|<span data-ttu-id="3b797-116">설정</span><span class="sxs-lookup"><span data-stu-id="3b797-116">Setting</span></span>|<span data-ttu-id="3b797-117">Description</span><span class="sxs-lookup"><span data-stu-id="3b797-117">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3b797-118">**RStrace**</span><span class="sxs-lookup"><span data-stu-id="3b797-118">**RStrace**</span></span>|<span data-ttu-id="3b797-119">오류 및 추적에 사용되는 네임스페이스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3b797-119">Specifies namespaces used for errors and tracing.</span></span>|  
|<span data-ttu-id="3b797-120">**DefaultTraceSwitch**</span><span class="sxs-lookup"><span data-stu-id="3b797-120">**DefaultTraceSwitch**</span></span>|<span data-ttu-id="3b797-121">ReportServerService 추적 로그에 보고되는 정보의 수준을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3b797-121">Specifies the level of information that is reported to the ReportServerService trace log.</span></span> <span data-ttu-id="3b797-122">각 수준에는 낮은 번호가 매겨진 모든 수준별로 보고된 정보가 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3b797-122">Each level includes the information reported by all lower-numbered levels.</span></span> <span data-ttu-id="3b797-123">추적을 설정하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="3b797-123">Disabling tracing is not recommended.</span></span> <span data-ttu-id="3b797-124">유효한 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="3b797-124">Valid values include:</span></span><br /><br /> <span data-ttu-id="3b797-125">0= 추적 해제</span><span class="sxs-lookup"><span data-stu-id="3b797-125">0= Disables tracing</span></span><br /><br /> <span data-ttu-id="3b797-126">1= 예외 및 다시 시작</span><span class="sxs-lookup"><span data-stu-id="3b797-126">1= Exceptions and restarts</span></span><br /><br /> <span data-ttu-id="3b797-127">2= 예외, 다시 시작, 경고</span><span class="sxs-lookup"><span data-stu-id="3b797-127">2= Exceptions, restarts, warnings</span></span><br /><br /> <span data-ttu-id="3b797-128">3= 예외, 다시 시작, 경고, 상태 메시지(기본값)</span><span class="sxs-lookup"><span data-stu-id="3b797-128">3= Exceptions, restarts, warnings, status messages (default)</span></span><br /><br /> <span data-ttu-id="3b797-129">4= 세부 정보 표시 모드</span><span class="sxs-lookup"><span data-stu-id="3b797-129">4= Verbose mode</span></span>|  
|<span data-ttu-id="3b797-130">**FileName**</span><span class="sxs-lookup"><span data-stu-id="3b797-130">**FileName**</span></span>|<span data-ttu-id="3b797-131">로그 파일 이름의 첫 번째 부분을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3b797-131">Specifies the first portion of the log file name.</span></span> <span data-ttu-id="3b797-132">`Prefix`에 지정된 값으로 이름의 나머지 부분을 완성합니다.</span><span class="sxs-lookup"><span data-stu-id="3b797-132">The value specified by `Prefix` completes the rest of the name.</span></span> <span data-ttu-id="3b797-133">기본적으로 이름은 ReportServerService_가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3b797-133">By default, the name is ReportServerService_.</span></span>|  
|<span data-ttu-id="3b797-134">**FileSizeLimitMb**</span><span class="sxs-lookup"><span data-stu-id="3b797-134">**FileSizeLimitMb**</span></span>|<span data-ttu-id="3b797-135">추적 로그 크기에 대한 상한값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3b797-135">Specifies an upper limit on trace log size.</span></span> <span data-ttu-id="3b797-136">파일은 메가바이트(MB) 단위로 측정됩니다.</span><span class="sxs-lookup"><span data-stu-id="3b797-136">The file is measured in megabytes.</span></span> <span data-ttu-id="3b797-137">유효한 값은 0에서 최대 정수 사이입니다.</span><span class="sxs-lookup"><span data-stu-id="3b797-137">Valid values are 0 to a maximum integer.</span></span> <span data-ttu-id="3b797-138">기본값은 32입니다.</span><span class="sxs-lookup"><span data-stu-id="3b797-138">The default value is 32.</span></span>|  
|<span data-ttu-id="3b797-139">**KeepFilesForDays**</span><span class="sxs-lookup"><span data-stu-id="3b797-139">**KeepFilesForDays**</span></span>|<span data-ttu-id="3b797-140">추적 로그 파일을 몇 일 후에 삭제할지 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3b797-140">Specifies the number of days after which a trace log file will be deleted.</span></span> <span data-ttu-id="3b797-141">유효한 값은 0에서 최대 정수 사이입니다.</span><span class="sxs-lookup"><span data-stu-id="3b797-141">Valid values are 0 to a maximum integer.</span></span> <span data-ttu-id="3b797-142">기본값은 14입니다.</span><span class="sxs-lookup"><span data-stu-id="3b797-142">The default value is 14.</span></span>|  
|`Prefix`|<span data-ttu-id="3b797-143">로그 인스턴스를 구분하는 생성 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3b797-143">Specifies a generated value that distinguishes one log instance from another.</span></span> <span data-ttu-id="3b797-144">기본적으로 타임스탬프 값이 추적 로그 파일 이름에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="3b797-144">By default, timestamp values are appended to trace log file names.</span></span> <span data-ttu-id="3b797-145">이 값은 " tid, time"으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="3b797-145">This value is set to " tid, time ".</span></span> <span data-ttu-id="3b797-146">이 설정은 수정하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="3b797-146">Do not modify this setting.</span></span>|  
|<span data-ttu-id="3b797-147">**TraceListeners**</span><span class="sxs-lookup"><span data-stu-id="3b797-147">**TraceListeners**</span></span>|<span data-ttu-id="3b797-148">추적 로그 내용을 출력할 대상을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3b797-148">Specifies a target for outputting trace log content.</span></span> <span data-ttu-id="3b797-149">대상이 여러 개일 경우 쉼표로 구분하여 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3b797-149">You can specify multiple targets using a comma to separate each one.</span></span> <span data-ttu-id="3b797-150">유효한 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="3b797-150">Valid values include:</span></span><br /><br /> <span data-ttu-id="3b797-151">DebugWindow(기본값)</span><span class="sxs-lookup"><span data-stu-id="3b797-151">DebugWindow (default)</span></span><br /><br /> <span data-ttu-id="3b797-152">File(기본값)</span><span class="sxs-lookup"><span data-stu-id="3b797-152">File (default)</span></span><br /><br /> <span data-ttu-id="3b797-153">StdOut</span><span class="sxs-lookup"><span data-stu-id="3b797-153">StdOut</span></span>|  
|<span data-ttu-id="3b797-154">**TraceFileMode**</span><span class="sxs-lookup"><span data-stu-id="3b797-154">**TraceFileMode**</span></span>|<span data-ttu-id="3b797-155">추적 로그에 24시간 동안의 데이터를 포함할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3b797-155">Specifies whether trace logs contain data for a 24-hour period.</span></span> <span data-ttu-id="3b797-156">일별로 각 구성 요소마다 고유한 추적 로그가 하나씩 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3b797-156">You should have one unique trace log for each component on each day.</span></span> <span data-ttu-id="3b797-157">이 값은 "Unique(기본값)"로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="3b797-157">This value is set to "Unique (default)".</span></span> <span data-ttu-id="3b797-158">이 값은 수정하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="3b797-158">Do not modify this value.</span></span>|  
|<span data-ttu-id="3b797-159">**Components**</span><span class="sxs-lookup"><span data-stu-id="3b797-159">**Components**</span></span>|<span data-ttu-id="3b797-160">추적 로그를 생성할 구성 요소를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3b797-160">Specifies the components for which trace logs are created.</span></span> <span data-ttu-id="3b797-161">기본값은 `all`입니다.</span><span class="sxs-lookup"><span data-stu-id="3b797-161">The default value is `all`.</span></span> <span data-ttu-id="3b797-162">이 설정에 대한 기타 유효한 값에는 내부 구성 요소의 이름이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="3b797-162">Other valid values for this setting include the names of internal components.</span></span> <span data-ttu-id="3b797-163">이 값은 수정하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="3b797-163">Do not modify this value.</span></span>|  
|<span data-ttu-id="3b797-164">**런타임에서**</span><span class="sxs-lookup"><span data-stu-id="3b797-164">**Runtime**</span></span>|<span data-ttu-id="3b797-165">이전 버전과의 호환성을 지원하는 구성 설정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3b797-165">Specifies configuration settings that support backward compatibility with the previous version.</span></span> <span data-ttu-id="3b797-166">런타임 설정은 이전 버전의 Microsoft.ReportingServices.Interfaces를 대상으로 하는 요청을 새 버전으로 리디렉션하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="3b797-166">Runtime settings are used to redirect requests that target the previous version of Microsoft.ReportingServices.Interfaces to the new version.</span></span><br /><br /> <span data-ttu-id="3b797-167">이 섹션의 모든 구성 설정은 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 제품 설명서에 설명되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3b797-167">All of the configuration settings in this section are described in the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] product documentation.</span></span> <span data-ttu-id="3b797-168">자세한 내용을 보려면 MSDN 웹 사이트 또는 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 설명서에서 "Runtime Schema Settings"를 검색하십시오.</span><span class="sxs-lookup"><span data-stu-id="3b797-168">For more information, search for "Runtime Schema Settings" on the MSDN Web site or in the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] documentation.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3b797-169">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3b797-169">See Also</span></span>  
 <span data-ttu-id="3b797-170">[Reporting Services 구성 파일](reporting-services-configuration-files.md) </span><span class="sxs-lookup"><span data-stu-id="3b797-170">[Reporting Services Configuration Files](reporting-services-configuration-files.md) </span></span>  
 [<span data-ttu-id="3b797-171">보고서 서버 서비스 추적 로그</span><span class="sxs-lookup"><span data-stu-id="3b797-171">Report Server Service Trace Log</span></span>](report-server-service-trace-log.md)  
  
  
