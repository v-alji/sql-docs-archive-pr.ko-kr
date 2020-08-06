---
title: 모델 배포 옵션(Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: cf1b17b4-47d5-4eba-83f9-fb0555806867
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 25af38deef2a5476f64f364116dc5e9168345fb2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740120"
---
# <a name="model-deployment-options-master-data-services"></a><span data-ttu-id="08861-102">모델 배포 옵션(Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="08861-102">Model Deployment Options (Master Data Services)</span></span>
  <span data-ttu-id="08861-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]에서 모델 패키지 파일을 배포할 때 새 모델이나 복제된 모델을 배포할지 또는 이전에 복제된 모델을 업데이트할지 여부를 결정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="08861-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], when you deploy a model package file, you must decide whether to deploy a new or cloned model, or to update a model that was previously cloned.</span></span>  
  
## <a name="workflows"></a><span data-ttu-id="08861-104">워크플로</span><span class="sxs-lookup"><span data-stu-id="08861-104">Workflows</span></span>  
 <span data-ttu-id="08861-105">모델 패키지로 작업할 때 사용하는 두 가지 주 워크플로가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="08861-105">When working with model packages, there are two primary workflows.</span></span>  
  
-   <span data-ttu-id="08861-106">테스트 환경에서 모델 패키지를 만들고 모델 복제본을 프로덕션 환경에 배포합니다.</span><span class="sxs-lookup"><span data-stu-id="08861-106">Create a package of a model in a test environment and deploy a clone of the model to a production environment.</span></span> <span data-ttu-id="08861-107">시간이 지나면 테스트 환경에서 프로덕션 환경으로 업데이트를 배포합니다.</span><span class="sxs-lookup"><span data-stu-id="08861-107">Over time, deploy updates from the test environment to the production environment.</span></span>  
  
-   <span data-ttu-id="08861-108">모델의 패키지를 만들고 동일한 환경에 새 모델로 배포합니다.</span><span class="sxs-lookup"><span data-stu-id="08861-108">Create a package of a model and deploy it as a new model to the same environment.</span></span> <span data-ttu-id="08861-109">이 경우 모델에 새 이름을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="08861-109">In this case, you must give the model a new name.</span></span>  
  
## <a name="options"></a><span data-ttu-id="08861-110">옵션</span><span class="sxs-lookup"><span data-stu-id="08861-110">Options</span></span>  
 <span data-ttu-id="08861-111">MDS 데이터베이스의 각 모델 개체에는 고유 ID(식별자)가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="08861-111">In the MDS database, each model object has a unique identifier (ID).</span></span> <span data-ttu-id="08861-112">이러한 ID는 모델 배포 패키지에 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="08861-112">These IDs are included in model deployment packages.</span></span> <span data-ttu-id="08861-113">패키지를 배포할 때 이러한 ID를 어떻게 처리할지 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="08861-113">When you deploy the package, you must choose what to do with these IDs.</span></span>  
  
 <span data-ttu-id="08861-114">다음 표에는 시스템 관리의 모델 배포 마법사나 MDSModelDeploy 도구를 사용하여 모델을 배포할 때 선택할 옵션을 결정하는 데 도움이 되는 정보가 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="08861-114">The following table should help you determine which choice to make when deploying a model by using either the System Administration model deployment wizard or the MDSModelDeploy tool.</span></span>  
  
