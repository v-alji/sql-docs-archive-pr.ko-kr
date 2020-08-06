---
title: 대상 위치 선택 (SSIS 패키지 업그레이드 마법사) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.is.upgradewizard.selectdestinationlocation.f1
ms.assetid: 89274a71-0ffe-4889-84df-f5a7d78459ef
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9411157434c3dbb9fb033f7b63b5e6041fd8f75d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661238"
---
# <a name="select-destination-location-ssis-package-upgrade-wizard"></a><span data-ttu-id="5e55a-102">대상 위치 선택(SSIS 패키지 업그레이드 마법사)</span><span class="sxs-lookup"><span data-stu-id="5e55a-102">Select Destination Location (SSIS Package Upgrade Wizard)</span></span>
  <span data-ttu-id="5e55a-103">**대상 위치 선택** 페이지를 사용하여 업그레이드된 패키지를 저장할 대상을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e55a-103">Use the **Select Destination Location** page to specify the destination to which to save the upgraded packages.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5e55a-104">이 페이지는 [!INCLUDE[ssIS](../includes/ssis-md.md)] 또는 명령 프롬프트에서 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 패키지 업그레이드 마법사를 실행한 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e55a-104">This page is only available when you run the [!INCLUDE[ssIS](../includes/ssis-md.md)] Package Upgrade Wizard from [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] or at the command prompt.</span></span>  
  
 <span data-ttu-id="5e55a-105">**SSIS 패키지 업그레이드 마법사를 실행하려면**</span><span class="sxs-lookup"><span data-stu-id="5e55a-105">**To run the SSIS Package Upgrade Wizard**</span></span>  
  
-   [<span data-ttu-id="5e55a-106">SSIS 패키지 업그레이드 마법사를 사용하여 Integration Services 패키지 업그레이드</span><span class="sxs-lookup"><span data-stu-id="5e55a-106">Upgrade Integration Services Packages Using the SSIS Package Upgrade Wizard</span></span>](install-windows/upgrade-integration-services-packages-using-the-ssis-package-upgrade-wizard.md)  
  
## <a name="static-options"></a><span data-ttu-id="5e55a-107">정적 옵션</span><span class="sxs-lookup"><span data-stu-id="5e55a-107">Static Options</span></span>  
 <span data-ttu-id="5e55a-108">**원본 위치에 저장**</span><span class="sxs-lookup"><span data-stu-id="5e55a-108">**Save to source location**</span></span>  
 <span data-ttu-id="5e55a-109">업그레이드된 패키지를 마법사의 **원본 위치 선택** 페이지에서 지정한 것과 동일한 위치에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="5e55a-109">Save the upgraded packages to the same location as specified on the **Select Source Location** page of the wizard.</span></span>  
  
 <span data-ttu-id="5e55a-110">원래 패키지가 파일 시스템에 저장되는 상태에서 마법사가 이러한 패키지를 백업하도록 하려면 **원본 위치에 저장** 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5e55a-110">If the original packages are stored in the file system and you want the wizard to back up those packages, select the **Save to source location** option.</span></span> <span data-ttu-id="5e55a-111">자세한 내용은 [SSIS 패키지 업그레이드 마법사를 사용하여 Integration Services 패키지 업그레이드](install-windows/upgrade-integration-services-packages-using-the-ssis-package-upgrade-wizard.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5e55a-111">For more information, see [Upgrade Integration Services Packages Using the SSIS Package Upgrade Wizard](install-windows/upgrade-integration-services-packages-using-the-ssis-package-upgrade-wizard.md).</span></span>  
  
 <span data-ttu-id="5e55a-112">**새 대상 위치 선택**</span><span class="sxs-lookup"><span data-stu-id="5e55a-112">**Select new destination location**</span></span>  
 <span data-ttu-id="5e55a-113">업그레이드된 패키지를 이 페이지에서 지정한 대상 위치에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="5e55a-113">Save the upgraded packages to the destination location that is specified on this page.</span></span>  
  
 <span data-ttu-id="5e55a-114">**패키지 원본**</span><span class="sxs-lookup"><span data-stu-id="5e55a-114">**Package source**</span></span>  
 <span data-ttu-id="5e55a-115">업그레이드 패키지를 저장할 위치를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5e55a-115">Specify where the upgrade packages are to be stored.</span></span> <span data-ttu-id="5e55a-116">이 옵션에는 다음 표에 나열된 값이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e55a-116">This option has the values listed in the following table.</span></span>  
  
