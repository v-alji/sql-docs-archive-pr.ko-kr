---
title: 지원되는 쿼리 형식(Visual Database Tools) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- Delete query
- queries [SQL Server], types
- Update query
- Query Designer [SQL Server], query types
- Criteria pane
- Insert Values query
- Select query
- Make Table query
- Insert Results query
- Diagram pane [Visual Database Tools]
- View Designer, query types
ms.assetid: 72b9116c-c128-4078-a78d-257a2955a3f6
author: stevestein
ms.author: sstein
ms.openlocfilehash: b00b7018fc6d0b631696811bd1870e09842b4162
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735783"
---
# <a name="supported-query-types-visual-database-tools"></a><span data-ttu-id="75d0b-102">지원되는 쿼리 형식(Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="75d0b-102">Supported Query Types (Visual Database Tools)</span></span>
  <span data-ttu-id="75d0b-103">[쿼리 및 뷰 디자이너](visual-database-tools.md)의 다이어그램 창과 조건 창(그래픽 창)에서 다음과 같은 쿼리 형식을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="75d0b-103">You can create the following types of queries in the Diagram and Criteria panes (the graphical panes) of the [Query and View Designer](visual-database-tools.md):</span></span>  
  
-   <span data-ttu-id="75d0b-104">**선택 쿼리** 하나 이상의 테이블 또는 뷰에서 데이터를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="75d0b-104">**Select query** Retrieves data from one or more tables or views.</span></span> <span data-ttu-id="75d0b-105">이 쿼리 형식은 SQL SELECT 문을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="75d0b-105">This type of query creates an SQL SELECT statement.</span></span>  
  
-   <span data-ttu-id="75d0b-106">**결과 삽입** 기존 행을 한 테이블에서 다른 테이블에 복사하거나 동일한 테이블에 새 행으로 복사하여 새 행을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="75d0b-106">**Insert Results** Creates new rows by copying existing rows from one table into another, or into the same table as new rows.</span></span> <span data-ttu-id="75d0b-107">이 쿼리 형식은 SQL INSERT INTO...SELECT 문을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="75d0b-107">This type of query creates an SQL INSERT INTO...SELECT statement.</span></span>  
  
-   <span data-ttu-id="75d0b-108">**값 삽입** 새 행을 만들고 지정된 열에 값을 삽입합니다.</span><span class="sxs-lookup"><span data-stu-id="75d0b-108">**Insert Values** Creates a new row and inserts values into specified columns.</span></span> <span data-ttu-id="75d0b-109">이 쿼리 형식은 SQL INSERT INTO...VALUES 문을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="75d0b-109">This type of query creates an SQL INSERT INTO...VALUES statement.</span></span>  
  
-   <span data-ttu-id="75d0b-110">**업데이트 쿼리** 테이블에서 하나 이상의 기존 행에 있는 개별 열의 값을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="75d0b-110">**Update query** Changes the values of individual columns in one or more existing rows in a table.</span></span> <span data-ttu-id="75d0b-111">이 쿼리 형식은 SQL UPDATE...SET 문을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="75d0b-111">This type of query creates an SQL UPDATE...SET statement.</span></span>  
  
-   <span data-ttu-id="75d0b-112">**삭제 쿼리** 테이블에서 하나 이상의 행을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="75d0b-112">**Delete query** Removes one or more rows from a table.</span></span> <span data-ttu-id="75d0b-113">이 쿼리 형식은 SQL DELETE 문을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="75d0b-113">This type of query creates an SQL DELETE statement.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="75d0b-114">삭제 쿼리는 테이블의 전체 행을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="75d0b-114">A Delete query removes entire rows from the table.</span></span> <span data-ttu-id="75d0b-115">따라서 개별 데이터 열의 값을 삭제하려면 업데이트 쿼리를 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="75d0b-115">If you want to delete values from individual data columns, use an Update query.</span></span>  
  
-   <span data-ttu-id="75d0b-116">**테이블 만들기 쿼리** 새 테이블을 만들고 이 테이블에 쿼리 결과를 복사하여 행을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="75d0b-116">**Make Table query** Creates a new table and creates rows in it by copying the results of a query into it.</span></span> <span data-ttu-id="75d0b-117">이 쿼리 형식은 SQL SELECT...INTO 문을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="75d0b-117">This type of query creates an SQL SELECT...INTO statement.</span></span>  
  
 <span data-ttu-id="75d0b-118">그래픽 창을 사용하여 만들 수 있는 쿼리 외에 Union 쿼리를 포함하여 어떤 SQL 문이든지 SQL 창에 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="75d0b-118">In addition to the queries you can create using the graphical panes, you can enter any SQL statement into the SQL pane, such as Union queries.</span></span>  
  
 <span data-ttu-id="75d0b-119">그래픽 창에 나타낼 수 없는 SQL 문을 사용하여 쿼리를 만드는 경우 쿼리 및 뷰 디자이너는 해당 창을 흐리게 표시하여 현재 만들고 있는 쿼리를 반영하지 않음을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="75d0b-119">When you create queries using SQL statements that cannot be represented in the graphical panes, the Query and View Designer dims those panes to indicate that they do not reflect the query you are creating.</span></span> <span data-ttu-id="75d0b-120">그러나 흐리게 표시된 창은 여전히 활성 상태이며 대부분 이 창에서도 쿼리를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="75d0b-120">However, the dimmed panes are still active and, in many cases, you can make changes to the query in those panes.</span></span> <span data-ttu-id="75d0b-121">그래픽 창에 나타낼 수 있는 쿼리에 변경 내용이 반영되면 해당 그래픽 창은 더 이상 흐리게 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="75d0b-121">If the changes you make result in a query that can be represented in the graphical panes, those panes are no longer dimmed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75d0b-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="75d0b-122">See Also</span></span>  
 <span data-ttu-id="75d0b-123">[쿼리 및 뷰 디자인 방법 도움말 항목 &#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="75d0b-123">[Design Queries and Views How-to Topics &#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="75d0b-124">쿼리 형식&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="75d0b-124">Types of Queries &#40;Visual Database Tools&#41;</span></span>](types-of-queries-visual-database-tools.md)  
  
  
