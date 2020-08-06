---
title: MSSQL_ENG020557 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG020557 error
ms.assetid: c43c6952-5b60-4347-b881-11a0004dce24
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 45c24d453eb95abaa967ae65ceb5934b7dee969e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661059"
---
# <a name="mssql_eng020557"></a><span data-ttu-id="a5674-102">MSSQL_ENG020557</span><span class="sxs-lookup"><span data-stu-id="a5674-102">MSSQL_ENG020557</span></span>
    
## <a name="message-details"></a><span data-ttu-id="a5674-103">메시지 정보</span><span class="sxs-lookup"><span data-stu-id="a5674-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a5674-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="a5674-104">Product Name</span></span>|<span data-ttu-id="a5674-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="a5674-105">SQL Server</span></span>|  
|<span data-ttu-id="a5674-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="a5674-106">Event ID</span></span>|<span data-ttu-id="a5674-107">20557</span><span class="sxs-lookup"><span data-stu-id="a5674-107">20557</span></span>|  
|<span data-ttu-id="a5674-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="a5674-108">Event Source</span></span>|<span data-ttu-id="a5674-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="a5674-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="a5674-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="a5674-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="a5674-111">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="a5674-111">Symbolic Name</span></span>||  
|<span data-ttu-id="a5674-112">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="a5674-112">Message Text</span></span>|<span data-ttu-id="a5674-113">에이전트를 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="a5674-113">Agent shutdown.</span></span> <span data-ttu-id="a5674-114">자세한 내용은 작업 '%s'에 대한 SQL Server 에이전트 작업 기록을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="a5674-114">For more information, see the SQL Server Agent job history for job '%s'.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="a5674-115">설명</span><span class="sxs-lookup"><span data-stu-id="a5674-115">Explanation</span></span>  
 <span data-ttu-id="a5674-116">복제 에이전트가 해당 기록 테이블에 원인을 기록하지 않고 종료되었거나 에이전트가 프로세스 중에 종료되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a5674-116">A replication agent has shut down without writing a reason to the appropriate history table, or the agent was shut down while in the middle of a process.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="a5674-117">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="a5674-117">User Action</span></span>  
  
-   <span data-ttu-id="a5674-118">에이전트를 다시 시작하여 이제 오류 없이 실행되는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="a5674-118">Restart the agent to see whether it will now run without failures.</span></span> <span data-ttu-id="a5674-119">자세한 내용은 [복제 에이전트 시작 및 중지&#40;SQL Server Management Studio&#41;](agents/start-and-stop-a-replication-agent-sql-server-management-studio.md) 및 [복제 에이전트 실행 파일 개념](concepts/replication-agent-executables-concepts.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a5674-119">For more information, see [Start and Stop a Replication Agent &#40;SQL Server Management Studio&#41;](agents/start-and-stop-a-replication-agent-sql-server-management-studio.md) and [Replication Agent Executables Concepts](concepts/replication-agent-executables-concepts.md).</span></span>  
  
-   <span data-ttu-id="a5674-120">에이전트 기록과 작업 기록에서 같은 시간대에 발생한 다른 오류를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="a5674-120">Check the agent history and job history for other errors that occurred around the same time.</span></span> <span data-ttu-id="a5674-121">복제 모니터에서 에이전트 상태 및 오류 정보를 보는 방법에 대한 자세한 내용은 [복제 모니터를 사용하여 정보 보기 및 작업 수행](monitor/view-information-and-perform-tasks-replication-monitor.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a5674-121">For information about how to view agent status and error details in Replication Monitor, see [View Information and Perform Tasks using Replication Monitor](monitor/view-information-and-perform-tasks-replication-monitor.md).</span></span>
-   <span data-ttu-id="a5674-122">에이전트에서 액세스하는 컴퓨터 사이에 기본 연결이 제대로 작동하는지 확인한 다음 **sqlcmd** 와 같은 유틸리티를 사용하여 각 컴퓨터에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="a5674-122">Verify that basic connectivity is working between the computers that are accessed by the agent, and then connect to each computer by using a utility, such as the **sqlcmd** utility.</span></span> <span data-ttu-id="a5674-123">각 컴퓨터에 연결할 때는 에이전트 연결 시 사용하는 계정과 같은 계정을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a5674-123">When you connect, use the same account under which the agent makes connections.</span></span> <span data-ttu-id="a5674-124">각 에이전트 계정에 필요한 사용 권한에 대한 자세한 내용은 [Replication Agent Security Model](security/replication-agent-security-model.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="a5674-124">For more information about the permissions that are required by each agent account, see [Replication Agent Security Model](security/replication-agent-security-model.md).</span></span>  
  
-   <span data-ttu-id="a5674-125">스냅샷을 만들거나 적용하는 동안 오류가 발생하면 스냅샷 디렉터리의 파일에서 오류를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="a5674-125">If the error occurs while you are creating or applying a snapshot, check the files in the snapshot directory for errors.</span></span>  
  
-   <span data-ttu-id="a5674-126">오류가 계속 발생하면 에이전트의 로깅을 늘리고 해당 로그의 출력 파일을 지정하십시오.</span><span class="sxs-lookup"><span data-stu-id="a5674-126">If the error continues to occur, increase the logging of the agent and specify an output file for the log.</span></span> <span data-ttu-id="a5674-127">오류의 컨텍스트에 따라 이러한 작업을 수행하면 오류 및 추가 오류 메시지가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5674-127">Depending on the context of the error, this could provide the steps leading up to the error and additional error messages.</span></span> <span data-ttu-id="a5674-128">복제에 대한 로깅을 구성하는 방법은 Microsoft 기술 자료 문서 [312292](https://support.microsoft.com/kb/312292)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="a5674-128">For more information about how to configure logging for replication, see the Microsoft Knowledge Base article [312292](https://support.microsoft.com/kb/312292).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5674-129">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a5674-129">See Also</span></span>  
 [<span data-ttu-id="a5674-130">오류 및 이벤트 참조&#40;복제&#41;</span><span class="sxs-lookup"><span data-stu-id="a5674-130">Errors and Events Reference &#40;Replication&#41;</span></span>](errors-and-events-reference-replication.md)  
  
  
