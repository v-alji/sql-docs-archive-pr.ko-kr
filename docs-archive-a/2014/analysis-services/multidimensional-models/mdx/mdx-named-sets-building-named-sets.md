---
title: 명명 된 집합을 MDX로 작성 (MDX) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Multidimensional Expressions [Analysis Services], named sets
- named sets [MDX]
- sets [MDX]
- MDX [Analysis Services], named sets
- queries [MDX], named sets
- set expressions [MDX]
ms.assetid: 213b0035-e96d-4ba0-83f2-ded206905603
author: minewiskan
ms.author: owend
ms.openlocfilehash: 91296f8c5d47afb15c67f0b60435c7f961734573
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730972"
---
# <a name="building-named-sets-in-mdx-mdx"></a><span data-ttu-id="6f2a3-102">명명된 집합을 MDX로 작성(MDX)</span><span class="sxs-lookup"><span data-stu-id="6f2a3-102">Building Named Sets in MDX (MDX)</span></span>
  <span data-ttu-id="6f2a3-103">식 집합은 길고 복잡한 선언이 될 수 있으므로 이해하기 어려울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f2a3-103">A set expression can be a lengthy and complex declaration, and therefore be difficult to follow or understand.</span></span> <span data-ttu-id="6f2a3-104">또는 식 집합이 너무 자주 사용되어 반복적으로 집합을 정의하는 작업이 부담이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f2a3-104">Or, a set expression may be used so frequently that repeatedly defining the set becomes burdensome.</span></span> <span data-ttu-id="6f2a3-105">이렇게 길고, 복잡하며, 일상적으로 사용되는 식을 쉽게 만들기 위해 MDX에서는 *명명된 집합*이라는 식을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f2a3-105">To help make working with a lengthy, complex or commonly used expression easier, Multidimensional Expressions (MDX) lets you such an expression as a *named set*.</span></span>  
  
 <span data-ttu-id="6f2a3-106">기본적으로 명명된 집합은 별칭이 할당된 집합 식입니다.</span><span class="sxs-lookup"><span data-stu-id="6f2a3-106">Basically, a named set is a set expression to which an alias has been assigned.</span></span> <span data-ttu-id="6f2a3-107">명명된 집합은 일반적으로 통합이 가능한 멤버나 함수를 집합으로 통합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f2a3-107">A named set can incorporate any members or functions that can ordinarily be incorporated into a set.</span></span> <span data-ttu-id="6f2a3-108">MDX는 명명된 집합 별칭을 집합 식으로 취급하기 때문에 집합 식이 사용되는 모든 곳에 이러한 별칭을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f2a3-108">Because MDX treats the named set alias as a set expression, you can use that alias anywhere a set expression is accepted.</span></span>  
  
 <span data-ttu-id="6f2a3-109">다음 컨텍스트 중 하나가 포함되도록 명명된 집합을 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f2a3-109">You can define a named set to have one of the following contexts:</span></span>  
  
-   <span data-ttu-id="6f2a3-110">**쿼리 범위** MDX 쿼리의 일부로 정의되는 명명된 집합을 만들어서 해당 범위가 쿼리로 제한되도록 하려면 WITH 키워드를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6f2a3-110">**Query-scoped** To create a named set that is defined as part of an MDX query, and therefore whose scope is limited to the query, you use the WITH keyword.</span></span> <span data-ttu-id="6f2a3-111">그런 다음 MDX SELECT 문 내에서 명명된 집합을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f2a3-111">You can then use the named set within an MDX SELECT statement.</span></span> <span data-ttu-id="6f2a3-112">이 방식을 사용할 경우, WITH 키워드를 사용하여 만든 명명된 집합은 SELECT 문을 배포하지 않아도 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f2a3-112">Using this approach, the named set created by using the WITH keyword can be changed without disturbing the SELECT statement.</span></span>  
  
     <span data-ttu-id="6f2a3-113">WITH 키워드를 사용하여 명명된 집합을 만드는 방법에 대한 자세한 내용은 [쿼리 범위 명명된 집합 만들기&#40;MDX&#41;](mdx-named-sets-creating-query-scoped-named-sets.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6f2a3-113">For more information about how to use the WITH keyword to create named sets, see [Creating Query-Scoped Named Sets &#40;MDX&#41;](mdx-named-sets-creating-query-scoped-named-sets.md).</span></span>  
  
-   <span data-ttu-id="6f2a3-114">**세션 범위** 범위가 쿼리 컨텍스트보다 넓은 즉, 범위가 MDX 세션의 수명인 명명된 집합을 만들려면 CREATE SET 문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6f2a3-114">**Session-scoped** To create a named set whose scope is wider than the context of the query, that is, whose scope is the lifetime of the MDX session, you use the CREATE SET statement.</span></span> <span data-ttu-id="6f2a3-115">CREATE SET 문을 사용하여 정의된 명명된 집합은 해당 세션의 모든 MDX 쿼리에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f2a3-115">A named set defined by using the CREATE SET statement is available to all MDX queries in that session.</span></span> <span data-ttu-id="6f2a3-116">예를 들어 CREATE SET 문은 여러 쿼리에서 하나의 집합을 계속적으로 다시 사용하는 클라이언트 애플리케이션에 적합합니다.</span><span class="sxs-lookup"><span data-stu-id="6f2a3-116">The CREATE SET statement makes sense, for example, in a client application that consistently reuses a set in a variety of queries.</span></span>  
  
     <span data-ttu-id="6f2a3-117">CREATE SET 문을 사용하여 세션에서 명명된 집합을 만드는 방법에 대한 자세한 내용은 [세션 범위 명명된 집합 만들기&#40;MDX&#41;](mdx-named-sets-creating-session-scoped-named-sets.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6f2a3-117">For more information about how to use the CREATE SET statement to create named sets in a session, see [Creating Session-Scoped Named Sets &#40;MDX&#41;](mdx-named-sets-creating-session-scoped-named-sets.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f2a3-118">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6f2a3-118">See Also</span></span>  
 <span data-ttu-id="6f2a3-119">[SELECT 문 &#40;MDX&#41;](/sql/mdx/mdx-data-manipulation-select) </span><span class="sxs-lookup"><span data-stu-id="6f2a3-119">[SELECT Statement &#40;MDX&#41;](/sql/mdx/mdx-data-manipulation-select) </span></span>  
 <span data-ttu-id="6f2a3-120">[CREATE SET 문 &#40;MDX&#41;](/sql/mdx/mdx-data-definition-create-set) </span><span class="sxs-lookup"><span data-stu-id="6f2a3-120">[CREATE SET Statement &#40;MDX&#41;](/sql/mdx/mdx-data-definition-create-set) </span></span>  
 [<span data-ttu-id="6f2a3-121">MDX 쿼리 기본 사항&#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="6f2a3-121">MDX Query Fundamentals &#40;Analysis Services&#41;</span></span>](mdx-query-fundamentals-analysis-services.md)  
  
  
