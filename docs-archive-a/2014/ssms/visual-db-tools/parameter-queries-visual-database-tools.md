---
title: 매개 변수 쿼리(Visual Database Tools) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- parameter queries [SQL Server]
ms.assetid: 4897c41a-324a-47b8-a30b-cbc9e9e19a8b
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7f6fd94ef180a34ae91d52c213092898612dc77d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652491"
---
# <a name="parameter-queries-visual-database-tools"></a><span data-ttu-id="1f92e-102">매개 변수 쿼리(Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="1f92e-102">Parameter Queries (Visual Database Tools)</span></span>
  <span data-ttu-id="1f92e-103">경우에 따라 매번 다른 값으로 여러 번 사용할 수 있는 쿼리를 만들 필요가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f92e-103">In some cases you want to create a query that you can use many times, but with a different value each time.</span></span> <span data-ttu-id="1f92e-104">예를 들어, 한 명의 저자가 저술한 책의 `title_ids` 를 모두 찾기 위해 쿼리하는 경우가 종종 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f92e-104">For example, you might frequently run a query to find all the `title_ids` written by one author.</span></span> <span data-ttu-id="1f92e-105">각 요청에 대해 매번 저자의 ID 또는 이름만 다른 동일한 쿼리를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f92e-105">You could run the same query for each request, except that the author's ID or name would be different each time.</span></span>  
  
 <span data-ttu-id="1f92e-106">매번 다른 값을 가질 수 있는 쿼리를 만들려면 쿼리에 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="1f92e-106">To create a query that can have different values at different times, you use parameters in the query.</span></span> <span data-ttu-id="1f92e-107">매개 변수는 쿼리를 실행할 때 제공되는 값에 대한 자리 표시자입니다.</span><span class="sxs-lookup"><span data-stu-id="1f92e-107">A parameter is a placeholder for a value that is supplied when the query runs.</span></span> <span data-ttu-id="1f92e-108">매개 변수를 사용하는 SQL 문은 다음과 같습니다. 여기에서 "?"는 저자의 ID에 대한 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="1f92e-108">An SQL statement with a parameter might look like the following, where "?" represents the parameter for the author's ID:</span></span>  
  
```  
SELECT title_id  
FROM titleauthor  
WHERE (au_id = ?)  
```  
  
## <a name="where-you-can-use-parameters"></a><span data-ttu-id="1f92e-109">매개 변수를 사용할 수 있는 위치</span><span class="sxs-lookup"><span data-stu-id="1f92e-109">Where You Can Use Parameters</span></span>  
 <span data-ttu-id="1f92e-110">매개 변수를 리터럴 텍스트 값 또는 리터럴 숫자 값에 대한 자리 표시자로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f92e-110">You can use parameters as placeholders for literal values - for either text or numeric values.</span></span> <span data-ttu-id="1f92e-111">매개 변수는 일반적으로 SQL 문의 WHERE 절 또는 HAVING 절에 있는 개별 행이나 그룹에 대한 검색 조건에서 자리 표시자로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="1f92e-111">Most commonly, parameters are used as placeholders in search conditions for individual rows or for groups (that is, in the WHERE or HAVING clauses of an SQL statement).</span></span>  
  
 <span data-ttu-id="1f92e-112">매개 변수를 식의 자리 표시자로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f92e-112">You can use parameters as placeholders in expressions.</span></span> <span data-ttu-id="1f92e-113">예를 들어, 쿼리를 실행할 때마다 다른 할인 가격을 제공하여 할인된 가격을 계산할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f92e-113">For example, you might want to calculate discounted prices by supplying a different discount value each time you run a query.</span></span> <span data-ttu-id="1f92e-114">이렇게 하려면 다음과 같은 식을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1f92e-114">To do so, you could specify the following expression:</span></span>  
  
```  
(price * ?)  
```  
  
