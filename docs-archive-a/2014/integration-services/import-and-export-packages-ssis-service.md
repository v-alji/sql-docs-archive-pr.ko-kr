---
title: 패키지 가져오기 및 내보내기 (SSIS 서비스) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- packages [Integration Services], importing
- packages [Integration Services], exporting
- importing packages
- exporting packages
ms.assetid: ef18ec11-b536-47d9-abd1-794099f43486
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b69f9d23431ed86f6b84be6857b7104cd8ba3dcc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652950"
---
# <a name="import-and-export-packages-ssis-service"></a><span data-ttu-id="8cc10-102">패키지 가져오기 및 내보내기(SSIS 서비스)</span><span class="sxs-lookup"><span data-stu-id="8cc10-102">Import and Export Packages (SSIS Service)</span></span>
    
> [!IMPORTANT]  
>  <span data-ttu-id="8cc10-103">이 항목에서는 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 패키지를 관리하는 Windows 서비스인 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 서비스에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="8cc10-103">This topic discusses the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service, a Windows service for managing [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] packages.</span></span> [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] <span data-ttu-id="8cc10-104">는 이전 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]버전과의 호환성을 위한 서비스를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="8cc10-104">supports the service for backward compatibility with earlier releases of [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].</span></span> <span data-ttu-id="8cc10-105">[!INCLUDE[ssSQL11](../includes/sssql11-md.md)]부터는 Integration Services 서버의 패키지와 같은 개체를 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8cc10-105">Starting in [!INCLUDE[ssSQL11](../includes/sssql11-md.md)], you can manage objects such as packages on the Integration Services server.</span></span>  
  
 <span data-ttu-id="8cc10-106">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] msdb 데이터베이스의 sysssispackages 테이블 또는 파일 시스템에 패키지를 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8cc10-106">Packages can be saved either in the sysssispackages table in the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] msdb database or in the file system.</span></span>  
  
 <span data-ttu-id="8cc10-107">패키지 저장소는 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 서비스에서 모니터링 및 관리하는 논리 스토리지이며 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 서비스의 구성 파일에 지정된 msdb 데이터베이스 및 파일 시스템 폴더를 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8cc10-107">The package store, which is the logical storage that [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service monitors and manages, can include both the msdb database and the file system folders specified in the configuration file for the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service.</span></span>  
  
 <span data-ttu-id="8cc10-108">다음 유형의 스토리지 간에 패키지를 가져오고 내보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8cc10-108">You can import and export packages between the following storage types:</span></span>  
  
-   <span data-ttu-id="8cc10-109">파일 시스템 내의 파일 시스템 폴더</span><span class="sxs-lookup"><span data-stu-id="8cc10-109">File system folders anywhere in the file system.</span></span>  
  
-   <span data-ttu-id="8cc10-110">SSIS 패키지 저장소 내 폴더.</span><span class="sxs-lookup"><span data-stu-id="8cc10-110">Folders in the SSIS Package Store.</span></span> <span data-ttu-id="8cc10-111">두 기본 폴더의 이름은 각각 File System 및 MSDB입니다.</span><span class="sxs-lookup"><span data-stu-id="8cc10-111">The two default folders are named File System and MSDB.</span></span>  
  
