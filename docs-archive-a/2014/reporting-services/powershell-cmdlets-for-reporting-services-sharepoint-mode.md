---
title: Reporting Services SharePoint 모드에 대 한 PowerShell cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 7835bc97-2827-4215-b0dd-52f692ce5e02
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2b20ad870fd8a9cd7f220eebb2b954d7a88a10c3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742896"
---
# <a name="powershell-cmdlets-for-reporting-services-sharepoint-mode"></a><span data-ttu-id="bdae2-102">Reporting Services SharePoint 모드용 PowerShell cmdlet</span><span class="sxs-lookup"><span data-stu-id="bdae2-102">PowerShell cmdlets for Reporting Services SharePoint Mode</span></span>
  <span data-ttu-id="bdae2-103">[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Sharepoint 모드를 설치 하는 경우 sharepoint 모드에서 보고서 서버를 지원 하기 위해 PowerShell cmdlet이 설치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bdae2-103">When you install [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint mode, PowerShell cmdlets are installed to support report Servers in SharePoint mode.</span></span> <span data-ttu-id="bdae2-104">cmdlet은 세 가지 범주의 기능을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="bdae2-104">The cmdlets cover three categories of functionality.</span></span>  
  
-   <span data-ttu-id="bdae2-105">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint 공유 서비스 및 프록시 설치</span><span class="sxs-lookup"><span data-stu-id="bdae2-105">Installation of the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint shared service and proxy.</span></span>  
  
-   <span data-ttu-id="bdae2-106">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 서비스 애플리케이션과 연결된 프록시의 프로비전 및 관리</span><span class="sxs-lookup"><span data-stu-id="bdae2-106">Provisioning and management of [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] service applications and associated proxies.</span></span>  
  
-   <span data-ttu-id="bdae2-107">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 기능(예: 확장 및 암호화 키) 관리</span><span class="sxs-lookup"><span data-stu-id="bdae2-107">Management of [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] features, for example extensions and encryption keys.</span></span>  
  
||  
|-|  
|[!INCLUDE[applies](../includes/applies-md.md)]<span data-ttu-id="bdae2-108">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]SharePoint 모드</span><span class="sxs-lookup"><span data-stu-id="bdae2-108">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint Mode</span></span>|  
  
 <span data-ttu-id="bdae2-109">**이 항목은 다음과 같이 구성되어 있습니다.**</span><span class="sxs-lookup"><span data-stu-id="bdae2-109">**This topic contains the following:**</span></span>  
  
