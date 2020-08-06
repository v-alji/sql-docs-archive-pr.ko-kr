---
title: MSSQL_ENG018752 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG018752 error
ms.assetid: 405b2655-acb4-4e15-bcc6-b8f86bb22b37
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: fe62d540ea8e988cd4249112f196f75493a8f623
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740827"
---
# <a name="mssql_eng018752"></a><span data-ttu-id="6ed94-102">MSSQL_ENG018752</span><span class="sxs-lookup"><span data-stu-id="6ed94-102">MSSQL_ENG018752</span></span>
    
## <a name="message-details"></a><span data-ttu-id="6ed94-103">메시지 정보</span><span class="sxs-lookup"><span data-stu-id="6ed94-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6ed94-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="6ed94-104">Product Name</span></span>|<span data-ttu-id="6ed94-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="6ed94-105">SQL Server</span></span>|  
|<span data-ttu-id="6ed94-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="6ed94-106">Event ID</span></span>|<span data-ttu-id="6ed94-107">18752</span><span class="sxs-lookup"><span data-stu-id="6ed94-107">18752</span></span>|  
|<span data-ttu-id="6ed94-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="6ed94-108">Event Source</span></span>|<span data-ttu-id="6ed94-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="6ed94-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="6ed94-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="6ed94-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="6ed94-111">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="6ed94-111">Symbolic Name</span></span>||  
|<span data-ttu-id="6ed94-112">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="6ed94-112">Message Text</span></span>|<span data-ttu-id="6ed94-113">한 번에 하나의 로그 판독기 에이전트 또는 로그 관련 프로시저(sp_repldone, sp_replcmds 및 sp_replshowcmds)만 데이터베이스에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6ed94-113">Only one Log Reader Agent or log-related procedure (sp_repldone, sp_replcmds, and sp_replshowcmds) can connect to a database at a time.</span></span> <span data-ttu-id="6ed94-114">로그 관련 프로시저를 실행한 경우 로그 판독기 에이전트를 시작하거나 다른 로그 관련 프로시저를 실행하기 전에 프로시저가 실행된 연결을 삭제하거나 해당 연결에 대해 sp_replflush를 실행하십시오.</span><span class="sxs-lookup"><span data-stu-id="6ed94-114">If you executed a log-related procedure, drop the connection over which the procedure was executed or execute sp_replflush over that connection before starting the Log Reader Agent or executing another log-related procedure.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="6ed94-115">설명</span><span class="sxs-lookup"><span data-stu-id="6ed94-115">Explanation</span></span>  
 <span data-ttu-id="6ed94-116">현재 둘 이상의 연결에서 **sp_repldone**, **sp_replcmds**또는 **sp_replshowcmds**중 하나를 실행하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ed94-116">More than one current connection is trying to execute any of the following: **sp_repldone**, **sp_replcmds**, or **sp_replshowcmds**.</span></span> <span data-ttu-id="6ed94-117">저장 프로시저 [sp_repldone&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-repldone-transact-sql) 및 [sp_replcmds&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-replcmds-transact-sql)는 게시된 데이터베이스에 복제된 트랜잭션에 대한 정보를 찾아 업데이트하기 위해 로그 판독기 에이전트에서 사용하는 저장 프로시저입니다.</span><span class="sxs-lookup"><span data-stu-id="6ed94-117">The stored procedures [sp_repldone &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-repldone-transact-sql) and [sp_replcmds &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-replcmds-transact-sql) are stored procedures used by the Log Reader Agent to locate and update information about replicated transactions in a published database.</span></span> <span data-ttu-id="6ed94-118">저장 프로시저 [sp_replshowcmds&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-replshowcmds-transact-sql)는 트랜잭션 복제와 관련된 특정 문제를 해결하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="6ed94-118">The stored procedure [sp_replshowcmds &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-replshowcmds-transact-sql) is used to troubleshoot certain types of issues with transactional replication.</span></span>  
  
 <span data-ttu-id="6ed94-119">이 오류는 다음과 같은 경우에 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="6ed94-119">This error is raised in the following circumstances:</span></span>  
  
-   <span data-ttu-id="6ed94-120">게시된 데이터베이스에 대해 로그 판독기 에이전트가 실행 중인데 두 번째 로그 판독기 에이전트가 같은 데이터베이스를 실행하려고 할 경우 두 번째 에이전트에 대해 오류가 발생하고 에이전트 기록에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="6ed94-120">If the Log Reader Agent for a published database is running and a second Log Reader Agent attempts to run against the same database, the error is raised for the second agent and appears in the agent history.</span></span>  
  
     <span data-ttu-id="6ed94-121">에이전트가 여러 개인 것으로 표시되는 경우 해당 에이전트 중 하나는 분리된 프로세스의 결과일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6ed94-121">In a situation where it appears there are multiple agents, it is possible that one of them is the result of an orphaned process.</span></span>  
  
-   <span data-ttu-id="6ed94-122">게시된 데이터베이스에 대해 로그 판독기 에이전트가 시작되었는데 사용자가 같은 데이터베이스에 대해 **sp_repldone**, **sp_replcmds**또는 **sp_replshowcmds** 를 실행할 경우 저장 프로시저가 실행된 애플리케이션(예: **sqlcmd**)에서 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="6ed94-122">If the Log Reader Agent for a published database is started and a user executes **sp_repldone**, **sp_replcmds**, or **sp_replshowcmds** against the same database, the error is raised in the application where the stored procedure was executed (such as **sqlcmd**).</span></span>  
  
