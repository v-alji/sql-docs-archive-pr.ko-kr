---
title: 사용자 지정 개체 빌드, 배포 및 디버깅 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- custom objects [Integration Services]
ms.assetid: b03685bc-5398-4c3f-901a-1219c1098fbe
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 13157fce4e5c7dd8987f4950a6b4250ea0e36094
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736597"
---
# <a name="building-deploying-and-debugging-custom-objects"></a><span data-ttu-id="e0c5b-102">사용자 지정 개체 빌드, 배포 및 디버깅</span><span class="sxs-lookup"><span data-stu-id="e0c5b-102">Building, Deploying, and Debugging Custom Objects</span></span>
  <span data-ttu-id="e0c5b-103">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]의 사용자 지정 개체에 대한 코드를 작성한 후에는 어셈블리를 빌드하여 배포하고 패키지에서 사용할 수 있도록 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너에 통합한 다음 테스트 및 디버깅을 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0c5b-103">After you have written the code for a custom object for [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], you must build the assembly, deploy it, integrate it into [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer to make it available for use in packages, and test and debug it.</span></span>

##  <a name="steps-in-building-deploying-and-debugging-a-custom-object-for-integration-services"></a><a name="top"></a> <span data-ttu-id="e0c5b-104">Integration Services의 사용자 지정 개체 빌드, 배포 및 디버깅 단계</span><span class="sxs-lookup"><span data-stu-id="e0c5b-104">Steps in Building, Deploying, and Debugging a Custom Object for Integration Services</span></span>
 <span data-ttu-id="e0c5b-105">개체의 사용자 지정 기능을 작성한 후에는</span><span class="sxs-lookup"><span data-stu-id="e0c5b-105">You have already written the custom functionality for your object.</span></span> <span data-ttu-id="e0c5b-106">이를 테스트하고 사용자가 사용할 수 있도록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0c5b-106">Now you have to test it and to make it available to users.</span></span> <span data-ttu-id="e0c5b-107">이 단계는 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]용으로 만들 수 있는 모든 유형의 사용자 지정 개체에서 매우 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="e0c5b-107">The steps are very similar for all the types of custom objects that you can create for [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].</span></span>

 <span data-ttu-id="e0c5b-108">사용자 지정 개체를 빌드, 배포 및 디버깅할 때 따라야 하는 단계는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="e0c5b-108">Here are the steps that you follow in building, deploying, and debugging it:</span></span>

