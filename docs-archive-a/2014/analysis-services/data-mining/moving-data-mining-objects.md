---
title: 데이터 마이닝 개체 이동 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data mining [Analysis Services], models
- data mining editor [Analysis Services]
- mining models [Analysis Services], managing
- Data Mining Designer
- mining models [Analysis Services], modifying
ms.assetid: bc108407-2603-4387-b930-b5bb9df78069
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2b10be3a79487376b173eab87059404b7f7a618e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728967"
---
# <a name="moving-data-mining-objects"></a><span data-ttu-id="1be60-102">데이터 마이닝 개체 이동</span><span class="sxs-lookup"><span data-stu-id="1be60-102">Moving Data Mining Objects</span></span>
  <span data-ttu-id="1be60-103">데이터 마이닝 개체를 이동하기 위한 가장 일반적인 시나리오는 테스트 또는 분석 환경에서 프로덕션 환경으로 모델을 배포하거나 다른 사용자와 모델을 공유하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="1be60-103">The most common scenarios for moving data mining objects are to deploy a model from a testing or analysis environment to a production environment, or to share models with other users.</span></span>  
  
 <span data-ttu-id="1be60-104">이 항목에서는 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]에서 제공하는 도구와 스크립트 언어를 사용하여 데이터 마이닝 개체를 이동하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="1be60-104">This topic describes how you can use the tools and scripting languages provided by [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], for moving data mining objects.</span></span>  
  
## <a name="moving-data-mining-objects-between-databases-or-servers"></a><span data-ttu-id="1be60-105">데이터베이스 또는 서버 간 데이터 마이닝 개체 이동</span><span class="sxs-lookup"><span data-stu-id="1be60-105">Moving Data Mining Objects between Databases or Servers</span></span>  
 <span data-ttu-id="1be60-106">다음 방법으로 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 데이터베이스 간이나 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스 간에 데이터 마이닝 개체를 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1be60-106">You can move data mining objects between [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] databases or between instances of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] in the following ways:</span></span>  
  
-   <span data-ttu-id="1be60-107">다른 데이터베이스에 솔루션을 다시 배포합니다.</span><span class="sxs-lookup"><span data-stu-id="1be60-107">Re-deploying the solution to a different database.</span></span>  
  
-   <span data-ttu-id="1be60-108">개별 개체 스크립팅</span><span class="sxs-lookup"><span data-stu-id="1be60-108">Scripting individual objects.</span></span>  
  
-   <span data-ttu-id="1be60-109">데이터베이스의 복사본을 백업한 다음 복원</span><span class="sxs-lookup"><span data-stu-id="1be60-109">Backing up and then restoring a copy of the database.</span></span>  
  
-   <span data-ttu-id="1be60-110">구조와 모델 내보내기 및 가져오기</span><span class="sxs-lookup"><span data-stu-id="1be60-110">Exporting and importing structures and models.</span></span>  
  
 <span data-ttu-id="1be60-111">다음 섹션에서는 이러한 옵션에 대해 자세히 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="1be60-111">The following section explains these options in more detail.</span></span>  
  
