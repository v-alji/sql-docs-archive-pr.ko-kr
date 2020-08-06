---
title: 업그레이드 관리자 실행 (명령 프롬프트) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Upgrade Advisor [SQL Server], running
- command prompt [Upgrade Advisor]
- UpgradeAdvisorWizardCmd utility
- XML formats [Upgrade Advisor]
ms.assetid: 7c83049b-9227-4723-9b7f-66288bc6bd1d
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: a968f9d70788e1100af263f3ef9947493b4bd0c0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639236"
---
# <a name="running-upgrade-advisor-command-prompt"></a><span data-ttu-id="2b89d-102">업그레이드 관리자 실행(명령 프롬프트)</span><span class="sxs-lookup"><span data-stu-id="2b89d-102">Running Upgrade Advisor (Command Prompt)</span></span>
  <span data-ttu-id="2b89d-103">**UpgradeAdvisorWizardCmd** 유틸리티를 사용 하 여 명령 프롬프트에서 업그레이드 관리자를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="2b89d-103">Use the **UpgradeAdvisorWizardCmd** utility to run Upgrade Advisor from the command prompt.</span></span> <span data-ttu-id="2b89d-104">XML 형식, 또는 쉼표로 구분된 값을 사용하는 파일로 결과를 받을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b89d-104">You can choose to receive results in XML format or in a file with comma-separated values.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b89d-105">구문</span><span class="sxs-lookup"><span data-stu-id="2b89d-105">Syntax</span></span>  
  
```  
  
      UpgradeAdvisorWizardCmd [ -? ]  |   
    [ -ConfigFilefilename | <server_info> ]  
    [ -SqlUserlogin_id-SqlPasswordpassword ]  
    [ -CSV ]  
  
where <server_info> is any combination of the following:  
        -Serverserver_name-Instanceinstance_name-ASInstanceAS_instance_name-RSInstanceRS_instance_name  
```  
  
