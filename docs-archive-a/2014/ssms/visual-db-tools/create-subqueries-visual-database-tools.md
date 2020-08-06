---
title: 하위 쿼리 만들기(Visual Database Tools) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- search criteria [SQL Server], subqueries
- nested queries
- subqueries [SQL Server], SQL pane
ms.assetid: 34f6b9b4-ca3a-4a4f-9594-36e513f1c547
author: stevestein
ms.author: sstein
ms.openlocfilehash: 540228839b9734992be008b5d4fb7d717176832e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651989"
---
# <a name="create-subqueries-visual-database-tools"></a><span data-ttu-id="ab63b-102">하위 쿼리 만들기(Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="ab63b-102">Create Subqueries (Visual Database Tools)</span></span>
  <span data-ttu-id="ab63b-103">한 쿼리의 결과를 다른 쿼리의 입력 항목으로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ab63b-103">You can use the results of one query as the input for another.</span></span> <span data-ttu-id="ab63b-104">하위 쿼리의 결과를 IN( ) 함수, EXISTS 연산자 또는 FROM 절을 사용하는 문으로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ab63b-104">You can use the results of a subquery as a statement that uses the IN( ) function, the EXISTS operator, or the FROM clause.</span></span>  
  
 <span data-ttu-id="ab63b-105">SQL 창에 직접 입력하거나 쿼리를 복사하여 다른 쿼리에 붙여넣는 방법으로 하위 쿼리를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ab63b-105">You can create a subquery by entering it directly into the SQL pane or by copying a query and pasting it into another.</span></span>  
  
### <a name="to-define-a-subquery-in-the-sql-pane"></a><span data-ttu-id="ab63b-106">SQL 창에서 하위 쿼리를 정의하려면</span><span class="sxs-lookup"><span data-stu-id="ab63b-106">To define a subquery in the SQL pane</span></span>  
  
1.  <span data-ttu-id="ab63b-107">기본 쿼리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ab63b-107">Create the primary query.</span></span>  
  
2.  <span data-ttu-id="ab63b-108">SQL 창에서 SQL 문을 선택한 다음 **복사** 명령을 사용하여 쿼리를 클립보드로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="ab63b-108">In the SQL pane, select the SQL statement, and then use **Copy** to move the query to the Clipboard.</span></span>  
  
3.  <span data-ttu-id="ab63b-109">새 쿼리를 시작한 다음 **붙여넣기** 명령을 사용하여 첫 번째 쿼리를 새 쿼리의 WHERE 절이나 FROM 절로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="ab63b-109">Start the new query, and then use **Paste** to move the first query into the new query's WHERE or FROM clause.</span></span>  
  
     <span data-ttu-id="ab63b-110">예를 들어, `products` 와 `suppliers`라는 두 개의 테이블이 있으며 스웨덴 공급자에 대한 모든 제품을 표시하는 쿼리를 만들려 한다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="ab63b-110">For example, imagine you have two tables, `products` and `suppliers`, and you want to create a query showing all products for suppliers in Sweden.</span></span> <span data-ttu-id="ab63b-111">`suppliers` 테이블에 첫 번째 쿼리를 만들어 모든 스웨덴 공급자를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="ab63b-111">Create the first query on the `suppliers` table to find all Swedish suppliers:</span></span>  
  
    ```  
    SELECT supplier_id  
    FROM supplier  
    WHERE (country = 'Sweden')  
    ```  
  
     <span data-ttu-id="ab63b-112">복사 명령을 사용하여 이 쿼리를 클립보드로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="ab63b-112">Use the Copy command to move this query to the Clipboard.</span></span> <span data-ttu-id="ab63b-113">`products` 테이블을 사용하여 필요한 제품 정보를 나열하는 두 번째 쿼리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ab63b-113">Create the second query using the `products` table, listing the information you need about products:</span></span>  
  
    ```  
    SELECT product_id, supplier_id, product_name  
    FROM products  
    ```  
  
     <span data-ttu-id="ab63b-114">SQL 창에서 두 번째 쿼리에 WHERE 절을 추가한 다음 클립보드에 있는 첫 번째 쿼리를 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="ab63b-114">In the SQL pane, add a WHERE clause to the second query, then paste the first query from the Clipboard.</span></span> <span data-ttu-id="ab63b-115">첫 번째 쿼리를 괄호로 묶은 결과는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="ab63b-115">Place parentheses around the first query, so that the end result looks like this:</span></span>  
  
    ```  
    SELECT product_id, supplier_id, product_name  
    FROM products  
    WHERE supplier_id IN  
       (SELECT supplier_id  
      FROM supplier  
      WHERE (country = 'Sweden'))  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="ab63b-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ab63b-116">See Also</span></span>  
 <span data-ttu-id="ab63b-117">[Visual Database Tools를 &#40;지원 되는 쿼리 유형&#41;](visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="ab63b-117">[Supported Query Types &#40;Visual Database Tools&#41;](visual-database-tools.md) </span></span>  
 [<span data-ttu-id="ab63b-118">검색 조건 지정&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="ab63b-118">Specify Search Criteria &#40;Visual Database Tools&#41;</span></span>](specify-search-criteria-visual-database-tools.md)  
  
  
