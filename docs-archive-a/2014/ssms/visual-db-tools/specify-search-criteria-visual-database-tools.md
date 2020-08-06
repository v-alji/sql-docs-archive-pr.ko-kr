---
title: 검색 조건 지정(Visual Database Tools) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- Query Designer [SQL Server], Criteria pane
- queries [Visual Database Tools]
- criteria for search conditions
- search conditions [SQL Server], search criteria
- View Designer, Criteria pane
- row return limitations [SQL Server]
- Criteria pane
- restricting rows returned
- search criteria [SQL Server]
- Visual Database Tools [SQL Server], queries
- limiting rows returned
ms.assetid: 25fb4e31-6dbf-4cf6-8e47-0dd0998c836c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 258aceb348ed3bcd7d4d19201a0169b53b54d711
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650347"
---
# <a name="specify-search-criteria-visual-database-tools"></a><span data-ttu-id="b701e-102">검색 조건 지정(Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="b701e-102">Specify Search Criteria (Visual Database Tools)</span></span>
  <span data-ttu-id="b701e-103">검색 기준을 사용하여 쿼리가 반환하는 행의 수를 제한할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b701e-103">You can use search criteria to restrict the number of rows returned by a query.</span></span>  
  
 <span data-ttu-id="b701e-104">검색 기준을 만드는 특정 단계에 대한 자세한 내용은 다음 표에 나열된 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="b701e-104">For details about the particular steps to creating search criteria, refer to the topics listed in the following table.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b701e-105">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="b701e-105">In This Section</span></span>  
 [<span data-ttu-id="b701e-106">검색 값 입력 규칙&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="b701e-106">Rules for Entering Search Values &#40;Visual Database Tools&#41;</span></span>](visual-database-tools.md)  
 <span data-ttu-id="b701e-107">텍스트, 숫자, 날짜 또는 논리 값을 입력하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="b701e-107">Explains how to enter text, numbers, dates, or logical values.</span></span>  
  
 [<span data-ttu-id="b701e-108">조건 창의 검색 조건 결합 규칙&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="b701e-108">Conventions for Combining Search Conditions in the Criteria Pane &#40;Visual Database Tools&#41;</span></span>](conventions-combine-search-conditions-in-criteria-pane-visual-db-tools.md)  
 <span data-ttu-id="b701e-109">AND 및 OR 연산자를 사용하는 데 필요한 기본 개념을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="b701e-109">Explains the concepts behind using the AND and OR operators.</span></span>  
  
 [<span data-ttu-id="b701e-110">검색 조건 지정&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="b701e-110">Specify Search Conditions &#40;Visual Database Tools&#41;</span></span>](specify-search-conditions-visual-database-tools.md)  
 <span data-ttu-id="b701e-111">필요한 데이터만 얻기 위해 검색 조건을 선택하는 데 필요한 기본 개념을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="b701e-111">Explains the basics of choosing search criteria to get just the data you want.</span></span>  
  
 [<span data-ttu-id="b701e-112">한 열에 여러 검색 조건 지정&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="b701e-112">Specify Multiple Search Conditions for One Column &#40;Visual Database Tools&#41;</span></span>](specify-multiple-search-conditions-for-one-column-visual-database-tools.md)  
 <span data-ttu-id="b701e-113">동일한 데이터 열에 대해 여러 검색 조건을 만드는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="b701e-113">Explains how to create multiple search conditions to the same data column.</span></span>  
  
 [<span data-ttu-id="b701e-114">여러 열에 여러 검색 조건 지정&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="b701e-114">Specify Multiple Search Conditions for Multiple Columns &#40;Visual Database Tools&#41;</span></span>](specify-multiple-search-conditions-for-multiple-columns-visual-database-tools.md)  
 <span data-ttu-id="b701e-115">여러 개의 데이터 열을 하나의 쿼리에 대한 검색 조건의 일부로 포함하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="b701e-115">Explains how to include several data columns as part of the search condition for a query.</span></span>  
  
 [<span data-ttu-id="b701e-116">쿼리에 TOP 절 지정&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="b701e-116">Specify the TOP Clause in Queries &#40;Visual Database Tools&#41;</span></span>](specify-the-top-clause-in-queries-visual-database-tools.md)  
 <span data-ttu-id="b701e-117">지정된 개수나 비율의 행만 반환하도록 만드는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="b701e-117">Explains how to have only a given number or percentage of rows returned.</span></span>  
  
 [<span data-ttu-id="b701e-118">동일한 쿼리에서 HAVING 및 WHERE 절 사용&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="b701e-118">Use HAVING and WHERE Clauses in the Same Query &#40;Visual Database Tools&#41;</span></span>](use-having-and-where-clauses-in-the-same-query-visual-database-tools.md)  
 <span data-ttu-id="b701e-119">쿼리에서 이러한 절을 모두 사용하는 방법과 그 이유에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="b701e-119">Explains how and why to use both of these clauses in a query.</span></span>  
  
 [<span data-ttu-id="b701e-120">값이 일치하지 않는 행 선택&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="b701e-120">Select Rows That Do Not Match a Value &#40;Visual Database Tools&#41;</span></span>](select-rows-that-do-not-match-a-value-visual-database-tools.md)  
 <span data-ttu-id="b701e-121">쿼리 문에 입력한 값과 지정된 열의 값이 일치하지 않는 행을 모두 반환하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="b701e-121">Explains how to return all rows where the value of a give column does not match the value you provide in the query statement.</span></span>  
  
 [<span data-ttu-id="b701e-122">행 포함 또는 제외&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="b701e-122">Include or Exclude Rows &#40;Visual Database Tools&#41;</span></span>](include-or-exclude-rows-visual-database-tools.md)  
 <span data-ttu-id="b701e-123">쿼리에 사용되는 절과 연산자에 대한 기본 개념을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="b701e-123">Explains the concepts behind clauses and operators used in queries.</span></span>  
  
 [<span data-ttu-id="b701e-124">중복 행 제외&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="b701e-124">Exclude Duplicate Rows &#40;Visual Database Tools&#41;</span></span>](exclude-duplicate-rows-visual-database-tools.md)  
 <span data-ttu-id="b701e-125">선택 쿼리에서 중복 행을 필터링하여 제거하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="b701e-125">Explains how to filter duplicate rows out of Select queries.</span></span>  
  
 [<span data-ttu-id="b701e-126">AND에 우선 순위가 있는 조건 조합&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="b701e-126">Combine Conditions When AND Has Precedence &#40;Visual Database Tools&#41;</span></span>](combine-conditions-when-and-has-precedence-visual-database-tools.md)  
 <span data-ttu-id="b701e-127">쿼리 결과를 필터링하기 위해 AND 연산자를 사용하는 방법과 그 이유에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="b701e-127">Explains why and how to use the AND operator to filter query results.</span></span>  
  
 [<span data-ttu-id="b701e-128">OR에 우선 순위가 있는 조건 조합&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="b701e-128">Combine Conditions When OR Has Precedence &#40;Visual Database Tools&#41;</span></span>](combine-conditions-when-or-has-precedence-visual-database-tools.md)  
 <span data-ttu-id="b701e-129">쿼리 결과를 필터링하기 위해 OR 연산자를 사용하는 방법과 그 이유에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="b701e-129">Explains why and how to use the OR operator to filter query results.</span></span>  
  
 [<span data-ttu-id="b701e-130">하위 쿼리 만들기&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="b701e-130">Create Subqueries &#40;Visual Database Tools&#41;</span></span>](create-subqueries-visual-database-tools.md)  
 <span data-ttu-id="b701e-131">하위 쿼리 또는 중첩된 쿼리를 만드는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="b701e-131">Explains how to create subqueries, or nested queries.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="b701e-132">관련 섹션</span><span class="sxs-lookup"><span data-stu-id="b701e-132">Related Sections</span></span>  
 [<span data-ttu-id="b701e-133">쿼리 관련 기본 작업 수행&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="b701e-133">Perform Basic Operations with Queries &#40;Visual Database Tools&#41;</span></span>](perform-basic-operations-with-queries-visual-database-tools.md)  
 <span data-ttu-id="b701e-134">가장 일반적인 쿼리 태스크를 수행하는 단계와 관련된 항목의 링크를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="b701e-134">Provides links to topics with steps for the most common querying tasks.</span></span>  
  
 [<span data-ttu-id="b701e-135">쿼리 형식&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="b701e-135">Types of Queries &#40;Visual Database Tools&#41;</span></span>](types-of-queries-visual-database-tools.md)  
 <span data-ttu-id="b701e-136">지원되는 쿼리 형식에 대해 설명하는 항목의 링크를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="b701e-136">Provides links to topics explaining the supported query types.</span></span>  
  
 [<span data-ttu-id="b701e-137">쿼리 결과 정렬 및 그룹화&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="b701e-137">Sort and Group Query Results &#40;Visual Database Tools&#41;</span></span>](sort-and-group-query-results-visual-database-tools.md)  
 <span data-ttu-id="b701e-138">쿼리 결과를 정렬하고 그룹화하는 단계와 관련된 항목의 링크를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="b701e-138">Provides links to topics with steps for sorting and grouping the results of a query.</span></span>  
  
 [<span data-ttu-id="b701e-139">쿼리 결과 요약&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="b701e-139">Summarize Query Results &#40;Visual Database Tools&#41;</span></span>](summarize-query-results-visual-database-tools.md)  
 <span data-ttu-id="b701e-140">NULL 및 숫자 이외의 열을 비롯한 결과를 요약하는 단계와 관련된 항목의 링크를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="b701e-140">Provides links to topics with steps for summarizing results, including NULL and Nonnumeric columns.</span></span>  
  
 [<span data-ttu-id="b701e-141">쿼리 및 뷰 디자인 방법 도움말 항목&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="b701e-141">Design Queries and Views How-to Topics &#40;Visual Database Tools&#41;</span></span>](design-queries-and-views-how-to-topics-visual-database-tools.md)  
 <span data-ttu-id="b701e-142">쿼리 및 뷰 디자이너를 사용하여 쿼리와 뷰에서 수행할 수 있는 작업에 대해 설명하는 항목과 섹션의 링크를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="b701e-142">Provides links to topics and sections covering work you can do in queries and views using the Query and View Designer.</span></span>  
  
  
