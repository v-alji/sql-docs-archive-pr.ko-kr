---
title: 변경 내용 추적 사용(SQL Server) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- change tracking [SQL Server], making changes
- change tracking [SQL Server], troubleshooting
- updating data [SQL Server]
- troubleshooting [SQL Server], change tracking
- data changes [SQL Server]
- tracking data changes [SQL Server]
- data [SQL Server], changing
- change tracking [SQL Server], data restore
- change tracking [SQL Server], ensuring consistent results
- change tracking [SQL Server], handling changes
ms.assetid: 5aec22ce-ae6f-4048-8a45-59ed05f04dc5
author: rothja
ms.author: jroth
ms.openlocfilehash: bdb8205a789894caf8c8e2d3c3f491751757bab6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660421"
---
# <a name="work-with-change-tracking-sql-server"></a><span data-ttu-id="44a41-102">변경 내용 추적 사용(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="44a41-102">Work with Change Tracking (SQL Server)</span></span>
  <span data-ttu-id="44a41-103">변경 내용 추적을 사용하는 애플리케이션은 추적된 변경 내용을 가져와서 다른 데이터 저장소에 적용하고 원본 데이터베이스를 업데이트할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-103">Applications that use change tracking must be able to obtain tracked changes, apply these changes to another data store, and update the source database.</span></span> <span data-ttu-id="44a41-104">이 항목에서는 이러한 태스크를 수행하는 방법과 장애 조치(Failover)가 발생하여 백업에서 데이터베이스를 복원해야 할 때 변경 내용 추적이 수행하는 역할에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-104">This topic describes how to perform these tasks, and also the role change tracking plays when a failover occurs and a database must be restored from a backup.</span></span>  
  
##  <a name="obtain-changes-by-using-change-tracking-functions"></a><a name="Obtain"></a> <span data-ttu-id="44a41-105">변경 내용 추적 함수를 사용하여 변경 내용 가져오기</span><span class="sxs-lookup"><span data-stu-id="44a41-105">Obtain Changes by Using Change Tracking Functions</span></span>  
 <span data-ttu-id="44a41-106">변경 내용 추적 함수를 사용하여 변경 내용과 데이터베이스에 수행된 변경에 대한 정보를 가져오는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-106">Describes how to use the change tracking functions to obtain changes and information about the changes that were made to a database.</span></span>  
  
### <a name="about-the-change-tracking-functions"></a><span data-ttu-id="44a41-107">변경 내용 추적 함수 정보</span><span class="sxs-lookup"><span data-stu-id="44a41-107">About the Change Tracking Functions</span></span>  
 <span data-ttu-id="44a41-108">애플리케이션은 다음 함수를 사용하여 데이터베이스에 적용된 변경 내용과 해당 변경 내용에 대한 정보를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-108">Applications can use the following functions to obtain the changes that are made in a database and information about the changes:</span></span>  
  
 <span data-ttu-id="44a41-109">CHANGETABLE(CHANGES ...) 함수</span><span class="sxs-lookup"><span data-stu-id="44a41-109">CHANGETABLE(CHANGES ...) function</span></span>  
 <span data-ttu-id="44a41-110">이 행 집합 함수는 변경 내용 정보를 쿼리하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-110">This rowset function is used to query for change information.</span></span> <span data-ttu-id="44a41-111">이 함수는 내부 변경 내용 추적 테이블에 저장된 데이터를 쿼리합니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-111">The function queries the data stored in the internal change tracking tables.</span></span> <span data-ttu-id="44a41-112">또한 이 함수는 작업, 업데이트된 열 및 행의 버전과 같은 다른 변경 내용 정보와 함께, 변경된 행의 기본 키를 포함하는 결과 집합을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-112">The function returns a results set that contains the primary keys of rows that have changed together with other change information such as the operation, columns updated and version for the row.</span></span>  
  
 <span data-ttu-id="44a41-113">CHANGETABLE(CHANGES ...)은 마지막 동기화 버전을 인수로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-113">CHANGETABLE(CHANGES ...) takes a last synchronization version as an argument.</span></span> <span data-ttu-id="44a41-114">마지막 동기화 버전은 `@last_synchronization_version` 변수를 사용하여 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-114">The last sychronization version is obtained using the `@last_synchronization_version` variable.</span></span> <span data-ttu-id="44a41-115">마지막 동기화 버전의 의미 체계는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-115">The semantics of the last synchronization version are as follows:</span></span>  
  
-   <span data-ttu-id="44a41-116">호출 클라이언트가 변경 내용을 가져왔으며 마지막 동기화 버전까지의 모든 변경 내용에 대해 알고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-116">The calling client has obtained changes and knows about all changes up to and including the last synchronization version.</span></span>  
  
-   <span data-ttu-id="44a41-117">따라서 CHANGETABLE(CHANGES ...)이 마지막 동기화 버전 이후 발생한 모든 변경 내용을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-117">CHANGETABLE(CHANGES ...) will therefore return all changes that have occurred after the last synchronization version.</span></span>  
  
     <span data-ttu-id="44a41-118">다음 그림에서는 CHANGETABLE(CHANGES ...)을 사용하여 변경 내용을 가져오는 방법을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-118">The following illustration shows how CHANGETABLE(CHANGES ...) is used to obtain changes.</span></span>  
  
     <span data-ttu-id="44a41-119">![변경 내용 추적 쿼리 출력의 예](../../database-engine/media/queryoutput.gif "변경 내용 추적 쿼리 출력의 예")</span><span class="sxs-lookup"><span data-stu-id="44a41-119">![Example of change tracking query output](../../database-engine/media/queryoutput.gif "Example of change tracking query output")</span></span>  
  
 <span data-ttu-id="44a41-120">CHANGE_TRACKING_CURRENT_VERSION() 함수</span><span class="sxs-lookup"><span data-stu-id="44a41-120">CHANGE_TRACKING_CURRENT_VERSION() function</span></span>  
 <span data-ttu-id="44a41-121">다음에 변경 내용을 쿼리할 때 사용할 현재 버전을 가져오는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-121">Is used to obtain the current version that will be used the next time when querying changes.</span></span> <span data-ttu-id="44a41-122">이 버전은 마지막으로 커밋된 트랜잭션의 버전을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-122">This version represents the version of the last committed transaction.</span></span>  
  
 <span data-ttu-id="44a41-123">CHANGE_TRACKING_MIN_VALID_VERSION() 함수</span><span class="sxs-lookup"><span data-stu-id="44a41-123">CHANGE_TRACKING_MIN_VALID_VERSION()function</span></span>  
 <span data-ttu-id="44a41-124">클라이언트에 포함할 수 있는 올바른 최소 버전을 가져오고 CHANGETABLE()에서 올바른 결과를 가져오는 데 계속 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-124">Is used to obtain the minimum valid version that a client can have and still obtain valid results from CHANGETABLE().</span></span> <span data-ttu-id="44a41-125">클라이언트는 이 함수에서 반환된 값에 대해 마지막 동기화 버전을 검사해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-125">The client should check the last synchronization version against the value thatis returned by this function.</span></span> <span data-ttu-id="44a41-126">마지막 동기화 버전이 이 함수에서 반환된 버전보다 작은 경우 클라이언트는 CHANGETABLE()에서 올바른 결과를 가져올 수 없으며 다시 초기화되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-126">If the last synchronization version is less than the version returned by this function, the client will be unable to obtain valid results from CHANGETABLE() and will have to reinitialize.</span></span>  
  
