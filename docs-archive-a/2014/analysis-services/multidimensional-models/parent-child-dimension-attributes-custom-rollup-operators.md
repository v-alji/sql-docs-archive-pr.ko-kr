---
title: 부모-자식 차원의 사용자 지정 롤업 연산자 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- child rollup operations
- UnaryOperatorColumn property
- custom rollup operators [Analysis Services]
- unary operators
- parent-child dimensions [Analysis Services]
ms.assetid: a3ddd9fc-5fa3-4227-9322-8c45a5b5c2c3
author: minewiskan
ms.author: owend
ms.openlocfilehash: db12ccc6703ee4863dd3b6bd598d2317b54fce6a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652404"
---
# <a name="custom-rollup-operators-in-parent-child-dimensions"></a><span data-ttu-id="c6ee9-102">부모-자식 차원의 사용자 지정 롤업 연산자</span><span class="sxs-lookup"><span data-stu-id="c6ee9-102">Custom Rollup Operators in Parent-Child Dimensions</span></span>
  <span data-ttu-id="c6ee9-103">사용자 지정 롤업 연산자는 부모-자식 계층에서 멤버 값이 부모 값으로 롤업되는 방식을 제어할 수 있는 간단한 방법을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="c6ee9-103">Custom rollup operators provide a simple way to control how member values are rolled up into parent values in a parent-child hierarchy.</span></span> <span data-ttu-id="c6ee9-104">부모-자식 관계를 포함하는 차원에서 부모 특성의 모든 계산되지 않는 멤버에 대한 롤업을 지정하는 단항 연산자가 있는 열을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c6ee9-104">In a dimension containing a parent-child relationship, you specify a column that contains unary operators that specify rollup for all noncalculated members of the parent attribute.</span></span> <span data-ttu-id="c6ee9-105">그러면 부모 멤버의 값이 계산될 때마다 멤버에 단항 연산자가 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6ee9-105">The unary operator is applied to members whenever the values of the parent members are evaluated.</span></span>  
  
 <span data-ttu-id="c6ee9-106">단항 연산자는 부모 특성의 `UnaryOperatorColumn` 속성으로 정의되는 열에 저장되며 특성의 각 멤버에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6ee9-106">The unary operators are stored in column defined by the `UnaryOperatorColumn` property of the parent attribute, and they are applied to each member of the attribute.</span></span> <span data-ttu-id="c6ee9-107">이 속성으로 지정한 열은 차원 테이블에 있거나 차원 테이블의 외부 키로 차원 테이블과 관련된 테이블에 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c6ee9-107">The column specified by this property can reside either in the dimension table or in a table related to the dimension table by a foreign key in the dimension table.</span></span>  
  
 <span data-ttu-id="c6ee9-108">사용자 지정 롤업 연산자는 사용자 지정 멤버 수식과 비슷하지만 훨씬 단순한 기능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="c6ee9-108">Custom rollup operators provide functionality similar to, but more simplified than, custom member formulas.</span></span> <span data-ttu-id="c6ee9-109">사용자 지정 멤버 수식은 MDX(Multidimensional Expressions) 식을 사용하여 멤버 롤업 방식을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="c6ee9-109">A custom member formula uses Multidimensional Expressions (MDX) expressions to determine how the members are rolled up.</span></span> <span data-ttu-id="c6ee9-110">반면에 사용자 지정 롤업 연산자는 간단한 단항 연산자를 사용하여 멤버 값이 부모에 미치는 영향을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="c6ee9-110">In contrast, a custom rollup operator uses a simple unary operator to determine how the value of a member affects the parent.</span></span> <span data-ttu-id="c6ee9-111">차원에서 상위 수준의 사용자 지정 멤버 수식은 현재 수준의 사용자 지정 롤업 연산자를 재정의합니다.</span><span class="sxs-lookup"><span data-stu-id="c6ee9-111">Custom member formulas of the preceding level in a dimension override a level's custom rollup operator.</span></span>  
  
## <a name="custom-rollup-precedence"></a><span data-ttu-id="c6ee9-112">사용자 지정 롤업 선행 규칙</span><span class="sxs-lookup"><span data-stu-id="c6ee9-112">Custom Rollup Precedence</span></span>  
 <span data-ttu-id="c6ee9-113">선행 규칙에 따라, 계층 구조에서 현재 수준의 원본 특성에 대한 사용자 지정 롤업 연산자는 상위 수준의 사용자 지정 멤버 수식을 재정의합니다.</span><span class="sxs-lookup"><span data-stu-id="c6ee9-113">In terms of precedence, the custom rollup operators of the source attribute for a level in a hierarchy override the custom member formulas of the previous level.</span></span> <span data-ttu-id="c6ee9-114">그러나 현재 수준의 사용자 지정 롤업 연산자는 상위 수준의 사용자 지정 멤버 수식에 의해 재정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6ee9-114">However, the custom member formulas of the preceding level override the custom rollup operators of a level.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6ee9-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c6ee9-115">See Also</span></span>  
 <span data-ttu-id="c6ee9-116">[사용자 지정 멤버 수식 정의](attribute-properties-define-custom-member-formulas.md) </span><span class="sxs-lookup"><span data-stu-id="c6ee9-116">[Define Custom Member Formulas](attribute-properties-define-custom-member-formulas.md) </span></span>  
 [<span data-ttu-id="c6ee9-117">부모-자식 차원의 단항 연산자</span><span class="sxs-lookup"><span data-stu-id="c6ee9-117">Unary Operators in Parent-Child Dimensions</span></span>](parent-child-dimension-attributes-unary-operators.md)  
  
  