### <a name="deploying"></a><span data-ttu-id="1be60-112">배포 중</span><span class="sxs-lookup"><span data-stu-id="1be60-112">Deploying</span></span>  
 <span data-ttu-id="1be60-113">다른 서버나 데이터베이스에 솔루션을 배포하려면 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]를 사용하여 만든 솔루션 파일이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1be60-113">Deploying the solution to a different server or database requires that you have the solution file that was created by using [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="1be60-114">Analysis Services 솔루션 배포에 대한 자세한 내용은 [Analysis Services 프로젝트 배포&#40;SSDT&#41;](../multidimensional-models/deploy-analysis-services-projects-ssdt.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1be60-114">For more information about deploying Analysis Services solutions, see [Deploy Analysis Services Projects &#40;SSDT&#41;](../multidimensional-models/deploy-analysis-services-projects-ssdt.md).</span></span>  
  
### <a name="scripting"></a><span data-ttu-id="1be60-115">스크립팅</span><span class="sxs-lookup"><span data-stu-id="1be60-115">Scripting</span></span>  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="1be60-116">은 개체를 스크립팅하는 데 사용할 수 있는 여러 언어를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="1be60-116">provides several languages that you can use to script objects.</span></span>  
  
-   <span data-ttu-id="1be60-117">**XMLA**: [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 개체를 마우스 오른쪽 단추로 클릭하면 XMLA를 사용하여 개체를 스크립팅할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1be60-117">**XMLA**: You can script objects using XMLA by right-clicking objects in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="1be60-118">스크립트를 실행하려면 대상 서버의 **XMLA 쿼리** 창에서 스크립트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="1be60-118">To execute the script, open it in an **XMLA Query** window on the target server.</span></span>  
  
-   <span data-ttu-id="1be60-119">**DMX**: [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] 및 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 제공하는 템플릿 또는 쿼리 작성기 중 하나를 사용하여 스크립트를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1be60-119">**DMX**: You can create scripts by using templates or one of the query builders provided in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] and [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="1be60-120">하지만 각 스크립트 언어로 수행할 수 있는 태스크에는 차이가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1be60-120">Note, however, that there are differences in the tasks that you can perform with each scripting language:</span></span>  
  
-   <span data-ttu-id="1be60-121">개체 설명 및 데이터 바인딩과 같은 속성은 DMX가 아닌 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] DDL 언어를 사용해서만 만들거나 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1be60-121">Properties such as the object description and data bindings can only by created or changed by using [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] DDL languages, not by using DMX.</span></span>  
  
-   <span data-ttu-id="1be60-122">DMX만 마이닝 개체의 가져오기 및 내보내기를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="1be60-122">Only DMX supports the import and export of mining objects.</span></span>  
  
-   <span data-ttu-id="1be60-123">DMX만 PMML 생성 또는 PMML에서 모델 정의 가져오기를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="1be60-123">Only DMX supports generating PMML or importing model definitions from PMML.</span></span>  
  
-   <span data-ttu-id="1be60-124">DMX만 애플리케이션 데이터를 사용한 모델 학습을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="1be60-124">Only DMX supports training a model with application data.</span></span> <span data-ttu-id="1be60-125">또한 DMX INSERT INTO 문은 키 열의 값을 제공하지 않는 모델 학습을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="1be60-125">Moreover, the DMX INSERT INTO statement supports training a model without providing values for a key column.</span></span>  
  
 <span data-ttu-id="1be60-126">자세한 내용은 [ASSL&#40;Analysis Services Scripting Language&#41;을 사용하여 개발](../multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="1be60-126">For more information, see [Developing with Analysis Services Scripting Language &#40;ASSL&#41;](../multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md).</span></span>  
  
### <a name="backup-and-restore"></a><span data-ttu-id="1be60-127">Backup 및 복원</span><span class="sxs-lookup"><span data-stu-id="1be60-127">Backup and Restore</span></span>  
 <span data-ttu-id="1be60-128">전체 Analysis Services 데이터베이스의 백업 및 복원은 현재 데이터 마이닝 구조가 OLAP 개체에 의존하는 경우 선택하는 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="1be60-128">Backup and restore of an entire Analysis Services database is the method of choice if your data mining solution relies on OLAP objects.</span></span> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="1be60-129">는 데이터베이스 백업을 더 빠르고 쉽게 할 수 있는 새로운 백업 및 복원 기능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="1be60-129">provides backup and restore functionality that makes database backups faster and easier.</span></span>  
  
 <span data-ttu-id="1be60-130">백업에 대한 자세한 내용은 [Analysis Services 데이터베이스 백업 및 복원](../multidimensional-models/backup-and-restore-of-analysis-services-databases.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1be60-130">For more information about backup, see [Backup and Restore of Analysis Services Databases](../multidimensional-models/backup-and-restore-of-analysis-services-databases.md).</span></span>  
  
### <a name="exporting-and-importing"></a><span data-ttu-id="1be60-131">내보내기 및 가져오기</span><span class="sxs-lookup"><span data-stu-id="1be60-131">Exporting and Importing</span></span>  
 <span data-ttu-id="1be60-132">DMX 문을 사용하여 마이닝 모델 및 구조를 내보낸 다음 다시 가져오는 것은 개별 관계형 데이터 마이닝 개체를 이동하거나 백업하는 가장 쉬운 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="1be60-132">Exporting and then re-importing mining models and structures by using DMX statements is the easiest way to move or back up individual relational data mining objects.</span></span> <span data-ttu-id="1be60-133">이러한 작업에 사용하는 DMX 구문에 대한 자세한 내용은 다음 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="1be60-133">For more information about the DMX syntax for these operations, see the following topics:</span></span>  
  
-   [<span data-ttu-id="1be60-134">EXPORT&#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="1be60-134">EXPORT &#40;DMX&#41;</span></span>](/sql/dmx/export-dmx)  
  
-   [<span data-ttu-id="1be60-135">IMPORT&#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="1be60-135">IMPORT &#40;DMX&#41;</span></span>](/sql/dmx/import-dmx)  
  
 <span data-ttu-id="1be60-136">INCLUDE DEPENDENCIES 옵션을 지정하면 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 는 필요한 모든 데이터 원본 뷰 정의도 내보내며, 사용자가 모델 또는 구조를 가져올 때 대상 서버에서 데이터 원본 뷰를 다시 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="1be60-136">If you specify the INCLUDE DEPENDENCIES option, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] will also export the definition of any required data source views, and when you import the model or structure, it will re-create the data source view on the target server.</span></span> <span data-ttu-id="1be60-137">모델 가져오기를 마친 후에는 개체에 대해 필요한 마이닝 사용 권한을 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1be60-137">After you have finished importing the model, make sure to set the necessary mining permissions on the object.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1be60-138">OLAP 모델은 DMX를 사용하여 내보내고 가져올 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1be60-138">You cannot export and import OLAP models by using DMX.</span></span> <span data-ttu-id="1be60-139">마이닝 모델이 OLAP 큐브를 기반으로 하는 경우 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 에서 제공하는 기능을 사용하여 전체 데이터베이스를 백업한 다음 복원하거나 큐브와 해당 모델을 다시 배포해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1be60-139">If your mining model is based on an OLAP cube, you must use the functionality provided by [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] for backing up and restoring an entire database, or redeploy the cube and its models.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1be60-140">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1be60-140">See Also</span></span>  
 [<span data-ttu-id="1be60-141">데이터 마이닝 솔루션 및 개체 관리</span><span class="sxs-lookup"><span data-stu-id="1be60-141">Management of Data Mining Solutions and Objects</span></span>](management-of-data-mining-solutions-and-objects.md)  
  
  
