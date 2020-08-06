---
title: Windows용 이벤트 추적 대상 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xevents
ms.topic: conceptual
helpviewer_keywords:
- event tracing for windows target
- ETW target
- targets [SQL Server extended events], event tracing for windows target
ms.assetid: ca2bb295-b7f6-49c3-91ed-0ad4c39f89d5
author: rothja
ms.author: jroth
ms.openlocfilehash: 55f247af30b5278f614b6505a94266cc07ec6c54
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647019"
---
# <a name="event-tracing-for-windows-target"></a><span data-ttu-id="2a44a-102">Windows용 이벤트 추적 대상</span><span class="sxs-lookup"><span data-stu-id="2a44a-102">Event Tracing for Windows Target</span></span>
  <span data-ttu-id="2a44a-103">ETW(Windows용 이벤트 추적)를 대상으로 사용하려면 먼저 ETW에 대한 실무 지식을 갖추고 있는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="2a44a-103">Before you use Event Tracing for Windows (ETW) as a target, we recommend that you have a working knowledge of ETW.</span></span> <span data-ttu-id="2a44a-104">ETW 추적은 확장 이벤트와 함께 사용되거나 확장 이벤트의 이벤트 소비자로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="2a44a-104">ETW tracing is either used together with Extended Events or as an Extended Events event consumer.</span></span> <span data-ttu-id="2a44a-105">다음 외부 링크를 클릭하면 ETW에 대한 배경 지식을 제공하는 항목으로 연결됩니다.</span><span class="sxs-lookup"><span data-stu-id="2a44a-105">The following external links provide a starting point for obtaining background information about ETW:</span></span>  
  
