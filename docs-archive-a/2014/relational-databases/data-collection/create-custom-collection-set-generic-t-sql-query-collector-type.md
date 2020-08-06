---
title: 일반 T-sql 쿼리 수집기 유형 (Transact-sql)을 사용 하는 사용자 지정 컬렉션 집합 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- T-SQL Query collector type
- collection sets [SQL Server], creating custom
ms.assetid: 6b06db5b-cfdc-4ce0-addd-ec643460605b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ab21ad5fd65556dec639fd5ca6999d23e2de673b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652871"
---
# <a name="create-a-custom-collection-set-that-uses-the-generic-t-sql-query-collector-type-transact-sql"></a><span data-ttu-id="c9550-102">일반 T-SQL 쿼리 수집기 유형을 사용하는 사용자 지정 컬렉션 집합 만들기(Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="c9550-102">Create a Custom Collection Set That Uses the Generic T-SQL Query Collector Type (Transact-SQL)</span></span>
  <span data-ttu-id="c9550-103">데이터 수집기와 함께 제공된 저장 프로시저를 사용하여 일반 T-SQL 쿼리 수집기 유형을 사용하는 컬렉션 항목을 포함하는 사용자 지정 컬렉션 집합을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c9550-103">You can create a custom collection set with collection items that use the Generic T-SQL Query collector type by using the stored procedures that are provided with the data collector.</span></span> <span data-ttu-id="c9550-104">이 태스크를 수행하려면 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 의 쿼리 편집기를 사용하여 다음 절차를 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9550-104">Accomplishing this task involves using Query Editor in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to carry out the following procedures:</span></span>  
  
-   <span data-ttu-id="c9550-105">업로드 일정 구성</span><span class="sxs-lookup"><span data-stu-id="c9550-105">Configure upload schedules.</span></span>  
  
-   <span data-ttu-id="c9550-106">컬렉션 집합 정의 및 만들기</span><span class="sxs-lookup"><span data-stu-id="c9550-106">Define and create the collection set.</span></span>  
  
-   <span data-ttu-id="c9550-107">컬렉션 항목 정의 및 만들기</span><span class="sxs-lookup"><span data-stu-id="c9550-107">Define and create a collection item.</span></span>  
  
