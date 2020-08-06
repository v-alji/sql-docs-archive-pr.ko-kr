---
title: 프로그래밍 방식으로 패키지 및 폴더 관리 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- enumerators [Integration Services]
- packages [Integration Services], managing
- custom enumerators [Integration Services]
ms.assetid: ec59b75d-ba09-44ac-9039-9d593bb462d9
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 695ff4ad020dbdfb2564b4964a55324db4248517
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740131"
---
# <a name="managing-packages-and-folders-programmatically"></a><span data-ttu-id="6a305-102">프로그래밍 방식으로 패키지 및 폴더 관리</span><span class="sxs-lookup"><span data-stu-id="6a305-102">Managing Packages and Folders Programmatically</span></span>
  <span data-ttu-id="6a305-103">프로그래밍 방식으로 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 패키지에 대한 작업을 수행할 때 개별 패키지 또는 폴더가 있는지 여부를 확인하거나 패키지가 저장된 폴더를 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6a305-103">As you work programmatically with [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages, you may want to determine whether an individual package or folder exists, or to manage the folders in which packages are stored.</span></span> <span data-ttu-id="6a305-104"><xref:Microsoft.SqlServer.Dts.Runtime.Application> 네임스페이스의 <xref:Microsoft.SqlServer.Dts.Runtime> 클래스는 이 요구 사항을 충족하기 위한 다양한 메서드를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="6a305-104">The <xref:Microsoft.SqlServer.Dts.Runtime.Application> class of the <xref:Microsoft.SqlServer.Dts.Runtime> namespace provides a variety of methods to satisfy these requirements.</span></span>  
  
##  <a name="determining-whether-a-package-or-folder-exists"></a><a name="exists"></a> <span data-ttu-id="6a305-105">패키지 또는 폴더가 있는지 확인</span><span class="sxs-lookup"><span data-stu-id="6a305-105">Determining Whether a Package or Folder Exists</span></span>  
 <span data-ttu-id="6a305-106">저장된 패키지가 있는지 여부를 프로그래밍 방식으로 확인하려면 해당 패키지를 로드 및 실행하기 전에 다음 메서드 중 하나를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="6a305-106">To determine programmatically whether a saved package exists, call one of the following methods before attempting to load and run the package:</span></span>  
  
|<span data-ttu-id="6a305-107">스토리지 위치</span><span class="sxs-lookup"><span data-stu-id="6a305-107">Storage Location</span></span>|<span data-ttu-id="6a305-108">호출할 메서드</span><span class="sxs-lookup"><span data-stu-id="6a305-108">Method to Call</span></span>|  
|----------------------|--------------------|  
|<span data-ttu-id="6a305-109">SSIS 패키지 저장소</span><span class="sxs-lookup"><span data-stu-id="6a305-109">SSIS Package Store</span></span>|<xref:Microsoft.SqlServer.Dts.Runtime.Application.ExistsOnDtsServer%2A>|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.ExistsOnSqlServer%2A>|  
  
 <span data-ttu-id="6a305-110">폴더가 있는지 여부를 프로그래밍 방식으로 확인하려면 해당 폴더에 저장된 패키지를 나열하기 전에 다음 메서드 중 하나를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="6a305-110">To determine programmatically whether a folder exists, call one of the following methods before attempting to list the packages stored in the folder, :</span></span>  
  
|<span data-ttu-id="6a305-111">스토리지 위치</span><span class="sxs-lookup"><span data-stu-id="6a305-111">Storage Location</span></span>|<span data-ttu-id="6a305-112">호출할 메서드</span><span class="sxs-lookup"><span data-stu-id="6a305-112">Method to Call</span></span>|  
|----------------------|--------------------|  
|<span data-ttu-id="6a305-113">SSIS 패키지 저장소</span><span class="sxs-lookup"><span data-stu-id="6a305-113">SSIS Package Store</span></span>|<xref:Microsoft.SqlServer.Dts.Runtime.Application.FolderExistsOnDtsServer%2A>|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.FolderExistsOnSqlServer%2A>|  
  

  
##  <a name="managing-packages-and-folders"></a><a name="managing"></a> <span data-ttu-id="6a305-114">패키지 및 폴더 관리</span><span class="sxs-lookup"><span data-stu-id="6a305-114">Managing Packages and Folders</span></span>  
 <span data-ttu-id="6a305-115"><xref:Microsoft.SqlServer.Dts.Runtime.Application> 네임스페이스의 <xref:Microsoft.SqlServer.Dts.Runtime> 클래스에서는 패키지와 패키지가 저장된 폴더를 관리하기 위한 추가 메서드를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="6a305-115">The <xref:Microsoft.SqlServer.Dts.Runtime.Application> class of the <xref:Microsoft.SqlServer.Dts.Runtime> namespace provides additional methods for managing packages and the folders in which they are stored.</span></span>  
  
###  <a name="removing-a-package"></a><a name="managing_rempkg"></a> <span data-ttu-id="6a305-116">패키지 제거</span><span class="sxs-lookup"><span data-stu-id="6a305-116">Removing a Package</span></span>  
 <span data-ttu-id="6a305-117">저장된 패키지를 프로그래밍 방식으로 제거하려면 다음 메서드 중 하나를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="6a305-117">To remove a saved package programmatically, call one of the following methods:</span></span>  
  
