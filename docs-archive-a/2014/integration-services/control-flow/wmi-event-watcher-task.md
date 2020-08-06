---
title: WMI 이벤트 감시자 태스크 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.wmieventwatchertask.f1
helpviewer_keywords:
- WQL [Integration Services]
- WMI Event Watcher task [Integration Services]
ms.assetid: b5bb52e9-a77e-41e1-93f9-d4c3bc6b2c9a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: be20624e5ccdf665e6274f647c342498e9c0f0a9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741155"
---
# <a name="wmi-event-watcher-task"></a><span data-ttu-id="766c0-102">WMI 이벤트 감시자 태스크</span><span class="sxs-lookup"><span data-stu-id="766c0-102">WMI Event Watcher Task</span></span>
  <span data-ttu-id="766c0-103">WMI 이벤트 감시자 태스크는 WQL(WMI Query Language) 이벤트 쿼리를 사용하여 특정 이벤트를 지정하기 위해 WMI(Windows Management Instrumentation) 이벤트를 감시합니다.</span><span class="sxs-lookup"><span data-stu-id="766c0-103">The WMI Event Watcher task watches for a Windows Management Instrumentation (WMI) event using a Management Instrumentation Query Language (WQL) event query to specify events of interest.</span></span> <span data-ttu-id="766c0-104">WMI 이벤트 감시자 태스크는 다음 용도로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="766c0-104">You can use the WMI Event Watcher task for the following purposes:</span></span>  
  
-   <span data-ttu-id="766c0-105">파일이 폴더에 추가되었다는 알림을 기다린 후 파일 처리를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="766c0-105">Wait for notification that files have been added to a folder and then initiate the processing of the file.</span></span>  
  
-   <span data-ttu-id="766c0-106">서버에서 사용 가능한 메모리가 지정된 백분율 아래로 떨어지면 파일을 삭제하는 패키지를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="766c0-106">Run a package that deletes files when the available memory on a server drops lower than a specified percentage.</span></span>  
  
-   <span data-ttu-id="766c0-107">애플리케이션 설치를 감시한 후 애플리케이션을 사용하는 패키지를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="766c0-107">Watch for installation of an application, and then run a package that uses the application.</span></span>  
  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <span data-ttu-id="766c0-108">에는 WMI 정보를 읽는 태스크가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="766c0-108">includes a task that reads WMI information.</span></span>  
  
 <span data-ttu-id="766c0-109">이 태스크에 대한 자세한 내용을 보려면 다음 항목을 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="766c0-109">For more information about this task, click the following topic:</span></span>  
  
-   [<span data-ttu-id="766c0-110">WMI 데이터 판독기 태스크</span><span class="sxs-lookup"><span data-stu-id="766c0-110">WMI Data Reader Task</span></span>](wmi-data-reader-task.md)  
  
