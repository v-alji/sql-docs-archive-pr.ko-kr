---
title: 튜플 | Microsoft Docs
ms.custom: ''
ms.date: 07/17/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 35b629ae-b1ef-44b1-b556-96956aeb56e7
author: minewiskan
ms.author: owend
ms.openlocfilehash: c39d03d60cb66f3b2e26b2e660bd85f4e5e9d4ec
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736994"
---
# <a name="tuples"></a><span data-ttu-id="84d05-102">튜플</span><span class="sxs-lookup"><span data-stu-id="84d05-102">Tuples</span></span>
  <span data-ttu-id="84d05-103">튜플은 큐브의 데이터 조각을 고유하게 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="84d05-103">A tuple uniquely identifies a slice of data from a cube.</span></span> <span data-ttu-id="84d05-104">동일한 계층에 속하는 둘 이상의 멤버가 없는 경우 튜플은 차원 멤버의 조합으로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="84d05-104">The tuple is formed by a combination of dimension members, as long as there are no two or more members that belong to the same hierarchy.</span></span>  
  
## <a name="implicit-or-default-attribute-members-in-a-tuple"></a><span data-ttu-id="84d05-105">튜플의 암시적 또는 기본 특성 멤버</span><span class="sxs-lookup"><span data-stu-id="84d05-105">Implicit or default attribute members in a tuple</span></span>  
 <span data-ttu-id="84d05-106">MDX 쿼리 또는 식에서 튜플을 정의할 때 각 특성 계층의 특성 멤버를 명시적으로 포함할 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="84d05-106">When defining a tuple in an MDX query or expression, you do not need to explicitly include the attribute member from every attribute hierarchy.</span></span> <span data-ttu-id="84d05-107">쿼리나 식에 특성 계층의 멤버가 명시적으로 포함되어 있지 않으면 해당 특성 계층의 기본 멤버가 암시적으로 튜플에 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="84d05-107">If a member from an attribute hierarchy is not explicitly included in a query or an expression, the default member for that attribute hierarchy is the attribute member implicitly included in the tuple.</span></span> <span data-ttu-id="84d05-108">큐브에 명시적으로 달리 정의되어 있지 않고 (All) 멤버가 있는 경우 모든 특성 계층의 기본 멤버는 (All) 멤버입니다.</span><span class="sxs-lookup"><span data-stu-id="84d05-108">Unless otherwise explicitly defined in a cube, the default member for every attribute hierarchy is the (All) member, if an (All) member exists.</span></span> <span data-ttu-id="84d05-109">특성 계층 내에 (All) 멤버가 없는 경우 기본 멤버는 해당 특성 계층의 최상위 수준 멤버입니다.</span><span class="sxs-lookup"><span data-stu-id="84d05-109">If an (All) member does not exist within an attribute hierarchy, the default member is a member of the attribute hierarchy's top level.</span></span> <span data-ttu-id="84d05-110">또한 기본 측정값이 명시적으로 정의되지 않은 경우 큐브에 지정된 첫 번째 측정값이 기본 측정값이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="84d05-110">The default measure is the first measure specified in the cube, unless a default measure is explicitly defined.</span></span> <span data-ttu-id="84d05-111">자세한 내용은 [기본 멤버 정의](../attribute-properties-define-a-default-member.md) 및 [DefaultMember&#40;MDX&#41;](/sql/mdx/defaultmember-mdx)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="84d05-111">For more information, see [Define a Default Member](../attribute-properties-define-a-default-member.md) and [DefaultMember &#40;MDX&#41;](/sql/mdx/defaultmember-mdx).</span></span>  
  
 <span data-ttu-id="84d05-112">예를 들어 다음 튜플은 Adventure Works 데이터베이스에서 Measures 차원의 단일 멤버만을 명시적으로 정의하여 단일 셀을 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="84d05-112">For example, the following tuple identifies a single cell in the Adventure Works database by explicitly defining only a single member of the Measures dimension.</span></span>  
  
