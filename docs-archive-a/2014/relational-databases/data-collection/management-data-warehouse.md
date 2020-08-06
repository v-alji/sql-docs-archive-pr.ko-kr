---
title: 관리 데이터 웨어하우스 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- data collector [SQL Server], management data warehouse
- data warehouse
- management data warehouse
ms.assetid: 9874a8b2-7ccd-494a-944c-ad33b30b5499
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 96eb26c3e273832aead4aa0421304df17dc5b8ff
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649099"
---
# <a name="management-data-warehouse"></a><span data-ttu-id="91601-102">관리 데이터 웨어하우스</span><span class="sxs-lookup"><span data-stu-id="91601-102">Management Data Warehouse</span></span>
  <span data-ttu-id="91601-103">관리 데이터 웨어하우스는 데이터 컬렉션 대상인 서버에서 수집되는 데이터를 포함하는 관계형 데이터베이스입니다.</span><span class="sxs-lookup"><span data-stu-id="91601-103">The management data warehouse is a relational database that contains the data that is collected from a server that is a data collection target.</span></span> <span data-ttu-id="91601-104">이 데이터를 사용하여 시스템 데이터 컬렉션 집합의 보고서를 생성하고 사용자 지정 보고서를 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="91601-104">This data is used to generate the reports for the System Data collection sets, and can also be used to create custom reports.</span></span>  
  
 <span data-ttu-id="91601-105">데이터 수집기 인프라는 데이터베이스 관리자가 정의하는 보존 정책을 구현하기 위해 필요한 작업 및 유지 관리 계획을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="91601-105">The data collector infrastructure defines the jobs and maintenance plans that are needed to implement the retention policies defined by the database administrator.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="91601-106">이 릴리스의 데이터 수집기에서는 로깅을 최소화하기 위해 단순 복구 모델을 사용하여 관리 데이터 웨어하우스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="91601-106">For this release of the data collector, the management data warehouse is created using the Simple recovery model, to minimize logging.</span></span> <span data-ttu-id="91601-107">사용자는 해당 조직에 맞는 복구 모델을 구현해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="91601-107">You should implement the appropriate recovery model for your organization.</span></span>  
  
## <a name="deploying-and-using-the-data-warehouse"></a><span data-ttu-id="91601-108">데이터 웨어하우스 배포 및 사용</span><span class="sxs-lookup"><span data-stu-id="91601-108">Deploying and Using the Data Warehouse</span></span>  
 <span data-ttu-id="91601-109">데이터 수집기가 실행되는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 의 동일한 인스턴스에 관리 데이터 웨어하우스를 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="91601-109">You can install the management data warehouse on the same instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that runs the data collector.</span></span> <span data-ttu-id="91601-110">그러나 모니터링 중인 서버에서 서버 리소스 또는 성능이 문제가 될 경우 다른 컴퓨터에 관리 데이터 웨어하우스를 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="91601-110">However, if server resources or performance is an issue on the server being monitored, you can install the management data warehouse on a different computer.</span></span>  
  
 <span data-ttu-id="91601-111">미리 정의된 시스템 컬렉션 집합에 필요한 스키마와 이들의 개체는 관리 데이터 웨어하우스를 만들 때 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="91601-111">The required schemas and their objects for the predefined system collection sets are created when you create the management data warehouse.</span></span> <span data-ttu-id="91601-112">만들어진 스키마는 핵심이며 스냅샷입니다. 세 번째 스키마인 custom_snapshots는 일반 T-SQL 쿼리 수집기 유형을 사용하는 컬렉션 항목을 포함하는 사용자 정의 컬렉션 집합이 만들어질 때 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="91601-112">The schemas that are created are core and snapshots.A third schema, custom_snapshots, is created when user-defined collection sets are created that include collection items that use the Generic T-SQL Query collector type.</span></span>  
  
