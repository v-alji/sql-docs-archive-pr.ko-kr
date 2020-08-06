---
title: 패키지 관리 옵션 선택 (SSIS 패키지 업그레이드 마법사) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.is.upgradewizard.selectpackagemgtoptions.f1
ms.assetid: 810fc020-51cd-43ed-9f35-af99b4f35947
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b5113ad5a1f6758a75742ca58aef04ce92168649
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661236"
---
# <a name="select-package-management-options-ssis-package-upgrade-wizard"></a><span data-ttu-id="e652e-102">패키지 관리 옵션 선택(SSIS 패키지 업그레이드 마법사)</span><span class="sxs-lookup"><span data-stu-id="e652e-102">Select Package Management Options (SSIS Package Upgrade Wizard)</span></span>
  <span data-ttu-id="e652e-103">**패키지 관리 옵션 선택** 페이지를 사용하여 패키지 업그레이드 옵션을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e652e-103">Use the **Select Package Management Options** page to specify options for upgrading packages.</span></span>  
  
 <span data-ttu-id="e652e-104">**SSIS 패키지 업그레이드 마법사를 실행하려면**</span><span class="sxs-lookup"><span data-stu-id="e652e-104">**To run the SSIS Package Upgrade Wizard**</span></span>  
  
-   [<span data-ttu-id="e652e-105">SSIS 패키지 업그레이드 마법사를 사용하여 Integration Services 패키지 업그레이드</span><span class="sxs-lookup"><span data-stu-id="e652e-105">Upgrade Integration Services Packages Using the SSIS Package Upgrade Wizard</span></span>](install-windows/upgrade-integration-services-packages-using-the-ssis-package-upgrade-wizard.md)  
  
