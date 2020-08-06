---
title: 패키지 구성 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- package configuration syntax [Integration Services]
- SQL Server Integration Services packages, configurations
- SSIS packages, configurations
- XML [Integration Services]
- Integration Services packages, configurations
- configuration syntax [Integration Services]
- indirect configurations [Integration Services]
- configurations [Integration Services]
- direct configurations [Integration Services]
- packages [Integration Services], configurations
ms.assetid: d20e0311-1fc9-4ddc-a381-6d127cf11b69
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0d22dbfedcf4cf7084e1667586f9774926f3b2a2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661243"
---
# <a name="package-configurations"></a><span data-ttu-id="bfea0-102">패키지 구성</span><span class="sxs-lookup"><span data-stu-id="bfea0-102">Package Configurations</span></span>
  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="bfea0-103">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]에서는 런타임에 속성 값을 업데이트하는 데 사용할 수 있는 패키지 구성을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="bfea0-103">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] provides package configurations that you can use to update the values of properties at run time.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="bfea0-104">구성은 패키지 배포 모델에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bfea0-104">Configurations are available for the package deployment model.</span></span> <span data-ttu-id="bfea0-105">매개 변수는 프로젝트 배포 모델에 대한 구성 대신 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="bfea0-105">Parameters are used in place of configurations for the project deployment model.</span></span> <span data-ttu-id="bfea0-106">프로젝트 배포 모델을 사용하면 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 프로젝트를 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 서버에 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bfea0-106">The project deployment model enables you to deploy [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] projects to the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] server.</span></span> <span data-ttu-id="bfea0-107">배포 모델에 대한 자세한 내용은 [Deployment of Projects and Packages](packages/deploy-integration-services-ssis-projects-and-packages.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="bfea0-107">For more information about the deployment models, see [Deployment of Projects and Packages](packages/deploy-integration-services-ssis-projects-and-packages.md).</span></span>  
  
 <span data-ttu-id="bfea0-108">구성은 완성된 패키지에 추가하는 속성/값 쌍입니다.</span><span class="sxs-lookup"><span data-stu-id="bfea0-108">A configuration is a property/value pair that you add to a completed package.</span></span> <span data-ttu-id="bfea0-109">일반적으로 패키지 개발 과정에서 패키지 개체의 패키지 집합 속성을 만든 다음 해당 패키지에 구성을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="bfea0-109">Typically, you create a package set properties on the package objects during package development, and then add the configuration to the package.</span></span> <span data-ttu-id="bfea0-110">패키지가 실행될 때는 구성의 새 속성 값이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="bfea0-110">When the package runs, it gets the new values of the property from the configuration.</span></span> <span data-ttu-id="bfea0-111">예를 들어 구성을 사용하여 연결 관리자의 연결 문자열을 변경하거나 변수 값을 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bfea0-111">For example, by using a configuration, you can change the connection string of a connection manager, or update the value of a variable.</span></span>  
  
 <span data-ttu-id="bfea0-112">패키지 구성을 사용하면 다음과 같은 이점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bfea0-112">Package configurations provide the following benefits:</span></span>  
  
-   <span data-ttu-id="bfea0-113">구성을 사용하면 개발 환경에서 프로덕션 환경으로 패키지를 쉽게 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bfea0-113">Configurations make it easier to move packages from a development environment to a production environment.</span></span> <span data-ttu-id="bfea0-114">예를 들어 구성으로 원본 파일의 경로를 업데이트하거나 데이터베이스 또는 서버의 이름을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bfea0-114">For example, a configuration can update the path of a source file, or change the name of a database or server.</span></span>  
  
-   <span data-ttu-id="bfea0-115">구성은 패키지를 여러 다른 서버로 배포할 때 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="bfea0-115">Configurations are useful when you deploy packages to many different servers.</span></span> <span data-ttu-id="bfea0-116">예를 들어 배포된 각 패키지 구성의 변수가 다른 디스크 공간 값을 포함할 수 있으며 사용 가능한 디스크 공간이 이 값을 충족하지 않을 경우 패키지가 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bfea0-116">For example, a variable in the configuration for each deployed package can contain a different disk space value, and if the available disk space does not meet this value, the package does not run.</span></span>  
  
-   <span data-ttu-id="bfea0-117">구성은 패키지를 좀 더 융통성 있게 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="bfea0-117">Configurations make packages more flexible.</span></span> <span data-ttu-id="bfea0-118">예를 들어 구성으로 속성 식에서 사용되는 변수의 값을 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bfea0-118">For example, a configuration can update the value of a variable that is used in a property expression.</span></span>  
  
 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="bfea0-119">에서는 XML 파일, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 데이터베이스 테이블, 환경 변수 및 패키지 변수와 같은 여러 가지 패키지 구성 저장 방식을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="bfea0-119">supports several different methods of storing package configurations, such as XML files, tables in a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] database, and environment and package variables.</span></span>  
  
 <span data-ttu-id="bfea0-120">각 구성은 한 개의 속성/값 쌍입니다.</span><span class="sxs-lookup"><span data-stu-id="bfea0-120">Each configuration is a property/value pair.</span></span> <span data-ttu-id="bfea0-121">XML 구성 파일 및 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 구성 유형은 여러 구성을 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bfea0-121">The XML configuration file and [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] configuration types can include multiple configurations.</span></span>  
  
 <span data-ttu-id="bfea0-122">패키지 설치를 위한 패키지 배포 유틸리티를 만드는 경우 구성이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="bfea0-122">The configurations are included when you create a package deployment utility for installing packages.</span></span> <span data-ttu-id="bfea0-123">패키지를 설치하는 경우 패키지 설치 단계의 하나로 구성이 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="bfea0-123">When you install the packages, the configurations can be updated as a step in the package installation.</span></span>  
  
