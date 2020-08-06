---
title: 쿼리 범위 명명 된 집합 만들기 (MDX) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- query-scoped named sets [MDX]
- WITH keyword
ms.assetid: 78bc1e9a-1bc4-4a5a-ab0b-cf430c8fbfe1
author: minewiskan
ms.author: owend
ms.openlocfilehash: 6eccb4e20fca03079a04a0219b07f6411b80a433
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730959"
---
# <a name="creating-query-scoped-named-sets-mdx"></a><span data-ttu-id="559ed-102">쿼리 범위 명명된 집합 만들기(MDX)</span><span class="sxs-lookup"><span data-stu-id="559ed-102">Creating Query-Scoped Named Sets (MDX)</span></span>
  <span data-ttu-id="559ed-103">단일 MDX 쿼리에만 명명된 집합이 필요한 경우 WITH 키워드를 사용하여 해당 명명된 집합을 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="559ed-103">If a named set is only required for a single Multidimensional Expressions (MDX) query, you can define that named set by using the WITH keyword.</span></span> <span data-ttu-id="559ed-104">WITH 키워드를 사용하여 만든 명명된 집합은 쿼리 실행이 종료된 다음에는 더 이상 존재하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="559ed-104">A named set that is created by using the WITH keyword no longer exists after the query has finished running.</span></span>  
  
 <span data-ttu-id="559ed-105">이 항목의 설명에서와 같이 WITH 키워드의 구문은 매우 유연하기 때문에 명명된 집합을 정의하는 함수를 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="559ed-105">As discussed in this topic, the syntax of the WITH keyword is quite flexible, even accommodating the use of functions to define the named set.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="559ed-106">명명된 집합에 대한 자세한 내용은 [명명된 집합을 MDX로 작성&#40;MDX&#41;](mdx-named-sets-building-named-sets.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="559ed-106">For more information about named sets, see [Building Named Sets in MDX &#40;MDX&#41;](mdx-named-sets-building-named-sets.md).</span></span>  
  
## <a name="with-keyword-syntax"></a><span data-ttu-id="559ed-107">WITH 키워드 구문</span><span class="sxs-lookup"><span data-stu-id="559ed-107">WITH Keyword Syntax</span></span>  
 <span data-ttu-id="559ed-108">WITH 키워드를 MDX SELECT 문에 추가하려면 기본 구문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="559ed-108">Use the following syntax to add the WITH keyword to a MDX SELECT statement:</span></span>  
  
```  
[ WITH <SELECT WITH clause> [ , <SELECT WITH clause> ... ] ]   
SELECT [ * | ( <SELECT query axis clause> [ , <SELECT query axis clause> ... ] ) ]  
FROM <SELECT subcube clause>   
[ <SELECT slicer axis clause> ]  
[ <SELECT cell property list clause> ]  
  
<SELECT WITH clause> ::=  
   ( SET Set_Identifier AS 'Set_Expression')  
  
```  
  
 <span data-ttu-id="559ed-109">WITH 키워드에 대한 구문에서 `Set_Identifier` 매개 변수에는 명명된 집합에 대한 별칭이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="559ed-109">In the syntax for the WITH keyword, the `Set_Identifier` parameter contains the alias for the named set.</span></span> <span data-ttu-id="559ed-110">`Set_Expression` 매개 변수에는 명명된 집합 별칭이 참조할 집합 식이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="559ed-110">The `Set_Expression` parameter contains the set expression to which the named set alias refers.</span></span>  
  
## <a name="with-keyword-example"></a><span data-ttu-id="559ed-111">WITH 키워드 예</span><span class="sxs-lookup"><span data-stu-id="559ed-111">WITH Keyword Example</span></span>  
 <span data-ttu-id="559ed-112">다음 MDX 쿼리에서는 Microsoft SQL Server 2000 Analysis Services의 예제 데이터베이스인 `FoodMart 2000`에서 다양한 Chardonnay 및 Chablis 와인의 단위 판매량을 조사합니다.</span><span class="sxs-lookup"><span data-stu-id="559ed-112">The following MDX query examines the unit sales of the various Chardonnay and Chablis wines in `FoodMart 2000`, the sample database for Microsoft SQL Server 2000 Analysis Services.</span></span> <span data-ttu-id="559ed-113">이 쿼리는 매우 단순한 결과 집합을 반환하지만 유지 관리 측면에서는 너무 길고 복잡합니다.</span><span class="sxs-lookup"><span data-stu-id="559ed-113">This query, although fairly simple in terms of the result set, is lengthy and unwieldy when you have to maintenance such a query.</span></span>  
  
```  
SELECT  
   {[Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Good].[Good Chardonnay],   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Pearl].[Pearl Chardonnay],   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Portsmouth].[Portsmouth Chardonnay],   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Top Measure].[Top Measure Chardonnay],   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Walrus].[Walrus Chardonnay],   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Good].[Good Chablis Wine],   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Pearl].[Pearl Chablis Wine],   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Portsmouth].[Portsmouth Chablis Wine],   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Top Measure].[Top Measure Chablis Wine],   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Walrus].[Walrus Chablis Wine]} ON COLUMNS,  
   {Measures.[Unit Sales]} ON ROWS  
FROM Sales  
```  
  
 <span data-ttu-id="559ed-114">이전의 MDX 쿼리를 보다 쉽게 유지 관리할 수 있도록 WITH 키워드를 사용하여 쿼리에 대한 명명된 집합을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="559ed-114">To make the previous MDX query easier to maintain, you can create a named set for the query by using the WITH keyword.</span></span> <span data-ttu-id="559ed-115">다음 코드는 WITH 키워드를 사용하여 명명된 집합인 `[ChardonnayChablis]`를 만드는 방법과 이러한 명명된 집합으로 인해 SELECT 문이 더 짧아지고 쉽게 유지 관리될 수 있는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="559ed-115">The following code shows how to use the WITH keyword to create a named set, `[ChardonnayChablis]`, and how the named set makes the SELECT statement shorter and easier to maintain.</span></span>  
  
```  
WITH SET [ChardonnayChablis] AS  
   {[Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Good].[Good Chardonnay],  
   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Pearl].[Pearl Chardonnay],  
   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Portsmouth].[Portsmouth Chardonnay],  
   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Top Measure].[Top Measure Chardonnay],  
   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Walrus].[Walrus Chardonnay],  
   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Good].[Good Chablis Wine],  
   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Pearl].[Pearl Chablis Wine],  
   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Portsmouth].[Portsmouth Chablis Wine],  
   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Top Measure].[Top Measure Chablis Wine],  
   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Walrus].[Walrus Chablis Wine]}  
  
SELECT  
   [ChardonnayChablis] ON COLUMNS,  
   {Measures.[Unit Sales]} ON ROWS  
FROM Sales  
```  
  
### <a name="using-functions-together-with-the-with-keyword"></a><span data-ttu-id="559ed-116">WITH 키워드와 함께 함수 사용</span><span class="sxs-lookup"><span data-stu-id="559ed-116">Using Functions Together with the WITH Keyword</span></span>  
 <span data-ttu-id="559ed-117">명명된 집합의 각 멤버를 명시적으로 정의할 수도 있지만 이 방식은 문을 길게 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="559ed-117">Although you can explicitly define each member of a named set, this approach can produce a lengthy statement.</span></span> <span data-ttu-id="559ed-118">명명된 집합을 쉽게 만들고 유지 관리하기 위해서는 MDX 함수를 사용하여 멤버를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="559ed-118">To make the creation and maintenance of a named set easier, you can use MDX functions to define the members.</span></span>  
  
 <span data-ttu-id="559ed-119">예를 들어 다음 MDX 쿼리 예에서는 [Filter](/sql/mdx/filter-mdx), [CurrentMember](/sql/mdx/current-mdx)및 [Name](/sql/mdx/members-string-mdx) MDX 함수와 InStr VBA 함수를 사용하여 `[ChardonnayChablis]` 라는 명명된 집합을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="559ed-119">For example, the following MDX query example uses the [Filter](/sql/mdx/filter-mdx), [CurrentMember](/sql/mdx/current-mdx), and [Name](/sql/mdx/members-string-mdx) MDX functions and the InStr VBA function to create the `[ChardonnayChablis]` named set.</span></span> <span data-ttu-id="559ed-120">이 버전의 `[ChardonnayChablis]` 명명된 집합은 이 항목의 앞에 표시된 명시적으로 정의된 것과 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="559ed-120">This version of the `[ChardonnayChablis]` named set is the same as the explicitly defined version shown previously in this topic.</span></span>  
  
```  
WITH SET [ChardonnayChablis] AS  
   'Filter([Product].Members, (InStr(1, [Product].CurrentMember.Name, "chardonnay") <> 0) OR (InStr(1, [Product].CurrentMember.Name, "chablis") <> 0))'  
  
SELECT  
   [ChardonnayChablis] ON COLUMNS,  
   {Measures.[Unit Sales]} ON ROWS  
FROM Sales  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="559ed-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="559ed-121">See Also</span></span>  
 <span data-ttu-id="559ed-122">[SELECT 문 &#40;MDX&#41;](/sql/mdx/mdx-data-manipulation-select) </span><span class="sxs-lookup"><span data-stu-id="559ed-122">[SELECT Statement &#40;MDX&#41;](/sql/mdx/mdx-data-manipulation-select) </span></span>  
 [<span data-ttu-id="559ed-123">세션 범위 명명된 집합 만들기&#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="559ed-123">Creating Session-Scoped Named Sets &#40;MDX&#41;</span></span>](mdx-named-sets-creating-session-scoped-named-sets.md)  
  
  
