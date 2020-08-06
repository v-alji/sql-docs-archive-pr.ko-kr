---
title: 패키지 실행 태스크 편집기 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.executepackagetask.parameter.F1
- sql12.dts.designer.executepackagetask.package.f1
- sql12.dts.designer.executepackagetask.general.f1
ms.assetid: c2c96b4f-eb10-4d8b-be34-88edfd0785fb
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b9b2e18516e1f5c1b7af56bd1e84ef875557fd49
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651790"
---
# <a name="execute-package-task-editor"></a><span data-ttu-id="c35f3-102">패키지 실행 태스크 편집기</span><span class="sxs-lookup"><span data-stu-id="c35f3-102">Execute Package Task Editor</span></span>
  <span data-ttu-id="c35f3-103">패키지 실행 태스크 편집기로 패키지 실행 태스크를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="c35f3-103">Use the Execute Package Task Editor to configure the Execute Package Task.</span></span> <span data-ttu-id="c35f3-104">패키지 실행 태스크는 패키지가 다른 패키지를 워크플로의 일부로 실행할 수 있도록 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 의 엔터프라이즈 기능을 확장했습니다.</span><span class="sxs-lookup"><span data-stu-id="c35f3-104">The Execute Package task extends the enterprise capabilities of [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] by letting packages run other packages as part of a workflow.</span></span>  
  
 <span data-ttu-id="c35f3-105">**수행 작업**</span><span class="sxs-lookup"><span data-stu-id="c35f3-105">**What do you want to do?**</span></span>  
  