-   [<span data-ttu-id="bdae2-110">Cmdlet 요약</span><span class="sxs-lookup"><span data-stu-id="bdae2-110">Cmdlet Summary</span></span>](#bkmk_cmdlet_sum)  
  
-   [<span data-ttu-id="bdae2-111">공유 서비스 및 프록시 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="bdae2-111">Shared Service and Proxy Cmdlets</span></span>](#bkmk_sharedservice_cmdlets)  
  
-   [<span data-ttu-id="bdae2-112">서비스 응용 프로그램 및 프록시 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="bdae2-112">Service Application and Proxy Cmdlets</span></span>](#bkmk_serviceapp_cmdlets)  
  
-   [<span data-ttu-id="bdae2-113">사용자 지정 기능 Cmdlet Reporting Services</span><span class="sxs-lookup"><span data-stu-id="bdae2-113">Reporting Services Custom Functionality Cmdlets</span></span>](#bkmk_ssrsfeatures_cmdlets)  
  
-   [<span data-ttu-id="bdae2-114">기본 샘플</span><span class="sxs-lookup"><span data-stu-id="bdae2-114">Basic Samples</span></span>](#bkmk_basic_samples)  
  
-   [<span data-ttu-id="bdae2-115">자세한 샘플</span><span class="sxs-lookup"><span data-stu-id="bdae2-115">Detailed Samples</span></span>](#bkmk_detailedsamples)  
  
    -   [<span data-ttu-id="bdae2-116">Reporting Services 서비스 응용 프로그램 및 프록시 만들기</span><span class="sxs-lookup"><span data-stu-id="bdae2-116">Create a Reporting Services service application and proxy</span></span>](#bkmk_example_create_service_application)  
  
    -   [<span data-ttu-id="bdae2-117">Reporting Services 배달 확장 프로그램 검토 및 업데이트</span><span class="sxs-lookup"><span data-stu-id="bdae2-117">Review and update a Reporting Services delivery extension</span></span>](#bkmk_example_delivery_extension)  
  
    -   [<span data-ttu-id="bdae2-118">Reporting Services 애플리케이션 데이터베이스의 속성 가져오기 및 설정(예: 데이터베이스 시간 제한)</span><span class="sxs-lookup"><span data-stu-id="bdae2-118">Get and set properties of the Reporting Servicea application database, for example database timeout</span></span>](#bkmk_example_db_properties)  
  
    -   [<span data-ttu-id="bdae2-119">Reporting services 데이터 확장 프로그램 나열-SharePoint 모드</span><span class="sxs-lookup"><span data-stu-id="bdae2-119">List reporting services data extensions - SharePoint mode</span></span>](#bkmk_example_list_data_extensions)  
  
    -   [<span data-ttu-id="bdae2-120">구독 소유자 변경 및 나열</span><span class="sxs-lookup"><span data-stu-id="bdae2-120">Change and list subscription owners</span></span>](#bkmk_change_subscription_owner)  
  
##  <a name="cmdlet-summary"></a><a name="bkmk_cmdlet_sum"></a><span data-ttu-id="bdae2-121">Cmdlet 요약</span><span class="sxs-lookup"><span data-stu-id="bdae2-121">Cmdlet Summary</span></span>  

 <span data-ttu-id="bdae2-122">cmdlet을 실행하려면 SharePoint 관리 셸을 열어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bdae2-122">To run the cmdlets you need to open the SharePoint Management Shell.</span></span> <span data-ttu-id="bdae2-123">Microsoft Windows에 포함된 그래픽 사용자 인터페이스 편집기인 **Windows PowerShell ISE(통합 스크립팅 환경)** 를 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bdae2-123">You can also use the graphical user interface editor that is included with Microsoft Windows, **Windows PowerShell Integrated Scripting Environment (ISE)**.</span></span> <span data-ttu-id="bdae2-124">자세한 내용은 [Windows Server에서 Windows PowerShell 시작](https://docs.microsoft.com/powershell/scripting/getting-started/starting-windows-powershell)를 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bdae2-124">For more information, see [Starting Windows PowerShell on Windows Server](https://docs.microsoft.com/powershell/scripting/getting-started/starting-windows-powershell).</span></span> <span data-ttu-id="bdae2-125">다음 cmdlet 요약에서 서비스 응용 프로그램 ' 데이터베이스 '에 대 한 참조는 서비스 응용 프로그램에서 만들고 사용 하는 모든 데이터베이스를 참조 합니다 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="bdae2-125">In the following cmdlet summaries, the references to service application 'databases', refer to all of the databases created and used by a [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] service application.</span></span> <span data-ttu-id="bdae2-126">여기에는 구성, 경고 및 임시 데이터베이스가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="bdae2-126">This includes the configuration, alerting, and temp databases.</span></span>  

  
 <span data-ttu-id="bdae2-127">PowerShell 예제를 입력할 때 다음과 비슷한 오류 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="bdae2-127">If you see an error message similar to the following when you type the PowerShell examples:</span></span>  
  
-   <span data-ttu-id="bdae2-128">Install-SPRSService : 'Install-SPRSService' 용어는</span><span class="sxs-lookup"><span data-stu-id="bdae2-128">Install-SPRSService : The term 'Install-SPRSService' is not recognized as the</span></span>  
    <span data-ttu-id="bdae2-129">cmdlet, 함수, 스크립트 파일 또는 실행 프로그램의 이름으로 인식되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bdae2-129">name of a cmdlet, function, script file, or operable program.</span></span> <span data-ttu-id="bdae2-130">이름의 철자를 확인하거나 경로가 포함되어 있으면 경로가 올바른지 확인하고 다시 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="bdae2-130">Check the spelling of the name, or if a path was included, verify that the path is correct and try again.</span></span>  
  
 <span data-ttu-id="bdae2-131">다음 문제 중 하나가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="bdae2-131">One of the following issues is occurring:</span></span>  
  
-   [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] <span data-ttu-id="bdae2-132">SharePoint 모드가 설치되어 있지 않으므로 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] cmdlet이 설치되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="bdae2-132">SharePoint mode is not installed and therefore the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] cmdlets are not installed.</span></span>  
  
-   <span data-ttu-id="bdae2-133">SharePoint 관리 셸 대신 Windows PowerShell 또는 Windows PowerShell ISE에서 PowerShell 명령을 실행했습니다.</span><span class="sxs-lookup"><span data-stu-id="bdae2-133">You ran the PowerShell command in Windows PowerShell or Windows PowerShell ISE instead of the SharePoint Management Shell.</span></span> <span data-ttu-id="bdae2-134">SharePoint 관리 셸을 사용하거나 다음 명령을 사용하여 Windows PowerShell 창에 SharePoint 스냅인을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="bdae2-134">Use the SharePoint Management shell or add the SharePoint Snap-in to the Windows PowerShell window with the following command:</span></span>  
  
    ```powershell
    Add-PSSnapin Microsoft.SharePoint.PowerShell  
    ```  
  
 <span data-ttu-id="bdae2-135">자세한 내용은 [Windows PowerShell을 사용 하 여 SharePoint 2013 () 관리를](https://technet.microsoft.com/library/ee806878.aspx) 참조 하세요 https://technet.microsoft.com/library/ee806878.aspx) .</span><span class="sxs-lookup"><span data-stu-id="bdae2-135">For more information see [Use Windows PowerShell to administer SharePoint 2013](https://technet.microsoft.com/library/ee806878.aspx) (https://technet.microsoft.com/library/ee806878.aspx).</span></span>  
  
#### <a name="to-open-the-sharepoint-management-shell-and-run-cmdlets"></a><span data-ttu-id="bdae2-136">SharePoint 관리 셸을 열고 cmdlet을 실행하려면</span><span class="sxs-lookup"><span data-stu-id="bdae2-136">To Open the SharePoint Management Shell and run cmdlets</span></span>  
  
1.  <span data-ttu-id="bdae2-137">**시작** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bdae2-137">Click the **Start** button</span></span>  
  
2.  <span data-ttu-id="bdae2-138">**Microsoft SharePoint 제품** 그룹을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bdae2-138">Click the **Microsoft SharePoint Products** group.</span></span>  
  
3.  <span data-ttu-id="bdae2-139">**SharePoint 관리 셸**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bdae2-139">Click the **SharePoint Management Shell**.</span></span>  
  
 <span data-ttu-id="bdae2-140">cmdlet의 명령줄 도움말을 보려면 PowerShell 명령 프롬프트에서 PowerShell 'Get-Help' 명령을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="bdae2-140">To view command line help for a cmdlet use the PowerShell 'Get-Help' command at the PowerShell command prompt.</span></span> <span data-ttu-id="bdae2-141">예:</span><span class="sxs-lookup"><span data-stu-id="bdae2-141">For example:</span></span>  
  
 `Get-Help Get-SPRSServiceApplicationServers`  
  
###  <a name="shared-service-and-proxy-cmdlets"></a><a name="bkmk_sharedservice_cmdlets"></a> <span data-ttu-id="bdae2-142">공유 서비스 및 프록시 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="bdae2-142">Shared Service and Proxy Cmdlets</span></span>  
 <span data-ttu-id="bdae2-143">다음 표에는 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint 공유 서비스에 대한 PowerShell cmdlet이 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bdae2-143">The following table contains the PowerShell cmdlets for the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint shared service.</span></span>  
  
|<span data-ttu-id="bdae2-144">cmdlet</span><span class="sxs-lookup"><span data-stu-id="bdae2-144">Cmdlet</span></span>|<span data-ttu-id="bdae2-145">설명</span><span class="sxs-lookup"><span data-stu-id="bdae2-145">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="bdae2-146">Install-SPRSService</span><span class="sxs-lookup"><span data-stu-id="bdae2-146">Install-SPRSService</span></span>|<span data-ttu-id="bdae2-147">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 공유 서비스를 설치 및 등록 또는 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="bdae2-147">Installs and registers, or uninstalls, the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] shared service.</span></span> <span data-ttu-id="bdae2-148">이 작업은 SharePoint 모드에서 SQL Server [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 가 설치된 시스템에서만 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bdae2-148">This can be done only on the machine that has an installation of SQL Server [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] in SharePoint mode.</span></span> <span data-ttu-id="bdae2-149">설치 시 다음 두 가지 작업이 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="bdae2-149">For installation, two operations occur:</span></span><br /><br /> <span data-ttu-id="bdae2-150">1) [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 서비스는 팜에 설치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bdae2-150">1) The [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] service is installed in the farm.</span></span><br /><br /> <span data-ttu-id="bdae2-151">2) [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 서비스 인스턴스가 현재 컴퓨터에 설치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bdae2-151">2) The [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] service instance is installed to the current machine.</span></span><br /><br /> <span data-ttu-id="bdae2-152">제거 시 다음 두 가지 작업이 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="bdae2-152">For Uninstallation, two operations occur:</span></span><br /><span data-ttu-id="bdae2-153">1) [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 현재 컴퓨터에서 서비스가 제거 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bdae2-153">1) The [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] service is uninstalled from the current machine.</span></span><br /><span data-ttu-id="bdae2-154">2) [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 서비스를 팜에서 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="bdae2-154">2) The [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] service is uninstalled from the farm.</span></span><br /><br /> <br /><br /> <span data-ttu-id="bdae2-155">참고: 팜 내 다른 시스템에 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 서비스가 설치되어 있거나 팜에서 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 서비스 애플리케이션이 실행되고 있는 경우 경고 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="bdae2-155">NOTE: If there are any other machines in the farm that have the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] service installed, or if there are still [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] service applications running in the farm, a warning message is displayed.</span></span>|  
|<span data-ttu-id="bdae2-156">Install-SPRSServiceProxy</span><span class="sxs-lookup"><span data-stu-id="bdae2-156">Install-SPRSServiceProxy</span></span>|<span data-ttu-id="bdae2-157">SharePoint 팜에 Reporting Services 서비스 프록시를 설치 및 등록 또는 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="bdae2-157">Installs and registers, or uninstalls, the Reporting Services service proxy in the SharePoint farm.</span></span>|  
|<span data-ttu-id="bdae2-158">Get-SPRSProxyUrl</span><span class="sxs-lookup"><span data-stu-id="bdae2-158">Get-SPRSProxyUrl</span></span>|<span data-ttu-id="bdae2-159">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 서비스 액세스를 위한 URL을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="bdae2-159">Gets the URL(s) for accessing the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] service.</span></span>|  
|<span data-ttu-id="bdae2-160">Get-SPRSServiceApplicationServers</span><span class="sxs-lookup"><span data-stu-id="bdae2-160">Get-SPRSServiceApplicationServers</span></span>|<span data-ttu-id="bdae2-161">로컬 SharePoint 팜 내 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 공유 서비스가 설치된 모든 서버를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="bdae2-161">Gets all servers in the local SharePoint farm that contain an installation of the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] shared service.</span></span> <span data-ttu-id="bdae2-162">이 cmdlet은 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 업그레이드 시 공유 서비스를 실행하므로 업그레이드되어야 하는 서버를 확인하는 데 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="bdae2-162">This cmdlet is useful for [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] upgrades, to determine which servers run the shared service and therefore need to be upgraded.</span></span>|  
  
###  <a name="service-application-and-proxy-cmdlets"></a><a name="bkmk_serviceapp_cmdlets"></a> <span data-ttu-id="bdae2-163">서비스 애플리케이션 및 프록시 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="bdae2-163">Service Application and Proxy Cmdlets</span></span>  
 <span data-ttu-id="bdae2-164">다음 표에는 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 서비스 애플리케이션과 관련 프록시에 대한 PowerShell cmdlet이 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bdae2-164">The following table contains the PowerShell cmdlets for [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] service applications and their associated proxies.</span></span>  
  
|<span data-ttu-id="bdae2-165">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="bdae2-165">cmdlet</span></span>|<span data-ttu-id="bdae2-166">설명</span><span class="sxs-lookup"><span data-stu-id="bdae2-166">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="bdae2-167">Get-SPRSServiceApplication</span><span class="sxs-lookup"><span data-stu-id="bdae2-167">Get-SPRSServiceApplication</span></span>|<span data-ttu-id="bdae2-168">하나 이상의 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 서비스 애플리케이션 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="bdae2-168">Gets one or more [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] service application objects.</span></span>|  
|<span data-ttu-id="bdae2-169">New-SPRSServiceApplication</span><span class="sxs-lookup"><span data-stu-id="bdae2-169">New-SPRSServiceApplication</span></span>|<span data-ttu-id="bdae2-170">새 Reporting Services 서비스 애플리케이션 및 연결된 데이터베이스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="bdae2-170">Create a new Reporting Services service application and associated databases.</span></span><br /><br /> <span data-ttu-id="bdae2-171">LogonType 매개 변수: 보고서 서버에서 보고서 서버 데이터베이스에 액세스하기 위해 SSRS 애플리케이션 풀 계정 또는 SQL Server 로그인을 사용하는지를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="bdae2-171">LogonType Parameter: Specifies if the report server uses the SSRS Application Pool account or a SQL Server login to access the report server database.</span></span> <span data-ttu-id="bdae2-172">다음 중 하나일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bdae2-172">It can be one of the following:</span></span><br /><br /> <span data-ttu-id="bdae2-173">0 Windows 인증</span><span class="sxs-lookup"><span data-stu-id="bdae2-173">0 Windows Authentication</span></span><br /><br /> <span data-ttu-id="bdae2-174">1 SQL Server</span><span class="sxs-lookup"><span data-stu-id="bdae2-174">1 SQL Server</span></span><br /><br /> <span data-ttu-id="bdae2-175">2 애플리케이션 풀 계정(기본값)</span><span class="sxs-lookup"><span data-stu-id="bdae2-175">2 Application Pool Account (default)</span></span>|  
|<span data-ttu-id="bdae2-176">Remove-SPRSServiceApplication</span><span class="sxs-lookup"><span data-stu-id="bdae2-176">Remove-SPRSServiceApplication</span></span>|<span data-ttu-id="bdae2-177">지정된 Reporting Services 서비스 애플리케이션을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="bdae2-177">Removes the specified Reporting Services service application.</span></span> <span data-ttu-id="bdae2-178">그러면 연결된 데이터베이스도 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="bdae2-178">This will also remove the associated databases.</span></span>|  
|<span data-ttu-id="bdae2-179">Set-SPRSServiceApplication</span><span class="sxs-lookup"><span data-stu-id="bdae2-179">Set-SPRSServiceApplication</span></span>|<span data-ttu-id="bdae2-180">기존 Reporting Services 서비스 애플리케이션의 속성을 편집합니다.</span><span class="sxs-lookup"><span data-stu-id="bdae2-180">Edits the properties of an existing Reporting Services service application.</span></span>|  
|<span data-ttu-id="bdae2-181">New-SPRSServiceApplicationProxy</span><span class="sxs-lookup"><span data-stu-id="bdae2-181">New-SPRSServiceApplicationProxy</span></span>|<span data-ttu-id="bdae2-182">새 Reporting Services 서비스 애플리케이션 프록시를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="bdae2-182">Creates a new Reporting Services service application proxy.</span></span>|  
|<span data-ttu-id="bdae2-183">Get-SPRSServiceApplicationProxy</span><span class="sxs-lookup"><span data-stu-id="bdae2-183">Get-SPRSServiceApplicationProxy</span></span>|<span data-ttu-id="bdae2-184">하나 이상의 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 서비스 애플리케이션 프록시를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="bdae2-184">Gets one or more [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] service application proxies.</span></span>|  
|<span data-ttu-id="bdae2-185">Dismount-SPRSDatabase</span><span class="sxs-lookup"><span data-stu-id="bdae2-185">Dismount-SPRSDatabase</span></span>|<span data-ttu-id="bdae2-186">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 서비스 애플리케이션에 대한 서비스 애플리케이션 데이터베이스를 분리합니다.</span><span class="sxs-lookup"><span data-stu-id="bdae2-186">Dismounts the service application databases for a [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] service application.</span></span>|  
|<span data-ttu-id="bdae2-187">Remove-SPRSDatabase</span><span class="sxs-lookup"><span data-stu-id="bdae2-187">Remove-SPRSDatabase</span></span>|<span data-ttu-id="bdae2-188">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 서비스 애플리케이션에 대한 서비스 애플리케이션 데이터베이스를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="bdae2-188">Remove the service application databases for a [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] service application.</span></span>|  
|<span data-ttu-id="bdae2-189">Set-SPRSDatabase</span><span class="sxs-lookup"><span data-stu-id="bdae2-189">Set-SPRSDatabase</span></span>|<span data-ttu-id="bdae2-190">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 서비스 애플리케이션에 연결된 데이터베이스의 속성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="bdae2-190">Sets the properties of the databases associated to a [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] service application.</span></span>|  
|<span data-ttu-id="bdae2-191">Mount-SPRSDatabase</span><span class="sxs-lookup"><span data-stu-id="bdae2-191">Mount-SPRSDatabase</span></span>|<span data-ttu-id="bdae2-192">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 서비스 애플리케이션에 대한 데이터베이스를 탑재합니다.</span><span class="sxs-lookup"><span data-stu-id="bdae2-192">Mounts databases for a [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] service application.</span></span>|  
|<span data-ttu-id="bdae2-193">New-SPRSDatabase</span><span class="sxs-lookup"><span data-stu-id="bdae2-193">New-SPRSDatabase</span></span>|<span data-ttu-id="bdae2-194">지정된 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 서비스 애플리케이션에 대해 새 서비스 애플리케이션 데이터베이스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="bdae2-194">Create new service application databases for the specified [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] service application.</span></span>|  
|<span data-ttu-id="bdae2-195">Get-SPRSDatabaseCreationScript</span><span class="sxs-lookup"><span data-stu-id="bdae2-195">Get-SPRSDatabaseCreationScript</span></span>|<span data-ttu-id="bdae2-196">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 서비스 애플리케이션 데이터베이스 화면에 데이터베이스 생성 스크립트를 출력합니다.</span><span class="sxs-lookup"><span data-stu-id="bdae2-196">Outputs the database creation script to the screen for a [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] service application.</span></span> <span data-ttu-id="bdae2-197">그런 다음 SQL Server Management Studio에서 스크립트를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bdae2-197">You can then run the script in SQL Server Management Studio.</span></span>|  
|<span data-ttu-id="bdae2-198">Get-SPRSDatabase</span><span class="sxs-lookup"><span data-stu-id="bdae2-198">Get-SPRSDatabase</span></span>|<span data-ttu-id="bdae2-199">하나 이상의 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 서비스 애플리케이션 데이터베이스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="bdae2-199">Gets one or more [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] service application databases.</span></span> <span data-ttu-id="bdae2-200">이 명령을 사용하여 서비스 애플리케이션 데이터베이스의 ID를 가져오므로, Set-SPRSDatabase comdlet을 사용하여 속성(예: `querytimeout`)을 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bdae2-200">Use the command to get the ID of service application database so you can use the Set-SPRSDatabase comdlet to modify properties, for example the `querytimeout`.</span></span> <span data-ttu-id="bdae2-201">이 항목의 예제를 참조 하십시오. [Reporting Servicea 응용 프로그램 데이터베이스의 속성 가져오기 및 설정 (예: 데이터베이스 시간 제한](#bkmk_example_db_properties)).</span><span class="sxs-lookup"><span data-stu-id="bdae2-201">See the example in this topic, [Get and set properties of the Reporting Servicea application database, for example database timeout](#bkmk_example_db_properties).</span></span>|  
|<span data-ttu-id="bdae2-202">Get-SPRSDatabaseRightsScript</span><span class="sxs-lookup"><span data-stu-id="bdae2-202">Get-SPRSDatabaseRightsScript</span></span>|<span data-ttu-id="bdae2-203">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 서비스 애플리케이션 데이터베이스 화면에 데이터베이스 권한 스크립트를 출력합니다.</span><span class="sxs-lookup"><span data-stu-id="bdae2-203">Outputs the database rights script to the screen for a [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] service application.</span></span> <span data-ttu-id="bdae2-204">원하는 사용자에 대한 프롬프트를 표시한 후 데이터베이스에서 사용 권한을 수정하기 위해 실행할 수 있는 Transact-SQL을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="bdae2-204">It will prompt for desired user and database then returns transact SQL you can run to modify permissions.</span></span> <span data-ttu-id="bdae2-205">그런 다음 SQL Server Management Studio에서 이 스크립트를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bdae2-205">You can then run this script in SQL Server Management Studio.</span></span>|  
|<span data-ttu-id="bdae2-206">Get-SPRSDatabaseUpgradeScript</span><span class="sxs-lookup"><span data-stu-id="bdae2-206">Get-SPRSDatabaseUpgradeScript</span></span>|<span data-ttu-id="bdae2-207">화면에 데이터베이스 업그레이드 스크립트를 출력합니다.</span><span class="sxs-lookup"><span data-stu-id="bdae2-207">Outputs a database upgrade script to the screen.</span></span> <span data-ttu-id="bdae2-208">이 스크립트는 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 서비스 애플리케이션 데이터베이스를 현재 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 설치의 데이터베이스 버전으로 업그레이드합니다.</span><span class="sxs-lookup"><span data-stu-id="bdae2-208">The script will upgrade [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] service application databases to the database version of the current [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] installation.</span></span>|  
  
###  <a name="reporting-services-custom-functionality-cmdlets"></a><a name="bkmk_ssrsfeatures_cmdlets"></a> <span data-ttu-id="bdae2-209">Reporting Services 사용자 지정 기능 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="bdae2-209">Reporting Services Custom Functionality Cmdlets</span></span>  
  
|<span data-ttu-id="bdae2-210">cmdlet</span><span class="sxs-lookup"><span data-stu-id="bdae2-210">Cmdlet</span></span>|<span data-ttu-id="bdae2-211">설명</span><span class="sxs-lookup"><span data-stu-id="bdae2-211">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="bdae2-212">Update-SPRSEncryptionKey</span><span class="sxs-lookup"><span data-stu-id="bdae2-212">Update-SPRSEncryptionKey</span></span>|<span data-ttu-id="bdae2-213">지정된 Reporting Services 서비스 애플리케이션에 대한 암호화 키를 업데이트하고 데이터를 다시 암호화합니다.</span><span class="sxs-lookup"><span data-stu-id="bdae2-213">Updates the encryption key for the specified Reporting Services service application and re-encrypts its data.</span></span>|  
|<span data-ttu-id="bdae2-214">Restore-SPRSEncryptionKey</span><span class="sxs-lookup"><span data-stu-id="bdae2-214">Restore-SPRSEncryptionKey</span></span>|<span data-ttu-id="bdae2-215">Reporting Services 서비스 애플리케이션에 대해 이전에 백업된 암호화 키를 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="bdae2-215">Restores a previously backed up encryption key for a Reporting Services service application.</span></span>|  
|<span data-ttu-id="bdae2-216">Remove-SPRSEncryptedData</span><span class="sxs-lookup"><span data-stu-id="bdae2-216">Remove-SPRSEncryptedData</span></span>|<span data-ttu-id="bdae2-217">지정된 Reporting Services 서비스 애플리케이션에 대한 암호화된 데이터를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="bdae2-217">Delete the encrypted data for the specified Reporting Services service application.</span></span>|  
|<span data-ttu-id="bdae2-218">Backup-SPRSEncryptionKey</span><span class="sxs-lookup"><span data-stu-id="bdae2-218">Backup-SPRSEncryptionKey</span></span>|<span data-ttu-id="bdae2-219">지정된 Reporting Services 서비스 애플리케이션에 대한 암호화 키를 백업합니다.</span><span class="sxs-lookup"><span data-stu-id="bdae2-219">Backs up the encryption key for the specified Reporting Services service application.</span></span>|  
|<span data-ttu-id="bdae2-220">New-SPRSExtension</span><span class="sxs-lookup"><span data-stu-id="bdae2-220">New-SPRSExtension</span></span>|<span data-ttu-id="bdae2-221">Reporting Services 서비스 애플리케이션의 새 확장 프로그램을 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="bdae2-221">Registers a new extension with a Reporting Services service application.</span></span>|  
|<span data-ttu-id="bdae2-222">Set-SPRSExtension</span><span class="sxs-lookup"><span data-stu-id="bdae2-222">Set-SPRSExtension</span></span>|<span data-ttu-id="bdae2-223">기존 Reporting Services 확장 프로그램의 속성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="bdae2-223">Sets the properties of an existing Reporting Services extension.</span></span>|  
|<span data-ttu-id="bdae2-224">Remove-SPRSExtension</span><span class="sxs-lookup"><span data-stu-id="bdae2-224">Remove-SPRSExtension</span></span>|<span data-ttu-id="bdae2-225">Reporting Services 서비스 애플리케이션에서 확장 프로그램을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="bdae2-225">Removes an extension from a Reporting Services service application.</span></span>|  
|<span data-ttu-id="bdae2-226">Get-SPRSExtension</span><span class="sxs-lookup"><span data-stu-id="bdae2-226">Get-SPRSExtension</span></span>|<span data-ttu-id="bdae2-227">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 서비스 애플리케이션에 대해 하나 이상의 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 확장을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="bdae2-227">Gets one or more [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] extensions for a [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] service application.</span></span><br /><br /> <span data-ttu-id="bdae2-228">유효한 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="bdae2-228">Valid values are:</span></span><br /><br /> <span data-ttu-id="bdae2-229">**배달**</span><span class="sxs-lookup"><span data-stu-id="bdae2-229">**Delivery**</span></span><br /><br /> <span data-ttu-id="bdae2-230">**DeliveryUI**</span><span class="sxs-lookup"><span data-stu-id="bdae2-230">**DeliveryUI**</span></span><br /><br /> <span data-ttu-id="bdae2-231">**렌더링**</span><span class="sxs-lookup"><span data-stu-id="bdae2-231">**Render**</span></span><br /><br /> <span data-ttu-id="bdae2-232">**Data**</span><span class="sxs-lookup"><span data-stu-id="bdae2-232">**Data**</span></span><br /><br /> <span data-ttu-id="bdae2-233">**보안**</span><span class="sxs-lookup"><span data-stu-id="bdae2-233">**Security**</span></span><br /><br /> <span data-ttu-id="bdae2-234">**인증**</span><span class="sxs-lookup"><span data-stu-id="bdae2-234">**Authentication**</span></span><br /><br /> <span data-ttu-id="bdae2-235">**EventProcessing**</span><span class="sxs-lookup"><span data-stu-id="bdae2-235">**EventProcessing**</span></span><br /><br /> <span data-ttu-id="bdae2-236">**ReportItems**</span><span class="sxs-lookup"><span data-stu-id="bdae2-236">**ReportItems**</span></span><br /><br /> <span data-ttu-id="bdae2-237">**Designer**</span><span class="sxs-lookup"><span data-stu-id="bdae2-237">**Designer**</span></span><br /><br /> <span data-ttu-id="bdae2-238">**ReportItemDesigner**</span><span class="sxs-lookup"><span data-stu-id="bdae2-238">**ReportItemDesigner**</span></span><br /><br /> <span data-ttu-id="bdae2-239">**ReportItemConverter**</span><span class="sxs-lookup"><span data-stu-id="bdae2-239">**ReportItemConverter**</span></span><br /><br /> <span data-ttu-id="bdae2-240">**ReportDefinitionCustomization**</span><span class="sxs-lookup"><span data-stu-id="bdae2-240">**ReportDefinitionCustomization**</span></span>|  
|<span data-ttu-id="bdae2-241">Get-SPRSSite</span><span class="sxs-lookup"><span data-stu-id="bdae2-241">Get-SPRSSite</span></span>|<span data-ttu-id="bdae2-242">"ReportingService" 기능 사용 여부에 따라 SharePoint 사이트를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="bdae2-242">Gets the SharePoint sites based on whether the "ReportingService" feature is enabled.</span></span> <span data-ttu-id="bdae2-243">기본적으로 "ReportingService" 기능이 설정되어 있는 사이트가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="bdae2-243">By default, sites that enable the "ReportingService" feature are returned.</span></span>|  
  
##  <a name="basic-samples"></a><a name="bkmk_basic_samples"></a><span data-ttu-id="bdae2-244">기본 샘플</span><span class="sxs-lookup"><span data-stu-id="bdae2-244">Basic Samples</span></span>  
 <span data-ttu-id="bdae2-245">이름에 'SPRS'가 포함된 cmdlet 목록을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="bdae2-245">Return a list of cmdlets that contain 'SPRS' in the name.</span></span> <span data-ttu-id="bdae2-246">이 목록은 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] cmdlet의 전체 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="bdae2-246">This will be the full list of [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] cmdlets.</span></span>  
  
```powershell
Get-command -noun *SPRS*  
```  
  
 <span data-ttu-id="bdae2-247">자세히 말해서 commandlist.txt라는 텍스트 파일로 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="bdae2-247">Or with a little more detail, piped to a text file named commandlist.txt</span></span>  
  
```powershell
Get-Command -Noun *SPRS* | Select name, definition | Format-List | Out-File c:\commandlist.txt  
```  
  
 <span data-ttu-id="bdae2-248">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint 서비스 및 서비스 프록시를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="bdae2-248">Install the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint service and service proxy.</span></span>  
  
```powershell
Install-SPRSService  
```  
  
```powershell
Install-SPRSServiceProxy  
```  
  
 <span data-ttu-id="bdae2-249">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 서비스 시작</span><span class="sxs-lookup"><span data-stu-id="bdae2-249">Start the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] service</span></span>  
  
```powershell
Get-SPServiceInstance -all | where {$_.TypeName -like "SQL Server Reporting*"} | Start-SPServiceInstance  
```  
  
 <span data-ttu-id="bdae2-250">로그 파일에서 필터링된 행 목록을 반환하려면 SharePoint 관리 셸에서 다음 명령을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="bdae2-250">Type the following command from the SharePoint Management Shell to return a filtered list of rows from the a log file.</span></span> <span data-ttu-id="bdae2-251">이 명령은 "ssrscustomactionerror"가 포함된 행에 대해 필터링합니다.</span><span class="sxs-lookup"><span data-stu-id="bdae2-251">The command will filter for lines that contain "ssrscustomactionerror".</span></span> <span data-ttu-id="bdae2-252">이 예제에서는 rssharepoint.msi를 설치할 때 만든 로그 파일을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="bdae2-252">This example is looking at the log file created when the rssharepoint.msi was installed.</span></span>  
  
```powershell
Get-Content -Path C:\Users\testuser\AppData\Local\Temp\rs_sp_0.log | Select-String "ssrscustomactionerror"  
```  
  
##  <a name="detailed-samples"></a><a name="bkmk_detailedsamples"></a><span data-ttu-id="bdae2-253">자세한 샘플</span><span class="sxs-lookup"><span data-stu-id="bdae2-253">Detailed Samples</span></span>  
 <span data-ttu-id="bdae2-254">다음 샘플 외에도 [Windows powershell 스크립트](../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2013.md#bkmk_full_script)항목의 "Windows powershell 스크립트" 섹션에서 1-4 단계를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="bdae2-254">In addition to the following samples, see the section "Windows PowerShell Script" in the topic [Windows PowerShell script for Steps 1-4](../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2013.md#bkmk_full_script).</span></span>  
  
###  <a name="create-a-reporting-services-service-application-and-proxy"></a><a name="bkmk_example_create_service_application"></a><span data-ttu-id="bdae2-255">Reporting Services 서비스 응용 프로그램 및 프록시 만들기</span><span class="sxs-lookup"><span data-stu-id="bdae2-255">Create a Reporting Services service application and proxy</span></span>  
 <span data-ttu-id="bdae2-256">이 예제 스크립트는 다음 태스크를 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="bdae2-256">This sample script completes the following tasks:</span></span>  
  
1.  <span data-ttu-id="bdae2-257">Reporting Services 서비스 애플리케이션 및 프록시를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="bdae2-257">Create a Reporting Services service application and proxy.</span></span> <span data-ttu-id="bdae2-258">이 스크립트는 "My App Pool" 애플리케이션 풀이 이미 있는 것으로 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="bdae2-258">The script assumes the application pool "My App Pool" already exists.</span></span>  
  
2.  <span data-ttu-id="bdae2-259">기본 프록시 그룹에 프록시 추가</span><span class="sxs-lookup"><span data-stu-id="bdae2-259">Add the proxy to the default proxy group</span></span>  
  
3.  <span data-ttu-id="bdae2-260">포트 80 웹앱의 콘텐츠 데이터베이스에 대한 서비스 앱 액세스를 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="bdae2-260">Grant the service app access to the port 80 web app's content database.</span></span> <span data-ttu-id="bdae2-261">이 스크립트는 "" 사이트가 이미 있다고 가정 http://sitename 합니다.</span><span class="sxs-lookup"><span data-stu-id="bdae2-261">The script assumes site "http://sitename" already exists.</span></span>  
  
```powershell
# Create service application and service application proxy  
$appPool = Get-SPServiceApplicationPool "My App Pool"  
$serviceApp = New-SPRSServiceApplication "My RS Service App" -ApplicationPool $appPool  
$serviceAppProxy = New-SPRSServiceApplicationProxy -Name "My RS Service App Proxy" -ServiceApplication $serviceApp  
  
# Add service application proxy to default proxy group.  Any web application that uses the default proxy group will now be able to use this service application.  
Get-SPServiceApplicationProxyGroup -default | Add-SPServiceApplicationProxyGroupMember -Member $serviceAppProxy  
  
# Grant application pool account access to the port 80 web application's content database.  
$webApp = Get-SPWebApplication "http://sitename"  
$appPoolAccountName = $appPool.ProcessAccount.LookupName()  
$webApp.GrantAccessToProcessIdentity($appPoolAccountName)
```  
  
###  <a name="review-and-update-a-reporting-services-delivery-extension"></a><a name="bkmk_example_delivery_extension"></a><span data-ttu-id="bdae2-262">Reporting Services 배달 확장 프로그램 검토 및 업데이트</span><span class="sxs-lookup"><span data-stu-id="bdae2-262">Review and update a Reporting Services delivery extension</span></span>  
 <span data-ttu-id="bdae2-263">다음 PowerShell 스크립트 예제에서 `My RS Service App`서비스 애플리케이션에 대해 보고서 서버 메일 배달 확장 프로그램의 구성을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="bdae2-263">The following PowerShell script example, updates the configuration for the report server e-mail delivery extension for the service application named `My RS Service App`.</span></span> <span data-ttu-id="bdae2-264">SMTP 서버(`<email server name>`) 및 FROM 메일 별칭(`<your FROM email address>`) 값을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="bdae2-264">Update the values for the SMTP server (`<email server name>`) and the FROM email alias (`<your FROM email address>`).</span></span>  
  
```powershell
$app = Get-SPRSServiceApplication -Name "My RS Service App"  
$emailCfg = Get-SPRSExtension -Identity $app -ExtensionType "Delivery" -Name "Report Server Email" | Select -ExpandProperty ConfigurationXml
$emailXml = [xml]$emailCfg
$emailXml.SelectSingleNode("//SMTPServer").InnerText = "<email server name>"  
$emailXml.SelectSingleNode("//SendUsing").InnerText = "2"  
$emailXml.SelectSingleNode("//SMTPAuthenticate").InnerText = "2"  
$emailXml.SelectSingleNode("//From").InnerText = '<your FROM email address>'  
Set-SPRSExtension -Identity $app -ExtensionType "Delivery" -Name "Report Server Email" -ExtensionConfiguration $emailXml.OuterXml  
```  
  
 <span data-ttu-id="bdae2-265">위의 예에서 서비스 애플리케이션의 정확한 이름을 모를 경우 부분 이름 검색을 기반으로 서비스 애플리케이션을 가져오도록 첫 번째 문을 다시 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bdae2-265">In the above example if you did not know the exact name of the service application, you could rewrite the first statement to get the service application based on a search of the partial name.</span></span> <span data-ttu-id="bdae2-266">예:</span><span class="sxs-lookup"><span data-stu-id="bdae2-266">For example:</span></span>  
  
```powershell
$app = Get-SPRSServiceApplication | Where {$_.name -like " ssrs_testapp *"}  
```  
  
 <span data-ttu-id="bdae2-267">다음 스크립트는 "Reporting Services 애플리케이션" 서비스 애플리케이션에 대해 보고서 서버 이메일 배달 확장 프로그램의 현재 구성 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="bdae2-267">The following script will return the current configuration values for the report server e-mail delivery extension for the service application named "Reporting Services Application".</span></span> <span data-ttu-id="bdae2-268">첫 번째 단계에서는 $app 변수 값을 "My RS Service App" 이름을 가진 서비스 애플리케이션의 개체로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="bdae2-268">The first step sets the value of the variable $app to the object of the service application that has a name of " My RS Service App "</span></span>  
  
 <span data-ttu-id="bdae2-269">두 번째 명령문은 $app 변수에서 서비스 애플리케이션 개체에 대한 'Report Server Email' 배달 확장 프로그램을 가져오고 configurationXML을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="bdae2-269">The second statement will Get the 'Report Server Email' delivery extension for the service application object in variable $app, and select the configurationXML</span></span>  
  
```powershell
$app = Get-SPRSServiceapplication -Name "Reporting Services Application"  
Get-SPRSExtension -Identity $app -ExtensionType "Delivery" -Name "Report Server Email" | Select -ExpandProperty ConfigurationXml  
```  
  
 <span data-ttu-id="bdae2-270">또한 다음과 같이 위의 두 문을 하나로 다시 쓸 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bdae2-270">You can also rewrite the above two statements as one:</span></span>  
  
```powershell
Get-SPRSServiceApplication -Name "Reporting Services Application" | Get-SPRSExtension -ExtensionType "Delivery" -Name "Report Server Email" | Select -ExpandProperty ConfigurationXml  
```  
  
###  <a name="get-and-set-properties-of-the-reporting-servicea-application-database-for-example-database-timeout"></a><a name="bkmk_example_db_properties"></a><span data-ttu-id="bdae2-271">Reporting Servicea 응용 프로그램 데이터베이스의 속성 가져오기 및 설정 (예: 데이터베이스 시간 제한)</span><span class="sxs-lookup"><span data-stu-id="bdae2-271">Get and set properties of the Reporting Servicea application database, for example database timeout</span></span>  
 <span data-ttu-id="bdae2-272">다음 예제에서는 데이터베이스 및 속성의 목록을 먼저 반환하므로 set 명령에 제공하는 데이터베이스 GUID(ID)를 결정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="bdae2-272">The following example first returns a list of the databases and properties so you can determine the database guid (ID) that you then supply to the set command.</span></span> <span data-ttu-id="bdae2-273">속성의 전체 목록은 `Get-SPRSDatabase | format-list`를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="bdae2-273">For a full list of the properties, use `Get-SPRSDatabase | format-list`.</span></span>  
  
```powershell
Get-SPRSDatabase | Select id, querytimeout,connectiontimeout, status, server, ServiceInstance
```  
  
 <span data-ttu-id="bdae2-274">다음은 출력의 예제입니다.</span><span class="sxs-lookup"><span data-stu-id="bdae2-274">The following is an example of the output.</span></span> <span data-ttu-id="bdae2-275">SET cmdlet에서 수정하고 사용할 데이터베이스의 ID를 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="bdae2-275">Determine the ID for the database you want to modify and use the ID in the SET cmdlet.</span></span>  
  
-   `Id                : 56f8d1bc-cb04-44cf-bd41-a873643c5a14`  
  
     `QueryTimeout      : 120`  
  
     `ConnectionTimeout : 15`  
  
     `Status            : Online`  
  
     `Server            : SPServer Name=uetestb01`  
  
     `ServiceInstance   : SPDatabaseServiceInstance`  
  
```powershell
Set-SPRSDatabase -Identity 56f8d1bc-cb04-44cf-bd41-a873643c5a14 -QueryTimeout 300  
```  
  
 <span data-ttu-id="bdae2-276">값이 설정되었는지 확인하려면 GET cmdlet을 다시 실행하세요.</span><span class="sxs-lookup"><span data-stu-id="bdae2-276">To verify the value is set, run the GET cmdlet again.</span></span>  
  
```powershell
Get-SPRSDatabase -Identity 56f8d1bc-cb04-44cf-bd41-a873643c5a14 | Select id, querytimeout,connectiontimeout, status, server, ServiceInstance  
```  
  
###  <a name="list-reporting-services-data-extensions---sharepoint-mode"></a><a name="bkmk_example_list_data_extensions"></a><span data-ttu-id="bdae2-277">Reporting services 데이터 확장 프로그램 나열-SharePoint 모드</span><span class="sxs-lookup"><span data-stu-id="bdae2-277">List reporting services data extensions - SharePoint mode</span></span>  
 <span data-ttu-id="bdae2-278">다음 예제는 각 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 서비스 애플리케이션을 반복하고 각각에 대한 현재 데이터 확장을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="bdae2-278">The following example loops through each [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] service application and lists the current data extensions for each.</span></span>  
  
```powershell
$apps = Get-SPRSServiceApplication  
foreach ($app in $apps)
{  
Write-host -ForegroundColor "yellow" Service App Name $app.Name  
Get-SPRSExtension -identity $app -ExtensionType "Data" | select name, extensiontype | Format-Table -AutoSize  
}  
```  
  
 <span data-ttu-id="bdae2-279">**예제 출력:**</span><span class="sxs-lookup"><span data-stu-id="bdae2-279">**Example output:**</span></span>  
  
-   `Name           ExtensionType`  
  
     `----           -------------`  
  
     `SQL                     Data`  
  
     `SQLAZURE                Data`  
  
     `SQLPDW                  Data`  
  
     `OLEDB                   Data`  
  
     `OLEDB-MD                Data`  
  
     `ORACLE                  Data`  
  
     `ODBC                    Data`  
  
     `XML                     Data`  
  
     `SHAREPOINTLIST          Data`  
  
###  <a name="change-and-list-subscription-owners"></a><a name="bkmk_change_subscription_owner"></a><span data-ttu-id="bdae2-280">구독 소유자 변경 및 나열</span><span class="sxs-lookup"><span data-stu-id="bdae2-280">Change and list subscription owners</span></span>  
 <span data-ttu-id="bdae2-281">[Use PowerShell to Change and List Reporting Services Subscription Owners and Run a Subscription](subscriptions/manage-subscription-owners-and-run-subscription-powershell.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="bdae2-281">See [Use PowerShell to Change and List Reporting Services Subscription Owners and Run a Subscription](subscriptions/manage-subscription-owners-and-run-subscription-powershell.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bdae2-282">참고 항목</span><span class="sxs-lookup"><span data-stu-id="bdae2-282">See Also</span></span>  
 <span data-ttu-id="bdae2-283">[PowerShell을 사용 하 여 Reporting Services 구독 소유자 변경 및 나열 및 구독 실행](subscriptions/manage-subscription-owners-and-run-subscription-powershell.md) </span><span class="sxs-lookup"><span data-stu-id="bdae2-283">[Use PowerShell to Change and List Reporting Services Subscription Owners and Run a Subscription](subscriptions/manage-subscription-owners-and-run-subscription-powershell.md) </span></span>  
 <span data-ttu-id="bdae2-284">[검사 목록: PowerShell을 사용 하 여 SharePoint용 PowerPivot 확인](https://docs.microsoft.com/analysis-services/instances/install-windows/checklist-use-powershell-to-verify-power-pivot-for-sharepoint) </span><span class="sxs-lookup"><span data-stu-id="bdae2-284">[CheckList: Use PowerShell to Verify PowerPivot for SharePoint](https://docs.microsoft.com/analysis-services/instances/install-windows/checklist-use-powershell-to-verify-power-pivot-for-sharepoint) </span></span>  
 [<span data-ttu-id="bdae2-285">CodePlex SharePoint 관리 PowerShell 스크립트</span><span class="sxs-lookup"><span data-stu-id="bdae2-285">CodePlex SharePoint Management PowerShell scripts</span></span>](https://sharepointpsscripts.codeplex.com/)   
