---
title: '작업 단계 속성: 새 작업 단계 (고급 페이지) | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.ag.job.stepadvanced.f1
ms.assetid: bdecfd4f-bcd8-4ba2-8ada-fbb636314f40
author: stevestein
ms.author: sstein
ms.openlocfilehash: 42820ffbdbb89261e839b5d1011f3a91b5841c86
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737426"
---
# <a name="job-step-properties-new-job-step-advanced-page"></a><span data-ttu-id="34182-102">작업 단계 속성: 새 작업 단계(고급 페이지)</span><span class="sxs-lookup"><span data-stu-id="34182-102">Job Step Properties: New Job Step (Advanced Page)</span></span>
  <span data-ttu-id="34182-103">이 페이지를 사용 하 여 에이전트 작업 단계의 속성을 확인 하 고 변경할 수 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34182-103">Use this page to view and change the properties of a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job step.</span></span>  
  
## <a name="options"></a><span data-ttu-id="34182-104">옵션</span><span class="sxs-lookup"><span data-stu-id="34182-104">Options</span></span>  
 <span data-ttu-id="34182-105">**성공한 경우 동작**</span><span class="sxs-lookup"><span data-stu-id="34182-105">**On success action**</span></span>  
 <span data-ttu-id="34182-106">작업 단계 성공 시 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트에서 수행할 동작을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="34182-106">Sets the action for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to perform if the job step succeeds.</span></span>  
  
 <span data-ttu-id="34182-107">**다시 시도 횟수**</span><span class="sxs-lookup"><span data-stu-id="34182-107">**Retry attempts**</span></span>  
 <span data-ttu-id="34182-108">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트에서 실패한 작업 단계를 다시 시도하는 횟수를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="34182-108">Sets the number of times that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent attempts to retry a failed job step.</span></span>  
  
 <span data-ttu-id="34182-109">**다시 시도 간격(분)**</span><span class="sxs-lookup"><span data-stu-id="34182-109">**Retry interval (minutes)**</span></span>  
 <span data-ttu-id="34182-110">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트에서 작업 단계를 다시 시도하기 전에 대기하는 시간을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="34182-110">Sets the amount of time for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to wait between retry attempts.</span></span>  
  
 <span data-ttu-id="34182-111">**실패한 경우 동작**</span><span class="sxs-lookup"><span data-stu-id="34182-111">**On failure action**</span></span>  
 <span data-ttu-id="34182-112">작업 단계 실패 시 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트에서 수행할 동작을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="34182-112">Sets the action for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to perform if the job step fails.</span></span>  
  
