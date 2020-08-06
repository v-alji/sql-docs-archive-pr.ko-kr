---
title: WMI 이벤트 감시자 태스크 편집기 (WMI 옵션 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.wmieventwatcher.wmiquery.f1
helpviewer_keywords:
- WMI Event Watcher Task Editor
ms.assetid: 525f3de7-a021-4e52-9939-3a83c88f131a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d7d95501f6442df3723261c970c7a90f48cbdc87
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734248"
---
# <a name="wmi-event-watcher-task-editor-wmi-options-page"></a><span data-ttu-id="156fb-102">WMI 이벤트 감시자 태스크 편집기(WMI 옵션 페이지)</span><span class="sxs-lookup"><span data-stu-id="156fb-102">WMI Event Watcher Task Editor (WMI Options Page)</span></span>
  <span data-ttu-id="156fb-103">**WMI 이벤트 감시자 태스크 편집기** 대화 상자의 **WMI 옵션** 페이지를 사용하여 WQL(Windows Management Instrumentation Query Language) 쿼리의 원본 및 WMI 이벤트 감시자 태스크가 Microsoft Windows Instrumentation(WMI) 이벤트에 응답하는 방식을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="156fb-103">Use the **WMI Options** page of the **WMI Event Watcher Task Editor** dialog box to specify the source of the Windows Management Instrumentation Query Language (WQL) query and how the WMI Event Watcher task responds to Microsoft Windows Instrumentation (WMI) events.</span></span>  
  
 <span data-ttu-id="156fb-104">이 태스크에 대한 자세한 내용은 [WMI Event Watcher Task](control-flow/wmi-event-watcher-task.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="156fb-104">To learn about this task, see [WMI Event Watcher Task](control-flow/wmi-event-watcher-task.md).</span></span> <span data-ttu-id="156fb-105">WQL(WMI Query Language)에 대한 자세한 내용은 MSDN 라이브러리의 WMI(Windows Management Instrumentation) 항목인 [Querying with WQL](https://go.microsoft.com/fwlink/?LinkId=79045)(WQL을 사용하여 쿼리)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="156fb-105">For more information about WMI Query Language (WQL), see the Windows Management Instrumentation topic, [Querying with WQL](https://go.microsoft.com/fwlink/?LinkId=79045), in the MSDN Library.</span></span>  
  
## <a name="static-options"></a><span data-ttu-id="156fb-106">정적 옵션</span><span class="sxs-lookup"><span data-stu-id="156fb-106">Static Options</span></span>  
 <span data-ttu-id="156fb-107">**WMIConnectionName**</span><span class="sxs-lookup"><span data-stu-id="156fb-107">**WMIConnectionName**</span></span>  
 <span data-ttu-id="156fb-108">목록에서 WMI 연결 관리자를 선택하거나 \<**New WMI Connection...**>을 클릭하여 새 연결 관리자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="156fb-108">Select a WMI connection manager in the list, or click \<**New WMI Connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="156fb-109">**관련 항목:** [WMI 연결 관리자](connection-manager/wmi-connection-manager.md), [WMI 연결 관리자 편집기](../../2014/integration-services/wmi-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="156fb-109">**Related Topics:** [WMI Connection Manager](connection-manager/wmi-connection-manager.md), [WMI Connection Manager Editor](../../2014/integration-services/wmi-connection-manager-editor.md)</span></span>  
  
 <span data-ttu-id="156fb-110">**WQLQuerySourceType**</span><span class="sxs-lookup"><span data-stu-id="156fb-110">**WQLQuerySourceType**</span></span>  
 <span data-ttu-id="156fb-111">태스크에서 실행하는 WQL 쿼리의 원본 유형을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="156fb-111">Select the source type of the WQL query that the task runs.</span></span> <span data-ttu-id="156fb-112">이 속성의 옵션은 다음 표에 나열되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="156fb-112">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="156fb-113">값</span><span class="sxs-lookup"><span data-stu-id="156fb-113">Value</span></span>|<span data-ttu-id="156fb-114">Description</span><span class="sxs-lookup"><span data-stu-id="156fb-114">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="156fb-115">**직접 입력**</span><span class="sxs-lookup"><span data-stu-id="156fb-115">**Direct input**</span></span>|<span data-ttu-id="156fb-116">WQL 쿼리에 대한 원본을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="156fb-116">Set the source to a WQL query.</span></span> <span data-ttu-id="156fb-117">이 값을 선택하면 동적 옵션 **WQLQuerySource**가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="156fb-117">Selecting this value displays the dynamic option, **WQLQuerySource**.</span></span>|  
|<span data-ttu-id="156fb-118">**파일 연결**</span><span class="sxs-lookup"><span data-stu-id="156fb-118">**File connection**</span></span>|<span data-ttu-id="156fb-119">WQL 쿼리가 포함된 파일을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="156fb-119">Select a file that contains the WQL query.</span></span> <span data-ttu-id="156fb-120">이 값을 선택하면 동적 옵션 **WQLQuerySource**가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="156fb-120">Selecting this value displays the dynamic option, **WQLQuerySource**.</span></span>|  
|<span data-ttu-id="156fb-121">**변수**</span><span class="sxs-lookup"><span data-stu-id="156fb-121">**Variable**</span></span>|<span data-ttu-id="156fb-122">WQL 쿼리를 정의하는 변수에 대한 원본을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="156fb-122">Set the source to a variable that defines WQL query.</span></span> <span data-ttu-id="156fb-123">이 값을 선택하면 동적 옵션 **WQLQuerySource**가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="156fb-123">Selecting this value displays the dynamic option, **WQLQuerySource**.</span></span>|  
  
 <span data-ttu-id="156fb-124">**ActionAtEvent**</span><span class="sxs-lookup"><span data-stu-id="156fb-124">**ActionAtEvent**</span></span>  
 <span data-ttu-id="156fb-125">WMI 이벤트가 이벤트를 기록하고 [!INCLUDE[ssIS](../includes/ssis-md.md)] 동작을 시작할지, 아니면 이벤트만 기록할지를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="156fb-125">Specify whether the WMI event logs the event and initiates an [!INCLUDE[ssIS](../includes/ssis-md.md)] action, or only logs the event.</span></span>  
  
 <span data-ttu-id="156fb-126">**AfterEvent**</span><span class="sxs-lookup"><span data-stu-id="156fb-126">**AfterEvent**</span></span>  
 <span data-ttu-id="156fb-127">WMI 이벤트를 수신한 후 태스크가 성공 또는 실패하도록 지정하거나 태스크가 이벤트가 다시 발생하는지 여부를 계속 감시하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="156fb-127">Specify whether the task succeeds or fails after it receives the WMI event, or if the task continues watching for the event to occur again.</span></span>  
  
 <span data-ttu-id="156fb-128">**ActionAtTimeout**</span><span class="sxs-lookup"><span data-stu-id="156fb-128">**ActionAtTimeout**</span></span>  
 <span data-ttu-id="156fb-129">태스크가 WMI 쿼리에 대한 제한 시간 초과 발생을 기록하고 이에 대한 응답으로 [!INCLUDE[ssIS](../includes/ssis-md.md)] 이벤트를 시작할지, 아니면 제한 시간 초과 발생만 기록할지를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="156fb-129">Specify whether the task logs a WMI query time-out and initiates an [!INCLUDE[ssIS](../includes/ssis-md.md)] event in response, or only logs the time-out.</span></span>  
  
 <span data-ttu-id="156fb-130">**AfterTimeout**</span><span class="sxs-lookup"><span data-stu-id="156fb-130">**AfterTimeout**</span></span>  
 <span data-ttu-id="156fb-131">제한 시간 초과에 대한 응답으로 태스크가 성공 또는 실패하도록 지정하거나 태스크가 제한 시간 초과가 다시 발생하는지 여부를 계속 감시하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="156fb-131">Specify whether the task succeeds or fails in response to a time-out, or if the task continues watching for another time-out to recur.</span></span>  
  
 <span data-ttu-id="156fb-132">**NumberOfEvents**</span><span class="sxs-lookup"><span data-stu-id="156fb-132">**NumberOfEvents**</span></span>  
 <span data-ttu-id="156fb-133">감시할 이벤트의 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="156fb-133">Specify the number of events to watch for.</span></span>  
  
 <span data-ttu-id="156fb-134">**Timeout**</span><span class="sxs-lookup"><span data-stu-id="156fb-134">**Timeout**</span></span>  
 <span data-ttu-id="156fb-135">이벤트가 발생할 때까지 대기할 시간(초)을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="156fb-135">Specify the number of seconds to wait for the event to occur.</span></span> <span data-ttu-id="156fb-136">값 0은 제한 시간이 적용되지 않음을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="156fb-136">A value of 0 means that no time-out is in effect.</span></span>  
  
## <a name="wqlquerysource-dynamic-options"></a><span data-ttu-id="156fb-137">WQLQuerySource 동적 옵션</span><span class="sxs-lookup"><span data-stu-id="156fb-137">WQLQuerySource Dynamic Options</span></span>  
  
### <a name="wqlquerysource--direct-input"></a><span data-ttu-id="156fb-138">WQLQuerySource = 직접 입력</span><span class="sxs-lookup"><span data-stu-id="156fb-138">WQLQuerySource = Direct input</span></span>  
 <span data-ttu-id="156fb-139">**WQLQuerySource**</span><span class="sxs-lookup"><span data-stu-id="156fb-139">**WQLQuerySource**</span></span>  
 <span data-ttu-id="156fb-140">쿼리를 입력하거나, 줄임표 단추(...)를 클릭하고 **WQL 쿼리** 대화 상자를 사용하여 쿼리를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="156fb-140">Provide a query, or click the ellipsis button (...) and enter a query using the **WQL Query** dialog box.</span></span>  
  
### <a name="wqlquerysource--file-connection"></a><span data-ttu-id="156fb-141">WQLQuerySource = 파일 연결</span><span class="sxs-lookup"><span data-stu-id="156fb-141">WQLQuerySource = File connection</span></span>  
 <span data-ttu-id="156fb-142">**WQLQuerySource**</span><span class="sxs-lookup"><span data-stu-id="156fb-142">**WQLQuerySource**</span></span>  
 <span data-ttu-id="156fb-143">목록에서 파일 연결 관리자를 선택하거나 \<**New connection...**>을 클릭하여 새 연결 관리자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="156fb-143">Select a File connection manager in the list, or click \<**New connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="156fb-144">**관련 항목:** [파일 연결 관리자](connection-manager/file-connection-manager.md), [파일 연결 관리자 편집기](../../2014/integration-services/file-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="156fb-144">**Related Topics:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)</span></span>  
  
### <a name="wqlquerysource--variable"></a><span data-ttu-id="156fb-145">WQLQuerySource = 변수</span><span class="sxs-lookup"><span data-stu-id="156fb-145">WQLQuerySource = Variable</span></span>  
 <span data-ttu-id="156fb-146">**WQLQuerySource**</span><span class="sxs-lookup"><span data-stu-id="156fb-146">**WQLQuerySource**</span></span>  
 <span data-ttu-id="156fb-147">목록에서 변수를 선택하거나 \<**New variable...**>를 클릭하여 새 변수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="156fb-147">Select a variable in the list, or click \<**New variable...**> to create a new variable.</span></span>  
  
 <span data-ttu-id="156fb-148">**관련 항목:** [Integration Services&#40;SSIS&#41; 변수](integration-services-ssis-variables.md), [변수 추가](../../2014/integration-services/add-variable.md)</span><span class="sxs-lookup"><span data-stu-id="156fb-148">**Related Topics:** [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), [Add Variable](../../2014/integration-services/add-variable.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="156fb-149">참고 항목</span><span class="sxs-lookup"><span data-stu-id="156fb-149">See Also</span></span>  
 <span data-ttu-id="156fb-150">[Integration Services 오류 및 메시지 참조](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="156fb-150">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="156fb-151">[WMI 이벤트 감시자 태스크 편집기 &#40;일반 페이지&#41;](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="156fb-151">[WMI Event Watcher Task Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="156fb-152">[식 페이지](expressions/expressions-page.md) </span><span class="sxs-lookup"><span data-stu-id="156fb-152">[Expressions Page](expressions/expressions-page.md) </span></span>  
 [<span data-ttu-id="156fb-153">WMI 데이터 판독기 태스크</span><span class="sxs-lookup"><span data-stu-id="156fb-153">WMI Data Reader Task</span></span>](control-flow/wmi-data-reader-task.md)  
  
  
