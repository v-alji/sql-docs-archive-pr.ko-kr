---
title: 장애 조치(failover) 클러스터 인스턴스 진단 로그 보기 및 읽기 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
ms.assetid: 68074bd5-be9d-4487-a320-5b51ef8e2b2d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 774dc4ec4a02c72420d004909cb7e6ee1b31f3a7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650554"
---
# <a name="view-and-read-failover-cluster-instance-diagnostics-log"></a><span data-ttu-id="45997-102">장애 조치(failover) 클러스터 인스턴스 진단 로그 보기 및 읽기</span><span class="sxs-lookup"><span data-stu-id="45997-102">View and Read Failover Cluster Instance Diagnostics Log</span></span>
  <span data-ttu-id="45997-103">SQL Server 리소스 DLL에 대한 모든 오류 및 경고 이벤트는 Windows 이벤트 로그에 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="45997-103">All critical errors and warning events for the SQL Server Resource DLL are written to the Windows event log.</span></span> <span data-ttu-id="45997-104">[sp_server_diagnostics&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-server-diagnostics-transact-sql) 시스템 저장 프로시저에서 캡처된 SQL Server 관련 진단 정보의 실행 로그는 SQL Server 장애 조치(failover) 클러스터 진단(*SQLDIAG* 로그라고도 함) 로그 파일에 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="45997-104">A running log of the diagnostic information specific to SQL Server is captured by the [sp_server_diagnostics &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-server-diagnostics-transact-sql) system stored procedure and is written to the SQL Server failover cluster diagnostics (also known as the *SQLDIAG* logs) log files.</span></span>  
  
