---
title: 멤버 속성 사용 (MDX) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- DIMENSION PROPERTIES keyword
- Properties function
- member properties [MDX]
- members [MDX], properties
ms.assetid: 26b5ad08-3799-4a5e-89f3-dca25e637d45
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5b7fdf989fc23ea70be7d7863f5d4c6ac0b61d8a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730955"
---
# <a name="using-member-properties-mdx"></a><span data-ttu-id="7e815-102">멤버 속성 사용(MDX)</span><span class="sxs-lookup"><span data-stu-id="7e815-102">Using Member Properties (MDX)</span></span>
  <span data-ttu-id="7e815-103">멤버 속성은 각 튜플에 있는 각 멤버에 대한 기본 정보를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="7e815-103">Member properties cover the basic information about each member in each tuple.</span></span> <span data-ttu-id="7e815-104">이 기본 정보에는 멤버 이름, 부모 수준 및 자식의 수 등이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="7e815-104">This basic information includes the member name, parent level, the number of children, and so on.</span></span> <span data-ttu-id="7e815-105">해당 수준의 모든 멤버에 대해 멤버 속성을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7e815-105">Member properties are available for all members at a given level.</span></span> <span data-ttu-id="7e815-106">조직의 측면에서 볼 때 멤버 속성은 단일 차원에 저장되어 있고 차원에 따라 조직된 데이터로 취급됩니다.</span><span class="sxs-lookup"><span data-stu-id="7e815-106">In terms of organization, member properties are treated as dimensionally organized data, stored on a single dimension.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7e815-107">[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에서는 멤버 속성을 특성 관계라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="7e815-107">In [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], member properties are know as attribute relationships.</span></span> <span data-ttu-id="7e815-108">자세한 내용은 [특성 관계](../../multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7e815-108">For more information, see [Attribute Relationships](../../multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md).</span></span>  
  
 <span data-ttu-id="7e815-109">멤버 속성은 *기본* 또는 *사용자 지정*중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="7e815-109">Member properties are either *intrinsic* or *custom*:</span></span>  
  
 <span data-ttu-id="7e815-110">기본 멤버 속성</span><span class="sxs-lookup"><span data-stu-id="7e815-110">Intrinsic member properties</span></span>  
 <span data-ttu-id="7e815-111">모든 멤버는 멤버의 서식 값과 같은 기본 멤버 속성을 지원하고 차원과 수준은 멤버 ID와 같은 기본 차원 및 수준 멤버 속성을 추가로 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="7e815-111">All members support intrinsic member properties, such as the formatted value of a member, while dimensions and levels supply additional intrinsic dimension and level member properties, such as the ID of a member.</span></span>  
  
 <span data-ttu-id="7e815-112">자세한 내용은 [기본 멤버 속성&#40;MDX&#41;](mdx-member-properties-intrinsic-member-properties.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7e815-112">For more information, see [Intrinsic Member Properties &#40;MDX&#41;](mdx-member-properties-intrinsic-member-properties.md).</span></span>  
  
 <span data-ttu-id="7e815-113">사용자 정의 멤버 속성</span><span class="sxs-lookup"><span data-stu-id="7e815-113">User-defined member properties</span></span>  
 <span data-ttu-id="7e815-114">멤버가 자신과 관련된 추가 속성을 가진 경우가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7e815-114">Members often have additional properties associated with them.</span></span> <span data-ttu-id="7e815-115">예를 들어 제품 수준은 각 제품에 대한 SKU, SRP, 무게 및 부피 속성을 제공할 수 있을 것입니다.</span><span class="sxs-lookup"><span data-stu-id="7e815-115">For example, the Products level may offer the SKU, SRP, Weight, and Volume properties for each product.</span></span> <span data-ttu-id="7e815-116">이런 속성이 멤버는 아니지만 제품 수준의 멤버에 대한 추가 정보를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="7e815-116">These properties are not members, but contain additional information about members at the Products level.</span></span>  
  
 <span data-ttu-id="7e815-117">자세한 내용은 [사용자 정의 멤버 속성&#40;MDX&#41;](mdx-member-properties-user-defined-member-properties.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7e815-117">For more information, see [User-Defined Member Properties &#40;MDX&#41;](mdx-member-properties-user-defined-member-properties.md).</span></span>  
  
 <span data-ttu-id="7e815-118">`PROPERTIES`키워드 또는 [properties](/sql/mdx/properties-mdx) 함수를 사용 하 여 기본 및 사용자 정의 멤버 속성을 모두 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7e815-118">Both intrinsic and user-defined member properties can be retrieved through the use of the `PROPERTIES` keyword or the [Properties](/sql/mdx/properties-mdx) function.</span></span>  
  
## <a name="using-the-properties-keyword"></a><span data-ttu-id="7e815-119">PROPERTIES 키워드 사용</span><span class="sxs-lookup"><span data-stu-id="7e815-119">Using the PROPERTIES Keyword</span></span>  
 <span data-ttu-id="7e815-120">`PROPERTIES` 키워드는 지정된 축 차원에 사용할 멤버 속성을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="7e815-120">The `PROPERTIES` keyword specifies the member properties that are to be used for a given axis dimension.</span></span> <span data-ttu-id="7e815-121">`PROPERTIES`키워드는 `<axis specification>` MDX [SELECT](/sql/mdx/mdx-data-manipulation-select) 문의 절에 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7e815-121">The `PROPERTIES` keyword is buried within the `<axis specification>` clause of the MDX [SELECT](/sql/mdx/mdx-data-manipulation-select) statement:</span></span>  
  
```  
SELECT [<axis_specification>  
       [, <axis_specification>...]]  
  FROM [<cube_specification>]  
[WHERE [<slicer_specification>]]  
```  
  
 <span data-ttu-id="7e815-122">`<axis_specification>` 절은 다음 구문에 나타낸 것과 같이 `<dim_props>` 절(옵션)을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="7e815-122">The `<axis_specification>` clause includes an optional `<dim_props>` clause, as shown in the following syntax:</span></span>  
  
```  
<axis_specification> ::= <set> [<dim_props>] ON <axis_name>  
```  
  
> [!NOTE]  
>  <span data-ttu-id="7e815-123">`<set>` 및 `<axis_name>` 값에 대한 자세한 내용은 [쿼리 축의 내용 지정&#40;MDX&#41;](mdx-query-and-slicer-axes-specify-the-contents-of-a-query-axis.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7e815-123">For more information about the `<set>` and `<axis_name>` values, see [Specifying the Contents of a Query Axis &#40;MDX&#41;](mdx-query-and-slicer-axes-specify-the-contents-of-a-query-axis.md).</span></span>  
  
 <span data-ttu-id="7e815-124">`<dim_props>` 절에서는 `PROPERTIES` 키워드를 사용하여 차원, 수준 및 멤버 속성을 쿼리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7e815-124">The `<dim_props>` clause lets you query dimension, level, and member properties using the `PROPERTIES` keyword.</span></span> <span data-ttu-id="7e815-125">다음 구문은 `<dim_props>` 절의 서식을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="7e815-125">The following syntax shows the formatting of the `<dim_props>` clause:</span></span>  
  
```  
<dim_props> ::= [DIMENSION] PROPERTIES <property> [,<property>...]  
```  
  
 <span data-ttu-id="7e815-126">`<property>` 구문의 분석은 쿼리하는 속성에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="7e815-126">The breakdown of the `<property>` syntax varies depending on the property that you are querying:</span></span>  
  
-   <span data-ttu-id="7e815-127">차원 또는 수준 이름에 앞서 상황에 맞는 기본 멤버 속성이 선행되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7e815-127">Context sensitive intrinsic member properties must be preceded with the name of the dimension or level.</span></span> <span data-ttu-id="7e815-128">하지만 상황에 맞지 않는 기본 멤버 속성을 차원 또는 수준 이름으로 정규화할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7e815-128">However, non-context sensitive intrinsic member properties cannot be qualified by the dimension or level name.</span></span> <span data-ttu-id="7e815-129">키워드를 기본 멤버 속성과 함께 사용 하는 방법에 대 한 자세한 내용은 `PROPERTIES` [기본 멤버 속성 &#40;MDX&#41;](mdx-member-properties-intrinsic-member-properties.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="7e815-129">For more information about how to use the `PROPERTIES` keyword with intrinsic member properties, see [Intrinsic Member Properties &#40;MDX&#41;](mdx-member-properties-intrinsic-member-properties.md).</span></span>  
  
-   <span data-ttu-id="7e815-130">사용자 정의 멤버 속성은 자신이 상주하는 수준 이름보다 선행되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7e815-130">User-defined member properties should be preceded by the name of the level in which they reside.</span></span> <span data-ttu-id="7e815-131">키워드를 사용자 정의 멤버 속성과 함께 사용 하는 방법에 대 한 자세한 내용은 `PROPERTIES` [사용자 정의 멤버 속성 &#40;MDX&#41;](mdx-member-properties-user-defined-member-properties.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="7e815-131">For more information about how to use the `PROPERTIES` keyword with user-defined member properties, see [User-Defined Member Properties &#40;MDX&#41;](mdx-member-properties-user-defined-member-properties.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e815-132">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7e815-132">See Also</span></span>  
 [<span data-ttu-id="7e815-133">속성 값 만들기 및 사용&#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="7e815-133">Creating and Using Property Values &#40;MDX&#41;</span></span>](../../creating-and-using-property-values-mdx.md)  
  
  
