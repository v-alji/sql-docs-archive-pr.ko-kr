---
title: '검사 목록: PowerShell을 사용 하 여 SharePoint용 PowerPivot 확인 Microsoft Docs'
ms.custom: ''
ms.date: 07/20/2020
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 73a13f05-3450-411f-95f9-4b6167cc7607
author: minewiskan
ms.author: owend
ms.openlocfilehash: 001b3fae82851b9ec08b0383bb3db9e6d011ae32
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729959"
---
# <a name="checklist-use-powershell-to-verify-powerpivot-for-sharepoint"></a><span data-ttu-id="283a1-102">검사 목록: PowerShell을 사용하여 SharePoint용 PowerPivot 확인</span><span class="sxs-lookup"><span data-stu-id="283a1-102">CheckList: Use PowerShell to Verify PowerPivot for SharePoint</span></span>
  <span data-ttu-id="283a1-103">서비스 및 데이터가 작동하는지 확인하는 견고한 확인 테스트에 성공하지 않으면 [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)] 설치 또는 복구 작업이 완료되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="283a1-103">No [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)] installation or recovery operation is complete without a solid verification test pass that confirms your services and data are operational.</span></span> <span data-ttu-id="283a1-104">이 문서에서는 Windows PowerShell을 사용하여 이러한 단계를 수행하는 방법을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="283a1-104">In this article, we show you how to perform these steps using Windows PowerShell.</span></span> <span data-ttu-id="283a1-105">각 단계를 고유한 섹션에 포함하여 특정 태스크로 바로 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="283a1-105">We put each step into its own section so that you can go straight to specific tasks.</span></span> <span data-ttu-id="283a1-106">예를 들어 유지 관리 또는 백업에 서비스 애플리케이션 및 콘텐츠 데이터베이스를 예약하려면 이 항목의 [데이터베이스](#bkmk_databases) 섹션에서 스크립트를 실행하여 이름을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="283a1-106">For example, run the script in the [Databases](#bkmk_databases) section of this topic to verify the name of the service application and content databases if you want to schedule them for maintenance or backup.</span></span>

|||
|-|-|
|<span data-ttu-id="283a1-107">![PowerShell 관련 콘텐츠](../../../reporting-services/media/rs-powershellicon.jpg "PowerShell 관련 콘텐츠")</span><span class="sxs-lookup"><span data-stu-id="283a1-107">![PowerShell related content](../../../reporting-services/media/rs-powershellicon.jpg "PowerShell related content")</span></span>|<span data-ttu-id="283a1-108">전체 PowerShell 스크립트가 항목 맨 아래에 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="283a1-108">A full PowerShell script is included at the bottom of the topic.</span></span> <span data-ttu-id="283a1-109">전체 스크립트를 시작점으로 사용하여 전체 [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)] 배포를 제작하는 데 사용자 지정 스크립트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="283a1-109">Use the full script as a starting point to build a custom script for auditing your full [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)] deployment.</span></span>|

||
|-|
|<span data-ttu-id="283a1-110">**[!INCLUDE[applies](../../../includes/applies-md.md)]** Sharepoint 2013 &#124; SharePoint 2010</span><span class="sxs-lookup"><span data-stu-id="283a1-110">**[!INCLUDE[applies](../../../includes/applies-md.md)]**  SharePoint 2013 &#124; SharePoint 2010</span></span>|

 <span data-ttu-id="283a1-111">**이 주제에서**: 다음 목차의 문자 항목이 다이어그램 영역에 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="283a1-111">**In this topic**: The lettered items in the following the TOC correspond to areas of the diagram.</span></span> <span data-ttu-id="283a1-112">다이어그램에서는 다음을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="283a1-112">The diagram illustrates the</span></span>

|||
|-|-|
|[<span data-ttu-id="283a1-113">PowerShell 환경 준비</span><span class="sxs-lookup"><span data-stu-id="283a1-113">Prepare your PowerShell environment</span></span>](#bkmk_prerequisites)<br /><br /> [<span data-ttu-id="283a1-114">증상 및 권장 되는 작업</span><span class="sxs-lookup"><span data-stu-id="283a1-114">Symptoms and Recommended Actions</span></span>](#bkmk_symptoms)<br /><br /> <span data-ttu-id="283a1-115">**(A)** [Analysis Services Windows 서비스](#bkmk_windows_service)</span><span class="sxs-lookup"><span data-stu-id="283a1-115">**(A)** [Analysis Services Windows Service](#bkmk_windows_service)</span></span><br /><br /> <span data-ttu-id="283a1-116">**(B)** [get-powerpivotsystemservice and get-powerpivotengineservice](#bkmk_engine_and_system_service)</span><span class="sxs-lookup"><span data-stu-id="283a1-116">**(B)** [PowerPivotSystemService and PowerPivotEngineService](#bkmk_engine_and_system_service)</span></span><br /><br /> <span data-ttu-id="283a1-117">**(C)** [PowerPivot 서비스 애플리케이션 및 프록시](#bkmk_powerpivot_service_application)</span><span class="sxs-lookup"><span data-stu-id="283a1-117">**(C)** [PowerPivot Service Application(s) and proxies](#bkmk_powerpivot_service_application)</span></span><br /><br /> <span data-ttu-id="283a1-118">**(D)** [데이터베이스](#bkmk_databases)</span><span class="sxs-lookup"><span data-stu-id="283a1-118">**(D)** [Databases](#bkmk_databases)</span></span><br /><br /> [<span data-ttu-id="283a1-119">SharePoint 기능</span><span class="sxs-lookup"><span data-stu-id="283a1-119">SharePoint Features</span></span>](#bkmk_features)<br /><br /> [<span data-ttu-id="283a1-120">타이머 작업</span><span class="sxs-lookup"><span data-stu-id="283a1-120">Timer Jobs</span></span>](#bkmk_timer_jobs)<br /><br /> [<span data-ttu-id="283a1-121">상태 규칙</span><span class="sxs-lookup"><span data-stu-id="283a1-121">Health Rules</span></span>](#bkmk_health_rules)<br /><br /> <span data-ttu-id="283a1-122">**(E)** [Windows 및 ULS 로그](#bkmk_logs)</span><span class="sxs-lookup"><span data-stu-id="283a1-122">**(E)** [Windows and ULS Logs](#bkmk_logs)</span></span><br /><br /> [<span data-ttu-id="283a1-123">MSOLAP 공급자</span><span class="sxs-lookup"><span data-stu-id="283a1-123">MSOLAP Provider</span></span>](#bkmk_msolap)<br /><br /> [<span data-ttu-id="283a1-124">ADOMD.Net 클라이언트 라이브러리</span><span class="sxs-lookup"><span data-stu-id="283a1-124">ADOMD.Net client Library</span></span>](#bkmk_adomd)<br /><br /> [<span data-ttu-id="283a1-125">상태 데이터 수집 규칙</span><span class="sxs-lookup"><span data-stu-id="283a1-125">Health Data Collection Rules</span></span>](#bkmk_health_collection)<br /><br /> [<span data-ttu-id="283a1-126">솔루션</span><span class="sxs-lookup"><span data-stu-id="283a1-126">Solutions</span></span>](#bkmk_solutions)<br /><br /> [<span data-ttu-id="283a1-127">수동 확인 단계</span><span class="sxs-lookup"><span data-stu-id="283a1-127">Manual Verification Steps</span></span>](#bkmk_manual)<br /><br /> [<span data-ttu-id="283a1-128">추가 리소스</span><span class="sxs-lookup"><span data-stu-id="283a1-128">More Resources</span></span>](#bkmk_more_resources)<br /><br /> [<span data-ttu-id="283a1-129">전체 PowerShell 스크립트</span><span class="sxs-lookup"><span data-stu-id="283a1-129">Full PowerShell Script</span></span>](#bkmk_full_script)|<span data-ttu-id="283a1-130">![PowerPivot의 PowerShell 확인](../../../sql-server/install/media/ssas-powershell-component-verification.png "PowerPivot의 PowerShell 확인")</span><span class="sxs-lookup"><span data-stu-id="283a1-130">![powershell verification of powerpivot](../../../sql-server/install/media/ssas-powershell-component-verification.png "powershell verification of powerpivot")</span></span>|

##  <a name="prepare-your-powershell-environment"></a><a name="bkmk_prerequisites"></a> <span data-ttu-id="283a1-131">PowerShell 환경 준비</span><span class="sxs-lookup"><span data-stu-id="283a1-131">Prepare your PowerShell environment</span></span>
 <span data-ttu-id="283a1-132">이 섹션의 단계에서는 PowerShell 환경을 준비합니다.</span><span class="sxs-lookup"><span data-stu-id="283a1-132">The steps in this section prepare your PowerShell environment.</span></span> <span data-ttu-id="283a1-133">현재 스크립트 환경에 구성된 방법에 따라 단계를 수행하지 않아도 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="283a1-133">The steps may not be required, depending on how your scripting environment is currently configured.</span></span>

 <span data-ttu-id="283a1-134">**PowerShell 사용 권한**</span><span class="sxs-lookup"><span data-stu-id="283a1-134">**PowerShell Permissions**</span></span>

 <span data-ttu-id="283a1-135">**관리자 권한**으로 Powershell 창 또는 PowerShell ISE(통합 스크립팅 환경)를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="283a1-135">Open a Powershell window or the PowerShell ISE (Integrated Scripting Environment) with **administrative privileges**.</span></span> <span data-ttu-id="283a1-136">명령을 실행할 때 관리자 권한이 없는 경우 다음과 유사한 오류 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="283a1-136">If you do not have administrative privileges when you run commands, you will see an error message similar to the following:</span></span>

 <span data-ttu-id="283a1-137">Get-SPLogEvent: 이 cmdlet을 실행하려면 컴퓨터 **관리자 권한** 이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="283a1-137">Get-SPLogEvent : You need to have Machine **administrator privileges** to run this cmdlet.</span></span>

 <span data-ttu-id="283a1-138">**SharePoint 및 [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)]** 모듈</span><span class="sxs-lookup"><span data-stu-id="283a1-138">**SharePoint and [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)]** Module</span></span>

 <span data-ttu-id="283a1-139">SharePoint 관련 cmdlet을 실행할 때 다음과 유사한 오류 메시지가 표시되는 경우 Add-PSSnapin 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="283a1-139">If you see an error message similar to the following when you run SharePoint related cmdlets, run the Add-PSSnapin command:</span></span>

 <span data-ttu-id="283a1-140">'Get-PowerPivotSystemService' 용어 **는 cmdlet, 함수, 스크립트 파일 또는 실행 프로그램의 이름으로 인식되지 않습니다**.</span><span class="sxs-lookup"><span data-stu-id="283a1-140">The term 'Get-PowerPivotSystemService' **is not recognized as the name of a cmdlet**, function, script file, or operable program.</span></span> <span data-ttu-id="283a1-141">이름의 철자를 확인하거나 경로가 포함되어 있으면 경로가 올바른지 확인하고 다시 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="283a1-141">Check the spelling of the name, or if a path was included, verify that the path is correct and try again.</span></span>

