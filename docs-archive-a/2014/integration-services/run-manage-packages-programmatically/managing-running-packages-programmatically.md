---
title: 프로그래밍 방식으로 패키지 실행 관리 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- packages [Integration Services], managing
- running packages [Integration Services]
ms.assetid: 0e91f4ac-6f29-40d7-8c28-9b82e4802c35
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 95c5f9c28b407631764d64523b37a6295870542a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740138"
---
# <a name="managing-running-packages-programmatically"></a><span data-ttu-id="89397-102">프로그래밍 방식으로 실행 중인 패키지 관리</span><span class="sxs-lookup"><span data-stu-id="89397-102">Managing Running Packages Programmatically</span></span>
  <span data-ttu-id="89397-103">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 패키지를 프로그래밍 방식으로 사용할 때 현재 실행 중인 패키지를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="89397-103">As you work programmatically with [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages, you may want to determine which packages are currently running.</span></span> <span data-ttu-id="89397-104"><xref:Microsoft.SqlServer.Dts.Runtime.Application> 네임스페이스의 <xref:Microsoft.SqlServer.Dts.Runtime> 클래스는 이 요구 사항을 충족하기 위한 메서드와 클래스를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="89397-104">The <xref:Microsoft.SqlServer.Dts.Runtime.Application> class of the <xref:Microsoft.SqlServer.Dts.Runtime> namespace provides methods and classes to satisfy these requirements.</span></span>  
  
 <span data-ttu-id="89397-105">패키지 모니터링에 대한 자세한 내용은 [패키지 관리&#40;SSIS 서비스&#41;](../service/package-management-ssis-service.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="89397-105">For more information about monitoring packages, see [Package Management &#40;SSIS Service&#41;](../service/package-management-ssis-service.md).</span></span>  
  
 <span data-ttu-id="89397-106">이 항목에서 설명한 모든 메서드에는 `Microsoft.SqlServer.ManagedDTS` 어셈블리에 대한 참조가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="89397-106">All the methods discussed in this topic require a reference to the `Microsoft.SqlServer.ManagedDTS` assembly.</span></span> <span data-ttu-id="89397-107">새 프로젝트에 참조를 추가한 후 `using` 또는 `Imports` 문을 사용하여 <xref:Microsoft.SqlServer.Dts.Runtime> 네임스페이스를 가져오십시오.</span><span class="sxs-lookup"><span data-stu-id="89397-107">After you add the reference in a new project, import the <xref:Microsoft.SqlServer.Dts.Runtime> namespace with a `using` or `Imports` statement.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="89397-108">SSIS 패키지 저장소를 사용하기 위한 <xref:Microsoft.SqlServer.Dts.Runtime.Application> 클래스의 메서드는 ".", localhost 또는 로컬 서버의 서버 이름만 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="89397-108">The methods of the <xref:Microsoft.SqlServer.Dts.Runtime.Application> class for working with the SSIS Package Store support only ".", localhost, or the server name for the local server.</span></span> <span data-ttu-id="89397-109">"(local)"은 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="89397-109">You cannot use "(local)".</span></span>  
  
## <a name="determining-which-packages-are-currently-running"></a><span data-ttu-id="89397-110">현재 실행 중인 패키지 확인</span><span class="sxs-lookup"><span data-stu-id="89397-110">Determining Which Packages Are Currently Running</span></span>  
 <span data-ttu-id="89397-111">지정한 서버에서 현재 실행 중인 패키지를 확인하려면 <xref:Microsoft.SqlServer.Dts.Runtime.Application.GetRunningPackages%2A> 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="89397-111">To determine which packages are currently running on the specified server, call the <xref:Microsoft.SqlServer.Dts.Runtime.Application.GetRunningPackages%2A> method.</span></span> <span data-ttu-id="89397-112">이 메서드는 <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackages> 개체의 <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackage> 컬렉션을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="89397-112">This method returns a <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackages> collection of <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackage> objects.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="89397-113">관리자는 컴퓨터에서 현재 실행 중인 모든 패키지를 볼 수 있고 다른 사용자는 자신이 실행한 패키지만 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="89397-113">Administrators see all packages that are currently executing on the computer; other users see only those packages that they have launched.</span></span>  
  
## <a name="working-with-running-packages"></a><span data-ttu-id="89397-114">실행 중인 패키지 작업</span><span class="sxs-lookup"><span data-stu-id="89397-114">Working with Running Packages</span></span>  
 <span data-ttu-id="89397-115">현재 실행 중인 패키지를 확인한 후에는 패키지에 대한 정보를 가져오고 패키지를 중지하도록 요청할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="89397-115">After you have determined which packages are currently running, you can retrieve information about the packages and request that a package be stopped.</span></span>  
  
### <a name="getting-information-about-a-running-package"></a><span data-ttu-id="89397-116">실행 중인 패키지에 대한 정보 얻기</span><span class="sxs-lookup"><span data-stu-id="89397-116">Getting Information about a Running Package</span></span>  
 <span data-ttu-id="89397-117"><xref:Microsoft.SqlServer.Dts.Runtime.RunningPackages> 컬렉션을 반복할 때 <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackage> 개체의 속성을 사용하여 패키지를 찾거나 실행 중인 패키지에 대한 추가 정보를 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="89397-117">As you iterate through the <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackages> collection, you can use the properties of the <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackage> object to locate a package or to obtain additional information about the packages that are running:</span></span>  
  
-   <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackage.ExecutionDuration%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackage.ExecutionStartTime%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackage.InstanceID%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackage.PackageDescription%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackage.PackageID%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackage.PackageName%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackage.UserName%2A>  
  
### <a name="stopping-a-running-package"></a><span data-ttu-id="89397-118">실행 중인 패키지 중지</span><span class="sxs-lookup"><span data-stu-id="89397-118">Stopping a Running Package</span></span>  
 <span data-ttu-id="89397-119"><xref:Microsoft.SqlServer.Dts.Runtime.RunningPackage.Stop%2A> 개체의 <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackage> 메서드를 호출하여 패키지를 중지하도록 요청할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="89397-119">You can call the <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackage.Stop%2A> method of a <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackage> object to request that the package be stopped.</span></span> <span data-ttu-id="89397-120">중지 요청이 실행된 시간과 패키지가 실제로 중지되는 시간 사이에는 지연이 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="89397-120">There may be a delay between the time that a stop request is issued and the time that the package actually stops.</span></span>  
  
<span data-ttu-id="89397-121">![Integration Services 아이콘 (작은 아이콘)](../media/dts-16.gif "Integration Services 아이콘(작은 아이콘)")  **은 최신 상태로 유지 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="89397-121">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="89397-122">Microsoft의 최신 다운로드, 문서, 예제 및 비디오와 커뮤니티에서 선택된 솔루션을 보려면 MSDN의 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="89397-122">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="89397-123">MSDN의 Integration Services 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="89397-123">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="89397-124">이러한 업데이트에 대한 자동 알림을 받으려면 해당 페이지에서 제공하는 RSS 피드를 구독하세요.</span><span class="sxs-lookup"><span data-stu-id="89397-124">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89397-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="89397-125">See Also</span></span>  
 <span data-ttu-id="89397-126">[SSIS 서비스를 &#40;패키지 관리&#41;](../service/package-management-ssis-service.md) </span><span class="sxs-lookup"><span data-stu-id="89397-126">[Package Management &#40;SSIS Service&#41;](../service/package-management-ssis-service.md) </span></span>  
 [<span data-ttu-id="89397-127">프로그래밍 방식으로 사용 가능 패키지 열거</span><span class="sxs-lookup"><span data-stu-id="89397-127">Enumerating Available Packages Programmatically</span></span>](../run-manage-packages-programmatically/enumerating-available-packages-programmatically.md)  
  
  
