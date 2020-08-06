---
title: '2 단원: 큐브 정의 및 배포 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: bb62e3c9-462f-4ad2-ac8e-92e2f9e9cc28
author: minewiskan
ms.author: owend
ms.openlocfilehash: a2c043920ac646ec4da9eaa2aace4bf6f48e694c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653637"
---
# <a name="lesson-2-defining-and-deploying-a-cube"></a><span data-ttu-id="71761-102">2단원: 큐브 정의 및 배포</span><span class="sxs-lookup"><span data-stu-id="71761-102">Lesson 2: Defining and Deploying a Cube</span></span>
  <span data-ttu-id="71761-103">프로젝트에서 데이터 원본 뷰를 정의 하면 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 초기 큐브를 정의할 준비가 된 것 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 입니다.</span><span class="sxs-lookup"><span data-stu-id="71761-103">After you define a data source view in your [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project, you are ready to define an initial [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] cube.</span></span>  
  
 <span data-ttu-id="71761-104">큐브 마법사를 사용하여 단일 패스에서 큐브와 차원을 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="71761-104">You can define a cube and its dimensions in a single pass using the Cube Wizard.</span></span> <span data-ttu-id="71761-105">또는 하나 이상의 차원을 정의한 다음 큐브 마법사를 사용하여 이러한 차원을 사용하는 큐브를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="71761-105">Alternatively, you can define one or more dimensions and then use the Cube Wizard to define a cube that uses those dimensions.</span></span> <span data-ttu-id="71761-106">복잡한 솔루션을 디자인하는 경우 일반적으로 차원을 정의하는 작업부터 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="71761-106">If you are designing a complex solution, you generally start by defining the dimensions.</span></span> <span data-ttu-id="71761-107">자세한 내용은 [다차원 모델의 차원](multidimensional-models/dimensions-in-multidimensional-models.md) 또는 [다차원 모델의 큐브](multidimensional-models/cubes-in-multidimensional-models.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="71761-107">For more information, see [Dimensions in Multidimensional Models](multidimensional-models/dimensions-in-multidimensional-models.md) or [Cubes in Multidimensional Models](multidimensional-models/cubes-in-multidimensional-models.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="71761-108">이 자습서의 모든 단원에 대한 완료된 프로젝트를 온라인으로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="71761-108">Completed projects for all of the lessons in this tutorial are available online.</span></span> <span data-ttu-id="71761-109">이전 단원에서 완료된 프로젝트를 시작 지점으로 사용하여 어떠한 단원으로든 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="71761-109">You can jump ahead to any lesson by using the completed project from the previous lesson as a starting point.</span></span> <span data-ttu-id="71761-110">이 자습서와 함께 제공되는 샘플 프로젝트를 다운로드하려면[여기를 클릭](https://go.microsoft.com/fwlink/?LinkID=221866) 하십시오.</span><span class="sxs-lookup"><span data-stu-id="71761-110">[Click here](https://go.microsoft.com/fwlink/?LinkID=221866) to download the sample projects that go with this tutorial.</span></span>  
  
 <span data-ttu-id="71761-111">이 단원에서는 다음 태스크를 다룹니다.</span><span class="sxs-lookup"><span data-stu-id="71761-111">This lesson contains the following tasks:</span></span>  
  
 [<span data-ttu-id="71761-112">차원 정의</span><span class="sxs-lookup"><span data-stu-id="71761-112">Defining a Dimension</span></span>](lesson-2-1-defining-a-dimension.md)  
 <span data-ttu-id="71761-113">이 태스크에서는 차원 마법사를 사용하여 차원을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="71761-113">In this task, you use the Dimension Wizard to define a dimension.</span></span>  
  
 [<span data-ttu-id="71761-114">큐브 정의</span><span class="sxs-lookup"><span data-stu-id="71761-114">Defining a Cube</span></span>](lesson-2-2-defining-a-cube.md)  
 <span data-ttu-id="71761-115">이 태스크에서는 큐브 마법사를 초기 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 큐브를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="71761-115">In this task, you use the Cube Wizard to define an initial [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] cube.</span></span>  
  
 [<span data-ttu-id="71761-116">차원에 특성 추가</span><span class="sxs-lookup"><span data-stu-id="71761-116">Adding Attributes to Dimensions</span></span>](lesson-2-3-adding-attributes-to-dimensions.md)  
 <span data-ttu-id="71761-117">이 태스크에서는 만든 차원에 특성을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="71761-117">In this task, you add attributes to the dimensions that you created.</span></span>  
  
 [<span data-ttu-id="71761-118">큐브 및 차원 속성 검토</span><span class="sxs-lookup"><span data-stu-id="71761-118">Reviewing Cube and Dimension Properties</span></span>](lesson-2-4-reviewing-cube-and-dimension-properties.md)  
 <span data-ttu-id="71761-119">이 태스크에서는 정의한 큐브의 구조를 큐브 마법사를 사용하여 검토합니다.</span><span class="sxs-lookup"><span data-stu-id="71761-119">In this task, you review the structure of the cube that you defined by using the Cube Wizard.</span></span>  
  
 [<span data-ttu-id="71761-120">Analysis Services 프로젝트 배포</span><span class="sxs-lookup"><span data-stu-id="71761-120">Deploying an Analysis Services Project</span></span>](lesson-2-5-deploying-an-analysis-services-project.md)  
 <span data-ttu-id="71761-121">이 태스크에서는 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 의 로컬 인스턴스로 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]프로젝트를 배포하고 특정 배포 속성에 대해 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="71761-121">In this task, you deploy the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project to your local instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], and learn about certain deployment properties.</span></span>  
  
 [<span data-ttu-id="71761-122">큐브 찾아보기</span><span class="sxs-lookup"><span data-stu-id="71761-122">Browsing the Cube</span></span>](lesson-2-6-browsing-the-cube.md)  
 <span data-ttu-id="71761-123">이 태스크에서는 Excel 또는 MDX 쿼리 디자이너를 사용하여 큐브와 차원 데이터를 찾아봅니다.</span><span class="sxs-lookup"><span data-stu-id="71761-123">In this task, you browse the cube and dimension data by using Excel or the MDX query designer.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="71761-124">다음 단원</span><span class="sxs-lookup"><span data-stu-id="71761-124">Next Lesson</span></span>  
 [<span data-ttu-id="71761-125">3단원: 측정값, 특성 및 계층 수정</span><span class="sxs-lookup"><span data-stu-id="71761-125">Lesson 3: Modifying Measures, Attributes and Hierarchies</span></span>](lesson-3-modifying-measures-attributes-and-hierarchies.md)  
  
## <a name="see-also"></a><span data-ttu-id="71761-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="71761-126">See Also</span></span>  
 <span data-ttu-id="71761-127">[Analysis Services 자습서 시나리오](analysis-services-tutorial-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="71761-127">[Analysis Services Tutorial Scenario](analysis-services-tutorial-scenario.md) </span></span>  
 <span data-ttu-id="71761-128">[&#40;의 다차원 모델링은 놀이 Works 자습서&#41;](multidimensional-modeling-adventure-works-tutorial.md) </span><span class="sxs-lookup"><span data-stu-id="71761-128">[Multidimensional Modeling &#40;Adventure Works Tutorial&#41;](multidimensional-modeling-adventure-works-tutorial.md) </span></span>  
 <span data-ttu-id="71761-129">[다차원 모델의 차원](multidimensional-models/dimensions-in-multidimensional-models.md) </span><span class="sxs-lookup"><span data-stu-id="71761-129">[Dimensions in Multidimensional Models](multidimensional-models/dimensions-in-multidimensional-models.md) </span></span>  
 <span data-ttu-id="71761-130">[다차원 모델의 큐브](multidimensional-models/cubes-in-multidimensional-models.md) </span><span class="sxs-lookup"><span data-stu-id="71761-130">[Cubes in Multidimensional Models](multidimensional-models/cubes-in-multidimensional-models.md) </span></span>  
 <span data-ttu-id="71761-131">[SSDT&#41;&#40;Analysis Services 프로젝트 속성 구성](multidimensional-models/configure-analysis-services-project-properties-ssdt.md) </span><span class="sxs-lookup"><span data-stu-id="71761-131">[Configure Analysis Services Project Properties &#40;SSDT&#41;](multidimensional-models/configure-analysis-services-project-properties-ssdt.md) </span></span>  
 <span data-ttu-id="71761-132">[SSDT &#40;Analysis Services 프로젝트 빌드&#41;](multidimensional-models/build-analysis-services-projects-ssdt.md) </span><span class="sxs-lookup"><span data-stu-id="71761-132">[Build Analysis Services Projects &#40;SSDT&#41;](multidimensional-models/build-analysis-services-projects-ssdt.md) </span></span>  
 [<span data-ttu-id="71761-133">Analysis Services 프로젝트 배포&#40;SSDT&#41;</span><span class="sxs-lookup"><span data-stu-id="71761-133">Deploy Analysis Services Projects &#40;SSDT&#41;</span></span>](multidimensional-models/deploy-analysis-services-projects-ssdt.md)  
  
  
