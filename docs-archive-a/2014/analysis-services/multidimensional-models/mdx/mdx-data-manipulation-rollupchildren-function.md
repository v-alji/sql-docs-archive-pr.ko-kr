---
title: RollupChildren 함수 (MDX) 작업 Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- queries [MDX], RollupChildren function
- RollupChildren function
- custom member properties [MDX]
- IIf function
ms.assetid: 03c624d4-f277-451d-9995-623a07ea2f86
author: minewiskan
ms.author: owend
ms.openlocfilehash: 341468d521cebe1fda33d73ea999f3b6571cb01e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737036"
---
# <a name="working-with-the-rollupchildren-function-mdx"></a><span data-ttu-id="5be94-102">RollupChildren 함수 작업(MDX)</span><span class="sxs-lookup"><span data-stu-id="5be94-102">Working with the RollupChildren Function (MDX)</span></span>
  <span data-ttu-id="5be94-103">MDX (Multidimensional Expressions) [RollupChildren](/sql/mdx/rollupchildren-mdx) [Search 및 Replace 스크립팅] 함수는 멤버의 자식을 롤업 하 고 각 자식에 다른 단항 연산자를 적용 하 고이 롤업 값을 숫자로 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="5be94-103">The Multidimensional Expressions (MDX) [RollupChildren](/sql/mdx/rollupchildren-mdx) [Script for Search and Replace] function rolls up the children of a member, applying a different unary operator to each child, and returns the value of this rollup as a number.</span></span> <span data-ttu-id="5be94-104">자식 멤버와 관련된 멤버 속성에서 단항 연산자를 제공하거나 함수에 직접 제공되는 문자열 식이 단항 연산자가 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5be94-104">The unary operator can be supplied by a member property associated with the child member, or the operator can be a string expression provided directly to the function.</span></span>  
  
## <a name="rollupchildren-function-examples"></a><span data-ttu-id="5be94-105">RollupChildren 함수 예</span><span class="sxs-lookup"><span data-stu-id="5be94-105">RollupChildren Function Examples</span></span>  
 <span data-ttu-id="5be94-106">MDX 문에서 `RollupChildren` 함수를 사용하는 방법을 설명하기는 쉽지만 MDX 쿼리에 미치는 이 함수의 효과는 매우 다양할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5be94-106">The use of the `RollupChildren` function in Multidimensional Expressions (MDX) statements is simple to explain, but the effect of this function on MDX queries can be wide-ranging.</span></span>  
  
 <span data-ttu-id="5be94-107">`RollupChildren` 함수의 효과는 기존의 큐브 데이터에 대한 선택적인 분석을 수행하도록 디자인된 MDX 쿼리에서 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="5be94-107">The effect of the `RollupChildren` function occurs in MDX queries designed to perform selective analysis on existing cube data.</span></span> <span data-ttu-id="5be94-108">예를 들어 다음 테이블에는 괄호로 표시된 단항 연산자(`UNARY_OPERATOR` 멤버 속성에 의해 표현됨)와 함께 Net Sales 부모 멤버에 대한 자식 멤버 목록이 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5be94-108">For example, the following table contains a list of child members for the Net Sales parent member, with their unary operators (represented by the `UNARY_OPERATOR` member property) shown in parentheses.</span></span>  
  
|<span data-ttu-id="5be94-109">부모 멤버</span><span class="sxs-lookup"><span data-stu-id="5be94-109">Parent member</span></span>|<span data-ttu-id="5be94-110">자식 멤버</span><span class="sxs-lookup"><span data-stu-id="5be94-110">Child member</span></span>|  
|-------------------|------------------|  
|<span data-ttu-id="5be94-111">순매출액</span><span class="sxs-lookup"><span data-stu-id="5be94-111">Net Sales</span></span>|<span data-ttu-id="5be94-112">Domestic Sales (+)</span><span class="sxs-lookup"><span data-stu-id="5be94-112">Domestic Sales (+)</span></span><br /><br /> <span data-ttu-id="5be94-113">Domestic Returns (-)</span><span class="sxs-lookup"><span data-stu-id="5be94-113">Domestic Returns (-)</span></span><br /><br /> <span data-ttu-id="5be94-114">Foreign Sales (+)</span><span class="sxs-lookup"><span data-stu-id="5be94-114">Foreign Sales (+)</span></span><br /><br /> <span data-ttu-id="5be94-115">Foreign Returns (-)</span><span class="sxs-lookup"><span data-stu-id="5be94-115">Foreign Returns (-)</span></span>|  
  
 <span data-ttu-id="5be94-116">Net Sales 부모 멤버는 현재 롤업의 일부로서 국내 및 해외 수입을 뺀 상태에서 순매출액 합계에서 국내 및 해외 총 판매액을 뺀 값을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="5be94-116">The Net Sales parent member currently provides a total of net sales minus the gross domestic and foreign sales values, with the domestic and foreign returns subtracted as part of the rollup.</span></span>  
  
 <span data-ttu-id="5be94-117">하지만 국내 및 해외 수입을 무시하고 국내 및 해외 총 판매액에 10%를 더한 값으로 빠르고 쉽게 전망치를 제공하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="5be94-117">However, you want to provide a quick and easy forecast of domestic and foreign gross sales plus 10%, ignoring the domestic and foreign returns.</span></span> <span data-ttu-id="5be94-118">`RollupChildren` 함수를 사용하여 이 값을 계산할 수 있는 방법에는 사용자 지정 멤버 속성으로 계산하거나 `IIf` 함수로 계산하는 두 가지 방법이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5be94-118">To calculate this value, you can use the `RollupChildren` function in one of two ways: with a custom member property or with the `IIf` function.</span></span>  
  