-   <span data-ttu-id="8cc10-112">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] msdb 데이터베이스</span><span class="sxs-lookup"><span data-stu-id="8cc10-112">The [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] msdb database.</span></span>  
  
 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="8cc10-113">를 사용하면 패키지를 가져오고 내보낼 수 있으며 이렇게 하면 패키지의 위치 및 스토리지 형식을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8cc10-113">gives you the ability to import and export packages, and by doing this change the storage format and location of packages.</span></span> <span data-ttu-id="8cc10-114">가져오기 및 내보내기 기능을 사용하여 파일 시스템, 패키지 저장소 또는 msdb 데이터베이스에 패키지를 추가할 수 있으며 하나의 스토리지 형식에서 다른 스토리지 형식으로 패키지를 복사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8cc10-114">Using the import and export features, you can add packages to the file system, package store, or msdb database, and copy packages from one storage format to another.</span></span> <span data-ttu-id="8cc10-115">예를 들어 msdb에 저장된 패키지를 파일 시스템으로 복사할 수 있으며 반대의 경우도 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="8cc10-115">For example, packages saved in msdb can be copied to the file system and vice versa.</span></span>  
  
 <span data-ttu-id="8cc10-116">**dtutil** 명령 프롬프트 유틸리티(dtutil.exe)를 사용하여 패키지를 다른 형식으로 복사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8cc10-116">You can also copy a package to a different format using the **dtutil** command prompt utility (dtutil.exe).</span></span> <span data-ttu-id="8cc10-117">자세한 내용은 [dtutil Utility](dtutil-utility.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8cc10-117">For more information, see [dtutil Utility](dtutil-utility.md).</span></span>  
  
## <a name="to-import-or-export-a-package"></a><span data-ttu-id="8cc10-118">패키지를 가져오거나 내보내려면</span><span class="sxs-lookup"><span data-stu-id="8cc10-118">To import or export a package</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="8cc10-119">이 항목에서는 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 의 일부인 [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)]서비스에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="8cc10-119">This topic discusses the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service that is part of [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)].</span></span> [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] <span data-ttu-id="8cc10-120">는 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 와의 이전 버전 호환성을 위해 [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)]서비스를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="8cc10-120">supports the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service for backward compatibility with [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)].</span></span> <span data-ttu-id="8cc10-121">[!INCLUDE[ssSQL11](../includes/sssql11-md.md)]에서 패키지를 관리하는 방법은 [Integration Services&#40;SSIS&#41; 서버](catalog/integration-services-ssis-server-and-catalog.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8cc10-121">For information about managing packages in [!INCLUDE[ssSQL11](../includes/sssql11-md.md)], see [Integration Services &#40;SSIS&#41; Server](catalog/integration-services-ssis-server-and-catalog.md).</span></span>  
  
 <span data-ttu-id="8cc10-122">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 패키지는 다음과 같은 위치에서 가져오거나 내보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8cc10-122">You can import or export an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package from or to the following locations:</span></span>  
  
-   <span data-ttu-id="8cc10-123">[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인스턴스, 파일 시스템 또는 [!INCLUDE[ssIS](../includes/ssis-md.md)] 패키지 저장소에 저장된 패키지를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8cc10-123">You can import a package that is stored in an instance of [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], in the file system, or in the [!INCLUDE[ssIS](../includes/ssis-md.md)] package store.</span></span> <span data-ttu-id="8cc10-124">가져온 패키지는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 나 [!INCLUDE[ssIS](../includes/ssis-md.md)] 패키지 저장소의 폴더에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="8cc10-124">The imported package is saved to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] or to a folder in the [!INCLUDE[ssIS](../includes/ssis-md.md)] package store.</span></span>  
  
-   <span data-ttu-id="8cc10-125">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]인스턴스, 파일 시스템 또는 [!INCLUDE[ssIS](../includes/ssis-md.md)] 패키지 저장소에 저장된 패키지를 다른 스토리지 형식 또는 위치로 내보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8cc10-125">You can export a package that is stored in an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], the file system, or the [!INCLUDE[ssIS](../includes/ssis-md.md)] Package Store to a different storage format and location.</span></span>  
  
 <span data-ttu-id="8cc10-126">그러나 버전이 다른 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]간에 패키지를 가져오거나 내보내는 경우 다음과 같은 몇 가지 제한 사항이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8cc10-126">However, there are some restrictions on importing and exporting a package between different versions of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="8cc10-127">[!INCLUDE[ssKatmai](../includes/sskatmai-md.md)]인스턴스에서는 [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)]인스턴스에서 패키지를 가져올 수만 있고 [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)]로 패키지를 내보낼 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8cc10-127">On an instance of [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)], you can import packages from an instance of [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)], but you cannot export packages to an instance of [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)].</span></span>  
  
