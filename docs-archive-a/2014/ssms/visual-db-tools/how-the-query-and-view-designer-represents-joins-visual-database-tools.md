---
title: 쿼리 및 뷰 디자이너의 조인 표시 방법 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL pane [Visual Database Tools]
- joins [SQL Server], Query and View Designer
- Diagram pane [Visual Database Tools]
ms.assetid: 20a99dcb-83bd-4aa6-9139-92e2e5ba4887
author: stevestein
ms.author: sstein
ms.openlocfilehash: 55fdea533436f9fa7c2a902667b3166085c27e99
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651975"
---
# <a name="how-the-query-and-view-designer-represents-joins-visual-database-tools"></a><span data-ttu-id="45130-102">쿼리 및 뷰 디자이너의 조인 표시 방법(Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="45130-102">How the Query and View Designer Represents Joins (Visual Database Tools)</span></span>
  <span data-ttu-id="45130-103">테이블이 조인되면 [쿼리 및 뷰 디자이너](visual-database-tools.md) 는 [다이어그램 창](diagram-pane-visual-database-tools.md) 에 조인을 그래픽으로 나타내고 [SQL 창](sql-pane-visual-database-tools.md)에 SQL 구문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="45130-103">If tables are joined, the [Query and View Designer](visual-database-tools.md) represents the join graphically in the [Diagram pane](diagram-pane-visual-database-tools.md) and by using SQL syntax in the [SQL pane](sql-pane-visual-database-tools.md).</span></span>  
  
