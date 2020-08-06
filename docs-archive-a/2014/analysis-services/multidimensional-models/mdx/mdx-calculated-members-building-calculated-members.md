---
title: 계산 멤버를 MDX로 작성 (MDX) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- MDX [Analysis Services], calculated members
- calculated members [MDX]
- Multidimensional Expressions [Analysis Services], calculated members
- queries [MDX], calculated members
ms.assetid: 9322e8b8-43e1-4e02-a7d1-e41a586a5bb8
author: minewiskan
ms.author: owend
ms.openlocfilehash: 30dc6562ec394065cf2f177608d4e5679cbd7df3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649731"
---
# <a name="building-calculated-members-in-mdx-mdx"></a><span data-ttu-id="ca200-102">계산 멤버를 MDX로 작성(MDX)</span><span class="sxs-lookup"><span data-stu-id="ca200-102">Building Calculated Members in MDX (MDX)</span></span>
  <span data-ttu-id="ca200-103">MDX에서 계산 멤버는 값을 반환하기 위해 MDX 식을 계산하여 확인되는 멤버입니다.</span><span class="sxs-lookup"><span data-stu-id="ca200-103">In Multidimensional Expressions (MDX), a calculated member is a member that is resolved by calculating an MDX expression to return a value.</span></span> <span data-ttu-id="ca200-104">이러한 정의에는 놀랄 만한 개념이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ca200-104">This innocuous definition covers an incredible amount of ground.</span></span> <span data-ttu-id="ca200-105">MDX 쿼리에서 계산 멤버를 구성하고 사용할 수 있으면 다차원 데이터에 대한 상당한 조작 기능을 활용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ca200-105">The ability to construct and use calculated members in an MDX query provides a great deal of manipulation capability for multidimensional data.</span></span>  
  
 <span data-ttu-id="ca200-106">계산 멤버는 계층 구조 안의 어느 지점에나 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ca200-106">You can create calculated members at any point within a hierarchy.</span></span> <span data-ttu-id="ca200-107">또한, 큐브의 기존 멤버는 물론, 동일한 MDX 식에서 정의된 다른 계산 멤버에도 종속되는 계산 멤버를 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ca200-107">You can also create calculated members that depend not only on existing members in a cube, but also on other calculated members defined in the same MDX expression.</span></span>  
  
 <span data-ttu-id="ca200-108">다음 컨텍스트 중 하나가 포함되도록 계산 멤버를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ca200-108">You can define a calculated member to have one of the following contexts:</span></span>  
  
-   <span data-ttu-id="ca200-109">**쿼리 범위** MDX 쿼리의 일부로 정의되는 계산 멤버를 만들어서 해당 범위가 쿼리로 제한되도록 하려면 WITH 키워드를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ca200-109">**Query-scoped** To create a calculated member that is defined as part of an MDX query, and therefore whose scope is limited to the query, you use the WITH keyword.</span></span> <span data-ttu-id="ca200-110">그런 다음 MDX SELECT 문 내에서 계산 멤버를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ca200-110">You can then use the calculated member within an MDX SELECT statement.</span></span> <span data-ttu-id="ca200-111">이 방식을 사용할 경우 WITH 키워드를 사용하여 만든 계산 멤버는 SELECT 문을 배포하지 않아도 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ca200-111">Using this approach, the calculated member created by using the WITH keyword can be changed without disturbing the SELECT statement.</span></span>  
  
     <span data-ttu-id="ca200-112">WITH 키워드를 사용하여 계산 멤버를 만드는 방법은 [쿼리 범위 계산 멤버 만들기&#40;MDX&#41;](mdx-calculated-members-query-scoped-calculated-members.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ca200-112">For more information about how to use the WITH keyword to create calculated members, see [Creating Query-Scoped Calculated Members &#40;MDX&#41;](mdx-calculated-members-query-scoped-calculated-members.md).</span></span>  
  
-   <span data-ttu-id="ca200-113">**세션 범위** 범위가 쿼리 컨텍스트보다 넓은, 즉 범위가 MDX 세션의 수명인 계산 멤버를 만들려면 CREATE MEMBER 문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ca200-113">**Session-scoped** To create a calculated member whose scope is wider than the context of the query, that is, whose scope is the lifetime of the MDX session, you use the CREATE MEMBER statement.</span></span> <span data-ttu-id="ca200-114">CREATE MEMBER 문을 사용하여 정의된 계산 멤버는 해당 세션의 모든 MDX 쿼리에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ca200-114">A calculated member defined by using the CREATE MEMBER statement is available to all MDX queries in that session.</span></span> <span data-ttu-id="ca200-115">예를 들어 CREATE MEMBER 문은 여러 쿼리에서 하나의 동일 집합을 계속적으로 다시 사용하는 클라이언트 애플리케이션에 적합합니다.</span><span class="sxs-lookup"><span data-stu-id="ca200-115">The CREATE MEMBER statement makes sense, for example, in a client application that consistently reuses the same set in a variety of queries.</span></span>  
  
     <span data-ttu-id="ca200-116">CREATE MEMBER 문을 사용하여 세션에서 계산 멤버를 만드는 방법은 [세션 범위 계산 멤버 만들기&#40;MDX&#41;](mdx-calculated-members-session-scoped-calculated-members.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ca200-116">For more information about how to use the CREATE MEMBER statement to create calculated members in a session, see [Creating Session-Scoped Calculated Members &#40;MDX&#41;](mdx-calculated-members-session-scoped-calculated-members.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca200-117">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ca200-117">See Also</span></span>  
 <span data-ttu-id="ca200-118">[CREATE MEMBER 문 &#40;MDX&#41;](/sql/mdx/mdx-data-definition-create-member) </span><span class="sxs-lookup"><span data-stu-id="ca200-118">[CREATE MEMBER Statement &#40;MDX&#41;](/sql/mdx/mdx-data-definition-create-member) </span></span>  
 <span data-ttu-id="ca200-119">[Mdx 함수 참조 &#40;MDX&#41;](/sql/mdx/mdx-function-reference-mdx) </span><span class="sxs-lookup"><span data-stu-id="ca200-119">[MDX Function Reference &#40;MDX&#41;](/sql/mdx/mdx-function-reference-mdx) </span></span>  
 [<span data-ttu-id="ca200-120">SELECT 문&#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="ca200-120">SELECT Statement &#40;MDX&#41;</span></span>](/sql/mdx/mdx-data-manipulation-select)  
  
  
