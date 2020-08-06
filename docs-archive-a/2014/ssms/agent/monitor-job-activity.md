---
title: 작업 활동 모니터링 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, monitoring
- jobs [SQL Server Agent], monitoring
- monitoring [SQL Server], jobs
- activity monitoring [SQL Server Agent]
- monitoring [SQL Server], SQL Server Agent
- monitoring [SQL Server Agent]
- SQL Server Agent Job Activity Monitor
- SQL Server Agent jobs, monitoring
- performance [SQL Server], jobs
- current activity
ms.assetid: 71cb432b-631d-4b8b-9965-e731b3d8266d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5088e029e90b4556c1559f8c948e8a8734762749
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649331"
---
# <a name="monitor-job-activity"></a><span data-ttu-id="46edc-102">작업 활동 모니터링</span><span class="sxs-lookup"><span data-stu-id="46edc-102">Monitor Job Activity</span></span>
  <span data-ttu-id="46edc-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 작업 활동 모니터를 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 정의된 모든 작업의 현재 활동을 모니터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="46edc-103">You can monitor the current activity of all defined jobs on an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent Job Activity Monitor.</span></span>  
  
## <a name="sql-server-agent-sessions"></a><span data-ttu-id="46edc-104">SQL Server 에이전트 세션</span><span class="sxs-lookup"><span data-stu-id="46edc-104">SQL Server Agent Sessions</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="46edc-105">에이전트는 서비스가 시작될 때마다 새 세션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="46edc-105">Agent creates a new session each time the service starts.</span></span> <span data-ttu-id="46edc-106">새 세션이 만들어지면 **msdb** 데이터베이스의 **sysjobactivity** 테이블은 정의된 모든 기존 작업으로 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="46edc-106">When a new session is created, the **sysjobactivity** table in the **msdb** database is populated with all the existing defined jobs.</span></span> <span data-ttu-id="46edc-107">이 테이블은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트가 다시 시작되었을 때 작업에 대한 마지막 활동을 보존합니다.</span><span class="sxs-lookup"><span data-stu-id="46edc-107">This table preserves the last activity for jobs when [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent is restarted.</span></span> <span data-ttu-id="46edc-108">각 세션은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 정상 작업 활동을 작업 시작부터 끝까지 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="46edc-108">Each session records [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent normal job activity from the start of the job to its finish.</span></span> <span data-ttu-id="46edc-109">이런 세션에 대한 정보는 **msdb** 데이터베이스의 **syssessions** 테이블에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="46edc-109">Information about these sessions is stored in the **syssessions** table of the **msdb** database.</span></span>  
  
## <a name="job-activity-monitor"></a><span data-ttu-id="46edc-110">작업 활동 모니터</span><span class="sxs-lookup"><span data-stu-id="46edc-110">Job Activity Monitor</span></span>  
 <span data-ttu-id="46edc-111">작업 활동 모니터에서는 **를 사용하여** sysjobactivity [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]테이블을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="46edc-111">The Job Activity Monitor allows you to view the **sysjobactivity** table by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="46edc-112">서버의 모든 작업을 보거나 표시할 작업 수를 제한하는 필터를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="46edc-112">You can view all jobs on the server, or you can define filters to limit the number of jobs displayed.</span></span> <span data-ttu-id="46edc-113">**에이전트 작업 활동** 표에서 열 머리글을 클릭하여 작업 정보를 정렬할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="46edc-113">You can also sort the job information by clicking on a column heading in the **Agent Job Activity** grid.</span></span> <span data-ttu-id="46edc-114">예를 들어 **마지막 실행** 열 머리글을 선택하면 마지막으로 실행된 순서대로 작업을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="46edc-114">For example, when you select the **Last Run** column heading, you can view the jobs in the order that they were last run.</span></span> <span data-ttu-id="46edc-115">열 머리글을 다시 클릭하면 마지막 실행 날짜에 따라 작업이 오름차순이나 내림차순으로 전환됩니다.</span><span class="sxs-lookup"><span data-stu-id="46edc-115">Clicking the column heading again toggles the jobs in ascending and descending order based on their last run date.</span></span>  
  
 <span data-ttu-id="46edc-116">작업 활동 모니터를 사용하여 다음 태스크를 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="46edc-116">Using the Job Activity Monitor you can perform the following tasks:</span></span>  
  
