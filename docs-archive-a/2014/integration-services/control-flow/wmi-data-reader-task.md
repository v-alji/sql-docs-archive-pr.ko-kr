---
title: WMI 데이터 판독기 태스크 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.wmidatareadertask.f1
helpviewer_keywords:
- WQL [Integration Services]
- WMI Data Reader task [Integration Services]
ms.assetid: dae57067-0275-4ac3-8f34-1b9d169f1112
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1d2f16a28e8b6c94c7275468dedb6d2dfec76d8a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647792"
---
# <a name="wmi-data-reader-task"></a><span data-ttu-id="8a13c-102">WMI 데이터 판독기 태스크</span><span class="sxs-lookup"><span data-stu-id="8a13c-102">WMI Data Reader Task</span></span>
  <span data-ttu-id="8a13c-103">WMI 데이터 판독기 태스크는 WMI(Windows Management Instrumentation) 쿼리 언어를 사용하여 WMI로부터 컴퓨터 시스템에 대한 정보를 반환하는 쿼리를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="8a13c-103">The WMI Data Reader task runs queries using the Windows Management Instrumentation (WMI) Query Language that returns information from WMI about a computer system.</span></span> <span data-ttu-id="8a13c-104">WMI 데이터 판독기 태스크는 다음 용도로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8a13c-104">You can use the WMI Data Reader task for the following purposes:</span></span>  
  
-   <span data-ttu-id="8a13c-105">로컬 또는 원격 컴퓨터의 Windows 이벤트 로그를 쿼리하고 정보를 파일이나 변수에 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="8a13c-105">Query the Windows event logs on a local or remote computer and write the information to a file or variable.</span></span>  
  
-   <span data-ttu-id="8a13c-106">하드웨어 구성 요소의 설치 여부, 상태 또는 속성에 대한 정보를 가져온 후 이 정보를 사용하여 제어 흐름에서 다른 태스크를 실행할지 여부를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="8a13c-106">Obtain information about the presence, state, or properties of hardware components, and then use this information to determine whether other tasks in the control flow should run.</span></span>  
  
-   <span data-ttu-id="8a13c-107">애플리케이션 목록을 가져오고 설치된 각 애플리케이션의 버전을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="8a13c-107">Get a list of applications and determine what version of each application is installed.</span></span>  
  
 <span data-ttu-id="8a13c-108">다음과 같은 방법으로 WMI 데이터 판독기 태스크를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8a13c-108">You can configure the WMI Data Reader task in the following ways:</span></span>  
  
-   <span data-ttu-id="8a13c-109">사용할 WMI 연결 관리자를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8a13c-109">Specify the WMI connection manager to use.</span></span>  
  
-   <span data-ttu-id="8a13c-110">WQL 쿼리의 원본을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8a13c-110">Specify the source of the WQL query.</span></span> <span data-ttu-id="8a13c-111">쿼리는 태스크 속성에 저장하거나 변수 또는 파일과 같은 태스크 외부에 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8a13c-111">The query can be stored in a task property, or the query can be stored outside the task, in a variable or a file.</span></span>  
  
-   <span data-ttu-id="8a13c-112">WQL 쿼리 결과의 형식을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="8a13c-112">Define the format of the WQL query results.</span></span> <span data-ttu-id="8a13c-113">태스크에는 테이블, 속성 이름/값의 쌍 또는 속성 값 형식이 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a13c-113">The task supports a table, property name/value pair, or property value format.</span></span>  
  
-   <span data-ttu-id="8a13c-114">쿼리 대상을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8a13c-114">Specify the destination of the query.</span></span> <span data-ttu-id="8a13c-115">대상은 변수 또는 파일일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8a13c-115">The destination can be a variable or a file.</span></span>  
  
