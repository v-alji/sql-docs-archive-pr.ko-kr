---
title: 세션 범위 계산 멤버 만들기 (MDX) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- CREATE MEMBER statement
- session-scoped calculated members [MDX]
ms.assetid: 2875ed89-2c26-4645-8ed9-8848479d110f
author: minewiskan
ms.author: owend
ms.openlocfilehash: 8fe7a9f137d8b74eaa5bad104dbfdb471dd14588
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653613"
---
# <a name="creating-session-scoped-calculated-members-mdx"></a><span data-ttu-id="135f1-102">세션 범위 계산 멤버 만들기(MDX)</span><span class="sxs-lookup"><span data-stu-id="135f1-102">Creating Session-Scoped Calculated Members (MDX)</span></span>
  <span data-ttu-id="135f1-103">MDX 세션 전체에서 사용할 수 있는 계산 멤버를 만들려면 [CREATE MEMBER](/sql/mdx/mdx-data-definition-create-member) 문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="135f1-103">To create a calculated member that is available throughout a Multidimensional Expressions (MDX) session, you use the [CREATE MEMBER](/sql/mdx/mdx-data-definition-create-member) statement.</span></span> <span data-ttu-id="135f1-104">CREATE MEMBER 문을 사용하여 만든 계산 멤버는 MDX 세션이 닫힌 후까지 제거되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="135f1-104">A calculated member that is created by using the CREATE MEMBER statement will not be removed until after the MDX session closes.</span></span>  
  
 <span data-ttu-id="135f1-105">이 항목에서 설명한 바와 같이 CREATE MEMBER 문의 구문은 간단하고 사용하기 쉽습니다.</span><span class="sxs-lookup"><span data-stu-id="135f1-105">As discussed in this topic, the syntax of the CREATE MEMBER statement is straightforward and easy to use.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="135f1-106">계산 멤버에 대한 자세한 내용은 [계산 멤버를 MDX로 작성&#40;MDX&#41;](mdx-calculated-members-building-calculated-members.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="135f1-106">For more information about calculated members, see [Building Calculated Members in MDX &#40;MDX&#41;](mdx-calculated-members-building-calculated-members.md).</span></span>  
  
## <a name="create-member-syntax"></a><span data-ttu-id="135f1-107">CREATE MEMBER 구문</span><span class="sxs-lookup"><span data-stu-id="135f1-107">CREATE MEMBER Syntax</span></span>  
 <span data-ttu-id="135f1-108">다음 구문을 사용하여 CREATE MEMBER 문을 MDX 문에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="135f1-108">Use the following syntax to add the CREATE MEMBER statement to the MDX statement:</span></span>  
  
```  
CREATE [SESSION] MEMBER [<cube-name>.]<fully-qualified-member-name> AS <expression> [,<property-definition-list>]  
<cube name> ::= CURRENTCUBE | <Cube Name>  
<property-definition-list> ::= <property-definition>  
  | <property-definition>, <property-definition-list>  
<property-definition> ::= <property-identifier> = <property-value>  
<property-identifier> ::= VISIBLE | SOLVEORDER | SOLVE_ORDER | FORMAT_STRING | NON_EMPTY_BEHAVIOR <ole db member properties>  
```  
  
 <span data-ttu-id="135f1-109">CREATE MEMBER 문에 대한 구문에서 `fully-qualified-member-name` 값은 계산 멤버의 정규화된 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="135f1-109">In the syntax for the CREATE MEMBER statement, the `fully-qualified-member-name` value is the fully qualified name of the calculated member.</span></span> <span data-ttu-id="135f1-110">이 정규화된 이름에는 계산 멤버가 연결된 차원 또는 수준이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="135f1-110">The fully qualified name includes the dimension or level to which the calculated member is associated.</span></span> <span data-ttu-id="135f1-111">`expression` 값은 식 값이 계산된 후의 계산 멤버의 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="135f1-111">The `expression` value returns the value of the calculated member after the expression value has been evaluated,.</span></span>  
  
## <a name="create-member-example"></a><span data-ttu-id="135f1-112">CREATE MEMBER 예</span><span class="sxs-lookup"><span data-stu-id="135f1-112">CREATE MEMBER Example</span></span>  
 <span data-ttu-id="135f1-113">다음 예에서는 CREATE MEMBER 문을 사용하여 `LastFourStores` 계산 멤버를 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="135f1-113">The following example uses the CREATE MEMBER statement to create the `LastFourStores` calculated member.</span></span> <span data-ttu-id="135f1-114">이 계산 멤버는 마지막 4개 매장에서 팔린 합계를 반환하고 큐브의 전체 세션에서 사용될 것입니다.</span><span class="sxs-lookup"><span data-stu-id="135f1-114">This calculated member returns the sum of units sold for the last four stores, and will be available throughout the whole session of the cube.</span></span>  
  
```  
Create Session Member [Store].[Measures].LastFourStores as   
sum(([Stores].[ByLocation].Lag(3) :  
[Stores].[ByLocation].NextMember), [Measures].[Units Sold])  
```  
  
## <a name="see-also"></a><span data-ttu-id="135f1-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="135f1-115">See Also</span></span>  
 [<span data-ttu-id="135f1-116">쿼리 범위 계산 멤버 만들기&#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="135f1-116">Creating Query-Scoped Calculated Members &#40;MDX&#41;</span></span>](mdx-calculated-members-query-scoped-calculated-members.md)  
  
  
