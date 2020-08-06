---
title: 패키지 배포 (SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Integration Services packages, deploying
- deploying packages [Integration Services]
- SQL Server Integration Services packages, deploying
- deploying packages [Integration Services], about deploying packages
- packages [Integration Services], deploying
- SSIS packages, deploying
ms.assetid: 0f5fc7be-e37e-4ecd-ba99-697c8ae3436f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 32627eddf5e7a696decd549e9b87ebb5c3b9d031
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652194"
---
# <a name="package-deployment-ssis"></a><span data-ttu-id="18aec-102">패키지 배포(SSIS)</span><span class="sxs-lookup"><span data-stu-id="18aec-102">Package Deployment (SSIS)</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="18aec-103">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]에는 패키지를 배포 컴퓨터에서 프로덕션 서버나 다른 컴퓨터로 손쉽게 배포할 수 있는 도구와 마법사가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="18aec-103">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] includes tools and wizards that make it simple to deploy packages from the development computer to the production server or to other computers.</span></span>  
  
 <span data-ttu-id="18aec-104">패키지 배포 과정은 다음 네 단계로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="18aec-104">There are four steps in the package deployment process:</span></span>  
  
1.  <span data-ttu-id="18aec-105">첫 번째 단계는 선택 사항입니다. 이 단계에서는 런타임에 패키지 요소의 속성을 업데이트하는 패키지 구성을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="18aec-105">The first optional step is optional and involves creating package configurations that update properties of package elements at run time.</span></span> <span data-ttu-id="18aec-106">구성은 패키지를 배포할 때 자동으로 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="18aec-106">The configurations are automatically included when you deploy the packages.</span></span>  
  
2.  <span data-ttu-id="18aec-107">두 번째 단계는 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 프로젝트를 빌드하여 패키지 배포 유틸리티를 만드는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="18aec-107">The second step is to build the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project to create a package deployment utility.</span></span> <span data-ttu-id="18aec-108">프로젝트의 배포 유틸리티에는 배포할 패키지가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="18aec-108">The deployment utility for the project contains the packages that you want to deploy</span></span>  
  
3.  <span data-ttu-id="18aec-109">세 번째 단계는 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 프로젝트를 빌드할 때 생성된 배포 폴더를 대상 컴퓨터로 복사하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="18aec-109">The third step is to copy the deployment folder that was created when you built the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project to the target computer.</span></span>  
  
4.  <span data-ttu-id="18aec-110">네 번째 단계는 대상 컴퓨터에서 패키지 설치 마법사를 실행하여 파일 시스템이나 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스에 패키지를 설치하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="18aec-110">The fourth step is to run, on the target computer, the Package Installation Wizard to install the packages to the file system or to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="18aec-111">관련 작업</span><span class="sxs-lookup"><span data-stu-id="18aec-111">Related Tasks</span></span>  
 <span data-ttu-id="18aec-112">배포 유틸리티를 만드는 방법에 대한 자세한 내용은 [배포 유틸리티 만들기](../create-a-deployment-utility.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="18aec-112">For information about how to create a deployment utility, see [Create a Deployment Utility](../create-a-deployment-utility.md).</span></span>  
  
 <span data-ttu-id="18aec-113">배포 유틸리티를 사용하여 패키지를 배포하는 방법에 대한 자세한 내용은 [배포 유틸리티를 사용한 패키지 배포](../deploy-packages-by-using-the-deployment-utility.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="18aec-113">For information about how to deploy packages using the deployment utility, see [Deploy Packages by Using the Deployment Utility](../deploy-packages-by-using-the-deployment-utility.md).</span></span>  
  
 <span data-ttu-id="18aec-114">패키지 구성을 만드는 방법에 대한 자세한 내용은 [패키지 구성 만들기](../create-package-configurations.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="18aec-114">For information about how to create package configurations, see [Create Package Configurations](../create-package-configurations.md).</span></span>  
  
  
