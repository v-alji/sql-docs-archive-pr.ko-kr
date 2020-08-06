---
title: 계획 지침 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- TEMPLATE plan guide
- SQL plan guides
- OPTIMIZE FOR query hint
- RECOMPILE query hint
- OBJECT plan guide
- plan guides [SQL Server], about plan guides
- OPTION clause
- plan guides [SQL Server]
- USE PLAN query hint
ms.assetid: bfc97632-c14c-4768-9dc5-a9c512f6b2bd
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: c97682163313a56acb8521174fa8d4012a69b529
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652783"
---
# <a name="plan-guides"></a><span data-ttu-id="96c6d-102">계획 지침</span><span class="sxs-lookup"><span data-stu-id="96c6d-102">Plan Guides</span></span>
  <span data-ttu-id="96c6d-103">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]에서 실제 쿼리의 텍스트를 직접 변경할 수 없거나 직접 변경하지 않으려는 경우 계획 지침에 따라 쿼리 성능을 최적화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="96c6d-103">Plan guides let you optimize the performance of queries when you cannot or do not want to directly change the text of the actual query in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="96c6d-104">계획 지침은 쿼리 힌트 또는 고정 쿼리 계획을 연결하여 쿼리 최적화에 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="96c6d-104">Plan guides influence the optimization of queries by attaching query hints or a fixed query plan to them.</span></span> <span data-ttu-id="96c6d-105">계획 안내는 타사 공급업체에서 제공된 데이터베이스 애플리케이션의 일부 쿼리 하위 집합이 올바른 성능을 내지 못하는 경우에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="96c6d-105">Plan guides can be useful when a small subset of queries in a database application provided by a third-party vendor are not performing as expected.</span></span> <span data-ttu-id="96c6d-106">계획 지침에서 최적화하려는 Transact-SQL 문을 지정하고 사용할 쿼리 힌트가 들어 있는 OPTION 절이나 쿼리를 최적화하는 데 사용할 특정 쿼리 계획을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="96c6d-106">In the plan guide, you specify the Transact-SQL statement that you want optimized and either an OPTION clause that contains the query hints you want to use or a specific query plan you want to use to optimize the query.</span></span> <span data-ttu-id="96c6d-107">쿼리가 실행하면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가 Transact-SQL 문을 계획 지침과 대응시키고 런타임에 쿼리에 OPTION 절을 추가하거나 지정된 쿼리 계획을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="96c6d-107">When the query executes, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] matches the Transact-SQL statement to the plan guide and attaches the OPTION clause to the query at run time or uses the specified query plan.</span></span>  
  
 <span data-ttu-id="96c6d-108">만들 수 있는 총 계획 지침 수는 사용 가능한 시스템 리소스에 의해서만 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="96c6d-108">The total number of plan guides you can create is limited only by available system resources.</span></span> <span data-ttu-id="96c6d-109">그러나 계획 지침은 성능 향상이나 안정화를 목적으로 하는 중요 업무용 쿼리로 제한되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="96c6d-109">Nevertheless, plan guides should be limited to mission-critical queries that are targeted for improved or stabilized performance.</span></span> <span data-ttu-id="96c6d-110">배포된 애플리케이션의 쿼리 로드 대부분에 영향을 주기 위해 계획 지침을 사용하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="96c6d-110">Plan guides should not be used to influence most of the query load of a deployed application.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="96c6d-111">계획 지침은 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 일부 버전에서 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="96c6d-111">Plan guides cannot be used in every edition of [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="96c6d-112">버전에서 지원 되는 기능 목록은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [SQL Server 2014 버전에서 지 원하는 기능](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="96c6d-112">For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span> <span data-ttu-id="96c6d-113">계획 지침은 모든 버전에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="96c6d-113">Plan guides are visible in any edition.</span></span> <span data-ttu-id="96c6d-114">계획 지침이 포함된 데이터베이스를 모든 버전에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="96c6d-114">You can also attach a database that contains plan guides to any edition.</span></span> <span data-ttu-id="96c6d-115">업그레이드된 버전의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에 데이터베이스를 복원하거나 첨부해도 계획 지침은 그대로 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="96c6d-115">Plan guides remain intact when you restore or attach a database to an upgraded version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="types-of-plan-guides"></a><span data-ttu-id="96c6d-116">계획 지침의 유형</span><span class="sxs-lookup"><span data-stu-id="96c6d-116">Types of Plan Guides</span></span>  
 <span data-ttu-id="96c6d-117">다음과 같은 계획 지침 유형을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="96c6d-117">The following types of plan guides can be created.</span></span>  
  
 <span data-ttu-id="96c6d-118">OBJECT 계획 지침</span><span class="sxs-lookup"><span data-stu-id="96c6d-118">OBJECT plan guide</span></span>  
 <span data-ttu-id="96c6d-119">OBJECT 계획 지침은 [!INCLUDE[tsql](../../includes/tsql-md.md)] 저장 프로시저, 사용자 정의 스칼라 함수, 다중 문 사용자 정의 테이블 반환 함수 및 DML 트리거의 컨텍스트에서 실행되는 쿼리와 일치합니다.</span><span class="sxs-lookup"><span data-stu-id="96c6d-119">An OBJECT plan guide matches queries that execute in the context of [!INCLUDE[tsql](../../includes/tsql-md.md)] stored procedures, scalar user-defined functions, multi-statement table-valued user-defined functions, and DML triggers.</span></span>  
  
 <span data-ttu-id="96c6d-120">`@Country`데이터베이스에 대해 배포되는 데이터베이스 애플리케이션에`region` _ [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 매개 변수를 가져오는 다음 저장 프로시저가 있다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="96c6d-120">Suppose the following stored procedure, which takes the `@Country`_`region` parameter, is in a database application that is deployed against the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database:</span></span>  
  
```  
CREATE PROCEDURE Sales.GetSalesOrderByCountry (@Country_region nvarchar(60))  
AS  
BEGIN  
    SELECT *  
    FROM Sales.SalesOrderHeader AS h, Sales.Customer AS c,   
        Sales.SalesTerritory AS t  
    WHERE h.CustomerID = c.CustomerID  
        AND c.TerritoryID = t.TerritoryID  
        AND CountryRegionCode = @Country_region  
END;  
```  
  
 <span data-ttu-id="96c6d-121">이 저장 프로시저가 `@Country`_`region = N'AU'` (오스트레일리아)에 맞게 컴파일되고 최적화되었다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="96c6d-121">Assume that this stored procedure has been compiled and optimized for `@Country`_`region = N'AU'` (Australia).</span></span> <span data-ttu-id="96c6d-122">그러나 오스트레일리아에서 발주되는 판매 주문이 비교적 적기 때문에 판매 주문이 더 많은 국가의 매개 변수 값을 사용하여 쿼리를 실행할 경우 성능이 저하됩니다.</span><span class="sxs-lookup"><span data-stu-id="96c6d-122">However, because there are relatively few sales orders that originate from Australia, performance decreases when the query executes using parameter values of countries with more sales orders.</span></span> <span data-ttu-id="96c6d-123">미국이 판매 주문을 가장 많이 내므로 `@Country`\_`region = N'US'` 매개 변수의 가능한 모든 값에 대해 `@Country`\_`region` 에 대해 생성된 쿼리 계획이 더 잘 수행될 가능성이 높습니다.</span><span class="sxs-lookup"><span data-stu-id="96c6d-123">Because the most sales orders originate in the United States, a query plan that is generated for `@Country`\_`region = N'US'` would likely perform better for all possible values of the `@Country`\_`region` parameter.</span></span>  
  
 <span data-ttu-id="96c6d-124">저장 프로시저를 수정하여 `OPTIMIZE FOR` 쿼리 힌트를 쿼리에 추가하면 이 문제를 해결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="96c6d-124">You could address this problem by modifying the stored procedure to add the `OPTIMIZE FOR` query hint to the query.</span></span> <span data-ttu-id="96c6d-125">그러나 저장 프로시저가 배포된 애플리케이션 안에 있기 때문에 애플리케이션 코드를 직접 수정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="96c6d-125">However, because the stored procedure is in a deployed application, you cannot directly modify the application code.</span></span> <span data-ttu-id="96c6d-126">대신 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 데이터베이스에서 다음 계획 지침을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="96c6d-126">Instead, you can create the following plan guide in the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database.</span></span>  
  
```  
sp_create_plan_guide   
@name = N'Guide1',  
@stmt = N'SELECT *FROM Sales.SalesOrderHeader AS h,  
        Sales.Customer AS c,  
        Sales.SalesTerritory AS t  
        WHERE h.CustomerID = c.CustomerID   
            AND c.TerritoryID = t.TerritoryID  
            AND CountryRegionCode = @Country_region',  
@type = N'OBJECT',  
@module_or_batch = N'Sales.GetSalesOrderByCountry',  
@params = NULL,  
@hints = N'OPTION (OPTIMIZE FOR (@Country_region = N''US''))';  
```  
  
 <span data-ttu-id="96c6d-127">`sp_create_plan_guide` 문에 지정되어 있는 쿼리가 실행되면 `OPTIMIZE FOR (@Country = N''US'')` 절을 포함하도록 최적화 이전에 쿼리가 수정됩니다.</span><span class="sxs-lookup"><span data-stu-id="96c6d-127">When the query specified in the `sp_create_plan_guide` statement executes, the query is modified before optimization to include the `OPTIMIZE FOR (@Country = N''US'')` clause.</span></span>  
  
 <span data-ttu-id="96c6d-128">SQL 계획 지침</span><span class="sxs-lookup"><span data-stu-id="96c6d-128">SQL plan guide</span></span>  
 <span data-ttu-id="96c6d-129">SQL 계획 지침은 데이터베이스 개체의 일부가 아닌 독립 실행형 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문과 일괄 처리의 컨텍스트에서 실행되는 쿼리와 일치합니다.</span><span class="sxs-lookup"><span data-stu-id="96c6d-129">An SQL plan guide matches queries that execute in the context of stand-alone [!INCLUDE[tsql](../../includes/tsql-md.md)] statements and batches that are not part of a database object.</span></span> <span data-ttu-id="96c6d-130">SQL 기반 계획 지침은 지정된 형식으로 매개 변수화되는 쿼리와 일치되도록 하는 데도 사용될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="96c6d-130">SQL-based plan guides can also be used to match queries that parameterize to a specified form.</span></span> <span data-ttu-id="96c6d-131">SQL 계획 지침은 독립 실행형 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문 및 일괄 처리에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="96c6d-131">SQL plan guides apply to stand-alone [!INCLUDE[tsql](../../includes/tsql-md.md)] statements and batches.</span></span> <span data-ttu-id="96c6d-132">이러한 문은 종종 애플리케이션에서 [sp_executesql](/sql/relational-databases/system-stored-procedures/sp-executesql-transact-sql) 시스템 저장 프로시저를 사용하여 제출됩니다.</span><span class="sxs-lookup"><span data-stu-id="96c6d-132">Frequently, these statements are submitted by an application by using the [sp_executesql](/sql/relational-databases/system-stored-procedures/sp-executesql-transact-sql) system stored procedure.</span></span> <span data-ttu-id="96c6d-133">예를 들어 다음 독립 실행형 일괄 처리를 생각해 보십시오.</span><span class="sxs-lookup"><span data-stu-id="96c6d-133">For example, consider the following stand-alone batch:</span></span>  
  
```  
SELECT TOP 1 * FROM Sales.SalesOrderHeader ORDER BY OrderDate DESC;  
```  
  
 <span data-ttu-id="96c6d-134">병렬 실행 계획이 이 쿼리에서 생성되지 않도록 하려면 다음 계획 지침을 만들고 `MAXDOP` 쿼리 힌트를 `1` 매개 변수의 `@hints` 로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="96c6d-134">To prevent a parallel execution plan from being generated on this query, create the following plan guide and set the `MAXDOP` query hint to `1` in the `@hints` parameter.</span></span>  
  
```  
sp_create_plan_guide   
@name = N'Guide2',   
@stmt = N'SELECT TOP 1 * FROM Sales.SalesOrderHeader ORDER BY OrderDate DESC',  
@type = N'SQL',  
@module_or_batch = NULL,   
@params = NULL,   
@hints = N'OPTION (MAXDOP 1)';  
```  
  
> [!IMPORTANT]  
>  <span data-ttu-id="96c6d-135">`@module_or_batch` 문의 `@params` 및 `sp_create_plan guide` 인수에 대해 제공되는 값은 실제 쿼리에서 전송되는 해당 텍스트와 일치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="96c6d-135">The values that are supplied for the `@module_or_batch` and `@params` arguments of the `sp_create_plan guide` statement must match the corresponding text submitted in the actual query.</span></span> <span data-ttu-id="96c6d-136">자세한 내용은 [sp_create_plan_guide&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) 문의 [SQL Server Profiler를 사용하여 계획 지침 작성 및 테스트](plan-guides.md)에서 실제 쿼리의 텍스트를 직접 변경할 수 없거나 직접 변경하지 않으려는 경우 계획 지침에 따라 쿼리 성능을 최적화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="96c6d-136">For more information, see [sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) and [Use SQL Server Profiler to Create and Test Plan Guides](plan-guides.md).</span></span>  
  
 <span data-ttu-id="96c6d-137">PARAMETERIZATION 데이터베이스 옵션을 FORCED로 설정했거나 쿼리 클래스를 매개 변수화하도록 지정하는 TEMPLATE 계획 지침을 만든 경우에 같은 형식으로 매개 변수화된 쿼리에 대해서도 SQL 계획 지침을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="96c6d-137">SQL plan guides can also be created on queries that parameterize to the same form when the PARAMETERIZATION database option is SET to FORCED, or when a TEMPLATE plan guide is created specifying that a parameterized class of queries.</span></span>  
  
 <span data-ttu-id="96c6d-138">TEMPLATE 계획 지침</span><span class="sxs-lookup"><span data-stu-id="96c6d-138">TEMPLATE plan guide</span></span>  
 <span data-ttu-id="96c6d-139">TEMPLATE 계획 지침은 지정된 형식으로 매개 변수화되는 독립 실행형 쿼리와 일치합니다.</span><span class="sxs-lookup"><span data-stu-id="96c6d-139">A TEMPLATE plan guide matches stand-alone queries that parameterize to a specified form.</span></span> <span data-ttu-id="96c6d-140">이 계획 지침은 쿼리 클래스에 대한 데이터베이스의 현재 PARAMETERIZATION 데이터베이스 SET 옵션을 대체하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="96c6d-140">These plan guides are used to override the current PARAMETERIZATION database SET option of a database for a class of queries.</span></span>  
  
 <span data-ttu-id="96c6d-141">다음과 같은 경우 TEMPLATE 계획 지침을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="96c6d-141">You can create a TEMPLATE plan guide in either of the following situations:</span></span>  
  
-   <span data-ttu-id="96c6d-142">PARAMETERIZATION 데이터베이스 옵션이 FORCED로 설정되었지만 단순 매개 변수화 규칙에 따라 컴파일하려는 쿼리가 있는 경우</span><span class="sxs-lookup"><span data-stu-id="96c6d-142">The PARAMETERIZATION database option is SET to FORCED, but there are queries you want compiled according to the rules of simple parameterization.</span></span>  
  
-   <span data-ttu-id="96c6d-143">PARAMETERIZATION 데이터베이스 옵션이 SIMPLE(기본 설정)로 설정되었지만 쿼리 클래스에 대해 강제 매개 변수화를 시도하려는 경우</span><span class="sxs-lookup"><span data-stu-id="96c6d-143">The PARAMETERIZATION database option is SET to SIMPLE (the default setting), but you want forced parameterization to be tried on a class of queries.</span></span>  
  
## <a name="plan-guide-matching-requirements"></a><span data-ttu-id="96c6d-144">계획 지침 일치 요구 사항</span><span class="sxs-lookup"><span data-stu-id="96c6d-144">Plan Guide Matching Requirements</span></span>  
 <span data-ttu-id="96c6d-145">계획 지침의 범위는 이 지침이 생성되는 데이터베이스입니다.</span><span class="sxs-lookup"><span data-stu-id="96c6d-145">Plan guides are scoped to the database in which they are created.</span></span> <span data-ttu-id="96c6d-146">따라서 쿼리를 실행할 때 현재 데이터베이스에 있는 계획 지침만 쿼리에 일치시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="96c6d-146">Therefore, only plan guides that are in the database that is current when a query executes can be matched to the query.</span></span> <span data-ttu-id="96c6d-147">예를 들어 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 가 현재 데이터베이스이면 다음 쿼리가 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="96c6d-147">For example, if [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] is the current database and the following query executes:</span></span>  
  
 `SELECT FirstName, LastName FROM Person.Person;`  
  
 <span data-ttu-id="96c6d-148">[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 데이터베이스의 계획 지침만 이 쿼리에 일치될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="96c6d-148">Only plan guides in the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database are eligible to be matched to this query.</span></span> <span data-ttu-id="96c6d-149">그러나 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 가 현재 데이터베이스이면 다음 문이 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="96c6d-149">However, if [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] is the current database and the following statements are run:</span></span>  
  
 `USE DB1;`  
  
 `SELECT FirstName, LastName FROM Person.Person;`  
  
 <span data-ttu-id="96c6d-150">쿼리가 `DB1` 컨텍스트에서 실행되므로 `DB1`의 계획 지침만 쿼리에 일치됩니다.</span><span class="sxs-lookup"><span data-stu-id="96c6d-150">Only plan guides in `DB1` are eligible to be matched to the query because the query is executing in the context of `DB1`.</span></span>  
  
 <span data-ttu-id="96c6d-151">SQL 또는 TEMPLATE 기반 계획 지침을 위해 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]는 두 값의 문자를 비교하여 @module_or_batch 및 @params 인수의 값을 일치시킵니다.</span><span class="sxs-lookup"><span data-stu-id="96c6d-151">For SQL- or TEMPLATE-based plan guides, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] matches the values for the @module_or_batch and @params arguments to a query by comparing the two values character by character.</span></span> <span data-ttu-id="96c6d-152">따라서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가 실제 일괄 처리에서 수신한 것과 똑같이 텍스트를 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="96c6d-152">This means you must provide the text exactly as [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] receives it in the actual batch.</span></span>  
  
 <span data-ttu-id="96c6d-153">@type이 'SQL'이고 @module_or_batch가 NULL로 설정된 경우 @module_or_batch 값은 @stmt 값으로 설정됩니다. 이는 *statement_text* 의 값이 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에 전송된 것과 문자 수준까지 같은 형식으로 제공되어야 함을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="96c6d-153">When @type = 'SQL' and @module_or_batch is set to NULL, the value of @module_or_batch is set to the value of @stmt. This means that the value for *statement_text* must be provided in the identical format, character-for-character, as it is submitted to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="96c6d-154">이 일치 작업을 더 효과적으로 처리하기 위해 내부 변환은 수행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="96c6d-154">No internal conversion is performed to facilitate this match.</span></span>  
  
 <span data-ttu-id="96c6d-155">일반(SQL 또는 OBJECT) 계획 지침 및 TEMPLATE 계획 지침 모두 문에 적용할 수 있을 경우 일반 계획 지침만 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="96c6d-155">When both a regular (SQL or OBJECT) plan guide and a TEMPLATE plan guide can apply to a statement, only the regular plan guide will be used.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="96c6d-156">계획 지침을 만들려는 문이 포함된 일괄 처리는 USE *database* 문을 포함할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="96c6d-156">The batch that contains the statement on which you want to create a plan guide cannot contain a USE *database* statement.</span></span>  
  
## <a name="plan-guide-effect-on-the-plan-cache"></a><span data-ttu-id="96c6d-157">계획 캐시의 계획 지침 효과</span><span class="sxs-lookup"><span data-stu-id="96c6d-157">Plan Guide Effect on the Plan Cache</span></span>  
 <span data-ttu-id="96c6d-158">모듈에 대한 계획 지침을 만들면 계획 캐시에서 해당 모듈에 대한 쿼리 계획이 제거되고,</span><span class="sxs-lookup"><span data-stu-id="96c6d-158">Creating a plan guide on a module removes the query plan for that module from the plan cache.</span></span> <span data-ttu-id="96c6d-159">일괄 처리에 OBJECT 또는 SQL 유형의 계획 지침을 만들면 같은 해시 값을 가진 일괄 처리에 대한 쿼리 계획이 제거되며,</span><span class="sxs-lookup"><span data-stu-id="96c6d-159">Creating a plan guide of type OBJECT or SQL on a batch removes the query plan for a batch that has the same hash value.</span></span> <span data-ttu-id="96c6d-160">TEMPLATE 유형의 계획 지침을 만들면 해당 데이터베이스 내의 계획 캐시에서 단일 문 일괄 처리가 모두 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="96c6d-160">Creating a plan guide of type TEMPLATE removes all single-statement batches from the plan cache within that database.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="96c6d-161">관련 작업</span><span class="sxs-lookup"><span data-stu-id="96c6d-161">Related Tasks</span></span>  
  
|<span data-ttu-id="96c6d-162">Task</span><span class="sxs-lookup"><span data-stu-id="96c6d-162">Task</span></span>|<span data-ttu-id="96c6d-163">항목</span><span class="sxs-lookup"><span data-stu-id="96c6d-163">Topic</span></span>|  
|----------|-----------|  
|<span data-ttu-id="96c6d-164">계획 지침을 만드는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="96c6d-164">Describes how to create a plan guide.</span></span>|[<span data-ttu-id="96c6d-165">새 계획 지침 만들기</span><span class="sxs-lookup"><span data-stu-id="96c6d-165">Create a New Plan Guide</span></span>](create-a-new-plan-guide.md)|  
|<span data-ttu-id="96c6d-166">매개 변수가 있는 쿼리에 대한 계획 지침을 만드는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="96c6d-166">Describes how to create a plan guide for parameterized queries.</span></span>|[<span data-ttu-id="96c6d-167">매개 변수가 있는 쿼리를 위한 계획 지침 만들기</span><span class="sxs-lookup"><span data-stu-id="96c6d-167">Create a Plan Guide for Parameterized Queries</span></span>](create-a-plan-guide-for-parameterized-queries.md)|  
|<span data-ttu-id="96c6d-168">계획 지침을 사용하여 쿼리 매개 변수화 동작을 제어하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="96c6d-168">Describes how to control query parameterization behavior by using plan guides.</span></span>|[<span data-ttu-id="96c6d-169">계획 지침을 사용하여 쿼리 매개 변수화 동작 지정</span><span class="sxs-lookup"><span data-stu-id="96c6d-169">Specify Query Parameterization Behavior by Using Plan Guides</span></span>](specify-query-parameterization-behavior-by-using-plan-guides.md)|  
|<span data-ttu-id="96c6d-170">계획 지침에 고정 쿼리를 포함하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="96c6d-170">Describes how to include a fixed query plan in a plan guide.</span></span>|[<span data-ttu-id="96c6d-171">계획 지침에 정해진 쿼리 계획 적용</span><span class="sxs-lookup"><span data-stu-id="96c6d-171">Apply a Fixed Query Plan to a Plan Guide</span></span>](apply-a-fixed-query-plan-to-a-plan-guide.md)|  
|<span data-ttu-id="96c6d-172">계획 지침에서 쿼리 힌트를 지정하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="96c6d-172">Describes how to specify query hints in a plan guide.</span></span>|[<span data-ttu-id="96c6d-173">계획 지침에 쿼리 힌트 연결</span><span class="sxs-lookup"><span data-stu-id="96c6d-173">Attach Query Hints to a Plan Guide</span></span>](attach-query-hints-to-a-plan-guide.md)|  
|<span data-ttu-id="96c6d-174">계획 지침 속성을 보는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="96c6d-174">Describes how to view plan guide properties.</span></span>|[<span data-ttu-id="96c6d-175">계획 지침 속성 보기</span><span class="sxs-lookup"><span data-stu-id="96c6d-175">View Plan Guide Properties</span></span>](view-plan-guide-properties.md)|  
|<span data-ttu-id="96c6d-176">SQL Server Profiler를 사용하여 계획 지침을 작성 및 테스트하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="96c6d-176">Describes how to use SQL Server Profiler to create and test plan guides.</span></span>|[<span data-ttu-id="96c6d-177">SQL Server Profiler를 사용하여 계획 지침 작성 및 테스트</span><span class="sxs-lookup"><span data-stu-id="96c6d-177">Use SQL Server Profiler to Create and Test Plan Guides</span></span>](plan-guides.md)|  
|<span data-ttu-id="96c6d-178">계획 지침의 유효성을 검사하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="96c6d-178">Describes how to validate plan guides.</span></span>|[<span data-ttu-id="96c6d-179">업그레이드 후 계획 지침의 유효성 검사</span><span class="sxs-lookup"><span data-stu-id="96c6d-179">Validate Plan Guides After Upgrade</span></span>](validate-plan-guides-after-upgrade.md)|  
  
## <a name="see-also"></a><span data-ttu-id="96c6d-180">참고 항목</span><span class="sxs-lookup"><span data-stu-id="96c6d-180">See Also</span></span>  
 <span data-ttu-id="96c6d-181">[sp_create_plan_guide&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="96c6d-181">[sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) </span></span>  
 <span data-ttu-id="96c6d-182">[sp_create_plan_guide_from_handle&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="96c6d-182">[sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql) </span></span>  
 <span data-ttu-id="96c6d-183">[sp_control_plan_guide&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-control-plan-guide-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="96c6d-183">[sp_control_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-control-plan-guide-transact-sql) </span></span>  
 <span data-ttu-id="96c6d-184">[sys.plan_guides&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-plan-guides-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="96c6d-184">[sys.plan_guides &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-plan-guides-transact-sql) </span></span>  
 [<span data-ttu-id="96c6d-185">sys.fn_validate_plan_guide&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="96c6d-185">sys.fn_validate_plan_guide &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-functions/sys-fn-validate-plan-guide-transact-sql)  
  
  
