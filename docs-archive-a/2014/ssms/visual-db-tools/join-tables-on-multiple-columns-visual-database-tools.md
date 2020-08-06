---
title: 여러 열에 대해 테이블 조인(Visual Database Tools) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- multiple column joins
- joins [SQL Server], multiple columns
ms.assetid: 56a158bc-a42a-4b78-baad-4721d2d22cd3
author: stevestein
ms.author: sstein
ms.openlocfilehash: dda52fe27b2034242c8cbf458dd010240c792146
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651419"
---
# <a name="join-tables-on-multiple-columns-visual-database-tools"></a><span data-ttu-id="577ef-102">여러 열에 대해 테이블 조인(Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="577ef-102">Join Tables on Multiple Columns (Visual Database Tools)</span></span>
  <span data-ttu-id="577ef-103">테이블을 여러 열과 조인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="577ef-103">You can join tables with multiple columns.</span></span> <span data-ttu-id="577ef-104">즉, 여러 조건을 만족하는 경우에만 두 테이블에서 행이 일치하는 쿼리를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="577ef-104">That is, you can create a query that matches rows from the two tables only if they satisfy multiple conditions.</span></span> <span data-ttu-id="577ef-105">한 테이블에 있는 여러 외래 키 열이 다른 테이블에 있는 여러 기본 키 열과 일치하는 관계가 데이터베이스에 포함된 경우 이 관계를 사용하여 여러 열 조인을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="577ef-105">If the database contains a relationship matching multiple foreign-key columns in one table to a multicolumn primary key in the other table, you can use this relationship to create a multicolumn join.</span></span> <span data-ttu-id="577ef-106">자세한 내용은 [테이블 자동 조인&#40;Visual Database Tools&#41;](visual-database-tools.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="577ef-106">For details, see [Join Tables Automatically &#40;Visual Database Tools&#41;](visual-database-tools.md).</span></span>  
  
 <span data-ttu-id="577ef-107">데이터베이스에 여러 외래 키 열 관계가 포함되지 않은 경우에도 조인을 수동으로 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="577ef-107">Even if the database contains no multi-column foreign-key relationship, you can create the join manually.</span></span>  
  
### <a name="to-manually-create-a-multicolumn-join"></a><span data-ttu-id="577ef-108">여러 열 조인을 수동으로 만들려면</span><span class="sxs-lookup"><span data-stu-id="577ef-108">To manually create a multicolumn join</span></span>  
  
1.  <span data-ttu-id="577ef-109">조인할 테이블을 [다이어그램 창](diagram-pane-visual-database-tools.md) 에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="577ef-109">Add to the [Diagram pane](diagram-pane-visual-database-tools.md) the tables you want to join.</span></span>  
  
2.  <span data-ttu-id="577ef-110">첫 번째 테이블 창의 첫 번째 조인 열 이름을 끌어서 두 번째 테이블 창의 관련 열 위에 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="577ef-110">Drag the name of the first join column in the first table window and drop it onto the related column in the second table window.</span></span> <span data-ttu-id="577ef-111">텍스트, ntext, 또는 이미지 열을 기반으로 할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="577ef-111">You cannot base a join on text, ntext, or image columns.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="577ef-112">일반적으로 조인 열의 데이터 형식은 같거나 호환 가능해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="577ef-112">In general, the join columns must be of the same (or compatible) data types.</span></span> <span data-ttu-id="577ef-113">예를 들어, 첫 번째 테이블의 조인 열이 날짜이면 이 열을 두 번째 테이블의 날짜 열과 관련시켜야 합니다.</span><span class="sxs-lookup"><span data-stu-id="577ef-113">For example, if the join column in the first table is a date, you must relate it to a date column in the second table.</span></span> <span data-ttu-id="577ef-114">반면에 첫 번째 조인 열이 정수이면 관련된 조인 열의 데이터 형식도 정수이어야 하지만 크기는 달라도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="577ef-114">On the other hand, if the first join column is an integer, the related join column must also be of an integer data type, but it can be a different size.</span></span> <span data-ttu-id="577ef-115">그러나 경우에 따라서는 암시적 데이터 형식 변환으로 외관상 호환되지 않는 열을 조인할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="577ef-115">However, there may be cases where implicit data type conversions can join seemingly incompatible columns will work.</span></span>  
    >   
    >  <span data-ttu-id="577ef-116">[쿼리 및 뷰 디자이너](query-and-view-designer-tools-visual-database-tools.md) 는 조인을 만드는 데 사용하는 열의 데이터 형식을 검사하지 않지만 데이터 형식이 호환되지 않으면 쿼리를 실행할 때 데이터베이스에 오류 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="577ef-116">The [Query and View Designer](query-and-view-designer-tools-visual-database-tools.md) will not check the data types of the columns you use to create a join, but when you execute the query, the database will display an error if the data types are not compatible.</span></span>  
  
3.  <span data-ttu-id="577ef-117">첫 번째 테이블 창의 두 번째 조인 열 이름을 끌어서 두 번째 테이블 창의 관련 열 위에 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="577ef-117">Drag the name of the second join column in the first table window and drop it onto the related column in the second table window.</span></span>  
  
4.  <span data-ttu-id="577ef-118">두 테이블에 있는 각 추가 조인 열 쌍에 대해 3단계를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="577ef-118">Repeat step 3 for each additional pair of join columns in the two tables.</span></span>  
  
5.  <span data-ttu-id="577ef-119">쿼리를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="577ef-119">Run the query.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="577ef-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="577ef-120">See Also</span></span>  
 [<span data-ttu-id="577ef-121">조인을 사용한 쿼리&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="577ef-121">Query with Joins &#40;Visual Database Tools&#41;</span></span>](query-with-joins-visual-database-tools.md)  
  
  
