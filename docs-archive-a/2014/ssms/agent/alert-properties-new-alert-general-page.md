---
title: 경고 속성-새 경고 (일반 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.ag.alert.general.f1
ms.assetid: f5c11610-62e3-44df-9800-a5dc35be4a09
author: stevestein
ms.author: sstein
ms.openlocfilehash: 471b0062ecc805e83020495e422f8914baec5f71
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737498"
---
# <a name="alert-properties-new-alert-general-page"></a><span data-ttu-id="e2360-102">경고 속성-새 경고 (일반 페이지)</span><span class="sxs-lookup"><span data-stu-id="e2360-102">Alert Properties-New Alert (General Page)</span></span>
  <span data-ttu-id="e2360-103">이 페이지를 사용 하 여 에이전트 경고의 일반 속성을 확인 하 고 수정할 수 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2360-103">Use this page to view and modify the general properties of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent alerts.</span></span>  
  
## <a name="options"></a><span data-ttu-id="e2360-104">옵션</span><span class="sxs-lookup"><span data-stu-id="e2360-104">Options</span></span>  
 <span data-ttu-id="e2360-105">**이름**</span><span class="sxs-lookup"><span data-stu-id="e2360-105">**Name**</span></span>  
 <span data-ttu-id="e2360-106">경고 이름을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="e2360-106">Change the name of the alert.</span></span>  
  
 <span data-ttu-id="e2360-107">**사용**</span><span class="sxs-lookup"><span data-stu-id="e2360-107">**Enable**</span></span>  
 <span data-ttu-id="e2360-108">경고를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="e2360-108">Enable the alert.</span></span> <span data-ttu-id="e2360-109">경고를 설정하지 않으면 경고에 지정된 동작이 수행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e2360-109">When the alert is not enabled, the actions specified in the alert do not occur.</span></span>  
  
 <span data-ttu-id="e2360-110">**형식**</span><span class="sxs-lookup"><span data-stu-id="e2360-110">**Type**</span></span>  
 <span data-ttu-id="e2360-111">경고 유형을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e2360-111">Select the type of alert:</span></span>  
  
-   <span data-ttu-id="e2360-112">**SQL Server 이벤트 경고** - [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 이벤트 로그의 메시지에 응답합니다.</span><span class="sxs-lookup"><span data-stu-id="e2360-112">**SQL Server event alert** responds to messages in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows event log.</span></span>  
  
-   <span data-ttu-id="e2360-113">**SQL Server 성능 조건 경고** - 성능 카운터의 특정 조건에 응답합니다.</span><span class="sxs-lookup"><span data-stu-id="e2360-113">**SQL Server performance condition alert** responds to a specific condition in a performance counter.</span></span>  
  
-   <span data-ttu-id="e2360-114">**WMI 이벤트 경고** - WMI(Windows Management Instrumentation) 이벤트에 응답합니다.</span><span class="sxs-lookup"><span data-stu-id="e2360-114">**WMI event alert** responds to a Windows Management Instrumentation (WMI) event.</span></span>  
  
## <a name="sql-server-event-alert-options"></a><span data-ttu-id="e2360-115">SQL Server 이벤트 경고 옵션</span><span class="sxs-lookup"><span data-stu-id="e2360-115">SQL Server Event Alert Options</span></span>  
 <span data-ttu-id="e2360-116">**데이터베이스 이름**</span><span class="sxs-lookup"><span data-stu-id="e2360-116">**Database name**</span></span>  
 <span data-ttu-id="e2360-117">이벤트에 대한 데이터베이스를 지정하거나, 이벤트가 발생하는 데이터베이스에 관계없이 메시지에 응답하도록 하려면 **모든 데이터베이스** 를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e2360-117">Specify a database for the event, or **all databases** to respond to a message regardless of the database where the event occurs.</span></span>  
  
 <span data-ttu-id="e2360-118">**오류 번호**</span><span class="sxs-lookup"><span data-stu-id="e2360-118">**Error number**</span></span>  
 <span data-ttu-id="e2360-119">이 이벤트가 오류에 응답하도록 지정하고 오류 번호를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e2360-119">Specify that this event responds to an error, and specify the error number.</span></span>  
  
 <span data-ttu-id="e2360-120">**심각도**</span><span class="sxs-lookup"><span data-stu-id="e2360-120">**Severity**</span></span>  
 <span data-ttu-id="e2360-121">이 이벤트가 특정 심각도를 지닌 메시지에 응답하도록 지정하고 심각도를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e2360-121">Specify that this event responds to any message with a specific severity level, and specify the severity level.</span></span>  
  
 <span data-ttu-id="e2360-122">**메시지에 다음 텍스트가 포함될 때 경고 발생**</span><span class="sxs-lookup"><span data-stu-id="e2360-122">**Raise alert when message contains**</span></span>  
 <span data-ttu-id="e2360-123">특정 문자열로 이벤트를 필터링합니다.</span><span class="sxs-lookup"><span data-stu-id="e2360-123">Filter events by a specific string.</span></span> <span data-ttu-id="e2360-124">이 옵션을 선택하면 경고가 특정 문자열을 포함하는 이벤트에 대해서만 응답합니다.</span><span class="sxs-lookup"><span data-stu-id="e2360-124">When this option is selected, the alert only responds to events that contain a specific string.</span></span>  
  
 <span data-ttu-id="e2360-125">**메시지 텍스트**</span><span class="sxs-lookup"><span data-stu-id="e2360-125">**Message text**</span></span>  
 <span data-ttu-id="e2360-126">이벤트를 필터링할 때 사용할 문자열을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e2360-126">Specify the string to use to filter events.</span></span>  
  
## <a name="sql-server-performance-condition-alerts"></a><span data-ttu-id="e2360-127">SQL Server 성능 조건 경고</span><span class="sxs-lookup"><span data-stu-id="e2360-127">SQL Server Performance Condition Alerts</span></span>  
 <span data-ttu-id="e2360-128">**Object**</span><span class="sxs-lookup"><span data-stu-id="e2360-128">**Object**</span></span>  
 <span data-ttu-id="e2360-129">모니터링할 성능 개체를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e2360-129">Specify the performance object to monitor.</span></span>  
  
 <span data-ttu-id="e2360-130">**카운터**</span><span class="sxs-lookup"><span data-stu-id="e2360-130">**Counter**</span></span>  
 <span data-ttu-id="e2360-131">모니터링할 성능 개체 내의 카운터를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e2360-131">Specify the counter within the performance object to monitor.</span></span>  
  
 <span data-ttu-id="e2360-132">**인스턴스**</span><span class="sxs-lookup"><span data-stu-id="e2360-132">**Instance**</span></span>  
 <span data-ttu-id="e2360-133">모니터링할 카운터의 인스턴스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e2360-133">Specify the instance of the counter to monitor.</span></span>  
  
 <span data-ttu-id="e2360-134">**경고 발생 카운터**</span><span class="sxs-lookup"><span data-stu-id="e2360-134">**Alert if counter**</span></span>  
 <span data-ttu-id="e2360-135">경고가 응답하는 카운터의 동작을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e2360-135">Specify the behavior of the counter that the alert responds to.</span></span> <span data-ttu-id="e2360-136">예를 들어 경고를 **Free space in tempdb (KB)** 카운터의 값이 특정 값 미만이 될 때 응답하도록 지정하거나 **SQL Compilations/sec** 가 특정 값을 초과할 때 응답하도록 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2360-136">For example, you may want the alert to respond to a condition where the value of the **Free space in tempdb (KB)** counter falls below a certain value, or you may want the alert to respond to a condition where the **SQL Compilations/sec** rises above a certain value.</span></span>  
  
 <span data-ttu-id="e2360-137">**값**</span><span class="sxs-lookup"><span data-stu-id="e2360-137">**Value**</span></span>  
 <span data-ttu-id="e2360-138">카운터에 대한 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e2360-138">Specify a value for the counter.</span></span>  
  
## <a name="wmi-event-alert-options"></a><span data-ttu-id="e2360-139">WMI 이벤트 경고 옵션</span><span class="sxs-lookup"><span data-stu-id="e2360-139">WMI Event Alert Options</span></span>  
 <span data-ttu-id="e2360-140">**Namespace**</span><span class="sxs-lookup"><span data-stu-id="e2360-140">**Namespace**</span></span>  
 <span data-ttu-id="e2360-141">WQL(WMI Query Language) 문에 사용할 네임스페이스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e2360-141">Specify the namespace to use for the WMI Query Language (WQL) statement.</span></span> <span data-ttu-id="e2360-142">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트를 실행하는 컴퓨터의 네임스페이스만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="e2360-142">Only namespaces on the computer that runs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent are supported.</span></span>  
  
 <span data-ttu-id="e2360-143">**쿼리**</span><span class="sxs-lookup"><span data-stu-id="e2360-143">**Query**</span></span>  
 <span data-ttu-id="e2360-144">경고 응답 이벤트를 식별하는 WQL 문을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e2360-144">Specify the WQL statement that identifies the event that the alert responds to.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2360-145">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e2360-145">See Also</span></span>  
 <span data-ttu-id="e2360-146">[Alerts](alerts.md) </span><span class="sxs-lookup"><span data-stu-id="e2360-146">[Alerts](alerts.md) </span></span>  
 <span data-ttu-id="e2360-147">[서버 이벤트 용 WMI 공급자에 WQL 사용](../../relational-databases/wmi-provider-server-events/using-wql-with-the-wmi-provider-for-server-events.md) </span><span class="sxs-lookup"><span data-stu-id="e2360-147">[Using WQL with the WMI Provider for Server Events](../../relational-databases/wmi-provider-server-events/using-wql-with-the-wmi-provider-for-server-events.md) </span></span>  
 <span data-ttu-id="e2360-148">[오류 번호를 사용 하 여 경고 만들기](create-an-alert-using-an-error-number.md) </span><span class="sxs-lookup"><span data-stu-id="e2360-148">[Create an Alert Using an Error Number](create-an-alert-using-an-error-number.md) </span></span>  
 [<span data-ttu-id="e2360-149">Create an Alert Using Severity Level</span><span class="sxs-lookup"><span data-stu-id="e2360-149">Create an Alert Using Severity Level</span></span>](create-an-alert-using-severity-level.md)  
  
  
