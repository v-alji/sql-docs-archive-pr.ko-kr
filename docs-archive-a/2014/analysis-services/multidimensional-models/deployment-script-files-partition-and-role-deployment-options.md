---
title: 파티션 및 역할 배포 옵션 지정 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- input files [Analysis Services]
- partitions [Analysis Services], deployment options
- Analysis Services deployments, roles
- Analysis Services deployments, partitions
- Analysis Services Deployment Wizard, roles
- Analysis Services Deployment Wizard, partitions
- deploying [Analysis Services], roles
- roles [Analysis Services], deployment options
- deploying [Analysis Services], partitions
- modifying role deployments
- modifying partition deployments
ms.assetid: e9b9ca57-a5cc-4fc0-87b5-305257038d56
author: minewiskan
ms.author: owend
ms.openlocfilehash: 8c8dd7bcb482c2d28a18e3039f5acb777b121202
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660162"
---
# <a name="specifying-partition-and-role-deployment-options"></a><span data-ttu-id="3224e-102">파티션 및 역할 배포 옵션 지정</span><span class="sxs-lookup"><span data-stu-id="3224e-102">Specifying Partition and Role Deployment Options</span></span>
  <span data-ttu-id="3224e-103">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]배포 마법사는 \<*project name*> deploymentoptions 파일에서 파티션 및 역할 배포 옵션을 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="3224e-103">The [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Deployment Wizard reads the partition and role deployment options from the \<*project name*>.deploymentoptions file.</span></span> [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]<span data-ttu-id="3224e-104">프로젝트를 빌드할 때이 파일을 만듭니다 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="3224e-104">creates this file when you build the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project.</span></span> [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]<span data-ttu-id="3224e-105">는 deploymentoptions 파일이 생성 될 때 현재 프로젝트의 파티션 및 역할 배포 옵션을 사용 합니다 \<*project name*> .</span><span class="sxs-lookup"><span data-stu-id="3224e-105">uses the partition and role deployment options of the current project when the \<*project name*>.deploymentoptions file is created.</span></span> <span data-ttu-id="3224e-106">이러한 구성 설정에 대한 자세한 내용은 [Understanding the Input Files Used to Create the Deployment Script](deployment-script-files-input-used-to-create-deployment-script.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="3224e-106">For more information about configuration settings, see [Understanding the Input Files Used to Create the Deployment Script](deployment-script-files-input-used-to-create-deployment-script.md).</span></span>  
  
## <a name="reviewing-the-partition-and-role-deployment-options"></a><span data-ttu-id="3224e-107">파티션 및 역할 배포 옵션 검토</span><span class="sxs-lookup"><span data-stu-id="3224e-107">Reviewing the Partition and Role Deployment Options</span></span>  
 <span data-ttu-id="3224e-108">Deploymentoptions 파일의 배포 옵션에는 \<*project name*> 다음이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3224e-108">The deployment options in the \<*project name*>.deploymentoptions file include the following:</span></span>  
  
 <span data-ttu-id="3224e-109">**파티션 배포 옵션**</span><span class="sxs-lookup"><span data-stu-id="3224e-109">**Partition deployment options**</span></span>  
 <span data-ttu-id="3224e-110">\<*project name*>Deploymentoptions 파일은 대상 데이터베이스의 기존 파티션을 유지 하거나 덮어쓸지 (기본값) 여부를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3224e-110">The \<*project name*>.deploymentoptions file specifies whether existing partitions in the destination database are retained or overwritten (default).</span></span> <span data-ttu-id="3224e-111">기존 파티션을 유지하는 경우 새 파티션만 배포되고 기존의 모든 측정값 그룹에 있는 파티션 및 집계 디자인은 변경되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3224e-111">If existing partitions are retained, only new partitions will be deployed, and the partitions and aggregation designs on all existing measure groups are left unchanged.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3224e-112">파티션이 존재하는 측정값 그룹이 삭제되면 파티션이 자동으로 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="3224e-112">If the measure group in which the partition exists is deleted, the partition is automatically deleted.</span></span>  
  
 <span data-ttu-id="3224e-113">**역할 배포 옵션**</span><span class="sxs-lookup"><span data-stu-id="3224e-113">**Role deployment options**</span></span>  
 <span data-ttu-id="3224e-114">\<*project name*>Deploymentoptions 파일은 다음 역할 배포 옵션 중 하나를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3224e-114">The \<*project name*>.deploymentoptions file specifies one of the following role deployment options:</span></span>  
  
-   <span data-ttu-id="3224e-115">대상 데이터베이스의 기존 역할 및 역할 멤버는 유지되고 새로운 역할 및 역할 멤버만 배포됩니다.</span><span class="sxs-lookup"><span data-stu-id="3224e-115">Existing roles and role members in the destination database are retained, and only new roles and role members are deployed.</span></span>  
  
-   <span data-ttu-id="3224e-116">대상 데이터베이스의 모든 기존 역할 및 멤버가 배포되는 역할 및 멤버로 교체됩니다.</span><span class="sxs-lookup"><span data-stu-id="3224e-116">All existing roles and members in the destination database are replaced by the roles and members being deployed.</span></span>  
  
-   <span data-ttu-id="3224e-117">대상 데이터베이스의 기존 역할 및 역할 멤버가 유지되고 새 역할이 배포되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3224e-117">Existing roles and role members in the destination database are retained, and no new roles are deployed.</span></span>  
  
-   <span data-ttu-id="3224e-118">**참고** 기존 역할과 멤버가 보존되는 경우 해당 역할과 관련된 권한은 없음으로 다시 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="3224e-118">**Note** When existing roles and members are retained, the permissions associated with those roles are reset to none.</span></span> <span data-ttu-id="3224e-119">보안 권한은 관련된 보안 역할이 아닌 보안을 설정하는 개체에 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="3224e-119">Security permissions are contained by the objects they secure, not by the security roles with which they are associated.</span></span> <span data-ttu-id="3224e-120">Analysis Service 배포 마법사를 사용 하 여이 동작을 수행 하는 방법에 대 한 자세한 내용은 Microsoft 기술 자료에서 ' 역할 및 멤버 유지 '를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="3224e-120">For more information about how to work with this behavior by using the Analysis Service Deployment Wizard, see 'Retain Roles and Members' in the Microsoft Knowledge Base.</span></span>  
  
## <a name="modifying-the-partition-and-role-deployment-options"></a><span data-ttu-id="3224e-121">파티션 및 역할 배포 옵션 수정</span><span class="sxs-lookup"><span data-stu-id="3224e-121">Modifying the Partition and Role Deployment Options</span></span>  
 <span data-ttu-id="3224e-122">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]Deploymentoptions 파일에 저장 된 것과 다른 파티션 및 역할 옵션을 사용 하 여 프로젝트를 배포 해야 할 수 있습니다. \<*project name*></span><span class="sxs-lookup"><span data-stu-id="3224e-122">You may have to deploy the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project using different partition and role options than those stored in the \<*project name*>.deploymentoptions file.</span></span> <span data-ttu-id="3224e-123">예를 들어 deploymentoptions 파일에 표시 된 대로 기존 파티션, 역할 및 멤버를 모두 대체 하는 대신 기존 파티션, 역할 및 역할 멤버를 유지 하려고 할 수 있습니다. \<*project name*></span><span class="sxs-lookup"><span data-stu-id="3224e-123">For example, you may want to retain existing partitions, roles, and role members, instead of replacing all existing partitions, roles, and members as indicated in the \<*project name*>.deploymentoptions file.</span></span>  
  
 <span data-ttu-id="3224e-124">프로젝트에서 파티션 및 역할의 배포를 수정 하려면 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] *\<project name>* 의 **속성 페이지** 대화 상자에 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 이러한 옵션이 표시 되지 않기 때문에 프로젝트 내에서 파티션 및 역할 설정을 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3224e-124">To modify the deployment of partitions and roles in an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project, you cannot change the partition and roles settings within the project because the *\<project name>* **Properties Pages** dialog box in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] does not display these options.</span></span> <span data-ttu-id="3224e-125">역할 및 파티션에 대 한 배포 옵션을 변경 하려면 \<*project name*> deploymentoptions 파일 자체에서이 정보를 변경 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3224e-125">If you want to change the deployment options for roles and partitions, you must change this information within the \<*project name*>.deploymentoptions file itself.</span></span> <span data-ttu-id="3224e-126">다음 절차에서는 deploymentoptions 파일 내에서 파티션 및 역할 배포 옵션을 변경 하는 방법에 대해 설명 합니다. \<*project name*></span><span class="sxs-lookup"><span data-stu-id="3224e-126">The following procedure describes how to change the partition and role deployment options within the \<*project name*>.deploymentoptions file.</span></span>  
  
