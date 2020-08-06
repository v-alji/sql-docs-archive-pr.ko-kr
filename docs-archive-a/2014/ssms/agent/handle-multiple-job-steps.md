---
title: 다중 작업 단계 처리 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- job steps [SQL Server Agent]
- ordering job steps [SQL Server]
- multiple job steps
- SQL Server Agent jobs, job steps
- control of flow for jobs [SQL Server]
ms.assetid: 7aba19ff-72b3-45f6-8e54-23f4988d63a8
author: stevestein
ms.author: sstein
ms.openlocfilehash: fef0fb69b5bfd028977276d8efabc333a21e0feb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639213"
---
# <a name="handle-multiple-job-steps"></a><span data-ttu-id="9e581-102">다중 작업 단계 처리</span><span class="sxs-lookup"><span data-stu-id="9e581-102">Handle Multiple Job Steps</span></span>
  <span data-ttu-id="9e581-103">작업에 둘 이상의 작업 단계가 있는 경우에는 작업 단계가 실행되는 순서를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e581-103">If your job has more than one job step, you must specify the order in which the job steps run.</span></span> <span data-ttu-id="9e581-104">이를 *흐름 제어\*\*라고 합니다.*</span><span class="sxs-lookup"><span data-stu-id="9e581-104">This is called *control of flow\*\*.*</span></span> <span data-ttu-id="9e581-105">언제든지 새 작업 단계를 추가하고 작업 단계의 흐름을 다시 정렬할 수 있습니다. 변경 내용은 다음에 작업이 실행될 때 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e581-105">You can add new job steps and rearrange the flow of job steps at any time; the changes take effect the next time the job is run.</span></span> <span data-ttu-id="9e581-106">다음 그림에서는 데이터베이스 백업 작업에 대한 흐름 제어를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="9e581-106">This illustration shows the control of flow for a database backup job.</span></span>  
  
 <span data-ttu-id="9e581-107">![SQL Server 에이전트 작업 단계 흐름 제어](../../database-engine/media/dbflow01.gif "SQL Server 에이전트 작업 단계 흐름 제어")</span><span class="sxs-lookup"><span data-stu-id="9e581-107">![SQL Server Agent job steps control of flow](../../database-engine/media/dbflow01.gif "SQL Server Agent job steps control of flow")</span></span>  
  
 <span data-ttu-id="9e581-108">첫 번째 단계는 데이터베이스 백업입니다.</span><span class="sxs-lookup"><span data-stu-id="9e581-108">The first step is Backup Database.</span></span> <span data-ttu-id="9e581-109">이 단계가 실패하면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트에서 알림을 받도록 정의된 운영자에게 실패를 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="9e581-109">If this step fails, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent reports failure to the operator who is defined to receive notification.</span></span> <span data-ttu-id="9e581-110">데이터베이스 백업 단계가 성공적으로 수행되면 다음 단계인 고객 데이터 "스크러빙"으로 진행합니다.</span><span class="sxs-lookup"><span data-stu-id="9e581-110">If the Backup Database step succeeds, the job proceeds to the next step, "Scrub" Customer Data.</span></span> <span data-ttu-id="9e581-111">이 단계가 실패하면 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 에이전트에서 데이터베이스 복원으로 건너뜁니다.</span><span class="sxs-lookup"><span data-stu-id="9e581-111">If this step fails, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent skips forward to Restore Database.</span></span> <span data-ttu-id="9e581-112">고객 데이터 "스크러빙"이 성공적으로 수행되면 다음 단계인 통계 업데이트로 진행하는 등 마지막 단계인 성공 보고 또는 실패 보고까지 계속 진행합니다.</span><span class="sxs-lookup"><span data-stu-id="9e581-112">If "Scrub" Customer Data succeeds, the job proceeds to the next step, Update Statistics, and so on, until the final step either results in Report Success or Report Failure.</span></span>  
  
 <span data-ttu-id="9e581-113">각 작업 단계의 성공과 실패에 대한 흐름 제어 동작을 정의하려면</span><span class="sxs-lookup"><span data-stu-id="9e581-113">You define a control-of-flow action for the success and failure of each job step.</span></span> <span data-ttu-id="9e581-114">작업 단계가 성공할 때 취해야 할 작업과 실패할 때 취해야 할 동작을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e581-114">You must specify an action to be taken when a job step succeeds and an action to be taken when a job step fails.</span></span> <span data-ttu-id="9e581-115">또한 실패한 작업 단계의 경우에는 재시도 횟수와 재시도 간의 간격을 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e581-115">You can also define the number of retry attempts for failed job steps and the interval between the retry attempts.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9e581-116">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 GUI(그래픽 사용자 인터페이스)를 사용하여 다중 단계 작업에서 단계를 하나 이상 삭제하면 GUI는 모든 작업 단계를 제거한 후 나머지 단계를 올바른 성공 시 또는 실패 시 참조와 함께 다시 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="9e581-116">When you use the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent graphical user interface (GUI) and delete one or more steps from a multistep job, the GUI removes all job steps and then adds the remaining steps back with the correct on-success or on-failure references.</span></span> <span data-ttu-id="9e581-117">예를 들어 5개의 단계로 이루어진 작업이 있으며 첫 번째 단계가 성공적으로 완료되면 4단계로 이동하도록 구성되었다고 가정해 보십시오.</span><span class="sxs-lookup"><span data-stu-id="9e581-117">For example, suppose you have a job with five steps, and the first step is configured to jump to step 4 if it completes successfully.</span></span> <span data-ttu-id="9e581-118">3단계를 삭제하면 GUI는 이 작업의 모든 단계를 제거하고 나머지 4개의 단계(1, 2, 4, 5)를 수정된 참조와 함께 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="9e581-118">If you delete step 3, the GUI removes all steps for this job and adds the remaining four steps (1, 2, 4, and 5) with corrected references.</span></span> <span data-ttu-id="9e581-119">이 경우 1단계가 성공적으로 완료되면 3단계로 이동하도록 1단계의 참조가 다시 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e581-119">In this case, the reference in step 1 would be reconfigured to jump to step 3 if step 1 completes successfully.</span></span>  
  
 <span data-ttu-id="9e581-120">작업 단계는 독립적이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e581-120">Job steps must be self-contained.</span></span> <span data-ttu-id="9e581-121">즉, 한 작업에서 작업 단계 간에 부울 값, 데이터 또는 숫자 값을 전달할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9e581-121">That is, a job cannot pass Boolean values, data, or numeric values between job steps.</span></span> <span data-ttu-id="9e581-122">그러나 영구 테이블이나 전역 임시 테이블을 사용하면 한 [!INCLUDE[tsql](../../includes/tsql-md.md)] 작업 단계에서 다른 작업 단계로 값을 전달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e581-122">You can, however, pass values from one [!INCLUDE[tsql](../../includes/tsql-md.md)] job step to another by using permanent tables or global temporary tables.</span></span> <span data-ttu-id="9e581-123">파일을 사용하여 실행 프로그램을 실행하는 작업 단계의 값을 한 작업 단계에서 다른 작업 단계로 전달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e581-123">You can pass values from job steps that run executable programs from one job step to another job step by using files.</span></span> <span data-ttu-id="9e581-124">예를 들어 하나의 작업 단계에서 실행되는 실행 파일이 파일에 기록하면 이후 작업 단계에서 실행되는 실행 파일은 해당 파일을 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="9e581-124">For example, the executable run by one job step writes a file, and the executable run by a subsequent job step reads the file.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9e581-125">반복 작업 단계(작업 단계 1 다음에 작업 단계 2가 실행된 다음 작업 단계 2가 작업 단계 1로 되돌아감)를 만들 경우 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]를 사용하여 작업을 만들면 경고 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e581-125">If you create looping job steps (job step 1 is followed by job step 2, then job step 2 returns to job step 1), a warning message appears when the job is created using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="9e581-126">에이전트에서 작업과 작업 단계 정보를 작업 기록에 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="9e581-126">Agent records job and job step information in the job history.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e581-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9e581-127">See Also</span></span>  
 <span data-ttu-id="9e581-128">[sp_add_job&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-job-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="9e581-128">[sp_add_job &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-job-transact-sql) </span></span>  
 <span data-ttu-id="9e581-129">[dbo.sysjobhistory &#40;Transact-sql&#41;](/sql/relational-databases/system-tables/dbo-sysjobhistory-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="9e581-129">[dbo.sysjobhistory &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/dbo-sysjobhistory-transact-sql) </span></span>  
 <span data-ttu-id="9e581-130">[Transact-sql&#41;&#40;작업dbo.sys](/sql/relational-databases/system-tables/dbo-sysjobs-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="9e581-130">[dbo.sysjobs &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/dbo-sysjobs-transact-sql) </span></span>  
 <span data-ttu-id="9e581-131">[dbo.sysjobsteps &#40;Transact-sql&#41;](/sql/relational-databases/system-tables/dbo-sysjobsteps-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="9e581-131">[dbo.sysjobsteps &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/dbo-sysjobsteps-transact-sql) </span></span>  
 <span data-ttu-id="9e581-132">[작업 구현](implement-jobs.md) </span><span class="sxs-lookup"><span data-stu-id="9e581-132">[Implement Jobs](implement-jobs.md) </span></span>  
 [<span data-ttu-id="9e581-133">작업 단계 관리</span><span class="sxs-lookup"><span data-stu-id="9e581-133">Manage Job Steps</span></span>](manage-job-steps.md)  
  
  