## <a name="understanding-how-package-configurations-are-applied-at-run-time"></a><span data-ttu-id="bfea0-124">런타임에 패키지 구성이 적용되는 방법 이해</span><span class="sxs-lookup"><span data-stu-id="bfea0-124">Understanding How Package Configurations Are Applied at Run Time</span></span>  
 <span data-ttu-id="bfea0-125">**dtexec** 명령 프롬프트 유틸리티(dtexec.exe)를 사용하여 배포된 패키지를 실행할 때 유틸리티에서는 패키지 구성을 두 번 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="bfea0-125">When you use the **dtexec** command prompt utility (dtexec.exe) to run a deployed package, the utility applies package configurations twice.</span></span> <span data-ttu-id="bfea0-126">즉, 명령줄에서 지정한 옵션을 적용하기 전과 후 모두에 구성을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="bfea0-126">The utility applies configurations both before and after it applies the options that you specified on command line.</span></span>  
  
 <span data-ttu-id="bfea0-127">유틸리티에서 패키지를 로드 및 실행할 때 이벤트가 다음과 같은 순서로 발생됩니다.</span><span class="sxs-lookup"><span data-stu-id="bfea0-127">As the utility loads and runs the package, events occur in the following order:</span></span>  
  
1.  <span data-ttu-id="bfea0-128">**dtexec** 유틸리티가 패키지를 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="bfea0-128">The **dtexec** utility loads the package.</span></span>  
  
2.  <span data-ttu-id="bfea0-129">유틸리티가 패키지에서 디자인 타임에 지정한 구성을 패키지에 지정된 순서로 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="bfea0-129">The utility applies the configurations that were specified in the package at design time and in the order that is specified in the package.</span></span> <span data-ttu-id="bfea0-130">부모 패키지 변수 구성만은 예외적으로</span><span class="sxs-lookup"><span data-stu-id="bfea0-130">(The one exception to this is the Parent Package Variables configurations.</span></span> <span data-ttu-id="bfea0-131">프로세스의 후반에 한 번만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="bfea0-131">The utility applies these configurations only once and later in the process.)</span></span>  
  
3.  <span data-ttu-id="bfea0-132">그런 다음 명령줄에서 지정한 옵션을 유틸리티가 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="bfea0-132">The utility then applies any options that you specified on the command line.</span></span>  
  
