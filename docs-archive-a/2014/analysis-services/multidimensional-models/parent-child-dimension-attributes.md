---
title: 부모-자식 계층의 특성 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data members [Analysis Services]
- nonleaf members
- MembersWithDataCaption property
- members [Analysis Services]
- members [Analysis Services], data
- leaf members
- parent-child dimensions [Analysis Services]
- MembersWithData property
ms.assetid: 249971cc-4bcd-44f1-8241-bdacc04d3d38
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5c4a7e8ba43ac8ede0bd60409f84a6fa233ce182
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730951"
---
# <a name="attributes-in-parent-child-hierarchies"></a><span data-ttu-id="e1cdf-102">부모-자식 계층의 특성</span><span class="sxs-lookup"><span data-stu-id="e1cdf-102">Attributes in Parent-Child Hierarchies</span></span>
  <span data-ttu-id="e1cdf-103">에서는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 일반적으로 차원의 멤버 내용에 대 한 일반적인 가정이 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e1cdf-103">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], a general assumption is usually made about the content of members in a dimension.</span></span> <span data-ttu-id="e1cdf-104">즉, 리프 멤버에는 기본 데이터 원본에서 직접 파생되는 데이터가 있고 리프가 아닌 멤버에는 자식 멤버에 대해 수행된 집계에서 파생되는 데이터가 있다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="e1cdf-104">Leaf members contain data derived directly from underlying data sources; nonleaf members contain data derived from aggregations performed on child members.</span></span>  
  
 <span data-ttu-id="e1cdf-105">그러나 부모-자식 계층에서는 리프가 아닌 멤버 중 일부가 자식 멤버에서 집계된 데이터 외에도 기본 데이터 원본에서 파생된 데이터를 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e1cdf-105">In a parent-child hierarchy, however, some nonleaf members may also have data derived from underlying data sources, in addition to data aggregated from child members.</span></span> <span data-ttu-id="e1cdf-106">부모-자식 계층의 이러한 리프가 아닌 멤버에 대해서는 기본 팩트 테이블 데이터가 포함된 특별한 시스템 생성 자식 멤버가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="e1cdf-106">For these nonleaf members in a parent-child hierarchy, special system-generated child members are created that contain the underlying fact table data.</span></span> <span data-ttu-id="e1cdf-107">이러한 멤버를 *데이터 멤버*라고 하며 해당 값은 리프가 아닌 멤버와 직접 연결되며 리프가 아닌 멤버의 하위 항목으로부터 계산되는 요약 값에 독립적입니다.</span><span class="sxs-lookup"><span data-stu-id="e1cdf-107">Referred to as *data members*, they contain a value directly associated with a nonleaf member that is independent of the summary value calculated from the descendants of the nonleaf member.</span></span>  
  
 <span data-ttu-id="e1cdf-108">데이터 멤버는 부모-자식 계층이 있는 차원에만 사용할 수 있으며 부모 특성에서 허용되는 경우에만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e1cdf-108">Data members are available only to dimensions with parent-child hierarchies, and are visible only if allowed by the parent attribute.</span></span> <span data-ttu-id="e1cdf-109">차원 디자이너를 사용하여 데이터 멤버의 표시 여부를 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e1cdf-109">You can use Dimension Designer to control the visibility of data members.</span></span> <span data-ttu-id="e1cdf-110">데이터 멤버를 노출하려면 부모 특성의 `MembersWithData` 속성을 `NonLeafDataVisible.`로 설정합니다. 부모 특성에 포함된 데이터 멤버를 숨기려면 부모 특성의 `MembersWithData` 속성을 `NonLeafDataHidden`으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="e1cdf-110">To expose data members, set the `MembersWithData` property for the parent attribute to `NonLeafDataVisible.` To hide data members contained by the parent attribute, set the `MembersWithData` property on the parent attribute to `NonLeafDataHidden`.</span></span>  
  
 <span data-ttu-id="e1cdf-111">이 설정은 리프가 아닌 멤버의 일반 집계 동작을 재정의하지 않습니다. 데이터 멤버는 항상 집계를 위해 자식 멤버로 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="e1cdf-111">This setting does not override the normal aggregation behavior for nonleaf members; the data member is always included as a child member for the purposes of aggregation.</span></span> <span data-ttu-id="e1cdf-112">그러나 사용자 지정 롤업 수식을 사용하여 일반 집계 동작을 재정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e1cdf-112">However, a custom rollup formula can be used to override the normal aggregation behavior.</span></span> <span data-ttu-id="e1cdf-113">MDX (Multidimensional Expressions) [DataMember](/sql/mdx/datamember-mdx) 함수는 속성 값에 관계 없이 연결 된 데이터 멤버의 값에 액세스 하는 기능을 제공 합니다 `MembersWithData` .</span><span class="sxs-lookup"><span data-stu-id="e1cdf-113">The Multidimensional Expressions (MDX) [DataMember](/sql/mdx/datamember-mdx) function gives you the ability to access the value of the associated data member regardless of the value of the `MembersWithData` property.</span></span>  
  
 <span data-ttu-id="e1cdf-114">부모 특성의 `MembersWithDataCaption` 속성은 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]에 데이터 멤버의 멤버 이름을 생성하는 데 사용되는 명명 템플릿을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="e1cdf-114">The `MembersWithDataCaption` property of the parent attribute provides [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] with the naming template used to generate member names for data members.</span></span>  
  
