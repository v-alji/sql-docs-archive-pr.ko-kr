---
title: Integration Services 프로젝트 변환 마법사 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.migrationwizard.f1
ms.assetid: a192b094-4d0f-4c21-b911-460ec844a49f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c47dc8ed1d0485a62128be732cc34de1dca35740
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651169"
---
# <a name="integration-services-project-conversion-wizard"></a><span data-ttu-id="88cae-102">Integration Services 프로젝트 변환 마법사</span><span class="sxs-lookup"><span data-stu-id="88cae-102">Integration Services Project Conversion Wizard</span></span>
  <span data-ttu-id="88cae-103">**Integration Services 프로젝트 변환 마법사** 는 프로젝트를 프로젝트 배포 모델로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="88cae-103">The **Integration Services Project Conversion Wizard** converts a project to the project deployment model.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="88cae-104">프로젝트에 하나 이상의 데이터 원본이 포함된 경우 프로젝트 변환이 완료되면 데이터 원본이 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="88cae-104">If the project contains one or more datasources, the datasources are removed when the project conversion is completed.</span></span> <span data-ttu-id="88cae-105">프로젝트의 패키지에서 공유할 수 있는 데이터 원본에 대한 연결을 만들려면 프로젝트 수준에서 연결 관리자를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="88cae-105">To create a connection to a data source that can be shared by the packages in the project, add a connection manager at the project level.</span></span> <span data-ttu-id="88cae-106">자세한 내용은 [패키지에서 연결 관리자 추가, 삭제 또는 공유](../../2014/integration-services/add-delete-or-share-a-connection-manager-in-a-package.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="88cae-106">For more information, see [Add, Delete, or Share a Connection Manager in a Package](../../2014/integration-services/add-delete-or-share-a-connection-manager-in-a-package.md).</span></span>  
  
 <span data-ttu-id="88cae-107">**수행 작업**</span><span class="sxs-lookup"><span data-stu-id="88cae-107">**What do you want to do?**</span></span>  
  
-   [<span data-ttu-id="88cae-108">Integration Services 프로젝트 변환 마법사 열기</span><span class="sxs-lookup"><span data-stu-id="88cae-108">Open the Integration Services Project Conversion Wizard</span></span>](#open_dialog)  
  
-   [<span data-ttu-id="88cae-109">패키지 찾기 페이지에서 옵션 설정</span><span class="sxs-lookup"><span data-stu-id="88cae-109">Set Options on the Locate Packages Page</span></span>](#locate)  
  
-   [<span data-ttu-id="88cae-110">패키지 선택 페이지에서 옵션 설정</span><span class="sxs-lookup"><span data-stu-id="88cae-110">Set Options on the Select Packages Page</span></span>](#selectPackages)  
  
-   [<span data-ttu-id="88cae-111">대상 선택 페이지에서 옵션 설정</span><span class="sxs-lookup"><span data-stu-id="88cae-111">Set Options on the Select Destination Page</span></span>](#destination)  
  
-   [<span data-ttu-id="88cae-112">프로젝트 속성 지정 페이지에서 옵션 설정</span><span class="sxs-lookup"><span data-stu-id="88cae-112">Set Options on the Specify Project Properties Page</span></span>](#projectProperties)  
  
-   [<span data-ttu-id="88cae-113">패키지 실행 태스크 업데이트 페이지에서 옵션 설정</span><span class="sxs-lookup"><span data-stu-id="88cae-113">Set Options on the Update Execute Package Task Page</span></span>](#executePackage)  
  
-   [<span data-ttu-id="88cae-114">구성 선택 페이지에서 옵션 설정</span><span class="sxs-lookup"><span data-stu-id="88cae-114">Set Options on the Select Configurations Page</span></span>](#configurations)  
  
-   [<span data-ttu-id="88cae-115">매개 변수 만들기 페이지에서 옵션 설정</span><span class="sxs-lookup"><span data-stu-id="88cae-115">Set Options on the Create Parameters Page</span></span>](#createParameters)  
  
-   [<span data-ttu-id="88cae-116">매개 변수 구성 페이지에서 옵션 설정</span><span class="sxs-lookup"><span data-stu-id="88cae-116">Set Options on the Configure Parameters Page</span></span>](#configureParameters)  
  
-   [<span data-ttu-id="88cae-117">검토 페이지에서 옵션 설정</span><span class="sxs-lookup"><span data-stu-id="88cae-117">Set the Options on the Review page</span></span>](#review)  
  
-   [<span data-ttu-id="88cae-118">변환 수행에서 옵션 설정</span><span class="sxs-lookup"><span data-stu-id="88cae-118">Set the Options on the Perform Conversion</span></span>](#conversion)  
  
##  <a name="open-the-integration-services-project-conversion-wizard"></a><a name="open_dialog"></a><span data-ttu-id="88cae-119">Integration Services 프로젝트 변환 마법사 열기</span><span class="sxs-lookup"><span data-stu-id="88cae-119">Open the Integration Services Project Conversion Wizard</span></span>  
 <span data-ttu-id="88cae-120">다음 중 하나를 수행하여 **Integration Services 프로젝트 변환** 마법사를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="88cae-120">Do one of the following to open the **Integration Services Project Conversion** Wizard.</span></span>  
  
-   <span data-ttu-id="88cae-121">[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]에서 프로젝트를 열고 솔루션 탐색기에서 프로젝트를 마우스 오른쪽 단추로 클릭한 다음 **프로젝트 배포 모델로 변환**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="88cae-121">Open the project in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], and then in Solution Explorer, right-click the project and click **Convert to Project Deployment Model**.</span></span>  
  
-   <span data-ttu-id="88cae-122">[!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]의 개체 탐색기에서 **프로젝트** 노드를 마우스 오른쪽 단추로 클릭하고 **패키지 가져오기**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="88cae-122">From Object Explorer in [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)], right-click the **Projects** node and select **Import Packages**.</span></span>  
  
 <span data-ttu-id="88cae-123">**Integration Services 프로젝트 변환 마법사** 를 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 에서 실행하는지 아니면 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]에서 실행하는지에 따라 수행되는 변환 태스크가 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="88cae-123">Depending on whether you run the **Integration Services Project Conversion Wizard** from [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] or from [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], the wizard performs different conversion tasks.</span></span> <span data-ttu-id="88cae-124">자세한 내용은 [Deploy Projects to Integration Services Server](../../2014/integration-services/deploy-projects-to-integration-services-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="88cae-124">For more information, see [Deploy Projects to Integration Services Server](../../2014/integration-services/deploy-projects-to-integration-services-server.md).</span></span>  
  
##  <a name="set-options-on-the-locate-packages-page"></a><a name="locate"></a><span data-ttu-id="88cae-125">패키지 찾기 페이지에서 옵션 설정</span><span class="sxs-lookup"><span data-stu-id="88cae-125">Set Options on the Locate Packages Page</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="88cae-126">**패키지 찾기** 페이지는 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]에서 마법사를 실행할 때만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="88cae-126">The **Locate Packages** page is available only when you run the wizard from [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)].</span></span>  
  
 <span data-ttu-id="88cae-127">**원본** 드롭다운 목록에서 **파일 시스템** 을 선택하면 페이지에 다음 옵션이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="88cae-127">The following option displays on the page when you select **File system** in the **Source** drop-down list.</span></span> <span data-ttu-id="88cae-128">패키지가 파일 시스템에 있으면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="88cae-128">Select this option when the package is resides in the file system.</span></span>  
  
 <span data-ttu-id="88cae-129">**폴더**</span><span class="sxs-lookup"><span data-stu-id="88cae-129">**Folder**</span></span>  
 <span data-ttu-id="88cae-130">패키지 경로를 입력하거나 **찾아보기**를 클릭하여 패키지로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="88cae-130">Type the package path, or navigate to the package by clicking **Browse**.</span></span>  
  
 <span data-ttu-id="88cae-131">**원본** 드롭다운 목록에서 **SSIS 패키지 저장소**를 선택하면 페이지에 다음 옵션이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="88cae-131">The following options display on the page when you select **SSIS Package Store** in the **Source** drop-down list.</span></span> <span data-ttu-id="88cae-132">패키지 저장소에 대한 자세한 내용은 [패키지 관리&#40;SSIS 서비스&#41;](service/package-management-ssis-service.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="88cae-132">For more information about the package store, see [Package Management &#40;SSIS Service&#41;](service/package-management-ssis-service.md).</span></span>  
  
 <span data-ttu-id="88cae-133">**Server**</span><span class="sxs-lookup"><span data-stu-id="88cae-133">**Server**</span></span>  
 <span data-ttu-id="88cae-134">서버 이름을 입력하거나 서버를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="88cae-134">Type the server name or select the server.</span></span>  
  
 <span data-ttu-id="88cae-135">**폴더**</span><span class="sxs-lookup"><span data-stu-id="88cae-135">**Folder**</span></span>  
 <span data-ttu-id="88cae-136">패키지 경로를 입력하거나 **찾아보기**를 클릭하여 패키지로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="88cae-136">Type the package path, or navigate to the package by clicking **Browse**.</span></span>  
  
 <span data-ttu-id="88cae-137">**원본** 드롭다운 목록에서 **Microsoft SQL Server** 를 선택하면 페이지에 다음 옵션이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="88cae-137">The following options display on the page when you select **Microsoft SQL Server** in the **Source** drop-down list.</span></span> <span data-ttu-id="88cae-138">패키지가 Microsoft [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]에 있으면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="88cae-138">Select this option when the package resides in Microsoft [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="88cae-139">**Server**</span><span class="sxs-lookup"><span data-stu-id="88cae-139">**Server**</span></span>  
 <span data-ttu-id="88cae-140">서버 이름을 입력하거나 서버를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="88cae-140">Type the server name or select the server.</span></span>  
  
 <span data-ttu-id="88cae-141">**Windows 인증 사용**</span><span class="sxs-lookup"><span data-stu-id="88cae-141">**Use Windows authentication**</span></span>  
 <span data-ttu-id="88cae-142">Microsoft Windows 인증 모드에서는 사용자가 Windows 사용자 계정을 통해 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="88cae-142">Microsoft Windows Authentication mode allows a user to connect through a Windows user account.</span></span> <span data-ttu-id="88cae-143">Windows 인증을 사용하면 사용자 이름 또는 암호를 제공할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="88cae-143">If you use Windows Authentication, you do not need to provide a user name or password.</span></span>  
  
 <span data-ttu-id="88cae-144">**SQL Server 인증 사용**</span><span class="sxs-lookup"><span data-stu-id="88cae-144">**Use SQL Server authentication**</span></span>  
 <span data-ttu-id="88cae-145">사용자가 지정한 로그인 이름과 암호를 사용하여 트러스트되지 않은 연결로부터 연결하면 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 에서 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 로그인 계정이 설정되었는지와 지정한 암호가 이전에 기록한 암호와 일치하는지를 확인하여 연결을 인증합니다.</span><span class="sxs-lookup"><span data-stu-id="88cae-145">When a user connects with a specified login name and password from a non-trusted connection, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] authenticates the connection by checking to see if a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] login account has been set up and if the specified password matches the one previously recorded.</span></span> <span data-ttu-id="88cae-146">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 에 로그인 계정이 설정되어 있지 않으면 인증이 실패하고 오류 메시지가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="88cae-146">If [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] does not have a login account set, authentication fails, and the user receives an error message.</span></span>  
  
 <span data-ttu-id="88cae-147">**사용자 이름**</span><span class="sxs-lookup"><span data-stu-id="88cae-147">**User name**</span></span>  
 <span data-ttu-id="88cae-148">SQL Server 인증을 사용할 경우 사용자 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="88cae-148">Specify a user name when you are using SQL Server Authentication.</span></span>  
  
 <span data-ttu-id="88cae-149">**암호**</span><span class="sxs-lookup"><span data-stu-id="88cae-149">**Password**</span></span>  
 <span data-ttu-id="88cae-150">SQL Server 인증을 사용할 경우 암호를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="88cae-150">Provide the password when you are using SQL Server Authentication.</span></span>  
  
 <span data-ttu-id="88cae-151">**폴더**</span><span class="sxs-lookup"><span data-stu-id="88cae-151">**Folder**</span></span>  
 <span data-ttu-id="88cae-152">패키지 경로를 입력하거나 **찾아보기**를 클릭하여 패키지로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="88cae-152">Type the package path, or navigate to the package by clicking **Browse**.</span></span>  
  
##  <a name="set-options-on-the-select-packages-page"></a><a name="selectPackages"></a><span data-ttu-id="88cae-153">패키지 선택 페이지에서 옵션 설정</span><span class="sxs-lookup"><span data-stu-id="88cae-153">Set Options on the Select Packages Page</span></span>  
 <span data-ttu-id="88cae-154">**패키지 이름**</span><span class="sxs-lookup"><span data-stu-id="88cae-154">**Package Name**</span></span>  
 <span data-ttu-id="88cae-155">패키지 파일을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="88cae-155">Lists the package file.</span></span>  
  
 <span data-ttu-id="88cae-156">**상태**</span><span class="sxs-lookup"><span data-stu-id="88cae-156">**Status**</span></span>  
 <span data-ttu-id="88cae-157">패키지를 프로젝트 배포 모델로 변환할 준비가 되었는지를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="88cae-157">Indicates whether a package is ready to convert to the project deployment model.</span></span>  
  
 <span data-ttu-id="88cae-158">**Message**</span><span class="sxs-lookup"><span data-stu-id="88cae-158">**Message**</span></span>  
 <span data-ttu-id="88cae-159">패키지와 연결된 메시지를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="88cae-159">Displays a message associated with the package.</span></span>  
  
 <span data-ttu-id="88cae-160">**암호**</span><span class="sxs-lookup"><span data-stu-id="88cae-160">**Password**</span></span>  
 <span data-ttu-id="88cae-161">패키지와 연결된 암호를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="88cae-161">Displays a password associated with the package.</span></span> <span data-ttu-id="88cae-162">암호 텍스트는 숨겨져 있습니다.</span><span class="sxs-lookup"><span data-stu-id="88cae-162">The password text is hidden.</span></span>  
  
 <span data-ttu-id="88cae-163">**선택 항목에 적용**</span><span class="sxs-lookup"><span data-stu-id="88cae-163">**Apply to selection**</span></span>  
 <span data-ttu-id="88cae-164">**암호** 입력란의 암호를 선택한 패키지에 적용하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="88cae-164">Click to apply the password in the **Password** text box, to the selected package or packages.</span></span>  
  
 <span data-ttu-id="88cae-165">**새로 고침**</span><span class="sxs-lookup"><span data-stu-id="88cae-165">**Refresh**</span></span>  
 <span data-ttu-id="88cae-166">패키지 목록을 새로 고칩니다.</span><span class="sxs-lookup"><span data-stu-id="88cae-166">Refreshes the list of packages.</span></span>  
  
##  <a name="set-options-on-the-select-destination-page"></a><a name="destination"></a><span data-ttu-id="88cae-167">대상 선택 페이지에서 옵션 설정</span><span class="sxs-lookup"><span data-stu-id="88cae-167">Set Options on the Select Destination Page</span></span>  
 <span data-ttu-id="88cae-168">이 페이지에서 새 프로젝트 배포 파일(.ispac)의 이름과 경로를 지정하거나 기존 파일을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="88cae-168">On this page, specify the name and path for a new project deployment file (.ispac) or select an existing file.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="88cae-169">**대상 선택** 페이지는 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]에서 마법사를 실행할 때만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="88cae-169">The **Select Destination** page is available only when you run the wizard from [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)].</span></span>  
  
 <span data-ttu-id="88cae-170">**출력 경로**</span><span class="sxs-lookup"><span data-stu-id="88cae-170">**Output path**</span></span>  
 <span data-ttu-id="88cae-171">배포 파일에 대한 경로를 입력하거나 **찾아보기**를 클릭하여 해당 파일로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="88cae-171">Type the path for the deployment file or navigate to the file by clicking **Browse**.</span></span>  
  
 <span data-ttu-id="88cae-172">**프로젝트 이름**</span><span class="sxs-lookup"><span data-stu-id="88cae-172">**Project name**</span></span>  
 <span data-ttu-id="88cae-173">프로젝트 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="88cae-173">Type the project name.</span></span>  
  
 <span data-ttu-id="88cae-174">**보호 수준**</span><span class="sxs-lookup"><span data-stu-id="88cae-174">**Protection level**</span></span>  
 <span data-ttu-id="88cae-175">보호 수준을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="88cae-175">Select the protection level.</span></span> <span data-ttu-id="88cae-176">자세한 내용은 [Access Control for Sensitive Data in Packages](security/access-control-for-sensitive-data-in-packages.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="88cae-176">For more information, see [Access Control for Sensitive Data in Packages](security/access-control-for-sensitive-data-in-packages.md).</span></span>  
  
 <span data-ttu-id="88cae-177">**프로젝트 설명**</span><span class="sxs-lookup"><span data-stu-id="88cae-177">**Project description**</span></span>  
 <span data-ttu-id="88cae-178">프로젝트에 대한 선택적 설명을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="88cae-178">Type an optional description for the project.</span></span>  
  
##  <a name="set-options-on-the-specify-project-properties-page"></a><a name="projectProperties"></a><span data-ttu-id="88cae-179">프로젝트 속성 지정 페이지에서 옵션 설정</span><span class="sxs-lookup"><span data-stu-id="88cae-179">Set Options on the Specify Project Properties Page</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="88cae-180">**프로젝트 속성 지정** 페이지는 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]에서 마법사를 실행할 때만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="88cae-180">The **Specify Project Properties** page is available only when you run the wizard from [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].</span></span>  
  
 <span data-ttu-id="88cae-181">**프로젝트 이름**</span><span class="sxs-lookup"><span data-stu-id="88cae-181">**Project name**</span></span>  
 <span data-ttu-id="88cae-182">프로젝트 이름을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="88cae-182">Lists the project name.</span></span>  
  
 <span data-ttu-id="88cae-183">**보호 수준**</span><span class="sxs-lookup"><span data-stu-id="88cae-183">**Protection level**</span></span>  
 <span data-ttu-id="88cae-184">프로젝트에 포함된 패키지에 대한 보호 수준을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="88cae-184">Select a protection level for the packages contained in the project.</span></span> <span data-ttu-id="88cae-185">보호 수준에 대한 자세한 내용은 [Access Control for Sensitive Data in Packages](security/access-control-for-sensitive-data-in-packages.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="88cae-185">For more information about protection levels, see [Access Control for Sensitive Data in Packages](security/access-control-for-sensitive-data-in-packages.md).</span></span>  
  
 <span data-ttu-id="88cae-186">**프로젝트 설명**</span><span class="sxs-lookup"><span data-stu-id="88cae-186">**Project description**</span></span>  
 <span data-ttu-id="88cae-187">선택적인 프로젝트 설명을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="88cae-187">Type an optional project description.</span></span>  
  
##  <a name="set-options-on-the-update-execute-package-task-page"></a><a name="executePackage"></a><span data-ttu-id="88cae-188">패키지 실행 태스크 업데이트 페이지에서 옵션 설정</span><span class="sxs-lookup"><span data-stu-id="88cae-188">Set Options on the Update Execute Package Task Page</span></span>  
 <span data-ttu-id="88cae-189">프로젝트 기반 참조를 사용할 수 있도록 패키지 실행 태스크 업데이트가 패키지에 포함되었습니다.</span><span class="sxs-lookup"><span data-stu-id="88cae-189">Update Execute Package Tasks contain in the packages, to use a project-based reference.</span></span> <span data-ttu-id="88cae-190">자세한 내용은 [Execute Package Task Editor](../../2014/integration-services/execute-package-task-editor.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="88cae-190">For more information, see [Execute Package Task Editor](../../2014/integration-services/execute-package-task-editor.md).</span></span>  
  
 <span data-ttu-id="88cae-191">**부모 패키지**</span><span class="sxs-lookup"><span data-stu-id="88cae-191">**Parent Package**</span></span>  
 <span data-ttu-id="88cae-192">패키지 실행 태스크를 사용하여 자식 패키지를 실행하는 패키지의 이름을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="88cae-192">Lists the name of the package that executes the child package using the Execute Package task.</span></span>  
  
 <span data-ttu-id="88cae-193">**작업 이름**</span><span class="sxs-lookup"><span data-stu-id="88cae-193">**Task name**</span></span>  
 <span data-ttu-id="88cae-194">패키지 실행 태스크의 이름을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="88cae-194">Lists the name of the Execute Package task.</span></span>  
  
 <span data-ttu-id="88cae-195">**원래 참조**</span><span class="sxs-lookup"><span data-stu-id="88cae-195">**Original reference**</span></span>  
 <span data-ttu-id="88cae-196">자식 패키지의 현재 경로를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="88cae-196">Lists the current path of the child package.</span></span>  
  
 <span data-ttu-id="88cae-197">**참조 할당**</span><span class="sxs-lookup"><span data-stu-id="88cae-197">**Assign reference**</span></span>  
 <span data-ttu-id="88cae-198">프로젝트에 저장된 자식 패키지를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="88cae-198">Select a child package stored in the project.</span></span>  
  
##  <a name="set-options-on-the-select-configurations-page"></a><a name="configurations"></a><span data-ttu-id="88cae-199">구성 선택 페이지에서 옵션 설정</span><span class="sxs-lookup"><span data-stu-id="88cae-199">Set Options on the Select Configurations Page</span></span>  
 <span data-ttu-id="88cae-200">매개 변수로 대체하려고 하는 패키지 구성을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="88cae-200">Select the package configurations that you want to replace with parameters.</span></span>  
  
 <span data-ttu-id="88cae-201">**패키지**</span><span class="sxs-lookup"><span data-stu-id="88cae-201">**Package**</span></span>  
 <span data-ttu-id="88cae-202">패키지 파일을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="88cae-202">Lists the package file.</span></span>  
  
 <span data-ttu-id="88cae-203">**형식**</span><span class="sxs-lookup"><span data-stu-id="88cae-203">**Type**</span></span>  
 <span data-ttu-id="88cae-204">XML 구성과 같은 구성 유형을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="88cae-204">Lists the type of configuration, such as an XML configuration file.</span></span>  
  
 <span data-ttu-id="88cae-205">**구성 문자열**</span><span class="sxs-lookup"><span data-stu-id="88cae-205">**Configuration String**</span></span>  
 <span data-ttu-id="88cae-206">구성 파일의 경로를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="88cae-206">Lists the path of the configuration file.</span></span>  
  
 <span data-ttu-id="88cae-207">**상태**</span><span class="sxs-lookup"><span data-stu-id="88cae-207">**Status**</span></span>  
 <span data-ttu-id="88cae-208">구성에 대한 상태 메시지를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="88cae-208">Displays a status message for the configuration.</span></span> <span data-ttu-id="88cae-209">전체 메시지 텍스트를 보려면 메시지를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="88cae-209">Click the message to view the entire message text.</span></span>  
  
 <span data-ttu-id="88cae-210">**구성 추가**</span><span class="sxs-lookup"><span data-stu-id="88cae-210">**Add Configurations**</span></span>  
 <span data-ttu-id="88cae-211">다른 프로젝트에 포함된 패키지 구성을 매개 변수로 바꾸려는 사용 가능한 구성 목록에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="88cae-211">Add package configurations contained in other projects to the list of available configurations that you want to replace with parameters.</span></span> <span data-ttu-id="88cae-212">파일 시스템 또는 SQL Server에 저장된 구성을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="88cae-212">You can select configurations stored in a file system or stored in SQL Server.</span></span>  
  
 <span data-ttu-id="88cae-213">**새로 고침**</span><span class="sxs-lookup"><span data-stu-id="88cae-213">**Refresh**</span></span>  
 <span data-ttu-id="88cae-214">구성 목록을 새로 고치려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="88cae-214">Click to refresh the list of configurations.</span></span>  
  
 <span data-ttu-id="88cae-215">**변환 후 구성을 모든 패키지에서 제거**</span><span class="sxs-lookup"><span data-stu-id="88cae-215">**Remove configurations from all packages after conversion**</span></span>  
 <span data-ttu-id="88cae-216">이 옵션을 선택하여 프로젝트에서 모든 구성을 제거하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="88cae-216">It is recommended that you remove all configurations from the project by selecting this option.</span></span>  
  
 <span data-ttu-id="88cae-217">이 옵션을 선택하지 않으면 매개 변수로 바꾸려고 선택한 구성만 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="88cae-217">If you don't select this option, only the configurations that you selected to replace with parameters are removed.</span></span>  
  
##  <a name="set-options-on-the-create-parameters-page"></a><a name="createParameters"></a><span data-ttu-id="88cae-218">매개 변수 만들기 페이지에서 옵션 설정</span><span class="sxs-lookup"><span data-stu-id="88cae-218">Set Options on the Create Parameters Page</span></span>  
 <span data-ttu-id="88cae-219">각 구성 속성에 대한 매개 변수 이름과 범위를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="88cae-219">Select the parameter name and scope for each configuration property.</span></span>  
  
 <span data-ttu-id="88cae-220">**패키지**</span><span class="sxs-lookup"><span data-stu-id="88cae-220">**Package**</span></span>  
 <span data-ttu-id="88cae-221">패키지 파일을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="88cae-221">Lists the package file.</span></span>  
  
 <span data-ttu-id="88cae-222">**매개 변수 이름**</span><span class="sxs-lookup"><span data-stu-id="88cae-222">**Parameter Name**</span></span>  
 <span data-ttu-id="88cae-223">매개 변수 이름을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="88cae-223">Lists the parameter name.</span></span>  
  
 <span data-ttu-id="88cae-224">**범위**</span><span class="sxs-lookup"><span data-stu-id="88cae-224">**Scope**</span></span>  
 <span data-ttu-id="88cae-225">패키지 또는 프로젝트 중에서 매개 변수 범위를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="88cae-225">Select the scope of the parameter, either package or project.</span></span>  
  
##  <a name="set-options-on-the-configure-parameters-page"></a><a name="configureParameters"></a><span data-ttu-id="88cae-226">매개 변수 구성 페이지에서 옵션 설정</span><span class="sxs-lookup"><span data-stu-id="88cae-226">Set Options on the Configure Parameters Page</span></span>  
 <span data-ttu-id="88cae-227">**이름**</span><span class="sxs-lookup"><span data-stu-id="88cae-227">**Name**</span></span>  
 <span data-ttu-id="88cae-228">매개 변수 이름을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="88cae-228">Lists the parameter name.</span></span>  
  
 <span data-ttu-id="88cae-229">**범위**</span><span class="sxs-lookup"><span data-stu-id="88cae-229">**Scope**</span></span>  
 <span data-ttu-id="88cae-230">매개 변수의 범위를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="88cae-230">Lists the scope of the parameter.</span></span>  
  
 <span data-ttu-id="88cae-231">**값**</span><span class="sxs-lookup"><span data-stu-id="88cae-231">**Value**</span></span>  
 <span data-ttu-id="88cae-232">매개 변수 값을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="88cae-232">Lists the parameter value.</span></span>  
  
 <span data-ttu-id="88cae-233">매개 변수 속성을 구성하려면 값 필드 옆에 있는 줄임표 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="88cae-233">Click the ellipsis button next to the value field to configure the parameter properties.</span></span>  
  
 <span data-ttu-id="88cae-234">**매개 변수 정보 설정** 대화 상자에서 매개 변수 값을 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="88cae-234">In the **Set Parameter Details** dialog box, you can edit the parameter value.</span></span> <span data-ttu-id="88cae-235">패키지를 실행할 때 매개 변수 값을 제공해야 하는지 여부를 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="88cae-235">You can also specify whether the parameter value must be provided when you run the package.</span></span>  
  
 <span data-ttu-id="88cae-236">매개 변수 옆에 있는 찾아보기 단추를 클릭하여 **에서** 구성 **대화 상자의** 매개 변수 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]페이지에 있는 값을 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="88cae-236">You can modify value in the **Parameters** page of the **Configure** dialog box in [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)], by clicking the browse button next to the parameter.</span></span> <span data-ttu-id="88cae-237">**매개 변수 값 설정** 대화 상자가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="88cae-237">The **Set Parameter Value** dialog box appears.</span></span>  
  
 <span data-ttu-id="88cae-238">**매개 변수 정보 설정** 대화 상자에는 매개 변수 값의 데이터 형식 및 매개 변수의 원본도 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="88cae-238">The **Set Parameter Details** dialog box also lists the data type of the parameter value and the origin of the parameter.</span></span>  
  
##  <a name="set-the-options-on-the-review-page"></a><a name="review"></a><span data-ttu-id="88cae-239">검토 페이지에서 옵션 설정</span><span class="sxs-lookup"><span data-stu-id="88cae-239">Set the Options on the Review page</span></span>  
 <span data-ttu-id="88cae-240">**검토** 페이지를 사용하여 프로젝트 변환을 위해 선택한 옵션을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="88cae-240">Use the **Review** page to confirm the options that you've selected for the conversion of the project.</span></span>  
  
 <span data-ttu-id="88cae-241">**이전**</span><span class="sxs-lookup"><span data-stu-id="88cae-241">**Previous**</span></span>  
 <span data-ttu-id="88cae-242">옵션을 변경하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="88cae-242">Click to change an option.</span></span>  
  
 <span data-ttu-id="88cae-243">**변환**</span><span class="sxs-lookup"><span data-stu-id="88cae-243">**Convert**</span></span>  
 <span data-ttu-id="88cae-244">프로젝트를 프로젝트 배포 모델로 변환하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="88cae-244">Click to convert the project to the project deployment model.</span></span>  
  
##  <a name="set-the-options-on-the-perform-conversion"></a><a name="conversion"></a><span data-ttu-id="88cae-245">변환 수행에서 옵션 설정</span><span class="sxs-lookup"><span data-stu-id="88cae-245">Set the Options on the Perform Conversion</span></span>  
 <span data-ttu-id="88cae-246">변환 수행 페이지에는 프로젝트 변환 상태가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="88cae-246">The Perform Conversion page shows status of the project conversion.</span></span>  
  
 <span data-ttu-id="88cae-247">**동작**</span><span class="sxs-lookup"><span data-stu-id="88cae-247">**Action**</span></span>  
 <span data-ttu-id="88cae-248">특정 변환 단계를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="88cae-248">Lists a specific conversion step.</span></span>  
  
 <span data-ttu-id="88cae-249">**결과**</span><span class="sxs-lookup"><span data-stu-id="88cae-249">**Result**</span></span>  
 <span data-ttu-id="88cae-250">각 변환 단계의 상태를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="88cae-250">Lists the status of each conversion step.</span></span> <span data-ttu-id="88cae-251">자세한 내용을 보려면 상태 메시지를 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="88cae-251">Click the status message for more information.</span></span>  
  
 <span data-ttu-id="88cae-252">프로젝트 변환은 프로젝트가 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]에 저장될 때까지 저장되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="88cae-252">The project conversion is not saved until the project is saved in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].</span></span>  
  
 <span data-ttu-id="88cae-253">**보고서 저장**</span><span class="sxs-lookup"><span data-stu-id="88cae-253">**Save report**</span></span>  
 <span data-ttu-id="88cae-254">프로젝트 변환 요약을 .xml 파일로 저장하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="88cae-254">Click to save a summary of the project conversion in an .xml file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88cae-255">참고 항목</span><span class="sxs-lookup"><span data-stu-id="88cae-255">See Also</span></span>  
 [<span data-ttu-id="88cae-256">Deploy Projects to Integration Services Server</span><span class="sxs-lookup"><span data-stu-id="88cae-256">Deploy Projects to Integration Services Server</span></span>](../../2014/integration-services/deploy-projects-to-integration-services-server.md)  
  
  
