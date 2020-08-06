---
title: 다차원 모델링 (어드벤처 Works 자습서) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- tutorials [Analysis Services]
- Analysis Services, tutorials
ms.assetid: db55e226-601a-4026-8651-573195555a59
author: minewiskan
ms.author: owend
ms.openlocfilehash: cd2e8f856d36cab045e6cbc4d34f7cfeffac3c3c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653029"
---
# <a name="multidimensional-modeling-adventure-works-tutorial"></a><span data-ttu-id="d684a-102">다차원 모델링(Adventure Works 자습서)</span><span class="sxs-lookup"><span data-stu-id="d684a-102">Multidimensional Modeling (Adventure Works Tutorial)</span></span>
  <span data-ttu-id="d684a-103">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 자습서입니다.</span><span class="sxs-lookup"><span data-stu-id="d684a-103">Welcome to the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial.</span></span> <span data-ttu-id="d684a-104">이 자습서의 모든 예에서는 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] 를 사용하여 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 라는 가상 회사에서 [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] 프로젝트를 개발 및 배포하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="d684a-104">This tutorial describes how to use [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] to develop and deploy an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project, using the fictitious company [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] for all examples.</span></span>  
  
## <a name="what-you-will-learn"></a><span data-ttu-id="d684a-105">학습 내용</span><span class="sxs-lookup"><span data-stu-id="d684a-105">What You Will Learn</span></span>  
 <span data-ttu-id="d684a-106">이 자습서에서는 다음 항목을 배웁니다.</span><span class="sxs-lookup"><span data-stu-id="d684a-106">In this tutorial, you will learn the following:</span></span>  
  
-   <span data-ttu-id="d684a-107">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 내의 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]프로젝트에서 데이터 원본, 데이터 원본 뷰, 차원, 특성, 특성 관계, 계층 및 큐브를 정의하는 방법</span><span class="sxs-lookup"><span data-stu-id="d684a-107">How to define data sources, data source views, dimensions, attributes, attribute relationships, hierarchies, and cubes in an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project within [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)].</span></span>  
  
-   <span data-ttu-id="d684a-108">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 프로젝트를 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]인스턴스에 배포하여 큐브 및 차원 데이터를 보는 방법과 배포된 개체를 처리하여 기본 데이터 원본의 데이터로 채우는 방법</span><span class="sxs-lookup"><span data-stu-id="d684a-108">How to view cube and dimension data by deploying the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project to an instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], and how to then process the deployed objects to populate them with data from the underlying data source.</span></span>  
  
-   <span data-ttu-id="d684a-109">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 프로젝트에서 측정값, 차원, 계층, 특성 및 측정값 그룹을 수정하는 방법과 개발 서버에서 배포된 큐브에 증분 변경을 배포하는 방법</span><span class="sxs-lookup"><span data-stu-id="d684a-109">How to modify the measures, dimensions, hierarchies, attributes, and measure groups in the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project, and how to then deploy the incremental changes to the deployed cube on the development server.</span></span>  
  