## <a name="arguments"></a><span data-ttu-id="2b89d-106">인수</span><span class="sxs-lookup"><span data-stu-id="2b89d-106">Arguments</span></span>  
 <span data-ttu-id="2b89d-107">**-?**</span><span class="sxs-lookup"><span data-stu-id="2b89d-107">**-?**</span></span>  
 <span data-ttu-id="2b89d-108">명령 구문을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="2b89d-108">Displays the command syntax.</span></span>  
  
 <span data-ttu-id="2b89d-109">**-** Smi-s _파일 이름_</span><span class="sxs-lookup"><span data-stu-id="2b89d-109">**-ConfigFile** _filename_</span></span>  
 <span data-ttu-id="2b89d-110">**UpgradeAdvisorWizardCmd** 유틸리티를 실행할 때 사용할 설정이 포함 된 XML 파일의 경로 이름 및 파일 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="2b89d-110">Is the path name and file name of an XML file that contains settings to use when you run the **UpgradeAdvisorWizardCmd** utility.</span></span>  
  
 <span data-ttu-id="2b89d-111">*<server_info>*</span><span class="sxs-lookup"><span data-stu-id="2b89d-111">*<server_info>*</span></span>  
 <span data-ttu-id="2b89d-112">분석할 컴퓨터와 인스턴스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2b89d-112">Specifies which computer and instance to analyze.</span></span> <span data-ttu-id="2b89d-113">구성 파일을 사용하지 않는 경우 이 옵션을 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="2b89d-113">Use these options if you are not using a configuration file.</span></span>  
  
 <span data-ttu-id="2b89d-114">*<server_info>* 는 다음 네 개의 인수를 임의로 조합 하 여 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b89d-114">*<server_info>* can be any combination of the following four arguments:</span></span>  
  
 <span data-ttu-id="2b89d-115">**-서버** _server_name_</span><span class="sxs-lookup"><span data-stu-id="2b89d-115">**-Server** _server_name_</span></span>  
 <span data-ttu-id="2b89d-116">분석할 컴퓨터의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2b89d-116">Specifies the name of the computer to analyze.</span></span> <span data-ttu-id="2b89d-117">로컬 컴퓨터(기본값) 또는 원격 컴퓨터일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b89d-117">This can be the local computer, which is the default value, or a remote computer.</span></span>  
  
 <span data-ttu-id="2b89d-118">**-인스턴스** _instance_name_</span><span class="sxs-lookup"><span data-stu-id="2b89d-118">**-Instance** _instance_name_</span></span>  
 <span data-ttu-id="2b89d-119">분석할 인스턴스의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2b89d-119">Specifies the name of the instance to analyze.</span></span> <span data-ttu-id="2b89d-120">기본값은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2b89d-120">There is no default value.</span></span> <span data-ttu-id="2b89d-121">이 매개 변수를 지정하지 않으면 [!INCLUDE[ssDE](../../includes/ssde-md.md)]이 검색되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2b89d-121">If you do not specify this parameter, the [!INCLUDE[ssDE](../../includes/ssde-md.md)] is not scanned.</span></span> <span data-ttu-id="2b89d-122">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 기본 인스턴스에 대한 값은 MSSQLSERVER입니다.</span><span class="sxs-lookup"><span data-stu-id="2b89d-122">The value for a default instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is MSSQLSERVER.</span></span> <span data-ttu-id="2b89d-123">명명된 인스턴스의 경우 인스턴스 이름을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="2b89d-123">For a named instance, use the instance name.</span></span>  
  
 <span data-ttu-id="2b89d-124">**-Asinstance**  _AS_instance_name_</span><span class="sxs-lookup"><span data-stu-id="2b89d-124">**-ASInstance**  _AS_instance_name_</span></span>  
 <span data-ttu-id="2b89d-125">분석할 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2b89d-125">Specifies the name of the instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] to analyze.</span></span> <span data-ttu-id="2b89d-126">기본값은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2b89d-126">There is no default value.</span></span> <span data-ttu-id="2b89d-127">이 값을 지정하지 않으면 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]가 검색되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2b89d-127">If you do not specify this value, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] is not scanned.</span></span> <span data-ttu-id="2b89d-128">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]의 기본 인스턴스에 대한 값은 MSSQLServerOLAPService입니다.</span><span class="sxs-lookup"><span data-stu-id="2b89d-128">The value for a default instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] is MSSQLServerOLAPService.</span></span> <span data-ttu-id="2b89d-129">명명된 인스턴스의 경우 인스턴스 이름을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="2b89d-129">For a named instance, use the instance name.</span></span>  
  
 <span data-ttu-id="2b89d-130">**-RSInstance**  _RS_instance_name_</span><span class="sxs-lookup"><span data-stu-id="2b89d-130">**-RSInstance**  _RS_instance_name_</span></span>  
 <span data-ttu-id="2b89d-131">분석할 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 인스턴스의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2b89d-131">Specifies the name of the instance of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] to analyze.</span></span> <span data-ttu-id="2b89d-132">기본값은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2b89d-132">There is no default value.</span></span> <span data-ttu-id="2b89d-133">이 값을 지정하지 않으면 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]가 검색되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2b89d-133">If you do not specify this value, [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] is not scanned.</span></span> <span data-ttu-id="2b89d-134">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]의 기본 인스턴스에 대한 값은 ReportServer입니다.</span><span class="sxs-lookup"><span data-stu-id="2b89d-134">The value for a default instance of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] is ReportServer.</span></span> <span data-ttu-id="2b89d-135">명명된 인스턴스의 경우 인스턴스 이름을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="2b89d-135">For a named instance, use the instance name.</span></span>  
  
 <span data-ttu-id="2b89d-136">**-SqlUser** _login_id_</span><span class="sxs-lookup"><span data-stu-id="2b89d-136">**-SqlUser** _login_id_</span></span>  
 <span data-ttu-id="2b89d-137">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인증을 사용하는 경우 이 값은 업그레이드 관리자가 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 연결하는 데 사용하는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그인입니다.</span><span class="sxs-lookup"><span data-stu-id="2b89d-137">If you are using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication, this value is the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login that Upgrade Advisor will use to connect to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="2b89d-138">로그인을 지정하지 않으면 Windows 인증을 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 연결됩니다.</span><span class="sxs-lookup"><span data-stu-id="2b89d-138">If you do not specify a login, Windows Authentication is used to connect to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span>  
  
 <span data-ttu-id="2b89d-139">**-Sqlpassword** _암호_</span><span class="sxs-lookup"><span data-stu-id="2b89d-139">**-SqlPassword** _password_</span></span>  
 <span data-ttu-id="2b89d-140">**-SqlUser** 인수를 사용 하는 경우이 인수를 사용 하 여 로그인에 대 한 암호를 지정 합니다 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="2b89d-140">If you use the **-SqlUser** argument, use this argument to specify the password for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login.</span></span>  
  
 <span data-ttu-id="2b89d-141">**-CSV**</span><span class="sxs-lookup"><span data-stu-id="2b89d-141">**-CSV**</span></span>  
 <span data-ttu-id="2b89d-142">표준 XML 결과 외에 쉼표로 구분된 값을 사용하여 .csv 파일로도 결과를 제공하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2b89d-142">Specifies to provide results as comma-separated values to a .csv file in addition to the standard XML results.</span></span> <span data-ttu-id="2b89d-143">결과는 내 문서 \\ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Upgrade Advisor\110\Reports 폴더에 기록 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2b89d-143">Results are written to the My Documents\\[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Upgrade Advisor\110\Reports folder.</span></span>  
  
## <a name="return-values"></a><span data-ttu-id="2b89d-144">반환 값</span><span class="sxs-lookup"><span data-stu-id="2b89d-144">Return Values</span></span>  
 <span data-ttu-id="2b89d-145">다음 표에서는 **UpgradeAdvisorWizardCmd** 가 반환 하는 값을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2b89d-145">The following table shows the values that **UpgradeAdvisorWizardCmd** returns.</span></span>  
  
|<span data-ttu-id="2b89d-146">값</span><span class="sxs-lookup"><span data-stu-id="2b89d-146">Value</span></span>|<span data-ttu-id="2b89d-147">설명</span><span class="sxs-lookup"><span data-stu-id="2b89d-147">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="2b89d-148">0</span><span class="sxs-lookup"><span data-stu-id="2b89d-148">0</span></span>|<span data-ttu-id="2b89d-149">분석이 성공했으며 업그레이드 문제가 발견되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="2b89d-149">Analysis succeeded, no upgrade issues found.</span></span>|  
|<span data-ttu-id="2b89d-150">양의 정수</span><span class="sxs-lookup"><span data-stu-id="2b89d-150">positive integer</span></span>|<span data-ttu-id="2b89d-151">분석이 성공했으며 업그레이드 문제가 발견되었습니다.</span><span class="sxs-lookup"><span data-stu-id="2b89d-151">Analysis succeeded, upgrade issues found.</span></span>|  
|<span data-ttu-id="2b89d-152">음의 정수</span><span class="sxs-lookup"><span data-stu-id="2b89d-152">negative integer</span></span>|<span data-ttu-id="2b89d-153">분석하지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="2b89d-153">Analysis failed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2b89d-154">설명</span><span class="sxs-lookup"><span data-stu-id="2b89d-154">Remarks</span></span>  
 <span data-ttu-id="2b89d-155">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인증 사용자 이름과 암호를 제외하고 분석을 실행하는 데 필요한 모든 정보는 XML 구성 파일로 제공될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b89d-155">All information that is required to run the analysis, other than [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication user names and passwords, can be provided in an XML configuration file.</span></span> <span data-ttu-id="2b89d-156">이 XML 구성 파일은 템플릿에 문서화되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b89d-156">This XML configuration file is documented in the template.</span></span> <span data-ttu-id="2b89d-157">구성 파일을 사용하지 않는 경우에는 컴퓨터 이름과 인스턴스 이름을 지정하여 기본 설정으로 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스의 모든 설치된 구성 요소를 분석할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b89d-157">If you do not use a configuration file, you can analyze all installed components in an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using default settings by specifying computer names and instance names.</span></span> <span data-ttu-id="2b89d-158">기본 구성 파일 설정에 대한 자세한 내용은 이 항목 뒷부분의 "요소 설명" 표를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="2b89d-158">See the "Element Descriptions" table later in this topic for a description of the default configuration file settings.</span></span>  
  
## <a name="configuration-file-template"></a><span data-ttu-id="2b89d-159">구성 파일 템플릿</span><span class="sxs-lookup"><span data-stu-id="2b89d-159">Configuration File Template</span></span>  
 <span data-ttu-id="2b89d-160">다음 XML을 템플릿으로 사용하여 사용자가 원하는 구성 파일을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b89d-160">Use the following XML as a template for creating your own configuration files.</span></span> <span data-ttu-id="2b89d-161">사용자 조직의 요구 사항에 맞게 템플릿을 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b89d-161">You can modify the template to meet the needs of your organization.</span></span>  
  
```xml  
<Configuration>  
    <Server> </Server>  
    <Instance></Instance>  
    <Components>  
        <SQLServer>  
            <Databases>  
                <Database></Database>  
            </Databases>  
            <TraceFiles>  
                <TraceFile></TraceFile>  
            </TraceFiles>  
            <BatchFiles>  
                <BatchFile></BatchFile>  
            </BatchFiles>  
            <BatchSeparator></BatchSeparator>  
        </SQLServer>  
        <AnalysisServices>  
            <ASInstance></ASInstance>  
            <Databases>  
                <Database></Database>  
            </Databases>  
        </AnalysisServices>  
        <ReportingServices>  
            <RSInstance></RSInstance>  
        </ReportingServices>  
        <IntegrationServices>  
            <PackagePath></PackagePath>  
        </IntegrationServices>  
    </Components>  
</Configuration>  
```  
  
## <a name="element-descriptions"></a><span data-ttu-id="2b89d-162">요소 설명</span><span class="sxs-lookup"><span data-stu-id="2b89d-162">Element Descriptions</span></span>  
  
|<span data-ttu-id="2b89d-163">태그</span><span class="sxs-lookup"><span data-stu-id="2b89d-163">Tag</span></span>|<span data-ttu-id="2b89d-164">정의</span><span class="sxs-lookup"><span data-stu-id="2b89d-164">Definition</span></span>|<span data-ttu-id="2b89d-165">발생 빈도</span><span class="sxs-lookup"><span data-stu-id="2b89d-165">Occurrence</span></span>|  
|---------|----------------|----------------|  
|`Configuration`|<span data-ttu-id="2b89d-166">업그레이드 관리자 구성 파일에 대한 부모 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="2b89d-166">Parent element for Upgrade Advisor configuration file.</span></span>|<span data-ttu-id="2b89d-167">구성 파일마다 한 번 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2b89d-167">Required once per configuration file.</span></span>|  
|`Server`|<span data-ttu-id="2b89d-168">분석할 서버의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="2b89d-168">Name of the server to analyze.</span></span>|<span data-ttu-id="2b89d-169">구성 파일마다 한 번만 지정할 수 있습니다(옵션).</span><span class="sxs-lookup"><span data-stu-id="2b89d-169">Optional once per configuration file.</span></span> <span data-ttu-id="2b89d-170">기본값은 로컬 컴퓨터입니다.</span><span class="sxs-lookup"><span data-stu-id="2b89d-170">The default value is the local computer.</span></span>|  
|`Instance`|<span data-ttu-id="2b89d-171">분석할 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 인스턴스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="2b89d-171">Name of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] instance to analyze.</span></span>|<span data-ttu-id="2b89d-172">구성 파일마다 한 번만 지정할 수 있습니다(옵션).</span><span class="sxs-lookup"><span data-stu-id="2b89d-172">Optional once per configuration file.</span></span> <span data-ttu-id="2b89d-173">기본값은 기본 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="2b89d-173">The default value is the default instance.</span></span><br /><br /> <span data-ttu-id="2b89d-174">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 요소나 `IntegrationServices` 요소가 서버에 있는 경우에는 구성 파일마다 한 번 지정해야 합니다</span><span class="sxs-lookup"><span data-stu-id="2b89d-174">Required once per configuration file, if a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] element or an `IntegrationServices` element is present on the server.</span></span>|  
|`Components`|<span data-ttu-id="2b89d-175">분석할 구성 요소를 지정하는 요소를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="2b89d-175">Contains elements that specify which components to analyze.</span></span>|<span data-ttu-id="2b89d-176">구성 파일마다 한 번 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2b89d-176">Required once per configuration file.</span></span>|  
|`SQLServer`|<span data-ttu-id="2b89d-177">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 인스턴스에 대한 분석 설정을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="2b89d-177">Contains analysis settings for an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>|<span data-ttu-id="2b89d-178">구성 파일마다 한 번만 지정할 수 있습니다(옵션).</span><span class="sxs-lookup"><span data-stu-id="2b89d-178">Optional once per configuration file.</span></span> <span data-ttu-id="2b89d-179">지정하지 않으면 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 데이터베이스가 분석되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2b89d-179">If not specified, [!INCLUDE[ssDE](../../includes/ssde-md.md)] databases are not analyzed.</span></span>|  
|<span data-ttu-id="2b89d-180">`Databases` 요소용 `SQLServer`</span><span class="sxs-lookup"><span data-stu-id="2b89d-180">`Databases` for `SQLServer` element</span></span>|<span data-ttu-id="2b89d-181">분석할 데이터베이스의 목록을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="2b89d-181">Contains a list of databases to analyze.</span></span>|<span data-ttu-id="2b89d-182">`SQLServer` 요소마다 한 번만 지정할 수 있습니다(옵션).</span><span class="sxs-lookup"><span data-stu-id="2b89d-182">Optional once per `SQLServer` element.</span></span> <span data-ttu-id="2b89d-183">이 요소가 없으면 인스턴스의 모든 데이터베이스가 분석됩니다.</span><span class="sxs-lookup"><span data-stu-id="2b89d-183">If this element is not present, all databases in the instance are analyzed.</span></span>|  
|<span data-ttu-id="2b89d-184">`Database` 요소용 `SQLServer`</span><span class="sxs-lookup"><span data-stu-id="2b89d-184">`Database` for `SQLServer` element</span></span>|<span data-ttu-id="2b89d-185">분석할 데이터베이스의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2b89d-185">Specifies the name of a database to analyze.</span></span>|<span data-ttu-id="2b89d-186">`Databases` 요소가 있는 경우 한 번 이상 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="2b89d-186">Required once or more if the `Databases` element is present.</span></span> <span data-ttu-id="2b89d-187">`Database` 요소에 "\*" 값이 포함되면 인스턴스의 모든 데이터베이스가 분석됩니다.</span><span class="sxs-lookup"><span data-stu-id="2b89d-187">If a `Database` element contains the value "\*", all databases in the instance are analyzed.</span></span> <span data-ttu-id="2b89d-188">기본값은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2b89d-188">There is no default value.</span></span>|  
|`TraceFiles`|<span data-ttu-id="2b89d-189">분석할 추적 파일의 목록을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="2b89d-189">Contains a list of trace files to analyze.</span></span>|<span data-ttu-id="2b89d-190">`SQLServer` 요소마다 한 번만 지정할 수 있습니다(옵션).</span><span class="sxs-lookup"><span data-stu-id="2b89d-190">Optional once per `SQLServer` element.</span></span>|  
|`TraceFile`|<span data-ttu-id="2b89d-191">분석할 추적 파일의 경로와 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2b89d-191">Specifies the path and name of a trace file to analyze.</span></span>|<span data-ttu-id="2b89d-192">`TraceFiles` 요소가 있는 경우 한 번 이상 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="2b89d-192">Required once or more if the `TraceFiles` element is present.</span></span> <span data-ttu-id="2b89d-193">기본값은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2b89d-193">There is no default value.</span></span>|  
|`BatchFiles`|<span data-ttu-id="2b89d-194">분석할 배치 파일의 목록을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="2b89d-194">Contains a list of batch files to analyze.</span></span>|<span data-ttu-id="2b89d-195">`SQLServer` 요소마다 한 번만 지정할 수 있습니다(옵션).</span><span class="sxs-lookup"><span data-stu-id="2b89d-195">Optional once per `SQLServer` element.</span></span>|  
|`BatchFile`|<span data-ttu-id="2b89d-196">분석할 배치 파일을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2b89d-196">Specifies a batch file to analyze.</span></span> <span data-ttu-id="2b89d-197">여러 개일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b89d-197">Can be multiple.</span></span>|<span data-ttu-id="2b89d-198">`BatchFiles` 요소가 있는 경우 한 번 이상 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="2b89d-198">Required once or more if the `BatchFiles` element is present.</span></span> <span data-ttu-id="2b89d-199">기본값은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2b89d-199">There is no default value.</span></span>|  
|`BatchSeparator`|<span data-ttu-id="2b89d-200">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 배치 파일에 사용되는 일괄 처리 구분 기호를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2b89d-200">Specifies the batch separator used in your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] batch files.</span></span>|<span data-ttu-id="2b89d-201">`SQLServer` 요소마다 한 번만 지정할 수 있습니다(옵션).</span><span class="sxs-lookup"><span data-stu-id="2b89d-201">Optional once per `SQLServer` element.</span></span> <span data-ttu-id="2b89d-202">기본값은 GO입니다.</span><span class="sxs-lookup"><span data-stu-id="2b89d-202">The default value is GO.</span></span>|  
|`AnalysisServices`|<span data-ttu-id="2b89d-203">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]에 대한 분석 설정을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="2b89d-203">Contains analysis settings for [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>|<span data-ttu-id="2b89d-204">구성 파일마다 한 번만 지정할 수 있습니다(옵션).</span><span class="sxs-lookup"><span data-stu-id="2b89d-204">Optional once per configuration file.</span></span> <span data-ttu-id="2b89d-205">지정하지 않으면 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 데이터베이스가 분석되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2b89d-205">If not specified, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] databases are not analyzed.</span></span>|  
|`ASInstance`|<span data-ttu-id="2b89d-206">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2b89d-206">Specifies the name of an instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>|<span data-ttu-id="2b89d-207">각 `AnalysisServices` 요소 당 한 번씩만 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="2b89d-207">Required once per `AnalysisServices` element.</span></span> <span data-ttu-id="2b89d-208">기본값은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2b89d-208">There is no default value.</span></span>|  
|<span data-ttu-id="2b89d-209">`Databases` 요소용 `Analysis Services`</span><span class="sxs-lookup"><span data-stu-id="2b89d-209">`Databases` for `Analysis Services` element</span></span>|<span data-ttu-id="2b89d-210">분석할 데이터베이스의 목록을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="2b89d-210">Contains a list of databases to analyze.</span></span>|<span data-ttu-id="2b89d-211">`AnalysisServices` 요소마다 한 번만 지정할 수 있습니다(옵션).</span><span class="sxs-lookup"><span data-stu-id="2b89d-211">Optional once per `AnalysisServices` element.</span></span> <span data-ttu-id="2b89d-212">이 요소가 없으면 인스턴스의 모든 데이터베이스가 분석됩니다.</span><span class="sxs-lookup"><span data-stu-id="2b89d-212">If this element is not present, all databases in the instance are analyzed.</span></span>|  
|<span data-ttu-id="2b89d-213">`Database` 요소용 `AnalysisServices`</span><span class="sxs-lookup"><span data-stu-id="2b89d-213">`Database` for `AnalysisServices` element</span></span>|<span data-ttu-id="2b89d-214">분석할 데이터베이스의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2b89d-214">Specifies the name of a database to analyze.</span></span>|<span data-ttu-id="2b89d-215">`Databases` 요소가 있는 경우 한 번 이상 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="2b89d-215">Required once or more if the `Databases` element is present.</span></span> <span data-ttu-id="2b89d-216">`Database` 요소에 "\*" 값이 포함되면 인스턴스의 모든 데이터베이스가 분석됩니다.</span><span class="sxs-lookup"><span data-stu-id="2b89d-216">If a `Database` element contains the value "\*", all databases in the instance are analyzed.</span></span> <span data-ttu-id="2b89d-217">기본값은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2b89d-217">There is no default value.</span></span>|  
|`ReportingServices`|<span data-ttu-id="2b89d-218">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]에 대해 분석을 실행하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2b89d-218">Specifies to run analysis against [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span>|<span data-ttu-id="2b89d-219">구성 파일마다 한 번만 지정할 수 있습니다(옵션).</span><span class="sxs-lookup"><span data-stu-id="2b89d-219">Optional once per configuration file.</span></span> <span data-ttu-id="2b89d-220">지정하지 않으면 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]가 분석되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2b89d-220">If not specified, [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] is not analyzed.</span></span>|  
|`RSInstance`|<span data-ttu-id="2b89d-221">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 인스턴스 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2b89d-221">Specifies the name of an instance of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span>|<span data-ttu-id="2b89d-222">각 `ReportingServices` 요소 당 한 번씩만 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="2b89d-222">Required once per `ReportingServices` element.</span></span> <span data-ttu-id="2b89d-223">기본값은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2b89d-223">There is no default value.</span></span>|  
|`IntegrationServices`|<span data-ttu-id="2b89d-224">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]에 대한 분석 설정을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="2b89d-224">Contains analysis settings for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].</span></span>|<span data-ttu-id="2b89d-225">구성 파일마다 한 번만 지정할 수 있습니다(옵션).</span><span class="sxs-lookup"><span data-stu-id="2b89d-225">Optional once per configuration file.</span></span> <span data-ttu-id="2b89d-226">지정하지 않으면 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]가 분석되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2b89d-226">If not specified, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] is not analyzed.</span></span>|  
|`PackagePath`|<span data-ttu-id="2b89d-227">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 패키지 집합의 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2b89d-227">Specifies the path of a set of [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages.</span></span>|<span data-ttu-id="2b89d-228">`IntegrationServices` 요소마다 한 번만 지정할 수 있습니다(옵션).</span><span class="sxs-lookup"><span data-stu-id="2b89d-228">Optional once per `IntegrationServices` element.</span></span> <span data-ttu-id="2b89d-229">이 요소가 없으면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에서 분석이 수행되며 외부에서 저장된 패키지는 분석되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2b89d-229">If this element is not present, analysis occurs on the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance, and no externally stored packages are analyzed.</span></span> <span data-ttu-id="2b89d-230">기본값은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2b89d-230">There is no default value.</span></span>|  
  
