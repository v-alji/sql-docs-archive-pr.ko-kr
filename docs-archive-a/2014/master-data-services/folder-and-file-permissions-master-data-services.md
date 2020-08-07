---
title: 폴더 및 파일 사용 권한(Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- security [Master Data Services], file and folder
- folders [Master Data Services]
- files [Master Data Services]
ms.assetid: 6402d81d-7349-47b1-95ca-99b0c0f4f373
author: lrtoyou1223
ms.author: lle
robots: noindex,nofollow
ms.openlocfilehash: 6dc356e074574a4c520b1f4de2f41db0e983c4df
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731831"
---
# <a name="folder-and-file-permissions-master-data-services"></a><span data-ttu-id="867be-102">폴더 및 파일 사용 권한(Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="867be-102">Folder and File Permissions (Master Data Services)</span></span>
  <span data-ttu-id="867be-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]를 설치할 경우 폴더와 파일이 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 공유 기능에 대해 지정한 설치 경로의 파일 시스템에 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="867be-103">When you install [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], folders and files are installed in the file system at the installation path you specify for [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] shared features.</span></span> <span data-ttu-id="867be-104">공유 기능에 기본 설치 경로를 사용 하는 경우 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 의 설치 경로는 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] *DRIVE*: Files\Microsoft SQL Server\120\Master Data Services입니다.</span><span class="sxs-lookup"><span data-stu-id="867be-104">If you use the default installation path for [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] shared features, the installation path for [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] is *drive*:\Program Files\Microsoft SQL Server\120\Master Data Services.</span></span> <span data-ttu-id="867be-105">공유 기능 설치 경로를 변경할 수 있지만 부모 폴더에서 상속된 사용 권한과 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]에 대해 명시적으로 설정된 사용 권한을 알고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="867be-105">Although you can change the shared features installation path, be aware of permissions that are inherited from the parent folder and permissions that are explicitly set for [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)].</span></span>  
  
## <a name="inherited-permissions"></a><span data-ttu-id="867be-106">상속된 사용 권한</span><span class="sxs-lookup"><span data-stu-id="867be-106">Inherited Permissions</span></span>  
 <span data-ttu-id="867be-107">**Microsoft SQL Server** 폴더, **Master Data Services** 폴더 및 대부분의 하위 폴더와 파일은 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 설치 프로그램에서 지정된 부모 폴더에서 사용 권한을 상속합니다.</span><span class="sxs-lookup"><span data-stu-id="867be-107">The **Microsoft SQL Server** folder, the **Master Data Services** folder, and most subfolders and files inherit permissions from the parent folder specified in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Setup.</span></span> <span data-ttu-id="867be-108">기본 설치 위치를 선택할 경우 사용 권한을 상속하는 부모 폴더는 *드라이브*:\Program Files입니다.</span><span class="sxs-lookup"><span data-stu-id="867be-108">If you choose the default installation location, the parent folder that permissions are inherited from is *drive*:\Program Files.</span></span> <span data-ttu-id="867be-109">다음 표에서는 **Program Files**의 기본 사용 권한에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="867be-109">The following table describes the default permissions for **Program Files**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="867be-110">**Program Files**의 기본 사용 권한을 수정하거나 다른 설치 위치를 선택할 경우 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 폴더 및 파일은 적절하게 부모 폴더에서 사용 권한을 상속하고 사용 권한은 다음 표에 설명된 것과 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="867be-110">If you modify default permissions for **Program Files**, or you choose a different installation location, the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] folders and files inherit permissions from their parent folder accordingly, and the permissions might differ from those described in the following table.</span></span>  
  
###### <a name="program-files-default-permissions"></a><span data-ttu-id="867be-111">Program Files 기본 사용 권한</span><span class="sxs-lookup"><span data-stu-id="867be-111">Program Files Default Permissions</span></span>  
  
|<span data-ttu-id="867be-112">그룹 또는 계정 이름</span><span class="sxs-lookup"><span data-stu-id="867be-112">Group or account name</span></span>|<span data-ttu-id="867be-113">사용 권한</span><span class="sxs-lookup"><span data-stu-id="867be-113">Permissions</span></span>|  
|---------------------------|-----------------|  
|<span data-ttu-id="867be-114">CREATOR OWNER</span><span class="sxs-lookup"><span data-stu-id="867be-114">CREATOR OWNER</span></span>|<span data-ttu-id="867be-115">특별 사용 권한</span><span class="sxs-lookup"><span data-stu-id="867be-115">Special permissions</span></span>|  
|<span data-ttu-id="867be-116">SYSTEM</span><span class="sxs-lookup"><span data-stu-id="867be-116">SYSTEM</span></span>|<span data-ttu-id="867be-117">특별 사용 권한</span><span class="sxs-lookup"><span data-stu-id="867be-117">Special permissions</span></span>|  
|<span data-ttu-id="867be-118">관리자</span><span class="sxs-lookup"><span data-stu-id="867be-118">Administrators</span></span>|<span data-ttu-id="867be-119">특별 사용 권한</span><span class="sxs-lookup"><span data-stu-id="867be-119">Special permissions</span></span>|  
|<span data-ttu-id="867be-120">사용자</span><span class="sxs-lookup"><span data-stu-id="867be-120">Users</span></span>|<span data-ttu-id="867be-121">읽기 & 실행, 폴더 내용 보기, 읽기</span><span class="sxs-lookup"><span data-stu-id="867be-121">Read & execute, List folder contents, Read</span></span>|  
|<span data-ttu-id="867be-122">TrustedInstaller</span><span class="sxs-lookup"><span data-stu-id="867be-122">TrustedInstaller</span></span>|<span data-ttu-id="867be-123">폴더 내용 보기, 특별 사용 권한</span><span class="sxs-lookup"><span data-stu-id="867be-123">List folder contents, Special permissions</span></span>|  
  
