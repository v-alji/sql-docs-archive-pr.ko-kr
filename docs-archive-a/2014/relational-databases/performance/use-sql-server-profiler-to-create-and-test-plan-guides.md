---
title: SQL Server Profiler를 사용하여 계획 지침 작성 및 테스트 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- checking plan guides
- plan guides [SQL Server], testing
- plan guides [SQL Server], SQL Server Profiler
- matching queries to plan guides [SQL Server]
- testing plan guides
- SQL Server Profiler, plan guides
- plan guides [SQL Server], creating
- capturing query text [SQL Server]
- verifying plan guides
- Profiler [SQL Server Profiler], plan guides
- query-to-plan guide matching [SQL Server]
ms.assetid: 7018dbf0-1a1a-411a-88af-327bedf9cfbd
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 543905343d74c9fbabe5f671d9021657ea5f76b5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732592"
---
# <a name="use-sql-server-profiler-to-create-and-test-plan-guides"></a><span data-ttu-id="ea2dc-102">SQL Server Profiler를 사용하여 계획 지침 작성 및 테스트</span><span class="sxs-lookup"><span data-stu-id="ea2dc-102">Use SQL Server Profiler to Create and Test Plan Guides</span></span>
  <span data-ttu-id="ea2dc-103">계획 지침을 만들 때는 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 를 사용하여 *sp_create_plan_guide* 저장 프로시저의 **statement_text** 인수에서 사용할 정확한 쿼리 텍스트를 캡처할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ea2dc-103">When you are creating a plan guide, you can use [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] to capture the exact query text for use in the *statement_text* argument of the **sp_create_plan_guide** stored procedure.</span></span> <span data-ttu-id="ea2dc-104">이렇게 하면 컴파일 시 계획 지침이 쿼리와 일치하도록 보장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ea2dc-104">This helps make sure that the plan guide will be matched to the query at compile time.</span></span> <span data-ttu-id="ea2dc-105">계획 지침을 만든 다음 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 를 사용하여 실제로 계획 지침이 쿼리와 일치하는지 여부를 테스트할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ea2dc-105">After the plan guide is created, [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] can also be used to test that the plan guide is, in fact, being matched to the query.</span></span> <span data-ttu-id="ea2dc-106">일반적으로 쿼리가 계획 지침과 일치하는지 확인하기 위해 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 를 사용하여 계획 지침을 테스트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea2dc-106">Generally, you should test plan guides by using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] to verify that your query is being matched to your plan guide.</span></span>  
  
## <a name="capturing-query-text-by-using-sql-server-profiler"></a><span data-ttu-id="ea2dc-107">SQL Server Profiler를 사용하여 쿼리 텍스트 캡처</span><span class="sxs-lookup"><span data-stu-id="ea2dc-107">Capturing Query Text by Using SQL Server Profiler</span></span>  
 <span data-ttu-id="ea2dc-108">쿼리를 실행하고 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 를 사용하여 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]에 전송된 대로 정확히 텍스트를 캡처하려는 경우 쿼리 텍스트와 정확히 일치하는 SQL 또는 TEMPLATE 유형의 계획 지침을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ea2dc-108">If you run a query and capture the text exactly as it was submitted to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], you can create a plan guide of type SQL or TEMPLATE that will match the query text exactly.</span></span> <span data-ttu-id="ea2dc-109">이렇게 하면 쿼리 최적화 프로그램에서 이 계획 지침이 사용되도록 보장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ea2dc-109">This makes sure that the plan guide is used by the query optimizer.</span></span>  
  
 <span data-ttu-id="ea2dc-110">애플리케이션에 의해 독립 실행형 일괄 처리로 전송되는 다음 쿼리를 고려하십시오.</span><span class="sxs-lookup"><span data-stu-id="ea2dc-110">Consider the following query that is submitted by an application as a stand-alone batch:</span></span>  
  
