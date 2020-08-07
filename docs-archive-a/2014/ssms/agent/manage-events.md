---
title: 이벤트 관리 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- event forwarding servers [SQL Server]
- events [SQL Server], forwarding
- event-triggered jobs [SQL Server]
- forwarding events [SQL Server]
- alerts [SQL Server], forwarded events
- alerts [SQL Server], management servers
- SQL Server Agent alerts, management servers
ms.assetid: 8f4ee7f5-80df-49fd-b2b8-d020e04b6e1b
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7ca6d56440b06d285cbb90f8d92325d59a452c16
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727899"
---
# <a name="manage-events"></a><span data-ttu-id="be552-102">이벤트 관리</span><span class="sxs-lookup"><span data-stu-id="be552-102">Manage Events</span></span>
  <span data-ttu-id="be552-103">특정 오류 심각도에 도달하거나 넘어선 모든 이벤트 메시지를 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 전달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="be552-103">You can forward to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] all event messages that meet or exceed a specific error severity level.</span></span> <span data-ttu-id="be552-104">이를 *이벤트 전달*이라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="be552-104">This is called *event forwarding*.</span></span> <span data-ttu-id="be552-105">전달 서버는 마스터 서버의 역할도 할 수 있는 전용 서버입니다.</span><span class="sxs-lookup"><span data-stu-id="be552-105">The forwarding server is a dedicated server that can also be a master server.</span></span> <span data-ttu-id="be552-106">이벤트 전달을 사용하면 서버 그룹에 대한 경고 관리를 중앙 집중화함으로써 많이 사용되는 서버의 작업을 줄일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="be552-106">You can use event forwarding to centralize alert management for a group of servers, thereby reducing the workload on heavily used servers.</span></span>  
  
 <span data-ttu-id="be552-107">한 대의 서버가 다른 서버 그룹에 대한 이벤트를 받을 때 이벤트를 받는 서버를 *경고 관리 서버*라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="be552-107">When one server receives events for a group of other servers, the server that receives events is called an *alerts management server*.</span></span> <span data-ttu-id="be552-108">다중 서버 환경에서는 마스터 서버를 경고 관리 서버로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="be552-108">In a multiserver environment, you designate the master server as the alerts management server.</span></span>  
  
## <a name="advantages-of-using-an-alerts-management-server"></a><span data-ttu-id="be552-109">경고 관리 서버 사용의 장점</span><span class="sxs-lookup"><span data-stu-id="be552-109">Advantages of Using an Alerts Management Server</span></span>  
 <span data-ttu-id="be552-110">경고 관리 서버를 설정하면 다음과 같은 장점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="be552-110">The advantages of setting up an alerts management server include:</span></span>  
  
-   <span data-ttu-id="be552-111">**중앙 집중식**-</span><span class="sxs-lookup"><span data-stu-id="be552-111">**Centralization**.</span></span> <span data-ttu-id="be552-112">여러 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스의 이벤트를 단일 서버에서 중앙 집중식으로 제어하고 간편하게 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="be552-112">Centralized control and a consolidated view of the events of several instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] are possible from a single server.</span></span>  
  
-   <span data-ttu-id="be552-113">**확장성**.</span><span class="sxs-lookup"><span data-stu-id="be552-113">**Scalability**.</span></span> <span data-ttu-id="be552-114">많은 물리적 서버를 한 대의 논리적 서버에서 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="be552-114">Many physical servers can be administered as one logical server.</span></span> <span data-ttu-id="be552-115">이 물리적 서버 그룹에 필요한 만큼 서버를 추가하거나 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="be552-115">You can add or remove servers to this physical server group as needed.</span></span>  
  
-   <span data-ttu-id="be552-116">**효율성**</span><span class="sxs-lookup"><span data-stu-id="be552-116">**Efficiency**.</span></span> <span data-ttu-id="be552-117">경고와 운영자를 한 번만 정의하면 되므로 구성 시간이 줄어듭니다.</span><span class="sxs-lookup"><span data-stu-id="be552-117">Configuration time is reduced, because you need to define alerts and operators only once.</span></span>  
  
## <a name="disadvantages-of-using-an-alerts-management-server"></a><span data-ttu-id="be552-118">경고 관리 서버 사용의 단점</span><span class="sxs-lookup"><span data-stu-id="be552-118">Disadvantages of Using an Alerts Management Server</span></span>  
 <span data-ttu-id="be552-119">경고 관리 서버를 설정하면 다음과 같은 단점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="be552-119">The disadvantages of setting up an alerts management server include:</span></span>  
  
