---
title: 작업 보기 또는 수정 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], modifying
- jobs [SQL Server Agent], viewing
- modifying jobs
- viewing jobs
- SQL Server Agent jobs, viewing
- SQL Server Agent jobs, modifying
- displaying jobs
ms.assetid: 57f649b8-190c-4304-abd7-7ca5297deab7
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5d0d731d25c20597be3ac84adfacd8973e4a51cd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731300"
---
# <a name="view-or-modify-jobs"></a><span data-ttu-id="0c3b6-102">작업 보기 또는 수정</span><span class="sxs-lookup"><span data-stu-id="0c3b6-102">View or Modify Jobs</span></span>
  <span data-ttu-id="0c3b6-103">생성한 모든 작업을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0c3b6-103">You can view any job you have created.</span></span> <span data-ttu-id="0c3b6-104">작업을 실행한 후 해당 기록도 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0c3b6-104">After you have run a job, you can also view its history.</span></span> <span data-ttu-id="0c3b6-105">작업 기록을 보면 작업 실행 시간, 작업 전체 상태, 각 작업 단계의 상태 등을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0c3b6-105">Viewing a job's history allows you to see when the job ran, the status of the job as a whole, and the status of each job step in the job.</span></span> <span data-ttu-id="0c3b6-106">과거 작업 실패 여부, 마지막으로 작업이 완료된 시간 및 각 작업 실행 시 작성된 출력 등을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0c3b6-106">You can see whether the job ever failed in the past, when the job last completed successfully, and what output the job created each time the job ran.</span></span> <span data-ttu-id="0c3b6-107">**sysadmin** 고정 서버 역할의 멤버는 소유자에 관계없이 모든 작업을 보거나 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0c3b6-107">Members of the **sysadmin** fixed server role can view or modify any job, regardless of the owner.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0c3b6-108">최소 한 번 이상 작업을 실행해야 작업 기록이 남습니다.</span><span class="sxs-lookup"><span data-stu-id="0c3b6-108">A job must have been executed at least one time for there to be a job history.</span></span> <span data-ttu-id="0c3b6-109">작업 기록 로그의 전체 크기와 작업당 크기를 제한할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0c3b6-109">You can limit the total size of the job history log and the size per job.</span></span>  
  
 <span data-ttu-id="0c3b6-110">끝으로 새로운 요구 사항을 충족하도록 작업을 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0c3b6-110">Finally, you can modify a job to meet new requirements.</span></span> <span data-ttu-id="0c3b6-111">다음을 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0c3b6-111">You can modify:</span></span>  
  
-   <span data-ttu-id="0c3b6-112">응답 옵션</span><span class="sxs-lookup"><span data-stu-id="0c3b6-112">Response options</span></span>  
  
-   <span data-ttu-id="0c3b6-113">일정</span><span class="sxs-lookup"><span data-stu-id="0c3b6-113">Schedules</span></span>  
  
-   <span data-ttu-id="0c3b6-114">작업 단계</span><span class="sxs-lookup"><span data-stu-id="0c3b6-114">Job steps</span></span>  
  
-   <span data-ttu-id="0c3b6-115">소유권</span><span class="sxs-lookup"><span data-stu-id="0c3b6-115">Ownership</span></span>  
  
-   <span data-ttu-id="0c3b6-116">작업 범주</span><span class="sxs-lookup"><span data-stu-id="0c3b6-116">Job category</span></span>  
  
-   <span data-ttu-id="0c3b6-117">대상 서버(다중 서버 작업만)</span><span class="sxs-lookup"><span data-stu-id="0c3b6-117">Target servers (multiserver jobs only)</span></span>  
  
 <span data-ttu-id="0c3b6-118">다중 서버 작업에 변경한 내용을 적용하려면 변경 내용을 다운로드 목록에 올려 대상 서버가 업데이트된 작업을 다운로드할 수 있도록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c3b6-118">To make sure that changes to multiserver jobs take effect, you must post the changes to the download list so that target servers can download the updated job.</span></span> <span data-ttu-id="0c3b6-119">대상 서버에 최신 작업 정의를 적용하려면 다중 서버 작업을 다음과 같이 업데이트한 후에 INSERT 명령을 게시하십시오.</span><span class="sxs-lookup"><span data-stu-id="0c3b6-119">To ensure that target servers have the most current job definitions, post an INSERT instruction after you update the multiserver job as follows:</span></span>  
  
