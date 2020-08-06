---
title: 열 별칭 만들기(Visual Database Tools) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- columns [SQL Server], aliases
- aliases [SQL Server], columns
ms.assetid: e2e1c166-8ea7-47a2-b6a7-e419bf0fa3bb
author: stevestein
ms.author: sstein
ms.openlocfilehash: febe7ed27ed10a283cab549bc65299577d69761c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648747"
---
# <a name="create-column-aliases-visual-database-tools"></a><span data-ttu-id="d246d-102">열 별칭 만들기(Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="d246d-102">Create Column Aliases (Visual Database Tools)</span></span>
  <span data-ttu-id="d246d-103">열 이름에 대한 별칭을 만들면 열 이름, 계산 및 요약 값에 대한 작업을 좀 더 쉽게 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d246d-103">You can create aliases for column names to make it easier to work with column names, calculations, and summary values.</span></span> <span data-ttu-id="d246d-104">예를 들어, 열 별칭을 만들어 다음 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d246d-104">For example, you can create a column alias to:</span></span>  
  
-   <span data-ttu-id="d246d-105">`(quantity * unit_price)` 같은 식이나 집계 함수에 대해 "Total Amount" 같은 열 이름을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d246d-105">Create a column name, such as "Total Amount," for an expression such as `(quantity * unit_price)` or for an aggregate function.</span></span>  
  
-   <span data-ttu-id="d246d-106">대신 `"d_id"` 같이 축약된 형식의 열 이름을 만들 수 있습니다. `"discounts.stor_id."`</span><span class="sxs-lookup"><span data-stu-id="d246d-106">Create a shortened form of a column name, such as `"d_id"` for `"discounts.stor_id."`</span></span>  
  
 <span data-ttu-id="d246d-107">열 별칭을 정의한 후에 선택 쿼리에 이 별칭을 사용하여 쿼리 결과를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d246d-107">After you have defined a column alias, you can use the alias in a Select query to specify query output.</span></span>  
  
### <a name="to-create-a-column-alias"></a><span data-ttu-id="d246d-108">열 별칭을 만들려면</span><span class="sxs-lookup"><span data-stu-id="d246d-108">To create a column alias</span></span>  
  
1.  <span data-ttu-id="d246d-109">**조건 창**에서 별칭을 만들려는 데이터 열이 포함된 행을 찾은 다음 필요한 경우 이 행을 출력하도록 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="d246d-109">In the **Criteria Pane**, locate the row containing the data column for which you want to create an alias, and if necessary, mark it for output.</span></span> <span data-ttu-id="d246d-110">데이터 열이 아직 표에 없으면 이를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="d246d-110">If the data column is not already in the grid, add it.</span></span>  
  
2.  <span data-ttu-id="d246d-111">선택한 행의 **별칭** 열에 별칭을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="d246d-111">In the **Alias** column for that row, enter the alias.</span></span> <span data-ttu-id="d246d-112">별칭은 SQL의 모든 명명 규칙을 준수해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d246d-112">The alias must follow all naming conventions for SQL.</span></span> <span data-ttu-id="d246d-113">입력한 별칭 이름에 공백이 포함되어 있으면 쿼리 및 뷰 디자이너에서 공백 주위에 자동으로 구분 기호가 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="d246d-113">If the alias name you enter contains spaces, the Query and View Designer automatically puts delimiters around it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d246d-114">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d246d-114">See Also</span></span>  
 <span data-ttu-id="d246d-115">[Visual Database Tools&#41;&#40;쿼리에 열 추가](visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="d246d-115">[Add Columns to Queries &#40;Visual Database Tools&#41;](visual-database-tools.md) </span></span>  
 <span data-ttu-id="d246d-116">[Visual Database Tools&#41;&#40;쿼리 결과 정렬 및 그룹화](sort-and-group-query-results-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="d246d-116">[Sort and Group Query Results &#40;Visual Database Tools&#41;](sort-and-group-query-results-visual-database-tools.md) </span></span>  
 <span data-ttu-id="d246d-117">[Visual Database Tools를 &#40;쿼리 결과 요약&#41;](summarize-query-results-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="d246d-117">[Summarize Query Results &#40;Visual Database Tools&#41;](summarize-query-results-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="d246d-118">쿼리 관련 기본 작업 수행&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="d246d-118">Perform Basic Operations with Queries &#40;Visual Database Tools&#41;</span></span>](perform-basic-operations-with-queries-visual-database-tools.md)  
  
  
