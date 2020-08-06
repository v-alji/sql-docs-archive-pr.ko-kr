---
title: 특성 관계 | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- member properties [Analysis Services], attribute relationships
- security [Analysis Services], properties
- PROPERTIES keyword
- storage [Analysis Services], attribute relationships
- natural hierarchies [Analysis Services]
- dimensions [Analysis Services], member properties
- queries [MDX], attribute relationships
- user-defined hierarchies [Analysis Services]
- attributes [Analysis Services], relationships
- member properties [Analysis Services]
- members [Analysis Services], attribute relationships
- storing data [Analysis Services], attribute relationships
- relationships [Analysis Services], attributes
ms.assetid: 2491422a-4cf5-4b23-b6ab-289222b22ce8
author: minewiskan
ms.author: owend
ms.openlocfilehash: 122638a2728a8a85ee58661196797383da20eef8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87733227"
---
# <a name="attribute-relationships"></a><span data-ttu-id="52ab6-102">의 차원 디자이너에 있는 차원 구조 뷰의</span><span class="sxs-lookup"><span data-stu-id="52ab6-102">Attribute Relationships</span></span>
  <span data-ttu-id="52ab6-103">에서 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 차원 내의 특성은 항상 키 특성과 직접 또는 간접적으로 관련이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52ab6-103">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], attributes within a dimension are always related either directly or indirectly to the key attribute.</span></span> <span data-ttu-id="52ab6-104">모든 차원 특성이 동일한 관계형 테이블에서 파생되는 별모양 스키마를 기반으로 차원을 정의할 경우 차원의 키 특성과 각각의 키가 아닌 특성 간에 특성 관계가 자동으로 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="52ab6-104">When you define a dimension based on a star schema, which is where all dimension attributes are derived from the same relational table, an attribute relationship is automatically defined between the key attribute and each non-key attribute of the dimension.</span></span> <span data-ttu-id="52ab6-105">그러나 차원 특성이 관련된 여러 테이블에서 파생되는 눈송이 스키마를 기반으로 차원을 정의하면 다음 사이에서 특성 관계가 자동으로 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="52ab6-105">When you define a dimension based on a snowflake schema, which is where dimension attributes are derived from multiple related tables, an attribute relationship is automatically defined as follows:</span></span>  
  
-   <span data-ttu-id="52ab6-106">키 특성과 주 차원 테이블의 열에 바인딩된 각각의 키가 아닌 특성 간</span><span class="sxs-lookup"><span data-stu-id="52ab6-106">Between the key attribute and each non-key attribute bound to columns in the main dimension table.</span></span>  
  
-   <span data-ttu-id="52ab6-107">키 특성과 기본 차원 테이블을 연결하는 보조 테이블의 외래 키에 바인딩된 특성 간</span><span class="sxs-lookup"><span data-stu-id="52ab6-107">Between the key attribute and the attribute bound to the foreign key in the secondary table that links the underlying dimension tables.</span></span>  
  
