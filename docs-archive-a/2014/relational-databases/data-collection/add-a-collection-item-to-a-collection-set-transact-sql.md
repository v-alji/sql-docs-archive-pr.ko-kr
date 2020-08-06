---
title: 컬렉션 집합에 컬렉션 항목 추가(Transact-SQL) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- collection items [SQL Server]
- collection sets [SQL Server], adding items
ms.assetid: 9fe6454e-8c0e-4b50-937b-d9871b20fd13
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0b21508761bdfbaf8918242b074f78203c1bcaed
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661152"
---
# <a name="add-a-collection-item-to-a-collection-set-transact-sql"></a><span data-ttu-id="d70ba-102">컬렉션 집합에 컬렉션 항목 추가(Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="d70ba-102">Add a Collection Item to a Collection Set (Transact-SQL)</span></span>
  <span data-ttu-id="d70ba-103">데이터 수집기와 함께 제공되는 저장 프로시저를 사용하여 기존 컬렉션 집합에 컬렉션 항목을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d70ba-103">You can add a collection item to an existing collection set using the stored procedures that are provided with the data collector.</span></span>  
  
 <span data-ttu-id="d70ba-104">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]의 쿼리 편집기를 사용하여 다음 단계를 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d70ba-104">Carry out the following steps using Query Editor in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
### <a name="add-a-collection-item-to-a-collection-set"></a><span data-ttu-id="d70ba-105">컬렉션 집합에 컬렉션 항목 추가</span><span class="sxs-lookup"><span data-stu-id="d70ba-105">Add a collection item to a collection set</span></span>  
  
1.  <span data-ttu-id="d70ba-106">**sp_syscollector_stop_collection_set** 저장 프로시저를 실행하여 항목을 추가할 컬렉션 집합을 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="d70ba-106">Stop the collection set that you want to add the item to by running the **sp_syscollector_stop_collection_set** stored procedure.</span></span> <span data-ttu-id="d70ba-107">예를 들어, "Test Collection Set"라는 컬렉션 집합을 중지하려면 다음 문을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="d70ba-107">For example, to stop a collection set that is named "Test Collection Set", run the following statements:</span></span>  
  
    ```sql  
    USE msdb  
    DECLARE @csid int  
    SELECT @csid = collection_set_id  
    FROM syscollector_collection_sets  
    WHERE name = 'Test Collection Set'  
    SELECT @csid  
    EXEC dbo.sp_syscollector_stop_collection_set @collection_set_id = @csid  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="d70ba-108">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 개체 탐색기를 사용하여 컬렉션 집합을 중지할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d70ba-108">You can also stop the collection set by using Object Explorer in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="d70ba-109">자세한 내용은 [컬렉션 집합 시작 또는 중지](start-or-stop-a-collection-set.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d70ba-109">For more information, see [Start or Stop a Collection Set](start-or-stop-a-collection-set.md).</span></span>  
  
2.  <span data-ttu-id="d70ba-110">컬렉션 항목을 추가하려는 컬렉션 집합을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d70ba-110">Declare the collection set that you want to add the collection item to.</span></span> <span data-ttu-id="d70ba-111">다음 코드에서는 컬렉션 집합 ID를 선언하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d70ba-111">The following code provides an example of how to declare the collection set ID.</span></span>  
  
    ```sql  
    DECLARE @collection_set_id_1 int  
    SELECT @collection_set_id_1 = collection_set_id FROM [msdb].[dbo].[syscollector_collection_sets]  
    WHERE name = N'Test Collection Set'; -- name of collection set  
    ```  
  
3.  <span data-ttu-id="d70ba-112">수집기 유형을 선언합니다.</span><span class="sxs-lookup"><span data-stu-id="d70ba-112">Declare the collector type.</span></span> <span data-ttu-id="d70ba-113">다음 코드에서는 일반 T-SQL 쿼리 수집기 유형을 선언하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d70ba-113">The following code provides an example of how to declare the Generic T-SQL Query collector type.</span></span>  
  
    ```sql  
    DECLARE @collector_type_uid_1 uniqueidentifier  
    SELECT @collector_type_uid_1 = collector_type_uid FROM [msdb].[dbo].[syscollector_collector_types]   
       WHERE name = N'Generic T-SQL Query Collector Type';  
    ```  
  
     <span data-ttu-id="d70ba-114">다음 코드를 실행하여 설치된 수집기 유형의 목록을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="d70ba-114">You can run the following code to obtain a list of the installed collector types:</span></span>  
  
    ```sql  
    USE msdb  
    SELECT * from syscollector_collector_types  
    GO  
    ```  
  
4.  <span data-ttu-id="d70ba-115">**sp_syscollector_create_collection_item** 저장 프로시저를 실행하여 컬렉션 항목을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d70ba-115">Run the **sp_syscollector_create_collection_item** stored procedure to create the collection item.</span></span> <span data-ttu-id="d70ba-116">원하는 수집기 유형에 필요한 스키마에 매핑되도록 컬렉션 항목에 대한 스키마를 선언해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d70ba-116">You must declare the schema for the collection item so that it maps to the required schema for the desired collector type.</span></span> <span data-ttu-id="d70ba-117">다음 예제에서는 일반 T-SQL 쿼리 입력 스키마를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="d70ba-117">The following example uses the Generic T-SQL Query input schema.</span></span>  
  
    ```sql  
    DECLARE @collection_item_id int;  
    EXEC [msdb].[dbo].[sp_syscollector_create_collection_item]   
    @name=N'OS Wait Stats', --name of collection item  
    @parameters=N'  
    <ns:TSQLQueryCollector xmlns:ns="DataCollectorType">  
     <Query>  
      <Value>select * from sys.dm_os_wait_stats</Value>  
      <OutputTable>os_wait_stats</OutputTable>  
    </Query>  
    </ns:TSQLQueryCollector>',  
    @collection_item_id = @collection_item_id OUTPUT,  
    @frequency = 60,  
    @collection_set_id = @collection_set_id_1, --- Provides the collection set ID number  
    @collector_type_uid = @collector_type_uid_1 -- Provides the collector type UID  
    SELECT @collection_item_id     
    ```  
  
5.  <span data-ttu-id="d70ba-118">업데이트된 컬렉션 집합을 시작하기 전에 다음 쿼리를 실행하여 새 컬렉션 항목이 만들어졌는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="d70ba-118">Before starting the updated collection set, run the following query to verify that the new collection item has been created:</span></span>  
  
    ```xaml  
    USE msdb  
    SELECT * from syscollector_collection_sets  
    SELECT * from syscollector_collection_items  
    GO  
    ```  
  
     <span data-ttu-id="d70ba-119">컬렉션 집합 및 해당 컬렉션 항목은 **결과** 탭에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d70ba-119">The collection sets and their collection items are displayed in the **Results** tab.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d70ba-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d70ba-120">See Also</span></span>  
 <span data-ttu-id="d70ba-121">[일반 T-SQL 쿼리 수집기 유형을 사용하는 사용자 지정 컬렉션 집합 만들기&#40;Transact-SQL&#41;](create-custom-collection-set-generic-t-sql-query-collector-type.md) </span><span class="sxs-lookup"><span data-stu-id="d70ba-121">[Create a Custom Collection Set That Uses the Generic T-SQL Query Collector Type &#40;Transact-SQL&#41;](create-custom-collection-set-generic-t-sql-query-collector-type.md) </span></span>  
 [<span data-ttu-id="d70ba-122">데이터 수집기 저장 프로시저&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="d70ba-122">Data Collector Stored Procedures &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql)  
  
  
