---
title: 기본 MDX 쿼리 (MDX) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- queries [MDX], SELECT statement
- queries [MDX], about queries
- cellsets [MDX]
- SELECT statement [MDX]
- cubes [Analysis Services], SELECT statement
ms.assetid: 4fa5a95a-fec9-4584-875c-dbf030c53e82
author: minewiskan
ms.author: owend
ms.openlocfilehash: b6b1a70753abe8e477bd1e522a37f4513cc12a52
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653610"
---
# <a name="the-basic-mdx-query-mdx"></a><span data-ttu-id="488ec-102">기본 MDX 쿼리(MDX)</span><span class="sxs-lookup"><span data-stu-id="488ec-102">The Basic MDX Query (MDX)</span></span>
  <span data-ttu-id="488ec-103">기본 MDX (Multidimensional Expressions) 쿼리는 MDX에서 가장 자주 사용 되는 쿼리 SELECT 문입니다.</span><span class="sxs-lookup"><span data-stu-id="488ec-103">The basic Multidimensional Expressions (MDX) query is the SELECT statement-the most frequently used query in MDX.</span></span> <span data-ttu-id="488ec-104">MDX SELECT 문에서 결과 집합을 지정하는 방식, SELECT 문의 구문 정의 및 SELECT 문을 사용하여 간단한 쿼리를 만드는 방법을 이해하면 MDX를 사용하여 다차원 데이터를 쿼리하는 방법을 확실히 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="488ec-104">By understanding how an MDX SELECT statement must specify a result set, what the syntax of the SELECT statement is, and how to create a simple query using the SELECT statement, you will have a solid understanding of how to use MDX to query multidimensional data.</span></span>  
  
## <a name="specifying-a-result-set"></a><span data-ttu-id="488ec-105">결과 집합 지정</span><span class="sxs-lookup"><span data-stu-id="488ec-105">Specifying a Result Set</span></span>  
 <span data-ttu-id="488ec-106">MDX에서 SELECT 문은 큐브로부터 반환된 다차원 데이터의 하위 집합이 포함되는 결과 집합을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="488ec-106">In MDX, the SELECT statement specifies a result set that contains a subset of multidimensional data that has been returned from a cube.</span></span> <span data-ttu-id="488ec-107">결과 집합을 지정하려면 MDX 쿼리에 다음과 같은 정보가 포함되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="488ec-107">To specify a result set, an MDX query must contain the following information:</span></span>  
  
-   <span data-ttu-id="488ec-108">결과 집합에 포함할 축 수.</span><span class="sxs-lookup"><span data-stu-id="488ec-108">The number of axes that you want the result set to contain.</span></span> <span data-ttu-id="488ec-109">MDX 쿼리에서는 축을 128개까지 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="488ec-109">You can specify up to 128 axes in an MDX query.</span></span>  
  
-   <span data-ttu-id="488ec-110">MDX 쿼리의 각 축에 포함할 멤버나 튜플의 집합</span><span class="sxs-lookup"><span data-stu-id="488ec-110">The set of members or tuples to include on each axis of the MDX query.</span></span>  
  
-   <span data-ttu-id="488ec-111">MDX 쿼리의 컨텍스트를 설정하는 큐브 이름</span><span class="sxs-lookup"><span data-stu-id="488ec-111">The name of the cube that sets the context of the MDX query.</span></span>  
  
