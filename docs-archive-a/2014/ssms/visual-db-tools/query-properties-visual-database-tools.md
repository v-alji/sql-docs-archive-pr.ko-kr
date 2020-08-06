---
title: 쿼리 속성(Visual Database Tools) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdtsql.chm:69636
- vdt.ppg.querydesigner.query
ms.assetid: 07495669-6ed5-4004-904e-aae1230be5e4
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6e3c8adfb50e15113228afe8b48218f341f19084
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730000"
---
# <a name="query-properties-visual-database-tools"></a><span data-ttu-id="396ee-102">쿼리 속성(Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="396ee-102">Query Properties (Visual Database Tools)</span></span>
  <span data-ttu-id="396ee-103">쿼리 속성은 쿼리 및 뷰 디자이너에서 쿼리를 연 경우 속성 창에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="396ee-103">These properties appear in the Properties window when you have a query open in Query and View Designer.</span></span> <span data-ttu-id="396ee-104">별도로 언급하지 않는 한 속성 창에서 이러한 속성을 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="396ee-104">Unless otherwise noted, you can edit these properties in the Properties window.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="396ee-105">이 항목의 속성은 사전순이 아니라 범주별로 정렬됩니다.</span><span class="sxs-lookup"><span data-stu-id="396ee-105">The properties in this topic are ordered by category, rather than alphabetically.</span></span>  
  