-   <span data-ttu-id="be552-120">**트래픽 증가**-</span><span class="sxs-lookup"><span data-stu-id="be552-120">**Increased traffic**.</span></span> <span data-ttu-id="be552-121">이벤트를 경고 관리 서버에 전달하면 네트워크 트래픽이 증가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="be552-121">Forwarding events to an alerts management server can increase network traffic.</span></span> <span data-ttu-id="be552-122">지정한 심각도를 넘는 이벤트만 전달하도록 제한하면 이러한 트래픽 증가를 완화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="be552-122">This increase can be moderated by restricting event forwarding to events that are above a designated severity level.</span></span>  
  
-   <span data-ttu-id="be552-123">**단일 지점에서 실패**-</span><span class="sxs-lookup"><span data-stu-id="be552-123">**Single point of failure**.</span></span> <span data-ttu-id="be552-124">경고 관리 서버가 오프라인인 경우 관리되는 서버 그룹의 어떠한 이벤트에 대해서도 경고가 발생하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="be552-124">If the alerts management server goes offline, no alerts are issued for any event on the managed group of servers.</span></span>  
  
-   <span data-ttu-id="be552-125">**서버 로드**.</span><span class="sxs-lookup"><span data-stu-id="be552-125">**Server load**.</span></span> <span data-ttu-id="be552-126">전달된 이벤트에 대한 경고를 처리하면 경고 관리 서버의 처리량이 증가됩니다.</span><span class="sxs-lookup"><span data-stu-id="be552-126">Handling alerts for the forwarded events causes an increased processing load on the alerts management server.</span></span>  
  
## <a name="guidelines-for-using-an-alerts-management-server"></a><span data-ttu-id="be552-127">경고 관리 서버 사용을 위한 지침</span><span class="sxs-lookup"><span data-stu-id="be552-127">Guidelines for Using an Alerts Management Server</span></span>  
 <span data-ttu-id="be552-128">경고 관리 서버를 구성하는 경우 다음 지침을 따르십시오.</span><span class="sxs-lookup"><span data-stu-id="be552-128">When configuring an alerts management server, follow these guidelines:</span></span>  
  
-   <span data-ttu-id="be552-129">또한 전달된 이벤트를 수신하려면 경고 관리 서버가 SQL Server의 기본 인스턴스여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="be552-129">In order to receive forwarded events, the alerts management server must be a default instance of SQL Server.</span></span>  
  
-   <span data-ttu-id="be552-130">많이 사용되거나 중요한 애플리케이션을 경고 관리 서버에서 실행하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="be552-130">Avoid running critical or heavily used applications on the alerts management server.</span></span>  
  
-   <span data-ttu-id="be552-131">하나의 경고 관리 서버를 많은 서버에서 공유하도록 구성하는 데 있어 네트워크 트래픽을 신중히 계획합니다.</span><span class="sxs-lookup"><span data-stu-id="be552-131">Carefully plan for the network traffic involved in configuring many servers to share the same alerts management server.</span></span> <span data-ttu-id="be552-132">정체되는 경우에는 특정 경고 관리 서버를 사용하는 서버의 수를 줄입니다.</span><span class="sxs-lookup"><span data-stu-id="be552-132">If congestion results, reduce the number of servers that use a particular alerts management server.</span></span>  
  
     <span data-ttu-id="be552-133">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 에 등록된 서버는 경고 전달 서버에서 선택할 수 있는 서버 목록의 일부로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="be552-133">The servers that are registered within [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] constitute the list of servers available to be chosen by that server as the alerts-forwarding server.</span></span>  
  
-   <span data-ttu-id="be552-134">서버별 응답이 필요한 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 의 로컬 인스턴스에서는 경고를 경고 관리 서버에 전달하지 않고 로컬 인스턴스에 경고를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="be552-134">Define alerts on the local instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that require a server-specific response, instead of forwarding the alerts to the alerts management server.</span></span>  
  
     <span data-ttu-id="be552-135">경고 관리 서버는 자신에게 경고를 전달하는 모든 서버를 논리적인 통합체로 간주합니다.</span><span class="sxs-lookup"><span data-stu-id="be552-135">The alerts management server views all the servers forwarding to it as a logical whole.</span></span> <span data-ttu-id="be552-136">예를 들어 경고 관리 서버는 서버 A에서 전달된 605 이벤트와 서버 B에서 전달된 605 이벤트에 같은 방법으로 응답합니다.</span><span class="sxs-lookup"><span data-stu-id="be552-136">For example, an alerts management server responds in the same way to a 605 event from server A and a 605 event from server B.</span></span>  
  