-   <span data-ttu-id="52ab6-108">보조 테이블의 외래 키에 바인딩된 특성과 보조 테이블의 열에 바인딩된 각각의 키가 아닌 특성 간</span><span class="sxs-lookup"><span data-stu-id="52ab6-108">Between the attribute bound to foreign key in the secondary table and each non-key attribute bound to columns from the secondary table.</span></span>  
  
 <span data-ttu-id="52ab6-109">그러나 다양한 이유로 이러한 기본 특성 관계를 변경하려고 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52ab6-109">However, there are a number of reasons why you might want to change these default attribute relationships.</span></span> <span data-ttu-id="52ab6-110">예를 들어 키가 아닌 특성을 기반으로 자연 계층, 사용자 지정 정렬 순서 또는 차원 세분성을 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52ab6-110">For example, you might want to define a natural hierarchy, a custom sort order, or dimension granularity based on a non-key attribute.</span></span> <span data-ttu-id="52ab6-111">자세한 내용은 [차원 특성 속성 참조](../multidimensional-models/dimension-attribute-properties-reference.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="52ab6-111">For more information, see [Dimension Attribute Properties Reference](../multidimensional-models/dimension-attribute-properties-reference.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="52ab6-112">MDX(Multidimensional Expressions)에서는 특성 관계를 멤버 속성이라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="52ab6-112">Attribute relationships are known in Multidimensional Expressions (MDX) as member properties.</span></span>  
  
## <a name="natural-hierarchy-relationships"></a><span data-ttu-id="52ab6-113">자연 계층 관계</span><span class="sxs-lookup"><span data-stu-id="52ab6-113">Natural Hierarchy Relationships</span></span>  
 <span data-ttu-id="52ab6-114">사용자 정의 계층에 포함된 각 특성이 바로 아래에 있는 특성과 일 대 다 관계를 가질 때 계층은 자연 계층입니다.</span><span class="sxs-lookup"><span data-stu-id="52ab6-114">A hierarchy is a natural hierarchy when each attribute included in the user-defined hierarchy has a one to many relationship with the attribute immediately below it.</span></span> <span data-ttu-id="52ab6-115">예를 들어 다음과 같은 8개의 열이 있는 관계형 원본 테이블을 기반으로 하는 Customer 차원을 고려해 보십시오.</span><span class="sxs-lookup"><span data-stu-id="52ab6-115">For example, consider a Customer dimension based on a relational source table with eight columns:</span></span>  
  
-   <span data-ttu-id="52ab6-116">CustomerKey</span><span class="sxs-lookup"><span data-stu-id="52ab6-116">CustomerKey</span></span>  
  
-   <span data-ttu-id="52ab6-117">CustomerName</span><span class="sxs-lookup"><span data-stu-id="52ab6-117">CustomerName</span></span>  
  
-   <span data-ttu-id="52ab6-118">나이</span><span class="sxs-lookup"><span data-stu-id="52ab6-118">Age</span></span>  
  
-   <span data-ttu-id="52ab6-119">성별</span><span class="sxs-lookup"><span data-stu-id="52ab6-119">Gender</span></span>  
  
-   <span data-ttu-id="52ab6-120">Email</span><span class="sxs-lookup"><span data-stu-id="52ab6-120">Email</span></span>  
  
-   <span data-ttu-id="52ab6-121">도시</span><span class="sxs-lookup"><span data-stu-id="52ab6-121">City</span></span>  
  
-   <span data-ttu-id="52ab6-122">국가</span><span class="sxs-lookup"><span data-stu-id="52ab6-122">Country</span></span>  
  
-   <span data-ttu-id="52ab6-123">지역</span><span class="sxs-lookup"><span data-stu-id="52ab6-123">Region</span></span>  
  
 <span data-ttu-id="52ab6-124">해당하는 Analysis Services 차원에는 다음의 7가지 특성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52ab6-124">The corresponding Analysis Services dimension has seven attributes:</span></span>  
  
-   <span data-ttu-id="52ab6-125">Customer(CustomerKey를 기반으로 하며 CustomerName이 멤버 이름을 제공함)</span><span class="sxs-lookup"><span data-stu-id="52ab6-125">Customer (based on CustomerKey, with CustomerName supplying member names)</span></span>  
  
-   <span data-ttu-id="52ab6-126">Age, Gender, Email, City, Region, Country</span><span class="sxs-lookup"><span data-stu-id="52ab6-126">Age, Gender, Email, City, Region, Country</span></span>  
  
 <span data-ttu-id="52ab6-127">자연 계층을 나타내는 관계는 수준에 대한 특성 및 아래 수준에 대한 특성 간의 특성 관계를 만들어 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="52ab6-127">Relationships representing natural hierarchies are enforced by creating an attribute relationship between the attribute for a level and the attribute for the level below it.</span></span> <span data-ttu-id="52ab6-128">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]의 경우 이를 통해 자연 관계와 잠재적인 집계가 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="52ab6-128">For [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], this specifies a natural relationship and potential aggregation.</span></span> <span data-ttu-id="52ab6-129">Customer 차원에 Country, Region, City 및 Customer 특성에 대한 자연 계층이 존재하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="52ab6-129">In the Customer dimension, a natural hierarchy exists for the Country, Region, City, and Customer attributes.</span></span> <span data-ttu-id="52ab6-130">`{Country, Region, City, Customer}`에 대한 자연 계층은 다음과 같은 특성 관계를 추가하여 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="52ab6-130">The natural hierarchy for `{Country, Region, City, Customer}` is described by adding the following attribute relationships:</span></span>  
  
-   <span data-ttu-id="52ab6-131">Region 특성에 대한 특성 관계로 Country 특성 추가</span><span class="sxs-lookup"><span data-stu-id="52ab6-131">The Country attribute as an attribute relationship to the Region attribute.</span></span>  
  
-   <span data-ttu-id="52ab6-132">City 특성에 대한 특성 관계로 Region 특성 추가</span><span class="sxs-lookup"><span data-stu-id="52ab6-132">The Region attribute as an attribute relationship to the City attribute.</span></span>  
  
-   <span data-ttu-id="52ab6-133">Customer 특성에 대한 특성 관계로 City 특성 추가</span><span class="sxs-lookup"><span data-stu-id="52ab6-133">The City attribute as an attribute relationship to the Customer attribute.</span></span>  
  
 <span data-ttu-id="52ab6-134">큐브의 데이터를 탐색 하려는 경우 데이터의 자연 계층을 나타내지 않는 사용자 정의 계층 ( *임시 또는* *보고* 계층 이라고 함)을 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52ab6-134">For navigating data in the cube, you can also create a user-defined hierarchy that does not represent a natural hierarchy in the data (which is called an *ad hoc* or *reporting* hierarchy).</span></span> <span data-ttu-id="52ab6-135">예를 들어 `{Age, Gender}`를 기반으로 사용자 정의 계층을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52ab6-135">For example, you could create a user-defined hierarchy based on `{Age, Gender}`.</span></span> <span data-ttu-id="52ab6-136">자연 계층은 원본 데이터의 자연 관계를 고려 하 여 사용자 로부터 숨겨진 구조를 집계 및 인덱싱할 수 있다는 장점이 있지만 사용자는 두 계층의 동작 방식에 차이가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="52ab6-136">Users do not see any difference in how the two hierarchies behave, although the natural hierarchy benefits from aggregating and indexing structures - hidden from the user - that account for the natural relationships in the source data.</span></span>  
  
 <span data-ttu-id="52ab6-137">수준 차원의 `SourceAttribute` 속성은 수준을 설명하는 데 사용되는 특성을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="52ab6-137">The `SourceAttribute` property of a level determines which attribute is used to describe the level.</span></span> <span data-ttu-id="52ab6-138">특성에 대한 `KeyColumns` 속성은 멤버를 공급하는 데이터 원본 뷰의 열을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="52ab6-138">The `KeyColumns` property on the attribute specifies the column in the data source view that supplies the members.</span></span> <span data-ttu-id="52ab6-139">특성에 대한 `NameColumn` 속성은 멤버에 대해 다른 이름 열을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52ab6-139">The `NameColumn` property on the attribute can specify a different name column for the members.</span></span>  
  
 <span data-ttu-id="52ab6-140">를 사용 하 여 사용자 정의 계층에 수준을 정의 하려면 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] **차원 디자이너** 를 사용 하 여 차원 특성, 차원 테이블의 열 또는 큐브의 데이터 원본 뷰에 포함 된 관련 테이블의 열을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52ab6-140">To define a level in a user-defined hierarchy using [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], the **Dimension Designer** allows you to select a dimension attribute, a column in a dimension table, or a column from a related table included in the data source view for the cube.</span></span> <span data-ttu-id="52ab6-141">사용자 정의 계층을 만드는 방법에 대 한 자세한 내용은 [사용자 정의 계층 만들기](../multidimensional-models/user-defined-hierarchies-create.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="52ab6-141">For more information about creating user-defined hierarchies, see [Create User-Defined Hierarchies](../multidimensional-models/user-defined-hierarchies-create.md).</span></span>  
  
 <span data-ttu-id="52ab6-142">Analysis Services에서는 멤버의 내용에 대해 대체로 하나의 가정이 이루어집니다.</span><span class="sxs-lookup"><span data-stu-id="52ab6-142">In Analysis Services, an assumption is usually made about the content of members.</span></span> <span data-ttu-id="52ab6-143">리프 멤버에는 하위 멤버가 없으며 기본 데이터 원본에서 파생된 데이터가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="52ab6-143">Leaf members have no descendents and contain data derived from underlying data sources.</span></span> <span data-ttu-id="52ab6-144">리프가 아닌 멤버에는 하위 멤버가 있고 자식 멤버에 대해 수행된 집계에서 파생된 데이터가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="52ab6-144">Nonleaf members have descendents and contain data derived from aggregations performed on child members.</span></span> <span data-ttu-id="52ab6-145">집계된 수준에서 멤버는 종속 수준의 집계를 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="52ab6-145">In aggregated levels, members are based on aggregations of subordinate levels.</span></span> <span data-ttu-id="52ab6-146">따라서 수준에 대한 원본 특성에서 `IsAggregatable` 속성을 `False`로 설정한 경우 집계 가능한 특성을 상위 수준으로 추가하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="52ab6-146">Therefore, when the `IsAggregatable` property is set to `False` on a source attribute for a level, no aggregatable attributes should be added as levels above it.</span></span>  
  