-   <span data-ttu-id="488ec-112">slicer 축에 포함할 멤버나 튜플의 집합.</span><span class="sxs-lookup"><span data-stu-id="488ec-112">The set of members or tuples to include on the slicer axis.</span></span> <span data-ttu-id="488ec-113">slicer 및 쿼리 축에 대한 자세한 내용은 [쿼리 및 Slicer 축으로 쿼리 제한&#40;MDX&#41;](mdx-query-and-slicer-axes-restricting-the-query.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="488ec-113">For more information about slicer and query axes, see[Restricting the Query with Query and Slicer Axes &#40;MDX&#41;](mdx-query-and-slicer-axes-restricting-the-query.md).</span></span>  
  
 <span data-ttu-id="488ec-114">쿼리 축, 쿼리될 큐브 및 slicer 축을 식별하기 위해 MDX SELECT 문은 다음 절을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="488ec-114">To identify the query axes, the cube that will be queried, and the slicer axis, the MDX SELECT statement uses the following clauses:</span></span>  
  
-   <span data-ttu-id="488ec-115">MDX SELECT 문의 쿼리 축을 결정하는 SELECT 절.</span><span class="sxs-lookup"><span data-stu-id="488ec-115">A SELECT clause that determines the query axes of an MDX SELECT statement.</span></span> <span data-ttu-id="488ec-116">SELECT 절의 쿼리 축 구성에 대한 자세한 내용은 [쿼리 축의 내용 지정&#40;MDX&#41;](mdx-query-and-slicer-axes-specify-the-contents-of-a-query-axis.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="488ec-116">For more information about the construction of query axes in a SELECT clause, see [Specifying the Contents of a Query Axis &#40;MDX&#41;](mdx-query-and-slicer-axes-specify-the-contents-of-a-query-axis.md).</span></span>  
  
-   <span data-ttu-id="488ec-117">쿼리될 큐브를 결정하는 FROM 절.</span><span class="sxs-lookup"><span data-stu-id="488ec-117">A FROM clause that determines which cube will be queried.</span></span> <span data-ttu-id="488ec-118">FROM 절에 대한 자세한 내용은 [SELECT 문&#40;MDX&#41;](/sql/mdx/mdx-data-manipulation-select)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="488ec-118">For more information about the FROM clause, see [SELECT Statement &#40;MDX&#41;](/sql/mdx/mdx-data-manipulation-select).</span></span>  
  
-   <span data-ttu-id="488ec-119">반환되는 데이터를 제한하기 위해 slicer 축에서 사용할 멤버나 튜플을 결정하는 선택적인 WHERE 절.</span><span class="sxs-lookup"><span data-stu-id="488ec-119">An optional WHERE clause that determines which members or tuples to use on the slicer axis to restrict the data returned.</span></span> <span data-ttu-id="488ec-120">WHERE 절의 slicer 축 구성에 대한 자세한 내용은 [Slicer 축의 내용 지정&#40;MDX&#41;](mdx-query-and-slicer-axes-specify-the-contents-of-a-slicer-axis.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="488ec-120">For more information about the construction of a slicer axis in a WHERE clause, see [Specifying the Contents of a Slicer Axis &#40;MDX&#41;](mdx-query-and-slicer-axes-specify-the-contents-of-a-slicer-axis.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="488ec-121">SELECT 문의 여러 절에 대한 자세한 내용은 [SELECT 문&#40;MDX&#41;](/sql/mdx/mdx-data-manipulation-select)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="488ec-121">For more detailed information about the various clauses of the SELECT statement, see [SELECT Statement &#40;MDX&#41;](/sql/mdx/mdx-data-manipulation-select).</span></span>  
  
## <a name="select-statement-syntax"></a><span data-ttu-id="488ec-122">SELECT 문 구문</span><span class="sxs-lookup"><span data-stu-id="488ec-122">SELECT Statement Syntax</span></span>  
 <span data-ttu-id="488ec-123">다음 구문은 SELECT, FROM 및 WHERE 절이 포함된 기본 SELECT 문을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="488ec-123">The following syntax shows a basic SELECT statement that includes the use of the SELECT, FROM, and WHERE clauses:</span></span>  
  
```  
[ WITH <SELECT WITH clause> [ , <SELECT WITH clause> ... ] ]   
SELECT [ * | ( <SELECT query axis clause>   
    [ , <SELECT query axis clause> ... ] ) ]  
FROM <SELECT subcube clause>   
[ <SELECT slicer axis clause> ]  
[ <SELECT cell property list clause> ]  
```  
  
 <span data-ttu-id="488ec-124">MDX SELECT 문은 WITH 키워드, 축 또는 slicer 축에 포함할 계산된 멤버를 만들기 위한 MDX 함수의 사용, 쿼리의 일부로 특정 셀 속성의 값을 반환하는 기능 등의 선택적 구문을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="488ec-124">The MDX SELECT statement supports optional syntax, such as the WITH keyword, the use of MDX functions to create calculated members for inclusion in an axis or slicer axis, and the ability to return the values of specific cell properties as part of the query.</span></span> <span data-ttu-id="488ec-125">MDX SELECT 문에 대한 자세한 내용은 [SELECT 문&#40;MDX&#41;](/sql/mdx/mdx-data-manipulation-select)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="488ec-125">For more information about the MDX SELECT statement, see [SELECT Statement &#40;MDX&#41;](/sql/mdx/mdx-data-manipulation-select).</span></span>  
  
### <a name="comparing-the-syntax-of-the-mdx-select-statement-to-sql"></a><span data-ttu-id="488ec-126">MDX SELECT 문의 구문과 SQL 구문 비교</span><span class="sxs-lookup"><span data-stu-id="488ec-126">Comparing the Syntax of the MDX SELECT Statement to SQL</span></span>  
 <span data-ttu-id="488ec-127">MDX SELECT 문의 구문 형식은 SQL 구문과 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="488ec-127">The syntax format for the MDX SELECT statement is similar to that of SQL syntax.</span></span> <span data-ttu-id="488ec-128">하지만 다음과 같은 점에서 근본적인 차이가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="488ec-128">However, there are several fundamental differences:</span></span>  
  
-   <span data-ttu-id="488ec-129">MDX 구문은 튜플이 나 멤버를 중괄호 ({및} 문자)로 묶어 집합을 구분 합니다. 멤버, 튜플 및 집합 구문에 대 한 자세한 내용은 [MDX&#41;&#40;멤버, 튜플 ](working-with-members-tuples-and-sets-mdx.md)및 집합 작업을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="488ec-129">MDX syntax distinguishes sets by surrounding tuples or members with braces (the { and } characters.) For more information about member, tuple, and set syntax, see [Working with Members, Tuples, and Sets &#40;MDX&#41;](working-with-members-tuples-and-sets-mdx.md).</span></span>  
  
-   <span data-ttu-id="488ec-130">MDX 쿼리는 SELECT 문에서 쿼리 축을 0개, 1개, 2개 또는 128개까지 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="488ec-130">MDX queries can have 0, 1, 2 or up to 128 query axes in the SELECT statement.</span></span> <span data-ttu-id="488ec-131">쿼리의 행과 열이 동작하는 방식이 크게 차이가 나는 SQL과 달리, 각 축은 똑같은 방식으로 동작합니다.</span><span class="sxs-lookup"><span data-stu-id="488ec-131">Each axis behaves in exactly the same way, unlike SQL where there are significant differences between how the rows and the columns of a query behave.</span></span>  
  
-   <span data-ttu-id="488ec-132">SQL 쿼리의 경우와 마찬가지로, FROM 절은 MDX 쿼리에 대한 데이터 원본 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="488ec-132">As with an SQL query, the FROM clause names the source of the data for the MDX query.</span></span> <span data-ttu-id="488ec-133">하지만 MDX FROM 절은 단일 큐브로 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="488ec-133">However, the MDX FROM clause is restricted to a single cube.</span></span> <span data-ttu-id="488ec-134">LookupCube 함수를 사용하여 값 단위로 다른 큐브 정보를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="488ec-134">Information from other cubes can be retrieved on a value-by-value basis by using the LookupCube function.</span></span>  
  
-   <span data-ttu-id="488ec-135">WHERE 절은 MDX 쿼리에서 slicer 축을 기술합니다.</span><span class="sxs-lookup"><span data-stu-id="488ec-135">The WHERE clause describes the slicer axis in an MDX query.</span></span> <span data-ttu-id="488ec-136">쿼리의 행 축에 나타나는 항목에 직접적으로 영향을 미치지 않는 SQL WHERE 절과 달리, 이 WHERE 절은 표시되지 않는 쿼리의 추가 축처럼 동작하여 결과 집합의 셀에 나타나는 값을 조각화합니다.</span><span class="sxs-lookup"><span data-stu-id="488ec-136">It acts as something like an invisible, extra axis in the query, slicing the values that appear in the cells in the result set; unlike the SQL WHERE clause it does not directly affect what appears on the rows axis of the query.</span></span> <span data-ttu-id="488ec-137">SQL WHERE 절의 기능은 FILTER 함수 등의 다른 MDX 함수를 통해 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="488ec-137">The functionality of the SQL WHERE clause is available through other MDX functions such as the FILTER function.</span></span>  
  
## <a name="select-statement-example"></a><span data-ttu-id="488ec-138">SELECT 문 예</span><span class="sxs-lookup"><span data-stu-id="488ec-138">SELECT Statement Example</span></span>  
 <span data-ttu-id="488ec-139">다음 예는 SELECT 문을 사용하는 기본 MDX 쿼리를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="488ec-139">The following example shows a basic MDX query that uses the SELECT statement.</span></span> <span data-ttu-id="488ec-140">이 쿼리는 Southwest 판매 지역의 2002년 및 2003년 판매액과 세금액이 포함된 결과 집합을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="488ec-140">This query returns a result set that contains the 2002 and 2003 sales and tax amounts for the Southwest sales territories.</span></span>  
  
```  
SELECT  
    { [Measures].[Sales Amount],   
        [Measures].[Tax Amount] } ON COLUMNS,  
    { [Date].[Fiscal].[Fiscal Year].&[2002],   
        [Date].[Fiscal].[Fiscal Year].&[2003] } ON ROWS  
FROM [Adventure Works]  
WHERE ( [Sales Territory].[Southwest] )  
```  
  
 <span data-ttu-id="488ec-141">이 예에서 쿼리는 다음과 같은 결과 집합 정보를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="488ec-141">In this example, the query defines the following result set information:</span></span>  
  
-   <span data-ttu-id="488ec-142">SELECT 절은 Measuers 차원의 Sales Amount 및 Tax Amount 멤버 및 Date 차원의 2002 및 2003 멤버로 쿼리 축을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="488ec-142">The SELECT clause sets the query axes as the Sales Amount and Tax Amount members of the Measures dimension, and the 2002 and 2003 members of the Date dimension.</span></span>  
  
-   <span data-ttu-id="488ec-143">FROM 절은 데이터 원본이 Adventure Works 큐브임을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="488ec-143">The FROM clause indicates that the data source is the Adventure Works cube.</span></span>  
  
-   <span data-ttu-id="488ec-144">WHERE 절은 Sales Territory 차원의 Southwest 멤버로 slicer 축을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="488ec-144">The WHERE clause defines the slicer axis as the Southwest member of the Sales Territory dimension.</span></span>  
  
 <span data-ttu-id="488ec-145">또한 쿼리 예에서는 COLUMNS 및 ROWS 축 별칭이 사용되었습니다.</span><span class="sxs-lookup"><span data-stu-id="488ec-145">Notice that the query example also uses the COLUMNS and ROWS axis aliases.</span></span> <span data-ttu-id="488ec-146">이러한 축의 순서 위치가 사용될 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="488ec-146">The ordinal positions for these axes could also have been used.</span></span> <span data-ttu-id="488ec-147">다음 예에서는 각 축의 순서 위치를 사용하도록 작성된 MDX 쿼리를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="488ec-147">The following example shows how the MDX query could have been written to use the ordinal position of each axis:</span></span>  
  
```  
SELECT  
    { [Measures].[Sales Amount],   
        [Measures].[Tax Amount] } ON 0,  
    { [Date].[Fiscal].[Fiscal Year].&[2002],   
        [Date].[Fiscal].[Fiscal Year].&[2003] } ON 1  
FROM [Adventure Works]  
WHERE ( [Sales Territory].[Southwest] )  
```  
  
 <span data-ttu-id="488ec-148">자세한 예는 [쿼리 축의 내용 지정&#40;MDX&#41;](mdx-query-and-slicer-axes-specify-the-contents-of-a-query-axis.md) 및 [Slicer 축의 내용 지정&#40;MDX&#41;](mdx-query-and-slicer-axes-specify-the-contents-of-a-slicer-axis.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="488ec-148">For more detailed examples, see [Specifying the Contents of a Query Axis &#40;MDX&#41;](mdx-query-and-slicer-axes-specify-the-contents-of-a-query-axis.md)and [Specifying the Contents of a Slicer Axis &#40;MDX&#41;](mdx-query-and-slicer-axes-specify-the-contents-of-a-slicer-axis.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="488ec-149">참고 항목</span><span class="sxs-lookup"><span data-stu-id="488ec-149">See Also</span></span>  
 <span data-ttu-id="488ec-150">[MDX의 주요 개념 &#40;Analysis Services&#41;](../key-concepts-in-mdx-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="488ec-150">[Key Concepts in MDX &#40;Analysis Services&#41;](../key-concepts-in-mdx-analysis-services.md) </span></span>  
 [<span data-ttu-id="488ec-151">SELECT 문&#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="488ec-151">SELECT Statement &#40;MDX&#41;</span></span>](/sql/mdx/mdx-data-manipulation-select)  
  
  