### <a name="obtaining-initial-data"></a><span data-ttu-id="44a41-127">초기 데이터 가져오기</span><span class="sxs-lookup"><span data-stu-id="44a41-127">Obtaining Initial Data</span></span>  
 <span data-ttu-id="44a41-128">애플리케이션에서 처음으로 변경 내용을 가져오려면 먼저 초기 데이터 및 동기화 버전을 가져오는 쿼리를 보내야 합니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-128">Before an application can obtain changes for the first time, the application must send a query to obtain the initial data and the synchronization version.</span></span> <span data-ttu-id="44a41-129">애플리케이션은 테이블에서 적합한 데이터를 직접 가져온 다음 CHANGE_TRACKING_CURRENT_VERSION()을 사용하여 초기 버전을 가져와야 합니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-129">The application must obtain the appropriate data directly from the table, and then use CHANGE_TRACKING_CURRENT_VERSION() to obtain the initial version.</span></span> <span data-ttu-id="44a41-130">처음 변경 내용을 가져오면 이 버전이 CHANGETABLE(CHANGES ...)에 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-130">This version will be passed to CHANGETABLE(CHANGES ...) the first time that changes are obtained.</span></span>  
  
 <span data-ttu-id="44a41-131">다음 예에서는 초기 동기화 버전 및 초기 데이터 집합을 가져오는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-131">The following example shows how to obtain the initial synchronization version and the initial data set.</span></span>  
  
```sql  
    -- Obtain the current synchronization version. This will be used next time that changes are obtained.  
    SET @synchronization_version = CHANGE_TRACKING_CURRENT_VERSION();  
  
    -- Obtain initial data set.  
    SELECT  
        P.ProductID, P.Name, P.ListPrice  
    FROM  
        SalesLT.Product AS P  
```  
  
### <a name="using-the-change-tracking-functions-to-obtain-changes"></a><span data-ttu-id="44a41-132">변경 내용 추적 함수를 사용하여 변경 내용 가져오기</span><span class="sxs-lookup"><span data-stu-id="44a41-132">Using the Change Tracking Functions to Obtain Changes</span></span>  
 <span data-ttu-id="44a41-133">테이블에 대해 변경된 행과 해당 변경 내용에 대한 정보를 가져오려면 CHANGETABLE(CHANGES...)을 사용합니다. 예를 들어 다음 쿼리에서는 `SalesLT.Product` 테이블에 대한 변경 내용을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-133">To obtain the changed rows for a table and information about the changes, use CHANGETABLE(CHANGES...). For example, the following query obtains changes for the `SalesLT.Product` table.</span></span>  
  
```sql  
SELECT  
    CT.ProductID, CT.SYS_CHANGE_OPERATION,  
    CT.SYS_CHANGE_COLUMNS, CT.SYS_CHANGE_CONTEXT  
FROM  
    CHANGETABLE(CHANGES SalesLT.Product, @last_synchronization_version) AS CT  
  
```  
  
 <span data-ttu-id="44a41-134">일반적으로 클라이언트는 행에 대한 기본 키만 가져오는 대신 해당 행에 대한 최신 데이터를 가져오려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-134">Usually, a client will want to obtain the latest data for a row instead of only the primary keys for the row.</span></span> <span data-ttu-id="44a41-135">따라서 애플리케이션은 CHANGETABLE(CHANGES ...)의 결과를 사용자 테이블의 데이터와 조인합니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-135">Therefore, an application would join the results from CHANGETABLE(CHANGES ...) with the data in the user table.</span></span> <span data-ttu-id="44a41-136">예를 들어 다음 쿼리에서는 `SalesLT.Product` 테이블과 조인하여 `Name` 및 `ListPrice` 열에 대한 값을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-136">For example, the following query joins with the `SalesLT.Product` table to obtain the values for the `Name` and `ListPrice` columns.</span></span> <span data-ttu-id="44a41-137">여기에서는 `OUTER JOIN`이 사용되었습니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-137">Note the use of `OUTER JOIN`.</span></span> <span data-ttu-id="44a41-138">이는 사용자 테이블에서 삭제된 행에 대해 변경 내용 정보가 반환되도록 하는 데 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-138">This is required to make sure that the change information is returned for those rows that have been deleted from the user table.</span></span>  
  
```sql  
SELECT  
    CT.ProductID, P.Name, P.ListPrice,  
    CT.SYS_CHANGE_OPERATION, CT.SYS_CHANGE_COLUMNS,  
    CT.SYS_CHANGE_CONTEXT  
FROM  
    SalesLT.Product AS P  
RIGHT OUTER JOIN  
    CHANGETABLE(CHANGES SalesLT.Product, @last_synchronization_version) AS CT  
ON  
    P.ProductID = CT.ProductID  
```  
  
 <span data-ttu-id="44a41-139">다음 변경 내용 열거에서 사용할 버전을 가져오려면 아래 예와 같이 CHANGE_TRACKING_CURRENT_VERSION()을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-139">To obtain the version for use in the next change enumeration, use CHANGE_TRACKING_CURRENT_VERSION(), as shown in the following example.</span></span>  
  
```sql  
SET @synchronization_version = CHANGE_TRACKING_CURRENT_VERSION()  
```  
  
 <span data-ttu-id="44a41-140">변경 내용을 가져올 때 애플리케이션은 다음 예와 같이 CHANGETABLE(CHANGES...) 및 CHANGE_TRACKING_CURRENT_VERSION()을 모두 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-140">When an application obtains changes, it must use both CHANGETABLE(CHANGES...) and CHANGE_TRACKING_CURRENT_VERSION(), as shown in the following example.</span></span>  
  
```sql  
-- Obtain the current synchronization version. This will be used the next time CHANGETABLE(CHANGES...) is called.  
SET @synchronization_version = CHANGE_TRACKING_CURRENT_VERSION();  
  
-- Obtain incremental changes by using the synchronization version obtained the last time the data was synchronized.  
SELECT  
    CT.ProductID, P.Name, P.ListPrice,  
    CT.SYS_CHANGE_OPERATION, CT.SYS_CHANGE_COLUMNS,  
    CT.SYS_CHANGE_CONTEXT  
FROM  
    SalesLT.Product AS P  
RIGHT OUTER JOIN  
    CHANGETABLE(CHANGES SalesLT.Product, @last_synchronization_version) AS CT  
ON  
    P.ProductID = CT.ProductID  
```  
  
### <a name="version-numbers"></a><span data-ttu-id="44a41-141">버전 번호</span><span class="sxs-lookup"><span data-stu-id="44a41-141">Version Numbers</span></span>  
 <span data-ttu-id="44a41-142">변경 내용 추적을 사용하도록 설정된 데이터베이스에는 버전 카운터가 있습니다. 이 카운터는 변경 내용 추적이 설정된 테이블에 변경 내용이 적용될 때마다 증가합니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-142">A database that has change tracking enabled has a version counter that increases as changes are made to change tracked tables.</span></span> <span data-ttu-id="44a41-143">변경된 각 행에는 이와 연관된 버전 번호가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-143">Each changed row has a version number that is associated with it.</span></span> <span data-ttu-id="44a41-144">변경 내용을 쿼리하기 위해 요청이 애플리케이션에 전송되면 버전 번호를 제공하는 함수가 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-144">When a request is sent to an application to query for changes, a function is called that supplies a version number.</span></span> <span data-ttu-id="44a41-145">이 함수는 해당 버전 이후 적용된 모든 변경 내용에 대한 정보를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-145">The function returns information about all the changes that have been made since that version.</span></span> <span data-ttu-id="44a41-146">여러 가지 측면에서 변경 내용 추적 버전은 개념상 `rowversion` 데이터 형식과 유사합니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-146">In some ways, change tracking version is similar in concept to the `rowversion` data type.</span></span>  
  