## <a name="options"></a><span data-ttu-id="e652e-106">옵션</span><span class="sxs-lookup"><span data-stu-id="e652e-106">Options</span></span>  
 <span data-ttu-id="e652e-107">**새 공급자 이름을 사용하도록 연결 문자열 업데이트**</span><span class="sxs-lookup"><span data-stu-id="e652e-107">**Update connection strings to use new provider names**</span></span>  
 <span data-ttu-id="e652e-108">연결 문자열이 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]현재 버전의 다음 공급자에 대해 다음 이름을 사용하도록 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="e652e-108">Update the connection strings to use the names for the following providers for the current release of [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="e652e-109">OLE DB Provider for [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e652e-109">OLE DB Provider for [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]</span></span>  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="e652e-110">Native Client</span><span class="sxs-lookup"><span data-stu-id="e652e-110">Native Client</span></span>  
  
 <span data-ttu-id="e652e-111">[!INCLUDE[ssIS](../includes/ssis-md.md)] 패키지 업그레이드 마법사는 연결 관리자에 저장된 연결 문자열만 업데이트하며</span><span class="sxs-lookup"><span data-stu-id="e652e-111">The [!INCLUDE[ssIS](../includes/ssis-md.md)] Package Upgrade Wizard updates only connection strings that are stored in connection managers.</span></span> <span data-ttu-id="e652e-112">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 식 언어 또는 스크립트 태스크의 코드를 사용하여 동적으로 생성된 연결 문자열은 업데이트하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e652e-112">The wizard does not update connection strings that are constructed dynamically by using the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] expression language, or by using code in a Script task.</span></span>  
  
 <span data-ttu-id="e652e-113">**업그레이드 패키지 유효성 검사**</span><span class="sxs-lookup"><span data-stu-id="e652e-113">**Validate upgrade packages**</span></span>  
 <span data-ttu-id="e652e-114">업그레이드 패키지의 유효성을 검사하고 유효성 검사를 통과한 업그레이드 패키지만 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="e652e-114">Validate the upgrade packages and save only those upgrade packages that pass validation.</span></span>  
  
 <span data-ttu-id="e652e-115">이 옵션을 선택하지 않으면 마법사는 업그레이드 패키지의 유효성을 검사하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e652e-115">If you do not select this option, the wizard will not validate upgrade packages.</span></span> <span data-ttu-id="e652e-116">따라서 마법사는 패키지의 유효성 여부와 관계없이 모든 업그레이드 패키지를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="e652e-116">Therefore, the wizard will save all upgrade packages, regardless of whether the packages are valid or not.</span></span> <span data-ttu-id="e652e-117">마법사는 마법사의 **대상 위치 선택** 페이지에서 지정한 대상에 업그레이드 패키지를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="e652e-117">The wizard saves upgrade packages to the destination that is specified on the **SelectDestination Location** page of the wizard.</span></span>  
  
 <span data-ttu-id="e652e-118">유효성 검사로 인해 업그레이드 프로세스의 소요 시간이 늘어납니다.</span><span class="sxs-lookup"><span data-stu-id="e652e-118">Validation adds time to the upgrade process.</span></span> <span data-ttu-id="e652e-119">성공적으로 업그레이드될 가능성이 높은 큰 패키지의 경우에는 이 옵션을 선택하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="e652e-119">We recommend that you do not select this option for large packages that are likely to be upgraded successfully.</span></span>  
  
 <span data-ttu-id="e652e-120">**새 패키지 ID 만들기**</span><span class="sxs-lookup"><span data-stu-id="e652e-120">**Create new package IDs**</span></span>  
 <span data-ttu-id="e652e-121">업그레이드 패키지의 새 패키지 ID를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e652e-121">Create new package IDs for the upgrade packages.</span></span>  
  
 <span data-ttu-id="e652e-122">**패키지 업그레이드 실패 시 업그레이드 프로세스 계속**</span><span class="sxs-lookup"><span data-stu-id="e652e-122">**Continue upgrade process when a package upgrade fails**</span></span>  
 <span data-ttu-id="e652e-123">특정 패키지를 업그레이드할 수 없는 경우 [!INCLUDE[ssIS](../includes/ssis-md.md)] 패키지 업그레이드 마법사가 나머지 패키지를 계속 업그레이드하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e652e-123">Specify that when a package cannot be upgraded, the [!INCLUDE[ssIS](../includes/ssis-md.md)] Package Upgrade Wizard continues to upgrade the remaining packages.</span></span>  
  
 <span data-ttu-id="e652e-124">**패키지 이름 충돌**</span><span class="sxs-lookup"><span data-stu-id="e652e-124">**Package name conflicts**</span></span>  
 <span data-ttu-id="e652e-125">마법사가 동일한 이름의 패키지를 처리하는 방법을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e652e-125">Specify how the wizard should handle packages that have the same name.</span></span> <span data-ttu-id="e652e-126">이 옵션에는 다음 표에 나열된 값이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e652e-126">This option has the values listed in the following table.</span></span>  
  
 <span data-ttu-id="e652e-127">**기존 패키지 파일 덮어쓰기**</span><span class="sxs-lookup"><span data-stu-id="e652e-127">**Overwrite existing package files**</span></span>  
 <span data-ttu-id="e652e-128">기존 패키지를 동일한 이름의 업그레이드 패키지로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="e652e-128">Replaces the existing package with the upgrade package of the same name.</span></span>  
  
 <span data-ttu-id="e652e-129">**업그레이드 패키지 이름에 숫자 접미사 추가**</span><span class="sxs-lookup"><span data-stu-id="e652e-129">**Add numeric suffixes to upgrade package names**</span></span>  
 <span data-ttu-id="e652e-130">업그레이드 패키지의 이름에 숫자 접미사를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="e652e-130">Adds a numeric suffix to the name of the upgrade package.</span></span>  
  
 <span data-ttu-id="e652e-131">**패키지 업그레이드 안 함**</span><span class="sxs-lookup"><span data-stu-id="e652e-131">**Do not upgrade packages**</span></span>  
 <span data-ttu-id="e652e-132">패키지가 업그레이드되지 않도록 하고 마법사 완료 시 오류를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="e652e-132">Stops the packages from being upgraded and displays an error when you complete the wizard.</span></span>  
  
 <span data-ttu-id="e652e-133">이러한 옵션은 마법사의 **대상 위치 선택** 페이지에서 **원본 위치에 저장** 옵션을 선택한 경우 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e652e-133">These options are not available when you select the **Save to source location** option on the **Select Destination Location** page of the wizard.</span></span>  
  
 <span data-ttu-id="e652e-134">**구성 무시**</span><span class="sxs-lookup"><span data-stu-id="e652e-134">**Ignore Configurations**</span></span>  
 <span data-ttu-id="e652e-135">패키지 업그레이드를 사용 하는 동안 패키지 구성을 로드하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e652e-135">Does not load package configurations during the package upgrade.</span></span> <span data-ttu-id="e652e-136">이 옵션을 선택하면 패키지를 업그레이드 하는 데 필요한 시간이 줄어듭니다.</span><span class="sxs-lookup"><span data-stu-id="e652e-136">Selecting this option reduces the time required to upgrade the package.</span></span>  
  
 <span data-ttu-id="e652e-137">**원래 패키지 백업**</span><span class="sxs-lookup"><span data-stu-id="e652e-137">**Backup original packages**</span></span>  
 <span data-ttu-id="e652e-138">마법사가 **SSISBackupFolder** 폴더에 원래 패키지를 백업하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="e652e-138">Have the wizard back up the original packages to an **SSISBackupFolder** folder.</span></span> <span data-ttu-id="e652e-139">마법사는 원래 패키지 및 업그레이드된 패키지가 포함된 폴더에 하위 폴더로 **SSISBackupFolder** 폴더를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e652e-139">The wizard creates the **SSISBackupFolder** folder as a subfolder to the folder that contains the original packages and the upgraded packages.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e652e-140">이 옵션은 원래 패키지 및 업그레이드된 패키지가 파일 시스템의 동일한 폴더에 저장되도록 지정한 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e652e-140">This option is available only when you specify that the original packages and the upgraded packages are stored in the file system and in the same folder.</span></span>  
  
 <span data-ttu-id="e652e-141">자세한 내용은 [SSIS 패키지 업그레이드 마법사를 사용하여 Integration Services 패키지 업그레이드](install-windows/upgrade-integration-services-packages-using-the-ssis-package-upgrade-wizard.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e652e-141">For more information, see [Upgrade Integration Services Packages Using the SSIS Package Upgrade Wizard](install-windows/upgrade-integration-services-packages-using-the-ssis-package-upgrade-wizard.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e652e-142">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e652e-142">See Also</span></span>  
 [<span data-ttu-id="e652e-143">Integration Services 패키지 업그레이드</span><span class="sxs-lookup"><span data-stu-id="e652e-143">Upgrade Integration Services Packages</span></span>](install-windows/upgrade-integration-services-packages.md)  
  
  
