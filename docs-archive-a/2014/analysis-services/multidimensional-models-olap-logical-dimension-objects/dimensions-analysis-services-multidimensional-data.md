---
title: 차원 (Analysis Services 다차원 데이터) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- OLAP objects [Analysis Services], dimensions
- dimensions [Analysis Services]
- Analysis Services objects, dimensions
ms.assetid: 2b114135-2572-4479-8c81-3ccf0cfeb9f7
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2e0e15d4f74c2c6cec06edaf692199e48534c7e9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738950"
---
# <a name="dimensions-analysis-services---multidimensional-data"></a><span data-ttu-id="70bb9-102">차원(Analysis Services - 다차원 데이터)</span><span class="sxs-lookup"><span data-stu-id="70bb9-102">Dimensions (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="70bb9-103">에서 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 차원은 큐브의 기본 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="70bb9-103">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], dimensions are a fundamental component of cubes.</span></span> <span data-ttu-id="70bb9-104">고객, 대리점 또는 직원 등 사용자의 관심 영역과 관련된 데이터를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="70bb9-104">Dimensions organize data with relation to an area of interest, such as customers, stores, or employees, to users.</span></span> <span data-ttu-id="70bb9-105">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]의 차원에는 차원 테이블의 열에 해당하는 특성이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="70bb9-105">Dimensions in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] contain attributes that correspond to columns in dimension tables.</span></span> <span data-ttu-id="70bb9-106">이러한 특성은 특성 계층으로 표시되며 사용자 정의 계층에 구성하거나 기본 차원 테이블의 열을 기반으로 하여 부모-자식 계층으로 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="70bb9-106">These attributes appear as attribute hierarchies and can be organized into user-defined hierarchies, or can be defined as parent-child hierarchies based on columns in the underlying dimension table.</span></span> <span data-ttu-id="70bb9-107">계층을 사용하여 큐브에 포함되어 있는 측정값을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="70bb9-107">Hierarchies are used to organize measures that are contained in a cube.</span></span> <span data-ttu-id="70bb9-108">다음 항목에서는 차원, 특성 및 계층의 개요를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="70bb9-108">The following topics provide an overview of dimensions, attributes, and hierarchies.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="70bb9-109">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="70bb9-109">In This Section</span></span>  
  
|<span data-ttu-id="70bb9-110">항목</span><span class="sxs-lookup"><span data-stu-id="70bb9-110">Topic</span></span>|<span data-ttu-id="70bb9-111">설명</span><span class="sxs-lookup"><span data-stu-id="70bb9-111">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="70bb9-112">차원 소개&#40;Analysis Services - 다차원 데이터&#41;</span><span class="sxs-lookup"><span data-stu-id="70bb9-112">Introduction to Dimensions &#40;Analysis Services - Multidimensional Data&#41;</span></span>](dimensions-analysis-services-multidimensional-data.md)|<span data-ttu-id="70bb9-113">차원 개념에 대한 개요를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="70bb9-113">Provides an overview of dimension concepts.</span></span>|  
|[<span data-ttu-id="70bb9-114">특성 및 특성 계층</span><span class="sxs-lookup"><span data-stu-id="70bb9-114">Attributes and Attribute Hierarchies</span></span>](attributes-and-attribute-hierarchies.md)|<span data-ttu-id="70bb9-115">특성 및 특성 계층에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="70bb9-115">Describes attributes and attribute hierarchies.</span></span>|  
|[<span data-ttu-id="70bb9-116">사용자 계층</span><span class="sxs-lookup"><span data-stu-id="70bb9-116">User Hierarchies</span></span>](user-hierarchies.md)|<span data-ttu-id="70bb9-117">특성의 사용자 정의 계층에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="70bb9-117">Describes user-defined hierarchies of attributes.</span></span>|  
|[<span data-ttu-id="70bb9-118">쓰기 가능 차원</span><span class="sxs-lookup"><span data-stu-id="70bb9-118">Write-Enabled Dimensions</span></span>](write-enabled-dimensions.md)|<span data-ttu-id="70bb9-119">쓰기 가능한 차원에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="70bb9-119">Describes write-enabled dimensions.</span></span>|  
|[<span data-ttu-id="70bb9-120">차원 번역</span><span class="sxs-lookup"><span data-stu-id="70bb9-120">Dimension Translations</span></span>](dimension-translations.md)|<span data-ttu-id="70bb9-121">차원 메타데이터 번역에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="70bb9-121">Describes translations of dimension meta data.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="70bb9-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="70bb9-122">See Also</span></span>  
 <span data-ttu-id="70bb9-123">[다차원 모델의 차원](../multidimensional-models/dimensions-in-multidimensional-models.md) </span><span class="sxs-lookup"><span data-stu-id="70bb9-123">[Dimensions in Multidimensional Models](../multidimensional-models/dimensions-in-multidimensional-models.md) </span></span>  
 [<span data-ttu-id="70bb9-124">큐브 개체는 Analysis Services 다차원 데이터를 &#40;&#41;</span><span class="sxs-lookup"><span data-stu-id="70bb9-124">Cube Objects &#40;Analysis Services - Multidimensional Data&#41;</span></span>](../multidimensional-models-olap-logical-cube-objects/cube-objects-analysis-services-multidimensional-data.md)  
  
  
