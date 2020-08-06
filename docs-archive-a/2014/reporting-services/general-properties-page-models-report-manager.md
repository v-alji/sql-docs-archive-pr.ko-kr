---
title: 일반 속성 페이지, 모델 (보고서 관리자) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.swb.reportserver.modelproperties.general.f1
ms.assetid: 7ad59850-8135-4c4d-95e9-6d705b6d77a8
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 0fbd96392716c63fb739c6455bb1eac04912b93f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660357"
---
# <a name="general-properties-page-models-report-manager"></a><span data-ttu-id="e0b1f-102">일반 속성 페이지, 모델(보고서 관리자)</span><span class="sxs-lookup"><span data-stu-id="e0b1f-102">General Properties Page, Models (Report Manager)</span></span>
  <span data-ttu-id="e0b1f-103">보고서 모델의 일반 속성 페이지를 사용하여 모델 정의 파일(.smdl)의 이름을 바꾸거나 파일을 삭제, 이동 또는 대체할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0b1f-103">Use the General properties page for report models to rename, delete, move, or replace the model definition (.smdl) file.</span></span> <span data-ttu-id="e0b1f-104">모델을 만들거나 수정한 사람 및 변경된 시간에 대한 자세한 내용은 페이지 맨 위에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e0b1f-104">Details about who created or modified the model and when the changes took place are indicated at the top of the page.</span></span>  
  
## <a name="navigation"></a><span data-ttu-id="e0b1f-105">탐색</span><span class="sxs-lookup"><span data-stu-id="e0b1f-105">Navigation</span></span>  
 <span data-ttu-id="e0b1f-106">사용자 인터페이스(UI)에서 이 위치를 탐색하려면 다음 절차를 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="e0b1f-106">Use the following procedure to navigate to this location in the user interface (UI).</span></span>  
  
###### <a name="to-open-the-general-properties-page-for-a-model"></a><span data-ttu-id="e0b1f-107">모델의 일반 속성 페이지를 열려면</span><span class="sxs-lookup"><span data-stu-id="e0b1f-107">To open the General properties page for a model</span></span>  
  
1.  <span data-ttu-id="e0b1f-108">보고서 관리자를 열고 속성을 보거나 구성하려는 모델을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="e0b1f-108">Open Report Manager, and locate the model for which you want to view or configure properties.</span></span>  
  
2.  <span data-ttu-id="e0b1f-109">모델 위로 마우스를 이동하여 드롭다운 화살표를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e0b1f-109">Hover over the model, and click the drop-down arrow.</span></span>  
  
3.  <span data-ttu-id="e0b1f-110">드롭다운 메뉴에서 **관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e0b1f-110">In the drop-down menu, click **Manage**.</span></span> <span data-ttu-id="e0b1f-111">모델의 일반 속성 페이지가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="e0b1f-111">This opens the General properties page for the model.</span></span>  
  
