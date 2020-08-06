---
title: 패키지 재배포 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- redeploying packages [Integration Services]
- deploying packages [Integration Services], redeploying
ms.assetid: 86806efb-8cf4-4f9d-9824-1152cb4c495c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 4c5286d406d96f62fc74eb619f7e7a6064fde2a3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729591"
---
# <a name="redeployment-of-packages"></a><span data-ttu-id="e07bb-102">패키지 재배포</span><span class="sxs-lookup"><span data-stu-id="e07bb-102">Redeployment of Packages</span></span>
  <span data-ttu-id="e07bb-103">프로젝트를 배포한 후 패키지 기능을 업데이트하거나 확장한 다음 업데이트된 패키지를 포함하는 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 프로젝트를 다시 배포해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e07bb-103">After a project is deployed, you may need to update or extend package functionality and then redeploy the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the updated packages.</span></span> <span data-ttu-id="e07bb-104">패키지 재배포 과정의 일부로 배포 유틸리티에 포함된 구성 속성을 검토하십시오.</span><span class="sxs-lookup"><span data-stu-id="e07bb-104">As part of the process of redeploying packages, you should review the configuration properties that are included in the deployment utility.</span></span> <span data-ttu-id="e07bb-105">예를 들어 패키지를 재배포한 후 구성을 변경할 수 없도록 하기를 원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e07bb-105">For example, you may not want to allow configuration changes after the package is redeployed.</span></span>  
  
## <a name="process-for-redeployment"></a><span data-ttu-id="e07bb-106">재배치 프로세스</span><span class="sxs-lookup"><span data-stu-id="e07bb-106">Process for Redeployment</span></span>  
 <span data-ttu-id="e07bb-107">패키지 업데이트를 완료한 다음에는 프로젝트를 다시 빌드하고 대상 컴퓨터에 배포 폴더를 복사한 다음 패키지 설치 마법사를 다시 실행하십시오.</span><span class="sxs-lookup"><span data-stu-id="e07bb-107">After you finish updating the packages, you rebuild the project, copy the deployment folder to the target computer, and then rerun the Package Installation Wizard.</span></span>  
  
 <span data-ttu-id="e07bb-108">프로젝트 내의 소수 패키지만 업데이트한 경우 전체 프로젝트를 재배포하고 싶지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e07bb-108">If you update only a few packages in the project, you may not want to redeploy the entire project.</span></span> <span data-ttu-id="e07bb-109">소수의 패키지만 배포하려면 새 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 프로젝트를 만들고 업데이트된 패키지를 추가한 다음 프로젝트를 빌드하고 배포하십시오.</span><span class="sxs-lookup"><span data-stu-id="e07bb-109">To deploy only a few packages, you can create a new [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project, add the updated packages to the new project, and then build and deploy the project.</span></span> <span data-ttu-id="e07bb-110">다른 프로젝트에 패키지를 추가하는 경우 자동으로 패키지와 함께 패키지 구성이 복사됩니다.</span><span class="sxs-lookup"><span data-stu-id="e07bb-110">Package configurations are automatically copied with the package when you add the package to a different project.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="e07bb-111">관련 작업</span><span class="sxs-lookup"><span data-stu-id="e07bb-111">Related Tasks</span></span>  
 [<span data-ttu-id="e07bb-112">배포 유틸리티를 사용한 패키지 배포</span><span class="sxs-lookup"><span data-stu-id="e07bb-112">Deploy Packages by Using the Deployment Utility</span></span>](../../2014/integration-services/deploy-packages-by-using-the-deployment-utility.md)  
  
  