4.  <span data-ttu-id="bfea0-133">그런 다음 유틸리티가 패키지에서 디자인 타임에 지정한 구성을 패키지에 지정된 순서로 다시 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="bfea0-133">The utility then reloads the configurations that were specified in the package at design time and in the order specified in the package.</span></span> <span data-ttu-id="bfea0-134">마찬가지로 부모 패키지 변수 구성만은 예외적으로 이 규칙을 따르지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bfea0-134">(Again, the exception to this rule is the Parent Package Variables configurations).</span></span> <span data-ttu-id="bfea0-135">유틸리티는 명령줄에서 지정한 명령줄 옵션을 사용하여 구성을 다시 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="bfea0-135">The utility uses any command-line options that were specified to reload the configurations.</span></span> <span data-ttu-id="bfea0-136">따라서 다른 위치에서 다른 값이 다시 로드될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bfea0-136">Therefore, different values might be reloaded from a different location.</span></span>  
  
5.  <span data-ttu-id="bfea0-137">유틸리티가 부모 패키지 변수 구성을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="bfea0-137">The utility applies the Parent Package Variable configurations.</span></span>  
  
6.  <span data-ttu-id="bfea0-138">유틸리티가 패키지를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="bfea0-138">The utility runs the package.</span></span>  
  
 <span data-ttu-id="bfea0-139">**dtexec** 유틸리티가 구성을 적용하는 방법은 다음과 같은 명령줄 옵션에 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="bfea0-139">The way in which the **dtexec** utility applies configurations affects the following command-line options:</span></span>  
  
-   <span data-ttu-id="bfea0-140">런타임에 **/Connection** 또는 **/Set** 옵션을 사용하면 디자인 타임에 지정한 위치와 다른 위치에서 패키지 구성을 로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bfea0-140">You can use the **/Connection** or **/Set** option at run time to load package configurations from a location other than the location that you specified at design time.</span></span>  
  
-   <span data-ttu-id="bfea0-141">**/ConfigFile** 옵션을 사용하면 디자인 타임에 지정하지 않은 추가 구성을 로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bfea0-141">You can use the **/ConfigFile** option to load additional configurations that you did not specify at design time.</span></span>  
  
 <span data-ttu-id="bfea0-142">그러나 이러한 명령줄 옵션에는 몇 가지 제한 사항이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bfea0-142">However, these command-line options do have some restrictions:</span></span>  
  
-   <span data-ttu-id="bfea0-143">**/Set** 또는 **/Connection** 옵션을 사용하여 구성에서도 설정된 단일 값을 재정의할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="bfea0-143">You cannot use the **/Set** or the **/Connection** option to override single values that are also set by a configuration.</span></span>  
  
