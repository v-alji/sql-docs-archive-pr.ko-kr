---
title: 조인 제거(Visual Database Tools) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- removing joins
- joins [SQL Server], removing
- deleting joins
ms.assetid: ccc212a1-fd13-48d6-85e5-5ff310c34bbd
author: stevestein
ms.author: sstein
ms.openlocfilehash: b037e317b629671f6ec5ea1fa90edfca6fafa627
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638485"
---
# <a name="remove-joins-visual-database-tools"></a><span data-ttu-id="972e2-102">조인 제거(Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="972e2-102">Remove Joins (Visual Database Tools)</span></span>
  <span data-ttu-id="972e2-103">내부 조인 또는 외부 조인을 통해 테이블을 더 이상 조인하지 않으려면 테이블 간의 조인을 제거하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="972e2-103">If you do not want tables to be joined via an inner join or an outer join, you can remove the join between them.</span></span> <span data-ttu-id="972e2-104">예를 들어 [쿼리 및 뷰 디자이너](visual-database-tools.md) 가 두 테이블 간에 자동으로 만든 조인을 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="972e2-104">For example, you might remove a join that the [Query and View Designer](visual-database-tools.md) has been created automatically between two tables.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="972e2-105">쿼리에서 조인을 제거해도 데이터베이스에서의 기본 관계는 변경되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="972e2-105">Removing a join from a query does not alter the underlying relationship in the database.</span></span>  
  
 <span data-ttu-id="972e2-106">조인된 두 테이블이 쿼리의 일부이고 두 테이블 간의 조인 조건을 모두 제거하는 경우 결과 쿼리는 두 테이블의 결과 즉, CROSS JOIN이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="972e2-106">If two joined tables are part of your query and you remove all join conditions between them, the resulting query becomes the product of both tables - that is, it becomes a CROSS JOIN.</span></span>  
  
### <a name="to-remove-a-join"></a><span data-ttu-id="972e2-107">조인을 제거하려면</span><span class="sxs-lookup"><span data-stu-id="972e2-107">To remove a join</span></span>  
  
-   <span data-ttu-id="972e2-108">[다이어그램 창](diagram-pane-visual-database-tools.md)에서 제거할 조인의 조인 선을 선택한 다음 Delete 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="972e2-108">In the [Diagram pane](diagram-pane-visual-database-tools.md), select the join line for the join to remove, and then press the DELETE key.</span></span> <span data-ttu-id="972e2-109">한 번에 조인 선을 여러 개 선택하여 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="972e2-109">You can select and delete multiple join lines at one time.</span></span>  
  
 <span data-ttu-id="972e2-110">쿼리 및 뷰 디자이너는 조인 선을 제거하고 [SQL 창](sql-pane-visual-database-tools.md)에서 문을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="972e2-110">The Query and View Designer removes the join line and alters the statement in the [SQL pane](sql-pane-visual-database-tools.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="972e2-111">참고 항목</span><span class="sxs-lookup"><span data-stu-id="972e2-111">See Also</span></span>  
 <span data-ttu-id="972e2-112">[Visual Database Tools &#40;자동으로 테이블 조인&#41;](join-tables-automatically-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="972e2-112">[Join Tables Automatically &#40;Visual Database Tools&#41;](join-tables-automatically-visual-database-tools.md) </span></span>  
 <span data-ttu-id="972e2-113">[Visual Database Tools를 &#40;테이블을 수동으로 조인&#41;](join-tables-manually-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="972e2-113">[Join Tables Manually &#40;Visual Database Tools&#41;](join-tables-manually-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="972e2-114">조인을 사용한 쿼리&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="972e2-114">Query with Joins &#40;Visual Database Tools&#41;</span></span>](query-with-joins-visual-database-tools.md)  
  
  
