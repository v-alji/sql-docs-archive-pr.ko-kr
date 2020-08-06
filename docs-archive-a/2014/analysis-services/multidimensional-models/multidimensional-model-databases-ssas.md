---
title: 다차원 모델 데이터베이스 (SSAS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Management Studio [Analysis Services], databases
- SQL Server Analysis Services, databases
- SSAS, databases
- Analysis Services, databases
- databases [Analysis Services], designing
- Business Intelligence Development Studio, databases [Analysis Services]
- databases [Analysis Services]
ms.assetid: 78b2f22a-b7bd-4a2b-b6fc-0bff4d2b3168
author: minewiskan
ms.author: owend
ms.openlocfilehash: 8dc4e7c872f87244e8353c80bd9acfcce584c167
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651922"
---
# <a name="multidimensional-model-databases-ssas"></a><span data-ttu-id="37e7a-102">다차원 model 데이터베이스(SSAS)</span><span class="sxs-lookup"><span data-stu-id="37e7a-102">Multidimensional Model Databases (SSAS)</span></span>
  <span data-ttu-id="37e7a-103">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 데이터베이스는 데이터 원본, 데이터 원본 뷰, 큐브, 차원 및 역할의 모음입니다.</span><span class="sxs-lookup"><span data-stu-id="37e7a-103">An [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database is a collection of data sources, data source views, cubes, dimensions, and roles.</span></span> <span data-ttu-id="37e7a-104">필요에 따라 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 데이터베이스에는 데이터 마이닝 구조 및 데이터베이스에 사용자 정의 기능을 추가하기 위한 방법을 제공하는 사용자 지정 어셈블리가 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="37e7a-104">Optionally, an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database can include structures for data mining, and custom assemblies that provide a way for you to add user-defined functions to the database.</span></span>  
  
 <span data-ttu-id="37e7a-105">큐브는 Analysis Services의 기본 쿼리 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="37e7a-105">Cubes are the fundamental query objects in Analysis Services.</span></span> <span data-ttu-id="37e7a-106">클라이언트 애플리케이션을 통해 Analysis Services 데이터베이스에 연결하면 해당 데이터베이스 내의 큐브에 연결됩니다.</span><span class="sxs-lookup"><span data-stu-id="37e7a-106">When you connect to an Analysis Services database via a client application, you connect to a cube within that database.</span></span> <span data-ttu-id="37e7a-107">차원, 어셈블리, 역할 또는 마이닝 구조를 여러 컨텍스트에서 다시 사용할 경우 데이터베이스에 여러 개의 큐브가 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="37e7a-107">A database might contain multiple cubes if you are reusing dimensions, assemblies, roles, or mining structures across multiple contexts.</span></span>  
  
 <span data-ttu-id="37e7a-108">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 데이터베이스를 프로그래밍 방식으로 또는 다음 대화형 방법 중 하나를 사용하여 만들고 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="37e7a-108">You can create and modify a [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database programmatically or by using one of these interactive methods:</span></span>  
  
-   <span data-ttu-id="37e7a-109">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 에서 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 의 지정된 인스턴스로 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]프로젝트를 배포합니다.</span><span class="sxs-lookup"><span data-stu-id="37e7a-109">Deploy an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project from [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] to a designated instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="37e7a-110">이 프로세스에서는 해당 이름을 가진 데이터베이스가 해당 인스턴스 내에 없을 경우 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 데이터베이스를 만들고 새로 만든 데이터베이스 내의 디자인된 개체를 인스턴스화합니다.</span><span class="sxs-lookup"><span data-stu-id="37e7a-110">This process creates an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database, if a database with that name does not already exist within that instance, and instantiates the designed objects within the newly created database.</span></span> <span data-ttu-id="37e7a-111">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 에서 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]데이터베이스 작업을 수행하면 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스에 프로젝트를 배포한 경우에만 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 프로젝트의 개체 변경 내용이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="37e7a-111">When working with an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], changes made to objects in the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project take effect only when the project is deployed to an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance.</span></span>  
  
