---
title: '1 단원: Analysis Services 데이터베이스 준비 (기본 데이터 마이닝 자습서) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 2a796977-6568-4705-9d27-86a9b36658c2
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 07647a940851fbdbdc65357e168747662dc88380
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742716"
---
# <a name="lesson-1-preparing-the-analysis-services-database-basic-data-mining-tutorial"></a><span data-ttu-id="9171b-102">1단원: Analysis Services 데이터베이스 준비(기본 데이터 마이닝 자습서)</span><span class="sxs-lookup"><span data-stu-id="9171b-102">Lesson 1: Preparing the Analysis Services Database (Basic Data Mining Tutorial)</span></span>
  <span data-ttu-id="9171b-103">[!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] 에서 비즈니스 인텔리전스 애플리케이션을 디자인하는 태스크를 수행한 사용자가 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]의 새 직원이라고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="9171b-103">You are a new employee of [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] who has been tasked with designing a business intelligence application in [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].</span></span> [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)]<span data-ttu-id="9171b-104">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]데이터 마이닝 환경을 활용 하 여 자전거를 구매한 사용자에 대 한 흥미롭고 조치 가능한 정보를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9171b-104">hopes to leverage your [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] data mining experience to discover interesting and actionable information about people who have purchased bicycles.</span></span> <span data-ttu-id="9171b-105">그런 다음 앞으로 자전거를 구매할 가능성이 높은 잠재 고객을 예측할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9171b-105">They then want you to predict which prospective customers are most likely to purchase a bicycle in the future.</span></span>  
  
 <span data-ttu-id="9171b-106">에서이 응용 프로그램을 디자인 하는 것 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 은 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 다차원 모델링 및 데이터 마이닝을 위한 프로젝트 템플릿을 기반으로 프로젝트를 만드는 것으로 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="9171b-106">Designing this application in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] starts with the creation in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] of a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project based on the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project template for multidimensional modeling and data mining.</span></span> <span data-ttu-id="9171b-107">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 프로젝트를 만든 후 하나 이상의 데이터 원본을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="9171b-107">After you create an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project, you define one or more data sources.</span></span> <span data-ttu-id="9171b-108">그런 다음 데이터 원본에서 선택한 테이블과 뷰에서 *데이터 원본 뷰*라는 메타데이터 뷰를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="9171b-108">Then, you define a view of the metadata, called a *data source view*, from selected tables and views from the data sources.</span></span>  
  
 <span data-ttu-id="9171b-109">이 단원에서는 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 프로젝트를 만들고 단일 데이터 원본을 정의한 다음 데이터 원본 뷰에 테이블의 하위 집합을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="9171b-109">In this lesson, you will create an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project, define a single data source, and add a subset of tables to a data source view.</span></span> <span data-ttu-id="9171b-110">이 단원에서는 다음 태스크를 다룹니다.</span><span class="sxs-lookup"><span data-stu-id="9171b-110">This lesson includes the following tasks:</span></span>  
  
 [<span data-ttu-id="9171b-111">기본 데이터 마이닝 자습서 &#40;Analysis Services 프로젝트 만들기 자습서&#41;</span><span class="sxs-lookup"><span data-stu-id="9171b-111">Creating an Analysis Services Project &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/creating-an-analysis-services-project-basic-data-mining-tutorial.md)  
  
 [<span data-ttu-id="9171b-112">기본 데이터 마이닝 &#40;데이터 원본 만들기 자습서&#41;</span><span class="sxs-lookup"><span data-stu-id="9171b-112">Creating a Data Source &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/creating-a-data-source-basic-data-mining-tutorial.md)  
  
 [<span data-ttu-id="9171b-113">기본 데이터 마이닝 자습서를 &#40;데이터 원본 뷰 만들기&#41;</span><span class="sxs-lookup"><span data-stu-id="9171b-113">Creating a Data Source View &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/creating-a-data-source-view-basic-data-mining-tutorial.md)  
  
## <a name="first-task-in-lesson"></a><span data-ttu-id="9171b-114">단원의 첫 번째 태스크</span><span class="sxs-lookup"><span data-stu-id="9171b-114">First Task in Lesson</span></span>  
 [<span data-ttu-id="9171b-115">기본 데이터 마이닝 자습서 &#40;Analysis Services 프로젝트 만들기 자습서&#41;</span><span class="sxs-lookup"><span data-stu-id="9171b-115">Creating an Analysis Services Project &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/creating-an-analysis-services-project-basic-data-mining-tutorial.md)  
  
## <a name="next-lesson"></a><span data-ttu-id="9171b-116">다음 단원</span><span class="sxs-lookup"><span data-stu-id="9171b-116">Next Lesson</span></span>  
 [<span data-ttu-id="9171b-117">2 단원: 기본 데이터 마이닝 자습서 &#40;대상 메일링 구조 구축&#41;</span><span class="sxs-lookup"><span data-stu-id="9171b-117">Lesson 2: Building a Targeted Mailing Structure &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-2-building-a-targeted-mailing-structure-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="9171b-118">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9171b-118">See Also</span></span>  
 <span data-ttu-id="9171b-119">[다차원 모델의 데이터 원본 뷰](https://docs.microsoft.com/analysis-services/multidimensional-models/data-source-views-in-multidimensional-models) </span><span class="sxs-lookup"><span data-stu-id="9171b-119">[Data Source Views in Multidimensional Models](https://docs.microsoft.com/analysis-services/multidimensional-models/data-source-views-in-multidimensional-models) </span></span>  
 <span data-ttu-id="9171b-120">[SSAS 다차원&#41;&#40;지원 되는 데이터 원본](https://docs.microsoft.com/analysis-services/multidimensional-models/supported-data-sources-ssas-multidimensional) </span><span class="sxs-lookup"><span data-stu-id="9171b-120">[Data Sources Supported &#40;SSAS Multidimensional&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/supported-data-sources-ssas-multidimensional) </span></span>  
 <span data-ttu-id="9171b-121">[SSDT &#40;Analysis Services 프로젝트 빌드&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/build-analysis-services-projects-ssdt) </span><span class="sxs-lookup"><span data-stu-id="9171b-121">[Build Analysis Services Projects &#40;SSDT&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/build-analysis-services-projects-ssdt) </span></span>  
 [<span data-ttu-id="9171b-122">Analysis Services 프로젝트 만들기</span><span class="sxs-lookup"><span data-stu-id="9171b-122">Creating an Analysis Services Project</span></span>](../analysis-services/lesson-1-1-creating-an-analysis-services-project.md)  
  
  