1.  <span data-ttu-id="e0c5b-109">생성할 어셈블리를 강력한 이름으로 [서명](#signing)합니다.</span><span class="sxs-lookup"><span data-stu-id="e0c5b-109">[Sign](#signing) the assembly to be generated with a strong name.</span></span>

2.  <span data-ttu-id="e0c5b-110">어셈블리를 [빌드](#building)합니다.</span><span class="sxs-lookup"><span data-stu-id="e0c5b-110">[Build](#building) the assembly.</span></span>

3.  <span data-ttu-id="e0c5b-111">어셈블리를 적절한 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 폴더로 이동하거나 복사하여 [배포](#deploying)합니다.</span><span class="sxs-lookup"><span data-stu-id="e0c5b-111">[Deploy](#deploying) the assembly by moving or copying it to the appropriate [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] folder.</span></span>

4.  <span data-ttu-id="e0c5b-112">GAC(전역 어셈블리 캐시)에 어셈블리를 [설치](#installing)합니다.</span><span class="sxs-lookup"><span data-stu-id="e0c5b-112">[Install](#installing) the assembly in the global assembly cache (GAC).</span></span>

     <span data-ttu-id="e0c5b-113">이 개체는 도구 상자에 자동으로 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="e0c5b-113">The object is automatically added to the Toolbox.</span></span>

5.  <span data-ttu-id="e0c5b-114">필요한 경우 [배포 문제를 해결](#troubleshooting)합니다.</span><span class="sxs-lookup"><span data-stu-id="e0c5b-114">[Troubleshoot](#troubleshooting) the deployment, if necessary.</span></span>

6.  <span data-ttu-id="e0c5b-115">코드를 [테스트](#testing)하고 디버그합니다.</span><span class="sxs-lookup"><span data-stu-id="e0c5b-115">[Test](#testing) and debug your code.</span></span>

##  <a name="signing-the-assembly"></a><a name="signing"></a> <span data-ttu-id="e0c5b-116">어셈블리 서명</span><span class="sxs-lookup"><span data-stu-id="e0c5b-116">Signing the Assembly</span></span>
 <span data-ttu-id="e0c5b-117">공유하려는 어셈블리는 전역 어셈블리 캐시에 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0c5b-117">When an assembly is meant to be shared, it must be installed in the global assembly cache.</span></span> <span data-ttu-id="e0c5b-118">전역 어셈블리 캐시에 추가된 어셈블리는 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]와 같은 애플리케이션에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0c5b-118">After the assembly has been added to the global assembly cache, the assembly can be used by applications such as [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="e0c5b-119">전역 어셈블리 캐시에 어셈블리를 추가하려면 어셈블리를 강력한 이름으로 서명하여 해당 어셈블리가 전역적으로 고유함을 보장해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0c5b-119">A requirement of the global assembly cache is that the assembly must be signed with a strong name, which guarantees that an assembly is globally unique.</span></span> <span data-ttu-id="e0c5b-120">강력한 이름의 어셈블리에는 어셈블리의 이름, culture, 공개 키 및 버전 번호를 포함하는 정규화된 이름이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0c5b-120">A strong-named assembly has a fully qualified name that includes the name, culture, public key, and version number of the assembly.</span></span> <span data-ttu-id="e0c5b-121">런타임에서는 이 정보를 사용하여 어셈블리를 찾고 같은 이름의 다른 어셈블리와 구별합니다.</span><span class="sxs-lookup"><span data-stu-id="e0c5b-121">The runtime uses this information to locate the assembly and to differentiate it from other assemblies with the same name.</span></span>

 <span data-ttu-id="e0c5b-122">강력한 이름으로 어셈블리를 서명하려면 먼저 퍼블릭/프라이빗 키 쌍이 있어야 하며 이 키 쌍이 없으면 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0c5b-122">To sign an assembly with a strong name, you must first have or create a public/private key pair.</span></span> <span data-ttu-id="e0c5b-123">이 퍼블릭 및 프라이빗 암호화 키 쌍은 빌드할 때 강력한 이름의 어셈블리를 만드는 데 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="e0c5b-123">This public and private cryptographic key pair is used at build time to create a strong-named assembly.</span></span>

 <span data-ttu-id="e0c5b-124">강력한 이름과 어셈블리를 서명할 때 따라야 하는 단계에 대한 자세한 내용은 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK 설명서의 다음 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="e0c5b-124">For more information about strong names and on the steps that you must followto sign an assembly, see the following topics in the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK documentation:</span></span>

-   <span data-ttu-id="e0c5b-125">강력한 이름의 어셈블리</span><span class="sxs-lookup"><span data-stu-id="e0c5b-125">Strong-Named Assemblies</span></span>

-   <span data-ttu-id="e0c5b-126">공개/개인 키 쌍 만들기</span><span class="sxs-lookup"><span data-stu-id="e0c5b-126">Creating a Key Pair</span></span>

-   <span data-ttu-id="e0c5b-127">방법: 강력한 이름으로 어셈블리 서명</span><span class="sxs-lookup"><span data-stu-id="e0c5b-127">Signing an Assembly with a Strong Name</span></span>

 <span data-ttu-id="e0c5b-128">[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]에서는 빌드할 때 어셈블리를 강력한 이름으로 서명하기가 쉽습니다.</span><span class="sxs-lookup"><span data-stu-id="e0c5b-128">You can easily sign your assembly with a strong name in [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] at build time.</span></span> <span data-ttu-id="e0c5b-129">**프로젝트 속성** 대화 상자에서 **서명** 탭을 선택 합니다. **어셈블리에 서명** 하는 옵션을 선택한 다음 키 (.snk) 파일의 경로를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0c5b-129">In the **Project Properties** dialog box, select the **Signing** tab. Select the option to **Sign the assembly** and then provide the path of the key (.snk) file.</span></span>

##  <a name="building-the-assembly"></a><a name="building"></a> <span data-ttu-id="e0c5b-130">어셈블리 빌드</span><span class="sxs-lookup"><span data-stu-id="e0c5b-130">Building the Assembly</span></span>
 <span data-ttu-id="e0c5b-131">프로젝트를 서명한 후에는 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]의 **빌드** 메뉴에서 사용할 수 있는 명령을 사용하여 프로젝트 또는 솔루션을 빌드하거나 다시 빌드해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0c5b-131">After signing the project, you must build or rebuild the project or the solution by using the commands available on the **Build** menu of [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)].</span></span> <span data-ttu-id="e0c5b-132">솔루션에 사용자 지정 사용자 인터페이스를 위한 별도의 프로젝트가 포함된 경우 이 프로젝트도 강력한 이름으로 서명해야 하며 이 프로젝트를 솔루션과 동시에 빌드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0c5b-132">Your solution may contain a separate project for a custom user interface, which must also be signed with a strong name, and can be built at the same time.</span></span>

 <span data-ttu-id="e0c5b-133">어셈블리를 배포하고 글로벌 어셈블리 캐시에 설치하는 다음 두 단계를 수행하는 데 가장 편리한 방법은 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]에서 이러한 단계를 빌드 후 이벤트로 스크립팅하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="e0c5b-133">The most convenient method for performing the next two steps-deploying the assembly and installing it in the global assembly cache-is to script these steps as a post-build event in [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].</span></span> <span data-ttu-id="e0c5b-134">빌드 이벤트는 [프로젝트 속성]의 **컴파일** 페이지([!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 프로젝트의 경우) 또는 **빌드 이벤트** 페이지(C# 프로젝트의 경우)에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0c5b-134">Build events are available from the **Compile** page of Project Properties for a [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] project, and from the **Build Events** page for a C# project.</span></span> <span data-ttu-id="e0c5b-135">**gacutil.exe**와 같은 명령 프롬프트 유틸리티에는 전체 경로가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="e0c5b-135">The full path is required for command prompt utilities such as **gacutil.exe**.</span></span> <span data-ttu-id="e0c5b-136">공백이 포함된 경로와 공백이 포함된 경로로 확장되는 $(TargetPath) 등의 매크로는 모두 따옴표로 묶어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0c5b-136">Quotation marks are required both around paths that contain spaces and around macros such as $(TargetPath) that expand to paths that contain spaces.</span></span>

 <span data-ttu-id="e0c5b-137">다음은 사용자 지정 로그 공급자에 대한 빌드 후 이벤트 명령줄의 예입니다.</span><span class="sxs-lookup"><span data-stu-id="e0c5b-137">Here is an example of a post-build event command line for a custom log provider:</span></span>

```
"C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0A\bin\NETFX 4.0 Tools\gacutil.exe" -u $(TargetName)
"C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0A\bin\NETFX 4.0 Tools\gacutil.exe" -i $(TargetFileName)
copy $(TargetFileName) "C:\Program Files\Microsoft SQL Server\120\DTS\LogProviders "
```

##  <a name="deploying-the-assembly"></a><a name="deploying"></a> <span data-ttu-id="e0c5b-138">어셈블리 배포</span><span class="sxs-lookup"><span data-stu-id="e0c5b-138">Deploying the Assembly</span></span>
 <span data-ttu-id="e0c5b-139">[!INCLUDE[ssIS](../../includes/ssis-md.md)]디자이너는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가 설치 될 때 만들어진 일련의 폴더에 있는 파일을 열거 하 여 패키지에서 사용할 수 있는 사용자 지정 개체를 찾습니다 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="e0c5b-139">The [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer locates the custom objects available for use in packages by enumerating the files found in a series of folders that are created when [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] is installed.</span></span> <span data-ttu-id="e0c5b-140">기본 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 설치 설정을 사용 하는 경우이 폴더 집합은 **C:\PROGRAM Files\Microsoft SQL Server\120\DTS**아래에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0c5b-140">When the default [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installation settings are used, this set of folders is located under **C:\Program Files\Microsoft SQL Server\120\DTS**.</span></span> <span data-ttu-id="e0c5b-141">그러나 사용자 지정 개체에 대 한 설치 프로그램을 만드는 경우 **HKEY_LOCAL_MACHINE \SOFTWARE\MICROSOFT\MICROSOFT SQL Server\120\SSIS\Setup\DtsPath** 레지스트리 키의 값을 확인 하 여이 폴더의 위치를 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0c5b-141">However if you create a setup program for your custom object, you should check the value of the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\SSIS\Setup\DtsPath** registry key to verify the location of this folder.</span></span>

 <span data-ttu-id="e0c5b-142">다음과 같은 두 가지 방법으로 폴더에 어셈블리를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0c5b-142">You can put the assembly in the folder in two ways:</span></span>

-   <span data-ttu-id="e0c5b-143">빌드 후 컴파일된 어셈블리를 적절한 폴더로 이동하거나 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="e0c5b-143">Move or copy the compiled assembly to the appropriate folder after building it.</span></span> <span data-ttu-id="e0c5b-144">편의상 빌드 후 이벤트에 복사 명령을 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0c5b-144">(For convenience, you can include the copy command in a Post-build Event.)</span></span>

-   <span data-ttu-id="e0c5b-145">어셈블리를 적절한 폴더에 직접 빌드합니다.</span><span class="sxs-lookup"><span data-stu-id="e0c5b-145">Build the assembly directly in the appropriate folder.</span></span>

 <span data-ttu-id="e0c5b-146">**C:\Program FILES\MICROSOFT SQL Server\120\DTS** 아래에 있는 다음 배포 폴더는 다양 한 유형의 사용자 지정 개체에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e0c5b-146">The following deployment folders under **C:\Program Files\Microsoft SQL Server\120\DTS** are used for the various types of custom objects:</span></span>

|<span data-ttu-id="e0c5b-147">사용자 지정 개체</span><span class="sxs-lookup"><span data-stu-id="e0c5b-147">Custom object</span></span>|<span data-ttu-id="e0c5b-148">배포 폴더</span><span class="sxs-lookup"><span data-stu-id="e0c5b-148">Deployment folder</span></span>|
|-------------------|-----------------------|
|<span data-ttu-id="e0c5b-149">Task</span><span class="sxs-lookup"><span data-stu-id="e0c5b-149">Task</span></span>|<span data-ttu-id="e0c5b-150">작업</span><span class="sxs-lookup"><span data-stu-id="e0c5b-150">Tasks</span></span>|
|<span data-ttu-id="e0c5b-151">ODBC 대상 편집기</span><span class="sxs-lookup"><span data-stu-id="e0c5b-151">Connection manager</span></span>|<span data-ttu-id="e0c5b-152">Connections</span><span class="sxs-lookup"><span data-stu-id="e0c5b-152">Connections</span></span>|
|<span data-ttu-id="e0c5b-153">로그 공급자</span><span class="sxs-lookup"><span data-stu-id="e0c5b-153">Log provider</span></span>|<span data-ttu-id="e0c5b-154">LogProviders</span><span class="sxs-lookup"><span data-stu-id="e0c5b-154">LogProviders</span></span>|
|<span data-ttu-id="e0c5b-155">데이터 흐름 구성 요소</span><span class="sxs-lookup"><span data-stu-id="e0c5b-155">Data flow component</span></span>|<span data-ttu-id="e0c5b-156">PipelineComponents</span><span class="sxs-lookup"><span data-stu-id="e0c5b-156">PipelineComponents</span></span>|

> [!NOTE]
>  <span data-ttu-id="e0c5b-157">이러한 폴더에 복사된 어셈블리는 사용 가능한 태스크, 연결 관리자 등의 열거형을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="e0c5b-157">Assemblies are copied to these folders to support the enumeration of available tasks, connection managers, and so on.</span></span> <span data-ttu-id="e0c5b-158">따라서 사용자 지정 개체의 사용자 지정 사용자 인터페이스만 포함된 어셈블리는 이러한 폴더에 배포하지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e0c5b-158">Therefore you do not have to deploy assemblies that contain only the custom user interface for custom objects to these folders.</span></span>

##  <a name="installing-the-assembly-in-the-global-assembly-cache"></a><a name="installing"></a> <span data-ttu-id="e0c5b-159">전역 어셈블리 캐시에 어셈블리 설치</span><span class="sxs-lookup"><span data-stu-id="e0c5b-159">Installing the Assembly in the Global Assembly Cache</span></span>
 <span data-ttu-id="e0c5b-160">GAC(전역 어셈블리 캐시)에 태스크 어셈블리를 설치하려면 **gacutil.exe** 명령줄 도구를 사용하거나 어셈블리를 `%system%\assembly` 디렉터리에 끌어 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="e0c5b-160">To install the task assembly into the global assembly cache (GAC), use the command line tool **gacutil.exe**, or drag the assemblies to the `%system%\assembly` directory.</span></span> <span data-ttu-id="e0c5b-161">편의상 **gacutil.exe**에 대한 호출을 빌드 후 이벤트에 포함할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0c5b-161">For convenience, you can also include the call to **gacutil.exe** in a Post-build Event.</span></span>

 <span data-ttu-id="e0c5b-162">다음 명령은 **gacutil.exe**를 사용하여 *MyTask.dll*이라는 구성 요소를 GAC에 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="e0c5b-162">The following command installs a component named *MyTask.dll* into the GAC by using **gacutil.exe**.</span></span>

 `gacutil /iF MyTask.dll`

 <span data-ttu-id="e0c5b-163">새 버전의 사용자 지정 개체를 설치한 후에는 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너를 닫았다가 다시 열어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0c5b-163">You must close and reopen [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer after you install a new version of your custom object.</span></span> <span data-ttu-id="e0c5b-164">전역 어셈블리 캐시에 이전 버전의 사용자 지정 개체를 설치한 경우 새 버전을 설치하려면 먼저 이전 버전을 제거해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0c5b-164">If you have installed earlier versions of your custom object in the global assembly cache, you must remove them before installing the new version.</span></span> <span data-ttu-id="e0c5b-165">어셈블리를 제거하려면 **gacutil.exe**를 실행하고 `/u` 옵션을 사용하여 어셈블리 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e0c5b-165">To uninstall an assembly, run **gacutil.exe** and specify the assembly name with the `/u` option.</span></span>

 <span data-ttu-id="e0c5b-166">전역 어셈블리 캐시에 대한 자세한 내용은 "[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 도구"의 "전역 어셈블리 캐시 도구(Gactutil.exe)"를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="e0c5b-166">For more information about the global assembly cache, see Global Assembly Cache Tool (Gactutil.exe) in the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] Tools.</span></span>

##  <a name="troubleshooting-the-deployment"></a><a name="troubleshooting"></a> <span data-ttu-id="e0c5b-167">배포 문제 해결</span><span class="sxs-lookup"><span data-stu-id="e0c5b-167">Troubleshooting the Deployment</span></span>
 <span data-ttu-id="e0c5b-168">사용자 지정 개체가 **도구 상자** 또는 사용 가능한 개체 목록에 표시되지만 패키지에 추가할 수 없는 경우 다음을 시도해 보세요.</span><span class="sxs-lookup"><span data-stu-id="e0c5b-168">If your custom object appears in the **Toolbox** or the list of available objects, but you are not able to add it to a package, try the following:</span></span>

1.  <span data-ttu-id="e0c5b-169">전역 어셈블리 캐시에 여러 버전의 구성 요소가 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="e0c5b-169">Look in the global assembly cache for multiple versions of your component.</span></span> <span data-ttu-id="e0c5b-170">전역 어셈블리 캐시에 여러 버전의 구성 요소가 있는 경우 디자이너에서 구성 요소를 로드하지 못할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0c5b-170">If there are multiple versions of the component in the global assembly cache, the designer may not be able to load your component.</span></span> <span data-ttu-id="e0c5b-171">전역 어셈블리 캐시에서 어셈블리의 모든 인스턴스를 삭제하고 어셈블리를 다시 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="e0c5b-171">Delete all instances of the assembly from the global assembly cache, and re-add the assembly.</span></span>

2.  <span data-ttu-id="e0c5b-172">배포 폴더에 어셈블리의 단일 인스턴스만 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="e0c5b-172">Make sure that only a single instance of the assembly exists in the deployment folder.</span></span>

3.  <span data-ttu-id="e0c5b-173">도구 상자를 새로 고칩니다.</span><span class="sxs-lookup"><span data-stu-id="e0c5b-173">Refresh the Toolbox.</span></span>

4.  <span data-ttu-id="e0c5b-174">[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]를 **devenv.exe**에 연결하고 초기화 코드를 단계별로 실행하도록 중단점을 설정하여 예외가 발생하지 않도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0c5b-174">Attach [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] to **devenv.exe** and set a breakpoint to step through your initialization code to ensure that no exceptions occur.</span></span>

##  <a name="testing-and-debugging-your-code"></a><a name="testing"></a> <span data-ttu-id="e0c5b-175">코드 테스트 및 디버깅</span><span class="sxs-lookup"><span data-stu-id="e0c5b-175">Testing and Debugging Your Code</span></span>
 <span data-ttu-id="e0c5b-176">사용자 지정 개체의 런타임 메서드를 가장 간단하게 디버그하려면 사용자 지정 개체를 빌드하고 해당 구성 요소를 사용하는 패키지를 실행한 후에 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]에서 **dtexec.exe**를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="e0c5b-176">The simplest approach to debugging the run-time methods of a custom object is to start **dtexec.exe** from [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] after building your custom object and run a package that uses the component.</span></span>

 <span data-ttu-id="e0c5b-177">메서드와 같은 구성 요소의 디자인 타임 메서드를 디버깅 하려면 `Validate` 의 두 번째 인스턴스에서 해당 구성 요소를 사용 하는 패키지를 열고 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] **devenv.exe** 프로세스에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0c5b-177">If you want to debug the component's design-time methods, such as the `Validate` method, open a package that uses the component in a second instance of [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], and attach to its **devenv.exe** process.</span></span>

 <span data-ttu-id="e0c5b-178">또한 패키지가 열려 있고 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너에서 실행 중일 때 구성 요소의 런타임 메서드를 디버그하려면 **DtsDebugHost.exe** 프로세스에도 연결할 수 있도록 패키지 실행을 강제로 일시 중지해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0c5b-178">If you also want to debug the component's run-time methods when a package is open and running in [!INCLUDE[ssIS](../../includes/ssis-md.md)] designer, you must force a pause in the execution of the package so that you can also attach to the **DtsDebugHost.exe** process.</span></span>

#### <a name="to-debug-an-objects-run-time-methods-by-attaching-to-dtexecexe"></a><span data-ttu-id="e0c5b-179">dtexec.exe에 연결하여 개체의 런타임 메서드를 디버깅하려면</span><span class="sxs-lookup"><span data-stu-id="e0c5b-179">To debug an object's run-time methods by attaching to dtexec.exe</span></span>

1.  <span data-ttu-id="e0c5b-180">이 항목에 설명된 대로 디버그 구성 요소에서 프로젝트를 서명 및 빌드하고 배포한 다음 전역 어셈블리 캐시에 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="e0c5b-180">Sign and build your project in the Debug configuration, deploy it, and install it in the global assembly cache as described in this topic.</span></span>

2.  <span data-ttu-id="e0c5b-181">**프로젝트 속성**의 **디버그** 탭에서 시작 **동작**으로 **시작 외부 프로그램** 을 선택 하 고 기본적으로 C:\Program Files\Microsoft SQL server\120\dts\binn입니다 .에 설치 된 **dtexec.exe**를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="e0c5b-181">On the **Debug** tab of **Project Properties**, select **Start external program** as the **Start Action**, and locate **dtexec.exe**, which is installed by default in C:\Program Files\Microsoft SQL Server\120\DTS\Binn.</span></span>

3.  <span data-ttu-id="e0c5b-182">**명령줄 옵션** 입력란의 **시작 옵션** 아래에서 구성 요소를 사용하는 패키지를 실행하는 데 필요한 명령줄 인수를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="e0c5b-182">In the **Command line options** text box, under **Start Options**, enter the command line arguments required to run a package that uses your component.</span></span> <span data-ttu-id="e0c5b-183">명령줄 인수는 /F[ILE] 스위치와 그 다음에 나오는 .dtsx 파일의 경로 및 파일 이름으로 구성되는 경우가 많습니다.</span><span class="sxs-lookup"><span data-stu-id="e0c5b-183">Often the command-line argument will consist of the /F[ILE] switch followed by the path and file name of the .dtsx file.</span></span> <span data-ttu-id="e0c5b-184">자세한 내용은 [dtexec Utility](../packages/dtexec-utility.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e0c5b-184">For more information, see [dtexec Utility](../packages/dtexec-utility.md).</span></span>

4.  <span data-ttu-id="e0c5b-185">원본 코드에서 구성 요소의 런타임 메서드 중 적절한 위치에 중단점을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="e0c5b-185">Set breakpoints in the source code where appropriate in the run-time methods of your component.</span></span>

5.  <span data-ttu-id="e0c5b-186">프로젝트를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="e0c5b-186">Run your project.</span></span>

#### <a name="to-debug-a-custom-objects-design-time-methods-by-attaching-to-sql-server-data-tools"></a><span data-ttu-id="e0c5b-187">SQL Server Data Tools에 연결하여 사용자 지정 개체의 디자인 타임 메서드를 디버깅하려면</span><span class="sxs-lookup"><span data-stu-id="e0c5b-187">To debug a custom object's design-time methods by attaching to SQL Server Data Tools</span></span>

1.  <span data-ttu-id="e0c5b-188">이 항목에 설명된 대로 디버그 구성 요소에서 프로젝트를 서명 및 빌드하고 배포한 다음 전역 어셈블리 캐시에 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="e0c5b-188">Sign and build your project in the Debug configuration, deploy it, and install it in the global assembly cache as described in this topic.</span></span>

2.  <span data-ttu-id="e0c5b-189">원본 코드에서 사용자 지정 개체의 디자인 타임 메서드 중 적절한 위치에 중단점을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="e0c5b-189">Set breakpoints in the source code where appropriate in the design-time methods of your custom object.</span></span>

3.  <span data-ttu-id="e0c5b-190">[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]의 두 번째 인스턴스를 열고 해당 사용자 지정 개체를 사용하는 패키지가 포함된 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 프로젝트를 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="e0c5b-190">Open a second instance of [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] and load an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project that contains a package that uses the custom object.</span></span>

4.  <span data-ttu-id="e0c5b-191">[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]의 첫 번째 인스턴스에서 **디버그** 메뉴의 **프로세스에 연결**을 선택하여 패키지가 로드되는 **devenv.exe**의 두 번째 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="e0c5b-191">From the first instance of [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], attach to the second instance of **devenv.exe** in which the package is loaded by selecting **Attach to Process** from the **Debug** menu of the first instance.</span></span>

5.  <span data-ttu-id="e0c5b-192">[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]의 두 번째 인스턴스에서 패키지를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="e0c5b-192">Run the package from the second instance of [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].</span></span>

#### <a name="to-debug-a-custom-objects-run-time-methods-by-attaching-to-sql-server-data-tools"></a><span data-ttu-id="e0c5b-193">SQL Server Data Tools에 연결하여 사용자 지정 개체의 런타임 메서드를 디버깅하려면</span><span class="sxs-lookup"><span data-stu-id="e0c5b-193">To debug a custom object's run-time methods by attaching to SQL Server Data Tools</span></span>

1.  <span data-ttu-id="e0c5b-194">이전 절차에 나열된 단계를 완료한 후 **DtsDebugHost.exe**에 연결할 수 있도록 패키지 실행을 강제로 일시 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="e0c5b-194">After you have completed the steps listed in the previous procedure, force a pause in the execution of your package so that you can attach to **DtsDebugHost.exe**.</span></span> <span data-ttu-id="e0c5b-195">패키지는 `OnPreExecute` 이벤트에 중단점을 추가하거나, 프로젝트에 스크립트 태스크를 추가하고 모달 메시지 상자를 표시하는 스크립트를 입력하여 강제로 일시 중지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0c5b-195">You can force this pause by adding a breakpoint to the `OnPreExecute` event, or by adding a Script task to your project and entering script that displays a modal message box.</span></span>

2.  <span data-ttu-id="e0c5b-196">패키지를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="e0c5b-196">Run the package.</span></span> <span data-ttu-id="e0c5b-197">일시 중지가 발생하면 코드 프로젝트가 열려 있는 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 인스턴스로 전환하고 **디버그** 메뉴에서 **프로세스에 연결**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e0c5b-197">When the pause occurs, switch to the instance of [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] in which your code project is open, and select **Attach to Process** from the **Debug** menu.</span></span> <span data-ttu-id="e0c5b-198">**형식** 열에 **x86** 전용으로 나열된 인스턴스가 아니라 **Managed, x86**으로 나열된 **DtsDebugHost.exe** 인스턴스에 연결해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0c5b-198">Make sure to attach to the instance of **DtsDebugHost.exe** listed as **Managed, x86** in the **Type** column, not to the instance listed as **x86** only.</span></span>

3.  <span data-ttu-id="e0c5b-199">일시 중지된 패키지로 돌아가서 중단점을 지나 계속하거나 **확인**을 클릭하여 스크립트 태스크에서 발생한 메시지 상자를 닫고 패키지 실행 및 디버깅을 계속합니다.</span><span class="sxs-lookup"><span data-stu-id="e0c5b-199">Return to the paused package and continue past the breakpoint, or click **OK** to dismiss the message box raised by the Script task, and continue package execution and debugging.</span></span>

<span data-ttu-id="e0c5b-200">![Integration Services 아이콘 (작은 아이콘)](../media/dts-16.gif "Integration Services 아이콘(작은 아이콘)")  **은 최신 상태로 유지 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="e0c5b-200">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="e0c5b-201">Microsoft의 최신 다운로드, 문서, 예제 및 비디오와 커뮤니티에서 선택된 솔루션을 보려면 MSDN의 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="e0c5b-201">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="e0c5b-202">MSDN의 Integration Services 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="e0c5b-202">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="e0c5b-203">이러한 업데이트에 대한 자동 알림을 받으려면 해당 페이지에서 제공하는 RSS 피드를 구독하세요.</span><span class="sxs-lookup"><span data-stu-id="e0c5b-203">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>

## <a name="see-also"></a><span data-ttu-id="e0c5b-204">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e0c5b-204">See Also</span></span>
 <span data-ttu-id="e0c5b-205">[Integration Services에 대 한 사용자 지정 개체 개발](developing-custom-objects-for-integration-services.md) [사용자 지정 개체 유지](persisting-custom-objects.md) [패키지 개발을 위한 문제 해결 도구](../troubleshooting/troubleshooting-tools-for-package-development.md)</span><span class="sxs-lookup"><span data-stu-id="e0c5b-205">[Developing Custom Objects for Integration Services](developing-custom-objects-for-integration-services.md) [Persisting Custom Objects](persisting-custom-objects.md) [Troubleshooting Tools for Package Development](../troubleshooting/troubleshooting-tools-for-package-development.md)</span></span>