### <a name="validating-the-last-synchronized-version"></a><span data-ttu-id="44a41-147">마지막으로 동기화된 버전의 유효성 검사</span><span class="sxs-lookup"><span data-stu-id="44a41-147">Validating the Last Synchronized Version</span></span>  
 <span data-ttu-id="44a41-148">변경 내용에 대한 정보는 제한된 시간 동안 유지 관리됩니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-148">Information about changes is maintained for a limited time.</span></span> <span data-ttu-id="44a41-149">시간은 ALTER DATABASE의 일부로 지정할 수 있는 CHANGE_RETENTION 매개 변수로 제어됩니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-149">The length of time is controlled by the CHANGE_RETENTION parameter that can be specified as part of the ALTER DATABASE.</span></span>  
  
 <span data-ttu-id="44a41-150">CHANGE_RETENTION에 대해 지정하는 시간에 따라 모든 애플리케이션이 데이터베이스에서 변경 내용을 요청해야 하는 빈도가 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-150">Be aware that the time specified for CHANGE_RETENTION determines how frequently all applications must request changes from the database.</span></span> <span data-ttu-id="44a41-151">애플리케이션의 *last_synchronization_version* 값이 테이블에 대해 올바른 최소 동기화 버전보다 작으면 해당 애플리케이션은 올바른 변경 내용 열거를 수행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-151">If an application has a value for *last_synchronization_version* that is older than the minimum valid synchronization version for a table, that application cannot perform valid change enumeration.</span></span> <span data-ttu-id="44a41-152">이는 일부 변경 내용 정보가 정리되었을 수 있기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-152">This is because some change information might have been cleaned up.</span></span> <span data-ttu-id="44a41-153">애플리케이션이 CHANGETABLE(CHANGES ...)을 사용하여 변경 내용을 가져오려면 먼저 애플리케이션이 CHANGETABLE(CHANGES ...)에 전달하려고 하는 *last_synchronization_version*에 대한 값의 유효성을 검사해야 합니다. *last_synchronization_version* 의 값이 잘못된 경우 해당 애플리케이션은 모든 데이터를 다시 초기화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-153">Before an application obtains changes by using CHANGETABLE(CHANGES ...), the application must validate the value for *last_synchronization_version* that it plans to pass to CHANGETABLE(CHANGES ...). If the value of *last_synchronization_version* is not valid, that application must reinitialize all the data.</span></span>  
  
 <span data-ttu-id="44a41-154">다음 예에서는 각 테이블에 대한 `last_synchronization_version` 값의 유효성을 확인하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-154">The following example shows how to verify the validity of the value of `last_synchronization_version` for each table.</span></span>  
  
```sql  
-- Check individual table.  
IF (@last_synchronization_version < CHANGE_TRACKING_MIN_VALID_VERSION(  
                                   OBJECT_ID('SalesLT.Product')))  
BEGIN  
  -- Handle invalid version and do not enumerate changes.  
  -- Client must be reinitialized.  
END  
```  
  
 <span data-ttu-id="44a41-155">다음 예와 같이 데이터베이스의 모든 테이블에 대해 `last_synchronization_version` 값의 유효성을 검사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-155">As the following example shows, the validity of the value of `last_synchronization_version` can be checked against all tables in the database.</span></span>  
  
```sql  
-- Check all tables with change tracking enabled  
IF EXISTS (  
  SELECT COUNT(*) FROM sys.change_tracking_tables  
  WHERE min_valid_version > @last_synchronization_version )  
BEGIN  
  -- Handle invalid version & do not enumerate changes  
  -- Client must be reinitialized  
END  
```  
  
### <a name="using-column-tracking"></a><span data-ttu-id="44a41-156">열 추적 사용</span><span class="sxs-lookup"><span data-stu-id="44a41-156">Using Column Tracking</span></span>  
 <span data-ttu-id="44a41-157">애플리케이션에서 열 추적을 사용하면 전체 행 대신 변경된 열에 대한 데이터만 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-157">Column tracking enables applications to obtain the data for only the columns that have changed instead of the whole row.</span></span> <span data-ttu-id="44a41-158">예를 들어 테이블에 크지만 거의 변경되지 않는 열이 하나 이상 있고 자주 변경되는 다른 열도 있는 시나리오가 있을 경우</span><span class="sxs-lookup"><span data-stu-id="44a41-158">For example, consider the scenario in which a table has one or more columns that are large, but rarely change; and also has other columns that frequently change.</span></span> <span data-ttu-id="44a41-159">열 추적을 사용하지 않으면 애플리케이션이 행이 변경되었다는 사실만 확인할 수 있으므로 큰 열 데이터를 포함하는 데이터를 모두 동기화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-159">Without column tracking, an application can only determine that a row has changed and would have to synchronize all the data that includes the large column data.</span></span> <span data-ttu-id="44a41-160">그러나 열 추적을 사용하면 애플리케이션이 큰 열 데이터가 변경되었는지 여부를 확인하여 변경된 데이터만 동기화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-160">However, by using column tracking, an application can determine whether the large column data changed and only synchronize the data if it has changed.</span></span>  
  
 <span data-ttu-id="44a41-161">열 추적 정보는 CHANGETABLE(CHANGES ...) 함수로 반환되는 SYS_CHANGE_COLUMNS 열에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-161">Column tracking information appears in the SYS_CHANGE_COLUMNS column that is returned by the CHANGETABLE(CHANGES ...) function.</span></span>  
  
 <span data-ttu-id="44a41-162">변경되지 않은 열에 대해 NULL이 반환되도록 열 추적을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-162">Column tracking can be used so that NULL is returned for a column that has not changed.</span></span> <span data-ttu-id="44a41-163">열이 NULL로 변경될 수 있는 경우 해당 열이 변경되었는지 여부를 나타내기 위해 별도의 열을 반환해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-163">If the column can be changed to NULL, a separate column must be returned to indicate whether the column changed.</span></span>  
  
 <span data-ttu-id="44a41-164">다음 예에서는 `CT_ThumbnailPhoto` 열이 변경되지 않은 경우 해당 열이 `NULL` 이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-164">In the following example, the `CT_ThumbnailPhoto` column will be `NULL` if that column did not change.</span></span> <span data-ttu-id="44a41-165">또한 이 열은 `NULL` 로 변경되었으므로 `NULL` 이 될 수 있습니다. 애플리케이션은 `CT_ThumbNailPhoto_Changed` 열을 사용하여 해당 열이 변경되었는지 여부를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-165">This column could also be `NULL` because it was changed to `NULL` - the application can use the `CT_ThumbNailPhoto_Changed` column to determine whether the column changed.</span></span>  
  
```sql  
DECLARE @PhotoColumnId int = COLUMNPROPERTY(  
    OBJECT_ID('SalesLT.Product'),'ThumbNailPhoto', 'ColumnId')  
  
SELECT  
    CT.ProductID, P.Name, P.ListPrice, -- Always obtain values.  
    CASE  
           WHEN CHANGE_TRACKING_IS_COLUMN_IN_MASK(  
                     @PhotoColumnId, CT.SYS_CHANGE_COLUMNS) = 1  
            THEN ThumbNailPhoto  
            ELSE NULL  
      END AS CT_ThumbNailPhoto,  
      CHANGE_TRACKING_IS_COLUMN_IN_MASK(  
                     @PhotoColumnId, CT.SYS_CHANGE_COLUMNS) AS  
                                   CT_ThumbNailPhoto_Changed  
     CT.SYS_CHANGE_OPERATION, CT.SYS_CHANGE_COLUMNS,  
     CT.SYS_CHANGE_CONTEXT  
FROM  
     SalesLT.Product AS P  
INNER JOIN  
     CHANGETABLE(CHANGES SalesLT.Product, @last_synchronization_version) AS CT  
ON  
     P.ProductID = CT.ProductID AND  
     CT.SYS_CHANGE_OPERATION = 'U'  
```  
  