-   <span data-ttu-id="be552-137">경고 시스템을 구성한 후 정기적으로 Microsoft Windows 애플리케이션 로그에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 이벤트를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="be552-137">After configuring your alert system, periodically check the Microsoft Windows application log for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent events.</span></span>  
  
     <span data-ttu-id="be552-138">경고 엔진에서 발생한 실패 내용은 "SQL Server 에이전트"라는 원본 이름으로 로컬 Windows 애플리케이션 로그에 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="be552-138">Failure conditions encountered by the alerts engine are written to the local Windows application log with a source name of "SQL Server Agent."</span></span> <span data-ttu-id="be552-139">예를 들어 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트가 정의된 전자 메일 알림을 보낼 수 없으면 이벤트가 애플리케이션 로그에 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="be552-139">For example, if [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent cannot send an e-mail notification as it has been defined, an event is logged in the application log.</span></span>  
  
 <span data-ttu-id="be552-140">로컬에 정의된 경고가 비활성화되고 경고를 표시하는 이벤트가 발생하는 경우 경고 전달 조건을 만족하면 그 이벤트는 경고 관리 서버로 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="be552-140">If a locally defined alert is inactivated, and an event occurs that would have caused the alert to fire, the event is forwarded to the alerts management server (if it satisfies the alert-forwarding condition).</span></span> <span data-ttu-id="be552-141">이러한 전달을 통해 로컬 사이트에 있는 사용자의 필요에 따라 경고 관리 서버에 정의된 경고가 로컬에서도 정의되는 경우 로컬에 정의된 경고를 무시하도록 설정하거나 해제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="be552-141">This forwarding allows local overrides (alerts defined locally that are also defined on the alerts management server) to be turned off and on as needed by the user at the local site.</span></span> <span data-ttu-id="be552-142">또한 로컬 경고에서 처리할 때라도 이벤트가 항상 전달되도록 요청할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="be552-142">You can also request that events always be forwarded, even if they are also handled by local alerts.</span></span>  
  
 <span data-ttu-id="be552-143">다중 서버 환경에서 이벤트를 관리하는 일반 태스크는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="be552-143">The following are common tasks for managing events in a multiserver environment:</span></span>  
  
 <span data-ttu-id="be552-144">**경고 관리 서버를 지정하려면**</span><span class="sxs-lookup"><span data-stu-id="be552-144">**To designate an alerts management server**</span></span>  
  
-   [<span data-ttu-id="be552-145">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="be552-145">SQL Server Management Studio</span></span>](../sql-server-management-studio-ssms.md)  
  
 <span data-ttu-id="be552-146">**경고에 대한 응답을 정의하려면**</span><span class="sxs-lookup"><span data-stu-id="be552-146">**To define the response to an alert**</span></span>  
  
-   [<span data-ttu-id="be552-147">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="be552-147">SQL Server Management Studio</span></span>](define-the-response-to-an-alert-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="be552-148">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="be552-148">Transact-SQL</span></span>](/sql/relational-databases/system-stored-procedures/sp-add-notification-transact-sql)  
  
## <a name="running-event-triggered-jobs"></a><span data-ttu-id="be552-149">이벤트 트리거된 작업의 실행</span><span class="sxs-lookup"><span data-stu-id="be552-149">Running Event-Triggered Jobs</span></span>  
 <span data-ttu-id="be552-150">경고에 응답하여 작업이 실행되도록 작업을 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="be552-150">You can define a job to be executed in response to an alert.</span></span> <span data-ttu-id="be552-151">예를 들어 작업을 실행하여 경고에서 감지한 문제를 진단하거나 해결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="be552-151">For example, you can execute a job that corrects or further diagnoses a problem detected by the alert.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="be552-152">작업에서 이벤트를 발생시킬 수 있으므로 재귀 경고 작업 루프를 만들지 않도록 주의하십시오.</span><span class="sxs-lookup"><span data-stu-id="be552-152">Because a job can raise an event, be careful not to create a recursive alert-job loop.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be552-153">참고 항목</span><span class="sxs-lookup"><span data-stu-id="be552-153">See Also</span></span>  
 [<span data-ttu-id="be552-154">Transact-sql&#41;메시지 &#40;sys.sys</span><span class="sxs-lookup"><span data-stu-id="be552-154">sys.sysmessages &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-compatibility-views/sys-sysmessages-transact-sql)  
  
  