-   <span data-ttu-id="8cc10-128">[!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)]인스턴스에서는 [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)]인스턴스에서 패키지를 가져오거나 인스턴스로 패키지를 내보낼 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8cc10-128">On an instance of [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)], you cannot import packages from, or export packages to, an instance of [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)].</span></span>  
  
 <span data-ttu-id="8cc10-129">다음 절차에서는 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 를 사용하여 패키지를 가져오거나 내보내는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="8cc10-129">The following procedures describe how to use [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to import or export a package.</span></span>  
  
#### <a name="to-import-a-package-by-using-sql-server-management-studio"></a><span data-ttu-id="8cc10-130">SQL Server Management Studio를 사용하여 패키지 가져오려면</span><span class="sxs-lookup"><span data-stu-id="8cc10-130">To import a package by Using SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="8cc10-131">**시작**을 클릭하고 **Microsoft** [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]를 가리킨 다음, **SQL Server Management Studio**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8cc10-131">Click **Start**, point to **Microsoft** [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], and then click **SQL Server Management Studio**.</span></span>  
  
2.  <span data-ttu-id="8cc10-132">**서버에 연결** 대화 상자에서 다음 옵션을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8cc10-132">In the **Connect to Server** dialog box set the following options:</span></span>  
  
    -   <span data-ttu-id="8cc10-133">**서버 유형** 상자에서 **Integration Services**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8cc10-133">In the **Server type** box, select **Integration Services**.</span></span>  
  
    -   <span data-ttu-id="8cc10-134">**서버 이름** 상자에 서버 이름을 입력하거나 **\<Browse for more...>** 를 클릭하여 사용할 서버를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="8cc10-134">In the **Server name** box, provide a server name or click **\<Browse for more...>** and locate the server to use.</span></span>  
  
3.  <span data-ttu-id="8cc10-135">개체 탐색기가 열려 있지 않으면 **보기** 메뉴에서 **개체 탐색기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8cc10-135">If Object Explorer is not open, on the **View** menu, click **Object Explorer**.</span></span>  
  
4.  <span data-ttu-id="8cc10-136">개체 탐색기에서 **저장된 패키지** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="8cc10-136">In Object Explorer, expand the **Stored Packages** folder.</span></span>  
  
5.  <span data-ttu-id="8cc10-137">하위 폴더를 확장하여 패키지를 가져오려는 폴더를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="8cc10-137">Expand the subfolders to locate the folder into which you want to import a package.</span></span>  
  
6.  <span data-ttu-id="8cc10-138">폴더를 마우스 오른쪽 단추로 클릭하고 **패키지 가져오기**를 클릭한 다음</span><span class="sxs-lookup"><span data-stu-id="8cc10-138">Right-click the folder, click **Import Package**.</span></span> <span data-ttu-id="8cc10-139">다음 중 하나를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="8cc10-139">and then do one of the following:</span></span>  
  
    -   <span data-ttu-id="8cc10-140">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]인스턴스에서 가져오려면 **SQL Server** 옵션을 선택한 후 서버를 지정하고 인증 모드를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8cc10-140">To import from an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], select the **SQL Server** option, and then specify the server and select the authentication mode.</span></span> <span data-ttu-id="8cc10-141">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인증을 선택한 경우 사용자 이름과 암호를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="8cc10-141">If you select [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication, provide a user name and a password.</span></span>  
  
         <span data-ttu-id="8cc10-142">찾아보기 단추 **(…)** 를 클릭하고 가져올 패키지를 선택한 후, **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8cc10-142">Click the browse button **(...)**, select the package to import, and then click **OK.**</span></span>  
  
    -   <span data-ttu-id="8cc10-143">파일 시스템에서 가져오려면 **파일 시스템** 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8cc10-143">To import from the file system, select the **File system** option.</span></span>  
  
         <span data-ttu-id="8cc10-144">찾아보기 단추 **(…)** 를 클릭하고 가져올 패키지를 선택한 후, **열기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8cc10-144">Click the browse button **(...)**, select the package to import, and then click **Open.**</span></span>  
  
    -   <span data-ttu-id="8cc10-145">[!INCLUDE[ssIS](../includes/ssis-md.md)] 패키지 저장소에서 가져오려면 **SSIS 패키지 저장소** 옵션을 선택하고 서버를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8cc10-145">To import from the [!INCLUDE[ssIS](../includes/ssis-md.md)] Package Store, select the **SSIS Package Store** option and specify the server.</span></span>  
  
         <span data-ttu-id="8cc10-146">찾아보기 단추 **(…)** 를 클릭하고 가져올 패키지를 선택한 후, **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8cc10-146">Click the browse button **(...)**, select the package to import, and then click **OK.**</span></span>  
  