### <a name="obtaining-consistent-and-correct-results"></a><span data-ttu-id="44a41-166">일관되고 올바른 결과 가져오기</span><span class="sxs-lookup"><span data-stu-id="44a41-166">Obtaining Consistent and Correct Results</span></span>  
 <span data-ttu-id="44a41-167">테이블에 대해 변경된 데이터를 가져오려면 여러 단계를 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-167">Obtaining the changed data for a table requires multiple steps.</span></span> <span data-ttu-id="44a41-168">특정 문제를 검토하여 처리하지 않으면 일관되지 않거나 잘못된 결과가 반환될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-168">Be aware that inconsistent or incorrect results could be returned if certain issues are not considered and handled.</span></span>  
  
 <span data-ttu-id="44a41-169">예를 들어 Sales 테이블과 SalesOrders 테이블에 적용된 변경 내용을 가져오려면 애플리케이션에서 다음 단계를 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-169">For example, to obtain the changes that were made to a Sales table and SalesOrders table, an application would perform the following steps:</span></span>  
  
1.  <span data-ttu-id="44a41-170">CHANGE_TRACKING_MIN_VALID_VERSION()을 사용하여 마지막으로 동기화된 버전의 유효성을 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-170">Validate the last synchronized version by using CHANGE_TRACKING_MIN_VALID_VERSION().</span></span>  
  
2.  <span data-ttu-id="44a41-171">CHANGE_TRACKING_CURRENT_VERSION()을 사용하여 다음에 변경 내용을 가져오는 데 사용할 수 있는 버전을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-171">Obtain the version that can be used to obtain change the next time by using CHANGE_TRACKING_CURRENT_VERSION().</span></span>  
  
3.  <span data-ttu-id="44a41-172">CHANGETABLE(CHANGES ...)을 사용하여 Sales 테이블에 대한 변경 내용을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-172">Obtain the changes for the Sales table by using CHANGETABLE(CHANGES ...).</span></span>  
  
4.  <span data-ttu-id="44a41-173">CHANGETABLE(CHANGES ...)을 사용하여 SalesOrders 테이블에 대한 변경 내용을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-173">Obtain the changes for the SalesOrders table by using CHANGETABLE(CHANGES ...).</span></span>  
  
 <span data-ttu-id="44a41-174">이전 단계로 반환되는 결과에 영향을 줄 수 있는 다음 두 프로세스가 데이터베이스에서 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-174">Two processes are occurring in the database that can affect the results that are returned by the previous steps:</span></span>  
  
-   <span data-ttu-id="44a41-175">정리 프로세스가 백그라운드에서 실행되어 지정된 보존 기간보다 오래된 변경 내용 추적 정보가 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-175">The cleanup process runs in the background and removes change tracking information that is older than the specified retention period.</span></span>  
  
     <span data-ttu-id="44a41-176">정리 프로세스는 데이터베이스에 대한 변경 내용 추적을 구성할 때 지정된 보존 기간을 사용하는 별도의 백그라운드 프로세스입니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-176">The cleanup process is a separate background process that uses the retention period that is specified when you configure change tracking for the database.</span></span> <span data-ttu-id="44a41-177">문제는 마지막 동기화 버전의 유효성을 검사한 시점과 CHANGETABLE(CHANGES...)을 호출한 시점 사이에 정리 프로세스가 발생할 수 있다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-177">The issue is that the cleanup process can occur in the time between when the last synchronization version was validated and when the call to CHANGETABLE(CHANGES...) is made.</span></span> <span data-ttu-id="44a41-178">방금 유효했던 마지막 동기화 버전이 변경 내용을 가져온 시점에 더 이상 유효하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-178">A last synchronization version that was just valid might no longer be valid by the time the changes are obtained.</span></span> <span data-ttu-id="44a41-179">따라서 잘못된 결과가 반환될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-179">Therefore, incorrect results might be returned.</span></span>  
  
-   <span data-ttu-id="44a41-180">Sales 테이블과 SalesOrders 테이블에 다음과 같이 진행 중인 DML 작업이 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-180">Ongoing DML operations are occurring in the Sales and SalesOrders tables, such as the following operations:</span></span>  
  
    -   <span data-ttu-id="44a41-181">CHANGE_TRACKING_CURRENT_VERSION()을 사용하여 다음에 사용할 버전을 가져온 후 테이블에 변경 내용이 적용될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-181">Changes can be made to the tables after the version for next time has been obtained by using CHANGE_TRACKING_CURRENT_VERSION().</span></span> <span data-ttu-id="44a41-182">따라서 예상한 것보다 많은 변경 내용이 반환될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-182">Therefore, more changes can be returned than expected.</span></span>  
  
    -   <span data-ttu-id="44a41-183">Sales 테이블에서 변경 내용을 가져오는 호출과 SalesOrders 테이블에서 변경 내용을 가져오는 호출 사이에 트랜잭션이 커밋될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-183">A transaction could commit in the time between the call to obtain changes from the Sales table and the call to obtain changes from the SalesOrders table.</span></span> <span data-ttu-id="44a41-184">따라서 SalesOrder 테이블에 대한 결과에 Sales 테이블에 없는 외래 키 값이 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-184">Therefore, the results for the SalesOrder table could have foreign key value that does not exist in the Sales table.</span></span>  
  
 <span data-ttu-id="44a41-185">앞에서 나열된 문제점을 해결하려면 스냅샷 격리를 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-185">To overcome the previously listed challenges, we recommend that you use snapshot isolation.</span></span> <span data-ttu-id="44a41-186">스냅숏 격리를 사용하면 변경 내용 정보의 일관성을 유지하고 백그라운드 정리 태스크와 관련된 경합 상태를 방지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-186">This will help to ensure consistency of change information and avoid race conditions that are related to the background cleanup task.</span></span> <span data-ttu-id="44a41-187">스냅샷 트랜잭션을 사용하지 않으면 변경 내용 추적을 사용하는 애플리케이션을 개발할 때 더 많은 노력이 필요할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-187">If you do not use snapshot transactions, developing an application that uses change tracking could require significantly more effort.</span></span>  
  
#### <a name="using-snapshot-isolation"></a><span data-ttu-id="44a41-188">스냅샷 격리 사용</span><span class="sxs-lookup"><span data-stu-id="44a41-188">Using Snapshot Isolation</span></span>  
 <span data-ttu-id="44a41-189">변경 내용 추적은 스냅샷 격리와 원활하게 작동하도록 디자인되었습니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-189">Change tracking has been designed to work well with snapshot isolation.</span></span> <span data-ttu-id="44a41-190">데이터베이스에 스냅샷 격리를 사용하도록 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-190">Snapshot isolation must be enabled for the database.</span></span> <span data-ttu-id="44a41-191">또한 변경 내용을 가져오는 데 필요한 모든 단계를 스냅샷 트랜잭션 내에 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-191">All the steps that are required to obtain changes must be included inside a snapshot transaction.</span></span> <span data-ttu-id="44a41-192">이렇게 하면 변경 내용을 가져오는 동안 데이터에 적용된 모든 변경 내용이 스냅샷 트랜잭션 내의 쿼리에 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-192">This will ensure that all changes that are made to data while obtaining changes will not be visible to the queries inside the snapshot transaction.</span></span>  
  
 <span data-ttu-id="44a41-193">스냅샷 트랜잭션 내의 데이터를 가져오려면 다음 단계를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-193">To obtain data inside a snapshot transaction, perform the following steps:</span></span>  
  
1.  <span data-ttu-id="44a41-194">트랜잭션 격리 수준을 스냅샷으로 설정하고 트랜잭션을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-194">Set the transaction isolation level to snapshot and start a transaction.</span></span>  
  
2.  <span data-ttu-id="44a41-195">CHANGE_TRACKING_MIN_VALID_VERSION()을 사용하여 마지막 동기화 버전의 유효성을 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-195">Validate the last synchronization version by using CHANGE_TRACKING_MIN_VALID_VERSION().</span></span>  
  
3.  <span data-ttu-id="44a41-196">CHANGE_TRACKING_CURRENT_VERSION()을 사용하여 다음에 사용할 버전을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-196">Obtain the version to be used the next time by using CHANGE_TRACKING_CURRENT_VERSION().</span></span>  
  
