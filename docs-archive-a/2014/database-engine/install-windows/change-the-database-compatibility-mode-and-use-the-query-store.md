---
title: 쿼리 계획 마이그레이션 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- query plans [SQL Server], migrating
- upgrading SQL Server, migrating query plans
- plan guides [SQL Server], migrating query plans
ms.assetid: 7e02a137-6867-4f6a-a45a-2b02674f7e65
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: dafd3a5f8a460bb08e63919c2cb853ad74dc2f1f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734432"
---
# <a name="migrate-query-plans"></a><span data-ttu-id="6de52-102">쿼리 계획 마이그레이션</span><span class="sxs-lookup"><span data-stu-id="6de52-102">Migrate Query Plans</span></span>
  <span data-ttu-id="6de52-103">데이터베이스를 최신 버전의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]로 업그레이드하면 대부분의 경우 쿼리 성능이 향상됩니다.</span><span class="sxs-lookup"><span data-stu-id="6de52-103">In most cases, upgrading a database to the most recent version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will result in improved query performance.</span></span> <span data-ttu-id="6de52-104">그러나 성능 향상을 위해 세심하게 튜닝된 중요한 쿼리의 경우 업그레이드하기 전에 각 쿼리에 대한 계획 지침을 만들어 쿼리 계획을 보존할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6de52-104">However, if you have mission-critical queries that have been carefully tuned for performance, you may want to preserve the query plans for these queries before upgrading by creating a plan guide for each query.</span></span> <span data-ttu-id="6de52-105">업그레이드 후에 쿼리 최적화 프로그램에서 한 개 이상의 쿼리에 대해 효율성이 낮은 계획이 선택된 경우 계획 지침을 사용하여 쿼리 최적화 프로그램에서 업그레이드 전 계획이 사용되도록 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6de52-105">If, after upgrading, the query optimizer chooses a less efficient plan for one or more of the queries, you can enable the plan guides and force the query optimizer to use the pre-upgrade plans.</span></span>  
  
 <span data-ttu-id="6de52-106">업그레이드 전에 계획 지침을 만들려면 다음 단계를 수행하십시오.</span><span class="sxs-lookup"><span data-stu-id="6de52-106">To create plan guides before upgrading follow these steps:</span></span>  
  
1.  <span data-ttu-id="6de52-107">[Sp_create_plan_guide](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) 저장 프로시저를 사용 하 고 use plan 쿼리 힌트에 쿼리 계획을 지정 하 여 각 업무상 중요 한 쿼리에 대 한 현재 계획을 기록 합니다.</span><span class="sxs-lookup"><span data-stu-id="6de52-107">Record the current plan for each mission critical query by using the [sp_create_plan_guide](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) stored procedure and specifying the query plan in the USE PLAN query hint.</span></span>  
  
2.  <span data-ttu-id="6de52-108">계획 지침이 쿼리에 적용되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="6de52-108">Verify that the plan guide is applied to the query.</span></span>  
  
3.  <span data-ttu-id="6de52-109">데이터베이스를 최신 버전의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]로 업그레이드합니다.</span><span class="sxs-lookup"><span data-stu-id="6de52-109">Upgrade the database to the newer version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
     <span data-ttu-id="6de52-110">이러한 계획은 업그레이드된 계획 지침 데이터베이스에 보관되며 업그레이드 후 계획을 되돌려야 할 경우에 대체 계획으로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="6de52-110">The plans are persisted in the upgraded database in the plan guides and serve as a fallback in case of plan regressions after the upgrade.</span></span>  
  
     <span data-ttu-id="6de52-111">업그레이드 후에는 새로운 릴리스에서 제공되는 향상된 계획이나 업데이트된 통계에 따른 유용한 다시 컴파일을 활용할 수 있도록 계획 지침을 사용하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="6de52-111">We recommend that you not enable the plan guides after the upgrade because you might miss opportunities for better plans in the new release or beneficial recompiles due to updated statistics.</span></span>  
  
