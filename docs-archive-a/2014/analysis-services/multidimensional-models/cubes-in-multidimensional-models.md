---
title: 다차원 모델의 큐브 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- OLAP objects [Analysis Services], cubes
- cubes [Analysis Services], about cubes
- cubes [Analysis Services]
- OLAP [Analysis Services], cubes
ms.assetid: e0f7acf3-4b07-41fc-a5fc-ac30b4a56c54
author: minewiskan
ms.author: owend
ms.openlocfilehash: 372bb8075b232ff8fbf8a54facf9bc065e6763a3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741419"
---
# <a name="cubes-in-multidimensional-models"></a><span data-ttu-id="32c63-102">다차원 모델의 큐브</span><span class="sxs-lookup"><span data-stu-id="32c63-102">Cubes in Multidimensional Models</span></span>
  <span data-ttu-id="32c63-103">큐브는 분석 목적의 정보를 포함하는 다차원 구조이며, 큐브의 주요 구성 요소는 차원과 측정값입니다.</span><span class="sxs-lookup"><span data-stu-id="32c63-103">A cube is a multidimensional structure that contains information for analytical purposes; the main constituents of a cube are dimensions and measures.</span></span> <span data-ttu-id="32c63-104">차원은 조각화 및 분석에 사용할 큐브의 구조를 정의하고, 측정값은 최종 사용자에게 의미가 있는 집계된 숫자 값을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="32c63-104">Dimensions define the structure of the cube that you use to slice and dice over, and measures provide aggregated numerical values of interest to the end user.</span></span> <span data-ttu-id="32c63-105">논리적 구조인 큐브를 사용하면 클라이언트 애플리케이션에서는 마치 값이 큐브의 셀에 포함되어 있고 가능한 모든 요약된 값에 대해 셀이 정의되어 있는 것처럼 측정값의 값을 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="32c63-105">As a logical structure, a cube allows a client application to retrieve values, of measures, as if they were contained in cells in the cube; cells are defined for every possible summarized value.</span></span> <span data-ttu-id="32c63-106">큐브의 셀은 차원 멤버의 교차에 의해 정의되며 해당 특정 교차 지점에 있는 측정값의 집계된 값을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="32c63-106">A cell, in the cube, is defined by the intersection of dimension members and contains the aggregated values of the measures at that specific intersection.</span></span>  
  
## <a name="benefits-of-using-cubes"></a><span data-ttu-id="32c63-107">큐브 사용의 이점</span><span class="sxs-lookup"><span data-stu-id="32c63-107">Benefits of Using Cubes</span></span>  
 <span data-ttu-id="32c63-108">큐브를 사용하면 분석을 위한 모든 관련 데이터를 한 곳에 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="32c63-108">A cube provides a single place where all related data, for analysis, is stored.</span></span>  
  
## <a name="components-of-cubes"></a><span data-ttu-id="32c63-109">큐브의 구성 요소</span><span class="sxs-lookup"><span data-stu-id="32c63-109">Components of Cubes</span></span>  
 <span data-ttu-id="32c63-110">큐브는 다음 요소로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="32c63-110">A cube is composed of:</span></span>  
  