## <a name="options-for-transact-sql-job-steps"></a><span data-ttu-id="34182-113">Transact-SQL 작업 단계 옵션</span><span class="sxs-lookup"><span data-stu-id="34182-113">Options for Transact-SQL Job Steps</span></span>  
 <span data-ttu-id="34182-114">**출력 파일**</span><span class="sxs-lookup"><span data-stu-id="34182-114">**Output file**</span></span>  
 <span data-ttu-id="34182-115">작업 단계의 출력에 사용할 파일을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="34182-115">Sets the file to use for output from the job step.</span></span> <span data-ttu-id="34182-116">이 옵션은 **sysadmin** 고정 서버 역할의 멤버만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34182-116">This option is available only to members of the **sysadmin** fixed server role.</span></span>  
  
 <span data-ttu-id="34182-117">**...**</span><span class="sxs-lookup"><span data-stu-id="34182-117">**...**</span></span>  
 <span data-ttu-id="34182-118">작업 단계의 출력에 사용할 파일을 찾아 봅니다.</span><span class="sxs-lookup"><span data-stu-id="34182-118">Browse to the file to use for output from the job step.</span></span>  
  
 <span data-ttu-id="34182-119">**보기**</span><span class="sxs-lookup"><span data-stu-id="34182-119">**View**</span></span>  
 <span data-ttu-id="34182-120">에서는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 이 단추를 사용 하 여 출력 파일을 볼 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="34182-120">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], this button is disabled for viewing output files.</span></span> <span data-ttu-id="34182-121">대신 메모장을 사용하여 작업 단계 출력 파일을 검토합니다.</span><span class="sxs-lookup"><span data-stu-id="34182-121">Instead, use Notepad to view job step output files.</span></span>  
  
 <span data-ttu-id="34182-122">**기존 파일에 출력 추가**</span><span class="sxs-lookup"><span data-stu-id="34182-122">**Append output to existing file**</span></span>  
 <span data-ttu-id="34182-123">출력을 파일의 기존 내용에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="34182-123">Append output to the existing contents of the file.</span></span> <span data-ttu-id="34182-124">그렇지 않으면 작업 단계가 실행될 때마다 이전 파일 내용을 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="34182-124">Otherwise, the previous file contents are overwritten each time the job step runs.</span></span>  
  
 <span data-ttu-id="34182-125">**테이블에 기록**</span><span class="sxs-lookup"><span data-stu-id="34182-125">**Log to table**</span></span>  
 <span data-ttu-id="34182-126">작업 단계 출력을 **msdb** 데이터베이스의 **sysjobstepslogs** 테이블에 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="34182-126">Logs job step output to the **sysjobstepslogs** table in the **msdb** database.</span></span>  
  
 <span data-ttu-id="34182-127">**보기**</span><span class="sxs-lookup"><span data-stu-id="34182-127">**View**</span></span>  
 <span data-ttu-id="34182-128">작업 단계가 최소 한 번 실행된 후에는 **보기** 를 클릭하여 테이블에 기록된 출력을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34182-128">After the job step has run at least once, click **View** to view its output in the table.</span></span>  
  
 <span data-ttu-id="34182-129">**테이블의 기존 항목에 출력 추가**</span><span class="sxs-lookup"><span data-stu-id="34182-129">**Append output to existing entry in table**</span></span>  
 <span data-ttu-id="34182-130">테이블의 기존 내용에 출력을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="34182-130">Appends output to the existing contents of the table.</span></span> <span data-ttu-id="34182-131">그렇지 않으면 작업 단계가 실행될 때마다 이전 테이블 내용을 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="34182-131">Otherwise, the previous table contents are overwritten each time the job step runs.</span></span>  
  
 <span data-ttu-id="34182-132">**기록에 단계 출력 포함**</span><span class="sxs-lookup"><span data-stu-id="34182-132">**Include step output in history**</span></span>  
 <span data-ttu-id="34182-133">작업 기록에 작업 단계의 출력을 포함하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="34182-133">Select this option to include output from the job step in the job history.</span></span>  
  
 <span data-ttu-id="34182-134">**다음 사용자 이름으로 실행**</span><span class="sxs-lookup"><span data-stu-id="34182-134">**Run as user**</span></span>  
 <span data-ttu-id="34182-135">사용자가 **sysadmin** 고정 서버 역할의 멤버인 경우 다른 SQL 로그인을 선택하여 이 작업 단계를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34182-135">If you are a member of the **sysadmin** fixed server role, you can select another SQL login to run this job step.</span></span>  
  
