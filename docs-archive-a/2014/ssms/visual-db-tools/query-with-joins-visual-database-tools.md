---
title: 조인을 사용한 쿼리(Visual Database Tools) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- queries [Visual Database Tools]
- View Designer, joins
- table joins [SQL Server]
- multiple table joins
- Visual Database Tools [SQL Server], queries
- Query Designer [SQL Server], joins
- joins [SQL Server], queries
ms.assetid: 8f068207-d777-4e64-8c4c-d821f0ddb450
author: stevestein
ms.author: sstein
ms.openlocfilehash: 9d0053e6786d96508be8a87347cdc0b19975a3fe
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729992"
---
# <a name="query-with-joins-visual-database-tools"></a><span data-ttu-id="38262-102">조인을 사용한 쿼리(Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="38262-102">Query with Joins (Visual Database Tools)</span></span>
  <span data-ttu-id="38262-103">쿼리 결과에 여러 테이블 또는 테이블 반환 개체의 데이터가 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38262-103">A query result can include data from multiple tables or table-valued objects.</span></span> <span data-ttu-id="38262-104">여러 테이블 반환 개체에 있는 데이터를 조합하려면 SQL에서 JOIN 연산을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="38262-104">To combine data from multiple table-valued objects, you use the JOIN operation from SQL.</span></span>  
  
 <span data-ttu-id="38262-105">여러 테이블을 사용하는 쿼리를 작성하는 방법은 다음 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="38262-105">For information about creating queries using multiple tables, see the following topics.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="38262-106">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="38262-106">In This Section</span></span>  
 [<span data-ttu-id="38262-107">조인 연산자 수정&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="38262-107">Modify Join Operators &#40;Visual Database Tools&#41;</span></span>](visual-database-tools.md)  
 <span data-ttu-id="38262-108">등호(=) 이외의 연산자를 사용하여 테이블을 조인하도록 지정하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="38262-108">Specify that tables should be joined using an operator other than equal (=).</span></span>  
  
 [<span data-ttu-id="38262-109">쿼리 및 뷰 디자이너의 조인 표시 방법&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="38262-109">How the Query and View Designer Represents Joins &#40;Visual Database Tools&#41;</span></span>](how-the-query-and-view-designer-represents-joins-visual-database-tools.md)  
 <span data-ttu-id="38262-110">다이어그램 창에 표시되는 조인의 그래픽 표현에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="38262-110">Explains the graphic representation of the join as you see it in the Diagram pane.</span></span>  
  
 [<span data-ttu-id="38262-111">테이블 자동 조인&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="38262-111">Join Tables Automatically &#40;Visual Database Tools&#41;</span></span>](join-tables-automatically-visual-database-tools.md)  
 <span data-ttu-id="38262-112">테이블을 조인해야 할지 여부를 쿼리 및 뷰 디자이너에서 결정하도록 만드는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="38262-112">Steps for allowing the Query and View Designer determine if tables should be joined.</span></span>  
  
 [<span data-ttu-id="38262-113">테이블 수동 조인&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="38262-113">Join Tables Manually &#40;Visual Database Tools&#41;</span></span>](join-tables-manually-visual-database-tools.md)  
 <span data-ttu-id="38262-114">다이어그램 창에서 조인을 직접 만드는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="38262-114">Steps for creating a join manually in the Diagram pane.</span></span>  
  
 [<span data-ttu-id="38262-115">여러 열에 대해 테이블 조인&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="38262-115">Join Tables on Multiple Columns &#40;Visual Database Tools&#41;</span></span>](join-tables-on-multiple-columns-visual-database-tools.md)  
 <span data-ttu-id="38262-116">각 테이블마다 여러 조건이 있는 테이블을 조인하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="38262-116">Steps for joining tables with multiple criteria for each table.</span></span>  
  
 [<span data-ttu-id="38262-117">외부 조인 만들기&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="38262-117">Create Outer Joins &#40;Visual Database Tools&#41;</span></span>](create-outer-joins-visual-database-tools.md)  
 <span data-ttu-id="38262-118">해당 테이블에서 행이 일치하지 않는 경우에도 조인된 테이블이 행을 포함하도록 지정하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="38262-118">Specify that joined tables should include rows even when they do not match rows in the corresponding table.</span></span>  
  
 [<span data-ttu-id="38262-119">조인 제거&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="38262-119">Remove Joins &#40;Visual Database Tools&#41;</span></span>](remove-joins-visual-database-tools.md)  
 <span data-ttu-id="38262-120">테이블 사이에서 조인을 제거하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="38262-120">Steps for removing a join between tables.</span></span>  
  
 [<span data-ttu-id="38262-121">자체 조인 자동으로 만들기&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="38262-121">Create Self-Joins Automatically &#40;Visual Database Tools&#41;</span></span>](create-self-joins-automatically-visual-database-tools.md)  
 <span data-ttu-id="38262-122">쿼리 및 뷰 디자이너를 사용하여 자체 조인을 만드는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="38262-122">Steps for allowing the Query and View Designer to create a self-join.</span></span>  
  
 [<span data-ttu-id="38262-123">수동으로 자체 조인 만들기&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="38262-123">Create Self-Joins Manually &#40;Visual Database Tools&#41;</span></span>](create-self-joins-manually-visual-database-tools.md)  
 <span data-ttu-id="38262-124">조인을 사용하여 단일 테이블에 포함된 데이터의 하위 집합을 찾는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="38262-124">Steps for using a join to find subsets of data within a single table.</span></span>  
  
 [<span data-ttu-id="38262-125">조인 속성 보기&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="38262-125">View Join Properties &#40;Visual Database Tools&#41;</span></span>](view-join-properties-visual-database-tools.md)  
 <span data-ttu-id="38262-126">조인의 속성을 보는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="38262-126">Steps for viewing the properties of a join.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="38262-127">관련 섹션</span><span class="sxs-lookup"><span data-stu-id="38262-127">Related Sections</span></span>  
 [<span data-ttu-id="38262-128">쿼리 형식&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="38262-128">Types of Queries &#40;Visual Database Tools&#41;</span></span>](types-of-queries-visual-database-tools.md)  
 <span data-ttu-id="38262-129">지원되는 쿼리 형식에 대해 설명하는 항목의 링크를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="38262-129">Provides links to topics describing the supported query types.</span></span>  
  
 [<span data-ttu-id="38262-130">쿼리 관련 기본 작업 수행&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="38262-130">Perform Basic Operations with Queries &#40;Visual Database Tools&#41;</span></span>](perform-basic-operations-with-queries-visual-database-tools.md)  
 <span data-ttu-id="38262-131">가장 일반적인 쿼리 태스크에 관련된 항목의 링크를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="38262-131">Provides links to topics covering the most common query tasks.</span></span>  
  
 [<span data-ttu-id="38262-132">검색 조건 지정&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="38262-132">Specify Search Criteria &#40;Visual Database Tools&#41;</span></span>](specify-search-criteria-visual-database-tools.md)  
 <span data-ttu-id="38262-133">다양한 종류의 검색 조건과 그러한 조건을 사용하는 방법에 대해 설명하는 항목의 링크를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="38262-133">Provides links to topics covering the various kinds of search criteria and how to use them.</span></span>  
  
  
