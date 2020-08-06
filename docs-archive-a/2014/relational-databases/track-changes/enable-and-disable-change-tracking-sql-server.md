---
title: 변경 내용 추적 설정 및 해제(SQL Server) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- change tracking [SQL Server], disabling
- data changes [SQL Server]
- change tracking [SQL Server], enabling
- tracking data changes [SQL Server]
- change tracking [SQL Server], configuring
- data [SQL Server], changing
ms.assetid: 1c92ec7e-ae53-4498-8bfd-c66a42a24d54
author: rothja
ms.author: jroth
ms.openlocfilehash: 402c63ae03df14e3a725fbc440575f5233d502f9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649950"
---
# <a name="enable-and-disable-change-tracking-sql-server"></a><span data-ttu-id="3b001-102">변경 내용 추적 설정 및 해제(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="3b001-102">Enable and Disable Change Tracking (SQL Server)</span></span>
  <span data-ttu-id="3b001-103">이 항목에서는 데이터베이스 및 테이블에 변경 내용 추적을 사용하도록 설정하거나 사용하지 않도록 설정하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="3b001-103">This topic describes how to enable and disable change tracking for a database and a table.</span></span>  
  
## <a name="enable-change-tracking-for-a-database"></a><span data-ttu-id="3b001-104">데이터베이스에 변경 내용 추적을 사용하도록 설정</span><span class="sxs-lookup"><span data-stu-id="3b001-104">Enable Change Tracking for a Database</span></span>  
 <span data-ttu-id="3b001-105">변경 내용 추적을 사용하기 전에 데이터베이스 수준에서 변경 내용 추적을 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3b001-105">Before you can use change tracking, you must enable change tracking at the database level.</span></span> <span data-ttu-id="3b001-106">다음 예에서는 [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-set-options)를 사용하여 변경 내용 추적을 사용하도록 설정하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="3b001-106">The following example shows how to enable change tracking by using [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-set-options).</span></span>  
  
```sql  
ALTER DATABASE AdventureWorks2012  
SET CHANGE_TRACKING = ON  
(CHANGE_RETENTION = 2 DAYS, AUTO_CLEANUP = ON)  
```  
  
 <span data-ttu-id="3b001-107">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 데이터베이스 속성&#40;변경 내용 추적 페이지&#41; [Database Properties &#40;ChangeTracking Page&#41;](../databases/database-properties-changetracking-page.md) 에 변경 내용을 설정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3b001-107">You can also enable change tracking in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] by using the [Database Properties &#40;ChangeTracking Page&#41;](../databases/database-properties-changetracking-page.md) dialog box.</span></span>  
  
 <span data-ttu-id="3b001-108">변경 내용 추적을 설정할 때 CHANGE_RETENTION 및 AUTO_CLEANUP 옵션을 지정할 수 있으며, 변경 내용 추적을 설정한 후 언제든지 이 값을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3b001-108">You can specify the CHANGE_RETENTION and AUTO_CLEANUP options when you enable change tracking, and you can change the values at any time after change tracking is enabled.</span></span>  
  
 <span data-ttu-id="3b001-109">변경 내용 보존 기간 값은 변경 내용 추적 정보가 유지되는 기간을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3b001-109">The change retention value specifies the time period for which change tracking information is kept.</span></span> <span data-ttu-id="3b001-110">이 기간보다 오래된 변경 내용 추적 정보는 정기적으로 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="3b001-110">Change tracking information that is older than this time period is removed periodically.</span></span> <span data-ttu-id="3b001-111">이 값을 설정할 때 애플리케이션이 이 데이터베이스에 있는 테이블을 동기화하는 빈도를 고려해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3b001-111">When you are setting this value, you should consider how often applications will synchronize with the tables in the database.</span></span> <span data-ttu-id="3b001-112">지정한 보존 기간은 최대 동기화 간격 이상이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3b001-112">The specified retention period must be at least as long as the maximum time period between synchronizations.</span></span> <span data-ttu-id="3b001-113">애플리케이션이 좀 더 긴 간격으로 변경 내용을 가져오면 일부 변경 내용 정보가 제거되지 않았을 수도 있으므로 반환되는 결과가 정확하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3b001-113">If an application obtains changes at longer intervals, the results that are returned might be incorrect because some of the change information has probably been removed.</span></span> <span data-ttu-id="3b001-114">잘못된 결과가 생성되는 것을 방지하기 위해 애플리케이션에서는 CHANGE_TRACKING_MIN_VALID_VERSION 시스템 함수를 사용하여 동기화 간의 간격이 너무 긴지 여부를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3b001-114">To avoid obtaining incorrect results, an application can use the CHANGE_TRACKING_MIN_VALID_VERSION system function to determine whether the interval between synchronizations has been too long.</span></span>  
  
 <span data-ttu-id="3b001-115">AUTO_CLEANUP 옵션을 사용하여 오래된 변경 내용 추적 정보를 제거하는 정리 태스크를 설정하거나 해제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3b001-115">You can use the AUTO_CLEANUP option to enable or disable the cleanup task that removes old change tracking information.</span></span> <span data-ttu-id="3b001-116">이 설정은 애플리케이션이 동기화되지 않는 일시적인 문제가 발생하여 이 문제가 해결될 때까지 보존 기간보다 오래된 변경 내용 추적 정보를 제거하는 프로세스를 일시 중지해야 하는 경우에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="3b001-116">This can be useful when there is a temporary problem that prevents applications from synchronizing and the process for removing change tracking information older than the retention period must be paused until the problem is resolved.</span></span>  
  
 <span data-ttu-id="3b001-117">변경 내용 추적을 사용하는 데이터베이스의 경우 다음 사항에 주의하십시오.</span><span class="sxs-lookup"><span data-stu-id="3b001-117">For any database that uses change tracking, be aware of the following:</span></span>  
  