-   <span data-ttu-id="bfea0-144">**/ConfigFile** 옵션을 사용하여 디자인 타임에 지정한 구성을 대체하는 구성을 로드할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="bfea0-144">You cannot use the **/ConfigFile** option to load configurations that replace the configurations that you specified at design time.</span></span>  
  
 <span data-ttu-id="bfea0-145">이러한 옵션에 대 한 자세한 내용과 이러한 옵션의 동작이 및 이전 버전 간에 어떻게 다른 지에 대 한 자세한 내용은 [!INCLUDE[ssISCurrent](../includes/ssiscurrent-md.md)] [SQL Server 2014의 Integration Services 기능에 대 한 동작 변경 내용](../../2014/integration-services/behavior-changes-to-integration-services-features-in-sql-server-2014.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="bfea0-145">For more information about these options, and how the behavior of these options differs between [!INCLUDE[ssISCurrent](../includes/ssiscurrent-md.md)] and earlier versions, see [Behavior Changes to Integration Services Features in SQL Server 2014](../../2014/integration-services/behavior-changes-to-integration-services-features-in-sql-server-2014.md).</span></span>  
  
## <a name="package-configuration-types"></a><span data-ttu-id="bfea0-146">패키지 구성 유형</span><span class="sxs-lookup"><span data-stu-id="bfea0-146">Package Configuration Types</span></span>  
 <span data-ttu-id="bfea0-147">다음 표에서는 패키지 구성 유형에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="bfea0-147">The following table describes the package configuration types.</span></span>  
  
|<span data-ttu-id="bfea0-148">Type</span><span class="sxs-lookup"><span data-stu-id="bfea0-148">Type</span></span>|<span data-ttu-id="bfea0-149">Description</span><span class="sxs-lookup"><span data-stu-id="bfea0-149">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="bfea0-150">XML 구성 파일</span><span class="sxs-lookup"><span data-stu-id="bfea0-150">XML configuration file</span></span>|<span data-ttu-id="bfea0-151">구성을 포함하는 XML 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="bfea0-151">An XML file contains the configurations.</span></span> <span data-ttu-id="bfea0-152">XML 파일은 여러 구성을 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bfea0-152">The XML file can include multiple configurations.</span></span>|  
|<span data-ttu-id="bfea0-153">환경 변수</span><span class="sxs-lookup"><span data-stu-id="bfea0-153">Environment variable</span></span>|<span data-ttu-id="bfea0-154">환경 변수는 구성을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="bfea0-154">An environment variable contains the configuration.</span></span>|  
|<span data-ttu-id="bfea0-155">레지스트리 항목</span><span class="sxs-lookup"><span data-stu-id="bfea0-155">Registry entry</span></span>|<span data-ttu-id="bfea0-156">레지스트리 항목은 구성을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="bfea0-156">A Registry entry contains the configuration.</span></span>|  
|<span data-ttu-id="bfea0-157">부모 패키지 변수</span><span class="sxs-lookup"><span data-stu-id="bfea0-157">Parent package variable</span></span>|<span data-ttu-id="bfea0-158">패키지 변수는 구성을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="bfea0-158">A variable in the package contains the configuration.</span></span> <span data-ttu-id="bfea0-159">이 구성 유형은 일반적으로 자식 패키지에서 속성을 업데이트하기 위해 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="bfea0-159">This configuration type is typically used to update properties in child packages.</span></span>|  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="bfea0-160">테이블</span><span class="sxs-lookup"><span data-stu-id="bfea0-160">table</span></span>|<span data-ttu-id="bfea0-161">구성을 포함하는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 데이터베이스의 테이블입니다.</span><span class="sxs-lookup"><span data-stu-id="bfea0-161">A table in a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] database contains the configuration.</span></span> <span data-ttu-id="bfea0-162">테이블은 여러 구성을 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bfea0-162">The table can include multiple configurations.</span></span>|  
  
### <a name="xml-configuration-files"></a><span data-ttu-id="bfea0-163">XML 구성 파일</span><span class="sxs-lookup"><span data-stu-id="bfea0-163">XML Configuration Files</span></span>  
 <span data-ttu-id="bfea0-164">**XML 구성 파일** 의 구성 유형을 선택한 경우 새 구성 파일을 만들고 기존의 파일을 다시 사용하면서 새 구성을 추가하거나 또는 기존의 파일을 다시 사용하지만 기존의 파일 내용을 덮어쓸 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bfea0-164">If you select the **XML configuration file** configuration type, you can create a new configuration file, reuse an existing file and add new configurations, or reuse an existing file but overwrite existing file content.</span></span>  
  
 <span data-ttu-id="bfea0-165">XML 구성 파일은 두 개의 부분으로 이루어집니다.</span><span class="sxs-lookup"><span data-stu-id="bfea0-165">An XML configuration file includes two sections:</span></span>  
  
-   <span data-ttu-id="bfea0-166">제목은 구성 파일 자체에 대한 정보를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="bfea0-166">A heading that contains information about the configuration file.</span></span> <span data-ttu-id="bfea0-167">이 요소는 파일을 만든 시각과 같은 특성 및 파일을 만든 사람의 이름을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="bfea0-167">This element includes attributes such as when the file was created and the name of the person who generated the file.</span></span>  
  
-   <span data-ttu-id="bfea0-168">구성 요소는 각 구성에 대한 정보를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="bfea0-168">Configuration elements that contain information about each configuration.</span></span> <span data-ttu-id="bfea0-169">이 요소는 속성 경로 및 속성의 구성 값과 같은 특성을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="bfea0-169">This element includes attributes such as the property path and the configured value of a property.</span></span>  
  
 <span data-ttu-id="bfea0-170">다음 XML 코드에서는 XML 구성 파일의 구문을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="bfea0-170">The following XML code demonstrates the syntax of an XML configuration file.</span></span> <span data-ttu-id="bfea0-171">이 예에서는 `MyVar`라는 정수 변수의 Value 속성에 대한 구성을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="bfea0-171">This example shows a configuration for the Value property of an integer variable named `MyVar`.</span></span>  
  
