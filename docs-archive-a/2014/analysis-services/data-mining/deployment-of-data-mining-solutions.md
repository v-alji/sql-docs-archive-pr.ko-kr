---
title: 데이터 마이닝 솔루션 배포 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining models [Analysis Services], deploying
- deploying [Analysis Services], production environments
- deploying [Analysis Services - data mining]
- solutions [Analysis Services], deploying
- models [Analysis Services], data mining
ms.assetid: d83effc7-437d-42e9-8ac3-b65f79e27043
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5764be2f7530add2fa4cb028b288be69598bb95c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659731"
---
# <a name="deployment-of-data-mining-solutions"></a><span data-ttu-id="36c9d-102">데이터 마이닝 솔루션 배포</span><span class="sxs-lookup"><span data-stu-id="36c9d-102">Deployment of Data Mining Solutions</span></span>
  <span data-ttu-id="36c9d-103">데이터 마이닝 프로세스의 마지막 단계는 모델을 프로덕션 환경에 배포하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="36c9d-103">The last step in the data mining process is to deploy the models to a production environment.</span></span> <span data-ttu-id="36c9d-104">배포 작업을 수행해야 사용자가 모델을 사용하여 다음과 같은 태스크를 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36c9d-104">Deployment is important because it makes the models available to users so that you can perform any of the following tasks:</span></span>  
  
-   <span data-ttu-id="36c9d-105">모델을 사용하여 예측을 만들고 비즈니스 의사 결정을 내릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36c9d-105">Use the models to create predictions and make business decisions.</span></span> <span data-ttu-id="36c9d-106">쿼리를 만드는 데 사용할 수 있는 도구에 대 한 자세한 내용은 [데이터 마이닝 쿼리 인터페이스](data-mining-query-tools.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="36c9d-106">For information about the tools you can use to create queries, see [Data Mining Query Interfaces](data-mining-query-tools.md).</span></span>  
  
-   <span data-ttu-id="36c9d-107">데이터 마이닝 기능을 직접 애플리케이션에 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36c9d-107">Embed data mining functionality directly into an application.</span></span> <span data-ttu-id="36c9d-108">마이닝 구조 및 마이닝 모델을 생성, 변경, 처리 및 삭제하기 위해 애플리케이션에서 사용할 수 있는 개체 집합이 포함된 어셈블리 또는 AMO(Analysis Management Objects)를 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36c9d-108">You can include Analysis Management Objects (AMO) or an assembly that contains a set of objects that your application can use to create, alter, process, and delete mining structures and mining models.</span></span>  
  