7.  <span data-ttu-id="8cc10-147">선택적으로 패키지 이름을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="8cc10-147">Optionally, update the package name.</span></span>  
  
8.  <span data-ttu-id="8cc10-148">패키지의 보호 수준을 업데이트하려면 찾아보기 단추 **(…)** 를 클릭하고 **패키지 보호 수준** 대화 상자를 사용하여 다른 보호 수준을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8cc10-148">To update the protection level of the package, click the browse button **(...)** and choose a different protection level by using the **Package Protection Level** dialog box.</span></span> <span data-ttu-id="8cc10-149">**암호로 중요한 데이터 암호화** 또는 **암호로 모든 데이터 암호화** 옵션을 선택한 경우 암호를 입력하고 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="8cc10-149">If the **Encrypt sensitive data with password** or the **Encrypt all data with password** option is selected, type and confirm a password.</span></span>  
  
9. <span data-ttu-id="8cc10-150">**확인** 을 클릭하여 가져오기를 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="8cc10-150">Click **OK** to complete the import.</span></span>  
  
#### <a name="to-export-a-package-by-using-sql-server-management-studio"></a><span data-ttu-id="8cc10-151">SQL Server Management Studio를 사용하여 패키지 내보내려면</span><span class="sxs-lookup"><span data-stu-id="8cc10-151">To export a package by Using SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="8cc10-152">**시작**을 클릭하고 **Microsoft** [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]를 가리킨 다음, **SQL Server Management Studio**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8cc10-152">Click **Start**, point to **Microsoft** [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], and then click **SQL Server Management Studio**.</span></span>  
  
2.  <span data-ttu-id="8cc10-153">**서버에 연결** 대화 상자에서 다음 옵션을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8cc10-153">In the **Connect to Server** dialog box, set the following options:</span></span>  
  
    -   <span data-ttu-id="8cc10-154">**서버 유형** 상자에서 **Integration Services**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8cc10-154">In the **Server type** box, select **Integration Services**.</span></span>  
  
    -   <span data-ttu-id="8cc10-155">**서버 이름** 상자에 서버 이름을 입력하거나 **\<Browse for more...>** 를 클릭하여 사용할 서버를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="8cc10-155">In the **Server name** box, provide a server name or click **\<Browse for more...>** and locate the server to use.</span></span>  
  
3.  <span data-ttu-id="8cc10-156">개체 탐색기가 열려 있지 않으면 **보기** 메뉴에서 **개체 탐색기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8cc10-156">If Object Explorer is not open, on the **View** menu, click **Object Explorer**.</span></span>  
  
4.  <span data-ttu-id="8cc10-157">개체 탐색기에서 **저장된 패키지** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="8cc10-157">In Object Explorer, expand the **Stored Packages** folder.</span></span>  
  
5.  <span data-ttu-id="8cc10-158">하위 폴더를 확장하고 내보내려는 패키지를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="8cc10-158">Expand the subfolders to locate the package you want to export.</span></span>  
  