|<span data-ttu-id="32c63-111">요소</span><span class="sxs-lookup"><span data-stu-id="32c63-111">Element</span></span>|<span data-ttu-id="32c63-112">설명</span><span class="sxs-lookup"><span data-stu-id="32c63-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="32c63-113">차원</span><span class="sxs-lookup"><span data-stu-id="32c63-113">Dimensions</span></span>|[<span data-ttu-id="32c63-114">다차원 모델의 차원</span><span class="sxs-lookup"><span data-stu-id="32c63-114">Dimensions in Multidimensional Models</span></span>](dimensions-in-multidimensional-models.md)|  
|<span data-ttu-id="32c63-115">측정값 및 측정값 그룹</span><span class="sxs-lookup"><span data-stu-id="32c63-115">Measures and Measure Groups</span></span>|[<span data-ttu-id="32c63-116">다차원 모델의 측정값 및 측정값 그룹 만들기</span><span class="sxs-lookup"><span data-stu-id="32c63-116">Create Measures and Measure Groups in Multidimensional Models</span></span>](create-measures-and-measure-groups-in-multidimensional-models.md)|  
|<span data-ttu-id="32c63-117">파티션</span><span class="sxs-lookup"><span data-stu-id="32c63-117">Partitions</span></span>|[<span data-ttu-id="32c63-118">다차원 모델의 파티션</span><span class="sxs-lookup"><span data-stu-id="32c63-118">Partitions in Multidimensional Models</span></span>](partitions-in-multidimensional-models.md)|  
|<span data-ttu-id="32c63-119">큐브 뷰</span><span class="sxs-lookup"><span data-stu-id="32c63-119">Perspectives</span></span>|[<span data-ttu-id="32c63-120">다차원 모델의 큐브 뷰</span><span class="sxs-lookup"><span data-stu-id="32c63-120">Perspectives in Multidimensional Models</span></span>](perspectives-in-multidimensional-models.md)|  
|<span data-ttu-id="32c63-121">계층 구조</span><span class="sxs-lookup"><span data-stu-id="32c63-121">Hierarchies</span></span>|[<span data-ttu-id="32c63-122">사용자 정의 계층 만들기</span><span class="sxs-lookup"><span data-stu-id="32c63-122">Create User-Defined Hierarchies</span></span>](user-defined-hierarchies-create.md)|  
|<span data-ttu-id="32c63-123">작업</span><span class="sxs-lookup"><span data-stu-id="32c63-123">Actions</span></span>|[<span data-ttu-id="32c63-124">다차원 모델의 동작</span><span class="sxs-lookup"><span data-stu-id="32c63-124">Actions in Multidimensional Models</span></span>](actions-in-multidimensional-models.md)|  
|<span data-ttu-id="32c63-125">KPI(핵심 성과 지표)</span><span class="sxs-lookup"><span data-stu-id="32c63-125">Key Performance Indicators (KPI)</span></span>|[<span data-ttu-id="32c63-126">다차원 모델의 KPI&#40;핵심 성과 지표&#41;</span><span class="sxs-lookup"><span data-stu-id="32c63-126">Key Performance Indicators &#40;KPIs&#41; in Multidimensional Models</span></span>](key-performance-indicators-kpis-in-multidimensional-models.md)|  
|<span data-ttu-id="32c63-127">계산</span><span class="sxs-lookup"><span data-stu-id="32c63-127">Calculations</span></span>|[<span data-ttu-id="32c63-128">다차원 모델의 계산</span><span class="sxs-lookup"><span data-stu-id="32c63-128">Calculations in Multidimensional Models</span></span>](calculations-in-multidimensional-models.md)|  
|<span data-ttu-id="32c63-129">Translations</span><span class="sxs-lookup"><span data-stu-id="32c63-129">Translations</span></span>|[<span data-ttu-id="32c63-130">다차원 모델의 번역</span><span class="sxs-lookup"><span data-stu-id="32c63-130">Translations in Multidimensional Models</span></span>](translations-in-multidimensional-models-analysis-services.md)|  
  
## <a name="related-tasks"></a><span data-ttu-id="32c63-131">관련 작업</span><span class="sxs-lookup"><span data-stu-id="32c63-131">Related Tasks</span></span>  
  
|<span data-ttu-id="32c63-132">항목</span><span class="sxs-lookup"><span data-stu-id="32c63-132">Topic</span></span>|<span data-ttu-id="32c63-133">설명</span><span class="sxs-lookup"><span data-stu-id="32c63-133">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="32c63-134">큐브 마법사를 사용하여 큐브 만들기</span><span class="sxs-lookup"><span data-stu-id="32c63-134">Create a Cube Using the Cube Wizard</span></span>](create-a-cube-using-the-cube-wizard.md)|<span data-ttu-id="32c63-135">큐브 마법사를 사용하여 큐브, 차원, 차원 특성 및 사용자 정의 계층을 정의하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="32c63-135">Describes how to use the Cube Wizard to define a cube, dimensions, dimension attributes, and user-defined hierarchies.</span></span>|  
|[<span data-ttu-id="32c63-136">다차원 모델의 측정값 및 측정값 그룹 만들기</span><span class="sxs-lookup"><span data-stu-id="32c63-136">Create Measures and Measure Groups in Multidimensional Models</span></span>](create-measures-and-measure-groups-in-multidimensional-models.md)|<span data-ttu-id="32c63-137">측정값 그룹을 정의하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="32c63-137">Describes how to define measure groups.</span></span>|  
|[<span data-ttu-id="32c63-138">다차원 모델의 계산</span><span class="sxs-lookup"><span data-stu-id="32c63-138">Calculations in Multidimensional Models</span></span>](calculations-in-multidimensional-models.md)|<span data-ttu-id="32c63-139">MDX 스크립트에서 계산을 정의 및 구성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="32c63-139">Describes how to define and configure a calculation in an MDX script.</span></span>|  
|[<span data-ttu-id="32c63-140">다차원 모델의 동작</span><span class="sxs-lookup"><span data-stu-id="32c63-140">Actions in Multidimensional Models</span></span>](actions-in-multidimensional-models.md)|<span data-ttu-id="32c63-141">동작을 정의 및 구성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="32c63-141">Describes how to define and configure an action.</span></span>|  
|[<span data-ttu-id="32c63-142">다차원 모델의 큐브 뷰</span><span class="sxs-lookup"><span data-stu-id="32c63-142">Perspectives in Multidimensional Models</span></span>](perspectives-in-multidimensional-models.md)|<span data-ttu-id="32c63-143">큐브 뷰를 정의 및 구성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="32c63-143">Describes how to define and configure a perspective.</span></span>|  
|[<span data-ttu-id="32c63-144">저장 프로시저 정의</span><span class="sxs-lookup"><span data-stu-id="32c63-144">Defining Stored Procedures</span></span>](../multidimensional-models-extending-olap-stored-procedures/defining-stored-procedures.md)|<span data-ttu-id="32c63-145">저장 프로시저 작업 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="32c63-145">Describes how to work with stored procedures.</span></span>|  
  
  
