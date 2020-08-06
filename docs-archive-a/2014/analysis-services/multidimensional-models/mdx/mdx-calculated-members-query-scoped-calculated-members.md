---
title: 쿼리 범위 계산 멤버 만들기 (MDX) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- WITH keyword
- query-scoped calculated members [MDX]
ms.assetid: c4507149-e67b-4e5d-9192-cc911acd9adc
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9c0b3e7184f3cc6abd189344bbce1b6e1f948ebb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649735"
---
# <a name="creating-query-scoped-calculated-members-mdx"></a><span data-ttu-id="3d7cd-102">쿼리 범위 계산 멤버 만들기(MDX)</span><span class="sxs-lookup"><span data-stu-id="3d7cd-102">Creating Query-Scoped Calculated Members (MDX)</span></span>
  <span data-ttu-id="3d7cd-103">단일 MDX 쿼리에만 계산 멤버가 필요한 경우 WITH 키워드를 사용하여 해당 계산 멤버를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d7cd-103">If a calculated member is only required for a single Multidimensional Expressions (MDX) query, you can define that calculated member by using the WITH keyword.</span></span> <span data-ttu-id="3d7cd-104">WITH 키워드를 사용하여 만든 계산 멤버는 쿼리 실행이 종료된 다음에는 더 이상 존재하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3d7cd-104">A calculated member that is created by using the WITH keyword no longer exists after the query has finished running.</span></span>  
  
 <span data-ttu-id="3d7cd-105">이 항목의 설명에서와 같이 WITH 키워드의 구문은 매우 유연하기 때문에 다른 계산 멤버를 기반으로 계산 멤버를 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d7cd-105">As discussed in this topic, the syntax of the WITH keyword is quite flexible, even allowing a calculated member to be based on another calculated member.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3d7cd-106">계산 멤버에 대한 자세한 내용은 [계산 멤버를 MDX로 작성&#40;MDX&#41;](mdx-calculated-members-building-calculated-members.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3d7cd-106">For more information about calculated members, see [Building Calculated Members in MDX &#40;MDX&#41;](mdx-calculated-members-building-calculated-members.md).</span></span>  
  
## <a name="with-keyword-syntax"></a><span data-ttu-id="3d7cd-107">WITH 키워드 구문</span><span class="sxs-lookup"><span data-stu-id="3d7cd-107">WITH Keyword Syntax</span></span>  
 <span data-ttu-id="3d7cd-108">WITH 키워드를 MDX SELECT 문에 추가하려면 기본 구문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="3d7cd-108">Use the following syntax to add the WITH keyword to an MDX SELECT statement:</span></span>  
  
```  
[ WITH <SELECT WITH clause> [ , <SELECT WITH clause> ... ] ] SELECT [ * | ( <SELECT query axis clause> [ , <SELECT query axis clause> ... ] ) ]FROM <SELECT subcube clause> [ <SELECT slicer axis clause> ][ <SELECT cell property list clause> ]  
<SELECT WITH clause> ::=  
   ( [ CALCULATED ] MEMBER <CREATE MEMBER body clause>) | <CREATE MEMBER body clause> ::= Member_Identifier AS 'MDX_Expression'  
   [ <CREATE MEMBER property clause> [ , <CREATE MEMBER property clause> ... ] ]  
<CREATE MEMBER property clause> ::=  
   ( MemberProperty_Identifier = Scalar_Expression )  
  
```  
  
 <span data-ttu-id="3d7cd-109">WITH 키워드 구문에서 `Member_Identifier` 값은 계산 멤버의 정규화된 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="3d7cd-109">In the syntax for the WITH keyword, the `Member_Identifier` value is the fully qualified name of the calculated member.</span></span> <span data-ttu-id="3d7cd-110">이 정규화된 이름에는 계산 멤버가 연결된 차원 또는 수준이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="3d7cd-110">This fully qualified name includes the dimension or level to which the calculated member is associated.</span></span> <span data-ttu-id="3d7cd-111">`MDX_Expression` 값은 식 값이 계산된 후의 계산 멤버의 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="3d7cd-111">The `MDX_Expression` value returns the value of the calculated member after the expression value has been evaluated.</span></span> <span data-ttu-id="3d7cd-112">`MemberProperty_Identifier` 값의 셀 속성 이름과 `Scalar_Expression` 값의 셀 속성 값을 제공하여 계산 멤버에 대한 기본 셀 속성 값을 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d7cd-112">The values of intrinsic cell properties for a calculated member can be optionally specified by supplying the name of the cell property in the `MemberProperty_Identifier` value and the value of the cell property in the `Scalar_Expression` value.</span></span>  
  
## <a name="with-keyword-examples"></a><span data-ttu-id="3d7cd-113">WITH 키워드 예</span><span class="sxs-lookup"><span data-stu-id="3d7cd-113">WITH Keyword Examples</span></span>  
 <span data-ttu-id="3d7cd-114">다음 MDX 쿼리는 `[Measures].[Special Discount]`계산 멤버를 정의하여 원래 할인 가격을 기준으로 특별 할인 가격을 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="3d7cd-114">The following MDX query defines a calculated member, `[Measures].[Special Discount]`, calculating a special discount based on the original discount amount.</span></span>  
  
```  
WITH   
   MEMBER [Measures].[Special Discount] AS  
   [Measures].[Discount Amount] * 1.5  
SELECT   
   [Measures].[Special Discount] on COLUMNS,  
   NON EMPTY [Product].[Product].MEMBERS  ON Rows  
FROM [Adventure Works]  
WHERE [Product].[Category].[Bikes]  
```  
  
 <span data-ttu-id="3d7cd-115">계산 멤버는 계층 구조 안의 어느 지점에나 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d7cd-115">You can also create calculated members at any point within a hierarchy.</span></span> <span data-ttu-id="3d7cd-116">예를 들어 아래 MDX 쿼리에서는 가상의 Sales 큐브에 대해 `[BigSeller]` 계산 멤버를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="3d7cd-116">For example, the following MDX query defines the `[BigSeller]` calculated member for a hypothetical Sales cube.</span></span> <span data-ttu-id="3d7cd-117">이 계산 멤버는 지정된 상점의 맥주 및 포도주에 대한 단위 판매가 적어도 100.00 이상인지 여부를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="3d7cd-117">This calculated member determines whether a specified store has at least 100.00 in unit sales for beer and wine.</span></span> <span data-ttu-id="3d7cd-118">하지만 쿼리는 `[BigSeller]` 계산 멤버를 `[Product]` 차원의 자식 멤버로 만들지 않으며, 그 대신 `[Beer and Wine]` 멤버의 자식 멤버로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3d7cd-118">However, the query creates the `[BigSeller]` calculated member not as a child member of the `[Product]` dimension, but instead as a child member of the `[Beer and Wine]` member.</span></span>  
  
```  
WITH   
   MEMBER [Product].[Beer and Wine].[BigSeller] AS  
  IIf([Product].[Beer and Wine] > 100, "Yes","No")  
SELECT  
   {[Product].[BigSeller]} ON COLUMNS,  
   Store.[Store Name].Members ON ROWS  
FROM Sales  
  
```  
  
 <span data-ttu-id="3d7cd-119">계산 멤버는 큐브의 기존 멤버에 종속될 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3d7cd-119">Calculated members do not have to depend only on existing members in a cube.</span></span> <span data-ttu-id="3d7cd-120">계산 멤버는 또한 동일 MDX 식에서 정의된 다른 계산 멤버에 기반할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d7cd-120">Calculated member can also be based on other calculated members defined in the same MDX expression.</span></span> <span data-ttu-id="3d7cd-121">예를 들어 다음 MDX 쿼리는 첫 번째 계산 멤버인 `[Measures].[Special Discount]`에서 만든 값을 사용하여 두 번째 계산 멤버인 `[Measures].[Special Discounted Amount]`의 값을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="3d7cd-121">For example, the following MDX query uses the value created in the first calculated member, `[Measures].[Special Discount]`, to generate the value of the second calculated member, `[Measures].[Special Discounted Amount]`.</span></span>  
  
```  
WITH   
   MEMBER [Measures].[Special Discount] AS  
   [Measures].[Discount Percentage] * 1.5,   
   FORMAT_STRING = 'Percent'  
  
   MEMBER [Measures].[Special Discounted Amount] AS  
   [Measures].[Reseller Average Unit Price] * [Measures].[Special Discount],   
   FORMAT_STRING = 'Currency'  
  
SELECT   
   {[Measures].[Special Discount], [Measures].[Special Discounted Amount]} on COLUMNS,  
   NON EMPTY [Product].[Product].MEMBERS  ON Rows  
FROM [Adventure Works]  
WHERE [Product].[Category].[Bikes]  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="3d7cd-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3d7cd-122">See Also</span></span>  
 <span data-ttu-id="3d7cd-123">[Mdx 함수 참조 &#40;MDX&#41;](/sql/mdx/mdx-function-reference-mdx) </span><span class="sxs-lookup"><span data-stu-id="3d7cd-123">[MDX Function Reference &#40;MDX&#41;](/sql/mdx/mdx-function-reference-mdx) </span></span>  
 <span data-ttu-id="3d7cd-124">[SELECT 문 &#40;MDX&#41;](/sql/mdx/mdx-data-manipulation-select) </span><span class="sxs-lookup"><span data-stu-id="3d7cd-124">[SELECT Statement &#40;MDX&#41;](/sql/mdx/mdx-data-manipulation-select) </span></span>  
 [<span data-ttu-id="3d7cd-125">세션 범위 계산 멤버 만들기&#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="3d7cd-125">Creating Session-Scoped Calculated Members &#40;MDX&#41;</span></span>](mdx-calculated-members-session-scoped-calculated-members.md)  
  
  