6.  <span data-ttu-id="8cc10-159">패키지를 마우스 오른쪽 단추로 클릭하고 **내보내기**를 클릭한 후 다음 중 하나를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="8cc10-159">Right-click the package, click **Export**, and then do one of the following:</span></span>  
  
    -   <span data-ttu-id="8cc10-160">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]인스턴스를 내보내려면 **SQL Server** 옵션을 선택한 후 서버를 지정하고 인증 모드를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8cc10-160">To export to an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], select the **SQL Server** option, and then specify the server and select the authentication mode.</span></span> <span data-ttu-id="8cc10-161">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인증을 선택한 경우 사용자 이름과 암호를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="8cc10-161">If you select [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication, provide a user name and a password.</span></span>  
  
         <span data-ttu-id="8cc10-162">찾아보기 단추 **(…)** 를 클릭하고 **SSIS 패키지** 폴더를 확장하여 패키지를 저장하려는 폴더를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="8cc10-162">Click the browse button **(...)**, and expand the **SSIS Packages** folder to locate the folder to which you want to save the package.</span></span> <span data-ttu-id="8cc10-163">선택적으로 패키지의 기본 이름을 업데이트한 후 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8cc10-163">Optionally, update the default name of the package, and then click **OK**.</span></span>  
  
    -   <span data-ttu-id="8cc10-164">파일 시스템으로 내보내려면 **파일 시스템** 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8cc10-164">To export to the file system, select the **File System** option.</span></span>  
  
         <span data-ttu-id="8cc10-165">찾아보기 단추 **(…)** 를 클릭하여 패키지를 내보내려는 폴더를 찾고, 패키지 파일의 이름을 입력한 후, **저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8cc10-165">Click the browse button **(...)** to locate the folder to which you want to export the package, type the name of the package file, and then click **Save.**</span></span>  
  
    -   <span data-ttu-id="8cc10-166">[!INCLUDE[ssIS](../includes/ssis-md.md)] 패키지 저장소로 내보내려면 **SSIS 패키지 저장소** 옵션을 선택하고 서버를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8cc10-166">To export to the [!INCLUDE[ssIS](../includes/ssis-md.md)] package store, select the **SSIS Package Store** option, and specify the server.</span></span>  
  
         <span data-ttu-id="8cc10-167">찾아보기 단추 **(…)** 를 클릭하고 **SSIS 패키지** 폴더를 확장하여 패키지를 저장하려는 폴더를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8cc10-167">Click the browse button **(...)**, expand the **SSIS Packages** folder, and select the folder to which you want to save the package.</span></span> <span data-ttu-id="8cc10-168">선택적으로 **패키지 이름** 입력란에 패키지의 새 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="8cc10-168">Optionally, enter a new name for the package in the **Package Name** text box.</span></span> [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
7.  <span data-ttu-id="8cc10-169">패키지의 보호 수준을 업데이트하려면 찾아보기 단추 **(…)** 를 클릭하고 **패키지 보호 수준** 대화 상자를 사용하여 다른 보호 수준을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8cc10-169">To update the protection level of the package, click the browse button **(...)** and choose a different protection level by using the **Package Protection Level** dialog box.</span></span> <span data-ttu-id="8cc10-170">**암호로 중요한 데이터 암호화** 또는 **암호로 모든 데이터 암호화** 옵션을 선택한 경우 암호를 입력하고 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="8cc10-170">If the **Encrypt sensitive data with password** or the **Encrypt all data with password** option is selected, type and confirm a password.</span></span>  
  
8.  <span data-ttu-id="8cc10-171">**확인** 을 클릭하여 내보내기를 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="8cc10-171">Click **OK** to complete the export.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8cc10-172">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8cc10-172">See Also</span></span>  
 [<span data-ttu-id="8cc10-173">패키지 관리&#40;SSIS 서비스&#41;</span><span class="sxs-lookup"><span data-stu-id="8cc10-173">Package Management &#40;SSIS Service&#41;</span></span>](service/package-management-ssis-service.md)  
  
  