-   <span data-ttu-id="3b001-118">변경 내용 추적을 사용하려면 데이터베이스 호환성 수준이 90 이상으로 설정되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3b001-118">To use change tracking, the database compatibility level must be set to 90 or greater.</span></span> <span data-ttu-id="3b001-119">데이터베이스 호환성 수준이 90 미만인 경우에도 변경 내용 추적을 구성할 수 있지만</span><span class="sxs-lookup"><span data-stu-id="3b001-119">If a database has a compatibility level of less than 90, you can configure change tracking.</span></span> <span data-ttu-id="3b001-120">변경 내용 추적 정보를 얻기 위해 사용되는 CHANGETABLE 함수에서 오류를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="3b001-120">However, the CHANGETABLE function, which is used to obtain change tracking information, will return an error.</span></span>  
  
-   <span data-ttu-id="3b001-121">스냅샷 격리를 사용하는 것은 모든 변경 내용 추적 정보가 일관되도록 보장하는 가장 쉬운 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="3b001-121">Using snapshot isolation is the easiest way for you to help ensure that all change tracking information is consistent.</span></span> <span data-ttu-id="3b001-122">이러한 이유로 데이터베이스에 대해 스냅샷 격리를 ON으로 설정하는 것이 가장 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="3b001-122">For this reason, we strongly recommend that snapshot isolation be set to ON for the database.</span></span> <span data-ttu-id="3b001-123">자세한 내용은 [변경 내용 추적 사용&#40;SQL Server&#41;](work-with-change-tracking-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3b001-123">For more information, see [Work with Change Tracking &#40;SQL Server&#41;](work-with-change-tracking-sql-server.md).</span></span>  
  
## <a name="enable-change-tracking-for-a-table"></a><span data-ttu-id="3b001-124">테이블에 변경 내용 추적을 사용하도록 설정</span><span class="sxs-lookup"><span data-stu-id="3b001-124">Enable Change Tracking for a Table</span></span>  
 <span data-ttu-id="3b001-125">추적하려는 테이블마다 변경 내용 추적을 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3b001-125">Change tracking must be enabled for each table that you want tracked.</span></span> <span data-ttu-id="3b001-126">변경 내용 추적이 설정되면 DML 작업에 의해 영향을 받는 테이블의 모든 행에 대해 변경 내용 추적 정보가 유지 관리됩니다.</span><span class="sxs-lookup"><span data-stu-id="3b001-126">When change tracking is enabled, change tracking information is maintained for all rows in the table that are affected by a DML operation.</span></span>  
  
 <span data-ttu-id="3b001-127">다음 예에서는 [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql)을 사용하여 테이블에 변경 내용 추적을 사용하도록 설정하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="3b001-127">The following example shows how to enable change tracking for a table by using [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql).</span></span>  
  
```sql  
ALTER TABLE Person.Contact  
ENABLE CHANGE_TRACKING  
WITH (TRACK_COLUMNS_UPDATED = ON)  
```  
  
 <span data-ttu-id="3b001-128">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 데이터베이스 속성&#40;변경 내용 추적 페이지&#41; [Database Properties &#40;ChangeTracking Page&#41;](../databases/database-properties-changetracking-page.md) 에 변경 내용을 설정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3b001-128">You can also enable change tracking for a table in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] by using the [Database Properties &#40;ChangeTracking Page&#41;](../databases/database-properties-changetracking-page.md) dialog box.</span></span>  
  
 <span data-ttu-id="3b001-129">TRACK_COLUMNS_UPDATED 옵션이 ON으로 설정되면 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 에서는 내부 변경 내용 추적 테이블에 업데이트된 열에 대한 추가 정보를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="3b001-129">When the TRACK_COLUMNS_UPDATED option is set to ON, the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] stores extra information about which columns were updated to the internal change tracking table.</span></span> <span data-ttu-id="3b001-130">열 추적을 사용하면 애플리케이션이 업데이트된 열만 동기화하도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3b001-130">Column tracking can enable an application to synchronize only those columns that were updated.</span></span> <span data-ttu-id="3b001-131">이로 인해 효율성과 성능이 향상될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3b001-131">This can improve efficiency and performance.</span></span> <span data-ttu-id="3b001-132">그러나 열 추적 정보 유지 관리로 인해 스토리지 오버헤드가 추가되기 때문에 이 옵션은 기본적으로 OFF로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="3b001-132">However, because maintaining column tracking information adds some extra storage overhead, this option is set to OFF by default.</span></span>  
  
