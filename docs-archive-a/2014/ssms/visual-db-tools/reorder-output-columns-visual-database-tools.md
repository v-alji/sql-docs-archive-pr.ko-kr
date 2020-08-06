---
title: 출력 열 다시 정렬(Visual Database Tools) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- reordering output columns [SQL Server]
- output columns [SQL Server]
ms.assetid: 76462885-de4a-4290-a26b-90696d3671f4
author: stevestein
ms.author: sstein
ms.openlocfilehash: 97fa3f768b03f24b8c8d154624a2d7a91aba45f3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651416"
---
# <a name="reorder-output-columns-visual-database-tools"></a><span data-ttu-id="07706-102">출력 열 다시 정렬(Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="07706-102">Reorder Output Columns (Visual Database Tools)</span></span>
  <span data-ttu-id="07706-103">출력 열이 결과에 표시되는 순서는 선택 쿼리에 데이터 열을 추가하는 순서에 따라 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="07706-103">The order in which you add data columns to a Select query determines the order in which they appear in the results.</span></span> <span data-ttu-id="07706-104">쿼리에 추가하는 첫 번째 열은 결과의 가장 왼쪽에 나타나고 두 번째 열은 그 다음에 나타나는 방식입니다.</span><span class="sxs-lookup"><span data-stu-id="07706-104">The first column you add to the query appears leftmost in the results, the second column next, and so on.</span></span>  
  
 <span data-ttu-id="07706-105">업데이트 쿼리나 삽입 쿼리를 만드는 경우 열을 추가하는 순서는 데이터가 처리되는 순서에 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="07706-105">If you are creating Update or Insert queries, the order in which you add columns affects the order in which data is processed.</span></span>  
  
 <span data-ttu-id="07706-106">열의 순서를 바꾸면 결과 집합에 데이터 열이 나타나는 위치나 데이터 열이 사용되는 순서를 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07706-106">To control where a data column appears in the result set, or in what order it is used, you can reorder the columns.</span></span>  
  
### <a name="to-reorder-columns-for-output"></a><span data-ttu-id="07706-107">출력 열의 순서를 바꾸려면</span><span class="sxs-lookup"><span data-stu-id="07706-107">To reorder columns for output</span></span>  
  
1.  <span data-ttu-id="07706-108">[조건 창](visual-database-tools.md)에서 행의 왼쪽에 있는 행 선택기 단추를 클릭하여 열이 포함된 행을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="07706-108">In the [Criteria pane](visual-database-tools.md), select the row containing the column by clicking the row selector button to the left of the row.</span></span>  
  
2.  <span data-ttu-id="07706-109">행 선택기 단추를 가리키고 행을 새 위치에 끌어 옵니다.</span><span class="sxs-lookup"><span data-stu-id="07706-109">Point to the row selector button and drag the row to a new location.</span></span>  
  
     <span data-ttu-id="07706-110">또는</span><span class="sxs-lookup"><span data-stu-id="07706-110">-or-</span></span>  
  
     <span data-ttu-id="07706-111">[SQL 창](sql-pane-visual-database-tools.md)에서 열 이름의 순서를 편집합니다.</span><span class="sxs-lookup"><span data-stu-id="07706-111">Edit the order of the column names in the [SQL pane](sql-pane-visual-database-tools.md).</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="07706-112">조건 창에 빈 행을 삽입한 다음 삽입할 데이터 열을 지정하여 조건 창의 특정 위치에 데이터 행을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07706-112">You can add a data row at a specific location in the Criteria pane by inserting a blank row into the Criteria pane, and then specifying the data column to insert.</span></span> <span data-ttu-id="07706-113">자세한 내용은 [쿼리에 열 추가&#40;Visual Database Tools&#41;](add-columns-to-queries-visual-database-tools.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="07706-113">For details, see [Add Columns to Queries &#40;Visual Database Tools&#41;](add-columns-to-queries-visual-database-tools.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07706-114">참고 항목</span><span class="sxs-lookup"><span data-stu-id="07706-114">See Also</span></span>  
 <span data-ttu-id="07706-115">[Visual Database Tools&#41;&#40;쿼리 결과 정렬 및 그룹화](sort-and-group-query-results-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="07706-115">[Sort and Group Query Results &#40;Visual Database Tools&#41;](sort-and-group-query-results-visual-database-tools.md) </span></span>  
 <span data-ttu-id="07706-116">[Visual Database Tools를 &#40;쿼리 결과 요약&#41;](summarize-query-results-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="07706-116">[Summarize Query Results &#40;Visual Database Tools&#41;](summarize-query-results-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="07706-117">쿼리 관련 기본 작업 수행&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="07706-117">Perform Basic Operations with Queries &#40;Visual Database Tools&#41;</span></span>](perform-basic-operations-with-queries-visual-database-tools.md)  
  
  
