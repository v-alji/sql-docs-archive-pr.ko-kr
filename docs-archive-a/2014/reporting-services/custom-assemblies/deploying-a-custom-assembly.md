---
title: 사용자 지정 어셈블리 배포 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- deploying custom assemblies [Reporting Services]
- custom assemblies [Reporting Services], deploying
- custom assemblies [Reporting Services], updating
- updating custom assemblies
ms.assetid: c6674cd8-0de7-4a5a-9e7c-12ffa49f6fd2
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3d88e1db844304b5cbb51f4af52b4715ef7e8c1e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741639"
---
# <a name="deploying-a-custom-assembly"></a><span data-ttu-id="a4d9f-102">사용자 지정 어셈블리 배포</span><span class="sxs-lookup"><span data-stu-id="a4d9f-102">Deploying a Custom Assembly</span></span>
  <span data-ttu-id="a4d9f-103">에서 사용자 지정 어셈블리를 배포 하려면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 어셈블리를 보고서 디자이너 및 보고서 서버의 응용 프로그램 폴더에 배치 합니다.</span><span class="sxs-lookup"><span data-stu-id="a4d9f-103">To deploy a custom assembly in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], place the assembly in the application folders of both Report Designer and the report server.</span></span> <span data-ttu-id="a4d9f-104">기본적으로 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]에서 사용자 지정 어셈블리에는 `Execution` 권한이 부여됩니다.</span><span class="sxs-lookup"><span data-stu-id="a4d9f-104">By default, custom assemblies are granted `Execution` permission in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="a4d9f-105">사용자 지정 어셈블리에 실행 권한 이상의 권한을 부여하려면 보고서 서버에 대한 rssrvpolicy.config 구성 파일 및 보고서 디자이너 미리 보기 창에 대한 rspreviewpolicy.config 구성 파일을 편집해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a4d9f-105">To grant custom assemblies privileges beyond Execute permission, you will need to edit the rssrvpolicy.config configuration file for the report server and the rspreviewpolicy.config configuration file for the Report Designer preview window.</span></span> <span data-ttu-id="a4d9f-106">또는 GAC(전역 어셈블리 캐시)에 사용자 지정 어셈블리를 설치할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a4d9f-106">Alternatively, you can install your custom assembly in the global assembly cache (GAC).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a4d9f-107">보고서 디자이너에는 보고서 프로젝트를 `DebugLocal` 모드에서 시작할 때 실행되는 팝업 미리 보기 창과 미리 보기 탭이라는 두 개의 미리 보기 모드가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a4d9f-107">There are two preview modes for Report Designer: the Preview tab and the pop-up preview window that is launched when your report project is started in `DebugLocal` mode.</span></span> <span data-ttu-id="a4d9f-108">미리 보기 탭에서는 `FullTrust` 권한 집합을 사용하여 모든 보고서 식을 실행하며 보안 정책 설정을 적용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a4d9f-108">The Preview tab executes all report expressions using the `FullTrust` permission set and does not apply security policy settings.</span></span> <span data-ttu-id="a4d9f-109">팝업 미리 보기 창은 보고서 서버 기능을 시뮬레이션하기 위한 것이므로 보고서 디자이너에서 사용자 지정 어셈블리를 사용하기 위해 작업자나 관리자가 수정해야 하는 정책 구성 파일을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="a4d9f-109">The pop-up preview window is meant to simulate the report server functionality and therefore has a policy configuration file that you or an administrator must modify to use custom assemblies in Report Designer.</span></span> <span data-ttu-id="a4d9f-110">또한 이 팝업 미리 보기는 사용자 지정 어셈블리를 잠급니다.</span><span class="sxs-lookup"><span data-stu-id="a4d9f-110">This pop-up preview also locks the custom assembly.</span></span> <span data-ttu-id="a4d9f-111">따라서 사용자 지정 어셈블리 코드를 수정하거나 업데이트하려면 미리 보기 창을 닫아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a4d9f-111">Therefore, you need to close the preview window in order to modify or update your custom assembly code.</span></span>  
  