4.  <span data-ttu-id="44a41-197">CHANGETABLE(CHANGES ...)을 사용하여 Sales 테이블에 대한 변경 내용을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-197">Obtain the changes for the Sales table by using CHANGETABLE(CHANGES ...)</span></span>  
  
5.  <span data-ttu-id="44a41-198">CHANGETABLE(CHANGES ...)을 사용하여 Salesorders 테이블에 대한 변경 내용을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-198">Obtain the changes for the Salesorders table by using CHANGETABLE(CHANGES ...)</span></span>  
  
6.  <span data-ttu-id="44a41-199">트랜잭션을 커밋합니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-199">Commit the transaction.</span></span>  
  
 <span data-ttu-id="44a41-200">변경 내용을 가져오는 모든 단계가 스냅샷 트랜잭션 내에 있으므로 다음 사항에 유의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-200">Some points to remember as all steps to obtain changes are inside a snapshot transaction:</span></span>  
  
-   <span data-ttu-id="44a41-201">마지막 동기화 버전의 유효성을 검사한 후 정리가 발생하면 정리에 의해 수행된 삭제 작업이 트랜잭션 내에 표시되지 않아 CHANGETABLE(CHANGES ...)의 결과가 계속 유효합니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-201">If cleanup occurs after the last synchronization version is validated, the results from CHANGETABLE(CHANGES ...) will still be valid as the delete operations performed by cleanup will not be visible inside the transaction.</span></span>  
  
-   <span data-ttu-id="44a41-202">다음 동기화 버전을 가져온 후에 Sales 테이블 또는 SalesOrders 테이블에 적용된 변경 내용은 표시되지 않으며 CHANGETABLE(CHANGES ...)에 대한 호출은 CHANGE_TRACKING_CURRENT_VERSION()으로 반환된 버전보다 최신인 버전의 변경 내용을 반환하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-202">Any changes that are made to the Sales table or the SalesOrders table after the next synchronization version is obtained will not be visible, and the calls to CHANGETABLE(CHANGES ...) will never return changes with a version later than that returned by CHANGE_TRACKING_CURRENT_VERSION().</span></span> <span data-ttu-id="44a41-203">CHANGETABLE(CHANGES …) 호출 사이에 커밋된 트랜잭션이 표시되지 않으므로 Sales 테이블과 SalesOrders 테이블 사이의 일관성도 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-203">Consistency between the Sales table and the SalesOrders table will also be maintained, because the transactions that were committed in the time between calls to CHANGETABLE(CHANGES ...) will not be visible.</span></span>  
  
 <span data-ttu-id="44a41-204">다음 예에서는 데이터베이스에 스냅샷 격리를 사용하도록 설정하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-204">The following example shows how snapshot isolation is enabled for a database.</span></span>  
  
```sql  
-- The database must be configured to enable snapshot isolation.  
ALTER DATABASE AdventureWorksLT  
    SET ALLOW_SNAPSHOT_ISOLATION ON;  
```  
  
 <span data-ttu-id="44a41-205">스냅샷 트랜잭션은 다음과 같이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-205">A snapshot transaction is used as follows:</span></span>  
  
