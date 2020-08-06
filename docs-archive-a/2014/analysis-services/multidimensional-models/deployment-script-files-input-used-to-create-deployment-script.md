---
title: 배포 스크립트를 만드는 데 사용 되는 입력 파일 이해 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- input files [Analysis Services]
- Analysis Services Deployment Wizard, scripts
- deploying [Analysis Services], input files
- Analysis Services Deployment Wizard, input files
- scripts [Analysis Services], deployment
- Analysis Services deployments, input files
- modifying input files
ms.assetid: 20e080cd-6a0e-4591-b022-ea4cd3638e36
author: minewiskan
ms.author: owend
ms.openlocfilehash: 34695993d4f153c6c0b97fef744d92c682517c99
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651375"
---
# <a name="understanding-the-input-files-used-to-create-the-deployment-script"></a><span data-ttu-id="b7e66-102">배포 스크립트를 만드는 데 사용하는 입력 파일 이해</span><span class="sxs-lookup"><span data-stu-id="b7e66-102">Understanding the Input Files Used to Create the Deployment Script</span></span>
  <span data-ttu-id="b7e66-103">프로젝트를 빌드하면 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 에서 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 프로젝트에 대 한 XML 파일을 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7e66-103">When you build a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project, [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] generates XML files for the project.</span></span> [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]<span data-ttu-id="b7e66-104">는 이러한 XML 파일을 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 프로젝트의 Output 폴더에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="b7e66-104">puts these XML files in the Output folder of the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project.</span></span> <span data-ttu-id="b7e66-105">기본 결과는 \Bin 폴더에 출력됩니다.</span><span class="sxs-lookup"><span data-stu-id="b7e66-105">By default output is out in the \Bin folder.</span></span> <span data-ttu-id="b7e66-106">다음 표에서는 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 에서 만드는 XML 파일을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="b7e66-106">The following table lists the XML files that [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] creates.</span></span>  
  
|<span data-ttu-id="b7e66-107">XMLA 파일</span><span class="sxs-lookup"><span data-stu-id="b7e66-107">XMLA file</span></span>|<span data-ttu-id="b7e66-108">Description</span><span class="sxs-lookup"><span data-stu-id="b7e66-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b7e66-109">\<*project name*>. asdatabase</span><span class="sxs-lookup"><span data-stu-id="b7e66-109">\<*project name*>.asdatabase</span></span>|<span data-ttu-id="b7e66-110">프로젝트의 모든 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 개체에 대한 선언적 정의가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="b7e66-110">Contains the declarative definitions for all the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] objects in the project.</span></span>|  
|<span data-ttu-id="b7e66-111">\<*project name*>deploymenttargets</span><span class="sxs-lookup"><span data-stu-id="b7e66-111">\<*project name*>.deploymenttargets</span></span>|<span data-ttu-id="b7e66-112">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 개체가 생성되는 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스 및 데이터베이스의 이름이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="b7e66-112">Contains the name of the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance and database in which the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] objects will be created.</span></span>|  
|<span data-ttu-id="b7e66-113">\<*project name*>configsettings</span><span class="sxs-lookup"><span data-stu-id="b7e66-113">\<*project name*>.configsettings</span></span>|<span data-ttu-id="b7e66-114">데이터 원본 연결 정보 및 개체 스토리지 위치와 같은 환경 관련 설정이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="b7e66-114">Contains environment specific settings, such as data source connection information and object storage locations.</span></span> <span data-ttu-id="b7e66-115">이 파일의 설정은 asdatabase 파일의 설정을 재정의 합니다. \<*project name*></span><span class="sxs-lookup"><span data-stu-id="b7e66-115">Settings in this file override settings in the \<*project name*>.asdatabase file.</span></span>|  
|<span data-ttu-id="b7e66-116">\<*project name*>deploymentoptions</span><span class="sxs-lookup"><span data-stu-id="b7e66-116">\<*project name*>.deploymentoptions</span></span>|<span data-ttu-id="b7e66-117">배포가 트랜잭션인지 여부와 배포된 개체가 배포 후 처리되어야 하는지 여부와 같은 배포 옵션이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="b7e66-117">Contains deployment options, such as whether deployment is transactional and whether deployed objects should be processed after deployment.</span></span>|  
  
> [!NOTE]  
>  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] <span data-ttu-id="b7e66-118">는 해당 프로젝트 파일에 암호를 저장하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b7e66-118">never stores passwords in its project files.</span></span>  
  
## <a name="modifying-the-input-files"></a><span data-ttu-id="b7e66-119">입력 파일 수정</span><span class="sxs-lookup"><span data-stu-id="b7e66-119">Modifying the Input Files</span></span>  
 <span data-ttu-id="b7e66-120">입력 파일의 값 이나 입력 파일에서 검색 한 값을 수정 하면 전체 \<*project name*> . asdatabase 파일 (또는 기존 데이터베이스에서 스크립트를 생성 하는 경우 전체 XMLA 스크립트 파일)을 편집 하지 않고 배포 대상, 구성 설정 및 배포 옵션을 변경할 수 있습니다 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="b7e66-120">Modifying the values in the input files, or the values retrieved from the input files, makes it possible to change the deployment destination, the configuration settings, and deployment options without editing the whole \<*project name*>.asdatabase file (or a whole XMLA script file if you generate a script from an existing [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database).</span></span> <span data-ttu-id="b7e66-121">개별 파일을 수정할 수 있으면 다른 용도의 다른 배포 스크립트를 쉽게 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b7e66-121">Being able to modify individual files lets you easily create different deployment scripts for different purposes.</span></span>  
  
 <span data-ttu-id="b7e66-122">다음 항목에서는 여러 입력 파일에서 값을 수정하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="b7e66-122">The following topics explain how to modify values in the various input files:</span></span>  
  
-   [<span data-ttu-id="b7e66-123">설치 대상 지정</span><span class="sxs-lookup"><span data-stu-id="b7e66-123">Specifying the Installation Target</span></span>](deployment-script-files-specifying-the-installation-target.md)  
  
-   [<span data-ttu-id="b7e66-124">파티션 및 역할 배포 옵션 지정</span><span class="sxs-lookup"><span data-stu-id="b7e66-124">Specifying Partition and Role Deployment Options</span></span>](deployment-script-files-partition-and-role-deployment-options.md)  
  
-   [<span data-ttu-id="b7e66-125">솔루션 배포를 위한 구성 설정 지정</span><span class="sxs-lookup"><span data-stu-id="b7e66-125">Specifying Configuration Settings for Solution Deployment</span></span>](deployment-script-files-solution-deployment-config-settings.md)  
  
-   [<span data-ttu-id="b7e66-126">처리 옵션 지정</span><span class="sxs-lookup"><span data-stu-id="b7e66-126">Specifying Processing Options</span></span>](deployment-script-files-specifying-processing-options.md)  
  
## <a name="see-also"></a><span data-ttu-id="b7e66-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b7e66-127">See Also</span></span>  
 <span data-ttu-id="b7e66-128">[Analysis Services 배포 마법사 실행](running-the-analysis-services-deployment-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="b7e66-128">[Running the Analysis Services Deployment Wizard](running-the-analysis-services-deployment-wizard.md) </span></span>  
 [<span data-ttu-id="b7e66-129">Analysis Services 배포 스크립트 이해</span><span class="sxs-lookup"><span data-stu-id="b7e66-129">Understanding the Analysis Services Deployment Script</span></span>](understanding-the-analysis-services-deployment-script.md)  
  
  
