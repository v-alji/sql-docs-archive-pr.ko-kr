---
title: 이벤트 세션 데이터 보기 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: ac742a01-2a95-42c7-b65e-ad565020dc49
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: eaeb5fd22b95b8f1056b8dce9e3c7d683b52602f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741204"
---
# <a name="view-event-session-data"></a><span data-ttu-id="6373f-102">이벤트 세션 데이터 보기</span><span class="sxs-lookup"><span data-stu-id="6373f-102">View Event Session Data</span></span>
  <span data-ttu-id="6373f-103">이 항목에서는 디스플레이 사용자 인터페이스를 사용하여 확장 이벤트 데이터를 확인하고 분석하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-103">This topic describes using the display user interface to see and analyze extended event data:</span></span>  
  
-   <span data-ttu-id="6373f-104">대상 데이터 보기</span><span class="sxs-lookup"><span data-stu-id="6373f-104">View Target Data</span></span>  
  
-   <span data-ttu-id="6373f-105">데이터 사용</span><span class="sxs-lookup"><span data-stu-id="6373f-105">Working With Data</span></span>  
  
## <a name="view-target-data"></a><span data-ttu-id="6373f-106">대상 데이터 보기</span><span class="sxs-lookup"><span data-stu-id="6373f-106">View Target Data</span></span>  
 <span data-ttu-id="6373f-107">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]내에서 지정된 대상에 수집된 데이터를 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-107">You can display the data collected into the specified target within [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
### <a name="view-target-data"></a><span data-ttu-id="6373f-108">대상 데이터 보기</span><span class="sxs-lookup"><span data-stu-id="6373f-108">View Target Data</span></span>  
 <span data-ttu-id="6373f-109">대상 데이터를 보려면</span><span class="sxs-lookup"><span data-stu-id="6373f-109">To view target data:</span></span>  
  
1.  <span data-ttu-id="6373f-110">개체 탐색기에서 **관리**, **확장 이벤트**, **세션**을 차례로 확장한 다음 세션을 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-110">In Object Explorer, expand **Management**, **Extended Events**, **Sessions**, and then a session.</span></span>  
  
2.  <span data-ttu-id="6373f-111">대상 이름을 마우스 오른쪽 단추로 클릭한 다음 **대상 데이터 보기** 를 클릭하여 대상 데이터를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-111">Right-click the target name, and then click **View Target Data** to display the target data.</span></span>  
  
     <span data-ttu-id="6373f-112">대상 데이터 창이 기본 보기로 나타나고 대상 데이터가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-112">The target data window appears in default view and displays the target data.</span></span>  
  
 <span data-ttu-id="6373f-113">대상 데이터 확인 참고 사항:</span><span class="sxs-lookup"><span data-stu-id="6373f-113">Notes on viewing target data:</span></span>  
  
-   <span data-ttu-id="6373f-114">대상 데이터는 ETW 대상에 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-114">Target data is not available for the ETW target.</span></span>  
  
-   <span data-ttu-id="6373f-115">xml 형식의 ring_buffer 데이터를 보려면 대상 데이터 창에서 **ring_buffer 대상 데이터** 링크를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-115">To view the ring_buffer data in xml format, in the target data window click the **ring_buffer target data** link.</span></span> <span data-ttu-id="6373f-116">ring_buffer.xml 파일이 XML 편집기에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-116">The ring_buffer.xml file appears in the xml editor.</span></span>  
  
