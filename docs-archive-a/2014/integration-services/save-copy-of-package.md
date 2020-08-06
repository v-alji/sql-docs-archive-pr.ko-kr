---
title: 패키지 복사본 저장 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.savecopyas.f1
helpviewer_keywords:
- Save Copy of Package dialog box
ms.assetid: 7b44c0d7-d8fa-4491-8836-0899f621d3a8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f0a685d8b38299e1ba1d03c4ec8c1052cc957dbb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738517"
---
# <a name="save-copy-of-package"></a><span data-ttu-id="469f4-102">패키지 복사본 저장</span><span class="sxs-lookup"><span data-stu-id="469f4-102">Save Copy of Package</span></span>
  <span data-ttu-id="469f4-103">**에서 사용할 수 있는** 패키지 복사본 저장 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]대화 상자를 통해 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 의 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 패키지 복사본을 다른 위치에 저장하고 필요에 따라 패키지의 보호 수준을 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="469f4-103">Use the **Save Copy of Package** dialog box, available in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], to save a copy of an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package from [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] to a different location and, optionally, modify the protection level of the package.</span></span>  
  
## <a name="options"></a><span data-ttu-id="469f4-104">옵션</span><span class="sxs-lookup"><span data-stu-id="469f4-104">Options</span></span>  
 <span data-ttu-id="469f4-105">**패키지 위치**</span><span class="sxs-lookup"><span data-stu-id="469f4-105">**Package location**</span></span>  
 <span data-ttu-id="469f4-106">패키지 복사본을 저장할 스토리지 위치 유형을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="469f4-106">Select the type of storage location in which to save the package copy.</span></span> <span data-ttu-id="469f4-107">다음 옵션을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="469f4-107">The following options are available:</span></span>  
  
 <span data-ttu-id="469f4-108">**SQL Server**</span><span class="sxs-lookup"><span data-stu-id="469f4-108">**SQL Server**</span></span>  
  
 <span data-ttu-id="469f4-109">**파일 시스템**</span><span class="sxs-lookup"><span data-stu-id="469f4-109">**File System**</span></span>  
  
 <span data-ttu-id="469f4-110">**SSIS 패키지 저장소**</span><span class="sxs-lookup"><span data-stu-id="469f4-110">**SSIS Package Store**</span></span>  
  
 <span data-ttu-id="469f4-111">**Server**</span><span class="sxs-lookup"><span data-stu-id="469f4-111">**Server**</span></span>  
 <span data-ttu-id="469f4-112">서버 이름을 입력하거나 목록에서 서버를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="469f4-112">Type a server name or select a server from the list.</span></span> <span data-ttu-id="469f4-113">이 옵션은 스토리지 위치가 **SQL Server** 또는 **SSIS 패키지 저장소**인 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="469f4-113">This option is available only if the storage location is **SQL Server** or **SSIS Package Store**.</span></span>  
  
 <span data-ttu-id="469f4-114">**인증**</span><span class="sxs-lookup"><span data-stu-id="469f4-114">**Authentication**</span></span>  
 <span data-ttu-id="469f4-115">Windows 인증 또는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인증을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="469f4-115">Select Windows Authentication or [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="469f4-116">이 옵션은 스토리지 위치가 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]인 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="469f4-116">This option is available only if the storage location is [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="469f4-117">가능하면 Windows 인증을 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="469f4-117">Whenever possible use Windows Authentication.</span></span>  
  
 <span data-ttu-id="469f4-118">**인증 유형**</span><span class="sxs-lookup"><span data-stu-id="469f4-118">**Authentication type**</span></span>  
 <span data-ttu-id="469f4-119">인증 유형을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="469f4-119">Select an authentication type.</span></span>  
  
 <span data-ttu-id="469f4-120">**사용자 이름**</span><span class="sxs-lookup"><span data-stu-id="469f4-120">**User name**</span></span>  
 <span data-ttu-id="469f4-121">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인증을 사용하는 경우 사용자 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="469f4-121">If using [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication, provide a user name.</span></span>  
  
 <span data-ttu-id="469f4-122">**암호**</span><span class="sxs-lookup"><span data-stu-id="469f4-122">**Password**</span></span>  
 <span data-ttu-id="469f4-123">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인증을 사용하는 경우 암호를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="469f4-123">If using [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication, provide a password.</span></span>  
  
 <span data-ttu-id="469f4-124">**패키지 경로**</span><span class="sxs-lookup"><span data-stu-id="469f4-124">**Package path**</span></span>  
 <span data-ttu-id="469f4-125">패키지 경로를 입력 하거나 찾아보기 **(...)** 단추를 클릭 하 고 패키지를 저장할 폴더를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="469f4-125">Type the package path, or click the browse **(...)** button and locate the folder in which to store the package.</span></span>  
  
 <span data-ttu-id="469f4-126">**보호 수준**</span><span class="sxs-lookup"><span data-stu-id="469f4-126">**Protection level**</span></span>  
 <span data-ttu-id="469f4-127">찾아보기 **(...)** 단추를 클릭 하 고 **패키지 보호 수준** 대화 상자에서 보호 수준을 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="469f4-127">Click the browse **(...)** button and update the protection level in the **Package Protection Level** dialog box.</span></span> <span data-ttu-id="469f4-128">자세한 내용은 [패키지 및 프로젝트 보호 수준 대화 상자](../../2014/integration-services/package-and-project-protection-level-dialog-box.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="469f4-128">For more information, see [Package and Project Protection Level Dialog Box](../../2014/integration-services/package-and-project-protection-level-dialog-box.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="469f4-129">참고 항목</span><span class="sxs-lookup"><span data-stu-id="469f4-129">See Also</span></span>  
 <span data-ttu-id="469f4-130">[패키지 가져오기 대화 상자 UI 참조](../../2014/integration-services/import-package-dialog-box-ui-reference.md) </span><span class="sxs-lookup"><span data-stu-id="469f4-130">[Import Package Dialog Box UI Reference](../../2014/integration-services/import-package-dialog-box-ui-reference.md) </span></span>  
 <span data-ttu-id="469f4-131">[패키지 내보내기 대화 상자 UI 참조](../../2014/integration-services/export-package-dialog-box-ui-reference.md) </span><span class="sxs-lookup"><span data-stu-id="469f4-131">[Export Package Dialog Box UI Reference](../../2014/integration-services/export-package-dialog-box-ui-reference.md) </span></span>  
 <span data-ttu-id="469f4-132">[패키지 저장](save-packages.md) </span><span class="sxs-lookup"><span data-stu-id="469f4-132">[Save Packages](save-packages.md) </span></span>  
 [<span data-ttu-id="469f4-133">패키지 가져오기 및 내보내기&#40;SSIS 서비스&#41;</span><span class="sxs-lookup"><span data-stu-id="469f4-133">Import and Export Packages &#40;SSIS Service&#41;</span></span>](../../2014/integration-services/import-and-export-packages-ssis-service.md)  
  
  
