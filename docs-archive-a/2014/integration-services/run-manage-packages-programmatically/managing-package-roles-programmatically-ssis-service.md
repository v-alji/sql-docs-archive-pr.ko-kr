---
title: 프로그래밍 방식으로 패키지 역할 관리(SSIS 서비스) | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- Integration Services packages, roles
- roles [Integration Services]
- packages [Integration Services], roles
ms.assetid: 2e0ca0d5-d4f5-421d-b17d-a48b37b923e5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: dff54f3f90d9e008ae21c83c2a8fdc3f7440a5c3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740137"
---
# <a name="managing-package-roles-programmatically-ssis-service"></a><span data-ttu-id="860f9-102">프로그래밍 방식으로 패키지 역할 관리(SSIS 서비스)</span><span class="sxs-lookup"><span data-stu-id="860f9-102">Managing Package Roles Programmatically (SSIS Service)</span></span>
  <span data-ttu-id="860f9-103">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 패키지를 프로그래밍 방식으로 사용할 때 패키지에 적용할 수 있는 역할을 확인하거나 개별 패키지에 적용된 역할을 확인 또는 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="860f9-103">As you work programmatically with [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages, you may want to determine which roles are available to apply to packages, or to determine or set the roles applied to an individual package.</span></span> <span data-ttu-id="860f9-104"><xref:Microsoft.SqlServer.Dts.Runtime.Application> 네임스페이스의 <xref:Microsoft.SqlServer.Dts.Runtime> 클래스는 이 요구 사항을 충족하기 위한 다양한 메서드를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="860f9-104">The <xref:Microsoft.SqlServer.Dts.Runtime.Application> class of the <xref:Microsoft.SqlServer.Dts.Runtime> namespace provides a variety of methods to satisfy these requirements.</span></span>

 <span data-ttu-id="860f9-105">역할은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **msdb** 데이터베이스에 저장된 패키지에만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="860f9-105">Roles apply only to packages stored in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **msdb** database.</span></span> <span data-ttu-id="860f9-106">패키지 역할에 대한 자세한 내용은 [Integration Services 역할&#40;SSIS Service&#41;](../security/integration-services-roles-ssis-service.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="860f9-106">For more information about package roles, see [Integration Services Roles &#40;SSIS Service&#41;](../security/integration-services-roles-ssis-service.md).</span></span>

 <span data-ttu-id="860f9-107">이 항목에서 설명한 모든 메서드에는 `Microsoft.SqlServer.ManagedDTS` 어셈블리에 대한 참조가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="860f9-107">All the methods discussed in this topic require a reference to the `Microsoft.SqlServer.ManagedDTS` assembly.</span></span> <span data-ttu-id="860f9-108">새 프로젝트에 참조를 추가한 후 `using` 또는 `Imports` 문을 사용하여 <xref:Microsoft.SqlServer.Dts.Runtime> 네임스페이스를 가져오십시오.</span><span class="sxs-lookup"><span data-stu-id="860f9-108">After you add the reference in a new project, import the <xref:Microsoft.SqlServer.Dts.Runtime> namespace by using a `using` or `Imports` statement.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="860f9-109">SSIS 패키지 저장소를 사용하기 위한 <xref:Microsoft.SqlServer.Dts.Runtime.Application> 클래스의 메서드는 ".", localhost 또는 로컬 서버의 서버 이름만 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="860f9-109">The methods of the <xref:Microsoft.SqlServer.Dts.Runtime.Application> class for working with the SSIS Package Store support only ".", localhost, or the server name for the local server.</span></span> <span data-ttu-id="860f9-110">"(local)"은 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="860f9-110">You cannot use "(local)".</span></span>

## <a name="determining-which-roles-are-available"></a><span data-ttu-id="860f9-111">사용 가능한 역할 확인</span><span class="sxs-lookup"><span data-stu-id="860f9-111">Determining Which Roles Are Available</span></span>
 <span data-ttu-id="860f9-112">특정 서버에 저장된 패키지에 사용할 수 있는 역할을 확인하려면 <xref:Microsoft.SqlServer.Dts.Runtime.Application.GetDtsServerRoles%2A> 클래스의 <xref:Microsoft.SqlServer.Dts.Runtime.Application> 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="860f9-112">To determine which roles are available for the packages stored on a particular server, call the <xref:Microsoft.SqlServer.Dts.Runtime.Application.GetDtsServerRoles%2A> method of the <xref:Microsoft.SqlServer.Dts.Runtime.Application> class.</span></span>

## <a name="determining-which-roles-are-assigned"></a><span data-ttu-id="860f9-113">할당된 역할 확인</span><span class="sxs-lookup"><span data-stu-id="860f9-113">Determining Which Roles Are Assigned</span></span>
 <span data-ttu-id="860f9-114">특정 패키지에 이미 할당된 역할을 확인하려면 <xref:Microsoft.SqlServer.Dts.Runtime.Application.GetPackageRoles%2A> 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="860f9-114">To determine which roles have already been assigned to a particular package, call the <xref:Microsoft.SqlServer.Dts.Runtime.Application.GetPackageRoles%2A> method.</span></span> <span data-ttu-id="860f9-115">패키지에 역할을 할당하려면 <xref:Microsoft.SqlServer.Dts.Runtime.Application.SetPackageRoles%2A> 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="860f9-115">To assign roles to a package, call the <xref:Microsoft.SqlServer.Dts.Runtime.Application.SetPackageRoles%2A> method.</span></span>

<span data-ttu-id="860f9-116">![Integration Services 아이콘 (작은 아이콘)](../media/dts-16.gif "Integration Services 아이콘(작은 아이콘)")  **은 최신 상태로 유지 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="860f9-116">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="860f9-117">Microsoft의 최신 다운로드, 문서, 예제 및 비디오와 커뮤니티에서 선택된 솔루션을 보려면 MSDN의 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="860f9-117">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="860f9-118">MSDN의 Integration Services 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="860f9-118">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="860f9-119">이러한 업데이트에 대한 자동 알림을 받으려면 해당 페이지에서 제공하는 RSS 피드를 구독하세요.</span><span class="sxs-lookup"><span data-stu-id="860f9-119">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>

## <a name="see-also"></a><span data-ttu-id="860f9-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="860f9-120">See Also</span></span>
 [<span data-ttu-id="860f9-121">Integration Services 역할&#40;SSIS 서비스&#41;</span><span class="sxs-lookup"><span data-stu-id="860f9-121">Integration Services Roles &#40;SSIS Service&#41;</span></span>](../security/integration-services-roles-ssis-service.md)