-   <span data-ttu-id="6373f-117">event_file 대상의 경우 다음 방법 중 하나를 사용하여 파일 대상 데이터(.XEL 파일)를 봅니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-117">For an event_file target, view the file target data (.XEL file) using one of the following methods:</span></span>  
  
    -   <span data-ttu-id="6373f-118">에서 파일 > 열기를 사용 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-118">Use File -> Open in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>
    
    -   <span data-ttu-id="6373f-119">파일을로 끌어 놓습니다 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="6373f-119">Drag and drop the file into [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span> 
    
    -   <span data-ttu-id="6373f-120">.XEL 파일을 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-120">Double click the .XEL file.</span></span>  
    
    -   <span data-ttu-id="6373f-121">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]에서 실행 중인 확장 이벤트 세션을 마우스 오른쪽 단추로 클릭하고 대상 데이터 보기를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-121">In [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], right click on a running Extended Events session and select View Target Data.</span></span> 
    
    -   <span data-ttu-id="6373f-122">[fn_xe_file_target_read_file](/sql/relational-databases/system-functions/sys-fn-xe-file-target-read-file-transact-sql).</span><span class="sxs-lookup"><span data-stu-id="6373f-122">[fn_xe_file_target_read_file](/sql/relational-databases/system-functions/sys-fn-xe-file-target-read-file-transact-sql).</span></span>
    
    -   <span data-ttu-id="6373f-123">[SQLServer 모듈](https://www.powershellgallery.com/packages/SqlServer.XEvent)에서 Powershell 읽기-sqlxevent를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-123">Use Powershell Read-SQLXevent in [SQLServer.XEvent module](https://www.powershellgallery.com/packages/SqlServer.XEvent).</span></span>
    
    -   <span data-ttu-id="6373f-124">[Xelite NuGet](https://www.nuget.org/packages/Microsoft.SqlServer.XEvent.XELite)을 사용 하 여 프로그래밍 방식으로 xevent를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-124">Programmatically consume XEvents by using the [XELite NuGet](https://www.nuget.org/packages/Microsoft.SqlServer.XEvent.XELite).</span></span>
    
    -   <span data-ttu-id="6373f-125">둘 이상의를 볼 수 있습니다. XEL 파일-> 열기 메뉴에서 **확장 이벤트 파일 병합** 을 선택 하 여 파일을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-125">You can view more than one .XEL file by selecting **Merge Extended Event Files** from the File -> Open menu.</span></span>

### <a name="watching-live-data"></a><span data-ttu-id="6373f-126">라이브 데이터 감시</span><span class="sxs-lookup"><span data-stu-id="6373f-126">Watching Live Data</span></span>  
 <span data-ttu-id="6373f-127">라이브 데이터를 캡처하면서 감시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-127">You can watch live data as it is being captured.</span></span>  
  
-   <span data-ttu-id="6373f-128">개체 탐색기에서 **관리**, **확장 이벤트**, **세션** 노드를 차례로 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-128">In Object Explorer, expand the **Management**, **Extended Events**, and then **Sessions** nodes.</span></span>  

-   <span data-ttu-id="6373f-129">세션 이름을 마우스 오른쪽 단추로 클릭한 다음 **라이브 데이터 감시** 를 클릭하여 추적 데이터를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-129">Right-click the session name and then click **Watch Live Data** to start displaying the tracing data.</span></span>  
  
     <span data-ttu-id="6373f-130">기본 표시 열은 **이벤트 이름** 및 **TimeStamp**입니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-130">The default display columns are **Event Name** and **TimeStamp**.</span></span>  
  
     <span data-ttu-id="6373f-131">추적 창에 다른 열을 추가하려면 확장 이벤트 도구 모음의 **열 선택** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-131">To add additional columns to the trace window, click the **Choose Columns** button on the Extended Events toolbar.</span></span> <span data-ttu-id="6373f-132">**세부 정보** 탭에 선택한 이벤트에 대한 모든 이벤트 세부 정보가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-132">The **Details** tab shows all of the event details for the selected event.</span></span>  
  
     <span data-ttu-id="6373f-133">이벤트는 일반적으로 약 30초 내에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-133">Events are usually displayed in approximately 30 seconds.</span></span> <span data-ttu-id="6373f-134">대기 시간을 변경하려면 **새 세션** 대화 상자의 **고급** 페이지에서 **최대 디스패치 대기 시간** 을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-134">If you want to change the latency period, you can change the **Maximum dispatch latency** on the **Advanced** page of the of the **New Session** dialog.</span></span>  
     
-    <span data-ttu-id="6373f-135">[SqlServer PowerShell 모듈](https://www.powershellgallery.com/packages/SqlServer.XEvent)을 통해 라이브 데이터를 스트리밍할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-135">Live data can be streamed by the [SqlServer.XEvent PowerShell module](https://www.powershellgallery.com/packages/SqlServer.XEvent).</span></span>
     
### <a name="to-refresh-target-data"></a><span data-ttu-id="6373f-136">대상 데이터를 새로 고치려면</span><span class="sxs-lookup"><span data-stu-id="6373f-136">To Refresh Target Data</span></span>  
 <span data-ttu-id="6373f-137">event_files 대상에 대해서는 대상 데이터를 새로 고칠 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-137">Refreshing target data is not supported for event_files targets:</span></span>  
  
1.  <span data-ttu-id="6373f-138">대상 데이터를 자동으로 새로 고치려면 대상 데이터를 마우스 오른쪽 단추로 클릭하고 **새로 고침 간격**을 선택한 다음 간격 목록에서 새로 고침 간격을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-138">To refresh the target data automatically, right click the target data, select **Refresh Interval**, and then select the refresh interval from the interval list.</span></span>  
  
2.  <span data-ttu-id="6373f-139">자동 새로 고침을 일시 중지하거나 재개하려면 대상 데이터를 마우스 오른쪽 단추로 클릭하고 **일시 중지** 또는 **재개**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-139">To pause and resume the automatic refresh, right-click the target data and then select **Pause** or **Resume**.</span></span>  
  
3.  <span data-ttu-id="6373f-140">대상 데이터를 수동으로 새로 고치려면 대상 데이터를 마우스 오른쪽 단추로 클릭한 다음 **새로 고침**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-140">To refresh the target data manually, right click the target data, and then select **Refresh**.</span></span>  
  
## <a name="working-with-data"></a><span data-ttu-id="6373f-141">데이터 사용</span><span class="sxs-lookup"><span data-stu-id="6373f-141">Working With Data</span></span>  
 <span data-ttu-id="6373f-142">확장 이벤트 사용자 인터페이스의 분석 기능을 사용하여 문제를 식별할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-142">You can use the analysis capabilities of the Extended Events user interface to identify problems.</span></span>  
  
### <a name="details-pane"></a><span data-ttu-id="6373f-143">정보 창</span><span class="sxs-lookup"><span data-stu-id="6373f-143">Details Pane</span></span>  
 <span data-ttu-id="6373f-144">**세부 정보** 창에는 필드 및 동작을 비롯하여 선택된 이벤트에 대한 모든 열이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-144">The **Details** pane shows all the columns for the selected event, including fields and actions.</span></span> <span data-ttu-id="6373f-145">**세부 정보** 창에서 행을 마우스 오른쪽 단추로 클릭하고 **테이블에 열 표시**를 선택하여 대상 데이터 테이블에 열을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-145">You can add a column to the target data table by right-clicking a row in the **Details** pane and selecting **Show Column in Table**.</span></span>  
  
### <a name="create-modify-or-delete-merged-columns"></a><span data-ttu-id="6373f-146">병합된 열 만들기, 수정 또는 삭제</span><span class="sxs-lookup"><span data-stu-id="6373f-146">Create, Modify, or Delete Merged Columns</span></span>  
 <span data-ttu-id="6373f-147">병합된 열을 사용하면 단일 열에 표시할 필드 집합을 결합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-147">A merged column allows you to combine a set of fields to be displayed in a single column.</span></span> <span data-ttu-id="6373f-148">병합된 열에는 필드 목록에 추가된 순서를 바탕으로 NULL이 아닌 첫 번째 필드의 데이터가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-148">The merged column will show the data from the first non-NULL field based on the order they are added to the field list.</span></span> <span data-ttu-id="6373f-149">이는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 프로파일러와 유사합니다. SQL Server 프로파일러에서는 이벤트에 따라 특정 열에 다른 데이터가 표시될 수 있습니다. 이에 대한 가장 일반적인 예는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 프로파일러의 TextData 필드입니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-149">This is similar to what you see in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Profiler, where a specific column may show different data depending on the event (the most common example of this is the TextData field in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Profiler).</span></span> <span data-ttu-id="6373f-150">예를 들어 sql_statement_completed 및 sql_batch_completed 이벤트의 문과 batch_text 필드를 각각 myStatement라는 필드로 병합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-150">For an example, you could merge the statement and batch_text fields from the sql_statement_completed and sql_batch_completed events, respectively, into a field named myStatement.</span></span> <span data-ttu-id="6373f-151">테이블에 myStatement 열을 표시하면 연결된 이벤트에 적절한 데이터가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-151">When you display the myStatement column in the table it will show the appropriate data for the associated event.</span></span>  
  
 <span data-ttu-id="6373f-152">다음과 같이 병합된 열을 만들거나, 수정하거나, 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-152">You can create, modify, or delete merged columns:</span></span>  
  
1.  <span data-ttu-id="6373f-153">.XEL 파일을 열고 추적 결과를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-153">Open a .XEL file to view the trace results.</span></span> <span data-ttu-id="6373f-154">세션 이름을 마우스 오른쪽 단추로 클릭 한 다음 **라이브 데이터 감시**를 선택할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-154">(You can also right click the session name, and then select **Watch Live Data**.)</span></span>  
  
2.  <span data-ttu-id="6373f-155">추적 결과 창에서 열 머리글을 마우스 오른쪽 단추로 클릭한 다음 **열 선택**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-155">In the trace results window, right-click the column header, and then click **Choose Columns**.</span></span>  
  
 <span data-ttu-id="6373f-156">병합된 열을 만들려면 **열 선택** 대화 상자에서 **새로 만들기** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-156">To create a merged column, click **New** in the **Choose Columns** dialog box.</span></span>  <span data-ttu-id="6373f-157">**병합된 새 열** 대화 상자에서 병합된 열의 이름을 지정하고 병합된 열에 포함할 원래 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-157">In the **New Merged Column** dialog, name the merged column and select the original columns to be included in the merged column.</span></span>  
  
 <span data-ttu-id="6373f-158">병합된 열을 편집하려면 **열 선택** 대화 상자에서 병합된 열을 선택하고 **편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-158">To edit a merged column, select a merged column in the **Choose Columns** dialog and click **Edit**.</span></span> <span data-ttu-id="6373f-159">**병합된 열 편집** 대화 상자에서 병합된 열의 이름을 바꾸거나 병합된 열에 포함할 원래 열을 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-159">In the **Edit Merged Column** dialog, rename the merged column or modify the original columns to be included in the merged column.</span></span>  
  
 <span data-ttu-id="6373f-160">병합된 열을 삭제하려면 **열 선택** 대화 상자에서 병합된 열을 선택하고 **삭제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-160">To delete a merged column, select a merged column in the **Choose Columns** dialog and click **Delete**.</span></span>  
  
### <a name="filter-results"></a><span data-ttu-id="6373f-161">결과 필터링</span><span class="sxs-lookup"><span data-stu-id="6373f-161">Filter Results</span></span>  
 <span data-ttu-id="6373f-162">추적 결과를 본 다음 필터를 적용하여 추적 창에 표시되는 추적 결과의 범위를 좁힐 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-162">You can view trace results, and then apply filters to narrow down the trace results that are displayed in the trace window.</span></span> <span data-ttu-id="6373f-163">표시 필터에는 시간 필터 및 고급 필터가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-163">The display filter includes a time filter and an advanced filter.</span></span> <span data-ttu-id="6373f-164">시간 필터를 사용하여 이벤트 타임스탬프를 기준으로 추적 결과를 필터링할 수 있으며, 고급 필터를 사용하면 이벤트 필드와 동작을 사용하여 필터 조건을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-164">You use the time filter to filter the trace results by event timestamp, and you use the advanced filter to construct filter conditions using the event fields and actions.</span></span> <span data-ttu-id="6373f-165">시간 및 고급 필터 간에는 "그리고"의 관계가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-165">There is an "and" relationship between the time and advanced filters.</span></span>  
  
 <span data-ttu-id="6373f-166">필터를 만들려면:</span><span class="sxs-lookup"><span data-stu-id="6373f-166">To create a filter:</span></span>  
  
1.  <span data-ttu-id="6373f-167">.XEL 파일을 열고 추적 결과를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-167">Open a .XEL file to view the trace results.</span></span> <span data-ttu-id="6373f-168">세션 이름을 마우스 오른쪽 단추로 클릭 한 다음 **라이브 데이터 감시**를 선택할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-168">(You can also right click the session name, and then select **Watch Live Data**.)</span></span>  
  
2.  <span data-ttu-id="6373f-169">추적 결과 창에서 필터링하려는 결과를 선택한 다음 **확장 이벤트** 도구 모음에서 **필터**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-169">In the trace results window, select the results you want to filter, and then on the **Extended Events** toolbar, click **Filters**.</span></span>  
  
3.  <span data-ttu-id="6373f-170">**필터** 대화 상자에서 **시간 필터 설정** 을 선택하고 슬라이더 막대를 끌거나 편집 상자에서 시간을 수정하여 시간 필터를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-170">In the **Filters** dialog box, select **Set time filter** to set the time filter by dragging the slider bars or modifying the time in the edit box.</span></span>  
  
4.  <span data-ttu-id="6373f-171">**추가 필터** 섹션에 필터 조건을 적용한 다음 **적용**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-171">In the **Additional filters** section, apply your filter criteria, and then click **Apply**.</span></span>  
  
### <a name="sort-results"></a><span data-ttu-id="6373f-172">결과 정렬</span><span class="sxs-lookup"><span data-stu-id="6373f-172">Sort Results</span></span>  
 <span data-ttu-id="6373f-173">결과를 오름차순 또는 내림차순으로 정렬하려면</span><span class="sxs-lookup"><span data-stu-id="6373f-173">To sort results either in ascending or descending order:</span></span>  
  
1.  <span data-ttu-id="6373f-174">.XEL 파일을 열고 추적 결과를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-174">Open a .XEL file to view the trace results.</span></span> <span data-ttu-id="6373f-175">세션 이름을 마우스 오른쪽 단추로 클릭 하 고 **라이브 데이터 감시**를 선택한 다음 도구 모음에서 **데이터 피드 중지** 단추를 클릭할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-175">(You can also right click the session name, select **Watch Live Data**, and then click the **Stop Data Feed** button on the toolbar.)</span></span>  
  
2.  <span data-ttu-id="6373f-176">추적 결과 창에서 정렬하려는 열 머리글을 마우스 오른쪽 단추로 클릭하고 **오름차순 정렬** 또는 **내림차순 정렬**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-176">In the trace results window, right-click the column heading you want to sort and click **Sort Ascending** or **Sort Descending**.</span></span>  
  
 <span data-ttu-id="6373f-177">열 머리글을 클릭하여 정렬 순서를 반대로 바꿀 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-177">You can also click the column header to reverse the sort order.</span></span>  
  
 <span data-ttu-id="6373f-178">그룹화된 열이 있는 경우 열을 정렬하면 그룹 내의 데이터만 정렬됩니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-178">If you have grouped columns, sorting the column will only sort data within the group.</span></span>  
  
### <a name="group-results"></a><span data-ttu-id="6373f-179">결과 그룹화</span><span class="sxs-lookup"><span data-stu-id="6373f-179">Group Results</span></span>  
 <span data-ttu-id="6373f-180">그룹화된 결과는 [!INCLUDE[tsql](../includes/tsql-md.md)]에서 `GROUP BY` 절의 기능에 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-180">Grouped results are equivalent to the functionality of the `GROUP BY` clause in [!INCLUDE[tsql](../includes/tsql-md.md)].</span></span> <span data-ttu-id="6373f-181">대상 데이터 테이블에는 데이터가 그룹화되어 표시되므로 사용자가 데이터를 확장하고 축소할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-181">The target data table will show the data grouped together, allowing you to expand and collapse the data.</span></span>  
  
 <span data-ttu-id="6373f-182">데이터를 집계하려면 먼저 그룹화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-182">You must group data before you can aggregate it.</span></span> <span data-ttu-id="6373f-183">예를 들어 query_hash 값을 기준으로 그룹화하고, 기간을 기준으로 내림차순으로 정렬하고, 각 그룹의 평균 기간을 구한 다음 집계를 기준으로 내림차순으로 정렬할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-183">For example, you can group on the query_hash value, sort descending by duration, get the average duration for each group, and then sort descending on the aggregation.</span></span>  <span data-ttu-id="6373f-184">이렇게 하면 고유 문 목록을 가장 긴 평균 기간부터 가장 짧은 평균 기간 순으로 보여 주는 목록이 생산됩니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-184">This will produce a list that shows the list of unique statements from longest to shortest average duration.</span></span> <span data-ttu-id="6373f-185">최상위 그룹을 확장하면 해당 쿼리의 개별 실행이 가장 긴 것부터 가장 짧은 것 순으로 정렬되어 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-185">When you expand the top group you will see the individual executions of that specific query sorted from longest to shortest.</span></span>  
  
 <span data-ttu-id="6373f-186">단일 열 또는 여러 열을 기준으로 결과를 그룹화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-186">You can group results by a single column or by multiple columns.</span></span>  
  
 <span data-ttu-id="6373f-187">.XEL 파일을 열고 추적 결과를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-187">Open a .XEL file to view the trace results.</span></span> <span data-ttu-id="6373f-188">세션 이름을 마우스 오른쪽 단추로 클릭 하 고 **라이브 데이터 감시**를 선택한 다음 도구 모음에서 **데이터 피드 중지** 단추를 클릭할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-188">(You can also right click the session name, select **Watch Live Data**, and then click the **Stop Data Feed** button on the toolbar.)</span></span>  
  
 <span data-ttu-id="6373f-189">단일 열을 기준으로 결과를 그룹화하려면 추적 결과 창에서 열 머리글을 마우스 오른쪽 단추로 클릭하고 **이 열을 기준으로 그룹화**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-189">To group results by a single column, right-click the column heading in the trace results window, and click **Group by this Column**.</span></span> <span data-ttu-id="6373f-190">그룹화를 실행 취소하려면 행 중 하나를 선택하고 **모든 그룹화 제거**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-190">To undo the grouping, select one of the rows and click **Remove All Groupings**.</span></span>  
  
 <span data-ttu-id="6373f-191">여러 열을 기준으로 결과를 그룹화하려면 **확장 이벤트** 도구 모음에서 **그룹화** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-191">To group results by a multiple columns, click the **Grouping** button on the **Extended Events** toolbar.</span></span> <span data-ttu-id="6373f-192">**그룹화** 대화 상자의 **사용 가능한 열** 상자에서 그룹화하려는 열을 선택하여 **그룹화할 열** 상자로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-192">In the **Available columns** box of the **Grouping** dialog, select the columns you want to group, and move them into the **Columns grouped on** box.</span></span> <span data-ttu-id="6373f-193">**그룹화할 열** 상자에서 순서를 변경하려면 위로 또는 아래로 화살표를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-193">To change the order in the **Columns grouped on** box, click the up or down arrows.</span></span>  
  
### <a name="aggregate-results"></a><span data-ttu-id="6373f-194">결과 집계</span><span class="sxs-lookup"><span data-stu-id="6373f-194">Aggregate Results</span></span>  
 <span data-ttu-id="6373f-195">추적 결과를 본 다음 결과의 열을 집계하여 이벤트 데이터를 추가 분석할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-195">You can view the trace results, and then further analyze your event data by aggregating columns in your results.</span></span> <span data-ttu-id="6373f-196">확장 이벤트는 다섯 가지 집계 함수를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-196">Extended Events supports five aggregation functions:</span></span>  
  
-   <span data-ttu-id="6373f-197">sum</span><span class="sxs-lookup"><span data-stu-id="6373f-197">sum</span></span>  
  
-   <span data-ttu-id="6373f-198">min</span><span class="sxs-lookup"><span data-stu-id="6373f-198">min</span></span>  
  
-   <span data-ttu-id="6373f-199">max</span><span class="sxs-lookup"><span data-stu-id="6373f-199">max</span></span>  
  
-   <span data-ttu-id="6373f-200">average</span><span class="sxs-lookup"><span data-stu-id="6373f-200">average</span></span>  
  
-   <span data-ttu-id="6373f-201">개수</span><span class="sxs-lookup"><span data-stu-id="6373f-201">count</span></span>  
  
 <span data-ttu-id="6373f-202">sum, min, max 및 average는 숫자 열에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-202">Sum, min, max, and average can only be used with numeric columns.</span></span> <span data-ttu-id="6373f-203">count는 그룹에서 선택한 열에 대해 존재하는 Null이 아닌 값의 숫자입니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-203">Count is the number of non-null values that exist for the selected column in the group.</span></span>  
  
 <span data-ttu-id="6373f-204">그룹에 대해 집계가 수행되므로 집계를 수행하기 전에 결과를 그룹화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-204">Aggregation is performed on a group, so you must group the results before you can perform the aggregation.</span></span> <span data-ttu-id="6373f-205">결과를 집계하려면</span><span class="sxs-lookup"><span data-stu-id="6373f-205">To aggregate results:</span></span>  
  
1.  <span data-ttu-id="6373f-206">.XEL 파일을 열고 추적 결과를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-206">Open a .XEL file to view the trace results.</span></span> <span data-ttu-id="6373f-207">세션 이름을 마우스 오른쪽 단추로 클릭 하 고 **라이브 데이터 감시**를 선택한 다음 도구 모음에서 **데이터 피드 중지** 단추를 클릭할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-207">(You can also right click the session name, select **Watch Live Data**, and then click the **Stop Data Feed** button on the toolbar.)</span></span>  
  
2.  <span data-ttu-id="6373f-208">**확장 이벤트** 도구 모음에서 **집계** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-208">On the **Extended Events** toolbar, click the **Aggregation** button.</span></span> <span data-ttu-id="6373f-209">집계 대화 상자에 집계에 사용할 수 있는 열이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-209">The Aggregation dialog box will display the columns available for aggregation.</span></span>  
  
3.  <span data-ttu-id="6373f-210">**집계 유형** 열에서 집계 유형을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-210">In the **Aggregation Type** column, select the aggregation type.</span></span>  
  
4.  <span data-ttu-id="6373f-211">**집계별 정렬** 상자에서 정렬 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-211">In the **Sort aggregation by** box, select the sort column.</span></span> <span data-ttu-id="6373f-212">그런 다음 오름차순 또는 내림차순을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-212">Then select ascending or descending order.</span></span>  
  
### <a name="search-for-text-in-columns"></a><span data-ttu-id="6373f-213">열에서 텍스트 검색</span><span class="sxs-lookup"><span data-stu-id="6373f-213">Search for Text in Columns</span></span>  
 <span data-ttu-id="6373f-214">다음과 같이 열에서 텍스트를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-214">You can search for text in columns:</span></span>  
  
1.  <span data-ttu-id="6373f-215">.XEL 파일을 열고 추적 결과를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-215">Open a .XEL file to view the trace results.</span></span> <span data-ttu-id="6373f-216">세션 이름을 마우스 오른쪽 단추로 클릭하고 **라이브 데이터 감시**를 선택할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-216">(You can also right click the session name, select **Watch Live Data**.</span></span>  
  
2.  <span data-ttu-id="6373f-217">**확장 이벤트** 도구 모음에서 **찾기** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-217">Click **Find** on the **Extended Events** toolbar.</span></span>  
  
3.  <span data-ttu-id="6373f-218">**확장 이벤트에서 찾기** 대화 상자의 **찾을 내용** 상자에 검색 텍스트를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-218">In the **Find what** box of the **Find in Extended Events** dialog box, enter the search text.</span></span> <span data-ttu-id="6373f-219">드롭다운 목록에서 가장 최근에 검색한 20개의 문자열 중 하나를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-219">You can select one of your last 20 search strings from the drop-down list.</span></span>  
  
4.  <span data-ttu-id="6373f-220">**찾는 위치** 상자에서 지정된 텍스트를 검색할 위치를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-220">In the **Look in** box, select the location to search for the specified text.</span></span> <span data-ttu-id="6373f-221">검색 시 다음 옵션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-221">Use the following options for searching:</span></span>  
  
    -   <span data-ttu-id="6373f-222">테이블 열.</span><span class="sxs-lookup"><span data-stu-id="6373f-222">Table Columns.</span></span> <span data-ttu-id="6373f-223">추적 창에 표시되는 모든 열을 검색하려면 이 옵션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-223">Use this option to search all visible columns in the trace window.</span></span>  
  
    -   <span data-ttu-id="6373f-224">자세히.</span><span class="sxs-lookup"><span data-stu-id="6373f-224">Details.</span></span> <span data-ttu-id="6373f-225">**확장 이벤트에서 찾기** 대화 상자를 열기 전에 선택한 추적 창에서 승격 된 모든 열 (승격 된 열 및 승격 되지 않은 열)을 검색 하려면이 옵션을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-225">Use this option to search all columns (promoted and non-promoted) in the trace window that were selected before opening the **Find in Extended Events** dialog box.</span></span>  
  
    -   <span data-ttu-id="6373f-226">*Event_column_name*입니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-226">*Event_column_name*.</span></span> <span data-ttu-id="6373f-227">드롭다운 목록의 특정 이벤트 열에서 검색하려면 이 옵션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-227">Use this option to search in a specific event column from the drop-down list.</span></span>  
  
5.  <span data-ttu-id="6373f-228">검색을 정의하는 방법을 지정하려면 다음 옵션을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="6373f-228">Use the following options to specify how you want to define the search:</span></span>  
  
    -   <span data-ttu-id="6373f-229">대/소문자 구분.</span><span class="sxs-lookup"><span data-stu-id="6373f-229">Match case.</span></span> <span data-ttu-id="6373f-230">찾을 내용 상자에 입력한 텍스트와 내용과 대/소문자가 모두 일치하는 검색 결과만 표시하려면 이 옵션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-230">Use this option to display the search results for the text you entered in the Find what box that are matched both by content and by case.</span></span>  
  
    -   <span data-ttu-id="6373f-231">단어 단위로.</span><span class="sxs-lookup"><span data-stu-id="6373f-231">Match whole word.</span></span> <span data-ttu-id="6373f-232">입력한 텍스트와 전체 단어가 일치하는 검색 결과만 표시하려면 이 옵션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-232">Use this option to display only the search results for the text you entered that match complete words.</span></span>  
  
    -   <span data-ttu-id="6373f-233">위로 검색.</span><span class="sxs-lookup"><span data-stu-id="6373f-233">Search up.</span></span> <span data-ttu-id="6373f-234">커서 위치에서 결과의 위로 검색하려면 이 옵션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-234">Use this option to search from your cursor location to the beginning of the results.</span></span>  
  
    -   <span data-ttu-id="6373f-235">사용.</span><span class="sxs-lookup"><span data-stu-id="6373f-235">Use.</span></span> <span data-ttu-id="6373f-236">찾을 내용 상자에 입력한 특수 문자 및 정규식을 해석하려면 이 옵션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-236">Use this option to interpret the special characters and the regular expressions you entered in the Find what box.</span></span> <span data-ttu-id="6373f-237">특수 문자에는 하나 이상의 문자를 나타내는 와일드카드 문자(\*) 및 (?)가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-237">Special characters include the wildcard characters (\*) and (?) to represent one or more characters.</span></span> <span data-ttu-id="6373f-238">정규식은 검색 텍스트의 패턴을 정의하는 데 사용하는 특수 표기입니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-238">Regular expressions are special notations used to define patterns of search text.</span></span>  
  
    -   <span data-ttu-id="6373f-239">**찾을 내용** 상자에 입력한 다음 텍스트를 검색하려면 **다음 찾기** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-239">Click **Find Next** to search for the next text that you entered in the **Find what** box.</span></span>  
  
### <a name="bookmarks"></a><span data-ttu-id="6373f-240">책갈피</span><span class="sxs-lookup"><span data-stu-id="6373f-240">Bookmarks</span></span>  
 <span data-ttu-id="6373f-241">행으로 보다 쉽게 돌아갈 수 있도록 대상 데이터에서 하나 이상의 행에 책갈피를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-241">To make it easier to return to a row, you can bookmark one or more row(s) in the target data.</span></span> <span data-ttu-id="6373f-242">책갈피를 변경하려면 행을 마우스 오른쪽 단추로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-242">Right click on a row to change the bookmark.</span></span> <span data-ttu-id="6373f-243">책갈피가 지정된 행으로 이동하려면 **확장 이벤트** 도구 모음에 있는 이전 및 다음 단추를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-243">Use the previous and next buttons on the **Extended Events** toolbar to navigate to bookmarked rows.</span></span>  
  
### <a name="change-display-settings"></a><span data-ttu-id="6373f-244">표시 설정 변경</span><span class="sxs-lookup"><span data-stu-id="6373f-244">Change Display Settings</span></span>  
 <span data-ttu-id="6373f-245">추적 결과의 열 정보(열 순서, 병합 열 및 열 너비) 및 필터 정보를 확장 이벤트의 표시 설정 파일(.viewsetting 파일)에 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-245">You can save column information (column order, merge column, and column width) and filter information of a trace result into an Extended Events display setting file (.viewsetting file).</span></span> <span data-ttu-id="6373f-246">파일을 저장한 후 추적 결과에 이 파일을 적용하여 뷰를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-246">After saving the file, you can apply it to your trace results to change the view.</span></span>  
  
 <span data-ttu-id="6373f-247">표시 설정을 변경하려면</span><span class="sxs-lookup"><span data-stu-id="6373f-247">To change the display settings:</span></span>  
  
1.  <span data-ttu-id="6373f-248">.XEL 파일을 열고 추적 결과를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-248">Open a .XEL file to view the trace results.</span></span> <span data-ttu-id="6373f-249">세션 이름을 마우스 오른쪽 단추로 클릭하고 **라이브 데이터 감시**를 선택할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-249">(You can also right click the session name, select **Watch Live Data**.</span></span>  
  
2.  <span data-ttu-id="6373f-250">**확장 이벤트** 도구 모음에서 **표시 설정**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-250">On the **Extended Events** toolbar, select **Display Settings**.</span></span> <span data-ttu-id="6373f-251">드롭다운 목록에서 다음 옵션 중 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-251">From the drop-down list, select one of the following options:</span></span>  
  
    -   <span data-ttu-id="6373f-252">다른 이름으로 저장:</span><span class="sxs-lookup"><span data-stu-id="6373f-252">Save as.</span></span> <span data-ttu-id="6373f-253">추적 결과의 열 및 필터 정보를 .viewsetting 파일에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-253">Save the columns and filter information of a trace result to a .viewsetting file.</span></span>  
  
    -   <span data-ttu-id="6373f-254">열기</span><span class="sxs-lookup"><span data-stu-id="6373f-254">Open.</span></span> <span data-ttu-id="6373f-255">기존 .viewsetting 파일을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-255">Open an existing .viewsetting file.</span></span>  
  
    -   <span data-ttu-id="6373f-256">최근 파일 열기:</span><span class="sxs-lookup"><span data-stu-id="6373f-256">Open recent.</span></span> <span data-ttu-id="6373f-257">최근에 저장한 .viewsetting 파일을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-257">Open a recently saved .viewsetting file.</span></span>  
  
### <a name="copy-or-export-trace-results"></a><span data-ttu-id="6373f-258">추적 결과 복사 또는 내보내기</span><span class="sxs-lookup"><span data-stu-id="6373f-258">Copy or Export Trace Results</span></span>  
 <span data-ttu-id="6373f-259">추적 결과에서 선택한 행으로 셀, 행 및 세부 정보를 복사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-259">You can copy cells, rows, and details to selected rows from your trace results.</span></span> <span data-ttu-id="6373f-260">추적 결과를 다음 대상으로 내보낼 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-260">You can also export your trace results to the following:</span></span>  
  
-   <span data-ttu-id="6373f-261">.XEL 파일</span><span class="sxs-lookup"><span data-stu-id="6373f-261">.XEL file</span></span>  
  
-   <span data-ttu-id="6373f-262">테이블</span><span class="sxs-lookup"><span data-stu-id="6373f-262">table</span></span>  
  
-   <span data-ttu-id="6373f-263">.CSV 파일</span><span class="sxs-lookup"><span data-stu-id="6373f-263">.CSV file</span></span>  
  
 <span data-ttu-id="6373f-264">추적 결과를 복사하려면 셀 또는 행을 선택하고 마우스 오른쪽 단추를 클릭한 다음 **복사** 를 선택하고 **셀**, **행**또는 **자세히**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-264">To copy trace results, select a cell, row, or rows, right click, select **Copy** and then **Cell**, **Row**, or **Details**.</span></span> <span data-ttu-id="6373f-265">확장 이벤트는 최대 1,000개의 행 복사를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-265">Extended Events supports copying up to a maximum of 1000 rows.</span></span>  
  
 <span data-ttu-id="6373f-266">**의** 확장 이벤트 **메뉴 옵션에서** 내보낼 위치 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]를 선택하여 추적 결과를 .XEL 파일, 테이블 또는 .CSV 파일로 내보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-266">You can export trace results to a .XEL file, table, or .CSV file by selecting **Export to** from the **Extended Events** menu option in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
### <a name="view-a-deadlock-graph-and-query-plans"></a><span data-ttu-id="6373f-267">교착 상태 그래프 및 쿼리 계획 보기</span><span class="sxs-lookup"><span data-stu-id="6373f-267">View a Deadlock Graph and Query Plans</span></span>  
 <span data-ttu-id="6373f-268">세부 정보 창에서 **xml_deadlock_report** 에 대한 교착 상태 그래프를 보면 교착 상태 문제를 손쉽게 해결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-268">You can view the deadlock graph for **xml_deadlock_report** in the Details pane to help you troubleshoot deadlocks.</span></span> <span data-ttu-id="6373f-269">다음 이벤트에 대한 쿼리 계획 그래프도 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-269">You can also view query plan graphs for the following events:</span></span>  
  
-   <span data-ttu-id="6373f-270">query_post_compilation_showplan</span><span class="sxs-lookup"><span data-stu-id="6373f-270">query_post_compilation_showplan</span></span>  
  
-   <span data-ttu-id="6373f-271">query_pre_execution_showplan</span><span class="sxs-lookup"><span data-stu-id="6373f-271">query_pre_execution_showplan</span></span>  
  
-   <span data-ttu-id="6373f-272">query_post_execution_showplan</span><span class="sxs-lookup"><span data-stu-id="6373f-272">query_post_execution_showplan</span></span>  
  
 <span data-ttu-id="6373f-273">교착 상태 그래프를 보려면</span><span class="sxs-lookup"><span data-stu-id="6373f-273">To view the deadlock graph:</span></span>  
  
-   <span data-ttu-id="6373f-274">개체 탐색기에서 **관리**, **확장 이벤트**, **세션** 노드를 차례로 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-274">In Object Explorer, expand the **Management**, **Extended Events**, and then **Sessions** nodes.</span></span>  
  
-   <span data-ttu-id="6373f-275">보려는 구성된 교착 상태 이벤트가 포함된 세션을 마우스 오른쪽 단추로 클릭하고 **라이브 데이터 감시**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-275">Right-click the session that contains the configured deadlock event that you want to view, and select **Watch Live Data**.</span></span>  
  
-   <span data-ttu-id="6373f-276">교착 상태 이벤트를 선택하고 세부 정보 창의 **교착 상태** 탭에서 그래프를 봅니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-276">Select the deadlock event and view the graph on the **Deadlock** tab in the Details pane.</span></span>  
  
 <span data-ttu-id="6373f-277">쿼리 계획 그래프를 보려면</span><span class="sxs-lookup"><span data-stu-id="6373f-277">To view query plan graphs:</span></span>  
  
1.  <span data-ttu-id="6373f-278">개체 탐색기에서 **관리**, **확장 이벤트**, **세션** 노드를 차례로 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-278">In Object Explorer, expand the **Management**, **Extended Events**, and then **Sessions** nodes.</span></span>  
  
2.  <span data-ttu-id="6373f-279">보려는 쿼리 계획 그래프(예: query_post_compilation_showplan)가 포함된 세션을 마우스 오른쪽 단추로 클릭한 다음 **라이브 데이터 감시**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-279">Right-click the session that contains the query plan graph that you want to view (for example, query_post_compilation_showplan), and then select **Watch Live Data**.</span></span>  
  
3.  <span data-ttu-id="6373f-280">쿼리 계획 그래프 이벤트(예: query_post_compilation_showplan)를 선택하고 세부 정보 창의 **쿼리 계획** 탭에서 그래프를 봅니다.</span><span class="sxs-lookup"><span data-stu-id="6373f-280">Select the query plan graph event (for example, query_post_compilation_showplan) and view the graph on the **Query plan** tab in the Details pane.</span></span>  
  
  