-   <span data-ttu-id="d684a-110">큐브 내에서 계산, KPI(핵심 성과 지표), 동작, 큐브 뷰, 번역 및 보안 역할을 정의하는 방법</span><span class="sxs-lookup"><span data-stu-id="d684a-110">How to define calculations, Key Performance Indicators (KPIs), actions, perspectives, translations, and security roles within a cube.</span></span>  
  
 <span data-ttu-id="d684a-111">이 단원에 대한 컨텍스트를 더 잘 이해할 수 있도록 이 자습서와 함께 시나리오 설명이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="d684a-111">A scenario description accompanies this tutorial so that you can better understand the context for these lessons.</span></span> <span data-ttu-id="d684a-112">자세한 내용은 [Analysis Services Tutorial Scenario](analysis-services-tutorial-scenario.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d684a-112">For more information, see [Analysis Services Tutorial Scenario](analysis-services-tutorial-scenario.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="d684a-113">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="d684a-113">Prerequisites</span></span>  
 <span data-ttu-id="d684a-114">이 자습서의 모든 단원을 완료하려면 예제 데이터, 예제 프로젝트 파일 및 소프트웨어가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d684a-114">You will need sample data, sample project files, and software to complete all of the lessons in this tutorial.</span></span> <span data-ttu-id="d684a-115">이 자습서의 필수 구성 요소를 찾아서 설치하는 방법은 [Install Sample Data and Projects for the Analysis Services Multidimensional Modeling Tutorial](install-sample-data-and-projects.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="d684a-115">For instructions on how to find and install the prerequisites for this tutorial, see [Install Sample Data and Projects for the Analysis Services Multidimensional Modeling Tutorial](install-sample-data-and-projects.md).</span></span>  
  
 <span data-ttu-id="d684a-116">이 자습서를 성공적으로 완료하려면 이 외에도 다음과 같은 사용 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d684a-116">Additionally, the following permissions must be in place to successfully complete this tutorial:</span></span>  
  
-   <span data-ttu-id="d684a-117">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 컴퓨터에서 Administrators 로컬 그룹의 멤버이거나 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]인스턴스에서 서버 관리 역할의 멤버여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d684a-117">You must be a member of the Administrators local group on the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] computer or be a member of the server administration role in the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="d684a-118">**AdventureWorksDW2012** 예제 데이터베이스에 대한 읽기 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d684a-118">You must have Read permissions in the **AdventureWorksDW2012** sample database.</span></span> <span data-ttu-id="d684a-119">이 예제 데이터베이스는 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] 릴리스에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d684a-119">This sample database is valid for the [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] release.</span></span>  
  
## <a name="lessons"></a><span data-ttu-id="d684a-120">단원</span><span class="sxs-lookup"><span data-stu-id="d684a-120">Lessons</span></span>  
 <span data-ttu-id="d684a-121">이 자습서에는 다음 단원이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d684a-121">This tutorial includes the following lessons.</span></span>  
  