###### <a name="to-deploy-a-custom-assembly-in-reporting-services"></a><span data-ttu-id="a4d9f-112">Reporting Services에서 사용자 지정 어셈블리를 배포하려면</span><span class="sxs-lookup"><span data-stu-id="a4d9f-112">To deploy a custom assembly in Reporting Services</span></span>  
  
1.  <span data-ttu-id="a4d9f-113">사용자 지정 어셈블리를 빌드 위치에서 보고서 서버 bin 폴더 또는 보고서 디자이너 폴더에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="a4d9f-113">Copy your custom assembly from your build location to the report server bin folder or the Report Designer folder.</span></span> <span data-ttu-id="a4d9f-114">보고서 서버 bin 폴더의 기본 위치는 %ProgramFiles%\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\Reporting Services\ReportServer\bin입니다.</span><span class="sxs-lookup"><span data-stu-id="a4d9f-114">The default location of the bin folder for the report server is %ProgramFiles%\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\Reporting Services\ReportServer\bin.</span></span> <span data-ttu-id="a4d9f-115">보고서 디자이너의 기본 위치는 %ProgramFiles%\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies입니다.</span><span class="sxs-lookup"><span data-stu-id="a4d9f-115">The default location of the Report Designer is %ProgramFiles%\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies.</span></span>  
  
     <span data-ttu-id="a4d9f-116">사용자 지정 어셈블리를 보고서 서버의 bin 폴더에 배치하면 사용자 지정 어셈블리를 참조하는 보고서를 게시할 수 있고, 보고서 디자이너 폴더에 배치하면 보고서 디자이너의 사용자 지정 어셈블리를 참조하는 보고서를 실행하고 디버깅할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a4d9f-116">Placing your custom assembly in the report server bin folder enables you to publish reports that reference your custom assembly, and placing it in the Report Designer folder enables you to run and debug reports that reference your custom assembly in Report Designer.</span></span>  
  
     <span data-ttu-id="a4d9f-117">사용자 지정 어셈블리 코드에 기본 실행 권한 이상의 권한을 부여해야 하는 경우 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="a4d9f-117">If you need to grant your custom assembly code permissions beyond the default execute permissions:</span></span>  
  
2.  <span data-ttu-id="a4d9f-118">해당하는 구성 파일을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="a4d9f-118">Open the appropriate configuration file.</span></span> <span data-ttu-id="a4d9f-119">rssrvpolicy.config의 기본 위치는 %ProgramFiles%\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\Reporting Services\ReportServer입니다.</span><span class="sxs-lookup"><span data-stu-id="a4d9f-119">The default location of rssrvpolicy.config is %ProgramFiles%\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\Reporting Services\ReportServer.</span></span> <span data-ttu-id="a4d9f-120">rspreviewpolicy.config의 기본 위치는 %ProgramFiles%\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies입니다.</span><span class="sxs-lookup"><span data-stu-id="a4d9f-120">The default location of rspreviewpolicy.config is %ProgramFiles%\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies.</span></span>  
  