|<span data-ttu-id="6a305-118">스토리지 위치</span><span class="sxs-lookup"><span data-stu-id="6a305-118">Storage Location</span></span>|<span data-ttu-id="6a305-119">호출할 메서드</span><span class="sxs-lookup"><span data-stu-id="6a305-119">Method to Call</span></span>|  
|----------------------|--------------------|  
|<span data-ttu-id="6a305-120">SSIS 패키지 저장소</span><span class="sxs-lookup"><span data-stu-id="6a305-120">SSIS Package Store</span></span>|<xref:Microsoft.SqlServer.Dts.Runtime.Application.RemoveFromDtsServer%2A>|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.RemoveFromSqlServer%2A>|  
  

  
###  <a name="creating-a-folder"></a><a name="managing_create"></a> <span data-ttu-id="6a305-121">폴더 만들기</span><span class="sxs-lookup"><span data-stu-id="6a305-121">Creating a Folder</span></span>  
 <span data-ttu-id="6a305-122">프로그래밍 방식으로 스토리지 폴더를 만들려면 다음 메서드 중 하나를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="6a305-122">To create a storage folder programmatically, call one of the following methods:</span></span>  
  
|<span data-ttu-id="6a305-123">스토리지 위치</span><span class="sxs-lookup"><span data-stu-id="6a305-123">Storage Location</span></span>|<span data-ttu-id="6a305-124">호출할 메서드</span><span class="sxs-lookup"><span data-stu-id="6a305-124">Method to Call</span></span>|  
|----------------------|--------------------|  
|<span data-ttu-id="6a305-125">SSIS 패키지 저장소</span><span class="sxs-lookup"><span data-stu-id="6a305-125">SSIS Package Store</span></span>|<xref:Microsoft.SqlServer.Dts.Runtime.Application.CreateFolderOnDtsServer%2A>|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.CreateFolderOnSqlServer%2A>|  
  

  
###  <a name="removing-a-folder"></a><a name="managing_remfldr"></a> <span data-ttu-id="6a305-126">폴더 제거</span><span class="sxs-lookup"><span data-stu-id="6a305-126">Removing a Folder</span></span>  
 <span data-ttu-id="6a305-127">프로그래밍 방식으로 스토리지 폴더를 제거하려면 다음 메서드 중 하나를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="6a305-127">To remove a storage folder programmatically, call one of the following methods:</span></span>  
  
|<span data-ttu-id="6a305-128">스토리지 위치</span><span class="sxs-lookup"><span data-stu-id="6a305-128">Storage Location</span></span>|<span data-ttu-id="6a305-129">호출할 메서드</span><span class="sxs-lookup"><span data-stu-id="6a305-129">Method to Call</span></span>|  
|----------------------|--------------------|  
|<span data-ttu-id="6a305-130">SSIS 패키지 저장소</span><span class="sxs-lookup"><span data-stu-id="6a305-130">SSIS Package Store</span></span>|<xref:Microsoft.SqlServer.Dts.Runtime.Application.RemoveFolderFromDtsServer%2A>|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.RemoveFolderFromSqlServer%2A>|  
  
  
  
###  <a name="renaming-a-folder"></a><a name="managing_rename"></a> <span data-ttu-id="6a305-131">폴더 이름 바꾸기</span><span class="sxs-lookup"><span data-stu-id="6a305-131">Renaming a Folder</span></span>  
 <span data-ttu-id="6a305-132">프로그래밍 방식으로 스토리지 폴더의 이름을 바꾸려면 다음 메서드 중 하나를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="6a305-132">To rename a storage folder programmatically, call one of the following methods:</span></span>  
  
|<span data-ttu-id="6a305-133">스토리지 위치</span><span class="sxs-lookup"><span data-stu-id="6a305-133">Storage Location</span></span>|<span data-ttu-id="6a305-134">호출할 메서드</span><span class="sxs-lookup"><span data-stu-id="6a305-134">Method to Call</span></span>|  
|----------------------|--------------------|  
|<span data-ttu-id="6a305-135">SSIS 패키지 저장소</span><span class="sxs-lookup"><span data-stu-id="6a305-135">SSIS Package Store</span></span>|<xref:Microsoft.SqlServer.Dts.Runtime.Application.RenameFolderOnDtsServer%2A>|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.RenameFolderOnSqlServer%2A>|  
  

  
<span data-ttu-id="6a305-136">![Integration Services 아이콘 (작은 아이콘)](../media/dts-16.gif "Integration Services 아이콘(작은 아이콘)")  **은 최신 상태로 유지 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="6a305-136">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="6a305-137">Microsoft의 최신 다운로드, 문서, 예제 및 비디오와 커뮤니티에서 선택된 솔루션을 보려면 MSDN의 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="6a305-137">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="6a305-138">MSDN의 Integration Services 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="6a305-138">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="6a305-139">이러한 업데이트에 대한 자동 알림을 받으려면 해당 페이지에서 제공하는 RSS 피드를 구독하세요.</span><span class="sxs-lookup"><span data-stu-id="6a305-139">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a305-140">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6a305-140">See Also</span></span>  
 <span data-ttu-id="6a305-141">[SSIS 서비스를 &#40;패키지 관리&#41;](../service/package-management-ssis-service.md) </span><span class="sxs-lookup"><span data-stu-id="6a305-141">[Package Management &#40;SSIS Service&#41;](../service/package-management-ssis-service.md) </span></span>  
 [<span data-ttu-id="6a305-142">프로그래밍 방식으로 사용 가능 패키지 열거</span><span class="sxs-lookup"><span data-stu-id="6a305-142">Enumerating Available Packages Programmatically</span></span>](../run-manage-packages-programmatically/enumerating-available-packages-programmatically.md)  
  
  
