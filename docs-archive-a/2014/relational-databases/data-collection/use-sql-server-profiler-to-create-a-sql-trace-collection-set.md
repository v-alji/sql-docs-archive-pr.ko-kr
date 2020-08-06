---
title: SQL Server Profiler를 사용 하 여 SQL 추적 컬렉션 집합 (SQL Server Management Studio) 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- SQL Trace collector set
ms.assetid: b6941dc0-50f5-475d-82eb-ce7c68117489
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e9c9514fef8069cef615d1480aad1e0acd1582cd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659479"
---
# <a name="use-sql-server-profiler-to-create-a-sql-trace-collection-set-sql-server-management-studio"></a><span data-ttu-id="ad7f5-102">SQL Server 프로파일러를 사용하여 SQL 추적 컬렉션 집합 만들기(SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="ad7f5-102">Use SQL Server Profiler to Create a SQL Trace Collection Set (SQL Server Management Studio)</span></span>
  <span data-ttu-id="ad7f5-103">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 에서 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 의 서버 쪽 추적 기능을 이용하여 일반 SQL 추적 수집기 유형을 사용하는 컬렉션 집합을 만들기 위한 추적 정의를 내보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ad7f5-103">In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] you can exploit the server-side trace capabilities of [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] to export a trace definition that you can use to create a collection set that uses the Generic SQL Trace collector type.</span></span> <span data-ttu-id="ad7f5-104">이 프로세스는 두 부분으로 구성되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ad7f5-104">There are two parts to this process:</span></span>  
  