## <a name="examples"></a><span data-ttu-id="2b89d-231">예</span><span class="sxs-lookup"><span data-stu-id="2b89d-231">Examples</span></span>  
  
### <a name="a-run-upgrade-advisor-using-a-configuration-file"></a><span data-ttu-id="2b89d-232">A.</span><span class="sxs-lookup"><span data-stu-id="2b89d-232">A.</span></span> <span data-ttu-id="2b89d-233">구성 파일을 사용하여 업그레이드 관리자 실행</span><span class="sxs-lookup"><span data-stu-id="2b89d-233">Run Upgrade Advisor Using a Configuration File</span></span>  
 <span data-ttu-id="2b89d-234">다음 예에서는 분석할 대상을 지정하는 구성 파일을 사용하여 명령 프롬프트에서 업그레이드 관리자를 실행하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2b89d-234">The following example shows how to run Upgrade Advisor from the command prompt by using a configuration file that specifies what to analyze.</span></span> <span data-ttu-id="2b89d-235">이 예에서는 Windows 인증을 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="2b89d-235">This example uses Windows Authentication to connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
```  
UpgradeAdvisorWizardCmd -ConfigFile "C:\My Documents\UpgradeConfig1.xml"  
```  
  
### <a name="b-run-upgrade-advisor-using-default-configuration-settings"></a><span data-ttu-id="2b89d-236">B.</span><span class="sxs-lookup"><span data-stu-id="2b89d-236">B.</span></span> <span data-ttu-id="2b89d-237">기본 구성 설정을 사용하여 업그레이드 관리자 실행</span><span class="sxs-lookup"><span data-stu-id="2b89d-237">Run Upgrade Advisor Using Default Configuration Settings</span></span>  
 <span data-ttu-id="2b89d-238">다음 예에서는 기본 구성 설정과 Windows 인증을 사용하여 명령 프롬프트에서 업그레이드 관리자를 실행하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2b89d-238">The following example shows how to run Upgrade Advisor from the command prompt by using default configuration settings and Windows Authentication.</span></span>  
  
