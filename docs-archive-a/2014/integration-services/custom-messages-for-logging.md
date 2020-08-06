---
title: 로깅에 대 한 사용자 지정 메시지 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- logs [Integration Services], custom
- writing log entries
- SSIS packages, logs
- custom messages for logging [Integration Services]
ms.assetid: 3c74bba9-02b7-4bf5-bad5-19278b680730
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 2b9f450c74ef6d46876adfde45729c71b3262449
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651207"
---
# <a name="custom-messages-for-logging"></a><span data-ttu-id="c1f40-102">로깅할 메시지 사용자 지정</span><span class="sxs-lookup"><span data-stu-id="c1f40-102">Custom Messages for Logging</span></span>
  [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]<span data-ttu-id="c1f40-103">는 패키지 및 여러 태스크에 대한 로그 항목 기록을 위해 다양한 사용자 지정 이벤트 집합을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="c1f40-103">provides a rich set of custom events for writing log entries for packages and many tasks.</span></span> <span data-ttu-id="c1f40-104">이러한 항목을 사용하면 나중에 분석할 수 있도록 미리 정의된 이벤트나 사용자가 정의한 메시지를 기록하여 실행 진행률, 결과 및 문제에 대한 세부 정보를 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1f40-104">You can use these entries to save detailed information about execution progress, results, and problems by recording predefined events or user-defined messages for later analysis.</span></span> <span data-ttu-id="c1f40-105">예를 들면 대량 삽입이 시작되고 끝나는 시간을 기록하여 패키지 실행 시 성능 문제를 식별할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1f40-105">For example, you can record when a bulk insert begins and ends to identify performance issues when the package runs.</span></span>  
  
 <span data-ttu-id="c1f40-106">사용자 지정 로그 항목은 패키지 및 모든 컨테이너와 태스크에 사용할 수 있는 표준 로깅 이벤트 집합과는 다른 항목 집합입니다.</span><span class="sxs-lookup"><span data-stu-id="c1f40-106">The custom log entries are a different set of entries than the set of standard logging events that are available for packages and all containers and tasks.</span></span> <span data-ttu-id="c1f40-107">사용자 지정 로그 항목은 패키지의 특정 태스크에 대한 유용한 정보를 캡처하도록 조정되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1f40-107">The custom log entries are tailored to capture useful information about a specific task in a package.</span></span> <span data-ttu-id="c1f40-108">예를 들어 SQL 실행 태스크에 대한 사용자 지정 로그 항목 중 하나는 해당 태스크에서 실행한 SQL 문을 로그에 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="c1f40-108">For example, one of the custom log entries for the Execute SQL task records the SQL statement that the task executes in the log.</span></span>  
  
 <span data-ttu-id="c1f40-109">모든 로그 항목에는 패키지가 시작되고 끝날 때 자동으로 기록되는 로그 항목을 비롯하여 날짜 및 시간 정보가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="c1f40-109">All log entries include date and time information, including the log entries that are automatically written when a package begins and finishes.</span></span> <span data-ttu-id="c1f40-110">로그 이벤트는 대부분 여러 항목을 로그에 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="c1f40-110">Many of the log events write multiple entries to the log.</span></span> <span data-ttu-id="c1f40-111">일반적으로 이벤트에 여러 단계가 있을 경우 이러한 기록이 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="c1f40-111">This typically occurs when the event has different phases.</span></span> <span data-ttu-id="c1f40-112">예를 들어 `ExecuteSQLExecutingQuery` 로그 이벤트는 3개의 항목을 기록합니다. 즉, 태스크에서 데이터베이스에 대한 연결을 설정한 후, 태스크에서 SQL 문 준비를 시작한 후, SQL 문 실행이 완료된 후에 각각 하나씩의 항목을 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="c1f40-112">For example, the `ExecuteSQLExecutingQuery` log event writes three entries: one entry after the task acquires a connection to the database, another after the task starts to prepare the SQL statement, and one more after the execution of the SQL statement is completed.</span></span>  
  
 <span data-ttu-id="c1f40-113">다음 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 개체에는 사용자 지정 로그 항목이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1f40-113">The following [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] objects have custom log entries:</span></span>  
  
 [<span data-ttu-id="c1f40-114">패키지</span><span class="sxs-lookup"><span data-stu-id="c1f40-114">Package</span></span>](#Package)  
  
 [<span data-ttu-id="c1f40-115">대량 삽입 태스크</span><span class="sxs-lookup"><span data-stu-id="c1f40-115">Bulk Insert Task</span></span>](#BulkInsert)  
  
 [<span data-ttu-id="c1f40-116">데이터 흐름 태스크</span><span class="sxs-lookup"><span data-stu-id="c1f40-116">Data Flow Task</span></span>](#DataFlow)  
  
 [<span data-ttu-id="c1f40-117">DTS 2000 실행 태스크</span><span class="sxs-lookup"><span data-stu-id="c1f40-117">Execute DTS 2000 Task</span></span>](#ExecuteDTS200)  
  
 [<span data-ttu-id="c1f40-118">프로세스 실행 태스크</span><span class="sxs-lookup"><span data-stu-id="c1f40-118">Execute Process Task</span></span>](#ExecuteProcess)  
  
 [<span data-ttu-id="c1f40-119">SQL 실행 태스크</span><span class="sxs-lookup"><span data-stu-id="c1f40-119">Execute SQL Task</span></span>](#ExecuteSQL)  
  
 [<span data-ttu-id="c1f40-120">파일 시스템 태스크</span><span class="sxs-lookup"><span data-stu-id="c1f40-120">File System Task</span></span>](#FileSystem)  
  
 [<span data-ttu-id="c1f40-121">FTP 태스크</span><span class="sxs-lookup"><span data-stu-id="c1f40-121">FTP Task</span></span>](#FTP)  
  
 [<span data-ttu-id="c1f40-122">메시지 큐 태스크</span><span class="sxs-lookup"><span data-stu-id="c1f40-122">Message Queue Task</span></span>](#MessageQueue)  
  
 [<span data-ttu-id="c1f40-123">스크립트 태스크</span><span class="sxs-lookup"><span data-stu-id="c1f40-123">Script Task</span></span>](#Script)  
  
 [<span data-ttu-id="c1f40-124">메일 보내기 태스크</span><span class="sxs-lookup"><span data-stu-id="c1f40-124">Send Mail Task</span></span>](#SendMail)  
  
 [<span data-ttu-id="c1f40-125">데이터베이스 전송 태스크</span><span class="sxs-lookup"><span data-stu-id="c1f40-125">Transfer Database Task</span></span>](#TransferDatabase)  
  
 [<span data-ttu-id="c1f40-126">오류 메시지 전송 태스크</span><span class="sxs-lookup"><span data-stu-id="c1f40-126">Transfer Error Messages Task</span></span>](#TransferErrorMessages)  
  
 [<span data-ttu-id="c1f40-127">작업 전송 태스크</span><span class="sxs-lookup"><span data-stu-id="c1f40-127">Transfer Jobs Task</span></span>](#TransferJobs)  
  
 [<span data-ttu-id="c1f40-128">로그인 전송 태스크</span><span class="sxs-lookup"><span data-stu-id="c1f40-128">Transfer Logins Task</span></span>](#TransferLogins)  
  
 [<span data-ttu-id="c1f40-129">master 저장 프로시저 전송 태스크</span><span class="sxs-lookup"><span data-stu-id="c1f40-129">Transfer Master Stored Procedures Task</span></span>](#TransferMasterStoredProcedures)  
  
 [<span data-ttu-id="c1f40-130">SQL Server 개체 전송 태스크</span><span class="sxs-lookup"><span data-stu-id="c1f40-130">Transfer SQL Server Objects Task</span></span>](#TransferSQLServerObjects)  
  
 [<span data-ttu-id="c1f40-131">웹 서비스 태스크</span><span class="sxs-lookup"><span data-stu-id="c1f40-131">Web Services Task</span></span>](#WebServices)  
  
 [<span data-ttu-id="c1f40-132">WMI 데이터 판독기 태스크</span><span class="sxs-lookup"><span data-stu-id="c1f40-132">WMI Data Reader Task</span></span>](#WMIDataReader)  
  
 [<span data-ttu-id="c1f40-133">WMI 이벤트 감시자 태스크</span><span class="sxs-lookup"><span data-stu-id="c1f40-133">WMI Event Watcher Task</span></span>](#WMIEventWatcher)  
  
 [<span data-ttu-id="c1f40-134">XML 태스크</span><span class="sxs-lookup"><span data-stu-id="c1f40-134">XML Task</span></span>](#XML)  
  
## <a name="log-entries"></a><span data-ttu-id="c1f40-135">로그 항목</span><span class="sxs-lookup"><span data-stu-id="c1f40-135">Log Entries</span></span>  
  
###  <a name="package"></a><a name="Package"></a> <span data-ttu-id="c1f40-136">패키지</span><span class="sxs-lookup"><span data-stu-id="c1f40-136">Package</span></span>  
 <span data-ttu-id="c1f40-137">다음 표에서는 패키지에 대한 사용자 지정 로그 항목을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="c1f40-137">The following table lists the custom log entries for packages.</span></span>  
  
|<span data-ttu-id="c1f40-138">로그 항목</span><span class="sxs-lookup"><span data-stu-id="c1f40-138">Log entry</span></span>|<span data-ttu-id="c1f40-139">Description</span><span class="sxs-lookup"><span data-stu-id="c1f40-139">Description</span></span>|  
|---------------|-----------------|  
|`PackageStart`|<span data-ttu-id="c1f40-140">패키지 실행이 시작되었음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c1f40-140">Indicates that the package began to run.</span></span><br /><br /> <span data-ttu-id="c1f40-141">참고: 이 로그 항목은 로그에 자동으로 기록되며</span><span class="sxs-lookup"><span data-stu-id="c1f40-141">Note: This log entry is automatically written to the log.</span></span> <span data-ttu-id="c1f40-142">제외할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c1f40-142">You cannot exclude it.</span></span>|  
|`PackageEnd`|<span data-ttu-id="c1f40-143">패키지가 완료되었음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c1f40-143">Indicates that the package completed.</span></span><br /><br /> <span data-ttu-id="c1f40-144">참고: 이 로그 항목은 로그에 자동으로 기록되며</span><span class="sxs-lookup"><span data-stu-id="c1f40-144">Note: This log entry is automatically written to the log.</span></span> <span data-ttu-id="c1f40-145">제외할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c1f40-145">You cannot exclude it.</span></span>|  
|`Diagnostic`|<span data-ttu-id="c1f40-146">동시에 실행될 수 있는 실행 파일 수처럼 패키지 실행에 영향을 주는 시스템 구성에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="c1f40-146">Provides information about the system configuration that affects package execution such as the number executables that can be run concurrently.</span></span><br /><br /> <span data-ttu-id="c1f40-147">`Diagnostic` 로그 항목에는 외부 데이터 공급자에 대한 호출 전후 항목도 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="c1f40-147">The `Diagnostic` log entry also includes before and after entries for calls to external data providers.</span></span> <span data-ttu-id="c1f40-148">자세한 내용은 [패키지 연결 문제 해결 도구](troubleshooting/troubleshooting-tools-for-package-connectivity.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c1f40-148">For more information, see [Troubleshooting Tools Package Connectivity](troubleshooting/troubleshooting-tools-for-package-connectivity.md).</span></span>|  
  
###  <a name="bulk-insert-task"></a><a name="BulkInsert"></a> <span data-ttu-id="c1f40-149">대량 삽입 태스크</span><span class="sxs-lookup"><span data-stu-id="c1f40-149">Bulk Insert Task</span></span>  
 <span data-ttu-id="c1f40-150">다음 표에서는 대량 삽입 태스크에 대한 사용자 지정 로그 항목을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="c1f40-150">The following table lists the custom log entries for the Bulk Insert task.</span></span>  
  
|<span data-ttu-id="c1f40-151">로그 항목</span><span class="sxs-lookup"><span data-stu-id="c1f40-151">Log entry</span></span>|<span data-ttu-id="c1f40-152">Description</span><span class="sxs-lookup"><span data-stu-id="c1f40-152">Description</span></span>|  
|---------------|-----------------|  
|`DTSBulkInsertTaskBegin`|<span data-ttu-id="c1f40-153">대량 삽입이 시작되었음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c1f40-153">Indicates that the bulk insert began.</span></span>|  
|`DTSBulkInsertTaskEnd`|<span data-ttu-id="c1f40-154">대량 삽입이 완료되었음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c1f40-154">Indicates that the bulk insert finished.</span></span>|  
|`DTSBulkInsertTaskInfos`|<span data-ttu-id="c1f40-155">태스크에 대한 설명 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="c1f40-155">Provides descriptive information about the task.</span></span>|  
  
###  <a name="data-flow-task"></a><a name="DataFlow"></a> <span data-ttu-id="c1f40-156">Data Flow Task</span><span class="sxs-lookup"><span data-stu-id="c1f40-156">Data Flow Task</span></span>  
 <span data-ttu-id="c1f40-157">다음 표에서는 데이터 흐름 태스크에 대한 사용자 지정 로그 항목을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="c1f40-157">The following table lists the custom log entries for the Data Flow task.</span></span>  
  
|<span data-ttu-id="c1f40-158">로그 항목</span><span class="sxs-lookup"><span data-stu-id="c1f40-158">Log entry</span></span>|<span data-ttu-id="c1f40-159">Description</span><span class="sxs-lookup"><span data-stu-id="c1f40-159">Description</span></span>|  
|---------------|-----------------|  
|`BufferSizeTuning`|<span data-ttu-id="c1f40-160">데이터 흐름 태스크로 인해 버퍼 크기가 변경되었음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c1f40-160">Indicates that the Data Flow task changed the size of the buffer.</span></span> <span data-ttu-id="c1f40-161">로그 항목은 크기가 변경된 이유를 설명하고 임시 새 버퍼 크기를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="c1f40-161">The log entry describes the reasons for the size change and lists the temporary new buffer size.</span></span>|  
|`OnPipelinePostEndOfRowset`|<span data-ttu-id="c1f40-162">구성 요소에 `ProcessInput` 메서드의 마지막 호출로 설정된 해당 행 집합 끝 신호를 제공했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c1f40-162">Denotes that a component has been given its end-of-rowset signal, which is set by the last call of the `ProcessInput` method.</span></span> <span data-ttu-id="c1f40-163">입력을 처리하는 데이터 흐름의 각 구성 요소에 대한 항목이 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="c1f40-163">An entry is written for each component in the data flow that processes input.</span></span> <span data-ttu-id="c1f40-164">이 항목은 구성 요소의 이름을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="c1f40-164">The entry includes the name of the component.</span></span>|  
|`OnPipelinePostPrimeOutput`|<span data-ttu-id="c1f40-165">구성 요소가 `PrimeOutput` 메서드에 대한 마지막 호출을 완료했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c1f40-165">Indicates that the component has completed its last call to the `PrimeOutput` method.</span></span> <span data-ttu-id="c1f40-166">데이터 흐름에 따라 여러 로그 항목이 기록될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1f40-166">Depending on the data flow, multiple log entries may be written.</span></span> <span data-ttu-id="c1f40-167">구성 요소가 원본일 경우에는 구성 요소가 행 처리를 완료했음을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="c1f40-167">If the component is a source, this means that the component has finished processing rows.</span></span>|  
|`OnPipelinePreEndOfRowset`|<span data-ttu-id="c1f40-168">구성 요소가 `ProcessInput` 메서드의 마지막 호출로 설정된 해당 행 집합 끝 신호를 수신하려고 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c1f40-168">Indicates that a component is about to receive its end-of-rowset signal, which is set by the last call of the `ProcessInput` method.</span></span> <span data-ttu-id="c1f40-169">입력을 처리하는 데이터 흐름의 각 구성 요소에 대한 항목이 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="c1f40-169">An entry is written for each component in the data flow that processes input.</span></span> <span data-ttu-id="c1f40-170">이 항목은 구성 요소의 이름을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="c1f40-170">The entry includes the name of the component.</span></span>|  
|`OnPipelinePrePrimeOutput`|<span data-ttu-id="c1f40-171">구성 요소가 `PrimeOutput` 메서드에서 해당 호출을 수신하려고 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c1f40-171">Indicates that the component is about to receive its call from the `PrimeOutput` method.</span></span> <span data-ttu-id="c1f40-172">데이터 흐름에 따라 여러 로그 항목이 기록될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1f40-172">Depending on the data flow, multiple log entries may be written.</span></span>|  
|`OnPipelineRowsSent`|<span data-ttu-id="c1f40-173">`ProcessInput` 메서드 호출로 구성 요소 입력에 제공한 행 수를 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="c1f40-173">Reports the number of rows provided to a component input by a call to the `ProcessInput` method.</span></span> <span data-ttu-id="c1f40-174">이 로그 항목은 구성 요소 이름을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="c1f40-174">The log entry includes the component name.</span></span>|  
|`PipelineBufferLeak`|<span data-ttu-id="c1f40-175">버퍼 관리자가 없어진 후에 버퍼를 활성 상태로 유지하는 모든 구성 요소에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="c1f40-175">Provides information about any component that kept buffers alive after the buffer manager goes away.</span></span> <span data-ttu-id="c1f40-176">즉, 버퍼 리소스가 릴리스되지 않았기 때문에 메모리 손실이 발생할 수 있음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c1f40-176">This means that buffers resources were not released and may cause memory leaks.</span></span> <span data-ttu-id="c1f40-177">로그 항목은 구성 요소 이름과 버퍼 ID를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="c1f40-177">The log entry provides the name of the component and the ID of the buffer.</span></span>|  
|`PipelineExecutionPlan`|<span data-ttu-id="c1f40-178">데이터 흐름의 실행 계획을 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="c1f40-178">Reports the execution plan of the data flow.</span></span> <span data-ttu-id="c1f40-179">버퍼를 구성 요소로 전송하는 방법에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="c1f40-179">It provides information about how buffers will be sent to components.</span></span> <span data-ttu-id="c1f40-180">이 정보는 PipelineExecutionTrees 항목과 함께 태스크에서 발생하는 사항에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="c1f40-180">This information, in combination with the PipelineExecutionTrees entry, describes what is occurring in the task.</span></span>|  
|`PipelineExecutionTrees`|<span data-ttu-id="c1f40-181">데이터 흐름에서 레이아웃 실행 트리를 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="c1f40-181">Reports the execution trees of the layout in the data flow.</span></span> <span data-ttu-id="c1f40-182">데이터 흐름 엔진 스케줄러는 이 트리를 사용하여 데이터 흐름의 실행 계획을 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="c1f40-182">The scheduler of the data flow engine use the trees to build the execution plan of the data flow.</span></span>|  
|`PipelineInitialization`|<span data-ttu-id="c1f40-183">태스크에 대한 초기화 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="c1f40-183">Provides initialization information about the task.</span></span> <span data-ttu-id="c1f40-184">이 정보에 BLOB 데이터의 임시 스토리지에 사용할 디렉터리, 기본 버퍼 크기 및 버퍼의 행 수가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="c1f40-184">This information includes the directories to use for temporary storage of BLOB data, the default buffer size, and the number of rows in a buffer.</span></span> <span data-ttu-id="c1f40-185">데이터 흐름 태스크의 구성에 따라 여러 로그 항목이 기록될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1f40-185">Depending on the configuration of the Data Flow task, multiple log entries may be written.</span></span>|  
  
###  <a name="execute-dts-2000-task"></a><a name="ExecuteDTS200"></a> <span data-ttu-id="c1f40-186">DTS 2000 실행 태스크</span><span class="sxs-lookup"><span data-stu-id="c1f40-186">Execute DTS 2000 Task</span></span>  
 <span data-ttu-id="c1f40-187">다음 표에서는 DTS 2000 실행 태스크에 대한 사용자 지정 로그 항목을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="c1f40-187">The following table lists the custom log entries for the Execute DTS 2000 task.</span></span>  
  
|<span data-ttu-id="c1f40-188">로그 항목</span><span class="sxs-lookup"><span data-stu-id="c1f40-188">Log entry</span></span>|<span data-ttu-id="c1f40-189">Description</span><span class="sxs-lookup"><span data-stu-id="c1f40-189">Description</span></span>|  
|---------------|-----------------|  
|`ExecuteDTS80PackageTaskBegin`|<span data-ttu-id="c1f40-190">태스크에서 DTS 2000 패키지 실행을 시작했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c1f40-190">Indicates that the task began to run a DTS 2000 package.</span></span>|  
|`ExecuteDTS80PackageTaskEnd`|<span data-ttu-id="c1f40-191">태스크가 완료되었음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c1f40-191">Indicates that the task finished.</span></span><br /><br /> <span data-ttu-id="c1f40-192">참고: DTS 2000 패키지는 태스크가 끝난 후에도 계속 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="c1f40-192">Note: The DTS 2000 package may continue to run after the task ends.</span></span>|  
|`ExecuteDTS80PackageTaskTaskInfo`|<span data-ttu-id="c1f40-193">태스크에 대한 설명 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="c1f40-193">Provides descriptive information about the task.</span></span>|  
|`ExecuteDTS80PackageTaskTaskResult`|<span data-ttu-id="c1f40-194">태스크에서 실행한 DTS 2000 패키지의 실행 결과를 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="c1f40-194">Reports the execution result of the DTS 2000 package that the task ran.</span></span>|  
  
###  <a name="execute-process-task"></a><a name="ExecuteProcess"></a> <span data-ttu-id="c1f40-195">프로세스 실행 태스크</span><span class="sxs-lookup"><span data-stu-id="c1f40-195">Execute Process Task</span></span>  
 <span data-ttu-id="c1f40-196">다음 표에서는 프로세스 실행 태스크에 대한 사용자 지정 로그 항목을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="c1f40-196">The following table lists the custom log entries for the Execute Process task.</span></span>  
  
|<span data-ttu-id="c1f40-197">로그 항목</span><span class="sxs-lookup"><span data-stu-id="c1f40-197">Log entry</span></span>|<span data-ttu-id="c1f40-198">Description</span><span class="sxs-lookup"><span data-stu-id="c1f40-198">Description</span></span>|  
|---------------|-----------------|  
|`ExecuteProcessExecutingProcess`|<span data-ttu-id="c1f40-199">태스크에서 실행하도록 구성된 실행 파일의 실행 프로세스에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="c1f40-199">Provides information about the process of running the executable that the task is configured to run.</span></span><br /><br /> <span data-ttu-id="c1f40-200">두 개의 로그 항목이 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="c1f40-200">Two log entries are written.</span></span> <span data-ttu-id="c1f40-201">한 항목에는 태스크가 실행하는 실행 파일의 이름과 위치에 대한 정보가 들어 있고 다른 항목은 실행 파일의 종료를 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="c1f40-201">One contains information about the name and location of the executable that the task runs, and the other records the exit from the executable.</span></span>|  
|`ExecuteProcessVariableRouting`|<span data-ttu-id="c1f40-202">실행 파일의 입력 및 출력으로 라우팅되는 변수에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="c1f40-202">Provides information about which variables are routed to the input and outputs of the executable.</span></span> <span data-ttu-id="c1f40-203">stdin(입력), stdout(출력) 및 stderr(오류 출력)에 대한 로그 항목이 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="c1f40-203">Log entries are written for stdin (the input), stdout (the output), and stderr (the error output).</span></span>|  
  
###  <a name="execute-sql-task"></a><a name="ExecuteSQL"></a> <span data-ttu-id="c1f40-204">SQL 실행 태스크</span><span class="sxs-lookup"><span data-stu-id="c1f40-204">Execute SQL Task</span></span>  
 <span data-ttu-id="c1f40-205">다음 표에서는 SQL 실행 태스크에 대한 사용자 지정 로그 항목을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="c1f40-205">The following table describes the custom log entry for the Execute SQL task.</span></span>  
  
|<span data-ttu-id="c1f40-206">로그 항목</span><span class="sxs-lookup"><span data-stu-id="c1f40-206">Log entry</span></span>|<span data-ttu-id="c1f40-207">Description</span><span class="sxs-lookup"><span data-stu-id="c1f40-207">Description</span></span>|  
|---------------|-----------------|  
|`ExecuteSQLExecutingQuery`|<span data-ttu-id="c1f40-208">SQL 문의 실행 단계에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="c1f40-208">Provides information about the execution phases of the SQL statement.</span></span> <span data-ttu-id="c1f40-209">로그 항목은 태스크에서 데이터베이스에 대한 연결을 설정할 때, 태스크에서 SQL 문 준비를 시작할 때 또는 SQL 문 실행이 완료된 후에 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="c1f40-209">Log entries are written when the task acquires connection to the database, when the task starts to prepare the SQL statement, and after the execution of the SQL statement is completed.</span></span> <span data-ttu-id="c1f40-210">준비 단계에 대한 로그 항목은 태스크에서 사용하는 SQL 문을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="c1f40-210">The log entry for the prepare phase includes the SQL statement that the task uses.</span></span>|  
  
###  <a name="file-system-task"></a><a name="FileSystem"></a> <span data-ttu-id="c1f40-211">파일 시스템 태스크</span><span class="sxs-lookup"><span data-stu-id="c1f40-211">File System Task</span></span>  
 <span data-ttu-id="c1f40-212">다음 표에서는 파일 시스템 태스크에 대한 사용자 지정 로그 항목을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="c1f40-212">The following table describes the custom log entry for the File System task.</span></span>  
  
|<span data-ttu-id="c1f40-213">로그 항목</span><span class="sxs-lookup"><span data-stu-id="c1f40-213">Log entry</span></span>|<span data-ttu-id="c1f40-214">Description</span><span class="sxs-lookup"><span data-stu-id="c1f40-214">Description</span></span>|  
|---------------|-----------------|  
|`FileSystemOperation`|<span data-ttu-id="c1f40-215">태스크에서 수행하는 작업을 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="c1f40-215">Reports the operation that the task performs.</span></span> <span data-ttu-id="c1f40-216">이 로그 항목은 파일 시스템 작업이 시작될 때 기록되며 원본 및 대상에 대한 정보를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="c1f40-216">The log entry is written when the file system operation starts and includes information about the source and destination.</span></span>|  
  
###  <a name="ftp-task"></a><a name="FTP"></a> <span data-ttu-id="c1f40-217">FTP 태스크</span><span class="sxs-lookup"><span data-stu-id="c1f40-217">FTP Task</span></span>  
 <span data-ttu-id="c1f40-218">다음 표에서는 FTP 태스크에 대한 사용자 지정 로그 항목을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="c1f40-218">The following table lists the custom log entries for the FTP task.</span></span>  
  
|<span data-ttu-id="c1f40-219">로그 항목</span><span class="sxs-lookup"><span data-stu-id="c1f40-219">Log entry</span></span>|<span data-ttu-id="c1f40-220">Description</span><span class="sxs-lookup"><span data-stu-id="c1f40-220">Description</span></span>|  
|---------------|-----------------|  
|`FTPConnectingToServer`|<span data-ttu-id="c1f40-221">태스크에서 FTP 서버에 대한 연결을 시작했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c1f40-221">Indicates that the task initiated a connection to the FTP server.</span></span>|  
|`FTPOperation`|<span data-ttu-id="c1f40-222">태스크에서 수행하는 FTP 작업의 시작 부분과 유형을 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="c1f40-222">Reports the beginning of and the type of FTP operation that the task performs.</span></span>|  
  
###  <a name="message-queue-task"></a><a name="MessageQueue"></a> <span data-ttu-id="c1f40-223">메시지 큐 태스크</span><span class="sxs-lookup"><span data-stu-id="c1f40-223">Message Queue Task</span></span>  
 <span data-ttu-id="c1f40-224">다음 표에서는 메시지 큐 태스크에 대한 사용자 지정 로그 항목을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="c1f40-224">The following table lists the custom log entries for the Message Queue task.</span></span>  
  
|<span data-ttu-id="c1f40-225">로그 항목</span><span class="sxs-lookup"><span data-stu-id="c1f40-225">Log entry</span></span>|<span data-ttu-id="c1f40-226">Description</span><span class="sxs-lookup"><span data-stu-id="c1f40-226">Description</span></span>|  
|---------------|-----------------|  
|`MSMQAfterOpen`|<span data-ttu-id="c1f40-227">태스크에서 메시지 큐 열기를 완료했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c1f40-227">Indicates that the task finished opening the message queue.</span></span>|  
|`MSMQBeforeOpen`|<span data-ttu-id="c1f40-228">태스크에서 메시지 큐 열기를 시작했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c1f40-228">Indicates that the task began to open the message queue.</span></span>|  
|`MSMQBeginReceive`|<span data-ttu-id="c1f40-229">태스크에서 메시지 받기를 시작했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c1f40-229">Indicates that the task began to receive a message.</span></span>|  
|`MSMQBeginSend`|<span data-ttu-id="c1f40-230">태스크에서 메시지 보내기를 시작했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c1f40-230">Indicates that the task began to send a message.</span></span>|  
|`MSMQEndReceive`|<span data-ttu-id="c1f40-231">태스크에서 메시지 받기를 완료했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c1f40-231">Indicates that the task finished receiving a message.</span></span>|  
|`MSMQEndSend`|<span data-ttu-id="c1f40-232">태스크에서 메시지 보내기를 완료했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c1f40-232">Indicates that the task finished sending a message</span></span>|  
|`MSMQTaskInfo`|<span data-ttu-id="c1f40-233">태스크에 대한 설명 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="c1f40-233">Provides descriptive information about the task.</span></span>|  
|`MSMQTaskTimeOut`|<span data-ttu-id="c1f40-234">태스크 시간이 초과되었음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c1f40-234">Indicates that the task timed out.</span></span>|  
  
###  <a name="script-task"></a><a name="Script"></a> <span data-ttu-id="c1f40-235">스크립트 태스크</span><span class="sxs-lookup"><span data-stu-id="c1f40-235">Script Task</span></span>  
 <span data-ttu-id="c1f40-236">다음 표에서는 스크립트 태스크에 대한 사용자 지정 로그 항목을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="c1f40-236">The following table describes the custom log entry for the Script task.</span></span>  
  
|<span data-ttu-id="c1f40-237">로그 항목</span><span class="sxs-lookup"><span data-stu-id="c1f40-237">Log entry</span></span>|<span data-ttu-id="c1f40-238">Description</span><span class="sxs-lookup"><span data-stu-id="c1f40-238">Description</span></span>|  
|---------------|-----------------|  
|`ScriptTaskLogEntry`|<span data-ttu-id="c1f40-239">스크립트에서 로깅을 구현한 결과를 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="c1f40-239">Reports the results of implementing logging in the script.</span></span> <span data-ttu-id="c1f40-240">`Log` 개체의 `Dts` 메서드 호출에 대해 각각 로그 항목이 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="c1f40-240">A log entry is written for each call to the `Log` method of the `Dts` object.</span></span> <span data-ttu-id="c1f40-241">이 항목은 코드가 실행되면 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="c1f40-241">The entry is written when the code is run.</span></span> <span data-ttu-id="c1f40-242">자세한 내용은 [Logging in the Script Task](extending-packages-scripting/task/logging-in-the-script-task.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c1f40-242">For more information, see [Logging in the Script Task](extending-packages-scripting/task/logging-in-the-script-task.md).</span></span>|  
  
###  <a name="send-mail-task"></a><a name="SendMail"></a> <span data-ttu-id="c1f40-243">메일 보내기 태스크</span><span class="sxs-lookup"><span data-stu-id="c1f40-243">Send Mail Task</span></span>  
 <span data-ttu-id="c1f40-244">다음 표에서는 메일 보내기 태스크에 대한 사용자 지정 로그 항목을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="c1f40-244">The following table lists the custom log entries for the Send Mail task.</span></span>  
  
|<span data-ttu-id="c1f40-245">로그 항목</span><span class="sxs-lookup"><span data-stu-id="c1f40-245">Log entry</span></span>|<span data-ttu-id="c1f40-246">Description</span><span class="sxs-lookup"><span data-stu-id="c1f40-246">Description</span></span>|  
|---------------|-----------------|  
|`SendMailTaskBegin`|<span data-ttu-id="c1f40-247">태스크에서 전자 메일 메시지 보내기를 시작했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c1f40-247">Indicates that the task began to send an e-mail message.</span></span>|  
|`SendMailTaskEnd`|<span data-ttu-id="c1f40-248">태스크에서 전자 메일 메시지 보내기를 완료했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c1f40-248">Indicates that the task finished sending an e-mail message.</span></span>|  
|`SendMailTaskInfo`|<span data-ttu-id="c1f40-249">태스크에 대한 설명 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="c1f40-249">Provides descriptive information about the task.</span></span>|  
  
###  <a name="transfer-database-task"></a><a name="TransferDatabase"></a> <span data-ttu-id="c1f40-250">데이터베이스 전송 태스크</span><span class="sxs-lookup"><span data-stu-id="c1f40-250">Transfer Database Task</span></span>  
 <span data-ttu-id="c1f40-251">다음 표에서는 데이터베이스 전송 태스크에 대한 사용자 지정 로그 항목을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="c1f40-251">The following table lists the custom log entries for the Transfer Database task.</span></span>  
  
|<span data-ttu-id="c1f40-252">로그 항목</span><span class="sxs-lookup"><span data-stu-id="c1f40-252">Log entry</span></span>|<span data-ttu-id="c1f40-253">Description</span><span class="sxs-lookup"><span data-stu-id="c1f40-253">Description</span></span>|  
|---------------|-----------------|  
|`SourceDB`|<span data-ttu-id="c1f40-254">태스크에서 복사한 데이터베이스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c1f40-254">Specifies the database that the task copied.</span></span>|  
|`SourceSQLServer`|<span data-ttu-id="c1f40-255">데이터베이스를 복사한 컴퓨터를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c1f40-255">Specifies the computer from which the database was copied.</span></span>|  
  
###  <a name="transfer-error-messages-task"></a><a name="TransferErrorMessages"></a> <span data-ttu-id="c1f40-256">오류 메시지 전송 태스크</span><span class="sxs-lookup"><span data-stu-id="c1f40-256">Transfer Error Messages Task</span></span>  
 <span data-ttu-id="c1f40-257">다음 표에서는 오류 메시지 전송 태스크에 대한 사용자 지정 로그 항목을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="c1f40-257">The following table lists the custom log entries for the Transfer Error Messages task.</span></span>  
  
|<span data-ttu-id="c1f40-258">로그 항목</span><span class="sxs-lookup"><span data-stu-id="c1f40-258">Log entry</span></span>|<span data-ttu-id="c1f40-259">Description</span><span class="sxs-lookup"><span data-stu-id="c1f40-259">Description</span></span>|  
|---------------|-----------------|  
|`TransferErrorMessagesTaskFinishedTransferringObjects`|<span data-ttu-id="c1f40-260">태스크에서 오류 메시지 전송을 완료했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c1f40-260">Indicates that the task finished transferring error messages.</span></span>|  
|`TransferErrorMessagesTaskStartTransferringObjects`|<span data-ttu-id="c1f40-261">태스크에서 오류 메시지 전송을 시작했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c1f40-261">Indicates that the task started to transfer error messages.</span></span>|  
  
###  <a name="transfer-jobs-task"></a><a name="TransferJobs"></a> <span data-ttu-id="c1f40-262">작업 전송 태스크</span><span class="sxs-lookup"><span data-stu-id="c1f40-262">Transfer Jobs Task</span></span>  
 <span data-ttu-id="c1f40-263">다음 표에서는 작업 전송 태스크에 대한 사용자 지정 로그 항목을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="c1f40-263">The following table lists the custom log entries for the Transfer Jobs task.</span></span>  
  
|<span data-ttu-id="c1f40-264">로그 항목</span><span class="sxs-lookup"><span data-stu-id="c1f40-264">Log entry</span></span>|<span data-ttu-id="c1f40-265">Description</span><span class="sxs-lookup"><span data-stu-id="c1f40-265">Description</span></span>|  
|---------------|-----------------|  
|`TransferJobsTaskFinishedTransferringObjects`|<span data-ttu-id="c1f40-266">태스크에서 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 에이전트 작업 전송을 완료했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c1f40-266">Indicates that the task finished transferring [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent jobs.</span></span>|  
|`TransferJobsTaskStartTransferringObjects`|<span data-ttu-id="c1f40-267">태스크에서 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 에이전트 작업 전송을 시작했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c1f40-267">Indicates that the task started to transfer [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent jobs.</span></span>|  
  
###  <a name="transfer-logins-task"></a><a name="TransferLogins"></a> <span data-ttu-id="c1f40-268">로그인 전송 태스크</span><span class="sxs-lookup"><span data-stu-id="c1f40-268">Transfer Logins Task</span></span>  
 <span data-ttu-id="c1f40-269">다음 표에서는 로그인 전송 태스크에 대한 사용자 지정 로그 항목을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="c1f40-269">The following table lists the custom log entries for the Transfer Logins task.</span></span>  
  
|<span data-ttu-id="c1f40-270">로그 항목</span><span class="sxs-lookup"><span data-stu-id="c1f40-270">Log entry</span></span>|<span data-ttu-id="c1f40-271">Description</span><span class="sxs-lookup"><span data-stu-id="c1f40-271">Description</span></span>|  
|---------------|-----------------|  
|`TransferLoginsTaskFinishedTransferringObjects`|<span data-ttu-id="c1f40-272">태스크에서 로그인 전송을 완료했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c1f40-272">Indicates that the task finished transferring logins.</span></span>|  
|`TransferLoginsTaskStartTransferringObjects`|<span data-ttu-id="c1f40-273">태스크에서 로그인 전송을 시작했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c1f40-273">Indicates that the task started to transfer logins.</span></span>|  
  
###  <a name="transfer-master-stored-procedures-task"></a><a name="TransferMasterStoredProcedures"></a> <span data-ttu-id="c1f40-274">Master 저장 프로시저 전송 태스크</span><span class="sxs-lookup"><span data-stu-id="c1f40-274">Transfer Master Stored Procedures Task</span></span>  
 <span data-ttu-id="c1f40-275">다음 표에서는 Master 저장 프로시저 전송 태스크에 대한 사용자 지정 로그 항목을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="c1f40-275">The following table lists the custom log entries for the Transfer Master Stored Procedures task.</span></span>  
  
|<span data-ttu-id="c1f40-276">로그 항목</span><span class="sxs-lookup"><span data-stu-id="c1f40-276">Log entry</span></span>|<span data-ttu-id="c1f40-277">Description</span><span class="sxs-lookup"><span data-stu-id="c1f40-277">Description</span></span>|  
|---------------|-----------------|  
|`TransferStoredProceduresTaskFinishedTransferringObjects`|<span data-ttu-id="c1f40-278">태스크에서 **master** 데이터베이스에 저장된 사용자 정의 저장 프로시저 전송을 완료했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c1f40-278">Indicates that the task finished transferring user-defined stored procedures that are stored in the **master** database.</span></span>|  
|`TransferStoredProceduresTaskStartTransferringObjects`|<span data-ttu-id="c1f40-279">태스크에서 **master** 데이터베이스에 저장된 사용자 정의 저장 프로시저 전송을 시작했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c1f40-279">Indicates that the task started to transfer user-defined stored procedures that are stored in the **master** database.</span></span>|  
  
###  <a name="transfer-sql-server-objects-task"></a><a name="TransferSQLServerObjects"></a> <span data-ttu-id="c1f40-280">SQL Server 개체 전송 태스크</span><span class="sxs-lookup"><span data-stu-id="c1f40-280">Transfer SQL Server Objects Task</span></span>  
 <span data-ttu-id="c1f40-281">다음 표에서는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 개체 전송 태스크에 대한 사용자 지정 로그 항목을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="c1f40-281">The following table lists the custom log entries for the Transfer [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Objects task.</span></span>  
  
|<span data-ttu-id="c1f40-282">로그 항목</span><span class="sxs-lookup"><span data-stu-id="c1f40-282">Log entry</span></span>|<span data-ttu-id="c1f40-283">Description</span><span class="sxs-lookup"><span data-stu-id="c1f40-283">Description</span></span>|  
|---------------|-----------------|  
|`TransferSqlServerObjectsTaskFinishedTransferringObjects`|<span data-ttu-id="c1f40-284">태스크에서 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 데이터베이스 개체 전송을 완료했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c1f40-284">Indicates that the task finished transferring [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] database objects.</span></span>|  
|`TransferSqlServerObjectsTaskStartTransferringObjects`|<span data-ttu-id="c1f40-285">태스크에서 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 데이터베이스 개체 전송을 시작했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c1f40-285">Indicates that the task started to transfer [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] database objects.</span></span>|  
  
###  <a name="web-services-task"></a><a name="WebServices"></a> <span data-ttu-id="c1f40-286">웹 서비스 태스크</span><span class="sxs-lookup"><span data-stu-id="c1f40-286">Web Services Task</span></span>  
 <span data-ttu-id="c1f40-287">다음 표에서는 웹 서비스 태스크에 사용할 수 있는 사용자 지정 로그 항목을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="c1f40-287">The following table lists the custom log entries that you can enable for the Web Services task.</span></span>  
  
|<span data-ttu-id="c1f40-288">로그 항목</span><span class="sxs-lookup"><span data-stu-id="c1f40-288">Log entry</span></span>|<span data-ttu-id="c1f40-289">Description</span><span class="sxs-lookup"><span data-stu-id="c1f40-289">Description</span></span>|  
|---------------|-----------------|  
|`WSTaskBegin`|<span data-ttu-id="c1f40-290">태스크에서 웹 서비스 액세스를 시작했습니다.</span><span class="sxs-lookup"><span data-stu-id="c1f40-290">The task began to access a Web service.</span></span>|  
|`WSTaskEnd`|<span data-ttu-id="c1f40-291">태스크에서 웹 서비스 메서드를 완료했습니다.</span><span class="sxs-lookup"><span data-stu-id="c1f40-291">The task completed a Web service method.</span></span>|  
|`WSTaskInfo`|<span data-ttu-id="c1f40-292">태스크에 대한 설명 정보입니다.</span><span class="sxs-lookup"><span data-stu-id="c1f40-292">Descriptive information about the task.</span></span>|  
  
###  <a name="wmi-data-reader-task"></a><a name="WMIDataReader"></a> <span data-ttu-id="c1f40-293">WMI 데이터 판독기 태스크</span><span class="sxs-lookup"><span data-stu-id="c1f40-293">WMI Data Reader Task</span></span>  
 <span data-ttu-id="c1f40-294">다음 표에서는 WMI 데이터 판독기 태스크에 대한 사용자 지정 로그 항목을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="c1f40-294">The following table lists the custom log entries for the WMI Data Reader task.</span></span>  
  
|<span data-ttu-id="c1f40-295">로그 항목</span><span class="sxs-lookup"><span data-stu-id="c1f40-295">Log entry</span></span>|<span data-ttu-id="c1f40-296">Description</span><span class="sxs-lookup"><span data-stu-id="c1f40-296">Description</span></span>|  
|---------------|-----------------|  
|`WMIDataReaderGettingWMIData`|<span data-ttu-id="c1f40-297">태스크에서 WMI 데이터 읽기를 시작했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c1f40-297">Indicates that the task began to read WMI data.</span></span>|  
|`WMIDataReaderOperation`|<span data-ttu-id="c1f40-298">태스크에서 실행한 WQL 쿼리를 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="c1f40-298">Reports the WQL query that the task ran.</span></span>|  
  
###  <a name="wmi-event-watcher-task"></a><a name="WMIEventWatcher"></a> <span data-ttu-id="c1f40-299">WMI 이벤트 감시자 태스크</span><span class="sxs-lookup"><span data-stu-id="c1f40-299">WMI Event Watcher Task</span></span>  
 <span data-ttu-id="c1f40-300">다음 표에서는 WMI 이벤트 감시자 태스크에 대한 사용자 지정 로그 항목을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="c1f40-300">The following table lists the custom log entries for the WMI Event Watcher task.</span></span>  
  
|<span data-ttu-id="c1f40-301">로그 항목</span><span class="sxs-lookup"><span data-stu-id="c1f40-301">Log entry</span></span>|<span data-ttu-id="c1f40-302">Description</span><span class="sxs-lookup"><span data-stu-id="c1f40-302">Description</span></span>|  
|---------------|-----------------|  
|`WMIEventWatcherEventOccurred`|<span data-ttu-id="c1f40-303">태스크에서 모니터링하고 있는 이벤트가 발생했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c1f40-303">Denotes that the event occurred that the task was monitoring.</span></span>|  
|`WMIEventWatcherTimedout`|<span data-ttu-id="c1f40-304">태스크 시간이 초과되었음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c1f40-304">Indicates that the task timed out.</span></span>|  
|`WMIEventWatcherWatchingForWMIEvents`|<span data-ttu-id="c1f40-305">태스크에서 WQL 쿼리 실행을 시작했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c1f40-305">Indicates that the task began to execute the WQL query.</span></span> <span data-ttu-id="c1f40-306">이 항목은 해당 쿼리를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="c1f40-306">The entry includes the query.</span></span>|  
  
###  <a name="xml-task"></a><a name="XML"></a> <span data-ttu-id="c1f40-307">XML 태스크</span><span class="sxs-lookup"><span data-stu-id="c1f40-307">XML Task</span></span>  
 <span data-ttu-id="c1f40-308">다음 표에서는 XML 태스크에 대한 사용자 지정 로그 항목을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="c1f40-308">The following table describes the custom log entry for the XML task.</span></span>  
  
|<span data-ttu-id="c1f40-309">로그 항목</span><span class="sxs-lookup"><span data-stu-id="c1f40-309">Log entry</span></span>|<span data-ttu-id="c1f40-310">Description</span><span class="sxs-lookup"><span data-stu-id="c1f40-310">Description</span></span>|  
|---------------|-----------------|  
|`XMLOperation`|<span data-ttu-id="c1f40-311">태스크에서 수행한 작업에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="c1f40-311">Provides information about the operation that the task performs</span></span>|   
  
## <a name="see-also"></a><span data-ttu-id="c1f40-312">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c1f40-312">See Also</span></span>  
 [<span data-ttu-id="c1f40-313">Integration Services&#40;SSIS&#41; 로깅</span><span class="sxs-lookup"><span data-stu-id="c1f40-313">Integration Services &#40;SSIS&#41; Logging</span></span>](performance/integration-services-ssis-logging.md)  
  
