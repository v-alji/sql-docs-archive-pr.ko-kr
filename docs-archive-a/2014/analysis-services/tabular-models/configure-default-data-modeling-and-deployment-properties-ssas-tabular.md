---
title: 기본 데이터 모델링 및 배포 속성 구성 (SSAS 테이블 형식) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.deployment.f1
- VS.TOOLSOPTIONSPAGES.ANALYSIS_SERVICES.DATA_MODELING
- sql12.asvs.bidtoolset.asoptions.f1
- VS.TOOLSOPTIONSPAGES.ANALYSIS_SERVICES.DEPLOYMENT
ms.assetid: 140d0c4e-943c-4387-a8d2-6e066c7e4e75
author: minewiskan
ms.author: owend
ms.openlocfilehash: 62d3697a0308eab51002867347df63145decfa93
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649221"
---
# <a name="configure-default-data-modeling-and-deployment-properties-ssas-tabular"></a><span data-ttu-id="64d14-102">기본 데이터 모델링 및 배포 속성 구성(SSAS 테이블 형식)</span><span class="sxs-lookup"><span data-stu-id="64d14-102">Configure Default Data Modeling and Deployment Properties (SSAS Tabular)</span></span>
  <span data-ttu-id="64d14-103">이 항목에서는 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]에서 만든 각각의 새로운 테이블 형식 모델 프로젝트에 대해 미리 정의될 수 있는 기본 호환성 수준, 배포 및 작업 영역 데이터베이스 속성 설정을 구성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="64d14-103">This topic describes how to configure the default compatibility level, deployment and workspace database property settings, which can be pre-defined for each new tabular model project you create in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="64d14-104">새 프로젝트를 만든 후 특정 요구 사항에 따라 이러한 속성을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="64d14-104">After a new project is created, these properties can still be changed depending on your particular requirements.</span></span>  
  
#### <a name="to-configure-the-default-compatibility-level-property-setting-for-new-model-projects"></a><span data-ttu-id="64d14-105">새 모델 프로젝트의 기본 호환성 수준 속성 설정을 구성하려면</span><span class="sxs-lookup"><span data-stu-id="64d14-105">To configure the default Compatibility Level property setting for new model projects</span></span>  
  
1.  <span data-ttu-id="64d14-106">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]에서 **도구** 메뉴를 클릭한 다음 **옵션**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="64d14-106">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], click the **Tools** menu, and then click **Options**.</span></span>  
  
2.  <span data-ttu-id="64d14-107">**옵션** 대화 상자에서 **Analysis Services 테이블 형식 디자이너**를 확장한 다음 **호환성 수준**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="64d14-107">In the **Options** dialog box, expand **Analysis Services Tabular Designers**, and then click **Compatibility Level**.</span></span>  
  
3.  <span data-ttu-id="64d14-108">다음 속성 설정을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="64d14-108">Configure the following property settings:</span></span>  
  
    |<span data-ttu-id="64d14-109">속성</span><span class="sxs-lookup"><span data-stu-id="64d14-109">Property</span></span>|<span data-ttu-id="64d14-110">기본 설정</span><span class="sxs-lookup"><span data-stu-id="64d14-110">Default setting</span></span>|<span data-ttu-id="64d14-111">Description</span><span class="sxs-lookup"><span data-stu-id="64d14-111">Description</span></span>|  
    |--------------|---------------------|-----------------|  
    |<span data-ttu-id="64d14-112">**새 프로젝트의 기본 호환성 수준**</span><span class="sxs-lookup"><span data-stu-id="64d14-112">**Default compatibility level for new projects**</span></span>|<span data-ttu-id="64d14-113">SQL Server 2012 (1100)</span><span class="sxs-lookup"><span data-stu-id="64d14-113">SQL Server 2012 (1100)</span></span>|<span data-ttu-id="64d14-114">이 설정은 새 테이블 형식 모델 프로젝트를 만들 때 사용할 기본 호환성 수준을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="64d14-114">This setting specifies the default compatibility level to use when creating a new Tabular model project.</span></span> <span data-ttu-id="64d14-115">SP1이 적용되지 않은 Analysis Services 인스턴스에 배포하려는 경우 SQL Server 2012 RTM(1100)을 선택하거나 배포 인스턴스에 SP1이 적용된 경우 SQL Server 2012 SP1 또는 SQL Server 2014를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="64d14-115">You can choose SQL Server 2012 RTM (1100) if you will deploy to an Analysis Services instance without SP1 applied, or SQL Server 2012 SP1 if your deployment instance has SP1 applied, or SQL Server 2014.</span></span> <span data-ttu-id="64d14-116">자세한 내용은 [호환성 수준 &#40;SSAS 테이블 형식 SP1&#41;](compatibility-level-for-tabular-models-in-analysis-services.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="64d14-116">For more information, see [Compatibility Level &#40;SSAS Tabular SP1&#41;](compatibility-level-for-tabular-models-in-analysis-services.md).</span></span>|  
    |<span data-ttu-id="64d14-117">**호환성 수준 옵션**</span><span class="sxs-lookup"><span data-stu-id="64d14-117">**Compatibility level options**</span></span>|<span data-ttu-id="64d14-118">모든 선택됨</span><span class="sxs-lookup"><span data-stu-id="64d14-118">All checked</span></span>|<span data-ttu-id="64d14-119">새 테이블 형식 모델 프로젝트의 호환성 수준 옵션 및 다른 Analysis Services 인스턴스에 배포할 시기를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="64d14-119">Specifies compatibility level options for new Tabular model projects and when deploying to another Analysis Services instance.</span></span>|  
  
#### <a name="to-configure-the-default-deployment-server-property-setting-for-new-model-projects"></a><span data-ttu-id="64d14-120">새 모델 프로젝트의 기본 배포 서버 속성 설정을 구성하려면</span><span class="sxs-lookup"><span data-stu-id="64d14-120">To configure the default deployment server property setting for new model projects</span></span>  
  
1.  <span data-ttu-id="64d14-121">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]에서 **도구** 메뉴를 클릭한 다음 **옵션**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="64d14-121">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], click the **Tools** menu, and then click **Options**.</span></span>  
  