1.  <span data-ttu-id="ad7f5-105">[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 추적을 만들고 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="ad7f5-105">Create and export a [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] trace.</span></span>  
  
2.  <span data-ttu-id="ad7f5-106">내보낸 추적을 기반으로 새 컬렉션 집합을 스크립팅합니다.</span><span class="sxs-lookup"><span data-stu-id="ad7f5-106">Script a new collection set based on an exported trace.</span></span>  
  
 <span data-ttu-id="ad7f5-107">다음 절차에 대한 시나리오에는 완료하는 데 80밀리초 이상이 걸리는 저장 프로시저에 대한 정보를 수집하는 과정이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ad7f5-107">The scenario for the following procedures involves collecting data about any stored procedure that requires 80 milliseconds or longer to complete.</span></span> <span data-ttu-id="ad7f5-108">이 프로시저를 완료하려면 다음을 수행할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad7f5-108">In order to complete these procedures you should be able to:</span></span>  
  
-   <span data-ttu-id="ad7f5-109">[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 를 사용하여 추적을 만들고 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="ad7f5-109">Use [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] to create and configure a trace.</span></span>  
  
-   <span data-ttu-id="ad7f5-110">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 를 사용하여 쿼리를 열고 편집하며 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="ad7f5-110">Use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to open, edit, and execute a query.</span></span>  
  
### <a name="create-and-export-a-sql-server-profiler-trace"></a><span data-ttu-id="ad7f5-111">SQL Server Profiler 추적 만들기 및 내보내기</span><span class="sxs-lookup"><span data-stu-id="ad7f5-111">Create and export a SQL Server Profiler trace</span></span>  
  
1.  <span data-ttu-id="ad7f5-112">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="ad7f5-112">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], open [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span> <span data-ttu-id="ad7f5-113">**도구** 메뉴에서 **SQL Server Profiler**를 클릭하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ad7f5-113">(On the **Tools** menu, click **SQL Server Profiler**.)</span></span>  
  
2.  <span data-ttu-id="ad7f5-114">**서버에 연결** 대화 상자에서 **취소**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ad7f5-114">In the **Connect to Server** dialog box, click **Cancel**.</span></span>  
  
3.  <span data-ttu-id="ad7f5-115">이 시나리오에서는 기간 값을 밀리초로 표시(기본 설정)하도록 구성되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="ad7f5-115">For this scenario, ensure that duration values are configured to display in milliseconds (the default).</span></span> <span data-ttu-id="ad7f5-116">이렇게 하려면 다음 단계를 수행하세요.</span><span class="sxs-lookup"><span data-stu-id="ad7f5-116">To do this, follow these steps:</span></span>  
  
    1.  <span data-ttu-id="ad7f5-117">**도구** 메뉴에서 **옵션**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ad7f5-117">On the **Tools** menu, click **Options**.</span></span>  
  
    2.  <span data-ttu-id="ad7f5-118">**표시 옵션** 영역에서 기간 열에 값 표시(마이크로초) 확인란이 선택 취소되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="ad7f5-118">In the **Display Options** area, ensure that the Show values in Duration column in microseconds check box is cleared.</span></span>  
  
    3.  <span data-ttu-id="ad7f5-119">**확인** 을 클릭하여 **일반 옵션** 대화 상자를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="ad7f5-119">Click **OK** to close the **General Options** dialog box.</span></span>  
  
4.  <span data-ttu-id="ad7f5-120">**파일** 메뉴에서 **새 추적**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ad7f5-120">On the **File** menu, click **New Trace**.</span></span>  
  
5.  <span data-ttu-id="ad7f5-121">**서버에 연결** 대화 상자에서 연결할 서버를 선택한 다음 **연결**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ad7f5-121">In the **Connect to Server** dialog box, select the server that you want to connect to, and then click **Connect**.</span></span>  
  
     <span data-ttu-id="ad7f5-122">**추적 속성** 대화 상자가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="ad7f5-122">The **Trace Properties** dialog box appears.</span></span>  
  
6.  <span data-ttu-id="ad7f5-123">**일반** 탭에서 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="ad7f5-123">On the **General** tab, do the following:</span></span>  
  
    1.  <span data-ttu-id="ad7f5-124">**추적 이름** 상자에서 추적에 사용할 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="ad7f5-124">In the **Trace name** box, type the name that you want to use for the trace.</span></span> <span data-ttu-id="ad7f5-125">이 예에서 추적 이름은 `SPgt80`입니다.</span><span class="sxs-lookup"><span data-stu-id="ad7f5-125">For this example, the trace name is `SPgt80`.</span></span>  
  
    2.  <span data-ttu-id="ad7f5-126">**템플릿 사용**목록에서 추적에 사용할 템플릿을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ad7f5-126">In the **Use the template list**, select the template to use for the trace.</span></span> <span data-ttu-id="ad7f5-127">이 예에서는 **TSQL_SPs**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ad7f5-127">For this example, click **TSQL_SPs**.</span></span>  
  
7.  <span data-ttu-id="ad7f5-128">**이벤트 선택** 탭에서 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="ad7f5-128">On the **Events Selection** tab, do the following:</span></span>  
  
    1.  <span data-ttu-id="ad7f5-129">추적에 사용할 이벤트를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ad7f5-129">Identify the events to use for the trace.</span></span> <span data-ttu-id="ad7f5-130">이 예에서는 **이벤트** 열에서 **ExistingConnection** 및 **SP:Completed**를 제외한 모든 확인란을 선택 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="ad7f5-130">For this example, clear all check boxes in the **Events** column, except for **ExistingConnection** and **SP:Completed**.</span></span>  
  
    2.  <span data-ttu-id="ad7f5-131">오른쪽 아래 모서리에 있는 **모든 열 표시** 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ad7f5-131">In the lower-right corner, select the **Show all columns** check box.</span></span>  
  
    3.  <span data-ttu-id="ad7f5-132">**SP:Completed** 행을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ad7f5-132">Click the **SP:Completed** row.</span></span>  
  
    4.  <span data-ttu-id="ad7f5-133">열을 스크롤하여 **기간** 열을 찾은 다음 **기간** 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ad7f5-133">Scroll across the row to the **Duration** column, and then select the **Duration** check box.</span></span>  
  
8.  <span data-ttu-id="ad7f5-134">오른쪽 아래 모서리에 있는 **열 필터** 를 클릭하여 **필터 편집** 대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="ad7f5-134">In the lower-right corner, click **Column Filters** to open the **Edit Filter** dialog box.</span></span> <span data-ttu-id="ad7f5-135">**필터 편집** 대화 상자에서 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="ad7f5-135">In the **Edit Filter** dialog box, do the following:</span></span>  
  
    1.  <span data-ttu-id="ad7f5-136">필터 목록에서 **기간**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ad7f5-136">In the filter list, click **Duration**.</span></span>  
  
    2.  <span data-ttu-id="ad7f5-137">부울 연산자 창에서 **크거나 같음** 노드를 확장 하 `80` 고를 값으로 입력 한 다음 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad7f5-137">In the Boolean operator window, expand the **Greater than or equal** node, type `80` as the value, and then click **OK**.</span></span>  
  
9. <span data-ttu-id="ad7f5-138">**실행** 을 클릭하여 추적을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="ad7f5-138">Click **Run** to start the trace.</span></span>  
  
10. <span data-ttu-id="ad7f5-139">도구 모음에서 **선택한 추적 중지** 또는 **선택한 추적 일시 중지**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ad7f5-139">On the toolbar, click **Stop Selected Trace** or **Pause Selected Trace**.</span></span>  
  
11. <span data-ttu-id="ad7f5-140">**파일** 메뉴에서 **내보내기**, **추적 정의 스크립트**를 차례로 가리킨 다음 **SQL 추적 컬렉션 집합**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ad7f5-140">On the **File** menu, point to **Export**, point to **Script Trace Definition**, and then click **For SQL Trace Collection Set**.</span></span>  
  
12. <span data-ttu-id="ad7f5-141">**다른 이름으로 저장** 대화 상자의 **파일 이름** 상자에 추적 정의에 사용할 이름을 입력한 다음 원하는 위치에 파일을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="ad7f5-141">In the **Save As** dialog box, type the name that you want to use for the trace definition in the **File name** box, and then save it in the location that you want.</span></span> <span data-ttu-id="ad7f5-142">이 예에서는 파일 이름이 추적 이름(SPgt80)과 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="ad7f5-142">For this example, the file name is the same as the trace name (SPgt80).</span></span>  
  
13. <span data-ttu-id="ad7f5-143">파일이 성공적으로 저장되었다는 메시지가 나타나면 **확인** 을 클릭한 다음 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="ad7f5-143">Click **OK** when you receive a message that the file was successfully saved, and then close [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span>  
  
### <a name="script-a-new-collection-set-from-a-sql-server-profiler-trace"></a><span data-ttu-id="ad7f5-144">SQL Server Profiler 추적에서 새 컬렉션 집합 스크립팅</span><span class="sxs-lookup"><span data-stu-id="ad7f5-144">Script a new collection set from a SQL Server Profiler trace</span></span>  
  
1.  <span data-ttu-id="ad7f5-145">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]의 **파일** 메뉴에서 **열기** 를 가리킨 다음 **파일**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ad7f5-145">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], on the **File** menu, point to **Open,** and then click **File**.</span></span>  
  
2.  <span data-ttu-id="ad7f5-146">**파일 열기** 대화 상자에서 이전 절차에서 만든 파일(SPgt80)을 찾아 엽니다.</span><span class="sxs-lookup"><span data-stu-id="ad7f5-146">In the **Open File** dialog box, locate and then open the file that you created in the previous procedure (SPgt80).</span></span>  
  
     <span data-ttu-id="ad7f5-147">저장한 추적 정보는 쿼리 창에서 열리고 새 컬렉션 집합을 만들기 위해 실행할 수 있는 스크립트로 병합됩니다.</span><span class="sxs-lookup"><span data-stu-id="ad7f5-147">The trace information that you saved is opened in a Query window and merged into a script that you can run to create the new collection set.</span></span>  
  
3.  <span data-ttu-id="ad7f5-148">스크립트를 스크롤한 다음 스크립트 주석 텍스트에서 설명하는 다음과 같은 대체 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="ad7f5-148">Scroll through the script and make the following replacements, which are noted in the script comment text:</span></span>  
  
    -   <span data-ttu-id="ad7f5-149">**SQLTrace Collection Set Name Here** 를 컬렉션 집합에 사용할 이름으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="ad7f5-149">Replace **SQLTrace Collection Set Name Here** with the name that you want to use for the collection set.</span></span> <span data-ttu-id="ad7f5-150">이 예에서는 컬렉션 집합 이름을 `SPROC_CollectionSet`으로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ad7f5-150">For this example, name the collection set `SPROC_CollectionSet`.</span></span>  
  
    -   <span data-ttu-id="ad7f5-151">**SQLTrace Collection Item Name Here** 를 컬렉션 항목에 사용할 이름으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="ad7f5-151">Replace **SQLTrace Collection Item Name Here** with the name that you want to use for the collection item.</span></span> <span data-ttu-id="ad7f5-152">이 예에서는 컬렉션 항목 이름을 `SPROC_Collection_Item`으로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ad7f5-152">For this example, name the collection item `SPROC_Collection_Item`.</span></span>  
  
4.  <span data-ttu-id="ad7f5-153">**실행** 을 클릭하여 쿼리를 실행하고 컬렉션 집합을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ad7f5-153">Click **Execute** to run the query and to create the collection set.</span></span>  
  
5.  <span data-ttu-id="ad7f5-154">개체 탐색기에서 컬렉션 집합이 만들어졌는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="ad7f5-154">In Object Explorer, verify that the collection set was created.</span></span> <span data-ttu-id="ad7f5-155">이렇게 하려면 다음 단계를 수행하세요.</span><span class="sxs-lookup"><span data-stu-id="ad7f5-155">To do this, follow these steps:</span></span>  
  
    1.  <span data-ttu-id="ad7f5-156">**관리**를 마우스 오른쪽 단추로 클릭한 다음 **새로 고침**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ad7f5-156">Right-click **Management**, and then click **Refresh**.</span></span>  
  
    2.  <span data-ttu-id="ad7f5-157">**관리**와 **데이터 컬렉션**을 차례로 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="ad7f5-157">Expand **Management**, and then expand **Data Collection**.</span></span>  
  
     <span data-ttu-id="ad7f5-158">`SPROC_CollectionSet`컬렉션 집합은 **시스템 데이터 컬렉션 집합** 노드와 같은 수준에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="ad7f5-158">The `SPROC_CollectionSet` collection set appears at the same level as the **System Data Collection Sets** node.</span></span> <span data-ttu-id="ad7f5-159">이 컬렉션 집합은 기본적으로 해제되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ad7f5-159">By default, the collection set is disabled.</span></span>  
  
6.  <span data-ttu-id="ad7f5-160">개체 탐색기를 사용하여 SPROC_CollectionSet에 대해 컬렉션 모드 및 업로드 일정 등의 속성을 편집합니다.</span><span class="sxs-lookup"><span data-stu-id="ad7f5-160">Use Object Explorer to edit the properties of SPROC_CollectionSet, such as the collection mode and upload schedule.</span></span> <span data-ttu-id="ad7f5-161">데이터 수집기와 함께 제공되는 시스템 데이터 컬렉션 집합의 경우와 동일한 절차를 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="ad7f5-161">Follow the same procedures that you would for the System Data collection sets that are provided with the data collector.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ad7f5-162">예제</span><span class="sxs-lookup"><span data-stu-id="ad7f5-162">Example</span></span>  
 <span data-ttu-id="ad7f5-163">다음 코드 샘플은 이전 절차에서 설명한 단계의 결과로 생성되는 최종 스크립트입니다.</span><span class="sxs-lookup"><span data-stu-id="ad7f5-163">The following code sample is the final script resulting from the steps documented in the preceding procedures.</span></span>  
  
```  
/*************************************************************/  
-- SQL Trace collection set generated from SQL Server Profiler  
-- Date: 11/19/2007  12:55:31 AM  
/*************************************************************/  
  
USE msdb  
GO  
  
BEGIN TRANSACTION  
BEGIN TRY  
  
-- Define collection set  
-- ***  
-- *** Replace 'SqlTrace Collection Set Name Here' in the   
-- *** following script with the name you want  
-- *** to use for the collection set.  
-- ***  
DECLARE @collection_set_id int;  
EXEC [dbo].[sp_syscollector_create_collection_set]  
    @name = N'SPROC_CollectionSet',  
    @schedule_name = N'CollectorSchedule_Every_15min',  
    @collection_mode = 0, -- cached mode needed for Trace collections  
    @logging_level = 0, -- minimum logging  
    @days_until_expiration = 5,  
    @description = N'Collection set generated by SQL Server Profiler',  
    @collection_set_id = @collection_set_id output;  
SELECT @collection_set_id;  
  
-- Define input and output variables for the collection item.  
DECLARE @trace_definition xml;  
DECLARE @collection_item_id int;  
  
-- Define the trace parameters as an XML variable  
SELECT @trace_definition = convert(xml,   
N'<ns:SqlTraceCollector xmlns:ns"DataCollectorType" use_default="0">  
<Events>  
  <EventType name="Sessions">  
    <Event id="17" name="ExistingConnection" columnslist="1,2,14,26,3,35,12" />  
  </EventType>  
  <EventType name="Stored Procedures">  
    <Event id="43" name="SP:Completed" columnslist="1,2,26,34,3,35,12,13,14,22" />  
  </EventType>  
</Events>  
<Filters>  
  <Filter columnid="13" columnname="Duration" logical_operator="AND" comparison_operator="GE" value="80000L" />  
</Filters>  
</ns:SqlTraceCollector>  
');  
  
-- Retrieve the collector type GUID for the trace collector type.  
DECLARE @collector_type_GUID uniqueidentifier;  
SELECT @collector_type_GUID = collector_type_uid FROM [dbo].[syscollector_collector_types] WHERE name = N'Generic SQL Trace Collector Type';  
  
-- Create the trace collection item.  
-- ***  
-- *** Replace 'SqlTrace Collection Item Name Here' in   
-- *** the following script with the name you want to  
-- *** use for the collection item.  
-- ***  
EXEC [dbo].[sp_syscollector_create_collection_item]  
   @collection_set_id = @collection_set_id,  
   @collector_type_uid = @collector_type_GUID,  
   @name = N'SPROC_Collection_Item',  
   @frequency = 900, -- specified the frequency for checking to see if trace is still running  
   @parameters = @trace_definition,  
   @collection_item_id = @collection_item_id output;  
SELECT @collection_item_id;  
  
COMMIT TRANSACTION;  
END TRY  
  
BEGIN CATCH  
ROLLBACK TRANSACTION;  
DECLARE @ErrorMessage nvarchar(4000);  
DECLARE @ErrorSeverity int;  
DECLARE @ErrorState int;  
DECLARE @ErrorNumber int;  
DECLARE @ErrorLine int;  
DECLARE @ErrorProcedure nvarchar(200);  
SELECT @ErrorLine = ERROR_LINE(),  
       @ErrorSeverity = ERROR_SEVERITY(),  
       @ErrorState = ERROR_STATE(),  
       @ErrorNumber = ERROR_NUMBER(),  
       @ErrorMessage = ERROR_MESSAGE(),  
       @ErrorProcedure = ISNULL(ERROR_PROCEDURE(), '-');  
RAISERROR (14684, @ErrorSeverity, 1 , @ErrorNumber, @ErrorSeverity, @ErrorState, @ErrorProcedure, @ErrorLine, @ErrorMessage);  
END CATCH;  
GO  
```  
  
  