-   [<span data-ttu-id="c35f3-106">패키지 실행 태스크 편집기 열기</span><span class="sxs-lookup"><span data-stu-id="c35f3-106">Open the Execute Package Task Editor</span></span>](#open)  
  
-   [<span data-ttu-id="c35f3-107">일반 페이지에서 옵션 설정</span><span class="sxs-lookup"><span data-stu-id="c35f3-107">Set the Options on the General Page</span></span>](#general)  
  
-   [<span data-ttu-id="c35f3-108">패키지 페이지에서 옵션 설정</span><span class="sxs-lookup"><span data-stu-id="c35f3-108">Set the Options on the Package Page</span></span>](#package)  
  
-   [<span data-ttu-id="c35f3-109">매개 변수 바인딩 페이지에서 옵션 설정</span><span class="sxs-lookup"><span data-stu-id="c35f3-109">Set the Options on the Parameter Bindings Page</span></span>](#parameter)  
  
##  <a name="open-the-execute-package-task-editor"></a><a name="open"></a> <span data-ttu-id="c35f3-110">패키지 실행 태스크 편집기 열기</span><span class="sxs-lookup"><span data-stu-id="c35f3-110">Open the Execute Package Task Editor</span></span>  
  
1.  <span data-ttu-id="c35f3-111">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 에서 패키지 실행 태스크가 들어 있는 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 프로젝트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="c35f3-111">Open an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] that contains an Execute Package task.</span></span>  
  
2.  <span data-ttu-id="c35f3-112">SSIS 디자이너에서 태스크를 마우스 오른쪽 단추로 클릭한 다음 **편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c35f3-112">Right-click the task in the SSIS Designer, and then click **Edit**.</span></span>  
  
##  <a name="set-the-options-on-the-general-page"></a><a name="general"></a> <span data-ttu-id="c35f3-113">일반 페이지에서 옵션 설정</span><span class="sxs-lookup"><span data-stu-id="c35f3-113">Set the Options on the General Page</span></span>  
 <span data-ttu-id="c35f3-114">**이름**</span><span class="sxs-lookup"><span data-stu-id="c35f3-114">**Name**</span></span>  
 <span data-ttu-id="c35f3-115">패키지 실행 태스크에 사용할 고유 이름을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="c35f3-115">Provide a unique name for the Execute Package task.</span></span> <span data-ttu-id="c35f3-116">이 이름은 태스크 아이콘에서 레이블로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="c35f3-116">This name is used as the label in the task icon.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c35f3-117">태스크 이름은 패키지 내에서 고유해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c35f3-117">Task names must be unique within a package.</span></span>  
  
 <span data-ttu-id="c35f3-118">**설명**</span><span class="sxs-lookup"><span data-stu-id="c35f3-118">**Description**</span></span>  
 <span data-ttu-id="c35f3-119">패키지 실행 태스크에 대한 설명을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="c35f3-119">Type a description of the Execute Package task.</span></span>  
  
##  <a name="set-the-options-on-the-package-page"></a><a name="package"></a> <span data-ttu-id="c35f3-120">패키지 페이지에서 옵션 설정</span><span class="sxs-lookup"><span data-stu-id="c35f3-120">Set the Options on the Package Page</span></span>  
 <span data-ttu-id="c35f3-121">**ReferenceType**</span><span class="sxs-lookup"><span data-stu-id="c35f3-121">**ReferenceType**</span></span>  
 <span data-ttu-id="c35f3-122">자식 패키지가 프로젝트 내부에 있는 경우 **프로젝트 참조** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c35f3-122">Select **Project Reference** for child packages that are in the project.</span></span> <span data-ttu-id="c35f3-123">자식 패키지가 프로젝트 외부에 있는 경우 **외부 참조** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c35f3-123">Select **External Reference** for child packages that are located outside the package</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c35f3-124">**ReferenceType** 옵션은 읽기 전용이며 패키지가 포함된 프로젝트가 프로젝트 배포 모델로 전환되지 않은 경우에는 **외부 참조** 로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="c35f3-124">The **ReferenceType** option is ready-only and set to **External Reference** if the project that contains the package has not been converted to the project deployment model.</span></span> <span data-ttu-id="c35f3-125">변환에 대한 자세한 내용은 [Integration Services 서버에 프로젝트 배포](../../2014/integration-services/deploy-projects-to-integration-services-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c35f3-125">For more information about conversion, see [Deploy Projects to Integration Services Server](../../2014/integration-services/deploy-projects-to-integration-services-server.md).</span></span>  
  
 <span data-ttu-id="c35f3-126">**암호**</span><span class="sxs-lookup"><span data-stu-id="c35f3-126">**Password**</span></span>  
 <span data-ttu-id="c35f3-127">자식 패키지가 암호로 보호되어 있으면 자식 패키지의 암호를 입력하거나 줄임표 단추(...)를 클릭하여 자식 패키지의 새 암호를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c35f3-127">If the child package is password protected, provide the password for the child package, or click the ellipsis button (...) and create a new password for the child package.</span></span>  
  
 `ExecuteOutOfProcess`  
 <span data-ttu-id="c35f3-128">자식 패키지를 부모 패키지 프로세스에서 실행할지 아니면 별도의 프로세스에서 실행할지 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c35f3-128">Specify whether the child package runs in the process of the parent package or in a separate process.</span></span> <span data-ttu-id="c35f3-129">기본적으로 패키지 실행 태스크의 ExecuteOutOfProcess 속성은로 설정 되 `False` 고 자식 패키지는 부모 패키지와 같은 프로세스에서 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c35f3-129">By default, the ExecuteOutOfProcess property of the Execute Package task is set to `False`, and the child package runs in the same process as the parent package.</span></span> <span data-ttu-id="c35f3-130">이 속성을 `true`로 설정하면 하위 패키지가 개별 프로세스로 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="c35f3-130">If you set this property to `true`, the child package runs in a separate process.</span></span> <span data-ttu-id="c35f3-131">이렇게 하면 하위 패키지의 실행 속도가 느려집니다.</span><span class="sxs-lookup"><span data-stu-id="c35f3-131">This may slow down the launching of the child package.</span></span> <span data-ttu-id="c35f3-132">또한 이 속성을 `true`로 설정하면 도구만 설치로 패키지를 디버깅할 수 없으며 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 제품을 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c35f3-132">In addition, if set the property to `true`, you cannot debug the package in a tools-only install; you must install the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] product.</span></span> <span data-ttu-id="c35f3-133">자세한 내용은 [Integration Services 설치](install-windows/install-integration-services.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c35f3-133">For more information, see [Install Integration Services](install-windows/install-integration-services.md).</span></span>  
  
### <a name="referencetype-dynamic-options"></a><span data-ttu-id="c35f3-134">ReferenceType 동적 옵션</span><span class="sxs-lookup"><span data-stu-id="c35f3-134">ReferenceType Dynamic Options</span></span>  
  
#### <a name="referencetype--external-reference"></a><span data-ttu-id="c35f3-135">ReferenceType = 외부 참조</span><span class="sxs-lookup"><span data-stu-id="c35f3-135">ReferenceType = External Reference</span></span>  
 <span data-ttu-id="c35f3-136">**위치**</span><span class="sxs-lookup"><span data-stu-id="c35f3-136">**Location**</span></span>  
 <span data-ttu-id="c35f3-137">자식 패키지의 위치를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c35f3-137">Select the location of the child package.</span></span> <span data-ttu-id="c35f3-138">이 속성의 옵션은 다음 표에 나열되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c35f3-138">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="c35f3-139">값</span><span class="sxs-lookup"><span data-stu-id="c35f3-139">Value</span></span>|<span data-ttu-id="c35f3-140">Description</span><span class="sxs-lookup"><span data-stu-id="c35f3-140">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c35f3-141">**SQL Server**</span><span class="sxs-lookup"><span data-stu-id="c35f3-141">**SQL Server**</span></span>|<span data-ttu-id="c35f3-142">위치를 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]인스턴스로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="c35f3-142">Set the location to an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>|  
|<span data-ttu-id="c35f3-143">**파일 시스템**</span><span class="sxs-lookup"><span data-stu-id="c35f3-143">**File system**</span></span>|<span data-ttu-id="c35f3-144">파일 시스템에 위치를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="c35f3-144">Set the location to the file system.</span></span>|  
  
 <span data-ttu-id="c35f3-145">**연결**</span><span class="sxs-lookup"><span data-stu-id="c35f3-145">**Connection**</span></span>  
 <span data-ttu-id="c35f3-146">자식 패키지의 스토리지 위치 유형을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c35f3-146">Select the type of storage location for the child package.</span></span>  
  
 <span data-ttu-id="c35f3-147">**PackageNameReadOnly**</span><span class="sxs-lookup"><span data-stu-id="c35f3-147">**PackageNameReadOnly**</span></span>  
 <span data-ttu-id="c35f3-148">패키지 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="c35f3-148">Displays the package name.</span></span>  
  
#### <a name="referencetype--project-reference"></a><span data-ttu-id="c35f3-149">ReferenceType = 프로젝트 참조</span><span class="sxs-lookup"><span data-stu-id="c35f3-149">ReferenceType = Project Reference</span></span>  
 <span data-ttu-id="c35f3-150">**PackageNameFromProjectReference**</span><span class="sxs-lookup"><span data-stu-id="c35f3-150">**PackageNameFromProjectReference**</span></span>  
 <span data-ttu-id="c35f3-151">프로젝트에 포함된 패키지 중 자식 패키지로 지정할 패키지를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c35f3-151">Select a package contained in the project, to be the child package.</span></span>  
  
### <a name="location-dynamic-options"></a><span data-ttu-id="c35f3-152">Location 동적 옵션</span><span class="sxs-lookup"><span data-stu-id="c35f3-152">Location Dynamic Options</span></span>  
  
#### <a name="location--sql-server"></a><span data-ttu-id="c35f3-153">Location = SQL Server</span><span class="sxs-lookup"><span data-stu-id="c35f3-153">Location = SQL Server</span></span>  
 <span data-ttu-id="c35f3-154">**연결**</span><span class="sxs-lookup"><span data-stu-id="c35f3-154">**Connection**</span></span>  
 <span data-ttu-id="c35f3-155">목록에서 OLE DB 연결 관리자를 선택하거나 \<**New connection...**>을 클릭하여 새 연결 관리자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c35f3-155">Select an OLE DB connection manager in the list, or click \<**New connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="c35f3-156">**관련 항목:** [OLE DB 연결 관리자](connection-manager/ole-db-connection-manager.md), [OLE DB 연결 관리자 구성](../../2014/integration-services/configure-ole-db-connection-manager.md)</span><span class="sxs-lookup"><span data-stu-id="c35f3-156">**Related Topics:** [OLE DB Connection Manager](connection-manager/ole-db-connection-manager.md), [Configure OLE DB Connection Manager](../../2014/integration-services/configure-ole-db-connection-manager.md)</span></span>  
  
 <span data-ttu-id="c35f3-157">**PackageName**</span><span class="sxs-lookup"><span data-stu-id="c35f3-157">**PackageName**</span></span>  
 <span data-ttu-id="c35f3-158">자식 패키지의 이름을 입력하거나 줄임표(...)를 클릭한 다음, 패키지를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="c35f3-158">Type the name of the child package, or click the ellipsis (...) and then locate the package.</span></span>  
  
#### <a name="location--file-system"></a><span data-ttu-id="c35f3-159">Location = 파일 시스템</span><span class="sxs-lookup"><span data-stu-id="c35f3-159">Location = File system</span></span>  
 <span data-ttu-id="c35f3-160">**연결**</span><span class="sxs-lookup"><span data-stu-id="c35f3-160">**Connection**</span></span>  
 <span data-ttu-id="c35f3-161">목록에서 파일 연결 관리자를 선택하거나 \<**New connection...**>을 클릭하여 새 연결 관리자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c35f3-161">Select a File connection manager in the list, or click \<**New connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="c35f3-162">**관련 항목:** [파일 연결 관리자](connection-manager/file-connection-manager.md), [파일 연결 관리자 편집기](../../2014/integration-services/file-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="c35f3-162">**Related Topics:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)</span></span>  
  
 <span data-ttu-id="c35f3-163">**PackageNameReadOnly**</span><span class="sxs-lookup"><span data-stu-id="c35f3-163">**PackageNameReadOnly**</span></span>  
 <span data-ttu-id="c35f3-164">패키지 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="c35f3-164">Displays the package name.</span></span>  
  
##  <a name="set-the-options-on-the-parameter-bindings-page"></a><a name="parameter"></a> <span data-ttu-id="c35f3-165">매개 변수 바인딩 페이지에서 옵션 설정</span><span class="sxs-lookup"><span data-stu-id="c35f3-165">Set the Options on the Parameter Bindings Page</span></span>  
 <span data-ttu-id="c35f3-166">부모 패키지나 프로젝트의 값을 자식 패키지에 전달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c35f3-166">You can pass values from the parent package or the project, to the child package.</span></span> <span data-ttu-id="c35f3-167">프로젝트에서 프로젝트 배포 모델을 사용해야 하며 자식 패키지는 부모 패키지와 동일한 프로젝트에 포함되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c35f3-167">The project must use the project deployment model and the child package must be contained in the same project that contains the parent package.</span></span>  
  
 <span data-ttu-id="c35f3-168">프로젝트를 프로젝트 배포 모델로 변환하는 방법은 [Integration Services 서버에 프로젝트 배포](../../2014/integration-services/deploy-projects-to-integration-services-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c35f3-168">For information about converting projects to the project deployment model, see [Deploy Projects to Integration Services Server](../../2014/integration-services/deploy-projects-to-integration-services-server.md).</span></span>  
  
 <span data-ttu-id="c35f3-169">**자식 패키지 매개 변수**</span><span class="sxs-lookup"><span data-stu-id="c35f3-169">**Child package parameter**</span></span>  
 <span data-ttu-id="c35f3-170">자식 패키지 매개 변수의 이름을 입력하거나 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c35f3-170">Enter or select a name for the child package parameter.</span></span>  
  
 <span data-ttu-id="c35f3-171">**매개 변수 또는 변수 바인딩**</span><span class="sxs-lookup"><span data-stu-id="c35f3-171">**Binding parameter or variable**</span></span>  
 <span data-ttu-id="c35f3-172">자식 패키지에 전달할 값이 포함된 매개 변수나 변수를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c35f3-172">Select the parameter or variable that contains the value that you want to pass to the child package.</span></span>  
  
 <span data-ttu-id="c35f3-173">**추가**</span><span class="sxs-lookup"><span data-stu-id="c35f3-173">**Add**</span></span>  
 <span data-ttu-id="c35f3-174">자식 패키지 매개 변수에 매개 변수나 변수를 매핑하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c35f3-174">Click to map a parameter or variable to a child package parameter.</span></span>  
  
 <span data-ttu-id="c35f3-175">**제거**</span><span class="sxs-lookup"><span data-stu-id="c35f3-175">**Remove**</span></span>  
 <span data-ttu-id="c35f3-176">매개 변수나 변수와 자식 패키지 매개 변수 간의 매핑을 제거하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c35f3-176">Click to remove a mapping between a parameter or variable and a child package parameter.</span></span>  
  
  