## <a name="specifying-unnamed-and-named-parameters"></a><span data-ttu-id="1f92e-115">명명되지 않은 매개 변수 및 명명된 매개 변수 지정</span><span class="sxs-lookup"><span data-stu-id="1f92e-115">Specifying Unnamed and Named Parameters</span></span>  
 <span data-ttu-id="1f92e-116">명명되지 않은 매개 변수와 명명된 매개 변수와 같이 두 가지 형식의 매개 변수를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f92e-116">You can specify two types of parameters: unnamed and named.</span></span> <span data-ttu-id="1f92e-117">명명되지 않은 매개 변수는 리터럴 값을 입력하거나 이를 대체할 쿼리의 임의 위치에 넣는 물음표(?)입니다.</span><span class="sxs-lookup"><span data-stu-id="1f92e-117">An unnamed parameter is a question mark (?) that you put anywhere in the query that you want to prompt for or substitute a literal value.</span></span> <span data-ttu-id="1f92e-118">예를 들어 `titleauthor` 테이블에서 저자의 ID를 검색하기 위해 명명되지 않은 매개 변수를 사용하는 경우 [SQL 창](visual-database-tools.md) 에 나타나는 결과 문은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="1f92e-118">For example, if you use an unnamed parameter to search for an author's id in the `titleauthor` table, the resulting statement in the [SQL Pane](visual-database-tools.md) might look like this:</span></span>  
  
```  
SELECT title_id  
FROM titleauthor  
WHERE (au_id = ?)  
```  
  
 <span data-ttu-id="1f92e-119">[쿼리 및 뷰 디자이너](query-and-view-designer-tools-visual-database-tools.md)에서 쿼리를 실행하면 [쿼리 매개 변수 대화 상자](query-parameters-dialog-box-visual-database-tools.md) 에 매개 변수 이름으로 "?"가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="1f92e-119">When you run the query in the [Query and View Designer](query-and-view-designer-tools-visual-database-tools.md), the [Query Parameters Dialog Box](query-parameters-dialog-box-visual-database-tools.md) appears with "?" as the name of the parameter.</span></span>  
  
 <span data-ttu-id="1f92e-120">또는 매개 변수에 이름을 할당할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f92e-120">Alternatively, you can assign a name to a parameter.</span></span> <span data-ttu-id="1f92e-121">명명된 매개 변수는 쿼리에 여러 개의 매개 변수가 있는 경우 특히 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="1f92e-121">Named parameters are particularly useful if you have multiple parameters in a query.</span></span> <span data-ttu-id="1f92e-122">예를 들어, 명명된 매개 변수를 사용하여 `authors` 테이블에서 저자의 이름과 성을 검색하는 경우 SQL 창에 나타나는 결과 문은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="1f92e-122">For example, if you use named parameters to search for an author's first and last names in the `authors` table, the resulting statement in the SQL pane might look like this:</span></span>  
  
```  
SELECT au_id  
FROM authors  
WHERE au_fname = %first name% AND  
      au_lname = %last name%  
```  
  
> [!TIP]  
>  <span data-ttu-id="1f92e-123">명명된 매개 변수 쿼리를 만들기 전에 접두사와 접미사를 정의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f92e-123">You must define prefix and suffix characters before creating a named parameter query.</span></span>  
  
 <span data-ttu-id="1f92e-124">쿼리 및 뷰 디자이너에서 쿼리를 실행하면 [쿼리 매개 변수 대화 상자](query-parameters-dialog-box-visual-database-tools.md) 에 명명된 매개 변수의 목록이 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="1f92e-124">When you run the query in the Query and View Designer, the [Query Parameters Dialog Box](query-parameters-dialog-box-visual-database-tools.md) appears with a list of named parameters.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f92e-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1f92e-125">See Also</span></span>  
 <span data-ttu-id="1f92e-126">[Visual Database Tools를 &#40;매개 변수를 사용 하 여 쿼리&#41;](query-with-parameters-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="1f92e-126">[Query with Parameters &#40;Visual Database Tools&#41;](query-with-parameters-visual-database-tools.md) </span></span>  
 <span data-ttu-id="1f92e-127">[Visual Database Tools를 &#40;지원 되는 쿼리 유형&#41;](supported-query-types-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="1f92e-127">[Supported Query Types &#40;Visual Database Tools&#41;](supported-query-types-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="1f92e-128">쿼리 및 뷰 디자인 방법 도움말 항목&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="1f92e-128">Design Queries and Views How-to Topics &#40;Visual Database Tools&#41;</span></span>](design-queries-and-views-how-to-topics-visual-database-tools.md)  
  
  