```  
UpgradeAdvisorWizardCmd -Server MyServer -Instance MyInst   
```  
  
### <a name="c-run-upgrade-advisor-using-ssnoversion-authentication"></a><span data-ttu-id="2b89d-239">C.</span><span class="sxs-lookup"><span data-stu-id="2b89d-239">C.</span></span> <span data-ttu-id="2b89d-240">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인증을 사용하여 업그레이드 관리자 실행</span><span class="sxs-lookup"><span data-stu-id="2b89d-240">Run Upgrade Advisor Using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication</span></span>  
 <span data-ttu-id="2b89d-241">다음 예에서는 구성 파일을 사용하여 명령 프롬프트에서 업그레이드 관리자를 실행하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2b89d-241">The following example shows how to run Upgrade Advisor from the command prompt by using a configuration file.</span></span> <span data-ttu-id="2b89d-242">이 예에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 사용자 이름과 암호를 지정하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="2b89d-242">This example specifies a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] user name and password to connect to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
```  
UpgradeAdvisorWizardCmd -ConfigFile "C:\My Documents\UpgradeConfig1.xml"   
    -SqlUser "MyUserName" -SqlPassword "QweRTy-55"  
```  
  
## <a name="see-also"></a><span data-ttu-id="2b89d-243">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2b89d-243">See Also</span></span>  
 <span data-ttu-id="2b89d-244">[업그레이드 문제 해결](../../../2014/sql-server/install/resolving-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="2b89d-244">[Resolving Upgrade Issues](../../../2014/sql-server/install/resolving-upgrade-issues.md) </span></span>  
 <span data-ttu-id="2b89d-245">[업그레이드 관리자 작업](../../../2014/sql-server/install/working-with-upgrade-advisor.md) </span><span class="sxs-lookup"><span data-stu-id="2b89d-245">[Working with Upgrade Advisor](../../../2014/sql-server/install/working-with-upgrade-advisor.md) </span></span>  
 [<span data-ttu-id="2b89d-246">업그레이드 관리자 &#40;사용자 인터페이스를 실행 하는 중&#41;</span><span class="sxs-lookup"><span data-stu-id="2b89d-246">Running Upgrade Advisor &#40;User Interface&#41;</span></span>](../../../2014/sql-server/install/running-upgrade-advisor-user-interface.md)  
  
  
