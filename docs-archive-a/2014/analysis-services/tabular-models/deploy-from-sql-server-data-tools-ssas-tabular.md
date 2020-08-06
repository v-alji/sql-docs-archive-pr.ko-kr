---
title: SQL Server Data Tools에서 배포 (SSAS 테이블 형식) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.deploystatus.f1
ms.assetid: 67dde3fe-ba43-41f3-b56c-c656029ee93f
author: minewiskan
ms.author: owend
ms.openlocfilehash: 8bc8008e7c79e1652b54b21e6afb116301d1700b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651916"
---
# <a name="deploy-from-sql-server-data-tools-ssas-tabular"></a><span data-ttu-id="db94d-102">SQL Server Data Tools에서 배포(SSAS 테이블 형식)</span><span class="sxs-lookup"><span data-stu-id="db94d-102">Deploy From SQL Server Data Tools (SSAS Tabular)</span></span>
  <span data-ttu-id="db94d-103">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]에서 배포 명령을 사용하여 테이블 형식 모델 솔루션을 배포하려면 이 항목의 태스크를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="db94d-103">Use the tasks in this topic to deploy a tabular model solution by using the Deploy command in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="db94d-104">이 항목의 섹션:</span><span class="sxs-lookup"><span data-stu-id="db94d-104">Sections in this topic:</span></span>  
  
