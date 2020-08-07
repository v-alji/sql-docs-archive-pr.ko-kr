---
title: 쿼리 결과에서 열 제거(Visual Database Tools) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- columns [SQL Server], deleting
- result sets [SQL Server], queries
- removing columns
- results [SQL Server], query
- deleting columns
- queries [SQL Server], results
ms.assetid: a7de7a87-4249-49bd-863d-dc0b40a49e78
author: stevestein
ms.author: sstein
ms.openlocfilehash: 90d502ad2cdb4c67d5d4f23f262b56cb17ea7519
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727728"
---
# <a name="remove-columns-from-query-results-visual-database-tools"></a><span data-ttu-id="75d0b-102">쿼리 결과에서 열 제거(Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="75d0b-102">Remove Columns from Query Results (Visual Database Tools)</span></span>
  <span data-ttu-id="75d0b-103">선택 쿼리에 사용 중인 열을 결과 집합에 표시하지 않으려는 경우 즉, 쿼리의 선택 목록에 포함하지 않으려는 경우 해당 열을 출력에서 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="75d0b-103">If you are using a column in a Select query but do not want to display it in the result set (that is, you do not want it in the query's select list), you can remove it from output.</span></span> <span data-ttu-id="75d0b-104">쿼리의 출력에서 열을 제거한 후에도 이 열을 검색 조건에 사용하거나 정렬 필드로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="75d0b-104">After you remove the column from the query's output, you can still use it in search conditions or as a sorting field.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="75d0b-105">쿼리의 열을 함께 제거하려면 [쿼리에서 열 제거&#40;Visual Database Tools&#41;](visual-database-tools.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="75d0b-105">If you want to remove a column from the query altogether, see [Remove Columns from Queries &#40;Visual Database Tools&#41;](visual-database-tools.md).</span></span>  
  
### <a name="to-remove-a-column-from-the-query-output"></a><span data-ttu-id="75d0b-106">쿼리 결과에서 열을 제거하려면</span><span class="sxs-lookup"><span data-stu-id="75d0b-106">To remove a column from the query output</span></span>  
  
-   <span data-ttu-id="75d0b-107">**조건 창**에서 제거하려는 데이터 열의 **출력** 열에 있는 확인란을 선택 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="75d0b-107">In the **Criteria Pane**, clear the check box in the **Output** column for the data column you want to remove.</span></span> <span data-ttu-id="75d0b-108">**출력** 열을 다시 선택하면 쿼리 결과에 열을 다시 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="75d0b-108">(If you want to add the column back to the query output, you can check the **Output** column again.)</span></span>  
  
     <span data-ttu-id="75d0b-109">또는</span><span class="sxs-lookup"><span data-stu-id="75d0b-109">-or-</span></span>  
  
-   <span data-ttu-id="75d0b-110">[SQL 창](sql-pane-visual-database-tools.md)의 출력 목록에서 열을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="75d0b-110">Remove the column from the output list in the [SQL pane](sql-pane-visual-database-tools.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75d0b-111">참고 항목</span><span class="sxs-lookup"><span data-stu-id="75d0b-111">See Also</span></span>  
 <span data-ttu-id="75d0b-112">[Visual Database Tools&#41;&#40;쿼리에 열 추가](add-columns-to-queries-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="75d0b-112">[Add Columns to Queries &#40;Visual Database Tools&#41;](add-columns-to-queries-visual-database-tools.md) </span></span>  
 <span data-ttu-id="75d0b-113">[Visual Database Tools&#41;&#40;쿼리에서 열을 제거 합니다.](visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="75d0b-113">[Remove Columns from Queries &#40;Visual Database Tools&#41;](visual-database-tools.md) </span></span>  
 <span data-ttu-id="75d0b-114">[Visual Database Tools&#41;&#40;쿼리 결과 정렬 및 그룹화](sort-and-group-query-results-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="75d0b-114">[Sort and Group Query Results &#40;Visual Database Tools&#41;](sort-and-group-query-results-visual-database-tools.md) </span></span>  
 <span data-ttu-id="75d0b-115">[Visual Database Tools를 &#40;쿼리 결과 요약&#41;](summarize-query-results-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="75d0b-115">[Summarize Query Results &#40;Visual Database Tools&#41;](summarize-query-results-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="75d0b-116">쿼리 관련 기본 작업 수행&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="75d0b-116">Perform Basic Operations with Queries &#40;Visual Database Tools&#41;</span></span>](perform-basic-operations-with-queries-visual-database-tools.md)  
  
  