###### <a name="core-schema"></a><span data-ttu-id="91601-113">core 스키마</span><span class="sxs-lookup"><span data-stu-id="91601-113">Core schema</span></span>  
 <span data-ttu-id="91601-114">core 스키마는 수집된 데이터를 구성하고 식별하는 데 사용되는 테이블, 저장 프로시저 및 뷰에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="91601-114">The core schema describes the tables, stored procedures, and views that are used to organize and to identify collected data.</span></span> <span data-ttu-id="91601-115">이러한 테이블은 개별 수집기 유형에 대해 생성되는 모든 데이터 테이블에서 공유됩니다.</span><span class="sxs-lookup"><span data-stu-id="91601-115">These tables are shared among all the data tables created for individual collector types.</span></span> <span data-ttu-id="91601-116">이 스키마는 잠겨 있으며 관리 데이터 웨어하우스 데이터베이스의 소유자만 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="91601-116">This schema is locked and can only be modified by the owner of the management data warehouse database.</span></span> <span data-ttu-id="91601-117">이 스키마의 테이블 이름에는 "core"가 접두사로 붙습니다.</span><span class="sxs-lookup"><span data-stu-id="91601-117">The names of the tables in this schema are prefixed by "core".</span></span>  
  
 <span data-ttu-id="91601-118">다음 표에서는 core 스키마의 데이터베이스 테이블에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="91601-118">The following table describes the database tables in the core schema.</span></span> <span data-ttu-id="91601-119">이러한 데이터베이스 테이블에서는 데이터 수집기를 사용하여 데이터가 있었던 위치, 데이터를 삽입한 사용자 및 데이터가 데이터 웨어하우스에 업로드된 시간을 추적할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="91601-119">These database tables enable the data collector to track where the data came from, who inserted it, and when it was uploaded to the data warehouse.</span></span>  
  
|<span data-ttu-id="91601-120">테이블 이름</span><span class="sxs-lookup"><span data-stu-id="91601-120">Table name</span></span>|<span data-ttu-id="91601-121">Description</span><span class="sxs-lookup"><span data-stu-id="91601-121">Description</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="91601-122">core.performance_counter_report_group_items</span><span class="sxs-lookup"><span data-stu-id="91601-122">core.performance_counter_report_group_items</span></span>|<span data-ttu-id="91601-123">관리 데이터 웨어하우스 보고서에서 성능 카운터를 그룹화하고 집계하는 방법에 대한 정보를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="91601-123">Stores information about how the management data warehouse reports should group and aggregate performance counters.</span></span>|  
|<span data-ttu-id="91601-124">core.snapshots_internal</span><span class="sxs-lookup"><span data-stu-id="91601-124">core.snapshots_internal</span></span>|<span data-ttu-id="91601-125">새로운 각 스냅샷을 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="91601-125">Identifies each new snapshot.</span></span> <span data-ttu-id="91601-126">업로드 패키지가 새 일괄 처리 데이터를 업로드하기 시작할 때마다 새 행이 이 테이블에 삽입됩니다.</span><span class="sxs-lookup"><span data-stu-id="91601-126">A new row is inserted into this table whenever an upload package starts uploading a new batch of data.</span></span>|  
|<span data-ttu-id="91601-127">core.snapshot_timetable_internal</span><span class="sxs-lookup"><span data-stu-id="91601-127">core.snapshot_timetable_internal</span></span>|<span data-ttu-id="91601-128">스냅샷 시간에 대한 정보를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="91601-128">Stores information about the snapshot times.</span></span> <span data-ttu-id="91601-129">많은 스냅샷이 거의 동시에 발생할 수 있으므로 스냅샷 시간은 별도의 테이블에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="91601-129">The snapshot time is stored in a separate table because many snapshots can happen at nearly the same time.</span></span>|  
|<span data-ttu-id="91601-130">core.source.info_internal</span><span class="sxs-lookup"><span data-stu-id="91601-130">core.source.info_internal</span></span>|<span data-ttu-id="91601-131">이 테이블은 데이터 원본에 대한 정보를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="91601-131">This table stores information about the data source.</span></span> <span data-ttu-id="91601-132">새 컬렉션 집합이 데이터를 데이터 웨어하우스에 업로드하기 시작할 때마다 이 테이블이 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="91601-132">This table is updated whenever a new collection set starts uploading data to the data warehouse.</span></span>|  
|<span data-ttu-id="91601-133">core.supported_collector_types_internal</span><span class="sxs-lookup"><span data-stu-id="91601-133">core.supported_collector_types_internal</span></span>|<span data-ttu-id="91601-134">데이터를 관리 데이터 웨어하우스에 업로드할 수 있는 등록된 수집기 유형의 ID를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="91601-134">Contains the IDs of registered collector types that can upload data to the management data warehouse.</span></span> <span data-ttu-id="91601-135">이 테이블은 웨어하우스의 스키마가 새 수집기 유형을 지원하도록 업데이트되는 경우에만 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="91601-135">This table is only updated when the schema of the warehouse is updated to support a new collector type.</span></span> <span data-ttu-id="91601-136">관리 데이터 웨어하우스가 생성되면 데이터 수집기에서 제공하는 수집기 유형의 ID로 이 테이블이 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="91601-136">When the management data warehouse is created, this table is populated with the IDs of the collector types provided by the data collector.</span></span>|  
|<span data-ttu-id="91601-137">core.wait_categories</span><span class="sxs-lookup"><span data-stu-id="91601-137">core.wait_categories</span></span>|<span data-ttu-id="91601-138">wait_type 특징에 따라 대기 유형을 그룹핑하는 데 사용되는 범주를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="91601-138">Contains the categories used to group wait types according to wait_type characteristic.</span></span>|  
|<span data-ttu-id="91601-139">core.wait_types</span><span class="sxs-lookup"><span data-stu-id="91601-139">core.wait_types</span></span>|<span data-ttu-id="91601-140">데이터 수집기에 의해 인식되는 대기 유형을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="91601-140">Contains the wait types recognized by the data collector.</span></span>|  
|<span data-ttu-id="91601-141">core.purge_info_internal</span><span class="sxs-lookup"><span data-stu-id="91601-141">core.purge_info_internal</span></span>|<span data-ttu-id="91601-142">관리 데이터 웨어하우스로부터 데이터 제거를 중지하기 위해 수행한 요청을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="91601-142">Indicates that a request has been made to stop the removal of data from the management data warehouse.</span></span>|  
  
 <span data-ttu-id="91601-143">위의 테이블이 수집기 유형 테이블에 정보를 저장하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="91601-143">The preceding tables are used with collector type tables to store information.</span></span> <span data-ttu-id="91601-144">예를 들어 일반 SQL 추적 수집기 유형은 다음 테이블을 사용하여 추적 데이터를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="91601-144">For example, the Generic SQL Trace collector type uses the following tables to store trace data:</span></span>  
  