2.  <span data-ttu-id="64d14-122">**옵션** 대화 상자에서 **Analysis Services 테이블 형식 디자이너**를 확장한 다음 **배포**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="64d14-122">In the **Options** dialog box, expand **Analysis Services Tabular Designers**, and then click **Deployment**.</span></span>  
  
3.  <span data-ttu-id="64d14-123">다음 속성 설정을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="64d14-123">Configure the following property settings:</span></span>  
  
    |<span data-ttu-id="64d14-124">속성</span><span class="sxs-lookup"><span data-stu-id="64d14-124">Property</span></span>|<span data-ttu-id="64d14-125">기본 설정</span><span class="sxs-lookup"><span data-stu-id="64d14-125">Default setting</span></span>|<span data-ttu-id="64d14-126">Description</span><span class="sxs-lookup"><span data-stu-id="64d14-126">Description</span></span>|  
    |--------------|---------------------|-----------------|  
    |<span data-ttu-id="64d14-127">**기본 배포 서버**</span><span class="sxs-lookup"><span data-stu-id="64d14-127">**Default deployment server**</span></span>|<span data-ttu-id="64d14-128">localhost</span><span class="sxs-lookup"><span data-stu-id="64d14-128">localhost</span></span>|<span data-ttu-id="64d14-129">이 설정은 모델을 배포할 때 사용할 기본 서버를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="64d14-129">This setting specifies the default server to use when deploying a model.</span></span> <span data-ttu-id="64d14-130">아래쪽 화살표를 클릭하여 사용할 수 있는 로컬 네트워크 Analysis Services 서버를 찾아보거나 원격 서버의 이름을 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="64d14-130">You can click the down arrow to browse for local network Analysis Services servers you can use or you can type the name of a remote server.</span></span>|  
  
    > [!NOTE]  
    >  <span data-ttu-id="64d14-131">기본 배포 서버 속성 설정을 변경해도 변경 전에 만들어진 기존 프로젝트는 영향을 받지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="64d14-131">Changes to the Default deployment Server property setting will not affect existing projects created prior to the change.</span></span>  
  
###  <a name="to-configure-the-default-workspace-database-property-settings-for-new-model-projects"></a><a name="bkmk_conf_default"></a> <span data-ttu-id="64d14-132">새 모델 프로젝트의 기본 작업 영역 데이터베이스 속성 설정을 구성하려면</span><span class="sxs-lookup"><span data-stu-id="64d14-132">To configure the default Workspace Database property settings for new model projects</span></span>  
  
1.  <span data-ttu-id="64d14-133">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]에서 **도구** 메뉴를 클릭한 다음 **옵션**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="64d14-133">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], click the **Tools** menu, and then click **Options**.</span></span>  
  
2.  <span data-ttu-id="64d14-134">**옵션** 대화 상자에서 **Analysis Services 테이블 형식 디자이너**를 확장한 다음 **작업 영역 데이터베이스**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="64d14-134">In the **Options** dialog box, expand **Analysis Services Tabular Designers**, and then click **Workspace Database**.</span></span>  
  