## <a name="options-for-operating-system-cmdexec-job-steps"></a><span data-ttu-id="34182-136">운영 체제(CmdExec) 작업 단계 옵션</span><span class="sxs-lookup"><span data-stu-id="34182-136">Options for Operating System (CmdExec) Job Steps</span></span>  
 <span data-ttu-id="34182-137">**출력 파일**</span><span class="sxs-lookup"><span data-stu-id="34182-137">**Output file**</span></span>  
 <span data-ttu-id="34182-138">작업 단계의 출력에 사용할 파일을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="34182-138">Sets the file to use for output from the job step.</span></span>  
  
 <span data-ttu-id="34182-139">**...**</span><span class="sxs-lookup"><span data-stu-id="34182-139">**...**</span></span>  
 <span data-ttu-id="34182-140">작업 단계의 출력에 사용할 파일을 찾아 봅니다.</span><span class="sxs-lookup"><span data-stu-id="34182-140">Browse to the file to use for output from the job step.</span></span>  
  
 <span data-ttu-id="34182-141">**보기**</span><span class="sxs-lookup"><span data-stu-id="34182-141">**View**</span></span>  
 <span data-ttu-id="34182-142">에서는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 이 단추를 사용 하 여 출력 파일을 볼 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="34182-142">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], this button is disabled for viewing output files.</span></span> <span data-ttu-id="34182-143">대신 메모장을 사용하여 작업 단계 출력 파일을 검토합니다.</span><span class="sxs-lookup"><span data-stu-id="34182-143">Instead, use Notepad to view job step output files.</span></span>  
  
 <span data-ttu-id="34182-144">**기존 파일에 출력 추가**</span><span class="sxs-lookup"><span data-stu-id="34182-144">**Append output to existing file**</span></span>  
 <span data-ttu-id="34182-145">작업 단계를 실행할 때마다 이전 파일 내용에 작업 단계 출력을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="34182-145">Appends the job step output to the previous file contents each time it runs.</span></span>  
  
 <span data-ttu-id="34182-146">**테이블에 기록**</span><span class="sxs-lookup"><span data-stu-id="34182-146">**Log to table**</span></span>  
 <span data-ttu-id="34182-147">작업 단계 출력을 **msdb** 데이터베이스의 **sysjobstepslogs** 테이블에 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="34182-147">Logs job step output to the **sysjobstepslogs** table in the **msdb** database.</span></span>  
  
 <span data-ttu-id="34182-148">**보기**</span><span class="sxs-lookup"><span data-stu-id="34182-148">**View**</span></span>  
 <span data-ttu-id="34182-149">작업 단계가 최소 한 번 실행된 후에는 **보기** 를 클릭하여 테이블에 기록된 출력을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34182-149">After the job step has run at least once, click **View** to view its output in the table.</span></span>  
  
 <span data-ttu-id="34182-150">**테이블의 기존 항목에 출력 추가**</span><span class="sxs-lookup"><span data-stu-id="34182-150">**Append output to existing entry in table**</span></span>  
 <span data-ttu-id="34182-151">테이블의 기존 내용에 출력을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="34182-151">Appends output to the existing contents of the table.</span></span> <span data-ttu-id="34182-152">그렇지 않으면 작업 단계가 실행될 때마다 이전 테이블 내용을 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="34182-152">Otherwise, the previous table contents are overwritten each time the job step runs.</span></span>  
  
 <span data-ttu-id="34182-153">**기록에 단계 출력 포함**</span><span class="sxs-lookup"><span data-stu-id="34182-153">**Include step output in history**</span></span>  
 <span data-ttu-id="34182-154">작업 기록에 작업 단계의 출력을 포함하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="34182-154">Select this option to include output from the job step in the job history.</span></span>  
  
