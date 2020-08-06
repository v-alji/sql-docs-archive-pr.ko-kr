---
title: MDX로 하위 큐브 작성 (MDX) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- queries [MDX], subcubes
- subcubes [MDX]
- filtered views [MDX]
- MDX [Analysis Services], subcubes
- Multidimensional Expressions [Analysis Services], subcubes
- CREATE SUBCUBE statement
ms.assetid: 5403a62b-99ac-4d83-b02a-89bf78bf0f46
author: minewiskan
ms.author: owend
ms.openlocfilehash: 653b4d30aa86f52179c7b13619ac4347aa65c339
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652412"
---
# <a name="building-subcubes-in-mdx-mdx"></a><span data-ttu-id="a3d32-102">MDX로 하위 큐브 작성(MDX)</span><span class="sxs-lookup"><span data-stu-id="a3d32-102">Building Subcubes in MDX (MDX)</span></span>
  <span data-ttu-id="a3d32-103">하위 큐브는 기본 데이터의 필터링된 뷰를 나타내는 큐브의 하위 집합입니다.</span><span class="sxs-lookup"><span data-stu-id="a3d32-103">A subcube is a subset of a cube on representing a filtered view of the underlying data.</span></span> <span data-ttu-id="a3d32-104">큐브를 하위 큐브로 제한하여 쿼리 성능을 높일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a3d32-104">By limiting the cube to a subcube, you can improve query performance.</span></span>  
  
 <span data-ttu-id="a3d32-105">하위 큐브를 정의하려면 이 항목에서 설명하는 바와 같이 [CREATE SUBCUBE](/sql/mdx/mdx-data-definition-create-subcube) 문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a3d32-105">To define a subcube, you use the [CREATE SUBCUBE](/sql/mdx/mdx-data-definition-create-subcube) statement, as described in this topic.</span></span>  
  
## <a name="create-subcube-syntax"></a><span data-ttu-id="a3d32-106">CREATE SUBCUBE 구문</span><span class="sxs-lookup"><span data-stu-id="a3d32-106">CREATE SUBCUBE Syntax</span></span>  
 <span data-ttu-id="a3d32-107">다음 구문을 사용하여 하위 큐브를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a3d32-107">Use the following syntax to create a subcube:</span></span>  
  
```  
CREATE SUBCUBE Subcube_Identifier AS Subcube_Expression  
```  
  
 <span data-ttu-id="a3d32-108">CREATE SUBCUBE 구문은 꽤 간단합니다.</span><span class="sxs-lookup"><span data-stu-id="a3d32-108">The CREATE SUBCUBE syntax is fairly simple.</span></span> <span data-ttu-id="a3d32-109">*Subcube_Identifier* 매개 변수는 하위 큐브의 기반이 되는 큐브를 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="a3d32-109">The *Subcube_Identifier* parameter identifies the cube on which the subcube will be based.</span></span> <span data-ttu-id="a3d32-110">*Subcube_Expression* 매개 변수는 하위 큐브가 될 큐브의 해당 부분을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a3d32-110">The *Subcube_Expression* parameter selects the part of the cube that will become the subcube</span></span>  
  
 <span data-ttu-id="a3d32-111">하위 큐브를 만들고 난 후 해당 하위 큐브는 세션을 닫거나 [DROP SUBCUBE](/sql/mdx/mdx-data-definition-drop-subcube) 문을 실행할 때까지는 모든 MDX 쿼리에 대한 컨텍스트가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a3d32-111">After you create a subcube, that subcube becomes the context for all MDX queries until either the session closes or you run the [DROP SUBCUBE](/sql/mdx/mdx-data-definition-drop-subcube) statement.</span></span>  
  
### <a name="what-a-subcube-contains"></a><span data-ttu-id="a3d32-112">하위 큐브가 포함하는 것</span><span class="sxs-lookup"><span data-stu-id="a3d32-112">What a Subcube Contains</span></span>  
 <span data-ttu-id="a3d32-113">CREATE SUBCUBE 문은 간단하게 사용할 수 있지만 이 문 자체가 하위 큐브의 일부가 되는 멤버들을 모두 명시적으로 표시하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a3d32-113">Although the CREATE SUBCUBE statement is fairly simple to use, the statement itself does not explicitly show all the members that become part of a subcube.</span></span> <span data-ttu-id="a3d32-114">하위 큐브를 정의할 때 다음 규칙을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="a3d32-114">In defining a subcube, the following rules apply:</span></span>  
  
-   <span data-ttu-id="a3d32-115">어떤 계층의 `(All)` 멤버를 포함하면 해당 계층의 모든 멤버가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="a3d32-115">If you include the `(All)` member of a hierarchy, you include every member of that hierarchy.</span></span>  
  
-   <span data-ttu-id="a3d32-116">임의의 멤버를 포함하면 해당 멤버의 상위 항목과 하위 항목이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="a3d32-116">If you include any member, you include that member's ascendants and descendants.</span></span>  
  
-   <span data-ttu-id="a3d32-117">어떤 계층의 모든 멤버를 포함하면 그 계층의 모든 멤버가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="a3d32-117">If you include every member from a level, you include all members from the hierarchy.</span></span> <span data-ttu-id="a3d32-118">다른 계층의 멤버가 해당 수준(예를 들어 고객을 포함하지 않은 도시와 같이 균형이 맞지 않는 계층)의 멤버와 공존하지 않는 경우에는 제외됩니다.</span><span class="sxs-lookup"><span data-stu-id="a3d32-118">Members from other hierarchies will be excluded if those members do not exist with members from the level (for example, an unbalanced hierarchy such as a city that does not contain customers).</span></span>  
  
