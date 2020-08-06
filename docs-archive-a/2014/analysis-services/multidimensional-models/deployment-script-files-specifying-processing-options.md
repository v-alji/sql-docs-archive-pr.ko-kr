---
title: 처리 옵션 지정 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Analysis Services deployments, processing options
- input files [Analysis Services]
- deploying [Analysis Services], processing options
- modifying processing options
- Analysis Services Deployment Wizard, processing options
ms.assetid: e9e50817-908e-4210-bc3d-8e2957568241
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9690aaa7e1d3b3870eb6ab01630b98027263655f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728883"
---
# <a name="specifying-processing-options"></a><span data-ttu-id="75d20-102">처리 옵션 지정</span><span class="sxs-lookup"><span data-stu-id="75d20-102">Specifying Processing Options</span></span>
  <span data-ttu-id="75d20-103">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]배포 마법사는 deploymentoptions 파일에서 처리 옵션을 읽습니다 \<*project name*> .</span><span class="sxs-lookup"><span data-stu-id="75d20-103">The [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Deployment Wizard reads the processing options from the \<*project name*>.deploymentoptions file.</span></span> [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]<span data-ttu-id="75d20-104">프로젝트를 빌드할 때이 파일을 만듭니다 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="75d20-104">creates this file when you build the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project.</span></span> [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]<span data-ttu-id="75d20-105">속성 페이지 대화 상자의 **배포** 페이지에 지정 된 처리 옵션을 사용 하 여 *\<project name>* **Properties Pages** \<*project name*> deploymentoptions 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="75d20-105">uses the processing options specified on the **Deployment** page of *\<project name>* **Properties Pages** dialog box to create the \<*project name*>.deploymentoptions file.</span></span>  
  
## <a name="reviewing-the-processing-options-for-deployment"></a><span data-ttu-id="75d20-106">배포를 위한 처리 옵션 검토</span><span class="sxs-lookup"><span data-stu-id="75d20-106">Reviewing the Processing Options for Deployment</span></span>  
 <span data-ttu-id="75d20-107">Deploymentoptions 파일 내에 저장 된 구성 설정은 다음과 같습니다 \<*project name*> .</span><span class="sxs-lookup"><span data-stu-id="75d20-107">The configuration settings stored within the \<*project name*>.deploymentoptions file are as follows:</span></span>  
  
-   <span data-ttu-id="75d20-108">**처리 방법** 이 설정은 배포 후 배포된 개체가 처리되는지 여부와 수행할 처리 유형을 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="75d20-108">**Processing Method** This setting controls whether the deployed objects are processed after deployment and the type of processing that will be performed.</span></span> <span data-ttu-id="75d20-109">3가지 처리 옵션은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="75d20-109">There are three processing options:</span></span>  
  
    -   <span data-ttu-id="75d20-110">기본 처리(기본값)</span><span class="sxs-lookup"><span data-stu-id="75d20-110">Default processing (default)</span></span>  
  
    -   <span data-ttu-id="75d20-111">전체 처리</span><span class="sxs-lookup"><span data-stu-id="75d20-111">Full processing</span></span>  
  
    -   <span data-ttu-id="75d20-112">없음</span><span class="sxs-lookup"><span data-stu-id="75d20-112">None</span></span>  
  
-   <span data-ttu-id="75d20-113">**쓰기 저장(writeback) 테이블 옵션** 쓰기 저장(writeback)이 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 프로젝트에 설정된 경우 이 설정은 쓰기 저장(writeback)의 처리 방법을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="75d20-113">**Writeback Table Options** If writeback is enabled in the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project, this setting defines how writeback is handled.</span></span> <span data-ttu-id="75d20-114">3가지 쓰기 저장(writeback) 테이블 옵션은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="75d20-114">There are three writeback table options:</span></span>  
  
    -   <span data-ttu-id="75d20-115">기본적으로 쓰기 저장(writeback) 테이블이 있는 경우 이 테이블이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="75d20-115">By default, if a writeback table exists, it will be used.</span></span> <span data-ttu-id="75d20-116">쓰기 저장(Writeback) 테이블이 없는 경우 새 쓰기 저장 테이블이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="75d20-116">If a writeback table does not exist, a new writeback table will be created.</span></span>  
  
    -   <span data-ttu-id="75d20-117">쓰기 저장(writeback) 테이블이 이미 있으면 배포가 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="75d20-117">If a writeback table already exists, the deployment fails.</span></span> <span data-ttu-id="75d20-118">쓰기 저장(Writeback) 테이블이 없는 경우 새 쓰기 저장 테이블이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="75d20-118">If a writeback table does not exist, a new writeback table will be created.</span></span>  
  
    -   <span data-ttu-id="75d20-119">쓰기 저장(writeback) 테이블이 이미 존재하는지 여부에 관계없이 새로운 쓰기 저장(writeback) 테이블이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="75d20-119">Regardless of whether a writeback table already exists, a new writeback table will be created.</span></span> <span data-ttu-id="75d20-120">이 경우 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 배포 마법사는 기존 테이블을 삭제하고 이를 새로운 쓰기 저장(writeback) 테이블로 교체합니다.</span><span class="sxs-lookup"><span data-stu-id="75d20-120">In this case, the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Deployment Wizard will delete any existing table and replace it with a new writeback table.</span></span>  
  
-   <span data-ttu-id="75d20-121">**트랜잭션 배포** 이 설정은 메타데이터 배포가 변경되고 처리 명령이 단일 트랜잭션 또는 개별 트랜잭션에 발생하는지 여부를 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="75d20-121">**Transactional Deployment** This setting controls whether the deployment of metadata changes and process commands occurs in a single transaction or in separate transactions.</span></span>  
  
    -   <span data-ttu-id="75d20-122">이 옵션이 `True`(기본값)인 경우 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]는 모든 메타데이터 변경 내용과 단일 트랜잭션 내의 모든 처리 명령을 배포합니다.</span><span class="sxs-lookup"><span data-stu-id="75d20-122">If this option is `True` (default), [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] deploys all metadata changes and all process commands within a single transaction.</span></span>  
  
    -   <span data-ttu-id="75d20-123">이 옵션이 `False`인 경우 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]는 단일 트랜잭션의 메타데이터 변경 내용을 배포하고 해당 트랜잭션의 각 처리 명령을 배포합니다.</span><span class="sxs-lookup"><span data-stu-id="75d20-123">If this option is `False`, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] deploys the metadata changes in a single transaction, and deploys each processing command in its own transaction.</span></span>  
  