-   <span data-ttu-id="37e7a-112">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 또는 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]를 사용하여 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 인스턴스 내에 빈 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]데이터베이스를 만든 다음 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 를 사용하여 해당 데이터베이스에 직접 연결하고 프로젝트가 아닌 데이터베이스 내에 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="37e7a-112">Create an empty [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database within an instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], by using either [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], and then connect directly to that database using [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] and create objects within it (rather than within a project).</span></span> <span data-ttu-id="37e7a-113">이런 방식으로 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 데이터베이스 작업을 수행하면 변경된 개체를 저장할 때 연결되어 있는 데이터베이스에 개체 변경 내용이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="37e7a-113">When working with an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database in this manner, changes made to objects take effect in the database to which you are connecting when the changed object is saved.</span></span>  
  
 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] <span data-ttu-id="37e7a-114">는 원본 제어 소프트웨어와 통합하여 여러 개발자가 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 프로젝트 내의 여러 개체 작업을 동시에 수행하는 것을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="37e7a-114">uses integration with source control software to support multiple developers working with different objects within an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project at the same time.</span></span> <span data-ttu-id="37e7a-115">개발자는 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 프로젝트를 통하지 않고 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 데이터베이스와 직접 상호 작용할 수도 있지만 이 경우 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 데이터베이스의 개체가 데이터베이스 배포에 사용된 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 프로젝트와 동기화되지 않을 위험이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="37e7a-115">A developer can also interact with an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database directly, rather than through an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project, but the risk of this is that the objects in an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database can become out of sync with the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project that was used for its deployment.</span></span> <span data-ttu-id="37e7a-116">배포 후에는 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 를 사용하여 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]데이터베이스를 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="37e7a-116">After deployment, you administer an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="37e7a-117">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 를 사용하여 파티션 및 역할과 같은 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]데이터베이스에 특정 변경이 수행될 수 있고 이로 인해 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 데이터베이스의 개체가 데이터베이스 배포에 사용된 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 프로젝트와 동기화되지 않을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="37e7a-117">Certain changes can also be made to an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], such as to partitions and roles, which can also cause the objects in an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database to become out of sync with the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project that was used for its deployment.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="37e7a-118">관련 작업</span><span class="sxs-lookup"><span data-stu-id="37e7a-118">Related Tasks</span></span>  
 [<span data-ttu-id="37e7a-119">Analysis Services 데이터베이스 연결 및 분리</span><span class="sxs-lookup"><span data-stu-id="37e7a-119">Attach and Detach Analysis Services Databases</span></span>](attach-and-detach-analysis-services-databases.md)  
  
 [<span data-ttu-id="37e7a-120">Analysis Services 데이터베이스 백업 및 복원</span><span class="sxs-lookup"><span data-stu-id="37e7a-120">Backup and Restore of Analysis Services Databases</span></span>](backup-and-restore-of-analysis-services-databases.md)  
  
 [<span data-ttu-id="37e7a-121">Analysis Services 데이터베이스 문서화 및 스크립트</span><span class="sxs-lookup"><span data-stu-id="37e7a-121">Document and Script an Analysis Services Database</span></span>](document-and-script-an-analysis-services-database.md)  
  
 [<span data-ttu-id="37e7a-122">Analysis Services 데이터베이스 수정 또는 삭제</span><span class="sxs-lookup"><span data-stu-id="37e7a-122">Modify or Delete an Analysis Services Database</span></span>](modify-or-delete-an-analysis-services-database.md)  
  
 [<span data-ttu-id="37e7a-123">Analysis Services 데이터베이스 이동</span><span class="sxs-lookup"><span data-stu-id="37e7a-123">Move an Analysis Services Database</span></span>](move-an-analysis-services-database.md)  
  
 [<span data-ttu-id="37e7a-124">다차원 데이터베이스 이름 바꾸기&#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="37e7a-124">Rename a Multidimensional Database &#40;Analysis Services&#41;</span></span>](rename-a-multidimensional-database-analysis-services.md)  
  
 [<span data-ttu-id="37e7a-125">다차원 데이터베이스 &#40;Analysis Services의 호환성 수준을 설정&#41;</span><span class="sxs-lookup"><span data-stu-id="37e7a-125">Set the Compatibility Level of a Multidimensional Database &#40;Analysis Services&#41;</span></span>](compatibility-level-of-a-multidimensional-database-analysis-services.md)  
  
 [<span data-ttu-id="37e7a-126">다차원 데이터베이스 속성 설정&#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="37e7a-126">Set Multidimensional Database Properties &#40;Analysis Services&#41;</span></span>](set-multidimensional-database-properties-analysis-services.md)  
  
 [<span data-ttu-id="37e7a-127">Analysis Services 데이터베이스 동기화</span><span class="sxs-lookup"><span data-stu-id="37e7a-127">Synchronize Analysis Services Databases</span></span>](synchronize-analysis-services-databases.md)  
  
 [<span data-ttu-id="37e7a-128">ReadOnly 모드와 ReadWrite 모드 간 Analysis Services 데이터베이스 전환</span><span class="sxs-lookup"><span data-stu-id="37e7a-128">Switch an Analysis Services database between ReadOnly and ReadWrite modes</span></span>](switch-an-analysis-services-database-between-readonly-and-readwrite-modes.md)  
  
## <a name="see-also"></a><span data-ttu-id="37e7a-129">참고 항목</span><span class="sxs-lookup"><span data-stu-id="37e7a-129">See Also</span></span>  
 <span data-ttu-id="37e7a-130">[온라인 모드에서 Analysis Services 데이터베이스에 연결](connect-in-online-mode-to-an-analysis-services-database.md) </span><span class="sxs-lookup"><span data-stu-id="37e7a-130">[Connect in Online Mode to an Analysis Services Database](connect-in-online-mode-to-an-analysis-services-database.md) </span></span>  
 <span data-ttu-id="37e7a-131">[SSDT&#41;&#40;Analysis Services 프로젝트 만들기](create-an-analysis-services-project-ssdt.md) </span><span class="sxs-lookup"><span data-stu-id="37e7a-131">[Create an Analysis Services Project &#40;SSDT&#41;](create-an-analysis-services-project-ssdt.md) </span></span>  
 [<span data-ttu-id="37e7a-132">MDX를 사용하여 다차원 데이터 쿼리</span><span class="sxs-lookup"><span data-stu-id="37e7a-132">Querying Multidimensional Data with MDX</span></span>](mdx/querying-multidimensional-data-with-mdx.md)  
  
  