-   <span data-ttu-id="91601-145">core.source_info_internal</span><span class="sxs-lookup"><span data-stu-id="91601-145">core.source_info_internal</span></span>  
  
-   <span data-ttu-id="91601-146">core.snapshots_internal</span><span class="sxs-lookup"><span data-stu-id="91601-146">core.snapshots_internal</span></span>  
  
-   <span data-ttu-id="91601-147">snapshots.trace_info</span><span class="sxs-lookup"><span data-stu-id="91601-147">snapshots.trace_info</span></span>  
  
-   <span data-ttu-id="91601-148">snapshots.trace_data</span><span class="sxs-lookup"><span data-stu-id="91601-148">snapshots.trace_data</span></span>  
  
###### <a name="snapshots-schema"></a><span data-ttu-id="91601-149">snapshot 스키마</span><span class="sxs-lookup"><span data-stu-id="91601-149">Snapshots schema</span></span>  
 <span data-ttu-id="91601-150">snapshots 스키마는 제공된 수집기 유형에 의해 수집된 데이터를 저장하고 유지 관리하는 데 필요한 개체에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="91601-150">The snapshots schema describes the objects needed to store and maintain the data collected by the collector types that are provided.</span></span> <span data-ttu-id="91601-151">이 스키마의 테이블은 고정되며 수집기 유형의 수명 동안 변경될 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="91601-151">The tables in this schema are fixed and do not need to be changed during the lifetime of the collector type.</span></span> <span data-ttu-id="91601-152">스키마를 변경해야 할 경우에는 mdw_admin 역할의 멤버만 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="91601-152">If changes are needed, the schema can only be changed by members of the mdw_admin role.</span></span> <span data-ttu-id="91601-153">이러한 테이블은 시스템 데이터 컬렉션 집합에서 수집한 데이터를 저장하기 위해 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="91601-153">These tables are created to store the data collected by the System Data collection sets.</span></span>  
  
 <span data-ttu-id="91601-154">다음 테이블은 서버 작업 및 쿼리 통계 컬렉션 집합에 필요한 관리 데이터 웨어하우스 스키마의 일부를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="91601-154">The following tables illustrate a portion of the management data warehouse schema that is required for the Server Activity and Query Statistics collection sets.</span></span>  
  
