---
title: 사용자 지정 식을 사용 하 여 값 요약 또는 집계 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- summarizing query results
- custom expressions to aggregate values [SQL Server]
ms.assetid: 34130ac1-0106-4766-b324-acb0b7bb6f6e
author: stevestein
ms.author: sstein
ms.openlocfilehash: b9f03f82842178a68c8a3d04ebc1bd738c0ab0b5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735791"
---
# <a name="summarize-or-aggregate-values-using-custom-expressions-visual-database-tools"></a><span data-ttu-id="99fb6-102">사용자 지정 식을 사용하여 값 요약 또는 집계(Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="99fb6-102">Summarize or Aggregate Values Using Custom Expressions (Visual Database Tools)</span></span>
  <span data-ttu-id="99fb6-103">집계 함수를 사용하여 데이터를 집계할 수 있을 뿐만 아니라 사용자 지정 식을 만들어 집계 값을 산출할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="99fb6-103">In addition to using aggregate functions to aggregate data, you can create custom expressions to produce aggregate values.</span></span> <span data-ttu-id="99fb6-104">집계 쿼리에서 집계 함수를 사용할 위치에 어디든지 사용자 지정 식을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="99fb6-104">You can use custom expressions in place of aggregate functions anywhere in an aggregate query.</span></span>  
  
 <span data-ttu-id="99fb6-105">예를 들어, `titles` 테이블에서 일반적인 평균 가격뿐만 아니라 가격이 할인된 경우의 평균 가격까지 표시하는 쿼리를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="99fb6-105">For example, in the `titles` table you might want to create a query that shows not just the average price, but what the average price would be if it were discounted.</span></span>  
  
 <span data-ttu-id="99fb6-106">테이블의 개별 행만 사용되는 계산에 기반한 식은 포함할 수 없습니다. 식을 계산할 때는 집계 값만 사용할 수 있으므로 이 식은 집계 값을 기반으로 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="99fb6-106">You cannot include an expression that is based on calculations involving only individual rows in the table; the expression must be based on an aggregate value, because only the aggregate values are available at the time the expression is calculated.</span></span>  
  
### <a name="to-specify-a-custom-expression-for-a-summary-value"></a><span data-ttu-id="99fb6-107">요약 값을 위한 사용자 지정 식을 지정하려면</span><span class="sxs-lookup"><span data-stu-id="99fb6-107">To specify a custom expression for a summary value</span></span>  
  
1.  <span data-ttu-id="99fb6-108">쿼리의 그룹을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="99fb6-108">Specify the groups for your query.</span></span> <span data-ttu-id="99fb6-109">자세한 내용은 [쿼리 결과 행 그룹화&#40;Visual Database Tools&#41;](visual-database-tools.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="99fb6-109">For details, see [Group Rows in Query Results &#40;Visual Database Tools&#41;](visual-database-tools.md).</span></span>  
  
2.  <span data-ttu-id="99fb6-110">조건 창의 빈 행으로 이동한 다음 **열** 열에 식을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="99fb6-110">Move to a blank row of the Criteria pane, and then type the expression in the **Columns** column.</span></span>  
  
     <span data-ttu-id="99fb6-111">[쿼리 및 뷰 디자이너](query-and-view-designer-tools-visual-database-tools.md)는 열 별칭을 식에 자동으로 할당하여 쿼리 출력에서 유용한 열 머리글을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="99fb6-111">The [Query and View Designer](query-and-view-designer-tools-visual-database-tools.md) automatically assigns a column alias to the expression to create a useful column heading in query output.</span></span> <span data-ttu-id="99fb6-112">자세한 내용은 [열 별칭 만들기&#40;Visual Database Tools&#41;](create-column-aliases-visual-database-tools.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="99fb6-112">For more details, see [Create Column Aliases &#40;Visual Database Tools&#41;](create-column-aliases-visual-database-tools.md).</span></span>  
  
3.  <span data-ttu-id="99fb6-113">식의 **그룹화 방법** 열에서 **식**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="99fb6-113">In the **Group By** column for the expression, select **Expression**.</span></span>  
  
4.  <span data-ttu-id="99fb6-114">쿼리를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="99fb6-114">Run the query.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99fb6-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="99fb6-115">See Also</span></span>  
 <span data-ttu-id="99fb6-116">[Visual Database Tools&#41;&#40;쿼리 결과 정렬 및 그룹화](sort-and-group-query-results-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="99fb6-116">[Sort and Group Query Results &#40;Visual Database Tools&#41;](sort-and-group-query-results-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="99fb6-117">쿼리 결과 요약&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="99fb6-117">Summarize Query Results &#40;Visual Database Tools&#41;</span></span>](summarize-query-results-visual-database-tools.md)  
  
  
