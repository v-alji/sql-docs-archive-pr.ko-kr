---
title: MDSModelDeploy를 사용하여 모델 배포 패키지 배포 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: fb2a4df4-5e0d-4b34-818f-383dbde1b15c
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: c23dcc592c2de34fa87703c8ba58d949dfec455c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652878"
---
# <a name="deploy-a-model-deployment-package-by-using-mdsmodeldeploy"></a><span data-ttu-id="eca98-102">MDSModelDeploy를 사용하여 모델 배포 패키지 배포</span><span class="sxs-lookup"><span data-stu-id="eca98-102">Deploy a Model Deployment Package by Using MDSModelDeploy</span></span>
  <span data-ttu-id="eca98-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]에서 MDSModelDeploy 도구를 사용하여 다음 중 하나를 포함하는 패키지를 배포합니다.</span><span class="sxs-lookup"><span data-stu-id="eca98-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], use the MDSModelDeploy tool to deploy a package that contains either:</span></span>  
  
-   <span data-ttu-id="eca98-104">모델 개체만</span><span class="sxs-lookup"><span data-stu-id="eca98-104">Model objects only.</span></span>  
  
-   <span data-ttu-id="eca98-105">모델 개체 및 데이터</span><span class="sxs-lookup"><span data-stu-id="eca98-105">Model objects and data.</span></span>  
  
 <span data-ttu-id="eca98-106">모델 개체만 포함하는 패키지를 배포하려면 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 웹 애플리케이션에서 모델 배포 마법사를 대신 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eca98-106">If you want to deploy a package that contains model objects only, you can use the model deployment wizard in the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] web application instead.</span></span> <span data-ttu-id="eca98-107">자세한 내용은 [Deploy a Model Deployment Package by Using the Wizard](../../2014/master-data-services/deploy-a-model-deployment-package-by-using-the-wizard.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="eca98-107">For more information, see [Deploy a Model Deployment Package by Using the Wizard](../../2014/master-data-services/deploy-a-model-deployment-package-by-using-the-wizard.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="eca98-108">패키지는 해당 패키지를 만드는 데 사용한 버전의 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 에만 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eca98-108">Packages can be deployed to the edition of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] they were created in only.</span></span> <span data-ttu-id="eca98-109">따라서 [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] 에서 만든 패키지는 [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] 이상에 배포할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="eca98-109">This means that packages created in [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] cannot be deployed to [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] or higher.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="eca98-110">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="eca98-110">Prerequisites</span></span>  
 <span data-ttu-id="eca98-111">이 절차를 수행하려면</span><span class="sxs-lookup"><span data-stu-id="eca98-111">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="eca98-112">대상 **환경의** 시스템 관리 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 기능 영역에 액세스할 수 있는 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="eca98-112">You must have permission to access the **System Administration** functional area in the target [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] environment.</span></span>  
  