|<span data-ttu-id="d684a-122">단원</span><span class="sxs-lookup"><span data-stu-id="d684a-122">Lesson</span></span>|<span data-ttu-id="d684a-123">예상 완료 시간</span><span class="sxs-lookup"><span data-stu-id="d684a-123">Estimated time to complete</span></span>|  
|------------|--------------------------------|  
|[<span data-ttu-id="d684a-124">1단원: Analysis Services 프로젝트 내의 데이터 원본 뷰 정의</span><span class="sxs-lookup"><span data-stu-id="d684a-124">Lesson 1: Defining a Data Source View within an Analysis Services Project</span></span>](lesson-1-defining-a-data-source-view-within-an-analysis-services-project.md)|<span data-ttu-id="d684a-125">15분</span><span class="sxs-lookup"><span data-stu-id="d684a-125">15 minutes</span></span>|  
|[<span data-ttu-id="d684a-126">2단원: 큐브 정의 및 배포</span><span class="sxs-lookup"><span data-stu-id="d684a-126">Lesson 2: Defining and Deploying a Cube</span></span>](lesson-2-defining-and-deploying-a-cube.md)|<span data-ttu-id="d684a-127">30분</span><span class="sxs-lookup"><span data-stu-id="d684a-127">30 minutes</span></span>|  
|[<span data-ttu-id="d684a-128">3단원: 측정값, 특성 및 계층 수정</span><span class="sxs-lookup"><span data-stu-id="d684a-128">Lesson 3: Modifying Measures, Attributes and Hierarchies</span></span>](lesson-3-modifying-measures-attributes-and-hierarchies.md)|<span data-ttu-id="d684a-129">45분</span><span class="sxs-lookup"><span data-stu-id="d684a-129">45 minutes</span></span>|  
|[<span data-ttu-id="d684a-130">4단원: 고급 특성 및 차원 속성 정의</span><span class="sxs-lookup"><span data-stu-id="d684a-130">Lesson 4: Defining Advanced Attribute and Dimension Properties</span></span>](lesson-4-defining-advanced-attribute-and-dimension-properties.md)|<span data-ttu-id="d684a-131">120분</span><span class="sxs-lookup"><span data-stu-id="d684a-131">120 minutes</span></span>|  
|[<span data-ttu-id="d684a-132">5단원: 차원과 측정값 그룹의 관계 정의</span><span class="sxs-lookup"><span data-stu-id="d684a-132">Lesson 5: Defining Relationships Between Dimensions and Measure Groups</span></span>](lesson-5-defining-relationships-between-dimensions-and-measure-groups.md)|<span data-ttu-id="d684a-133">45분</span><span class="sxs-lookup"><span data-stu-id="d684a-133">45 minutes</span></span>|  
|[<span data-ttu-id="d684a-134">6단원: 계산 정의</span><span class="sxs-lookup"><span data-stu-id="d684a-134">Lesson 6: Defining Calculations</span></span>](lesson-6-defining-calculations.md)|<span data-ttu-id="d684a-135">45분</span><span class="sxs-lookup"><span data-stu-id="d684a-135">45 minutes</span></span>|  
|[<span data-ttu-id="d684a-136">7단원: KPI&#40;핵심 성과 지표&#41; 정의</span><span class="sxs-lookup"><span data-stu-id="d684a-136">Lesson 7: Defining Key Performance Indicators &#40;KPIs&#41;</span></span>](lesson-7-defining-key-performance-indicators-kpis.md)|<span data-ttu-id="d684a-137">30분</span><span class="sxs-lookup"><span data-stu-id="d684a-137">30 minutes</span></span>|  
|[<span data-ttu-id="d684a-138">8단원: 작업 정의</span><span class="sxs-lookup"><span data-stu-id="d684a-138">Lesson 8: Defining Actions</span></span>](lesson-8-defining-actions.md)|<span data-ttu-id="d684a-139">30분</span><span class="sxs-lookup"><span data-stu-id="d684a-139">30 minutes</span></span>|  
|[<span data-ttu-id="d684a-140">9단원: 큐브 뷰 및 번역 정의</span><span class="sxs-lookup"><span data-stu-id="d684a-140">Lesson 9: Defining Perspectives and Translations</span></span>](lesson-9-defining-perspectives-and-translations.md)|<span data-ttu-id="d684a-141">30분</span><span class="sxs-lookup"><span data-stu-id="d684a-141">30 minutes</span></span>|  
|[<span data-ttu-id="d684a-142">10단원: 관리자 역할 정의</span><span class="sxs-lookup"><span data-stu-id="d684a-142">Lesson 10: Defining Administrative Roles</span></span>](lesson-10-defining-administrative-roles.md)|<span data-ttu-id="d684a-143">15분</span><span class="sxs-lookup"><span data-stu-id="d684a-143">15 minutes</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="d684a-144">이 자습서에서 만들 큐브 데이터베이스는 codeplex 사이트에서 다운로드할 수 있는 Adventure Works 예제 데이터베이스의 일부인 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 다차원 모델 프로젝트의 단순화된 버전입니다.</span><span class="sxs-lookup"><span data-stu-id="d684a-144">The cube database that you will create in this tutorial is a simplified version of the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] multidimensional model project that is part of the Adventure Works sample databases available for download on the codeplex site.</span></span> <span data-ttu-id="d684a-145">놀이 Works 다차원 데이터베이스의 자습서 버전은 바로 개선 하고자 하는 특정 기술에 더 집중 하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d684a-145">The tutorial version of the Adventure Works multidimensional database is simplified to bring greater focus to the specific skills that you will want to improve right away.</span></span> <span data-ttu-id="d684a-146">이 자습서를 끝낸 후에는 직접 다차원 모델 프로젝트를 탐색하여 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 다차원 모델링에 대한 이해를 높이는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="d684a-146">After you complete the tutorial, consider exploring the multidimensional model project on your own to further your understanding of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] multidimensional modeling.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="d684a-147">다음 단계</span><span class="sxs-lookup"><span data-stu-id="d684a-147">Next Step</span></span>  
 <span data-ttu-id="d684a-148">자습서를 시작하려면 첫 번째 단원인 [Lesson 1: Defining a Data Source View within an Analysis Services Project](lesson-1-defining-a-data-source-view-within-an-analysis-services-project.md)로 이동하십시오.</span><span class="sxs-lookup"><span data-stu-id="d684a-148">To begin the tutorial, continue to the first lesson: [Lesson 1: Defining a Data Source View within an Analysis Services Project](lesson-1-defining-a-data-source-view-within-an-analysis-services-project.md).</span></span>  
  
  
