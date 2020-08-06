---
title: 중복 행 제외(Visual Database Tools) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- search criteria [SQL Server], excluding rows
- row duplicates [SQL Server]
- duplicate rows
- row excluded in search [SQL Server]
- result sets [SQL Server], duplicate values
- excluding rows
ms.assetid: ab35a363-421d-4665-946b-ae3f6397af50
author: stevestein
ms.author: sstein
ms.openlocfilehash: 3b396f2738f6895684d828884d4822ea9165e0a9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660265"
---
# <a name="exclude-duplicate-rows-visual-database-tools"></a><span data-ttu-id="36c8e-102">중복 행 제외(Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="36c8e-102">Exclude Duplicate Rows (Visual Database Tools)</span></span>
  <span data-ttu-id="36c8e-103">결과 집합에서 중복 행을 제외하도록 지정하면 결과 집합에 고유 값만 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36c8e-103">If you want to see only unique values in a result set, you can specify that you want to exclude duplicates from the result set.</span></span>  
  
### <a name="to-exclude-duplicate-rows-from-the-result-set"></a><span data-ttu-id="36c8e-104">결과 집합에서 중복 행을 제외하려면</span><span class="sxs-lookup"><span data-stu-id="36c8e-104">To exclude duplicate rows from the result set</span></span>  
  
1.  <span data-ttu-id="36c8e-105">다이어그램 창의 배경을 마우스 오른쪽 단추로 클릭한 다음 바로 가기 메뉴에서 **속성** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="36c8e-105">Right-click the background of the Diagram pane, then choose **Properties** from the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="36c8e-106">속성 창에서 **고유 값** 을 클릭하고 값을 **예**로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="36c8e-106">In the Property window, click **Distinct values** and set the value to **Yes**.</span></span>  
  
     <span data-ttu-id="36c8e-107">쿼리 및 뷰 디자이너에서 SQL 문의 열 표시 목록 앞에 DISTINCT라는 키워드가 삽입됩니다.</span><span class="sxs-lookup"><span data-stu-id="36c8e-107">The Query and View Designer inserts the keyword DISTINCT in front of the list of display columns in the SQL statement.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="36c8e-108">DISTINCT 키워드를 사용하면 결과 창에서 결과 집합을 수정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="36c8e-108">If you use the DISTINCT keyword you may not be able to modify the result set in the results pane.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36c8e-109">참고 항목</span><span class="sxs-lookup"><span data-stu-id="36c8e-109">See Also</span></span>  
 <span data-ttu-id="36c8e-110">[Visual Database Tools &#40;검색 조건을 지정&#41;](visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="36c8e-110">[Specify Search Criteria &#40;Visual Database Tools&#41;](visual-database-tools.md) </span></span>  
 [<span data-ttu-id="36c8e-111">쿼리 결과 정렬 및 그룹화&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="36c8e-111">Sort and Group Query Results &#40;Visual Database Tools&#41;</span></span>](sort-and-group-query-results-visual-database-tools.md)  
  
  