```  
<?xml version="1.0"?>  
<DTSConfiguration>  
   <DTSConfigurationHeading>  
      <DTSConfigurationFileInfo  
          GeneratedBy="DomainName\UserName"  
          GeneratedFromPackageName="Package"  
          GeneratedFromPackageID="{2AF06766-817A-4E28-9878-0DE37A150648}"  
          GeneratedDate="2/01/2005 5:58:09 PM"/>  
   </DTSConfigurationHeading>  
   <Configuration ConfiguredType="Property" Path="\Package.Variables[User::MyVar].Value" ValueType="Int32">  
      <ConfiguredValue>0</ConfiguredValue>  
   </Configuration>  
</DTSConfiguration>  
  
```  
  
### <a name="registry-entry"></a><span data-ttu-id="bfea0-172">레지스트리 항목</span><span class="sxs-lookup"><span data-stu-id="bfea0-172">Registry Entry</span></span>  
 <span data-ttu-id="bfea0-173">레지스트리 항목을 사용하여 구성을 저장하려면 기존 키를 사용하거나 HKEY_CURRENT_USER에서 새 키를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bfea0-173">If you want to use a Registry entry to store the configuration, you can either use an existing key or create a new key in HKEY_CURRENT_USER.</span></span> <span data-ttu-id="bfea0-174">`Value` 값이 있는 레지스트리 키를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bfea0-174">The Registry key that you use must have a value named `Value`.</span></span> <span data-ttu-id="bfea0-175">값은 DWORD 또는 문자열이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bfea0-175">The value can be a DWORD or a string.</span></span>  
  
 <span data-ttu-id="bfea0-176">**레지스트리 항목** 구성 유형을 선택할 경우 레지스트리 항목 상자에 레지스트리 키의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="bfea0-176">If you select the **Registry entry** configuration type, you type the name of the Registry key in the Registry entry box.</span></span> <span data-ttu-id="bfea0-177">형식은 \<registry key>입니다.</span><span class="sxs-lookup"><span data-stu-id="bfea0-177">The format is \<registry key>.</span></span> <span data-ttu-id="bfea0-178">HKEY_CURRENT_USER의 루트에 없는 레지스트리 키를 사용하려면 \<Registry key\registry key\\...> 형식을 사용하여 키를 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="bfea0-178">If you want to use a Registry key that is not at the root of HKEY_CURRENT_USER, use the format \<Registry key\registry key\\...> to identify the key.</span></span> <span data-ttu-id="bfea0-179">예를 들어 SSISPackages에 있는 MyPackage 키를 사용하려면 `SSISPackages\MyPackage`를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="bfea0-179">For example, to use the MyPackage key located in SSISPackages, type `SSISPackages\MyPackage`.</span></span>  
  
### <a name="sql-server"></a><span data-ttu-id="bfea0-180">SQL Server</span><span class="sxs-lookup"><span data-stu-id="bfea0-180">SQL Server</span></span>  
 <span data-ttu-id="bfea0-181">**SQL Server** 구성 유형을 선택한 경우 구성을 저장할 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 데이터베이스에 대한 연결을 지정하십시오.</span><span class="sxs-lookup"><span data-stu-id="bfea0-181">If you select the **SQL Server** configuration type, you specify the connection to the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] database in which you want to store the configurations.</span></span> <span data-ttu-id="bfea0-182">기존 테이블에 구성을 저장하거나 지정한 데이터베이스에 새 테이블을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bfea0-182">You can save the configurations to an existing table or create a new table in the specified database.</span></span>  
  
 <span data-ttu-id="bfea0-183">다음 SQL 문에서는 패키지 구성 마법사가 제공하는 기본 CREATE TABLE 문을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="bfea0-183">The following SQL statement shows the default CREATE TABLE statement that the Package Configuration Wizard provides.</span></span>  
  
```  
CREATE TABLE [dbo].[SSIS Configurations]  
(  
ConfigurationFilter NVARCHAR(255) NOT NULL,  
ConfiguredValue NVARCHAR(255) NULL,  
PackagePath NVARCHAR(255) NOT NULL,  
ConfiguredValueType NVARCHAR(20) NOT NULL  
)  
  
```  
  
 <span data-ttu-id="bfea0-184">구성에 지정한 이름은 **ConfigurationFilter** 열에 저장된 값입니다.</span><span class="sxs-lookup"><span data-stu-id="bfea0-184">The name that you provide for the configuration is the value stored in the **ConfigurationFilter** column.</span></span>  
  
