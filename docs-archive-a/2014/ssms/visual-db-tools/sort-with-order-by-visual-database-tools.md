---
title: ORDER BY를 사용하여 정렬(Visual Database Tools) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- ORDER BY clause [Visual Database Tools]
ms.assetid: 459f5640-8058-4c24-97e7-7bbd6168bc39
author: stevestein
ms.author: sstein
ms.openlocfilehash: 93bdb9ed01c7935c5b9dae543804fca758a9262d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737360"
---
# <a name="sort-with-order-by-visual-database-tools"></a><span data-ttu-id="b29e4-102">ORDER BY를 사용하여 정렬(Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="b29e4-102">Sort with ORDER BY (Visual Database Tools)</span></span>
  <span data-ttu-id="b29e4-103">ORDER BY 절을 사용하면 반환된 행에 있는 하나 이상의 열을 기준으로 쿼리 결과를 정렬할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b29e4-103">You can sort query results by one or more of the columns in the returned rows by using an ORDER BY clause.</span></span> <span data-ttu-id="b29e4-104">조건 정보 창에서 옵션을 선택하여 ORDER BY 절을 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b29e4-104">You can define an ORDER BY clause by choosing options in the Criteria Details pane.</span></span>  
  
### <a name="to-sort-a-query-using-an-order-by-clause"></a><span data-ttu-id="b29e4-105">ORDER BY 절을 사용하여 쿼리를 정렬하려면</span><span class="sxs-lookup"><span data-stu-id="b29e4-105">To sort a query using an ORDER BY clause</span></span>  
  
1.  <span data-ttu-id="b29e4-106">쿼리를 열거나 새 쿼리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b29e4-106">Open a query or create a new one.</span></span>  
  
2.  <span data-ttu-id="b29e4-107">[조건 창](visual-database-tools.md)에서 쿼리 결과를 정렬하는 데 사용하려는 열에 상응하는 행의 **정렬 형식** 열을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b29e4-107">In the [Criteria Pane](visual-database-tools.md), click the **Sort Type** column for the row corresponding to the column that you want to use to sort your query results.</span></span>  
  
3.  <span data-ttu-id="b29e4-108">드롭다운 목록에서 *오름차순* 또는 *내림차순* 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b29e4-108">Choose *Ascending* or *Descending* from the drop-down list.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b29e4-109">열의 **정렬 형식** 항목을 지우면 ORDER BY 절에서 해당 열이 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="b29e4-109">Clearing the **Sort Type** entry for a column removes that column from the ORDER BY clause.</span></span>  
  
 <span data-ttu-id="b29e4-110">조건 창에서 작업하는 경우 가장 최근의 동작에 일치하도록 쿼리의 UNION 절이 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="b29e4-110">Notice that as you work in the Criteria pane, your query's UNION clause changes to match your most recent actions.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b29e4-111">여러 열을 기준으로 결과를 정렬하는 경우 **정렬 순서** 열을 사용하여 각 열에 대해 서로를 기준으로 열이 검색되는 순서를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b29e4-111">When sorting results by more than one column, specify the order in which columns are searched relative to each other by using the **Sort Order** column.</span></span> <span data-ttu-id="b29e4-112">자세한 내용은 **방법: 쿼리에서 여러 열 정렬**을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b29e4-112">For more information, see **How to: Sort Multiple Columns in Queries**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b29e4-113">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b29e4-113">See Also</span></span>  
 <span data-ttu-id="b29e4-114">[Visual Database Tools&#41;&#40;쿼리 결과 정렬 및 그룹화](sort-and-group-query-results-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="b29e4-114">[Sort and Group Query Results &#40;Visual Database Tools&#41;](sort-and-group-query-results-visual-database-tools.md) </span></span>  
 <span data-ttu-id="b29e4-115">[Visual Database Tools를 &#40;쿼리 결과 요약&#41;](summarize-query-results-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="b29e4-115">[Summarize Query Results &#40;Visual Database Tools&#41;](summarize-query-results-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="b29e4-116">쿼리 및 뷰 디자인 방법 도움말 항목&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="b29e4-116">Design Queries and Views How-to Topics &#40;Visual Database Tools&#41;</span></span>](design-queries-and-views-how-to-topics-visual-database-tools.md)  
  
  
