---
title: 원본 위치 선택 (SSIS 패키지 업그레이드 마법사) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.is.upgradewizard.selectsourcelocation.f1
ms.assetid: 429f146e-edb4-4401-a225-f2c8468971c5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e24eec77dc87a6215f9d686cf5af964cc244d68d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728456"
---
# <a name="select-source-location-ssis-package-upgrade-wizard"></a><span data-ttu-id="e043d-102">원본 위치 선택(SSIS 패키지 업그레이드 마법사)</span><span class="sxs-lookup"><span data-stu-id="e043d-102">Select Source Location (SSIS Package Upgrade Wizard)</span></span>
  <span data-ttu-id="e043d-103">**원본 위치 선택** 페이지를 사용하여 패키지를 업그레이드할 원본을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e043d-103">Use the **Select Source Location** page to specify the source from which to upgrade packages.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e043d-104">이 페이지는 [!INCLUDE[ssIS](../includes/ssis-md.md)] 또는 명령 프롬프트에서 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 패키지 업그레이드 마법사를 실행한 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e043d-104">This page is only available when you run the [!INCLUDE[ssIS](../includes/ssis-md.md)] Package Upgrade Wizard from [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] or at the command prompt.</span></span>  
  
 <span data-ttu-id="e043d-105">**SSIS 패키지 업그레이드 마법사를 실행하려면**</span><span class="sxs-lookup"><span data-stu-id="e043d-105">**To run the SSIS Package Upgrade Wizard**</span></span>  
  
-   [<span data-ttu-id="e043d-106">SSIS 패키지 업그레이드 마법사를 사용하여 Integration Services 패키지 업그레이드</span><span class="sxs-lookup"><span data-stu-id="e043d-106">Upgrade Integration Services Packages Using the SSIS Package Upgrade Wizard</span></span>](install-windows/upgrade-integration-services-packages-using-the-ssis-package-upgrade-wizard.md)  
  
## <a name="static-options"></a><span data-ttu-id="e043d-107">정적 옵션</span><span class="sxs-lookup"><span data-stu-id="e043d-107">Static Options</span></span>  
 <span data-ttu-id="e043d-108">**패키지 원본**</span><span class="sxs-lookup"><span data-stu-id="e043d-108">**Package source**</span></span>  
 <span data-ttu-id="e043d-109">업그레이드할 패키지를 포함하는 스토리지 위치를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e043d-109">Select the storage location that contains the packages to be upgraded.</span></span> <span data-ttu-id="e043d-110">이 옵션에는 다음 표에 나열된 값이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e043d-110">This option has the values listed in the following table.</span></span>  
  
|<span data-ttu-id="e043d-111">값</span><span class="sxs-lookup"><span data-stu-id="e043d-111">Value</span></span>|<span data-ttu-id="e043d-112">Description</span><span class="sxs-lookup"><span data-stu-id="e043d-112">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e043d-113">**파일 시스템**</span><span class="sxs-lookup"><span data-stu-id="e043d-113">**File System**</span></span>|<span data-ttu-id="e043d-114">업그레이드할 패키지가 로컬 컴퓨터의 폴더에 있음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="e043d-114">Indicates that the packages to be upgraded are in a folder on the local computer.</span></span><br /><br /> <span data-ttu-id="e043d-115">이러한 패키지를 업그레이드하기 전에 마법사가 원래 패키지를 백업하도록 하려면 원래 패키지를 파일 시스템에 저장해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e043d-115">To have the wizard back up the original packages before upgrading those packages, the original packages must be stored in the file system.</span></span> <span data-ttu-id="e043d-116">자세한 내용은 방법 도움말 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="e043d-116">For more information, see How To Topic.</span></span>|  
|<span data-ttu-id="e043d-117">**SSIS 패키지 저장소**</span><span class="sxs-lookup"><span data-stu-id="e043d-117">**SSIS Package Store**</span></span>|<span data-ttu-id="e043d-118">업그레이드할 패키지가 패키지 저장소에 있음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="e043d-118">Indicates that the packages to be upgraded are in the package store.</span></span> <span data-ttu-id="e043d-119">패키지 저장소는 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 서비스가 관리하는 파일 시스템 폴더 집합으로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="e043d-119">The package store consists of the set of file system folders that the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service manages.</span></span> <span data-ttu-id="e043d-120">자세한 내용은 [패키지 관리&#40;SSIS 서비스&#41;](service/package-management-ssis-service.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e043d-120">For more information, see [Package Management &#40;SSIS Service&#41;](service/package-management-ssis-service.md).</span></span><br /><br /> <span data-ttu-id="e043d-121">이 값을 선택하면 해당 **패키지 원본** 동적 옵션이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e043d-121">Selecting this value displays the corresponding **Package source** dynamic options.</span></span>|  
|<span data-ttu-id="e043d-122">**Microsoft SQL Server**</span><span class="sxs-lookup"><span data-stu-id="e043d-122">**Microsoft SQL Server**</span></span>|<span data-ttu-id="e043d-123">업그레이드할 패키지가 기존 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]인스턴스에 있음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="e043d-123">Indicates the packages to be upgraded are from an existing instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span><br /><br /> <span data-ttu-id="e043d-124">이 값을 선택하면 해당 **패키지 원본** 동적 옵션이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e043d-124">Selecting this value displays the corresponding **Package source** dynamic options.</span></span>|  
  
 <span data-ttu-id="e043d-125">**폴더**</span><span class="sxs-lookup"><span data-stu-id="e043d-125">**Folder**</span></span>  
 <span data-ttu-id="e043d-126">업그레이드할 패키지를 포함하는 폴더의 이름을 입력하거나 **찾아보기** 를 클릭하여 폴더를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="e043d-126">Type the name of a folder that contains the packages you want to upgrade or click **Browse** and locate the folder.</span></span>  
  
 <span data-ttu-id="e043d-127">**찾아보기**</span><span class="sxs-lookup"><span data-stu-id="e043d-127">**Browse**</span></span>  
 <span data-ttu-id="e043d-128">업그레이드할 패키지를 포함하는 폴더를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="e043d-128">Browse to locate the folder that contains the packages you want to upgrade.</span></span>  
  
