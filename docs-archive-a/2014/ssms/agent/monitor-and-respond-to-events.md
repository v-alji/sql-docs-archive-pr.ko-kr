---
title: 이벤트 모니터링 및 응답 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- notifications [SQL Server], alert
- events [SQL Server], alerts
- alerts [SQL Server]
- notifications [SQL Server]
- events [SQL Server], automatically responding to
- administrator notifications [SQL Server Agent]
- automatic event responses
- SQL Server Agent alerts
- monitoring [SQL Server], events
- responding to events automatically
ms.assetid: f7fbe155-5b68-4777-bc71-a47637471f32
author: stevestein
ms.author: sstein
ms.openlocfilehash: afdf1beffd6099fce84f03a8ba65f7de9abb8f0b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731328"
---
# <a name="monitor-and-respond-to-events"></a><span data-ttu-id="48285-102">이벤트 모니터링 및 응답</span><span class="sxs-lookup"><span data-stu-id="48285-102">Monitor and Respond to Events</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="48285-103">에이전트는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 메시지, 특정 성능 조건 및 WMI(Windows Management Instrumentation) 이벤트와 같은 *이벤트*를 모니터링하고 자동으로 응답할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="48285-103">Agent can monitor and automatically respond to *events*, such as messages from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], specific performance conditions, and Windows Management Instrumentation (WMI) events.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="48285-104">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="48285-104">In This Section</span></span>  
 [<span data-ttu-id="48285-105">경고</span><span class="sxs-lookup"><span data-stu-id="48285-105">Alerts</span></span>](alerts.md)  
 <span data-ttu-id="48285-106">경고 명명 방법과 경고가 응답할 이벤트나 성능 조건을 선택하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="48285-106">Contains information about naming an alert and selecting the events or performance conditions to which alerts respond.</span></span>  
  
 [<span data-ttu-id="48285-107">사용자 정의 이벤트 만들기</span><span class="sxs-lookup"><span data-stu-id="48285-107">Create a User-Defined Event</span></span>](create-a-user-defined-event.md)  
 <span data-ttu-id="48285-108">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에 미리 정의된 이벤트 이외의 이벤트를 만드는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="48285-108">Contains information about how to create events other than those that are predefined by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="48285-109">연산자</span><span class="sxs-lookup"><span data-stu-id="48285-109">Operators</span></span>](operators.md)  
 <span data-ttu-id="48285-110">작업 실패 또는 작업 성공 시 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트가 알림을 보내기 위해 사용할 수 있는 관리자용 별칭을 만드는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="48285-110">Contains information about creating aliases for administrators that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent can use to send notifications when jobs fail or succeed.</span></span>  
  