-   <span data-ttu-id="36c9d-109">사용자가 예측을 요청하고, 추세를 보고, 모델을 비교하는 데 사용할 수 있는 보고서를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36c9d-109">Create reports that let users request predictions, view trends, or compare models.</span></span>  
  
 <span data-ttu-id="36c9d-110">이 섹션에서는 배포 옵션에 대해 자세히 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="36c9d-110">This section provides detailed information about deployment options.</span></span>  
  
 [<span data-ttu-id="36c9d-111">데이터 마이닝 솔루션 배포 요구 사항</span><span class="sxs-lookup"><span data-stu-id="36c9d-111">Requirements for Deployment of Data Mining Solutions</span></span>](#bkmk_Reqs)  
  
 [<span data-ttu-id="36c9d-112">관계형 솔루션 배포</span><span class="sxs-lookup"><span data-stu-id="36c9d-112">Deploying a Relational Solution</span></span>](#bkmk_RelationalSltn)  
  
 [<span data-ttu-id="36c9d-113">다차원 솔루션 배포</span><span class="sxs-lookup"><span data-stu-id="36c9d-113">Deploying a Multidimensional Solution</span></span>](#bkmk_MDSltn)  
  
 [<span data-ttu-id="36c9d-114">관련 리소스</span><span class="sxs-lookup"><span data-stu-id="36c9d-114">Related Resources</span></span>](#bkmk_Resources)  
  
## <a name="in-this-section"></a><span data-ttu-id="36c9d-115">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="36c9d-115">In This Section</span></span>  
 [<span data-ttu-id="36c9d-116">데이터 마이닝 솔루션을 이전 버전의 SQL Server에 배포</span><span class="sxs-lookup"><span data-stu-id="36c9d-116">Deploy a Data Mining Solution to Previous Versions of SQL Server</span></span>](deploy-a-data-mining-solution-to-previous-versions-of-sql-server.md)  
  
 [<span data-ttu-id="36c9d-117">데이터 마이닝 개체 내보내기 및 가져오기</span><span class="sxs-lookup"><span data-stu-id="36c9d-117">Export and Import Data Mining Objects</span></span>](export-and-import-data-mining-objects.md)  
  
##  <a name="requirements-for-deployment-of-data-mining-solutions"></a><a name="bkmk_Reqs"></a><span data-ttu-id="36c9d-118">데이터 마이닝 솔루션 배포를 위한 요구 사항</span><span class="sxs-lookup"><span data-stu-id="36c9d-118">Requirements for Deployment of Data Mining Solutions</span></span>  
 <span data-ttu-id="36c9d-119">솔루션을 배포하는 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스는 다차원 개체 및 데이터 마이닝 개체를 지원하는 모드에서 실행되고 있어야 합니다. 즉 데이터 마이닝 개체를 테이블 형식 모델 또는 PowerPivot 데이터를 호스팅하는 인스턴스에 배포할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="36c9d-119">The instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] to which you deploy the solution must be running in a mode that supports multidimensional objects and data mining objects; that is, you cannot deploy data mining objects to an instance that hosts tabular models or PowerPivot data.</span></span>  
  
 <span data-ttu-id="36c9d-120">따라서 Visual Studio에서 데이터 마이닝 솔루션을 만드는 경우 반드시 **Analysis Services 다차원 및 데이터 마이닝 프로젝트**템플릿을 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="36c9d-120">Therefore, when you create a data mining solution in Visual Studio, be sure to use the template, **Analysis Services Multidimensional and Data Mining Project**.</span></span>  
  
 <span data-ttu-id="36c9d-121">솔루션을 배포하면 지정된 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스에서 솔루션 파일과 같은 이름의 데이터베이스에 데이터 마이닝에 사용되는 개체가 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="36c9d-121">When you deploy the solution, the objects used for data mining are created in the specified [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance, in a database with the same name as the solution file.</span></span>  
  
###  <a name="deploying-a-relational-solution"></a><a name="bkmk_RelationalSltn"></a><span data-ttu-id="36c9d-122">관계형 솔루션 배포</span><span class="sxs-lookup"><span data-stu-id="36c9d-122">Deploying a Relational Solution</span></span>  
 <span data-ttu-id="36c9d-123">관계형 데이터 마이닝 솔루션을 배포하면 필요한 데이터 마이닝 개체가 새 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 데이터베이스에 만들어지고 해당 개체가 기본적으로 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="36c9d-123">When you deploy a relational data mining solution, the required data mining objects are created within a new [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database, and the objects are processed by default.</span></span> <span data-ttu-id="36c9d-124">구성 속성인 **처리 옵션**을 사용하여 처리 옵션을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36c9d-124">You can change processing options by using the configuration property, **Processing Option**.</span></span> <span data-ttu-id="36c9d-125">자세한 내용은 [Analysis Services 프로젝트 속성 구성&#40;SSDT&#41;](../multidimensional-models/configure-analysis-services-project-properties-ssdt.md)인스턴스에 정의된 개체가 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="36c9d-125">For more information, see [Configure Analysis Services Project Properties &#40;SSDT&#41;](../multidimensional-models/configure-analysis-services-project-properties-ssdt.md).</span></span>  
  
 <span data-ttu-id="36c9d-126">기본적으로 매번 증분 변경 내용만 배포됩니다.</span><span class="sxs-lookup"><span data-stu-id="36c9d-126">By default, only incremental changes are deployed each time.</span></span> <span data-ttu-id="36c9d-127">즉 마이닝 모델을 수정하는 경우 프로젝트를 다시 배포하면 해당 마이닝 모델만 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="36c9d-127">In other words, you can modify a mining model, and when you re-deploy the project, only that mining model would be updated.</span></span> <span data-ttu-id="36c9d-128">하지만 여러 클라이언트가 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 데이터베이스를 편집하고 있으면 이 경우 오류가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36c9d-128">However, if you have multiple clients editing the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database, this can lead to errors.</span></span> <span data-ttu-id="36c9d-129">솔루션을 배포할 때 전체 데이터베이스를 새로 고치도록 기본 배포 모드를 변경하려면 **배포 모드** 속성을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="36c9d-129">To change the default deployment mode so that the entire database is refreshed when you deploy the solution, change the **Deployment Mode** property</span></span>  
  
 <span data-ttu-id="36c9d-130">관계형 데이터 마이닝 솔루션에서 배포해야 하는 개체는 데이터 원본 정의, 사용된 모든 데이터 원본 뷰, 마이닝 구조 및 모든 종속 마이닝 모델 뿐입니다.</span><span class="sxs-lookup"><span data-stu-id="36c9d-130">In a relational data mining solution, the only objects that must be deployed are the data source definition, any data source views that were used, the mining structures, and all dependent mining models.</span></span>  
  
###  <a name="deploying-a-multidimensional-solution"></a><a name="bkmk_MDSltn"></a><span data-ttu-id="36c9d-131">다차원 솔루션 배포</span><span class="sxs-lookup"><span data-stu-id="36c9d-131">Deploying a Multidimensional Solution</span></span>  
 <span data-ttu-id="36c9d-132">다차원 데이터 마이닝 솔루션을 배포하면 원본 큐브와 동일한 데이터베이스 내부에 데이터 마이닝 개체가 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="36c9d-132">When you deploy a multidimensional data mining solution, this solution creates your data mining objects within the same database as the source cube.</span></span>  
  
 <span data-ttu-id="36c9d-133">마이닝 구조 또는 마이닝 모델을 처리할 때 원본 큐브도 처리해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="36c9d-133">When you process the mining structure or mining model, you must process the source cube as well.</span></span> <span data-ttu-id="36c9d-134">따라서 OLAP 마이닝 모델을 사용하는 솔루션을 배포하는 데 걸리는 시간이 관계형 데이터 마이닝 솔루션의 경우보다 더 길 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36c9d-134">For this reason, deploying a solution that uses OLAP mining models can take longer than relational data mining solutions.</span></span>  
  
 <span data-ttu-id="36c9d-135">대개 데이터 마이닝 개체는 큐브에 사용되는 것과 동일한 데이터 원본 및 데이터 원본 뷰를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="36c9d-135">Typically data mining objects also use the same data sources and data source views that are used for the cube.</span></span> <span data-ttu-id="36c9d-136">하지만 데이터 마이닝에 사용하도록 특별히 만든 데이터 원본 및 데이터 원본 뷰를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36c9d-136">However, you can add data sources and data source views that are targeted specifically to data mining.</span></span> <span data-ttu-id="36c9d-137">예를 들어 대개 큐브는 잠재 클라이언트에 대한 데이터 또는 다차원 개체에 사용되지 않은 외부 데이터를 포함하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="36c9d-137">For example, typically a cube would not contain data about prospective clients, or external data not used in the multidimensional objects.</span></span>  
  
##  <a name="related-resources"></a><a name="bkmk_Resources"></a><span data-ttu-id="36c9d-138">관련 리소스</span><span class="sxs-lookup"><span data-stu-id="36c9d-138">Related Resources</span></span>  
 [<span data-ttu-id="36c9d-139">데이터 마이닝 개체 이동</span><span class="sxs-lookup"><span data-stu-id="36c9d-139">Moving Data Mining Objects</span></span>](moving-data-mining-objects.md)  
  
 <span data-ttu-id="36c9d-140">모델이 관계형 데이터만 기반으로 하는 경우 모델을 이동하는 가장 손쉬운 방법은 DMX를 사용하여 개체를 내보내고 가져오는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="36c9d-140">If your model is based on relational data only, exporting and importing objects using DMX is the easiest way to move models.</span></span>  
  
 [<span data-ttu-id="36c9d-141">Analysis Services 데이터베이스 이동</span><span class="sxs-lookup"><span data-stu-id="36c9d-141">Move an Analysis Services Database</span></span>](../multidimensional-models/move-an-analysis-services-database.md)  
  
 <span data-ttu-id="36c9d-142">모델이 큐브를 데이터 원본으로 사용하는 경우 모델과 해당 지원 큐브 데이터를 이동하는 방법을 보려면 다음 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="36c9d-142">When models use a cube as a data source, refer to this topic for more information about how to move models and their supporting cube data.</span></span>  
  
 [<span data-ttu-id="36c9d-143">Analysis Services 프로젝트 배포&#40;SSDT&#41;</span><span class="sxs-lookup"><span data-stu-id="36c9d-143">Deploy Analysis Services Projects &#40;SSDT&#41;</span></span>](../multidimensional-models/deploy-analysis-services-projects-ssdt.md)  
  
 <span data-ttu-id="36c9d-144">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 프로젝트의 배포에 대한 일반적인 정보를 제공하고 프로젝트를 구성할 때 설정할 수 있는 속성에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="36c9d-144">Provides general information about deployment of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] projects, and describes the properties that you can set as part of the project configuration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36c9d-145">참고 항목</span><span class="sxs-lookup"><span data-stu-id="36c9d-145">See Also</span></span>  
 <span data-ttu-id="36c9d-146">[다차원 모델 개체 처리](../multidimensional-models/processing-a-multidimensional-model-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="36c9d-146">[Multidimensional Model Object Processing](../multidimensional-models/processing-a-multidimensional-model-analysis-services.md) </span></span>  
 <span data-ttu-id="36c9d-147">[데이터 마이닝 쿼리 인터페이스](data-mining-query-tools.md) </span><span class="sxs-lookup"><span data-stu-id="36c9d-147">[Data Mining Query Interfaces](data-mining-query-tools.md) </span></span>  
 [<span data-ttu-id="36c9d-148">처리 요구 사항 및 고려 사항&#40;데이터 마이닝&#41;</span><span class="sxs-lookup"><span data-stu-id="36c9d-148">Processing Requirements and Considerations &#40;Data Mining&#41;</span></span>](processing-requirements-and-considerations-data-mining.md)  
  
  