-   [<span data-ttu-id="db94d-105">배포 옵션 및 배포 서버 속성 구성</span><span class="sxs-lookup"><span data-stu-id="db94d-105">Configure Deployment Options and Deployment Server Properties</span></span>](#bkmk_deploy)  
  
-   [<span data-ttu-id="db94d-106">테이블 형식 모델 솔루션 배포</span><span class="sxs-lookup"><span data-stu-id="db94d-106">Deploy a Tabular Model Solution</span></span>](#bkmk_deploy_proc)  
  
-   [<span data-ttu-id="db94d-107">배포 상태</span><span class="sxs-lookup"><span data-stu-id="db94d-107">Deploy Status</span></span>](#bkmk_deploy_status)  
  
##  <a name="configure-deployment-options-and-deployment-server-properties"></a><a name="bkmk_deploy"></a> <span data-ttu-id="db94d-108">배포 옵션 및 배포 서버 속성 구성</span><span class="sxs-lookup"><span data-stu-id="db94d-108">Configure Deployment Options and Deployment Server Properties</span></span>  
 <span data-ttu-id="db94d-109">테이블 형식 모델 솔루션을 배포하기 전에 먼저 배포 옵션 및 배포 서버 속성을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="db94d-109">Before you deploy your tabular model solution, you must first specify the Deployment Options and Deployment Server properties.</span></span> <span data-ttu-id="db94d-110">배포 속성 및 설정에 대한 자세한 내용은 [테이블 형식 모델 솔루션 배포&#40;SSAS 테이블 형식&#41;](tabular-model-solution-deployment-ssas-tabular.md)에서 배포 명령을 사용하여 테이블 형식 모델 솔루션을 배포하려면 이 항목의 태스크를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="db94d-110">For more information about deployment properties and settings, see [Tabular Model Solution Deployment &#40;SSAS Tabular&#41;](tabular-model-solution-deployment-ssas-tabular.md).</span></span>  
  
#### <a name="to-configure-deployment-options-and-deployment-server-properties"></a><span data-ttu-id="db94d-111">배포 옵션 및 배포 서버 속성을 구성하려면</span><span class="sxs-lookup"><span data-stu-id="db94d-111">To configure Deployment Options and Deployment Server properties</span></span>  
  
1.  <span data-ttu-id="db94d-112">[!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]의 **솔루션 탐색기**에서 프로젝트 이름을 마우스 오른쪽 단추로 클릭하고 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="db94d-112">In [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], in **Solution Explorer**, right-click the project name, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="db94d-113">\*\* \<project name> 속성\*\* 대화 상자의 **배포 옵션**에서 기본 설정과 다른 경우 속성 설정을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="db94d-113">In the **\<project name> Properties** dialog, in **Deployment Options**, specify property settings if different from the default settings.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="db94d-114">캐시된 모드의 모델의 경우 **쿼리 모드** 는 항상 **메모리 내**입니다.</span><span class="sxs-lookup"><span data-stu-id="db94d-114">For models in cached mode, **Query Mode** is always **In-Memory**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="db94d-115"> DirectQuery 모드에서는 모델에 **가장 설정** 을 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="db94d-115">You cannot specify **Impersonation Settings** for models in DirectQuery mode.</span></span>  
  
3.  <span data-ttu-id="db94d-116">**배포 서버**에서 기본 설정과 다른 경우 **서버** (이름), **버전**, **데이터베이스** (이름) 및 **큐브 이름** 속성 설정을 지정한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="db94d-116">In **Deployment Server**, specify the **Server** (name), **Edition**, **Database** (name), and **Cube Name** property settings, if different from the default settings, and then click **OK**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="db94d-117">새 프로젝트를 만들 때마다 자동으로 지정된 서버로 배포되도록 기본 배포 서버 속성 설정을 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db94d-117">You can also specify the Default Deployment Server property setting so any new projects you create will automatically be deployed to the specified server.</span></span> <span data-ttu-id="db94d-118">자세한 내용은 [기본 데이터 모델링 및 배포 속성 구성&#40;SSAS 테이블 형식&#41;](properties-ssas-tabular.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="db94d-118">For more information, see [Configure Default Data Modeling and Deployment Properties &#40;SSAS Tabular&#41;](properties-ssas-tabular.md).</span></span>  
  
##  <a name="deploy-a-tabular-model-solution"></a><a name="bkmk_deploy_proc"></a><span data-ttu-id="db94d-119">테이블 형식 모델 솔루션 배포</span><span class="sxs-lookup"><span data-stu-id="db94d-119">Deploy a Tabular Model Solution</span></span>  
  
#### <a name="to-deploy-a-tabular-model-solution"></a><span data-ttu-id="db94d-120">테이블 형식 모델 솔루션을 배포하려면</span><span class="sxs-lookup"><span data-stu-id="db94d-120">To deploy a tabular model solution</span></span>  
  
-   <span data-ttu-id="db94d-121">의 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] **빌드** 메뉴에서 \*\*배포 \<project name> \*\*를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="db94d-121">In [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], on the **Build** menu, click **Deploy \<project name>**.</span></span>  
  
     <span data-ttu-id="db94d-122">처리 옵션 속성이 처리 안 함으로 설정되지 않았으면 **배포** 대화 상자에 메타데이터 배포 및 모델에 포함된 각 테이블의 처리 상태가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="db94d-122">The **Deploy** dialog box will appear and indicate the status of the metadata deployment and the processing (unless Processing Option property is set to Do Not Process) of each table included in the model.</span></span> <span data-ttu-id="db94d-123">배포 프로세스가 완료된 후 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 를 사용하여 Analysis Services 인스턴스에 연결하고 새 model 데이터베이스 개체가 만들어졌는지 확인하거나, 클라이언트 보고 애플리케이션을 사용하여 배포 모델에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="db94d-123">After the deployment process is complete, use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to connect to the Analysis Services instance and verify the new model database object has been created or use a client reporting application to connect to the deployed model.</span></span>  
  
##  <a name="deploy-status"></a><a name="bkmk_deploy_status"></a> <span data-ttu-id="db94d-124">배포 상태</span><span class="sxs-lookup"><span data-stu-id="db94d-124">Deploy Status</span></span>  
 <span data-ttu-id="db94d-125">**배포** 대화 상자에서는 배포 작업의 진행 상황을 모니터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db94d-125">The **Deploy** dialog box enables you to monitor the progress of a Deploy operation.</span></span> <span data-ttu-id="db94d-126">배포 작업을 중지할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db94d-126">A deploy operation can also be stopped.</span></span>  
  
 <span data-ttu-id="db94d-127">**상태**</span><span class="sxs-lookup"><span data-stu-id="db94d-127">**Status**</span></span>  
 <span data-ttu-id="db94d-128">배포 작업의 성공 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="db94d-128">Indicates whether the Deploy operation was successful or not.</span></span>  
  
 <span data-ttu-id="db94d-129">**세부 정보**</span><span class="sxs-lookup"><span data-stu-id="db94d-129">**Details**</span></span>  
 <span data-ttu-id="db94d-130">배포된 메타데이터 항목 및 각 메타데이터 항목의 상태를 나열하고 각 문제에 대한 메시지를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="db94d-130">Lists the metadata items that were deployed, the status for each metadata item, and provides a message of any issues.</span></span>  
  
 <span data-ttu-id="db94d-131">**배포 중지**</span><span class="sxs-lookup"><span data-stu-id="db94d-131">**Stop Deploy**</span></span>  
 <span data-ttu-id="db94d-132">배포 작업을 중지하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="db94d-132">Click to halt the Deploy operation.</span></span> <span data-ttu-id="db94d-133">이 옵션은 배포 작업에 시간이 너무 많이 걸리거나 오류가 너무 많은 경우에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="db94d-133">This option is useful if the Deploy operation is taking too long, or if there are too many errors.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db94d-134">참고 항목</span><span class="sxs-lookup"><span data-stu-id="db94d-134">See Also</span></span>  
 <span data-ttu-id="db94d-135">[테이블 형식 모델 솔루션 배포 &#40;SSAS 테이블 형식&#41;](tabular-model-solution-deployment-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="db94d-135">[Tabular Model Solution Deployment &#40;SSAS Tabular&#41;](tabular-model-solution-deployment-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="db94d-136">기본 데이터 모델링 및 배포 속성 구성&#40;SSAS 테이블 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="db94d-136">Configure Default Data Modeling and Deployment Properties &#40;SSAS Tabular&#41;</span></span>](properties-ssas-tabular.md)  
  
  
