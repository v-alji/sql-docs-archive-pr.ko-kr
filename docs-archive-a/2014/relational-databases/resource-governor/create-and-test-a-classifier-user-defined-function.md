---
title: 분류자 사용자 정의 함수 만들기 및 테스트 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Resource Governor, classifier function create
- classifier function [SQL Server], test
- classifier function [SQL Server], create
- Resource Governor, classifier function test
ms.assetid: 7866b3c9-385b-40c6-aca5-32d3337032be
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 1b8e5371762e38cf2b3ac8c1d506b467dcfa7e3c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731484"
---
# <a name="create-and-test-a-classifier-user-defined-function"></a><span data-ttu-id="c9fff-102">분류자 사용자 정의 함수 만들기 및 테스트</span><span class="sxs-lookup"><span data-stu-id="c9fff-102">Create and Test a Classifier User-Defined Function</span></span>
  <span data-ttu-id="c9fff-103">이 항목에서는 분류자 사용자 정의 함수(Transact-UDF)를 만들고 테스트하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c9fff-103">This topic shows how to create and test a classifier user-defined function (UDF).</span></span> <span data-ttu-id="c9fff-104">이 단계에는 [!INCLUDE[tsql](../../includes/tsql-md.md)] 쿼리 편집기에서 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 문을 실행하는 작업이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c9fff-104">The steps involve executing [!INCLUDE[tsql](../../includes/tsql-md.md)] statements in the [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Query Editor.</span></span>  
  
 <span data-ttu-id="c9fff-105">아래 절차에 나오는 예에서는 매우 복잡한 분류자 사용자 정의 함수를 만드는 경우에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="c9fff-105">The example shown in the following procedure illustrates the possibilities for creating a fairly complex classifier user-defined function.</span></span>  
  
 <span data-ttu-id="c9fff-106">이 예제에서는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="c9fff-106">In our example:</span></span>  
  
-   <span data-ttu-id="c9fff-107">지정한 시간 범위 동안의 프로덕션 처리를 위해 리소스 풀(pProductionProcessing) 및 작업 그룹(gProductionProcessing)을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c9fff-107">A resource pool (pProductionProcessing) and workload group (gProductionProcessing) are created for production processing during a specified time range.</span></span>  
  
-   <span data-ttu-id="c9fff-108">프로덕션 처리에 대한 요구 사항에 맞지 않는 연결 처리를 위해 리소스 풀(pOffHoursProcessing) 및 작업 그룹(gOffHoursProcessing)을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c9fff-108">A resource pool (pOffHoursProcessing) and workload group (gOffHoursProcessing) are created for handling connections that do not meet the requirements for production processing.</span></span>  
  
-   <span data-ttu-id="c9fff-109">로그인 시간에 대해 계산할 수 있는 시작 시간과 종료 시간을 보유하기 위해 마스터에 테이블(TblClassificationTimeTable)을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c9fff-109">A table (TblClassificationTimeTable) is created in master to hold start and end times that can be evaluated against a login time.</span></span> <span data-ttu-id="c9fff-110">리소스 관리자가 분류자 함수에 대한 스키마 바인딩을 사용하기 때문에 마스터에 이 테이블을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9fff-110">This must be created in master because Resource Governor uses schema binding for classifier functions.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c9fff-111">가능하면 자주 업데이트하는 큰 테이블은 마스터에 저장하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="c9fff-111">As a best practice, you should not store large, frequently updated tables in master.</span></span>  
  
 <span data-ttu-id="c9fff-112">분류자 함수는 로그인 시간을 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="c9fff-112">The classifier function extends the login time.</span></span> <span data-ttu-id="c9fff-113">과도하게 복잡한 함수를 사용하면 로그인을 수행할 때 시간이 초과되거나 빠른 연결 속도를 늦출 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c9fff-113">An overly complex function can cause logins to time out or slow down fast connections.</span></span>  
  
### <a name="to-create-the-classifier-user-defined-function"></a><span data-ttu-id="c9fff-114">분류자 사용자 정의 함수를 만들려면</span><span class="sxs-lookup"><span data-stu-id="c9fff-114">To create the classifier user-defined function</span></span>  
  
1.  <span data-ttu-id="c9fff-115">새 리소스 풀 및 작업 그룹을 만들고 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="c9fff-115">Create and configure the new resource pools and workload groups.</span></span> <span data-ttu-id="c9fff-116">각 작업 그룹을 적합한 리소스 풀에 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="c9fff-116">Assign each workload group to the appropriate resource pool.</span></span>  
  
    ```  
    --- Create a resource pool for production processing  
    --- and set limits.  
    USE master  
    GO  
    CREATE RESOURCE POOL pProductionProcessing  
    WITH  
    (  
         MAX_CPU_PERCENT = 100,  
         MIN_CPU_PERCENT = 50  
    )  
    GO  
    --- Create a workload group for production processing  
    --- and configure the relative importance.  
    CREATE WORKLOAD GROUP gProductionProcessing  
    WITH  
    (  
         IMPORTANCE = MEDIUM  
    )  
    --- Assign the workload group to the production processing  
    --- resource pool.  
    USING pProductionProcessing  
    GO  
    --- Create a resource pool for off-hours processing  
    --- and set limits.  
  
    CREATE RESOURCE POOL pOffHoursProcessing  
    WITH  
    (  
         MAX_CPU_PERCENT = 50,  
         MIN_CPU_PERCENT = 0  
    )  
    GO  
    --- Create a workload group for off-hours processing  
    --- and configure the relative importance.  
    CREATE WORKLOAD GROUP gOffHoursProcessing  
    WITH  
    (  
         IMPORTANCE = LOW  
    )  
    --- Assign the workload group to the off-hours processing  
    --- resource pool.  
    USING pOffHoursProcessing  
    GO  
    ```  
  
2.  <span data-ttu-id="c9fff-117">메모리 내 구성을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="c9fff-117">Update the in-memory configuration.</span></span>  
  
    ```  
    ALTER RESOURCE GOVERNOR RECONFIGURE  
    GO  
    ```  
  
3.  <span data-ttu-id="c9fff-118">테이블을 만들고 프로덕션 처리 시간 범위의 시작 시간과 종료 시간을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="c9fff-118">Create a table and define the start and end times for the production processing time range.</span></span>  
  
    ```  
    USE master  
    GO  
    CREATE TABLE tblClassificationTimeTable  
    (  
         strGroupName     sysname          not null,  
         tStartTime       time              not null,  
         tEndTime         time              not null  
    )  
    GO  
    --- Add time values that the classifier will use to  
    --- determine the workload group for a session.  
    INSERT into tblClassificationTimeTable VALUES('gProductionProcessing', '6:35 AM', '6:15 PM')  
    go  
    ```  
  
4.  <span data-ttu-id="c9fff-119">조회 테이블의 시간에 대해 계산될 수 있는 시간 함수 및 값을 사용하는 분류자 함수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c9fff-119">Create the classifier function that uses time functions and values that can be evaluated against the times in the lookup table.</span></span> <span data-ttu-id="c9fff-120">분류자 함수에서 조회 테이블을 사용하는 방법에 대한 자세한 내용은 이 항목의 "분류자 함수에서 조회 테이블을 사용하는 최선의 구현 방법"을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c9fff-120">For information about using Lookup Tables in a classifier function, see "Best practices for using Lookup Tables in a classifier function" in this topic.</span></span>  
  
    > [!NOTE]  
    >  [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] <span data-ttu-id="c9fff-121">에는 날짜 및 시간 데이터 형식 및 함수의 확장된 집합이 도입되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c9fff-121">introduced an expanded set of date and time data types and functions.</span></span> <span data-ttu-id="c9fff-122">자세한 내용은 [날짜 및 시간 데이터 형식 및 함수&#40;Transact-SQL&#41;](/sql/t-sql/functions/date-and-time-data-types-and-functions-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c9fff-122">For more information, see [Date and Time Data Types and Functions &#40;Transact-SQL&#41;](/sql/t-sql/functions/date-and-time-data-types-and-functions-transact-sql).</span></span>  
  
    ```  
    CREATE FUNCTION fnTimeClassifier()  
    RETURNS sysname  
    WITH SCHEMABINDING  
    AS  
    BEGIN  
         DECLARE @strGroup sysname  
         DECLARE @loginTime time  
         SET @loginTime = CONVERT(time,GETDATE())  
         SELECT TOP 1 @strGroup = strGroupName  
              FROM dbo.tblClassificationTimeTable  
              WHERE tStartTime <= @loginTime and tEndTime >= @loginTime  
         IF(@strGroup is not null)  
         BEGIN  
              RETURN @strGroup  
         END  
    --- Use the default workload group if there is no match  
    --- on the lookup.  
         RETURN N'gOffHoursProcessing'  
    END  
    GO  
    ```  
  
5.  <span data-ttu-id="c9fff-123">분류자 함수를 등록하고 메모리 내 구성을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="c9fff-123">Register the classifier function and update the in-memory configuration.</span></span>  
  
    ```  
    ALTER RESOURCE GOVERNOR with (CLASSIFIER_FUNCTION = dbo.fnTimeClassifier)  
    ALTER RESOURCE GOVERNOR RECONFIGURE  
    GO  
    ```  
  
### <a name="to-verify-the-resource-pools-workload-groups-and-the-classifier-user-defined-function"></a><span data-ttu-id="c9fff-124">리소스 풀, 작업 그룹 및 분류자 사용자 정의 함수를 확인하려면</span><span class="sxs-lookup"><span data-stu-id="c9fff-124">To verify the resource pools, workload groups, and the classifier user-defined function</span></span>  
  
1.  <span data-ttu-id="c9fff-125">다음 쿼리를 사용하여 리소스 풀 및 작업 그룹 구성을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="c9fff-125">Obtain the resource pool and workload group configuration by using the following query.</span></span>  
  
    ```  
    USE master  
    SELECT * FROM sys.resource_governor_resource_pools  
    SELECT * FROM sys.resource_governor_workload_groups  
    GO  
    ```  
  
2.  <span data-ttu-id="c9fff-126">다음 쿼리를 사용하여 분류자 함수가 존재하며 설정되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="c9fff-126">Verify that the classifier function exists and is enabled by using the following queries.</span></span>  
  
    ```  
    --- Get the classifier function Id and state (enabled).  
    SELECT * FROM sys.resource_governor_configuration  
    GO  
    --- Get the classifer function name and the name of the schema  
    --- that it is bound to.  
    SELECT   
          object_schema_name(classifier_function_id) AS [schema_name],  
          object_name(classifier_function_id) AS [function_name]  
    FROM sys.dm_resource_governor_configuration  
  
    ```  
  
3.  <span data-ttu-id="c9fff-127">다음 쿼리를 사용하여 리소스 풀 및 작업 그룹에 대한 현재 런타임 데이터를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="c9fff-127">Obtain the current runtime data for the resource pools and workload groups by using the following query.</span></span>  
  
    ```  
    SELECT * FROM sys.dm_resource_governor_resource_pools  
    SELECT * FROM sys.dm_resource_governor_workload_groups  
    GO  
    ```  
  
4.  <span data-ttu-id="c9fff-128">다음 쿼리를 사용하여 각 그룹에 있는 세션을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="c9fff-128">Find out what sessions are in each group by using the following query.</span></span>  
  
    ```  
    SELECT s.group_id, CAST(g.name as nvarchar(20)), s.session_id, s.login_time, CAST(s.host_name as nvarchar(20)), CAST(s.program_name AS nvarchar(20))  
              FROM sys.dm_exec_sessions s  
         INNER JOIN sys.dm_resource_governor_workload_groups g  
              ON g.group_id = s.group_id  
    ORDER BY g.name  
    GO  
    ```  
  
5.  <span data-ttu-id="c9fff-129">다음 쿼리를 사용하여 각 그룹에 있는 요청을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="c9fff-129">Find out which requests are in each group by using the following query.</span></span>  
  
    ```  
    SELECT r.group_id, g.name, r.status, r.session_id, r.request_id, r.start_time, r.command, r.sql_handle, t.text   
               FROM sys.dm_exec_requests r  
         INNER JOIN sys.dm_resource_governor_workload_groups g  
                ON g.group_id = r.group_id  
         CROSS APPLY sys.dm_exec_sql_text(r.sql_handle) AS t  
    ORDER BY g.name  
    GO  
    ```  
  
6.  <span data-ttu-id="c9fff-130">다음 쿼리를 사용하여 분류자에서 실행하는 요청을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="c9fff-130">Find out what requests are running in the classifier by using the following query.</span></span>  
  
    ```  
    SELECT s.group_id, g.name, s.session_id, s.login_time, s.host_name, s.program_name   
               FROM sys.dm_exec_sessions s  
         INNER JOIN sys.dm_resource_governor_workload_groups g  
               ON g.group_id = s.group_id  
                     AND 'preconnect' = s.status  
    ORDER BY g.name  
    GO  
  
    SELECT r.group_id, g.name, r.status, r.session_id, r.request_id, r.start_time, r.command, r.sql_handle, t.text   
               FROM sys.dm_exec_requests r  
         INNER JOIN sys.dm_resource_governor_workload_groups g  
               ON g.group_id = r.group_id  
                     AND 'preconnect' = r.status  
         CROSS APPLY sys.dm_exec_sql_text(r.sql_handle) AS t  
    ORDER BY g.name  
    GO  
    ```  
  
### <a name="best-practices-for-using-lookup-tables-in-a-classifier-function"></a><span data-ttu-id="c9fff-131">분류자 함수에서 조회 테이블을 사용하는 최선의 구현 방법</span><span class="sxs-lookup"><span data-stu-id="c9fff-131">Best practices for using Lookup Tables in a classifier function</span></span>  
  
1.  <span data-ttu-id="c9fff-132">조회 테이블은 반드시 필요한 경우에만 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="c9fff-132">Do not use a lookup table unless it is absolutely necessary.</span></span> <span data-ttu-id="c9fff-133">조회 테이블을 사용해야 하는 경우에는 함수 자체에 테이블을 하드 코딩할 수 있습니다. 그러나 이 경우에는 분류자 함수의 동적 변경 및 복잡도 간에 균형을 조정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9fff-133">If you need to use a lookup table, it can be hard coded into the function itself; however, this needs to be balanced with the complexity and dynamic changes of the classifier function.</span></span>  
  
2.  <span data-ttu-id="c9fff-134">조회 테이블에 대해 수행되는 I/O를 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="c9fff-134">Limit the I/O performed for lookup tables.</span></span>  
  
    1.  <span data-ttu-id="c9fff-135">TOP 1을 사용하여 행을 하나만 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="c9fff-135">Use the TOP 1 to return only one row.</span></span>  
  
    2.  <span data-ttu-id="c9fff-136">테이블의 행 수를 최소화합니다.</span><span class="sxs-lookup"><span data-stu-id="c9fff-136">Minimize the number of rows in the table.</span></span>  
  
    3.  <span data-ttu-id="c9fff-137">테이블의 모든 행이 한 페이지 또는 소수의 페이지에 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9fff-137">Make all rows of the table exist on a single page, or a small number of pages.</span></span>  
  
    4.  <span data-ttu-id="c9fff-138">Index Seek 작업을 사용하여 찾은 행이 최대한 많은 찾기 열을 사용하는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="c9fff-138">Confirm that rows found using the Index Seek operations use as many seeking columns as possible.</span></span>  
  
    5.  <span data-ttu-id="c9fff-139">조인을 통해 여러 테이블을 사용하려는 경우에는 단일 테이블로 비정규화합니다.</span><span class="sxs-lookup"><span data-stu-id="c9fff-139">De-normalize to a single table if you are considering using multiple tables with joins.</span></span>  
  
3.  <span data-ttu-id="c9fff-140">조회 테이블에 대한 차단을 방지합니다.</span><span class="sxs-lookup"><span data-stu-id="c9fff-140">Prevent blocking on the lookup table.</span></span>  
  
    1.  <span data-ttu-id="c9fff-141">`NOLOCK` 힌트를 사용하여 차단을 방지하거나 함수에서 `SET LOCK_TIMEOUT` (최대값 1000밀리초)을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="c9fff-141">Use the `NOLOCK` hint to prevent blocking or use `SET LOCK_TIMEOUT` in the function with a maximum value of 1000 milliseconds.</span></span>  
  
    2.  <span data-ttu-id="c9fff-142">테이블은 반드시 master 데이터베이스에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9fff-142">Table(s) must exist in the master database.</span></span> <span data-ttu-id="c9fff-143">클라이언트 컴퓨터가 연결을 시도할 때 복구가 보장되는 데이터베이스는 master 데이터베이스뿐입니다.</span><span class="sxs-lookup"><span data-stu-id="c9fff-143">(The master database is the only database that is guaranteed to be recovered when the client computers attempt to connect).</span></span>  
  
    3.  <span data-ttu-id="c9fff-144">항상 스키마를 사용하여 테이블 이름을 정규화합니다.</span><span class="sxs-lookup"><span data-stu-id="c9fff-144">Always fully-qualify the table name with the schema.</span></span> <span data-ttu-id="c9fff-145">master 데이터베이스를 사용해야 하기 때문에 데이터베이스 이름은 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c9fff-145">The database name is not necessary since it has to be the master database.</span></span>  
  
    4.  <span data-ttu-id="c9fff-146">테이블에 트리거를 사용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c9fff-146">No triggers on the table.</span></span>  
  
    5.  <span data-ttu-id="c9fff-147">테이블 콘텐츠를 업데이트하는 경우에는 기록기가 판독기를 차단하지 않도록 스냅샷 격리 수준 트랜잭션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="c9fff-147">If you are updating the table contents, make sure to use a snapshot isolation level transaction to prevent Writer blocking Readers.</span></span> <span data-ttu-id="c9fff-148">`NOLOCK` 힌트를 사용해도 차단을 완화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c9fff-148">Note that using the `NOLOCK` hint should also mitigate this.</span></span>  
  
    6.  <span data-ttu-id="c9fff-149">가능한 경우 테이블 콘텐츠 변경 시 분류자 함수를 사용하지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="c9fff-149">If possible, disable the classifier function when changing the table contents.</span></span>  
  
        > [!WARNING]  
        >  <span data-ttu-id="c9fff-150">이러한 최선의 구현 방법을 따르는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="c9fff-150">We highly recommend following these best practices.</span></span> <span data-ttu-id="c9fff-151">문제가 발생하여 최선의 구현 방법을 따를 수 없는 경우에는 Microsoft 지원 센터에 문의하여 향후 발생할 수 있는 문제를 예방하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="c9fff-151">If there are issues that prevent you from following the best practices, we recommend that you contact Microsoft Support so that you can proactively prevent any future problems.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9fff-152">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c9fff-152">See Also</span></span>  
 <span data-ttu-id="c9fff-153">[리소스 관리자](resource-governor.md) </span><span class="sxs-lookup"><span data-stu-id="c9fff-153">[Resource Governor](resource-governor.md) </span></span>  
 <span data-ttu-id="c9fff-154">[리소스 관리자 사용](enable-resource-governor.md) </span><span class="sxs-lookup"><span data-stu-id="c9fff-154">[Enable Resource Governor](enable-resource-governor.md) </span></span>  
 <span data-ttu-id="c9fff-155">[리소스 관리자 리소스 풀](resource-governor-resource-pool.md) </span><span class="sxs-lookup"><span data-stu-id="c9fff-155">[Resource Governor Resource Pool](resource-governor-resource-pool.md) </span></span>  
 <span data-ttu-id="c9fff-156">[리소스 관리자 작업 그룹](resource-governor-workload-group.md) </span><span class="sxs-lookup"><span data-stu-id="c9fff-156">[Resource Governor Workload Group](resource-governor-workload-group.md) </span></span>  
 <span data-ttu-id="c9fff-157">[템플릿을 사용하여 리소스 관리자 구성](configure-resource-governor-using-a-template.md) </span><span class="sxs-lookup"><span data-stu-id="c9fff-157">[Configure Resource Governor Using a Template](configure-resource-governor-using-a-template.md) </span></span>  
 <span data-ttu-id="c9fff-158">[리소스 관리자 속성 보기](view-resource-governor-properties.md) </span><span class="sxs-lookup"><span data-stu-id="c9fff-158">[View Resource Governor Properties](view-resource-governor-properties.md) </span></span>  
 <span data-ttu-id="c9fff-159">[ALTER RESOURCE GOVERNOR&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-resource-governor-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c9fff-159">[ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-resource-governor-transact-sql) </span></span>  
 <span data-ttu-id="c9fff-160">[CREATE RESOURCE POOL&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-resource-pool-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c9fff-160">[CREATE RESOURCE POOL &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-resource-pool-transact-sql) </span></span>  
 <span data-ttu-id="c9fff-161">[CREATE WORKLOAD GROUP&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-workload-group-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c9fff-161">[CREATE WORKLOAD GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-workload-group-transact-sql) </span></span>  
 <span data-ttu-id="c9fff-162">[CREATE FUNCTION&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-function-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c9fff-162">[CREATE FUNCTION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-function-transact-sql) </span></span>  
 [<span data-ttu-id="c9fff-163">ALTER RESOURCE GOVERNOR&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="c9fff-163">ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-resource-governor-transact-sql)  
  
  