## <a name="package-source-dynamic-options"></a><span data-ttu-id="e043d-129">패키지 원본 동적 옵션</span><span class="sxs-lookup"><span data-stu-id="e043d-129">Package Source Dynamic Options</span></span>  
  
### <a name="package-source--ssis-package-store"></a><span data-ttu-id="e043d-130">패키지 원본 = SSIS 패키지 저장소</span><span class="sxs-lookup"><span data-stu-id="e043d-130">Package source = SSIS Package Store</span></span>  
 <span data-ttu-id="e043d-131">**Server**</span><span class="sxs-lookup"><span data-stu-id="e043d-131">**Server**</span></span>  
 <span data-ttu-id="e043d-132">업그레이드할 패키지가 있는 서버의 이름을 입력하거나 목록에서 이 서버를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e043d-132">Type the name of the server that has the packages to be upgraded, or select this server in the list.</span></span>  
  
### <a name="package-source--microsoft-sql-server"></a><span data-ttu-id="e043d-133">패키지 원본 = Microsoft SQL Server</span><span class="sxs-lookup"><span data-stu-id="e043d-133">Package source = Microsoft SQL Server</span></span>  
 <span data-ttu-id="e043d-134">**Server**</span><span class="sxs-lookup"><span data-stu-id="e043d-134">**Server**</span></span>  
 <span data-ttu-id="e043d-135">업그레이드할 패키지가 있는 서버의 이름을 입력하거나 목록에서 이 서버를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e043d-135">Type the name of the server that has the packages to be upgraded, or select this server from the list.</span></span>  
  
 <span data-ttu-id="e043d-136">**Windows 인증 사용**</span><span class="sxs-lookup"><span data-stu-id="e043d-136">**Use Windows authentication**</span></span>  
 <span data-ttu-id="e043d-137">Windows 인증을 사용하여 서버에 연결하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e043d-137">Select to use Windows Authentication to connect to the server.</span></span>  
  
 <span data-ttu-id="e043d-138">**SQL Server 인증 사용**</span><span class="sxs-lookup"><span data-stu-id="e043d-138">**Use SQL Server authentication**</span></span>  
 <span data-ttu-id="e043d-139">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인증을 사용하여 서버에 연결하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e043d-139">Select to use [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication to connect to the server.</span></span> <span data-ttu-id="e043d-140">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인증을 사용하는 경우 사용자 이름과 암호를 입력해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e043d-140">If you use [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication, you must provide a user name and password.</span></span>  
  
 <span data-ttu-id="e043d-141">**사용자 이름**</span><span class="sxs-lookup"><span data-stu-id="e043d-141">**User name**</span></span>  
 <span data-ttu-id="e043d-142">서버에 연결할 때 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인증에 사용할 사용자 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="e043d-142">Type the user name that [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication will use to connect to the server.</span></span>  
  
 <span data-ttu-id="e043d-143">**암호**</span><span class="sxs-lookup"><span data-stu-id="e043d-143">**Password**</span></span>  
 <span data-ttu-id="e043d-144">서버에 연결할 때 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인증에 사용할 암호를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="e043d-144">Type the password that [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication will use to connect to the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e043d-145">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e043d-145">See Also</span></span>  
 [<span data-ttu-id="e043d-146">Integration Services 패키지 업그레이드</span><span class="sxs-lookup"><span data-stu-id="e043d-146">Upgrade Integration Services Packages</span></span>](install-windows/upgrade-integration-services-packages.md)  
  
  
