---
title: 부모-자식 계층 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- hierarchies [Analysis Services], parent-child
- dimensions [Analysis Services], parent-child
- parent attributes [Analysis Services]
- data members [Analysis Services]
- hierarchies [Analysis Services], multilevel
- self-joins
- self-referencing relationships
- members [Analysis Services], data
- parent-child dimensions [Analysis Services]
ms.assetid: 4657f5dc-d88e-48d2-a448-08f79bc89546
author: minewiskan
ms.author: owend
ms.openlocfilehash: b08641e9ba17e6ad2e2f4112e01073d448aa8564
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742619"
---
# <a name="parent-child-hierarchy"></a><span data-ttu-id="905f3-102">부모-자식 계층</span><span class="sxs-lookup"><span data-stu-id="905f3-102">Parent-Child Hierarchy</span></span>
  <span data-ttu-id="905f3-103">부모-자식 계층은 부모 특성이 포함된 표준 차원의 계층입니다.</span><span class="sxs-lookup"><span data-stu-id="905f3-103">A parent-child hierarchy is a hierarchy in a standard dimension that contains a parent attribute.</span></span> <span data-ttu-id="905f3-104">부모 특성은 차원 주 테이블 내의 *자체 참조 관계*또는 *셀프 조인*을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="905f3-104">A parent attribute describes a *self-referencing relationship*, or *self-join*, within a dimension main table.</span></span> <span data-ttu-id="905f3-105">부모-자식 계층은 단일 부모 특성에서 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="905f3-105">Parent-child hierarchies are constructed from a single parent attribute.</span></span> <span data-ttu-id="905f3-106">계층에 존재하는 수준은 부모 특성과 관련된 멤버 간 부모-자식 관계에서 가져오므로 부모-자식 계층에는 하나의 수준만 할당됩니다.</span><span class="sxs-lookup"><span data-stu-id="905f3-106">Only one level is assigned to a parent-child hierarchy, because the levels present in the hierarchy are drawn from the parent-child relationships between members associated with the parent attribute.</span></span> <span data-ttu-id="905f3-107">부모-자식 계층의 멤버 위치는 부모 특성의 `KeyColumns` 및 `RootMemberIf` 속성에 의해 결정되지만 한 수준의 멤버 위치는 부모 특성의 `OrderBy` 속성에 의해 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="905f3-107">The position of a member in a parent-child hierarchy is determined by the `KeyColumns` and `RootMemberIf` properties of the parent attribute, whereas the position of a member in a level is determined by the `OrderBy` property of the parent attribute.</span></span> <span data-ttu-id="905f3-108">특성 속성에 대한 자세한 내용은 [특성 및 특성 계층](../multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="905f3-108">For more information about attribute properties, see [Attributes and Attribute Hierarchies](../multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md).</span></span>  
  
 <span data-ttu-id="905f3-109">부모-자식 계층의 수준 간 부모-자식 관계로 인해 일부 리프가 아닌 멤버는 자식 멤버에서 집계한 데이터뿐만 아니라 기본 데이터 원본에서 파생된 데이터를 가질 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="905f3-109">Because of parent-child relationships between levels in a parent-child hierarchy, some nonleaf members can also have data derived from underlying data sources, in addition to data aggregated from child members.</span></span>  
  
## <a name="dimension-schema"></a><span data-ttu-id="905f3-110">차원 스키마</span><span class="sxs-lookup"><span data-stu-id="905f3-110">Dimension Schema</span></span>  
 <span data-ttu-id="905f3-111">부모-자식 계층의 차원 스키마는 차원 주 테이블에 있는 자체 참조 관계에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="905f3-111">The dimension schema of a parent-child hierarchy depends on a self-referencing relationship present on the dimension main table.</span></span> <span data-ttu-id="905f3-112">예를 들어 다음 다이어그램에서는 **예제 데이터베이스의** DimOrganization [!INCLUDE[ssSampleDBDWobject](../../includes/sssampledbdwobject-md.md)] 차원 주 테이블을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="905f3-112">For example, the following diagram illustrates the **DimOrganization** dimension main table in the [!INCLUDE[ssSampleDBDWobject](../../includes/sssampledbdwobject-md.md)] sample database.</span></span>  
  
 <span data-ttu-id="905f3-113">![DimOrganization 테이블의 자체 참조 조인](../dev-guide/media/dimorganization.gif "DimOrganization 테이블의 자체 참조 조인")</span><span class="sxs-lookup"><span data-stu-id="905f3-113">![Self-referencing join in DimOrganization table](../dev-guide/media/dimorganization.gif "Self-referencing join in DimOrganization table")</span></span>  
  
 <span data-ttu-id="905f3-114">이 차원 테이블에서 **ParentOrganizationKey** 열은 **OrganizationKey** 기본 키 열과 외래 키 관계에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="905f3-114">In this dimension table, the **ParentOrganizationKey** column has a foreign key relationship with the **OrganizationKey** primary key column.</span></span> <span data-ttu-id="905f3-115">즉, 이 테이블의 각 레코드는 부모-자식 관계를 통해 테이블의 다른 레코드와 관련될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="905f3-115">In other words, each record in this table can be related through a parent-child relationship with another record in the table.</span></span> <span data-ttu-id="905f3-116">이러한 종류의 자체 조인은 일반적으로 부서 내 직원 관리 구조와 같은 조직 엔터티 데이터를 나타내는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="905f3-116">This kind of self-join is generally used to represent organization entity data, such as the management structure of employees in a department.</span></span>  
  
## <a name="hierarchies-and-levels"></a><span data-ttu-id="905f3-117">계층 및 수준</span><span class="sxs-lookup"><span data-stu-id="905f3-117">Hierarchies and Levels</span></span>  
 <span data-ttu-id="905f3-118">부모-자식 관계가 없는 차원은 특성을 그룹화하고 정렬하여 계층을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="905f3-118">Dimensions that do not have a parent-child relationship construct hierarchies by grouping and ordering attributes.</span></span> <span data-ttu-id="905f3-119">이러한 차원에서는 계층에 대한 수준 이름이 특성 이름에서 파생됩니다.</span><span class="sxs-lookup"><span data-stu-id="905f3-119">These dimensions derive the level names for their hierarchies from the attribute names.</span></span>  
  
 <span data-ttu-id="905f3-120">그러나 부모-자식 차원은 차원 주 테이블에 포함된 데이터를 검사하여 부모-자식 계층을 구성한 다음 테이블에 있는 레코드 간의 부모-자식 관계를 평가합니다.</span><span class="sxs-lookup"><span data-stu-id="905f3-120">However, parent-child dimensions construct parent-child hierarchies by examining the data that the dimension main table contains, and then evaluating the parent-child relationships between the records in the table.</span></span> <span data-ttu-id="905f3-121">부모-자식 계층에 대한 자세한 내용은 [사용자 계층](../multidimensional-models-olap-logical-dimension-objects/user-hierarchies.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="905f3-121">For more information about parent-child hierarchies, see [User Hierarchies](../multidimensional-models-olap-logical-dimension-objects/user-hierarchies.md).</span></span>  
  
 <span data-ttu-id="905f3-122">부모-자식 계층에서는 계층의 수준 이름이 계층을 만드는 데 사용되는 특성에서 파생되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="905f3-122">Parent-child hierarchies do not derive the names for the levels in a parent-child hierarchy from the attributes that are used to create the hierarchy.</span></span> <span data-ttu-id="905f3-123">대신 이러한 차원은 명명 템플릿을 사용 하 여 자동으로 수준 이름을 만듭니다. 특성은 특성 계층을 생성 하는 방법을 제어 하는 부모 특성의 수준에서 지정할 수 있는 문자열 식입니다.</span><span class="sxs-lookup"><span data-stu-id="905f3-123">Instead, these dimensions create level names automatically by using a naming template-a string expression you can specify at the level of the parent attribute that controls how the attribute generates the attribute hierarchy.</span></span> <span data-ttu-id="905f3-124">부모 특성의 명명 템플릿을 설정하는 방법에 대한 자세한 내용은 [특성 및 특성 계층](../multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="905f3-124">For more information about how to set the naming template for a parent attribute, see [Attributes and Attribute Hierarchies](../multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md).</span></span>  
  
## <a name="data-members"></a><span data-ttu-id="905f3-125">데이터 멤버</span><span class="sxs-lookup"><span data-stu-id="905f3-125">Data Members</span></span>  
 <span data-ttu-id="905f3-126">일반적으로 차원의 리프 멤버는 기본 데이터 원본에서 직접 파생된 데이터를 포함하는 반면 리프가 아닌 멤버는 자식 멤버에 대해 수행된 집계에서 파생된 데이터를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="905f3-126">Typically, leaf members in a dimension contain data derived directly from underlying data sources, whereas nonleaf members contain data derived from aggregations performed on child members.</span></span>  
  
 <span data-ttu-id="905f3-127">그러나 부모-자식 계층에는 자식 멤버에서 집계되는 데이터뿐 아니라 기본 데이터 원본에서 파생되는 데이터를 포함하는 리프가 아닌 멤버가 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="905f3-127">However, parent-child hierarchies might have some nonleaf members whose data is derived from underlying data sources, in addition to data aggregated from child members.</span></span> <span data-ttu-id="905f3-128">부모-자식 계층의 이러한 리프가 아닌 멤버에 대해서는 기본 팩트 테이블 데이터가 포함된 특별한 시스템 생성 자식 멤버를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="905f3-128">For these nonleaf members in a parent-child hierarchy, special system-generated child members can be created that contain the underlying fact table data.</span></span> <span data-ttu-id="905f3-129">*데이터 멤버*라고 하는 이러한 특수 자식 멤버에는 리프가 아닌 멤버와 직접 연결되며 리프가 아닌 멤버의 하위 항목에서 계산되는 요약 값에 독립적인 값이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="905f3-129">Referred to as *data members*, these special child members contain a value that is directly associated with a nonleaf member and is independent of the summary value calculated from the descendants of the nonleaf member.</span></span> <span data-ttu-id="905f3-130">데이터 멤버에 대한 자세한 내용은 [부모-자식 계층의 특성](parent-child-dimension-attributes.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="905f3-130">For more information about data members, see [Attributes in Parent-Child Hierarchies](parent-child-dimension-attributes.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="905f3-131">참고 항목</span><span class="sxs-lookup"><span data-stu-id="905f3-131">See Also</span></span>  
 <span data-ttu-id="905f3-132">[부모-자식 계층의 특성](parent-child-dimension-attributes.md) </span><span class="sxs-lookup"><span data-stu-id="905f3-132">[Attributes in Parent-Child Hierarchies](parent-child-dimension-attributes.md) </span></span>  
 [<span data-ttu-id="905f3-133">데이터베이스 차원 속성</span><span class="sxs-lookup"><span data-stu-id="905f3-133">Database Dimension Properties</span></span>](../multidimensional-models-olap-logical-dimension-objects/database-dimension-properties.md)  
  
  
