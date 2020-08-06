---
title: 쿼리 결과 요약(Visual Database Tools) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- summarizing query results
- queries [SQL Server], results
- aggregate queries [SQL Server]
ms.assetid: c9e15350-ed57-4d95-814d-815fbebfd86b
author: stevestein
ms.author: sstein
ms.openlocfilehash: 08713be2d4439e520df07ec5efd6cb761a78a994
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735788"
---
# <a name="summarize-query-results-visual-database-tools"></a><span data-ttu-id="1df7c-102">쿼리 결과 요약(Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="1df7c-102">Summarize Query Results (Visual Database Tools)</span></span>
  <span data-ttu-id="1df7c-103">집계 쿼리를 만들 때 특정 논리 원칙이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="1df7c-103">When you create aggregate queries, certain logical principles apply.</span></span> <span data-ttu-id="1df7c-104">예를 들어, 요약 쿼리에서는 개별 행의 내용을 표시할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1df7c-104">For example, you cannot display the contents of individual rows in a summary query.</span></span> <span data-ttu-id="1df7c-105">쿼리 및 뷰 디자이너를 사용하면 [다이어그램 창](visual-database-tools.md) 및 [조건 창](criteria-pane-visual-database-tools.md) 의 동작에 따라 이러한 원칙을 준수할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1df7c-105">The Query and View Designer helps you comply with these principles in the way the [Diagram pane](visual-database-tools.md) and [Criteria pane](criteria-pane-visual-database-tools.md) behave.</span></span>  
  
 <span data-ttu-id="1df7c-106">집계 쿼리의 원칙과 쿼리 및 뷰 디자이너의 동작을 이해하면 논리적으로 올바른 집계 쿼리를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1df7c-106">By understanding the principles of aggregate queries and the Query and View Designer's behavior, you can create logically correct aggregate queries.</span></span> <span data-ttu-id="1df7c-107">가장 우선하는 원칙은 집계 쿼리를 사용하면 요약 정보만 만들어진다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="1df7c-107">The overriding principle is that aggregate queries can result only in summary information.</span></span> <span data-ttu-id="1df7c-108">따라서 나머지 대부분의 원칙은 집계 쿼리 내의 개별 데이터 열을 참조할 수 있는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="1df7c-108">Thus, most of the principles that follow describe the ways that you can reference individual data columns within an aggregate query.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1df7c-109">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="1df7c-109">In This Section</span></span>  
 [<span data-ttu-id="1df7c-110">집계 쿼리에서 열 작업&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="1df7c-110">Work with Columns in Aggregate Queries &#40;Visual Database Tools&#41;</span></span>](work-with-columns-in-aggregate-queries-visual-database-tools.md)  
 <span data-ttu-id="1df7c-111">GROUP BY, WHERE 및 HAVING 절을 사용하여 열을 그룹화하고 요약하는 데 관련된 기본적인 개념을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="1df7c-111">Describes concepts about grouping and summarizing columns with the GROUP BY, WHERE, and HAVING clauses.</span></span>  
  
 [<span data-ttu-id="1df7c-112">테이블의 행 계산&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="1df7c-112">Count Rows in a Table &#40;Visual Database Tools&#41;</span></span>](count-rows-in-a-table-visual-database-tools.md)  
 <span data-ttu-id="1df7c-113">테이블의 행 수 또는 테이블에서 조건 집합을 충족하는 행 수를 계산하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="1df7c-113">Provides steps for counting the number of rows in a table or the number of rows in a table that meet a set of criteria.</span></span>  
  
 [<span data-ttu-id="1df7c-114">테이블에 있는 모든 행의 값 요약 또는 집계&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="1df7c-114">Summarize or Aggregate Values for All Rows in a Table &#40;Visual Database Tools&#41;</span></span>](summarize-or-aggregate-values-for-all-rows-in-a-table-visual-database-tools.md)  
 <span data-ttu-id="1df7c-115">그룹화된 행 집합이 아닌 모든 행을 요약하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="1df7c-115">Provides steps for summarizing all rows rather than for a set of grouped rows.</span></span>  
  
 [<span data-ttu-id="1df7c-116">사용자 지정 식을 사용하여 값 요약 또는 집계&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="1df7c-116">Summarize or Aggregate Values Using Custom Expressions &#40;Visual Database Tools&#41;</span></span>](summarize-or-aggregate-values-using-custom-expressions-visual-database-tools.md)  
 <span data-ttu-id="1df7c-117">미리 정의된 절을 사용하는 대신 요약 또는 집계 식을 사용하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="1df7c-117">Provides steps for using expressions to summarize or aggregate rather than using the predefined clauses.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="1df7c-118">관련 섹션</span><span class="sxs-lookup"><span data-stu-id="1df7c-118">Related Sections</span></span>  
 [<span data-ttu-id="1df7c-119">쿼리 및 뷰 디자인 방법 도움말 항목&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="1df7c-119">Design Queries and Views How-to Topics &#40;Visual Database Tools&#41;</span></span>](design-queries-and-views-how-to-topics-visual-database-tools.md)  
 <span data-ttu-id="1df7c-120">쿼리 및 뷰 디자이너를 사용하는 방법과 관련된 항목에 대한 링크를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="1df7c-120">Provides links to topics covering how to use the Query and View Designer.</span></span>  
  
  