-   <span data-ttu-id="a3d32-119">하위 큐브는 항상 큐브의 모든 `(All)` 멤버를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="a3d32-119">A subcube will always contain every `(All)` member from the cube.</span></span>  
  
 <span data-ttu-id="a3d32-120">또한 하위 큐브 내의 집계 값은 시각적으로 합쳐집니다.</span><span class="sxs-lookup"><span data-stu-id="a3d32-120">Additionally, aggregate values within the subcube are visually totaled.</span></span> <span data-ttu-id="a3d32-121">예를 들어 하위 큐브는 `USA`, `WA`및 `OR`을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="a3d32-121">For example, a subcube contains `USA`, `WA`, and `OR`.</span></span> <span data-ttu-id="a3d32-122">`USA` 및 `{WA,OR}` 이 하위 큐브에 의해 정의된 유일한 주이므로 `WA` 에 대한 집계 값은 `OR` 의 합계가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a3d32-122">The aggregate value for `USA` will be the sum of `{WA,OR}` because `WA` and `OR` are the only states defined by the subcube.</span></span> <span data-ttu-id="a3d32-123">다른 모든 주는 무시합니다.</span><span class="sxs-lookup"><span data-stu-id="a3d32-123">All other states will be ignored.</span></span>  
  
 <span data-ttu-id="a3d32-124">또한 하위 큐브 외부의 셀에 대한 명시적 참조는 전체 큐브의 컨텍스트에서 계산되는 셀 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="a3d32-124">Also, explicit references to cells outside the subcube return cell values that are evaluated in the context of the whole cube.</span></span> <span data-ttu-id="a3d32-125">예를 들어 현재 연도로 제한되는 하위 큐브를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a3d32-125">For example, you create a subcube that is limited to the current year.</span></span> <span data-ttu-id="a3d32-126">그런 다음 [ParallelPeriod](/sql/mdx/parallelperiod-mdx) 함수를 사용하여 현재 연도를 이전 연도와 비교합니다.</span><span class="sxs-lookup"><span data-stu-id="a3d32-126">You then use the [ParallelPeriod](/sql/mdx/parallelperiod-mdx) function to compare the current year to the previous year.</span></span> <span data-ttu-id="a3d32-127">이전 연도 값은 하위 큐브 외부에 있더라도 값의 차이가 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a3d32-127">The difference in values will be returned even though the previous year's value lies outside the subcube.</span></span>  
  
 <span data-ttu-id="a3d32-128">마지막으로 원래 컨텍스트를 덮어쓰지 않은 경우 하위 SELECT에서 계산된 집합 함수는 하위 SELECT의 컨텍스트에서 계산됩니다.</span><span class="sxs-lookup"><span data-stu-id="a3d32-128">Finally, if the original context is not overwritten, set functions evaluated in a subselect are evaluated in the context of the subselect.</span></span> <span data-ttu-id="a3d32-129">컨텍스트를 덮어쓴 경우 집합 함수는 전체 큐브의 컨텍스트에서 계산됩니다.</span><span class="sxs-lookup"><span data-stu-id="a3d32-129">If the context is overwritten, set functions are evaluated in the context of the whole cube.</span></span>  
  
## <a name="create-subcube-example"></a><span data-ttu-id="a3d32-130">CREATE SUBCUBE 예</span><span class="sxs-lookup"><span data-stu-id="a3d32-130">CREATE SUBCUBE Example</span></span>  
 <span data-ttu-id="a3d32-131">다음 예에서는 예산 큐브를 4200 및 4300 계정으로만 한정하는 하위 큐브를 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a3d32-131">The following example creates a subcube that restricts the Budget cube to only accounts 4200 and 4300:</span></span>  
  
 `CREATE SUBCUBE Budget AS SELECT {[Account].[Account].&[4200], [Account].[Account].&[4300] } ON 0 FROM Budget`  
  
 <span data-ttu-id="a3d32-132">해당 세션에 대한 하위 큐브를 만들면 이후의 쿼리는 전체 큐브가 아니라 그 하위 큐브에 대해서만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="a3d32-132">Having created a subcube for the session, any subsequent queries will be against the subcube, not the whole cube.</span></span> <span data-ttu-id="a3d32-133">예를 들어 다음 쿼리를 실행하십시오.</span><span class="sxs-lookup"><span data-stu-id="a3d32-133">For example, you run the following query.</span></span> <span data-ttu-id="a3d32-134">이 쿼리는 4200 및 4300 계정의 멤버만 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="a3d32-134">This query will only return members from accounts 4200 and 4300.</span></span>  
  
 `SELECT [Account].[Account].Members ON 0, Measures.Members ON 1 FROM Budget`  
  
## <a name="see-also"></a><span data-ttu-id="a3d32-135">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a3d32-135">See Also</span></span>  
 <span data-ttu-id="a3d32-136">[MDX&#41;&#40;쿼리에 큐브 컨텍스트 설정](establishing-cube-context-in-a-query-mdx.md) </span><span class="sxs-lookup"><span data-stu-id="a3d32-136">[Establishing Cube Context in a Query &#40;MDX&#41;](establishing-cube-context-in-a-query-mdx.md) </span></span>  
 [<span data-ttu-id="a3d32-137">MDX 쿼리 기본 사항&#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="a3d32-137">MDX Query Fundamentals &#40;Analysis Services&#41;</span></span>](mdx-query-fundamentals-analysis-services.md)  
  
  
