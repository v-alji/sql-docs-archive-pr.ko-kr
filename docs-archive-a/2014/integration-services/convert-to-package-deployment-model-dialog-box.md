---
title: 패키지 배포 모델로 변환 대화 상자 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.bids.converttolegacydeployment.f1
ms.assetid: 9e60a34a-10f7-48d1-966f-b3ff236ab4b7
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b52932ad26f8cebd2e67b0025f4b881241119f6e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651836"
---
# <a name="convert-to-package-deployment-model-dialog-box"></a><span data-ttu-id="f9561-102">패키지 배포 모델로 변환 대화 상자</span><span class="sxs-lookup"><span data-stu-id="f9561-102">Convert to Package Deployment Model Dialog Box</span></span>
  <span data-ttu-id="f9561-103">**패키지 배포 모델로 변환** 명령을 사용하면 프로젝트 및 프로젝트의 각 패키지에서 해당 모델과의 호환성을 검사한 후 패키지를 패키지 배포 모델로 변환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f9561-103">The **Convert to Package Deployment Model** command allows you to convert a package to the package deployment model after checking the project and each package in the project for compatibility with that model.</span></span> <span data-ttu-id="f9561-104">패키지에 매개 변수와 같이 프로젝트 배포 모델에 고유한 기능이 사용된 경우 패키지를 변환할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f9561-104">If a package uses features unique to the project deployment model, such as parameters, then the package cannot be converted.</span></span>  
  
## <a name="task-list"></a><span data-ttu-id="f9561-105">작업 목록</span><span class="sxs-lookup"><span data-stu-id="f9561-105">Task List</span></span>  
 <span data-ttu-id="f9561-106">패키지를 패키지 배포 모델로 변환하려면 두 단계가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="f9561-106">Converting a package to the package deployment model requires two steps.</span></span>  
  
1.  <span data-ttu-id="f9561-107">**프로젝트** 메뉴에서 **패키지 배포 모델로 변환** 명령을 선택하면 이 모델에 대한 프로젝트 및 각 패키지의 호환성이 검사됩니다.</span><span class="sxs-lookup"><span data-stu-id="f9561-107">When you select the **Convert to Package Deployment Model** command from the **Project** menu, the project and each package are checked for compatibility with this model.</span></span> <span data-ttu-id="f9561-108">결과는 **결과** 테이블에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f9561-108">The results are displayed in the **Results** table.</span></span>  
  
     <span data-ttu-id="f9561-109">프로젝트 또는 패키지가 호환성 테스트를 실패한 경우 **결과** 열에서 **실패** 를 클릭하여 자세한 내용을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="f9561-109">If the project or a package fails the compatibility test, click **Failed** in the **Result** column for more information.</span></span> <span data-ttu-id="f9561-110">**보고서 저장** 을 클릭하여 이 정보의 복사본을 텍스트 파일로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="f9561-110">Click **Save Report** to save a copy of this information to a text file.</span></span>  
  
2.  <span data-ttu-id="f9561-111">프로젝트 및 모든 패키지가 호환성 테스트를 성공하면 **확인** 을 클릭하여 패키지를 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="f9561-111">If the project and all packages pass the compatibility test, then click **OK** to convert the package.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f9561-112">프로젝트를 프로젝트 배포 모델로 변환하려면 **Integration Services 프로젝트 변환 마법사**를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f9561-112">To convert a project to the project deployment model, use the **Integration Services Project Conversion Wizard**.</span></span> <span data-ttu-id="f9561-113">자세한 내용은 [Integration Services Project Conversion Wizard](../../2014/integration-services/integration-services-project-conversion-wizard.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f9561-113">For more information, see [Integration Services Project Conversion Wizard](../../2014/integration-services/integration-services-project-conversion-wizard.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9561-114">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f9561-114">See Also</span></span>  
 <span data-ttu-id="f9561-115">[프로젝트 및 패키지 배포](packages/deploy-integration-services-ssis-projects-and-packages.md) </span><span class="sxs-lookup"><span data-stu-id="f9561-115">[Deployment of Projects and Packages](packages/deploy-integration-services-ssis-projects-and-packages.md) </span></span>  
 <span data-ttu-id="f9561-116">[SSIS&#41;패키지 배포 &#40;](packages/legacy-package-deployment-ssis.md) </span><span class="sxs-lookup"><span data-stu-id="f9561-116">[Package Deployment &#40;SSIS&#41;](packages/legacy-package-deployment-ssis.md) </span></span>  
 [<span data-ttu-id="f9561-117">Integration Services 프로젝트 변환 마법사</span><span class="sxs-lookup"><span data-stu-id="f9561-117">Integration Services Project Conversion Wizard</span></span>](../../2014/integration-services/integration-services-project-conversion-wizard.md)  
  
  
