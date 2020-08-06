---
title: 스크립팅 솔루션에서 다른 어셈블리 참조 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- SSIS Script task, .NET Framework
- Script task [Integration Services], adding references
- referencing custom assemblies
- SSIS Script task, VisualBasic namespace
- assemblies [Integration Services]
- VisualBasic namespace
- Script task [Integration Services], VisualBasic namespace
- Microsoft.VisualBasic namespace
- Script task [Integration Services], .NET Framework
- .NET Framework [Integration Services]
- referencing Web services
ms.assetid: 9b655bcd-19f6-43d8-9f89-1b4d299c6380
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 685bbaa62da88e84cd848eb49dcf5bedb03d5390
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647757"
---
# <a name="referencing-other-assemblies-in-scripting-solutions"></a><span data-ttu-id="2b4c3-102">스크립팅 솔루션에서 다른 어셈블리 참조</span><span class="sxs-lookup"><span data-stu-id="2b4c3-102">Referencing Other Assemblies in Scripting Solutions</span></span>
  <span data-ttu-id="2b4c3-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 클래스 라이브러리는 스크립트 개발자가 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 패키지에서 사용자 지정 기능을 구현하는 데 사용할 수 있는 강력한 도구 세트를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="2b4c3-103">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] class library provides the script developer with a powerful set of tools for implementing custom functionality in [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages.</span></span> <span data-ttu-id="2b4c3-104">스크립트 태스크와 스크립트 구성 요소에서는 관리되는 사용자 지정 어셈블리도 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b4c3-104">The Script task and the Script component can also use custom managed assemblies.</span></span>

> [!NOTE]
>  <span data-ttu-id="2b4c3-105">패키지에서 웹 서비스의 개체와 메서드를 사용할 수 있도록 설정하려면 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] VSTA(Tools for Applications)에서 사용할 수 있는 **웹 참조 추가** 명령을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="2b4c3-105">To enable your packages to use the objects and methods from a Web service, use the **Add Web Reference** command available in [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA).</span></span> <span data-ttu-id="2b4c3-106">이전 버전의 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]에서는 웹 서비스를 사용하려면 프록시 클래스를 생성해야 했습니다.</span><span class="sxs-lookup"><span data-stu-id="2b4c3-106">In earlier versions of [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], you had to generate a proxy class to use a Web service.</span></span>

## <a name="using-a-managed-assembly"></a><span data-ttu-id="2b4c3-107">관리되는 어셈블리 사용</span><span class="sxs-lookup"><span data-stu-id="2b4c3-107">Using a Managed Assembly</span></span>
 <span data-ttu-id="2b4c3-108">디자인 타임에 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]에서 관리되는 어셈블리를 찾을 수 있게 하려면 다음 단계를 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2b4c3-108">For [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] to find a managed assembly at design time, you must do the following steps:</span></span>

1.  <span data-ttu-id="2b4c3-109">컴퓨터의 임의 폴더에 관리되는 어셈블리를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="2b4c3-109">Store the managed assembly in any folder on your computer.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="2b4c3-110">이전 버전의 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]에서는 %windir%\Microsoft.NET\Framework\vx.x.xxxxx 폴더나 %ProgramFiles%\Microsoft SQL Server\100\SDK\Assemblies 폴더에 저장된 관리되는 어셈블리에 대한 참조만 추가할 수 있었습니다.</span><span class="sxs-lookup"><span data-stu-id="2b4c3-110">In earlier versions of [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], you could only add a reference to a managed assembly that was stored in the %windir%\Microsoft.NET\Framework\vx.x.xxxxx folder or the %ProgramFiles%\Microsoft SQL Server\100\SDK\Assemblies folder.</span></span>

2.  <span data-ttu-id="2b4c3-111">관리되는 어셈블리에 대한 참조를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="2b4c3-111">Add a reference to the managed assembly.</span></span>

     <span data-ttu-id="2b4c3-112">참조를 추가하려면 VSTA의 **참조 추가** 대화 상자에 있는 **찾아보기** 탭에서 관리되는 어셈블리를 찾아 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="2b4c3-112">To add the reference, in VSTA, in the **Add Reference** dialog box, on the **Browse** tab, locate and add the managed assembly.</span></span>

 <span data-ttu-id="2b4c3-113">런타임에 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]에서 관리되는 어셈블리를 찾을 수 있게 하려면 다음 단계를 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2b4c3-113">For [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] to find the managed assembly at run time, you must do the following steps:</span></span>

1.  <span data-ttu-id="2b4c3-114">강력한 이름으로 관리되는 어셈블리에 서명합니다.</span><span class="sxs-lookup"><span data-stu-id="2b4c3-114">Sign the managed assembly with a strong name.</span></span>