```  
SELECT COUNT(*) AS c  
FROM Sales.SalesOrderHeader AS h  
INNER JOIN Sales.SalesOrderDetail AS d  
  ON h.SalesOrderID = d.SalesOrderID  
WHERE h.OrderDate BETWEEN '20000101' and '20050101';  
```  
  
 <span data-ttu-id="ea2dc-111">병합 조인 연산을 사용하여 이 쿼리를 실행하려고 하지만 SHOWPLAN에 이 쿼리가 병합 조인을 사용하지 않는 것으로 표시된다고 가정해 보십시오.</span><span class="sxs-lookup"><span data-stu-id="ea2dc-111">Suppose you want this query to execute using a merge join operation, but SHOWPLAN indicates that the query is not using a merge join.</span></span> <span data-ttu-id="ea2dc-112">애플리케이션에서는 쿼리를 직접 변경할 수 없기 때문에 그 대신 컴파일 시 쿼리에 MERGE JOIN 쿼리 힌트를 첨부하도록 지정하는 계획 지침을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ea2dc-112">You cannot change the query directly in the application, so instead you create a plan guide to specify that the MERGE JOIN query hint be appended to the query at compile time.</span></span>  
  
 <span data-ttu-id="ea2dc-113">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 수신하는 것과 정확히 같은 쿼리 텍스트를 캡처하려면 다음 단계를 수행하십시오.</span><span class="sxs-lookup"><span data-stu-id="ea2dc-113">To capture the text of the query exactly as [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] receives it, follow these steps:</span></span>  
  