-   <span data-ttu-id="eca98-113">모델 배포 패키지가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="eca98-113">A model deployment package must exist.</span></span> <span data-ttu-id="eca98-114">자세한 내용은  [Create a Model Deployment Package by Using MDSModelDeploy](../../2014/master-data-services/create-a-model-deployment-package-by-using-mdsmodeldeploy.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="eca98-114">For more information, see  [Create a Model Deployment Package by Using MDSModelDeploy](../../2014/master-data-services/create-a-model-deployment-package-by-using-mdsmodeldeploy.md).</span></span>  
  
-   <span data-ttu-id="eca98-115">모델을 배포하는 환경에서 관리자여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="eca98-115">You must be an administrator in the environment where you are deploying the model.</span></span> <span data-ttu-id="eca98-116">자세한 내용은 [관리자 &#40;MDS(Master Data Services)&#41;](administrators-master-data-services.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="eca98-116">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="eca98-117">데이터로 모델을 업데이트하려는 경우 배포하려는 버전을 **잠금** 또는 **커밋됨** 상태로 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="eca98-117">If you are updating a model with data, the version you're deploying to cannot be **Locked** or **Committed**.</span></span>  
  
### <a name="to-deploy-a-model-deployment-package"></a><span data-ttu-id="eca98-118">모델 배포 패키지를 배포하려면</span><span class="sxs-lookup"><span data-stu-id="eca98-118">To deploy a model deployment package</span></span>  
  
1.  <span data-ttu-id="eca98-119">새 모델 또는 모델 복제를 배포할지 이전에 복제된 모델을 업데이트할지 여부를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="eca98-119">Determine whether you are deploying a new model, a clone of a model, or updating a previously-cloned model.</span></span> <span data-ttu-id="eca98-120">자세한 내용은 [모델 배포 옵션&#40;Master Data Services&#41;](../../2014/master-data-services/model-deployment-options-master-data-services.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="eca98-120">For more information, see [Model Deployment Options &#40;Master Data Services&#41;](../../2014/master-data-services/model-deployment-options-master-data-services.md).</span></span>  
  
2.  <span data-ttu-id="eca98-121">명령 프롬프트를 열고 MDSModelDeploy.exe로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="eca98-121">Open a command prompt and navigate to MDSModelDeploy.exe.</span></span>  
  
    -   <span data-ttu-id="eca98-122">MDS를 기본 위치에 설치 하는 경우이 도구는 *드라이브*: Files\Microsoft SQL Server\120\Master Data Services\Configuration\MDSModelDeploy.exe에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eca98-122">If MDS is installed at the default location, the tool is available at *drive*:\Program Files\Microsoft SQL Server\120\Master Data Services\Configuration\MDSModelDeploy.exe</span></span>  
  
    -   <span data-ttu-id="eca98-123">MDS를 기본 위치에 설치하지 않은 경우 로컬 컴퓨터에서 MDSModelDeploy.exe를 검색하십시오.</span><span class="sxs-lookup"><span data-stu-id="eca98-123">If MDS is not installed at the default location, search the local computer for MDSModelDeploy.exe.</span></span>  
  
3.  <span data-ttu-id="eca98-124">선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="eca98-124">Optional.</span></span> <span data-ttu-id="eca98-125">보기 옵션 및 도움말입니다.</span><span class="sxs-lookup"><span data-stu-id="eca98-125">View options and help.</span></span>  
  
    -   <span data-ttu-id="eca98-126">모든 사용 가능한 옵션을 표시하려면 `MDSModelDeploy` 를 입력하고 Enter 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="eca98-126">To display all available options, type `MDSModelDeploy` and press Enter.</span></span>  
  
    -   <span data-ttu-id="eca98-127">옵션에 대한 도움말을 표시하려면 *과 같이 입력합니다. 여기서* OptionName `MDSModelDeploy help OptionName`은 옵션의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="eca98-127">To display help for an option, type the following, where *OptionName* is the name of the option: `MDSModelDeploy help OptionName`.</span></span>  
  
4.  <span data-ttu-id="eca98-128">선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="eca98-128">Optional.</span></span> <span data-ttu-id="eca98-129">여러 웹 애플리케이션이 있는 경우 이 명령을 입력하고 Enter 키를 눌러 배포할 서비스의 이름을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="eca98-129">If you have multiple web applications, determine the name of the service you will deploy to by typing this command and pressing Enter:</span></span>  
  
    ```  
    MDSModelDeploy listservices  
    ```  
  
     <span data-ttu-id="eca98-130">값의 목록(예: `MDS1, Default Web Site, MDS`)이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="eca98-130">A list of values is returned, for example `MDS1, Default Web Site, MDS`.</span></span> <span data-ttu-id="eca98-131">이 목록의 첫 번째 값(이 경우 `MDS1`)은 모델을 배포하는 데 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="eca98-131">The first value in this list (in this case, `MDS1`) is needed to deploy the model.</span></span>  
  
5.  <span data-ttu-id="eca98-132">모델을 만들지, 복제할지 또는 업데이트할지에 따라 명령 프롬프트에 다음과 같이 입력하고 Enter 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="eca98-132">Depending on whether you are creating a model, cloning a model, or updating a model, at the command prompt, type the following and press Enter.</span></span>  
  
    -   <span data-ttu-id="eca98-133">새 모델을 만들려면</span><span class="sxs-lookup"><span data-stu-id="eca98-133">To create a new model:</span></span>  
  
        ```  
        MDSModelDeploy deploynew -package PackageName -model ModelName -service ServiceName  
        ```  
  
    -   <span data-ttu-id="eca98-134">모델 복제를 만들려면</span><span class="sxs-lookup"><span data-stu-id="eca98-134">To create a clone of a model:</span></span>  
  
        ```  
        MDSModelDeploy deployclone -package PackageName  
        ```  
  
    -   <span data-ttu-id="eca98-135">기존 모델과 해당 데이터를 업데이트하려면</span><span class="sxs-lookup"><span data-stu-id="eca98-135">To update an existing model and its data:</span></span>  
  
        ```  
        MDSModelDeploy deployupdate -package PackageName -version VersionName  
        ```  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="eca98-136">MDSModelDeploy 도구를 사용하여 기존 모델 및 해당 데이터를 업데이트하고 패키지에 엔터티, 특성 또는 대상 모델에 있는 멤버를 포함하지 않는 경우 MDSModelDeploy는 모델에서 해당 엔터티, 특성 또는 멤버를 삭제하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eca98-136">If you use the MDSModelDeploy tool to update an existing model and its data, and the package does not contain an entity, attribute, or member that exists in the destination model, MDSModelDeploy will not delete that entity, attribute, or member from the model.</span></span>  
  
     <span data-ttu-id="eca98-137">여기서 *PackageName* 은 패키지 파일(.pkg)의 이름이고, *ModelName* 은 새 모델의 이름이고, *VersionName* 은 버전 이름이고, *ServiceName* 은 이전 단계에서 반환된 서비스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="eca98-137">Where *PackageName* is the name of the package (.pkg) file, *ModelName* is the name of the new model, *VersionName* is the name of the version, and *ServiceName* is the name of the service that you returned in the previous step.</span></span> <span data-ttu-id="eca98-138">모델 및 버전 이름이 대/소문자가 구분되는 이름과 정확하게 일치하는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="eca98-138">Ensure that the model and version names match the exact case-sensitive names.</span></span>  
  
6.  <span data-ttu-id="eca98-139">패키지가 성공적으로 배포되면 "MDSModelDeploy 작업이 성공적으로 완료되었습니다."라는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="eca98-139">When the package is successfully deployed, a message stating "MDSModelDeploy operation completed successfully" is displayed.</span></span>  
  
 <span data-ttu-id="eca98-140">**참고:**</span><span class="sxs-lookup"><span data-stu-id="eca98-140">**Notes:**</span></span>  
  
-   <span data-ttu-id="eca98-141">패키지의 구독 뷰 이름이 기존 모델의 구독 뷰와 동일 하면 뷰가 *subscriptionviewname*로 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="eca98-141">If a subscription view in the package has the same name as a subscription view in an existing model, the view is created as *modelname.subscriptionviewname*.</span></span> <span data-ttu-id="eca98-142">이 이름이 이미 사용 중이면 구독 뷰가 만들어지지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eca98-142">If this name is already in use, the subscription view is not created.</span></span>  
  
-   <span data-ttu-id="eca98-143">배포 프로세스는 다음과 같은 4단계로 진행됩니다.</span><span class="sxs-lookup"><span data-stu-id="eca98-143">The deployment process has four steps:</span></span>  
  
    1.  <span data-ttu-id="eca98-144">모델 개체가 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="eca98-144">The model objects are created.</span></span>  
  
    2.  <span data-ttu-id="eca98-145">비즈니스 규칙이 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="eca98-145">Business rules are created.</span></span>  
  
    3.  <span data-ttu-id="eca98-146">구독 뷰가 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="eca98-146">Subscription views are created.</span></span>  
  
    4.  <span data-ttu-id="eca98-147">마스터 데이터가 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="eca98-147">Master data is populated.</span></span>  
  
-   <span data-ttu-id="eca98-148">새 모델 또는 복제된 모델을 만들 때 단계 실행 중 프로세스가 실패하면 모델이 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="eca98-148">When creating a new or cloned model, if the process fails during any step, the model is deleted.</span></span>  
  
     <span data-ttu-id="eca98-149">모델을 업데이트할 때 처음 3단계 동안 프로세스가 실패하면 진행되지 않습니다. 그러나 이미 수행한 변경 내용은 롤백되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eca98-149">When updating a model, if the process fails during the first three steps, it does not proceed; however, changes that are already made are not rolled back.</span></span> <span data-ttu-id="eca98-150">4단계에서 프로세스가 실패하면 업데이트 가능한 멤버가 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="eca98-150">If the process fails in step 4, members that can be updated are updated.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="eca98-151">다음 단계</span><span class="sxs-lookup"><span data-stu-id="eca98-151">Next Steps</span></span>  
 <span data-ttu-id="eca98-152">사용자 정의 메타데이터, 파일 특성, 사용자 및 그룹 권한은 모델 배포 패키지에 포함되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eca98-152">User-defined metadata, file attributes, and user and group permissions are not included in model deployment packages.</span></span> <span data-ttu-id="eca98-153">모델을 배포한 후에 이러한 항목을 수동으로 업데이트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="eca98-153">After you deploy a model, you must update these manually.</span></span> <span data-ttu-id="eca98-154">자세한 내용은 다음을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="eca98-154">For more information, see:</span></span>  
  
-   [<span data-ttu-id="eca98-155">메타 데이터 &#40;추가 MDS(Master Data Services)&#41;</span><span class="sxs-lookup"><span data-stu-id="eca98-155">Add Metadata &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/add-metadata-master-data-services.md)  
  
-   [<span data-ttu-id="eca98-156">모델 개체 사용 권한 할당&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="eca98-156">Assign Model Object Permissions &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/assign-model-object-permissions-master-data-services.md)  
  
## <a name="see-also"></a><span data-ttu-id="eca98-157">참고 항목</span><span class="sxs-lookup"><span data-stu-id="eca98-157">See Also</span></span>  
 [<span data-ttu-id="eca98-158">모델 배포&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="eca98-158">Deploying Models &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/deploying-models-master-data-services.md)  
  
  
