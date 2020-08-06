---
title: 오름차순 또는 내림차순으로 정렬(Visual Database Tools) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- descending sorts
- ascending sorts
ms.assetid: d61cc55b-9ee8-4ecf-a32f-6459ae43910b
author: stevestein
ms.author: sstein
ms.openlocfilehash: 67b5e6b00f62cfc297cc5930bc8cf3a41314a2f8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660248"
---
# <a name="sort-in-ascending-or-descending-order-visual-database-tools"></a><span data-ttu-id="6fbd8-102">오름차순 또는 내림차순으로 정렬(Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="6fbd8-102">Sort in Ascending or Descending Order (Visual Database Tools)</span></span>
  <span data-ttu-id="6fbd8-103">`ASC` 또는 `DESC` 키워드를 `ORDER BY` 절과 함께 사용하면 결과 집합에 있는 하나 이상의 열에 대해 쿼리 결과를 오름차순이나 내림차순으로 정렬할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6fbd8-103">You can sort query results in ascending or descending order on one or more of the columns in the result set by using the `ASC` or `DESC` keywords with the `ORDER BY` clause.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6fbd8-104">정렬 순서는 부분적으로 열의 배치 순서에 따라 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="6fbd8-104">The sort order is determined in part by the column's collation sequence.</span></span> <span data-ttu-id="6fbd8-105">[데이터 정렬 대화 상자](visual-database-tools.md)에서 데이터 정렬 순서를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6fbd8-105">You can change the collation sequence in the [Collation Dialog Box](visual-database-tools.md).</span></span>  
  
 <span data-ttu-id="6fbd8-106">다음 절차에서는 ORDER BY 절을 사용하여 하나 이상의 열을 정렬하는 쿼리를 뷰 디자이너에서 열고 있다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="6fbd8-106">The following procedure assumes that you have a query open in Query and View Designer that uses the ORDER BY clause to sort one or more columns.</span></span>  
  
### <a name="to-specify-or-change-the-order-in-which-results-are-sorted"></a><span data-ttu-id="6fbd8-107">결과 정렬 순서를 지정하거나 변경하려면</span><span class="sxs-lookup"><span data-stu-id="6fbd8-107">To specify or change the order in which results are sorted</span></span>  
  
1.  <span data-ttu-id="6fbd8-108">[조건 창](criteria-pane-visual-database-tools.md)에서 순서를 변경하려는 열의 **정렬 형식** 필드를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6fbd8-108">In the [Criteria pane](criteria-pane-visual-database-tools.md), click the **Sort Type** field for the column that you want to reorder.</span></span>  
  
2.  <span data-ttu-id="6fbd8-109">**오름차순** 이나 **내림차순** 을 선택하여 열의 정렬 순서를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6fbd8-109">Choose **Ascending** or **Descending** to specify the sort order for the column.</span></span>  
  
 <span data-ttu-id="6fbd8-110">조건 창에서 작업하는 경우 가장 최근의 동작에 일치하도록 쿼리의 UNION 절이 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="6fbd8-110">Notice that as you work in the Criteria pane, your query's UNION clause changes to match your most recent actions.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6fbd8-111">여러 열을 기준으로 결과를 정렬하는 경우 정렬 순서 열을 사용하여 각 열에 대해 서로를 기준으로 열이 검색되는 순서를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6fbd8-111">When sorting results by more than one column, specify the order in which columns are searched relative to each other by using the Sort Order column.</span></span> <span data-ttu-id="6fbd8-112">자세한 내용은 [쿼리에서 여러 열 정렬&#40;Visual Database Tools&#41;](sort-multiple-columns-in-queries-visual-database-tools.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6fbd8-112">For more information, see [Sort Multiple Columns in Queries &#40;Visual Database Tools&#41;](sort-multiple-columns-in-queries-visual-database-tools.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6fbd8-113">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6fbd8-113">See Also</span></span>  
 <span data-ttu-id="6fbd8-114">[Visual Database Tools&#41;&#40;쿼리 결과 정렬 및 그룹화](sort-and-group-query-results-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="6fbd8-114">[Sort and Group Query Results &#40;Visual Database Tools&#41;](sort-and-group-query-results-visual-database-tools.md) </span></span>  
 <span data-ttu-id="6fbd8-115">[Visual Database Tools를 &#40;쿼리 결과 요약&#41;](summarize-query-results-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="6fbd8-115">[Summarize Query Results &#40;Visual Database Tools&#41;](summarize-query-results-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="6fbd8-116">쿼리 및 뷰 디자인 방법 도움말 항목&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="6fbd8-116">Design Queries and Views How-to Topics &#40;Visual Database Tools&#41;</span></span>](design-queries-and-views-how-to-topics-visual-database-tools.md)  
  
  