```
Add-PSSnapin Microsoft.Sharepoint.Powershell -EA 0
```

 <span data-ttu-id="283a1-142">**Windows PowerShell**</span><span class="sxs-lookup"><span data-stu-id="283a1-142">**Windows PowerShell**</span></span>

 <span data-ttu-id="283a1-143">PowerShell ISE에 대한 자세한 내용은 [Windows PowerShell ISE 소개](https://technet.microsoft.com/library/dd315244.aspx) 및 [Windows PowerShell을 사용하여 SharePoint 2013 관리](https://technet.microsoft.com/library/ee806878\(v=office.15\).aspx)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="283a1-143">For more information on the PowerShell ISE, see [Introducing the Windows PowerShell ISE](https://technet.microsoft.com/library/dd315244.aspx) and [Use Windows PowerShell to administer SharePoint 2013](https://technet.microsoft.com/library/ee806878\(v=office.15\).aspx).</span></span>

|||
|-|-|
|<span data-ttu-id="283a1-144">![SharePoint 일반 응용 프로그램 집합의 PowerPivot](../../../sql-server/install/media/ssas-powerpivot-logo.png "SharePoint 일반 응용 프로그램 집합의 PowerPivot")</span><span class="sxs-lookup"><span data-stu-id="283a1-144">![powerpivot in sharepoint general application set](../../../sql-server/install/media/ssas-powerpivot-logo.png "powerpivot in sharepoint general application set")</span></span>|<span data-ttu-id="283a1-145">[!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] 관리 대시보드를 사용하여 중앙 관리에서 대부분의 구성 요소를 선택적으로 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="283a1-145">You can optionally verify a majority of the components in Central Administration, using the [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] management dashboard.</span></span> <span data-ttu-id="283a1-146">중앙 관리에서 대시보드를 열려면 **일반 애플리케이션 설정**, **PowerPivot** 의 **관리 대시보드**를 차례로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="283a1-146">To open the dashboard in Central Administration, click **General Application Settings**, and then click **Management Dashboard** in the **PowerPivot**.</span></span> <span data-ttu-id="283a1-147">대시보드에 대한 자세한 내용은 [PowerPivot Management Dashboard and Usage Data](../../power-pivot-sharepoint/power-pivot-management-dashboard-and-usage-data.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="283a1-147">For more information on the dashboard, see [PowerPivot Management Dashboard and Usage Data](../../power-pivot-sharepoint/power-pivot-management-dashboard-and-usage-data.md).</span></span>|

##  <a name="symptoms-and-recommended-actions"></a><a name="bkmk_symptoms"></a><span data-ttu-id="283a1-148">증상 및 권장 되는 작업</span><span class="sxs-lookup"><span data-stu-id="283a1-148">Symptoms and Recommended Actions</span></span>
 <span data-ttu-id="283a1-149">다음 표는 증상 또는 문제 및 문제를 해결하는 데 도움이 되는 이 항목의 제안되는 섹션 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="283a1-149">The following table is a list of symptoms or issues and the suggested section of this topic to consult to help you resolve the issue.</span></span>

|<span data-ttu-id="283a1-150">증상</span><span class="sxs-lookup"><span data-stu-id="283a1-150">Symptom</span></span>|<span data-ttu-id="283a1-151">섹션 참조</span><span class="sxs-lookup"><span data-stu-id="283a1-151">See section</span></span>|
|-------------|-----------------|
|<span data-ttu-id="283a1-152">데이터 새로 고침이 실행되지 않음</span><span class="sxs-lookup"><span data-stu-id="283a1-152">Data refresh is not running</span></span>|<span data-ttu-id="283a1-153">[Timer Jobs](#bkmk_timer_jobs) 섹션을 참조하여 **PowerPivot 데이터 새로 고침 타이머 작업** 이 온라인인지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="283a1-153">See the section [Timer Jobs](#bkmk_timer_jobs) and verify the **Online PowerPivot Data Refresh Timer Job** is online.</span></span>|
|<span data-ttu-id="283a1-154">관리 대시보드 데이터가 오래됨</span><span class="sxs-lookup"><span data-stu-id="283a1-154">Management dashboard data is old</span></span>|<span data-ttu-id="283a1-155">[타이머 작업](#bkmk_timer_jobs) 섹션을 참고하여 **관리 대시보드 처리 타이머 작업** 이 온라인인지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="283a1-155">See the section [Timer Jobs](#bkmk_timer_jobs) and verify the **Management Dashboard Processing Timer Job** is online.</span></span>|
|<span data-ttu-id="283a1-156">관리 대시보드의 일부</span><span class="sxs-lookup"><span data-stu-id="283a1-156">Some portions of the Management Dashboard</span></span>|<span data-ttu-id="283a1-157">Excel Services 또는 SharePoint용 PowerPivot이 없는 중앙 관리의 토폴로지가 포함된 팜에 SharePoint용 PowerPivot을 설치하는 경우, PowerPivot 관리 대시보드의 모든 기본 제공 보고서에 액세스하려면 Microsoft ADOMD.NET 클라이언트 라이브러리를 다운로드하여 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="283a1-157">If you install PowerPivot for SharePoint into a farm that has the topology of Central Administration, without Excel Services or PowerPivot for SharePoint, you must download and install the Microsoft ADOMD.NET client library if you want full access to the built-in reports in the PowerPivot management dashboard.</span></span> <span data-ttu-id="283a1-158">대시보드의 일부 보고서는 ADOMD.NET을 사용하여 팜의 PowerPivot 쿼리 처리 및 서버 상태에 대한 보고 데이터를 제공하는 내부 데이터에 액세스합니다.</span><span class="sxs-lookup"><span data-stu-id="283a1-158">Some reports in the dashboard use ADOMD.NET to access internal data that provides reporting data on PowerPivot query processing and server health in the farm.</span></span> <span data-ttu-id="283a1-159">[ADOMD.Net 클라이언트 라이브러리](#bkmk_adomd) 섹션 및 [중앙 관리를 실행하는 웹 프런트 엔드 서버에 ADOMD.NET 설치](../../../sql-server/install/install-adomd-net-on-web-front-end-servers-running-central-administration.md)항목을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="283a1-159">See the section [ADOMD.Net client Library](#bkmk_adomd) and the topic [Install ADOMD.NET on Web Front-End Servers Running Central Administration](../../../sql-server/install/install-adomd-net-on-web-front-end-servers-running-central-administration.md).</span></span>|
|\<future content>||

##  <a name="analysis-services-windows-service"></a><a name="bkmk_windows_service"></a> <span data-ttu-id="283a1-160">Analysis Services Windows 서비스</span><span class="sxs-lookup"><span data-stu-id="283a1-160">Analysis Services Windows Service</span></span>
 <span data-ttu-id="283a1-161">이 섹션의 스크립트는 SharePoint 모드에서 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 인스턴스를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="283a1-161">The script in this section verifies the instance of [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] in SharePoint mode.</span></span> <span data-ttu-id="283a1-162">서비스가 **실행 중**인지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="283a1-162">Verify the service is **running**.</span></span>

```powershell
Get-Service | Select name, displayname, status | Where {$_.Name -eq "msolap`$powerpivot"} | Format-Table -Property * -AutoSize | Out-Default
```

```Output
Name              DisplayName                                Status
----              -----------                                ------
MSOLAP$POWERPIVOT SQL Server Analysis Services (POWERPIVOT) Running
```

##  <a name="powerpivotsystemservice-and-powerpivotengineservice"></a><a name="bkmk_engine_and_system_service"></a><span data-ttu-id="283a1-163">Get-powerpivotsystemservice 및 Get-powerpivotengineservice</span><span class="sxs-lookup"><span data-stu-id="283a1-163">PowerPivotSystemService and PowerPivotEngineService</span></span>
 <span data-ttu-id="283a1-164">이 섹션의 스크립트는 [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)] 시스템 서비스 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="283a1-164">The scripts in this section verify the [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)] system services.</span></span> <span data-ttu-id="283a1-165">SharePoint 2013 배포를 위한 시스템 서비스 하나와 SharePoint 2010 배포를 위한 서비스 2개가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="283a1-165">There is one system service for a SharePoint 2013 deployment and two services for a SharePoint 2010 deployment.</span></span>

 <span data-ttu-id="283a1-166">**PowerPivotSystemService**</span><span class="sxs-lookup"><span data-stu-id="283a1-166">**PowerPivotSystemService**</span></span>

 <span data-ttu-id="283a1-167">상태가 **온라인**인지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="283a1-167">Verify the Status is **Online**.</span></span>

```powershell
Get-PowerPivotSystemService | Select typename, status, applications, farm | Format-Table -Property * -AutoSize | Out-Default
```

```Output
TypeName                                  Status Applications                             Farm
--------                                  ------ ------------                             ----
SQL Server PowerPivot Service Application Online {Default PowerPivot Service Application} SPFarm Name=SharePoint_Config_77d8ab0744a34e8aa27c806a2b8c760c
```

 <span data-ttu-id="283a1-168">**Get-powerpivotengineservice**</span><span class="sxs-lookup"><span data-stu-id="283a1-168">**PowerPivotEngineService**</span></span>

> [!NOTE]
>  <span data-ttu-id="283a1-169">SharePoint 2013을 사용 중인 경우**이 스크립트를 건너뜁니다** .</span><span class="sxs-lookup"><span data-stu-id="283a1-169">**Skip this script if** you are using SharePoint 2013.</span></span> <span data-ttu-id="283a1-170">PowerPivotEngineService는 SharePoint 2013 배포의 일부입니다.</span><span class="sxs-lookup"><span data-stu-id="283a1-170">The PowerPivotEngineService is not part of a SharePoint 2013 deployment.</span></span> <span data-ttu-id="283a1-171">SharePoint 2013에서 Get-PowerPivot**엔진**서비스 cmdlet을 실행 하면 다음과 유사한 오류 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="283a1-171">If you run the Get-PowerPivot**Engine**Service cmdlet on SharePoint 2013, you will see an error message similar to the following.</span></span> <span data-ttu-id="283a1-172">이 항목의 사전 요구 사항 섹션에 명시된 Add-PSSnapin 명령을 실행한 경우에도 이 오류 메시지가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="283a1-172">This error message is returned even if you have run the Add-PSSnapin command described in the prerequisites section of this topic.</span></span>
> 
>  <span data-ttu-id="283a1-173">'Get-PowerPivotEngineService' 용어는 cmdlet 이름으로 인식되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="283a1-173">The term 'Get-PowerPivotEngineService' is not recognized as the name of a cmdlet</span></span>

 <span data-ttu-id="283a1-174">SharePoint 2010 배포에서 상태가 **온라인**인지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="283a1-174">In a SharePoint 2010 deployment, verify the status is **Online**.</span></span>

```powershell
Get-PowerPivotEngineService | Select typename, status, name, instances, farm | Format-Table -Property * -AutoSize | Out-Default
```

```Output
TypeName  : SQL Server Analysis Services
Status    : Online
Name      : MSOLAP$POWERPIVOT
Instances : {POWERPIVOT}
Farm      : SPFarm Name=SharePoint_Config
```

##  <a name="powerpivot-service-applications-and-proxies"></a><a name="bkmk_powerpivot_service_application"></a><span data-ttu-id="283a1-175">PowerPivot 서비스 응용 프로그램 및 프록시</span><span class="sxs-lookup"><span data-stu-id="283a1-175">PowerPivot Service Application(s) and proxies</span></span>
 <span data-ttu-id="283a1-176">상태가 **온라인**인지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="283a1-176">Verify the status is **Online**.</span></span> <span data-ttu-id="283a1-177">Excel Services 애플리케이션에서는 서비스 애플리케이션 데이터베이스를 사용하지 않으므로 cmdlet이 데이터베이스 이름을 반환하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="283a1-177">The Excel Services Application does not use a service application database and therefore the cmdlet does not return a database name.</span></span> <span data-ttu-id="283a1-178">이 항목의 이후 데이터베이스 섹션에서 데이터베이스가 온라인인지 확인할 수 있도록 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] 서비스 애플리케이션에서 데이터베이스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="283a1-178">Note the database used by the [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] service application so you can verify the database is online in the database section later in this topic.</span></span>

 <span data-ttu-id="283a1-179">**PowerPivot 및 Excel Service 애플리케이션**</span><span class="sxs-lookup"><span data-stu-id="283a1-179">**PowerPivot and Excel Service Application(s)**</span></span>

 <span data-ttu-id="283a1-180">SharePoint 2010 배포의 경우 상태가 **온라인**인지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="283a1-180">For a SharePoint 2010 deployment, verify the status is **Online**.</span></span>

```powershell
Get-PowerPivotServiceApplication | Select typename,name, status, unattendedaccount, applicationpool, farm, database
Get-SPExcelServiceApplication | Select typename, DisplayName, status
```

```Output
TypeName          : PowerPivot Service Application
Name              : PowerPivotServiceApplication1
Status            : Online
UnattendedAccount : PowerPivotUnattendedAccount
ApplicationPool   : SPIisWebServiceApplicationPool Name=sqlbi_serviceapp
Farm              : SPFarm Name=SharePoint_Config
Database          : GeminiServiceDatabase Name=PowerPivotServiceApplication1_19648f3f2c944e27acdc6c20aab8487a

TypeName    : Excel Services Application Web Service Application
DisplayName : Excel Services Application
Status      : Online
```

 <span data-ttu-id="283a1-181">**서비스 응용 프로그램 풀**</span><span class="sxs-lookup"><span data-stu-id="283a1-181">**Service Application Pool**</span></span>

> [!NOTE]
>  <span data-ttu-id="283a1-182">다음 코드 샘플은 먼저 기본 [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)] 서비스 애플리케이션의 applicationpool 속성을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="283a1-182">The following code sample first returns the applicationpool property of the default [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)] service application.</span></span> <span data-ttu-id="283a1-183">이름은 문자열에서 구문 처리되고 애플리케이션 풀 개체 상태를 가져오는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="283a1-183">The name is parsed from the string and used to get the status of the application pool object.</span></span>
> 
>  <span data-ttu-id="283a1-184">상태가 **온라인**인지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="283a1-184">Verify the Status is **Online**.</span></span> <span data-ttu-id="283a1-185">사이트를 검색할 때 상태가 온라인이 아니거나 "http 오류"가 표시 되는 경우 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] IIS 응용 프로그램 풀의 id 자격 증명이 올바른지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="283a1-185">If the status is not Online or you see "http error" when you browse the [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] site, verify the identity credentials in the IIS application pools are still correct.</span></span> <span data-ttu-id="283a1-186">IIS 풀 이름은 Get-SPServiceApplicationPool 명령에서 반환되는 ID 속성 값입니다.</span><span class="sxs-lookup"><span data-stu-id="283a1-186">The IIS pool name will is the value of the ID property returned by the Get-SPServiceApplicationPool command.</span></span>

```powershell
$poolname = [string](Get-PowerPivotServiceApplication | Select -Property applicationpool)
$position = $poolname.lastindexof("=")
$poolname = $poolname.substring($position+1)
$poolname = $poolname.substring(0,$poolname.length-1)

Get-SPServiceApplicationPool | Select name, status, processaccountname, id | Where {$_.Name -eq $poolname} | Format-Table -Property * -AutoSize | Out-Default
```

```Output
Name                           Status ProcessAccountName Id
----                           ------ ------------------ ------- 
SharePoint Web Services System Online DOMAIN\account     89b50ec3-49e3-4de7-881a-2cec4b8b73ea
```

 ![참고](../../../reporting-services/media/rs-fyinote.png "참고") 응용 프로그램 풀은 중앙 관리 페이지 **서비스 응용 프로그램 관리**에서도 확인할 수 있습니다. <span data-ttu-id="283a1-188">서비스 애플리케이션의 이름을 클릭한 다음 리본에서 **속성** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="283a1-188">Click the name of the service application and then click **properties** in the ribbon.</span></span>

 <span data-ttu-id="283a1-189">**PowerPivot 및 Excel Service 애플리케이션 프록시**</span><span class="sxs-lookup"><span data-stu-id="283a1-189">**PowerPivot and Excel Service Application proxies**</span></span>

 <span data-ttu-id="283a1-190">상태가 **온라인**인지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="283a1-190">Verify the Status is **Online**.</span></span>

```powershell
Get-SPServiceApplicationProxy | Select typename, status, unattendedaccount, displayname | Where {$_.TypeName -Like "*powerpivot*" -Or $_.TypeName -Like "*excel services*"} | Format-Table -Property * -AutoSize | Out-Default
```

```Output
TypeName                                                 Status UnattendedAccount           DisplayName
--------                                                 ------ -----------------           -----------
PowerPivot Service Application Proxy                     Online PowerPivotUnattendedAccount PowerPivotServiceApplication1
Excel Services Application Web Service Application Proxy Online                             Excel Services Application
```

##  <a name="databases"></a><a name="bkmk_databases"></a> <span data-ttu-id="283a1-191">데이터베이스</span><span class="sxs-lookup"><span data-stu-id="283a1-191">Databases</span></span>
 <span data-ttu-id="283a1-192">다음 스크립트는 서비스 애플리케이션 데이터베이스 및 모든 콘텐츠 데이터베이스의 상태를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="283a1-192">The following script returns the status of the service application databases and all content databases.</span></span> <span data-ttu-id="283a1-193">상태가 **온라인**인지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="283a1-193">Verify the status is **Online**.</span></span>

```powershell
Get-SPDatabase | Select name, status, server, typename | Where {$_.TypeName -eq "content database" -Or $_.TypeName -Like "*Gemini*"} | Format-Table -Property * -AutoSize | Out-Default
```

```Output
Name                                                                       Status Server                  TypeName 
----                                                                       ------ ------                  -------- 
DefaultPowerPivotServiceApplicationDB-38422181-2b68-4ab2-b2bb-9c00c39e5a5e Online SPServer Name=TESTSERVER Microsoft.AnalysisServices.SPAddin.GeminiServiceDatabase
DefaultWebApplicationDB-f0db1a8e-4c22-408c-b9b9-153bd74b0312               Online TESTSERVER\POWERPIVOT    Content Database 
SharePoint_Admin_3cadf0b098bf49e0bb15abd487f5c684                          Online TESTSERVER\POWERPIVOT    Content Database
```

##  <a name="sharepoint-features"></a><a name="bkmk_features"></a><span data-ttu-id="283a1-194">SharePoint 기능</span><span class="sxs-lookup"><span data-stu-id="283a1-194">SharePoint Features</span></span>
 <span data-ttu-id="283a1-195">사이트, 웹 및 팜 기능이 온라인인지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="283a1-195">Verify the site, web, and farm features are online.</span></span>

```powershell
Get-SPFeature | Select displayname, status, scope, farm | Where {$_.displayName -Like "*powerpivot*"} | Format-Table -Property * -AutoSize | Out-Default
```

```Output
DisplayName     Status Scope Farm                         
-----------     ------ ----- ----                         
PowerPivotSite  Online  Site SPFarm Name=SharePoint_Config
PowerPivotAdmin Online   Web SPFarm Name=SharePoint_Config
PowerPivot      Online  Farm SPFarm Name=SharePoint_Config
```

##  <a name="timer-jobs"></a><a name="bkmk_timer_jobs"></a> <span data-ttu-id="283a1-196">타이머 작업</span><span class="sxs-lookup"><span data-stu-id="283a1-196">Timer Jobs</span></span>
 <span data-ttu-id="283a1-197">타이머 작업이 **온라인**인지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="283a1-197">Verify the Time Jobs are **Online**.</span></span> <span data-ttu-id="283a1-198">[!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] EngineService가 SharePoint 2013에 설치되어 있지 않으므로 스크립트가 SharePoint 2013 배포에서 EngineService 타이머 작업을 목록에 나타내지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="283a1-198">The [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] EngineService is not installed on SharePoint 2013, therefore the script will not list EngineService timer jobs in a SharePoint 2013 deployment.</span></span>

```powershell
Get-SPTimerJob | Where {$_.service -Like "*power*" -Or $_.service -Like "*mid*"} | Select status, displayname, LastRunTime, service | Format-Table -Property * -AutoSize | Out-Default
```

```Output
      Status DisplayName                                                                          LastRunTime          Service                             
------ -----------                                                                          -----------          -------                             
Online Health Analysis Job (Daily, SQL Server Analysis Services, All Servers)               4/9/2014 12:00:01 AM EngineService Name=MSOLAP$POWERPIVOT
Online Health Analysis Job (Hourly, SQL Server Analysis Services, All Servers)              4/9/2014 1:00:01 PM  EngineService Name=MSOLAP$POWERPIVOT
Online Health Analysis Job (Weekly, SQL Server Analysis Services, All Servers)              4/6/2014 12:00:10 AM EngineService Name=MSOLAP$POWERPIVOT
Online PowerPivot Management Dashboard Processing Timer Job                                 4/8/2014 3:45:38 AM  MidTierService
Online PowerPivot Health Statistics Collector Timer Job                                     4/9/2014 1:00:12 PM  MidTierService
Online PowerPivot Data Refresh Timer Job                                                    4/9/2014 1:09:36 PM  MidTierService
Online Health Analysis Job (Daily, SQL Server PowerPivot Service Application, All Servers)  4/9/2014 12:00:00 AM MidTierService
Online Health Analysis Job (Daily, SQL Server PowerPivot Service Application, Any Server)   4/9/2014 12:00:00 AM MidTierService
Online Health Analysis Job (Weekly, SQL Server PowerPivot Service Application, All Servers) 4/6/2014 12:00:03 AM MidTierService
Online Health Analysis Job (Weekly, SQL Server PowerPivot Service Application, Any Server)  4/6/2014 12:00:03 AM MidTierService
Online PowerPivot Setup Extension Timer Job                                                 4/1/2014 1:40:31 AM  MidTierService
```

##  <a name="health-rules"></a><a name="bkmk_health_rules"></a> <span data-ttu-id="283a1-199">상태 규칙</span><span class="sxs-lookup"><span data-stu-id="283a1-199">Health Rules</span></span>
 <span data-ttu-id="283a1-200">SharePoint 2013 배포에는 규칙이 훨씬 적습니다.</span><span class="sxs-lookup"><span data-stu-id="283a1-200">There are fewer rules in a SharePoint 2013 deployment.</span></span> <span data-ttu-id="283a1-201">각 SharePoint 환경에 대 한 규칙의 전체 목록과 규칙 사용 방법에 대 한 설명은 [PowerPivot 상태 규칙-구성](../../power-pivot-sharepoint/configure-power-pivot-health-rules.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="283a1-201">For a full list of rules for each SharePoint environment and an explanation of how to use the rules, see [PowerPivot Health Rules - Configure](../../power-pivot-sharepoint/configure-power-pivot-health-rules.md).</span></span>

```powershell
Get-SPHealthAnalysisRule | Select name, enabled, summary | Where {$_.summary -Like "*power*"}  | Format-Table -Property * -AutoSize | Out-Default
```

```Output
Name                          Enabled Summary
----                          ------- -------         
SecondaryLogonHealthRule         True PowerPivot:  Secondary Logon service (seclogon) is disabled
DataRefreshTimerJobHealthRule    True PowerPivot: The PowerPivot Data Refresh timer job is disabled.
ASUsageLoadHealthRule            True PowerPivot: The ratio of load events to connections is too high.
ASMiniDumpHealthRule             True PowerPivot: One or more minidump files were found in the Logs directory, indicating a program crash
ASUsageCubeRule                  True PowerPivot: Usage data is not getting updated at the expected frequency.
ASADOMDNETHealthRule             True PowerPivot: ADOMD.NET is not installed on a standalone WFE that is configured for central admin
MidTierAcctReadPermissionRule    True PowerPivot: MidTier process account should have 'Full Read' permission on all associated SPWebApplications.
```

##  <a name="windows-and-uls-logs"></a><a name="bkmk_logs"></a> <span data-ttu-id="283a1-202">Windows 및 ULS 로그</span><span class="sxs-lookup"><span data-stu-id="283a1-202">Windows and ULS Logs</span></span>
 <span data-ttu-id="283a1-203">**Windows 이벤트 로그**</span><span class="sxs-lookup"><span data-stu-id="283a1-203">**Windows event log**</span></span>

 <span data-ttu-id="283a1-204">다음 명령은 SharePoint 모드의 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 인스턴스 관련 이벤트의 Windows 이벤트 로그를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="283a1-204">The following command will search the windows event log for events related to the instance of [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] in SharePoint mode.</span></span> <span data-ttu-id="283a1-205">이벤트를 사용 하지 않도록 설정 하거나 이벤트 수준을 변경 하는 방법에 대 한 자세한 내용은 [SharePoint 로그 파일과 진단 로깅 &#40;구성 및 보기 SharePoint용 PowerPivot&#41;](../../power-pivot-sharepoint/configure-and-view-sharepoint-and-diagnostic-logging.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="283a1-205">For information on disabling events or changing the event level, see [Configure and View SharePoint Log Files  and Diagnostic Logging &#40;PowerPivot for SharePoint&#41;](../../power-pivot-sharepoint/configure-and-view-sharepoint-and-diagnostic-logging.md).</span></span>

 <span data-ttu-id="283a1-206">**서비스 이름:** MSOLAP$POWERPIVOT</span><span class="sxs-lookup"><span data-stu-id="283a1-206">**Service Name:** MSOLAP$POWERPIVOT</span></span>

 <span data-ttu-id="283a1-207">**Windows 서비스의 표시 이름:** SQL Server Analysis Services(POWERPIVOT)</span><span class="sxs-lookup"><span data-stu-id="283a1-207">**Display name in Windows Services:** SQL Server Analysis Services (POWERPIVOT)</span></span>

```powershell
Get-EventLog "application" | Where-Object {$_.source -Like "msolap`$powerpivot*"}  | Select timegenerated, entrytype , source, message | Format-Table -property * -AutoSize | Out-Default
```

```Output
TimeGenerated           EntryType Source            Message
-------------           --------- ------            -------
4/16/2014 1:45:19 PM  Information MSOLAP$POWERPIVOT Software usage metrics are disabled.
4/16/2014 1:45:19 PM  Information MSOLAP$POWERPIVOT Service started. Microsoft SQL Server Analysis Services 64 Bit Evaluation (x64) RTM 12.0.1997.5.
4/16/2014 1:45:18 PM  Information MSOLAP$POWERPIVOT The flight recorder was started.
4/14/2014 6:45:37 PM  Information MSOLAP$POWERPIVOT Software usage metrics are disabled.
```

 <span data-ttu-id="283a1-208">**SharePoint ULS 로그, 지난 48시간**</span><span class="sxs-lookup"><span data-stu-id="283a1-208">**SharePoint ULS Log, last 48 hours**</span></span>

 <span data-ttu-id="283a1-209">다음 명령은 지난 48시간 동안 생성된 ULS 로그에서 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] 메시지를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="283a1-209">The following command will return [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] messages from the ULS log that were created in the last 48 hours.</span></span> <span data-ttu-id="283a1-210">필요에 따라 addhours 매개 변수를 조정합니다.</span><span class="sxs-lookup"><span data-stu-id="283a1-210">Adjust the addhours parameter for your need.</span></span>

```powershell
Get-SPLogEvent -StartTime(Get-Date).AddHours(-48) | Where-Object {$_.Area -eq "powerpivot service" -and $_.level -eq "high"} | Select timestamp, area, category, eventid,level, message | Format-Table -Property * -AutoSize | Out-Default
```

 <span data-ttu-id="283a1-211">다음 명령 변형은 **데이터 새로 고침** 범주에 대한 로그 이벤트만 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="283a1-211">The following variation of the command only returns log events for the **data refresh** category.</span></span>

```powershell
Get-SPLogEvent -starttime(Get-Date).addhours(-48) | Where-Object {$_.category -eq "data refresh" -and $_.level -eq "high"} | Select timestamp, area, category, eventid, level, correlation, message
```

```Output
Timestamp   : 4/14/2014 7:15:01 PM
Area        : PowerPivot Service
Category    : Data Refresh
EventID     : 43
Level       : High
Correlation : 5755879c-7cab-e097-8f80-f27895d44a77
Message     : The following error occurred when working with the service application, Default PowerPivot Service Application. Skipping the service application..

Timestamp   : 4/14/2014 7:15:02 PM
Area        : PowerPivot Service
Category    : Data Refresh
EventID     : 99
Level       : High
Correlation : 5755879c-7cab-e097-8f80-f27895d44a77
Message     : EXCEPTION: System.TimeoutException: The request channel timed out while waiting for a reply after 00:00:47.0625313. Increase the timeout value passed to 
              the call to Request or increase the SendTimeout value on the Binding. The time allotted to this operation may have been a portion of a longer timeout. 
              ---> System.TimeoutException: The HTTP request to 'http://localhost:32843/SecurityTokenServiceApplication/securitytoken.svc/actas' has exceeded the 
              allotted timeout of 00:00:54.5930000. The time allotted to this operation may have been a portion of a longer timeout. ---> System.Net.WebException: The 
              operation has timed out     at System.Net.HttpWebRequest.GetResponse()     at 
              System.ServiceModel.Channels.HttpChannelFactory`1.HttpRequestChannel.HttpChannelRequest.WaitForReply(TimeSpan timeout...
```

##  <a name="msolap-provider"></a><a name="bkmk_msolap"></a> <span data-ttu-id="283a1-212">MSOLAP 공급자</span><span class="sxs-lookup"><span data-stu-id="283a1-212">MSOLAP Provider</span></span>
 <span data-ttu-id="283a1-213">MSOLAP 공급자를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="283a1-213">Verify the provider MSOLAP provider.</span></span> [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]<span data-ttu-id="283a1-214">및는 [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)] [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] MSOLAP. 5를 요구 합니다.</span><span class="sxs-lookup"><span data-stu-id="283a1-214">and [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)] [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] require MSOLAP.5.</span></span>

```powershell
$excelApp = Get-SPExcelServiceApplication
Get-SPExcelDataProvider -ExcelServiceApplication $excelApp | Select providerid, providertype, description | Where {$_.providerid -like "msolap*" } | Format-Table -Property * -AutoSize | Out-Default
```

```Output
ProviderId ProviderType Description
---------- ------------ -----------
MSOLAP     Oledb        Microsoft OLE DB Provider for OLAP Services     
MSOLAP.3   Oledb        Microsoft OLE DB Provider for OLAP Services 9.0 
MSOLAP.4   Oledb        Microsoft OLE DB Provider for OLAP Services 10.0
MSOLAP.5   Oledb        Microsoft OLE DB Provider for OLAP Services 11.0
```

 <span data-ttu-id="283a1-215">자세한 내용은 [SharePoint 서버에서 Analysis Services OLE DB 공급자 설치](../../../sql-server/install/install-the-analysis-services-ole-db-provider-on-sharepoint-servers.md) 및 [MSOLAP.5를 Excel Services에서 신뢰할 수 있는 데이터 공급자로 추가](https://technet.microsoft.com/library/hh758436.aspx)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="283a1-215">For more information, see [Install the Analysis Services OLE DB Provider on SharePoint Servers](../../../sql-server/install/install-the-analysis-services-ole-db-provider-on-sharepoint-servers.md) and [Add MSOLAP.5 as a Trusted Data Provider in Excel Services](https://technet.microsoft.com/library/hh758436.aspx).</span></span>

##  <a name="adomdnet-client-library"></a><a name="bkmk_adomd"></a><span data-ttu-id="283a1-216">ADOMD.Net 클라이언트 라이브러리</span><span class="sxs-lookup"><span data-stu-id="283a1-216">ADOMD.Net client Library</span></span>

```powershell
Get-WMIObject -Class win32_product | Where-Object {$_.name -Like "*ado*"} | Select name, version, vendor | Format-Table -Property * -AutoSize | out-default
```

```Output
name                                                  version      vendor
----                                                  -------      ------
Microsoft SQL Server 2008 Analysis Services ADOMD.NET 10.1.2531.0  Microsoft Corporation
Microsoft SQL Server 2005 Analysis Services ADOMD.NET 9.00.1399.06 Microsoft Corporation
```

 <span data-ttu-id="283a1-217">자세한 내용은 [중앙 관리를 실행하는 웹 프런트 엔드 서버에 ADOMD.NET 설치](../../../sql-server/install/install-adomd-net-on-web-front-end-servers-running-central-administration.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="283a1-217">For more information, see [Install ADOMD.NET on Web Front-End Servers Running Central Administration](../../../sql-server/install/install-adomd-net-on-web-front-end-servers-running-central-administration.md).</span></span>

##  <a name="health-data-collection-rules"></a><a name="bkmk_health_collection"></a> <span data-ttu-id="283a1-218">상태 데이터 수집 규칙</span><span class="sxs-lookup"><span data-stu-id="283a1-218">Health Data Collection Rules</span></span>
 <span data-ttu-id="283a1-219">**상태** 가 온라인이고 **설정** 이 True인지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="283a1-219">Verify the **Status** is Online and **Enabled** is True.</span></span>

```powershell
Get-SPUsageDefinition | Select name, status, enabled, tablename, DaysToKeepDetailedData | Where {$_.name -Like "powerpivot*"} | Format-Table -Property * -AutoSize | Out-Default
```

```Output
Name                         Status Enabled TableName                   DaysToKeepDetailedData
----                         ------ ------- ---------                   ----------------------
PowerPivot Connections       OnlineTrue AnalysisServicesConnections  14
PowerPivot Load Data Usage   Online    True AnalysisServicesLoads                           14
PowerPivot Query Usage       Online    True AnalysisServicesRequests                        14
PowerPivot Unload Data Usage Online    True AnalysisServicesUnloads                         14
```

 <span data-ttu-id="283a1-220">자세한 내용은 [PowerPivot Usage Data Collection](../../power-pivot-sharepoint/power-pivot-usage-data-collection.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="283a1-220">For more information, see [PowerPivot Usage Data Collection](../../power-pivot-sharepoint/power-pivot-usage-data-collection.md).</span></span>

##  <a name="solutions"></a><a name="bkmk_solutions"></a><span data-ttu-id="283a1-221">해결책이</span><span class="sxs-lookup"><span data-stu-id="283a1-221">Solutions</span></span>
 <span data-ttu-id="283a1-222">다른 구성 요소가 온라인인 경우 솔루션을 확인하는 단계를 건너뛸 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="283a1-222">If the other components are online then you can skip verifying the solutions.</span></span> <span data-ttu-id="283a1-223">그러나 상태 규칙이 없는 경우 표시되는 두 해결 방법을 확인하고 PowerPivot 솔루션이 **온라인** 이고 **배포됨**인지 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="283a1-223">If however the Health rules are missing, verify the two solutions exist and showed Verify the two PowerPivot solutions are **Online** and **Deployed**.</span></span>

```powershell
Get-SPSolution | Select name, status, deployed, DeploymentState, DeployedServers | Where {$_.Name -Like "*powerpivot*"} | Format-Table -Property * -AutoSize | Out-Default
```

<span data-ttu-id="283a1-224">SharePoint 2013:</span><span class="sxs-lookup"><span data-stu-id="283a1-224">SharePoint 2013:</span></span>

```Output
Name                                 Status Deployed        DeploymentState DeployedServers
----                                 ------ --------        --------------- ---------------
powerpivotfarm14solution.wsp         Online     True         GlobalDeployed {UETESTA00}
powerpivotfarmsolution.wsp           Online     True         GlobalDeployed {UETESTA00}
powerpivotwebapplicationsolution.wsp Online     True WebApplicationDeployed {UETESTA00}
```

<span data-ttu-id="283a1-225">SharePoint  2010:</span><span class="sxs-lookup"><span data-stu-id="283a1-225">SharePoint 2010:</span></span>

```Output
Name                 Status Deployed        DeploymentState DeployedServers 
----                 ------ --------        --------------- --------------- 
powerpivotfarm.wsp   Online     True         GlobalDeployed {uesql11spoint2}
powerpivotwebapp.wsp Online     True WebApplicationDeployed {uesql11spoint2}
```

 <span data-ttu-id="283a1-226">SharePoint 솔루션 배포 방법은 [솔루션 패키지 배포(SharePoint Server 2010)](https://technet.microsoft.com/library/cc262995\(v=office.14\).aspx)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="283a1-226">For more information on how to deploy SharePoint solutions, see [Deploy solution packages (SharePoint Server 2010)](https://technet.microsoft.com/library/cc262995\(v=office.14\).aspx).</span></span>

##  <a name="manual-verification-steps"></a><a name="bkmk_manual"></a><span data-ttu-id="283a1-227">수동 확인 단계</span><span class="sxs-lookup"><span data-stu-id="283a1-227">Manual Verification Steps</span></span>
 <span data-ttu-id="283a1-228">이 섹션에서는 PowerShell cmdlet으로 완료할 수 없는 확인 단계에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="283a1-228">This section describes verification steps that cannot be completed with PowerShell cmdlets.</span></span>

 <span data-ttu-id="283a1-229">**예약된 데이터 새로 고침:** 통합 문서에 대한 새로 고침 일정을 **가능한 한 빨리 새로 고침**으로 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="283a1-229">**Scheduled Data Refresh:** Configure the refresh schedule a workbook to **Also refresh as soon as possible**.</span></span>  <span data-ttu-id="283a1-230">자세한 내용은 [데이터 새로 고침 예약 및 Windows 인증을 지원 하지 않는 데이터 원본 &#40;SharePoint용 PowerPivot&#41;](../../power-pivot-sharepoint/schedule-data-refresh-and-data-sources-no-windows-authentication.md)의 "데이터 새로 고침 확인" 섹션을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="283a1-230">For more information, see the "Verify Data Refresh" section of [Schedule Data Refresh and Data Sources That Do Not Support Windows Authentication &#40;PowerPivot for SharePoint&#41;](../../power-pivot-sharepoint/schedule-data-refresh-and-data-sources-no-windows-authentication.md).</span></span>

##  <a name="more-resources"></a><a name="bkmk_more_resources"></a><span data-ttu-id="283a1-231">추가 리소스</span><span class="sxs-lookup"><span data-stu-id="283a1-231">More Resources</span></span>
 <span data-ttu-id="283a1-232">[Windows PowerShell의 웹 서버(IIS) 관리 Cmdlet](https://technet.microsoft.com/library/ee790599.aspx).</span><span class="sxs-lookup"><span data-stu-id="283a1-232">[Web Server (IIS) Administration Cmdlets in Windows PowerShell](https://technet.microsoft.com/library/ee790599.aspx).</span></span>

 <span data-ttu-id="283a1-233">[SharePoint에서 서비스, IIS 사이트 및 애플리케이션 풀 상태를 확인하기 위한 PowerShell](https://gallery.technet.microsoft.com/office/PowerShell-to-check-a6ed72a0).</span><span class="sxs-lookup"><span data-stu-id="283a1-233">[PowerShell to check services, IIS sites and Application Pool status in SharePoint](https://gallery.technet.microsoft.com/office/PowerShell-to-check-a6ed72a0).</span></span>

 <span data-ttu-id="283a1-234">[SharePoint 2013용 Windows PowerShell 참조](https://technet.microsoft.com/library/ee890108\(v=office.15\).aspx)</span><span class="sxs-lookup"><span data-stu-id="283a1-234">[Windows PowerShell for SharePoint 2013 reference](https://technet.microsoft.com/library/ee890108\(v=office.15\).aspx)</span></span>

 <span data-ttu-id="283a1-235">[SharePoint Foundation 2010용 Windows PowerShell 참조](https://technet.microsoft.com/library/ee890105\(v=office.14\).aspx)</span><span class="sxs-lookup"><span data-stu-id="283a1-235">[Windows PowerShell for SharePoint Foundation 2010 reference](https://technet.microsoft.com/library/ee890105\(v=office.14\).aspx)</span></span>

 <span data-ttu-id="283a1-236">[Windows PowerShell을 사용하여 Excel Services 관리(SharePoint Server 2010)](https://technet.microsoft.com/library/ff191201\(v=office.14\).aspx)</span><span class="sxs-lookup"><span data-stu-id="283a1-236">[Manage Excel Services with Windows PowerShell (SharePoint Server 2010)](https://technet.microsoft.com/library/ff191201\(v=office.14\).aspx)</span></span>

 [<span data-ttu-id="283a1-237">SQL Server 설치 로그 파일 보기 및 읽기</span><span class="sxs-lookup"><span data-stu-id="283a1-237">View and Read SQL Server Setup Log Files</span></span>](../../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md)

 [<span data-ttu-id="283a1-238">Get-EvenLog cmdlet 사용</span><span class="sxs-lookup"><span data-stu-id="283a1-238">Use the Get-EvenLog cmdlet</span></span>](https://technet.microsoft.com/library/ee176846.aspx)

##  <a name="full-powershell-script"></a><a name="bkmk_full_script"></a><span data-ttu-id="283a1-239">전체 PowerShell 스크립트</span><span class="sxs-lookup"><span data-stu-id="283a1-239">Full PowerShell Script</span></span>
 <span data-ttu-id="283a1-240">다음 스크립트에는 이전 섹션의 모든 명령이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="283a1-240">The Following script contains all of the commands from the previous sections.</span></span> <span data-ttu-id="283a1-241">스크립트는 이 항목에 있는 것과 동일한 순서로 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="283a1-241">The script runs the commands in the same order as they are presented in this topic.</span></span> <span data-ttu-id="283a1-242">스크립트에는 추가 필터링이 필요할 경우 이 항목에 명시된 일부 선택적 명령 변형이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="283a1-242">The script contains some optional variations of the commands noted in this topic in case you need additional filtering.</span></span> <span data-ttu-id="283a1-243">변형은 주석 문자(#)로 비활성화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="283a1-243">The variations are disabled with a comment character (#).</span></span> <span data-ttu-id="283a1-244">스크립트에는 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] SharePoint 모드를 확인하기 위한 일부 문도 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="283a1-244">The script also includes some statements for verifying [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] SharePoint mode.</span></span> <span data-ttu-id="283a1-245">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 문은 주석 문자(#)로 비활성화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="283a1-245">The [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] statements are disabled with a comment character (#).</span></span>

```powershell
# This script audits services related to PowerPivot for SharePoint
$starttime = Get-Date
write-host -foregroundcolor DarkGray StartTime $starttime

Write-Host  "Import the SharePoint PowerShell snappin"
Add-PSSnapin Microsoft.Sharepoint.Powershell -EA 0

Write-Host -ForegroundColor Green "Analysis Services Windows Service"
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"
Get-Service | Select name, displayname, status | Where {$_.Name -eq "msolap`$powerpivot"} | Format-Table -Property * -AutoSize | Out-Default

Write-Host -ForegroundColor Green "PowerPivotEngineService and PowerPivotSystemService"
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"

Get-PowerPivotSystemService | Select typename, status, applications, farm | Format-Table -property * -AutoSize | Out-Default
# If needed, you can run the following to compare job definitions specific to the service against the results of the timer job definition section
#Get-PowerPivotSystemService | select -ExpandProperty jobdefinitions | select displayname, schedule, service | format-table -property * -autosize | out-default

Get-PowerPivotEngineService | Select typename, status, name, instances, farm | Format-Table -property * -AutoSize | Out-Default
# If needed, you can run the following to compare job definitions specific to the service against the results of the timer job definition section
#Get-PowerPivotEngineService | select -ExpandProperty jobdefinitions | select displayname, schedule, service | format-table -property * -autosize | out-default

#Write-Host -ForegroundColor Green "Service Instances - optional if you want to associate services with the server"
#Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"
#Get-SPServiceInstance | select typename, status, server, service, instance | where {$_.TypeName -like "*powerpivot*" -or $_.TypeName -like "*excel*" -or $_.TypeName -like "*Analysis Services*"} | format-table -property * -autosize | out-default
#Get-PowerPivotEngineServiceInstance  | select typename, ASServername, status, server, service, instance
#Get-PowerPivotSystemServiceInstance  | select typename, ASSServerName, status, server, service, instance

Write-Host -ForegroundColor Green "PowerPivot And Excel Service Applications"
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"
Get-PowerPivotServiceApplication | Select typename,name, status, unattendedaccount, applicationpool, farm, database
Get-SPExcelServiceApplication | Select typename,  DisplayName, status

#Write-Host ""
Write-Host -ForegroundColor Green "PowerPivot Service Application pool"
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"
# the following assumes there is only 1 PowerPivot Service Application, and returns that application's pool name.  if you have more than one, use the 2nd version
$poolname = [string](Get-PowerPivotServiceApplication | Select -Property applicationpool)
$position = $poolname.lastindexof("=")
$poolname = $poolname.substring($position+1)
$poolname = $poolname.substring(0,$poolname.length-1)
Get-SPServiceApplicationPool | Select name, status, processaccountname, id | Where {$_.Name -eq $poolname} | Format-Table -Property * -AutoSize | Out-Default

#Write-Host ""
Write-Host -ForegroundColor Green "PowerPivot and Excel Service Application Proxy"
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"
Get-SPServiceApplicationProxy |  Select typename, status, unattendedaccount, displayname | Where {$_.TypeName -like "*powerpivot*" -or $_.TypeName -like "*excel services*"} | Format-Table -Property * -AutoSize | Out-Default
#Get-SPServiceApplicationProxy |  select typename, status, unattendedaccount, displayname | where {$_.TypeName -like "*powerpivot*" -or $_.TypeName -like "*Reporting Services*" -or $_.TypeName -like "*excel services*"} | format-table -property * -autosize | out-default

Write-Host -ForegroundColor Green "DATABASES"
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"
Get-SPDatabase | Select name, status, server, typename | Where {$_.TypeName -eq "content database" -or $_.TypeName -like "*Gemini*"} | Format-Table -Property * -AutoSize | Out-Default
#Get-SPDatabase | select name, status, server, typename | where {$_.TypeName -eq "content database" -or $_.TypeName -like "*Gemini*" -or $_.TypeName -like "*ReportingServices*"}

Write-Host -ForegroundColor Green "features"
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"
Get-SPFeature | Select displayname, status, scope, farm | Where {$_.displayName -like "*powerpivot*"} | Format-Table -Property * -AutoSize | Out-Default
#Get-SPFeature | select displayname, status, scope, farm | where {$_.displayName -like "*powerpivot*" -or $_.displayName -like "*ReportServer*"}  | format-table -property * -autosize | out-default

Write-Host -ForegroundColor Green "Timer Jobs (Job Definitions) -- list is the same as seen in the 'Review timer job definitions' section of the management dashboard"
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"
Get-SPTimerJob | Where {$_.service -like "*power*" -or $_.service -like "*mid*"} | Select status, displayname, LastRunTime, service | Format-Table -Property * -AutoSize | Out-Default

Write-Host -ForegroundColor Green "health rules"
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"
Get-SPHealthAnalysisRule | Select name, enabled, summary | Where {$_.summary -Like "*power*"}  | Format-Table -Property * -AutoSize | Out-Default

$time = Get-Date
Write-Host -ForegroundColor DarkGray StartTime $starttime
Write-Host -ForegroundColor DarkGray EndTime $time

Write-Host -ForegroundColor Green "Windows Event Log data MSSQL$POWERPIVOT and "
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"
Get-EventLog "application" | Where-Object {$_.source -like "msolap`$powerpivot*"}  | Select timegenerated, entrytype , source, message | Format-Table -Property * -autosize | Out-Default
#The following is the same command but with the Inforamtion events filtered out.
#Get-EventLog "application" | Where-Object {$_.source -like "msolap`$powerpivot*" -and ($_.entrytype -match "error" -or $_.entrytype -match "critical" -or $_.entrytype -match "warning")}  |select timegenerated, entrytype , source, message | format-table -property * -autosize | out-default

#Write-Host ""
Write-Host -ForegroundColor Green "ULS Log data"
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"
Get-SPLogEvent -StartTime(Get-Date).AddHours(-48) | Where-Object {$_.Area -eq "powerpivot service" -and $_.level -eq "high"} | Select timestamp, area, category, eventid, level, correlation, message | Format-Table -Property * -AutoSize | Out-Default
#the following example filters for the category 'data refresh'
#Get-SPLogEvent -starttime(get-date).addhours(-48) | Where-Object {$_.category -eq "data refresh" -and $_.level -eq "high"} | select timestamp, area, category, eventid, level, correlation, message

$time = Get-Date
Write-Host -ForegroundColor DarkGray StartTime $starttime
Write-Host -ForegroundColor DarkGray EndTime $time

Write-Host -ForegroundColor Green "MSOLAP data provider for Excel Servivces, service application"
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"
$excelApp = Get-SPExcelServiceApplication
Get-SPExcelDataProvider -ExcelServiceApplication $excelApp | Select providerid, providertype, description | Where {$_.providerid -like "msolap*" } | Format-Table -Property * -AutoSize | Out-Default

Write-Host -ForegroundColor Green "ADOMD.net client library"
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"
Get-WMIObject -Class win32_product | Where-Object {$_.name -like "*ado*"} | Select name, version, vendor | Format-Table -Property * -AutoSize | Out-Default

Write-Host -ForegroundColor Green "Usage Data Rules"
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"
Get-SPUsageDefinition | Select name, status, enabled, tablename, DaysToKeepDetailedData | Where {$_.name -like "powerpivot*"} | Format-Table -Property * -AutoSize | Out-Default

Write-Host -ForegroundColor Green "Solutions"
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"
Get-SPSolution | Select name, status, deployed, DeploymentState, DeployedServers | Where {$_.Name -like "*powerpivot*"} | Format-Table -Property * -AutoSize | Out-Default

$time = Get-Date
Write-Host -ForegroundColor DarkGray StartTime $starttime
Write-Host -ForegroundColor DarkGray EndTime $time
```
