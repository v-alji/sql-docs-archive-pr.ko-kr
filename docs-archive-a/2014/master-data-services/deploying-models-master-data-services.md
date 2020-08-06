---
title: 모델 배포(Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- deployment packages [Master Data Services], about deployment packages
- deployment packages [Master Data Services]
ms.assetid: 30085c08-034f-4efe-80fe-408f9091ff5c
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: a9cc99112ec874e89ae07faa575235d9a041a972
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661698"
---
# <a name="deploying-models-master-data-services"></a><span data-ttu-id="9c5c0-102">모델 배포(Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="9c5c0-102">Deploying Models (Master Data Services)</span></span>
  <span data-ttu-id="9c5c0-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]에서 패키지는 배포 가능한 모델 구조와 모델의 데이터(옵션)를 포함하는 XML 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="9c5c0-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], a package is an XML file that contains a deployable model structure, and optionally, data from the model.</span></span> <span data-ttu-id="9c5c0-104">모델 패키지를 사용하여 MDS 환경 간에 모델의 복사본을 이동하거나 기존 MDS 환경에 새로운 모델을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="9c5c0-104">Use model packages to move copies of models from one MDS environment to another, or to create new models in your existing MDS environment.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="9c5c0-105">패키지는 해당 패키지를 만드는 데 사용한 버전의 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 에만 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9c5c0-105">Packages can be deployed to the edition of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] they were created in only.</span></span> <span data-ttu-id="9c5c0-106">따라서 [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] 에서 만든 패키지는 [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] 이상에 배포할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9c5c0-106">This means that packages created in [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] cannot be deployed to [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] or higher.</span></span>  
  
## <a name="tools-for-deploying-models"></a><span data-ttu-id="9c5c0-107">모델 배포 도구</span><span class="sxs-lookup"><span data-stu-id="9c5c0-107">Tools for Deploying Models</span></span>  
 <span data-ttu-id="9c5c0-108">모델 패키지를 사용하려면 필요에 따라 다음 세 도구 중 하나를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5c0-108">To work with model packages, you can use one of three tools, depending on your needs.</span></span>  
  
-   <span data-ttu-id="9c5c0-109">**MDSModelDeploy 도구**: 모델 개체와 데이터를 만들고 배포하려면 MDSModelDeploy.exe 도구를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5c0-109">**MDSModelDeploy tool**: To create and deploy model objects and data, use the MDSModelDeploy.exe tool.</span></span> <span data-ttu-id="9c5c0-110">MDS 설치 시 기본 경로를 선택한 경우이 도구는 *드라이브*: Files\Microsoft SQL Server\120\Master Data services\configuration에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9c5c0-110">If you selected the default path when installing MDS, this tool is located on *drive*:\Program Files\Microsoft SQL Server\120\Master Data Services\Configuration.</span></span>  
  
-   <span data-ttu-id="9c5c0-111">**모델 배포 마법사**: 모델 구조만의 패키지를 만들고 배포하려면 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 웹 애플리케이션의 마법사를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5c0-111">**Model Deployment wizard**: To create and deploy packages of the model structure only, use the wizard in the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] web application.</span></span> <span data-ttu-id="9c5c0-112">이 마법사를 사용하여 데이터를 배포할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9c5c0-112">You cannot use this wizard to deploy data.</span></span>  
  
-   <span data-ttu-id="9c5c0-113">**모델 패키지 편집기**: 모델 패키지를 편집하려면 모델 패키지 편집기 마법사를 실행하는 ModelPackageEditor.exe를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5c0-113">**Model Package Editor**: To edit a model package, use the ModelPackageEditor.exe that launches the Model Package Editor wizard.</span></span> <span data-ttu-id="9c5c0-114">이 마법사를 사용하여 MDSModelDeploy 도구 또는 모델 배포 마법사로 만든 패키지를 편집합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5c0-114">You use this wizard to edit a package that was created by the MDSModelDeploy tool or the Model Deployment wizard.</span></span> <span data-ttu-id="9c5c0-115">MDS 설치 시 기본 경로를 선택한 경우이 도구는 *드라이브*: Files\Microsoft SQL Server\120\Master Data services\configuration에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9c5c0-115">If you selected the default path when installing MDS, this tool is located on *drive*:\Program Files\Microsoft SQL Server\120\Master Data Services\Configuration.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="9c5c0-116">MDSDeployModel을 사용하여 새 모델을 만들거나 모델의 복제본을 만들거나 기존 모델 및 해당 데이터를 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9c5c0-116">You can use the MDSDeployModel to create a new model, create a clone of a model, or update an existing model and its data.</span></span> <span data-ttu-id="9c5c0-117">MDSModelDeploy 도구를 사용하여 기존 모델 및 해당 데이터를 업데이트하고 패키지에 엔터티, 특성 또는 대상 모델에 있는 멤버를 포함하지 않는 경우 MDSModelDeploy는 모델에서 해당 엔터티, 특성 또는 멤버를 삭제하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9c5c0-117">If you use the MDSModelDeploy tool to update an existing model and its data, and the package does not contain an entity, attribute, or member that exists in the destination model, MDSModelDeploy will not delete that entity, attribute, or member from the model.</span></span>  
  
