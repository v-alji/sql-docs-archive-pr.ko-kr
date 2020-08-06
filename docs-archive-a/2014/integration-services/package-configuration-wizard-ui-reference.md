---
title: 패키지 구성 마법사 UI 참조 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.configwizard.selectobjects.f1
- sql12.dts.configwizard.selecconfigtype.f1
- sql12.dts.configwizard.finishdtsconfiguration.f1
- sql12.dts.configwizard.welcome.f1
ms.assetid: adca6938-6d5a-40ec-950e-dceb79d044fe
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 222c5f58ca4e942dd23909b433ab346c500fceed
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660051"
---
# <a name="package-configuration-wizard-ui-reference"></a><span data-ttu-id="b45c0-102">패키지 구성 마법사 UI 참조</span><span class="sxs-lookup"><span data-stu-id="b45c0-102">Package Configuration Wizard UI Reference</span></span>
  <span data-ttu-id="b45c0-103">**패키지 구성 마법사** 를 사용하여 런타임에 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 패키지 및 패키지 개체의 속성을 업데이트하는 구성을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b45c0-103">Use the **Package Configuration Wizard** to create configurations that update the properties of an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package and its objects at run time.</span></span> <span data-ttu-id="b45c0-104">이 마법사는 **패키지 구성 도우미** 대화 상자에서 기존 구성을 수정하거나 새 구성을 추가하는 경우 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="b45c0-104">This wizard runs when you add a new configuration or modify an existing one in the **Package Configurations Organizer** dialog box.</span></span> <span data-ttu-id="b45c0-105">**패키지 구성 도우미** 대화 상자를 열려면 **의** SSIS **메뉴에서** 패키지 구성 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b45c0-105">To open the **Package Configurations Organizer** dialog box, select **Package Configurations** on the **SSIS** menu in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="b45c0-106">자세한 내용은 [패키지 구성 만들기](../../2014/integration-services/create-package-configurations.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b45c0-106">For more information, see [Create Package Configurations](../../2014/integration-services/create-package-configurations.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b45c0-107">구성은 패키지 배포 모델에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b45c0-107">Configurations are available for the package deployment model.</span></span> <span data-ttu-id="b45c0-108">매개 변수는 프로젝트 배포 모델에 대한 구성 대신 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="b45c0-108">Parameters are used in place of configurations for the project deployment model.</span></span> <span data-ttu-id="b45c0-109">프로젝트 배포 모델을 사용하면 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 프로젝트를 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 서버에 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b45c0-109">The project deployment model enables you to deploy [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] projects to the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] server.</span></span> <span data-ttu-id="b45c0-110">배포 모델에 대한 자세한 내용은 [Deployment of Projects and Packages](packages/deploy-integration-services-ssis-projects-and-packages.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="b45c0-110">For more information about the deployment models, see [Deployment of Projects and Packages](packages/deploy-integration-services-ssis-projects-and-packages.md).</span></span>  
  
 <span data-ttu-id="b45c0-111">다음 섹션에서는 마법사의 페이지에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="b45c0-111">The following sections describe pages of the Wizard.</span></span>  
  
## <a name="welcome-to-the-package-configuration-wizard-page"></a><span data-ttu-id="b45c0-112">패키지 구성 마법사 시작 페이지</span><span class="sxs-lookup"><span data-stu-id="b45c0-112">Welcome to the Package Configuration Wizard Page</span></span>  
 <span data-ttu-id="b45c0-113">**SSIS 구성 마법사** 를 사용하여 런타임에 패키지 및 패키지 개체의 속성을 업데이트하는 구성을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b45c0-113">Use the **SSIS Configuration Wizard** to create configurations that update the properties of a package and its objects at run time.</span></span>  
  
### <a name="options"></a><span data-ttu-id="b45c0-114">옵션</span><span class="sxs-lookup"><span data-stu-id="b45c0-114">Options</span></span>  
 <span data-ttu-id="b45c0-115">**이 페이지를 다시 표시 안 함**</span><span class="sxs-lookup"><span data-stu-id="b45c0-115">**Don't show this page again**</span></span>  
 <span data-ttu-id="b45c0-116">다음에 마법사를 열 때 시작 페이지를 표시하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b45c0-116">Skip the welcome page the next time you open the wizard.</span></span>  
  
 <span data-ttu-id="b45c0-117">**다음**</span><span class="sxs-lookup"><span data-stu-id="b45c0-117">**Next**</span></span>  
 <span data-ttu-id="b45c0-118">마법사의 다음 페이지로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="b45c0-118">Go the next page in the wizard.</span></span>  
  
## <a name="select-configuration-type-page"></a><span data-ttu-id="b45c0-119">구성 유형 선택 페이지</span><span class="sxs-lookup"><span data-stu-id="b45c0-119">Select Configuration Type Page</span></span>  
 <span data-ttu-id="b45c0-120">**구성 유형 선택** 페이지를 사용하여 만들 구성 유형을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b45c0-120">Use the **Select Configuration Type** page to specify the type of configuration to create.</span></span>  
  
 <span data-ttu-id="b45c0-121">사용할 구성 유형을 결정하는 데 추가 정보가 필요한 경우 [Package Configurations](../../2014/integration-services/package-configurations.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="b45c0-121">If you need additional information to determine which type of configuration to use, see [Package Configurations](../../2014/integration-services/package-configurations.md).</span></span>  
  
### <a name="static-options"></a><span data-ttu-id="b45c0-122">정적 옵션</span><span class="sxs-lookup"><span data-stu-id="b45c0-122">Static Options</span></span>  
 <span data-ttu-id="b45c0-123">**구성 유형**</span><span class="sxs-lookup"><span data-stu-id="b45c0-123">**Configuration type**</span></span>  
 <span data-ttu-id="b45c0-124">다음 옵션을 사용하여 구성을 저장할 원본 유형을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b45c0-124">Select the type of source in which to store the configuration, using the following options:</span></span>  
  
|<span data-ttu-id="b45c0-125">값</span><span class="sxs-lookup"><span data-stu-id="b45c0-125">Value</span></span>|<span data-ttu-id="b45c0-126">Description</span><span class="sxs-lookup"><span data-stu-id="b45c0-126">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b45c0-127">**XML 구성 파일**</span><span class="sxs-lookup"><span data-stu-id="b45c0-127">**XML configuration file**</span></span>|<span data-ttu-id="b45c0-128">구성을 XML 파일로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="b45c0-128">Store the configuration as an XML file.</span></span> <span data-ttu-id="b45c0-129">이 값을 선택하면 **구성 유형**섹션에 설명된 동적 옵션이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b45c0-129">Selecting this value displays the dynamic options in the section, **Configuration Type**.</span></span>|  
|<span data-ttu-id="b45c0-130">**환경 변수**</span><span class="sxs-lookup"><span data-stu-id="b45c0-130">**Environment variable**</span></span>|<span data-ttu-id="b45c0-131">환경 변수 중 하나에 구성을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="b45c0-131">Store the configuration in one of the environment variables.</span></span> <span data-ttu-id="b45c0-132">이 값을 선택하면 **구성 유형**섹션에 설명된 동적 옵션이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b45c0-132">Selecting this value displays the dynamic options in the section, **Configuration Type**.</span></span>|  
|<span data-ttu-id="b45c0-133">**레지스트리 항목**</span><span class="sxs-lookup"><span data-stu-id="b45c0-133">**Registry entry**</span></span>|<span data-ttu-id="b45c0-134">레지스트리에 구성을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="b45c0-134">Store the configuration in the Registry.</span></span> <span data-ttu-id="b45c0-135">이 값을 선택하면 **구성 유형**섹션에 설명된 동적 옵션이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b45c0-135">Selecting this value displays the dynamic options in the section, **Configuration Type**.</span></span>|  
|<span data-ttu-id="b45c0-136">**부모 패키지 변수**</span><span class="sxs-lookup"><span data-stu-id="b45c0-136">**Parent package variable**</span></span>|<span data-ttu-id="b45c0-137">태스크를 포함하는 패키지의 변수로 구성을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="b45c0-137">Store the configuration as a variable in the package that contains the task.</span></span>  <span data-ttu-id="b45c0-138">이 값을 선택하면 **구성 유형**섹션에 설명된 동적 옵션이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b45c0-138">Selecting this value displays the dynamic options in the section, **Configuration Type**.</span></span>|  
|<span data-ttu-id="b45c0-139">**SQL Server**</span><span class="sxs-lookup"><span data-stu-id="b45c0-139">**SQL Server**</span></span>|<span data-ttu-id="b45c0-140">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]의 테이블에 구성을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="b45c0-140">Store the configuration in a table in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="b45c0-141">이 값을 선택하면 **구성 유형**섹션에 설명된 동적 옵션이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b45c0-141">Selecting this value displays the dynamic options in the section, **Configuration Type**.</span></span>|  
  
 <span data-ttu-id="b45c0-142">**다음**</span><span class="sxs-lookup"><span data-stu-id="b45c0-142">**Next**</span></span>  
 <span data-ttu-id="b45c0-143">마법사 시퀀스에서 다음 페이지를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="b45c0-143">View the next page in the wizard sequence.</span></span>  
  
### <a name="dynamic-options"></a><span data-ttu-id="b45c0-144">동적 옵션</span><span class="sxs-lookup"><span data-stu-id="b45c0-144">Dynamic Options</span></span>  
  
#### <a name="configuration-type-option--xml-configuration-file"></a><span data-ttu-id="b45c0-145">구성 유형 옵션 = XML 구성 파일</span><span class="sxs-lookup"><span data-stu-id="b45c0-145">Configuration Type Option = XML Configuration File</span></span>  
 <span data-ttu-id="b45c0-146">**구성 설정을 직접 지정**</span><span class="sxs-lookup"><span data-stu-id="b45c0-146">**Specify configuration settings directly**</span></span>  
 <span data-ttu-id="b45c0-147">설정을 직접 지정하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="b45c0-147">Use to specify settings directly.</span></span>  
  
|<span data-ttu-id="b45c0-148">값</span><span class="sxs-lookup"><span data-stu-id="b45c0-148">Value</span></span>|<span data-ttu-id="b45c0-149">Description</span><span class="sxs-lookup"><span data-stu-id="b45c0-149">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b45c0-150">**구성 파일 이름**</span><span class="sxs-lookup"><span data-stu-id="b45c0-150">**Configuration file name**</span></span>|<span data-ttu-id="b45c0-151">마법사에서 생성하는 구성 파일의 경로를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="b45c0-151">Type the path of the configuration file that the wizard generates.</span></span>|  
|<span data-ttu-id="b45c0-152">**찾아보기**</span><span class="sxs-lookup"><span data-stu-id="b45c0-152">**Browse**</span></span>|<span data-ttu-id="b45c0-153">**구성 파일 위치 선택** 대화 상자를 사용하여 마법사에서 생성하는 구성 파일의 경로를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b45c0-153">Use the **Select Configuration File Location** dialog box to specify the path of the configuration file that the wizard generates.</span></span> <span data-ttu-id="b45c0-154">파일이 없으면 마법사에서 새 파일을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="b45c0-154">If the file does not exist, it is created by the wizard.</span></span>|  
  
 <span data-ttu-id="b45c0-155">**구성 위치가 환경 변수에 저장됨**</span><span class="sxs-lookup"><span data-stu-id="b45c0-155">**Configuration location is stored in an environment variable**</span></span>  
 <span data-ttu-id="b45c0-156">구성이 저장되는 환경 변수를 지정하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="b45c0-156">Use to specify the environment variable in which to store the configuration.</span></span>  
  
|<span data-ttu-id="b45c0-157">값</span><span class="sxs-lookup"><span data-stu-id="b45c0-157">Value</span></span>|<span data-ttu-id="b45c0-158">Description</span><span class="sxs-lookup"><span data-stu-id="b45c0-158">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b45c0-159">**환경 변수**</span><span class="sxs-lookup"><span data-stu-id="b45c0-159">**Environment variable**</span></span>|<span data-ttu-id="b45c0-160">목록에서 환경 변수를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b45c0-160">Select an environment variable from the list.</span></span>|  
  
#### <a name="configuration-type-option--environment-variable"></a><span data-ttu-id="b45c0-161">구성 유형 옵션 = 환경 변수</span><span class="sxs-lookup"><span data-stu-id="b45c0-161">Configuration Type Option = Environment Variable</span></span>  
 <span data-ttu-id="b45c0-162">**환경 변수**</span><span class="sxs-lookup"><span data-stu-id="b45c0-162">**Environment variable**</span></span>  
 <span data-ttu-id="b45c0-163">구성 정보를 포함하는 환경 변수를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b45c0-163">Select the environment variable that contains the configuration information.</span></span>  
  
#### <a name="configuration-type-option--registry-entry"></a><span data-ttu-id="b45c0-164">구성 유형 옵션 = 레지스트리 항목</span><span class="sxs-lookup"><span data-stu-id="b45c0-164">Configuration Type Option = Registry Entry</span></span>  
 <span data-ttu-id="b45c0-165">**구성 설정을 직접 지정**</span><span class="sxs-lookup"><span data-stu-id="b45c0-165">**Specify configuration settings directly**</span></span>  
 <span data-ttu-id="b45c0-166">설정을 직접 지정하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="b45c0-166">Use to specify settings directly.</span></span>  
  
|<span data-ttu-id="b45c0-167">값</span><span class="sxs-lookup"><span data-stu-id="b45c0-167">Value</span></span>|<span data-ttu-id="b45c0-168">Description</span><span class="sxs-lookup"><span data-stu-id="b45c0-168">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b45c0-169">**레지스트리 항목**</span><span class="sxs-lookup"><span data-stu-id="b45c0-169">**Registry entry**</span></span>|<span data-ttu-id="b45c0-170">구성 정보를 포함하는 레지스트리 키를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="b45c0-170">Type the Registry key that contains the configuration information.</span></span> <span data-ttu-id="b45c0-171">형식은 \<registry key>입니다.</span><span class="sxs-lookup"><span data-stu-id="b45c0-171">The format is \<registry key>.</span></span><br /><br /> <span data-ttu-id="b45c0-172">레지스트리 키가 HKEY_CURRENT_USER에 이미 있어야 하고 Value라고 지정된 값을 가져야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b45c0-172">The Registry key must already exist in HKEY_CURRENT_USER and have a value named Value.</span></span> <span data-ttu-id="b45c0-173">값은 DWORD 또는 문자열이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b45c0-173">The value can be a DWORD or a string.</span></span><br /><br /> <span data-ttu-id="b45c0-174">HKEY_CURRENT_USER의 루트에 없는 레지스트리 키를 사용하려면 \<Registry key\registry key\\...> 형식을 사용하여 키를 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="b45c0-174">If you want to use a Registry key is not at the root of HKEY_CURRENT_USER, use the format \<Registry key\registry key\\...> to identify the key.</span></span>|  
  
 <span data-ttu-id="b45c0-175">**구성 위치가 환경 변수에 저장됨**</span><span class="sxs-lookup"><span data-stu-id="b45c0-175">**Configuration location is stored in an environment variable**</span></span>  
 <span data-ttu-id="b45c0-176">구성이 저장되는 환경 변수를 지정하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="b45c0-176">Use to specify the environment variable to store the configuration in.</span></span>  
  
|<span data-ttu-id="b45c0-177">값</span><span class="sxs-lookup"><span data-stu-id="b45c0-177">Value</span></span>|<span data-ttu-id="b45c0-178">Description</span><span class="sxs-lookup"><span data-stu-id="b45c0-178">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b45c0-179">**환경 변수**</span><span class="sxs-lookup"><span data-stu-id="b45c0-179">**Environment variable**</span></span>|<span data-ttu-id="b45c0-180">목록에서 환경 변수를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b45c0-180">Select an environment variable from the list.</span></span>|  
  
#### <a name="configuration-type-option--parent-package-variable"></a><span data-ttu-id="b45c0-181">구성 유형 옵션 = 부모 패키지 변수</span><span class="sxs-lookup"><span data-stu-id="b45c0-181">Configuration Type Option = Parent Package Variable</span></span>  
 <span data-ttu-id="b45c0-182">**구성 설정을 직접 지정**</span><span class="sxs-lookup"><span data-stu-id="b45c0-182">**Specify configuration settings directly**</span></span>  
 <span data-ttu-id="b45c0-183">설정을 직접 지정하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="b45c0-183">Use to specify settings directly.</span></span>  
  
|<span data-ttu-id="b45c0-184">값</span><span class="sxs-lookup"><span data-stu-id="b45c0-184">Value</span></span>|<span data-ttu-id="b45c0-185">Description</span><span class="sxs-lookup"><span data-stu-id="b45c0-185">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b45c0-186">**부모 변수**</span><span class="sxs-lookup"><span data-stu-id="b45c0-186">**Parent variable**</span></span>|<span data-ttu-id="b45c0-187">구성 정보를 포함하는 부모 패키지의 변수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b45c0-187">Specify the variable in the parent package that contains the configuration information.</span></span>|  
  
 <span data-ttu-id="b45c0-188">**구성 위치가 환경 변수에 저장됨**</span><span class="sxs-lookup"><span data-stu-id="b45c0-188">**Configuration location is stored in an environment variable**</span></span>  
 <span data-ttu-id="b45c0-189">구성이 저장되는 환경 변수를 지정하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="b45c0-189">Use to specify the environment variable that stores the configuration.</span></span>  
  
|<span data-ttu-id="b45c0-190">값</span><span class="sxs-lookup"><span data-stu-id="b45c0-190">Value</span></span>|<span data-ttu-id="b45c0-191">Description</span><span class="sxs-lookup"><span data-stu-id="b45c0-191">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b45c0-192">**환경 변수**</span><span class="sxs-lookup"><span data-stu-id="b45c0-192">**Environment variable**</span></span>|<span data-ttu-id="b45c0-193">목록에서 환경 변수를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b45c0-193">Select an environment variable from the list.</span></span>|  
  
#### <a name="configuration-type-options--sql-server"></a><span data-ttu-id="b45c0-194">구성 유형 옵션 = SQL Server</span><span class="sxs-lookup"><span data-stu-id="b45c0-194">Configuration Type Options = SQL Server</span></span>  
 <span data-ttu-id="b45c0-195">**구성 설정을 직접 지정**</span><span class="sxs-lookup"><span data-stu-id="b45c0-195">**Specify configuration settings directly**</span></span>  
 <span data-ttu-id="b45c0-196">설정을 직접 지정하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="b45c0-196">Use to specify settings directly.</span></span>  
  
|<span data-ttu-id="b45c0-197">값</span><span class="sxs-lookup"><span data-stu-id="b45c0-197">Value</span></span>|<span data-ttu-id="b45c0-198">Description</span><span class="sxs-lookup"><span data-stu-id="b45c0-198">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b45c0-199">**연결**</span><span class="sxs-lookup"><span data-stu-id="b45c0-199">**Connection**</span></span>|<span data-ttu-id="b45c0-200">목록에서 연결을 선택하거나 **새로 만들기** 를 클릭하여 새 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b45c0-200">Select a connection from the list, or click **New** to create a new connection.</span></span>|  
|<span data-ttu-id="b45c0-201">**구성 테이블**</span><span class="sxs-lookup"><span data-stu-id="b45c0-201">**Configuration table**</span></span>|<span data-ttu-id="b45c0-202">기존 테이블을 선택하거나 **새로 만들기** 를 클릭하여 새 테이블을 만드는 SQL 문을 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="b45c0-202">Select an existing table, or click **New** to write a SQL statement that creates a new table.</span></span>|  
|<span data-ttu-id="b45c0-203">**구성 필터**</span><span class="sxs-lookup"><span data-stu-id="b45c0-203">**Configuration filter**</span></span>|<span data-ttu-id="b45c0-204">기존 구성 이름을 선택하거나 새 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="b45c0-204">Select an existing configuration name or type a new name.</span></span><br /><br /> <span data-ttu-id="b45c0-205">같은 테이블에 여러 SQL Server 구성을 저장할 수 있으며 각 구성은 여러 구성 항목을 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b45c0-205">Many SQL Server configurations can be stored in the same table, and each configuration can include multiple configuration items.</span></span><br /><br /> <span data-ttu-id="b45c0-206">이 사용자 정의 값은 특정 구성에 속하는 구성 항목을 식별하기 위해 테이블에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="b45c0-206">This user-defined value is stored in the table to identify configuration items that belong to a particular configuration</span></span>|  
  
 <span data-ttu-id="b45c0-207">**구성 위치가 환경 변수에 저장됨**</span><span class="sxs-lookup"><span data-stu-id="b45c0-207">**Configuration location is stored in an environment variable**</span></span>  
 <span data-ttu-id="b45c0-208">구성이 저장되는 환경 변수를 지정하는 데 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b45c0-208">Use to specify the environment variable where the configuration is stored.</span></span>  
  
|<span data-ttu-id="b45c0-209">값</span><span class="sxs-lookup"><span data-stu-id="b45c0-209">Value</span></span>|<span data-ttu-id="b45c0-210">Description</span><span class="sxs-lookup"><span data-stu-id="b45c0-210">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b45c0-211">**환경 변수**</span><span class="sxs-lookup"><span data-stu-id="b45c0-211">**Environment variable**</span></span>|<span data-ttu-id="b45c0-212">목록에서 환경 변수를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b45c0-212">Select an environment variable from the list.</span></span>|  
  
## <a name="select-objects-to-export-page"></a><span data-ttu-id="b45c0-213">내보낼 개체 선택 페이지</span><span class="sxs-lookup"><span data-stu-id="b45c0-213">Select Objects to Export Page</span></span>  
 <span data-ttu-id="b45c0-214">**대상 속성 선택 또는 내보낼 속성 선택** 페이지를 사용하여 구성에 포함할 개체 속성을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b45c0-214">Use the **Select Target Property or Select Properties to Export** page to specify the object properties that the configuration contains.</span></span> <span data-ttu-id="b45c0-215">여러 속성을 선택하는 기능은 XML 구성 유형을 선택하는 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b45c0-215">The ability to select multiple properties is available only if you select the XML configuration type.</span></span>  
  
### <a name="options"></a><span data-ttu-id="b45c0-216">옵션</span><span class="sxs-lookup"><span data-stu-id="b45c0-216">Options</span></span>  
 <span data-ttu-id="b45c0-217">**개체**</span><span class="sxs-lookup"><span data-stu-id="b45c0-217">**Objects**</span></span>  
 <span data-ttu-id="b45c0-218">패키지 계층을 확장하고 내보낼 속성을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b45c0-218">Expand the package hierarchy and select the properties to export.</span></span>  
  
 <span data-ttu-id="b45c0-219">**속성 특성**</span><span class="sxs-lookup"><span data-stu-id="b45c0-219">**Property attributes**</span></span>  
 <span data-ttu-id="b45c0-220">속성의 특성을 봅니다.</span><span class="sxs-lookup"><span data-stu-id="b45c0-220">View the attributes of a property.</span></span>  
  
 <span data-ttu-id="b45c0-221">**다음**</span><span class="sxs-lookup"><span data-stu-id="b45c0-221">**Next**</span></span>  
 <span data-ttu-id="b45c0-222">마법사의 다음 페이지로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="b45c0-222">Go to the next page in the wizard.</span></span>  
  
## <a name="completing-the-wizard-page"></a><span data-ttu-id="b45c0-223">마법사 완료 페이지</span><span class="sxs-lookup"><span data-stu-id="b45c0-223">Completing the Wizard Page</span></span>  
 <span data-ttu-id="b45c0-224">**마법사 완료** 페이지를 사용하여 구성의 이름을 지정하고 마법사에서 구성을 만드는 데 사용하는 설정을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b45c0-224">Use the **Completing the Wizard** page to provide a name for the configuration and view settings used by the wizard to create the configuration.</span></span> <span data-ttu-id="b45c0-225">마법사를 완료하면 패키지의 모든 구성을 나열하는 **패키지 구성 도우미** 가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b45c0-225">After the wizard completes, the **Package Configurations Organizer** is displayed, which lists all configurations for the package.</span></span>  
  
### <a name="options"></a><span data-ttu-id="b45c0-226">옵션</span><span class="sxs-lookup"><span data-stu-id="b45c0-226">Options</span></span>  
 <span data-ttu-id="b45c0-227">**구성 이름**</span><span class="sxs-lookup"><span data-stu-id="b45c0-227">**Configuration name**</span></span>  
 <span data-ttu-id="b45c0-228">구성의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="b45c0-228">Type the name of the configuration.</span></span>  
  
 <span data-ttu-id="b45c0-229">**미리 보기**</span><span class="sxs-lookup"><span data-stu-id="b45c0-229">**Preview**</span></span>  
 <span data-ttu-id="b45c0-230">마법사에서 구성을 만드는 데 사용하는 설정을 봅니다.</span><span class="sxs-lookup"><span data-stu-id="b45c0-230">View the settings used by the wizard to create the configuration.</span></span>  
  
 <span data-ttu-id="b45c0-231">**마침**</span><span class="sxs-lookup"><span data-stu-id="b45c0-231">**Finish**</span></span>  
 <span data-ttu-id="b45c0-232">구성을 만든 다음 **패키지 구성 마법사**를 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="b45c0-232">Create the configuration and exit the **Package Configuration Wizard**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b45c0-233">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b45c0-233">See Also</span></span>  
 [<span data-ttu-id="b45c0-234">패키지 구성 만들기</span><span class="sxs-lookup"><span data-stu-id="b45c0-234">Create Package Configurations</span></span>](../../2014/integration-services/create-package-configurations.md)  
  
  