-   <span data-ttu-id="91601-155">시스템 수준 리소스 테이블</span><span class="sxs-lookup"><span data-stu-id="91601-155">System-level resource tables</span></span>  
  
    -   <span data-ttu-id="91601-156">**snapshots.os_wait_stats**</span><span class="sxs-lookup"><span data-stu-id="91601-156">**snapshots.os_wait_stats**</span></span>  
  
    -   <span data-ttu-id="91601-157">**snapshots.os_latch_stats**</span><span class="sxs-lookup"><span data-stu-id="91601-157">**snapshots.os_latch_stats**</span></span>  
  
    -   <span data-ttu-id="91601-158">**snapshots.os_schedulers**</span><span class="sxs-lookup"><span data-stu-id="91601-158">**snapshots.os_schedulers**</span></span>  
  
    -   `snapshots.os_memory_clerks`  
  
    -   <span data-ttu-id="91601-159">**snapshots.os_memory_nodes**</span><span class="sxs-lookup"><span data-stu-id="91601-159">**snapshots.os_memory_nodes**</span></span>  
  
    -   <span data-ttu-id="91601-160">snapshots.sql_process_and_system_memory</span><span class="sxs-lookup"><span data-stu-id="91601-160">snapshots.sql_process_and_system_memory</span></span>  
  
-   <span data-ttu-id="91601-161">시스템 작업</span><span class="sxs-lookup"><span data-stu-id="91601-161">System activity</span></span>  
  
    -   <span data-ttu-id="91601-162">snapshots.active_sessions_and_requests</span><span class="sxs-lookup"><span data-stu-id="91601-162">snapshots.active_sessions_and_requests</span></span>  
  
-   <span data-ttu-id="91601-163">쿼리 통계</span><span class="sxs-lookup"><span data-stu-id="91601-163">Query statistics</span></span>  
  
    -   <span data-ttu-id="91601-164">snapshots.query_stats</span><span class="sxs-lookup"><span data-stu-id="91601-164">snapshots.query_stats</span></span>  
  
-   <span data-ttu-id="91601-165">I/O 통계</span><span class="sxs-lookup"><span data-stu-id="91601-165">I/O statistics</span></span>  
  
    -   `snapshots.io_virtual_file_stats`  
  
-   <span data-ttu-id="91601-166">쿼리 텍스트 및 계획</span><span class="sxs-lookup"><span data-stu-id="91601-166">Query text and plan</span></span>  
  
    -   <span data-ttu-id="91601-167">snapshots.notable_query_text</span><span class="sxs-lookup"><span data-stu-id="91601-167">snapshots.notable_query_text</span></span>  
  
    -   <span data-ttu-id="91601-168">snapshots.notable_query_plan</span><span class="sxs-lookup"><span data-stu-id="91601-168">snapshots.notable_query_plan</span></span>  
  
-   <span data-ttu-id="91601-169">정규화된 쿼리 통계</span><span class="sxs-lookup"><span data-stu-id="91601-169">Normalized query statistics</span></span>  
  
    -   <span data-ttu-id="91601-170">snapshots.distinct_queries</span><span class="sxs-lookup"><span data-stu-id="91601-170">snapshots.distinct_queries</span></span>  
  
    -   <span data-ttu-id="91601-171">snapshots.distinct_query_to_handle</span><span class="sxs-lookup"><span data-stu-id="91601-171">snapshots.distinct_query_to_handle</span></span>  
  
 <span data-ttu-id="91601-172">**Custom_snapshots 스키마**</span><span class="sxs-lookup"><span data-stu-id="91601-172">**Custom_snapshots schema**</span></span>  
  
 <span data-ttu-id="91601-173">custom_snapshots 스키마는 표준 또는 타사 수집기 유형을 사용하여 사용자 정의 컬렉션 집합을 만들 때 생성된 새 테이블과 뷰에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="91601-173">The custom_snapshots schema describes new tables and views that are created when standard or third-party collector types are used to create user-defined collection sets.</span></span> <span data-ttu-id="91601-174">컬렉션 항목에 새 데이터 테이블이 필요한 모든 수집기 유형은 이 스키마에 테이블을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="91601-174">Any collector type that requires a new data table for a collection item can create that table in this schema.</span></span> <span data-ttu-id="91601-175">새 테이블은 mdw_writer 역할의 멤버가 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="91601-175">New tables can be added in this schema by members of the mdw_writer role.</span></span> <span data-ttu-id="91601-176">스키마에 대한 다른 변경 작업은 mdw_admin 역할의 멤버만 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="91601-176">Any other changes to the schema can only be made by members of the mdw_admin role.</span></span>  
  
 <span data-ttu-id="91601-177">데이터베이스 테이블 열에 대한 자세한 데이터 형식 및 콘텐츠 정보는 각 테이블에 해당되는 데이터 수집기 저장 프로시저에 대한 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="91601-177">You can get detailed data type and content information for the database table columns by reading the documentation for the appropriate data collector stored procedure for each of the tables.</span></span>  
  
