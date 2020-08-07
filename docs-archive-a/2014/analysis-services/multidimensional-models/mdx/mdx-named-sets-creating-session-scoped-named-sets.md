---
title: 세션 범위 명명 된 집합 만들기 (MDX) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- CREATE SET statement
- session-scoped named sets [MDX]
ms.assetid: b751e1e4-6d4c-4d36-a28d-ffdaaee0f1c7
author: minewiskan
ms.author: owend
ms.openlocfilehash: d35bd61dcc59eca8bcb920ed99f2e791631047c7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734500"
---
# <a name="creating-session-scoped-named-sets-mdx"></a><span data-ttu-id="be105-102">세션 범위 명명된 집합 만들기(MDX)</span><span class="sxs-lookup"><span data-stu-id="be105-102">Creating Session-Scoped Named Sets (MDX)</span></span>
  <span data-ttu-id="be105-103">MDX 세션에서 사용할 수 있는 명명된 집합을 만들려면 [CREATE SET](/sql/mdx/mdx-data-definition-create-set) 문을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="be105-103">To create a named set that is available throughout a Multidimensional Expressions (MDX) session, you use the [CREATE SET](/sql/mdx/mdx-data-definition-create-set) statement.</span></span> <span data-ttu-id="be105-104">CREATE SET 문으로 작성한 명명된 집합은 MDX 세션이 종료된 뒤에도 제거되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="be105-104">A named set that is created by using the CREATE SET statement will not be removed until after the MDX session closes.</span></span>  
  
 <span data-ttu-id="be105-105">이 항목에서 설명되겠지만 WITH 키워드의 구문은 간단하며 사용하기 쉽습니다.</span><span class="sxs-lookup"><span data-stu-id="be105-105">As discussed in this topic, the syntax of the WITH keyword is straightforward and easy to use.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="be105-106">명명된 집합에 대한 자세한 내용은 [명명된 집합을 MDX로 작성&#40;MDX&#41;](mdx-named-sets-building-named-sets.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="be105-106">For more information about named sets, see [Building Named Sets in MDX &#40;MDX&#41;](mdx-named-sets-building-named-sets.md).</span></span>  
  
## <a name="create-set-syntax"></a><span data-ttu-id="be105-107">CREATE SET 구문</span><span class="sxs-lookup"><span data-stu-id="be105-107">CREATE SET Syntax</span></span>  
 <span data-ttu-id="be105-108">CREATE SET 문의 구문은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="be105-108">Use the following syntax for the CREATE SET statement:</span></span>  
  
```  
CREATE SESSION SET [CURRENTCUBE. | <cube name>.]<Set Identifier> AS <Set Expression>  
```  
  
 <span data-ttu-id="be105-109">CREATE SET 구문에서 `cube name` 매개 변수는 명명된 집합의 멤버를 포함하는 큐브의 이름을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="be105-109">In the CREATE SET syntax, the `cube name` parameter contains the name of the cube that contains the members for the named set.</span></span> <span data-ttu-id="be105-110">`cube name` 매개 변수를 지정하지 않으면 명명된 집합의 멤버를 포함하는 큐브로 현재 큐브를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="be105-110">If the `cube name` parameter is not specified, the current cube will be used as the cube that contains the member for the named set.</span></span> <span data-ttu-id="be105-111">또한 `Set_Identifier` 매개 변수는 명명된 집합의 별칭을 포함하며 `Set_Expression` 매개 변수는 명명된 집합 별칭이 참조할 집합 식을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="be105-111">Also, the `Set_Identifier` parameter contains the alias for the named set, and the `Set_Expression` parameter contains the set expression to which the named set alias will refer.</span></span>  
  
## <a name="create-set-example"></a><span data-ttu-id="be105-112">CREATE SET 예</span><span class="sxs-lookup"><span data-stu-id="be105-112">CREATE SET Example</span></span>  
 <span data-ttu-id="be105-113">다음 예에서는 CREATE SET 문을 사용하여 Store 큐브를 바탕으로 `SetCities_2_3` 으로 명명된 집합을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="be105-113">The following example uses the CREATE SET statement to create the `SetCities_2_3` named set based on the Store cube.</span></span> <span data-ttu-id="be105-114">City 2 및 City 3의 상점이 `SetCities_2_3` 으로 명명된 집합의 멤버가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="be105-114">The members of the `SetCities_2_3` named set are the stores within City 2 and City 3.</span></span>  
  
```  
create Session set [Store].[SetCities_2_3] as  
{[Data Stores].[ByLocation].[State].&[CA].&[City 02],  
[Data Stores].[ByLocation].[State].&[NH].&[City 03]}  
```  
  
 <span data-ttu-id="be105-115">CREATE SET 문을 사용하여 정의한 `SetCities_2_3` 명명된 집합은 현재 MDX 세션이 유지되는 동안 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="be105-115">By using the CREATE SET statement to define the `SetCities_2_3` named set, this named set remains available for the length of the current MDX session.</span></span> <span data-ttu-id="be105-116">다음 예는 City 2 및 City 3 멤버를 반환하는 유효한 쿼리이며 `SetCities_2_3` 으로 명명된 집합을 만든 뒤 세션을 종료하기 전까지 언제든지 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="be105-116">The following example is a valid query that would return City 2 and City 3 members, and that could be run anytime after you create the `SetCities_2_3` named set and before the session closes.</span></span>  
  
```  
select SetCities_2_3 on 0 from [Store]  
```  
  
## <a name="see-also"></a><span data-ttu-id="be105-117">참고 항목</span><span class="sxs-lookup"><span data-stu-id="be105-117">See Also</span></span>  
 [<span data-ttu-id="be105-118">쿼리 범위 명명된 집합 만들기&#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="be105-118">Creating Query-Scoped Named Sets &#40;MDX&#41;</span></span>](mdx-named-sets-creating-query-scoped-named-sets.md)  
  
  