## <a name="wql-queries"></a><span data-ttu-id="766c0-111">WQL 쿼리</span><span class="sxs-lookup"><span data-stu-id="766c0-111">WQL Queries</span></span>  
 <span data-ttu-id="766c0-112">WQL은 WMI 이벤트 알림 및 기타 WMI 관련 기능을 지원하기 위한 확장 기능이 포함된 SQL의 언어입니다.</span><span class="sxs-lookup"><span data-stu-id="766c0-112">WQL is a dialect of SQL with extensions to support WMI event notification and other WMI-specific features.</span></span> <span data-ttu-id="766c0-113">WQL에 대한 자세한 내용은 [MSDN Library](https://go.microsoft.com/fwlink/?linkid=62553)에서 WMI(Windows Management Instrumentation) 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="766c0-113">For more information about WQL, see the Windows Management Instrumentation documentation in the [MSDN Library](https://go.microsoft.com/fwlink/?linkid=62553).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="766c0-114">WMI 클래스는 Windows 버전마다 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="766c0-114">WMI classes vary between versions of Windows.</span></span>  
  
 <span data-ttu-id="766c0-115">다음 쿼리는 CPU 사용이 40%를 넘는 알림을 감시합니다.</span><span class="sxs-lookup"><span data-stu-id="766c0-115">The following query watches for notification that the CPU use is more than 40 percent.</span></span>  
  
```  
SELECT * from __InstanceModificationEvent WITHIN 2 WHERE TargetInstance ISA 'Win32_Processor' and TargetInstance.LoadPercentage > 40  
```  
  
 <span data-ttu-id="766c0-116">다음 쿼리는 폴더에 추가된 파일 알림을 감시합니다.</span><span class="sxs-lookup"><span data-stu-id="766c0-116">The following query watches for notification that a file has been added to a folder.</span></span>  
  
```  
SELECT * FROM __InstanceCreationEvent WITHIN 10 WHERE TargetInstance ISA "CIM_DirectoryContainsFile" and TargetInstance.GroupComponent= "Win32_Directory.Name=\"c:\\\\WMIFileWatcher\""   
```  
  
## <a name="custom-logging-messages-available-on-the-wmi-event-watcher-task"></a><span data-ttu-id="766c0-117">WMI 이벤트 감시자 태스크에 사용할 수 있는 사용자 지정 로깅 메시지</span><span class="sxs-lookup"><span data-stu-id="766c0-117">Custom Logging Messages Available on the WMI Event Watcher Task</span></span>  
 <span data-ttu-id="766c0-118">다음 표에서는 WMI 이벤트 감시자 태스크에 대한 사용자 지정 로그 항목을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="766c0-118">The following table lists the custom log entries for the WMI Event Watcher task.</span></span> <span data-ttu-id="766c0-119">자세한 내용은 [Integration Services&#40;SSIS&#41; 로깅](../performance/integration-services-ssis-logging.md) 및 [로깅할 메시지 사용자 지정](../custom-messages-for-logging.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="766c0-119">For more information, see [Integration Services &#40;SSIS&#41; Logging](../performance/integration-services-ssis-logging.md) and [Custom Messages for Logging](../custom-messages-for-logging.md).</span></span>  
  
|<span data-ttu-id="766c0-120">로그 항목</span><span class="sxs-lookup"><span data-stu-id="766c0-120">Log entry</span></span>|<span data-ttu-id="766c0-121">Description</span><span class="sxs-lookup"><span data-stu-id="766c0-121">Description</span></span>|  
|---------------|-----------------|  
|`WMIEventWatcherEventOccurred`|<span data-ttu-id="766c0-122">태스크에서 모니터링하고 있는 이벤트가 발생했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="766c0-122">Indicates that an event occurred that the task was monitoring.</span></span>|  
|`WMIEventWatcherTimedout`|<span data-ttu-id="766c0-123">태스크 시간이 초과되었음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="766c0-123">Indicates that the task timed out.</span></span>|  
|`WMIEventWatcherWatchingForWMIEvents`|<span data-ttu-id="766c0-124">태스크에서 WQL 쿼리 실행을 시작했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="766c0-124">Indicates that the task began to execute the WQL query.</span></span> <span data-ttu-id="766c0-125">이 항목은 해당 쿼리를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="766c0-125">The entry includes the query.</span></span>|  
  
## <a name="configuration-of-the-wmi-event-watcher-task"></a><span data-ttu-id="766c0-126">WMI 이벤트 감시자 태스크 구성</span><span class="sxs-lookup"><span data-stu-id="766c0-126">Configuration of the WMI Event Watcher Task</span></span>  
 <span data-ttu-id="766c0-127">다음과 같은 방법으로 WMI 데이터 판독기 태스크를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="766c0-127">You can configure the WMI Data Reader task in the following ways:</span></span>  
  
-   <span data-ttu-id="766c0-128">사용할 WMI 연결 관리자를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="766c0-128">Specify the WMI connection manager to use.</span></span>  
  
-   <span data-ttu-id="766c0-129">WQL 쿼리의 원본을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="766c0-129">Specify the source of the WQL query.</span></span> <span data-ttu-id="766c0-130">원본은 태스크, 변수 또는 파일의 외부에 있을 수 있으며 쿼리는 태스크 속성에 저장될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="766c0-130">The source can be external to the task, a variable or a file, or the query can be stored in a task property.</span></span>  
  
-   <span data-ttu-id="766c0-131">WMI 이벤트가 발생할 때 태스크에서 취할 동작을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="766c0-131">Specify the action that the task takes when the WMI event occurs.</span></span> <span data-ttu-id="766c0-132">이벤트 알림과 이벤트 이후의 상태를 로깅하거나 WMI 이벤트와 관련된 정보, 알림 및 이벤트 이후의 상태를 제공하는 사용자 지정 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 이벤트를 발생시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="766c0-132">You can log the event notification and the status after the event, or raise custom [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] events that provide information associated with the WMI event, the notification, and the status after the event.</span></span>  
  
-   <span data-ttu-id="766c0-133">태스크가 이벤트에 대응하는 방법을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="766c0-133">Define how the task responds to the event.</span></span> <span data-ttu-id="766c0-134">이벤트에 따라 태스크가 성공 또는 실패하도록 구성하거나 단지 태스크에서 이벤트를 다시 감시하도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="766c0-134">The task can be configured to succeed or fail, depending on the event, or the task can just watch for the event again.</span></span>  
  
-   <span data-ttu-id="766c0-135">WMI 쿼리 시간이 종료될 때 태스크에서 취할 동작을 지정합니다. 시간 제한 및 시간 제한 이후의 상태를 로깅하거나 WMI 이벤트 시간이 종료되었고 해당 제한 시간과 제한 시간 상태를 로깅하도록 나타내는 사용자 지정 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 이벤트를 발생시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="766c0-135">Specify the action the task takes when the WMI query times out. You can log the time-out and the status after time-out, or raise a custom [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] event, indicating that the WMI event timed out and logging the time-out and time-out status.</span></span>  
  
-   <span data-ttu-id="766c0-136">태스크가 시간 종료에 대응하는 방법을 정의합니다. 태스크가 성공 또는 실패하도록 구성하거나 단지 태스크에서 이벤트를 다시 감시하도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="766c0-136">Define how the task responds to the time-out. The task can be configured to succeed or fail, or the task can just watch for the event again.</span></span>  
  
-   <span data-ttu-id="766c0-137">태스크가 이벤트를 감시하는 횟수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="766c0-137">Specify the number of times the task watches for the event.</span></span>  
  
-   <span data-ttu-id="766c0-138">제한 시간을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="766c0-138">Specify the time-out.</span></span>  
  
 <span data-ttu-id="766c0-139">원본이 파일인 경우 WMI 이벤트 감시자 태스크는 파일 연결 관리자를 사용하여 파일에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="766c0-139">If the source is a file, the WMI Event Watcher task uses a File connection manager to connect to the file.</span></span> <span data-ttu-id="766c0-140">자세한 내용은 [Flat File Connection Manager](../connection-manager/file-connection-manager.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="766c0-140">For more information, see [Flat File Connection Manager](../connection-manager/file-connection-manager.md).</span></span>  
  
 <span data-ttu-id="766c0-141">WMI 이벤트 감시자 태스크는 WMI 연결 관리자를 사용하여 WMI 정보를 읽어 온 서버에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="766c0-141">The WMI Event Watcher task uses a WMI connection manager to connect to the server from which it reads WMI information.</span></span> <span data-ttu-id="766c0-142">자세한 내용은 [WMI Connection Manager](../connection-manager/wmi-connection-manager.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="766c0-142">For more information, see [WMI Connection Manager](../connection-manager/wmi-connection-manager.md).</span></span>  
  
 <span data-ttu-id="766c0-143">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너를 사용하거나 프로그래밍 방식으로 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="766c0-143">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="766c0-144">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너에서 설정할 수 있는 속성에 대한 자세한 내용을 보려면 다음 항목 중 하나를 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="766c0-144">For more information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="766c0-145">WMI 이벤트 감시자 태스크 편집기&#40;일반 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="766c0-145">WMI Event Watcher Task Editor &#40;General Page&#41;</span></span>](../general-page-of-integration-services-designers-options.md)  
  
-   [<span data-ttu-id="766c0-146">WMI 이벤트 감시자 태스크 편집기&#40;WMI 옵션 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="766c0-146">WMI Event Watcher Task Editor &#40;WMI Options Page&#41;</span></span>](../wmi-event-watcher-task-editor-wmi-options-page.md)  
  
-   [<span data-ttu-id="766c0-147">식 페이지</span><span class="sxs-lookup"><span data-stu-id="766c0-147">Expressions Page</span></span>](../expressions/expressions-page.md)  
  
 <span data-ttu-id="766c0-148">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너에서 이러한 속성을 설정하는 방법을 보려면 다음 항목을 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="766c0-148">For more information about how to set these properties in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="766c0-149">태스크 또는 컨테이너의 속성 설정</span><span class="sxs-lookup"><span data-stu-id="766c0-149">Set the Properties of a Task or Container</span></span>](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="programmatic-configuration-of-the-wmi-event-watcher-task"></a><span data-ttu-id="766c0-150">WMI 이벤트 감시자 태스크의 프로그래밍 방식 구성</span><span class="sxs-lookup"><span data-stu-id="766c0-150">Programmatic Configuration of the WMI Event Watcher Task</span></span>  
 <span data-ttu-id="766c0-151">이러한 속성을 프로그래밍 방식으로 설정하는 방법을 보려면 다음 항목을 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="766c0-151">For more information about programmatically setting these properties, click the following topic:</span></span>  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.WmiEventWatcherTask.WmiEventWatcherTask>  
  
  