## <a name="options-for-powershell-job-steps"></a><span data-ttu-id="34182-155">PowerShell 작업 단계 옵션</span><span class="sxs-lookup"><span data-stu-id="34182-155">Options for PowerShell Job Steps</span></span>  
 <span data-ttu-id="34182-156">**출력 파일**</span><span class="sxs-lookup"><span data-stu-id="34182-156">**Output file**</span></span>  
 <span data-ttu-id="34182-157">작업 단계의 출력에 사용할 파일을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="34182-157">Sets the file to use for output from the job step.</span></span>  
  
 <span data-ttu-id="34182-158">**...**</span><span class="sxs-lookup"><span data-stu-id="34182-158">**...**</span></span>  
 <span data-ttu-id="34182-159">작업 단계의 출력에 사용할 파일을 찾아 봅니다.</span><span class="sxs-lookup"><span data-stu-id="34182-159">Browse to the file to use for output from the job step.</span></span>  
  
 <span data-ttu-id="34182-160">**보기**</span><span class="sxs-lookup"><span data-stu-id="34182-160">**View**</span></span>  
 <span data-ttu-id="34182-161">에서는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 이 단추를 사용 하 여 출력 파일을 볼 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="34182-161">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], this button is disabled for viewing output files.</span></span> <span data-ttu-id="34182-162">대신 메모장을 사용하여 작업 단계 출력 파일을 검토합니다.</span><span class="sxs-lookup"><span data-stu-id="34182-162">Instead, use Notepad to view job step output files.</span></span>  
  
 <span data-ttu-id="34182-163">**기존 파일에 출력 추가**</span><span class="sxs-lookup"><span data-stu-id="34182-163">**Append output to existing file**</span></span>  
 <span data-ttu-id="34182-164">작업 단계를 실행할 때마다 이전 파일 내용에 작업 단계 출력을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="34182-164">Appends the job step output to the previous file contents each time it runs.</span></span>  
  
 <span data-ttu-id="34182-165">**테이블에 기록**</span><span class="sxs-lookup"><span data-stu-id="34182-165">**Log to table**</span></span>  
 <span data-ttu-id="34182-166">작업 단계 출력을 **msdb** 데이터베이스의 **sysjobstepslogs** 테이블에 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="34182-166">Logs job step output to the **sysjobstepslogs** table in the **msdb** database.</span></span>  
  
 <span data-ttu-id="34182-167">**보기**</span><span class="sxs-lookup"><span data-stu-id="34182-167">**View**</span></span>  
 <span data-ttu-id="34182-168">작업 단계가 최소 한 번 실행된 후에는 **보기** 를 클릭하여 테이블에 기록된 출력을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34182-168">After the job step has run at least once, click **View** to view its output in the table.</span></span>  
  
 <span data-ttu-id="34182-169">**테이블의 기존 항목에 출력 추가**</span><span class="sxs-lookup"><span data-stu-id="34182-169">**Append output to existing entry in table**</span></span>  
 <span data-ttu-id="34182-170">테이블의 기존 내용에 출력을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="34182-170">Appends output to the existing contents of the table.</span></span> <span data-ttu-id="34182-171">그렇지 않으면 작업 단계가 실행될 때마다 이전 테이블 내용을 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="34182-171">Otherwise, the previous table contents are overwritten each time the job step runs.</span></span>  
  
 <span data-ttu-id="34182-172">**기록에 단계 출력 포함**</span><span class="sxs-lookup"><span data-stu-id="34182-172">**Include step output in history**</span></span>  
 <span data-ttu-id="34182-173">작업 기록에 작업 단계의 출력을 포함하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="34182-173">Select this option to include output from the job step in the job history.</span></span>  
  
## <a name="options-for-replication-queue-reader-job-steps"></a><span data-ttu-id="34182-174">복제 큐 판독기 작업 단계 옵션</span><span class="sxs-lookup"><span data-stu-id="34182-174">Options for Replication Queue Reader Job Steps</span></span>  
 <span data-ttu-id="34182-175">**Server**</span><span class="sxs-lookup"><span data-stu-id="34182-175">**Server**</span></span>  
 <span data-ttu-id="34182-176">복제 큐 판독기 작업 단계에 사용할 서버를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="34182-176">Sets the server to use for a replication queue reader job step.</span></span>  
  
 <span data-ttu-id="34182-177">**Database**</span><span class="sxs-lookup"><span data-stu-id="34182-177">**Database**</span></span>  
 <span data-ttu-id="34182-178">복제 큐 판독기 작업 단계에 사용할 데이터베이스를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="34182-178">Sets the database to use for a replication queue reader job step.</span></span>  
  
