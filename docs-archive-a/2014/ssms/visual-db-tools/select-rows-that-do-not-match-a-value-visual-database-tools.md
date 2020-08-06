---
title: 값이 일치하지 않는 행 선택(Visual Database Tools) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- search conditions [SQL Server], rows not matching value
- row not matching value [SQL Server]
- NOT operator [Visual Database Tools]
- search criteria [SQL Server], rows not matching value
ms.assetid: 19898578-7b2f-401c-bb8f-9f2a017efdf7
author: stevestein
ms.author: sstein
ms.openlocfilehash: 412ec93cbfedc87e92da9e86c7e4c7455919722a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734855"
---
# <a name="select-rows-that-do-not-match-a-value-visual-database-tools"></a><span data-ttu-id="65685-102">값이 일치하지 않는 행 선택(Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="65685-102">Select Rows That Do Not Match a Value (Visual Database Tools)</span></span>
  <span data-ttu-id="65685-103">값이 일치하지 않는 행을 찾으려면 NOT 연산자를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="65685-103">To find rows that do not match a value, use the NOT operator.</span></span>  
  
### <a name="to-find-rows-that-do-not-match-a-value"></a><span data-ttu-id="65685-104">값이 일치하지 않는 행을 찾으려면</span><span class="sxs-lookup"><span data-stu-id="65685-104">To find rows that do not match a value</span></span>  
  
1.  <span data-ttu-id="65685-105">검색 조건 내에 사용할 열이나 식을 [조건 창](visual-database-tools.md)에 아직 추가하지 않았다면 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="65685-105">If you have not done so already, add the columns or expressions that you want to use within your search condition to the [Criteria pane](visual-database-tools.md).</span></span>  
  
2.  <span data-ttu-id="65685-106">검색할 데이터 열이나 식이 포함된 행을 찾은 다음 표 형태 창의 **필터** 열에 NOT 연산자와 검색 값을 차례로 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="65685-106">Locate the row containing the data column or expression to search, and then in the **Filter** grid column, enter the NOT operator followed by a search value.</span></span>  
  
 <span data-ttu-id="65685-107">예를 들어 `products` 테이블에서 제품 코드 열의 값이 "A" 이외의 문자로 시작하는 행을 모두 찾으려면 다음 검색 조건을 입력하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="65685-107">For example, to find all the rows in a `products` table where the values in the product code column begin with a character other than "A," you can enter a search condition such as the following:</span></span>  
  
```  
NOT LIKE 'A%'  
```  
  
## <a name="see-also"></a><span data-ttu-id="65685-108">참고 항목</span><span class="sxs-lookup"><span data-stu-id="65685-108">See Also</span></span>  
 <span data-ttu-id="65685-109">[Visual Database Tools&#41;&#40;검색 값을 입력 하는 규칙](rules-for-entering-search-values-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="65685-109">[Rules for Entering Search Values &#40;Visual Database Tools&#41;](rules-for-entering-search-values-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="65685-110">검색 조건 지정&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="65685-110">Specify Search Criteria &#40;Visual Database Tools&#41;</span></span>](specify-search-criteria-visual-database-tools.md)  
  
  