```  
(Measures.[Reseller Sales Amount])  
```  
  
 <span data-ttu-id="84d05-113">이 예에서는 Measures 차원의 Reseller Sales Amount 멤버와 큐브에 있는 각 특성 계층의 기본 멤버로 구성된 셀을 고유하게 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="84d05-113">The previous example uniquely identifies the cell consisting of the Reseller Sales Amount member from the Measures dimension and the default member from every attribute hierarchy in the cube.</span></span> <span data-ttu-id="84d05-114">Destination Currency 특성 계층을 제외한 모든 특성 계층의 기본 멤버는 (All) 멤버입니다.</span><span class="sxs-lookup"><span data-stu-id="84d05-114">The default member is the (All) member for every attribute hierarchy other than the Destination Currency attribute hierarchy.</span></span> <span data-ttu-id="84d05-115">Destination Currency 계층의 기본 멤버는 US Dollar 멤버입니다. 이 기본 멤버는 Adventure Works 큐브에 대한 MDX 스크립트에 정의되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84d05-115">The default member for the Destination Currency hierarchy is the US Dollar member (this default member is defined in the MDX script for the Adventure Works cube).</span></span>  
  
 <span data-ttu-id="84d05-116">다음 쿼리에서는 앞의 예에서 지정한 튜플이 참조하는 셀의 값($80,450.596.98)을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="84d05-116">The following query returns the value for the cell referenced by the tuple specified in the previous example, ($80,450.596.98).</span></span>  
  
```  
SELECT   
Measures.[Reseller Sales Amount] ON COLUMNS   
FROM [Adventure Works]  
```  
  
> [!NOTE]  
>  <span data-ttu-id="84d05-117">쿼리에서 집합(이 경우 단일 튜플로 구성)의 축을 지정할 때는 먼저 열 집합 축을 지정한 후 행 집합 축을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="84d05-117">When you specify an axis for a set (in this case composed of a single tuple) in a query, you must begin by specifying a set for the column axis before specifying a set for the row axis.</span></span> <span data-ttu-id="84d05-118">열 축은 *axis(0)* 또는 간단히 *0*으로도 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84d05-118">The column axis can also be referred to as *axis(0)* or simply *0*.</span></span> <span data-ttu-id="84d05-119">MDX 쿼리에 대한 자세한 내용은 [기본 MDX 쿼리&#40;MDX&#41;](mdx-query-the-basic-query.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="84d05-119">For more information about MDX queries, see [The Basic MDX Query &#40;MDX&#41;](mdx-query-the-basic-query.md).</span></span>  
  
### <a name="tuples-as-values-or-member-references"></a><span data-ttu-id="84d05-120">값 또는 멤버 참조인 튜플</span><span class="sxs-lookup"><span data-stu-id="84d05-120">Tuples as values or member references</span></span>  
 <span data-ttu-id="84d05-121">앞의 예에서처럼 쿼리에 튜플을 사용하여 해당 튜플이 참조하는 셀의 값을 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84d05-121">You can use a tuple in a query to return the value in the cell that is referenced by the tuple, as in the previous example.</span></span> <span data-ttu-id="84d05-122">또는 식에 튜플을 사용하여 해당 튜플에 지정된 멤버를 명시적으로 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84d05-122">Or you can use a tuple in an expression to explicitly refer to the members specified in the tuple.</span></span> <span data-ttu-id="84d05-123">쿼리나 식에서는 튜플을 반환하거나 구성하는 함수를 이용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84d05-123">The query or the expression can utilize functions that either return or consume tuples.</span></span> <span data-ttu-id="84d05-124">튜플을 사용하면 해당 튜플이 지정하는 셀의 값을 참조할 수 있으며 튜플을 함수에 사용할 경우에는 멤버의 조합을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84d05-124">A tuple can be used to either refer to the value of the cell that the tuple specifies, or to specify a combination of members when utilized in a function.</span></span>  
  