#### <a name="to-change-the-deployment-of-partitions-or-roles-after-the-input-files-have-been-generated"></a><span data-ttu-id="3224e-127">입력 파일을 생성한 다음 파티션 또는 역할 배포를 변경하려면</span><span class="sxs-lookup"><span data-stu-id="3224e-127">To change the deployment of partitions or roles after the input files have been generated</span></span>  
  
-   <span data-ttu-id="3224e-128">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 배포 마법사를 대화식으로 실행하고 **파티션 및 역할 배포 옵션** 페이지에서 파티션 및 역할에 대한 새 배포 옵션을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3224e-128">Run the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Deployment Wizard interactively, and on the **Partition and Role Deployment Options** page, specify new deployment options for the partitions and roles.</span></span>  
  
     <span data-ttu-id="3224e-129">또는</span><span class="sxs-lookup"><span data-stu-id="3224e-129">-or-</span></span>  
  
-   <span data-ttu-id="3224e-130">명령 프롬프트에서 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 배포 마법사를 실행하여 응답 파일 모드에서 마법사를 실행하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="3224e-130">Run the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Deployment Wizard at the command prompt, and set the wizard to run in answer file mode.</span></span> <span data-ttu-id="3224e-131">응답 파일 모드에 대 한 자세한 내용은 [Analysis Services 배포 마법사 실행](running-the-analysis-services-deployment-wizard.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="3224e-131">(For more information about answer file mode, see [Running the Analysis Services Deployment Wizard](running-the-analysis-services-deployment-wizard.md).)</span></span>  
  
     <span data-ttu-id="3224e-132">또는</span><span class="sxs-lookup"><span data-stu-id="3224e-132">-or-</span></span>  
  
-   <span data-ttu-id="3224e-133">\<*project name*>텍스트 편집기에서 deploymentoptions를 열고 옵션을 수동으로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="3224e-133">Open the \<*project name*>.deploymentoptions in any text editor and manually change the options.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3224e-134">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3224e-134">See Also</span></span>  
 <span data-ttu-id="3224e-135">[설치 대상 지정](deployment-script-files-specifying-the-installation-target.md) </span><span class="sxs-lookup"><span data-stu-id="3224e-135">[Specifying the Installation Target](deployment-script-files-specifying-the-installation-target.md) </span></span>  
 <span data-ttu-id="3224e-136">[솔루션 배포를 위한 구성 설정 지정](deployment-script-files-solution-deployment-config-settings.md) </span><span class="sxs-lookup"><span data-stu-id="3224e-136">[Specifying Configuration Settings for Solution Deployment](deployment-script-files-solution-deployment-config-settings.md) </span></span>  
 [<span data-ttu-id="3224e-137">처리 옵션 지정</span><span class="sxs-lookup"><span data-stu-id="3224e-137">Specifying Processing Options</span></span>](deployment-script-files-specifying-processing-options.md)  
  
  