## <a name="what-packages-contain"></a><span data-ttu-id="9c5c0-118">패키지에 포함된 내용</span><span class="sxs-lookup"><span data-stu-id="9c5c0-118">What Packages Contain</span></span>  
 <span data-ttu-id="9c5c0-119">모델 패키지는 .pkg 확장명으로 저장되는 XML 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="9c5c0-119">A model package is an XML file that is saved with the .pkg extension.</span></span> <span data-ttu-id="9c5c0-120">배포 패키지를 만드는 경우 데이터 포함 여부를 결정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9c5c0-120">When you create a deployment package, you can decide whether or not to include data.</span></span> <span data-ttu-id="9c5c0-121">데이터를 포함하려면 포함할 데이터의 버전을 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5c0-121">If you decide to include data, you must select a version of the data to include.</span></span>  
  
 <span data-ttu-id="9c5c0-122">모든 모델 개체가 패키지에 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="9c5c0-122">All model objects are included in a package.</span></span> <span data-ttu-id="9c5c0-123">모델 개체는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="9c5c0-123">These objects are:</span></span>  
  
-   <span data-ttu-id="9c5c0-124">엔터티</span><span class="sxs-lookup"><span data-stu-id="9c5c0-124">Entities</span></span>  
  
-   <span data-ttu-id="9c5c0-125">특성</span><span class="sxs-lookup"><span data-stu-id="9c5c0-125">Attributes</span></span>  
  
-   <span data-ttu-id="9c5c0-126">특성 그룹</span><span class="sxs-lookup"><span data-stu-id="9c5c0-126">Attribute groups</span></span>  
  
-   <span data-ttu-id="9c5c0-127">계층 구조</span><span class="sxs-lookup"><span data-stu-id="9c5c0-127">Hierarchies</span></span>  
  
-   <span data-ttu-id="9c5c0-128">컬렉션</span><span class="sxs-lookup"><span data-stu-id="9c5c0-128">Collections</span></span>  
  
-   <span data-ttu-id="9c5c0-129">비즈니스 규칙</span><span class="sxs-lookup"><span data-stu-id="9c5c0-129">Business rules</span></span>  
  
-   <span data-ttu-id="9c5c0-130">버전 플래그</span><span class="sxs-lookup"><span data-stu-id="9c5c0-130">Version flags</span></span>  
  
-   <span data-ttu-id="9c5c0-131">구독 뷰</span><span class="sxs-lookup"><span data-stu-id="9c5c0-131">Subscription views</span></span>  
  
 <span data-ttu-id="9c5c0-132">사용자 정의 메타데이터, 파일 특성, 사용자 및 그룹 권한은 포함되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9c5c0-132">User-defined metadata, file attributes, and user and group permissions are not included.</span></span> <span data-ttu-id="9c5c0-133">모델을 배포한 후에 이러한 항목을 수동으로 업데이트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5c0-133">After you deploy a model, you must update these manually.</span></span>  
  
