---
title: SSIS 패키지 업그레이드 마법사를 사용하여 Integration Services 패키지 업그레이드 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Integration Services packages, upgrading
- upgrading Integration Services packages
ms.assetid: 9359275a-48f5-4d1e-8ae7-e797759e3ccf
author: chugugrace
ms.author: chugu
ms.openlocfilehash: bcafd1c9750d8333639ca2d315512a2c2b8759c0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651184"
---
# <a name="upgrade-integration-services-packages-using-the-ssis-package-upgrade-wizard"></a><span data-ttu-id="c1dd2-102">SSIS 패키지 업그레이드 마법사를 사용하여 Integration Services 패키지 업그레이드</span><span class="sxs-lookup"><span data-stu-id="c1dd2-102">Upgrade Integration Services Packages Using the SSIS Package Upgrade Wizard</span></span>
  <span data-ttu-id="c1dd2-103">이전 버전의 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 에서 만들어진 패키지를 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 에서 사용되는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 형식으로 업그레이드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1dd2-103">You can upgrade packages that were created in earlier versions of [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] to the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] format that [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] uses.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="c1dd2-104">는 이 과정을 돕는 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 패키지 업그레이드 마법사를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="c1dd2-104">provides the [!INCLUDE[ssIS](../../includes/ssis-md.md)] Package Upgrade Wizard to help in this process.</span></span> <span data-ttu-id="c1dd2-105">원래 패키지를 백업하도록 마법사를 구성할 수 있으므로 업그레이드에 문제가 있을 경우 원래 패키지를 계속 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1dd2-105">Because you can configure the wizard to backup up your original packages, you can continue to use the original packages if you experience upgrade difficulties.</span></span>  
  
 <span data-ttu-id="c1dd2-106">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 패키지 업그레이드 마법사는 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 가 설치될 때 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="c1dd2-106">The [!INCLUDE[ssIS](../../includes/ssis-md.md)] Package Upgrade Wizard is installed when [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] is installed.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c1dd2-107">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 패키지 업그레이드 마법사는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Standard, Enterprise 및 Developer Edition에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1dd2-107">The [!INCLUDE[ssIS](../../includes/ssis-md.md)] Package Upgrade Wizard is available in the Standard, Enterprise, and Developer Editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="c1dd2-108">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 패키지를 업그레이드하는 방법은 [Integration Services 패키지 업그레이드](upgrade-integration-services-packages.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c1dd2-108">For more information about how to upgrade [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages, see [Upgrade Integration Services Packages](upgrade-integration-services-packages.md).</span></span>  
  
 <span data-ttu-id="c1dd2-109">이 항목의 나머지 부분에서는 마법사를 실행하고 원래 패키지를 백업하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="c1dd2-109">The remainder of this topic describes how to run the wizard and back up the original packages.</span></span>  
  
## <a name="running-the-ssis-package-upgrade-wizard"></a><span data-ttu-id="c1dd2-110">SSIS 패키지 업그레이드 마법사 실행</span><span class="sxs-lookup"><span data-stu-id="c1dd2-110">Running the SSIS Package Upgrade Wizard</span></span>  
 <span data-ttu-id="c1dd2-111">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 패키지 업그레이드 마법사는 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]또는 명령줄에서 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1dd2-111">You can run the [!INCLUDE[ssIS](../../includes/ssis-md.md)] Package Upgrade Wizard from [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], from [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], or at the command prompt.</span></span>  
  
#### <a name="to-run-the-wizard-from-sql-server-data-tools"></a><span data-ttu-id="c1dd2-112">SQL Server Data Tools에서 마법사를 실행하려면</span><span class="sxs-lookup"><span data-stu-id="c1dd2-112">To run the wizard from SQL Server Data Tools</span></span>  
  
1.  <span data-ttu-id="c1dd2-113">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]에서 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 프로젝트를 만들거나 엽니다.</span><span class="sxs-lookup"><span data-stu-id="c1dd2-113">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], create or open an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project.</span></span>  
  