-   <span data-ttu-id="45997-105">**시작하기 전 주의 사항:**  [권장 사항](#Recommendations), [보안](#Security)</span><span class="sxs-lookup"><span data-stu-id="45997-105">**Before you begin:**  [Recommendations](#Recommendations), [Security](#Security)</span></span>  
  
-   <span data-ttu-id="45997-106">**진단 로그를 보려면:**  [SQL Server Management Studio](#SSMSProcedure), [Transact-SQL](#TsqlProcedure)</span><span class="sxs-lookup"><span data-stu-id="45997-106">**To View the Diagnostic Log, using:**  [SQL Server Management Studio](#SSMSProcedure), [Transact-SQL](#TsqlProcedure)</span></span>  
  
-   <span data-ttu-id="45997-107">**진단 로그 설정을 구성하려면:** [Transact-SQL](#TsqlConfigure)</span><span class="sxs-lookup"><span data-stu-id="45997-107">**To Configure Diagnostic Log settings, using:** [Transact-SQL](#TsqlConfigure)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="45997-108">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="45997-108">Before You Begin</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="45997-109">권장 사항</span><span class="sxs-lookup"><span data-stu-id="45997-109">Recommendations</span></span>  
 <span data-ttu-id="45997-110">기본적으로 SQLDIAG는 SQL Server 인스턴스 디렉터리의 로컬 LOG 폴더에 저장 됩니다 (예: ' C_Files\Microsoft SQL Server\MSSQL12. \<InstanceName> ). AlwaysOn FCI (장애 조치 (Failover) 클러스터 인스턴스)를 소유 하는 노드의 \MSSQL\LOG</span><span class="sxs-lookup"><span data-stu-id="45997-110">By default, the SQLDIAG are stored under a local LOG folder of the SQL Server instance directory, for example, 'C\Program Files\Microsoft SQL Server\MSSQL12.\<InstanceName>\MSSQL\LOG' of the owning node of the AlwaysOn Failover Cluster Instance (FCI).</span></span> <span data-ttu-id="45997-111">각 SQLDIAG 로그 파일의 크기는 100MB로 고정됩니다.</span><span class="sxs-lookup"><span data-stu-id="45997-111">The size of each SQLDIAG log file is fixed at 100 MB.</span></span> <span data-ttu-id="45997-112">새 로그에 재활용하기 전에 이러한 로그 파일이 컴퓨터에 10개 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="45997-112">Ten such log files are stored on the computer before they are recycled for new logs.</span></span>  
  
 <span data-ttu-id="45997-113">로그는 확장 이벤트 파일 형식을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="45997-113">The logs use the extended events file format.</span></span> <span data-ttu-id="45997-114">**sys.fn_xe_file_target_read_file** 시스템 함수를 사용하여 확장 이벤트에서 만든 파일을 읽을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45997-114">The **sys.fn_xe_file_target_read_file** system function can be used to read the files that are created by Extended Events.</span></span> <span data-ttu-id="45997-115">행당 하나의 이벤트가 XML 형식으로 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="45997-115">One event, in XML format, is returned per row.</span></span> <span data-ttu-id="45997-116">XML 데이터를 결과 집합으로 구문 분석하려면 시스템 뷰를 쿼리합니다.</span><span class="sxs-lookup"><span data-stu-id="45997-116">Query the system view to parse the XML data as a result-set.</span></span> <span data-ttu-id="45997-117">자세한 내용은 [sys.fn_xe_file_target_read_file&#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-xe-file-target-read-file-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="45997-117">For more information, see [sys.fn_xe_file_target_read_file &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-xe-file-target-read-file-transact-sql).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="45997-118">보안</span><span class="sxs-lookup"><span data-stu-id="45997-118">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="45997-119">권한</span><span class="sxs-lookup"><span data-stu-id="45997-119">Permissions</span></span>  
 <span data-ttu-id="45997-120">**fn_xe_file_target_read_file**을 실행하려면 VIEW SERVER STATE 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="45997-120">VIEW SERVER STATE permission is needed to run **fn_xe_file_target_read_file**.</span></span>  
  
 <span data-ttu-id="45997-121">SQL Server Management Studio를 관리자로 열기</span><span class="sxs-lookup"><span data-stu-id="45997-121">Open SQL Server Management Studio as Administrator</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="45997-122">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="45997-122">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="45997-123">**진단 로그 파일을 보려면:**</span><span class="sxs-lookup"><span data-stu-id="45997-123">**To view the Diagnostic log files:**</span></span>  
  
1.  <span data-ttu-id="45997-124">**파일** 메뉴에서 **열기**, **파일**을 선택한 다음 보려는 진단 로그 파일을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="45997-124">From the **File** menu, select **Open**, **File**, and choose the diagnostic log file you want to view.</span></span>  
  
2.  <span data-ttu-id="45997-125">이벤트가 왼쪽 창에 행으로 표시되며 기본적으로 **이름**및 **타임스탬프** 라는 두 열만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="45997-125">The events are displayed as rows in the right pane, and by default **name**, and **timestamp** are the only two columns displayed.</span></span>  
  
     <span data-ttu-id="45997-126">또한 **ExtendedEvents** 메뉴도 활성화됩니다.</span><span class="sxs-lookup"><span data-stu-id="45997-126">This also activates the **ExtendedEvents** menu.</span></span>  
  
3.  <span data-ttu-id="45997-127">추가 열을 보려면 **ExtendedEvents** 메뉴로 이동하고 **열 선택**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="45997-127">To see more columns, go the **ExtendedEvents** menu, and select **Choose Columns**.</span></span>  
  
     <span data-ttu-id="45997-128">표시할 열을 선택할 수 있는 사용 가능한 열이 포함된 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="45997-128">A dialog box opens with the available columns allowing you to select the columns for display.</span></span>  
  
4.  <span data-ttu-id="45997-129">**ExtendedEvents** 메뉴를 사용하고 **필터** 옵션을 선택하여 이벤트 데이터를 필터링하고 정렬할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45997-129">You can filter, and sort the event data using the **ExtendedEvents** menu and selecting the **Filter** option.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="45997-130">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="45997-130">Using Transact-SQL</span></span>  
 <span data-ttu-id="45997-131">**진단 로그 파일을 보려면:**</span><span class="sxs-lookup"><span data-stu-id="45997-131">**To view the Diagnostic log files:**</span></span>  
  
 <span data-ttu-id="45997-132">SQLDIAG 로그 파일의 모든 로그 항목을 보려면 다음 쿼리를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="45997-132">To view all the log items in the SQLDIAG log file, use the following query:</span></span>  
  
```  
SELECT  
xml_data.value('(event/@name)[1]','varchar(max)') AS 'Name'  
,xml_data.value('(event/@package)[1]','varchar(max)') AS 'Package'  
,xml_data.value('(event/@timestamp)[1]','datetime') AS 'Time'  
,xml_data.value('(event/data[@name=''state'']/value)[1]','int') AS 'State'  
,xml_data.value('(event/data[@name=''state_desc'']/text)[1]','varchar(max)') AS 'State Description'  
,xml_data.value('(event/data[@name=''failure_condition_level'']/value)[1]','int') AS 'Failure Conditions'  
,xml_data.value('(event/data[@name=''node_name'']/value)[1]','varchar(max)') AS 'Node_Name'  
,xml_data.value('(event/data[@name=''instancename'']/value)[1]','varchar(max)') AS 'Instance Name'  
,xml_data.value('(event/data[@name=''creation time'']/value)[1]','datetime') AS 'Creation Time'  
,xml_data.value('(event/data[@name=''component'']/value)[1]','varchar(max)') AS 'Component'  
,xml_data.value('(event/data[@name=''data'']/value)[1]','varchar(max)') AS 'Data'  
,xml_data.value('(event/data[@name=''info'']/value)[1]','varchar(max)') AS 'Info'  
FROM  
 ( SELECT object_name AS 'event'  
  ,CONVERT(xml,event_data) AS 'xml_data'  
  FROM sys.fn_xe_file_target_read_file('C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Log\SQLNODE1_MSSQLSERVER_SQLDIAG_0_129936003752530000.xel',NULL,NULL,NULL)   
)   
AS XEventData  
ORDER BY Time;  
  
```  
  
> [!NOTE]  
>  <span data-ttu-id="45997-133">WHERE 절을 사용하여 특정 구성 요소 또는 상태에 대한 결과를 필터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45997-133">You can filter the results for specific components or state using the WHERE clause.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlConfigure"></a> <span data-ttu-id="45997-134">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="45997-134">Using Transact-SQL</span></span>  
 <span data-ttu-id="45997-135">**진단 로그 속성을 구성하려면**</span><span class="sxs-lookup"><span data-stu-id="45997-135">**To configure the Diagnostic Log Properties**</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="45997-136">이 절차에 대한 예는 이 섹션의 뒷부분에 나오는 [예제(Transact-SQL)](#TsqlExample)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="45997-136">For an example of this procedure, see [Example (Transact-SQL)](#TsqlExample), later in this section.</span></span>  
  
 <span data-ttu-id="45997-137">DDL (데이터 정의 언어) 문을 사용 하 여 `ALTER SERVER CONFIGURATION` [Sp_server_diagnostics &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-server-diagnostics-transact-sql) 프로시저에서 캡처한 진단 데이터의 로깅을 시작 하거나 중지 하 고 로그 파일 롤오버 수, 로그 파일 크기 및 파일 위치와 같은 SQLDIAG 로그 구성 매개 변수를 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45997-137">Using the Data Definition Language (DDL) statement, `ALTER SERVER CONFIGURATION`, you can start or stop logging diagnostic data captured by the [sp_server_diagnostics &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-server-diagnostics-transact-sql) procedure, and set SQLDIAG log configuration parameters such as the log file rollover count, log file size, and file location.</span></span> <span data-ttu-id="45997-138">구문에 대한 자세한 내용은 [Setting diagnostic log options](/sql/t-sql/statements/alter-server-configuration-transact-sql#Diagnostic)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="45997-138">For syntax details, see [Setting diagnostic log options](/sql/t-sql/statements/alter-server-configuration-transact-sql#Diagnostic).</span></span>  
  
###  <a name="examples-transact-sql"></a><a name="ConfigTsqlExample"></a> <span data-ttu-id="45997-139">예(Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="45997-139">Examples (Transact-SQL)</span></span>  
  
####  <a name="setting-diagnostic-log-options"></a><a name="TsqlExample"></a> <span data-ttu-id="45997-140">Setting diagnostic log options</span><span class="sxs-lookup"><span data-stu-id="45997-140">Setting diagnostic log options</span></span>  
 <span data-ttu-id="45997-141">이 섹션의 예에서는 진단 로그 옵션 값을 설정하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="45997-141">The examples in this section show how to set the values for the diagnostic log option.</span></span>  
  
##### <a name="a-starting-diagnostic-logging"></a><span data-ttu-id="45997-142">A.</span><span class="sxs-lookup"><span data-stu-id="45997-142">A.</span></span> <span data-ttu-id="45997-143">진단 로깅 시작</span><span class="sxs-lookup"><span data-stu-id="45997-143">Starting diagnostic logging</span></span>  
 <span data-ttu-id="45997-144">다음 예에서는 진단 데이터의 로깅을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="45997-144">The following example starts the logging of diagnostic data.</span></span>  
  
```  
ALTER SERVER CONFIGURATION SET DIAGNOSTICS LOG ON;  
```  
  
##### <a name="b-stopping-diagnostic-logging"></a><span data-ttu-id="45997-145">B.</span><span class="sxs-lookup"><span data-stu-id="45997-145">B.</span></span> <span data-ttu-id="45997-146">진단 로깅 중지</span><span class="sxs-lookup"><span data-stu-id="45997-146">Stopping diagnostic logging</span></span>  
 <span data-ttu-id="45997-147">다음 예에서는 진단 데이터의 로깅을 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="45997-147">The following example stops the logging of diagnostic data.</span></span>  
  
```  
ALTER SERVER CONFIGURATION SET DIAGNOSTICS LOG OFF;  
```  
  
##### <a name="c-specifying-the-location-of-the-diagnostic-logs"></a><span data-ttu-id="45997-148">C.</span><span class="sxs-lookup"><span data-stu-id="45997-148">C.</span></span> <span data-ttu-id="45997-149">진단 로그의 위치 지정</span><span class="sxs-lookup"><span data-stu-id="45997-149">Specifying the location of the diagnostic logs</span></span>  
 <span data-ttu-id="45997-150">다음 예에서는 진단 로그의 위치를 지정된 파일 경로로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="45997-150">The following example sets the location of the diagnostic logs to the specified file path.</span></span>  
  
```  
ALTER SERVER CONFIGURATION  
SET DIAGNOSTICS LOG PATH = 'C:\logs';  
```  
  
##### <a name="d-specifying-the-maximum-size-of-each-diagnostic-log"></a><span data-ttu-id="45997-151">D.</span><span class="sxs-lookup"><span data-stu-id="45997-151">D.</span></span> <span data-ttu-id="45997-152">각 진단 로그의 최대 크기 지정</span><span class="sxs-lookup"><span data-stu-id="45997-152">Specifying the maximum size of each diagnostic log</span></span>  
 <span data-ttu-id="45997-153">다음 예에서는 각 진단 로그의 최대 크기를 10MB로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="45997-153">The following example set the maximum size of each diagnostic log to 10 megabytes.</span></span>  
  
```  
ALTER SERVER CONFIGURATION   
SET DIAGNOSTICS LOG MAX_SIZE = 10 MB;  
```  
  
## <a name="see-also"></a><span data-ttu-id="45997-154">참고 항목</span><span class="sxs-lookup"><span data-stu-id="45997-154">See Also</span></span>  
 [<span data-ttu-id="45997-155">Failover Policy for Failover Cluster Instances</span><span class="sxs-lookup"><span data-stu-id="45997-155">Failover Policy for Failover Cluster Instances</span></span>](failover-policy-for-failover-cluster-instances.md)  
  
  