### <a name="tuple-dimensionality"></a><span data-ttu-id="84d05-125">튜플 차원</span><span class="sxs-lookup"><span data-stu-id="84d05-125">Tuple dimensionality</span></span>  
 <span data-ttu-id="84d05-126">튜플의 *차원* 은 해당 튜플에서 멤버가 나타나는 순서 또는 시퀀스를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="84d05-126">The *dimensionality* of a tuple refers to the sequence or order of the members in the tuple.</span></span> <span data-ttu-id="84d05-127">암시적 멤버는 항상 동일한 순서로 나타나므로 차원은 대개 튜플에 명시적으로 정의된 멤버의 측면에서 생각할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84d05-127">Since the implicit members always occur in the same order, dimensionality is most often thought of in terms of the explicitly defined members of the tuple.</span></span> <span data-ttu-id="84d05-128">튜플 집합을 정의할 때는 튜플의 멤버 순서가 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="84d05-128">The ordering of the members of the tuple is important when you define a set of tuples.</span></span> <span data-ttu-id="84d05-129">다음 예에서는 튜플의 두 멤버를 열 축에 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="84d05-129">The following example includes two members in a tuple on the column axis.</span></span>  
  
```  
SELECT   
([Measures].[Reseller Sales Amount],[Date].[Calendar Year].[CY 2004]) ON COLUMNS   
FROM [Adventure Works]  
```  
  
> [!NOTE]  
>  <span data-ttu-id="84d05-130">둘 이상의 차원에서 튜플의 멤버를 명시적으로 지정할 때는 튜플 전체를 괄호로 묶어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="84d05-130">When you explicitly specify a member in a tuple from more than one dimension, you must include the entire tuple in parentheses.</span></span> <span data-ttu-id="84d05-131">튜플의 단일 멤버만 지정할 때는 괄호로 묶지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="84d05-131">When only specifying a single member in a tuple, parentheses are optional.</span></span>  
  
 <span data-ttu-id="84d05-132">앞의 예에 나온 쿼리의 튜플은 Measures 차원의 Reseller Sales Amount 측정값과 Date 차원의 Calendar Year 특성 계층 중 CY 2004 멤버가 교차하는 지점의 큐브 셀을 반환하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="84d05-132">The tuple in the query in the previous example specifies the return of the cube cell at the intersection of the Reseller Sales Amount Measure of the Measures dimension and the CY 2004 member of the Calendar Year attribute hierarchy in the Date dimension.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="84d05-133">특성 멤버는 멤버 이름이나 멤버 키로 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84d05-133">An attribute member can be referred by either its member name or its member key.</span></span> <span data-ttu-id="84d05-134">앞의 예에서 [CY 2004]에 대한 참조는 &[2004]로 바꿀 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84d05-134">In the previous example, you could replace the reference to [CY 2004] with &[2004].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84d05-135">참고 항목</span><span class="sxs-lookup"><span data-stu-id="84d05-135">See Also</span></span>  
 <span data-ttu-id="84d05-136">[MDX의 주요 개념 &#40;Analysis Services&#41;](../key-concepts-in-mdx-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="84d05-136">[Key Concepts in MDX &#40;Analysis Services&#41;](../key-concepts-in-mdx-analysis-services.md) </span></span>  
 <span data-ttu-id="84d05-137">[큐브 공간](cube-space.md) </span><span class="sxs-lookup"><span data-stu-id="84d05-137">[Cube Space](cube-space.md) </span></span>  
 <span data-ttu-id="84d05-138">[Autoexist](autoexists.md) </span><span class="sxs-lookup"><span data-stu-id="84d05-138">[Autoexists](autoexists.md) </span></span>  
 [<span data-ttu-id="84d05-139">멤버, 튜플 및 집합 작업&#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="84d05-139">Working with Members, Tuples, and Sets &#40;MDX&#41;</span></span>](working-with-members-tuples-and-sets-mdx.md)  
  
  