3.  <span data-ttu-id="64d14-135">다음 속성 설정을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="64d14-135">Configure the following property settings:</span></span>  
  
    |<span data-ttu-id="64d14-136">속성</span><span class="sxs-lookup"><span data-stu-id="64d14-136">Property</span></span>|<span data-ttu-id="64d14-137">기본 설정</span><span class="sxs-lookup"><span data-stu-id="64d14-137">Default setting</span></span>|<span data-ttu-id="64d14-138">Description</span><span class="sxs-lookup"><span data-stu-id="64d14-138">Description</span></span>|  
    |--------------|---------------------|-----------------|  
    |<span data-ttu-id="64d14-139">**기본 작업 영역 서버**</span><span class="sxs-lookup"><span data-stu-id="64d14-139">**Default workspace server**</span></span>|<span data-ttu-id="64d14-140">**localhost**</span><span class="sxs-lookup"><span data-stu-id="64d14-140">**localhost**</span></span>|<span data-ttu-id="64d14-141">이 속성은 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]에서 모델을 작성하는 동안 작업 영역 데이터베이스를 호스팅하는 데 사용할 기본 서버를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="64d14-141">This property specifies the default server that will be used to host the workspace database while the model is being authored in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="64d14-142">로컬 컴퓨터에서 실행되는 Analysis Services의 모든 사용 가능한 인스턴스가 목록 상자에 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="64d14-142">All available instances of Analysis Services running on the local computer are included in the listbox.</span></span><br /><br /> <span data-ttu-id="64d14-143">참고: 항상 로컬 Analysis Services 서버를 작업 영역 서버로 지정하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="64d14-143">Note: It is recommended that you always specify a local Analysis Services server as the workspace server.</span></span> <span data-ttu-id="64d14-144">원격 서버에 있는 작업 영역 데이터베이스의 경우 PowerPivot에서 데이터 가져오기가 지원되지 않고 데이터를 로컬로 백업할 수 없으며 쿼리 중에 사용자 인터페이스에서 지연이 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="64d14-144">For workspace databases on a remote server, importing data from PowerPivot is not supported, data cannot be backed up locally, and the user interface may experience latency during queries.</span></span>|  
    |<span data-ttu-id="64d14-145">**모델을 닫은 후 작업 영역 데이터베이스 보존**</span><span class="sxs-lookup"><span data-stu-id="64d14-145">**Workspace database retention after the model is closed**</span></span>|<span data-ttu-id="64d14-146">**작업 영역 데이터베이스를 디스크에 유지하지만 메모리에서 언로드**</span><span class="sxs-lookup"><span data-stu-id="64d14-146">**Keep workspace databases on disk, but unload from memory**</span></span>|<span data-ttu-id="64d14-147">모델을 닫은 후 작업 영역 데이터베이스가 보존되는 방법을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="64d14-147">Specifies how a workspace database is retained after a model is closed.</span></span> <span data-ttu-id="64d14-148">작업 영역 데이터베이스에는 모델 메타데이터, 모델로 가져온 데이터 및 가장 자격 증명(암호화됨)이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="64d14-148">A workspace database includes model metadata, the data imported into a model, and impersonation credentials (encrypted).</span></span> <span data-ttu-id="64d14-149">경우에 따라 작업 영역 데이터베이스가 매우 크고 많은 양의 메모리를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="64d14-149">In some cases, the workspace database can be very large and consume a significant amount of memory.</span></span> <span data-ttu-id="64d14-150">기본적으로 작업 영역 데이터베이스는 메모리에서 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="64d14-150">By default, workspace databases are removed from memory.</span></span> <span data-ttu-id="64d14-151">이 설정을 변경할 때는 모델에서 작업할 빈도뿐만 아니라 사용 가능한 메모리 리소스를 고려해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="64d14-151">When changing this setting, it is important to consider your available memory resources as well as how often you plan to work on the model.</span></span> <span data-ttu-id="64d14-152">이 속성 설정에는 다음과 같은 옵션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="64d14-152">This property setting has the following options:</span></span><br /><br /> <span data-ttu-id="64d14-153">**작업 영역을 메모리에 유지** - 모델을 닫은 후 메모리에 작업 영역을 유지하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="64d14-153">**Keep workspaces in memory** - Specifies to keep workspaces in memory after a model is closed.</span></span> <span data-ttu-id="64d14-154">이 옵션을 사용하면 메모리 소비량이 많아지지만 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]에서 모델을 열 때 리소스가 더 적게 사용되며 작업 영역이 더 빠르게 로드됩니다.</span><span class="sxs-lookup"><span data-stu-id="64d14-154">This option will consume more memory; however, when opening a model in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], fewer resources are consumed and the workspace will load faster.</span></span><br /><br /> <span data-ttu-id="64d14-155">**작업 영역 데이터베이스를 디스크에 유지하지만 메모리에서 언로드** - 모델을 닫은 후 디스크에는 작업 영역 데이터베이스를 유지하지만 메모리에는 유지하지 않도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="64d14-155">**Keep workspace databases on disk, but unload from memory** - Specifies to keep the workspace database on disk, but no longer in memory after a model is closed.</span></span> <span data-ttu-id="64d14-156">이 옵션을 사용하면 메모리 소비량이 적어지지만 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]에서 모델을 열 때 리소스가 추가로 소비되며 작업 영역 데이터베이스가 메모리에 유지되는 경우보다 느리게 모델이 로드됩니다.</span><span class="sxs-lookup"><span data-stu-id="64d14-156">This option will consume less memory; however, when opening a model in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], additional resources are consumed and the model will load more slowly than if the workspace database is kept in memory.</span></span> <span data-ttu-id="64d14-157">메모리 내 리소스가 제한되어 있거나 원격 작업 영역 데이터베이스에서 작업하는 경우 이 옵션을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="64d14-157">Use this option when in-memory resources are limited or when working on a remote workspace database.</span></span><br /><br /> <span data-ttu-id="64d14-158">**작업 영역 삭제** - 모델을 닫은 후 메모리에서 작업 영역 데이터베이스를 삭제하고 디스크에 작업 영역 데이터베이스를 유지하지 않도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="64d14-158">**Delete workspace** - Specifies to delete workspace database from memory and not keep workspace database on disk after the model is closed.</span></span> <span data-ttu-id="64d14-159">이 옵션을 사용하면 메모리 및 스토리지 공간 소비량이 적어지지만 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]에서 모델을 열 때 리소스가 추가로 소비되며 작업 영역 데이터베이스가 메모리나 디스크에 유지되는 경우보다 느리게 모델이 로드됩니다.</span><span class="sxs-lookup"><span data-stu-id="64d14-159">This option will consume less memory and storage space; however, when opening a model in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], additional resources are consumed and the model will load more slowly than if the workspace database is kept in memory or on-disk.</span></span> <span data-ttu-id="64d14-160">가끔씩만 모델에서 작업하는 경우 이 옵션을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="64d14-160">Use this option when only occasionally working on models.</span></span>|  
    |<span data-ttu-id="64d14-161">**데이터 백업**</span><span class="sxs-lookup"><span data-stu-id="64d14-161">**Data backup**</span></span>|<span data-ttu-id="64d14-162">**디스크 데이터의 백업 보관**</span><span class="sxs-lookup"><span data-stu-id="64d14-162">**Keep backup of data on disk**</span></span>|<span data-ttu-id="64d14-163">모델 데이터의 백업이 백업 파일에 유지되는지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="64d14-163">Specifies whether or not a backup of the model data is kept in a backup file.</span></span> <span data-ttu-id="64d14-164">이 속성 설정에는 다음과 같은 옵션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="64d14-164">This property setting has the following options:</span></span><br /><br /> <span data-ttu-id="64d14-165">**디스크에 데이터 백업 보관** - 모델 데이터의 백업을 디스크에 보관하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="64d14-165">**Keep backup of data on disk** - Specifies to keep a backup of model data on disk.</span></span> <span data-ttu-id="64d14-166">모델을 저장하면 데이터가 백업 파일(ABF)에도 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="64d14-166">When the model is saved, the data will also be saved to the backup (ABF) file.</span></span> <span data-ttu-id="64d14-167">이 옵션을 선택하면 모델 저장 및 로드 시간이 길어질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="64d14-167">Selecting this option can cause slower model save and load times</span></span><br /><br /> <span data-ttu-id="64d14-168">**디스크에 데이터 백업 보관 안 함** - 모델 데이터의 백업을 디스크에 보관하지 않도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="64d14-168">**Do not keep backup of databack on disk** - Specifies to not keep a backup of model data on disk.</span></span> <span data-ttu-id="64d14-169">이 옵션을 사용하면 저장 및 모델 로드 시간이 최소화됩니다.</span><span class="sxs-lookup"><span data-stu-id="64d14-169">This option will minimize save and model loading time.</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="64d14-170">기본 모델 속성을 변경해도 변경 전에 만들어진 기존 모델의 속성은 영향을 받지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="64d14-170">Changes to default model properties will not affect properties for existing models created prior to the change.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64d14-171">참고 항목</span><span class="sxs-lookup"><span data-stu-id="64d14-171">See Also</span></span>  
 <span data-ttu-id="64d14-172">[프로젝트 속성 &#40;SSAS 테이블 형식&#41;](properties-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="64d14-172">[Project Properties &#40;SSAS Tabular&#41;](properties-ssas-tabular.md) </span></span>  
 <span data-ttu-id="64d14-173">[SSAS 테이블 형식&#41;&#40;모델 속성](model-properties-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="64d14-173">[Model Properties &#40;SSAS Tabular&#41;](model-properties-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="64d14-174">호환성 수준 &#40;SSAS 테이블 형식 SP1&#41;</span><span class="sxs-lookup"><span data-stu-id="64d14-174">Compatibility Level &#40;SSAS Tabular SP1&#41;</span></span>](compatibility-level-for-tabular-models-in-analysis-services.md)  
  
  