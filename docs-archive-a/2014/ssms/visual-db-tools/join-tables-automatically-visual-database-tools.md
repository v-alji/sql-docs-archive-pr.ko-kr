---
title: 테이블 자동 조인(Visual Database Tools) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- automatic joins
- joins [SQL Server], creating
- joins [SQL Server], automatic
ms.assetid: f152af82-bcb6-49ca-af19-48cdb7fc9ac6
author: stevestein
ms.author: sstein
ms.openlocfilehash: d05100f801d972759c1b5c105814f5cdbdccf84f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727760"
---
# <a name="join-tables-automatically-visual-database-tools"></a><span data-ttu-id="4b7e7-102">테이블 자동 조인(Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="4b7e7-102">Join Tables Automatically (Visual Database Tools)</span></span>
  <span data-ttu-id="4b7e7-103">쿼리에 두 개 이상의 테이블을 추가하면 [쿼리 및 뷰 디자이너](visual-database-tools.md) 가 해당 테이블 사이의 관련성을 판단합니다.</span><span class="sxs-lookup"><span data-stu-id="4b7e7-103">When you add two or more tables to a query, the [Query and View Designer](visual-database-tools.md) attempts to determine if they are related.</span></span> <span data-ttu-id="4b7e7-104">관련이 있는 경우 쿼리 및 뷰 디자이너는 테이블 또는 테이블 구조 개체를 나타내는 사각형 사이에 자동으로 조인 선을 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="4b7e7-104">If they are, the Query and View Designer automatically puts join lines between the rectangles representing the tables or table-structured objects.</span></span>  
  
 <span data-ttu-id="4b7e7-105">다음과 같은 경우 쿼리 및 뷰 디자이너는 테이블이 조인되었다고 판단합니다.</span><span class="sxs-lookup"><span data-stu-id="4b7e7-105">The Query and View Designer will recognize tables as joined if:</span></span>  
  
-   <span data-ttu-id="4b7e7-106">데이터베이스에 테이블 관련성을 지정하는 정보가 포함된 경우</span><span class="sxs-lookup"><span data-stu-id="4b7e7-106">The database contains information that specifies that the tables are related.</span></span>  
  
-   <span data-ttu-id="4b7e7-107">이름과 데이터 형식이 같은 두 개의 열이 각 테이블에 하나씩 있는 경우.</span><span class="sxs-lookup"><span data-stu-id="4b7e7-107">If two columns, one in each table, have the same name and data type.</span></span> <span data-ttu-id="4b7e7-108">이 열은 하나 이상의 테이블에서 기본 키여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4b7e7-108">The column must be a primary key in at least one of the tables.</span></span> <span data-ttu-id="4b7e7-109">예를 들어, `employee` 와 `jobs` 테이블을 추가하고 `job_id` 열이 `jobs` 테이블의 기본 키이며 각 테이블에 데이터 형식이 같은 `job_id` 라는 열이 있는 경우 쿼리 및 뷰 디자이너는 이 두 테이블을 자동으로 조인합니다.</span><span class="sxs-lookup"><span data-stu-id="4b7e7-109">For example, if you add `employee` and `jobs` tables, if the `job_id` column is the primary key in the `jobs` table, and if each table has a column called `job_id` with the same data type, the Query and View Designer will automatically join the tables.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="4b7e7-110">쿼리 및 뷰 디자이너는 이름과 데이터 형식이 같은 열을 기반으로 하여 조인을 하나만 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="4b7e7-110">The Query and View Designer will create only one join based on columns with the same name and data type.</span></span> <span data-ttu-id="4b7e7-111">둘 이상의 조인이 가능한 경우에도 쿼리 및 뷰 디자이너는 처음 발견한 일치 열 집합을 기반으로 해서 하나의 조인을 만든 다음 조인 작업을 중단합니다.</span><span class="sxs-lookup"><span data-stu-id="4b7e7-111">If more than one join is possible, the Query and View Designer stops after creating a join based on the first set of matching columns that it finds.</span></span>  
  
-   <span data-ttu-id="4b7e7-112">쿼리 및 뷰 디자이너에서 검색 조건(WHERE 절)이 실제 조인 조건임을 감지하는 경우.</span><span class="sxs-lookup"><span data-stu-id="4b7e7-112">The Query and View Designer detects that a search condition (a WHERE clause) is actually a join condition.</span></span> <span data-ttu-id="4b7e7-113">예를 들어, `employee` 및 `jobs`테이블을 추가한 다음 두 테이블의 `job_id` 열에서 같은 값을 검색하는 검색 조건을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4b7e7-113">For example, you might add the tables `employee` and `jobs`, then create a search condition that searches for the same value in the `job_id` column of both tables.</span></span> <span data-ttu-id="4b7e7-114">이때 쿼리 및 뷰 디자이너는 검색 조건의 결과로 조인이 만들어짐을 감지하여 검색 조건을 기반으로 해서 조인 조건을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="4b7e7-114">When you do, the Query and View Designer detects that the search condition results in a join, and then creates a join condition based on the search condition.</span></span>  
  
 <span data-ttu-id="4b7e7-115">쿼리 및 뷰 디자이너가 사용자 쿼리에 적합하지 않은 조인을 만든 경우 조인을 수정하거나 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4b7e7-115">If the Query and View Designer has created a join that is not suitable to your query, you can modify the join or remove it.</span></span> <span data-ttu-id="4b7e7-116">자세한 내용은 [조인 연산자 수정&#40;Visual Database Tools&#41;](modify-join-operators-visual-database-tools.md) 및 [조인 제거&#40;Visual Database Tools&#41;](remove-joins-visual-database-tools.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4b7e7-116">For details, see [Modify Join Operators &#40;Visual Database Tools&#41;](modify-join-operators-visual-database-tools.md) and [Remove Joins &#40;Visual Database Tools&#41;](remove-joins-visual-database-tools.md).</span></span>  
  
 <span data-ttu-id="4b7e7-117">쿼리 및 뷰 디자이너가 사용자 쿼리에 있는 테이블을 자동으로 조인하지 않는 경우 사용자가 직접 조인을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4b7e7-117">If the Query and View Designer does not automatically join the tables in your query, you can create a join yourself.</span></span> <span data-ttu-id="4b7e7-118">자세한 내용은 [테이블 수동 조인&#40;Visual Database Tools&#41;](join-tables-manually-visual-database-tools.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4b7e7-118">For details, see [Join Tables Manually &#40;Visual Database Tools&#41;](join-tables-manually-visual-database-tools.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b7e7-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4b7e7-119">See Also</span></span>  
 <span data-ttu-id="4b7e7-120">[쿼리 및 뷰 디자이너에서 Visual Database Tools &#40;조인을 나타내는 방법&#41;](how-the-query-and-view-designer-represents-joins-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="4b7e7-120">[How the Query and View Designer Represents Joins &#40;Visual Database Tools&#41;](how-the-query-and-view-designer-represents-joins-visual-database-tools.md) </span></span>  
 <span data-ttu-id="4b7e7-121">[쿼리 및 뷰 디자인 방법 도움말 항목 &#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="4b7e7-121">[Design Queries and Views How-to Topics &#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="4b7e7-122">조인을 사용한 쿼리&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="4b7e7-122">Query with Joins &#40;Visual Database Tools&#41;</span></span>](query-with-joins-visual-database-tools.md)  
  
  