-   <span data-ttu-id="8a13c-116">쿼리 대상을 덮어쓰거나, 유지하거나, 추가할지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="8a13c-116">Indicate whether the query destination is overwritten, kept, or appended.</span></span>  
  
 <span data-ttu-id="8a13c-117">원본 또는 대상이 파일인 경우 WMI 데이터 판독기 태스크는 파일 연결 관리자를 사용하여 파일에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="8a13c-117">If the source or destination is a file, the WMI Data Reader task uses a File connection manager to connect to the file.</span></span> <span data-ttu-id="8a13c-118">자세한 내용은 [Flat File Connection Manager](../connection-manager/file-connection-manager.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8a13c-118">For more information, see [Flat File Connection Manager](../connection-manager/file-connection-manager.md).</span></span>  
  
 <span data-ttu-id="8a13c-119">WMI 데이터 판독기 태스크는 WMI 연결 관리자를 사용하여 WMI 정보를 읽어 온 서버에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="8a13c-119">The WMI Data Reader task uses a WMI connection manager to connect to the server from which it reads WMI information.</span></span> <span data-ttu-id="8a13c-120">자세한 내용은 [WMI Connection Manager](../connection-manager/wmi-connection-manager.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8a13c-120">For more information, see [WMI Connection Manager](../connection-manager/wmi-connection-manager.md).</span></span>  
  
## <a name="wql-query"></a><span data-ttu-id="8a13c-121">WQL 쿼리</span><span class="sxs-lookup"><span data-stu-id="8a13c-121">WQL Query</span></span>  
 <span data-ttu-id="8a13c-122">WQL은 WMI 이벤트 알림 및 기타 WMI 관련 기능을 지원하기 위한 확장 기능이 포함된 SQL의 언어입니다.</span><span class="sxs-lookup"><span data-stu-id="8a13c-122">WQL is a dialect of SQL with extensions to support WMI event notification and other WMI-specific features.</span></span> <span data-ttu-id="8a13c-123">WQL에 대한 자세한 내용은 [MSDN Library](https://go.microsoft.com/fwlink/?linkid=7022)에서 WMI(Windows Management Instrumentation) 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="8a13c-123">For more information about WQL, see the Windows Management Instrumentation documentation in the [MSDN Library](https://go.microsoft.com/fwlink/?linkid=7022).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8a13c-124">WMI 클래스는 Windows 버전마다 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="8a13c-124">WMI classes vary between versions of Windows.</span></span>  
  
 <span data-ttu-id="8a13c-125">다음 WQL 쿼리는 애플리케이션 로그 이벤트의 항목을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="8a13c-125">The following WQL query returns entries in the Application log event.</span></span>  
  
```  
SELECT * FROM Win32_NTLogEvent WHERE LogFile = 'Application' AND (SourceName='SQLISService' OR SourceName='SQLISPackage') AND TimeGenerated > '20050117'  
```  
  
 <span data-ttu-id="8a13c-126">다음 WQL 쿼리는 논리적 디스크 정보를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="8a13c-126">The following WQL query returns logical disk information.</span></span>  
  
```  
SELECT FreeSpace, DeviceId, Size, SystemName, Description FROM Win32_LlogicalDisk  
```  
  
 <span data-ttu-id="8a13c-127">다음 WQL 쿼리는 운영 체제에 대한 QFE(Quick Fix Engineering) 업데이트 목록을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="8a13c-127">The following WQL query returns a list of the quick fix engineering (QFE) updates to the operating system.</span></span>  
  
```  
Select * FROM Win32_QuickFixEngineering  
```  
  
## <a name="custom-logging-messages-available-on-the-wmi-data-reader-task"></a><span data-ttu-id="8a13c-128">WMI 데이터 판독기 태스크에 사용할 수 있는 사용자 지정 로깅 메시지</span><span class="sxs-lookup"><span data-stu-id="8a13c-128">Custom Logging Messages Available on the WMI Data Reader Task</span></span>  
 <span data-ttu-id="8a13c-129">다음 표에서는 WMI 데이터 판독기 태스크에 대한 사용자 지정 로그 항목을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="8a13c-129">The following table lists the custom log entries for the WMI Data Reader task.</span></span> <span data-ttu-id="8a13c-130">자세한 내용은 [Integration Services&#40;SSIS&#41; 로깅](../performance/integration-services-ssis-logging.md) 및 [로깅할 메시지 사용자 지정](../custom-messages-for-logging.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8a13c-130">For more information, see [Integration Services &#40;SSIS&#41; Logging](../performance/integration-services-ssis-logging.md) and [Custom Messages for Logging](../custom-messages-for-logging.md).</span></span>  
  
|<span data-ttu-id="8a13c-131">로그 항목</span><span class="sxs-lookup"><span data-stu-id="8a13c-131">Log entry</span></span>|<span data-ttu-id="8a13c-132">Description</span><span class="sxs-lookup"><span data-stu-id="8a13c-132">Description</span></span>|  
|---------------|-----------------|  
|`WMIDataReaderGettingWMIData`|<span data-ttu-id="8a13c-133">태스크에서 WMI 데이터 읽기를 시작했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="8a13c-133">Indicates that the task began to read WMI data.</span></span>|  
|`WMIDataReaderOperation`|<span data-ttu-id="8a13c-134">태스크에서 실행한 WQL 쿼리를 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="8a13c-134">Reports the WQL query that the task ran.</span></span>|  
  
## <a name="configuration-of-the-wmi-data-reader-task"></a><span data-ttu-id="8a13c-135">WMI 데이터 판독기 태스크 구성</span><span class="sxs-lookup"><span data-stu-id="8a13c-135">Configuration of the WMI Data Reader Task</span></span>  
 <span data-ttu-id="8a13c-136">프로그래밍 방식을 통해 또는 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너를 사용하여 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8a13c-136">You can set properties programmatically or through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer.</span></span>  
  
 <span data-ttu-id="8a13c-137">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너에서 설정할 수 있는 속성에 대한 자세한 내용을 보려면 다음 항목 중 하나를 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="8a13c-137">For information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="8a13c-138">WMI 데이터 판독기 태스크 편집기&#40;WMI 옵션 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="8a13c-138">WMI Data Reader Task Editor &#40;WMI Options Page&#41;</span></span>](../wmi-data-reader-task-editor-wmi-options-page.md)  
  
-   [<span data-ttu-id="8a13c-139">식 페이지</span><span class="sxs-lookup"><span data-stu-id="8a13c-139">Expressions Page</span></span>](../expressions/expressions-page.md)  
  
 <span data-ttu-id="8a13c-140">이러한 속성을 프로그래밍 방식으로 설정하는 방법을 보려면 다음 항목을 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="8a13c-140">For information about programmatically setting these properties, click the following topic:</span></span>  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.WmiDataReaderTask.WmiDataReaderTask>  
  
## <a name="related-tasks"></a><span data-ttu-id="8a13c-141">관련 작업</span><span class="sxs-lookup"><span data-stu-id="8a13c-141">Related Tasks</span></span>  
 <span data-ttu-id="8a13c-142">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너에서 이러한 속성을 설정하는 방법을 보려면 다음 항목을 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="8a13c-142">For more information about how to set these properties in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="8a13c-143">태스크 또는 컨테이너의 속성 설정</span><span class="sxs-lookup"><span data-stu-id="8a13c-143">Set the Properties of a Task or Container</span></span>](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="see-also"></a><span data-ttu-id="8a13c-144">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8a13c-144">See Also</span></span>  
 <span data-ttu-id="8a13c-145">[Integration Services 태스크](integration-services-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="8a13c-145">[Integration Services Tasks](integration-services-tasks.md) </span></span>  
 [<span data-ttu-id="8a13c-146">제어 흐름</span><span class="sxs-lookup"><span data-stu-id="8a13c-146">Control Flow</span></span>](control-flow.md)  
  
  
