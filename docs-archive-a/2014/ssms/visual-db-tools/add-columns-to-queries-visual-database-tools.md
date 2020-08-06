---
title: 쿼리에 열 추가(Visual Database Tools) | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- inserting columns
- columns [SQL Server], adding
- queries [SQL Server], columns
- adding columns
ms.assetid: 82f3ba72-3d72-4fb1-8179-2a953a782787
author: stevestein
ms.author: sstein
ms.openlocfilehash: 49c6e575eea2d4437be1f16b400ca22120471fcf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648763"
---
# <a name="add-columns-to-queries-visual-database-tools"></a><span data-ttu-id="a0e42-102">쿼리에 열 추가(Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="a0e42-102">Add Columns to Queries (Visual Database Tools)</span></span>
  <span data-ttu-id="a0e42-103">쿼리에서 열을 사용하려면 쿼리에 열을 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a0e42-103">To use a column in a query, you must add it to the query.</span></span> <span data-ttu-id="a0e42-104">열을 추가하여 쿼리 출력에 표시하거나, 정렬에 사용하거나, 열의 내용을 검색하거나, 해당 내용을 요약할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a0e42-104">You might add a column to display it in query output, to use it for sorting, to search the contents of the column, or to summarize its contents.</span></span> <span data-ttu-id="a0e42-105">쿼리를 실행할 때 쿼리에 사용되는 열 중 어떠한 열을 결과 창에 포함할지 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a0e42-105">You can decide which of the columns you use in the query are included in the results pane when the query is run.</span></span> <span data-ttu-id="a0e42-106">자세한 내용은 [쿼리 결과에서 열 제거&#40;Visual Database Tools&#41;](visual-database-tools.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a0e42-106">For more information see [Remove Columns from Query Results &#40;Visual Database Tools&#41;](visual-database-tools.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a0e42-107">쿼리 및 뷰 디자이너에서 열의 데이터 형식을 보려면 **다이어그램 창** 에서 테이블이나 테이블 반환 개체를 선택하고 속성 창에서 열 목록을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a0e42-107">To view the data type of a column in Query and View Designer; select the table or table-valued object in the **Diagram Pane** and in the properties window click Column List.</span></span> <span data-ttu-id="a0e42-108">그런 다음, **줄임표(...)** 를 클릭하여 **열 목록** 대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="a0e42-108">Then click the **ellipses (...)** to open the **Column List** dialog box.</span></span>  
  
 <span data-ttu-id="a0e42-109">쿼리에 열을 사용할 때 그 위치와 상관 없이 열, 리터럴, 연산자 및 함수의 조합으로 구성된 식을 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a0e42-109">Wherever you use a column in a query, you can also use an expression that can consist of any combination of columns, literals, operators, and functions.</span></span>  
  
### <a name="to-add-an-individual-column"></a><span data-ttu-id="a0e42-110">개별 열을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="a0e42-110">To add an individual column</span></span>  
  
-   <span data-ttu-id="a0e42-111">**다이어그램 창**에서 포함하려는 열 옆에 있는 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a0e42-111">In the **Diagram Pane**, select the check box next to the column that you want to include.</span></span>  
  
     <span data-ttu-id="a0e42-112">또는</span><span class="sxs-lookup"><span data-stu-id="a0e42-112">-or-</span></span>  
  
-   <span data-ttu-id="a0e42-113">**조건 창**의 표에서 비어 있는 첫째 행으로 이동하여 **열** 열의 필드를 클릭한 다음 드롭다운 목록에서 열 이름을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a0e42-113">In the **Criteria Pane**, move to the first blank grid row, click the field in the **Column** column, and select a column name from the drop-down list.</span></span>  
  
### <a name="to-add-all-columns-for-one-table-or-table-valued-object"></a><span data-ttu-id="a0e42-114">하나의 테이블 또는 테이블 반환 개체에 대한 열 전체를 추가하려면</span><span class="sxs-lookup"><span data-stu-id="a0e42-114">To add all columns for one table or table-valued object</span></span>  
  
-   <span data-ttu-id="a0e42-115">**다이어그램 창**에서 \*\* \* (모든 열)\*\* 옆의 확인란을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="a0e42-115">In the **Diagram Pane**, select the check box next to **\*(All Columns)**.</span></span>  
  
### <a name="to-add-all-columns-for-all-tables-and-table-structured-objects"></a><span data-ttu-id="a0e42-116">모든 테이블 및 테이블 구조 개체에 대한 열 전체를 추가하려면</span><span class="sxs-lookup"><span data-stu-id="a0e42-116">To add all columns for all tables and table-structured objects</span></span>  
  
1.  <span data-ttu-id="a0e42-117">**테이블 작업 창** 에 조인 선이 선택되어 있지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a0e42-117">Make sure no join lines in the **Table Operations Pane** are selected.</span></span>  
  
2.  <span data-ttu-id="a0e42-118">디자인 창에서 빈 공간을 마우스 오른쪽 단추로 클릭하고 바로 가기 메뉴에서 **속성** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a0e42-118">Right-click in the empty space of the Design window and choose **Properties** from the shortcut menu.</span></span>  
  
3.  <span data-ttu-id="a0e42-119">속성 창에서 **모든 열 출력** 을 클릭하고 드롭다운 목록에서 **예** 또는 **아니요** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a0e42-119">In the Properties window click **Output all columns** and choose **Yes** or **No** from the dropdown list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0e42-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a0e42-120">See Also</span></span>  
 <span data-ttu-id="a0e42-121">[Visual Database Tools&#41;&#40;쿼리 결과에서 열을 제거 합니다.](visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="a0e42-121">[Remove Columns from Query Results &#40;Visual Database Tools&#41;](visual-database-tools.md) </span></span>  
 <span data-ttu-id="a0e42-122">[Visual Database Tools&#41;&#40;쿼리에서 열을 제거 합니다.](remove-columns-from-queries-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="a0e42-122">[Remove Columns from Queries &#40;Visual Database Tools&#41;](remove-columns-from-queries-visual-database-tools.md) </span></span>  
 <span data-ttu-id="a0e42-123">[Visual Database Tools &#40;검색 조건을 지정&#41;](specify-search-criteria-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="a0e42-123">[Specify Search Criteria &#40;Visual Database Tools&#41;](specify-search-criteria-visual-database-tools.md) </span></span>  
 <span data-ttu-id="a0e42-124">[Visual Database Tools를 &#40;쿼리 결과 요약&#41;](summarize-query-results-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="a0e42-124">[Summarize Query Results &#40;Visual Database Tools&#41;](summarize-query-results-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="a0e42-125">쿼리 관련 기본 작업 수행&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="a0e42-125">Perform Basic Operations with Queries &#40;Visual Database Tools&#41;</span></span>](perform-basic-operations-with-queries-visual-database-tools.md)  
  
  