## <a name="options-for-sql-server-analysis-services-job-steps"></a><span data-ttu-id="34182-179">SQL Server Analysis Services 작업 단계 옵션</span><span class="sxs-lookup"><span data-stu-id="34182-179">Options for SQL Server Analysis Services Job Steps</span></span>  
 <span data-ttu-id="34182-180">**출력 파일**</span><span class="sxs-lookup"><span data-stu-id="34182-180">**Output file**</span></span>  
 <span data-ttu-id="34182-181">작업 단계의 출력에 사용할 파일을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="34182-181">Sets the file to use for output from the job step.</span></span> <span data-ttu-id="34182-182">이 옵션은 **sysadmin** 고정 서버 역할의 멤버만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34182-182">This option is available only to members of the **sysadmin** fixed server role.</span></span>  
  
 <span data-ttu-id="34182-183">**...**</span><span class="sxs-lookup"><span data-stu-id="34182-183">**...**</span></span>  
 <span data-ttu-id="34182-184">작업 단계의 출력에 사용할 파일을 찾아 봅니다.</span><span class="sxs-lookup"><span data-stu-id="34182-184">Browse to the file to use for output from the job step.</span></span>  
  
 <span data-ttu-id="34182-185">**보기**</span><span class="sxs-lookup"><span data-stu-id="34182-185">**View**</span></span>  
 <span data-ttu-id="34182-186">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]에서는 이 단추를 사용하여 출력 파일을 표시할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="34182-186">In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], this button is disabled for viewing output files.</span></span> <span data-ttu-id="34182-187">대신 메모장을 사용하여 작업 단계 출력 파일을 검토합니다.</span><span class="sxs-lookup"><span data-stu-id="34182-187">Instead, use Notepad to view job step output files.</span></span>  
  
 <span data-ttu-id="34182-188">**기존 파일에 출력 추가**</span><span class="sxs-lookup"><span data-stu-id="34182-188">**Append output to existing file**</span></span>  
 <span data-ttu-id="34182-189">출력을 파일의 기존 내용에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="34182-189">Append output to the existing contents of the file.</span></span> <span data-ttu-id="34182-190">그렇지 않으면 작업 단계가 실행될 때마다 이전 파일 내용을 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="34182-190">Otherwise, the previous file contents are overwritten each time the job step runs.</span></span>  
  
 <span data-ttu-id="34182-191">**테이블에 기록**</span><span class="sxs-lookup"><span data-stu-id="34182-191">**Log to table**</span></span>  
 <span data-ttu-id="34182-192">작업 단계 출력을 **msdb** 데이터베이스의 **sysjobstepslogs** 테이블에 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="34182-192">Logs job step output to the **sysjobstepslogs** table in the **msdb** database.</span></span>  
  
 <span data-ttu-id="34182-193">**보기**</span><span class="sxs-lookup"><span data-stu-id="34182-193">**View**</span></span>  
 <span data-ttu-id="34182-194">작업 단계가 최소 한 번 실행된 후에는 **보기** 를 클릭하여 테이블에 기록된 출력을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34182-194">After the job step has run at least once, click **View** to view its output in the table.</span></span>  
  
 <span data-ttu-id="34182-195">**테이블의 기존 항목에 출력 추가**</span><span class="sxs-lookup"><span data-stu-id="34182-195">**Append output to existing entry in table**</span></span>  
 <span data-ttu-id="34182-196">테이블의 기존 내용에 출력을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="34182-196">Appends output to the existing contents of the table.</span></span> <span data-ttu-id="34182-197">그렇지 않으면 작업 단계가 실행될 때마다 이전 테이블 내용을 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="34182-197">Otherwise, the previous table contents are overwritten each time the job step runs.</span></span>  
  
 <span data-ttu-id="34182-198">**기록에 단계 출력 포함**</span><span class="sxs-lookup"><span data-stu-id="34182-198">**Include step output in history**</span></span>  
 <span data-ttu-id="34182-199">작업 기록에 작업 단계의 출력을 포함하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="34182-199">Select this option to include output from the job step in the job history.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34182-200">참고 항목</span><span class="sxs-lookup"><span data-stu-id="34182-200">See Also</span></span>  
 [<span data-ttu-id="34182-201">작업 단계 관리</span><span class="sxs-lookup"><span data-stu-id="34182-201">Manage Job Steps</span></span>](manage-job-steps.md)  
  
  