### <a name="using-a-custom-member-property"></a><span data-ttu-id="5be94-119">사용자 지정 멤버 속성 사용</span><span class="sxs-lookup"><span data-stu-id="5be94-119">Using a Custom Member Property</span></span>  
 <span data-ttu-id="5be94-120">롤업 계산이 자주 수행되는 연산인 경우에는 특정 함수에 대한 각 자식에 사용될 연산자를 저장하는 멤버 속성을 만드는 것이 한 가지 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="5be94-120">If the rollup calculation is to be a frequently performed operation, one method is to create a member property that stores the operator that will be used for each child for a specific function.</span></span> <span data-ttu-id="5be94-121">다음 테이블에서는 유효한 단항 연산자를 표시하고 예상 결과를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="5be94-121">The following table displays valid unary operators and describes the expected result.</span></span>  
  
|<span data-ttu-id="5be94-122">연산자</span><span class="sxs-lookup"><span data-stu-id="5be94-122">Operator</span></span>|<span data-ttu-id="5be94-123">결과</span><span class="sxs-lookup"><span data-stu-id="5be94-123">Result</span></span>|  
|--------------|------------|  
|+|<span data-ttu-id="5be94-124">합계 = 합계 + 현재 자식 항목</span><span class="sxs-lookup"><span data-stu-id="5be94-124">total = total + current child</span></span>|  
|-|<span data-ttu-id="5be94-125">합계 = 합계 - 현재 자식 항목</span><span class="sxs-lookup"><span data-stu-id="5be94-125">total = total - current child</span></span>|  
|*|<span data-ttu-id="5be94-126">합계 = 합계 \* 현재 자식 항목</span><span class="sxs-lookup"><span data-stu-id="5be94-126">total = total \* current child</span></span>|  
|/|<span data-ttu-id="5be94-127">합계 = 합계 / 현재 자식 항목</span><span class="sxs-lookup"><span data-stu-id="5be94-127">total = total / current child</span></span>|  
|~|<span data-ttu-id="5be94-128">자식 항목을 롤업에 사용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5be94-128">Child is not used in the rollup.</span></span> <span data-ttu-id="5be94-129">자식 값을 무시합니다.</span><span class="sxs-lookup"><span data-stu-id="5be94-129">The child's value is ignored.</span></span>|  
  
 <span data-ttu-id="5be94-130">예를 들어 `SALES_OPERATOR`라는 멤버 속성을 만들 수 있으며 다음 테이블에 표시된 것과 같이 그 멤버 속성에 다음의 단항 연산자가 할당됩니다.</span><span class="sxs-lookup"><span data-stu-id="5be94-130">For example, a member property called `SALES_OPERATOR` could be created, and the following unary operators would be assigned to that member property, as shown in the following table.</span></span>  
  