2.  <span data-ttu-id="2b4c3-115">패키지가 실행되는 컴퓨터의 전역 어셈블리 캐시에 어셈블리를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="2b4c3-115">Install the assembly in the global assembly cache on the computer on which the package is run.</span></span>

     <span data-ttu-id="2b4c3-116">자세한 내용은 [사용자 지정 개체 빌드, 배포 및 디버그](../extending-packages-custom-objects/building-deploying-and-debugging-custom-objects.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2b4c3-116">For more information, see [Building, Deploying, and Debugging Custom Objects](../extending-packages-custom-objects/building-deploying-and-debugging-custom-objects.md).</span></span>

## <a name="using-the-microsoft-net-framework-class-library"></a><span data-ttu-id="2b4c3-117">Microsoft .NET Framework 클래스 라이브러리 사용</span><span class="sxs-lookup"><span data-stu-id="2b4c3-117">Using the Microsoft .NET Framework Class Library</span></span>
 <span data-ttu-id="2b4c3-118">스크립트 태스크와 스크립트 구성 요소에서는 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 클래스 라이브러리에서 제공하는 다른 모든 개체와 기능을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b4c3-118">The Script task and the Script component can take advantage of all the other objects and functionality exposed by the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] class library.</span></span> <span data-ttu-id="2b4c3-119">예를 들어 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]를 사용하여 사용자 환경에 대한 정보를 검색하고 패키지를 실행하는 컴퓨터와 상호 작용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b4c3-119">For example, by using the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], you can retrieve information about your environment and interact with the computer that is running the package.</span></span>

 <span data-ttu-id="2b4c3-120">다음 목록에서는 자주 사용되는 몇 가지 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 클래스에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="2b4c3-120">This list describes several of the more frequently used [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] classes:</span></span>

-   <span data-ttu-id="2b4c3-121">`System.Data`ADO.NET 아키텍처를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="2b4c3-121">`System.Data` Contains the ADO.NET architecture.</span></span>

-   <span data-ttu-id="2b4c3-122">`System.IO`파일 시스템 및 스트림에 대 한 인터페이스를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="2b4c3-122">`System.IO` Provides an interface to the file system and streams.</span></span>

-   <span data-ttu-id="2b4c3-123">`System.Windows.Forms`폼을 만드는 기능을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="2b4c3-123">`System.Windows.Forms` Provides form creation.</span></span>

-   <span data-ttu-id="2b4c3-124">`System.Text.RegularExpressions`정규식 작업을 위한 클래스를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="2b4c3-124">`System.Text.RegularExpressions` Provides classes for working with regular expressions.</span></span>

-   <span data-ttu-id="2b4c3-125">`System.Environment`로컬 컴퓨터, 현재 사용자, 컴퓨터 및 사용자 설정에 대 한 정보를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="2b4c3-125">`System.Environment` Returns information about the local computer, the current user, and computer and user settings.</span></span>

-   <span data-ttu-id="2b4c3-126">`System.Net`네트워크 통신을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="2b4c3-126">`System.Net` Provides network communications.</span></span>

-   <span data-ttu-id="2b4c3-127">`System.DirectoryServices`Active Directory를 노출 합니다.</span><span class="sxs-lookup"><span data-stu-id="2b4c3-127">`System.DirectoryServices` Exposes Active Directory.</span></span>

-   <span data-ttu-id="2b4c3-128">`System.Drawing`광범위 한 이미지 조작 라이브러리를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="2b4c3-128">`System.Drawing` Provides extensive image manipulation libraries.</span></span>

-   <span data-ttu-id="2b4c3-129">`System.Threading`다중 스레드 프로그래밍을 가능 하 게 합니다.</span><span class="sxs-lookup"><span data-stu-id="2b4c3-129">`System.Threading` Enables multithreaded programming.</span></span>

 <span data-ttu-id="2b4c3-130">[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]에 대한 자세한 내용은 MSDN Library를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="2b4c3-130">For more information about the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], see the MSDN Library.</span></span>

<span data-ttu-id="2b4c3-131">![Integration Services 아이콘 (작은 아이콘)](../media/dts-16.gif "Integration Services 아이콘(작은 아이콘)")  **은 최신 상태로 유지 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="2b4c3-131">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="2b4c3-132">Microsoft의 최신 다운로드, 문서, 예제 및 비디오와 커뮤니티에서 선택된 솔루션을 보려면 MSDN의 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="2b4c3-132">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="2b4c3-133">MSDN의 Integration Services 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="2b4c3-133">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="2b4c3-134">이러한 업데이트에 대한 자동 알림을 받으려면 해당 페이지에서 제공하는 RSS 피드를 구독하세요.</span><span class="sxs-lookup"><span data-stu-id="2b4c3-134">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>

## <a name="see-also"></a><span data-ttu-id="2b4c3-135">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2b4c3-135">See Also</span></span>
 [<span data-ttu-id="2b4c3-136">스크립팅을 사용한 패키지 확장</span><span class="sxs-lookup"><span data-stu-id="2b4c3-136">Extending Packages with Scripting</span></span>](extending-packages-with-scripting.md)