3.  <span data-ttu-id="a4d9f-121">사용자 지정 어셈블리에 대한 코드 그룹을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="a4d9f-121">Add a code group for your custom assembly.</span></span> <span data-ttu-id="a4d9f-122">자세한 내용은 [보안 개발&#40;Reporting Services&#41;](../extensions/secure-development/secure-development-reporting-services.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a4d9f-122">For more information, see [Secure Development &#40;Reporting Services&#41;](../extensions/secure-development/secure-development-reporting-services.md).</span></span>  
  
## <a name="updating-custom-assemblies"></a><span data-ttu-id="a4d9f-123">사용자 지정 어셈블리 업데이트</span><span class="sxs-lookup"><span data-stu-id="a4d9f-123">Updating Custom Assemblies</span></span>  
 <span data-ttu-id="a4d9f-124">게시된 다수의 보고서에서 현재 참조하고 있는 사용자 지정 어셈블리의 버전을 어느 시점에 업데이트해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a4d9f-124">At some point, you may need to update a version of a custom assembly that is currently being referenced by several published reports.</span></span> <span data-ttu-id="a4d9f-125">해당하는 어셈블리가 보고서 서버의 bin 디렉터리나 보고서 디자이너에 이미 있으며 어셈블리의 버전 번호가 높아지거나 어떤 식으로든 변경되는 경우 현재 게시된 보고서는 더 이상 올바르게 작동하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a4d9f-125">If that assembly already exists in the bin directory of the report server or Report Designer and the version number of the assembly is incremented or changed in some way, the currently published reports will no longer work properly.</span></span> <span data-ttu-id="a4d9f-126">보고서 정의의 `CodeModules` 요소에서 참조되는 어셈블리의 버전을 업데이트하고 보고서를 다시 게시해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a4d9f-126">You will need to update the version of the assembly that is referenced in the `CodeModules` element of the report definition and republish the reports.</span></span> <span data-ttu-id="a4d9f-127">사용자 지정 어셈블리를 자주 업데이트할 예정이며 현재 게시된 보고서에서 새 어셈블리를 참조해야 하는 경우에는 특정 어셈블리의 모든 업데이트에서 동일한 버전 사용을 고려해야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a4d9f-127">If you know that you will frequently update a custom assembly and your currently published reports need to reference the new assembly, you may want to consider using the same version number across all updates of a particular assembly.</span></span>  
  
 <span data-ttu-id="a4d9f-128">현재 게시된 보고서에서 새 버전의 어셈블리를 참조할 필요가 없는 경우 사용자 지정 어셈블리를 전역 어셈블리 캐시에 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a4d9f-128">If you do not need your currently published reports to reference the new version of the assembly, you can deploy your custom assembly to the global assembly cache.</span></span> <span data-ttu-id="a4d9f-129">전역 어셈블리 캐시에서는 동일한 어셈블리의 여러 버전을 유지 관리할 수 있으므로 현재 보고서에서 이전 버전의 어셈블리를 참조하고 새로 게시된 보고서에서 업데이트된 어셈블리를 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a4d9f-129">The global assembly cache can maintain multiple versions of the same assembly, so that your current reports can reference the previous version of your assembly and your newly published reports can reference the updated assembly.</span></span> <span data-ttu-id="a4d9f-130">또 다른 방법은 이전 어셈블리에 대한 모든 요청이 새 어셈블리로 리디렉션되도록 보고서 서버의 바인딩 리디렉션을 설정하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="a4d9f-130">Yet another approach would be to set the binding redirect of the report server to force a redirect of all requests for the old assembly to the new assembly.</span></span> <span data-ttu-id="a4d9f-131">이 경우 보고서 서버 Web.config 파일 및 보고서 서버 ReportService.exe.config 파일을 수정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a4d9f-131">You would need to modify the report server Web.config file and the report server ReportService.exe.config file.</span></span> <span data-ttu-id="a4d9f-132">항목은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="a4d9f-132">The entry might look like the following:</span></span>  
  
```  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="myAssembly"  
                              publicKeyToken="32ab4ba45e0a69a1"  
                              culture="neutral" />  
            <bindingRedirect oldVersion="1.0.0.0"  
                             newVersion="2.0.0.0"/>  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a4d9f-133">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a4d9f-133">See Also</span></span>  
 <span data-ttu-id="a4d9f-134">[보고서에서 사용자 지정 어셈블리 사용](using-custom-assemblies-with-reports.md) </span><span class="sxs-lookup"><span data-stu-id="a4d9f-134">[Using Custom Assemblies with Reports](using-custom-assemblies-with-reports.md) </span></span>  
 [<span data-ttu-id="a4d9f-135">어셈블리 및 전역 어셈블리 캐시 사용</span><span class="sxs-lookup"><span data-stu-id="a4d9f-135">Working with Assemblies and the Global Assembly Cache</span></span>](https://go.microsoft.com/fwlink/?LinkId=63912)  
  
  