|<span data-ttu-id="5be94-131">부모 멤버</span><span class="sxs-lookup"><span data-stu-id="5be94-131">Parent member</span></span>|<span data-ttu-id="5be94-132">자식 멤버</span><span class="sxs-lookup"><span data-stu-id="5be94-132">Child member</span></span>|  
|-------------------|------------------|  
|<span data-ttu-id="5be94-133">순매출액</span><span class="sxs-lookup"><span data-stu-id="5be94-133">Net Sales</span></span>|<span data-ttu-id="5be94-134">Domestic Sales (+)</span><span class="sxs-lookup"><span data-stu-id="5be94-134">Domestic Sales (+)</span></span><br /><br /> <span data-ttu-id="5be94-135">Domestic Returns (~)</span><span class="sxs-lookup"><span data-stu-id="5be94-135">Domestic Returns (~)</span></span><br /><br /> <span data-ttu-id="5be94-136">Foreign Sales (+)</span><span class="sxs-lookup"><span data-stu-id="5be94-136">Foreign Sales (+)</span></span><br /><br /> <span data-ttu-id="5be94-137">Foreign Returns (~)</span><span class="sxs-lookup"><span data-stu-id="5be94-137">Foreign Returns (~)</span></span>|  
  
 <span data-ttu-id="5be94-138">이 새 멤버 속성으로 다음 MDX 문은 총 판매액 추산 연산을 빠르고 효율적으로 수행하게 됩니다(해외 및 국내 수입은 무시).</span><span class="sxs-lookup"><span data-stu-id="5be94-138">With this new member property, the following MDX statement would perform the gross sales estimate operation quickly and efficiently (ignoring Foreign and Domestic returns):</span></span>  
  
```  
RollupChildren([Net Sales], [Net Sales].CurrentMember.Properties("SALES_OPERATOR")) * 1.1  
```  
  
 <span data-ttu-id="5be94-139">이 함수를 호출하면 멤버 속성에 저장된 연산자를 사용하여 각 자식의 값을 합계에 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="5be94-139">When the function is called, the value of each child is applied to a total using the operator stored in the member property.</span></span> <span data-ttu-id="5be94-140">국내 및 해외 수입에 대한 멤버를 무시하고 `RollupChildren` 함수가 반환한 롤업 합계에 1.1을 곱합니다.</span><span class="sxs-lookup"><span data-stu-id="5be94-140">The members for domestic and foreign returns are ignored, and the rollup total returned by the `RollupChildren` function is multiplied by 1.1.</span></span>  
  
### <a name="using-the-iif-function"></a><span data-ttu-id="5be94-141">IIf 함수 사용</span><span class="sxs-lookup"><span data-stu-id="5be94-141">Using the IIf Function</span></span>  
 <span data-ttu-id="5be94-142">예를 들어 작업이 일반적이 지 않거나 연산이 하나의 MDX 쿼리에만 적용 되는 경우 [IIf](/sql/mdx/iif-mdx) 함수를 함수와 함께 사용 `RollupChildren` 하 여 동일한 결과를 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5be94-142">If the example operation is not commonplace or if the operation applies only to one MDX query, the [IIf](/sql/mdx/iif-mdx) function can be used with the `RollupChildren` function to provide the same result.</span></span> <span data-ttu-id="5be94-143">다음 MDX 쿼리를 이용하면 사용자 지정 멤버 속성을 사용하지 않고도 앞선 예로 든 MDX와 같은 결과가 나옵니다.</span><span class="sxs-lookup"><span data-stu-id="5be94-143">The following MDX query provides the same result as the earlier MDX example, but does so without resorting to the use of a custom member property:</span></span>  
  
```  
RollupChildren([Net Sales], IIf([Net Sales].CurrentMember.Properties("UNARY_OPERATOR") = "-", "~", [Net Sales].CurrentMember.Properties("UNARY_OPERATOR))) * 1.1  
```  
  
 <span data-ttu-id="5be94-144">이 MDX 문은 자식 멤버의 단항 연산자를 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="5be94-144">The MDX statement examines the unary operator of the child member.</span></span> <span data-ttu-id="5be94-145">국내 및 해외 수입 멤버의 경우에서와 같이 단항 연산자를 빼기에 사용하는 경우 `IIf` 함수가 물결표(~) 단항 연산자를 대체합니다.</span><span class="sxs-lookup"><span data-stu-id="5be94-145">If the unary operator is used for subtraction (as in the case with the domestic and foreign returns members), the `IIf` function substitutes the tilde (~) unary operator.</span></span> <span data-ttu-id="5be94-146">그렇지 않으면 `IIf` 함수는 자식 멤버의 단항 연산자를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="5be94-146">Otherwise, the `IIf` function uses the unary operator of the child member.</span></span> <span data-ttu-id="5be94-147">마지막으로 반환된 롤업 합계에 1.1을 곱하면 국내 및 해외 총 판매 예측 값이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5be94-147">Finally, the returned rollup total is then multiplied by 1.1 to provide the domestic and foreign gross sales forecast value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5be94-148">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5be94-148">See Also</span></span>  
 [<span data-ttu-id="5be94-149">데이터 조작&#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="5be94-149">Manipulating Data &#40;MDX&#41;</span></span>](mdx-data-manipulation-manipulating-data.md)  
  
  