```  
EXECUTE sp_post_msx_operation 'INSERT', 'JOB', '<job id>'  
```  
  
 <span data-ttu-id="0c3b6-120">자세한 내용은 [sp_purge_jobhistory &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-purge-jobhistory-transact-sql)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0c3b6-120">For more information, see [sp_purge_jobhistory &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-purge-jobhistory-transact-sql).</span></span>  
  
 <span data-ttu-id="0c3b6-121">**sysadmin** 고정 서버 역할의 멤버는 모든 작업의 정의나 기록을 볼 수 있고 모든 작업을 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0c3b6-121">Members of the **sysadmin** fixed server role can view the definition or history of any job, and can modify any job.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="0c3b6-122">관련 작업</span><span class="sxs-lookup"><span data-stu-id="0c3b6-122">Related Tasks</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0c3b6-123">**설명**</span><span class="sxs-lookup"><span data-stu-id="0c3b6-123">**Description**</span></span>|<span data-ttu-id="0c3b6-124">**항목**</span><span class="sxs-lookup"><span data-stu-id="0c3b6-124">**Topic**</span></span>|  
|<span data-ttu-id="0c3b6-125">[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 에이전트 작업을 보는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="0c3b6-125">Describes how to view [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent jobs.</span></span>|[<span data-ttu-id="0c3b6-126">View a Job</span><span class="sxs-lookup"><span data-stu-id="0c3b6-126">View a Job</span></span>](view-a-job.md)|  
|<span data-ttu-id="0c3b6-127">[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 에이전트 작업 기록 로그를 보는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="0c3b6-127">Describes how to view the [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent job history log.</span></span>|[<span data-ttu-id="0c3b6-128">View the Job History</span><span class="sxs-lookup"><span data-stu-id="0c3b6-128">View the Job History</span></span>](view-the-job-history.md)|  
|<span data-ttu-id="0c3b6-129">[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 에이전트 작업 기록 로그의 내용을 삭제하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="0c3b6-129">Describes how to delete the contents of the [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent job history log.</span></span>|[<span data-ttu-id="0c3b6-130">Clear the Job History Log</span><span class="sxs-lookup"><span data-stu-id="0c3b6-130">Clear the Job History Log</span></span>](clear-the-job-history-log.md)|  
|<span data-ttu-id="0c3b6-131">[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 에이전트 작업 기록 로그의 크기 제한을 설정하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="0c3b6-131">Describes how to set size limits for [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent job history logs.</span></span>|[<span data-ttu-id="0c3b6-132">Resize the Job History Log</span><span class="sxs-lookup"><span data-stu-id="0c3b6-132">Resize the Job History Log</span></span>](resize-the-job-history-log.md)|  
|<span data-ttu-id="0c3b6-133">[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 에이전트 작업의 속성을 변경하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="0c3b6-133">Describes how to change the properties of [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent jobs.</span></span>|[<span data-ttu-id="0c3b6-134">Modify a Job</span><span class="sxs-lookup"><span data-stu-id="0c3b6-134">Modify a Job</span></span>](modify-a-job.md)|  
  
## <a name="see-also"></a><span data-ttu-id="0c3b6-135">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0c3b6-135">See Also</span></span>  
 [<span data-ttu-id="0c3b6-136">dbo.sysjobhistory &#40;Transact-sql&#41;</span><span class="sxs-lookup"><span data-stu-id="0c3b6-136">dbo.sysjobhistory &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-tables/dbo-sysjobhistory-transact-sql)  
  
  