### <a name="best-practices"></a><span data-ttu-id="91601-178">모범 사례</span><span class="sxs-lookup"><span data-stu-id="91601-178">Best Practices</span></span>  
 <span data-ttu-id="91601-179">관리 데이터 웨어하우스를 사용할 때는 다음과 같은 최선의 방법을 따르는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="91601-179">When working with the management data warehouse, we recommend following these best practices:</span></span>  
  
-   <span data-ttu-id="91601-180">새 수집기 유형을 추가하지 않는 한 관리 데이터 웨어하우스 테이블의 메타데이터를 수정하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="91601-180">Do not modify the metadata of management data warehouse tables unless you are adding a new collector type.</span></span>  
  
-   <span data-ttu-id="91601-181">관리 데이터 웨어하우스의 데이터를 직접 수정하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="91601-181">Do not directly modify the data in the management data warehouse.</span></span> <span data-ttu-id="91601-182">수집한 데이터를 변경하면 수집된 데이터의 타당성이 무효화됩니다.</span><span class="sxs-lookup"><span data-stu-id="91601-182">Changing the data that you have collected invalidates the legitimacy of the collected data.</span></span>  
  
-   <span data-ttu-id="91601-183">테이블을 직접 사용하는 대신 데이터 수집기와 함께 제공되는 문서화된 저장 프로시저 및 함수를 사용하여 인스턴스 및 애플리케이션 데이터에 액세스합니다.</span><span class="sxs-lookup"><span data-stu-id="91601-183">Instead of directly using the tables, use the documented stored procedures and functions that are provided with the data collector to access instance and application data.</span></span> <span data-ttu-id="91601-184">테이블 이름과 정의는 변경될 수 있습니다. 이러한 정보는 애플리케이션을 업데이트할 때 변경되며 후속 릴리스에서 변경될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="91601-184">The table names and definitions can change, do change when you update the application, and might change in future releases.</span></span>  
  
## <a name="change-history"></a><span data-ttu-id="91601-185">변경 내역</span><span class="sxs-lookup"><span data-stu-id="91601-185">Change History</span></span>  
  
|<span data-ttu-id="91601-186">업데이트된 내용</span><span class="sxs-lookup"><span data-stu-id="91601-186">Updated content</span></span>|  
|---------------------|  
|<span data-ttu-id="91601-187">"core 스키마" 섹션에 core.performance_counter_report_group_items 테이블이 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="91601-187">Added the core.performance_counter_report_group_items table to the "Core schema" section.</span></span>|  
|<span data-ttu-id="91601-188">"snapshots 스키마" 섹션의 테이블 목록이 업데이트되었습니다.</span><span class="sxs-lookup"><span data-stu-id="91601-188">Updated the list of tables in the "Snapshots schema" section.</span></span> <span data-ttu-id="91601-189">snapshots.os_memory_clerks,snapshots.sql_process_and_system_memory 및 snapshots.io_virtual_file_stats가 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="91601-189">Added snapshots.os_memory_clerks,snapshots.sql_process_and_system_memory, and snapshots.io_virtual_file_stats.</span></span> <span data-ttu-id="91601-190">snapshots.os_process_memory 및 snapshots.distinct_query_stats가 제거되었습니다.</span><span class="sxs-lookup"><span data-stu-id="91601-190">Removedsnapshots.os_process_memory and snapshots.distinct_query_stats.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="91601-191">참고 항목</span><span class="sxs-lookup"><span data-stu-id="91601-191">See Also</span></span>  
 <span data-ttu-id="91601-192">[관리 데이터 웨어하우스 저장 프로시저&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/management-data-warehouse-stored-procedures-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="91601-192">[Management Data Warehouse Stored Procedures &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/management-data-warehouse-stored-procedures-transact-sql) </span></span>  
 <span data-ttu-id="91601-193">[데이터 수집기 저장 프로시저&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="91601-193">[Data Collector Stored Procedures &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql) </span></span>  
 <span data-ttu-id="91601-194">[데이터 컬렉션](data-collection.md) </span><span class="sxs-lookup"><span data-stu-id="91601-194">[Data Collection](data-collection.md) </span></span>  
 [<span data-ttu-id="91601-195">컬렉션 집합 보고서 보기&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="91601-195">View a Collection Set Report &#40;SQL Server Management Studio&#41;</span></span>](view-a-collection-set-report-sql-server-management-studio.md)  
  
  
