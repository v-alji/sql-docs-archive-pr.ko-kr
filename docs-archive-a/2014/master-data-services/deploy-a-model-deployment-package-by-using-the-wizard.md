---
title: 마법사를 사용하여 모델 배포 패키지 배포 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- deployment packages [Master Data Services], deploying
- models [Master Data Services], deploying a package
ms.assetid: 4f65dc60-0ff8-46e6-9988-5bc5b9603ad0
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 75af9f7c12d866c6d9707f62c898aa7601f94800
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736454"
---
# <a name="deploy-a-model-deployment-package-by-using-the-wizard"></a><span data-ttu-id="93fe5-102">마법사를 사용하여 모델 배포 패키지 배포</span><span class="sxs-lookup"><span data-stu-id="93fe5-102">Deploy a Model Deployment Package by Using the Wizard</span></span>
  <span data-ttu-id="93fe5-103">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 모델 배포 마법사를 사용하여 모델 개체만 포함된 패키지를 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="93fe5-103">Use the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] model deployment wizard to deploy packages that contain model objects only.</span></span> <span data-ttu-id="93fe5-104">데이터가 포함된 패키지를 배포해야 하는 경우 [MDSModelDeploy를 사용하여 모델 배포 패키지 배포](../../2014/master-data-services/deploy-a-model-deployment-package-by-using-mdsmodeldeploy.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="93fe5-104">If you need to deploy a package with data, see [Deploy a Model Deployment Package by Using MDSModelDeploy](../../2014/master-data-services/deploy-a-model-deployment-package-by-using-mdsmodeldeploy.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="93fe5-105">패키지는 해당 패키지를 만드는 데 사용한 버전의 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 에만 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="93fe5-105">Packages can be deployed to the edition of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] they were created in only.</span></span> <span data-ttu-id="93fe5-106">따라서 [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] 에서 만든 패키지는 [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]에 배포할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="93fe5-106">This means that packages created in [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] cannot be deployed to [!INCLUDE[ssSQL11](../includes/sssql11-md.md)].</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="93fe5-107">필수 조건</span><span class="sxs-lookup"><span data-stu-id="93fe5-107">Prerequisites</span></span>  
 <span data-ttu-id="93fe5-108">이 절차를 수행하려면</span><span class="sxs-lookup"><span data-stu-id="93fe5-108">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="93fe5-109">대상 **환경의** 시스템 관리 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 기능 영역에 액세스할 수 있는 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="93fe5-109">You must have permission to access the **System Administration** functional area in the target [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] environment.</span></span>  
  
-   <span data-ttu-id="93fe5-110">모델 배포 패키지가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="93fe5-110">A model deployment package must exist.</span></span> <span data-ttu-id="93fe5-111">자세한 내용은 [마법사를 사용하여 모델 배포 패키지 만들기](../../2014/master-data-services/create-a-model-deployment-package-by-using-the-wizard.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="93fe5-111">For more information, see [Create a Model Deployment Package by Using the Wizard](../../2014/master-data-services/create-a-model-deployment-package-by-using-the-wizard.md).</span></span>  
  
-   <span data-ttu-id="93fe5-112">모델을 배포하는 환경에서 관리자여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="93fe5-112">You must be an administrator in the environment where you are deploying the model.</span></span> <span data-ttu-id="93fe5-113">자세한 내용은 [관리자 &#40;MDS(Master Data Services)&#41;](administrators-master-data-services.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="93fe5-113">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
### <a name="to-deploy-a-model-deployment-package-of-model-objects-only"></a><span data-ttu-id="93fe5-114">모델 개체의 모델 배포 패키지만 배포하려면</span><span class="sxs-lookup"><span data-stu-id="93fe5-114">To deploy a model deployment package of model objects only</span></span>  
  
1.  <span data-ttu-id="93fe5-115">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]에서 **시스템 관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="93fe5-115">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="93fe5-116">**모델 뷰** 페이지의 메뉴 모음에서 **시스템** 을 가리키고 **배포**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="93fe5-116">On the **Model View** page, from the menu bar, point to **System** and click **Deployment**.</span></span>  
  
3.  <span data-ttu-id="93fe5-117">**모델 배포 마법사**에서 **배포**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="93fe5-117">On the **Model Deployment Wizard**, click **Deploy**.</span></span>  
  
4.  <span data-ttu-id="93fe5-118">**찾아보기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="93fe5-118">Click **Browse**.</span></span>  
  
5.  <span data-ttu-id="93fe5-119">배포 패키지(.pkg 파일)를 찾은 다음 **열기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="93fe5-119">Find your deployment package (.pkg file) and click **Open**.</span></span>  
  
6.  <span data-ttu-id="93fe5-120">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="93fe5-120">Click **Next**.</span></span>  
  
7.  <span data-ttu-id="93fe5-121">패키지가 로드되면 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="93fe5-121">After the package is loaded, click **Next**.</span></span>  
  
8.  <span data-ttu-id="93fe5-122">모델이 이미 있는 경우 **기존 모델 업데이트**를 선택하여 해당 모델을 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="93fe5-122">If the model already exists, you can update it by selecting **Update the existing model**.</span></span> <span data-ttu-id="93fe5-123">새 모델을 만들려는 경우 **새 모델 만들기** 를 선택하고 **다음** 을 클릭하면 새 모델의 이름을 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="93fe5-123">To create a new model, select **Create a new model** and after you click **Next** you can type a name for the new model.</span></span>  
  
9. <span data-ttu-id="93fe5-124">마법사를 끝내려면 **마침**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="93fe5-124">Click **Finish** to exit the wizard.</span></span>  
  
 <span data-ttu-id="93fe5-125">**참고:**</span><span class="sxs-lookup"><span data-stu-id="93fe5-125">**Notes:**</span></span>  
  
-   <span data-ttu-id="93fe5-126">패키지의 구독 뷰 이름이 기존 모델의 구독 뷰와 동일 하면 뷰가 *subscriptionviewname*로 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="93fe5-126">If a subscription view in the package has the same name as a subscription view in an existing model, the view is created as *modelname.subscriptionviewname*.</span></span> <span data-ttu-id="93fe5-127">이 이름이 이미 사용 중이면 구독 뷰가 만들어지지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="93fe5-127">If this name is already in use, the subscription view is not created.</span></span>  
  
-   <span data-ttu-id="93fe5-128">배포 프로세스는 다음과 같은 4단계로 진행됩니다.</span><span class="sxs-lookup"><span data-stu-id="93fe5-128">The deployment process has four steps:</span></span>  
  
    1.  <span data-ttu-id="93fe5-129">모델 개체가 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="93fe5-129">The model objects are created.</span></span>  
  
    2.  <span data-ttu-id="93fe5-130">구독 뷰가 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="93fe5-130">Subscription views are created.</span></span>  
  
    3.  <span data-ttu-id="93fe5-131">비즈니스 규칙이 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="93fe5-131">Business rules are created.</span></span>  
  
    4.  <span data-ttu-id="93fe5-132">마스터 데이터가 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="93fe5-132">Master data is populated.</span></span>  
  
-   <span data-ttu-id="93fe5-133">새 모델 또는 복제된 모델을 만들 때 단계 실행 중 프로세스가 실패하면 모델이 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="93fe5-133">When creating a new or cloned model, if the process fails during any step, the model is deleted.</span></span>  
  
     <span data-ttu-id="93fe5-134">모델을 업데이트할 때 처음 3단계 동안 프로세스가 실패하면 해당 단계 다음으로 진행되지 않습니다. 그러나 이미 수행한 변경 내용은 롤백되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="93fe5-134">When updating a model, if the process fails during any of the first three steps, it does not proceed beyond that step; however, changes that are already made are not rolled back.</span></span> <span data-ttu-id="93fe5-135">4단계에서 프로세스가 실패하면 업데이트 가능한 멤버가 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="93fe5-135">If the process fails in step 4, members that can be updated are updated.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="93fe5-136">다음 단계</span><span class="sxs-lookup"><span data-stu-id="93fe5-136">Next Steps</span></span>  
 <span data-ttu-id="93fe5-137">사용자 정의 메타데이터, 파일 특성, 사용자 및 그룹 권한은 모델 배포 패키지에 포함되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="93fe5-137">User-defined metadata, file attributes, and user and group permissions are not included in model deployment packages.</span></span> <span data-ttu-id="93fe5-138">모델을 배포한 후에 이러한 항목을 수동으로 업데이트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="93fe5-138">After you deploy a model, you must update these manually.</span></span> <span data-ttu-id="93fe5-139">자세한 내용은 다음을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="93fe5-139">For more information, see:</span></span>  
  
-   [<span data-ttu-id="93fe5-140">메타 데이터 &#40;추가 MDS(Master Data Services)&#41;</span><span class="sxs-lookup"><span data-stu-id="93fe5-140">Add Metadata &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/add-metadata-master-data-services.md)  
  
-   [<span data-ttu-id="93fe5-141">모델 개체 사용 권한 할당&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="93fe5-141">Assign Model Object Permissions &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/assign-model-object-permissions-master-data-services.md)  
  
## <a name="see-also"></a><span data-ttu-id="93fe5-142">참고 항목</span><span class="sxs-lookup"><span data-stu-id="93fe5-142">See Also</span></span>  
 [<span data-ttu-id="93fe5-143">모델 배포&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="93fe5-143">Deploying Models &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/deploying-models-master-data-services.md)  
  
  