## <a name="sample-packages"></a><span data-ttu-id="9c5c0-134">예제 패키지</span><span class="sxs-lookup"><span data-stu-id="9c5c0-134">Sample Packages</span></span>  
 <span data-ttu-id="9c5c0-135">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]를 설치하면 예제 패키지 파일이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="9c5c0-135">Sample package files are included when you install [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)].</span></span> <span data-ttu-id="9c5c0-136">이러한 패키지 파일은 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]를 설치한 Master Data Services\Samples\Packages 디렉터리에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9c5c0-136">These package files are in the Master Data Services\Samples\Packages directory where you installed [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)].</span></span> <span data-ttu-id="9c5c0-137">MDSModelDeploy 도구를 사용하여 이러한 예제 패키지를 배포하면 예제 모델이 생성되어 데이터로 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="9c5c0-137">When you deploy these sample packages by using the MDSModelDeploy tool, sample models are created and populated with data.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="9c5c0-138">관련 작업</span><span class="sxs-lookup"><span data-stu-id="9c5c0-138">Related Tasks</span></span>  
  
|<span data-ttu-id="9c5c0-139">태스크 설명</span><span class="sxs-lookup"><span data-stu-id="9c5c0-139">Task Description</span></span>|<span data-ttu-id="9c5c0-140">항목</span><span class="sxs-lookup"><span data-stu-id="9c5c0-140">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="9c5c0-141">MDSModelDeploy 도구를 사용하여 모델 개체 및/또는 데이터의 새 배포 패키지를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="9c5c0-141">Create a new deployment package of model objects and/or data by using the MDSModelDeploy tool.</span></span>|[<span data-ttu-id="9c5c0-142">MDSModelDeploy를 사용하여 모델 배포 패키지 만들기</span><span class="sxs-lookup"><span data-stu-id="9c5c0-142">Create a Model Deployment Package by Using MDSModelDeploy</span></span>](../../2014/master-data-services/create-a-model-deployment-package-by-using-mdsmodeldeploy.md)|  
|<span data-ttu-id="9c5c0-143">마법사를 사용하여 모델 개체만의 새 배포 패키지를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="9c5c0-143">Create a new deployment package of model objects only by using the wizard.</span></span>|[<span data-ttu-id="9c5c0-144">마법사를 사용하여 모델 배포 패키지 만들기</span><span class="sxs-lookup"><span data-stu-id="9c5c0-144">Create a Model Deployment Package by Using the Wizard</span></span>](../../2014/master-data-services/create-a-model-deployment-package-by-using-the-wizard.md)|  
|<span data-ttu-id="9c5c0-145">MDSModelDeploy 도구를 사용하여 모델 개체 및/또는 데이터의 패키지를 배포합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5c0-145">Deploy a package of model objects and data by using the MDSModelDeploy tool.</span></span>|[<span data-ttu-id="9c5c0-146">MDSModelDeploy를 사용하여 모델 배포 패키지 배포</span><span class="sxs-lookup"><span data-stu-id="9c5c0-146">Deploy a Model Deployment Package by Using MDSModelDeploy</span></span>](../../2014/master-data-services/deploy-a-model-deployment-package-by-using-mdsmodeldeploy.md)|  
|<span data-ttu-id="9c5c0-147">마법사를 사용하여 모델 개체만의 패키지를 배포합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5c0-147">Deploy a package of model objects only by using the wizard.</span></span>|[<span data-ttu-id="9c5c0-148">마법사를 사용하여 모델 배포 패키지 배포</span><span class="sxs-lookup"><span data-stu-id="9c5c0-148">Deploy a Model Deployment Package by Using the Wizard</span></span>](../../2014/master-data-services/deploy-a-model-deployment-package-by-using-the-wizard.md)|  
|<span data-ttu-id="9c5c0-149">모델 배포 패키지를 편집하여 전체 모델이 아닌 모델의 일부 선택한 부분만 배포합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5c0-149">Edit a model deployment package to deploy selected parts of a model, rather than the entire model.</span></span>|[<span data-ttu-id="9c5c0-150">모델 배포 패키지 편집</span><span class="sxs-lookup"><span data-stu-id="9c5c0-150">Edit a Model Deployment Package</span></span>](../../2014/master-data-services/edit-a-model-deployment-package.md)|  
  
## <a name="related-content"></a><span data-ttu-id="9c5c0-151">관련 내용</span><span class="sxs-lookup"><span data-stu-id="9c5c0-151">Related Content</span></span>  
  
-   [<span data-ttu-id="9c5c0-152">모델 배포 옵션&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="9c5c0-152">Model Deployment Options &#40;Master Data Services&#41;</span></span>](model-deployment-options-master-data-services.md)  
  
  