-   [<span data-ttu-id="2a44a-106">Windows 이벤트</span><span class="sxs-lookup"><span data-stu-id="2a44a-106">Windows Events</span></span>](https://go.microsoft.com/fwlink/?LinkId=92380)  
  
-   [<span data-ttu-id="2a44a-107">ETW를 사용한 디버깅 및 성능 조정 개선</span><span class="sxs-lookup"><span data-stu-id="2a44a-107">Improve Debugging And Performance Tuning With ETW</span></span>](https://go.microsoft.com/fwlink/?LinkId=92381)  
  
 <span data-ttu-id="2a44a-108">ETW 대상을 여러 세션에 추가할 수 있지만 이는 단일 대상입니다.</span><span class="sxs-lookup"><span data-stu-id="2a44a-108">The ETW target is a singleton target, although the target can be added to many sessions.</span></span> <span data-ttu-id="2a44a-109">한 이벤트가 여러 세션에서 발생하는 경우 해당 이벤트는 발생 항목당 한 번만 ETW 대상으로 전파됩니다.</span><span class="sxs-lookup"><span data-stu-id="2a44a-109">If an event is raised on many sessions, the event will only be propagated to the ETW target one time per event occurrence.</span></span> <span data-ttu-id="2a44a-110">확장 이벤트 엔진은 프로세스당 하나의 인스턴스로 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="2a44a-110">The Extended Events engine is limited to a single instance per process.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="2a44a-111">ETW 대상이 작동하려면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 서비스 시작 계정이 Performance Log Users 그룹의 멤버여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2a44a-111">For the ETW target to work, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Service startup account must be a member of the Performance Log Users group.</span></span>  
  
 <span data-ttu-id="2a44a-112">ETW 세션에 있는 이벤트의 구성은 확장 이벤트 엔진을 호스팅하는 프로세스에서 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="2a44a-112">The configuration of the events present in an ETW session is controlled by the process that hosts the Extended Events engine.</span></span> <span data-ttu-id="2a44a-113">엔진은 발생할 이벤트 및 이벤트 실행을 위해 충족해야 할 조건을 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="2a44a-113">The engine controls which events to raise and what conditions must be met for an event to occur.</span></span>  
  
 <span data-ttu-id="2a44a-114">ETW 대상이 프로세스의 수명이 유지되는 동안 처음으로 확장 이벤트 세션에 연결하여 바인딩되면 ETW 대상은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 공급자에서 단일 ETW 세션을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="2a44a-114">After binding to an Extended Events session, which attaches the ETW target for the first time during the lifetime of a process, the ETW target opens a single ETW session on the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider.</span></span> <span data-ttu-id="2a44a-115">ETW 세션이 이미 있으면 ETW 대상은 기존 세션에 대한 참조를 얻습니다.</span><span class="sxs-lookup"><span data-stu-id="2a44a-115">If an ETW session already exists, the ETW target obtains a reference to the existing session.</span></span> <span data-ttu-id="2a44a-116">이러한 ETW 세션은 지정된 컴퓨터의 모든 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스 전체에서 공유할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a44a-116">This ETW session is shared across all [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instances on a given computer.</span></span> <span data-ttu-id="2a44a-117">또한 이 ETW 세션은 ETW 대상이 있는 세션의 모든 이벤트를 수신합니다.</span><span class="sxs-lookup"><span data-stu-id="2a44a-117">This ETW session receives all the events from sessions that have the ETW target.</span></span>  
  
 <span data-ttu-id="2a44a-118">ETW 대상이 이벤트를 소비하고 이를 ETW로 전송하려면 공급자가 필요하므로 세션에는 모든 확장 이벤트 패키지가 활성화됩니다.</span><span class="sxs-lookup"><span data-stu-id="2a44a-118">Because ETW needs providers to be enabled to consume events and flow them down to the ETW, all Extended Events packages are enabled on the session.</span></span> <span data-ttu-id="2a44a-119">이벤트가 발생하면 ETW 대상은 이벤트에 대한 공급자가 활성화되어 있는 세션에 이벤트를 전송합니다.</span><span class="sxs-lookup"><span data-stu-id="2a44a-119">When an event is fired, the ETW target sends the event to the session on which the provider for the event is enabled.</span></span>  
  
 <span data-ttu-id="2a44a-120">ETW 대상은 이벤트를 발생시키는 스레드에서의 이벤트 동기 게시를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="2a44a-120">The ETW target supports synchronous publishing of events on the thread that raises the event.</span></span> <span data-ttu-id="2a44a-121">하지만 ETW 대상은 비동기 이벤트 게시를 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2a44a-121">However, the ETW target does not support asynchronous event publishing.</span></span>  
  
 <span data-ttu-id="2a44a-122">ETW 대상은 Logman.exe와 같은 외부 ETW 컨트롤러를 제어하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2a44a-122">The ETW target does not support control from external ETW controllers such as Logman.exe.</span></span> <span data-ttu-id="2a44a-123">ETW 추적을 생성하려면 ETW 대상으로 이벤트 세션을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2a44a-123">To produce ETW traces, an event session must be created with the ETW target.</span></span> <span data-ttu-id="2a44a-124">자세한 내용은 [CREATE EVENT SESSION&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-event-session-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2a44a-124">For more information, see [CREATE EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-event-session-transact-sql).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2a44a-125">ETW 대상을 활성화하면 이름이 XE_DEFAULT_ETW_SESSION인 ETW 세션이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="2a44a-125">Enabling the ETW target creates an ETW session that is named XE_DEFAULT_ETW_SESSION.</span></span> <span data-ttu-id="2a44a-126">XE_DEFAULT_ETW_SESSION이라는 세션이 이미 있는 경우에는 기존 세션이 속성 수정 없이 그대로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="2a44a-126">If a session with the name XE_DEFAULT_ETW_SESSION already exists, it is used without modifying any properties of the existing session.</span></span> <span data-ttu-id="2a44a-127">XE_DEFAULT_ETW_SESSION은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 모든 인스턴스 간에 공유됩니다.</span><span class="sxs-lookup"><span data-stu-id="2a44a-127">The XE_DEFAULT_ETW_SESSION is shared between all instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="2a44a-128">XE_DEFAULT_ETW_SESSION을 시작한 후에는 ETW 컨트롤러(예: Logman 도구)를 사용하여 중지해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2a44a-128">After you start the XE_DEFAULT_ETW_SESSION, you must stop it by using an ETW controller, such as the Logman tool.</span></span> <span data-ttu-id="2a44a-129">예를 들어 명령 프롬프트에서 다음 명령을 실행할 수 있습니다. `logman stop XE_DEFAULT_ETW_SESSION -ets`</span><span class="sxs-lookup"><span data-stu-id="2a44a-129">For example, you can run the following command at the command prompt: `logman stop XE_DEFAULT_ETW_SESSION -ets`.</span></span>  
  
 <span data-ttu-id="2a44a-130">다음 표에서는 ETW 대상을 구성하는 데 사용할 수 있는 옵션에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="2a44a-130">The following table describes the available options for configuring the ETW target.</span></span>  
  
|<span data-ttu-id="2a44a-131">옵션</span><span class="sxs-lookup"><span data-stu-id="2a44a-131">Option</span></span>|<span data-ttu-id="2a44a-132">허용되는 값</span><span class="sxs-lookup"><span data-stu-id="2a44a-132">Allowed values</span></span>|<span data-ttu-id="2a44a-133">Description</span><span class="sxs-lookup"><span data-stu-id="2a44a-133">Description</span></span>|  
|------------|--------------------|-----------------|  
|<span data-ttu-id="2a44a-134">default_xe_session_name</span><span class="sxs-lookup"><span data-stu-id="2a44a-134">default_xe_session_name</span></span>|<span data-ttu-id="2a44a-135">최대 256자까지의 모든 문자열.</span><span class="sxs-lookup"><span data-stu-id="2a44a-135">Any string up to 256 characters.</span></span> <span data-ttu-id="2a44a-136">이 값은 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="2a44a-136">This value is optional.</span></span>|<span data-ttu-id="2a44a-137">확장 이벤트 세션 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="2a44a-137">The Extended Events session name.</span></span> <span data-ttu-id="2a44a-138">기본적으로 이 이름은 XE_DEFAULT_ETW_SESSION입니다.</span><span class="sxs-lookup"><span data-stu-id="2a44a-138">By default, this is XE_DEFAULT_ETW_SESSION.</span></span>|  
|<span data-ttu-id="2a44a-139">default_etw_session_logfile_path</span><span class="sxs-lookup"><span data-stu-id="2a44a-139">default_etw_session_logfile_path</span></span>|<span data-ttu-id="2a44a-140">최대 256자까지의 모든 문자열.</span><span class="sxs-lookup"><span data-stu-id="2a44a-140">Any string up to 256 characters.</span></span> <span data-ttu-id="2a44a-141">이 값은 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="2a44a-141">This value is optional.</span></span>|<span data-ttu-id="2a44a-142">확장 이벤트 세션의 로그 파일에 대한 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="2a44a-142">The path of the log file for the Extended Events session.</span></span> <span data-ttu-id="2a44a-143">기본적으로 이 경로는 %TEMP%\ XEEtw.etl입니다.</span><span class="sxs-lookup"><span data-stu-id="2a44a-143">By default, this is %TEMP%\ XEEtw.etl.</span></span>|  
|<span data-ttu-id="2a44a-144">default_etw_session_logfile_size_mb</span><span class="sxs-lookup"><span data-stu-id="2a44a-144">default_etw_session_logfile_size_mb</span></span>|<span data-ttu-id="2a44a-145">부호 없는 정수</span><span class="sxs-lookup"><span data-stu-id="2a44a-145">Any unsigned integer.</span></span> <span data-ttu-id="2a44a-146">이 값은 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="2a44a-146">This value is optional.</span></span>|<span data-ttu-id="2a44a-147">확장 이벤트 세션의 로그 파일 크기(MB)입니다.</span><span class="sxs-lookup"><span data-stu-id="2a44a-147">The log file size, in megabytes (MB), for the Extended Events session.</span></span> <span data-ttu-id="2a44a-148">기본값은 20MB입니다.</span><span class="sxs-lookup"><span data-stu-id="2a44a-148">The default is 20 MB.</span></span>|  
|<span data-ttu-id="2a44a-149">default_etw_session_buffer_size_kb</span><span class="sxs-lookup"><span data-stu-id="2a44a-149">default_etw_session_buffer_size_kb</span></span>|<span data-ttu-id="2a44a-150">부호 없는 정수</span><span class="sxs-lookup"><span data-stu-id="2a44a-150">Any unsigned integer.</span></span> <span data-ttu-id="2a44a-151">이 값은 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="2a44a-151">This value is optional.</span></span>|<span data-ttu-id="2a44a-152">확장 이벤트 세션의 메모리 내 버퍼 크기(KB)입니다.</span><span class="sxs-lookup"><span data-stu-id="2a44a-152">The in-memory buffer size, in kilobytes (KB), for the Extended Events session.</span></span> <span data-ttu-id="2a44a-153">기본값은 128KB입니다.</span><span class="sxs-lookup"><span data-stu-id="2a44a-153">The default is 128 KB.</span></span>|  
|<span data-ttu-id="2a44a-154">retries</span><span class="sxs-lookup"><span data-stu-id="2a44a-154">retries</span></span>|<span data-ttu-id="2a44a-155">부호 없는 정수</span><span class="sxs-lookup"><span data-stu-id="2a44a-155">Any unsigned integer.</span></span>|<span data-ttu-id="2a44a-156">이벤트가 삭제되기 전에 ETW 하위 시스템에 이벤트 게시를 재시도한 횟수입니다.</span><span class="sxs-lookup"><span data-stu-id="2a44a-156">The number of times to retry publishing the event to the ETW subsystem before dropping the event.</span></span> <span data-ttu-id="2a44a-157">기본값은 0입니다.</span><span class="sxs-lookup"><span data-stu-id="2a44a-157">The default is 0.</span></span>|  
  
 <span data-ttu-id="2a44a-158">이러한 설정의 구성은 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="2a44a-158">Configuring these settings is optional.</span></span> <span data-ttu-id="2a44a-159">ETW 대상은 이러한 설정에 대해 기본값을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="2a44a-159">The ETW target uses default values for these settings.</span></span>  
  
 <span data-ttu-id="2a44a-160">ETW 대상의 역할은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="2a44a-160">The ETW target is responsible for:</span></span>  
  
-   <span data-ttu-id="2a44a-161">기본 ETW 세션을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="2a44a-161">Creating the default ETW session.</span></span>  
  
-   <span data-ttu-id="2a44a-162">ETW로 모든 확장 이벤트 패키지를 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="2a44a-162">Registering all Extended Events packages with ETW.</span></span> <span data-ttu-id="2a44a-163">이렇게 하면 이벤트가 ETW에 의해 삭제되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2a44a-163">This ensures that events are not dropped by ETW.</span></span>  
  
-   <span data-ttu-id="2a44a-164">ETW로의 이벤트 흐름을 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="2a44a-164">Managing the flow of events to ETW.</span></span> <span data-ttu-id="2a44a-165">ETW 대상은 확장 이벤트 데이터를 사용하여 ETW 이벤트를 만들고 적절한 ETW 세션에 전송합니다.</span><span class="sxs-lookup"><span data-stu-id="2a44a-165">The ETW target creates an ETW event with Extended Events data and sends it to the appropriate ETW session.</span></span> <span data-ttu-id="2a44a-166">이벤트가 버퍼 크기보다 크거나 데이터가 ETW 이벤트에 맞지 않는 경우 ETW는 이벤트를 조각으로 분할합니다.</span><span class="sxs-lookup"><span data-stu-id="2a44a-166">If the event is larger than the buffer size, or data cannot fit in one ETW event, ETW splits the event into fragments.</span></span>  
  
-   <span data-ttu-id="2a44a-167">확장 이벤트 패키지를 항상 활성화된 상태로 유지합니다.</span><span class="sxs-lookup"><span data-stu-id="2a44a-167">Keeping Extended Events packages enabled at all times.</span></span>  
  
 <span data-ttu-id="2a44a-168">ETW에서 사용하는 기본 파일 위치는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="2a44a-168">The following default file locations are used by ETW:</span></span>  
  
-   <span data-ttu-id="2a44a-169">ETW 출력 파일은 %TEMP%\XEEtw.etl에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="2a44a-169">The ETW output file is in %TEMP%\XEEtw.etl.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="2a44a-170">첫 번째 세션이 시작되면 파일 경로를 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2a44a-170">The file path cannot be changed after the first session starts.</span></span>  
  
-   <span data-ttu-id="2a44a-171">MOF(Managed Object Format) 파일은 *\<your install path>* \Microsoft SQL Server\Shared에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a44a-171">Managed Object Format (MOF) files are in *\<your install path>* \Microsoft SQL Server\Shared.</span></span> <span data-ttu-id="2a44a-172">자세한 내용은 MSDN의 [Managed Object Format](https://go.microsoft.com/fwlink/?LinkId=92851) 을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="2a44a-172">For more information, see [Managed Object Format](https://go.microsoft.com/fwlink/?LinkId=92851) on MSDN.</span></span>  
  
## <a name="adding-the-target-to-a-session"></a><span data-ttu-id="2a44a-173">세션에 대상 추가</span><span class="sxs-lookup"><span data-stu-id="2a44a-173">Adding the Target to a Session</span></span>  
 <span data-ttu-id="2a44a-174">확장 이벤트 세션에 ETW 대상을 추가하려면 이벤트 세션을 만들거나 변경할 때 다음 문을 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2a44a-174">To add the ETW target to an Extended Events session, you must include the following statement when you create or alter an event session:</span></span>  
  
```  
ADD TARGET package0.etw_classic_sync_target  
```  
  
 <span data-ttu-id="2a44a-175">데이터를 보는 방법을 비롯한 ETW 대상을 사용하는 방법을 보여 주는 전체 예에 대한 자세한 내용은 [확장 이벤트를 사용하여 시스템 작업 모니터링](monitor-system-activity-using-extended-events.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2a44a-175">For more information about a full example that shows how to use the ETW target, including how to view the data, see [Monitor System Activity Using Extended Events](monitor-system-activity-using-extended-events.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a44a-176">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2a44a-176">See Also</span></span>  
 <span data-ttu-id="2a44a-177">[SQL Server 확장 이벤트 대상](../../database-engine/sql-server-extended-events-targets.md) </span><span class="sxs-lookup"><span data-stu-id="2a44a-177">[SQL Server Extended Events Targets](../../database-engine/sql-server-extended-events-targets.md) </span></span>  
 <span data-ttu-id="2a44a-178">[sys.dm_xe_session_targets&#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-session-targets-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="2a44a-178">[sys.dm_xe_session_targets &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-session-targets-transact-sql) </span></span>  
 <span data-ttu-id="2a44a-179">[CREATE EVENT SESSION&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-event-session-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="2a44a-179">[CREATE EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-event-session-transact-sql) </span></span>  
 [<span data-ttu-id="2a44a-180">ALTER EVENT SESSION&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="2a44a-180">ALTER EVENT SESSION &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-event-session-transact-sql)  
  
  