## <a name="disable-change-tracking-for-a-database-or-table"></a><span data-ttu-id="3b001-133">데이터베이스 또는 테이블에 변경 내용 추적을 사용하지 않도록 설정</span><span class="sxs-lookup"><span data-stu-id="3b001-133">Disable Change Tracking for a Database or Table</span></span>  
 <span data-ttu-id="3b001-134">우선 변경 내용 추적이 설정된 모든 테이블에 대해 변경 내용 추적을 해제해야 해당 데이터베이스에 대한 변경 내용 추적을 OFF로 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3b001-134">Change tracking must first be disabled for all change-tracked tables before change tracking can be set to OFF for the database.</span></span> <span data-ttu-id="3b001-135">데이터베이스에서 변경 내용 추적이 설정된 테이블을 확인하려면 [sys.change_tracking_tables](/sql/relational-databases/system-catalog-views/change-tracking-catalog-views-sys-change-tracking-tables) 카탈로그 뷰를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="3b001-135">To determine the tables that have change tracking enabled for a database, use the [sys.change_tracking_tables](/sql/relational-databases/system-catalog-views/change-tracking-catalog-views-sys-change-tracking-tables) catalog view.</span></span>  
  
 <span data-ttu-id="3b001-136">데이터베이스의 테이블에 변경 내용 추적이 설정되어 있지 않으면 해당 데이터베이스에 대해 변경 내용 추적을 해제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3b001-136">When no tables in a database track changes, you can disable change tracking for the database.</span></span> <span data-ttu-id="3b001-137">다음 예에서는 [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-set-options)를 사용하여 데이터베이스에 변경 내용 추적을 사용하지 않도록 설정하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="3b001-137">The following example shows how to disable change tracking for a database by using [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-set-options).</span></span>  
  
```sql  
ALTER DATABASE AdventureWorks2012  
SET CHANGE_TRACKING = OFF  
```  
  
 <span data-ttu-id="3b001-138">다음 예에서는 [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql)을 사용하여 테이블에 변경 내용 추적을 사용하지 않도록 설정하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="3b001-138">The following example shows how to disable change tracking for a table by using [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql).</span></span>  
  
```sql  
ALTER TABLE Person.Contact  
DISABLE CHANGE_TRACKING;  
```  
  
## <a name="see-also"></a><span data-ttu-id="3b001-139">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3b001-139">See Also</span></span>  
 <span data-ttu-id="3b001-140">[데이터베이스 속성&#40;변경 내용 추적 페이지&#41;](../databases/database-properties-changetracking-page.md) </span><span class="sxs-lookup"><span data-stu-id="3b001-140">[Database Properties &#40;ChangeTracking Page&#41;](../databases/database-properties-changetracking-page.md) </span></span>  
 <span data-ttu-id="3b001-141">[ALTER DATABASE SET 옵션&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options) </span><span class="sxs-lookup"><span data-stu-id="3b001-141">[ALTER DATABASE SET Options &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options) </span></span>  
 <span data-ttu-id="3b001-142">[sys.change_tracking_databases&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/change-tracking-catalog-views-sys-change-tracking-databases) </span><span class="sxs-lookup"><span data-stu-id="3b001-142">[sys.change_tracking_databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/change-tracking-catalog-views-sys-change-tracking-databases) </span></span>  
 <span data-ttu-id="3b001-143">[sys.change_tracking_tables&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/change-tracking-catalog-views-sys-change-tracking-tables) </span><span class="sxs-lookup"><span data-stu-id="3b001-143">[sys.change_tracking_tables &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/change-tracking-catalog-views-sys-change-tracking-tables) </span></span>  
 <span data-ttu-id="3b001-144">[데이터 변경 내용 추적&#40;SQL Server&#41;](track-data-changes-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="3b001-144">[Track Data Changes &#40;SQL Server&#41;](track-data-changes-sql-server.md) </span></span>  
 <span data-ttu-id="3b001-145">[변경 내용 추적 정보&#40;SQL Server&#41;](../track-changes/about-change-tracking-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="3b001-145">[About Change Tracking &#40;SQL Server&#41;](../track-changes/about-change-tracking-sql-server.md) </span></span>  
 <span data-ttu-id="3b001-146">[변경 데이터 작업&#40;SQL Server&#41;](work-with-change-data-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="3b001-146">[Work with Change Data &#40;SQL Server&#41;](work-with-change-data-sql-server.md) </span></span>  
 [<span data-ttu-id="3b001-147">변경 내용 추적 관리&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="3b001-147">Manage Change Tracking &#40;SQL Server&#41;</span></span>](manage-change-tracking-sql-server.md)  
  
  
