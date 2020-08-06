---
title: WMI 데이터 판독기 태스크 편집기 (WMI 옵션 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.wmidatareadertask.wmiquery.f1
helpviewer_keywords:
- WMI Data Reader Task Editor
ms.assetid: 4b8d4716-882d-41b0-b77e-e0e2741a2cd5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: cfb28e7f8f352f708085bf664757391a05869752
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660018"
---
# <a name="wmi-data-reader-task-editor-wmi-options-page"></a><span data-ttu-id="94b12-102">WMI 데이터 판독기 태스크 편집기(WMI 옵션 페이지)</span><span class="sxs-lookup"><span data-stu-id="94b12-102">WMI Data Reader Task Editor (WMI Options Page)</span></span>
  <span data-ttu-id="94b12-103">**WMI 데이터 판독기 태스크 편집기** 대화 상자의 **WMI 옵션** 페이지를 사용하여 WQL(WMI Query Language) 쿼리의 원본 및 쿼리 결과의 대상을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="94b12-103">Use the **WMI Options** page of the **WMI Data Reader Task Editor** dialog box to specify the source of the Windows Management Instrumentation Query Language (WQL) query and the destination of the query result.</span></span>  
  
 <span data-ttu-id="94b12-104">이 태스크에 대한 자세한 내용은 [WMI Data Reader Task](control-flow/wmi-data-reader-task.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="94b12-104">To learn about this task, see [WMI Data Reader Task](control-flow/wmi-data-reader-task.md).</span></span> <span data-ttu-id="94b12-105">WQL(WMI Query Language)에 대한 자세한 내용은 MSDN 라이브러리의 WMI(Windows Management Instrumentation) 항목인 [Querying with WQL](https://go.microsoft.com/fwlink/?LinkId=79045)(WQL을 사용하여 쿼리)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="94b12-105">For more information about WMI Query Language (WQL), see the Windows Management Instrumentation topic, [Querying with WQL](https://go.microsoft.com/fwlink/?LinkId=79045), in the MSDN Library.</span></span>  
  
## <a name="static-options"></a><span data-ttu-id="94b12-106">정적 옵션</span><span class="sxs-lookup"><span data-stu-id="94b12-106">Static Options</span></span>  
 <span data-ttu-id="94b12-107">**WMIConnectionName**</span><span class="sxs-lookup"><span data-stu-id="94b12-107">**WMIConnectionName**</span></span>  
 <span data-ttu-id="94b12-108">목록에서 WMI 연결 관리자를 선택하거나 \<**New WMI Connection...**>을 클릭하여 새 연결 관리자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="94b12-108">Select a WMI connection manager in the list, or click \<**New WMI Connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="94b12-109">**관련 항목:** [WMI 연결 관리자](connection-manager/wmi-connection-manager.md), [WMI 연결 관리자 편집기](../../2014/integration-services/wmi-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="94b12-109">**Related Topics:** [WMI Connection Manager](connection-manager/wmi-connection-manager.md), [WMI Connection Manager Editor](../../2014/integration-services/wmi-connection-manager-editor.md)</span></span>  
  
 <span data-ttu-id="94b12-110">**WQLQuerySourceType**</span><span class="sxs-lookup"><span data-stu-id="94b12-110">**WQLQuerySourceType**</span></span>  
 <span data-ttu-id="94b12-111">태스크에서 실행하는 WQL 쿼리의 원본 유형을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="94b12-111">Select the source type of the WQL query that the task runs.</span></span> <span data-ttu-id="94b12-112">이 속성의 옵션은 다음 표에 나열되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="94b12-112">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="94b12-113">값</span><span class="sxs-lookup"><span data-stu-id="94b12-113">Value</span></span>|<span data-ttu-id="94b12-114">Description</span><span class="sxs-lookup"><span data-stu-id="94b12-114">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="94b12-115">**직접 입력**</span><span class="sxs-lookup"><span data-stu-id="94b12-115">**Direct input**</span></span>|<span data-ttu-id="94b12-116">WQL 쿼리에 대한 원본을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="94b12-116">Set the source to a WQL query.</span></span> <span data-ttu-id="94b12-117">이 값을 선택하면 동적 옵션 **WQLQuerySourceType**이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="94b12-117">Selecting this value displays the dynamic option **WQLQuerySourceType**.</span></span>|  
|<span data-ttu-id="94b12-118">**파일 연결**</span><span class="sxs-lookup"><span data-stu-id="94b12-118">**File connection**</span></span>|<span data-ttu-id="94b12-119">WQL 쿼리가 포함된 파일을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="94b12-119">Select a file that contains the WQL query.</span></span> <span data-ttu-id="94b12-120">이 값을 선택하면 동적 옵션 **WQLQuerySourceType**이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="94b12-120">Selecting this value displays the dynamic option **WQLQuerySourceType**.</span></span>|  
|<span data-ttu-id="94b12-121">**변수**</span><span class="sxs-lookup"><span data-stu-id="94b12-121">**Variable**</span></span>|<span data-ttu-id="94b12-122">원본을 WQL 쿼리를 정의하는 변수로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="94b12-122">Set the source to a variable that defines the WQL query.</span></span> <span data-ttu-id="94b12-123">이 값을 선택하면 동적 옵션 **WQLQuerySourceType**이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="94b12-123">Selecting this value displays the dynamic option **WQLQuerySourceType**.</span></span>|  
  
 <span data-ttu-id="94b12-124">**OutputType**</span><span class="sxs-lookup"><span data-stu-id="94b12-124">**OutputType**</span></span>  
 <span data-ttu-id="94b12-125">출력 유형을 데이터 테이블, 속성 값 또는 속성 이름 및 값으로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="94b12-125">Specify whether the output should be a data table, property value, or property name and value.</span></span>  
  
 <span data-ttu-id="94b12-126">**OverwriteDestination**</span><span class="sxs-lookup"><span data-stu-id="94b12-126">**OverwriteDestination**</span></span>  
 <span data-ttu-id="94b12-127">대상 파일 또는 변수의 원본 데이터에 대한 유지, 덮어쓰기 또는 추가 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="94b12-127">Specifies whether to keep, overwrite, or append to the original data in the destination file or variable.</span></span>  
  
 <span data-ttu-id="94b12-128">**DestinationType**</span><span class="sxs-lookup"><span data-stu-id="94b12-128">**DestinationType**</span></span>  
 <span data-ttu-id="94b12-129">태스크에서 실행하는 WQL 쿼리의 대상 유형을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="94b12-129">Select the destination type of the WQL query that the task runs.</span></span> <span data-ttu-id="94b12-130">이 속성의 옵션은 다음 표에 나열되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="94b12-130">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="94b12-131">값</span><span class="sxs-lookup"><span data-stu-id="94b12-131">Value</span></span>|<span data-ttu-id="94b12-132">Description</span><span class="sxs-lookup"><span data-stu-id="94b12-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="94b12-133">**파일 연결**</span><span class="sxs-lookup"><span data-stu-id="94b12-133">**File connection**</span></span>|<span data-ttu-id="94b12-134">WQL 쿼리 결과를 저장할 파일을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="94b12-134">Select a file to save the results of the WQL query in.</span></span> <span data-ttu-id="94b12-135">이 값을 선택하면 동적 옵션인 **DestinationType**이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="94b12-135">Selecting this value displays the dynamic option, **DestinationType**.</span></span>|  
|<span data-ttu-id="94b12-136">**변수**</span><span class="sxs-lookup"><span data-stu-id="94b12-136">**Variable**</span></span>|<span data-ttu-id="94b12-137">WQL 쿼리 결과를 저장할 변수를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="94b12-137">Set the variable to store the results of the WQL query in.</span></span> <span data-ttu-id="94b12-138">이 값을 선택하면 동적 옵션인 **DestinationType**이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="94b12-138">Selecting this value displays the dynamic option, **DestinationType**.</span></span>|  
  
## <a name="wqlquerysourcetype-dynamic-options"></a><span data-ttu-id="94b12-139">WQLQuerySourceType 동적 옵션</span><span class="sxs-lookup"><span data-stu-id="94b12-139">WQLQuerySourceType Dynamic Options</span></span>  
  
### <a name="wqlquerysourcetype--direct-input"></a><span data-ttu-id="94b12-140">WQLQuerySourceType = 직접 입력</span><span class="sxs-lookup"><span data-stu-id="94b12-140">WQLQuerySourceType = Direct input</span></span>  
 <span data-ttu-id="94b12-141">**WQLQuerySource**</span><span class="sxs-lookup"><span data-stu-id="94b12-141">**WQLQuerySource**</span></span>  
 <span data-ttu-id="94b12-142">쿼리를 제공하거나, 줄임표(...)를 클릭하고 **WQL 쿼리** 대화 상자를 사용하여 쿼리를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="94b12-142">Provide a query, or click the ellipsis (...) and enter a query using the **WQL Query** dialog box.</span></span>  
  
### <a name="wqlquerysourcetype--file-connection"></a><span data-ttu-id="94b12-143">WQLQuerySourceType = 파일 연결</span><span class="sxs-lookup"><span data-stu-id="94b12-143">WQLQuerySourceType = File connection</span></span>  
 <span data-ttu-id="94b12-144">**WQLQuerySource**</span><span class="sxs-lookup"><span data-stu-id="94b12-144">**WQLQuerySource**</span></span>  
 <span data-ttu-id="94b12-145">목록에서 파일 연결 관리자를 선택하거나 \<**New connection...**>을 클릭하여 새 연결 관리자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="94b12-145">Select a File connection manager in the list, or click \<**New connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="94b12-146">**관련 항목:** [파일 연결 관리자](connection-manager/file-connection-manager.md), [파일 연결 관리자 편집기](../../2014/integration-services/file-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="94b12-146">**Related Topics:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)</span></span>  
  
### <a name="wqlquerysourcetype--variable"></a><span data-ttu-id="94b12-147">WQLQuerySourceType = 변수</span><span class="sxs-lookup"><span data-stu-id="94b12-147">WQLQuerySourceType = Variable</span></span>  
 <span data-ttu-id="94b12-148">**WQLQuerySource**</span><span class="sxs-lookup"><span data-stu-id="94b12-148">**WQLQuerySource**</span></span>  
 <span data-ttu-id="94b12-149">목록에서 변수를 선택하거나 \<**New variable...**>를 클릭하여 새 변수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="94b12-149">Select a variable in the list, or click \<**New variable...**> to create a new variable.</span></span>  
  
 <span data-ttu-id="94b12-150">**관련 항목:** [Integration Services&#40;SSIS&#41; 변수](integration-services-ssis-variables.md), [변수 추가](../../2014/integration-services/add-variable.md)</span><span class="sxs-lookup"><span data-stu-id="94b12-150">**Related Topics:** [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), [Add Variable](../../2014/integration-services/add-variable.md)</span></span>  
  
## <a name="destinationtype-dynamic-options"></a><span data-ttu-id="94b12-151">DestinationType 동적 옵션</span><span class="sxs-lookup"><span data-stu-id="94b12-151">DestinationType Dynamic Options</span></span>  
  
### <a name="destinationtype--file-connection"></a><span data-ttu-id="94b12-152">DestinationType = 파일 연결</span><span class="sxs-lookup"><span data-stu-id="94b12-152">DestinationType = File connection</span></span>  
 <span data-ttu-id="94b12-153">**대상**</span><span class="sxs-lookup"><span data-stu-id="94b12-153">**Destination**</span></span>  
 <span data-ttu-id="94b12-154">목록에서 파일 연결 관리자를 선택하거나 \<**New connection...**>을 클릭하여 새 연결 관리자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="94b12-154">Select a File connection manager in the list, or click \<**New connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="94b12-155">**관련 항목:** [파일 연결 관리자](connection-manager/file-connection-manager.md), [파일 연결 관리자 편집기](../../2014/integration-services/file-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="94b12-155">**Related Topics:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)</span></span>  
  
### <a name="destinationtype--variable"></a><span data-ttu-id="94b12-156">DestinationType = 변수</span><span class="sxs-lookup"><span data-stu-id="94b12-156">DestinationType = Variable</span></span>  
 <span data-ttu-id="94b12-157">**대상**</span><span class="sxs-lookup"><span data-stu-id="94b12-157">**Destination**</span></span>  
 <span data-ttu-id="94b12-158">목록에서 변수를 선택하거나 \<**New variable...**>를 클릭하여 새 변수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="94b12-158">Select a variable in the list, or click \<**New variable...**> to create a new variable.</span></span>  
  
 <span data-ttu-id="94b12-159">**관련 항목:** [Integration Services&#40;SSIS&#41; 변수](integration-services-ssis-variables.md), [변수 추가](../../2014/integration-services/add-variable.md)</span><span class="sxs-lookup"><span data-stu-id="94b12-159">**Related Topics:** [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), [Add Variable](../../2014/integration-services/add-variable.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94b12-160">참고 항목</span><span class="sxs-lookup"><span data-stu-id="94b12-160">See Also</span></span>  
 <span data-ttu-id="94b12-161">[Integration Services 오류 및 메시지 참조](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="94b12-161">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="94b12-162">[WMI 데이터 판독기 태스크 편집기 &#40;일반 페이지&#41;](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="94b12-162">[WMI Data Reader Task Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="94b12-163">[식 페이지](expressions/expressions-page.md) </span><span class="sxs-lookup"><span data-stu-id="94b12-163">[Expressions Page](expressions/expressions-page.md) </span></span>  
 [<span data-ttu-id="94b12-164">WMI 이벤트 감시자 태스크</span><span class="sxs-lookup"><span data-stu-id="94b12-164">WMI Event Watcher Task</span></span>](control-flow/wmi-event-watcher-task.md)  
  
  
