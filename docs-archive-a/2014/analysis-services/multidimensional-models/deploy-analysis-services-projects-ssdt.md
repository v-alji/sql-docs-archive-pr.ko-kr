---
title: Analysis Services 프로젝트 배포 (SSDT) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- deploy [Analysis Services]
- projects [Analysis Services], deploying
- Business Intelligence Development Studio, deploying projects [Analysis Services]
ms.assetid: 29490a5b-1573-4a35-9277-10c6a6e4ef0e
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5317eea19d088a8d3f9d8bfb86da4e0429d62c3e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651378"
---
# <a name="deploy-analysis-services-projects-ssdt"></a><span data-ttu-id="7cba3-102">Analysis Services 프로젝트 배포(SSDT)</span><span class="sxs-lookup"><span data-stu-id="7cba3-102">Deploy Analysis Services Projects (SSDT)</span></span>
  <span data-ttu-id="7cba3-103">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 에서 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]프로젝트를 개발하는 동안 프로젝트에서 정의된 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 데이터베이스를 만들기 위해 개발 서버에 자주 프로젝트를 배포합니다.</span><span class="sxs-lookup"><span data-stu-id="7cba3-103">During development of an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], you frequently deploy the project to a development server in order to create the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database defined by the project.</span></span> <span data-ttu-id="7cba3-104">큐브에서 셀을 찾아보거나 차원 멤버를 찾아보거나 KPI(핵심 성과 지표) 수식을 확인하는 등 프로젝트를 테스트하려면 이 작업을 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7cba3-104">This is required to test the project; for example, to browse cells in the cube, browse dimension members, or verify key performance indicators (KPIs) formulas.</span></span>  
  
## <a name="deploying-a-project"></a><span data-ttu-id="7cba3-105">프로젝트 배포</span><span class="sxs-lookup"><span data-stu-id="7cba3-105">Deploying a Project</span></span>  
 <span data-ttu-id="7cba3-106">독립적으로 프로젝트를 배포하거나 솔루션 내의 모든 프로젝트를 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7cba3-106">You can deploy a project independently, or you can deploy all of the projects within the solution.</span></span> <span data-ttu-id="7cba3-107">프로젝트를 배포하면 여러 작업이 순서대로 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="7cba3-107">When you deploy a project, several things happen in sequence.</span></span> <span data-ttu-id="7cba3-108">먼저 프로젝트가 작성됩니다.</span><span class="sxs-lookup"><span data-stu-id="7cba3-108">First, the project is built.</span></span> <span data-ttu-id="7cba3-109">이 단계에서는 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 데이터베이스와 해당 요소 개체를 정의하는 출력 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="7cba3-109">This step creates the output files that define the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database and its constituent objects.</span></span> <span data-ttu-id="7cba3-110">다음에는 대상 서버의 유효성이 확인됩니다.</span><span class="sxs-lookup"><span data-stu-id="7cba3-110">Next, the destination server is validated.</span></span> <span data-ttu-id="7cba3-111">마지막으로 대상 데이터베이스와 해당 개체가 대상 서버에 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="7cba3-111">Finally, the destination database and its objects are created on the destination server.</span></span> <span data-ttu-id="7cba3-112">배포 중에 배포 엔진은 이전 배포 시 프로젝트에서 해당 개체를 만들지 않은 경우 기존 데이터베이스를 프로젝트의 내용으로 모두 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="7cba3-112">During deployment, the deployment engine totally replaces any pre-existing database with the contents of the project unless those objects were created by the project during a previous deployment.</span></span>  
  
 <span data-ttu-id="7cba3-113">초기 배포 후에는 \obj 폴더에 IncrementalSnapshot.xml 파일이 생성 됩니다 \<Project Name> .</span><span class="sxs-lookup"><span data-stu-id="7cba3-113">After an initial deployment, an IncrementalSnapshot.xml file is generated in the \<Project Name>\obj folder.</span></span> <span data-ttu-id="7cba3-114">이 파일은 대상 서버의 데이터베이스나 해당 개체가 프로젝트 외부에서 변경되었는지 여부를 확인하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="7cba3-114">This file is used to determine if the database or its objects on the destination server have changed outside of the project.</span></span> <span data-ttu-id="7cba3-115">이 경우 대상 데이터베이스의 모든 개체를 덮어쓸 것인지 묻는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="7cba3-115">If so, you will be prompted to overwrite all objects in the destination database.</span></span> <span data-ttu-id="7cba3-116">모든 변경이 프로젝트 내에서 수행되었으며 프로젝트에 증분 배포가 구성된 경우에는 변경 내용만 대상 서버로 배포됩니다.</span><span class="sxs-lookup"><span data-stu-id="7cba3-116">If all changes were made within the project and the project is configured for incremental deployment, only the changes will be deployed to the destination server.</span></span>  
  
 <span data-ttu-id="7cba3-117">프로젝트 구성 및 관련 설정에 따라 프로젝트 배포에 사용되는 배포 속성이 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="7cba3-117">The project configuration and its associated settings determine the deployment properties that will be used to deploy the project.</span></span> <span data-ttu-id="7cba3-118">공유 프로젝트의 경우 각 개발자가 선택한 프로젝트 구성 옵션이 포함된 고유한 구성을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7cba3-118">For a shared project, each developer can use their own configuration with their own project configuration options.</span></span> <span data-ttu-id="7cba3-119">예를 들어 각 개발자는 서로 다른 테스트 서버를 지정하여 다른 개발자와 격리된 상태로 작업할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7cba3-119">For example, each developer can specify a different test server to work in isolation from other developers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7cba3-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7cba3-120">See Also</span></span>  
 [<span data-ttu-id="7cba3-121">Analysis Services 프로젝트 만들기&#40;SSDT&#41;</span><span class="sxs-lookup"><span data-stu-id="7cba3-121">Create an Analysis Services Project &#40;SSDT&#41;</span></span>](create-an-analysis-services-project-ssdt.md)  
  
  