## <a name="about-monitoring-and-responding-to-events"></a><span data-ttu-id="48285-111">이벤트 모니터링 및 응답 정보</span><span class="sxs-lookup"><span data-stu-id="48285-111">About Monitoring and Responding to Events</span></span>  
 <span data-ttu-id="48285-112">이벤트에 대한 자동화된 응답을 *경고*라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="48285-112">Automated responses to events are called *alerts*.</span></span> <span data-ttu-id="48285-113">하나 이상의 이벤트에 대한 경고를 정의하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트가 이벤트 발생에 응답하는 방법을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="48285-113">You can define an alert on one or more events to specify how you want [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to respond to their occurrence.</span></span> <span data-ttu-id="48285-114">경고는 관리자에게 알리거나 작업을 실행하거나 또는 두 가지 방법을 모두 사용하여 이벤트에 응답할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="48285-114">An alert can respond to an event by notifying an administrator or running a job, or both.</span></span> <span data-ttu-id="48285-115">경고는 다른 컴퓨터의 Microsoft Windows 애플리케이션 로그에 이벤트를 전달할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="48285-115">An alert can also forward an event to the Microsoft Windows application log on a different computer.</span></span> <span data-ttu-id="48285-116">예를 들어 심각도가 19인 이벤트가 발생하면 운영자가 즉시 알림을 받을 수 있도록 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="48285-116">For example, you can specify that an operator be notified immediately if an event of severity 19 occurs.</span></span> <span data-ttu-id="48285-117">경고를 정의하면 데이터베이스 관리자가 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]를 보다 효과적으로 모니터링하고 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="48285-117">By defining alerts, database administrators can more effectively monitor and manage [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="48285-118">에이전트는 경고가 정의된 이벤트에만 응답합니다.</span><span class="sxs-lookup"><span data-stu-id="48285-118">Agent only responds to events for which an alert is defined.</span></span> <span data-ttu-id="48285-119">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트가 이벤트를 모니터링하기 위해 사용하는 방법은 이벤트 유형에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="48285-119">The method that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent uses to monitor events depends on the type of event.</span></span>  
  
 <span data-ttu-id="48285-120">성능 카운터에 대해 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 경고가 정의되어 있는 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트는 성능 카운터를 직접 모니터링합니다.</span><span class="sxs-lookup"><span data-stu-id="48285-120">When a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent alert is defined for a performance counter, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent directly monitors the performance counter.</span></span> <span data-ttu-id="48285-121">WMI 이벤트의 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트는 WMI 이벤트에 대한 이벤트 쿼리를 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="48285-121">For a WMI event, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent registers an event query for the WMI event.</span></span>  
  
 <span data-ttu-id="48285-122">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 메시지에 응답하기 위해 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트는 Windows 애플리케이션 로그를 모니터링합니다.</span><span class="sxs-lookup"><span data-stu-id="48285-122">To respond to messages from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent monitors the Windows application log.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="48285-123">에이전트는 이 로그에 나타나는 메시지에만 응답할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="48285-123">Agent can only respond to messages that appear in this log.</span></span> <span data-ttu-id="48285-124">기본적으로 SQL Server는 다음 메시지를 Windows 애플리케이션 로그에 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="48285-124">By default, SQL Server logs the following messages in the Windows application log:</span></span>  
  
-   <span data-ttu-id="48285-125">심각도가 19 이상인 sysmessages 오류</span><span class="sxs-lookup"><span data-stu-id="48285-125">Severity 19 or higher sysmessages errors.</span></span>  
  
     <span data-ttu-id="48285-126">심각도가 19 이하인 특정 sysmessages 오류도 기록하려면 sp_altermessage 저장 프로시저를 사용하여 그러한 오류를 "항상 기록"하도록 지정하십시오.</span><span class="sxs-lookup"><span data-stu-id="48285-126">If you also want to log specific sysmessages errors that have a severity lower than 19, use the sp_altermessage stored procedure to designate such errors as "always logged".</span></span>  
  
-   <span data-ttu-id="48285-127">WITH LOG 구문을 사용하여 호출된 모든 RAISERROR 문</span><span class="sxs-lookup"><span data-stu-id="48285-127">Any RAISERROR statement invoked by using the WITH LOG syntax.</span></span>  
  
     <span data-ttu-id="48285-128">RAISERROR WITH LOG 사용은 SQL Server 인스턴스의 메시지를 Windows 애플리케이션 로그에 쓸 때 권장되는 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="48285-128">Using RAISERROR WITH LOG is the recommended way to write to the Windows application log from an instance of SQL Server.</span></span>  
  
-   <span data-ttu-id="48285-129">xp_logevent를 사용하여 기록된 모든 애플리케이션 이벤트</span><span class="sxs-lookup"><span data-stu-id="48285-129">Any application event that is logged by using xp_logevent.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="48285-130">애플리케이션 이벤트를 기록하면 로그 공간이 사용되므로 Windows 애플리케이션 로그가 최대 크기를 초과할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="48285-130">Logging application events consumes log space and can cause the Windows application log to exceed its maximum size.</span></span> <span data-ttu-id="48285-131">최대 Windows 애플리케이션 로그 크기를 충분히 크게 설정하여 SQL Server 이벤트 정보가 손실되지 않도록 하십시오.</span><span class="sxs-lookup"><span data-stu-id="48285-131">Make sure that the maximum Windows application log size is large enough to avoid loss of SQL Server event information.</span></span>  
  
 <span data-ttu-id="48285-132">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 메시지를 기록하면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 서비스는 메시지를 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 관리자가 정의한 경고와 비교합니다.</span><span class="sxs-lookup"><span data-stu-id="48285-132">When [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] logs a message, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service compares the message against the alerts defined by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] administrator.</span></span>  
  
 <span data-ttu-id="48285-133">이벤트 원본에 관계 없이 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 서비스는 이벤트에 대한 경고에 지정된 태스크를 수행하여 이벤트에 응답합니다.</span><span class="sxs-lookup"><span data-stu-id="48285-133">Regardless of the source of the event, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service responds to the event by performing the tasks specified in the alert for the event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48285-134">참고 항목</span><span class="sxs-lookup"><span data-stu-id="48285-134">See Also</span></span>  
 [<span data-ttu-id="48285-135">Transact-sql&#41;sp_altermessage &#40;</span><span class="sxs-lookup"><span data-stu-id="48285-135">sp_altermessage &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-altermessage-transact-sql)  
  
  
