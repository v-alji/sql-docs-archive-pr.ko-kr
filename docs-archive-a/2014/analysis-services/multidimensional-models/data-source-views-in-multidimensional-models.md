---
title: 다차원 모델의 데이터 원본 뷰 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data source views [Analysis Services]
- data source views [Analysis Services], about data source views
- SQL Server Analysis Services, data source views
- data source views [Analysis Services], multiple
- Analysis Services, data source views
- multiple data source views
- SSAS, data source views
ms.assetid: 4c12376f-4fc2-492b-9a00-93eec34571ed
author: minewiskan
ms.author: owend
ms.openlocfilehash: 1aef6b6d716ec71ac082ca8b7c042492c1712b1a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741411"
---
# <a name="data-source-views-in-multidimensional-models"></a><span data-ttu-id="6f09b-102">다차원 모델의 데이터 원본 뷰</span><span class="sxs-lookup"><span data-stu-id="6f09b-102">Data Source Views in Multidimensional Models</span></span>
  <span data-ttu-id="6f09b-103">DSV(데이터 원본 뷰)는 추상화된 관계형 데이터 원본으로서 다차원 프로젝트에서 이 데이터 원본을 사용하여 큐브와 차원을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f09b-103">A data source view (DSV) is an abstraction of a relational data source that becomes the basis of the cubes and dimensions you create in a multidimensional project.</span></span> <span data-ttu-id="6f09b-104">DSV의 목적은 프로젝트에 사용된 데이터 구조를 제어하고 기본 데이터 원본과 관계없이 작업할 수 있도록 하는 것입니다. 예를 들어 원래 데이터 원본을 직접 수정하지 않고 열의 이름을 바꾸거나 열을 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f09b-104">The purpose of a DSV is to give you control over the data structures used in your project, and to work independently of the underlying data sources (for example, the ability to rename or concatenate columns without directly modifying the original data source).</span></span>  
  
 <span data-ttu-id="6f09b-105">하나 이상의 데이터 원본에서 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 프로젝트나 데이터베이스에 여러 개의 데이터 원본 뷰를 작성하고 각각 서로 다른 솔루션의 요구 사항을 만족하도록 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f09b-105">You can build multiple data source views in an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project or database on one or more data sources, and construct each one to satisfy the requirements for a different solution.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="6f09b-106">관련 작업</span><span class="sxs-lookup"><span data-stu-id="6f09b-106">Related Tasks</span></span>  
 [<span data-ttu-id="6f09b-107">데이터 원본 뷰 정의&#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="6f09b-107">Defining a Data Source View &#40;Analysis Services&#41;</span></span>](defining-a-data-source-view-analysis-services.md)  
  
 [<span data-ttu-id="6f09b-108">데이터 원본 뷰에서 테이블이나 뷰 추가 또는 제거&#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="6f09b-108">Adding or Removing Tables or Views in a Data Source View &#40;Analysis Services&#41;</span></span>](adding-or-removing-tables-or-views-in-a-data-source-view-analysis-services.md)  
  
 [<span data-ttu-id="6f09b-109">데이터 원본 뷰에서 속성 변경&#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="6f09b-109">Change Properties in a Data Source View &#40;Analysis Services&#41;</span></span>](change-properties-in-a-data-source-view-analysis-services.md)  
  
 [<span data-ttu-id="6f09b-110">데이터 원본 뷰에서 논리적 관계 정의&#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="6f09b-110">Define Logical Relationships in a Data Source View &#40;Analysis Services&#41;</span></span>](define-logical-relationships-in-a-data-source-view-analysis-services.md)  
  
 [<span data-ttu-id="6f09b-111">데이터 원본 뷰에서 논리적 기본 키 정의&#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="6f09b-111">Define Logical Primary Keys in a Data Source View &#40;Analysis Services&#41;</span></span>](define-logical-primary-keys-in-a-data-source-view-analysis-services.md)  
  
 [<span data-ttu-id="6f09b-112">데이터 원본 뷰에서 명명된 계산 정의&#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="6f09b-112">Define Named Calculations in a Data Source View &#40;Analysis Services&#41;</span></span>](define-named-calculations-in-a-data-source-view-analysis-services.md)  
  
 [<span data-ttu-id="6f09b-113">데이터 원본 뷰에서 명명된 쿼리 정의&#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="6f09b-113">Define Named Queries in a Data Source View &#40;Analysis Services&#41;</span></span>](define-named-queries-in-a-data-source-view-analysis-services.md)  
  
 [<span data-ttu-id="6f09b-114">데이터 원본 뷰의 테이블 또는 명명된 쿼리 바꾸기&#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="6f09b-114">Replace a Table or a Named Query in a Data Source View &#40;Analysis Services&#41;</span></span>](replace-a-table-or-a-named-query-in-a-data-source-view-analysis-services.md)  
  
 [<span data-ttu-id="6f09b-115">데이터 원본 뷰 디자이너에서의 다이어그램 작업&#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="6f09b-115">Work with Diagrams in Data Source View Designer &#40;Analysis Services&#41;</span></span>](work-with-diagrams-in-data-source-view-designer-analysis-services.md)  
  
 [<span data-ttu-id="6f09b-116">데이터 원본 뷰에서 데이터 탐색&#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="6f09b-116">Explore Data in a Data Source View &#40;Analysis Services&#41;</span></span>](explore-data-in-a-data-source-view-analysis-services.md)  
  
 [<span data-ttu-id="6f09b-117">데이터 원본 뷰 삭제&#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="6f09b-117">Delete a Data Source View &#40;Analysis Services&#41;</span></span>](delete-a-data-source-view-analysis-services.md)  
  
 [<span data-ttu-id="6f09b-118">데이터 원본 뷰에서 스키마 새로 고침&#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="6f09b-118">Refresh the Schema in a Data Source View &#40;Analysis Services&#41;</span></span>](refresh-the-schema-in-a-data-source-view-analysis-services.md)  
  
## <a name="see-also"></a><span data-ttu-id="6f09b-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6f09b-119">See Also</span></span>  
 <span data-ttu-id="6f09b-120">[스키마 생성 마법사 &#40;Analysis Services&#41;](schema-generation-wizard-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="6f09b-120">[Schema Generation Wizard &#40;Analysis Services&#41;](schema-generation-wizard-analysis-services.md) </span></span>  
 [<span data-ttu-id="6f09b-121">SSAS 다차원&#41;&#40;지원 되는 데이터 원본</span><span class="sxs-lookup"><span data-stu-id="6f09b-121">Data Sources Supported &#40;SSAS Multidimensional&#41;</span></span>](supported-data-sources-ssas-multidimensional.md)  
  
  
