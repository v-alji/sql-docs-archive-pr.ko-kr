---
title: Cube 개체 (Analysis Services 다차원 데이터) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- cubes [Analysis Services], objects
ms.assetid: 5cee362e-3f95-4467-bc6c-29b1518ecbf3
author: minewiskan
ms.author: owend
ms.openlocfilehash: 0e6dfb75be696ab26893e668b99dc36c7340f86c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651938"
---
# <a name="cube-objects-analysis-services---multidimensional-data"></a><span data-ttu-id="5be42-102">큐브 개체(Analysis Services - 다차원 데이터)</span><span class="sxs-lookup"><span data-stu-id="5be42-102">Cube Objects (Analysis Services - Multidimensional Data)</span></span>
    
## <a name="introducing-cube-objects"></a><span data-ttu-id="5be42-103">큐브 개체 소개</span><span class="sxs-lookup"><span data-stu-id="5be42-103">Introducing Cube Objects</span></span>  
 <span data-ttu-id="5be42-104">단순 <xref:Microsoft.AnalysisServices.Cube> 개체는 기본 정보, 차원 및 측정값 그룹으로 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5be42-104">A simple <xref:Microsoft.AnalysisServices.Cube> object is composed of: basic information, dimensions, and measure groups.</span></span> <span data-ttu-id="5be42-105">기본 정보에는 큐브의 이름, 큐브의 기본 측정값, 데이터 원본, 스토리지 모드 등이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="5be42-105">Basic information includes the name of the cube, the default measure of the cube, the data source, the storage mode, and others.</span></span>  
  
 <span data-ttu-id="5be42-106">Dimensions 컬렉션에는 데이터베이스 차원 컬렉션의 큐브에 사용되는 실제 차원 집합이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5be42-106">The Dimensions collection contains the actual set of dimensions used in the cube from the database dimensions colection.</span></span> <span data-ttu-id="5be42-107">모든 차원은 큐브에서 참조되기 전에 데이터베이스의 차원 컬렉션에 정의되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5be42-107">All dimensions have to be defined in the dimensions collection of the database before being referenced in the cube.</span></span> <span data-ttu-id="5be42-108">전용 차원은에서 사용할 수 없습니다 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="5be42-108">Private dimensions are not available in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="5be42-109">측정값 그룹은 큐브에 있는 측정값의 집합으로,</span><span class="sxs-lookup"><span data-stu-id="5be42-109">Measure groups are sets of measures in the cube.</span></span> <span data-ttu-id="5be42-110">공용 데이터 원본 뷰와 차원의 공통 집합이 있는 측정값의 컬렉션입니다.</span><span class="sxs-lookup"><span data-stu-id="5be42-110">A measure group is a collection of measures that have a common data source view and a common set of dimensions.</span></span> <span data-ttu-id="5be42-111">측정값 그룹은 측정값의 처리 단위이므로 개별적으로 처리하고 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5be42-111">A measure group is the unit of process for measures; measure groups can be processed individually and then browsed.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5be42-112">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="5be42-112">In this section</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5be42-113">항목</span><span class="sxs-lookup"><span data-stu-id="5be42-113">Topic</span></span>||  
|[<span data-ttu-id="5be42-114">동작&#40;Analysis Services - 다차원 데이터&#41;</span><span class="sxs-lookup"><span data-stu-id="5be42-114">Actions &#40;Analysis Services - Multidimensional Data&#41;</span></span>](../multidimensional-models/actions-analysis-services-multidimensional-data.md)||  
|[<span data-ttu-id="5be42-115">Aggregations and Aggregation Designs</span><span class="sxs-lookup"><span data-stu-id="5be42-115">Aggregations and Aggregation Designs</span></span>](aggregations-and-aggregation-designs.md)||  
|[<span data-ttu-id="5be42-116">계산</span><span class="sxs-lookup"><span data-stu-id="5be42-116">Calculations</span></span>](calculations.md)||  
|[<span data-ttu-id="5be42-117">큐브 셀 Analysis Services 다차원 데이터를 &#40;&#41;</span><span class="sxs-lookup"><span data-stu-id="5be42-117">Cube Cells &#40;Analysis Services - Multidimensional Data&#41;</span></span>](cube-cells-analysis-services-multidimensional-data.md)||  
|[<span data-ttu-id="5be42-118">큐브 속성</span><span class="sxs-lookup"><span data-stu-id="5be42-118">Cube Properties</span></span>](cube-properties-multidimensional-model-programming.md)||  
|[<span data-ttu-id="5be42-119">큐브 저장소 &#40;Analysis Services 다차원 데이터&#41;</span><span class="sxs-lookup"><span data-stu-id="5be42-119">Cube Storage &#40;Analysis Services - Multidimensional Data&#41;</span></span>](cube-storage-analysis-services-multidimensional-data.md)||  
|[<span data-ttu-id="5be42-120">큐브 번역</span><span class="sxs-lookup"><span data-stu-id="5be42-120">Cube Translations</span></span>](cube-translations.md)||  
|[<span data-ttu-id="5be42-121">차원 관계</span><span class="sxs-lookup"><span data-stu-id="5be42-121">Dimension Relationships</span></span>](dimension-relationships.md)||  
|[<span data-ttu-id="5be42-122">다차원 모델의 KPI&#40;핵심 성과 지표&#41;</span><span class="sxs-lookup"><span data-stu-id="5be42-122">Key Performance Indicators &#40;KPIs&#41; in Multidimensional Models</span></span>](../multidimensional-models/key-performance-indicators-kpis-in-multidimensional-models.md)||  
|[<span data-ttu-id="5be42-123">측정값 및 측정값 그룹</span><span class="sxs-lookup"><span data-stu-id="5be42-123">Measures and Measure Groups</span></span>](../multidimensional-models/measures-and-measure-groups.md)||  
|[<span data-ttu-id="5be42-124">파티션&#40;Analysis Services - 다차원 데이터&#41;</span><span class="sxs-lookup"><span data-stu-id="5be42-124">Partitions &#40;Analysis Services - Multidimensional Data&#41;</span></span>](partitions-analysis-services-multidimensional-data.md)||  
|[<span data-ttu-id="5be42-125">큐브 뷰</span><span class="sxs-lookup"><span data-stu-id="5be42-125">Perspectives</span></span>](perspectives.md)||  
  
  