```sql  
SET TRANSACTION ISOLATION LEVEL SNAPSHOT;  
BEGIN TRAN  
  -- Verify that version of the previous synchronization is valid.  
  -- Obtain the version to use next time.  
  -- Obtain changes.  
COMMIT TRAN  
```  
  
 <span data-ttu-id="44a41-206">스냅샷 트랜잭션에 대한 자세한 내용은 [SET TRANSACTION ISOLATION LEVEL&#40;Transact-SQL&#41;](/sql/t-sql/statements/set-transaction-isolation-level-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="44a41-206">For more information about snapshot transactions, see [SET TRANSACTION ISOLATION LEVEL &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-transaction-isolation-level-transact-sql).</span></span>  
  
#### <a name="alternatives-to-using-snapshot-isolation"></a><span data-ttu-id="44a41-207">스냅샷 격리 사용의 대체 방법</span><span class="sxs-lookup"><span data-stu-id="44a41-207">Alternatives to Using Snapshot Isolation</span></span>  
 <span data-ttu-id="44a41-208">스냅샷 격리 사용의 대체 방법이 있지만 이 경우 모든 애플리케이션 요구 사항이 충족되려면 더 많은 작업이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-208">There are alternatives to using snapshot isolation, but they require more work to make sure all application requirements are met.</span></span> <span data-ttu-id="44a41-209">*last_synchronization_version* 의 유효성을 유지하며 변경 내용을 가져오기 전에 정리 프로세스로 인해 데이터가 제거되지 않도록 하려면 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-209">To make sure the *last_synchronization_version* is valid and data is not removed by the cleanup process before changes are obtained, do the following:</span></span>  
  
1.  <span data-ttu-id="44a41-210">CHANGETABLE()을 호출한 후 *last_synchronization_version* 을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-210">Check *last_synchronization_version* after the calls to CHANGETABLE().</span></span>  
  
2.  <span data-ttu-id="44a41-211">CHANGETABLE()을 사용하여 변경 내용을 가져오는 각 쿼리의 일부로 *last_synchronization_version* 을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-211">Check *last_synchronization_version* as part of each query to obtain changes by using CHANGETABLE().</span></span>  
  
 <span data-ttu-id="44a41-212">다음 열거에 대한 동기화 버전을 가져온 후 변경 내용이 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-212">Changes can occur after the synchronization version for the next enumeration has been obtained.</span></span> <span data-ttu-id="44a41-213">이러한 상황은 다음 두 가지 방식으로 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-213">There are two ways to handle this situation.</span></span> <span data-ttu-id="44a41-214">사용되는 옵션은 애플리케이션과 해당 애플리케이션이 각 접근 방식의 부작용을 처리할 수 있는 방식에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-214">The option that is used depends on the application and how it can handle the side-effects of each approach:</span></span>  
  
-   <span data-ttu-id="44a41-215">새 동기화 버전보다 큰 버전을 포함하는 변경 내용을 무시합니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-215">Ignore changes that have a version larger than the new synchronization version.</span></span>  
  
     <span data-ttu-id="44a41-216">이 접근 방식에서는 새 동기화 버전 이전에 만들어지거나 업데이트된 새 행 또는 업데이트된 행의 경우 건너뛴 다음 나중에 업데이트되는 부작용이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-216">This approach has the side effect that a new or updated row would be skipped if it was created or updated before the new synchronization version, but then updated afterward.</span></span> <span data-ttu-id="44a41-217">새 행의 경우 만들어진 다른 테이블에 건너뛴 행을 참조하는 행이 있으면 참조 무결성 문제가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-217">If there is a new row, a referential integrity problem might occur if there was a row in another table that was created that referenced the skipped row.</span></span> <span data-ttu-id="44a41-218">업데이트된 기존 행의 경우 해당 행을 건너뛰고 다음 번까지 동기화하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-218">If there is an updated existing row, the row will be skipped and not synchronized until the next time.</span></span>  
  
-   <span data-ttu-id="44a41-219">새 동기화 버전보다 큰 버전을 포함하는 변경 내용까지 모두 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-219">Include all changes, even those that have a version larger than the new synchronization version.</span></span>  
  
     <span data-ttu-id="44a41-220">새 동기화 버전보다 큰 버전을 포함하는 행은 다음 동기화에서 다시 얻게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-220">The rows that have a version larger than the new synchronization version will be obtained again on the next synchronization.</span></span> <span data-ttu-id="44a41-221">이를 예상하여 애플리케이션에서 처리해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-221">This must be expected and handled by the application.</span></span>  
  
 <span data-ttu-id="44a41-222">앞의 두 옵션 외에도 작업에 따라 두 옵션을 결합한 접근 방식을 시도해 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-222">In addition to the previous two options, you can devise approach that combines both options, depending on the operation.</span></span> <span data-ttu-id="44a41-223">예를 들어 행이 만들어지거나 삭제된 다음 번 동기화 버전 이후의 변경 내용은 무시하고 업데이트는 무시하지 않는 애플리케이션을 고안할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-223">For example, you might want an application for which it is best to ignore changes newer than the next synchronization version in which the row was created or deleted, but updates are not ignored.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="44a41-224">변경 내용 추적 또는 사용자 지정 추적 메커니즘을 사용할 때 애플리케이션에 적합한 접근 방식을 선택하려면 상당한 분석 작업이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-224">Choosing the approach that will work for the application when you are using change tracking (or any custom tracking mechanism), requires significant analysis.</span></span> <span data-ttu-id="44a41-225">따라서 스냅샷 격리를 사용하는 것이 훨씬 간단합니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-225">Therefore, it is much simpler to use snapshot isolation.</span></span>  
  
##  <a name="how-change-tracking-handles-changes-to-a-database"></a><a name="Handles"></a><span data-ttu-id="44a41-226">변경 내용 추적에서 데이터베이스의 변경 내용을 처리 하는 방법</span><span class="sxs-lookup"><span data-stu-id="44a41-226">How Change Tracking Handles Changes to a Database</span></span>  
 <span data-ttu-id="44a41-227">변경 내용 추적을 사용하는 일부 애플리케이션에서는 다른 데이터 저장소와 양방향 동기화를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-227">Some applications that use change tracking perform two-way synchronization with another data store.</span></span> <span data-ttu-id="44a41-228">즉, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스에 적용된 변경 내용은 다른 데이터 저장소에서 업데이트되고 다른 저장소에서 적용된 변경 내용은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스에서 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-228">That is, changes that are made in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database are updated in the other data store, and changes that are made in the other store are updated in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database.</span></span>  
  
 <span data-ttu-id="44a41-229">애플리케이션에서 다른 데이터 저장소의 변경 내용으로 로컬 데이터베이스를 업데이트하는 경우에는 다음 작업을 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-229">When an application updates the local database with changes from another data store, the application must perform the following operations:</span></span>  
  
-   <span data-ttu-id="44a41-230">충돌을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-230">Check for conflicts.</span></span>  
  
     <span data-ttu-id="44a41-231">충돌은 같은 시간에 동일한 데이터가 두 데이터 저장소 모두에서 변경된 경우 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-231">A conflict occurs when the same data is changed at the same time in both data stores.</span></span> <span data-ttu-id="44a41-232">애플리케이션은 충돌을 확인할 뿐만 아니라 충돌을 해결할 수 있는 정보를 가져올 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-232">The application must be able to check for a conflict and obtain enough information to enable the conflict to be resolved.</span></span>  
  
-   <span data-ttu-id="44a41-233">애플리케이션 컨텍스트 정보를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-233">Store application context information.</span></span>  
  
     <span data-ttu-id="44a41-234">애플리케이션은 변경 내용 추적 정보가 있는 데이터를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-234">The application stores data that has the change tracking information.</span></span> <span data-ttu-id="44a41-235">이 정보는 로컬 데이터베이스에서 변경 내용을 가져온 경우 다른 변경 내용 추적 정보와 함께 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-235">This information would be available together with other change tracking information when changes were obtained from the local database.</span></span> <span data-ttu-id="44a41-236">이 컨텍스트 정보에 대한 일반적인 예는 변경 내용의 원본인 데이터 저장소에 대한 식별자입니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-236">A common example of this contextual information is an identifier for the data store that was the source of the change.</span></span>  
  
 <span data-ttu-id="44a41-237">이전 작업을 수행하기 위해 동기화 애플리케이션에서 다음 함수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-237">To perform the previous operations, a synchronization application can use the following functions:</span></span>  
  
-   <span data-ttu-id="44a41-238">CHANGETABLE(VERSION...)</span><span class="sxs-lookup"><span data-stu-id="44a41-238">CHANGETABLE(VERSION...)</span></span>  
  
     <span data-ttu-id="44a41-239">애플리케이션에서 변경 내용을 적용할 때 이 함수를 사용하여 충돌을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-239">When an application is making changes, it can use this function to check for conflicts.</span></span> <span data-ttu-id="44a41-240">이 함수는 변경 내용이 추적된 테이블의 지정된 행에 대한 최신 변경 내용 추적 정보를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-240">The function obtains the latest change tracking information for a specified row in a change tracked table.</span></span> <span data-ttu-id="44a41-241">이 변경 내용 추적 정보에는 행이 마지막으로 변경되었을 때의 버전이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-241">The change tracking information includes the version of the row that was last changed.</span></span> <span data-ttu-id="44a41-242">애플리케이션에서는 이 정보를 사용하여 애플리케이션이 마지막으로 동기화된 후 행이 변경되었는지 여부를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-242">This information enables an application to determine whether the row was changed after the last time that the application was synchronized.</span></span>  
  
-   <span data-ttu-id="44a41-243">WITH CHANGE_TRACKING_CONTEXT</span><span class="sxs-lookup"><span data-stu-id="44a41-243">WITH CHANGE_TRACKING_CONTEXT</span></span>  
  
     <span data-ttu-id="44a41-244">애플리케이션에서 이 절을 사용하여 컨텍스트 정보를 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-244">An application can use this clause to store context data.</span></span>  
  
### <a name="checking-for-conflicts"></a><span data-ttu-id="44a41-245">충돌 확인</span><span class="sxs-lookup"><span data-stu-id="44a41-245">Checking for Conflicts</span></span>  
 <span data-ttu-id="44a41-246">양방향 동기화 시나리오에서 클라이언트 애플리케이션은 애플리케이션이 마지막으로 변경 내용을 가져온 이후 행이 업데이트되지 않았는지 여부를 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-246">In a two-way synchronization scenario, the client application must determine whether a row has not been updated since the application last obtained the changes.</span></span>  
  
 <span data-ttu-id="44a41-247">다음 예에서는 별도의 쿼리 없이 CHANGETABLE(VERSION ...) 함수를 사용하여 가장 효율적인 방법으로 충돌을 확인하는 방법을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-247">The following example shows how to use the CHANGETABLE(VERSION ...) function to check for conflicts in the most efficient way, without a separate query.</span></span> <span data-ttu-id="44a41-248">이 예에서 `CHANGETABLE(VERSION ...)` 은 `SYS_CHANGE_VERSION` 에서 지정한 행에 대한 `@product id`을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-248">In the example, `CHANGETABLE(VERSION ...)` determines the `SYS_CHANGE_VERSION` for the row specified by `@product id`.</span></span> <span data-ttu-id="44a41-249">`CHANGETABLE(CHANGES ...)` 가 동일한 정보를 가져올 수 있지만 효율성이 떨어집니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-249">`CHANGETABLE(CHANGES ...)` can obtain the same information, but that would be less efficient.</span></span> <span data-ttu-id="44a41-250">행에 대한 `SYS_CHANGE_VERSION` 값이 `@last_sync_version`값보다 크면 충돌이 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-250">If the value of `SYS_CHANGE_VERSION` for the row is larger than the value of `@last_sync_version`, there is a conflict.</span></span> <span data-ttu-id="44a41-251">충돌이 발생하는 경우 행이 업데이트되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-251">If there is a conflict, the row will not be updated.</span></span> <span data-ttu-id="44a41-252">행에 사용할 수 있는 변경 정보가 없을 수 있으므로 `ISNULL()` 검사가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-252">The `ISNULL()` check is required because there might be no change information available for the row.</span></span> <span data-ttu-id="44a41-253">변경 내용 추적을 설정한 이후 또는 변경 내용 정보를 정리한 이후 행이 업데이트되지 않은 경우 변경 내용 정보가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-253">No change information would exist if the row had not been updated since change tracking was enabled or since the change information was cleaned up.</span></span>  
  
```sql  
-- Assumption: @last_sync_version has been validated.  
  
UPDATE  
    SalesLT.Product  
SET  
    ListPrice = @new_listprice  
FROM  
    SalesLT.Product AS P  
WHERE  
    ProductID = @product_id AND  
    @last_sync_version >= ISNULL (  
        SELECT CT.SYS_CHANGE_VERSION  
        FROM CHANGETABLE(VERSION SalesLT.Product,  
                        (ProductID), (P.ProductID)) AS CT),  
        0)  
```  
  
 <span data-ttu-id="44a41-254">다음 코드는 업데이트된 행 개수를 검사하고 충돌에 대한 자세한 정보를 식별할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-254">The following code can check the updated row count and can identify more information about the conflict.</span></span>  
  
```sql  
-- If the change cannot be made, find out more information.  
IF (@@ROWCOUNT = 0)  
BEGIN  
    -- Obtain the complete change information for the row.  
    SELECT  
        CT.SYS_CHANGE_VERSION, CT.SYS_CHANGE_CREATION_VERSION,  
        CT.SYS_CHANGE_OPERATION, CT.SYS_CHANGE_COLUMNS  
    FROM  
        CHANGETABLE(CHANGES SalesLT.Product, @last_sync_version) AS CT  
    WHERE  
        CT.ProductID = @product_id;  
  
    -- Check CT.SYS_CHANGE_VERSION to verify that it really was a conflict.  
    -- Check CT.SYS_CHANGE_OPERATION to determine the type of conflict:  
    -- update-update or update-delete.  
    -- The row that is specified by @product_id might no longer exist   
    -- if it has been deleted.  
END  
```  
  
### <a name="setting-context-information"></a><span data-ttu-id="44a41-255">컨텍스트 정보 설정</span><span class="sxs-lookup"><span data-stu-id="44a41-255">Setting Context Information</span></span>  
 <span data-ttu-id="44a41-256">애플리케이션은 WITH CHANGE_TRACKING_CONTEXT 절을 사용하여 컨텍스트 정보를 변경 내용 정보와 함께 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-256">By using the WITH CHANGE_TRACKING_CONTEXT clause, an application can store context information together with the change information.</span></span> <span data-ttu-id="44a41-257">이 정보는 CHANGETABLE(CHANGES ...)에서 반환된 SYS_CHANGE_CONTEXT 열에서 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-257">This information can then be obtained from the SYS_CHANGE_CONTEXT column that is returned by CHANGETABLE(CHANGES ...).</span></span>  
  
 <span data-ttu-id="44a41-258">일반적으로 컨텍스트 정보는 변경 내용의 원본을 식별하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-258">Context information is typically used to identify the source of the changes.</span></span> <span data-ttu-id="44a41-259">변경 내용의 원본을 식별할 수 있는 경우 이 컨텍스트 정보는 데이터 저장소에서 사용되어 데이터 저장소에서 다시 동기화할 때 변경 내용을 가져오지 않도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-259">If the source of the change can be identified, that information can be used by a data store to avoid obtaining changes when it synchronizes again.</span></span>  
  
```sql  
  -- Try to update the row and check for a conflict.  
  WITH CHANGE_TRACKING_CONTEXT (@source_id)  
  UPDATE  
     SalesLT.Product  
  SET  
      ListPrice = @new_listprice  
  FROM  
      SalesLT.Product AS P  
  WHERE  
     ProductID = @product_id AND  
     @last_sync_version >= ISNULL (  
         (SELECT CT.SYS_CHANGE_VERSION FROM CHANGETABLE(VERSION SalesLT.Product,  
         (ProductID), (P.ProductID)) AS CT),  
         0)  
```  
  
### <a name="ensuring-consistent-and-correct-results"></a><span data-ttu-id="44a41-260">일관성 있고 올바른 결과 확인</span><span class="sxs-lookup"><span data-stu-id="44a41-260">Ensuring Consistent and Correct Results</span></span>  
 <span data-ttu-id="44a41-261">애플리케이션은 @last_sync_version 값의 유효성을 검사할 때 정리 프로세스를 고려해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-261">An application must consider the cleanup process when it validates the value of @last_sync_version.</span></span> <span data-ttu-id="44a41-262">그 이유는 CHANGE_TRACKING_MIN_VALID_VERSION()이 호출된 이후 업데이트가 적용되기 전에 데이터가 제거되었을 수도 있기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-262">This is because data could have been removed after CHANGE_TRACKING_MIN_VALID_VERSION() was called, but before the update was made.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="44a41-263">스냅샷 격리를 사용하고 스냅샷 트랜잭션 내에서 변경하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-263">We recommend that you use snapshot isolation and make the changes within a snapshot transaction.</span></span>  
  
```sql  
-- Prerequisite is to ensure ALLOW_SNAPSHOT_ISOLATION is ON for the database.  
  
SET TRANSACTION ISOLATION LEVEL SNAPSHOT;  
BEGIN TRAN  
    -- Verify that last_sync_version is valid.  
    IF (@last_sync_version <  
CHANGE_TRACKING_MIN_VALID_VERSION(OBJECT_ID('SalesLT.Product')))  
    BEGIN  
       RAISERROR (N'Last_sync_version too old', 16, -1);  
    END  
    ELSE  
    BEGIN  
        -- Try to update the row.  
        -- Check @@ROWCOUNT and check for a conflict.  
    END  
COMMIT TRAN  
```  
  
> [!NOTE]  
>  <span data-ttu-id="44a41-264">스냅샷 트랜잭션 내에서 업데이트되는 행이 스냅샷 트랜잭션이 시작된 후 다른 트랜잭션에서 업데이트되었을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-264">There is a possibility that the row being updated within the snapshot transaction could have been updated in another transaction after the snapshot transaction was started.</span></span> <span data-ttu-id="44a41-265">이런 경우에 스냅샷 격리 업데이트 충돌이 발생하고 해당 트랜잭션이 종료됩니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-265">In this case, a snapshot isolation update conflict will occur and lead to the transaction being terminated.</span></span> <span data-ttu-id="44a41-266">이러한 경우가 발생하면 업데이트를 다시 시도하세요.</span><span class="sxs-lookup"><span data-stu-id="44a41-266">If this happens, retry the update.</span></span> <span data-ttu-id="44a41-267">그러면 변경 내용 추적 충돌이 검색되고 행이 변경되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-267">This will then lead to a change tracking conflict being detected and no rows being changed.</span></span>  
  
##  <a name="change-tracking-and-data-restore"></a><a name="DataRestore"></a><span data-ttu-id="44a41-268">변경 내용 추적 및 데이터 복원</span><span class="sxs-lookup"><span data-stu-id="44a41-268">Change Tracking and Data Restore</span></span>  
 <span data-ttu-id="44a41-269">동기화가 필요한 애플리케이션에서는 변경 내용 추적이 설정된 데이터베이스를 이전 버전의 데이터로 되돌리는 경우를 고려해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-269">Applications that require synchronization must consider the case in which a database that has change tracking enabled reverts to an earlier version of the data.</span></span> <span data-ttu-id="44a41-270">이런 경우는 백업에서 데이터베이스가 복원된 후, 비동기 데이터베이스 미러링에 장애 조치가 있는 경우 또는 로그 전달을 사용할 때 실패한 경우에 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-270">This can occur after a database is restored from a backup, when there is a failover to an asynchronous database mirror, or when there is a failure when using log shipping.</span></span> <span data-ttu-id="44a41-271">다음 시나리오에서는 이러한 문제를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-271">The following scenario illustrates the issue:</span></span>  
  
1.  <span data-ttu-id="44a41-272">테이블 T1는 변경 내용이 추적되고 테이블의 유효한 최소 버전 50입니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-272">Table T1 is change tracked, and the minimum valid version for table is 50.</span></span>  
  
2.  <span data-ttu-id="44a41-273">클라이언트 애플리케이션은 버전 100에서 데이터를 동기화하고 버전 50과 100 사이의 모든 변경 사항에 대한 정보를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-273">A client application synchronizes data at version 100 and obtains information about all changes between versions 50 and 100.</span></span>  
  
3.  <span data-ttu-id="44a41-274">버전 100 이후 추가 변경 내용이 테이블 T1에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-274">Additional changes are made to table T1 after version 100.</span></span>  
  
4.  <span data-ttu-id="44a41-275">버전 120에서 오류가 발생하고 데이터베이스 관리자는 데이터베이스를 복원하지만 데이터 손실이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-275">At version 120, there is a failure and the database administrator restores the database with data loss.</span></span> <span data-ttu-id="44a41-276">복원 작업 후 테이블에는 버전 70까지 데이터가 포함되고 동기화된 최소 버전은 여전히 50입니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-276">After the restore operation, the table contains data up through version 70, and the minimum synchronized version is still 50.</span></span>  
  
     <span data-ttu-id="44a41-277">즉, 동기화된 데이터 저장소에는 주 데이터 저장소에 더 이상 존재하지 않는 데이터가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-277">This means that the synchronized data store has data that no longer exists in the primary data store.</span></span>  
  
5.  <span data-ttu-id="44a41-278">T1은 여러 번 업데이트되어서</span><span class="sxs-lookup"><span data-stu-id="44a41-278">T1 is updated many times.</span></span> <span data-ttu-id="44a41-279">현재 버전은 130입니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-279">This brings the current version to 130.</span></span>  
  
6.  <span data-ttu-id="44a41-280">클라이언트 애플리케이션이 다시 동기화되어 마지막으로 동기화된 버전인 100을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-280">The client application synchronizes again and supplies a last-synchronized version of 100.</span></span> <span data-ttu-id="44a41-281">100은 50보다 크므로 클라이언트는 이 번호의 유효성을 검사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-281">The client validates this number successfully because 100 is greater than 50.</span></span>  
  
     <span data-ttu-id="44a41-282">클라이언트는 버전 100과 130 사이의 변경 내용을 가져옵니다</span><span class="sxs-lookup"><span data-stu-id="44a41-282">The client obtains changes between version 100 and 130.</span></span> <span data-ttu-id="44a41-283">이 지점에서 클라이언트는 이전과 다른 70과 100 사이의 변경 내용을 인식하지 못합니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-283">At this point, the client is not aware that the changes between 70 and 100 are not the same as before.</span></span> <span data-ttu-id="44a41-284">클라이언트와 서버의 데이터는 동기화되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-284">The data on the client and server are not synchronized.</span></span>  
  
 <span data-ttu-id="44a41-285">데이터베이스가 버전 100 이후 지점으로 복구되면 동기화에 아무 문제가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-285">Note that if the database was recovered to a point after version 100, there would be no problems with synchronization.</span></span> <span data-ttu-id="44a41-286">클라이언트와 서버는 다음 동기화 간격 동안 데이터를 올바르게 동기화합니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-286">The client and server would synchronize data correctly during the next synchronization interval.</span></span>  
  
 <span data-ttu-id="44a41-287">변경 내용 추적은 데이터 손실의 복구를 지원하지 않지만</span><span class="sxs-lookup"><span data-stu-id="44a41-287">Change tracking does not provide support for recovering from the loss of data.</span></span> <span data-ttu-id="44a41-288">이러한 세 가지 유형의 동기화 문제를 감지할 수 있는 다음 두 가지 옵션을 가지고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-288">However, there are two options for detecting these types of synchronization issues:</span></span>  
  
-   <span data-ttu-id="44a41-289">데이터베이스 버전 ID를 서버에 저장하고 데이터베이스가 복구될 때마다 이 값을 업데이트합니다. 그렇지 않으면 데이터가 손실됩니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-289">Store a database version ID on the server, and update this value whenever a database is recovered or otherwise loses data.</span></span> <span data-ttu-id="44a41-290">데이터를 동기화할 때 각 클라이언트 애플리케이션은 ID를 저장하고 각 클라이언트는 이 ID의 유효성을 검사해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-290">Each client application would store the ID, and each client would have to validate this ID when it synchronizes data.</span></span> <span data-ttu-id="44a41-291">데이터 손실이 발생하면 ID가 일치하지 않고 클라이언트가 다시 초기화됩니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-291">If data loss occurs, the IDs will not match and the clients would reinitialize.</span></span> <span data-ttu-id="44a41-292">한 가지 단점은 데이터 손실이 마지막으로 동기화된 경계에 교차되지 않은 경우에 클라이언트가 불필요하게 다시 초기화해야 할 수도 있다는 점입니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-292">One drawback is if the data loss had not crossed the last synchronized boundary, the client might do unnecessary reinitialization.</span></span>  
  
-   <span data-ttu-id="44a41-293">클라이언트가 변경 내용에 대해 쿼리할 때 서버의 각 클라이언트에 대한 마지막 동기화 버전을 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-293">When a client queries for changes, record the last synchronization version number for each client on the server.</span></span> <span data-ttu-id="44a41-294">데이터에 문제가 있으면 마지막으로 동기화된 버전 번호가 일치하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-294">If there is a problem with the data, the last synchronized version numbers would not match.</span></span> <span data-ttu-id="44a41-295">이것은 다시 동기화해야 한다는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="44a41-295">This indicates that a reinitialization is required.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44a41-296">참고 항목</span><span class="sxs-lookup"><span data-stu-id="44a41-296">See Also</span></span>  
 <span data-ttu-id="44a41-297">[데이터 변경 내용 추적&#40;SQL Server&#41;](../track-changes/track-data-changes-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="44a41-297">[Track Data Changes &#40;SQL Server&#41;](../track-changes/track-data-changes-sql-server.md) </span></span>  
 <span data-ttu-id="44a41-298">[변경 내용 추적 정보&#40;SQL Server&#41;](../track-changes/about-change-tracking-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="44a41-298">[About Change Tracking &#40;SQL Server&#41;](../track-changes/about-change-tracking-sql-server.md) </span></span>  
 <span data-ttu-id="44a41-299">[변경 내용 추적 &#40;SQL Server 관리&#41;](../track-changes/manage-change-tracking-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="44a41-299">[Manage Change Tracking &#40;SQL Server&#41;](../track-changes/manage-change-tracking-sql-server.md) </span></span>  
 <span data-ttu-id="44a41-300">[변경 내용 추적 &#40;SQL Server 사용 및 사용 안 함&#41;](../track-changes/enable-and-disable-change-tracking-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="44a41-300">[Enable and Disable Change Tracking &#40;SQL Server&#41;](../track-changes/enable-and-disable-change-tracking-sql-server.md) </span></span>  
 <span data-ttu-id="44a41-301">[CHANGETABLE &#40;Transact-sql&#41;](/sql/relational-databases/system-functions/changetable-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="44a41-301">[CHANGETABLE &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/changetable-transact-sql) </span></span>  
 <span data-ttu-id="44a41-302">[Transact-sql&#41;CHANGE_TRACKING_MIN_VALID_VERSION &#40;](/sql/relational-databases/system-functions/change-tracking-min-valid-version-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="44a41-302">[CHANGE_TRACKING_MIN_VALID_VERSION &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/change-tracking-min-valid-version-transact-sql) </span></span>  
 <span data-ttu-id="44a41-303">[Transact-sql&#41;CHANGE_TRACKING_CURRENT_VERSION &#40;](/sql/relational-databases/system-functions/change-tracking-current-version-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="44a41-303">[CHANGE_TRACKING_CURRENT_VERSION &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/change-tracking-current-version-transact-sql) </span></span>  
 [<span data-ttu-id="44a41-304">WITH CHANGE_TRACKING_CONTEXT&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="44a41-304">WITH CHANGE_TRACKING_CONTEXT &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-functions/with-change-tracking-context-transact-sql)  
  
  
