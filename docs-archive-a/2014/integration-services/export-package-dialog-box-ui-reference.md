---
title: 패키지 내보내기 대화 상자 UI 참조 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.dtsserver.exportpackage.f1
helpviewer_keywords:
- Export Package dialog box
ms.assetid: 3742fe8a-ef57-444d-b2fb-cb25d16bae97
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8aedb771dc61fca737ba3841e65b8cb8655d173e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743399"
---
# <a name="export-package-dialog-box-ui-reference"></a><span data-ttu-id="b0f05-102">패키지 내보내기 대화 상자 UI 참조</span><span class="sxs-lookup"><span data-stu-id="b0f05-102">Export Package Dialog Box UI Reference</span></span>
  <span data-ttu-id="b0f05-103">**에서 사용 가능한** 패키지 내보내기 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]대화 상자를 사용하여 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 패키지를 다른 위치로 내보내고 필요에 따라 패키지의 보호 수준을 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b0f05-103">Use the **Export Package** dialog box, available in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], to export a [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package to a different location and optionally, modify the protection level of the package.</span></span>  
  
## <a name="options"></a><span data-ttu-id="b0f05-104">옵션</span><span class="sxs-lookup"><span data-stu-id="b0f05-104">Options</span></span>  
 <span data-ttu-id="b0f05-105">**패키지 위치**</span><span class="sxs-lookup"><span data-stu-id="b0f05-105">**Package location**</span></span>  
 <span data-ttu-id="b0f05-106">패키지를 내보낼 스토리지 유형을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b0f05-106">Select the type of storage to export the package to.</span></span> <span data-ttu-id="b0f05-107">다음 옵션을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b0f05-107">The following options are available:</span></span>  
  
 <span data-ttu-id="b0f05-108">**SQL Server**</span><span class="sxs-lookup"><span data-stu-id="b0f05-108">**SQL Server**</span></span>  
  
 <span data-ttu-id="b0f05-109">**파일 시스템**</span><span class="sxs-lookup"><span data-stu-id="b0f05-109">**File System**</span></span>  
  
 <span data-ttu-id="b0f05-110">**SSIS 패키지 스토리지**</span><span class="sxs-lookup"><span data-stu-id="b0f05-110">**SSIS Package Storage**</span></span>  
  
 <span data-ttu-id="b0f05-111">**Server**</span><span class="sxs-lookup"><span data-stu-id="b0f05-111">**Server**</span></span>  
 <span data-ttu-id="b0f05-112">서버 이름을 입력하거나 목록에서 서버를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b0f05-112">Type a server name or select a server from the list.</span></span>  
  
 <span data-ttu-id="b0f05-113">**인증**</span><span class="sxs-lookup"><span data-stu-id="b0f05-113">**Authentication**</span></span>  
 <span data-ttu-id="b0f05-114">Windows 인증 또는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인증을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b0f05-114">Select Windows Authentication or [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="b0f05-115">이 옵션은 스토리지 위치가 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]인 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b0f05-115">This option is available only if the storage location is [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="b0f05-116">가능하면 Windows 인증을 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="b0f05-116">Whenever possible, use Windows Authentication.</span></span>  
  
 <span data-ttu-id="b0f05-117">**인증 유형**</span><span class="sxs-lookup"><span data-stu-id="b0f05-117">**Authentication type**</span></span>  
 <span data-ttu-id="b0f05-118">인증 유형을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b0f05-118">Select an authentication type.</span></span>  
  
 <span data-ttu-id="b0f05-119">**사용자 이름**</span><span class="sxs-lookup"><span data-stu-id="b0f05-119">**User name**</span></span>  
 <span data-ttu-id="b0f05-120">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인증을 사용하는 경우 사용자 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="b0f05-120">If using [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication, provide a user name.</span></span>  
  
 <span data-ttu-id="b0f05-121">**암호**</span><span class="sxs-lookup"><span data-stu-id="b0f05-121">**Password**</span></span>  
 <span data-ttu-id="b0f05-122">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인증을 사용하는 경우 암호를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="b0f05-122">If using [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication, provide a password.</span></span>  
  
 <span data-ttu-id="b0f05-123">**패키지 경로**</span><span class="sxs-lookup"><span data-stu-id="b0f05-123">**Package path**</span></span>  
 <span data-ttu-id="b0f05-124">패키지 경로를 입력하거나 찾아보기 단추 **(...)** 를 클릭한 다음, 패키지를 저장할 폴더를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="b0f05-124">Type the package path, or click the browse button **(...)** and locate the folder in which to store the package.</span></span>  
  
 <span data-ttu-id="b0f05-125">**보호 수준**</span><span class="sxs-lookup"><span data-stu-id="b0f05-125">**Protection level**</span></span>  
 <span data-ttu-id="b0f05-126">찾아보기 단추 **(...)** 를 클릭한 다음, **패키지 보호 수준** 대화 상자에서 보호 수준을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="b0f05-126">Click the browse button **(...)** and update the protection level in the **Package Protection Level** dialog box.</span></span> <span data-ttu-id="b0f05-127">자세한 내용은 [패키지 및 프로젝트 보호 수준 대화 상자](../../2014/integration-services/package-and-project-protection-level-dialog-box.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b0f05-127">For more information, see [Package and Project Protection Level Dialog Box](../../2014/integration-services/package-and-project-protection-level-dialog-box.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0f05-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b0f05-128">See Also</span></span>  
 <span data-ttu-id="b0f05-129">[패키지 복사본 저장](../../2014/integration-services/save-copy-of-package.md) </span><span class="sxs-lookup"><span data-stu-id="b0f05-129">[Save Copy of Package](../../2014/integration-services/save-copy-of-package.md) </span></span>  
 <span data-ttu-id="b0f05-130">[패키지 가져오기 대화 상자 UI 참조](../../2014/integration-services/import-package-dialog-box-ui-reference.md) </span><span class="sxs-lookup"><span data-stu-id="b0f05-130">[Import Package Dialog Box UI Reference](../../2014/integration-services/import-package-dialog-box-ui-reference.md) </span></span>  
 <span data-ttu-id="b0f05-131">[패키지 저장](save-packages.md) </span><span class="sxs-lookup"><span data-stu-id="b0f05-131">[Save Packages](save-packages.md) </span></span>  
 [<span data-ttu-id="b0f05-132">패키지 가져오기 및 내보내기&#40;SSIS 서비스&#41;</span><span class="sxs-lookup"><span data-stu-id="b0f05-132">Import and Export Packages &#40;SSIS Service&#41;</span></span>](../../2014/integration-services/import-and-export-packages-ssis-service.md)  
  
  
