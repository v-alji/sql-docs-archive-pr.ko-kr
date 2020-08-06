---
title: '1 단원: Analysis Services 프로젝트 내에서 데이터 원본 뷰 정의 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 7d3ffabd-78ae-4204-8323-29949d030c16
author: minewiskan
ms.author: owend
ms.openlocfilehash: 8a3d69225217154e5072d0cd34349a247730ddaf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740587"
---
# <a name="lesson-1-defining-a-data-source-view-within-an-analysis-services-project"></a><span data-ttu-id="cfac8-102">1단원: Analysis Services 프로젝트 내의 데이터 원본 뷰 정의</span><span class="sxs-lookup"><span data-stu-id="cfac8-102">Lesson 1: Defining a Data Source View within an Analysis Services Project</span></span>
  <span data-ttu-id="cfac8-103">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 의 비즈니스 인텔리전스 애플리케이션 디자인은 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 에서 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]프로젝트를 만드는 것부터 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="cfac8-103">Designing a business intelligence application in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] starts with creating an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="cfac8-104">이 프로젝트에서 솔루션의 모든 요소를 정의하고 데이터 원본 뷰를 사용하여 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="cfac8-104">Within this project, you define all the elements of your solution, starting with a data source view.</span></span>  
  
 <span data-ttu-id="cfac8-105">이 단원에서는 다음 태스크를 다룹니다.</span><span class="sxs-lookup"><span data-stu-id="cfac8-105">This lesson contains the following tasks:</span></span>  
  
 [<span data-ttu-id="cfac8-106">Analysis Services 프로젝트 만들기</span><span class="sxs-lookup"><span data-stu-id="cfac8-106">Creating an Analysis Services Project</span></span>](lesson-1-1-creating-an-analysis-services-project.md)  
 <span data-ttu-id="cfac8-107">이 태스크에서는 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 다차원 모델 템플릿을 기반으로 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial 프로젝트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="cfac8-107">In this task, you create the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial project, based on an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] multidimensional model template.</span></span>  
  
 [<span data-ttu-id="cfac8-108">데이터 원본 정의</span><span class="sxs-lookup"><span data-stu-id="cfac8-108">Defining a Data Source</span></span>](lesson-1-2-defining-a-data-source.md)  
 <span data-ttu-id="cfac8-109">이 태스크에서는 **AdventureWorksDW2012** 데이터베이스를 이후 단원에서 정의할 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 차원 및 큐브의 데이터 원본으로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="cfac8-109">In this task, you specify the **AdventureWorksDW2012** database as the data source for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] dimensions and cubes that you will define in subsequent lessons.</span></span>  
  
 [<span data-ttu-id="cfac8-110">데이터 원본 뷰 정의</span><span class="sxs-lookup"><span data-stu-id="cfac8-110">Defining a Data Source View</span></span>](lesson-1-3-defining-a-data-source-view.md)  
 <span data-ttu-id="cfac8-111">이 태스크에서는 **AdventureWorksDW2012** 데이터베이스의 선택한 테이블에서 메타데이터의 단일 통합 뷰를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="cfac8-111">In this task, you define a single unified view of the metadata from selected tables in the **AdventureWorksDW2012** database.</span></span>  
  
 [<span data-ttu-id="cfac8-112">기본 테이블 이름 수정</span><span class="sxs-lookup"><span data-stu-id="cfac8-112">Modifying Default Table Names</span></span>](lesson-1-4-modifying-default-table-names.md)  
 <span data-ttu-id="cfac8-113">이 태스크에서는 이후 정의할 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 개체 이름이 사용자에게 더 친숙하도록 데이터 원본 뷰에서 테이블 이름을 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="cfac8-113">In this task, you modify table names in the data source view, so that the names of subsequent [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] objects that you define will be more user-friendly.</span></span>  
  
 <span data-ttu-id="cfac8-114">이 단원용으로 작성된 샘플 프로젝트 파일과 결과를 비교하십시오.</span><span class="sxs-lookup"><span data-stu-id="cfac8-114">Compare your results against a sample project file that was built for this lesson.</span></span> <span data-ttu-id="cfac8-115">이 자습서와 함께 제공되는 예제 프로젝트를 다운로드하는 방법은 codeplex의 제품 예제 페이지에서 [SQL Server 2012용 SSAS 다차원 모델 프로젝트](https://go.microsoft.com/fwlink/p/?LinkID=221866) 를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="cfac8-115">For more information about downloading the sample projects that go with this tutorial, see [SSAS Multidimensional Model Projects for SQL Server 2012](https://go.microsoft.com/fwlink/p/?LinkID=221866) on the product samples page on codeplex.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="cfac8-116">다음 단원</span><span class="sxs-lookup"><span data-stu-id="cfac8-116">Next Lesson</span></span>  
 [<span data-ttu-id="cfac8-117">2단원: 큐브 정의 및 배포</span><span class="sxs-lookup"><span data-stu-id="cfac8-117">Lesson 2: Defining and Deploying a Cube</span></span>](lesson-2-defining-and-deploying-a-cube.md)  
  
## <a name="see-also"></a><span data-ttu-id="cfac8-118">참고 항목</span><span class="sxs-lookup"><span data-stu-id="cfac8-118">See Also</span></span>  
 <span data-ttu-id="cfac8-119">[SSDT&#41;&#40;Analysis Services 프로젝트 만들기](multidimensional-models/create-an-analysis-services-project-ssdt.md) </span><span class="sxs-lookup"><span data-stu-id="cfac8-119">[Create an Analysis Services Project &#40;SSDT&#41;](multidimensional-models/create-an-analysis-services-project-ssdt.md) </span></span>  
 <span data-ttu-id="cfac8-120">[SSAS 다차원&#41;&#40;지원 되는 데이터 원본](multidimensional-models/supported-data-sources-ssas-multidimensional.md) </span><span class="sxs-lookup"><span data-stu-id="cfac8-120">[Data Sources Supported &#40;SSAS Multidimensional&#41;](multidimensional-models/supported-data-sources-ssas-multidimensional.md) </span></span>  
 <span data-ttu-id="cfac8-121">[다차원 모델의 데이터 원본 뷰](multidimensional-models/data-source-views-in-multidimensional-models.md) </span><span class="sxs-lookup"><span data-stu-id="cfac8-121">[Data Source Views in Multidimensional Models](multidimensional-models/data-source-views-in-multidimensional-models.md) </span></span>  
 <span data-ttu-id="cfac8-122">[Analysis Services 자습서 시나리오](analysis-services-tutorial-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="cfac8-122">[Analysis Services Tutorial Scenario](analysis-services-tutorial-scenario.md) </span></span>  
 [<span data-ttu-id="cfac8-123">다차원 모델링&#40;Adventure Works 자습서&#41;</span><span class="sxs-lookup"><span data-stu-id="cfac8-123">Multidimensional Modeling &#40;Adventure Works Tutorial&#41;</span></span>](multidimensional-modeling-adventure-works-tutorial.md)  
  
  