-   <span data-ttu-id="6ed94-123">게시된 데이터베이스에 대해 실행 중인 로그 판독기 에이전트가 없는 상태에서 사용자가 **sp_repldone**, **sp_replcmds**또는 **sp_replshowcmds** 를 실행한 다음 프로시저가 실행된 연결을 닫지 않을 경우 로그 판독기 에이전트가 데이터베이스에 연결을 시도하면 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="6ed94-123">If no Log Reader Agent is running for a published database and a user executes **sp_repldone**, **sp_replcmds**, or **sp_replshowcmds** and then does not close the connection over which the procedure was executed, the error is raised when the Log Reader Agent attempts to connect to the database.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="6ed94-124">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="6ed94-124">User Action</span></span>  
 <span data-ttu-id="6ed94-125">다음 단계를 수행하면 문제를 해결하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6ed94-125">The following steps can help you to troubleshoot the problem.</span></span> <span data-ttu-id="6ed94-126">다음 단계를 수행하는 중 로그 판독기 에이전트가 오류 없이 시작되면 나머지 단계를 완료할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6ed94-126">If any step allows the Log Reader Agent to start without errors, there is no need to complete the remaining steps.</span></span>  
  
-   <span data-ttu-id="6ed94-127">로그 판독기 에이전트의 기록에서 이 오류의 원인이 될 수 있는 다른 오류가 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="6ed94-127">Check the history of the Log Reader agent for any other errors that could be contributing to this error.</span></span> <span data-ttu-id="6ed94-128">복제 모니터에서 에이전트 상태 및 오류 정보를 보는 방법에 대한 자세한 내용은 [복제 모니터를 사용하여 정보 보기 및 작업 수행](monitor/view-information-and-perform-tasks-replication-monitor.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6ed94-128">For information about viewing agent status and error details in Replication Monitor, see [View Information and Perform Tasks using Replication Monitor](monitor/view-information-and-perform-tasks-replication-monitor.md).</span></span>  
  
-   <span data-ttu-id="6ed94-129">[sp_who&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-who-transact-sql)의 출력에서 게시된 데이터베이스에 연결된 특정 프로세스 ID 번호(SPID)를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="6ed94-129">Check the output of [sp_who &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-who-transact-sql) for specific process identification numbers (SPIDs) that are connected to the published database.</span></span> <span data-ttu-id="6ed94-130">**sp_repldone**, **sp_replcmds**또는 **sp_replshowcmds**를 실행했을 가능성이 있는 연결을 모두 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="6ed94-130">Close any connections that might have run **sp_repldone**, **sp_replcmds**, or **sp_replshowcmds**.</span></span>  
  
-   <span data-ttu-id="6ed94-131">로그 판독기 에이전트를 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="6ed94-131">Restart the Log Reader Agent.</span></span> <span data-ttu-id="6ed94-132">자세한 내용은 [복제 에이전트 시작 및 중지&#40;SQL Server Management Studio&#41;](agents/start-and-stop-a-replication-agent-sql-server-management-studio.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6ed94-132">For more information, see [Start and Stop a Replication Agent &#40;SQL Server Management Studio&#41;](agents/start-and-stop-a-replication-agent-sql-server-management-studio.md).</span></span>  
  
-   <span data-ttu-id="6ed94-133">배포자에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 서비스를 다시 시작(클러스터에서 오프라인 또는 온라인 상태로 만듦)합니다.</span><span class="sxs-lookup"><span data-stu-id="6ed94-133">Restart the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service (bring it offline or online in a cluster) on the Distributor.</span></span> <span data-ttu-id="6ed94-134">예약된 작업이 다른 **인스턴스에서**sp_repldone **,** sp_replcmds **또는** sp_replshowcmds [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 를 실행했을 가능성이 있는 경우 해당 인스턴스에 대한 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트도 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="6ed94-134">If there is possibility that a scheduled job could have executed **sp_repldone**, **sp_replcmds**, or **sp_replshowcmds** from any other [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance, restart the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent for those instances as well.</span></span> <span data-ttu-id="6ed94-135">자세한 내용은 [SQL Server 에이전트 서비스 시작, 중지 또는 일시 중지](../../ssms/agent/start-stop-or-pause-the-sql-server-agent-service.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6ed94-135">For more information, see [Start, Stop, or Pause the SQL Server Agent Service](../../ssms/agent/start-stop-or-pause-the-sql-server-agent-service.md).</span></span>  
  
-   <span data-ttu-id="6ed94-136">게시 데이터베이스의 게시자에서 [sp_replflush&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-replflush-transact-sql)를 실행한 다음 로그 판독기 에이전트를 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="6ed94-136">Execute [sp_replflush &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-replflush-transact-sql) at the Publisher on the publication database, and then restart the Log Reader Agent.</span></span>  
  
-   <span data-ttu-id="6ed94-137">오류가 계속 발생하면 에이전트의 로깅을 늘리고 해당 로그의 출력 파일을 지정하십시오.</span><span class="sxs-lookup"><span data-stu-id="6ed94-137">If the error continues to occur, increase the logging of the agent and specify an output file for the log.</span></span> <span data-ttu-id="6ed94-138">오류의 컨텍스트에 따라 이러한 작업을 수행하면 오류 및/또는 추가 오류 메시지가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6ed94-138">Depending on the context of the error, this could provide the steps leading up to the error and/or additional error messages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ed94-139">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6ed94-139">See Also</span></span>  
 <span data-ttu-id="6ed94-140">[오류 및 이벤트 참조&#40;복제&#41;](errors-and-events-reference-replication.md) </span><span class="sxs-lookup"><span data-stu-id="6ed94-140">[Errors and Events Reference &#40;Replication&#41;](errors-and-events-reference-replication.md) </span></span>  
 [<span data-ttu-id="6ed94-141">복제 로그 판독기 에이전트</span><span class="sxs-lookup"><span data-stu-id="6ed94-141">Replication Log Reader Agent</span></span>](agents/replication-log-reader-agent.md)  
  
  