2.  <span data-ttu-id="c1dd2-114">솔루션 탐색기에서 **SSIS 패키지** 노드를 마우스 오른쪽 단추로 클릭하고 **모든 패키지 업그레이드** 를 클릭하여 이 노드의 모든 패키지를 업그레이드합니다.</span><span class="sxs-lookup"><span data-stu-id="c1dd2-114">In Solution Explorer, right-click the **SSIS Packages** node, and then click **Upgrade All Packages** to upgrade all the packages under this node.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c1dd2-115">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 또는 [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)] 패키지가 포함된 [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)] 프로젝트를 열면 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]는 자동으로 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 패키지 업그레이드 마법사를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="c1dd2-115">When you open an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project that contains [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)] or [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)] packages, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] automatically opens the [!INCLUDE[ssIS](../../includes/ssis-md.md)] Package Upgrade Wizard.</span></span>  
  
#### <a name="to-run-the-wizard-from-sql-server-management-studio"></a><span data-ttu-id="c1dd2-116">SQL Server Management Studio에서 마법사를 실행하려면</span><span class="sxs-lookup"><span data-stu-id="c1dd2-116">To run the wizard from SQL Server Management Studio</span></span>  
  
-   <span data-ttu-id="c1dd2-117">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]에 연결하고 **저장된 패키지** 노드를 확장하고 **파일 시스템** 또는 **MSDB** 노드를 마우스 오른쪽 단추로 클릭한 다음 **패키지 업그레이드**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c1dd2-117">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], expand the **Stored Packages** node, and right-click the **File System** or **MSDB** node, and then click **Upgrade Packages**.</span></span>  
  
#### <a name="to-run-the-wizard-at-the-command-prompt"></a><span data-ttu-id="c1dd2-118">명령 프롬프트에서 마법사를 실행하려면</span><span class="sxs-lookup"><span data-stu-id="c1dd2-118">To run the wizard at the command prompt</span></span>  
  
-   <span data-ttu-id="c1dd2-119">명령 프롬프트에서 **C:\Program FILES\MICROSOFT SQL Server\120\DTS\Binn** 폴더에 있는 SSISUpgrade.exe 파일을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1dd2-119">At the command prompt, run the SSISUpgrade.exe file from the **C:\Program Files\Microsoft SQL Server\120\DTS\Binn** folder.</span></span>  
  
## <a name="backing-up-the-original-packages"></a><span data-ttu-id="c1dd2-120">원래 패키지 백업</span><span class="sxs-lookup"><span data-stu-id="c1dd2-120">Backing Up the Original Packages</span></span>  
 <span data-ttu-id="c1dd2-121">원래 패키지를 백업하려면 원래 패키지와 업그레이드된 패키지가 파일 시스템의 같은 폴더에 저장되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1dd2-121">To back up the original packages, both the original packages and the upgraded packages must be stored in the same folder in the file system.</span></span> <span data-ttu-id="c1dd2-122">마법사를 실행하는 방법에 따라 이 스토리지 위치는 자동으로 선택될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1dd2-122">Depending on how you run the wizard, this storage location might be automatically selected.</span></span>  
  
-   <span data-ttu-id="c1dd2-123">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 에서 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]패키지 업그레이드 마법사를 실행하면 자동으로 원래 패키지와 업그레이드된 패키지가 파일 시스템의 같은 폴더에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="c1dd2-123">When you run the [!INCLUDE[ssIS](../../includes/ssis-md.md)] Package Upgrade Wizard from [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], the wizard automatically stores both the original packages and upgraded packages in the same folder in the file system.</span></span>  
  
-   <span data-ttu-id="c1dd2-124">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 또는 명령 프롬프트에서 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 패키지 업그레이드 마법사를 실행하면 원래 패키지와 업그레이드된 패키지에 대해 다른 스토리지 위치를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1dd2-124">When you run the [!INCLUDE[ssIS](../../includes/ssis-md.md)] Package Upgrade Wizard from [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or at the command prompt, you can specify different storage locations for the original and upgraded packages.</span></span> <span data-ttu-id="c1dd2-125">원래 패키지를 백업하려면 원본 패키지와 업그레이드된 패키지가 파일 시스템의 같은 폴더에 저장되도록 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1dd2-125">To back up the original packages, make sure to specify that both the original and upgraded packages are stored in the same folder in the file system.</span></span> <span data-ttu-id="c1dd2-126">다른 스토리지 옵션을 지정하면 마법사는 원래 패키지를 백업할 수 없게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c1dd2-126">If you specify any other storage options, the wizard will not be able to back up the original packages.</span></span>  
  
 <span data-ttu-id="c1dd2-127">마법사는 원래 패키지를 백업할 때 **SSISBackupFolder** 폴더에 원래 패키지의 복사본을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="c1dd2-127">When the wizard backs up the original packages, the wizard stores a copy of the original packages in an **SSISBackupFolder** folder.</span></span> <span data-ttu-id="c1dd2-128">마법사는 원래 패키지 및 업그레이드된 패키지가 포함된 폴더에 하위 폴더로 이 **SSISBackupFolder** 폴더를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c1dd2-128">The wizard creates this **SSISBackupFolder** folder as a subfolder to the folder that contains the original packages and the upgraded packages.</span></span>  
  
