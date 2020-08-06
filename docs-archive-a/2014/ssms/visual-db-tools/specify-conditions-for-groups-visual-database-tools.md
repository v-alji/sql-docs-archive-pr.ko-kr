---
title: 그룹 조건 지정(Visual Database Tools) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- HAVING clause, query groups
- group query conditions [SQL Server]
ms.assetid: 269ad9c5-3261-4526-badf-7be3c869f229
author: stevestein
ms.author: sstein
ms.openlocfilehash: da9bc1b70fbfae8bf2a68a3a3ba332020020f310
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638484"
---
# <a name="specify-conditions-for-groups-visual-database-tools"></a><span data-ttu-id="0a104-102">그룹 조건 지정(Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="0a104-102">Specify Conditions for Groups (Visual Database Tools)</span></span>
  <span data-ttu-id="0a104-103">HAVING 절에서 그룹 전체에 적용되는 조건을 지정하여 쿼리에 표시되는 그룹을 제한할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a104-103">You can limit the groups that appear in a query by specifying a condition that applies to groups as a whole - a HAVING clause.</span></span> <span data-ttu-id="0a104-104">데이터를 그룹화하고 집계한 후에 HAVING 절의 조건이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a104-104">After the data has been grouped and aggregated, the conditions in the HAVING clause are applied.</span></span> <span data-ttu-id="0a104-105">쿼리에는 이 조건에 맞는 그룹만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a104-105">Only the groups that meet the conditions appear in the query.</span></span>  
  
 <span data-ttu-id="0a104-106">예를 들어, `titles` 테이블의 각 출판사에서 발행한 모든 도서의 평균 가격 중에서 $10.00를 초과하는 평균 가격만 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a104-106">For example, you might want to see the average price of all books for each publisher in a `titles` table, but only if the average price exceeds $10.00.</span></span> <span data-ttu-id="0a104-107">이 경우, `AVG(price) > 10`과 같은 조건을 사용하여 HAVING 절을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="0a104-107">In that case, you could specify a HAVING clause with a condition such as `AVG(price) > 10`.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0a104-108">경우에 따라서는 그룹 전체에 조건을 적용하기 전에 특정 개별 행을 그룹에서 제외할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a104-108">In some instances, you might want to exclude individual rows from groups before applying a condition to groups as a whole.</span></span> <span data-ttu-id="0a104-109">자세한 내용은 [동일한 쿼리에서 HAVING 및 WHERE 절 사용&#40;Visual Database Tools&#41;](visual-database-tools.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0a104-109">For details, see [Use HAVING and WHERE Clauses in the Same Query &#40;Visual Database Tools&#41;](visual-database-tools.md).</span></span>  
  
 <span data-ttu-id="0a104-110">AND 및 OR을 사용하여 조건을 연결하면 HAVING 절에 대한 복잡한 조건을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a104-110">You can create complex conditions for a HAVING clause by using AND and OR to link conditions.</span></span> <span data-ttu-id="0a104-111">검색 조건에 AND 및 OR을 사용하는 방법에 대한 자세한 내용은 [한 열에 여러 검색 조건 지정&#40;Visual Database Tools&#41;](specify-multiple-search-conditions-for-one-column-visual-database-tools.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0a104-111">For details about using AND and OR in search conditions, see [Specify Multiple Search Conditions for One Column &#40;Visual Database Tools&#41;](specify-multiple-search-conditions-for-one-column-visual-database-tools.md).</span></span>  
  
### <a name="to-specify-a-condition-for-a-group"></a><span data-ttu-id="0a104-112">그룹에 대한 조건을 지정하려면</span><span class="sxs-lookup"><span data-stu-id="0a104-112">To specify a condition for a group</span></span>  
  
1.  <span data-ttu-id="0a104-113">쿼리의 그룹을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="0a104-113">Specify the groups for your query.</span></span> <span data-ttu-id="0a104-114">자세한 내용은 [쿼리 결과 행 그룹화&#40;Visual Database Tools&#41;](group-rows-in-query-results-visual-database-tools.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0a104-114">For details, see [Group Rows in Query Results &#40;Visual Database Tools&#41;](group-rows-in-query-results-visual-database-tools.md).</span></span>  
  
2.  <span data-ttu-id="0a104-115">조건의 기반으로 삼을 열이 [조건 창](criteria-pane-visual-database-tools.md)에 아직 없으면 이 열을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="0a104-115">If it is not already in the [Criteria pane](criteria-pane-visual-database-tools.md), add the column on which you want to base the condition.</span></span> <span data-ttu-id="0a104-116">조건에 사용되는 열은 대부분 이미 그룹 열이거나 요약 열인 경우가 많습니다. 집계 함수나 GROUP BY 절의 일부가 아닌 열은 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0a104-116">(Most often the condition involves a column that is already a group or summary column.) You cannot use a column that is not part of an aggregate function or of the GROUP BY clause.</span></span>  
  
3.  <span data-ttu-id="0a104-117">**필터** 열에서 그룹에 적용할 조건을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="0a104-117">In the **Filter** column, specify the condition to apply to the group.</span></span>  
  
     <span data-ttu-id="0a104-118">[쿼리 및 뷰 디자이너](query-and-view-designer-tools-visual-database-tools.md) 에서 [SQL 창](sql-pane-visual-database-tools.md)의 문에 HAVING 절이 자동으로 작성됩니다. 예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="0a104-118">The [Query and View Designer](query-and-view-designer-tools-visual-database-tools.md) automatically creates a HAVING clause in the statement in the [SQL pane](sql-pane-visual-database-tools.md), such as in the following example:</span></span>  
  
    ```  
    SELECT pub_id, AVG(price)  
    FROM titles  
    GROUP BY pub_id  
    HAVING (AVG(price) > 10)  
  
    ```  
  
4.  <span data-ttu-id="0a104-119">추가로 지정할 각 조건에 대하여 2단계와 3단계를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="0a104-119">Repeat steps 2 and 3 for each additional condition you want to specify.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a104-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0a104-120">See Also</span></span>  
 [<span data-ttu-id="0a104-121">쿼리 결과 정렬 및 그룹화&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="0a104-121">Sort and Group Query Results &#40;Visual Database Tools&#41;</span></span>](sort-and-group-query-results-visual-database-tools.md)  
  
  