4.  <span data-ttu-id="6de52-112">업그레이드 후에 효율성이 떨어지는 계획이 선택되면 계획 지침을 일부 또는 모두 활성화하여 새 계획을 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="6de52-112">If less efficient plans are chosen after the upgrade, activate all or a subset of the plan guides to override the new plans.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6de52-113">예제</span><span class="sxs-lookup"><span data-stu-id="6de52-113">Example</span></span>  
 <span data-ttu-id="6de52-114">다음 예에서는 계획 지침을 만들어 쿼리에 대한 업그레이드 전 계획을 기록하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="6de52-114">The following example shows how to record a pre-upgrade plan for a query by creating a plan guide.</span></span>  
  
### <a name="step-1-collect-the-plan"></a><span data-ttu-id="6de52-115">1 단계: 계획 수집</span><span class="sxs-lookup"><span data-stu-id="6de52-115">Step 1: Collect the Plan</span></span>  
 <span data-ttu-id="6de52-116">계획 지침에 기록되는 쿼리 계획은 XML 형식이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6de52-116">The query plan recorded in the plan guide must be in XML format.</span></span> <span data-ttu-id="6de52-117">다음과 같은 방법으로 XML 형식의 쿼리 계획을 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6de52-117">XML-formatted query plans can be produced through the following ways:</span></span>  
  
-   [<span data-ttu-id="6de52-118">SET SHOWPLAN_XML</span><span class="sxs-lookup"><span data-stu-id="6de52-118">SET SHOWPLAN_XML</span></span>](/sql/t-sql/statements/set-showplan-xml-transact-sql)  
  
-   [<span data-ttu-id="6de52-119">SET STATISTICS XML</span><span class="sxs-lookup"><span data-stu-id="6de52-119">SET STATISTICS XML</span></span>](/sql/t-sql/statements/set-statistics-xml-transact-sql)  
  
-   <span data-ttu-id="6de52-120">[Dm_exec_query_plan](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-query-plan-transact-sql) 동적 관리 함수의 query_plan 열을 쿼리 하는 중입니다.</span><span class="sxs-lookup"><span data-stu-id="6de52-120">Querying the query_plan column of the [sys.dm_exec_query_plan](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-query-plan-transact-sql) dynamic management function.</span></span>  
  
-   <span data-ttu-id="6de52-121">실행 계획 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] [xml](../../relational-databases/event-classes/showplan-xml-event-class.md), 실행 [계획 xml 통계 프로필](../../relational-databases/event-classes/showplan-xml-statistics-profile-event-class.md)및 실행 [계획 xml For Query Compile](../../relational-databases/event-classes/showplan-xml-for-query-compile-event-class.md) 이벤트 클래스</span><span class="sxs-lookup"><span data-stu-id="6de52-121">The [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] [Showplan XML](../../relational-databases/event-classes/showplan-xml-event-class.md), [Showplan XML Statistics Profile](../../relational-databases/event-classes/showplan-xml-statistics-profile-event-class.md), and [Showplan XML For Query Compile](../../relational-databases/event-classes/showplan-xml-for-query-compile-event-class.md) event classes.</span></span>  
  
 <span data-ttu-id="6de52-122">다음 예에서는 동적 관리 뷰를 쿼리하여 `SELECT City, StateProvinceID, PostalCode FROM Person.Address ORDER BY PostalCode DESC;` 문에 대한 쿼리 계획을 수집합니다.</span><span class="sxs-lookup"><span data-stu-id="6de52-122">The following example collects the query plan for the statement `SELECT City, StateProvinceID, PostalCode FROM Person.Address ORDER BY PostalCode DESC;` by querying dynamic management views.</span></span>  
  
```  
USE AdventureWorks;  
GO  
SELECT query_plan  
    FROM sys.dm_exec_query_stats AS qs   
    CROSS APPLY sys.dm_exec_sql_text(qs.sql_handle) AS st  
    CROSS APPLY sys.dm_exec_text_query_plan(qs.plan_handle, DEFAULT, DEFAULT) AS qp  
    WHERE st.text LIKE N'SELECT City, StateProvinceID, PostalCode FROM Person.Address ORDER BY PostalCode DESC;%';  
GO  
```  
  