|<span data-ttu-id="5e55a-117">값</span><span class="sxs-lookup"><span data-stu-id="5e55a-117">Value</span></span>|<span data-ttu-id="5e55a-118">Description</span><span class="sxs-lookup"><span data-stu-id="5e55a-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="5e55a-119">**파일 시스템**</span><span class="sxs-lookup"><span data-stu-id="5e55a-119">**File System**</span></span>|<span data-ttu-id="5e55a-120">업그레이드된 패키지를 로컬 컴퓨터의 폴더에 저장함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5e55a-120">Indicates that the upgraded packages are to be saved to a folder on the local computer.</span></span>|  
|<span data-ttu-id="5e55a-121">**SSIS 패키지 저장소**</span><span class="sxs-lookup"><span data-stu-id="5e55a-121">**SSIS Package Store**</span></span>|<span data-ttu-id="5e55a-122">업그레이드된 패키지를 Integration Services 패키지 저장소에 저장함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5e55a-122">Indicates that the upgraded packages are to be saved to the Integration Services package store.</span></span> <span data-ttu-id="5e55a-123">패키지 저장소는 Integration Services 서비스에서 관리하는 파일 시스템 폴더 집합으로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="5e55a-123">The package store consists of the set of file system folders that the Integration Services service manages.</span></span> <span data-ttu-id="5e55a-124">자세한 내용은 [패키지 관리&#40;SSIS 서비스&#41;](service/package-management-ssis-service.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5e55a-124">For more information, see [Package Management &#40;SSIS Service&#41;](service/package-management-ssis-service.md).</span></span><br /><br /> <span data-ttu-id="5e55a-125">이 값을 선택하면 해당 **패키지 원본** 동적 옵션이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="5e55a-125">Selecting this value displays the corresponding **Package source** dynamics options.</span></span>|  
|<span data-ttu-id="5e55a-126">**Microsoft SQL Server**</span><span class="sxs-lookup"><span data-stu-id="5e55a-126">**Microsoft SQL Server**</span></span>|<span data-ttu-id="5e55a-127">업그레이드된 패키지를 기존 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]인스턴스에 저장함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5e55a-127">Indicates that the upgraded packages are to be saved to an existing instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span><br /><br /> <span data-ttu-id="5e55a-128">이 값을 선택하면 해당 **패키지 원본** 동적 옵션이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="5e55a-128">Selecting this value displays the corresponding dynamic **Package source** dynamic options.</span></span>|  
  
 <span data-ttu-id="5e55a-129">**폴더**</span><span class="sxs-lookup"><span data-stu-id="5e55a-129">**Folder**</span></span>  
 <span data-ttu-id="5e55a-130">업그레이드된 패키지를 저장할 폴더의 이름을 입력하거나 **찾아보기** 를 클릭하여 폴더를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="5e55a-130">Type the name of a folder to which the upgraded packages will be saved, or click **Browse** and locate the folder.</span></span>  
  
 <span data-ttu-id="5e55a-131">**찾아보기**</span><span class="sxs-lookup"><span data-stu-id="5e55a-131">**Browse**</span></span>  
 <span data-ttu-id="5e55a-132">업그레이드된 패키지를 저장할 폴더를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="5e55a-132">Browse to locate the folder to which the upgraded packages will be saved.</span></span>  
  
## <a name="package-source-dynamic-options"></a><span data-ttu-id="5e55a-133">패키지 원본 동적 옵션</span><span class="sxs-lookup"><span data-stu-id="5e55a-133">Package Source Dynamic Options</span></span>  
  
### <a name="package-source--ssis-package-store"></a><span data-ttu-id="5e55a-134">패키지 원본 = SSIS 패키지 저장소</span><span class="sxs-lookup"><span data-stu-id="5e55a-134">Package source = SSIS Package Store</span></span>  
 <span data-ttu-id="5e55a-135">**Server**</span><span class="sxs-lookup"><span data-stu-id="5e55a-135">**Server**</span></span>  
 <span data-ttu-id="5e55a-136">업그레이드 패키지를 저장할 서버의 이름을 입력하거나 목록에서 서버를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5e55a-136">Type the name of the server to which the upgrade packages will be saved, or select a server in the list.</span></span>  
  
### <a name="package-source--microsoft-sql-server"></a><span data-ttu-id="5e55a-137">패키지 원본 = Microsoft SQL Server</span><span class="sxs-lookup"><span data-stu-id="5e55a-137">Package source = Microsoft SQL Server</span></span>  
 <span data-ttu-id="5e55a-138">**Server**</span><span class="sxs-lookup"><span data-stu-id="5e55a-138">**Server**</span></span>  
 <span data-ttu-id="5e55a-139">업그레이드 패키지를 저장할 서버의 이름을 입력하거나 목록에서 이 서버를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5e55a-139">Type the name of the server to which the upgrade packages will be saved, or select this server in the list.</span></span>  
  
 <span data-ttu-id="5e55a-140">**Windows 인증 사용**</span><span class="sxs-lookup"><span data-stu-id="5e55a-140">**Use Windows authentication**</span></span>  
 <span data-ttu-id="5e55a-141">Windows 인증을 사용하여 서버에 연결하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5e55a-141">Select to use Windows Authentication to connect to the server.</span></span>  
  
 <span data-ttu-id="5e55a-142">**SQL Server 인증 사용**</span><span class="sxs-lookup"><span data-stu-id="5e55a-142">**Use SQL Server authentication**</span></span>  
 <span data-ttu-id="5e55a-143">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인증을 사용하여 서버에 연결하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5e55a-143">Select to use [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication to connect to the server.</span></span> <span data-ttu-id="5e55a-144">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인증을 사용하는 경우 사용자 이름과 암호를 입력해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e55a-144">If you use [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication, you must provide a user name and password.</span></span>  
  
 <span data-ttu-id="5e55a-145">**사용자 이름**</span><span class="sxs-lookup"><span data-stu-id="5e55a-145">**User name**</span></span>  
 <span data-ttu-id="5e55a-146">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인증을 사용하여 서버에 연결할 때 사용할 사용자 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="5e55a-146">Type the user name to be used when using [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication to connect to the server.</span></span>  
  
 <span data-ttu-id="5e55a-147">**암호**</span><span class="sxs-lookup"><span data-stu-id="5e55a-147">**Password**</span></span>  
 <span data-ttu-id="5e55a-148">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인증을 사용하여 서버에 연결할 때 사용할 암호를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="5e55a-148">Type the password to be used when using [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication to connect to the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e55a-149">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5e55a-149">See Also</span></span>  
 [<span data-ttu-id="5e55a-150">Integration Services 패키지 업그레이드</span><span class="sxs-lookup"><span data-stu-id="5e55a-150">Upgrade Integration Services Packages</span></span>](install-windows/upgrade-integration-services-packages.md)  
  
  