## <a name="options"></a><span data-ttu-id="396ee-106">옵션</span><span class="sxs-lookup"><span data-stu-id="396ee-106">Options</span></span>  
 <span data-ttu-id="396ee-107">**ID 범주**</span><span class="sxs-lookup"><span data-stu-id="396ee-107">**Identity Category**</span></span>  
 <span data-ttu-id="396ee-108">확장하면 **이름** 속성이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="396ee-108">Expand to show the **Name** property.</span></span>  
  
 <span data-ttu-id="396ee-109">**이름**</span><span class="sxs-lookup"><span data-stu-id="396ee-109">**Name**</span></span>  
 <span data-ttu-id="396ee-110">현재 쿼리의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="396ee-110">Shows the name of the current query.</span></span> <span data-ttu-id="396ee-111">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]에서는 이를 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="396ee-111">Cannot be changed in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span>  
  
 <span data-ttu-id="396ee-112">**데이터베이스 이름**</span><span class="sxs-lookup"><span data-stu-id="396ee-112">**Database Name**</span></span>  
 <span data-ttu-id="396ee-113">선택한 테이블의 데이터 원본 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="396ee-113">Shows the name of the data source for the selected table.</span></span>  
  
 <span data-ttu-id="396ee-114">**서버 이름**</span><span class="sxs-lookup"><span data-stu-id="396ee-114">**Server Name**</span></span>  
 <span data-ttu-id="396ee-115">데이터 원본의 서버 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="396ee-115">Shows the name of the server for the data source.</span></span>  
  
 <span data-ttu-id="396ee-116">**쿼리 디자이너 범주**</span><span class="sxs-lookup"><span data-stu-id="396ee-116">**Query Designer Category**</span></span>  
 <span data-ttu-id="396ee-117">확장하면 나머지 속성이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="396ee-117">Expands to show the remaining properties.</span></span>  
  
 <span data-ttu-id="396ee-118">**대상 테이블**</span><span class="sxs-lookup"><span data-stu-id="396ee-118">**Destination table**</span></span>  
 <span data-ttu-id="396ee-119">데이터가 삽입되는 테이블의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="396ee-119">Specify the name of the table into which you are inserting data.</span></span> <span data-ttu-id="396ee-120">이 목록은 INSERT 쿼리 또는 MAKE TABLE 쿼리를 만드는 경우 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="396ee-120">This list appears if you are creating an INSERT query or MAKE TABLE query.</span></span> <span data-ttu-id="396ee-121">INSERT 쿼리를 작성하는 경우 이 목록에서 테이블 이름을 선택하십시오.</span><span class="sxs-lookup"><span data-stu-id="396ee-121">For an INSERT query, select a table name from the list.</span></span>  
  
 <span data-ttu-id="396ee-122">MAKE TABLE 쿼리를 작성하는 경우 새 테이블의 이름을 입력하십시오.</span><span class="sxs-lookup"><span data-stu-id="396ee-122">For a MAKE TABLE query, type the name of the new table.</span></span> <span data-ttu-id="396ee-123">다른 데이터 원본에 대상 테이블을 만들려면 대상 데이터 원본의 이름, 소유자(필요한 경우) 및 테이블의 이름을 포함하는 정규화된 테이블 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="396ee-123">To create a destination table in another data source, specify a fully qualified table name, including the name of the target data source, the owner (if required), and the name of the table.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="396ee-124">쿼리 디자이너는 이 이름이 이미 사용되고 있는지 또는 사용자에게 테이블을 만들 수 있는 권한이 있는지를 확인하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="396ee-124">Query Designer does not check whether the name is already in use or whether you have permission to create the table.</span></span>  
  
 <span data-ttu-id="396ee-125">**고유 값**</span><span class="sxs-lookup"><span data-stu-id="396ee-125">**Distinct values**</span></span>  
 <span data-ttu-id="396ee-126">결과 집합에서 중복 항목을 필터링하도록 쿼리를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="396ee-126">Specify that the query will filter out duplicates in the result set.</span></span> <span data-ttu-id="396ee-127">이 옵션은 하나 이상의 테이블에 있는 열 중 일부만 사용하고 이 열에 중복 값이 포함되어 있는 경우 또는 둘 이상의 테이블을 조인하는 과정에서 결과 집합에 중복 행이 만들어지는 경우에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="396ee-127">This option is useful when you are using only some of the columns from the table or tables and those columns might contain duplicate values, or when the process of joining two or more tables produces duplicate rows in the result set.</span></span> <span data-ttu-id="396ee-128">이 옵션을 선택하면 SQL 창에서 DISTINCT를 문에 삽입하는 것과 결과가 같습니다.</span><span class="sxs-lookup"><span data-stu-id="396ee-128">Choosing this option is equivalent to inserting the word DISTINCT into the statement in the SQL pane.</span></span>  
  
 <span data-ttu-id="396ee-129">**GROUP BY 확장**</span><span class="sxs-lookup"><span data-stu-id="396ee-129">**GROUP BY Extension**</span></span>  
 <span data-ttu-id="396ee-130">집계 쿼리를 기반으로 하는 쿼리에 대한 추가 옵션을 사용할 수 있음을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="396ee-130">Specify that additional options for queries based on aggregate queries are available.</span></span> <span data-ttu-id="396ee-131">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="396ee-131">(Applies only to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].)</span></span>  
  
 <span data-ttu-id="396ee-132">**모든 열 출력**</span><span class="sxs-lookup"><span data-stu-id="396ee-132">**Output All Columns**</span></span>  
 <span data-ttu-id="396ee-133">현재 쿼리에서 모든 테이블의 전체 열이 결과 집합에 포함되도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="396ee-133">Specify that all columns from all tables in the current query will be in the result set.</span></span> <span data-ttu-id="396ee-134">이 옵션을 선택하면 SQL 문에서 SELECT 키워드 다음에 개별 열 이름 대신 별표(\*)를 지정하는 것과 결과가 같습니다.</span><span class="sxs-lookup"><span data-stu-id="396ee-134">Choosing this option is equivalent to specifying an asterisk (\*) in place of individual column names after the SELECT keyword in the SQL statement.</span></span>  
  
 <span data-ttu-id="396ee-135">**쿼리 매개 변수 목록**</span><span class="sxs-lookup"><span data-stu-id="396ee-135">**Query Parameter List**</span></span>  
 <span data-ttu-id="396ee-136">쿼리 매개 변수를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="396ee-136">Shows query parameters.</span></span> <span data-ttu-id="396ee-137">이 매개 변수를 편집하려면 속성을 클릭한 다음, 속성의 오른쪽에 있는 줄임표 **(...)** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="396ee-137">To edit the parameters click the property and then click the ellipses **(...)** to the right of the property.</span></span> <span data-ttu-id="396ee-138">일반 OLE DB에만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="396ee-138">(Applies only to generic OLE DB.)</span></span>  
  
 <span data-ttu-id="396ee-139">**SQL 주석**</span><span class="sxs-lookup"><span data-stu-id="396ee-139">**SQL Comment**</span></span>  
 <span data-ttu-id="396ee-140">SQL 문에 대한 설명을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="396ee-140">Shows a description of the SQL statements.</span></span> <span data-ttu-id="396ee-141">전체 설명을 보거나 편집하려면 설명을 클릭한 다음, 속성의 오른쪽에 있는 줄임표 **(...)** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="396ee-141">To see the entire description or to edit it, click the description and then click the ellipses **(...)** to the right of the property.</span></span> <span data-ttu-id="396ee-142">쿼리의 사용자나 사용 시기 등과 같은 정보를 주석에 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="396ee-142">Your comments can include information such as who uses the query and when they use it.</span></span> <span data-ttu-id="396ee-143">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 7.0 이상 버전에만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="396ee-143">(Applies only to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 7.0 databases or later.)</span></span>  
  
 <span data-ttu-id="396ee-144">**Top 사양 범주**</span><span class="sxs-lookup"><span data-stu-id="396ee-144">**Top Specification Category**</span></span>  
 <span data-ttu-id="396ee-145">확장하면 **Top**, **Percent**, **식**및 **With Ties** 속성이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="396ee-145">Expand to show properties for the **Top**, **Percent**, **Expression**, and **With Ties** properties.</span></span>  
  
 <span data-ttu-id="396ee-146">**(Top)**</span><span class="sxs-lookup"><span data-stu-id="396ee-146">**(Top)**</span></span>  
 <span data-ttu-id="396ee-147">결과 집합에서 처음 *n* 개 행 또는 처음 *n* %에 해당하는 행만 반환하는 TOP 절이 쿼리에 포함되도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="396ee-147">Specify hat the query will include a TOP clause, which returns only the first *n* rows or first *n* percentage of rows in the result set.</span></span> <span data-ttu-id="396ee-148">기본값은 쿼리가 결과 집합에서 처음 10개 행을 반환하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="396ee-148">The default is that the query returns the first 10 rows in the result set.</span></span>  
  
 <span data-ttu-id="396ee-149">이 상자는 반환할 행 수를 변경하거나 백분율을 다르게 지정하려는 경우에 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="396ee-149">Use this box to change the number of rows to return or to specify a different percentage.</span></span> <span data-ttu-id="396ee-150">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="396ee-150">(Applies only to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] or later.)</span></span>  
  
 <span data-ttu-id="396ee-151">**식**</span><span class="sxs-lookup"><span data-stu-id="396ee-151">**Expression**</span></span>  
 <span data-ttu-id="396ee-152">쿼리에서 반환할 행의 수나 비율을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="396ee-152">Specify the number or percentage of rows that the query will return.</span></span> <span data-ttu-id="396ee-153">**Percent** 를 예로 설정한 경우 이 값은 쿼리에서 반환할 행의 비율을 나타내고, **Percent** 를 아니요로 설정한 경우 이 값은 반환할 행의 수를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="396ee-153">If you set **Percent** to Yes, this number is the percentage of rows the query will return; if you set **Percent** to No, it represents the number of rows to return.</span></span> <span data-ttu-id="396ee-154">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 7.0 이상 버전에만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="396ee-154">(Applies only to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] version 7.0 or later.)</span></span>  
  
 <span data-ttu-id="396ee-155">**백분율**</span><span class="sxs-lookup"><span data-stu-id="396ee-155">**Percent**</span></span>  
 <span data-ttu-id="396ee-156">결과 집합의 처음 *n* %에 해당하는 행만 쿼리가 반환하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="396ee-156">Specify that the query will return only the first *n* percent of rows in the result set.</span></span> <span data-ttu-id="396ee-157">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 7.0 이상 버전에만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="396ee-157">(Applies only to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] version 7.0 or later.)</span></span>  
  
 <span data-ttu-id="396ee-158">**With Ties**</span><span class="sxs-lookup"><span data-stu-id="396ee-158">**With Ties**</span></span>  
 <span data-ttu-id="396ee-159">뷰에 WITH TIES 절이 포함되도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="396ee-159">Specify that the view will include a WITH TIES clause.</span></span> <span data-ttu-id="396ee-160">WITH TIES는 백분율을 기반으로 하는 ORDER BY 절과 TOP 절이 뷰에 포함되어 있을 경우 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="396ee-160">WITH TIES is useful if a view includes an ORDER BY clause and a TOP clause based on percentage.</span></span> <span data-ttu-id="396ee-161">이 옵션을 설정하는 경우 백분율 값이 ORDER BY 절에서 동일한 값을 가진 행 집합의 중간까지만 포함하면 동일한 값을 가진 행을 모두 포함할 수 있도록 뷰가 확장됩니다.</span><span class="sxs-lookup"><span data-stu-id="396ee-161">If this option is set, and if the percentage cutoff falls in the middle of a set of rows with identical values in the ORDER BY clause, the view is extended to include all such rows.</span></span> <span data-ttu-id="396ee-162">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 7.0 이상 버전에만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="396ee-162">(Applies only to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] version 7.0 or later.)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="396ee-163">참고 항목</span><span class="sxs-lookup"><span data-stu-id="396ee-163">See Also</span></span>  
 <span data-ttu-id="396ee-164">[Visual Database Tools를 &#40;매개 변수를 사용 하 여 쿼리&#41;](visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="396ee-164">[Query with Parameters &#40;Visual Database Tools&#41;](visual-database-tools.md) </span></span>  
 [<span data-ttu-id="396ee-165">쿼리 및 뷰 디자인 방법 도움말 항목&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="396ee-165">Design Queries and Views How-to Topics &#40;Visual Database Tools&#41;</span></span>](design-queries-and-views-how-to-topics-visual-database-tools.md)  
  
  