1.  <span data-ttu-id="ea2dc-114">[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 추적을 시작하고 **SQL:BatchStarting** 이벤트 유형을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ea2dc-114">Start a [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] trace, making sure that the **SQL:BatchStarting** event type is selected.</span></span>  
  
2.  <span data-ttu-id="ea2dc-115">애플리케이션이 쿼리를 실행하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea2dc-115">Have the application run the query.</span></span>  
  
3.  <span data-ttu-id="ea2dc-116">[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 추적을 일시 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="ea2dc-116">Pause the [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] Trace.</span></span>  
  
4.  <span data-ttu-id="ea2dc-117">이 쿼리에 해당하는 **SQL:BatchStarting** 이벤트를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ea2dc-117">Click the **SQL:BatchStarting** event that corresponds to the query.</span></span>  
  
5.  <span data-ttu-id="ea2dc-118">마우스 오른쪽 단추로 클릭하고 **이벤트 데이터 추출**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ea2dc-118">Right-click and select **Extract Event Data**.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="ea2dc-119">프로파일러 추적 창의 아래쪽 창에서 일괄 처리 텍스트를 선택하여 복사하려고 하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="ea2dc-119">Do not try to copy the batch text by selecting it from the lower pane of the Profiler trace window.</span></span> <span data-ttu-id="ea2dc-120">이렇게 하면 만든 계획 지침이 원본 일괄 처리와 일치하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ea2dc-120">This might cause the plan guide that you create to not match the original batch.</span></span>  
  
6.  <span data-ttu-id="ea2dc-121">이벤트 데이터를 파일에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="ea2dc-121">Save the event data to a file.</span></span> <span data-ttu-id="ea2dc-122">이 데이터는 일괄 처리 텍스트입니다.</span><span class="sxs-lookup"><span data-stu-id="ea2dc-122">This is the batch text.</span></span>  
  
7.  <span data-ttu-id="ea2dc-123">일괄 처리 텍스트 파일을 메모장에서 열고 텍스트를 복사 및 붙여 넣기 버퍼로 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="ea2dc-123">Open the batch text file in Notepad and copy the text to the copy and paste buffer.</span></span>  
  
8.  <span data-ttu-id="ea2dc-124">계획 지침을 만들고 복사한 텍스트를 **@stmt**인수에 대해 지정된 따옴표( **@stmt** ) 안에 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="ea2dc-124">Create the plan guide and paste the copied text inside the quotation marks (**''**) specified for the **@stmt** argument.</span></span> <span data-ttu-id="ea2dc-125">인수의 앞에 다른 작은따옴표를 사용 하 여 임의의 작은따옴표를 이스케이프 해야 합니다 **@stmt** .</span><span class="sxs-lookup"><span data-stu-id="ea2dc-125">You must escape any single quotation marks in the **@stmt** argument by preceding them with another single quotation mark.</span></span> <span data-ttu-id="ea2dc-126">작은따옴표를 삽입할 때는 다른 문자를 추가 또는 제거하지 않도록 주의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea2dc-126">Be careful not to add or remove any other characters when you insert these single quotation marks.</span></span> <span data-ttu-id="ea2dc-127">예를 들어 날짜 리터럴 **'** 20000101 **'** 은 **''** 20000101 **''** 로 구분해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea2dc-127">For example, the date literal **'** 20000101 **'** must be delimited as **''** 20000101 **''**.</span></span>  
  
 <span data-ttu-id="ea2dc-128">계획 지침은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="ea2dc-128">Here is the plan guide:</span></span>  
  
```  
EXEC sp_create_plan_guide   
    @name = N'MyGuide1',  
    @stmt = N'<paste the text copied from the batch text file here>',  
    @type = N'SQL',  
    @module_or_batch = NULL,  
    @params = NULL,  
    @hints = N'OPTION (MERGE JOIN)';  
```  
  
## <a name="testing-plan-guides-by-using-sql-server-profiler"></a><span data-ttu-id="ea2dc-129">SQL Server Profiler를 사용하여 계획 지침 테스트</span><span class="sxs-lookup"><span data-stu-id="ea2dc-129">Testing Plan Guides by Using SQL Server Profiler</span></span>  
 <span data-ttu-id="ea2dc-130">계획 지침이 쿼리와 일치하는지 확인하려면 다음 단계를 수행하십시오.</span><span class="sxs-lookup"><span data-stu-id="ea2dc-130">To verify that a plan guide is being matched to a query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="ea2dc-131">[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 추적을 시작하고 **성능** 노드 아래에 있는 **Showplan XML** 이벤트 유형을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ea2dc-131">Start a [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] trace, making certain that the **Showplan XML** event type is selected (located under the **Performance** node).</span></span>  
  
2.  <span data-ttu-id="ea2dc-132">애플리케이션이 쿼리를 실행하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea2dc-132">Have the application run the query.</span></span>  
  
3.  <span data-ttu-id="ea2dc-133">[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 추적을 일시 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="ea2dc-133">Pause the [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] Trace.</span></span>  
  
4.  <span data-ttu-id="ea2dc-134">해당 쿼리에 대한 **Showplan XML** 이벤트를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="ea2dc-134">Find the **Showplan XML** event for the affected query.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ea2dc-135">**Showplan XML for Query Compile** 이벤트를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ea2dc-135">The **Showplan XML for Query Compile** event cannot be used.</span></span> <span data-ttu-id="ea2dc-136">해당 이벤트에**PlanGuideDB** 가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ea2dc-136">**PlanGuideDB** does not exist in that event.</span></span>  
  
5.  <span data-ttu-id="ea2dc-137">계획 지침이 OBJECT 또는 SQL 유형인 경우 쿼리와 일치할 것으로 예상되는 계획 지침의 **PlanGuideDB** 및 **PlanGuideName** 특성이 **Showplan XML** 이벤트에 포함되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="ea2dc-137">If the plan guide is of type OBJECT or SQL, verify that the **Showplan XML** event contains the **PlanGuideDB** and **PlanGuideName** attributes for the plan guide that you expected to match the query.</span></span> <span data-ttu-id="ea2dc-138">또는 TEMPLATE 계획 지침의 경우 예상되는 계획 지침의 **TemplatePlanGuideDB** 및 **TemplatePlanGuideName** 특성이 **Showplan XML** 이벤트에 포함되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="ea2dc-138">Or, in the case of a TEMPLATE plan guide, verify that the **Showplan XML** event contains the **TemplatePlanGuideDB** and **TemplatePlanGuideName** attributes for the expected plan guide.</span></span> <span data-ttu-id="ea2dc-139">그러면 계획 지침이 작동하는지 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ea2dc-139">This verifies that the plan guide is working.</span></span> <span data-ttu-id="ea2dc-140">이러한 특성은 계획의 **\<StmtSimple>** 요소에 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="ea2dc-140">These attributes are contained under the **\<StmtSimple>** element of the plan.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea2dc-141">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ea2dc-141">See Also</span></span>  
 [<span data-ttu-id="ea2dc-142">sp_create_plan_guide&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="ea2dc-142">sp_create_plan_guide &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql)  
  
  
