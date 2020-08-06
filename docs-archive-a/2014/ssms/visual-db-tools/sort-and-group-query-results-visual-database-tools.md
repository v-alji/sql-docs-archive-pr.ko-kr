---
title: 쿼리 결과 정렬 및 그룹화(Visual Database Tools) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- View Designer, Results pane
- result sets [SQL Server], queries
- queries [SQL Server], groups
- Query Designer [SQL Server], Results pane
- results [SQL Server], query
- grouping query results
- row sorting [SQL Server]
- queries [SQL Server], results
- ordering query results [SQL Server]
- Results pane
- sorting query results [SQL Server]
ms.assetid: b004e1c0-cacc-4241-9426-9fd426978918
author: stevestein
ms.author: sstein
ms.openlocfilehash: fdaede20960356404cd0319c213abb76a19b8a77
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727720"
---
# <a name="sort-and-group-query-results-visual-database-tools"></a><span data-ttu-id="b65f6-102">쿼리 결과 정렬 및 그룹화(Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="b65f6-102">Sort and Group Query Results (Visual Database Tools)</span></span>
  <span data-ttu-id="b65f6-103">쿼리 결과의 각 결과 행이 원본 데이터의 전체 행 그룹에 대응하는 쿼리 결과를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b65f6-103">You can create a query result in which each result row corresponds to an entire group of rows from the original data.</span></span>  
  
 <span data-ttu-id="b65f6-104">그와 같은 쿼리를 만드는 방법에 대한 자세한 내용은 아래 표에 나와 있는 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="b65f6-104">To learn the details about creating such queries, see the topics listed in the following table.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b65f6-105">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="b65f6-105">In This Section</span></span>  
 [<span data-ttu-id="b65f6-106">행 정렬&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="b65f6-106">Sort Rows &#40;Visual Database Tools&#41;</span></span>](visual-database-tools.md)  
 <span data-ttu-id="b65f6-107">행을 정렬하는 다양한 방법과 그러한 방법을 사용하는 이유에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="b65f6-107">Describes the various ways in which you can sort rows and why you would use them.</span></span>  
  
 [<span data-ttu-id="b65f6-108">행 그룹 축소&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="b65f6-108">Collapse Groups of Rows &#40;Visual Database Tools&#41;</span></span>](collapse-groups-of-rows-visual-database-tools.md)  
 <span data-ttu-id="b65f6-109">중복 제거나 계산 등과 같이 행의 데이터를 정렬하는 다양한 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="b65f6-109">Describes the various ways to collapse rows, such as calculating or eliminating duplicates.</span></span>  
  
 [<span data-ttu-id="b65f6-110">ORDER BY를 사용하여 정렬&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="b65f6-110">Sort with ORDER BY &#40;Visual Database Tools&#41;</span></span>](sort-with-order-by-visual-database-tools.md)  
 <span data-ttu-id="b65f6-111">지정된 순서로 결과를 반환하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="b65f6-111">Provides steps for returning results in a specified order.</span></span>  
  
 [<span data-ttu-id="b65f6-112">오름차순 또는 내림차순으로 정렬&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="b65f6-112">Sort in Ascending or Descending Order &#40;Visual Database Tools&#41;</span></span>](sort-in-ascending-or-descending-order-visual-database-tools.md)  
 <span data-ttu-id="b65f6-113">정렬 방향을 변경하거나 설정하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="b65f6-113">Provides steps for changing or setting sort direction.</span></span>  
  
 [<span data-ttu-id="b65f6-114">쿼리에서 여러 열 정렬&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="b65f6-114">Sort Multiple Columns in Queries &#40;Visual Database Tools&#41;</span></span>](sort-multiple-columns-in-queries-visual-database-tools.md)  
 <span data-ttu-id="b65f6-115">여러 열에 대한 결과 집합의 순서를 설정하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="b65f6-115">Provides steps for setting the order of results sets for multiple columns.</span></span>  
  
 [<span data-ttu-id="b65f6-116">쿼리 결과 행 그룹화&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="b65f6-116">Group Rows in Query Results &#40;Visual Database Tools&#41;</span></span>](group-rows-in-query-results-visual-database-tools.md)  
 <span data-ttu-id="b65f6-117">데이터를 그룹으로 구성하여 요약 정보의 하위 집합을 만드는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="b65f6-117">Provides steps for creating subsets of summary information by organizing data into groups.</span></span>  
  
 [<span data-ttu-id="b65f6-118">그룹 조건 지정&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="b65f6-118">Specify Conditions for Groups &#40;Visual Database Tools&#41;</span></span>](specify-conditions-for-groups-visual-database-tools.md)  
 <span data-ttu-id="b65f6-119">행 그룹에 적용되는 검색 조건을 만드는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="b65f6-119">Provides steps for creating search conditions that apply to groups of rows.</span></span>  
  
 [<span data-ttu-id="b65f6-120">출력 열 다시 정렬&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="b65f6-120">Reorder Output Columns &#40;Visual Database Tools&#41;</span></span>](reorder-output-columns-visual-database-tools.md)  
 <span data-ttu-id="b65f6-121">현재 정렬 설정을 변경하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="b65f6-121">Provides steps for changing current sorting settings.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="b65f6-122">관련 섹션</span><span class="sxs-lookup"><span data-stu-id="b65f6-122">Related Sections</span></span>  
 [<span data-ttu-id="b65f6-123">쿼리 결과 요약&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="b65f6-123">Summarize Query Results &#40;Visual Database Tools&#41;</span></span>](summarize-query-results-visual-database-tools.md)  
 <span data-ttu-id="b65f6-124">쿼리 결과 요약에 대해 설명하는 항목의 링크를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="b65f6-124">Provides links to topics on summarizing query results.</span></span>  
  
 [<span data-ttu-id="b65f6-125">쿼리 관련 기본 작업 수행&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="b65f6-125">Perform Basic Operations with Queries &#40;Visual Database Tools&#41;</span></span>](perform-basic-operations-with-queries-visual-database-tools.md)  
 <span data-ttu-id="b65f6-126">가장 일반적인 쿼리 태스크에 관련된 항목의 링크를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="b65f6-126">Provides links to topics covering the most common query tasks.</span></span>  
  
 [<span data-ttu-id="b65f6-127">쿼리 및 뷰 디자인 방법 도움말 항목&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="b65f6-127">Design Queries and Views How-to Topics &#40;Visual Database Tools&#41;</span></span>](design-queries-and-views-how-to-topics-visual-database-tools.md)  
 <span data-ttu-id="b65f6-128">쿼리 및 뷰 디자이너를 사용하는 방법과 관련된 항목에 대한 링크를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="b65f6-128">Provides links to topics covering how to use the Query and View Designer.</span></span>  
  
  