## <a name="explicit-permissions"></a><span data-ttu-id="867be-124">명시적 사용 권한</span><span class="sxs-lookup"><span data-stu-id="867be-124">Explicit Permissions</span></span>  
 <span data-ttu-id="867be-125">**MDSTempDir** 폴더 및 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] Web.config 파일( **WebApplication** 폴더에 있음)은 사용 권한을 상속하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="867be-125">The **MDSTempDir** folder and the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] Web.config file (in the **WebApplication** folder) do not inherit permissions.</span></span> <span data-ttu-id="867be-126">이러한 폴더와 파일은 선택한 설치 경로에 상관없이 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]를 설치할 때 명시적으로 설정된 사용 권한을 가집니다.</span><span class="sxs-lookup"><span data-stu-id="867be-126">They have permissions that are set explicitly when you install [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], regardless of the installation path you choose.</span></span> <span data-ttu-id="867be-127">이러한 사용 권한은 수정하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="867be-127">Do not modify these permissions.</span></span>  
  
###### <a name="mdstempdir-permissions"></a><span data-ttu-id="867be-128">MDSTempDir 사용 권한</span><span class="sxs-lookup"><span data-stu-id="867be-128">MDSTempDir Permissions</span></span>  
  
|<span data-ttu-id="867be-129">그룹 또는 계정 이름</span><span class="sxs-lookup"><span data-stu-id="867be-129">Group or account name</span></span>|<span data-ttu-id="867be-130">사용 권한</span><span class="sxs-lookup"><span data-stu-id="867be-130">Permissions</span></span>|  
|---------------------------|-----------------|  
|<span data-ttu-id="867be-131">SYSTEM</span><span class="sxs-lookup"><span data-stu-id="867be-131">SYSTEM</span></span>|<span data-ttu-id="867be-132">수정, 읽기 & 실행, 폴더 내용 보기, 읽기, 쓰기</span><span class="sxs-lookup"><span data-stu-id="867be-132">Modify, Read & execute, List folder contents, Read, Write</span></span>|  
|<span data-ttu-id="867be-133">관리자</span><span class="sxs-lookup"><span data-stu-id="867be-133">Administrators</span></span>|<span data-ttu-id="867be-134">수정, 읽기 & 실행, 폴더 내용 보기, 읽기, 쓰기</span><span class="sxs-lookup"><span data-stu-id="867be-134">Modify, Read & execute, List folder contents, Read, Write</span></span>|  
|<span data-ttu-id="867be-135">MDS_ServiceAccounts</span><span class="sxs-lookup"><span data-stu-id="867be-135">MDS_ServiceAccounts</span></span>|<span data-ttu-id="867be-136">수정, 읽기 & 실행, 폴더 내용 보기, 읽기, 쓰기</span><span class="sxs-lookup"><span data-stu-id="867be-136">Modify, Read & execute, List folder contents, Read, Write</span></span>|  
  
###### <a name="webconfig-permissions"></a><span data-ttu-id="867be-137">Web.config 사용 권한</span><span class="sxs-lookup"><span data-stu-id="867be-137">Web.config Permissions</span></span>  
  
|<span data-ttu-id="867be-138">그룹 또는 계정 이름</span><span class="sxs-lookup"><span data-stu-id="867be-138">Group or account name</span></span>|<span data-ttu-id="867be-139">사용 권한</span><span class="sxs-lookup"><span data-stu-id="867be-139">Permissions</span></span>|  
|---------------------------|-----------------|  
|<span data-ttu-id="867be-140">SYSTEM</span><span class="sxs-lookup"><span data-stu-id="867be-140">SYSTEM</span></span>|<span data-ttu-id="867be-141">모든 권한, 수정, 읽기 & 실행, 읽기, 쓰기</span><span class="sxs-lookup"><span data-stu-id="867be-141">Full control, Modify, Read & execute, Read, Write</span></span>|  
|<span data-ttu-id="867be-142">관리자</span><span class="sxs-lookup"><span data-stu-id="867be-142">Administrators</span></span>|<span data-ttu-id="867be-143">모든 권한, 수정, 읽기 & 실행, 읽기, 쓰기</span><span class="sxs-lookup"><span data-stu-id="867be-143">Full control, Modify, Read & execute, Read, Write</span></span>|  
|<span data-ttu-id="867be-144">MDS_ServiceAccounts</span><span class="sxs-lookup"><span data-stu-id="867be-144">MDS_ServiceAccounts</span></span>|<span data-ttu-id="867be-145">읽기 & 실행, 읽기</span><span class="sxs-lookup"><span data-stu-id="867be-145">Read & execute, Read</span></span>|  
  
 <span data-ttu-id="867be-146">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] Web.config 파일의 내용에 대한 자세한 내용은 [웹 구성 참조&#40;Master Data Services&#41;](web-configuration-reference-master-data-services.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="867be-146">For more information about the contents of the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] Web.config file, see [Web Configuration Reference &#40;Master Data Services&#41;](web-configuration-reference-master-data-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="867be-147">참고 항목</span><span class="sxs-lookup"><span data-stu-id="867be-147">See Also</span></span>  
 [<span data-ttu-id="867be-148">MDS(Master Data Services) 설치</span><span class="sxs-lookup"><span data-stu-id="867be-148">Install Master Data Services</span></span>](install-windows/install-master-data-services.md)  
  
  