#### <a name="to-back-up-the-original-packages-in-sql-server-management-studio-or-at-the-command-prompt"></a><span data-ttu-id="c1dd2-129">SQL Server Management Studio 또는 명령 프롬프트에서 원래 패키지를 백업하려면</span><span class="sxs-lookup"><span data-stu-id="c1dd2-129">To back up the original packages in SQL Server Management Studio or at the command prompt</span></span>  
  
1.  <span data-ttu-id="c1dd2-130">파일 시스템의 한 위치에 원래 패키지를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="c1dd2-130">Save the original packages to a location on the file system.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c1dd2-131">마법사의 백업 옵션은 파일 시스템에 저장된 패키지에서만 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="c1dd2-131">The backup option in the wizard only works with packages that have been stored to the file system.</span></span>  
  
2.  <span data-ttu-id="c1dd2-132">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 또는 명령 프롬프트에서 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 패키지 업그레이드 마법사를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="c1dd2-132">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or at the command prompt, run the [!INCLUDE[ssIS](../../includes/ssis-md.md)] Package Upgrade Wizard.</span></span>  
  
3.  <span data-ttu-id="c1dd2-133">마법사의 **원본 위치 선택** 페이지에서 **패키지 원본** 속성을 **파일 시스템**으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="c1dd2-133">On the **Select Source Location** page of the wizard, set the **Package source** property to **File System**.</span></span>  
  
4.  <span data-ttu-id="c1dd2-134">마법사의 **대상 위치 선택** 페이지에서 **원본 위치에 저장** 을 선택하여 업그레이드된 패키지를 원래 패키지 같은 위치에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="c1dd2-134">On the **Select Destination Location** page of the wizard, select **Save to source location** tosave the upgraded packages to the same location as the original packages.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c1dd2-135">마법사의 백업 옵션은 업그레이드된 패키지가 원래 패키지와 같은 폴더에 저장되어 있는 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1dd2-135">The backup option in the wizard is available only when the upgraded packages are stored in the same folder as the original packages.</span></span>  
  
5.  <span data-ttu-id="c1dd2-136">마법사의 **패키지 관리 옵션 선택** 페이지에서 **원래 패키지 백업** 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c1dd2-136">On the **Select Package Management Options** page of the wizard, select the **Backup original packages** option.</span></span>  
  
#### <a name="to-back-up-the-original-packages-in-sql-server-data-tools"></a><span data-ttu-id="c1dd2-137">SQL Server Data Tools에서 원래 패키지를 백업하려면</span><span class="sxs-lookup"><span data-stu-id="c1dd2-137">To back up the original packages in SQL Server Data Tools</span></span>  
  
1.  <span data-ttu-id="c1dd2-138">파일 시스템의 한 위치에 원래 패키지를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="c1dd2-138">Save the original packages to a location on the file system.</span></span>  
  
2.  <span data-ttu-id="c1dd2-139">마법사의 **패키지 관리 옵션 선택** 페이지에서 **원래 패키지 백업** 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c1dd2-139">On the **Select Package Management Options** page of the wizard, select the **Backup original packages** option.</span></span>  
  
    > [!WARNING]  
    >  <span data-ttu-id="c1dd2-140">마법사를 자동으로 실행하는 [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)]에서 [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)] 또는 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 프로젝트를 열면 **원래 패키지 백업** 옵션이 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c1dd2-140">The **Backup original packages** option is not displayed when you open a [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)] or [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)] project in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], which automatically launches the wizard.</span></span>  
  
3.  <span data-ttu-id="c1dd2-141">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]에서 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 패키지 업그레이드 마법사를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="c1dd2-141">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], run the [!INCLUDE[ssIS](../../includes/ssis-md.md)] Package Upgrade Wizard.</span></span>  
  
  
