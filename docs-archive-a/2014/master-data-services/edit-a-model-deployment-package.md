---
title: 모델 배포 패키지 편집 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 6b0fdb7d-83dd-4392-9011-4ae642c471f1
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: b8bfd7083e2ba763d15a405266260b5a096c8378
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661681"
---
# <a name="edit-a-model-deployment-package"></a><span data-ttu-id="ee89d-102">모델 배포 패키지 편집</span><span class="sxs-lookup"><span data-stu-id="ee89d-102">Edit a Model Deployment Package</span></span>
  <span data-ttu-id="ee89d-103">이 항목에서는 MDS에서 전체 모델 대신 모델의 선택한 부분을 배포하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="ee89d-103">This topic describes how to deploy selected parts of a model in MDS, rather than an entire model.</span></span> <span data-ttu-id="ee89d-104">이렇게 하려면 모델 패키지 편집기를 사용하여 MDS 모델 패키지를 편집하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ee89d-104">To do so, you edit an MDS model package using the Model Package Editor.</span></span>  
  
 <span data-ttu-id="ee89d-105">모델 패키지 편집기 마법사에서는 MDS 패키지에 포함할 모델의 특정 엔터티, 파생 계층, 구독 뷰 및 비즈니스 규칙을 선택한 다음 나중에 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ee89d-105">The Model Package Editor wizard enables you to select the specific entities, derived hierarchies, subscription views, and business rules in a model that you want to include in an MDS package, and then later deploy.</span></span> <span data-ttu-id="ee89d-106">모델에서 배포하지 않으려는 부분은 그대로 남겨 둘 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ee89d-106">You can leave out those parts of the model that you do not want to deploy.</span></span> <span data-ttu-id="ee89d-107">엔터티를 선택하면 해당 엔터티의 모든 종속 개체도 자동으로 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="ee89d-107">When you select an entity, all of the dependent objects in that entity are also automatically selected.</span></span>  
  
 <span data-ttu-id="ee89d-108">모델 패키지 편집기를 사용하여 MDSModelDeploy 도구(개체 및 데이터가 포함된 패키지 파일을 만드는 도구) 또는 모델 배포 마법사(모델 구조만 포함된 파일을 만드는 도구)를 사용하여 만든 패키지 파일에서 모델의 일부분을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ee89d-108">You use the Model Package Editor to select parts of a model in a package file that was created by either the MDSModelDeploy tool (which creates a package file that includes objects and data) or the Model Deployment wizard (which creates a file that includes only the model structure).</span></span> <span data-ttu-id="ee89d-109">패키지의 모델을 편집한 후에는 MDSModelDeploy 도구를 사용하여 개체 및 데이터를 배포하거나 모델 배포 마법사를 사용하여 모델 구조만 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ee89d-109">After editing the model in the package, you use the MDSModelDeploy tool to deploy objects and data, or the Model Deployment wizard to deploy just the model structure.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="ee89d-110">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="ee89d-110">Prerequisites</span></span>  
 <span data-ttu-id="ee89d-111">이 절차를 수행하려면</span><span class="sxs-lookup"><span data-stu-id="ee89d-111">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="ee89d-112">모델 관리자여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ee89d-112">You must be a model administrator.</span></span> <span data-ttu-id="ee89d-113">자세한 내용은 [관리자 &#40;MDS(Master Data Services)&#41;](administrators-master-data-services.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ee89d-113">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="ee89d-114">편집할 모델 패키지가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ee89d-114">A model package must exist for you to edit.</span></span> <span data-ttu-id="ee89d-115">자세한 내용은 [모델 배포&#40;Master Data Services&#41;](../../2014/master-data-services/deploying-models-master-data-services.md) 및 [마법사를 사용하여 모델 배포 패키지 만들기](../../2014/master-data-services/create-a-model-deployment-package-by-using-the-wizard.md) 또는 [MDSModelDeploy를 사용하여 모델 배포 패키지 만들기](../../2014/master-data-services/create-a-model-deployment-package-by-using-mdsmodeldeploy.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ee89d-115">For more information, see [Deploying Models &#40;Master Data Services&#41;](../../2014/master-data-services/deploying-models-master-data-services.md) and [Create a Model Deployment Package by Using the Wizard](../../2014/master-data-services/create-a-model-deployment-package-by-using-the-wizard.md) or [Create a Model Deployment Package by Using MDSModelDeploy](../../2014/master-data-services/create-a-model-deployment-package-by-using-mdsmodeldeploy.md).</span></span>  
  
### <a name="to-edit-a-model-deployment-package"></a><span data-ttu-id="ee89d-116">모델 배포 패키지를 편집하려면</span><span class="sxs-lookup"><span data-stu-id="ee89d-116">To edit a model deployment package</span></span>  
  
1.  <span data-ttu-id="ee89d-117">MDS의 Windows 탐색기에서 *drive*:\Program Files\Microsoft SQL Server\120\Master Data Services\Configuration으로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="ee89d-117">In Windows Explorer on the MDS server, move to *drive*:\Program Files\Microsoft SQL Server\120\Master Data Services\Configuration.</span></span>  
  
2.  <span data-ttu-id="ee89d-118">Modelpackageeditor.exe를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="ee89d-118">Execute ModelPackageEditor.exe.</span></span>  
  
3.  <span data-ttu-id="ee89d-119">모델 패키지 편집기 마법사에서 **찾아보기**를 클릭하여 패키지가 포함된 폴더로 이동한 다음 패키지를 선택하고 **열기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ee89d-119">In the Model Package Editor wizard, click **Browse**, move to the folder containing your packages, select a package, and then click **Open**.</span></span> <span data-ttu-id="ee89d-120">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ee89d-120">Click **Next**.</span></span>  
  
4.  <span data-ttu-id="ee89d-121">배포할 엔터티, 파생 계층, 구독 뷰 또는 비즈니스 규칙을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ee89d-121">Select those entities, derived hierarchies, subscriptions views, or business rules that you want to deploy.</span></span> <span data-ttu-id="ee89d-122">배포하지 않을 엔터티, 파생 계층, 구독 뷰 또는 비즈니스 규칙의 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="ee89d-122">Deselect those that you do not want to deploy.</span></span> <span data-ttu-id="ee89d-123">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ee89d-123">Click **Next**.</span></span>  
  
5.  <span data-ttu-id="ee89d-124">배포할 선택 항목의 목록을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="ee89d-124">Verify the list of selections to deploy.</span></span> <span data-ttu-id="ee89d-125">변경하려면 **뒤로** 를 클릭한 다음 4단계를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="ee89d-125">To change, click **Back** and repeat step 4.</span></span>  
  
6.  <span data-ttu-id="ee89d-126">**찾아보기**를 클릭하여 부분 패키지를 저장할 폴더로 이동한 다음 부분 패키지의 파일 이름(확장명은 .pkg)을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="ee89d-126">Click **Browse**, move to the folder that you want to save the partial package in, and then enter the file name of the partial package (with a .pkg extension).</span></span> <span data-ttu-id="ee89d-127">**저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ee89d-127">Click **Save**.</span></span>  
  
7.  <span data-ttu-id="ee89d-128">**Finish**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ee89d-128">Click **Finish**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="ee89d-129">다음 단계</span><span class="sxs-lookup"><span data-stu-id="ee89d-129">Next Steps</span></span>  
  
-   [<span data-ttu-id="ee89d-130">마법사를 사용하여 모델 배포 패키지 배포</span><span class="sxs-lookup"><span data-stu-id="ee89d-130">Deploy a Model Deployment Package by Using the Wizard</span></span>](../../2014/master-data-services/deploy-a-model-deployment-package-by-using-the-wizard.md)  
  
-   [<span data-ttu-id="ee89d-131">MDSModelDeploy를 사용하여 모델 배포 패키지 배포</span><span class="sxs-lookup"><span data-stu-id="ee89d-131">Deploy a Model Deployment Package by Using MDSModelDeploy</span></span>](../../2014/master-data-services/deploy-a-model-deployment-package-by-using-mdsmodeldeploy.md)  
  
  
