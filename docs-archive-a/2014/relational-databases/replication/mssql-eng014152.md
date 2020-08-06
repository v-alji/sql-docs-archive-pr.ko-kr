---
title: MSSQL_ENG014152 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG014152 error
ms.assetid: 4215e2b1-cd30-441f-9671-9afc742adf6e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 615b9cf2996653d86c44d6e43a83e01e8287b110
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649496"
---
# <a name="mssql_eng014152"></a><span data-ttu-id="4981a-102">MSSQL_ENG014152</span><span class="sxs-lookup"><span data-stu-id="4981a-102">MSSQL_ENG014152</span></span>
    
## <a name="message-details"></a><span data-ttu-id="4981a-103">메시지 정보</span><span class="sxs-lookup"><span data-stu-id="4981a-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="4981a-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="4981a-104">Product Name</span></span>|<span data-ttu-id="4981a-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="4981a-105">SQL Server</span></span>|  
|<span data-ttu-id="4981a-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="4981a-106">Event ID</span></span>|<span data-ttu-id="4981a-107">14152</span><span class="sxs-lookup"><span data-stu-id="4981a-107">14152</span></span>|  
|<span data-ttu-id="4981a-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="4981a-108">Event Source</span></span>|<span data-ttu-id="4981a-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="4981a-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="4981a-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="4981a-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="4981a-111">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="4981a-111">Symbolic Name</span></span>||  
|<span data-ttu-id="4981a-112">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="4981a-112">Message Text</span></span>|<span data-ttu-id="4981a-113">복제-%s: 에이전트 %s이(가) 다시 시도하도록 예약되었습니다.</span><span class="sxs-lookup"><span data-stu-id="4981a-113">Replication-%s: agent %s scheduled for retry.</span></span> <span data-ttu-id="4981a-114">%s</span><span class="sxs-lookup"><span data-stu-id="4981a-114">%s</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="4981a-115">설명</span><span class="sxs-lookup"><span data-stu-id="4981a-115">Explanation</span></span>  
 <span data-ttu-id="4981a-116">지정한 복제 에이전트가 요청한 작업을 다시 시도하도록 예약되었습니다.</span><span class="sxs-lookup"><span data-stu-id="4981a-116">The specified replication agent has been scheduled to retry the requested operation.</span></span> <span data-ttu-id="4981a-117">작업 단계에 대해 구성된 최대의 다시 시도 횟수에 도달할 때까지 프로세스는 계속해서 작업을 다시 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="4981a-117">The process continues to retry until it reaches the configured maximum number of retry attempts for the job step.</span></span>  
  
 <span data-ttu-id="4981a-118">일반적으로 다시 시도는 다음 원인 중 하나로 인해 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="4981a-118">A retry typically occurs because of one of the following reasons:</span></span>  
  
-   <span data-ttu-id="4981a-119">**QueryTimeout** 값이 초과되었습니다.</span><span class="sxs-lookup"><span data-stu-id="4981a-119">The **QueryTimeout** value is exceeded.</span></span>  
  
-   <span data-ttu-id="4981a-120">**LoginTimeout** 값이 초과되었습니다.</span><span class="sxs-lookup"><span data-stu-id="4981a-120">The **LoginTimeout** value is exceeded.</span></span>  
  
-   <span data-ttu-id="4981a-121">복제 프로세스가 교착 상태에서 처리되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="4981a-121">The replication process was chosen as a deadlock victim.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="4981a-122">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="4981a-122">User Action</span></span>  
 <span data-ttu-id="4981a-123">사용자 동작은 다시 시도 메시지가 빈번하게 표시되는 경우에만 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="4981a-123">If the retry message is infrequent, no user action is required.</span></span>  
  
 <span data-ttu-id="4981a-124">[sp_help_jobstep](/sql/relational-databases/system-stored-procedures/sp-help-jobstep-transact-sql) 을 사용하여, 지정한 복제 에이전트의 **에이전트 실행** 단계에서 다시 시도할 최대 횟수에 대한 현재 설정을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="4981a-124">Use [sp_help_jobstep](/sql/relational-databases/system-stored-procedures/sp-help-jobstep-transact-sql) to view the current setting for the maximum number of times the **Run agent** step for the specified replication agent will retry.</span></span> <span data-ttu-id="4981a-125">**@retry_attempts** [Sp_update_jobstep](/sql/relational-databases/system-stored-procedures/sp-update-jobstep-transact-sql) 저장 프로시저의 매개 변수를 사용 하 여 작업 단계에서 다시 시도 하는 횟수를 조정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4981a-125">You can use the **@retry_attempts** parameter of the [sp_update_jobstep](/sql/relational-databases/system-stored-procedures/sp-update-jobstep-transact-sql) stored procedure to adjust the number of times a job step retries.</span></span>  
  
 <span data-ttu-id="4981a-126">다시 시도 메시지가 자주 표시되는 경우 다시 시도를 발생시키는 메시지를 기준으로 문제를 해결합니다.</span><span class="sxs-lookup"><span data-stu-id="4981a-126">If the retry message recurs frequently, troubleshoot the issue based on the message that is causing the retry.</span></span> <span data-ttu-id="4981a-127">다시 시도가 예약된 이유를 나타내는 메시지에 대한 에이전트 기록을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="4981a-127">Check the agent's history for messages that indicate why the retry had to be scheduled.</span></span> <span data-ttu-id="4981a-128">경우에 따라 복제 에이전트에 대해 더 자세한 로깅을 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4981a-128">In some cases you may have to enable more detailed logging for your replication agent.</span></span> <span data-ttu-id="4981a-129">복제에 대한 로깅을 구성하는 방법은 Microsoft 기술 자료 문서 [312292](https://support.microsoft.com/kb/312292)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="4981a-129">For more information about how to configure logging for replication, see the Microsoft Knowledge Base article [312292](https://support.microsoft.com/kb/312292).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4981a-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4981a-130">See Also</span></span>  
 [<span data-ttu-id="4981a-131">오류 및 이벤트 참조&#40;복제&#41;</span><span class="sxs-lookup"><span data-stu-id="4981a-131">Errors and Events Reference &#40;Replication&#41;</span></span>](errors-and-events-reference-replication.md)  
  
  