-   <span data-ttu-id="46edc-117">작업을 시작 및 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="46edc-117">Start and stop jobs.</span></span>  
  
-   <span data-ttu-id="46edc-118">작업 속성을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="46edc-118">View job properties.</span></span>  
  
-   <span data-ttu-id="46edc-119">특정 작업의 기록을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="46edc-119">View the history for a specific job.</span></span>  
  
-   <span data-ttu-id="46edc-120">**에이전트 작업 활동** 표의 정보를 수동으로 새로 고치거나 **새로 고침 설정 보기**를 클릭하여 자동 새로 고침 간격을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="46edc-120">Refresh the information in the **Agent Job Activity** grid manually or set an automatic refresh interval by clicking **View refresh settings**.</span></span>  
  
 <span data-ttu-id="46edc-121">작업 활동 모니터를 사용하여 실행이 예약된 작업과 현재 세션 동안 실행된 작업의 최종 결과를 알아보고 현재 실행 중이거나 유휴 상태의 작업을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="46edc-121">Use the Job Activity Monitor when you want to find out what jobs are scheduled to run, the last outcome of jobs that have run during the current session, and to find out which jobs are currently running or idle.</span></span> <span data-ttu-id="46edc-122">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 서비스가 예기치 않게 중지될 경우 작업 활동 모니터의 이전 세션을 살펴보면 실행 중이었던 작업을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="46edc-122">If the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service fails unexpectedly, you can determine which jobs were in the middle of being executed by looking at the previous session in the Job Activity Monitor.</span></span>  
  
 <span data-ttu-id="46edc-123">작업 활동 모니터를 열려면 **개체 탐색기에서** SQL Server 에이전트 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 를 확장하고 **작업 활동 모니터**를 마우스 오른쪽 단추로 클릭한 다음 **작업 활동 보기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="46edc-123">To open the Job Activity Monitor, expand **SQL Server Agent** in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] Object Explorer, right-click **Job Activity Monitor**, and click **View Job Activity**.</span></span>  
  
 <span data-ttu-id="46edc-124">**sp_help_jobactivity**저장 프로시저를 사용하여 현재 세션의 작업 활동을 볼 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="46edc-124">You can also view job activity for the current session by using the stored procedure **sp_help_jobactivity**.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="46edc-125">관련 작업</span><span class="sxs-lookup"><span data-stu-id="46edc-125">Related Tasks</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="46edc-126">**설명**</span><span class="sxs-lookup"><span data-stu-id="46edc-126">**Description**</span></span>|<span data-ttu-id="46edc-127">**항목**</span><span class="sxs-lookup"><span data-stu-id="46edc-127">**Topic**</span></span>|  
|<span data-ttu-id="46edc-128">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 작업의 런타임 상태를 보는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="46edc-128">Describes how to view the runtime state of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs.</span></span>|[<span data-ttu-id="46edc-129">작업 활동 보기</span><span class="sxs-lookup"><span data-stu-id="46edc-129">View Job Activity</span></span>](view-job-activity.md)|  
  
## <a name="see-also"></a><span data-ttu-id="46edc-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="46edc-130">See Also</span></span>  
 <span data-ttu-id="46edc-131">[작업 활동 보기](view-job-activity.md) </span><span class="sxs-lookup"><span data-stu-id="46edc-131">[View Job Activity](view-job-activity.md) </span></span>  
 <span data-ttu-id="46edc-132">[dbo.sysjobactivity &#40;Transact-sql&#41;](/sql/relational-databases/system-tables/dbo-sysjobactivity-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="46edc-132">[dbo.sysjobactivity &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/dbo-sysjobactivity-transact-sql) </span></span>  
 <span data-ttu-id="46edc-133">[Transact-sql&#41;&#40;dbo.sys세션](/sql/relational-databases/system-tables/dbo-syssessions-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="46edc-133">[dbo.syssessions &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/dbo-syssessions-transact-sql) </span></span>  
 [<span data-ttu-id="46edc-134">Transact-sql&#41;sp_help_jobactivity &#40;</span><span class="sxs-lookup"><span data-stu-id="46edc-134">sp_help_jobactivity &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-help-jobactivity-transact-sql)  
  
  