### <a name="step-2-create-the-plan-guide-to-force-the-plan"></a><span data-ttu-id="6de52-123">2 단계: 계획을 적용 하는 계획 지침 만들기</span><span class="sxs-lookup"><span data-stu-id="6de52-123">Step 2: Create the Plan Guide to Force the Plan</span></span>  
 <span data-ttu-id="6de52-124">앞에서 설명한 방법 중 하나로 만든 XML 형식의 쿼리 계획을 계획 지침에 사용하려면 sp_create_plan_guide의 OPTION 절에 지정된 USE PLAN 쿼리 힌트 안에 쿼리 계획을 문자열 리터럴로 복사하고 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="6de52-124">Using the XML-formatted query plan (obtained by any of the methods previously described) in the plan guide, copy and paste the query plan as a string literal inside the USE PLAN query hint specified in the OPTION clause of sp_create_plan_guide.</span></span>  
  
 <span data-ttu-id="6de52-125">계획 지침을 만들기 전에 XML 계획 내에 표시된 따옴표(')에 두 번째 따옴표를 추가하여 이스케이프 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="6de52-125">Within the XML plan itself, escape quotation marks (') that appear in the plan with a second quotation mark before creating the plan guide.</span></span> <span data-ttu-id="6de52-126">예를 들어 `WHERE A.varchar = 'This is a string'`이 포함된 계획에서 코드를 `WHERE A.varchar = ''This is a string''`으로 수정하여 이스케이프 처리해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6de52-126">For example, a plan that contains `WHERE A.varchar = 'This is a string'` must be escaped by modifying the code to `WHERE A.varchar = ''This is a string''`.</span></span>  
  
 <span data-ttu-id="6de52-127">다음 예에서는 1단계에서 수집된 쿼리 계획에 대한 계획 지침을 만들고 `@hints` 매개 변수에 쿼리에 대한 XML 실행 계획을 삽입합니다.</span><span class="sxs-lookup"><span data-stu-id="6de52-127">The following example creates a plan guide for the query plan collected in step 1 and inserts the XML Showplan for the query in the `@hints` parameter.</span></span> <span data-ttu-id="6de52-128">간단하게 나타내기 위해 이 예에는 실행 계획 중 일부만 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6de52-128">For brevity, only partial Showplan output is included in the example.</span></span>  
  
```  
EXECUTE sp_create_plan_guide   
@name = N'Guide1',  
@stmt = N'SELECT City, StateProvinceID, PostalCode FROM Person.Address ORDER BY PostalCode DESC;',  
@type = N'SQL',  
@module_or_batch = NULL,  
@params = NULL,  
@hints = N'OPTION(USE PLAN N''<ShowPlanXML xmlns=''''https://schemas.microsoft.com/sqlserver/2004/07/showplan''''   
    Version=''''0.5'''' Build=''''9.00.1116''''>  
    <BatchSequence><Batch><Statements><StmtSimple>  
    ...  
    </StmtSimple></Statements></Batch>  
    </BatchSequence></ShowPlanXML>'')';  
GO  
```  
  
### <a name="step-3-verify-that-the-plan-guide-is-applied-to-the-query"></a><span data-ttu-id="6de52-129">3 단계: 계획 지침이 쿼리에 적용 되는지 확인</span><span class="sxs-lookup"><span data-stu-id="6de52-129">Step 3: Verify That the Plan Guide Is Applied to the Query</span></span>  
 <span data-ttu-id="6de52-130">쿼리를 다시 실행하고 생성되는 쿼리 계획을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="6de52-130">Run the query again and examine the query plan that is produced.</span></span> <span data-ttu-id="6de52-131">생성된 계획이 계획 지침에 지정한 계획과 일치하는 것을 볼 수 있을 것입니다.</span><span class="sxs-lookup"><span data-stu-id="6de52-131">You should see that the plan matches the one that you specified in the plan guide.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6de52-132">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6de52-132">See Also</span></span>  
 <span data-ttu-id="6de52-133">[sp_create_plan_guide&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="6de52-133">[sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) </span></span>  
 <span data-ttu-id="6de52-134">[쿼리 힌트&#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-query) </span><span class="sxs-lookup"><span data-stu-id="6de52-134">[Query Hints &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-query) </span></span>  
 [<span data-ttu-id="6de52-135">계획 지침</span><span class="sxs-lookup"><span data-stu-id="6de52-135">Plan Guides</span></span>](../../relational-databases/performance/plan-guides.md)  
  
  
