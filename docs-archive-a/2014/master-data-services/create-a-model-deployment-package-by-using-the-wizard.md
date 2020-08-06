---
title: 마법사를 사용하여 모델 배포 패키지 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- deployment packages [Master Data Services], creating
- models [Master Data Services], creating a deployment package
- creating packages [Master Data Services]
ms.assetid: b24ec4c2-1378-4c72-ac69-4ec2647030f0
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: abb30f9d8e08d8eec8e04960b61575da3a1dbcc0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660656"
---
# <a name="create-a-model-deployment-package-by-using-the-wizard"></a><span data-ttu-id="97522-102">마법사를 사용하여 모델 배포 패키지 만들기</span><span class="sxs-lookup"><span data-stu-id="97522-102">Create a Model Deployment Package by Using the Wizard</span></span>
  <span data-ttu-id="97522-103">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 모델 배포 마법사를 사용하여 모델 개체로만 패키지를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="97522-103">Use the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] model deployment wizard to create a package of the model objects only.</span></span> <span data-ttu-id="97522-104">패키지에 데이터를 포함해야 하는 경우 [MDSModelDeploy를 사용하여 모델 배포 패키지 만들기](../../2014/master-data-services/create-a-model-deployment-package-by-using-mdsmodeldeploy.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="97522-104">If you need to include data in the package, see [Create a Model Deployment Package by Using MDSModelDeploy](../../2014/master-data-services/create-a-model-deployment-package-by-using-mdsmodeldeploy.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="97522-105">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="97522-105">Prerequisites</span></span>  
 <span data-ttu-id="97522-106">이 절차를 수행하려면</span><span class="sxs-lookup"><span data-stu-id="97522-106">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="97522-107">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 웹 애플리케이션에서는 사용자에게 **시스템 관리** 기능 영역에 대한 액세스 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="97522-107">In the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] web application, you must have permission to access the **System Administration** functional area.</span></span>  
  
-   <span data-ttu-id="97522-108">모델 관리자여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="97522-108">You must be a model administrator.</span></span> <span data-ttu-id="97522-109">자세한 내용은 [관리자 &#40;MDS(Master Data Services)&#41;](administrators-master-data-services.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="97522-109">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="97522-110">패키지를 만들 모델이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="97522-110">A model must exist for you to create a package of.</span></span> <span data-ttu-id="97522-111">자세한 내용은 [모델 만들기&#40;Master Data Services&#41;](../../2014/master-data-services/create-a-model-master-data-services.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="97522-111">For more information, see [Create a Model &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-model-master-data-services.md).</span></span>  
  
### <a name="to-create-a-model-deployment-package"></a><span data-ttu-id="97522-112">모델 배포 패키지를 만들려면</span><span class="sxs-lookup"><span data-stu-id="97522-112">To create a model deployment package</span></span>  
  
1.  <span data-ttu-id="97522-113">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]에서 **시스템 관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="97522-113">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="97522-114">**모델 뷰** 페이지의 메뉴 모음에서 **시스템** 을 가리키고 **배포**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="97522-114">On the **Model View** page, from the menu bar, point to **System** and click **Deployment**.</span></span>  
  
3.  <span data-ttu-id="97522-115">**모델 배포 마법사**에서 **만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="97522-115">On the **Model Deployment Wizard**, click **Create**.</span></span>  
  
4.  <span data-ttu-id="97522-116">**패키지 만들기** 페이지의 **모델** 목록에서 모델을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="97522-116">On the **Create Package** page, select a model from the **Model** list.</span></span>  
  
5.  <span data-ttu-id="97522-117">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="97522-117">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="97522-118">**다운로드**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="97522-118">Click **Download**.</span></span>  
  
7.  <span data-ttu-id="97522-119">파일을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="97522-119">Save the file.</span></span>  
  
8.  <span data-ttu-id="97522-120">**닫기**를 클릭하여 마법사를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="97522-120">Click **Close** to close the wizard.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="97522-121">다음 단계</span><span class="sxs-lookup"><span data-stu-id="97522-121">Next Steps</span></span>  
  
-   [<span data-ttu-id="97522-122">마법사를 사용하여 모델 배포 패키지 배포</span><span class="sxs-lookup"><span data-stu-id="97522-122">Deploy a Model Deployment Package by Using the Wizard</span></span>](../../2014/master-data-services/deploy-a-model-deployment-package-by-using-the-wizard.md)  
  
## <a name="see-also"></a><span data-ttu-id="97522-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="97522-123">See Also</span></span>  
 [<span data-ttu-id="97522-124">모델 배포&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="97522-124">Deploying Models &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/deploying-models-master-data-services.md)  
  
  