## <a name="diagram-pane"></a><span data-ttu-id="45130-104">다이어그램 창</span><span class="sxs-lookup"><span data-stu-id="45130-104">Diagram Pane</span></span>  
 <span data-ttu-id="45130-105">다이어그램 창에서 쿼리 및 뷰 디자이너는 조인에 포함된 데이터 열 사이에 조인 선을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="45130-105">In the Diagram pane the Query and View Designer displays a join line between the data columns involved in the join.</span></span> <span data-ttu-id="45130-106">쿼리 및 뷰 디자이너는 각 조인 조건에 대해 한 개의 조인 선을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="45130-106">The Query and View Designer displays one join line for each join condition.</span></span> <span data-ttu-id="45130-107">예를 들어, 아래 그림은 조인된 두 테이블 사이에 있는 조인 선을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="45130-107">For example, the following illustration shows a join line between two tables that are joined:</span></span>  
  
 <span data-ttu-id="45130-108">![조인 선은 두 테이블 간 관계를 보여 줌](../../database-engine/media//dv3wbig.gif "조인 선은 두 테이블 간 관계를 보여 줌")</span><span class="sxs-lookup"><span data-stu-id="45130-108">![Join line shows relationship between two tables](../../database-engine/media//dv3wbig.gif "Join line shows relationship between two tables")</span></span>  
  
 <span data-ttu-id="45130-109">테이블이 두 개 이상의 조인 조건을 사용하여 조인된 경우 쿼리 및 뷰 디자이너는 다음 예에서와 같이 여러 개의 조인 선을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="45130-109">If tables are joined using more than one join condition, the Query and View Designer displays multiple join lines, as in the following example:</span></span>  
  
 <span data-ttu-id="45130-110">![둘 이상의 조인 조건을 사용하여 테이블 조인](../../database-engine/media//dv3w9n1.gif "둘 이상의 조인 조건을 사용하여 테이블 조인")</span><span class="sxs-lookup"><span data-stu-id="45130-110">![Tables joined using more than one join condition](../../database-engine/media//dv3w9n1.gif "Tables joined using more than one join condition")</span></span>  
  
 <span data-ttu-id="45130-111">예를 들어, 테이블 또는 테이블 구조 개체를 나타내는 사각형이 최소화되거나 조인에 식이 포함되어 조인된 데이터 열이 표시되지 않는 경우 쿼리 및 뷰 디자이너는 테이블 또는 테이블 구조 개체를 나타내는 사각형의 제목 표시줄에 조인 선을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="45130-111">If the joined data columns are not displayed (for example, the rectangle representing the table or table-structured object is minimized or the join involves an expression), the Query and View Designer places the join line at the title bar of the rectangle representing the table or table-structured object.</span></span>  
  
 <span data-ttu-id="45130-112">조인 선의 가운데 있는 아이콘 모양은 테이블 또는 테이블 구조 개체가 조인되는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="45130-112">The shape of the icon in the middle of the join line indicates how the tables or table-structured objects are joined.</span></span> <span data-ttu-id="45130-113">조인 절이 등호(=) 이외의 연산자를 사용하는 경우 조인 선 아이콘에 해당 연산자가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="45130-113">If the join clause uses an operator other than equal (=), the operator appears in the join line icon.</span></span> <span data-ttu-id="45130-114">다음 표는 조인 선에 표시되는 아이콘 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="45130-114">The following table lists the icons that appear in the join line.</span></span>  
  
|<span data-ttu-id="45130-115">**조인 선 아이콘**</span><span class="sxs-lookup"><span data-stu-id="45130-115">**Join line icon**</span></span>|<span data-ttu-id="45130-116">**설명**</span><span class="sxs-lookup"><span data-stu-id="45130-116">**Description**</span></span>|  
|------------------------|---------------------|  
|<span data-ttu-id="45130-117">![Visual Database Tools 아이콘](../../database-engine/media//dv3wbih.gif "Visual Database Tools 아이콘")</span><span class="sxs-lookup"><span data-stu-id="45130-117">![Visual Database Tools icon](../../database-engine/media//dv3wbih.gif "Visual Database Tools icon")</span></span>|<span data-ttu-id="45130-118">등호(=)를 사용하여 만든 내부 조인</span><span class="sxs-lookup"><span data-stu-id="45130-118">Inner join (created using an equal sign).</span></span>|  
|<span data-ttu-id="45130-119">![Visual Database Tools 아이콘](../../database-engine/media//dv3wbii.gif "Visual Database Tools 아이콘")</span><span class="sxs-lookup"><span data-stu-id="45130-119">![Visual Database Tools icon](../../database-engine/media//dv3wbii.gif "Visual Database Tools icon")</span></span>|<span data-ttu-id="45130-120">">" 연산자를 기반으로 하는 내부 조인</span><span class="sxs-lookup"><span data-stu-id="45130-120">Inner join based on the "greater than" operator.</span></span>|  
|<span data-ttu-id="45130-121">![Visual Database Tools 아이콘](../../database-engine/media//dv3wbij.gif "Visual Database Tools 아이콘")</span><span class="sxs-lookup"><span data-stu-id="45130-121">![Visual Database Tools icon](../../database-engine/media//dv3wbij.gif "Visual Database Tools icon")</span></span>|<span data-ttu-id="45130-122">관련 테이블에 일치하는 내용이 없는 경우에도 왼쪽에 나타난 테이블의 모든 행을 포함하는 외부 조인</span><span class="sxs-lookup"><span data-stu-id="45130-122">Outer join in which all rows from the table represented on the left will be included, even if they do not have matches in the related table.</span></span>|  
|<span data-ttu-id="45130-123">![Visual Database Tools 아이콘](../../database-engine/media//dv3wbik.gif "Visual Database Tools 아이콘")</span><span class="sxs-lookup"><span data-stu-id="45130-123">![Visual Database Tools icon](../../database-engine/media//dv3wbik.gif "Visual Database Tools icon")</span></span>|<span data-ttu-id="45130-124">관련 테이블에 일치하는 내용이 없는 경우에도 오른쪽에 나타난 테이블의 모든 행을 포함하는 외부 조인</span><span class="sxs-lookup"><span data-stu-id="45130-124">Outer join in which all rows from the table represented on the right will be included, even if they do not have matches in the related table.</span></span>|  
|<span data-ttu-id="45130-125">![Visual Database Tools 아이콘](../../database-engine/media//dv3wbil.gif "Visual Database Tools 아이콘")</span><span class="sxs-lookup"><span data-stu-id="45130-125">![Visual Database Tools icon](../../database-engine/media//dv3wbil.gif "Visual Database Tools icon")</span></span>|<span data-ttu-id="45130-126">관련 테이블에 일치하는 내용이 없는 경우에도 양쪽 테이블의 모든 행을 포함하는 완전 외부 조인</span><span class="sxs-lookup"><span data-stu-id="45130-126">Full outer join in which all rows from both tables will be included, even if they do not have matches in the related table.</span></span>|  
  
 <span data-ttu-id="45130-127">조인 선의 끝에 있는 기호는 조인 형식을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="45130-127">The symbols on the ends of the join line indicate the type of join.</span></span> <span data-ttu-id="45130-128">다음 표는 조인 형식과 조인 선의 끝에 표시되는 아이콘 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="45130-128">The following table lists the types of joins and the icons displayed on the ends of the join line.</span></span>  
  
|<span data-ttu-id="45130-129">**조인 선 끝의 아이콘**</span><span class="sxs-lookup"><span data-stu-id="45130-129">**Icon on ends of join line**</span></span>|<span data-ttu-id="45130-130">**조인 형식**</span><span class="sxs-lookup"><span data-stu-id="45130-130">**Type of join**</span></span>|  
|-----------------------------------|----------------------|  
|<span data-ttu-id="45130-131">![Visual Database Tools 아이콘](../../database-engine/media//dv3wbim.gif "Visual Database Tools 아이콘")</span><span class="sxs-lookup"><span data-stu-id="45130-131">![Visual Database Tools icon](../../database-engine/media//dv3wbim.gif "Visual Database Tools icon")</span></span>|<span data-ttu-id="45130-132">일 대 일 조인</span><span class="sxs-lookup"><span data-stu-id="45130-132">One-to-one join.</span></span>|  
|<span data-ttu-id="45130-133">![Visual Database Tools 아이콘](../../database-engine/media//dv3wbin.gif "Visual Database Tools 아이콘")</span><span class="sxs-lookup"><span data-stu-id="45130-133">![Visual Database Tools icon](../../database-engine/media//dv3wbin.gif "Visual Database Tools icon")</span></span>|<span data-ttu-id="45130-134">일 대 다 조인</span><span class="sxs-lookup"><span data-stu-id="45130-134">One-to-many join.</span></span>|  
|<span data-ttu-id="45130-135">![Visual Database Tools 아이콘](../../database-engine/media//dv3wbio.gif "Visual Database Tools 아이콘")</span><span class="sxs-lookup"><span data-stu-id="45130-135">![Visual Database Tools icon](../../database-engine/media//dv3wbio.gif "Visual Database Tools icon")</span></span>|<span data-ttu-id="45130-136">쿼리 및 뷰 디자이너는 조인 형식을 결정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="45130-136">Query and View Designer cannot determine the join type.</span></span> <span data-ttu-id="45130-137">조인을 수동으로 만든 경우 이러한 상황이 자주 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="45130-137">This situation occurs most often when you have created a join manually.</span></span>|  
  
## <a name="sql-pane"></a><span data-ttu-id="45130-138">SQL 창</span><span class="sxs-lookup"><span data-stu-id="45130-138">SQL Pane</span></span>  
 <span data-ttu-id="45130-139">SQL 문에서는 다양한 방법으로 조인을 표현할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45130-139">A join can be expressed in a number of ways in an SQL statement.</span></span> <span data-ttu-id="45130-140">정확한 구문은 사용 중인 데이터베이스 및 조인을 정의하는 방법에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="45130-140">The exact syntax depends on the database you are using and on how you have defined the join.</span></span>  
  
 <span data-ttu-id="45130-141">테이블 조인과 관련된 구문 옵션은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="45130-141">Syntax options for joining tables include:</span></span>  
  
-   <span data-ttu-id="45130-142">**FROM 절의 JOIN 한정자**.</span><span class="sxs-lookup"><span data-stu-id="45130-142">**JOIN qualifier for the FROM clause**.</span></span>   <span data-ttu-id="45130-143">키워드 INNER 및 OUTER가 조인 형식을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="45130-143">The keywords INNER and OUTER specify the join type.</span></span> <span data-ttu-id="45130-144">이 구문은 ANSI 92 SQL 표준입니다.</span><span class="sxs-lookup"><span data-stu-id="45130-144">This syntax is standard for ANSI 92 SQL.</span></span>  
  
     <span data-ttu-id="45130-145">예를 들어, 각 테이블의 `publishers` 열을 기반으로 하여 `pub_info` 테이블과 `pub_id` 테이블을 조인하는 경우 결과 SQL 문은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="45130-145">For example, if you join the `publishers` and `pub_info` tables based on the `pub_id` column in each table, the resulting SQL statement might look like this:</span></span>  
  
    ```  
    SELECT *  
    FROM publishers INNER JOIN pub_info ON  
       publishers.pub_id = pub_info.pub_id  
    ```  
  
     <span data-ttu-id="45130-146">외부 조인을 만드는 경우 INNER 대신에 LEFT OUTER 또는 RIGHT OUTER가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="45130-146">If you create an outer join, the words LEFT OUTER or RIGHT OUTER appear in place of the word INNER.</span></span>  
  
-   <span data-ttu-id="45130-147">**두 테이블의 열을 비교하는 WHERE 절**.</span><span class="sxs-lookup"><span data-stu-id="45130-147">**WHERE clause compares columns in both tables**.</span></span>   <span data-ttu-id="45130-148">데이터베이스에서 JOIN 구문이 지원되지 않거나 사용자가 JOIN 구문을 직접 입력한 경우 WHERE 절이 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="45130-148">A WHERE clause appears if the database does not support the JOIN syntax (or if you entered it yourself).</span></span> <span data-ttu-id="45130-149">WHERE 절에서 조인을 만들면 두 테이블 이름이 FROM 절에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="45130-149">If the join is created in the WHERE clause, both table names appear in the FROM clause.</span></span>  
  
     <span data-ttu-id="45130-150">예를 들어, 아래 문은 `publishers` 테이블과 `pub_info` 테이블을 조인합니다.</span><span class="sxs-lookup"><span data-stu-id="45130-150">For example, the following statement joins the `publishers` and `pub_info` tables.</span></span>  
  
    ```  
    SELECT *  
    FROM publishers, pub_info  
    WHERE publishers.pub_id = pub_info.pub_id  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="45130-151">참고 항목</span><span class="sxs-lookup"><span data-stu-id="45130-151">See Also</span></span>  
 <span data-ttu-id="45130-152">[Visual Database Tools를 &#40;조인을 사용 하 여 쿼리&#41;](query-with-joins-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="45130-152">[Query with Joins &#40;Visual Database Tools&#41;](query-with-joins-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="45130-153">조인 대화 상자&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="45130-153">Join Dialog Box &#40;Visual Database Tools&#41;</span></span>](join-dialog-box-visual-database-tools.md)  
  
  