## <a name="modifying-the-processing-options-for-deployment"></a><span data-ttu-id="75d20-124">배포를 위한 처리 옵션 수정</span><span class="sxs-lookup"><span data-stu-id="75d20-124">Modifying the Processing Options for Deployment</span></span>  
 <span data-ttu-id="75d20-125">그러나 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] deploymentoptions 파일에 저장 된 것과 다른 처리 옵션을 사용 하 여 프로젝트를 배포 해야 할 수도 있습니다. \<*project name*></span><span class="sxs-lookup"><span data-stu-id="75d20-125">However, you may need to deploy the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project using different processing options than those stored in the \<*project name*>.deploymentoptions file.</span></span> <span data-ttu-id="75d20-126">예를 들어 모든 개체를 완전히 처리하거나 기본 처리 옵션을 사용하여 처리할 수 있으며, 또는 처리가 발생하지 않도록 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="75d20-126">For example, you may want to have all objects fully processed, or processed using the default processing option, or have no processing occur.</span></span> <span data-ttu-id="75d20-127">큐브 또는 차원이 쓰기 설정된 경우 새 쓰기 저장(writeback) 테이블이나 기존 테이블을 사용하도록 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="75d20-127">If the cubes or dimensions are write-enabled, you can specify whether a new or existing writeback table be used.</span></span>  
  
 <span data-ttu-id="75d20-128">배포 중에 사용된 처리 옵션을 수정하려는 경우 프로젝트를 편집하고 다시 작성하거나 다음 절차에 설명된 대로 다음 방법 중 하나를 사용하여 입력 파일에서 처리 옵션을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="75d20-128">To modify the processing options used during deployment, you can either edit and rebuild the project, or change the processing options in the input file by using one of the methods as described in the following procedure.</span></span>  
  
#### <a name="to-change-processing-options-after-the-input-files-have-been-generated"></a><span data-ttu-id="75d20-129">입력 파일을 생성한 다음 처리 옵션을 변경하려면</span><span class="sxs-lookup"><span data-stu-id="75d20-129">To change processing options after the input files have been generated</span></span>  
  
-   <span data-ttu-id="75d20-130">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 배포 마법사를 대화형으로 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="75d20-130">Run the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Deployment Wizard interactively.</span></span> <span data-ttu-id="75d20-131">**처리 옵션** 페이지에서 배포할 프로젝트의 처리 옵션을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="75d20-131">On the **Processing Options** page, specify the processing options for the project being deployed.</span></span>  
  
     <span data-ttu-id="75d20-132">또는</span><span class="sxs-lookup"><span data-stu-id="75d20-132">-or-</span></span>  
  
-   <span data-ttu-id="75d20-133">명령 프롬프트에서 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 배포 마법사를 실행하여 응답 파일 모드에서 마법사를 실행하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="75d20-133">Run the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Deployment Wizard at the command prompt and set the wizard to run in answer file mode.</span></span> <span data-ttu-id="75d20-134">응답 파일 모드에 대한 자세한 내용은 [Running the Analysis Services Deployment Wizard](running-the-analysis-services-deployment-wizard.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="75d20-134">For more information about answer file mode, see [Running the Analysis Services Deployment Wizard](running-the-analysis-services-deployment-wizard.md).</span></span>  
  
     <span data-ttu-id="75d20-135">또는</span><span class="sxs-lookup"><span data-stu-id="75d20-135">-or-</span></span>  
  
-   <span data-ttu-id="75d20-136">\<*project name*>텍스트 편집기를 사용 하 여 deploymentoptions 파일을 수정 합니다.</span><span class="sxs-lookup"><span data-stu-id="75d20-136">Modify the \<*project name*>.deploymentoptions file by using any text editor.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75d20-137">참고 항목</span><span class="sxs-lookup"><span data-stu-id="75d20-137">See Also</span></span>  
 <span data-ttu-id="75d20-138">[설치 대상 지정](deployment-script-files-specifying-the-installation-target.md) </span><span class="sxs-lookup"><span data-stu-id="75d20-138">[Specifying the Installation Target](deployment-script-files-specifying-the-installation-target.md) </span></span>  
 <span data-ttu-id="75d20-139">[파티션 및 역할 배포 옵션 지정](deployment-script-files-partition-and-role-deployment-options.md) </span><span class="sxs-lookup"><span data-stu-id="75d20-139">[Specifying Partition and Role Deployment Options](deployment-script-files-partition-and-role-deployment-options.md) </span></span>  
 [<span data-ttu-id="75d20-140">솔루션 배포를 위한 구성 설정 지정</span><span class="sxs-lookup"><span data-stu-id="75d20-140">Specifying Configuration Settings for Solution Deployment</span></span>](deployment-script-files-solution-deployment-config-settings.md)  
  
  