|<span data-ttu-id="08861-115">옵션</span><span class="sxs-lookup"><span data-stu-id="08861-115">Option</span></span>|<span data-ttu-id="08861-116">설명</span><span class="sxs-lookup"><span data-stu-id="08861-116">Description</span></span>|<span data-ttu-id="08861-117">참고</span><span class="sxs-lookup"><span data-stu-id="08861-117">Notes</span></span>|  
|------------|-----------------|-----------|  
|<span data-ttu-id="08861-118">단추를 사용하여 새</span><span class="sxs-lookup"><span data-stu-id="08861-118">New</span></span>|<span data-ttu-id="08861-119">고유한 이름의 새 모델을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="08861-119">Create a new model with a unique name.</span></span> <span data-ttu-id="08861-120">모든 모델 개체에 대해 새 식별자가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="08861-120">New identifiers are created for all model objects.</span></span>|<span data-ttu-id="08861-121">새 식별자가 할당된 새 모델을 만들 경우 이후 모델 배포 도구를 사용하여 모델에 업데이트를 적용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="08861-121">If you create a new model with new identifiers, you cannot use model deployment tools to apply updates to the model later.</span></span> <span data-ttu-id="08861-122">웹 애플리케이션에서 마법사를 사용하여 모델 패키지를 배포하는 경우에는 동일한 이름이나 ID를 가진 모델이 이미 있는 경우에만 새 모델을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="08861-122">When using the wizard in the web application to deploy a model package, you have the option to create a new model only if a model with the same name or ID already exists.</span></span>|  
|<span data-ttu-id="08861-123">복제</span><span class="sxs-lookup"><span data-stu-id="08861-123">Clone</span></span>|<span data-ttu-id="08861-124">패키지의 모델을 그대로 복제하여 새 모델을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="08861-124">Create a new model that is an exact clone of the model in the package.</span></span> <span data-ttu-id="08861-125">이 방법은 해당 이름이나 식별자를 가진 모델이 대상 환경에 없는 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="08861-125">This works only if the model does not exist (by name or identifier) in the target environment.</span></span> <span data-ttu-id="08861-126">"복제" 옵션은 동일한 모델을 여러 환경에서 사용하려고 하며 시간이 지나면 복제한 모델을 업데이트하려는 경우에 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="08861-126">Use "clone" when you want to have the same model in multiple environments and update the cloned model over time.</span></span>|<span data-ttu-id="08861-127">웹 애플리케이션에서 마법사의 기본 동작입니다.</span><span class="sxs-lookup"><span data-stu-id="08861-127">This is the default behavior of the wizard in the web application.</span></span> <span data-ttu-id="08861-128">이름이나 ID가 같은 모델이 이미 있으면 대신 새 모델을 만들라는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="08861-128">If a model with the same name or ID already exists, you are prompted to create a new model instead.</span></span>|  
|<span data-ttu-id="08861-129">업데이트</span><span class="sxs-lookup"><span data-stu-id="08861-129">Update</span></span>|<span data-ttu-id="08861-130">기존 모델을 패키지의 모델로 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="08861-130">Update an existing model with the model in the package.</span></span> <span data-ttu-id="08861-131">두 모델의 식별자가 동일해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="08861-131">The identifiers must be the same in both models.</span></span> <span data-ttu-id="08861-132">이 옵션은 이전에 복제한 모델을 업데이트하는 데 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="08861-132">This is used to update a model that you previously cloned.</span></span>|<span data-ttu-id="08861-133">이전에 복제한 모델만 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="08861-133">You can only update models that were previously cloned.</span></span> <span data-ttu-id="08861-134">이름과 ID가 일치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="08861-134">(The names and IDs must match.)</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="08861-135">참고 항목</span><span class="sxs-lookup"><span data-stu-id="08861-135">See Also</span></span>  
 <span data-ttu-id="08861-136">[MDSModelDeploy를 사용 하 여 모델 배포 패키지 배포](../../2014/master-data-services/deploy-a-model-deployment-package-by-using-mdsmodeldeploy.md) </span><span class="sxs-lookup"><span data-stu-id="08861-136">[Deploy a Model Deployment Package by Using MDSModelDeploy](../../2014/master-data-services/deploy-a-model-deployment-package-by-using-mdsmodeldeploy.md) </span></span>  
 <span data-ttu-id="08861-137">[마법사를 사용 하 여 모델 배포 패키지 배포](../../2014/master-data-services/deploy-a-model-deployment-package-by-using-the-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="08861-137">[Deploy a Model Deployment Package by Using the Wizard](../../2014/master-data-services/deploy-a-model-deployment-package-by-using-the-wizard.md) </span></span>  
 [<span data-ttu-id="08861-138">모델 배포&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="08861-138">Deploying Models &#40;Master Data Services&#41;</span></span>](deploying-models-master-data-services.md)  
  
  