## <a name="using-data-members"></a><span data-ttu-id="e1cdf-115">데이터 멤버 사용</span><span class="sxs-lookup"><span data-stu-id="e1cdf-115">Using Data Members</span></span>  
 <span data-ttu-id="e1cdf-116">데이터 멤버는 부모-자식 계층이 있는 조직 차원의 측정값을 집계하는 경우 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="e1cdf-116">Data members are useful when aggregating measures along organizational dimensions that have parent-child hierarchies.</span></span> <span data-ttu-id="e1cdf-117">예를 들어 아래 다이어그램에서는 제품의 총 판매량을 나타내는 세 가지 수준이 있는 차원을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="e1cdf-117">For example, the following diagram shows a dimension that has three levels, representing the gross sales volume of products.</span></span> <span data-ttu-id="e1cdf-118">첫 번째 수준은 모든 영업 사원의 총 판매량을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="e1cdf-118">The first level shows the gross sales volume for all salespersons.</span></span> <span data-ttu-id="e1cdf-119">두 번째 수준에는 영업 관리자별로 그룹화된 모든 영업 담당자의 총 판매량이 포함되고 세 번째 수준에는 영업 사원별로 그룹화된 모든 영업 담당자의 총 판매량이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="e1cdf-119">The second level contains the gross sales volume for all sales staff grouped by sales manager, and the third level contains the gross sales volume for all sales staff grouped by salesperson.</span></span>  
  
 <span data-ttu-id="e1cdf-120">![3개의 수준을 포함하는 총 판매량 차원](../media/agdatamember1.gif "3개의 수준을 포함하는 총 판매량 차원")</span><span class="sxs-lookup"><span data-stu-id="e1cdf-120">![Gross sales volume dimension with three levels](../media/agdatamember1.gif "Gross sales volume dimension with three levels")</span></span>  
  
 <span data-ttu-id="e1cdf-121">일반적으로 Sales Manager 1 멤버의 값은 Salesperson 1 및 Salesperson 2 멤버의 값을 집계하여 파생됩니다.</span><span class="sxs-lookup"><span data-stu-id="e1cdf-121">Ordinarily, the value of the Sales Manager 1 member would be derived by aggregating the values of the Salesperson 1 and Salesperson 2 members.</span></span> <span data-ttu-id="e1cdf-122">그러나 Sales Manager 1도 제품을 판매할 수 있어 Sales Manager 1에 관련된 총 판매량이 있을 수 있으므로 팩트 테이블에서 파생된 데이터가 해당 멤버에 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e1cdf-122">However, because Sales Manager 1 also can sell products, that member may also contain data derived from the fact table, because there may be gross sales associated with Sales Manager 1.</span></span>  
  
 <span data-ttu-id="e1cdf-123">또한 각 영업 담당자 멤버에 대한 개별 커미션이 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e1cdf-123">Moreover, the individual commissions for each sales staff member can vary.</span></span> <span data-ttu-id="e1cdf-124">이 경우 자신의 영업 사원이 거둔 총 판매량과는 반대로 두 가지 기준을 사용하여 영업 관리자의 개별 총 판매량에 대한 커미션을 컴퓨팅합니다.</span><span class="sxs-lookup"><span data-stu-id="e1cdf-124">In this case, two different scales are used to compute commissions for the individual gross sales of the sales managers, as opposed to the total of gross sales generated by their salespersons.</span></span> <span data-ttu-id="e1cdf-125">그러므로 리프가 아닌 멤버에게는 기본 팩트 테이블 데이터에 액세스할 수 있는지 여부가 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="e1cdf-125">Therefore, it is important to be able to access the underlying fact table data for nonleaf members.</span></span> <span data-ttu-id="e1cdf-126">MDX `DataMember` 함수를 사용하여 Sales Manager 1 멤버의 개별 총 판매량을 검색하고, 사용자 지정 롤업 식을 사용하여 Sales Manager 1 멤버의 집계 값에서 데이터 멤버를 제외함으로써 해당 멤버와 관련된 영업 사원의 판매량을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e1cdf-126">The MDX `DataMember` function can be used to retrieve the individual gross sales volume of the Sales Manager 1 member, and a custom rollup expression can be used to exclude the data member from the aggregated value of the Sales Manager 1 member, providing the gross sales volume of the salespersons associated with that member.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1cdf-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e1cdf-127">See Also</span></span>  
 <span data-ttu-id="e1cdf-128">[차원 특성 속성 참조](dimension-attribute-properties-reference.md) </span><span class="sxs-lookup"><span data-stu-id="e1cdf-128">[Dimension Attribute Properties Reference](dimension-attribute-properties-reference.md) </span></span>  
 [<span data-ttu-id="e1cdf-129">부모-자식 계층</span><span class="sxs-lookup"><span data-stu-id="e1cdf-129">Parent-Child Hierarchy</span></span>](parent-child-dimension.md)  
  
  