## <a name="options"></a><span data-ttu-id="e0b1f-112">옵션</span><span class="sxs-lookup"><span data-stu-id="e0b1f-112">Options</span></span>  
 <span data-ttu-id="e0b1f-113">**이름**</span><span class="sxs-lookup"><span data-stu-id="e0b1f-113">**Name**</span></span>  
 <span data-ttu-id="e0b1f-114">모델의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e0b1f-114">Specifies the name of the model.</span></span> <span data-ttu-id="e0b1f-115">이름은 하나 이상의 영숫자 문자를 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0b1f-115">A name must contain at least one alphanumeric character.</span></span> <span data-ttu-id="e0b1f-116">공백과 특정 기호도 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0b1f-116">It can also include spaces and some symbols.</span></span> <span data-ttu-id="e0b1f-117">이름 지정 시에는 다음 문자를 사용하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="e0b1f-117">Do not use the following characters when specifying a name:</span></span>  
  
 <span data-ttu-id="e0b1f-118">; ?</span><span class="sxs-lookup"><span data-stu-id="e0b1f-118">; ?</span></span> <span data-ttu-id="e0b1f-119">: \@ & = +, $/\* \< > | " /</span><span class="sxs-lookup"><span data-stu-id="e0b1f-119">: \@ & = + , $ / \* \< > | " /</span></span>  
  
 <span data-ttu-id="e0b1f-120">**설명**</span><span class="sxs-lookup"><span data-stu-id="e0b1f-120">**Description**</span></span>  
 <span data-ttu-id="e0b1f-121">모델에 대한 설명을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="e0b1f-121">Type a description of the model.</span></span> <span data-ttu-id="e0b1f-122">이 설명은 해당 모델 액세스 권한이 있는 사용자의 내용 페이지에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e0b1f-122">This description appears in the Contents page to users who have permission to access the modelt.</span></span>  
  
 <span data-ttu-id="e0b1f-123">**목록 뷰에서 숨기기**</span><span class="sxs-lookup"><span data-stu-id="e0b1f-123">**Hidden in list view**</span></span>  
 <span data-ttu-id="e0b1f-124">폴더의 뷰 모드가 목록 뷰인 경우 항목을 숨기려면 이 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e0b1f-124">Select this check box to hide the item when the folder is set in list view.</span></span> <span data-ttu-id="e0b1f-125">목록 뷰는 보고서 관리자에서 지원되는 폴더 내용을 보기 위한 모드입니다.</span><span class="sxs-lookup"><span data-stu-id="e0b1f-125">List view is a mode for viewing folder contents that is supported in Report Manager.</span></span> <span data-ttu-id="e0b1f-126">[!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] 에서 이 옵션을 설정하여 해당 항목이 보고서 관리자에 표시되는 방법을 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0b1f-126">You can set this option in [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] to define how this item is viewed in Report Manager.</span></span> <span data-ttu-id="e0b1f-127">보고서 관리자의 보기 모드에 대 한 자세한 내용은 [내용 페이지 &#40;보고서 관리자&#41;](../../2014/reporting-services/contents-page-report-manager.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e0b1f-127">For more information about view modes in Report Manager, see [Contents Page &#40;Report Manager&#41;](../../2014/reporting-services/contents-page-report-manager.md).</span></span>  
  
 <span data-ttu-id="e0b1f-128">**적용**</span><span class="sxs-lookup"><span data-stu-id="e0b1f-128">**Apply**</span></span>  
 <span data-ttu-id="e0b1f-129">클릭하여 변경 내용을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="e0b1f-129">Click to save your changes.</span></span>  
  
 <span data-ttu-id="e0b1f-130">**삭제**</span><span class="sxs-lookup"><span data-stu-id="e0b1f-130">**Delete**</span></span>  
 <span data-ttu-id="e0b1f-131">클릭하여 보고서 서버 데이터베이스에서 모델을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="e0b1f-131">Click to remove the model from the report server database.</span></span> <span data-ttu-id="e0b1f-132">모델을 삭제해도 연결 정보를 제공하는 종속 공유 데이터 원본과 해당 모델을 데이터 원본으로 사용하는 보고서는 삭제되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e0b1f-132">Deleting a model does not delete the dependent shared data source that provides connection information, nor does it delete reports that use the model as a data source.</span></span> <span data-ttu-id="e0b1f-133">단, 모델이 삭제된 후 해당 모델을 사용하는 보고서는 더 이상 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e0b1f-133">However, after the model is deleted, reports that use the model will no longer run.</span></span>  
  
 <span data-ttu-id="e0b1f-134">**이동**</span><span class="sxs-lookup"><span data-stu-id="e0b1f-134">**Move**</span></span>  
 <span data-ttu-id="e0b1f-135">클릭하여 보고서 서버 폴더 계층 구조 내의 다른 위치로 모델을 옮깁니다.</span><span class="sxs-lookup"><span data-stu-id="e0b1f-135">Click to relocate a model within the report server folder hierarchy.</span></span> <span data-ttu-id="e0b1f-136">이 단추를 클릭하면 폴더를 검색하여 새 폴더 위치를 찾을 수 있는 항목 이동 페이지가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="e0b1f-136">Clicking this button opens the Move Items page, on which you can browse through folders for a new folder location.</span></span> <span data-ttu-id="e0b1f-137">자세한 내용은 [항목 이동 페이지 &#40;보고서 관리자&#41;](../../2014/reporting-services/move-items-page-report-manager.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e0b1f-137">For more information, see [Move Items Page &#40;Report Manager&#41;](../../2014/reporting-services/move-items-page-report-manager.md).</span></span>  
  
 <span data-ttu-id="e0b1f-138">**저장**</span><span class="sxs-lookup"><span data-stu-id="e0b1f-138">**Save**</span></span>  
 <span data-ttu-id="e0b1f-139">모델 정의의 읽기 전용 복사본을 저장하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e0b1f-139">Click to save a read-only copy of the model definition.</span></span> <span data-ttu-id="e0b1f-140">컴퓨터에 정의된 파일 연결에 따라 파일이 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 또는 다른 애플리케이션에서 열립니다.</span><span class="sxs-lookup"><span data-stu-id="e0b1f-140">Depending on the file associations defined on your computer, the file will open in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] or a different application.</span></span> <span data-ttu-id="e0b1f-141">대부분의 경우 모델은 XML 파일로 열립니다.</span><span class="sxs-lookup"><span data-stu-id="e0b1f-141">In most cases, the model opens as an XML file.</span></span>  
  
 <span data-ttu-id="e0b1f-142">사용자가 여는 복사본은 보고서 서버에 초기에 게시된 원래 모델 정의와 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="e0b1f-142">The copy that you open is identical to the original model definition that was initially published to the report server.</span></span> <span data-ttu-id="e0b1f-143">모델이 게시된 후 모델에 설정된 모든 속성(예: 데이터 원본 속성)은 여는 파일에 반영되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e0b1f-143">Any properties that were set on the model after it was published (such as data source properties) are not reflected in the file that you open.</span></span>  
  
 <span data-ttu-id="e0b1f-144">모델 정의를 수정하고 공유 폴더에 새 파일로 저장한 다음 보고서 서버에 새 항목으로 업로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0b1f-144">You can modify the model definition and save it as a new file in a shared folder, and upload the model definition to the report server as a new item.</span></span> <span data-ttu-id="e0b1f-145">모델 정의가 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 또는 다른 애플리케이션에서 열려 있는 동안 수정한 내용은 보고서 서버에 직접 저장되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e0b1f-145">Modifications that you make to the model definition while it is open in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] (or another application) are not saved directly to the report server.</span></span> <span data-ttu-id="e0b1f-146">수정한 모델을 보고서 서버에 게시하려면 해당 파일을 업로드해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0b1f-146">You must upload the file to publish the modified model to the report server.</span></span>  
  
 <span data-ttu-id="e0b1f-147">모델 디자이너에서 보고서 모델을 열려면 모델을 .smdl 파일로 저장한 다음 이 .smdl 파일을 모델 디자이너의 프로젝트에 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0b1f-147">Note that if you want to open the report model in Model Designer, you should save the model as .smdl file, and then add the .smdl file to a project in Model Designer.</span></span>  
  
 <span data-ttu-id="e0b1f-148">**바꾸기**</span><span class="sxs-lookup"><span data-stu-id="e0b1f-148">**Replace**</span></span>  
 <span data-ttu-id="e0b1f-149">파일 시스템의 .smdl 파일에 있는 다른 정의로 모델 정의를 대체하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e0b1f-149">Click to replace the model definition with a different one from an .smdl file located on the file system.</span></span> <span data-ttu-id="e0b1f-150">모델 정의를 업데이트하는 경우에는 업데이트를 완료한 후 공유 데이터 원본 설정을 다시 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0b1f-150">If you update a model definition, you must reset the shared data source settings after the update is complete.</span></span>  
  
 <span data-ttu-id="e0b1f-151">**모델 다시 생성**</span><span class="sxs-lookup"><span data-stu-id="e0b1f-151">**Regenerate Model**</span></span>  
 <span data-ttu-id="e0b1f-152">클릭하여 현재 버전을 대체하는 기본 모델을 다시 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="e0b1f-152">Click to regenerate a default model that replaces the current version.</span></span> <span data-ttu-id="e0b1f-153">이 옵션은 모델이 생성된 후에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="e0b1f-153">This option appears after the model is generated.</span></span> <span data-ttu-id="e0b1f-154">생성된 모델은 공유 데이터 원본을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0b1f-154">The generated model is based on the shared data source.</span></span> <span data-ttu-id="e0b1f-155">모델을 사용자 지정하려면 먼저 생성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0b1f-155">It cannot be customized before it is generated.</span></span> <span data-ttu-id="e0b1f-156">모델을 생성한 후에는 **편집** 을 클릭하여 모델 정의를 열고 파일 시스템에 이를 저장한 다음 모델 디자이너의 프로젝트에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0b1f-156">However, after you generate it, you can click **Edit** to open the model definition, save it to the file system, and then add it to a project in Model Designer.</span></span> <span data-ttu-id="e0b1f-157">모델을 구체화한 후에는 보고서 서버에 새 항목으로 업로드하거나 이 페이지의 **업데이트** 를 클릭하여 모델 디자이너에서 수정한 버전으로 생성된 버전을 대체할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0b1f-157">After you refine the model, you can upload it to the report server as a new item, or click **Update** on this page to replace the generated model with the version you revised in Model Designer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0b1f-158">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e0b1f-158">See Also</span></span>  
 <span data-ttu-id="e0b1f-159">[보고서 또는 모델을 공유 데이터 원본에 바인딩 &#40;SSRS&#41;](report-data/bind-a-report-or-model-to-a-shared-data-source-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="e0b1f-159">[Bind a Report or Model to a Shared Data Source &#40;SSRS&#41;](report-data/bind-a-report-or-model-to-a-shared-data-source-ssrs.md) </span></span>  
 [<span data-ttu-id="e0b1f-160">Management Studio의 보고서 서버 F1 도움말</span><span class="sxs-lookup"><span data-stu-id="e0b1f-160">Report Server in Management Studio F1 Help</span></span>](tools/report-server-in-management-studio-f1-help.md)  
  
  
