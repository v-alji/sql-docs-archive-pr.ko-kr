---
title: 측정값 속성 구성 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- additivity [Analysis Services]
- ID property
- ErrorConfiguration property
- AggregateFunction property
- DisplayFolder property
- IgnoreUnrelatedDimensions property
- FormatString property
- Description property
- semiadditive
- properties [Analysis Services], measure groups
- aggregate functions [Analysis Services]
- DataType property
- ProcessingMode property
- MeasureExpression property
- AggregationPrefix property
- Visible property
- properties [Analysis Services], measures
- StorageLocation property
- StorageMode property
- formats [Analysis Services], measures
- Source property
- aggregations [Analysis Services], measures
- measures [Analysis Services], properties
- nonadditive [Analysis Services]
- Name property
- measures [Analysis Services], display formats
- ProcessingPriority property
- measure groups [Analysis Services], properties
- Type property
- ProactiveCaching property
ms.assetid: e9031078-c4f5-4986-b0c9-4d064b622ab7
author: minewiskan
ms.author: owend
ms.openlocfilehash: 7ca291a5181fdb3f7a88845431d61ffd7a1034eb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737108"
---
# <a name="configure-measure-properties"></a><span data-ttu-id="2227b-102">측정값 속성 구성</span><span class="sxs-lookup"><span data-stu-id="2227b-102">Configure Measure Properties</span></span>
  <span data-ttu-id="2227b-103">측정값에는 해당 측정값의 작동 방법을 정의하고 측정값의 표시 방법을 제어하는 데 사용할 수 있는 속성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2227b-103">Measures have properties that enable you to define how the measures function and to control how the measures appear to users.</span></span>  
  
 <span data-ttu-id="2227b-104">큐브 또는 측정값을 만들거나 편집할 때 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 에서 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2227b-104">You can set properties in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] when creating or editing a cube or measure.</span></span> <span data-ttu-id="2227b-105">또한 MDX 또는 AMO를 사용하여 프로그래밍 방식으로 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2227b-105">You can also set them programmatically, using MDX or AMO.</span></span> <span data-ttu-id="2227b-106">자세한 내용은 [다차원 모델의 측정값 및 측정값 그룹 만들기](create-measures-and-measure-groups-in-multidimensional-models.md), [CREATE MEMBER 문&#40;MDX&#41;](/sql/mdx/mdx-data-definition-create-member) 또는 [AMO OLAP 기본 개체 프로그래밍](https://docs.microsoft.com/bi-reference/amo/programming-amo-olap-basic-objects)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2227b-106">See [Create Measures and Measure Groups in Multidimensional Models](create-measures-and-measure-groups-in-multidimensional-models.md) or [CREATE MEMBER Statement &#40;MDX&#41;](/sql/mdx/mdx-data-definition-create-member) or [Programming AMO OLAP Basic Objects](https://docs.microsoft.com/bi-reference/amo/programming-amo-olap-basic-objects) for details.</span></span>  
  
## <a name="measure-properties"></a><span data-ttu-id="2227b-107">측정값 속성</span><span class="sxs-lookup"><span data-stu-id="2227b-107">Measure Properties</span></span>  
 <span data-ttu-id="2227b-108">측정값은 해당 속성이 측정값 수준에서 무시되는 경우를 제외하고 자신이 속한 측정값 그룹에서 특정 속성을 상속합니다.</span><span class="sxs-lookup"><span data-stu-id="2227b-108">Measures inherit certain properties from the measure group of which they are a member, unless those properties are overridden at the measure level.</span></span> <span data-ttu-id="2227b-109">측정값 속성은 측정값이 집계되는 방법, 측정값의 데이터 형식, 사용자에게 표시되는 이름, 측정값이 나타날 표시 폴더, 측정값의 형식 문자열, 측정값 식, 기본 원본 열 및 사용자에 대한 표시 유형을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="2227b-109">Measure properties determine how a measure is aggregated, its data type, the name that is displayed to the user, the display folder in which the measure will appear, its format string, any measure expression, the underlying source column, and its visibility to users.</span></span>  
  
|<span data-ttu-id="2227b-110">속성</span><span class="sxs-lookup"><span data-stu-id="2227b-110">Property</span></span>|<span data-ttu-id="2227b-111">정의</span><span class="sxs-lookup"><span data-stu-id="2227b-111">Definition</span></span>|  
|--------------|----------------|  
|`AggregateFunction`|<span data-ttu-id="2227b-112">필수 요소.</span><span class="sxs-lookup"><span data-stu-id="2227b-112">Required.</span></span> <span data-ttu-id="2227b-113">측정값이 집계되는 방법을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="2227b-113">Determines how measures are aggregated.</span></span> <span data-ttu-id="2227b-114">`Sum`이 기본 집계입니다.</span><span class="sxs-lookup"><span data-stu-id="2227b-114">`Sum` is the default aggregation.</span></span> <span data-ttu-id="2227b-115">자세한 내용은 각 함수 설명의 [Use Aggregate Functions](use-aggregate-functions.md) 을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2227b-115">For more information, see [Use Aggregate Functions](use-aggregate-functions.md) for a description of each function.</span></span>|  
|`DataType`|<span data-ttu-id="2227b-116">필수 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="2227b-116">Required.</span></span> <span data-ttu-id="2227b-117">측정값이 바인딩되는 기본 팩트 테이블 열의 데이터 형식을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2227b-117">Specifies the data type of the column in the underlying fact table to which the measure is bound.</span></span> <span data-ttu-id="2227b-118">이 값은 기본적으로 원본 열에서 상속됩니다.</span><span class="sxs-lookup"><span data-stu-id="2227b-118">This value is inherited from the source column by default.</span></span>|  
|`Description`|<span data-ttu-id="2227b-119">클라이언트 애플리케이션에 노출될 수 있는 측정값에 대한 설명을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="2227b-119">Provides a description of the measure, which may be exposed in client applications.</span></span>|  
|`DisplayFolder`|<span data-ttu-id="2227b-120">사용자가 큐브에 연결할 때 측정값이 표시되는 폴더를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2227b-120">Specifies the folder in which the measure will appear when users connect to the cube.</span></span> <span data-ttu-id="2227b-121">큐브에 많은 측정값이 있을 때 표시 폴더를 사용하여 측정값을 분류하고 사용자 검색 환경을 개선할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2227b-121">When a cube has many measures, you can use display folders to categorize the measures and improve the user browsing experience.</span></span>|  
|`FormatString`|<span data-ttu-id="2227b-122">측정값의 `FormatString` 속성을 사용하여 사용자에게 측정값을 표시하는 데 사용되는 형식을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2227b-122">You can select the format that is used to display measure values to users by using the `FormatString` property of the measure.</span></span><br /><br /> <span data-ttu-id="2227b-123">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]에서 표시 형식 목록이 제공되지만 목록에 없는 여러 가지 추가 형식을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2227b-123">Although a list of display formats is provided in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], you can specify many additional formats that are not in the list.</span></span> <span data-ttu-id="2227b-124">Microsoft Visual Basic에서 유효한 사용자 정의 형식이나 명명된 형식을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2227b-124">You can specify any named or user-defined format that is valid in Microsoft Visual Basic.</span></span>|  
|`ID`|<span data-ttu-id="2227b-125">필수 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="2227b-125">Required.</span></span> <span data-ttu-id="2227b-126">측정값의 고유 ID를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="2227b-126">Displays the unique identifier (ID) of the measure.</span></span> <span data-ttu-id="2227b-127">이 속성은 읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="2227b-127">This property is read-only.</span></span>|  
|`MeasureExpression`|<span data-ttu-id="2227b-128">측정값을 정의하는 제한된 MDX 식을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2227b-128">Specifies a constrained MDX expression defining the value of the measure.</span></span> <span data-ttu-id="2227b-129">식은 집계되기 전에 리프 수준에서 평가되고 값의 가중치 적용을 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="2227b-129">The expression is evaluated at the leaf level before being aggregated, and allows for weighting of a value.</span></span> <span data-ttu-id="2227b-130">예를 들어 통화 변환에서 판매액은 환율에 따라 가중치가 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="2227b-130">For example, in currency conversion where a sales amount is weighted by the exchange rate.</span></span>|  
|`Name`|<span data-ttu-id="2227b-131">필수 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="2227b-131">Required.</span></span> <span data-ttu-id="2227b-132">측정값의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2227b-132">Specifies the name of the measure.</span></span>|  
|`Source`|<span data-ttu-id="2227b-133">필수 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="2227b-133">Required.</span></span> <span data-ttu-id="2227b-134">측정값이 바인딩되는 데이터 원본 뷰의 열을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2227b-134">Specifies the column in the data source view to which the measure is bound.</span></span> <span data-ttu-id="2227b-135">[데이터 원본 및 바인딩&#40;SSAS 다차원&#41;](data-sources-and-bindings-ssas-multidimensional.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2227b-135">See [Data Sources and Bindings &#40;SSAS Multidimensional&#41;](data-sources-and-bindings-ssas-multidimensional.md).</span></span>|  
|`Visible`|<span data-ttu-id="2227b-136">클라이언트 애플리케이션에서 측정값의 표시 유형을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="2227b-136">Determines the visibility of the measure in client applications.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2227b-137">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2227b-137">See Also</span></span>  
 <span data-ttu-id="2227b-138">[측정값 그룹 속성 구성](configure-measure-group-properties.md) </span><span class="sxs-lookup"><span data-stu-id="2227b-138">[Configure Measure Group Properties](configure-measure-group-properties.md) </span></span>  
 [<span data-ttu-id="2227b-139">측정값 수정</span><span class="sxs-lookup"><span data-stu-id="2227b-139">Modifying Measures</span></span>](../lesson-3-1-modifying-measures.md)  
  
  