## <a name="direct-and-indirect-configurations"></a><span data-ttu-id="bfea0-185">직접 및 간접 구성</span><span class="sxs-lookup"><span data-stu-id="bfea0-185">Direct and Indirect Configurations</span></span>  
 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="bfea0-186">는 직접 및 간접 구성을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="bfea0-186">provides direct and indirect configurations.</span></span> <span data-ttu-id="bfea0-187">구성을 직접으로 지정한 경우 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 는 구성 항목 및 패키지 개체 속성 간에 직접 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="bfea0-187">If you specify configurations directly, [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] creates a direct link between the configuration item and the package object property.</span></span> <span data-ttu-id="bfea0-188">직접 구성은 원본의 위치가 변경되지 않는 경우에 적합합니다.</span><span class="sxs-lookup"><span data-stu-id="bfea0-188">Direct configurations are a better choice when the location of the source does not change.</span></span> <span data-ttu-id="bfea0-189">예를 들어 패키지의 모든 배포가 동일한 파일 경로를 사용하는 경우 XML 구성 파일을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bfea0-189">For example, if you are sure that all deployments in the package use the same file path, you can specify an XML configuration file.</span></span>  
  
 <span data-ttu-id="bfea0-190">간접 구성은 환경 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="bfea0-190">Indirect configurations use environment variables.</span></span> <span data-ttu-id="bfea0-191">구성 설정을 직접 지정하는 대신 구성이 구성 값을 포함하는 환경 변수를 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="bfea0-191">Instead of specifying the configuration setting directly, the configuration points to an environment variable, which in turn contains the configuration value.</span></span> <span data-ttu-id="bfea0-192">간접 구성은 각 패키지의 배포에 대해 구성 위치가 변경될 수 있는 경우에 적합합니다.</span><span class="sxs-lookup"><span data-stu-id="bfea0-192">Using indirect configurations is a better choice when the location of the configuration can change for each deployment of a package.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="bfea0-193">관련 작업</span><span class="sxs-lookup"><span data-stu-id="bfea0-193">Related Tasks</span></span>  
 [<span data-ttu-id="bfea0-194">패키지 구성 만들기</span><span class="sxs-lookup"><span data-stu-id="bfea0-194">Create Package Configurations</span></span>](../../2014/integration-services/create-package-configurations.md)  
  
## <a name="related-content"></a><span data-ttu-id="bfea0-195">관련 내용</span><span class="sxs-lookup"><span data-stu-id="bfea0-195">Related Content</span></span>  
  
-   <span data-ttu-id="bfea0-196">msdn.microsoft.com의 기술 문서 - [Integration Services 패키지 구성 이해](https://go.microsoft.com/fwlink/?LinkId=165643)</span><span class="sxs-lookup"><span data-stu-id="bfea0-196">Technical article, [Understanding Integration Services Package Configurations](https://go.microsoft.com/fwlink/?LinkId=165643), on msdn.microsoft.com</span></span>  
  
-   <span data-ttu-id="bfea0-197">Www.sqlis.com의 블로그 항목 [-코드 패키지 구성에서 패키지 만들기](https://go.microsoft.com/fwlink/?LinkId=217663).</span><span class="sxs-lookup"><span data-stu-id="bfea0-197">Blog entry, [Creating packages in code - Package Configurations](https://go.microsoft.com/fwlink/?LinkId=217663), on www.sqlis.com.</span></span>  
  
-   <span data-ttu-id="bfea0-198">블로그 항목 [-API 샘플-blogs.msdn.com에서 프로그래밍 방식으로 패키지에 구성 파일을 추가](https://go.microsoft.com/fwlink/?LinkId=217664)합니다.</span><span class="sxs-lookup"><span data-stu-id="bfea0-198">Blog entry, [API Sample - Programmatically add a configuration file to a package](https://go.microsoft.com/fwlink/?LinkId=217664), on blogs.msdn.com.</span></span>  
  
  