-   <span data-ttu-id="c9550-108">컬렉션 집합 및 컬렉션 항목의 존재 여부 확인</span><span class="sxs-lookup"><span data-stu-id="c9550-108">Verify that the collection set and collection items exist.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c9550-109">사용자 지정 컬렉션 집합을 만들기 전에 데이터 컬렉션 매개 변수를 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9550-109">Before you create a custom collection set, you must configure data collection parameters.</span></span> <span data-ttu-id="c9550-110">자세한 내용은 [데이터 컬렉션 매개 변수 구성&#40;Transact-SQL&#41;](configure-data-collection-parameters-transact-sql.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c9550-110">For more information, see [Configure Data Collection Parameters &#40;Transact-SQL&#41;](configure-data-collection-parameters-transact-sql.md).</span></span>  
  
### <a name="define-and-create-the-collection-set"></a><span data-ttu-id="c9550-111">컬렉션 집합 정의 및 만들기</span><span class="sxs-lookup"><span data-stu-id="c9550-111">Define and create the collection set</span></span>  
  
1.  <span data-ttu-id="c9550-112">sp_syscollector_create_collection_set 저장 프로시저를 사용하여 새 컬렉션 집합을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="c9550-112">Define a new collection set using the sp_syscollector_create_collection_set stored procedure.</span></span>  
  
    ```  
    USE msdb;  
    DECLARE @collection_set_id int;  
    DECLARE @collection_set_uid uniqueidentifier;  
    EXEC sp_syscollector_create_collection_set   
        @name=N'DMV Test 1',   
        @collection_mode=0,   
        @description=N'This is a test collection set',   
        @logging_level=1,   
        @days_until_expiration=14,   
        @schedule_name=N'CollectorSchedule_Every_15min',   
        @collection_set_id=@collection_set_id OUTPUT,   
        @collection_set_uid=@collection_set_uid OUTPUT;  
    SELECT @collection_set_id, @collection_set_uid;  
    ```  
  
     <span data-ttu-id="c9550-113">컬렉션 모드는 0(캐시됨) 또는 1(캐시 안 됨)로 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c9550-113">The collection mode can be set to either 0 (cached) or to 1 (non-cached).</span></span>  
  
     <span data-ttu-id="c9550-114">로깅 수준은 0, 1 또는 2로 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c9550-114">The logging level can be set to 0, 1 or 2.</span></span>  
  
     <span data-ttu-id="c9550-115">데이터 수집기와 함께 제공되는 미리 구성된 일정은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="c9550-115">The following preconfigured schedules are provided with the data collector:</span></span>  
  
    -   <span data-ttu-id="c9550-116">CollectorSchedule_Every_5min</span><span class="sxs-lookup"><span data-stu-id="c9550-116">CollectorSchedule_Every_5min</span></span>  
  
    -   <span data-ttu-id="c9550-117">CollectorSchedule_Every_10min</span><span class="sxs-lookup"><span data-stu-id="c9550-117">CollectorSchedule_Every_10min</span></span>  
  
    -   <span data-ttu-id="c9550-118">CollectorSchedule_Every_15min</span><span class="sxs-lookup"><span data-stu-id="c9550-118">CollectorSchedule_Every_15min</span></span>  
  
    -   <span data-ttu-id="c9550-119">CollectorSchedule_Every_30min</span><span class="sxs-lookup"><span data-stu-id="c9550-119">CollectorSchedule_Every_30min</span></span>  
  
    -   <span data-ttu-id="c9550-120">CollectorSchedule_Every_60min</span><span class="sxs-lookup"><span data-stu-id="c9550-120">CollectorSchedule_Every_60min</span></span>  
  
    -   <span data-ttu-id="c9550-121">CollectorSchedule_Every_6h</span><span class="sxs-lookup"><span data-stu-id="c9550-121">CollectorSchedule_Every_6h</span></span>  
  
     <span data-ttu-id="c9550-122">제공되는 일정 중 하나를 사용하지 않으려는 경우 새 일정을 만들어 컬렉션 집합에 대해 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c9550-122">If you do not want to use one of the schedules that are provided, you can create a new schedule and use it for the collection set.</span></span> <span data-ttu-id="c9550-123">자세한 내용은 [일정을 만들고 작업에 연결](../../ssms/agent/create-and-attach-schedules-to-jobs.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c9550-123">For more information, see [Create and Attach Schedules to Jobs](../../ssms/agent/create-and-attach-schedules-to-jobs.md).</span></span>  
  
### <a name="define-and-create-a-collection-item"></a><span data-ttu-id="c9550-124">컬렉션 항목 정의 및 만들기</span><span class="sxs-lookup"><span data-stu-id="c9550-124">Define and create a collection item</span></span>  
  
1.  <span data-ttu-id="c9550-125">새 컬렉션 항목은 이미 설치된 일반 수집기 유형을 기반으로 하므로 다음 코드를 실행하여 일반 T-SQL 쿼리 수집기 유형에 해당하는 GUID를 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c9550-125">Because the new collection item is based on a generic collector type that is already installed, you can run the following code to set the GUID to correspond to the Generic T-SQL Query collector type.</span></span>  
  
    ```sql  
    DECLARE @collector_type_uid uniqueidentifier;  
    SELECT @collector_type_uid = collector_type_uid FROM [msdb].[dbo].[syscollector_collector_types]   
    WHERE name = N'Generic T-SQL Query Collector Type';  
    DECLARE @collection_item_id int;  
    ```  
  
2.  <span data-ttu-id="c9550-126">sp_syscollector_create_collection_item 저장 프로시저를 사용하여 컬렉션 항목을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c9550-126">Use the sp_syscollector_create_collection_item stored procedure to create the collection item.</span></span> <span data-ttu-id="c9550-127">일반 T-SQL 쿼리 수집기 유형에 필요한 스키마에 매핑되도록 컬렉션 항목에 대한 스키마를 선언합니다.</span><span class="sxs-lookup"><span data-stu-id="c9550-127">Declare the schema for the collection item so it maps to the schema that is required for the Generic T-SQL Query collector type.</span></span>  
  
    ```sql  
    EXEC sp_syscollector_create_collection_item   
        @name=N'Query Stats - Test 1',   
        @parameters=N'  
            <ns:TSQLQueryCollector xmlns:ns="DataCollectorType">  
            <Query>  
            <Value>SELECT * FROM sys.dm_exec_query_stats</Value>  
            <OutputTable>dm_exec_query_stats</OutputTable>  
            </Query>  
            </ns:TSQLQueryCollector>',   
        @collection_item_id=@collection_item_id OUTPUT,   
        @frequency=5,   
        @collection_set_id=@collection_set_id,   
        @collector_type_uid=@collector_type_uid;  
    SELECT @collection_item_id;  
    ```  
  
### <a name="verify-that-the-new-collection-set-and-collection-item-exist"></a><span data-ttu-id="c9550-128">새 컬렉션 집합 및 컬렉션 항목의 존재 여부 확인</span><span class="sxs-lookup"><span data-stu-id="c9550-128">Verify that the new collection set and collection item exist</span></span>  
  
1.  <span data-ttu-id="c9550-129">새 컬렉션 집합을 시작하기 전에 다음 쿼리를 실행하여 새 컬렉션 집합 및 해당 컬렉션 항목이 생성되었는지 여부를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="c9550-129">Before starting the new collection set, run the following query to verify that the new collection set and its collection item have been created.</span></span>  
  
    ```sql  
    USE msdb;  
    SELECT * FROM syscollector_collection_sets;  
    SELECT * FROM syscollector_collection_items;  
    GO  
    ```  
  
     <span data-ttu-id="c9550-130">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 직접 확인할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c9550-130">You can also do a visual check in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="c9550-131">개체 탐색기에서 **관리** 노드를 확장한 다음 **데이터 컬렉션**을 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="c9550-131">In Object Explorer, expand the **Management** node, and then expand **Data Collection**.</span></span> <span data-ttu-id="c9550-132">새 컬렉션 집합이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c9550-132">The new collection set will be displayed.</span></span> <span data-ttu-id="c9550-133">컬렉션 집합의 아이콘에 있는 빨간색 원은 컬렉션 집합이 중지되었음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c9550-133">The red circle icon for the collection set indicates that the collection set is stopped.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c9550-134">예제</span><span class="sxs-lookup"><span data-stu-id="c9550-134">Example</span></span>  
 <span data-ttu-id="c9550-135">다음 코드 예는 앞의 단계에 나와 있는 예제를 조합합니다.</span><span class="sxs-lookup"><span data-stu-id="c9550-135">The following code sample combines the examples that are documented in the previous steps.</span></span> <span data-ttu-id="c9550-136">컬렉션 집합 컬렉션 모드가 캐시됨 모드인 0으로 설정되어 있으므로 컬렉션 항목에 대해 설정된 컬렉션 빈도(5초)가 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c9550-136">Note that the collection frequency that is set for the collection item (5 seconds) is ignored because the collection set collection mode is set to 0, which is cached mode.</span></span> <span data-ttu-id="c9550-137">자세한 내용은 [Data Collection](data-collection.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c9550-137">For more information, see [Data Collection](data-collection.md).</span></span>  
  
```sql  
USE msdb;  
  
DECLARE @collection_set_id int;  
DECLARE @collection_set_uid uniqueidentifier  
  
EXEC dbo.sp_syscollector_create_collection_set  
    @name = N'DMV Stats Test 1',  
    @collection_mode = 0,  
    @description = N'This is a test collection set',  
    @logging_level=1,  
    @days_until_expiration = 14,  
    @schedule_name=N'CollectorSchedule_Every_15min',  
    @collection_set_id = @collection_set_id OUTPUT,  
    @collection_set_uid = @collection_set_uid OUTPUT;  
SELECT @collection_set_id,@collection_set_uid;  
  
DECLARE @collector_type_uid uniqueidentifier;  
SELECT @collector_type_uid = collector_type_uid FROM syscollector_collector_types   
WHERE name = N'Generic T-SQL Query Collector Type';  
  
DECLARE @collection_item_id int;  
EXEC sp_syscollector_create_collection_item  
@name= N'Query Stats - Test 1',  
@parameters=N'  
<ns:TSQLQueryCollector xmlns:ns="DataCollectorType">  
<Query>  
  <Value>select * from sys.dm_exec_query_stats</Value>  
  <OutputTable>dm_exec_query_stats</OutputTable>  
</Query>  
 </ns:TSQLQueryCollector>',  
    @collection_item_id = @collection_item_id OUTPUT,  
    @frequency = 5, -- This parameter is ignored in cached mode  
    @collection_set_id = @collection_set_id,  
    @collector_type_uid = @collector_type_uid;  
SELECT @collection_item_id;  
  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="c9550-138">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c9550-138">See Also</span></span>  
 <span data-ttu-id="c9550-139">[데이터 수집기 저장 프로시저&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c9550-139">[Data Collector Stored Procedures &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql) </span></span>  
 <span data-ttu-id="c9550-140">[일정 관리](../../ssms/agent/manage-schedules.md) </span><span class="sxs-lookup"><span data-stu-id="c9550-140">[Manage Schedules](../../ssms/agent/manage-schedules.md) </span></span>  
 [<span data-ttu-id="c9550-141">컬렉션 집합 시작 또는 중지</span><span class="sxs-lookup"><span data-stu-id="c9550-141">Start or Stop a Collection Set</span></span>](start-or-stop-a-collection-set.md)  
  
  