## <a name="defining-an-attribute-relationship"></a><span data-ttu-id="52ab6-147">특성 관계 정의</span><span class="sxs-lookup"><span data-stu-id="52ab6-147">Defining an Attribute Relationship</span></span>  
 <span data-ttu-id="52ab6-148">특성 관계를 만들 때 주요 제약 조건은 특성 관계에서 참조하는 특성에 특성 관계가 속하는 특성의 멤버에 대한 값이 하나만 있어야 한다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="52ab6-148">The main constraint when you create an attribute relationship is to make sure that the attribute referred to by the attribute relationship has no more than one value for any member in the attribute to which the attribute relationship belongs.</span></span> <span data-ttu-id="52ab6-149">예를 들어 City 특성과 State 특성 간에 관계를 정의하면 각 도시는 하나의 시와만 관련될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52ab6-149">For example, if you define a relationship between a City attribute and a State attribute, each city can only relate to a single state.</span></span>  
  
## <a name="attribute-relationship-queries"></a><span data-ttu-id="52ab6-150">특성 관계 쿼리</span><span class="sxs-lookup"><span data-stu-id="52ab6-150">Attribute Relationship Queries</span></span>  
 <span data-ttu-id="52ab6-151">MDX 쿼리에 MDX `PROPERTIES` 문의 `SELECT` 키워드를 사용하여 특성 관계에서 멤버 속성 형식으로 데이터를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52ab6-151">You can use MDX queries to retrieve data from attribute relationships, in the form of member properties, with the `PROPERTIES` keyword of the MDX `SELECT` statement.</span></span> <span data-ttu-id="52ab6-152">MDX를 사용 하 여 멤버 속성을 검색 하는 방법에 대 한 자세한 내용은 [멤버 속성 &#40;mdx&#41;사용 ](../multidimensional-models/mdx/mdx-member-properties.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="52ab6-152">For more information about how to use MDX to retrieve member properties, see [Using Member Properties &#40;MDX&#41;](../multidimensional-models/mdx/mdx-member-properties.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52ab6-153">참고 항목</span><span class="sxs-lookup"><span data-stu-id="52ab6-153">See Also</span></span>  
 <span data-ttu-id="52ab6-154">[특성 및 특성 계층](attributes-and-attribute-hierarchies.md) </span><span class="sxs-lookup"><span data-stu-id="52ab6-154">[Attributes and Attribute Hierarchies](attributes-and-attribute-hierarchies.md) </span></span>  
 <span data-ttu-id="52ab6-155">[차원 특성 속성 참조](../multidimensional-models/dimension-attribute-properties-reference.md) </span><span class="sxs-lookup"><span data-stu-id="52ab6-155">[Dimension Attribute Properties Reference](../multidimensional-models/dimension-attribute-properties-reference.md) </span></span>  
 <span data-ttu-id="52ab6-156">[사용자 계층](user-hierarchies.md) </span><span class="sxs-lookup"><span data-stu-id="52ab6-156">[User Hierarchies](user-hierarchies.md) </span></span>  
 [<span data-ttu-id="52ab6-157">사용자 계층 속성</span><span class="sxs-lookup"><span data-stu-id="52ab6-157">User Hierarchy Properties</span></span>](user-hierarchies-properties.md)  
  
  
